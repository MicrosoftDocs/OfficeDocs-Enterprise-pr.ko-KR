---
title: Microsoft 클라우드 연결을 위한 ExpressRoute
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/12/2019
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: bf2295c4-d411-49cd-aaa5-116a4a456c5a
description: '요약: Microsoft의 클라우드 서비스 및 플랫폼에 대 한 더 빠르고 안정적인 연결을 지원 하기 위한 방법에 대해 알아봅니다.'
ms.openlocfilehash: a3b36e98c946bc3ae7281bd38cd4b98820ee8afb
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/30/2019
ms.locfileid: "33488170"
---
# <a name="expressroute-for-microsoft-cloud-connectivity"></a><span data-ttu-id="bce47-103">Microsoft 클라우드 연결을 위한 ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="bce47-103">ExpressRoute for Microsoft cloud connectivity</span></span>

 <span data-ttu-id="bce47-104">**요약:** Microsoft의 클라우드 서비스 및 플랫폼에 대 한 더 빠르고 안정적인 연결을 지원 하기 위한 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-104">**Summary:** Understand how ExpressRoute can help you with faster and more reliable connections to Microsoft's cloud services and platforms.</span></span>
  
<span data-ttu-id="bce47-105">ExpressRoute는 Microsoft 클라우드에 대해 개인, 전용, 고처리량의 네트워크 연결을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-105">ExpressRoute provides a private, dedicated, high-throughput network connection to Microsoft's cloud.</span></span>
  
## <a name="expressroute-to-the-microsoft-cloud"></a><span data-ttu-id="bce47-106">Microsoft 클라우드로의 모든 express</span><span class="sxs-lookup"><span data-stu-id="bce47-106">ExpressRoute to the Microsoft cloud</span></span>

<span data-ttu-id="bce47-107">다음은 express 연결을 사용 하지 않고 Microsoft 클라우드의 네트워킹 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-107">Here is the networking path to the Microsoft cloud without an ExpressRoute connection.</span></span>
  
<span data-ttu-id="bce47-108">**그림 1: express가 없는 네트워킹 경로**</span><span class="sxs-lookup"><span data-stu-id="bce47-108">**Figure 1: The networking path without ExpressRoute**</span></span>

![그림 1: express가 없는 네트워킹 경로](media/Network-Poster/ExpressRoute.png)
  
<span data-ttu-id="bce47-110">그림 1에서는 온-프레미스 네트워크와 Microsoft 클라우드 간의 일반적인 경로를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-110">Figure 1 shows the typical path between an on-premises network and the Microsoft cloud.</span></span> <span data-ttu-id="bce47-111">온-프레미스 네트워크에 지는 ISP에 대 한 WAN 링크를 통해 인터넷에 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-111">The on-premises network edge connects to the Internet through a WAN link to an ISP.</span></span> <span data-ttu-id="bce47-112">그러면 트래픽은 인터넷을 통해 Microsoft 클라우드의 가장자리로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-112">The traffic then travels across the Internet to the edge of the Microsoft cloud.</span></span> <span data-ttu-id="bce47-113">microsoft 클라우드 내의 클라우드 제품에는 Office 365, microsoft Azure, microsoft Intune 및 Dynamics 365가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-113">Cloud offerings within the Microsoft cloud include Office 365, Microsoft Azure, Microsoft Intune, and Dynamics 365.</span></span> <span data-ttu-id="bce47-114">조직의 사용자는 온-프레미스 네트워크 또는 인터넷에 위치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-114">Users of an organization can be located on the on-premises network or on the Internet.</span></span>
  
<span data-ttu-id="bce47-115">express 기반 연결이 없으면 온-프레미스 네트워크에 지와 ISP 간의 연결을 제어할 수 있는 Microsoft 클라우드 (즉, 서비스 공급자와의 관계)에 대 한 트래픽 경로의 일부일 뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-115">Without an ExpressRoute connection, the only part of the traffic path to the Microsoft cloud that you can control (and have a relationship with the service provider) is the link between your on-premises network edge and your ISP.</span></span> 
  
<span data-ttu-id="bce47-116">ISP와 Microsoft 클라우드 edge 간의 경로는 악의적인 사용자의 중단, 트래픽 혼잡 및 모니터링을 통해 인터넷에서 가장 좋은 배달 시스템입니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-116">The path between your ISP and the Microsoft cloud edge is a best-effort delivery system on the Internet subject to outages, traffic congestion, and monitoring by malicious users.</span></span>
  
<span data-ttu-id="bce47-117">로밍 또는 원격 사용자와 같은 인터넷의 사용자는 인터넷을 통해 Microsoft 클라우드로 트래픽을 전송 합니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-117">Users on the Internet, such as roaming or remote users, send their traffic to the Microsoft cloud over the Internet.</span></span>
  
<span data-ttu-id="bce47-118">다음은 express로 연결 되는 Microsoft 클라우드의 네트워킹 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-118">Here are the networking paths to the Microsoft cloud with an ExpressRoute connection.</span></span>
  
<span data-ttu-id="bce47-119">**그림 2: express를 사용 하는 네트워킹 경로**</span><span class="sxs-lookup"><span data-stu-id="bce47-119">**Figure 2: The networking paths with ExpressRoute**</span></span>

![그림 2: express를 사용 하는 네트워킹 경로](media/Network-Poster/ExpressRoute-post.png)
  
