---
title: Microsoft 365 네트워크 평가 (미리 보기)
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 03/31/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Microsoft 365 네트워크 평가 (미리 보기)
ms.openlocfilehash: 2ee18f50e841982e8f677964d2e7e57d95a209d8
ms.sourcegitcommit: 6508db0a839427e1a21b1cde883d828e3c8886c6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "43185749"
---
# <a name="microsoft-365-network-assessment-preview"></a><span data-ttu-id="e0c2d-103">Microsoft 365 네트워크 평가 (미리 보기)</span><span class="sxs-lookup"><span data-stu-id="e0c2d-103">Microsoft 365 network assessment (preview)</span></span>

<span data-ttu-id="e0c2d-104">Microsoft 365 관리 센터의 Microsoft 365 페이지 연결에서 **네트워크 평가** 는 많은 네트워크 성능 메트릭 집계를 1-100의 포인트 값으로 표시 되는 엔터프라이즈 네트워크 상태의 스냅숏으로 정제 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0c2d-104">In the Microsoft 365 Admin Center's Connectivity to Microsoft 365 page, **network assessments** distill an aggregate of many network performance metrics into a snapshot of your enterprise network health, represented by a points value from 1 - 100.</span></span> <span data-ttu-id="e0c2d-105">네트워크 평가는 전체 테 넌 트와 사용자가 테 넌 트에 연결 하는 각 지리적 위치에 대해 범위가 지정 되므로 Microsoft 365 관리자는 회사의 네트워크 상태를 신속 하 게 파악 하 고 전체 사무실 위치에 대 한 자세한 보고서로 드릴 다운할 수 있는 쉬운 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0c2d-105">Network assessments are scoped to both the entire tenant and for each geographic location from which users connect to your tenant, providing Microsoft 365 administrators with an easy way to instantly grasp a gestalt of the enterprise's network health and quickly drill down into a detailed report for any global office location.</span></span>

<span data-ttu-id="e0c2d-106">Network 평가 점수 값은 표시 되는 시간에 실시간으로 컴파일된 대기 시간, 대역폭, 다운로드 속도 및 연결 품질 메트릭에 대 한 평균 측정 단위입니다.</span><span class="sxs-lookup"><span data-stu-id="e0c2d-106">The network assessment points value is an average measurement of latency, bandwidth, download speed and connection quality metrics compiled live at the time they are viewed.</span></span> <span data-ttu-id="e0c2d-107">Microsoft 소유의 네트워크에 대 한 성능 메트릭은 평가 결과가 모호 하 고 회사 네트워크에 한정 되도록 하기 위해 이러한 측정값에서 제외 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0c2d-107">Performance metrics for Microsoft-owned networks are excluded from these measurements to ensure that assessment results are unambiguous and specific to the corporate network.</span></span>

![네트워크 평가 값](Media/m365-mac-perf/m365-mac-perf-overview-score-top.png)

<span data-ttu-id="e0c2d-109">아주 낮은 네트워크 평가 값은 Microsoft 365 클라이언트에 테 넌 트에 연결 하는 중요 한 문제가 있거나 응답성이 뛰어난 사용자 환경을 유지 관리 하는 반면, 값이 높으면 성능 문제가 거의 없는 네트워크를 올바르게 구성한 것을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0c2d-109">A very low network assessment value suggests that Microsoft 365 clients will have significant problems connecting to the tenant or maintaining a responsive user experience, while a high value indicates a properly configured network with few ongoing performance issues.</span></span> <span data-ttu-id="e0c2d-110">값이 80%는 네트워크 성능으로 인 한 Microsoft 365 연결 또는 응답성에 대 한 일반 사용자 불만을 수신 하지 않을 것으로 예상 되는 정상적인 기준을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e0c2d-110">A value of 80% represents a healthy baseline where you should not expect to receive regular user complaints about Microsoft 365 connectivity or responsiveness due to network performance.</span></span> <span data-ttu-id="e0c2d-111">반복적으로 네트워크 연결이 개선 됨에 따라이 값은 사용자 환경에 따라 증가 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0c2d-111">As iterative network connectivity improvements are made, this value will increase along with user experience.</span></span>

