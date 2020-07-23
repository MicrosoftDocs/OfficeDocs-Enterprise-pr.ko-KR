---
title: PowerShell을 사용 하 여 Microsoft 365 그룹 구성원 유지 관리
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
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: PowerShell을 사용 하 여 Microsoft 365 그룹의 멤버 자격을 유지 하는 방법을 알아봅니다.
ms.openlocfilehash: f75587c9c50a1fce3a5abfb00ddba2845318e9c4
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230654"
---
# <a name="maintain-microsoft-365-group-membership-with-powershell"></a><span data-ttu-id="49875-103">PowerShell을 사용 하 여 Microsoft 365 그룹 구성원 유지 관리</span><span class="sxs-lookup"><span data-stu-id="49875-103">Maintain Microsoft 365 group membership with PowerShell</span></span>

<span data-ttu-id="49875-104">*이 문서는 Microsoft 365 Enterprise 및 Office 365 Enterprise에 모두 적용 됩니다.*</span><span class="sxs-lookup"><span data-stu-id="49875-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="49875-105">Microsoft 365 관리 센터 대신 microsoft 365 용 PowerShell을 사용 하 여 Microsoft 365의 그룹 구성원 자격을 유지 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49875-105">You can use PowerShell for Microsoft 365 as an alternative to the Microsoft 365 admin center to maintain group membership in Microsoft 365.</span></span> 

> [!TIP]
> <span data-ttu-id="49875-106">사용자 계정 및 그룹 이름을 지정 하 여 실행 가능한 PowerShell 명령을 생성 하려면이 [그룹 유지 관리 Microsoft Excel 통합 문서](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/maintain-group-membership-with-office-365-powershell/GroupMaintPowerShellGenerator.xlsx)를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="49875-106">To generate ready-to-run PowerShell commands by specifying user account and group names, use this [group maintenance Microsoft Excel workbook](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/maintain-group-membership-with-office-365-powershell/GroupMaintPowerShellGenerator.xlsx).</span></span> 

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="49875-107">Graph 모듈용 Azure Active Directory PowerShell 사용하기</span><span class="sxs-lookup"><span data-stu-id="49875-107">Use the Azure Active Directory PowerShell for Graph module</span></span>
<span data-ttu-id="49875-108">먼저 [Microsoft 365 테 넌 트에 연결](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)합니다.</span><span class="sxs-lookup"><span data-stu-id="49875-108">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>

### <a name="add-or-remove-user-accounts-as-members-of-a-group"></a><span data-ttu-id="49875-109">사용자 계정을 그룹의 구성원으로 추가 또는 제거</span><span class="sxs-lookup"><span data-stu-id="49875-109">Add or remove user accounts as members of a group</span></span>

<span data-ttu-id="49875-110">**Upn을 기준으로 사용자 계정을 추가 하려면**Upn (사용자 계정 이름)을 입력 하 고 (예: belindan@contoso.com), 그룹 표시 이름을 "<" 및 ">" 문자를 제거 하 고 powershell 창 또는 powershell ISE (통합 스크립트 환경)에서 이러한 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="49875-110">**To add a user account by its UPN**, fill in the user account User Principal Name (UPN) (example: belindan@contoso.com) and the group display name, removing the “<” and “>” characters, and run these commands in the PowerShell window or the PowerShell Integrated Script Environment (ISE).</span></span>

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="49875-111">**표시 이름으로 사용자 계정을 추가 하려면**사용자 계정 표시 이름 (예: Belinda newman)과 그룹 표시 이름을 입력 하 고 powershell 창 또는 powershell ISE에서 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="49875-111">**To add a user account by its display name**, fill in the user account display name (example: Belinda Newman) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userName="<display name of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="49875-112">UPN을 사용 하 **여 사용자 계정을 제거 하려면**사용자 계정 UPN (예: belindan@contoso.com)과 그룹 표시 이름을 입력 하 고 powershell 창 또는 powershell ISE에서이 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="49875-112">**To remove a user account by its UPN**, fill in the user account UPN (example: belindan@contoso.com) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="49875-113">**표시 이름으로 사용자 계정을 제거 하려면**사용자 계정 표시 이름 (예: Belinda newman)과 그룹 표시 이름을 입력 하 고 powershell 창 또는 powershell ISE에서 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="49875-113">**To remove a user account by its display name**, fill in the user account display name (example: Belinda Newman) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userName="<display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

### <a name="add-or-remove-groups-as-members-of-a-group"></a><span data-ttu-id="49875-114">그룹 구성원으로 그룹 추가 또는 제거</span><span class="sxs-lookup"><span data-stu-id="49875-114">Add or remove groups as members of a group</span></span>

<span data-ttu-id="49875-115">보안 그룹은 다른 그룹을 구성원으로 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49875-115">Security groups can contain other groups as members.</span></span> <span data-ttu-id="49875-116">그러나 Microsoft 365 그룹은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="49875-116">Microsoft 365 groups, however, cannot.</span></span> <span data-ttu-id="49875-117">이 섹션에는 보안 그룹에 대 한 그룹만 추가 하거나 제거 하기 위한 PowerShell 명령이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49875-117">This section contains PowerShell commands to add or remove groups only for a security group.</span></span>

