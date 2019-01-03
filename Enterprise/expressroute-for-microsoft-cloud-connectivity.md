---
title: Microsoft 클라우드 연결을 위한 ExpressRoute
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/02/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: bf2295c4-d411-49cd-aaa5-116a4a456c5a
description: '요약: ExpressRoute 하는 방법 더욱 빠르고 안정적 연결을 포함 하는 Microsoft의 클라우드 서비스와 플랫폼을 이해 합니다.'
ms.openlocfilehash: b0f47278a94b2926cd540ce759ced9b2418aa598
ms.sourcegitcommit: 6e3bfe55a173a733d6696790b88efa39853ebdb9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/02/2019
ms.locfileid: "27470170"
---
# <a name="expressroute-for-microsoft-cloud-connectivity"></a><span data-ttu-id="4d887-103">Microsoft 클라우드 연결을 위한 ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="4d887-103">ExpressRoute for Microsoft cloud connectivity</span></span>

 <span data-ttu-id="4d887-104">**요약:** ExpressRoute 하는 방법 더욱 빠르고 안정적 연결을 포함 하는 Microsoft의 클라우드 서비스와 플랫폼을 이해 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-104">**Summary:** Understand how ExpressRoute can help you with faster and more reliable connections to Microsoft's cloud services and platforms.</span></span>
  
<span data-ttu-id="4d887-105">ExpressRoute는 Microsoft 클라우드에 대해 개인, 전용, 고처리량의 네트워크 연결을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-105">ExpressRoute provides a private, dedicated, high-throughput network connection to Microsoft's cloud.</span></span>
  
## <a name="expressroute-to-the-microsoft-cloud"></a><span data-ttu-id="4d887-106">Microsoft 클라우드로 ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="4d887-106">ExpressRoute to the Microsoft cloud</span></span>

<span data-ttu-id="4d887-107">ExpressRoute에 연결 하지 않고 Microsoft 클라우드 네트워킹 경로 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-107">Here is the networking path to the Microsoft cloud without an ExpressRoute connection.</span></span>
  
<span data-ttu-id="4d887-108">**그림 1: ExpressRoute가 없는 네트워킹 경로**</span><span class="sxs-lookup"><span data-stu-id="4d887-108">**Figure 1: The networking path without ExpressRoute**</span></span>

![그림 1: ExpressRoute가 없는 네트워킹 경로](media/Network-Poster/ExpressRoute.png)
  
<span data-ttu-id="4d887-p101">그림 1는 온-프레미스 네트워크 및 Microsoft 클라우드 간에 일반적인 경로 표시 합니다. WAN 통해 인터넷에 연결 하는 온-프레미스 네트워크에 지는 ISP에 대 한 링크입니다. 다음의 트래픽은 인터넷을 통해 Microsoft 클라우드의 가장자리에 있습니다. Microsoft 클라우드 내에서 클라우드 서비스에는 Office 365, Microsoft Azure, Microsoft Intune 및 Dynamics 365 포함 합니다. 조직의 사용자는 온-프레미스 네트워크 또는 인터넷에 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-p101">Figure 1 shows the typical path between an on-premises network and the Microsoft cloud. The on-premises network edge connects to the Internet through a WAN link to an ISP. The traffic then travels across the Internet to the edge of the Microsoft cloud. Cloud offerings within the Microsoft cloud include Office 365, Microsoft Azure, Microsoft Intune, and Dynamics 365. Users of an organization can be located on the on-premises network or on the Internet.</span></span>
  
<span data-ttu-id="4d887-115">부분만 ExpressRoute 연결 하지 않고 수를 제어 (하는 서비스 공급자와 관계가)은 ISP와 사용자 온-프레미스 네트워크 가장자리 사이의 연결 하 여 Microsoft 클라우드 트래픽 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-115">Without an ExpressRoute connection, the only part of the traffic path to the Microsoft cloud that you can control (and have a relationship with the service provider) is the link between your on-premises network edge and your ISP.</span></span> 
  
<span data-ttu-id="4d887-116">ISP와 Microsoft 클라우드 가장자리 사이의 경로 최상의 배달 시스템 인터넷 중단, 교통 혼잡 사실 및 악의적인 사용자가 모니터링에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-116">The path between your ISP and the Microsoft cloud edge is a best-effort delivery system on the Internet subject to outages, traffic congestion, and monitoring by malicious users.</span></span>
  
<span data-ttu-id="4d887-117">로밍 또는 원격 사용자와 같은 인터넷 사용자가 인터넷을 통해 Microsoft 클라우드 자신의 트래픽을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-117">Users on the Internet, such as roaming or remote users, send their traffic to the Microsoft cloud over the Internet.</span></span>
  
<span data-ttu-id="4d887-118">다음은 ExpressRoute 연결을 사용 하 여 Microsoft 클라우드 네트워킹 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-118">Here are the networking paths to the Microsoft cloud with an ExpressRoute connection.</span></span>
  
<span data-ttu-id="4d887-119">**그림 2: ExpressRoute 사용한 네트워킹 경로**</span><span class="sxs-lookup"><span data-stu-id="4d887-119">**Figure 2: The networking paths with ExpressRoute**</span></span>

![그림 2: ExpressRoute 사용한 네트워킹 경로](media/Network-Poster/ExpressRoute-post.png)
  
