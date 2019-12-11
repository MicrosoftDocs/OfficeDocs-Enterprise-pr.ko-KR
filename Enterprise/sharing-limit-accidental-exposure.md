---
title: 우발적 노출 제한
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
localization_priority: Priority
description: 파일을 조직 외부의 사람들과 공유할 때 실수로 발생하는 정보 노출을 제한하는 방법을 알아보세요.
ms.openlocfilehash: d980af0a8aa60416a32f4c2fe5d4a1c8911842f4
ms.sourcegitcommit: b5992f367ccae97a8ea538738fe36d3d703cd6e7
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2019
ms.locfileid: "39919251"
---
# <a name="limit-accidental-exposure-to-files-when-sharing-with-people-outside-your-organization"></a><span data-ttu-id="6320c-103">파일을 조직 외부의 사람들과 공유할 때 실수로 발생하는 정보 노출을 제한</span><span class="sxs-lookup"><span data-stu-id="6320c-103">Limit accidental exposure to files when sharing with people outside your organization</span></span>

<span data-ttu-id="6320c-104">파일 및 폴더를 조직 외부의 사람들과 공유할 때 기밀 정보를 우발적으로 공유하게 되는 가능성을 줄일 수 있는 다양한 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6320c-104">When sharing files and folders with guests, there are a variety of options to reduce the chances of accidentally sharing confidential information.</span></span> <span data-ttu-id="6320c-105">이 문서에서 설명하는 옵션 중에서 조직의 필요 사항에 가장 적합한 방법을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6320c-105">You can choose from the options in this article to best meet the needs of your organization.</span></span>

## <a name="use-best-practices-for-anyone-links"></a><span data-ttu-id="6320c-106">모든 사용자 링크 모범 사례 활용</span><span class="sxs-lookup"><span data-stu-id="6320c-106">Use best practices for Anyone links</span></span>

<span data-ttu-id="6320c-107">조직의 사용자가 인증되지 않은 공유를 수행해야 하지만 인증되지 않은 사람이 콘텐츠를 수정하는 것이 우려되는 경우 [인증되지 않은 공유 모범 사례](best-practices-anonymous-sharing.md)를 읽고 조직에서의 인증되지 않은 공유 작업 방법에 대한 지침을 학습하세요.</span><span class="sxs-lookup"><span data-stu-id="6320c-107">If people in your organization need to do unauthenticated sharing, but you're concerned about unauthenticated guests modifying content, read [Best practices for unauthenticated sharing](best-practices-anonymous-sharing.md) for guidance on how to work with unauthenticated sharing in your organization.</span></span>

## <a name="turn-off-anyone-links"></a><span data-ttu-id="6320c-108">모든 사용자 링크 해제</span><span class="sxs-lookup"><span data-stu-id="6320c-108">Turn off Anyone links</span></span>

<span data-ttu-id="6320c-109">Anyone 링크는 가장 쉽게 공유하는 방법이며 사용자가 IT 부서의 통제 밖에 있는 다른 솔루션을 찾는 데 위험을 줄여주기에 *Anyone* 링크를 활성화 상태로 둘 것을 권장합니다.</span><span class="sxs-lookup"><span data-stu-id="6320c-109">We recommend leaving *Anyone* links enabled for appropriate content because it's the easiest way to share and can help reduce the risk of users seeking other solutions that are outside the control of your IT department.</span></span> <span data-ttu-id="6320c-110">*Anyone*링크는 다른 사용자에게 전달될 수 있지만 파일 액세스는 링크가 있는 사용자만할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6320c-110">*Anyone* links can be forwarded to others, but file access is only available to those who have the link.</span></span>

<span data-ttu-id="6320c-111">조직 외부의 사람들이 SharePoint, 그룹 또는 팀의 콘텐츠에 액세스할 때 항상 인증을 하게 하려면 *모든 사용자* 공유를 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="6320c-111">If you always want guests to authenticate when accessing content in SharePoint, Groups, or Teams, you can turn off *Anyone* sharing.</span></span> <span data-ttu-id="6320c-112">이렇게 하면 사용자가 인증되지 않은 콘텐츠를 공유할 수 없게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6320c-112">This will prevent users from unauthenticated sharing of content.</span></span>

