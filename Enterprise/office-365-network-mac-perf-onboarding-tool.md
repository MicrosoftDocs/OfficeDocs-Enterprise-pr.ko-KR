---
title: Microsoft 365 관리 센터에서 microsoft 365 connectivity test (preview)
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 04/21/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: M365 관리 센터의 Microsoft 365 connectivity test (preview)
ms.openlocfilehash: 0c6f16c39c5a2db99ed636cb3a1b52818383ea5a
ms.sourcegitcommit: dce58576a61f2c8efba98657b3f6e277a12a3a7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/12/2020
ms.locfileid: "44208799"
---
# <a name="microsoft-365-connectivity-test-in-the-microsoft-365-admin-center-preview"></a>Microsoft 365 관리 센터의 microsoft 365 connectivity test (preview)

Microsoft 365 connectivity test는에 있습니다 <https://connectivity.office.com> . 이 도구는 Microsoft 365 관리 센터에서 제공 하는 네트워크 통찰력 및 네트워크 점수 정보에 대 한 adjunct입니다. **| 네트워크 성능** 메뉴

>[!NOTE]
>온 보 딩 도구는 WW 상업용 및 GCC 중간에 있는 테 넌 트를 지원 하지만 GCC High, DoD, 독일 또는 중국이 아닙니다.

Microsoft 365 관리 센터의 네트워크 insights는 Microsoft 365 테 넌 트에 대 한 제품 측정을 기반으로 합니다. 비교 시 Microsoft 365 연결 테스트의 네트워크 insights 도구에서 로컬로 실행 됩니다. 제품에서 수행할 수 있는 테스트는 제한 되며 사용자에 대 한 로컬 테스트를 실행 하 여 더 많은 데이터를 수집할 수 있습니다. Microsoft 365 관리 센터의 네트워크 insights에서 특정 사무실 위치에 Microsoft 365 사용에 대 한 네트워킹 문제가 있음을 보여 줍니다. Microsoft 365 연결 테스트를 통해 권장 되는 네트워크 성능 개선 작업으로 인해 발생 하는 문제의 근본적인 원인을 확인할 수 있습니다.

Microsoft 365 관리 센터의 각 사무실 위치에 대해 네트워킹 품질 상태를 평가할 수 있으며 Microsoft 365 연결 테스트를 기반으로 테스트를 배포한 후 더 자세한 내용을 확인할 수 있는 방법을 함께 사용 하는 것이 좋습니다.

>[!IMPORTANT]
>네트워크 insights, Microsoft 365 관리 센터의 성능 권장 사항 및 평가는 현재 미리 보기 상태 이며, 기능 미리 보기 프로그램에 등록 되어 있는 Microsoft 365 테 넌 트에만 사용할 수 있습니다.

## <a name="the-advanced-tests-client-application"></a>고급 테스트 클라이언트 응용 프로그램

Microsoft 365 연결 테스트는 두 부분으로 구성 됩니다. 웹 사이트가 <https://connectivity.office.com> 있고 다운로드 가능한 Windows 클라이언트 응용 프로그램이 있습니다. 다운로드 가능한 클라이언트는 고급 네트워크 연결 테스트를 실행 하 고 대부분의 테스트를 실행 해야 합니다.

웹 사이트에서 고급 클라이언트 테스트를 실행할 수 있으며, 결과를 실행 하는 동안 웹 페이지로 다시 채웁니다.

![O365 네트워크 온 보 딩 도구 예제 테스트 결과](Media/m365-mac-perf/m365-mac-perf-onboarding-tool-tests.png)

## <a name="user-office-location"></a>사용자 사무실 위치

사용자의 사무실 위치는 사용자 웹 브라우저에서 검색 됩니다. 네트워크 거리를 엔터프라이즈 네트워크 경계의 특정 부분으로 식별 하는 데 사용 됩니다.

사용자 사무실 위치는 지도 보기에 표시 됩니다.

## <a name="distance-to-the-network-egress-location"></a>네트워크 송신 위치에 대 한 거리

서버 쪽에서 네트워크 송신 IP 주소를 식별 합니다. 위치 데이터베이스는 네트워크 egress의 대략적인 위치를 조회 하 여 해당 위치에서 사무실 위치로의 거리를 확인 하는 데 사용 됩니다. 이는 거리가 500 마일 (800 킬로미터) 보다 크면 네트워크에 대 한 정보를 파악 하는 것으로 표시 됩니다.