<span data-ttu-id="4d887-p102">그림 2는 두 네트워킹 경로 보여줍니다. Microsoft Intune로의 트래픽은 기본 인터넷 트래픽와 같은 경로입니다. ExpressRoute 연결, 온-프레미스 네트워크의 가장자리와 Microsoft 클라우드 가장자리 사이의 전용된 경로 통해 Office 365, Microsoft Azure 및 Dynamics 365 여행에 대 한 트래픽입니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-p102">Figure 2 shows two networking paths. Traffic to Microsoft Intune travels the same path as normal Internet traffic. Traffic to Office 365, Microsoft Azure, and Dynamics 365 travels across the ExpressRoute connection, a dedicated path between the edge of the on-premises network and the edge of the Microsoft cloud.</span></span>
  
<span data-ttu-id="4d887-p103">ExpressRoute 연결을 사용할 경우 서비스 공급자와 관계를 통해 제어 이제, microsoft 프로그램 가장자리에서 전체 트래픽 경로 통해 클라우드 지 합니다. 이 연결에는 예측 가능한 성능과 [99.95% 가동 시간 SLA](https://azure.microsoft.com/support/legal/sla/expressroute/v1_3/)제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-p103">With an ExpressRoute connection, you now have control, through a relationship with your service provider, over the entire traffic path from your edge to the Microsoft cloud edge. This connection can offer predictable performance and a [99.95% uptime SLA](https://azure.microsoft.com/support/legal/sla/expressroute/v1_3/).</span></span>
  
<span data-ttu-id="4d887-p104">이제 예측 가능한 처리량과 대기 시간을 Office 365, Azure, 및 Dynamics 365 서비스에 대 한 서비스 공급자의 연결을 기반으로 계산할 수 있습니다. 이 이번에는 Microsoft Intune에 대 한 ExpressRoute 연결 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-p104">You can now count on predictable throughput and latency, based on your service provider's connection, to Office 365, Azure, and Dynamics 365 services. ExpressRoute connections to Microsoft Intune are not supported at this time.</span></span>
  
<span data-ttu-id="4d887-128">ExpressRoute 연결을 통해 전송 되는 트래픽 더이상 인터넷 중단, 교통 혼잡 사실 및 모니터링에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-128">Traffic sent over the ExpressRoute connection is no longer subject to Internet outages, traffic congestion, and monitoring.</span></span>
  
<span data-ttu-id="4d887-p105">로밍 또는 원격 사용자와 같은 인터넷의 사용자에는 인터넷을 통해 Microsoft 클라우드 자신의 트래픽을 여전히 보냅니다. 온-프레미스 네트워크에 대 한 원격 액세스 연결을 통해 ExpressRoute 연결을 통해 전송 되는 Azure IaaS에서 호스팅되는 비즈니스 응용 프로그램의 인트라넷 라인에 대 한 트래픽은 예외가입니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-p105">Users on the Internet, such as roaming or remote users, still send their traffic to the Microsoft cloud over the Internet. One exception is traffic to an intranet line of business application hosted in Azure IaaS, which is sent over the ExpressRoute connection via a remote access connection to the on-premises network.</span></span>
  
<span data-ttu-id="4d887-131">ExpressRoute 연결의 경우와 인증서 해지 목록 확인 하 고, 일부 트래픽이 여전히 DNS 쿼리 예: 인터넷을 통해 전송 하 고 콘텐츠 배달 네트워크 (CDN)을 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-131">Even with an ExpressRoute connection, some traffic is still sent over the Internet, such as DNS queries, certificate revocation list checking, and content delivery network (CDN) requests.</span></span>
  
<span data-ttu-id="4d887-132">자세한 내용은 다음의 추가 리소스를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="4d887-132">See these additional resources for more information:</span></span>
  
- [<span data-ttu-id="4d887-133">Office 365용 ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="4d887-133">ExpressRoute for Office 365</span></span>](https://aka.ms/expressrouteoffice365)
    
- [<span data-ttu-id="4d887-134">Azure에 대 한 ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="4d887-134">ExpressRoute for Azure</span></span>](https://azure.microsoft.com/services/expressroute/)
    
## <a name="advantages-of-expressroute-for-azure"></a><span data-ttu-id="4d887-135">Azure에 대 한 ExpressRoute의 장점</span><span class="sxs-lookup"><span data-stu-id="4d887-135">Advantages of ExpressRoute for Azure</span></span>

<span data-ttu-id="4d887-136">ExpressRoute를 사용 하 여 Azure 기반 클라우드 서비스에 대 한 경우의 몇가지 이점은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-136">Here are some advantages of using ExpressRoute for Azure-based cloud services:</span></span>
  
- <span data-ttu-id="4d887-p106">**예측 가능한 성능:** Microsoft 클라우드의 가장자리를 전용된 경로 사용 하 여 성적 인터넷 공급자 중단 될 수 없는 및 인터넷 트래픽이 급격히 증가할 합니다. 확인할 수 있으며 Microsoft 클라우드 처리량과 대기 시간 SLA에 책임이 있는 공급자를 보관할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-p106">**Predictable performance:** With a dedicated path to the edge of the Microsoft cloud, your performance is not subject to Internet provider outages and spikes in Internet traffic. You can determine and hold your providers accountable to a throughput and latency SLA to the Microsoft cloud.</span></span>
    
- <span data-ttu-id="4d887-p107">**대화 트래픽에 대 한 데이터 개인정보:** 전용된 ExpressRoute 대 한 연결을 통해 보내는 트래픽을 인터넷 모니터링 또는 패킷 캡처 및 분석 악의적인 사용자에 게 영향을 받지 않습니다. 멀티 프로토콜 레이블 전환 MPLS 기반 WAN 링크를 사용 하는 것 만큼 안전 것입니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-p107">**Data privacy for your traffic:** Traffic sent over your dedicated ExpressRoute connection is not subject to Internet monitoring or packet capture and analysis by malicious users. It is as secure as using Multiprotocol Label Switching (MPLS)-based WAN links.</span></span>
    
- <span data-ttu-id="4d887-141">**높은 처리량 연결:** Exchange 공급자 및 네트워크 서비스 공급자가 ExpressRoute 연결에 대 한 전체 지원이 포함 된 최대 10 개의 g b p s 링크 Microsoft 클라우드를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-141">**High throughput connections:** With wide support for ExpressRoute connections by exchange providers and network service providers, you can obtain up to a 10 Gbps link to the Microsoft cloud.</span></span>
    
- <span data-ttu-id="4d887-142">**일부 구성에 대 한 비용 절감:** ExpressRoute 연결에는 추가 비용 변수가 이기는 하지만 일부 경우에 단일 ExpressRoute 연결 수 비용을 줄일 Microsoft 클라우드 서비스에 대 한 적절 한 처리량을 제공 하 여 조직의 여러 위치에서 인터넷 용량 증가 보다 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-142">**Lower cost for some configurations:** Although ExpressRoute connections are an additional cost, in some cases a single ExpressRoute connection can cost less than increasing your Internet capacity at multiple locations of your organization to provide adequate throughput to Microsoft cloud services.</span></span>
    
<span data-ttu-id="4d887-p108">ExpressRoute 연결 된 모든 구성에 더 높은 성능은 보장 되지 않습니다. 지역 Microsoft 데이터 센터에서 소수의 홉만 고대역폭 인터넷 연결을 보다 낮은 대역폭 ExpressRoute 연결을 통해 더 낮은 성능을 제공 하는 것이 불가능 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-p108">An ExpressRoute connection is not a guarantee of higher performance in every configuration. It is possible to have lower performance over a low-bandwidth ExpressRoute connection than a high-bandwidth Internet connection that is only a few hops away from a regional Microsoft datacenter.</span></span>
  
<span data-ttu-id="4d887-145">Office 365와 함께 ExpressRoute를 사용 하는 것에 대 한 최신 권장 사항에 대 한 [Office 365에 대 한 ExpressRoute](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd)를 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-145">For the latest recommendations for using ExpressRoute with Office 365, see [ExpressRoute for Office 365](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd).</span></span>
  
## <a name="expressroute-connectivity-models"></a><span data-ttu-id="4d887-146">ExpressRoute 연결 모델</span><span class="sxs-lookup"><span data-stu-id="4d887-146">ExpressRoute connectivity models</span></span>

<span data-ttu-id="4d887-147">표 1은 ExpressRoute 연결에 대 한 세가지 기본 연결 모델을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-147">Table 1 shows the three primary connectivity models for ExpressRoute connections.</span></span>
  
|<span data-ttu-id="4d887-148">**클라우드 exchange에 함께 배치**</span><span class="sxs-lookup"><span data-stu-id="4d887-148">**Co-located at a cloud exchange**</span></span>|<span data-ttu-id="4d887-149">**지점간 이더넷**</span><span class="sxs-lookup"><span data-stu-id="4d887-149">**Point-to-point Ethernet**</span></span>|<span data-ttu-id="4d887-150">**모든-를-모든 (IP VPN) 연결**</span><span class="sxs-lookup"><span data-stu-id="4d887-150">**Any-to-any (IP VPN) connection**</span></span>|
|:-----|:-----|:-----|
|![ExpressRoute 연결 모델: 클라우드 Exchange에 공동으로 배치됨](media/Network-Poster/ER-Conn1.png)|![ExpressRoute 연결 모델: 지점 간 이더넷](media/Network-Poster/ER-Conn2.png)|![ExpressRoute 연결 모델: Any-to-Any(IP VPN) 연결 ](media/Network-Poster/ER-Conn3.png)|
|<span data-ttu-id="4d887-154">데이터 센터는 클라우드 exchange와 시설에 있는 공동, 하는 경우에 대 한 가상 크로스-연결 공동 위치 공급자의 이더넷 exchange 통해 Microsoft 클라우드를 주문할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-154">If your datacenter is co-located in a facility with a cloud exchange, you can order a virtual cross-connection to the Microsoft cloud through the co-location provider's Ethernet exchange.</span></span>  <br/> |<span data-ttu-id="4d887-155">데이터 센터를 귀하의 구내에 있는 경우에 Microsoft 클라우드에 연결할 지점간 이더넷 링크를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-155">If your datacenter is located on your premises, you can use a point-to-point Ethernet link to connect to the Microsoft cloud.</span></span>  <br/> |<span data-ttu-id="4d887-156">이미 조직의 사이트를 연결 하려면 IP VPN (MPLS) 공급자를 사용 하는, 사용자의 개인 WAN에서 다른 위치로 처럼 작동 하는 Microsoft 클라우드에 대 한 ExpressRoute 연결.</span><span class="sxs-lookup"><span data-stu-id="4d887-156">If you are already using an IP VPN (MPLS) provider to connect the sites of your organization, an ExpressRoute connection to the Microsoft cloud acts like another location on your private WAN.</span></span>  <br/> |
   
 <span data-ttu-id="4d887-157">**표 1: ExpressRoute 연결 모델**</span><span class="sxs-lookup"><span data-stu-id="4d887-157">**Table 1: ExpressRoute connectivity models**</span></span>
  
## <a name="expressroute-peering-relationships-to-microsoft-cloud-services"></a><span data-ttu-id="4d887-158">Microsoft 클라우드 서비스에 대 한 ExpressRoute 피어 링 관계</span><span class="sxs-lookup"><span data-stu-id="4d887-158">ExpressRoute peering relationships to Microsoft cloud services</span></span>

<span data-ttu-id="4d887-p109">단일 ExpressRoute 연결 최대 2 개의 서로 다른 테두리 게이트웨이 프로토콜 (BGP) 피어 링 관계 Microsoft 클라우드의 다른 부분을 지원합니다. BPG 피어 관계를 사용 하 여 트러스트를 설정 하 고 라우팅 정보를 교환 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-p109">A single ExpressRoute connection supports up to two different Border Gateway Protocol (BGP) peering relationships to different parts of the Microsoft cloud. BPG uses peering relationships to establish trust and exchange routing information.</span></span>
  
<span data-ttu-id="4d887-161">**그림 3: 두 다른 BGP 관계에 대 한 단일 ExpressRoute 연결**</span><span class="sxs-lookup"><span data-stu-id="4d887-161">**Figure 3: The two different BGP relationships in a single ExpressRoute connection**</span></span>

![그림 3: 두 다른 BGP 관계에 대 한 단일 ExpressRoute 연결](media/Network-Poster/ERPeering.png)
  
<span data-ttu-id="4d887-p110">그림 3에 대 한 ExpressRoute 연결을 온-프레미스 네트워크에서 나옵니다. ExpressRoute 연결에는 두 논리 피어 관계에 있습니다. Microsoft SaaS 서비스를 Office 365, Dynamcs 365 및 Azure PaaS 서비스를 포함 한 Microsoft 피어 링 관계를 이동 합니다. 개인 피어 링 관계 Azure IaaS 하 고 가상 컴퓨터를 호스팅하는 가상 네트워크 게이트웨이 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-p110">Figure 3 shows an ExpressRoute connection from an on-premises network. The ExpressRoute connection has two logical peering relationships. A Microsoft peering relationship goes to Microsoft SaaS services, including Office 365, Dynamcs 365, and Azure PaaS services. A private peering relationship goes to Azure IaaS and to a virtual network gateway that hosts virtual machines.</span></span>
  
<span data-ttu-id="4d887-167">Microsoft 피어 링 BGP 관계:</span><span class="sxs-lookup"><span data-stu-id="4d887-167">The Microsoft peering BGP relationship:</span></span> 
  
- <span data-ttu-id="4d887-168">Office 365, Dynamics 365 및 Azure 서비스의 공용 주소로 DMZ에서 라우터에서 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-168">Is from a router in your DMZ to the public addresses of Office 365, Dynamics 365, and Azure services.</span></span> 
    
- <span data-ttu-id="4d887-169">양방향 시작 하는 통신을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-169">Supports bidirectional-initiated communication.</span></span>
    
<span data-ttu-id="4d887-170">개인 피어 링 BGP 관계:</span><span class="sxs-lookup"><span data-stu-id="4d887-170">The private peering BGP relationship:</span></span>
  
- <span data-ttu-id="4d887-171">Azure VNets에 할당 하는 개인 IP 주소에 조직의 네트워크의에 지에 라우터에서 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-171">Is from a router on the edge of your organization network to the private IP addresses assigned to your Azure VNets.</span></span>
    
- <span data-ttu-id="4d887-172">양방향 시작 하는 통신을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-172">Supports bidirectional-initiated communication.</span></span>
    
- <span data-ttu-id="4d887-173">조직 네트워크 내부적으로 일관 된 주소 지정 및 라우팅을 사용 하 여 전체 Microsoft 클라우드를 확장 한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-173">Is an extension of your organization network to the Microsoft cloud, complete with internally-consistent addressing and routing.</span></span>

>[!Note]
><span data-ttu-id="4d887-174">이전 버전의이 문서 뒷부분에 있는 공용 피어 링 BGP 관계는 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-174">The public peering BGP relationship described in previous versions of this article has been deprecated.</span></span>
>
    
## <a name="example-of-application-deployment-and-traffic-flow-with-expressroute"></a><span data-ttu-id="4d887-175">ExpressRoute 사용 하 여 응용 프로그램 배포 및 트래픽 흐름의 예</span><span class="sxs-lookup"><span data-stu-id="4d887-175">Example of application deployment and traffic flow with ExpressRoute</span></span>

<span data-ttu-id="4d887-p111">방법의 트래픽은 ExpressRoute 연결 전체에 걸쳐 및 Microsoft 클라우드 내에서 원본 및 대상 및 응용 프로그램 동작 간의 경로의 홉에서 경로의 함수입니다. 사이트 마다 VPN 연결을 통해는 온-프레미스 SharePoint 팜의 액세스 하는 Azure 가상 컴퓨터에서 실행 중인 응용 프로그램의 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-p111">How traffic travels across ExpressRoute connections and within the Microsoft cloud is a function of the routes at the hops of the path between the source and the destination and application behavior. Here is an example of an application running on an Azure virtual machine that accesses an on-premises SharePoint farm over a site-to-site VPN connection.</span></span>
  
<span data-ttu-id="4d887-178">**그림 4: 온-프레미스 SharePoint 팜에 액세스하는 Azure 가상 컴퓨터의 응용 프로그램**</span><span class="sxs-lookup"><span data-stu-id="4d887-178">**Figure 4: An application on an Azure virtual machine accessing an on-premises SharePoint farm**</span></span>

![그림 4: 온-프레미스 SharePoint 팜에 액세스하는 Azure 가상 컴퓨터의 응용 프로그램](media/Network-Poster/ER-App-Flow1.png)

  
<span data-ttu-id="4d887-180">그림 4에서는 응용 프로그램 서버 간에 온-프레미스 SharePoint 팜, 온-프레미스 네트워크 및 Azure IaaS, Azure IaaS 가상 컴퓨터를 사용 하는 트래픽과으로 실행 되는 응용 프로그램 서버에서에서 가상 네트워크 간의 사이트 마다 VPN 연결 흐름 및 SharePoint 팜 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-180">Figure 4 shows an on-premises SharePoint farm, a site-to-site VPN connection between the on-premises network and a virtual network in Azure IaaS, an application server running as an Azure IaaS virtual machine, and the traffic flow between the application server and the SharePoint farm.</span></span>
  
<span data-ttu-id="4d887-181">응용 프로그램의 온-프레미스 DNS를 사용 하 여 SharePoint 팜의 IP 주소를 찾아 사이트 마다 VPN 연결을 통해 모든 트래픽은 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-181">The application locates the IP address of the SharePoint farm using the on-premises DNS and all traffic goes over the site-to-site VPN connection.</span></span>
  
<span data-ttu-id="4d887-182">이 조직 Office 365의 SharePoint Online으로 온-프레미스 SharePoint 팜의 마이그레이션되며 ExpressRoute 연결을 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-182">This organization migrated their on-premises SharePoint farm to SharePoint Online in Office 365 and deployed an ExpressRoute connection.</span></span>
  
<span data-ttu-id="4d887-183">**그림 5: 온-프레미스 SharePoint 팜을 SharePoint Online으로 이동**</span><span class="sxs-lookup"><span data-stu-id="4d887-183">**Figure 5: Moving the on-premises SharePoint farm to SharePoint Online**</span></span>

![그림 5: 온-프레미스 SharePoint 팜을 SharePoint Online으로 이동](media/Network-Poster/Hairpin1.png)
  
<span data-ttu-id="4d887-p112">그림 5 표시 피어 링 관계를 가진 ExpressRoute 연결의 추가 Microsoft SaaS 및 Office 365 하 고 Azure IaaS 가상 네트워크에서 응용 프로그램 서버를 포함 합니다. SharePoint 온-프레미스 팜에 Office 365로 마이그레이션 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-p112">Figure 5 shows the addition of an ExpressRoute connection with peering relationships to Microsoft SaaS and Office 365 and to Azure IaaS containing the application server on a virtual network. The SharePoint on-premises farm has been migrated to Office 365.</span></span>
  
<span data-ttu-id="4d887-187">Microsoft 및 개인 피어 관계:</span><span class="sxs-lookup"><span data-stu-id="4d887-187">With the Microsoft and private peering relationships:</span></span>
  
- <span data-ttu-id="4d887-188">Azure 가상 네트워크 게이트웨이에서 온-프레미스 위치는 ExpressRoute 연결을 통해 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-188">From the Azure virtual network gateway, on-premises locations are available across the ExpressRoute connection.</span></span>
    
- <span data-ttu-id="4d887-189">Office 365 구독에서 프록시 서버와 같은 지 장치의 공용 IP 주소는 ExpressRoute 연결을 통해 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-189">From the Office 365 subscription, public IP addresses of edge devices, such as proxy servers, are available across the ExpressRoute connection.</span></span>
    
- <span data-ttu-id="4d887-190">온-프레미스 네트워크에서에 지, Azure VNet의 개인 IP 주소 및 Office 365의 공용 IP 주소는 사용할 수 있는 ExpressRoute 연결을 통해입니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-190">From the on-premises network edge, the private IP addresses of the Azure VNet and the public IP addresses of Office 365 are available across the ExpressRoute connection.</span></span>
    
<span data-ttu-id="4d887-191">응용 프로그램 액세스 하는 Url의 SharePoint Online, 프록시 서버는 지에 ExpressRoute 연결을 통해 해당 트래픽을 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-191">When the application accesses the URLs of SharePoint Online, it forwards its traffic across the ExpressRoute connection to a proxy server in the edge.</span></span> 
  
<span data-ttu-id="4d887-p113">프록시 서버에서 SharePoint Online의 IP 주소를 찾으면 ExpressRoute 연결을 통해 다시 트래픽을 전달 합니다. 응답 트래픽은 역방향 경로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-p113">When the proxy server locates the IP address of SharePoint Online, it forwards the traffic back over the ExpressRoute connection. Response traffic travels the reverse path.</span></span>
  
<span data-ttu-id="4d887-194">**그림 6: SharePoint 팜이 Office 365의 SharePoint Online으로 마이그레이션되었을 때의 트래픽 흐름**</span><span class="sxs-lookup"><span data-stu-id="4d887-194">**Figure 6: Traffic flow when the SharePoint farm has been migrated to SharePoint Online in Office 365**</span></span>

![그림 6: SharePoint 팜이 Office 365의 SharePoint Online으로 마이그레이션되었을 때의 트래픽 흐름](media/Network-Poster/Hairpin2.png)

  
<span data-ttu-id="4d887-196">그림 6 응용 프로그램 서버와 Office 365의 SharePoint Online 간의 트래픽을 개인 피어 링 관계 온-프레미스 네트워크 경계를 응용 프로그램 서버에서 한 가장자리에서 다음을 통해 Microsoft 피어 링 관계를 통해 흐르는 하는 방법을 보여줍니다. Office 365 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-196">Figure 6 shows how the traffic between the application server and SharePoint Online in Office 365 flows over the private peering relationship from the application server to the on-premises network edge, and then from the edge over the Microsoft peering relationship to Office 365.</span></span>
  
<span data-ttu-id="4d887-197">라우팅 및 응용 프로그램 동작의 결과 고정 하는 머리가 반환이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-197">The result is hair pinning, a consequence of the routing and application behavior.</span></span>
  
## <a name="expressroute-and-microsofts-cloud-network"></a><span data-ttu-id="4d887-198">ExpressRoute 및 Microsoft의 클라우드 네트워크</span><span class="sxs-lookup"><span data-stu-id="4d887-198">ExpressRoute and Microsoft's cloud network</span></span>

<span data-ttu-id="4d887-199">ExpressRoute 연결 서로 다른 두 버전에서 사용할 수 있는: ExpressRoute 및 ExpressRoute 프리미엄 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-199">ExpressRoute connections are available in two different versions: ExpressRoute and ExpressRoute Premium.</span></span>
  
### <a name="expressroute"></a><span data-ttu-id="4d887-200">ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="4d887-200">ExpressRoute</span></span>

<span data-ttu-id="4d887-201">방법의 트래픽은 조직 네트워크 사이의 Microsoft 데이터 센터의 조합입니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-201">How traffic travels between your organization network and a Microsoft datacenter is a combination of:</span></span>
  
- <span data-ttu-id="4d887-202">사용자 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-202">Your locations.</span></span>
    
- <span data-ttu-id="4d887-203">Microsoft 클라우드 피어 링 위치 (Microsoft 지에 연결 하는 실제 위치).</span><span class="sxs-lookup"><span data-stu-id="4d887-203">Microsoft cloud peering locations (the physical locations to connect to the Microsoft edge).</span></span>
    
- <span data-ttu-id="4d887-204">Microsoft 데이터 센터 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-204">Microsoft datacenter locations.</span></span>
    
<span data-ttu-id="4d887-205">Microsoft 데이터 센터 및 위치를 피어 링 클라우드는 모든 Microsoft 클라우드 네트워크에 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-205">Microsoft datacenter and cloud peering locations are all connected to the Microsoft cloud network.</span></span>
  
<span data-ttu-id="4d887-p114">Microsoft 클라우드 피어 링 위치에 대 한 ExpressRoute 연결을 만들 때에 Microsoft 클라우드 네트워크와 동일한 대륙의 모든 Microsoft 데이터 센터 위치에 연결 된 있습니다. Microsoft 클라우드 네트워크를 통해 클라우드 피어 링 위치와 대상 Microsoft 데이터 센터 간의 트래픽의 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-p114">When you create an ExpressRoute connection to a Microsoft cloud peering location, you are connected to the Microsoft cloud network and all the Microsoft datacenter locations in the same continent. The traffic between the cloud peering location and the destination Microsoft datacenter is carried over the Microsoft cloud network.</span></span>
  
<span data-ttu-id="4d887-208">이 모든-를-모든 연결 모델에 대 한 로컬 Microsoft 데이터 센터에 최적이 아닌 배달 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-208">This can result in non-optimal delivery to local Microsoft datacenters for the any-to-any connectivity model.</span></span>
  
<span data-ttu-id="4d887-209">**단일 ExpressRoute 연결을 사용 하는 지리적으로 분산 된 조직의 그림 7: 예**</span><span class="sxs-lookup"><span data-stu-id="4d887-209">**Figure 7: Example of a geographically-distributed organization that uses a single ExpressRoute connection**</span></span>

![단일 ExpressRoute 연결을 사용 하는 지리적으로 분산 된 조직의 그림 7: 예](media/Network-Poster/MSNet1.png)
  
<span data-ttu-id="4d887-p115">그림 7 두 위치와 조직 미국, 대한민국 북서쪽에서 위치 1 및 북동쪽에서 위치 2를 보여줍니다. 모든-를-모든 WAN 공급자에서 연결 합니다. 이 조직에 서울에 Microsoft 피어 링 위치로 ExpressRoute 연결이 합니다. 위치 2에서는 동부 지역 데이터 센터에 대해 북동쪽에서 해야 서 부 지역 Microsoft 피어 링 위치에 이르는 모든 조직의 WAN에서 출장 트래픽과 했다가 다시 국가에서 Microsoft 클라우드 네트워크를 통해 동부 데이터 센터입니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-p115">Figure 7 shows an organization with two locations, Location 1 in the northwest of the United States and Location 2 in the northeast. They are connected by an any-to-any WAN provider. This organization also has an ExpressRoute connection to a Microsoft peering location on the west coast. Traffic from Location 2 in the northeast destined for an east coast datacenter must travel all the way across the organization's WAN to the west coast, to the Microsoft peering location, and then back across the country over the Microsoft cloud network to the east coast datacenter.</span></span>
  
<span data-ttu-id="4d887-215">최적의 배달에 대 한 지역 Microsoft 클라우드 피어 링 위치를 여러 ExpressRoute 연결을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-215">For optimal delivery, use multiple ExpressRoute connections to regional Microsoft cloud peering locations.</span></span> 
  
<span data-ttu-id="4d887-216">**그림 8: 지역 데이터 센터로의 최적 전달을 위한 여러 개의 ExpressRoute 연결 사용**</span><span class="sxs-lookup"><span data-stu-id="4d887-216">**Figure 8: The use of multiple ExpressRoute connections for optimal delivery to regional datacenters**</span></span>

![그림 8: 지역 데이터 센터로의 최적 전달을 위한 여러 개의 ExpressRoute 연결 사용](media/Network-Poster/MSNet2.png)
  
<span data-ttu-id="4d887-p116">그림 8 지역별로 로컬 Microsoft 피어 링 위치를 각 위치에 대 한 두 ExpressRoute 연결 된 동일한 조직에 나와 있습니다. 이 구성에서 위치 2에서는 동부 지역 데이터 센터에 대해 북동쪽에서 트래픽은 동부 피어 링 위치에 직접, Microsoft 클라우드 네트워크를 다음 동부 지역 데이터 센터에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-p116">Figure 8 shows the same organization with two ExpressRoute connections, one for each location, to regionally local Microsoft peering locations. In this configuration, traffic from Location 2 in the northeast destined for an east coast datacenter goes directly to an east coast peering location, to the Microsoft cloud network, and then to the east coast datacenter.</span></span>
  
<span data-ttu-id="4d887-220">여러 ExpressRoute 연결을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-220">Multiple ExpressRoute connections can provide:</span></span>
  
- <span data-ttu-id="4d887-221">지역별로 로컬 Microsoft 데이터 센터 위치를 성능이 향상 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-221">Better performance to regionally local Microsoft datacenter locations.</span></span>
    
- <span data-ttu-id="4d887-222">로컬 ExpressRoute 연결을 사용할 수 없게 하는 경우 Microsoft 클라우드로 가용성을 향상 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-222">Higher availability to the Microsoft cloud when a local ExpressRoute connection becomes unavailable.</span></span>
    
<span data-ttu-id="4d887-p117">이 동일한 대륙에는 조직에 적합 한 작동합니다. 그러나 조직의 대륙 외부 Microsoft 데이터 센터에 대 한 트래픽 인터넷을 통해 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-p117">This works well for organizations in the same continent. However, traffic to Microsoft datacenters outside the organization's continent travels over the Internet.</span></span>
  
<span data-ttu-id="4d887-225">Microsoft 클라우드 네트워크를 통해 intercontinental 트래픽에 대 한 ExpressRoute 프리미엄 연결을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-225">For intercontinental traffic over the Microsoft cloud network, you must use ExpressRoute Premium connections.</span></span>
  
### <a name="expressroute-premium"></a><span data-ttu-id="4d887-226">ExpressRoute 프리미엄</span><span class="sxs-lookup"><span data-stu-id="4d887-226">ExpressRoute Premium</span></span>

<span data-ttu-id="4d887-227">대륙에 분산 전역적으로 하는 조직에서는 ExpressRoute Premium을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-227">For organizations that are globally distributed across continents, you can use ExpressRoute Premium.</span></span> 
  
<span data-ttu-id="4d887-p118">ExpressRoute 프리미엄와 모든 대륙에 어떤 Microsoft 피어 링 위치에서 모든 대륙에 모든 Microsoft 데이터 센터에 도달할 수 있습니다. 대륙 간의 트래픽은 Microsoft 클라우드 네트워크를 통해 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-p118">With ExpressRoute Premium, you can reach any Microsoft datacenter on any continent from any Microsoft peering location on any continent. The traffic between continents is carried over the Microsoft cloud network.</span></span>
  
<span data-ttu-id="4d887-230">여러 ExpressRoute 프리미엄 연결이 설정 된 다음을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-230">With multiple ExpressRoute Premium connections, you can have:</span></span>
  
- <span data-ttu-id="4d887-231">Continentally 로컬 Microsoft 데이터 센터에 성능이 향상 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-231">Better performance to continentally local Microsoft datacenters.</span></span>
    
- <span data-ttu-id="4d887-232">로컬 ExpressRoute 연결을 사용할 수 없게 하는 경우 전역 Microsoft 클라우드로 가용성을 향상 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-232">Higher availability to the global Microsoft cloud when a local ExpressRoute connection becomes unavailable.</span></span>
    
<span data-ttu-id="4d887-233">ExpressRoute 프리미엄 Office 365 기반 ExpressRoute 연결에 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-233">ExpressRoute Premium is required for Office 365-based ExpressRoute connections.</span></span>
  
<span data-ttu-id="4d887-234">**전세계 Microsoft 클라우드 네트워크의 그림 9:**</span><span class="sxs-lookup"><span data-stu-id="4d887-234">**Figure 9: The world-wide Microsoft cloud network**</span></span>

![전세계 Microsoft 클라우드 네트워크의 그림 9:](media/Network-Poster/MSNet3.png)
  
<span data-ttu-id="4d887-p119">그림 9 대륙 및 세계와의 상호 연결의 지역에 걸쳐 있는 네트워크를 사용 하 여 전세계 Microsoft 클라우드 네트워크의 논리 다이어그램을 보여줍니다. 각 대륙에 Microsoft 클라우드 네트워크의 부분을 함께 글로벌 엔터프라이즈 연결을 만듦 ExpressRoute 프리미엄 해당 지역 허브 사무실에서 로컬 Microsoft 피어 링 위치를</span><span class="sxs-lookup"><span data-stu-id="4d887-p119">Figure 9 shows a logical diagram of the worldwide Microsoft cloud network, with networks that span the continents and regions of the world and their interconnections. With a portion of the Microsoft cloud network in each continent, a global enterprise creates ExpressRoute Premium connections from its regional hub offices to local Microsoft peering locations.</span></span>
  
<span data-ttu-id="4d887-238">지역 사무소에 대 한 Office 365 트래픽을 적절 한:</span><span class="sxs-lookup"><span data-stu-id="4d887-238">For a regional office, appropriate Office 365 traffic to:</span></span>
  
- <span data-ttu-id="4d887-239">Office 365 데이터 센터를 대륙 대륙 내에서 Microsoft 클라우드 네트워크를 통해 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-239">Continental Office 365 datacenters travels over the Microsoft cloud network within the continent.</span></span>
    
- <span data-ttu-id="4d887-240">다른 대륙에 office 365 데이터 센터 intercontinental Microsoft 클라우드 네트워크를 통해 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-240">Office 365 datacenters in another continent travels over the intercontinental Microsoft cloud network.</span></span>
    
<span data-ttu-id="4d887-241">자세한 내용은 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4d887-241">For more information, see:</span></span>
  
- [<span data-ttu-id="4d887-242">Office 365 교육에 대 한 azure ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="4d887-242">Azure ExpressRoute for Office 365 Training</span></span>](https://channel9.msdn.com/series/aer/)
    
- [<span data-ttu-id="4d887-243">Office 365의 네트워크 계획 및 성능 조정</span><span class="sxs-lookup"><span data-stu-id="4d887-243">Network planning and performance tuning for Office 365</span></span>](https://aka.ms/tune)
    
- [<span data-ttu-id="4d887-244">Office 365 성능 관리</span><span class="sxs-lookup"><span data-stu-id="4d887-244">Office 365 Performance Management</span></span>](https://mva.microsoft.com/en-US/training-courses/office-365-performance-management-8416)
    
## <a name="expressroute-options"></a><span data-ttu-id="4d887-245">ExpressRoute 옵션</span><span class="sxs-lookup"><span data-stu-id="4d887-245">ExpressRoute options</span></span>

<span data-ttu-id="4d887-246">또한 ExpressRoute 배포는 다음 옵션을 통합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-246">You can also incorporate the following options into your ExpressRoute deployment:</span></span>
  
- <span data-ttu-id="4d887-247">**에 지에 대 한 보안:** 예: 트래픽 검사 또는 침입/맬웨어 감지 ExpressRoute 연결을 통해 보내고 받은 트래픽에 대 한 고급 보안을 제공 하려면 보안 어플라이언스 DMZ 내에서 또는 인트라넷의 테두리에 트래픽 경로에 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-247">**Security at your edge:** To provide advanced security for the traffic sent and received over the ExpressRoute connection, such as traffic inspection or intrusion/malware detection, place your security appliances in the traffic path within your DMZ or at the border of your intranet.</span></span>
    
- <span data-ttu-id="4d887-p120">**Vm에 대 한 인터넷 트래픽을:** Azure Vm 인터넷 위치를 사용 하 여 직접 트래픽을 시작 하지 못하도록 하려면 Microsoft에 기본 경로를 알립니다. 인터넷에 대 한 트래픽 ExpressRoute 연결을 통해 및 온-프레미스 프록시 서버를 통해 라우팅됩니다. Azure Vm 트래픽은 Azure PaaS 서비스 또는 Office 365 ExpressRoute 연결을 통해 다시 라우팅됩니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-p120">**Internet traffic for VMs:** To prevent Azure VMs from initiating traffic directly with Internet locations, advertise the default route to Microsoft. Traffic to the Internet is routed across the ExpressRoute connection and through your on-premises proxy servers. Traffic from Azure VMs to Azure PaaS services or Office 365 is routed back across the ExpressRoute connection.</span></span>
    
- <span data-ttu-id="4d887-p121">**WAN 최적화 프로그램이:** 크로스-프레미스 Azure에 대 한 개인 피어 링 연결의 양쪽에 WAN 최적화 프로그램이 배포할 수 가상 네트워크 (VNet). Azure VNet 내부 Azure 마켓플레이스 및 라우팅 사용자 정의에서 WAN 최적화 프로그램이 네트워크 기기 기기를 통해 트래픽을 라우팅 하는데 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-p121">**WAN optimizers:** You can deploy WAN optimizers on both sides of a private peering connection for a cross-premises Azure virtual network (VNet). Inside the Azure VNet, use a WAN optimizer network appliance from the Azure marketplace and user-defined routing to route the traffic through the appliance.</span></span>
    
- <span data-ttu-id="4d887-p122">**서비스의 품질:** IPv4 헤더의 트래픽 코드 포인트 DSCP (Differentiated Services) 값을 사용 하 여 음성, 비디오/대화형, 또는 최상의 배달에 대 한 표시 합니다. 이 비즈니스 온라인 트래픽에 대 한 Microsoft 피어 링 관계 및 Skype 특히 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d887-p122">**Quality of service:** Use Differentiated Services Code Point (DSCP) values in the IPv4 header of your traffic to mark it for voice, video/interactive, or best-effort delivery. This is especially important for the Microsoft peering relationship and Skype for Business Online traffic.</span></span>
    
<span data-ttu-id="4d887-255">자세한 내용은 다음의 추가 리소스를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="4d887-255">See these additional resources for more information:</span></span>
  
- [<span data-ttu-id="4d887-256">Office 365용 ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="4d887-256">ExpressRoute for Office 365</span></span>](https://aka.ms/expressrouteoffice365)
    
- [<span data-ttu-id="4d887-257">Office 365 교육에 대 한 azure ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="4d887-257">Azure ExpressRoute for Office 365 Training</span></span>](https://channel9.msdn.com/series/aer/)
    
- [<span data-ttu-id="4d887-258">Azure에 대 한 ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="4d887-258">ExpressRoute for Azure</span></span>](https://azure.microsoft.com/services/expressroute/)
    
## <a name="next-step"></a><span data-ttu-id="4d887-259">다음 단계</span><span class="sxs-lookup"><span data-stu-id="4d887-259">Next step</span></span>

[<span data-ttu-id="4d887-260">Microsoft SaaS에 대한 네트워킹 디자인</span><span class="sxs-lookup"><span data-stu-id="4d887-260">Designing networking for Microsoft SaaS</span></span>](designing-networking-for-microsoft-saas.md)

## <a name="see-also"></a><span data-ttu-id="4d887-261">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4d887-261">See also</span></span>

[<span data-ttu-id="4d887-262">Microsoft Cloud Networking for Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="4d887-262">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="4d887-263">Microsoft 클라우드 IT 아키텍처 리소스</span><span class="sxs-lookup"><span data-stu-id="4d887-263">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

