---
title: "DAP(위임된 액세스 권한) 파트너용 Windows PowerShell을 통해 고객 보고 데이터 집계"
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: DecEntMigration
ms.assetid: 0f946b46-200a-4bdd-9b1b-019a554ddcc6
description: "요약: 검색할 Office 365에 대 한 Windows PowerShell을 사용 하 여 보고 모든 고객 테 및 집계 데이터에서 단일 위치에 합니다."
ms.openlocfilehash: 89651971424d1b9a494335572d2654d8402ec146
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2017
---
# <a name="aggregate-customer-reporting-data-via-windows-powershell-for-delegated-access-permission-dap-partners"></a><span data-ttu-id="f8f38-103">DAP(위임된 액세스 권한) 파트너용 Windows PowerShell을 통해 고객 보고 데이터 집계</span><span class="sxs-lookup"><span data-stu-id="f8f38-103">Aggregate customer reporting data via Windows PowerShell for Delegated Access Permission (DAP) partners</span></span>

 <span data-ttu-id="f8f38-104">**요약:** Office 365에 대 한 Windows PowerShell을 사용 하 여 모든 고객 테에서 보고서를 검색 하 고 한곳에 데이터를 집계 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8f38-104">**Summary:** Use Windows PowerShell for Office 365 to retrieve reports on all customer tenancies and aggregate the data into a single location.</span></span>
  
<span data-ttu-id="f8f38-p101">기본적으로 Office 365에 대 한 Windows PowerShell에서 여러 고객 테 보고 데이터의 기본 제공 집계를 되어있지 않습니다. 그러나 각 고객에 대 한 단일 보고서를 검색 하 고 다음 단일 위치를 보고 데이터를 집계 하 여 모든 고객 테 반복할 Office 365 스크립트에 대 한 Windows PowerShell이이 예제를 사용할 수 있습니다. 결과 모든 고객 테 넌 트에 대 한 단일 보고서를 한 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f8f38-p101">By default, Windows PowerShell for Office 365 does not have a built-in aggregation of reporting data from multiple customer tenancies. However, you can use this sample Windows PowerShell for Office 365 script to iterate through all your customer tenancies to retrieve a single report for each of your customers and then aggregate the reporting data into a single location. The result is that you'll have a single report for all your customer tenants.</span></span> 
  
<span data-ttu-id="f8f38-p102">위임 된 액세스 권한 (DAP) 파트너는 신디케이션 및 클라우드 솔루션 공급자 (CSP) 파트너입니다. 다른 회사 네트워크 또는 전화 통신 공급자 자주 됩니다. 이러한 번들를 고객에 게 자신의 서비스 제품으로 Office 365 구독 합니다. Office 365 구독을 판매 하는 경우 고객 테에서 thecustomer 테 자신이 관리할 수 있도록 하 고 보고서에 사용 권한은 관리할 대리 (AOBO)를 자동으로 부여 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f8f38-p102">Delegated Access Permission (DAP) partners are Syndication and Cloud Solution Providers (CSP) Partners. They are frequently network or telecom providers to other companies. They bundle Office 365 subscriptions into their service offerings to their customers. When they sell an Office 365 subscription, they are automatically granted Administer On Behalf Of (AOBO) permissions to thecustomer tenancies so they can administer and report on the customer tenancies.</span></span>
## <a name="before-you-begin"></a><span data-ttu-id="f8f38-112">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="f8f38-112">Before you begin</span></span>

<span data-ttu-id="f8f38-113">이 스크립트를 사용하려면 다음과 같은 변수에 대한 특정 값을 대체하세요.</span><span class="sxs-lookup"><span data-stu-id="f8f38-113">To use this script, substitute your particular values in for these variables:</span></span>
  
- <span data-ttu-id="f8f38-p103">**$UserName** -파트너 관리자 사용자 이름입니다. 이러한 자격 증명에 모든 고객 테에 연결 하는데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f8f38-p103">**$UserName** - This is your partner administrator user name. These credentials will be used to connect to all your customer tenancies.</span></span>
    
- <span data-ttu-id="f8f38-116">**$OutputFile** -하기 위해 집계 데이터를 보고 하는 쉼표로 구분 된 값 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="f8f38-116">**$OutputFile** - This is the comma-separated value file that reporting data will be aggregated to.</span></span>
    
