---
title: PowerShell을 사용 하 여 라이선스가 부여 되 고 라이선스가 없는 Microsoft 365 사용자 보기
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/21/2020
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
- O365ITProTrain
- Ent_Office_Other
- PowerShell
- seo-marvel-apr2020
ms.assetid: e4ee53ed-ed36-4993-89f4-5bec11031435
description: 이 문서에서는 PowerShell을 사용 하 여 허가 되거나 허가 되지 않은 Microsoft 365 사용자 계정을 보는 방법에 대해 설명 합니다.
ms.openlocfilehash: 470c4dff2b425ba570926002c1efd68310e37d71
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605290"
---
# <a name="view-licensed-and-unlicensed-microsoft-365-users-with-powershell"></a>PowerShell을 사용 하 여 라이선스가 부여 되 고 라이선스가 없는 Microsoft 365 사용자 보기

*이 문서는 Microsoft 365 Enterprise와 Office 365 Enterprise에 모두 적용됩니다.*

Microsoft 365 조직의 사용자 계정에는 조직에서 사용할 수 있는 라이선스 계획에서 사용 가능한 라이선스 중 일부 또는 모두가 할당 되거나 아예 제공 되지 않을 수 있습니다. Microsoft 365 용 PowerShell을 사용 하 여 조직에서 라이선스가 부여 되 고 라이선스가 없는 사용자를 빠르게 찾을 수 있습니다.

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Graph 모듈용 Azure Active Directory PowerShell 사용하기

먼저 [Microsoft 365 테 넌 트에 연결](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)합니다.
 
조직에서 라이선스 계획 (라이선스가 없는 사용자)이 할당 되지 않은 모든 사용자 계정 목록을 보려면 다음 명령을 실행 합니다.
  
```powershell
Get-AzureAdUser | ForEach{ $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $_.AssignedLicenses[$i].SkuId ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $false) { Write-Host $_.UserPrincipalName} }
```

라이선스 계획 (라이선스 사용자)이 할당 된 조직의 모든 사용자 계정 목록을 보려면 다음 명령을 실행 합니다.
  
```powershell
Get-AzureAdUser | ForEach { $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $_.AssignedLicenses[$i].SkuId ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $true) { Write-Host $_.UserPrincipalName} }
```

>[!Note]
>구독의 모든 사용자를 나열 하려면 `Get-AzureAdUser -All $true` 명령을 사용 합니다.
>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Windows PowerShell용 Microsoft Azure Active Directory 모듈 사용하기

먼저 [Microsoft 365 테 넌 트에 연결](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)합니다.

조직의 모든 사용자 계정 및 라이선스 상태 목록을 보려면 PowerShell에서 다음 명령을 실행 합니다.
  
```powershell
Get-MsolUser -All
```

>[!Note]
>PowerShell Core는 Windows PowerShell용 Microsoft Azure Active Directory 모듈 및 이름에 **Msol**이 있는 cmdlet을 지원하지 않습니다. 이러한 cmdlet을 계속 사용하려면 Windows PowerShell에서 이를 실행해야 합니다.
>

조직의 모든 허가 되지 않은 사용자 계정 목록을 보려면 다음 명령을 실행 합니다.
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly
```

전체 목록을 보려면 다음 명령을 실행 하 여 조직에 있는 사용자 계정의 라이센스:
  
```powershell
Get-MsolUser -All | where {$_.isLicensed -eq $true}
```

## <a name="see-also"></a>기타 참고 항목

[PowerShell로 Microsoft 365 사용자 계정, 라이선스 및 그룹 관리](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[PowerShell로 Microsoft 365 관리](manage-office-365-with-office-365-powershell.md)
  
[Microsoft 365 용 PowerShell 시작](getting-started-with-office-365-powershell.md)
