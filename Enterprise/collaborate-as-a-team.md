---
title: 게스트와 팀으로 공동 작업하기
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
localization_priority: Normal
f1.keywords: NOCSH
description: 팀에서 게스트와 공동 작업 하는 방법에 대해 알아봅니다.
ms.openlocfilehash: 87635d6fd2196fd706d27fb68cbe24e51b723220
ms.sourcegitcommit: 4e50f43857f93f42b71650354d1aec9ed4cc7fe2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/06/2020
ms.locfileid: "42549137"
---
# <a name="collaborate-with-guests-in-a-team"></a><span data-ttu-id="17da5-103">게스트와 팀으로 공동 작업하기</span><span class="sxs-lookup"><span data-stu-id="17da5-103">Collaborate with guests in a team</span></span>

<span data-ttu-id="17da5-104">여러 문서, 작업 및 대화에서 게스트와 공동 작업을 수행 해야 하는 경우 Microsoft 팀을 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-104">If you need to collaborate with guests across documents, tasks, and conversations, we recommend using Microsoft Teams.</span></span> <span data-ttu-id="17da5-105">팀은 영구 채팅 및 통합 사용자 환경에서 사용자 지정 및 확장 가능한 공동 작업 도구 집합을 사용 하 여 Office 및 SharePoint에서 사용할 수 있는 모든 공동 작업 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-105">Teams provides all of the collaboration features available in Office and SharePoint with persistent chat and a customizable and extensible set of collaboration tools in a unified user experience.</span></span>

<span data-ttu-id="17da5-106">이 문서에서는 게스트와의 공동 작업을 위해 팀을 설정 하는 데 필요한 Microsoft 365 구성 단계를 안내 합니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-106">In this article, we'll walk through the Microsoft 365 configuration steps necessary to set up a team for collaboration with guests.</span></span>

## <a name="video-demonstration"></a><span data-ttu-id="17da5-107">비디오 데모</span><span class="sxs-lookup"><span data-stu-id="17da5-107">Video demonstration</span></span>

<span data-ttu-id="17da5-108">이 비디오에서는이 문서에서 설명 하는 구성 단계를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-108">This video shows the configuration steps described in this document.</span></span></br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE44NTr?autoplay=false]

## <a name="azure-organizational-relationships-settings"></a><span data-ttu-id="17da5-109">Azure 조직 관계 설정</span><span class="sxs-lookup"><span data-stu-id="17da5-109">Azure Organizational relationships settings</span></span>

<span data-ttu-id="17da5-110">Microsoft 365의 공유는 Azure Active Directory의 조직 관계 설정에 따라 최상위 수준에서 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-110">Sharing in Microsoft 365 is governed at its highest level by the organizational relationships settings in Azure Active Directory.</span></span> <span data-ttu-id="17da5-111">Azure AD에서 게스트 공유가 사용 하지 않도록 설정 되거나 제한 되 면 Microsoft 365에서 구성한 모든 공유 설정이 재정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-111">If guest sharing is disabled or restricted in Azure AD, this will override any sharing settings that you configure in Microsoft 365.</span></span>

<span data-ttu-id="17da5-112">조직 관계 설정을 확인 하 여 게스트가 공유 하는 것이 차단 되지 않는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-112">Check the organizational relationships settings to ensure that sharing with guests is not blocked.</span></span>

![Azure Active Directory 조직 관계 설정 페이지 스크린샷](media/azure-ad-organizational-relationships-settings.png)

<span data-ttu-id="17da5-114">조직 관계 설정을 설정 하려면</span><span class="sxs-lookup"><span data-stu-id="17da5-114">To set organizational relationship settings</span></span>

