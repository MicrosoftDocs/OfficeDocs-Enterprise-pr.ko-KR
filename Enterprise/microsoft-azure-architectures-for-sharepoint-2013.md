---
title: "SharePoint 2013에 대 한 Microsoft Azure 아키텍처"
ms.author: bcarter
author: bcarter
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 98fc1006-9399-4ff0-a216-c7c05820d822
description: "요약: SharePoint 2013 솔루션은 Microsoft Azure 가상 컴퓨터에서 호스팅할 수 있습니다. 어떤 유형의 솔루션은 가장 잘 맞는 및 Microsoft Azure 하나는 호스트를 설정 하는 방법에 알아봅니다."
ms.openlocfilehash: b21e40351b3d4ae304e0268ad75462c8592e3a69
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2017
---
# <a name="microsoft-azure-architectures-for-sharepoint-2013"></a><span data-ttu-id="6b108-104">SharePoint 2013에 대 한 Microsoft Azure 아키텍처</span><span class="sxs-lookup"><span data-stu-id="6b108-104">Microsoft Azure Architectures for SharePoint 2013</span></span>

 <span data-ttu-id="6b108-p102">**요약:** SharePoint 2013 솔루션은 Microsoft Azure 가상 컴퓨터에서 호스팅할 수 있습니다. 어떤 유형의 솔루션은 가장 잘 맞는 및 Microsoft Azure 하나는 호스트를 설정 하는 방법에 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-p102">**Summary:** SharePoint 2013 solutions can be hosted in Microsoft Azure virtual machines. Learn which type of solutions are a good fit and how to set up Microsoft Azure to host one.</span></span>
  
<span data-ttu-id="6b108-p103">Azure는 SharePoint Server 2013 솔루션을 호스팅하기 위한 좋은 환경입니다. 대부분의 경우에서 Office 365 좋지만 Azure에서 호스팅되는 SharePoint 서버 팜의 특정 솔루션에 대 한 적절 한 옵션이 될 수 있습니다. 이 문서에서는 SharePoint 솔루션 좋은 되도록 Azure 플랫폼에 맞게 설계 하는 방법을 설명 합니다. 다음 두 특정 솔루션은 예제로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-p103">Azure is a good environment for hosting a SharePoint Server 2013 solution. In most cases, we recommend Office 365, but a SharePoint Server farm hosted in Azure can be a good option for specific solutions. This article describes how to architect SharePoint solutions so they are a good fit in the Azure platform. The following two specific solutions are used as examples:</span></span>
  
- [<span data-ttu-id="6b108-111">Microsoft Azure의 SharePoint Server 2013 재해 복구</span><span class="sxs-lookup"><span data-stu-id="6b108-111">SharePoint Server 2013 Disaster Recovery in Microsoft Azure</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md)
    
- [<span data-ttu-id="6b108-112">SharePoint Server 2013을 사용 하 여 Microsoft Azure의 인터넷 사이트</span><span class="sxs-lookup"><span data-stu-id="6b108-112">Internet Sites in Microsoft Azure using SharePoint Server 2013</span></span>](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md)
    
## <a name="recommended-sharepoint-solutions-for-azure-infrastructure-services"></a><span data-ttu-id="6b108-113">Azure 인프라 서비스에 대 한 권장 되는 SharePoint 솔루션</span><span class="sxs-lookup"><span data-stu-id="6b108-113">Recommended SharePoint solutions for Azure Infrastructure Services</span></span>

<span data-ttu-id="6b108-p104">Azure 인프라 서비스에는 SharePoint 솔루션을 호스팅하기 위한 주목할 옵션입니다. 일부 솔루션은 다른 사용자 보다이 플랫폼에 대 한 보다 적합 합니다. 다음 표에서 권장 되는 솔루션을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-p104">Azure infrastructure services is a compelling option for hosting SharePoint solutions. Some solutions are a better fit for this platform than others. The following table shows recommended solutions.</span></span>
  
