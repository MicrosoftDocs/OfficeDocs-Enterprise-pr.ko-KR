---
title: "정치적 캠페인 개발/테스트 환경에 대 한 사용자 및 그룹 구성"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: None
ms.custom: Strat_O365_Enterprise
ms.assetid: 0e22bcf3-bad3-42a4-b44f-276e0cf4790f
description: "요약: 사용자 및 그룹 정치적 캠페인 개발/테스트 환경에 대 한 Office 365 및 Enterprise 이동성 + (EMS) 보안 평가판 구독을 만듭니다."
ms.openlocfilehash: adc5cdfe6d5c0c039ceb1c9068032fe2dae20114
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/09/2018
---
# <a name="configure-groups-and-users-for-a-political-campaign-devtest-environment"></a><span data-ttu-id="e0201-103">정치적 캠페인 개발/테스트 환경에 대 한 사용자 및 그룹 구성</span><span class="sxs-lookup"><span data-stu-id="e0201-103">Configure groups and users for a political campaign dev/test environment</span></span>

 <span data-ttu-id="e0201-104">**요약:** 정치적 캠페인 개발/테스트 환경에 대 한 그룹 사용자와 Office 365 및 Enterprise 이동성 + (EMS) 보안 평가판 구독을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e0201-104">**Summary:** Create Office 365 and Enterprise Mobility + Security (EMS) trial subscriptions with users and groups for a political campaign dev/test environment.</span></span>
  
<span data-ttu-id="e0201-105">이 문서의 지침을 사용 하 여 간소화 된 사용자 계정 및 [정치적 캠페인, 비영리, 및 기타 민첩 한 조직에 대 한 보안 지침 Microsoft](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md) 솔루션에 대 한 그룹을 포함 하는 개발/테스트 환경을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e0201-105">Use the instructions in this article to create a dev/test environment that includes simplified user accounts and groups for the [Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md) solution.</span></span>
  
## <a name="phase-1-create-your-office-365-devtest-environment"></a><span data-ttu-id="e0201-106">1단계: Office 365 개발/테스트 환경 만들기</span><span class="sxs-lookup"><span data-stu-id="e0201-106">Phase 1: Create your Office 365 dev/test environment</span></span>

<span data-ttu-id="e0201-107">이 단계에서 Office 365 e 5 및 Enterprise 이동성 + 정치적 캠페인을 나타내는 가상의 조직에 대 한 보안 (EMS) e 5에 대 한 평가판 구독 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0201-107">In this phase, you obtain trial subscriptions for Office 365 E5 and Enterprise Mobility + Security (EMS) E5 for a fictional organization that represents a political campaign.</span></span>
  
