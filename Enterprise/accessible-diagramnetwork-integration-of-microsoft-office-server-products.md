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
description: 이 문서는 Microsoft Office Server 제품의 Network Integration 이라는 다이어그램의 액세스 가능한 텍스트 버전입니다.
ms.openlocfilehash: d63b3b581a03840676393657d6ed641e11046ef9
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068564"
---
# <a name="accessible-diagram---network-integration-of-microsoft-office-server-products"></a>액세스 가능한 다이어그램-Microsoft Office Server 제품의 네트워크 통합

**요약:** 이 문서는 Microsoft Office Server 제품의 Network Integration 이라는 다이어그램의 액세스 가능한 텍스트 버전입니다.
  
이 포스터는 Lync Server 2013, SharePoint 2013 및 Exchange Server 2013이 포함 된 네트워크 환경에 대 한 일반적인 그림을 제공 합니다. 또한이 제품은 원격 및 내부 액세스, 인증, 클라이언트 트래픽 및 공유 장치를 통한 라우팅 트래픽 등에서 공통적으로 사용 되는 다음과 같은 네트워킹 요소를 보여줍니다. 
  
## <a name="high-level-concepts-for-lync-exchange-sharepoint-server-and-office-web-apps"></a>Lync, Exchange, SharePoint Server 및 Office Web Apps에 대 한 높은 수준의 개념

### <a name="about-the-design"></a>디자인 정보

#### <a name="streamlined-network-design"></a>합리적인 네트워크 디자인

이 토폴로지는 SharePoint 2013, Exchange Server 2013 및 Lync Server 2013의 온-프레미스 네트워크 배포를 보여 줍니다. 또한 인터넷에서 인바운드 SMTP (Simple Mail Transfer Protocol) 트래픽에 대 한 스팸 및 맬웨어 보호 기능을 제공 하는 Microsoft 클라우드 기반 서비스의 사용과 Exchange Online Protection을 함께 보여 줍니다. 
  
이 네트워크 디자인은 최소 네트워크 기능 집합으로 간소화 되었습니다. 디자인은 일부 조직에 필요한 추가 보안 또는 인프라 기능을 고려 하지 않습니다. 
  
다이어그램: 
  
- 게이트웨이 라우터를 통한 인바운드 및 아웃 바운드 트래픽과 해당 하는 SharePoint, Exchange 및 Lync server 계층에 대 한 부하 분산을 보여 주는 예제 네트워크 토폴로지 (외부 및 내부)를 제공 합니다. 
    
- 타사 VPN 게이트웨이 또는 DirectAccess 서버와 같은 선택적 원격 액세스 서버를 사용 하 여 로밍 또는 원격 직원에 대 한 보안 통신을 제공 하는 방법을 보여 줍니다. 
    
- 자세한 내용은 클라이언트에서 각 플랫폼 서버 계층으로의 SharePoint, Exchange 및 Lync 트래픽 흐름에 대해 설명 합니다. 
    
- 클라이언트 (예: 파트너 또는 직원)를 기반으로 하는 원격 또는 내부 액세스 연결의 유형 및 사용 되는 인증 방법을 식별 합니다. 
    
- 프런트 엔드, 응용 프로그램, 데이터베이스 및 기타 수준을 식별 하 여 필요한 서버 역할로 SharePoint, Exchange 및 Lync 플랫폼을 구분 합니다. 
    
SharePoint, Lync 및 Exchange에서 여기에 사용 되는 아키텍처는 이러한 플랫폼을 구현 하는 기본적인 방법을 제안 하지 않습니다. 또한 고유한 네트워크 요구 사항 및 보안 고려 사항에 따라 토폴로지가 다르다는 것을 보여 주는 예제를 제공 합니다. 
  
#### <a name="gateway-router"></a>게이트웨이 라우터

이 토폴로지의 경우 게이트웨이 라우터는 네트워크의 가장자리에 위치 하 고 인트라넷에서 들어오고 나가는 모든 트래픽을 라우팅합니다. 또는 게이트웨이 라우터와 표시 된 부하 분산 장치 (예: 여러 방화벽 계층) 간의 간격을 브리지 하는 다른 구성 요소도 있을 수 있습니다. 이 토폴로지는 네트워크를 여러 개 배포 하는 한 가지 방법만을 나타냅니다. 이 구성에서 게이트웨이는 라우터 인터페이스에서 특별히 들어오고 나가는 IP 기반 트래픽을 허용 하기 위해 Acl (액세스 제어 목록)을 사용 하 여 구성 됩니다. 네트워크 전체에서 방화벽 등의 다른 장치 에서도 Acl, 고급 검사 또는 NAT (Network Address Translation)를 수행할 수 있습니다. 
  
