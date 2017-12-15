---
title: "Microsoft Azure PaaS에 대 한 네트워킹 디자인 (영문)"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 19568184-705b-493b-b713-b484367adba9
description: "요약: Microsoft Azure PaaS에 대 한 액세스에 대 한 네트워크를 최적화 하는 방법을 이해 합니다."
ms.openlocfilehash: d63a7a20d4648b0044a24ea86ad4e9125779a027
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2017
---
# <a name="designing-networking-for-microsoft-azure-paas"></a><span data-ttu-id="e1839-103">Microsoft Azure PaaS에 대 한 네트워킹 디자인 (영문)</span><span class="sxs-lookup"><span data-stu-id="e1839-103">Designing networking for Microsoft Azure PaaS</span></span>

 <span data-ttu-id="e1839-104">**요약:** Microsoft Azure PaaS에 대 한 액세스에 대 한 네트워크를 최적화 하는 방법을 이해 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1839-104">**Summary:** Understand how to optimize your network for access to Microsoft Azure PaaS.</span></span>
  
<span data-ttu-id="e1839-105">Azure PaaS 앱용 네트워킹을 최적화하려면 적절한 인터넷 대역폭이 필요하고 여러 사이트 또는 앱 간에 네트워크 트래픽을 분산해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1839-105">Optimizing networking for Azure PaaS apps requires adequate Internet bandwidth and can require the distribution of network traffic across multiple sites or apps.</span></span>
  
## <a name="planning-steps-for-hosting-organization-paas-applications-in-azure"></a><span data-ttu-id="e1839-106">Azure의 조직 PaaS 응용 프로그램 호스팅에 대 한 계획 단계</span><span class="sxs-lookup"><span data-stu-id="e1839-106">Planning steps for hosting organization PaaS applications in Azure</span></span>

<span data-ttu-id="e1839-107">여기에 섹션 본문을 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="e1839-107">Insert section body here.</span></span>
  
1. <span data-ttu-id="e1839-108">[Microsoft 클라우드 연결의 공통 요소](common-elements-of-microsoft-cloud-connectivity.md)에 **Microsoft 클라우드 서비스에 대 한 네트워크를 준비 하는 단계** 섹션을 통해 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1839-108">Go through the **Steps to prepare your network for Microsoft cloud services** section in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).</span></span>
    
2. <span data-ttu-id="e1839-109">[Microsoft SaaS에 대 한 네트워킹 디자인 (영문)](designing-networking-for-microsoft-saas.md)에서 **Microsoft SaaS 서비스에 대 한 네트워크를 준비 하는 단계** 섹션의 2-4 단계를 사용 하 여 인터넷 대역폭을 최적화 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1839-109">Optimize your Internet bandwidth using steps 2 - 4 of the **Steps to prepare your network for Microsoft SaaS services** section in [Designing networking for Microsoft SaaS](designing-networking-for-microsoft-saas.md).</span></span>
    
3. <span data-ttu-id="e1839-110">Azure에 대 한 ExpressRoute 연결의 필요 여부를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1839-110">Determine whether you need an ExpressRoute connection to Azure.</span></span>
    
4. <span data-ttu-id="e1839-111">웹 기반 작업에 대 한 Azure 응용 프로그램 게이트웨이 필요 여부를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1839-111">For web-based workloads, determine whether you need the Azure Application Gateway.</span></span>
    
5. <span data-ttu-id="e1839-112">서로 다른 데이터 센터의 다른 끝점에 대 한 트래픽 배포용 Azure 트래픽 관리자의 필요 여부를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1839-112">For distribution of traffic to different endpoints in different data centers, determine whether you need Azure Traffic Manager.</span></span>
    
## <a name="internet-bandwidth-for-organization-paas-applications"></a><span data-ttu-id="e1839-113">조직 PaaS 응용 프로그램에 대 한 인터넷 대역폭</span><span class="sxs-lookup"><span data-stu-id="e1839-113">Internet bandwidth for organization PaaS applications</span></span>

<span data-ttu-id="e1839-p101">Azure PaaS에서 호스팅되는 조직 응용 프로그램의 경우 인트라넷 사용자에 대 한 인터넷 대역폭을 필요 합니다. 두 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1839-p101">Organization applications hosted in Azure PaaS require Internet bandwidth for intranet users. There are two options:</span></span>
  
