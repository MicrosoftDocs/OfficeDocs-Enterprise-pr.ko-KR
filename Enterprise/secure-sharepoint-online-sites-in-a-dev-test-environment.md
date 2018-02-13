---
title: "개발/테스트 환경에서 SharePoint Online 사이트 보호"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365, Strat_O365_Enterprise
ms.service: o365-solutions
localization_priority: Normal
ms.custom: Strat_O365_Enterprise
ms.assetid: 06af70f3-e7dc-4ee2-a385-fb4d61a5e93b
description: "요약: 개발/테스트 환경에서 공용, 개인, 소문자를 구분 및 기밀 사항이 SharePoint Online 팀 사이트를 만듭니다."
ms.openlocfilehash: a0448cdbce570db748f8fcae784fd6f1beefc218
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/13/2018
---
# <a name="secure-sharepoint-online-sites-in-a-devtest-environment"></a><span data-ttu-id="ddabb-103">개발/테스트 환경에서 SharePoint Online 사이트 보호</span><span class="sxs-lookup"><span data-stu-id="ddabb-103">Secure SharePoint Online sites in a dev/test environment</span></span>

 <span data-ttu-id="ddabb-104">**요약:** 개발/테스트 환경에서 공용, 개인, 소문자를 구분 및 기밀 사항이 SharePoint Online 팀 사이트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-104">**Summary:** Create public, private, sensitive, and highly confidential SharePoint Online team sites in a dev/test environment.</span></span>
  
<span data-ttu-id="ddabb-105">이 문서는 4 개의 서로 다른 유형의 [SharePoint Online 보안 사이트 및 파일](secure-sharepoint-online-sites-and-files.md) 솔루션을 위한 SharePoint Online 팀 사이트를 포함 하는 개발/테스트 환경을 만드는 단계별 지침을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-105">This article provides step-by-step instructions to create a dev/test environment that includes the four different types of SharePoint Online team sites for the [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md) solution.</span></span>
  
![보안 SharePoint Online 개발/테스트 환경의 모든 네 개의 팀 사이트입니다.](images/b0fea489-359c-4c85-a0ad-e4efb4a1e47f.png)
  
<span data-ttu-id="ddabb-107">이 개발/테스트 환경을 사용 하 여 정보 보호 동작과 테스트 및 프로덕션 환경에서 SharePoint Online 팀 사이트를 배포 하기 전에 특정 요구 사항에 대 한 설정을 세부적으로 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-107">Use this dev/test environment to experiment with the information protection behaviors and fine-tune settings for your specific needs before deploying SharePoint Online team sites in production.</span></span>
  
## <a name="phase-1-create-your-devtest-environment"></a><span data-ttu-id="ddabb-108">1 단계: 개발/테스트 환경 만들기</span><span class="sxs-lookup"><span data-stu-id="ddabb-108">Phase 1: Create your dev/test environment</span></span>

<span data-ttu-id="ddabb-109">이 단계에서는 가상의 조직에 대 한 Office 365 및 Enterprise 이동성 + 보안에 대 한 평가판 구독 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-109">In this phase, you obtain trial subscriptions for Office 365 and Enterprise Mobility + Security for a fictional organization.</span></span>
  
<span data-ttu-id="ddabb-110">먼저, [Office 365 개발/테스트 환경](office-365-dev-test-environment.md)중 **2 단계** 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-110">First, follow the instructions in **Phase 2** of the [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="ddabb-111">다음으로, EMS 평가판 구독에 등록 하 고 Office 365 평가판 구독와 같은 조직에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-111">Next, sign up for the EMS trial subscription and add it to the same organization as your Office 365 trial subscription.</span></span>
  