<span data-ttu-id="bce47-121">그림 2는 두 개의 네트워킹 경로를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-121">Figure 2 shows two networking paths.</span></span> <span data-ttu-id="bce47-122">Microsoft Intune으로의 트래픽은 일반적인 인터넷 트래픽과 같은 경로를 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-122">Traffic to Microsoft Intune travels the same path as normal Internet traffic.</span></span> <span data-ttu-id="bce47-123">Office 365, microsoft Azure 및 Dynamics 365에 대 한 트래픽은 온-프레미스 네트워크의 가장자리와 Microsoft 클라우드의 가장자리 사이의 전용 경로인 간 연결을 통해 이동 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-123">Traffic to Office 365, Microsoft Azure, and Dynamics 365 travels across the ExpressRoute connection, a dedicated path between the edge of the on-premises network and the edge of the Microsoft cloud.</span></span>
  
<span data-ttu-id="bce47-124">이제는이 연결을 통해 서비스 공급자와의 관계를 통해 edge에서 Microsoft 클라우드 edge까지 전체 트래픽 경로를 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-124">With an ExpressRoute connection, you now have control, through a relationship with your service provider, over the entire traffic path from your edge to the Microsoft cloud edge.</span></span> <span data-ttu-id="bce47-125">이 연결은 예측 가능한 성능을 제공 하 고 [99.95% 가동 SLA](https://azure.microsoft.com/support/legal/sla/expressroute/v1_3/)를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-125">This connection can offer predictable performance and a [99.95% uptime SLA](https://azure.microsoft.com/support/legal/sla/expressroute/v1_3/).</span></span>
  
<span data-ttu-id="bce47-126">이제 서비스 공급자의 연결, Office 365, Azure 및 Dynamics 365 서비스에 따라 예측 가능한 처리량과 대기 시간을 계산할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-126">You can now count on predictable throughput and latency, based on your service provider's connection, to Office 365, Azure, and Dynamics 365 services.</span></span> <span data-ttu-id="bce47-127">지금은 Microsoft Intune에 대 한 간 연결이 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-127">ExpressRoute connections to Microsoft Intune are not supported at this time.</span></span>
  
<span data-ttu-id="bce47-128">express 경로 연결을 통해 전송 되는 트래픽은 더 이상 인터넷 중단, 트래픽 혼잡 및 모니터링에 영향을 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-128">Traffic sent over the ExpressRoute connection is no longer subject to Internet outages, traffic congestion, and monitoring.</span></span>
  
<span data-ttu-id="bce47-129">로밍 또는 원격 사용자와 같은 인터넷의 사용자는 여전히 인터넷을 통해 Microsoft 클라우드로 트래픽을 전송 합니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-129">Users on the Internet, such as roaming or remote users, still send their traffic to the Microsoft cloud over the Internet.</span></span> <span data-ttu-id="bce47-130">한 가지 예외는 Azure IaaS에 호스트 되는 인트라넷 라인 비즈니스 응용 프로그램에 대 한 트래픽으로, 원격 액세스 연결을 통해 온-프레미스 네트워크로의 연결을 통해 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-130">One exception is traffic to an intranet line of business application hosted in Azure IaaS, which is sent over the ExpressRoute connection via a remote access connection to the on-premises network.</span></span>
  
<span data-ttu-id="bce47-131">또한이 연결을 사용 하는 경우에도 일부 트래픽은 인터넷을 통해 여전히 DNS 쿼리, 인증서 해지 목록 확인 및 CDN (콘텐츠 배달 네트워크) 요청과 같이 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-131">Even with an ExpressRoute connection, some traffic is still sent over the Internet, such as DNS queries, certificate revocation list checking, and content delivery network (CDN) requests.</span></span>
  
<span data-ttu-id="bce47-132">자세한 내용은 다음 추가 리소스를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bce47-132">See these additional resources for more information:</span></span>
  
- [<span data-ttu-id="bce47-133">Office 365용 Express 경로</span><span class="sxs-lookup"><span data-stu-id="bce47-133">ExpressRoute for Office 365</span></span>](https://aka.ms/expressrouteoffice365)
    
- [<span data-ttu-id="bce47-134">Azure의 express 경로</span><span class="sxs-lookup"><span data-stu-id="bce47-134">ExpressRoute for Azure</span></span>](https://azure.microsoft.com/services/expressroute/)
    
## <a name="advantages-of-expressroute-for-azure"></a><span data-ttu-id="bce47-135">Azure에 대 한 express의 장점</span><span class="sxs-lookup"><span data-stu-id="bce47-135">Advantages of ExpressRoute for Azure</span></span>

<span data-ttu-id="bce47-136">Azure 기반 클라우드 서비스에 대해 express를 사용 하는 경우의 몇 가지 이점은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-136">Here are some advantages of using ExpressRoute for Azure-based cloud services:</span></span>
  
- <span data-ttu-id="bce47-137">**예측 가능한 성능:** Microsoft 클라우드의 가장자리에 대 한 전용 경로를 사용 하는 경우에는 성능이 인터넷 공급자 중단 및 인터넷 트래픽의 스파이크에 영향을 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-137">**Predictable performance:** With a dedicated path to the edge of the Microsoft cloud, your performance is not subject to Internet provider outages and spikes in Internet traffic.</span></span> <span data-ttu-id="bce47-138">Microsoft 클라우드에 대 한 처리량 및 대기 시간 SLA를 담당 하는 공급자를 확인 하 고 보유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-138">You can determine and hold your providers accountable to a throughput and latency SLA to the Microsoft cloud.</span></span>
    
- <span data-ttu-id="bce47-139">**트래픽에 대 한 데이터 개인 정보:** 전용 express 경로 연결을 통해 전송 되는 트래픽은 악의적인 사용자가 인터넷을 모니터링 하거나 패킷 캡처 및 분석을 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-139">**Data privacy for your traffic:** Traffic sent over your dedicated ExpressRoute connection is not subject to Internet monitoring or packet capture and analysis by malicious users.</span></span> <span data-ttu-id="bce47-140">MPLS (멀티 프로토콜 레이블 전환) 기반 WAN 링크를 사용 하는 것 만큼 안전 합니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-140">It is as secure as using Multiprotocol Label Switching (MPLS)-based WAN links.</span></span>
    
- <span data-ttu-id="bce47-141">**높은 처리량 연결:** exchange 공급자 및 네트워크 서비스 공급자가 제공 하는 express 간 연결에 대 한 폭넓은 지원을 통해 Microsoft 클라우드에 최대 10mb의 링크를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-141">**High throughput connections:** With wide support for ExpressRoute connections by exchange providers and network service providers, you can obtain up to a 10 Gbps link to the Microsoft cloud.</span></span>
    
- <span data-ttu-id="bce47-142">**일부 구성의 경우 비용이 저렴 합니다.** 경제적인 연결 비용은 추가 비용이 긴 하지만, 경우에 따라 단일 express 연결을 통해 Microsoft 클라우드 서비스에 적절 한 처리량을 제공 하기 위해 조직의 여러 위치에서 인터넷 용량을 늘리는 것 보다 비용이 적게 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-142">**Lower cost for some configurations:** Although ExpressRoute connections are an additional cost, in some cases a single ExpressRoute connection can cost less than increasing your Internet capacity at multiple locations of your organization to provide adequate throughput to Microsoft cloud services.</span></span>
    
<span data-ttu-id="bce47-143">모든 구성에서 한도로 연결을 설정 하는 것은 더 높은 성능을 보장 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-143">An ExpressRoute connection is not a guarantee of higher performance in every configuration.</span></span> <span data-ttu-id="bce47-144">지역 Microsoft 데이터 센터에서 몇 가지 홉만을 제외 하는 고대역폭 인터넷 연결 보다 대역폭이 낮은 비트 단위 연결을 사용 하는 경우에는 성능이 낮아질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-144">It is possible to have lower performance over a low-bandwidth ExpressRoute connection than a high-bandwidth Internet connection that is only a few hops away from a regional Microsoft datacenter.</span></span>
  
<span data-ttu-id="bce47-145">office 365에서 express를 사용 하기 위한 최신 권장 사항은 [office 365 용 express](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="bce47-145">For the latest recommendations for using ExpressRoute with Office 365, see [ExpressRoute for Office 365](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd).</span></span>
  
## <a name="expressroute-connectivity-models"></a><span data-ttu-id="bce47-146">express 경로 연결 모델</span><span class="sxs-lookup"><span data-stu-id="bce47-146">ExpressRoute connectivity models</span></span>

<span data-ttu-id="bce47-147">표 1에는 간 연결에 대 한 세 가지 기본 연결 모델이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-147">Table 1 shows the three primary connectivity models for ExpressRoute connections.</span></span>
  
|<span data-ttu-id="bce47-148">**클라우드 exchange에 배치**</span><span class="sxs-lookup"><span data-stu-id="bce47-148">**Co-located at a cloud exchange**</span></span>|<span data-ttu-id="bce47-149">**지점 간 이더넷**</span><span class="sxs-lookup"><span data-stu-id="bce47-149">**Point-to-point Ethernet**</span></span>|<span data-ttu-id="bce47-150">**임의 (IP VPN) 연결**</span><span class="sxs-lookup"><span data-stu-id="bce47-150">**Any-to-any (IP VPN) connection**</span></span>|
|:-----|:-----|:-----|
|![express 경로 연결 모델: 클라우드 exchange에 배치](media/Network-Poster/ER-Conn1.png)|![express 수준 연결 모델: 지점 간 이더넷](media/Network-Poster/ER-Conn2.png)|![express 수준 연결 모델: any (IP VPN) 연결](media/Network-Poster/ER-Conn3.png)|
|<span data-ttu-id="bce47-154">데이터 센터가 클라우드 교환과 함께 기능에 배치 되어 있는 경우, 공동 위치 공급자의 이더넷 교환을 통해 Microsoft 클라우드와의 가상 교차 연결을 주문할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-154">If your datacenter is co-located in a facility with a cloud exchange, you can order a virtual cross-connection to the Microsoft cloud through the co-location provider's Ethernet exchange.</span></span>  <br/> |<span data-ttu-id="bce47-155">데이터 센터가 온-프레미스에 있는 경우 지점간 이더넷 링크를 사용 하 여 Microsoft 클라우드에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-155">If your datacenter is located on your premises, you can use a point-to-point Ethernet link to connect to the Microsoft cloud.</span></span>  <br/> |<span data-ttu-id="bce47-156">이미 IP VPN (MPLS) 공급자를 사용 하 여 조직의 사이트에 연결 하는 경우 Microsoft 클라우드로의 간 연결 기능은 사설 WAN의 다른 위치와 동일 하 게 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-156">If you are already using an IP VPN (MPLS) provider to connect the sites of your organization, an ExpressRoute connection to the Microsoft cloud acts like another location on your private WAN.</span></span>  <br/> |
   
 <span data-ttu-id="bce47-157">**표 1: express 경로 연결 모델**</span><span class="sxs-lookup"><span data-stu-id="bce47-157">**Table 1: ExpressRoute connectivity models**</span></span>
  
## <a name="expressroute-peering-relationships-to-microsoft-cloud-services"></a><span data-ttu-id="bce47-158">Microsoft 클라우드 서비스에 대 한 자세한 피어 링 관계</span><span class="sxs-lookup"><span data-stu-id="bce47-158">ExpressRoute peering relationships to Microsoft cloud services</span></span>

<span data-ttu-id="bce47-159">단일 express 연결에서는 Microsoft 클라우드의 서로 다른 부분에 대해 두 개의 서로 다른 BGP (Border Gateway Protocol) 피어 링 관계를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-159">A single ExpressRoute connection supports up to two different Border Gateway Protocol (BGP) peering relationships to different parts of the Microsoft cloud.</span></span> <span data-ttu-id="bce47-160">bpg는 피어 링 관계를 사용 하 여 트러스트 및 exchange 라우팅 정보를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-160">BPG uses peering relationships to establish trust and exchange routing information.</span></span>
  
<span data-ttu-id="bce47-161">**그림 3: 단일 express 연결에서 두 개의 서로 다른 BGP 관계**</span><span class="sxs-lookup"><span data-stu-id="bce47-161">**Figure 3: The two different BGP relationships in a single ExpressRoute connection**</span></span>

![그림 3: 단일 express 연결에서 두 개의 서로 다른 BGP 관계](media/Network-Poster/ERPeering.png)
  
<span data-ttu-id="bce47-163">그림 3은 온-프레미스 네트워크를 통한 express 간 연결을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-163">Figure 3 shows an ExpressRoute connection from an on-premises network.</span></span> <span data-ttu-id="bce47-164">이 연결에는 두 개의 논리적 피어 링 관계가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-164">The ExpressRoute connection has two logical peering relationships.</span></span> <span data-ttu-id="bce47-165">microsoft 피어 링 관계는 Office 365, Dynamcs 365 및 Azure PaaS 서비스를 포함 하는 microsoft SaaS 서비스로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-165">A Microsoft peering relationship goes to Microsoft SaaS services, including Office 365, Dynamcs 365, and Azure PaaS services.</span></span> <span data-ttu-id="bce47-166">사설 피어 링 관계는 Azure IaaS 및 가상 컴퓨터를 호스트 하는 가상 네트워크 게이트웨이로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-166">A private peering relationship goes to Azure IaaS and to a virtual network gateway that hosts virtual machines.</span></span>
  
<span data-ttu-id="bce47-167">Microsoft 피어 링 BGP 관계:</span><span class="sxs-lookup"><span data-stu-id="bce47-167">The Microsoft peering BGP relationship:</span></span> 
  
- <span data-ttu-id="bce47-168">은 DMZ의 라우터에서 Office 365, Dynamics 365 및 Azure 서비스의 공용 주소로 변환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-168">Is from a router in your DMZ to the public addresses of Office 365, Dynamics 365, and Azure services.</span></span> 
    
- <span data-ttu-id="bce47-169">양방향으로 시작 되는 통신을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-169">Supports bidirectional-initiated communication.</span></span>
    
<span data-ttu-id="bce47-170">개인 피어 링 BGP 관계:</span><span class="sxs-lookup"><span data-stu-id="bce47-170">The private peering BGP relationship:</span></span>
  
- <span data-ttu-id="bce47-171">는 조직 네트워크의 가장자리에 있는 라우터에서 Azure vnet에 할당 된 개인 IP 주소로 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-171">Is from a router on the edge of your organization network to the private IP addresses assigned to your Azure VNets.</span></span>
    
- <span data-ttu-id="bce47-172">양방향으로 시작 되는 통신을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-172">Supports bidirectional-initiated communication.</span></span>
    
- <span data-ttu-id="bce47-173">은 조직 네트워크를 Microsoft 클라우드로 확장 한 것으로, 내부에서 주소 지정 및 라우팅을 완료 합니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-173">Is an extension of your organization network to the Microsoft cloud, complete with internally-consistent addressing and routing.</span></span>

>[!Note]
><span data-ttu-id="bce47-174">이 문서의 이전 버전에서 설명한 공용 피어 링 BGP 관계는 더 이상 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-174">The public peering BGP relationship described in previous versions of this article has been deprecated.</span></span>
>
    
## <a name="example-of-application-deployment-and-traffic-flow-with-expressroute"></a><span data-ttu-id="bce47-175">express를 사용한 응용 프로그램 배포 및 트래픽 흐름의 예</span><span class="sxs-lookup"><span data-stu-id="bce47-175">Example of application deployment and traffic flow with ExpressRoute</span></span>

<span data-ttu-id="bce47-176">대상 및 응용 프로그램 동작 간의 경로 홉에 따라, Microsoft 클라우드 내에서 트래픽이 여러 개 간의 연결에 따라 이동 하는 방식이 여기에 해당 합니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-176">How traffic travels across ExpressRoute connections and within the Microsoft cloud is a function of the routes at the hops of the path between the source and the destination and application behavior.</span></span> <span data-ttu-id="bce47-177">다음은 사이트 간 VPN 연결을 통해 온-프레미스 SharePoint 팜에 액세스 하는 Azure 가상 컴퓨터에서 실행 되는 응용 프로그램의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-177">Here is an example of an application running on an Azure virtual machine that accesses an on-premises SharePoint farm over a site-to-site VPN connection.</span></span>
  
<span data-ttu-id="bce47-178">**그림 4: 온-프레미스 SharePoint 팜에 액세스 하는 Azure 가상 컴퓨터의 응용 프로그램**</span><span class="sxs-lookup"><span data-stu-id="bce47-178">**Figure 4: An application on an Azure virtual machine accessing an on-premises SharePoint farm**</span></span>

![그림 4: 온-프레미스 SharePoint 팜에 액세스 하는 Azure 가상 컴퓨터의 응용 프로그램](media/Network-Poster/ER-App-Flow1.png)

  
<span data-ttu-id="bce47-180">그림 4에서는 온-프레미스 SharePoint 팜, 온-프레미스 네트워크와 azure iaas의 가상 네트워크 간의 사이트 간 VPN 연결, azure iaas 가상 컴퓨터로 실행 되는 응용 프로그램 서버 및 응용 프로그램 서버 간 트래픽 흐름을 보여 줍니다. SharePoint 팜</span><span class="sxs-lookup"><span data-stu-id="bce47-180">Figure 4 shows an on-premises SharePoint farm, a site-to-site VPN connection between the on-premises network and a virtual network in Azure IaaS, an application server running as an Azure IaaS virtual machine, and the traffic flow between the application server and the SharePoint farm.</span></span>
  
<span data-ttu-id="bce47-181">응용 프로그램은 온-프레미스 DNS를 사용 하 여 SharePoint 팜의 IP 주소를 찾고 모든 트래픽은 사이트 간 VPN 연결을 통해 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-181">The application locates the IP address of the SharePoint farm using the on-premises DNS and all traffic goes over the site-to-site VPN connection.</span></span>
  
<span data-ttu-id="bce47-182">이 조직은 온-프레미스 sharepoint 팜을 Office 365에서 SharePoint Online으로 마이그레이션 했으며,로 연결을 배포 했습니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-182">This organization migrated their on-premises SharePoint farm to SharePoint Online in Office 365 and deployed an ExpressRoute connection.</span></span>
  
<span data-ttu-id="bce47-183">**그림 5: 온-프레미스 sharepoint 팜을 sharepoint Online으로 이동**</span><span class="sxs-lookup"><span data-stu-id="bce47-183">**Figure 5: Moving the on-premises SharePoint farm to SharePoint Online**</span></span>

![그림 5: 온-프레미스 sharepoint 팜을 sharepoint Online으로 이동](media/Network-Poster/Hairpin1.png)
  
<span data-ttu-id="bce47-185">그림 5에서는 Microsoft SaaS 및 Office 365에 대 한 피어 링 관계와 가상 네트워크의 응용 프로그램 서버가 포함 된 Azure IaaS 간의 연결을 추가 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-185">Figure 5 shows the addition of an ExpressRoute connection with peering relationships to Microsoft SaaS and Office 365 and to Azure IaaS containing the application server on a virtual network.</span></span> <span data-ttu-id="bce47-186">SharePoint 온-프레미스 팜이 Office 365로 마이그레이션 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-186">The SharePoint on-premises farm has been migrated to Office 365.</span></span>
  
<span data-ttu-id="bce47-187">Microsoft 및 개인 피어 링 관계를 사용 하는 경우:</span><span class="sxs-lookup"><span data-stu-id="bce47-187">With the Microsoft and private peering relationships:</span></span>
  
- <span data-ttu-id="bce47-188">Azure virtual network 게이트웨이에서 온-프레미스 위치는 간 연결을 통해 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-188">From the Azure virtual network gateway, on-premises locations are available across the ExpressRoute connection.</span></span>
    
- <span data-ttu-id="bce47-189">Office 365 구독에서 프록시 서버와 같은에 지 장치의 공용 IP 주소를 express 간 연결에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-189">From the Office 365 subscription, public IP addresses of edge devices, such as proxy servers, are available across the ExpressRoute connection.</span></span>
    
- <span data-ttu-id="bce47-190">온-프레미스 네트워크에 지에서 Azure VNet의 개인 ip 주소와 Office 365의 공용 ip 주소는 모든 express 연결에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-190">From the on-premises network edge, the private IP addresses of the Azure VNet and the public IP addresses of Office 365 are available across the ExpressRoute connection.</span></span>
    
<span data-ttu-id="bce47-191">응용 프로그램은 SharePoint Online의 url에 액세스 하는 경우, 대상 간 연결을 통해 트래픽을 해당에 지의 프록시 서버로 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-191">When the application accesses the URLs of SharePoint Online, it forwards its traffic across the ExpressRoute connection to a proxy server in the edge.</span></span> 
  
<span data-ttu-id="bce47-192">프록시 서버가 SharePoint Online의 IP 주소를 찾으면이를 통해 통신을 위한 express 연결을 통해 트래픽을 다시 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-192">When the proxy server locates the IP address of SharePoint Online, it forwards the traffic back over the ExpressRoute connection.</span></span> <span data-ttu-id="bce47-193">응답 트래픽은 역방향 경로를 따라 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-193">Response traffic travels the reverse path.</span></span>
  
<span data-ttu-id="bce47-194">**그림 6: sharepoint 팜이 Office 365에서 sharepoint Online으로 마이그레이션 되었을 때의 트래픽 흐름**</span><span class="sxs-lookup"><span data-stu-id="bce47-194">**Figure 6: Traffic flow when the SharePoint farm has been migrated to SharePoint Online in Office 365**</span></span>

![그림 6: sharepoint 팜이 Office 365에서 sharepoint Online으로 마이그레이션 되었을 때의 트래픽 흐름](media/Network-Poster/Hairpin2.png)

  
<span data-ttu-id="bce47-196">그림 6에서는 Office 365에서 응용 프로그램 서버와 SharePoint Online 간의 트래픽이 응용 프로그램 서버에서 온-프레미스 네트워크에 지에 대 한 개인 피어 링 관계를 통과 한 후에 Microsoft 피어 링 관계의 가장자리에서 이동 하는 방식을 보여 줍니다. Office 365</span><span class="sxs-lookup"><span data-stu-id="bce47-196">Figure 6 shows how the traffic between the application server and SharePoint Online in Office 365 flows over the private peering relationship from the application server to the on-premises network edge, and then from the edge over the Microsoft peering relationship to Office 365.</span></span>
  
<span data-ttu-id="bce47-197">이렇게 하면 경로 및 응용 프로그램 동작의 결과로 머리카락 고정이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-197">The result is hair pinning, a consequence of the routing and application behavior.</span></span>
  
## <a name="expressroute-and-microsofts-cloud-network"></a><span data-ttu-id="bce47-198">express 경로 및 Microsoft의 클라우드 네트워크</span><span class="sxs-lookup"><span data-stu-id="bce47-198">ExpressRoute and Microsoft's cloud network</span></span>

<span data-ttu-id="bce47-199">다른 두 버전의 express 경로 연결을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-199">ExpressRoute connections are available in two different versions: ExpressRoute and ExpressRoute Premium.</span></span>
  
### <a name="expressroute"></a><span data-ttu-id="bce47-200">ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="bce47-200">ExpressRoute</span></span>

<span data-ttu-id="bce47-201">조직 네트워크와 Microsoft 데이터 센터 간에 전송 되는 트래픽은 다음과 같은 조합으로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-201">How traffic travels between your organization network and a Microsoft datacenter is a combination of:</span></span>
  
- <span data-ttu-id="bce47-202">위치입니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-202">Your locations.</span></span>
    
- <span data-ttu-id="bce47-203">microsoft 클라우드 피어 링 위치 (microsoft edge에 연결할 실제 위치)</span><span class="sxs-lookup"><span data-stu-id="bce47-203">Microsoft cloud peering locations (the physical locations to connect to the Microsoft edge).</span></span>
    
- <span data-ttu-id="bce47-204">Microsoft 데이터 센터 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-204">Microsoft datacenter locations.</span></span>
    
<span data-ttu-id="bce47-205">microsoft datacenter 및 클라우드 피어 링 위치는 모두 microsoft 클라우드 네트워크에 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-205">Microsoft datacenter and cloud peering locations are all connected to the Microsoft cloud network.</span></span>
  
<span data-ttu-id="bce47-206">microsoft 클라우드 피어 링 위치로가는 간 연결을 만들 때 microsoft 클라우드 네트워크와 동일한 대륙의 모든 microsoft 데이터 센터 위치에 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-206">When you create an ExpressRoute connection to a Microsoft cloud peering location, you are connected to the Microsoft cloud network and all the Microsoft datacenter locations in the same continent.</span></span> <span data-ttu-id="bce47-207">클라우드 피어 링 위치와 대상 microsoft 데이터 센터 간의 트래픽은 Microsoft 클라우드 네트워크를 통해 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-207">The traffic between the cloud peering location and the destination Microsoft datacenter is carried over the Microsoft cloud network.</span></span>
  
<span data-ttu-id="bce47-208">이로 인해 임의 연결 모델에 대 한 로컬 Microsoft 데이터 센터에 최적이 배달 되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-208">This can result in non-optimal delivery to local Microsoft datacenters for the any-to-any connectivity model.</span></span>
  
<span data-ttu-id="bce47-209">**그림 7: 단일 express 연결을 사용 하는 지리적으로 분산 된 조직의 예**</span><span class="sxs-lookup"><span data-stu-id="bce47-209">**Figure 7: Example of a geographically-distributed organization that uses a single ExpressRoute connection**</span></span>

![그림 7: 단일 express 연결을 사용 하는 지리적으로 분산 된 조직의 예](media/Network-Poster/MSNet1.png)
  
<span data-ttu-id="bce47-211">그림 7은 지역에서 미국의 북서쪽에 위치 1, 두 위치, 즉 북동쪽에 위치 2가 있는 조직을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-211">Figure 7 shows an organization with two locations, Location 1 in the northwest of the United States and Location 2 in the northeast.</span></span> <span data-ttu-id="bce47-212">모든 WAN 공급자가 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-212">They are connected by an any-to-any WAN provider.</span></span> <span data-ttu-id="bce47-213">이 조직에는 또한 경기도의 Microsoft 피어 링 위치에 대 한 간 연결이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-213">This organization also has an ExpressRoute connection to a Microsoft peering location on the west coast.</span></span> <span data-ttu-id="bce47-214">동부 해안 데이터 센터에 대 한 북동쪽 지역에 있는 위치 2의 트래픽은 조직의 모든 WAN에서 경기도로, microsoft 피어 링 위치로 이동 하 고, microsoft 클라우드 네트워크를 통해 국가 전체에서 동부 해안으로 복원 되어야 합니다. 센터가.</span><span class="sxs-lookup"><span data-stu-id="bce47-214">Traffic from Location 2 in the northeast destined for an east coast datacenter must travel all the way across the organization's WAN to the west coast, to the Microsoft peering location, and then back across the country over the Microsoft cloud network to the east coast datacenter.</span></span>
  
<span data-ttu-id="bce47-215">최적의 전달을 위해 지역 Microsoft 클라우드 피어 링 위치로의 여러 개인 설정 연결을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-215">For optimal delivery, use multiple ExpressRoute connections to regional Microsoft cloud peering locations.</span></span> 
  
<span data-ttu-id="bce47-216">**그림 8: 지역별 데이터 센터로의 최적 전달을 위한 여러 개의 express 연결 사용**</span><span class="sxs-lookup"><span data-stu-id="bce47-216">**Figure 8: The use of multiple ExpressRoute connections for optimal delivery to regional datacenters**</span></span>

![그림 8: 지역별 데이터 센터로의 최적 전달을 위한 여러 개의 express 연결 사용](media/Network-Poster/MSNet2.png)
  
<span data-ttu-id="bce47-218">그림 8에서는 각 위치에 하나씩 두 개의 지역적으로 연결을 사용 하는 동일한 조직을 보여 주고 로컬 Microsoft 피어 링 위치를 모두 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-218">Figure 8 shows the same organization with two ExpressRoute connections, one for each location, to regionally local Microsoft peering locations.</span></span> <span data-ttu-id="bce47-219">이 구성에서 동부 해안 datacenter로 향하는 북동쪽의 위치 2에 있는 트래픽은 동쪽 해안 피어 링 위치, Microsoft 클라우드 네트워크, 그리고 동쪽 해안 datacenter로 직접 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-219">In this configuration, traffic from Location 2 in the northeast destined for an east coast datacenter goes directly to an east coast peering location, to the Microsoft cloud network, and then to the east coast datacenter.</span></span>
  
<span data-ttu-id="bce47-220">여러 개의 express 연결에 다음이 제공 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-220">Multiple ExpressRoute connections can provide:</span></span>
  
- <span data-ttu-id="bce47-221">지역적으로 로컬 Microsoft 데이터 센터 위치에 대 한 성능 향상</span><span class="sxs-lookup"><span data-stu-id="bce47-221">Better performance to regionally local Microsoft datacenter locations.</span></span>
    
- <span data-ttu-id="bce47-222">로컬 express 연결을 사용할 수 없는 경우 Microsoft 클라우드로의 가용성이 향상 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-222">Higher availability to the Microsoft cloud when a local ExpressRoute connection becomes unavailable.</span></span>
    
<span data-ttu-id="bce47-223">이는 동일한 대륙의 조직에 적합 합니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-223">This works well for organizations in the same continent.</span></span> <span data-ttu-id="bce47-224">그러나 조직의 대륙 외부에 있는 Microsoft 데이터 센터에 대 한 트래픽은 인터넷을 통해 이동 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-224">However, traffic to Microsoft datacenters outside the organization's continent travels over the Internet.</span></span>
  
<span data-ttu-id="bce47-225">Microsoft 클라우드 네트워크를 통한 intercontinental 트래픽의 경우에는 express 사용자 Premium 연결을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-225">For intercontinental traffic over the Microsoft cloud network, you must use ExpressRoute Premium connections.</span></span>
  
### <a name="expressroute-premium"></a><span data-ttu-id="bce47-226">express 경로 Premium</span><span class="sxs-lookup"><span data-stu-id="bce47-226">ExpressRoute Premium</span></span>

<span data-ttu-id="bce47-227">대륙에 전역적으로 분산 된 조직의 경우,가을 프리미엄 Premium을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-227">For organizations that are globally distributed across continents, you can use ExpressRoute Premium.</span></span> 
  
<span data-ttu-id="bce47-228">가 중 Premium을 사용 하는 경우 대륙의 모든 microsoft 피어 링 위치에서 모든 microsoft 데이터 센터에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-228">With ExpressRoute Premium, you can reach any Microsoft datacenter on any continent from any Microsoft peering location on any continent.</span></span> <span data-ttu-id="bce47-229">대륙 간의 트래픽은 Microsoft 클라우드 네트워크를 통해 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-229">The traffic between continents is carried over the Microsoft cloud network.</span></span>
  
<span data-ttu-id="bce47-230">여러 개의 express Premium 연결을 사용 하는 경우 다음을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-230">With multiple ExpressRoute Premium connections, you can have:</span></span>
  
- <span data-ttu-id="bce47-231">continentally 로컬 Microsoft 데이터 센터에 대 한 향상 된 성능</span><span class="sxs-lookup"><span data-stu-id="bce47-231">Better performance to continentally local Microsoft datacenters.</span></span>
    
- <span data-ttu-id="bce47-232">로컬 express 연결을 사용할 수 없는 경우 전체 Microsoft 클라우드에 대 한 가용성 향상</span><span class="sxs-lookup"><span data-stu-id="bce47-232">Higher availability to the global Microsoft cloud when a local ExpressRoute connection becomes unavailable.</span></span>
    
<span data-ttu-id="bce47-233">비트 단위 Premium은 Office 365 기반 간 연결에 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-233">ExpressRoute Premium is required for Office 365-based ExpressRoute connections.</span></span>
  
<span data-ttu-id="bce47-234">**그림 9: world wide Microsoft 클라우드 네트워크**</span><span class="sxs-lookup"><span data-stu-id="bce47-234">**Figure 9: The world-wide Microsoft cloud network**</span></span>

![그림 9: world wide Microsoft 클라우드 네트워크](media/Network-Poster/MSNet3.png)
  
<span data-ttu-id="bce47-236">그림 9는 전 세계 대륙 및 지역에 걸친 네트워크를 포함 하는 전 세계 Microsoft 클라우드 네트워크의 논리적 다이어그램을 보여 줍니다 interconnections.</span><span class="sxs-lookup"><span data-stu-id="bce47-236">Figure 9 shows a logical diagram of the worldwide Microsoft cloud network, with networks that span the continents and regions of the world and their interconnections.</span></span> <span data-ttu-id="bce47-237">각 대륙의 Microsoft 클라우드 네트워크 부분을 사용 하 여 지역 허브 사무소에서 로컬 Microsoft 피어 링 위치로의 기본 설정 프리미엄 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-237">With a portion of the Microsoft cloud network in each continent, a global enterprise creates ExpressRoute Premium connections from its regional hub offices to local Microsoft peering locations.</span></span>
  
<span data-ttu-id="bce47-238">지역별 사무소의 경우 다음에 해당 하는 office 365 트래픽을 대상으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-238">For a regional office, appropriate Office 365 traffic to:</span></span>
  
- <span data-ttu-id="bce47-239">대륙 Office 365 데이터 센터가 대륙 내의 Microsoft 클라우드 네트워크를 통해 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-239">Continental Office 365 datacenters travels over the Microsoft cloud network within the continent.</span></span>
    
- <span data-ttu-id="bce47-240">Office 365 다른 대륙의 데이터 센터가 intercontinental Microsoft 클라우드 네트워크를 통해 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-240">Office 365 datacenters in another continent travels over the intercontinental Microsoft cloud network.</span></span>
    
<span data-ttu-id="bce47-241">자세한 내용은 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bce47-241">For more information, see:</span></span>
  
- [<span data-ttu-id="bce47-242">Office 365 교육을 위한 Azure express 경로</span><span class="sxs-lookup"><span data-stu-id="bce47-242">Azure ExpressRoute for Office 365 Training</span></span>](https://channel9.msdn.com/series/aer/)
    
- [<span data-ttu-id="bce47-243">Office 365의 네트워크 계획 및 성능 조정</span><span class="sxs-lookup"><span data-stu-id="bce47-243">Network planning and performance tuning for Office 365</span></span>](https://aka.ms/tune)
    
## <a name="expressroute-options"></a><span data-ttu-id="bce47-244">express 경로 옵션</span><span class="sxs-lookup"><span data-stu-id="bce47-244">ExpressRoute options</span></span>

<span data-ttu-id="bce47-245">또한이 경우에는 다음 옵션을 사용자의 메일 \ 배포에 통합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-245">You can also incorporate the following options into your ExpressRoute deployment:</span></span>
  
- <span data-ttu-id="bce47-246">**에 지의 보안:** 트래픽 검사 또는 침입/맬웨어 감지와 같은 거 든 지 연결을 통해 전송 및 수신 되는 트래픽에 고급 보안을 제공 하려면 DMZ 내의 트래픽 경로 또는 인트라넷 테두리에 해당 보안 장비를 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-246">**Security at your edge:** To provide advanced security for the traffic sent and received over the ExpressRoute connection, such as traffic inspection or intrusion/malware detection, place your security appliances in the traffic path within your DMZ or at the border of your intranet.</span></span>
    
- <span data-ttu-id="bce47-247">**vm에 대 한 인터넷 트래픽:** Azure vm에서 인터넷 위치를 통해 직접 트래픽을 시작 하지 못하도록 하려면 Microsoft에 기본 경로를 보급 합니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-247">**Internet traffic for VMs:** To prevent Azure VMs from initiating traffic directly with Internet locations, advertise the default route to Microsoft.</span></span> <span data-ttu-id="bce47-248">인터넷 트래픽은 모든 express 연결 및 온-프레미스 프록시 서버를 통해 라우팅됩니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-248">Traffic to the Internet is routed across the ExpressRoute connection and through your on-premises proxy servers.</span></span> <span data-ttu-id="bce47-249">azure vm에서 azure PaaS services 또는 Office 365로의 트래픽은 모든 express 연결에서 다시 라우팅됩니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-249">Traffic from Azure VMs to Azure PaaS services or Office 365 is routed back across the ExpressRoute connection.</span></span>
    
- <span data-ttu-id="bce47-250">**WAN 최적화 프로그램이:** 크로스-프레미스 Azure VNet (가상 네트워크)에 대해 사설 피어 링 연결의 양쪽에 WAN 최적화 프로그램이를 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-250">**WAN optimizers:** You can deploy WAN optimizers on both sides of a private peering connection for a cross-premises Azure virtual network (VNet).</span></span> <span data-ttu-id="bce47-251">azure VNet 내부에서 azure marketplace 및 사용자 정의 라우팅에서 WAN 최적화 네트워크 어플라이언스를 사용 하 여 기기를 통해 트래픽을 라우팅합니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-251">Inside the Azure VNet, use a WAN optimizer network appliance from the Azure marketplace and user-defined routing to route the traffic through the appliance.</span></span>
    
- <span data-ttu-id="bce47-252">**서비스 품질:** 트래픽의 IPv4 헤더에 있는 dscp (구별 된 서비스 코드 포인트) 값을 사용 하 여 음성, 비디오/대화형 또는 최상의 배달에 대해 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-252">**Quality of service:** Use Differentiated Services Code Point (DSCP) values in the IPv4 header of your traffic to mark it for voice, video/interactive, or best-effort delivery.</span></span> <span data-ttu-id="bce47-253">이는 Microsoft 피어 링 관계 및 비즈니스용 Skype Online 트래픽에 특히 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="bce47-253">This is especially important for the Microsoft peering relationship and Skype for Business Online traffic.</span></span>
    
<span data-ttu-id="bce47-254">자세한 내용은 다음 추가 리소스를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bce47-254">See these additional resources for more information:</span></span>
  
- [<span data-ttu-id="bce47-255">Office 365용 Express 경로</span><span class="sxs-lookup"><span data-stu-id="bce47-255">ExpressRoute for Office 365</span></span>](https://aka.ms/expressrouteoffice365)
    
- [<span data-ttu-id="bce47-256">Office 365 교육을 위한 Azure express 경로</span><span class="sxs-lookup"><span data-stu-id="bce47-256">Azure ExpressRoute for Office 365 Training</span></span>](https://channel9.msdn.com/series/aer/)
    
- [<span data-ttu-id="bce47-257">Azure의 express 경로</span><span class="sxs-lookup"><span data-stu-id="bce47-257">ExpressRoute for Azure</span></span>](https://azure.microsoft.com/services/expressroute/)
    
## <a name="next-step"></a><span data-ttu-id="bce47-258">다음 단계</span><span class="sxs-lookup"><span data-stu-id="bce47-258">Next step</span></span>

[<span data-ttu-id="bce47-259">Microsoft SaaS에 대한 네트워킹 디자인</span><span class="sxs-lookup"><span data-stu-id="bce47-259">Designing networking for Microsoft SaaS</span></span>](designing-networking-for-microsoft-saas.md)

## <a name="see-also"></a><span data-ttu-id="bce47-260">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bce47-260">See also</span></span>

[<span data-ttu-id="bce47-261">Microsoft Cloud Networking for Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="bce47-261">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="bce47-262">Microsoft 클라우드 IT 아키텍처 리소스</span><span class="sxs-lookup"><span data-stu-id="bce47-262">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

