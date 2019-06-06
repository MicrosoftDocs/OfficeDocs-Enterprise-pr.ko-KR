---
title: Office 365 네트워크 연결 평가
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/5/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 64b420ef-0218-48f6-8a34-74bb27633b10
description: Office 365은 전세계의 모든 고객이 인터넷 연결을 사용 하 여 서비스에 연결할 수 있도록 하기 위한 것입니다. 서비스가 발전 함에 따라 Office 365의 보안, 성능 및 안정성이 인터넷을 사용 하 여 서비스에 대 한 연결을 설정 하는 고객에 따라 개선 됩니다.
ms.openlocfilehash: 3ea80ddccaf9fabbe158a10f0af1d35dbf3a9889
ms.sourcegitcommit: 0449c6f854c682719cac1bd0d086f2e3b20078b9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/05/2019
ms.locfileid: "34724828"
---
# <a name="assessing-office-365-network-connectivity"></a><span data-ttu-id="8afa8-104">Office 365 네트워크 연결 평가</span><span class="sxs-lookup"><span data-stu-id="8afa8-104">Assessing Office 365 network connectivity</span></span>

<span data-ttu-id="8afa8-105">Office 365은 전세계의 모든 고객이 인터넷 연결을 사용 하 여 서비스에 연결할 수 있도록 하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="8afa8-105">Office 365 is designed to enable customers all over the world to connect to the service using an internet connection.</span></span> <span data-ttu-id="8afa8-106">서비스가 발전 함에 따라 Office 365의 보안, 성능 및 안정성이 인터넷을 사용 하 여 서비스에 대 한 연결을 설정 하는 고객에 따라 개선 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8afa8-106">As the service evolves, the security, performance, and reliability of Office 365 are improved based on customers using the internet to establish a connection to the service.</span></span>
  
<span data-ttu-id="8afa8-107">Office 365을 사용 하려는 고객은 기존 및 예상 인터넷 연결 요구 사항을 배포 프로젝트의 일부로 평가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8afa8-107">Customers planning to use Office 365 should assess their existing and forecasted internet connectivity needs as a part of the deployment project.</span></span> <span data-ttu-id="8afa8-108">엔터프라이즈 클래스 배포를 안정적이 고 적절 한 크기의 인터넷 연결을 사용 하는 것은 Office 365 기능과 시나리오를 소비 하는 중요 한 부분입니다.</span><span class="sxs-lookup"><span data-stu-id="8afa8-108">For enterprise class deployments reliable and appropriately sized internet connectivity is a critical part of consuming Office 365 features and scenarios.</span></span>
  
<span data-ttu-id="8afa8-109">네트워크 평가는 크기 및 기본 설정에 따라 다양 한 사용자 및 조직에서 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8afa8-109">Network evaluations can be performed by many different people and organizations depending on your size and preferences.</span></span> <span data-ttu-id="8afa8-110">또한 평가의 네트워크 범위는 배포 프로세스의 위치에 따라 달라질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8afa8-110">The network scope of the assessment can also vary depending on where you're at in your deployment process.</span></span> <span data-ttu-id="8afa8-111">네트워크 평가를 수행 하는 데 필요한 정보를 보다 쉽게 이해할 수 있도록 지원 되는 옵션을 이해 하는 데 도움이 되는 네트워크 평가 가이드를 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="8afa8-111">To help you get a better understanding of what it takes to perform a network assessment, we've produced a network assessment guide to help you understand the options available to you.</span></span> <span data-ttu-id="8afa8-112">이 평가에서는 Office 365을 성공적으로 채택할 수 있도록 배포 프로젝트에 추가 해야 하는 단계 및 리소스를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8afa8-112">This assessment will determine what steps and resources need to be added to the deployment project to enable you to successfully adopt Office 365.</span></span>
  
