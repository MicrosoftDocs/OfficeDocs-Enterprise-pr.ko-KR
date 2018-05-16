---
title: IOS 및 Microsoft 기업 365 개발/테스트 환경에서 Android 장치 등록
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/14/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: 요약:이 테스트 랩 가이드를 사용 하 여 Microsoft 365 개발/테스트 환경에서 장치를 등록 하 고 원격으로 관리 하기를.
ms.openlocfilehash: b5ceecd74ac010d787bc580054d5dd43db952fef
ms.sourcegitcommit: 29c8571ca4912549bac55ec9d1642d21eba5b0e4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/16/2018
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-devtest-environment"></a><span data-ttu-id="fd6d1-103">IOS 및 Microsoft 기업 365 개발/테스트 환경에서 Android 장치 등록</span><span class="sxs-lookup"><span data-stu-id="fd6d1-103">Enroll iOS and Android devices in your Microsoft Enterprise 365 dev/test environment</span></span>

 <span data-ttu-id="fd6d1-104">**요약:** 이 테스트 랩 가이드를 Microsoft 365 개발/테스트 환경에서 장치를 등록 하 고 원격으로 관리 하기를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd6d1-104">**Summary:** Use this Test Lab Guide to enroll devices in your Microsoft 365 dev/test environment and manage them remotely.</span></span>
  
