---
title: "Microsoft 하이브리드 클라우드 시나리오의 아키텍처"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 06d8c959-39e5-4150-b1ae-aaf0eee4c058
description: "요약: Microsoft의 하이브리드 클라우드 서비스의 아키텍처를 이해 합니다."
ms.openlocfilehash: 6c61d7467177b0dbf70e5540e32b059b348a062c
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/11/2018
---
# <a name="architecture-of-microsoft-hybrid-cloud-scenarios"></a><span data-ttu-id="67bf4-103">Microsoft 하이브리드 클라우드 시나리오의 아키텍처</span><span class="sxs-lookup"><span data-stu-id="67bf4-103">Architecture of Microsoft hybrid cloud scenarios</span></span>

 <span data-ttu-id="67bf4-104">**요약:** Microsoft의 하이브리드 클라우드 서비스의 아키텍처를 이해 합니다.</span><span class="sxs-lookup"><span data-stu-id="67bf4-104">**Summary:** Understand the architecture of Microsoft's hybrid cloud offerings.</span></span>
  
<span data-ttu-id="67bf4-105">계획 하 고 Microsoft 클라우드 서비스 및 플랫폼 하이브리드 클라우드 시나리오를 구현 하는 아키텍처 접근 방법을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="67bf4-105">Use an architectural approach to plan and implement hybrid cloud scenarios with Microsoft cloud services and platforms.</span></span>
  
<span data-ttu-id="67bf4-106">**Microsoft 하이브리드 클라우드 스택의 그림 1:**</span><span class="sxs-lookup"><span data-stu-id="67bf4-106">**Figure 1: The Microsoft hybrid cloud stack**</span></span>

![Microsoft 하이브리드 클라우드 스택](images/Hybrid_Poster/Hybrid_Cloud_Stack.png)
  
<span data-ttu-id="67bf4-108">그림 1 온-프레미스, 네트워크, Identity, 앱 및 시나리오 및 클라우드 서비스 (Microsoft SaaS, Azure PaaS 및 Azure PaaS)의 범주를 포함 하는 Microsoft 하이브리드 클라우드 스택 및 해당 레이어를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="67bf4-108">Figure 1 shows the Microsoft hybrid cloud stack and its layer, which include on-premises, network, Identity, apps and scenarios, and the category of cloud service (Microsoft SaaS, Azure PaaS, and Azure PaaS).</span></span>
  
<span data-ttu-id="67bf4-p101">앱 및 시나리오 계층에는이 모델의 추가 문서에서 자세히 설명 하는 특정 하이브리드 클라우드 시나리오 포함 됩니다. Identity, 네트워크 및 온-프레미스 레이어 클라우드 서비스 (SaaS, PaaS, 또는 PaaS)의 범주에 공통 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67bf4-p101">The Apps and scenarios layer contains the specific hybrid cloud scenarios that are detailed in the additional articles of this model. The Identity, Network, and On-premises layers can be common to the categories of cloud service (SaaS, PaaS, or PaaS).</span></span>
  
- <span data-ttu-id="67bf4-111">온-프레미스</span><span class="sxs-lookup"><span data-stu-id="67bf4-111">On-premises</span></span>
    
    <span data-ttu-id="67bf4-p102">온-프레미스 인프라 하이브리드 시나리오에 대 한 비즈니스 및 비즈니스 응용 프로그램의 줄에 대 한 개발자를 위한 SharePoint, Exchange, Skype 서버를 포함할 수 있습니다. 데이터 저장소 (데이터베이스, 목록, 파일)를 포함할 수도 있습니다. ExpressRoute 연결 하지 않고 역방향 프록시를 통해 또는 DMZ에 액세스할 수 있는 또는 엑스트라넷 서버 또는 데이터를 요청 하 여 온-프레미스 데이터 저장소에 대 한 액세스를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="67bf4-p102">On-premises infrastructure for hybrid scenarios can include servers for SharePoint, Exchange, Skype for Business, and line of business applications. It can also include data stores (databases, lists, files). Without ExpressRoute connections, access to the on-premises data stores must be allowed through a reverse proxy or by making the server or data accessible on your DMZ or extranet.</span></span>
    
- <span data-ttu-id="67bf4-115">네트워크</span><span class="sxs-lookup"><span data-stu-id="67bf4-115">Network</span></span>
    
    <span data-ttu-id="67bf4-p103">Microsoft 클라우드 플랫폼 및 서비스에 대 한 연결에 대 한 두 선택 사항이: 기존 인터넷 파이프 및 ExpressRoute 합니다. 예측 가능한 성능 문제가 중요 한 경우 ExpressRoute 연결을 사용 합니다. Microsoft SaaS 서비스 (Office 365 및 Dynamics 365), Azure PaaS 서비스 및 Azure PaaS 서비스에 직접 연결을 하나의 ExpressRoute 연결을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67bf4-p103">There are two choices for connectivity to Microsoft cloud platforms and services: your existing Internet pipe and ExpressRoute. Use an ExpressRoute connection if predictable performance is important. You can use one ExpressRoute connection to connect directly to Microsoft SaaS services (Office 365 and Dynamics 365), Azure PaaS services, and Azure PaaS services.</span></span>
    