1. <span data-ttu-id="ddabb-p101">평가판 구독의 전역 관리자 계정의 자격 증명을 사용 하 여 Office 365 포털에 필요한 경우에 로그인 합니다. 도움말을 보려면 [Office 365에 로그인 할 위치](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="ddabb-p101">If needed, sign in to the Office 365 portal with the credentials of the global administrator account of your trial subscription. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="ddabb-114">**Admin** 타일을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-114">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="ddabb-115">왼쪽 탐색 영역에서 브라우저에서 **Office 관리 센터** 탭을 클릭 **대금 청구 > 구매 서비스**합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-115">On the **Office Admin center** tab in your browser, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="ddabb-p102">**서비스 구매** 페이지 **Enterprise 이동성 + 보안 e 5** 항목을 찾습니다. 마우스 포인터를 올려 하 고 **무료 평가판을 시작**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-p102">On the **Purchase services** page, find the **Enterprise Mobility + Security E5** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="ddabb-118">**주문 확인** 페이지에서 **지금 시도**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-118">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="ddabb-119">**순서 확인** 페이지에서 **계속**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-119">On the **Order receipt** page, click **Continue**.</span></span>
    
<span data-ttu-id="ddabb-120">다음으로, 엔터프라이즈 이동성 + 전역 관리자 계정에 대 한 보안 E5 라이선스 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-120">Next, enable the Enterprise Mobility + Security E5 license for your global administrator account.</span></span>
  
1. <span data-ttu-id="ddabb-121">왼쪽 탐색 영역에서 브라우저에서 **Office 365 관리 센터** 탭을 클릭 **사용자 > 활성 사용자**합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-121">On the **Office 365 Admin center** tab in your browser, in the left navigation, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="ddabb-122">전역 관리자 계정을 클릭 하 고 **제품 라이선스**에 대 한 **편집** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-122">Click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="ddabb-123">**제품 라이선스** 창에서 **엔터프라이즈 이동성 + 보안 e 5** **전환**에 대 한 제품 라이선스 설정, **저장** 을 클릭 하 고 두번 **닫기** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-123">On the **Product licenses** pane, turn the product license for **Enterprise Mobility + Security E5** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
## <a name="phase-2-create-and-configure-your-azure-active-directory-ad-groups-and-users"></a><span data-ttu-id="ddabb-124">2 단계: 만들기 및 Azure Active Directory (AD) 그룹 및 사용자를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-124">Phase 2: Create and configure your Azure Active Directory (AD) groups and users</span></span>

<span data-ttu-id="ddabb-125">이 단계에서 만들기 및 가상의 조직에 대 한 Azure AD 그룹 및 사용자를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-125">In this phase, you create and configure the Azure AD groups and users for your fictional organization.</span></span>
  
<span data-ttu-id="ddabb-126">먼저 Azure 포털을 사용 하는 일반적인 조직에 대 한 그룹의 집합을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-126">First, create a set of groups for a typical organization with the Azure portal.</span></span>
  
1. <span data-ttu-id="ddabb-127">브라우저에서 별도 탭을 만들고 [https://portal.azure.com](https://portal.azure.com)에서 Azure 포털으로 이동 합니다. 필요한 경우 Office 365 E5 평가판 구독에 대 한 전역 관리자 계정의 자격 증명을 사용 하 여 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-127">Create a separate tab in your browser, and then go to the Azure portal at [https://portal.azure.com](https://portal.azure.com). If needed, sign in with the credentials of the global administrator account for your Office 365 E5 trial subscription.</span></span>
    
2. <span data-ttu-id="ddabb-128">Azure 포털에서 클릭 **Azure Active Directory > 사용자 및 그룹 > 모든 그룹**합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-128">In the Azure portal, click **Azure Active Directory > Users and groups > All groups**.</span></span>
    
3. <span data-ttu-id="ddabb-129">**모든 그룹** 블레이드에서 **+ 새 그룹을**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-129">On the **All groups** blade, click **+ New group**.</span></span>
    
4. <span data-ttu-id="ddabb-130">**그룹** 블레이드에서:</span><span class="sxs-lookup"><span data-stu-id="ddabb-130">On the **Group** blade:</span></span>
    
  - <span data-ttu-id="ddabb-131">**사용자 이름에서**형식 **C 제품군**</span><span class="sxs-lookup"><span data-stu-id="ddabb-131">Type **C-Suite** in **Name**.</span></span>
    
  - <span data-ttu-id="ddabb-132">**멤버 자격**에서 **할당** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-132">Select **Assigned** in **Membership**.</span></span>
    
  - <span data-ttu-id="ddabb-133">**Office를 사용 하도록 설정 기능**에 대 한 **예** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-133">Click **Yes** for **Enable Office features**.</span></span>
    
5. <span data-ttu-id="ddabb-134">**만들기**클릭 한 다음 **그룹** 블레이드를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-134">Click **Create**, and then close the **Group** blade.</span></span>
    
6. <span data-ttu-id="ddabb-135">다음 그룹 이름에 대해 3-5 단계를 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-135">Repeat steps 3-5 for the following group names:</span></span>
    
  - <span data-ttu-id="ddabb-136">IT 담당자</span><span class="sxs-lookup"><span data-stu-id="ddabb-136">IT staff</span></span>
    
  - <span data-ttu-id="ddabb-137">리서치 직원</span><span class="sxs-lookup"><span data-stu-id="ddabb-137">Research staff</span></span>
    
  - <span data-ttu-id="ddabb-138">정규 직원</span><span class="sxs-lookup"><span data-stu-id="ddabb-138">Regular staff</span></span>
    
  - <span data-ttu-id="ddabb-139">마케팅 직원</span><span class="sxs-lookup"><span data-stu-id="ddabb-139">Marketing staff</span></span>
    
  - <span data-ttu-id="ddabb-140">영업 직원</span><span class="sxs-lookup"><span data-stu-id="ddabb-140">Sales staff</span></span>
    
7. <span data-ttu-id="ddabb-141">브라우저 열기에서 Azure 포털 탭을 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-141">Keep the Azure portal tab in your browser open.</span></span>
    
<span data-ttu-id="ddabb-142">다음으로 자동 라이선스 그룹의 구성원 Office 365 및 EMS 구독에 대 한 라이선스를 자동으로 할당 됩니다 되도록 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-142">Next, you configure automatic licensing so that members of your groups are automatically assigned licenses for your Office 365 and EMS subscriptions.</span></span>
  
1. <span data-ttu-id="ddabb-143">Azure 포털에서 클릭 **Azure Active Directory > 라이선스 > 모든 제품**합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-143">In the Azure portal, click **Azure Active Directory > Licenses > All products**.</span></span>
    
2. <span data-ttu-id="ddabb-144">목록에서 **엔터프라이즈 이동성 + 보안 e 5** 및 **Office 365 Enterprise e 5**를 선택한 다음 **할당**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-144">In the list, select **Enterprise Mobility + Security E5** and **Office 365 Enterprise E5**, and then click **Assign**.</span></span>
    
3. <span data-ttu-id="ddabb-145">**라이선스를 할당** 블레이드에서 **사용자 및 그룹을**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-145">In the **Assign license** blade, click **Users and groups**.</span></span>
    
4. <span data-ttu-id="ddabb-146">그룹 목록에서 다음을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-146">In the list of groups, select the following:</span></span>
    
  - <span data-ttu-id="ddabb-147">C-제품군</span><span class="sxs-lookup"><span data-stu-id="ddabb-147">C-Suite</span></span>
    
  - <span data-ttu-id="ddabb-148">IT 담당자</span><span class="sxs-lookup"><span data-stu-id="ddabb-148">IT staff</span></span>
    
  - <span data-ttu-id="ddabb-149">리서치 직원</span><span class="sxs-lookup"><span data-stu-id="ddabb-149">Research staff</span></span>
    
  - <span data-ttu-id="ddabb-150">정규 직원</span><span class="sxs-lookup"><span data-stu-id="ddabb-150">Regular staff</span></span>
    
  - <span data-ttu-id="ddabb-151">마케팅 직원</span><span class="sxs-lookup"><span data-stu-id="ddabb-151">Marketing staff</span></span>
    
  - <span data-ttu-id="ddabb-152">영업 직원</span><span class="sxs-lookup"><span data-stu-id="ddabb-152">Sales staff</span></span>
    
5. <span data-ttu-id="ddabb-153">**선택**을 클릭 하 고 **할당**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-153">Click **Select**, and then click **Assign**.</span></span>
    
6. <span data-ttu-id="ddabb-154">브라우저에서 Azure 포털 탭을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-154">Close the Azure portal tab in your browser.</span></span>
    
<span data-ttu-id="ddabb-155">다음에는 [Azure Active Directory V2 PowerShell 모듈을 사용 하 여 연결](https://go.microsoft.com/fwlink/?linkid=842218)있습니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-155">Next, you [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
<span data-ttu-id="ddabb-156">조직 이름, 사용자 위치 및 공통 암호를 입력 하 고 스크립트 ISE (통합 환경) 사용자 계정을 만들고 해당 그룹에 추가 하는 PowerShell 명령 프롬프트에서 다음이 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-156">Fill in your organization name, your location, and a common password, and then run these commands from the PowerShell command prompt or Integrated Script Environment (ISE) to create user accounts and add them to their groups:</span></span>
  
```
$orgName="<organization name, such as contoso for the contoso.onmicrosoft.com trial subscription domain name>"
$location="<the ISO ALPHA2 country code, such as US for the United States>"
$commonPassword="<common password for all the new accounts>"

$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password=$commonPassword

$groupName="C-Suite"
$userNames=@("CEO","CFO","CIO") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="IT staff"
$userNames=@("ITAdmin1","ITAdmin2") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Research staff"
$userNames=@("Researcher1") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Regular staff"
$userNames=@("Regular1", "Regular2") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Marketing staff"
$userNames=@("Marketing1", "Marketing2") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Sales staff"
$userNames=@("SalesPerson1") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
```

> [!NOTE]
> <span data-ttu-id="ddabb-p103">여기에 일반적인 암호 사용 자동화 및 개발/테스트 환경에 대 한 구성이 쉽기 때문입니다. 프로덕션 구독에 대 한 권장 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-p103">The use of a common password here is for automation and ease of configuration for a dev/test environment. This is not recommended for production subscriptions.</span></span> 
  
<span data-ttu-id="ddabb-159">라이선스 그룹 기반 제대로 작동 하는지 확인 하려면 다음이 단계를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-159">Use these steps to verify that group-based licensing is working correctly.</span></span>
  
1. <span data-ttu-id="ddabb-160">브라우저의 **Microsoft Office 홈** 탭에서 **관리** 타일을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-160">From the **Microsoft Office Home** tab of your browser, click the **Admin** tile.</span></span>
    
2. <span data-ttu-id="ddabb-161">브라우저의 새 **Office 관리 센터** 탭에서 **사용자**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-161">From the new **Office Admin center** tab of your browser, click **Users**.</span></span>
    
3. <span data-ttu-id="ddabb-162">사용자의 목록에서 **CEO**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-162">In the list of users, click **CEO**.</span></span>
    
4. <span data-ttu-id="ddabb-163">**CEO** 사용자 계정의 속성을 나열 하는 창에는 할당 된 **제품 라이선스**) (에서 **엔터프라이즈 이동성 + 보안 e 5** 및 **Office 365 Enterprise E5** 라이선스를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-163">In the pane that lists the properties of the **CEO** user account, verify that it has been assigned the **Enterprise Mobility + Security E5** and **Office 365 Enterprise E5** licenses (in **Product licenses**).</span></span>
    
## <a name="phase-3-create-office-365-labels"></a><span data-ttu-id="ddabb-164">3 단계: Office 365 레이블 만들기</span><span class="sxs-lookup"><span data-stu-id="ddabb-164">Phase 3: Create Office 365 labels</span></span>

<span data-ttu-id="ddabb-165">이 단계에서는 다양 한 수준의 SharePoint Online 팀 사이트 문서 폴더에 대 한 보안에 대 한 레이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-165">In this phase, you create the labels for the different levels of security for SharePoint Online team site documents folders.</span></span>
  
1. <span data-ttu-id="ddabb-p104">필요한 경우 인터넷 브라우저의 개인 인스턴스를 사용 하 고 Office 365 E5 평가판 구독의 전역 관리자 계정 사용 하 여 Office 365 포털에 로그인 합니다. 도움말을 보려면 [Office 365에 로그인 할 위치](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="ddabb-p104">If needed, use a private instance of your Internet browser and sign in to the Office 365 portal with the global administrator account of your Office 365 E5 trial subscription. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="ddabb-168">**Microsoft Office 홈** 탭에서 **관리** 타일을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-168">From the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="ddabb-169">브라우저의 새 **Office 관리 센터** 탭을 클릭 **관리 센터 > 보안 &amp; 준수**합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-169">From the new **Office Admin center** tab of your browser, click **Admin centers > Security &amp; Compliance**.</span></span>
    
4. <span data-ttu-id="ddabb-170">새에서 **홈-보안 &amp; 준수** 탭 클릭 하 여 브라우저의 **분류 > 레이블**합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-170">From the new **Home - Security &amp; Compliance** tab of your browser, click **Classifications > Labels**.</span></span>
    
5. <span data-ttu-id="ddabb-171">**홈 > 레이블** 창 **레이블 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-171">From the **Home > Labels** pane, click **Create a label**.</span></span>
    
6. <span data-ttu-id="ddabb-172">**이름에 레이블** 창에서 **내부 공용**, 입력 하 고 ****을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-172">On the **Name your label** pane, type **Internal Public**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="ddabb-173">**레이블 설정** 창에서 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-173">On the **Label settings** pane, click **Next**.</span></span>
    
8. <span data-ttu-id="ddabb-174">**설정 검토** 창에서 **이 레이블 만들기**를 클릭 하 고 **닫기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-174">On the **Review your settings** pane, click **Create this label**, and then click **Close**.</span></span>
    
9. <span data-ttu-id="ddabb-175">이러한 추가 레이블에 대 한 5 ~ 8 단계를 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-175">Repeat steps 5-8 for these additional labels:</span></span>
    
  - <span data-ttu-id="ddabb-176">개인</span><span class="sxs-lookup"><span data-stu-id="ddabb-176">Private</span></span>
    
  - <span data-ttu-id="ddabb-177">중요 한</span><span class="sxs-lookup"><span data-stu-id="ddabb-177">Sensitive</span></span>
    
  - <span data-ttu-id="ddabb-178">기밀</span><span class="sxs-lookup"><span data-stu-id="ddabb-178">Highly Confidential</span></span>
    
10. <span data-ttu-id="ddabb-179">**홈 > 레이블** 창 **게시 레이블**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-179">From the **Home > Labels** pane, click **Publish labels**.</span></span>
    
11. <span data-ttu-id="ddabb-180">**게시를 선택 레이블** 창에서 **게시를 선택 레이블을**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-180">On the **Choose labels to publish** pane, click **Choose labels to publish**.</span></span>
    
12. <span data-ttu-id="ddabb-181">**Choose 레이블** 창에서 **추가** 클릭 하 고 모든 4 개의 레이블을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-181">On the **Choose labels** pane, click **Add** and select all four labels.</span></span>
    
13. <span data-ttu-id="ddabb-182">**완료**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-182">Click **Done**.</span></span>
    
14. <span data-ttu-id="ddabb-183">**게시를 선택 레이블** 창에서 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-183">On the **Choose labels to publish** pane, click **Next**.</span></span>
    
15. <span data-ttu-id="ddabb-184">**Choose 위치** 창에서 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-184">On the **Choose locations** pane, click **Next**.</span></span>
    
16. <span data-ttu-id="ddabb-185">**이름에 정책** 창에서 **이름** **예제 조직** 를 입력 하 고 ****을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-185">On the **Name your policy** pane, type **Example organization** in **Name**, and then click **Next**.</span></span>
    
17. <span data-ttu-id="ddabb-186">**설정 검토** 창에서 **게시 레이블**를 클릭 한 다음 **닫기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-186">On the **Review your settings** pane, click **Publish labels**, and then click **Close**.</span></span>
    
## <a name="phase-4-create-your-sharepoint-online-team-sites"></a><span data-ttu-id="ddabb-187">4 단계: SharePoint Online 팀 사이트 만들기</span><span class="sxs-lookup"><span data-stu-id="ddabb-187">Phase 4: Create your SharePoint Online team sites</span></span>

<span data-ttu-id="ddabb-188">이 단계에서 만들고 예제 조직에 대 한 다음과 같은 네가지 유형의 SharePoint Online 팀 사이트를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-188">In this phase, you create and configure the four types of SharePoint Online team sites for your example organization.</span></span>
  
### <a name="organization-wide-team-site"></a><span data-ttu-id="ddabb-189">조직 전체 팀 사이트</span><span class="sxs-lookup"><span data-stu-id="ddabb-189">Organization wide team site</span></span>

<span data-ttu-id="ddabb-190">초기 계획 공용 SharePoint Online 팀 사이트를 만들려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-190">To create a baseline public SharePoint Online team site, do the following:</span></span>
  
1. <span data-ttu-id="ddabb-p105">필요한 경우 로컬 컴퓨터에서 브라우저를 사용 하 고 전역 관리자 계정을 사용 하 여 Office 365 포털에 로그인 합니다. 도움말을 보려면 [Office 365에 로그인 할 위치](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="ddabb-p105">If needed, use a browser on your local computer and sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="ddabb-193">타일의 목록에서 **SharePoint**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-193">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="ddabb-194">브라우저에서 새 **SharePoint** 탭에서 **+ 사이트 만들기를**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-194">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="ddabb-195">**사이트 만들기** 페이지에서 **팀 사이트**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-195">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="ddabb-196">**사이트 이름** **조직 전체**를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-196">In **Site name**, type **Organization wide**.</span></span> 
    
6. <span data-ttu-id="ddabb-197">**팀 사이트 설명** **전체 조직에 대 한 SharePoint 사이트**를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-197">In **Team site description**, type **SharePoint site for the entire organization**.</span></span>
    
7. <span data-ttu-id="ddabb-198">**개인 설정** **공용-이 사이트에 액세스할 수는 조직의 모든 사용자**를 선택 하 고 ****을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-198">In **Privacy settings**, select **Public - anyone in the organization can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="ddabb-199">에 **가 수행 하려는 추가?** 창 **마침**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-199">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="ddabb-200">다음으로 내부 공용 레이블에 대 한 조직 전체 팀 사이트의 문서 폴더를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-200">Next, configure the documents folder of the Organization wide team site for the Internal Public label.</span></span>
  
1. <span data-ttu-id="ddabb-201">브라우저의 **조직 전체의-홈** 탭에서 **문서**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-201">In the **Organization wide-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="ddabb-202">설정 아이콘을 클릭 하 고 **라이브러리 설정**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-202">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="ddabb-203">**사용 권한 및 관리**, 아래에서 **이 라이브러리에 항목 레이블을 적용을**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-203">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="ddabb-204">**레이블 설정 적용** **내부 공용**을 선택 하 고 **저장**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-204">In **Settings-Apply Label**, select **Internal Public**, and then click **Save**.</span></span>
    
<span data-ttu-id="ddabb-205">구성 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-205">Here is your resulting configuration.</span></span>
  
![조직 차원 공용 SharePoint Online 팀 사이트에 대한 기준 수준 보호입니다.](images/25c86847-a38d-49ad-bb5f-c7c04206b6dc.png)
  
### <a name="project-1-team-site"></a><span data-ttu-id="ddabb-207">프로젝트 1 팀 사이트</span><span class="sxs-lookup"><span data-stu-id="ddabb-207">Project 1 team site</span></span>

<span data-ttu-id="ddabb-208">조직 내에서 프로젝트에 대 한 초기 계획 개인 SharePoint Online 팀 사이트를 만들려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-208">To create a baseline private SharePoint Online team site for a project within the organization, do the following:</span></span>
  
1. <span data-ttu-id="ddabb-p106">필요한 경우 로컬 컴퓨터에서 브라우저를 사용 하 고 전역 관리자 계정을 사용 하 여 Office 365 포털에 로그인 합니다. 도움말을 보려면 [Office 365에 로그인 할 위치](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="ddabb-p106">If needed, use a browser on your local computer and sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="ddabb-211">타일의 목록에서 **SharePoint**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-211">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="ddabb-212">브라우저에서 새 **SharePoint** 탭에서 **+ 사이트 만들기를**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-212">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="ddabb-213">**사이트 만들기** 페이지에서 **팀 사이트**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-213">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="ddabb-214">**사이트 이름** **프로젝트 1**을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-214">In **Site name**, type **Project 1**.</span></span> 
    
6. <span data-ttu-id="ddabb-215">**팀 사이트 설명** 에서 **프로젝트 1에 대 한 SharePoint 사이트**를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-215">In **Team site description,** type **SharePoint site for Project 1**.</span></span>
    
7. <span data-ttu-id="ddabb-216">**개인정보 보호 설정**선택 **개인-이 사이트에 액세스할 수 있는 구성원만**, **다음**을 클릭 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-216">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="ddabb-217">에 **가 수행 하려는 추가?** 창 **마침**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-217">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="ddabb-218">다음으로 개인 레이블에 대 한 프로젝트 1 팀 사이트의 문서 폴더를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-218">Next, configure the documents folder of the Project 1 team site for the Private label.</span></span>
  
1. <span data-ttu-id="ddabb-219">브라우저의 **프로젝트 1 홈** 탭에서 **문서**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-219">In the **Project 1-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="ddabb-220">설정 아이콘을 클릭 하 고 **라이브러리 설정**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-220">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="ddabb-221">**사용 권한 및 관리**, 아래에서 **이 라이브러리에 항목 레이블을 적용을**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-221">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="ddabb-222">**레이블 설정 적용** **개인**을 선택 하 고 **저장**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-222">In **Settings-Apply Label**, select **Private**, and then click **Save**.</span></span>
    
<span data-ttu-id="ddabb-223">구성 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-223">Here is your resulting configuration.</span></span>
  
![Project1 개인 SharePoint Online 팀 사이트에 대한 기준 수준의 보호입니다.](images/ecd96376-b5dc-4042-9cbd-b3765507ace7.png)
  
### <a name="marketing-campaigns-team-site"></a><span data-ttu-id="ddabb-225">마케팅 캠페인 팀 사이트</span><span class="sxs-lookup"><span data-stu-id="ddabb-225">Marketing campaigns team site</span></span>

<span data-ttu-id="ddabb-226">대부분은 중요 하지 수준의 격리 된 SharePoint Online 팀 사이트 마케팅 캠페인 리소스에 대 한를 만들려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-226">To create a sensitive-level isolated SharePoint Online team site for marketing campaign resources, do the following:</span></span>
  
1. <span data-ttu-id="ddabb-p107">전역 관리자 계정을 사용 하 여 Office 365 포털에 로그인 브라우저를 사용 하 여 로컬 컴퓨터에서 하십시오. 도움말을 보려면 [Office 365에 로그인 할 위치](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="ddabb-p107">Using a browser on your local computer, sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="ddabb-229">타일의 목록에서 **SharePoint**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-229">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="ddabb-230">브라우저에서 새 **SharePoint** 탭에서 **+ 사이트 만들기를**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-230">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="ddabb-231">**사이트 만들기** 페이지에서 **팀 사이트**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-231">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="ddabb-232">**팀 사이트 이름** **마케팅 캠페인**을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-232">In **Team site name**, type **Marketing campaigns**.</span></span>
    
6. <span data-ttu-id="ddabb-233">**팀 사이트 설명** **마케팅 캠페인 리소스 (중요)에 대 한 SharePoint 사이트**를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-233">In **Team site description**, type **SharePoint site for marketing campaign resources (sensitive)**.</span></span>
    
7.  <span data-ttu-id="ddabb-234">**개인정보 보호 설정**선택 **개인-이 사이트에 액세스할 수 있는 구성원만**, **다음**을 클릭 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-234">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="ddabb-235">에 **가 수행 하려는 추가?** 창 **마침**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-235">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
9. <span data-ttu-id="ddabb-236">도구 모음에서 브라우저에서 새 **마케팅 캠페인** 탭에서 설정 아이콘을 클릭 한 다음 **사이트 사용 권한**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-236">On the new **Marketing campaigns** tab in your browser, in the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
10. <span data-ttu-id="ddabb-237">**사이트 사용 권한** 창에서 **고급 사용 권한 설정**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-237">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
11. <span data-ttu-id="ddabb-238">브라우저에서 새 **사용 권한** 탭에서 **액세스 요청 설정**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-238">In the new **Permissions** tab in your browser, click **Access Request Settings**.</span></span>
    
12. <span data-ttu-id="ddabb-239">**액세스 요청 설정** 대화 상자에서 확인란의 선택을 취소 **사이트 및 개별 파일 및 폴더 공유 허용 구성원** 및 **사이트 구성원 그룹에 다른 사용자를 초대 하도록 허용 구성원** 을 **@ ITAdmin1**입력\<프로그램 조직 이름 >**. onmicrosoft.com** **액세스에 대 한 모든 요청을 보낼**에서 한 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-239">In the **Access Request Settings** dialog box, clear the **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** check boxes, type **ITAdmin1@**\<your organization name>**.onmicrosoft.com** in **Send all requests for access**, and then click **OK**.</span></span>
    
13. <span data-ttu-id="ddabb-240">**마케팅 캠페인 구성원** 목록에서 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-240">Click **Marketing campaigns Members** in the list.</span></span>
    
14. <span data-ttu-id="ddabb-241">**사용자 및 그룹** 페이지에서 **새로 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-241">On the **People and Groups** page, click **New**.</span></span>
    
15. <span data-ttu-id="ddabb-242">**공유** 대화 상자에서 입력 **마케팅 직원**을 선택한 다음 **공유**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-242">In the **Share** dialog box, type **Marketing staff**, select it, and then click **Share**.</span></span>
    
16. <span data-ttu-id="ddabb-243">**Researcher1** 사용자 계정에 대 한 14 및 15 단계를 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-243">Repeat steps 14 and 15 for the **Researcher1** user account.</span></span>
    
17. <span data-ttu-id="ddabb-244">브라우저에서 뒤로 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-244">Click the back button on your browser.</span></span>
    
18. <span data-ttu-id="ddabb-245">**마케팅 캠페인 소유자** 목록에서 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-245">Click **Marketing campaigns Owners** in the list.</span></span>
    
19. <span data-ttu-id="ddabb-246">**사용자 및 그룹** 페이지에서 **새로 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-246">On the **People and Groups** page, click **New**.</span></span>
    
20. <span data-ttu-id="ddabb-247">**공유** 대화 상자에서 입력 **IT 담당자**를 선택한 다음 **공유**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-247">In the **Share** dialog box, type **IT staff**, select it, and then click **Share**.</span></span>
    
21. <span data-ttu-id="ddabb-248">브라우저에서 뒤로 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-248">Click the back button on your browser.</span></span>
    
22. <span data-ttu-id="ddabb-249">브라우저에서 **사용자 및 그룹** 탭을 닫은 브라우저에서 **마케팅 캠페인 홈** 탭을 클릭 한 다음 **사이트 사용 권한** 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-249">Close the **People and Groups** tab in your browser, click the **Marketing campaigns-Home** tab in your browser, and then close the **Site permissions** pane.</span></span>
    
<span data-ttu-id="ddabb-250">사용 권한 구성 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-250">Here are the results of configuring permissions:</span></span>
  
- <span data-ttu-id="ddabb-251">**마케팅 캠페인 Members** SharePoint 그룹에는 **마케팅 캠페인** 그룹 (포함 하는 전역 관리자 사용자 계정), (Marketing1 및 Marketing2 사용자가 들어 있는 **마케팅 직원** 그룹 포함 계정) 및 **Researcher1** 사용자 계정입니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-251">The **Marketing campaigns-Members** SharePoint group contains only the **Marketing campaigns** group (which contains the global administrator user account), the **Marketing staff** group (which contains the Marketing1 and Marketing2 user accounts), and the **Researcher1** user account.</span></span>
    
- <span data-ttu-id="ddabb-252">**마케팅 캠페인 Owners** SharePoint 그룹의 **IT 담당자가** 그룹 (포함 하는 ITAdmin1 및 ITAdmin2 사용자 계정을)를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-252">The **Marketing campaigns-Owners** SharePoint group contains only the **IT staff** group (which contains only the ITAdmin1 and ITAdmin2 user accounts).</span></span>
    
- <span data-ttu-id="ddabb-253">**마케팅 캠페인 방문자** SharePoint 그룹에는 없는 그룹이 나 사용자 계정을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-253">The **Marketing campaigns-Visitors** SharePoint group contains no groups or user accounts.</span></span>
    
- <span data-ttu-id="ddabb-254">구성원 (이 수행할 수 있습니다 **마케팅 캠페인 소유자** 그룹의 구성원으로) 사이트 수준 사용 권한을 수정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-254">Members cannot modify site-level permissions (this can only be done by members of the **Marketing campaigns-Owners** group).</span></span>
    
- <span data-ttu-id="ddabb-255">다른 사용자의 계정을 사이트 또는 해당 리소스에 액세스할 수 없습니다 하지만 ITAdmin1 사용자 계정 사서함을 전자 메일을 보내 하는 사이트에 대 한 액세스를 요청할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-255">Other user accounts cannot access the site or its resources, but can request access to the site, which will send an email to the ITAdmin1 user account mailbox.</span></span>
    
<span data-ttu-id="ddabb-256">다음으로 중요 한 레이블에 대 한 마케팅 캠페인 팀 사이트의 문서 폴더를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-256">Next, configure the documents folder of the Marketing campaigns team site for the Sensitive label.</span></span>
  
1. <span data-ttu-id="ddabb-257">브라우저의 **마케팅 캠페인 홈** 탭에서 **문서**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-257">In the **Marketing campaigns-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="ddabb-258">설정 아이콘을 클릭 하 고 **라이브러리 설정**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-258">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="ddabb-259">**사용 권한 및 관리**, 아래에서 **이 라이브러리에 항목 레이블을 적용을**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-259">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="ddabb-260">**레이블 설정 적용** **중요 한**을 선택 하 고 **저장**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-260">In **Settings-Apply Label**, select **Sensitive**, and then click **Save**.</span></span>
    
<span data-ttu-id="ddabb-261">다음으로 조직 외부의 마케팅 캠페인 사이트를 포함 하는 중요 한 레이블로 SharePoint Online 팀 사이트에 문서를 공유 하는 경우 사용자에 게 알리는 하는 데이터 손실 방지 (DLP) 정책을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-261">Next, configure a data loss prevention (DLP) policy that notifies users when they share a document on a SharePoint Online team site with the Sensitive label, which includes the Marketing campaigns site, outside the organization.</span></span>
  
1. <span data-ttu-id="ddabb-262">브라우저에서 **Microsoft Office 홈** 탭에서 클릭 된 **보안 &amp; 준수** 바둑판식으로 배열 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-262">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
2. <span data-ttu-id="ddabb-263">새에서 **보안 &amp; 준수** 브라우저에서 탭을 클릭 **데이터 손실 방지 > 정책**합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-263">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
3. <span data-ttu-id="ddabb-264">**데이터 손실 방지** 창에서 **+ 정책 만들기를**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-264">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
4. <span data-ttu-id="ddabb-265">**서식 파일을 시작 하거나 사용자 지정 정책을 만들** 창 **사용자 지정**을 클릭 하 고 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-265">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
5. <span data-ttu-id="ddabb-266">**이름에 정책** 창에서 **이름** **중요 한 레이블 SharePoint Online 팀 사이트** 를 입력 하 고 ****을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-266">In the **Name your policy** pane, type **Sensitive label SharePoint Online team sites** in **Name**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="ddabb-267">**선택 위치** 창에서 **특정 위치를 선택 합니다.**를 클릭 하 고 ****을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-267">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="ddabb-268">위치 목록에서 **Exchange 전자 메일** 및 **OneDrive 계정** 위치를 사용 하지 않도록 설정 하 고 ****을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-268">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
8. <span data-ttu-id="ddabb-269">**중요 한 정보를 보호 하려면 유형의 사용자 지정** 창에서 **편집**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-269">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
9. <span data-ttu-id="ddabb-270">**보호 하기 위해 콘텐츠 형식 선택** 창에서 드롭다운 목록 상자에서 **추가** 클릭 하 고 **레이블**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-270">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
10. <span data-ttu-id="ddabb-271">**레이블** 창에서 **+ 기호 추가**클릭, **중요 한** 레이블을 선택, **추가**클릭 하 고 **완료**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-271">In the **Labels** pane, click **+ Add**, select the **Sensitive** label, click **Add**, and then click **Done**.</span></span>
    
11. <span data-ttu-id="ddabb-272">**보호 하기 위해 콘텐츠 형식 선택** 창에서 **저장**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-272">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
12. <span data-ttu-id="ddabb-273">**중요 한 정보를 보호 하려면 유형의 사용자 지정** 창에서 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-273">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
13. <span data-ttu-id="ddabb-274">**는 중요 한 정보를 검색 하는 경우 작업을 수행 하 시겠습니까?** 창 **사용자 지정 팁 및 전자 메일을**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-274">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
14. <span data-ttu-id="ddabb-275">**사용자 지정 정책 팁 및 전자 메일 알림** 창에서 **사용자 지정 정책 팁 텍스트를**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-275">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
15. <span data-ttu-id="ddabb-276">텍스트 상자에 입력 하거나 다음에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-276">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="ddabb-p108">조직 외부의 사용자와 공유 하려면 파일을 다운로드 하 고 파일을 엽니다. 파일을 다음 문서 보호를 클릭 하 고 암호를 암호화 하 고 강력한 암호를 지정 합니다. 별도 전자 메일 또는 다른 수단 통신의 암호를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-p108">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
16. <span data-ttu-id="ddabb-280">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-280">Click **OK**.</span></span>
    
17. <span data-ttu-id="ddabb-281">**는 중요 한 정보를 검색 하는 경우 작업을 수행 하 시겠습니까?** 창에서 **공유, 다른 사람을 차단 하 고 공유 내용에 대 한 액세스를 제한** 확인란의 선택을 취소 하 고 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-281">In the **What do you want to do if we detect sensitive info?** pane, clear the **Block people from sharing, and restrict access to shared content** check box, and then click **Next**.</span></span>
    
18. <span data-ttu-id="ddabb-282">**먼저 수행 정책 또는 테스트 작업을 설정 하 시겠습니까?** 창 **예, 귀하가 켜기**를 클릭 한 후에 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-282">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="ddabb-283">**설정 검토** 창에서 **만들기**를 클릭 한 다음 **닫기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-283">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
<span data-ttu-id="ddabb-284">구성 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-284">Here is your resulting configuration.</span></span>
  
![격리된 SharePoint Online 팀 사이트의 마케팅 캠페인에 대한 중요한 수준의 보호입니다.](images/33992bd5-96ee-4bfb-9ecf-c8a6736dd100.png)
  
### <a name="company-strategy-team-site"></a><span data-ttu-id="ddabb-286">회사 전략 팀 사이트</span><span class="sxs-lookup"><span data-stu-id="ddabb-286">Company strategy team site</span></span>

<span data-ttu-id="ddabb-287">조직의 수석 경영진의 전략적 회사 리소스에 대 한 매우 기밀 수준에서 격리 된 SharePoint Online 팀 사이트를 만들 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-287">To create an isolated SharePoint Online team site at the highly confidential level for strategic company resources of the chief executives of the organization, do the following:</span></span>
  
1. <span data-ttu-id="ddabb-p109">필요한 경우 로컬 컴퓨터에서 브라우저를 사용 하 고 전역 관리자 계정을 사용 하 여 Office 365 포털에 로그인 합니다. 도움말을 보려면 [Office 365에 로그인 할 위치](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="ddabb-p109">If needed, use a browser on your local computer and sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="ddabb-290">타일의 목록에서 **SharePoint**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-290">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="ddabb-291">브라우저에서 새 **SharePoint** 탭에서 **+ 사이트 만들기를**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-291">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="ddabb-292">**사이트 만들기** 페이지에서 **팀 사이트**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-292">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="ddabb-293">**팀 사이트 이름**, **회사 전략**을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-293">In **Team site name**, type **Company strategy**.</span></span>
    
6. <span data-ttu-id="ddabb-294">**팀 사이트 설명** **회사 전략 (기밀)에 대 한 SharePoint 사이트**를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-294">In **Team site description**, type **SharePoint site for company strategy (highly confidential)**.</span></span>
    
7.  <span data-ttu-id="ddabb-295">**개인정보 보호 설정**선택 **개인-이 사이트에 액세스할 수 있는 구성원만**, **다음**을 클릭 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-295">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="ddabb-296">에 **가 수행 하려는 추가?** 창 **마침**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-296">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
9. <span data-ttu-id="ddabb-297">도구 모음에서 브라우저에서 새 **회사 전략** 탭에서 설정 아이콘을 클릭 한 다음 **사이트 사용 권한**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-297">On the new **Company strategy** tab in your browser, in the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
10. <span data-ttu-id="ddabb-298">**사이트 사용 권한** 창에서 **고급 사용 권한 설정**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-298">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
11. <span data-ttu-id="ddabb-299">브라우저에서 새 **사용 권한** 탭에서 **액세스 요청 설정**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-299">In the new **Permissions** tab in your browser, click **Access Request Settings**.</span></span>
    
12. <span data-ttu-id="ddabb-300">**액세스 요청 설정** 대화 상자에서 **사이트 및 개별 파일 및 폴더 공유 허용 구성원** 및 **사이트 구성원 그룹에 다른 사용자를 초대 하도록 허용 구성원** (있도록 삭제 세 확인란을 모두 선택이 취소 됩니다), 다음 **를 클릭 하 고 확인**합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-300">In the **Access Request Settings** dialog box, clear **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** (so that all three check boxes are cleared), and then click **OK**.</span></span>
    
13. <span data-ttu-id="ddabb-301">목록에서 **회사 전략 구성원을** 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-301">Click **Company strategy Members** in the list.</span></span>
    
14. <span data-ttu-id="ddabb-302">**사용자 및 그룹** 페이지에서 **새로 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-302">On the **People and Groups** page, click **New**.</span></span>
    
15. <span data-ttu-id="ddabb-303">**공유** 대화 상자에서 입력 **C 제품군**을 선택한 다음 **공유**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-303">In the **Share** dialog box, type **C-Suite**, select it, and then click **Share**.</span></span>
    
16. <span data-ttu-id="ddabb-304">목록에서 **회사 전략 소유자를** 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-304">Click **Company strategy Owners** in the list.</span></span>
    
17. <span data-ttu-id="ddabb-305">**사용자 및 그룹** 페이지에서 **새로 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-305">On the **People and Groups** page, click **New**.</span></span>
    
18. <span data-ttu-id="ddabb-306">**공유** 대화 상자에서 입력 **IT 담당자**를 선택한 다음 **공유**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-306">In the **Share** dialog box, type **IT staff**, select it, and then click **Share**.</span></span>
    
19. <span data-ttu-id="ddabb-307">브라우저에서 뒤로 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-307">Click the back button on your browser.</span></span>
    
20. <span data-ttu-id="ddabb-308">브라우저에서 **사용자 및 그룹** 탭을 닫은 브라우저에서 **회사 전략 홈** 탭을 클릭 한 다음 **사이트 사용 권한** 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-308">Close the **People and Groups** tab in your browser, click the **Company strategy-Home** tab in your browser, and then close the **Site permissions** pane.</span></span>
    
<span data-ttu-id="ddabb-309">사용 권한 구성 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-309">Here are the results of configuring permissions:</span></span>
  
- <span data-ttu-id="ddabb-310">**회사 전략 구성원** SharePoint 그룹의 **C 제품군** 그룹 (포함 하는 CEO, CFO, 및 CIO 사용자 계정을) 및 하는 **회사 전략** 그룹 (전역 관리자 사용자 계정이 포함 되어 있음)를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-310">The **Company strategy-Members** SharePoint group contains only the **C-Suite** group (which contains only the CEO, CFO, and CIO user accounts) and the **Company strategy** group (which contains only the global administrator user account).</span></span>
    
- <span data-ttu-id="ddabb-311">**회사 전략 Owners** SharePoint 그룹의 **IT 담당자가** 그룹 (포함 하는 ITAdmin1 및 ITAdmin2 사용자 계정을)를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-311">The **Company strategy-Owners** SharePoint group contains only the **IT staff** group (which contains only the ITAdmin1 and ITAdmin2 user accounts).</span></span>
    
- <span data-ttu-id="ddabb-312">**회사 전략 방문자** SharePoint 그룹에는 없는 그룹이 나 사용자 계정을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-312">The **Company strategy-Visitors** SharePoint group contains no groups or user accounts.</span></span>
    
- <span data-ttu-id="ddabb-313">구성원 (이 수만 수행할 수 있는 **회사 전략 소유자** 그룹의 구성원으로) 사이트 수준 사용 권한을 수정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-313">Members cannot modify site-level permissions (this can only be done by members of the **Company strategy-Owners** group).</span></span>
    
- <span data-ttu-id="ddabb-p110">다른 사용자의 계정을 사이트 또는 해당 리소스에 액세스 하거나 사이트에 대 한 액세스를 요청할 수 없습니다. 사이트에 추가 사용 권한이 전역 관리자 또는 **회사 전략 소유자** 그룹의 구성원에 의해 수행 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-p110">Other user accounts cannot access the site or its resources or request access to the site. Additional permissions to the site must be done by the global administrator or by a member of the **Company strategy-Owners** group.</span></span>
    
<span data-ttu-id="ddabb-316">다음으로 기밀로 레이블에 대 한 회사 전략 팀 사이트의 문서 폴더를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-316">Next, configure the documents folder of the Company strategy team site for the Highly Confidential label.</span></span>
  
1. <span data-ttu-id="ddabb-317">브라우저의 **회사 전략-홈** 탭에서 **문서**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-317">In the **Company strategy-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="ddabb-318">설정 아이콘을 클릭 하 고 **라이브러리 설정**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-318">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="ddabb-319">**사용 권한 및 관리**, 아래에서 **이 라이브러리에 항목 레이블을 적용을**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-319">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="ddabb-320">**레이블 설정 적용** **매우 기밀**을 선택 하 고 **저장**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-320">In **Settings-Apply Label**, select **Highly Confidential**, and then click **Save**.</span></span>
    
<span data-ttu-id="ddabb-321">다음으로, DLP 정책 구성 요소 (영문)가 사용 하는 조직 외부의 회사 전략 사이트를 포함 하는 매우 기밀 레이블로 SharePoint Online 팀 사이트에 문서를 공유 하는 경우.</span><span class="sxs-lookup"><span data-stu-id="ddabb-321">Next, configure a DLP policy that blocks users when they share a document on a SharePoint Online team site with the Highly Confidential label, which includes the Company strategy site, outside the organization.</span></span>
  
1. <span data-ttu-id="ddabb-p111">필요한 경우 로컬 컴퓨터에서 브라우저를 사용 하 고 보안 관리자 또는 회사 관리자 역할을 가진 계정으로 사용 하 여 Office 365 포털에 로그인 합니다. 도움말을 보려면 [Office 365에 로그인 할 위치](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="ddabb-p111">If needed, use a browser on your local computer and sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="ddabb-324">브라우저에서 **Microsoft Office 홈** 탭에서 클릭 된 **보안 &amp; 준수** 바둑판식으로 배열 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-324">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
3. <span data-ttu-id="ddabb-325">새에서 **보안 &amp; 준수** 브라우저에서 탭을 클릭 **데이터 손실 방지 > 정책**합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-325">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
4. <span data-ttu-id="ddabb-326">**데이터 손실 방지** 창에서 **+ 정책 만들기를**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-326">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
5. <span data-ttu-id="ddabb-327">**서식 파일을 시작 하거나 사용자 지정 정책을 만들** 창 **사용자 지정**을 클릭 하 고 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-327">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="ddabb-328">**이름에 정책** 창에서 **이름** **매우 기밀 레이블 SharePoint Online 팀 사이트** 를 입력 하 고 ****을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-328">In the **Name your policy** pane, type **Highly Confidential label SharePoint Online team sites** in **Name**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="ddabb-329">**선택 위치** 창에서 **특정 위치를 선택 합니다.**를 클릭 하 고 ****을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-329">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="ddabb-330">위치 목록에서 **Exchange 전자 메일** 및 **OneDrive 계정** 위치를 사용 하지 않도록 설정 하 고 ****을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-330">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
9. <span data-ttu-id="ddabb-331">**중요 한 정보를 보호 하려면 유형의 사용자 지정** 창에서 **편집**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-331">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
10. <span data-ttu-id="ddabb-332">**보호 하기 위해 콘텐츠 형식 선택** 창에서 드롭다운 목록 상자에서 **추가** 클릭 하 고 **레이블**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-332">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
11. <span data-ttu-id="ddabb-333">**레이블** 창에서 **+ 기호 추가**클릭, **기밀 사항이** 레이블을 선택, **추가**클릭 하 고 **완료**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-333">In the **Labels** pane, click **+ Add**, select the **Highly Confidential** label, click **Add**, and then click **Done**.</span></span>
    
12. <span data-ttu-id="ddabb-334">**보호 하기 위해 콘텐츠 형식 선택** 창에서 **저장**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-334">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
13. <span data-ttu-id="ddabb-335">**중요 한 정보를 보호 하려면 유형의 사용자 지정** 창에서 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-335">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
14. <span data-ttu-id="ddabb-336">**는 중요 한 정보를 검색 하는 경우 작업을 수행 하 시겠습니까?** 창 **사용자 지정 팁 및 전자 메일을**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-336">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
15. <span data-ttu-id="ddabb-337">**사용자 지정 정책 팁 및 전자 메일 알림** 창에서 **사용자 지정 정책 팁 텍스트를**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-337">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
16. <span data-ttu-id="ddabb-338">텍스트 상자에 입력 하거나 다음에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-338">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="ddabb-p112">조직 외부의 사용자와 공유 하려면 파일을 다운로드 하 고 파일을 엽니다. 파일을 다음 문서 보호를 클릭 하 고 암호를 암호화 하 고 강력한 암호를 지정 합니다. 별도 전자 메일 또는 다른 수단 통신의 암호를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-p112">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
17. <span data-ttu-id="ddabb-342">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-342">Click **OK**.</span></span>
    
18. <span data-ttu-id="ddabb-343">**는 중요 한 정보를 검색 하는 경우 작업을 수행 하 시겠습니까?** 창 **, 업무 효율성을 재정의 하려면 필요**를 선택 하 고 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-343">In the **What do you want to do if we detect sensitive info?** pane, select **Require a business justification to override**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="ddabb-344">**먼저 수행 정책 또는 테스트 작업을 설정 하 시겠습니까?** 창 **예, 귀하가 켜기**를 클릭 한 후에 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-344">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
20. <span data-ttu-id="ddabb-345">**설정 검토** 창에서 **만들기**를 클릭 한 다음 **닫기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-345">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
<span data-ttu-id="ddabb-346">다음으로, [Office 365 관리 센터와 Azure RMS 활성화](https://docs.microsoft.com/information-protection/deploy-use/activate-office365)의 지시를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-346">Next, follow the instructions in [Activate Azure RMS with the Office 365 admin center](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).</span></span>
  
<span data-ttu-id="ddabb-347">다음, 새 범위가 지정 된 정책 및 하위 레이블 보호 및 다음 단계를 사용 하 여 권한을 사용 하 여 Azure 정보 보호를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-347">Next, configure Azure Information Protection with a new scoped policy and sub-label for protection and permissions with the following steps:</span></span>
  
1. <span data-ttu-id="ddabb-p113">보안 관리자 또는 회사 관리자 역할을 가진 계정으로 사용 하 여 Office 365 포털에 로그인 합니다. 도움말을 보려면 [Office 365에 로그인 할 위치](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="ddabb-p113">Sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="ddabb-350">브라우저의 별도 탭에서 Azure 포털 ([https://portal.azure.com](https://portal.azure.com))로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-350">In a separate tab of your browser, go to the Azure portal ([https://portal.azure.com](https://portal.azure.com)).</span></span>
    
3. <span data-ttu-id="ddabb-351">처음으로 Azure 정보 보호를 구성 하는 경우 다음 [지침](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="ddabb-351">If this is the first time you are configuring Azure Information Protection, see these [instructions](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span></span>
    
4. <span data-ttu-id="ddabb-352">목록 창에서 **서비스를 더**, **정보**를 입력 한 다음 **Azure 정보 보호**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-352">In the list pane, click **More services**, type **information**, and then click **Azure Information Protection**.</span></span>
    
5. <span data-ttu-id="ddabb-353">**Azure 정보 보호** 블레이드에서를 클릭 **정책 범위 > 새 정책을 추가 +**합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-353">On the **Azure Information protection** blade, , click **Scoped policies > + Add a new policy**.</span></span>
    
6. <span data-ttu-id="ddabb-354">**정책 이름** 및 **설명**에 **회사 전략 팀 사이트의 문서에 대 한 레이블** **CompanyStrategy** 를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-354">Type **CompanyStrategy** in **Policy name** and **Label for documents in the Company strategy team site** in **Description**.</span></span>
    
7. <span data-ttu-id="ddabb-355">클릭 **있는 사용자 또는 그룹에이 정책을 가져오려면 선택 > 사용자/그룹**, **C 제품군**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-355">Click **Select which users or groups get this policy > User/Groups**, and then select **C-Suite**.</span></span>
    
8. <span data-ttu-id="ddabb-356">클릭 **선택 > 확인**합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-356">Click **Select > OK**.</span></span>
    
9. <span data-ttu-id="ddabb-357">**기밀 사항이** 레이블에 대 한 줄임표 (...)를 클릭 하 고 **하위 레이블 추가**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-357">For the **Highly Confidential** label, click the ellipses (…), and then click **Add a sub-label**.</span></span>
    
10. <span data-ttu-id="ddabb-358">**이름** 및 **설명**의 레이블 내에 대 한 설명을 하위 레이블에 대 한 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-358">Type a name for the sub-label in **Name** and a description of the label in **Description**.</span></span>
    
11. <span data-ttu-id="ddabb-359">**문서 및이 레이블이 포함 된 전자 메일에 대 한 사용 권한 설정**에서 **암호로 보호**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-359">In **Set permissions for documents and emails containing this label**, click **Protect**.</span></span>
    
12. <span data-ttu-id="ddabb-360">**보호** 섹션에서 **Azure (클라우드 키)를**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-360">In the **Protection** section, click **Azure (cloud key)**.</span></span>
    
13. <span data-ttu-id="ddabb-361">**보호** 블레이드 **보호 설정**아래에서 **+ 추가 사용 권한을**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-361">On the **Protection** blade, under **Protection settings**, click **+ Add permissions**.</span></span>
    
14. <span data-ttu-id="ddabb-362">**추가 사용 권한** 블레이드 **지정 사용자 및 그룹을**에서 **디렉터리 찾아보기 +**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-362">On the **Add permissions** blade, under **Specify users and groups**, click **+ Browse directory**.</span></span>
    
15. <span data-ttu-id="ddabb-363">**AAD 사용자 및 그룹** 창에서 **C 제품군**선택 하 고 **선택**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-363">On the **AAD Users and Groups** pane, select **C-Suite**, and then click **Select**.</span></span>
    
16. <span data-ttu-id="ddabb-364">**사전 설정에서 사용 권한을 선택**아래에서 **인쇄**, **복사 및 콘텐츠 추출**및 **앞으로** 확인란의 선택을 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-364">Under **Choose permissions from the preset**, clear the **Print**, **Copy and extract content**, and **Forward** check boxes.</span></span>
    
17. <span data-ttu-id="ddabb-365">두 번 **확인** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-365">Click **OK** twice.</span></span>
    
18. <span data-ttu-id="ddabb-366">**하위 레이블** 블레이드에서 **저장**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-366">On the **Sub-label** blade, click **Save**.</span></span>
    
19. <span data-ttu-id="ddabb-367">새 범위가 지정 된 정책 블레이드를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-367">Close the new scoped policy blade.</span></span>
    
20. <span data-ttu-id="ddabb-368">**Azure 정보 보호-범위가 지정 된 정책** 블레이드에서 **게시**클릭 한 다음 **예**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-368">On the **Azure Information protection - Scoped policies** blade, click **Publish**, and then click **Yes**.</span></span>
    
<span data-ttu-id="ddabb-369">Azure 정보 보호 하 고이 새 레이블을 사용 하 여 문서를 보호 하려면 테스트 컴퓨터에서 [Azure 정보 보호 클라이언트 설치](https://docs.microsoft.com/information-protection/rms-client/install-client-app) 를 수행 해야, Office 365 포털에서 Office를 설치 하 고에 **계정을 사용 하 여 Microsoft Word에서 로그인 C-제품군** 평가판 구독의 그룹입니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-369">To protect a document with Azure Information Protection and this new label, you must [install the Azure Information Protection client](https://docs.microsoft.com/information-protection/rms-client/install-client-app) on a test machine, install Office from the Office 365 portal, and then sign in from Microsoft Word with an account in the **C-Suite** group of your trial subscription.</span></span>
  
<span data-ttu-id="ddabb-370">구성 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-370">Here is your resulting configuration.</span></span>
  
![격리된 SharePoint Online 팀 사이트의 회사 전략에 대한 높은 기밀 수준의 보호입니다.](images/c22695f9-50a1-4abf-a0dd-344b0c92cf94.png)
  
<span data-ttu-id="ddabb-372">이제 평가판 구독에서 다양 한 사용자 계정에 대 한 액세스를 테스트 하 고 이러한 4 개 사이트에서 문서를 만들 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-372">You are now ready to create documents in these four sites and test access to them with various user accounts in your trial subscription.</span></span>
  
<span data-ttu-id="ddabb-373">4 개의 모든 SharePoint Online 팀 사이트에 대 한 전체 구성 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-373">Here is the overall configuration for all four SharePoint Online team sites.</span></span>
  
![보안 SharePoint Online 개발/테스트 환경의 모든 네 개의 팀 사이트입니다.](images/b0fea489-359c-4c85-a0ad-e4efb4a1e47f.png)
  
## <a name="next-step"></a><span data-ttu-id="ddabb-375">다음 단계</span><span class="sxs-lookup"><span data-stu-id="ddabb-375">Next step</span></span>

<span data-ttu-id="ddabb-376">보안 SharePoint Online 사이트의 프로덕션 배포에 대 한 준비가 되 면 [보안 SharePoint Online 사이트 및 파일에](secure-sharepoint-online-sites-and-files.md) 대 한 자세한 정보와 단계별 배포 문서 링크를 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddabb-376">When you are ready for production deployment of secure SharePoint Online sites, see [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md) for detailed information and links to step-by-step deployment articles.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="ddabb-377">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ddabb-377">See Also</span></span>

[<span data-ttu-id="ddabb-378">SharePoint Online 사이트 및 파일의 보안</span><span class="sxs-lookup"><span data-stu-id="ddabb-378">Secure SharePoint Online sites and files</span></span>](secure-sharepoint-online-sites-and-files.md)
  
[<span data-ttu-id="ddabb-379">보안 솔루션</span><span class="sxs-lookup"><span data-stu-id="ddabb-379">Security solutions</span></span>](security-solutions.md)
  
[<span data-ttu-id="ddabb-380">클라우드 채택 및 하이브리드 솔루션</span><span class="sxs-lookup"><span data-stu-id="ddabb-380">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
[<span data-ttu-id="ddabb-381">정치적 캠페인, 비영리, 및 기타 민첩 한 조직에 대 한 Microsoft 보안 지침</span><span class="sxs-lookup"><span data-stu-id="ddabb-381">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)




