---
title: "정치적 캠페인 개발/테스트 환경에서 팀 사이트 만들기"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: None
ms.custom: Strat_O365_Enterprise
ms.assetid: c2112ce8-1c4b-424f-b200-59e161db2d21
description: "요약: 정치적 캠페인 개발/테스트 환경에서 공용, 개인, 소문자를 구분 및 기밀 사항이 SharePoint Online 팀 사이트를 만듭니다."
ms.openlocfilehash: cc410dc98e37ca6fc0e96f00f413e57ba1958d50
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/09/2018
---
# <a name="create-team-sites-in-a-political-campaign-devtest-environment"></a><span data-ttu-id="c2f51-103">정치적 캠페인 개발/테스트 환경에서 팀 사이트 만들기</span><span class="sxs-lookup"><span data-stu-id="c2f51-103">Create team sites in a political campaign dev/test environment</span></span>

 <span data-ttu-id="c2f51-104">**요약:** 정치적 캠페인 개발/테스트 환경에서 공용, 개인, 소문자를 구분 및 기밀 사항이 SharePoint Online 팀 사이트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-104">**Summary:** Create public, private, sensitive, and highly confidential SharePoint Online team sites in your political campaign dev/test environment.</span></span> 
  
<span data-ttu-id="c2f51-p101">[정치적 캠페인, 비영리, 및 기타 민첩 한 조직에 대 한 Microsoft 보안 지침](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md) 에 대 한 4 개의 다양 한 유형의 SharePoint Online 팀 사이트를 포함 하는 개발/테스트 환경을 만들기 위해이 문서의 지침을 사용 하 여 솔루션입니다. 이러한 사이트는 항목 10, 제목은 **SharePoint 및 비즈니스용 OneDrive에**자세히 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-p101">Use the instructions in this article to create a dev/test environment that includes the four different types of SharePoint Online team sites for the [Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md) solution. These sites are described in detail on Topic 10, titled **SharePoint and OneDrive for Business**.</span></span>
  
## <a name="phase-1-create-your-political-campaign-devtest-environment"></a><span data-ttu-id="c2f51-107">1 단계: 정치적 캠페인 개발/테스트 환경 만들기</span><span class="sxs-lookup"><span data-stu-id="c2f51-107">Phase 1: Create your political campaign dev/test environment</span></span>

<span data-ttu-id="c2f51-108">먼저, 사용자 구독, 사용자 및 그룹을 만들려면 [구성 그룹 및 정치적 캠페인 개발/테스트 환경에 대 한 사용자의](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md) 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-108">First, follow the instructions in [Configure groups and users for a political campaign dev/test environment](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md) to create your subscriptions, users, and groups.</span></span>
  
## <a name="phase-2-create-office-365-labels"></a><span data-ttu-id="c2f51-109">2 단계: Office 365 레이블 만들기</span><span class="sxs-lookup"><span data-stu-id="c2f51-109">Phase 2: Create Office 365 labels</span></span>

<span data-ttu-id="c2f51-110">이 단계에서는 다양 한 수준의 SharePoint Online 팀 사이트 문서 폴더에 대 한 보안에 대 한 레이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-110">In this phase, you create the labels for the different levels of security for SharePoint Online team site document folders.</span></span>
  