<span data-ttu-id="49875-118">**표시 이름별로 그룹을 추가 하려면**추가할 그룹의 표시 이름을 입력 하 고 구성원 그룹을 포함할 그룹의 표시 이름을 채운 다음 powershell 창 또는 powershell ISE에서이 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="49875-118">**To add a group by its display name**, fill in the display name of the group you’re going to add and the display name of the group that will contain the member group and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="49875-119">**표시 이름으로 그룹을 제거 하려면**제거할 그룹의 표시 이름과 구성원 그룹을 포함 하는 그룹의 표시 이름을 입력 하 고 powershell 창 또는 powershell ISE에서이 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="49875-119">**To remove a group by its display name**, fill in the display name of the group you’re going to remove and the display name of the group that will contain the member group and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="49875-120">Windows PowerShell용 Microsoft Azure Active Directory 모듈 사용하기</span><span class="sxs-lookup"><span data-stu-id="49875-120">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="49875-121">먼저 [Microsoft 365 테 넌 트에 연결](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)합니다.</span><span class="sxs-lookup"><span data-stu-id="49875-121">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>


### <a name="add-or-remove-user-accounts-as-members-of-a-group"></a><span data-ttu-id="49875-122">사용자 계정을 그룹의 구성원으로 추가 또는 제거</span><span class="sxs-lookup"><span data-stu-id="49875-122">Add or remove user accounts as members of a group</span></span>

<span data-ttu-id="49875-123">**Upn을 기준으로 사용자 계정을 추가 하려면**Upn (사용자 계정 이름)을 입력 하 고 (예: belindan@contoso.com), 그룹 표시 이름을 "<" 및 ">" 문자를 제거 하 고 powershell 창 또는 powershell ISE에서이 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="49875-123">**To add a user account by its UPN**, fill in the user account User Principal Name (UPN) (example: belindan@contoso.com) and the group display name, removing the “<” and “>” characters, and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="49875-124">**표시 이름으로 사용자 계정을 추가 하려면**사용자 계정 표시 이름 (예: Belinda newman)과 그룹 표시 이름을 입력 하 고 powershell 창 또는 powershell ISE에서 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="49875-124">**To add a user account by its display name**, fill in the user account display name (example: Belinda Newman) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userName="<display name of the user account to add>"
$groupName="<display name of the group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.DisplayName -eq $userName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="49875-125">UPN을 사용 하 **여 사용자 계정을 제거 하려면**사용자 계정 UPN (예: belindan@contoso.com)과 그룹 표시 이름을 입력 하 고 powershell 창 또는 powershell ISE에서이 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="49875-125">**To remove a user account by its UPN**, fill in the user account UPN (example: belindan@contoso.com) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="49875-126">**표시 이름으로 사용자 계정을 제거 하려면**사용자 계정 표시 이름 (예: Belinda newman)과 그룹 표시 이름을 입력 하 고 powershell 창 또는 powershell ISE에서 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="49875-126">**To remove a user account by its display name**, fill in the user account display name (example: Belinda Newman) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userName="<display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.DisplayName -eq $userName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

### <a name="add-or-remove-groups-as-members-of-a-group"></a><span data-ttu-id="49875-127">그룹 구성원으로 그룹 추가 또는 제거</span><span class="sxs-lookup"><span data-stu-id="49875-127">Add or remove groups as members of a group</span></span>

<span data-ttu-id="49875-128">보안 그룹은 다른 그룹을 구성원으로 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49875-128">Security groups can contain other groups as members.</span></span> <span data-ttu-id="49875-129">그러나 Microsoft 365 그룹은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="49875-129">Microsoft 365 groups, however, cannot.</span></span> <span data-ttu-id="49875-130">이 섹션에는 보안 그룹에 대 한 그룹만 추가 하거나 제거 하기 위한 PowerShell 명령이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49875-130">This section contains PowerShell commands to add or remove groups only for a security group.</span></span>

<span data-ttu-id="49875-131">**표시 이름별로 그룹을 추가 하려면**추가할 그룹의 표시 이름을 입력 하 고 구성원 그룹을 포함할 그룹의 표시 이름을 채운 다음 powershell 창 또는 powershell ISE에서이 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="49875-131">**To add a group by its display name**, fill in the display name of the group you’re going to add and the display name of the group that will contain the member group and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID -GroupMemberType Group
```

<span data-ttu-id="49875-132">**표시 이름으로 그룹을 제거 하려면**제거할 그룹의 표시 이름과 구성원 그룹을 포함 하는 그룹의 표시 이름을 입력 하 고 powershell 창 또는 powershell ISE에서이 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="49875-132">**To remove a group by its display name**, fill in the display name of the group you’re going to remove and the display name of the group that will contain the member group and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group contains the member group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID -GroupMemberType Group
```

## <a name="see-also"></a><span data-ttu-id="49875-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="49875-133">See also</span></span>

[<span data-ttu-id="49875-134">PowerShell을 사용 하 여 Microsoft 365 사용자 계정, 라이선스 및 그룹 관리</span><span class="sxs-lookup"><span data-stu-id="49875-134">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="49875-135">PowerShell을 사용 하 여 Microsoft 365 관리</span><span class="sxs-lookup"><span data-stu-id="49875-135">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="49875-136">Microsoft 365 용 PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="49875-136">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)

