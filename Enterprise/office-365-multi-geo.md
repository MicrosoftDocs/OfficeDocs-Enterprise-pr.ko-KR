---
title: Microsoft 365 Multi-Geo
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Microsoft 365 Multi-Geo를 사용하여 Microsoft 365 범위를 여러 지리적 지역으로 확장합니다.
ms.openlocfilehash: d69d8adb83eb639589efec0863b2e15966339b58
ms.sourcegitcommit: 012bf4d8ad132435f9baeffd6f7e5ed264a8bfe0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/06/2020
ms.locfileid: "44057734"
---
# <a name="microsoft-365-multi-geo"></a><span data-ttu-id="c918e-103">Microsoft 365 Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="c918e-103">Microsoft 365 Multi-Geo</span></span>

<span data-ttu-id="c918e-104">Microsoft 365 Multi-Geo를 사용하면 Microsoft 365 범위를 기존 테넌트 내 여러 지리적 지역 및 / 또는 국가로 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c918e-104">With Microsoft 365 Multi-Geo, your organization can expand its Microsoft 365 presence to multiple geographic regions and/or countries within your existing tenant.</span></span> <span data-ttu-id="c918e-105">Microsoft 계정 팀에 문의하여 Microsoft 365 Multi-Geo용 Multi-National Company에 등록하세요.</span><span class="sxs-lookup"><span data-stu-id="c918e-105">Reach out to your Microsoft Account Team to sign up your Multi-National Company for Microsoft 365 Multi-Geo.</span></span>
  
<span data-ttu-id="c918e-106">Microsoft 365 Multi-Geo를 사용하여 데이터 상주 요구 사항을 충족하기 위해 선택한 지리적 위치의 미사용 데이터를 프로비저닝 및 저장하고, 동시에 귀하의 전 세계 작업자들이 최신 생산성 환경을 활용하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c918e-106">With Microsoft 365 Multi-Geo, you can provision and store data at rest in the geo locations that you've chosen to meet data residency requirements, and at the same time unlock your global roll out of modern productivity experiences to your workforce.</span></span>

#### <a name="video-introducing-microsoft-365-multi-geo"></a><span data-ttu-id="c918e-107">비디오: Microsoft 365 Multi-Geo 소개</span><span class="sxs-lookup"><span data-stu-id="c918e-107">Video: Introducing Microsoft 365 Multi-Geo</span></span>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1Yk6B?autoplay=false]

<span data-ttu-id="c918e-108">Multi-Geo 환경에서 Microsoft 365 테넌트는 중앙 위치(Microsoft 365 구독이 원래 제공되었던 위치)와 하나 이상의 위성 위치로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="c918e-108">In a Multi-Geo environment, your Microsoft 365 tenant consists of a central location (where your Microsoft 365 subscription was originally provisioned) and one or more satellite locations.</span></span> <span data-ttu-id="c918e-109">Multi-Geo 테넌트의 경우 지리적 위치, 그룹 및 사용자 정보에 대한 정보는 Azure Active Directory(AAD)에서 관리됩니다.</span><span class="sxs-lookup"><span data-stu-id="c918e-109">In a multi-geo tenant, the information about geo locations, groups, and user information, is mastered in Azure Active Directory (AAD).</span></span> <span data-ttu-id="c918e-110">테넌트 정보가 중앙에서 관리되고 각 지리적 위치와 동기화되기 때문에 회사의 모든 사람과 관련된 공유 및 경험은 전역 세계적으로 인식됩니다.</span><span class="sxs-lookup"><span data-stu-id="c918e-110">Because your tenant information is mastered centrally and synchronized into each geo location, sharing and experiences involving anyone from your company contain global awareness.</span></span>

![SharePoint 관리 센터의 Multi-Geo 지도 스크린샷](media/multi-geo-world-map.png)

<span data-ttu-id="c918e-112">참고로, Microsoft 365 Multi-Geo는 성능 최적화를 위해 설계되지 않았고 데이터 상주 요구 사항을 충족하도록 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c918e-112">Note that Microsoft 365 Multi-Geo is not designed for performance optimization, it is designed to meet data residency requirements.</span></span> <span data-ttu-id="c918e-113">Microsoft 365의 성능 최적화에 대한 자세한 내용은 [Microsoft 365의 네트워크 계획 및 성능 조정](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848)을 참조하거나 지원 그룹에 문의하세요.</span><span class="sxs-lookup"><span data-stu-id="c918e-113">For information about performance optimization for Microsoft 365, see [Network planning and performance tuning for Microsoft 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) or contact your support group.</span></span>