#### <a name="load-balancer-and-reverse-proxy-devices"></a>부하 분산 장치와 역방향 프록시 장치

하드웨어 또는 소프트웨어 부하 분산 솔루션을 사용 하 여 SharePoint 프런트 엔드 웹 서버 및 Exchange 클라이언트 액세스 서버 (CASs)를 포함 하는 세그먼트에 대 한 트래픽을 리디렉션할 수 있습니다. 경우에 따라 지 속성 요구 사항에 대해 레이어 7 하드웨어 기반 부하 분산 장치를 사용 하는 것이 좋습니다 (예: 쿠키 또는 헤더). 그러나 비용, 활용도 증대 및 작업 부하와 같은 요소는 특정 요구에 적합 하지 않을 수 있습니다. SharePoint, Exchange 및 Lync에서 부하 분산을 위해 다음 사항을 고려 하세요. 
  
- SharePoint-SharePoint 2013의 경우 프런트 엔드 웹 서버에 대 한 선호도를 사용 하도록 설정할 필요가 없습니다. 일반적으로이는 고정 세션을 만드는 데 사용 되며 클라이언트에서 각 프런트 엔드 웹 서버에 대 한 여러 인증 요청을 방지 하기 위한 것입니다. SharePoint 2013의 새로운 분산 캐시 서비스는 SharePoint 팜의 웹 서버 전체에 로그온 토큰을 저장 하 고 배포 합니다. 
    
- Exchange-Exchange 2013에서 CAS 역할은 계층 4 부하 분산을 사용 하 여 전송 계층에 요청을 분산 하는 방식으로 설계 되었습니다. 따라서 부하 분산 장치 사용률 및 작업 부하가 크게 감소할 수 있습니다. 
    
- Lync 풀에 대 한 SIP (Session 착수 프로토콜) 트래픽에는 DNS (Lync Domain Name System) 부하 분산을 사용 하는 것이 좋습니다. HLB (하드웨어 부하 분산)는 Lync Web (HTTPS) 트래픽에 필요 합니다. 
    
### <a name="remote-access-options"></a>원격 액세스 옵션

인터넷의 파트너를 위해 인트라넷 리소스를 게시 하거나 원격 또는 로밍 직원에 게 보안 원격 액세스를 제공할 수 있는 몇 가지 옵션이 있습니다. 이러한 예에는 역방향 프록시, DirectAccess 및 타사 VPN 게이트웨이가 포함 됩니다. 이 섹션의 뒷부분에서 설명 하는 원격 액세스 솔루션은 SharePoint, Lync 및 Exchange에 대 한 것 이거나, 온-프레미스 배포에서 이러한 서버의 조합에 해당 합니다. 그러나 일부 원격 옵션은 특정 솔루션에서 작동 하지 않을 수 있습니다. 
  
역방향 프록시-역방향 프록시는 SSL (Secure Sockets Layer)과 같은 트래픽 암호화를 지원 하며,이를 통해 인터넷의 인증 된 사용자 및 파트너에 게 인트라넷 응용 프로그램 및 웹 리소스를 게시할 수 있습니다. Microsoft Forefront UAG (통합 액세스 게이트웨이)를 예로 들 수 있습니다. 많은 하드웨어 부하 분산 장치 역시 역방향 프록시 기능을 지원 합니다. 그러나 트래픽 격리, 보안 compartmentalization 및 성능 최적화와 같은 요구 사항에 따라 독립 실행형 솔루션을 사용 하는 경우에도 여전히 유효한 시나리오가 있습니다. 
  
역방향 프록시 혜택 및 고려 사항: 
  
- 인트라넷 리소스에 액세스 하는 파트너 또는 사용자에 대 한 인증 및 보안 액세스를 제공 합니다 (클라이언트와 역방향 프록시 서버 사이에 SSL (TCP 443) 사용). 
    
- Exchange의 경우 Forefront UAG와 같은 역방향 프록시를 사용 하는 경우의 이점은 Exchange 클라이언트 액세스 서버에 액세스 하기 전에 사전 인증입니다. OWA (Outlook Web Access)와 같은 게시 된 응용 프로그램을 사용 하는 원격 액세스 사용자는 내부 네트워크에 연결 되기 전에 기본, NTLM 또는 Kerberos 방법으로 인증할 수 있습니다. 
    
