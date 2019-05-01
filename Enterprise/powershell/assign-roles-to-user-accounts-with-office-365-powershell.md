---
title: Office 365 PowerShell을 사용한 사용자 계정에 역할을 할당 합니다.
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/18/2019
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
description: '요약: Office 365 PowerShell을 사용 하 여 사용자 계정에 역할을 할당 합니다.'
ms.openlocfilehash: 78f2e08df6d46588b93dc217d0e16b7c3a350a88
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/30/2019
ms.locfileid: "33491994"
---
# <a name="assign-roles-to-user-accounts-with-office-365-powershell"></a>Office 365 PowerShell을 사용한 사용자 계정에 역할을 할당 합니다.

Office 365 PowerShell을 사용 하 여 사용자 계정에 쉽고 빠르게 역할을 할당할 수 있습니다.

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Graph 모듈용 Azure Active Directory PowerShell 사용하기

먼저 전역 관리자 계정을 사용 하 여 [Office 365 테 넌 트에 연결](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module) 합니다.
  
다음으로, 역할에 추가 하려는 사용자 계정의 로그인 이름 (예: fredsm@contoso.com)을 확인 합니다. 이를 UPN (사용자 계정 이름)이 라고도 합니다.

다음으로, 역할 이름을 확인 합니다. 이 [관리자 역할 권한 목록을 Azure Active Directory에서](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles)사용 합니다.

>[!Note]
>이 문서의 참고 사항에 주의 하십시오. 일부 역할 이름은 Azure AD PowerShell에 따라 다릅니다. 예를 들어 Microsoft 365 관리 센터의 "sharepoint 관리자" 역할에는 Azure AD PowerShell에 대 한 "sharepoint Service 관리자" 라는 이름이 지정 됩니다.
>

다음으로, 로그인 및 역할 이름을 입력 하 고 다음 명령을 실행 합니다.
  
```
$userName="<sign-in name of the account>"
$roleName="<role name>"
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
if ($role -eq $null) {
$roleTemplate = Get-AzureADDirectoryRoleTemplate | Where {$_.displayName -eq $roleName}
Enable-AzureADDirectoryRole -RoleTemplateId $roleTemplate.ObjectId
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
}
Add-AzureADDirectoryRoleMember -ObjectId $role.ObjectId -RefObjectId (Get-AzureADUser | Where {$_.UserPrincipalName -eq $userName}).ObjectID
```

다음은 완성 된 명령 집합의 예입니다.
  
```
$userName="belindan@contoso.com"
$roleName="SharePoint Service Administrator"
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
if ($role -eq $null) {
$roleTemplate = Get-AzureADDirectoryRoleTemplate | Where {$_.displayName -eq $roleName}
Enable-AzureADDirectoryRole -RoleTemplateId $roleTemplate.ObjectId
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
}
Add-AzureADDirectoryRoleMember -ObjectId $role.ObjectId -RefObjectId (Get-AzureADUser | Where {$_.UserPrincipalName -eq $userName}).ObjectID
```

특정 역할에 대 한 사용자 이름 목록을 표시 하려면 다음 명령을 사용 합니다.

```
$roleName="<role name>"
Get-AzureADDirectoryRole | Where { $_.DisplayName -eq $roleName } | Get-AzureADDirectoryRoleMember | Ft DisplayName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Windows PowerShell용 Microsoft Azure Active Directory 모듈 사용하기

먼저 전역 관리자 계정을 사용 하 여 [Office 365 테 넌 트에 연결](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) 합니다.
  
### <a name="for-a-single-role-change"></a>단일 역할 변경의 경우

다음을 확인합니다.
  
- 구성 하려는 사용자 계정입니다.
    
    사용자 계정을 지정 하려면 해당 표시 이름을 결정 해야 합니다. 전체 목록 계정을 가져오려면 다음 명령을 사용 합니다.
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    이 명령은 표시 이름별로 정렬 된 사용자 계정의 표시 이름을 한 번에 하나씩 나열 합니다. **Where** cmdlet을 사용 하 여 목록을 더 작은 집합으로 필터링 할 수 있습니다. 예를 들면 다음과 같습니다.
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    이 명령은 표시 이름이 "John"으로 시작 하는 사용자 계정만 나열 합니다.
    
- 할당 하려는 역할입니다.
    
    사용자 계정에 할당할 수 있는 사용 가능한 역할 목록을 표시 하려면 다음 명령을 사용 합니다.
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

계정의 표시 이름과 역할 이름을 확인 한 후에는 다음 명령을 사용 하 여 계정에 역할을 할당 합니다.
  
```
$dispName="<The Display Name of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

명령을 복사 하 여 메모장에 붙여 넣습니다. **$dispName** 및 **$roleName** 변수의 경우 설명 텍스트를 해당 값으로 바꾸고, \< 및 > 문자를 제거 하 고, 따옴표를 남겨 두어야 합니다. 수정 된 줄을 복사 하 여 windows PowerShell 용 windows Azure Active Directory 모듈 창에 붙여 넣어 실행 합니다. 또는 Windows PowerShell ISE (통합 스크립트 환경)를 사용할 수 있습니다.
  
다음은 완성 된 명령 집합의 예입니다.
  
```
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

### <a name="for-multiple-role-changes"></a>여러 역할 변경의 경우

다음을 확인합니다.
  
- 구성 하려는 사용자 계정
    
    사용자 계정을 지정 하려면 해당 표시 이름을 결정 해야 합니다. 목록 계정을 가져오려면 다음 명령을 사용 합니다.
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    이 명령은 표시 이름별로 정렬 된 모든 사용자 계정의 표시 이름을 한 번에 한 화면씩 나열 합니다. **Where** cmdlet을 사용 하 여 목록을 더 작은 집합으로 필터링 할 수 있습니다. 예를 들면 다음과 같습니다.
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    이 명령은 표시 이름이 "John"으로 시작 하는 사용자 계정만 나열 합니다.
    
- 각 사용자 계정에 할당 하려는 역할
    
    사용자 계정에 할당할 수 있는 사용 가능한 역할 목록을 표시 하려면 다음 명령을 사용 합니다.
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

다음으로 DisplayName 및 role Name 필드가 있는 CSV (쉼표로 구분 된 값) 텍스트 파일을 만듭니다. 예를 들면 다음과 같습니다.
  
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
- [Office 365 PowerShell을 사용하여 Office 365 관리](manage-office-365-with-office-365-powershell.md)
- [Office 365 PowerShell 시작](getting-started-with-office-365-powershell.md)
