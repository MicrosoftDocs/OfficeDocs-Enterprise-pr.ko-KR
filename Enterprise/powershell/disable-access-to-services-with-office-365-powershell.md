---
title: PowerShell을 사용 하 여 Microsoft 365 서비스에 액세스할 수 없도록 설정
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/27/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Ent_Office_Other
- PowerShell
- LIL_Placement
- seo-marvel-apr2020
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: 이 문서에서는 PowerShell을 사용 하 여 사용자의 Microsoft 365 서비스에 대 한 액세스를 사용 하지 않도록 설정 하는 방법을 알아봅니다.
ms.openlocfilehash: f546014b83e0910e38817e0b7ef84d67f1b88614
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605974"
---
# <a name="disable-access-to-microsoft-365-services-with-powershell"></a>PowerShell을 사용 하 여 Microsoft 365 서비스에 액세스할 수 없도록 설정

*이 문서는 Microsoft 365 Enterprise와 Office 365 Enterprise에 모두 적용됩니다.*

Microsoft 365 계정에 라이선스 계획의 라이선스가 할당 되 면 해당 라이선스의 사용자가 Microsoft 365 서비스를 사용할 수 있습니다. 그러나 사용자가 액세스할 수 있는 Microsoft 365 서비스는 제어할 수 있습니다. 예를 들어 라이선스를 사용 하 여 SharePoint Online 서비스에 액세스할 수 있는 경우에도 액세스를 사용 하지 않도록 설정할 수 있습니다. PowerShell을 사용 하 여 특정 라이선스 계획에 대 한 모든 서비스에 대 한 액세스를 사용 하지 않도록 설정할 수 있습니다.

- 개별 계정
- 계정 그룹
- 조직의 모든 계정입니다.

>[!Note]
>다른 서비스가 종속 되어 있을 때 지정 된 서비스를 사용 하지 않도록 설정할 수 있는 Microsoft 365 서비스 종속성이 있습니다.
>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Windows PowerShell용 Microsoft Azure Active Directory 모듈 사용하기

먼저 [Microsoft 365 테 넌 트에 연결](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)합니다.

다음으로, 다음 명령을 사용 하 여 Account과 Uid 라고도 하는 사용 가능한 라이선스 계획을 봅니다.

```powershell
Get-MsolAccountSku | Select AccountSkuId | Sort AccountSkuId
```

>[!Note]
>PowerShell Core는 Windows PowerShell용 Microsoft Azure Active Directory 모듈 및 이름에 **Msol**이 있는 cmdlet을 지원하지 않습니다. 이러한 cmdlet을 계속 사용하려면 Windows PowerShell에서 이를 실행해야 합니다.
>

자세한 내용은 [PowerShell을 사용 하 여 라이선스 및 서비스 보기](view-licenses-and-services-with-office-365-powershell.md)를 참조 하세요.
    
이 항목에서 설명 하는 절차의 이전 및 후 결과를 보려면 [PowerShell을 사용 하 여 계정 라이선스 및 서비스 세부 정보 보기](view-account-license-and-service-details-with-office-365-powershell.md)를 참조 하세요.
    
이 항목에서 설명하는 절차를 자동화하는 PowerShell 스크립트를 사용할 수 있습니다. 특히이 스크립트를 사용 하면 Sway를 포함 하 여 Microsoft 365 조직에서 서비스를 확인 하 고 사용 하지 않도록 설정할 수 있습니다. 자세한 내용은 [PowerShell을 사용 하 여 Sway에 액세스 사용 안 함을](disable-access-to-sway-with-office-365-powershell.md)참조 하세요.
    
    
### <a name="disable-specific-microsoft-365-services-for-specific-users-for-a-specific-licensing-plan"></a>특정 라이선스 계획에 대해 특정 사용자에 대해 특정 Microsoft 365 서비스를 사용 하지 않도록 설정
  
특정 라이선스 계획에 대해 사용자에 대해 특정 Microsoft 365 서비스 집합을 사용 하지 않도록 설정 하려면 다음 단계를 수행 합니다.
  
#### <a name="step-1-identify-the-undesirable-services-in-the-licensing-plan-by-using-the-following-syntax"></a>1 단계: 다음 구문을 사용 하 여 라이선스 계획에서 원하지 않는 서비스를 식별 합니다.
    
```powershell
$LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
```

