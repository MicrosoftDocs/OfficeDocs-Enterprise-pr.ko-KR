---
title: "격리 된 SharePoint Online 팀 사이트를 디자인 합니다."
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
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Ent_Solutions
ms.assetid: 775a4e9e-3135-4a48-b32f-bbdd9f2bd0aa
description: "격리 된 SharePoint Online 팀 사이트에 대 한 디자인 프로세스를 통해 요약: 단계입니다."
ms.openlocfilehash: 343872ef7a41b40a87454da27ddccc4530ffe2eb
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2017
---
# <a name="design-an-isolated-sharepoint-online-team-site"></a><span data-ttu-id="6259a-103">격리 된 SharePoint Online 팀 사이트를 디자인 합니다.</span><span class="sxs-lookup"><span data-stu-id="6259a-103">Design an isolated SharePoint Online team site</span></span>

 <span data-ttu-id="6259a-104">**요약:** 격리 된 SharePoint Online 팀 사이트에 대 한 디자인 프로세스를 단계별로 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="6259a-104">**Summary:** Step through the design process for isolated SharePoint Online team sites.</span></span>
  
<span data-ttu-id="6259a-105">이 문서는 격리 된 SharePoint Online 팀 사이트를 만들기 전에 내려야 주요 디자인 결정을 안내 합니다.</span><span class="sxs-lookup"><span data-stu-id="6259a-105">This article takes you through the key design decisions you must make before creating an isolated SharePoint Online team site.</span></span>
  
## <a name="phase-1-determine-your-sharepoint-groups-and-permission-levels"></a><span data-ttu-id="6259a-106">1 단계: SharePoint 그룹 및 권한 수준 결정</span><span class="sxs-lookup"><span data-stu-id="6259a-106">Phase 1: Determine your SharePoint groups and permission levels</span></span>

<span data-ttu-id="6259a-107">기본적으로 모든 SharePoint Online 팀 사이트는 다음과 같은 SharePoint 그룹을 사용 하 여 만든은:</span><span class="sxs-lookup"><span data-stu-id="6259a-107">Every SharePoint Online team site by default is created with the following SharePoint groups:</span></span>
  
- <span data-ttu-id="6259a-108">\<사이트 이름 > 구성원</span><span class="sxs-lookup"><span data-stu-id="6259a-108">\<site name> Members</span></span>
    
- <span data-ttu-id="6259a-109">\<사이트 이름 > 방문자</span><span class="sxs-lookup"><span data-stu-id="6259a-109">\<site name> Visitors</span></span>
    
- <span data-ttu-id="6259a-110">\<사이트 이름 > 소유자</span><span class="sxs-lookup"><span data-stu-id="6259a-110">\<site name> Owners</span></span>
    
<span data-ttu-id="6259a-111">이러한 그룹은 Office 365 및 Azure Active Directory (AD) 그룹에서 별도 하며 사이트의 리소스에 대 한 사용 권한을 할당 하는 것에 대 한 기초입니다.</span><span class="sxs-lookup"><span data-stu-id="6259a-111">These groups are separate from Office 365 and Azure Active Directory (AD) groups and are the basis for assigning permissions for the resources of the site.</span></span>
  
<span data-ttu-id="6259a-p101">사이트에서 수행 하는 SharePoint 그룹의 구성원 수를 결정 하는 특정 사용 권한 집합 사용 권한 수준입니다. 기본적으로 SharePoint Online 팀 사이트에 대 한 사용 권한 수준이 세: 편집, 읽기 및 모든 권한입니다. 다음 표에서 SharePoint 그룹 및 할당 된 사용 권한 수준을의 기본 상관 관계를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="6259a-p101">The set of specific permissions that determines what a member of a SharePoint group can do in a site is a permission level. There are three permission levels by default for a SharePoint Online team site: Edit, Read, and Full control. The following table shows the default correlation of SharePoint groups and assigned permission levels:</span></span>
  