네트워크 송신 위치가 지도 보기에 표시 되 고 엔터프라이즈 WAN 내부에 네트워크가 연결 되었음을 나타내는 사용자 사무실 위치에 연결이 설정 됩니다.

네트워크 송신 IP 주소에서 조회 되는 위치는 정확 하지 않을 수 있으며이 테스트에서 잘못 된 결과가 이어집니다. 특정 IP 주소에 대해이 오류가 발생 하는지 확인 하려면 공개적으로 액세스 가능한 네트워크 IP 주소 위치 웹 사이트를 사용할 수 있습니다.

Microsoft 365 네트워크 연결에는 사용자 사무실 위치에서 인터넷으로 로컬 및 직접 네트워크 송신을 구현 하는 것이 좋습니다. 이러한 네트워크 통찰력을 해결 하는 가장 좋은 방법은 로컬 및 직접 egress에 대 한 개선 사항입니다.

## <a name="exchange-online-service-front-door"></a>Exchange Online 서비스 전면 도어

사용 중인 Exchange Online 서비스 전면 도어는 Outlook에서이를 수행 하는 것과 동일한 방식으로 식별 되며, 사용자 사무실 위치에서의 네트워크 TCP 대기 시간을 측정 합니다. 이 두 가지 모두 표시 되며, 현재 위치에 대 한 권장 되는 최적 서비스 전면 도어 목록과 비교 됩니다. 이는 최적이 아닌 Exchange Online 서비스 전면 문이 사용 중인 경우 네트워크에 대 한 통찰력으로 표시 됩니다.

Exchange Online 서비스 프런트 도어를 사용 하는 경우에는 회사 네트워크 egress가 되기 전에 로컬 및 직접 네트워크 송신을 권장 하는 네트워크 교환이 발생 하는 경우가 있습니다. 또한 원격 DNS 재귀 해결 프로그램 서버를 사용 하는 경우에도 DNS 재귀 해결 프로그램 서버를 네트워크 egress에 정렬 하는 것이 좋습니다.

Exchange Online 서비스 전면 도어의 TCP 대기 시간에 대 한 잠재적 개선이 계산 됩니다. 이 작업은 테스트를 거친 사용자 사무실 위치 네트워크 대기 시간을 살펴보고 현재 위치에서 closets Exchange Online 서비스 전면 도어의 네트워크 대기 시간을 빼서 수행 합니다. 차이점은 개선에 대 한 잠재적인 기회를 나타냅니다.

## <a name="comparison-of-performance-of-customers-in-the-area"></a>영역의 고객 성능 비교

Exchange Online 서비스에 대 한 사용자 사무실 위치의 네트워크 TCP 대기 시간은 같은 메트로 영역의 다른 Microsoft 365 고객과 비교 됩니다. 네트워크에 대 한 자세한 내용은 같은 지하철 영역에 있는 고객 중 10% 이상이 더 나은 성능을 가진 경우에 표시 됩니다.

이 네트워크 통찰력은 도시의 모든 사용자가 동일한 통신 인프라에 대 한 액세스 권한을 가지 며 인터넷 회로 및 Microsoft 네트워크와 같은 근접성을 갖게 된다는 것을 기반으로 생성 됩니다.

## <a name="in-use-default-gateway"></a>기본 게이트웨이 사용

사용 중인 기본 게이트웨이는 테스트 클라이언트가 TCP/IP 네트워크 연결을 라우팅하기 위해 구성한 라우터입니다.

이는 정보를 제공 하기 위한 것 이며 네트워크 통찰력에는 영향을 주지 않습니다.

## <a name="in-use-dns-servers"></a>사용 중인 DNS 서버

테스트를 실행 한 클라이언트 컴퓨터에 구성 된 DNS 서버를 표시 합니다. DNS 재귀 확인 프로그램 서버 일 수 있지만 드문 경우는 아닙니다. DNS 결과를 캐시 하 고 캐시 되지 않은 DNS 요청을 다른 DNS 서버로 전달 하는 DNS 전달자 서버가 될 수 있습니다.

이는 정보를 제공 하기 위한 것 이며 네트워크 통찰력에는 영향을 주지 않습니다.

## <a name="identified-dns-recursive-resolver-server"></a>식별 된 DNS 재귀 확인 프로그램 서버