다음 예제에서는 라는 라이선스 계획에서 Office 및 SharePoint Online 서비스를 사용 하지 않도록 설정 하는 **LicenseOptions** 개체 `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3)를 만듭니다.
    
```powershell
$LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
```

#### <a name="step-2-use-the-licenseoptions-object-from-step-1-on-one-or-more-users"></a>2 단계: 한 명 이상의 사용자에 대해 1 단계의 **LicenseOptions** 개체를 사용 합니다.
    
서비스를 사용 하지 않도록 설정 된 새 계정을 만들려면 다음 구문을 사용 합니다.
    
```powershell
New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
```

다음 예에서는 라이선스를 할당 하 고 1 단계에서 설명 하는 서비스를 사용 하지 않도록 설정 하는 Allie에 대 한 새 계정을 만듭니다.
    
```powershell
New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
```

Microsoft 365 용 PowerShell에서 사용자 계정을 만드는 방법에 대 한 자세한 내용은 [powershell을 사용 하 여 사용자 계정 만들기](create-user-accounts-with-office-365-powershell.md)를 참조 하십시오.
    
사용이 허가 된 기존 사용자에 대 한 서비스를 사용 하지 않도록 설정 하려면 다음 구문을 사용 합니다.
    
```powershell
Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
```

이 예에서는 사용자 BelindaN@litwareinc.com에 대 한 서비스를 사용 하지 않도록 설정 합니다.
    
```powershell
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
```

기존의 사용이 허가 된 모든 사용자에 대해 1 단계에서 설명 하는 서비스를 사용 하지 않도록 설정 하려면 **get-msolaccountsku** cmdlet의 표시에서 Microsoft 365 계획의 이름을 지정 하 고 **LITWAREINC: enterprisepack**과 같이 지정한 후 다음 명령을 실행 합니다.
    
```powershell
$acctSKU="<AccountSkuId>"
$AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses.AccountSku.SkuPartNumber -contains ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
$AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

 _All_ 매개 변수를 사용 하지 않고 **get-msoluser** cmdlet을 사용 하는 경우에는 첫 번째 500 사용자 계정만 반환 됩니다.

기존 사용자 그룹에 대 한 서비스를 사용 하지 않도록 설정 하려면 다음 방법 중 하나를 사용 하 여 사용자를 식별 합니다.
    
**방법 1 기존 계정 특성을 기반으로 계정 필터링** 

그렇게 하려면 다음 구문을 사용합니다.
    
```powershell
$x = Get-MsolUser -All <FilterableAttributes>
$x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

다음 예에서는 미국 영업부에 있는 사용자에 대 한 서비스를 사용 하지 않도록 설정 합니다.
    
```powershell
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
$USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

**방법 2: 특정 계정 목록 사용** 

이 작업을 수행 하려면 다음 단계를 수행 합니다.
    
1. 다음과 같이 각 줄에 한 계정에 포함 된 텍스트 파일을 만듭니다.
    
   ```powershell
   akol@contoso.com
   tjohnston@contoso.com
   kakers@contoso.com
   ```

   이 예제에서 텍스트 파일은 C: \\ 내 문서Accounts.txt입니다 \\ .
    
2. 다음 명령을 실행합니다.
    
   ```powershell
   Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
   ```

여러 라이선싱 계획에 대 한 서비스에 대 한 액세스를 사용 하지 않도록 설정 하려면 각 라이선스 계획에 대해 위의 지침을 반복 하 고 다음을 수행 합니다.

- 사용자 계정에 라이선스 계획이 할당 되었습니다.
- 사용 하지 않도록 설정할 서비스는 라이선스 계획에서 사용할 수 있습니다.

사용자가 라이선스를 계획에 할당 하는 동안 Microsoft 365 서비스를 사용 하지 않도록 설정 하려면 [사용자 라이선스를 할당 하는 동안 서비스에 대 한 액세스 사용 안 함을](disable-access-to-services-while-assigning-user-licenses.md)참조 하세요.

### <a name="assign-all-services-in-a-licensing-plan-to-a-user-account"></a>라이선스 계획의 모든 서비스를 사용자 계정에 할당

서비스를 사용 하지 않도록 설정한 사용자 계정의 경우 다음 명령을 사용 하 여 특정 라이선스 계획에 대해 모든 서비스를 사용 하도록 설정할 수 있습니다.

```powershell
$userUPN="<user account UPN>"
$acctSKU="<AccountSkuId>"
$LO = New-MsolLicenseOptions -AccountSkuId $acctSKU
Set-MsolUserLicense -UserPrincipalName $userUPN -LicenseOptions $LO
```

## <a name="related-topic"></a>관련 항목

[PowerShell로 Microsoft 365 사용자 계정, 라이선스 및 그룹 관리](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[PowerShell로 Microsoft 365 관리](manage-office-365-with-office-365-powershell.md)
  
[Microsoft 365 용 PowerShell 시작](getting-started-with-office-365-powershell.md)
