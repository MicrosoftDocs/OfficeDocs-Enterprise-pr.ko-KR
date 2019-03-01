---
title: Office 365의 네트워크 설정
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/01/2018
ms.audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: ''
description: '요약: Office 365의 네트워킹을 이해하려면 다음 문서를 참조하세요.'
ms.openlocfilehash: b86d4afaf204cfdd22cb4ca7c85608b384ca431a
ms.sourcegitcommit: eb52922c0ee34791fd71ae78338ab203f7761eec
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/28/2019
ms.locfileid: "30341919"
---
# <a name="set-up-your-network-for-office-365"></a><span data-ttu-id="40b2b-103">Office 365의 네트워크 설정</span><span class="sxs-lookup"><span data-stu-id="40b2b-103">Set up your network for Office 365</span></span>

<span data-ttu-id="40b2b-104">**요약:** Office 365의 네트워킹을 이해하려면 다음 문서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="40b2b-104">**Summary:** See these articles to understand networking for Office 365.</span></span>
  
<span data-ttu-id="40b2b-p101">Office 365 온보딩에서 중요한 부분은 먼저 네트워크와 인터넷 연결의 액세스가 최적화 설정되어 있는지 확인하는 것입니다. 전역으로 배포된 SaaS(Software-as-a-Service) 클라우드에 액세스하도록 온-프레미스 네트워크를 구성하는 것은 온-프레미스 데이터 센터로의 트래픽에 최적화된 기존 네트워크의 경우와는 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="40b2b-p101">An important part of your Office 365 onboarding is to first ensure that your network and Internet connections are set up for optimized access. Configuring your on-premises network to access a globally distributed Software-as-a-Service (SaaS) cloud is different from a traditional network that is optimized for traffic to on-premises datacenters.</span></span> 

<span data-ttu-id="40b2b-107">다음 문서를 사용하여 주요 차이점을 이해하고 에지 장치, 클라이언트 컴퓨터, 온-프레미스 네트워크를 수정하여 최상의 사용자 성능을 얻으세요.</span><span class="sxs-lookup"><span data-stu-id="40b2b-107">Use these articles to understand the key differences and to modify your  edge devices, client computers, and on-premises network to get the best user performance.</span></span>

## <a name="how-office-365-networking-works"></a><span data-ttu-id="40b2b-108">Office 365 네트워킹 작동 방식</span><span class="sxs-lookup"><span data-stu-id="40b2b-108">How Office 365 networking works</span></span>

<span data-ttu-id="40b2b-109">Office 365의 연결 개요는 다음 문서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="40b2b-109">See these articles for an overview of connectivity for Office 365:</span></span>

- [<span data-ttu-id="40b2b-110">Office 365 네트워킹 연결 개요</span><span class="sxs-lookup"><span data-stu-id="40b2b-110">Office 365 networking connectivity overview</span></span>](office-365-networking-overview.md)
- [<span data-ttu-id="40b2b-111">Office 365 네트워크 연결 원칙</span><span class="sxs-lookup"><span data-stu-id="40b2b-111">Office 365 network connectivity principles</span></span>](office-365-network-connectivity-principles.md)
- [<span data-ttu-id="40b2b-112">Office 365에 대한 네트워크 연결</span><span class="sxs-lookup"><span data-stu-id="40b2b-112">Network connectivity to Office 365</span></span>](network-connectivity.md)

