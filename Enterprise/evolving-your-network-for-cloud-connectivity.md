---
title: 클라우드 연결을 위해 네트워크 개선
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/28/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 83e2859a-c673-47c4-880a-01cdfdadb93e
description: '요약: 클라우드 채택으로 인해 네트워크 인프라 투자에 대 한 새로운 접근 방법이 필요한 방식에 대해 설명 합니다.'
ms.openlocfilehash: 47d24a4f545cfae8a6bd1c507a61f48b6d26cc7d
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067634"
---
# <a name="evolving-your-network-for-cloud-connectivity"></a><span data-ttu-id="b5ab1-103">클라우드 연결을 위해 네트워크 개선</span><span class="sxs-lookup"><span data-stu-id="b5ab1-103">Evolving your network for cloud connectivity</span></span>

 <span data-ttu-id="b5ab1-104">**요약:** 클라우드 채택에서 네트워크 인프라 투자에 대 한 새로운 접근 방식을 필요로 하는 방식을 이해 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5ab1-104">**Summary:** Understand how cloud adoption requires a new approach to network infrastructure investments.</span></span>
  
<span data-ttu-id="b5ab1-p101">클라우드 마이그레이션으로 인해 회사 네트워크 내부 및 외부의 트래픽 흐름 양과 특성이 달라지고 있습니다. 또한 보안 위험을 완화시키는 방법도 영향을 받고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5ab1-p101">Cloud migration changes the volume and nature of traffic flows within and outside a corporate network. It also affects approaches to mitigating security risk.</span></span>
  
- <span data-ttu-id="b5ab1-107">클라우드 이전</span><span class="sxs-lookup"><span data-stu-id="b5ab1-107">Before the cloud</span></span>
    
    <span data-ttu-id="b5ab1-108">대부분의 네트워킹 인프라 투자가 온-프레미스 데이터 센터에 대 한 사용 가능, 안정성 및 안정적인 연결을 보장 하는 데 소요 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b5ab1-108">Most networking infrastructure investments were spent on ensuring available, reliable, and performant connectivity to on-premises datacenters.</span></span> <span data-ttu-id="b5ab1-109">대부분의 조직에서 내부 비즈니스 운영에는 인터넷 연결이 중요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b5ab1-109">For many organizations, Internet connectivity was not critical for internal business operations.</span></span> <span data-ttu-id="b5ab1-110">네트워크 경계는 보안 침해에 대 한 기본 방어책 이었습니다.</span><span class="sxs-lookup"><span data-stu-id="b5ab1-110">Network boundaries were primary defenses against security breaches.</span></span>
    
- <span data-ttu-id="b5ab1-111">클라우드 후</span><span class="sxs-lookup"><span data-stu-id="b5ab1-111">After the cloud</span></span>
    
    <span data-ttu-id="b5ab1-112">신규 및 마이그레이션된 생산성 및 IT 워크 로드를 클라우드에서 실행 하면 인프라 투자가 온-프레미스 데이터 센터에서 인터넷 연결로 전환 되므로, 이제 내부 비즈니스 운영에 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5ab1-112">With new and migrated productivity and IT workloads running in the cloud, infrastructure investments shift from on-premises datacenters to Internet connectivity, which is now critical for internal business operations.</span></span> <span data-ttu-id="b5ab1-113">페더레이션 연결은 id 및 데이터를 보호 하는 보안 전략을 네트워크를 통해 전달 하 고 Microsoft 클라우드 서비스에 대 한 연결을 가리키기 위해 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5ab1-113">Federated connectivity shifts security strategy to protecting identities and data as they flow through the network and points of connectivity to Microsoft cloud services.</span></span>
    
<span data-ttu-id="b5ab1-114">네트워크 인프라 투자가 연결로 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b5ab1-114">Network infrastructure investments begin with connectivity.</span></span> <span data-ttu-id="b5ab1-115">추가 투자는 클라우드 서비스의 범주에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="b5ab1-115">Additional investments depend on the category of cloud service.</span></span>
  