<span data-ttu-id="e0201-108">먼저, [Office 365 개발/테스트 환경](office-365-dev-test-environment.md)중 **2 단계** 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="e0201-108">First, follow the instructions in **Phase 2** of the [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="e0201-109">다음으로, EMS E5 평가판 구독에 등록 하 고 Office 365 평가판 구독와 같은 조직에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0201-109">Next, sign up for the EMS E5 trial subscription and add it to the same organization as your Office 365 trial subscription.</span></span>
  
1. <span data-ttu-id="e0201-p101">평가판 구독의 전역 관리자 계정의 자격 증명을 사용 하 여 Office 365 포털에 필요한 경우에 로그인 합니다. 도움말을 보려면 [Office 365에 로그인 할 위치](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="e0201-p101">If needed, sign in to the Office 365 portal with the credentials of the global administrator account of your trial subscription. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="e0201-112">**Admin** 타일을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0201-112">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="e0201-113">왼쪽 탐색 영역에서 브라우저에서 **Office 관리 센터** 탭을 클릭 **대금 청구 > 구매 서비스**합니다.</span><span class="sxs-lookup"><span data-stu-id="e0201-113">On the **Office Admin center** tab in your browser, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="e0201-p102">**서비스 구매** 페이지 **Enterprise 이동성 + 보안 e 5** 항목을 찾습니다. 마우스 포인터를 올려 하 고 **무료 평가판을 시작**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0201-p102">On the **Purchase services** page, find the **Enterprise Mobility + Security E5** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="e0201-116">**주문 확인** 페이지에서 **지금 시도**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0201-116">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="e0201-117">**순서 확인** 페이지에서 **계속**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0201-117">On the **Order receipt** page, click **Continue**.</span></span>
    
<span data-ttu-id="e0201-118">다음으로, 전역 관리자 계정에 대 한 EMS E5 라이선스를 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0201-118">Next, enable the EMS E5 license for your global administrator account.</span></span>
  
1. <span data-ttu-id="e0201-119">왼쪽 탐색 영역에서 브라우저에서 **Office 365 관리 센터** 탭을 클릭 **사용자 > 활성 사용자**합니다.</span><span class="sxs-lookup"><span data-stu-id="e0201-119">On the **Office 365 Admin center** tab in your browser, in the left navigation, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="e0201-120">전역 관리자 계정을 클릭 하 고 **제품 라이선스**에 대 한 **편집** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0201-120">Click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="e0201-121">**제품 라이선스** 창에서 **엔터프라이즈 이동성 + 보안 e 5** **전환**에 대 한 제품 라이선스 설정, **저장** 을 클릭 하 고 두번 **닫기** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0201-121">On the **Product licenses** pane, turn the product license for **Enterprise Mobility + Security E5** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
## <a name="phase-2-create-and-configure-your-azure-active-directory-ad-groups"></a><span data-ttu-id="e0201-122">2 단계: 그룹 만들기 및 구성 하면 Azure Active Directory (AD)</span><span class="sxs-lookup"><span data-stu-id="e0201-122">Phase 2: Create and configure your Azure Active Directory (AD) groups</span></span>

<span data-ttu-id="e0201-123">이 단계에서 만들고 캠페인에 대 한 Azure AD 그룹을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0201-123">In this phase, you create and configure the Azure AD groups for your campaign.</span></span>
  
<span data-ttu-id="e0201-124">먼저, Azure 포털과 일반적인 정치적 캠페인에 대 한 그룹의 집합을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e0201-124">First, create a set of groups for a typical political campaign with the Azure portal.</span></span>
  
1. <span data-ttu-id="e0201-125">브라우저에서 별도 탭에 있는 [https://portal.azure.com](https://portal.azure.com)에서 Azure 포털으로 이동 합니다. 필요한 경우 Office 365 E5 평가판 구독에 대 한 전역 관리자 계정의 자격 증명을 사용 하 여 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0201-125">On a separate tab in your browser, go to the Azure portal at [https://portal.azure.com](https://portal.azure.com). If needed, sign in with the credentials of the global administrator account for your Office 365 E5 trial subscription.</span></span>
    
2. <span data-ttu-id="e0201-126">Azure 포털에서 클릭 **Azure Active Directory > 사용자 및 그룹 > 모든 그룹**합니다.</span><span class="sxs-lookup"><span data-stu-id="e0201-126">In the Azure portal, click **Azure Active Directory > Users and groups > All groups**.</span></span>
    
3. <span data-ttu-id="e0201-127">이 목록에 각 그룹 이름에 대해 다음 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0201-127">Do the following steps for each group name in this list:</span></span>
    
  - <span data-ttu-id="e0201-128">선임 및 전략적 직원</span><span class="sxs-lookup"><span data-stu-id="e0201-128">Senior and strategic staff</span></span>
    
  - <span data-ttu-id="e0201-129">IT 담당자</span><span class="sxs-lookup"><span data-stu-id="e0201-129">IT staff</span></span>
    
  - <span data-ttu-id="e0201-130">분석 직원</span><span class="sxs-lookup"><span data-stu-id="e0201-130">Analytics staff</span></span>
    
  - <span data-ttu-id="e0201-131">일반 핵심 직원</span><span class="sxs-lookup"><span data-stu-id="e0201-131">Regular core staff</span></span>
    
  - <span data-ttu-id="e0201-132">작업 담당자</span><span class="sxs-lookup"><span data-stu-id="e0201-132">Operations staff</span></span>
    
  - <span data-ttu-id="e0201-133">필드 직원</span><span class="sxs-lookup"><span data-stu-id="e0201-133">Field staff</span></span>
    
1. <span data-ttu-id="e0201-134">**모든 그룹** 블레이드에서 **+ 새 그룹을**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0201-134">On the **All groups** blade, click **+ New group**.</span></span>
    
2. <span data-ttu-id="e0201-135">**사용자 이름에서**목록에서 그룹 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0201-135">Type the group name from the list in **Name**.</span></span>
    
3. <span data-ttu-id="e0201-136">**멤버 자격**에서 **동적 사용자** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0201-136">Select **Dynamic user** in **Membership**.</span></span>
    
4. <span data-ttu-id="e0201-137">**Office를 사용 하도록 설정 기능**에 대 한 **예** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0201-137">Click **Yes** for **Enable Office features**.</span></span>
    
5. <span data-ttu-id="e0201-138">**추가 동적 쿼리**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0201-138">Click **Add dynamic query**.</span></span>
    
6. <span data-ttu-id="e0201-139">**사용자를 추가할 위치**, **부서**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0201-139">In **Add users where**, select **department**.</span></span>
    
7. <span data-ttu-id="e0201-140">다음 필드에 **는**선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0201-140">In the next field, select **Equals**.</span></span>
    
8. <span data-ttu-id="e0201-141">다음 필드 목록에서 그룹 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0201-141">In the next field, type the group name from the list.</span></span>
    
9. <span data-ttu-id="e0201-142">**추가 쿼리**클릭 한 다음 **만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0201-142">Click **Add query**, and then click **Create**.</span></span>
    
10. <span data-ttu-id="e0201-143">**사용자 및 그룹-모든 그룹을**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0201-143">Click **Users and groups - All groups**.</span></span>
    
<span data-ttu-id="e0201-144">다음으로, 구성원은 Office 365 e 5 및 EMS E5 라이선스를 자동으로 할당 되도록 그룹을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0201-144">Next, you configure the groups so that members are automatically assigned Office 365 E5 and EMS E5 licenses.</span></span>
  
1. <span data-ttu-id="e0201-145">Azure 포털에서 클릭 **Azure Active Directory > 라이선스 > 모든 제품**합니다.</span><span class="sxs-lookup"><span data-stu-id="e0201-145">In the Azure portal, click **Azure Active Directory > Licenses > All products**.</span></span>
    
2. <span data-ttu-id="e0201-146">목록에서 **엔터프라이즈 이동성 + 보안 e 5** 및 **Office 365 Enterprise e 5**를 선택한 다음 **할당 +**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0201-146">In the list, select **Enterprise Mobility + Security E5** and **Office 365 Enterprise E5**, and then click **+ Assign**.</span></span>
    
3. <span data-ttu-id="e0201-147">**라이선스를 할당** 블레이드에서 **사용자 및 그룹을**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0201-147">In the **Assign license** blade, click **Users and groups**.</span></span>
    
4. <span data-ttu-id="e0201-148">그룹 목록에서 다음을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0201-148">In the list of groups, select the following:</span></span>
    
  - <span data-ttu-id="e0201-149">분석 직원</span><span class="sxs-lookup"><span data-stu-id="e0201-149">Analytics staff</span></span>
    
  - <span data-ttu-id="e0201-150">필드 직원</span><span class="sxs-lookup"><span data-stu-id="e0201-150">Field staff</span></span>
    
  - <span data-ttu-id="e0201-151">IT 담당자</span><span class="sxs-lookup"><span data-stu-id="e0201-151">IT staff</span></span>
    
  - <span data-ttu-id="e0201-152">작업 담당자</span><span class="sxs-lookup"><span data-stu-id="e0201-152">Operations staff</span></span>
    
  - <span data-ttu-id="e0201-153">일반 핵심 직원</span><span class="sxs-lookup"><span data-stu-id="e0201-153">Regular core staff</span></span>
    
  - <span data-ttu-id="e0201-154">선임 및 전략적 직원</span><span class="sxs-lookup"><span data-stu-id="e0201-154">Senior and strategic staff</span></span>
    
5. <span data-ttu-id="e0201-155">**선택**을 클릭 하 고 **할당**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0201-155">Click **Select**, and then click **Assign**.</span></span>
    
6. <span data-ttu-id="e0201-156">브라우저에서 Azure 포털 탭을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="e0201-156">Close the Azure portal tab in your browser.</span></span>
    
## <a name="phase-3-add-your-user-accounts"></a><span data-ttu-id="e0201-157">3 단계: 사용자 계정 추가</span><span class="sxs-lookup"><span data-stu-id="e0201-157">Phase 3: Add your user accounts</span></span>

<span data-ttu-id="e0201-158">이 단계에서 정치적 캠페인에 대 한 예제 사용자 계정을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0201-158">In this phase, you add the example user accounts for your political campaign.</span></span>
  
<span data-ttu-id="e0201-159">첫째, [Azure Active Directory V2 PowerShell 모듈을 사용 하 여 연결](https://go.microsoft.com/fwlink/?linkid=842218)있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0201-159">First, you [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
<span data-ttu-id="e0201-160">다음으로, 조직 이름, 사용자 위치 및 공통 암호를 입력 한 다음 PowerShell 명령 프롬프트 또는 스크립트 ISE (통합 환경)에서 다음이 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0201-160">Next, you fill in your organization name, your location, and a common password, and then run these commands from the PowerShell command prompt or Integrated Script Environment (ISE):</span></span>
  
```
$orgName="<organization name, such as contoso for the contoso.onmicrosoft.com trial subscription domain name>"
$location="<the ISO ALPHA2 country code, such as US for the United States>"
$commonPassword="<common password for all the new accounts>"

$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password=$commonPassword

$deptName="Senior and strategic staff"
$userNames=@("Candidate","ChiefOfStaff","Strategic1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="IT staff"
$userNames=@("ITAdmin1","ITAdmin2") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Analytics staff"
$userNames=@("DataScientist1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Regular core staff"
$userNames=@("Regular1","Regular2") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Operations staff"
$userNames=@("Operations1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Field staff"
$userNames=@("FieldConsultant1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }

```

> [!IMPORTANT]
> <span data-ttu-id="e0201-p103">여기에 일반적인 암호 사용 자동화 및 개발/테스트 환경에 대 한 구성이 쉽기 때문입니다. 프로덕션 구독에 대 한 권장 되지 않습니다. 각 이러한 새 사용자 계정을 사용 하 여 서명 하 암호를 변경 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0201-p103">The use of a common password here is for automation and ease of configuration for a dev/test environment. This is not recommended for production subscriptions. As you sign in with each of these new user accounts, you will be prompted to change the password.</span></span> 
  
<span data-ttu-id="e0201-164">동적 그룹 멤버 자격 및 라이선스 그룹 기반 올바르게 작동 하는지 확인 하려면 다음이 단계를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0201-164">Use these steps to verify that dynamic group membership and group-based licensing are working correctly.</span></span>
  
1. <span data-ttu-id="e0201-165">브라우저의 **Microsoft Office 홈** 탭에서 **관리** 타일을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0201-165">From the **Microsoft Office Home** tab of your browser, click the **Admin** tile.</span></span>
    
2. <span data-ttu-id="e0201-166">브라우저의 새 **Office 관리 센터** 탭에서 **사용자**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0201-166">From the new **Office Admin center** tab of your browser, click **Users**.</span></span>
    
3. <span data-ttu-id="e0201-167">사용자의 목록에서 **후보**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0201-167">In the list of users, click **Candidate**.</span></span>
    
4. <span data-ttu-id="e0201-168">**후보** 사용자 계정의 속성을 나열 하는 창에서 다음을 확인.</span><span class="sxs-lookup"><span data-stu-id="e0201-168">In the pane that lists the properties of the **Candidate** user account, verify that:</span></span>
    
  - <span data-ttu-id="e0201-169">해당 **그룹 구성원 자격**) (의 **수석 및 전략적 직원** 그룹의 구성원입니다.</span><span class="sxs-lookup"><span data-stu-id="e0201-169">It is a member of the **Senior and strategic staff** group (in **Group memberships**).</span></span>
    
  - <span data-ttu-id="e0201-170">**엔터프라이즈 이동성 + 보안 e 5** 및 **Office 365 Enterprise E5** 라이선스 ( **제품 라이선스**)에 할당 된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="e0201-170">It has been assigned the **Enterprise Mobility + Security E5** and **Office 365 Enterprise E5** licenses (in **Product licenses**).</span></span>
    
5. <span data-ttu-id="e0201-171">**후보** 사용자 계정 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="e0201-171">Close the **Candidate** user account pane.</span></span>
    
## <a name="record-values-for-future-reference"></a><span data-ttu-id="e0201-172">나중에 참조할 수에 대 한 레코드 값</span><span class="sxs-lookup"><span data-stu-id="e0201-172">Record values for future reference</span></span>

<span data-ttu-id="e0201-173">Office 365 및 EMS 평가판 구독이 개발/테스트 환경에 대 한 작업에 대 한 이러한 값을 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0201-173">Record these values for working with the Office 365 and EMS trial subscriptions for this dev/test environment:</span></span>
  
- <span data-ttu-id="e0201-174">평가판 구독 조직 이름: ___</span><span class="sxs-lookup"><span data-stu-id="e0201-174">Your trial subscription organization name: _______________________________________________</span></span> 
    
    <span data-ttu-id="e0201-175">예, contoso.onmicrosoft.com 형식의 평가판 구독 도메인 이름에 대 한 조직 이름은 "contoso"입니다.</span><span class="sxs-lookup"><span data-stu-id="e0201-175">For example, for the trial subscription domain name of contoso.onmicrosoft.com, the organization name is "contoso".</span></span>
    
- <span data-ttu-id="e0201-176">Office 365 전역 관리자 이름: ___.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="e0201-176">The Office 365 global administrator name: ____________________________________.onmicrosoft.com</span></span>
    
    <span data-ttu-id="e0201-177">안전한 위치에이 계정에 대 한 암호 및 다른 사용자 계정에 대 한 일반적인 초기 암호를 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0201-177">Record the password for this account and the common initial password for the other user accounts in a secure location.</span></span>
    
## <a name="next-step"></a><span data-ttu-id="e0201-178">다음 단계</span><span class="sxs-lookup"><span data-stu-id="e0201-178">Next step</span></span>

<span data-ttu-id="e0201-179">[정치적 캠페인 개발/테스트 환경에서 팀 사이트 만들기와](create-team-sites-in-a-political-campaign-dev-test-environment.md)이 개발/테스트 환경에서 SharePoint Online 팀 사이트의 서로 다른 네가지 형식의 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0201-179">Build the four different types of SharePoint Online team sites in this dev/test environment with [Create team sites in a political campaign dev/test environment](create-team-sites-in-a-political-campaign-dev-test-environment.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e0201-180">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e0201-180">See Also</span></span>

[<span data-ttu-id="e0201-181">정치적 캠페인, 비영리, 및 기타 민첩 한 조직에 대 한 Microsoft 보안 지침</span><span class="sxs-lookup"><span data-stu-id="e0201-181">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="e0201-182">정치적 캠페인 개발/테스트 환경에서 팀 사이트 만들기</span><span class="sxs-lookup"><span data-stu-id="e0201-182">Create team sites in a political campaign dev/test environment</span></span>](create-team-sites-in-a-political-campaign-dev-test-environment.md)
  
[<span data-ttu-id="e0201-183">클라우드 도입 TLG(테스트 랩 가이드)</span><span class="sxs-lookup"><span data-stu-id="e0201-183">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="e0201-184">클라우드 채택 및 하이브리드 솔루션</span><span class="sxs-lookup"><span data-stu-id="e0201-184">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




