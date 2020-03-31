---
title: 중국 사용자에 대 한 Office 365 전역 테 넌 트 성능 최적화
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 2/13/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- remotework
search.appverid: MET150
f1.keywords:
- NOCSH
description: 이 문서에서는 글로벌 Office 365 테 넌 트의 중국 사용자에 대 한 네트워크 성능을 최적화 하기 위한 지침을 제공 합니다.
ms.openlocfilehash: 50cf6189c922ada5d4ebb9683bec0dd8c6e38f6d
ms.sourcegitcommit: cb942f32da99eda6455756ce0fd409cf8ee9de3e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/30/2020
ms.locfileid: "43058971"
---
# <a name="office-365-global-tenant-performance-optimization-for-china-users"></a><span data-ttu-id="f6574-103">중국 사용자에 대 한 Office 365 전역 테 넌 트 성능 최적화</span><span class="sxs-lookup"><span data-stu-id="f6574-103">Office 365 global tenant performance optimization for China users</span></span>

>[!IMPORTANT]
><span data-ttu-id="f6574-104">이 지침은 **중국에 있는 Enterprise office 365 사용자가** **글로벌 Office 365 테 넌 트**에 연결 하는 사용 시나리오에만 해당 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6574-104">This guidance is specific to usage scenarios in which **enterprise Office 365 users located in China** connect to a **global Office 365 tenant**.</span></span> <span data-ttu-id="f6574-105">이 지침은 21Vianet에서 운영 하는 Office 365의 테 넌 트에는 적용 **되지** 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f6574-105">This guidance does **not** apply to tenants in Office 365 operated by 21Vianet.</span></span>

<span data-ttu-id="f6574-106">중국에서 글로벌 Office 365 테 넌 트 및 회사 현재 상태인 기업에 게 중국 기반 사용자에 대 한 Office 365 클라이언트 성능은 중국 Telco의 인터넷 아키텍처에 고유한 요인에 따라 복잡할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6574-106">For enterprises with global Office 365 tenants and a corporate presence in China, Office 365 client performance for China-based users can be complicated by factors unique to China Telco's Internet architecture.</span></span>

<span data-ttu-id="f6574-107">중국 Isp는 전체적인 경계 네트워크 혼잡에 취약 한 경계 장치를 통과 하는 글로벌 공용 인터넷에 대 한 offshore 연결을 규정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6574-107">China ISPs have regulated offshore connections to the global public Internet that go through perimeter devices which are prone to high-levels of cross-border network congestion.</span></span> <span data-ttu-id="f6574-108">이 혼잡은 중국 들어오고 나가는 모든 인터넷 트래픽에 대 한 패킷 손실 및 대기 시간을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f6574-108">This congestion creates packet loss and latency for all Internet traffic going into and out of China.</span></span>

![Office 365 트래픽-최적화 되지 않음](media/O365-networking/China-O365-unoptimized.png)

<span data-ttu-id="f6574-110">패킷 손실 및 대기 시간은 네트워크 서비스 (특히 대용량 파일 전송)가 필요 하거나 실시간 고성능 (오디오 및 비디오 응용 프로그램)을 필요로 하는 대규모 데이터 교환이 필요한 서비스의 성능에 부정적인 영향을 주는 일입니다.</span><span class="sxs-lookup"><span data-stu-id="f6574-110">Packet loss and latency is detrimental to the performance of network services, especially services that require large data exchanges (such as large file transfers) or requiring near real-time performance (audio and video applications).</span></span>

<span data-ttu-id="f6574-111">이 항목의 목표는 Office 365 서비스에서 중국 테두리 간 네트워크 혼잡의 영향을 완화 하기 위한 모범 사례를 제공 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6574-111">The goal of this topic is to provide best practices for mitigating the impact of China cross-border network congestion on Office 365 services.</span></span> <span data-ttu-id="f6574-112">이 항목에서는 중국 캐리어 내의 복잡 한 라우팅으로 인 한 높은 패킷 대기 시간 문제와 같은 다른 일반적인 지난 마일 성능 문제를 해결 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f6574-112">This topic does not address other common last-mile performance issues such as issues of high packet latency due to complex routing within China carriers.</span></span>

