---
title: "블록 사용자 계정 Office 365 PowerShell을 사용 하 여"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/10/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- PowerShell
ms.assetid: 04e58c2a-400b-496a-acd4-8ec5d37236dc
description: "Office 365 PowerShell을 사용 하 여 차단 하 고 Office 365 계정에 대 한 액세스를 차단 해제 하는 방법에 설명 합니다."
ms.openlocfilehash: 34d144c982210ddc9d557b6094f71706f8edbb7f
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2018
---
# <a name="block-user-accounts-with-office-365-powershell"></a>블록 사용자 계정 Office 365 PowerShell을 사용 하 여

**요약:**  Office 365 PowerShell을 사용 하 여 차단 하 고 Office 365 계정에 대 한 액세스를 차단 해제 하는 방법에 설명 합니다.
  
Office 365 계정에 대 한 액세스를 차단에 로그인 하 고 서비스 및 Office 365 조직에서 데이터에 액세스 하는 계정을 사용 하 여에서 시킬 수 없습니다. 계정에 대 한 액세스를 차단 하면 차단 하는 경우 사용자는 다음과 같은 오류 메시지가에 로그인 하려고 할 때:
  
![차단된 Office 365 계정](images/o365_powershell_account_blocked.png)
  
Office 365 PowerShell을 사용 하 여 여러 사용자 계정 및 개별에 대 한 액세스를 차단 하 수 있습니다.
  
## <a name="before-you-begin"></a>시작하기 전에

- 이 항목의 절차를 수행하려면 Office 365 PowerShell에 연결되어 있어야 합니다. 지침을 보려면 [PowerShell Office 365에 연결](connect-to-office-365-powershell.md)을 참조하세요.
    
- 사용자 계정, 차단 하는 경우에 모든 사용자의 장치 및 클라이언트에 영향을 24 시간 까지도 걸릴 수 있습니다.
    
## <a name="use-office-365-powershell-to-block-access-to-individual-user-accounts"></a>사용 하 여 Office 365 PowerShell 개별 사용자 계정에 대 한 액세스를 차단 하려면

개별 사용자 계정에 대 한 액세스를 차단 하려면 다음 구문을 사용 합니다.
  
```
Set-MsolUser -UserPrincipalName <UPN of user account>  -BlockCredential $true
```

이 예제에서는 사용할 수 없게 해당 사용자 계정이 fabricec@litwareinc.com.
  
```
Set-MsolUser -UserPrincipalName fabricec@litwareinc.com -BlockCredential $true
```

사용자 계정 차단 해제 하려면 다음 명령을 실행 합니다.
  
```
Set-MsolUser -UserPrincipalName <UPN of user account>  -BlockCredential $false
```

언제 든 지 다음 명령 사용 하 여 사용자 계정의 차단 된 상태를 확인할 수 있습니다.
  
```
Get-MolUser -UserPrincipalName <UPN of user account> | Select DisplayName,BlockCredential
```

## <a name="use-office-365-powershell-to-block-access-to-multiple-user-accounts"></a>Office 365 PowerShell을 사용 하 여 여러 사용자 계정에 대 한 액세스를 차단 하려면

먼저, 다음과 같이 각 줄에 하나의 계정이 포함 된 텍스트 파일을 만듭니다.
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```
다음 명령 예제 텍스트 파일 C:\My Documents\Accounts.txt를입니다. 텍스트 파일의 경로 파일 이름으로 대체 합니다.
    
텍스트 파일에 나열 된 계정에 대 한 액세스를 차단 하려면 다음 명령을 실행 합니다.
    
  ```
  Get-Content Accounts.txt | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $true }
  ```
텍스트 파일에 나열 된 계정 차단 해제 하려면 다음 명령을 실행 합니다.
    
  ```
  Get-Content Accounts.txt | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $false }
  ```

## <a name="use-the-azure-active-directory-v2-powershell-module-to-block-access-to-user-accounts"></a>Azure Active Directory V2 PowerShell 모듈을 사용하여 사용자 계정 액세스 차단

Azure Active Directory V2 PowerShell 모듈에서 **New-AzureADUser** cmdlet을 사용하려면 먼저 구독에 연결해야 합니다. 지침은[Azure Active Directory V2 PowerShell 모듈을 사용하여 연결](https://go.microsoft.com/fwlink/?linkid=842218)을 참조하세요.
  
연결한 후 다음 구문을 사용하여 개별 사용자 계정을 차단합니다.
  
```
Set-AzureADUser -ObjectID <UPN of user account> -AccountEnabled $false
```

> [!NOTE]
> Set-AzureAD cmdlet의 -ObjectID 매개 변수는 사용자 계정 이름으로도 알려진 계정 이름이나 계정의 개체 ID를 허용합니다. 
  
이 예제에서는 사용할 수 없게 해당 사용자 계정이 fabricec@litwareinc.com.
  
```
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $false
```

사용자 계정을 차단 해제하려면 다음 명령을 실행합니다.
  
```
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $true
```

UPN 사용자의 표시 이름에 따라 사용자 계정으로 표시 하려면 다음 명령을 사용 합니다.
  
```
$userName="<user account display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName

```

Caleb Sills 라는 사용자에 대 한 사용자 계정의 UPN을 표시 하는이 예제입니다.
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

사용자 이름을 기준으로 계정을 차단하려면 다음 명령을 사용합니다.
  
```
$userName="<user account display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

언제 든 지 다음 명령 사용 하 여 사용자 계정의 차단 된 상태를 확인할 수 있습니다.
  
```
Get-AzureADUser -UserPrincipalName <UPN of user account> | Select DisplayName,AccountEnabled
```

여러 사용자 계정에 대 한 액세스를 차단 하려면 다음과 같이 각 줄에 하나의 계정 이름을 포함 하는 텍스트 파일을 만듭니다.
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

다음 명령 예제 텍스트 파일 C:\My Documents\Accounts.txt를입니다. 텍스트 파일의 경로 파일 이름으로 대체 합니다.
    
텍스트 파일에 나열 된 계정에 대 한 액세스를 차단 하려면 다음 명령을 실행 합니다.
    
```
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $false }
```

텍스트 파일에 나열 된 계정 차단 해제 하려면 다음 명령을 실행 합니다.
    
```
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $true }
```

## <a name="see-also"></a>참고 항목
<a name="SeeAlso"> </a>

Office 365 PowerShell을 사용하여 사용자를 관리하는 방법에 대한 다음 추가 항목을 참조하세요.
  
- [Office 365 PowerShell을 사용 하 여 사용자 계정 만들기](create-user-accounts-with-office-365-powershell.md)
    
- [삭제 한 사용자 계정 Office 365 PowerShell을 사용 하 여 복원 합니다.](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Office 365 PowerShell을 사용 하 여 사용자 계정에 라이선스를 할당 합니다.](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [Office 365 PowerShell을 사용 하 여 사용자 계정에서 라이센스를 제거 합니다.](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
이 항목에서 사용된 cmdlet에 대한 자세한 내용은 다음 항목을 참조하십시오.
  
- [Get-content](https://go.microsoft.com/fwlink/p/?LinkId=113310)
    
- [이와](https://go.microsoft.com/fwlink/p/?LinkId=691644)
    
- [New-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/new-azureaduser?view=azureadps-2.0)
    

