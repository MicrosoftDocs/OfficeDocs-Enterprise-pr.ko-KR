---
title: 클라우드 연결을 위해 네트워크 확장
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
ms.assetid: 83e2859a-c673-47c4-880a-01cdfdadb93e
description: '요약: 클라우드 채택 네트워크 인프라 투자를 하는 새로운 방법이 필요 하는 방법을 이해 합니다.'
ms.openlocfilehash: c8fba120292b89894850312a84fd6067d925a07f
ms.sourcegitcommit: 25a022f4ef4e56c5407e8e3a8a34265f8fc94264
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/29/2018
ms.locfileid: "26872259"
---
# <a name="evolving-your-network-for-cloud-connectivity"></a><span data-ttu-id="1fbf0-103">클라우드 연결을 위해 네트워크 확장</span><span class="sxs-lookup"><span data-stu-id="1fbf0-103">Evolving your network for cloud connectivity</span></span>

 <span data-ttu-id="1fbf0-104">**요약:** 클라우드 채택 네트워크 인프라 투자를 하는 새로운 방법이 필요 하는 방법을 이해 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fbf0-104">**Summary:** Understand how cloud adoption requires a new approach to network infrastructure investments.</span></span>
  
<span data-ttu-id="1fbf0-p101">클라우드 마이그레이션으로 인해 회사 네트워크 내부 및 외부의 트래픽 흐름 양과 특성이 달라지고 있습니다. 또한 보안 위험을 완화시키는 방법도 영향을 받고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1fbf0-p101">Cloud migration changes the volume and nature of traffic flows within and outside a corporate network. It also affects approaches to mitigating security risk.</span></span>
  
- <span data-ttu-id="1fbf0-107">클라우드 하기 전에</span><span class="sxs-lookup"><span data-stu-id="1fbf0-107">Before the cloud</span></span>
    
    <span data-ttu-id="1fbf0-p102">대화 가능, 신뢰할 수 있는지 확인 하 고 온-프레미스 데이터 센터에 대 한 성능이 연결에 소요 되는 대부분 네트워킹 인프라 투자 했습니다. 대부분의 조직에 대 한 인터넷 연결 내부 비즈니스 작업에 대 한 중요 한 없습니다. 네트워크 경계 보안 위반에 대 한 기본 방어 했습니다.</span><span class="sxs-lookup"><span data-stu-id="1fbf0-p102">Most networking infrastructure investments were spent on ensuring available, reliable, and performant connectivity to on-premises datacenters. For many organizations, Internet connectivity was not critical for internal business operations. Network boundaries were primary defenses against security breaches.</span></span>
    
- <span data-ttu-id="1fbf0-111">클라우드 후</span><span class="sxs-lookup"><span data-stu-id="1fbf0-111">After the cloud</span></span>
    
    <span data-ttu-id="1fbf0-p103">새로 추가 되거나 마이그레이션된 생산성 및 클라우드에서 실행 되는 IT 작업 부하를 인프라 투자에서 shift 온-프레미스 내부 비즈니스 작업에 대 한 중요 한 이제는 인터넷 연결을 데이터 센터입니다. 페더레이션된 연결 네트워크와 Microsoft 클라우드 서비스에 대 한 연결 지점을 통해 흐를 때 id 및 데이터를 보호 하기 위해 보안 전략을 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fbf0-p103">With new and migrated productivity and IT workloads running in the cloud, infrastructure investments shift from on-premises datacenters to Internet connectivity, which is now critical for internal business operations. Federated connectivity shifts security strategy to protecting identities and data as they flow through the network and points of connectivity to Microsoft cloud services.</span></span>
    
<span data-ttu-id="1fbf0-p104">네트워크 인프라 투자 연결으로 시작 합니다. 추가로 투자 클라우드 서비스의 종류에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="1fbf0-p104">Network infrastructure investments begin with connectivity. Additional investments depend on the category of cloud service.</span></span>
  
