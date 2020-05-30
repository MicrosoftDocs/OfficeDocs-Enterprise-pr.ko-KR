---
title: Office 365 서비스에 연결되는 네트워크 장치 계획
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/29/2016
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 073433ca-3511-4db9-b173-7a2edca57691
description: '요약: Office 365에 연결 하는 데 사용 되는 네트워크 용량, WAN 가속기 및 부하 분산 장치에 대 한 고려 사항을 설명 합니다.'
ms.openlocfilehash: 9776611aa64f8783a22252a2c4182e63bda1093a
ms.sourcegitcommit: bb5b7bd241f58491198de2d74dbdce76f7bb8f62
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2020
ms.locfileid: "44419376"
---
# <a name="plan-for-network-devices-that-connect-to-office-365-services"></a><span data-ttu-id="feef6-103">Office 365 서비스에 연결되는 네트워크 장치 계획</span><span class="sxs-lookup"><span data-stu-id="feef6-103">Plan for network devices that connect to Office 365 services</span></span>

<span data-ttu-id="feef6-104">*이 문서는 Microsoft 365 Enterprise와 Office 365 Enterprise에 모두 적용됩니다.*</span><span class="sxs-lookup"><span data-stu-id="feef6-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>
  
<span data-ttu-id="feef6-105">**요약**: Office 365에 연결 하는 데 사용 되는 네트워크 용량, WAN 가속기 및 부하 분산 장치에 대 한 고려 사항을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="feef6-105">**Summary**: Describes considerations for network capacity, WAN accelerators, and load balancing devices that are used to connect to Office 365.</span></span>

<span data-ttu-id="feef6-106">일부 네트워크 하드웨어에서는 지원 되는 동시 세션 수에 제한이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="feef6-106">Some network hardware may have limitations on the number of concurrent sessions that are supported.</span></span> <span data-ttu-id="feef6-107">사용자가 2000 명 이상인 조직의 경우 네트워크 장치를 모니터링 하 여 추가 Office 365 서비스 트래픽을 처리할 수 있는지 확인 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="feef6-107">For organizations having more than 2,000 users, we recommend that they monitor their network devices to ensure they are capable of handling the additional Office 365 service traffic.</span></span> <span data-ttu-id="feef6-108">SNMP (Simple Network Management Protocol) 모니터링 소프트웨어를 통해이 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="feef6-108">Simple Network Management Protocol (SNMP) monitoring software can help you do this.</span></span>

