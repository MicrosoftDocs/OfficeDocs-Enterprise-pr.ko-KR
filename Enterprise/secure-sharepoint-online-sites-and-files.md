---
title: SharePoint Online 사이트 및 파일 보호
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Architecture
ms.assetid: 1d51bd87-17bf-457c-b698-61821de3afa0
description: '요약: SharePoint Online 및 Office 365에서 파일을 보호하기 위한 구성 권장 사항입니다.'
ms.openlocfilehash: 5ee7ce0f5d52076ec27a3478a39b998a96e0e270
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915083"
---
# <a name="secure-sharepoint-online-sites-and-files"></a><span data-ttu-id="081db-103">SharePoint Online 사이트 및 파일 보호</span><span class="sxs-lookup"><span data-stu-id="081db-103">Secure SharePoint Online sites and files</span></span>

 <span data-ttu-id="081db-104">**요약:** SharePoint Online 및 Office 365에서 파일을 보호하기 위한 구성 권장 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="081db-104">**Summary:** Configuration recommendations for protecting files in SharePoint Online and Office 365.</span></span>
  
<span data-ttu-id="081db-p101">이 문서에서는 SharePoint Online 팀 사이트 및 간편한 공동 작업으로 보안 균형을 조정하는 파일 보호를 구성하기 위한 권장 사항을 제공합니다. 그리고 가장 공개적인 공유 정책을 사용하여 조직 내에서 공용 사이트를 시작하는 별도의 네 가지 구성을 정의합니다. 각각의 추가 구성은 의미 있는 보호 단계를 나타내지만, 리소스에 대한 액세스 및 공동 작업 기능은 관련 사용자 집합으로 축소됩니다. 이러한 권장 사항에 기반하여 시작하고 조직의 요구 사항에 맞게 해당 구성을 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="081db-p101">This article provides recommendations for configuring SharePoint Online team sites and file protection that balances security with ease of collaboration. This article defines four different configurations, starting with a public site within your organization with the most open sharing policies. Each additional configuration represents a meaningful step up in protection, but the ability to access and collaborate on resources is reduced to the relevant set of users. Use these recommendations as a starting point and adjust the configurations to meet the needs of your organization.</span></span> 
  
<span data-ttu-id="081db-109">이 문서의 구성은 데이터, ID 및 장치의 3계층 보호에 대한 Microsoft 권장 사항과 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="081db-109">The configurations in this article align with Microsoft's recommendations for three tiers of protection for data, identities, and devices:</span></span>
  
- <span data-ttu-id="081db-110">초기 보호</span><span class="sxs-lookup"><span data-stu-id="081db-110">Baseline protection</span></span>
    
- <span data-ttu-id="081db-111">중요 보호</span><span class="sxs-lookup"><span data-stu-id="081db-111">Sensitive protection</span></span>
    
- <span data-ttu-id="081db-112">극비 보호</span><span class="sxs-lookup"><span data-stu-id="081db-112">Highly confidential protection</span></span>
    
<span data-ttu-id="081db-113">이러한 계층 및 각 계층에 권장되는 기능에 대한 자세한 내용은 다음 리소스를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="081db-113">For more information about these tiers and capabilities recommended for each tier, see the following resources.</span></span> 
  