<span data-ttu-id="6320c-113">*모든 사용자* 링크를 비활성화하는 경우 사용자는 여전히 *특정 사용자* 링크를 사용하여 쉽게 게스트와 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6320c-113">If you disable *Anyone* links, users can still easily share with guests using *Specific people* links.</span></span> <span data-ttu-id="6320c-114">이 경우 조직 외부의 모든 사람이 공유 콘텐츠에 액세스를 하려면 먼저 인증을 해야합니다.</span><span class="sxs-lookup"><span data-stu-id="6320c-114">In this case, all guests will be required to authenticate before they can access the shared content.</span></span>

<span data-ttu-id="6320c-115">필요에 따라 특정 사이트나 조직 전체에 대해 *Anyone* 링크를 비활성화시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6320c-115">Depending on your needs, you can disable *Anyone* links for specific sites, or for your whole organization.</span></span>

<span data-ttu-id="6320c-116">조직에 대해 *Anyone* 링크를 해제 하려면</span><span class="sxs-lookup"><span data-stu-id="6320c-116">To turn off *Anyone* links for your organization</span></span>
1. <span data-ttu-id="6320c-117">SharePoint 관리 센터의 왼쪽 탐색 창에서 **공유**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6320c-117">In the SharePoint admin center, in the left navigation, click **Sharing**.</span></span>
2. <span data-ttu-id="6320c-118">SharePoint 외부 공유 설정을 **신규 및 기존 게스트**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6320c-118">Set the SharePoint external sharing settings to **New and existing guests**.</span></span></br>
   <span data-ttu-id="6320c-119">![SharePoint 사이트 외부 공유 설정 스크린샷](media/sharepoint-organization-external-sharing-controls-new-users.png)</span><span class="sxs-lookup"><span data-stu-id="6320c-119">![Screenshot of SharePoint site external sharing settings](media/sharepoint-organization-external-sharing-controls-new-users.png)</span></span>
3. <span data-ttu-id="6320c-120">**저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6320c-120">Click **Save**.</span></span>

<span data-ttu-id="6320c-121">사이트에 대해 *Anyone* 링크를 해제하려면</span><span class="sxs-lookup"><span data-stu-id="6320c-121">To turn off *Anyone* links for a site</span></span>
1. <span data-ttu-id="6320c-122">SharePoint 관리 센터의 왼쪽 탐색 창에서 **사이트**를 확장시키고 **Active 사이트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6320c-122">In the SharePoint admin center, in the left navigation, expand **Sites** and click **Active sites**.</span></span>
2. <span data-ttu-id="6320c-123">방금 생성한 팀의 사이트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6320c-123">Select the site for the team that you just created.</span></span>
3. <span data-ttu-id="6320c-124">리본 메뉴에서 **공유**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6320c-124">In the ribbon, click **Sharing**.</span></span>
4. <span data-ttu-id="6320c-125">공유가 **신규 및 기존 게스트로**설정되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="6320c-125">Ensure that sharing is set to **New and existing guests**.</span></span></br>
   <span data-ttu-id="6320c-126">![SharePoint 사이트 외부 공유 설정 스크린샷](media/sharepoint-site-external-sharing-settings.png)</span><span class="sxs-lookup"><span data-stu-id="6320c-126">![Screenshot of SharePoint site external sharing settings](media/sharepoint-site-external-sharing-settings.png)</span></span>
5. <span data-ttu-id="6320c-127">변경한 내용이 있으면 **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6320c-127">If you made changes, click **Save**.</span></span>

## <a name="domain-filtering"></a><span data-ttu-id="6320c-128">도메인 필터링</span><span class="sxs-lookup"><span data-stu-id="6320c-128">Domain filtering</span></span>

<span data-ttu-id="6320c-129">도메인 허용 또는 거부 목록을 사용하여 사용자가 조직 외부의 사람들과 공유할 수 있는 도메인을 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6320c-129">You can use domain allow or deny lists to determine domains your users can share with people outside your organization.</span></span>

<span data-ttu-id="6320c-130">허용 목록을 사용하여 조직의 사용자가 조직 외부의 사람들과 공유할 수있는 도메인 목록을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6320c-130">With an allow list, you can specify a list of domains where users in your organization can share with people outside your organization.</span></span> <span data-ttu-id="6320c-131">다른 도메인으로 공유하는 것은 차단됩니다.</span><span class="sxs-lookup"><span data-stu-id="6320c-131">Sharing with to other domains is blocked.</span></span> <span data-ttu-id="6320c-132">조직에서 특정 도메인 목록의 사람들과만 공동 작업을 하는 경우, 이 기능을 사용하여 다른 도메인과의 공유를 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6320c-132">If your organization only collaborates with guests from a list of specific domains, you can use this feature to prevent sharing with other domains.</span></span>

