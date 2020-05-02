---
title: Office 365 PowerShell을 사용 하 여 계정 라이센스와 서비스 정보 보기
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/17/2019
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
- PowerShell
- Ent_Office_Other
- LIL_Placement
ms.assetid: ace07d8a-15ca-4b89-87f0-abbce809b519
description: Office 365 PowerShell을 사용 하 여 사용자에 게 할당 된 Office 365 서비스를 확인 하는 방법에 대해 설명 합니다.
ms.openlocfilehash: 603470be87aea2d58f343511026fb2860e58b688
ms.sourcegitcommit: d1022143bdefdd5583d8eff08046808657b49c94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/02/2020
ms.locfileid: "44004491"
---
# <a name="view-account-license-and-service-details-with-office-365-powershell"></a>Office 365 PowerShell을 사용 하 여 계정 라이센스와 서비스 정보 보기

Office 365에서는 라이선스 요금제 (Sku 또는 Office 365 요금제 라고도 함)의 라이선스를 사용자에 게 해당 요금제에 대해 정의 된 Office 365 서비스에 대 한 액세스 권한을 부여 합니다. 그러나 사용자는 현재 할당된 라이선스에서 사용할 수 있는 모든 서비스에 액세스하지 못할 수도 있습니다. Office 365 PowerShell을 사용 하 여 사용자 계정에 대 한 서비스 상태를 볼 수 있습니다. 

라이선스 계획, 라이선스 및 서비스에 대 한 자세한 내용은 [Office 365 PowerShell을 사용 하 여 라이선스 및 서비스 보기](view-licenses-and-services-with-office-365-powershell.md)를 참조 하세요.

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Graph 모듈용 Azure Active Directory PowerShell 사용하기

먼저, [Office 365 테넌트에 연결](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)합니다.
  
그런 다음이 명령을 사용 하 여 테 넌 트에 대 한 라이선스 계획을 나열 합니다.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

이러한 명령을 사용 하 여 각 라이선스 계획에서 사용할 수 있는 서비스를 나열 합니다.

```powershell
$allSKUs=Get-AzureADSubscribedSku
$licArray = @()
for($i = 0; $i -lt $allSKUs.Count; $i++)
{
$licArray += "Service Plan: " + $allSKUs[$i].SkuPartNumber
$licArray +=  Get-AzureADSubscribedSku -ObjectID $allSKUs[$i].ObjectID | Select -ExpandProperty ServicePlans
$licArray +=  ""
}
$licArray
```

이러한 명령을 사용 하 여 사용자 계정에 할당 된 라이선스를 나열 합니다.

```powershell
$userUPN="<user account UPN, such as belindan@contoso.com>"
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Windows PowerShell용 Microsoft Azure Active Directory 모듈 사용하기

먼저, [Office 365 테넌트에 연결](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)합니다.

다음으로이 명령을 실행 하 여 조직에서 사용할 수 있는 라이선스 계획을 나열 합니다. 

```powershell
Get-MsolAccountSku
```
>[!Note]
>PowerShell Core는 Windows PowerShell용 Microsoft Azure Active Directory 모듈 및 이름에 **Msol**이 있는 cmdlet을 지원하지 않습니다. 이러한 cmdlet을 계속 사용하려면 Windows PowerShell에서 이를 실행해야 합니다.
>

다음으로, 각 라이선스 계획에서 사용할 수 있는 서비스와 이러한 서비스가 나열 되는 순서 (인덱스 번호)를 나열 하려면이 명령을 실행 합니다.

```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```
  
이 명령을 사용 하 여 사용자에 게 할당 된 라이선스와 해당 라이선스가 나열 되는 순서 (인덱스 번호)를 나열 합니다.

```powershell
Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses
```

### <a name="to-view-services-for-a-user-account"></a>사용자 계정에 대 한 서비스를 보려면

사용자가 액세스할 수 있는 모든 Office 365 서비스를 보려면 다음 구문을 사용 합니다.
  
```powershell
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

이 예에서는 사용자 BelindaN@litwareinc.com에 게 액세스 권한이 있는 서비스를 표시 합니다. 사용자의 계정에 할당된 모든 라이선스와 관련된 서비스를 표시합니다.
  
```powershell
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

이 예제에서는 사용자 BelindaN@litwareinc.com이 계정에 할당된 첫 번째 라이선스(인덱스 번호: 0)에서 액세스할 수 있는 서비스를 표시합니다.
  
```powershell
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

*여러 라이선스가*할당 된 사용자의 모든 서비스를 보려면 다음 구문을 사용 합니다.

```powershell
$userUPN="<user account UPN>"
$AllLicenses=(Get-MsolUser -UserPrincipalName $userUPN).Licenses
$licArray = @()
for($i = 0; $i -lt $AllLicenses.Count; $i++)
{
$licArray += "License: " + $AllLicenses[$i].AccountSkuId
$licArray +=  $AllLicenses[$i].ServiceStatus
$licArray +=  ""
}
$licArray
```
 
## <a name="see-also"></a>참고 항목

[Office 365 PowerShell을 사용 하 여 사용자 계정, 라이선스 및 그룹 관리](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Office 365 PowerShell 사용한 Office 365 관리](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell 시작](getting-started-with-office-365-powershell.md)
