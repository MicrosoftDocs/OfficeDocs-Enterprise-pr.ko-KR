---
title: Office 365의 네트워크 및 마이그레이션 계획
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/29/2018
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- BCS160
ms.assetid: f5ee6c33-bcd7-4b0b-b0f8-dc1d9fb8d132
description: 네트워크 계획 및 테스트에 대 한 정보 링크와 Office 365로의 마이그레이션에 대 한 링크가 포함 되어 있습니다.
ms.openlocfilehash: 530e07aeb2f3420f0c752f2b254913a42c73f8ee
ms.sourcegitcommit: 6b12e3ab76809d5632923def7ee367cd48ef3ccc
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/13/2020
ms.locfileid: "45117270"
---
# <a name="network-and-migration-planning-for-office-365"></a><span data-ttu-id="99457-103">Office 365의 네트워크 및 마이그레이션 계획</span><span class="sxs-lookup"><span data-stu-id="99457-103">Network and migration planning for Office 365</span></span>

<span data-ttu-id="99457-104">*이 문서는 Microsoft 365 Enterprise 및 Office 365 Enterprise에 모두 적용 됩니다.*</span><span class="sxs-lookup"><span data-stu-id="99457-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="99457-105">이 문서에는 네트워크 계획 및 테스트에 대 한 정보와 Office 365로의 마이그레이션에 대 한 링크가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99457-105">This article contains links to information about network planning and testing, and migration to Office 365.</span></span>
  
<span data-ttu-id="99457-106">처음으로 배포 하거나 Office 365로 마이그레이션하기 전에 다음 항목의 정보를 사용 하 여 필요한 대역폭을 예상 하 고 테스트 하 여 Office 365로 배포 하거나 마이그레이션할 대역폭이 충분 한지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99457-106">Before you deploy for the first time or migrate to Office 365, you can use the information in these topics to estimate the bandwidth you need and then to test and verify that you have enough bandwidth to deploy or migrate to Office 365.</span></span>

