---
title: Office 365 PowerShell을 사용한 사용자 계정에 역할을 할당 합니다.
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/31/2019
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- O365ITProTrain
- PowerShell
- Ent_Office_Other
ms.assetid: ede7598c-b5d5-4e3e-a488-195f02f26d93
description: '요약: Office 365 PowerShell을 사용 사용자 계정에 역할을 할당 합니다.'
ms.openlocfilehash: 702c7358ccca9bb36bd106d742b5c454283ee8b4
ms.sourcegitcommit: d0c870c7a487eda48b11f649b30e4818fd5608aa
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/01/2019
ms.locfileid: "29690439"
---
# <a name="assign-roles-to-user-accounts-with-office-365-powershell"></a>Office 365 PowerShell을 사용한 사용자 계정에 역할을 할당 합니다.

빠르고 쉽게 역할 할당할 수 있습니다를 Office 365 PowerShell을 사용 하는 사용자 계정입니다.

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Graph 모듈용 Azure Active Directory PowerShell 사용하기

첫째, [Office 365 테 넌 트에 연결](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module) 전역 관리자 계정을 사용 합니다.
  
다음으로 결정 역할에 추가 하려는 사용자 계정의 로그인 이름 (예: fredsm@contoso.com). 이 사용자 계정 이름 (UPN) 라고도 합니다.

그런 다음 역할의 이름을 결정 합니다. 이 명령을 사용 하 여 powershell 할당할 수 있는 역할을 나열 합니다.

````
Get-AzureADDirectoryRole
````

다음으로 로그인 하 고 역할 이름을 입력 하 고이 명령을 실행 합니다.
  
```
$userName="<sign-in name of the account>"
$roleName="<role name>"
Add-AzureADDirectoryRoleMember -ObjectId (Get-AzureADDirectoryRole | Where {$_.DisplayName -eq $roleName}).ObjectID -RefObjectId (Get-AzureADUser | Where {$_.UserPrincipalName -eq $userName}).ObjectID
```

완료 된 명령 집합의 예는 다음과 같습니다.
  
```
$userName="belindan@contoso.com"
$roleName="Lync Service Administrator"
Add-AzureADDirectoryRoleMember -ObjectId (Get-AzureADDirectoryRole | Where {$_.DisplayName -eq $roleName}).ObjectID -RefObjectId (Get-AzureADUser | Where {$_.UserPrincipalName -eq $userName}).ObjectID
```

특정 역할에 대 한 사용자 이름의 목록을 표시 하려면 다음이 명령을 사용 합니다.

```
$roleName="<role name>"
Get-AzureADDirectoryRole | Where { $_.DisplayName -eq $roleName } | Get-AzureADDirectoryRoleMember | Ft DisplayName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Windows PowerShell용 Microsoft Azure Active Directory 모듈 사용하기

첫째, [Office 365 테 넌 트에 연결](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) 전역 관리자 계정을 사용 합니다.
  
### <a name="for-a-single-role-change"></a>단일 역할 변경

다음 사항을 확인 해야 합니다.
  
- 구성 하려는 사용자 계정입니다.
    
    사용자 계정을 지정 하려면 해당 표시 이름에 사항을 결정 해야 합니다. 전체 목록은 계정을 가져오려면이 명령을 사용 하 여:
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    이 명령은 한번에 한 화면 표시 이름별 정렬 하 여 사용자 계정의 표시 이름을 나열 합니다. **여기서** cmdlet을 사용 하 여 더 작은 집합 목록을 필터링 할 수 있습니다. 다음은 한 예가입니다.
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    이 명령은 "John"으로 시작 되는 표시 이름을 사용자 계정만 나열 합니다.
    
- 할당 하려는 역할입니다.
    
    사용자 계정에 할당할 수 있는 사용 가능한 역할의 목록을 표시 하려면이 명령을 사용 합니다.
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

역할의 이름과 계정의 표시 이름의 확인 한 후에 계정에 역할을 할당 하려면 이러한 명령을 사용 합니다.
  
```
$dispName="<The Display Name of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

명령을 복사 하 고 메모장에 붙여넣습니다. **$DispName** 및 **$roleName** 변수에 대 한 설명 텍스트 해당 값으로 바꿉니다, 제거는 \< 및 gt_ 문자 그대로 따옴표를 입력 하 고 합니다. 수정 된 줄을 복사 하 고 실행 하 여 Windows Azure Active Directory 모듈에 대 한 Windows PowerShell 창에 붙여넣습니다. 또는 Windows PowerShell 스크립트 ISE (통합 환경)를 사용할 수 있습니다.
  
완료 된 명령 집합의 예는 다음과 같습니다.
  
```
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

### <a name="for-multiple-role-changes"></a>여러 역할 변경에 대 한

다음 사항을 확인 해야 합니다.
  
- 어떤 사용자 계정을 구성 해야 합니다.
    
    사용자 계정을 지정 하려면 해당 표시 이름에 사항을 결정 해야 합니다. 목록 계정을 가져오려면이 명령을 사용 하 여:
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    이 명령은 한번에 한 화면 표시 이름별 정렬 된 모든 사용자 계정의 표시 이름을 나열 합니다. **여기서** cmdlet을 사용 하 여 더 작은 집합 목록을 필터링 할 수 있습니다. 다음은 한 예가입니다.
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    이 명령은 "John"으로 시작 되는 표시 이름을 사용자 계정만 나열 합니다.
    
- 각 사용자 계정에 할당 하려는 되는 역할입니다.
    
    사용자 계정에 할당할 수 있는 사용 가능한 역할의 목록을 표시 하려면이 명령을 사용 합니다.
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

다음으로, DisplayName 및 역할 있는 쉼표로 구분 된 값 (CSV) 텍스트 파일을 만들 필드 이름을 지정 합니다. 다음은 한 예가입니다.
  
```
DisplayName,RoleName
"Belinda Newman","Billing Administrator"
"John Doe","SharePoint Service Administrator"
"Alice Smithers","Lync Service Administrator"
```

다음으로, CSV 파일의 위치를 입력 하 고 PowerShell 명령 프롬프트에서 결과 명령을 실행 합니다.
  
```
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach {Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $_.DisplayName).UserPrincipalName -RoleName $_.RoleName }

```

## <a name="see-also"></a>참고 항목

- [Office 365 PowerShell로 사용자 계정 및 라이선스 관리](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [Office 365 PowerShell로 Office 365 관리](manage-office-365-with-office-365-powershell.md)
- [Office 365 PowerShell 시작](getting-started-with-office-365-powershell.md)
