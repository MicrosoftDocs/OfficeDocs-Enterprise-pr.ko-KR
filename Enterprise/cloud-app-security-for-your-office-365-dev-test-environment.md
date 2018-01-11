---
title: "Office 365 개발/테스트 환경에 대 한 클라우드 응용 프로그램 보안"
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
- TLG
- Ent_TLGs
ms.assetid: 22248f2f-b370-435e-b6ac-0ae0cae36b96
description: "요약: 구성 및 Office 365 개발/테스트 환경에서 Office 365 클라우드 응용 프로그램 보안을 시연 합니다."
ms.openlocfilehash: 8d398dcbf1ca5dea5ee790a64829eef55765025a
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/11/2018
---
# <a name="cloud-app-security-for-your-office-365-devtest-environment"></a><span data-ttu-id="bf465-103">Office 365 개발/테스트 환경에 대 한 클라우드 응용 프로그램 보안</span><span class="sxs-lookup"><span data-stu-id="bf465-103">Cloud App Security for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="bf465-104">**요약:** 구성 하 고 Office 365 개발/테스트 환경에서 Office 365 클라우드 응용 프로그램 보안을 시연 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf465-104">**Summary:** Configure and demonstrate Office 365 Cloud App Security in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="bf465-p101">이전에 Office 365 고급 보안 관리 라고 office 365 클라우드 응용 프로그램 보안에 대 한 모니터링 하 고 알리기 위해 Office 365 구독에 의심 스러운 활동의 조사 하 고 가능한 수행할 수 있도록 하는 정책을 만들 수 있습니다. 업데이트 관리 작업입니다. 자세한 내용은 [개요의 클라우드 앱 Office 365의 보안](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="bf465-p101">Office 365 Cloud App Security, previously known as Office 365 Advanced Security Management, allows you to create policies that monitor for and inform you of suspicious activities in your Office 365 subscription, so that you can investigate and take possible remediation action. For more information, see [Overview of Cloud App Security in Office 365](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475).</span></span>
  
<span data-ttu-id="bf465-107">이 문서의 지침을 사용 하도록 설정 하 고 Office 365 평가판 구독에서 클라우드 응용 프로그램 보안 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf465-107">With the instructions in this article, you enable and test Cloud App Security in your Office 365 trial subscription.</span></span>
  
