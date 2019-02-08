---
title: Office 365 네트워크 연결 개요 (영문)
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 9/12/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: 네트워크 최적화는 SaaS 서비스, Office 365 네트워킹의 목표에 대 한 중요 한 이유에 대해 설명 하며 SaaS 다른 작업에서 서로 다른 네트워킹을 요구 하는 방법입니다.
ms.openlocfilehash: 4acaee86136c88e5ac5b3c795f594fb056d15204
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897211"
---
# <a name="office-365-network-connectivity-overview"></a><span data-ttu-id="84aa9-103">Office 365 네트워크 연결 개요 (영문)</span><span class="sxs-lookup"><span data-stu-id="84aa9-103">Office 365 network connectivity overview</span></span>

<span data-ttu-id="84aa9-p101">Office 365은 마이크로 서비스 및 응용 프로그램의 다양 한 집합을 통해 생산성 및 공동 작업 시나리오를 제공 하는 분산된 소프트웨어--a-서비스로 (SaaS) 클라우드입니다. Outlook, Word 및 PowerPoint와 같은 Office 365의 클라이언트 구성 요소는 사용자 컴퓨터에서 실행 하 고 다른 구성 요소에 Office 365의 Microsoft 데이터 센터에서 실행 하는 연결 합니다. Office 365 최종 사용자 경험의 품질을 결정 하는 가장 중요 한 요소에는 네트워크 안정성과 Office 365 클라이언트 및 Office 365 서비스 앞면 도어 간에 낮은 대기 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="84aa9-p101">Office 365 is a distributed Software-as-a-Service (SaaS) cloud that provides productivity and collaboration scenarios through a diverse set of micro-services and applications. Client components of Office 365 such as Outlook, Word and PowerPoint run on user computers and connect to other components of Office 365 that run in Microsoft datacenters. The most significant factor that determines the quality of the Office 365 end user experience is network reliability and low latency between Office 365 clients and Office 365 service front doors.</span></span>

<span data-ttu-id="84aa9-107">이 문서에서는 네트워킹, Office 365의 목표에 대해 배웁니다 하며 Office 365 네트워킹 일반 인터넷 트래픽 보다 최적화 하는 다른 접근 방법을 요구 하는 이유 합니다.</span><span class="sxs-lookup"><span data-stu-id="84aa9-107">In this article, you will learn about the goals of Office 365 networking, and why Office 365 networking requires a different approach to optimization than generic Internet traffic.</span></span>

## <a name="office-365-networking-goals"></a><span data-ttu-id="84aa9-108">Office 365 네트워킹 목표</span><span class="sxs-lookup"><span data-stu-id="84aa9-108">Office 365 networking goals</span></span>

<span data-ttu-id="84aa9-p102">Office 365 네트워킹의 궁극적인 목표 클라이언트와 가장 가까운 Office 365 끝점 간의 제한 수준이 가장 낮은 액세스를 사용 하 여 최종 사용자 경험을 최적화 하는 것입니다. 최종 사용자 경험의 품질은 성능 및 사용자를 사용 하는 응용 프로그램의 응답이 직접적인 관련이 있습니다. 사용자 전화 통화, 회 및 공유 화면 공동 작업은 결함 없는 하 고 Outlook는 서버쪽 인덱싱 및 AI를 활용 하는 빠른 검색 기능에 대 한 유용한 네트워킹 연결에서 사용 하 여 있도록 Microsoft 팀의 낮은 대기 시간에 의존 예 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="84aa9-p102">The ultimate goal of Office 365 networking is to optimize the end user experience by enabling the least restrictive access between clients and the closest Office 365 endpoints. The quality of end user experience is directly related to the performance and responsiveness of the application that the user is using. For example, Microsoft Teams relies on low latency so that user phone calls, conferences and shared screen collaborations are glitch-free, and Outlook relies on great networking connectivity for instant search features that leverage server-side indexing and AI capabilities.</span></span>

