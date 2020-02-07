---
title: Office 365 개발/테스트 환경용 Cloud App Security
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/05/2018
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 22248f2f-b370-435e-b6ac-0ae0cae36b96
description: '요약: Office 365 개발/테스트 환경에서 Office 365 Cloud App Security를 구성 하 고 시연 하는 방법을 설명 합니다.'
ms.openlocfilehash: a4f0f9e8912a5455ec5253e9992873136e71d694
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41840805"
---
# <a name="cloud-app-security-for-your-office-365-devtest-environment"></a><span data-ttu-id="664ae-103">Office 365 개발/테스트 환경용 Cloud App Security</span><span class="sxs-lookup"><span data-stu-id="664ae-103">Cloud App Security for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="664ae-104">**요약:** Office 365 개발/테스트 환경에서 Office 365 Cloud App Security를 구성 하 고 시연 합니다.</span><span class="sxs-lookup"><span data-stu-id="664ae-104">**Summary:** Configure and demonstrate Office 365 Cloud App Security in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="664ae-105">Office 365 Cloud App Security (이전에는 Office 365 Advanced Security Management)를 사용 하 여 Office 365 구독에서 의심 스러운 활동을 모니터링 하 고이를 조사 하 고 문제를 해결 하는 데 도움이 되는 정책을 만들 수 있습니다. 동작은.</span><span class="sxs-lookup"><span data-stu-id="664ae-105">Office 365 Cloud App Security, previously known as Office 365 Advanced Security Management, lets you create policies that monitor for and inform you of suspicious activities in your Office 365 subscription, so that you can investigate and take possible remediation action.</span></span> <span data-ttu-id="664ae-106">자세한 내용은 [Office 365의 Cloud App Security 개요](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="664ae-106">For more information, see [Overview of Cloud App Security in Office 365](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475).</span></span>
  
<span data-ttu-id="664ae-107">이 문서의 지침을 사용 하 여 Office 365 평가판 구독에서 Cloud App Security를 사용 하도록 설정 하 고 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="664ae-107">With the instructions in this article, you enable and test Cloud App Security in your Office 365 trial subscription.</span></span>
  
