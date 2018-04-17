---
title: 보호의 세 계층에 대 한 SharePoint Online 사이트 배포
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
- Ent_Solutions
ms.assetid: 1e8e3cfd-b878-4088-b941-9940363a5fae
description: '요약: 만들기 및 다양 한 수준의 정보 보호에 대 한 SharePoint Online 팀 사이트를 구성 합니다.'
ms.openlocfilehash: ddeb1885cbc74be6e7098660eb1d9906d43739fd
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
---
# <a name="deploy-sharepoint-online-sites-for-three-tiers-of-protection"></a><span data-ttu-id="2ad00-103">보호의 세 계층에 대 한 SharePoint Online 사이트 배포</span><span class="sxs-lookup"><span data-stu-id="2ad00-103">Deploy SharePoint Online sites for three tiers of protection</span></span>

 <span data-ttu-id="2ad00-104">**요약:** 페이지를 만들고 다양 한 수준의 정보 보호에 대 한 SharePoint Online 팀 사이트를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-104">**Summary:** Create and configure SharePoint Online team sites for various levels of information protection.</span></span>
  
<span data-ttu-id="2ad00-p101">이 문서의 단계를 사용하여 초기, 중요 및 극비 SharePoint Online 팀 사이트를 디자인하고 배포합니다. 이러한 3계층 보호에 대한 자세한 내용은 [SharePoint Online 사이트 및 파일 보호](secure-sharepoint-online-sites-and-files.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2ad00-p101">Use the steps in this article to design and deploy baseline, sensitive, and highly confidential SharePoint Online team sites. For more information about these three tiers of protection, see [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md).</span></span>
  
## <a name="baseline-sharepoint-online-team-sites"></a><span data-ttu-id="2ad00-107">초기 SharePoint Online 팀 사이트</span><span class="sxs-lookup"><span data-stu-id="2ad00-107">Baseline SharePoint Online team sites</span></span>

<span data-ttu-id="2ad00-p102">초기 보호에는 공용 및 개인 팀 사이트가 모두 포함됩니다. 공용 팀 사이트는 조직의 모든 사용자가 검색하고 액세스할 수 있습니다. 개인 사이트는 팀 사이트와 연결된 Office 365 그룹의 구성원만 검색하고 액세스할 수 있습니다. 이러한 유형의 팀 사이트 모두에서는 구성원이 다른 사용자와 사이트를 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-p102">Baseline protection includes both public and private team sites. Public team sites can be discovered and accessed by anybody in the organization. Private sites can only be discovered and accessed by members of the Office 365 group associated with the team site. Both of these types of team sites allow members to share the site with others.</span></span>
  
### <a name="public"></a><span data-ttu-id="2ad00-112">Public</span><span class="sxs-lookup"><span data-stu-id="2ad00-112">Public</span></span>

<span data-ttu-id="2ad00-113">공용 액세스 및 권한이 있는 초기 SharePoint Online 팀 사이트를 만들려면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-113">To create a baseline SharePoint Online team site with public access and permissions, do the following:</span></span>
  
1. <span data-ttu-id="2ad00-p103">SharePoint Online 팀 사이트 (SharePoint Online 관리자)를 관리 하는데 사용 되는 계정 사용 하 여 Office 365 포털에 로그인 합니다. 도움말을 보려면 [Office 365에 로그인 할 위치](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="2ad00-p103">Sign in to the Office 365 portal with an account that will also be used to administer the SharePoint Online team site (a SharePoint Online administrator). For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="2ad00-116">타일 목록에서 **SharePoint**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-116">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="2ad00-117">브라우저의 새 **SharePoint** 탭에서 **+ 사이트 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-117">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="2ad00-118">**사이트 만들기** 페이지에서 **팀 사이트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-118">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="2ad00-119">**사이트 이름**에서 공용 팀 사이트의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-119">In **Site name**, type a name for the public team site.</span></span> 
    
6. <span data-ttu-id="2ad00-120">**팀 사이트 설명**에서 사이트의 목적에 대한 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-120">In **Team site description**, type a description of the purpose of the site.</span></span>
    
7. <span data-ttu-id="2ad00-121">**개인 설정** **공용-이 사이트에 액세스할 수는 조직의 모든 사용자**를 선택 하 고 ****을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-121">In **Privacy settings**, select **Public - anyone in the organization can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="2ad00-122">**Who do you want to add?(누구를 추가하시겠습니까?)** 창에서 **마침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-122">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="2ad00-123">구성 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-123">Here is your resulting configuration.</span></span>
  
![공용 SharePoint Online 팀 사이트에 대한 기준 수준 보호입니다.](images/bcd46b8d-3f89-4398-80ce-4da17ee85e03.png)
  
### <a name="private"></a><span data-ttu-id="2ad00-125">개인</span><span class="sxs-lookup"><span data-stu-id="2ad00-125">Private</span></span>

<span data-ttu-id="2ad00-126">개인 액세스 및 권한이 있는 초기 SharePoint Online 팀 사이트를 만들려면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-126">To create a baseline SharePoint Online team site with private access and permissions, do the following:</span></span>
  
1. <span data-ttu-id="2ad00-p104">SharePoint Online 팀 사이트 (SharePoint Online 관리자)를 관리 하는데 사용 되는 계정 사용 하 여 Office 365 포털에 로그인 합니다. 도움말을 보려면 [Office 365에 로그인 할 위치](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="2ad00-p104">Sign in to the Office 365 portal with an account that will also be used to administer the SharePoint Online team site (a SharePoint Online administrator). For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="2ad00-129">타일 목록에서 **SharePoint**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-129">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="2ad00-130">브라우저의 새 **SharePoint** 탭에서 **+ 사이트 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-130">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="2ad00-131">**사이트 만들기** 페이지에서 **팀 사이트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-131">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="2ad00-132">**사이트 이름**에서 개인 팀 사이트의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-132">In **Site name**, type a name for the private team site.</span></span> 
    
6. <span data-ttu-id="2ad00-133">**팀 사이트 설명** 에 사이트의 용도에 대 한 설명을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-133">In **Team site description,** type a description of the purpose of the site.</span></span>
    
7. <span data-ttu-id="2ad00-134">**개인정보 보호 설정**선택 **개인-이 사이트에 액세스할 수 있는 구성원만**, **다음**을 클릭 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-134">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="2ad00-135">**누구를 추가하시겠습니까?** 창의 **구성원 추가**에서 이 개인 팀 사이트에 액세스할 수 있는 사용자 계정의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-135">On the **Who do you want to add?** pane, in **Add members**, type the names of user accounts that have access to this private team site.</span></span>
    
9. <span data-ttu-id="2ad00-136">작업이 완료 되 면 **마침** 을 클릭 하는 사이트에 추가 된 구성원 초기 집합 추가 (영문)</span><span class="sxs-lookup"><span data-stu-id="2ad00-136">When you are done adding the initial set of members to the site, click **Finish**</span></span>
    
<span data-ttu-id="2ad00-137">구성 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-137">Here is your resulting configuration.</span></span>
  
![개인 SharePoint Online 팀 사이트에 대한 기준 수준의 보호입니다.](images/91769026-37e3-4383-ac3c-dbf7aca98e41.png)
  
## <a name="sensitive-sharepoint-online-team-sites"></a><span data-ttu-id="2ad00-139">중요 SharePoint Online 팀 사이트</span><span class="sxs-lookup"><span data-stu-id="2ad00-139">Sensitive SharePoint Online team sites</span></span>

<span data-ttu-id="2ad00-140">중요 SharePoint Online 팀 사이트는 격리된 팀 사이트이며, 팀 사이트와 연결된 Office 365 그룹의 구성원 자격 대신 SharePoint 그룹의 구성원 자격을 통해 권한이 제어됩니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-140">A sensitive SharePoint Online team site is an isolated team site, which means that permissions are controlled through membership in SharePoint groups instead of membership in the Office 365 group associated with the team site.</span></span>
  
<span data-ttu-id="2ad00-141">격리 된 팀 사이트를 만들려면 두 가지 주요 단계가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-141">To create an isolated team site, there are two main steps.</span></span>
  
### <a name="step-1-design-your-isolated-site"></a><span data-ttu-id="2ad00-142">1단계: 고립된 사이트 디자인</span><span class="sxs-lookup"><span data-stu-id="2ad00-142">Step 1: Design your isolated site</span></span>

<span data-ttu-id="2ad00-143">격리된 팀 사이트를 디자인하려면 다음을 결정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-143">To design your isolated team site, you need to determine:</span></span>
  
- <span data-ttu-id="2ad00-144">SharePoint 그룹 및 권한 수준</span><span class="sxs-lookup"><span data-stu-id="2ad00-144">Your SharePoint groups and permission levels.</span></span>
    
- <span data-ttu-id="2ad00-145">SharePoint 그룹의 구성원 포함 될 액세스 그룹의 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-145">The set of access groups that will be members of your SharePoint groups.</span></span>
    
     <span data-ttu-id="2ad00-146">액세스 그룹의 권장 집합이 사이트 구성원에 대 한 하나, 사이트 뷰어에 대 한 표시 하 고 사이트 관리자를 위한 하나 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-146">The recommended set of access groups is one for site members, one for site viewers, and one for site administrators.</span></span>
    
- <span data-ttu-id="2ad00-147">액세스 그룹 내에서 중첩된 그룹을 사용할지 여부</span><span class="sxs-lookup"><span data-stu-id="2ad00-147">Whether you will use nested groups within your access groups.</span></span>
    
<span data-ttu-id="2ad00-148">예를 들어 권장되는 그룹 구조와 권한 수준은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-148">For example, the recommended group structure and permission levels look like this:</span></span>
  
|<span data-ttu-id="2ad00-149">**SharePoint 그룹**</span><span class="sxs-lookup"><span data-stu-id="2ad00-149">**SharePoint group**</span></span>|<span data-ttu-id="2ad00-150">**권한 수준**</span><span class="sxs-lookup"><span data-stu-id="2ad00-150">**Permission level**</span></span>|<span data-ttu-id="2ad00-151">**액세스 그룹(예제)**</span><span class="sxs-lookup"><span data-stu-id="2ad00-151">**Access group (examples)**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="2ad00-152">[사이트 이름] 구성원</span><span class="sxs-lookup"><span data-stu-id="2ad00-152">[site name] Members</span></span>  <br/> |<span data-ttu-id="2ad00-153">편집</span><span class="sxs-lookup"><span data-stu-id="2ad00-153">Edit</span></span>  <br/> |<span data-ttu-id="2ad00-154">[사이트 이름] 구성원</span><span class="sxs-lookup"><span data-stu-id="2ad00-154">[site name] Members</span></span>  <br/> |
|<span data-ttu-id="2ad00-155">[사이트 이름] 방문자</span><span class="sxs-lookup"><span data-stu-id="2ad00-155">[site name] Visitors</span></span>  <br/> |<span data-ttu-id="2ad00-156">읽기</span><span class="sxs-lookup"><span data-stu-id="2ad00-156">Read</span></span>  <br/> |<span data-ttu-id="2ad00-157">[사이트 이름] 뷰어</span><span class="sxs-lookup"><span data-stu-id="2ad00-157">[site name] Viewers</span></span>  <br/> |
|<span data-ttu-id="2ad00-158">[사이트 이름] 소유자</span><span class="sxs-lookup"><span data-stu-id="2ad00-158">[site name] Owners</span></span>  <br/> |<span data-ttu-id="2ad00-159">모든 권한</span><span class="sxs-lookup"><span data-stu-id="2ad00-159">Full control</span></span>  <br/> |<span data-ttu-id="2ad00-160">[사이트 이름] 관리자</span><span class="sxs-lookup"><span data-stu-id="2ad00-160">[site name] Admins</span></span>  <br/> |
   
<span data-ttu-id="2ad00-p105">SharePoint 그룹 및 권한 수준은 기본적으로 팀 사이트에 대해 만들어집니다. 액세스 그룹의 이름을 결정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-p105">The SharePoint groups and permission levels are created by default for a team site. You need to determine the names of your access groups.</span></span>
  
<span data-ttu-id="2ad00-163">디자인 프로세스에 대한 자세한 내용은 [격리된 SharePoint Online 팀 사이트 디자인](design-an-isolated-sharepoint-online-team-site.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2ad00-163">For the details of the design process, see [Design an isolated SharePoint Online team site](design-an-isolated-sharepoint-online-team-site.md).</span></span>
  
### <a name="step-2-deploy-your-isolated-site"></a><span data-ttu-id="2ad00-164">2단계: 격리된 사이트 배포</span><span class="sxs-lookup"><span data-stu-id="2ad00-164">Step 2: Deploy your isolated site</span></span>

<span data-ttu-id="2ad00-165">격리된 사이트를 배포하려면 먼저 다음을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-165">To deploy your isolated site, you first need to:</span></span>
  
- <span data-ttu-id="2ad00-166">각 액세스 그룹에 추가할 사용자 계정 및 그룹을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-166">Determine the user accounts and groups to add to each of your access groups.</span></span>
    
- <span data-ttu-id="2ad00-167">액세스 그룹을 만들고 사용자 및 그룹 구성원을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-167">Create the access groups and add the user and group members.</span></span>
    
<span data-ttu-id="2ad00-168">자세한 단계는 [격리된 SharePoint Online 팀 사이트 배포](deploy-an-isolated-sharepoint-online-team-site.md)의 **1단계**를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2ad00-168">For the detailed steps, see **Phase 1** of [Deploy an isolated SharePoint Online team site](deploy-an-isolated-sharepoint-online-team-site.md).</span></span>
  
<span data-ttu-id="2ad00-169">그런 다음 이러한 단계를 SharePoint Online 팀 사이트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-169">Next, you create the SharePoint Online team site with these steps.</span></span>
  
1. <span data-ttu-id="2ad00-p106">SharePoint Online 팀 사이트 (SharePoint Online 관리자)를 관리 하는데 사용 되는 계정 사용 하 여 Office 365 포털에 로그인 합니다. 도움말을 보려면 [Office 365에 로그인 할 위치](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="2ad00-p106">Sign in to the Office 365 portal with an account that will also be used to administer the SharePoint Online team site (a SharePoint Online administrator). For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="2ad00-172">타일 목록에서 **SharePoint**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-172">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="2ad00-173">브라우저의 새 **SharePoint** 탭에서 **+ 사이트 만들기를**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-173">In the new **SharePoint** tab of your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="2ad00-174">**사이트 만들기** 페이지에서 **팀 사이트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-174">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="2ad00-175">**사이트 이름**에서 개인 팀 사이트의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-175">In **Site name**, type a name for the private team site.</span></span>
    
6. <span data-ttu-id="2ad00-176">**팀 사이트 설명**대 한 선택적 설명을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-176">In **Team site description**, type an optional description.</span></span>
    
7. <span data-ttu-id="2ad00-177">**개인정보 보호 설정**선택 **개인-이 사이트에 액세스할 수 있는 구성원만**, **다음**을 클릭 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-177">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="2ad00-178">**Who do you want to add?(누구를 추가하시겠습니까?)** 창에서 **마침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-178">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="2ad00-179">그리고 나서 새 SharePoint Online 팀 사이트에서 다음 단계를 사용하여 권한을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-179">Next, from the new SharePoint Online team site, configure permissions with these steps.</span></span>
  
1. <span data-ttu-id="2ad00-p107">결정은 이름 UPN (사용자 계정) IT 관리자 또는 다른 사람에 대 한 응답 및 사이트에 대 한 액세스에 대 한 요청을 해결 하는 일을 담당 됩니다 (belindan@contoso.com은 UPN의 예). 쓰기 여기에 해당 UPN: ___ 합니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-p107">Determine the User Principal Name (UPN) of the IT administrator or other person who will be responsible for responding to and addressing requests for access to the site (belindan@contoso.com is an example of a UPN). Write that UPN here: _________________________________________.</span></span>
    
2. <span data-ttu-id="2ad00-182">도구 모음에서 설정 아이콘을 클릭 한 다음 **사이트 사용 권한**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-182">In the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
3. <span data-ttu-id="2ad00-183">**사이트 권한** 창에서 **고급 권한 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-183">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
4. <span data-ttu-id="2ad00-184">브라우저의 새 **권한** 탭에서 **액세스 요청 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-184">On the new **Permissions** tab of your browser, click **Access Request Settings**.</span></span>
    
5. <span data-ttu-id="2ad00-185">**액세스 요청 설정** 대화 상자에서 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-185">In the **Access Requests Settings** dialog box:</span></span>
    
  - <span data-ttu-id="2ad00-186">**구성원이 사이트와 개별 파일 및 폴더를 공유할 수 있도록 허용합니다.** 및 **구성원이 다른 사용자들을 사이트 구성원 그룹에 초대할 수 있도록 허용합니다.** 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-186">Clear the **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** check boxes.</span></span>
    
  - <span data-ttu-id="2ad00-187">**모든 액세스 요청 보내기**의 1단계에서 IT 관리자의 UPN을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-187">Type the UPN of your IT administrator from step 1 in **Send all requests for access**.</span></span>
    
  - <span data-ttu-id="2ad00-188">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-188">Click **OK**.</span></span>
    
6. <span data-ttu-id="2ad00-189">브라우저의 **권한** 탭에서 목록의 **[사이트 이름] 구성원**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-189">On the **Permissions** tab of your browser, click **[site name] Members** in the list.</span></span>
    
7. <span data-ttu-id="2ad00-190">**사용자 및 그룹에서** **새로 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-190">In **People and Groups**, click **New**.</span></span>
    
8. <span data-ttu-id="2ad00-191">**공유** 대화 상자에서이 사이트에 대 한 사이트 구성원 액세스 그룹의 이름을 입력을 선택한 다음 **공유**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-191">In the **Share** dialog box, type the name of your site members access group for this site, select it, and then click **Share**.</span></span>
    
9. <span data-ttu-id="2ad00-192">브라우저에서 뒤로 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-192">Click the back button on your browser.</span></span>
    
10. <span data-ttu-id="2ad00-193">목록에서 **[사이트 이름] 소유자** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-193">Click **[site name] Owners** in the list.</span></span>
    
11. <span data-ttu-id="2ad00-194">**사용자 및 그룹에서** **새로 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-194">In **People and Groups**, click **New**.</span></span>
    
12. <span data-ttu-id="2ad00-195">**공유** 대화 상자에서이 사이트에 대 한 사이트 관리자가 액세스 그룹의 이름을 입력을 선택한 다음 **공유**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-195">In the **Share** dialog box, type the name of the site administrators access group for this site, select it, and then click **Share**.</span></span>
    
13. <span data-ttu-id="2ad00-196">브라우저에서 뒤로 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-196">Click the back button on your browser.</span></span>
    
14. <span data-ttu-id="2ad00-197">목록에서 **[사이트 이름] 방문자** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-197">Click **[site name] Visitors** in the list.</span></span>
    
15. <span data-ttu-id="2ad00-198">**사용자 및 그룹에서** **새로 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-198">In **People and Groups**, click **New**.</span></span>
    
16. <span data-ttu-id="2ad00-199">**공유** 대화 상자에서이 사이트에 대 한 사이트 뷰어 액세스 그룹의 이름을 입력을 선택한 다음 **공유**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-199">In the **Share** dialog box, type the name of the site viewers access group for this site, select it, and then click **Share**.</span></span>
    
17. <span data-ttu-id="2ad00-200">브라우저의 **권한** 탭을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-200">Close the **Permissions** tab of your browser.</span></span>
    
<span data-ttu-id="2ad00-201">이러한 사용 권한 설정의 결과:</span><span class="sxs-lookup"><span data-stu-id="2ad00-201">The results of these permission settings are:</span></span>
  
- <span data-ttu-id="2ad00-202">**[사이트 이름] 소유자** SharePoint 그룹에는 모든 구성원이 **모든 권한** 권한 수준을 갖는 사이트 관리자 액세스 그룹이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-202">The **[site name] Owners** SharePoint group contains the site administrators access group, in which all the members have the **Full control** permission level.</span></span>
    
- <span data-ttu-id="2ad00-203">**[사이트 이름] 구성원** SharePoint 그룹에는 모든 구성원이 **편집** 권한 수준을 갖는 사이트 구성원 액세스 그룹이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-203">The **[site name] Members** SharePoint group contains the site members access group, in which all the members have the **Edit** permission level.</span></span>
    
- <span data-ttu-id="2ad00-204">**[사이트 이름] 방문자** SharePoint 그룹에는 모든 구성원이 **읽기** 권한 수준을 갖는 사이트 뷰어 액세스 그룹이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-204">The **[site name] Visitors** SharePoint group contains the site viewers access group, in which all the members have the **Read** permission level.</span></span>
    
- <span data-ttu-id="2ad00-205">구성원이 다른 구성원을 초대하는 기능은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-205">The ability for members to invite other members is disabled.</span></span>
    
- <span data-ttu-id="2ad00-206">구성원이 아닌 사용자가 액세스를 요청하는 기능은 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-206">The ability for non-members to request access is enabled.</span></span>
    
<span data-ttu-id="2ad00-207">구성 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-207">Here is your resulting configuration.</span></span>
  
![격리된 SharePoint Online 팀 사이트에 대한 중요한 수준의 보호입니다.](images/7a6ab9c6-560a-4674-ac39-8175644dbe6f.png)
  
<span data-ttu-id="2ad00-209">사이트 구성원은 이제 액세스 그룹 중 하나의 그룹 구성원 자격을 통해 사이트의 리소스에서 안전하게 공동 작업할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-209">The members of the site, through group membership in one of the access groups, can now securely collaborate on the resources of the site.</span></span>
  
## <a name="highly-confidential-sharepoint-online-team-sites"></a><span data-ttu-id="2ad00-210">극비 SharePoint Online 팀 사이트</span><span class="sxs-lookup"><span data-stu-id="2ad00-210">Highly confidential SharePoint Online team sites</span></span>

<span data-ttu-id="2ad00-211">극비 SharePoint Online 팀 사이트는 격리된 팀 사이트이며, 팀 사이트와 연결된 Office 365 그룹의 구성원 자격 대신 SharePoint 그룹의 구성원 자격을 통해 권한이 제어됩니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-211">A highly confidential SharePoint Online team site is an isolated team site, which means that permissions are controlled through membership in SharePoint groups instead of membership in the Office 365 group associated with the team site.</span></span>
  
<span data-ttu-id="2ad00-212">매우 중요한 기밀에 속하는 정보와 공동 작업을 위해 격리된 팀 사이트를 만들려면 다음 두 가지 주요 단계가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-212">To create an isolated team site for highly confidential information and collaboration, there are two main steps.</span></span>
  
### <a name="step-1-design-your-isolated-site"></a><span data-ttu-id="2ad00-213">1단계: 고립된 사이트 디자인</span><span class="sxs-lookup"><span data-stu-id="2ad00-213">Step 1: Design your isolated site</span></span>

<span data-ttu-id="2ad00-214">격리된 팀 사이트를 디자인하려면 다음을 결정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-214">To design your isolated team site, you need to determine:</span></span>
  
- <span data-ttu-id="2ad00-215">SharePoint 그룹 및 권한 수준</span><span class="sxs-lookup"><span data-stu-id="2ad00-215">Your SharePoint groups and permission levels.</span></span>
    
- <span data-ttu-id="2ad00-216">SharePoint 그룹의 구성원 포함 될 액세스 그룹의 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-216">The set of access groups that will be members of your SharePoint groups.</span></span>
    
     <span data-ttu-id="2ad00-217">액세스 그룹의 권장 집합이 사이트 구성원에 대 한 하나, 사이트 뷰어에 대 한 표시 하 고 사이트 관리자를 위한 하나 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-217">The recommended set of access groups is one for site members, one for site viewers, and one for site administrators.</span></span>
    
- <span data-ttu-id="2ad00-218">액세스 그룹 내에서 중첩된 그룹을 사용할지 여부</span><span class="sxs-lookup"><span data-stu-id="2ad00-218">Whether you will use nested groups within your access groups.</span></span>
    
<span data-ttu-id="2ad00-219">예를 들어 권장되는 그룹 구조와 권한 수준은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-219">For example, the recommended group structure and permission levels look like this:</span></span>
  
|<span data-ttu-id="2ad00-220">**SharePoint 그룹**</span><span class="sxs-lookup"><span data-stu-id="2ad00-220">**SharePoint group**</span></span>|<span data-ttu-id="2ad00-221">**권한 수준**</span><span class="sxs-lookup"><span data-stu-id="2ad00-221">**Permission level**</span></span>|<span data-ttu-id="2ad00-222">**액세스 그룹(예제)**</span><span class="sxs-lookup"><span data-stu-id="2ad00-222">**Access group (examples)**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="2ad00-223">[사이트 이름] 구성원</span><span class="sxs-lookup"><span data-stu-id="2ad00-223">[site name] Members</span></span>  <br/> |<span data-ttu-id="2ad00-224">편집</span><span class="sxs-lookup"><span data-stu-id="2ad00-224">Edit</span></span>  <br/> |<span data-ttu-id="2ad00-225">[사이트 이름] 구성원</span><span class="sxs-lookup"><span data-stu-id="2ad00-225">[site name] Members</span></span>  <br/> |
|<span data-ttu-id="2ad00-226">[사이트 이름] 방문자</span><span class="sxs-lookup"><span data-stu-id="2ad00-226">[site name] Visitors</span></span>  <br/> |<span data-ttu-id="2ad00-227">읽기</span><span class="sxs-lookup"><span data-stu-id="2ad00-227">Read</span></span>  <br/> |<span data-ttu-id="2ad00-228">[사이트 이름] 뷰어</span><span class="sxs-lookup"><span data-stu-id="2ad00-228">[site name] Viewers</span></span>  <br/> |
|<span data-ttu-id="2ad00-229">[사이트 이름] 소유자</span><span class="sxs-lookup"><span data-stu-id="2ad00-229">[site name] Owners</span></span>  <br/> |<span data-ttu-id="2ad00-230">모든 권한</span><span class="sxs-lookup"><span data-stu-id="2ad00-230">Full control</span></span>  <br/> |<span data-ttu-id="2ad00-231">[사이트 이름] 관리자</span><span class="sxs-lookup"><span data-stu-id="2ad00-231">[site name] Admins</span></span>  <br/> |
   
<span data-ttu-id="2ad00-p108">SharePoint 그룹 및 권한 수준은 기본적으로 팀 사이트에 대해 만들어집니다. 액세스 그룹의 이름을 결정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-p108">The SharePoint groups and permission levels are created by default for a team site. You need to determine the names of your access groups.</span></span>
  
<span data-ttu-id="2ad00-234">디자인 프로세스에 대한 자세한 내용은 [격리된 SharePoint Online 팀 사이트 디자인](design-an-isolated-sharepoint-online-team-site.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2ad00-234">For the details of the design process, see [Design an isolated SharePoint Online team site](design-an-isolated-sharepoint-online-team-site.md).</span></span>
  
### <a name="step-2-deploy-your-isolated-site"></a><span data-ttu-id="2ad00-235">2단계: 격리된 사이트 배포</span><span class="sxs-lookup"><span data-stu-id="2ad00-235">Step 2: Deploy your isolated site</span></span>

<span data-ttu-id="2ad00-236">격리된 사이트를 배포하려면 먼저 다음을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-236">To deploy your isolated site, you first need to:</span></span>
  
- <span data-ttu-id="2ad00-237">각 액세스 그룹의 사용자 및 그룹 구성원을 결정</span><span class="sxs-lookup"><span data-stu-id="2ad00-237">Determine the user and group members of each of your access groups</span></span>
    
- <span data-ttu-id="2ad00-238">액세스 그룹을 만들고 사용자 및 그룹 구성원 추가</span><span class="sxs-lookup"><span data-stu-id="2ad00-238">Create the access groups and add the user and group members</span></span>
    
- <span data-ttu-id="2ad00-239">액세스 그룹을 사용 하는 격리 된 팀 사이트 만들기</span><span class="sxs-lookup"><span data-stu-id="2ad00-239">Create an isolated team site that uses your access groups</span></span>
    
<span data-ttu-id="2ad00-240">자세한 단계는 [격리된 SharePoint Online 팀 사이트 배포](deploy-an-isolated-sharepoint-online-team-site.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2ad00-240">For the detailed steps, see [Deploy an isolated SharePoint Online team site](deploy-an-isolated-sharepoint-online-team-site.md).</span></span>
  
<span data-ttu-id="2ad00-241">결과의 사용 권한 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-241">The results of the permission settings are:</span></span>
  
- <span data-ttu-id="2ad00-242">**[사이트 이름] 소유자** SharePoint 그룹에는 모든 구성원이 **모든 권한** 권한 수준을 갖는 사이트 관리자 액세스 그룹이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-242">The **[site name] Owners** SharePoint group contains the site administrators access group, in which all the members have the **Full control** permission level.</span></span>
    
- <span data-ttu-id="2ad00-243">**[사이트 이름] 구성원** SharePoint 그룹에는 모든 구성원이 **편집** 권한 수준을 갖는 사이트 구성원 액세스 그룹이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-243">The **[site name] Members** SharePoint group contains the site members access group, in which all the members have the **Edit** permission level.</span></span>
    
- <span data-ttu-id="2ad00-244">**[사이트 이름] 방문자** SharePoint 그룹에는 모든 구성원이 **읽기** 권한 수준을 갖는 사이트 뷰어 액세스 그룹이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-244">The **[site name] Visitors** SharePoint group contains the site viewers access group, in which all the members have the **Read** permission level.</span></span>
    
- <span data-ttu-id="2ad00-245">구성원이 다른 구성원을 초대하는 기능은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-245">The ability for members to invite other members is disabled.</span></span>
    
- <span data-ttu-id="2ad00-246">구성원이 아닌 사용자가 액세스를 요청하는 기능은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-246">The ability for non-members to request access is disabled.</span></span>
    
<span data-ttu-id="2ad00-247">결과적으로 구성은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-247">Here is your resulting configuration.</span></span>
  
![격리된 SharePoint Online 팀 사이트에 대한 높은 기밀 수준의 보호입니다.](images/196359ab-d7ed-4fcf-97b4-61820a74aca4.png)
  
<span data-ttu-id="2ad00-249">사이트 구성원은 이제 액세스 그룹 중 하나의 그룹 구성원 자격을 통해 사이트의 리소스에서 안전하게 공동 작업할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ad00-249">The members of the site, through group membership in one of the access groups, can now securely collaborate on the resources of the site.</span></span>
  
## <a name="next-step"></a><span data-ttu-id="2ad00-250">다음 단계</span><span class="sxs-lookup"><span data-stu-id="2ad00-250">Next step</span></span>

[<span data-ttu-id="2ad00-251">Office 365 레이블 및 DLP 사용 하 여 SharePoint Online 파일 보호</span><span class="sxs-lookup"><span data-stu-id="2ad00-251">Protect SharePoint Online files with Office 365 labels and DLP</span></span>](protect-sharepoint-online-files-with-office-365-labels-and-dlp.md)
    
## <a name="see-also"></a><span data-ttu-id="2ad00-252">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2ad00-252">See Also</span></span>

[<span data-ttu-id="2ad00-253">SharePoint Online 사이트 및 파일 보호</span><span class="sxs-lookup"><span data-stu-id="2ad00-253">Secure SharePoint Online sites and files</span></span>](secure-sharepoint-online-sites-and-files.md)
  
[<span data-ttu-id="2ad00-254">개발/테스트 환경의 SharePoint Online 사이트 보호</span><span class="sxs-lookup"><span data-stu-id="2ad00-254">Secure SharePoint Online sites in a dev/test environment</span></span>](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[<span data-ttu-id="2ad00-255">정치적 캠페인, 비영리 조직 및 기타 기밀 조직에 대한 Microsoft 보안 지침</span><span class="sxs-lookup"><span data-stu-id="2ad00-255">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="2ad00-256">클라우드 채택 및 하이브리드 솔루션</span><span class="sxs-lookup"><span data-stu-id="2ad00-256">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