- [<span data-ttu-id="081db-114">Office 365용 ID 및 장치 보호</span><span class="sxs-lookup"><span data-stu-id="081db-114">Identity and Device Protection for Office 365</span></span>](microsoft-cloud-it-architecture-resources.md#BKMK_O365IDP)
    
- [<span data-ttu-id="081db-115">Office 365의 파일 보호 솔루션</span><span class="sxs-lookup"><span data-stu-id="081db-115">File Protection Solutions in Office 365</span></span>](microsoft-cloud-it-architecture-resources.md#BKMK_O365fileprotect)
    
## <a name="capability-overview"></a><span data-ttu-id="081db-116">기능 개요</span><span class="sxs-lookup"><span data-stu-id="081db-116">Capability overview</span></span>

<span data-ttu-id="081db-p102">SharePoint Online 팀 사이트에 대한 권장 사항은 다양한 Office 365 기능을 활용합니다. 극비 사이트의 경우 Azure Information Protection을 사용하는 것이 좋습니다. 이는 EMS(Enterprise Mobility + Security)에 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="081db-p102">Recommendations for SharePoint Online team sites draw on a variety of Office 365 capabilities. For highly confidential sites, Azure Information Protection is recommended. This is included in Enterprise Mobility + Security (EMS).</span></span> 
  
<span data-ttu-id="081db-120">다음 그림은 4가지 SharePoint Online 팀 사이트에 권장되는 구성을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="081db-120">The following illustration shows the recommended configurations for four SharePoint Online team sites.</span></span>

![SharePoint 사이트에 대한 권장 구성](Media/SharePoint-site-configuration-v2.png)

<span data-ttu-id="081db-122">그림에서 보여 주듯이 다음과 같이 설명됩니다.</span><span class="sxs-lookup"><span data-stu-id="081db-122">As illustrated:</span></span>
  
- <span data-ttu-id="081db-p103">초기 보호에는 SharePoint Online 팀 사이트(공용 사이트 및 개인 사이트)에 대한 두 가지 옵션이 있습니다. 공용 사이트는 조직의 모든 사용자가 검색하고 액세스할 수 있습니다. 개인 사이트는 사이트의 구성원만 검색하고 액세스할 수 있습니다. 이 두 사이트 모두의 구성에서는 그룹 외부와의 공유를 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="081db-p103">Baseline protection includes two options for SharePoint Online team sites — a public site and private site. Public sites can be discovered and accessed by anybody in the organization. Private sites can only be discovered and accessed by members of the site. Both of these site configurations allow for sharing outside the group.</span></span> 
    
- <span data-ttu-id="081db-127">중요한 기밀 보호의 대상이 되는 사이트는 특정 그룹의 구성원에게만 액세스가 제한되는 개인 사이트입니다.</span><span class="sxs-lookup"><span data-stu-id="081db-127">Sites for sensitive and highly confidential protection are private sites with access limited only to members of specific groups.</span></span>
    
- <span data-ttu-id="081db-p104">Office 365 레이블에서는 필요한 보호 수준을 사용하여 데이터를 분류하는 방법을 제공합니다. SharePoint Online 팀 사이트마다 사이트에 대한 기본 레이블을 통해 문서 라이브러리의 파일에 자동으로 레이블을 지정하도록 구성됩니다. 4가지 사이트 구성에 해당하는 이 예의 레이블은 내부 공용, 개인, 중요, 및 극비입니다. 사용자는 레이블을 변경할 수 있지만 이 구성은 모든 파일에서 기본 레이블을 받도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="081db-p104">Office 365 labels provide a way to classify data with a needed protection level. Each of the SharePoint Online team sites are configured to automatically label files in document libraries with a default label for the site. Corresponding to the four site configurations, the labels in this example are Internal Public, Private, Sensitive, and Highly Confidential. Users can change the labels, but this configuration ensures all files receive a default label.</span></span>
    
- <span data-ttu-id="081db-132">사용자가 조직 외부로 이러한 종류의 파일을 보내려고 할 때 경고하거나 방지하기 위해 중요 및 극비 Office 365 레이블에 대한 DLP(데이터 손실 방지) 정책이 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="081db-132">Data loss prevention (DLP) policies are configured for the Sensitive and Highly Confidential Office 365 labels to either warn or prevent users when they attempt to send these types of files outside the organization.</span></span>
    
- <span data-ttu-id="081db-p105">시나리오에 필요한 경우 Azure Information Protection을 사용하여 극비 파일을 암호화하고 사용 권한을 부여할 수 있습니다. 이는 모든 고객에게 권장되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="081db-p105">If needed for your scenario, you can use Azure Information Protection to encrypt and grants permissions to files that are highly confidential. This is not recommended for all customers.</span></span>
    
## <a name="tenant-wide-settings-for-sharepoint-online-and-onedrive-for-business"></a><span data-ttu-id="081db-135">SharePoint Online 및 비즈니스용 OneDrive에 대한 테넌트 수준 설정</span><span class="sxs-lookup"><span data-stu-id="081db-135">Tenant-wide settings for SharePoint Online and OneDrive for Business</span></span>

<span data-ttu-id="081db-p106">SharePoint Online 및 비즈니스용 OneDrive에는 모든 사이트 및 사용자에게 영향을 주는 테넌트 수준 설정이 포함됩니다. 또한 이러한 설정 중 일부는 사이트 수준에서 더 제한적으로 조정할 수 있지만 해당 제한을 완화할 수는 없습니다. 이 섹션에서는 보안 및 공동 작업에 영향을 주는 테넌트 수준 설정에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="081db-p106">SharePoint Online and OneDrive for Business include tenant-wide settings that affect all sites and users. Some of these settings can also be adjusted at the site level to be more restrictive (but not less). This section discusses tenant-wide settings that affect security and collaboration.</span></span> 
  
### <a name="sharing"></a><span data-ttu-id="081db-139">공유</span><span class="sxs-lookup"><span data-stu-id="081db-139">Sharing</span></span>

<span data-ttu-id="081db-140">이 솔루션의 경우 다음과 같은 테넌트 수준 설정을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="081db-140">For this solution, we recommend the following tenant-wide settings:</span></span>
  
- <span data-ttu-id="081db-141">익명 공유를 포함하여 모든 계정 유형과 공유할 수 있도록 허용하는 기본 공유 정책을 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="081db-141">Keep the default sharing policy that allows all sharing with all account types, including anonymous sharing.</span></span>
    
- <span data-ttu-id="081db-142">필요한 경우 익명 연결이 만료되도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="081db-142">Set anonymous links to expire, if desired.</span></span>
    
- <span data-ttu-id="081db-p107">공유할 기본 연결 종류를 내부로 변경합니다. 이렇게 하면 실수로 데이터를 조직 외부로 누출하지 않도록 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="081db-p107">Change the default link type for sharing to Internal. This helps prevent accidental data leakage outside your organization.</span></span>
    
<span data-ttu-id="081db-p108">외부 공유를 허용하는 것이 반직관적일 수 있지만, 이 방법은 전자 메일로 파일을 보내는 것에 비해 파일 공유를 다 자세히 제어합니다. SharePoint Online과 Outlook은 함께 작동하여 파일에 대해 안전한 공동 작업을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="081db-p108">While it might seem counterintuitive to allow external sharing, this approach provides more control over file sharing compared to sending files in email. SharePoint Online and Outlook work together to provide secure collaboration on files.</span></span> 
  
- <span data-ttu-id="081db-147">기본적으로 Outlook은 전자 메일로 파일을 보내는 대신 파일에 대한 링크를 공유합니다.</span><span class="sxs-lookup"><span data-stu-id="081db-147">By default, Outlook shares a link to a file instead of sending the file in email.</span></span> 
    
- <span data-ttu-id="081db-148">SharePoint Online과 비즈니스용 OneDrive를 사용하면 조직 내부와 외부 모두의 참가자와 파일에 대한 링크를 쉽게 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="081db-148">SharePoint Online and OneDrive for Business make it easy to share links to files with contributors who are both inside and outside your organization</span></span>
    
<span data-ttu-id="081db-p109">또한 외부 공유를 관리하는 데 도움이 되는 제어가 있습니다. 예를 들어, 다음을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="081db-p109">You also have controls to help govern external sharing. For example, you can:</span></span>
  
- <span data-ttu-id="081db-151">익명 게스트 링크를 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="081db-151">Disable an anonymous guest link.</span></span>
    
- <span data-ttu-id="081db-152">사이트에 대한 사용자 액세스를 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="081db-152">Revoke user access to a site.</span></span>
    
- <span data-ttu-id="081db-153">특정 사이트 또는 문서에 대한 액세스 권한이 있는 사용자인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="081db-153">See who has access to a specific site or document.</span></span>
    
- <span data-ttu-id="081db-154">익명 공유 링크 만료를 설정합니다(테넌트 설정).</span><span class="sxs-lookup"><span data-stu-id="081db-154">Set anonymous sharing links to expire (tenant setting).</span></span>
    
- <span data-ttu-id="081db-155">조직 외부에서 공유할 수 있는 사용자를 제한합니다(테넌트 설정).</span><span class="sxs-lookup"><span data-stu-id="081db-155">Limit who can share outside your organization (tenant setting).</span></span>
    
### <a name="use-external-sharing-together-with-data-loss-prevention-dlp"></a><span data-ttu-id="081db-156">DLP(데이터 손실 방지)와 함께 외부 공유 사용</span><span class="sxs-lookup"><span data-stu-id="081db-156">Use external sharing together with data loss prevention (DLP)</span></span>

<span data-ttu-id="081db-p110">외부 공유를 허용하지 않으면 비즈니스 요구 사항을 가지고 있는 사용자는 대체 도구 및 방법을 찾습니다. 중요한 기밀 파일을 보호하려면 외부 공유를 DLP 정책과 결합하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="081db-p110">If you don't allow external sharing, users with a business need will find alternate tools and methods. Microsoft recommends you combine external sharing with DLP policies to protect sensitive and highly confidential files.</span></span>
  
### <a name="device-access-settings"></a><span data-ttu-id="081db-159">장치 액세스 설정</span><span class="sxs-lookup"><span data-stu-id="081db-159">Device access settings</span></span>

<span data-ttu-id="081db-p111">SharePoint Online 및 비즈니스용 OneDrive에 대한 장치 액세스 설정을 통해 액세스가 브라우저에만 제한되는지(파일을 다운로드할 수 없는지) 또는 액세스가 차단되는지 여부를 결정할 수 있습니다. 이러한 설정은 현재 첫 번째 릴리스에 있으며 테넌트 전체에 적용됩니다. 사이트 수준의 장치 액세스 정책을 구성할 수 있는 기능은 곧 제공될 예정입니다. 이 솔루션의 경우 테넌트 전체에 적용되는 장치 액세스 설정을 사용하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="081db-p111">Device access settings for SharePoint Online and OneDrive for Business let you determine whether access is limited to browser only (files can't be downloaded) or if access is blocked. These settings are currently in First Release and apply tenant-wide. Coming soon is the ability to configure device access policies at the site level. For this solution, we recommend not using device access settings that apply tenant-wide.</span></span>
  
<span data-ttu-id="081db-164">첫 번째 릴리스에 있는 장치 액세스 설정을 사용하려면 [Office 365에서 표준 또는 첫 번째 릴리스 옵션을 설정](https://support.office.com/article/Set-up-the-Standard-or-First-Release-options-in-Office-365-3B3ADFA4-1777-4FF0-B606-FB8732101F47)합니다.</span><span class="sxs-lookup"><span data-stu-id="081db-164">To use device access settings while these are in first release: [Set up the Standard or First Release Options in Office 365](https://support.office.com/article/Set-up-the-Standard-or-First-Release-options-in-Office-365-3B3ADFA4-1777-4FF0-B606-FB8732101F47).</span></span>
  
### <a name="onedrive-for-business"></a><span data-ttu-id="081db-165">비즈니스용 OneDrive</span><span class="sxs-lookup"><span data-stu-id="081db-165">OneDrive for Business</span></span>

<span data-ttu-id="081db-p112">이러한 설정을 방문하여 비즈니스용 OneDrive 사이트에 대한 기본 설정을 변경할지 여부를 결정합니다. 현재 공유 및 장치 액세스 설정은 SharePoint Online 관리 센터에서 복제되어 두 환경 모두에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="081db-p112">Visit these settings to decide if you want to change the default settings for OneDrive for Business sites. Currently, the sharing and device access settings are duplicated from the SharePoint Online admin center and apply to both environments.</span></span>
  
## <a name="sharepoint-team-site-configuration"></a><span data-ttu-id="081db-168">SharePoint 팀 사이트 구성</span><span class="sxs-lookup"><span data-stu-id="081db-168">SharePoint team site configuration</span></span>

<span data-ttu-id="081db-p113">다음 표에서는 이 문서의 앞부분에서 설명한 팀 사이트 각각에 대한 구성을 요약하고 있습니다. 이러한 구성을 시작하기 위한 권장 사항으로 사용하고, 조직의 요구 사항에 맞게 사이트 유형 및 구성을 조정합니다. 모든 조직에 모든 유형의 사이트가 필요한 것은 아니며, 소수의 조직에만 극비 보호가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="081db-p113">The following table summarizes the configuration for each of the team sites described earlier in this article. Use these configurations as starting point recommendations and adjust the site types and configurations to meet the needs of your organization. Not every organization needs every type of site. Only a small number of organizations require highly confidential protection.</span></span>
  
||||||
|:-----|:-----|:-----|:-----|:-----|
||<span data-ttu-id="081db-173">**초기 보호 #1**</span><span class="sxs-lookup"><span data-stu-id="081db-173">**Baseline protection #1**</span></span> <br/> |<span data-ttu-id="081db-174">**초기 보호 #2**</span><span class="sxs-lookup"><span data-stu-id="081db-174">**Baseline protection #2**</span></span> <br/> |<span data-ttu-id="081db-175">**중요 보호**</span><span class="sxs-lookup"><span data-stu-id="081db-175">**Sensitive protection**</span></span> <br/> |<span data-ttu-id="081db-176">**극비**</span><span class="sxs-lookup"><span data-stu-id="081db-176">**Highly confidential**</span></span> <br/> |
|<span data-ttu-id="081db-177">설명</span><span class="sxs-lookup"><span data-stu-id="081db-177">Description</span></span>  <br/> |<span data-ttu-id="081db-178">조직 내에서 검색 및 공동 작업을 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="081db-178">Open discovery and collaboration within the organization.</span></span>  <br/> |<span data-ttu-id="081db-179">그룹 외부와의 공유가 허용되는 개인 사이트 및 그룹입니다.</span><span class="sxs-lookup"><span data-stu-id="081db-179">Private site and group with sharing allowed outside the group.</span></span>  <br/> |<span data-ttu-id="081db-p114">격리된 사이트이며, 액세스 수준이 특정 그룹의 구성원으로 정의됩니다. 사이트의 구성원에게만 공유가 허용됩니다. DLP에서 조직 외부로 파일을 보내려고 할 때 사용자에게 경고합니다.</span><span class="sxs-lookup"><span data-stu-id="081db-p114">Isolated site, in which levels of access are defined by membership in specific groups. Sharing is only allowed to members of the site. DLP warns users when attempting to send files outside the organization.</span></span>  <br/> |<span data-ttu-id="081db-p115">Azure Information Protection을 사용한 파일 암호화 및 권한 부여로 격리된 사이트입니다. DLP에서 사용자가 조직 외부로 파일을 보내지 못하도록 방지합니다.</span><span class="sxs-lookup"><span data-stu-id="081db-p115">Isolated site + file encryption and permissions with Azure Information Protection. DLP prevents users from sending files outside the organization.</span></span>  <br/> |
|<span data-ttu-id="081db-185">개인 또는 공용 팀 사이트</span><span class="sxs-lookup"><span data-stu-id="081db-185">Private or public team site</span></span>  <br/> |<span data-ttu-id="081db-186">Public</span><span class="sxs-lookup"><span data-stu-id="081db-186">Public</span></span>  <br/> |<span data-ttu-id="081db-187">개인</span><span class="sxs-lookup"><span data-stu-id="081db-187">Private</span></span>  <br/> |<span data-ttu-id="081db-188">개인</span><span class="sxs-lookup"><span data-stu-id="081db-188">Private</span></span>  <br/> |<span data-ttu-id="081db-189">개인</span><span class="sxs-lookup"><span data-stu-id="081db-189">Private</span></span>  <br/> |
|<span data-ttu-id="081db-190">액세스 가능한 사용자</span><span class="sxs-lookup"><span data-stu-id="081db-190">Who has access?</span></span>  <br/> |<span data-ttu-id="081db-191">B2B 사용자 및 게스트 사용자를 포함한 조직의 모든 사용자</span><span class="sxs-lookup"><span data-stu-id="081db-191">Everybody in the organization, including B2B users and guest users.</span></span>  <br/> |<span data-ttu-id="081db-p116">사이트 구성원만 - 다른 사용자는 액세스를 요청할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="081db-p116">Members of the site only. Others can request access.</span></span>  <br/> |<span data-ttu-id="081db-p117">사이트 구성원만 - 다른 사용자는 액세스를 요청할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="081db-p117">Members of the site only. Others can request access.</span></span>  <br/> |<span data-ttu-id="081db-p118">구성원만 - 다른 사용자는 액세스를 요청할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="081db-p118">Members only. Others cannot request access.</span></span>  <br/> |
|<span data-ttu-id="081db-198">사이트 수준 공유 제어</span><span class="sxs-lookup"><span data-stu-id="081db-198">Site-level sharing controls</span></span>  <br/> |<span data-ttu-id="081db-p119">모든 사용자에게 공유가 허용됩니다. 기본 설정입니다.</span><span class="sxs-lookup"><span data-stu-id="081db-p119">Sharing allowed with anybody. Default settings.</span></span>  <br/> |<span data-ttu-id="081db-p120">모든 사용자에게 공유가 허용됩니다. 기본 설정입니다.</span><span class="sxs-lookup"><span data-stu-id="081db-p120">Sharing allowed with anybody. Default settings.</span></span>  <br/> |<span data-ttu-id="081db-203">구성원은 사이트에 대한 액세스를 공유할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="081db-203">Members cannot share access to the site.</span></span>  <br/> <span data-ttu-id="081db-204">구성원이 아닌 사용자는 사이트에 대한 액세스를 요청할 수 있지만, 사이트 관리자가 이러한 요청을 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="081db-204">Non-members can request access to the site, but these requests need to be addressed by a site administrator.</span></span>  <br/> |<span data-ttu-id="081db-205">구성원은 사이트에 대한 액세스를 공유할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="081db-205">Members cannot share access to the site.</span></span>  <br/> <span data-ttu-id="081db-206">구성원이 아닌 사용자는 사이트 또는 콘텐츠에 대한 액세스를 요청할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="081db-206">Non-members cannot request access to the site or contents.</span></span>  <br/> |
|<span data-ttu-id="081db-207">사이트 수준 장치 액세스 제어</span><span class="sxs-lookup"><span data-stu-id="081db-207">Site-level device access controls</span></span>  <br/> |<span data-ttu-id="081db-208">추가 제어가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="081db-208">No additional controls.</span></span>  <br/> |<span data-ttu-id="081db-209">추가 제어가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="081db-209">No additional controls.</span></span>  <br/> |<span data-ttu-id="081db-p121">사이트 수준 제어가 곧 제공될 예정이며, 사용자는 비호환 또는 비도메인 가입 장치로 파일을 다운로드할 수 없습니다. 이렇게 하면 다른 모든 장치에서 브라우저 전용으로 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="081db-p121">Site-level controls are coming soon, which prevents users from downloading files to non-compliant or non-domain joined devices. This allows browser-only access from all other devices.</span></span>  <br/> |<span data-ttu-id="081db-212">파일을 비호환 또는 비도메인 가입 장치로 다운로드할 수 없도록 차단하는 사이트 수준 제어가 곧 제공될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="081db-212">Site-level controls are coming soon, which blocks downloading of files to non-compliant or non-domain joined devices.</span></span>  <br/> |
|<span data-ttu-id="081db-213">Office 365 레이블</span><span class="sxs-lookup"><span data-stu-id="081db-213">Office 365 labels</span></span>  <br/> |<span data-ttu-id="081db-214">내부 공용</span><span class="sxs-lookup"><span data-stu-id="081db-214">Internal Public</span></span>  <br/> |<span data-ttu-id="081db-215">개인</span><span class="sxs-lookup"><span data-stu-id="081db-215">Private</span></span>  <br/> |<span data-ttu-id="081db-216">중요</span><span class="sxs-lookup"><span data-stu-id="081db-216">Sensitive</span></span>  <br/> |<span data-ttu-id="081db-217">극비</span><span class="sxs-lookup"><span data-stu-id="081db-217">Highly Confidential</span></span>  <br/> |
|<span data-ttu-id="081db-218">DLP 정책</span><span class="sxs-lookup"><span data-stu-id="081db-218">DLP policies</span></span>  <br/> |||<span data-ttu-id="081db-219">레이블이 중요 계층으로 지정된 파일을 조직 외부로 보낼 때 사용자에게 경고합니다.</span><span class="sxs-lookup"><span data-stu-id="081db-219">Warn users when sending files that are labeled as Sensitive outside the organization.</span></span>  <br/> <span data-ttu-id="081db-220">신용 카드 번호 또는 기타 개인 데이터와 같은 중요 데이터 형식의 외부 공유를 차단하기 위해 이러한 데이터 형식(구성한 사용자 지정 데이터 형식 포함)에 대한 추가 DLP 정책을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="081db-220">To block external sharing of sensitive data types, such as credit card numbers or other personal data, you can configure additional DLP policies for these data types (including custom data types you configure).</span></span>  <br/> |<span data-ttu-id="081db-p122">사용자가 극비 계층으로 레이블이 지정된 파일을 외부 조직으로 보내지 못하도록 차단합니다. 사용자(파일을 공유하는 사용자 포함)는 근거를 제공하여 이 설정을 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="081db-p122">Block users from sending files that are labeled as highly confidential outside organization. Allow users to override this by providing justification, including who they are sharing the file with.</span></span>  <br/> |
|<span data-ttu-id="081db-223">Azure Information Protection</span><span class="sxs-lookup"><span data-stu-id="081db-223">Azure Information Protection</span></span>  <br/> ||||<span data-ttu-id="081db-p123">Azure Information Protection을 사용하여 파일에 대한 권한을 자동으로 암호화하고 부여합니다. 파일이 누출되는 경우 이러한 보호는 해당 파일과 함께 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="081db-p123">Use Azure Information Protection to automatically encrypt and grant permissions to files. This protection travels with the files in case they are leaked.</span></span>  <br/> <span data-ttu-id="081db-p124">Office 365는 Azure Information Protection으로 암호화된 파일을 읽을 수 없습니다. 또한 DLP 정책은 메타데이터(레이블 포함)에만 작동할 수 있지만 파일의 내용(예: 파일 내의 신용 카드 번호)에는 작동할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="081db-p124">Office 365 cannot read files encrypted with Azure Information Protection. Additionally, DLP policies can only work with the metadata (including labels) but not the contents of these files (such as credit card numbers within files).</span></span>  <br/> |
   
<span data-ttu-id="081db-p125">이 솔루션에 나오는 4가지 다른 SharePoint Online 팀 사이트 유형을 배포하는 단계를 보려면 [3계층의 보호를 위해 SharePoint Online 사이트 배포](deploy-sharepoint-online-sites-for-three-tiers-of-protection.md)를 참조하세요. 개발/테스트 환경을 만드는 단계를 보려면 [개발/테스트 환경의 보안 SharePoint Online 사이트](secure-sharepoint-online-sites-in-a-dev-test-environment.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="081db-p125">For the steps to deploy the four different types of SharePoint Online team sites in this solution, see [Deploy SharePoint Online sites for three tiers of protection](deploy-sharepoint-online-sites-for-three-tiers-of-protection.md). For the steps to create a dev/test environment, see [Secure SharePoint Online sites in a dev/test environment](secure-sharepoint-online-sites-in-a-dev-test-environment.md).</span></span> 
  
## <a name="office-365-classification-and-labels"></a><span data-ttu-id="081db-230">Office 365 분류 및 레이블</span><span class="sxs-lookup"><span data-stu-id="081db-230">Office 365 classification and labels</span></span>

<span data-ttu-id="081db-p126">중요 데이터가 있는 환경에서는 Office 365 레이블을 사용하는 것이 좋습니다. Office 365 레이블을 구성하고 게시한 후에는 다음을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="081db-p126">Using Office 365 labels is recommended for environments with sensitive data. After you configure and publish Office 365 labels:</span></span>
  
- <span data-ttu-id="081db-233">SharePoint Online 팀 사이트의 문서 라이브러리에 기본 레이블을 적용하여 해당 라이브러리의 모든 문서에서 기본 레이블을 사용하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="081db-233">You can apply a default label to a document library in a SharePoint Online team site, so that all documents in that library get the default label.</span></span> 
    
- <span data-ttu-id="081db-234">특정 조건과 일치하는 경우 콘텐츠에 레이블을 자동으로 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="081db-234">You can apply labels to content automatically if it matches specific conditions.</span></span>
    
- <span data-ttu-id="081db-235">Office 365 레이블을 기준으로 하는 DLP 정책을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="081db-235">You can apply DLP policies that are based on Office 365 labels.</span></span>
    
- <span data-ttu-id="081db-p127">조직의 사용자가 웹용 Outlook, Outlook 2010 이상, 비즈니스용 OneDrive, SharePoint Online 및 Office 365 그룹에서 콘텐츠에 레이블을 수동으로 적용할 수 있습니다. 사용자는 종종 자신이 사용하고 있는 콘텐츠의 형식을 가장 잘 알고 있기 때문에 콘텐츠를 분류하여 적절한 DLP 정책을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="081db-p127">People in your organization can apply a label manually to content in Outlook on the web, Outlook 2010 and later, OneDrive for Business, SharePoint Online, and Office 365 groups. Users often know best what type of content they're working with, so they can classify it and have the appropriate DLP policy applied.</span></span>
    
![SharePoint 사이트에 대한 권장 구성](media/7fed0126-ab4a-4480-922c-681970642339.png)
  
<span data-ttu-id="081db-239">그림에서 보여 주듯이 이 솔루션에는 다음과 같은 레이블 만들기가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="081db-239">As illustrated, this solution includes creating the following labels:</span></span>
  
- <span data-ttu-id="081db-240">극비</span><span class="sxs-lookup"><span data-stu-id="081db-240">Highly Confidential</span></span>
    
- <span data-ttu-id="081db-241">중요</span><span class="sxs-lookup"><span data-stu-id="081db-241">Sensitive</span></span>
    
- <span data-ttu-id="081db-242">개인</span><span class="sxs-lookup"><span data-stu-id="081db-242">Private</span></span>
    
- <span data-ttu-id="081db-243">내부 공용</span><span class="sxs-lookup"><span data-stu-id="081db-243">Internal Public</span></span>
    
<span data-ttu-id="081db-p128">이러한 레이블은 이 문서의 앞부분에 있는 그림과 차트에서 권장된 사이트와 매핑됩니다. 이 솔루션에서 DLP 정책을 구성하여 중요 및 극비 레이블이 지정된 파일을 유출하지 못하도록 방지하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="081db-p128">These labels are mapped to the recommended sites in the illustrations and charts earlier in this article. This solution recommends configuring DLP policies to help prevent the leakage of files labeled as Sensitive and Highly Confidential.</span></span>
  
<span data-ttu-id="081db-246">이 솔루션에서 Office 365 레이블 및 DLP 정책을 구성하는 단계는 [Office 365 레이블 및 DLP(데이터 손실 방지)를 사용하여 SharePoint Online 파일 보호](protect-sharepoint-online-files-with-office-365-labels-and-dlp.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="081db-246">For the steps to configure Office 365 labels and DLP policies in this solution, see [Protect SharePoint Online files with Office 365 labels and DLP](protect-sharepoint-online-files-with-office-365-labels-and-dlp.md).</span></span>
  
## <a name="azure-information-protection"></a><span data-ttu-id="081db-247">Azure Information Protection</span><span class="sxs-lookup"><span data-stu-id="081db-247">Azure Information Protection</span></span>

<span data-ttu-id="081db-p129">보안 시나리오가 필요하다면 Azure Information Protection을 사용하여 어디서나 파일과 동반하는 레이블과 보호를 적용할 수 있습니다. Azure Information Protection 레이블은 Office 365 레이블과 다릅니다. 이 솔루션의 경우 Azure Information Protection 범위 지정 정책 및 극비 레이블의 하위 레이블을 사용하여 최고 수준의 보안으로 보호해야 하는 파일에 대한 권한을 암호화하고 부여하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="081db-p129">If warranted for your security scenario, you can use Azure Information Protection to apply labels and protections that follow the files wherever they go. Azure Information Protection labels are different than Office 365 labels. For this solution, we recommend you use a scoped Azure Information Protection policy and a sub-label of the Highly Confidential label to encrypt and grant permissions to files that need to be protected with the highest level of security.</span></span> 
  
<span data-ttu-id="081db-p130">Office 365에 저장된 파일에 Azure Information Protection 암호화가 적용되어 있으면 이 파일의 내용을 처리할 수 없습니다. 즉 공동 작성, eDiscovery, 검색, Delve 및 기타 공동 작업 기능이 작동하지 않습니다. DLP 정책은 메타데이터(Office 365 레이블 포함)에만 작동할 수 있지만 파일의 내용(예: 파일 내의 신용 카드 번호)에는 작동할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="081db-p130">Be aware that when Azure Information Protection encryption is applied to files stored in Office 365, the service cannot process the contents of these files. Co-authoring, eDiscovery, search, Delve, and other collaborative features do not work. DLP policies can only work with the metadata (including Office 365 labels) but not the contents of these files (such as credit card numbers within files).</span></span>
  
![Azure에서 Azure Information Protection을 구성하고 클라이언트 도구 모음에 레이블을 표시합니다.](media/1266a7a0-5078-49ab-bbf1-b0cf41451f62.png)
  
<span data-ttu-id="081db-255">그림에서 보여 주듯이 다음과 같이 설명됩니다.</span><span class="sxs-lookup"><span data-stu-id="081db-255">As illustrated:</span></span>
  
- <span data-ttu-id="081db-p131">Microsoft Azure Portal에서 Azure Information Protection 정책 및 레이블을 구성합니다. 범위 지정 Azure Information Protection 정책의 하위 레이블을 구성하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="081db-p131">You configure Azure Information Protection policies and labels in the Microsoft Azure portal. Configuring a sub-label of a scoped Azure Information Protection policy is recommended.</span></span>
    
- <span data-ttu-id="081db-258">Azure Information Protection 레이블은 Office 응용 프로그램에서 **Information Protection** 표시줄로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="081db-258">Azure Information Protection labels show up as an **Information protection** bar in Office applications.</span></span>
    
### <a name="adding-permissions-for-external-users"></a><span data-ttu-id="081db-259">외부 사용자에 대한 권한 추가</span><span class="sxs-lookup"><span data-stu-id="081db-259">Adding permissions for external users</span></span>

<span data-ttu-id="081db-p132">Azure Information Protection으로 보호된 파일에 대한 액세스 권한을 외부 사용자에게 부여할 수 있는 두 가지 방법이 있습니다. 이 두 가지 방법에서는 모두 Azure AD 계정이 외부 사용자에게 있어야 합니다. 외부 사용자가 Azure AD를 사용하는 조직의 구성원이 아닌 경우 [https://aka.ms/aip-signup](https://aka.ms/aip-signup) 등록 페이지를 사용하여 Azure AD 계정을 개별로 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="081db-p132">There are two ways you can grant external users access to files protected with Azure Information Protection. In both these cases, external users must have an Azure AD account. If external users aren't members of an organization that uses Azure AD, they can obtain an Azure AD account as an individual by using this sign-up page: [https://aka.ms/aip-signup](https://aka.ms/aip-signup).</span></span>
  
- <span data-ttu-id="081db-263">레이블 보호를 구성하는 데 사용되는 외부 사용자를 Azure AD 그룹에 추가</span><span class="sxs-lookup"><span data-stu-id="081db-263">Add external users to an Azure AD group that is used to configure protection for a label</span></span>
    
     <span data-ttu-id="081db-p133">먼저 계정을 디렉터리에 B2B 사용자로 추가해야 합니다. [Azure Rights Management에서 그룹 구성원 자격을 캐시](https://docs.microsoft.com/information-protection/plan-design/prepare#group-membership-caching-by-azure-rights-management)하는 데 몇 시간이 걸릴 수 있습니다. 이 방법을 사용하면 레이블로 보호된 기존의 모든 파일(사용자가 Azure AD 그룹에 추가되기 전에 보호된 파일도 포함)에 대한 권한이 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="081db-p133">You'll need to first add the account as a B2B user in your directory. It can take a couple of hours for [group membership caching by Azure Rights Management](https://docs.microsoft.com/information-protection/plan-design/prepare#group-membership-caching-by-azure-rights-management). With this method, permissions are granted to all existing files protected with the label (even files protected before a user is added to the Azure AD group).</span></span>
    
- <span data-ttu-id="081db-267">외부 사용자를 레이블 보호에 직접 추가</span><span class="sxs-lookup"><span data-stu-id="081db-267">Add external users directly to the label protection</span></span>
    
     <span data-ttu-id="081db-p134">조직(예: Fabrikam.com), Azure AD 그룹(조직 내의 재무 그룹) 또는 개별 사용자의 모든 사용자를 추가할 수 있습니다. 예를 들어 조절기의 외부 팀을 레이블 보호에 추가할 수 있습니다. 이 방법을 사용하면 외부 엔터티가 보호에 추가된 후 레이블로 보호된 파일에 대한 권한만 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="081db-p134">You can add all users from an organization (e.g. Fabrikam.com), an Azure AD group (such as a finance group within an organization), or an individual user. For example, you can add an external team of regulators to the protection for a label. With this method, permissions are granted only to files protected with the label after the external entity is added to the protection.</span></span>
    
### <a name="deploying-and-using-azure-information-protection"></a><span data-ttu-id="081db-271">Azure Information Protection 배포 및 사용</span><span class="sxs-lookup"><span data-stu-id="081db-271">Deploying and using Azure Information Protection</span></span>

<span data-ttu-id="081db-272">이 솔루션에서 Azure Information Protection을 구성하는 단계는 [Azure Information Protection을 사용하여 SharePoint Online 파일 보호](protect-sharepoint-online-files-with-azure-information-protection.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="081db-272">For the steps to configure Azure Information Protection in this solution, see [Protect SharePoint Online files with Azure Information Protection](protect-sharepoint-online-files-with-azure-information-protection.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="081db-273">참고 항목</span><span class="sxs-lookup"><span data-stu-id="081db-273">See Also</span></span>

[<span data-ttu-id="081db-274">정치적 캠페인, 비영리 조직 및 기타 기밀 조직에 대한 Microsoft 보안 지침</span><span class="sxs-lookup"><span data-stu-id="081db-274">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="081db-275">보안 솔루션</span><span class="sxs-lookup"><span data-stu-id="081db-275">Security solutions</span></span>](security-solutions.md)
  
[<span data-ttu-id="081db-276">클라우드 도입 및 하이브리드 솔루션</span><span class="sxs-lookup"><span data-stu-id="081db-276">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
[<span data-ttu-id="081db-277">개발/테스트 환경의 보안 SharePoint Online 사이트</span><span class="sxs-lookup"><span data-stu-id="081db-277">Secure SharePoint Online sites in a dev/test environment</span></span>](secure-sharepoint-online-sites-in-a-dev-test-environment.md)