- <span data-ttu-id="e1839-p102">**옵션 1:** 최대 부하를 처리 하기 용량을 사용 하 여 인터넷 트래픽을 위해 최적화 하 여 기존 파이프를 사용 합니다. 인터넷에 지, 클라이언트 사용 현황 및 IT 운영 고려 사항에 대 한[Microsoft SaaS에 대 한 네트워킹 디자인 (영문)을](designing-networking-for-microsoft-saas.md) 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="e1839-p102">**Option 1:** Use your existing pipe, optimized for Internet traffic with the capacity to handle peak loads. See[Designing networking for Microsoft SaaS](designing-networking-for-microsoft-saas.md) for Internet edge, client usage, and IT operations considerations.</span></span>
    
- <span data-ttu-id="e1839-118">**옵션 2:** 고대역폭 또는 낮은 대기 시간 요구 Azure에 ExpressRoute 연결을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1839-118">**Option 2:** For high-bandwidth or low latency needs, use an ExpressRoute connection to Azure.</span></span>
    
<span data-ttu-id="e1839-119">**Azure PaaS 서비스를 연결 하기 위한 그림 1: 연결 옵션**</span><span class="sxs-lookup"><span data-stu-id="e1839-119">**Figure 1: Connection options for connecting the Azure PaaS services**</span></span>

![그림 1: Azure PaaS 서비스에 대한 연결 옵션](images/Network_Poster/PaaS1.png)
  
<span data-ttu-id="e1839-121">그림 1 인터넷 파이프 또는 ExpressRoute을 통해 Azure PaaS 서비스에 연결 하는 온-프레미스 네트워크를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="e1839-121">Figure 1 shows an on-premises network connecting to Azure PaaS services over an Internet pipe or ExpressRoute.</span></span>
  
## <a name="azure-application-gateway"></a><span data-ttu-id="e1839-122">Azure 응용 프로그램 게이트웨이</span><span class="sxs-lookup"><span data-stu-id="e1839-122">Azure Application Gateway</span></span>

<span data-ttu-id="e1839-123">응용 프로그램 수준에서 라우팅 및 부하 분산 서비스 수 있도록 하는 확장 가능 하 고 항상 사용 가능 웹 프런트엔드 Azure에서 웹 앱, 클라우드 서비스와 가상 컴퓨터에 대 한 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1839-123">Application-level routing and load balancing services that let you build a scalable and highly-available web front end in Azure for web apps, cloud services, and virtual machines.</span></span> 
  
<span data-ttu-id="e1839-124">**그림 2: Azure 응용 프로그램 게이트웨이**</span><span class="sxs-lookup"><span data-stu-id="e1839-124">**Figure 2: Azure Application Gateway**</span></span>

![그림 2: Azure 응용 프로그램 Gateway 서비스](images/Network_Poster/PaaS2.png)
  
<span data-ttu-id="e1839-126">그림 2에서는 Azure 응용 프로그램 게이트웨이 및 인터넷에서 사용자 요청 하는 방식 Azure 웹 앱, 클라우드 서비스 또는 가상 컴퓨터를 라우팅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1839-126">Figure 2 shows the Azure Application Gateway and how user requests from the Internet can be routed to Azure web apps, cloud services, or virtual machines.</span></span>
  
<span data-ttu-id="e1839-127">현재 응용 프로그램 게이트웨이 다음에 대 한 계층 7 응용 프로그램 배달을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="e1839-127">Application Gateway currently supports layer 7 application delivery for the following:</span></span>
  
- <span data-ttu-id="e1839-128">HTTP 부하 분산</span><span class="sxs-lookup"><span data-stu-id="e1839-128">HTTP load balancing</span></span>
    
- <span data-ttu-id="e1839-129">세션 쿠키 기반 선호도</span><span class="sxs-lookup"><span data-stu-id="e1839-129">Cookie-based session affinity</span></span>
    
- <span data-ttu-id="e1839-130">SSL 오프 로드</span><span class="sxs-lookup"><span data-stu-id="e1839-130">SSL offload</span></span>
    
<span data-ttu-id="e1839-131">자세한 내용은 [응용 프로그램 게이트웨이](https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction)참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="e1839-131">For more information, see [Application Gateway](https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction).</span></span>
  
## <a name="azure-traffic-manager"></a><span data-ttu-id="e1839-132">Azure 트래픽 관리자</span><span class="sxs-lookup"><span data-stu-id="e1839-132">Azure Traffic Manager</span></span>

