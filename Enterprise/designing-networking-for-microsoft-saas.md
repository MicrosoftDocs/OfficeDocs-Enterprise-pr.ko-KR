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
description: '요약: Office 365, Microsoft Intune 및 Dynamics 365 포함 한 Microsoft의 SaaS 서비스에 대 한 액세스에 대 한 네트워크를 최적화 하는 방법을 이해 합니다.'
ms.openlocfilehash: 3d47c53de1bc1121ef72eb519c51c0ad9423fff9
ms.sourcegitcommit: 25a022f4ef4e56c5407e8e3a8a34265f8fc94264
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/29/2018
ms.locfileid: "26872269"
---
# <a name="designing-networking-for-microsoft-saas"></a><span data-ttu-id="0a355-103">Microsoft SaaS에 대한 네트워킹 디자인</span><span class="sxs-lookup"><span data-stu-id="0a355-103">Designing networking for Microsoft SaaS</span></span>

 <span data-ttu-id="0a355-104">**요약:** Office 365, Microsoft Intune 및 Dynamics 365 포함 한 Microsoft의 SaaS 서비스에 대 한 액세스에 대 한 네트워크를 최적화 하는 방법을 이해 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a355-104">**Summary:** Understand how to optimize your network for access to Microsoft's SaaS services, including Office 365, Microsoft Intune, and Dynamics 365.</span></span>
  
<span data-ttu-id="0a355-105">Microsoft SaaS 서비스에 대 한 네트워크 최적화의 내부 구성 데이터베이스 및 Microsoft SaaS 서비스 트래픽의 다양 한 범주 회람 하는 지 장치 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a355-105">Optimizing your network for Microsoft SaaS services requires the configuration of internal and edge devices to route the different categories of traffic to Microsoft SaaS services.</span></span>
  
## <a name="steps-to-prepare-your-network-for-microsoft-saas-services"></a><span data-ttu-id="0a355-106">Microsoft SaaS 서비스에 대 한 네트워크를 준비 하는 단계</span><span class="sxs-lookup"><span data-stu-id="0a355-106">Steps to prepare your network for Microsoft SaaS services</span></span>

<span data-ttu-id="0a355-107">Microsoft SaaS 서비스에 대 한 네트워크를 최적화 하기 위해 다음이 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a355-107">Follow these steps to optimize your network for Microsoft SaaS services:</span></span>
  
1. <span data-ttu-id="0a355-108">[Microsoft 클라우드 연결의 공통 요소](common-elements-of-microsoft-cloud-connectivity.md)에 **Microsoft 클라우드 서비스에 대 한 네트워크를 준비 하는 단계** 섹션을 통해 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a355-108">Go through the **Steps to prepare your network for Microsoft cloud services** section in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).</span></span>
    
2. <span data-ttu-id="0a355-109">사무실 각각에 대 한 인터넷 연결을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a355-109">Add an Internet connection to each of your offices.</span></span>
    
3. <span data-ttu-id="0a355-110">모든 인터넷 연결에 대 한 Isp를 사용 하는 DNS 서버를 로컬 IP 주소를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a355-110">Ensure that the ISPs for all Internet connections use a DNS server with a local IP address.</span></span>
    
4. <span data-ttu-id="0a355-111">네트워크 hairpins, 보안 클라우드 기반 서비스와 같은 중간 대상을 검사 하 고 가능한 경우 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a355-111">Examine your network hairpins, intermediate destinations such as cloud-based security services, and eliminate them if possible.</span></span>
    
5. <span data-ttu-id="0a355-112">최적화에 대 한 처리를 무시 하 고 Microsoft SaaS 트래픽의 범주를 허용 하 여에 지 장치를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a355-112">Configure your edge devices to bypass processing for the Optimize and Allow categories of Microsoft SaaS traffic.</span></span>

## <a name="optimizing-traffic-to-microsofts-saas-services"></a><span data-ttu-id="0a355-113">Microsoft의 SaaS 서비스에 대 한 트래픽 최적화</span><span class="sxs-lookup"><span data-stu-id="0a355-113">Optimizing traffic to Microsoft’s SaaS services</span></span>    

<span data-ttu-id="0a355-114">Microsoft SaaS 트래픽의 편리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a355-114">There are three categories of Microsoft SaaS traffic:</span></span>

- <span data-ttu-id="0a355-115">최적화</span><span class="sxs-lookup"><span data-stu-id="0a355-115">Optimize</span></span>

  <span data-ttu-id="0a355-116">모든 Microsoft SaaS 서비스 및 Microsoft SaaS 대역폭, 연결 및 데이터 볼륨의 나타내는 75% 이상에 대 한 연결에 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="0a355-116">Required for connectivity to every Microsoft SaaS service and represent over 75% of Microsoft SaaS bandwidth, connections, and volume of data.</span></span>

