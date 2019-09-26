---
title: 보안 게스트 공유 환경 만들기
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
localization_priority: Priority
description: Microsoft 365에서 보안 게스트 공유 환경 만드는 방법에 대해 알아보세요.
ms.openlocfilehash: 97aa0cf11159af483c307de8bdb2c3b15e704d36
ms.sourcegitcommit: c16ab90d0b9902228ce4337f1c64900592936cce
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/23/2019
ms.locfileid: "37108379"
---
# <a name="create-a-secure-guest-sharing-environment"></a><span data-ttu-id="49366-103">보안 게스트 공유 환경 만들기</span><span class="sxs-lookup"><span data-stu-id="49366-103">Create a secure guest sharing environment</span></span>

<span data-ttu-id="49366-104">이 문서에서는 Microsoft 365에서 보안 게스트 공유 환경을 만들기 위한 다양 한 옵션을 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="49366-104">In this article, we'll walk through a variety of options for creating a secure guest sharing environment in Microsoft 365.</span></span> <span data-ttu-id="49366-105">이는 사용 가능한 옵션에 대한 아이디어를 제공하는 예제 시나리오입니다.</span><span class="sxs-lookup"><span data-stu-id="49366-105">This is an example scenario to give you an idea of the options available.</span></span> <span data-ttu-id="49366-106">조직의 보안 및 규정 준수 요구 사항을 충족하기 위해 다음과 같이 다양한 조합의 절차를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49366-106">You can use these procedures in different combinations to meet the security and compliance needs of your organization.</span></span> <span data-ttu-id="49366-107">이 문서의 마지막에는 테스트 사례를 통해 이러한 옵션 중 일부를 어떻게 적용했는지 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="49366-107">At the end of the article, we'll walk through a test case to see how some of these options work together.</span></span>

<span data-ttu-id="49366-108">이 시나리오에서는 다음과 같은 사항을 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="49366-108">This scenario includes the following configuration:</span></span>

- <span data-ttu-id="49366-109">게스트에 대한 다단계 인증 설정</span><span class="sxs-lookup"><span data-stu-id="49366-109">Setting up multi-factor authentication for guests.</span></span>
- <span data-ttu-id="49366-110">게스트에 대한 사용 약관 설정</span><span class="sxs-lookup"><span data-stu-id="49366-110">Setting up a terms of use for guests.</span></span>
- <span data-ttu-id="49366-111">게스트가 계속해서 팀 및 사이트에 대해 권한이 필요한지 주기적으로 확인하기 위한 분기별 게스트 액세스 검토 설정</span><span class="sxs-lookup"><span data-stu-id="49366-111">Setting up quarterly guest access reviews to periodically validate whether guests continue to need permissions to teams and sites.</span></span>
- <span data-ttu-id="49366-112">관리되지 않은 장치에 대해서는 게스트가 웹에만 액세스하도록 제한</span><span class="sxs-lookup"><span data-stu-id="49366-112">Restricting guests to web-only access for unmanaged devices.</span></span>
- <span data-ttu-id="49366-113">게스트가 매일 인증할 수 있도록 세션 시간 제한 정책 구성</span><span class="sxs-lookup"><span data-stu-id="49366-113">Configuring a session timeout policy to ensure guests authenticate daily.</span></span>
- <span data-ttu-id="49366-114">콘텐츠를 분류하기 위한 민감도 레이블을 만들고 게시</span><span class="sxs-lookup"><span data-stu-id="49366-114">Creating and publishing sensitivity labels to classify content.</span></span>
- <span data-ttu-id="49366-115">극비 프로젝트에 대한 중요한 정보 유형 만들기</span><span class="sxs-lookup"><span data-stu-id="49366-115">Creating a sensitive information type for a highly confidential project.</span></span>
- <span data-ttu-id="49366-116">중요한 정보 유형이 포함된 문서에 *극비* 레이블을 자동으로 할당</span><span class="sxs-lookup"><span data-stu-id="49366-116">Automatically assigning a *highly confidential* label to documents that contain the sensitive information type.</span></span>
- <span data-ttu-id="49366-117">*극비*로 레이블 지정된 파일에서 게스트 액세스를 자동으로 제거</span><span class="sxs-lookup"><span data-stu-id="49366-117">Automatically removing guest access from files labeled as *highly confidential*.</span></span>

<span data-ttu-id="49366-118">이 문서에서 다루는 일부 옵션은 게스트가 Azure Active Directory의 계정이 있어야 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49366-118">Some of the options discussed in this article require guests to have an account in Azure Active Directory.</span></span> <span data-ttu-id="49366-119">파일과 폴더를 공유할 때 게스트가 디렉터리에 포함되도록 하려면 [Azure AD B2B와 SharePoint 및 OneDrive의 통합(미리 보기)](https://docs.microsoft.com/sharepoint/sharepoint-azureb2b-integration-preview)을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="49366-119">To ensure that guests are included in the directory when you share files and folders with them, use the [SharePoint and OneDrive integration with Azure AD B2B Preview](https://docs.microsoft.com/sharepoint/sharepoint-azureb2b-integration-preview).</span></span>

<span data-ttu-id="49366-120">이 문서에서는 게스트 공유 설정을 활성화하는 방법에 대해서는 다루지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="49366-120">Note that we won't discuss enabling guest sharing settings in this article.</span></span> <span data-ttu-id="49366-121">다른 시나리오의 게스트 공유 활성화에 대해 자세히 알아보려면 [조직 외부 사용자와 공동 작업](https://docs.microsoft.com/Office365/Enterprise/collaborating-with-people-outside-your-organization)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="49366-121">See [Collaborating with people outside your organization](https://docs.microsoft.com/Office365/Enterprise/collaborating-with-people-outside-your-organization) for details about enabling guest sharing for different scenarios.</span></span>

## <a name="set-up-multi-factor-authentication-for-guests"></a><span data-ttu-id="49366-122">게스트에 대한 다단계 인증 설정</span><span class="sxs-lookup"><span data-stu-id="49366-122">Set up multi-factor authentication for guests</span></span>

<span data-ttu-id="49366-123">다단계 인증은 계정이 손상될 가능성을 대폭 줄여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="49366-123">Multi-factor authentication greatly reduces the chances of an account being compromised.</span></span> <span data-ttu-id="49366-124">게스트 사용자는 관리 정책이나 모범 사례를 준수하지 않는 개인 이메일 계정을 사용할 가능성이 높기 때문에 게스트에 대해 다단계 인증을 요구하는 것은 특히 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-124">Since guest users may be using personal email accounts that don't adhere to any governance policies or best practices, it's especially important to require multi-factor authentication for guests.</span></span> <span data-ttu-id="49366-125">게스트 사용자의 사용자 이름 및 비밀번호가 도난될 경우 2단계 인증을 요구하면 알 수 없는 당사자가 내 사이트 및 파일에 액세스할 가능성이 대폭 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="49366-125">If a guest user's username and password is stolen, requiring a second factor of authentication greatly reduces the chances of unknown parties gaining access to your sites and files.</span></span>

<span data-ttu-id="49366-126">이 예제에서는 Azure Active Directory에서 조건부 액세서 정책을 사용하여 게스트에 대한 다단계 인증을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-126">In this example, we'll set up multi-factor authentication for guests by using a conditional access policy in Azure Active Directory.</span></span>

