---
title: 정치적 캠페인 개발/테스트 환경에서 팀 사이트 만들기
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/21/2018
ms.audience: ITPro
ms.topic: article
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.custom: ''
ms.assetid: c2112ce8-1c4b-424f-b200-59e161db2d21
description: '요약: 정치적 캠페인 개발/테스트 환경에서 공용, 개인, 중요 및 극비 SharePoint Online 팀 사이트를 만듭니다.'
ms.openlocfilehash: 03e73a540d1a92d20446d8e12066df87bd179293
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915263"
---
# <a name="create-team-sites-in-a-political-campaign-devtest-environment"></a><span data-ttu-id="3610c-103">정치적 캠페인 개발/테스트 환경에서 팀 사이트 만들기</span><span class="sxs-lookup"><span data-stu-id="3610c-103">Create team sites in a political campaign dev/test environment</span></span>

 <span data-ttu-id="3610c-104">**요약:** 정치적 캠페인 개발/테스트 환경에서 공용, 개인, 중요 및 극비 SharePoint Online 팀 사이트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-104">**Summary:** Create public, private, sensitive, and highly confidential SharePoint Online team sites in your political campaign dev/test environment.</span></span> 
  
<span data-ttu-id="3610c-p101">이 문서의 지침을 사용하여 [정치적 캠페인, 비영리 조직 및 기타 기밀 조직에 대한 Microsoft 보안 지침](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md) 솔루션에 대한 4가지 다른 유형의 SharePoint Online 팀 사이트가 포함된 개발/테스트 환경을 만듭니다. 이러한 사이트는 **SharePoint 및 비즈니스용 OneDrive** 제목의 항목 10에 자세히 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-p101">Use the instructions in this article to create a dev/test environment that includes the four different types of SharePoint Online team sites for the [Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md) solution. These sites are described in detail on Topic 10, titled **SharePoint and OneDrive for Business**.</span></span>
  
## <a name="phase-1-create-your-political-campaign-devtest-environment"></a><span data-ttu-id="3610c-107">1단계: 정치적 캠페인 개발/테스트 환경 만들기</span><span class="sxs-lookup"><span data-stu-id="3610c-107">Phase 1: Create your political campaign dev/test environment</span></span>

<span data-ttu-id="3610c-108">먼저 [정치적 캠페인 개발/테스트 환경에 대한 사용자 및 그룹 구성](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md)의 지침에 따라 구독, 사용자 및 그룹을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-108">First, follow the instructions in [Configure groups and users for a political campaign dev/test environment](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md) to create your subscriptions, users, and groups.</span></span>
  
## <a name="phase-2-create-office-365-labels"></a><span data-ttu-id="3610c-109">2단계: Office 365 레이블 만들기</span><span class="sxs-lookup"><span data-stu-id="3610c-109">Phase 2: Create Office 365 labels</span></span>

<span data-ttu-id="3610c-110">이 단계에서는 SharePoint Online 팀 사이트에 있는 문서 폴더의 다양한 보안 수준에 대한 레이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-110">In this phase, you create the labels for the different levels of security for SharePoint Online team site document folders.</span></span>
  
