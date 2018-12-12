---
title: 삭제 한 사용자 계정 Office 365 PowerShell을 사용 하 여 복원 합니다.
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
- PowerShell
- Ent_Office_Other
- O365ITProTrain
ms.assetid: 209c9868-448c-49bc-baae-11e28b923a39
description: Office 365 PowerShell을 사용하여 Office 365 사용자 계정을 삭제하고 복원하는 방법에 대해 알아보세요.
ms.openlocfilehash: 09f3595ed7cd5434efb2897a43ba1bbca5286c25
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2018
ms.locfileid: "17552781"
---
# <a name="delete-and-restore-user-accounts-with-office-365-powershell"></a>삭제 한 사용자 계정 Office 365 PowerShell을 사용 하 여 복원 합니다.

**요약:** Office 365 PowerShell을 사용하여 Office 365 사용자 계정을 삭제하고 복원하는 방법에 대해 알아보세요.
  
사용 하 여 Office 365 PowerShell 사용자 계정을 삭제 하려면 계정을 삭제 영구적으로 되지 않습니다. 30 일 이내에 삭제 한 사용자 계정은 복원할 수 있습니다.
  
## <a name="before-you-begin"></a>시작하기 전에

- 이 항목의 절차를 수행하려면 Office 365 PowerShell에 연결되어 있어야 합니다. 지침을 보려면 [PowerShell Office 365에 연결](connect-to-office-365-powershell.md)을 참조하세요.
    
- _-All_ 매개 변수를 사용하지 않고 **Get-MsolUser** cmdlet을 사용하는 경우 처음 500개의 계정만 반환됩니다.
    
## <a name="use-office-365-powershell-to-block-access-to-individual-user-accounts"></a>사용 하 여 Office 365 PowerShell 개별 사용자 계정에 대 한 액세스를 차단 하려면
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

 **참고:**
  
- 복원할 수 있는 삭제 된 사용자의 목록을 보려면 다음 명령을 실행 합니다.
    
  ```
  Get-MsolUser -All -ReturnDeletedUsers
  ```

- 원본 사용자 계정의 사용자 계정 이름을 다른 계정으로 사용할 경우 사용의  _NewUserPrincipalName_ 매개 변수 대신 _UserPrincipalName_ 사용자 계정을 복원할 때 다른 사용자 계정 이름 지정.
    
## <a name="use-the-azure-active-directory-v2-powershell-module-to-remove-a-user-account"></a>Azure Active Directory V2 PowerShell 모듈을 사용하여 사용자 계정 제거
<a name="ShortVersion"> </a>

Azure Active Directory V2 PowerShell 모듈에서 **Remove-AzureADUser** cmdlet을 사용하려면 먼저 구독에 연결해야 합니다. 지침에 대한 자세한 내용은 [Azure Active Directory V2 PowerShell 모듈을 사용하여 연결](https://go.microsoft.com/fwlink/?linkid=842218)을 참조하세요.
  
연결한 후 다음 구문을 사용하여 개별 사용자 계정을 제거합니다.
  
```
Remove-AzureADUser -ObjectID <Account>
```

이 예제에서는 사용자 계정 fabricec@litwareinc.com을 제거합니다.
  
```
Remove-AzureADUser -ObjectID fabricec@litwareinc.com
```

> [!NOTE]
> **Remove-AzureAD** cmdlet의 **-ObjectID** 매개 변수는 사용자 계정 이름으로도 알려진 계정 이름이나 계정의 개체 ID를 허용합니다.
  
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

Office 365 PowerShell을 사용하여 사용자를 관리하는 방법에 대한 다음 추가 항목을 참조하세요.
  
- [Office 365 PowerShell을 사용 하 여 사용자 계정 만들기](create-user-accounts-with-office-365-powershell.md)
    
- [블록 사용자 계정 Office 365 PowerShell을 사용 하 여](block-user-accounts-with-office-365-powershell.md)
    
- [Office 365 PowerShell을 사용 하 여 사용자 계정에 라이선스를 할당 합니다.](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [Office 365 PowerShell을 사용 하 여 사용자 계정에서 라이센스를 제거 합니다.](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
이 항목에서 사용된 cmdlet에 대한 자세한 내용은 다음 항목을 참조하십시오.
  
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [Remove-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691636)
    
- [Restore-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691637)
    
- [New-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/new-azureaduser?view=azureadps-2.0)
    