## <a name="corporate-network-best-practices"></a><span data-ttu-id="f6574-113">회사 네트워크 모범 사례</span><span class="sxs-lookup"><span data-stu-id="f6574-113">Corporate network best practices</span></span>

<span data-ttu-id="f6574-114">글로벌 Office 365 테 넌 트 및 중국의 사용자가 포함 된 대부분의 기업에서는 중국 사무실 위치와 전 세계 offshore 위치 간에 회사 네트워크 트래픽을 전송 하는 개인 네트워크를 구현 했습니다.</span><span class="sxs-lookup"><span data-stu-id="f6574-114">Many enterprises with global Office 365 tenants and users in China have implemented private networks that carry corporate network traffic between China office locations and offshore locations around the world.</span></span> <span data-ttu-id="f6574-115">이러한 기업은 이러한 기업에서 중국의 네트워크 혼잡을 방지 하 고 Office 365 서비스 성능을 최적화 하기 위해이 네트워크 인프라를 활용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6574-115">These enterprises can leverage this network infrastructure to avoid cross-border network congestion and optimize their Office 365 service performance in China.</span></span>

>[!IMPORTANT]
><span data-ttu-id="f6574-116">모든 사설 WAN 구현과 마찬가지로, 사용자의 국가 및/또는 지역에 대 한 규정 요구 사항을 항상 확인 하 여 네트워크 구성이 준수 되도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6574-116">As with all private WAN implementations, you should always consult regulatory requirements for your country and/or region to ensure that your network configuration is in compliance.</span></span>

