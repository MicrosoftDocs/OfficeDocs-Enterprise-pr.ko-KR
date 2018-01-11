---
title: "Microsoft 365 엔터프라이즈 개발/테스트 환경에 대 한 MAM 정책"
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
ms.assetid: 1aa9639b-2862-49c4-bc33-1586dda636b8
description: "요약:이 테스트 랩 가이드를 사용 하 여 EMS 모바일 응용 프로그램 관리 (MAM) 정책 Microsoft 365 개발/테스트 환경에 추가 합니다."
ms.openlocfilehash: cd5a9801ec7cc5c8fe287fa65015fcb02dd542bf
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/11/2018
---
# <a name="mam-policies-for-your-microsoft-365-enterprise-devtest-environment"></a><span data-ttu-id="0bb3d-103">Microsoft 365 엔터프라이즈 개발/테스트 환경에 대 한 MAM 정책</span><span class="sxs-lookup"><span data-stu-id="0bb3d-103">MAM policies for your Microsoft 365 Enterprise dev/test environment</span></span>

 <span data-ttu-id="0bb3d-104">**요약:** 이 테스트 랩 가이드를 사용 하 여 Microsoft 365 개발/테스트 환경에 EMS 모바일 응용 프로그램 관리 (MAM) 정책을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bb3d-104">**Summary:** Use this Test Lab Guide to add EMS mobile application management (MAM) policies to your Microsoft 365 dev/test environment.</span></span>
  
