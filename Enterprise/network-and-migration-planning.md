---
title: Office 365의 네트워크 및 마이그레이션 계획
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/29/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
- BCS160
ms.assetid: f5ee6c33-bcd7-4b0b-b0f8-dc1d9fb8d132
description: 네트워크 계획 및 테스트 하는 방법에 대 한 정보에 대 한 링크와 Office 365로의 마이그레이션 포함 합니다.
ms.openlocfilehash: e2434a65b48c12f38d7371a569ba8e0bc282ae06
ms.sourcegitcommit: ad5bdc53ca67ee6a663c27648511c1ad768a76d4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/28/2018
ms.locfileid: "23223060"
---
# <a name="network-and-migration-planning-for-office-365"></a><span data-ttu-id="b8490-103">Office 365의 네트워크 및 마이그레이션 계획</span><span class="sxs-lookup"><span data-stu-id="b8490-103">Network and migration planning for Office 365</span></span>

<span data-ttu-id="b8490-104">이 문서에는 계획 및 테스트, 네트워크에 대 한 정보에 대 한 링크와 Office 365로의 마이그레이션 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8490-104">This article contains links to information about network planning and testing, and migration to Office 365.</span></span>
  
<span data-ttu-id="b8490-105">Office 365로 처음 배포하거나 마이그레이션하기 전에 다음 항목의 정보를 사용하여 필요한 대역폭을 예상하고 테스트한 후, Office 365로 배포하거나 마이그레이션할 대역폭이 충분한지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8490-105">Before you deploy for the first time or migrate to Office 365, you can use the information in these topics to estimate the bandwidth you need and then to test and verify that you have enough bandwidth to deploy or migrate to Office 365.</span></span>

