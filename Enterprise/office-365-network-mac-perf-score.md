---
title: Office 365 네트워크 평가 (미리 보기)
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
description: Office 365 네트워크 평가 (미리 보기)
ms.openlocfilehash: f919eeb2771095502865b4a5079b91eb8d7efe36
ms.sourcegitcommit: e2f7bb4ccd4c74902235f680104ca6b56c051587
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/19/2020
ms.locfileid: "42106396"
---
# <a name="office-365-network-assessment-preview"></a><span data-ttu-id="9aad4-103">Office 365 네트워크 평가 (미리 보기)</span><span class="sxs-lookup"><span data-stu-id="9aad4-103">Office 365 network assessment (preview)</span></span>

<span data-ttu-id="9aad4-104">Office 365 네트워크 평가는 고객 네트워크 연결의 상대적인 사용자 환경에 미치는 영향을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9aad4-104">The Office 365 network assessment indicates the relative user experience impact from customer network connectivity.</span></span> <span data-ttu-id="9aad4-105">고객이 담당 하는 네트워크 디자인을 최적화할 수 있도록 Microsoft 소유의 네트워크 연결에 대 한 영향은 여기에서 제외 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9aad4-105">The impact of any Microsoft owned network connectivity is excluded from this to enable customers to optimize network designs for which they are responsible.</span></span>

<span data-ttu-id="9aad4-106">이는 주요 Office 365 작업의 사용자 환경에 영향을 주는 측정값으로 계산 되며 0에서 100 사이의 비율로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9aad4-106">It is calculated from measurements that impact user experience in key Office 365 workloads and shown as a percentage with a range of 0 to 100.</span></span>

<span data-ttu-id="9aad4-107">네트워크 점수가 낮으면 Office 365 클라이언트에서 연결 또는 남은 사용자의 응답에 심각한 문제가 있음을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="9aad4-107">A very low network score suggests that Office 365 clients will have significant problems connecting or remaining user responsive.</span></span> <span data-ttu-id="9aad4-108">점수가 80% 인 네트워크 연결이 네트워크 성능으로 인해 Office 365 사용자 환경에 대 한 사용자 불만을 수신 하지 않을 것으로 예상 합니다.</span><span class="sxs-lookup"><span data-stu-id="9aad4-108">A score of 80% represents network connectivity where you should not expect to receive user complaints about your Office 365 user experience due to your network performance.</span></span> <span data-ttu-id="9aad4-109">네트워크 연결이 개선 됨에 따라이 점수는 사용자 환경에 따라 증가 합니다.</span><span class="sxs-lookup"><span data-stu-id="9aad4-109">As network connectivity improvements are made, this score will increase along with user experience.</span></span>

>[!IMPORTANT]
><span data-ttu-id="9aad4-110">네트워크 성능 권장 사항, Microsoft 365 관리 센터의 통찰력 및 평가는 현재 미리 보기 상태 이며, 기능 미리 보기 프로그램에 등록 되어 있는 Office 365 테 넌 트에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9aad4-110">Network performance recommendations, insights and assessments in the Microsoft 365 Admin Center is currently in preview status, and is only available for Office 365 tenants that have been enrolled in the feature preview program.</span></span>

## <a name="exchange-online"></a><span data-ttu-id="9aad4-111">Exchange Online</span><span class="sxs-lookup"><span data-stu-id="9aad4-111">Exchange Online</span></span>

<span data-ttu-id="9aad4-112">Exchange Online의 경우 클라이언트 컴퓨터에서 Exchange 프런트 엔드 서버로의 TCP 대기 시간이 측정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9aad4-112">For Exchange Online the TCP latency from the client machine to the Exchange front end server is measured.</span></span> <span data-ttu-id="9aad4-113">이는 네트워크가 고객 LAN 및 WAN을 통과 하는 거리에 영향을 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9aad4-113">This can be impacted by the distance the network travels over the customers LAN and WAN.</span></span> <span data-ttu-id="9aad4-114">또한 연결을 지연 시키거나 패킷을 다시 전송 하도록 하는 네트워크 매개 장치 또는 서비스의 영향을 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9aad4-114">It can also be impacted by network intermediary devices or services which delay the connectivity or cause packets to be resent.</span></span>

## <a name="sharepoint-online"></a><span data-ttu-id="9aad4-115">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="9aad4-115">SharePoint Online</span></span>

<span data-ttu-id="9aad4-116">SharePoint Online의 경우 사용자가 문서에 액세스 하는 데 사용할 수 있는 다운로드 속도가 측정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9aad4-116">For SharePoint Online the download speed available for a user to access a document is measured.</span></span> <span data-ttu-id="9aad4-117">이는 클라이언트 컴퓨터와 Microsoft 네트워크 간의 네트워크 회로에서 사용 가능한 대역폭의 영향을 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9aad4-117">This can be impacted by the bandwidth available on network circuits between the client machine and Microsoft’s network.</span></span> <span data-ttu-id="9aad4-118">또한 복잡 한 네트워크 장치에서 병목 현상이 발생 한 네트워크 혼잡 이나 적절 하지 않은 서비스 범위에 있는 경우에도 영향을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="9aad4-118">It is also often impacted by network congestion that exists in bottlenecks in complex network devices or in poor coverage Wi-Fi areas.</span></span>

