---
title: PowerShell을 사용 하 여 사용자 계정에 Microsoft 365 라이선스 할당
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/16/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Ent_Office_Other
- LIL_Placement
- PowerShell
- O365ITProTrain
ms.assetid: ba235f4f-e640-4360-81ea-04507a3a70be
search.appverid:
- MET150
description: PowerShell을 사용 하 여 라이선스가 없는 사용자에 게 Microsoft 365 라이선스를 할당 하는 방법
ms.openlocfilehash: 25a57158be82f985885a7ceaf89f526f9d522b4d
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/22/2020
ms.locfileid: "45229834"
---
# <a name="assign-microsoft-365-licenses-to-user-accounts-with-powershell"></a>PowerShell을 사용 하 여 사용자 계정에 Microsoft 365 라이선스 할당

*이 문서는 Microsoft 365 Enterprise 및 Office 365 Enterprise에 모두 적용 됩니다.*

사용자는 계정에 라이선스 요금제의 라이선스가 할당 되기 전 까지는 Microsoft 365 서비스를 사용할 수 없습니다. PowerShell을 사용 하 여 라이선스가 없는 계정에 빠르게 라이선스를 할당할 수 있습니다. 

>[!Note]
>사용자 계정에는 위치를 할당 해야 합니다. Microsoft 365 관리 센터 또는 PowerShell에서 사용자 계정의 속성을 사용 하 여이 작업을 수행할 수 있습니다.
>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Graph 모듈용 Azure Active Directory PowerShell 사용하기

먼저 [Microsoft 365 테 넌 트에 연결](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)합니다.
  

그런 다음이 명령을 사용 하 여 테 넌 트에 대 한 라이선스 계획을 나열 합니다.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

다음으로, UPN (사용자 계정 이름)이 라고도 하는 라이선스를 추가할 계정의 로그인 이름을 가져옵니다.

다음으로, 사용자 계정에 사용 위치를 할당 했는지 확인 합니다.

```powershell
Get-AzureADUser -ObjectID <user sign-in name (UPN)> | Select DisplayName, UsageLocation
```

사용 위치를 할당 하지 않은 경우 다음 명령을 사용 하 여 할당을 할당할 수 있습니다.

```powershell
$userUPN="<user sign-in name (UPN)>"
$userLoc="<ISO 3166-1 alpha-2 country code>"
Set-AzureADUser -ObjectID $userUPN -UsageLocation $userLoc
```

마지막으로 사용자 로그인 이름 및 라이선스 계획 이름을 지정 하 고 다음 명령을 실행 합니다.

```powershell
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Windows PowerShell용 Microsoft Azure Active Directory 모듈 사용하기

먼저 [Microsoft 365 테 넌 트에 연결](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)합니다.

`Get-MsolAccountSku`사용 가능한 라이선스 계획 및 조직의 각 계획에서 사용 가능한 라이선스 수를 확인 하려면 명령을 실행 합니다. 각 계획에서 사용할 수 있는 라이선스의 수는 **activeunits**  -  **WarningUnits**  -  **ConsumedUnits**입니다. 라이선스 계획, 라이선스 및 서비스에 대 한 자세한 내용은 PowerShell을 [사용 하 여 라이선스 및 서비스 보기](view-licenses-and-services-with-office-365-powershell.md)를 참조 하세요.

>[!Note]
>PowerShell Core는 Windows PowerShell용 Microsoft Azure Active Directory 모듈 및 이름에 **Msol**이 있는 cmdlet을 지원하지 않습니다. 이러한 cmdlet을 계속 사용하려면 Windows PowerShell에서 이를 실행해야 합니다.
>

조직에서 라이선스가 없는 계정을 찾으려면이 명령을 실행 합니다.

```powershell
Get-MsolUser -All -UnlicensedUsersOnly
```

**UsageLocation** 속성이 유효한 ISO 3166-1 국가 코드로 설정 된 사용자 계정에만 라이선스를 할당할 수 있습니다. 예를 들어 미국, 프랑스의 경우 FR을 들을 있습니다. 일부 Microsoft 365 서비스는 특정 국가에서 사용할 수 없습니다. 자세한 내용은 [사용권 제한 정보](https://go.microsoft.com/fwlink/p/?LinkId=691730)를 참조 하세요.
    
**UsageLocation** 값이 없는 계정을 찾으려면이 명령을 실행 합니다.

```powershell
Get-MsolUser -All | where {$_.UsageLocation -eq $null}
```

계정에 **UsageLocation** 값을 설정 하려면 다음 명령을 실행 합니다.

```powershell
Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>
```

예시:

```powershell
Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US
```
    
**-All** 매개 변수를 사용하지 않고 **Get-MsolUser** cmdlet을 사용하는 경우 처음 500개의 계정만 반환됩니다.

### <a name="assigning-licenses-to-user-accounts"></a>사용자 계정에 라이선스 할당
    
사용자에 게 라이선스를 할당 하려면 PowerShell에서 다음 명령을 사용 합니다.
  
```powershell
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

