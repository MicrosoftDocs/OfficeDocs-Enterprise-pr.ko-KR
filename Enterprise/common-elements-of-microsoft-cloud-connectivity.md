---
title: Microsoft 클라우드 연결의 공통 요소
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/28/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 061d4507-7360-4029-8f4b-3d4bc6b4ade0
description: '요약: 네트워킹 인프라의 공통 요소와 네트워크를 준비 하는 방법에 대해 설명 합니다.'
ms.openlocfilehash: e00ad8820ef37c818c270323cf2aa036bb86a804
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/30/2019
ms.locfileid: "33490202"
---
# <a name="common-elements-of-microsoft-cloud-connectivity"></a><span data-ttu-id="f2b35-103">Microsoft 클라우드 연결의 공통 요소</span><span class="sxs-lookup"><span data-stu-id="f2b35-103">Common elements of Microsoft cloud connectivity</span></span>

 <span data-ttu-id="f2b35-104">**요약:** 네트워킹 인프라의 공통 요소와 네트워크를 준비 하는 방법을 이해 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2b35-104">**Summary:** Understand the common elements of networking infrastructure and how to prepare your network.</span></span>
  
<span data-ttu-id="f2b35-105">네트워킹을 Microsoft 클라우드와 통합하면 보다 폭넓은 서비스에 최적 상태로 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2b35-105">Integrating your networking with the Microsoft cloud provides optimal access to a broad range of services.</span></span>
  
## <a name="steps-to-prepare-your-network-for-microsoft-cloud-services"></a><span data-ttu-id="f2b35-106">Microsoft 클라우드 서비스용 네트워크를 준비 하는 단계</span><span class="sxs-lookup"><span data-stu-id="f2b35-106">Steps to prepare your network for Microsoft cloud services</span></span>
<span data-ttu-id="f2b35-107"><a name="steps"> </a></span><span class="sxs-lookup"><span data-stu-id="f2b35-107"></span></span>

<span data-ttu-id="f2b35-108">온-프레미스 네트워크에 대해 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2b35-108">For your on-premises network:</span></span>
  
1. <span data-ttu-id="f2b35-109">클라이언트 컴퓨터를 분석 하 고 네트워크 하드웨어, 소프트웨어 드라이버, 프로토콜 설정 및 인터넷 브라우저에 맞게 최적화 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2b35-109">Analyze your client computers and optimize for network hardware, software drivers, protocol settings, and Internet browsers.</span></span>
    
2. <span data-ttu-id="f2b35-110">인터넷에 지 장치에 대 한 트래픽 대기 시간 및 최적의 라우팅을 위해 온-프레미스 네트워크를 분석 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2b35-110">Analyze your on-premises network for traffic latency and optimal routing to the Internet edge device.</span></span>
    
3. <span data-ttu-id="f2b35-111">인터넷에 지 장치의 용량 및 성능을 분석 하 고 더 높은 트래픽 수준에 맞게 최적화 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2b35-111">Analyze the capacity and performance of your Internet edge device and optimize for higher levels of traffic.</span></span>
    
<span data-ttu-id="f2b35-112">인터넷 연결의 경우:</span><span class="sxs-lookup"><span data-stu-id="f2b35-112">For your Internet connection:</span></span>
  
1. <span data-ttu-id="f2b35-113">외부 방화벽과 같은 인터넷에 지 장치 및 연결할 Microsoft 클라우드 서비스의 지역별 위치 간의 대기 시간을 분석 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2b35-113">Analyze the latency between your Internet edge device (such as your external firewall) and the regional locations of the Microsoft cloud service to which you are connecting.</span></span>
    
2. <span data-ttu-id="f2b35-114">현재 인터넷 연결의 용량 및 사용률을 분석 하 고 필요한 경우 용량을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2b35-114">Analyze the capacity and utilization of your current Internet connection and add capacity if needed.</span></span> <span data-ttu-id="f2b35-115">또는, express 경로 연결을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2b35-115">Alternately, add an ExpressRoute connection.</span></span>
    