- <span data-ttu-id="67bf4-119">Identity</span><span class="sxs-lookup"><span data-stu-id="67bf4-119">Identity</span></span>
    
    <span data-ttu-id="67bf4-p104">클라우드 id 인프라에 대 한 두가지를 Microsoft 클라우드 플랫폼에 따라 이동 하 고 있습니다. SaaS 및 Azure PaaS Azure AD와 온-프레미스 identity 인프라가 통합 또는 사용자 온-프레미스 identity 인프라 또는 타사 id 공급자와 페더레이션. Vm Azure에서 실행을 위한 Windows Server AD, Vm에 있는 가상 네트워크 (VNets)와 같은 사용자 온-프레미스 id 인프라를 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67bf4-p104">For cloud identity infrastructure, there are two ways to go, depending on the Microsoft cloud platform. For SaaS and Azure PaaS, integrate your on-premises identity infrastructure with Azure AD or federate with your on-premises identity infrastructure or third-party identity providers. For VMs running in Azure, you can extend your on-premises identity infrastructure, such as Windows Server AD, to the virtual networks (VNets) where your VMs reside.</span></span>
    
## <a name="hybrid-cloud-scenarios-for-the-three-phase-cloud-adoption-process"></a><span data-ttu-id="67bf4-123">3 단계 클라우드 채택 프로세스에 대 한 하이브리드 클라우드 시나리오</span><span class="sxs-lookup"><span data-stu-id="67bf4-123">Hybrid cloud scenarios for the three-phase cloud adoption process</span></span>

<span data-ttu-id="67bf4-p105">클라우드 이유는 3 단계 방식을 사용 하는 Microsoft를 포함 한 대부분의 기업은 합니다. 하이브리드 클라우드 시나리오는 각 단계에는 역할을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67bf4-p105">Many enterprises, including Microsoft's, use a three-phase approach to adopting the cloud. Hybrid cloud scenarios can play a role in each phase.</span></span>
  
1. <span data-ttu-id="67bf4-126">SaaS 생산성 작업 이동</span><span class="sxs-lookup"><span data-stu-id="67bf4-126">Move productivity workloads to SaaS</span></span>
    
    <span data-ttu-id="67bf4-127">현재는 또는 온-프레미스 유지 되어야 하는 생산성 작업 부하에 대 한 하이브리드 시나리오를 사용 하면 해당 클라우드 대응 하는와 통합 될 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="67bf4-127">For productivity workloads that currently are or must stay on-premises, hybrid scenarios allow them to be integrated with their cloud counterparts.</span></span>
    
2. <span data-ttu-id="67bf4-128">Azure PaaS에 새로 추가 되거나 현대 응용 프로그램 개발 (영문)</span><span class="sxs-lookup"><span data-stu-id="67bf4-128">Develop new and modern applications in Azure PaaS</span></span>
    
    <span data-ttu-id="67bf4-129">Azure PaaS 하이브리드 응용 프로그램에서 온-프레미스 서버 또는 저장소 리소스를 활용 안전 하 게 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67bf4-129">Azure PaaS hybrid applications can securely leverage on-premises server or storage resources.</span></span>
    
3. <span data-ttu-id="67bf4-130">기존 응용 프로그램을 Azure IaaS 이동</span><span class="sxs-lookup"><span data-stu-id="67bf4-130">Move existing applications to Azure IaaS</span></span>
    
    <span data-ttu-id="67bf4-131">리프트 shift 및 빌드 클라우드 시나리오에 대 한 Azure Vm에서 실행 중인 서버 기반 응용 프로그램 쉽게 구축 및 확장성을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="67bf4-131">For lift-and-shift and build-in-the-cloud scenarios, server-based applications running on Azure VMs provide easy provisioning and scaling.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="67bf4-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="67bf4-132">See Also</span></span>

[<span data-ttu-id="67bf4-133">Microsoft Hybrid Cloud for Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="67bf4-133">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="67bf4-134">Microsoft 클라우드 IT 아키텍처 리소스</span><span class="sxs-lookup"><span data-stu-id="67bf4-134">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="67bf4-135">Microsoft의 엔터프라이즈 클라우드 로드맵: IT 의사 결정권자를 위한 리소스</span><span class="sxs-lookup"><span data-stu-id="67bf4-135">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



