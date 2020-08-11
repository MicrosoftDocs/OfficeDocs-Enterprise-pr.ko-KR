---
title: PowerShell을 사용 하 여 Microsoft 365 사용자 계정 차단
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/16/2020
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
- Ent_Office_Other
- PowerShell
- seo-marvel-apr2020
ms.assetid: 04e58c2a-400b-496a-acd4-8ec5d37236dc
description: 이 문서에서는 PowerShell을 사용 하 여 Microsoft 365 계정에 대 한 액세스를 차단 및 차단 해제 하는 방법을 설명 합니다.
ms.openlocfilehash: 1d32554642f29b4548e2525135d20967ba6b0f16
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606434"
---
# <a name="block-microsoft-365-user-accounts-with-powershell"></a>PowerShell을 사용 하 여 Microsoft 365 사용자 계정 차단

*이 문서는 Microsoft 365 Enterprise와 Office 365 Enterprise에 모두 적용됩니다.*

Microsoft 365 계정에 대 한 액세스를 차단 하면 사용자가 계정을 사용 하 여 Microsoft 365 조직의 서비스 및 데이터에 로그인 하 고 액세스할 수 없습니다. PowerShell을 사용 하 여 개별 및 여러 사용자 계정에 대 한 액세스를 차단할 수 있습니다.

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Graph 모듈용 Azure Active Directory PowerShell 사용하기

먼저 [Microsoft 365 테 넌 트에 연결](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)합니다.
 
### <a name="block-access-to-individual-user-accounts"></a>개별 사용자 계정에 대 한 액세스 차단

개별 사용자 계정을 차단 하려면 다음 구문을 사용 합니다.
  
```powershell
Set-AzureADUser -ObjectID <sign-in name of the user account> -AccountEnabled $false
```

> [!NOTE]
> AzureAD cmdlet의-ObjectID 매개 변수는 사용자 보안 주체 이름이 라고도 하는 계정 로그인 이름 또는 계정의 개체 ID를 허용 합니다. 
  
이 예제에서는 사용할 수 없게 해당 사용자 계정이 fabricec@litwareinc.com.
  
```powershell
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $false
```

사용자 계정을 차단 해제하려면 다음 명령을 실행합니다.
  
```powershell
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $true
```

사용자의 표시 이름을 기준으로 사용자 계정 UPN을 표시 하려면 다음 명령을 사용 합니다.
  
```powershell
$userName="<display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName

```

이 예에서는 Caleb 창턱 라는 사용자에 대 한 사용자 계정 UPN을 표시 합니다.
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

사용자의 표시 이름을 기준으로 계정을 차단 하려면 다음 명령을 사용 합니다.
  
```powershell
$userName="<display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

언제 든 지 다음 명령을 사용 하 여 사용자 계정의 차단 된 상태를 확인할 수 있습니다.
  
```powershell
Get-AzureADUser -UserPrincipalName <UPN of user account> | Select DisplayName,AccountEnabled
```

### <a name="block-access-to-multiple-user-accounts"></a>여러 사용자 계정에 대 한 액세스 차단

여러 사용자 계정에 대 한 액세스를 차단 하려면 다음과 같은 각 줄에 계정 로그인 이름이 하나씩 포함 된 텍스트 파일을 만듭니다.
    
  ```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

다음 명령에서는 예제 텍스트 파일을 C:\My Documents\Accounts.txt 합니다. 텍스트 파일의 경로 및 파일 이름으로 바꿉니다.
  
텍스트 파일에 나열 된 계정에 대 한 액세스를 차단 하려면 다음 명령을 실행 합니다.
    
```powershell
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $false }
```

텍스트 파일에 나열 된 계정 차단 해제 하려면 다음 명령을 실행 합니다.
    
```powershell
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $true }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Windows PowerShell용 Microsoft Azure Active Directory 모듈 사용하기

먼저 [Microsoft 365 테 넌 트에 연결](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)합니다.
    
### <a name="block-access-to-individual-user-accounts"></a>개별 사용자 계정에 대 한 액세스 차단

개별 사용자 계정에 대 한 액세스를 차단 하려면 다음 구문을 사용 합니다.
  
```powershell
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $true
```

>[!Note]
>PowerShell Core는 Windows PowerShell용 Microsoft Azure Active Directory 모듈 및 이름에 **Msol**이 있는 cmdlet을 지원하지 않습니다. 이러한 cmdlet을 계속 사용하려면 Windows PowerShell에서 이를 실행해야 합니다.
>

이 예제에서는 사용할 수 없게 해당 사용자 계정이 fabricec@litwareinc.com.
  
```powershell
Set-MsolUser -UserPrincipalName fabricec@litwareinc.com -BlockCredential $true
```

사용자 계정 차단 해제 하려면 다음 명령을 실행 합니다.
  
```powershell
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $false
```

언제 든 지 다음 명령을 사용 하 여 사용자 계정의 차단 된 상태를 확인할 수 있습니다.
  
```powershell
Get-MsolUser -UserPrincipalName <sign-in name of user account> | Select DisplayName,BlockCredential
```

### <a name="block-access-to-multiple-user-accounts"></a>여러 사용자 계정에 대 한 액세스 차단

먼저 다음과 같이 각 줄에 하나의 계정을 포함 하는 텍스트 파일을 만듭니다.
    
```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
```

다음 명령에서는 예제 텍스트 파일을 C:\My Documents\Accounts.txt 합니다. 텍스트 파일의 경로 및 파일 이름으로 바꿉니다.
    
텍스트 파일에 나열 된 계정에 대 한 액세스를 차단 하려면 다음 명령을 실행 합니다.
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $true }
  ```
텍스트 파일에 나열 된 계정 차단 해제 하려면 다음 명령을 실행 합니다.
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $false }
  ```

## <a name="see-also"></a>참고 항목

[PowerShell로 Microsoft 365 사용자 계정, 라이선스 및 그룹 관리](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[PowerShell로 Microsoft 365 관리](manage-office-365-with-office-365-powershell.md)
  
[Microsoft 365 용 PowerShell 시작](getting-started-with-office-365-powershell.md)