<span data-ttu-id="0bb3d-p101">Microsoft 엔터프라이즈 이동성 + 보안 (EMS) 직원에 게 조직의 데이터를 보호 하는 동안 자신의 좋아하는 앱 및 장치를 사용 하 여 생산성을 유지 하는데 도움이 됩니다. 자세한 내용은 [엔터프라이즈 이동성 + 보안 (EMS)를](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="0bb3d-p101">The Microsoft Enterprise Mobility + Security (EMS) helps keep your employees productive using their favorite apps and devices while protecting your organization's data. For more information, see [Enterprise Mobility + Security (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span></span>
  
<span data-ttu-id="0bb3d-107">이 문서의 지침을과 함께 Microsoft 365 개발/테스트 환경에 모바일 응용 프로그램 관리 (MAM) 정책을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bb3d-107">With the instructions in this article, you add mobile application management (MAM) policies to your Microsoft 365 dev/test environment.</span></span>
  
## <a name="phase-1-build-out-your-microsoft-365-devtest-environment"></a><span data-ttu-id="0bb3d-108">1 단계: Microsoft 365 개발/테스트 환경을 구축합니다</span><span class="sxs-lookup"><span data-stu-id="0bb3d-108">Phase 1: Build out your Microsoft 365 dev/test environment</span></span>

<span data-ttu-id="0bb3d-109">[개발/테스트 환경에서 Microsoft 365 Enterprise의](the-microsoft-365-enterprise-dev-test-environment.md)에서 지시를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="0bb3d-109">Follow the instructions in [The Microsoft 365 Enterprise dev/test environment](the-microsoft-365-enterprise-dev-test-environment.md).</span></span>
  
## <a name="phase-2-create-and-deploy-mam-policies-for-ios-and-android-devices"></a><span data-ttu-id="0bb3d-110">2단계: iOS 및 Android 장치용으로 MAM 정책 만들고 배포하기</span><span class="sxs-lookup"><span data-stu-id="0bb3d-110">Phase 2: Create and deploy MAM policies for iOS and Android devices</span></span>

<span data-ttu-id="0bb3d-111">이 단계에서는 두 개의 다른 MAM 정책을 만들고 배포할 수 있습니다. 하나는 iOS 장치용이며 하나는 Android 장치용입니다.</span><span class="sxs-lookup"><span data-stu-id="0bb3d-111">In this phase, you create and deploy two different MAM policies: one for iOS devices and one for Android devices.</span></span>
  
1. <span data-ttu-id="0bb3d-112">Office 365 포털 ([https://portal.office.com](https://portal.office.com))에 이동 하 고 전역 관리자 계정 사용 하 여 Office 365 평가판 구독에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bb3d-112">Go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
2. <span data-ttu-id="0bb3d-113">브라우저의 새 탭에서 Azure 포털 ([https://azure.portal.com](https://azure.portal.com)) 열고 프로그램 Office 365 전역 관리자 계정을 사용 하 여 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bb3d-113">On a new tab of your browser, open the Azure portal ([https://azure.portal.com](https://azure.portal.com)) and sign in using your Office 365 global administrator account.</span></span>
    
3. <span data-ttu-id="0bb3d-114">탐색 창에서 Internet Explorer에서 포털 Azure 탭에서 **더 많은 서비스** (또는 오른쪽 화살표)를 클릭 하 고 **Intune**입력 **Intune**를 클릭 한 다음 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bb3d-114">On the Azure portal tab in Internet Explorer, in the navigation pane, click **More services** (or the right arrow), type **Intune**, and then click **Intune**.</span></span>
    
4. <span data-ttu-id="0bb3d-115">왼쪽 탐색 창에서 **그룹**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0bb3d-115">In the left navigation pane, click **Groups**.</span></span>
    
5. <span data-ttu-id="0bb3d-116">**사용자 및 그룹 모든 그룹** 블레이드에서 **추가**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bb3d-116">On the **Users and groups-All groups** blade, click **Add**.</span></span>
    
6. <span data-ttu-id="0bb3d-117">**멤버 자격 종류**에 **할당 됨** 을 선택 **iOS 장치 사용자를 관리 되는** **이름**입력을 **그룹** 블레이드에서 **예** 에 대 한 선택 **를 사용 하도록 설정 하는 Office 기능?**, 다음 **만들기**를 클릭 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0bb3d-117">On the **Group** blade, type **Managed iOS device users** in **Name**, select **Assigned** in **Membership type**, select **Yes** for **Enable Office features?**, and then click **Create**.</span></span> 
    
7. <span data-ttu-id="0bb3d-118">**그룹** 블레이드를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="0bb3d-118">Close the **Group** blade.</span></span>
    
8. <span data-ttu-id="0bb3d-119">**사용자 및 그룹 모든 그룹** 블레이드에서 **추가**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bb3d-119">On the **Users and groups-All groups** blade, click **Add**.</span></span>
    
9. <span data-ttu-id="0bb3d-120">사이트 **멤버 자격 종류**에 **할당 됨** 을 선택 **Android 관리 되는 장치 사용자** **이름**입력 하 고을 **그룹** 블레이드에서를 **예** 에 대 한 선택 **를 사용 하도록 설정 하는 Office 기능?**, 다음 **만들기**를 클릭 하 고 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bb3d-120">On the **Group** blade, type **Managed Android device users** in **Name**, select **Assigned** in **Membership type**, select **Yes** for **Enable Office features?**, and then click **Create**.</span></span>
    
10. <span data-ttu-id="0bb3d-121">**사용자 및 그룹 모든 그룹** 블레이드를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="0bb3d-121">Close the **Users and groups-All groups** blade.</span></span>
    
11. <span data-ttu-id="0bb3d-122">**Intune** 블레이드 **빠른 작업** 목록에서 **준수 정책 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bb3d-122">On the **Intune** blade, in the **Quick tasks** list, click **Create a compliance policy**.</span></span>
    
12. <span data-ttu-id="0bb3d-123">**규정 준수 정책 프로필** 블레이드 **정책 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bb3d-123">On the **Compliance Policy Profiles** blade, click **Create Policy**.</span></span>
    
13. <span data-ttu-id="0bb3d-p102">**정책 만들기** 블레이드 **이름** **iOS**를 입력 합니다. **플랫폼** **iOS**, 선택한 **iOS 규정 준수 정책** 블레이드에서 **확인** 을 클릭 한 다음 **만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bb3d-p102">On the **Create Policy** blade, in **Name**, type **iOS**. In **Platform**, select **iOS**, click **OK** on the **iOS compliance policy** blade, and then click **Create**.</span></span>
    
14. <span data-ttu-id="0bb3d-126">**규정 준수 정책 프로필** 블레이드 **정책 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bb3d-126">On the **Compliance Policy Profiles** blade, click **Create Policy**.</span></span>
    
15. <span data-ttu-id="0bb3d-p103">**정책 만들기** 블레이드 **이름**, **Android**을 입력 합니다. **플랫폼** **Android**선택, **Android 규정 준수 정책** 블레이드에서 **확인** 을 클릭 하 고 **만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bb3d-p103">On the **Create Policy** blade, in **Name**, type **Android**. In **Platform**, select **Android**, click **OK** on the **Android compliance policy** blade, and then click **Create**.</span></span>
    
16. <span data-ttu-id="0bb3d-129">**규정 준수 정책 프로필** 블레이드 **Android** 정책 이름을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bb3d-129">On the **Compliance Policy Profiles** blade, click the **Android** policy name.</span></span>
    
17. <span data-ttu-id="0bb3d-130">**Android-속성** 블레이드의 왼쪽 탐색 영역에서 **할당**을 클릭 하 고 **그룹을 선택 합니다.**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bb3d-130">In the left navigation of the **Android - Properties** blade, click **Assignments**, and then click **Select groups**.</span></span>
    
18. <span data-ttu-id="0bb3d-131">**그룹을 선택** 블레이드 **Android 관리 되는 장치 사용자** 그룹을 클릭 하 고 **선택**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bb3d-131">On the **Select groups** blade, click the **Managed Android device users** group, and then click **Select**.</span></span>
    
19. <span data-ttu-id="0bb3d-132">**저장**을 클릭 하 고 **Android-배정** 블레이드를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="0bb3d-132">Click **Save**, and then close the **Android - Assignments** blade.</span></span>
    
20. <span data-ttu-id="0bb3d-133">**규정 준수 정책 프로필** 블레이드 **iOS** 정책 이름을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bb3d-133">On the **Compliance Policy Profiles** blade, click the **iOS** policy name.</span></span>
    
21. <span data-ttu-id="0bb3d-134">**IOS-속성** 블레이드의 왼쪽 탐색 영역에서 **할당**을 클릭 하 고 **그룹을 선택 합니다.**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bb3d-134">In the left navigation of the **iOS - Properties** blade, click **Assignments**, and then click **Select groups**.</span></span>
    
22. <span data-ttu-id="0bb3d-135">**그룹 선택** 블레이드 **관리 되는 iOS 장치 사용자** 그룹을 클릭 하 고 **선택**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bb3d-135">On the **Select groups** blade, click the **Managed iOS device users** group, and then click **Select**.</span></span>
    
23. <span data-ttu-id="0bb3d-136">**저장**을 클릭 하 고 **iOS-배정** 블레이드를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="0bb3d-136">Click **Save**, and then close the **iOS - Assignments** blade.</span></span>
    
24. <span data-ttu-id="0bb3d-137">**규정 준수 정책 프로필** 블레이드를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="0bb3d-137">Close the **Compliance Policy Profiles** blade.</span></span>
    
25. <span data-ttu-id="0bb3d-138">**Intune** 블레이드에서의 왼쪽된 탐색 영역에서 **관리 앱** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bb3d-138">On the **Intune** blade, click **Manage apps** in the left navigation.</span></span>
    
26. <span data-ttu-id="0bb3d-139">**모바일 앱** 블레이드 **앱**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bb3d-139">On the **Mobile Apps** blade, click **Apps**.</span></span>
    
27. <span data-ttu-id="0bb3d-140">앱 목록에서 **PowerPoint**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bb3d-140">In the list of apps, click **PowerPoint**,</span></span> 
    
28. <span data-ttu-id="0bb3d-p104">**PowerPoint 개요** 블레이드 클릭 **할당 > 그룹을 선택 > 관리 되는 iOS 장치 > 선택**합니다. **형식** **가능 시간**선택 하 고 **저장**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bb3d-p104">On the **PowerPoint Overview** blade, click **Assignments > Select groups > Managed iOS devices > Select**. In **Type**, select **Available**, and then click **Save**.</span></span>
    
29. <span data-ttu-id="0bb3d-143">다음 앱은 28단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="0bb3d-143">Repeat step 28 for the following apps:</span></span>
    
  - <span data-ttu-id="0bb3d-144">Android용 Outlook</span><span class="sxs-lookup"><span data-stu-id="0bb3d-144">Outlook for Android</span></span>
    
  - <span data-ttu-id="0bb3d-145">iOS용 Word</span><span class="sxs-lookup"><span data-stu-id="0bb3d-145">Word for iOS</span></span>
    
  - <span data-ttu-id="0bb3d-146">IOS용 Excel</span><span class="sxs-lookup"><span data-stu-id="0bb3d-146">Excel for iOS</span></span>
    
  - <span data-ttu-id="0bb3d-147">iOS용 Outlook</span><span class="sxs-lookup"><span data-stu-id="0bb3d-147">Outlook for iOS</span></span>
    
  - <span data-ttu-id="0bb3d-148">iOS용 iPad의 Microsoft Dynamics CRM</span><span class="sxs-lookup"><span data-stu-id="0bb3d-148">Microsoft Dynamics CRM on iPad for iOS</span></span>
    
  - <span data-ttu-id="0bb3d-149">iOS용 iPhone의 Microsoft Dynamics CRM</span><span class="sxs-lookup"><span data-stu-id="0bb3d-149">Microsoft Dynamics CRM on iPhone for iOS</span></span>
    
  - <span data-ttu-id="0bb3d-150">Android 휴대폰용 Dynamics CRM</span><span class="sxs-lookup"><span data-stu-id="0bb3d-150">Dynamics CRM for Phones for Android</span></span>
    
  - <span data-ttu-id="0bb3d-151">Android 태블릿용 Dynamics CRM</span><span class="sxs-lookup"><span data-stu-id="0bb3d-151">Dynamics CRM for Tablets for Android</span></span>
    
  - <span data-ttu-id="0bb3d-152">Android용 Excel</span><span class="sxs-lookup"><span data-stu-id="0bb3d-152">Excel for Android</span></span>
    
  - <span data-ttu-id="0bb3d-153">Android용 Word</span><span class="sxs-lookup"><span data-stu-id="0bb3d-153">Word for Android</span></span>
    
  - <span data-ttu-id="0bb3d-154">iOS용 OneNote</span><span class="sxs-lookup"><span data-stu-id="0bb3d-154">OneNote for iOS</span></span>
    
30. <span data-ttu-id="0bb3d-155">**모바일 응용 프로그램-응용 프로그램** 블레이드를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="0bb3d-155">Close the **Mobile Apps - Apps** blade.</span></span>
    
31. <span data-ttu-id="0bb3d-156">**모바일 앱** 블레이드 **App 보호 정책**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bb3d-156">On the **Mobile Apps** blade, click **App Protection Policies**.</span></span>
    
32. <span data-ttu-id="0bb3d-157">**응용 프로그램 보호 정책** 블레이드에서 **정책을 추가**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bb3d-157">On the **App Protection Policies** blade, click **Add a policy**.</span></span>
    
33. <span data-ttu-id="0bb3d-158">**추가 정책** 블레이드에서 **iOS**입력 하 고 **필요한 앱을 선택 합니다.**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bb3d-158">On the **Add a policy** blade, type **iOS**, and then click **Select required apps**.</span></span>
    
34. <span data-ttu-id="0bb3d-159">**앱** 블레이드에서 **PowerPoint**, **iPhone에서 Microsoft Dynamics CRM**, **Excel**, **iPhone에서 Microsoft Dynamics CRM**, **단어**, **OneNote**및 **Outlook**누르고 **을 선택**합니다.</span><span class="sxs-lookup"><span data-stu-id="0bb3d-159">On the **Apps** blade, click **PowerPoint**, **Microsoft Dynamics CRM on iPhone**, **Excel**, **Microsoft Dynamics CRM on iPhone**, **Word**, **OneNote**, and **Outlook**, and then click **Select**.</span></span>
    
35. <span data-ttu-id="0bb3d-160">**추가 정책** 블레이드에서 **만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bb3d-160">On the **Add a policy** blade, click **Create**.</span></span>
    
36. <span data-ttu-id="0bb3d-161">**응용 프로그램 보호 정책** 블레이드에서 **정책을 추가**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bb3d-161">On the **App Protection Policies** blade, click **Add a policy**.</span></span>
    
37. <span data-ttu-id="0bb3d-162">**추가 정책** 블레이드에서 입력 **Android** **Android** **플랫폼**선택한 다음 **필요한 앱을 선택 합니다.**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bb3d-162">On the **Add a policy** blade, type **Android**, select **Android** in **Platform**, and then click **Select required apps**.</span></span>
    
38. <span data-ttu-id="0bb3d-163">**앱** 블레이드에서 **PowerPoint**, **태블릿에 대 한 Dynamics CRM**, **Excel**, **Word**, **Outlook**및 **전화에 대 한 Dynamics CRM**누르고 **을 선택**합니다.</span><span class="sxs-lookup"><span data-stu-id="0bb3d-163">On the **Apps** blade, click **PowerPoint**, **Dynamics CRM for tablets**, **Excel**, **Word**, **Outlook**, and **Dynamics CRM for phones**, and then click **Select**.</span></span>
    
39. <span data-ttu-id="0bb3d-164">**추가 정책** 블레이드에서 **만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bb3d-164">On the **Add a policy** blade, click **Create**.</span></span>
    
<span data-ttu-id="0bb3d-165">이제 iOS 장치용과 Android 장치용의 두 가지 MAM 정책이 있으며 선택한 앱의 설정 테스트를 실험할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0bb3d-165">You now have two MAM policies, one for iOS devices and one for Android devices, and are ready to experiment with testing settings for the selected apps.</span></span>
  
> [!TIP]
> <span data-ttu-id="0bb3d-166">[여기](http://aka.ms/catlgstack)를 클릭하여 One Microsoft 클라우드 테스트 랩 가이드 스택의 모든 기사에 대한 가상 맵을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0bb3d-166">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="0bb3d-167">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0bb3d-167">See Also</span></span>

[<span data-ttu-id="0bb3d-168">Microsoft 365 엔터프라이즈 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="0bb3d-168">The Microsoft 365 Enterprise dev/test environment</span></span>](the-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="0bb3d-169">IOS 및 Microsoft 기업 365 개발/테스트 환경에서 Android 장치 등록</span><span class="sxs-lookup"><span data-stu-id="0bb3d-169">Enroll iOS and Android devices in your Microsoft Enterprise 365 dev/test environment</span></span>](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
  
[<span data-ttu-id="0bb3d-170">클라우드 도입 TLG(테스트 랩 가이드)</span><span class="sxs-lookup"><span data-stu-id="0bb3d-170">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="0bb3d-171">엔터프라이즈 이동성 + 보안 (EMS)</span><span class="sxs-lookup"><span data-stu-id="0bb3d-171">Enterprise Mobility + Security (EMS)</span></span>](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


