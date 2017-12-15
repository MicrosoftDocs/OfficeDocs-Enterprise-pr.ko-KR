---
title: "삭제 한 사용자 계정 Office 365 PowerShell을 사용 하 여 복원 합니다."
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- DecEntMigration
- PowerShell
- Ent_Office_Other
- O365ITProTrain
ms.assetid: 209c9868-448c-49bc-baae-11e28b923a39
description: "Office 365 PowerShell을 사용 하 여 삭제 하 고 Office 365 사용자 계정 복원 하는 방법에 알아봅니다."
ms.openlocfilehash: 8404395ea9594cea1a2e772cecbeb011756b7754
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2017
---
# <a name="delete-and-restore-user-accounts-with-office-365-powershell"></a>삭제 한 사용자 계정 Office 365 PowerShell을 사용 하 여 복원 합니다.

**요약:**  Office 365 PowerShell을 사용 하 여 삭제 하 고 Office 365 사용자 계정 복원 하는 방법에 알아봅니다.
  
Office 365 PowerShell을 사용 하 여 사용자 계정을 삭제 하려면 계정 영구적으로 삭제 되지 않습니다. 30 일 이내에 삭제 된 사용자 계정에 복원할 수 있습니다.
  
## <a name="before-you-begin"></a>시작하기 전에

- 이 항목의 절차에서는 Office 365 PowerShell에 연결 해야 합니다. 자세한 내용은 [Office 365 PowerShell 연결](connect-to-office-365-powershell.md)을 참조 하십시오.
    
- 사용 하지 않고 **Get-msoluser** cmdlet을 사용 하는 경우는 _-모든_ 매개 변수를 처음 500 개 계정만 반환 됩니다.
    
## <a name="use-office-365-powershell-to-block-access-to-individual-user-accounts"></a>Office 365 PowerShell을 사용 하 여 개별 사용자 계정에 대 한 액세스를 차단 하려면
<a name="ShortVersion"> </a>

사용자 계정을 삭제 하려면 다음 구문을 사용 합니다.
  
```
Remove-MsolUser -UserPrincipalName <Account>
```

BelindaN@litwareinc.com 사용자 계정을 삭제 하는이 예제입니다.
  
```
Remove-MsolUser -UserPrincipalName belindan@litwareinc.com
```

30 일 유예 기간 동안 삭제 된 사용자 계정을 복원 하려면 다음 구문을 사용 합니다.
  
```
Restore-MsolUser -UserPrincipalName <Account>
```

삭제 된 계정 BelindaN@litwareinc.com을 복원 하는이 예제입니다.
  
```
Restore-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

 **참고 사항:**
  
- 복원할 수 있는 삭제 된 사용자의 목록을 보려면 다음 명령을 실행 합니다.
    
  ```
  Get-MsolUser -All -ReturnDeletedUsers
  ```

- 사용자 계정의 원래 사용자 계정 이름 다른 계정에서 사용 하는 경우는 사용자 계정이 복원 하는 경우 다른 사용자 계정 이름을 지정 하려면 _UserPrincipalName_ 대신 _NewUserPrincipalName_ 매개 변수를 사용 합니다.
    
## <a name="use-the-azure-active-directory-v2-powershell-module-to-remove-a-user-account"></a>Azure Active Directory V2 PowerShell 모듈을 사용하여 사용자 계정 제거
<a name="ShortVersion"> </a>

Azure Active Directory V2 PowerShell 모듈에서 **제거 AzureADUser** cmdlet을 사용 하려면 먼저 구독에 연결 해야 합니다. 지침, [Azure Active Directory V2 PowerShell 모듈을 사용 하 여 연결](https://go.microsoft.com/fwlink/?linkid=842218)을 참조 하십시오.
  
연결한 후 다음 구문을 사용하여 개별 사용자 계정을 제거합니다.
  
```
Remove-AzureADUser -ObjectID <Account>
```

이 예제에서는 사용자 계정 fabricec@litwareinc.com을 제거합니다.
  
```
Remove-AzureADUser -ObjectID fabricec@litwareinc.com
```

> [!NOTE]
> **제거 AzureAD** cmdlet의 **-ObjectID** 매개 변수는 허용 중 하나는 계정 이름로 알려져 사용자 계정 이름 또는 계정 개체 id입니다.
  
사용자 이름을 기준으로 계정 이름을 표시하려면 다음 명령을 사용합니다.
  
```
$userName="<User name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

이 예제에서는 Caleb Sills라는 사용자의 계정 이름을 표시합니다.
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

사용자 이름을 기준으로 계정을 제거하려면 다음 명령을 사용합니다.
  
```
$userName="<User name>"
Remove-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

## <a name="see-also"></a>참고 항목
<a name="SeeAlso"> </a>

Office 365 powershell 사용자를 관리 하는 방법에 대 한 다음 추가 항목을 참조 합니다.
  
- [Office 365 PowerShell을 사용한 사용자 계정 만들기](create-user-accounts-with-office-365-powershell.md)
    
- [Office 365 powershell 블록 사용자 계정](block-user-accounts-with-office-365-powershell.md)
    
- [Office 365 PowerShell을 사용한 사용자 계정에 게 라이선스 할당](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [Office 365 PowerShell을 사용한 사용자 계정에서 라이선스를 제거 합니다.](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
이 항목에서 사용된 cmdlet에 대한 자세한 내용은 다음 항목을 참조하십시오.
  
- [Get-msoluser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [이와 제거](https://go.microsoft.com/fwlink/p/?LinkId=691636)
    
- [이와 복원](https://go.microsoft.com/fwlink/p/?LinkId=691637)
    
- [새 AzureADUser](https://docs.microsoft.com/powershell/module/azuread/new-azureaduser?view=azureadps-2.0)
    

