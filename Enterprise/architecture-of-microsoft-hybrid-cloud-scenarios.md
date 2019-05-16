---
title: Microsoft 하이브리드 클라우드 시나리오의 아키텍처
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 06d8c959-39e5-4150-b1ae-aaf0eee4c058
description: '요약: Microsoft의 하이브리드 클라우드 제품 아키텍처를 파악 합니다.'
ms.openlocfilehash: 513e45629a7092803cc644241d84985a37e43876
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068324"
---
# <a name="architecture-of-microsoft-hybrid-cloud-scenarios"></a><span data-ttu-id="65147-103">Microsoft 하이브리드 클라우드 시나리오의 아키텍처</span><span class="sxs-lookup"><span data-stu-id="65147-103">Architecture of Microsoft hybrid cloud scenarios</span></span>

 <span data-ttu-id="65147-104">**요약:** Microsoft 하이브리드 클라우드 서비스의 아키텍처를 파악 합니다.</span><span class="sxs-lookup"><span data-stu-id="65147-104">**Summary:** Understand the architecture of Microsoft's hybrid cloud offerings.</span></span>
  
<span data-ttu-id="65147-105">아키텍처 접근 방식을 사용 하 여 Microsoft 클라우드 서비스 및 플랫폼과 함께 하이브리드 클라우드 시나리오를 계획 하 고 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="65147-105">Use an architectural approach to plan and implement hybrid cloud scenarios with Microsoft cloud services and platforms.</span></span>
  
<span data-ttu-id="65147-106">**그림 1: Microsoft 하이브리드 클라우드 스택**</span><span class="sxs-lookup"><span data-stu-id="65147-106">**Figure 1: The Microsoft hybrid cloud stack**</span></span>

![Microsoft 하이브리드 클라우드 스택](media/Hybrid-Poster/Hybrid-Cloud-Stack.png)
  
<span data-ttu-id="65147-108">그림 1은 온-프레미스, 네트워크, Id, 앱 및 시나리오, 클라우드 서비스 범주 (Microsoft SaaS, Azure PaaS 및 Azure PaaS)를 포함 하는 Microsoft 하이브리드 클라우드 스택 및 해당 계층을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="65147-108">Figure 1 shows the Microsoft hybrid cloud stack and its layer, which include on-premises, network, Identity, apps and scenarios, and the category of cloud service (Microsoft SaaS, Azure PaaS, and Azure PaaS).</span></span>
  
<span data-ttu-id="65147-109">앱 및 시나리오 계층에는이 모델의 추가 문서에 자세히 설명 된 특정 하이브리드 클라우드 시나리오가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65147-109">The Apps and scenarios layer has the specific hybrid cloud scenarios that are detailed in the additional articles of this model.</span></span> <span data-ttu-id="65147-110">Id, 네트워크 및 온-프레미스 계층은 클라우드 서비스 (SaaS, PaaS 또는 PaaS)의 범주에 공통 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65147-110">The Identity, Network, and On-premises layers can be common to the categories of cloud service (SaaS, PaaS, or PaaS).</span></span>
  
- <span data-ttu-id="65147-111">온-프레미스</span><span class="sxs-lookup"><span data-stu-id="65147-111">On-premises</span></span>
    
    <span data-ttu-id="65147-112">하이브리드 시나리오의 온-프레미스 인프라에는 SharePoint, Exchange, 비즈니스용 Skype 및 lob (기간 업무) 응용 프로그램에 대 한 서버가 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65147-112">On-premises infrastructure for hybrid scenarios can include servers for SharePoint, Exchange, Skype for Business, and line of business applications.</span></span> <span data-ttu-id="65147-113">데이터 저장소 (데이터베이스, 목록, 파일)도 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65147-113">It can also include data stores (databases, lists, files).</span></span> <span data-ttu-id="65147-114">Express 연결을 사용 하지 않으면 온-프레미스 데이터 저장소에 대 한 액세스를 역방향 프록시를 통해 허용 하거나 DMZ 또는 엑스트라넷에서 서버 또는 데이터에 액세스할 수 있도록 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="65147-114">Without ExpressRoute connections, access to the on-premises data stores must be allowed through a reverse proxy or by making the server or data accessible on your DMZ or extranet.</span></span>
    
