---
title: Office 365 개발/테스트 환경용 Multi-Factor Authentication
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/20/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: e2b354b9-7f18-4da0-9107-6245eae0f33f
description: '요약: Office 365 개발/테스트 환경에서 스마트 전화로 전송 되는 텍스트 메시지를 사용 하 여 다단계 인증을 구성 합니다.'
ms.openlocfilehash: 2c53d7fa9239395e28d68487dd0ccea8cc57efb7
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069954"
---
# <a name="multi-factor-authentication-for-your-office-365-devtest-environment"></a><span data-ttu-id="10696-103">Office 365 개발/테스트 환경용 Multi-Factor Authentication</span><span class="sxs-lookup"><span data-stu-id="10696-103">Multi-factor authentication for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="10696-104">**요약:** Office 365 개발/테스트 환경의 스마트 전화로 전송 되는 텍스트 메시지를 사용 하 여 다단계 인증을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="10696-104">**Summary:** Configure multi-factor authentication using text messages sent to a smart phone in an Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="10696-105">Office 365 구독에 로그인 하는 데 필요한 추가 보안 수준을 설정 하려면 계정을 인증 하기 위해 사용자 이름 및 암호를 초과 해야 하는 Azure multi-factor authentication을 사용 하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10696-105">For an additional level of security for signing in to your Office 365 subscription, you can enable Azure multi-factor authentication, which requires more than just a username and password to authenticate an account.</span></span> <span data-ttu-id="10696-106">Office 365에 대 한 다단계 인증을 사용 하는 경우 사용자는 전화 통화를 승인 하거나, 문자 메시지로 보낸 확인 코드를 입력 하거나, 암호를 올바르게 입력 한 후 스마트 전화에서 앱 암호를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="10696-106">With multi-factor authentication for Office 365, users are required to acknowledge a phone call, type a verification code sent in a text message, or specify an app password on their smart phones after correctly entering their passwords.</span></span> <span data-ttu-id="10696-107">사용자는 이 두 번째 인증 요소를 충족해야 로그인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10696-107">They can sign in only after this second authentication factor has been satisfied.</span></span> 
  
<span data-ttu-id="10696-108">이 문서에서는 특정 Office 365 계정에 대해 텍스트 메시지 기반 인증을 사용 하 고 테스트 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="10696-108">This article describes how to enable and test text message-based authentication for a specific Office 365 account.</span></span>
  
<span data-ttu-id="10696-109">개발/테스트 환경에서 Office 365에 대 한 다단계 인증을 설정 하는 단계는 다음 두 단계로 진행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10696-109">There are two phases to setting up multi-factor authentication for Office 365 in a dev/test environment:</span></span>
  
1. <span data-ttu-id="10696-110">Office 365 개발/테스트 환경을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="10696-110">Create the Office 365 dev/test environment.</span></span>
    
2. <span data-ttu-id="10696-111">사용자 2 계정에 대해 multi-factor authentication을 사용 하도록 설정 하 고 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="10696-111">Enable and test multi-factor authentication for the User 2 account.</span></span>
    