## <a name="microsoft-cloud-connectivity-options"></a><span data-ttu-id="f2b35-116">Microsoft 클라우드 연결 옵션</span><span class="sxs-lookup"><span data-stu-id="f2b35-116">Microsoft cloud connectivity options</span></span>
<span data-ttu-id="f2b35-117"><a name="steps"> </a></span><span class="sxs-lookup"><span data-stu-id="f2b35-117"></span></span>

<span data-ttu-id="f2b35-118">기존 인터넷 파이프 또는 Office 365, Azure 및 Dynamics 365에 대 한 express 연결을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2b35-118">Use your existing Internet pipe or an ExpressRoute connection to Office 365, Azure, and Dynamics 365.</span></span>
  
<span data-ttu-id="f2b35-119">**그림 1: Microsoft 클라우드 연결에 대 한 옵션**</span><span class="sxs-lookup"><span data-stu-id="f2b35-119">**Figure 1: Options for Microsoft cloud connectivity**</span></span>

![그림 1: Microsoft 클라우드 연결에 대 한 옵션](media/Network-Poster/CommonElements.png)

  
<span data-ttu-id="f2b35-121">그림 1에서는 기존 인터넷 파이프 또는 비트 경로를 사용 하 여 온-프레미스 네트워크를 Microsoft 클라우드 제품에 연결 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f2b35-121">Figure 1 shows how an on-premises network can be connected to Microsoft cloud offerings using their existing Internet pipe or ExpressRoute.</span></span> <span data-ttu-id="f2b35-122">인터넷 파이프는 DMZ를 나타내며 다음과 같은 구성 요소를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2b35-122">The Internet pipe represents a DMZ and can have the following components:</span></span>
  
- <span data-ttu-id="f2b35-123">**내부 방화벽:** 신뢰할 수 있는 네트워크와 트러스트 되지 않은 네트워크가 서로 다른 장벽입니다.</span><span class="sxs-lookup"><span data-stu-id="f2b35-123">**Internal firewall:** A barrier between your trusted network and an untrusted one.</span></span> <span data-ttu-id="f2b35-124">규칙에 따라 트래픽 필터링 및 모니터링을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2b35-124">Performs traffic filtering (based on rules) and monitoring.</span></span>
    
- <span data-ttu-id="f2b35-125">**외부 작업:** 인터넷에서 외부 사용자가 사용할 수 있는 웹 사이트 또는 기타 작업</span><span class="sxs-lookup"><span data-stu-id="f2b35-125">**External workload:** Web sites or other workloads made available to external users on the Internet.</span></span>
    
- <span data-ttu-id="f2b35-126">**프록시 서버:** 서비스 인트라넷 사용자를 대신 하 여 웹 콘텐츠를 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2b35-126">**Proxy server:** Services requests for web content on behalf of intranet users.</span></span> <span data-ttu-id="f2b35-127">역방향 프록시는 원치 않는 인바운드 요청을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2b35-127">A reverse proxy permits unsolicited inbound requests.</span></span>
    
- <span data-ttu-id="f2b35-128">**외부 방화벽:** 아웃 바운드 트래픽 및 지정 된 인바운드 트래픽을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2b35-128">**External firewall:** Allows outbound traffic and specified inbound traffic.</span></span> <span data-ttu-id="f2b35-129">주소 변환, 패킷 검사, SSL 중단 및 검사, 데이터 손실 방지 등을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2b35-129">Can perform address translation, packet inspection, SSL Break and Inspect, or data loss prevention.</span></span>
    
- <span data-ttu-id="f2b35-130">**ISP에 대 한 WAN 연결:** 인터넷을 통해 연결 하 고 라우팅할 때 ISP에 대 한 반송파 기반 연결</span><span class="sxs-lookup"><span data-stu-id="f2b35-130">**WAN connection to ISP:** A carrier-based connection to an ISP, who peers with the Internet for connectivity and routing.</span></span>
    
