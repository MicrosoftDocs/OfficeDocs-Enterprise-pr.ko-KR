---
title: 액세스할 수 있는 다이어그램-네트워크 통합의 Microsoft Office 서버 제품
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 89f564eb-95c3-4077-bb92-75bf71b51270
description: 이 문서에는 네트워크 통합의 Microsoft Office 서버 제품 라는 다이어그램의 액세스할 수 있는 텍스트 버전입니다.
ms.openlocfilehash: 3fa27b99bf0babf00c536057b9d21da784b6d94f
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/09/2018
ms.locfileid: "17504431"
---
# <a name="accessible-diagram---network-integration-of-microsoft-office-server-products"></a><span data-ttu-id="bc9a7-103">액세스할 수 있는 다이어그램-네트워크 통합의 Microsoft Office 서버 제품</span><span class="sxs-lookup"><span data-stu-id="bc9a7-103">Accessible diagram - Network Integration of Microsoft Office Server Products</span></span>

<span data-ttu-id="bc9a7-104">**요약:** 이 문서에는 네트워크 통합의 Microsoft Office 서버 제품 라는 다이어그램의 액세스할 수 있는 텍스트 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-104">**Summary:** This article is an accessible text version of the diagram named Network Integration of Microsoft Office Server Products.</span></span>
  
<span data-ttu-id="bc9a7-p101">이 포스터에는 Lync Server 2013, SharePoint 2013 및 Exchange Server 2013을 포함 하는 네트워크 환경에 대 한 일반적인 설명을 제공 합니다. 또한 이러한 제품에서 공통 되는 다음과 같은 네트워킹 요소에 설명: 내부 및 원격 액세스, 인증, 클라이언트 트래픽 및 공유 장치를 통해 트래픽 라우팅.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-p101">This poster provides a general illustration of a network environment that includes Lync Server 2013, SharePoint 2013, and Exchange Server 2013. It also illustrates the following networking elements that are common across these products: remote and internal access, authentication, client traffic, and routing traffic through shared devices.</span></span> 
  
## <a name="high-level-concepts-for-lync-exchange-sharepoint-server-and-office-web-apps"></a><span data-ttu-id="bc9a7-107">Lync, Exchange, SharePoint Server 및 Office Web Apps에 대 한 높은 수준의 개념</span><span class="sxs-lookup"><span data-stu-id="bc9a7-107">High-level concepts for Lync, Exchange, SharePoint Server, and Office Web Apps</span></span>

### <a name="about-the-design"></a><span data-ttu-id="bc9a7-108">디자인 하는 방법에 대 한</span><span class="sxs-lookup"><span data-stu-id="bc9a7-108">About the design</span></span>

#### <a name="streamlined-network-design"></a><span data-ttu-id="bc9a7-109">효율적인된 네트워크 디자인</span><span class="sxs-lookup"><span data-stu-id="bc9a7-109">Streamlined network design</span></span>

<span data-ttu-id="bc9a7-p102">이 토폴로지는 SharePoint 2013, Exchange Server 2013 및 Lync Server 2013의 온-프레미스 네트워크 배포를 보여줍니다. 또한 Microsoft 클라우드 기반 서비스를 인터넷에서 인바운드 SMTP Simple Mail Transfer Protocol () 트래픽에 대 한 스팸 및 맬웨어로부터 보호를 제공 하는 Exchange Online Protection의 사용을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-p102">This topology illustrates an on-premises network deployment of SharePoint 2013, Exchange Server 2013, and Lync Server 2013. It also shows the use of the Microsoft cloud-based service, Exchange Online Protection, which provides spam and malware protection for inbound Simple Mail Transfer Protocol (SMTP) traffic from the Internet.</span></span> 
  
<span data-ttu-id="bc9a7-p103">이 네트워크 디자인 네트워크 기능의 최소 집합을 간소화 됩니다. 계정 추가 보안 또는 인프라 기능으로 일부 조직에서는 필요할 수 있는 디자인 고려 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-p103">This network design is streamlined to a minimum set of network features. The design does not take into account additional security or infrastructure features that some organizations might require.</span></span> 
  
<span data-ttu-id="bc9a7-114">이 다이어그램:</span><span class="sxs-lookup"><span data-stu-id="bc9a7-114">This diagram:</span></span> 
  
- <span data-ttu-id="bc9a7-115">게이트웨이 라우터 및 클라이언트 세션 트래픽 (외부 및 내부)를 적절 한 SharePoint, Exchange 및 Lync server 계층의 부하 분산을 통해 인바운드 및 아웃 바운드 트래픽을 설명 네트워크 토폴로지 예를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-115">Provides an example network topology illustrating inbound and outbound traffic through a gateway router and load balancing of client session traffic (external and internal) to the appropriate SharePoint, Exchange, and Lync server tiers.</span></span> 
    
- <span data-ttu-id="bc9a7-116">제 3 자가 VPN 게이트웨이 또는 로밍 또는 원격 직원에 대 한 보안 통신을 제공 하려면 DirectAccess 서버와 같은 선택적인 원격 액세스 서버 사용을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-116">Shows the use of optional remote access servers, such as a third-party VPN gateway or DirectAccess server, to provide secure communication for roaming or remote employees.</span></span> 
    
- <span data-ttu-id="bc9a7-117">SharePoint, Exchange 및 Lync 트래픽 흐름 클라이언트에서 각 플랫폼 서버 계층에 자세히 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-117">Details the SharePoint, Exchange, and Lync traffic flow from the client to each platform server tier.</span></span> 
    
- <span data-ttu-id="bc9a7-118">클라이언트 (예: 파트너 또는 직원) 및 사용 하는 인증 방법에 따라 원격 또는 내부 액세스 연결의 형식을 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-118">Identifies the type of remote or internal access connection based on client (such as partner or employee), and the authentication method used.</span></span> 
    
- <span data-ttu-id="bc9a7-119">필요한 서버 역할, 프런트엔드, 응용 프로그램, 데이터베이스 및 기타 수준을 식별 하 여 SharePoint, Exchange 및 Lync 플랫폼을 나눕니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-119">Breaks down the SharePoint, Exchange, and Lync platforms by required server roles, identifying the front end, application, database, and other levels.</span></span> 
    
<span data-ttu-id="bc9a7-p104">Sharepoint, Lync, 여기서 사용 되는 아키텍처 및 Exchange 이러한 플랫폼을 구현 하는 기본 방법을 제안 하지 않습니다. 단순히 토폴로지를 고유한 네트워크 요구 사항 및 보안 고려 사항에 따라 다르게 예를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-p104">The architecture used here for SharePoint, Lync, and Exchange does not suggest a preferred way of implementing these platforms. It merely provides an example as topologies differ based on unique network requirements and security considerations.</span></span> 
  
#### <a name="gateway-router"></a><span data-ttu-id="bc9a7-122">게이트웨이 라우터</span><span class="sxs-lookup"><span data-stu-id="bc9a7-122">Gateway router</span></span>