<span data-ttu-id="40b2b-113">성능 향상에 대한 조언은 [Office 365의 네트워크 계획 및 성능 조정](network-planning-and-performance.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="40b2b-113">For advice on enhancing performance, see [Network planning and performance tuning for Office 365](network-planning-and-performance.md).</span></span>

## <a name="support-office-365-networking-as-a-network-equipment-vendor"></a><span data-ttu-id="40b2b-114">네트워크 장비 공급업체로서 Office 365 네트워킹 지원</span><span class="sxs-lookup"><span data-stu-id="40b2b-114">Support Office 365 networking as a network equipment vendor</span></span>

<span data-ttu-id="40b2b-p102">네트워크 장비 공급업체의 경우 [Office 365 네트워킹 파트너 프로그램](office-365-networking-partner-program.md)에 참가하세요. 프로그램에 등록하여 제품 및 솔루션에 Office 365 네트워크 연결 원칙을 구축하세요.</span><span class="sxs-lookup"><span data-stu-id="40b2b-p102">If you are a network equipment vendor, join the [Office 365 Networking Partner Program](office-365-networking-partner-program.md). Enroll in the program to build Office 365 network connectivity principles into your products and solutions.</span></span> 

## <a name="office-365-endpoints"></a><span data-ttu-id="40b2b-117">Office 365 엔드포인트</span><span class="sxs-lookup"><span data-stu-id="40b2b-117">Office 365 endpoints</span></span>

<span data-ttu-id="40b2b-118">엔드포인트는 인터넷에서 Office 365 트래픽을 위한 대상 IP 주소, DNS 도메인 이름, URL의 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="40b2b-118">Endpoints are the set of destination IP addresses, DNS domain names, and URLs for Office 365 traffic on the Internet.</span></span> 

<span data-ttu-id="40b2b-p103">Office 365 클라우드 기반 서비스에 대한 성능을 최적화하려면 클라이언트 브라우저와 에지 네트워크의 장치가 이러한 엔드포인트를 특별하게 처리해야 합니다. 이러한 장치로는 방화벽, SSL Break and Inspect 및 패킷 검사 장치, 데이터 손실 방지 시스템 등이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40b2b-p103">To optimize performance to Office 365 cloud-based services, these endpoints need special handling by your client browsers and the devices in your edge network. These devices include firewalls, SSL Break and Inspect and packet inspection devices, and data loss prevention systems.</span></span>

<span data-ttu-id="40b2b-121">자세한 내용은 [Office 365 엔드포인트 관리](managing-office-365-endpoints.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="40b2b-121">See [Managing Office 365 endpoints](managing-office-365-endpoints.md) for the details.</span></span>

<span data-ttu-id="40b2b-p104">현재 5개의 서로 다른 Office 365 클라우드가 있습니다. 이 표는 각 클라우드의 엔드포인트 목록으로 안내합니다.</span><span class="sxs-lookup"><span data-stu-id="40b2b-p104">There are currently five different Office 365 clouds. This table takes you to the list of endpoints for each one.</span></span>

|||
|:-------|:-----|
| [<span data-ttu-id="40b2b-124">전 세계 엔드포인트</span><span class="sxs-lookup"><span data-stu-id="40b2b-124">Worldwide endpoints</span></span>](urls-and-ip-address-ranges.md) | <span data-ttu-id="40b2b-125">미국 GCC(정부 커뮤니티 클라우드)를 포함하는 전 세계 Office 365 구독의 엔드포인트입니다.</span><span class="sxs-lookup"><span data-stu-id="40b2b-125">The endpoints for worldwide Office 365 subscriptions, which include the United States Government Community Cloud (GCC).</span></span> |
| [<span data-ttu-id="40b2b-126">미국 정부 DoD 엔드포인트</span><span class="sxs-lookup"><span data-stu-id="40b2b-126">U.S. Government DoD endpoints</span></span>](office-365-u-s-government-dod-endpoints.md) | <span data-ttu-id="40b2b-127">미국 DoD(국방부) 구독의 엔드포인트입니다.</span><span class="sxs-lookup"><span data-stu-id="40b2b-127">The endpoints for United States Department of Defense (DoD) subscriptions.</span></span> |
| [<span data-ttu-id="40b2b-128">미국 정부 GCC High 엔드포인트</span><span class="sxs-lookup"><span data-stu-id="40b2b-128">U.S. Government GCC High endpoints</span></span>](office-365-u-s-government-gcc-high-endpoints.md) | <span data-ttu-id="40b2b-129">미국 GCC(정부 커뮤니티 클라우드) High 구독의 엔드포인트입니다.</span><span class="sxs-lookup"><span data-stu-id="40b2b-129">The endpoints for United States Government Community Cloud High (GCC High) subscriptions.</span></span> |
| [<span data-ttu-id="40b2b-130">21Vianet에서 운영하는 Office 365 엔드포인트</span><span class="sxs-lookup"><span data-stu-id="40b2b-130">Office 365 operated by 21Vianet endpoints</span></span>](urls-and-ip-address-ranges-21vianet.md) | <span data-ttu-id="40b2b-131">21Vianet에서 운영하는 Office 365용 엔드포인트입니다. 중국에서 Office 365의 요구 사항을 충족하도록 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="40b2b-131">The endpoints for Office 365 operated by 21Vianet, which is designed to meet the needs for Office 365 in China.</span></span> |
| [<span data-ttu-id="40b2b-132">Office 365 Germany 끝점</span><span class="sxs-lookup"><span data-stu-id="40b2b-132">Office 365 Germany endpoints</span></span>](office-365-germany-endpoints.md) | <span data-ttu-id="40b2b-133">독일, EU(유럽 연합), EFTA(유럽 자유 무역 연합)의 가장 규제를 많이 받는 고객을 위해 유럽에 있는 별도 클라우드의 엔드포인트입니다.</span><span class="sxs-lookup"><span data-stu-id="40b2b-133">The endpoints for a separate cloud in Europe for the most regulated customers in Germany, the European Union (EU), and the European Free Trade Association (EFTA).</span></span> |
|||

<span data-ttu-id="40b2b-134">Office 365 클라우드의 최신 엔드포인트 목록을 자동으로 가져오게 만들려면 [Office 365 IP 주소 및 URL 웹 서비스](office-365-ip-web-service.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="40b2b-134">To automate getting the latest list of endpoints for your Office 365 cloud, see the [Office 365 IP Address and URL Web service](office-365-ip-web-service.md).</span></span>

<span data-ttu-id="40b2b-135">엔드포인트에 대한 추가 내용은 다음 문서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="40b2b-135">For additional endpoints, see these articles:</span></span>

- [<span data-ttu-id="40b2b-136">웹 서비스에 포함되지 않는 추가 엔드포인트</span><span class="sxs-lookup"><span data-stu-id="40b2b-136">Additional endpoints not included in the Web service</span></span>](additional-office365-ip-addresses-and-urls.md)
- [<span data-ttu-id="40b2b-137">Mac용 Office 2016의 네트워크 요청</span><span class="sxs-lookup"><span data-stu-id="40b2b-137">Network requests in Office 2016 for Mac</span></span>](network-requests-in-office-2016-for-mac.md)


## <a name="additional-topics-for-office-365-networking"></a><span data-ttu-id="40b2b-138">Office 365 네트워킹의 추가 항목</span><span class="sxs-lookup"><span data-stu-id="40b2b-138">Additional topics for Office 365 networking</span></span>

<span data-ttu-id="40b2b-139">Office 365 네트워킹의 특수한 항목은 다음 문서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="40b2b-139">See these articles for specialized topics in Office 365 networking:</span></span>

- [<span data-ttu-id="40b2b-140">콘텐츠 배달 네트워크</span><span class="sxs-lookup"><span data-stu-id="40b2b-140">Content delivery networks</span></span>](content-delivery-networks.md)
- [<span data-ttu-id="40b2b-141">Office 365 서비스의 IPv6 지원</span><span class="sxs-lookup"><span data-stu-id="40b2b-141">IPv6 support in Office 365 services</span></span>](ipv6-support.md)
- [<span data-ttu-id="40b2b-142">NAT 지원(Office 365)</span><span class="sxs-lookup"><span data-stu-id="40b2b-142">NAT support with Office 365</span></span>](nat-support-with-office-365.md)

## <a name="expressroute-for-office-365"></a><span data-ttu-id="40b2b-143">Office 365용 ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="40b2b-143">ExpressRoute for Office 365</span></span>

<span data-ttu-id="40b2b-144">Office 365 트래픽의 ExpressRoute 사용에 대한 자세한 내용은 다음 문서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="40b2b-144">See these articles for information on the use of ExpressRoute for Office 365 traffic:</span></span>

- [<span data-ttu-id="40b2b-145">Office 365용 Azure ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="40b2b-145">Azure ExpressRoute for Office 365</span></span>](azure-expressroute.md)
- [<span data-ttu-id="40b2b-146">Office 365용 ExpressRoute 구현</span><span class="sxs-lookup"><span data-stu-id="40b2b-146">Implementing ExpressRoute for Office 365</span></span>](implementing-expressroute.md)
- [<span data-ttu-id="40b2b-147">Office 365용 ExpressRoute를 사용한 네트워크 계획</span><span class="sxs-lookup"><span data-stu-id="40b2b-147">Network planning with ExpressRoute for Office 365</span></span>](network-planning-with-expressroute.md)
- [<span data-ttu-id="40b2b-148">Office 365용 ExpressRoute를 사용한 라우팅</span><span class="sxs-lookup"><span data-stu-id="40b2b-148">Routing with ExpressRoute for Office 365</span></span>](routing-with-expressroute.md)
