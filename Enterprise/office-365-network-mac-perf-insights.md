---
title: Office 365 network performance insights (미리 보기)
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 02/04/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Office 365 network performance insights (미리 보기)
ms.openlocfilehash: 2e57ffabec5b2172cb36f10135406ddda95bc1c5
ms.sourcegitcommit: e2f7bb4ccd4c74902235f680104ca6b56c051587
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/19/2020
ms.locfileid: "42106403"
---
# <a name="office-365-network-performance-insights-preview"></a><span data-ttu-id="038c1-103">Office 365 network performance insights (미리 보기)</span><span class="sxs-lookup"><span data-stu-id="038c1-103">Office 365 network performance insights (preview)</span></span>

<span data-ttu-id="038c1-104">Microsoft 365 관리 센터 네트워크 성능 페이지에는 사무실 사무소에 대 한 네트워크 perimeters 디자인 시 도움이 될 수 있는 Office 365 네트워크 정보가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="038c1-104">The Microsoft 365 Admin Center network performance pages show Office 365 network insights which can help in designing network perimeters for your office locations.</span></span> <span data-ttu-id="038c1-105">각 사무실 위치에 대해 표시할 수 있는 5 가지 특정 네트워크 정보가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="038c1-105">There are five specific network insights that may be shown for each office location.</span></span>

>[!IMPORTANT]
><span data-ttu-id="038c1-106">네트워크 성능 권장 사항, Microsoft 365 관리 센터의 통찰력 및 평가는 현재 미리 보기 상태 이며, 기능 미리 보기 프로그램에 등록 되어 있는 Office 365 테 넌 트에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="038c1-106">Network performance recommendations, insights and assessments in the Microsoft 365 Admin Center is currently in preview status, and is only available for Office 365 tenants that have been enrolled in the feature preview program.</span></span>

## <a name="backhauled-network-egress"></a><span data-ttu-id="038c1-107">Backhauled 네트워크 송신</span><span class="sxs-lookup"><span data-stu-id="038c1-107">Backhauled network egress</span></span>

<span data-ttu-id="038c1-108">사용자 위치에서 네트워크 송신으로의 거리가 500 마일 (800 킬로미터) 보다 크고,이는 성능에 영향을 기대할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="038c1-108">The distance from the user location to the network egress is greater than 500 miles (800 kilometers) and this is expected to be impacting performance.</span></span> <span data-ttu-id="038c1-109">로컬 송신 사용자에 게 더 가까이 권장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="038c1-109">Local egress closer to the user is recommended.</span></span>

<span data-ttu-id="038c1-110">이는 사무실 위치와 네트워크 송신 사이의 거리가 500 마일 보다 큼을 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="038c1-110">This identifies that the distance between the office location and the network egress is more than 500 miles.</span></span> <span data-ttu-id="038c1-111">Office 위치는 난독 처리 된 클라이언트 컴퓨터 위치로 식별 되며 네트워크 송신 위치는 역방향 IP 주소를 위치 데이터베이스에 사용 하 여 식별 됩니다.</span><span class="sxs-lookup"><span data-stu-id="038c1-111">The office location is identified by an obfuscated client machine location and the network egress location is identified by using reverse IP Address to location databases.</span></span> <span data-ttu-id="038c1-112">컴퓨터에서 Windows 위치 서비스를 사용 하지 않도록 설정 하면 office 위치가 정확 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="038c1-112">The office location may be inaccurate if Windows Location Services is disabled on machines.</span></span> <span data-ttu-id="038c1-113">역방향 IP 주소 데이터베이스 정보가 부정확 한 경우 네트워크 송신 위치가 부정확 하 게 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="038c1-113">The network egress location may be inaccurate if the reverse IP Address database information is inaccurate.</span></span>

<span data-ttu-id="038c1-114">여기에는 사무실 위치, 네트워크 송신 위치 및 이러한 간의 거리가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="038c1-114">Details for this insight include the office location, the network egress location, and the distance between them.</span></span>

<span data-ttu-id="038c1-115">이에 대 한 자세한 정보를 제공 하려면 인터넷에서 Microsoft의 네트워크에 연결 하 고 Office 365 서비스 전면 도어에 연결할 수 있도록 네트워크를 office 위치에 더 가깝게 egress로 설정 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="038c1-115">For this insight we would recommend network egress closer to the office location so that connectivity can route optimally to Microsoft's network on the Internet and onto Office 365 service front doors.</span></span> <span data-ttu-id="038c1-116">또한 사용자에 게 네트워크를 닫도록 함 office 위치도 사용 하면 향후에도 Microsoft는 네트워크의 현재 상태와 Office 365 서비스 전면 도어를 모두 확장 하는 동시에 성능을 향상 시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="038c1-116">Having close network egress to users office locations also allows for improved performance in the future as Microsoft expands both network points of presence and Office 365 service front doors in the future.</span></span>