<span data-ttu-id="bc9a7-p105">이 토폴로지에 대 한 게이트웨이 라우터는 네트워크의 가장자리에 배치 된 위치의 및 인트라넷에서 들어오고 나가는 모든 트래픽을 라우팅합니다. 또는 있을 수 게이트웨이 라우터 및 방화벽의 여러 계층 예: 표시 된 부하 분산 장치 간의 간격을 브리지 하는 다른 구성 요소입니다. 이 토폴로지는 많은 로그 아웃 네트워크를 배포 하는 방법을 하나를 나타냅니다. 이 구성에는 게이트웨이 트래픽을 허용 하기 위해 매우 특정 들어오고 나가는 IP 기반 라우터 인터페이스에 대 한 액세스 제어 목록 (Acl)로 구성 됩니다. Acl, 고급 검사, 또는 네트워크 주소 변환 (NAT)도 네트워크를 통해 방화벽 같은 다른 장치에서 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-p105">For this topology, the gateway router sits at the edge of the network and routes all incoming and outgoing traffic to and from the intranet. Alternatively, there could also be other components that bridge the gap between the gateway router and the load balancer shown, such as multiple layers of firewalls. This topology represents just one way to deploy your network out of many. In this configuration, the gateway is configured with access control lists (ACLs) to permit very specific incoming and outgoing IP-based traffic on the router interfaces. ACLs, advanced inspection, or Network Address Translation (NAT) can also be performed on other devices, such as firewalls, throughout your network.</span></span> 
  
#### <a name="load-balancer-and-reverse-proxy-devices"></a><span data-ttu-id="bc9a7-128">부하 분산 장치 및 역방향 프록시 장치</span><span class="sxs-lookup"><span data-stu-id="bc9a7-128">Load balancer and reverse proxy devices</span></span>

<span data-ttu-id="bc9a7-p106">SharePoint 프런트엔드 웹 서버 및 Exchange 클라이언트 액세스 서버 (클래스)를 포함 하 여 세그먼트에 대 한 트래픽을 리디렉션하려면 하드웨어 또는 소프트웨어 부하 분산 솔루션을 사용할 수 있습니다. 경우에 따라 쿠키 또는 머리글 같은 요청에 정보를 사용 하 여 더 뛰어난 성능을 낼 수 대로 지 속성 요구 사항에 대 한 계층 7 하드웨어 기반 부하 분산 장치를 사용 하 여 최적의 됩니다. 그러나 비용 및 증가 된 사용률 같은 요소가 및 작업량 이러한 솔루션에서 특정 요구 사항에 대 한 바람직한 교환 조건은 되지 않을 수 있습니다. SharePoint, Exchange 및 Lync를 통해 부하를 분산에 대 한 다음과 같은 사항을 고려 하십시오.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-p106">You can use hardware or software load balancing solutions to redirect traffic for segments including SharePoint front-end web servers and Exchange Client Access Servers (CASs). In some cases it's optimal to use a layer 7 hardware-based load balancer for persistence requirements as it can perform better by using information in the request, such as cookies or headers. However, factors like cost and increased utilization and workload from such a solution might not be desirable for your specific needs. Consider the following points for load balancing across SharePoint, Exchange, and Lync:</span></span> 
  
- <span data-ttu-id="bc9a7-p107">SharePoint 2013에 대 한 SharePoint-하지 필요가 프런트엔드 웹 서버에 대 한 선호도 사용 하도록 설정 합니다. 일반적으로 스티커 세션을 만들고 각 프런트엔드 웹 서버에 클라이언트에서 여러 인증 요청을 방지 하기 위한이 사용 됩니다. SharePoint 2013의 새로운 배포 된 캐시 서비스를 저장 하 고 SharePoint 팜의 웹 서버 간에 로그온 토큰을 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-p107">SharePoint - For SharePoint 2013, you do not need to enable affinity for your front-end web servers. Normally, this would be used for creating sticky sessions and avoiding multiple authentication requests from clients to each front-end web server. The new Distributed Cache service in SharePoint 2013 stores and distributes logon tokens across the web servers of the SharePoint farm.</span></span> 
    
- <span data-ttu-id="bc9a7-p108">Exchange 2013, CAS 역할에서에서 Exchange-전송 계층에서 요청을 배포 하는 layer 4 부하 분산을 사용 하도록 설계 되었습니다. 부하 분산 장치 사용률 및 작업 부하 크게 저하 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-p108">Exchange - In Exchange 2013, the CAS role is designed to use layer 4 load balancing, distributing requests at the transport layer. This can significantly decrease load balancer utilization and workload.</span></span> 
    
- <span data-ttu-id="bc9a7-p109">Lync-Lync 풀에 대 한 프로토콜 SIP (Session Initiation) 트래픽에 대 한 시스템 DNS (Domain Name) 부하 분산은 것이 좋습니다. 하드웨어 부하 분산 (HLB)는 Lync 웹 (HTTPS) 트래픽을 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-p109">Lync - Domain Name System (DNS) load balancing is recommended for Session Initiation Protocol (SIP) traffic for Lync pools. Hardware load balancing (HLB) is required for Lync Web (HTTPS) traffic.</span></span> 
    
### <a name="remote-access-options"></a><span data-ttu-id="bc9a7-140">원격 액세스 옵션</span><span class="sxs-lookup"><span data-stu-id="bc9a7-140">Remote access options</span></span>

<span data-ttu-id="bc9a7-p110">인터넷에서 파트너에 대 한 인트라넷 리소스를 게시 하거나 원격 또는 로밍 직원에 대 한 보안 된 원격 액세스를 제공할 수 있는 여러 옵션이 있습니다. 이러한 예로 역방향 프록시, DirectAccess, 및 제 3 자가 VPN 게이트웨이. 이 섹션의 뒷부분에서 설명 하는 원격 액세스 솔루션은 SharePoint, Lync 및 Exchange에 대 한 가능성 또는 온-프레미스 배포에서 이러한 서버의 조합입니다. 그러나 일부 원격 옵션 특정 솔루션과 함께 작동 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-p110">There are several options that can publish intranet resources for partners on the Internet or provide secure remote access for remote or roaming employees. Such examples include reverse proxies, DirectAccess, and third-party VPN gateways. The remote access solutions discussed later in this section are possibilities for SharePoint, Lync, and Exchange, or any combination of these servers in an on-premises deployment. However, some remote options might not work with a particular solution.</span></span> 
  
<span data-ttu-id="bc9a7-p111">역방향 프록시-역방향 프록시 Secure Sockets Layer (SSL) 등의 트래픽을 암호화를 지원 하 고 인증 된 사용자와 인터넷에서 파트너와 인트라넷 응용 프로그램 및 웹 리소스를 게시할 수 있습니다. Microsoft Forefront Unified Access Gateway (UAG) 그 예가입니다. 많은 하드웨어 부하 분산 장치는 또한 역방향 프록시 기능을 지원합니다. 그러나 요구와 트래픽 격리, 보안 작업 및 성능 최적화 등의 요구 사항에 따라 독립 실행형 솔루션을 사용 하기 위한 여전히 유효한 시나리오가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-p111">Reverse Proxy - A reverse proxy supports traffic encryption, such as Secure Sockets Layer (SSL), and with it you can publish intranet applications and web resources to authenticated users and partners on the Internet. An example is Microsoft Forefront Unified Access Gateway (UAG). Many hardware load balancers also support reverse proxy functionality. However, there are still valid scenarios for using a standalone solution based on your needs and requirements, such as traffic isolation, security compartmentalization, and performance optimization.</span></span> 
  
<span data-ttu-id="bc9a7-149">역방향 프록시 이점 및 고려 사항:</span><span class="sxs-lookup"><span data-stu-id="bc9a7-149">Reverse-proxy benefits and considerations:</span></span> 
  
- <span data-ttu-id="bc9a7-150">파트너 또는 인트라넷 리소스에 액세스 하는 사용자에 대 한 인증 및 보안에 대 한 액세스를 제공 (역방향 프록시 서버와 클라이언트 사이의 SSL (TCP 443)를 사용).</span><span class="sxs-lookup"><span data-stu-id="bc9a7-150">Provides authenticated and secured access for partners or users accessing intranet resources (uses SSL (TCP 443) between the client and reverse proxy server).</span></span> 
    
