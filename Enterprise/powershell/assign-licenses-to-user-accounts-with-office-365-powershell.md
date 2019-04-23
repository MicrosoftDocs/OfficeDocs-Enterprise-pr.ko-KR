---
title: Office 365 PowerShell을 사용 하 여 사용자 계정에 라이선스를 할당 합니다.
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/18/2019
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- LIL_Placement
- PowerShell
- O365ITProTrain
ms.assetid: ba235f4f-e640-4360-81ea-04507a3a70be
search.appverid:
- MET150
description: office 365 PowerShell을 사용 하는 방법에 대해 설명 합니다.
ms.openlocfilehash: ac2cdb8c303cacc5c9664b877ba86a5b196432b1
ms.sourcegitcommit: 51f9e89e4b9d54f92ef5c70468bda96e664b8a6b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2019
ms.locfileid: "31957649"
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a>Office 365 PowerShell을 사용 하 여 사용자 계정에 라이선스를 할당 합니다.

**요약:**  office 365 PowerShell을 사용 하는 방법에 대해 설명 합니다.
  
사용자는 계정에 라이선스 요금제의 라이선스가 할당 되기 전 까지는 모든 Office 365 서비스를 사용할 수 없습니다. Office 365 PowerShell을 사용 하 여 라이선스가 없는 계정에 빠르게 라이선스를 할당할 수 있습니다. 


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Graph 모듈용 Azure Active Directory PowerShell 사용하기

먼저, [Office 365 테넌트에 연결](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)합니다.
  

그런 다음이 명령을 사용 하 여 테 넌 트에 대 한 라이선스 계획을 나열 합니다.

```
Get-AzureADSubscribedSku | Select SkuPartNumber
```

다음으로, UPN (사용자 계정 이름)이 라고도 하는 라이선스를 추가할 계정의 로그인 이름을 가져옵니다.

마지막으로 사용자 로그인 이름 및 라이선스 계획 이름을 지정 하 고 다음 명령을 실행 합니다.

```
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Windows PowerShell용 Microsoft Azure Active Directory 모듈 사용하기

먼저, [Office 365 테넌트에 연결](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)합니다.

**Get-get-msolaccountsku** 명령을 실행 하 여 조직의 각 계획에서 사용할 수 있는 라이선스 계획 및 사용 가능한 라이선스 수를 확인 합니다. 각 계획에서 사용할 수 있는 라이선스의 수는 **activeunits** - **WarningUnits** - **ConsumedUnits**입니다. 라이선스 계획, 라이선스 및 서비스에 대 한 자세한 내용은 [Office 365 PowerShell을 사용 하 여 라이선스 및 서비스 보기](view-licenses-and-services-with-office-365-powershell.md)를 참조 하세요.
    
조직에서 라이선스가 없는 계정을 찾으려면이 명령을 실행 합니다.

```
Get-MsolUser -All -UnlicensedUsersOnly
```
    
**UsageLocation** 속성이 유효한 ISO 3166-1 국가 코드로 설정 된 사용자 계정에만 라이선스를 할당할 수 있습니다. 예를 들어 미국, 프랑스의 경우 FR을 들을 있습니다. 일부 Office 365 서비스는 특정 국가에서 사용할 수 없습니다. 자세한 내용은 [사용권 제한 정보](https://go.microsoft.com/fwlink/p/?LinkId=691730)를 참조 하세요.
    
**UsageLocation** 값이 없는 계정을 찾으려면이 명령을 실행 합니다.

```
Get-MsolUser -All | where {$_.UsageLocation -eq $null}
```

계정에 **UsageLocation** 값을 설정 하려면 다음 명령을 실행 합니다.

```
Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>
```

예를 들면 다음과 같습니다.

```
Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US
```
    
**-All** 매개 변수를 사용하지 않고 **Get-MsolUser** cmdlet을 사용하는 경우 처음 500개의 계정만 반환됩니다.

### <a name="assigning-licenses-to-user-accounts"></a>사용자 계정에 라이선스 할당
    
사용자에 게 라이선스를 할당 하려면 Office 365 PowerShell에서 다음 명령을 사용 합니다.
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

이 예에서는 **litwareinc: enterprisepack** (Office 365 Enterprise E3) 라이선스 계획에서 라이선스가 없는 사용자 **belindan@litwareinc.com**에 게 라이선스를 할당 합니다.
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

라이선스가 너무 많은 사용자에 게 라이선스를 할당 하려면이 명령을 실행 합니다.
  
```
Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>] | Set-MsolUserLicense -AddLicenses "<AccountSkuId>"
```
  
>[!Note]
>동일한 라이센스 제도에서 여러 라이센스 사용자 지정할 수 없습니다. 반환 하는 순서 대로 사용자에 게 라이선스 할당 된 충분 한 사용 가능한 라이센스를 설정 하지 않은 경우는 **Get-MsolUser** cmdlet 사용 가능한 라이센스가 실행 될 때까지.
>

이 예에서는 **litwareinc: enterprisepack** (Office 365 Enterprise E3) 라이선스 계획에서 라이선스가 없는 모든 사용자에 게 라이선스를 할당 합니다.
  
```
Get-MsolUser -All -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

이 예에서는 미국의 영업 부서에 있는 라이선스가 없는 사용자에 게 동일한 라이선스를 할당 합니다.
  
```
Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```
  
## <a name="new-to-office-365"></a>Office 365의 새로운 기능

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a>참고 항목

[Office 365 PowerShell로 사용자 계정 및 라이선스 관리](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Office 365 PowerShell 사용한 Office 365 관리](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell 시작](getting-started-with-office-365-powershell.md)