- <span data-ttu-id="65147-115">네트워크</span><span class="sxs-lookup"><span data-stu-id="65147-115">Network</span></span>
    
    <span data-ttu-id="65147-116">Microsoft 클라우드 플랫폼과 서비스에 연결 하는 데는 두 가지 옵션이 있습니다 (기존 인터넷 파이프 및 Express).</span><span class="sxs-lookup"><span data-stu-id="65147-116">There are two choices for connectivity to Microsoft cloud platforms and services: your existing Internet pipe and ExpressRoute.</span></span> <span data-ttu-id="65147-117">예측 가능한 성능이 중요 한 경우에는 Express 연결을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="65147-117">Use an ExpressRoute connection if predictable performance is important.</span></span> <span data-ttu-id="65147-118">하나의 Express 연결을 사용 하 여 Microsoft SaaS 서비스 (Office 365 및 Dynamics 365), Azure PaaS services 및 Azure IaaS 서비스에 직접 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65147-118">You can use one ExpressRoute connection to connect directly to Microsoft SaaS services (Office 365 and Dynamics 365), Azure PaaS services, and Azure IaaS services.</span></span>
    
- <span data-ttu-id="65147-119">ID</span><span class="sxs-lookup"><span data-stu-id="65147-119">Identity</span></span>
    
    <span data-ttu-id="65147-120">클라우드 id 인프라의 경우 Microsoft 클라우드 플랫폼에 따라 두 가지 방법을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65147-120">For cloud identity infrastructure, there are two ways to go, depending on the Microsoft cloud platform.</span></span> <span data-ttu-id="65147-121">SaaS 및 Azure PaaS의 경우 Azure AD와 온-프레미스 id 인프라를 통합 하거나 온-프레미스 id 인프라 또는 타사 id 공급자와 페더레이션 합니다.</span><span class="sxs-lookup"><span data-stu-id="65147-121">For SaaS and Azure PaaS, integrate your on-premises identity infrastructure with Azure AD or federate with your on-premises identity infrastructure or third-party identity providers.</span></span> <span data-ttu-id="65147-122">Azure에서 실행 되는 Vm의 경우 AD DS (Active Directory 도메인 서비스)와 같은 온-프레미스 id 인프라를 Vm이 상주 하는 가상 네트워크 (Vnet)로 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65147-122">For VMs running in Azure, you can extend your on-premises identity infrastructure, such as Active Directory Domain Services (AD DS), to the virtual networks (VNets) where your VMs reside.</span></span>
    
## <a name="hybrid-cloud-scenarios-for-the-three-phase-cloud-adoption-process"></a><span data-ttu-id="65147-123">3 단계 클라우드 도입 프로세스에 대 한 하이브리드 클라우드 시나리오</span><span class="sxs-lookup"><span data-stu-id="65147-123">Hybrid cloud scenarios for the three-phase cloud adoption process</span></span>

<span data-ttu-id="65147-124">Microsoft를 비롯 한 많은 기업에서는 3 단계 접근 방식을 사용 하 여 클라우드를 채택 합니다.</span><span class="sxs-lookup"><span data-stu-id="65147-124">Many enterprises, including Microsoft's, use a three-phase approach to adopting the cloud.</span></span> <span data-ttu-id="65147-125">하이브리드 클라우드 시나리오에서는 각 단계에서 역할을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65147-125">Hybrid cloud scenarios can play a role in each phase.</span></span>
  
1. <span data-ttu-id="65147-126">업무 부하를 SaaS로 이동</span><span class="sxs-lookup"><span data-stu-id="65147-126">Move productivity workloads to SaaS</span></span>
    
    <span data-ttu-id="65147-127">현재 온-프레미스에 있는 생산성 워크 로드의 경우 하이브리드 시나리오를 사용 하 여 해당 클라우드 사용자와 통합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65147-127">For productivity workloads that currently are or must stay on-premises, hybrid scenarios allow them to be integrated with their cloud counterparts.</span></span>
    
2. <span data-ttu-id="65147-128">Azure PaaS에서 새로운 최신 응용 프로그램 개발</span><span class="sxs-lookup"><span data-stu-id="65147-128">Develop new and modern applications in Azure PaaS</span></span>
    
    <span data-ttu-id="65147-129">Azure PaaS 하이브리드 응용 프로그램은 온-프레미스 서버 또는 저장소 리소스를 안전 하 게 활용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65147-129">Azure PaaS hybrid applications can securely leverage on-premises server or storage resources.</span></span>
    
3. <span data-ttu-id="65147-130">Azure IaaS로 기존 응용 프로그램 이동</span><span class="sxs-lookup"><span data-stu-id="65147-130">Move existing applications to Azure IaaS</span></span>
    
    <span data-ttu-id="65147-131">리프트 및 비-클라우드 시나리오의 경우 Azure Vm에서 실행 되는 서버 기반 응용 프로그램은 쉬운 프로 비전 및 확장 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="65147-131">For lift-and-shift and build-in-the-cloud scenarios, server-based applications running on Azure VMs provide easy provisioning and scaling.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="65147-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="65147-132">See Also</span></span>

[<span data-ttu-id="65147-133">Microsoft Hybrid Cloud for Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="65147-133">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="65147-134">Microsoft 클라우드 IT 아키텍처 리소스</span><span class="sxs-lookup"><span data-stu-id="65147-134">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

