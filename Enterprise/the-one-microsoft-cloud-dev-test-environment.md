---
title: "하나의 Microsoft 클라우드 개발/테스트 환경"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Strat_O365_Enterprise
- Ent_TLGs
ms.assetid: a1370fe4-2fd6-4fea-ad1d-3555433d6d2e
description: "요약:이 테스트 랩 가이드를 사용 하 여 Microsoft의 클라우드 서비스를 모두 포함 하는 개발/테스트 환경을 만들 수 있습니다."
ms.openlocfilehash: 486aabd769461a7e743ac390d633913053b467a8
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/09/2018
---
# <a name="the-one-microsoft-cloud-devtest-environment"></a><span data-ttu-id="8bcb7-103">하나의 Microsoft 클라우드 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="8bcb7-103">The One Microsoft Cloud dev/test environment</span></span>

 <span data-ttu-id="8bcb7-104">**요약:** 이 테스트 랩 가이드를 사용 하 여 Microsoft의 클라우드 서비스를 모두 포함 하는 개발/테스트 환경을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8bcb7-104">**Summary:** Use this Test Lab Guide to create a dev/test environment that includes all of Microsoft's cloud offerings.</span></span>
  
<span data-ttu-id="8bcb7-p101">이 문서의 지침을 시뮬레이션 된 인트라넷 Microsoft Azure 인프라 서비스에 만들고 Microsoft Office 365, Microsoft Enterprise 이동성 + 보안 (EMS) 및 Microsoft Dynamics 365 구독을 추가 합니다. 결과 단일 개발/테스트 환경에서 동시에 모든 Microsoft 클라우드 서비스를 사용 하는 간소화 된 조직입니다.</span><span class="sxs-lookup"><span data-stu-id="8bcb7-p101">With the instructions in this article, you create a simulated intranet in Microsoft Azure infrastructure services and then add Microsoft Office 365, Microsoft Enterprise Mobility + Security (EMS), and Microsoft Dynamics 365 subscriptions. The result is a simplified organization that uses all Microsoft's cloud offerings at the same time in a single dev/test environment.</span></span> 
  
![Azure, Office 365, EMS 및 Dynamics 365를 사용하는 One Microsoft 클라우드 개발/테스트 환경 3 단계](images/31714fcc-0c7d-411f-bcd1-c62d9be090ee.png)
  
<span data-ttu-id="8bcb7-108">결과 구성을 사용 하 여 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8bcb7-108">You can use the resulting configuration to:</span></span>
  
- <span data-ttu-id="8bcb7-109">통합 하 여 Azure Active Directory (AD)를 제공 하는 일반적인 identity 인프라와 같은 Microsoft의 클라우드 서비스 간에 경험이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bcb7-109">Experience the integration across Microsoft's cloud offerings, such as the common identity infrastructure provided by Azure Active Directory (AD).</span></span>
    
- <span data-ttu-id="8bcb7-110">여러 Microsoft 클라우드 서비스를 포함 하는-종단간 시나리오를 평가 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bcb7-110">Evaluate end-to-end scenarios that include multiple Microsoft Cloud offerings.</span></span>
    
- <span data-ttu-id="8bcb7-111">데모, 개념 증명 또는 여러 Microsoft 클라우드 서비스를 사용 하는 개발/테스트 구성을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8bcb7-111">Create a demo, proof-of-concept, or dev/test configuration that uses multiple Microsoft Cloud offerings.</span></span>
    
- <span data-ttu-id="8bcb7-112">전문적인 개발을 위한 Microsoft 클라우드 대비한을 구축 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bcb7-112">Build your Microsoft Cloud skills for professional development.</span></span>
    
## <a name="phase-1-create-a-simulated-intranet-and-add-office-365"></a><span data-ttu-id="8bcb7-113">1 단계: 시뮬레이션 된 인트라넷 연결을 만들고 Office 365에 추가</span><span class="sxs-lookup"><span data-stu-id="8bcb7-113">Phase 1: Create a simulated intranet and add Office 365</span></span>

