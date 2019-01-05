---
title: Office 365 PowerShell을 사용 하 여 허가 된 / 허가 되지 않은 사용자 보기
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: e4ee53ed-ed36-4993-89f4-5bec11031435
description: 사용 하는 방법에 설명 Office 365 PowerShell 허가 된 / 허가 되지 않은 사용자 계정을 볼 수 있습니다.
ms.openlocfilehash: 79f7bf1966d515634c5fc038db650c19547259aa
ms.sourcegitcommit: a39d15b7cf758dfb262d2724bcfd283bba3d2ce1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/04/2019
ms.locfileid: "27730343"
---
# <a name="view-licensed-and-unlicensed-users-with-office-365-powershell"></a>Office 365 PowerShell을 사용 하 여 허가 된 / 허가 되지 않은 사용자 보기

**요약:** Office 365 PowerShell을 사용하여 허가되거나 허가되지 않은 사용자 계정을 확인할 수 있습니다.
  
사용자 계정에 사용자 Office 365 조직 일부, 또는 전체 조직에서 사용할 수 있는 라이센스 계획에서 할당 된 사용 가능한 라이선스 중 있을 수 있습니다. 사용할 수 있습니다 Office 365 PowerShell 조직에서 허가 된 / 허가 되지 않은 사용자를 빠르게 찾을 수 있습니다.


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Graph 모듈용 Azure Active Directory PowerShell 사용하기

먼저, [Office 365 테넌트에 연결](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)합니다.
 
할당 되지 않은 사용자의 라이선스 계획 (허가 되지 않은 사용자) 중 하나는 조직에서 모든 사용자 계정 목록을 보려면 다음 명령을 실행 합니다.
  
```
Get-AzureAdUser | ForEach{ $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $user.AssignedLicenses[$i].disabledplans ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $false) { Write-Host $_.UserPrincipalName} }
```

된 조직에서 모든 사용자 계정 목록을 보려면 다음 명령을 실행 하 여 라이선스 계획 (사용이 허가 된 사용자) 중 하나를 할당 합니다.
  
```
Get-AzureAdUser | ForEach { $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $user.AssignedLicenses[$i].disabledplans ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $true) { Write-Host $_.UserPrincipalName} }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Windows PowerShell용 Microsoft Azure Active Directory 모듈 사용하기

먼저, [Office 365 테넌트에 연결](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)합니다.

조직에서 모든 사용자 계정 및 라이선스 상태 목록을 보려는 다음 명령에서 실행 Office 365 PowerShell.
  
```
Get-MsolUser -All
```

조직의 모든 허가 되지 않은 사용자 계정 목록을 보려면 다음 명령을 실행 합니다.
  
```
Get-MsolUser -All -UnlicensedUsersOnly
```

전체 목록을 보려면 다음 명령을 실행 하 여 조직에 있는 사용자 계정의 라이센스:
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true}
```

## <a name="see-also"></a>참고 항목

[Office 365 PowerShell로 사용자 계정 및 라이선스 관리](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Office 365 PowerShell로 Office 365 관리](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell 시작](getting-started-with-office-365-powershell.md)
