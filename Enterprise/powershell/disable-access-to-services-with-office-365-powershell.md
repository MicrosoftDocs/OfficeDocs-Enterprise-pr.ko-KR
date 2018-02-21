---
title: "Office 365 PowerShell을 사용 하 여 서비스에 대 한 액세스를 비활성화 합니다."
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/13/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- PowerShell
- LIL_Placement
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: "Office 365 PowerShell을 사용 하 여 조직에서 사용자를 위한 Office 365 서비스에 대 한 액세스를 사용 하지 않도록 설정 하는 방법에 설명 합니다."
ms.openlocfilehash: 61d92a1a0c55a381f10fedbb43403dd099fcb69b
ms.sourcegitcommit: 07416472be80566370c30631aff740177b37b24c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/19/2018
---
# <a name="disable-access-to-services-with-office-365-powershell"></a>Office 365 PowerShell을 사용 하 여 서비스에 대 한 액세스를 비활성화 합니다.

**요약:** Office 365 PowerShell을 사용 하 여 조직에서 사용자를 위한 Office 365 서비스에 대 한 액세스를 사용 하지 않도록 설정 하는 방법에 설명 합니다.
  
Office 365 계정을 라이선스 계획에서 라이선스를 할당 된, Office 365 서비스 사용할 수 있습니다는 사용자에 게 해당 라이선스에서 합니다. 그러나 사용자가 액세스할 수 있는 Office 365 서비스를 제어할 수 있습니다. 예, 라이선스에는 SharePoint Online에 액세스할 수 있도록, 경우에에 대 한 액세스를 비활성화할 수 있습니다. 실제로 임의 개수의 대 한 서비스에 대 한 액세스를 사용 하지 않도록 설정 하려면 Office 365 PowerShell를 사용할 수 있습니다.

- 개별 계정입니다.
    
- 그룹 계정입니다.
    
- 조직의 모든 계정입니다.
    
## <a name="before-you-begin"></a>시작하기 전에
<a name="RTT"> </a>

- 이 항목의 절차를 수행하려면 Office 365 PowerShell에 연결되어 있어야 합니다. 지침을 보려면 [PowerShell Office 365에 연결](connect-to-office-365-powershell.md)을 참조하세요.
    
- **Get-msolaccountsku** cmdlet를 사용 하 여 사용 가능한 라이선스 계획 및 해당 계획에서 사용할 수 있는 Office 365 서비스를 볼 수 있습니다. 자세한 내용은 [보기 라이선스 및 Office 365 PowerShell을 사용 하 여 서비스를](view-licenses-and-services-with-office-365-powershell.md)참조 하십시오.
    
- 참조 하는 하기 전과 후이 항목의 절차에서는의 결과 [Office 365 powershell 계정 라이선스 및 서비스 정보 보기](view-account-license-and-service-details-with-office-365-powershell.md)를 참조 합니다.
    
- PowerShell 스크립트를 사용할 수 있는이 항목에서 설명 하는 절차를 자동화 합니다. 특히, 스크립트를 사용 하 보기 및 Office 365 조직 전체에서 영향을 포함 하 여 서비스를 사용 하지 않도록 설정할 수 있습니다. 자세한 내용은 [Office 365 powershell 영향에 대 한 액세스를 사용 하지 않도록 설정](disable-access-to-sway-with-office-365-powershell.md)을 참조 하십시오.
    
- _모든_ 매개 변수를 사용 하지 않고 **Get-msoluser** cmdlet을 사용 하는 경우 첫번째 500 사용자 계정만 반환 됩니다.
    
## <a name="specific-office-365-services-for-specific-users-for-a-single-licensing-plan"></a>단일 라이선스에 대 한 특정 사용자에 대 한 특정 Office 365 서비스 계획
  
단일 라이선스 계획에서 사용자를 위한 Office 365 서비스의 특정 집합을 사용 하지 않으려면 다음 단계를 수행 합니다.
  
