---
title: Office 365 개발/테스트 환경용 다단계 인증
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/22/2018
ms.audience: ITPro
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
description: '요약: Office 365 개발/테스트 환경에서 스마트폰으로 전송 하는 텍스트 메시지를 사용 하 여 다단계 인증을 구성 합니다.'
ms.openlocfilehash: 6e2aefa9309e7e268c937055f7fe59600f8c87da
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897451"
---
# <a name="multi-factor-authentication-for-your-office-365-devtest-environment"></a><span data-ttu-id="68a5a-103">Office 365 개발/테스트 환경용 다단계 인증</span><span class="sxs-lookup"><span data-stu-id="68a5a-103">Multi-factor authentication for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="68a5a-104">**요약:** Office 365 개발/테스트 환경에서 스마트폰으로 전송 하는 텍스트 메시지를 사용 하 여 다단계 인증을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="68a5a-104">**Summary:** Configure multi-factor authentication using text messages sent to a smart phone in an Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="68a5a-p101">추가 된 Office 365 구독에 로그인 하는 것에 대 한 보안 수준을 대 한 사용자 이름 및 계정 인증 암호 단순한 필요로 하는 Azure 다단계 인증을 사용할 수 있습니다. Office 365에 대 한 다단계 인증을 사용 하면 사용자가 전화 통화, 텍스트 메시지를 열고 전송 확인 코드를 입력 하거나 올바르게 자신의 암호를 입력 한 후 스마트 전화 앱 암호를 지정 해야 합니다. 이 두번째 인증 요소를 충족 된 후에에 로그인 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68a5a-p101">For an additional level of security for signing in to your Office 365 subscription, you can enable Azure multi-factor authentication, which requires more than just a username and password to authenticate an account. With multi-factor authentication for Office 365, users are required to acknowledge a phone call, type a verification code sent in a text message, or specify an app password on their smart phones after correctly entering their passwords. They can sign in only after this second authentication factor has been satisfied.</span></span> 
  
<span data-ttu-id="68a5a-108">이 문서에서는 설정 하 고 특정 Office 365 계정에 대 한 텍스트 메시지 기반 인증을 테스트 하는 방법에 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="68a5a-108">This article describes how to enable and test text message-based authentication for a specific Office 365 account.</span></span>
  
<span data-ttu-id="68a5a-109">개발/테스트 환경에서 Office 365에 대 한 다단계 인증을 설정 하는 두 단계로 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68a5a-109">There are two phases to setting up multi-factor authentication for Office 365 in a dev/test environment:</span></span>
  
1. <span data-ttu-id="68a5a-110">Office 365 개발/테스트 환경을 만듭니다.
</span><span class="sxs-lookup"><span data-stu-id="68a5a-110">Create the Office 365 dev/test environment.</span></span>
    
2. <span data-ttu-id="68a5a-111">사용 하도록 설정 하 고 사용자 2 계정에 대 한 다단계 인증을 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="68a5a-111">Enable and test multi-factor authentication for the User 2 account.</span></span>
    
