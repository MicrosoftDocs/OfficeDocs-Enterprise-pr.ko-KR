---
title: Microsoft Azure PaaS에 대한 네트워킹 디자인
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
ms.assetid: 19568184-705b-493b-b713-b484367adba9
description: '요약: Microsoft Azure PaaS에 대 한 액세스를 위해 네트워크를 최적화 하는 방법을 알아봅니다.'
ms.openlocfilehash: 49096276a0e8356a11e52bc8765cc796eec32510
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/30/2019
ms.locfileid: "33491378"
---
# <a name="designing-networking-for-microsoft-azure-paas"></a><span data-ttu-id="c100b-103">Microsoft Azure PaaS에 대한 네트워킹 디자인</span><span class="sxs-lookup"><span data-stu-id="c100b-103">Designing networking for Microsoft Azure PaaS</span></span>

 <span data-ttu-id="c100b-104">**요약:** Microsoft Azure PaaS에 액세스 하기 위해 네트워크를 최적화 하는 방법을 이해 합니다.</span><span class="sxs-lookup"><span data-stu-id="c100b-104">**Summary:** Understand how to optimize your network for access to Microsoft Azure PaaS.</span></span>
  
<span data-ttu-id="c100b-105">Azure PaaS 앱용 네트워킹을 최적화하려면 적절한 인터넷 대역폭이 필요하고 여러 사이트 또는 앱 간에 네트워크 트래픽을 분산해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c100b-105">Optimizing networking for Azure PaaS apps requires adequate Internet bandwidth and can require the distribution of network traffic across multiple sites or apps.</span></span>
  
## <a name="planning-steps-for-hosting-organization-paas-applications-in-azure"></a><span data-ttu-id="c100b-106">Azure에서 조직 PaaS 응용 프로그램을 호스팅하기 위한 계획 단계</span><span class="sxs-lookup"><span data-stu-id="c100b-106">Planning steps for hosting organization PaaS applications in Azure</span></span>

1. <span data-ttu-id="c100b-107">[microsoft 클라우드 연결의 공통 요소](common-elements-of-microsoft-cloud-connectivity.md)에 있는 **microsoft 클라우드 서비스용 네트워크 섹션을 준비 하는 단계** 를 진행 합니다.</span><span class="sxs-lookup"><span data-stu-id="c100b-107">Go through the **Steps to prepare your network for Microsoft cloud services** section in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).</span></span>
    
2. <span data-ttu-id="c100b-108">[microsoft saas에 대 한 네트워킹 디자인](designing-networking-for-microsoft-saas.md)에서 **microsoft saas 서비스용 네트워크 준비** 섹션의 단계 2-4을 사용 하 여 인터넷 대역폭을 최적화 합니다.</span><span class="sxs-lookup"><span data-stu-id="c100b-108">Optimize your Internet bandwidth using steps 2 - 4 of the **Steps to prepare your network for Microsoft SaaS services** section in [Designing networking for Microsoft SaaS](designing-networking-for-microsoft-saas.md).</span></span>
    
3. <span data-ttu-id="c100b-109">Azure에 대 한 express 간 연결이 필요한 지 여부를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c100b-109">Determine whether you need an ExpressRoute connection to Azure.</span></span>
    
4. <span data-ttu-id="c100b-110">웹 기반 작업을 수행 하는 경우 Azure 응용 프로그램 게이트웨이가 필요한 지 여부를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c100b-110">For web-based workloads, determine whether you need the Azure Application Gateway.</span></span>
    
5. <span data-ttu-id="c100b-111">서로 다른 데이터 센터에 있는 여러 끝점에 대 한 트래픽을 분산 하려면 Azure traffic Manager가 필요한 지 여부를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c100b-111">For distribution of traffic to different endpoints in different data centers, determine whether you need Azure Traffic Manager.</span></span>
    
## <a name="internet-bandwidth-for-organization-paas-applications"></a><span data-ttu-id="c100b-112">조직 PaaS 응용 프로그램에 대 한 인터넷 대역폭</span><span class="sxs-lookup"><span data-stu-id="c100b-112">Internet bandwidth for organization PaaS applications</span></span>

<span data-ttu-id="c100b-113">Azure PaaS에서 호스트 되는 조직 응용 프로그램에는 인트라넷 사용자에 대 한 인터넷 대역폭이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="c100b-113">Organization applications hosted in Azure PaaS require Internet bandwidth for intranet users.</span></span> <span data-ttu-id="c100b-114">다음 두 가지 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c100b-114">There are two options:</span></span>
  
