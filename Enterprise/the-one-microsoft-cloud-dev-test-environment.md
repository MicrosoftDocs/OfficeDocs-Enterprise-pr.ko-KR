---
title: One Microsoft Cloud 개발/테스트 환경
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: a1370fe4-2fd6-4fea-ad1d-3555433d6d2e
description: '요약: 이 테스트 랩 가이드를 사용하여 모든 Microsoft의 클라우드 서비스가 포함된 개발/테스트 환경을 만듭니다.'
ms.openlocfilehash: 29fcb1108ceac6aa488ca71d723789a7a2e6c409
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/27/2018
---
# <a name="the-one-microsoft-cloud-devtest-environment"></a><span data-ttu-id="0a6e6-103">One Microsoft Cloud 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="0a6e6-103">The One Microsoft Cloud dev/test environment</span></span>

 <span data-ttu-id="0a6e6-104">**요약:** 이 테스트 랩 가이드를 사용하여 모든 Microsoft의 클라우드 서비스가 포함된 개발/테스트 환경을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0a6e6-104">**Summary:** Use this Test Lab Guide to create a dev/test environment that includes all of Microsoft's cloud offerings.</span></span>
  
<span data-ttu-id="0a6e6-p101">이 문서의 지침에 따라 Microsoft Azure 인프라 서비스에서 시뮬레이트된 인트라넷을 만든 후 Microsoft Office 365, Microsoft Enterprise Mobility + Security 및 Microsoft Dynamics 365 구독을 추가합니다. 그 결과 단일 개발/테스트 환경에서 모든 Microsoft 클라우드 서비스를 동시에 사용하는 간소화된 조직이 구현됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a6e6-p101">With the instructions in this article, you create a simulated intranet in Microsoft Azure infrastructure services and then add Microsoft Office 365, Microsoft Enterprise Mobility + Security (EMS), and Microsoft Dynamics 365 subscriptions. The result is a simplified organization that uses all Microsoft's cloud offerings at the same time in a single dev/test environment.</span></span> 
  
![Azure, Office 365, EMS 및 Dynamics 365를 사용하는 One Microsoft 클라우드 개발/테스트 환경 3단계](images/31714fcc-0c7d-411f-bcd1-c62d9be090ee.png)
  
<span data-ttu-id="0a6e6-108">구성 결과를 사용하여 다음을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a6e6-108">You can use the resulting configuration to:</span></span>
  
- <span data-ttu-id="0a6e6-109">Azure AD(Azure Active Directory)에서 제공하는 공통 ID 인프라와 같은 통합을 Microsoft 클라우드 서비스에서 경험할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a6e6-109">Experience the integration across Microsoft's cloud offerings, such as the common identity infrastructure provided by Azure Active Directory (AD).</span></span>
    
- <span data-ttu-id="0a6e6-110">여러 Microsoft 클라우드 서비스를 포함하는 종단 간 시나리오를 평가합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6e6-110">Evaluate end-to-end scenarios that include multiple Microsoft Cloud offerings.</span></span>
    
- <span data-ttu-id="0a6e6-111">여러 Microsoft 클라우드 서비스를 사용하는 데모, 개념 증명 또는 개발/테스트 구성을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0a6e6-111">Create a demo, proof-of-concept, or dev/test configuration that uses multiple Microsoft Cloud offerings.</span></span>
    
- <span data-ttu-id="0a6e6-112">전문성 개발을 위한 Microsoft 클라우드 기술을 구축합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6e6-112">Build your Microsoft Cloud skills for professional development.</span></span>
    
## <a name="phase-1-create-a-simulated-intranet-and-add-office-365"></a><span data-ttu-id="0a6e6-113">1단계: 시뮬레이트된 인트라넷 만들기 및 Office 365 추가</span><span class="sxs-lookup"><span data-stu-id="0a6e6-113">Phase 1: Create a simulated intranet and add Office 365</span></span>