<span data-ttu-id="038c1-117">이 통찰력은 일부 요약 보기에서 "Egress"로 간략 한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="038c1-117">This insight is abbreviated as "Egress" in some summary views.</span></span>

## <a name="better-performance-detected-for-customers-near-you"></a><span data-ttu-id="038c1-118">주변 고객에 게 더 나은 성능 검색</span><span class="sxs-lookup"><span data-stu-id="038c1-118">Better performance detected for customers near you</span></span>

<span data-ttu-id="038c1-119">Metro 영역에 있는 많은 고객의 경우에는이 사무실 위치에서 조직의 사용자 보다 더 나은 성능을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="038c1-119">Since a significant number of customers in your metro area have better performance than users in your organization at this office location.</span></span>

<span data-ttu-id="038c1-120">이는이 사무실 위치와 같은 도시에 있는 Office 365 고객의 집계 성과를 조사 합니다.</span><span class="sxs-lookup"><span data-stu-id="038c1-120">This looks at the aggregate performance of Office 365 customers in the same city as this office location.</span></span>

![상대적 네트워크 성능](Media/m365-mac-perf/m365-mac-perf-relative-perf.png)

<span data-ttu-id="038c1-122">더 나은 성능 버킷으로 동일한 도시의 Office 365 고객 비율을 계산 합니다.</span><span class="sxs-lookup"><span data-stu-id="038c1-122">We calculate the percentage of Office 365 customers in the same city in better performance buckets.</span></span> <span data-ttu-id="038c1-123">이 수가 10% 보다 많은 경우 네트워크 통찰력을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="038c1-123">If this number if 10% of more then we show the network insight.</span></span>

<span data-ttu-id="038c1-124">이 통찰력은 일부 요약 보기에서 "피어"로 간략 한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="038c1-124">This insight is abbreviated as "Peers" in some summary views.</span></span>

## <a name="use-of-a-non-optimal-exchange-online-service-front-door"></a><span data-ttu-id="038c1-125">최적이 아닌 Exchange Online 서비스 전면 도어 사용</span><span class="sxs-lookup"><span data-stu-id="038c1-125">Use of a non-optimal Exchange Online service front door</span></span>

<span data-ttu-id="038c1-126">사용자가 최적의 Office 365 서비스 전면 도어에 연결 하지 않고 성능에 영향을 주는 것으로 예상 됩니다.</span><span class="sxs-lookup"><span data-stu-id="038c1-126">The user is not connecting to an optimal Office 365 service front door and this is expected to be impacting performance.</span></span>

<span data-ttu-id="038c1-127">적절 한 성능을 제공 하는 office 위치 도시에서 사용 하기에 적합 한 Exchange Online 서비스 프런트 도어를 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="038c1-127">We list Exchange Online service front doors which are suitable for use from the office location city with good performance.</span></span> <span data-ttu-id="038c1-128">현재 테스트에서이 목록에 없는 Exchange Online 서비스 앞 도어를 사용 하는 경우에는이 권장 사항을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="038c1-128">If the current test shows use of an Exchange Online service front door not on this list, then we call out this recommendation.</span></span>

<span data-ttu-id="038c1-129">Exchange Online 서비스 프런트 도어를 사용 하는 경우에는 회사 네트워크 egress가 되기 전에 로컬 및 직접 네트워크 송신을 권장 하는 네트워크 교환이 발생 하는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="038c1-129">Use of a non-optimal Exchange Online service front door could be caused by network backhaul before the corporate network egress in which case we recommend local and direct network egress.</span></span> <span data-ttu-id="038c1-130">또한 원격 DNS 재귀 해결 프로그램 서버를 사용 하는 경우에도 DNS 재귀 해결 프로그램 서버를 네트워크 egress에 정렬 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="038c1-130">It could also be caused by use of a remote DNS Recursive Resolver server in which case we recommend aligning the DNS Recursive Resolver server with the network egress.</span></span>

<span data-ttu-id="038c1-131">이에 대 한 자세한 정보는 요약 보기의 "라우팅" 이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="038c1-131">This insight is abbreviated as "Routing" in some summary views.</span></span>

## <a name="use-of-non-optimal-sharepoint-online-service-front-door"></a><span data-ttu-id="038c1-132">최적이 아닌 SharePoint Online 서비스 전면 도어 사용</span><span class="sxs-lookup"><span data-stu-id="038c1-132">Use of non-optimal SharePoint Online service front door</span></span>