- <span data-ttu-id="1fbf0-p105">**Software as a Service (SaaS)** Microsoft SaaS 서비스는 Office 365, Microsoft Intune 및 Microsoft Dynamics 365 포함 됩니다. 사용자가 SaaS 서비스의 성공적인 채택 했는지에 따라 항상 사용 가능 하 고 성능이 연결에서 인터넷 또는 Microsoft 클라우드 서비스에 직접 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fbf0-p105">**Software as a Service (SaaS)** Microsoft SaaS services include Office 365, Microsoft Intune, and Microsoft Dynamics 365. Successful adoption of SaaS services by users depends on highly-available and performant connectivity to the Internet, or directly to Microsoft cloud services.</span></span>
    
    <span data-ttu-id="1fbf0-p106">네트워크 아키텍처 안정적이 고 중복 연결 및 충분 한 대역폭에 중점을 둡니다. 진행 중인 투자 성능 모니터링 및 튜닝을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fbf0-p106">Network architecture focuses on reliable, redundant connectivity and ample bandwidth. Ongoing investments include performance monitoring and tuning.</span></span>
    
- <span data-ttu-id="1fbf0-p107">**서비스 (PaaS)으로 azure 플랫폼** Microsoft SaaS 서비스에 대 한 투자를 외에도 다중 사이트 또는 지리적으로 분산 된 PaaS 응용 프로그램은 클라이언트 트래픽을 분산 하기 위해 Azure 트래픽 관리자 설계 필요할 수 있습니다. 진행 중인 투자 성능 및 트래픽 배포 모니터링 및 장애 조치 테스트를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fbf0-p107">**Azure Platform as a Service (PaaS)** In addition to the investments for Microsoft SaaS services, multi-site or geographically distributed PaaS applications might require architecting Azure Traffic Manager to distribute client traffic. Ongoing investments include performance and traffic distribution monitoring and failover testing.</span></span>
    
- <span data-ttu-id="1fbf0-p108">**Azure 인프라 서비스 (IaaS)** Microsoft SaaS 및 PaaS 서비스에 대 한 투자를 외에도 디자인 필요 IaaS에서 IT 작업 부하를 실행 하 고 해당 가상 컴퓨터를 호스팅할, 고, 라우팅, IP를 실행 하는 응용 프로그램에 대 한 보안 연결 구성 azure 가상 네트워크 주소 지정, DNS 및 부하 분산 진행 중인 투자 성능과 보안을 모니터링 하 고 문제를 해결을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fbf0-p108">**Azure Infrastructure as a Service (IaaS)** In addition to the investments for Microsoft SaaS and PaaS services, running IT workloads in IaaS requires the design and configuration of Azure virtual networks that host virtual machines, secure connectivity to applications running on them, routing, IP addressing, DNS, and load balancing. Ongoing investments include performance and security monitoring and troubleshooting.</span></span>