1. <span data-ttu-id="c2f51-p102">평가판 구독의 전역 관리자 계정의 자격 증명을 사용 하 여 Office 365 포털에 필요한 경우에 로그인 합니다. 도움말을 보려면 [Office 365에 로그인 할 위치](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="c2f51-p102">If needed, sign in to the Office 365 portal with the credentials of the global administrator account of your trial subscription. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="c2f51-113">**Microsoft Office 홈** 탭에서 **관리** 타일을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-113">From the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="c2f51-114">브라우저의 새 **Office 관리 센터** 탭을 클릭 **관리 센터 > 보안 &amp; 준수**합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-114">From the new **Office Admin center** tab of your browser, click **Admin centers > Security &amp; Compliance**.</span></span>
    
4. <span data-ttu-id="c2f51-115">새에서 **홈-보안 &amp; 준수** 탭 클릭 하 여 브라우저의 **분류 > 레이블**합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-115">From the new **Home - Security &amp; Compliance** tab of your browser, click **Classifications > Labels**.</span></span>
    
5. <span data-ttu-id="c2f51-116">**홈 > 레이블** 창 **레이블 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-116">From the **Home > Labels** pane, click **Create a label**.</span></span>
    
6. <span data-ttu-id="c2f51-117">**이름에 레이블** 창에서 **내부**입력 하 고 ****을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-117">On the **Name your label** pane, type **Internal**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="c2f51-118">**레이블 설정** 창에서 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-118">On the **Label settings** pane, click **Next**.</span></span>
    
8. <span data-ttu-id="c2f51-119">**설정 검토** 창에서 **이 레이블 만들기**를 클릭 하 고 **닫기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-119">On the **Review your settings** pane, click **Create this label**, and then click **Close**.</span></span>
    
9. <span data-ttu-id="c2f51-120">이러한 추가 레이블에 대 한 5 ~ 8 단계를 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-120">Repeat steps 5-8 for these additional labels:</span></span>
    
  - <span data-ttu-id="c2f51-121">개인</span><span class="sxs-lookup"><span data-stu-id="c2f51-121">Private</span></span>
    
  - <span data-ttu-id="c2f51-122">중요 한</span><span class="sxs-lookup"><span data-stu-id="c2f51-122">Sensitive</span></span>
    
  - <span data-ttu-id="c2f51-123">기밀</span><span class="sxs-lookup"><span data-stu-id="c2f51-123">Highly Confidential</span></span>
    
10. <span data-ttu-id="c2f51-124">**홈 > 레이블** 창 **게시 레이블**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-124">From the **Home > Labels** pane, click **Publish labels**.</span></span>
    
11. <span data-ttu-id="c2f51-125">**게시를 선택 레이블** 창에서 **게시를 선택 레이블을**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-125">On the **Choose labels to publish** pane, click **Choose labels to publish**.</span></span>
    
12. <span data-ttu-id="c2f51-126">**Choose 레이블** 창에서 **추가** 클릭 하 고 모든 4 개의 레이블을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-126">On the **Choose labels** pane, click **Add** and select all four labels.</span></span>
    
13. <span data-ttu-id="c2f51-127">**완료**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-127">Click **Done**.</span></span>
    
14. <span data-ttu-id="c2f51-128">**게시를 선택 레이블** 창에서 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-128">On the **Choose labels to publish** pane, click **Next**.</span></span>
    
15. <span data-ttu-id="c2f51-129">**Choose 위치** 창에서 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-129">On the **Choose locations** pane, click **Next**.</span></span>
    
16. <span data-ttu-id="c2f51-130">**이름에 정책** 창에서 **이름** **캠페인** 를 입력 하 고 ****을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-130">On the **Name your policy** pane, type **Campaign** in **Name**, and then click **Next**.</span></span>
    
17. <span data-ttu-id="c2f51-131">**설정 검토** 창에서 **게시 레이블**를 클릭 한 다음 **닫기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-131">On the **Review your settings** pane, click **Publish labels**, and then click **Close**.</span></span>
    
## <a name="phase-3-create-your-sharepoint-online-team-sites"></a><span data-ttu-id="c2f51-132">3 단계: SharePoint Online 팀 사이트 만들기</span><span class="sxs-lookup"><span data-stu-id="c2f51-132">Phase 3: Create your SharePoint Online team sites</span></span>

<span data-ttu-id="c2f51-133">이 단계에서 만들고 정치적 캠페인에 해당 하는 네가지 유형의 SharePoint Online 팀 사이트에 대 한 SharePoint Online 팀 사이트를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-133">In this phase, you create and configure SharePoint Online team sites for your political campaign corresponding to the four types of SharePoint Online team sites.</span></span>
  
### <a name="campaign-wide-team-site"></a><span data-ttu-id="c2f51-134">캠페인 전체 팀 사이트</span><span class="sxs-lookup"><span data-stu-id="c2f51-134">Campaign wide team site</span></span>

<span data-ttu-id="c2f51-135">초기 계획 공용 SharePoint Online 팀 사이트를 만들려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-135">To create a baseline public SharePoint Online team site, do the following:</span></span>
  
1. <span data-ttu-id="c2f51-136">필요한 경우 로컬 컴퓨터에서 브라우저를 사용 하 고 전역 관리자 계정을 사용 하 여 Office 365 포털 ([https://portal.office.com](https://portal.office.com))에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-136">If needed, use a browser on your local computer and sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using your global administrator account.</span></span>
    
2. <span data-ttu-id="c2f51-137">타일의 목록에서 **SharePoint**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-137">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="c2f51-138">브라우저에서 새 **SharePoint** 탭에서 **+ 사이트 만들기를**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-138">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="c2f51-139">**사이트 만들기** 페이지에서 **팀 사이트**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-139">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="c2f51-140">**사이트 이름** **캠페인 전체**를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-140">In **Site name**, type **Campaign wide**.</span></span> 
    
6. <span data-ttu-id="c2f51-141">**팀 사이트 설명** **전체 캠페인에 대 한 SharePoint 사이트**를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-141">In **Team site description**, type **SharePoint site for the entire campaign**.</span></span>
    
7. <span data-ttu-id="c2f51-142">**개인 설정** **공용-이 사이트에 액세스할 수는 조직의 모든 사용자**를 선택 하 고 ****을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-142">In **Privacy settings**, select **Public - anyone in the organization can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="c2f51-143">에 **가 수행 하려는 추가?** 창 **마침**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-143">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="c2f51-144">다음으로 내부 레이블에 대 한 캠페인 전체 팀 사이트의 문서 폴더를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-144">Next, configure the documents folder of the Campaign wide team site for the Internal label.</span></span>
  
1. <span data-ttu-id="c2f51-145">브라우저의 **캠페인 전체 홈** 탭에서 **문서**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-145">In the **Campaign wide-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="c2f51-146">설정 아이콘을 클릭 하 고 **라이브러리 설정**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-146">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="c2f51-147">**사용 권한 및 관리**, 아래에서 **이 라이브러리에 항목 레이블을 적용을**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-147">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="c2f51-148">**레이블 설정 적용** **내부**를 선택한 다음 **저장**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-148">In **Settings-Apply Label**, select **Internal**, and then click **Save**.</span></span>
    
### <a name="campaign-project-1-team-site"></a><span data-ttu-id="c2f51-149">캠페인 프로젝트 1 팀 사이트</span><span class="sxs-lookup"><span data-stu-id="c2f51-149">Campaign project 1 team site</span></span>

<span data-ttu-id="c2f51-150">캠페인 내에서 프로젝트에 대 한 초기 계획 개인 SharePoint Online 팀 사이트를 만들려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-150">To create a baseline private SharePoint Online team site for a project within the campaign, do the following:</span></span>
  
1. <span data-ttu-id="c2f51-151">필요한 경우 로컬 컴퓨터에서 브라우저를 사용 하 고 전역 관리자 계정을 사용 하 여 Office 365 포털 ([https://portal.office.com](https://portal.office.com))에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-151">If needed, use a browser on your local computer and sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using your global administrator account.</span></span>
    
2. <span data-ttu-id="c2f51-152">타일의 목록에서 **SharePoint**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-152">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="c2f51-153">브라우저에서 새 **SharePoint** 탭에서 **+ 사이트 만들기를**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-153">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="c2f51-154">**사이트 만들기** 페이지에서 **팀 사이트**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-154">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="c2f51-155">**사이트 이름** **캠페인 프로젝트 1을**입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-155">In **Site name**, type **Campaign project 1**.</span></span> 
    
6. <span data-ttu-id="c2f51-156">**팀 사이트 설명** 에서 **캠페인 프로젝트 1에 대 한 SharePoint 사이트**를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-156">In **Team site description,** type **SharePoint site for Campaign project 1**.</span></span>
    
7. <span data-ttu-id="c2f51-157">**개인정보 보호 설정**선택 **개인-이 사이트에 액세스할 수 있는 구성원만**, **다음**을 클릭 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-157">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="c2f51-158">에 **가 수행 하려는 추가?** 창 **마침**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-158">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="c2f51-159">다음으로 개인 레이블에 대 한 캠페인 프로젝트 1 팀 사이트의 문서 폴더를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-159">Next, configure the documents folder of the Campaign project 1 team site for the Private label.</span></span>
  
1. <span data-ttu-id="c2f51-160">브라우저의 **캠페인 프로젝트 1-홈** 탭에서 **문서**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-160">In the **Campaign project 1-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="c2f51-161">설정 아이콘을 클릭 하 고 **라이브러리 설정**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-161">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="c2f51-162">**사용 권한 및 관리**, 아래에서 **이 라이브러리에 항목 레이블을 적용을**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-162">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="c2f51-163">**레이블 설정 적용** **개인**을 선택 하 고 **저장**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-163">In **Settings-Apply Label**, select **Private**, and then click **Save**.</span></span>
    
### <a name="campaign-marketing-team-site"></a><span data-ttu-id="c2f51-164">팀 사이트를 마케팅 캠페인</span><span class="sxs-lookup"><span data-stu-id="c2f51-164">Campaign marketing team site</span></span>

<span data-ttu-id="c2f51-165">대부분은 중요 하지 수준의 격리 된 SharePoint Online 팀 사이트 리소스 마케팅 캠페인에 대 한를 만들려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-165">To create a sensitive-level isolated SharePoint Online team site for campaign marketing resources, do the following:</span></span>
  
1. <span data-ttu-id="c2f51-166">전역 관리자 계정을 사용 하 여 Office 365 포털 ([https://portal.office.com](https://portal.office.com))에 로그인 한 브라우저를 사용 하 여 로컬 컴퓨터에서 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-166">Using a browser on your local computer, sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using your global administrator account.</span></span>
    
2. <span data-ttu-id="c2f51-167">타일의 목록에서 **SharePoint**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-167">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="c2f51-168">브라우저에서 새 **SharePoint** 탭에서 **+ 사이트 만들기를**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-168">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="c2f51-169">**사이트 만들기** 페이지에서 **팀 사이트**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-169">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="c2f51-170">**팀 사이트 이름** **마케팅 캠페인을**입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-170">In **Team site name**, type **Campaign marketing**.</span></span>
    
6. <span data-ttu-id="c2f51-171">**팀 사이트 설명** **(중요) 마케팅 캠페인에 대 한 SharePoint 사이트**를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-171">In **Team site description**, type **SharePoint site for campaign marketing (sensitive)**.</span></span>
    
7.  <span data-ttu-id="c2f51-172">**개인정보 보호 설정**선택 **개인-이 사이트에 액세스할 수 있는 구성원만**, **다음**을 클릭 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-172">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="c2f51-173">에 **가 수행 하려는 추가?** 창 **마침**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-173">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
9. <span data-ttu-id="c2f51-174">도구 모음에서 브라우저에서 새 **캠페인 마케팅** 탭에서 설정 아이콘을 클릭 한 다음 **사이트 사용 권한**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-174">On the new **Campaign marketing** tab in your browser, in the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
10. <span data-ttu-id="c2f51-175">**사이트 사용 권한** 창에서 **고급 사용 권한 설정**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-175">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
11. <span data-ttu-id="c2f51-176">브라우저에서 새 **사용 권한** 탭에서 **액세스 요청 설정**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-176">In the new **Permissions** tab in your browser, click **Access Request Settings**.</span></span>
    
12. <span data-ttu-id="c2f51-177">**액세스 요청 설정** 대화 상자에서 확인란의 선택을 취소 **사이트 및 개별 파일 및 폴더 공유 허용 구성원** 및 **사이트 구성원 그룹에 다른 사용자를 초대 하도록 허용 구성원** 을 **@ ITAdmin1** 입력<your organization name> **합니다. onmicrosoft.com** **액세스에 대 한 모든 요청을 보낼**에서 한 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-177">In the **Access Request Settings** dialog box, clear the **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** check boxes, type **ITAdmin1@**<your organization name> **.onmicrosoft.com** in **Send all requests for access**, and then click **OK**.</span></span>
    
13. <span data-ttu-id="c2f51-178">목록에서 **구성원을 마케팅 캠페인** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-178">Click **Campaign marketing Members** in the list.</span></span>
    
14. <span data-ttu-id="c2f51-179">**사용자 및 그룹** 페이지에서 **새로 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-179">On the **People and Groups** page, click **New**.</span></span>
    
15. <span data-ttu-id="c2f51-180">**공유** 대화 상자에서 입력 **선임 및 전략적 직원을**선택한 다음 **공유**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-180">In the **Share** dialog box, type **Senior and strategic staff**, select it, and then click **Share**.</span></span>
    
16. <span data-ttu-id="c2f51-181">**분석 직원** 그룹 및 **Regular1** 사용자 계정에 대 한 14 및 15 단계를 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-181">Repeat steps 14 and 15 for the **Analytics staff** group and the **Regular1** user account.</span></span>
    
17. <span data-ttu-id="c2f51-182">브라우저에서 뒤로 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-182">Click the back button on your browser.</span></span>
    
18. <span data-ttu-id="c2f51-183">목록에서 **소유자를 마케팅 캠페인** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-183">Click **Campaign marketing Owners** in the list.</span></span>
    
19. <span data-ttu-id="c2f51-184">**사용자 및 그룹** 페이지에서 **새로 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-184">On the **People and Groups** page, click **New**.</span></span>
    
20. <span data-ttu-id="c2f51-185">**공유** 대화 상자에서 입력 **IT 담당자**를 선택한 다음 **공유**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-185">In the **Share** dialog box, type **IT staff**, select it, and then click **Share**.</span></span>
    
21. <span data-ttu-id="c2f51-186">브라우저에서 뒤로 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-186">Click the back button on your browser.</span></span>
    
22. <span data-ttu-id="c2f51-187">브라우저에서 **사용자 및 그룹** 탭을 닫은 브라우저에서 **캠페인 마케팅 홈** 탭을 클릭 한 다음 **사이트 사용 권한** 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-187">Close the **People and Groups** tab in your browser, click the **Campaign marketing-Home** tab in your browser, and then close the **Site permissions** pane.</span></span>
    
<span data-ttu-id="c2f51-188">사용 권한 구성 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-188">Here are the results of configuring permissions:</span></span>
  
- <span data-ttu-id="c2f51-189">**캠페인 마케팅 Members** SharePoint 그룹만 **선임 및 전략적 직원** 그룹이 포함 (포함 하는 후보, ChiefOfStaff, 및 Strategic1 사용자 계정), **캠페인 마케팅** 그룹 (포함 하는 전역 관리자 사용자 계정) (포함 하는 DataScientist1 사용자 계정)의 **분석 직원** 그룹 및 **Regular1** 사용자 계정입니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-189">The **Campaign marketing-Members** SharePoint group contains only the **Senior and strategic staff** group (which contains the Candidate, ChiefOfStaff, and Strategic1 user accounts), the **Campaign marketing** group (which contains the global administrator user account), the **Analytics staff** group (which contains the DataScientist1 user account), and the **Regular1** user account.</span></span>
    
- <span data-ttu-id="c2f51-190">**캠페인 마케팅 Owners** SharePoint 그룹의 **IT 담당자가** 그룹 (포함 하는 ITAdmin1 및 ITAdmin2 사용자 계정을)를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-190">The **Campaign marketing-Owners** SharePoint group contains only the **IT staff** group (which contains only the ITAdmin1 and ITAdmin2 user accounts).</span></span>
    
- <span data-ttu-id="c2f51-191">**캠페인 마케팅 방문자** SharePoint 그룹에는 없는 그룹이 나 사용자 계정을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-191">The **Campaign marketing-Visitors** SharePoint group contains no groups or user accounts.</span></span>
    
- <span data-ttu-id="c2f51-192">구성원 (이 수행할 수 있습니다 **캠페인 마케팅 소유자** 그룹의 구성원으로) 사이트 수준 사용 권한을 수정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-192">Members cannot modify site-level permissions (this can only be done by members of the **Campaign marketing-Owners** group).</span></span>
    
- <span data-ttu-id="c2f51-193">다른 사용자의 계정을 사이트 또는 해당 리소스에 액세스할 수 없습니다 하지만 ITAdmin1 사용자 계정 사서함을 전자 메일을 보내 하는 사이트에 대 한 액세스를 요청할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-193">Other user accounts cannot access the site or its resources, but can request access to the site, which will send an email to the ITAdmin1 user account mailbox.</span></span>
    
<span data-ttu-id="c2f51-194">다음으로 중요 한 레이블에 대 한 캠페인 마케팅 팀 사이트의 문서 폴더를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-194">Next, configure the documents folder of the Campaign marketing team site for the Sensitive label.</span></span>
  
1. <span data-ttu-id="c2f51-195">브라우저의 **캠페인 마케팅-홈** 탭에서 **문서**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-195">In the **Campaign marketing-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="c2f51-196">설정 아이콘을 클릭 하 고 **라이브러리 설정**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-196">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="c2f51-197">**사용 권한 및 관리**, 아래에서 **이 라이브러리에 항목 레이블을 적용을**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-197">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="c2f51-198">**레이블 설정 적용** **중요 한**을 선택 하 고 **저장**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-198">In **Settings-Apply Label**, select **Sensitive**, and then click **Save**.</span></span>
    
<span data-ttu-id="c2f51-p103">다음으로 SharePoint Online 팀 사이트의 문서에 조직 외부의 중요 한 레이블와 공유 하는 경우 사용자에 게 알리는 하는 데이터 손실 방지 (DLP) 정책을 구성 합니다. 이 DLP 정책 캠페인 마케팅 사이트의 리소스에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-p103">Next, configure a data loss prevention (DLP) policy that notifies users when they share a document on a SharePoint Online team site with the Sensitive label outside the organization. This DLP policy will apply to resources in the Campaign marketing site.</span></span>
  
1. <span data-ttu-id="c2f51-201">브라우저에서 **Microsoft Office 홈** 탭에서 클릭 된 **보안 &amp; 준수** 바둑판식으로 배열 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-201">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
2. <span data-ttu-id="c2f51-202">새에서 **보안 &amp; 준수** 브라우저에서 탭을 클릭 **데이터 손실 방지 > 정책**합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-202">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
3. <span data-ttu-id="c2f51-203">**데이터 손실 방지** 창에서 **+ 정책 만들기를**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-203">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
4. <span data-ttu-id="c2f51-204">**서식 파일을 시작 하거나 사용자 지정 정책을 만들** 창 **사용자 지정**을 클릭 하 고 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-204">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
5. <span data-ttu-id="c2f51-205">**이름에 정책** 창에서 **이름** **중요 한 레이블 SharePoint Online 팀 사이트** 를 입력 하 고 ****을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-205">In the **Name your policy** pane, type **Sensitive label SharePoint Online team sites** in **Name**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="c2f51-206">**선택 위치** 창에서 **특정 위치를 선택 합니다.**를 클릭 하 고 ****을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-206">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="c2f51-207">위치 목록에서 **Exchange 전자 메일** 및 **OneDrive 계정** 위치를 사용 하지 않도록 설정 하 고 ****을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-207">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
8. <span data-ttu-id="c2f51-208">**중요 한 정보를 보호 하려면 유형의 사용자 지정** 창에서 **편집**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-208">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
9. <span data-ttu-id="c2f51-209">**보호 하기 위해 콘텐츠 형식 선택** 창에서 드롭다운 목록 상자에서 **추가** 클릭 하 고 **레이블**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-209">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
10. <span data-ttu-id="c2f51-210">**레이블** 창에서 **+ 기호 추가**클릭, **중요 한** 레이블을 선택, **추가**클릭 하 고 **완료**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-210">In the **Labels** pane, click **+ Add**, select the **Sensitive** label, click **Add**, and then click **Done**.</span></span>
    
11. <span data-ttu-id="c2f51-211">**보호 하기 위해 콘텐츠 형식 선택** 창에서 **저장**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-211">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
12. <span data-ttu-id="c2f51-212">**중요 한 정보를 보호 하려면 유형의 사용자 지정** 창에서 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-212">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
13. <span data-ttu-id="c2f51-213">**는 중요 한 정보를 검색 하는 경우 작업을 수행 하 시겠습니까?** 창 **사용자 지정 팁 및 전자 메일을**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-213">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
14. <span data-ttu-id="c2f51-214">**사용자 지정 정책 팁 및 전자 메일 알림** 창에서 **사용자 지정 정책 팁 텍스트를**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-214">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
15. <span data-ttu-id="c2f51-215">텍스트 상자에 입력 하거나 다음에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-215">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="c2f51-p104">조직 외부의 사용자와 공유 하려면 파일을 다운로드 하 고 파일을 엽니다. 파일을 다음 문서 보호를 클릭 하 고 암호를 암호화 하 고 강력한 암호를 지정 합니다. 별도 전자 메일 또는 다른 수단 통신의 암호를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-p104">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
16. <span data-ttu-id="c2f51-219">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-219">Click **OK**.</span></span>
    
17. <span data-ttu-id="c2f51-220">**는 중요 한 정보를 검색 하는 경우 작업을 수행 하 시겠습니까?** 창에서 **공유, 다른 사람을 차단 하 고 공유 내용에 대 한 액세스를 제한** 확인란의 선택을 취소 하 고 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-220">In the **What do you want to do if we detect sensitive info?** pane, clear the **Block people from sharing, and restrict access to shared content** check box, and then click **Next**.</span></span>
    
18. <span data-ttu-id="c2f51-221">**먼저 수행 정책 또는 테스트 작업을 설정 하 시겠습니까?** 창 **예, 귀하가 켜기**를 클릭 한 후에 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-221">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="c2f51-222">**설정 검토** 창에서 **만들기**를 클릭 한 다음 **닫기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-222">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
### <a name="campaign-strategy-team-site"></a><span data-ttu-id="c2f51-223">캠페인 전략 팀 사이트</span><span class="sxs-lookup"><span data-stu-id="c2f51-223">Campaign strategy team site</span></span>

<span data-ttu-id="c2f51-224">캠페인 전략 리소스에 대 한 매우 기밀 수준에서 격리 된 SharePoint Online 팀 사이트를 만들려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-224">To create an isolated SharePoint Online team site at the highly confidential level for campaign strategy resources, do the following:</span></span>
  
1. <span data-ttu-id="c2f51-225">필요한 경우 로컬 컴퓨터에서 브라우저를 사용 하 고 전역 관리자 계정을 사용 하 여 Office 365 포털 ([https://portal.office.com](https://portal.office.com))에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-225">If needed, use a browser on your local computer and sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using your global administrator account.</span></span>
    
2. <span data-ttu-id="c2f51-226">타일의 목록에서 **SharePoint**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-226">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="c2f51-227">브라우저에서 새 **SharePoint** 탭에서 **+ 사이트 만들기를**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-227">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="c2f51-228">**사이트 만들기** 페이지에서 **팀 사이트**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-228">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="c2f51-229">**팀 사이트 이름** **캠페인 전략**을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-229">In **Team site name**, type **Campaign strategy**.</span></span>
    
6. <span data-ttu-id="c2f51-230">**팀 사이트 설명** **캠페인 전략 (기밀)에 대 한 SharePoint 사이트**를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-230">In **Team site description**, type **SharePoint site for campaign strategy (highly confidential)**.</span></span>
    
7.  <span data-ttu-id="c2f51-231">**개인정보 보호 설정**선택 **개인-이 사이트에 액세스할 수 있는 구성원만**, **다음**을 클릭 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-231">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="c2f51-232">에 **가 수행 하려는 추가?** 창 **마침**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-232">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
9. <span data-ttu-id="c2f51-233">도구 모음에서 브라우저에서 새 **캠페인 전략** 탭에서 설정 아이콘을 클릭 한 다음 **사이트 사용 권한**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-233">On the new **Campaign strategy** tab in your browser, in the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
10. <span data-ttu-id="c2f51-234">**사이트 사용 권한** 창에서 **고급 사용 권한 설정**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-234">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
11. <span data-ttu-id="c2f51-235">브라우저에서 새 **사용 권한** 탭에서 **액세스 요청 설정**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-235">In the new **Permissions** tab in your browser, click **Access Request Settings**.</span></span>
    
12. <span data-ttu-id="c2f51-236">**액세스 요청 설정** 대화 상자에서 **사이트 및 개별 파일 및 폴더 공유 허용 구성원** 및 **사이트 구성원 그룹에 다른 사용자를 초대 하도록 허용 구성원** (있도록 삭제 세 확인란을 모두 선택이 취소 됩니다), 다음 **를 클릭 하 고 확인**합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-236">In the **Access Request Settings** dialog box, clear **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** (so that all three check boxes are cleared), and then click **OK**.</span></span>
    
13. <span data-ttu-id="c2f51-237">목록에서 **캠페인 전략 구성원을** 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-237">Click **Campaign strategy Members** in the list.</span></span>
    
14. <span data-ttu-id="c2f51-238">**사용자 및 그룹** 페이지에서 **새로 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-238">On the **People and Groups** page, click **New**.</span></span>
    
15. <span data-ttu-id="c2f51-239">**공유** 대화 상자에서 입력 **선임 및 전략적 직원을**선택한 다음 **공유**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-239">In the **Share** dialog box, type **Senior and strategic staff**, select it, and then click **Share**.</span></span>
    
16. <span data-ttu-id="c2f51-240">목록에서 **캠페인 전략 소유자를** 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-240">Click **Campaign strategy Owners** in the list.</span></span>
    
17. <span data-ttu-id="c2f51-241">**사용자 및 그룹** 페이지에서 **새로 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-241">On the **People and Groups** page, click **New**.</span></span>
    
18. <span data-ttu-id="c2f51-242">**공유** 대화 상자에서 입력 **IT 담당자**를 선택한 다음 **공유**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-242">In the **Share** dialog box, type **IT staff**, select it, and then click **Share**.</span></span>
    
19. <span data-ttu-id="c2f51-243">브라우저에서 뒤로 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-243">Click the back button on your browser.</span></span>
    
20. <span data-ttu-id="c2f51-244">브라우저에서 **사용자 및 그룹** 탭을 닫은 브라우저에서 **전략 홈 캠페인** 탭을 클릭 한 다음 **사이트 사용 권한** 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-244">Close the **People and Groups** tab in your browser, click the **Campaign strategy-Home** tab in your browser, and then close the **Site permissions** pane.</span></span>
    
<span data-ttu-id="c2f51-245">사용 권한 구성 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-245">Here are the results of configuring permissions:</span></span>
  
- <span data-ttu-id="c2f51-246">**캠페인 전략 Members** SharePoint 그룹에만 하는 **수석 및 전략적 직원** 그룹 (후보, ChiefOfStaff, 및 Strategic1 사용자 계정을 포함)와 (포함 하는 **캠페인 전략** 그룹 포함 전역 관리자 사용자 계정만)입니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-246">The **Campaign strategy-Members** SharePoint group contains only the **Senior and strategic staff** group (which contains only the Candidate, ChiefOfStaff, and Strategic1 user accounts) and the **Campaign strategy** group (which contains only the global administrator user account).</span></span>
    
- <span data-ttu-id="c2f51-247">**캠페인 전략 Owners** SharePoint 그룹의 **IT 담당자가** 그룹 (포함 하는 ITAdmin1 및 ITAdmin2 사용자 계정을)를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-247">The **Campaign strategy-Owners** SharePoint group contains only the **IT staff** group (which contains only the ITAdmin1 and ITAdmin2 user accounts).</span></span>
    
- <span data-ttu-id="c2f51-248">**캠페인 전략 방문자** SharePoint 그룹에는 없는 그룹이 나 사용자 계정을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-248">The **Campaign strategy-Visitors** SharePoint group contains no groups or user accounts.</span></span>
    
- <span data-ttu-id="c2f51-249">구성원 (이 수행할 수 있습니다 **캠페인 전략 소유자** 그룹의 구성원으로) 사이트 수준 사용 권한을 수정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-249">Members cannot modify site-level permissions (this can only be done by members of the **Campaign strategy-Owners** group).</span></span>
    
- <span data-ttu-id="c2f51-p105">다른 사용자의 계정을 사이트 또는 해당 리소스에 액세스 하거나 사이트에 대 한 액세스를 요청할 수 없습니다. 사이트에 추가 사용 권한이 전역 관리자에 의해 또는 **캠페인 전략 소유자** 그룹의 구성원에 의해 수행 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-p105">Other user accounts cannot access the site or its resources or request access to the site. Additional permissions to the site must be done by the global administrator or by a member of the **Campaign strategy-Owners** group.</span></span>
    
<span data-ttu-id="c2f51-252">다음으로 기밀로 레이블에 대 한 캠페인 전략 팀 사이트의 문서 폴더를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-252">Next, configure the documents folder of the Campaign strategy team site for the Highly Confidential label.</span></span>
  
1. <span data-ttu-id="c2f51-253">브라우저의 **캠페인 전략 홈** 탭에서 **문서**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-253">In the **Campaign strategy-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="c2f51-254">설정 아이콘을 클릭 하 고 **라이브러리 설정**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-254">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="c2f51-255">**사용 권한 및 관리**, 아래에서 **이 라이브러리에 항목 레이블을 적용을**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-255">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="c2f51-256">**레이블 설정 적용** **매우 기밀**을 선택 하 고 **저장**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-256">In **Settings-Apply Label**, select **Highly Confidential**, and then click **Save**.</span></span>
    
<span data-ttu-id="c2f51-p106">다음으로, DLP 정책 구성 요소 (영문)가 사용 하는 조직 외부의 기밀 사항이 레이블로 SharePoint Online 팀 사이트에 문서를 공유 하는 경우. 이 DLP 정책 캠페인 전략 사이트의 리소스에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-p106">Next, configure a DLP policy that blocks users when they share a document on a SharePoint Online team site with the Highly Confidential label outside the organization. This DLP policy will apply to resources in the Campaign strategy site.</span></span>
  
1. <span data-ttu-id="c2f51-259">필요한 경우 로컬 컴퓨터에서 브라우저를 사용 하 고 보안 관리자 또는 회사 관리자 역할을 가진 계정으로 사용 하 여 Office 365 포털 ([https://portal.office.com](https://portal.office.com))에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-259">If needed, use a browser on your local computer and sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) with an account that has the Security Administrator or Company Administrator role.</span></span>
    
2. <span data-ttu-id="c2f51-260">브라우저에서 **Microsoft Office 홈** 탭에서 클릭 된 **보안 &amp; 준수** 바둑판식으로 배열 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-260">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
3. <span data-ttu-id="c2f51-261">새에서 **보안 &amp; 준수** 브라우저에서 탭을 클릭 **데이터 손실 방지 > 정책**합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-261">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
4. <span data-ttu-id="c2f51-262">**데이터 손실 방지** 창에서 **+ 정책 만들기를**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-262">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
5. <span data-ttu-id="c2f51-263">**서식 파일을 시작 하거나 사용자 지정 정책을 만들** 창 **사용자 지정**을 클릭 하 고 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-263">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="c2f51-264">**이름에 정책** 창에서 **이름** **매우 기밀 레이블 SharePoint Online 팀 사이트** 를 입력 하 고 ****을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-264">In the **Name your policy** pane, type **Highly Confidential label SharePoint Online team sites** in **Name**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="c2f51-265">**선택 위치** 창에서 **특정 위치를 선택 합니다.**를 클릭 하 고 ****을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-265">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="c2f51-266">위치 목록에서 **Exchange 전자 메일** 및 **OneDrive 계정** 위치를 사용 하지 않도록 설정 하 고 ****을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-266">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
9. <span data-ttu-id="c2f51-267">**중요 한 정보를 보호 하려면 유형의 사용자 지정** 창에서 **편집**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-267">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
10. <span data-ttu-id="c2f51-268">**보호 하기 위해 콘텐츠 형식 선택** 창에서 드롭다운 목록 상자에서 **추가** 클릭 하 고 **레이블**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-268">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
11. <span data-ttu-id="c2f51-269">**레이블** 창에서 **+ 기호 추가**클릭, **기밀 사항이** 레이블을 선택, **추가**클릭 하 고 **완료**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-269">In the **Labels** pane, click **+ Add**, select the **Highly Confidential** label, click **Add**, and then click **Done**.</span></span>
    
12. <span data-ttu-id="c2f51-270">**보호 하기 위해 콘텐츠 형식 선택** 창에서 **저장**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-270">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
13. <span data-ttu-id="c2f51-271">**중요 한 정보를 보호 하려면 유형의 사용자 지정** 창에서 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-271">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
14. <span data-ttu-id="c2f51-272">**는 중요 한 정보를 검색 하는 경우 작업을 수행 하 시겠습니까?** 창 **사용자 지정 팁 및 전자 메일을**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-272">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
15. <span data-ttu-id="c2f51-273">**사용자 지정 정책 팁 및 전자 메일 알림** 창에서 **사용자 지정 정책 팁 텍스트를**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-273">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
16. <span data-ttu-id="c2f51-274">텍스트 상자에 입력 하거나 다음에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-274">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="c2f51-p107">조직 외부의 사용자와 공유 하려면 파일을 다운로드 하 고 파일을 엽니다. 파일을 다음 문서 보호를 클릭 하 고 암호를 암호화 하 고 강력한 암호를 지정 합니다. 별도 전자 메일 또는 다른 수단 통신의 암호를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-p107">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
17. <span data-ttu-id="c2f51-278">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-278">Click **OK**.</span></span>
    
18. <span data-ttu-id="c2f51-279">**는 중요 한 정보를 검색 하는 경우 작업을 수행 하 시겠습니까?** 창 **, 업무 효율성을 재정의 하려면 필요**를 선택 하 고 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-279">In the **What do you want to do if we detect sensitive info?** pane, select **Require a business justification to override**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="c2f51-280">**먼저 수행 정책 또는 테스트 작업을 설정 하 시겠습니까?** 창 **예, 귀하가 켜기**를 클릭 한 후에 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-280">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
20. <span data-ttu-id="c2f51-281">**설정 검토** 창에서 **만들기**를 클릭 한 다음 **닫기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-281">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
<span data-ttu-id="c2f51-282">[Office 365 관리 센터와 Azure RMS 활성화](https://docs.microsoft.com/information-protection/deploy-use/activate-office365)의 지침을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-282">Use the instructions in [Activate Azure RMS with the Office 365 admin center](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).</span></span>
  
<span data-ttu-id="c2f51-283">다음, 새 범위가 지정 된 정책 및 하위 레이블 보호 및 다음 단계를 사용 하 여 권한을 사용 하 여 Azure 정보 보호를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-283">Next, configure Azure Information Protection with a new scoped policy and sub-label for protection and permissions with the following steps:</span></span>
  
1. <span data-ttu-id="c2f51-p108">보안 관리자 또는 회사 관리자 역할을 가진 계정으로 사용 하 여 Office 365 포털에 로그인 합니다. 도움말을 보려면 [Office 365에 로그인 할 위치](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="c2f51-p108">Sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="c2f51-286">브라우저의 별도 탭에서 Azure 포털 ([https://portal.azure.com](https://portal.azure.com))로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-286">In a separate tab of your browser, go to the Azure portal ([https://portal.azure.com](https://portal.azure.com)).</span></span>
    
3. <span data-ttu-id="c2f51-287">처음으로 Azure 정보 보호를 구성 하는 경우 다음 [지침](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="c2f51-287">If this is the first time you are configuring Azure Information Protection, see these [instructions](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span></span>
    
4. <span data-ttu-id="c2f51-288">목록 창에서 **서비스를 더**, **정보**를 입력 한 다음 **Azure 정보 보호**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-288">In the list pane, click **More services**, type **information**, and then click **Azure Information Protection**.</span></span>
    
5. <span data-ttu-id="c2f51-289">**Azure 정보 보호** 블레이드에서를 클릭 **정책 범위 > 새 정책을 추가 +**합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-289">On the **Azure Information protection** blade, , click **Scoped policies > + Add a new policy**.</span></span>
    
6. <span data-ttu-id="c2f51-290">**정책 이름** 및 **설명**에 **캠페인 전략 팀 사이트의 문서에 대 한 레이블** **CampaignStrategy** 를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-290">Type **CampaignStrategy** in **Policy name** and **Label for documents in the Campaign strategy team site** in **Description**.</span></span>
    
7. <span data-ttu-id="c2f51-291">클릭 **있는 사용자 또는 그룹에이 정책을 가져오려면 선택 > 사용자/그룹**, 다음 **선임 및 전략적 직원을**선택 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-291">Click **Select which users or groups get this policy > User/Groups**, and then select **Senior and strategic staff**.</span></span>
    
8. <span data-ttu-id="c2f51-292">클릭 **선택 > 확인**합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-292">Click **Select > OK**.</span></span>
    
9. <span data-ttu-id="c2f51-293">**기밀 사항이** 레이블에 대 한 줄임표 (...)를 클릭 하 고 **하위 레이블 추가**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-293">For the **Highly Confidential** label, click the ellipses (…), and then click **Add a sub-label**.</span></span>
    
10. <span data-ttu-id="c2f51-294">**이름** 및 **설명**의 레이블 내에 대 한 설명을 하위 레이블에 대 한 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-294">Type a name for the sub-label in **Name** and a description of the label in **Description**.</span></span>
    
11. <span data-ttu-id="c2f51-295">**문서 및이 레이블이 포함 된 전자 메일에 대 한 사용 권한 설정**에서 **암호로 보호**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-295">In **Set permissions for documents and emails containing this label**, click **Protect**.</span></span>
    
12. <span data-ttu-id="c2f51-296">**보호** 섹션에서 **Azure (클라우드 키)를**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-296">In the **Protection** section, click **Azure (cloud key)**.</span></span>
    
13. <span data-ttu-id="c2f51-297">**보호** 블레이드 **보호 설정**아래에서 **+ 추가 사용 권한을**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-297">On the **Protection** blade, under **Protection settings**, click **+ Add permissions**.</span></span>
    
14. <span data-ttu-id="c2f51-298">**추가 사용 권한** 블레이드 **지정 사용자 및 그룹을**에서 **디렉터리 찾아보기 +**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-298">On the **Add permissions** blade, under **Specify users and groups**, click **+ Browse directory**.</span></span>
    
15. <span data-ttu-id="c2f51-299">**AAD 사용자 및 그룹** 창에서 **수석 및 전략적 직원을**선택한 다음 **선택**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-299">On the **AAD Users and Groups** pane, select **Senior and strategic staff**, and then click **Select**.</span></span>
    
16. <span data-ttu-id="c2f51-300">**사전 설정에서 사용 권한을 선택**아래에서 **인쇄**, **복사 및 콘텐츠 추출**및 **앞으로** 확인란의 선택을 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-300">Under **Choose permissions from the preset**, clear the **Print**, **Copy and extract content**, and **Forward** check boxes.</span></span>
    
17. <span data-ttu-id="c2f51-301">두 번 **확인** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-301">Click **OK** twice.</span></span>
    
18. <span data-ttu-id="c2f51-302">**하위 레이블** 블레이드에서 **저장**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-302">On the **Sub-label** blade, click **Save**.</span></span>
    
19. <span data-ttu-id="c2f51-303">새 범위가 지정 된 정책 블레이드를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-303">Close the new scoped policy blade.</span></span>
    
20. <span data-ttu-id="c2f51-304">**Azure 정보 보호-범위가 지정 된 정책** 블레이드에서 **게시**클릭 한 다음 **예**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-304">On the **Azure Information protection - Scoped policies** blade, click **Publish**, and then click **Yes**.</span></span>
    
<span data-ttu-id="c2f51-305">이제 이러한 4 개 사이트에서 문서를 만드는 작업을 시작 하 고 평가판 구독에서 다양 한 사용자 계정과 함께 자신에 게 액세스를 테스트할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-305">You are now ready to begin creating documents in these four sites and test access to them with various user accounts in your trial subscription.</span></span> 
  
<span data-ttu-id="c2f51-306">Azure 정보 보호 하 고이 새 레이블을 사용 하 여 문서를 보호 하려면 테스트 컴퓨터에서 [Azure 정보 보호 클라이언트 설치](https://docs.microsoft.com/information-protection/rms-client/install-client-app) 를 수행 해야, Office 365 포털에서 Office를 설치 하 고에 **계정을 사용 하 여 Microsoft Word에서 로그인 선임 및 전략적 직원** 평가판 구독의 그룹입니다.</span><span class="sxs-lookup"><span data-stu-id="c2f51-306">To protect a document with Azure Information Protection and this new label, you must [install the Azure Information Protection client](https://docs.microsoft.com/information-protection/rms-client/install-client-app) on a test machine, install Office from the Office 365 portal, and then sign in from Microsoft Word with an account in the **Senior and strategic staff** group of your trial subscription.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c2f51-307">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c2f51-307">See Also</span></span>

[<span data-ttu-id="c2f51-308">정치적 캠페인, 비영리, 및 기타 민첩 한 조직에 대 한 Microsoft 보안 지침</span><span class="sxs-lookup"><span data-stu-id="c2f51-308">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="c2f51-309">정치적 캠페인 개발/테스트 환경에 대 한 사용자 및 그룹 구성</span><span class="sxs-lookup"><span data-stu-id="c2f51-309">Configure groups and users for a political campaign dev/test environment</span></span>](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md)
  
[<span data-ttu-id="c2f51-310">클라우드 도입 TLG(테스트 랩 가이드)</span><span class="sxs-lookup"><span data-stu-id="c2f51-310">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="c2f51-311">클라우드 채택 및 하이브리드 솔루션</span><span class="sxs-lookup"><span data-stu-id="c2f51-311">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




