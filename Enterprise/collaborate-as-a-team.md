---
title: 팀의 게스트와 공동 작업
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
localization_priority: Normal
description: 팀에서 게스트와 공동 작업 하는 방법에 대해 알아봅니다.
ms.openlocfilehash: 9a169e33a9cbd8f079966443bd3d830aa79f4971
ms.sourcegitcommit: 3bba97053caf5f9cff0ef3205afb7869535f38bd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/16/2019
ms.locfileid: "36992417"
---
# <a name="collaborate-with-guests-in-a-team"></a><span data-ttu-id="7b6af-103">팀의 게스트와 공동 작업</span><span class="sxs-lookup"><span data-stu-id="7b6af-103">Collaborate with guests in a team</span></span>

<span data-ttu-id="7b6af-104">여러 문서, 작업 및 대화에서 게스트와 공동 작업을 수행 해야 하는 경우 Microsoft 팀을 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-104">If you need to collaborate with guests across documents, tasks, and conversations, we recommend using Microsoft Teams.</span></span> <span data-ttu-id="7b6af-105">팀은 영구 채팅 및 통합 사용자 환경에서 사용자 지정 및 확장 가능한 공동 작업 도구 집합을 사용 하 여 Office 및 SharePoint에서 사용할 수 있는 모든 공동 작업 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-105">Teams provides all of the collaboration features available in Office and SharePoint with persistent chat and a customizable and extensible set of collaboration tools in a unified user experience.</span></span>

<span data-ttu-id="7b6af-106">이 문서에서는 게스트와의 공동 작업을 위해 팀을 설정 하는 데 필요한 Microsoft 365 구성 단계를 안내 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-106">In this article, we'll walk through the Microsoft 365 configuration steps necessary to set up a team for collaboration with guests.</span></span>

## <a name="azure-organizational-relationships-settings"></a><span data-ttu-id="7b6af-107">Azure 조직 관계 설정</span><span class="sxs-lookup"><span data-stu-id="7b6af-107">Azure Organizational relationships settings</span></span>

<span data-ttu-id="7b6af-108">Microsoft 365의 공유는 Azure Active Directory의 조직 관계 설정에 따라 최상위 수준에서 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-108">Sharing in Microsoft 365 is governed at its highest level by the organizational relationships settings in Azure Active Directory.</span></span> <span data-ttu-id="7b6af-109">Azure AD에서 게스트 공유가 사용 하지 않도록 설정 되거나 제한 되 면 Microsoft 365에서 구성한 모든 공유 설정이 재정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-109">If guest sharing is disabled or restricted in Azure AD, this will override any sharing settings that you configure in Microsoft 365.</span></span>

<span data-ttu-id="7b6af-110">조직 관계 설정을 확인 하 여 게스트가 공유 하는 것이 차단 되지 않는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-110">Check the organizational relationships settings to ensure that sharing with guests is not blocked.</span></span>

![Azure Active Directory 조직 관계 설정 페이지 스크린샷](media/azure-ad-organizational-relationships-settings.png)

<span data-ttu-id="7b6af-112">조직 관계 설정을 설정 하려면</span><span class="sxs-lookup"><span data-stu-id="7b6af-112">To set organizational relationship settings</span></span>