>[!IMPORTANT]
><span data-ttu-id="e0c2d-112">네트워크 insights, Microsoft 365 관리 센터의 성능 권장 사항 및 평가는 현재 미리 보기 상태 이며, 기능 미리 보기 프로그램에 등록 되어 있는 Microsoft 365 테 넌 트에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0c2d-112">Network insights, performance recommendations and assessments in the Microsoft 365 Admin Center is currently in preview status, and is only available for Microsoft 365 tenants that have been enrolled in the feature preview program.</span></span>

## <a name="network-assessment-panel"></a><span data-ttu-id="e0c2d-113">네트워크 평가 패널</span><span class="sxs-lookup"><span data-stu-id="e0c2d-113">Network assessment panel</span></span>

<span data-ttu-id="e0c2d-114">테 넌 트 또는 특정 사무실 위치로 범위가 지정 되었는지 여부에 관계 없이 각 네트워크 평가에는 평가에 대 한 세부 정보가 포함 된 패널이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0c2d-114">Each network assessment, whether scoped to the tenant or to a specific office location, shows a panel with details about the assessment.</span></span> <span data-ttu-id="e0c2d-115">이 패널에는 평가에 대 한 가로 막대형 차트와 측정 데이터를 받은 작업을 포함 하는 각 구성 요소 작업의 총 지점에 대 한 완료율이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0c2d-115">This panel shows a bar chart of the assessment both as a percentage and as the total points for each component workload including only workloads where measurement data was received.</span></span> <span data-ttu-id="e0c2d-116">Office 위치 네트워크 평가의 경우 office 위치와 같은 도시의 데이터를 보고 한 모든 Microsoft 365 클라이언트의 중앙값을 나타내는 벤치 마크가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0c2d-116">For an office location network assessment, we also show a benchmark which is the median of all Microsoft 365 clients that reported data in the same city as your office location.</span></span>

![네트워크 평가 값 예](Media/m365-mac-perf/m365-mac-perf-overview-score.png)

<span data-ttu-id="e0c2d-118">패널의 **평가 분석** 에서는 각 구성 요소 작업에 대 한 평가를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e0c2d-118">The **Assessment breakdown** in the panel shows the assessment for each of the component workloads.</span></span>

<span data-ttu-id="e0c2d-119">**평가 기록** 에는 평가 및 벤치 마크의 최근 30 일이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0c2d-119">The **Assessment history** shows the past 30 days of the assessment and the benchmark.</span></span>

## <a name="tenant-network-assessments-and-office-location-network-assessments"></a><span data-ttu-id="e0c2d-120">테 넌 트 네트워크 평가 및 사무실 위치 네트워크 평가</span><span class="sxs-lookup"><span data-stu-id="e0c2d-120">Tenant network assessments and office location network assessments</span></span>

<span data-ttu-id="e0c2d-121">네트워크 평가는 사무실의 네트워크 경계를 Microsoft 네트워크로의 디자인을 측정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0c2d-121">A network assessment measures the design of the network perimeter of an office location to Microsoft's network.</span></span> <span data-ttu-id="e0c2d-122">네트워크 경계에 대 한 향상은 각 사무실 위치에서 또는 네트워크 연결이 집계 되는 위치에 있어 여러 위치에 영향을 주는 향상 된 기능을 제공 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="e0c2d-122">Improvements to the network perimeter is best done at each office location, or where network connectivity is aggregated there may be improvements that impact multiple locations.</span></span>

<span data-ttu-id="e0c2d-123">네트워크 성능 개요 페이지에는 전체 Microsoft 365 테 넌 트에 대 한 네트워크 평가 값과 해당 위치의 요약 페이지에 있는 검색 된 각 사무실 위치에 대 한 특정 값이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0c2d-123">We show a network assessment value for the whole Microsoft 365 tenant on the network performance overview page and a specific value for each detected office location on that location's summary page.</span></span>

## <a name="exchange-online"></a><span data-ttu-id="e0c2d-124">Exchange Online</span><span class="sxs-lookup"><span data-stu-id="e0c2d-124">Exchange Online</span></span>

