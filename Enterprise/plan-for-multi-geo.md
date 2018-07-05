---
title: 비즈니스용 OneDrive Multi-Geo 계획
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: 비즈니스용 OneDrive Multi-Geo, 다중 위치 작동 방식 및 데이터 저장소에 사용할 수 있는 지리적 위치에 대해 알아봅니다.
ms.openlocfilehash: 54efc6092338e505ef44344f9c3d3a7efe9ae498
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/27/2018
ms.locfileid: "18908362"
---
# <a name="plan-for-onedrive-for-business-multi-geo"></a><span data-ttu-id="dad82-103">비즈니스용 OneDrive Multi-Geo 계획</span><span class="sxs-lookup"><span data-stu-id="dad82-103">Plan for OneDrive for Business</span></span>

<span data-ttu-id="dad82-104">이 설명서는 데이터 상주 요구 사항을 충족해야 하는 회사 현재 상황에 따라 추가적인 지역으로 SharePoint Online 테넌트를 확장하려고 준비하는 MNC(다국적 회사)의 관리자를 대상으로 작성되었습니다.</span><span class="sxs-lookup"><span data-stu-id="dad82-104">This guidance is designed for administrators of multi-national companies (MNCs) who are preparing their SharePoint Online tenant to be expanded to additional geographies in accordance with the company’s presence to meet data residency requirements.</span></span>

<span data-ttu-id="dad82-p101">OneDrive Multi-Geo 구성에서 Office 365 테넌트는 하나의 중앙 위치(기본 위치라고도 함)와 하나 이상의 위성 지리적 위치로 구성됩니다. 이 테넌트는 여러 지리적 위치에 걸쳐 있는 단일 테넌트입니다. OneDrive Multi-Geo에서 지리적 위치를 포함하는 테넌트 정보는 AAD(Azure Active Directory)에서 마스터됩니다.</span><span class="sxs-lookup"><span data-stu-id="dad82-p101">In a OneDrive Multi-Geo configuration, your Office 365 tenant consists of a central location (also known as the default location) and one or more satellite geo locations. This is a single tenant that spans across multiple geo locations. In OneDrive Multi-Geo, your tenant information, including geo locations, is mastered in Azure Active Directory (AAD).</span></span> 

<span data-ttu-id="dad82-108">다음은 구성의 기본 개념을 이해하는 데 도움이 되는 몇 가지 핵심적인 다중 위치 용어입니다.</span><span class="sxs-lookup"><span data-stu-id="dad82-108">Here are some key multi-geo terms to help you understand the basic concepts of the configuration:</span></span>