|<span data-ttu-id="6259a-115">**SharePoint 그룹**</span><span class="sxs-lookup"><span data-stu-id="6259a-115">**SharePoint group**</span></span>|<span data-ttu-id="6259a-116">**사용 권한 수준**</span><span class="sxs-lookup"><span data-stu-id="6259a-116">**Permission level**</span></span>|
|:-----|:-----|
|<span data-ttu-id="6259a-117">\<사이트 이름 > 구성원</span><span class="sxs-lookup"><span data-stu-id="6259a-117">\<site name> Members</span></span>  <br/> |<span data-ttu-id="6259a-118">편집</span><span class="sxs-lookup"><span data-stu-id="6259a-118">Edit</span></span>  <br/> |
|<span data-ttu-id="6259a-119">\<사이트 이름 > 방문자</span><span class="sxs-lookup"><span data-stu-id="6259a-119">\<site name> Visitors</span></span>  <br/> |<span data-ttu-id="6259a-120">읽기</span><span class="sxs-lookup"><span data-stu-id="6259a-120">Read</span></span>  <br/> |
|<span data-ttu-id="6259a-121">\<사이트 이름 > 소유자</span><span class="sxs-lookup"><span data-stu-id="6259a-121">\<site name> Owners</span></span>  <br/> |<span data-ttu-id="6259a-122">모든 권한</span><span class="sxs-lookup"><span data-stu-id="6259a-122">Full control</span></span>  <br/> |
   
 <span data-ttu-id="6259a-p102">**모범 사례:** 추가 SharePoint 그룹 및 권한 수준을 만들 수 있습니다. 격리 된 SharePoint Online 사이트에 대 한 기본 SharePoint 그룹 및 권한 수준을 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="6259a-p102">**Best practice:** You can create additional SharePoint groups and permission levels. However, we recommend using the default SharePoint groups and permission levels for your isolated SharePoint Online site.</span></span>
  
<span data-ttu-id="6259a-125">다음은 기본 SharePoint 그룹 및 권한 수준입니다.</span><span class="sxs-lookup"><span data-stu-id="6259a-125">Here are the default SharePoint groups and permission levels.</span></span>
  
![SharePoint Online 사이트에 대한 기본 SharePoint 그룹 및 사용 권한 수준입니다.](images/3f892ab4-6479-42f0-a505-1ba0ef94b9c6.png)
  
## <a name="phase-2-assign-permissions-to-users-with-access-groups"></a><span data-ttu-id="6259a-127">2 단계: 액세스 그룹과 사용자에 게 사용 권한 할당</span><span class="sxs-lookup"><span data-stu-id="6259a-127">Phase 2: Assign permissions to users with access groups</span></span>

<span data-ttu-id="6259a-p103">자신의 사용자 계정 또는 Office 365 또는 Azure AD 그룹은 사용자 계정이 SharePoint 그룹에 구성원을 추가 하 여 사용자에 게 사용 권한을 할당할 수 있습니다. 추가 되 면 Office 365 사용자 계정 하거나 직접 또는 간접적으로 Office 365 또는 Azure AD 그룹의 구성원 자격을 통해, SharePoint 그룹에 연결 된 사용 권한 수준에 할당 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6259a-p103">You can assign permissions to users by adding their user account, or an Office 365 or Azure AD group of which the user account is a member, to the SharePoint groups. Once added, the Office 365 user accounts, either directly or indirectly via membership in an Office 365 or Azure AD group, are assigned the permission level associated with the SharePoint group.</span></span>
  
<span data-ttu-id="6259a-130">기본 SharePoint 그룹을 예로 사용:</span><span class="sxs-lookup"><span data-stu-id="6259a-130">Using the default SharePoint groups as an example:</span></span>
  
- <span data-ttu-id="6259a-131">구성원은 ** \<사이트 이름 > 구성원** 모두 사용자 계정 및 그룹을 포함할 수 있는 SharePoint 그룹 **편집** 사용 권한 수준에 할당 된</span><span class="sxs-lookup"><span data-stu-id="6259a-131">Members of the **\<site name> Members** SharePoint group, which can include both user accounts and groups, are assigned the **Edit** permission level</span></span>
    
- <span data-ttu-id="6259a-132">구성원은 ** \<사이트 이름 > 방문자** 모두 사용자 계정 및 그룹을 포함할 수 있는 SharePoint 그룹에 **읽기** 권한 수준에 할당 된</span><span class="sxs-lookup"><span data-stu-id="6259a-132">Members of the **\<site name> Visitors** SharePoint group, which can include both user accounts and groups, are assigned the **Read** permission level</span></span>
    
