---
title: 액세스 가능한 다이어그램-Microsoft Office Server 제품의 네트워크 통합
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 89f564eb-95c3-4077-bb92-75bf71b51270
f1.keywords:
- NOCSH
description: 이 문서는 Microsoft Office Server 제품의 Network Integration 이라는 다이어그램의 액세스 가능한 텍스트 버전입니다.
ms.openlocfilehash: def94a4523ad78676d6a9532a60dcba78032f23b
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843869"
---
# <a name="accessible-diagram---network-integration-of-microsoft-office-server-products"></a><span data-ttu-id="c47a4-103">액세스 가능한 다이어그램-Microsoft Office Server 제품의 네트워크 통합</span><span class="sxs-lookup"><span data-stu-id="c47a4-103">Accessible diagram - Network Integration of Microsoft Office Server Products</span></span>

<span data-ttu-id="c47a4-104">**요약:** 이 문서는 Microsoft Office Server 제품의 Network Integration 이라는 다이어그램의 액세스 가능한 텍스트 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-104">**Summary:** This article is an accessible text version of the diagram named Network Integration of Microsoft Office Server Products.</span></span>
  
<span data-ttu-id="c47a4-105">이 포스터는 Lync Server 2013, SharePoint 2013 및 Exchange Server 2013이 포함 된 네트워크 환경에 대 한 일반적인 그림을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-105">This poster provides a general illustration of a network environment that includes Lync Server 2013, SharePoint 2013, and Exchange Server 2013.</span></span> <span data-ttu-id="c47a4-106">또한이 제품은 원격 및 내부 액세스, 인증, 클라이언트 트래픽 및 공유 장치를 통한 라우팅 트래픽 등에서 공통적으로 사용 되는 다음과 같은 네트워킹 요소를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-106">It also illustrates the following networking elements that are common across these products: remote and internal access, authentication, client traffic, and routing traffic through shared devices.</span></span> 
  
## <a name="high-level-concepts-for-lync-exchange-sharepoint-server-and-office-web-apps"></a><span data-ttu-id="c47a4-107">Lync, Exchange, SharePoint Server 및 Office Web Apps에 대 한 높은 수준의 개념</span><span class="sxs-lookup"><span data-stu-id="c47a4-107">High-level concepts for Lync, Exchange, SharePoint Server, and Office Web Apps</span></span>

### <a name="about-the-design"></a><span data-ttu-id="c47a4-108">디자인 정보</span><span class="sxs-lookup"><span data-stu-id="c47a4-108">About the design</span></span>

#### <a name="streamlined-network-design"></a><span data-ttu-id="c47a4-109">합리적인 네트워크 디자인</span><span class="sxs-lookup"><span data-stu-id="c47a4-109">Streamlined network design</span></span>

<span data-ttu-id="c47a4-110">이 토폴로지는 SharePoint 2013, Exchange Server 2013 및 Lync Server 2013의 온-프레미스 네트워크 배포를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-110">This topology illustrates an on-premises network deployment of SharePoint 2013, Exchange Server 2013, and Lync Server 2013.</span></span> <span data-ttu-id="c47a4-111">또한 인터넷에서 인바운드 SMTP (Simple Mail Transfer Protocol) 트래픽에 대 한 스팸 및 맬웨어 보호 기능을 제공 하는 Microsoft 클라우드 기반 서비스의 사용과 Exchange Online Protection을 함께 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-111">It also shows the use of the Microsoft cloud-based service, Exchange Online Protection, which provides spam and malware protection for inbound Simple Mail Transfer Protocol (SMTP) traffic from the Internet.</span></span> 
  
<span data-ttu-id="c47a4-112">이 네트워크 디자인은 최소 네트워크 기능 집합으로 간소화 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-112">This network design is streamlined to a minimum set of network features.</span></span> <span data-ttu-id="c47a4-113">디자인은 일부 조직에 필요한 추가 보안 또는 인프라 기능을 고려 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-113">The design does not take into account additional security or infrastructure features that some organizations might require.</span></span> 
  
<span data-ttu-id="c47a4-114">다이어그램:</span><span class="sxs-lookup"><span data-stu-id="c47a4-114">This diagram:</span></span> 
  
- <span data-ttu-id="c47a4-115">게이트웨이 라우터를 통한 인바운드 및 아웃 바운드 트래픽과 해당 하는 SharePoint, Exchange 및 Lync server 계층에 대 한 부하 분산을 보여 주는 예제 네트워크 토폴로지 (외부 및 내부)를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-115">Provides an example network topology illustrating inbound and outbound traffic through a gateway router and load balancing of client session traffic (external and internal) to the appropriate SharePoint, Exchange, and Lync server tiers.</span></span> 
    
- <span data-ttu-id="c47a4-116">타사 VPN 게이트웨이 또는 DirectAccess 서버와 같은 선택적 원격 액세스 서버를 사용 하 여 로밍 또는 원격 직원에 대 한 보안 통신을 제공 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-116">Shows the use of optional remote access servers, such as a third-party VPN gateway or DirectAccess server, to provide secure communication for roaming or remote employees.</span></span> 
    
- <span data-ttu-id="c47a4-117">자세한 내용은 클라이언트에서 각 플랫폼 서버 계층으로의 SharePoint, Exchange 및 Lync 트래픽 흐름에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-117">Details the SharePoint, Exchange, and Lync traffic flow from the client to each platform server tier.</span></span> 
    
- <span data-ttu-id="c47a4-118">클라이언트 (예: 파트너 또는 직원)를 기반으로 하는 원격 또는 내부 액세스 연결의 유형 및 사용 되는 인증 방법을 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-118">Identifies the type of remote or internal access connection based on client (such as partner or employee), and the authentication method used.</span></span> 
    
- <span data-ttu-id="c47a4-119">프런트 엔드, 응용 프로그램, 데이터베이스 및 기타 수준을 식별 하 여 필요한 서버 역할로 SharePoint, Exchange 및 Lync 플랫폼을 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-119">Breaks down the SharePoint, Exchange, and Lync platforms by required server roles, identifying the front end, application, database, and other levels.</span></span> 
    
<span data-ttu-id="c47a4-120">SharePoint, Lync 및 Exchange에서 여기에 사용 되는 아키텍처는 이러한 플랫폼을 구현 하는 기본적인 방법을 제안 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-120">The architecture used here for SharePoint, Lync, and Exchange does not suggest a preferred way of implementing these platforms.</span></span> <span data-ttu-id="c47a4-121">또한 고유한 네트워크 요구 사항 및 보안 고려 사항에 따라 토폴로지가 다르다는 것을 보여 주는 예제를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-121">It merely provides an example as topologies differ based on unique network requirements and security considerations.</span></span> 
  
#### <a name="gateway-router"></a><span data-ttu-id="c47a4-122">게이트웨이 라우터</span><span class="sxs-lookup"><span data-stu-id="c47a4-122">Gateway router</span></span>