<span data-ttu-id="6320c-133">거부 목록을 사용하면 조직의 사용자가 조직 외부의 사람들과 공유할 수 없는 도메인 목록을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6320c-133">With a deny list, you can specify a list of domains from which users in your organization cannot invite guests.</span></span> <span data-ttu-id="6320c-134">나열된 도메인과의 공유는 차단됩니다.</span><span class="sxs-lookup"><span data-stu-id="6320c-134">Sharing with the listed domains is blocked.</span></span> <span data-ttu-id="6320c-135">이는 예를 들어 조직의 콘텐츠에 액세스하지 못하도록 하려는 경우와 같이 경쟁업체가 있는 경우 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6320c-135">This can be useful if you have competitors, for example, who you want to prevent from becoming guests in your organization.</span></span>

<span data-ttu-id="6320c-136">이 허용 및 거부 목록은 게스트와의 공유에만 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6320c-136">The allow and deny lists only affect sharing with authenticated guests.</span></span> <span data-ttu-id="6320c-137">사용자가 이를 비활성화시키지 않은 경우 사용자는 여전히 *Anyone* 링크를 사용하여 금지된 도메인의 사람들과 계속 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6320c-137">Users can still share with guests from prohibited domains by using *Anyone* links if you haven't disabled them.</span></span> <span data-ttu-id="6320c-138">도메인 허용과 거부 목록을 이용하여 최상의 결과를 내기 위해서는 위에 설명한 데로 *Anyone* 링크를 비활성화할 것을 고려합니다.</span><span class="sxs-lookup"><span data-stu-id="6320c-138">For best results with domain allow and deny lists, consider disabling *Anyone* links as described above.</span></span>

<span data-ttu-id="6320c-139">조직 외부의 사람들에 대한 도메인 허용 또는 거부 목록을 설정하려면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="6320c-139">To set up a domain allow or deny list for guest sharing</span></span>
1. <span data-ttu-id="6320c-140">왼쪽 탐색 창의 SharePoint 관리 센터에서 **공유**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6320c-140">In the SharePoint admin center, in the left navigation, click **Sharing**.</span></span>
2. <span data-ttu-id="6320c-141">**외부 공유에 대한 고급 설정**에서 **도메인 별 외부 공유 제한** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6320c-141">Under **Advanced settings for external sharing**, select the **Limit external sharing by domain** check box.</span></span>
3. <span data-ttu-id="6320c-142">**도메인 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6320c-142">Click **Add domains**.</span></span>
4. <span data-ttu-id="6320c-143">도메인을 차단할지를 선택하고 도메인을 입력한 후 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6320c-143">Select whether you want to block domains, type the domains, and click **OK**.</span></span></br>
   <span data-ttu-id="6320c-144">![도메인 별 SharePoint 외부 공유 제한 스크린샷](media/sharepoint-sharing-block-domain.png)</span><span class="sxs-lookup"><span data-stu-id="6320c-144">![Screenshot of SharePoint limit external sharing by domain setting](media/sharepoint-sharing-block-domain.png)</span></span>
5. <span data-ttu-id="6320c-145">**저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6320c-145">Click **Save**.</span></span>

