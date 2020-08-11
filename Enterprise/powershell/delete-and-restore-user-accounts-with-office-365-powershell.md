---
title: PowerShell을 사용 하 여 Microsoft 365 사용자 계정 삭제
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
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
- O365ITProTrain
- seo-marvel-apr2020
ms.assetid: 209c9868-448c-49bc-baae-11e28b923a39
description: 이 문서에서는 PowerShell에서 서로 다른 모듈을 사용 하 여 Microsoft 365 사용자 계정을 삭제 하는 방법을 알아봅니다.
ms.openlocfilehash: d34201e2ef467ab4250ccde46a3d082b1b927d61
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605984"
---
# <a name="delete-microsoft-365-user-accounts-with-powershell"></a>PowerShell을 사용 하 여 Microsoft 365 사용자 계정 삭제

Microsoft 365 용 PowerShell을 사용 하 여 사용자 계정을 삭제할 수 있습니다.
   
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Graph 모듈용 Azure Active Directory PowerShell 사용하기

먼저 [Microsoft 365 테 넌 트에 연결](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)합니다.

연결한 후 다음 구문을 사용하여 개별 사용자 계정을 제거합니다.
  
```powershell
Remove-AzureADUser -ObjectID <sign-in name>
```

이 예제에서는 사용자 계정 fabricec@litwareinc.com을 제거합니다.
  
```powershell
Remove-AzureADUser -ObjectID fabricec@litwareinc.com
```

> [!NOTE]
> **AzureADUser** cmdlet의 **-ObjectID** 매개 변수는 사용자 보안 주체 이름이 라고도 하는 계정의 로그인 이름 또는 계정의 개체 ID를 허용 합니다.
  
사용자 이름을 기준으로 계정 이름을 표시하려면 다음 명령을 사용합니다.
  
```powershell
$userName="<User name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

이 예제에서는 Caleb Sills라는 사용자의 계정 이름을 표시합니다.
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

사용자 표시 이름을 기준으로 계정을 제거하려면 다음 명령을 사용합니다.
  
```powershell
$userName="<display name>"
Remove-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Windows PowerShell용 Microsoft Azure Active Directory 모듈 사용하기

Windows PowerShell용 Microsoft Azure Active Directory 모듈을 사용하여 사용자 계정을 삭제할 경우에 계정은 영구 삭제되지 않습니다. 30일 이내에 삭제한 사용자 계정은 복원할 수 있습니다. 

먼저 [Microsoft 365 테 넌 트에 연결](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)합니다.

사용자 계정을 삭제 하려면 다음 구문을 사용 합니다.
  
```powershell
Remove-MsolUser -UserPrincipalName <sign-in name>
```

>[!Note]
>PowerShell Core는 Windows PowerShell용 Microsoft Azure Active Directory 모듈 및 이름에 **Msol**이 있는 cmdlet을 지원하지 않습니다. 이러한 cmdlet을 계속 사용하려면 Windows PowerShell에서 이를 실행해야 합니다.
>

BelindaN@litwareinc.com 사용자 계정을 삭제 하는이 예제입니다.
  
```powershell
Remove-MsolUser -UserPrincipalName belindan@litwareinc.com
```

30 일 유예 기간 동안 삭제 된 사용자 계정을 복원 하려면 다음 구문을 사용 합니다.
  
```powershell
Restore-MsolUser -UserPrincipalName <sign-in name>
```

삭제 된 계정 BelindaN@litwareinc.com을 복원 하는이 예제입니다.
  
```powershell
Restore-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

 **참고:**
  
- 복원할 수 있는 삭제된 사용자 목록을 보려면 다음 명령을 실행 합니다.
    
  ```powershell
  Get-MsolUser -All -ReturnDeletedUsers
  ```

- 사용자 계정의 원본 사용자 계정 이름이 다른 계정에서 사용된 경우에, 사용자 계정을 복원할 때 다른 사용자 계정 이름을 지정하려면 _UserPrincipalName_ 대신에 _NewUserPrincipalName_ 매개 변수를 사용합니다.


## <a name="see-also"></a>참고 항목

[PowerShell로 Microsoft 365 사용자 계정, 라이선스 및 그룹 관리](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[PowerShell로 Microsoft 365 관리](manage-office-365-with-office-365-powershell.md)
  
[Microsoft 365 용 PowerShell 시작](getting-started-with-office-365-powershell.md)