<span data-ttu-id="038c1-133">사용자가 가장 가까운 SharePoint Online 서비스 앞 도어에 연결 되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="038c1-133">The user is not connecting to the closest SharePoint Online service front door.</span></span> <span data-ttu-id="038c1-134">이는 성능에 영향을 기대할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="038c1-134">This is expected to be impacting performance.</span></span>

<span data-ttu-id="038c1-135">테스트 클라이언트가 연결 되는 SharePoint Online 서비스 프런트 도어를 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="038c1-135">We identify the SharePoint Online service front door that the test client is connecting to.</span></span> <span data-ttu-id="038c1-136">그런 다음 office 위치 도시에서 해당 도시의 예상 SharePoint Online 서비스 전면 도어를 비교 합니다.</span><span class="sxs-lookup"><span data-stu-id="038c1-136">Then for the office location city we compare that to the expected SharePoint Online service front door for that city.</span></span> <span data-ttu-id="038c1-137">일치 하지 않는 경우이 권장 사항을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="038c1-137">If it doesn't match, then we make this recommendation.</span></span>

<span data-ttu-id="038c1-138">이 통찰력은 일부 요약 보기에서 "Afd"로 간략 한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="038c1-138">This insight is abbreviated as "Afd" in some summary views.</span></span>

## <a name="low-download-speed-from-sharepoint-front-door"></a><span data-ttu-id="038c1-139">SharePoint 전면 도어에서 다운로드 속도 낮음</span><span class="sxs-lookup"><span data-stu-id="038c1-139">Low download speed from SharePoint front door</span></span>

<span data-ttu-id="038c1-140">비즈니스용 OneDrive에서 문서를 로드 하는 데 걸리는 시간에 영향을 주는 하위 최적 네트워크 다운로드 속도를 감지 합니다.</span><span class="sxs-lookup"><span data-stu-id="038c1-140">Sub optimal network download speed detected which impacts how long it takes to load documents from OneDrive for Business.</span></span>

<span data-ttu-id="038c1-141">사용자가 SharePoint Online에서 가져올 수 있는 다운로드 속도 및 비즈니스용 OneDrive 서비스의 프런트 도어는 초당 메가바이트 (MBps)로 측정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="038c1-141">The download speed that a user can get from SharePoint Online and OneDrive for Business service front doors is measured in megabytes per second (MBps).</span></span> <span data-ttu-id="038c1-142">이 값이 1 MBps 보다 작으면 이러한 통찰력을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="038c1-142">If this value is less than 1 MBps then we provide this insight.</span></span>

<span data-ttu-id="038c1-143">사용자가 대역폭을 가져올 수 있는 다운로드 속도를 개선 하려면 다음을 수행 해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="038c1-143">To improve download speed that a user can get bandwidth may need to be increased.</span></span> <span data-ttu-id="038c1-144">또는 사무실 위치에 있는 사용자 컴퓨터와 SharePoint Online 서비스 전면 도어의 네트워크 정체가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="038c1-144">Alternatively, there may be network congestion between user machines at the office location and the SharePoint Online service front door.</span></span> <span data-ttu-id="038c1-145">이를 congestive 손실 이라고 하는 경우도 있으며 충분 한 대역폭을 사용할 수 있는 경우에도 사용자가 사용할 수 있는 다운로드 속도를 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="038c1-145">This is sometimes called congestive loss and it restricts the download speed available to users even if sufficient bandwidth is available.</span></span>

<span data-ttu-id="038c1-146">이 통찰력은 일부 요약 보기에서 "처리량"으로 간략하게 정리 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="038c1-146">This insight is abbreviated as "Throughput" in some summary views.</span></span>

## <a name="related-topics"></a><span data-ttu-id="038c1-147">관련 항목</span><span class="sxs-lookup"><span data-stu-id="038c1-147">Related topics</span></span>

[<span data-ttu-id="038c1-148">Microsoft 365 관리 센터의 네트워크 성능 권장 사항 (미리 보기)</span><span class="sxs-lookup"><span data-stu-id="038c1-148">Network performance recommendations in the Microsoft 365 Admin Center (preview)</span></span>](office-365-network-mac-perf-overview.md)

[<span data-ttu-id="038c1-149">Office 365 네트워크 평가 (미리 보기)</span><span class="sxs-lookup"><span data-stu-id="038c1-149">Office 365 network assessment (preview)</span></span>](office-365-network-mac-perf-score.md)

[<span data-ttu-id="038c1-150">M365 관리 센터의 Office 365 네트워크 온 보 딩 도구 (미리 보기)</span><span class="sxs-lookup"><span data-stu-id="038c1-150">Office 365 Network Onboarding Tool in the M365 Admin Center (preview)</span></span>](office-365-network-mac-perf-onboarding-tool.md)
