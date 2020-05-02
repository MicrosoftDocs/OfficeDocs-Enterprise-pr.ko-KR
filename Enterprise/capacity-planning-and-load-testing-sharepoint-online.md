---
title: Capacity planning and load testing SharePoint Online(용량 계획과 부하 테스트가 가능한 SharePoint Online)
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 04/10/2019
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- SPO160
- MET150
ms.assetid: c932bd9b-fb9a-47ab-a330-6979d03688c0
description: 이 문서에서는 허용 되지 않으므로 기존 부하 테스트를 수행 하지 않고 SharePoint Online에 배포 하는 방법에 대해 설명 합니다.
ms.openlocfilehash: d082dbd93f9724080118f5e387713dc374e50643
ms.sourcegitcommit: d1022143bdefdd5583d8eff08046808657b49c94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/02/2020
ms.locfileid: "44004611"
---
# <a name="capacity-planning-and-load-testing-sharepoint-online"></a><span data-ttu-id="35d23-103">Capacity planning and load testing SharePoint Online(용량 계획과 부하 테스트가 가능한 SharePoint Online)</span><span class="sxs-lookup"><span data-stu-id="35d23-103">Capacity planning and load testing SharePoint Online</span></span>
<span data-ttu-id="35d23-104">이 문서에서는 SharePoint Online에서 부하 테스트가 허용 되지 않으므로 기존 부하 테스트 없이 SharePoint Online에 배포 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="35d23-104">This article describes how you can deploy to SharePoint Online without traditional load testing, since load-testing is not permitted on SharePoint Online.</span></span> <span data-ttu-id="35d23-105">SharePoint Online은 클라우드 서비스 이며 부하 기능, 서비스의 전체 부하 균형은 Microsoft에 의해 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="35d23-105">SharePoint Online is a cloud service and the load capabilities, health and overall balance of load in the service is managed by Microsoft.</span></span>
  