## <a name="terminology"></a><span data-ttu-id="c918e-114">용어</span><span class="sxs-lookup"><span data-stu-id="c918e-114">Terminology</span></span>

<span data-ttu-id="c918e-115">다음은 Microsoft 365 Multi-Geo를 설명하는 데 사용되는 주요 용어입니다.</span><span class="sxs-lookup"><span data-stu-id="c918e-115">Here are the key terms used in describing Microsoft 365 Multi-Geo:</span></span>

- <span data-ttu-id="c918e-116">**중앙 위치** - 테넌트가 원래 프로비저닝된 지리적 위치</span><span class="sxs-lookup"><span data-stu-id="c918e-116">**Central location** - the geo location where your tenant was originally provisioned.</span></span>
- <span data-ttu-id="c918e-117">**지역 관리자** - 하나 이상의 지정된 위성 위치를 관리할 수 있는 관리자</span><span class="sxs-lookup"><span data-stu-id="c918e-117">**Geo administrator** - An administrator who can administer one or more specified satellite locations.</span></span>
- <span data-ttu-id="c918e-118">**지역 코드** - 주어직 지리적 위치에 대한 세 자리 코드</span><span class="sxs-lookup"><span data-stu-id="c918e-118">**Geo code** - a three-letter code for a given geo location.</span></span>
- <span data-ttu-id="c918e-119">**지리적 위치** – Exchange 우편함 및 OneDrive 및 SharePoint 사이트를 포함하여 데이터를 호스팅하기 위해 Multi-Geo 테넌트에서 사용할 수있는 지리적 위치</span><span class="sxs-lookup"><span data-stu-id="c918e-119">**Geo location** – A geographic location that can be used in a multi-geo tenant to host data, including Exchange mailboxes and OneDrive and SharePoint sites.</span></span>
- <span data-ttu-id="c918e-120">**선호 하는 데이터 위치 (PDL)** - 사용자가 Exchange 사서함과 OneDrive를 프로비저닝하는 위치를 나타내는 관리자가 설정한 사용자 속성</span><span class="sxs-lookup"><span data-stu-id="c918e-120">**Preferred Data Location (PDL)** – A user property set by the administrator that indicates where the geo location where the users Exchange mailbox and OneDrive should be provisioned.</span></span> <span data-ttu-id="c918e-121">또한 PDL은 사용자가 만든 SharePoint 사이트가 프로비저닝되는 위치를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="c918e-121">The PDL also determines where SharePoint sites that are created by the user are provisioned.</span></span>
- <span data-ttu-id="c918e-122">**위성 위치** - 지리적 인식 Microsoft 365 작업(SharePoint, OneDrive 및 Exchange)이 Multi-Geo 테넌트에서 사용하도록 설정된 지리적 위치</span><span class="sxs-lookup"><span data-stu-id="c918e-122">**Satellite location** – The geo locations where the geo-aware Microsoft 365 workloads (SharePoint, OneDrive, and Exchange) are enabled in a multi-geo tenant.</span></span>
- <span data-ttu-id="c918e-123">**테넌트** – Microsoft 365에서 일반적으로 하나 이상의 도메인에 연결되어 있는 조직을 나타내는 표현(예: contoso.com)</span><span class="sxs-lookup"><span data-stu-id="c918e-123">**Tenant** – An organization's representation in Microsoft 365 which typically has one or more domains associated with it (for example, contoso.com).</span></span>

## <a name="microsoft-365-multi-geo-availability"></a><span data-ttu-id="c918e-124">Microsoft 365 Multi-Geo 사용 가능 여부</span><span class="sxs-lookup"><span data-stu-id="c918e-124">Microsoft 365 Multi-Geo availability</span></span>

<span data-ttu-id="c918e-125">Microsoft 365 Multi-Geo는 현재 다음 지역 및 국가에서 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="c918e-125">Microsoft 365 Multi-Geo is currently offered in these regions and countries:</span></span>