<span data-ttu-id="49366-127">게스트에 대한 다단계 인증을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="49366-127">To set up multi-factor authentication for Office 365</span></span>
1. <span data-ttu-id="49366-128">Microsoft Azure에서 *조건부 액세스*를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-128">In Microsoft Azure, search for *Conditional access*.</span></span>
2. <span data-ttu-id="49366-129">**조건부 액세스 - 정책** 블레이드에서 **새 정책**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-129">On the **Conditional Access - Policies** blade, click **New policy**.</span></span>
3. <span data-ttu-id="49366-130">**이름** 필드에서 *게스트 MFA*를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-130">In the **Name** field, type *Guest MFA*.</span></span>
4. <span data-ttu-id="49366-131">**할당** 아래에서 **사용자 및 그룹**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-131">Under **Assignments**, click **Users and groups**.</span></span>
5. <span data-ttu-id="49366-132">**사용자 및 그룹** 블레이드에서 **사용자 및 그룹 선택**을 선택하고 **모든 게스트 및 외부 사용자** 확인란을 선택한 후 **완료**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-132">On the **Users and groups** blade, select **Select users and groups**, select the **All guests and external users** check box, and then click **Done**.</span></span>
4. <span data-ttu-id="49366-133">**액세스 제어** 아래에서 **허용**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-133">Under **Access controls**, click **Grant**.</span></span>
5. <span data-ttu-id="49366-134">**허용** 블레이드에서 **다단계 인증 필요** 확인란을 선택한 후, **선택**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-134">On the **Grant** blade, select the **Require multi-factor authentication** check box, and then click **Select**.</span></span>
6. <span data-ttu-id="49366-135">**새로 만들기** 블레이드의 **정책 사용**에서 **설정**을 클릭한 후 **만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-135">On the **New** blade, under **Enable policy**, click **On**, and then click **Create**.</span></span>

<span data-ttu-id="49366-136">이제 게스트는 공유 콘텐츠, 사이트 또는 팀에 액세스하기 전에 다단계 인증에 등록해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-136">Now, guest will be required to enroll in multi-factor authentication before they can access shared content, sites, or teams.</span></span>

### <a name="more-information"></a><span data-ttu-id="49366-137">추가 정보</span><span class="sxs-lookup"><span data-stu-id="49366-137">More information</span></span>