<span data-ttu-id="c47a4-123">이 토폴로지의 경우 게이트웨이 라우터는 네트워크의 가장자리에 위치 하 고 인트라넷에서 들어오고 나가는 모든 트래픽을 라우팅합니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-123">For this topology, the gateway router sits at the edge of the network and routes all incoming and outgoing traffic to and from the intranet.</span></span> <span data-ttu-id="c47a4-124">또는 게이트웨이 라우터와 표시 된 부하 분산 장치 (예: 여러 방화벽 계층) 간의 간격을 브리지 하는 다른 구성 요소도 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-124">Alternatively, there could also be other components that bridge the gap between the gateway router and the load balancer shown, such as multiple layers of firewalls.</span></span> <span data-ttu-id="c47a4-125">이 토폴로지는 네트워크를 여러 개 배포 하는 한 가지 방법만을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-125">This topology represents just one way to deploy your network out of many.</span></span> <span data-ttu-id="c47a4-126">이 구성에서 게이트웨이는 라우터 인터페이스에서 특별히 들어오고 나가는 IP 기반 트래픽을 허용 하기 위해 Acl (액세스 제어 목록)을 사용 하 여 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-126">In this configuration, the gateway is configured with access control lists (ACLs) to permit very specific incoming and outgoing IP-based traffic on the router interfaces.</span></span> <span data-ttu-id="c47a4-127">네트워크 전체에서 방화벽 등의 다른 장치 에서도 Acl, 고급 검사 또는 NAT (Network Address Translation)를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-127">ACLs, advanced inspection, or Network Address Translation (NAT) can also be performed on other devices, such as firewalls, throughout your network.</span></span> 
  
#### <a name="load-balancer-and-reverse-proxy-devices"></a><span data-ttu-id="c47a4-128">부하 분산 장치와 역방향 프록시 장치</span><span class="sxs-lookup"><span data-stu-id="c47a4-128">Load balancer and reverse proxy devices</span></span>

<span data-ttu-id="c47a4-129">하드웨어 또는 소프트웨어 부하 분산 솔루션을 사용 하 여 SharePoint 프런트 엔드 웹 서버 및 Exchange 클라이언트 액세스 서버 (CASs)를 포함 하는 세그먼트에 대 한 트래픽을 리디렉션할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-129">You can use hardware or software load balancing solutions to redirect traffic for segments including SharePoint front-end web servers and Exchange Client Access Servers (CASs).</span></span> <span data-ttu-id="c47a4-130">경우에 따라 지 속성 요구 사항에 대해 레이어 7 하드웨어 기반 부하 분산 장치를 사용 하는 것이 좋습니다 (예: 쿠키 또는 헤더).</span><span class="sxs-lookup"><span data-stu-id="c47a4-130">In some cases it's optimal to use a layer 7 hardware-based load balancer for persistence requirements as it can perform better by using information in the request, such as cookies or headers.</span></span> <span data-ttu-id="c47a4-131">그러나 비용, 활용도 증대 및 작업 부하와 같은 요소는 특정 요구에 적합 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-131">However, factors like cost and increased utilization and workload from such a solution might not be desirable for your specific needs.</span></span> <span data-ttu-id="c47a4-132">SharePoint, Exchange 및 Lync에서 부하 분산을 위해 다음 사항을 고려 하세요.</span><span class="sxs-lookup"><span data-stu-id="c47a4-132">Consider the following points for load balancing across SharePoint, Exchange, and Lync:</span></span> 
  
- <span data-ttu-id="c47a4-133">SharePoint-SharePoint 2013의 경우 프런트 엔드 웹 서버에 대 한 선호도를 사용 하도록 설정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-133">SharePoint - For SharePoint 2013, you do not need to enable affinity for your front-end web servers.</span></span> <span data-ttu-id="c47a4-134">일반적으로이는 고정 세션을 만드는 데 사용 되며 클라이언트에서 각 프런트 엔드 웹 서버에 대 한 여러 인증 요청을 방지 하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-134">Normally, this would be used for creating sticky sessions and avoiding multiple authentication requests from clients to each front-end web server.</span></span> <span data-ttu-id="c47a4-135">SharePoint 2013의 새로운 분산 캐시 서비스는 SharePoint 팜의 웹 서버 전체에 로그온 토큰을 저장 하 고 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-135">The new Distributed Cache service in SharePoint 2013 stores and distributes logon tokens across the web servers of the SharePoint farm.</span></span> 
    
- <span data-ttu-id="c47a4-136">Exchange-Exchange 2013에서 CAS 역할은 계층 4 부하 분산을 사용 하 여 전송 계층에 요청을 분산 하는 방식으로 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-136">Exchange - In Exchange 2013, the CAS role is designed to use layer 4 load balancing, distributing requests at the transport layer.</span></span> <span data-ttu-id="c47a4-137">따라서 부하 분산 장치 사용률 및 작업 부하가 크게 감소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-137">This can significantly decrease load balancer utilization and workload.</span></span> 
    
- <span data-ttu-id="c47a4-138">Lync 풀에 대 한 SIP (Session 착수 프로토콜) 트래픽에는 DNS (lync Domain Name System) 부하 분산을 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-138">Lync - Domain Name System (DNS) load balancing is recommended for Session Initiation Protocol (SIP) traffic for Lync pools.</span></span> <span data-ttu-id="c47a4-139">HLB (하드웨어 부하 분산)는 Lync Web (HTTPS) 트래픽에 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-139">Hardware load balancing (HLB) is required for Lync Web (HTTPS) traffic.</span></span> 
    
### <a name="remote-access-options"></a><span data-ttu-id="c47a4-140">원격 액세스 옵션</span><span class="sxs-lookup"><span data-stu-id="c47a4-140">Remote access options</span></span>

<span data-ttu-id="c47a4-141">인터넷의 파트너를 위해 인트라넷 리소스를 게시 하거나 원격 또는 로밍 직원에 게 보안 원격 액세스를 제공할 수 있는 몇 가지 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-141">There are several options that can publish intranet resources for partners on the Internet or provide secure remote access for remote or roaming employees.</span></span> <span data-ttu-id="c47a4-142">이러한 예에는 역방향 프록시, DirectAccess 및 타사 VPN 게이트웨이가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-142">Such examples include reverse proxies, DirectAccess, and third-party VPN gateways.</span></span> <span data-ttu-id="c47a4-143">이 섹션의 뒷부분에서 설명 하는 원격 액세스 솔루션은 SharePoint, Lync 및 Exchange에 대 한 것 이거나, 온-프레미스 배포에서 이러한 서버의 조합에 해당 합니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-143">The remote access solutions discussed later in this section are possibilities for SharePoint, Lync, and Exchange, or any combination of these servers in an on-premises deployment.</span></span> <span data-ttu-id="c47a4-144">그러나 일부 원격 옵션은 특정 솔루션에서 작동 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-144">However, some remote options might not work with a particular solution.</span></span> 
  
<span data-ttu-id="c47a4-145">역방향 프록시-역방향 프록시는 SSL (Secure Sockets Layer)과 같은 트래픽 암호화를 지원 하며,이를 통해 인터넷의 인증 된 사용자 및 파트너에 게 인트라넷 응용 프로그램 및 웹 리소스를 게시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-145">Reverse Proxy - A reverse proxy supports traffic encryption, such as Secure Sockets Layer (SSL), and with it you can publish intranet applications and web resources to authenticated users and partners on the Internet.</span></span> <span data-ttu-id="c47a4-146">Microsoft Forefront UAG (통합 액세스 게이트웨이)를 예로 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-146">An example is Microsoft Forefront Unified Access Gateway (UAG).</span></span> <span data-ttu-id="c47a4-147">많은 하드웨어 부하 분산 장치 역시 역방향 프록시 기능을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-147">Many hardware load balancers also support reverse proxy functionality.</span></span> <span data-ttu-id="c47a4-148">그러나 트래픽 격리, 보안 compartmentalization 및 성능 최적화와 같은 요구 사항에 따라 독립 실행형 솔루션을 사용 하는 경우에도 여전히 유효한 시나리오가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-148">However, there are still valid scenarios for using a standalone solution based on your needs and requirements, such as traffic isolation, security compartmentalization, and performance optimization.</span></span> 
  