- <span data-ttu-id="b5ab1-116">**SaaS (Software as a Service)** Microsoft SaaS 서비스에는 Office 365, Microsoft Intune 및 Microsoft Dynamics 365가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b5ab1-116">**Software as a Service (SaaS)** Microsoft SaaS services include Office 365, Microsoft Intune, and Microsoft Dynamics 365.</span></span> <span data-ttu-id="b5ab1-117">사용자가 SaaS 서비스를 성공적으로 채택 해야 하는 경우에는 가용성이 높고 인터넷에 대 한 고성능 연결을 사용 하거나 Microsoft 클라우드 서비스에 직접 의존 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5ab1-117">Successful adoption of SaaS services by users depends on highly-available and performant connectivity to the Internet, or directly to Microsoft cloud services.</span></span>
    
    <span data-ttu-id="b5ab1-118">네트워크 아키텍처는 안정적이 고 중복 된 연결 및 충분 한 대역폭을 중심으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5ab1-118">Network architecture focuses on reliable, redundant connectivity and ample bandwidth.</span></span> <span data-ttu-id="b5ab1-119">지속적인 투자에는 성능 모니터링 및 조정 등이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b5ab1-119">Ongoing investments include performance monitoring and tuning.</span></span>
    
- <span data-ttu-id="b5ab1-120">**Azure PaaS (Platform as a Service)** Microsoft SaaS 서비스에 대 한 투자 외에도 다중 사이트 또는 지리적으로 분산 된 PaaS 응용 프로그램은 클라이언트 트래픽을 분산 하기 위해 Azure Traffic Manager를 설계 해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5ab1-120">**Azure Platform as a Service (PaaS)** In addition to the investments for Microsoft SaaS services, multi-site or geographically distributed PaaS applications might require architecting Azure Traffic Manager to distribute client traffic.</span></span> <span data-ttu-id="b5ab1-121">지속적인 투자에는 성능 및 트래픽 분산 모니터링 및 장애 조치 (failover) 테스트가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b5ab1-121">Ongoing investments include performance and traffic distribution monitoring and failover testing.</span></span>
    
- <span data-ttu-id="b5ab1-122">**Azure IaaS (인프라 as a Service)** Microsoft SaaS 및 PaaS 서비스에 대 한 투자 외에도, IaaS에서 IT 작업을 실행 하는 경우 가상 컴퓨터를 호스트 하는 Azure virtual network의 디자인 및 구성, 라우팅, IP에서 실행 되는 응용 프로그램에 대 한 보안 연결 필요 주소 지정, DNS 및 부하 분산</span><span class="sxs-lookup"><span data-stu-id="b5ab1-122">**Azure Infrastructure as a Service (IaaS)** In addition to the investments for Microsoft SaaS and PaaS services, running IT workloads in IaaS requires the design and configuration of Azure virtual networks that host virtual machines, secure connectivity to applications running on them, routing, IP addressing, DNS, and load balancing.</span></span> <span data-ttu-id="b5ab1-123">지속적인 투자에는 성능 및 보안 모니터링과 문제 해결이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b5ab1-123">Ongoing investments include performance and security monitoring and troubleshooting.</span></span>