- <span data-ttu-id="0a355-117">허용</span><span class="sxs-lookup"><span data-stu-id="0a355-117">Allow</span></span>

  <span data-ttu-id="0a355-118">특정에 대 한 연결에 필요한 Microsoft SaaS 서비스 및 기능 설명 비디오 되지 않은 네트워크 성능 및 최적화 범주에 나타난 대기 시간에 민감한 같이 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a355-118">Required for connectivity to specific Microsoft SaaS services and features but are not as sensitive to network performance and latency as those in the Optimize category.</span></span>

- <span data-ttu-id="0a355-119">기본</span><span class="sxs-lookup"><span data-stu-id="0a355-119">Default</span></span>

  <span data-ttu-id="0a355-p101">Microsoft SaaS 서비스 및 모든 최적화 필요 하지 않은 의존 관계를 나타냅니다. 일반 인터넷 트래픽와 같은 기본 범주 트래픽을 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a355-p101">Represent Microsoft SaaS services and dependencies that do not require any optimization. You can treat Default category traffic like normal Internet traffic.</span></span>


<span data-ttu-id="0a355-122">**그림 1: 권장 하는 모든 사무실에 대 한 Microsoft SaaS 트래픽에 대 한 구성**</span><span class="sxs-lookup"><span data-stu-id="0a355-122">**Figure 1: Recommended configuration for Microsoft SaaS traffic for all offices**</span></span>

![그림 1: 권장 하는 모든 사무실에 대 한 Microsoft SaaS 트래픽에 대 한 구성](media/Network-Poster/SaaS1.png)

<span data-ttu-id="0a355-124">그림 1 지사 하 고 있는 지역 또는 중앙 위치를 포함 하 여 모든 사무실을의 권장된 구성을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="0a355-124">Figure 1 shows the recommended configuration of all offices, including branch offices and regional or central ones, in which:</span></span>

- <span data-ttu-id="0a355-125">**기본** 범주 및 일반 인터넷 트래픽을 프록시 서버와 다른 지 장치를 인터넷 기반 보안 위험 으로부터 보호 기능을 제공 하는 사무실으로 라우팅됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a355-125">**Default** category and general Internet traffic is routed to offices that have proxy servers and other edge devices to provide protection against Internet-based security risks.</span></span>
- <span data-ttu-id="0a355-126">**최적화** 하 고 **허용** 범주 트래픽은 Microsoft 네트워크 프런트엔드 연결 하는 사용자, 프록시 서버와 다른 지 장치 우회 하 여 포함 된 office와 가장 가까운 가장자리에 직접 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a355-126">**Optimize** and **Allow** category traffic is forwarded directly to the edge of the Microsoft network front end nearest to the office containing the connecting user, bypassing proxy servers and other edge devices.</span></span>

<span data-ttu-id="0a355-127">지사에서 소프트웨어 정의 광역 네트워크 (SD WAN) 장치 트래픽을 분리 되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a355-127">Software-defined wide area network (SD-WAN) devices in branch offices separate traffic so that:</span></span> 

- <span data-ttu-id="0a355-128">**기본** 범주 및 일반 인터넷 트래픽은 중앙 또는 지역 영업소 WAN 백본으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a355-128">**Default** category and general Internet traffic goes to a central or regional office over the WAN backbone.</span></span> 
- <span data-ttu-id="0a355-129">**최적화** 하 고 **허용** 범주 트래픽은 로컬 인터넷 연결을 제공 하는 ISP에 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a355-129">**Optimize** and **Allow** category traffic goes to the ISP providing the local Internet connection.</span></span>
  
<span data-ttu-id="0a355-130">자세한 내용은 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0a355-130">For more information, see:</span></span>
  
- [<span data-ttu-id="0a355-131">네트워크 연결 원칙</span><span class="sxs-lookup"><span data-stu-id="0a355-131">Network connectivity principles</span></span>](https://aka.ms/expressrouteoffice365)

- [<span data-ttu-id="0a355-132">Office 365의 네트워크 및 마이그레이션 계획</span><span class="sxs-lookup"><span data-stu-id="0a355-132">Network and migration planning for Office 365</span></span>](https://aka.ms/tune)
    
## <a name="next-step"></a><span data-ttu-id="0a355-133">다음 단계</span><span class="sxs-lookup"><span data-stu-id="0a355-133">Next step</span></span>

[<span data-ttu-id="0a355-134">Microsoft Azure PaaS에 대한 네트워킹 디자인</span><span class="sxs-lookup"><span data-stu-id="0a355-134">Designing networking for Microsoft Azure PaaS</span></span>](designing-networking-for-microsoft-azure-paas.md)
    
## <a name="see-also"></a><span data-ttu-id="0a355-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0a355-135">See also</span></span>

[<span data-ttu-id="0a355-136">Microsoft Cloud Networking for Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="0a355-136">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="0a355-137">Microsoft 클라우드 IT 아키텍처 리소스</span><span class="sxs-lookup"><span data-stu-id="0a355-137">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