1. <span data-ttu-id="3610c-p102">필요한 경우 평가판 구독의 전역 관리자 계정 자격 증명으로 Office 365 포털에 로그인합니다. 도움을 받으려면 [Office 365에 로그인하는 위치](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3610c-p102">If needed, sign in to the Office 365 portal with the credentials of the global administrator account of your trial subscription. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="3610c-113">**Microsoft Office 홈** 탭에서 **관리** 타일을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-113">From the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="3610c-114">브라우저의 새 **Office 관리 센터** 탭에서 **관리 센터 > 보안 및 준수**를 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-114">From the new **Office Admin center** tab of your browser, click **Admin centers > Security &amp; Compliance**.</span></span>
    
4. <span data-ttu-id="3610c-115">브라우저의 새 **홈 - 보안 및 준수** 탭에서 **분류 > 레이블**을 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-115">From the new **Home - Security &amp; Compliance** tab of your browser, click **Classifications > Labels**.</span></span>
    
5. <span data-ttu-id="3610c-116">**홈 > 레이블** 창에서 **레이블 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-116">From the **Home > Labels** pane, click **Create a label**.</span></span>
    
6. <span data-ttu-id="3610c-117">**레이블 이름 지정** 창에서 **내부**를 입력하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-117">On the **Name your label** pane, type **Internal**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="3610c-118">**레이블 설정** 창에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-118">On the **Label settings** pane, click **Next**.</span></span>
    
8. <span data-ttu-id="3610c-119">**설정 검토** 창에서 **이 레이블 만들기**, **닫기**를 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-119">On the **Review your settings** pane, click **Create this label**, and then click **Close**.</span></span>
    
9. <span data-ttu-id="3610c-120">추가 레이블에 5-8단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-120">Repeat steps 5-8 for these additional labels:</span></span>
    
  - <span data-ttu-id="3610c-121">개인</span><span class="sxs-lookup"><span data-stu-id="3610c-121">Private</span></span>
    
  - <span data-ttu-id="3610c-122">중요</span><span class="sxs-lookup"><span data-stu-id="3610c-122">Sensitive</span></span>
    
  - <span data-ttu-id="3610c-123">극비</span><span class="sxs-lookup"><span data-stu-id="3610c-123">Highly Confidential</span></span>
    
10. <span data-ttu-id="3610c-124">**홈 > 레이블 ** 창에서 **레이블 게시**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-124">From the **Home > Labels** pane, click **Publish labels**.</span></span>
    
11. <span data-ttu-id="3610c-125">**게시할 레이블 선택** 창에서 **게시할 레이블 선택**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-125">On the **Choose labels to publish** pane, click **Choose labels to publish**.</span></span>
    
12. <span data-ttu-id="3610c-126">**레이블 선택** 창에서 **추가**를 클릭하고 네 개의 레이블을 모두 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-126">On the **Choose labels** pane, click **Add** and select all four labels.</span></span>
    
13. <span data-ttu-id="3610c-127">**완료**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-127">Click **Done**.</span></span>
    
14. <span data-ttu-id="3610c-128">**게시할 레이블 선택** 창에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-128">On the **Choose labels to publish** pane, click **Next**.</span></span>
    
15. <span data-ttu-id="3610c-129">**위치 선택** 창에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-129">On the **Choose locations** pane, click **Next**.</span></span>
    
16. <span data-ttu-id="3610c-130">**정책 이름 지정** 창에서 **이름**에 **캠페인**을 입력하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-130">On the **Name your policy** pane, type **Campaign** in **Name**, and then click **Next**.</span></span>
    
17. <span data-ttu-id="3610c-131">**설정 검토** 창에서 **레이블 게시**, **닫기**를 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-131">On the **Review your settings** pane, click **Publish labels**, and then click **Close**.</span></span>
    
## <a name="phase-3-create-your-sharepoint-online-team-sites"></a><span data-ttu-id="3610c-132">3단계: SharePoint Online 팀 사이트 만들기</span><span class="sxs-lookup"><span data-stu-id="3610c-132">Phase 3: Create your SharePoint Online team sites</span></span>

<span data-ttu-id="3610c-133">이 단계에서는 네 가지 유형의 SharePoint Online 팀 사이트에 해당하는 정치적 캠페인을 위한 SharePoint Online 팀 사이트를 만들고 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-133">In this phase, you create and configure SharePoint Online team sites for your political campaign corresponding to the four types of SharePoint Online team sites.</span></span>
  
### <a name="campaign-wide-team-site"></a><span data-ttu-id="3610c-134">캠페인 수준의 팀 사이트</span><span class="sxs-lookup"><span data-stu-id="3610c-134">Campaign wide team site</span></span>

<span data-ttu-id="3610c-135">초기 공용 SharePoint Online 팀 사이트를 만들려면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-135">To create a baseline public SharePoint Online team site, do the following:</span></span>
  
1. <span data-ttu-id="3610c-136">필요한 경우 로컬 컴퓨터에서 브라우저를 사용하여 전역 관리자 계정으로 Office 365 포털([https://portal.office.com](https://portal.office.com))에 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-136">If needed, use a browser on your local computer and sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using your global administrator account.</span></span>
    
2. <span data-ttu-id="3610c-137">타일 목록에서 **SharePoint**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-137">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="3610c-138">브라우저의 새 **SharePoint** 탭에서 **+ 사이트 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-138">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="3610c-139">**사이트 만들기** 페이지에서 **팀 사이트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-139">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="3610c-140">**사이트 이름**에 **캠페인 수준**을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-140">In **Site name**, type **Campaign wide**.</span></span> 
    
6. <span data-ttu-id="3610c-141">**팀 사이트 설명**에서 **전체 캠페인에 대한 SharePoint 사이트**를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-141">In **Team site description**, type **SharePoint site for the entire campaign**.</span></span>
    
7. <span data-ttu-id="3610c-142">**개인 정보 설정**에서 **공개 – 조직의 모든 사용자가 이 사이트에 액세스할 수 있습니다.** 를 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-142">In **Privacy settings**, select **Public - anyone in the organization can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="3610c-143">**어떤 사람을 추가하시겠습니까?** 창에서 **마침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-143">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="3610c-144">그런 다음, 내부 레이블에 대한 캠페인 수준 팀 사이트의 문서 폴더를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-144">Next, configure the documents folder of the Campaign wide team site for the Internal label.</span></span>
  
1. <span data-ttu-id="3610c-145">브라우저의 **캠페인 수준 - 홈** 탭에서 **문서**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-145">In the **Campaign wide-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="3610c-146">설정 아이콘을 클릭한 다음, **라이브러리 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-146">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="3610c-147">**권한 및 관리** 아래에서 **이 라이브러리의 항목에 레이블 적용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-147">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="3610c-148">**설정 - 레이블 적용**에서 **내부**를 선택하고 **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-148">In **Settings-Apply Label**, select **Internal**, and then click **Save**.</span></span>
    
### <a name="campaign-project-1-team-site"></a><span data-ttu-id="3610c-149">캠페인 프로젝트 1 팀 사이트</span><span class="sxs-lookup"><span data-stu-id="3610c-149">Campaign project 1 team site</span></span>

<span data-ttu-id="3610c-150">캠페인 내에서 프로젝트에 대한 초기 개인 SharePoint Online 팀 사이트를 만들려면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-150">To create a baseline private SharePoint Online team site for a project within the campaign, do the following:</span></span>
  
1. <span data-ttu-id="3610c-151">필요한 경우 로컬 컴퓨터에서 브라우저를 사용하여 전역 관리자 계정으로 Office 365 포털([https://portal.office.com](https://portal.office.com))에 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-151">If needed, use a browser on your local computer and sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using your global administrator account.</span></span>
    
2. <span data-ttu-id="3610c-152">타일 목록에서 **SharePoint**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-152">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="3610c-153">브라우저의 새 **SharePoint** 탭에서 **+ 사이트 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-153">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="3610c-154">**사이트 만들기** 페이지에서 **팀 사이트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-154">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="3610c-155">**사이트 이름**에 **캠페인 프로젝트 1**을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-155">In **Site name**, type **Campaign project 1**.</span></span> 
    
6. <span data-ttu-id="3610c-156">**팀 사이트 설명**에 **캠페인 프로젝트 1에 대한 SharePoint 사이트**를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-156">In **Team site description,** type **SharePoint site for Campaign project 1**.</span></span>
    
7. <span data-ttu-id="3610c-157">**개인 정보 설정**에서 **비공개 – 구성원만 이 사이트에 액세스할 수 있습니다.** 를 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-157">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="3610c-158">**어떤 사람을 추가하시겠습니까?** 창에서 **마침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-158">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="3610c-159">그런 다음, 비공개 레이블에 대한 캠페인 프로젝트 1 팀 사이트의 문서 폴더를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-159">Next, configure the documents folder of the Campaign project 1 team site for the Private label.</span></span>
  
1. <span data-ttu-id="3610c-160">브라우저의 **캠페인 프로젝트 1 - 홈** 탭에서 **문서**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-160">In the **Campaign project 1-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="3610c-161">설정 아이콘을 클릭한 다음, **라이브러리 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-161">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="3610c-162">**권한 및 관리** 아래에서 **이 라이브러리의 항목에 레이블 적용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-162">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="3610c-163">**설정 - 레이블 적용**에서 **개인**을 선택하고 **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-163">In **Settings-Apply Label**, select **Private**, and then click **Save**.</span></span>
    
### <a name="campaign-marketing-team-site"></a><span data-ttu-id="3610c-164">캠페인 마케팅 팀 사이트</span><span class="sxs-lookup"><span data-stu-id="3610c-164">Campaign marketing team site</span></span>

<span data-ttu-id="3610c-165">캠페인 마케팅 리소스에 대해 격리된 중요 수준 SharePoint Online 팀 사이트를 만들려면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-165">To create a sensitive-level isolated SharePoint Online team site for campaign marketing resources, do the following:</span></span>
  
1. <span data-ttu-id="3610c-166">로컬 컴퓨터에서 브라우저를 사용하여 전역 관리자 계정으로 Office 365 포털([https://portal.office.com](https://portal.office.com))에 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-166">Using a browser on your local computer, sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using your global administrator account.</span></span>
    
2. <span data-ttu-id="3610c-167">타일 목록에서 **SharePoint**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-167">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="3610c-168">브라우저의 새 **SharePoint** 탭에서 **+ 사이트 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-168">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="3610c-169">**사이트 만들기** 페이지에서 **팀 사이트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-169">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="3610c-170">**팀 사이트 이름**에 **캠페인 마케팅**을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-170">In **Team site name**, type **Campaign marketing**.</span></span>
    
6. <span data-ttu-id="3610c-171">**팀 사이트 설명**에 **캠페인 마케팅에 대한 SharePoint 사이트(중요)** 를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-171">In **Team site description**, type **SharePoint site for campaign marketing (sensitive)**.</span></span>
    
7.  <span data-ttu-id="3610c-172">**개인 정보 설정**에서 **비공개 – 구성원만 이 사이트에 액세스할 수 있습니다.** 를 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-172">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="3610c-173">**어떤 사람을 추가하시겠습니까?** 창에서 **마침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-173">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
9. <span data-ttu-id="3610c-174">브라우저의 새 **캠페인 마케팅** 탭에 있는 도구 모음에서 설정 아이콘을 클릭한 다음, **사이트 권한**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-174">On the new **Campaign marketing** tab in your browser, in the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
10. <span data-ttu-id="3610c-175">**사이트 권한** 창에서 **고급 권한 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-175">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
11. <span data-ttu-id="3610c-176">브라우저의 새 **권한** 탭에서 **액세스 요청 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-176">In the new **Permissions** tab in your browser, click **Access Request Settings**.</span></span>
    
12. <span data-ttu-id="3610c-177">**액세스 요청 설정** 대화 상자에서 **구성원이 사이트와 개별 파일 및 폴더를 공유할 수 있도록 허용합니다.** 및 **구성원이 다른 사용자들을 사이트 구성원 그룹에 초대할 수 있도록 허용합니다.** 확인란의 선택을 취소하고 **모든 액세스 요청 보내기**에 **ITAdmin1@**<your organization name> **.onmicrosoft.com**을 입력하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-177">In the **Access Request Settings** dialog box, clear the **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** check boxes, type **ITAdmin1@**<your organization name> **.onmicrosoft.com** in **Send all requests for access**, and then click **OK**.</span></span>
    
13. <span data-ttu-id="3610c-178">목록에서 **캠페인 마케팅 구성원**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-178">Click **Campaign marketing Members** in the list.</span></span>
    
14. <span data-ttu-id="3610c-179">**사용자 및 그룹** 페이지에서 **새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-179">On the **People and Groups** page, click **New**.</span></span>
    
15. <span data-ttu-id="3610c-180">**공유** 대화 상자에 **선임 및 전략적 직원**를 입력하고 선택한 후 **공유**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-180">In the **Share** dialog box, type **Senior and strategic staff**, select it, and then click **Share**.</span></span>
    
16. <span data-ttu-id="3610c-181">**분석 직원** 그룹과 **Regular1** 사용자 계정에 대해 14 및 15 단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-181">Repeat steps 14 and 15 for the **Analytics staff** group and the **Regular1** user account.</span></span>
    
17. <span data-ttu-id="3610c-182">브라우저에서 뒤로 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-182">Click the back button on your browser.</span></span>
    
18. <span data-ttu-id="3610c-183">목록에서 **캠페인 마케팅 소유자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-183">Click **Campaign marketing Owners** in the list.</span></span>
    
19. <span data-ttu-id="3610c-184">**사용자 및 그룹** 페이지에서 **새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-184">On the **People and Groups** page, click **New**.</span></span>
    
20. <span data-ttu-id="3610c-185">**공유** 대화 상자에서 **IT 직원**를 입력하고 선택한 후 **공유**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-185">In the **Share** dialog box, type **IT staff**, select it, and then click **Share**.</span></span>
    
21. <span data-ttu-id="3610c-186">브라우저에서 뒤로 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-186">Click the back button on your browser.</span></span>
    
22. <span data-ttu-id="3610c-187">브라우저에서 **사용자 및 그룹** 탭을 닫고 브라우저에서 **캠페인 마케팅 - 홈** 탭을 클릭한 다음, **사이트 권한** 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-187">Close the **People and Groups** tab in your browser, click the **Campaign marketing-Home** tab in your browser, and then close the **Site permissions** pane.</span></span>
    
<span data-ttu-id="3610c-188">권한 구성의 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-188">Here are the results of configuring permissions:</span></span>
  
- <span data-ttu-id="3610c-189">**캠페인 마케팅 - 구성원** SharePoint 그룹에는 **선임 및 전략적 직원** 그룹(Candidate, ChiefOfStaff 및 Strategic1 사용자 계정 포함), **마케팅 캠페인** 그룹(전역 관리자 사용자 계정 포함) 그룹, **분석 직원** 그룹(DataScientist1 사용자 계정을 포함) 및 **Regular1** 사용자 계정만 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-189">The **Campaign marketing-Members** SharePoint group contains only the **Senior and strategic staff** group (which contains the Candidate, ChiefOfStaff, and Strategic1 user accounts), the **Campaign marketing** group (which contains the global administrator user account), the **Analytics staff** group (which contains the DataScientist1 user account), and the **Regular1** user account.</span></span>
    
- <span data-ttu-id="3610c-190">**캠페인 마케팅 - 소유자** SharePoint 그룹에는 **IT 직원** 그룹(ITAdmin1 및 ITAdmin2 사용자 계정만 포함) 그룹만 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-190">The **Campaign marketing-Owners** SharePoint group contains only the **IT staff** group (which contains only the ITAdmin1 and ITAdmin2 user accounts).</span></span>
    
- <span data-ttu-id="3610c-191">**캠페인 마케팅 - 방문자** SharePoint 그룹에는 그룹 또는 사용자 계정이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-191">The **Campaign marketing-Visitors** SharePoint group contains no groups or user accounts.</span></span>
    
- <span data-ttu-id="3610c-192">구성원은 사이트 수준 권한을 수정할 수 없습니다(이 작업은 **캠페인 마케팅 - 소유자** 그룹의 구성원만 수행할 수 있음).</span><span class="sxs-lookup"><span data-stu-id="3610c-192">Members cannot modify site-level permissions (this can only be done by members of the **Campaign marketing-Owners** group).</span></span>
    
- <span data-ttu-id="3610c-193">다른 사용자 계정은 사이트 또는 해당 리소스에 액세스할 수 없지만, 해당 사이트에 대한 액세스는 요청할 수 있으며, 이 사이트에서 ITAdmin1 사용자 계정 사서함으로 전자 메일을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-193">Other user accounts cannot access the site or its resources, but can request access to the site, which will send an email to the ITAdmin1 user account mailbox.</span></span>
    
<span data-ttu-id="3610c-194">그런 다음, 중요 레이블에 대한 캠페인 마케팅 팀 사이트의 문서 폴더를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-194">Next, configure the documents folder of the Campaign marketing team site for the Sensitive label.</span></span>
  
1. <span data-ttu-id="3610c-195">브라우저의 **캠페인 마케팅 - 홈** 탭에서 **문서**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-195">In the **Campaign marketing-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="3610c-196">설정 아이콘을 클릭한 다음, **라이브러리 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-196">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="3610c-197">**권한 및 관리** 아래에서 **이 라이브러리의 항목에 레이블 적용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-197">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="3610c-198">**설정 - 레이블 적용**에서 **중요**를 선택하고 **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-198">In **Settings-Apply Label**, select **Sensitive**, and then click **Save**.</span></span>
    
<span data-ttu-id="3610c-p103">그런 다음, SharePoint Online 팀 사이트의 문서를 조직 외부의 중요 레이블과 공유할 때 사용자에게 알리는 DLP(데이터 손실 방지) 정책을 구성합니다. 이 DLP 정책은 캠페인 마케팅 사이트의 리소스에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-p103">Next, configure a data loss prevention (DLP) policy that notifies users when they share a document on a SharePoint Online team site with the Sensitive label outside the organization. This DLP policy will apply to resources in the Campaign marketing site.</span></span>
  
1. <span data-ttu-id="3610c-201">브라우저의 **Microsoft Office 홈** 탭에서 **보안 및 준수** 타일을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-201">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
2. <span data-ttu-id="3610c-202">브라우저의 새 **보안 및 준수** 탭에서 **데이터 손실 방지 > 정책**을 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-202">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
3. <span data-ttu-id="3610c-203">**데이터 손실 방지** 창에서 **+ 정책 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-203">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
4. <span data-ttu-id="3610c-204">**서식 파일로 시작하거나 사용자 지정 정책 만들기** 창에서 **사용자 지정**, **다음**을 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-204">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
5. <span data-ttu-id="3610c-205">**정책 이름 지정** 창의 **이름**에서 **중요 레이블 SharePoint Online 팀 사이트**를 입력하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-205">In the **Name your policy** pane, type **Sensitive label SharePoint Online team sites** in **Name**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="3610c-206">**위치 선택** 창에서 **특정 위치 선택 허용**을 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-206">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="3610c-207">위치 목록에서 **Exchange 전자 메일** 및 **OneDrive 계정** 위치를 사용하지 않도록 설정하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-207">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
8. <span data-ttu-id="3610c-208">**보호할 중요 정보의 유형 사용자 지정** 창에서 **편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-208">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
9. <span data-ttu-id="3610c-209">**보호할 콘텐츠 유형 선택** 창의 드롭다운 상자에서 **추가**, **레이블**을 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-209">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
10. <span data-ttu-id="3610c-210">**레이블** 창에서 **+ 추가**를 클릭하고, **중요** 레이블을 선택하고, **추가**를 클릭한 다음, **완료**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-210">In the **Labels** pane, click **+ Add**, select the **Sensitive** label, click **Add**, and then click **Done**.</span></span>
    
11. <span data-ttu-id="3610c-211">**보호할 콘텐츠 유형 선택** 창에서 **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-211">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
12. <span data-ttu-id="3610c-212">**Customize the types of sensitive info you want to protect(보호할 중요 정보 유형 사용자 지정)** 창에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-212">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
13. <span data-ttu-id="3610c-213">**중요한 정보를 발견하면 ** 창에서 **팁 및 전자 메일 사용자 지정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-213">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
14. <span data-ttu-id="3610c-214">**Customize policy tips and email notifications(정책 팁 및 전자 메일 알림 사용자 지정)** 창에서 **Customize the policy tip text(정책 팁 텍스트 사용자 지정)** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-214">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
15. <span data-ttu-id="3610c-215">텍스트 상자에 다음을 입력하거나 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-215">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="3610c-p104">조직 외부의 사용자와 공유하려면 파일을 다운로드한 다음 파일을 엽니다. 파일, 문서 보호, 암호 설정을 차례로 클릭한 다음 강력한 암호를 지정합니다. 암호를 별도의 전자 메일 또는 다른 통신 수단으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-p104">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
16. <span data-ttu-id="3610c-219">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-219">Click **OK**.</span></span>
    
17. <span data-ttu-id="3610c-220">**중요한 정보를 감지하는 경우 어떻게 하시겠어요?** 창에서 **사용자의 공유를 차단하고 공유 콘텐츠에 대한 액세스를 제한** 확인란의 선택을 취소하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-220">In the **What do you want to do if we detect sensitive info?** pane, clear the **Block people from sharing, and restrict access to shared content** check box, and then click **Next**.</span></span>
    
18. <span data-ttu-id="3610c-221">**정책을 켤까요 아니면 먼저 테스트를 수행할까요?** 창에서 **예, 지금 켜겠습니다.** 를 클릭하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-221">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="3610c-222">**설정 검토 창**에서 **만들기**, **닫기**를 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-222">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
### <a name="campaign-strategy-team-site"></a><span data-ttu-id="3610c-223">캠페인 전략 팀 사이트</span><span class="sxs-lookup"><span data-stu-id="3610c-223">Campaign strategy team site</span></span>

<span data-ttu-id="3610c-224">캠페인 전략 리소스에 대해 격리된 극비 수준의 SharePoint Online 팀 사이트를 만들려면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-224">To create an isolated SharePoint Online team site at the highly confidential level for campaign strategy resources, do the following:</span></span>
  
1. <span data-ttu-id="3610c-225">필요한 경우 로컬 컴퓨터에서 브라우저를 사용하여 전역 관리자 계정으로 Office 365 포털([https://portal.office.com](https://portal.office.com))에 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-225">If needed, use a browser on your local computer and sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using your global administrator account.</span></span>
    
2. <span data-ttu-id="3610c-226">타일 목록에서 **SharePoint**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-226">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="3610c-227">브라우저의 새 **SharePoint** 탭에서 **+ 사이트 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-227">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="3610c-228">**사이트 만들기** 페이지에서 **팀 사이트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-228">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="3610c-229">**팀 사이트 이름**에 **캠페인 전략**을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-229">In **Team site name**, type **Campaign strategy**.</span></span>
    
6. <span data-ttu-id="3610c-230">**팀 사이트 설명**에 **캠페인 전략에 대한 SharePoint 사이트(극비)** 를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-230">In **Team site description**, type **SharePoint site for campaign strategy (highly confidential)**.</span></span>
    
7.  <span data-ttu-id="3610c-231">**개인 정보 설정**에서 **비공개 – 구성원만 이 사이트에 액세스할 수 있습니다.** 를 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-231">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="3610c-232">**어떤 사람을 추가하시겠습니까?** 창에서 **마침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-232">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
9. <span data-ttu-id="3610c-233">브라우저의 새 **캠페인 전략** 탭에 있는 도구 모음에서 설정 아이콘을 클릭한 다음, **사이트 권한**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-233">On the new **Campaign strategy** tab in your browser, in the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
10. <span data-ttu-id="3610c-234">**사이트 권한** 창에서 **고급 권한 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-234">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
11. <span data-ttu-id="3610c-235">브라우저의 새 **권한** 탭에서 **액세스 요청 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-235">In the new **Permissions** tab in your browser, click **Access Request Settings**.</span></span>
    
12. <span data-ttu-id="3610c-236">**액세스 요청 설정** 대화 상자에서 **구성원이 사이트와 개별 파일 및 폴더를 공유할 수 있도록 허용합니다.** 및 **구성원이 다른 사용자들을 사이트 구성원 그룹에 초대할 수 있도록 허용합니다.** 확인란의 선택을 취소하고(3개 확인란이 모두 선택 취소됨) **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-236">In the **Access Request Settings** dialog box, clear **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** (so that all three check boxes are cleared), and then click **OK**.</span></span>
    
13. <span data-ttu-id="3610c-237">목록에서 **캠페인 전략 구성원**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-237">Click **Campaign strategy Members** in the list.</span></span>
    
14. <span data-ttu-id="3610c-238">**사용자 및 그룹** 페이지에서 **새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-238">On the **People and Groups** page, click **New**.</span></span>
    
15. <span data-ttu-id="3610c-239">**공유** 대화 상자에 **선임 및 전략적 직원**를 입력하고 선택한 후 **공유**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-239">In the **Share** dialog box, type **Senior and strategic staff**, select it, and then click **Share**.</span></span>
    
16. <span data-ttu-id="3610c-240">목록에서 **캠페인 전략 소유자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-240">Click **Campaign strategy Owners** in the list.</span></span>
    
17. <span data-ttu-id="3610c-241">**사용자 및 그룹** 페이지에서 **새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-241">On the **People and Groups** page, click **New**.</span></span>
    
18. <span data-ttu-id="3610c-242">**공유** 대화 상자에서 **IT 직원**를 입력하고 선택한 후 **공유**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-242">In the **Share** dialog box, type **IT staff**, select it, and then click **Share**.</span></span>
    
19. <span data-ttu-id="3610c-243">브라우저에서 뒤로 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-243">Click the back button on your browser.</span></span>
    
20. <span data-ttu-id="3610c-244">브라우저에서 **사용자 및 그룹** 탭을 닫고 브라우저에서 **캠페인 전략 - 홈** 탭을 클릭한 다음, **사이트 권한** 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-244">Close the **People and Groups** tab in your browser, click the **Campaign strategy-Home** tab in your browser, and then close the **Site permissions** pane.</span></span>
    
<span data-ttu-id="3610c-245">권한 구성의 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-245">Here are the results of configuring permissions:</span></span>
  
- <span data-ttu-id="3610c-246">**캠페인 전략 - 구성원** SharePoint 그룹에는 **선임 및 전략적 직원** 그룹(Candidate, ChiefOfStaff 및 Strategic1 사용자 계정만 포함) 및 **캠페인 전략** 그룹(전역 관리자 사용자 계정만 포함)만 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-246">The **Campaign strategy-Members** SharePoint group contains only the **Senior and strategic staff** group (which contains only the Candidate, ChiefOfStaff, and Strategic1 user accounts) and the **Campaign strategy** group (which contains only the global administrator user account).</span></span>
    
- <span data-ttu-id="3610c-247">**캠페인 전략 - 소유자** SharePoint 그룹에는 **IT 직원** 그룹(ITAdmin1 및 ITAdmin2 사용자 계정만 포함) 그룹만 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-247">The **Campaign strategy-Owners** SharePoint group contains only the **IT staff** group (which contains only the ITAdmin1 and ITAdmin2 user accounts).</span></span>
    
- <span data-ttu-id="3610c-248">**캠페인 전략 - 방문자** SharePoint 그룹에는 그룹 또는 사용자 계정이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-248">The **Campaign strategy-Visitors** SharePoint group contains no groups or user accounts.</span></span>
    
- <span data-ttu-id="3610c-249">구성원은 사이트 수준 권한을 수정할 수 없습니다(이 작업은 **캠페인 전략 - 소유자** 그룹의 구성원만 수행할 수 있음).</span><span class="sxs-lookup"><span data-stu-id="3610c-249">Members cannot modify site-level permissions (this can only be done by members of the **Campaign strategy-Owners** group).</span></span>
    
- <span data-ttu-id="3610c-p105">다른 사용자 계정은 사이트 또는 해당 리소스에 액세스하거나 사이트에 대한 액세스를 요청할 수 없습니다. 사이트에 대한 추가 권한은 전역 관리자 또는 **캠페인 전략 - 소유자** 그룹의 구성원이 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-p105">Other user accounts cannot access the site or its resources or request access to the site. Additional permissions to the site must be done by the global administrator or by a member of the **Campaign strategy-Owners** group.</span></span>
    
<span data-ttu-id="3610c-252">그런 다음, 극비 레이블에 대한 캠페인 전략 팀 사이트의 문서 폴더를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-252">Next, configure the documents folder of the Campaign strategy team site for the Highly Confidential label.</span></span>
  
1. <span data-ttu-id="3610c-253">브라우저의 **캠페인 전략 - 홈** 탭에서 **문서**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-253">In the **Campaign strategy-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="3610c-254">설정 아이콘을 클릭한 다음, **라이브러리 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-254">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="3610c-255">**권한 및 관리** 아래에서 **이 라이브러리의 항목에 레이블 적용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-255">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="3610c-256">**설정 - 레이블 적용**에서 **극비**를 선택하고 **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-256">In **Settings-Apply Label**, select **Highly Confidential**, and then click **Save**.</span></span>
    
<span data-ttu-id="3610c-p106">그런 다음, SharePoint Online 팀 사이트의 문서를 조직 외부의 극비 레이블과 공유할 때 사용자를 차단하는 DLP 정책을 구성합니다. 이 DLP 정책은 캠페인 전략 사이트의 리소스에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-p106">Next, configure a DLP policy that blocks users when they share a document on a SharePoint Online team site with the Highly Confidential label outside the organization. This DLP policy will apply to resources in the Campaign strategy site.</span></span>
  
1. <span data-ttu-id="3610c-259">필요한 경우 로컬 컴퓨터에서 브라우저를 사용하여 보안 관리자 또는 회사 관리자 역할이 있는 계정으로 Office 365 포털([https://portal.office.com](https://portal.office.com))에 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-259">If needed, use a browser on your local computer and sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) with an account that has the Security Administrator or Company Administrator role.</span></span>
    
2. <span data-ttu-id="3610c-260">브라우저의 **Microsoft Office 홈** 탭에서 **보안 및 준수** 타일을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-260">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
3. <span data-ttu-id="3610c-261">브라우저의 새 **보안 및 준수** 탭에서 **데이터 손실 방지 > 정책**을 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-261">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
4. <span data-ttu-id="3610c-262">**데이터 손실 방지** 창에서 **+ 정책 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-262">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
5. <span data-ttu-id="3610c-263">**서식 파일로 시작하거나 사용자 지정 정책 만들기** 창에서 **사용자 지정**, **다음**을 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-263">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="3610c-264">**정책 이름 지정** 창의 **이름**에서 **극비 레이블 SharePoint Online 팀 사이트**를 입력하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-264">In the **Name your policy** pane, type **Highly Confidential label SharePoint Online team sites** in **Name**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="3610c-265">**위치 선택** 창에서 **특정 위치 선택 허용**을 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-265">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="3610c-266">위치 목록에서 **Exchange 전자 메일** 및 **OneDrive 계정** 위치를 사용하지 않도록 설정하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-266">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
9. <span data-ttu-id="3610c-267">**보호할 중요 정보의 유형 사용자 지정** 창에서 **편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-267">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
10. <span data-ttu-id="3610c-268">**보호할 콘텐츠 유형 선택** 창의 드롭다운 상자에서 **추가**, **레이블**을 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-268">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
11. <span data-ttu-id="3610c-269">**레이블** 창에서 **+ 추가**를 클릭하고, **극비** 레이블을 선택하고, **추가**를 클릭한 다음, **완료**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-269">In the **Labels** pane, click **+ Add**, select the **Highly Confidential** label, click **Add**, and then click **Done**.</span></span>
    
12. <span data-ttu-id="3610c-270">**보호할 콘텐츠 유형 선택** 창에서 **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-270">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
13. <span data-ttu-id="3610c-271">**Customize the types of sensitive info you want to protect(보호할 중요 정보 유형 사용자 지정)** 창에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-271">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
14. <span data-ttu-id="3610c-272">**중요한 정보를 발견하면 ** 창에서 **팁 및 전자 메일 사용자 지정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-272">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
15. <span data-ttu-id="3610c-273">**Customize policy tips and email notifications(정책 팁 및 전자 메일 알림 사용자 지정)** 창에서 **Customize the policy tip text(정책 팁 텍스트 사용자 지정)** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-273">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
16. <span data-ttu-id="3610c-274">텍스트 상자에 다음을 입력하거나 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-274">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="3610c-p107">조직 외부의 사용자와 공유하려면 파일을 다운로드한 다음 파일을 엽니다. 파일, 문서 보호, 암호 설정을 차례로 클릭한 다음 강력한 암호를 지정합니다. 암호를 별도의 전자 메일 또는 다른 통신 수단으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-p107">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
17. <span data-ttu-id="3610c-278">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-278">Click **OK**.</span></span>
    
18. <span data-ttu-id="3610c-279">**중요한 정보를 감지하는 경우 어떻게 하시겠어요?** 창에서 **재정의하려면 비즈니스 사유 필요**를 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-279">In the **What do you want to do if we detect sensitive info?** pane, select **Require a business justification to override**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="3610c-280">**정책을 켤까요 아니면 먼저 테스트를 수행할까요?** 창에서 **예, 지금 켜겠습니다.** 를 클릭하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-280">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
20. <span data-ttu-id="3610c-281">**설정 검토 창**에서 **만들기**, **닫기**를 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-281">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
<span data-ttu-id="3610c-282">[Office 365 관리 센터에서 Azure RMS 활성화](https://docs.microsoft.com/information-protection/deploy-use/activate-office365)의 지침을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-282">Use the instructions in [Activate Azure RMS with the Office 365 admin center](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).</span></span>
  
<span data-ttu-id="3610c-283">다음으로, 아래 단계에 따라 보호 및 권한에 대한 새 범위 지정 정책 및 하위 레이블을 사용하여 Azure Information Protection을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-283">Next, configure Azure Information Protection with a new scoped policy and sub-label for protection and permissions with the following steps:</span></span>
  
1. <span data-ttu-id="3610c-p108">보안 관리자 또는 회사 관리자 역할이 있는 계정으로 Office 365 포털에 로그인합니다. 도움을 받으려면 [Office 365에 로그인하는 위치](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3610c-p108">Sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="3610c-286">브라우저의 별도 탭에서 Azure Portal([https://portal.azure.com](https://portal.azure.com))로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-286">In a separate tab of your browser, go to the Azure portal ([https://portal.azure.com](https://portal.azure.com)).</span></span>
    
3. <span data-ttu-id="3610c-287">처음으로 Azure Information Protection을 구성하는 경우 다음 [지침](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3610c-287">If this is the first time you are configuring Azure Information Protection, see these [instructions](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span></span>
    
4. <span data-ttu-id="3610c-288">목록 창에서 **모든 서비스**를 클릭하고 **정보**를 입력한 다음, **Azure Information Protection**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-288">In the list pane, click **All services**, type **information**, and then click **Azure Information Protection**.</span></span>

5. <span data-ttu-id="3610c-289">**레이블**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-289">Click **Labels**.</span></span>
    
6. <span data-ttu-id="3610c-290">**기밀** 레이블을 마우스 오른쪽 단추로 클릭하고 **하위 레이블 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-290">Right-click the **Highly Confidential** label, and then click **Add a sub-label**.</span></span>
    
7. <span data-ttu-id="3610c-291">**이름**에 **CampaignStrategy**를 입력하고 **설명**에 **캠페인 전략 팀 사이트의 문서에 대한 레이블**을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-291">Type **CampaignStrategy** in **Name** and **Label for documents in the Campaign strategy team site** in **Description**.</span></span>
    
8. <span data-ttu-id="3610c-292">**이 레이블을 포함하는 문서 및 전자 메일에 대한 권한 설정**에서 **보호**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-292">In **Set permissions for documents and emails containing this label**, click **Protect**.</span></span>
    
9. <span data-ttu-id="3610c-293">**보호** 섹션에서 **Azure(클라우드 키)** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-293">In the **Protection** section, click **Azure (cloud key)**.</span></span>
    
10. <span data-ttu-id="3610c-294">**보호** 블레이드의 **보호 설정** 아래에서 **+ 권한 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-294">On the **Protection** blade, under **Protection settings**, click **+ Add permissions**.</span></span>
    
11. <span data-ttu-id="3610c-295">**권한 추가** 블레이드의 **사용자 및 그룹 지정** 아래에서 **+ 디렉터리 찾아보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-295">On the **Add permissions** blade, under **Specify users and groups**, click **+ Browse directory**.</span></span>
    
12. <span data-ttu-id="3610c-296">**AAD 사용자 및 그룹** 창에서 **선임 및 전략적 직원**을 선택하고 **선택**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-296">On the **AAD Users and Groups** pane, select **Senior and strategic staff**, and then click **Select**.</span></span>
    
13. <span data-ttu-id="3610c-297">**미리 설정된 또는 설정된 사용자 지정에서 권한 선택**에서 **사용자 지정**을 클릭한 다음 **권한 보기**, **콘텐츠 편집**, **저장**, **회신** 및 **모두 회신** 확인란을 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-297">Under **Choose permissions from the preset or set custom**, click **Custom**, and then click the **View Rights**, **Edit Content**, **Save**, **Reply**, and **Reply all** check boxes.</span></span>
    
14. <span data-ttu-id="3610c-298">**확인**를 두 번 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-298">Click **OK** twice.</span></span>
    
15. <span data-ttu-id="3610c-299">**하위 레이블** 블레이드에서 **저장**을 클릭하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-299">On the **Sub-label** blade, click **Save**, and then click **OK**.</span></span>

16. <span data-ttu-id="3610c-300">**Azure Information Protection** 블레이드에서 **정책 > + 새 정책 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-300">On the **Azure Information protection** blade, click **Policies > + Add a new policy**.</span></span>
    
17. <span data-ttu-id="3610c-301">**정책 이름**에 **CampaignStrategy**를 입력하고 **설명**에 **캠페인 전략 팀 사이트의 문서**를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-301">Type **CampaignStrategy** in **Name** and **Documents in the Campaign strategy team site** in **Description**.</span></span>
    
18. <span data-ttu-id="3610c-302">**이 정책을 가져올 사용자 또는 그룹을 선택합니다 > 사용자/그룹**을 클릭한 후 **선임 및 전략적 직원**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-302">Click **Select which users or groups get this policy > User/Groups**, and then select **Senior and strategic staff**.</span></span>
    
19. <span data-ttu-id="3610c-303">**선택 > 확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-303">Click **Select > OK**.</span></span>

20. <span data-ttu-id="3610c-p109">**레이블 추가 또는 제거**를 클릭합니다. **정책: 레이블 추가 또는 제거** 창에서 **캠페인 전략**을 클릭하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-p109">Click **Add or remove labels**. In the **Policy: Add or remove labels** pane, click **CampaignStrategy**, and then click **OK**.</span></span>   

21. <span data-ttu-id="3610c-306">**저장**을 클릭한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-306">Click **Save**, and then click **OK**.</span></span>
  
<span data-ttu-id="3610c-307">이제 이러한 네 가지 사이트에서 문서를 만들고 다양한 사용자 계정으로 해당 문서에 대한 액세스를 테스트할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-307">You are now ready to begin creating documents in these four sites and test access to them with various user accounts.</span></span> 
  
<span data-ttu-id="3610c-308">Azure Information Protection 및 이 새로운 레이블을 사용하여 문서를 보호하려면 테스트 컴퓨터에 [Azure Information Protection 클라이언트를 설치](https://docs.microsoft.com/information-protection/rms-client/install-client-app)하고, Office 365 포털에서 Office를 설치한 다음, Microsoft Word에서 평가판 구독의 **선임 및 전략적 직원** 그룹에 속한 계정으로 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="3610c-308">To protect a document with Azure Information Protection and this new label, you must [install the Azure Information Protection client](https://docs.microsoft.com/information-protection/rms-client/install-client-app) on a test machine, install Office from the Office 365 portal, and then sign in from Microsoft Word with an account in the **Senior and strategic staff** group of your trial subscription.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="3610c-309">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3610c-309">See Also</span></span>

[<span data-ttu-id="3610c-310">정치적 캠페인, 비영리 조직 및 기타 기밀 조직에 대한 Microsoft 보안 지침</span><span class="sxs-lookup"><span data-stu-id="3610c-310">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="3610c-311">정치적 캠페인 개발/테스트 환경에 대해 그룹 및 사용자 구성</span><span class="sxs-lookup"><span data-stu-id="3610c-311">Configure groups and users for a political campaign dev/test environment</span></span>](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md)
  
[<span data-ttu-id="3610c-312">클라우드 도입 TLG(테스트 랩 가이드)</span><span class="sxs-lookup"><span data-stu-id="3610c-312">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="3610c-313">클라우드 도입 및 하이브리드 솔루션</span><span class="sxs-lookup"><span data-stu-id="3610c-313">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