- Exchange 및 SharePoint의 경우 Forefront UAG와 같은 솔루션은 SSL 연결을 종료 하 고 인트라넷 리소스 서버의 로드를 줄이고 인증서를 위한 단일 관리 지점을 제공 합니다. 
    
- Lync의 경우 웹 (HTTPS) 트래픽은 클라이언트 통신을 위해 역방향 프록시 (TCP 443)를 통과 합니다. 역방향 프록시는 Lync 웹 서비스, Exchange CAS 및 Office Web Apps에 대 한 HTTPS 연결을 프록시 합니다. Lync Server 2013에서는 UAG를 지원 하지 않습니다. 
    
DirectAccess-인증에 IPsec (인터넷 프로토콜 보안)을 사용 하 고 DirectAccess 클라이언트와 서버 간의 트래픽 암호화에 사용 되는 원격 액세스 기술입니다. DirectAccess는 연결을 시작할 필요 없이 로밍 및 원격 직원과의 인터넷 및 인트라넷 리소스에 동시에 액세스할 수 있도록 합니다. 
  
고려해 야 할 DirectAccess: 
  
- DirectAccess는 DirectAccess 클라이언트와 서버 간에 IPsec 보호 된 트래픽 (프로토콜 50, 51 및 UDP 500)을 사용 합니다. 
    
- Windows Server 2012 및 Windows 8 용 DirectAccess에는 서버 및 클라이언트 인증을 위한 PKI (공개 키 인프라) 배포가 필요 하지 않습니다. 
    
- IPsec 암호화 및 암호 해독과 관련 된 오디오 및 비디오 대기 시간 문제로 인해 Lync Server 2013에서 DirectAccess를 사용 하는 것이 좋습니다. 
    
    VPN 게이트웨이-일반적인 VPN 게이트웨이는 원격 액세스 클라이언트 컴퓨터가 터널링 및 사용자가 시작한 연결을 통해 논리적으로 인트라넷에 투영 되는 원격 액세스 연결을 제공 합니다. Windows Server 2012 또는 몇몇 타사 솔루션에서 통합 원격 액세스를 사용 하 여 로밍 또는 원격 직원을 위해 인트라넷에 보안 액세스를 제공할 수 있습니다. Lync에는 VPN을 사용할 수 없습니다. 원격 Lync 트래픽은에 지 서버 및 분할 터널링을 사용 해야 합니다. 
    
### <a name="domain-name-system-dns-considerations"></a>DNS (Domain Name System) 고려 사항

인터넷 및 인트라넷 사용자가 DNS 이름을 적절 한 IP 주소로 확인 하는 데 사용할 수 있는 DNS 레코드 집합을 계획 해야 합니다. 
  
- 인터넷 기반 파트너 및 로밍 또는 원격 사원의 경우, 인터넷 DNS 서버에 등록 된 DNS 레코드는 게이트웨이 라우터에 해당 하는 공용 IP 주소 집합, Lync에 지 서버, Vip (가상 IP 주소) 집합에 대 한 해결 방법을 제공 합니다. 부하 분산 및 DirectAccess 또는 VPN 게이트웨이가 필요 합니다. 
    
- 인트라넷 기반 사용자의 경우 인트라넷 DNS 서버를 사용 하 여 등록 된 DNS 레코드는 SharePoint, Lync 및 Exchange 리소스에 액세스할 수 있도록 부하 분산 장치에 대 한 Vip (가상 IP 주소) 집합에 대 한 해결 방법을 제공 합니다. 
    
- DirectAccess 클라이언트는 인트라넷 dns 이름 공간 및 인터넷 DNS 서버에 해당 하는 이름에 대해 인트라넷 DNS 서버를 사용 합니다. DirectAccess 작업을 단순화 하려면 인트라넷 및 인터넷 기반 이름에 대해 서로 다른 DNS 네임 스페이스를 사용 하는 분할 DNS 구현을 사용 하는 것이 좋습니다. 예를 들어 인트라넷 네임 스페이스에는 contoso.com for Internet namespace 및 corp.contoso.com을 사용 합니다. 
    
