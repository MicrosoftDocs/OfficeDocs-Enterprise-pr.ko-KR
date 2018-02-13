---
title: "Office 365 및 Dynamics 365 개발/테스트 환경"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365, Strat_O365_Enterprise
ms.custom: Strat_O365_Enterprise, Ent_TLGs
ms.assetid: 098c1a1d-83a1-40eb-bbc9-47de7af8bb23
description: "요약:이 테스트 랩 가이드를 사용 하 여 Dynamics 365 Office 365 개발/테스트 환경에 추가 합니다."
ms.openlocfilehash: f13cf81f989867e543439e1ccb6ecd7f8ba55cb6
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/13/2018
---
# <a name="office-365-and-dynamics-365-devtest-environment"></a><span data-ttu-id="06da7-103">Office 365 및 Dynamics 365 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="06da7-103">Office 365 and Dynamics 365 dev/test environment</span></span>

 <span data-ttu-id="06da7-104">**요약:** 이 테스트 랩 가이드를 사용 하 여 Office 365 개발/테스트 환경에 Dynamics 365 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="06da7-104">**Summary:** Use this Test Lab Guide to add Dynamics 365 to your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="06da7-105">이 문서의 지침을 사용 하면 추가 Dynamics 365 평가판 구독 Office 365 개발/테스트 환경와 같은 조직에는 Office 365 및 Dynamics 365 개발/테스트 환경 만들기 (영문).</span><span class="sxs-lookup"><span data-stu-id="06da7-105">With the instructions in this article, you add a Dynamics 365 trial subscription to the same organization as your Office 365 dev/test environment, creating an Office 365 and Dynamics 365 dev/test environment.</span></span>
  
<span data-ttu-id="06da7-p101">Dynamics 365 기능 및 특징을 설명 하기 위해 Dynamics 365 평가판 구독을 사용할 수 있습니다. 다음과 같은 솔루션을 Dynamics 365 계획 1, Enterprise Edition 평가판 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="06da7-p101">You can use a Dynamics 365 trial subscription to demonstrate features and capabilities of Dynamics 365. The following solutions are included with a Dynamics 365 Plan 1, Enterprise Edition trial:</span></span>
  