> [!TIP]
> <span data-ttu-id="68a5a-112">[여기](http://aka.ms/catlgstack)를 클릭하여 One Microsoft 클라우드 테스트 랩 가이드 스택의 모든 문서에 대한 가상 맵을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68a5a-112">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="68a5a-113">1단계: 경량 또는 시뮬레이트된 엔터프라이즈 Office 365 개발/테스트 환경을 구축합니다.</span><span class="sxs-lookup"><span data-stu-id="68a5a-113">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="68a5a-114">최소 요구 사항을 경량 방식으로 다단계 인증을 테스트 하려면 2와 [Office 365 개발/테스트 환경](office-365-dev-test-environment.md)의 3 단계에서 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="68a5a-114">If you just want to test multi-factor authentication in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="68a5a-115">시뮬레이션 된 엔터프라이즈에서 다단계 인증을 테스트 하려는 경우 [Office 365 개발/테스트 환경에 대 한 디렉터리 동기화](dirsync-for-your-office-365-dev-test-environment.md)의 지시를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="68a5a-115">If you want to test multi-factor authentication in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="68a5a-p102">다단계 인증을 테스트 하지 않아도 인터넷에 연결 하는 시뮬레이션 된 인트라넷을 포함 하는 시뮬레이션 된 엔터프라이즈 개발/테스트 환경 및 Windows Server AD 포리스트에 대 한 디렉터리 동기화 합니다. 제공은 다단계 인증을 테스트 하 고 일반적인 조직을 대표 하는 환경에서 사용해 수 있도록 하는 옵션으로 여기 합니다.</span><span class="sxs-lookup"><span data-stu-id="68a5a-p102">Testing multi-factor authentication does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can test multi-factor authentication and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account"></a><span data-ttu-id="68a5a-118">2 단계: 사용 하도록 설정 하 고 사용자 2 계정에 대 한 다단계 인증 테스트</span><span class="sxs-lookup"><span data-stu-id="68a5a-118">Phase 2: Enable and test multi-factor authentication for the User 2 account</span></span>

<span data-ttu-id="68a5a-119">다음이 단계를 사용 하 여 사용자 2 계정에 대 한 다단계 인증을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="68a5a-119">Enable multi-factor authentication for the User 2 account with these steps:</span></span>
  
1. <span data-ttu-id="68a5a-120">브라우저의 별도 인스턴스를 열고, Office 365 포털에 이동 ([https://portal.office.com](https://portal.office.com)), 다음 전역 관리자 계정 사용 하 여 Office 365 평가판 구독에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="68a5a-120">Open a separate instance of your browser, go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)), and then sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
2. <span data-ttu-id="68a5a-121">기본 포털 페이지에서 **관리자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68a5a-121">From the main portal page, click **Admin**.</span></span>
    
3. <span data-ttu-id="68a5a-122">왼쪽 탐색에서 **사용자 > 활성화된 사용자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68a5a-122">In the left navigation, click **Users > Active users**.</span></span>
    
4. <span data-ttu-id="68a5a-123">현재 사용자가 창에서 **더 많은 gt_ 설치 Azure 다단계 인증**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="68a5a-123">In the Active users pane, click **More > Setup Azure multi-factor auth**.</span></span>
    
5. <span data-ttu-id="68a5a-124">목록에서 **사용자 2** 계정을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="68a5a-124">In the list, select the **User 2** account.</span></span>
    
6. <span data-ttu-id="68a5a-125">**사용자 2** 섹션에서 **빠른 단계** **사용**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="68a5a-125">In the **User 2** section, under **Quick steps**, click **Enable**.</span></span>
    
7. <span data-ttu-id="68a5a-126">**다단계 인증을 사용 하도록 설정 하는 방법에 대 한** 대화 상자에서 **다단계 인증 사용**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="68a5a-126">In the **About enabling multi-factor auth** dialog box, click **Enable multi-factor auth**.</span></span>
    
8. <span data-ttu-id="68a5a-127">**업데이트 성공** 대화 상자에서 **닫기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="68a5a-127">In the **Update successful** dialog box, click **Close**.</span></span>
    
9. <span data-ttu-id="68a5a-128">**Microsoft Office 홈** 탭의 오른쪽 위에 있는 사용자 계정 아이콘을 클릭 하 고 **로그 아웃**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="68a5a-128">On the **Microsoft Office Home** tab, click the user account icon in the upper right, and then click **Sign out**.</span></span>
    
10. <span data-ttu-id="68a5a-129">브라우저 인스턴스를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="68a5a-129">Close your browser instance.</span></span>
    
<span data-ttu-id="68a5a-130">유효성 검사에 대 한 텍스트 메시지를 사용 하 고 이러한 단계를 테스트 하는 사용자 2 계정에 대 한 구성을 완료 합니다.</span><span class="sxs-lookup"><span data-stu-id="68a5a-130">Complete the configuration for the User 2 account to use a text message for validation and test it with these steps:</span></span>
  
1. <span data-ttu-id="68a5a-131">브라우저의 새 인스턴스를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="68a5a-131">Open a new instance of your browser.</span></span>
    
2. <span data-ttu-id="68a5a-132">Office 365 포털에 이동 ([https://portal.office.com](https://portal.office.com))와 사용자 2 계정 사용 하 여 로그인 (@ user2\<조직 name>.onmicrosoft.com) 및 암호입니다.</span><span class="sxs-lookup"><span data-stu-id="68a5a-132">Go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) and sign in with the User 2 account (user2@\<organization name>.onmicrosoft.com) and password.</span></span>
    
3. <span data-ttu-id="68a5a-p103">로그인 한 후 추가 보안 유효성 검사에 대 한 계정을 설정 하 라는 메시지가 표시 됩니다. **지금 설정**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="68a5a-p103">After signing in, you are prompted to set up the account for additional security validation. Click **Set it up now**.</span></span>
    
4. <span data-ttu-id="68a5a-135">**추가 보안 확인** 페이지 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="68a5a-135">On the **Additional security verification** page:</span></span>
    
  - <span data-ttu-id="68a5a-136">국가 또는 지역을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="68a5a-136">Select your country or region.</span></span>
    
  - <span data-ttu-id="68a5a-137">텍스트 메시지를 받을 스마트 전화의 전화번호를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="68a5a-137">Type phone number of the smart phone that will receive text messages.</span></span>
    
  - <span data-ttu-id="68a5a-138">**메서드**를 **보내기 나에 게 텍스트 메시지를 여는 코드를**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="68a5a-138">in **Method**, click **Send me a code by text message**.</span></span>
    
5. <span data-ttu-id="68a5a-139">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68a5a-139">Click **Next**.</span></span>
    
6. <span data-ttu-id="68a5a-140">스마트 전화기에서 받은 텍스트 메시지에서 확인 코드를 입력 한 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="68a5a-140">Enter the verification code from the text message received on your smart phone, and then click **Verify**.</span></span>
    
7. <span data-ttu-id="68a5a-141">**3 단계: 기존 응용 프로그램을 유지** 페이지를 안전한 위치에 2 사용자 계정에 대 한 표시 된 앱 암호를 기록 하 고 다음 **완료**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="68a5a-141">On the **Step 3: Keep your existing applications** page, record the displayed app password for the User 2 account in a secure location, and then click **Done**.</span></span>
    
8. <span data-ttu-id="68a5a-p104">이것은 처음으로 하는 경우 귀하가 사용자 2 계정을 사용 하 여 메시지가 표시 되는 암호를 변경 해야 합니다. 원래 암호와 새 암호를을 두번 입력 하 고 **암호를 업데이트 하 고 로그인**을 클릭 합니다. 안전한 위치에 새 암호를 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="68a5a-p104">If this is the first time you signed in with the User 2 account, you are prompted to change the password. Type the original password and a new password twice, and then click **Update password and sign in**. Record the new password in a secure location.</span></span>
    
    <span data-ttu-id="68a5a-145">브라우저의 **Microsoft Office Home** 탭에는 Office 365 포털 사용자 2에 대 한 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="68a5a-145">You should see the Office 365 portal for User 2 on the **Microsoft Office Home** tab of your browser.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="68a5a-146">참고 항목</span><span class="sxs-lookup"><span data-stu-id="68a5a-146">See Also</span></span>

[<span data-ttu-id="68a5a-147">클라우드 도입 TLG(테스트 랩 가이드)</span><span class="sxs-lookup"><span data-stu-id="68a5a-147">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="68a5a-148">기본 구성 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="68a5a-148">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="68a5a-149">Office 365 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="68a5a-149">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="68a5a-150">클라우드 도입 및 하이브리드 솔루션</span><span class="sxs-lookup"><span data-stu-id="68a5a-150">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="68a5a-151">Office 365 배포의 다단계 인증 계획</span><span class="sxs-lookup"><span data-stu-id="68a5a-151">Plan for multi-factor authentication for Office 365 Deployments</span></span>](https://support.office.com/article/Plan-for-multi-factor-authentication-for-Office-365-Deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)

