---
title: Office 365에 대한 네트워크 연결
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/01/2018
ms.audience: ITPro
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
description: Office 365는 전세계 고객에 게 인터넷 연결을 사용 하 여 서비스에 연결할 수 있도록 설계 되었습니다. 서비스 발전 함에 따라 보안, 성능 및 안정성을 Office 365는 향상 된 기반 서비스에 대 한 연결을 설정 하는 인터넷을 사용 하는 고객에 있습니다.
ms.openlocfilehash: da086aa3fcd23ccb4a82cde2a1f7d812c111071a
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2019
ms.locfileid: "25911392"
---
# <a name="network-connectivity-to-office-365"></a><span data-ttu-id="24faa-104">Office 365에 대한 네트워크 연결</span><span class="sxs-lookup"><span data-stu-id="24faa-104">Network connectivity to Office 365</span></span>

<span data-ttu-id="24faa-p102">Office 365는 전세계 고객에 게 인터넷 연결을 사용 하 여 서비스에 연결할 수 있도록 설계 되었습니다. 서비스 발전 함에 따라 보안, 성능 및 안정성을 Office 365는 향상 된 기반 서비스에 대 한 연결을 설정 하는 인터넷을 사용 하는 고객에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24faa-p102">Office 365 is designed to enable customers all over the world to connect to the service using an internet connection. As the service evolves, the security, performance, and reliability of Office 365 are improved based on customers using the internet to establish a connection to the service.</span></span>
  
<span data-ttu-id="24faa-p103">Office 365를 사용 하 여 계획 하는 고객 배포 프로젝트의 일부로 자신의 기존 수준과 예상 인터넷 연결 요구를 평가 해야 합니다. 엔터프라이즈 클래스 배포에 대 한 안정적이 고 적절 한 크기의 인터넷 연결이 사용 (영문) Office 365 기능 및 시나리오의 중요 한 부분입니다.</span><span class="sxs-lookup"><span data-stu-id="24faa-p103">Customers planning to use Office 365 should assess their existing and forecasted internet connectivity needs as a part of the deployment project. For enterprise class deployments reliable and appropriately sized internet connectivity is a critical part of consuming Office 365 features and scenarios.</span></span>
  
<span data-ttu-id="24faa-p104">대부분의 다른 사용자 및 크기 및 기본 설정에 따라 조직에서 네트워크 평가 수행할 수 있습니다. 평가의 네트워크 범위도 배포 프로세스에서에 위치에 따라 달라질 수 있습니다. 보다 잘 이해 하는 네트워크 평가 수행 하는 데 걸리는 얻을 수 있도록, 사용할 수 있는 옵션을 이해 하는데 도움이 되는 네트워크 평가 가이드를 생성 했을 때 했습니다. 이 평가 단계 및 리소스 필요한 정보 성공적으로 Office 365를 채택할 수 있도록 하는 배포 프로젝트에 추가할 수를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="24faa-p104">Network evaluations can be performed by many different people and organizations depending on your size and preferences. The network scope of the assessment can also vary depending on where you're at in your deployment process. To help you get a better understanding of what it takes to perform a network assessment, we've produced a network assessment guide to help you understand the options available to you. This assessment will determine what steps and resources need to be added to the deployment project to enable you to successfully adopt Office 365.</span></span>
  