[<span data-ttu-id="49366-138">클라우드 기반 Azure 다단계 인증 배포 계획</span><span class="sxs-lookup"><span data-stu-id="49366-138">Planning a cloud-based Azure Multi-Factor Authentication deployment</span></span>](https://docs.microsoft.com/azure/active-directory/authentication/howto-mfa-getstarted)

## <a name="set-up-a-terms-of-use-for-guests"></a><span data-ttu-id="49366-139">게스트에 대한 사용 약관 설정</span><span class="sxs-lookup"><span data-stu-id="49366-139">Set up a terms of use for guests</span></span>

<span data-ttu-id="49366-140">게스트 사용자는 조직의 비공개 계약 또는 다른 법률 계약에 서명을 하지 않는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="49366-140">Often times guest users may not have signed non-disclosure agreements or other legal agreements with your organization.</span></span> <span data-ttu-id="49366-141">게스트에게 공유된 파일에 액세스하기 전에 사용 약관이 동의하도록 요구할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49366-141">You can require guests to agree to a terms of use before accessing files that are shared with them.</span></span> <span data-ttu-id="49366-142">처음 공유 파일 또는 사이트에 액세스하려고 시도할 때 사용 약관이 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49366-142">The terms of use can be displayed the first time they attempt to access a shared file or site.</span></span>

<span data-ttu-id="49366-143">사용 약관을 만들려면 먼저 Word 또는 다른 작성 프로그램에서 문서를 만든 후에 .pdf 파일로 저장해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-143">To create a terms of use, you first need to create the document in Word or another authoring program, and then save it as a .pdf file.</span></span> <span data-ttu-id="49366-144">그런 다음 이 파일을 Azure AD에 업로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49366-144">This file can then be uploaded to Azure AD.</span></span>

<span data-ttu-id="49366-145">Azure AD 사용 약관을 만들려면</span><span class="sxs-lookup"><span data-stu-id="49366-145">To create an Azure AD terms of use</span></span>
1. <span data-ttu-id="49366-146">Azure에 전역 관리자, 보안 관리자 또는 조건부 액세스 관리자로 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-146">Sign in to Azure as a Global Administrator, Security Administrator, or Conditional Access Administrator.</span></span>
2. <span data-ttu-id="49366-147">[사용 약관](https://aka.ms/catou)으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-147">Navigate to [Terms of use](https://aka.ms/catou).</span></span>
3. <span data-ttu-id="49366-148">**새 사용 약관**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-148">Click **New terms**.</span></span></br>
   <span data-ttu-id="49366-149">![Azure AD 새 사용 약관 설정 스크린샷](media/azure-ad-guest-terms-of-use.png)</span><span class="sxs-lookup"><span data-stu-id="49366-149">![Screenshot of Azure AD new terms of use settings](media/azure-ad-guest-terms-of-use.png)</span></span>
4. <span data-ttu-id="49366-150">**이름** 및 **디스플레이 이름** 상자에 *게스트 사용 약관*을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-150">In the **Name** and **Display name** boxes, type *Guest terms of use*.</span></span>
6. <span data-ttu-id="49366-151">**사용 약관 문서**의 경우 작성한 pdf 파일을 찾아 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-151">For **Terms of use document**, browse to the pdf file that you created and select it.</span></span>
7. <span data-ttu-id="49366-152">사용 약관 문서의 언어를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-152">Select the language for your terms of use document.</span></span>
8. <span data-ttu-id="49366-153">**사용자가 사용 약관을 확장해야 함**을 **켜기**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-153">Set **Require users to expand the terms of use** to **On**.</span></span>
9. <span data-ttu-id="49366-154">**조건부 액세스**의 **조건부 액세스 정책 템플릿으로 적용** 목록에서 **나중에 조건부 액세스 정책 만들기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-154">Under **Conditional Access**, in the **Enforce with Conditional Access policy template** list choose **Create conditional access policy later**.</span></span>
10. <span data-ttu-id="49366-155">**만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-155">Click **Create**.</span></span>

<span data-ttu-id="49366-156">사용 약관을 만들었으면 다음 단계는 게스트 사용자에게 사용 약관을 표시하는 조건부 액세스 정책을 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="49366-156">Once you've created the terms of use, the next step is to create a conditional access policy that displays the terms of use to guest users.</span></span>

<span data-ttu-id="49366-157">조건부 액세스 정책을 만들려면</span><span class="sxs-lookup"><span data-stu-id="49366-157">To create a conditional access policy</span></span>
1. <span data-ttu-id="49366-158">Microsoft Azure에서 *조건부 액세스*를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-158">In Microsoft Azure, search for *Conditional access*.</span></span>
2. <span data-ttu-id="49366-159">**조건부 액세스 - 정책** 블레이드에서 **새 정책**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-159">On the **Conditional Access - Policies** blade, click **New policy**.</span></span>
3. <span data-ttu-id="49366-160">**이름** 상자에서 *게스트 사용자 사용 약관 정책*을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-160">In the **Name** box, type *Guest user terms of use policy*.</span></span>
4. <span data-ttu-id="49366-161">**할당** 아래에서 **사용자 및 그룹**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-161">Under **Assignments**, click **Users and groups**.</span></span>
5. <span data-ttu-id="49366-162">**사용자 및 그룹** 블레이드에서 **사용자 및 그룹 선택**을 선택하고 **모든 게스트 및 외부 사용자** 확인란을 선택한 후 **완료**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-162">On the **Users and groups** blade, select **Select users and groups**, select the **All guests and external users** check box, and then click **Done**.</span></span>
6. <span data-ttu-id="49366-163">**할당**에서 **클라우드 앱 또는 작업**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-163">Under **Assignments**, click **Cloud apps or actions**.</span></span>
7. <span data-ttu-id="49366-164">**포함** 탭에서 **앱 선택**을 선택한 후 **선택**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-164">On the **Include** tab, select **Select apps**, and then click **Select**.</span></span>
8. <span data-ttu-id="49366-165">**선택** 블레이드에서 **Microsoft Teams**, **Office 365 SharePoint Online**, 및 **Outlook Groups**를 선택한 후 **선택**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-165">On the **Select** blade, select **Microsoft Teams**, **Office 365 SharePoint Online**, and **Outlook Groups**, and then click **Select**.</span></span>
9. <span data-ttu-id="49366-166">**클라우드 앱 및 작업** 블레이드에서 **완료**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-166">On the **Cloud apps or actions** blade, click **Done**.</span></span>
10. <span data-ttu-id="49366-167">**액세스 제어** 아래에서 **허용**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-167">Under **Access controls**, click **Grant**.</span></span>
11. <span data-ttu-id="49366-168">**허용** 블레이드에서 **게스트 사용 약관**을 선택한 후 **선택**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-168">On the **Grant** blade, select **Guest terms of use**, and then click **Select**.</span></span>
12. <span data-ttu-id="49366-169">**새로 만들기** 블레이드의 **정책 사용**에서 **설정**을 클릭한 후 **만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-169">On the **New** blade, under **Enable policy**, click **On**, and then click **Create**.</span></span>

<span data-ttu-id="49366-170">이제 게스트 사용자가 처음으로 콘텐츠나 조직의 팀 또는 사이트에 액세스하려고 하면 사용 약관을 수락해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-170">Now, the first time a guest user attempts to access content or a team or site in your organization, they will be required to accept the terms of use.</span></span>

### <a name="more-information"></a><span data-ttu-id="49366-171">추가 정보</span><span class="sxs-lookup"><span data-stu-id="49366-171">More information</span></span>
[<span data-ttu-id="49366-172">Azure Active Directory 사용 약관</span><span class="sxs-lookup"><span data-stu-id="49366-172">Azure Active Directory terms of use</span></span>](https://docs.microsoft.com/azure/active-directory/conditional-access/terms-of-use)

## <a name="set-up-guest-access-reviews"></a><span data-ttu-id="49366-173">게스트 액세스 검토 설정</span><span class="sxs-lookup"><span data-stu-id="49366-173">Set up guest access reviews</span></span>

<span data-ttu-id="49366-174">Azure AD의 액세스 검토로 다양한 팀과 그룹에 대한 주기적 사용자 액세스 검토를 자동화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49366-174">With access reviews in Azure AD, you can automate a periodic review of user access to various teams and groups.</span></span> <span data-ttu-id="49366-175">특히 게스트에 대해 액세스 검토를 요청하여 게스트 사용자가 필요 이상으로 오랫동안 조직의 중요한 정보에 대한 액세스 권한을 유지하지 않도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49366-175">By requiring an access review for guests specifically, you can help ensure guest users do not retain access to your organization's sensitive information for longer than is necessary.</span></span>

<span data-ttu-id="49366-176">액세스 검토는 프로그램으로 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49366-176">Access reviews can be organized into programs.</span></span> <span data-ttu-id="49366-177">프로그램은 보고 및 감사 목적으로 액세스 검토를 구성하는 데 사용할 수 있는 유사한 액세스 검토 그룹입니다.</span><span class="sxs-lookup"><span data-stu-id="49366-177">A program is a grouping of similar access reviews that can be used to organize access reviews for reporting and auditing purposes.</span></span>

<span data-ttu-id="49366-178">이 예제에서는 게스트 액세스 검토를 위한 프로그램을 만들어 봅니다.</span><span class="sxs-lookup"><span data-stu-id="49366-178">In this example, we'll create a program for guest access reviews.</span></span>

<span data-ttu-id="49366-179">프로그램을 만들려면</span><span class="sxs-lookup"><span data-stu-id="49366-179">To create a program for the package</span></span>
1. <span data-ttu-id="49366-180">Azure Portal에 로그인하고 [ID 거버넌스 페이지](https://portal.azure.com/#blade/Microsoft_AAD_ERM/DashboardBlade)를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="49366-180">Sign in to the Azure portal and open the [Identity Governance page](https://portal.azure.com/#blade/Microsoft_AAD_ERM/DashboardBlade).</span></span>
2. <span data-ttu-id="49366-181">왼쪽 메뉴에서 **프로그램**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-181">In the left menu, click **Programs**</span></span>
3. <span data-ttu-id="49366-182">**새 프로그램**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-182">Click **New program**.</span></span>
4. <span data-ttu-id="49366-183">**이름** 상자에 *게스트 액세스 검토 프로그램*을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-183">In the **Name** box, type *Guest access review program*.</span></span>
5. <span data-ttu-id="49366-184">**설명** 상자에 *게스트 액세스 검토를 위한 프로그램*을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-184">In the **Description** box, type *Program for guest access reviews*.</span></span>
6. <span data-ttu-id="49366-185">**만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-185">Click **Create**.</span></span>

<span data-ttu-id="49366-186">프로그램이 만들어지면 게스트 액세스 검토를 만들고 프로그램에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49366-186">Once the program has been created, we can create a guest access review and associate it with the program.</span></span>

<span data-ttu-id="49366-187">게스트 사용자 액세스 검토를 설정하려면</span><span class="sxs-lookup"><span data-stu-id="49366-187">To set up a guest user access review</span></span>
1. <span data-ttu-id="49366-188">[ID 거버넌스 페이지](https://portal.azure.com/#blade/Microsoft_AAD_ERM/DashboardBlade)의 왼쪽 메뉴에서 **액세스 검토**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-188">On the [Identity Governance page](https://portal.azure.com/#blade/Microsoft_AAD_ERM/DashboardBlade), in the left menu, click **Access reviews**.</span></span>
2. <span data-ttu-id="49366-189">**새 액세스 검토**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-189">Click **New access review**.</span></span></br>
   <span data-ttu-id="49366-190">![Azure AD 액세스 검토 설정 스크린샷](media/azure-ad-create-access-review.png)</span><span class="sxs-lookup"><span data-stu-id="49366-190">![Screenshot of Azure AD access review settings](media/azure-ad-create-access-review.png)</span></span>
3. <span data-ttu-id="49366-191">**이름** 상자에 *분기별 게스트 액세스 검토*를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-191">In the **Name** box, type *Quarterly guest access review*.</span></span>
4. <span data-ttu-id="49366-192">**빈도**는 **분기별**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-192">For **Frequency**, choose **Quarterly**.</span></span>
5. <span data-ttu-id="49366-193">**종료**는 **안 함**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-193">For **End**, choose **Never**.</span></span>
6. <span data-ttu-id="49366-194">**범위**는 **게스트 사용자만**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-194">For **Scope**, choose **Guest users only**.</span></span>
7. <span data-ttu-id="49366-195">**그룹**을 클릭하고 액세스 검토에 포함하려는 그룹을 선택한 후 **선택**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-195">Click **Group**, select the groups that you want to include in the access review, and then click **Select**.</span></span>
8. <span data-ttu-id="49366-196">**프로그램** 아래에서 **프로그램에 연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-196">Under **Programs**, click **Link to program**.</span></span>
9. <span data-ttu-id="49366-197">**프로그램 선택** 블레이드에서 **게스트 액세스 검토 프로그램**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-197">On the **Select a program** blade, choose **Guest access review program**</span></span>
10. <span data-ttu-id="49366-198">**시작**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-198">Click **Start**</span></span>

<span data-ttu-id="49366-199">각 지정 그룹에 대해 별도의 액세스 검토를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="49366-199">A separate access review is created for each group that you specify.</span></span> <span data-ttu-id="49366-200">각 그룹의 그룹 소유자는 해당 그룹에 대한 게스트 액세스를 승인 또는 거부하기 위한 이메일을 분기별로 받게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="49366-200">Group owners of each groups will be emailed quarterly to approve or deny guest access to their groups.</span></span>

<span data-ttu-id="49366-201">게스트가 팀이나 그룹에, 또는 개별 파일 및 폴더에 대한 액세스 권한을 받을 수 있음에 주의하는 것이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-201">It's important to note that guests can be given access to teams or groups, or to individual files and folders.</span></span> <span data-ttu-id="49366-202">파일 및 폴더에 대한 액세스 권한을 주면 게스트가 특정 그룹에 추가되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49366-202">When given access to files and folders, guests may not be added to any particular group.</span></span> <span data-ttu-id="49366-203">팀이나 그룹에 속하지 않은 게스트 사용자에 대한 액세스 검토를 수행하려는 경우 모든 게스트가 포함되도록 Azure AD에서 동적 그룹을 만든 후에 해당 그룹에 대한 액세스 검토를 만들면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="49366-203">If you want to do access reviews on guest users who don't belong to a team or group, you can create a dynamic group in Azure AD to contain all guests and then create an access review for that group.</span></span>

### <a name="more-information"></a><span data-ttu-id="49366-204">추가 정보</span><span class="sxs-lookup"><span data-stu-id="49366-204">More information</span></span>
[<span data-ttu-id="49366-205">Azure AD 액세스 검토를 사용하여 게스트 액세스 관리</span><span class="sxs-lookup"><span data-stu-id="49366-205">Manage guest access with Azure AD access reviews</span></span>](https://docs.microsoft.com/azure/active-directory/governance/manage-guest-access-with-access-reviews)

[<span data-ttu-id="49366-206">Azure AD 액세스 검토에서 그룹 또는 애플리케이션에 대한 액세스 검토 만들기</span><span class="sxs-lookup"><span data-stu-id="49366-206">Create an access review of groups or applications in Azure AD access reviews</span></span>](https://docs.microsoft.com/azure/active-directory/governance/create-access-review)

## <a name="set-up-web-only-access-for-guest-users"></a><span data-ttu-id="49366-207">게스트 사용자가 웹에만 액세스할 수 있게 설정</span><span class="sxs-lookup"><span data-stu-id="49366-207">Set up web-only access for guest users</span></span>

<span data-ttu-id="49366-208">게스트 사용자가 웹 브라우저만 사용하여 팀, 사이트 및 파일에 액세스하게 하면 공격 영역을 줄이고 관리가 용이해지게 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49366-208">You can reduce your attack surface and ease administration by requiring guest users to access your teams, sites, and files by using a web browser only.</span></span> <span data-ttu-id="49366-209">이는 Azure AD 조건부 액세스 정책으로 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="49366-209">This is done with an Azure AD conditional access policy.</span></span>

<span data-ttu-id="49366-210">게스트가 웹에만 액세스하도록 제한하려면</span><span class="sxs-lookup"><span data-stu-id="49366-210">To restrict guests to web-ony access</span></span>
1. <span data-ttu-id="49366-211">Microsoft Azure에서 *조건부 액세스*를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-211">In Microsoft Azure, search for *Conditional access*.</span></span>
2. <span data-ttu-id="49366-212">**조건부 액세스 - 정책** 블레이드에서 **새 정책**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-212">On the **Conditional Access - Policies** blade, click **New policy**.</span></span>
3. <span data-ttu-id="49366-213">**이름** 상자에 *게스트 사용자 사용 약관 정책*을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-213">In the **Name** box, type *Guest user browser access*.</span></span>
4. <span data-ttu-id="49366-214">**할당** 아래에서 **사용자 및 그룹**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-214">Under **Assignments**, click **Users and groups**.</span></span>
5. <span data-ttu-id="49366-215">**사용자 및 그룹** 블레이드에서 **사용자 및 그룹 선택**을 선택하고 **모든 게스트 및 외부 사용자** 확인란을 선택한 후 **완료**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-215">On the **Users and groups** blade, select **Select users and groups**, select the **All guests and external users** check box, and then click **Done**.</span></span>
6. <span data-ttu-id="49366-216">**할당**에서 **클라우드 앱 또는 작업**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-216">Under **Assignments**, click **Cloud apps or actions**.</span></span>
7. <span data-ttu-id="49366-217">**포함** 탭에서 **앱 선택**을 선택한 후 **선택**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-217">On the **Include** tab, select **Select apps**, and then click **Select**.</span></span>
8. <span data-ttu-id="49366-218">**선택** 블레이드에서 **Microsoft Teams**, **Office 365 SharePoint Online**, 및 **Outlook Groups**를 선택한 후 **선택**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-218">On the **Select** blade, select **Microsoft Teams**, **Office 365 SharePoint Online**, and **Outlook Groups**, and then click **Select**.</span></span>
9. <span data-ttu-id="49366-219">**클라우드 앱 및 작업** 블레이드에서 **완료**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-219">On the **Cloud apps or actions** blade, click **Done**.</span></span>
10. <span data-ttu-id="49366-220">**할당** 아래에서 **조건**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-220">Under **Assignments**, click **Conditions**.</span></span>
11. <span data-ttu-id="49366-221">**조건** 블레이드에서 **클라이언트 앱**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-221">On the **Conditions** blade, click **Client apps**.</span></span>
12. <span data-ttu-id="49366-222">**클라이언트 앱** 블레이드에서 **구성**의 경우 **예**를 클릭하고 **모바일 앱 및 데스크톱 클라이언트**와 **최신 인증 클라이언트** 설정을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-222">On the **Client apps** blade, click **Yes** for **Configure**, and then select the **Mobile apps and desktop clients** and **Modern authentication clients** settings.</span></span></br>
    <span data-ttu-id="49366-223">![Azure AD 조건부 액세스 클라이언트 앱 설정 스크린샷](media/azure-ad-conditional-access-client-mobile.png)</span><span class="sxs-lookup"><span data-stu-id="49366-223">![Screenshot of Azure AD conditional access client apps settings](media/azure-ad-conditional-access-client-mobile.png)</span></span>
13. <span data-ttu-id="49366-224">**완료**를 클릭한 후 **조건** 블레이드에서 다시 **완료**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-224">Click **Done**, and then on the **Conditions** blade, click **Done** again.</span></span>
14. <span data-ttu-id="49366-225">**액세스 제어** 아래에서 **허용**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-225">Under **Access controls**, click **Grant**.</span></span>
15. <span data-ttu-id="49366-226">**허용** 블레이드에서 **디바이스를 준수 상태로 표시해야 함** 및 **하이브리드 Azure AD 조인 디바이스 필요**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-226">On the **Grant** blade, select **Require device to be marked as compliant** and **Require Hybrid Azure AD joined device**.</span></span>
16. <span data-ttu-id="49366-227">**다중 컨트롤의 경우** 아래에서 **선택한 컨트롤 중 하나 필요**를 선택한 후 **선택**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-227">Under **For multiple controls**, select **Require one of the selected controls**, and then click **Select**.</span></span>
17. <span data-ttu-id="49366-228">**새로 만들기** 블레이드의 **정책 사용**에서 **설정**을 클릭한 후 **만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-228">On the **New** blade, under **Enable policy**, click **On**, and then click **Create**.</span></span>

## <a name="configure-a-session-timeout-for-guest-users"></a><span data-ttu-id="49366-229">게스트 사용자에 대한 세션 시간 제한 구성</span><span class="sxs-lookup"><span data-stu-id="49366-229">Configure a session timeout for guest users</span></span>

<span data-ttu-id="49366-230">게스트가 정기적으로 인증하도록 요구하면 게스트 사용자의 장치가 보안이 유지되지 않을 경우 조직의 콘텐츠에 알 수 없는 사용자가 액세스할 가능성이 줄어들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49366-230">Requiring guests to authenticate on a regular basis can reduce the possibility of unknown users accessing your organization's content if a guest user's device isn't kept secure.</span></span> <span data-ttu-id="49366-231">Azure AD에서 게스트 사용자에 대해 세션 시간 제한 조건부 액세스 정책을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49366-231">You can configure a session timeout conditional access policy for guest users in Azure AD.</span></span>

<span data-ttu-id="49366-232">게스트 세션 시간 제한 정책을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="49366-232">To configure a guest session timeout policy</span></span>
1. <span data-ttu-id="49366-233">Microsoft Azure에서 *조건부 액세스*를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-233">In Microsoft Azure, search for *Conditional access*.</span></span>
2. <span data-ttu-id="49366-234">**조건부 액세스 - 정책** 블레이드에서 **새 정책**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-234">On the **Conditional Access - Policies** blade, click **New policy**.</span></span>
3. <span data-ttu-id="49366-235">**이름** 상자에 *게스트 세션 시간 제한*을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-235">In the **Name** box, type *Guest session timeout*.</span></span>
4. <span data-ttu-id="49366-236">**할당** 아래에서 **사용자 및 그룹**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-236">Under **Assignments**, click **Users and groups**.</span></span>
5. <span data-ttu-id="49366-237">**사용자 및 그룹** 블레이드에서 **사용자 및 그룹 선택**을 선택하고 **모든 게스트 및 외부 사용자** 확인란을 선택한 후 **완료**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-237">On the **Users and groups** blade, select **Select users and groups**, select the **All guests and external users** check box, and then click **Done**.</span></span>
6. <span data-ttu-id="49366-238">**할당**에서 **클라우드 앱 또는 작업**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-238">Under **Assignments**, click **Cloud apps or actions**.</span></span>
7. <span data-ttu-id="49366-239">**포함** 탭에서 **앱 선택**을 선택한 후 **선택**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-239">On the **Include** tab, select **Select apps**, and then click **Select**.</span></span>
8. <span data-ttu-id="49366-240">**선택** 블레이드에서 **Microsoft Teams**, **Office 365 SharePoint Online**, 및 **Outlook Groups**를 선택한 후 **선택**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-240">On the **Select** blade, select **Microsoft Teams**, **Office 365 SharePoint Online**, and **Outlook Groups**, and then click **Select**.</span></span>
9. <span data-ttu-id="49366-241">**클라우드 앱 및 작업** 블레이드에서 **완료**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-241">On the **Cloud apps or actions** blade, click **Done**.</span></span>
10. <span data-ttu-id="49366-242">**액세스 제어** 아래에서 **세션**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-242">Under **Access controls**, click **Session**.</span></span>
11. <span data-ttu-id="49366-243">**세션** 블레이드에서 **로그인 빈도**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-243">On the **Session** blade, select **Sign-in frequency**.</span></span>
12. <span data-ttu-id="49366-244">시간에서 **1**과 **일**을 선택한 후 **선택**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-244">Select **1** and **Days** for the time period, and then click **Select**.</span></span>
13. <span data-ttu-id="49366-245">**새로 만들기** 블레이드의 **정책 사용**에서 **설정**을 클릭한 후 **만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-245">On the **New** blade, under **Enable policy**, click **On**, and then click **Create**.</span></span>

## <a name="create-sensitivity-labels"></a><span data-ttu-id="49366-246">민감도 레이블 만들기</span><span class="sxs-lookup"><span data-stu-id="49366-246">Create sensitivity labels</span></span>

<span data-ttu-id="49366-247">민감도 레이블은 조직의 정보를 분류하고 보호하는 데 다양한 방식으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49366-247">Sensitivity labels can be used in a variety of ways to classify and protect your organization's information.</span></span> <span data-ttu-id="49366-248">이 예제에서는 공유 파일 및 폴더에 대한 게스트 액세스를 관리하는 데 레이블이 어떻게 사용될 수 있는지 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="49366-248">In this example, we'll look at how labels can be used to help you manage guest access to shared files and folders.</span></span>

<span data-ttu-id="49366-249">먼저 Microsoft 365 규정 준수 센터에서 다음의 3가지 민감도 레이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="49366-249">First, we'll create three sensitivity labels in the Microsoft 365 Compliance Center:</span></span>

- <span data-ttu-id="49366-250">일반</span><span class="sxs-lookup"><span data-stu-id="49366-250">General</span></span>
- <span data-ttu-id="49366-251">기밀</span><span class="sxs-lookup"><span data-stu-id="49366-251">Confidential</span></span>
- <span data-ttu-id="49366-252">극비</span><span class="sxs-lookup"><span data-stu-id="49366-252">Highly Confidential</span></span>

<span data-ttu-id="49366-253">다음 절차를 통해 *일반* 및 *기밀* 레이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="49366-253">Use the following procedure to create the *General* and *Confidential* labels.</span></span>

<span data-ttu-id="49366-254">분류 레이블(일반 및 기밀)을 만들려면</span><span class="sxs-lookup"><span data-stu-id="49366-254">To create a classification label (General and Confidential)</span></span>
1. <span data-ttu-id="49366-255">[Microsoft 365 규정 준수 센터](https://compliance.microsoft.com)의 왼쪽 탐색에서 **분류**를 확장한 후 **민감도 레이블**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-255">In the [Microsoft 365 Compliance Center](https://compliance.microsoft.com), in the left navigation, expand **Classification**, and then click **Sensitivity labels**.</span></span>
2. <span data-ttu-id="49366-256">**레이블 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-256">Click **Retention labels > Create a label**.</span></span>
3. <span data-ttu-id="49366-257">**레이블 이름**에 *일반* 또는 *기밀*을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-257">In **Label name**, type *General* or *Confidential*.</span></span>
4. <span data-ttu-id="49366-258">**도구 설명**에 *직원, 게스트 및 파트너와 공유할 수 있는 일반 정보* 또는 *기밀 정보. 직원과 인증된 게스트와만 공유*라고 입력한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-258">In **Tooltip**, type *General information that can be shared with employees, guests, and partners* or *Confidential information. Share only with employees and authorized guests*, and then click **Next**.</span></span>
5. <span data-ttu-id="49366-259">암호화를 **끄기**로 두고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-259">Leave encryption **Off** and click **Next**.</span></span>
6. <span data-ttu-id="49366-260">콘텐츠 표시를 **끄기**로 두고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-260">Leave content marking **Off** and click **Next**.</span></span>
7. <span data-ttu-id="49366-261">엔드포인트 데이터 손실 방지를 **끄기**로 두고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-261">Leave endpoint data loss prevention **Off** and click **Next**.</span></span>
8. <span data-ttu-id="49366-262">자동 레이블 지정을 **끄기**로 두고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-262">Leave auto labeling **Off** and click **Next**.</span></span>
9. <span data-ttu-id="49366-263">**만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-263">Click **Create**.</span></span>

<span data-ttu-id="49366-264">*극비* 레이블의 경우 레이블과 함께 문서의 자동 워터마킹을 더하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="49366-264">With the *Highly Confidential* label, we'll add automatic watermarking of documents with the label.</span></span>

<span data-ttu-id="49366-265">분류 레이블(극비)을 만들려면</span><span class="sxs-lookup"><span data-stu-id="49366-265">To create a classification label (Highly confidential)</span></span>
1. <span data-ttu-id="49366-266">**레이블 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-266">Click **Retention labels > Create a label**.</span></span>
2. <span data-ttu-id="49366-267">**레이블 이름**에 *극비*를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-267">In **Label name**, type *Highly confidential*.</span></span>
3. <span data-ttu-id="49366-268">**도구 설명**에 *극비 정보. 게스트와 공유하지 않음*을 입력한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-268">In **Tooltip**, type *Highly confidential information. Do not share with guests*, and then click **Next**.</span></span>
4. <span data-ttu-id="49366-269">암호화를 **끄기**로 두고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-269">Leave encryption **Off** and click **Next**.</span></span>
5. <span data-ttu-id="49366-270">콘텐츠 표시를 **켜기**로 설정하고 **헤더 추가** 확인란을 선택한 후 **텍스트 사용자 지정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-270">Turn content marking **On**, select the **Add a header** check box, and then click **Customize text**.</span></span>
6. <span data-ttu-id="49366-271">헤더 텍스트에 *극비*를 입력하고 **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-271">Type *Highly confidential* for the header text and click **Save**.</span></span>
7. <span data-ttu-id="49366-272">**콘텐츠 표시** 페이지에서 콘텐츠 표시를 **켜기**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-272">On the **Content marking** page, turn content marking **On**.</span></span>
8. <span data-ttu-id="49366-273">**워터마크 추가** 확인란을 선택한 후 **텍스트 사용자 지정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-273">Select the **Add a watermark** check box, and then click **Customize text**.</span></span>
9. <span data-ttu-id="49366-274">**워터마크 텍스트**에 *극비*를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-274">For **Watermark text**, type *Highly Confidential*.</span></span>
10. <span data-ttu-id="49366-275">**글꼴 크기**에 *24*를 입력한 후 **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-275">Type *24* for **Font size**, and then click **Save**.</span></span>
11. <span data-ttu-id="49366-276">**콘텐츠 표시** 페이지에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-276">On the **Welcome** page, click **Next**.</span></span>
12. <span data-ttu-id="49366-277">엔드포인트 데이터 손실 방지를 **끄기**로 두고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-277">Leave endpoint data loss prevention **Off** and click **Next**.</span></span>
13. <span data-ttu-id="49366-278">자동 레이블 지정을 **끄기**로 두고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-278">Leave auto labeling **Off** and click **Next**.</span></span>
14. <span data-ttu-id="49366-279">**만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-279">Click **Create**.</span></span>

![Microsoft 365 규정 준수 센터의 민감도 레이블 스크린샷](media/microsoft-365-sharing-sensitivity-labels.png)

<span data-ttu-id="49366-281">레이블을 만들었으면 다음 단계는 게시하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="49366-281">Once you've created the labels, the next step is to publish them.</span></span> 

<span data-ttu-id="49366-282">레이블을 게시하려면</span><span class="sxs-lookup"><span data-stu-id="49366-282">To publish labels</span></span>
1. <span data-ttu-id="49366-283">**민감도 레이블** 페이지에서 **레이블 게시**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-283">On the **Sensitivity labels** page, click **Publish labels**.</span></span>
2. <span data-ttu-id="49366-284">**게시할 레이블 선택**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-284">Click **Choose labels to publish**.</span></span>
3. <span data-ttu-id="49366-285">**추가**를 클릭하고 만든 레이블을 선택한 후 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-285">Click **Add**, select the backup file that you created in step 3, and then click **OK**.</span></span>
4. <span data-ttu-id="49366-286">**완료**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-286">Click **Done**.</span></span>
5. <span data-ttu-id="49366-287">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-287">Click **Next**.</span></span>
6. <span data-ttu-id="49366-288">사용자와 그룹이 **모두**로 설정되도록 두고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-288">Leave the users and groups set to **All** and click **Next**.</span></span>
7. <span data-ttu-id="49366-289">**문서 및 이메일에 기본적으로 이 레이블 적용** 목록에서 **일반**을 선택한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-289">In the **Apply this label by default to documents and email** list, choose **General**, and then click **Next**.</span></span>
8. <span data-ttu-id="49366-290">**정책 설정** 페이지에서 이름에 *문서 민감도*를 입력한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-290">On the **Policy settings** page, type *Document sensitivity* for the name, and then click **Next**.</span></span>
9. <span data-ttu-id="49366-291">**게시**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-291">Click **Publish**.</span></span>

<span data-ttu-id="49366-292">레이블이 게시되면 Office 데스크톱 앱의 사용자에게 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="49366-292">With the labels published, they're available to users of Office desktop apps.</span></span> <span data-ttu-id="49366-293">사용자가 **극비** 레이블을 적용하면 워터마크가 자동으로 문서에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="49366-293">When users apply the **Highly Confidential** label, a watermark is automatically added to the document.</span></span>

### <a name="more-information"></a><span data-ttu-id="49366-294">추가 정보</span><span class="sxs-lookup"><span data-stu-id="49366-294">More information</span></span>
[<span data-ttu-id="49366-295">민감도 레이블 개요</span><span class="sxs-lookup"><span data-stu-id="49366-295">Overview of sensitivity labels</span></span>](https://docs.microsoft.com/Office365/SecurityCompliance/sensitivity-labels)

## <a name="create-a-sensitive-information-type-for-a-highly-confidential-project"></a><span data-ttu-id="49366-296">극비 프로젝트에 대한 중요한 정보 유형 만들기</span><span class="sxs-lookup"><span data-stu-id="49366-296">Create a sensitive information type for a highly confidential project</span></span>

<span data-ttu-id="49366-297">중요한 정보 유형은 규정 준수 요구 사항을 적용하기 위해 정책 워크플로에 사용할 수 있는 미리 정의된 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="49366-297">Sensitive information types are predefined strings that can be used in policy workflows to enforce compliance requirements.</span></span> <span data-ttu-id="49366-298">Microsoft 365 규정 준수 센터는 운전면허증 번호, 신용카드 번호, 은행 계좌 번호 등을 포함한 100개 넘는 중요한 정보 유형을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-298">The Microsoft 365 Compliance Center comes with over one hundred sensitive information types, including driver's license numbers, credit card numbers, bank account numbers, etc.</span></span>

<span data-ttu-id="49366-299">조직에 특정화된 콘텐츠를 관리하기 위해 사용자 지정 중요한 정보 유형을 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49366-299">You can create custom sensitive information types to help manage content specific to your organization.</span></span> <span data-ttu-id="49366-300">이 예제에서는 극비 프로젝트에 대한 사용자 지정 중요한 정보 유형을 만들어봅니다.</span><span class="sxs-lookup"><span data-stu-id="49366-300">In this example, we'll create a custom sensitive information type for a highly confidential project.</span></span> <span data-ttu-id="49366-301">그런 다음 이 중요한 정보 유형을 사용하여 분류 레이블에 자동으로 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49366-301">We can then use this sensitive information type to automatically apply a classification label.</span></span>

<span data-ttu-id="49366-302">사용자 지정 중요한 정보 유형을 만들려면</span><span class="sxs-lookup"><span data-stu-id="49366-302">To create a sensitive information type</span></span>
1. <span data-ttu-id="49366-303">[Microsoft 365 규정 준수 센터](https://compliance.microsoft.com)의 왼쪽 탐색에서 **분류**를 확장한 후 **중요한 정보 유형**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-303">In the [Microsoft 365 Compliance Center](https://compliance.microsoft.com), in the left navigation, expand **Classification**, and then click **Sensitive info types**.</span></span>
2. <span data-ttu-id="49366-304">**만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-304">Click **Create**.</span></span>
3. <span data-ttu-id="49366-305">**이름**과 **설명**에 **프로젝트 Saturn**을 입력한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-305">For **Name** and **Description**, type **Project Saturn**, and then click **Next**.</span></span>
4. <span data-ttu-id="49366-306">**요소 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-306">Click **Add an element**.</span></span>
5. <span data-ttu-id="49366-307">**다음이 포함된 콘텐츠 검색** 목록에서 **키워드**를 선택한 후 키워드 상자에 *프로젝트 Saturn*을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-307">On the **Detect content containing** list, select **Keywords**, and then type *Project Saturn* in the keyword box.</span></span>
6. <span data-ttu-id="49366-308">**다음**을 클릭한 후 **마침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-308">Click **Next**, and then click **Finish**.</span></span>
7. <span data-ttu-id="49366-309">중요한 정보 유형을 테스할지 묻는 메시지가 표시되면 **아니요**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-309">If asked if you would like to test the sensitive information type, click **No**.</span></span>

### <a name="more-information"></a><span data-ttu-id="49366-310">추가 정보</span><span class="sxs-lookup"><span data-stu-id="49366-310">More information</span></span>
[<span data-ttu-id="49366-311">사용자 지정 중요한 정보 유형</span><span class="sxs-lookup"><span data-stu-id="49366-311">Custom sensitive information types</span></span>](https://docs.microsoft.com/Office365/SecurityCompliance/custom-sensitive-info-types)

## <a name="create-a-policy-to-assign-a-label-based-on-a-sensitive-information-type"></a><span data-ttu-id="49366-312">중요한 정보 유형을 기반으로 레이블을 할당할 정책 만들기</span><span class="sxs-lookup"><span data-stu-id="49366-312">Create a policy to assign a label based on a sensitive information type</span></span>

<span data-ttu-id="49366-313">중요한 정보 유형을 만들었으면 Microsoft Cloud App Security에서 *프로젝트 Saturn* 문자열이 포함된 문서에 *극비* 레이블을 자동으로 적용할 파일 정책을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49366-313">Once the sensitive information type is created, we can create a file policy in Microsoft Cloud App Security to apply the *Highly Confidential* label to documents that contain the *Project Saturn* string automatically.</span></span>

> [!NOTE]
> <span data-ttu-id="49366-314">Cloud App Security에서 민감도 레이블을 사용할 수 있게 하는 복제 프로세스가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49366-314">There is a replication process that makes sensitivity labels available in Cloud App Security.</span></span> <span data-ttu-id="49366-315">현재는 정책에 사용할 수 있는 레이블이 보이지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49366-315">You may not see the label available for a policy right away.</span></span>

<span data-ttu-id="49366-316">중요한 정보 유형 기반 파일 정책을 만들려면</span><span class="sxs-lookup"><span data-stu-id="49366-316">To create a sensitive information type-based file policy</span></span>
1. <span data-ttu-id="49366-317">[Microsoft Cloud App Security](https://portal.cloudappsecurity.com)를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="49366-317">[Microsoft Cloud App Security](https://portal.cloudappsecurity.com)</span></span>
2. <span data-ttu-id="49366-318">왼쪽 탐색에서 **컨트롤**을 확장한 후 **정책**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-318">In the left navigation, expand **Control**, and then click **Policies**.</span></span>
3. <span data-ttu-id="49366-319">**정책 만들기**를 클릭한 후 **파일 정책**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-319">Click **Create policy**, and then choose **File policy**.</span></span>
4. <span data-ttu-id="49366-320">**파일 이름**에 *프로젝트 Saturn 레이블 지정*을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-320">For **Policy name**, type *Project Saturn labeling*.</span></span>
5. <span data-ttu-id="49366-321">**이 정책이 적용될 파일의 필터 생성** 아래에서 X를 두 번 클릭하여 기본 필터를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-321">Under **Create a filter for the files this policy will act on**, click X twice to delete the default filters.</span></span>
7. <span data-ttu-id="49366-322">**필터 선택** 목록에서 **앱**을 선택한 후 **앱 선택...** 목록에서 **Microsoft SharePoint Online**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-322">In the **Select a filter** list, choose **App**, and then select **Microsoft SharePoint Online** from the **Select apps...** list.</span></span>
8. <span data-ttu-id="49366-323">**검사 방법** 아래에서 **데이터 분류 서비스**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-323">Under **Inspection method**, choose **Data classification service**.</span></span>
9. <span data-ttu-id="49366-324">**검사 유형 선택** 목록에서 **중요한 정보 유형**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-324">On the **Choose inspection type** list, choose **Sensitive information type**.</span></span>
10. <span data-ttu-id="49366-325">*프로젝트 Saturn* 민감도 레이블을 검색하고 선택한 후 **완료**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-325">Search for and select the *Project Saturn* sensitivity label, and then click **Done**.</span></span></br>
   <span data-ttu-id="49366-326">![Cloud App Security 검사 방법 설정 스크린샷](media/mcas-sensitive-info-type-project-saturn.png)</span><span class="sxs-lookup"><span data-stu-id="49366-326">![Screenshot of Cloud App Security inspection method settings](media/mcas-sensitive-info-type-project-saturn.png)</span></span>
11. <span data-ttu-id="49366-327">**거버넌스** 아래에서 **Microsoft SharePoint Online**을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-327">Under **Governance**, expand **Microsoft SharePoint Online**.</span></span>
12. <span data-ttu-id="49366-328">**분류 레이블 적용** 확인란을 선택하고 **극비** 레이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-328">Select the **Apply classification label** check box and select the **Highly Confidential** label.</span></span>
13. <span data-ttu-id="49366-329">**만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-329">Click **Create**.</span></span>

<span data-ttu-id="49366-330">정책이 준비되었으면 사용자가 "프로젝트 Saturn"을 문서에 입력할 경우 Cloud App Security에서 파일을 스캔할 때 *극비* 레이블을 자동으로 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-330">With the policy in place, when a user types "Project Saturn" into a document, Cloud App Security will automatically apply the *Highly Confidential* label when it scans the file.</span></span>

### <a name="more-information"></a><span data-ttu-id="49366-331">추가 정보</span><span class="sxs-lookup"><span data-stu-id="49366-331">More information</span></span>
[<span data-ttu-id="49366-332">파일 정책</span><span class="sxs-lookup"><span data-stu-id="49366-332">File policies</span></span>](https://docs.microsoft.com/cloud-app-security/data-protection-policies)

## <a name="create-a-policy-to-remove-guest-access-to-highly-confidential-files"></a><span data-ttu-id="49366-333">극비 파일에 대한 게스트 액세스 권한을 제거할 정책 만들기</span><span class="sxs-lookup"><span data-stu-id="49366-333">Create a policy to remove guest access to highly confidential files</span></span>

<span data-ttu-id="49366-334">이 문서의 이 예제에서 *극비* 레이블이 지정된 파일은 게스트와 공유하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="49366-334">In the example in this article, files with the *Highly Confidential* label shouldn't be shared with guests.</span></span> <span data-ttu-id="49366-335">Cloud App Security에서 해당 레이블이 지정된 파일의 게스트 액세스 권한을 자동으로 제거하는 파일 정책을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49366-335">We can create a file policy in Cloud App Security that automatically removes guest access from files with that label.</span></span>

<span data-ttu-id="49366-336">이 방법으로 사용자가 이러한 파일을 공유 또는 재공유하는 것을 방지할 수는 없음에 유의하세요.</span><span class="sxs-lookup"><span data-stu-id="49366-336">Note that this doesn't prevent users from sharing or re-sharing these files.</span></span> <span data-ttu-id="49366-337">게스트 공유를 허용하는 사이트에 저장된 파일에 대한 관리 정책을 사용자가 따르도록 하는 데 계속 의존할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49366-337">You're still reliant on your users to follow your governance policies for files that are stored in sites that allow guest sharing.</span></span> <span data-ttu-id="49366-338">하지만 게스트와 공유한 이후 추가된, 기밀 정보가 있는 파일의 게스트 액세스를 제거하는 데는 유용한 도구일 수 있씁니다.</span><span class="sxs-lookup"><span data-stu-id="49366-338">However, this can be a useful tool for removing guest access from files that had confidential information added to them after they were shared with guests.</span></span>

<span data-ttu-id="49366-339">레이블 기반 파일 정책을 만들려면</span><span class="sxs-lookup"><span data-stu-id="49366-339">To create a label-based file policy</span></span>
1. <span data-ttu-id="49366-340">[Microsoft Cloud App Security](https://portal.cloudappsecurity.com)를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="49366-340">[Microsoft Cloud App Security](https://portal.cloudappsecurity.com)</span></span>
2. <span data-ttu-id="49366-341">왼쪽 탐색에서 **컨트롤**을 확장한 후 **정책**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-341">In the left navigation, expand **Control**, and then click **Policies**.</span></span>
3. <span data-ttu-id="49366-342">**정책 만들기**를 클릭한 후 **파일 정책**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-342">Click **Create policy**, and then choose **File policy**.</span></span>
4. <span data-ttu-id="49366-343">**정책 이름**에 *프로젝트 Saturn - 게스트 액세스 제거*를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-343">For **Policy name**, type *Project Saturn - remove guest access*.</span></span>
5. <span data-ttu-id="49366-344">**이 정책이 적용될 파일의 필터 생성** 아래에서 X를 두 번 클릭하여 기본 필터를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-344">Under **Create a filter for the files this policy will act on**, click X twice to delete the default filters.</span></span>
6. <span data-ttu-id="49366-345">**필터 선택** 목록에서 **앱**을 선택한 후 **앱 선택...** 목록에서 **Microsoft SharePoint Online**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-345">In the **Select a filter** list, choose **App**, and then select **Microsoft SharePoint Online** from the **Select apps...** list.</span></span>
7. <span data-ttu-id="49366-346">**필터 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-346">Click **Add a user**.</span></span>
8. <span data-ttu-id="49366-347">**필터 선택** 목록에서 **분류 레이블**을 선택한 후 **필터 선택...** 목록에서 **Azure Information Protection**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-347">In the **Select a filter** list, choose **Classification label**, and then select **Azure Information Protection** from the **Select filter...** list.</span></span>
9. <span data-ttu-id="49366-348">**분류 레이블 선택** 목록에서 **극비**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-348">In the **Select classification label** list, select **Highly Confidential**.</span></span></br>
   <span data-ttu-id="49366-349">![Cloud App Security 정책 필터 설정 스크린샷](media/mcas-sharepoint-confidential-label-filter.png)</span><span class="sxs-lookup"><span data-stu-id="49366-349">![Screenshot of Cloud App Security policy filter settings](media/mcas-sharepoint-confidential-label-filter.png)</span></span>
10. <span data-ttu-id="49366-350">**거버넌스** 아래에서 **Microsoft SharePoint Online**을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-350">Under **Governance**, expand **Microsoft SharePoint Online**.</span></span>
11. <span data-ttu-id="49366-351">**정책 일치 다이제스트를 파일 소유자에게 전송** 및 **외부 사용자 제거** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-351">Select the **Send policy-match digest to file owner** and **Remove external users** check boxes.</span></span>
12. <span data-ttu-id="49366-352">사용자 지정 알림 메시지에는 *이 파일은 극비 항목입니다. 회사 정책상 게스트와 공유하는 것이 금지됩니다.* 를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-352">For the custom notification message, type *This file is highly confidential. Company policy prohibits sharing it with guests*.</span></span>
13. <span data-ttu-id="49366-353">**만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-353">Click **Create**.</span></span>

<span data-ttu-id="49366-354">이 정책은 *특정 사용자* 링크를 사용하여 공유된 파일에 대한 액세스를 제거한다는 것에 주의하는 것이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-354">It's important to note, that this policy removes access for files shared using a *Specific people* link.</span></span> <span data-ttu-id="49366-355">익명(*모든 사용자*) 링크에서 액세스를 제거하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="49366-355">It doesn't remove access from anonymous (*Anyone*) links.</span></span> <span data-ttu-id="49366-356">게스트가 전체 사이트나 팀의 구성원일 경우에도 액세스가 제거되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="49366-356">It also doesn't remove access if the guest is a member of the site or team as a whole.</span></span> <span data-ttu-id="49366-357">게스트 구성원이 포함된 사이트 또는 팀의 극비 문서를 마련할 계획이면 [팀 내 비공개 채널](https://support.office.com/article/60ef929a-4d68-418b-bf4f-5784db184ec9)을 사용하고 비공개 채널의 조직 구성원에게만 허용하는 방법을 고려하세요.</span><span class="sxs-lookup"><span data-stu-id="49366-357">If you plan to have highly confidential documents in a site or team with guest members, consider using [private channels in Teams](https://support.office.com/article/60ef929a-4d68-418b-bf4f-5784db184ec9) and only allowing members of your organization in the private channels.</span></span>

## <a name="test-the-solution"></a><span data-ttu-id="49366-358">솔루션 테스트</span><span class="sxs-lookup"><span data-stu-id="49366-358">Test the solution</span></span>

<span data-ttu-id="49366-359">이 문서에서 설명한 솔루션을 테스트하려면 Word 문서를 만들고 문서 라이브러리에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-359">To test the solution described in this article, create a Word document and save it to a document library.</span></span> <span data-ttu-id="49366-360">게스트 사용자와 파일을 공유합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-360">Share the file with a guest user.</span></span> <span data-ttu-id="49366-361">게스트가 문서에 액세스하려고 하면 다단계 인증에 등록한 후 사용 약관을 수락해야 한다는 요구를 받습니다.</span><span class="sxs-lookup"><span data-stu-id="49366-361">When the guest attempts to access the document, they should be required to enroll in multi-factor authentication, and then accept the terms of use.</span></span>

<span data-ttu-id="49366-362">게스트가 문서에 대한 액세스 권한을 갖게 되면 문서에 *프로젝트 Saturn*을 입력하고 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="49366-362">Once the guest has access to the document, type *Project Saturn* in the document and save it.</span></span> <span data-ttu-id="49366-363">Cloud App Security가 문서를 스캔하면 *극비* 레이블이 적용되고 게스트 사용자가 더 이상 해당 문서에 대해 액세스 권한을 갖지 못하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="49366-363">Once Cloud App Security scans the document, the *Highly Confidential* label should be applied and the guest user should no longer have access to it.</span></span>

<span data-ttu-id="49366-364">이 문서에 설명된 도구를 다양하게 조합하여 사용함으로써 조직에 생산적이면서도 안전한 게스트 공유 환경을 구축할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49366-364">You can use the tools described in this article in various combinations to help create a productive but safe guest sharing environment for your organization.</span></span>

## <a name="see-also"></a><span data-ttu-id="49366-365">참고 항목</span><span class="sxs-lookup"><span data-stu-id="49366-365">See Also</span></span>

[<span data-ttu-id="49366-366">게스트와 공유할 때 파일에 실수로 발생하는 노출을 제한</span><span class="sxs-lookup"><span data-stu-id="49366-366">Limit accidental exposure to files when sharing with guests</span></span>](sharing-limit-accidental-exposure.md)

[<span data-ttu-id="49366-367">익명 사용자와 파일 및 폴더를 공유하는 최상의 방법</span><span class="sxs-lookup"><span data-stu-id="49366-367">Best practices for sharing files and folders with anonymous users</span></span>](best-practices-anonymous-sharing.md)
