---
title: Microsoft 365에서의 공유 제한
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.collection: SPO_Content
ms.custom: ''
localization_priority: Priority
description: Microsoft 365에서 공유를 제한하는 방법에 대해 알아봅니다.
ms.openlocfilehash: dd2705aefd4f91c4ce8773019f94acf53afea6c8
ms.sourcegitcommit: 4f465f690c6563cfa9f6029d3e7e9e3cace96671
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41658802"
---
# <a name="limit-sharing-in-microsoft-365"></a><span data-ttu-id="12bb9-103">Microsoft 365에서의 공유 제한</span><span class="sxs-lookup"><span data-stu-id="12bb9-103">Limit sharing in Microsoft 365</span></span>

<span data-ttu-id="12bb9-104">내부 공유를 완전히 비활성화하거나 사이트에서 공유 버튼을 제거할 수는 없지만 조직의 요구를 충족시키기 위해 Microsoft 365에서 공유를 제한할 수 있는 다양한 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-104">While you can't disable internal sharing entirely or remove the Share button from sites, there are a variety of ways that you can limit sharing in Microsoft 365 to meet the needs of your organization.</span></span>

<span data-ttu-id="12bb9-105">파일 공유 방법은 아래 표에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-105">The methods of sharing files are listed in the table below.</span></span> <span data-ttu-id="12bb9-106">자세한 정보를 확인하려면 **공유 방법** 열에서 해당 링크를 클릭하세요.</span><span class="sxs-lookup"><span data-stu-id="12bb9-106">Click the link in the **Sharing method** column for detailed information.</span></span>