||
|:-----|
| <span data-ttu-id="b8490-106">이 문서는 [네트워크 계획 및 Office 365에 대 한 성능 조정](https://aka.ms/tune)의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="b8490-106">This article is part of [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>|

|||
|:-----|:-----|
|![Microsoft 클라우드 네트워킹 엔터프라이즈 설계자 포스터 (영문)에 대 한 참조](media/3094be9f-2407-4fa5-896d-aa66ef7b9bb9.png)|<span data-ttu-id="b8490-108">Office 365 및 기타 Microsoft 클라우드 플랫폼 및 서비스에 대 한 네트워크를 최적화 하는 단계를 [엔터프라이즈 설계자에 대 한 Microsoft 클라우드 네트워킹](https://aka.ms/cloudarchnetworking) 포스터를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="b8490-108">For the steps to optimize your network for Office 365 and other Microsoft cloud platforms and services, see the [Microsoft Cloud Networking for Enterprise Architects](https://aka.ms/cloudarchnetworking) poster.</span></span> |
   
## <a name="estimate-network-bandwidth-requirements"></a><span data-ttu-id="b8490-109">네트워크 대역폭 요구 사항 예상</span><span class="sxs-lookup"><span data-stu-id="b8490-109">Estimate network bandwidth requirements</span></span>
<span data-ttu-id="b8490-110"><a name="EstimateBandwidthRequirements"> </a></span><span class="sxs-lookup"><span data-stu-id="b8490-110"></span></span>

<span data-ttu-id="b8490-p101">Office 365를 사용 하 여 조직의 인터넷 회로의 사용량이 증가할 수 있습니다. 현재 사용할 수 있는 대역폭의 양을 20% 이상에서 나가는 하는 동안 Office 365 배포 완벽 하 게 되 면 예상된 증가 처리 하기에 충분 한지 확인 하는 것이 중요 것은 사용자가 가장 많은 일을 처리 하는 용량.</span><span class="sxs-lookup"><span data-stu-id="b8490-p101">Using Office 365 may increase the utilization of your organization's internet circuit. It's important to determine if the amount of bandwidth currently available is enough to handle the estimated increase once Office 365 is fully deployed while leaving at least 20% capacity to handle the busiest of days.</span></span>
  
<span data-ttu-id="b8490-113">대역폭을 예측 하려면 다음 단계를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8490-113">To estimate the bandwidth, use the following steps:</span></span>
  
1. <span data-ttu-id="b8490-p102">클라이언트에서 사용할 각 인터넷 탈출 수를 평가 합니다. 가능한 연결의 많은 처리에서는 다중 terabit 네트워크를 사용 하는 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8490-p102">Assess the number of clients that will use each Internet egress. Let our multi-terabit network handle as much of the connection as possible.</span></span> 
    
2. <span data-ttu-id="b8490-p103">Office 365 서비스 및 기능을 사용 하 여 클라이언트에 대해 사용할 수를 결정 합니다. 다양 한 서비스 또는 사용 프로필을 가진 사용자의 그룹 가능성이 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8490-p103">Determine which Office 365 services and features will be available for clients to use. You will likely have groups of people with different services or usage profiles.</span></span>
    
3. <span data-ttu-id="b8490-p104">클라이언트의 파일럿 그룹에 대 한 네트워크 사용을 측정 합니다. 파일럿 클라이언트는 서로 다른 지리적 위치를 비롯 하 여 조직에는 사용자의 다른 프로필의 담당자에 게 확인 합니다. 있습니다 수 상호 확인 이전 계산기에 대 한 결과 [Exchange ](https://go.microsoft.com/fwlink/p/?LinkId=321550)및 [비즈니스를 위한 Skype](https://go.microsoft.com/fwlink/p/?LinkId=321551) 또는 여기에서는 자체 네트워크에서 수행 되는 [사례 연구](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365) 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8490-p104">Measure the network use for a pilot group of clients. Ensure the pilot clients are representative of the different profiles of people in the organization as well as the different geographic locations. You can cross-check your results against our old calculators for [Exchange ](https://go.microsoft.com/fwlink/p/?LinkId=321550)and [Skype for Business](https://go.microsoft.com/fwlink/p/?LinkId=321551) or the [case study](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365) we performed on our own network.</span></span> 
    
4. <span data-ttu-id="b8490-121">파일럿 그룹에서 측정 단위를 사용 하 여 전체 조직의 요구를 추정할 수 및 다시 네트워크를 변경 하기 전에 추정치의 유효성을 검사 하는 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8490-121">Use the measurements from the pilot group to extrapolate the entire organization's needs and re-test to validate the estimations before making any changes to your network.</span></span>
    
## <a name="test-your-existing-network"></a><span data-ttu-id="b8490-122">기존 네트워크 테스트</span><span class="sxs-lookup"><span data-stu-id="b8490-122">Test your existing network</span></span>
<span data-ttu-id="b8490-123"><a name="calculators"> </a></span><span class="sxs-lookup"><span data-stu-id="b8490-123"></span></span>

 <span data-ttu-id="b8490-p105">**도구 네트워크.** 테스트 하 고 다운로드, 업로드 및 대기 시간 제약 조건을 결정에 대 한 인터넷 대역폭의 유효성을 검사 합니다. 이러한 도구를 사용 하는 완벽 하 게 배포한 후 작업과 마이그레이션에 대 한 네트워크의 기능을 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8490-p105">**Network tools.** Test and validate your Internet bandwidth to determine download, upload, and latency constraints. These tools will help you determine the capabilities of your network for migration as well as after you're fully deployed.</span></span> 
  
- <span data-ttu-id="b8490-p106">[Microsoft 메시지 분석기](https://technet.microsoft.com/library/jj649776.aspx): 메시지 분석기 네트워크 문제를 해결 하는 것에 대 한 효과적인 도구입니다. 메시지 분석기, 표시 하 고, 캡처하고 프로토콜 기반 메시징 트래픽 및 시스템 메시지를 분석 합니다. 메시지 분석기 가져오기, 집계 및 로그 및 추적 파일에서 데이터를 분석할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8490-p106">[Microsoft Message Analyzer](https://technet.microsoft.com/library/jj649776.aspx): Message Analyzer is an effective tool for troubleshooting network issues. Message Analyzer captures, displays, and analyzes protocol-based messaging traffic and system messages. Message Analyzer also lets you import, aggregate, and analyze data from log and trace files.</span></span>
    
- <span data-ttu-id="b8490-130">[Microsoft 원격 연결 분석기](https://go.microsoft.com/fwlink/p/?LinkId=517243): Exchange Online 환경에 대 한 연결을 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8490-130">[Microsoft Remote Connectivity Analyzer](https://go.microsoft.com/fwlink/p/?LinkId=517243): Tests connectivity in your Exchange Online environment.</span></span>
    
- <span data-ttu-id="b8490-131">Outlook 및 Office 365 문제를 해결 하는 [Microsoft 기술 지원 서비스 및 Office 365에 대 한 복구 도우미](https://diagnostics.office.com/#/Download?env=SOC) 를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8490-131">Use the [Microsoft Support and Recovery Assistant for Office 365](https://diagnostics.office.com/#/Download?env=SOC) to fix Outlook and Office 365 problems.</span></span> 
    
## <a name="best-practices-for-network-planning-and-improving-migration-performance-for-office-365"></a><span data-ttu-id="b8490-132">Best practices for network planning and improving migration performance for Office 365</span><span class="sxs-lookup"><span data-stu-id="b8490-132">Best practices for network planning and improving migration performance for Office 365</span></span>
<span data-ttu-id="b8490-133"><a name="BestPractices"> </a></span><span class="sxs-lookup"><span data-stu-id="b8490-133"></span></span>

<span data-ttu-id="b8490-134">하셔서에 Office 365 환경을 개선 하는 방법에 대 한 자세한 내용은 이러한 유용한 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8490-134">Dig a little deeper into these best practices for more information about improving your Office 365 experience.</span></span>
  
1. <span data-ttu-id="b8490-p107">사용자에 게 즉시 도와 시작 싶으십니까? 방금 네트워크 되지 협력 하는 경우 SharePoint Online, Exchange Online 및 Lync Online을 포함 하 여 Office 365를 사용 하 여에 대 한 팁 [저속 네트워크에서 Office 365를 사용 하는 것에 대 한 모범 사례](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166) 를 참조 하십시오. 이 문서는 Office 365 환경을 최적화 하기 위한 콘텐츠 TechNet 및 Support.office.com의 부하를 연결 하 고 웹 페이지 및 최상의 Office 365 환경에 대 한 Internet Explorer 설정을 설정 하는 방법을 사용자 지정 하는 간편한 방법에 대 한 정보를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8490-p107">Want to get started helping your users right away? See [Best practices for using Office 365 on a slow network](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166) for tips on using Office 365, including SharePoint Online, Exchange Online, and Lync Online, when your network just isn't cooperating. This article links out to loads of content on TechNet and Support.office.com for optimizing your Office 365 experience and includes information on easy ways to customize your web pages and how to set your Internet Explorer settings for the best Office 365 experience.</span></span> 
    
2. <span data-ttu-id="b8490-p108">최상의 성능을 시작 및 안전 하 게 Office 365 트래픽을 관리 하기 위한 연결 원칙을 이해 하려면 [Office 365 네트워크 연결 원칙](https://aka.ms/o365networkingprinciples) 읽습니다. 이 문서는 안전 하 게 Office 365 네트워크 연결을 최적화 하는 것에 대 한 최신 지침을 이해 하는데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8490-p108">Read [Office 365 Network Connectivity Principles](https://aka.ms/o365networkingprinciples) to understand the connectivity principles for securely managing Office 365 traffic and getting the best possible performance. This article will help you understand the most recent guidance for securely optimizing Office 365 network connectivity.</span></span> 
    
3. <span data-ttu-id="b8490-p109">신중 하 게 Windows 업데이트에 대 한 일정을 관리 하 여 메일 마이그레이션 성능을 개선 합니다. 일괄 처리에서 클라이언트 컴퓨터를 업데이트할 수 있으며 모든 클라이언트 컴퓨터의 네트워크 대역폭 사용을 제어 하는 Office 365로 마이그레이션하기 전에 업데이트 수 있습니다. 자세한 내용은 [수동으로 업데이트 하 고 최신 업데이트에 대 한 Office 365 용 데스크톱 구성](https://support.microsoft.com/gp/office-2013-365-update)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="b8490-p109">Improve mail migration performance by carefully managing the schedule for Windows Updates. You can update your client computers in batches and ensure that all client computers are updated before migrating to Office 365 to regulate the use of network bandwidth. For more information, see [Manually update and configure desktops for Office 365 for the latest updates](https://support.microsoft.com/gp/office-2013-365-update).</span></span>
    
4. <span data-ttu-id="b8490-p110">Office 365 네트워크 트래픽을 신뢰할 수 있는 인터넷 서비스도 처리 있으며는 기존의 필터링 및 일부 조직에서는 신뢰할 수 없는 인터넷 서비스 네트워크 트래픽을에 배치 하는 검사를 무시 하도록 허용 하는 경우 가장을 수행 합니다. 아웃 바운드 프록시 사용자 인증 및 패킷 검사와 같은 처리으로 적절 한 네트워크 주소 변환 (NAT) 및 충분 한 대역폭 용량 증가 처리를 사용 하 여 인터넷을 로컬 탈출 보장 제거이 일반적으로 포함 네트워크 요청 수입니다. 네트워크에 있는 신뢰할 수 있는 인터넷 서비스의으로 Office 365를 처리 하 여 네트워크를 구성 하는 방법에 대 한 추가 지침에 대 한 [끝점을 Office 365 관리](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="b8490-p110">Office 365 network traffic performs best when it's treated as a trusted Internet service and allowed to bypass much of the traditional filtering and scanning that some organizations place on network traffic to untrusted Internet services. This typically includes removing outbound processing such as proxy user authentication and packet inspection, as well as ensuring local egress to the Internet with the proper Network Address Translation (NAT) and enough bandwidth capacity to handle the increased network requests. Refer to [Managing Office 365 endpoints](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)for additional guidance on configuring your network to handle Office 365 as a trusted Internet service on your network.</span></span>
    
1. <span data-ttu-id="b8490-p111">[Office 365 관리 끝점](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)을 확인 합니다. Office 365 하려고 추가 트래픽 보안 트래픽이 증가 하는 비롯 하 여 증가 하 게 설정 하는 아웃 바운드 프록시 연결에 TLS/SSL을 통해 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="b8490-p111">Ensure [Managing Office 365 endpoints](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a). The additional traffic going to Office 365 results in an increase of outbound proxy connections as well as an increase in secure traffic over TLS/SSL.</span></span>
    
2. <span data-ttu-id="b8490-p112">아웃 바운드 프록시에 사용자 인증을 요구 하는 경우에 저속 연결 또는 기능의 손실 발생할 수 있습니다. Office 365 도메인에 대 한 인증 요구 사항을 우회이 오버 헤드를 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8490-p112">If your outbound proxies require user authentication you may experience slow connectivity or a loss of functionality. Bypassing the authentication requirement for the Office 365 domains can reduce this overhead.</span></span>
    
3. <span data-ttu-id="b8490-p113">공유 일정 및 사서함 수가 많은 경우 Outlook에서 Exchange로의 연결 수가 늘어나는 것을 볼 수 있습니다. 예를 들어 사용 중인 각 공유 일정에 대해 Outlook 클라이언트에서 연결을 최대 두 개까지 추가로 열 수도 있습니다. 이 경우 탈출 방화벽이 연결을 처리할 수 있는지 확인하거나, Office 365에 대한 연결용 프록시를 Outlook으로 바이패스합니다.</span><span class="sxs-lookup"><span data-stu-id="b8490-p113">If you have a large number of shared calendars and mailboxes, you may see an increase in the number of connections from Outlook to Exchange. For instance, the Outlook client may open up to two additional connections for each shared calendar in use. In this situation, ensure that the egress proxy can handle the connections, or bypass the proxy for connections to Office 365 for Outlook.</span></span>
    
4. <span data-ttu-id="b8490-p114">공용 IP 주소에 대 한 지원 되는 장치의 최대 수와 여러 IP 주소 부하를 분산 하는 방법을 결정 합니다. 자세한 내용은 [Office 365와의 NAT 지원](nat-support-with-office-365.md)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="b8490-p114">Determine the maximum number of supported devices for a public IP address and how to load balance across multiple IP addresses. For more information, see [NAT support with Office 365](nat-support-with-office-365.md).</span></span>
    
5. <span data-ttu-id="b8490-p115">컴퓨터에서 아웃 바운드 연결 네트워크에을 검사 하는 경우 연결 및 성능을 향상 시킬 Office 365 도메인에는 필터링이 입력 되지 않도록 합니다. 또한 아웃 바운드 검사 자주 사용 하지 않고 단일 인터넷 탈출에 대 한 필요성을 제거 고 전송 되는 Office 365 네트워크 요청에 대 한 로컬 인터넷 탈출 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8490-p115">If you're inspecting outbound connections from computers on your network, bypassing this filtering to the Office 365 domains will improve connectivity and performance. Additionally, bypassing outbound inspection often removes the need for a single Internet egress and enables local Internet egress for Office 365 destined network requests.</span></span>
    
6. <span data-ttu-id="b8490-p116">일부 고객 찾을 내부 네트워크 설정 성능에 영향을 줄 수 있습니다. 자동 협상 또는 자동 검색 하 고, 네트워크 최대 전송 단위 (MTU) 크기와 같은 설정에 부여 되며 최적 경로 인터넷에 일반적인 위치를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="b8490-p116">Some customers find internal network settings may affect performance. Settings such as maximum transmission unit (MTU) size, network auto-negotiation or auto-detection, and sub-optimal routes to the Internet are common places to look.</span></span>
    
## <a name="network-planning-reference-for-office-365"></a><span data-ttu-id="b8490-159">Office 365에 대한 네트워크 계획 참조</span><span class="sxs-lookup"><span data-stu-id="b8490-159">Network planning reference for Office 365</span></span>
<span data-ttu-id="b8490-160"><a name="NetReference"> </a></span><span class="sxs-lookup"><span data-stu-id="b8490-160"></span></span>

<span data-ttu-id="b8490-161">이 항목에서는 자세한 Office 365 네트워크 참조 정보를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8490-161">These topics contain detailed Office 365 network reference information.</span></span>
  
- [<span data-ttu-id="b8490-162">Office 365 끝점 관리</span><span class="sxs-lookup"><span data-stu-id="b8490-162">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
    
- [<span data-ttu-id="b8490-163">클라이언트 연결</span><span class="sxs-lookup"><span data-stu-id="b8490-163">Client connectivity</span></span>](client-connectivity.md)
    
- [<span data-ttu-id="b8490-164">콘텐츠 배달 네트워크</span><span class="sxs-lookup"><span data-stu-id="b8490-164">Content delivery networks</span></span>](content-delivery-networks.md)
    
- [<span data-ttu-id="b8490-165">Office 365에 대 한 외부 도메인 이름 시스템 레코드</span><span class="sxs-lookup"><span data-stu-id="b8490-165">External Domain Name System records for Office 365</span></span>](external-domain-name-system-records.md)
    
- [<span data-ttu-id="b8490-166">Office 365 서비스의 IPv6 지원</span><span class="sxs-lookup"><span data-stu-id="b8490-166">IPv6 support in Office 365 services</span></span>](ipv6-support.md)
    
- [<span data-ttu-id="b8490-167">Office 365 네트워크 연결 원칙</span><span class="sxs-lookup"><span data-stu-id="b8490-167">Office 365 Network Connectivity Principles</span></span>](https://aka.ms/o365networkingprinciples)
    
- [<span data-ttu-id="b8490-168">Microsoft 가상 Academy: Office 365 성능 관리</span><span class="sxs-lookup"><span data-stu-id="b8490-168">Microsoft Virtual Academy: Office 365 Performance Management</span></span>](https://mva.microsoft.com/en-us/training-courses/office-365-performance-management-8416)
    
- [<span data-ttu-id="b8490-169">Office 365 비디오 네트워킹 질문 (FAQ)</span><span class="sxs-lookup"><span data-stu-id="b8490-169">Office 365 video networking Frequently Asked Questions (FAQ)</span></span>](office-365-video-networking-faq.md)
    
- [<span data-ttu-id="b8490-170">Office 365 서비스에 연결되는 네트워크 장치 계획</span><span class="sxs-lookup"><span data-stu-id="b8490-170">Plan for network devices that connect to Office 365 services</span></span>](plan-for-network-devices.md)
    
- [<span data-ttu-id="b8490-171">Office 365 서비스 배포 관리자</span><span class="sxs-lookup"><span data-stu-id="b8490-171">Deployment advisors for Office 365 services</span></span>](deployment-advisors-for-office-365.md)
    