<span data-ttu-id="f6574-117">첫 번째 단계에서는 [Office 365의 네트워크 계획 및 성능 조정](https://aka.ms/tune)에서 벤치 마크 네트워크 지침을 따르는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6574-117">As a first step, it is crucial that you follow our benchmark network guidance at [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span> <span data-ttu-id="f6574-118">기본 목표는 가능한 경우 중국의 인터넷에서 글로벌 Office 365 서비스에 액세스 하지 않도록 하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f6574-118">The primary goal should be to avoid accessing global Office 365 services from the Internet in China if possible.</span></span>

- <span data-ttu-id="f6574-119">기존 개인 네트워크를 활용 하 여 중국 사무실 네트워크와 중국 외부의 공용 인터넷에서 전송 되는 offshore 위치 간의 Office 365 네트워크 트래픽을 운반 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6574-119">Leverage your existing private network to carry Office 365 network traffic between China office networks and offshore locations that egress on the public Internet outside China.</span></span> <span data-ttu-id="f6574-120">중국 외부에 있는 거의 모든 위치에서 분명 한 이점이 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6574-120">Almost any location outside China will provide a clear benefit.</span></span> <span data-ttu-id="f6574-121">네트워크 관리자는 [Microsoft 글로벌 네트워크](https://docs.microsoft.com/azure/networking/microsoft-global-network)와의 대기 시간이 낮은 상호 연결을 사용 하는 영역에서 더 최적화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6574-121">Network administrators can further optimize by egressing in areas with low-latency interconnect with the [Microsoft global network](https://docs.microsoft.com/azure/networking/microsoft-global-network).</span></span> <span data-ttu-id="f6574-122">예를 들어, 홍콩, 일본, 대한민국을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6574-122">Hong Kong, Japan, and South Korea are examples.</span></span>
- <span data-ttu-id="f6574-123">VPN 연결을 통해 회사 네트워크에 액세스 하도록 사용자 장치를 구성 하 여 Office 365 트래픽이 회사 네트워크의 개인 offshore 링크를 통과 하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6574-123">Configure user devices to access the corporate network over a VPN connection to allow Office 365 traffic to transit the corporate network's private offshore link.</span></span> <span data-ttu-id="f6574-124">VPN 클라이언트가 분할 터널링을 사용 하도록 구성 되지 않았는지 또는 사용자 장치가 Office 365 트래픽의 분할 터널링을 무시 하도록 구성 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6574-124">Ensure that VPN clients are either not configured to use split tunneling, or that user devices are configured to ignore split tunneling for Office 365 traffic.</span></span>
- <span data-ttu-id="f6574-125">개인 offshore 링크를 통해 모든 Office 365 트래픽을 라우팅하도록 네트워크를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6574-125">Configure your network to route all Office 365 traffic across your private offshore link.</span></span> <span data-ttu-id="f6574-126">개인 링크에 대 한 트래픽 양을 최소화 해야 하는 경우에는 **최적화** 범주에서 끝점만 경로를 설정 하 고 요청을 **허용** **하 고 끝점에서** 인터넷을 전송할 수 있도록 허용 하도록 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6574-126">If you must minimize the volume of traffic on your private link, you can choose to only route endpoints in the **Optimize** category, and allow requests to **Allow** and **Default** endpoints to transit the Internet.</span></span> <span data-ttu-id="f6574-127">이렇게 하면 높은 대기 시간 및 패킷 손실을 가장 많이 받는 중요 한 서비스에 최적화 된 트래픽을 제한 하 여 성능을 개선 하 고 대역폭 소비를 최소화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6574-127">This will improve performance and minimize bandwidth consumption by limiting optimized traffic to critical services that are most sensitive to high latency and packet loss.</span></span>
- <span data-ttu-id="f6574-128">가능한 경우 TCP 대신, 라이브 미디어 스트리밍 트래픽 (예: 팀)에 대해 UDP를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6574-128">If possible, use UDP instead of TCP for live media streaming traffic, such as for Teams.</span></span> <span data-ttu-id="f6574-129">UDP는 TCP 보다 더 나은 라이브 미디어 스트리밍 성능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6574-129">UDP offers better live media streaming performance than TCP.</span></span>

<span data-ttu-id="f6574-130">Office 365 트래픽을 선택적으로 라우팅하는 방법에 대 한 자세한 내용은 [office 365 끝점 관리](managing-office-365-endpoints.md)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="f6574-130">For information about how to selectively route Office 365 traffic, see [Managing Office 365 endpoints](managing-office-365-endpoints.md).</span></span> <span data-ttu-id="f6574-131">모든 국가별 Office 365 Url 및 IP 주소 목록은 [Office 365 url 및 ip 주소 범위](urls-and-ip-address-ranges.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f6574-131">For a list of all worldwide Office 365 URLs and IP addresses, see [Office 365 URLs and IP address ranges](urls-and-ip-address-ranges.md).</span></span>

![Office 365 트래픽 최적화 됨](media/O365-networking/China-O365-optimized.png)

## <a name="user-best-practices"></a><span data-ttu-id="f6574-133">사용자 모범 사례</span><span class="sxs-lookup"><span data-stu-id="f6574-133">User best practices</span></span>

<span data-ttu-id="f6574-134">집, 커피숍, 호텔 및 회사 네트워크에 연결 되어 있지 않은 지사의 원격 위치에서 글로벌 Office 365 테 넌 트에 연결 하는 중국의 사용자는 장치와 사무실 간의 트래픽 때문에 네트워크 성능이 저하 될 수 있습니다. 365는 중국의 혼잡 한 경계 네트워크 회로를 통과 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6574-134">Users in China who connect to global Office 365 tenants from remote locations such as homes, coffee shops, hotels and branch offices with no connection to enterprise networks can experience poor network performance because traffic between their devices and Office 365 must transit China's congested cross-border network circuits.</span></span>

<span data-ttu-id="f6574-135">회사 네트워크에 대 한 경계 간 개인 네트워크 및/또는 VPN 액세스가 옵션이 아닌 경우에는 이러한 모범 사례를 따르기 위해 중국 기반 사용자에 게 교육 하 여 사용자별 성능 문제를 완화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6574-135">If cross-border private networks and/or VPN access into the corporate network are not an option, per-user performance issues can still be mitigated by training your China-based users to follow these best practices.</span></span>

- <span data-ttu-id="f6574-136">캐싱을 지 원하는 리치 Office 클라이언트 (예: Outlook, 팀, OneDrive 등)를 활용 하 고 웹 기반 클라이언트를 사용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f6574-136">Utilize rich Office clients that support caching (e.g. Outlook, Teams, OneDrive, etc.), and avoid web-based clients.</span></span> <span data-ttu-id="f6574-137">Office 클라이언트 캐싱 및 오프 라인 액세스 기능을 사용 하면 네트워크 혼잡 및 대기 시간에 대 한 영향을 크게 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6574-137">Office client caching and offline access features can dramatically reduce the impact of network congestion and latency.</span></span>
- <span data-ttu-id="f6574-138">_오디오 회의_ 기능을 사용 하 여 Office 365 테 넌 트를 구성한 경우 팀 사용자는 PSTN (공중 전화망)을 통해 모임에 참가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6574-138">If your Office 365 tenant has been configured with the _Audio Conferencing_ feature, Teams users can join meetings via the public switched telephone network (PSTN).</span></span> <span data-ttu-id="f6574-139">자세한 내용은 [Office 365의 오디오 회의](https://docs.microsoft.com/microsoftteams/audio-conferencing-in-office-365)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f6574-139">For more information, see [Audio Conferencing in Office 365](https://docs.microsoft.com/microsoftteams/audio-conferencing-in-office-365).</span></span>
- <span data-ttu-id="f6574-140">사용자에 게 네트워크 성능 문제가 발생 하면 문제 해결을 위해 IT 부서에 보고 하 고 Office 365 서비스에 문제가 있는 것으로 의심 되는 경우 Microsoft 기술 지원부에 문의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6574-140">If users experience network performance issues, they should report to their IT department for troubleshooting, and escalate to Microsoft support if trouble with Office 365 services is suspected.</span></span> <span data-ttu-id="f6574-141">일부 문제가 교차 테두리 네트워크 성능으로 인해 발생 하는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="f6574-141">Not all issues are caused by cross-border network performance.</span></span>

<span data-ttu-id="f6574-142">Microsoft는 광범위 한 네트워크 아키텍처 및 특성 범위에서 Office 365 사용자 환경 및 클라이언트 성능 향상을 위해 지속적으로 작동 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6574-142">Microsoft is continually working to improve the Office 365 user experience and the performance of clients over the widest possible range of network architectures and characteristics.</span></span> <span data-ttu-id="f6574-143">[Office 365 기술 커뮤니티](https://techcommunity.microsoft.com/t5/office-365/bd-p/Office365General) 를 방문 하 여 대화를 시작 하거나 참여 하 고, 리소스를 찾고, 기능 요청 및 제안을 제출 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6574-143">Visit the [Office 365 Tech Community](https://techcommunity.microsoft.com/t5/office-365/bd-p/Office365General) to start or join a conversation, find resources, and submit feature requests and suggestions.</span></span>

## <a name="related-topics"></a><span data-ttu-id="f6574-144">관련 항목</span><span class="sxs-lookup"><span data-stu-id="f6574-144">Related topics</span></span>

[<span data-ttu-id="f6574-145">Office 365의 네트워크 계획 및 성능 조정</span><span class="sxs-lookup"><span data-stu-id="f6574-145">Network planning and performance tuning for Office 365</span></span>](https://aka.ms/tune)

[<span data-ttu-id="f6574-146">Office 365 네트워크 연결 원칙</span><span class="sxs-lookup"><span data-stu-id="f6574-146">Office 365 network connectivity principles</span></span>](office-365-network-connectivity-principles.md)

[<span data-ttu-id="f6574-147">Office 365 끝점 관리</span><span class="sxs-lookup"><span data-stu-id="f6574-147">Managing Office 365 endpoints</span></span>](managing-office-365-endpoints.md)

[<span data-ttu-id="f6574-148">Office 365 URL 및 IP 주소 범위</span><span class="sxs-lookup"><span data-stu-id="f6574-148">Office 365 URLs and IP address ranges</span></span>](urls-and-ip-address-ranges.md)

[<span data-ttu-id="f6574-149">Microsoft 글로벌 네트워크</span><span class="sxs-lookup"><span data-stu-id="f6574-149">Microsoft global network</span></span>](https://docs.microsoft.com/azure/networking/microsoft-global-network)
