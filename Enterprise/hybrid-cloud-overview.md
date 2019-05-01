---
title: 하이브리드 클라우드 개요
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 3ea3ee10-411e-4690-b9e5-f1b46f1f4d59
description: '요약: Microsoft 하이브리드 클라우드의 정의 및 요소를 이해 합니다.'
ms.openlocfilehash: c048cfeb840bbb03b1886c7053603cfdc84f37ab
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/30/2019
ms.locfileid: "33491162"
---
# <a name="hybrid-cloud-overview"></a><span data-ttu-id="a2151-103">하이브리드 클라우드 개요</span><span class="sxs-lookup"><span data-stu-id="a2151-103">Hybrid cloud overview</span></span>

 <span data-ttu-id="a2151-104">**요약:** Microsoft 하이브리드 클라우드의 정의 및 요소를 이해 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2151-104">**Summary:** Understand the definition and elements of Microsoft hybrid cloud.</span></span>
  
<span data-ttu-id="a2151-105">하이브리드 클라우드는 온-프레미스 네트워크와 클라우드에서 계산 또는 저장소 리소스를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2151-105">Hybrid cloud uses compute or storage resources on your on-premises network and in the cloud.</span></span> <span data-ttu-id="a2151-106">하이브리드 클라우드를 경로로 사용 하 여 비즈니스 및 IT 요구를 클라우드로 마이그레이션하거나, 전체 IT 전략의 일환으로 기존 온-프레미스 인프라와 클라우드 플랫폼 및 서비스를 통합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2151-106">You can use hybrid cloud as a path to migrate your business and its IT needs to the cloud or integrate cloud platforms and services with your existing on-premises infrastructure as part of your overall IT strategy.</span></span>
  
## <a name="microsoft-hybrid-cloud"></a><span data-ttu-id="a2151-107">Microsoft 하이브리드 클라우드</span><span class="sxs-lookup"><span data-stu-id="a2151-107">Microsoft hybrid cloud</span></span>

<span data-ttu-id="a2151-108">microsoft 하이브리드 클라우드는 다음과 같은 microsoft 클라우드 플랫폼을 온-프레미스 구성 요소와 결합 하는 비즈니스 시나리오 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="a2151-108">Microsoft hybrid cloud is a set of business scenarios that combine a Microsoft cloud platform with an on-premises component, such as:</span></span> 
  
- <span data-ttu-id="a2151-109">온-프레미스 sharepoint 팜 및 Office 365에서 SharePoint Online의 콘텐츠에서 검색 결과 가져오기</span><span class="sxs-lookup"><span data-stu-id="a2151-109">Getting search results from content both in an on-premises SharePoint farm and in SharePoint Online in Office 365.</span></span>
    
- <span data-ttu-id="a2151-110">Azure에서 실행 되는 모바일 앱이 온-프레미스 데이터 저장소를 쿼리 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2151-110">A mobile app running in Azure that queries an on-premises data store.</span></span>
    
- <span data-ttu-id="a2151-111">Azure 가상 컴퓨터에서 실행 되는 인트라넷 IT 작업</span><span class="sxs-lookup"><span data-stu-id="a2151-111">An intranet IT workload running on Azure virtual machines.</span></span>
    
<span data-ttu-id="a2151-112">**그림 1: Microsoft 하이브리드 클라우드의 구성 요소**</span><span class="sxs-lookup"><span data-stu-id="a2151-112">**Figure 1: Components of the Microsoft hybrid cloud**</span></span>

![Microsoft 하이브리드 클라우드의 구성 요소](media/Hybrid-Poster/MS-Hybrid-Cloud.png)
  
<span data-ttu-id="a2151-114">그림 1에서는 온-프레미스 네트워크에서 Office 365, PaaS (azure Platform as a service) 집합에 이르기까지 Microsoft 하이브리드 클라우드의 구성 요소를 보여 주고, 인터넷 이나 express 간 연결에서 사용할 수 있는 azure Infrastructure as a service (IaaS) 서비스를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="a2151-114">Figure 1 shows the components of the Microsoft hybrid cloud, from an on-premises network to the set of Office 365, Azure Platform as a Service (PaaS), and Azure Infrastructure as a Service (IaaS) services available across the Internet or an ExpressRoute connection.</span></span>
  
<span data-ttu-id="a2151-115">Microsoft는 SaaS (Software as a Service), PaaS 및 IaaS를 포함 하 여 marketplace에서 가장 완벽 한 클라우드 솔루션을 제공 하므로 다음과 같은 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2151-115">Because Microsoft has the most complete cloud solution in the marketplace—including Software as a Service (SaaS), PaaS, and IaaS—you can:</span></span>
  