- <span data-ttu-id="c100b-115">**옵션 1:** 최대 부하를 처리 하기 위해 용량과의 인터넷 트래픽에 최적화 된 기존 파이프를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c100b-115">**Option 1:** Use your existing pipe, optimized for Internet traffic with the capacity to handle peak loads.</span></span> <span data-ttu-id="c100b-116">인터넷에 지에 대 한[Microsoft SaaS에 대 한 네트워킹 디자인](designing-networking-for-microsoft-saas.md) , 클라이언트 사용량 및 IT 작업 고려 사항을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c100b-116">See[Designing networking for Microsoft SaaS](designing-networking-for-microsoft-saas.md) for Internet edge, client usage, and IT operations considerations.</span></span>
    
- <span data-ttu-id="c100b-117">**옵션 2:** 고대역폭 또는 낮은 대기 시간 요구 사항에 대 한 자세한 내용은 Azure에 대 한 express 연결을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c100b-117">**Option 2:** For high-bandwidth or low latency needs, use an ExpressRoute connection to Azure.</span></span>
    
<span data-ttu-id="c100b-118">**그림 1: Azure PaaS 서비스 연결에 대 한 연결 옵션**</span><span class="sxs-lookup"><span data-stu-id="c100b-118">**Figure 1: Connection options for connecting the Azure PaaS services**</span></span>

![그림 1: Azure PaaS 서비스에 대 한 연결 옵션](media/Network-Poster/PaaS1.png)
  
<span data-ttu-id="c100b-120">그림 1에서는 인터넷 파이프 또는 express를 통해 Azure PaaS 서비스에 연결 되는 온-프레미스 네트워크를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c100b-120">Figure 1 shows an on-premises network connecting to Azure PaaS services over an Internet pipe or ExpressRoute.</span></span>
  
## <a name="azure-application-gateway"></a><span data-ttu-id="c100b-121">Azure 응용 프로그램 게이트웨이</span><span class="sxs-lookup"><span data-stu-id="c100b-121">Azure Application Gateway</span></span>

<span data-ttu-id="c100b-122">웹 앱, 클라우드 서비스 및 가상 컴퓨터에 대 한 Azure에서 확장 가능 하 고 가용성이 높은 웹 프런트 엔드를 작성할 수 있게 해 주는 응용 프로그램 수준 라우팅 및 부하 분산 서비스</span><span class="sxs-lookup"><span data-stu-id="c100b-122">Application-level routing and load balancing services that let you build a scalable and highly-available web front end in Azure for web apps, cloud services, and virtual machines.</span></span> 
  
<span data-ttu-id="c100b-123">**그림 2: Azure 응용 프로그램 게이트웨이**</span><span class="sxs-lookup"><span data-stu-id="c100b-123">**Figure 2: Azure Application Gateway**</span></span>

![그림 2: Azure 응용 프로그램 게이트웨이 서비스](media/Network-Poster/PaaS2.png)
  
<span data-ttu-id="c100b-125">그림 2는 azure 응용 프로그램 게이트웨이를 보여 주고, 인터넷 으로부터의 사용자 요청을 azure web apps, 클라우드 서비스 또는 가상 컴퓨터로 라우팅할 수 있는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="c100b-125">Figure 2 shows the Azure Application Gateway and how user requests from the Internet can be routed to Azure web apps, cloud services, or virtual machines.</span></span>
  
<span data-ttu-id="c100b-126">응용 프로그램 게이트웨이는 현재 다음에 대 한 계층 7 응용 프로그램 전달을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="c100b-126">Application Gateway currently supports layer 7 application delivery for the following:</span></span>
  
- <span data-ttu-id="c100b-127">HTTP 부하 분산</span><span class="sxs-lookup"><span data-stu-id="c100b-127">HTTP load balancing</span></span>
    
- <span data-ttu-id="c100b-128">쿠키 기반 세션 선호도</span><span class="sxs-lookup"><span data-stu-id="c100b-128">Cookie-based session affinity</span></span>
    
- <span data-ttu-id="c100b-129">SSL 오프 로드</span><span class="sxs-lookup"><span data-stu-id="c100b-129">SSL offload</span></span>
    