<span data-ttu-id="1fbf0-p109">[Microsoft 365](https://www.microsoft.com/microsoft-365) 은 Office 365, 엔터프라이즈 관리 + 보안 (EMS) 및 Windows 10의 조합입니다. 여러 SaaS 및 Azure 서비스 하는 모든 사용자가 수 기업용 완료, 지능적인 솔루션에 대 한 Microsoft 365 결합 하 고 안전 하 게 공동 작업 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fbf0-p109">[Microsoft 365](https://www.microsoft.com/microsoft-365) is a combination of Office 365, Enterprise Management + Security (EMS), and Windows 10. Microsoft 365 combines multiple SaaS and Azure services for a complete, intelligent solution that empowers everyone to be creative and work together securely.</span></span>
    
## <a name="areas-of-networking-investment-for-success-in-the-cloud"></a><span data-ttu-id="1fbf0-126">클라우드에서 성공에 대 한 투자 네트워킹의 영역</span><span class="sxs-lookup"><span data-stu-id="1fbf0-126">Areas of networking investment for success in the cloud</span></span>

<span data-ttu-id="1fbf0-p110">엔터프라이즈 조직 인트라넷 간에 네트워크 처리량을 최적화 하 고 인터넷 조직적인 접근 방식을 취하고에서 활용 합니다. 또한 ExpressRoute 연결에서 이점을 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1fbf0-p110">Enterprise organizations benefit from taking a methodical approach to optimizing network throughput across your intranet and to the Internet. You might also benefit from an ExpressRoute connection.</span></span>
  
### <a name="optimize-intranet-connectivity-to-your-edge-network"></a><span data-ttu-id="1fbf0-129">경계 네트워크에 대 한 인트라넷 연결을 최적화 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fbf0-129">Optimize intranet connectivity to your edge network</span></span>

<span data-ttu-id="1fbf0-p111">년 동안 대부분의 조직에서는 인트라넷 연결 및 온-프레미스 데이터 센터에서 실행 되는 응용 프로그램에 대 한 성능 최적화가. 생산성과 Microsoft 클라우드를 실행 하는 IT 작업 추가 투자 높은 연결 가용성을 확인 해야 하 고 지 네트워크와 인트라넷 사용자 간의 트래픽을 성능에 주는 최적이 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fbf0-p111">Over the years, many organizations have optimized intranet connectivity and performance to applications running in on-premises datacenters. With productivity and IT workloads running in the Microsoft cloud, additional investment must ensure high connectivity availability and that traffic performance between your edge network and your intranet users is optimal.</span></span>
  
### <a name="optimize-throughput-at-your-edge-network"></a><span data-ttu-id="1fbf0-132">경계 네트워크의 처리량을 최적화 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fbf0-132">Optimize throughput at your edge network</span></span>

<span data-ttu-id="1fbf0-133">일상적인 생산성 트래픽 여행 클라우드로의 기타를으로 최신 해야 고가용성을 제공 하 고, 최고 부하를 충족 하기 위한 충분 한 공간이를 경계 네트워크에 시스템의 집합을 밀접 하 게 검토 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fbf0-133">As more of your day-to-day productivity traffic travels to the cloud, you should closely examine the set of systems at your edge network to ensure that they are current, provide high availability, and have sufficient capacity to meet peak loads.</span></span>
  
### <a name="for-a-high-sla-to-azure-office-365-and-dynamics-365-use-expressroute"></a><span data-ttu-id="1fbf0-134">Azure에 높은 SLA에 대 한 Office 365 및 Dynamics 365 ExpressRoute 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1fbf0-134">For a high SLA to Azure, Office 365, and Dynamics 365, use ExpressRoute</span></span>

<span data-ttu-id="1fbf0-p112">경계 네트워크에서 사용자의 현재 인터넷 연결을 사용할 수 있지만 Microsoft 클라우드 서비스 간에 트래픽을 인터넷 하려고 하는 다른 인트라넷 트래픽과 파이프를 공유 해야 합니다. 또한 Microsoft 클라우드 서비스에 대 한 트래픽을 인터넷 교통 혼잡 사실을 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="1fbf0-p112">Although you can use your current Internet connection from your edge network, traffic to and from Microsoft cloud services must share the pipe with other intranet traffic going to the Internet. Additionally, your traffic to Microsoft cloud services is subject to Internet traffic congestion.</span></span>
  
<span data-ttu-id="1fbf0-137">높은 SLA 및 최상의 성능을 ExpressRoute, 네트워크 및 Azure, Office 365, Dynamics 365 또는 모든 3 사이는 전용된 WAN 연결을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fbf0-137">For a high SLA and the best performance, use ExpressRoute, a dedicated WAN connection between your network and Azure, Office 365, Dynamics 365, or all three.</span></span> 
  
<span data-ttu-id="1fbf0-p113">ExpressRoute 전용된 연결에 대 한 기존 네트워크 공급자를 활용할 수 있습니다. 리소스 ExpressRoute 하 여 연결 된 조직에서는 지리적으로 분산 된 경우에 사용자의 WAN에 있는 것 처럼 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1fbf0-p113">ExpressRoute can leverage your existing network provider for a dedicated connection. Resources connected by ExpressRoute appear as if they are on your WAN, even for geographically-distributed organizations.</span></span>
  
<span data-ttu-id="1fbf0-140">자세한 내용은 [Microsoft 클라우드 연결에 대 한 ExpressRoute](expressroute-for-microsoft-cloud-connectivity.md)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="1fbf0-140">For more information, see [ExpressRoute for Microsoft cloud connectivity](expressroute-for-microsoft-cloud-connectivity.md).</span></span>
  
## <a name="scope-of-network-investments"></a><span data-ttu-id="1fbf0-141">네트워크 투자의 범위</span><span class="sxs-lookup"><span data-stu-id="1fbf0-141">Scope of network investments</span></span>

<span data-ttu-id="1fbf0-p114">네트워크 투자의 범위는 클라우드 서비스의 종류에 따라 달라 집니다. Microsoft의 클라우드 간에 투자 최대화 하는 팀이 네트워킹의 투자 합니다. 예, IaaS 서비스에 대 한 투자 모든 투자 영역에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1fbf0-p114">The scope of network investments depend on the category of cloud service. Investing across Microsoft's cloud maximizes the investments of networking teams. For example, investments for IaaS services apply to all investment areas.</span></span>
  
|||||
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="1fbf0-145">투자 영역</span><span class="sxs-lookup"><span data-stu-id="1fbf0-145">Investment area</span></span>  <br/> |<span data-ttu-id="1fbf0-146">SaaS</span><span class="sxs-lookup"><span data-stu-id="1fbf0-146">SaaS</span></span>  <br/> |<span data-ttu-id="1fbf0-147">PaaS</span><span class="sxs-lookup"><span data-stu-id="1fbf0-147">PaaS</span></span>  <br/> |<span data-ttu-id="1fbf0-148">IaaS</span><span class="sxs-lookup"><span data-stu-id="1fbf0-148">IaaS</span></span>  <br/> |
|<span data-ttu-id="1fbf0-149">충분 한 대역폭을 사용한 설계자 안정적이 고 중복 인터넷 연결</span><span class="sxs-lookup"><span data-stu-id="1fbf0-149">Architect reliable, redundant Internet connectivity with ample bandwidth</span></span>  <br/> |<span data-ttu-id="1fbf0-150">적용</span><span class="sxs-lookup"><span data-stu-id="1fbf0-150">Applies</span></span>  <br/> |<span data-ttu-id="1fbf0-151">적용</span><span class="sxs-lookup"><span data-stu-id="1fbf0-151">Applies</span></span>  <br/> |<span data-ttu-id="1fbf0-152">적용</span><span class="sxs-lookup"><span data-stu-id="1fbf0-152">Applies</span></span>  <br/> |
|<span data-ttu-id="1fbf0-153">모니터링 및 성능에 대 한 인터넷 처리량 조정</span><span class="sxs-lookup"><span data-stu-id="1fbf0-153">Monitor and tune Internet throughput for performance</span></span>  <br/> |<span data-ttu-id="1fbf0-154">적용</span><span class="sxs-lookup"><span data-stu-id="1fbf0-154">Applies</span></span>  <br/> |<span data-ttu-id="1fbf0-155">적용</span><span class="sxs-lookup"><span data-stu-id="1fbf0-155">Applies</span></span>  <br/> |<span data-ttu-id="1fbf0-156">적용</span><span class="sxs-lookup"><span data-stu-id="1fbf0-156">Applies</span></span>  <br/> |
|<span data-ttu-id="1fbf0-157">인터넷 연결 및 처리량 문제를 해결</span><span class="sxs-lookup"><span data-stu-id="1fbf0-157">Troubleshoot Internet connectivity and throughput issues</span></span>  <br/> |<span data-ttu-id="1fbf0-158">적용</span><span class="sxs-lookup"><span data-stu-id="1fbf0-158">Applies</span></span>  <br/> |<span data-ttu-id="1fbf0-159">적용</span><span class="sxs-lookup"><span data-stu-id="1fbf0-159">Applies</span></span>  <br/> |<span data-ttu-id="1fbf0-160">적용</span><span class="sxs-lookup"><span data-stu-id="1fbf0-160">Applies</span></span>  <br/> |
|<span data-ttu-id="1fbf0-161">다른 끝점에 대 한 분산 트래픽 부하를 디자인 Azure 트래픽 관리자</span><span class="sxs-lookup"><span data-stu-id="1fbf0-161">Design Azure Traffic Manager to load balance traffic to different endpoints</span></span>  <br/> ||<span data-ttu-id="1fbf0-162">적용</span><span class="sxs-lookup"><span data-stu-id="1fbf0-162">Applies</span></span>  <br/> |<span data-ttu-id="1fbf0-163">적용</span><span class="sxs-lookup"><span data-stu-id="1fbf0-163">Applies</span></span>  <br/> |
|<span data-ttu-id="1fbf0-164">Azure 가상 네트워크에 대 한 신뢰할 수 있는, 중복, 설계자 및 성능이 연결</span><span class="sxs-lookup"><span data-stu-id="1fbf0-164">Architect reliable, redundant, and performant connectivity to Azure virtual networks</span></span>  <br/> |||<span data-ttu-id="1fbf0-165">적용</span><span class="sxs-lookup"><span data-stu-id="1fbf0-165">Applies</span></span>  <br/> |
|<span data-ttu-id="1fbf0-166">Azure 가상 컴퓨터에 대 한 보안 연결을 디자인 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fbf0-166">Design secure connectivity to Azure virtual machines</span></span>  <br/> |||<span data-ttu-id="1fbf0-167">적용</span><span class="sxs-lookup"><span data-stu-id="1fbf0-167">Applies</span></span>  <br/> |
|<span data-ttu-id="1fbf0-168">디자인 및 온-프레미스 위치와 가상 네트워크 간의 라우팅을 구현합니다</span><span class="sxs-lookup"><span data-stu-id="1fbf0-168">Design and implement routing between on-premises locations and virtual networks</span></span>  <br/> |||<span data-ttu-id="1fbf0-169">적용</span><span class="sxs-lookup"><span data-stu-id="1fbf0-169">Applies</span></span>  <br/> |
|<span data-ttu-id="1fbf0-170">설계 하 고 내부 및 인터넷 IT 작업에 대해 부하 분산을 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fbf0-170">Architect and implement load balancing for internal and Internet-facing IT workloads</span></span>  <br/> |||<span data-ttu-id="1fbf0-171">적용</span><span class="sxs-lookup"><span data-stu-id="1fbf0-171">Applies</span></span>  <br/> |
|<span data-ttu-id="1fbf0-172">가상 컴퓨터 연결 및 처리량 문제를 해결</span><span class="sxs-lookup"><span data-stu-id="1fbf0-172">Troubleshoot virtual machine connectivity and throughput issues</span></span>  <br/> |||<span data-ttu-id="1fbf0-173">적용</span><span class="sxs-lookup"><span data-stu-id="1fbf0-173">Applies</span></span>  <br/> |
   
## <a name="next-step"></a><span data-ttu-id="1fbf0-174">다음 단계</span><span class="sxs-lookup"><span data-stu-id="1fbf0-174">Next step</span></span>

[<span data-ttu-id="1fbf0-175">Microsoft 클라우드 연결의 일반적인 요소</span><span class="sxs-lookup"><span data-stu-id="1fbf0-175">Common elements of Microsoft cloud connectivity</span></span>](common-elements-of-microsoft-cloud-connectivity.md)

## <a name="see-also"></a><span data-ttu-id="1fbf0-176">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1fbf0-176">See also</span></span>

[<span data-ttu-id="1fbf0-177">Microsoft Cloud Networking for Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="1fbf0-177">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="1fbf0-178">Microsoft 클라우드 IT 아키텍처 리소스</span><span class="sxs-lookup"><span data-stu-id="1fbf0-178">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)