- <span data-ttu-id="a2151-116">작업 및 응용 프로그램을 클라우드로 마이그레이션하기 위해 기존 온-프레미스 투자를 활용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2151-116">Leverage your existing on-premises investments as you migrate workloads and applications to the cloud.</span></span>
    
- <span data-ttu-id="a2151-117">장기적 IT 계획에 하이브리드 클라우드 시나리오를 통합 합니다 (예: 규정 또는 정책이 특정 데이터 또는 작업을 클라우드로 이동 하는 것을 허용 하지 않는 경우).</span><span class="sxs-lookup"><span data-stu-id="a2151-117">Incorporate hybrid cloud scenarios into your long-term IT plans, for example, when regulations or policies do not permit moving specific data or workloads to the cloud.</span></span>
    
- <span data-ttu-id="a2151-118">여러 Microsoft 클라우드 서비스 및 플랫폼을 포함 하는 추가 하이브리드 시나리오를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a2151-118">Create additional hybrid scenarios that include multiple Microsoft cloud services and platforms.</span></span>
    
<span data-ttu-id="a2151-119">Microsoft 클라우드 서비스가 포함 된 하이브리드 클라우드의 시나리오는 플랫폼에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="a2151-119">Scenarios for hybrid cloud with Microsoft cloud services vary with the platform.</span></span>
  
- <span data-ttu-id="a2151-120">SaaS</span><span class="sxs-lookup"><span data-stu-id="a2151-120">SaaS</span></span>
    
    <span data-ttu-id="a2151-121">microsoft SaaS 서비스에는 Office 365, microsoft Intune 및 microsoft Dynamics 365가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a2151-121">Microsoft SaaS services include Office 365, Microsoft Intune, and Microsoft Dynamics 365.</span></span> <span data-ttu-id="a2151-122">Microsoft SaaS가 포함 된 하이브리드 클라우드 시나리오는 이러한 서비스를 온-프레미스 서비스 또는 응용 프로그램과 결합 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2151-122">Hybrid cloud scenarios with Microsoft SaaS combine these services with on-premises services or applications.</span></span> <span data-ttu-id="a2151-123">예를 들어 Office 365에서 실행 되는 Exchange Online은 온-프레미스에 배포 된 비즈니스용 Skype 2019와 통합 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2151-123">For example, Exchange Online running in Office 365 can be integrated with Skype for Business 2019 that is deployed on-premises.</span></span>
    
- <span data-ttu-id="a2151-124">Azure PaaS</span><span class="sxs-lookup"><span data-stu-id="a2151-124">Azure PaaS</span></span>
    
    <span data-ttu-id="a2151-125">Microsoft Azure PaaS 서비스를 사용 하면 클라우드 기반 응용 프로그램을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2151-125">Microsoft Azure PaaS services allow you to create cloud-based applications.</span></span> <span data-ttu-id="a2151-126">azure paas 서비스가 포함 된 하이브리드 클라우드 시나리오는 azure paas 앱을 온-프레미스 리소스 또는 응용 프로그램과 결합 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2151-126">Hybrid cloud scenarios with Azure PaaS services combine an Azure PaaS app with on-premises resources or applications.</span></span> <span data-ttu-id="a2151-127">예를 들어 Azure PaaS 앱은 모바일 앱 사용자에 게 표시 하는 데 필요한 정보를 위해 온-프레미스 데이터 저장소를 안전 하 게 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2151-127">For example, an Azure PaaS app could securely query an on-premises data store for information needed to display to mobile app users.</span></span>
    
- <span data-ttu-id="a2151-128">Azure IaaS</span><span class="sxs-lookup"><span data-stu-id="a2151-128">Azure IaaS</span></span>
    
    <span data-ttu-id="a2151-129">Azure IaaS 서비스를 사용 하면 온-프레미스 데이터 센터가 아닌 클라우드에서 서버 기반 IT 워크 로드를 빌드하고 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2151-129">Azure IaaS services allow you to build and run server-based IT workloads in the cloud, rather than in your on-premises datacenter.</span></span> <span data-ttu-id="a2151-130">Azure IaaS services가 포함 된 하이브리드 클라우드 시나리오는 일반적으로 온-프레미스 네트워크에 투명 하 게 연결 된 가상 컴퓨터에서 실행 되는 IT 작업으로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a2151-130">Hybrid cloud scenarios with Azure IaaS services typically consist of an IT workload that runs on virtual machines that is transparently connected to your on-premises network.</span></span> <span data-ttu-id="a2151-131">온-프레미스 사용자는 차이점을 볼 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a2151-131">Your on-premises users will not notice the difference.</span></span>
    
## <a name="elements-of-hybrid-cloud"></a><span data-ttu-id="a2151-132">하이브리드 클라우드의 요소</span><span class="sxs-lookup"><span data-stu-id="a2151-132">Elements of hybrid cloud</span></span>

