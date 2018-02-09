---
title: "IOS 및 Microsoft 기업 365 개발/테스트 환경에서 Android 장치 등록"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: "요약:이 테스트 랩 가이드를 사용 하 여 Microsoft 365 개발/테스트 환경에서 장치를 등록 하 고 원격으로 관리 하기를."
ms.openlocfilehash: 77b5074b083656fdfa2cd460510231dae0689d10
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/09/2018
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-devtest-environment"></a><span data-ttu-id="9b2b7-103">IOS 및 Microsoft 기업 365 개발/테스트 환경에서 Android 장치 등록</span><span class="sxs-lookup"><span data-stu-id="9b2b7-103">Enroll iOS and Android devices in your Microsoft Enterprise 365 dev/test environment</span></span>

 <span data-ttu-id="9b2b7-104">**요약:** 이 테스트 랩 가이드를 Microsoft 365 개발/테스트 환경에서 장치를 등록 하 고 원격으로 관리 하기를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-104">**Summary:** Use this Test Lab Guide to enroll devices in your Microsoft 365 dev/test environment and manage them remotely.</span></span>
  
<span data-ttu-id="9b2b7-p101">Microsoft Enterprise 이동성 제품군 (EMS) 직원에 게 조직의 데이터를 보호 하는 동안 자신의 좋아하는 앱 및 장치를 사용 하 여 생산성을 유지 도움이 됩니다. 자세한 내용은 [엔터프라이즈 이동성 + 보안 (EMS)를](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-p101">The Microsoft Enterprise Mobility Suite (EMS) helps keep your employees productive using their favorite apps and devices while protecting your organization's data. For more information, see [Enterprise Mobility + Security (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span></span>
  
<span data-ttu-id="9b2b7-p102">장치 수준에서 보안을 적용해야 하면 Microsoft Intune에 장치를 등록해야 합니다. 장치 등록은 조직의 법적 정책을 기준으로 회사 소유 장치와 개인(BYOD) 및 공유 장치를 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-p102">If you need to apply security at the device level, you must enroll devices into Microsoft Intune. Device enrollment not only helps you to manage corporate-owned devices, but also personal (BYOD) and shared devices, depending on your organization's legal policies.</span></span>
  
<span data-ttu-id="9b2b7-109">이 문서에서 제공 하는 지침을 따르면를 등록 하 고 Microsoft 365 개발/테스트 환경에서 iOS 및 Android 장치에 대 한 기본 모바일 장치 관리 기능을 테스트 하는 작업을 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-109">By following the instructions provided in this article, you'll be able to enroll and test basic mobile device management capabilities for iOS and Android devices in your Microsoft 365 dev/test environment.</span></span>
  
## <a name="phase-1-create-your-microsoft-365-devtest-environment"></a><span data-ttu-id="9b2b7-110">1 단계: Microsoft 365 개발/테스트 환경 만들기</span><span class="sxs-lookup"><span data-stu-id="9b2b7-110">Phase 1: Create your Microsoft 365 dev/test environment</span></span>

<span data-ttu-id="9b2b7-111">[개발/테스트 환경에서 Microsoft 365 Enterprise의](the-microsoft-365-enterprise-dev-test-environment.md)에서 지시를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-111">Follow the instructions in [The Microsoft 365 Enterprise dev/test environment](the-microsoft-365-enterprise-dev-test-environment.md).</span></span>
  
## <a name="phase-2-customize-the-microsoft-intune-company-portal-app"></a><span data-ttu-id="9b2b7-112">2단계: Microsoft Intune 회사 포털 앱 사용자 지정</span><span class="sxs-lookup"><span data-stu-id="9b2b7-112">Phase 2: Customize the Microsoft Intune Company Portal app</span></span>

<span data-ttu-id="9b2b7-113">이러한 단계를 사용하여 가상 회사의 Microsoft Intune 회사 포털 앱을 사용자 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-113">Use these steps to customize the Microsoft Intune Company Portal app for your fictional company:</span></span>
  
1. <span data-ttu-id="9b2b7-114">새 탭에 있는 Microsoft Intune 관리 콘솔 ([https://manage.microsoft.com](https://manage.microsoft.com))을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-114">On a new tab, open the Microsoft Intune administration console ([https://manage.microsoft.com](https://manage.microsoft.com)).</span></span>
    
2. <span data-ttu-id="9b2b7-115">탐색 창의 **관리** 를 클릭 하 고 **관리** 창에서 **모바일 장치 관리** 를 차례로 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-115">Click **Admin** in the navigation pane, and then click **Mobile Device Management** in the **Administration** pane.</span></span>
    
3. <span data-ttu-id="9b2b7-p103">**작업** 목록에서 **모바일 장치 관리 기관 설정**을 선택 합니다. **Microsoft Intune**로 설정 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-p103">In the **Tasks** list, select **Set Mobile Device Management Authority**. Ensure that it is set to **Microsoft Intune**.</span></span>
    
4. <span data-ttu-id="9b2b7-118">**관리** 창에서 **회사 포털**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-118">In the **Administration** pane, click **Company Portal**.</span></span>
    
5. <span data-ttu-id="9b2b7-119">**회사 포털** 창에서 다음 설정을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-119">In the **Company Portal** pane, configure the following settings:</span></span>
    
  - <span data-ttu-id="9b2b7-120">회사 이름: \<가상의 회사 이름 ></span><span class="sxs-lookup"><span data-stu-id="9b2b7-120">Company name: \<your fictional company name></span></span>
    
  - <span data-ttu-id="9b2b7-121">IT 부서에 대 한 대화 상대 이름: **User5**</span><span class="sxs-lookup"><span data-stu-id="9b2b7-121">IT department contact name: **User5**</span></span>
    
  - <span data-ttu-id="9b2b7-122">IT 부서 전화번호: **555-1234**</span><span class="sxs-lookup"><span data-stu-id="9b2b7-122">IT department phone number: **555-1234**</span></span>
    
  - <span data-ttu-id="9b2b7-123">IT 부서 전자 메일 주소: **@ User5**\<가상의 조직 이름 > **. onmicrosoft.com** (User5 계정의 전자 메일 주소)</span><span class="sxs-lookup"><span data-stu-id="9b2b7-123">IT department e-mail address: **User5@**\<fictional organization name> **.onmicrosoft.com** (the email address of the User5 account)</span></span>
    
6. <span data-ttu-id="9b2b7-124">**사용자 지정** **테마 색**에서 **녹색** 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-124">In **Customization**, select **Green** in **Theme color**.</span></span>
    
7. <span data-ttu-id="9b2b7-125">**저장**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-125">Click **Save**.</span></span>
    
<span data-ttu-id="9b2b7-126">다음으로 Microsoft Intune 회사 포털 앱을 설치하고 iOS 또는 Android 장치를 등록한 다음 Microsoft Intune 관리 콘솔에서 기본 관리 기능을 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-126">Next, you will install the Microsoft Intune Company Portal app and enroll an iOS or Android device, and then test basic management functionality from the Microsoft Intune administration console.</span></span>
  
## <a name="phase-3-for-ios-devices-only-enroll-and-manage-an-ios-device"></a><span data-ttu-id="9b2b7-127">3단계(iOS 장치만 해당): iOS 장치 등록 및 관리</span><span class="sxs-lookup"><span data-stu-id="9b2b7-127">Phase 3 (for iOS devices only): Enroll and manage an iOS device</span></span>

<span data-ttu-id="9b2b7-128">Intune에서 관리할 iOS 장치를 등록하려면 다음 항목이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-128">To enroll an iOS device for management by Intune, you will need the following:</span></span>
  
- <span data-ttu-id="9b2b7-129">Apple iPad 또는 iPhone과 같은 iOS 장치.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-129">An iOS device such as an Apple iPad or iPhone.</span></span>
    
- <span data-ttu-id="9b2b7-130">IOS 장치 암호에 대 한 지식입니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-130">Knowledge of the iOS device's passcode.</span></span>
    
- <span data-ttu-id="9b2b7-p104">Apple ID (계정 이름 및 암호). 수행 하지 이미 있는 경우, [Apple ID 웹사이트](https://appleid.apple.com/#!&amp;page=signin) 로 이동 하 고 **Apple ID 만들기**를 클릭 합니다. Office 365 구독의 전역 관리자 계정에 대응 하는 Apple ID를 만듭니다. 안전한 위치에 새 Apple ID 계정 이름 및 암호를 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-p104">An Apple ID (an account name and password). If you do not already have one, go to the [Apple ID website](https://appleid.apple.com/#!&amp;page=signin) and click **Create your Apple ID**. Create an Apple ID corresponding to the global administrator account of your Office 365 subscription. Record your new Apple ID account name and password in a secure location.</span></span>
    
<span data-ttu-id="9b2b7-p105">Intune에서 iOS 및 Mac 장치를 관리하려면 APN(Apple Push Notification service) 인증서가 있어야 합니다. Intune에 인증서가 추가되면 사용자가 Microsoft Intune 회사 포털 앱을 설치하여 장치를 등록하거나 관리자가 회사 소유 iOS 장치 관리를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-p105">An Apple Push Notification service (APNs) certificate is required for Intune to manage iOS and Mac devices. Once the certificate is added to Intune, users can install the Microsoft Intune Company Portal app to enroll their devices or the administrator can set up corporate-owned iOS device management.</span></span>
  
<span data-ttu-id="9b2b7-p106">Apple Push Certificates 포털에서 트러스트 관계 인증서를 요청하려면 인증서 서명 요청 파일이 있어야 합니다. 인증서 서명 요청 파일을 가져오려면:</span><span class="sxs-lookup"><span data-stu-id="9b2b7-p106">You need a certificate signing request file to request a trust relationship certificate from the Apple Push Certificates Portal. To get a certificate signing request file:</span></span>
  
1. <span data-ttu-id="9b2b7-139">Microsoft Intune 관리 콘솔에서 탐색 창에서 **관리** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-139">In the Microsoft Intune administration console, click **Admin** in the navigation pane.</span></span>
    
    <span data-ttu-id="9b2b7-140">**관리** 창에서 엽니다 **모바일 장치 관리 > iOS 및 Mac OS X**, 다음 **작업**에 **한 apn을 사용할 인증서를 업로드** 를 클릭 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-140">In the **Administration** pane, open **Mobile Device Management > iOS and Mac OS X**, and then click **Upload an APNs Certificate** in **Tasks**.</span></span> 
    
2. <span data-ttu-id="9b2b7-p107">**한 apn을 사용할 인증서를 업로드** 창에서 **다운로드 한 apn을 사용할 인증서 요청을**클릭 합니다. 이름 **개발자 테스트**를 사용 하 여 로컬로 요청 (.csr) 파일에 서명 인증서를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-p107">In the **Upload an APNs Certificate** pane, click **Download the APNs certificate request**. Save the certificate signing request (.csr) file locally with the name **dev-test**.</span></span>
    
<span data-ttu-id="9b2b7-143">Apple Push Notification Service 인증서를 가져오려면:</span><span class="sxs-lookup"><span data-stu-id="9b2b7-143">To get an Apple Push Notification service certificate:</span></span>
  
1. <span data-ttu-id="9b2b7-144">새 탭 열기 [Apple 푸시 인증서 포털](https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=3fbfc9ad8dfedeb78be1d37f6458e72adc3160d1ad5b323a9e5c5eb2f8e7e3e2&amp;rv=2)이동 하 고가 프로그램 Apple ID로 로그인</span><span class="sxs-lookup"><span data-stu-id="9b2b7-144">Open a new tab, go to the [Apple Push Certificates Portal](https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=3fbfc9ad8dfedeb78be1d37f6458e72adc3160d1ad5b323a9e5c5eb2f8e7e3e2&amp;rv=2), and sign in with your Apple ID.</span></span>
    
2. <span data-ttu-id="9b2b7-145">**시작** 페이지에서 **인증서 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-145">On the **Get Started** page, click **Create a Certificate**.</span></span>
    
3. <span data-ttu-id="9b2b7-146">**사용 약관** 페이지에서 **읽어야 하는 이러한 조건 및 조건에 동의**선택 하 고 **수락**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-146">On the **Terms of Use** page, select **I have read and agree to these terms and conditions**, and then click **Accept**.</span></span>
    
4. <span data-ttu-id="9b2b7-p108">**새 푸시 인증서 만들기** 페이지에서 이전 절차에서 저장 한 **개발 test.csr** 파일 **찾아보기** 를 클릭 선택한 다음 **업로드**를 클릭 합니다. Json 파일을 열려면 대화 상자가 나타나면 개발 test.csr 파일이 저장 된 동일한 폴더에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-p108">On the **Create a New Push Certificate** page, click **Browse** and select the **dev-test.csr** file saved in the previous procedure, and then click **Upload**. When prompted to open a json file, save it to the same folder where the dev-test.csr file is stored.</span></span>
    
5. <span data-ttu-id="9b2b7-149">Open [Apple 푸시 인증서 포털](https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=3fbfc9ad8dfedeb78be1d37f6458e72adc3160d1ad5b323a9e5c5eb2f8e7e3e2&amp;rv=2) 다른 탭에 있는 및 **타사 서버에 대 한 인증서**대 한 **다운로드**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-149">Open the [Apple Push Certificates Portal](https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=3fbfc9ad8dfedeb78be1d37f6458e72adc3160d1ad5b323a9e5c5eb2f8e7e3e2&amp;rv=2) in a different tab and for **Certificates for Third-Party Servers**, click **Download**.</span></span>
    
6. <span data-ttu-id="9b2b7-p109">.Pem 파일을 열려면 대화 상자가 나타나면 이름 **개발 test.pem** 개발 test.csr 파일이 저장 된 동일한 폴더에 함께 저장 합니다. 한 apn을 사용할 인증서입니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-p109">When prompted to open a .pem file, save it with the name **dev-test.pem** to the same folder where the dev-test.csr file is stored. This is your APNs certificate.</span></span>
    
<span data-ttu-id="9b2b7-152">APN 인증서를 Intune에 업로드하려면:</span><span class="sxs-lookup"><span data-stu-id="9b2b7-152">To upload the APNs certificate into Intune:</span></span>
  
1. <span data-ttu-id="9b2b7-153">Microsoft Intune 관리 콘솔 탭 **한 apn을 사용할 인증서를 업로드** 페이지에 **업로드 한 apn을 사용할 인증서를**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-153">On the Microsoft Intune administration console tab, on the **Upload an APNs Certificate** page, click **Upload the APNs certificate**.</span></span>
    
2. <span data-ttu-id="9b2b7-154">**찾아보기** 를 클릭 하 고 **개발 test.pem** 파일을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-154">Click **Browse** and specify the **dev-test.pem** file.</span></span>
    
3. <span data-ttu-id="9b2b7-p110">**열기**를 클릭 하 고 Apple ID 계정 이름을 입력 한 다음 **업로드**를 클릭 합니다. **IOS 및 MaxOS X 모바일 장치 관리 설정** 페이지에서 **등록에 대 한 준비가 된** 메시지를 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-p110">Click **Open**, type your Apple ID account name, and then click **Upload**. You should see a **Ready for enrollment** message on the **iOS and MaxOS X Mobile Device Management Setup** page.</span></span>
    
<span data-ttu-id="9b2b7-157">이제 설치된 APN 인증서를 통해 Intune에서 등록된 모바일 장치에 정책을 푸시하여 iOS 장치를 등록하고 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-157">With the APNs certificate installed, Intune can now enroll and manage iOS devices by pushing policy to enrolled mobile devices.</span></span>
  
<span data-ttu-id="9b2b7-158">Microsoft Intune 회사 포털 앱을 다운로드하고 iOS 장치를 등록하려면:</span><span class="sxs-lookup"><span data-stu-id="9b2b7-158">To download the Microsoft Intune Company portal app and enroll the iOS device:</span></span>
  
1. <span data-ttu-id="9b2b7-159">iOS 장치에서 Apple ID로 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-159">From your iOS device, sign in with your Apple ID.</span></span>
    
2. <span data-ttu-id="9b2b7-160">**Apple 스토어** 앱을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-160">Open the **Apple Store** app.</span></span>
    
3. <span data-ttu-id="9b2b7-161">검색 상자에 **intune** 를 입력 하 고 **Microsoft Intune 회사 포털**을 한 다음 **가져오기**, 하 고 **설치**를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-161">Type **intune** in the search box and tap **Microsoft Intune Company Portal**, then **Get**, and then **Install**.</span></span>
    
4. <span data-ttu-id="9b2b7-162">설치, **열기**를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-162">After it installs, tap **Open**.</span></span>
    
5. <span data-ttu-id="9b2b7-163">**Intune 회사 포털** 화면에서 Office 365 전역 관리자 계정을 사용 하 여 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-163">On the **Intune Company Portal** screen, sign in with your Office 365 global administrator account.</span></span>
    
6. <span data-ttu-id="9b2b7-164">**회사 액세스 설치** 화면에서 **시작**을 누른 다음 **계속** 을 두번 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-164">On the **Company Access Setup** screen, tap **Begin**, and then tap **Continue** twice.</span></span>
    
7. <span data-ttu-id="9b2b7-165">**기능 가져온 다음?** 화면에서 **등록**을 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-165">On the **What comes next?** screen, tap **Enroll**.</span></span>
    
8. <span data-ttu-id="9b2b7-166">**활성화 장치의 관리자에 게?** 화면에서 **활성화**를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-166">On the **Activate device administrator?** screen, tap **Activate**.</span></span>
    
9. <span data-ttu-id="9b2b7-167">**프로필 관리** 화면에서 **설치**를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-167">On the **Management Profile** screen, tap **Install**.</span></span>
    
10. <span data-ttu-id="9b2b7-168">**암호를 입력**하면 iOS 장치 암호를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-168">In **Enter Passcode**, type your iOS device passcode.</span></span>
    
11. <span data-ttu-id="9b2b7-169">**어떤 가져온 다음** 화면에서 **등록**을 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-169">On the **What comes next** screen, tap **Enroll**.</span></span>
    
12. <span data-ttu-id="9b2b7-170">**프로 파일 설치** **설치**를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-170">In **Install Profile**, tap **Install**.</span></span>
    
13. <span data-ttu-id="9b2b7-171">**경고** 페이지에서 **설치**를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-171">On the **Warning** page, tap **Install**.</span></span>
    
14. <span data-ttu-id="9b2b7-172">**원격 관리** **신뢰**를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-172">In **Remote Management**, tap **Trust**.</span></span>
    
15. <span data-ttu-id="9b2b7-173">등록 프로세스를 완료 하려면 **완료** 를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-173">Tap **Done** to complete the enrollment process.</span></span>
    
16. <span data-ttu-id="9b2b7-174">것인지 묻는 메시지가 나타나면 **"포털 Comp"에서이 페이지를 열고?**, **열기**를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-174">When prompted to **Open this page in "Comp Portal"?**, tap **Open**.</span></span>
    
17. <span data-ttu-id="9b2b7-175">**회사 액세스 설치** 화면에서 **시작**을 누른 다음 **완료**를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-175">On the **Company Access Setup** screen, tap **Begin**, and then tap **Done**.</span></span>
    
18. <span data-ttu-id="9b2b7-176">Microsoft Intune 회사 포털 앱의 기본 화면에 다음 항목이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-176">On the main screen of the Microsoft Intune Company Portal app, you should see:</span></span>
    
  - <span data-ttu-id="9b2b7-177">녹색 배너.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-177">A green banner.</span></span>
    
  - <span data-ttu-id="9b2b7-178">가상 회사 이름(왼쪽 위).</span><span class="sxs-lookup"><span data-stu-id="9b2b7-178">Your fictional company name in the upper left.</span></span>
    
  - <span data-ttu-id="9b2b7-179">**내 장치**에 나열 된 사용자 iOS 장치 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-179">Your iOS device name listed in **My Devices**.</span></span>
    
  - <span data-ttu-id="9b2b7-180">**헬프데스크** 섹션- **555-1234** 및 **전자 메일 하 여 대화 상대** 단추 전화번호와 **User5** **대화 상대 이름** .</span><span class="sxs-lookup"><span data-stu-id="9b2b7-180">In the **Helpdesk** section, the **Contact Name** of **User5** with the phone number of **555-1234** and a **Contact by email** button.</span></span>
    
<span data-ttu-id="9b2b7-p111">Microsoft Intune에서는 원격 잠금 및 암호 초기화 기능을 모두 제공합니다. 장치를 분실한 경우 원격으로 장치를 잠글 수 있습니다. 암호를 잊은 경우 원격으로 암호를 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-p111">Microsoft Intune provides both remote lock and passcode reset capabilities. If someone loses their device, you can lock the device remotely. If someone forgets their passcode, you can remove the passcode remotely.</span></span>
  
<span data-ttu-id="9b2b7-184">원격으로 iOS 장치를 잠그려면:</span><span class="sxs-lookup"><span data-stu-id="9b2b7-184">To lock an iOS device remotely:</span></span>
  
1. <span data-ttu-id="9b2b7-185">브라우저의 Microsoft Intune 관리 콘솔 탭에서 관리 컴퓨터에서의 왼쪽된 탐색 영역에서 **그룹** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-185">From your administration computer, on the Microsoft Intune administration console tab of your browser, click **Groups** in the left navigation.</span></span>
    
2. <span data-ttu-id="9b2b7-186">**그룹** 창에서 엽니다 **모든 장치 > 모든 모바일 장치 > 모두 직접 관리 하는 장치**합니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-186">In the **Groups** pane, open **All devices > All Mobile devices > All Direct Managed Devices**.</span></span>
    
3. <span data-ttu-id="9b2b7-187">**모든 직접 관리 하는 장치** 창에서 **장치** 탭을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-187">In the **All Direct Managed Devices** pane, click the **Devices** tab.</span></span>
    
4. <span data-ttu-id="9b2b7-188">장치 목록에서 해당하는 iOS 장치를 클릭합니다. </span><span class="sxs-lookup"><span data-stu-id="9b2b7-188">In the devices list, click your iOS device.</span></span> 
    
5. <span data-ttu-id="9b2b7-189">iOS 장치에서 기본 화면이 표시되도록 합니다. </span><span class="sxs-lookup"><span data-stu-id="9b2b7-189">From your iOS device, make sure it is at the main screen.</span></span> 
    
6. <span data-ttu-id="9b2b7-p112">작업 표시줄에서 사용자 관리 컴퓨터에서 클릭 **원격 작업 > 원격 잠금**합니다. 잠금 화면으로 전환 하는 것 처럼 iOS 장치를 시청 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-p112">From your administration computer, on the taskbar, click **Remote Tasks > Remote Lock**. Watch your iOS device as it switches to the lockout screen.</span></span>
    
<span data-ttu-id="9b2b7-192">암호를 제거하려면:</span><span class="sxs-lookup"><span data-stu-id="9b2b7-192">To remove the passcode:</span></span>
  
1. <span data-ttu-id="9b2b7-193">**모든 직접 관리 하는 장치** 창에서 관리 컴퓨터에서 **장치** 탭을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-193">From your administration computer, in the **All Direct Managed Devices** pane, click the **Devices** tab.</span></span>
    
2. <span data-ttu-id="9b2b7-p113">목록에서 iOS 장치를 클릭 합니다. 작업 표시줄에서 클릭 **원격 작업 > 암호 재설정**합니다. 1 분까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-p113">In the list, click your iOS device. On the taskbar, click **Remote Tasks > Passcode Reset**. Wait for one minute.</span></span>
    
3. <span data-ttu-id="9b2b7-p114">IOS 장치에서 잠금을 해제 하 고 암호 더이상 인지 확인 합니다. 암호를 다시을 변경 하려면 **설정**하 고 다음 **암호**으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-p114">From your iOS device, unlock it and notice that there is no longer a passcode. To change the passcode back, go into **Settings**, and then **Passcode**.</span></span>
    
## <a name="phase-3-for-android-devices-only-enroll-and-manage-an-android-device"></a><span data-ttu-id="9b2b7-199">3단계(Android 장치만 해당): Android 장치 등록 및 관리</span><span class="sxs-lookup"><span data-stu-id="9b2b7-199">Phase 3 (for Android devices only): Enroll and manage an Android device</span></span>

<span data-ttu-id="9b2b7-200">Intune에서 관리할 Android 장치를 등록하려면 다음 항목이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-200">You will need the following to enroll an Android device for management by Intune:</span></span>
  
- <span data-ttu-id="9b2b7-201">Android 장치.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-201">An Android device.</span></span>
    
- <span data-ttu-id="9b2b7-202">장치의 암호에 대 한 지식입니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-202">Knowledge of the device's passcode.</span></span>
    
<span data-ttu-id="9b2b7-203">Intune 회사 포털 앱을 다운로드하고 Android 장치를 등록하려면:</span><span class="sxs-lookup"><span data-stu-id="9b2b7-203">To download the Intune Company portal app and enroll the Android device:</span></span>
  
1. <span data-ttu-id="9b2b7-204">Android 장치에서 **Google 재생 저장소**이동 하 고 **시작**을 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-204">From your Android device, go to the **Google Play Store**, and then tap **Get Started**.</span></span>
    
2. <span data-ttu-id="9b2b7-205">검색 상자에 **intune** 를 입력 하 고 검색 결과에서 **intune 회사 포털** 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-205">Type **intune** in the search box, and then tap **intune company portal** in the search results.</span></span>
    
3. <span data-ttu-id="9b2b7-206">**Intune 회사 포털** 항목을 누른 다음 **설치**를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-206">Tap the **Intune Company Portal** item, and then tap **Install**.</span></span>
    
4. <span data-ttu-id="9b2b7-207">**계정 설정에 대 한 전체** 화면에 **계속**하 고 다음 **건너뛰기**를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-207">On the **For Complete account setup** screen, tap **Continue**, and then **Skip**.</span></span>
    
5. <span data-ttu-id="9b2b7-p115">**Intune 회사 포털** **수락**을 누릅니다. 앱 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-p115">In **Intune Company Portal**, tap **Accept**. The app installs.</span></span>
    
6. <span data-ttu-id="9b2b7-210">**열기**를 누른 다음 **로그인**을 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-210">Tap **Open**, and then tap **Sign in**.</span></span>
    
7. <span data-ttu-id="9b2b7-211">**Intune 회사 포털** 화면에서 Office 365 전역 관리자 계정을 사용 하 여 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-211">On the **Intune Company Portal** screen, sign in with your Office 365 global administrator account.</span></span>
    
8. <span data-ttu-id="9b2b7-212">**회사 액세스 설정** 화면에서 두번 **시작**및 **계속** 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-212">On the **Company Access Setup** screen, tap **Begin**, and then **Continue** twice.</span></span>
    
9. <span data-ttu-id="9b2b7-213">**기능 가져온 다음?** 화면에서 **등록**을 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-213">On the **What comes next?** screen, tap **Enroll**.</span></span>
    
10. <span data-ttu-id="9b2b7-214">**활성화 장치의 관리자에 게?** 화면에서 누릅니다 **활성화.**</span><span class="sxs-lookup"><span data-stu-id="9b2b7-214">On the **Activate device administrator?** screen, tap **Activate.**</span></span>
    
11. <span data-ttu-id="9b2b7-p116">**개인정보 보호 정책** 화면에서 **읽었으며** 선택 하 고 **확인**을 누릅니다. 등록 프로세스를 완료할 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-p116">On the **Privacy Policy** screen, select **I acknowledge** and then tap **Confirm**. Wait for the enrollment process to complete.</span></span>
    
12. <span data-ttu-id="9b2b7-217">**회사 액세스 설치** 화면에서 **계속**누른 다음 **완료**를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-217">In the **Company Access Setup** screen, tap **Continue**, and then tap **Done**.</span></span>
    
13. <span data-ttu-id="9b2b7-218">Microsoft Intune 회사 포털 앱의 기본 화면 왼쪽 위에 녹색 배너와 가상 회사 이름이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-218">On the main screen of the Microsoft Intune Company Portal app, you should see a green banner and your fictional company name in the upper left.</span></span>
    
14. <span data-ttu-id="9b2b7-p117">**내 장치**를 누릅니다. Android 장치 이름 목록에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-p117">Tap **My devices**. You should see your Android device name in the list.</span></span>
    
15. <span data-ttu-id="9b2b7-p118">**IT 대화 상대**를 누릅니다. **User5**의 대화 상대는 IT 및 **555-1234**, **전자 메일에 게 문의** 하는 버튼의 전화번호를 참조 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-p118">Tap **Contact IT**. You should see the phone number of **555-1234**, a **Contact by email** button, and the IT contact of **User5**.</span></span>
    
<span data-ttu-id="9b2b7-p119">Microsoft Intune에서는 원격 잠금 및 암호 초기화 기능을 모두 제공합니다. 장치를 분실한 경우 원격으로 장치를 잠글 수 있습니다. 암호를 잊은 경우 원격으로 암호를 초기화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-p119">Microsoft Intune provides both remote lock and passcode reset capabilities. If someone loses their device, you can lock the device remotely. If someone forgets their passcode, you can reset the passcode remotely.</span></span>
  
<span data-ttu-id="9b2b7-226">원격으로 Android 장치를 잠그려면:</span><span class="sxs-lookup"><span data-stu-id="9b2b7-226">To lock an Android device remotely:</span></span>
  
1. <span data-ttu-id="9b2b7-227">브라우저의 Microsoft Intune 관리 콘솔 탭에서 관리 컴퓨터에서의 왼쪽된 탐색 영역에서 **그룹** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-227">From your administration computer, on the Microsoft Intune administration console tab of your browser, click **Groups** in the left navigation.</span></span>
    
2. <span data-ttu-id="9b2b7-228">**그룹** 창에서 엽니다 **모든 장치 > 모든 모바일 장치 > 모두 직접 관리 하는 장치**합니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-228">In the **Groups** pane, open **All devices > All Mobile devices > All Direct Managed Devices**.</span></span>
    
3. <span data-ttu-id="9b2b7-229">**모든 직접 관리 하는 장치** 창에서 **장치** 탭을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-229">In the **All Direct Managed Devices** pane, click the **Devices** tab.</span></span>
    
4. <span data-ttu-id="9b2b7-230">장치 목록에서 해당하는 Android 장치를 클릭합니다. </span><span class="sxs-lookup"><span data-stu-id="9b2b7-230">In the devices list, click your Android device.</span></span> 
    
5. <span data-ttu-id="9b2b7-231">Android 장치에서 기본 화면이 표시되도록 합니다. </span><span class="sxs-lookup"><span data-stu-id="9b2b7-231">From your Android device, make sure it is at the main screen.</span></span> 
    
6. <span data-ttu-id="9b2b7-p120">작업 표시줄에서 사용자 관리 컴퓨터에서 클릭 **원격 작업 > 원격 잠금**합니다. 대화 상자가 나타나면 **예**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-p120">From your administration computer, on the taskbar, click **Remote Tasks > Remote Lock**. When prompted, click **Yes**.</span></span>
    
7. <span data-ttu-id="9b2b7-234">Android 장치가 잠금 화면으로 전환되는 것을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-234">Watch your Android device as it switches to the lockout screen.</span></span>
    
<span data-ttu-id="9b2b7-235">Android 장치에 대 한 암호를 다시 설정할 때 Intune 관리 포털을 생성 하 고 강력한 암호를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-235">When you reset the passcode for Android devices, the Intune administration portal generates and configures a strong passcode.</span></span>
  
<span data-ttu-id="9b2b7-236">원격으로 암호를 초기화하려면:</span><span class="sxs-lookup"><span data-stu-id="9b2b7-236">To reset the passcode remotely:</span></span>
  
1. <span data-ttu-id="9b2b7-237">관리 컴퓨터의 **모든 직접 관리 하는 장치** 창에서 브라우저를 Microsoft Intune 관리 콘솔 탭에서 Android 장치를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-237">From your administration computer, on the Microsoft Intune administration console tab of your browser, in the **All Direct Managed Devices** pane, click your Android device.</span></span>
    
2. <span data-ttu-id="9b2b7-238">작업 표시줄에서 클릭 **원격 작업 > 암호 재설정**합니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-238">On the taskbar, click **Remote Tasks > Passcode Reset**.</span></span>
    
3. <span data-ttu-id="9b2b7-p121">**원격 작업: 암호 재설정** 메시지를 표시, **예**를 클릭 합니다. 1 분까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-p121">On the **Remote Task: Passcode Reset** prompt, click **Yes**. Wait for one minute.</span></span>
    
4. <span data-ttu-id="9b2b7-241">**모든 직접 관리 하는 장치** 창에서 **속성 보기를**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-241">In the **All Direct Managed Devices** pane, click **View Properties**.</span></span>
    
5. <span data-ttu-id="9b2b7-242">**암호 다시 설정**아래에서 새 암호를 note 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-242">Under **Passcode Reset**, note the new passcode.</span></span>
    
6. <span data-ttu-id="9b2b7-243">Android 장치에서 잠금 화면의 새 암호를 입력합니다. </span><span class="sxs-lookup"><span data-stu-id="9b2b7-243">From your Android device, enter the new passcode from the lockout screen.</span></span> 
    
7. <span data-ttu-id="9b2b7-244">암호를 다시을 변경 하려면 **설정**으로 이동, **장치**를 누릅니다, 그리고 **잠금 화면**을 누릅니다, 그리고은 암호에 대 한 새 암호를 다시, 누르고 **화면 잠금 기능**및 사용자가 선택한을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-244">To change the passcode back, go into **Settings**, tap **Device**, tap **Lock screen**, enter the new passcode again, tap **Screen lock**, and then your choice for the passcode.</span></span>
    
> [!TIP]
> <span data-ttu-id="9b2b7-245">[여기](http://aka.ms/catlgstack)를 클릭하여 One Microsoft 클라우드 테스트 랩 가이드 스택의 모든 기사에 대한 가상 맵을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b2b7-245">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="9b2b7-246">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9b2b7-246">See Also</span></span>

[<span data-ttu-id="9b2b7-247">Microsoft 365 엔터프라이즈 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="9b2b7-247">The Microsoft 365 Enterprise dev/test environment</span></span>](the-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="9b2b7-248">Microsoft 365 엔터프라이즈 개발/테스트 환경에 대 한 MAM 정책</span><span class="sxs-lookup"><span data-stu-id="9b2b7-248">MAM policies for your Microsoft 365 Enterprise dev/test environment</span></span>](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="9b2b7-249">클라우드 도입 TLG(테스트 랩 가이드)</span><span class="sxs-lookup"><span data-stu-id="9b2b7-249">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="9b2b7-250">엔터프라이즈 이동성 + 보안 (EMS)</span><span class="sxs-lookup"><span data-stu-id="9b2b7-250">Enterprise Mobility + Security (EMS)</span></span>](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