<span data-ttu-id="fd6d1-p101">Microsoft Enterprise 이동성 제품군 (EMS) 직원에 게 조직의 데이터를 보호 하는 동안 자신의 좋아하는 앱 및 장치를 사용 하 여 생산성을 유지 도움이 됩니다. 자세한 내용은 [엔터프라이즈 이동성 + 보안 (EMS)를](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="fd6d1-p101">The Microsoft Enterprise Mobility Suite (EMS) helps keep your employees productive using their favorite apps and devices while protecting your organization's data. For more information, see [Enterprise Mobility + Security (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span></span>
  
<span data-ttu-id="fd6d1-p102">장치 수준에서 보안을 적용 해야하는 경우에 Microsoft Intune에 장치를 등록 해야 합니다. 장치 등록 뿐아니라를 사용 하면 조직 소유의 장치를 관리할 수 (BYOD) 개인 및 공유 장치를 조직에 따라서는 법적 수도 있지만 정책입니다.</span><span class="sxs-lookup"><span data-stu-id="fd6d1-p102">If you need to apply security at the device level, you must enroll devices into Microsoft Intune. Device enrollment not only helps you to manage organization-owned devices, but also personal (BYOD) and shared devices, depending on your organization's legal policies.</span></span>
  
<span data-ttu-id="fd6d1-109">이 문서에서 제공 하는 지침을 따르면를 등록 하 고 Microsoft 365 개발/테스트 환경에서 iOS 및 Android 장치에 대 한 기본 모바일 장치 관리 기능을 테스트 하는 작업을 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fd6d1-109">By following the instructions provided in this article, you'll be able to enroll and test basic mobile device management capabilities for iOS and Android devices in your Microsoft 365 dev/test environment.</span></span>
  
## <a name="phase-1-create-your-microsoft-365-devtest-environment"></a><span data-ttu-id="fd6d1-110">1 단계: Microsoft 365 개발/테스트 환경 만들기</span><span class="sxs-lookup"><span data-stu-id="fd6d1-110">Phase 1: Create your Microsoft 365 dev/test environment</span></span>

<span data-ttu-id="fd6d1-111">[개발/테스트 환경에서 Microsoft 365 Enterprise의](the-microsoft-365-enterprise-dev-test-environment.md)에서 지시를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="fd6d1-111">Follow the instructions in [The Microsoft 365 Enterprise dev/test environment](the-microsoft-365-enterprise-dev-test-environment.md).</span></span>
  
## <a name="phase-2-enroll-your-ios-and-android-devices"></a><span data-ttu-id="fd6d1-112">2 단계: iOS 및 Android 장치 등록</span><span class="sxs-lookup"><span data-stu-id="fd6d1-112">Phase 2: Enroll your iOS and Android devices</span></span>

<span data-ttu-id="fd6d1-113">먼저,의 지침을 사용 하 여 [설치 회사 포털 응용 프로그램에 로그인 하 고](https://docs.microsoft.com/intune-user-help/install-and-sign-in-to-the-intune-company-portal-app-ios) 개발/테스트 테 넌 트에 대 한 Microsoft Intune 회사 포털 응용 프로그램을 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fd6d1-113">First, use the instructions in [Install and sign in to the Company Portal app](https://docs.microsoft.com/intune-user-help/install-and-sign-in-to-the-intune-company-portal-app-ios) to customize the Microsoft Intune Company Portal app for your dev/test tenant.</span></span>

<span data-ttu-id="fd6d1-114">다음으로 iOS 장치를 등록 하려면 [회사 리소스에 대 한 액세스를 설정](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios) 하는의 지침을 따르십시오.</span><span class="sxs-lookup"><span data-stu-id="fd6d1-114">Next, use the instructions in [Set up access to your company resources](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios) to enroll an iOS device.</span></span>

<span data-ttu-id="fd6d1-115">다음으로, Android 장치와 등록 [등록 Intune에서 Android 장치에서](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android) 에서 지침을 따르십시오.</span><span class="sxs-lookup"><span data-stu-id="fd6d1-115">Next, use the instructions in [Enroll your Android device in Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android) to enroll an Android device.</span></span>

## <a name="phase-2-manage-your-ios-and-android-devices-remotely"></a><span data-ttu-id="fd6d1-116">2 단계: iOS 및 Android 장치를 원격으로 관리</span><span class="sxs-lookup"><span data-stu-id="fd6d1-116">Phase 2: Manage your iOS and Android devices remotely</span></span>

<span data-ttu-id="fd6d1-p103">Microsoft Intune에서는 원격 잠금 및 암호 초기화 기능을 모두 제공합니다. 장치를 분실한 경우 원격으로 장치를 잠글 수 있습니다. 암호를 잊은 경우 원격으로 암호를 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fd6d1-p103">Microsoft Intune provides both remote lock and passcode reset capabilities. If someone loses their device, you can lock the device remotely. If someone forgets their passcode, you can remove the passcode remotely.</span></span>
  
<span data-ttu-id="fd6d1-120">원격으로 iOS 장치를 잠그려면:</span><span class="sxs-lookup"><span data-stu-id="fd6d1-120">To lock an iOS device remotely:</span></span>
  
1.  <span data-ttu-id="fd6d1-121">새 탭을 열고 이동 http://manage.microsoft.com (필요한 경우).</span><span class="sxs-lookup"><span data-stu-id="fd6d1-121">Open a new tab and go to http://manage.microsoft.com (if needed).</span></span> 

2.  <span data-ttu-id="fd6d1-122">브라우저의 Microsoft Intune 관리 콘솔에서의 왼쪽된 탐색 영역에서 **그룹** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd6d1-122">From the Microsoft Intune administration console of your browser, click **Groups** in the left navigation.</span></span>

3. <span data-ttu-id="fd6d1-123">**그룹** 창에서 엽니다 **모든 장치 > 모든 모바일 장치 > 모두 직접 관리 하는 장치**합니다.</span><span class="sxs-lookup"><span data-stu-id="fd6d1-123">In the **Groups** pane, open **All devices > All Mobile devices > All Direct Managed Devices**.</span></span>
    
4. <span data-ttu-id="fd6d1-124">**모든 직접 관리 하는 장치** 창에서 **장치** 탭을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd6d1-124">In the **All Direct Managed Devices** pane, click the **Devices** tab.</span></span>
    
5. <span data-ttu-id="fd6d1-125">장치 목록에서 해당하는 iOS 장치를 클릭합니다. </span><span class="sxs-lookup"><span data-stu-id="fd6d1-125">In the devices list, click your iOS device.</span></span> 
    
6. <span data-ttu-id="fd6d1-126">iOS 장치에서 기본 화면이 표시되도록 합니다. </span><span class="sxs-lookup"><span data-stu-id="fd6d1-126">From your iOS device, make sure it is at the main screen.</span></span> 
    
7. <span data-ttu-id="fd6d1-p104">작업 표시줄에서 사용자 관리 컴퓨터에서 클릭 **원격 작업 > 원격 잠금**합니다. 잠금 화면으로 전환 하는 것 처럼 iOS 장치를 시청 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd6d1-p104">From your administration computer, on the taskbar, click **Remote Tasks > Remote Lock**. Watch your iOS device as it switches to the lockout screen.</span></span>
    
<span data-ttu-id="fd6d1-129">암호를 제거하려면:</span><span class="sxs-lookup"><span data-stu-id="fd6d1-129">To remove the passcode:</span></span>
  
1. <span data-ttu-id="fd6d1-130">**모든 직접 관리 하는 장치** 창에서 관리 컴퓨터에서 **장치** 탭을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd6d1-130">From your administration computer, in the **All Direct Managed Devices** pane, click the **Devices** tab.</span></span>
    
2. <span data-ttu-id="fd6d1-p105">목록에서 iOS 장치를 클릭 합니다. 작업 표시줄에서 클릭 **원격 작업 > 암호 재설정**합니다. 1 분까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="fd6d1-p105">In the list, click your iOS device. On the taskbar, click **Remote Tasks > Passcode Reset**. Wait for one minute.</span></span>
    
3. <span data-ttu-id="fd6d1-p106">IOS 장치에서 잠금을 해제 하 고 암호 더이상 인지 확인 합니다. 암호를 다시을 변경 하려면 **설정**하 고 다음 **암호**으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd6d1-p106">From your iOS device, unlock it and notice that there is no longer a passcode. To change the passcode back, go into **Settings**, and then **Passcode**.</span></span>
    
<span data-ttu-id="fd6d1-136">원격으로 Android 장치를 잠그려면:</span><span class="sxs-lookup"><span data-stu-id="fd6d1-136">To lock an Android device remotely:</span></span>
  
1. <span data-ttu-id="fd6d1-137">브라우저의 Microsoft Intune 관리 콘솔에서의 왼쪽된 탐색 영역에서 **그룹** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd6d1-137">From the Microsoft Intune administration console of your browser, click **Groups** in the left navigation.</span></span>
    
2. <span data-ttu-id="fd6d1-138">**그룹** 창에서 엽니다 **모든 장치 > 모든 모바일 장치 > 모두 직접 관리 하는 장치**합니다.</span><span class="sxs-lookup"><span data-stu-id="fd6d1-138">In the **Groups** pane, open **All devices > All Mobile devices > All Direct Managed Devices**.</span></span>
    
3. <span data-ttu-id="fd6d1-139">**모든 직접 관리 하는 장치** 창에서 **장치** 탭을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd6d1-139">In the **All Direct Managed Devices** pane, click the **Devices** tab.</span></span>
    
4. <span data-ttu-id="fd6d1-140">장치 목록에서 해당하는 Android 장치를 클릭합니다. </span><span class="sxs-lookup"><span data-stu-id="fd6d1-140">In the devices list, click your Android device.</span></span> 
    
5. <span data-ttu-id="fd6d1-141">Android 장치에서 기본 화면이 표시되도록 합니다. </span><span class="sxs-lookup"><span data-stu-id="fd6d1-141">From your Android device, make sure it is at the main screen.</span></span> 
    
6. <span data-ttu-id="fd6d1-p107">작업 표시줄에서 사용자 관리 컴퓨터에서 클릭 **원격 작업 > 원격 잠금**합니다. 대화 상자가 나타나면 **예**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd6d1-p107">From your administration computer, on the taskbar, click **Remote Tasks > Remote Lock**. When prompted, click **Yes**.</span></span>
    
7. <span data-ttu-id="fd6d1-144">Android 장치가 잠금 화면으로 전환되는 것을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="fd6d1-144">Watch your Android device as it switches to the lockout screen.</span></span>
    
<span data-ttu-id="fd6d1-145">Android 장치에 대 한 암호를 다시 설정할 때 Intune 관리 포털을 생성 하 고 강력한 암호를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd6d1-145">When you reset the passcode for Android devices, the Intune administration portal generates and configures a strong passcode.</span></span>
  
<span data-ttu-id="fd6d1-146">원격으로 암호를 초기화하려면:</span><span class="sxs-lookup"><span data-stu-id="fd6d1-146">To reset the passcode remotely:</span></span>
  
1. <span data-ttu-id="fd6d1-147">관리 컴퓨터의 **모든 직접 관리 하는 장치** 창에서 브라우저를 Microsoft Intune 관리 콘솔 탭에서 Android 장치를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd6d1-147">From your administration computer, on the Microsoft Intune administration console tab of your browser, in the **All Direct Managed Devices** pane, click your Android device.</span></span>
    
2. <span data-ttu-id="fd6d1-148">작업 표시줄에서 클릭 **원격 작업 > 암호 재설정**합니다.</span><span class="sxs-lookup"><span data-stu-id="fd6d1-148">On the taskbar, click **Remote Tasks > Passcode Reset**.</span></span>
    
3. <span data-ttu-id="fd6d1-p108">**원격 작업: 암호 재설정** 메시지를 표시, **예**를 클릭 합니다. 1 분까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="fd6d1-p108">On the **Remote Task: Passcode Reset** prompt, click **Yes**. Wait for one minute.</span></span>
    
4. <span data-ttu-id="fd6d1-151">**모든 직접 관리 하는 장치** 창에서 **속성 보기를**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd6d1-151">In the **All Direct Managed Devices** pane, click **View Properties**.</span></span>
    
5. <span data-ttu-id="fd6d1-152">**암호 다시 설정**아래에서 새 암호를 note 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd6d1-152">Under **Passcode Reset**, note the new passcode.</span></span>
    
6. <span data-ttu-id="fd6d1-153">Android 장치에서 잠금 화면의 새 암호를 입력합니다. </span><span class="sxs-lookup"><span data-stu-id="fd6d1-153">From your Android device, enter the new passcode from the lockout screen.</span></span> 
    
7. <span data-ttu-id="fd6d1-154">암호를 다시을 변경 하려면 **설정**으로 이동, **장치**를 누릅니다, 그리고 **잠금 화면**을 누릅니다, 그리고은 암호에 대 한 새 암호를 다시, 누르고 **화면 잠금 기능**및 사용자가 선택한을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd6d1-154">To change the passcode back, go into **Settings**, tap **Device**, tap **Lock screen**, enter the new passcode again, tap **Screen lock**, and then your choice for the passcode.</span></span>
    

> [!TIP]
> <span data-ttu-id="fd6d1-155">[여기](http://aka.ms/catlgstack)를 클릭하여 One Microsoft 클라우드 테스트 랩 가이드 스택의 모든 기사에 대한 가상 맵을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fd6d1-155">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="fd6d1-156">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fd6d1-156">See Also</span></span>

[<span data-ttu-id="fd6d1-157">Microsoft 365 Enterprise 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="fd6d1-157">The Microsoft 365 Enterprise dev/test environment</span></span>](the-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="fd6d1-158">Microsoft 365 Enterprise 개발/테스트 환경용 MAM(모바일 응용 프로그램 관리) 정책</span><span class="sxs-lookup"><span data-stu-id="fd6d1-158">MAM policies for your Microsoft 365 Enterprise dev/test environment</span></span>](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="fd6d1-159">클라우드 도입 TLG(테스트 랩 가이드)</span><span class="sxs-lookup"><span data-stu-id="fd6d1-159">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="fd6d1-160">엔터프라이즈 이동성 + 보안 (EMS)</span><span class="sxs-lookup"><span data-stu-id="fd6d1-160">Enterprise Mobility + Security (EMS)</span></span>](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