- <span data-ttu-id="06da7-p102">[Microsoft Dynamics 365 Sales에 대 한](https://www.microsoft.com/dynamics365/sales)합니다. 자동화 및 판매원 집중할 수 및 현명 작동을 내리도록 지원 되는 디지털 인텔리전스 영업을 늘립니다.</span><span class="sxs-lookup"><span data-stu-id="06da7-p102">[Microsoft Dynamics 365 for Sales](https://www.microsoft.com/dynamics365/sales). Increase your sales with automation and digital intelligence helping your salespeople stay focused and work smarter.</span></span>
    
- <span data-ttu-id="06da7-p103">[Microsoft Dynamics 365 고객 서비스에 대 한](https://www.microsoft.com/dynamics365/customer-service)합니다. 전체 정보 및 디지털 인텔리전스 원활 하 게 서비스를 제공 하는데 필요한 사용자 에이전트에 게 제공 하 여 충성도 획득 합니다.</span><span class="sxs-lookup"><span data-stu-id="06da7-p103">[Microsoft Dynamics 365 for Customer Service](https://www.microsoft.com/dynamics365/customer-service). Earn loyalty by giving your agents the complete information and digital intelligence they need to provide seamless service.</span></span>
    
- <span data-ttu-id="06da7-p104">[Microsoft Dynamics 365 필드 서비스에 대 한](https://www.microsoft.com/dynamics365/field-service)합니다. 하면 일정을 최적화 하 고, 직원, 착용 하기, 수익을 높일 수 예측 도구를 사용 하 여 마스터 서비스를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="06da7-p104">[Microsoft Dynamics 365 for Field Service](https://www.microsoft.com/dynamics365/field-service). Master the service call by optimizing your schedules, equipping your workforce, and using predictive tools to increase profit.</span></span>
    
- <span data-ttu-id="06da7-p105">[Microsoft Dynamics 365 프로젝트 서비스 자동화에 대 한](https://www.microsoft.com/en-us/dynamics365/project-service-automation)합니다. 프로젝트를 성공적으로 완료 하 고 생산성을 직원 및 지능형 도구와 많은 이익을 관계를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="06da7-p105">[Microsoft Dynamics 365 for Project Service Automation](https://www.microsoft.com/en-us/dynamics365/project-service-automation). Complete your projects successfully and create profitable relationships with productive employees and intelligent tools.</span></span>
    
<span data-ttu-id="06da7-116">Dynamics 365 평가판 구독에 대 한 위의 중 하나 이상을 탐색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06da7-116">You can explore one or more of the above for your Dynamics 365 trial subscription.</span></span>
  
![Microsoft 클라우드의 테스트 랩 가이드](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> <span data-ttu-id="06da7-118">클릭 [여기](http://aka.ms/catlgstack) 에 한 맵이 하나의 Microsoft 클라우드 테스트 랩 가이드 스택의 모든 문서를 시각적으로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="06da7-118">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="06da7-119">1단계: 경량 또는 시뮬레이트된 엔터프라이즈 Office 365 개발/테스트 환경을 구축합니다.</span><span class="sxs-lookup"><span data-stu-id="06da7-119">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="06da7-120">최소 요구 사항을 경량 방식으로 Office 365 및 Dynamics 365 테스트 하려면 2와 [Office 365 개발/테스트 환경](office-365-dev-test-environment.md)의 3 단계에서 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="06da7-120">If you just want to test Office 365 and Dynamics 365 in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="06da7-121">Office 365 및 Dynamics 365 시뮬레이션 된 enterprise에 대 한 테스트 하려는 경우 [Office 365 개발/테스트 환경에 대 한 디렉터리 동기화](dirsync-for-your-office-365-dev-test-environment.md)의 지시를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="06da7-121">If you want to test Office 365 and Dynamics 365 for a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="06da7-p106">이 문서의 구성 인터넷에 연결 하는 시뮬레이션 된 인트라넷을 포함 하는 시뮬레이션 된 엔터프라이즈 개발/테스트 환경에 원하지 않는 및 Windows Server AD 포리스트에 대 한 디렉터리 동기화 합니다. 제공은 일반적인 조직을 대표 하는 환경에서 Office 365와 Dynamics 365 테스트할 수 있도록 하는 옵션으로 여기 합니다.</span><span class="sxs-lookup"><span data-stu-id="06da7-p106">The configuration in this article does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can experiment with Office 365 and Dynamics 365 in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-add-a-dynamics-365-trial-subscription"></a><span data-ttu-id="06da7-124">2 단계: Dynamics 365 평가판 구독 추가</span><span class="sxs-lookup"><span data-stu-id="06da7-124">Phase 2: Add a Dynamics 365 trial subscription</span></span>

<span data-ttu-id="06da7-125">이 단계에서 Dynamics 365 평가판 구독에 대 한 등록 하 여 Office 365 평가판 구독와 같은 조직에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="06da7-125">In this phase, you sign up for the Dynamics 365 trial subscription and add it to the same organization as your Office 365 trial subscription.</span></span>
  
### <a name="sign-up-for-a-dynamics-365-trial-subscription"></a><span data-ttu-id="06da7-126">Dynamics 365 평가판 구독에 등록</span><span class="sxs-lookup"><span data-stu-id="06da7-126">Sign up for a Dynamics 365 trial subscription</span></span>

1. <span data-ttu-id="06da7-127">브라우저를 사용 하는 중 하나에서 데스크톱 컴퓨터 (lightweight) 나 CLIENT1 (enterprise 시뮬레이션)에 [https://portal.office.com](https://portal.office.com) 전역 관리자 계정의 자격 증명을 사용 하 여 Office 365 포털에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="06da7-127">Using a browser on either your desktop computer (lightweight) or from CLIENT1 (simulated enterprise), sign in to the Office 365 portal at [https://portal.office.com](https://portal.office.com) with the credentials of your global administrator account.</span></span>
    
2. <span data-ttu-id="06da7-128">**Admin** 타일을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="06da7-128">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="06da7-129">왼쪽 탐색 영역에서 **Office 관리 센터** 탭을 클릭 **대금 청구 > 구매 서비스**합니다.</span><span class="sxs-lookup"><span data-stu-id="06da7-129">On the **Office admin center** tab, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="06da7-p107">**서비스 구매** 페이지 **Dynamics 365 계획 1 Enterprise Edition** 항목을 찾습니다. 마우스 포인터를 올려 하 고 **무료 평가판을 시작**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="06da7-p107">On the **Purchase services** page, find the **Dynamics 365 Plan 1 Enterprise Edition** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="06da7-132">**주문 확인** 페이지에서 **지금 시도**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="06da7-132">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="06da7-133">**순서 확인** 페이지에서 **계속**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="06da7-133">On the **Order receipt** page, click **Continue**.</span></span>
    
> [!NOTE]
> <span data-ttu-id="06da7-p108">Dynamics 365 계획 1 Enterprise Edition 평가판 구독은 30 일입니다. 다른 30 일에 대 한 내역 구독을 쉽게 확장할 수 있습니다. 영구 개발/테스트 환경에 대 한 만들기 새 적은 수의 라이선스를 사용 하 여 구독을 지불 합니다.</span><span class="sxs-lookup"><span data-stu-id="06da7-p108">The Dynamics 365 Plan 1 Enterprise Edition trial subscription is 30 days. You can easily extend the trail subscription for another 30 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
## <a name="phase-3-assign-dynamics-365-licenses-and-system-administrators"></a><span data-ttu-id="06da7-137">3 단계: Dynamics 365 라이선스 및 시스템 관리자를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="06da7-137">Phase 3: Assign Dynamics 365 licenses and system administrators</span></span>

<span data-ttu-id="06da7-138">이 단계에서 전역 관리자, 사용자 2 및 3 사용자 계정에 Dynamics 365 라이선스를 할당 하 고 시스템 관리자가 하 게 합니다.</span><span class="sxs-lookup"><span data-stu-id="06da7-138">In this phase, you assign Dynamics 365 licenses to the global administrator, User 2, and User 3 accounts and make them system administrators.</span></span>
  
<span data-ttu-id="06da7-139">Dynamics 365 라이선스를 할당 하려면 다음이 단계를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="06da7-139">Use these steps to assign Dynamics 365 licenses.</span></span>
  
1. <span data-ttu-id="06da7-140">**Office 관리 센터** 탭을 클릭 **사용자 > 활성 사용자**합니다.</span><span class="sxs-lookup"><span data-stu-id="06da7-140">On the **Office admin center** tab, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="06da7-141">활성 사용자 목록에서 전역 관리자 계정을 클릭 하 고 **제품 라이선스**에 대 한 **편집** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="06da7-141">In the list of active users, click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="06da7-142">**제품 라이선스** 창에서 **전환** **Dynamics 365 계획 1 Enterprise Edition** 대 한 제품 라이선스 설정, **저장** 을 클릭 하 고 두번 **닫기** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="06da7-142">On the **Product licenses** pane, turn the product license for **Dynamics 365 Plan 1 Enterprise Edition** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="06da7-143">사용자 2 및 3 사용자 계정에 대해 2-3 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="06da7-143">Perform steps 2 and 3 for the User 2 and User 3 accounts.</span></span>
    
5. <span data-ttu-id="06da7-144">**Office 관리 센터** 탭을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="06da7-144">Close the **Office admin center** tab.</span></span>
    
<span data-ttu-id="06da7-145">Dynamics 365 시스템 관리자는 사용자 2 및 3 사용자 계정을 구성 하려면 다음이 단계를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="06da7-145">Use these steps to configure the User 2 and User 3 accounts as Dynamics 365 system administrators.</span></span>
  
1. <span data-ttu-id="06da7-146">**Microsoft Office 홈** 탭에서 **관리**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="06da7-146">From the **Microsoft Office Home** tab, click **Admin**.</span></span>
    
2. <span data-ttu-id="06da7-147">**Office 관리 센터** 탭의 왼쪽된 탐색 영역에서 **관리 센터**를 클릭 하 고 **Dynamics 365**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="06da7-147">On the **Office Admin center** tab, in the left navigation, click **Admin centers**, and then click **Dynamics 365**.</span></span>
    
    <span data-ttu-id="06da7-148">Dynamics 365 Dynamics 365 메뉴에 표시 되기 전에 프로 비전을 완료할 때까지 대기 해야할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06da7-148">You may need to wait for Dynamics 365 to finish provisioning before Dynamics 365 appears in the menu.</span></span>
    
3. <span data-ttu-id="06da7-149">Dynamics 365 탭에서 **대부분의**를 클릭 하 고 다음을 클릭 **설치를 완료 합니다.**</span><span class="sxs-lookup"><span data-stu-id="06da7-149">On the Dynamics 365 tab, click **All of these**, and then click **Complete Setup.**</span></span>
    
    <span data-ttu-id="06da7-150">설치가 완료 될 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="06da7-150">Wait for setup to complete.</span></span>
    
    <span data-ttu-id="06da7-p109">설치가 완료 되 면 내역 구독의 일부인 샘플 데이터를 기반으로 영업 활동 대시보드를 표시 합니다. **평가판 시작** 보려면 잠시 비디오를 수행 합니다. 완료 되 면 비디오 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="06da7-p109">When setup completes, it displays a Sales Activity Dashboard based on sample data that is part of the trail subscription. Take a few moments to view the **Welcome to your trial** video. Close the video window when complete.</span></span>
    
4. <span data-ttu-id="06da7-154">위쪽 도구 모음에서 **Sales**옆에 있는 아래쪽 화살표를 클릭 하 고 **설정**, **보안**을 클릭 한 다음 합니다.</span><span class="sxs-lookup"><span data-stu-id="06da7-154">On the toolbar at the top, click the down arrow next to **Sales**, click **Settings**, and then click **Security**.</span></span>
    
5. <span data-ttu-id="06da7-155">**보안** 페이지에서 **사용자**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="06da7-155">On the **Security** page, click **Users**.</span></span>
    
6. <span data-ttu-id="06da7-156">사용자의 목록에서 **사용자 2**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="06da7-156">In the list of users, click **User 2**.</span></span>
    
7. <span data-ttu-id="06da7-157">도구 모음에서 **관리 역할**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="06da7-157">In the tool bar, click **Manage Roles**.</span></span>
    
8. <span data-ttu-id="06da7-158">**역할 관리** **시스템 관리자**클릭 한 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="06da7-158">In **Manage Roles**, click **System Administrator**, and then click **OK**.</span></span>
    
9. <span data-ttu-id="06da7-159">맨 위쪽에 있는 도구 모음에서 **보안**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="06da7-159">In the tool bar at the top click **Security**.</span></span>
    
10. <span data-ttu-id="06da7-160">3 사용자 계정에 대해 5-8 단계를 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="06da7-160">Repeat steps 5-8 for the User 3 account.</span></span>
    
11. <span data-ttu-id="06da7-161">닫기는 **사용자: User3** 탭 합니다.</span><span class="sxs-lookup"><span data-stu-id="06da7-161">Close the **User: User3** tab.</span></span>
    
> [!NOTE]
> <span data-ttu-id="06da7-162">Office 365 전역 관리자 계정 Dynamics 365 시스템 관리자 역할을 자동으로 할당 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="06da7-162">Your Office 365 global administrator account was automatically assigned the Dynamics 365 system administrator role.</span></span> 
  
<span data-ttu-id="06da7-163">Office 365 및 Dynamics 365 개발/테스트 환경을 현재가지고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06da7-163">Your Office 365 and Dynamics 365 dev/test environment now has:</span></span>
  
- <span data-ttu-id="06da7-164">Office 365 e 5 엔터프라이즈 및 Dynamics 365 평가판 구독 사용자 계정의 대화 목록와 같은 조직 및 동일한 Azure AD 테 넌 트를 공유 합니다.</span><span class="sxs-lookup"><span data-stu-id="06da7-164">Office 365 E5 Enterprise and Dynamics 365 trial subscriptions sharing the same organization and the same Azure AD tenant with your list of user accounts.</span></span>
    
- <span data-ttu-id="06da7-165">사용자 글로벌 엔터프라이즈 관리자, 사용자 2 및 3 사용자 계정을 Office 365 e 5 엔터프라이즈 사용자와 Dynamics 365 모두 사용 하도록 설정 된 및 Dynamics 365 시스템 관리자가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06da7-165">Your global enterprise administrator, User 2, and User 3 accounts are enabled to use both Office 365 E5 Enterprise and Dynamics 365 and are Dynamics 365 system administrators.</span></span>
    
## <a name="next-step"></a><span data-ttu-id="06da7-166">다음 단계</span><span class="sxs-lookup"><span data-stu-id="06da7-166">Next step</span></span>

<span data-ttu-id="06da7-167">Office 365 및 Dynamics 365 작동 하는 방법을 [Office 365 및 Dynamics 365 개발/테스트 환경에 대 한 Exchange Online 통합](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md)된 Exchange Online 사서함을 설명 하 고 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="06da7-167">Configure and then demonstrate how Office 365 and Dynamics 365 work together in Exchange Online mailboxes with [Exchange Online integration for your Office 365 and Dynamics 365 dev/test environment](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="06da7-168">참고 항목</span><span class="sxs-lookup"><span data-stu-id="06da7-168">See Also</span></span>

[<span data-ttu-id="06da7-169">클라우드 도입 TLG(테스트 랩 가이드)</span><span class="sxs-lookup"><span data-stu-id="06da7-169">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="06da7-170">기본 구성 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="06da7-170">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="06da7-171">Office 365 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="06da7-171">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="06da7-172">Office 365 개발/테스트 환경용 DirSync</span><span class="sxs-lookup"><span data-stu-id="06da7-172">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)

[<span data-ttu-id="06da7-173">Dynamics 365용 구독 관리(온라인)</span><span class="sxs-lookup"><span data-stu-id="06da7-173">Subscription Management for Dynamics 365 (online)</span></span>](https://technet.microsoft.com/library/jj679903.aspx)
  
[<span data-ttu-id="06da7-174">Dynamics 365 관리</span><span class="sxs-lookup"><span data-stu-id="06da7-174">Administering Dynamics 365</span></span>](https://technet.microsoft.com/library/dn531101.aspx)