<span data-ttu-id="0a6e6-114">[Office 365 개발/테스트 환경용 DirSync](dirsync-for-your-office-365-dev-test-environment.md)의 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="0a6e6-114">Follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="0a6e6-115">그림 1은 Office 365와 온-프레미스 Windows Server AD(Active Directory) 포리스트의 Azure 인프라 서비스 및 디렉터리 동기화에서 실행되는 시뮬레이트된 인트라넷을 포함하는 구성 결과를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="0a6e6-115">Figure 1 shows your resulting configuration, which includes Office 365 and a simulated intranet running in Azure infrastructure services and directory synchronization from an on-premises Windows Server Active Directory (AD) forest.</span></span>
  
<span data-ttu-id="0a6e6-116">**그림 1: Office 365를 사용한 Azure의 시뮬레이트된 인트라넷**</span><span class="sxs-lookup"><span data-stu-id="0a6e6-116">**Figure 1: The simulated intranet in Azure with Office 365**</span></span>

![DirSync를 사용하는 Office 365 개발/테스트 환경](images/be5b37b0-f832-4878-b153-436c31546e21.png)
  
> [!NOTE]
> <span data-ttu-id="0a6e6-p102">Azure 평가 기간은 30일입니다. Office 365 Enterprise E5 평가 구독 기간은 30일로, 추가로 30일 동안 연장될 수 있습니다. 영구 개발/테스트 환경의 경우 적은 수의 라이선스를 사용하여 새 유료 Azure 구독과 새 유료 Office 365 Enterprise E5 구독을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0a6e6-p102">The Azure trial is 30 days. The Office 365 Enterprise E5 Trial subscription is 30 days, which can be easily extended for another 30 days. For a permanent dev/test environment, create a new paid Azure subscription and a new paid Office 365 Enterprise E5 subscription with a small number of licenses.</span></span> 
  
## <a name="phase-2-add-ems"></a><span data-ttu-id="0a6e6-121">2단계: EMS 추가</span><span class="sxs-lookup"><span data-stu-id="0a6e6-121">Phase 2: Add EMS</span></span>

<span data-ttu-id="0a6e6-122">이 단계에서는 EMS 평가판 구독을 등록하고 Office 365 평가판 구독과 동일한 조직에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6e6-122">In this phase, you sign up for the EMS trial subscription and add it to the same organization as your Office 365 trial subscription.</span></span>
  