<span data-ttu-id="35d23-106">사이트 실행을 성공적으로 수행할 수 있도록 하기 위한 가장 좋은 방법은 [포털 시작 롤아웃 계획](https://docs.microsoft.com/office365/enterprise/planportallaunchroll-out)에서 강조 표시 되는 기본 원칙, 사례 및 권장 사항을 따르는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="35d23-106">The best approach to ensuring the success of launching your site is to follow basic principles, practices and recommendations which are highlighted in the [plan your portal launch roll-out](https://docs.microsoft.com/office365/enterprise/planportallaunchroll-out).</span></span>

## <a name="overview-of-how-sharepoint-online-performs-capacity-planning"></a><span data-ttu-id="35d23-107">SharePoint Online의 용량 계획 수행 방법 개요</span><span class="sxs-lookup"><span data-stu-id="35d23-107">Overview of how SharePoint Online performs Capacity planning</span></span> 
<span data-ttu-id="35d23-108">온-프레미스 배포를 통해 SharePoint Online의 주요 장점 중 하나는 배포 된 지역의 사용자에 대 한 최적화 뿐 아니라 클라우드의 회복 력입니다.</span><span class="sxs-lookup"><span data-stu-id="35d23-108">One of the main benefits of SharePoint Online over an on-premises deployment is the elasticity of the cloud as well as optimizations for users in distributed regions.</span></span> <span data-ttu-id="35d23-109">대규모 환경에서는 수백만 명의 사용자를 매일 처리할 수 있도록 설정 되어 있으므로, 팜 균형 조정 및 확장을 통해 용량을 효과적으로 처리 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="35d23-109">Our large scale environment is set up to service millions of users on a daily basis, so it is important that we handle capacity effectively by balancing and expanding farms.</span></span>
  
<span data-ttu-id="35d23-110">한 팜의 모든 테 넌 트에 대 한 증가는 종종 예측 불가능 하지만, 집계 된 요청의 합계는 시간에 따라 예측할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="35d23-110">While the growth is often unpredictable for any one tenant in any one farm, the aggregated sum of requests is predictable over time.</span></span> <span data-ttu-id="35d23-111">SharePoint Online의 성장 추세를 파악 하 여 향후 확장이 계획 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35d23-111">By identifying the growth trends in SharePoint Online, we can plan for future expansion.</span></span>
  
<span data-ttu-id="35d23-112">어떤 팜에서 든 효율적으로 용량을 사용 하 고 예기치 않은 성장을 처리 하기 위해 서비스의 다양 한 요소를 추적 하 고 모니터링 하는 자동화 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="35d23-112">In order to efficiently use capacity and deal with unexpected growth, in any farm, we have automation that tracks and monitors various elements of the service.</span></span> <span data-ttu-id="35d23-113">여러 메트릭이 사용 되며,이는 기본 구성 요소의 CPU 부하 중 하나인 프런트 엔드 서버를 수직 확장 하는 신호로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="35d23-113">Multiple metrics are utilized, with one of the main ones being CPU load, which is used as a signal to scale-up front end servers.</span></span> <span data-ttu-id="35d23-114">또한 시간에 따른 부하 및 증가에 따라 SQL 환경을 확장 하 고 단계 및 전파를 통해 해당 부하와 성장을 적절 하 게 배포할 수 있으므로 [단계별/물결 방식을 사용](https://docs.microsoft.com/office365/enterprise/planportallaunchroll-out)하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="35d23-114">Additionally to this we recommend a [phased / wave approach](https://docs.microsoft.com/office365/enterprise/planportallaunchroll-out), as SQL environments will scale according to load and growth over time, and following the phases and waves allows for the correct distribution of that load and growth.</span></span> 

<span data-ttu-id="35d23-115">용량은 하드웨어를 지속적으로 추가 하는 것 보다 더 많은 작업을 수행 하는 것이 아니라, 해당 용량을 관리 하 고 제어 하 여 유효한 부하 요청을 처리 하 고 있는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35d23-115">Capacity is more than just about adding more hardware on a continuous basis but it also pertains to managing and controlling that capacity to ensure it is servicing valid load requests.</span></span> <span data-ttu-id="35d23-116">고객은 권장 지침에 따라 최상의 환경을 유지 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="35d23-116">We recommend that customers follow the recommended guidance to ensure they have the best experience.</span></span> <span data-ttu-id="35d23-117">또한 서비스에서 "악성 프로그램" 동작을 허용 하지 않도록 제한 패턴과 제어가 적절 하 게 구현 되었음을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="35d23-117">It also means that we have throttling patterns and controls in place to ensure we do not allow "abusive" behavior in the service.</span></span> <span data-ttu-id="35d23-118">의도적인 것이 전부는 아닐 수는 있지만 해당 동작의 영향을 제한 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="35d23-118">Whilst not all "bad" behavior is intentional, we do have to ensure that we limit the effect of that behavior.</span></span> <span data-ttu-id="35d23-119">제한 및이를 방지 하는 방법에 대 한 자세한 내용은 [제한 지침](https://docs.microsoft.com/sharepoint/dev/general-development/how-to-avoid-getting-throttled-or-blocked-in-sharepoint-online) 문서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="35d23-119">For further information on throttling and how to avoid it, review the [how to avoid being throttled guidance](https://docs.microsoft.com/sharepoint/dev/general-development/how-to-avoid-getting-throttled-or-blocked-in-sharepoint-online) article.</span></span>

## <a name="why-you-cannot-load-test-sharepoint-online"></a><span data-ttu-id="35d23-120">테스트 SharePoint Online을 로드할 수 없는 이유</span><span class="sxs-lookup"><span data-stu-id="35d23-120">Why you cannot load test SharePoint Online</span></span>
<span data-ttu-id="35d23-121">온-프레미스 환경에서는 부하 테스트를 사용 하 여 확장 가정의 유효성을 검사 하 고 팜의 중단 지점을 찾습니다. 부하에 따라 포화</span><span class="sxs-lookup"><span data-stu-id="35d23-121">With on-premises environments, load testing is used to validate scale assumption and ultimately find the breaking point of a farm; by saturating it with load.</span></span> 

<span data-ttu-id="35d23-122">SharePoint Online을 사용 하는 경우에는 배율이 비교적 유체 이며 특정 추론을 기반으로 하 여 부하를 조정 하 고 제한 및 제어 하는 경우에는 다른 작업이 수행 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="35d23-122">With SharePoint Online we need to do things differently because the scale is relatively fluid and adjusts, throttles and controls load, based on certain heuristics.</span></span> <span data-ttu-id="35d23-123">대규모의 다중 테 넌 트 환경에서는 동일한 팜의 모든 테 넌 트를 보호 해야 하므로 부하 테스트를 자동으로 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="35d23-123">Being such a large scale multi-tenant environment, we must protect all tenants in the same farm, so we will automatically throttle any load tests.</span></span> <span data-ttu-id="35d23-124">그러나 시간을 들 여 테스트를 수행 하는 것 외에도, 오늘 테스트 한 팜이 테스트를 수행 하는 동안 규모를 변경 하거나 테스트 후에 확장 및 팜 균형 작업이 진행 됨에 따라 시간이 초과 되어 결과를 disappointing 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35d23-124">If you do however attempt to load test, besides being throttled, you will receive disappointing and potentially misleading results because the farm you tested today will probably have had scale changes during the testing window or within hours after testing, as scale and farm balancing actions are performed on an on-going basis.</span></span>

<span data-ttu-id="35d23-125">여기서는 테스트 SharePoint를 서비스로 로드 하는 대신 권장 되는 방법에 중점을 둔 [채 정상적인 포털 지침을 만들고, 시작 하 고, 유지 관리](https://go.microsoft.com/fwlink/?linkid=2105838) 하는 방법을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="35d23-125">Instead of trying to load test SharePoint as a service, rather focus on following the recommended practices and follow the [Creating, launching and maintaining a healthy portal](https://go.microsoft.com/fwlink/?linkid=2105838) guidance.</span></span>