> [!TIP]
> <span data-ttu-id="10696-112">[여기](http://aka.ms/catlgstack)를 클릭하여 Office 365 테스트 랩 가이드 스택의 모든 문서에 대한 가상 맵을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10696-112">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the Office 365 Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="10696-113">1단계: 경량 또는 시뮬레이트된 엔터프라이즈 Office 365 개발/테스트 환경을 구축합니다.</span><span class="sxs-lookup"><span data-stu-id="10696-113">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="10696-114">최소 요구 사항을 사용 하 여 경량 방식으로 multi-factor authentication을 테스트 하려는 경우에는 [Office 365 개발/테스트 환경의](office-365-dev-test-environment.md)2 단계 및 3 단계의 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="10696-114">If you just want to test multi-factor authentication in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="10696-115">시뮬레이트된 엔터프라이즈에서 다단계 인증을 테스트 하려는 경우에는 [Office 365 개발/테스트 환경에 대 한 DirSync](dirsync-for-your-office-365-dev-test-environment.md)의 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="10696-115">If you want to test multi-factor authentication in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="10696-116">다단계 인증을 테스트 하는 경우에는 AD DS (Active Directory 도메인 서비스) 포리스트의 인터넷 및 디렉터리 동기화에 연결 된 시뮬레이트된 인트라넷을 포함 하는 시뮬레이트된 엔터프라이즈 개발/테스트 환경이 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="10696-116">Testing multi-factor authentication does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Active Directory Domain Services (AD DS) forest.</span></span> <span data-ttu-id="10696-117">다단계 인증을 테스트 하 고 일반적인 조직을 나타내는 환경에서 테스트할 수 있도록 옵션으로 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10696-117">It is provided here as an option so that you can test multi-factor authentication and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account"></a><span data-ttu-id="10696-118">2 단계: 사용자 2 계정에 대해 multi-factor authentication 사용 및 테스트</span><span class="sxs-lookup"><span data-stu-id="10696-118">Phase 2: Enable and test multi-factor authentication for the User 2 account</span></span>

<span data-ttu-id="10696-119">사용자 2 계정에 대해 다단계 인증을 사용 하도록 설정 하려면 다음 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="10696-119">Enable multi-factor authentication for the User 2 account with these steps:</span></span>
  
1. <span data-ttu-id="10696-120">별도의 브라우저 인스턴스를 열고 Office 365 portal ([https://www.office.com](https://www.office.com))로 이동한 다음 전역 관리자 계정을 사용 하 여 office 365 평가판 구독에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="10696-120">Open a separate instance of your browser, go to the Office 365 portal ([https://www.office.com](https://www.office.com)), and then sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
2. <span data-ttu-id="10696-121">기본 포털 페이지에서 **관리자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="10696-121">From the main portal page, click **Admin**.</span></span>
    
3. <span data-ttu-id="10696-122">왼쪽 탐색에서 **사용자 > 활성화된 사용자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="10696-122">In the left navigation, click **Users > Active users**.</span></span>
    
4. <span data-ttu-id="10696-123">활성 사용자 창에서 **더 _GT_ 다단계 인증 설정을**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="10696-123">In the Active users pane, click **More > Multi-factor authentication setup**.</span></span>
    
5. <span data-ttu-id="10696-124">목록에서 **사용자 2** 계정을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="10696-124">In the list, select the **User 2** account.</span></span>
    
6. <span data-ttu-id="10696-125">**사용자 2** 섹션의 **빠른 단계**에서 **사용**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="10696-125">In the **User 2** section, under **Quick steps**, click **Enable**.</span></span>
    
7. <span data-ttu-id="10696-126">**다단계 인증 사용** 대화 상자에서 **다단계 인증 사용**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="10696-126">In the **About enabling multi-factor auth** dialog box, click **Enable multi-factor auth**.</span></span>
    
8. <span data-ttu-id="10696-127">**업데이트 완료** 대화 상자에서 **닫기를**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="10696-127">In the **Updates successful** dialog box, click **Close**.</span></span>
    
9. <span data-ttu-id="10696-128">**Microsoft Office 홈** 탭의 오른쪽 위에 있는 사용자 계정 아이콘을 클릭 한 다음 **로그 아웃**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="10696-128">On the **Microsoft Office Home** tab, click the user account icon in the upper right, and then click **Sign out**.</span></span>
    
10. <span data-ttu-id="10696-129">브라우저 인스턴스를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="10696-129">Close your browser instance.</span></span>
    
<span data-ttu-id="10696-130">사용자 2 계정에 대 한 구성을 완료 하 여 유효성 검사에 텍스트 메시지를 사용 하 고 다음 단계를 사용 하 여 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="10696-130">Complete the configuration for the User 2 account to use a text message for validation and test it with these steps:</span></span>
  
1. <span data-ttu-id="10696-131">브라우저의 새 인스턴스를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="10696-131">Open a new instance of your browser.</span></span>
    
2. <span data-ttu-id="10696-132">Office 365 portal ([https://www.office.com](https://www.office.com))로 이동 하 여 사용자 2 계정 (name> @\<조 직, .com) 및 암호를 사용 하 여 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="10696-132">Go to the Office 365 portal ([https://www.office.com](https://www.office.com)) and sign in with the User 2 account (user2@\<organization name>.onmicrosoft.com) and password.</span></span>
    
3. <span data-ttu-id="10696-133">로그인 한 후에는 추가 보안 유효성 검사를 위해 계정을 설정 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10696-133">After signing in, you are prompted to set up the account for additional security validation.</span></span> <span data-ttu-id="10696-134">**지금 설정**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="10696-134">Click **Set it up now**.</span></span>
    
4. <span data-ttu-id="10696-135">**추가 보안 확인** 페이지에서 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="10696-135">On the **Additional security verification** page:</span></span>
    
  - <span data-ttu-id="10696-136">국가 또는 지역을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="10696-136">Select your country or region.</span></span>
    
  - <span data-ttu-id="10696-137">텍스트 메시지를 받을 스마트 폰의 전화 번호를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="10696-137">Type phone number of the smart phone that will receive text messages.</span></span>
    
  - <span data-ttu-id="10696-138">**방법**에서 **문자 메시지로 코드 보내기를**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="10696-138">in **Method**, click **Send me a code by text message**.</span></span>
    
5. <span data-ttu-id="10696-139">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="10696-139">Click **Next**.</span></span>
    
6. <span data-ttu-id="10696-140">스마트 폰에서 받은 문자 메시지의 확인 코드를 입력 하 고 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="10696-140">Enter the verification code from the text message received on your smart phone, and then click **Verify**.</span></span>
    
7. <span data-ttu-id="10696-141">**3 단계: 기존 응용 프로그램 유지** 페이지에서 사용자 2 계정에 대해 표시 된 앱 암호를 안전한 위치에 기록 하 고 **완료**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="10696-141">On the **Step 3: Keep your existing applications** page, record the displayed app password for the User 2 account in a secure location, and then click **Done**.</span></span>
    
8. <span data-ttu-id="10696-142">사용자 2 계정으로 처음 로그인 하는 경우 암호를 변경 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10696-142">If this is the first time you signed in with the User 2 account, you are prompted to change the password.</span></span> <span data-ttu-id="10696-143">원래 암호와 새 암호를 두 번 입력 한 다음 **암호 업데이트 및 로그인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="10696-143">Type the original password and a new password twice, and then click **Update password and sign in**.</span></span> <span data-ttu-id="10696-144">새 암호를 안전한 위치에 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="10696-144">Record the new password in a secure location.</span></span>
    
    <span data-ttu-id="10696-145">브라우저의 **Microsoft Office 홈** 탭에 사용자 2에 대 한 Office 365 포털이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10696-145">You should see the Office 365 portal for User 2 on the **Microsoft Office Home** tab of your browser.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="10696-146">참고 항목</span><span class="sxs-lookup"><span data-stu-id="10696-146">See Also</span></span>

[<span data-ttu-id="10696-147">클라우드 도입 TLG(테스트 랩 가이드)</span><span class="sxs-lookup"><span data-stu-id="10696-147">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="10696-148">기본 구성 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="10696-148">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="10696-149">Office 365 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="10696-149">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="10696-150">클라우드 도입 및 하이브리드 솔루션</span><span class="sxs-lookup"><span data-stu-id="10696-150">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="10696-151">Office 365 배포에 대 한 다단계 인증 계획</span><span class="sxs-lookup"><span data-stu-id="10696-151">Plan for multi-factor authentication for Office 365 Deployments</span></span>](https://support.office.com/article/Plan-for-multi-factor-authentication-for-Office-365-Deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)