사용 중인 DNS 재귀 해결 프로그램은 특정 DNS 요청을 수행한 다음 DNS 이름 서버에 동일한 요청을 받은 IP 주소를 물어 확인 합니다. 이 IP 주소는 DNS 재귀 해결 프로그램 이며 위치를 찾기 위해 IP 주소 위치 데이터베이스에서 조회 됩니다. 그러면 사용자 사무실 위치에서 DNS 재귀 확인자 서버 위치로의 거리가 계산 됩니다. 이는 거리가 500 마일 (800 킬로미터) 보다 크면 네트워크에 대 한 정보를 파악 하는 것으로 표시 됩니다.

네트워크 송신 IP 주소에서 조회 되는 위치는 정확 하지 않을 수 있으며이 테스트에서 잘못 된 결과가 이어집니다. 특정 IP 주소에 대해이 오류가 발생 하는지 확인 하려면 공개적으로 액세스 가능한 네트워크 IP 주소 위치 웹 사이트를 사용할 수 있습니다.

이 네트워크 통찰력은 Exchange Online 서비스의 프런트 도어 선택에 특히 영향을 줍니다. 이 통찰력을 확인 하려면 로컬 및 직접 네트워크 송신이 필수 구성 요소 여야 하 고, DNS 재귀 해결 프로그램을 해당 네트워크 egress에 가까이에 배치 해야 합니다.

## <a name="dns-lookup-of-exchange-online-front-end-server-and-sharepoint-online-front-end-server"></a>Exchange Online 프런트 엔드 서버 및 SharePoint Online 프런트 엔드 서버의 DNS 조회

이러한 두 가지 Microsoft 365 작업에 대 한 서비스 전면 도어의 DNS 레코드가 표시 됩니다. 이러한 사용자는 정보를 제공 하기 위한 것 이며 연결 된 네트워크 통찰력은 없습니다.

## <a name="proxy-server-identification"></a>프록시 서버 id

로컬 컴퓨터에 구성 된 프록시 서버를 확인 합니다. 최적화 범주에 대 한 네트워크 경로에 구성 되어 있는 항목 (Microsoft 365 네트워크 트래픽)이 있는지 확인 합니다. 사용자 사무실 위치에서 프록시 서버 까지의 거리를 확인 합니다. 이러한 간격은 먼저 ICMP ping을 통해 테스트 하며,이로 인해 TCP ping을 실행 하는 데 실패 한 경우에는 IP 주소 위치 데이터베이스에서 프록시 서버 IP 주소를 조회 합니다. 사용자 사무실 위치에서 프록시 서버가 500 마일 (800 킬로미터) 보다 멀리 떨어진 경우 네트워크 통찰력을 볼 수 있습니다.

## <a name="media-quality-checks"></a>미디어 품질 검사

