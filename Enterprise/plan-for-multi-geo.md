---
title: 비즈니스 다중-지리적으로 분산 비즈니스용 OneDrive 계획
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: Strat_SP_gtc
localization_priority: Normal
description: 비즈니스 다중-지리적으로 분산, 다중-지리적으로 분산 작동 하는 방법 및 어떤 지리적 위치 데이터 저장소에서 사용할 수 있는 OneDrive을 소개 합니다.
ms.openlocfilehash: d7d6cfbbff4cf0ec2516f2506946c2832d96b3f2
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
---
# <a name="plan-for-onedrive-for-business-multi-geo"></a><span data-ttu-id="8b587-103">비즈니스 다중-지리적으로 분산 비즈니스용 OneDrive 계획</span><span class="sxs-lookup"><span data-stu-id="8b587-103">Plan for OneDrive for Business Multi-Geo</span></span>

<span data-ttu-id="8b587-104">이 설명서는 자신의 SharePoint Online 테 넌 트 데이터 residency 요구를 충족 하기 위해 회사의 현재 상태에 따라 추가 지역 하기 위해 확장할 수 있도록 준비 하는 다국적 기업 (MNCs)의 관리자를 위한 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8b587-104">This guidance is designed for administrators of multi-national companies (MNCs) who are preparing their SharePoint Online tenant to be expanded to additional geographies in accordance with the company’s presence to meet data residency requirements.</span></span>

<span data-ttu-id="8b587-p101">OneDrive 다중-지리적으로 분산 구성에서 Office 365 테 넌 트 (기본 위치 라고도 함) 하는 중앙 위치 및 위성 지리적 위치를 하나 이상으로 구성 됩니다. 여러 지리적 위치에 걸쳐 있는 단일 테 넌 트입니다. OneDrive 다중-Geo의 지리적 위치를 포함 하 여 테 넌 트 정보를에서 Azure Active Directory (AAD) 마스터입니다.</span><span class="sxs-lookup"><span data-stu-id="8b587-p101">In a OneDrive Multi-Geo configuration, your Office 365 tenant consists of a central location (also known as the default location) and one or more satellite geo locations. This is a single tenant that spans across multiple geo locations. In OneDrive Multi-Geo, your tenant information, including geo locations, is mastered in Azure Active Directory (AAD).</span></span> 

<span data-ttu-id="8b587-108">일부 주요 다중-지리적으로 분산 용어 구성의 기본 개념을 이해 하는데 도움이 되는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8b587-108">Here are some key multi-geo terms to help you understand the basic concepts of the configuration:</span></span>