- <span data-ttu-id="bc9a7-p112">Exchange에 대 한 Forefront UAG 같은 역방향 프록시를 사용 하 여 혜택은 Exchange 클라이언트 액세스 서버에 액세스 하기 전에 사전 인증입니다. 원격 액세스 사용자를 사용 하 여 Outlook Web Access (OWA)에 인증할 수는 기본 NTLM 또는 Kerberos 메서드는 내부 네트워크에 도달 하기 전에 같은 응용 프로그램을 게시 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-p112">For Exchange, a benefit of using a reverse proxy such as Forefront UAG is pre-authentication before accessing the Exchange Client access server. Remote access users using published applications such as Outlook Web Access (OWA) can authenticate with the basic, NTLM, or Kerberos methods before they reach the internal network.</span></span> 
    
- <span data-ttu-id="bc9a7-153">Exchange 및 SharePoint에 대 한 Forefront UAG와 같은 솔루션 SSL 연결을 종료 하 고 인증서에 대 한 관리는 단일 지점을 제공 하는 동안 인트라넷 리소스 서버의 부하를 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-153">For Exchange and SharePoint, solutions like Forefront UAG can terminate SSL connections and decrease the load of the intranet resources server while providing a single point of management for certificates.</span></span> 
    
- <span data-ttu-id="bc9a7-p113">Lync에 대 한 웹 (HTTPS) 트래픽에 대 한 클라이언트 통신에 대 한 역방향 프록시 (TCP 443)를 통해 이동합니다. 역방향 프록시 프록시는 HTTPS Lync 웹 서비스, Exchange CAS 및 Office 웹 응용 프로그램에 연결 합니다. Lync Server 2013 UAG를 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-p113">For Lync, Web (HTTPS) traffic goes through the reverse proxy (TCP 443) for client communication. The reverse proxy proxies the HTTPS connection to Lync Web Services, Exchange CAS, and Office Web Apps. Lync Server 2013 does not support UAG.</span></span> 
    
<span data-ttu-id="bc9a7-p114">DirectAccess-인터넷 프로토콜 보안 (IPsec) 인증을 위해 및 DirectAccess 클라이언트와 서버 간의 트래픽 암호화에 대 한 의존 하는 원격 액세스 기술입니다. DirectAccess 로밍 및 원격 직원에 대 한 연결을 시작 하지 않고도 인터넷 및 인트라넷 모두 리소스에 대 한 동시 액세스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-p114">DirectAccess - A remote access technology that relies on Internet Protocol security (IPsec) for authentication and for encrypting traffic between the DirectAccess client and server. DirectAccess provides simultaneous access to both Internet and intranet resources for roaming and remote employees without having to initiate a connection.</span></span> 
  
<span data-ttu-id="bc9a7-159">DirectAccess 사항을 고려해 야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-159">DirectAccess points to consider:</span></span> 
  
- <span data-ttu-id="bc9a7-160">DirectAccess를 사용 하 여 IPsec로 보호 된 트래픽 (프로토콜 50 및 51 및 UDP 500) DirectAccess 클라이언트와 서버 간의 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-160">DirectAccess uses IPsec protected traffic (protocol 50 and 51 and UDP 500) between the DirectAccess client and server.</span></span> 
    
- <span data-ttu-id="bc9a7-161">Windows Server 2012 DirectAccess 및 Windows 8 서버 및 클라이언트 인증에 대 한 공용 키 인프라 (PKI) 배포가 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-161">DirectAccess for Windows Server 2012 and Windows 8 does not need a public key infrastructure (PKI) deployment for server and client authentication.</span></span> 
    
- <span data-ttu-id="bc9a7-162">Lync Server 2013을 사용한 DirectAccess를 사용 하 여 IPsec 암호화 및 암호 해독와 관련 된 오디오 및 비디오 대기 시간 문제 때문에 대 한 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-162">We recommend against using DirectAccess with Lync Server 2013 because of audio and video latency issues associated with IPsec encryption and decryption.</span></span> 
    
    <span data-ttu-id="bc9a7-p115">VPN 게이트웨이-일반적인 VPN 게이트웨이는 원격 액세스 클라이언트 컴퓨터는 터널링 되 고 사용자가 시작한 연결을 통해 인트라넷에 프로젝트 논리적으로 원격 액세스 연결을 제공 합니다. 로밍 또는 원격 직원용 인트라넷에 대 한 보안된 액세스를 제공 하려면 Windows Server 2012 또는 여러 타사 솔루션에서 원격 액세스 통합을 사용할 수 있습니다. VPN은 Lync에 대 한 권장 되지 않습니다. 원격 Lync 트래픽을에 지 서버를 사용 하 고 터널링 분할 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-p115">VPN Gateway - Typical VPN gateways provide a remote access connection in which a remote access client computer is logically projected onto the intranet through a tunneled and user-initiated connection. You can use Unified Remote Access in Windows Server 2012 or several third-party solutions to provide secured access to the intranet for roaming or remote employees. VPN is not recommended for Lync. Remote Lync traffic should use the Edge Servers and split tunneling.</span></span> 
    
### <a name="domain-name-system-dns-considerations"></a><span data-ttu-id="bc9a7-167">도메인 이름 시스템 (DNS) 고려 사항</span><span class="sxs-lookup"><span data-stu-id="bc9a7-167">Domain Name System (DNS) considerations</span></span>

<span data-ttu-id="bc9a7-168">적절 한 IP 주소로 DNS 이름을 확인 하기 위해 인터넷 및 인트라넷 모두 사용자를 허용 하는 DNS 레코드 집합에 대 한 계획을 세워야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-168">You need to plan for the set of DNS records that allow both Internet and intranet users to resolve DNS names to the appropriate IP addresses.</span></span> 
  
- <span data-ttu-id="bc9a7-169">인터넷 기반 파트너와 로밍 또는 원격 직원에 대 한 DNS 레코드에 등록 된 인터넷 DNS 서버에서 집합에 해당 게이트웨이 라우터, Lync에 지 서버 집합의 가상 IP 주소 (Vip) 하는 공용 IP 주소에는 해상도 제공 부하 분산 장치 하 고 필요에 따라 DirectAccess 또는 VPN 게이트웨이.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-169">For Internet-based partners and roaming or remote employees, DNS records registered with Internet DNS servers provide resolution to the set of public IP addresses corresponding to the gateway router, the Lync Edge Server, the set of virtual IP addresses (VIPs) on the load balancer, and the DirectAccess or VPN gateway as needed.</span></span> 
    
- <span data-ttu-id="bc9a7-170">사용자가 인트라넷 기반 인트라넷 DNS 서버에 등록 하는 DNS 레코드 SharePoint, Lync 및 Exchange 리소스에 대 한 액세스에 대 한 해결 방법의 가상 IP 주소 (Vip) 집합을 부하 분산 장치에 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-170">For intranet-based users, DNS records registered with intranet DNS servers provide resolution to the set of virtual IP addresses (VIPs) on the load balancer for access to SharePoint, Lync, and Exchange resources.</span></span> 
    
