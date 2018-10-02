---
title: OneDrive 및 Office 365의 SharePoint Online에 제공되는 다중 위치 기능
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/16/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
ms.assetid: 094e86f2-9ff0-40ac-af31-28fcaba00c1d
description: OneDrive 및 SharePoint Online의 다중 위치 기능으로 여러 지리적 지역으로 Office 365 범위를 확장합니다.
ms.openlocfilehash: c6648dc8a0b225105e408fc082f6bb4d1a1b4930
ms.sourcegitcommit: 2f138e0733266ab4b179bbe882c734500118dde1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2018
ms.locfileid: "24012738"
---
# <a name="multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365"></a><span data-ttu-id="23e21-103">OneDrive 및 Office 365의 SharePoint Online에 제공되는 다중 위치 기능</span><span class="sxs-lookup"><span data-stu-id="23e21-103">Multi-Geo Capabilities in OneDrive and SharePoint Online in Office 365</span></span>

<span data-ttu-id="23e21-p101">OneDrive 및 SharePoint Online의 Multi-Geo 기능을 사용하여 조직은 Office 365 사용 범위를 기존 테넌트 내의 여러 지리적 지역 및/또는 국가로 확장할 수 있습니다. 또한 Microsoft 계정 팀에 연락하여 비즈니스용 OneDrive Multi-Geo에 귀하의 다국적 기업을 등록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23e21-p101">With multi-geo capabilities in OneDrive and SharePoint Online, your organization can expand its Office 365 presence to multiple geographic regions and/or countries within your existing tenant. Reach out to your Microsoft Account Team to sign up your Multi-National Company for OneDrive for Business Multi-Geo.</span></span>
  
<span data-ttu-id="23e21-106">OneDrive Multi-Geo를 사용하여 데이터 상주 요구 사항을 충족하기 위해 선택한 지리적 위치에서 미사용 데이터를 프로비전 및 저장하고, 동시에 귀하의 전 세계 작업자들이 최신 생산선 환경을 활용하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23e21-106">With OneDrive Multi-Geo, you can provision and store data at rest in the geo locations that you've chosen to meet data residency requirements, and at the same time unlock your global roll out of modern productivity experiences to your workforce.</span></span>
  
<span data-ttu-id="23e21-107">다중 위치 기능이 조직에 유용하게 사용될 수 있는 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="23e21-107">Here's how multi-geo features can benefit your organization:</span></span>
  
- <span data-ttu-id="23e21-108">단일 Office 365 테넌트가 여러 개의 지리적 위치에 걸쳐 있는 하나의 연결된 전역 조직으로 작용합니다.</span><span class="sxs-lookup"><span data-stu-id="23e21-108">Operate as one global connected organization with a single Office 365 tenant spanning multiple geo locations.</span></span>
    
- <span data-ttu-id="23e21-109">지정된 지리적 위치 내에서 미사용 데이터를 생성 및 호스트하여 데이터 상주 요구 사항을 충족합니다.</span><span class="sxs-lookup"><span data-stu-id="23e21-109">Meet data residency requirements by creating and hosting data-at-rest within a specified geo location.</span></span>
    
- <span data-ttu-id="23e21-110">중앙 위치 사용자가 사용하는 것과 동일한 최신 생산성 환경을 위성 사용자도 누릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23e21-110">Empower your satellite users with the same modern productivity experiences enjoyed by your central location users.</span></span>
    
- <span data-ttu-id="23e21-111">콘텐츠 액세스 권한을 안전하게 유지하면서 역할 변화에 맞춰 지리적 위치 간을 이동할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="23e21-111">Enable your users to move across geo locations as their role changes, while access to their content is kept intact.</span></span>
    
- <span data-ttu-id="23e21-112">지리적 위치별 공유 정책을 조정하고, 사이트별로 데이터 손실 방지 정책을 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="23e21-112">Tailor your sharing policies per geo location and data loss prevention policies per site.</span></span>
    
- <span data-ttu-id="23e21-113">지리적 위치별로 eDiscovery 관리자를 지정하고, 지리적 위치에 맞게 관리 방식을 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23e21-113">Designate eDiscovery managers per geo location and allow governing cases tailored to your geo location.</span></span>
    
- <span data-ttu-id="23e21-114">추가적인 지리적 위치에 대한 고유한 URL 네임스페이스(예: ContosoEUR.sharepoint.com)를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="23e21-114">Choose unique URL namespaces (for example, ContosoEUR.sharepoint.com) for your additional geo locations.</span></span>
    
- <span data-ttu-id="23e21-115">지역의 온-프레미스 데이터를 Office 365 다중 위치 테넌트에 통합합니다.</span><span class="sxs-lookup"><span data-stu-id="23e21-115">Consolidate your regional on-premises data into your Office 365 multi-geo tenant.</span></span>
    
<span data-ttu-id="23e21-p102">다중 위치 구성에서 Office 365 테넌트는 하나의 중앙 위치(기본 위치라고도 함)와 하나 이상의 위성 지리적 위치로 구성됩니다. 다중 위치의 핵심 개념은 단일 테넌트가 하나의 다중 지리적 위치에 걸쳐 있는 다중 위치 개념입니다. 다중 위치 테넌트에서 지리적 위치, 그룹 및 사용자에 대한 정보는 AAD(Azure Active Directory)에서 마스터됩니다. 테넌트 정보가 중앙에서 마스터된 후 각 지리적 위치로 동기화되므로, 회사 직원 누구든지 전역 정보를 공유하고 경험할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23e21-p102">In a multi-geo configuration, your Office 365 tenant consists of a central location (also known as the default location) and one or more satellite geo locations. The key concept of multi-geo is that a single tenancy will span across one multiple geo locations. In a multi-geo tenant, the information about geo locations, groups, and user information, is mastered in Azure Active Directory (AAD). Because your tenant information is mastered centrally and synchronized into each geo location, sharing and experiences involving anyone from your company contain global awareness.</span></span>