> [!TIP]
> <span data-ttu-id="bf465-108">클릭 [여기](http://aka.ms/catlgstack) 에 한 맵이 하나의 Microsoft 클라우드 테스트 랩 가이드 스택의 모든 문서를 시각적으로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf465-108">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="bf465-109">1단계: 경량 또는 시뮬레이트된 엔터프라이즈 Office 365 개발/테스트 환경을 구축합니다.</span><span class="sxs-lookup"><span data-stu-id="bf465-109">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="bf465-110">최소 요구 사항을 경량 방식으로 클라우드 응용 프로그램 보안을 테스트 하려면 2와 [Office 365 개발/테스트 환경](office-365-dev-test-environment.md)의 3 단계에서 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="bf465-110">If you just want to test Cloud App Security in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="bf465-111">시뮬레이션 된 엔터프라이즈에서 클라우드 응용 프로그램 보안을 테스트 하려는 경우 [Office 365 개발/테스트 환경에 대 한 디렉터리 동기화](dirsync-for-your-office-365-dev-test-environment.md)의 지시를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="bf465-111">If you want to test Cloud App Security in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="bf465-p102">테스트 클라우드 앱 보안 인터넷에 연결 하는 시뮬레이션 된 인트라넷을 포함 하는 시뮬레이션 된 엔터프라이즈 개발/테스트 환경에 원하지 않는 및 Windows Server AD 포리스트에 대 한 디렉터리 동기화 합니다. 제공은 클라우드 응용 프로그램 보안을 테스트 하 고 일반적인 조직을 대표 하는 환경에서 사용해 수 있도록 하는 옵션으로 여기 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf465-p102">Testing Cloud App Security does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can test Cloud App Security and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-before-enabling-cloud-app-security-and-creating-a-policy"></a><span data-ttu-id="bf465-114">2 단계: 하기 전에 클라우드 응용 프로그램 보안을 사용 하도록 설정 하 고 정책 만들기</span><span class="sxs-lookup"><span data-stu-id="bf465-114">Phase 2: Before enabling Cloud App Security and creating a policy</span></span>

<span data-ttu-id="bf465-115">이 절차는 클라우드 응용 프로그램 보안을 사용 하도록 설정 하기 전에 사용자의 역할을 변경 없음 전자 메일 알림을 제공 전역 관리자에 게 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="bf465-115">In this procedure, you demonstrate that before enabling Cloud App Security, changing a user's role provides no email notification to the global administrator.</span></span>
  
### <a name="test-the-default-notification-behavior-of-office-365"></a><span data-ttu-id="bf465-116">Office 365의 기본 알림 동작 테스트</span><span class="sxs-lookup"><span data-stu-id="bf465-116">Test the default notification behavior of Office 365</span></span>

1. <span data-ttu-id="bf465-117">Office 365 포털 ([https://portal.office.com](https://portal.office.com))에 이동 하 고 전역 관리자 계정 사용 하 여 Office 365 평가판 구독에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf465-117">Go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
  - <span data-ttu-id="bf465-118">경량 Office 365 개발/테스트 환경을 사용하는 경우 로컬 컴퓨터에서 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="bf465-118">If you are using the lightweight Office 365 dev/test environment, sign in from your local computer.</span></span>
    
  - <span data-ttu-id="bf465-119">시뮬레이션 된 엔터프라이즈 Office 365 개발/테스트 환경을 사용 하는 경우 [Azure 포털](https://portal.azure.com) 을 사용 하 여 CLIENT1 가상 컴퓨터에 연결한 다음 CLIENT1에서 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf465-119">If you are using the simulated enterprise Office 365 dev/test environment, use the [Azure portal](https://portal.azure.com) to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="bf465-120">주 포털 페이지에서 **관리**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf465-120">From the main portal page, click **Admin**.</span></span>
    
3. <span data-ttu-id="bf465-121">왼쪽 탐색 영역에서 클릭 **사용자 > 활성 사용자**합니다.</span><span class="sxs-lookup"><span data-stu-id="bf465-121">In the left navigation, click **Users > Active users**.</span></span>
    
4. <span data-ttu-id="bf465-122">**사용자 4** 계정을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf465-122">Click the **User 4** account.</span></span>
    
5. <span data-ttu-id="bf465-123">**사용자 4** 페이지에서 **역할** 행에 대 한 **편집** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf465-123">On the **User 4** page, click **Edit** for the **Roles** row.</span></span>
    
6. <span data-ttu-id="bf465-p103">**사용자 역할 편집** 페이지에서 **전역 관리자**를 클릭 하 고 **user4@contoso.com** **대체 전자 메일 주소**입력 한 다음 **저장**을 클릭 합니다. **닫기** 를 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf465-p103">On the **Edit user roles** page, click **Global administrator**, type **user4@contoso.com** in the **Alternative email address**, and then click **Save**. Click **Close** twice.</span></span>
    
7. <span data-ttu-id="bf465-126">왼쪽 위에서에서 응용 프로그램 시작 관리자 아이콘을 선택 하 고 **메일**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf465-126">Select the app launcher icon in the upper-left and choose **Mail**.</span></span>
    
8. <span data-ttu-id="bf465-p104">30 분 기다립니다. 전역 관리자 권한으로 사용자 4 역할에서 변경 된 알려주는 받은 편지함에 전자 메일 메시지 없이 것을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf465-p104">Wait 30 minutes. Notice that there is no email message in the inbox notifying you of the change in User 4's role as a global administrator.</span></span>
    
## <a name="phase-3-enable-cloud-app-security-and-create-a-policy"></a><span data-ttu-id="bf465-129">3 단계: 클라우드 응용 프로그램 보안을 사용 하도록 설정 하 고 정책 만들기</span><span class="sxs-lookup"><span data-stu-id="bf465-129">Phase 3: Enable Cloud App Security and create a policy</span></span>

<span data-ttu-id="bf465-p105">이 절차를 있습니다 클라우드 응용 프로그램 보안을 설정 하 고 사용자 계정 역할의 변경 내용에 대 한 전역 관리자 계정에 게 전자 메일 알림을 보내도록 하는 새 정책을 만듭니다. 이 절차를 수행 하려면:</span><span class="sxs-lookup"><span data-stu-id="bf465-p105">In this procedure, you enable Cloud App Security and create a new policy to send email notifications to your global administrator account for changes in user account roles. This procedure requires:</span></span>
  
- <span data-ttu-id="bf465-132">Office 365 평가판 구독의 전역 관리자 계정 이름 및 암호.</span><span class="sxs-lookup"><span data-stu-id="bf465-132">The global administrator account name and password of your Office 365 trial subscription.</span></span>
    
- <span data-ttu-id="bf465-133">Office 365 평가판 구독의 User 5 계정 이름 및 암호.</span><span class="sxs-lookup"><span data-stu-id="bf465-133">The name and password of the User 5 account of your Office 365 trial subscription.</span></span>
    
### <a name="enable-and-configure-cloud-app-security"></a><span data-ttu-id="bf465-134">설정 하 고 클라우드 응용 프로그램 보안 설정 구성</span><span class="sxs-lookup"><span data-stu-id="bf465-134">Enable and configure Cloud App Security</span></span>

1. <span data-ttu-id="bf465-135">Office 365 포털 ([https://portal.office.com](https://portal.office.com))에 이동 하 고 전역 관리자 계정 사용 하 여 Office 365 평가판 구독에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf465-135">Go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
2. <span data-ttu-id="bf465-136">클릭 하 고 **보안 &amp; 준수** 바둑판식으로 배열 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf465-136">Click the **Security &amp; Compliance** tile.</span></span>
    
3. <span data-ttu-id="bf465-137">왼쪽된 탐색 창의 클릭 **알림 > 고급 알림 관리**합니다.</span><span class="sxs-lookup"><span data-stu-id="bf465-137">In the left navigation pane, click **Alerts > Manage advanced alerts**.</span></span>
    
4. <span data-ttu-id="bf465-138">**고급 알림 관리** 페이지에서 **Office 365 클라우드 응용 프로그램 보안 설정**를 클릭 한 다음 **Office 365 클라우드 응용 프로그램 보안으로 이동**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf465-138">On the **Manage advanced alerts** page, click **Turn on Office 365 Cloud App Security**, and then click **Go to Office 365 Cloud App Security**.</span></span>
    
5. <span data-ttu-id="bf465-139">새 **대시보드** 탭을 클릭 **제어 > 정책**합니다.</span><span class="sxs-lookup"><span data-stu-id="bf465-139">On the new **Dashboard** tab, click **Control > Policies**.</span></span>
    
6. <span data-ttu-id="bf465-140">**정책** 페이지에서 **정책 만들기**클릭 한 다음 **활동 정책**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf465-140">On the **Policy** page, click **Create policy**, and then click **Activity policy**.</span></span>
    
7. <span data-ttu-id="bf465-141">**정책 이름** **관리 작업**을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf465-141">In **Policy name**, type **Administrative activity**.</span></span>
    
8. <span data-ttu-id="bf465-142">**정책 심각도** **높은**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf465-142">In **Policy severity**, click **High**.</span></span>
    
9. <span data-ttu-id="bf465-143">**범주** **권한이 부여 된 계정**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf465-143">In **Category**, click **Privileged accounts**.</span></span>
    
10. <span data-ttu-id="bf465-144">**정책에 대 한 만들기 필터**에 **일치 하는 다음의 모든 활동**을에서 **관리 작업**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf465-144">In **Create filters for the policy**, in **Activities matching all of the following**, click **Administrative activity**.</span></span>
    
11. <span data-ttu-id="bf465-p106">**경고** **경고로 전자 메일 보내기**를 클릭 합니다. (영문) **를**, 전역 관리자 계정의 전자 메일 주소를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf465-p106">In **Alerts**, click **Send alert as email**. In **To**, type the email address of your global administrator account.</span></span>
    
12. <span data-ttu-id="bf465-147">페이지의 맨 아래에 **만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf465-147">At the bottom of the page, click **Create**.</span></span>
    
## <a name="phase-4-show-cloud-app-security-in-action"></a><span data-ttu-id="bf465-148">4 단계: 동작의 표시 클라우드 응용 프로그램 보안</span><span class="sxs-lookup"><span data-stu-id="bf465-148">Phase 4: Show Cloud App Security in action</span></span>

<span data-ttu-id="bf465-149">이 절차에서는 클라우드 앱 보안 경고를 만드는 방법을 보여주는 및 사용자 4가 사용자 5 암호 및 사용자 관리 관리자가 전역 관리자 계정에 전자 메일 알림을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="bf465-149">In this procedure, you demonstrate how Cloud App Security creates alerts and sends email notifications to the global administrator account when User 4 makes User 5 a password and user management administrator.</span></span>
  
### <a name="demonstrate-email-notification-for-a-change-in-user-account-roles"></a><span data-ttu-id="bf465-150">사용자 계정 역할 변경에 대한 전자 메일 알림 보여 주기</span><span class="sxs-lookup"><span data-stu-id="bf465-150">Demonstrate email notification for a change in user account roles</span></span>

1. <span data-ttu-id="bf465-151">위 오른쪽에서 사용자 아이콘을 클릭 하 고 **로그 아웃**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf465-151">In the upper-right, click the user icon, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="bf465-152">[Https://portal.office.com](https://portal.office.com)로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf465-152">Go to [https://portal.office.com](https://portal.office.com).</span></span>
    
3. <span data-ttu-id="bf465-153">Office 365 로그인 페이지에서 **다른 계정 사용**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf465-153">On the Office 365 sign in page, click **Use another account**.</span></span>
    
4. <span data-ttu-id="bf465-154">사용자 4 계정 이름 및 해당 암호를 입력 하 고 **로그인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf465-154">Type the User 4 account name and its password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="bf465-155">필요한 경우 사용자 4 계정 암호를 변경 하 고 **암호를 업데이트 하 고 로그인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf465-155">If needed, change the User 4 account password, and then click **Update password and sign in**.</span></span>
    
6. <span data-ttu-id="bf465-156">Office 365 포털 페이지에서 **관리**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf465-156">On the Office 365 portal page, click **Admin**.</span></span>
    
7. <span data-ttu-id="bf465-157">필요한 경우에 프로그램 관리자의 연락처 정보를 업데이트 하려면 대화 상자가 나타나면 **취소** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf465-157">If needed, click **cancel** when prompted to update your admin contact info.</span></span>
    
8. <span data-ttu-id="bf465-158">주 포털 페이지에서 **관리**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf465-158">From the main portal page, click **Admin**.</span></span>
    
9. <span data-ttu-id="bf465-159">왼쪽 탐색 영역에서 클릭 **사용자 > 활성 사용자**합니다.</span><span class="sxs-lookup"><span data-stu-id="bf465-159">In the left navigation, click **Users > Active users**.</span></span>
    
10. <span data-ttu-id="bf465-160">**5 사용자** 계정을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf465-160">Click the **User 5** account.</span></span>
    
11. <span data-ttu-id="bf465-161">**사용자 5** 페이지에서 **역할** 행에 대 한 **편집** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf465-161">On the **User 5** page, click **Edit** for the **Roles** row.</span></span>
    
12. <span data-ttu-id="bf465-p107">**사용자 역할 편집** 페이지에서 **사용자 지정 된 관리자**를 클릭합니다, 그리고 **암호 관리자** 및 **사용자 관리 관리자**를 클릭합니다, 그리고 **user5@contoso.com** **대체 전자 메일 주소**입력 하 고을 클릭합니다 **저장**합니다. **닫기** 를 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf465-p107">On the **Edit user roles** page, click **Customized administrator**, click **Password administrator** and **User management administrator**, type **user5@contoso.com** in the **Alternative email address**, and then click **Save**. Click **Close** twice.</span></span>
    
13. <span data-ttu-id="bf465-164">위 오른쪽에 있는 사용자 아이콘을 클릭 하 고 **로그 아웃**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf465-164">Click the user icon in the upper-right, and then click **Sign out**.</span></span> 
    
14. <span data-ttu-id="bf465-165">[Https://portal.office.com](https://portal.office.com)로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf465-165">Go to [https://portal.office.com](https://portal.office.com).</span></span>
    
15. <span data-ttu-id="bf465-166">**Office 365 로그인** 페이지에서 전역 관리자 계정 이름을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf465-166">On the **Office 365 sign in** page, click your global administrator account name.</span></span>
    
16. <span data-ttu-id="bf465-167">암호를 입력 한 다음 **로그인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf465-167">Type the password, and then click **Sign in**.</span></span>
    
17. <span data-ttu-id="bf465-168">주 포털 페이지에서 **관리**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf465-168">From the main portal page, click **Admin**.</span></span>
    
18. <span data-ttu-id="bf465-169">클릭 하 고 **보안 &amp; 준수** 바둑판식으로 배열 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf465-169">Click the **Security &amp; Compliance** tile.</span></span>
    
19. <span data-ttu-id="bf465-170">왼쪽된 탐색 창의 클릭 **알림 > 고급 알림 관리**합니다.</span><span class="sxs-lookup"><span data-stu-id="bf465-170">In the left navigation pane, click **Alerts > Manage advanced alerts**.</span></span>
    
20. <span data-ttu-id="bf465-171">**고급 알림 관리** 페이지에서 **Office 365 클라우드 응용 프로그램 보안으로 이동**합니다.를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf465-171">On the **Manage advanced alerts** page, click **Go to Office 365 Cloud App Security**.</span></span>
    
21. <span data-ttu-id="bf465-172">새 **대시보드** 탭에서 **관리 작업**에 대 한 두 새 경고를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf465-172">On the new **Dashboard** tab, notice the two new alerts for **Administrative activity**.</span></span>
    
22. <span data-ttu-id="bf465-p108">**Microsoft Office 홈** 탭에서 **메일**을 클릭 합니다. 최대 30 분까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="bf465-p108">From the **Microsoft Office Home** tab, click **Mail**. Wait up to 30 minutes.</span></span> 
    
    <span data-ttu-id="bf465-p109">두 새 전자 메일 메시지 제목 **Microsoft Azure AD 알림 서비스**와 받은 편지함에 나타납니다. 하나의 메시지 나타내고 사용자 5 계정 **암호 관리자** 역할에 추가 된 사용자 5 계정이 **사용자 관리자** 역할에 추가 된 다른 메시지를 나타냅니다 (같은 사용자 관리 관리자 역할에 Office 365 관리 센터)입니다.</span><span class="sxs-lookup"><span data-stu-id="bf465-p109">You should see two new email messages in the inbox with the title **Microsoft Azure AD Notification Service**. One message indicates that the User 5 account was added to the **Password Administrator** role and another message indicates that the User 5 account was added to the **User Administrator** role (equal to the User management administrator role in the Office 365 Admin center).</span></span>
    
<span data-ttu-id="bf465-p110">이제 새 정책 만들기 및 추가 Office 365 클라우드 응용 프로그램 보안을 사용해이 환경에 사용할 수 있습니다. 추가 구성 문서 링크를 [Office 365 클라우드 응용 프로그램 보안에 대 한 준비](https://support.office.com/article/Get-ready-for-Office-365-Cloud-App-Security-d9ee4d67-f2b3-42b4-9c9e-c4529904990a) 를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="bf465-p110">You can now use this environment to create new policies and further experiment with Office 365 Cloud App Security. See [Get ready for Office 365 Cloud App Security](https://support.office.com/article/Get-ready-for-Office-365-Cloud-App-Security-d9ee4d67-f2b3-42b4-9c9e-c4529904990a) for links to additional configuration articles.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="bf465-179">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bf465-179">See Also</span></span>

[<span data-ttu-id="bf465-180">클라우드 도입 TLG(테스트 랩 가이드)</span><span class="sxs-lookup"><span data-stu-id="bf465-180">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="bf465-181">Office 365 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="bf465-181">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="bf465-182">클라우드 채택 및 하이브리드 솔루션</span><span class="sxs-lookup"><span data-stu-id="bf465-182">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="bf465-183">Office 365의에서 클라우드 앱 보안 개요</span><span class="sxs-lookup"><span data-stu-id="bf465-183">Overview of Cloud App Security in Office 365</span></span>](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475)


