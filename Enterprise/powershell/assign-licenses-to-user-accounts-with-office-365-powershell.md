---
title: Office 365 PowerShell을 사용 하 여 사용자 계정에 라이선스를 할당 합니다.
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/29/2019
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
description: Office 365 PowerShell 할당 허가 되지 않은 사용자에 게 Office 365 라이선스를 사용 하는 방법에 설명 합니다.
ms.openlocfilehash: ab9b66065e20d0c2d6cfb673dac24ee2ab79e831
ms.sourcegitcommit: 6826e0ea4a777f7d98500209a9d3bc75e89f8d15
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/30/2019
ms.locfileid: "29651185"
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a>Office 365 PowerShell을 사용 하 여 사용자 계정에 라이선스를 할당 합니다.

**요약:**  Office 365 PowerShell 할당 허가 되지 않은 사용자에 게 Office 365 라이선스를 사용 하는 방법에 설명 합니다.
  
사용자가 자신의 계정이 할당 된 라이선스 라이선스 계획에서 때까지 모든 Office 365 서비스를 사용할 수 없습니다. Office 365 PowerShell을 사용 하 여 신속 하 게 사용 허가 되지 않은 계정에 라이선스를 할당 하 수 있습니다. 


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Graph 모듈용 Azure Active Directory PowerShell 사용하기

먼저, [Office 365 테넌트에 연결](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)합니다.
  

다음으로,이 명령 사용 하 여 테 넌 트에 대 한 라이선스 계획을 나열 합니다.

```
Get-AzureADSubscribedSku | Select SkuPartNumber
```

다음으로도 알려져 사용자 계정 이름 (UPN) 라이선스, 추가 추가할 계정의 로그인 이름을 가져옵니다.

마지막으로, 사용자 로그인 이름 및 라이선스 계획 이름을 지정 하 고 이러한 명령을 실행 합니다.

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

조직에서 각 계획에서 사용 가능한 라이선스 계획 및 사용 가능한 라이선스 수를 보려면 **Get-msolaccountsku** 명령을 실행 합니다. 각 계획에서 사용 가능한 라이선스 수가 **ActiveUnits** - **WarningUnits** - **ConsumedUnits**합니다. 계획, 라이선스 및 서비스 라이선스에 대 한 자세한 내용은 [보기 라이선스 및 Office 365 PowerShell을 사용 하 여 서비스를](view-licenses-and-services-with-office-365-powershell.md)참조 하십시오.
    
조직에서 허가 되지 않은 계정을 찾으려고이 명령을 실행 합니다.

```
Get-MsolUser -All -UnlicensedUsersOnly
```
    
만 **usagelocation이** 속성이 유효한 ISO 3166-1 alpha-2 국가 코드를로 설정 하는 사용자 계정에 라이선스를 할당할 수 있습니다. 예: 대한민국, 미국, 대한민국 및 프랑스에 대 한 FR 합니다. 일부 Office 365 서비스 일부 국가에서는 사용할 수 없습니다. 자세한 내용은 [라이선스 제한에 대 한](https://go.microsoft.com/fwlink/p/?LinkId=691730)참조입니다.
    
**Usagelocation이** 값을 갖지 않는 계정을이 명령을 실행 합니다.

```
Get-MsolUser -All | where {$_.UsageLocation -eq $null}
```

계정에 **usagelocation이** 값을 설정 하려면이 명령을 실행 합니다.

```
Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>
```

예를 들면 다음과 같습니다.

```
Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US
```
    
**-All** 매개 변수를 사용하지 않고 **Get-MsolUser** cmdlet을 사용하는 경우 처음 500개의 계정만 반환됩니다.

### <a name="assigning-licenses-to-user-accounts"></a>사용자 계정에 라이선스를 할당합니다.
    
사용자에 게 라이선스를 할당 하려면 Office 365 PowerShell에서 다음 명령을 사용 합니다.
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

이 예제에서는는 **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) 적절 한 계획을 허가 되지 않은 사용자 **belindan@litwareinc.com**라이선스에서 라이선스를 할당 합니다.
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

많은 허가 되지 않은 사용자에 게 라이선스를 할당할이 명령을 실행 합니다.
  
```
Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>] | ForEach {Set-MsolUserLicense -AddLicenses "<AccountSkuId>"}
```
  
>[!Note]
>동일한 라이선스 계획에서 사용자에 게 여러 라이선스를 할당할 수 없습니다. 충분 한 사용 가능한 라이선스를 설치 하지 않은 경우 사용 가능한 라이선스 실행 될 때까지 **Get-msoluser** cmdlet에 의해 반환 하는 순서는 사용자에 게 라이선스 할당 됩니다.
>

이 예제에서는 모든 허가 되지 않은 사용자에 게 **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) 라이선스 계획에서 라이선스를 할당합니다.
  
```
Get-MsolUser -All -UnlicensedUsersOnly | ForEach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

이 예제에서는 미국에서 Sales 부서에 허가 되지 않은 사용자에 게 이러한 동일한 라이선스를 할당합니다.
  
```
Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly | ForEach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```
  
## <a name="new-to-office-365"></a>Office 365의 새로운 기능

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a>참고 항목

[Office 365 PowerShell로 사용자 계정 및 라이선스 관리](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Office 365 PowerShell로 Office 365 관리](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell 시작](getting-started-with-office-365-powershell.md)