<span data-ttu-id="84aa9-p103">네트워크 디자인의 주요 목표는 클라이언트 컴퓨터에서 왕복 시간 (RTT)을 줄이면 대기 시간을 최소화 하기 위해 Microsoft 글로벌 네트워크 대기 시간이 적은 Microsoft의 데이터 센터의 모든 상호 연결 하는 Microsoft의 공용 네트워크 백본에 여야 합니다. 고가용성 클라우드 응용 프로그램 진입점 전세계에 분산 합니다. Microsoft 글로벌 네트워크 [어떻게 Microsoft 구축 하는 신속 하 고 신뢰할 수 있는 전역 네트워크에](https://azure.microsoft.com/en-us/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)대 한 자세한 내용을 알아보십시오.</span><span class="sxs-lookup"><span data-stu-id="84aa9-p103">The primary goal in the network design should be to minimize latency by reducing the round-trip time (RTT) from client machines to the Microsoft Global Network, Microsoft's public network backbone that interconnects all of Microsoft's datacenters with low latency, high availability cloud application entry points spread around the world. You can learn more about the Microsoft Global Network at [How Microsoft builds its fast and reliable global network](https://azure.microsoft.com/en-us/blog/how-microsoft-builds-its-fast-and-reliable-global-network/).</span></span>

<span data-ttu-id="84aa9-p104">Office 365 네트워크 성능 최적화 복잡 하 게 할 필요 하지 않습니다. 몇가지 주요 원칙에 따라 수행 하 여 최상의 성능을 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84aa9-p104">Optimizing Office 365 network performance doesn't need to be complicated. You can get the best possible performance by following a few key principles:</span></span>

- <span data-ttu-id="84aa9-116">Office 365 네트워크 트래픽을 확인합니다</span><span class="sxs-lookup"><span data-stu-id="84aa9-116">Identify Office 365 network traffic</span></span>
- <span data-ttu-id="84aa9-117">사용자가 Office 365에 연결 하는 있는 각 위치에서 인터넷에 로컬 분기 탈출 Office 365 네트워크 트래픽 허용</span><span class="sxs-lookup"><span data-stu-id="84aa9-117">Allow local branch egress of Office 365 network traffic to the internet from each location where users connect to Office 365</span></span>
- <span data-ttu-id="84aa9-118">Office 365 트래픽을 프록시 및 패킷 검사 장치를 무시 하도록 허용</span><span class="sxs-lookup"><span data-stu-id="84aa9-118">Allow Office 365 traffic to bypass proxies and packet inspection devices</span></span>

<span data-ttu-id="84aa9-119">Office 365 네트워크 연결 원칙에 대 한 자세한 내용은 [Office 365 네트워크 연결 원칙](office-365-network-connectivity-principles.md)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="84aa9-119">For more information on Office 365 network connectivity principles, see [Office 365 Network Connectivity Principles](office-365-network-connectivity-principles.md).</span></span>

## <a name="traditional-network-architectures-and-saas"></a><span data-ttu-id="84aa9-120">기존 네트워크 아키텍처 및 SaaS</span><span class="sxs-lookup"><span data-stu-id="84aa9-120">Traditional network architectures and SaaS</span></span>

<span data-ttu-id="84aa9-p105">클라이언트/서버 작업 부하에 대 한 일반 네트워크 아키텍처 원칙은 회사 네트워크 경계 외부 클라이언트와 끝점 간의 트래픽을 확장 하지 않으므로 가정 중심으로 설계 되었습니다. 또한 대부분의 기업 네트워크에서 모든 아웃 바운드 인터넷 연결 회사 네트워크를 통과 하 고 중앙 위치에서 탈출.</span><span class="sxs-lookup"><span data-stu-id="84aa9-p105">Traditional network architecture principles for client/server workloads are designed around the assumption that traffic between clients and endpoints does not extend outside the corporate network perimeter. Also, in many enterprise networks, all outbound Internet connections traverse the corporate network, and egress from a central location.</span></span>

<span data-ttu-id="84aa9-p106">일반 인터넷 트래픽에 대 한 높은 대기 시간 네트워크 경계 보안을 유지 하기 위해 필요한 장단점이 전통적인 네트워크 아키텍처에서 및 업그레이드 또는 수평 확장에 일반적으로 인터넷 트래픽에 대 한 성능 최적화 관련 된 네트워크 탈출 지점의 장비입니다. 그러나이 방법을 Office 365와 같은 SaaS 서비스의 최적의 네트워크 성능에 대 한 요구 사항은 다루지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="84aa9-p106">In traditional network architectures, higher latency for generic Internet traffic is a necessary tradeoff in order to maintain network perimeter security, and performance optimization for Internet traffic typically involves upgrading or scaling out the equipment at network egress points. However, this approach does not address the requirements for optimum network performance of SaaS services such as Office 365.</span></span>

## <a name="identifying-office-365-network-traffic"></a><span data-ttu-id="84aa9-125">Office 365 네트워크 트래픽 식별</span><span class="sxs-lookup"><span data-stu-id="84aa9-125">Identifying Office 365 network traffic</span></span>

<span data-ttu-id="84aa9-126">간편 하 게 Office 365 네트워크 트래픽을 확인 하 고 네트워크 id 관리를 간단 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="84aa9-126">We're making it easier to identify Office 365 network traffic and making it simpler to manage the network identification.</span></span>

- <span data-ttu-id="84aa9-p107">인터넷 대기 시간이 영향을 받지는 네트워크 트래픽으로부터 매우 중요 한 네트워크 트래픽을 구분 하기 위한 네트워크 끝점의 새 범주입니다. 약간의 Url 및 지원 IP 주소는 가장 중요 한 "최적화" 범주에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84aa9-p107">New categories of network endpoints to differentiate highly critical network traffic from network traffic which is not impacted by Internet latencies. There are just a handful of URLs and supporting IP Addresses in the most critical “Optimize” category.</span></span>
- <span data-ttu-id="84aa9-p108">스크립트 사용 또는 Office 365의 직접 장치 구성 및 변경 관리를 위한 웹 서비스 네트워크 식별 합니다. 변경이 웹 서비스에서 또는 RSS 형식에서 또는 Microsoft 흐름 서식 파일을 사용 하 여 전자 메일에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84aa9-p108">Web services for script usage or direct device configuration and change management of Office 365 network identification. Changes are available from the web service, or in RSS format, or on email using a Microsoft Flow template.</span></span>
- <span data-ttu-id="84aa9-131">장치 또는 Office 365 네트워크 연결 원칙을 따르는 되 고 간단한 구성을 서비스를 제공 하는 Microsoft 파트너와 [office 365 네트워크 파트너 프로그램](http://aka.ms/Office365NPP) 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="84aa9-131">[Office 365 Network partner program](http://aka.ms/Office365NPP) with Microsoft partners who provide devices or services that follow Office 365 network connectivity principles and have simple configuration.</span></span>

## <a name="securing-office-365-connections"></a><span data-ttu-id="84aa9-132">Office 365 연결 보호</span><span class="sxs-lookup"><span data-stu-id="84aa9-132">Securing Office 365 connections</span></span>

<span data-ttu-id="84aa9-p109">기존 네트워크 보안의 목표 침입 및 악의적인 이용에 대 한 회사 네트워크 경계를 강화 하는 것입니다. 대부분의 기업 네트워크 프록시 서버, 방화벽, SSL 나누기와 같은 기술을 사용 하 여 인터넷 트래픽에 대 한 네트워크 보안을 강화 하 고 상세 패킷 검사 및 데이터 손실 방지 시스템 검사 합니다. 이러한 기술을 일반 인터넷 요청에 대 한 중요 한 위험 완화를 제공 하지만 성능, 확장성 및 Office 365 끝점에 적용 하면 최종 사용자 경험의 품질을 대폭 절감할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84aa9-p109">The goal of traditional network security is to harden the corporate network perimeter against intrusion and malicious exploits. Most enterprise networks enforce network security for Internet traffic using technologies like proxy servers, firewalls, SSL break and inspect, deep packet inspection, and data loss prevention systems. These technologies provide important risk mitigation for generic Internet requests but can dramatically reduce performance, scalability, and the quality of end user experience when applied to Office 365 endpoints.</span></span>

<span data-ttu-id="84aa9-p110">Office 365 콘텐츠 보안 및 데이터 사용 현황 준수 Office 365 기능 및 작업을 위해 특별히 설계 된 기본 제공 보안 및 관리 방식 기능에 대 한 조직의 요구를 충족 하는 하는데 도움이 됩니다. Office 365 보안 및 규정 준수 하는 방법에 대 한 자세한 내용은 [Office 365 보안 로드맵](https://docs.microsoft.com/en-us/office365/securitycompliance/security-roadmap)을 참조 하십시오. Office 365 트래픽을 고급 수준 처리를 수행 하는 고급 네트워크 솔루션에서 Microsoft의 권장 사항 및 지원 위치 하는 방법에 대 한 자세한 내용은 [타사 네트워크 장치 또는 Office 365 트래픽에서 솔루션을 사용 하 여](https://support.microsoft.com/en-us/help/2690045)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="84aa9-p110">Office 365 helps meet your organization's needs for content security and data usage compliance with built-in security and governance features designed specifically for Office 365 features and workloads. For more information about Office 365 security and compliance, see the [Office 365 security roadmap](https://docs.microsoft.com/en-us/office365/securitycompliance/security-roadmap). For more information about Microsoft’s recommendations and support position on advanced network solutions that perform advanced-level processing on Office 365 traffic, see [Using third-party network devices or solutions on Office 365 traffic](https://support.microsoft.com/en-us/help/2690045).</span></span>

## <a name="why-is-office-365-networking-different"></a><span data-ttu-id="84aa9-139">Office 365는 왜 다른 네트워킹?</span><span class="sxs-lookup"><span data-stu-id="84aa9-139">Why is Office 365 networking different?</span></span>

<span data-ttu-id="84aa9-p111">Office 365 끝점 보안 및 경계 보안을 적용에 대 한 필요성을 줄이고 암호화 된 네트워크 연결을 사용 하 여 최적의 성능을 위해 설계 되었습니다. Office 365 데이터 센터는 전세계 있으며 최상의 사용할 수 있는 서비스 끝점에 연결 하는 클라이언트에 대 한 다양 한 메서드를 사용 하는 서비스는 설계 되었습니다. 사용자 데이터 및 처리 많은 Microsoft 데이터 센터 간의 배포 이므로 단일 네트워크 끝점이 컴퓨터는 클라이언트에 연결할 수 없습니다. 사실, 데이터 및 Office 365 테 넌 트에 서비스에 있는 최종 사용자가 액세스는 지리적 위치에 맞게 Microsoft 글로벌 네트워크에서 동적으로 최적화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="84aa9-p111">Office 365 is designed for optimal performance using endpoint security and encrypted network connections, reducing the need for perimeter security enforcement. Office 365 datacenters are located across the world and the service is designed to use various methods for connecting clients to best available service endpoints. Since user data and processing is distributed between many Microsoft datacenters, there is no single network endpoint to which client machines can connect. In fact, data and services in your Office 365 tenant are dynamically optimized by the Microsoft Global Network to adapt to the geographic locations from which they are accessed by end users.</span></span>

<span data-ttu-id="84aa9-144">특정 일반적인 성능 문제는 Office 365 트래픽이 패킷 검사 및 중앙 집중화 된 탈출 때 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="84aa9-144">Certain common performance issues are created when Office 365 traffic is subject to packet inspection and centralized egress:</span></span>

- <span data-ttu-id="84aa9-145">매우 불량 비디오 및 오디오 스트림 성능과 데이터 검색, 검색, 실시간 공동 작업, 일정 약속 있음/없음 정보, 제품에서 콘텐츠 및 기타 서비스의 느린 응답 발생할 수도 있는 높은 대기 시간</span><span class="sxs-lookup"><span data-stu-id="84aa9-145">High latency can cause extremely poor performance of video and audio streams, and slow response of data retrieval, searches, real-time collaboration, calendar free/busy information, in-product content and other services</span></span>
- <span data-ttu-id="84aa9-146">Office 365 전역 네트워크의 중앙 위치 비교 동적 라우팅 기능에서에서 연결을 egressing, 대기 시간 및 왕복 대기 시간을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="84aa9-146">Egressing connections from a central location defeats the dynamic routing capabilities of the Office 365 global network, adding latency and round-trip time</span></span>
- <span data-ttu-id="84aa9-147">Office 365 네트워크 트래픽 보안 SSL 암호 해독 하 고 다시 암호화 프로토콜 오류가 발생할 수 있고 보안 위험</span><span class="sxs-lookup"><span data-stu-id="84aa9-147">Decrypting SSL secured Office 365 network traffic and re-encrypting it can cause protocol errors and has security risk</span></span>

<span data-ttu-id="84aa9-p112">클라이언트의 지리적 위치에 최대한 가깝게 탈출 트래픽을 허용 하 여 Office 365 진입점의 네트워크 경로 단축 연결 향상 시킬 수 Office 365의 성능 및 최종 사용자 경험 합니다. 또한 Office 365 성능 및 안정성에 네트워크 아키텍처를 향후 변경의 영향을 줄일 수는 것이 도움이 됩니다. 최적의 연결 모델 항상 네트워크 탈출 회사 네트워크 또는 공항 집, 호텔, 커피숍 등 원격 위치에 인지 여부에 관계 없이 사용자의 위치를 제공 하는 것입니다. 일반 인터넷 트래픽 및 WAN 기반 회사 네트워크 트래픽 개별적으로 라우팅되는 및 로컬 직접 탈출 모델을 사용 하지 합니다. 이 로컬 직접 탈출 모델은 아래 다이어그램에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="84aa9-p112">Shortening the network path to Office 365 entry points by allowing client traffic to egress as close as possible to their geographic location can improve connectivity performance and the end user experience in Office 365. It can also help to reduce the impact of future changes to the network architecture on Office 365 performance and reliability. The optimum connectivity model is to always provide network egress at the user's location, regardless of whether this is on the corporate network or remote locations such as home, hotels, coffee shops and airports. Generic Internet traffic and WAN based corporate network traffic would be separately routed and not use the local direct egress model. This local direct egress model is represented in the diagram below.</span></span>

![로컬 탈출 네트워크 아키텍처](media/6bc636b0-1234-4ceb-a45a-aadd1044b39c.png)

<span data-ttu-id="84aa9-154">로컬 탈출 아키텍처는 다음과 같은 이점이 있습니다 Office 365 네트워크 트래픽에 대 한 기존 모델을 통해:</span><span class="sxs-lookup"><span data-stu-id="84aa9-154">The local egress architecture has the following benefits for Office 365 network traffic over the traditional model:</span></span>
  
- <span data-ttu-id="84aa9-p113">경로 길이 최적화 하 여 Office 365 성능을 최적화를 제공 합니다. 최종 사용자 연결 Microsoft 글로벌 네트워크 _서비스 앞면 도어 분산_ 인프라에서 가장 가까운 Office 365 진입점에 라우팅되는 동적으로 및 다음 내부적으로 데이터 및 서비스 끝점을 통해 트래픽이 라우팅될 Microsoft의 매우 낮은 대기 시간 고가용성 진한 파이버입니다.</span><span class="sxs-lookup"><span data-stu-id="84aa9-p113">Provides optimal Office 365 performance by optimizing route length. End user connections are dynamically routed to the nearest Office 365 entry point by the Microsoft Global Network's _Distributed Service Front Door_ infrastructure, and traffic is then routed internally to data and service endpoints over Microsoft's ultra-low latency high availability dark fiber.</span></span>
- <span data-ttu-id="84aa9-157">Office 365 트래픽, 프록시 및 트래픽 검사 장치를 무시에 대 한 로컬 탈출 허용 하 여 회사 네트워크 인프라에서 부하를 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="84aa9-157">Reduces the load on corporate network infrastructure by allowing local egress for Office 365 traffic, bypassing proxies and traffic inspection devices.</span></span>
- <span data-ttu-id="84aa9-158">클라이언트 끝점 보안 및 클라우드 보안 기능, 중복 네트워크 보안 기술의 응용 프로그램은 사용 하지 않는 활용 하 여 양쪽 끝에서 연결을 보호 합니다.</span><span class="sxs-lookup"><span data-stu-id="84aa9-158">Secures connections on both ends by leveraging client endpoint security and cloud security features, avoiding application of redundant network security technologies.</span></span>

> [!NOTE]
> <span data-ttu-id="84aa9-p114">_분산 서비스 앞면 도어_ 인프라는 지리적으로 분산 된 위치에는 Microsoft 글로벌 네트워크의 사용 가능한과 확장성이 높은 네트워크 지 합니다. 최종 사용자 연결을 종료 하 고 Microsoft 글로벌 네트워크 내에서를 효율적으로 라우팅합니다. Microsoft 글로벌 네트워크 [어떻게 Microsoft 구축 하는 신속 하 고 신뢰할 수 있는 전역 네트워크에](https://azure.microsoft.com/en-us/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)대 한 자세한 내용을 알아보십시오.</span><span class="sxs-lookup"><span data-stu-id="84aa9-p114">The _Distributed Service Front Door_ infrastructure is the Microsoft Global Network's highly available and scalable network edge with geographically distributed locations. It terminates end user connections and efficiently routes them within the Microsoft Global Network. You can learn more about the Microsoft Global Network at [How Microsoft builds its fast and reliable global network](https://azure.microsoft.com/en-us/blog/how-microsoft-builds-its-fast-and-reliable-global-network/).</span></span>

<span data-ttu-id="84aa9-162">Office 365 네트워크 연결 원칙을 적용 하 고 이해 (영문)에 대 한 자세한 내용은 [Office 365 네트워크 연결 원칙](office-365-network-connectivity-principles.md)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="84aa9-162">For more information on understanding and applying Office 365 network connectivity principles, see [Office 365 Network Connectivity Principles](office-365-network-connectivity-principles.md).</span></span>

## <a name="conclusion"></a><span data-ttu-id="84aa9-163">결론</span><span class="sxs-lookup"><span data-stu-id="84aa9-163">Conclusion</span></span>

<span data-ttu-id="84aa9-p115">Office 365 네트워크 성능 최적화 결국 불필요 한 장애 요소를 제거 합니다. 신뢰할 수 있는 트래픽을으로 Office 365 연결 처리, 패킷 검사 및 프록시 대역폭에 대 한 경쟁으로 도입 되에서 대기 시간을 방지할 수 있습니다. 클라이언트 컴퓨터와 Office 365 끝점 사이의 연결을 로컬 허용 트래픽을 동적으로 Microsoft 글로벌 네트워크를 통해 라우팅될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84aa9-p115">Optimizing Office 365 network performance really comes down to removing unnecessary impediments. By treating Office 365 connections as trusted traffic, you can prevent latency from being introduced by packet inspection and competition for proxy bandwidth. Allowing local connections between client machines and Office 365 endpoints enables traffic to be dynamically routed through the Microsoft Global Network.</span></span>

## <a name="related-topics"></a><span data-ttu-id="84aa9-167">관련 항목</span><span class="sxs-lookup"><span data-stu-id="84aa9-167">Related Topics</span></span>

[<span data-ttu-id="84aa9-168">Office 365 네트워크 연결 원칙</span><span class="sxs-lookup"><span data-stu-id="84aa9-168">Office 365 Network Connectivity Principles</span></span>](office-365-network-connectivity-principles.md)

[<span data-ttu-id="84aa9-169">Office 365 IP 주소 및 URL 웹 서비스</span><span class="sxs-lookup"><span data-stu-id="84aa9-169">Office 365 IP Address and URL Web service</span></span>](office-365-ip-web-service.md)

[<span data-ttu-id="84aa9-170">Office 365 끝점 관리</span><span class="sxs-lookup"><span data-stu-id="84aa9-170">Managing Office 365 endpoints</span></span>](managing-office-365-endpoints.md)

[<span data-ttu-id="84aa9-171">Office 365 IP 주소 및 URL 웹 서비스</span><span class="sxs-lookup"><span data-stu-id="84aa9-171">Office 365 IP Address and URL Web service</span></span>](office-365-ip-web-service.md)

[<span data-ttu-id="84aa9-172">Office 365에 대한 네트워크 연결</span><span class="sxs-lookup"><span data-stu-id="84aa9-172">Network connectivity to Office 365</span></span>](network-connectivity.md)

[<span data-ttu-id="84aa9-173">Office 365 네트워크 및 성능 조정</span><span class="sxs-lookup"><span data-stu-id="84aa9-173">Office 365 network and performance tuning</span></span>](network-planning-and-performance.md)

[<span data-ttu-id="84aa9-174">초기 계획 및 성능 기록을 사용하여 Office 365 성능 조정</span><span class="sxs-lookup"><span data-stu-id="84aa9-174">Office 365 performance tuning using baselines and performance history</span></span>](performance-tuning-using-baselines-and-history.md)

[<span data-ttu-id="84aa9-175">Office 365 성능 문제 해결 계획</span><span class="sxs-lookup"><span data-stu-id="84aa9-175">Performance troubleshooting plan for Office 365</span></span>](performance-troubleshooting-plan.md)

[<span data-ttu-id="84aa9-176">Microsoft는 신속 하 고 신뢰할 수 있는 전역 네트워크를 구축 하는 방법</span><span class="sxs-lookup"><span data-stu-id="84aa9-176">How Microsoft builds its fast and reliable global network</span></span>](https://azure.microsoft.com/en-us/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)