## <a name="microsoft-teams"></a><span data-ttu-id="9aad4-119">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="9aad4-119">Microsoft Teams</span></span>

<span data-ttu-id="9aad4-120">Microsoft 팀의 경우 네트워크 품질은 UDP 대기 시간, UDP 지터 및 UDP 패킷 손실으로 측정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9aad4-120">For Microsoft Teams the Network quality is measured as UDP latency, UDP jitter, and UDP packet loss.</span></span> <span data-ttu-id="9aad4-121">UDP는 Microsoft 팀의 통화 및 회의 오디오 및 비디오 미디어 연결에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9aad4-121">UDP is used for call and conferencing audio and video media connectivity for Microsoft Teams.</span></span> <span data-ttu-id="9aad4-122">이는 UDP가 보다 일반적인 TCP 프로토콜과 별도로 구성 되므로 네트워크의 UDP 지원에서의 연결 간격 외에도 대기 시간 및 다운로드 속도와 동일한 요인의 영향을 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9aad4-122">This can be impacted by the same factors as for latency and download speed in addition to connectivity gaps in a network’s UDP support since UDP is configured separately to the more common TCP protocol.</span></span>

## <a name="tenant-network-score-and-office-location-network-score"></a><span data-ttu-id="9aad4-123">테 넌 트 네트워크 점수 및 사무실 위치 네트워크 점수</span><span class="sxs-lookup"><span data-stu-id="9aad4-123">Tenant network score and office location network score</span></span>

<span data-ttu-id="9aad4-124">네트워크 점수는 office 위치의 네트워크 경계에 대 한 디자인을 Microsoft 네트워크로 측정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9aad4-124">A network score measures the design of the network perimeter of an office location to Microsoft’s network.</span></span> <span data-ttu-id="9aad4-125">네트워크 경계에 대 한 향상은 각 사무실 위치에서 또는 네트워크 연결이 집계 되는 위치에 있어 여러 위치에 영향을 주는 향상 된 기능을 제공 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9aad4-125">Improvements to the network perimeter is best done at each office location, or where network connectivity is aggregated there may be improvements that impact multiple locations.</span></span>
<span data-ttu-id="9aad4-126">네트워크 성능 개요 페이지에서 전체 Office 365 테 넌 트에 대 한 네트워크 점수를 표시 하 고 해당 위치에 대 한 요약 페이지에서 검색 된 각 사무실 위치에 대 한 특정 네트워크 점수를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9aad4-126">We show a network score for the whole Office 365 tenant on the network performance overview page and a specific network score for each detected office location on that location’s summary page.</span></span>

## <a name="network-score-panel"></a><span data-ttu-id="9aad4-127">네트워크 점수 패널</span><span class="sxs-lookup"><span data-stu-id="9aad4-127">Network score panel</span></span>

<span data-ttu-id="9aad4-128">각 네트워크는 테 넌 트 또는 특정 사무실 위치에 대해 점수가 점수에 대 한 세부 정보가 포함 된 패널을 표시할지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9aad4-128">Each network score whether for the tenant or for a specific office location shows a panel with details about the score.</span></span> <span data-ttu-id="9aad4-129">이 패널에는 점수의 가로 막대형 차트가 표시 되며, 측정 데이터를 받은 작업량을 비롯 하 여 각 구성 요소 작업의 총 점수를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9aad4-129">This panel shows a bar chart of the score both as a percentage and as the total points for each component workload including only workloads where measurement data was received.</span></span> <span data-ttu-id="9aad4-130">사무실 위치 네트워크 점수에는 사무실 위치와 같은 구/군/시 데이터를 보고 한 모든 Office 365 클라이언트의 중앙값을 나타내는 벤치 마크가 함께 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9aad4-130">For an office location network score we also show a benchmark which is the median of all Office 365 clients that reported data in the same City as your office location.</span></span>

<span data-ttu-id="9aad4-131">패널의 점수 분석 결과에는 각 구성 요소 작업의 점수가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9aad4-131">The score breakdown in the panel shows the score for each of the component workloads.</span></span>

<span data-ttu-id="9aad4-132">점수 기록에는 점수 및 벤치 마크의 이전 30 일이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9aad4-132">The score history shows the past 30 days of the score and the benchmark.</span></span>

## <a name="related-topics"></a><span data-ttu-id="9aad4-133">관련 항목</span><span class="sxs-lookup"><span data-stu-id="9aad4-133">Related topics</span></span>

[<span data-ttu-id="9aad4-134">Microsoft 365 관리 센터의 네트워크 성능 권장 사항 (미리 보기)</span><span class="sxs-lookup"><span data-stu-id="9aad4-134">Network performance recommendations in the Microsoft 365 Admin Center (preview)</span></span>](office-365-network-mac-perf-overview.md)

[<span data-ttu-id="9aad4-135">Office 365 network performance insights (미리 보기)</span><span class="sxs-lookup"><span data-stu-id="9aad4-135">Office 365 network performance insights (preview)</span></span>](office-365-network-mac-perf-insights.md)

[<span data-ttu-id="9aad4-136">M365 관리 센터의 Office 365 네트워크 온 보 딩 도구 (미리 보기)</span><span class="sxs-lookup"><span data-stu-id="9aad4-136">Office 365 Network Onboarding Tool in the M365 Admin Center (preview)</span></span>](office-365-network-mac-perf-onboarding-tool.md)