- <span data-ttu-id="bc9a7-p116">DirectAccess 클라이언트는 인트라넷 DNS 네임 스페이스 및 하지 않는 이름에 대 한 인터넷 DNS 서버에 해당 하는 이름에 대 한 인트라넷 DNS 서버를 사용 합니다. DirectAccess의 작업을 단순화 하려면 인트라넷 및 인터넷 기반 이름에 대 한 서로 다른 DNS 네임 스페이스를 사용 하는 분할 DNS 구현 사용을 고려 합니다. 예: contoso.com을 사용 하 여 인터넷 네임 스페이스 및 corp.contoso.com 인트라넷 네임 스페이스에 대 한.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-p116">DirectAccess clients use intranet DNS servers for names corresponding to the intranet DNS name space and Internet DNS servers for names that do not. To simplify the operation of DirectAccess, consider the use of a split DNS implementation that uses different DNS namespaces for intranet and Internet-based names. For example, use contoso.com for Internet namespace and corp.contoso.com for the intranet namespace.</span></span> 
    
- <span data-ttu-id="bc9a7-p117">Exchange는 회사 네트워크 내에 있는에서 공개적으로 라우팅된 트래픽 IP 해상도 호스트 다릅니다 여기서 분할 DNS 모델을 사용 합니다. 여기에 최소한 클라이언트 트래픽 용 OWA, 자동 검색, ActiveSync Url에 대 한 DNS 레코드 및 인바운드 메일에 대해 MX 레코드를 포함 하도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-p117">Exchange uses a split DNS model where host to IP resolution differs on publicly routed traffic from that on the corporate network. At a minimum, you need to have DNS records for OWA, Autodiscover, ActiveSync URLs for client traffic, and an MX record for inbound mail.</span></span> 
    
- <span data-ttu-id="bc9a7-176">Exchange Online Protection (EOP)를 사용 하는 경우 MX 레코드 Exchange 팜의 하는 대신 해당 서비스를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-176">If you are using Exchange Online Protection (EOP), your MX record points to that service instead of your Exchange farm.</span></span> 
    
- <span data-ttu-id="bc9a7-177">Exchange에 대 한 공용 DNS에서 TXT 레코드 소유권 증명 해야 하 고를 설정 하는 페더레이션 조직 ID 페더레이션 공유 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-177">For Exchange, you need a proof of ownership TXT record in your public DNS, and a Federation Org ID to set up federated sharing.</span></span> 
    
- <span data-ttu-id="bc9a7-178">원격 액세스 VPN 연결 활성화 되었을 때만 인트라넷 DNS 서버를 사용 하 여 원격 액세스 VPN 클라이언트를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-178">Remote access VPN clients can be configured to use only intranet DNS servers when the remote access VPN connection is active.</span></span> 
    
### <a name="diagram-description"></a><span data-ttu-id="bc9a7-179">다이어그램 설명</span><span class="sxs-lookup"><span data-stu-id="bc9a7-179">Diagram Description</span></span>

<span data-ttu-id="bc9a7-p118">이 다이어그램 게이트웨이 라우터 및 클라이언트 세션 트래픽 (외부 및 내부)를 적절 한 SharePoint, Exchange 및 Lync server 계층의 부하 분산을 통해 인바운드 및 아웃 바운드 트래픽을 설명 네트워크 토폴로지 예를 제공 합니다. 이 다이어그램에 대 한 설명은 두 부분으로 나뉩니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-p118">This diagram provides an example network topology illustrating inbound and outbound traffic through a gateway router and load balancing of client session traffic (external and internal) to the appropriate SharePoint, Exchange, and Lync server tiers. The description of this diagram is divided into two parts:</span></span> 
  
- <span data-ttu-id="bc9a7-182">다이어그램에 표시 된 구성 요소에 대 한 설명</span><span class="sxs-lookup"><span data-stu-id="bc9a7-182">Description of components shown in the diagram</span></span> 
    
- <span data-ttu-id="bc9a7-183">SharePoint, Exchange, Lync 및 Office Web Apps 서버 계층에 트래픽을 구성 요소를 통해 이동 하는 방법에 대 한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-183">Description of how traffic moves through the components to the SharePoint, Exchange, Lync, and Office Web Apps server tiers.</span></span> 
    
#### <a name="description-of-components-shown-in-the-diagram"></a><span data-ttu-id="bc9a7-184">다이어그램에 표시 된 구성 요소에 대 한 설명</span><span class="sxs-lookup"><span data-stu-id="bc9a7-184">Description of components shown in the diagram</span></span>

#### <a name="user-types"></a><span data-ttu-id="bc9a7-185">사용자 유형</span><span class="sxs-lookup"><span data-stu-id="bc9a7-185">User types</span></span>

<span data-ttu-id="bc9a7-186">4 개의 서로 다른 유형의 사용자 사이 있는 외부 네트워크 및 클라우드 서비스 3 내부를 포함 하는:</span><span class="sxs-lookup"><span data-stu-id="bc9a7-186">There are four different types of users, three outside the network and cloud services and one internal, which include:</span></span> 
  
- <span data-ttu-id="bc9a7-187">파트너 회사 (기업 간)-외부</span><span class="sxs-lookup"><span data-stu-id="bc9a7-187">Partner companies (business-to-business)-external</span></span> 
    
- <span data-ttu-id="bc9a7-188">개별 파트너 (SharePoint 및 익명 (Lync))-외부</span><span class="sxs-lookup"><span data-stu-id="bc9a7-188">Individual partners (SharePoint and anonymous (Lync))-external</span></span> 
    
- <span data-ttu-id="bc9a7-189">로밍 및 원격 직원 외부</span><span class="sxs-lookup"><span data-stu-id="bc9a7-189">Roaming and remote employees-external</span></span> 
    
- <span data-ttu-id="bc9a7-190">내부 직원</span><span class="sxs-lookup"><span data-stu-id="bc9a7-190">Internal employees</span></span> 
    
#### <a name="cloud-based-email-traffic"></a><span data-ttu-id="bc9a7-191">클라우드 기반 전자 메일 트래픽</span><span class="sxs-lookup"><span data-stu-id="bc9a7-191">Cloud-based email traffic</span></span>

<span data-ttu-id="bc9a7-192">다음과 같은 구성 요소가 클라우드 기반 SMTP 기반 전자 메일 트래픽의 경우, 인터넷 메일 호스트 또는 Exchange Online 보호 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-192">There is a cloud-based component for SMTP-based email traffic, either Internet Mail Hosts or Exchange Online Protection.</span></span> 
  
#### <a name="authentication-for-external-access"></a><span data-ttu-id="bc9a7-193">외부 액세스에 대 한 인증</span><span class="sxs-lookup"><span data-stu-id="bc9a7-193">Authentication for external access</span></span>

<span data-ttu-id="bc9a7-p119">특정 Lync, SharePoint 및 각 사용자 유형에 대 한 Exchange에 대 한 인증 절차 집합이 있습니다. 이 문서의 뒷부분에 자세히 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-p119">There is a specific set of authentication procedures for Lync, SharePoint, and Exchange for each of the user types. They are described in more detail later in this document.</span></span> 
  
#### <a name="gateway-router-with-acls"></a><span data-ttu-id="bc9a7-196">Acl 사용 하 여 게이트웨이 라우터</span><span class="sxs-lookup"><span data-stu-id="bc9a7-196">Gateway router with ACLs</span></span>

<span data-ttu-id="bc9a7-197">게이트웨이 라우터는 네트워크의 가장자리에 배치 된 위치의 및 인트라넷에서 들어오고 나가는 모든 트래픽을 라우팅합니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-197">The gateway router sits at the edge of the network and routes all incoming and outgoing traffic to and from the intranet.</span></span> 
  
#### <a name="remote-access-servers-for-lync-and-sharepoint"></a><span data-ttu-id="bc9a7-198">Lync 및 SharePoint에 대 한 원격 액세스 서버</span><span class="sxs-lookup"><span data-stu-id="bc9a7-198">Remote access servers for Lync and SharePoint</span></span>