<span data-ttu-id="e0c2d-125">Exchange Online의 경우 클라이언트 컴퓨터에서 Exchange 프런트 엔드 서버로의 TCP 대기 시간이 측정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0c2d-125">For Exchange Online the TCP latency from the client machine to the Exchange front end server is measured.</span></span> <span data-ttu-id="e0c2d-126">이는 네트워크가 고객 LAN 및 WAN을 통과 하는 거리에 영향을 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0c2d-126">This can be impacted by the distance the network travels over the customers LAN and WAN.</span></span> <span data-ttu-id="e0c2d-127">또한 연결을 지연 시키거나 패킷을 다시 전송 하도록 하는 네트워크 매개 장치 또는 서비스의 영향을 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0c2d-127">It can also be impacted by network intermediary devices or services which delay the connectivity or cause packets to be resent.</span></span>

## <a name="sharepoint-online"></a><span data-ttu-id="e0c2d-128">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="e0c2d-128">SharePoint Online</span></span>

<span data-ttu-id="e0c2d-129">SharePoint Online의 경우 사용자가 문서에 액세스 하는 데 사용할 수 있는 다운로드 속도가 측정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0c2d-129">For SharePoint Online the download speed available for a user to access a document is measured.</span></span> <span data-ttu-id="e0c2d-130">이는 클라이언트 컴퓨터와 Microsoft 네트워크 간의 네트워크 회로에서 사용 가능한 대역폭의 영향을 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0c2d-130">This can be impacted by the bandwidth available on network circuits between the client machine and Microsoft's network.</span></span> <span data-ttu-id="e0c2d-131">또한 복잡 한 네트워크 장치에서 병목 현상이 발생 한 네트워크 혼잡 이나 적절 하지 않은 서비스 범위에 있는 경우에도 영향을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="e0c2d-131">It is also often impacted by network congestion that exists in bottlenecks in complex network devices or in poor coverage Wi-Fi areas.</span></span>

## <a name="microsoft-teams"></a><span data-ttu-id="e0c2d-132">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="e0c2d-132">Microsoft Teams</span></span>

<span data-ttu-id="e0c2d-133">Microsoft 팀의 경우 네트워크 품질은 UDP 대기 시간, UDP 지터 및 UDP 패킷 손실으로 측정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0c2d-133">For Microsoft Teams the Network quality is measured as UDP latency, UDP jitter, and UDP packet loss.</span></span> <span data-ttu-id="e0c2d-134">UDP는 Microsoft 팀의 통화 및 회의 오디오 및 비디오 미디어 연결에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0c2d-134">UDP is used for call and conferencing audio and video media connectivity for Microsoft Teams.</span></span> <span data-ttu-id="e0c2d-135">이는 UDP가 보다 일반적인 TCP 프로토콜과 별도로 구성 되므로 네트워크의 UDP 지원에서의 연결 간격 외에도 대기 시간 및 다운로드 속도와 동일한 요인의 영향을 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0c2d-135">This can be impacted by the same factors as for latency and download speed in addition to connectivity gaps in a network's UDP support since UDP is configured separately to the more common TCP protocol.</span></span>

## <a name="related-topics"></a><span data-ttu-id="e0c2d-136">관련 항목</span><span class="sxs-lookup"><span data-stu-id="e0c2d-136">Related topics</span></span>

[<span data-ttu-id="e0c2d-137">Microsoft 365 관리 센터의 네트워크 성능 권장 사항 (미리 보기)</span><span class="sxs-lookup"><span data-stu-id="e0c2d-137">Network performance recommendations in the Microsoft 365 Admin Center (preview)</span></span>](office-365-network-mac-perf-overview.md)

[<span data-ttu-id="e0c2d-138">Microsoft 365 network performance insights (preview)</span><span class="sxs-lookup"><span data-stu-id="e0c2d-138">Microsoft 365 network performance insights (preview)</span></span>](office-365-network-mac-perf-insights.md)

[<span data-ttu-id="e0c2d-139">M365 관리 센터의 Microsoft 365 네트워크 온 보 딩 도구 (미리 보기)</span><span class="sxs-lookup"><span data-stu-id="e0c2d-139">Microsoft 365 Network Onboarding Tool in the M365 Admin Center (preview)</span></span>](office-365-network-mac-perf-onboarding-tool.md)

[<span data-ttu-id="e0c2d-140">Microsoft 365 네트워크 연결 위치 서비스 (미리 보기)</span><span class="sxs-lookup"><span data-stu-id="e0c2d-140">Microsoft 365 Network Connectivity Location Services (preview)</span></span>](office-365-network-mac-location-services.md)