<span data-ttu-id="8afa8-113">포괄적인 네트워크 평가는 [Skype 작업 프레임 워크](https://www.skypeoperationsframework.com/) 에 규정 된 것과 마찬가지로 구현 정보와 함께 네트워킹 디자인 문제에 대 한 가능한 솔루션을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="8afa8-113">A comprehensive network assessment, like those prescribed in the [Skype Operations Framework](https://www.skypeoperationsframework.com/) will provide possible solutions to networking design challenges along with implementation details.</span></span> <span data-ttu-id="8afa8-114">대부분의 네트워크 평가는 기존 네트워크 및 인터넷 송신 인프라에 대 한 [경미한 구성 또는 디자인 변경을](https://aka.ms/manageo365endpoints) 통해 Office 365에 대 한 네트워크 연결을 수용할 수 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8afa8-114">Most network assessments will indicate network connectivity to Office 365 can be accommodated with [minor configuration or design changes](https://aka.ms/manageo365endpoints) to the existing network and internet egress infrastructure.</span></span>

<span data-ttu-id="8afa8-115">Office 365에 대 한 네트워크 연결을 나타내는 몇 가지 평가는 네트워킹 구성 요소에 대 한 추가 투자가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="8afa8-115">Some assessments will indicate network connectivity to Office 365 will require additional investments in networking components.</span></span> <span data-ttu-id="8afa8-116">예를 들어, Office 365에 대 한 인터넷 연결을 지원 하기 위해 WAN 대역폭에 투자 하거나 최적화 된 라우팅 인프라를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8afa8-116">For example, investments in WAN bandwidth or optimized routing infrastructure to support internet connectivity to Office 365.</span></span> <span data-ttu-id="8afa8-117">경우에 따라 평가는 Office 365에 대 한 네트워크 연결이 [비즈니스용 Skype 온라인 미디어 품질과](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917)같은 시나리오에 대 한 규제 또는 성능 요구 사항의 영향을 받게 되는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8afa8-117">Occasionally an assessment will indicate network connectivity to Office 365 is influenced by regulation or performance requirements for scenarios such as [Skype for Business Online media quality](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917).</span></span> <span data-ttu-id="8afa8-118">이러한 추가 요구 사항에 따라 인터넷 연결 인프라, 라우팅 최적화 및 특수 직접 연결에 대 한 투자가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8afa8-118">These additional requirements may lead to investments in internet connectivity infrastructure, routing optimization, and specialized direct connectivity.</span></span>
  
> [!NOTE]
> <span data-ttu-id="8afa8-119">Microsoft authorization는 Office 365 용 Express 경로를 사용 하는 데 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="8afa8-119">Microsoft authorization is required to use ExpressRoute for Office 365.</span></span> <span data-ttu-id="8afa8-120">고객의 규정 요구 사항에 직접 연결 하는 경우 Microsoft는 모든 고객 요청을 검토 하 고 Office 365 사용에 대 한 사용자만 권한 부여를 승인 합니다.</span><span class="sxs-lookup"><span data-stu-id="8afa8-120">Microsoft reviews every customer request and only authorizes ExpressRoute for Office 365 usage when a customer's regulatory requirement mandates direct connectivity.</span></span> <span data-ttu-id="8afa8-121">이러한 요구 사항을 충족 하는 경우 해석 하는 규정에 대 한 텍스트 발췌문 및 웹 링크를 제공 하 여 Microsoft 검토를 시작 하기 [위한 Office 365의 express 경로 요청 양식에](https://aka.ms/O365ERReview) 직접 연결이 필요 하다는 것을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="8afa8-121">If you have such requirements, please provide the text excerpt and web link to the regulation which you interpret to mean that direct connectivity is required in the [ExpressRoute for Office 365 Request Form](https://aka.ms/O365ERReview) to begin a Microsoft review.</span></span> <span data-ttu-id="8afa8-122">인증 되지 않은 구독에서 Office 365에 대 한 경로 필터를 만들려고 하면 [오류 메시지가](https://support.microsoft.com/kb/3181709)표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8afa8-122">Unauthorized subscriptions trying to create route filters for Office 365 will receive an [error message](https://support.microsoft.com/kb/3181709).</span></span>
  
<span data-ttu-id="8afa8-123">Office 365에 대 한 네트워크 평가를 계획할 때 고려해 야 할 주요 사항은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8afa8-123">Key points to consider when planning your network assessment for Office 365:</span></span>
  
- <span data-ttu-id="8afa8-124">Office 365은 공용 인터넷을 통해 실행 되는 안전 하 고 신뢰할 수 있는 고성능 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="8afa8-124">Office 365 is a secure, reliable, high performance service that runs over the public internet.</span></span> <span data-ttu-id="8afa8-125">서비스의 이러한 측면을 개선 하기 위해 계속 투자 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8afa8-125">We continue to invest to enhance these aspects of the service.</span></span> <span data-ttu-id="8afa8-126">인터넷 연결을 통해 모든 Office 365 서비스를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8afa8-126">All Office 365 services are available via internet connectivity.</span></span>

- <span data-ttu-id="8afa8-127">Microsoft는 가용성, 글로벌, 인터넷 기반 연결에 대 한 성능과 같은 Office 365의 핵심 측면을 지속적으로 최적화 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8afa8-127">We are continually optimizing core aspects of Office 365 such as availability, global reach, and performance for internet based connectivity.</span></span> <span data-ttu-id="8afa8-128">예를 들어 많은 Office 365 서비스는 확장 된 인터넷 연결에 지 노드 집합을 활용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8afa8-128">For example, many Office 365 services leverage an expanding set of internet facing edge nodes.</span></span> <span data-ttu-id="8afa8-129">이에 지 네트워크는 인터넷을 통해 들어오는 연결에 대해 가장 적합 한 근접성 및 성능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="8afa8-129">This edge network offers the best proximity and performance to connections coming over the internet.</span></span>

- <span data-ttu-id="8afa8-130">비즈니스용 Skype Online 음성, 비디오 또는 모임 기능과 같은 포함 된 서비스에 대해 Office 365을 사용 하는 경우, 고객은 종단 간 네트워크 평가를 완료 하 고 Skype 운영 프레임 워크를 사용 하 여 요구 사항을 충족 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8afa8-130">When considering using Office 365 for any of the included services such as Skype for Business Online voice, video, or meeting capabilities, customers must complete an end to end network assessment and meet requirements using our Skype Operations Framework.</span></span> <span data-ttu-id="8afa8-131">이러한 고객은 Express 경로를 포함 하 여 클라우드 연결에 대 한 특정 요구 사항을 충족 하는 여러 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8afa8-131">These customers will have several options to meet specific requirements for cloud connectivity, including ExpressRoute.</span></span>

<span data-ttu-id="8afa8-132">Microsoft [Office 365의 네트워크 성능 최적화](https://msdn.microsoft.com/en-us/library/mt450488.aspx)를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="8afa8-132">Have a look at Microsoft's case study [Optimizing network performance for Microsoft Office 365](https://msdn.microsoft.com/en-us/library/mt450488.aspx).</span></span> <span data-ttu-id="8afa8-133">Office 365을 평가 중 이며 네트워크 평가로 시작할 위치를 잘 모르거나 문제를 해결 하는 데 도움이 필요한 네트워크 디자인 문제가 있는지 확실 하지 않은 경우 Microsoft 계정 팀에 문의 하세요.</span><span class="sxs-lookup"><span data-stu-id="8afa8-133">If you're evaluating Office 365 and aren't sure where to begin with your network assessment or have found network design challenges that you need assistance to overcome, please work with your Microsoft account team.</span></span>
  
<span data-ttu-id="8afa8-134">또한 [office 365 네트워크 연결 원칙](https://aka.ms/o365networkingprinciples) 을 읽으면 office 365 트래픽을 안전 하 게 관리 하 고 가능한 최적의 성능을 얻는 데 필요한 연결 원리를 파악할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8afa8-134">Also, read [Office 365 Network Connectivity Principles](https://aka.ms/o365networkingprinciples) to understand the connectivity principles for securely managing Office 365 traffic and getting the best possible performance.</span></span> <span data-ttu-id="8afa8-135">이 문서는 Office 365 네트워크 연결을 안전 하 게 최적화 하기 위한 가장 최근 지침을 이해 하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8afa8-135">This article will help you understand the most recent guidance for securely optimizing Office 365 network connectivity.</span></span>

## <a name="the-office-365-network-onboarding-tool"></a><span data-ttu-id="8afa8-136">Office 365 네트워크 온 보 딩 도구</span><span class="sxs-lookup"><span data-stu-id="8afa8-136">The Office 365 Network Onboarding tool</span></span>

<span data-ttu-id="8afa8-137">[Office 365 네트워크 온 보 딩 도구인](https://aka.ms/netonboard)새 개념 증명 (POC) 도구를 사용 하 여 지정 된 사용자 위치와 Office 365 사이에 적용할 수 있는 네트워킹 연결 개선 사항에 대 한 특정 지침을 제공 하는 기본 연결 테스트를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8afa8-137">You can use the [Office 365 Network Onboarding tool](https://aka.ms/netonboard), a new proof of concept (POC) tool, to run basic connectivity tests that provide specific guidance about networking connectivity improvements that can be made between a given user location and Office 365.</span></span>

<span data-ttu-id="8afa8-138">네트워크 온 보 딩 도구는 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="8afa8-138">The Network Onboarding tool does the following:</span></span>

- <span data-ttu-id="8afa8-139">위치를 검색 하거나 테스트할 위치를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8afa8-139">Detects your location, or you can specify a location to test</span></span>
- <span data-ttu-id="8afa8-140">네트워크 송신 위치를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="8afa8-140">Checks the location of your network egress</span></span>
- <span data-ttu-id="8afa8-141">네트워크 경로에서 가장 가까운 Office 365 서비스 전면 도어를 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="8afa8-141">Tests the network path to the nearest Office 365 service front door</span></span>

<span data-ttu-id="8afa8-142">이 도구는 다음 정보를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="8afa8-142">The tool displays the following information:</span></span>

- <span data-ttu-id="8afa8-143">결과 및 영향 탭</span><span class="sxs-lookup"><span data-stu-id="8afa8-143">Results and impact tab</span></span>
  - <span data-ttu-id="8afa8-144">사용 중 서비스 전면 도어 맵의 위치</span><span class="sxs-lookup"><span data-stu-id="8afa8-144">The location on a map of the in-use service front door</span></span>
  - <span data-ttu-id="8afa8-145">최적의 연결을 제공 하는 다른 서비스 전면 문의 맵의 위치</span><span class="sxs-lookup"><span data-stu-id="8afa8-145">The location on a map of other service front doors that would provide optimal connectivity</span></span>
  - <span data-ttu-id="8afa8-146">사용자 가까이에 있는 다른 Office 365 고객에 비해 상대적인 성능</span><span class="sxs-lookup"><span data-stu-id="8afa8-146">Relative performance compared to other Office 365 customers near you</span></span>
- <span data-ttu-id="8afa8-147">세부 정보 및 솔루션 탭</span><span class="sxs-lookup"><span data-stu-id="8afa8-147">Details and solutions tab</span></span>
  - <span data-ttu-id="8afa8-148">구/군/시 및 국가별로 사용자 위치</span><span class="sxs-lookup"><span data-stu-id="8afa8-148">User location by city and country</span></span>
  - <span data-ttu-id="8afa8-149">구/군/시, 시/도를 사용한 네트워크 송신 위치</span><span class="sxs-lookup"><span data-stu-id="8afa8-149">Network egress location by city, state and country</span></span>
  - <span data-ttu-id="8afa8-150">사용자에서 네트워크로의 송신 거리</span><span class="sxs-lookup"><span data-stu-id="8afa8-150">User to network egress distance</span></span>
  - <span data-ttu-id="8afa8-151">Office 365 Exchange Online 서비스 전면 도어 위치</span><span class="sxs-lookup"><span data-stu-id="8afa8-151">Office 365 Exchange Online service front door location</span></span>
  - <span data-ttu-id="8afa8-152">최적의 Office 365 사용자 위치에 대 한 Exchange Online 서비스 프런트 도어</span><span class="sxs-lookup"><span data-stu-id="8afa8-152">Optimal Office 365 Exchange Online service front door(s) for user location</span></span>
  - <span data-ttu-id="8afa8-153">사용자의 metro 영역에 있는 고객 (성능 향상)</span><span class="sxs-lookup"><span data-stu-id="8afa8-153">Customers in your metro area with better performance</span></span>

<span data-ttu-id="8afa8-154">Office 365 네트워크의 온 보 딩 도구 릴리스에 대해 자세히 살펴보고 [office 365 네트워크 성능 도구 POC 릴리스](https://techcommunity.microsoft.com/t5/Office-365-Networking/Office-365-Network-Performance-tool-POC-release/m-p/319579#M102) 블로그 게시물에 의견을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8afa8-154">You can read about the Office 365 Network Onboarding tool release and provide feedback at the [Office 365 Network Performance tool POC release](https://techcommunity.microsoft.com/t5/Office-365-Networking/Office-365-Network-Performance-tool-POC-release/m-p/319579#M102) blog post.</span></span> <span data-ttu-id="8afa8-155">이 도구 및 기타 Office 365 네트워킹 업데이트에 대 한 이후 업데이트에 대 한 정보가 [Office 365 네트워킹](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking) 블로그에 게시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8afa8-155">Information about future updates to this tool and other Office 365 networking updates will be posted to the [Office 365 Networking](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking) blog.</span></span>
  
<span data-ttu-id="8afa8-156">여기서는 다음을 수행 [ https://aka.ms/o365networkconnectivity하는 데 사용할 수 있는 간단한 링크를 제공 합니다.](https://aka.ms/o365networkconnectivity)</span><span class="sxs-lookup"><span data-stu-id="8afa8-156">Here's a short link you can use to come back: [https://aka.ms/o365networkconnectivity.](https://aka.ms/o365networkconnectivity)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="8afa8-157">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8afa8-157">See also</span></span>

[<span data-ttu-id="8afa8-158">Office 365 네트워크 연결 개요</span><span class="sxs-lookup"><span data-stu-id="8afa8-158">Office 365 Network Connectivity Overview</span></span>](office-365-networking-overview.md)

[<span data-ttu-id="8afa8-159">Office 365 네트워크 연결 원칙</span><span class="sxs-lookup"><span data-stu-id="8afa8-159">Office 365 Network Connectivity Principles</span></span>](https://aka.ms/o365networkingprinciples)

[<span data-ttu-id="8afa8-160">Office 365 끝점 관리</span><span class="sxs-lookup"><span data-stu-id="8afa8-160">Managing Office 365 endpoints</span></span>](managing-office-365-endpoints.md)

[<span data-ttu-id="8afa8-161">Office 365 URL 및 IP 주소 범위</span><span class="sxs-lookup"><span data-stu-id="8afa8-161">Office 365 URLs and IP address ranges</span></span>](urls-and-ip-address-ranges.md)

[<span data-ttu-id="8afa8-162">Office 365 IP 주소 및 URL 웹 서비스</span><span class="sxs-lookup"><span data-stu-id="8afa8-162">Office 365 IP Address and URL Web service</span></span>](office-365-ip-web-service.md)

[<span data-ttu-id="8afa8-163">Office 365 네트워크 및 성능 조정</span><span class="sxs-lookup"><span data-stu-id="8afa8-163">Office 365 network and performance tuning</span></span>](network-planning-and-performance.md)