- Exchange는 라우팅 DNS 모델을 사용 하며,이는 호스트에서 IP로의 확인이 회사 네트워크의 공용 라우팅된 트래픽에 따라 다릅니다. 최소한 OWA, 자동 검색, 클라이언트 트래픽의 ActiveSync Url 및 인바운드 메일용 MX 레코드에 대 한 DNS 레코드가 있어야 합니다. 
    
- EOP (Exchange Online Protection)를 사용 하는 경우 MX 레코드는 Exchange 팜이 아닌 해당 서비스를 가리킵니다. 
    
- Exchange의 경우 공용 DNS에 대 한 소유권 TXT 레코드와 페더레이션 공유를 설정 하기 위한 페더레이션 조직 ID가 필요 합니다. 
    
- 원격 액세스 VPN 연결이 활성 상태인 경우 인트라넷 DNS 서버만 사용 하도록 원격 액세스 VPN 클라이언트를 구성할 수 있습니다. 
    
### <a name="diagram-description"></a>다이어그램 설명

이 다이어그램에서는 게이트웨이 라우터를 통한 인바운드 및 아웃 바운드 트래픽과 해당 하는 SharePoint, Exchange 및 Lync server 계층에 대 한 부하 분산 (외부 및 내부)을 보여 주는 예제 네트워크 토폴로지를 제공 합니다. 이 다이어그램의 설명은 다음과 같은 두 부분으로 나뉩니다. 
  
- 다이어그램에 표시 된 구성 요소에 대 한 설명 
    
- 구성 요소를 통해 SharePoint, Exchange, Lync 및 Office Web Apps 서버 계층으로 트래픽이 이동 하는 방식에 대 한 설명입니다. 
    
#### <a name="description-of-components-shown-in-the-diagram"></a>다이어그램에 표시 된 구성 요소에 대 한 설명

#### <a name="user-types"></a>사용자 유형

네트워크 및 클라우드 서비스 외에도 다음과 같은 네 가지 유형의 사용자와 내부 1 개가 있습니다. 
  
- 파트너 회사 (회사 간)-외부 
    
- 개별 파트너 (SharePoint 및 익명 (Lync))-외부 
    
- 로밍 및 원격 직원-외부 
    
- 내부 직원 
    
#### <a name="cloud-based-email-traffic"></a>클라우드 기반 전자 메일 트래픽

SMTP 기반 전자 메일 트래픽을 위한 클라우드 기반 구성 요소 (인터넷 메일 호스트 또는 Exchange Online Protection)가 있습니다. 
  
#### <a name="authentication-for-external-access"></a>외부 액세스에 대 한 인증

Lync, SharePoint 및 Exchange에 대 한 특정 인증 절차 집합은 각 사용자 유형에 대해 제공 됩니다. 여기에 대해서는이 문서의 뒷부분에 자세히 설명 되어 있습니다. 
  
#### <a name="gateway-router-with-acls"></a>Acl을 사용 하는 게이트웨이 라우터

게이트웨이 라우터는 네트워크의 가장자리에 위치 하 고 인트라넷에서 들어오고 나가는 모든 트래픽을 라우팅합니다. 
  
#### <a name="remote-access-servers-for-lync-and-sharepoint"></a>Lync 및 SharePoint 용 원격 액세스 서버

이 토폴로지에는 Lync Edge 서버와 SharePoint VPN 게이트웨이 또는 DirectAccess 서버가 포함 되어 있습니다. 
  
#### <a name="load-balancer-and-reverse-proxy-device"></a>부하 분산 장치 및 역방향 프록시 디바이스

하드웨어 또는 소프트웨어 부하 분산 솔루션을 사용 하 여 SharePoint 프런트 엔드 웹 서버 및 Exchange 클라이언트 액세스 서버 (CASs)를 포함 하는 세그먼트에 대 한 트래픽을 리디렉션할 수 있습니다. 이 토폴로지는 부하 분산 장치의 Lync VIP, SharePoint VIP 및 Exchange VIP 구성 요소를 보여 줍니다. 
  
#### <a name="servers"></a>Servers

서버는 Lync, SharePoint, Exchange 및 Office Web Apps 서버 4 대입니다. 각 서버에는 프런트 엔드, 클라이언트 액세스 계층, 응용 프로그램 계층 및 데이터베이스/저장소 계층의 세 가지 계층을 사용할 수 있습니다.
  
#### <a name="front-end-client-access-tier"></a>프런트 엔드, 클라이언트 액세스 계층