<span data-ttu-id="bc9a7-199">이 토폴로지는 Lync에 지 서버와 SharePoint VPN 게이트웨이 또는 DirectAccess 서버를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-199">This topology includes a Lync Edge server, and a SharePoint VPN gateway or DirectAccess server.</span></span> 
  
#### <a name="load-balancer-and-reverse-proxy-device"></a><span data-ttu-id="bc9a7-200">부하 분산 장치 및 역방향 프록시 장치</span><span class="sxs-lookup"><span data-stu-id="bc9a7-200">Load balancer and reverse proxy device</span></span>

<span data-ttu-id="bc9a7-p120">SharePoint 프런트엔드 웹 서버 및 Exchange 클라이언트 액세스 서버 (클래스)를 포함 하 여 세그먼트에 대 한 트래픽을 리디렉션하려면 하드웨어 또는 소프트웨어 부하 분산 솔루션을 사용할 수 있습니다. 이 토폴로지는 부하 분산 장치에서 Lync VIP, SharePoint VIP 및 Exchange VIP 구성 요소를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-p120">You can use hardware or software load balancing solutions to redirect traffic for segments including SharePoint front-end web servers and Exchange Client Access Servers (CASs). This topology shows Lync VIP, SharePoint VIP, and Exchange VIP components in the load balancer.</span></span> 
  
#### <a name="servers"></a><span data-ttu-id="bc9a7-203">서버</span><span class="sxs-lookup"><span data-stu-id="bc9a7-203">Servers</span></span>

<span data-ttu-id="bc9a7-p121">4 명의 서버가: Lync, SharePoint, Exchange 및 Office Web Apps 서버입니다. 각 서버에는 세 계층 있을 수: 프런트, 클라이언트 액세스 계층, 응용 프로그램 계층 및 데이터베이스/저장소 계층입니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-p121">There are four servers: Lync, SharePoint, Exchange, and Office Web Apps Server. Each server can have three tiers: a front-end, client-access tier, an application tier, and a database/storage tier.</span></span>
  
#### <a name="front-end-client-access-tier"></a><span data-ttu-id="bc9a7-206">프런트엔드, 클라이언트 액세스 계층</span><span class="sxs-lookup"><span data-stu-id="bc9a7-206">Front-end, client-access tier</span></span>

<span data-ttu-id="bc9a7-207">이 계층 4 대의 모든 서버에서 구성 요소에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-207">This tier has components on all four servers:</span></span> 
  
- <span data-ttu-id="bc9a7-p122">Lync 풀 (프런트엔드)입니다. 다이어그램은 두 Lync 데이터베이스를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-p122">Lync pool (front end). The diagram shows two Lync databases.</span></span> 
    
- <span data-ttu-id="bc9a7-p123">SharePoint 프런트엔드 및 분산된 캐시 합니다. 다이어그램 세 SharePoint 데이터베이스를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-p123">SharePoint front end and distributed cache. The diagram shows three SharePoint databases.</span></span> 
    
- <span data-ttu-id="bc9a7-p124">Exchange CAS 합니다. 다이어그램은 두 Exchange 데이터베이스를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-p124">Exchange CAS. The diagram shows two Exchange databases.</span></span> 
    
- <span data-ttu-id="bc9a7-p125">Office Web Apps 서버입니다. 다이어그램은 두 Office 웹 응용 프로그램 데이터베이스를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-p125">Office Web Apps Server. The diagram shows two Office Web Apps databases.</span></span> 
    
#### <a name="application-tier"></a><span data-ttu-id="bc9a7-216">응용 프로그램 계층</span><span class="sxs-lookup"><span data-stu-id="bc9a7-216">Application tier</span></span>

<span data-ttu-id="bc9a7-217">이 계층에는 SharePoint 서버에만 구성 요소:</span><span class="sxs-lookup"><span data-stu-id="bc9a7-217">This tier has components only on the SharePoint server:</span></span> 
  
- <span data-ttu-id="bc9a7-p126">(쿼리, 인덱스, 관리)을 검색 합니다. 다이어그램 세 SharePoint 데이터베이스를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-p126">Search (query, index, admin). The diagram shows three SharePoint databases.</span></span> 
    
- <span data-ttu-id="bc9a7-p127">일괄 처리 합니다. 다이어그램 세 SharePoint 데이터베이스를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-p127">Batch processing. The diagram shows three SharePoint databases.</span></span> 
    
#### <a name="databasestorage-tier"></a><span data-ttu-id="bc9a7-222">데이터베이스/저장소 계층</span><span class="sxs-lookup"><span data-stu-id="bc9a7-222">Database/storage tier</span></span>

<span data-ttu-id="bc9a7-223">이 계층 Lync, SharePoint 및 Exchange 서버에서 구성 요소에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-223">This tier has components on the Lync, SharePoint, and Exchange servers:</span></span> 
  
- <span data-ttu-id="bc9a7-p128">Lync 데이터베이스 (백엔드)입니다. 다이어그램 세 Lync 데이터베이스를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-p128">Lync Database (backend). The diagram shows three Lync databases.</span></span> 
    
- <span data-ttu-id="bc9a7-p129">SharePoint 데이터베이스입니다. 다이어그램 세 SharePoint 데이터베이스를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-p129">SharePoint Database. The diagram shows three SharePoint databases.</span></span> 
    
- <span data-ttu-id="bc9a7-p130">Exchange 사서함 서버입니다. 다이어그램은 두 Exchange 사서함 서버를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-p130">Exchange Mailbox server. The diagram shows two Exchange Mailbox servers.</span></span> 
    
