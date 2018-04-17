---
title: SharePoint Online 사이트 및 파일 보호
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Architecture
ms.assetid: 1d51bd87-17bf-457c-b698-61821de3afa0
description: '요약: SharePoint Online 및 Office 365에서 파일을 보호 하기 위해 구성 권장 합니다.'
ms.openlocfilehash: 800d81d657164b2a936b95764d57fd092cfa21cc
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
---
# <a name="secure-sharepoint-online-sites-and-files"></a><span data-ttu-id="e2f83-103">SharePoint Online 사이트 및 파일 보호</span><span class="sxs-lookup"><span data-stu-id="e2f83-103">Secure SharePoint Online sites and files</span></span>

 <span data-ttu-id="e2f83-104">**요약:** SharePoint Online 및 Office 365에서 파일을 보호 하기 위해 구성 권장 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="e2f83-104">**Summary:** Configuration recommendations for protecting files in SharePoint Online and Office 365.</span></span>
  
<span data-ttu-id="e2f83-p101">이 문서에서는 SharePoint Online 팀 사이트 및 공동 작업의 간편 하 게 균형잡힌 보안을 제공 하는 파일 보호를 구성 하기 위한 권장 사항을 제공 합니다. 이 문서에서는 가장 open 공유 정책 사용 하 여 조직 내에서 공용 사이트로 시작 하 여 4 개의 서로 다른 구성 정의 합니다. 각 추가 구성 보호를 의미 있는 단계를 나타냅니다 하지만 관련 된 사용자 집합에 액세스 하 고 리소스에 공동 작업을 수행 하는 기능 영역이 줄어듭니다. 시작 지점으로 이러한 지침을 사용 하 여 하 고 조정 하 여 조직의 요구 사항에 맞게 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2f83-p101">This article provides recommendations for configuring SharePoint Online team sites and file protection that balances security with ease of collaboration. This article defines four different configurations, starting with a public site within your organization with the most open sharing policies. Each additional configuration represents a meaningful step up in protection, but the ability to access and collaborate on resources is reduced to the relevant set of users. Use these recommendations as a starting point and adjust the configurations to meet the needs of your organization.</span></span> 
  
<span data-ttu-id="e2f83-109">이 문서의 구성은 데이터, ID 및 장치의 3계층 보호에 대한 Microsoft 권장 사항과 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="e2f83-109">The configurations in this article align with Microsoft's recommendations for three tiers of protection for data, identities, and devices:</span></span>
  
- <span data-ttu-id="e2f83-110">초기 보호</span><span class="sxs-lookup"><span data-stu-id="e2f83-110">Baseline protection</span></span>
    
- <span data-ttu-id="e2f83-111">중요 보호</span><span class="sxs-lookup"><span data-stu-id="e2f83-111">Sensitive protection</span></span>
    
- <span data-ttu-id="e2f83-112">극비 보호</span><span class="sxs-lookup"><span data-stu-id="e2f83-112">Highly confidential protection</span></span>
    
<span data-ttu-id="e2f83-113">이러한 계층 및 각 계층에 권장되는 기능에 대한 자세한 내용은 다음 리소스를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e2f83-113">For more information about these tiers and capabilities recommended for each tier, see the following resources.</span></span> 
  