이 계층에는 4 대의 모든 서버에 구성 요소가 있습니다. 
  
- Lync 풀 (프런트 엔드) 이 다이어그램은 두 개의 Lync 데이터베이스를 보여 줍니다. 
    
- SharePoint 프런트 엔드 및 분산 캐시 이 다이어그램은 세 개의 SharePoint 데이터베이스를 보여 줍니다. 
    
- Exchange CAS 이 다이어그램에는 두 개의 Exchange 데이터베이스가 표시 됩니다. 
    
- Office Web Apps 서버 두 개의 Office Web Apps 데이터베이스를 보여 주는 다이어그램 
    
#### <a name="application-tier"></a>응용 프로그램 계층

이 계층에는 SharePoint server의 구성 요소만 포함 됩니다. 
  
- 검색 (쿼리, 인덱스, 관리) 이 다이어그램은 세 개의 SharePoint 데이터베이스를 보여 줍니다. 
    
- 일괄 처리 이 다이어그램은 세 개의 SharePoint 데이터베이스를 보여 줍니다. 
    
#### <a name="databasestorage-tier"></a>데이터베이스/저장소 계층

이 계층에는 Lync, SharePoint 및 Exchange 서버에 구성 요소가 있습니다. 
  
- Lync 데이터베이스 (백 엔드) 이 다이어그램은 3 개의 Lync 데이터베이스를 보여줍니다. 
    
- SharePoint 데이터베이스 이 다이어그램은 세 개의 SharePoint 데이터베이스를 보여 줍니다. 
    
- Exchange 사서함 서버 이 다이어그램에는 두 개의 Exchange 사서함 서버가 표시 됩니다. 
    
