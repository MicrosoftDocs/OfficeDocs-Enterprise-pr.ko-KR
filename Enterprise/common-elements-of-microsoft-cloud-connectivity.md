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
description: '요약: 네트워킹 인프라의 일반적인 요소 및 네트워크를 준비 하는 방법을 이해 합니다.'
ms.openlocfilehash: e00ad8820ef37c818c270323cf2aa036bb86a804
ms.sourcegitcommit: 25a022f4ef4e56c5407e8e3a8a34265f8fc94264
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/29/2018
ms.locfileid: "26872219"
---
# <a name="common-elements-of-microsoft-cloud-connectivity"></a><span data-ttu-id="3cf8a-103">Microsoft 클라우드 연결의 공통 요소</span><span class="sxs-lookup"><span data-stu-id="3cf8a-103">Common elements of Microsoft cloud connectivity</span></span>

 <span data-ttu-id="3cf8a-104">**요약:** 네트워킹 인프라의 공통 요소 및 네트워크를 준비 하는 방법을 이해 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cf8a-104">**Summary:** Understand the common elements of networking infrastructure and how to prepare your network.</span></span>
  
<span data-ttu-id="3cf8a-105">네트워킹을 Microsoft 클라우드와 통합하면 보다 폭넓은 서비스에 최적 상태로 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3cf8a-105">Integrating your networking with the Microsoft cloud provides optimal access to a broad range of services.</span></span>
  
## <a name="steps-to-prepare-your-network-for-microsoft-cloud-services"></a><span data-ttu-id="3cf8a-106">Microsoft 클라우드 서비스에 대 한 네트워크를 준비 하는 단계</span><span class="sxs-lookup"><span data-stu-id="3cf8a-106">Steps to prepare your network for Microsoft cloud services</span></span>
<span data-ttu-id="3cf8a-107"><a name="steps"> </a></span><span class="sxs-lookup"><span data-stu-id="3cf8a-107"></span></span>

<span data-ttu-id="3cf8a-108">온-프레미스 네트워크:</span><span class="sxs-lookup"><span data-stu-id="3cf8a-108">For your on-premises network:</span></span>
  
1. <span data-ttu-id="3cf8a-109">클라이언트 컴퓨터를 분석 하 고 네트워크 하드웨어, 소프트웨어 드라이버, 프로토콜 설정 및 인터넷 브라우저를 최적화 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cf8a-109">Analyze your client computers and optimize for network hardware, software drivers, protocol settings, and Internet browsers.</span></span>
    
2. <span data-ttu-id="3cf8a-110">트래픽 대기 시간 및 인터넷에서에 지 장치 최적의 라우팅에 대 한 온-프레미스 네트워크를 분석 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cf8a-110">Analyze your on-premises network for traffic latency and optimal routing to the Internet edge device.</span></span>
    
3. <span data-ttu-id="3cf8a-111">인터넷에 지 장치의 성능과 용량을 분석 하 고 더 높은 수준의 트래픽 최적화 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cf8a-111">Analyze the capacity and performance of your Internet edge device and optimize for higher levels of traffic.</span></span>
    
<span data-ttu-id="3cf8a-112">인터넷 연결에 대 한:</span><span class="sxs-lookup"><span data-stu-id="3cf8a-112">For your Internet connection:</span></span>
  
1. <span data-ttu-id="3cf8a-113">인터넷에 지 장치 (예: 외부 방화벽)와 연결 된 Microsoft 클라우드 서비스의 지역 위치 간 대기 시간을 분석 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cf8a-113">Analyze the latency between your Internet edge device (such as your external firewall) and the regional locations of the Microsoft cloud service to which you are connecting.</span></span>
    
2. <span data-ttu-id="3cf8a-p101">용량 및 현재 인터넷 연결의 사용률을 분석 하 고 필요한 경우 용량을 추가 합니다. 또는 ExpressRoute에 대 한 연결을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cf8a-p101">Analyze the capacity and utilization of your current Internet connection and add capacity if needed. Alternately, add an ExpressRoute connection.</span></span>
    
## <a name="microsoft-cloud-connectivity-options"></a><span data-ttu-id="3cf8a-116">Microsoft 클라우드 연결 옵션</span><span class="sxs-lookup"><span data-stu-id="3cf8a-116">Microsoft cloud connectivity options</span></span>
<span data-ttu-id="3cf8a-117"><a name="steps"> </a></span><span class="sxs-lookup"><span data-stu-id="3cf8a-117"></span></span>

<span data-ttu-id="3cf8a-118">기존 인터넷 파이프 사용자 또는 Office 365, Azure, 및 Dynamics 365 대 한 ExpressRoute 연결을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cf8a-118">Use your existing Internet pipe or an ExpressRoute connection to Office 365, Azure, and Dynamics 365.</span></span>
  
<span data-ttu-id="3cf8a-119">**Microsoft 클라우드 연결에 대 한 그림 1: 옵션**</span><span class="sxs-lookup"><span data-stu-id="3cf8a-119">**Figure 1: Options for Microsoft cloud connectivity**</span></span>

![그림 1:  Microsoft 클라우드 연결을 위한 옵션](media/Network-Poster/CommonElements.png)

  
<span data-ttu-id="3cf8a-p102">그림 1는 기존 인터넷 파이프 또는 ExpressRoute를 사용 하 여 Microsoft 클라우드 서비스에는 온-프레미스 네트워크 수 연결 하는 방법을 보여줍니다. 인터넷 파이프 DMZ를 나타내며 다음과 같은 구성 요소를 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3cf8a-p102">Figure 1 shows how an on-premises network can be connected to Microsoft cloud offerings using their existing Internet pipe or ExpressRoute. The Internet pipe represents a DMZ and can have the following components:</span></span>
  
