---
title: Office 365 PowerShell을 사용 하 여 사용자 계정에서 라이센스를 제거 합니다.
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/20/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
- O365ITProTrain
ms.assetid: e7e4dc5e-e299-482c-9414-c265e145134f
description: Office 365 PowerShell을 사용 하 여 이전에 사용자에 게 할당 된 Office 365 라이선스를 제거 하는 방법에 대해 설명 합니다.
ms.openlocfilehash: ea762e992056ac3265336055eabb860f67482093
ms.sourcegitcommit: f2e640ffdbef95c6d98845f85fd9bea21a7388aa
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/21/2020
ms.locfileid: "43580925"
---
# <a name="remove-licenses-from-user-accounts-with-office-365-powershell"></a>Office 365 PowerShell을 사용 하 여 사용자 계정에서 라이센스를 제거 합니다.

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Graph 모듈용 Azure Active Directory PowerShell 사용하기

먼저, [Office 365 테넌트에 연결](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)합니다.

그런 다음이 명령을 사용 하 여 테 넌 트에 대 한 라이선스 계획을 나열 합니다.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

다음으로, UPN (사용자 계정 이름)이 라고도 하는 라이선스를 제거할 계정의 로그인 이름을 가져옵니다.

마지막으로 사용자 로그인 및 라이선스 계획 이름을 지정 하 고 "<" 및 ">" 문자를 제거한 후 다음 명령을 실행 합니다.

```powershell
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$license.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
$licenses.AddLicenses = $license
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
$Licenses.AddLicenses = @()
$Licenses.RemoveLicenses =  (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Windows PowerShell용 Microsoft Azure Active Directory 모듈 사용하기

먼저, [Office 365 테넌트에 연결](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)합니다.
   
조직의**AccountSkuID** (라이선스 계획) 정보를 확인 하려면 다음 항목을 참조 하십시오.
    
  - [라이선스 및 Office 365 PowerShell을 사용 하 여 서비스를 표시 합니다.](view-licenses-and-services-with-office-365-powershell.md)
    
  - [Office 365 PowerShell을 사용 하 여 계정 라이센스와 서비스 정보 보기](view-account-license-and-service-details-with-office-365-powershell.md)
    
_-All_ 매개 변수를 사용하지 않고 **Get-MsolUser** cmdlet을 사용하는 경우 처음 500개의 계정만 반환됩니다.
    
### <a name="removing-licenses-from-user-accounts"></a>사용자 계정에서 라이선스 제거

기존 사용자 계정에서 라이센스를 제거 하려면 다음 구문을 사용 합니다.
  
```powershell
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

>[!Note]
>PowerShell Core는 Windows PowerShell용 Microsoft Azure Active Directory 모듈 및 이름에 **Msol**이 있는 cmdlet을 지원하지 않습니다. 이러한 cmdlet을 계속 사용하려면 Windows PowerShell에서 이를 실행해야 합니다.
>

이 예에서는 사용자 계정 BelindaN@litwareinc.com에서 **litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3) 라이선스를 제거 합니다.
  
```powershell
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

>[!Note]
>Cmdlet을 사용 하 여 취소 된 라이선스의 사용자 할당을 취소할 수 없습니다. *canceled* `Set-MsolUserLicense` Microsoft 365 관리 센터에서 각 사용자 계정에 대해 개별적으로이 작업을 수행 해야 합니다.
>

기존 사용이 허가 된 사용자 그룹에서 라이센스를 제거 하려면 다음 방법 중 하나를 사용.
  
- **기존 계정 특성을 기반으로 계정 필터링** 이 작업을 수행 하려면 다음 구문을 사용 합니다.
    
```powershell
$x = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

이 예에서는 미국의 영업 부서에 있는 사용자의 모든 계정에서 **litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3) 라이선스를 제거 합니다.
    
```powershell
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
$USSales | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

- **특정 계정 목록 사용** 이렇게 하려면 다음 단계를 수행 합니다.
    
1. 만들고 다음과 같이 각 줄에 한 계정에 포함 된 텍스트 파일을 저장 합니다.
    
  ```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

2. 다음 구문을 사용합니다.
    
  ```powershell
  Get-Content "<FileNameAndPath>" | ForEach { Set-MsolUserLicense -UserPrincipalName $_ -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"... }
  ```

이 예에서는 텍스트 파일 C:\My Documents\accounts.txt입니다 .에 정의 된 사용자 계정에서 **litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3) 라이선스를 제거 합니다.
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUserLicense -UserPrincipalName $_ -RemoveLicenses "litwareinc:ENTERPRISEPACK" }
  ```

모든 기존 사용자 계정에서 모든 라이선스를 제거 하려면 다음 구문을 사용 합니다.
  
```powershell
$users = Get-MsolUser -All | where {$_.isLicensed -eq $true}
ForEach($user in $users)
{
$licenses = $user.Licenses.AccountSkuId
ForEach ($lic in $licenses)
{ Set-MsolUserLicense -UserPrincipalName $user.UserPrincipalName -RemoveLicenses $lic }
}
```

라이선스를 회수하는 또 다른 방법은 사용자 계정을 삭제하는 것입니다. 자세한 내용은 [Office 365 PowerShell을 사용 하 여 사용자 계정 삭제 및 복원을](delete-and-restore-user-accounts-with-office-365-powershell.md)참조 하세요.
  
## <a name="see-also"></a>참고 항목

[Office 365 PowerShell을 사용 하 여 사용자 계정, 라이선스 및 그룹 관리](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Office 365 PowerShell 사용한 Office 365 관리](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell 시작](getting-started-with-office-365-powershell.md)