<span data-ttu-id="c47a4-149">역방향 프록시 혜택 및 고려 사항:</span><span class="sxs-lookup"><span data-stu-id="c47a4-149">Reverse-proxy benefits and considerations:</span></span> 
  
- <span data-ttu-id="c47a4-150">인트라넷 리소스에 액세스 하는 파트너 또는 사용자에 대 한 인증 및 보안 액세스를 제공 합니다 (클라이언트와 역방향 프록시 서버 사이에 SSL (TCP 443) 사용).</span><span class="sxs-lookup"><span data-stu-id="c47a4-150">Provides authenticated and secured access for partners or users accessing intranet resources (uses SSL (TCP 443) between the client and reverse proxy server).</span></span> 
    
- <span data-ttu-id="c47a4-151">Exchange의 경우 Forefront UAG와 같은 역방향 프록시를 사용 하는 경우의 이점은 Exchange 클라이언트 액세스 서버에 액세스 하기 전에 사전 인증입니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-151">For Exchange, a benefit of using a reverse proxy such as Forefront UAG is pre-authentication before accessing the Exchange Client access server.</span></span> <span data-ttu-id="c47a4-152">OWA (Outlook Web Access)와 같은 게시 된 응용 프로그램을 사용 하는 원격 액세스 사용자는 내부 네트워크에 연결 되기 전에 기본, NTLM 또는 Kerberos 방법으로 인증할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-152">Remote access users using published applications such as Outlook Web Access (OWA) can authenticate with the basic, NTLM, or Kerberos methods before they reach the internal network.</span></span> 
    
- <span data-ttu-id="c47a4-153">Exchange 및 SharePoint의 경우 Forefront UAG와 같은 솔루션은 SSL 연결을 종료 하 고 인트라넷 리소스 서버의 로드를 줄이고 인증서를 위한 단일 관리 지점을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-153">For Exchange and SharePoint, solutions like Forefront UAG can terminate SSL connections and decrease the load of the intranet resources server while providing a single point of management for certificates.</span></span> 
    
- <span data-ttu-id="c47a4-154">Lync의 경우 웹 (HTTPS) 트래픽은 클라이언트 통신을 위해 역방향 프록시 (TCP 443)를 통과 합니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-154">For Lync, Web (HTTPS) traffic goes through the reverse proxy (TCP 443) for client communication.</span></span> <span data-ttu-id="c47a4-155">역방향 프록시는 Lync 웹 서비스, Exchange CAS 및 Office Web Apps에 대 한 HTTPS 연결을 프록시 합니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-155">The reverse proxy proxies the HTTPS connection to Lync Web Services, Exchange CAS, and Office Web Apps.</span></span> <span data-ttu-id="c47a4-156">Lync Server 2013에서는 UAG를 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-156">Lync Server 2013 does not support UAG.</span></span> 
    
<span data-ttu-id="c47a4-157">DirectAccess-인증에 IPsec (인터넷 프로토콜 보안)을 사용 하 고 DirectAccess 클라이언트와 서버 간의 트래픽 암호화에 사용 되는 원격 액세스 기술입니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-157">DirectAccess - A remote access technology that relies on Internet Protocol security (IPsec) for authentication and for encrypting traffic between the DirectAccess client and server.</span></span> <span data-ttu-id="c47a4-158">DirectAccess는 연결을 시작할 필요 없이 로밍 및 원격 직원과의 인터넷 및 인트라넷 리소스에 동시에 액세스할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-158">DirectAccess provides simultaneous access to both Internet and intranet resources for roaming and remote employees without having to initiate a connection.</span></span> 
  
<span data-ttu-id="c47a4-159">고려해 야 할 DirectAccess:</span><span class="sxs-lookup"><span data-stu-id="c47a4-159">DirectAccess points to consider:</span></span> 
  
- <span data-ttu-id="c47a4-160">DirectAccess는 DirectAccess 클라이언트와 서버 간에 IPsec 보호 된 트래픽 (프로토콜 50, 51 및 UDP 500)을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-160">DirectAccess uses IPsec protected traffic (protocol 50 and 51 and UDP 500) between the DirectAccess client and server.</span></span> 
    
- <span data-ttu-id="c47a4-161">Windows Server 2012 및 Windows 8 용 DirectAccess에는 서버 및 클라이언트 인증을 위한 PKI (공개 키 인프라) 배포가 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-161">DirectAccess for Windows Server 2012 and Windows 8 does not need a public key infrastructure (PKI) deployment for server and client authentication.</span></span> 
    
- <span data-ttu-id="c47a4-162">IPsec 암호화 및 암호 해독과 관련 된 오디오 및 비디오 대기 시간 문제로 인해 Lync Server 2013에서 DirectAccess를 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-162">We recommend against using DirectAccess with Lync Server 2013 because of audio and video latency issues associated with IPsec encryption and decryption.</span></span> 
    
    <span data-ttu-id="c47a4-163">VPN 게이트웨이-일반적인 VPN 게이트웨이는 원격 액세스 클라이언트 컴퓨터가 터널링 및 사용자가 시작한 연결을 통해 논리적으로 인트라넷에 투영 되는 원격 액세스 연결을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-163">VPN Gateway - Typical VPN gateways provide a remote access connection in which a remote access client computer is logically projected onto the intranet through a tunneled and user-initiated connection.</span></span> <span data-ttu-id="c47a4-164">Windows Server 2012 또는 몇몇 타사 솔루션에서 통합 원격 액세스를 사용 하 여 로밍 또는 원격 직원을 위해 인트라넷에 보안 액세스를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-164">You can use Unified Remote Access in Windows Server 2012 or several third-party solutions to provide secured access to the intranet for roaming or remote employees.</span></span> <span data-ttu-id="c47a4-165">Lync에는 VPN을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-165">VPN is not recommended for Lync.</span></span> <span data-ttu-id="c47a4-166">원격 Lync 트래픽은에 지 서버 및 분할 터널링을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-166">Remote Lync traffic should use the Edge Servers and split tunneling.</span></span> 
    
### <a name="domain-name-system-dns-considerations"></a><span data-ttu-id="c47a4-167">DNS (Domain Name System) 고려 사항</span><span class="sxs-lookup"><span data-stu-id="c47a4-167">Domain Name System (DNS) considerations</span></span>

<span data-ttu-id="c47a4-168">인터넷 및 인트라넷 사용자가 DNS 이름을 적절 한 IP 주소로 확인 하는 데 사용할 수 있는 DNS 레코드 집합을 계획 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-168">You need to plan for the set of DNS records that allow both Internet and intranet users to resolve DNS names to the appropriate IP addresses.</span></span> 
  
- <span data-ttu-id="c47a4-169">인터넷 기반 파트너 및 로밍 또는 원격 사원의 경우, 인터넷 DNS 서버에 등록 된 DNS 레코드는 게이트웨이 라우터에 해당 하는 공용 IP 주소 집합, Lync에 지 서버, Vip (가상 IP 주소) 집합에 대 한 해결 방법을 제공 합니다. 부하 분산 및 DirectAccess 또는 VPN 게이트웨이가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-169">For Internet-based partners and roaming or remote employees, DNS records registered with Internet DNS servers provide resolution to the set of public IP addresses corresponding to the gateway router, the Lync Edge Server, the set of virtual IP addresses (VIPs) on the load balancer, and the DirectAccess or VPN gateway as needed.</span></span> 
    
- <span data-ttu-id="c47a4-170">인트라넷 기반 사용자의 경우 인트라넷 DNS 서버를 사용 하 여 등록 된 DNS 레코드는 SharePoint, Lync 및 Exchange 리소스에 액세스할 수 있도록 부하 분산 장치에 대 한 Vip (가상 IP 주소) 집합에 대 한 해결 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-170">For intranet-based users, DNS records registered with intranet DNS servers provide resolution to the set of virtual IP addresses (VIPs) on the load balancer for access to SharePoint, Lync, and Exchange resources.</span></span> 
    