이 테스트에서는 비즈니스용 Skype 네트워크 평가 도구를 설치 및 실행 하 고 결과를 해석 합니다. 이 도구는에서 찾을 수 있습니다 [https://www.microsoft.com/download/details.aspx?id=53885](https://www.microsoft.com/download/details.aspx?id=53885) .

이러한 테스트는 Microsoft 팀 오디오 및 비디오 통화 및 회의 기능에서 사용 하는 것과 같은 UDP 프로토콜 검사입니다. UDP 패킷 손실, UDP 네트워크 대기 시간, UDP 지터 및 UDP 패킷 다시 정렬에 대해 테스트 합니다. 네트워크 통찰력은 허용 범위를 초과 하는 경우에 표시 됩니다.

## <a name="tcp-connectivity-tests"></a>TCP 연결 테스트

사용자 사무실 위치에서 필요한 모든 Microsoft 365 네트워크 끝점에 대 한 HTTP 연결을 테스트 합니다. 이러한 기능은에 게시 됩니다 [https://aka.ms/o365ip](https://aka.ms/o365ip) . 연결할 수 없는 모든 필수 네트워크 끝점에 대 한 네트워크 통찰력이 표시 됩니다.

연결 ay는 회사 네트워크 경계에 있거나 클라우드 프록시로 사용 중인 프록시 서버, 방화벽 또는 다른 네트워크 보안 장치에 의해 차단 됩니다.

## <a name="ssl-interception-tests"></a>SSL 가로채기 테스트

에서 정의 된 최적화 또는 허용 범주에 있는 각각의 필수 Microsoft 365 네트워크 끝점에서 SSL 인증서를 테스트 합니다 [https://aka.ms/o365ip](https://aka.ms/o365ip) . Microsoft SSL 인증서를 찾지 못하는 테스트는 중간 네트워크 장치에 의해 연결 된 암호화 된 네트워크를 차단 해야 합니다. 네트워크에 대 한 통찰력은 모든 암호화 된 네트워크 끝점에 표시 됩니다.

Microsoft에서 제공 하지 않는 SSL 인증서가 발견 되 면 테스트에 대 한 FQDN과 사용 중인 SSL 인증서 소유자가 표시 됩니다. SSL 인증서 소유자는 프록시 서버 공급 업체가 될 수도 있고, 엔터프라이즈 자체 서명 된 인증서 일 수도 있습니다.

## <a name="network-path-diagnostics"></a>네트워크 경로 진단

이 섹션에서는 Exchange Online 서비스 전면 도어, SharePoint Online 서비스 전면 도어 및 Microsoft 팀 서비스 전면 도어에 대 한 ICMP traceroute 결과를 보여 줍니다. 정보를 제공 하기 위한 것 이며 연결 된 네트워크 통찰력은 없습니다.

## <a name="faq"></a>FAQ

다음은 자주 묻는 몇 가지 질문에 대 한 대답입니다.

### <a name="is-this-tool-released-and-supported-by-microsoft"></a>이 도구는 Microsoft에서 출시 및 지원 하나요?

이는 현재 개념 증명 이며 Microsoft의 지원을 통해 일반 가용성 릴리스 상태에 도달할 때까지 정기적으로 업데이트를 제공 하는 계획입니다. 개선에 도움이 되는 의견을 제공 하세요. 테스트 결과를 기준으로 조직에 대해 사용자 지정 된이 도구의 일부로 보다 자세한 Office 365 네트워크 온 보 딩 가이드를 게시할 계획입니다.

### <a name="what-is-microsoft-365-service-front-door"></a>Microsoft 365 서비스 전면 도어 란?

Microsoft 365 서비스 전면 도어는 Microsoft의 글로벌 네트워크에서 Office 클라이언트 및 서비스가 네트워크 연결을 종료 하는 진입점입니다. Microsoft 365에 대 한 최적의 네트워크 연결을 위해 네트워크 연결이 도시나 메트로 가장 가까운 Microsoft 365 전면 도어로 종료 되는 것이 좋습니다.

참고: Microsoft 365 서비스 전면 도어는 Azure marketplace에서 제공 되는 "Azure 전면 도어 서비스" 제품과 직접 관계가 없습니다.

### <a name="what-is-an-optimal-microsoft-365-service-front-door"></a>최적의 Microsoft 365 서비스 전면 도어 란 무엇입니까?

최적의 Microsoft 365 서비스 전면 도어는 일반적으로 구/군/시 또는 메트로 지역에 있는 네트워크 egress에 가장 가까운 곳입니다. Microsoft 365 네트워크 성능 도구를 사용 하 여 사용 중인 Microsoft 365 서비스 전면 도어 및 최적의 서비스 전면 도어 위치를 확인 합니다. 사용 중인 전면 문이 최적 상태 이면 도구에서 Microsoft의 글로벌 네트워크에 최적 상태로 연결 하는 것입니다.

### <a name="what-is-an-internet-egress-location"></a>인터넷 송신 위치 란?

인터넷 송신 위치는 네트워크 트래픽이 기업 네트워크를 종료 하 고 인터넷에 연결 하는 위치입니다. 또한 NAT (Network Address Translation) 장치가 있는 위치로도 식별 되며, 대개 ISP (인터넷 서비스 공급자)와 연결 됩니다. 위치와 인터넷 송신 위치 사이에 긴 거리가 표시 되 면이로 인해 상당한 WAN 백을 확인할 수 있습니다.

## <a name="related-topics"></a>관련 항목

[Microsoft 365 관리 센터의 네트워크 성능 권장 사항 (미리 보기)](office-365-network-mac-perf-overview.md)

[Microsoft 365 network performance insights (preview)](office-365-network-mac-perf-insights.md)

[Microsoft 365 네트워크 평가 (미리 보기)](office-365-network-mac-perf-score.md)

[Microsoft 365 네트워크 연결 위치 서비스 (미리 보기)](office-365-network-mac-location-services.md)