- <span data-ttu-id="6259a-133">구성원은 ** \<사이트 이름 > 소유자** 모두 사용자 계정 및 그룹을 포함할 수 있는 SharePoint 그룹에 **모든 권한** 사용 권한 수준에 할당 된</span><span class="sxs-lookup"><span data-stu-id="6259a-133">Members of the **\<site name> Owners** SharePoint group, which can include both user accounts and groups, are assigned the **Full control** permission level</span></span>
    
 <span data-ttu-id="6259a-p104">**모범 사례:** 개별 사용자 계정을 통해 사용 권한을 관리할 수는 있지만 단일을 사용 하는 것이 좋습니다 Azure AD 그룹에서 액세스 하는 그룹을 대신 라고 합니다. 각 SharePoint 그룹에 대 한 계정 사용자의 목록을 관리 하지 않고 액세스 그룹의 구성원 자격을 통해 사용 권한 관리가 간편해 집니다.</span><span class="sxs-lookup"><span data-stu-id="6259a-p104">**Best practice:** Although you can manage permissions through individual user accounts, we recommend that you use a single Azure AD group, known as an access group, instead. This simplifies the management of permissions through membership in the access group, rather than managing the list of user accounts for each SharePoint group.</span></span>
  
<span data-ttu-id="6259a-p105">Office 365 용 azure AD 그룹 Office 365 그룹 보다 서로 다릅니다. Azure AD 그룹 **보안** 로 해당 **형식** 을 설정 하 여 Office 관리 센터에 표시 하 고 전자 메일 주소를 갖지 않습니다. Azure AD 그룹 내에서 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6259a-p105">Azure AD groups for Office 365 are different than Office 365 groups. Azure AD groups appear in the Office Admin center with their **Type** set to **Security** and do not have an email address. Azure AD groups can be managed within:</span></span>
  
- <span data-ttu-id="6259a-139">Windows Server Active Directory (AD)</span><span class="sxs-lookup"><span data-stu-id="6259a-139">Windows Server Active Directory (AD)</span></span>
    
    <span data-ttu-id="6259a-p106">다음은 온-프레미스 Windows Server AD 인프라에서 만든 및 Office 365 구독에 동기화 된 그룹입니다. Office 관리 센터에서 이러한 그룹 **Synched active directory와**의 **상태** 를 가집니다.</span><span class="sxs-lookup"><span data-stu-id="6259a-p106">These are groups that have been created in your on-premises Windows Server AD infrastructure and synchronized to your Office 365 subscription. In the Office Admin center, these groups have a **Status** of **Synched with active directory**.</span></span>
    
- <span data-ttu-id="6259a-142">Office 365</span><span class="sxs-lookup"><span data-stu-id="6259a-142">Office 365</span></span>
    
    <span data-ttu-id="6259a-p107">다음은 Office 관리 센터, Azure 포털 또는 Microsoft PowerShell 중 하나를 사용 하 여 만든 그룹입니다. Office 관리 센터에서 이러한 그룹 **클라우드**의 **상태** 를 가집니다.</span><span class="sxs-lookup"><span data-stu-id="6259a-p107">These are groups that have been created using either the Office Admin center, the Azure portal, or Microsoft PowerShell. In the Office Admin center, these groups have a **Status** of **Cloud**.</span></span>
    
 <span data-ttu-id="6259a-145">**모범 사례:** Windows Server AD 온-프레미스를 사용 하 여 Office 365 구독와 동기화 하는 경우 사용자 및 Windows Server AD와 함께 그룹 관리를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="6259a-145">**Best practice:** If you are using Windows Server AD on-premises and synchronizing with your Office 365 subscription, perform your user and group management with Windows Server AD.</span></span>
  
<span data-ttu-id="6259a-146">격리 된 SharePoint Online 팀 사이트, 권장된 그룹 구조는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="6259a-146">For isolated SharePoint Online team sites, the recommended group structure looks like this:</span></span>
  
