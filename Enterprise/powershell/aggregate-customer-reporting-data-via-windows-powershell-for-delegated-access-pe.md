---
title: DAP(위임된 액세스 권한) 파트너용 Windows PowerShell을 통해 고객 보고 데이터 집계
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: 0f946b46-200a-4bdd-9b1b-019a554ddcc6
description: 요약:Office 365에 대해 Windows PowerShell을 사용하여 모든 고객 테넌트에서 보고서를 검색하고 단일 위치로 데이터를 집계합니다.
ms.openlocfilehash: eba2c3be848b878670321485718317b5552b2db3
ms.sourcegitcommit: 8ff1cd7733dba438697b68f90189d4da72bbbefd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/20/2018
---
# <a name="aggregate-customer-reporting-data-via-windows-powershell-for-delegated-access-permission-dap-partners"></a>DAP(위임된 액세스 권한) 파트너용 Windows PowerShell을 통해 고객 보고 데이터 집계

 **요약:** Office 365에 대해 Windows PowerShell을 사용하여 모든 고객 테넌트에서 보고서를 검색하고 단일 위치로 데이터를 집계합니다.
  
기본적으로 Office 365용 Windows PowerShell에는 여러 고객 테넌트의 보고 데이터에 대한 기본 제공 집계가 없습니다. 그러나 Office 365 스크립트에 대해 이 샘플 Windows PowerShell을 사용하여 각각의 고객에 대한 단일 보고서를 검색하도록 모든 고객 테넌트를 반복한 후 단일 위치에 보고 데이터를 집계할 수 있습니다. 그 결과 모든 고객 테넌트에 대한 단일 보고서를 얻게 됩니다. 
  
DAP(위임된 액세스 권한) 파트너는 Syndication 및 CSP(클라우드 솔루션 공급자) 파트너입니다. 이러한 공급자는 다른 회사의 네트워크 또는 전자 통신 공급자인 경우가 많습니다. 이러한 공급자는 서비스와 Office 365 구독을 통합해서 고객에게 제공합니다. Office 365 구독을 판매하는 경우 고객 테넌트에 대한 AOBO(관리 위임자) 권한이 자동으로 부여되므로 고객 테넌트를 관리하고 보고할 수 있습니다.
## <a name="before-you-begin"></a>시작하기 전에

이 스크립트를 사용하려면 다음과 같은 변수에 대한 특정 값을 대체하세요.
  
- **$UserName** - 파트너 관리자 사용자 이름입니다. 이러한 자격 증명은 모든 고객 테넌트에 연결하는 데 사용됩니다.
    
- **$OutputFile** - 보고 데이터가 집계되는, 쉼표로 구분된 값 파일입니다.
    
- **$ErrorFile** - 오류에 대한 텍스트 로그 파일입니다.
    
- **$ScriptBlock** - 이 샘플 스크립트는 **Get-MailboxActivityReport** 와 매개 변수(예: 시작/종료 날짜)를 사용하여 시작할 수 있습니다. 다른 보고서를 원하는 경우 원하는 보고서 이름과 **Get-MailboxActivityReport** 에 대해 필요한 매개 변수를 대체합니다.
    
- [DAP(위임된 액세스 권한) 파트너용 원격 Windows PowerShell을 사용하여 Exchange Online 테넌트에 연결](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md) 에서 단계를 사용하여 원격 Windows PowerShell 세션을 Exchange Online으로 엽니다.
    
## <a name="use-windows-powershell-to-aggregate-customer-tenant-reports-to-a-single-location"></a>Windows PowerShell을 사용하여 고객 테넌트 보고서를 단일 위치에 집계

1. 아래 스크립트를 복사하여 메모장에 붙여넣습니다.
    
  ```
  # Import the MSOnline module to allow connectivity to Office 365.

Import-Module MSOnline

# This is the partner admin user name to be used to run the report.

$UserName = "admin@contoso.onmicrosoft.com"

# These are the locations for the report output and error log.

$OutputFile = ".\ReportOutput.csv"

$ErrorFile = ".\Errors.txt"

# This is the report to run and all the necessary parameters.

$ScriptBlock = {Get-MailboxActivityReport -ReportType Daily -StartDate 03/18/2015 -EndDate 03/18/2015}

$LinesToSkip = 0

# This is the prompt for the password of the partner admin user name.

$Cred = get-credential -Credential $UserName

# Establish a Windows PowerShell session with Office 365.

Connect-MsolService -Credential $Cred

# Get all the contracts for the signed-in partner.  
# Contracts define the AOBO/DAP relationship between the partner and the customers.

$Contracts = Get-MsolPartnerContract -All

Write-Host "Found $($Contracts.Count) customers for this Partner."

# For each of the contracts (customers), run the specified report and output the information.

foreach ($c in $contracts) { 

    # Get the initial domain for the customer.

    $InitialDomain = Get-MsolDomain -TenantId $c.TenantId | Where {$_.IsInitial -eq $true}

    # Construct the URL with the DelegatedOrg parameter.
    
    $DelegatedOrgURL = "https://ps.outlook.com/powershell-liveid?DelegatedOrg=" + $InitialDomain.Name
        
    Write-Host "Running report for $($InitialDomain.Name)"

    # Invoke-Command establishes a Windows PowerShell session based on the URL,
    # runs the command, and closes the Windows PowerShell session.
    
    $ReportInfo = Invoke-Command -ConnectionUri $DelegatedOrgURL -Credential $Cred -Authentication Basic -ConfigurationName Microsoft.Exchange -AllowRedirection -ScriptBlock $ScriptBlock -HideComputerName

    # If Invoke-Command returned information (that is, it's not NULL), format and output the information.
    
    If ($ReportInfo) {

        Write-Host "Writing report information for $($InitialDomain.Name) to $OutputFile"  -foregroundcolor green

        # Convert the report data to CSV format.
        # For the first time, don't skip any lines, so include the header.
        # For all other times, skip the first line (so don't rewrite the header).
        
        $OutputInfo = $ReportInfo |  ConvertTo-CSV -NoTypeInformation | Select -Skip $LinesToSkip

        Out-File $OutputFile -InputObject $OutputInfo -Append

        $LinesToSkip = 1

    } else {

        # If Invoke-Command didn't return and report data, log an error.
        
        Write-Host "No report information for $($InitialDomain.Name)." -foregroundcolor yellow
           
        Out-File $ErrorFile  -InputObject @("No report information for $($InitialDomain.Name).") -Append
    }

}

  ```

2. 스크립트를 쉽게 찾을 수 있는 위치에 GetMailboxActivityReport.ps1로 저장합니다. 예를 들어 해당 파일은 C:\\O365 Scripts에 저장됩니다. 
    
3. 이 구문을 따라 원격 Windows PowerShell 에서 스크립트를 실행합니다.
    
  ```
  &amp; "C:\O365 Scripts\GetMailboxActivityReport.ps1"
  ```

이 샘플 스크립트는 집계된 보고서를 ReportOutput.csv 파일에 배치합니다.
  
## <a name="see-also"></a>참고 항목

#### 

[파트너를 위한 도움말](https://go.microsoft.com/fwlink/p/?LinkID=533477)
  
[Office 365 Reporting Web Service](https://go.microsoft.com/fwlink/p/?LinkId=532777)
  
[Exchange Online의 Reporting Cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=526430)