## <a name="areas-of-networking-common-to-all-microsoft-cloud-services"></a><span data-ttu-id="f2b35-131">모든 Microsoft 클라우드 서비스에 공통 되는 네트워킹 영역</span><span class="sxs-lookup"><span data-stu-id="f2b35-131">Areas of networking common to all Microsoft cloud services</span></span>
<span data-ttu-id="f2b35-132"><a name="steps"> </a></span><span class="sxs-lookup"><span data-stu-id="f2b35-132"></span></span>

<span data-ttu-id="f2b35-133">Microsoft의 클라우드 서비스를 채택할 때 이러한 네트워킹 영역을 고려해 야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2b35-133">You need to consider these areas of networking when adopting any of Microsoft's cloud services.</span></span>
  
- <span data-ttu-id="f2b35-134">**인트라넷 성능:** 클라이언트 컴퓨터를 포함 하는 인트라넷이 최적화 되지 않으면 인터넷 기반 리소스에 대 한 성능이 저하 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2b35-134">**Intranet performance:** Performance to Internet-based resources will suffer if your intranet, including client computers, is not optimized.</span></span>
    
- <span data-ttu-id="f2b35-135">에 **지 장치:** 네트워크의 가장자리에 있는 장치는 egress 지점으로, nat (network Address 번역가), 프록시 서버 (역방향 프록시 포함), 방화벽, 침입 감지 장치 또는 조합 등을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2b35-135">**Edge devices:** Devices at the edge of your network are egress points and can include Network Address Translators (NATs), proxy servers (including reverse proxies), firewalls, intrusion detection devices, or a combination.</span></span>
    
- <span data-ttu-id="f2b35-136">**인터넷 연결:** ISP와 인터넷에 대 한 WAN 연결에서는 최대 부하를 처리할 수 있는 충분 한 용량을 가져야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2b35-136">**Internet connection:** Your WAN connection to your ISP and the Internet should have enough capacity to handle peak loads.</span></span> <span data-ttu-id="f2b35-137">또한 express 경로 연결을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2b35-137">You can also use an ExpressRoute connection.</span></span>
    
- <span data-ttu-id="f2b35-138">**인터넷 DNS:** Microsoft 클라우드 또는 클라우드에서 호스트 되는 서비스를 찾기 위한 A, AAAA, CNAME, MX, PTR 및 기타 레코드입니다.</span><span class="sxs-lookup"><span data-stu-id="f2b35-138">**Internet DNS:** A, AAAA, CNAME, MX, PTR and other records to locate Microsoft cloud or your services hosted in the cloud.</span></span> <span data-ttu-id="f2b35-139">예를 들어 Azure PaaS에 호스트 되는 앱에 대 한 CNAME 레코드가 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2b35-139">For example, you might need a CNAME record for your app hosted in Azure PaaS.</span></span>
    

## <a name="next-step"></a><span data-ttu-id="f2b35-140">다음 단계</span><span class="sxs-lookup"><span data-stu-id="f2b35-140">Next step</span></span>

[<span data-ttu-id="f2b35-141">Microsoft 클라우드 연결에 대한 ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="f2b35-141">ExpressRoute for Microsoft cloud connectivity</span></span>](expressroute-for-microsoft-cloud-connectivity.md)

## <a name="see-also"></a><span data-ttu-id="f2b35-142">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f2b35-142">See also</span></span>

<span data-ttu-id="f2b35-143"><a name="steps"> </a></span><span class="sxs-lookup"><span data-stu-id="f2b35-143"></span></span>

[<span data-ttu-id="f2b35-144">Microsoft Cloud Networking for Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="f2b35-144">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="f2b35-145">Microsoft 클라우드 IT 아키텍처 리소스</span><span class="sxs-lookup"><span data-stu-id="f2b35-145">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)


