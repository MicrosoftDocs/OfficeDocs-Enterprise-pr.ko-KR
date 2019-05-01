---
title: Microsoft SaaS에 대한 네트워킹 디자인
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
ms.assetid: 4194020a-3847-4259-9f2d-5c556a4510f9
description: '요약: Office 365, Microsoft Intune 및 Dynamics 365를 포함 하 여 Microsoft의 SaaS 서비스에 액세스할 수 있도록 네트워크를 최적화 하는 방법을 알아봅니다.'
ms.openlocfilehash: 3d47c53de1bc1121ef72eb519c51c0ad9423fff9
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487302"
---
# <a name="designing-networking-for-microsoft-saas"></a><span data-ttu-id="b3beb-103">Microsoft SaaS에 대한 네트워킹 디자인</span><span class="sxs-lookup"><span data-stu-id="b3beb-103">Designing networking for Microsoft SaaS</span></span>

 <span data-ttu-id="b3beb-104">**요약:** Office 365, Microsoft Intune 및 Dynamics 365를 포함 하 여 Microsoft의 SaaS 서비스에 액세스 하기 위해 네트워크를 최적화 하는 방법을 이해 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3beb-104">**Summary:** Understand how to optimize your network for access to Microsoft's SaaS services, including Office 365, Microsoft Intune, and Dynamics 365.</span></span>
  
<span data-ttu-id="b3beb-105">Microsoft SaaS 서비스를 위해 네트워크를 최적화하려면 Microsoft SaaS 서비스로 다양한 범주의 트래픽을 라우팅하기 위해 내부 장치와 에지 장치를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3beb-105">Optimizing your network for Microsoft SaaS services requires the configuration of internal and edge devices to route the different categories of traffic to Microsoft SaaS services.</span></span>
  
## <a name="steps-to-prepare-your-network-for-microsoft-saas-services"></a><span data-ttu-id="b3beb-106">Microsoft SaaS 서비스용 네트워크를 준비 하는 단계</span><span class="sxs-lookup"><span data-stu-id="b3beb-106">Steps to prepare your network for Microsoft SaaS services</span></span>

<span data-ttu-id="b3beb-107">다음 단계에 따라 Microsoft SaaS 서비스에 대 한 네트워크를 최적화 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3beb-107">Follow these steps to optimize your network for Microsoft SaaS services:</span></span>
  
1. <span data-ttu-id="b3beb-108">[microsoft 클라우드 연결의 공통 요소](common-elements-of-microsoft-cloud-connectivity.md)에 있는 **microsoft 클라우드 서비스용 네트워크 섹션을 준비 하는 단계** 를 진행 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3beb-108">Go through the **Steps to prepare your network for Microsoft cloud services** section in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).</span></span>
    
2. <span data-ttu-id="b3beb-109">각 사무실에 인터넷 연결을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3beb-109">Add an Internet connection to each of your offices.</span></span>
    
3. <span data-ttu-id="b3beb-110">모든 인터넷 연결에 대 한 isp에서 로컬 IP 주소가 있는 DNS 서버를 사용 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3beb-110">Ensure that the ISPs for all Internet connections use a DNS server with a local IP address.</span></span>
    
4. <span data-ttu-id="b3beb-111">네트워크 헤어핀 방지 클라우드 기반 보안 서비스와 같은 중간 대상을 검사 하 고 가능한 경우 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3beb-111">Examine your network hairpins, intermediate destinations such as cloud-based security services, and eliminate them if possible.</span></span>
    
5. <span data-ttu-id="b3beb-112">Microsoft SaaS 트래픽의 최적화 및 허용 범주에 대 한 처리를 우회 하도록에 지 장치를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3beb-112">Configure your edge devices to bypass processing for the Optimize and Allow categories of Microsoft SaaS traffic.</span></span>

## <a name="optimizing-traffic-to-microsofts-saas-services"></a><span data-ttu-id="b3beb-113">Microsoft의 SaaS 서비스에 대 한 트래픽 최적화</span><span class="sxs-lookup"><span data-stu-id="b3beb-113">Optimizing traffic to Microsoft’s SaaS services</span></span>    

<span data-ttu-id="b3beb-114">Microsoft SaaS 트래픽의 범주에는 다음 세 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3beb-114">There are three categories of Microsoft SaaS traffic:</span></span>

- <span data-ttu-id="b3beb-115">최적화</span><span class="sxs-lookup"><span data-stu-id="b3beb-115">Optimize</span></span>

  <span data-ttu-id="b3beb-116">모든 microsoft saas 서비스에 연결 하 고 microsoft saas 대역폭, 연결 및 데이터 양을 75% 이상으로 표시 하는 데 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3beb-116">Required for connectivity to every Microsoft SaaS service and represent over 75% of Microsoft SaaS bandwidth, connections, and volume of data.</span></span>