1. 다음 구문을 사용 하 여 라이선스 계획에서 원하지 않는 서비스를 식별 합니다.
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
  ```

    다음 예제에서는 이름이 지정 된 라이선스 계획에서 Office Online 및 SharePoint Online 서비스를 사용 하지 않도록 설정 하는 **LicenseOptions** 개체를 `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
  ```

2. 1 단계에서에서 **LicenseOptions** 개체를 사용 하 여 하나 이상의 사용자에 게 있습니다.
    
  - 서비스를 비활성화 하는 가진 새 계정을 만들려면 다음 구문을 사용 합니다.
    
  ```
  New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
  ```

    다음 예제에서는 라이선스를 할당 하 고 1 단계에서에서 설명 하는 서비스를 사용 하지 않도록 설정 하는 Allie Bellew에 대 한 새 계정을 만듭니다.
    
  ```
  New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
  ```

    Office 365 PowerShell의 사용자 계정 만들기 (영문) 하는 방법에 대 한 자세한 내용은 [Office 365 PowerShell을 사용한 사용자 계정 만들기를](create-user-accounts-with-office-365-powershell.md)참조 하십시오.
    
  - 기존 사용이 허가 된 사용자에 대 한 서비스를 사용 하지 않으려면 다음 구문을 사용 합니다.
    
  ```
  Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
  ```

    BelindaN@litwareinc.com 사용자에 대 한 서비스를 해제 하는이 예제입니다.
    
  ```
  Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
  ```

  - 모든 기존 사용이 허가 된 사용자에 대해 1 단계에서에서 설명 하는 서비스를 사용 하지 않으려면 (예: **litwareinc:ENTERPRISEPACK**) **Get-msolaccountsku** cmdlet의 표시에서 Office 365 계획의 이름을 지정 하 고 다음 명령을 실행 합니다.
    
  ```
  $acctSKU="<AccountSkuId>"
  $AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
  $AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - 기존 사용자 그룹에 대 한 서비스를 사용 하지 않으려면 다음 방법 중 하나를 사용자를 식별 하기 위해 사용.
    
  - **기존 계정 특성을 기준으로 계정 필터링** 이 작업을 수행 하려면 다음 구문을 사용 합니다.
    
  ```
  $x = Get-MsolUser -All <FilterableAttributes>
  $x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

    다음 예제에서는 미국에서 Sales 부서에 있는 사용자에 대 한 서비스를 비활성화합니다.
    
  ```
  $USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
  $USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - **특정 계정 목록 사용** 이 작업을 수행 하려면 다음 단계를 수행 합니다.
    
1. 다음과 같이 각 줄에 한 계정에 포함 된 텍스트 파일을 만듭니다.
    
  ```
  akol@contoso.com
  tjohnston@contoso.com
  kakers@contoso.com
  ```

    이 예제에서는 텍스트 파일은 c:\\My Documents\\Accounts.txt 합니다.
    
2. 다음 명령을 실행합니다.
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

라이선스 계획에 할당 되는 동안에 사용자를 위한 Office 365 서비스를 사용 하지 않도록 하십시오 [사용자 라이선스를 할당 하는 동안 서비스에 대 한 액세스를 사용 하지 않도록 설정](disable-access-to-services-while-assigning-user-licenses.md)을 참조 하십시오.
  
## <a name="specific-office-365-services-for-users-from-all-licensing-plans"></a>모든 라이선스 계획에서 사용자에 대 한 특정 Office 365 서비스
  
모든 사용 가능한 라이선스 계획에 사용자를 위한 Office 365 서비스를 비활성화 하려면 다음 단계를 수행 합니다.
  
1. 아래 스크립트를 복사하여 메모장에 붙여넣습니다.
    
  ```
  $AllLicensingPlans = Get-MsolAccountSku
for($i = 0; $i -lt $AllLicensingPlans.Count; $i++)
{
    $O365Licences = New-MsolLicenseOptions -AccountSkuId $AllLicensingPlans[$i].AccountSkuId -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
    Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $O365Licences
}
  ```