1. <span data-ttu-id="7b6af-113">Microsoft Azure에 로그인 [https://portal.azure.com](https://portal.azure.com)합니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-113">Log in to Microsoft Azure at [https://portal.azure.com](https://portal.azure.com).</span></span>
2. <span data-ttu-id="7b6af-114">왼쪽 탐색 창에서 **Azure Active Directory**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-114">In the left navigation, click **Azure Active Directory**.</span></span>
3. <span data-ttu-id="7b6af-115">**개요** 창에서 **조직 관계**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-115">In the **Overview** pane, click **Organizational relationships**.</span></span>
4. <span data-ttu-id="7b6af-116">**조직 관계** 창에서 **설정을**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-116">In the **Organizational relationships** pane, click **Settings**.</span></span>
5. <span data-ttu-id="7b6af-117">**Guest inviter 역할의 관리자 및 사용자가 초대** 를 하 고 **구성원은 초대** 를 할 수 있는지 확인 하 고 둘 다 **예**로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-117">Ensure that **Admins and users in the guest inviter role can invite** and **Members can invite** are both set to **Yes**.</span></span>
6. <span data-ttu-id="7b6af-118">변경한 경우 **저장**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-118">If you made changes, click **Save**.</span></span>

<span data-ttu-id="7b6af-119">**공동 작업 제한** 섹션의 설정을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-119">Note the settings in the **Collaboration restrictions** section.</span></span> <span data-ttu-id="7b6af-120">공동 작업 하려는 게스트의 도메인이 차단 되지 않았는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-120">Make sure that the domains of the guests that you want to collaborate with aren't blocked.</span></span>

## <a name="teams-guest-access-settings"></a><span data-ttu-id="7b6af-121">팀 게스트 액세스 설정</span><span class="sxs-lookup"><span data-stu-id="7b6af-121">Teams guest access settings</span></span>

<span data-ttu-id="7b6af-122">팀에는 게스트 액세스에 대 한 마스터 온/오프 스위치가 있으며, 팀원 들이 어떤 게스트 작업을 수행할 수 있는지를 제어 하는 다양 한 설정을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-122">Teams has a master on/off switch for guest access and a variety of settings available to control what guests can do in a team.</span></span> <span data-ttu-id="7b6af-123">게스트 액세스를 팀에서 작동 시키려면 마스터 스위치를 사용 하 여 **팀에서 게스트 액세스 허용** 이 **설정** 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-123">The master switch, **Allow guest access in Teams** must be **On** for guest access to work in Teams.</span></span>

<span data-ttu-id="7b6af-124">팀에서 게스트 액세스를 사용 하도록 설정 되어 있는지 확인 하 고 비즈니스 요구에 따라 게스트 설정을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-124">Check to ensure that guest access is enabled in Teams and make any adjustment to the guest settings based on your business needs.</span></span> <span data-ttu-id="7b6af-125">이러한 설정은 모든 팀에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-125">Keep in mind that these settings affect all teams.</span></span>

![팀의 게스트 액세스 전환 스크린샷](media/teams-guest-access-toggle-on.png)

<span data-ttu-id="7b6af-127">팀 게스트 액세스 설정을 설정 하려면</span><span class="sxs-lookup"><span data-stu-id="7b6af-127">To set Teams guest access settings</span></span>

1. <span data-ttu-id="7b6af-128">에서 [https://admin.microsoft.com](https://admin.microsoft.com)Microsoft 365 관리 센터에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-128">Log in to the Microsoft 365 admin center at [https://admin.microsoft.com](https://admin.microsoft.com).</span></span>
2. <span data-ttu-id="7b6af-129">왼쪽 탐색 영역에서 **모두 표시**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-129">In the left navigation, click **Show all**.</span></span>
3. <span data-ttu-id="7b6af-130">**관리 센터**에서 **팀**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-130">Under **Admin centers**, click **Teams**.</span></span>
4. <span data-ttu-id="7b6af-131">팀 관리 센터의 왼쪽 탐색 창에서 **조직 전체 설정을** 확장 하 고 **게스트 액세스**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-131">In the Teams admin center, in the left navigation, expand **Org-wide settings** and click **Guest access**.</span></span>
5. <span data-ttu-id="7b6af-132">**팀에서 게스트 액세스 허용** 이 설정 되어 있는지 확인 **합니다.**</span><span class="sxs-lookup"><span data-stu-id="7b6af-132">Ensure that **Allow guest access in Teams** is set to **On**.</span></span>
6. <span data-ttu-id="7b6af-133">추가 게스트 설정을 원하는 대로 변경한 다음 **저장**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-133">Make any desired changes to the additional guest settings, and then click **Save**.</span></span>

> [!NOTE]
> <span data-ttu-id="7b6af-134">팀 게스트 설정이 설정 된 후 활성 상태가 되는 데 최대 24 시간이 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-134">It may take up to twenty-four hours for the Teams guest setting to become active after you turn it on.</span></span>

## <a name="office-365-groups-guest-settings"></a><span data-ttu-id="7b6af-135">Office 365 그룹 게스트 설정</span><span class="sxs-lookup"><span data-stu-id="7b6af-135">Office 365 Groups guest settings</span></span>

<span data-ttu-id="7b6af-136">팀에서는 team 구성원에 게 Office 365 그룹을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-136">Teams uses Office 365 Groups for team membership.</span></span> <span data-ttu-id="7b6af-137">팀에서 게스트 액세스를 작동 하려면 Office 365 그룹 게스트 설정이 설정 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-137">The Office 365 Groups guest settings must be turned on in order for guest access in Teams to work.</span></span>

![Microsoft 365 관리 센터의 Office 365 그룹 게스트 설정 스크린샷](media/office-365-groups-guest-settings.png)

<span data-ttu-id="7b6af-139">Office 365 그룹 게스트 설정을 설정 하려면</span><span class="sxs-lookup"><span data-stu-id="7b6af-139">To set Office 365 Groups guest settings</span></span>

1. <span data-ttu-id="7b6af-140">Microsoft 365 관리 센터의 왼쪽 탐색 영역에서 **설정을**확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-140">In the Microsoft 365 admin center, in the left navigation, expand **Settings**.</span></span>
2. <span data-ttu-id="7b6af-141">**서비스 & 추가 기능**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-141">Click **Services & add-ins**.</span></span>
3. <span data-ttu-id="7b6af-142">목록에서 **Office 365 그룹**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-142">In the list, click **Office 365 Groups**.</span></span>
4. <span data-ttu-id="7b6af-143">**조직 외부 구성원이 그룹 콘텐츠에 액세스** 하 고 그룹 **소유자가 조직 외부의 사람을 그룹에 추가** 하도록 허용 확인란을 모두 선택 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-143">Ensure that the **Let group members outside your organization access group content** and **Let group owners add people outside your organization to groups** check boxes are both checked.</span></span>
5. <span data-ttu-id="7b6af-144">변경한 경우 **변경 내용 저장**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-144">If you made changes, click **Save changes**.</span></span>


## <a name="sharepoint-organization-level-sharing-settings"></a><span data-ttu-id="7b6af-145">SharePoint 조직 수준 공유 설정</span><span class="sxs-lookup"><span data-stu-id="7b6af-145">SharePoint organization level sharing settings</span></span>

<span data-ttu-id="7b6af-146">게스트가 팀의 파일에 액세스할 수 있도록 하려면 SharePoint 조직 수준 공유 설정에서 게스트가 공유 하도록 허용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-146">In order for guests to have access to files in Teams, the SharePoint organization-level sharing settings must allow for sharing with guests.</span></span>

<span data-ttu-id="7b6af-147">조직 수준 설정에 따라 팀에 연결 된 사이트를 포함 하 여 개별 사이트에서 사용할 수 있는 설정이 결정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-147">The organization-level settings determine what settings are available for individual sites, including sites associated with teams.</span></span> <span data-ttu-id="7b6af-148">사이트 설정은 조직 수준 설정 보다는 더 이상 허용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-148">Site settings cannot be more permissive than the organization-level settings.</span></span>

<span data-ttu-id="7b6af-149">익명 사용자와 파일 및 폴더 공유를 허용 하려면 **모든 사용자**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-149">If you want to allow file and folder sharing with anonymous users, choose **Anyone**.</span></span> <span data-ttu-id="7b6af-150">모든 게스트가 인증을 받도록 하려면 **신규 및 기존 게스트**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-150">If you want to ensure that all guests have to authenticate, choose **New and existing guests**.</span></span> <span data-ttu-id="7b6af-151">조직의 모든 사이트에 필요한 가장 관대 한 설정을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-151">Choose the most permissive setting that will be needed by any site in your organization.</span></span>

![SharePoint 조직 수준 공유 설정 스크린샷](media/sharepoint-organization-external-sharing-controls.png)


<span data-ttu-id="7b6af-153">SharePoint 조직 수준 공유 설정을 설정 하려면</span><span class="sxs-lookup"><span data-stu-id="7b6af-153">To set SharePoint organization level sharing settings</span></span>

1. <span data-ttu-id="7b6af-154">Microsoft 365 관리 센터의 왼쪽 탐색에 있는 **관리 센터**에서 **SharePoint**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-154">In the Microsoft 365 admin center, in the left navigation, under **Admin centers**, click **SharePoint**.</span></span>
2. <span data-ttu-id="7b6af-155">SharePoint 관리 센터의 왼쪽 탐색 창에서 **공유**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-155">In the SharePoint admin center, in the left navigation, click **Sharing**.</span></span>
3. <span data-ttu-id="7b6af-156">SharePoint 용 외부 공유가 **사용자** 또는 **신규 및 기존 게스트로**설정 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-156">Ensure that external sharing for SharePoint is set to **Anyone** or **New and existing guests**.</span></span>
4. <span data-ttu-id="7b6af-157">변경한 경우 **저장**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-157">If you made changes, click **Save**.</span></span>


## <a name="sharepoint-organization-level-default-link-settings"></a><span data-ttu-id="7b6af-158">SharePoint 조직 수준 기본 링크 설정</span><span class="sxs-lookup"><span data-stu-id="7b6af-158">SharePoint organization level default link settings</span></span>

<span data-ttu-id="7b6af-159">기본 파일 및 폴더 링크 설정에 따라 파일 또는 폴더를 공유할 때 기본적으로 사용자에 게 표시 되는 링크 옵션이 결정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-159">The default file and folder link settings determine which link option is shown to the user by default when they share a file or folder.</span></span> <span data-ttu-id="7b6af-160">원하는 경우 공유 하기 전에 다른 옵션 중 하나로 연결 유형을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-160">Users can change the link type to one of the other options before sharing if desired.</span></span>

<span data-ttu-id="7b6af-161">이 설정은 조직의 모든 팀 및 SharePoint 사이트에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-161">Keep in mind that this setting affects all teams and SharePoint sites in your organization.</span></span>

<span data-ttu-id="7b6af-162">사용자가 파일 및 폴더를 공유할 때 기본적으로 선택 되는 링크 유형을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-162">Choose the type of link that's selected by default when users share files and folders:</span></span>

- <span data-ttu-id="7b6af-163">**링크를 포함 하는 모든 사용자** 익명 사용자와 많은 파일 및 폴더를 공유할 것으로 예상 되는 경우이 옵션을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-163">**Anyone with the link** - Choose this option if you expect to share a lot of files and folders with anonymous users.</span></span> <span data-ttu-id="7b6af-164">*모든* 링크를 허용 하지만 실수로 익명 공유가 염려 되는 경우에는 다른 옵션 중 하나를 기본값으로 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-164">If you want to allow *Anyone* links but are concerned about accidental anonymous sharing, consider one of the other options as the default.</span></span> <span data-ttu-id="7b6af-165">이 링크 형식은 **모든 사용자** 가 공유 하도록 설정한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-165">This link type is only available if you've enabled **Anyone** sharing.</span></span>
- <span data-ttu-id="7b6af-166">**조직의 사용자만** 조직 내부 사용자와 파일 및 폴더 공유를 사용할 것으로 예상 되는 경우이 옵션을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-166">**Only people in your organization** - Choose this option if you expect most file and folder sharing to be with people inside your organization.</span></span>
- <span data-ttu-id="7b6af-167">**특정 사용자** -게스트와 파일 및 폴더 공유를 많이 수행 해야 하는 경우이 옵션을 고려 하세요.</span><span class="sxs-lookup"><span data-stu-id="7b6af-167">**Specific people** - Consider this option if you expect to do a lot of file and folder sharing with guests.</span></span> <span data-ttu-id="7b6af-168">이 유형의 링크는 게스트에서 작동 하며 인증을 요구 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-168">This type of link works with guests and requires them to authenticate.</span></span>
 
![SharePoint 조직 수준 파일 및 폴더 공유 설정 스크린샷](media/sharepoint-organization-files-folders-sharing-settings.png)


<span data-ttu-id="7b6af-170">SharePoint 조직 수준 기본 링크 설정을 설정 하려면</span><span class="sxs-lookup"><span data-stu-id="7b6af-170">To set the SharePoint organization level default link settings</span></span>

1. <span data-ttu-id="7b6af-171">SharePoint 관리 센터에서 공유 페이지로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-171">Navigate to the Sharing page in the SharePoint admin center.</span></span>
2. <span data-ttu-id="7b6af-172">**파일 및 폴더 링크**에서 사용 하려는 기본 공유 링크를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-172">Under **File and folder links**, select the default sharing link that you want to use.</span></span>
3. <span data-ttu-id="7b6af-173">변경한 경우 **저장**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-173">If you made changes, click **Save**.</span></span>

## <a name="create-a-team"></a><span data-ttu-id="7b6af-174">팀 만들기</span><span class="sxs-lookup"><span data-stu-id="7b6af-174">Create a team</span></span>

<span data-ttu-id="7b6af-175">다음 단계는 게스트와 공동 작업 하는 데 사용할 팀을 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-175">The next step is to create the team that you plan to use for collaborating with guests.</span></span>

<span data-ttu-id="7b6af-176">팀을 만들려면</span><span class="sxs-lookup"><span data-stu-id="7b6af-176">To create a team</span></span>
1. <span data-ttu-id="7b6af-177">팀의 **팀** 탭에서 왼쪽 창의 아래쪽에 있는 **참가 또는 팀 만들기** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-177">In Teams, on the **Teams** tab, click **Join or create a team** at the bottom of the left pane.</span></span>
2. <span data-ttu-id="7b6af-178">**팀 만들기를**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-178">Click **Create a team**.</span></span>
3. <span data-ttu-id="7b6af-179">**팀 구성 처음부터 새로 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-179">Click **Build a team from scratch**.</span></span>
4. <span data-ttu-id="7b6af-180">**개인** 또는 **공개**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-180">Choose **Private** or **Public**.</span></span>
5. <span data-ttu-id="7b6af-181">팀의 이름과 설명을 입력 하 고 **만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-181">Type a name and description for the team, and then click **Create**.</span></span>
6. <span data-ttu-id="7b6af-182">**건너뛰기를**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-182">Click **Skip**.</span></span>

<span data-ttu-id="7b6af-183">나중에 사용자를 초대 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-183">We'll invite users later.</span></span> <span data-ttu-id="7b6af-184">다음으로 팀과 연결 된 SharePoint 사이트에 대 한 사이트 수준 공유 설정을 확인 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-184">Next, it's important to check the site-level sharing settings for the SharePoint site that is associated with the team.</span></span>

## <a name="sharepoint-site-level-sharing-settings"></a><span data-ttu-id="7b6af-185">SharePoint 사이트 수준 공유 설정</span><span class="sxs-lookup"><span data-stu-id="7b6af-185">SharePoint site level sharing settings</span></span>

<span data-ttu-id="7b6af-186">사이트 수준 공유 설정을 확인 하 여이 팀에 대해 원하는 액세스 유형을 허용 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-186">Check the site-level sharing settings to make sure that they allow the type of access that you want for this team.</span></span> <span data-ttu-id="7b6af-187">예를 들어 조직 수준 설정을 모든 **사용자**로 설정 했지만 모든 게스트가이 팀에 대해 인증을 받으려는 경우에는 사이트 수준 공유 설정이 **신규 및 기존 게스트로**설정 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-187">For example, if you set the organization-level settings to **Anyone**, but you want all guests to authenticate for this team, then make sure the site-level sharing settings are set to **New and existing guests**.</span></span>

![SharePoint 사이트 외부 공유 설정 스크린샷](media/sharepoint-site-external-sharing-settings.png)


<span data-ttu-id="7b6af-189">사이트 수준 공유 설정을 설정 하려면</span><span class="sxs-lookup"><span data-stu-id="7b6af-189">To set site-level sharing settings</span></span>
1. <span data-ttu-id="7b6af-190">SharePoint 관리 센터의 왼쪽 탐색 창에서 **사이트** 를 확장 하 고 **활성 사이트**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-190">In the SharePoint admin center, in the left navigation, expand **Sites** and click **Active sites**.</span></span>
2. <span data-ttu-id="7b6af-191">방금 만든 팀의 사이트를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-191">Select the site for the team that you just created.</span></span>
3. <span data-ttu-id="7b6af-192">리본 메뉴에서 **공유**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-192">In the ribbon, click **Sharing**.</span></span>
4. <span data-ttu-id="7b6af-193">공유가 **사용자** 또는 **신규 및 기존 게스트로**설정 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-193">Ensure that sharing is set to **Anyone** or **New and existing guests**.</span></span>
5. <span data-ttu-id="7b6af-194">변경한 경우 **저장**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-194">If you made changes, click **Save**.</span></span>

## <a name="invite-users"></a><span data-ttu-id="7b6af-195">사용자 초대</span><span class="sxs-lookup"><span data-stu-id="7b6af-195">Invite users</span></span>

<span data-ttu-id="7b6af-196">이제 게스트 공유 설정이 구성 되므로 팀에 내부 사용자 및 게스트를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-196">Guest sharing settings are now configured, so you can start adding internal users and guests to your team.</span></span> 

<span data-ttu-id="7b6af-197">팀에 내부 사용자를 초대 하려면</span><span class="sxs-lookup"><span data-stu-id="7b6af-197">To invite internal users to a team</span></span>
1. <span data-ttu-id="7b6af-198">팀에서 **기타 옵션** (**\*\***)을 클릭 하 고 **구성원 추가**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-198">In the team, click **More options** (**\*\*\***), and then click **Add member**.</span></span>
2. <span data-ttu-id="7b6af-199">초대 하려는 사용자의 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-199">Type the name of the person who you want to invite.</span></span>
3. <span data-ttu-id="7b6af-200">**추가**를 클릭한 다음 **닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-200">Click **Add**, and then click **Close**.</span></span>

<span data-ttu-id="7b6af-201">팀에 게스트를 초대 하려면</span><span class="sxs-lookup"><span data-stu-id="7b6af-201">To invite guests to a team</span></span>
1. <span data-ttu-id="7b6af-202">팀에서 **기타 옵션** (**\*\***)을 클릭 하 고 **구성원 추가**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-202">In the team, click **More options** (**\*\*\***), and then click **Add member**.</span></span>
2. <span data-ttu-id="7b6af-203">초대 하려는 게스트의 전자 메일 주소를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-203">Type the email address of the guest who you want to invite.</span></span>
3. <span data-ttu-id="7b6af-204">**게스트 정보 편집**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-204">Click **Edit guest information**.</span></span>
4. <span data-ttu-id="7b6af-205">게스트의 전체 이름을 입력 하 고 확인 표시를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-205">Type the guest's full name and click the check mark.</span></span>
5. <span data-ttu-id="7b6af-206">**추가**를 클릭한 다음 **닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7b6af-206">Click **Add**, and then click **Close**.</span></span>

## <a name="see-also"></a><span data-ttu-id="7b6af-207">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7b6af-207">See Also</span></span>