<span data-ttu-id="a2151-133">Microsoft 클라우드 플랫폼 및 서비스를 사용 하 여 하이브리드 클라우드 시나리오를 계획 하 고 구현할 때 다음 요소를 고려해 야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2151-133">You must account for the following elements when planning and implementing hybrid cloud scenarios with Microsoft cloud platforms and services.</span></span>
  
- <span data-ttu-id="a2151-134">네트워킹</span><span class="sxs-lookup"><span data-stu-id="a2151-134">Networking</span></span>
    
    <span data-ttu-id="a2151-135">하이브리드 클라우드 용 네트워킹에는 Microsoft 클라우드 플랫폼 및 서비스에 대 한 연결이 포함 되어 있으며 최대 부하에 따라 성능이 높은 대역폭을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2151-135">Networking for hybrid cloud scenarios includes the connectivity to Microsoft cloud platforms and services and enough bandwidth to be performant under peak loads.</span></span> <span data-ttu-id="a2151-136">자세한 내용은 [Microsoft 클라우드 네트워킹 for 엔터프라이즈 설계자](microsoft-cloud-networking-for-enterprise-architects.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a2151-136">For more information, see [Microsoft Cloud Networking for Enterprise Architects](microsoft-cloud-networking-for-enterprise-architects.md).</span></span>
    
- <span data-ttu-id="a2151-137">ID</span><span class="sxs-lookup"><span data-stu-id="a2151-137">Identity</span></span>
    
    <span data-ttu-id="a2151-138">SaaS 및 azure PaaS의 id 하이브리드 시나리오에는 온-프레미스 ad ds (Active Directory 도메인 서비스)와 동기화 하거나 ad ds 또는 기타 id 공급자와 페더레이션 할 수 있는 공통 id 공급자로 Azure AD를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2151-138">Identity for SaaS and Azure PaaS hybrid scenarios can include Azure AD as a common identity provider, which can be synchronized with your on-premises Active Directory Domain Services (AD DS), or federated with AD DS or other identity providers.</span></span> <span data-ttu-id="a2151-139">Azure IaaS로 온-프레미스 id 인프라를 확장할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2151-139">You can also extend your on-premises Identity infrastructure to Azure IaaS.</span></span> <span data-ttu-id="a2151-140">자세한 내용은 [Microsoft 클라우드 id for 엔터프라이즈 설계자](microsoft-cloud-it-architecture-resources.md#identity)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a2151-140">For more information, see [Microsoft Cloud Identity for Enterprise Architects](microsoft-cloud-it-architecture-resources.md#identity).</span></span>
    
- <span data-ttu-id="a2151-141">보안</span><span class="sxs-lookup"><span data-stu-id="a2151-141">Security</span></span>
    
    <span data-ttu-id="a2151-142">하이브리드 클라우드의 보안은 id, 데이터 보호, 관리 권한 관리, 위협 인식 및 거 버 넌 스 및 보안 정책의 구현에 대 한 보호 및 관리를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2151-142">Security for hybrid cloud scenarios includes protection and management for your identities, data protection, administrative privilege management, threat awareness, and the implementation of governance and security policies.</span></span> <span data-ttu-id="a2151-143">자세한 내용은 [엔터프라이즈 설계자 용 Microsoft Cloud Security](microsoft-cloud-it-architecture-resources.md#security)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a2151-143">For more information, see [Microsoft Cloud Security for Enterprise Architects](microsoft-cloud-it-architecture-resources.md#security).</span></span>
    
- <span data-ttu-id="a2151-144">관리</span><span class="sxs-lookup"><span data-stu-id="a2151-144">Management</span></span>
    
    <span data-ttu-id="a2151-145">관리 하이브리드 클라우드 시나리오의 경우 설정, 데이터, 계정, 정책 및 권한을 유지 관리 하 고 시나리오 및 해당 성능 요소의 진행 상태를 모니터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2151-145">Management for hybrid cloud scenarios includes the ability to maintain settings, data, accounts, policies, and permissions and to monitor the ongoing health of the elements of the scenario and its performance.</span></span> <span data-ttu-id="a2151-146">Azure IaaS에서 가상 컴퓨터를 관리 하기 위해 Systems Management Server와 같은 동일한 도구 집합을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2151-146">You can also use the same tool set, such as Systems Management Server, for managing virtual machines in Azure IaaS.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="a2151-147">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a2151-147">See Also</span></span>

[<span data-ttu-id="a2151-148">Microsoft Hybrid Cloud for Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="a2151-148">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="a2151-149">Microsoft 클라우드 IT 아키텍처 리소스</span><span class="sxs-lookup"><span data-stu-id="a2151-149">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