> [!TIP]
> <span data-ttu-id="664ae-108">[여기](https://aka.ms/catlgstack)를 클릭하여 Office 365 테스트 랩 가이드 스택의 모든 문서에 대한 가상 맵을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="664ae-108">Click [here](https://aka.ms/catlgstack) for a visual map to all the articles in the Office 365 Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="664ae-109">1단계: 경량 또는 시뮬레이트된 엔터프라이즈 Office 365 개발/테스트 환경을 구축합니다.</span><span class="sxs-lookup"><span data-stu-id="664ae-109">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="664ae-110">최소 요구 사항에 따라 간단한 방법으로 Cloud App Security를 테스트 하려면 [Office 365 개발/테스트 환경의](office-365-dev-test-environment.md)2, 3 단계의 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="664ae-110">If you just want to test Cloud App Security in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="664ae-111">시뮬레이트된 엔터프라이즈에서 Cloud App Security를 테스트 하려면 [Office 365 개발/테스트 환경용 DirSync](dirsync-for-your-office-365-dev-test-environment.md)의 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="664ae-111">If you want to test Cloud App Security in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="664ae-112">클라우드 앱 보안을 테스트 하는 경우 AD DS (Active Directory 도메인 서비스) 포리스트의 인터넷 및 디렉터리 동기화에 연결 된 시뮬레이트된 인트라넷을 포함 하는 시뮬레이트된 엔터프라이즈 개발/테스트 환경이 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="664ae-112">Testing Cloud App Security does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for an Active Directory Domain Services (AD DS) forest.</span></span> <span data-ttu-id="664ae-113">클라우드 앱 보안을 테스트 하 고 일반적인 조직을 나타내는 환경에서 테스트해 볼 수 있도록 여기에 제공 되는 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="664ae-113">It is provided here as an option so that you can test Cloud App Security and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-before-enabling-cloud-app-security-and-creating-a-policy"></a><span data-ttu-id="664ae-114">2 단계: Cloud App Security를 사용 하도록 설정 하 고 정책을 만들기 전</span><span class="sxs-lookup"><span data-stu-id="664ae-114">Phase 2: Before enabling Cloud App Security and creating a policy</span></span>

<span data-ttu-id="664ae-115">이 절차에서는 Cloud App Security를 사용 하기 전에 사용자 역할을 변경 하면 전역 관리자에 게 전자 메일 알림이 제공 되지 않음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="664ae-115">In this procedure, you demonstrate that before enabling Cloud App Security, changing a user's role provides no email notification to the global administrator.</span></span>
  
### <a name="test-the-default-notification-behavior-of-office-365"></a><span data-ttu-id="664ae-116">Office 365의 기본 알림 동작 테스트</span><span class="sxs-lookup"><span data-stu-id="664ae-116">Test the default notification behavior of Office 365</span></span>

1. <span data-ttu-id="664ae-117">Microsoft 365 관리 센터 ([https://admin.microsoft.com](https://admin.microsoft.com))로 이동 하 고 전역 관리자 계정을 사용 하 여 Office 365 평가판 구독에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="664ae-117">Go to the Microsoft 365 admin center ([https://admin.microsoft.com](https://admin.microsoft.com)) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
  - <span data-ttu-id="664ae-118">경량 Office 365 개발/테스트 환경을 사용하는 경우 로컬 컴퓨터에서 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="664ae-118">If you are using the lightweight Office 365 dev/test environment, sign in from your local computer.</span></span>
    
  - <span data-ttu-id="664ae-119">시뮬레이트된 enterprise Office 365 개발/테스트 환경을 사용 하는 경우 [Azure portal](https://portal.azure.com) 을 사용 하 여 client1 가상 컴퓨터에 연결한 다음, client1에서 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="664ae-119">If you are using the simulated enterprise Office 365 dev/test environment, use the [Azure portal](https://portal.azure.com) to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="664ae-120">기본 포털 페이지에서 **관리자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="664ae-120">From the main portal page, click **Admin**.</span></span>
    
3. <span data-ttu-id="664ae-121">왼쪽 탐색에서 **사용자 > 활성화된 사용자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="664ae-121">In the left navigation, click **Users > Active users**.</span></span>
    
4. <span data-ttu-id="664ae-122">**User 4** 계정을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="664ae-122">Click the **User 4** account.</span></span>
    
5. <span data-ttu-id="664ae-123">**User 4** 페이지에서 **규칙** 열에 대한 **편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="664ae-123">On the **User 4** page, click **Edit** for the **Roles** row.</span></span>
    
6. <span data-ttu-id="664ae-p103">**사용자 역할 편집** 페이지에서 **전역 관리자**를 클릭하고 **대체 전자 메일 주소**에 **user4@contoso.com**을 입력한 다음 **저장**을 클릭합니다. **닫기**를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="664ae-p103">On the **Edit user roles** page, click **Global administrator**, type **user4@contoso.com** in the **Alternative email address**, and then click **Save**. Click **Close** twice.</span></span>
    
7. <span data-ttu-id="664ae-126">	왼쪽 위에서 앱 시작 관리자 아이콘을 선택하고 *\*메일*\*을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="664ae-126">Select the app launcher icon in the upper-left and choose **Mail**.</span></span>
    
8. <span data-ttu-id="664ae-127">30분간 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="664ae-127">Wait 30 minutes.</span></span> <span data-ttu-id="664ae-128">사용자 4의 역할이 전역 관리자로 변경 되었음을 알리는 받은 편지함에 전자 메일 메시지가 없는 것을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="664ae-128">Notice that there is no email message in the inbox notifying you of the change in User 4's role as a global administrator.</span></span>
    
## <a name="phase-3-enable-cloud-app-security-and-create-a-policy"></a><span data-ttu-id="664ae-129">3 단계: Cloud App Security를 사용 하도록 설정 하 고 정책 만들기</span><span class="sxs-lookup"><span data-stu-id="664ae-129">Phase 3: Enable Cloud App Security and create a policy</span></span>

<span data-ttu-id="664ae-130">이 절차에서는 Cloud App Security을 사용 하도록 설정 하 고 사용자 계정 역할 변경에 대 한 전자 메일 알림을 전역 관리자 계정에 보내도록 새 정책을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="664ae-130">In this procedure, you enable Cloud App Security and create a new policy to send email notifications to your global administrator account for changes in user account roles.</span></span> <span data-ttu-id="664ae-131">이 프로시저에는 다음 항목이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="664ae-131">This procedure requires:</span></span>
  
- <span data-ttu-id="664ae-132">Office 365 평가판 구독의 전역 관리자 계정 이름 및 암호.</span><span class="sxs-lookup"><span data-stu-id="664ae-132">The global administrator account name and password of your Office 365 trial subscription.</span></span>
    
- <span data-ttu-id="664ae-133">Office 365 평가판 구독의 User 5 계정 이름 및 암호.</span><span class="sxs-lookup"><span data-stu-id="664ae-133">The name and password of the User 5 account of your Office 365 trial subscription.</span></span>
    
### <a name="enable-and-configure-cloud-app-security"></a><span data-ttu-id="664ae-134">Cloud App Security 사용 및 구성</span><span class="sxs-lookup"><span data-stu-id="664ae-134">Enable and configure Cloud App Security</span></span>

1. <span data-ttu-id="664ae-135">Microsoft 365 관리 센터 ([https://admin.microsoft.com](https://admin.microsoft.com))로 이동 하 고 전역 관리자 계정을 사용 하 여 Office 365 평가판 구독에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="664ae-135">Go to the Microsoft 365 admin center ([https://admin.microsoft.com](https://admin.microsoft.com)) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
2. <span data-ttu-id="664ae-136">**관리** 타일을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="664ae-136">Click the **Admin** tile.</span></span> <span data-ttu-id="664ae-137">**Office 관리 센터** 탭에서 **관리 센터 > 보안 & 규정 준수**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="664ae-137">On the **Office Admin center** tab, click **Admin centers > Security & Compliance**.</span></span>
    
3. <span data-ttu-id="664ae-138">왼쪽 탐색 창에서 **경고 > 고급 알림 관리**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="664ae-138">In the left navigation pane, click **Alerts > Manage advanced alerts**.</span></span>
    
4. <span data-ttu-id="664ae-139">**고급 알림 관리** 페이지에서 **Office 365 Cloud app security 사용**을 클릭 하 고 **office 365 cloud app security로 이동을**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="664ae-139">On the **Manage advanced alerts** page, click **Turn on Office 365 Cloud App Security**, and then click **Go to Office 365 Cloud App Security**.</span></span>
    
5. <span data-ttu-id="664ae-140">새 **대시보드** 탭에서 **> 정책 제어**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="664ae-140">On the new **Dashboard** tab, click **Control > Policies**.</span></span>
    
6. <span data-ttu-id="664ae-141">**정책** 페이지에서 **정책 만들기**를 클릭 한 다음 **활동 정책을**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="664ae-141">On the **Policy** page, click **Create policy**, and then click **Activity policy**.</span></span>
    
7. <span data-ttu-id="664ae-142">**정책 이름**에 **관리 활동**을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="664ae-142">In **Policy name**, type **Administrative activity**.</span></span>
    
8. <span data-ttu-id="664ae-143">**정책 심각도**에서 **높음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="664ae-143">In **Policy severity**, click **High**.</span></span>
    
9. <span data-ttu-id="664ae-144">**범주**에서 **권한이 부여 된 계정을**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="664ae-144">In **Category**, click **Privileged accounts**.</span></span>
    
10. <span data-ttu-id="664ae-145">**정책에 대 한 필터 만들기**의 **다음 작업과 일치 하는 작업**의 **관리 작업**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="664ae-145">In **Create filters for the policy**, in **Activities matching all of the following**, click **Administrative activity**.</span></span>
    
11. <span data-ttu-id="664ae-p107">**경고**에서 **전자 메일로 경고 보내기**를 클릭합니다. **받는 사람**에서 전역 관리자 계정의 전자 메일 주소를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="664ae-p107">In **Alerts**, click **Send alert as email**. In **To**, type the email address of your global administrator account.</span></span>
    
12. <span data-ttu-id="664ae-148">페이지 하단에서 **만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="664ae-148">At the bottom of the page, click **Create**.</span></span>
    
## <a name="phase-4-show-cloud-app-security-in-action"></a><span data-ttu-id="664ae-149">4 단계: Cloud App Security in action을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="664ae-149">Phase 4: Show Cloud App Security in action</span></span>

<span data-ttu-id="664ae-150">이 절차에서는 사용자 4가 사용자 5를 암호 및 사용자 관리 관리자로 설정한 경우 Cloud App Security에서 알림을 만들고 전역 관리자 계정으로 전자 메일 알림을 보내는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="664ae-150">In this procedure, you demonstrate how Cloud App Security creates alerts and sends email notifications to the global administrator account when User 4 makes User 5 a password and user management administrator.</span></span>
  
### <a name="demonstrate-email-notification-for-a-change-in-user-account-roles"></a><span data-ttu-id="664ae-151">사용자 계정 역할 변경에 대한 전자 메일 알림 보여 주기</span><span class="sxs-lookup"><span data-stu-id="664ae-151">Demonstrate email notification for a change in user account roles</span></span>

1. <span data-ttu-id="664ae-152">오른쪽 위에서 사용자 아이콘을 클릭한 다음 **로그아웃**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="664ae-152">In the upper-right, click the user icon, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="664ae-153">[https://www.office.com](https://www.office.com)으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="664ae-153">Go to [https://www.office.com](https://www.office.com).</span></span>
    
3. <span data-ttu-id="664ae-154">Office 365 로그인 페이지에서 **다른 계정 사용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="664ae-154">On the Office 365 sign in page, click **Use another account**.</span></span>
    
4. <span data-ttu-id="664ae-155">User 4 계정 이름 및 암호를 입력한 다음 **로그인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="664ae-155">Type the User 4 account name and its password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="664ae-156">필요한 경우 User 4 계정 암호를 변경한 다음 **암호 업데이트 및 로그인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="664ae-156">If needed, change the User 4 account password, and then click **Update password and sign in**.</span></span>
    
6. <span data-ttu-id="664ae-157">Office 365 포털 페이지에서 **관리자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="664ae-157">On the Office 365 portal page, click **Admin**.</span></span>
    
7. <span data-ttu-id="664ae-158">관리자 연락처 정보를 업데이트하라는 메시지가 표시되면 필요한 경우 **취소**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="664ae-158">If needed, click **cancel** when prompted to update your admin contact info.</span></span>
    
8. <span data-ttu-id="664ae-159">기본 포털 페이지에서 **관리자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="664ae-159">From the main portal page, click **Admin**.</span></span>
    
9. <span data-ttu-id="664ae-160">왼쪽 탐색에서 **사용자 > 활성화된 사용자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="664ae-160">In the left navigation, click **Users > Active users**.</span></span>
    
10. <span data-ttu-id="664ae-161">**User 5** 계정을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="664ae-161">Click the **User 5** account.</span></span>
    
11. <span data-ttu-id="664ae-162">**User 5** 페이지에서 **규칙** 열에 대한 **편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="664ae-162">On the **User 5** page, click **Edit** for the **Roles** row.</span></span>
    
12. <span data-ttu-id="664ae-p108">**사용자 역할 편집** 페이지에서 **사용자 지정된 관리자**를 클릭하고 **암호 관리자** 및 **사용자 관리 관리자**를 클릭한 다음 **대체 전자 메일 주소**에 **user5@contoso.com**을 입력하고 **저장**을 클릭합니다. **닫기**를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="664ae-p108">On the **Edit user roles** page, click **Customized administrator**, click **Password administrator** and **User management administrator**, type **user5@contoso.com** in the **Alternative email address**, and then click **Save**. Click **Close** twice.</span></span>
    
13. <span data-ttu-id="664ae-165">오른쪽 위에서 사용자 아이콘을 클릭한 다음 **로그아웃**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="664ae-165">Click the user icon in the upper-right, and then click **Sign out**.</span></span> 
    
14. <span data-ttu-id="664ae-166">[https://www.office.com](https://www.office.com)으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="664ae-166">Go to [https://www.office.com](https://www.office.com).</span></span>
    
15. <span data-ttu-id="664ae-167">**Office 365 로그인** 페이지에서 전역 관리자 계정 이름을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="664ae-167">On the **Office 365 sign in** page, click your global administrator account name.</span></span>
    
16. <span data-ttu-id="664ae-168">암호를 입력한 다음 **로그인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="664ae-168">Type the password, and then click **Sign in**.</span></span>
    
17. <span data-ttu-id="664ae-169">Office 365 포털 페이지에서 **관리자**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="664ae-169">From the Office 365 portal page, click **Admin**.</span></span>
    
18. <span data-ttu-id="664ae-170">**보안 &amp; 준수** 타일을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="664ae-170">Click the **Security &amp; Compliance** tile.</span></span>
    
19. <span data-ttu-id="664ae-171">왼쪽 탐색 창에서 **경고 > 고급 알림 관리**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="664ae-171">In the left navigation pane, click **Alerts > Manage advanced alerts**.</span></span>
    
20. <span data-ttu-id="664ae-172">**고급 알림 관리** 페이지에서 **Office 365 Cloud App Security로 이동을**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="664ae-172">On the **Manage advanced alerts** page, click **Go to Office 365 Cloud App Security**.</span></span>
    
21. <span data-ttu-id="664ae-173">새 **대시보드** 탭에서 **관리 활동**에 대 한 두 개의 새로운 알림을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="664ae-173">On the new **Dashboard** tab, notice the two new alerts for **Administrative activity**.</span></span>
    
22. <span data-ttu-id="664ae-174">**Microsoft Office 홈** 탭에서 **메일**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="664ae-174">From the **Microsoft Office Home** tab, click **Mail**.</span></span> <span data-ttu-id="664ae-175">최대 30분을 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="664ae-175">Wait up to 30 minutes.</span></span> 
    
    <span data-ttu-id="664ae-176">받은 편지함에 제목 **Microsoft AZURE AD 알림 서비스**와 함께 새 전자 메일 메시지가 두 개 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="664ae-176">You should see two new email messages in the inbox with the title **Microsoft Azure AD Notification Service**.</span></span> <span data-ttu-id="664ae-177">한 메시지는 사용자 5 계정을 **암호 관리자** 역할에 추가 했으며 사용자 5 계정이 **사용자 관리자** 역할에 추가 되었다는 것을 의미 합니다 (Microsoft 365 관리 센터의 사용자 관리 관리자 역할과 같음).</span><span class="sxs-lookup"><span data-stu-id="664ae-177">One message indicates that the User 5 account was added to the **Password Administrator** role and another message indicates that the User 5 account was added to the **User Administrator** role (equal to the User management administrator role in the Microsoft 365 admin center).</span></span>
    
<span data-ttu-id="664ae-178">이제이 환경을 사용 하 여 새 정책을 만들고 Office 365 Cloud App Security를 추가로 경험해 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="664ae-178">You can now use this environment to create new policies and further experiment with Office 365 Cloud App Security.</span></span> <span data-ttu-id="664ae-179">추가 구성 문서에 대 한 링크는 [Office 365 Cloud App Security 준비](https://support.office.com/article/Get-ready-for-Office-365-Cloud-App-Security-d9ee4d67-f2b3-42b4-9c9e-c4529904990a) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="664ae-179">See [Get ready for Office 365 Cloud App Security](https://support.office.com/article/Get-ready-for-Office-365-Cloud-App-Security-d9ee4d67-f2b3-42b4-9c9e-c4529904990a) for links to additional configuration articles.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="664ae-180">참고 항목</span><span class="sxs-lookup"><span data-stu-id="664ae-180">See Also</span></span>

[<span data-ttu-id="664ae-181">클라우드 도입 TLG(테스트 랩 가이드)</span><span class="sxs-lookup"><span data-stu-id="664ae-181">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="664ae-182">Office 365 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="664ae-182">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="664ae-183">클라우드 도입 및 하이브리드 솔루션</span><span class="sxs-lookup"><span data-stu-id="664ae-183">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="664ae-184">Office 365의 Cloud App Security 개요</span><span class="sxs-lookup"><span data-stu-id="664ae-184">Overview of Cloud App Security in Office 365</span></span>](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475)