-   <span data-ttu-id="dad82-109">**테넌트** – Office 365 클라우드에서 일반적으로 하나 이상의 도메인에 연결되어 있는 조직을 나타내는 표현입니다(예: http://contoso.sharepoint.com)).</span><span class="sxs-lookup"><span data-stu-id="dad82-109">**Tenant** – An organization’s representation in the Office 365 cloud which typically has one or more domains associated with it (for example, http://contoso.sharepoint.com).</span></span> 

-   <span data-ttu-id="dad82-p102">**지리적 위치** – 테넌트의 데이터가 호스트되는 지리적 위치입니다. 다중 위치 테넌트는 둘 이상의 지리적 위치(예: 북미 및 유럽)에 걸쳐 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dad82-p102">**Geo locations** – The geographic locations where your tenant’s data is hosted. Multi-geo tenants span more than one geo location, for example, North America and Europe.</span></span>

-   <span data-ttu-id="dad82-112">**ADL(허용된 데이터 위치)** – 테넌트가 OneDrive 및 SharePoint 데이터를 호스트하도록 구성된 지리적 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="dad82-112">**Allowed Data Locations (ADL)** – The geo locations for which your tenant has been configured to host OneDrive and SharePoint data.</span></span>

-   <span data-ttu-id="dad82-p103">**PDL(기본 설정 데이터 위치)** - 개별 사용자의 OneDrive 데이터가 저장되는 지리적 위치입니다. 관리자는 이 위치를 테넌트에 대해 구성된 허용된 데이터 위치로 설정할 수 있습니다. OneDrive 사이트가 이미 있는 사용자의 PDL을 변경하는 경우 해당 OneDrive 데이터가 자동으로 새 지리적 위치로 이동되지 않습니다. 자세한 내용은 [OneDrive 라이브러리를 다른 지리적 위치로 이동](move-onedrive-between-geo-locations.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dad82-p103">**Preferred Data Location (PDL)** – The geo location where an individual user’s OneDrive data is stored. This can be set by the administrator to any of the Allowed Data Locations that have been configured for the tenant. Note that if you change the PDL for a user who already has a OneDrive site, their OneDrive data is not moved to the new geo location automatically. See [Move a OneDrive library to a different geo-location](move-onedrive-between-geo-locations.md) for more information.</span></span>

<span data-ttu-id="dad82-117">Multi-Geo를 사용하려면 다음 4가지 주요 단계가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="dad82-117">Enabling Multi-Geo requires four key steps:</span></span>

1.  <span data-ttu-id="dad82-118">계정 팀과 협의하여 추가 하려면 계정 팀에서 작업 하는 _Office 365의 Multi-Geo 기능_ 서비스 계획을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="dad82-118">Work with your account team to add the _Multi-Geo Capabilities in Office 365_ service plan.</span></span>

2.  <span data-ttu-id="dad82-119">원하는 위성 지리적 위치를 선택하고 테넌트에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="dad82-119">Choose your desired satellite geo location(s) and add them to your tenant.</span></span>

3.  <span data-ttu-id="dad82-p104">사용자의 기본 설정 데이터 위치를 원하는 위성 지리적 위치로 설정합니다. 사용자에 대해 새 OneDrive 사이트가 프로비전될 경우 해당 PDL로 프로비전됩니다.</span><span class="sxs-lookup"><span data-stu-id="dad82-p104">Set your users’ preferred data location to the desired satellite geo location. When a new OneDrive site is provisioned for a user, it is provisioned to their PDL.</span></span>

4.  <span data-ttu-id="dad82-122">필요에 따라 홈 위치에 있는 사용자의 기존 OneDrive 사이트를 기본 설정 데이터 위치로 마이그레이션합니다.</span><span class="sxs-lookup"><span data-stu-id="dad82-122">Migrate your users’ existing OneDrive sites from the home location to their preferred data location as needed.</span></span>

<span data-ttu-id="dad82-123">이러한 각 단계에 대한 자세한 내용은 [비즈니스용 OneDrive Multi-Geo 구성](multi-geo-tenant-configuration.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dad82-123">See [Configure OneDrive for Business Multi-Geo](multi-geo-tenant-configuration.md) for details on each of these steps.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="dad82-p105">Office 365의 Multi-Geo 기능은 성능 최적화 사례에 맞게 디자인되지 않았으며, 데이터 상주 요구 사항을 충족하도록 디자인되었습니다. Office 365의 성능 최적화에 대한 내용은 [Office 365의 네트워크 계획 및 성능 조정](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848)을 참조하거나 지원 그룹에 문의하세요.</span><span class="sxs-lookup"><span data-stu-id="dad82-p105">Note that the Multi-Geo features of Office 365 are not designed for performance optimization cases, they are designed to meet data residency requirements. For information about performance optimization for Office 365, see [Network planning and performance tuning for Office 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) or contact your support group.</span></span>

<span data-ttu-id="dad82-p106">다음 위치를 OneDrive 파일을 호스트할 수 있는 위성 지리적 위치로 구성할 수 있습니다. 다중 위치를 계획할 때는 Office 365 테넌트에 추가하려는 위치 목록을 만듭니다. 한두 개의 위성 위치에서 시작한 후 필요에 따라 더 많은 지리적 위치로 점차적으로 확장하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="dad82-p106">You can configure any of the following locations to be satellite geo locations where you can host OneDrive files. As you plan for multi-geo, make a list of the locations that you want to add to your Office 365 tenant. We recommend starting with one or two satellite locations and then gradually expanding to more geo locations, if needed.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="dad82-129"><strong>위치</strong></span><span class="sxs-lookup"><span data-stu-id="dad82-129"><strong>Location</strong></span></span></th>
<th align="left"><span data-ttu-id="dad82-130"><strong>코드</strong></span><span class="sxs-lookup"><span data-stu-id="dad82-130"><strong>Code</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="dad82-131">아시아 태평양</span><span class="sxs-lookup"><span data-stu-id="dad82-131">Asia/Pacific</span></span></td>
<td align="left"><span data-ttu-id="dad82-132">APC</span><span class="sxs-lookup"><span data-stu-id="dad82-132">APC</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="dad82-133">유럽/중동/아프리카</span><span class="sxs-lookup"><span data-stu-id="dad82-133">Europe / Middle East / Africa</span></span></td>
<td align="left"><span data-ttu-id="dad82-134">EUR</span><span class="sxs-lookup"><span data-stu-id="dad82-134">EUR</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="dad82-135">북미</span><span class="sxs-lookup"><span data-stu-id="dad82-135">North America</span></span></td>
<td align="left"><span data-ttu-id="dad82-136">NAM</span><span class="sxs-lookup"><span data-stu-id="dad82-136">NAM</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="dad82-137">오스트레일리아</span><span class="sxs-lookup"><span data-stu-id="dad82-137">Australia</span></span></td>
<td align="left"><span data-ttu-id="dad82-138">AUS</span><span class="sxs-lookup"><span data-stu-id="dad82-138">AUS</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="dad82-139">캐나다</span><span class="sxs-lookup"><span data-stu-id="dad82-139">Canada</span></span></td>
<td align="left"><span data-ttu-id="dad82-140">CAN</span><span class="sxs-lookup"><span data-stu-id="dad82-140">CAN</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="dad82-141">일본</span><span class="sxs-lookup"><span data-stu-id="dad82-141">Japan</span></span></td>
<td align="left"><span data-ttu-id="dad82-142">JPN</span><span class="sxs-lookup"><span data-stu-id="dad82-142">JPN</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="dad82-143">한국</span><span class="sxs-lookup"><span data-stu-id="dad82-143">Korea</span></span></td>
<td align="left"><span data-ttu-id="dad82-144">KOR</span><span class="sxs-lookup"><span data-stu-id="dad82-144">KOR</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="dad82-145">영국</span><span class="sxs-lookup"><span data-stu-id="dad82-145">United Kingdom</span></span></td>
<td align="left"><span data-ttu-id="dad82-146">GBR</span><span class="sxs-lookup"><span data-stu-id="dad82-146">GBR</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="dad82-147">예정된 지리적 위치:</span><span class="sxs-lookup"><span data-stu-id="dad82-147">Upcoming geo locations:</span></span>
  
- <span data-ttu-id="dad82-148">프랑스</span><span class="sxs-lookup"><span data-stu-id="dad82-148">France</span></span>
- <span data-ttu-id="dad82-149">인도</span><span class="sxs-lookup"><span data-stu-id="dad82-149">India</span></span>

<span data-ttu-id="dad82-p107">다중 위치를 구성할 경우 Office 365로 마이그레이션하는 동안 온-프레미스 인프라를 통합할 기회를 고려하는 것이 좋습니다. 예를 들어, 싱가포르 및 말레이시아에 온-프레미스 팜이 있는 경우, 데이터 상주 요구에 맞을 경우 APC 위성 위치로 통합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dad82-p107">When you configure multi-geo, consider taking the opportunity to consolidate your on-premises infrastructure while migrating to Office 365. For example, if you have on-premises farms in Singapore and Malaysia, then you can consolidate them to the APC satellite location, provided data residency requirements allow you to do so.</span></span>

## <a name="best-practices"></a><span data-ttu-id="dad82-152">모범 사례</span><span class="sxs-lookup"><span data-stu-id="dad82-152">Best practices</span></span>

<span data-ttu-id="dad82-p108">Office 365에 초기 테스트를 수행하기 위한 테스트 사용자를 만드는 것이 좋습니다. 프로덕션 사용자를 OneDrive Multi-Geo 기능에 등록하기 전에 이 사용자로 일부 테스트 및 확인 단계를 진행하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dad82-p108">We recommend that you create a test user in Office 365 to do some initial testing. We’ll walk through some testing and verification steps with this user before you proceed to onboard production users into the OneDrive Multi-Geo feature.</span></span>

<span data-ttu-id="dad82-p109">테스트 사용자로 테스트를 완료한 후 IT 부서에서 새 지리적 위치에서 최초로 OneDrive를 사용할 파일럿 그룹을 선택합니다. 이 첫 번째 그룹으로 OneDrive가 아직 없는 사용자를 선택합니다. 이 초기 그룹에는 5명 이하의 사용자를 포함한 후 일괄 롤아웃 방식에 따라 서서히 확장하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="dad82-p109">Once you’ve completed testing with the test user, select a pilot group – perhaps from your IT department – to be the first to use OneDrive in a new geo-location. For this first group, select users who do not yet have a OneDrive. We recommend no more than five people in this initial group and gradually expand following a batched rollout approach.</span></span>

<span data-ttu-id="dad82-p110">Office 365에서 해당 OneDrive를 프로비전할 지리적 위치를 결정할 수 있도록 각 사용자에게는 PDL(*기본 설정 데이터 위치*)이 설정되어 있어야 합니다. 사용자의 기본 설정 데이터 위치는 선택한 위성 위치 중 하나 또는 사용자의 중앙 위치와 일치해야 합니다. PDL 필드는 필수는 아니지만 모든 사용자에 대해 PDL을 설정하는 것이 좋습니다. PDL이 없는 사용자의 워크로드는 Multi-Geo 논리에 따라 중앙 위치에 프로비전됩니다.</span><span class="sxs-lookup"><span data-stu-id="dad82-p110">Each user should have a *preferred data location* (PDL) set so that Office 365 can determine in which geo location to provision their OneDrive. The user’s preferred data location must match one of your chosen satellite locations or your central location. While the PDL field is not mandatory, we recommend that a PDL be set for all users. Workloads of a user without a PDL will be provisioned in the central location based on the Multi-Geo logic.</span></span>   

<span data-ttu-id="dad82-p111">사용자 목록을 만들고, 해당 UPN(사용자 주체 이름)과 해당 기본 설정 데이터 위치에 대한 위치 코드를 포함합니다. 시작할 테스트 사용자와 초기 파일럿 그룹을 포함합니다. 구성 절차를 위해 이 목록이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="dad82-p111">Create a list of your users, and include their user principal name (UPN) and the location code for the appropriate preferred data location. Include your test user and your initial pilot group to start with. You’ll need this list for the configuration procedures.</span></span>

<span data-ttu-id="dad82-p112">사용자가 온-프레미스 AD(Active Directory) 시스템에서 AAD(Azure Active Directory)로 동기화되면 Azure Active Directory Connect를 사용하여 동기화된 사용자에 대한 기본 설정 데이터 위치를 설정해야 합니다. Azure AD PowerShell을 사용하여 동기화된 사용자의 기본 설정 데이터 위치를 직접 구성할 수는 없습니다. AD에서 PDL를 설정하고 동기화하는 단계는 [Azure Active Directory Connect 동기화: Office 365 리소스에 대한 기본 설정 데이터 위치 구성](https://docs.microsoft.com/ko-KR/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation)에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dad82-p112">If your users are synchronized from an on-premises Active Directory (AD) system to Azure Active Directory (AAD), you must set the preferred data location for synchronized users by using Azure Active Directory Connect. You cannot directly configure the preferred data location for synchronized users using Azure AD PowerShell. The steps to set up PDL in AD and Synchronize it are covered in [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](https://docs.microsoft.com/ko-KR/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span>

<span data-ttu-id="dad82-p113">SharePoint 및 OneDrive 설정과 서비스가 다중 위치를 인식하므로 다중 위치 테넌트의 관리는 다중 위치가 아닌 테넌트의 관리와 다를 수 있습니다. 구성을 계속하기 전에 [다중 위치 환경 관리](administering-a-multi-geo-environment.md)를 검토하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="dad82-p113">The administration of a multi-geo tenant can differ from a non-multi-geo tenant, as many of the SharePoint and OneDrive settings and services are multi-geo aware. We recommend that you review [Administering a multi-geo environment](administering-a-multi-geo-environment.md) before you proceed with your configuration.</span></span>

<span data-ttu-id="dad82-170">다중 위치 환경의 최종 사용자 경험에 대한 자세한 내용은 [다중 위치 환경의 사용자 경험](multi-geo-user-experience.md)을 읽어보세요.</span><span class="sxs-lookup"><span data-stu-id="dad82-170">Read [User experience in a multgeo environment](multi-geo-user-experience.md) for details about your end users' experience in a multi-geo environment.</span></span>

<span data-ttu-id="dad82-171">비즈니스용 OneDrive Multi-Geo 구성을 시작하려면 [비즈니스용 OneDrive Multi-Geo 구성](multi-geo-tenant-configuration.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dad82-171">To get started configuring OneDrive for Business Multi-Geo, see [Configure OneDrive for Business Multi-Geo](multi-geo-tenant-configuration.md).</span></span>

<span data-ttu-id="dad82-172">구성을 완료한 경우 기본 설정 데이터 위치에서 작업할 때 필요하므로 [사용자의 OneDrive 라이브러리를 마이그레이션](move-onedrive-between-geo-locations.md)해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dad82-172">Once you’ve completed the configuration, remember to [migrate your users' OneDrive libraries](move-onedrive-between-geo-locations.md) as needed to get your users working from their preferred data locations.</span></span>