||
|:-----|
| <span data-ttu-id="feef6-109">이 문서는 [Office 365의 네트워크 계획 및 성능 조정](https://aka.ms/tune)의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="feef6-109">This article is part of [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>|

<span data-ttu-id="feef6-110">온-프레미스 나가는 인터넷 프록시 설정도 클라이언트 응용 프로그램에 대 한 Office 365 서비스 연결에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="feef6-110">On-premises outgoing Internet proxy settings also affect connectivity to Office 365 services for your client applications.</span></span> <span data-ttu-id="feef6-111">또한 Microsoft 클라우드 서비스 Url 및 응용 프로그램에 대 한 연결을 허용 하도록 네트워크 프록시 장치를 구성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="feef6-111">You must also configure your network proxy devices to allow connections for Microsoft cloud services URLs and applications.</span></span> <span data-ttu-id="feef6-112">모든 조직은 서로 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="feef6-112">Every organization is different.</span></span> <span data-ttu-id="feef6-113">Microsoft가이 프로세스를 관리 하는 방법 및 구축 하는 대역폭의 양에 대 한 아이디어를 얻으려면 [사례 연구를 읽어보십시오](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365).</span><span class="sxs-lookup"><span data-stu-id="feef6-113">To get an idea for how Microsoft manages this process and the amount of bandwidth we provision, [read the case study](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365).</span></span>
  
<span data-ttu-id="feef6-114">다음 비즈니스용 Skype 도움말 문서에는 비즈니스용 Skype 설정에 대 한 자세한 정보가 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="feef6-114">The following Skype for Business Help articles have more information about Skype for Business settings:</span></span>
  
- [<span data-ttu-id="feef6-115">관리자에 대 한 비즈니스용 Skype Online 로그인 오류 해결</span><span class="sxs-lookup"><span data-stu-id="feef6-115">Troubleshooting Skype for Business Online sign-in errors for administrators</span></span>](https://docs.microsoft.com/skypeforbusiness/set-up-skype-for-business-online/troubleshooting-sign-in-errors-for-admins)

- [<span data-ttu-id="feef6-116">온-프레미스 방화벽이 연결을 차단 하므로 비즈니스용 Skype에 연결할 수 없거나 특정 기능이 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="feef6-116">You cannot connect to Skype for Business, or certain features do not work, because an on-premises firewall blocks the connection</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=243625)

> [!NOTE]
> <span data-ttu-id="feef6-117">이러한 설정 중 상당수는 비즈니스용 Skype에 따라 다르지만 네트워크 구성에 대 한 일반적인 지침은 모든 Office 365 서비스에 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="feef6-117">While many of these settings are Skype for Business-specific, the general guidance on network configuration is useful for all Office 365 services.</span></span>
  
## <a name="determining-network-capacity"></a><span data-ttu-id="feef6-118">네트워크 용량 확인</span><span class="sxs-lookup"><span data-stu-id="feef6-118">Determining Network Capacity</span></span>

<span data-ttu-id="feef6-119">연결에 있는 모든 네트워크 장치에는 용량 제한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="feef6-119">Every network device that exists on a connection has its capacity limit.</span></span> <span data-ttu-id="feef6-120">이러한 장치에는 클라이언트 및 서버 네트워크 어댑터, 라우터, 스위치 및 허브를 상호 연결 하는 허브가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="feef6-120">These devices include the client and server network adapters, routers, switches, and hubs that interconnect them.</span></span> <span data-ttu-id="feef6-121">적절 한 네트워크 용량을 통해 포화 상태인 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="feef6-121">Adequate network capacity means that none of them are saturated.</span></span> <span data-ttu-id="feef6-122">네트워크 활동 모니터링은 모든 네트워크 장치의 실제 부하를 최대 용량 보다 작게 유지 하는 데 반드시 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="feef6-122">Monitoring network activity is essential to help ensure that the actual loads on all network devices are less than their maximum capacity.</span></span> <span data-ttu-id="feef6-123">네트워크 용량은 프록시 장치 성능에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="feef6-123">Network capacity affects proxy device performance.</span></span>
  
<span data-ttu-id="feef6-124">대부분의 경우 인터넷 연결 대역폭은 트래픽 크기에 대 한 제한을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="feef6-124">In most situations, the Internet connection bandwidth sets the limit for the amount of traffic.</span></span> <span data-ttu-id="feef6-125">인터넷 링크를 과도 하 게 사용 하 여 트래픽이 가장 많이 발생 하는 경우에는 성능이 저하 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="feef6-125">Weak performance during peak traffic hours is probably caused by excessive use of the Internet link.</span></span> <span data-ttu-id="feef6-126">이 상황은 지점용 본사에서 느린 WAN (광역 네트워크) 링크를 통해 분기 사무실 프록시 서버 컴퓨터가 프록시 장치에 연결 되는 지점 시나리오에도 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="feef6-126">This situation also applies to a branch office scenario, where branch office proxy server computers are connected to the proxy device at the branch's headquarters over a slow Wide Area Network (WAN) link.</span></span>
  
<span data-ttu-id="feef6-127">네트워크 용량을 테스트 하려면 프록시 네트워크 인터페이스에서 네트워크 활동을 모니터링 합니다.</span><span class="sxs-lookup"><span data-stu-id="feef6-127">To test network capacity, monitor the network activity on the proxy network interface.</span></span> <span data-ttu-id="feef6-128">네트워크 인터페이스의 최대 대역폭 중 75% 이상이 면 적절 하지 않은 네트워크 인프라의 대역폭을 늘리는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="feef6-128">If it's more than 75 percent of the maximum bandwidth of any network interface, consider increasing the bandwidth of the network infrastructure that's inadequate.</span></span> <span data-ttu-id="feef6-129">또는 HTTP 압축과 같은 고급 기능을 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="feef6-129">Or, consider using advanced features, such as HTTP compression.</span></span>
  
## <a name="wan-accelerators"></a><span data-ttu-id="feef6-130">WAN 가속기</span><span class="sxs-lookup"><span data-stu-id="feef6-130">WAN Accelerators</span></span>

<span data-ttu-id="feef6-131">조직에서 WAN (wide area network) 가속 프록시 기기를 사용 하는 경우에는 Office 365 서비스에 액세스할 때 문제가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="feef6-131">If your organization uses wide area network (WAN) acceleration proxy appliances, you may encounter issues when you access the Office 365 services.</span></span> <span data-ttu-id="feef6-132">사용자가 Office 365에 액세스할 때 일관 된 환경을 유지 하도록 네트워크 장치 또는 장치를 최적화 해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="feef6-132">You may need to optimize your network device or devices to ensure that your users have a consistent experience when accessing Office 365.</span></span> <span data-ttu-id="feef6-133">예를 들어 Office 365 서비스는 일부 Office 365 콘텐츠 및 TCP 헤더를 암호화 합니다.</span><span class="sxs-lookup"><span data-stu-id="feef6-133">For example, Office 365 services encrypt some Office 365 content and the TCP header.</span></span> <span data-ttu-id="feef6-134">장치가 이러한 유형의 트래픽을 처리 하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="feef6-134">Your device may not be able to handle this kind of traffic.</span></span>
  
<span data-ttu-id="feef6-135">[Office 365에서 WAN 최적화 컨트롤러 또는 트래픽/검사 장치를 사용 하는](https://support.microsoft.com/kb/2690045)방법에 대 한 지원 설명을 읽으십시오.</span><span class="sxs-lookup"><span data-stu-id="feef6-135">Read our support statement about [Using WAN Optimization Controller or Traffic/Inspection devices with Office 365](https://support.microsoft.com/kb/2690045).</span></span>
  
## <a name="hardware-and-software-load-balancing-devices"></a><span data-ttu-id="feef6-136">하드웨어 및 소프트웨어 부하 분산 장치</span><span class="sxs-lookup"><span data-stu-id="feef6-136">Hardware and Software Load-balancing Devices</span></span>

<span data-ttu-id="feef6-137">조직에서 AD FS (Active Directory Federation Services) 서버 및/또는 Exchange 하이브리드 서버에 요청을 배포 하려면 HLB (하드웨어 부하 분산 장치) 또는 NLB (네트워크 부하 분산) 솔루션을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="feef6-137">Your organization needs to use a hardware load balancer (HLB) or a Network Load Balancing (NLB) solution to distribute requests to your Active Directory Federation Services (AD FS) servers and/or your Exchange hybrid servers.</span></span> <span data-ttu-id="feef6-138">부하 분산 장치는 온-프레미스 서버에 대 한 네트워크 트래픽을 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="feef6-138">Load-balancing devices control the network traffic to the on-premises servers.</span></span> <span data-ttu-id="feef6-139">이러한 서버는 single sign-on 및 Exchange 하이브리드 배포의 가용성을 보장 하는 데 매우 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="feef6-139">These servers are crucial in helping to ensure the availability of single sign-on and Exchange hybrid deployment.</span></span>
  
<span data-ttu-id="feef6-140">Windows Server에 기본 제공 되는 소프트웨어 기반 NLB 솔루션을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="feef6-140">We provide a software-based NLB solution built into Windows Server.</span></span> <span data-ttu-id="feef6-141">Office 365는이 솔루션을 지원 하 여 부하 분산을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="feef6-141">Office 365 supports this solution to achieve load balancing.</span></span>
  
## <a name="firewalls-and-proxies"></a><span data-ttu-id="feef6-142">방화벽과 프록시</span><span class="sxs-lookup"><span data-stu-id="feef6-142">Firewalls and proxies</span></span>

<span data-ttu-id="feef6-143">Office 365에 연결 하도록 방화벽과 프록시를 구성 하는 방법에 대 한 자세한 내용은 [office 365 끝점 관리](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a), [office 365 네트워크 연결 평가](assessing-network-connectivity.md)및 [office 365 endpoints FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d) 에 대 한 자세한 내용을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="feef6-143">For more details on configuring firewalls and proxies to connect to Office 365, read [Managing Office 365 endpoints](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a), [Assessing Office 365 network connectivity](assessing-network-connectivity.md), and [Office 365 endpoints FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d) to learn more about devices and circuit selection.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="feef6-144">참고 항목</span><span class="sxs-lookup"><span data-stu-id="feef6-144">See also</span></span>

[<span data-ttu-id="feef6-145">Office 365 서비스에 대 한 설정 가이드</span><span class="sxs-lookup"><span data-stu-id="feef6-145">Setup guides for Office 365 services</span></span>](setup-guides-for-office-365.md)

[<span data-ttu-id="feef6-146">Microsoft 365 Enterprise 개요</span><span class="sxs-lookup"><span data-stu-id="feef6-146">Microsoft 365 Enterprise overview</span></span>](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