이 예에서는 **litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3) 라이선스 계획에서 라이선스가 없는 사용자 **belindan \@ litwareinc.com**에 라이선스를 할당 합니다.
  
```powershell
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

라이선스가 없는 모든 사용자에 게 라이선스를 할당 하려면이 명령을 실행 합니다.
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>] | Set-MsolUserLicense -AddLicenses "<AccountSkuId>"
```
  
>[!Note]
>동일한 라이센스 제도에서 여러 라이센스 사용자 지정할 수 없습니다. 반환 하는 순서 대로 사용자에 게 라이선스 할당 된 충분 한 사용 가능한 라이센스를 설정 하지 않은 경우는 **Get-MsolUser** cmdlet 사용 가능한 라이센스가 실행 될 때까지.
>

이 예에서는 **litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3) 라이선스 계획에서 라이선스가 없는 모든 사용자에 게 라이선스를 할당 합니다.
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

이 예에서는 미국의 영업 부서에 있는 라이선스가 없는 사용자에 게 동일한 라이선스를 할당 합니다.
  
```powershell
Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```
  
## <a name="move-a-user-to-a-different-subscription-license-plan-with-the-azure-active-directory-powershell-for-graph-module"></a>Graph 모듈에 대 한 Azure Active Directory PowerShell을 사용 하 여 다른 구독으로 사용자 이동 (라이선스 계획)

먼저 [Microsoft 365 테 넌 트에 연결](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)합니다.
  
다음으로, UPN (사용자 계정 이름)이 라고도 하는 스위치 구독을 사용할 사용자 계정의 로그인 이름을 가져옵니다.

그런 다음이 명령을 사용 하 여 테 넌 트에 대 한 구독 (라이선스 계획)을 나열 합니다.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

다음으로는 사용자 계정에 현재 이러한 명령이 포함 된 구독을 나열 합니다.

```powershell
$userUPN="<user account UPN>"
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

현재 사용자가 있는 구독 (보낸 사람 구독)과 사용자가 이동 하는 구독 (TO subscription)을 식별 합니다.

마지막으로 TO 및 FROM 구독 이름 (SKU 부분 번호)을 지정 하 고 다음 명령을 실행 합니다.

```powershell
$subscriptionFrom="<SKU part number of the current subscription>"
$subscriptionTo="<SKU part number of the new subscription>"
# Unassign
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$license.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $subscriptionFrom -EQ).SkuID
$licenses.AddLicenses = $license
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
$licenses.AddLicenses = @()
$licenses.RemoveLicenses =  (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $subscriptionFrom -EQ).SkuID
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
# Assign
$license.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $subscriptionTo -EQ).SkuID
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$licenses.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
```

이러한 명령을 사용 하 여 사용자 계정에 대 한 구독의 변경 내용을 확인할 수 있습니다.

```powershell
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

## <a name="see-also"></a>참고 항목

[PowerShell을 사용 하 여 사용자 계정, 라이선스 및 그룹 관리](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[PowerShell을 사용 하 여 Microsoft 365 관리](manage-office-365-with-office-365-powershell.md)
  
[Microsoft 365 용 PowerShell 시작](getting-started-with-office-365-powershell.md)
