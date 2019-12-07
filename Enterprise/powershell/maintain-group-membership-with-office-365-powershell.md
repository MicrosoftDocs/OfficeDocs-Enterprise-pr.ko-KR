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
ms.openlocfilehash: dfd3cad3f2e691930b5f4c754ee07205d3950e54
ms.sourcegitcommit: 7e65640fb1a86858a95c9ef0edbb58d0f171c5ee
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/06/2019
ms.locfileid: "39886662"
---
# <a name="maintain-group-membership-with-office-365-powershell"></a><span data-ttu-id="62317-103">Office 365 PowerShell을 사용 하 여 그룹 구성원 자격 유지 관리</span><span class="sxs-lookup"><span data-stu-id="62317-103">Maintain group membership with Office 365 PowerShell</span></span>

<span data-ttu-id="62317-104">Microsoft 365 관리 센터 대신 Office 365 PowerShell을 사용 하 여 Office 365에서 그룹 구성원 자격을 유지 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62317-104">You can use Office 365 PowerShell as an alternative to the Microsoft 365 admin center to maintain group membership in Office 365.</span></span> 

> [!TIP]
> <span data-ttu-id="62317-105">사용자 계정 및 그룹 이름을 지정 하 여 실행 가능한 PowerShell 명령을 생성 하려면이 [그룹 유지 관리 Microsoft Excel 통합 문서](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/maintain-group-membership-with-office-365-powershell/GroupMaintPowerShellGenerator.xlsx)를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="62317-105">To generate ready-to-run PowerShell commands by specifying user account and group names, use this [group maintenance Microsoft Excel workbook](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/maintain-group-membership-with-office-365-powershell/GroupMaintPowerShellGenerator.xlsx).</span></span> 

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="62317-106">Graph 모듈용 Azure Active Directory PowerShell 사용하기</span><span class="sxs-lookup"><span data-stu-id="62317-106">Use the Azure Active Directory PowerShell for Graph module</span></span>
<span data-ttu-id="62317-107">먼저, [Office 365 테넌트에 연결](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)합니다.</span><span class="sxs-lookup"><span data-stu-id="62317-107">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>

### <a name="add-or-remove-user-accounts-as-members-of-a-group"></a><span data-ttu-id="62317-108">사용자 계정을 그룹의 구성원으로 추가 또는 제거</span><span class="sxs-lookup"><span data-stu-id="62317-108">Add or remove user accounts as members of a group</span></span>

<span data-ttu-id="62317-109">**Upn을 기준으로 사용자 계정을 추가 하려면**Upn (사용자 계정 이름)을 입력 하 고 (예: belindan@contoso.com), 그룹 표시 이름을 "<" 및 ">" 문자를 제거 하 고 powershell 창 또는 powershell ISE (통합 스크립트 환경)에서 이러한 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="62317-109">**To add a user account by its UPN**, fill in the user account User Principal Name (UPN) (example: belindan@contoso.com) and the group display name, removing the “<” and “>” characters, and run these commands in the PowerShell window or the PowerShell Integrated Script Environment (ISE).</span></span>

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="62317-110">**표시 이름으로 사용자 계정을 추가 하려면**사용자 계정 표시 이름 (예: Belinda newman)과 그룹 표시 이름을 입력 하 고 powershell 창 또는 powershell ISE에서 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="62317-110">**To add a user account by its display name**, fill in the user account display name (example: Belinda Newman) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userName="<display name of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="62317-111">UPN을 사용 하 **여 사용자 계정을 제거 하려면**사용자 계정 UPN (예: belindan@contoso.com)과 그룹 표시 이름을 입력 하 고 powershell 창 또는 powershell ISE에서이 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="62317-111">**To remove a user account by its UPN**, fill in the user account UPN (example: belindan@contoso.com) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="62317-112">**표시 이름으로 사용자 계정을 제거 하려면**사용자 계정 표시 이름 (예: Belinda newman)과 그룹 표시 이름을 입력 하 고 powershell 창 또는 powershell ISE에서 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="62317-112">**To remove a user account by its display name**, fill in the user account display name (example: Belinda Newman) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userName="<display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

### <a name="add-or-remove-groups-as-members-of-a-group"></a><span data-ttu-id="62317-113">그룹 구성원으로 그룹 추가 또는 제거</span><span class="sxs-lookup"><span data-stu-id="62317-113">Add or remove groups as members of a group</span></span>

<span data-ttu-id="62317-114">보안 그룹은 다른 그룹을 구성원으로 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62317-114">Security groups can contain other groups as members.</span></span> <span data-ttu-id="62317-115">그러나 Office 365 그룹은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="62317-115">Office 365 groups, however, cannot.</span></span> <span data-ttu-id="62317-116">이 섹션에는 보안 그룹에 대 한 그룹만 추가 하거나 제거 하기 위한 PowerShell 명령이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62317-116">This section contains PowerShell commands to add or remove groups only for a security group.</span></span>