## <a name="video-introducing-office-365-multi-geo"></a><span data-ttu-id="23e21-120">비디오: Office 365 Multi-Geo 소개</span><span class="sxs-lookup"><span data-stu-id="23e21-120">Video: Introducing Office 365 Multi-Geo</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE1Yk6B?autoplay=false]
  
## <a name="get-multi-geo-features-in-three-simple-steps"></a><span data-ttu-id="23e21-121">세 가지 간단한 단계로 다중 위치 기능 설정</span><span class="sxs-lookup"><span data-stu-id="23e21-121">Get multi-geo features in three simple steps</span></span>

<span data-ttu-id="23e21-122">다중 위치 기능은 다음과 같이 간단히 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23e21-122">Configuring multi-geo is easy:</span></span>
  
1. <span data-ttu-id="23e21-p103">계정 팀과 협의하여 추가 하려면 계정 팀에서 작업 하는 _Office 365의 Multi-Geo 기능_ 서비스 계획을 추가합니다. 필요한 라이선스 수를 추가하는 과정이 안내됩니다.</span><span class="sxs-lookup"><span data-stu-id="23e21-p103">Work with your account team to add the _Multi-Geo Capabilities in Office 365_ service plan. They will guide you to add the number of licenses needed.</span></span>
    
2. <span data-ttu-id="23e21-125">위성 위치를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="23e21-125">Add your satellite locations.</span></span>
    
3. <span data-ttu-id="23e21-126">해당 위치에 맞게 사용자 계정을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="23e21-126">Configure your user accounts for the appropriate location.</span></span>
    
## <a name="multi-geo-status-and-availability"></a><span data-ttu-id="23e21-127">다중 위치 상태 및 가용성</span><span class="sxs-lookup"><span data-stu-id="23e21-127">Multi-Geo status and availability</span></span>

<span data-ttu-id="23e21-128">OneDrive Multi-Geo는 현재 다음 지역 및 국가에서 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="23e21-128">OneDrive Multi-Geo is currently offered in these regions and countries:</span></span>
  
- <span data-ttu-id="23e21-129">아시아 태평양</span><span class="sxs-lookup"><span data-stu-id="23e21-129">Asia-Pacific</span></span>
    
- <span data-ttu-id="23e21-130">오스트레일리아</span><span class="sxs-lookup"><span data-stu-id="23e21-130">Australia</span></span>
    
- <span data-ttu-id="23e21-131">캐나다</span><span class="sxs-lookup"><span data-stu-id="23e21-131">Canada</span></span>
    
- <span data-ttu-id="23e21-132">EMEA(유럽 연합)</span><span class="sxs-lookup"><span data-stu-id="23e21-132">European Union (EMEA)</span></span>

- <span data-ttu-id="23e21-133">프랑스</span><span class="sxs-lookup"><span data-stu-id="23e21-133">France</span></span>
    
- <span data-ttu-id="23e21-134">일본</span><span class="sxs-lookup"><span data-stu-id="23e21-134">Japan</span></span>
    
- <span data-ttu-id="23e21-135">영국</span><span class="sxs-lookup"><span data-stu-id="23e21-135">United Kingdom</span></span>
    
- <span data-ttu-id="23e21-136">미국(북미)</span><span class="sxs-lookup"><span data-stu-id="23e21-136">United States (North America)</span></span>
    
- <span data-ttu-id="23e21-137">한국</span><span class="sxs-lookup"><span data-stu-id="23e21-137">Korea</span></span>
      
<span data-ttu-id="23e21-138">예정된 지리적 위치:</span><span class="sxs-lookup"><span data-stu-id="23e21-138">Upcoming geo locations:</span></span>
  
- <span data-ttu-id="23e21-139">인도</span><span class="sxs-lookup"><span data-stu-id="23e21-139">India</span></span>
    
## <a name="getting-started"></a><span data-ttu-id="23e21-140">시작</span><span class="sxs-lookup"><span data-stu-id="23e21-140">Getting started</span></span>

<span data-ttu-id="23e21-p104">비즈니스용 OneDrive Multi-Geo를 시작하려는 경우 첫 번째 단계는 [비즈니스용 OneDrive Multi-Geo 환경 계획](plan-for-multi-geo.md)입니다. 다음은 [다중 위치 환경 관리 방법 알아보기](administering-a-multi-geo-environment.md) 및 [사용자가 다중 위치 환경을 경험하는 방식](multi-geo-user-experience.md)입니다. 비즈니스용 OneDrive Multi-Geo를 설정할 준비가 되면 [다중 위치에 대한 테넌트를 구성](multi-geo-tenant-configuration.md)하고 [기존 OneDrive 사이트를 새 지리적 위치로 이동](move-onedrive-between-geo-locations.md)한 후 [검색을 설정](configure-search-for-multi-geo.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="23e21-p104">To get started with OneDrive for Business Multi-Geo, the first step is to [plan your OneDrive for Business Multi-Geo environment](plan-for-multi-geo.md). Next, [learn about administering a multi-geo environment](administering-a-multi-geo-environment.md) and [how your users will experience a multi-geo environment](multi-geo-user-experience.md). When you are ready to set up OneDrive for Business Multi-Geo, [configure your tenant for multi-geo](multi-geo-tenant-configuration.md), then [move any existing OneDrive sites to thier new geo-locations](move-onedrive-between-geo-locations.md) and [set up search](configure-search-for-multi-geo.md).</span></span>
