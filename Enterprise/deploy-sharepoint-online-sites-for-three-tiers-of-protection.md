---
title: "보호의 세 계층에 대 한 SharePoint Online 사이트 배포"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Strat_O365_Enterprise
- Ent_Solutions
ms.assetid: 1e8e3cfd-b878-4088-b941-9940363a5fae
description: "요약: 만들기 및 다양 한 수준의 정보 보호에 대 한 SharePoint Online 팀 사이트를 구성 합니다."
ms.openlocfilehash: f015ce8d7c91d02ce5dc0a7791ba22a53bc2933f
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2018
---
# <a name="deploy-sharepoint-online-sites-for-three-tiers-of-protection"></a><span data-ttu-id="52b2e-103">보호의 세 계층에 대 한 SharePoint Online 사이트 배포</span><span class="sxs-lookup"><span data-stu-id="52b2e-103">Deploy SharePoint Online sites for three tiers of protection</span></span>

 <span data-ttu-id="52b2e-104">**요약:** 페이지를 만들고 다양 한 수준의 정보 보호에 대 한 SharePoint Online 팀 사이트를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-104">**Summary:** Create and configure SharePoint Online team sites for various levels of information protection.</span></span>
  
<span data-ttu-id="52b2e-p101">이 문서의 단계를 사용 하 여 디자인 하 고 초기 계획, 소문자를 구분 하 고 매우 기밀 SharePoint Online 팀 사이트를 배포 합니다. 이러한 세 계층의 보호 하는 방법에 대 한 자세한 내용은 [SharePoint Online 보안 사이트 및 파일을](secure-sharepoint-online-sites-and-files.md)참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="52b2e-p101">Use the steps in this article to design and deploy baseline, sensitive, and highly confidential SharePoint Online team sites. For more information about these three tiers of protection, see [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md).</span></span>
  
## <a name="baseline-sharepoint-online-team-sites"></a><span data-ttu-id="52b2e-107">초기 계획 SharePoint Online 팀 사이트</span><span class="sxs-lookup"><span data-stu-id="52b2e-107">Baseline SharePoint Online team sites</span></span>

<span data-ttu-id="52b2e-p102">초기 계획 보호 모두 공용 및 개인 팀 사이트를 포함합니다. 공용 팀 사이트를 검색 하 고 조직에서 누구나 하 여 액세스할 수 있습니다. 개인 사이트 수만 검색 하 고 팀 사이트와 연결 된 Office 365 그룹의 구성원으로 액세스 합니다. 이러한 유형의 팀 사이트의 두 구성원이 다른 사용자와 사이트를 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-p102">Baseline protection includes both public and private team sites. Public team sites can be discovered and accessed by anybody in the organization. Private sites can only be discovered and accessed by members of the Office 365 group associated with the team site. Both of these types of team sites allow members to share the site with others.</span></span>
  
### <a name="public"></a><span data-ttu-id="52b2e-112">공용</span><span class="sxs-lookup"><span data-stu-id="52b2e-112">Public</span></span>

<span data-ttu-id="52b2e-113">일반 액세스 및 사용 권한으로 초기 SharePoint Online 팀 사이트를 만들려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-113">To create a baseline SharePoint Online team site with public access and permissions, do the following:</span></span>
  