|<span data-ttu-id="6b108-117">**해결 방법**</span><span class="sxs-lookup"><span data-stu-id="6b108-117">**Solution**</span></span>|<span data-ttu-id="6b108-118">**이 솔루션은 Azure에 대 한 권장 되는 이유**</span><span class="sxs-lookup"><span data-stu-id="6b108-118">**Why this solution is recommended for Azure**</span></span>|
|:-----|:-----|
|<span data-ttu-id="6b108-119">개발 및 테스트 환경</span><span class="sxs-lookup"><span data-stu-id="6b108-119">Development and test environments</span></span>  <br/> |<span data-ttu-id="6b108-120">만들고 이러한 환경을 관리 하기 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-120">It's easy to create and manage these environments.</span></span>  <br/> |
|<span data-ttu-id="6b108-121">Azure로의 온-프레미스 SharePoint 팜 재해 복구</span><span class="sxs-lookup"><span data-stu-id="6b108-121">Disaster recovery of on-premises SharePoint farms to Azure</span></span>  <br/> |<span data-ttu-id="6b108-122">**호스트 된 보조 데이터 센터** Azure를 사용 하 여 서로 다른 영역에 보조 데이터 센터에 투자 하는 대신 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-122">**Hosted secondary datacenter** Use Azure instead of investing in a secondary datacenter in a different region.</span></span> <br/> <span data-ttu-id="6b108-p105">**저렴 재해 복구 환경** 유지 관리 하 고는 온-프레미스 재해 복구 환경 보다 적은 자원에 대 한 지불 합니다. 자원 수 있습니다를 선택 하는 재해 복구 환경에 따라 달라 집니다: 정지 대기, 웜 대기 또는 핫 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-p105">**Lower-cost disaster-recovery environments** Maintain and pay for fewer resources than an on-premises disaster recovery environment. The number of resources depends on the disaster recovery environment you choose: cold standby, warm standby, or hot standby. </span></span><br/> <span data-ttu-id="6b108-p106">**보다 탄력적 플랫폼** 재해 발생 시 쉽게 확장 복구 SharePoint 팜의 부하 요구 사항을 충족 합니다. 리소스에는 필요 없는 경우의 수직 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-p106">**More elastic platform** In the event of a disaster, easily scale-out your recovery SharePoint farm to meet load requirements. Scale in when you no longer need the resources. </span></span><br/> <span data-ttu-id="6b108-127">[Microsoft Azure의 SharePoint Server 2013 재해 복구](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="6b108-127">See [SharePoint Server 2013 Disaster Recovery in Microsoft Azure](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md).</span></span>  <br/> |
|<span data-ttu-id="6b108-128">기능 및 Office 365에서 사용할 수 없는 확장을 사용 하는 인터넷 사이트</span><span class="sxs-lookup"><span data-stu-id="6b108-128">Internet-facing sites that use features and scale not available in Office 365</span></span>  <br/> |<span data-ttu-id="6b108-129">**자신의 노력** 인프라를 구축 하는 것 보다 큰 사이트 만들기 (영문)에 집중 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-129">**Focus your efforts** Concentrate on building a great site rather than building infrastructure.</span></span> <br/> <span data-ttu-id="6b108-p107">**Azure에서 탄성을 활용** 새 서버를 추가 하 여 요청에 대 한 팜 크기를 조정 하 고 필요한 리소스에 대해서만 지불 합니다. 동적 컴퓨터 할당이 올바르지 않은 (자동 크기 조정)를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-p107">**Take advantage of elasticity in Azure** Size the farm for the demand by adding new servers, and pay only for resources you need. Dynamic machine allocation is not supported (auto scale). </span></span><br/> <span data-ttu-id="6b108-132">**Azure Active Directory (AD)를 사용 하 여** 고객 계정에 대 한 Azure AD 활용 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-132">**Use Azure Active Directory (AD)** Take advantage of Azure AD for customer accounts.</span></span> <br/> <span data-ttu-id="6b108-133">**Office 365에서 사용할 수 없는 SharePoint 추가 기능** 상세 보고 및 웹 분석을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-133">**Add SharePoint functionality not available in Office 365** Add deep reporting and web analytics.</span></span> <br/> <span data-ttu-id="6b108-134">[SharePoint Server 2013을 사용 하 여 Microsoft Azure의 인터넷 사이트](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="6b108-134">See [Internet Sites in Microsoft Azure using SharePoint Server 2013](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md).</span></span>  <br/> |
|<span data-ttu-id="6b108-135">Office 365 또는 온-프레미스 환경을 지원 하도록 app 팜</span><span class="sxs-lookup"><span data-stu-id="6b108-135">App farms to support Office 365 or on-premises environments</span></span>  <br/> |<span data-ttu-id="6b108-136">**빌드, 테스트 및 호스트 앱** Azure 지원 모두 온-프레미스 및 클라우드 환경입니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-136">**Build, test, and host apps** in Azure to support both on-premises and cloud environments.</span></span> <br/> <span data-ttu-id="6b108-137">Azure 온-프레미스 환경에 대 한 새 하드웨어를 구입 하는 대신에 **이 역할을 호스트** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-137">**Host this role** in Azure instead of buying new hardware for on-premises environments.</span></span> <br/> |
   
<span data-ttu-id="6b108-138">인트라넷 및 공동 작업 솔루션 및 작업을 다음 옵션을 고려 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-138">For intranet and collaboration solutions and workloads, consider the following options:</span></span>
  
- <span data-ttu-id="6b108-p108">Office 365 비즈니스 요구 사항을 충족 또는 솔루션의 일부가 될 수를 확인 합니다. Office 365에는 항상 최신 상태로 유지 하는 다양 한 기능 집합을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-p108">Determine if Office 365 meets your business requirements or can be part of the solution. Office 365 provides a rich feature set that is always up to date.</span></span>
    
- <span data-ttu-id="6b108-p109">Office 365 모든 비즈니스 요구 사항을 충족 하지 않는, SharePoint 2013 온-프레미스에서 Microsoft Consulting Services (MCS) 표준 구현을 하는 것이 좋습니다. 표준 아키텍처를 사용자 지정 된 것 보다 지원할 수 있습니다, 가격이, 더 쉽고 빠르게 솔루션 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-p109">If Office 365 does not meet all your business requirements, consider a standard implementation of SharePoint 2013 on premises from Microsoft Consulting Services (MCS). A standard architecture can be a quicker, cheaper, and easier solution for you to support than a customized one.</span></span> 
    
- <span data-ttu-id="6b108-143">표준 구현도 비즈니스 요구 사항을 충족 하지 하는 경우 사용자 지정 된 온-프레미스 솔루션을 고려 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-143">If a standard implementation doesn't meet your business requirements, consider a customized on-premises solution.</span></span>
    
- <span data-ttu-id="6b108-p110">클라우드 플랫폼을 사용 하 여 비즈니스 요구 사항에 대 한 중요 한 경우 Azure 인프라 서비스에서 호스팅되는 SharePoint 2013의 표준 또는 사용자 지정 된 구현을 하는 것이 좋습니다. SharePoint 솔루션을 훨씬 쉽게 다른 기본이 아닌 Microsoft 공용 클라우드 플랫폼 보다 Azure에서 지원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-p110">If using a cloud platform is important for your business requirements, consider a standard or customized implementation of SharePoint 2013 hosted in Azure infrastructure services. SharePoint solutions are much easier to support in Azure than other non-native Microsoft public cloud platforms.</span></span>
    
## <a name="before-you-design-the-azure-environment"></a><span data-ttu-id="6b108-146">Azure 환경을 디자인 하기 전에</span><span class="sxs-lookup"><span data-stu-id="6b108-146">Before you design the Azure environment</span></span>

<span data-ttu-id="6b108-p111">이 문서의 예제에서는 SharePoint 토폴로지를 사용 하는 동안에 모든 SharePoint 팜 토폴로지를 사용 하 여 이러한 디자인 개념을 사용할 수 있습니다. Azure 환경을 디자인 하기 전에 다음 토폴로지, 아키텍처, 용량 및 성능 지침을 사용 하 여 SharePoint 팜 디자인 수 있습니다:</span><span class="sxs-lookup"><span data-stu-id="6b108-p111">While this article uses example SharePoint topologies, you can use these design concepts with any SharePoint farm topology. Before you design the Azure environment, use the following topology, architecture, capacity, and performance guidance to design the SharePoint farm:</span></span>
  
- [<span data-ttu-id="6b108-149">SharePoint 2013 IT 전문가 위한 아키텍처 디자인</span><span class="sxs-lookup"><span data-stu-id="6b108-149">Architecture design for SharePoint 2013 IT pros</span></span>](http://technet.microsoft.com/en-us/sharepoint/fp123594.aspx)
    
- [<span data-ttu-id="6b108-150">성능 및 SharePoint Server 2013의 용량 관리에 대 한 계획</span><span class="sxs-lookup"><span data-stu-id="6b108-150">Plan for performance and capacity management in SharePoint Server 2013</span></span>](http://technet.microsoft.com/library/8dd52916-f77d-4444-b593-1f7d6f330e5f.aspx)
    
## <a name="determine-the-active-directory-domain-type"></a><span data-ttu-id="6b108-151">Active Directory 도메인 유형 결정</span><span class="sxs-lookup"><span data-stu-id="6b108-151">Determine the Active Directory domain type</span></span>

<span data-ttu-id="6b108-p112">각 SharePoint 서버 팜은 팜 설치에 대 한 관리 계정을 제공 하기 위해 Active Directory를 사용 합니다. 이 시간에서 Azure의 SharePoint 솔루션에 대 한 두 옵션이 있습니다. 이러한 옵션은 다음 표에 설명 되어있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-p112">Each SharePoint Server farm relies on Active Directory to provide administrative accounts for farm setup. At this time, there are two options for SharePoint solutions in Azure. These are described in the following table.</span></span>
  
|<span data-ttu-id="6b108-155">**옵션**</span><span class="sxs-lookup"><span data-stu-id="6b108-155">**Option**</span></span>|<span data-ttu-id="6b108-156">**설명**</span><span class="sxs-lookup"><span data-stu-id="6b108-156">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="6b108-157">전용된 도메인</span><span class="sxs-lookup"><span data-stu-id="6b108-157">Dedicated domain</span></span>  <br/> |<span data-ttu-id="6b108-p113">SharePoint 팜의 지원 하기 위해 Azure에 전용 및 격리 된 Active Directory 도메인을 배포할 수 있습니다. 공용 인터넷 사이트에 대 한 좋은 선택입니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-p113">You can deploy a dedicated and isolated Active Directory domain to Azure to support your SharePoint farm. This is a good choice for public-facing Internet sites.</span></span>  <br/> |
|<span data-ttu-id="6b108-160">크로스-프레미스 연결을 통해 온-프레미스 도메인을 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-160">Extend the on-premises domain through a cross-premises connection</span></span>  <br/> |<span data-ttu-id="6b108-p114">크로스-프레미스 연결을 통해 온-프레미스 도메인을 확장 하면 마치 호스팅된 온-프레미스 것 처럼 사용자가 인트라넷을 통해 SharePoint 팜의 액세스 합니다. 온-프레미스 Active Directory 및 DNS 구현을 활용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-p114">When you extend the on-premises domain through a cross-premises connection, users access the SharePoint farm via your intranet as if it were hosted on-premises. You can take advantage of your on-premises Active Directory and DNS implementation.</span></span>  <br/> <span data-ttu-id="6b108-163">크로스-프레미스 연결이 장애 조치 하 여 온-프레미스 팜에서 Azure의 재해 복구 환경을 구축 하기 위한 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-163">A cross-premises connection is required for building a disaster-recovery environment in Azure to fail over to from your on-premises farm.</span></span>  <br/> |
   
<span data-ttu-id="6b108-p115">이 문서에 대 한 크로스-프레미스 연결을 통해 온-프레미스 도메인을 확장 하기 위한 디자인 개념 포함 됩니다. 솔루션 전용된 도메인을 사용 하는 경우 크로스-프레미스 연결이 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-p115">This article includes design concepts for extending the on-premises domain through a cross-premises connection. If your solution uses a dedicated domain, you don't need a cross-premises connection.</span></span>
  
## <a name="design-the-virtual-network"></a><span data-ttu-id="6b108-166">가상 네트워크를 디자인 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-166">Design the virtual network</span></span>

<span data-ttu-id="6b108-p116">먼저 가상 컴퓨터에서는 겁니다 서브넷을 포함 하는 Azure에 가상 네트워크를 해야 합니다. 가상 네트워크 서브넷에 할당 하는 중 일부는 개인 IP 주소 공간이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-p116">First you need a virtual network in Azure, which includes subnets on which you will place your virtual machines. The virtual network needs a private IP address space, portions of which you assign to the subnets.</span></span>
  
<span data-ttu-id="6b108-169">다른 위치를 포함할 수 있는 조직 네트워크에서에서 사용 하지 않은 개인 주소 공간을 선택 해야 Azure에 온-프레미스 네트워크 확장 하는 크로스-프레미스 연결 (재해 복구 환경에 필요)을 통해, 하는 경우 온-프레미스 환경 및 기타 Azure 가상 네트워크입니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-169">If you are extending your on-premises network to Azure through a cross-premises connection (required for a disaster recovery environment), you must choose a private address space that is not already in use elsewhere in your organization network, which can include your on-premises environment and other Azure virtual networks.</span></span> 
  
<span data-ttu-id="6b108-170">**Azure에 가상 네트워크를 사용 하는 그림 1: 온-프레미스 환경**</span><span class="sxs-lookup"><span data-stu-id="6b108-170">**Figure 1: On-premises environment with a virtual network in Azure**</span></span>

![SharePoint 솔루션에 대한 Microsoft Azure Virtual Network 디자인입니다. Azure Gateway에 대한 하나의 서브넷입니다. 가상 컴퓨터에 대한 하나의 서브넷입니다.](images/OPrrasconWA_AZarch.png)
  
<span data-ttu-id="6b108-174">다음은 이 다이어그램에 대한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-174">In this diagram:</span></span>
  
- <span data-ttu-id="6b108-p118">Azure에서 가상 네트워크는 온-프레미스 환경으로 수평적으로 그림이 합니다. 두 환경 사이트 마다 VPN 연결 또는 ExpressRoute 될 수 있는 크로스-프레미스 연결을 통해 아직 연결 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-p118">A virtual network in Azure is illustrated side-by-side to the on-premises environment. The two environments are not yet connected by a cross-premises connection, which can be a site-to-site VPN connection or ExpressRoute.</span></span>
    
- <span data-ttu-id="6b108-p119">이 시점에서 가상 네트워크 서브넷 및 없는 다른 아키텍처 요소에만 포함합니다. 하나의 서브넷 Azure 게이트웨이 호스팅하고 다른 서브넷 SharePoint 팜에 있는 Active Directory 및 DNS에 대 한 추가 계층을 호스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-p119">At this point, the virtual network just includes the subnets and no other architectural elements. One subnet will host the Azure gateway and other subnets host the tiers of the SharePoint farm, with an additional one for Active Directory and DNS.</span></span>
    
## <a name="add-cross-premises-connectivity"></a><span data-ttu-id="6b108-179">크로스-프레미스 연결 추가</span><span class="sxs-lookup"><span data-stu-id="6b108-179">Add cross-premises connectivity</span></span>

<span data-ttu-id="6b108-p120">다음 배포 단계 (이 솔루션에 적용 됨) 하는 경우 크로스-프레미스 연결을 만드는 것입니다. 크로스-프레미스 연결에 대 한 Azure 게이트웨이 별도 게이트웨이 서브넷에 있는 만들고 주소 공간을 할당 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-p120">The next deployment step is to create the cross-premises connection (if this applies to your solution). For cross-premises connections, a Azure gateway resides in a separate gateway subnet, which you must create and assign an address space.</span></span> 
  
<span data-ttu-id="6b108-182">크로스-프레미스 연결에 대 한 계획 하는 경우를 정의 하 고는 Azure 게이트웨이 만들고 온-프레미스 게이트웨이 장치를 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-182">When you plan for a cross-premises connection, you define and create an Azure gateway and connection to an on-premises gateway device.</span></span>
  
<span data-ttu-id="6b108-183">**그림 2: Azure 게이트웨이와 온-프레미스 게이트웨이 장치를 사용 하 여 온-프레미스 환경 및 Azure 사이의 사이트 간 연결을 제공 하려면**</span><span class="sxs-lookup"><span data-stu-id="6b108-183">**Figure 2: Using an Azure gateway and an on-premises gateway device to provide site-to-site connectivity between the on-premises environment and Azure**</span></span>

![크로스-프레미스 연결(사이트 간 VPN 연결 또는 Express 경로일 수 있음)에 의해 Azure Virtual Network에 연결된 온-프레미스 환경](images/AZarch_VPNgtwyconnct.png)
  
<span data-ttu-id="6b108-185">다음은 이 다이어그램에 대한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-185">In this diagram:</span></span>
  
- <span data-ttu-id="6b108-186">다이어그램에 추가 하는 이전, 온-프레미스 환경에 연결 되어 Azure 가상 네트워크 사이트 마다 VPN 연결 또는 ExpressRoute 될 수 있는 한 크로스-프레미스 연결 하 여 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-186">Adding to the previous diagram, the on-premises environment is connected to the Azure virtual network by a cross-premise connection, which can be a site-to-site VPN connection or ExpressRoute.</span></span>
    
- <span data-ttu-id="6b108-187">Azure는 게이트웨이 게이트웨이 서브넷에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-187">An Azure gateway is on a gateway subnet.</span></span>
    
- <span data-ttu-id="6b108-188">온-프레미스 환경 라우터 또는 VPN 서버와 같은 게이트웨이 장치를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-188">The on-premises environment includes a gateway device, such as a router or VPN server.</span></span>
    
<span data-ttu-id="6b108-189">크로스-프레미스 가상 네트워크 만들기 및 계획에 대 한 자세한 내용은 [Microsoft Azure 가상 네트워크에 연결 하는 온-프레미스 네트워크 연결](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="6b108-189">For additional information to plan for and create a cross-premises virtual network, see [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span>
  
## <a name="add-windows-server-active-directory-ad-and-dns"></a><span data-ttu-id="6b108-190">Windows Server Active Directory (AD)를 추가 하 고 DNS</span><span class="sxs-lookup"><span data-stu-id="6b108-190">Add Windows Server Active Directory (AD) and DNS</span></span>

<span data-ttu-id="6b108-191">Windows Server AD Azure의 재해 복구를 위한 배포 및 하이브리드 시나리오에서 Windows Server AD의 DNS 두 온-프레미스 배포 및 Azure 가상 컴퓨터에서 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-191">For disaster recovery in Azure, you deploy Windows Server AD and DNS in a hybrid scenario where Windows Server AD is deployed both on-premises and on Azure virtual machines.</span></span>
  
<span data-ttu-id="6b108-192">**그림 3: 하이브리드 Active Directory 도메인 구성**</span><span class="sxs-lookup"><span data-stu-id="6b108-192">**Figure 3: Hybrid Active Directory domain configuration**</span></span>

![Azure Virtual Network와 SharePoint 팜 서브넷에 배포된 두 가상 컴퓨터: 복제 도메인 컨트롤러 및 DNS 서버](images/AZarch_HyADdomainConfig.png)
  
<span data-ttu-id="6b108-p121">이 다이어그램 두 가상 컴퓨터에 Windows Server AD 및 DNS 서브넷을 추가 하 여 이전 다이어그램에 구축 합니다. 이러한 가상 컴퓨터는 복제 도메인 컨트롤러 및 DNS 서버입니다. 온-프레미스 Windows Server AD 환경의 확장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-p121">This diagram builds on the previous diagrams by adding two virtual machines to a Windows Server AD and DNS subnet. These virtual machines are replica domain controllers and DNS servers. They are an extension of the on-premises Windows Server AD environment.</span></span> 
  
<span data-ttu-id="6b108-p122">다음 표에서 Azure에 이러한 가상 컴퓨터에 대 한 구성 권장 사항을 제공 합니다. 시작 지점으로이 사용 하 여 사용자가 자신의 환경 디자인 (영문)에 대 한-온-프레미스 환경의 Azure 환경 하지 통신할 전용된 도메인에 대 한도입니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-p122">The following table provides configuration recommendations for these virtual machines in Azure. Use these as a starting point for designing your own environment—even for a dedicated domain where your Azure environment doesn't communicate with your on-premises environment.</span></span>
  
|<span data-ttu-id="6b108-199">**항목**</span><span class="sxs-lookup"><span data-stu-id="6b108-199">**Item**</span></span>|<span data-ttu-id="6b108-200">**구성**</span><span class="sxs-lookup"><span data-stu-id="6b108-200">**Configuration**</span></span>|
|:-----|:-----|
|<span data-ttu-id="6b108-201">Azure에 가상 컴퓨터 크기</span><span class="sxs-lookup"><span data-stu-id="6b108-201">Virtual machine size in Azure</span></span>  <br/> |<span data-ttu-id="6b108-202">표준 계층에서 A1 또는 A2 크기</span><span class="sxs-lookup"><span data-stu-id="6b108-202">A1 or A2 size in the Standard tier</span></span>  <br/> |
|<span data-ttu-id="6b108-203">운영 체제</span><span class="sxs-lookup"><span data-stu-id="6b108-203">Operating system</span></span>  <br/> |<span data-ttu-id="6b108-204">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="6b108-204">Windows Server 2012 R2</span></span>  <br/> |
|<span data-ttu-id="6b108-205">Active Directory 역할</span><span class="sxs-lookup"><span data-stu-id="6b108-205">Active Directory role</span></span>  <br/> |<span data-ttu-id="6b108-p123">AD DS 도메인 컨트롤러를 글로벌 카탈로그 서버로 지정 합니다. 이 구성은 크로스-프레미스 연결을 통해 탈출 트래픽을 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-p123">AD DS domain controller designated as a global catalog server. This configuration reduces egress traffic across the cross-premises connection.</span></span>  <br/> <span data-ttu-id="6b108-208">(공통 되지 않음) 변경 속도가 빠른 다중 도메인 환경에서 온-프레미스 복제 트래픽을 줄일 수 Azure에서 글로벌 카탈로그 서버와 동기화 할 필요가 도메인 컨트롤러를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-208">In a multidomain environment with high rates of change (this is not common), configure domain controllers on premises not to sync with the global catalog servers in Azure, to reduce replication traffic.</span></span>  <br/> |
|<span data-ttu-id="6b108-209">DNS 역할</span><span class="sxs-lookup"><span data-stu-id="6b108-209">DNS role</span></span>  <br/> |<span data-ttu-id="6b108-210">설치 하 고 도메인 컨트롤러에서 DNS 서버 서비스를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-210">Install and configure the DNS Server service on the domain controllers.</span></span>  <br/> |
|<span data-ttu-id="6b108-211">데이터 디스크</span><span class="sxs-lookup"><span data-stu-id="6b108-211">Data disks</span></span>  <br/> |<span data-ttu-id="6b108-p124">Active Directory 데이터베이스, 로그 및 SYSVOL Azure 추가 데이터 디스크에 배치 합니다. 이러한 운영 체제 디스크 또는 Azure에서 제공 하는 임시 디스크에 배치 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="6b108-p124">Place the Active Directory database, logs, and SYSVOL on additional Azure data disks. Do not place these on the operating system disk or the temporary disks provided by Azure.</span></span>  <br/> |
|<span data-ttu-id="6b108-214">IP 주소</span><span class="sxs-lookup"><span data-stu-id="6b108-214">IP addresses</span></span>  <br/> |<span data-ttu-id="6b108-215">고정 IP 주소를 사용 하 고 도메인 컨트롤러를 구성한 후 이러한 주소는 가상 네트워크의 가상 컴퓨터를 할당 하 여 가상 네트워크를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-215">Use static IP addresses and configure the virtual network to assign these addresses to the virtual machines in the virtual network after the domain controllers have been configured.</span></span>  <br/> |
   
> [!IMPORTANT]
> <span data-ttu-id="6b108-p125">Azure의 Active Directory를 배포 하기 전에 [Windows Server Active Directory를 배포에 Azure 가상 컴퓨터에 대 한 지침](https://go.microsoft.com/fwlink/p/?linkid=392681)을 제공 합니다. 솔루션에 필요한 다른 아키텍처 또는 다른 구성 설정 하는 경우 이러한 도움말 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-p125">Before you deploy Active Directory in Azure, read [Guidelines for Deploying Windows Server Active Directory on Azure Virtual Machines](https://go.microsoft.com/fwlink/p/?linkid=392681). These help you determine if a different architecture or different configuration settings are needed for your solution.</span></span> 
  
## <a name="add-the-sharepoint-farm"></a><span data-ttu-id="6b108-218">SharePoint 팜 추가</span><span class="sxs-lookup"><span data-stu-id="6b108-218">Add the SharePoint farm</span></span>

<span data-ttu-id="6b108-219">적절 한 서브넷에 대 한 계층에는 SharePoint 팜에서의 가상 컴퓨터를 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-219">Place the virtual machines of the SharePoint farm in tiers on the appropriate subnets.</span></span>
  
<span data-ttu-id="6b108-220">**SharePoint 가상 컴퓨터의 그림 4: 배치**</span><span class="sxs-lookup"><span data-stu-id="6b108-220">**Figure 4: Placement of SharePoint virtual machines**</span></span>

![SharePoint 팜 서브넷 내의 Azure Virtual Network에 추가된 데이터베이스 서버 및 SharePoint 서버 역할](images/AZarch_SPVMsinCloudSer.png)
  
<span data-ttu-id="6b108-222">이 다이어그램의 각 계층에서 SharePoint 팜 서버 역할을 추가 하 여 이전 다이어그램에서 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-222">This diagram builds on the previous diagrams by adding the SharePoint farm server roles in their respective tiers.</span></span>
  
- <span data-ttu-id="6b108-223">SQL Server를 실행 하는 두 데이터베이스 가상 컴퓨터에서 데이터베이스 계층을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-223">Two database virtual machines running SQL Server create the database tier.</span></span>
    
- <span data-ttu-id="6b108-224">각 다음 계층에 대 한 SharePoint Server 2013을 실행 하는 두 가상 컴퓨터: 프런트엔드 서버, 분산된 캐시 서버 및 백엔드 서버입니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-224">Two virtual machines running SharePoint Server 2013 for each of the following tiers: front end servers, distributed cache servers, and back end servers.</span></span>
    
## <a name="design-and-fine-tune-server-roles-for-availability-sets-and-fault-domains"></a><span data-ttu-id="6b108-225">디자인 및 가용성 집합과 장애 도메인에 대 한 서버 역할을 미세 조정</span><span class="sxs-lookup"><span data-stu-id="6b108-225">Design and fine tune server roles for availability sets and fault domains</span></span>

<span data-ttu-id="6b108-p126">장애 도메인은를 실행 하는 역할 인스턴스에서 하드웨어의 그룹입니다. Azure 인프라에 의해 동시에 같은 장애 도메인 내에서 가상 컴퓨터를 업데이트할 수 있습니다. 또는 동일한 랙을 공유 하기 때문에 동시에 실패할 수 있습니다. 동일한 장애 도메인에 가상 컴퓨터 두 대의 위험을 방지 하려면 다른 장애 도메인에서 각 가상 컴퓨터를 유지 하는 가용성 집합으로 가상 컴퓨터를 구성할 수 있습니다. 세 가상 컴퓨터 가용성 집합으로 구성 된 경우 동일한 장애 도메인에 있는 가상 컴퓨터의 2 개 이하의 Azure 보장 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-p126">A fault domain is a grouping of hardware in which role instances run. Virtual machines within the same fault domain can be updated by the Azure infrastructure at the same time. Or, they can fail at the same time because they share the same rack. To avoid the risk of having two virtual machines on the same fault domain, you can configure your virtual machines as an availability set, which ensures that each virtual machine is in a different fault domain. If three virtual machines are configured as an availability set, Azure guarantees that no more than two of the virtual machines are located in the same fault domain.</span></span>
  
<span data-ttu-id="6b108-p127">SharePoint 팜에 대해 Azure 아키텍처를 디자인할 때 가용성 집합의 일부를 동일한 서버 역할을 구성 합니다. 이렇게 하면 가상 컴퓨터에 여러 장애 도메인 분산 되는 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-p127">When you design the Azure architecture for a SharePoint farm, configure identical server roles to be part of an availability set. This ensures that your virtual machines are spread across multiple fault domains.</span></span>
  
<span data-ttu-id="6b108-233">**그림 5: SharePoint 팜 계층에 대 한 고가용성을 제공 하려면 사용 하 여 Azure 가용성 집합**</span><span class="sxs-lookup"><span data-stu-id="6b108-233">**Figure 5: Use Azure Availability Sets to provide high availability for the SharePoint farm tiers**</span></span>

![SharePoint 2013 솔루션용 Azure 인프라의 가용성 집합 구성](images/AZenv_WinAzureAvailSetsHA.png)
  
<span data-ttu-id="6b108-p128">이 다이어그램 Azure 인프라 내에서 가용성 집합의 구성이 호출합니다. 다음 역할의 각 별도 가용성 집합을 공유 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-p128">This diagram calls out the configuration of availability sets within the Azure infrastructure. Each of the following roles share a separate availability set:</span></span>
  
- <span data-ttu-id="6b108-237">Active Directory 및 DNS</span><span class="sxs-lookup"><span data-stu-id="6b108-237">Active Directory and DNS</span></span>
    
- <span data-ttu-id="6b108-238">데이터베이스</span><span class="sxs-lookup"><span data-stu-id="6b108-238">Database</span></span>
    
- <span data-ttu-id="6b108-239">백엔드</span><span class="sxs-lookup"><span data-stu-id="6b108-239">Back end</span></span>
    
- <span data-ttu-id="6b108-240">캐시를 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-240">Distribute cache</span></span>
    
- <span data-ttu-id="6b108-241">프런트 엔드</span><span class="sxs-lookup"><span data-stu-id="6b108-241">Front end</span></span>
    
<span data-ttu-id="6b108-p129">SharePoint 팜 해야할 것이 좋으며 Azure 플랫폼에서 조정 됩니다. 모든 구성 요소의 고가용성을 보장 하려면 확인 하는 서버 역할이 구성 되는 모두 동일 하 게 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-p129">The SharePoint farm might need to be fine tuned in the Azure platform. To ensure high availability of all components, ensure that the server roles are all configured identically.</span></span>
  
<span data-ttu-id="6b108-p130">다음은 특정 용량 및 성능 목표를 충족 하는 표준 인터넷 사이트 아키텍처를 표시 하는 예제입니다. 이 예제는 다음과 같은 아키텍처 모델에 자세히 볼: [SharePoint Server 2013 용 인터넷 사이트 검색 아키텍처](https://go.microsoft.com/fwlink/p/?LinkId=261519)입니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-p130">Here is an example that shows a standard Internet Sites architecture that meets specific capacity and performance goals. This example is featured in the following architecture model: [Internet Sites Search Architectures for SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=261519).</span></span>
  
<span data-ttu-id="6b108-246">**그림 6: 3 계층 팜의 용량 및 성능 목표에 대 한 예제 계획**</span><span class="sxs-lookup"><span data-stu-id="6b108-246">**Figure 6: Planning example for capacity and performance goals in a three-tier farm**</span></span>

![특정 용량 및 성능 목표를 충족하는 구성 요소 할당이 있는 표준 SharePoint 2013 인터넷 사이트 아키텍처](images/AZarch_CapPerfexmpArch.png)
  
<span data-ttu-id="6b108-248">다음은 이 다이어그램에 대한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-248">In this diagram:</span></span>
  
- <span data-ttu-id="6b108-249">3 계층 팜 표현 됩니다: 웹 서버, 응용 프로그램 서버 및 데이터베이스 서버입니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-249">A three-tier farm is represented: web servers, application servers, and database servers.</span></span>
    
- <span data-ttu-id="6b108-250">세 웹 서버는 여러 구성 요소와 동일 하 게 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-250">The three web servers are configured identically with multiple components.</span></span>
    
- <span data-ttu-id="6b108-251">두 데이터베이스 서버는 동일 하 게 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-251">The two database servers are configured identically.</span></span>
    
- <span data-ttu-id="6b108-p131">세 응용 프로그램 서버를 동일 하 게 구성 되지 않습니다. 이러한 서버 역할 Azure에서 설정 하는 가용성에 대 한 미세 조정에 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-p131">The three application servers are not configured identically. These server roles require fine tuning for availability sets in Azure.</span></span>
    
<span data-ttu-id="6b108-254">응용 프로그램 서버 계층에 자세히 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-254">Let's look closer at the application server tier.</span></span>
  
<span data-ttu-id="6b108-255">**미세 조정 하기 전에 그림 7: 응용 프로그램 서버 계층**</span><span class="sxs-lookup"><span data-stu-id="6b108-255">**Figure 7: Application server tier before fine tuning**</span></span>

![Microsoft Azure 가용성 집합에 맞게 조정하기 전 SharePoint Server 2013 응용 프로그램 서버 계층 예제](images/AZarch_AppServtierBefore.png)
  
<span data-ttu-id="6b108-257">다음은 이 다이어그램에 대한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-257">In this diagram:</span></span>
  
- <span data-ttu-id="6b108-258">세 서버 응용 프로그램 계층에 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-258">Three servers are included in the application tier.</span></span>
    
- <span data-ttu-id="6b108-259">첫번째 서버에는 4 개의 구성 요소가 포함 되어있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-259">The first server includes four components.</span></span>
    
- <span data-ttu-id="6b108-260">두번째 서버는 다음 세가지 구성 요소를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-260">The second server includes three components.</span></span>
    
- <span data-ttu-id="6b108-261">세번째 서버 두 구성 요소를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-261">The third server includes two components.</span></span>
    
<span data-ttu-id="6b108-p132">팜에 대 한 성능 및 용량 목표 하 여 구성 요소 수를 결정 합니다. 이 아키텍처 azure에 맞게 세 서버 모두 4 개의 구성 요소에 복제는 표시 됩니다. 이 성능 및 용량에 필요한 것 보다 세부적 구성 요소의 수를 늘립니다. 단점은이 디자인 때 이러한 세 가상 컴퓨터 가용성 집합에 할당 된 모든 구성 요소 4 개 Azure 플랫폼에서의 고가용성을 보장 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-p132">You determine the number of components by the performance and capacity targets for the farm. To adapt this architecture for Azure, we'll replicate the four components across all three servers. This increases the number of components beyond what is necessary for performance and capacity. The tradeoff is that this design ensures high availability of all four components in the Azure platform when these three virtual machines are assigned to an availability set.</span></span>
  
<span data-ttu-id="6b108-266">**그림 8: 응용 프로그램 서버 계층 미세 조정 후**</span><span class="sxs-lookup"><span data-stu-id="6b108-266">**Figure 8: Application server tier after fine tuning**</span></span>

![Microsoft Azure 가용성 집합에 맞게 조정한 후 SharePoint Server 2013 응용 프로그램 서버 계층 예제](images/AZarch_AppServtierAfter.png)
  
<span data-ttu-id="6b108-268">이 다이어그램에서는 동일한 4 개의 구성 요소를 사용 하 여 동일 하 게 구성 하는 모든 세 응용 프로그램 서버를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-268">This diagram shows all three application servers configured identically with the same four components.</span></span>
  
<span data-ttu-id="6b108-269">SharePoint 팜에 있는 계층에 가용성 집합을 추가할는 구현 완료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-269">When we add availability sets to the tiers of the SharePoint farm, the implementation is complete.</span></span>
  
<span data-ttu-id="6b108-270">**그림 9: 완료 된 SharePoint 팜에 있는 Azure 인프라 서비스**</span><span class="sxs-lookup"><span data-stu-id="6b108-270">**Figure 9: The completed SharePoint farm in Azure infrastructure services**</span></span>

![Virtual Network, 크로스-프레미스 연결, 서브넷, VM 및 가용성 집합이 있는 Azure 인프라 서비스의 SharePoint 2013 팜 예제](images/7256292f-bf11-485b-8917-41ba206153ee.png)
  
<span data-ttu-id="6b108-272">이 다이어그램에서는 각 계층의 서버에 대 한 장애 도메인을 제공 하려면 가용성 집합을 가진 Azure 인프라 서비스에서 구현 하는 SharePoint 팜을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-272">This diagram shows the SharePoint farm implemented in Azure infrastructure services, with availability sets to provide fault domains for the servers in each tier.</span></span>
  
<span data-ttu-id="6b108-273">**토론에 참가**</span><span class="sxs-lookup"><span data-stu-id="6b108-273">**Join the discussion**</span></span>

|<span data-ttu-id="6b108-274">**문의처**</span><span class="sxs-lookup"><span data-stu-id="6b108-274">**Contact us**</span></span>|<span data-ttu-id="6b108-275">**설명**</span><span class="sxs-lookup"><span data-stu-id="6b108-275">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="6b108-276">**클라우드 채택 콘텐츠 합니까 필요 합니까?**</span><span class="sxs-lookup"><span data-stu-id="6b108-276">**What cloud adoption content do you need?**</span></span> <br/> |<span data-ttu-id="6b108-p133">여러 Microsoft 클라우드 플랫폼 및 서비스에 걸쳐 있는 클라우드 채택에 대 한 콘텐츠를 만듭니다. 보겠습니다 작업을 알 사용해 클라우드 채택 콘텐츠를 구상할 [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20)에 전자 메일을 발송 하 여 특정 콘텐츠를 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-p133">We are creating content for cloud adoption that spans multiple Microsoft cloud platforms and services. Let us know what you think about our cloud adoption content, or ask for specific content by sending email to [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20).  </span></span><br/> |
|<span data-ttu-id="6b108-279">**클라우드 채택 토론에 참가**</span><span class="sxs-lookup"><span data-stu-id="6b108-279">**Join the cloud adoption discussion**</span></span> <br/> |<span data-ttu-id="6b108-p134">클라우드 기반 솔루션에 열정을 갖고 인 경우에는 클라우드 채택 자문 보드 (CAAB) Microsoft 콘텐츠 개발자, 업계 전문가는 전세계 어디에서 고객의 더 큰, 생생한 커뮤니티와 연결할에 참가 하는 것이 좋습니다. 참가, Microsoft 기술 커뮤니티의 [CAAB (클라우드 채택 자문 위원회) 공간](https://aka.ms/caab) 의 구성원으로 자신을 추가 하 고[CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!)에서 빠른 전자 메일을 보내주시기 합니다. 누구나 [CAAB 블로그 (영문)](https://blogs.technet.com/b/solutions_advisory_board/)에서 커뮤니티 관련 콘텐츠를 읽을 수 있습니다. 그러나 CAAB 구성원에 게 새 클라우드 채택 리소스 및 솔루션에 설명 하는 개인 웨 초대장을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-p134">If you are passionate about cloud-based solutions, consider joining the Cloud Adoption Advisory Board (CAAB) to connect with a larger, vibrant community of Microsoft content developers, industry professionals, and customers from around the globe. To join, add yourself as a member of the [CAAB (Cloud Adoption Advisory Board) space](https://aka.ms/caab) of the Microsoft Tech Community and send us a quick email at[CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!). Anyone can read community-related content on the [CAAB blog](https://blogs.technet.com/b/solutions_advisory_board/). However, CAAB members get invitations to private webinars that describe new cloud adoption resources and solutions.  </span></span><br/> |
|<span data-ttu-id="6b108-283">**여기에서 참조 하 여 아트 가져오기**</span><span class="sxs-lookup"><span data-stu-id="6b108-283">**Get the art you see here**</span></span> <br/> |<span data-ttu-id="6b108-p135">이 문서에서 참조 하는 이미지의 편집 가능한 복사본을 원하는 귀하에 게 보내야 기꺼이 표시 됩니다. URL 및 [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20)는 이미지의 제목을 포함 하 여 요청을 전자 메일로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="6b108-p135">If you want an editable copy of the art you see in this article, we'll be glad to send it to you. Email your request, including the URL and title of the art, to [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20).  </span></span><br/> |
   
## <a name="see-also"></a><span data-ttu-id="6b108-286">See Also</span><span class="sxs-lookup"><span data-stu-id="6b108-286">See Also</span></span>

[<span data-ttu-id="6b108-287">클라우드 채택 및 하이브리드 솔루션</span><span class="sxs-lookup"><span data-stu-id="6b108-287">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
[<span data-ttu-id="6b108-288">SharePoint Server 2013을 사용 하 여 Microsoft Azure의 인터넷 사이트</span><span class="sxs-lookup"><span data-stu-id="6b108-288">Internet Sites in Microsoft Azure using SharePoint Server 2013</span></span>](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md)
  
[<span data-ttu-id="6b108-289">Microsoft Azure의 SharePoint Server 2013 재해 복구</span><span class="sxs-lookup"><span data-stu-id="6b108-289">SharePoint Server 2013 Disaster Recovery in Microsoft Azure</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md)