<span data-ttu-id="e1839-133">클라우드 서비스 또는 다른 데이터 센터 또는 끝점을 외부에 있는 Azure 웹 응용 프로그램을 포함할 수 있는 다른 끝점에 대 한 트래픽의 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1839-133">Distribution of traffic to different endpoints, which can include cloud services or Azure web apps located in different data centers or external endpoints.</span></span>
  
<span data-ttu-id="e1839-134">트래픽 관리자는 다음과 같은 라우팅 방법을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e1839-134">Traffic Manager uses the following routing methods:</span></span>
  
- <span data-ttu-id="e1839-135">**장애 조치:** 끝점을 동일한 컴퓨터나 다른 Azure 데이터 센터에 있으며 모든 트래픽에 대 한 기본 끝점을 사용 하지만 기본 또는 백업 끝점을 사용할 수 없는 경우 백업을 제공 하려는 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1839-135">**Failover:** The endpoints are in the same or different Azure datacenters and you want to use a primary endpoint for all traffic, but provide backups in case the primary or the backup endpoints are unavailable.</span></span>
    
- <span data-ttu-id="e1839-136">**라운드 로빈:** 동일한 데이터 센터에는 끝점의 집합을 통해 또는 다른 데이터 센터 간에 부하를 분산 하려는 경우</span><span class="sxs-lookup"><span data-stu-id="e1839-136">**Round robin:** You want to distribute load across a set of endpoints in the same datacenter or across different datacenters.</span></span>
    
- <span data-ttu-id="e1839-137">**성능:** 끝점을 다른 지리적 위치에 있고 가장 낮은 대기 시간 측면에서 "가장 가까운" 끝점을 사용 하 여 요청 클라이언트를 원하는 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1839-137">**Performance:** You have endpoints in different geographic locations and you want requesting clients to use the "closest" endpoint in terms of the lowest latency.</span></span>
    
<span data-ttu-id="e1839-138">세 지리적으로 분산 된 웹 응용 프로그램에 대 한 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e1839-138">Here is an example for three geographically-distributed web apps.</span></span>
  
<span data-ttu-id="e1839-139">**그림 3: Azure 트래픽 관리자**</span><span class="sxs-lookup"><span data-stu-id="e1839-139">**Figure 3: Azure Traffic Manager**</span></span>

![그림 3: Azure 트래픽 관리자](images/Network_Poster/PaaS3.png)
  
<span data-ttu-id="e1839-p103">그림 3은 트래픽 관리자 미국, 유럽 및 아시아에서는 세가지 다른 Azure 웹 응용 프로그램에 대 한 경로 요청을 사용 하 여 기본 프로세스를 보여줍니다. 예제:</span><span class="sxs-lookup"><span data-stu-id="e1839-p103">Figure 3 shows the basic process that Traffic Manager uses to route requests to three different Azure web apps in United States, Europe, and Asia. In the example:</span></span>
  
1. <span data-ttu-id="e1839-143">URL을 Azure 트래픽 관리자, 지역 웹 응용 프로그램의 이름을 반환 하는 요청을 가져옵니다 웹사이트에 대 한 사용자 DNS 쿼리 성능 라우팅 방법을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1839-143">A user DNS query for a web site URL gets directed to Azure Traffic Manager, which returns the name of a regional web app, based on the performance routing method.</span></span>
    
2. <span data-ttu-id="e1839-144">유럽에서 지역 웹 응용 프로그램을 사용 하 여 트래픽을 시작 하는 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="e1839-144">The user initiates traffic with the regional web app in Europe.</span></span>
    
<span data-ttu-id="e1839-145">자세한 내용은 [트래픽 관리자](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="e1839-145">For more information, see [Traffic Manager](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e1839-146">See Also</span><span class="sxs-lookup"><span data-stu-id="e1839-146">See Also</span></span>

[<span data-ttu-id="e1839-147">Microsoft 클라우드 엔터프라이즈 설계자에 대 한 네트워킹</span><span class="sxs-lookup"><span data-stu-id="e1839-147">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="e1839-148">Microsoft 클라우드 IT 아키텍처 리소스</span><span class="sxs-lookup"><span data-stu-id="e1839-148">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="e1839-149">Microsoft의 엔터프라이즈 클라우드 로드맵: IT 의사 결정권자를 위한 리소스</span><span class="sxs-lookup"><span data-stu-id="e1839-149">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