- <span data-ttu-id="c47a4-171">DirectAccess 클라이언트는 인트라넷 dns 이름 공간 및 인터넷 DNS 서버에 해당 하는 이름에 대해 인트라넷 DNS 서버를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-171">DirectAccess clients use intranet DNS servers for names corresponding to the intranet DNS name space and Internet DNS servers for names that do not.</span></span> <span data-ttu-id="c47a4-172">DirectAccess 작업을 단순화 하려면 인트라넷 및 인터넷 기반 이름에 대해 서로 다른 DNS 네임 스페이스를 사용 하는 분할 DNS 구현을 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-172">To simplify the operation of DirectAccess, consider the use of a split DNS implementation that uses different DNS namespaces for intranet and Internet-based names.</span></span> <span data-ttu-id="c47a4-173">예를 들어 인트라넷 네임 스페이스에는 contoso.com for Internet namespace 및 corp.contoso.com을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-173">For example, use contoso.com for Internet namespace and corp.contoso.com for the intranet namespace.</span></span> 
    
- <span data-ttu-id="c47a4-174">Exchange는 라우팅 DNS 모델을 사용 하며,이는 호스트에서 IP로의 확인이 회사 네트워크의 공용 라우팅된 트래픽에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-174">Exchange uses a split DNS model where host to IP resolution differs on publicly routed traffic from that on the corporate network.</span></span> <span data-ttu-id="c47a4-175">최소한 OWA, 자동 검색, 클라이언트 트래픽의 ActiveSync Url 및 인바운드 메일용 MX 레코드에 대 한 DNS 레코드가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-175">At a minimum, you need to have DNS records for OWA, Autodiscover, ActiveSync URLs for client traffic, and an MX record for inbound mail.</span></span> 
    
- <span data-ttu-id="c47a4-176">EOP (Exchange Online Protection)를 사용 하는 경우 MX 레코드는 Exchange 팜이 아닌 해당 서비스를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-176">If you are using Exchange Online Protection (EOP), your MX record points to that service instead of your Exchange farm.</span></span> 
    
- <span data-ttu-id="c47a4-177">Exchange의 경우 공용 DNS에 대 한 소유권 TXT 레코드와 페더레이션 공유를 설정 하기 위한 페더레이션 조직 ID가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-177">For Exchange, you need a proof of ownership TXT record in your public DNS, and a Federation Org ID to set up federated sharing.</span></span> 
    
- <span data-ttu-id="c47a4-178">원격 액세스 VPN 연결이 활성 상태인 경우 인트라넷 DNS 서버만 사용 하도록 원격 액세스 VPN 클라이언트를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-178">Remote access VPN clients can be configured to use only intranet DNS servers when the remote access VPN connection is active.</span></span> 
    
### <a name="diagram-description"></a><span data-ttu-id="c47a4-179">다이어그램 설명</span><span class="sxs-lookup"><span data-stu-id="c47a4-179">Diagram Description</span></span>

<span data-ttu-id="c47a4-180">이 다이어그램에서는 게이트웨이 라우터를 통한 인바운드 및 아웃 바운드 트래픽과 해당 하는 SharePoint, Exchange 및 Lync server 계층에 대 한 부하 분산 (외부 및 내부)을 보여 주는 예제 네트워크 토폴로지를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-180">This diagram provides an example network topology illustrating inbound and outbound traffic through a gateway router and load balancing of client session traffic (external and internal) to the appropriate SharePoint, Exchange, and Lync server tiers.</span></span> <span data-ttu-id="c47a4-181">이 다이어그램의 설명은 다음과 같은 두 부분으로 나뉩니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-181">The description of this diagram is divided into two parts:</span></span> 
  
- <span data-ttu-id="c47a4-182">다이어그램에 표시 된 구성 요소에 대 한 설명</span><span class="sxs-lookup"><span data-stu-id="c47a4-182">Description of components shown in the diagram</span></span> 
    
- <span data-ttu-id="c47a4-183">구성 요소를 통해 SharePoint, Exchange, Lync 및 Office Web Apps 서버 계층으로 트래픽이 이동 하는 방식에 대 한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-183">Description of how traffic moves through the components to the SharePoint, Exchange, Lync, and Office Web Apps server tiers.</span></span> 
    
#### <a name="description-of-components-shown-in-the-diagram"></a><span data-ttu-id="c47a4-184">다이어그램에 표시 된 구성 요소에 대 한 설명</span><span class="sxs-lookup"><span data-stu-id="c47a4-184">Description of components shown in the diagram</span></span>

#### <a name="user-types"></a><span data-ttu-id="c47a4-185">사용자 유형</span><span class="sxs-lookup"><span data-stu-id="c47a4-185">User types</span></span>

<span data-ttu-id="c47a4-186">네트워크 및 클라우드 서비스 외에도 다음과 같은 네 가지 유형의 사용자와 내부 1 개가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-186">There are four different types of users, three outside the network and cloud services and one internal, which include:</span></span> 
  
- <span data-ttu-id="c47a4-187">파트너 회사 (회사 간)-외부</span><span class="sxs-lookup"><span data-stu-id="c47a4-187">Partner companies (business-to-business)-external</span></span> 
    
- <span data-ttu-id="c47a4-188">개별 파트너 (SharePoint 및 익명 (Lync))-외부</span><span class="sxs-lookup"><span data-stu-id="c47a4-188">Individual partners (SharePoint and anonymous (Lync))-external</span></span> 
    
- <span data-ttu-id="c47a4-189">로밍 및 원격 직원-외부</span><span class="sxs-lookup"><span data-stu-id="c47a4-189">Roaming and remote employees-external</span></span> 
    
- <span data-ttu-id="c47a4-190">내부 직원</span><span class="sxs-lookup"><span data-stu-id="c47a4-190">Internal employees</span></span> 
    
#### <a name="cloud-based-email-traffic"></a><span data-ttu-id="c47a4-191">클라우드 기반 전자 메일 트래픽</span><span class="sxs-lookup"><span data-stu-id="c47a4-191">Cloud-based email traffic</span></span>

<span data-ttu-id="c47a4-192">SMTP 기반 전자 메일 트래픽을 위한 클라우드 기반 구성 요소 (인터넷 메일 호스트 또는 Exchange Online Protection)가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-192">There is a cloud-based component for SMTP-based email traffic, either Internet Mail Hosts or Exchange Online Protection.</span></span> 
  
#### <a name="authentication-for-external-access"></a><span data-ttu-id="c47a4-193">외부 액세스에 대 한 인증</span><span class="sxs-lookup"><span data-stu-id="c47a4-193">Authentication for external access</span></span>

<span data-ttu-id="c47a4-194">Lync, SharePoint 및 Exchange에 대 한 특정 인증 절차 집합은 각 사용자 유형에 대해 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-194">There is a specific set of authentication procedures for Lync, SharePoint, and Exchange for each of the user types.</span></span> <span data-ttu-id="c47a4-195">여기에 대해서는이 문서의 뒷부분에 자세히 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-195">They are described in more detail later in this document.</span></span> 
  
#### <a name="gateway-router-with-acls"></a><span data-ttu-id="c47a4-196">Acl을 사용 하는 게이트웨이 라우터</span><span class="sxs-lookup"><span data-stu-id="c47a4-196">Gateway router with ACLs</span></span>