- <span data-ttu-id="b3beb-117">허용</span><span class="sxs-lookup"><span data-stu-id="b3beb-117">Allow</span></span>

  <span data-ttu-id="b3beb-118">특정 Microsoft SaaS 서비스 및 기능에 연결 하는 데 필요 하지만, 최적화 범주에 있는 것 처럼 네트워크 성능 및 대기 시간을 구분 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b3beb-118">Required for connectivity to specific Microsoft SaaS services and features but are not as sensitive to network performance and latency as those in the Optimize category.</span></span>

- <span data-ttu-id="b3beb-119">기본</span><span class="sxs-lookup"><span data-stu-id="b3beb-119">Default</span></span>

  <span data-ttu-id="b3beb-120">최적화가 필요 하지 않은 Microsoft SaaS 서비스 및 종속성을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b3beb-120">Represent Microsoft SaaS services and dependencies that do not require any optimization.</span></span> <span data-ttu-id="b3beb-121">기본 범주 트래픽을 일반적인 인터넷 트래픽과 같이 취급할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3beb-121">You can treat Default category traffic like normal Internet traffic.</span></span>


<span data-ttu-id="b3beb-122">**그림 1: 모든 사무실에 대 한 Microsoft SaaS 트래픽에 권장 되는 구성**</span><span class="sxs-lookup"><span data-stu-id="b3beb-122">**Figure 1: Recommended configuration for Microsoft SaaS traffic for all offices**</span></span>

![그림 1: 모든 사무실에 대 한 Microsoft SaaS 트래픽에 권장 되는 구성](media/Network-Poster/SaaS1.png)

<span data-ttu-id="b3beb-124">그림 1에는 다음과 같은 지사, 지역 또는 중앙 it를 비롯 한 모든 사무실의 권장 구성이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3beb-124">Figure 1 shows the recommended configuration of all offices, including branch offices and regional or central ones, in which:</span></span>

- <span data-ttu-id="b3beb-125">**기본** 범주 및 일반 인터넷 트래픽은 인터넷 기반 보안 위험 으로부터 보호를 제공 하기 위해 프록시 서버 및 기타에 지 장치를 포함 하는 사무실로 라우팅됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3beb-125">**Default** category and general Internet traffic is routed to offices that have proxy servers and other edge devices to provide protection against Internet-based security risks.</span></span>
- <span data-ttu-id="b3beb-126">**최적화** 및 **허용** 범주 트래픽은 프록시 서버 및 기타에 지 장치를 바이패스 하 여 연결 하는 사용자를 포함 하는 office에 가장 가까운 Microsoft 네트워크 프런트 엔드의 모서리로 바로 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3beb-126">**Optimize** and **Allow** category traffic is forwarded directly to the edge of the Microsoft network front end nearest to the office containing the connecting user, bypassing proxy servers and other edge devices.</span></span>

<span data-ttu-id="b3beb-127">지사의 SD (wide area network) 장치에는 다음과 같은 개별 트래픽이 사용 되도록 별도의 트래픽을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3beb-127">Software-defined wide area network (SD-WAN) devices in branch offices separate traffic so that:</span></span> 

- <span data-ttu-id="b3beb-128">**기본** 범주 및 일반 인터넷 트래픽은 WAN 백본으로 중앙 또는 지역별 사무실로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3beb-128">**Default** category and general Internet traffic goes to a central or regional office over the WAN backbone.</span></span> 
- <span data-ttu-id="b3beb-129">**최적화** 및 **허용** 범주 트래픽은 로컬 인터넷 연결을 제공 하는 ISP로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3beb-129">**Optimize** and **Allow** category traffic goes to the ISP providing the local Internet connection.</span></span>
  
<span data-ttu-id="b3beb-130">자세한 내용은 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b3beb-130">For more information, see:</span></span>
  
- [<span data-ttu-id="b3beb-131">네트워크 연결 원칙</span><span class="sxs-lookup"><span data-stu-id="b3beb-131">Network connectivity principles</span></span>](https://aka.ms/expressrouteoffice365)

- [<span data-ttu-id="b3beb-132">Office 365의 네트워크 및 마이그레이션 계획</span><span class="sxs-lookup"><span data-stu-id="b3beb-132">Network and migration planning for Office 365</span></span>](https://aka.ms/tune)
    
## <a name="next-step"></a><span data-ttu-id="b3beb-133">다음 단계</span><span class="sxs-lookup"><span data-stu-id="b3beb-133">Next step</span></span>

[<span data-ttu-id="b3beb-134">Microsoft Azure PaaS에 대한 네트워킹 디자인</span><span class="sxs-lookup"><span data-stu-id="b3beb-134">Designing networking for Microsoft Azure PaaS</span></span>](designing-networking-for-microsoft-azure-paas.md)
    
## <a name="see-also"></a><span data-ttu-id="b3beb-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b3beb-135">See also</span></span>

[<span data-ttu-id="b3beb-136">Microsoft Cloud Networking for Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="b3beb-136">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="b3beb-137">Microsoft 클라우드 IT 아키텍처 리소스</span><span class="sxs-lookup"><span data-stu-id="b3beb-137">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

