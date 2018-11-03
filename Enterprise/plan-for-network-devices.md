---
title: Office 365 서비스에 연결되는 네트워크 장치 계획
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/29/2016
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
ms.assetid: 073433ca-3511-4db9-b173-7a2edca57691
description: '요약: Office 365에 연결하는 데 사용되는 네트워크 용량, WAN 가속기 및 부하 분산 장치에 대한 고려 사항을 설명합니다.'
ms.openlocfilehash: 023eb3f5ed4d81d1d49d18c69ef8c81032fd5851
ms.sourcegitcommit: 317c2753be2aedb60698e94606ba59b63c962328
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/02/2018
ms.locfileid: "25933125"
---
# <a name="plan-for-network-devices-that-connect-to-office-365-services"></a><span data-ttu-id="4efa9-103">Office 365 서비스에 연결되는 네트워크 장치 계획</span><span class="sxs-lookup"><span data-stu-id="4efa9-103">Plan for network devices that connect to Office 365 services</span></span>

 <span data-ttu-id="4efa9-104">**요약**: Office 365에 연결하는 데 사용되는 네트워크 용량, WAN 가속기 및 부하 분산 장치에 대한 고려 사항을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4efa9-104">**Summary**: Describes considerations for network capacity, WAN accelerators, and load balancing devices that are used to connect to Office 365.</span></span>
  
<span data-ttu-id="4efa9-p101">일부 네트워크 하드웨어 지원 되는 동시 세션 수에 제한이 가질 수 있습니다. 사용자 들이 2, 000 개 이상의 조직에서는 추가 Office 365 서비스 트래픽을 처리할 수 있는지 확인 하도록 네트워크 장치를 모니터링 하는 것이 좋습니다. 단순 네트워크 관리 프로토콜 (SNMP) 소프트웨어 모니터링은이 작업을 수행 하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4efa9-p101">Some network hardware may have limitations on the number of concurrent sessions that are supported. For organizations having more than 2,000 users, we recommend that they monitor their network devices to ensure they are capable of handling the additional Office 365 service traffic. Simple Network Management Protocol (SNMP) monitoring software can help you do this.</span></span>