1. <span data-ttu-id="0a6e6-123">데스크톱 컴퓨터 또는 CLIENT1의 브라우저에서 전역 관리자 계정의 자격 증명을 사용하여 [https://portal.office.comhttps://portal.office.com](https://portal.office.com)의 Office 365 포털에 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6e6-123">With a browser on either your desktop computer (lightweight) or from CLIENT1 (simulated enterprise), sign in to the Office 365 portal at  https://portal.office.com https://portal.office.com  with the credentials of your global administrator account.</span></span>
    
2. <span data-ttu-id="0a6e6-124">**관리** 타일을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6e6-124">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="0a6e6-125">브라우저의 **Office 관리 센터** 탭에 있는 왼쪽 탐색 영역에서 **대금 청구 > 서비스 구매**를 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6e6-125">On the **Office Admin center** tab in your browser, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="0a6e6-p103">
            **구매 서비스** 페이지에서 **Enterprise Mobility + Security E5** 항목을 찾습니다. 마우스 포인터를 가져간 후 **평가판 시작**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6e6-p103">On the **Purchase services** page, find the **Enterprise Mobility + Security E5** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="0a6e6-128">**주문 확인** 페이지에서 **지금 평가판 사용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6e6-128">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="0a6e6-129">**주문 접수** 페이지에서 **계속**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6e6-129">On the **Order receipt** page, click **Continue**.</span></span>
    
> [!NOTE]
> <span data-ttu-id="0a6e6-p104">Enterprise Mobility + Security E5 평가판 구독 기간은 90일입니다. 영구 개발/테스트 환경의 경우 소수의 라이선스를 사용해서 유료 구독을 새로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0a6e6-p104">The Enterprise Mobility + Security E5 trial subscription is 90 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
<span data-ttu-id="0a6e6-132">그런 다음, 모든 사용자 계정에 대해 Enterprise Mobility + Security E5 라이선스를 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6e6-132">Next, enable the Enterprise Mobility + Security E5 license for your global administrator account.</span></span>
  
1. <span data-ttu-id="0a6e6-133">브라우저의 **Office 365 관리 센터** 탭에 있는 왼쪽 탐색 영역에서 **사용자 > 활성 사용자**를 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6e6-133">On the **Office 365 Admin center** tab in your browser, in the left navigation, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="0a6e6-134">전역 관리자 계정을 클릭한 다음, **제품 라이선스**에 대해 **편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6e6-134">Click your global administrator account, and then click Edit for Product licenses.</span></span>
    
3. <span data-ttu-id="0a6e6-135">**제품 라이선스** 창에서 **Enterprise Mobility + Security E5**에 대한 제품 라이선스를 **설정**으로 바꾸고 **저장**을 클릭한 후 **닫기**를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6e6-135">On the **Product licenses** pane, turn the product license for **Enterprise Mobility + Security E5** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="0a6e6-136">다른 모든 계정(사용자 1, 사용자 2, 사용자 3, 사용자 4 및 사용자 5)에 대해 2-3단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6e6-136">For all of your other accounts (User1 [if present], User 2, User 3, User 4, and User 5), do steps 2 and 3.</span></span>
    
<span data-ttu-id="0a6e6-137">이제 개발/테스트 환경에는 다음이 구현됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a6e6-137">Your Office 365 and EMS dev/test environment now has:</span></span>
  
- <span data-ttu-id="0a6e6-138">Azure 인프라 서비스에서 실행되는 시뮬레이트된 인트라넷</span><span class="sxs-lookup"><span data-stu-id="0a6e6-138">A simulated intranet running in Azure infrastructure services.</span></span>
    
- <span data-ttu-id="0a6e6-139">사용자 계정 목록과 동일한 조직 및 동일한 Azure AD 테넌트를 공유하는 Office 365 E5 Enterprise 및 EMS 평가판 구독</span><span class="sxs-lookup"><span data-stu-id="0a6e6-139">Office 365 E5 Enterprise and EMS trial subscriptions sharing the same organization and the same Azure AD tenant with your list of user accounts.</span></span>
    
- <span data-ttu-id="0a6e6-140">모든 사용자 계정이 Office 365 E5 Enterprise 및 EMS를 사용하도록 설정</span><span class="sxs-lookup"><span data-stu-id="0a6e6-140">All of your user accounts enabled to use Office 365 E5 Enterprise and EMS.</span></span>
    
<span data-ttu-id="0a6e6-141">그림 2는 EMS를 추가하는 구성 결과를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="0a6e6-141">Figure 2 shows your resulting configuration, which adds EMS.</span></span>
  
<span data-ttu-id="0a6e6-142">**그림 2: Office 365 및 EMS를 사용한 Azure의 시뮬레이트된 인트라넷**</span><span class="sxs-lookup"><span data-stu-id="0a6e6-142">**Figure 2: The simulated intranet in Azure with Office 365 and EMS**</span></span>

![Azure, Office 365 및 EMS를 사용하는 One Microsoft 클라우드 개발/테스트 환경 2단계](images/fdb520fe-ebbd-4681-a80e-b60df52f07c5.png)
  
## <a name="phase-3-add-dynamics-365"></a><span data-ttu-id="0a6e6-144">3단계: Dynamics 365 추가</span><span class="sxs-lookup"><span data-stu-id="0a6e6-144">Phase 3: Add Dynamics 365</span></span>

<span data-ttu-id="0a6e6-145">이 단계에서는 Dynamics 365  평가판 구독을 등록하고 Office 365 및 EMS 평가판 구독과 동일한 조직에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6e6-145">In this phase, you sign up for the EMS trial subscription and add it to the same organization as your Office 365 trial subscription.</span></span>
  
1. <span data-ttu-id="0a6e6-146">데스크톱 컴퓨터 또는 CLIENT1의 브라우저에서 전역 관리자 계정의 자격 증명을 사용하여 [https://portal.office.comhttps://portal.office.com](https://portal.office.com)의 Office 365 포털에 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6e6-146">With a browser on either your desktop computer (lightweight) or from CLIENT1 (simulated enterprise), sign in to the Office 365 portal at  https://portal.office.com https://portal.office.com  with the credentials of your global administrator account.</span></span>
    
2. <span data-ttu-id="0a6e6-147">**관리** 타일을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6e6-147">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="0a6e6-148">**Office 관리 센터** 탭에 있는 왼쪽 탐색 영역에서 **대금 청구 > 서비스 구매**를 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6e6-148">On the **Office Admin center** tab in your browser, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="0a6e6-p105">**구매 서비스** 페이지에서 **Dynamics 365 Plan 1 Enterprise Edition** 항목을 찾습니다. 마우스 포인터를 가져간 후 **평가판 시작**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6e6-p105">On the **Purchase services** page, find the **Enterprise Mobility + Security E5** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="0a6e6-151">**주문 확인** 페이지에서 **지금 평가판 사용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6e6-151">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="0a6e6-152">**주문 접수** 페이지에서 **계속**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6e6-152">On the **Order receipt** page, click **Continue**.</span></span>
    
> [!NOTE]
> <span data-ttu-id="0a6e6-p106">Dynamics 365 Plan 1 Enterprise Edition 평가 기간은 30일입니다. 추가로 30일 동안 내역 구독을 연장할 수 있습니다. 영구 개발/테스트 환경의 경우 소수의 라이선스를 사용해서 유료 구독을 새로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0a6e6-p106">The Dynamics 365 Plan 1 Enterprise Edition trial subscription is 30 days. You can easily extend the trail subscription for another 30 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
<span data-ttu-id="0a6e6-156">다음 단계에 따라 전역 관리자, 사용자 2 및 사용자 3 계정에 Dynamics 365 라이선스를 할당하고 시스템 관리자로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6e6-156">Use these steps to assign Dynamics 365 licenses to the global administrator, User 2, and User 3 accounts and make them system administrators.</span></span>
  
1. <span data-ttu-id="0a6e6-157">**Office 관리 센터** 탭에서 **사용자 > 활성 사용자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6e6-157">On the **Office 365 Admin center** tab in your browser, in the left navigation, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="0a6e6-158">활성 사용자 목록에서 전역 관리자 계정을 클릭한 다음, **제품 라이선스**에 대해 **편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6e6-158">In the list of active users, click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="0a6e6-159">**제품 라이선스** 창에서 **Dynamics 365 Plan 1 Enterprise Edition**에 대한 제품 라이선스를 **설정**으로 바꾸고 **저장**을 클릭한 후 **닫기**를 차례로 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6e6-159">On the **Product licenses** pane, turn the product license for **Dynamics 365 Plan 1 Enterprise Edition** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="0a6e6-160">사용자 2 및 사용자 3 계정에 대해 2, 3단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6e6-160">Perform steps 2 and 3 for the User 2 and User 3 accounts.</span></span>
    
5. <span data-ttu-id="0a6e6-161">**Office 관리 센터** 탭을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="0a6e6-161">Close the **Office admin center** tab.</span></span>
    
<span data-ttu-id="0a6e6-162">다음 단계를 사용하여 사용자 2 및 사용자 3 계정을 Dynamics 365 시스템 관리자로 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6e6-162">Use these steps to configure the User 2 and User 3 accounts as Dynamics 365 system administrators.</span></span>
  
1. <span data-ttu-id="0a6e6-163">브라우저의 **Office 관리 센터** 탭에 있는 왼쪽 탐색 영역에서 **관리 센터**를 클릭하고 **Dynamics 365**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6e6-163">On the **Office Admin center** tab in your browser, in the left navigation, click **Admin centers**, and then click **Dynamics 365**.</span></span>
    
    <span data-ttu-id="0a6e6-164">메뉴에 Dynamics 365가 표시되기 전에 Dynamics 365에서 프로비전이 완료될 때까지 기다려야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a6e6-164">You may need to wait for Dynamics 365 to finish provisioning before Dynamics 365 appears in the menu.</span></span>
    
2. <span data-ttu-id="0a6e6-165">Dynamics 365 탭에서 **이러한 항목 모두**를 클릭한 후 **설치 완료**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6e6-165">On the Dynamics 365 tab, click **All of these**, and then click **Complete Setup.**</span></span>
    
    <span data-ttu-id="0a6e6-166">설치가 완료될 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="0a6e6-166">Wait for provisioning to complete.</span></span>
    
    <span data-ttu-id="0a6e6-p107">설치가 완료되면 내역 구독에 포함된 샘플 데이터를 기준으로 하는 판매 활동 대시보드가 표시됩니다. 몇 분 정도 할애하여 **평가판 시작** 비디오를 시청하세요. 완료되면 비디오 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="0a6e6-p107">When setup completes, it displays a Sales Activity Dashboard based on sample data that is part of the trail subscription. Take a few moments to view the **Welcome to your trial** video. Close the video window when complete.</span></span>
    
3. <span data-ttu-id="0a6e6-170">맨 위에 있는 도구 모음에서 **판매** 옆에 있는 아래쪽 화살표를 클릭하고 **설정**을 클릭한 후 **보안**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6e6-170">On the toolbar at the top, click the down arrow next to **Sales**, click **Settings**, and then click **Security**.</span></span>
    
4. <span data-ttu-id="0a6e6-171">**보안** 페이지에서 **사용자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6e6-171">On the **Security** page, click **Users**.</span></span>
    
5. <span data-ttu-id="0a6e6-172">사용자 목록에서 **사용자 2**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6e6-172">In the list of users, click **CEO**.</span></span>
    
6. <span data-ttu-id="0a6e6-173">도구 모음에서 **역할 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6e6-173">In the tool bar, click **Manage Roles**.</span></span>
    
7. <span data-ttu-id="0a6e6-174">**역할 관리**에서 **시스템 관리자**를 클릭하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6e6-174">In **Manage Roles**, click **System Administrator**, and then click **OK**.</span></span>
    
8. <span data-ttu-id="0a6e6-175">맨 위의 도구 모음에서 **보안**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6e6-175">In the tool bar at the top click **Security**.</span></span>
    
9. <span data-ttu-id="0a6e6-176">사용자 3 계정에 대해 5-8단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6e6-176">Repeat steps 5-8 for the User 3 account.</span></span>
    
10. <span data-ttu-id="0a6e6-177">**사용자: 사용자3** 탭을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="0a6e6-177">Close the **User: User3** tab.</span></span>
    
> [!NOTE]
> <span data-ttu-id="0a6e6-178">Office 365 전역 관리자 계정에 Dynamics 365 시스템 관리자 역할이 자동으로 할당되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0a6e6-178">Your Office 365 global administrator account was automatically assigned the Dynamics 365 system administrator role.</span></span> 
  
<span data-ttu-id="0a6e6-179">이제 개발/테스트 환경에는 다음이 구현됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a6e6-179">Your Office 365 and EMS dev/test environment now has:</span></span>
  
- <span data-ttu-id="0a6e6-180">Azure 인프라 서비스에서 실행되는 시뮬레이트된 인트라넷</span><span class="sxs-lookup"><span data-stu-id="0a6e6-180">A simulated intranet running in Azure infrastructure services.</span></span>
    
- <span data-ttu-id="0a6e6-181">사용자 계정 목록과 동일한 조직 및 동일한 Azure AD 테넌트를 공유하는 Office 365 E5 Enterprise, EMS 및 Dynamics 365 평가판 구독</span><span class="sxs-lookup"><span data-stu-id="0a6e6-181">Office 365 E5 Enterprise and EMS trial subscriptions sharing the same organization and the same Azure AD tenant with your list of user accounts.</span></span>
    
- <span data-ttu-id="0a6e6-182">모든 사용자 계정이 Office 365 E5 Enterprise 및 EMS를 사용하도록 설정</span><span class="sxs-lookup"><span data-stu-id="0a6e6-182">All of your user accounts enabled to use Office 365 E5 Enterprise and EMS.</span></span>
    
- <span data-ttu-id="0a6e6-183">전역 엔터프라이즈 관리자, 사용자 2 및 사용자 3 계정이 Dynamics 365를 사용하도록 설정되며, Dynamics 365 시스템 관리자가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a6e6-183">Your global enterprise administrator, User 2, and User 3 accounts are enabled to use Dynamics 365 and are Dynamics 365 system administrators.</span></span>
    
<span data-ttu-id="0a6e6-184">그림 3은 구성 결과를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="0a6e6-184">Figure 3 shows your resulting configuration.</span></span>
  
<span data-ttu-id="0a6e6-185">**그림 3: Office 365, EMS 및 Dynamics 365를 사용한 Azure의 시뮬레이트된 인트라넷**</span><span class="sxs-lookup"><span data-stu-id="0a6e6-185">**Figure 3: The simulated intranet in Azure with Office 365, EMS, and Dynamics 365**</span></span>

![Azure, Office 365, EMS 및 Dynamics 365를 사용하는 One Microsoft 클라우드 개발/테스트 환경 3단계](images/31714fcc-0c7d-411f-bcd1-c62d9be090ee.png)
  
## <a name="next-steps"></a><span data-ttu-id="0a6e6-187">다음 단계</span><span class="sxs-lookup"><span data-stu-id="0a6e6-187">Next steps</span></span>

<span data-ttu-id="0a6e6-p108">이제 One Microsoft 클라우드 개발/테스트 환경을 체험해볼 수 있습니다. 지원되는 몇 가지 환경은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0a6e6-p108">You can now experiment with your One Microsoft Cloud dev/test environment. Here are some ideas for guided experiences:</span></span>
  
- [<span data-ttu-id="0a6e6-190">Office 365용 EMS 응용 프로그램에서 MAM(모바일 응용 프로그램 관리) 정책 구성</span><span class="sxs-lookup"><span data-stu-id="0a6e6-190">Configure mobile application management (MAM) policies in EMS for Office 365 applications</span></span>](https://technet.microsoft.com/library/mt764059.aspx)
    
- [<span data-ttu-id="0a6e6-191">Office 365의 Exchange Online과 Dynamics 365 연락처와의 통합 예시</span><span class="sxs-lookup"><span data-stu-id="0a6e6-191">Demonstrate Exchange Online in Office 365 integration with Dynamics 365 contacts</span></span>](https://technet.microsoft.com/library/mt798313.aspx)
    
- [<span data-ttu-id="0a6e6-192">서버 기반 워크로드를 호스트하기 위해 Azure 인프라 서비스에서 시뮬레이트된 크로스-프레미스 네트워크 만들기</span><span class="sxs-lookup"><span data-stu-id="0a6e6-192">Create a simulated cross-premises network in Azure infrastructure services for hosting server-based workloads</span></span>](https://technet.microsoft.com/library/mt745150.aspx)
    
## <a name="see-also"></a><span data-ttu-id="0a6e6-193">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0a6e6-193">See Also</span></span>

[<span data-ttu-id="0a6e6-194">클라우드 도입 TLG(테스트 랩 가이드)</span><span class="sxs-lookup"><span data-stu-id="0a6e6-194">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="0a6e6-195">Microsoft 클라우드 IT 아키텍처 리소스</span><span class="sxs-lookup"><span data-stu-id="0a6e6-195">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)
  
[<span data-ttu-id="0a6e6-196">하이브리드 솔루션</span><span class="sxs-lookup"><span data-stu-id="0a6e6-196">Hybrid solutions</span></span>](hybrid-solutions.md)
  
[<span data-ttu-id="0a6e6-197">보안 솔루션</span><span class="sxs-lookup"><span data-stu-id="0a6e6-197">Security solutions</span></span>](security-solutions.md)