|<span data-ttu-id="12bb9-107">공유 방법</span><span class="sxs-lookup"><span data-stu-id="12bb9-107">Sharing method</span></span>|<span data-ttu-id="12bb9-108">설명</span><span class="sxs-lookup"><span data-stu-id="12bb9-108">Description</span></span>|<span data-ttu-id="12bb9-109">제한 옵션</span><span class="sxs-lookup"><span data-stu-id="12bb9-109">Limiting options</span></span>|
|:-------------|:----------|:-------------|
|[<span data-ttu-id="12bb9-110">Office 365 그룹 또는 팀</span><span class="sxs-lookup"><span data-stu-id="12bb9-110">Office 365 group or team</span></span>](#office-365-group-or-team)|<span data-ttu-id="12bb9-111">Microsoft Teams 팀 또는 Office 365 그룹에 대한 액세스 권한을 받은 사람들은 연결된 SharePoint 사이트의 파일에 대한 편집 권한을 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-111">People granted access to a Microsoft Teams team or Office 365 group have edit access to files in the associated SharePoint site.</span></span>|<span data-ttu-id="12bb9-112">그룹 또는 팀이 비공개인 경우 팀에 대한 초대 공유는 승인을 위해 소유자에게 이동됩니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-112">If the group or team is private, sharing invitations to join the team go to the owner for approval.</span></span> <span data-ttu-id="12bb9-113">관리자는 게스트 액세스를 비활성화하여 조직 외부의 사람들이 액세스하지 못하게 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-113">Admins can disable guest access to prevent access by people from outside the organization.</span></span>|
|[<span data-ttu-id="12bb9-114">SharePoint 사이트</span><span class="sxs-lookup"><span data-stu-id="12bb9-114">SharePoint site</span></span>](#sharepoint-site)|<span data-ttu-id="12bb9-115">사람들은 소유자, 회원 또는 방문자에게 SharePoint 사이트에 대한 액세스 권한을 부여할 수 있으며 사이트의 파일에 대해 해당 수준의 액세스 권한을 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-115">People can be granted Owner, Member, or Visitor access to a SharePoint site and will have that level of access to files in the site.</span></span>|<span data-ttu-id="12bb9-116">사이트 소유자만 사이트를 공유할 수 있도록 사이트 권한을 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-116">Site permissions can be restricted so that only site owners can share the site.</span></span>|
|[<span data-ttu-id="12bb9-117">특정 사용자와 공유</span><span class="sxs-lookup"><span data-stu-id="12bb9-117">Sharing with specific people</span></span>](#sharing-with-specific-people)|<span data-ttu-id="12bb9-118">편집 권한이 있는 사이트 구성원과 사용자는 *특정 사용자* 링크를 사용하여 파일 및 폴더에 직접 권한을 부여하거나 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-118">Site members and people with edit permissions can give direct permissions to files and folders or share them by using *Specific people* links.</span></span>|<span data-ttu-id="12bb9-119">사이트 소유자만 파일 및 폴더를 공유할 수 있도록 사이트 권한을 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-119">Site permissions can be restricted so that only site owners can share files and folders.</span></span> <span data-ttu-id="12bb9-120">이 경우 사이트 구성원의 직접 액세스 및 *특정 사용자* 링크 공유는 소유자에게 전달되어 승인을 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-120">In this case, direct access and *Specific people* link sharing by site members goes to site owner for approval.</span></span>|
|[<span data-ttu-id="12bb9-121">SharePoint 게스트 공유</span><span class="sxs-lookup"><span data-stu-id="12bb9-121">SharePoint guest sharing</span></span>](#sharepoint-guest-sharing)|<span data-ttu-id="12bb9-122">SharePoint 사이트 소유자 및 구성원은 조직 외부의 사용자와 파일 및 폴더를 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-122">SharePoint site owners and members can share files and folders with people outside the organization.</span></span>|<span data-ttu-id="12bb9-123">전체 조직 또는 개별 사이트에 대해 게스트 공유 기능을 비활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-123">Guest sharing can be disabled for the entire organization or for individual sites.</span></span>|
|[<span data-ttu-id="12bb9-124">*조직 내부 사용자* 공유 링크</span><span class="sxs-lookup"><span data-stu-id="12bb9-124">*People in your organization* sharing links</span></span>](#people-in-your-organization-sharing-links)|<span data-ttu-id="12bb9-125">SharePoint 사이트 소유자 및 구성원은 *조직 내 사용자* 링크를 사용하여 파일을 공유할 수 있으며, 이는 조직 내부의 모든 사람이 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-125">SharePoint site owners and members can share files using *People in your organization* links, which will work for anyone inside the organization.</span></span>|<span data-ttu-id="12bb9-126">사이트 수준에서 *조직의 사용자* 링크를 비활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-126">*People in your organization* links can be disabled at the site level.</span></span>|
|[<span data-ttu-id="12bb9-127">전자 메일</span><span class="sxs-lookup"><span data-stu-id="12bb9-127">Email</span></span>](#email)|<span data-ttu-id="12bb9-128">파일에 대한 액세스 권한이 있는 사용자는 전자 메일을 통해 파일을 다른 사용자에게 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-128">People with access to a file can send it to others via email.</span></span>|<span data-ttu-id="12bb9-129">관리자는 민감도 레이블을 사용하여 파일이 권한 없는 사용자와 공유되지 않도록 파일을 암호화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-129">Admins can encrypt files by using sensitivity labels to prevent them being shared with unauthorized people.</span></span>|
|[<span data-ttu-id="12bb9-130">다운로드 또는 파일 복사</span><span class="sxs-lookup"><span data-stu-id="12bb9-130">Download or file copy</span></span>](#download-or-file-copy)|<span data-ttu-id="12bb9-131">파일에 대한 액세스 권한이 있는 사용자는 파일을 다운로드하거나 복사하여 이를 Microsoft 365 범위 밖에 있는 다른 사용자와 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-131">People with access to a file can download or copy it and share it with others outside the scope of Microsoft 365.</span></span>|<span data-ttu-id="12bb9-132">관리자는 민감도 레이블을 사용하여 파일이 권한 없는 사용자와 공유되지 않도록 파일을 암호화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-132">Admins can encrypt files by using sensitivity labels to prevent them being shared with unauthorized people.</span></span>|

<span data-ttu-id="12bb9-133">이 문서에 설명된 관리 컨트롤을 사용하여 조직의 공유를 제한할 수 있지만 Microsoft 365에서 제공되는 보안 및 규정 준수 기능을 사용하여 안전한 공유 환경을 만드는 것을 고려해 볼 것을 강력히 권장합니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-133">While you can use the admin controls described in this article to limit sharing in your organization, we highly recommend that you consider using the security and compliance features available in Microsoft 365 to create a secure sharing environment.</span></span> <span data-ttu-id="12bb9-134">자세한 내용은 [ Microsoft 365와 SharePoint의 파일 공동 작업](https://docs.microsoft.com/sharepoint/deploy-file-collaboration) 및 [엄격히 규제되는 데이터용 Teams](https://docs.microsoft.com/microsoft-365/enterprise/secure-teams-highly-regulated-data-scenario)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="12bb9-134">See [File collaboration in SharePoint with Microsoft 365](https://docs.microsoft.com/sharepoint/deploy-file-collaboration) and [Teams for highly regulated data](https://docs.microsoft.com/microsoft-365/enterprise/secure-teams-highly-regulated-data-scenario) for information.</span></span>

<span data-ttu-id="12bb9-135">조직에서 공유를 사용하는 방법을 이해하려면 [파일 및 폴더 공유에 대한 보고서를 실행하세요](https://docs.microsoft.com/sharepoint/sharing-reports).</span><span class="sxs-lookup"><span data-stu-id="12bb9-135">To understand how sharing is being used in your organization, [run a report on file and folder sharing](https://docs.microsoft.com/sharepoint/sharing-reports).</span></span>

## <a name="office-365-group-or-team"></a><span data-ttu-id="12bb9-136">Office 365 그룹 또는 팀</span><span class="sxs-lookup"><span data-stu-id="12bb9-136">Office 365 group or team</span></span>

<span data-ttu-id="12bb9-137">Office 365 그룹 또는 Microsoft Teams 팀에서 공유를 제한하려는 경우 그룹 또는 팀을 비공개로 설정하는 것이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-137">If you want to limit sharing in an Office 365 group or Microsoft Teams team, it's important to make the group or team private.</span></span> <span data-ttu-id="12bb9-138">조직 내부 사용자는 언제든 지 공용 그룹이나 팀에 참석할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-138">People inside your organization can join a public group or team anytime.</span></span> <span data-ttu-id="12bb9-139">그룹이나 팀이 비공개가 아닌 이상, 조직 내에서 팀 또는 해당 파일의 공유를 제한할 수 있는 방법이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-139">Unless the group or team is private, there's no way to limit sharing of the team or its files within the organization.</span></span>

### <a name="guest-sharing"></a><span data-ttu-id="12bb9-140">게스트 공유</span><span class="sxs-lookup"><span data-stu-id="12bb9-140">Guest sharing</span></span>

<span data-ttu-id="12bb9-141">Teams에서 게스트 액세스를 방지하려는 경우 Teams 관리 센터에서 게스트 공유를 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-141">If you want to prevent guest access in Teams, you can turn off guest sharing in the Teams admin center.</span></span>

<span data-ttu-id="12bb9-142">Teams에 대해 게스트 공유를 해제하려면</span><span class="sxs-lookup"><span data-stu-id="12bb9-142">To turn off guest sharing for Teams</span></span>
1. <span data-ttu-id="12bb9-143">Teams 관리 센터에서 **조직 전체 설정**을 확장한 다음 **게스트 액세스**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-143">In the Teams admin center, expand **Org-wide settings**, and then click **Guest access**.</span></span>
2. <span data-ttu-id="12bb9-144">**Teams에서 게스트 액세스 허용**을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-144">Turn off **Allow guest access in Teams**.</span></span>
3. <span data-ttu-id="12bb9-145">**저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-145">Click **Save**.</span></span>

<span data-ttu-id="12bb9-146">Office 365 그룹에서 게스트 액세스를 방지하려는 경우 Microsoft 365 관리 센터에서 그룹 게스트 액세스 설정을 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-146">If you want to prevent guest access in Office 365 groups, you can turn off the groups guest access settings in the Microsoft 365 admin center.</span></span>

<span data-ttu-id="12bb9-147">Office 365 그룹에서 게스트 공유를 해제하려면</span><span class="sxs-lookup"><span data-stu-id="12bb9-147">To turn off guest sharing in Office 365 groups</span></span>
1. <span data-ttu-id="12bb9-148">Microsoft 365 관리 센터에서 **설정**을 클릭한 다음 **설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-148">In the Microsoft 365 admin center, click **Settings**, and then click **Settings**.</span></span>
2. <span data-ttu-id="12bb9-149">**서비스** 탭에서 **Office 365 그룹**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-149">On the **Services** tab, click **Office 365 Groups**.</span></span>
3. <span data-ttu-id="12bb9-150">**조직 외부의 그룹 구성원이 그룹 콘텐츠에 액세스할 수 있도록 허용** 및 **그룹 소유자가 조직 외부의 사람을 그룹에 추가하도록 허용** 확인란을 선택 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-150">Clear the **Let group members outside your organization access group content** and **Let group owners add people outside your organization to groups** check boxes.</span></span>
4. <span data-ttu-id="12bb9-151">**변경 내용 저장**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-151">Click **Save changes**.</span></span>

    ![Microsoft 365 관리 센터의 Office 365 그룹 공유 설정 스크린샷](media/office-365-groups-guest-settings-off.png)

> [!NOTE]
> <span data-ttu-id="12bb9-153">특정 그룹이나 팀에 대한 게스트 공유를 방지하려는 경우 Microsoft PowerShell을 사용하여 이 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-153">If you want to prevent guest sharing for a particular group or team, you can do so by using Microsoft PowerShell.</span></span> <span data-ttu-id="12bb9-154">자세한 내용은 [특정 그룹의 게스트 사용자 차단](https://docs.microsoft.com/office365/admin/create-groups/manage-guest-access-in-groups?view=o365-worldwide#block-guest-users-from-a-specific-group)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="12bb9-154">See [Block guest users from a specific group](https://docs.microsoft.com/office365/admin/create-groups/manage-guest-access-in-groups?view=o365-worldwide#block-guest-users-from-a-specific-group) for details.</span></span>

<span data-ttu-id="12bb9-155">Azure Active Directory에서 도메인을 허용하거나 차단하여 게스트를 특정 도메인의 사용자로 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-155">You can limit guest sharing to users from specific domains by allowing or blocking domains in Azure Active Directory.</span></span> <span data-ttu-id="12bb9-156">[Azure AD B2B를 SharePoint 및 OneDrive와 통합](https://docs.microsoft.com/sharepoint/sharepoint-azureb2b-integration-preview)을 활성화한 경우 이러한 설정은 SharePoint의 게스트 공유에도 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-156">This will also affect guest sharing in SharePoint if you have enabled [SharePoint and OneDrive integration with Azure AD B2B](https://docs.microsoft.com/sharepoint/sharepoint-azureb2b-integration-preview).</span></span>

<span data-ttu-id="12bb9-157">지정된 도메인에서만 초대를 공유할 수 있도록 허용하려면</span><span class="sxs-lookup"><span data-stu-id="12bb9-157">To allow sharing invitations only from specified domains</span></span>
1. <span data-ttu-id="12bb9-158">Azure Active Directory의 개요 페이지에서 **조직 관계**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-158">In Azure Active Directory, on the Overview page, click **Organizational relationships**.</span></span>
2. <span data-ttu-id="12bb9-159">**설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-159">Click **Settings**.</span></span>
3. <span data-ttu-id="12bb9-160">**공동 작업 제한 사항**에서 **지정된 도메인에 대한 초대 거부** 또는 **지정된 도메인에 대한 초대만 허용**을 선택한 다음 사용하려는 도메인을 입력하십시오.</span><span class="sxs-lookup"><span data-stu-id="12bb9-160">Under **Collaboration restrictions**, select **Deny invitations to the specified domains** or **Allow invitations only to the specified domains**, and then type the domains that you want to use.</span></span>
4. <span data-ttu-id="12bb9-161">**저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-161">Click **Save**.</span></span>

    ![Azure Active Directory의 공동 작업 제한 설정 스크린샷](media/azure-ad-allow-only-specified-domains.png)

## <a name="sharepoint-site"></a><span data-ttu-id="12bb9-163">SharePoint 사이트</span><span class="sxs-lookup"><span data-stu-id="12bb9-163">SharePoint site</span></span>

<span data-ttu-id="12bb9-164">SharePoint 사이트 공유를 사이트 소유자에게만 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-164">You can limit SharePoint site sharing to site owners only.</span></span> <span data-ttu-id="12bb9-165">이렇게 하면 사이트 구성원이 사이트를 공유할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-165">This prevents site members from sharing the site.</span></span> <span data-ttu-id="12bb9-166">사이트가 Office 365 그룹에 연결된 경우 그룹 구성원은 다른 사람을 그룹에 초대할 수 있으며 해당 사용자는 사이트에 액세스할 수 있음을 기억하십시오.</span><span class="sxs-lookup"><span data-stu-id="12bb9-166">Keep in mind that if the site is connected to an Office 365 group, group members can invite others to the group and those users will have site access.</span></span>

<span data-ttu-id="12bb9-167">소유자에게로만 사이트 공유를 제한하려면</span><span class="sxs-lookup"><span data-stu-id="12bb9-167">To limit site sharing to owners</span></span>
1. <span data-ttu-id="12bb9-168">사이트에서 톱니바퀴 아이콘을 클릭한 다음 **사이트 권한**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-168">In the site, click the gear icon, and then click **Site permissions**.</span></span>
2. <span data-ttu-id="12bb9-169">**공유 설정**에서 **공유 설정 변경**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-169">Under **Sharing settings**, click **Change sharing settings**.</span></span>
3. <span data-ttu-id="12bb9-170">**사이트 소유자 및 구성원, 편집 권한이 있는 사용자는 파일 및 폴더를 공유할 수 있지만 사이트는 오직 사이트 소유자만 공유**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-170">Select **Site owners and members, and people with Edit permissions can share files and folders, but only site owners can share the site**.</span></span>
4. <span data-ttu-id="12bb9-171">**저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-171">Click **Save**.</span></span>

    ![SharePoint 사이트의 공유 권한 설정의 스크린샷](media/sharepoint-site-sharing-permissions-level-two.png)

<span data-ttu-id="12bb9-173">액세스 요청을 해제하여 사이트의 구성원이 아닌 사용자가 액세스를 요청하지 못하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-173">You can prevent users who are not members of the site from requesting access by turning off access requests.</span></span>

<span data-ttu-id="12bb9-174">액세스 요청을 해제하려면</span><span class="sxs-lookup"><span data-stu-id="12bb9-174">To turn off access requests</span></span>
1. <span data-ttu-id="12bb9-175">사이트에서 톱니바퀴 아이콘을 클릭한 다음 **사이트 권한**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-175">In the site, click the gear icon, and then click **Site permissions**.</span></span>
2. <span data-ttu-id="12bb9-176">**공유 설정**에서 **공유 설정 변경**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-176">Under **Sharing settings**, click **Change sharing settings**.</span></span>
3. <span data-ttu-id="12bb9-177">**액세스 요청 허용**을 해제한 다음, **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-177">Turn off **Allow access requests**, and then click **Save**.</span></span>

<span data-ttu-id="12bb9-178">사이트에 대한 도메인을 허용하거나 차단하여 사이트 공유를 특정 도메인으로 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-178">You can limit site sharing to specific domains by allowing or blocking domains for the site.</span></span>

<span data-ttu-id="12bb9-179">사이트 공유를 도메인별로 제한하려면</span><span class="sxs-lookup"><span data-stu-id="12bb9-179">To limit site sharing by domain</span></span>
1. <span data-ttu-id="12bb9-180">SharePoint 관리 센터의 **사이트**에서 **활성 사이트**를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="12bb9-180">In the SharePoint admin center, under **Sites**, click **Active sites**.</span></span>
2. <span data-ttu-id="12bb9-181">동기화할 사이트를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-181">Click the site that you want to configure.</span></span>
3. <span data-ttu-id="12bb9-182">**정책** 탭의 **외부 공유**에서 **편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-182">On the **Policies** tab, under **External sharing** click **Edit**.</span></span>
4. <span data-ttu-id="12bb9-183">**외부 공유에 대한 고급 설정**에서 **도메인별 공유 제한**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-183">Under **Advanced settings for external sharing**, select the **Limit sharing by domain**.</span></span>
5. <span data-ttu-id="12bb9-184">허용하거나 차단할 도메인을 추가하고 **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-184">Add the domains that you want to allow or block, and then click **Save**.</span></span>
6. <span data-ttu-id="12bb9-185">**저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-185">Click **Save**.</span></span>

    ![허용된 도메인 사이트 수준 설정 스크린샷](media/limit-site-sharing-by-domain.png)

## <a name="sharing-with-specific-people"></a><span data-ttu-id="12bb9-187">특정 사용자와 공유</span><span class="sxs-lookup"><span data-stu-id="12bb9-187">Sharing with specific people</span></span>

<span data-ttu-id="12bb9-188">사이트 또는 해당 콘텐츠의 공유를 제한하려는 경우 사이트 소유자만 파일, 폴더 및 사이트를 공유하도록 사이트를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-188">if you want to limit the sharing of a site or its contents, you can configure the site to only allow site owners to share files, folders, and the site.</span></span> <span data-ttu-id="12bb9-189">이러한 내용이 구성되면 사이트 구성원이 *특정 사용자* 링크를 사용하여 파일 또는 폴더를 공유하려는 시도가 승인을 위해 사이트 소유자에게 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-189">When this is configured, site members' attempts to share files or folders by using *Specific people* links will go to the site owner for approval.</span></span>

<span data-ttu-id="12bb9-190">사이트, 파일 및 폴더 공유를 소유자에게로만 제한하려면</span><span class="sxs-lookup"><span data-stu-id="12bb9-190">To limit site, file, and folder sharing to owners</span></span>
1. <span data-ttu-id="12bb9-191">사이트에서 톱니바퀴 아이콘을 클릭한 다음 **사이트 권한**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-191">In the site, click the gear icon, and then click **Site permissions**.</span></span>
2. <span data-ttu-id="12bb9-192">**공유 설정**에서 **공유 설정 변경**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-192">Under **Sharing settings**, click **Change sharing settings**.</span></span>
3. <span data-ttu-id="12bb9-193">**오직 사이트 소유자만 파일, 폴더 및 사이트를 공유**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-193">Select **Only site owners can share files, folders, and the site**.</span></span>
4. <span data-ttu-id="12bb9-194">**저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-194">Click **Save**.</span></span>

    ![SharePoint 사이트의 공유 권한 설정의 스크린샷](media/sharepoint-site-only-site-owners-can-share.png)

## <a name="sharepoint-guest-sharing"></a><span data-ttu-id="12bb9-196">SharePoint 게스트 공유</span><span class="sxs-lookup"><span data-stu-id="12bb9-196">SharePoint guest sharing</span></span>

<span data-ttu-id="12bb9-197">조직 외부 사람과 SharePoint 또는 OneDrive 파일 및 폴더를 공유하지 못하게 하려면 전체 조직 또는 개별 사이트에 대한 게스트 공유를 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-197">If you want to prevent sharing SharePoint or OneDrive files and folders with people outside your organization, you can turn off guest sharing for the entire organization or for an individual site.</span></span>

<span data-ttu-id="12bb9-198">조직에 대한 SharePoint 게스트 공유를 끄려면</span><span class="sxs-lookup"><span data-stu-id="12bb9-198">To turn off SharePoint guest sharing for your organization</span></span>
1. <span data-ttu-id="12bb9-199">SharePoint 관리 센터의 **정책**에서 **공유**를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="12bb9-199">In the SharePoint admin center, under **Policies**, click **Sharing**.</span></span>
2. <span data-ttu-id="12bb9-200">**외부 공유**에서 SharePoint 슬라이더를 아래쪽에 있는 **조직의 사용자에게만**으로 드래그합니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-200">Under **External sharing**, drag the SharePoint slider down to **Only people in your organization**.</span></span>
3. <span data-ttu-id="12bb9-201">**저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-201">Click **Save**.</span></span>

    ![SharePoint 조직 수준 공유 설정의 스크린샷](media/sharepoint-tenant-sharing-off.png)


<span data-ttu-id="12bb9-203">사이트에 대해 게스트 공유를 해제하려면</span><span class="sxs-lookup"><span data-stu-id="12bb9-203">To turn off guest sharing for a site</span></span>
1. <span data-ttu-id="12bb9-204">SharePoint 관리 센터의 **사이트**에서 **활성 사이트**를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="12bb9-204">In the SharePoint admin center, under **Sites**, click **Active sites**.</span></span>
2. <span data-ttu-id="12bb9-205">동기화할 사이트를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-205">Click the site that you want to configure.</span></span>
3. <span data-ttu-id="12bb9-206">**정책** 탭의 **외부 공유**에서 **편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-206">On the **Policies** tab, under **External sharing** click **Edit**.</span></span>
4. <span data-ttu-id="12bb9-207">**외부 공유**에서 **조직의 사용자에게만**을 선택한 다음 **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-207">Under **External sharing**, choose **Only people in your organization**, and then click **Save**.</span></span>

    ![SharePoint 사이트 수준 공유 설정 스크린샷](media/sharepoint-site-external-sharing-settings-off.png)

<span data-ttu-id="12bb9-209">조직 외부의 사람들과의 공유를 허용하지만 모든 사람이 인증을 받도록 하려면 전체 조직 또는 개별 사이트에 대해 *모든 사용자*(익명 공유) 링크를 비활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-209">If you would like to allow sharing with people outside your organization but you want to make sure that everyone authenticates, you can disable *Anyone* (anonymous sharing) links for the entire organization or for an individual site.</span></span>

<span data-ttu-id="12bb9-210">조직 수준에서 *모든 사용자* 링크를 해제하려면</span><span class="sxs-lookup"><span data-stu-id="12bb9-210">To turn off *Anyone* links at the organization level</span></span>
1. <span data-ttu-id="12bb9-211">SharePoint 관리 센터의 **정책**에서 **공유**를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="12bb9-211">In the SharePoint admin center, under **Policies**, click **Sharing**.</span></span>
2. <span data-ttu-id="12bb9-212">**외부 공유**에서 SharePoint 슬라이더를 아래쪽에 있는 **신규 및 기존 게스트**로 드래그합니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-212">Under **External sharing**, drag the SharePoint slider down to **New and existing guests**.</span></span>
3. <span data-ttu-id="12bb9-213">**저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-213">Click **Save**.</span></span>

    ![SharePoint 사이트 수준 공유 설정 스크린샷](media/sharepoint-guest-sharing-new-and-existing-guests.png)

<span data-ttu-id="12bb9-215">사이트에 대해 *Anyone* 링크를 해제하려면</span><span class="sxs-lookup"><span data-stu-id="12bb9-215">To turn off *Anyone* links for a site</span></span>
1. <span data-ttu-id="12bb9-216">SharePoint 관리 센터의 **사이트**에서 **활성 사이트**를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="12bb9-216">In the SharePoint admin center, under **Sites**, click **Active sites**.</span></span>
2. <span data-ttu-id="12bb9-217">동기화할 사이트를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-217">Click the site that you want to configure.</span></span>
3. <span data-ttu-id="12bb9-218">**정책** 탭의 **외부 공유**에서 **편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-218">On the **Policies** tab, under **External sharing** click **Edit**.</span></span>
4. <span data-ttu-id="12bb9-219">**외부 공유**에서 OneDrive에 대한 **신규 및 기존 게스트**를 선택한 다음, **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-219">Under **External sharing**, choose **New and existing guests**, and then click **Save**.</span></span>

    ![SharePoint 사이트 수준 공유 설정 스크린샷](media/sharepoint-site-external-sharing-settings-new-and-existing-guests.png)

## <a name="people-in-your-organization-sharing-links"></a><span data-ttu-id="12bb9-221">*조직 내부 사용자* 공유 링크</span><span class="sxs-lookup"><span data-stu-id="12bb9-221">*People in your organization* sharing links</span></span>

<span data-ttu-id="12bb9-222">기본적으로 사이트 회원은 *조직 내 사용자* 링크를 사용하여 조직의 다른 사람과 파일 및 폴더를 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-222">By default, members of a site can share files and folders with other people in your organization by using a *People in your organization* link.</span></span> <span data-ttu-id="12bb9-223">PowerShell을 사용하여 *조직 내 사용자* 링크를 비활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-223">You can disable *People in your organization* links by using PowerShell:</span></span>

`Set-SPOSite -Identity <site> -DisableCompanyWideSharingLinks`

<span data-ttu-id="12bb9-224">다음의 예를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="12bb9-224">For example:</span></span>

`Set-SPOSite -Identity https://contoso.sharepoint.com -DisableCompanyWideSharingLinks`

## <a name="email"></a><span data-ttu-id="12bb9-225">전자 메일</span><span class="sxs-lookup"><span data-stu-id="12bb9-225">Email</span></span>

<span data-ttu-id="12bb9-226">암호화를 사용하여 전자 메일이 의도하지 않게 공유되는 것을 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-226">You can prevent unwanted sharing of emails by using encryption.</span></span> <span data-ttu-id="12bb9-227">따라서 전자 메일이 전달되거나 허가되지 않은 사용자에게 공유되는 것을 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-227">This prevents emails being forwarded or otherwise shared with unauthorized users.</span></span> <span data-ttu-id="12bb9-228">민감도 레이블을 사용하여 전자 메일 암호화를 활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-228">Email encryption can be enabled by using sensitivity labels.</span></span> <span data-ttu-id="12bb9-229">자세한 내용은 [민감도 레이블에서 암호화를 사용하여 콘텐츠 액세스 제한](https://docs.microsoft.com/microsoft-365/compliance/encryption-sensitivity-labels)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="12bb9-229">See [Restrict access to content by using encryption in sensitivity labels](https://docs.microsoft.com/microsoft-365/compliance/encryption-sensitivity-labels) for details.</span></span>

## <a name="download-or-file-copy"></a><span data-ttu-id="12bb9-230">다운로드 또는 파일 복사</span><span class="sxs-lookup"><span data-stu-id="12bb9-230">Download or file copy</span></span>

<span data-ttu-id="12bb9-231">Microsoft 365의 파일 및 폴더에 대한 액세스 권한이 있는 사용자는 파일을 다운로드하고 외부 미디어에 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-231">Users who have access to files and folders in Microsoft 365 can download files and copy them to external media.</span></span> <span data-ttu-id="12bb9-232">원치 않는 파일이 공유되는 위험을 줄이기 위해 민감도 레이블을 사용하여 콘텐츠를 암호화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12bb9-232">To reduce the risk of unwanted file sharing, you can encrypt the content by using sensitivity labels.</span></span>

## <a name="see-also"></a><span data-ttu-id="12bb9-233">참고 항목</span><span class="sxs-lookup"><span data-stu-id="12bb9-233">See also</span></span>

[<span data-ttu-id="12bb9-234">Microsoft 365 게스트 공유 설정 참조</span><span class="sxs-lookup"><span data-stu-id="12bb9-234">Microsoft 365 guest sharing settings reference</span></span>](microsoft-365-guest-settings.md)