각 SharePoint server 역할에 설치 된 구성 요소에 대 한 자세한 내용은 [sharepoint 용 능률적인 토폴로지-2013](https://aka.ms/Ma5cgk)을 참조 하십시오. 
  
#### <a name="description-of-how-traffic-moves-through-the-components-to-the-different-server-tiers"></a>구성 요소를 통해 트래픽이 서로 다른 서버 계층으로 이동 하는 방식에 대 한 설명

이 섹션에서는 사용자 요청이 네트워크 토폴로지를 이동 하는 방법에 대해 설명 합니다. 
  
#### <a name="authentication-and-routing-for-external-access"></a>외부 액세스용 인증 및 라우팅

네트워크 및 클라우드 서비스 외에도 다음과 같은 세 가지 유형의 클라이언트가 있습니다. 
  
- 파트너 회사 (회사 간)-외부 
    
- 개별 파트너 (SharePoint 및 익명 (Lync))-외부 
    
- 로밍 및 원격 직원-외부 
    
각 외부 사용자 유형에 대 한 인증 및 라우팅 프로세스는 개별적으로 설명 됩니다. 
  
#### <a name="partner-companies-business-to-business-httpspartnerwebcontosocom"></a>파트너 회사 (b2b) (https://partnerweb.contoso.com)

- Lync: 다른 조직과의 페더레이션 트러스트, AOL과의 Skype 및 공용 IM 연결 (PIC) Lync federation 트래픽은 게이트웨이 라우터를 lync에 지 서버에서 lync VIP (부하 분산 장치/역방향 프록시 서버)로 이동한 다음 Lync Server로 이동 합니다. 
    
- SharePoint: SAML 인증을 사용 하는 신뢰할 수 있는 파트너 id 공급자 SharePoint 클라이언트 트래픽은 게이트웨이 라우터를 통해 SharePoint VIP (부하 분산 장치/역방향 프록시 서버)로 이동한 다음 SharePoint 서버로 이동 합니다. 
    
- Exchange: 메일 트래픽용 상호 인증 TLS, 페더레이션 공유에 대 한 SAML 인증 Exchange 클라이언트 트래픽은 게이트웨이 라우터를 통해 Exchange VIP (부하 분산 장치/역방향 프록시 서버)로 이동한 다음 Exchange 서버로 이동 합니다. 
    
- SMTP 트래픽은 게이트웨이 라우터를 통과 하 고 Exchange VIP (부하 분산 장치/역방향 프록시 서버)를 통해 Exchange 서버를 통과 합니다. 
    
#### <a name="individual-partners-sharepoint-and-anonymous-lync-httpspartnerwebcontosocom-and-httpsmeetcontosocom"></a>개별 파트너 (SharePoint) 및 익명 (Lync)https://partnerweb.contoso.com 및https://meet.contoso.com)

- Lync: 익명 사용자는 직원용으로 구성 된 Lync 모임에만 참가할 수 있습니다. Lync federation 트래픽은 게이트웨이 라우터를 lync에 지 서버에서 lync VIP (부하 분산 장치/역방향 프록시 서버)로 이동한 다음 Lync Server로 이동 합니다. 
    
- SharePoint: SAML 인증 또는 폼 기반 인증을 사용 하는 신뢰할 수 있는 파트너 id 공급자 SharePoint 클라이언트 트래픽은 게이트웨이 라우터를 통해 SharePoint VIP (부하 분산 장치/역방향 프록시 서버)로 이동한 다음 SharePoint 서버로 이동 합니다. 
    
- Exchange: 적용 되지 않습니다. 
    
- Lync 웹 트래픽은 게이트웨이 라우터를 lync에 지 서버에서 lync VIP (부하 분산 장치/역방향 프록시 서버)에 대 한 하드웨어 부하 분산 장치 (HTTPS 트래픽에 필요)로 이동한 다음 Lync Server로 이동 합니다. 
    
#### <a name="roaming-and-remote-employees"></a>로밍 및 원격 직원

1. https://intranet.contoso.com 
    
2. https://teams.contoso.com 
    
3. https://my.contoso.com
    
4. https://partnerweb.contoso.com 
    
5. https://mail.contoso.com* 
    
6. https://dial.contoso.com*
    
7. https://meet.contoso.com*
    
* Exchange URL에는 자동 검색, ecp, EWS, Microsoft-서버-ActiveSync, OAB, owa, PowerShell 가상 디렉터리가 포함 되어 있습니다. 
  
- Lync: TLS-DSK 또는 NTLM 인증 Lync 클라이언트 트래픽은 게이트웨이 라우터를 lync에 지 서버에서 lync VIP (부하 분산 장치/역방향 프록시 서버)로 이동한 다음 Lync Server로 이동 합니다. 
    
- SharePoint: AD DS (Active Directory 도메인 서비스), 폼 기반 인증 또는 SAML 인증을 사용 합니다. SharePoint 클라이언트 트래픽은 VPN 게이트웨이 또는 DirectAccess 서버를 통해 SharePoint VIP (부하 분산 장치/역방향 프록시 서버)로 이동한 다음 SharePoint server로 이동 합니다. 
    
- Exchange: SSL (ActiveSync, 자동 검색) 및 OWA (폼 기반 인증)를 통한 기본 인증 Exchange 클라이언트 트래픽은 게이트웨이 라우터를 통해 Exchange VIP (부하 분산 장치/역방향 프록시 서버)로 이동한 다음 Exchange 서버로 이동 합니다. 
    
- Lync 클라이언트 트래픽은 게이트웨이 라우터를 통해 Lync VIP (부하 분산 장치/역방향 프록시 서버)에 대 한 하드웨어 부하 분산 장치 (HTTPS 트래픽에 필요 함)로 이동한 다음 Lync Server로 이동 합니다. 
    
#### <a name="authentication-for-internal-access"></a>내부 액세스용 인증

#### <a name="internal-employees"></a>내부 직원

> https://intranet.contoso.com 
    
> https://teams.contoso.com 
    
> https://my.contoso.com
    
> https://partnerweb.contoso.com
    
> https://mail.contoso.com* 
    
> https://dial.contoso.com 
    
> https://meet.contoso.com
    
> https://admin.contoso.com
    
- Lync: Kerberos, TLS-DSK 또는 NTLM 인증 Lync 클라이언트 트래픽은 Lync VIP (부하 분산 장치/역방향 프록시 서버)로 이동한 다음 Lync Server로 이동 합니다. 
    
- SharePoint: AD DS (Active Directory 도메인 서비스), 폼 기반 인증 또는 SAML 인증을 사용 합니다. Sharepoint 클라이언트 트래픽은 SharePoint VIP (부하 분산/역방향 프록시 서버)로 이동한 다음 SharePoint 서버로 이동 합니다. 
    
- Exchange: AD DS, 폼 기반 인증 Exchange 클라이언트 트래픽은 Exchange VIP (부하 분산 장치/역방향 프록시 서버)로 이동한 다음 Exchange 서버로 이동 합니다. 
    
- Lync 클라이언트 트래픽은 HTTPS 트래픽에 필요한 하드웨어 부하 분산 장치에 대 한 Lync VIP (부하 분산 장치/역방향 프록시 서버)로 이동한 다음 Lync Server로 이동 합니다. 
    
#### <a name="cloud-based-email-traffic"></a>클라우드 기반 전자 메일 트래픽

SMTP 기반 전자 메일 트래픽에 사용 되는 클라우드 기반 구성 요소는 인터넷 메일 호스트 또는 Exchange Online Protection으로 구성 됩니다.
  
이러한 구성 요소는 SMTP를 사용 하 여 네트워크를 통해 전자 메일 트래픽을 이동 합니다. 트래픽이 게이트웨이 라우터를 통해 Exchange VIP (부하 분산 장치/역방향 프록시 서버)로 이동한 다음 Exchange 서버로 이동 합니다. 
  
### <a name="network-traffic-legend"></a>네트워크 트래픽 범례

범례 상자에는 그래프에 표시 되는 다양 한 유형의 트래픽이 다음과 같이 서로 다른 색상의 선으로 나타납니다. 
  
- 녹색 줄: Lync SIP 트래픽 
    
- 파란 선: Lync 웹 트래픽 
    
- 자주색 줄: SharePoint 클라이언트 트래픽 
    
- 주황색 줄: Exchange 클라이언트 트래픽 
    
- 회색 줄: exchange 온-프레미스 및 Exchange Online Protection 간의 Exchange 메일 서버 트래픽 
    
각 트래픽 유형 및 사용 하는 포트에 대해서도 범례 상자에 설명 되어 있습니다. 
  
#### <a name="lync-sip-traffic-and-lync-web-traffic"></a>Lync SIP 트래픽 및 Lync 웹 트래픽

Lync에 지 서버는 외부 사용자 통신에 다음 포트를 사용 합니다. 
  
- 신호/IM 트래픽 (SIP/SIMPLE): TCP 포트 443 (인바운드 트래픽에 대해 개방) 
    
- PSOM (웹 회의 트래픽): TCP 443 (인바운드 트래픽에 대해 열기) 
    
- A/V 트래픽 (SRTP): TCP 443, UDP 3478 및 TCP 50000-59999 (선택 사항) (인바운드 및 아웃 바운드 트래픽을 위해 열기) 
    
Lync에 지 서버는 다음 포트를 사용 하 여 페더레이션 통신을 수행 합니다. 
  
- TCP 포트 5061 (SIP), 5269 (XMPP), 443 및 UDP 3478 (SRTP) (인바운드 및 아웃 바운드 트래픽을 위해 열기) 
    
#### <a name="sharepoint-client-traffic"></a>SharePoint 클라이언트 트래픽

SharePoint에서는 클라이언트와 부하 분산 장치 간의 암호화 된 통신을 위해 SSL (TCP 포트 443)을 사용할 수 있습니다. 인터넷에서 외부 액세스를 사용 하는 경우 게이트웨이 라우터 (또는 외부 방화벽)에서 인바운드 및 아웃 바운드 트래픽에 대해이 포트를 열어야 합니다. 
  
#### <a name="exchange-client-traffic-and-exchange-mail-server-traffic"></a>Exchange 클라이언트 트래픽 및 Exchange 메일 서버 트래픽

Exchange에서는 서버 간 통신에 TCP 포트 25 (SMTP)를 사용 합니다. 대부분의 클라이언트 트래픽 (OWA, ActiveSync, 자동 검색, Outlook Anywhere)은 포트 443 (HTTPS)를 통해 처리 됩니다. POP 또는 IMAP 클라이언트를 사용 하는 경우에는 포트 110 (POP3), 995 (암호화 된 POP3), 143 (IMAP4), 993 (암호화 된 IMAP4) 및 587 (SMTP)도 이러한 클라이언트를 지원 합니다. 
  
#### <a name="more-on-lync-network-traffic"></a>Lync 네트워크 트래픽에 대 한 자세한 내용은 무엇입니까?

Lync Server를 통해 조직에서 인스턴트 메시징, 웹 회의, 응용 프로그램 공유 및 음성 통신을 제공 하는 방법에 대해 알아봅니다. 자세한 내용은 [Microsoft Lync Server 2013 프로토콜 워크 로드 포스터](https://aka.ms/G5jzjo)를 참조 하세요. 
  
또한 포스터에는이 정보에 액세스할 수 있는 QR 코드가 포함 되어 있습니다. 
  