<span data-ttu-id="c47a4-197">게이트웨이 라우터는 네트워크의 가장자리에 위치 하 고 인트라넷에서 들어오고 나가는 모든 트래픽을 라우팅합니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-197">The gateway router sits at the edge of the network and routes all incoming and outgoing traffic to and from the intranet.</span></span> 
  
#### <a name="remote-access-servers-for-lync-and-sharepoint"></a><span data-ttu-id="c47a4-198">Lync 및 SharePoint 용 원격 액세스 서버</span><span class="sxs-lookup"><span data-stu-id="c47a4-198">Remote access servers for Lync and SharePoint</span></span>

<span data-ttu-id="c47a4-199">이 토폴로지에는 Lync Edge 서버와 SharePoint VPN 게이트웨이 또는 DirectAccess 서버가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-199">This topology includes a Lync Edge server, and a SharePoint VPN gateway or DirectAccess server.</span></span> 
  
#### <a name="load-balancer-and-reverse-proxy-device"></a><span data-ttu-id="c47a4-200">부하 분산 장치 및 역방향 프록시 디바이스</span><span class="sxs-lookup"><span data-stu-id="c47a4-200">Load balancer and reverse proxy device</span></span>

<span data-ttu-id="c47a4-201">하드웨어 또는 소프트웨어 부하 분산 솔루션을 사용 하 여 SharePoint 프런트 엔드 웹 서버 및 Exchange 클라이언트 액세스 서버 (CASs)를 포함 하는 세그먼트에 대 한 트래픽을 리디렉션할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-201">You can use hardware or software load balancing solutions to redirect traffic for segments including SharePoint front-end web servers and Exchange Client Access Servers (CASs).</span></span> <span data-ttu-id="c47a4-202">이 토폴로지는 부하 분산 장치의 Lync VIP, SharePoint VIP 및 Exchange VIP 구성 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-202">This topology shows Lync VIP, SharePoint VIP, and Exchange VIP components in the load balancer.</span></span> 
  
#### <a name="servers"></a><span data-ttu-id="c47a4-203">Servers</span><span class="sxs-lookup"><span data-stu-id="c47a4-203">Servers</span></span>

<span data-ttu-id="c47a4-204">서버는 Lync, SharePoint, Exchange 및 Office Web Apps 서버 4 대입니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-204">There are four servers: Lync, SharePoint, Exchange, and Office Web Apps Server.</span></span> <span data-ttu-id="c47a4-205">각 서버에는 프런트 엔드, 클라이언트 액세스 계층, 응용 프로그램 계층 및 데이터베이스/저장소 계층의 세 가지 계층을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-205">Each server can have three tiers: a front-end, client-access tier, an application tier, and a database/storage tier.</span></span>
  
#### <a name="front-end-client-access-tier"></a><span data-ttu-id="c47a4-206">프런트 엔드, 클라이언트 액세스 계층</span><span class="sxs-lookup"><span data-stu-id="c47a4-206">Front-end, client-access tier</span></span>

<span data-ttu-id="c47a4-207">이 계층에는 4 대의 모든 서버에 구성 요소가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-207">This tier has components on all four servers:</span></span> 
  
- <span data-ttu-id="c47a4-208">Lync 풀 (프런트 엔드)</span><span class="sxs-lookup"><span data-stu-id="c47a4-208">Lync pool (front end).</span></span> <span data-ttu-id="c47a4-209">이 다이어그램은 두 개의 Lync 데이터베이스를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-209">The diagram shows two Lync databases.</span></span> 
    
- <span data-ttu-id="c47a4-210">SharePoint 프런트 엔드 및 분산 캐시</span><span class="sxs-lookup"><span data-stu-id="c47a4-210">SharePoint front end and distributed cache.</span></span> <span data-ttu-id="c47a4-211">이 다이어그램은 세 개의 SharePoint 데이터베이스를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-211">The diagram shows three SharePoint databases.</span></span> 
    
- <span data-ttu-id="c47a4-212">Exchange CAS</span><span class="sxs-lookup"><span data-stu-id="c47a4-212">Exchange CAS.</span></span> <span data-ttu-id="c47a4-213">이 다이어그램에는 두 개의 Exchange 데이터베이스가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-213">The diagram shows two Exchange databases.</span></span> 
    
- <span data-ttu-id="c47a4-214">Office Web Apps 서버</span><span class="sxs-lookup"><span data-stu-id="c47a4-214">Office Web Apps Server.</span></span> <span data-ttu-id="c47a4-215">두 개의 Office Web Apps 데이터베이스를 보여 주는 다이어그램</span><span class="sxs-lookup"><span data-stu-id="c47a4-215">The diagram shows two Office Web Apps databases.</span></span> 
    
#### <a name="application-tier"></a><span data-ttu-id="c47a4-216">응용 프로그램 계층</span><span class="sxs-lookup"><span data-stu-id="c47a4-216">Application tier</span></span>

<span data-ttu-id="c47a4-217">이 계층에는 SharePoint server의 구성 요소만 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-217">This tier has components only on the SharePoint server:</span></span> 
  
- <span data-ttu-id="c47a4-218">검색 (쿼리, 인덱스, 관리)</span><span class="sxs-lookup"><span data-stu-id="c47a4-218">Search (query, index, admin).</span></span> <span data-ttu-id="c47a4-219">이 다이어그램은 세 개의 SharePoint 데이터베이스를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-219">The diagram shows three SharePoint databases.</span></span> 
    
- <span data-ttu-id="c47a4-220">일괄 처리</span><span class="sxs-lookup"><span data-stu-id="c47a4-220">Batch processing.</span></span> <span data-ttu-id="c47a4-221">이 다이어그램은 세 개의 SharePoint 데이터베이스를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-221">The diagram shows three SharePoint databases.</span></span> 
    
#### <a name="databasestorage-tier"></a><span data-ttu-id="c47a4-222">데이터베이스/저장소 계층</span><span class="sxs-lookup"><span data-stu-id="c47a4-222">Database/storage tier</span></span>

<span data-ttu-id="c47a4-223">이 계층에는 Lync, SharePoint 및 Exchange 서버에 구성 요소가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-223">This tier has components on the Lync, SharePoint, and Exchange servers:</span></span> 
  
- <span data-ttu-id="c47a4-224">Lync 데이터베이스 (백 엔드)</span><span class="sxs-lookup"><span data-stu-id="c47a4-224">Lync Database (backend).</span></span> <span data-ttu-id="c47a4-225">이 다이어그램은 3 개의 Lync 데이터베이스를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-225">The diagram shows three Lync databases.</span></span> 
    
- <span data-ttu-id="c47a4-226">SharePoint 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="c47a4-226">SharePoint Database.</span></span> <span data-ttu-id="c47a4-227">이 다이어그램은 세 개의 SharePoint 데이터베이스를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-227">The diagram shows three SharePoint databases.</span></span> 
    
- <span data-ttu-id="c47a4-228">Exchange 사서함 서버</span><span class="sxs-lookup"><span data-stu-id="c47a4-228">Exchange Mailbox server.</span></span> <span data-ttu-id="c47a4-229">이 다이어그램에는 두 개의 Exchange 사서함 서버가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-229">The diagram shows two Exchange Mailbox servers.</span></span> 
    