-   <span data-ttu-id="8b587-109">**테 넌 트** -일반적으로 연결 된 하나 이상의 도메인을 포함 하는 Office 365 클라우드 조직의 표현 (등 http://contoso.sharepoint.com)합니다.</span><span class="sxs-lookup"><span data-stu-id="8b587-109">**Tenant** – An organization’s representation in the Office 365 cloud which typically has one or more domains associated with it (for example, http://contoso.sharepoint.com).</span></span> 

-   <span data-ttu-id="8b587-p102">**지리적으로 분산 위치** -테 넌 트의 데이터 호스팅되는 지리적 위치입니다. 다중-지리적으로 분산 테 넌 트 예: 북미 및 유럽 둘 이상의 지리적 위치에 걸쳐 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b587-p102">**Geo locations** – The geographic locations where your tenant’s data is hosted. Multi-geo tenants span more than one geo location, for example, North America and Europe.</span></span>

-   <span data-ttu-id="8b587-112">**허용 된 데이터 위치 (ADL)** -을 테 넌 트에 구성 된 호스트 OneDrive와 SharePoint 데이터에 지리적 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="8b587-112">**Allowed Data Locations (ADL)** – The geo locations for which your tenant has been configured to host OneDrive and SharePoint data.</span></span>

-   <span data-ttu-id="8b587-p103">**기본 설정 데이터 위치 (PDL)** -개별 사용자의 OneDrive 데이터가 저장 된 지리적 위치입니다. 관리자가 있는 테 넌 트에 대해 구성 된 허용 데이터 위치를 설정할 수 있습니다. OneDrive 사이트에 이미 있는 사용자에 대 한 PDL 변경 되는 경우 자신의 OneDrive 데이터 옮기지 않도록 새로운 지리적 위치에 자동으로 note 합니다. 자세한 내용은 [OneDrive 라이브러리를 다른 지리적 위치를 이동](move-onedrive-between-geo-locations.md) 을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="8b587-p103">**Preferred Data Location (PDL)** – The geo location where an individual user’s OneDrive data is stored. This can be set by the administrator to any of the Allowed Data Locations that have been configured for the tenant. Note that if you change the PDL for a user who already has a OneDrive site, their OneDrive data is not moved to the new geo location automatically. See [Move a OneDrive library to a different geo-location](move-onedrive-between-geo-locations.md) for more information.</span></span>

<span data-ttu-id="8b587-117">다중-지리적으로 분산을 사용 하도록 설정 4 개의 주요 단계를 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b587-117">Enabling Multi-Geo requires four key steps:</span></span>

1.  <span data-ttu-id="8b587-118">_Office 365의 다중-지리적으로 분산 기능_ 서비스 계획을 추가 하려면 계정 팀과 함께 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b587-118">Work with your account team to add the _Multi-Geo Capabilities in Office 365_ service plan.</span></span>

2.  <span data-ttu-id="8b587-119">원하는 대화 지리적 위치를 위성 및 테 넌 트에 추가 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b587-119">Choose your desired satellite geo location(s) and add them to your tenant.</span></span>

3.  <span data-ttu-id="8b587-p104">원하는 위성 지리적 위치를 사용자의 기본 데이터 위치를 설정 합니다. 사용자에 대 한 새 OneDrive 사이트 구축, 될 때 해당 PDL를 프로 비전 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8b587-p104">Set your users’ preferred data location to the desired satellite geo location. When a new OneDrive site is provisioned for a user, it is provisioned to their PDL.</span></span>

4.  <span data-ttu-id="8b587-122">필요에 따라 기본 데이터 위치로 홈 위치에서 사용자의 기존 OneDrive 사이트를 마이그레이션하십시오.</span><span class="sxs-lookup"><span data-stu-id="8b587-122">Migrate your users’ existing OneDrive sites from the home location to their preferred data location as needed.</span></span>

<span data-ttu-id="8b587-123">이러한 각 단계에 대 한 자세한 내용은 [OneDrive 구성에 대 한 비즈니스 다중-지리적으로 분산을](multi-geo-tenant-configuration.md) 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="8b587-123">See [Configure OneDrive for Business Multi-Geo](multi-geo-tenant-configuration.md) for details on each of these steps.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8b587-p105">Note는 Office 365의 다중-지리적으로 분산 기능 성능 최적화 사례에 대 한 설계 되지 않았습니다, 데이터 residency 요구 사항을 충족 하도록 디자인 되었습니다. Office 365에 대 한 성능 최적화 하는 방법에 대 한 정보에 대 한 [네트워크 계획 및 성능 조정 Office 365에 대 한](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) 참조 또는 지원 그룹에 게 문의 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b587-p105">Note that the Multi-Geo features of Office 365 are not designed for performance optimization cases, they are designed to meet data residency requirements. For information about performance optimization for Office 365, see [Network planning and performance tuning for Office 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) or contact your support group.</span></span>

<span data-ttu-id="8b587-p106">OneDrive 파일을 호스팅할 수 있는 위성 지리적 위치를 다음 위치 중 하나를 구성할 수 있습니다. 다중-지리적으로 분산을 계획할 때는 Office 365 테 넌 트에 추가 하려는 위치 목록을 확인 합니다. 필요한 경우 하나 또는 두 위성 위치로 시작 하 고 더 많은 지리적 위치를 점진적으로 확장 권장 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b587-p106">You can configure any of the following locations to be satellite geo locations where you can host OneDrive files. As you plan for multi-geo, make a list of the locations that you want to add to your Office 365 tenant. We recommend starting with one or two satellite locations and then gradually expanding to more geo locations, if needed.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="8b587-129"><strong>위치</strong></span><span class="sxs-lookup"><span data-stu-id="8b587-129"><strong>Location</strong></span></span></th>
<th align="left"><span data-ttu-id="8b587-130"><strong>코드</strong></span><span class="sxs-lookup"><span data-stu-id="8b587-130"><strong>Code</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="8b587-131">아시아 태평양</span><span class="sxs-lookup"><span data-stu-id="8b587-131">Asia-Pacific</span></span></td>
<td align="left"><span data-ttu-id="8b587-132">APC</span><span class="sxs-lookup"><span data-stu-id="8b587-132">APC</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="8b587-133">유럽 동쪽 중간 / / 아프리카</span><span class="sxs-lookup"><span data-stu-id="8b587-133">Europe / Middle East / Africa</span></span></td>
<td align="left"><span data-ttu-id="8b587-134">EUR</span><span class="sxs-lookup"><span data-stu-id="8b587-134">EUR</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="8b587-135">북미</span><span class="sxs-lookup"><span data-stu-id="8b587-135">North America</span></span></td>
<td align="left"><span data-ttu-id="8b587-136">이름</span><span class="sxs-lookup"><span data-stu-id="8b587-136">NAM</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="8b587-137">오스트레일리아</span><span class="sxs-lookup"><span data-stu-id="8b587-137">Australia</span></span></td>
<td align="left"><span data-ttu-id="8b587-138">오스트레일리아</span><span class="sxs-lookup"><span data-stu-id="8b587-138">AUS</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="8b587-139">캐나다</span><span class="sxs-lookup"><span data-stu-id="8b587-139">Canada</span></span></td>
<td align="left"><span data-ttu-id="8b587-140">수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b587-140">CAN</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="8b587-141">일본</span><span class="sxs-lookup"><span data-stu-id="8b587-141">Japan</span></span></td>
<td align="left"><span data-ttu-id="8b587-142">일본어</span><span class="sxs-lookup"><span data-stu-id="8b587-142">JPN</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="8b587-143">한국</span><span class="sxs-lookup"><span data-stu-id="8b587-143">Korea</span></span></td>
<td align="left"><span data-ttu-id="8b587-144">KOR</span><span class="sxs-lookup"><span data-stu-id="8b587-144">KOR</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="8b587-145">영국</span><span class="sxs-lookup"><span data-stu-id="8b587-145">United Kingdom</span></span></td>
<td align="left"><span data-ttu-id="8b587-146">GBR</span><span class="sxs-lookup"><span data-stu-id="8b587-146">GBR</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="8b587-147">예정 된 지리적 위치:</span><span class="sxs-lookup"><span data-stu-id="8b587-147">Upcoming geo locations:</span></span>
  
- <span data-ttu-id="8b587-148">프랑스</span><span class="sxs-lookup"><span data-stu-id="8b587-148">France</span></span>
- <span data-ttu-id="8b587-149">인도</span><span class="sxs-lookup"><span data-stu-id="8b587-149">India</span></span>

<span data-ttu-id="8b587-p107">다중-지리적으로 분산을 구성 하는 경우에 Office 365로 마이그레이션하는 동안 온-프레미스 인프라를 통합 하 여 기회를 수행 하는 것이 좋습니다. 예, 싱가포르 및 말레이시아에서 온-프레미스 팜이 다음을 병합할 수 있습니다 APC 위성 위치에 데이터 residency 요구 사항을 사용 하면 그렇게 하면 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b587-p107">When you configure multi-geo, consider taking the opportunity to consolidate your on-premises infrastructure while migrating to Office 365. For example, if you have on-premises farms in Singapore and Malaysia, then you can consolidate them to the APC satellite location, provided data residency requirements allow you to do so.</span></span>

## <a name="best-practices"></a><span data-ttu-id="8b587-152">모범 사례</span><span class="sxs-lookup"><span data-stu-id="8b587-152">Best practices</span></span>

<span data-ttu-id="8b587-p108">초기 테스트를 수행 하려면 Office 365의 테스트 사용자를 만드는 것이 좋습니다. 여기서 안내 일부 테스트 및 확인 단계가이 사용자와 온보드 프로덕션 사용자에 게 OneDrive 다중-지리적으로 분산 기능으로 진행 하기 전에 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b587-p108">We recommend that you create a test user in Office 365 to do some initial testing. We’ll walk through some testing and verification steps with this user before you proceed to onboard production users into the OneDrive Multi-Geo feature.</span></span>

<span data-ttu-id="8b587-p109">테스트 사용자를 사용 하 여 테스트를 완료 한 후 새로운 지리적 위치에 OneDrive를 사용 하 여 처음에-IT 부서에서 아마도 파일럿 그룹-를 선택 합니다. 이 첫번째 그룹에 대 한 OneDrive 아직 없는 사용자를 선택 합니다. 이 초기 그룹에서 최대 5 개 까지만 사용자 것을 권장 합니다 하 고 점진적으로 일괄 처리 된 롤아웃 접근 방식에 따라를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b587-p109">Once you’ve completed testing with the test user, select a pilot group – perhaps from your IT department – to be the first to use OneDrive in a new geo-location. For this first group, select users who do not yet have a OneDrive. We recommend no more than five people in this initial group and gradually expand following a batched rollout approach.</span></span>

<span data-ttu-id="8b587-p110">각 사용자는 *기본 데이터 위치* (PDL) Office 365의 OneDrive를 프로 비전 하는 지리적으로 분산 위치에서 확인할 수 있도록 설정 해야 합니다. 사용자의 기본 데이터 위치는 선택한 위성 위치 나 중앙 위치 중 하 나와 일치 해야 합니다. PDL 필드는 필수가 아님을, 하는 동안 모든 사용자에 게는 PDL을 설정 하는 것 하는 것이 좋습니다. 다중-지리적으로 분산 논리에 따라 중앙 위치에는 PDL 없는 사용자의 작업 부하를 구축할 수 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8b587-p110">Each user should have a *preferred data location* (PDL) set so that Office 365 can determine in which geo location to provision their OneDrive. The user’s preferred data location must match one of your chosen satellite locations or your central location. While the PDL field is not mandatory, we recommend that a PDL be set for all users. Workloads of a user without a PDL will be provisioned in the central location based on the Multi-Geo logic.</span></span>   

<span data-ttu-id="8b587-p111">사용자에 게 목록을 만들고 해당 사용자 계정 이름 (UPN) 하 고 적절 한 기본 설정된 데이터 위치에 대 한 위치 코드를 포함 합니다. 테스트 사용자 및 초기 파일럿 그룹을 시작 하 여 포함 됩니다. 구성 절차에 대 한이 목록에 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b587-p111">Create a list of your users, and include their user principal name (UPN) and the location code for the appropriate preferred data location. Include your test user and your initial pilot group to start with. You’ll need this list for the configuration procedures.</span></span>

<span data-ttu-id="8b587-p112">사용자에 게는 온-프레미스 Active Directory (AD) 시스템에서을 Azure Active Directory (AAD)을 동기화 하는 경우에 Azure Active Directory 연결을 사용 하 여 동기화 된 사용자에 대 한 기본 설정된 데이터 위치를 설정 해야 합니다. Azure AD PowerShell을 사용 하 여 동기화 된 사용자에 대 한 기본 설정된 데이터 위치를 직접 구성할 수 없습니다. AD에서 PDL를 설정 하 고 동기화 하는 단계에 대해서는 설명 [Azure Active Directory 연결 동기화: Office 365 리소스에 대 한 기본 설정된 데이터 위치 구성](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation)합니다.</span><span class="sxs-lookup"><span data-stu-id="8b587-p112">If your users are synchronized from an on-premises Active Directory (AD) system to Azure Active Directory (AAD), you must set the preferred data location for synchronized users by using Azure Active Directory Connect. You cannot directly configure the preferred data location for synchronized users using Azure AD PowerShell. The steps to set up PDL in AD and Synchronize it are covered in [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span>

<span data-ttu-id="8b587-p113">지리적 다중 테 넌 트 관리에서 대부분의 SharePoint 및 OneDrive 설정으로 비 geo 다중 테 넌 다를 수 및 서비스는 다중-지리적으로 분산을 인식 합니다. 검토 하는 [다중-지리적으로 분산 환경 관리](administering-a-multi-geo-environment.md) 구성을 진행 하기 전에 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8b587-p113">The administration of a multi-geo tenant can differ from a non-multi-geo tenant, as many of the SharePoint and OneDrive settings and services are multi-geo aware. We recommend that you review [Administering a multi-geo environment](administering-a-multi-geo-environment.md) before you proceed with your configuration.</span></span>

<span data-ttu-id="8b587-170">다중-지리적으로 분산 환경에서 최종 사용자의 환경에 대 한 자세한 내용은 [multgeo 환경에서 사용자 경험](multi-geo-user-experience.md) 을 읽어보십시오.</span><span class="sxs-lookup"><span data-stu-id="8b587-170">Read [User experience in a multgeo environment](multi-geo-user-experience.md) for details about your end users' experience in a multi-geo environment.</span></span>

<span data-ttu-id="8b587-171">OneDrive에 대 한 비즈니스 다중-지리적으로 분산 구성 시작 [OneDrive 구성에 대 한 비즈니스 다중-지리적으로 분산을](multi-geo-tenant-configuration.md)참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="8b587-171">To get started configuring OneDrive for Business Multi-Geo, see [Configure OneDrive for Business Multi-Geo](multi-geo-tenant-configuration.md).</span></span>

<span data-ttu-id="8b587-172">(영문)의 기본 데이터 위치에서 사용자를 가져오는데 필요한 구성을 완료 했으면, [사용자의 OneDrive 라이브러리를](move-onedrive-between-geo-locations.md) 마이그레이션할 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b587-172">Once you’ve completed the configuration, remember to [migrate your users' OneDrive libraries](move-onedrive-between-geo-locations.md) as needed to get your users working from their preferred data locations.</span></span>