||
|:-----|
| <span data-ttu-id="99457-107">이 문서는 [Office 365의 네트워크 계획 및 성능 조정](https://aka.ms/tune)의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="99457-107">This article is part of [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>|

|||
|:-----|:-----|
|![엔터프라이즈 설계자 포스터 용 Microsoft 클라우드 네트워킹 참조](media/3094be9f-2407-4fa5-896d-aa66ef7b9bb9.png)|<span data-ttu-id="99457-109">Office 365 및 기타 Microsoft 클라우드 플랫폼 및 서비스에 대 한 네트워크를 최적화 하는 단계는 [Microsoft 클라우드 네트워킹 For 엔터프라이즈 설계자](https://aka.ms/cloudarchnetworking) 포스터를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="99457-109">For the steps to optimize your network for Office 365 and other Microsoft cloud platforms and services, see the [Microsoft Cloud Networking for Enterprise Architects](https://aka.ms/cloudarchnetworking) poster.</span></span> |
   
## <a name="estimate-network-bandwidth-requirements"></a><span data-ttu-id="99457-110">네트워크 대역폭 요구 사항 예상</span><span class="sxs-lookup"><span data-stu-id="99457-110">Estimate network bandwidth requirements</span></span>
<span data-ttu-id="99457-111"><a name="EstimateBandwidthRequirements"> </a></span><span class="sxs-lookup"><span data-stu-id="99457-111"><a name="EstimateBandwidthRequirements"> </a></span></span>

<span data-ttu-id="99457-112">Office 365을 사용 하면 조직의 인터넷 회로 사용률이 향상 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99457-112">Using Office 365 may increase the utilization of your organization's internet circuit.</span></span> <span data-ttu-id="99457-113">최대 일 수를 처리 하기 위해 20%의 용량을 남겨 두고 Office 365이 완전히 배포 되 면 현재 사용 가능한 대역폭의 양이 충분 한지를 확인 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="99457-113">It's important to determine if the amount of bandwidth currently available is enough to handle the estimated increase once Office 365 is fully deployed while leaving at least 20% capacity to handle the busiest of days.</span></span>
  
<span data-ttu-id="99457-114">대역폭을 예상 하려면 다음 단계를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="99457-114">To estimate the bandwidth, use the following steps:</span></span>
  
1. <span data-ttu-id="99457-115">각 인터넷 송신을 사용할 클라이언트 수를 평가 합니다.</span><span class="sxs-lookup"><span data-stu-id="99457-115">Assess the number of clients that will use each Internet egress.</span></span> <span data-ttu-id="99457-116">다중 terabit 네트워크가 가능한 한 많은 연결을 처리 하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="99457-116">Let our multi-terabit network handle as much of the connection as possible.</span></span> 
    
2. <span data-ttu-id="99457-117">클라이언트에서 사용할 수 있는 Office 365 서비스 및 기능을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="99457-117">Determine which Office 365 services and features will be available for clients to use.</span></span> <span data-ttu-id="99457-118">다른 서비스 또는 사용 프로필을 가진 사용자 그룹을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99457-118">You will likely have groups of people with different services or usage profiles.</span></span>
    
3. <span data-ttu-id="99457-119">파일럿 클라이언트 그룹의 네트워크 사용을 측정 합니다.</span><span class="sxs-lookup"><span data-stu-id="99457-119">Measure the network use for a pilot group of clients.</span></span> <span data-ttu-id="99457-120">파일럿 클라이언트가 각 지리적 위치 뿐 아니라 조직에 있는 각 사용자의 프로필을 대표 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="99457-120">Ensure the pilot clients are representative of the different profiles of people in the organization as well as the different geographic locations.</span></span> <span data-ttu-id="99457-121">[Exchange](https://techcommunity.microsoft.com/t5/exchange-team-blog/announcing-the-exchange-client-network-bandwidth-calculator-beta/ba-p/601744) 및 [비즈니스용 Skype](https://go.microsoft.com/fwlink/p/?LinkId=321551) 에 대 한 이전 계산기와 자신의 네트워크에서 수행한 [사례 연구](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365) 에 대해 결과를 상호 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99457-121">You can cross-check your results against our old calculators for [Exchange](https://techcommunity.microsoft.com/t5/exchange-team-blog/announcing-the-exchange-client-network-bandwidth-calculator-beta/ba-p/601744) and [Skype for Business](https://go.microsoft.com/fwlink/p/?LinkId=321551) or the [case study](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365) we performed on our own network.</span></span> 
    
4. <span data-ttu-id="99457-122">파일럿 그룹의 측정값을 사용 하 여 전체 조직의 요구 사항을 추정 하 고 다시 테스트 하 여 네트워크를 변경 하기 전 까지의 추정치를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="99457-122">Use the measurements from the pilot group to extrapolate the entire organization's needs and re-test to validate the estimations before making any changes to your network.</span></span>
    
## <a name="test-your-existing-network"></a><span data-ttu-id="99457-123">기존 네트워크 테스트</span><span class="sxs-lookup"><span data-stu-id="99457-123">Test your existing network</span></span>
<span data-ttu-id="99457-124"><a name="calculators"> </a></span><span class="sxs-lookup"><span data-stu-id="99457-124"><a name="calculators"> </a></span></span>

 <span data-ttu-id="99457-125">**네트워크 도구**</span><span class="sxs-lookup"><span data-stu-id="99457-125">**Network tools.**</span></span> <span data-ttu-id="99457-126">인터넷 대역폭을 테스트 하 고 유효성을 검사 하 여 다운로드, 업로드 및 대기 시간 제한을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="99457-126">Test and validate your Internet bandwidth to determine download, upload, and latency constraints.</span></span> <span data-ttu-id="99457-127">이러한 도구는 마이그레이션에 대 한 네트워크 기능 뿐 아니라 완벽 하 게 배포 된 후에도 결정 하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="99457-127">These tools will help you determine the capabilities of your network for migration as well as after you're fully deployed.</span></span> 
    
- <span data-ttu-id="99457-128">[Microsoft 원격 연결 분석기](https://go.microsoft.com/fwlink/p/?LinkId=517243): Exchange Online 환경에서 연결을 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="99457-128">[Microsoft Remote Connectivity Analyzer](https://go.microsoft.com/fwlink/p/?LinkId=517243): Tests connectivity in your Exchange Online environment.</span></span>
    
- <span data-ttu-id="99457-129">[Office 365 용 Microsoft 지원 및 복구 도우미](https://diagnostics.office.com/#/Download?env=SOC) 를 사용 하 여 Outlook 및 Office 365 문제를 해결 합니다.</span><span class="sxs-lookup"><span data-stu-id="99457-129">Use the [Microsoft Support and Recovery Assistant for Office 365](https://diagnostics.office.com/#/Download?env=SOC) to fix Outlook and Office 365 problems.</span></span> 
    
## <a name="best-practices-for-network-planning-and-improving-migration-performance-for-office-365"></a><span data-ttu-id="99457-130">네트워크 계획을 위한 모범 사례 및 Office 365의 마이그레이션 성능 개선</span><span class="sxs-lookup"><span data-stu-id="99457-130">Best practices for network planning and improving migration performance for Office 365</span></span>
<span data-ttu-id="99457-131"><a name="BestPractices"> </a></span><span class="sxs-lookup"><span data-stu-id="99457-131"><a name="BestPractices"> </a></span></span>

<span data-ttu-id="99457-132">Office 365 환경을 개선 하는 방법에 대 한 자세한 내용을 보려면 이러한 모범 사례를 자세히 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="99457-132">Dig a little deeper into these best practices for more information about improving your Office 365 experience.</span></span>
  
1. <span data-ttu-id="99457-133">사용자를 즉시 활용할 수 있도록 하기 원하십니까?</span><span class="sxs-lookup"><span data-stu-id="99457-133">Want to get started helping your users right away?</span></span> <span data-ttu-id="99457-134">네트워크가 너무 많이 사용 되지 않는 경우 SharePoint Online, Exchange Online, Lync Online 등 Office 365 사용에 대 한 팁을 보려면 [느린 네트워크에서 office 365을 사용할](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166) 때 유용한 정보를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="99457-134">See [Best practices for using Office 365 on a slow network](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166) for tips on using Office 365, including SharePoint Online, Exchange Online, and Lync Online, when your network just isn't cooperating.</span></span> <span data-ttu-id="99457-135">이 문서에서는 Office 365 환경을 최적화 하기 위해 TechNet 및 Support.office.com의 콘텐츠 로드에 대해 설명 하 고, 웹 페이지를 사용자 지정 하는 간편한 방법 및 최상의 Office 365 환경을 위한 Internet Explorer 설정을 설정 하는 방법에 대 한 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="99457-135">This article links out to loads of content on TechNet and Support.office.com for optimizing your Office 365 experience and includes information on easy ways to customize your web pages and how to set your Internet Explorer settings for the best Office 365 experience.</span></span> 
    
2. <span data-ttu-id="99457-136">Office [365 네트워크 연결 원칙](https://aka.ms/o365networkingprinciples) 을 읽고 office 365 트래픽을 안전 하 게 관리 하 고 가능한 최적의 성능을 얻는 데 필요한 연결 원칙을 이해 합니다.</span><span class="sxs-lookup"><span data-stu-id="99457-136">Read [Office 365 Network Connectivity Principles](https://aka.ms/o365networkingprinciples) to understand the connectivity principles for securely managing Office 365 traffic and getting the best possible performance.</span></span> <span data-ttu-id="99457-137">이 문서는 Office 365 네트워크 연결을 안전 하 게 최적화 하기 위한 가장 최근 지침을 이해 하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="99457-137">This article will help you understand the most recent guidance for securely optimizing Office 365 network connectivity.</span></span> 
    
3. <span data-ttu-id="99457-138">Windows 업데이트 일정을 신중 하 게 관리 하 여 메일 마이그레이션 성능을 향상 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="99457-138">Improve mail migration performance by carefully managing the schedule for Windows Updates.</span></span> <span data-ttu-id="99457-139">클라이언트 컴퓨터를 일괄적으로 업데이트 하 고 네트워크 대역폭 사용을 조정 하기 위해 Office 365로 마이그레이션하기 전에 모든 클라이언트 컴퓨터가 업데이트 되는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99457-139">You can update your client computers in batches and ensure that all client computers are updated before migrating to Office 365 to regulate the use of network bandwidth.</span></span> <span data-ttu-id="99457-140">자세한 내용은 [최신 업데이트에 대 한 Office 365 데스크톱 수동 업데이트 및 구성을](https://support.microsoft.com/gp/office-2013-365-update)참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="99457-140">For more information, see [Manually update and configure desktops for Office 365 for the latest updates](https://support.microsoft.com/gp/office-2013-365-update).</span></span>
    
4. <span data-ttu-id="99457-141">Office 365 네트워크 트래픽은 신뢰할 수 있는 인터넷 서비스로 취급 되 고 일부 조직에서 신뢰할 수 없는 인터넷 서비스에 대 한 네트워크 트래픽을 수행 하는 일반적인 필터링 및 검색 기능을 많이 사용 하지 않을 때 가장 적합 합니다.</span><span class="sxs-lookup"><span data-stu-id="99457-141">Office 365 network traffic performs best when it's treated as a trusted Internet service and allowed to bypass much of the traditional filtering and scanning that some organizations place on network traffic to untrusted Internet services.</span></span> <span data-ttu-id="99457-142">여기에는 일반적으로 프록시 사용자 인증 및 패킷 검사와 같은 아웃 바운드 처리를 제거 하 고, 올바른 NAT (Network Address Translation)를 사용 하 여 인터넷에 대 한 로컬 송신을 보장 하 고 증가 된 네트워크 요청을 처리할 수 있는 충분 한 대역폭 용량을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="99457-142">This typically includes removing outbound processing such as proxy user authentication and packet inspection, as well as ensuring local egress to the Internet with the proper Network Address Translation (NAT) and enough bandwidth capacity to handle the increased network requests.</span></span> <span data-ttu-id="99457-143">네트워크에서 신뢰할 수 있는 인터넷 서비스로 Office 365를 처리 하도록 네트워크를 구성 하는 방법에 대 한 추가 지침은 [office 365 끝점 관리](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="99457-143">Refer to [Managing Office 365 endpoints](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)for additional guidance on configuring your network to handle Office 365 as a trusted Internet service on your network.</span></span>
    
1. <span data-ttu-id="99457-144">[Office 365 끝점 관리](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="99457-144">Ensure [Managing Office 365 endpoints](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a).</span></span> <span data-ttu-id="99457-145">Office 365로 들어오는 추가 트래픽으로 인해 아웃 바운드 프록시 연결이 증가 하 고 TLS/SSL을 통한 보안 트래픽이 증가 합니다.</span><span class="sxs-lookup"><span data-stu-id="99457-145">The additional traffic going to Office 365 results in an increase of outbound proxy connections as well as an increase in secure traffic over TLS/SSL.</span></span>
    
2. <span data-ttu-id="99457-146">아웃 바운드 프록시에 사용자 인증이 필요한 경우 연결 속도가 느리거나 기능 손실이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99457-146">If your outbound proxies require user authentication you may experience slow connectivity or a loss of functionality.</span></span> <span data-ttu-id="99457-147">Office 365 도메인에 대 한 인증 요구 사항을 건너뛰면 이러한 오버 헤드를 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99457-147">Bypassing the authentication requirement for the Office 365 domains can reduce this overhead.</span></span>
    
3. <span data-ttu-id="99457-148">공유 일정 및 사서함의 수가 많은 경우 Outlook에서 Exchange로의 연결 수가 증가 하는 것을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99457-148">If you have a large number of shared calendars and mailboxes, you may see an increase in the number of connections from Outlook to Exchange.</span></span> <span data-ttu-id="99457-149">예를 들어 Outlook 클라이언트는 사용 중인 각 공유 일정에 대해 최대 2 개의 추가 연결을 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99457-149">For instance, the Outlook client may open up to two additional connections for each shared calendar in use.</span></span> <span data-ttu-id="99457-150">이러한 상황에서는 egress 프록시가 연결을 처리할 수 있도록 하거나 Outlook에 대 한 Office 365 연결에 프록시를 사용 하지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="99457-150">In this situation, ensure that the egress proxy can handle the connections, or bypass the proxy for connections to Office 365 for Outlook.</span></span>
    
4. <span data-ttu-id="99457-151">공용 IP 주소에 대해 지원 되는 최대 장치 수와 여러 IP 주소 간의 로드 균형을 조정 하는 방법을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="99457-151">Determine the maximum number of supported devices for a public IP address and how to load balance across multiple IP addresses.</span></span> <span data-ttu-id="99457-152">자세한 내용은 [Office 365에서 NAT 지원](nat-support-with-office-365.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="99457-152">For more information, see [NAT support with Office 365](nat-support-with-office-365.md).</span></span>
    
5. <span data-ttu-id="99457-153">네트워크의 컴퓨터에서 나가는 아웃 바운드 연결을 조사 하는 경우, Office 365 도메인에 대 한이 필터링을 우회 하면 연결 및 성능이 향상 됩니다.</span><span class="sxs-lookup"><span data-stu-id="99457-153">If you're inspecting outbound connections from computers on your network, bypassing this filtering to the Office 365 domains will improve connectivity and performance.</span></span> <span data-ttu-id="99457-154">또한 아웃 바운드 검사를 우회 하면 단일 인터넷 송신이 필요 하지 않으며 Office 365에서 전송 된 네트워크 요청에 대해 로컬 인터넷 송신을 사용 하도록 설정 하기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="99457-154">Additionally, bypassing outbound inspection often removes the need for a single Internet egress and enables local Internet egress for Office 365 destined network requests.</span></span>
    
6. <span data-ttu-id="99457-155">일부 고객이 내부 네트워크 설정을 발견 하면 성능에 영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99457-155">Some customers find internal network settings may affect performance.</span></span> <span data-ttu-id="99457-156">MTU (최대 전송 단위) 크기, 네트워크 자동 협상, 자동 검색 및 인터넷에 대 한 하위 최적 경로와 같은 설정은 일반적인 모습입니다.</span><span class="sxs-lookup"><span data-stu-id="99457-156">Settings such as maximum transmission unit (MTU) size, network auto-negotiation or auto-detection, and sub-optimal routes to the Internet are common places to look.</span></span>
    
## <a name="network-planning-reference-for-office-365"></a><span data-ttu-id="99457-157">Office 365에 대 한 네트워크 계획 참조</span><span class="sxs-lookup"><span data-stu-id="99457-157">Network planning reference for Office 365</span></span>
<span data-ttu-id="99457-158"><a name="NetReference"> </a></span><span class="sxs-lookup"><span data-stu-id="99457-158"><a name="NetReference"> </a></span></span>

<span data-ttu-id="99457-159">이러한 항목에는 자세한 Office 365 네트워크 참조 정보가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99457-159">These topics contain detailed Office 365 network reference information.</span></span>
  
- [<span data-ttu-id="99457-160">Office 365 끝점 관리</span><span class="sxs-lookup"><span data-stu-id="99457-160">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
    
- [<span data-ttu-id="99457-161">콘텐츠 배달 네트워크</span><span class="sxs-lookup"><span data-stu-id="99457-161">Content delivery networks</span></span>](content-delivery-networks.md)
    
- [<span data-ttu-id="99457-162">Office 365에 대한 외부 Domain Name System 레코드</span><span class="sxs-lookup"><span data-stu-id="99457-162">External Domain Name System records for Office 365</span></span>](external-domain-name-system-records.md)
    
- [<span data-ttu-id="99457-163">Office 365 서비스의 IPv6 지원</span><span class="sxs-lookup"><span data-stu-id="99457-163">IPv6 support in Office 365 services</span></span>](ipv6-support.md)
    
- [<span data-ttu-id="99457-164">Office 365 네트워크 연결 원칙</span><span class="sxs-lookup"><span data-stu-id="99457-164">Office 365 Network Connectivity Principles</span></span>](https://aka.ms/o365networkingprinciples)
    
- [<span data-ttu-id="99457-165">Office 365 비디오 네트워킹에 대 한 질문과 대답 (FAQ)</span><span class="sxs-lookup"><span data-stu-id="99457-165">Office 365 video networking Frequently Asked Questions (FAQ)</span></span>](office-365-video-networking-faq.md)
    
- [<span data-ttu-id="99457-166">Office 365 서비스에 연결되는 네트워크 장치 계획</span><span class="sxs-lookup"><span data-stu-id="99457-166">Plan for network devices that connect to Office 365 services</span></span>](plan-for-network-devices.md)
    
- [<span data-ttu-id="99457-167">Office 365 서비스에 대 한 설정 가이드</span><span class="sxs-lookup"><span data-stu-id="99457-167">Setup guides for Office 365 services</span></span>](setup-guides-for-office-365.md)
 
## <a name="see-also"></a><span data-ttu-id="99457-168">참고 항목</span><span class="sxs-lookup"><span data-stu-id="99457-168">See also</span></span>

[<span data-ttu-id="99457-169">Microsoft 365 Enterprise 개요</span><span class="sxs-lookup"><span data-stu-id="99457-169">Microsoft 365 Enterprise overview</span></span>](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