<span data-ttu-id="24faa-p105">[Skype 작업 프레임 워크](https://www.skypeoperationsframework.com/) 에서 설명한 것과 같은 포괄적인 네트워크 평가, 네트워킹 구현 세부 사항 함께 디자인 문제를 해결할 수를 제공 합니다. 대부분의 네트워크 평가 Office 365에 대 한 네트워크 연결을 사용 하 여 [보조 구성 또는 디자인 변경](https://aka.ms/manageo365endpoints) 기존 네트워크와 인터넷 탈출 인프라를 수용할 수 있습니다 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="24faa-p105">A comprehensive network assessment, like those prescribed in the [Skype Operations Framework](https://www.skypeoperationsframework.com/) will provide possible solutions to networking design challenges along with implementation details. Most network assessments will indicate network connectivity to Office 365 can be accommodated with [minor configuration or design changes](https://aka.ms/manageo365endpoints) to the existing network and internet egress infrastructure.</span></span>

<span data-ttu-id="24faa-p106">일부 평가 Office 365에 대 한 네트워크 연결에는 네트워킹 구성 요소에 대 한 추가 투자가 필요 표시 됩니다. WAN 대역폭 또는 인터넷을 통해 연결 Office 365를 지원 하기 위해 최적화 된 라우팅 인프라 투자 예입니다. 필요에 따라 평가 사용 하는 Office 365에 대 한 네트워크 연결 [비즈니스 온라인 미디어 품질에 대 한 Skype](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917)등의 시나리오에 대 한 규정 또는 성능 요구 사항에 의해 영향을 받습니다 표시 됩니다. 이러한 추가 요구 사항에 투자 한 인터넷 연결 인프라, 라우팅 최적화 및 특수 직접 연결 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24faa-p106">Some assessments will indicate network connectivity to Office 365 will require additional investments in networking components. For example, investments in WAN bandwidth or optimized routing infrastructure to support internet connectivity to Office 365. Occasionally an assessment will indicate network connectivity to Office 365 is influenced by regulation or performance requirements for scenarios such as [Skype for Business Online media quality](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917). These additional requirements may lead to investments in internet connectivity infrastructure, routing optimization, and specialized direct connectivity.</span></span>
  
> [!NOTE]
> <span data-ttu-id="24faa-p107">Office 365에 대 한 ExpressRoute를 사용 하는 데 Microsoft 인증이 필요 합니다. Microsoft는 모든 고객 요청을 검토 하 고만 권한을 부여 ExpressRoute Office 365 사용 현황에 대 한 요구 사항을 규정 하는 고객의 요구 하는 경우 직접 연결 하는 경우. 이러한 요구 사항, 있는 경우 Microsoft 검토를 시작 하려면 [Office 365 요청 양식에 대 한 ExpressRoute](https://aka.ms/O365ERReview) 에 직접 연결 필요 하다는 것을 의미를 해석 하는 규정을 텍스트 발췌문 및 웹 링크를 제공 하십시오. Office 365에 대 한 경로 필터를 만들 권한이 없는 구독 [오류 메시지](https://support.microsoft.com/kb/3181709)를 받습니다.</span><span class="sxs-lookup"><span data-stu-id="24faa-p107">Microsoft authorization is required to use ExpressRoute for Office 365. Microsoft reviews every customer request and only authorizes ExpressRoute for Office 365 usage when a customer's regulatory requirement mandates direct connectivity. If you have such requirements, please provide the text excerpt and web link to the regulation which you interpret to mean that direct connectivity is required in the [ExpressRoute for Office 365 Request Form](https://aka.ms/O365ERReview) to begin a Microsoft review. Unauthorized subscriptions trying to create route filters for Office 365 will receive an [error message](https://support.microsoft.com/kb/3181709).</span></span>
  
<span data-ttu-id="24faa-123">Office 365에 대 한 네트워크 평가 계획할 때 고려할 주요 내용을:</span><span class="sxs-lookup"><span data-stu-id="24faa-123">Key points to consider when planning your network assessment for Office 365:</span></span>
  
- <span data-ttu-id="24faa-p108">Office 365는 공용 인터넷을 통해 실행 되는 보안, 안정성, 높은 성능을 서비스입니다. 서비스의 이러한 측면을 향상 시키기 위해 투자 계속 합니다. 모든 Office 365 서비스는 인터넷 연결을 통해 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24faa-p108">Office 365 is a secure, reliable, high performance service that runs over the public internet. We continue to invest to enhance these aspects of the service. All Office 365 services are available via internet connectivity.</span></span>

- <span data-ttu-id="24faa-p109">가용성, 글로벌 예: Office 365의 측면에 도달 하는 핵심을 지속적으로 최적화는 우리 하 고 인터넷에 대 한 성능 기반 연결 합니다. 등 대부분의 Office 365 서비스 인터넷에 연결 합니다 지 노드를 확장 집합을 활용 합니다. 이 지 네트워크 가장 근접 및 성능 인터넷을 통해 들어오는 연결을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="24faa-p109">We are continually optimizing core aspects of Office 365 such as availability, global reach, and performance for internet based connectivity. For example, many Office 365 services leverage an expanding set of internet facing edge nodes. This edge network offers the best proximity and performance to connections coming over the internet.</span></span>

- <span data-ttu-id="24faa-p110">Office 365를 사용 하 여 비즈니스 온라인 음성, 비디오, 또는 모임 기능에 대 한 Skype와 같은 포함 된 서비스 중 하나에 대 한 고려 하 고, 고객을 종단간 네트워크 평가 완료 하 고이 Skype 작업 프레임 워크를 사용 하 여 요구 사항을 충족 해야 합니다. 이러한 고객 ExpressRoute를 포함 하 여 클라우드 연결에 대 한 특정 요구를 충족 하기 위해 여러 옵션이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="24faa-p110">When considering using Office 365 for any of the included services such as Skype for Business Online voice, video, or meeting capabilities, customers must complete an end to end network assessment and meet requirements using our Skype Operations Framework. These customers will have several options to meet specific requirements for cloud connectivity, including ExpressRoute.</span></span>

<span data-ttu-id="24faa-p111">Microsoft의 사례 연구 [Microsoft Office 365에 대 한 네트워크 성능 최적화를](https://msdn.microsoft.com/en-us/library/mt450488.aspx)보세요. Office 365를 평가 하 고 및 되지 않은 경우 네트워크 평가로 시작 하거나 네트워크 디자인을 찾을 수 있는 위치를 Microsoft 계정 팀과 함께 작업 하십시오 극복 하기 위해 지원 해야 과제 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="24faa-p111">Have a look at Microsoft's case study [Optimizing network performance for Microsoft Office 365](https://msdn.microsoft.com/en-us/library/mt450488.aspx). If you're evaluating Office 365 and aren't sure where to begin with your network assessment or have found network design challenges that you need assistance to overcome, please work with your Microsoft account team.</span></span>
  
<span data-ttu-id="24faa-p112">또한 안전 하 게 Office 365 트래픽을 관리 하 고 사용 가능한 최고의 성능을 연결 원칙을 이해 하려면 [Office 365 네트워크 연결 원칙](https://aka.ms/o365networkingprinciples) 읽어보십시오. 이 문서는 안전 하 게 Office 365 네트워크 연결을 최적화 하는 것에 대 한 최신 지침을 이해 하는데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="24faa-p112">Also, read [Office 365 Network Connectivity Principles](https://aka.ms/o365networkingprinciples) to understand the connectivity principles for securely managing Office 365 traffic and getting the best possible performance. This article will help you understand the most recent guidance for securely optimizing Office 365 network connectivity.</span></span>
  
<span data-ttu-id="24faa-136">다음은 짧은 링크를 다시 사용할 수 있습니다: [ https://aka.ms/o365networkconnectivity합니다.](https://aka.ms/o365networkconnectivity)</span><span class="sxs-lookup"><span data-stu-id="24faa-136">Here's a short link you can use to come back: [https://aka.ms/o365networkconnectivity.](https://aka.ms/o365networkconnectivity)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="24faa-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="24faa-137">See also</span></span>

[<span data-ttu-id="24faa-138">Office 365 끝점 관리</span><span class="sxs-lookup"><span data-stu-id="24faa-138">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[<span data-ttu-id="24faa-139">Office 365 끝점 FAQ</span><span class="sxs-lookup"><span data-stu-id="24faa-139">Office 365 endpoints FAQ</span></span>](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
  
[<span data-ttu-id="24faa-140">Office 365 네트워크 및 성능 조정</span><span class="sxs-lookup"><span data-stu-id="24faa-140">Office 365 network and performance tuning</span></span>](network-planning-and-performance.md)
  
[<span data-ttu-id="24faa-141">Office 365용 Azure ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="24faa-141">Azure ExpressRoute for Office 365</span></span>](azure-expressroute.md)
  
[<span data-ttu-id="24faa-142">Office 365용 ExpressRoute를 사용한 라우팅</span><span class="sxs-lookup"><span data-stu-id="24faa-142">Routing with ExpressRoute for Office 365</span></span>](routing-with-expressroute.md)
  
[<span data-ttu-id="24faa-143">Office 365용 ExpressRoute를 사용한 네트워크 계획</span><span class="sxs-lookup"><span data-stu-id="24faa-143">Network planning with ExpressRoute for Office 365</span></span>](network-planning-with-expressroute.md)
  
[<span data-ttu-id="24faa-144">Office 365용 ExpressRoute 시나리오에서 BGP 커뮤니티 사용(미리 보기)</span><span class="sxs-lookup"><span data-stu-id="24faa-144">Using BGP communities in ExpressRoute for Office 365 scenarios (preview)</span></span>](bgp-communities-in-expressroute.md)
  
[<span data-ttu-id="24faa-145">비즈니스용 Skype Online의 미디어 품질 및 네트워크 연결 성능</span><span class="sxs-lookup"><span data-stu-id="24faa-145">Media Quality and Network Connectivity Performance in Skype for Business Online</span></span>](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[<span data-ttu-id="24faa-146">Office 365 URL 및 IP 주소 범위</span><span class="sxs-lookup"><span data-stu-id="24faa-146">Office 365 URLs and IP address ranges</span></span>](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[<span data-ttu-id="24faa-147">Office 365 네트워크 연결 원칙</span><span class="sxs-lookup"><span data-stu-id="24faa-147">Office 365 Network Connectivity Principles</span></span>](https://aka.ms/o365networkingprinciples)
