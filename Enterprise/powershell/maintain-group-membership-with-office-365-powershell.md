---
title: Office 365 PowerShell을 사용 하 여 그룹 구성원 자격 유지 관리
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/06/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- O365ITProTrain
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: Office 365 PowerShell을 사용 하 여 Office 365의 그룹 멤버 자격을 유지 하는 방법을 알아봅니다.
ms.openlocfilehash: e7cd4cb76f28bfbe2e1bc538df6727ac403c29df
ms.sourcegitcommit: 3539ec707f984de6f3b874744ff8b6832fbd665e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/17/2019
ms.locfileid: "40072500"
---
# <a name="maintain-group-membership-with-office-365-powershell"></a>Office 365 PowerShell을 사용 하 여 그룹 구성원 자격 유지 관리

Microsoft 365 관리 센터 대신 Office 365 PowerShell을 사용 하 여 Office 365에서 그룹 구성원 자격을 유지 관리할 수 있습니다. 

> [!TIP]
> 사용자 계정 및 그룹 이름을 지정 하 여 실행 가능한 PowerShell 명령을 생성 하려면이 [그룹 유지 관리 Microsoft Excel 통합 문서](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/maintain-group-membership-with-office-365-powershell/GroupMaintPowerShellGenerator.xlsx)를 사용 합니다. 

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Graph 모듈용 Azure Active Directory PowerShell 사용하기
먼저, [Office 365 테넌트에 연결](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)합니다.

### <a name="add-or-remove-user-accounts-as-members-of-a-group"></a>사용자 계정을 그룹의 구성원으로 추가 또는 제거

**Upn을 기준으로 사용자 계정을 추가 하려면**Upn (사용자 계정 이름)을 입력 하 고 (예: belindan@contoso.com), 그룹 표시 이름을 "<" 및 ">" 문자를 제거 하 고 powershell 창 또는 powershell ISE (통합 스크립트 환경)에서 이러한 명령을 실행 합니다.

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**표시 이름으로 사용자 계정을 추가 하려면**사용자 계정 표시 이름 (예: Belinda newman)과 그룹 표시 이름을 입력 하 고 powershell 창 또는 powershell ISE에서 다음 명령을 실행 합니다.

```powershell
$userName="<display name of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

UPN을 사용 하 **여 사용자 계정을 제거 하려면**사용자 계정 UPN (예: belindan@contoso.com)과 그룹 표시 이름을 입력 하 고 powershell 창 또는 powershell ISE에서이 명령을 실행 합니다.

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**표시 이름으로 사용자 계정을 제거 하려면**사용자 계정 표시 이름 (예: Belinda newman)과 그룹 표시 이름을 입력 하 고 powershell 창 또는 powershell ISE에서 다음 명령을 실행 합니다.

```powershell
$userName="<display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

### <a name="add-or-remove-groups-as-members-of-a-group"></a>그룹 구성원으로 그룹 추가 또는 제거

보안 그룹은 다른 그룹을 구성원으로 포함할 수 있습니다. 그러나 Office 365 그룹은 사용할 수 없습니다. 이 섹션에는 보안 그룹에 대 한 그룹만 추가 하거나 제거 하기 위한 PowerShell 명령이 포함 되어 있습니다.

**표시 이름별로 그룹을 추가 하려면**추가할 그룹의 표시 이름을 입력 하 고 구성원 그룹을 포함할 그룹의 표시 이름을 채운 다음 powershell 창 또는 powershell ISE에서이 명령을 실행 합니다.

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**표시 이름으로 그룹을 제거 하려면**제거할 그룹의 표시 이름과 구성원 그룹을 포함 하는 그룹의 표시 이름을 입력 하 고 powershell 창 또는 powershell ISE에서이 명령을 실행 합니다.

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Windows PowerShell용 Microsoft Azure Active Directory 모듈 사용하기

먼저, [Office 365 테넌트에 연결](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)합니다.


### <a name="add-or-remove-user-accounts-as-members-of-a-group"></a>사용자 계정을 그룹의 구성원으로 추가 또는 제거

**Upn을 기준으로 사용자 계정을 추가 하려면**Upn (사용자 계정 이름)을 입력 하 고 (예: belindan@contoso.com), 그룹 표시 이름을 "<" 및 ">" 문자를 제거 하 고 powershell 창 또는 powershell ISE에서이 명령을 실행 합니다.

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**표시 이름으로 사용자 계정을 추가 하려면**사용자 계정 표시 이름 (예: Belinda newman)과 그룹 표시 이름을 입력 하 고 powershell 창 또는 powershell ISE에서 다음 명령을 실행 합니다.

```powershell
$userName="<display name of the user account to add>"
$groupName="<display name of the group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.DisplayName -eq $userName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

UPN을 사용 하 **여 사용자 계정을 제거 하려면**사용자 계정 UPN (예: belindan@contoso.com)과 그룹 표시 이름을 입력 하 고 powershell 창 또는 powershell ISE에서이 명령을 실행 합니다.

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**표시 이름으로 사용자 계정을 제거 하려면**사용자 계정 표시 이름 (예: Belinda newman)과 그룹 표시 이름을 입력 하 고 powershell 창 또는 powershell ISE에서 다음 명령을 실행 합니다.

```powershell
$userName="<display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.DisplayName -eq $userName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

### <a name="add-or-remove-groups-as-members-of-a-group"></a>그룹 구성원으로 그룹 추가 또는 제거

보안 그룹은 다른 그룹을 구성원으로 포함할 수 있습니다. 그러나 Office 365 그룹은 사용할 수 없습니다. 이 섹션에는 보안 그룹에 대 한 그룹만 추가 하거나 제거 하기 위한 PowerShell 명령이 포함 되어 있습니다.

**표시 이름별로 그룹을 추가 하려면**추가할 그룹의 표시 이름을 입력 하 고 구성원 그룹을 포함할 그룹의 표시 이름을 채운 다음 powershell 창 또는 powershell ISE에서이 명령을 실행 합니다.

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID -GroupMemberType Group
```

**표시 이름으로 그룹을 제거 하려면**제거할 그룹의 표시 이름과 구성원 그룹을 포함 하는 그룹의 표시 이름을 입력 하 고 powershell 창 또는 powershell ISE에서이 명령을 실행 합니다.

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group contains the member group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID -GroupMemberType Group
```

## <a name="see-also"></a>참고 항목

[Office 365 PowerShell을 사용 하 여 사용자 계정, 라이선스 및 그룹 관리](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Office 365 PowerShell을 사용하여 Office 365 관리](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell 시작](getting-started-with-office-365-powershell.md)