1. <span data-ttu-id="52b2e-p103">SharePoint Online 팀 사이트 (SharePoint Online 관리자)를 관리 하는데 사용 되는 계정 사용 하 여 Office 365 포털에 로그인 합니다. 도움말을 보려면 [Office 365에 로그인 할 위치](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="52b2e-p103">Sign in to the Office 365 portal with an account that will also be used to administer the SharePoint Online team site (a SharePoint Online administrator). For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="52b2e-116">타일의 목록에서 **SharePoint**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-116">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="52b2e-117">브라우저에서 새 **SharePoint** 탭에서 **+ 사이트 만들기를**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-117">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="52b2e-118">**사이트 만들기** 페이지에서 **팀 사이트**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-118">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="52b2e-119">**사이트 이름**공용 팀 사이트에 대 한 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-119">In **Site name**, type a name for the public team site.</span></span> 
    
6. <span data-ttu-id="52b2e-120">**팀 사이트 설명**사이트의 용도에 대 한 설명을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-120">In **Team site description**, type a description of the purpose of the site.</span></span>
    
7. <span data-ttu-id="52b2e-121">**개인 설정** **공용-이 사이트에 액세스할 수는 조직의 모든 사용자**를 선택 하 고 ****을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-121">In **Privacy settings**, select **Public - anyone in the organization can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="52b2e-122">에 **가 수행 하려는 추가?** 창 **마침**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-122">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="52b2e-123">구성 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-123">Here is your resulting configuration.</span></span>
  
![공용 SharePoint Online 팀 사이트에 대한 기준 수준 보호입니다.](images/bcd46b8d-3f89-4398-80ce-4da17ee85e03.png)
  
### <a name="private"></a><span data-ttu-id="52b2e-125">개인</span><span class="sxs-lookup"><span data-stu-id="52b2e-125">Private</span></span>

<span data-ttu-id="52b2e-126">개인 액세스 및 사용 권한으로 초기 SharePoint Online 팀 사이트를 만들려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-126">To create a baseline SharePoint Online team site with private access and permissions, do the following:</span></span>
  
1. <span data-ttu-id="52b2e-p104">SharePoint Online 팀 사이트 (SharePoint Online 관리자)를 관리 하는데 사용 되는 계정 사용 하 여 Office 365 포털에 로그인 합니다. 도움말을 보려면 [Office 365에 로그인 할 위치](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="52b2e-p104">Sign in to the Office 365 portal with an account that will also be used to administer the SharePoint Online team site (a SharePoint Online administrator). For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="52b2e-129">타일의 목록에서 **SharePoint**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-129">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="52b2e-130">브라우저에서 새 **SharePoint** 탭에서 **+ 사이트 만들기를**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-130">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="52b2e-131">**사이트 만들기** 페이지에서 **팀 사이트**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-131">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="52b2e-132">**사이트 이름**개인 팀 사이트에 대 한 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-132">In **Site name**, type a name for the private team site.</span></span> 
    
6. <span data-ttu-id="52b2e-133">**팀 사이트 설명** 에 사이트의 용도에 대 한 설명을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-133">In **Team site description,** type a description of the purpose of the site.</span></span>
    
7. <span data-ttu-id="52b2e-134">**개인정보 보호 설정**선택 **개인-이 사이트에 액세스할 수 있는 구성원만**, **다음**을 클릭 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-134">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="52b2e-135">에 **가 수행 하려는 추가?** 창, **구성원 추가**개인 팀 사이트에 액세스할 수 있는 사용자 계정의 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-135">On the **Who do you want to add?** pane, in **Add members**, type the names of user accounts that have access to this private team site.</span></span>
    
9. <span data-ttu-id="52b2e-136">작업이 완료 되 면 **마침** 을 클릭 하는 사이트에 추가 된 구성원 초기 집합 추가 (영문)</span><span class="sxs-lookup"><span data-stu-id="52b2e-136">When you are done adding the initial set of members to the site, click **Finish**</span></span>
    
<span data-ttu-id="52b2e-137">구성 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-137">Here is your resulting configuration.</span></span>
  
![개인 SharePoint Online 팀 사이트에 대한 기준 수준의 보호입니다.](images/91769026-37e3-4383-ac3c-dbf7aca98e41.png)
  
## <a name="sensitive-sharepoint-online-team-sites"></a><span data-ttu-id="52b2e-139">중요 한 SharePoint Online 팀 사이트</span><span class="sxs-lookup"><span data-stu-id="52b2e-139">Sensitive SharePoint Online team sites</span></span>

<span data-ttu-id="52b2e-140">중요 한 SharePoint Online 팀 사이트는 사용 권한을 팀 사이트와 연결 된 Office 365 그룹의 구성원 이어야 하는 대신 SharePoint 그룹의 구성원 자격을 통해 제어 되는 것을 의미 하는 한 격리 된 팀 사이트입니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-140">A sensitive SharePoint Online team site is an isolated team site, which means that permissions are controlled through membership in SharePoint groups instead of membership in the Office 365 group associated with the team site.</span></span>
  
<span data-ttu-id="52b2e-141">격리 된 팀 사이트를 만들려면 두 가지 주요 단계가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-141">To create an isolated team site, there are two main steps.</span></span>
  
### <a name="step-1-design-your-isolated-site"></a><span data-ttu-id="52b2e-142">1 단계: 격리 된 사이트를 디자인 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-142">Step 1: Design your isolated site</span></span>

<span data-ttu-id="52b2e-143">격리 된 팀 사이트를 디자인 하려면 결정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-143">To design your isolated team site, you need to determine:</span></span>
  
- <span data-ttu-id="52b2e-144">SharePoint 그룹 및 권한 수준입니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-144">Your SharePoint groups and permission levels.</span></span>
    
- <span data-ttu-id="52b2e-145">SharePoint 그룹의 구성원 포함 될 액세스 그룹의 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-145">The set of access groups that will be members of your SharePoint groups.</span></span>
    
     <span data-ttu-id="52b2e-146">액세스 그룹의 권장 집합이 사이트 구성원에 대 한 하나, 사이트 뷰어에 대 한 표시 하 고 사이트 관리자를 위한 하나 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-146">The recommended set of access groups is one for site members, one for site viewers, and one for site administrators.</span></span>
    
- <span data-ttu-id="52b2e-147">여부에 대 한 액세스 그룹 내에서 중첩 된 그룹을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-147">Whether you will use nested groups within your access groups.</span></span>
    
<span data-ttu-id="52b2e-148">예, 권장된 그룹 구조 및 사용 권한 수준을 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-148">For example, the recommended group structure and permission levels look like this:</span></span>
  
|<span data-ttu-id="52b2e-149">**SharePoint 그룹**</span><span class="sxs-lookup"><span data-stu-id="52b2e-149">**SharePoint group**</span></span>|<span data-ttu-id="52b2e-150">**사용 권한 수준**</span><span class="sxs-lookup"><span data-stu-id="52b2e-150">**Permission level**</span></span>|<span data-ttu-id="52b2e-151">**액세스 그룹 (예)**</span><span class="sxs-lookup"><span data-stu-id="52b2e-151">**Access group (examples)**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="52b2e-152">[사이트 이름] 구성원</span><span class="sxs-lookup"><span data-stu-id="52b2e-152">[site name] Members</span></span>  <br/> |<span data-ttu-id="52b2e-153">편집</span><span class="sxs-lookup"><span data-stu-id="52b2e-153">Edit</span></span>  <br/> |<span data-ttu-id="52b2e-154">[사이트 이름] 구성원</span><span class="sxs-lookup"><span data-stu-id="52b2e-154">[site name] Members</span></span>  <br/> |
|<span data-ttu-id="52b2e-155">[사이트 이름] 방문자</span><span class="sxs-lookup"><span data-stu-id="52b2e-155">[site name] Visitors</span></span>  <br/> |<span data-ttu-id="52b2e-156">읽기</span><span class="sxs-lookup"><span data-stu-id="52b2e-156">Read</span></span>  <br/> |<span data-ttu-id="52b2e-157">[사이트 이름] 뷰어</span><span class="sxs-lookup"><span data-stu-id="52b2e-157">[site name] Viewers</span></span>  <br/> |
|<span data-ttu-id="52b2e-158">[사이트 이름] 소유자</span><span class="sxs-lookup"><span data-stu-id="52b2e-158">[site name] Owners</span></span>  <br/> |<span data-ttu-id="52b2e-159">모든 권한</span><span class="sxs-lookup"><span data-stu-id="52b2e-159">Full control</span></span>  <br/> |<span data-ttu-id="52b2e-160">[사이트 이름] 관리자</span><span class="sxs-lookup"><span data-stu-id="52b2e-160">[site name] Admins</span></span>  <br/> |
   
<span data-ttu-id="52b2e-p105">SharePoint 그룹 및 권한 수준을 팀 사이트에 대 한 기본적으로 만들어집니다. 액세스 그룹의 이름을 결정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-p105">The SharePoint groups and permission levels are created by default for a team site. You need to determine the names of your access groups.</span></span>
  
<span data-ttu-id="52b2e-163">디자인 프로세스의 세부 정보에 대 한 [디자인 한 격리 된 SharePoint Online 팀 사이트를](design-an-isolated-sharepoint-online-team-site.md)참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-163">For the details of the design process, see [Design an isolated SharePoint Online team site](design-an-isolated-sharepoint-online-team-site.md).</span></span>
  
### <a name="step-2-deploy-your-isolated-site"></a><span data-ttu-id="52b2e-164">2 단계: 격리 된 사이트를 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-164">Step 2: Deploy your isolated site</span></span>

<span data-ttu-id="52b2e-165">격리 된 사이트를 배포 하려면 먼저 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-165">To deploy your isolated site, you first need to:</span></span>
  
- <span data-ttu-id="52b2e-166">사용자 계정 및 각 access 그룹에 추가할 그룹을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-166">Determine the user accounts and groups to add to each of your access groups.</span></span>
    
- <span data-ttu-id="52b2e-167">액세스 그룹을 만들고 사용자 및 그룹 구성원을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-167">Create the access groups and add the user and group members.</span></span>
    
<span data-ttu-id="52b2e-168">자세한 단계 [는 격리 된 SharePoint Online 팀 사이트 배포](deploy-an-isolated-sharepoint-online-team-site.md)의 **1 단계** 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="52b2e-168">For the detailed steps, see **Phase 1** of [Deploy an isolated SharePoint Online team site](deploy-an-isolated-sharepoint-online-team-site.md).</span></span>
  
<span data-ttu-id="52b2e-169">그런 다음 이러한 단계를 SharePoint Online 팀 사이트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-169">Next, you create the SharePoint Online team site with these steps.</span></span>
  
1. <span data-ttu-id="52b2e-p106">SharePoint Online 팀 사이트 (SharePoint Online 관리자)를 관리 하는데 사용 되는 계정 사용 하 여 Office 365 포털에 로그인 합니다. 도움말을 보려면 [Office 365에 로그인 할 위치](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="52b2e-p106">Sign in to the Office 365 portal with an account that will also be used to administer the SharePoint Online team site (a SharePoint Online administrator). For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="52b2e-172">타일의 목록에서 **SharePoint**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-172">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="52b2e-173">브라우저의 새 **SharePoint** 탭에서 **+ 사이트 만들기를**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-173">In the new **SharePoint** tab of your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="52b2e-174">**사이트 만들기** 페이지에서 **팀 사이트**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-174">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="52b2e-175">**사이트 이름**개인 팀 사이트에 대 한 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-175">In **Site name**, type a name for the private team site.</span></span>
    
6. <span data-ttu-id="52b2e-176">**팀 사이트 설명**대 한 선택적 설명을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-176">In **Team site description**, type an optional description.</span></span>
    
7. <span data-ttu-id="52b2e-177">**개인정보 보호 설정**선택 **개인-이 사이트에 액세스할 수 있는 구성원만**, **다음**을 클릭 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-177">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="52b2e-178">에 **가 수행 하려는 추가?** 창 **마침**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-178">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="52b2e-179">다음으로 새 SharePoint Online 팀 사이트에서 권한을 이러한 단계를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-179">Next, from the new SharePoint Online team site, configure permissions with these steps.</span></span>
  
1. <span data-ttu-id="52b2e-p107">결정은 이름 UPN (사용자 계정) IT 관리자 또는 다른 사람에 대 한 응답 및 사이트에 대 한 액세스에 대 한 요청을 해결 하는 일을 담당 됩니다 (belindan@contoso.com은 UPN의 예). 쓰기 여기에 해당 UPN: ___ 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-p107">Determine the User Principal Name (UPN) of the IT administrator or other person who will be responsible for responding to and addressing requests for access to the site (belindan@contoso.com is an example of a UPN). Write that UPN here: _________________________________________.</span></span>
    
2. <span data-ttu-id="52b2e-182">도구 모음에서 설정 아이콘을 클릭 한 다음 **사이트 사용 권한**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-182">In the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
3. <span data-ttu-id="52b2e-183">**사이트 사용 권한** 창에서 **고급 사용 권한 설정**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-183">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
4. <span data-ttu-id="52b2e-184">브라우저의 새 **사용 권한** 탭에서 **액세스 요청 설정**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-184">On the new **Permissions** tab of your browser, click **Access Request Settings**.</span></span>
    
5. <span data-ttu-id="52b2e-185">**액세스 요청 설정** 대화 상자:</span><span class="sxs-lookup"><span data-stu-id="52b2e-185">In the **Access Requests Settings** dialog box:</span></span>
    
  - <span data-ttu-id="52b2e-186">**사이트 및 개별 파일 및 폴더 공유 허용 구성원** 및 **사이트 구성원 그룹에 다른 사용자를 초대 하도록 허용 구성원** 확인란의 선택을 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-186">Clear the **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** check boxes.</span></span>
    
  - <span data-ttu-id="52b2e-187">**액세스에 대 한 모든 요청**에서 1 단계에서 IT 관리자의 UPN을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-187">Type the UPN of your IT administrator from step 1 in **Send all requests for access**.</span></span>
    
  - <span data-ttu-id="52b2e-188">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-188">Click **OK**.</span></span>
    
6. <span data-ttu-id="52b2e-189">브라우저의 **사용 권한** 탭에서 목록에서 **[사이트 이름] 구성원** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-189">On the **Permissions** tab of your browser, click **[site name] Members** in the list.</span></span>
    
7. <span data-ttu-id="52b2e-190">**사용자 및 그룹에서** **새로 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-190">In **People and Groups**, click **New**.</span></span>
    
8. <span data-ttu-id="52b2e-191">**공유** 대화 상자에서이 사이트에 대 한 사이트 구성원 액세스 그룹의 이름을 입력을 선택한 다음 **공유**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-191">In the **Share** dialog box, type the name of your site members access group for this site, select it, and then click **Share**.</span></span>
    
9. <span data-ttu-id="52b2e-192">브라우저에서 뒤로 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-192">Click the back button on your browser.</span></span>
    
10. <span data-ttu-id="52b2e-193">목록에서 **[사이트 이름] 소유자** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-193">Click **[site name] Owners** in the list.</span></span>
    
11. <span data-ttu-id="52b2e-194">**사용자 및 그룹에서** **새로 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-194">In **People and Groups**, click **New**.</span></span>
    
12. <span data-ttu-id="52b2e-195">**공유** 대화 상자에서이 사이트에 대 한 사이트 관리자가 액세스 그룹의 이름을 입력을 선택한 다음 **공유**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-195">In the **Share** dialog box, type the name of the site administrators access group for this site, select it, and then click **Share**.</span></span>
    
13. <span data-ttu-id="52b2e-196">브라우저에서 뒤로 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-196">Click the back button on your browser.</span></span>
    
14. <span data-ttu-id="52b2e-197">목록에서 **[사이트 이름] 방문자** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-197">Click **[site name] Visitors** in the list.</span></span>
    
15. <span data-ttu-id="52b2e-198">**사용자 및 그룹에서** **새로 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-198">In **People and Groups**, click **New**.</span></span>
    
16. <span data-ttu-id="52b2e-199">**공유** 대화 상자에서이 사이트에 대 한 사이트 뷰어 액세스 그룹의 이름을 입력을 선택한 다음 **공유**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-199">In the **Share** dialog box, type the name of the site viewers access group for this site, select it, and then click **Share**.</span></span>
    
17. <span data-ttu-id="52b2e-200">브라우저의 **사용 권한** 탭을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-200">Close the **Permissions** tab of your browser.</span></span>
    
<span data-ttu-id="52b2e-201">이러한 사용 권한 설정의 결과:</span><span class="sxs-lookup"><span data-stu-id="52b2e-201">The results of these permission settings are:</span></span>
  
- <span data-ttu-id="52b2e-202">**[사이트 이름] Owners** SharePoint 그룹의 모든 구성원에 **모든 권한** 권한 수준을 가진 사이트 관리자가 액세스 그룹을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-202">The **[site name] Owners** SharePoint group contains the site administrators access group, in which all the members have the **Full control** permission level.</span></span>
    
- <span data-ttu-id="52b2e-203">**[사이트 이름] 구성원** SharePoint 그룹의 모든 구성원에 있는 사용 권한 수준 **편집** 사이트 구성원 액세스 그룹을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-203">The **[site name] Members** SharePoint group contains the site members access group, in which all the members have the **Edit** permission level.</span></span>
    
- <span data-ttu-id="52b2e-204">**[사이트 이름] 방문자** SharePoint 그룹의 모든 구성원에 **읽기** 권한 수준을 가진 사이트 뷰어 액세스 그룹을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-204">The **[site name] Visitors** SharePoint group contains the site viewers access group, in which all the members have the **Read** permission level.</span></span>
    
- <span data-ttu-id="52b2e-205">다른 구성원을 초대 하는 구성원에 대 한 기능을 사용 하는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-205">The ability for members to invite other members is disabled.</span></span>
    
- <span data-ttu-id="52b2e-206">액세스 요청을 비 구성원에 대 한 기능을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-206">The ability for non-members to request access is enabled.</span></span>
    
<span data-ttu-id="52b2e-207">구성 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-207">Here is your resulting configuration.</span></span>
  
![격리된 SharePoint Online 팀 사이트에 대한 중요한 수준의 보호입니다.](images/7a6ab9c6-560a-4674-ac39-8175644dbe6f.png)
  
<span data-ttu-id="52b2e-209">액세스 그룹 중 하나에서 그룹 구성원 자격을 통해 사이트의 구성원은 사이트의 리소스에 안전 하 게 공동 작업 이제 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-209">The members of the site, through group membership in one of the access groups, can now securely collaborate on the resources of the site.</span></span>
  
## <a name="highly-confidential-sharepoint-online-team-sites"></a><span data-ttu-id="52b2e-210">기밀 사항이 SharePoint Online 팀 사이트</span><span class="sxs-lookup"><span data-stu-id="52b2e-210">Highly confidential SharePoint Online team sites</span></span>

<span data-ttu-id="52b2e-211">기밀 사항이 SharePoint Online 팀 사이트는 사용 권한을 팀 사이트와 연결 된 Office 365 그룹의 구성원 이어야 하는 대신 SharePoint 그룹의 구성원 자격을 통해 제어 되는 것을 의미 하는 한 격리 된 팀 사이트입니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-211">A highly confidential SharePoint Online team site is an isolated team site, which means that permissions are controlled through membership in SharePoint groups instead of membership in the Office 365 group associated with the team site.</span></span>
  
<span data-ttu-id="52b2e-212">매우 기밀 정보 및 공동 작업에 대 한 격리 된 팀 사이트를 만들려면 두 가지 주요 단계가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-212">To create an isolated team site for highly confidential information and collaboration, there are two main steps.</span></span>
  
### <a name="step-1-design-your-isolated-site"></a><span data-ttu-id="52b2e-213">1 단계: 격리 된 사이트를 디자인 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-213">Step 1: Design your isolated site</span></span>

<span data-ttu-id="52b2e-214">격리 된 팀 사이트를 디자인 하려면 결정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-214">To design your isolated team site, you need to determine:</span></span>
  
- <span data-ttu-id="52b2e-215">SharePoint 그룹 및 권한 수준입니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-215">Your SharePoint groups and permission levels.</span></span>
    
- <span data-ttu-id="52b2e-216">SharePoint 그룹의 구성원 포함 될 액세스 그룹의 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-216">The set of access groups that will be members of your SharePoint groups.</span></span>
    
     <span data-ttu-id="52b2e-217">액세스 그룹의 권장 집합이 사이트 구성원에 대 한 하나, 사이트 뷰어에 대 한 표시 하 고 사이트 관리자를 위한 하나 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-217">The recommended set of access groups is one for site members, one for site viewers, and one for site administrators.</span></span>
    
- <span data-ttu-id="52b2e-218">여부에 대 한 액세스 그룹 내에서 중첩 된 그룹을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-218">Whether you will use nested groups within your access groups.</span></span>
    
<span data-ttu-id="52b2e-219">예, 권장된 그룹 구조 및 사용 권한 수준을 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-219">For example, the recommended group structure and permission levels look like this:</span></span>
  
|<span data-ttu-id="52b2e-220">**SharePoint 그룹**</span><span class="sxs-lookup"><span data-stu-id="52b2e-220">**SharePoint group**</span></span>|<span data-ttu-id="52b2e-221">**사용 권한 수준**</span><span class="sxs-lookup"><span data-stu-id="52b2e-221">**Permission level**</span></span>|<span data-ttu-id="52b2e-222">**액세스 그룹 (예)**</span><span class="sxs-lookup"><span data-stu-id="52b2e-222">**Access group (examples)**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="52b2e-223">[사이트 이름] 구성원</span><span class="sxs-lookup"><span data-stu-id="52b2e-223">[site name] Members</span></span>  <br/> |<span data-ttu-id="52b2e-224">편집</span><span class="sxs-lookup"><span data-stu-id="52b2e-224">Edit</span></span>  <br/> |<span data-ttu-id="52b2e-225">[사이트 이름] 구성원</span><span class="sxs-lookup"><span data-stu-id="52b2e-225">[site name] Members</span></span>  <br/> |
|<span data-ttu-id="52b2e-226">[사이트 이름] 방문자</span><span class="sxs-lookup"><span data-stu-id="52b2e-226">[site name] Visitors</span></span>  <br/> |<span data-ttu-id="52b2e-227">읽기</span><span class="sxs-lookup"><span data-stu-id="52b2e-227">Read</span></span>  <br/> |<span data-ttu-id="52b2e-228">[사이트 이름] 뷰어</span><span class="sxs-lookup"><span data-stu-id="52b2e-228">[site name] Viewers</span></span>  <br/> |
|<span data-ttu-id="52b2e-229">[사이트 이름] 소유자</span><span class="sxs-lookup"><span data-stu-id="52b2e-229">[site name] Owners</span></span>  <br/> |<span data-ttu-id="52b2e-230">모든 권한</span><span class="sxs-lookup"><span data-stu-id="52b2e-230">Full control</span></span>  <br/> |<span data-ttu-id="52b2e-231">[사이트 이름] 관리자</span><span class="sxs-lookup"><span data-stu-id="52b2e-231">[site name] Admins</span></span>  <br/> |
   
<span data-ttu-id="52b2e-p108">SharePoint 그룹 및 권한 수준을 팀 사이트에 대 한 기본적으로 만들어집니다. 액세스 그룹의 이름을 결정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-p108">The SharePoint groups and permission levels are created by default for a team site. You need to determine the names of your access groups.</span></span>
  
<span data-ttu-id="52b2e-234">디자인 프로세스의 세부 정보에 대 한 [디자인 한 격리 된 SharePoint Online 팀 사이트를](design-an-isolated-sharepoint-online-team-site.md)참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-234">For the details of the design process, see [Design an isolated SharePoint Online team site](design-an-isolated-sharepoint-online-team-site.md).</span></span>
  
### <a name="step-2-deploy-your-isolated-site"></a><span data-ttu-id="52b2e-235">2 단계: 격리 된 사이트를 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-235">Step 2: Deploy your isolated site</span></span>

<span data-ttu-id="52b2e-236">격리 된 사이트를 배포 하려면 먼저 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-236">To deploy your isolated site, you first need to:</span></span>
  
- <span data-ttu-id="52b2e-237">각 액세스 그룹의 사용자 및 그룹 구성원을 결정</span><span class="sxs-lookup"><span data-stu-id="52b2e-237">Determine the user and group members of each of your access groups</span></span>
    
- <span data-ttu-id="52b2e-238">액세스 그룹을 만들고 사용자 및 그룹 구성원 추가</span><span class="sxs-lookup"><span data-stu-id="52b2e-238">Create the access groups and add the user and group members</span></span>
    
- <span data-ttu-id="52b2e-239">액세스 그룹을 사용 하는 격리 된 팀 사이트 만들기</span><span class="sxs-lookup"><span data-stu-id="52b2e-239">Create an isolated team site that uses your access groups</span></span>
    
<span data-ttu-id="52b2e-240">자세한 단계 [는 격리 된 SharePoint Online 팀 사이트의 배포](deploy-an-isolated-sharepoint-online-team-site.md)를 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-240">For the detailed steps, see [Deploy an isolated SharePoint Online team site](deploy-an-isolated-sharepoint-online-team-site.md).</span></span>
  
<span data-ttu-id="52b2e-241">결과의 사용 권한 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-241">The results of the permission settings are:</span></span>
  
- <span data-ttu-id="52b2e-242">**[사이트 이름] Owners** SharePoint 그룹의 모든 구성원에 **모든 권한** 권한 수준을 가진 사이트 관리자가 액세스 그룹을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-242">The **[site name] Owners** SharePoint group contains the site administrators access group, in which all the members have the **Full control** permission level.</span></span>
    
- <span data-ttu-id="52b2e-243">**[사이트 이름] 구성원** SharePoint 그룹의 모든 구성원에 있는 사용 권한 수준 **편집** 사이트 구성원 액세스 그룹을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-243">The **[site name] Members** SharePoint group contains the site members access group, in which all the members have the **Edit** permission level.</span></span>
    
- <span data-ttu-id="52b2e-244">**[사이트 이름] 방문자** SharePoint 그룹의 모든 구성원에 **읽기** 권한 수준을 가진 사이트 뷰어 액세스 그룹을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-244">The **[site name] Visitors** SharePoint group contains the site viewers access group, in which all the members have the **Read** permission level.</span></span>
    
- <span data-ttu-id="52b2e-245">다른 구성원을 초대 하는 구성원에 대 한 기능을 사용 하는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-245">The ability for members to invite other members is disabled.</span></span>
    
- <span data-ttu-id="52b2e-246">액세스 요청을 비 구성원에 대 한 기능을 사용 하는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-246">The ability for non-members to request access is disabled.</span></span>
    
<span data-ttu-id="52b2e-247">구성 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-247">Here is your resulting configuration.</span></span>
  
![격리된 SharePoint Online 팀 사이트에 대한 높은 기밀 수준의 보호입니다.](images/196359ab-d7ed-4fcf-97b4-61820a74aca4.png)
  
<span data-ttu-id="52b2e-249">액세스 그룹 중 하나에서 그룹 구성원 자격을 통해 사이트의 구성원은 사이트의 리소스에 안전 하 게 공동 작업 이제 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52b2e-249">The members of the site, through group membership in one of the access groups, can now securely collaborate on the resources of the site.</span></span>
  
## <a name="next-step"></a><span data-ttu-id="52b2e-250">다음 단계</span><span class="sxs-lookup"><span data-stu-id="52b2e-250">Next step</span></span>

[<span data-ttu-id="52b2e-251">Office 365 레이블 및 DLP 사용 하 여 SharePoint Online 파일 보호</span><span class="sxs-lookup"><span data-stu-id="52b2e-251">Protect SharePoint Online files with Office 365 labels and DLP</span></span>](protect-sharepoint-online-files-with-office-365-labels-and-dlp.md)
    
## <a name="see-also"></a><span data-ttu-id="52b2e-252">참고 항목</span><span class="sxs-lookup"><span data-stu-id="52b2e-252">See Also</span></span>

[<span data-ttu-id="52b2e-253">SharePoint Online 사이트 및 파일의 보안</span><span class="sxs-lookup"><span data-stu-id="52b2e-253">Secure SharePoint Online sites and files</span></span>](secure-sharepoint-online-sites-and-files.md)
  
[<span data-ttu-id="52b2e-254">개발/테스트 환경에서 SharePoint Online 사이트 보호</span><span class="sxs-lookup"><span data-stu-id="52b2e-254">Secure SharePoint Online sites in a dev/test environment</span></span>](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[<span data-ttu-id="52b2e-255">정치적 캠페인, 비영리, 및 기타 민첩 한 조직에 대 한 Microsoft 보안 지침</span><span class="sxs-lookup"><span data-stu-id="52b2e-255">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="52b2e-256">클라우드 채택 및 하이브리드 솔루션</span><span class="sxs-lookup"><span data-stu-id="52b2e-256">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