- [<span data-ttu-id="e2f83-114">Office 365용 ID 및 장치 보호</span><span class="sxs-lookup"><span data-stu-id="e2f83-114">Identity and Device Protection for Office 365</span></span>](microsoft-cloud-it-architecture-resources.md#BKMK_O365IDP)
    
- [<span data-ttu-id="e2f83-115">Office 365의 파일 보호 솔루션</span><span class="sxs-lookup"><span data-stu-id="e2f83-115">File Protection Solutions in Office 365</span></span>](microsoft-cloud-it-architecture-resources.md#BKMK_O365fileprotect)
    
## <a name="capability-overview"></a><span data-ttu-id="e2f83-116">기능 개요</span><span class="sxs-lookup"><span data-stu-id="e2f83-116">Capability overview</span></span>

<span data-ttu-id="e2f83-p102">SharePoint Online 팀 사이트에 대한 권장 사항은 다양한 Office 365 기능을 활용합니다. 극비 사이트의 경우 Azure Information Protection을 사용하는 것이 좋습니다. 이는 EMS(Enterprise Mobility + Security)에 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2f83-p102">Recommendations for SharePoint Online team sites draw on a variety of Office 365 capabilities. For highly confidential sites, Azure Information Protection is recommended. This is included in Enterprise Mobility + Security (EMS).</span></span> 
  
<span data-ttu-id="e2f83-120">다음 그림에는 4 개의 SharePoint Online 팀 사이트에 대 한 권장된 구성을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="e2f83-120">The following illustration shows the recommended configurations for four SharePoint Online team sites.</span></span>
  
![SharePoint 사이트에 대한 권장 구성](images/ad0dcd70-f6f5-465c-8d16-1889481ca07a.png)
  
<span data-ttu-id="e2f83-122">그림에서 보여 주듯이 다음과 같이 설명됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2f83-122">As illustrated:</span></span>
  
- <span data-ttu-id="e2f83-p103">초기 보호에는 SharePoint Online 팀 사이트(공용 사이트 및 개인 사이트)에 대한 두 가지 옵션이 있습니다. 공용 사이트는 조직의 모든 사용자가 검색하고 액세스할 수 있습니다. 개인 사이트는 사이트의 구성원만 검색하고 액세스할 수 있습니다. 이 두 사이트 모두의 구성에서는 그룹 외부와의 공유를 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="e2f83-p103">Baseline protection includes two options for SharePoint Online team sites — a public site and private site. Public sites can be discovered and accessed by anybody in the organization. Private sites can only be discovered and accessed by members of the site. Both of these site configurations allow for sharing outside the group.</span></span> 
    
- <span data-ttu-id="e2f83-127">중요한 기밀 보호의 대상이 되는 사이트는 특정 그룹의 구성원에게만 액세스가 제한되는 개인 사이트입니다.</span><span class="sxs-lookup"><span data-stu-id="e2f83-127">Sites for sensitive and highly confidential protection are private sites with access limited only to members of specific groups.</span></span>
    
- <span data-ttu-id="e2f83-p104">Office 365 레이블에서는 필요한 보호 수준을 사용하여 데이터를 분류하는 방법을 제공합니다. SharePoint Online 팀 사이트마다 사이트에 대한 기본 레이블을 통해 문서 라이브러리의 파일에 자동으로 레이블을 지정하도록 구성됩니다. 4가지 사이트 구성에 해당하는 이 예의 레이블은 내부 공용, 개인, 중요, 및 극비입니다. 사용자는 레이블을 변경할 수 있지만 이 구성은 모든 파일에서 기본 레이블을 받도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2f83-p104">Office 365 labels provide a way to classify data with a needed protection level. Each of the SharePoint Online team sites are configured to automatically label files in document libraries with a default label for the site. Corresponding to the four site configurations, the labels in this example are Internal Public, Private, Sensitive, and Highly Confidential. Users can change the labels, but this configuration ensures all files receive a default label.</span></span>
    
- <span data-ttu-id="e2f83-132">사용자가 조직 외부로 이러한 종류의 파일을 보내려고 할 때 경고하거나 방지하기 위해 중요 및 극비 Office 365 레이블에 대한 DLP(데이터 손실 방지) 정책이 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2f83-132">Data loss prevention (DLP) policies are configured for the Sensitive and Highly Confidential Office 365 labels to either warn or prevent users when they attempt to send these types of files outside the organization.</span></span>
    
- <span data-ttu-id="e2f83-133">극비 보호로 구성된 사이트의 경우 Azure Information Protection은 파일에 대한 권한을 암호화하고 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="e2f83-133">For sites configured with highly confidential protection, Azure Information Protection encrypts and grants permissions for files.</span></span>
    
## <a name="tenant-wide-settings-for-sharepoint-online-and-onedrive-for-business"></a><span data-ttu-id="e2f83-134">SharePoint Online 및 비즈니스용 OneDrive에 대한 테넌트 수준 설정</span><span class="sxs-lookup"><span data-stu-id="e2f83-134">Tenant-wide settings for SharePoint Online and OneDrive for Business</span></span>

<span data-ttu-id="e2f83-p105">SharePoint Online 및 비즈니스용 OneDrive에는 모든 사이트 및 사용자에게 영향을 주는 테넌트 수준 설정이 포함됩니다. 또한 이러한 설정 중 일부는 사이트 수준에서 더 제한적으로 조정할 수 있지만 해당 제한을 완화할 수는 없습니다. 이 섹션에서는 보안 및 공동 작업에 영향을 주는 테넌트 수준 설정에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e2f83-p105">SharePoint Online and OneDrive for Business include tenant-wide settings that affect all sites and users. Some of these settings can also be adjusted at the site level to be more restrictive (but not less). This section discusses tenant-wide settings that affect security and collaboration.</span></span> 
  
### <a name="sharing"></a><span data-ttu-id="e2f83-138">공유</span><span class="sxs-lookup"><span data-stu-id="e2f83-138">Sharing</span></span>

<span data-ttu-id="e2f83-139">이 솔루션의 경우 다음과 같은 테넌트 수준 설정을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="e2f83-139">For this solution, we recommend the following tenant-wide settings:</span></span>
  
- <span data-ttu-id="e2f83-140">익명 공유를 포함하여 모든 계정 유형과 공유할 수 있도록 허용하는 기본 공유 정책을 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="e2f83-140">Keep the default sharing policy that allows all sharing with all account types, including anonymous sharing.</span></span>
    
- <span data-ttu-id="e2f83-141">필요한 경우 익명 연결이 만료되도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e2f83-141">Set anonymous links to expire, if desired.</span></span>
    
- <span data-ttu-id="e2f83-p106">공유할 기본 연결 종류를 내부로 변경합니다. 이렇게 하면 실수로 데이터를 조직 외부로 누출하지 않도록 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2f83-p106">Change the default link type for sharing to Internal. This helps prevent accidental data leakage outside your organization.</span></span>
    
<span data-ttu-id="e2f83-p107">외부 공유를 허용하는 것이 반직관적일 수 있지만, 이 방법은 전자 메일로 파일을 보내는 것에 비해 파일 공유를 다 자세히 제어합니다. SharePoint Online과 Outlook은 함께 작동하여 파일에 대해 안전한 공동 작업을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e2f83-p107">While it might seem counterintuitive to allow external sharing, this approach provides more control over file sharing compared to sending files in email. SharePoint Online and Outlook work together to provide secure collaboration on files.</span></span> 
  
- <span data-ttu-id="e2f83-146">기본적으로 Outlook은 전자 메일로 파일을 보내는 대신 파일에 대한 링크를 공유합니다.</span><span class="sxs-lookup"><span data-stu-id="e2f83-146">By default, Outlook shares a link to a file instead of sending the file in email.</span></span> 
    
- <span data-ttu-id="e2f83-147">SharePoint Online 및 비즈니스용 OneDrive 쉽게 내부와 조직 외부에 있는 참가자와 파일에 대 한 링크를 공유 하려면</span><span class="sxs-lookup"><span data-stu-id="e2f83-147">SharePoint Online and OneDrive for Business make it easy to share links to files with contributors who are both inside and outside your organization</span></span>
    
<span data-ttu-id="e2f83-p108">또한 외부 공유를 관리하는 데 도움이 되는 제어가 있습니다. 예를 들어, 다음을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2f83-p108">You also have controls to help govern external sharing. For example, you can:</span></span>
  
- <span data-ttu-id="e2f83-150">익명 게스트 링크를 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e2f83-150">Disable an anonymous guest link.</span></span>
    
- <span data-ttu-id="e2f83-151">사이트에 대한 사용자 액세스를 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="e2f83-151">Revoke user access to a site.</span></span>
    
- <span data-ttu-id="e2f83-152">특정 사이트 또는 문서에 대한 액세스 권한이 있는 사용자인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e2f83-152">See who has access to a specific site or document.</span></span>
    
- <span data-ttu-id="e2f83-153">익명 공유 링크 만료를 설정합니다(테넌트 설정).</span><span class="sxs-lookup"><span data-stu-id="e2f83-153">Set anonymous sharing links to expire (tenant setting).</span></span>
    
- <span data-ttu-id="e2f83-154">조직 외부에서 공유할 수 있는 사용자를 제한합니다(테넌트 설정).</span><span class="sxs-lookup"><span data-stu-id="e2f83-154">Limit who can share outside your organization (tenant setting).</span></span>
    
### <a name="use-external-sharing-together-with-data-loss-prevention-dlp"></a><span data-ttu-id="e2f83-155">DLP(데이터 손실 방지)와 함께 외부 공유 사용</span><span class="sxs-lookup"><span data-stu-id="e2f83-155">Use external sharing together with data loss prevention (DLP)</span></span>

<span data-ttu-id="e2f83-p109">외부 공유 하는 것이 없도록, 대체 도구 및 방법 비즈니스를 사용 하는 사용자를 찾을 수 필요 합니다. 중요 한 및 기밀 파일을 보호 하기 위해 DLP 정책을 사용 하 여 외부 공유를 결합 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="e2f83-p109">If you don't allow external sharing, users with a business need will find alternate tools and methods. Microsoft recommends you combine external sharing with DLP policies to protect sensitive and highly confidential files.</span></span>
  
### <a name="device-access-settings"></a><span data-ttu-id="e2f83-158">장치 액세스 설정</span><span class="sxs-lookup"><span data-stu-id="e2f83-158">Device access settings</span></span>

<span data-ttu-id="e2f83-p110">SharePoint Online 및 비즈니스용 OneDrive에 대 한 장치 액세스 설정을 통해 access 브라우저 전용으로 제한 되는지 확인 (파일을 다운로드할 수 없습니다.) 액세스를 차단 하는 경우 또는 합니다. 이러한 설정은 현재 최초 버전에 및 테 넌 트 수준을 적용 합니다. 사이트 수준에서 장치 액세스 정책을 구성 하는 기능을는 곧 제공 될 예정입니다. 이 솔루션에 대 한 하지 테 넌 트 수준에 적용 되는 장치 액세스 설정을 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="e2f83-p110">Device access settings for SharePoint Online and OneDrive for Business let you determine whether access is limited to browser only (files can't be downloaded) or if access is blocked. These settings are currently in First Release and apply tenant-wide. Coming soon is the ability to configure device access policies at the site level. For this solution, we recommend not using device access settings that apply tenant-wide.</span></span>
  
<span data-ttu-id="e2f83-163">첫 번째 릴리스에 있는 장치 액세스 설정을 사용하려면 [Office 365에서 표준 또는 첫 번째 릴리스 옵션을 설정](https://support.office.com/article/Set-up-the-Standard-or-First-Release-options-in-Office-365-3B3ADFA4-1777-4FF0-B606-FB8732101F47)합니다.</span><span class="sxs-lookup"><span data-stu-id="e2f83-163">To use device access settings while these are in first release: [Set up the Standard or First Release Options in Office 365](https://support.office.com/article/Set-up-the-Standard-or-First-Release-options-in-Office-365-3B3ADFA4-1777-4FF0-B606-FB8732101F47).</span></span>
  
### <a name="onedrive-for-business"></a><span data-ttu-id="e2f83-164">비즈니스용 OneDrive</span><span class="sxs-lookup"><span data-stu-id="e2f83-164">OneDrive for Business</span></span>

<span data-ttu-id="e2f83-p111">이러한 설정을 방문하여 비즈니스용 OneDrive 사이트에 대한 기본 설정을 변경할지 여부를 결정합니다. 현재 공유 및 장치 액세스 설정은 SharePoint Online 관리 센터에서 복제되어 두 환경 모두에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2f83-p111">Visit these settings to decide if you want to change the default settings for OneDrive for Business sites. Currently, the sharing and device access settings are duplicated from the SharePoint Online admin center and apply to both environments.</span></span>
  
## <a name="sharepoint-team-site-configuration"></a><span data-ttu-id="e2f83-167">SharePoint 팀 사이트 구성</span><span class="sxs-lookup"><span data-stu-id="e2f83-167">SharePoint team site configuration</span></span>

<span data-ttu-id="e2f83-p112">다음 표에서는 이 문서의 앞부분에서 설명한 팀 사이트 각각에 대한 구성을 요약하고 있습니다. 이러한 구성을 시작하기 위한 권장 사항으로 사용하고, 조직의 요구 사항에 맞게 사이트 유형 및 구성을 조정합니다. 모든 조직에 모든 유형의 사이트가 필요한 것은 아니며, 소수의 조직에만 극비 보호가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="e2f83-p112">The following table summarizes the configuration for each of the team sites described earlier in this article. Use these configurations as starting point recommendations and adjust the site types and configurations to meet the needs of your organization. Not every organization needs every type of site. Only a small number of organizations require highly confidential protection.</span></span>
  
||||||
|:-----|:-----|:-----|:-----|:-----|
||<span data-ttu-id="e2f83-172">**초기 보호 #1**</span><span class="sxs-lookup"><span data-stu-id="e2f83-172">**Baseline protection #1**</span></span> <br/> |<span data-ttu-id="e2f83-173">**초기 보호 #2**</span><span class="sxs-lookup"><span data-stu-id="e2f83-173">**Baseline protection #2**</span></span> <br/> |<span data-ttu-id="e2f83-174">**중요 보호**</span><span class="sxs-lookup"><span data-stu-id="e2f83-174">**Sensitive protection**</span></span> <br/> |<span data-ttu-id="e2f83-175">**극비**</span><span class="sxs-lookup"><span data-stu-id="e2f83-175">**Highly confidential**</span></span> <br/> |
|<span data-ttu-id="e2f83-176">설명</span><span class="sxs-lookup"><span data-stu-id="e2f83-176">Description</span></span>  <br/> |<span data-ttu-id="e2f83-177">조직 내에서 검색 및 공동 작업을 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="e2f83-177">Open discovery and collaboration within the organization.</span></span>  <br/> |<span data-ttu-id="e2f83-178">그룹 외부와의 공유가 허용되는 개인 사이트 및 그룹입니다.</span><span class="sxs-lookup"><span data-stu-id="e2f83-178">Private site and group with sharing allowed outside the group.</span></span>  <br/> |<span data-ttu-id="e2f83-p113">격리된 사이트이며, 액세스 수준이 특정 그룹의 구성원으로 정의됩니다. 사이트의 구성원에게만 공유가 허용됩니다. DLP에서 조직 외부로 파일을 보내려고 할 때 사용자에게 경고합니다.</span><span class="sxs-lookup"><span data-stu-id="e2f83-p113">Isolated site, in which levels of access are defined by membership in specific groups. Sharing is only allowed to members of the site. DLP warns users when attempting to send files outside the organization.</span></span>  <br/> |<span data-ttu-id="e2f83-p114">Azure Information Protection을 사용한 파일 암호화 및 권한 부여로 격리된 사이트입니다. DLP에서 사용자가 조직 외부로 파일을 보내지 못하도록 방지합니다.</span><span class="sxs-lookup"><span data-stu-id="e2f83-p114">Isolated site + file encryption and permissions with Azure Information Protection. DLP prevents users from sending files outside the organization.</span></span>  <br/> |
|<span data-ttu-id="e2f83-184">개인 또는 공용 팀 사이트</span><span class="sxs-lookup"><span data-stu-id="e2f83-184">Private or public team site</span></span>  <br/> |<span data-ttu-id="e2f83-185">Public</span><span class="sxs-lookup"><span data-stu-id="e2f83-185">Public</span></span>  <br/> |<span data-ttu-id="e2f83-186">개인</span><span class="sxs-lookup"><span data-stu-id="e2f83-186">Private</span></span>  <br/> |<span data-ttu-id="e2f83-187">개인</span><span class="sxs-lookup"><span data-stu-id="e2f83-187">Private</span></span>  <br/> |<span data-ttu-id="e2f83-188">개인</span><span class="sxs-lookup"><span data-stu-id="e2f83-188">Private</span></span>  <br/> |
|<span data-ttu-id="e2f83-189">액세스 가능한 사용자</span><span class="sxs-lookup"><span data-stu-id="e2f83-189">Who has access?</span></span>  <br/> |<span data-ttu-id="e2f83-190">B2B 사용자 및 게스트 사용자를 포함한 조직의 모든 사용자</span><span class="sxs-lookup"><span data-stu-id="e2f83-190">Everybody in the organization, including B2B users and guest users.</span></span>  <br/> |<span data-ttu-id="e2f83-p115">사이트 구성원만 - 다른 사용자는 액세스를 요청할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2f83-p115">Members of the site only. Others can request access.</span></span>  <br/> |<span data-ttu-id="e2f83-p116">사이트 구성원만 - 다른 사용자는 액세스를 요청할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2f83-p116">Members of the site only. Others can request access.</span></span>  <br/> |<span data-ttu-id="e2f83-p117">구성원만 - 다른 사용자는 액세스를 요청할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e2f83-p117">Members only. Others cannot request access.</span></span>  <br/> |
|<span data-ttu-id="e2f83-197">사이트 수준 공유 제어</span><span class="sxs-lookup"><span data-stu-id="e2f83-197">Site-level sharing controls</span></span>  <br/> |<span data-ttu-id="e2f83-p118">모든 사용자에게 공유가 허용됩니다. 기본 설정입니다.</span><span class="sxs-lookup"><span data-stu-id="e2f83-p118">Sharing allowed with anybody. Default settings.</span></span>  <br/> |<span data-ttu-id="e2f83-p119">모든 사용자에게 공유가 허용됩니다. 기본 설정입니다.</span><span class="sxs-lookup"><span data-stu-id="e2f83-p119">Sharing allowed with anybody. Default settings.</span></span>  <br/> |<span data-ttu-id="e2f83-202">구성원은 사이트에 대한 액세스를 공유할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e2f83-202">Members cannot share access to the site.</span></span>  <br/> <span data-ttu-id="e2f83-203">구성원이 아닌 사용자는 사이트에 대한 액세스를 요청할 수 있지만, 사이트 관리자가 이러한 요청을 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2f83-203">Non-members can request access to the site, but these requests need to be addressed by a site administrator.</span></span>  <br/> |<span data-ttu-id="e2f83-204">구성원은 사이트에 대한 액세스를 공유할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e2f83-204">Members cannot share access to the site.</span></span>  <br/> <span data-ttu-id="e2f83-205">구성원이 아닌 사용자는 사이트 또는 콘텐츠에 대한 액세스를 요청할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e2f83-205">Non-members cannot request access to the site or contents.</span></span>  <br/> |
|<span data-ttu-id="e2f83-206">사이트 수준 장치 액세스 제어</span><span class="sxs-lookup"><span data-stu-id="e2f83-206">Site-level device access controls</span></span>  <br/> |<span data-ttu-id="e2f83-207">추가 제어가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e2f83-207">No additional controls.</span></span>  <br/> |<span data-ttu-id="e2f83-208">추가 제어가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e2f83-208">No additional controls.</span></span>  <br/> |<span data-ttu-id="e2f83-p120">사이트 수준 제어가 곧 제공될 예정이며, 사용자는 비호환 또는 비도메인 가입 장치로 파일을 다운로드할 수 없습니다. 이렇게 하면 다른 모든 장치에서 브라우저 전용으로 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2f83-p120">Site-level controls are coming soon, which prevents users from downloading files to non-compliant or non-domain joined devices. This allows browser-only access from all other devices.</span></span>  <br/> |<span data-ttu-id="e2f83-211">파일을 비호환 또는 비도메인 가입 장치로 다운로드할 수 없도록 차단하는 사이트 수준 제어가 곧 제공될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="e2f83-211">Site-level controls are coming soon, which blocks downloading of files to non-compliant or non-domain joined devices.</span></span>  <br/> |
|<span data-ttu-id="e2f83-212">Office 365 레이블</span><span class="sxs-lookup"><span data-stu-id="e2f83-212">Office 365 labels</span></span>  <br/> |<span data-ttu-id="e2f83-213">내부 공용</span><span class="sxs-lookup"><span data-stu-id="e2f83-213">Internal Public</span></span>  <br/> |<span data-ttu-id="e2f83-214">개인</span><span class="sxs-lookup"><span data-stu-id="e2f83-214">Private</span></span>  <br/> |<span data-ttu-id="e2f83-215">중요</span><span class="sxs-lookup"><span data-stu-id="e2f83-215">Sensitive</span></span>  <br/> |<span data-ttu-id="e2f83-216">극비</span><span class="sxs-lookup"><span data-stu-id="e2f83-216">Highly Confidential</span></span>  <br/> |
|<span data-ttu-id="e2f83-217">DLP 정책</span><span class="sxs-lookup"><span data-stu-id="e2f83-217">DLP policies</span></span>  <br/> |||<span data-ttu-id="e2f83-218">레이블이 중요 계층으로 지정된 파일을 조직 외부로 보낼 때 사용자에게 경고합니다.</span><span class="sxs-lookup"><span data-stu-id="e2f83-218">Warn users when sending files that are labeled as Sensitive outside the organization.</span></span>  <br/> <span data-ttu-id="e2f83-219">신용 카드 번호 또는 기타 개인 데이터와 같은 중요 데이터 형식의 외부 공유를 차단하기 위해 이러한 데이터 형식(구성한 사용자 지정 데이터 형식 포함)에 대한 추가 DLP 정책을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2f83-219">To block external sharing of sensitive data types, such as credit card numbers or other personal data, you can configure additional DLP policies for these data types (including custom data types you configure).</span></span>  <br/> |<span data-ttu-id="e2f83-p121">사용자가 극비 계층으로 레이블이 지정된 파일을 외부 조직으로 보내지 못하도록 차단합니다. 사용자(파일을 공유하는 사용자 포함)는 근거를 제공하여 이 설정을 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2f83-p121">Block users from sending files that are labeled as highly confidential outside organization. Allow users to override this by providing justification, including who they are sharing the file with.</span></span>  <br/> |
|<span data-ttu-id="e2f83-222">Azure Information Protection</span><span class="sxs-lookup"><span data-stu-id="e2f83-222">Azure Information Protection</span></span>  <br/> ||||<span data-ttu-id="e2f83-p122">Azure 정보 보호를 사용 하 여 자동으로 암호화 하 고 파일에 사용 권한을 부여 합니다. 자신이 유출 되는 경우이 보호 된 파일 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2f83-p122">Use Azure Information Protection to automatically encrypt and grant permissions to files. This protection travels with the files in case they are leaked.</span></span>  <br/> <span data-ttu-id="e2f83-p123">Office 365 Azure 정보 보호를 사용 하 여 암호화 된 파일을 읽을 수 없습니다. 또한 DLP 정책 (레이블 포함) 메타 데이터를 포함 하지만 (예: 파일 내에서 신용 카드 번호) 이러한 파일의 내용이 아니라 포함 작동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2f83-p123">Office 365 cannot read files encrypted with Azure Information Protection. Additionally, DLP policies can only work with the metadata (including labels) but not the contents of these files (such as credit card numbers within files).</span></span>  <br/> |
   
<span data-ttu-id="e2f83-p124">4 개의 서로 다른 유형의이 솔루션의 SharePoint Online 팀 사이트를 배포 하는 단계를 [보호의 세 계층에 대 한 배포 SharePoint Online 사이트](deploy-sharepoint-online-sites-for-three-tiers-of-protection.md)를 참조 하십시오. 개발/테스트 환경 만들기, [개발/테스트 환경에서 SharePoint Online 보안 사이트](secure-sharepoint-online-sites-in-a-dev-test-environment.md)를 참조 하는 단계입니다.</span><span class="sxs-lookup"><span data-stu-id="e2f83-p124">For the steps to deploy the four different types of SharePoint Online team sites in this solution, see [Deploy SharePoint Online sites for three tiers of protection](deploy-sharepoint-online-sites-for-three-tiers-of-protection.md). For the steps to create a dev/test environment, see [Secure SharePoint Online sites in a dev/test environment](secure-sharepoint-online-sites-in-a-dev-test-environment.md).</span></span> 
  
## <a name="office-365-classification-and-labels"></a><span data-ttu-id="e2f83-229">Office 365 분류 및 레이블</span><span class="sxs-lookup"><span data-stu-id="e2f83-229">Office 365 classification and labels</span></span>

<span data-ttu-id="e2f83-p125">Office 365 레이블을 사용 하 여 중요 한 데이터가 포함 된 환경에 대 한 것이 좋습니다. 하 고 나면 구성 하 고 Office 365 레이블을 게시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2f83-p125">Using Office 365 labels is recommended for environments with sensitive data. After you configure and publish Office 365 labels:</span></span>
  
- <span data-ttu-id="e2f83-232">해당 라이브러리의 모든 문서 기본 레이블을 받도록 기본 레이블 SharePoint Online 팀 사이트의 문서 라이브러리에 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2f83-232">You can apply a default label to a document library in a SharePoint Online team site, so that all documents in that library get the default label.</span></span> 
    
- <span data-ttu-id="e2f83-233">적용할 수 있습니다 레이블 콘텐츠를 자동으로 특정 조건에 맞으면.</span><span class="sxs-lookup"><span data-stu-id="e2f83-233">You can apply labels to content automatically if it matches specific conditions.</span></span>
    
- <span data-ttu-id="e2f83-234">Office 365 레이블을 기반으로 하는 DLP 정책을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2f83-234">You can apply DLP policies that are based on Office 365 labels.</span></span>
    
- <span data-ttu-id="e2f83-p126">조직의 사용자에 게 콘텐츠에 적용할 수 레이블을 수동으로 웹에서 Outlook에서 Outlook 2010 이상, 비즈니스, SharePoint Online 및 Office 365 그룹에 대 한 OneDrive 합니다. 사용자가 자주 알고 있는 가장 콘텐츠 유형은 사용 중인, 분류 하 고 적절 한 DLP 정책이 적용 된 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2f83-p126">People in your organization can apply a label manually to content in Outlook on the web, Outlook 2010 and later, OneDrive for Business, SharePoint Online, and Office 365 groups. Users often know best what type of content they're working with, so they can classify it and have the appropriate DLP policy applied.</span></span>
    
![SharePoint 사이트에 대한 권장 구성](images/7fed0126-ab4a-4480-922c-681970642339.png)
  
<span data-ttu-id="e2f83-238">그림에서 보여 주듯이 이 솔루션에는 다음과 같은 레이블 만들기가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2f83-238">As illustrated, this solution includes creating the following labels:</span></span>
  
- <span data-ttu-id="e2f83-239">극비</span><span class="sxs-lookup"><span data-stu-id="e2f83-239">Highly Confidential</span></span>
    
- <span data-ttu-id="e2f83-240">중요</span><span class="sxs-lookup"><span data-stu-id="e2f83-240">Sensitive</span></span>
    
- <span data-ttu-id="e2f83-241">개인</span><span class="sxs-lookup"><span data-stu-id="e2f83-241">Private</span></span>
    
- <span data-ttu-id="e2f83-242">내부 공용</span><span class="sxs-lookup"><span data-stu-id="e2f83-242">Internal Public</span></span>
    
<span data-ttu-id="e2f83-p127">이러한 레이블은 그림에서 권장 되는 사이트와이 문서의 앞부분에서 차트에 매핑됩니다. 이 솔루션의 대부분은 중요 하지과 매우 기밀로 표시 된 파일 누출 방지 하려면 DLP 정책을 구성 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="e2f83-p127">These labels are mapped to the recommended sites in the illustrations and charts earlier in this article. This solution recommends configuring DLP policies to help prevent the leakage of files labeled as Sensitive and Highly Confidential.</span></span>
  
<span data-ttu-id="e2f83-245">이 솔루션에서 Office 365 레이블 및 DLP 정책을 구성하는 단계는 [Office 365 레이블 및 DLP(데이터 손실 방지)를 사용하여 SharePoint Online 파일 보호](protect-sharepoint-online-files-with-office-365-labels-and-dlp.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e2f83-245">For the steps to configure Office 365 labels and DLP policies in this solution, see [Protect SharePoint Online files with Office 365 labels and DLP](protect-sharepoint-online-files-with-office-365-labels-and-dlp.md).</span></span>
  
## <a name="azure-information-protection"></a><span data-ttu-id="e2f83-246">Azure Information Protection</span><span class="sxs-lookup"><span data-stu-id="e2f83-246">Azure Information Protection</span></span>

<span data-ttu-id="e2f83-p128">Azure Information Protection을 사용하여 어디서나 파일과 동반하는 레이블과 보호를 적용합니다. 이 솔루션의 경우 Azure Information Protection 범위 지정 정책 및 극비 레이블의 하위 레이블을 사용하여 최고 수준의 보안으로 보호해야 하는 파일에 대한 권한을 암호화하고 부여하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="e2f83-p128">Use Azure Information Protection to apply labels and protections that follow the files wherever they go. For this solution, we recommend you use a scoped Azure Information Protection policy and a sub-label of the Highly Confidential label to encrypt and grant permissions to files that need to be protected with the highest level of security.</span></span> 
  
<span data-ttu-id="e2f83-p129">Office 365에 저장된 파일에 Azure Information Protection 암호화가 적용되어 있으면 이 파일의 내용을 처리할 수 없습니다. 즉 공동 작성, eDiscovery, 검색, Delve 및 기타 공동 작업 기능이 작동하지 않습니다. DLP 정책은 메타데이터(Office 365 레이블 포함)에만 작동할 수 있지만 파일의 내용(예: 파일 내의 신용 카드 번호)에는 작동할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e2f83-p129">Be aware that when Azure Information Protection encryption is applied to files stored in Office 365, the service cannot process the contents of these files. Co-authoring, eDiscovery, search, Delve, and other collaborative features do not work. DLP policies can only work with the metadata (including Office 365 labels) but not the contents of these files (such as credit card numbers within files).</span></span>
  
![Azure에서 Azure Information Protection을 구성하고 클라이언트 도구 모음에 레이블을 표시합니다.](images/1266a7a0-5078-49ab-bbf1-b0cf41451f62.png)
  
<span data-ttu-id="e2f83-253">그림에서 보여 주듯이 다음과 같이 설명됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2f83-253">As illustrated:</span></span>
  
- <span data-ttu-id="e2f83-p130">Microsoft Azure 포털에서 Azure 정보 보호 정책 및 레이블을 구성합니다. 범위가 지정 된 Azure 정보 보호 정책의 하위 레이블을 구성 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="e2f83-p130">You configure Azure Information Protection policies and labels in the Microsoft Azure portal. Configuring a sub-label of a scoped Azure Information Protection policy is recommended.</span></span>
    
- <span data-ttu-id="e2f83-256">Azure 정보 보호를 Office 응용 프로그램의 **정보 보호** 막대로 표시를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e2f83-256">Azure Information Protection labels show up as an **Information protection** bar in Office applications.</span></span>
    
### <a name="adding-permissions-for-external-users"></a><span data-ttu-id="e2f83-257">외부 사용자에 대한 권한 추가</span><span class="sxs-lookup"><span data-stu-id="e2f83-257">Adding permissions for external users</span></span>

<span data-ttu-id="e2f83-p131">두 가지 방법으로 Azure 정보 보호를 사용 하 여 보호 된 파일에 대 한 액세스를 외부 사용자에 게 부여 합니다. 두이 경우 모두에서 외부 사용자에 게 Azure AD 계정이 있어야 합니다. 외부 사용자에 게 Azure AD를 사용 하는 조직 구성원 하지 않으면 이러한 얻을 수 Azure AD 계정을 개인으로이 등록 페이지를 사용 하 여: [https://aka.ms/aip-signup](https://aka.ms/aip-signup)합니다.</span><span class="sxs-lookup"><span data-stu-id="e2f83-p131">There are two ways you can grant external users access to files protected with Azure Information Protection. In both these cases, external users must have an Azure AD account. If external users aren't members of an organization that uses Azure AD, they can obtain an Azure AD account as an individual by using this sign-up page: [https://aka.ms/aip-signup](https://aka.ms/aip-signup).</span></span>
  
- <span data-ttu-id="e2f83-261">외부 사용자에 게 레이블에 대 한 보호를 구성 하는데 사용 되는 Azure AD 그룹 추가</span><span class="sxs-lookup"><span data-stu-id="e2f83-261">Add external users to an Azure AD group that is used to configure protection for a label</span></span>
    
     <span data-ttu-id="e2f83-p132">먼저 디렉터리의 B2B 사용자 계정을 추가 해야 합니다. [Azure 권한 관리 하 여 캐싱을 그룹 구성원](https://docs.microsoft.com/information-protection/plan-design/prepare#group-membership-caching-by-azure-rights-management)에 대 한 시간 정도 걸릴 수 있습니다. 이 메서드를 사용 하는 레이블 (짝수 보호 되는 파일 Azure AD 그룹에 사용자 추가 되기 전에)를 사용 하 여 보호 하는 모든 기존 파일 권한이 부여 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2f83-p132">You'll need to first add the account as a B2B user in your directory. It can take a couple of hours for [group membership caching by Azure Rights Management](https://docs.microsoft.com/information-protection/plan-design/prepare#group-membership-caching-by-azure-rights-management). With this method, permissions are granted to all existing files protected with the label (even files protected before a user is added to the Azure AD group).</span></span>
    
- <span data-ttu-id="e2f83-265">외부 사용자에 게 레이블 보호에 직접 추가</span><span class="sxs-lookup"><span data-stu-id="e2f83-265">Add external users directly to the label protection</span></span>
    
     <span data-ttu-id="e2f83-p133">조직 (예: Fabrikam.com), (예: 조직 내에서 재무 그룹)는 Azure AD 그룹이 나 개별 사용자의 모든 사용자를 추가할 수 있습니다. 예, 레이블에 대 한 보호 조절기의 외부는 팀을 추가할 수 있습니다. 이 메서드를 사용 권한이 외부 엔터티 보호에 추가 된 후 레이블에 대해 보호 되는 파일에만 부여 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2f83-p133">You can add all users from an organization (e.g. Fabrikam.com), an Azure AD group (such as a finance group within an organization), or an individual user. For example, you can add an external team of regulators to the protection for a label. With this method, permissions are granted only to files protected with the label after the external entity is added to the protection.</span></span>
    
### <a name="deploying-and-using-azure-information-protection"></a><span data-ttu-id="e2f83-269">Azure Information Protection 배포 및 사용</span><span class="sxs-lookup"><span data-stu-id="e2f83-269">Deploying and using Azure Information Protection</span></span>

<span data-ttu-id="e2f83-270">이 솔루션에서 Azure Information Protection을 구성하는 단계는 [Azure Information Protection을 사용하여 SharePoint Online 파일 보호](protect-sharepoint-online-files-with-azure-information-protection.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e2f83-270">For the steps to configure Azure Information Protection in this solution, see [Protect SharePoint Online files with Azure Information Protection](protect-sharepoint-online-files-with-azure-information-protection.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e2f83-271">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e2f83-271">See Also</span></span>

[<span data-ttu-id="e2f83-272">정치적 캠페인, 비영리 조직 및 기타 기밀 조직에 대한 Microsoft 보안 지침</span><span class="sxs-lookup"><span data-stu-id="e2f83-272">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="e2f83-273">보안 솔루션</span><span class="sxs-lookup"><span data-stu-id="e2f83-273">Security solutions</span></span>](security-solutions.md)
  
[<span data-ttu-id="e2f83-274">클라우드 채택 및 하이브리드 솔루션</span><span class="sxs-lookup"><span data-stu-id="e2f83-274">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
[<span data-ttu-id="e2f83-275">개발/테스트 환경의 SharePoint Online 사이트 보호</span><span class="sxs-lookup"><span data-stu-id="e2f83-275">Secure SharePoint Online sites in a dev/test environment</span></span>](secure-sharepoint-online-sites-in-a-dev-test-environment.md)