|<span data-ttu-id="6259a-147">**SharePoint 그룹**</span><span class="sxs-lookup"><span data-stu-id="6259a-147">**SharePoint group**</span></span>|<span data-ttu-id="6259a-148">**Azure AD 기반 액세스 그룹**</span><span class="sxs-lookup"><span data-stu-id="6259a-148">**Azure AD-based access group**</span></span>|<span data-ttu-id="6259a-149">**사용 권한 수준**</span><span class="sxs-lookup"><span data-stu-id="6259a-149">**Permission level**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="6259a-150">\<사이트 이름 > 구성원</span><span class="sxs-lookup"><span data-stu-id="6259a-150">\<site name> Members</span></span>  <br/> |<span data-ttu-id="6259a-151">\<사이트 이름 > 구성원</span><span class="sxs-lookup"><span data-stu-id="6259a-151">\<site name> Members</span></span>  <br/> |<span data-ttu-id="6259a-152">편집</span><span class="sxs-lookup"><span data-stu-id="6259a-152">Edit</span></span>  <br/> |
|<span data-ttu-id="6259a-153">\<사이트 이름 > 방문자</span><span class="sxs-lookup"><span data-stu-id="6259a-153">\<site name> Visitors</span></span>  <br/> |<span data-ttu-id="6259a-154">\<사이트 이름 > 뷰어</span><span class="sxs-lookup"><span data-stu-id="6259a-154">\<site name> Viewers</span></span>  <br/> |<span data-ttu-id="6259a-155">읽기</span><span class="sxs-lookup"><span data-stu-id="6259a-155">Read</span></span>  <br/> |
|<span data-ttu-id="6259a-156">\<사이트 이름 > 소유자</span><span class="sxs-lookup"><span data-stu-id="6259a-156">\<site name> Owners</span></span>  <br/> |<span data-ttu-id="6259a-157">\<사이트 이름 > 관리자</span><span class="sxs-lookup"><span data-stu-id="6259a-157">\<site name> Admins</span></span>  <br/> |<span data-ttu-id="6259a-158">모든 권한</span><span class="sxs-lookup"><span data-stu-id="6259a-158">Full control</span></span>  <br/> |
   
 <span data-ttu-id="6259a-p108">**모범 사례:** SharePoint 그룹의 구성원으로 Office 365 또는 Azure AD 그룹을 사용할 수 있지만 Azure AD 그룹을 사용 하는 것이 좋습니다. Azure AD 그룹, Windows Server AD 또는 Office 365를 통해 관리 되는 사용 권한을 할당 하려면 중첩 된 그룹을 사용 하 여 더 큰 유연성을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="6259a-p108">**Best practice:** Although you can use either Office 365 or Azure AD groups as members of SharePoint groups, we recommend that you use Azure AD groups. Azure AD groups, managed either through Windows Server AD or Office 365, give you more flexibility to use nested groups to assign permissions.</span></span>
  
<span data-ttu-id="6259a-161">다음은 기본 SharePoint 그룹 Azure AD 기반 액세스 그룹을 사용 하도록 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="6259a-161">Here are the default SharePoint groups configured to use Azure AD-based access groups.</span></span>
  
![기본 SharePoint Online 사이트 그룹의 구성원으로 액세스 그룹을 사용합니다.](images/50a76328-ae69-483e-9029-ac4e7357b5ef.png)
  
<span data-ttu-id="6259a-163">세 액세스 그룹을 디자인할 때 다음 사항에 유의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6259a-163">When designing the three access groups, keep the following in mind:</span></span>
  
- <span data-ttu-id="6259a-164">일부 구성원만 있어야는 ** \<사이트 이름 > Admins** 액세스 그룹에서 해당 하는 소수의 팀 사이트를 관리 하는 SharePoint Online 관리자입니다.</span><span class="sxs-lookup"><span data-stu-id="6259a-164">There should be only a few members in the **\<site name> Admins** access group, corresponding to a small number of SharePoint Online administrators who are managing the team site.</span></span>
    