[!INCLUDE [Microsoft 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

## <a name="getting-started"></a><span data-ttu-id="c918e-126">시작하기</span><span class="sxs-lookup"><span data-stu-id="c918e-126">Getting started</span></span>

<span data-ttu-id="c918e-127">Multi-Geo를 시작하려면 이러한 단계를 따르세요.</span><span class="sxs-lookup"><span data-stu-id="c918e-127">Follow these steps to get started with multi-geo:</span></span>

1. <span data-ttu-id="c918e-128">계정 팀과 협의하여 _Microsoft 365의 Multi-Geo 기능_ 서비스 계획을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="c918e-128">Work with your account team to add the _Multi-Geo Capabilities in Microsoft 365_ service plan.</span></span> <span data-ttu-id="c918e-129">계정 팀이 필요한 라이센스 수를 추가할 수 있도록 안내합니다.</span><span class="sxs-lookup"><span data-stu-id="c918e-129">They will guide you to add the number of licenses needed.</span></span> <span data-ttu-id="c918e-130">Multi-Geo 기능은 Microsoft 365 구독을 250개 이상 보유한 EA 고객에게 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="c918e-130">Multi-Geo feature is available to EA customers with a minimum of 250 Microsoft 365 subscriptions.</span></span>

   <span data-ttu-id="c918e-131">Microsoft 365 Multi-Geo를 사용하여 시작하기 전에 Microsoft에서는 Multi-Geo 지원을 위해 Exchange Online 테넌트를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c918e-131">Before you can start using Microsoft 365 Multi-Geo, Microsoft needs to configure your Exchange Online tenant for multi-geo support.</span></span> <span data-ttu-id="c918e-132">이 일회성 구성 프로세스는 *Microsoft 365의 Multi-Geo 기능* 서비스 계획을 주문하고 테넌트에 라이선스가 표시된 후에 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="c918e-132">This one-time configuration process is triggered after you order the *Multi-Geo Capabilities in Microsoft 365* service plan and the licenses show up in your tenant.</span></span> <span data-ttu-id="c918e-133">Multi-Geo 라이선스가 적용되면 [Microsoft 365 메시지 센터](https://support.office.com/article/38FB3333-BFCC-4340-A37B-DEDA509C2093)에서 알림을 받게 되며 Microsoft 365 Multi-Geo 기능을 구성하고 사용하기 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c918e-133">You'll receive notifications in the [Microsoft 365 message center](https://support.office.com/article/38FB3333-BFCC-4340-A37B-DEDA509C2093) once your Multi-Geo licenses are applied and you then may begin configuring and using your Microsoft 365 Multi-Geo capabilities.</span></span>

2. <span data-ttu-id="c918e-134">[Multi-Geo 환경 계획](plan-for-multi-geo.md)을 읽으세요.</span><span class="sxs-lookup"><span data-stu-id="c918e-134">Read [Plan your multi-geo environment](plan-for-multi-geo.md).</span></span>

3. <span data-ttu-id="c918e-135">[Multi-Geo 환경 관리](administering-a-multi-geo-environment.md) 및 [사용자가 환경을 경험하는 방법](multi-geo-user-experience.md)에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="c918e-135">Learn about [administering a multi-geo environment](administering-a-multi-geo-environment.md) and [how your users will experience the environment](multi-geo-user-experience.md).</span></span>

4. <span data-ttu-id="c918e-136">Microsoft 365 Multi-Geo를 설치할 준비가 되면 [Multi-Geo의 테넌트를 구성합니다](multi-geo-tenant-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="c918e-136">When you are ready to set up Microsoft 365 Multi-Geo, [configure your tenant for multi-geo](multi-geo-tenant-configuration.md).</span></span>

5. <span data-ttu-id="c918e-137">[검색 설정](configure-search-for-multi-geo.md)</span><span class="sxs-lookup"><span data-stu-id="c918e-137">[Set up search](configure-search-for-multi-geo.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c918e-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c918e-138">See also</span></span>

[<span data-ttu-id="c918e-139">Exchange Online 및 OneDrive의 Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="c918e-139">Multi-Geo in Exchange Online and OneDrive</span></span>](https://Aka.ms/GoMultiGeo)

[<span data-ttu-id="c918e-140">OneDrive 및 SharePoint Online의 Multi-Geo 기능</span><span class="sxs-lookup"><span data-stu-id="c918e-140">Multi-Geo Capabilities in OneDrive and SharePoint Online</span></span>](https://docs.microsoft.com/office365/enterprise/multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365)

[<span data-ttu-id="c918e-141">Exchange Online의 Multi-Geo 기능</span><span class="sxs-lookup"><span data-stu-id="c918e-141">Multi-Geo Capabilities in Exchange Online</span></span>](https://docs.microsoft.com/office365/enterprise/multi-geo-capabilities-in-exchange-online)

[<span data-ttu-id="c918e-142">Multi-Geo 환경의 Teams 작업 환경</span><span class="sxs-lookup"><span data-stu-id="c918e-142">Teams experience in a multi-geo environment</span></span>](https://docs.microsoft.com/microsoftteams/teams-experience-o365odb-spo-multi-geo)
