---
title: Office 365 PowerShell로 사용자 계정 삭제하기
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- O365ITProTrain
ms.assetid: 209c9868-448c-49bc-baae-11e28b923a39
description: Office 365 PowerShell을 사용하여 Office 365 사용자 계정을 삭제하는 방법에 대해 알아보세요.
ms.openlocfilehash: e62c06981a861580804dde852ad3da7bd729fdbe
ms.sourcegitcommit: 4b057db053e93b0165f1ec6c4799cff4c2852566
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/25/2019
ms.locfileid: "39257649"
---
# <a name="delete-user-accounts-with-office-365-powershell"></a>Office 365 PowerShell로 사용자 계정 삭제하기

사용자 계정을 삭제할 때 Office 365 PowerShell을 사용할 수 있습니다.
   
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Graph 모듈용 Azure Active Directory PowerShell 사용하기

먼저, [Office 365 테넌트에 연결](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)합니다.

연결한 후 다음 구문을 사용하여 개별 사용자 계정을 제거합니다.
  
```powershell
Remove-AzureADUser -ObjectID <sign-in name>
```

>[!Note]
>PowerShell Core에서는 이름에 **Msol** 이 포함 된 Windows powershell 모듈 및 cmdlet에 대 한 Microsoft Azure Active Directory 모듈을 지원 하지 않습니다. 이러한 cmdlet을 계속 사용 하려면 Windows PowerShell에서 실행 해야 합니다.
>

이 예제에서는 사용자 계정 fabricec@litwareinc.com을 제거합니다.
  
```powershell
Remove-AzureADUser -ObjectID fabricec@litwareinc.com
```

> [!NOTE]
> **Remove-AureAD** cmdlet의 **-ObjectID** 매개 변수는 사용자 계정 이름으로 알려진 계정 로그인 이름, 또는 계정의 개체 ID를 허용합니다.
  
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

먼저, [Office 365 테넌트에 연결](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)합니다.


사용자 계정을 삭제하려면 다음 구문을 사용 합니다.
  
```powershell
Remove-MsolUser -UserPrincipalName <sign-in name>
```

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

[Office 365 PowerShell로 사용자 계정 및 라이선스 관리](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Office 365 PowerShell 사용한 Office 365 관리](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell 시작](getting-started-with-office-365-powershell.md)