<span data-ttu-id="62317-117">**표시 이름별로 그룹을 추가 하려면**추가할 그룹의 표시 이름을 입력 하 고 구성원 그룹을 포함할 그룹의 표시 이름을 채운 다음 powershell 창 또는 powershell ISE에서이 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="62317-117">**To add a group by its display name**, fill in the display name of the group you’re going to add and the display name of the group that will contain the member group and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="62317-118">**표시 이름으로 그룹을 제거 하려면**제거할 그룹의 표시 이름과 구성원 그룹을 포함 하는 그룹의 표시 이름을 입력 하 고 powershell 창 또는 powershell ISE에서이 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="62317-118">**To remove a group by its display name**, fill in the display name of the group you’re going to remove and the display name of the group that will contain the member group and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="62317-119">Windows PowerShell용 Microsoft Azure Active Directory 모듈 사용하기</span><span class="sxs-lookup"><span data-stu-id="62317-119">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="62317-120">먼저, [Office 365 테넌트에 연결](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)합니다.</span><span class="sxs-lookup"><span data-stu-id="62317-120">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>


### <a name="add-or-remove-user-accounts-as-members-of-a-group"></a><span data-ttu-id="62317-121">사용자 계정을 그룹의 구성원으로 추가 또는 제거</span><span class="sxs-lookup"><span data-stu-id="62317-121">Add or remove user accounts as members of a group</span></span>

<span data-ttu-id="62317-122">**Upn을 기준으로 사용자 계정을 추가 하려면**Upn (사용자 계정 이름)을 입력 하 고 (예: belindan@contoso.com), 그룹 표시 이름을 "<" 및 ">" 문자를 제거 하 고 powershell 창 또는 powershell ISE에서이 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="62317-122">**To add a user account by its UPN**, fill in the user account User Principal Name (UPN) (example: belindan@contoso.com) and the group display name, removing the “<” and “>” characters, and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="62317-123">**표시 이름으로 사용자 계정을 추가 하려면**사용자 계정 표시 이름 (예: Belinda newman)과 그룹 표시 이름을 입력 하 고 powershell 창 또는 powershell ISE에서 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="62317-123">**To add a user account by its display name**, fill in the user account display name (example: Belinda Newman) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userName="<display name of the user account to add>"
$groupName="<display name of the group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.DisplayName -eq $userName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="62317-124">UPN을 사용 하 **여 사용자 계정을 제거 하려면**사용자 계정 UPN (예: belindan@contoso.com)과 그룹 표시 이름을 입력 하 고 powershell 창 또는 powershell ISE에서이 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="62317-124">**To remove a user account by its UPN**, fill in the user account UPN (example: belindan@contoso.com) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="62317-125">**표시 이름으로 사용자 계정을 제거 하려면**사용자 계정 표시 이름 (예: Belinda newman)과 그룹 표시 이름을 입력 하 고 powershell 창 또는 powershell ISE에서 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="62317-125">**To remove a user account by its display name**, fill in the user account display name (example: Belinda Newman) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userName="<display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.DisplayName -eq $userName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

### <a name="add-or-remove-groups-as-members-of-a-group"></a><span data-ttu-id="62317-126">그룹 구성원으로 그룹 추가 또는 제거</span><span class="sxs-lookup"><span data-stu-id="62317-126">Add or remove groups as members of a group</span></span>

<span data-ttu-id="62317-127">보안 그룹은 다른 그룹을 구성원으로 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62317-127">Security groups can contain other groups as members.</span></span> <span data-ttu-id="62317-128">그러나 Office 365 그룹은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="62317-128">Office 365 groups, however, cannot.</span></span> <span data-ttu-id="62317-129">이 섹션에는 보안 그룹에 대 한 그룹만 추가 하거나 제거 하기 위한 PowerShell 명령이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62317-129">This section contains PowerShell commands to add or remove groups only for a security group.</span></span>

<span data-ttu-id="62317-130">**표시 이름별로 그룹을 추가 하려면**추가할 그룹의 표시 이름을 입력 하 고 구성원 그룹을 포함할 그룹의 표시 이름을 채운 다음 powershell 창 또는 powershell ISE에서이 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="62317-130">**To add a group by its display name**, fill in the display name of the group you’re going to add and the display name of the group that will contain the member group and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID -GroupMemberType Group
```

<span data-ttu-id="62317-131">**표시 이름으로 그룹을 제거 하려면**제거할 그룹의 표시 이름과 구성원 그룹을 포함 하는 그룹의 표시 이름을 입력 하 고 powershell 창 또는 powershell ISE에서이 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="62317-131">**To remove a group by its display name**, fill in the display name of the group you’re going to remove and the display name of the group that will contain the member group and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group contains the member group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID -GroupMemberType Group
```

## <a name="see-also"></a><span data-ttu-id="62317-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="62317-132">See also</span></span>

[<span data-ttu-id="62317-133">Office 365 PowerShell로 사용자 계정 및 라이선스 관리</span><span class="sxs-lookup"><span data-stu-id="62317-133">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="62317-134">Office 365 PowerShell 사용한 Office 365 관리</span><span class="sxs-lookup"><span data-stu-id="62317-134">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="62317-135">Office 365 PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="62317-135">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