||
|:-----|
| <span data-ttu-id="4efa9-108">이 문서는 [네트워크 계획 및 Office 365에 대 한 성능 조정](https://aka.ms/tune)의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="4efa9-108">This article is part of [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>|

<span data-ttu-id="4efa9-p102">온-프레미스 보내는 인터넷 프록시 설정 클라이언트 응용 프로그램에 대 한 Office 365 서비스에 대 한 연결에도 영향을 줍니다. Microsoft 클라우드 서비스 Url 및 응용 프로그램에 대 한 연결을 허용 하도록 네트워크 프록시 장치로 구성 해야 합니다. 모든 조직은 다릅니다. Microsoft는이 프로세스 및 대역폭을 관리 하는 방법에 대 한 아이디어를 가져오려면는 프로 비전, [사례 연구 읽기](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365)합니다.</span><span class="sxs-lookup"><span data-stu-id="4efa9-p102">On-premises outgoing Internet proxy settings also affect connectivity to Office 365 services for your client applications. You must also configure your network proxy devices to allow connections for Microsoft cloud services URLs and applications. Every organization is different. To get an idea for how Microsoft manages this process and the amount of bandwidth we provision, [read the case study](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365).</span></span>
  
<span data-ttu-id="4efa9-113">비즈니스 도움말 문서에 대 한 다음 Skype 비즈니스 설정에 대 한 Skype 하는 방법에 대 한 자세한 내용은 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4efa9-113">The following Skype for Business Help articles have more information about Skype for Business settings:</span></span>
  
- [<span data-ttu-id="4efa9-114">관리자를 위한 비즈니스 Online 로그인 오류에 대 한 문제해결 Skype</span><span class="sxs-lookup"><span data-stu-id="4efa9-114">Troubleshooting Skype for Business Online sign-in errors for administrators</span></span>](https://docs.microsoft.com/skypeforbusiness/set-up-skype-for-business-online/troubleshooting-sign-in-errors-for-admins)

- [<span data-ttu-id="4efa9-115">비즈니스, 용 Skype에 연결할 수 없거나 특정 기능이 작동 하지 않으면 온-프레미스 방화벽이 연결을 차단 하기 때문에</span><span class="sxs-lookup"><span data-stu-id="4efa9-115">You cannot connect to Skype for Business, or certain features do not work, because an on-premises firewall blocks the connection</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=243625)

> [!NOTE]
> <span data-ttu-id="4efa9-116">이러한 설정의 대부분은 비즈니스 관련 용 Skype, 하는 동안 네트워크 구성에 대 한 일반적인 지침은 모든 Office 365 서비스에 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="4efa9-116">While many of these settings are Skype for Business-specific, the general guidance on network configuration is useful for all Office 365 services.</span></span>
  
## <a name="determining-network-capacity"></a><span data-ttu-id="4efa9-117">네트워크 용량 결정</span><span class="sxs-lookup"><span data-stu-id="4efa9-117">Determining Network Capacity</span></span>

<span data-ttu-id="4efa9-p103">연결에 있는 모든 네트워크 장치에는 용량 제한이 있습니다. 이러한 장치에는 장치들을 서로 연결하는 클라이언트 및 서버 네트워크 어댑터, 라우터, 스위치, 허브 등이 포함됩니다. 네트워크 용량이 충분하면 이러한 네트워크 장치가 포화 상태가 되지 않습니다. 네트워크 활동 모니터링은 모든 네트워크 장치의 실제 로드를 최대 용량 미만으로 유지하는 데 중요합니다. 네트워크 용량은 프록시 장치 성능에 영향을 줍니다. 네트워크 용량은 프록시 장치 성능에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4efa9-p103">Every network device that exists on a connection has its capacity limit. These devices include the client and server network adapters, routers, switches, and hubs that interconnect them. Adequate network capacity means that none of them are saturated. Monitoring network activity is essential to help ensure that the actual loads on all network devices are less than their maximum capacity. Network capacity affects proxy device performance.</span></span>
  
<span data-ttu-id="4efa9-p104">대부분의 경우 인터넷 연결 대역폭 트래픽 양에 대 한도 설정합니다. 사용량이 가장 많은 트래픽 시간 동안 약한 성능은 잠재적인 인터넷 링크의 과도 하 게 사용 하 여 발생 합니다. 이 상황은 지점 시나리오의 경우, 느린 넓은 WAN (광역 네트워크) 링크를 통해 지점 프록시 서버 컴퓨터 분기의 본사에서 프록시 장치에 연결 된 위치에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4efa9-p104">In most situations, the Internet connection bandwidth sets the limit for the amount of traffic. Weak performance during peak traffic hours is probably caused by excessive use of the Internet link. This situation also applies to a branch office scenario, where branch office proxy server computers are connected to the proxy device at the branch's headquarters over a slow Wide Area Network (WAN) link.</span></span>
  
<span data-ttu-id="4efa9-p105">네트워크 용량을 테스트 하려면 프록시 네트워크 인터페이스에 대 한 네트워크 활동을 모니터링 합니다. 모든 네트워크 인터페이스의 최대 대역폭의 75% 보다 많은 경우에 적절 한 없는 네트워크 인프라의 대역폭을 늘리면 하는 것이 좋습니다. 또는 HTTP 압축 등의 고급 기능을 사용 하 여 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="4efa9-p105">To test network capacity, monitor the network activity on the proxy network interface. If it's more than 75 percent of the maximum bandwidth of any network interface, consider increasing the bandwidth of the network infrastructure that's inadequate. Or, consider using advanced features, such as HTTP compression.</span></span>
  
## <a name="wan-accelerators"></a><span data-ttu-id="4efa9-129">WAN 가속기</span><span class="sxs-lookup"><span data-stu-id="4efa9-129">WAN Accelerators</span></span>

<span data-ttu-id="4efa9-p106">조직 광역 네트워크 (WAN) 가속 프록시 장치를 사용 하는 경우에 Office 365 서비스에 액세스할 때 문제가 발생할 수 있습니다. 네트워크 장치 또는 Office 365에 액세스할 때 사용자에 게 일관 된 환경을 권한이 있는지 확인 하는 장치를 최적화 해야할 수 있습니다. 등 Office 365 서비스의 일부 Office 365 콘텐츠 및 TCP 헤더를 암호화 합니다. 장치 이러한 종류의 트래픽 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4efa9-p106">If your organization uses wide area network (WAN) acceleration proxy appliances, you may encounter issues when you access the Office 365 services. You may need to optimize your network device or devices to ensure that your users have a consistent experience when accessing Office 365. For example, Office 365 services encrypt some Office 365 content and the TCP header. Your device may not be able to handle this kind of traffic.</span></span>
  
<span data-ttu-id="4efa9-134">[WAN 최적화 컨트롤러를 사용 하 여 또는 Office 365를 사용 하 여 트래픽을/검사 장치에](https://support.microsoft.com/kb/2690045)대 한 지원 정보를 보호 정책을 읽어보십시오.</span><span class="sxs-lookup"><span data-stu-id="4efa9-134">Read our support statement about [Using WAN Optimization Controller or Traffic/Inspection devices with Office 365](https://support.microsoft.com/kb/2690045).</span></span>
  
## <a name="hardware-and-software-load-balancing-devices"></a><span data-ttu-id="4efa9-135">하드웨어 및 소프트웨어 부하 분산 장치</span><span class="sxs-lookup"><span data-stu-id="4efa9-135">Hardware and Software Load-balancing Devices</span></span>

<span data-ttu-id="4efa9-p107">조직에서는 HLB(하드웨어 부하 분산 장치) 또는 NLB(네트워크 부하 분산) 솔루션을 사용하여 요청을 AD FS(Active Directory Federation Services) 서버 및/또는 Exchange 하이브리드 서버로 분산시켜야 합니다. 부하 분산 장치는 온-프레미스 서버에 대한 네트워크 트래픽을 제어합니다. Single Sign-On 및 Exchange 하이브리드 배포를 사용 가능한 상태로 유지하려면 이러한 서버가 반드시 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="4efa9-p107">Your organization needs to use a hardware load balancer (HLB) or a Network Load Balancing (NLB) solution to distribute requests to your Active Directory Federation Services (AD FS) servers and/or your Exchange hybrid servers. Load-balancing devices control the network traffic to the on-premises servers. These servers are crucial in helping to ensure the availability of single sign-on and Exchange hybrid deployment.</span></span>
  
<span data-ttu-id="4efa9-p108">Windows 서버에 기본 제공 되는 소프트웨어 기반 NLB 솔루션을 제공 합니다. Office 365 부하 분산을 달성 하기 위해이 솔루션을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="4efa9-p108">We provide a software-based NLB solution built into Windows Server. Office 365 supports this solution to achieve load balancing.</span></span>
  
## <a name="firewalls-and-proxies"></a><span data-ttu-id="4efa9-141">방화벽 및 프록시</span><span class="sxs-lookup"><span data-stu-id="4efa9-141">Firewalls and proxies</span></span>

<span data-ttu-id="4efa9-142">대 한 자세한 내용은 방화벽 및 프록시 장치 및 회로 선택 하는 방법에 대 한 자세한 내용은 [Office 365 관리 끝점](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a), [Office 365에 대 한 네트워크 연결](network-connectivity.md)및 [Office 365 끝점 FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d) 읽고 Office 365에 연결을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="4efa9-142">For more details on configuring firewalls and proxies to connect to Office 365, read [Managing Office 365 endpoints](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a), [Network connectivity to Office 365](network-connectivity.md), and [Office 365 endpoints FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d) to learn more about devices and circuit selection.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="4efa9-143">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4efa9-143">See also</span></span>

[<span data-ttu-id="4efa9-144">Office 365 서비스 배포 관리자</span><span class="sxs-lookup"><span data-stu-id="4efa9-144">Deployment advisors for Office 365 services</span></span>](deployment-advisors-for-office-365.md)