<span data-ttu-id="b5ab1-124">[Microsoft 365](https://www.microsoft.com/microsoft-365) 는 Office 365, EMS (Enterprise Management + Security) 및 Windows 10의 조합입니다.</span><span class="sxs-lookup"><span data-stu-id="b5ab1-124">[Microsoft 365](https://www.microsoft.com/microsoft-365) is a combination of Office 365, Enterprise Management + Security (EMS), and Windows 10.</span></span> <span data-ttu-id="b5ab1-125">Microsoft 365에서는 여러 SaaS 및 Azure 서비스를 함께 사용 하 여 모든 사람이 창조적이 고 안전 하 게 함께 작업할 수 있도록 하는 완벽 한 지능형 솔루션을 결합 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5ab1-125">Microsoft 365 combines multiple SaaS and Azure services for a complete, intelligent solution that empowers everyone to be creative and work together securely.</span></span>
    
## <a name="areas-of-networking-investment-for-success-in-the-cloud"></a><span data-ttu-id="b5ab1-126">클라우드의 성공에 대 한 네트워킹 투자 영역</span><span class="sxs-lookup"><span data-stu-id="b5ab1-126">Areas of networking investment for success in the cloud</span></span>

<span data-ttu-id="b5ab1-127">엔터프라이즈 조직은 체계적인 접근 방식을 사용 하 여 인트라넷 및 인터넷에서 네트워크 처리량을 최적화 하는 것을 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5ab1-127">Enterprise organizations benefit from taking a methodical approach to optimizing network throughput across your intranet and to the Internet.</span></span> <span data-ttu-id="b5ab1-128">또한가 수 연결을 통해 혜택을 얻을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5ab1-128">You might also benefit from an ExpressRoute connection.</span></span>
  
### <a name="optimize-intranet-connectivity-to-your-edge-network"></a><span data-ttu-id="b5ab1-129">에 지 네트워크에 대 한 인트라넷 연결 최적화</span><span class="sxs-lookup"><span data-stu-id="b5ab1-129">Optimize intranet connectivity to your edge network</span></span>

<span data-ttu-id="b5ab1-130">대부분의 조직에서는 온-프레미스 데이터 센터에서 실행 되는 응용 프로그램에 대 한 인트라넷 연결 및 성능을 최적화 했습니다.</span><span class="sxs-lookup"><span data-stu-id="b5ab1-130">Over the years, many organizations have optimized intranet connectivity and performance to applications running in on-premises datacenters.</span></span> <span data-ttu-id="b5ab1-131">Microsoft 클라우드에서 생산성과 IT 작업을 실행 하는 경우 추가 투자가 높은 연결 가용성을 보장 하 고,에 지 네트워크와 인트라넷 사용자 간의 트래픽 성능이 최적이 되도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5ab1-131">With productivity and IT workloads running in the Microsoft cloud, additional investment must ensure high connectivity availability and that traffic performance between your edge network and your intranet users is optimal.</span></span>
  
### <a name="optimize-throughput-at-your-edge-network"></a><span data-ttu-id="b5ab1-132">에 지 네트워크에서 처리량 최적화</span><span class="sxs-lookup"><span data-stu-id="b5ab1-132">Optimize throughput at your edge network</span></span>

<span data-ttu-id="b5ab1-133">일상 생산성 트래픽이 클라우드로 이동 하는 경우에도 최신 상태를 유지 하 고 고가용성을 제공 하 고 최대 부하를 충족 하기에 충분 한 용량을 갖게 하려면에 지 네트워크의 시스템 집합을 면밀 하 게 검토 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5ab1-133">As more of your day-to-day productivity traffic travels to the cloud, you should closely examine the set of systems at your edge network to ensure that they are current, provide high availability, and have sufficient capacity to meet peak loads.</span></span>
  
### <a name="for-a-high-sla-to-azure-office-365-and-dynamics-365-use-expressroute"></a><span data-ttu-id="b5ab1-134">Azure, Office 365 및 Dynamics 365에 대 한 높은 SLA를 보려면 Express를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5ab1-134">For a high SLA to Azure, Office 365, and Dynamics 365, use ExpressRoute</span></span>

<span data-ttu-id="b5ab1-135">에 지 네트워크에서 현재 인터넷 연결을 사용할 수 있지만 Microsoft 클라우드 서비스와의 트래픽은 인터넷으로 들어오는 다른 인트라넷 트래픽과 파이프를 공유 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5ab1-135">Although you can use your current Internet connection from your edge network, traffic to and from Microsoft cloud services must share the pipe with other intranet traffic going to the Internet.</span></span> <span data-ttu-id="b5ab1-136">또한 Microsoft 클라우드 서비스에 대 한 트래픽은 인터넷 트래픽 혼잡의 영향을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="b5ab1-136">Additionally, your traffic to Microsoft cloud services is subject to Internet traffic congestion.</span></span>
  
<span data-ttu-id="b5ab1-137">높은 SLA 및 최적의 성능을 위해서는 네트워크와 Azure, Office 365, Dynamics 365 또는 3 모두 간의 전용 WAN 연결을 사용 하는 방법 \ 사용자를 사용할 것을 권장 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5ab1-137">For a high SLA and the best performance, use ExpressRoute, a dedicated WAN connection between your network and Azure, Office 365, Dynamics 365, or all three.</span></span> 
  
<span data-ttu-id="b5ab1-138">Express에서 전용 연결을 위해 기존 네트워크 공급자를 활용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5ab1-138">ExpressRoute can leverage your existing network provider for a dedicated connection.</span></span> <span data-ttu-id="b5ab1-139">이 방법으로는 국내 분산 조직의 경우에도, 기본적으로로 연결 된 리소스는 WAN에 있는 것 처럼 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="b5ab1-139">Resources connected by ExpressRoute appear as if they are on your WAN, even for geographically-distributed organizations.</span></span>
  
<span data-ttu-id="b5ab1-140">자세한 내용은 [Microsoft 클라우드 연결용 express](expressroute-for-microsoft-cloud-connectivity.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b5ab1-140">For more information, see [ExpressRoute for Microsoft cloud connectivity](expressroute-for-microsoft-cloud-connectivity.md).</span></span>
  
## <a name="scope-of-network-investments"></a><span data-ttu-id="b5ab1-141">네트워크 투자 범위</span><span class="sxs-lookup"><span data-stu-id="b5ab1-141">Scope of network investments</span></span>

<span data-ttu-id="b5ab1-142">네트워크 투자 범위는 클라우드 서비스 범주에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="b5ab1-142">The scope of network investments depend on the category of cloud service.</span></span> <span data-ttu-id="b5ab1-143">Microsoft 클라우드를 통한 투자는 네트워킹 팀에 대 한 투자를 극대화 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5ab1-143">Investing across Microsoft's cloud maximizes the investments of networking teams.</span></span> <span data-ttu-id="b5ab1-144">예를 들어, IaaS 서비스용 투자는 모든 투자 영역에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b5ab1-144">For example, investments for IaaS services apply to all investment areas.</span></span>
  
|||||
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="b5ab1-145">투자 영역</span><span class="sxs-lookup"><span data-stu-id="b5ab1-145">Investment area</span></span>  <br/> |<span data-ttu-id="b5ab1-146">SaaS</span><span class="sxs-lookup"><span data-stu-id="b5ab1-146">SaaS</span></span>  <br/> |<span data-ttu-id="b5ab1-147">PaaS</span><span class="sxs-lookup"><span data-stu-id="b5ab1-147">PaaS</span></span>  <br/> |<span data-ttu-id="b5ab1-148">IaaS</span><span class="sxs-lookup"><span data-stu-id="b5ab1-148">IaaS</span></span>  <br/> |
|<span data-ttu-id="b5ab1-149">신뢰할 수 있는 안정적인 인터넷 연결 설계자 (충분 한 대역폭 포함)</span><span class="sxs-lookup"><span data-stu-id="b5ab1-149">Architect reliable, redundant Internet connectivity with ample bandwidth</span></span>  <br/> |<span data-ttu-id="b5ab1-150">적용</span><span class="sxs-lookup"><span data-stu-id="b5ab1-150">Applies</span></span>  <br/> |<span data-ttu-id="b5ab1-151">적용</span><span class="sxs-lookup"><span data-stu-id="b5ab1-151">Applies</span></span>  <br/> |<span data-ttu-id="b5ab1-152">적용</span><span class="sxs-lookup"><span data-stu-id="b5ab1-152">Applies</span></span>  <br/> |
|<span data-ttu-id="b5ab1-153">성능에 대 한 인터넷 처리량 모니터링 및 조정</span><span class="sxs-lookup"><span data-stu-id="b5ab1-153">Monitor and tune Internet throughput for performance</span></span>  <br/> |<span data-ttu-id="b5ab1-154">적용</span><span class="sxs-lookup"><span data-stu-id="b5ab1-154">Applies</span></span>  <br/> |<span data-ttu-id="b5ab1-155">적용</span><span class="sxs-lookup"><span data-stu-id="b5ab1-155">Applies</span></span>  <br/> |<span data-ttu-id="b5ab1-156">적용</span><span class="sxs-lookup"><span data-stu-id="b5ab1-156">Applies</span></span>  <br/> |
|<span data-ttu-id="b5ab1-157">인터넷 연결 및 처리량 문제 해결</span><span class="sxs-lookup"><span data-stu-id="b5ab1-157">Troubleshoot Internet connectivity and throughput issues</span></span>  <br/> |<span data-ttu-id="b5ab1-158">적용</span><span class="sxs-lookup"><span data-stu-id="b5ab1-158">Applies</span></span>  <br/> |<span data-ttu-id="b5ab1-159">적용</span><span class="sxs-lookup"><span data-stu-id="b5ab1-159">Applies</span></span>  <br/> |<span data-ttu-id="b5ab1-160">적용</span><span class="sxs-lookup"><span data-stu-id="b5ab1-160">Applies</span></span>  <br/> |
|<span data-ttu-id="b5ab1-161">다른 끝점에 대 한 트래픽의 부하를 분산 하도록 Azure Traffic Manager 디자인</span><span class="sxs-lookup"><span data-stu-id="b5ab1-161">Design Azure Traffic Manager to load balance traffic to different endpoints</span></span>  <br/> ||<span data-ttu-id="b5ab1-162">적용</span><span class="sxs-lookup"><span data-stu-id="b5ab1-162">Applies</span></span>  <br/> |<span data-ttu-id="b5ab1-163">적용</span><span class="sxs-lookup"><span data-stu-id="b5ab1-163">Applies</span></span>  <br/> |
|<span data-ttu-id="b5ab1-164">Azure virtual network에 대 한 신뢰할 수 있는 중복 및 안정적인 연결 설계자</span><span class="sxs-lookup"><span data-stu-id="b5ab1-164">Architect reliable, redundant, and performant connectivity to Azure virtual networks</span></span>  <br/> |||<span data-ttu-id="b5ab1-165">적용</span><span class="sxs-lookup"><span data-stu-id="b5ab1-165">Applies</span></span>  <br/> |
|<span data-ttu-id="b5ab1-166">Azure 가상 컴퓨터에 대 한 안전한 연결 디자인</span><span class="sxs-lookup"><span data-stu-id="b5ab1-166">Design secure connectivity to Azure virtual machines</span></span>  <br/> |||<span data-ttu-id="b5ab1-167">적용</span><span class="sxs-lookup"><span data-stu-id="b5ab1-167">Applies</span></span>  <br/> |
|<span data-ttu-id="b5ab1-168">온-프레미스 위치와 가상 네트워크 간의 라우팅 디자인 및 구현</span><span class="sxs-lookup"><span data-stu-id="b5ab1-168">Design and implement routing between on-premises locations and virtual networks</span></span>  <br/> |||<span data-ttu-id="b5ab1-169">적용</span><span class="sxs-lookup"><span data-stu-id="b5ab1-169">Applies</span></span>  <br/> |
|<span data-ttu-id="b5ab1-170">내부 및 인터넷 연결 IT 워크 로드에 대 한 부하 분산 설계 및 구현</span><span class="sxs-lookup"><span data-stu-id="b5ab1-170">Architect and implement load balancing for internal and Internet-facing IT workloads</span></span>  <br/> |||<span data-ttu-id="b5ab1-171">적용</span><span class="sxs-lookup"><span data-stu-id="b5ab1-171">Applies</span></span>  <br/> |
|<span data-ttu-id="b5ab1-172">가상 컴퓨터 연결 및 처리량 문제 해결</span><span class="sxs-lookup"><span data-stu-id="b5ab1-172">Troubleshoot virtual machine connectivity and throughput issues</span></span>  <br/> |||<span data-ttu-id="b5ab1-173">적용</span><span class="sxs-lookup"><span data-stu-id="b5ab1-173">Applies</span></span>  <br/> |
   
## <a name="next-step"></a><span data-ttu-id="b5ab1-174">다음 단계</span><span class="sxs-lookup"><span data-stu-id="b5ab1-174">Next step</span></span>

[<span data-ttu-id="b5ab1-175">Microsoft 클라우드 연결의 일반적인 요소</span><span class="sxs-lookup"><span data-stu-id="b5ab1-175">Common elements of Microsoft cloud connectivity</span></span>](common-elements-of-microsoft-cloud-connectivity.md)

## <a name="see-also"></a><span data-ttu-id="b5ab1-176">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b5ab1-176">See also</span></span>

[<span data-ttu-id="b5ab1-177">Microsoft Cloud Networking for Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="b5ab1-177">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="b5ab1-178">Microsoft 클라우드 IT 아키텍처 리소스</span><span class="sxs-lookup"><span data-stu-id="b5ab1-178">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)