<span data-ttu-id="8bcb7-114">[Office 365 개발/테스트 환경에 대 한 디렉터리 동기화](dirsync-for-your-office-365-dev-test-environment.md)의 지시를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="8bcb7-114">Follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="8bcb7-115">그림 1에는 Office 365와 온-프레미스 Windows Server Active Directory (AD) 포리스트에서 Azure 인프라 서비스 및 디렉터리 동기화를 실행 하는 시뮬레이션 된 인트라넷을 포함 하 여 결과 구성을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="8bcb7-115">Figure 1 shows your resulting configuration, which includes Office 365 and a simulated intranet running in Azure infrastructure services and directory synchronization from an on-premises Windows Server Active Directory (AD) forest.</span></span>
  
<span data-ttu-id="8bcb7-116">**그림 1: Office 365와 Azure에서 시뮬레이트된 인트라넷**</span><span class="sxs-lookup"><span data-stu-id="8bcb7-116">**Figure 1: The simulated intranet in Azure with Office 365**</span></span>

![DirSync를 사용하는 Office 365 개발/테스트 환경](images/be5b37b0-f832-4878-b153-436c31546e21.png)
  
> [!NOTE]
> <span data-ttu-id="8bcb7-p102">Azure 평가판은 30 일입니다. Office 365 Enterprise e 5 평가판 구독은 쉽게 확장할 수 있습니다를 다른 30 일 하는 30 일입니다. 영구 개발/테스트 환경에 대 한 만들기 새 Azure 구독 및 라이선스 수가 적은로 새 유료 Office 365 Enterprise E5 구독을 지불 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bcb7-p102">The Azure trial is 30 days. The Office 365 Enterprise E5 Trial subscription is 30 days, which can be easily extended for another 30 days. For a permanent dev/test environment, create a new paid Azure subscription and a new paid Office 365 Enterprise E5 subscription with a small number of licenses.</span></span> 
  
## <a name="phase-2-add-ems"></a><span data-ttu-id="8bcb7-121">2 단계: EMS 추가</span><span class="sxs-lookup"><span data-stu-id="8bcb7-121">Phase 2: Add EMS</span></span>

<span data-ttu-id="8bcb7-122">이 단계에서는 EMS 평가판 구독을 등록하고 Office 365 평가판 구독과 동일한 조직에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="8bcb7-122">In this phase, you sign up for the EMS trial subscription and add it to the same organization as your Office 365 trial subscription.</span></span>
  