1. <span data-ttu-id="17da5-115">Microsoft Azure에 로그인 [https://portal.azure.com](https://portal.azure.com)합니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-115">Log in to Microsoft Azure at [https://portal.azure.com](https://portal.azure.com).</span></span>
2. <span data-ttu-id="17da5-116">왼쪽 탐색 창에서 **Azure Active Directory**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-116">In the left navigation, click **Azure Active Directory**.</span></span>
3. <span data-ttu-id="17da5-117">**개요** 창에서 **조직 관계**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-117">In the **Overview** pane, click **Organizational relationships**.</span></span>
4. <span data-ttu-id="17da5-118">**조직 관계** 창에서 **설정을**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-118">In the **Organizational relationships** pane, click **Settings**.</span></span>
5. <span data-ttu-id="17da5-119">**Guest inviter 역할의 관리자 및 사용자가 초대** 를 하 고 **구성원은 초대** 를 할 수 있는지 확인 하 고 둘 다 **예**로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-119">Ensure that **Admins and users in the guest inviter role can invite** and **Members can invite** are both set to **Yes**.</span></span>
6. <span data-ttu-id="17da5-120">변경한 내용이 있으면 **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-120">If you made changes, click **Save**.</span></span>

<span data-ttu-id="17da5-121">**공동 작업 제한** 섹션의 설정을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-121">Note the settings in the **Collaboration restrictions** section.</span></span> <span data-ttu-id="17da5-122">공동 작업 하려는 게스트의 도메인이 차단 되지 않았는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-122">Make sure that the domains of the guests that you want to collaborate with aren't blocked.</span></span>

## <a name="teams-guest-access-settings"></a><span data-ttu-id="17da5-123">팀 게스트 액세스 설정</span><span class="sxs-lookup"><span data-stu-id="17da5-123">Teams guest access settings</span></span>

<span data-ttu-id="17da5-124">팀에는 게스트 액세스에 대 한 마스터 온/오프 스위치가 있으며, 팀원 들이 어떤 게스트 작업을 수행할 수 있는지를 제어 하는 다양 한 설정을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-124">Teams has a master on/off switch for guest access and a variety of settings available to control what guests can do in a team.</span></span> <span data-ttu-id="17da5-125">게스트 액세스를 팀에서 작동 시키려면 마스터 스위치를 사용 하 여 **팀에서 게스트 액세스 허용** 이 **설정** 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-125">The master switch, **Allow guest access in Teams** must be **On** for guest access to work in Teams.</span></span>

<span data-ttu-id="17da5-126">팀에서 게스트 액세스를 사용 하도록 설정 되어 있는지 확인 하 고 비즈니스 요구에 따라 게스트 설정을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-126">Check to ensure that guest access is enabled in Teams and make any adjustment to the guest settings based on your business needs.</span></span> <span data-ttu-id="17da5-127">이러한 설정은 모든 팀에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-127">Keep in mind that these settings affect all teams.</span></span>

![Teams의 게스트 액세스 토글의 스크린샷](media/teams-guest-access-toggle-on.png)

<span data-ttu-id="17da5-129">팀 게스트 액세스 설정을 설정 하려면</span><span class="sxs-lookup"><span data-stu-id="17da5-129">To set Teams guest access settings</span></span>

1. <span data-ttu-id="17da5-130">에서 [https://admin.microsoft.com](https://admin.microsoft.com)Microsoft 365 관리 센터에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-130">Log in to the Microsoft 365 admin center at [https://admin.microsoft.com](https://admin.microsoft.com).</span></span>
2. <span data-ttu-id="17da5-131">왼쪽 탐색 영역에서 **모두 표시**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-131">In the left navigation, click **Show all**.</span></span>
3. <span data-ttu-id="17da5-132">**관리 센터**에서 **팀**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-132">Under **Admin centers**, click **Teams**.</span></span>
4. <span data-ttu-id="17da5-133">팀 관리 센터의 왼쪽 탐색 창에서 **조직 전체 설정을** 확장 하 고 **게스트 액세스**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-133">In the Teams admin center, in the left navigation, expand **Org-wide settings** and click **Guest access**.</span></span>
5. <span data-ttu-id="17da5-134">**팀에서 게스트 액세스 허용** 이 설정 되어 있는지 확인 **합니다.**</span><span class="sxs-lookup"><span data-stu-id="17da5-134">Ensure that **Allow guest access in Teams** is set to **On**.</span></span>
6. <span data-ttu-id="17da5-135">추가 게스트 설정을 원하는 대로 변경한 다음 **저장**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-135">Make any desired changes to the additional guest settings, and then click **Save**.</span></span>

> [!NOTE]
> <span data-ttu-id="17da5-136">팀 게스트 설정이 설정 된 후 활성 상태가 되는 데 최대 24 시간이 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-136">It may take up to twenty-four hours for the Teams guest setting to become active after you turn it on.</span></span>

## <a name="office-365-groups-guest-settings"></a><span data-ttu-id="17da5-137">Office 365 그룹 게스트 설정</span><span class="sxs-lookup"><span data-stu-id="17da5-137">Office 365 Groups guest settings</span></span>

<span data-ttu-id="17da5-138">팀에서는 team 구성원에 게 Office 365 그룹을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-138">Teams uses Office 365 Groups for team membership.</span></span> <span data-ttu-id="17da5-139">팀에서 게스트 액세스를 작동 하려면 Office 365 그룹 게스트 설정이 설정 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-139">The Office 365 Groups guest settings must be turned on in order for guest access in Teams to work.</span></span>

![Microsoft 365 관리 센터의 Office 365 그룹 게스트 설정 스크린샷](media/office-365-groups-guest-settings.png)

<span data-ttu-id="17da5-141">Office 365 그룹 게스트 설정을 설정 하려면</span><span class="sxs-lookup"><span data-stu-id="17da5-141">To set Office 365 Groups guest settings</span></span>

1. <span data-ttu-id="17da5-142">Microsoft 365 관리 센터의 왼쪽 탐색 영역에서 **설정을**확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-142">In the Microsoft 365 admin center, in the left navigation, expand **Settings**.</span></span>
2. <span data-ttu-id="17da5-143">**서비스 & 추가 기능**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-143">Click **Services & add-ins**.</span></span>
3. <span data-ttu-id="17da5-144">목록에서 **Office 365 그룹**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-144">In the list, click **Office 365 Groups**.</span></span>
4. <span data-ttu-id="17da5-145">**조직 외부 구성원이 그룹 콘텐츠에 액세스** 하 고 그룹 **소유자가 조직 외부의 사람을 그룹에 추가** 하도록 허용 확인란을 모두 선택 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-145">Ensure that the **Let group members outside your organization access group content** and **Let group owners add people outside your organization to groups** check boxes are both checked.</span></span>
5. <span data-ttu-id="17da5-146">변경한 경우 **변경 내용 저장**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-146">If you made changes, click **Save changes**.</span></span>


## <a name="sharepoint-organization-level-sharing-settings"></a><span data-ttu-id="17da5-147">SharePoint 조직 수준 공유 설정</span><span class="sxs-lookup"><span data-stu-id="17da5-147">SharePoint organization level sharing settings</span></span>

<span data-ttu-id="17da5-148">파일, 폴더 및 목록과 같은 팀 콘텐츠는 모두 SharePoint에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-148">Teams content such as files, folders, and lists are all stored in SharePoint.</span></span> <span data-ttu-id="17da5-149">게스트가 팀의 이러한 항목에 액세스할 수 있도록 하려면 SharePoint 조직 수준 공유 설정에서 게스트가 공유 하도록 허용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-149">In order for guests to have access to these items in Teams, the SharePoint organization-level sharing settings must allow for sharing with guests.</span></span>

<span data-ttu-id="17da5-150">조직 수준 설정에 따라 팀에 연결 된 사이트를 포함 하 여 개별 사이트에서 사용할 수 있는 설정이 결정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-150">The organization-level settings determine what settings are available for individual sites, including sites associated with teams.</span></span> <span data-ttu-id="17da5-151">사이트 설정은 조직 수준 설정 보다는 더 이상 허용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-151">Site settings cannot be more permissive than the organization-level settings.</span></span>

<span data-ttu-id="17da5-152">인증 되지 않은 사용자와 파일 및 폴더 공유를 허용 하려면 **모든 사용자**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-152">If you want to allow file and folder sharing with unauthenticated people, choose **Anyone**.</span></span> <span data-ttu-id="17da5-153">모든 게스트가 인증을 받도록 하려면 **신규 및 기존 게스트**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-153">If you want to ensure that all guests have to authenticate, choose **New and existing guests**.</span></span> <span data-ttu-id="17da5-154">조직의 모든 사이트에 필요한 가장 관대 한 설정을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-154">Choose the most permissive setting that will be needed by any site in your organization.</span></span>

![SharePoint 조직 수준 공유 설정의 스크린샷](media/sharepoint-organization-external-sharing-controls.png)


<span data-ttu-id="17da5-156">SharePoint 조직 수준 공유 설정을 설정 하려면</span><span class="sxs-lookup"><span data-stu-id="17da5-156">To set SharePoint organization level sharing settings</span></span>

1. <span data-ttu-id="17da5-157">Microsoft 365 관리 센터의 왼쪽 탐색에 있는 **관리 센터**에서 **SharePoint**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-157">In the Microsoft 365 admin center, in the left navigation, under **Admin centers**, click **SharePoint**.</span></span>
2. <span data-ttu-id="17da5-158">왼쪽 탐색 창의 SharePoint 관리 센터에서 **공유**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-158">In the SharePoint admin center, in the left navigation, click **Sharing**.</span></span>
3. <span data-ttu-id="17da5-159">SharePoint 용 외부 공유가 **사용자** 또는 **신규 및 기존 게스트로**설정 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-159">Ensure that external sharing for SharePoint is set to **Anyone** or **New and existing guests**.</span></span>
4. <span data-ttu-id="17da5-160">변경한 내용이 있으면 **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-160">If you made changes, click **Save**.</span></span>


## <a name="sharepoint-organization-level-default-link-settings"></a><span data-ttu-id="17da5-161">SharePoint 조직 수준 기본 링크 설정</span><span class="sxs-lookup"><span data-stu-id="17da5-161">SharePoint organization level default link settings</span></span>

<span data-ttu-id="17da5-162">기본 파일 및 폴더 링크 설정에 따라 파일 또는 폴더를 공유할 때 기본적으로 사용자에 게 표시 되는 링크 옵션이 결정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-162">The default file and folder link settings determine which link option is shown to the user by default when they share a file or folder.</span></span> <span data-ttu-id="17da5-163">원하는 경우 공유 하기 전에 다른 옵션 중 하나로 연결 유형을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-163">Users can change the link type to one of the other options before sharing if desired.</span></span>

<span data-ttu-id="17da5-164">이 설정은 조직의 모든 팀 및 SharePoint 사이트에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-164">Keep in mind that this setting affects all teams and SharePoint sites in your organization.</span></span>

<span data-ttu-id="17da5-165">사용자가 파일 및 폴더를 공유할 때 기본적으로 선택 되는 링크 유형을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-165">Choose the type of link that's selected by default when users share files and folders:</span></span>

- <span data-ttu-id="17da5-166">**링크가 있는 모든 사용자** -파일 및 폴더의 인증 되지 않은 공유를 많이 사용 하는 경우이 옵션을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-166">**Anyone with the link** - Choose this option if you expect to do a lot of unauthenticated sharing of files and folders.</span></span> <span data-ttu-id="17da5-167">*모든* 링크를 허용 하지만 실수로 인증 되지 않은 공유가 발생 하는 것이 염려 되는 경우에는 다른 옵션 중 하나를 기본값으로 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-167">If you want to allow *Anyone* links but are concerned about accidental unauthenticated sharing, consider one of the other options as the default.</span></span> <span data-ttu-id="17da5-168">이 링크 형식은 **모든 사용자** 가 공유 하도록 설정한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-168">This link type is only available if you've enabled **Anyone** sharing.</span></span>
- <span data-ttu-id="17da5-169">**조직의 사용자만** 조직 내부 사용자와 파일 및 폴더 공유를 사용할 것으로 예상 되는 경우이 옵션을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-169">**Only people in your organization** - Choose this option if you expect most file and folder sharing to be with people inside your organization.</span></span>
- <span data-ttu-id="17da5-170">**특정 사용자** -게스트와 파일 및 폴더 공유를 많이 수행 해야 하는 경우이 옵션을 고려 하세요.</span><span class="sxs-lookup"><span data-stu-id="17da5-170">**Specific people** - Consider this option if you expect to do a lot of file and folder sharing with guests.</span></span> <span data-ttu-id="17da5-171">이 유형의 링크는 게스트에서 작동 하며 인증을 요구 합니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-171">This type of link works with guests and requires them to authenticate.</span></span>
 
![SharePoint 조직 수준 파일 및 폴더 공유 설정 스크린샷](media/sharepoint-organization-files-folders-sharing-settings.png)


<span data-ttu-id="17da5-173">SharePoint 조직 수준 기본 링크 설정을 설정 하려면</span><span class="sxs-lookup"><span data-stu-id="17da5-173">To set the SharePoint organization level default link settings</span></span>

1. <span data-ttu-id="17da5-174">SharePoint 관리 센터에서 공유 페이지로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-174">Navigate to the Sharing page in the SharePoint admin center.</span></span>
2. <span data-ttu-id="17da5-175">**파일 및 폴더 링크**에서 사용 하려는 기본 공유 링크를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-175">Under **File and folder links**, select the default sharing link that you want to use.</span></span>
3. <span data-ttu-id="17da5-176">변경한 내용이 있으면 **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-176">If you made changes, click **Save**.</span></span>

## <a name="create-a-team"></a><span data-ttu-id="17da5-177">팀 만들기</span><span class="sxs-lookup"><span data-stu-id="17da5-177">Create a team</span></span>

<span data-ttu-id="17da5-178">다음 단계는 게스트와 공동 작업 하는 데 사용할 팀을 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-178">The next step is to create the team that you plan to use for collaborating with guests.</span></span>

<span data-ttu-id="17da5-179">팀을 만들려면</span><span class="sxs-lookup"><span data-stu-id="17da5-179">To create a team</span></span>
1. <span data-ttu-id="17da5-180">팀의 **팀** 탭에서 왼쪽 창의 아래쪽에 있는 **참가 또는 팀 만들기** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-180">In Teams, on the **Teams** tab, click **Join or create a team** at the bottom of the left pane.</span></span>
2. <span data-ttu-id="17da5-181">**팀 만들기를**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-181">Click **Create a team**.</span></span>
3. <span data-ttu-id="17da5-182">**팀 구성 처음부터 새로 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-182">Click **Build a team from scratch**.</span></span>
4. <span data-ttu-id="17da5-183">**개인** 또는 **공개**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-183">Choose **Private** or **Public**.</span></span>
5. <span data-ttu-id="17da5-184">팀의 이름과 설명을 입력 하 고 **만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-184">Type a name and description for the team, and then click **Create**.</span></span>
6. <span data-ttu-id="17da5-185">**건너뛰기를**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-185">Click **Skip**.</span></span>

<span data-ttu-id="17da5-186">나중에 사용자를 초대 합니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-186">We'll invite users later.</span></span> <span data-ttu-id="17da5-187">다음으로 팀과 연결 된 SharePoint 사이트에 대 한 사이트 수준 공유 설정을 확인 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-187">Next, it's important to check the site-level sharing settings for the SharePoint site that is associated with the team.</span></span>

## <a name="sharepoint-site-level-sharing-settings"></a><span data-ttu-id="17da5-188">SharePoint 사이트 수준 공유 설정</span><span class="sxs-lookup"><span data-stu-id="17da5-188">SharePoint site level sharing settings</span></span>

<span data-ttu-id="17da5-189">사이트 수준 공유 설정을 확인 하 여이 팀에 대해 원하는 액세스 유형을 허용 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-189">Check the site-level sharing settings to make sure that they allow the type of access that you want for this team.</span></span> <span data-ttu-id="17da5-190">예를 들어 조직 수준 설정을 모든 **사용자**로 설정 했지만 모든 게스트가이 팀에 대해 인증을 받으려는 경우에는 사이트 수준 공유 설정이 **신규 및 기존 게스트로**설정 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-190">For example, if you set the organization-level settings to **Anyone**, but you want all guests to authenticate for this team, then make sure the site-level sharing settings are set to **New and existing guests**.</span></span>

![SharePoint 사이트 외부 공유 설정 스크린샷](media/sharepoint-site-external-sharing-settings.png)


<span data-ttu-id="17da5-192">사이트 수준 공유 설정을 설정 하려면</span><span class="sxs-lookup"><span data-stu-id="17da5-192">To set site-level sharing settings</span></span>
1. <span data-ttu-id="17da5-193">SharePoint 관리 센터의 왼쪽 탐색 창에서 **사이트**를 확장시키고 **Active 사이트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-193">In the SharePoint admin center, in the left navigation, expand **Sites** and click **Active sites**.</span></span>
2. <span data-ttu-id="17da5-194">방금 생성한 팀의 사이트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-194">Select the site for the team that you just created.</span></span>
3. <span data-ttu-id="17da5-195">리본 메뉴에서 **공유**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-195">In the ribbon, click **Sharing**.</span></span>
4. <span data-ttu-id="17da5-196">공유가 **사용자** 또는 **신규 및 기존 게스트로**설정 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-196">Ensure that sharing is set to **Anyone** or **New and existing guests**.</span></span>
5. <span data-ttu-id="17da5-197">변경한 내용이 있으면 **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-197">If you made changes, click **Save**.</span></span>

## <a name="invite-users"></a><span data-ttu-id="17da5-198">사용자 초대</span><span class="sxs-lookup"><span data-stu-id="17da5-198">Invite users</span></span>

<span data-ttu-id="17da5-199">이제 게스트 공유 설정이 구성 되므로 팀에 내부 사용자 및 게스트를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-199">Guest sharing settings are now configured, so you can start adding internal users and guests to your team.</span></span> 

<span data-ttu-id="17da5-200">팀에 내부 사용자를 초대 하려면</span><span class="sxs-lookup"><span data-stu-id="17da5-200">To invite internal users to a team</span></span>
1. <span data-ttu-id="17da5-201">팀에서 **기타 옵션** (**\*\***)을 클릭 하 고 **구성원 추가**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-201">In the team, click **More options** (**\*\*\***), and then click **Add member**.</span></span>
2. <span data-ttu-id="17da5-202">초대 하려는 사용자의 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-202">Type the name of the person who you want to invite.</span></span>
3. <span data-ttu-id="17da5-203">**추가**를 클릭한 다음 **닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-203">Click **Add**, and then click **Close**.</span></span>

<span data-ttu-id="17da5-204">팀에 게스트를 초대 하려면</span><span class="sxs-lookup"><span data-stu-id="17da5-204">To invite guests to a team</span></span>
1. <span data-ttu-id="17da5-205">팀에서 **기타 옵션** (**\*\***)을 클릭 하 고 **구성원 추가**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-205">In the team, click **More options** (**\*\*\***), and then click **Add member**.</span></span>
2. <span data-ttu-id="17da5-206">초대 하려는 게스트의 전자 메일 주소를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-206">Type the email address of the guest who you want to invite.</span></span>
3. <span data-ttu-id="17da5-207">**게스트 정보 편집**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-207">Click **Edit guest information**.</span></span>
4. <span data-ttu-id="17da5-208">게스트의 전체 이름을 입력 하 고 확인 표시를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-208">Type the guest's full name and click the check mark.</span></span>
5. <span data-ttu-id="17da5-209">**추가**를 클릭한 다음 **닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="17da5-209">Click **Add**, and then click **Close**.</span></span>

## <a name="see-also"></a><span data-ttu-id="17da5-210">참고 항목</span><span class="sxs-lookup"><span data-stu-id="17da5-210">See Also</span></span>

[<span data-ttu-id="17da5-211">인증되지 않은 사용자와 파일 및 폴더를 공유하는 모범 사례</span><span class="sxs-lookup"><span data-stu-id="17da5-211">Best practices for sharing files and folders with unauthenticated users</span></span>](best-practices-anonymous-sharing.md)

[<span data-ttu-id="17da5-212">게스트와 공유할 때 파일에 실수로 발생하는 노출을 제한</span><span class="sxs-lookup"><span data-stu-id="17da5-212">Limit accidental exposure to files when sharing with guests</span></span>](sharing-limit-accidental-exposure.md)

[<span data-ttu-id="17da5-213">보안 게스트 공유 환경 만들기</span><span class="sxs-lookup"><span data-stu-id="17da5-213">Create a secure guest sharing environment</span></span>](create-a-secure-guest-sharing-environment.md)

[<span data-ttu-id="17da5-214">관리 대상 게스트와 B2B 엑스트라넷 작성</span><span class="sxs-lookup"><span data-stu-id="17da5-214">Create a B2B extranet with managed guests</span></span>](b2b-extranet.md)