<span data-ttu-id="c100b-130">자세한 내용은 [응용 프로그램 게이트웨이](https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c100b-130">For more information, see [Application Gateway](https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction).</span></span>
  
## <a name="azure-traffic-manager"></a><span data-ttu-id="c100b-131">Azure 트래픽 관리자</span><span class="sxs-lookup"><span data-stu-id="c100b-131">Azure Traffic Manager</span></span>

<span data-ttu-id="c100b-132">서로 다른 데이터 센터 또는 외부 끝점에 있는 클라우드 서비스 또는 Azure web apps를 포함할 수 있는 여러 끝점에 대 한 트래픽 분산</span><span class="sxs-lookup"><span data-stu-id="c100b-132">Distribution of traffic to different endpoints, which can include cloud services or Azure web apps located in different data centers or external endpoints.</span></span>
  
<span data-ttu-id="c100b-133">Traffic Manager는 다음과 같은 라우팅 방법을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c100b-133">Traffic Manager uses the following routing methods:</span></span>
  
- <span data-ttu-id="c100b-134">**장애 조치:** 끝점이 동일 하거나 서로 다른 Azure 데이터 센터에 있으며 모든 트래픽에 대해 기본 끝점을 사용 하려고 하지만 기본 또는 백업 끝점을 사용할 수 없는 경우 백업을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c100b-134">**Failover:** The endpoints are in the same or different Azure datacenters and you want to use a primary endpoint for all traffic, but provide backups in case the primary or the backup endpoints are unavailable.</span></span>
    
- <span data-ttu-id="c100b-135">**라운드 로빈:** 동일한 데이터 센터의 끝점 집합이 나 서로 다른 데이터 센터 간에 부하를 분산 하려는 경우</span><span class="sxs-lookup"><span data-stu-id="c100b-135">**Round robin:** You want to distribute load across a set of endpoints in the same datacenter or across different datacenters.</span></span>
    
- <span data-ttu-id="c100b-136">**성능:** 다른 지리적 위치에 끝점이 있고 클라이언트에서 가장 짧은 대기 시간에 대 한 "가장 가까운" 끝점을 사용 하도록 요청 하려는 경우</span><span class="sxs-lookup"><span data-stu-id="c100b-136">**Performance:** You have endpoints in different geographic locations and you want requesting clients to use the "closest" endpoint in terms of the lowest latency.</span></span>
    
<span data-ttu-id="c100b-137">다음은 지리적으로 분산 된 세 개의 웹 응용 프로그램에 대 한 예입니다.</span><span class="sxs-lookup"><span data-stu-id="c100b-137">Here is an example for three geographically-distributed web apps.</span></span>
  
<span data-ttu-id="c100b-138">**그림 3: Azure Traffic Manager**</span><span class="sxs-lookup"><span data-stu-id="c100b-138">**Figure 3: Azure Traffic Manager**</span></span>

![그림 3: Azure Traffic Manager](media/Network-Poster/PaaS3.png)
  
<span data-ttu-id="c100b-140">그림 3에서는 트래픽 관리자가 요청을 미국, 유럽 및 아시아의 세 가지 다른 Azure 웹 앱으로 라우팅하기 위해 사용 하는 기본 프로세스를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c100b-140">Figure 3 shows the basic process that Traffic Manager uses to route requests to three different Azure web apps in United States, Europe, and Asia.</span></span> <span data-ttu-id="c100b-141">예:</span><span class="sxs-lookup"><span data-stu-id="c100b-141">In the example:</span></span>
  
1. <span data-ttu-id="c100b-142">웹 사이트 URL에 대 한 사용자 DNS 쿼리는 성능 라우팅 방법을 기반으로 지역 웹 앱의 이름을 반환 하는 Azure Traffic Manager로 리디렉션됩니다.</span><span class="sxs-lookup"><span data-stu-id="c100b-142">A user DNS query for a web site URL gets directed to Azure Traffic Manager, which returns the name of a regional web app, based on the performance routing method.</span></span>
    
2. <span data-ttu-id="c100b-143">사용자가 유럽의 지역별 웹 앱을 사용 하 여 트래픽을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="c100b-143">The user initiates traffic with the regional web app in Europe.</span></span>
    
<span data-ttu-id="c100b-144">자세한 내용은 [Traffic Manager](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="c100b-144">For more information, see [Traffic Manager](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview).</span></span>

## <a name="next-step"></a><span data-ttu-id="c100b-145">다음 단계</span><span class="sxs-lookup"><span data-stu-id="c100b-145">Next step</span></span>

[<span data-ttu-id="c100b-146">Microsoft Azure IaaS에 대한 네트워킹 디자인</span><span class="sxs-lookup"><span data-stu-id="c100b-146">Designing networking for Microsoft Azure IaaS</span></span>](designing-networking-for-microsoft-azure-iaas.md)
 
## <a name="see-also"></a><span data-ttu-id="c100b-147">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c100b-147">See also</span></span>

[<span data-ttu-id="c100b-148">Microsoft Cloud Networking for Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="c100b-148">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="c100b-149">Microsoft 클라우드 IT 아키텍처 리소스</span><span class="sxs-lookup"><span data-stu-id="c100b-149">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