1. <span data-ttu-id="8bcb7-123">중 하나에서 브라우저와 데스크톱 컴퓨터에서 CLIENT1, 로그인에 [https://portal.office.com](https://portal.office.com) 전역 관리자 계정의 자격 증명을 사용 하 여 Office 365 포털에 또는 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bcb7-123">With a browser on either your desktop computer or from CLIENT1, sign in to the Office 365 portal at [https://portal.office.com](https://portal.office.com) with the credentials of your global administrator account.</span></span>
    
2. <span data-ttu-id="8bcb7-124">**Admin** 타일을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bcb7-124">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="8bcb7-125">왼쪽 탐색 영역에서 브라우저에서 **Office 관리 센터** 탭을 클릭 **대금 청구 > 구매 서비스**합니다.</span><span class="sxs-lookup"><span data-stu-id="8bcb7-125">On the **Office Admin center** tab in your browser, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="8bcb7-p103">**서비스 구매** 페이지 **Enterprise 이동성 + 보안 e 5** 항목을 찾습니다. 마우스 포인터를 올려 하 고 **무료 평가판을 시작**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bcb7-p103">On the **Purchase services** page, find the **Enterprise Mobility + Security E5** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="8bcb7-128">**주문 확인** 페이지에서 **지금 시도**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bcb7-128">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="8bcb7-129">**순서 확인** 페이지에서 **계속**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bcb7-129">On the **Order receipt** page, click **Continue**.</span></span>
    
> [!NOTE]
> <span data-ttu-id="8bcb7-p104">Enterprise Mobility + Security E5 평가판 구독 기간은 90일입니다. 영구 개발/테스트 환경의 경우 소수의 라이선스를 사용해서 유료 구독을 새로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8bcb7-p104">The Enterprise Mobility + Security E5 trial subscription is 90 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
<span data-ttu-id="8bcb7-132">다음으로, 엔터프라이즈 이동성 + 모든 사용자 계정에 대 한 보안 E5 라이선스 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bcb7-132">Next, enable the Enterprise Mobility + Security E5 license for all user accounts.</span></span>
  
1. <span data-ttu-id="8bcb7-133">왼쪽 탐색 영역에서 브라우저에서 **Office 365 관리 센터** 탭을 클릭 **사용자 > 활성 사용자**합니다.</span><span class="sxs-lookup"><span data-stu-id="8bcb7-133">On the **Office 365 Admin center** tab in your browser, in the left navigation, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="8bcb7-134">전역 관리자 계정을 클릭 하 고 **제품 라이선스**에 대 한 **편집** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bcb7-134">Click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="8bcb7-135">**제품 라이선스** 창에서 **엔터프라이즈 이동성 + 보안 e 5** **전환**에 대 한 제품 라이선스 설정, **저장** 을 클릭 하 고 두번 **닫기** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bcb7-135">On the **Product licenses** pane, turn the product license for **Enterprise Mobility + Security E5** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="8bcb7-136">다른 계정을 (User1, 사용자 2, 사용자 3, 4 사용자 및 사용자 5) 모두에 대해 2-3 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="8bcb7-136">For all of your other accounts (User1, User 2, User 3, User 4, and User 5), do steps 2 and 3.</span></span>
    
<span data-ttu-id="8bcb7-137">개발/테스트 환경을 현재가지고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8bcb7-137">Your dev/test environment now has:</span></span>
  
- <span data-ttu-id="8bcb7-138">Azure 인프라 서비스에서 실행 되는 시뮬레이션 된 인트라넷 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bcb7-138">A simulated intranet running in Azure infrastructure services.</span></span>
    
- <span data-ttu-id="8bcb7-139">사용자 계정 목록과 동일한 조직 및 동일한 Azure AD 테넌트를 공유하는 Office 365 E5 Enterprise 및 EMS 평가판 구독</span><span class="sxs-lookup"><span data-stu-id="8bcb7-139">Office 365 E5 Enterprise and EMS trial subscriptions sharing the same organization and the same Azure AD tenant with your list of user accounts.</span></span>
    
- <span data-ttu-id="8bcb7-140">모든 사용자 계정이 Office 365 E5 Enterprise 및 EMS를 사용하도록 설정</span><span class="sxs-lookup"><span data-stu-id="8bcb7-140">All of your user accounts enabled to use Office 365 E5 Enterprise and EMS.</span></span>
    
<span data-ttu-id="8bcb7-141">그림 2 EMS를 추가 하는 구성에 결과 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="8bcb7-141">Figure 2 shows your resulting configuration, which adds EMS.</span></span>
  
<span data-ttu-id="8bcb7-142">**그림 2: Office 365와 EMS Azure의 시뮬레이션 된 인트라넷**</span><span class="sxs-lookup"><span data-stu-id="8bcb7-142">**Figure 2: The simulated intranet in Azure with Office 365 and EMS**</span></span>

![Azure, Office 365 및 EMS를 사용하는 One Microsoft 클라우드 개발/테스트 환경 2 단계](images/fdb520fe-ebbd-4681-a80e-b60df52f07c5.png)
  
## <a name="phase-3-add-dynamics-365"></a><span data-ttu-id="8bcb7-144">3 단계: Dynamics 365 추가</span><span class="sxs-lookup"><span data-stu-id="8bcb7-144">Phase 3: Add Dynamics 365</span></span>

<span data-ttu-id="8bcb7-145">이 단계에서 Dynamics 365 평가판 구독에 대 한 등록 하 여 Office 365 및 EMS 평가판 구독와 같은 조직에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bcb7-145">In this phase, you sign up for the Dynamics 365 trial subscription and add it to the same organization as your Office 365 and EMS trial subscriptions.</span></span>
  
1. <span data-ttu-id="8bcb7-146">브라우저를 사용 하는 중 하나에서 데스크톱 컴퓨터 또는 CLIENT1에서 로그인에 [https://portal.office.com](https://portal.office.com) 전역 관리자 계정의 자격 증명을 사용 하 여 Office 365 포털에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8bcb7-146">Using a browser on either your desktop computer or from CLIENT1, sign in to the Office 365 portal at [https://portal.office.com](https://portal.office.com) with the credentials of your global administrator account.</span></span>
    
2. <span data-ttu-id="8bcb7-147">**Admin** 타일을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bcb7-147">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="8bcb7-148">왼쪽 탐색 영역에서 **Office 관리 센터** 탭을 클릭 **대금 청구 > 구매 서비스**합니다.</span><span class="sxs-lookup"><span data-stu-id="8bcb7-148">On the **Office admin center** tab, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="8bcb7-p105">**서비스 구매** 페이지 **Dynamics 365 계획 1 Enterprise Edition** 항목을 찾습니다. 마우스 포인터를 올려 하 고 **무료 평가판을 시작**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bcb7-p105">On the **Purchase services** page, find the **Dynamics 365 Plan 1 Enterprise Edition** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="8bcb7-151">**주문 확인** 페이지에서 **지금 시도**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bcb7-151">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="8bcb7-152">**순서 확인** 페이지에서 **계속**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bcb7-152">On the **Order receipt** page, click **Continue**.</span></span>
    
> [!NOTE]
> <span data-ttu-id="8bcb7-p106">Dynamics 365 계획 1 Enterprise Edition 평가판 구독은 30 일입니다. 다른 30 일에 대 한 내역 구독을 쉽게 확장할 수 있습니다. 영구 개발/테스트 환경에 대 한 만들기 새 적은 수의 라이선스를 사용 하 여 구독을 지불 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bcb7-p106">The Dynamics 365 Plan 1 Enterprise Edition trial subscription is 30 days. You can easily extend the trail subscription for another 30 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
<span data-ttu-id="8bcb7-156">전역 관리자, 사용자 2 및 3 사용자 계정에 Dynamics 365 라이선스를 할당 하 고 시스템 관리자가 있도록 하려면 다음이 단계를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bcb7-156">Use these steps to assign Dynamics 365 licenses to the global administrator, User 2, and User 3 accounts and make them system administrators.</span></span>
  
1. <span data-ttu-id="8bcb7-157">**Office 관리 센터** 탭을 클릭 **사용자 > 활성 사용자**합니다.</span><span class="sxs-lookup"><span data-stu-id="8bcb7-157">On the **Office admin center** tab, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="8bcb7-158">활성 사용자 목록에서 전역 관리자 계정을 클릭 하 고 **제품 라이선스**에 대 한 **편집** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bcb7-158">In the list of active users, click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="8bcb7-159">**제품 라이선스** 창에서 **전환** **Dynamics 365 계획 1 Enterprise Edition** 대 한 제품 라이선스 설정, **저장** 을 클릭 하 고 두번 **닫기** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bcb7-159">On the **Product licenses** pane, turn the product license for **Dynamics 365 Plan 1 Enterprise Edition** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="8bcb7-160">사용자 2 및 3 사용자 계정에 대해 2-3 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bcb7-160">Perform steps 2 and 3 for the User 2 and User 3 accounts.</span></span>
    
5. <span data-ttu-id="8bcb7-161">**Office 관리 센터** 탭을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="8bcb7-161">Close the **Office admin center** tab.</span></span>
    
<span data-ttu-id="8bcb7-162">Dynamics 365 시스템 관리자는 사용자 2 및 3 사용자 계정을 구성 하려면 다음이 단계를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bcb7-162">Use these steps to configure the User 2 and User 3 accounts as Dynamics 365 system administrators.</span></span>
  
1. <span data-ttu-id="8bcb7-163">왼쪽 탐색 영역에서 브라우저에서 **Office 관리 센터** 탭에서 **관리 센터**, 를클릭하고 **Dynamics 365**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bcb7-163">On the **Office Admin center** tab in your browser, in the left navigation, click **Admin centers**, and then click **Dynamics 365**.</span></span>
    
    <span data-ttu-id="8bcb7-164">Dynamics 365 Dynamics 365 메뉴에 표시 되기 전에 프로 비전을 완료할 때까지 대기 해야할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8bcb7-164">You may need to wait for Dynamics 365 to finish provisioning before Dynamics 365 appears in the menu.</span></span>
    
2. <span data-ttu-id="8bcb7-165">Dynamics 365 탭에서 **대부분의**를 클릭 하 고 다음을 클릭 **설치를 완료 합니다.**</span><span class="sxs-lookup"><span data-stu-id="8bcb7-165">On the Dynamics 365 tab, click **All of these**, and then click **Complete Setup.**</span></span>
    
    <span data-ttu-id="8bcb7-166">설치가 완료 될 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="8bcb7-166">Wait for setup to complete.</span></span>
    
    <span data-ttu-id="8bcb7-p107">설치가 완료 되 면 내역 구독의 일부인 샘플 데이터를 기반으로 영업 활동 대시보드를 표시 합니다. **평가판 시작** 보려면 잠시 비디오를 수행 합니다. 완료 되 면 비디오 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="8bcb7-p107">When setup completes, it displays a Sales Activity Dashboard based on sample data that is part of the trail subscription. Take a few moments to view the **Welcome to your trial** video. Close the video window when complete.</span></span>
    
3. <span data-ttu-id="8bcb7-170">위쪽 도구 모음에서 **Sales**옆에 있는 아래쪽 화살표를 클릭 하 고 **설정**, **보안**을 클릭 한 다음 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bcb7-170">On the toolbar at the top, click the down arrow next to **Sales**, click **Settings**, and then click **Security**.</span></span>
    
4. <span data-ttu-id="8bcb7-171">**보안** 페이지에서 **사용자**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bcb7-171">On the **Security** page, click **Users**.</span></span>
    
5. <span data-ttu-id="8bcb7-172">사용자의 목록에서 **사용자 2**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bcb7-172">In the list of users, click **User 2**.</span></span>
    
6. <span data-ttu-id="8bcb7-173">도구 모음에서 **관리 역할**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bcb7-173">In the tool bar, click **Manage Roles**.</span></span>
    
7. <span data-ttu-id="8bcb7-174">**역할 관리** **시스템 관리자**클릭 한 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bcb7-174">In **Manage Roles**, click **System Administrator**, and then click **OK**.</span></span>
    
8. <span data-ttu-id="8bcb7-175">맨 위쪽에 있는 도구 모음에서 **보안**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bcb7-175">In the tool bar at the top click **Security**.</span></span>
    
9. <span data-ttu-id="8bcb7-176">3 사용자 계정에 대해 5-8 단계를 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bcb7-176">Repeat steps 5-8 for the User 3 account.</span></span>
    
10. <span data-ttu-id="8bcb7-177">닫기는 **사용자: User3** 탭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bcb7-177">Close the **User: User3** tab.</span></span>
    
> [!NOTE]
> <span data-ttu-id="8bcb7-178">Office 365 전역 관리자 계정 Dynamics 365 시스템 관리자 역할을 자동으로 할당 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8bcb7-178">Your Office 365 global administrator account was automatically assigned the Dynamics 365 system administrator role.</span></span> 
  
<span data-ttu-id="8bcb7-179">개발/테스트 환경을 현재가지고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8bcb7-179">Your dev/test environment now has:</span></span>
  
- <span data-ttu-id="8bcb7-180">Azure 인프라 서비스에서 실행 되는 시뮬레이션 된 인트라넷 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bcb7-180">A simulated intranet running in Azure infrastructure services.</span></span>
    
- <span data-ttu-id="8bcb7-181">Office 365 e 5 Enterprise, EMS, 및 Dynamics 365 평가판 구독 사용자 계정의 대화 목록와 같은 조직 및 동일한 Azure AD 테 넌 트를 공유 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bcb7-181">Office 365 E5 Enterprise, EMS, and Dynamics 365 trial subscriptions sharing the same organization and the same Azure AD tenant with your list of user accounts.</span></span>
    
- <span data-ttu-id="8bcb7-182">모든 사용자 계정이 Office 365 E5 Enterprise 및 EMS를 사용하도록 설정</span><span class="sxs-lookup"><span data-stu-id="8bcb7-182">All of your user accounts enabled to use Office 365 E5 Enterprise and EMS.</span></span>
    
- <span data-ttu-id="8bcb7-183">사용자 글로벌 엔터프라이즈 관리자, 사용자 2 및 3 사용자 계정을 Dynamics 365 사용 하 여 사용 되며 Dynamics 365 시스템 관리자가.</span><span class="sxs-lookup"><span data-stu-id="8bcb7-183">Your global enterprise administrator, User 2, and User 3 accounts are enabled to use Dynamics 365 and are Dynamics 365 system administrators.</span></span>
    
<span data-ttu-id="8bcb7-184">그림 3은 결과 구성을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="8bcb7-184">Figure 3 shows your resulting configuration.</span></span>
  
<span data-ttu-id="8bcb7-185">**그림 3: Office 365, EMS, Dynamics 365 Azure에서 시뮬레이트된 인트라넷**</span><span class="sxs-lookup"><span data-stu-id="8bcb7-185">**Figure 3: The simulated intranet in Azure with Office 365, EMS, and Dynamics 365**</span></span>

![Azure, Office 365, EMS 및 Dynamics 365를 사용하는 One Microsoft 클라우드 개발/테스트 환경 3 단계](images/31714fcc-0c7d-411f-bcd1-c62d9be090ee.png)
  
## <a name="next-steps"></a><span data-ttu-id="8bcb7-187">다음 단계</span><span class="sxs-lookup"><span data-stu-id="8bcb7-187">Next steps</span></span>

<span data-ttu-id="8bcb7-p108">이제 한 Microsoft 클라우드 개발/테스트 환경 실험 수 있습니다. 실무 안내 경험에 대 한 몇가지 아이디어는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8bcb7-p108">You can now experiment with your One Microsoft Cloud dev/test environment. Here are some ideas for guided experiences:</span></span>
  
- [<span data-ttu-id="8bcb7-190">Office 365 응용 프로그램에 대 한 EMS에서 모바일 응용 프로그램 관리 (MAM) 정책 구성</span><span class="sxs-lookup"><span data-stu-id="8bcb7-190">Configure mobile application management (MAM) policies in EMS for Office 365 applications</span></span>](https://technet.microsoft.com/library/mt764059.aspx)
    
- [<span data-ttu-id="8bcb7-191">Office 365 통합 Dynamics 365 대화 상대와의 Exchange Online 시연</span><span class="sxs-lookup"><span data-stu-id="8bcb7-191">Demonstrate Exchange Online in Office 365 integration with Dynamics 365 contacts</span></span>](https://technet.microsoft.com/library/mt798313.aspx)
    
- [<span data-ttu-id="8bcb7-192">서버 기반 작업 부하를 호스팅하기 위한 Azure 인프라 서비스에서 시뮬레이션 된 크로스-프레미스 네트워크를 만들기</span><span class="sxs-lookup"><span data-stu-id="8bcb7-192">Create a simulated cross-premises network in Azure infrastructure services for hosting server-based workloads</span></span>](https://technet.microsoft.com/library/mt745150.aspx)
    
## <a name="see-also"></a><span data-ttu-id="8bcb7-193">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8bcb7-193">See Also</span></span>

[<span data-ttu-id="8bcb7-194">클라우드 도입 TLG(테스트 랩 가이드)</span><span class="sxs-lookup"><span data-stu-id="8bcb7-194">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="8bcb7-195">Microsoft 클라우드 IT 아키텍처 리소스</span><span class="sxs-lookup"><span data-stu-id="8bcb7-195">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)
  
[<span data-ttu-id="8bcb7-196">하이브리드 솔루션</span><span class="sxs-lookup"><span data-stu-id="8bcb7-196">Hybrid solutions</span></span>](hybrid-solutions.md)
  
[<span data-ttu-id="8bcb7-197">보안 솔루션</span><span class="sxs-lookup"><span data-stu-id="8bcb7-197">Security solutions</span></span>](security-solutions.md)