- <span data-ttu-id="6259a-p109">대부분의 사이트 구성원은 ** \<사이트 이름 > 구성원** 또는 ** \<사이트 이름 > 뷰어** 그룹에 액세스 합니다. 때문에 사이트의 구성원은 ** \<사이트 이름 > 구성원** 액세스 그룹을 삭제 하거나 사이트의 리소스를 수정, 신중 하 게 해당 구성원을 고려 하는 기능이 있습니다. 확실에 있을 때 사이트 구성원을 추가할는 ** \<사이트 이름 > 뷰어** 액세스 그룹입니다.</span><span class="sxs-lookup"><span data-stu-id="6259a-p109">Most of your site members are in the **\<site name> Members** or **\<site name> Viewers** access groups. Because site members in the **\<site name> Members** access group have the ability to delete or modify resources in the site, carefully consider its membership. When in doubt, add the site member to the **\<site name> Viewers** access group.</span></span>
    
<span data-ttu-id="6259a-168">SharePoint 그룹 및 ProjectX 라는 격리 된 사이트에 대 한 액세스 그룹의 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="6259a-168">Here is an example of the SharePoint groups and access groups for an isolated site named ProjectX.</span></span>
  
![SharePoint Online 사이트인 ProjectX의 액세스 그룹을 사용한 예입니다.](images/13afe542-9ffd-4671-9f48-210a0e2a502a.png)
  
## <a name="phase-3-use-nested-azure-ad-groups"></a><span data-ttu-id="6259a-170">3 단계: 사용 하 여 중첩 된 Azure AD 그룹</span><span class="sxs-lookup"><span data-stu-id="6259a-170">Phase 3: Use nested Azure AD groups</span></span>

<span data-ttu-id="6259a-p110">사용자 수가 적은 에서만, 프로젝트 사이트의 SharePoint 그룹에 추가 하는 Azure AD 기반 액세스 그룹의 한 수준 대부분의 시나리오 적합 합니다. 그러나 많은 수의 사용자와 해당 사용자를 포함 하는 경우 이미의 구성원 설정 Azure AD 그룹 보다 쉽게 권한을 할당할 수 있습니다 SharePoint 중첩 된 그룹 또는 다른 그룹 구성원으로 포함 된 그룹을 사용 하 여 합니다.</span><span class="sxs-lookup"><span data-stu-id="6259a-p110">For a project confined to a small number of people, a single level of Azure AD-based access groups added to the SharePoint groups of the site will fit most scenarios. However, if you have a large number of people and those people are already members of established Azure AD groups, you can more easily assign SharePoint permissions by using nested groups, or groups that contain other groups as members.</span></span>
  
<span data-ttu-id="6259a-p111">판매, 마케팅, 엔지니어링, 법률의 중역 간의 공동 작업을 위한 격리 된 SharePoint online 팀 사이트 만들기 및 지원 부서 및 해당 부서 이미 임원 사용자 계정 사용 하 여 자신의 그룹 하려는 예 구성원 이어야 합니다. 새 사이트 구성원에 대 한 새 그룹을 만들고 모든 임원 개별 사용자 계정에 배치 하는 대신 각 부서에 대 한 기존 임원 그룹 새 그룹에 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="6259a-p111">For example, you want to create an isolated SharePoint online team site for collaboration among the executives of the sales, marketing, engineering, legal, and support departments and those departments already their own groups with executive user account membership. Rather than creating a new group for the new site members and placing all the individual executive user accounts in it, put the existing executive groups for each department in the new group.</span></span>
  
 <span data-ttu-id="6259a-p112">여러 조직 간에 Office 365 구독을 공유 하는 경우에 조직에 대 한 사이트를 격리에 대 한 그룹 구성원 자격의 단일 수준을 많은 수의 사용자 계정으로 인해 관리 하기가 어려울 될 수 있습니다. 사용할 수는 경우에 사용 권한을 관리 하는 조직 내에서 그룹을 포함 하는 각 조직에 대 한 Azure AD 그룹을 중첩 합니다.</span><span class="sxs-lookup"><span data-stu-id="6259a-p112">If you are sharing an Office 365 subscription between multiple organizations, a single level of group membership for an isolated site for an organization might become difficult to manage due to the sheer number of user accounts. In this case, you can use nested Azure AD groups for each organization that contain the groups within their organizations to manage the permissions.</span></span>
  
