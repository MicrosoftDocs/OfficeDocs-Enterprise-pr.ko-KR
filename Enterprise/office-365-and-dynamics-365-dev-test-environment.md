---
title: Office 365 및 Dynamics 365 개발/테스트 환경
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/18/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Ent_TLGs
ms.assetid: 098c1a1d-83a1-40eb-bbc9-47de7af8bb23
description: '요약: 이 테스트 랩 가이드를 사용하여 Office 365 개발/테스트 환경에 Dynamics 365를 추가합니다.'
ms.openlocfilehash: 9e4c98129c68ab5d2f0d9fc486ab62740c625af5
ms.sourcegitcommit: 4ef8e113fa20b539de1087422455fc26ff123d55
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/19/2019
ms.locfileid: "30574062"
---
# <a name="office-365-and-dynamics-365-devtest-environment"></a><span data-ttu-id="5718a-103">Office 365 및 Dynamics 365 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="5718a-103">Office 365 and Dynamics 365 dev/test environment</span></span>

 <span data-ttu-id="5718a-104">**요약:** 이 테스트 랩 가이드를 사용하여 Office 365 개발/테스트 환경에 Dynamics 365를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="5718a-104">**Summary:** Use this Test Lab Guide to add Dynamics 365 to your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="5718a-105">이 문서의 지침을 사용하여 Dynamics 365 평가판 구독을 Office 365 개발/테스트 환경과 동일한 조직에 추가하여 Office 365 및 Dynamics 365 개발/테스트 환경을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5718a-105">With the instructions in this article, you add a Dynamics 365 trial subscription to the same organization as your Office 365 dev/test environment, creating an Office 365 and Dynamics 365 dev/test environment.</span></span>

![Office 365 및 Dynamics 365 개발/테스트 환경](media/o365-dynamics365-dev-test.png)
  
  
<span data-ttu-id="5718a-p101">Dynamics 365 평가판 구독을 사용하여 Dynamics 365의 기능을 시연할 수 있습니다. 다음과 같은 해결 방법이 Dynamics 365 계획 1, Enterprise Edition 평가판에 함께 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="5718a-p101">You can use a Dynamics 365 trial subscription to demonstrate features and capabilities of Dynamics 365. The following solutions are included with a Dynamics 365 Plan 1, Enterprise Edition trial:</span></span>
  