- <span data-ttu-id="3cf8a-p103">**내부 방화벽:** 신뢰할 수 있는 네트워크 사이는 신뢰할 수 없는 간의 장벽입니다. 트래픽 필터링 (규칙에 따라) 및 모니터링을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cf8a-p103">**Internal firewall:** A barrier between your trusted network and an untrusted one. Performs traffic filtering (based on rules) and monitoring.</span></span>
    
- <span data-ttu-id="3cf8a-125">**외부 작업:** 웹사이트 또는 기타 작업 사용할 수는 인터넷에서 외부 사용자에 게 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3cf8a-125">**External workload:** Web sites or other workloads made available to external users on the Internet.</span></span>
    
- <span data-ttu-id="3cf8a-p104">**프록시 서버:** 인트라넷 사용자를 대신 하 여 웹 콘텐츠에 대 한 요청을 처리 합니다. 역방향 프록시는 원하지 않는 인바운드 요청을 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="3cf8a-p104">**Proxy server:** Services requests for web content on behalf of intranet users. A reverse proxy permits unsolicited inbound requests.</span></span>
    
- <span data-ttu-id="3cf8a-p105">**외부 방화벽:** 아웃 바운드 트래픽 및 지정 된 인바운드 트래픽을 허용합니다. 주소 변환, 패킷 검사, SSL 중단 하 고 검사, 또는 데이터 손실 방지를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3cf8a-p105">**External firewall:** Allows outbound traffic and specified inbound traffic. Can perform address translation, packet inspection, SSL Break and Inspect, or data loss prevention.</span></span>
    
- <span data-ttu-id="3cf8a-130">**ISP에 대 한 WAN 연결:** 연결 및 라우팅에 대 한 인터넷을 통한 피어가 ISP에 통신사업자 기반 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cf8a-130">**WAN connection to ISP:** A carrier-based connection to an ISP, who peers with the Internet for connectivity and routing.</span></span>
    
## <a name="areas-of-networking-common-to-all-microsoft-cloud-services"></a><span data-ttu-id="3cf8a-131">모든 Microsoft 클라우드 서비스에 일반적인 네트워킹의 영역</span><span class="sxs-lookup"><span data-stu-id="3cf8a-131">Areas of networking common to all Microsoft cloud services</span></span>
<span data-ttu-id="3cf8a-132"><a name="steps"> </a></span><span class="sxs-lookup"><span data-stu-id="3cf8a-132"></span></span>

<span data-ttu-id="3cf8a-133">Microsoft의 클라우드 서비스 중 하나를 채택 하는 경우 네트워킹의 이러한 영역을 고려해 야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cf8a-133">You need to consider these areas of networking when adopting any of Microsoft's cloud services.</span></span>
  
- <span data-ttu-id="3cf8a-134">**인트라넷 성능:** 클라이언트 컴퓨터를 포함 하 여 인트라넷을 최적화 되지 않은 경우 인터넷 기반 리소스에는 성능 저하 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3cf8a-134">**Intranet performance:** Performance to Internet-based resources will suffer if your intranet, including client computers, is not optimized.</span></span>
    
- <span data-ttu-id="3cf8a-135">**장치에 지:** 네트워크의 가장자리 탈출 요소가 장치와 네트워크 주소 변환기 (Nat), 프록시 서버 (역방향 프록시 포함), 방화벽, 침입 탐지 장치 또는 조합이 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3cf8a-135">**Edge devices:** Devices at the edge of your network are egress points and can include Network Address Translators (NATs), proxy servers (including reverse proxies), firewalls, intrusion detection devices, or a combination.</span></span>
    
- <span data-ttu-id="3cf8a-p106">**인터넷 연결:** ISP와 인터넷에 대 한 WAN 연결에는 최대 부하를 처리 하기에 충분 한 용량이 있어야 합니다. 또한 ExpressRoute 연결을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3cf8a-p106">**Internet connection:** Your WAN connection to your ISP and the Internet should have enough capacity to handle peak loads. You can also use an ExpressRoute connection.</span></span>
    
- <span data-ttu-id="3cf8a-p107">**인터넷 DNS:** A, AAAA, CNAME, MX, PTR 및 다른 레코드를 Microsoft 클라우드 또는 클라우드에서 호스팅되는 서비스를 찾습니다. 예, Azure PaaS에서 호스팅되는 응용 프로그램에 대 한 CNAME 레코드를 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3cf8a-p107">**Internet DNS:** A, AAAA, CNAME, MX, PTR and other records to locate Microsoft cloud or your services hosted in the cloud. For example, you might need a CNAME record for your app hosted in Azure PaaS.</span></span>
    

## <a name="next-step"></a><span data-ttu-id="3cf8a-140">다음 단계</span><span class="sxs-lookup"><span data-stu-id="3cf8a-140">Next step</span></span>

[<span data-ttu-id="3cf8a-141">Microsoft 클라우드 연결에 대한 ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="3cf8a-141">ExpressRoute for Microsoft cloud connectivity</span></span>](expressroute-for-microsoft-cloud-connectivity.md)

## <a name="see-also"></a><span data-ttu-id="3cf8a-142">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3cf8a-142">See also</span></span>

<span data-ttu-id="3cf8a-143"><a name="steps"> </a></span><span class="sxs-lookup"><span data-stu-id="3cf8a-143"></span></span>

[<span data-ttu-id="3cf8a-144">Microsoft Cloud Networking for Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="3cf8a-144">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="3cf8a-145">Microsoft 클라우드 IT 아키텍처 리소스</span><span class="sxs-lookup"><span data-stu-id="3cf8a-145">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)