<span data-ttu-id="6259a-177">사용 하 여 중첩 된 Azure AD 그룹:</span><span class="sxs-lookup"><span data-stu-id="6259a-177">To use nested Azure AD groups:</span></span>
  
1. <span data-ttu-id="6259a-178">식별 하거나 사용자 계정이 포함 되며 해당 하는 사용자 계정을 구성원으로 추가 하는 Azure AD 그룹을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6259a-178">Identify or create the Azure AD groups that will contain user accounts and add the appropriate user accounts as members.</span></span>
    
2. <span data-ttu-id="6259a-179">다른 Azure AD 그룹 포함 되며 해당 그룹 구성원으로 추가 하는 컨테이너 Azure AD 기반 액세스 그룹을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6259a-179">Create the container Azure AD-based access group that will contain the other Azure AD groups and add those groups as members.</span></span>
    
3.  <span data-ttu-id="6259a-180">SharePoint 그룹 및 해당 사용 권한 수준을 식별 하는 적절 한 컨테이너 액세스 그룹에 대 한 액세스 수준을, 합니다.</span><span class="sxs-lookup"><span data-stu-id="6259a-180">For the appropriate level of access for the container access group, identify the SharePoint group and corresponding permission level.</span></span>
    
> [!NOTE]
> <span data-ttu-id="6259a-181">중첩 된 Office 365 그룹을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6259a-181">You cannot use nested Office 365 groups.</span></span> 
  
<span data-ttu-id="6259a-182">중첩 된 Azure AD의 예가 ProjectX 멤버 액세스 그룹에 대 한 그룹과 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="6259a-182">Here is an example of nested Azure AD groups for the ProjectX member access group.</span></span>
  
![ProjectX 사이트의 구성원 액세스 그룹에 대해 중첩 액세스 그룹을 사용한 예입니다.](images/2abca710-bf9e-4ce8-9bcd-a8e128264fb1.png)
  
<span data-ttu-id="6259a-184">잠재 고객 연구 (영문), 엔지니어링 및 프로젝트에 사용자 계정을 모두 하기 때문에 팀 사이트 구성원이 될 하기 위한 것, 자신의 Azure AD 그룹 ProjectX 멤버 액세스 그룹을 추가 하면 더 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="6259a-184">Because all of the user accounts in the Research, Engineering, and Project leads teams are intended to be site members, it is easier to add their Azure AD groups to the ProjectX Members access group.</span></span>
  
## <a name="next-step"></a><span data-ttu-id="6259a-185">다음 단계</span><span class="sxs-lookup"><span data-stu-id="6259a-185">Next step</span></span>

<span data-ttu-id="6259a-186">만들고 프로덕션 환경에서 격리 된 사이트를 구성 준비가 되 면 [SharePoint Online 팀 사이트를 격리 된 배포](deploy-an-isolated-sharepoint-online-team-site.md)를 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="6259a-186">When you are ready to create and configure an isolated site in production, see [Deploy an isolated SharePoint Online team site](deploy-an-isolated-sharepoint-online-team-site.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="6259a-187">See Also</span><span class="sxs-lookup"><span data-stu-id="6259a-187">See Also</span></span>

[<span data-ttu-id="6259a-188">격리 된 SharePoint Online 팀 사이트</span><span class="sxs-lookup"><span data-stu-id="6259a-188">Isolated SharePoint Online team sites</span></span>](isolated-sharepoint-online-team-sites.md)
  
[<span data-ttu-id="6259a-189">SharePoint Online 팀 사이트를 격리 관리</span><span class="sxs-lookup"><span data-stu-id="6259a-189">Manage an isolated SharePoint Online team site</span></span>](manage-an-isolated-sharepoint-online-team-site.md)
  
[<span data-ttu-id="6259a-190">보안 솔루션</span><span class="sxs-lookup"><span data-stu-id="6259a-190">Security solutions</span></span>](security-solutions.md)

[<span data-ttu-id="6259a-191">SharePoint Online 팀 사이트를 격리를 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="6259a-191">Deploy an isolated SharePoint Online team site</span></span>](deploy-an-isolated-sharepoint-online-team-site.md)