- <span data-ttu-id="f8f38-117">**$ErrorFile** -오류에 대 한 텍스트 로그 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="f8f38-117">**$ErrorFile** - This is the text log file for errors.</span></span>
    
- <span data-ttu-id="f8f38-p104">**$ScriptBlock** -이 샘플 스크립트를 사용 하 여 **Get MailboxActivityReport** 및 매개 변수 (예: 시작 및 종료 날짜)을 시작 하는 방법을 수 있도록 합니다. 다른 보고서를 원하는 경우 **Get MailboxActivityReport**에 대 한 원하는 보고서의 이름 및 필요한 매개 변수를 대체 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8f38-p104">**$ScriptBlock** - This sample script uses **Get-MailboxActivityReport** and parameters (such as start and end dates) so you have a way to get started. If you want other reports, substitute the report name that you want and necessary parameters for **Get-MailboxActivityReport**.</span></span>
    
- <span data-ttu-id="f8f38-120">Exchange Online에 대 한 원격 Windows PowerShell 세션에 [대 한 액세스 권한을 위임 (DAP) 파트너에 대 한 원격 Windows PowerShell을 사용한 Exchange Online 테 넌 트에 연결](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md) 하는 단계를 사용 하 여 열기</span><span class="sxs-lookup"><span data-stu-id="f8f38-120">Open a remote Windows PowerShell session to Exchange Online by using the steps in [Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)</span></span>
    
## <a name="use-windows-powershell-to-aggregate-customer-tenant-reports-to-a-single-location"></a><span data-ttu-id="f8f38-121">Windows PowerShell을 사용 하 여 단일 위치에 집계 고객 테 넌 트 보고서</span><span class="sxs-lookup"><span data-stu-id="f8f38-121">Use Windows PowerShell to aggregate customer tenant reports to a single location</span></span>

1. <span data-ttu-id="f8f38-122">아래 스크립트를 복사하여 메모장에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="f8f38-122">Copy and paste this script into Notepad.</span></span>
    
  ```
  # Import the MSOnline module to allow connectivity to Office 365.

Import-Module MSOnline

# This is the partner admin user name to be used to run the report.

$UserName = "admin@contoso.onmicrosoft.com"

# These are the locations for the report output and error log.

$OutputFile = ".\\ReportOutput.csv"

$ErrorFile = ".\\Errors.txt"

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

2. <span data-ttu-id="f8f38-p105">쉽게 찾을 수 있는 위치에 GetMailboxActivityReport.ps1로 스크립트를 저장 합니다. C: \에 파일을 저장 된 예:\\O365 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="f8f38-p105">Save the script as GetMailboxActivityReport.ps1 in a location that's easy for you to find. For the example, the file is saved in C:\\O365 Scripts.</span></span> 
    
3. <span data-ttu-id="f8f38-125">이 구문을 수행 하 여 원격 Windows PowerShell에서 스크립트를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8f38-125">Run the script in remote Windows PowerShell by following this syntax.</span></span>
    
  ```
  &amp; "C:\\O365 Scripts\\GetMailboxActivityReport.ps1"
  ```

<span data-ttu-id="f8f38-126">이 샘플 스크립트는 집계된 보고서를 ReportOutput.csv 파일에 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="f8f38-126">This sample script places the aggregated report in the ReportOutput.csv file.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="f8f38-127">See also</span><span class="sxs-lookup"><span data-stu-id="f8f38-127">See also</span></span>

#### 

[<span data-ttu-id="f8f38-128">파트너에 대 한 도움말</span><span class="sxs-lookup"><span data-stu-id="f8f38-128">Help for partners</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=533477)
  
[<span data-ttu-id="f8f38-129">Office 365 보고 웹 서비스</span><span class="sxs-lookup"><span data-stu-id="f8f38-129">Office 365 Reporting web service</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532777)
  
[<span data-ttu-id="f8f38-130">Exchange Online의 보고 cmdlet</span><span class="sxs-lookup"><span data-stu-id="f8f38-130">Reporting cmdlets in Exchange Online</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=526430)