<span data-ttu-id="6320c-146">SharePoint 및 OneDrive 보다 상위 수준에서 도메인 별로 공유를 제한하려는 경우 Azure Active Directory의 [특정 조직에서 B2B 사용자에 대한 초청을 허용하거나 차단](https://docs.microsoft.com/azure/active-directory/b2b/allow-deny-list)할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6320c-146">If you want to limit sharing by domain at a higher level than SharePoint and OneDrive, you can [allow or block invitations to B2B users from specific organizations](https://docs.microsoft.com/azure/active-directory/b2b/allow-deny-list) in Azure Active Directory.</span></span> <span data-ttu-id="6320c-147">설정이 SharePoint 및 OneDrive에 적용되도록 [Azure AD B2B 사전 검토와 Sharepoint 및 OneDrive의 통합](https://docs.microsoft.com/sharepoint/sharepoint-azureb2b-integration-preview)을 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6320c-147">(You must configure the [SharePoint and OneDrive integration with Azure AD B2B Preview](https://docs.microsoft.com/sharepoint/sharepoint-azureb2b-integration-preview) for these settings to affect SharePoint and OneDrive.)</span></span>

## <a name="limit-sharing-of-files-folders-and-sites-with-people-outside-your-organization-to-specified-security-groups"></a><span data-ttu-id="6320c-148">조직 외부의 사람들과 파일, 폴더 및 사이트 공유를 지정된 보안 그룹으로 제한하세요.</span><span class="sxs-lookup"><span data-stu-id="6320c-148">Limit sharing of files, folders, and sites with people outside your organization to specified security groups</span></span>

<span data-ttu-id="6320c-149">조직 외부의 사람과 파일, 폴더 및 사이트 공유를 특정 보안 그룹의 구성원으로 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6320c-149">You can restrict guest sharing of files, folders, and sites to members of a specific security group.</span></span> <span data-ttu-id="6320c-150">이 기능은 승인 워크플로 또는 요청 프로세스를 사용하여 외부 공유 기능을 활성화하려는 경우 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="6320c-150">This is useful if you want to enable guest sharing, but with an approval workflow or request process.</span></span>

<span data-ttu-id="6320c-151">보안 그룹의 구성원으로 외부 공유를 제한하려면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="6320c-151">To limit guest sharing to members of a security group</span></span>
1. <span data-ttu-id="6320c-152">왼쪽 탐색 창의 SharePoint 관리 센터에서 **공유**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6320c-152">In the SharePoint admin center, in the left navigation, click **Sharing**.</span></span>
2. <span data-ttu-id="6320c-153">**기타 설정**에서.</span><span class="sxs-lookup"><span data-stu-id="6320c-153">Under **Other settings**.</span></span> <span data-ttu-id="6320c-154">**외부 공유를 특정 보안 그룹으로 제한** 링크를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="6320c-154">follow the **Limit external sharing to specific security groups** link.</span></span>
3. <span data-ttu-id="6320c-155">**조직 외부에서 공유할 수 있는 사용자**에서 하나 또는 두 개의 확인란을 선택합니다: a.</span><span class="sxs-lookup"><span data-stu-id="6320c-155">Under **Who can share outside your organization**, select one or both of the check boxes: a.</span></span> <span data-ttu-id="6320c-156">인증된 사용자들과 공유할 수 있는 보안 그룹을 지정하기 위해 **선택된 보안 그룹에 있는 사용자들만 인증된 외부 사용자들과 공유하도록 합니다**b.</span><span class="sxs-lookup"><span data-stu-id="6320c-156">**Let only users in selected security groups share with authenticated external users** to specify a security group that can share with authenticated users b.</span></span> <span data-ttu-id="6320c-157">Anyone 링크를 사용하여 인증된 사용자들과 공유할 수 있는 보안 그룹을 지정하기 위해 **선택된 보안 그룹에 있는 사용자들만 익명의 링크를 사용하여 인증된 외부 사용자들과 공유하도록 합니다**</span><span class="sxs-lookup"><span data-stu-id="6320c-157">**Let only users in selected security groups share with authenticated external users and using anonymous links** to specify a security group that can share with authenticated users and by using Anyone links</span></span>
4. <span data-ttu-id="6320c-158">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6320c-158">Click **OK**.</span></span>

<span data-ttu-id="6320c-159">이는 파일, 폴더, 사이트에 영향을 주지만 Office 365 그룹 또는 팀은 영향을 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6320c-159">Note that this affects files, folders, and sites, but not Office 365 groups or Teams.</span></span> <span data-ttu-id="6320c-160">구성원이 게스트를 비공개 Office 365 그룹 또는 Microsoft 팀의 비공개 팀에 초청 시 초청장이 그룹 또는 팀 소유자에게 승인을 받기 위해 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="6320c-160">When members invite guests to a private Office 365 group or a private team in Microsoft Teams, the invitation is sent to the group or team owner for approval.</span></span>

## <a name="see-also"></a><span data-ttu-id="6320c-161">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6320c-161">See Also</span></span>

[<span data-ttu-id="6320c-162">보안 게스트 공유 환경 만들기</span><span class="sxs-lookup"><span data-stu-id="6320c-162">Create a secure guest sharing environment</span></span>](create-a-secure-guest-sharing-environment.md)

[<span data-ttu-id="6320c-163">익명 사용자와 파일 및 폴더를 공유 하는 최상의 방법</span><span class="sxs-lookup"><span data-stu-id="6320c-163">Best practices for sharing files and folders with anonymous users</span></span>](best-practices-anonymous-sharing.md)