<span data-ttu-id="bc9a7-230">각 SharePoint 서버 역할에 설치 된 구성 요소에 대 한 자세한 내용은 [SharePoint 2013에 대 한 간소화 된 토폴로지](https://aka.ms/Ma5cgk)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-230">For more information about components installed on each of the SharePoint server roles, see [Streamlined Topologies for SharePoint 2013](https://aka.ms/Ma5cgk).</span></span> 
  
#### <a name="description-of-how-traffic-moves-through-the-components-to-the-different-server-tiers"></a><span data-ttu-id="bc9a7-231">다른 서버 계층에 트래픽을 구성 요소를 통해 이동 하는 방법을 설명</span><span class="sxs-lookup"><span data-stu-id="bc9a7-231">Description of how traffic moves through the components to the different server tiers</span></span>

<span data-ttu-id="bc9a7-232">이 섹션에서는 네트워크 토폴로지를 통해 사용자의 요청을 이동 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-232">This section describes how user requests move through the network topology.</span></span> 
  
#### <a name="authentication-and-routing-for-external-access"></a><span data-ttu-id="bc9a7-233">인증 및 외부 액세스에 대 한 라우팅</span><span class="sxs-lookup"><span data-stu-id="bc9a7-233">Authentication and routing for external access</span></span>

<span data-ttu-id="bc9a7-234">서로 다른 세가지 유형의 네트워크 서비스와 클라우드 서비스를 포함 하는 외부 클라이언트에는</span><span class="sxs-lookup"><span data-stu-id="bc9a7-234">There are three different types of clients outside the network and cloud services, which include:</span></span> 
  
- <span data-ttu-id="bc9a7-235">파트너 회사 (기업 간)-외부</span><span class="sxs-lookup"><span data-stu-id="bc9a7-235">Partner companies (business-to-business)-external</span></span> 
    
- <span data-ttu-id="bc9a7-236">개별 파트너 (SharePoint 및 익명 (Lync))-외부</span><span class="sxs-lookup"><span data-stu-id="bc9a7-236">Individual partners (SharePoint and anonymous (Lync))-external</span></span> 
    
- <span data-ttu-id="bc9a7-237">로밍 및 원격 직원 외부</span><span class="sxs-lookup"><span data-stu-id="bc9a7-237">Roaming and remote employees-external</span></span> 
    
<span data-ttu-id="bc9a7-238">인증 및 각 외부 사용자 유형에 대 한 라우팅 프로세스 개별적으로 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-238">The authentication and routing process for each external user type is described individually.</span></span> 
  
#### <a name="partner-companies-business-to-business-httpspartnerwebcontosocom"></a><span data-ttu-id="bc9a7-239">파트너 회사 (-비즈니스) (https://partnerweb.contoso.com)</span><span class="sxs-lookup"><span data-stu-id="bc9a7-239">Partner companies (business-to-business) (https://partnerweb.contoso.com)</span></span>

- <span data-ttu-id="bc9a7-p131">Lync: Skype 및가 AOL 인 공용 IM 연결 (PIC) 다른 조직과 페더레이션 트러스트 합니다. Lync 페더레이션 트래픽 Lync에 지 서버, Lync VIP (부하 분산 장치/역방향 프록시 서버)을 다음 Lync 서버에는 게이트웨이 라우터를 통해 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-p131">Lync: federation trust with other organizations, Skype and Public IM Connectivity (PIC) with AOL. The Lync federation traffic goes through the gateway router to the Lync Edge Server, to the Lync VIP (load balancer/reverse proxy server), and then to the Lync Server.</span></span> 
    
- <span data-ttu-id="bc9a7-p132">SharePoint: SAML 인증을 사용 하는 파트너 id 공급자를 신뢰합니다. SharePoint 클라이언트 트래픽 SharePoint VIP (부하 분산 장치/역방향 프록시 서버) 및 SharePoint Server 게이트웨이 라우터를 통해 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-p132">SharePoint: Trusted partner identity provider with SAML authentication. The SharePoint client traffic goes through the Gateway router to the SharePoint VIP (load balancer/reverse proxy server), and then to the SharePoint Server.</span></span> 
    
- <span data-ttu-id="bc9a7-p133">Exchange: 상호 인증 TLS 메일 트래픽의 경우, 페더레이션 공유에 대 한 SAML 인증 합니다. Exchange 클라이언트 트래픽 Exchange VIP (부하 분산 장치/역방향 프록시 서버) 및 Exchange Server 게이트웨이 라우터를 통해 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-p133">Exchange: Mutual Auth TLS for mail traffic, SAML authentication for Federated Sharing. The Exchange client traffic goes through the Gateway router to the Exchange VIP (load balancer/reverse proxy server), and then to the Exchange Server.</span></span> 
    
- <span data-ttu-id="bc9a7-246">SMTP 트래픽은 게이트웨이 라우터를 통해 및 Exchange VIP (부하 분산 장치/역방향 프록시 서버)를 통해 Exchange 서버에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-246">SMTP traffic goes through the Gateway router and through the Exchange VIP (load balancer/reverse proxy server) to the Exchange server.</span></span> 
    
#### <a name="individual-partners-sharepoint-and-anonymous-lync-httpspartnerwebcontosocom-and-httpsmeetcontosocom"></a><span data-ttu-id="bc9a7-247">개별 파트너 (SharePoint) 및 익명 (Lync) (https://partnerweb.contoso.com 및 https://meet.contoso.com)</span><span class="sxs-lookup"><span data-stu-id="bc9a7-247">Individual partners (SharePoint) and anonymous (Lync) (https://partnerweb.contoso.com and https://meet.contoso.com)</span></span>

- <span data-ttu-id="bc9a7-p134">Lync: 익명 사용자가 직원 별로 Lync 모임에만 참가할 수 있습니다. Lync 페더레이션 트래픽 Lync에 지 서버, Lync VIP (부하 분산 장치/역방향 프록시 서버)을 다음 Lync 서버에는 게이트웨이 라우터를 통해 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-p134">Lync: anonymous users can only join Lync meetings organized by employees. The Lync federation traffic goes through the Gateway router to the Lync Edge Server, to the Lync VIP (load balancer/reverse proxy server), and then to the Lync Server.</span></span> 
    
- <span data-ttu-id="bc9a7-p135">신뢰할 수 있는 파트너 id 공급자를 SharePoint: SAML 인증 나 양식 기반 인증을 사용 합니다. SharePoint 클라이언트 트래픽 SharePoint VIP (부하 분산 장치/역방향 프록시 서버) 및 SharePoint Server 게이트웨이 라우터를 통해 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-p135">SharePoint: Trusted partner identity provider with SAML authentication or forms-based authentication. The SharePoint client traffic goes through the Gateway router to the SharePoint VIP (load balancer/reverse proxy server), and then to the SharePoint Server.</span></span> 
    
- <span data-ttu-id="bc9a7-252">Exchange: 적용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-252">Exchange: Does not apply.</span></span> 
    
- <span data-ttu-id="bc9a7-253">Lync 웹 트래픽 HTTPS 트래픽에 대 한 요구 되는 하드웨어 부하 분산 장치를 한 다음 Lync Server 게이트웨이 라우터를 통해 Lync VIP (부하 분산 장치/역방향 프록시 서버)에 Lync에 지 서버로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-253">Lync Web traffic goes through the Gateway router to the Lync Edge Server, to the Lync VIP (load balancer/reverse proxy server), to a hardware load balancer, which is required for HTTPS traffic, and then to the Lync Server.</span></span> 
    
#### <a name="roaming-and-remote-employees"></a><span data-ttu-id="bc9a7-254">로밍 및 원격 직원</span><span class="sxs-lookup"><span data-stu-id="bc9a7-254">Roaming and remote employees</span></span>

1. <span data-ttu-id="bc9a7-255">https://intranet.contoso.com</span><span class="sxs-lookup"><span data-stu-id="bc9a7-255">https://intranet.contoso.com</span></span> 
    
2. <span data-ttu-id="bc9a7-256">https://teams.contoso.com</span><span class="sxs-lookup"><span data-stu-id="bc9a7-256">https://teams.contoso.com</span></span> 
    
3. <span data-ttu-id="bc9a7-257">https://my.contoso.com</span><span class="sxs-lookup"><span data-stu-id="bc9a7-257">https://my.contoso.com</span></span>
    
4. <span data-ttu-id="bc9a7-258">https://partnerweb.contoso.com</span><span class="sxs-lookup"><span data-stu-id="bc9a7-258">https://partnerweb.contoso.com</span></span> 
    
5. <span data-ttu-id="bc9a7-259">https://mail.contoso.com \*</span><span class="sxs-lookup"><span data-stu-id="bc9a7-259">https://mail.contoso.com\*</span></span> 
    
6. <span data-ttu-id="bc9a7-260">https://dial.contoso.com \*</span><span class="sxs-lookup"><span data-stu-id="bc9a7-260">https://dial.contoso.com\*</span></span>
    
7. <span data-ttu-id="bc9a7-261">https://meet.contoso.com \*</span><span class="sxs-lookup"><span data-stu-id="bc9a7-261">https://meet.contoso.com\*</span></span>
    
* <span data-ttu-id="bc9a7-262">다음 가상 디렉터리에 하는 Exchange URL: 자동 검색, ecp, EWS, Microsoft-서버-ActiveSync, OAB, owa, PowerShell</span><span class="sxs-lookup"><span data-stu-id="bc9a7-262">The Exchange URL has the following virtual directories: Autodiscover, ecp, EWS, Microsoft-Server-ActiveSync, OAB, owa, PowerShell</span></span> 
  
- <span data-ttu-id="bc9a7-p136">Lync: TLS DSK 또는 NTLM 인증 합니다. Lync 클라이언트 트래픽 Lync에 지 서버, Lync VIP (부하 분산 장치/역방향 프록시 서버)을 다음 Lync 서버에는 게이트웨이 라우터를 통해 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-p136">Lync: TLS-DSK or NTLM authentication. The Lync client traffic goes through the Gateway router to the Lync Edge Server, to the Lync VIP (load balancer/reverse proxy server), and then to the Lync Server.</span></span> 
    
- <span data-ttu-id="bc9a7-p137">SharePoint: Active Directory 도메인 서비스 (AD DS), 폼 기반 인증 또는 SAML 인증 합니다. SharePoint 클라이언트 트래픽은 VPN 게이트웨이 또는 DirectAccess 서버를 통해 SharePoint VIP (부하 분산 장치/역방향 프록시 서버) 및 SharePoint server 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-p137">SharePoint: Active Directory Domain Services (AD DS), forms-based authentication, or SAML authentication. The SharePoint client traffic goes through the VPN gateway or the DirectAccess server to the SharePoint VIP (load balancer/reverse proxy server), and then to the SharePoint server.</span></span> 
    
- <span data-ttu-id="bc9a7-p138">Exchange: SSL (ActiveSync, 자동 검색), 폼 기반 인증 (OWA)를 통한 기본 인증 합니다. Exchange 클라이언트 트래픽 Exchange VIP (부하 분산 장치/역방향 프록시 서버) 및 Exchange Server 게이트웨이 라우터를 통해 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-p138">Exchange: Basic authentication over SSL (ActiveSync, Autodiscover), forms-based authentication (OWA). The Exchange client traffic goes through the Gateway router to the Exchange VIP (load balancer/reverse proxy server), and then to the Exchange Server.</span></span> 
    
- <span data-ttu-id="bc9a7-269">Lync 클라이언트 트래픽 Lync VIP (부하 분산 장치/역방향 프록시 서버)가 필요한 HTTPS 트래픽에 하드웨어 부하 분산을 한 다음 Lync Server 게이트웨이 라우터를 통해 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-269">Lync client traffic goes through the Gateway router to the Lync VIP (load balancer/reverse proxy server) to a hardware load balancer, which is required for HTTPS traffic, and then to the Lync Server.</span></span> 
    
#### <a name="authentication-for-internal-access"></a><span data-ttu-id="bc9a7-270">내부 액세스에 대 한 인증</span><span class="sxs-lookup"><span data-stu-id="bc9a7-270">Authentication for internal access</span></span>

#### <a name="internal-employees"></a><span data-ttu-id="bc9a7-271">내부 직원</span><span class="sxs-lookup"><span data-stu-id="bc9a7-271">Internal employees</span></span>

> <span data-ttu-id="bc9a7-272">https://intranet.contoso.com</span><span class="sxs-lookup"><span data-stu-id="bc9a7-272">https://intranet.contoso.com</span></span> 
    
> <span data-ttu-id="bc9a7-273">https://teams.contoso.com</span><span class="sxs-lookup"><span data-stu-id="bc9a7-273">https://teams.contoso.com</span></span> 
    
> <span data-ttu-id="bc9a7-274">https://my.contoso.com</span><span class="sxs-lookup"><span data-stu-id="bc9a7-274">https://my.contoso.com</span></span>
    
> <span data-ttu-id="bc9a7-275">https://partnerweb.contoso.com</span><span class="sxs-lookup"><span data-stu-id="bc9a7-275">https://partnerweb.contoso.com</span></span>
    
> <span data-ttu-id="bc9a7-276">https://mail.contoso.com \*</span><span class="sxs-lookup"><span data-stu-id="bc9a7-276">https://mail.contoso.com\*</span></span> 
    
> <span data-ttu-id="bc9a7-277">https://dial.contoso.com</span><span class="sxs-lookup"><span data-stu-id="bc9a7-277">https://dial.contoso.com</span></span> 
    
> <span data-ttu-id="bc9a7-278">https://meet.contoso.com</span><span class="sxs-lookup"><span data-stu-id="bc9a7-278">https://meet.contoso.com</span></span>
    
> <span data-ttu-id="bc9a7-279">https://admin.contoso.com</span><span class="sxs-lookup"><span data-stu-id="bc9a7-279">https://admin.contoso.com</span></span>
    
- <span data-ttu-id="bc9a7-p139">Lync: Kerberos, TLS-DSK 또는 NTLM 인증 합니다. Lync 클라이언트 트래픽은 Lync VIP (부하 분산 장치/역방향 프록시 서버) 한 다음 Lync Server 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-p139">Lync: Kerberos, TLS-DSK, or NTLM authentication. The Lync client traffic goes to the Lync VIP (load balancer/reverse proxy server), and then to the Lync Server.</span></span> 
    
- <span data-ttu-id="bc9a7-p140">SharePoint: Active Directory 도메인 서비스 (AD DS), 폼 기반 인증 또는 SAML 인증 합니다. SharePoint 클라이언트 트래픽은 SharePoint VIP (부하 분산 장치/역방향 프록시 서버) 및 SharePoint Server 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-p140">SharePoint: Active Directory Domain Services (AD DS), forms-based authentication, or SAML authentication. The SharePoint client traffic goes to the SharePoint VIP (load balancer/reverse proxy server), and then to the SharePoint Server.</span></span> 
    
- <span data-ttu-id="bc9a7-p141">Exchange: AD DS, 폼 기반 인증 합니다. Exchange 클라이언트 트래픽은 Exchange VIP (부하 분산 장치/역방향 프록시 서버) 및 Exchange Server 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-p141">Exchange: AD DS, forms-based authentication. The Exchange client traffic goes to the Exchange VIP (load balancer/reverse proxy server), and then to the Exchange Server.</span></span> 
    
- <span data-ttu-id="bc9a7-286">Lync 클라이언트 트래픽 Lync VIP (부하 분산 장치/역방향 프록시 서버)가 필요한 HTTPS 트래픽에 하드웨어 부하 분산을 한 다음 Lync Server로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-286">Lync client traffic goes to the Lync VIP (load balancer/reverse proxy server) to a hardware load balancer, which is required for HTTPS traffic, and then to the Lync Server.</span></span> 
    
#### <a name="cloud-based-email-traffic"></a><span data-ttu-id="bc9a7-287">클라우드 기반 전자 메일 트래픽</span><span class="sxs-lookup"><span data-stu-id="bc9a7-287">Cloud-based email traffic</span></span>

<span data-ttu-id="bc9a7-288">인터넷 메일 호스트 또는 Exchange Online Protection의 SMTP 기반 전자 메일 트래픽에 클라우드 기반 구성 요소 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-288">The cloud-based component for SMTP-based email traffic consists of either Internet Mail Hosts or Exchange Online Protection.</span></span>
  
<span data-ttu-id="bc9a7-p142">이러한 구성 요소는 SMTP를 사용 하 여 네트워크를 통해 전자 메일 트래픽을 이동 합니다. 트래픽을은 Exchange VIP (부하 분산 장치/역방향 프록시 서버) 및 Exchange Server 게이트웨이 라우터를 통해 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-p142">These components move email traffic over the network using SMTP. The traffic goes through the Gateway router to the Exchange VIP (load balancer/reverse proxy server), and then to the Exchange Server.</span></span> 
  
### <a name="network-traffic-legend"></a><span data-ttu-id="bc9a7-291">네트워크 트래픽 범례</span><span class="sxs-lookup"><span data-stu-id="bc9a7-291">Network traffic legend</span></span>

<span data-ttu-id="bc9a7-292">범례 상자는 다양 한 유형의 다음과 같이 서로 다른 색이 지정 된 줄의 그래프에서 설명 하는 트래픽 그래픽으로 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-292">The legend box graphically shows the different types of traffic depicted on the graph in different colored lines as follows:</span></span> 
  
- <span data-ttu-id="bc9a7-293">선 녹색: Lync SIP 트래픽</span><span class="sxs-lookup"><span data-stu-id="bc9a7-293">Green line: Lync SIP traffic</span></span> 
    
- <span data-ttu-id="bc9a7-294">선 파랑: Lync 웹 트래픽</span><span class="sxs-lookup"><span data-stu-id="bc9a7-294">Blue line: Lync Web traffic</span></span> 
    
- <span data-ttu-id="bc9a7-295">선 보라색: SharePoint 클라이언트 트래픽</span><span class="sxs-lookup"><span data-stu-id="bc9a7-295">Purple line: SharePoint client traffic</span></span> 
    
- <span data-ttu-id="bc9a7-296">주황색 줄: Exchange 클라이언트 트래픽</span><span class="sxs-lookup"><span data-stu-id="bc9a7-296">Orange line: Exchange client traffic</span></span> 
    
- <span data-ttu-id="bc9a7-297">선 회색으로 표시: Exchange 온-프레미스 및 Exchange Online Protection 간에 Exchange 메일 서버 트래픽입니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-297">Gray line: Exchange Mail Server traffic between Exchange on-premises and Exchange Online Protection.</span></span> 
    
<span data-ttu-id="bc9a7-298">다양 한 유형의 트래픽 및 사용 하는 포트를 범례 상자도 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-298">The different types of traffic and the ports that they use are also described in the legend box.</span></span> 
  
#### <a name="lync-sip-traffic-and-lync-web-traffic"></a><span data-ttu-id="bc9a7-299">Lync SIP 트래픽 및 Lync 웹 트래픽</span><span class="sxs-lookup"><span data-stu-id="bc9a7-299">Lync SIP traffic and Lync web traffic</span></span>

<span data-ttu-id="bc9a7-300">Lync에 지 서버 외부 사용자 통신을 위한 다음 포트를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-300">The Lync Edge Server uses the following ports for external user communication:</span></span> 
  
- <span data-ttu-id="bc9a7-301">IM 신호 트래픽 (SIP/단순): TCP 포트 443 (인바운드 트래픽에 대 한 개방 됨)</span><span class="sxs-lookup"><span data-stu-id="bc9a7-301">Signaling/IM traffic (SIP/SIMPLE): TCP port 443 (open for inbound traffic)</span></span> 
    
- <span data-ttu-id="bc9a7-302">웹 회의 트래픽 (PSOM): TCP 443 (인바운드 트래픽에 대 한 개방 됨)</span><span class="sxs-lookup"><span data-stu-id="bc9a7-302">Web conferencing traffic (PSOM): TCP 443 (open for inbound traffic)</span></span> 
    
- <span data-ttu-id="bc9a7-303">A / V 트래픽을 (SRTP): TCP 443, UDP 3478 및 TCP 50000-59999 (선택 사항) (인바운드 및 아웃 바운드 트래픽에 대 한 개방 됨)</span><span class="sxs-lookup"><span data-stu-id="bc9a7-303">A/V traffic (SRTP): TCP 443, UDP 3478 and TCP 50000-59999 (optional) (open for inbound and outbound traffic)</span></span> 
    
<span data-ttu-id="bc9a7-304">Lync에 지 서버 페더레이션 통신을 위한 다음 포트를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-304">Lync Edge Server uses the following ports for federation communication:</span></span> 
  
- <span data-ttu-id="bc9a7-305">TCP 포트 5061 (SIP) 5269 (XMPP) 443 및 UDP 3478 (SRTP) (인바운드 및 아웃 바운드 트래픽에 대 한 개방 됨)</span><span class="sxs-lookup"><span data-stu-id="bc9a7-305">TCP ports 5061 (SIP), 5269 (XMPP), 443 and UDP 3478 (SRTP) (open for inbound and outbound traffic)</span></span> 
    
#### <a name="sharepoint-client-traffic"></a><span data-ttu-id="bc9a7-306">SharePoint 클라이언트 트래픽</span><span class="sxs-lookup"><span data-stu-id="bc9a7-306">SharePoint client traffic</span></span>

<span data-ttu-id="bc9a7-p143">SharePoint은 클라이언트 및 부하 분산 장치 간의 암호화 된 통신을 위해 TCP 포트 443 (SSL)를 사용할 수 있습니다. 이 포트는 인터넷에서 외부 액세스에 대 한 게이트웨이 라우터 (또는 외부 방화벽)에서 인바운드 및 아웃 바운드 트래픽에 대 한 열 수를 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-p143">SharePoint can use TCP port 443 (SSL) for encrypted communication between the client and the load balancer. For external access from the Internet, this port needs to be opened for inbound and outbound traffic on the gateway router (or external firewall).</span></span> 
  
#### <a name="exchange-client-traffic-and-exchange-mail-server-traffic"></a><span data-ttu-id="bc9a7-309">클라이언트 트래픽 exchange 및 Exchange 메일 서버 트래픽</span><span class="sxs-lookup"><span data-stu-id="bc9a7-309">Exchange client traffic and Exchange mail server traffic</span></span>

<span data-ttu-id="bc9a7-p144">Exchange 서버-서버 통신을 위해 TCP 포트 25 (SMTP)을 사용합니다. 클라이언트 트래픽 (OWA, ActiveSync, 자동 검색, 외부에서 Outlook 사용) 대부분은 포트 443 (HTTPS)을 통해 처리 됩니다. POP 또는 IMAP 클라이언트를 사용 하는 경우 이러한 클라이언트를 지원 하기 위해 포트 110 (POP3), 995 (암호화 된 POP3), 143 (IMAP4), 993 (암호화 된 IMAP4) 및 587 (SMTP)도 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-p144">Exchange uses TCP port 25 (SMTP) for server-to-server communications. Most client traffic (OWA, ActiveSync, Autodiscover, Outlook Anywhere) is handled over port 443 (HTTPS). If you have POP or IMAP clients, ports 110 (POP3), 995 (encrypted POP3), 143 (IMAP4), 993 (encrypted IMAP4), and 587 (SMTP) are also used to support these clients.</span></span> 
  
#### <a name="more-on-lync-network-traffic"></a><span data-ttu-id="bc9a7-313">더 많은 Lync 네트워크 트래픽을?</span><span class="sxs-lookup"><span data-stu-id="bc9a7-313">More on Lync network traffic?</span></span>

<span data-ttu-id="bc9a7-p145">Lync Server를 통해 방법을 보려면 인스턴트 메시징, 웹 회의 응용 프로그램 공유 및 음성 통신을 제공 하 여 조직에 알아봅니다. 자세한 내용은 [Microsoft Lync Server 2013 프로토콜 작업 포스터](https://aka.ms/G5jzjo)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-p145">Learn how Lync Server can help your organization provide instant messaging, web conferencing, application sharing, and voice communication. For more information, see [Microsoft Lync Server 2013 Protocol Workloads Poster](https://aka.ms/G5jzjo).</span></span> 
  
<span data-ttu-id="bc9a7-316">포스터에는이 정보에 액세스 하기 위해 QR 코드를 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bc9a7-316">The poster also includes a QR code to access this information.</span></span> 
  