2. 사용자 환경에 대 한 다음 값을 사용자 지정 합니다.
    
  -  _<UndesirableService>_이 예제에서는 Office Online 및 SharePoint Online를 사용 합니다.
    
  -  _<Account>_이 예제에서는 belindan@litwareinc.com를 사용 합니다.
    
    사용자 지정 된 스크립트는 다음과 같습니다.
    
  ```
  $AllLicensingPlans = Get-MsolAccountSku
for($i = 0; $i -lt $AllLicensingPlans.Count; $i++)
{
    $O365Licences = New-MsolLicenseOptions -AccountSkuId $AllLicensingPlans[$i].AccountSkuId -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
    Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $O365Licences
}
  ```

3. 으로 스크립트를 저장 `RemoveO365Services.ps1` 를 쉽게 찾을 수 있는 위치에 있습니다. 이 예제에서는에서 파일을 저장 합니다는 `C:\\O365 Scripts`합니다.
    
4. 다음 명령을 사용 하 여 Office 365 PowerShell에서 스크립트를 실행 합니다.
    
  ```
  & "C:\O365 Scripts\RemoveO365Services.ps1"
  ```

> [!NOTE]
> 이러한 절차의 효과 반전 하려면 (즉, 다시 사용할 수 없는 서비스를 사용 하도록 설정)을 하는 절차를 다시 실행 되지만 값을 사용 하 여 `$null` _DisabledPlans_ 매개 변수에 대 한 합니다.
  
[맨위로 돌아가기](disable-access-to-services-with-office-365-powershell.md#RTT)


## <a name="all-office-365-services-for-all-users-for-a-single-licensing-plan"></a>단일 라이선스에 대 한 모든 사용자에 대 한 모든 Office 365 서비스 계획
 
특정 라이선스 계획에서 모든 사용자에 대 한 모든 Office 365 서비스를 사용 하지 않도록 설정 합니다 (예: **litwareinc:ENTERPRISEPACK**) $acctSKU에 대 한 라이선스 계획 이름을 지정 하 고 PowerShell 명령 창에 다음이 명령을 실행:

```
$acctSKU="<AccountSkuId>"
$servicesList=(Get-MsolAccountSku | Select -ExpandProperty ServiceStatus).ServicePlan.ServiceName
$lo = New-MsolLicenseOptions -AccountSkuId $acctSKU -DisabledPlans $servicesList
$AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
$AllLicensed | ForEach {Set-MsolUserLicense -ObjectID $_.ObjectID -LicenseOptions $lo}
```

## <a name="new-to-office-365"></a>Office 365의 새로운 기능
<a name="LinkedIn"> </a>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a>참고 항목
<a name="SeeAlso"> </a>

Office 365 PowerShell을 사용 하여 사용자를 관리에 대하여 다음과 같은 추가 항목을 참조 하십시오.
  
- [삭제 한 사용자 계정 Office 365 PowerShell을 사용 하 여 복원 합니다.](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [삭제 한 사용자 계정 Office 365 PowerShell을 사용 하 여 복원 합니다.](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [블록 사용자 계정 Office 365 PowerShell을 사용 하 여](block-user-accounts-with-office-365-powershell.md)
    
- [Office 365 PowerShell을 사용 하 여 사용자 계정에 라이선스를 할당 합니다.](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [Office 365 PowerShell을 사용 하 여 사용자 계정 만들기](create-user-accounts-with-office-365-powershell.md)
    
이 항목에서 사용된 cmdlet에 대한 자세한 내용은 다음 항목을 참조하십시오.
  
- [Get-content](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [Get-msolaccountsku](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [새 MsolLicenseOptions](https://go.microsoft.com/fwlink/p/?LinkId=691546)
    
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [New-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [Set-msoluserlicense](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [ForEach-Object](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
  