<span data-ttu-id="c47a4-230">각 SharePoint server 역할에 설치 된 구성 요소에 대 한 자세한 내용은 [sharepoint 용 능률적인 토폴로지-2013](https://aka.ms/Ma5cgk)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="c47a4-230">For more information about components installed on each of the SharePoint server roles, see [Streamlined Topologies for SharePoint 2013](https://aka.ms/Ma5cgk).</span></span> 
  
#### <a name="description-of-how-traffic-moves-through-the-components-to-the-different-server-tiers"></a><span data-ttu-id="c47a4-231">구성 요소를 통해 트래픽이 서로 다른 서버 계층으로 이동 하는 방식에 대 한 설명</span><span class="sxs-lookup"><span data-stu-id="c47a4-231">Description of how traffic moves through the components to the different server tiers</span></span>

<span data-ttu-id="c47a4-232">이 섹션에서는 사용자 요청이 네트워크 토폴로지를 이동 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-232">This section describes how user requests move through the network topology.</span></span> 
  
#### <a name="authentication-and-routing-for-external-access"></a><span data-ttu-id="c47a4-233">외부 액세스용 인증 및 라우팅</span><span class="sxs-lookup"><span data-stu-id="c47a4-233">Authentication and routing for external access</span></span>

<span data-ttu-id="c47a4-234">네트워크 및 클라우드 서비스 외에도 다음과 같은 세 가지 유형의 클라이언트가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-234">There are three different types of clients outside the network and cloud services, which include:</span></span> 
  
- <span data-ttu-id="c47a4-235">파트너 회사 (회사 간)-외부</span><span class="sxs-lookup"><span data-stu-id="c47a4-235">Partner companies (business-to-business)-external</span></span> 
    
- <span data-ttu-id="c47a4-236">개별 파트너 (SharePoint 및 익명 (Lync))-외부</span><span class="sxs-lookup"><span data-stu-id="c47a4-236">Individual partners (SharePoint and anonymous (Lync))-external</span></span> 
    
- <span data-ttu-id="c47a4-237">로밍 및 원격 직원-외부</span><span class="sxs-lookup"><span data-stu-id="c47a4-237">Roaming and remote employees-external</span></span> 
    
<span data-ttu-id="c47a4-238">각 외부 사용자 유형에 대 한 인증 및 라우팅 프로세스는 개별적으로 설명 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-238">The authentication and routing process for each external user type is described individually.</span></span> 
  
#### <a name="partner-companies-business-to-business-httpspartnerwebcontosocom"></a><span data-ttu-id="c47a4-239">파트너 회사 (b2b) (https://partnerweb.contoso.com)</span><span class="sxs-lookup"><span data-stu-id="c47a4-239">Partner companies (business-to-business) (https://partnerweb.contoso.com)</span></span>

- <span data-ttu-id="c47a4-240">Lync: 다른 조직과의 페더레이션 트러스트, AOL과의 Skype 및 공용 IM 연결 (PIC)</span><span class="sxs-lookup"><span data-stu-id="c47a4-240">Lync: federation trust with other organizations, Skype and Public IM Connectivity (PIC) with AOL.</span></span> <span data-ttu-id="c47a4-241">Lync federation 트래픽은 게이트웨이 라우터를 lync에 지 서버에서 lync VIP (부하 분산 장치/역방향 프록시 서버)로 이동한 다음 Lync Server로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-241">The Lync federation traffic goes through the gateway router to the Lync Edge Server, to the Lync VIP (load balancer/reverse proxy server), and then to the Lync Server.</span></span> 
    
- <span data-ttu-id="c47a4-242">SharePoint: SAML 인증을 사용 하는 신뢰할 수 있는 파트너 id 공급자</span><span class="sxs-lookup"><span data-stu-id="c47a4-242">SharePoint: Trusted partner identity provider with SAML authentication.</span></span> <span data-ttu-id="c47a4-243">SharePoint 클라이언트 트래픽은 게이트웨이 라우터를 통해 SharePoint VIP (부하 분산 장치/역방향 프록시 서버)로 이동한 다음 SharePoint 서버로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-243">The SharePoint client traffic goes through the Gateway router to the SharePoint VIP (load balancer/reverse proxy server), and then to the SharePoint Server.</span></span> 
    
- <span data-ttu-id="c47a4-244">Exchange: 메일 트래픽용 상호 인증 TLS, 페더레이션 공유에 대 한 SAML 인증</span><span class="sxs-lookup"><span data-stu-id="c47a4-244">Exchange: Mutual Auth TLS for mail traffic, SAML authentication for Federated Sharing.</span></span> <span data-ttu-id="c47a4-245">Exchange 클라이언트 트래픽은 게이트웨이 라우터를 통해 Exchange VIP (부하 분산 장치/역방향 프록시 서버)로 이동한 다음 Exchange 서버로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-245">The Exchange client traffic goes through the Gateway router to the Exchange VIP (load balancer/reverse proxy server), and then to the Exchange Server.</span></span> 
    
- <span data-ttu-id="c47a4-246">SMTP 트래픽은 게이트웨이 라우터를 통과 하 고 Exchange VIP (부하 분산 장치/역방향 프록시 서버)를 통해 Exchange 서버를 통과 합니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-246">SMTP traffic goes through the Gateway router and through the Exchange VIP (load balancer/reverse proxy server) to the Exchange server.</span></span> 
    
#### <a name="individual-partners-sharepoint-and-anonymous-lync-httpspartnerwebcontosocom-and-httpsmeetcontosocom"></a><span data-ttu-id="c47a4-247">개별 파트너 (SharePoint) 및 익명 (Lync)https://partnerweb.contoso.com 및https://meet.contoso.com)</span><span class="sxs-lookup"><span data-stu-id="c47a4-247">Individual partners (SharePoint) and anonymous (Lync) (https://partnerweb.contoso.com and https://meet.contoso.com)</span></span>

- <span data-ttu-id="c47a4-248">Lync: 익명 사용자는 직원용으로 구성 된 Lync 모임에만 참가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-248">Lync: anonymous users can only join Lync meetings organized by employees.</span></span> <span data-ttu-id="c47a4-249">Lync federation 트래픽은 게이트웨이 라우터를 lync에 지 서버에서 lync VIP (부하 분산 장치/역방향 프록시 서버)로 이동한 다음 Lync Server로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-249">The Lync federation traffic goes through the Gateway router to the Lync Edge Server, to the Lync VIP (load balancer/reverse proxy server), and then to the Lync Server.</span></span> 
    
- <span data-ttu-id="c47a4-250">SharePoint: SAML 인증 또는 폼 기반 인증을 사용 하는 신뢰할 수 있는 파트너 id 공급자</span><span class="sxs-lookup"><span data-stu-id="c47a4-250">SharePoint: Trusted partner identity provider with SAML authentication or forms-based authentication.</span></span> <span data-ttu-id="c47a4-251">SharePoint 클라이언트 트래픽은 게이트웨이 라우터를 통해 SharePoint VIP (부하 분산 장치/역방향 프록시 서버)로 이동한 다음 SharePoint 서버로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-251">The SharePoint client traffic goes through the Gateway router to the SharePoint VIP (load balancer/reverse proxy server), and then to the SharePoint Server.</span></span> 
    
- <span data-ttu-id="c47a4-252">Exchange: 적용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-252">Exchange: Does not apply.</span></span> 
    
- <span data-ttu-id="c47a4-253">Lync 웹 트래픽은 게이트웨이 라우터를 lync에 지 서버에서 lync VIP (부하 분산 장치/역방향 프록시 서버)에 대 한 하드웨어 부하 분산 장치 (HTTPS 트래픽에 필요)로 이동한 다음 Lync Server로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-253">Lync Web traffic goes through the Gateway router to the Lync Edge Server, to the Lync VIP (load balancer/reverse proxy server), to a hardware load balancer, which is required for HTTPS traffic, and then to the Lync Server.</span></span> 
    
#### <a name="roaming-and-remote-employees"></a><span data-ttu-id="c47a4-254">로밍 및 원격 직원</span><span class="sxs-lookup"><span data-stu-id="c47a4-254">Roaming and remote employees</span></span>

1. https://intranet.contoso.com 
    
2. https://teams.contoso.com 
    
3. https://my.contoso.com
    
4. https://partnerweb.contoso.com 
    
5. https://mail.contoso.com* 
    
6. https://dial.contoso.com*
    
7. https://meet.contoso.com*
    
* <span data-ttu-id="c47a4-255">Exchange URL에는 자동 검색, ecp, EWS, Microsoft-서버-ActiveSync, OAB, owa, PowerShell 가상 디렉터리가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-255">The Exchange URL has the following virtual directories: Autodiscover, ecp, EWS, Microsoft-Server-ActiveSync, OAB, owa, PowerShell</span></span> 
  
- <span data-ttu-id="c47a4-256">Lync: TLS-DSK 또는 NTLM 인증</span><span class="sxs-lookup"><span data-stu-id="c47a4-256">Lync: TLS-DSK or NTLM authentication.</span></span> <span data-ttu-id="c47a4-257">Lync 클라이언트 트래픽은 게이트웨이 라우터를 lync에 지 서버에서 lync VIP (부하 분산 장치/역방향 프록시 서버)로 이동한 다음 Lync Server로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-257">The Lync client traffic goes through the Gateway router to the Lync Edge Server, to the Lync VIP (load balancer/reverse proxy server), and then to the Lync Server.</span></span> 
    
- <span data-ttu-id="c47a4-258">SharePoint: AD DS (Active Directory 도메인 서비스), 폼 기반 인증 또는 SAML 인증을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-258">SharePoint: Active Directory Domain Services (AD DS), forms-based authentication, or SAML authentication.</span></span> <span data-ttu-id="c47a4-259">SharePoint 클라이언트 트래픽은 VPN 게이트웨이 또는 DirectAccess 서버를 통해 SharePoint VIP (부하 분산 장치/역방향 프록시 서버)로 이동한 다음 SharePoint server로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-259">The SharePoint client traffic goes through the VPN gateway or the DirectAccess server to the SharePoint VIP (load balancer/reverse proxy server), and then to the SharePoint server.</span></span> 
    
- <span data-ttu-id="c47a4-260">Exchange: SSL (ActiveSync, 자동 검색) 및 OWA (폼 기반 인증)를 통한 기본 인증</span><span class="sxs-lookup"><span data-stu-id="c47a4-260">Exchange: Basic authentication over SSL (ActiveSync, Autodiscover), forms-based authentication (OWA).</span></span> <span data-ttu-id="c47a4-261">Exchange 클라이언트 트래픽은 게이트웨이 라우터를 통해 Exchange VIP (부하 분산 장치/역방향 프록시 서버)로 이동한 다음 Exchange 서버로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-261">The Exchange client traffic goes through the Gateway router to the Exchange VIP (load balancer/reverse proxy server), and then to the Exchange Server.</span></span> 
    
- <span data-ttu-id="c47a4-262">Lync 클라이언트 트래픽은 게이트웨이 라우터를 통해 Lync VIP (부하 분산 장치/역방향 프록시 서버)에 대 한 하드웨어 부하 분산 장치 (HTTPS 트래픽에 필요 함)로 이동한 다음 Lync Server로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-262">Lync client traffic goes through the Gateway router to the Lync VIP (load balancer/reverse proxy server) to a hardware load balancer, which is required for HTTPS traffic, and then to the Lync Server.</span></span> 
    
#### <a name="authentication-for-internal-access"></a><span data-ttu-id="c47a4-263">내부 액세스용 인증</span><span class="sxs-lookup"><span data-stu-id="c47a4-263">Authentication for internal access</span></span>

#### <a name="internal-employees"></a><span data-ttu-id="c47a4-264">내부 직원</span><span class="sxs-lookup"><span data-stu-id="c47a4-264">Internal employees</span></span>

> https://intranet.contoso.com 
    
> https://teams.contoso.com 
    
> https://my.contoso.com
    
> https://partnerweb.contoso.com
    
> https://mail.contoso.com* 
    
> https://dial.contoso.com 
    
> https://meet.contoso.com
    
> https://admin.contoso.com
    
- <span data-ttu-id="c47a4-265">Lync: Kerberos, TLS-DSK 또는 NTLM 인증</span><span class="sxs-lookup"><span data-stu-id="c47a4-265">Lync: Kerberos, TLS-DSK, or NTLM authentication.</span></span> <span data-ttu-id="c47a4-266">Lync 클라이언트 트래픽은 Lync VIP (부하 분산 장치/역방향 프록시 서버)로 이동한 다음 Lync Server로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-266">The Lync client traffic goes to the Lync VIP (load balancer/reverse proxy server), and then to the Lync Server.</span></span> 
    
- <span data-ttu-id="c47a4-267">SharePoint: AD DS (Active Directory 도메인 서비스), 폼 기반 인증 또는 SAML 인증을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-267">SharePoint: Active Directory Domain Services (AD DS), forms-based authentication, or SAML authentication.</span></span> <span data-ttu-id="c47a4-268">Sharepoint 클라이언트 트래픽은 SharePoint VIP (부하 분산/역방향 프록시 서버)로 이동한 다음 SharePoint 서버로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-268">The SharePoint client traffic goes to the SharePoint VIP (load balancer/reverse proxy server), and then to the SharePoint Server.</span></span> 
    
- <span data-ttu-id="c47a4-269">Exchange: AD DS, 폼 기반 인증</span><span class="sxs-lookup"><span data-stu-id="c47a4-269">Exchange: AD DS, forms-based authentication.</span></span> <span data-ttu-id="c47a4-270">Exchange 클라이언트 트래픽은 Exchange VIP (부하 분산 장치/역방향 프록시 서버)로 이동한 다음 Exchange 서버로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-270">The Exchange client traffic goes to the Exchange VIP (load balancer/reverse proxy server), and then to the Exchange Server.</span></span> 
    
- <span data-ttu-id="c47a4-271">Lync 클라이언트 트래픽은 HTTPS 트래픽에 필요한 하드웨어 부하 분산 장치에 대 한 Lync VIP (부하 분산 장치/역방향 프록시 서버)로 이동한 다음 Lync Server로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-271">Lync client traffic goes to the Lync VIP (load balancer/reverse proxy server) to a hardware load balancer, which is required for HTTPS traffic, and then to the Lync Server.</span></span> 
    
#### <a name="cloud-based-email-traffic"></a><span data-ttu-id="c47a4-272">클라우드 기반 전자 메일 트래픽</span><span class="sxs-lookup"><span data-stu-id="c47a4-272">Cloud-based email traffic</span></span>

<span data-ttu-id="c47a4-273">SMTP 기반 전자 메일 트래픽에 사용 되는 클라우드 기반 구성 요소는 인터넷 메일 호스트 또는 Exchange Online Protection으로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-273">The cloud-based component for SMTP-based email traffic consists of either Internet Mail Hosts or Exchange Online Protection.</span></span>
  
<span data-ttu-id="c47a4-274">이러한 구성 요소는 SMTP를 사용 하 여 네트워크를 통해 전자 메일 트래픽을 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-274">These components move email traffic over the network using SMTP.</span></span> <span data-ttu-id="c47a4-275">트래픽이 게이트웨이 라우터를 통해 Exchange VIP (부하 분산 장치/역방향 프록시 서버)로 이동한 다음 Exchange 서버로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-275">The traffic goes through the Gateway router to the Exchange VIP (load balancer/reverse proxy server), and then to the Exchange Server.</span></span> 
  
### <a name="network-traffic-legend"></a><span data-ttu-id="c47a4-276">네트워크 트래픽 범례</span><span class="sxs-lookup"><span data-stu-id="c47a4-276">Network traffic legend</span></span>

<span data-ttu-id="c47a4-277">범례 상자에는 그래프에 표시 되는 다양 한 유형의 트래픽이 다음과 같이 서로 다른 색상의 선으로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-277">The legend box graphically shows the different types of traffic depicted on the graph in different colored lines as follows:</span></span> 
  
- <span data-ttu-id="c47a4-278">녹색 줄: Lync SIP 트래픽</span><span class="sxs-lookup"><span data-stu-id="c47a4-278">Green line: Lync SIP traffic</span></span> 
    
- <span data-ttu-id="c47a4-279">파란 선: Lync 웹 트래픽</span><span class="sxs-lookup"><span data-stu-id="c47a4-279">Blue line: Lync Web traffic</span></span> 
    
- <span data-ttu-id="c47a4-280">자주색 줄: SharePoint 클라이언트 트래픽</span><span class="sxs-lookup"><span data-stu-id="c47a4-280">Purple line: SharePoint client traffic</span></span> 
    
- <span data-ttu-id="c47a4-281">주황색 줄: Exchange 클라이언트 트래픽</span><span class="sxs-lookup"><span data-stu-id="c47a4-281">Orange line: Exchange client traffic</span></span> 
    
- <span data-ttu-id="c47a4-282">회색 줄: exchange 온-프레미스 및 Exchange Online Protection 간의 Exchange 메일 서버 트래픽</span><span class="sxs-lookup"><span data-stu-id="c47a4-282">Gray line: Exchange Mail Server traffic between Exchange on-premises and Exchange Online Protection.</span></span> 
    
<span data-ttu-id="c47a4-283">각 트래픽 유형 및 사용 하는 포트에 대해서도 범례 상자에 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-283">The different types of traffic and the ports that they use are also described in the legend box.</span></span> 
  
#### <a name="lync-sip-traffic-and-lync-web-traffic"></a><span data-ttu-id="c47a4-284">Lync SIP 트래픽 및 Lync 웹 트래픽</span><span class="sxs-lookup"><span data-stu-id="c47a4-284">Lync SIP traffic and Lync web traffic</span></span>

<span data-ttu-id="c47a4-285">Lync에 지 서버는 외부 사용자 통신에 다음 포트를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-285">The Lync Edge Server uses the following ports for external user communication:</span></span> 
  
- <span data-ttu-id="c47a4-286">신호/IM 트래픽 (SIP/SIMPLE): TCP 포트 443 (인바운드 트래픽에 대해 개방)</span><span class="sxs-lookup"><span data-stu-id="c47a4-286">Signaling/IM traffic (SIP/SIMPLE): TCP port 443 (open for inbound traffic)</span></span> 
    
- <span data-ttu-id="c47a4-287">PSOM (웹 회의 트래픽): TCP 443 (인바운드 트래픽에 대해 열기)</span><span class="sxs-lookup"><span data-stu-id="c47a4-287">Web conferencing traffic (PSOM): TCP 443 (open for inbound traffic)</span></span> 
    
- <span data-ttu-id="c47a4-288">A/V 트래픽 (SRTP): TCP 443, UDP 3478 및 TCP 50000-59999 (선택 사항) (인바운드 및 아웃 바운드 트래픽을 위해 열기)</span><span class="sxs-lookup"><span data-stu-id="c47a4-288">A/V traffic (SRTP): TCP 443, UDP 3478 and TCP 50000-59999 (optional) (open for inbound and outbound traffic)</span></span> 
    
<span data-ttu-id="c47a4-289">Lync에 지 서버는 다음 포트를 사용 하 여 페더레이션 통신을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-289">Lync Edge Server uses the following ports for federation communication:</span></span> 
  
- <span data-ttu-id="c47a4-290">TCP 포트 5061 (SIP), 5269 (XMPP), 443 및 UDP 3478 (SRTP) (인바운드 및 아웃 바운드 트래픽을 위해 열기)</span><span class="sxs-lookup"><span data-stu-id="c47a4-290">TCP ports 5061 (SIP), 5269 (XMPP), 443 and UDP 3478 (SRTP) (open for inbound and outbound traffic)</span></span> 
    
#### <a name="sharepoint-client-traffic"></a><span data-ttu-id="c47a4-291">SharePoint 클라이언트 트래픽</span><span class="sxs-lookup"><span data-stu-id="c47a4-291">SharePoint client traffic</span></span>

<span data-ttu-id="c47a4-292">SharePoint에서는 클라이언트와 부하 분산 장치 간의 암호화 된 통신을 위해 SSL (TCP 포트 443)을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-292">SharePoint can use TCP port 443 (SSL) for encrypted communication between the client and the load balancer.</span></span> <span data-ttu-id="c47a4-293">인터넷에서 외부 액세스를 사용 하는 경우 게이트웨이 라우터 (또는 외부 방화벽)에서 인바운드 및 아웃 바운드 트래픽에 대해이 포트를 열어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-293">For external access from the Internet, this port needs to be opened for inbound and outbound traffic on the gateway router (or external firewall).</span></span> 
  
#### <a name="exchange-client-traffic-and-exchange-mail-server-traffic"></a><span data-ttu-id="c47a4-294">Exchange 클라이언트 트래픽 및 Exchange 메일 서버 트래픽</span><span class="sxs-lookup"><span data-stu-id="c47a4-294">Exchange client traffic and Exchange mail server traffic</span></span>

<span data-ttu-id="c47a4-295">Exchange에서는 서버 간 통신에 TCP 포트 25 (SMTP)를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-295">Exchange uses TCP port 25 (SMTP) for server-to-server communications.</span></span> <span data-ttu-id="c47a4-296">대부분의 클라이언트 트래픽 (OWA, ActiveSync, 자동 검색, Outlook Anywhere)은 포트 443 (HTTPS)를 통해 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-296">Most client traffic (OWA, ActiveSync, Autodiscover, Outlook Anywhere) is handled over port 443 (HTTPS).</span></span> <span data-ttu-id="c47a4-297">POP 또는 IMAP 클라이언트를 사용 하는 경우에는 포트 110 (POP3), 995 (암호화 된 POP3), 143 (IMAP4), 993 (암호화 된 IMAP4) 및 587 (SMTP)도 이러한 클라이언트를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-297">If you have POP or IMAP clients, ports 110 (POP3), 995 (encrypted POP3), 143 (IMAP4), 993 (encrypted IMAP4), and 587 (SMTP) are also used to support these clients.</span></span> 
  
#### <a name="more-on-lync-network-traffic"></a><span data-ttu-id="c47a4-298">Lync 네트워크 트래픽에 대 한 자세한 내용은 무엇입니까?</span><span class="sxs-lookup"><span data-stu-id="c47a4-298">More on Lync network traffic?</span></span>

<span data-ttu-id="c47a4-299">Lync Server를 통해 조직에서 인스턴트 메시징, 웹 회의, 응용 프로그램 공유 및 음성 통신을 제공 하는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-299">Learn how Lync Server can help your organization provide instant messaging, web conferencing, application sharing, and voice communication.</span></span> <span data-ttu-id="c47a4-300">자세한 내용은 [Microsoft Lync Server 2013 프로토콜 워크 로드 포스터](https://aka.ms/G5jzjo)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c47a4-300">For more information, see [Microsoft Lync Server 2013 Protocol Workloads Poster](https://aka.ms/G5jzjo).</span></span> 
  
<span data-ttu-id="c47a4-301">또한 포스터에는이 정보에 액세스할 수 있는 QR 코드가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c47a4-301">The poster also includes a QR code to access this information.</span></span> 
  