- <span data-ttu-id="5718a-p102">[Microsoft Dynamics 365 for Sales](https://www.microsoft.com/dynamics365/sales). 자동화 및 디지털 인텔리전스를 통해 영업 사원이 집중력을 유지하고 더욱 똑똑하게 업무를 수행할 수 있도록 도와 판매량을 늘립니다.</span><span class="sxs-lookup"><span data-stu-id="5718a-p102">[Microsoft Dynamics 365 for Sales](https://www.microsoft.com/dynamics365/sales). Increase your sales with automation and digital intelligence helping your salespeople stay focused and work smarter.</span></span>
    
- <span data-ttu-id="5718a-p103">[Microsoft Dynamics 365 for Customer Service](https://www.microsoft.com/dynamics365/customer-service). 에이전트가 원활한 서비스를 제공하는 데 필요한 완벽한 정보와 디지털 인텔리전스를 제공하여 충성도를 얻습니다.</span><span class="sxs-lookup"><span data-stu-id="5718a-p103">[Microsoft Dynamics 365 for Customer Service](https://www.microsoft.com/dynamics365/customer-service). Earn loyalty by giving your agents the complete information and digital intelligence they need to provide seamless service.</span></span>
    
- <span data-ttu-id="5718a-p104">[Microsoft Dynamics 365 for Field Service](https://www.microsoft.com/dynamics365/field-service). 일정을 최적화하고 직원을 배치하며 예측 도구를 사용하여 이익을 늘려서 서비스 호출을 마스터합니다.</span><span class="sxs-lookup"><span data-stu-id="5718a-p104">[Microsoft Dynamics 365 for Field Service](https://www.microsoft.com/dynamics365/field-service). Master the service call by optimizing your schedules, equipping your workforce, and using predictive tools to increase profit.</span></span>
    
- <span data-ttu-id="5718a-p105">[Microsoft Dynamics 365 for Project Service Automation](https://www.microsoft.com/ko-KR/dynamics365/project-service-automation). 프로젝트를 성공적으로 완료하고 생산적인 직원rhk 지능형 도구를 통해 수익성 있는 관계를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5718a-p105">[Microsoft Dynamics 365 for Project Service Automation](https://www.microsoft.com/ko-KR/dynamics365/project-service-automation). Complete your projects successfully and create profitable relationships with productive employees and intelligent tools.</span></span>
    
<span data-ttu-id="5718a-117">Dynamics 365 평가판 구독에 대해 위 내용 중 하나 이상을 탐색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5718a-117">You can explore one or more of the above for your Dynamics 365 trial subscription.</span></span>
  
![Microsoft 클라우드의 테스트 랩 가이드](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> <span data-ttu-id="5718a-119">[여기](http://aka.ms/catlgstack)를 클릭하여 One Microsoft 클라우드 테스트 랩 가이드 스택의 모든 문서에 대한 가상 맵을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5718a-119">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="5718a-120">1단계: 경량 또는 시뮬레이트된 엔터프라이즈 Office 365 개발/테스트 환경을 구축합니다.</span><span class="sxs-lookup"><span data-stu-id="5718a-120">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="5718a-121">최소 요구 사항과 경량 방식으로 Office 365 및 Dynamics 365를 테스트하려면 [Office 365 개발/테스트 환경](office-365-dev-test-environment.md)의 2, 3단계의 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="5718a-121">If you just want to test Office 365 and Dynamics 365 in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="5718a-122">시뮬레이트된 엔터프라이즈에서 Office 365 및 Dynamics 365를 테스트하려면 [Office 365 개발/테스트 환경에 대한 디렉터리 동기화](dirsync-for-your-office-365-dev-test-environment.md) 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="5718a-122">If you want to test Office 365 and Dynamics 365 for a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>

![Office 365 개발/테스트 환경](media/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
> [!NOTE]
> <span data-ttu-id="5718a-p106">이 문서의 구성에는 시뮬레이트된 엔터프라이즈 개발/테스트 환경이 필요하지 않습니다. 해당 환경에는 Windows Server AD 포리스트의 디렉터리 동기화 및 인터넷에 연결된 시뮬레이트된 인트라넷이 포함되어 있습니다. 여기서는 옵션으로 제공되므로 일반적인 조직을 나타내는 환경에서 Office 365 및 Dynamics 365를 실험할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5718a-p106">The configuration in this article does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can experiment with Office 365 and Dynamics 365 in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-add-a-dynamics-365-trial-subscription"></a><span data-ttu-id="5718a-126">2단계: Dynamics 365 평가판 구독 추가</span><span class="sxs-lookup"><span data-stu-id="5718a-126">Phase 2: Add a Dynamics 365 trial subscription</span></span>

<span data-ttu-id="5718a-127">이 단계에서는 Dynamics 365 평가판 구독을 등록하고 Office 365 평가판 구독과 동일한 조직에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="5718a-127">In this phase, you sign up for the Dynamics 365 trial subscription and add it to the same organization as your Office 365 trial subscription.</span></span>
  
### <a name="sign-up-for-a-dynamics-365-trial-subscription"></a><span data-ttu-id="5718a-128">Dynamics 365 평가판 구독 등록</span><span class="sxs-lookup"><span data-stu-id="5718a-128">Sign up for a Dynamics 365 trial subscription</span></span>

1. <span data-ttu-id="5718a-129">데스크톱 컴퓨터(경량) 또는 CLIENT1(시뮬레이트된 엔터프라이즈)의 브라우저에서 전역 관리자 계정의 자격 증명을 사용하여 [https://admin.microsoft.com](https://admin.microsoft.com)의 Microsoft 365 관리 센터에 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="5718a-129">Using a browser on either your desktop computer (lightweight) or from CLIENT1 (simulated enterprise), sign in to the Office 365 portal at [https://admin.microsoft.com](https://admin.microsoft.com) with the credentials of your global administrator account.</span></span>
    
2. <span data-ttu-id="5718a-130">**관리** 타일을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5718a-130">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="5718a-131">**Microsoft 365 관리 센터** 탭에 있는 왼쪽 탐색 영역에서 **대금 청구 > 서비스 구매**를 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5718a-131">On the **Microsoft 365 admin center** tab, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="5718a-p107">**구매 서비스** 페이지에서 **Dynamics 365 Plan 1 Enterprise Edition** 항목을 찾습니다. 마우스 포인터를 가져간 후 **평가판 시작**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5718a-p107">On the **Purchase services** page, find the **Dynamics 365 Plan 1 Enterprise Edition** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="5718a-134">**주문 확인** 페이지에서 **지금 평가판 사용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5718a-134">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="5718a-135">**주문 접수** 페이지에서 **계속**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5718a-135">On the **Order receipt** page, click **Continue**.</span></span>

![Office 365 및 Dynamics 365 개발/테스트 환경](media/o365-dynamics365-dev-test.png)
    
> [!NOTE]
> <span data-ttu-id="5718a-p108">Dynamics 365 Plan 1 Enterprise Edition 평가 기간은 30일입니다. 추가로 30일 동안 내역 구독을 연장할 수 있습니다. 영구 개발/테스트 환경의 경우 소수의 라이선스를 사용해서 유료 구독을 새로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5718a-p108">The Dynamics 365 Plan 1 Enterprise Edition trial subscription is 30 days. You can easily extend the trail subscription for another 30 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
## <a name="phase-3-assign-dynamics-365-licenses-and-system-administrators"></a><span data-ttu-id="5718a-140">3단계: Dynamics 365 라이선스 및 시스템 관리자 할당</span><span class="sxs-lookup"><span data-stu-id="5718a-140">Phase 3: Assign Dynamics 365 licenses and system administrators</span></span>

<span data-ttu-id="5718a-141">이 단계에서는 전역 관리자, 사용자 2 및 사용자 3 계정에 Dynamics 365 라이선스를 할당하고 시스템 관리자로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5718a-141">In this phase, you assign Dynamics 365 licenses to the global administrator, User 2, and User 3 accounts and make them system administrators.</span></span>
  
<span data-ttu-id="5718a-142">다음 단계를 사용하여 Dynamics 365 라이선스를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="5718a-142">Use these steps to assign Dynamics 365 licenses.</span></span>
  
1. <span data-ttu-id="5718a-143">**Microsoft 365 관리 센터** 탭에서 **사용자 > 활성 사용자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5718a-143">On the **Microsoft 365 admin center** tab, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="5718a-144">활성 사용자 목록에서 전역 관리자 계정을 클릭한 다음, **제품 라이선스**에 대해 **편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5718a-144">In the list of active users, click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="5718a-145">**제품 라이선스** 창에서 **Dynamics 365 Plan 1 Enterprise Edition**에 대한 제품 라이선스를 **설정**으로 바꾸고 **저장**을 클릭한 후 **닫기**를 차례로 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5718a-145">On the **Product licenses** pane, turn the product license for **Dynamics 365 Plan 1 Enterprise Edition** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="5718a-146">사용자 2 및 사용자 3 계정에 대해 2, 3단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="5718a-146">Perform steps 2 and 3 for the User 2 and User 3 accounts.</span></span>
    
5. <span data-ttu-id="5718a-147">**Microsoft 365 관리 센터** 탭을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="5718a-147">Close the **Microsoft 365 admin center** tab.</span></span>
    
<span data-ttu-id="5718a-148">다음 단계를 사용하여 사용자 2 및 사용자 3 계정을 Dynamics 365 시스템 관리자로 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="5718a-148">Use these steps to configure the User 2 and User 3 accounts as Dynamics 365 system administrators.</span></span>
  
1. <span data-ttu-id="5718a-149">**Microsoft Office 홈** 탭에서 **관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5718a-149">From the **Microsoft Office Home** tab, click **Admin**.</span></span>
    
2. <span data-ttu-id="5718a-150">**Office 관리 센터** 탭에 있는 왼쪽 탐색 영역에서 **관리 센터**를 클릭하고 **Dynamics 365**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5718a-150">On the **Office Admin center** tab, in the left navigation, click **Admin centers**, and then click **Dynamics 365**.</span></span>
    
    <span data-ttu-id="5718a-151">메뉴에 Dynamics 365가 표시되기 전에 Dynamics 365에서 프로비전이 완료될 때까지 기다려야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5718a-151">You may need to wait for Dynamics 365 to finish provisioning before Dynamics 365 appears in the menu.</span></span>
    
3. <span data-ttu-id="5718a-152">Dynamics 365 탭에서 **이러한 항목 모두**를 클릭한 후 **설치 완료**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5718a-152">On the Dynamics 365 tab, click **All of these**, and then click **Complete Setup.**</span></span>
    
    <span data-ttu-id="5718a-153">설치가 완료될 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="5718a-153">Wait for setup to complete.</span></span>
    
    <span data-ttu-id="5718a-p109">설치가 완료되면 내역 구독에 포함된 샘플 데이터를 기준으로 하는 판매 활동 대시보드가 표시됩니다. 몇 분 정도 할애하여 **평가판 시작** 비디오를 시청하세요. 완료되면 비디오 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="5718a-p109">When setup completes, it displays a Sales Activity Dashboard based on sample data that is part of the trail subscription. Take a few moments to view the **Welcome to your trial** video. Close the video window when complete.</span></span>
    
4. <span data-ttu-id="5718a-157">맨 위에 있는 도구 모음에서 **판매** 옆에 있는 아래쪽 화살표를 클릭하고 **설정**을 클릭한 후 **보안**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5718a-157">On the toolbar at the top, click the down arrow next to **Sales**, click **Settings**, and then click **Security**.</span></span>
    
5. <span data-ttu-id="5718a-158">**보안** 페이지에서 **사용자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5718a-158">On the **Security** page, click **Users**.</span></span>
    
6. <span data-ttu-id="5718a-159">사용자 목록에서 **사용자 2**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5718a-159">In the list of users, click **User 2**.</span></span>
    
7. <span data-ttu-id="5718a-160">도구 모음에서 **역할 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5718a-160">In the tool bar, click **Manage Roles**.</span></span>
    
8. <span data-ttu-id="5718a-161">**역할 관리**에서 **시스템 관리자**를 클릭하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5718a-161">In **Manage Roles**, click **System Administrator**, and then click **OK**.</span></span>
    
9. <span data-ttu-id="5718a-162">맨 위의 도구 모음에서 **보안**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5718a-162">In the tool bar at the top click **Security**.</span></span>
    
10. <span data-ttu-id="5718a-163">사용자 3 계정에 대해 5-8단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="5718a-163">Repeat steps 5-8 for the User 3 account.</span></span>
    
11. <span data-ttu-id="5718a-164">**사용자: 사용자3** 탭을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="5718a-164">Close the **User: User3** tab.</span></span>
    
> [!NOTE]
> <span data-ttu-id="5718a-165">Office 365 전역 관리자 계정에 Dynamics 365 시스템 관리자 역할이 자동으로 할당되었습니다.</span><span class="sxs-lookup"><span data-stu-id="5718a-165">Your Office 365 global administrator account was automatically assigned the Dynamics 365 system administrator role.</span></span> 
  
<span data-ttu-id="5718a-166">Office 365 및 Dynamics 365 개발/테스트 환경에는 다음이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="5718a-166">Your Office 365 and Dynamics 365 dev/test environment now has:</span></span>
  
- <span data-ttu-id="5718a-167">사용자 계정 목록과 동일한 조직 및 동일한 Microsoft Azure AD 테넌트를 공유하는 Office 365 E5 Enterprise 및 Dynamics 365 평가판 구독</span><span class="sxs-lookup"><span data-stu-id="5718a-167">Office 365 E5 Enterprise and Dynamics 365 trial subscriptions sharing the same organization and the same Azure AD tenant with your list of user accounts.</span></span>
    
- <span data-ttu-id="5718a-168">전역 엔터프라이즈 관리자, 사용자 2 및 사용자 3 계정이 Office 365 E5 Enterprise 및 Dynamics 365를 함께 사용하도록 설정되며, Dynamics 365 시스템 관리자가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5718a-168">Your global enterprise administrator, User 2, and User 3 accounts are enabled to use both Office 365 E5 Enterprise and Dynamics 365 and are Dynamics 365 system administrators.</span></span>
    
## <a name="next-step"></a><span data-ttu-id="5718a-169">다음 단계</span><span class="sxs-lookup"><span data-stu-id="5718a-169">Next step</span></span>

<span data-ttu-id="5718a-170">[Office 365 및 Dynamics 365 개발/테스트 환경을 위한 Exchange Online 통합](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md)을 사용하여 Exchange Online 사서함에서 Office 365 및 Dynamics 365가 함께 작동하는 방법을 구성한 다음 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="5718a-170">Configure and then demonstrate how Office 365 and Dynamics 365 work together in Exchange Online mailboxes with [Exchange Online integration for your Office 365 and Dynamics 365 dev/test environment](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="5718a-171">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5718a-171">See Also</span></span>

[<span data-ttu-id="5718a-172">클라우드 도입 TLG(테스트 랩 가이드)</span><span class="sxs-lookup"><span data-stu-id="5718a-172">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="5718a-173">기본 구성 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="5718a-173">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="5718a-174">Office 365 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="5718a-174">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="5718a-175">Office 365 개발/테스트 환경용 DirSync</span><span class="sxs-lookup"><span data-stu-id="5718a-175">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)

[<span data-ttu-id="5718a-176">Dynamics 365용 구독 관리(온라인)</span><span class="sxs-lookup"><span data-stu-id="5718a-176">Subscription Management for Dynamics 365 (online)</span></span>](https://technet.microsoft.com/library/jj679903.aspx)
  
[<span data-ttu-id="5718a-177">Dynamics 365 관리</span><span class="sxs-lookup"><span data-stu-id="5718a-177">Administering Dynamics 365</span></span>](https://technet.microsoft.com/library/dn531101.aspx)


