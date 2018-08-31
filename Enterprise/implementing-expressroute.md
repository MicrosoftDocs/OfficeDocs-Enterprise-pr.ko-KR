---
title: Office 365용 ExpressRoute 구현
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/5/2017
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
ms.assetid: 77735c9d-8b80-4d2f-890e-a8598547dea6
description: Office 365에 대 한 ExpressRoute 대체 라우팅 경로를 제공 많은 인터넷 마주보는 Office 365 서비스 합니다. Office 365에 대 한 ExpressRoute의 아키텍처는 이미 액세스할 수 있는 인터넷을 통해 해당 IP 접두사에 후속 재배포에 대 한 프로 비전 된 ExpressRoute 회로에 Office 365 서비스의 공용 IP 접두사 광고 기반 네트워크입니다. ExpressRoute와 여러 서로 다른 라우팅 경로 인터넷을 통해 및 ExpressRoute를 통해 다양 한 Office 365 서비스에 대 한 효과적으로 사용 합니다. 네트워크에서 라우팅의이 상태는 내부 네트워크 토폴로지를 설계 하는 방법에 중요 한 변경이 나타낼 수 있습니다.
ms.openlocfilehash: c4479a236d1419293dbd433e8d3c10a11ea5fb45
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542264"
---
# <a name="implementing-expressroute-for-office-365"></a>Office 365용 ExpressRoute 구현

Office 365에 대 한 ExpressRoute 대체 라우팅 경로를 제공 많은 인터넷 마주보는 Office 365 서비스 합니다. Office 365에 대 한 ExpressRoute의 아키텍처는 이미 액세스할 수 있는 인터넷을 통해 해당 IP 접두사에 후속 재배포에 대 한 프로 비전 된 ExpressRoute 회로에 Office 365 서비스의 공용 IP 접두사 광고 기반 네트워크입니다. ExpressRoute와 여러 서로 다른 라우팅 경로 인터넷을 통해 및 ExpressRoute를 통해 다양 한 Office 365 서비스에 대 한 효과적으로 사용 합니다. 네트워크에서 라우팅의이 상태는 내부 네트워크 토폴로지를 설계 하는 방법에 중요 한 변경이 나타낼 수 있습니다.
  
 **상태:** 전체 가이드 v2
  
핵심 네트워크와 인터넷에 삽입 하는 경로 사용 하 여 두 전용된 회선을 통해 사용할 수 있는 라우팅을 필요 없이의 네트워크 복잡성에 대 한 수용 하기 위해 Office 365 구현에 대 한 사용자 ExpressRoute를 신중 하 게 계획 해야 합니다. 및 팀 세부 계획 및이 가이드에서 테스트를 수행 하지 않아도, 하는 경우는 간헐적으로 발생 하는 높은 위험 수준 또는 ExpressRoute 회선을 사용 하는 경우 Office 365에 대 한 연결의 총 손실 서비스입니다.
  
성공적인 구현 해야할 인프라 요구 사항 분석, 상세 네트워크 평가 통해 이동 하 고 디자인, 신중 하 게 미리 구성 된 고 통제 된 방식으로 롤아웃 계획 및 구축 자세한 유효성 검사 및 테스트 계획 해야 합니다. 분산 된 대규모 환경에 대 한은 몇 개월에 걸쳐 구현을 참조 하는 경우가 종종 발생 하지 않습니다. 이 가이드는 대비할 수 있도록 설계 되었습니다.
  
성공적인 대규모 배포의 경우 6 개월 계획에서 사용 하 고 자주 네트워킹, 방화벽 및 프록시 서버 관리자, Office 365 관리자, 보안, 최종 사용자 지원, 프로젝트를 포함 하 여 조직에서 다양 한 영역에서 팀 구성원을 포함 될 수 있습니다. 관리 및 프로젝트 스폰서 합니다. 계획 프로세스에 대 한 투자 가동 중지 시간이 나 복잡 하 고 비용이 많이 드는 문제를 해결 하는 배포 오류를 겪을 수 있는 가능성을 줄일 수 있습니다.
  
다음과 같은 필수 구성 요소가이 구현 가이드를 시작 하기 전에 완료 될 예정입니다.
  
1. ExpressRoute는 권장 하 고 승인 하는 경우를 결정 하는 네트워크 평가 완료 했습니다.

2. ExpressRoute 네트워크 서비스 공급자를 선택 했습니다. [ExpressRoute 파트너 및 피어 링 위치](https://azure.microsoft.com/documentation/articles/expressroute-locations/)하는 방법에 대 한 세부 정보를 확인 합니다.

3. 했을 때 이미 잘 읽고 이해 [ExpressRoute 설명서](https://azure.microsoft.com/documentation/services/expressroute/) 및 내부 네트워크는 ExpressRoute 필수 구성 요소가 끝을 충족 합니다.

4. 팀의 모든 공용 지침 및 설명서의 읽기 [https://aka.ms/expressrouteoffice365](https://aka.ms/expressrouteoffice365), [https://aka.ms/ert](https://aka.ms/ert)를 포함 하 여 중요 한 기술 세부 이해 하기 위해 채널 9에서 [Office 365 교육에 대 한 Azure ExpressRoute](https://channel9.msdn.com/series/aer) 시리즈를 조사 하 고:

      - SaaS 서비스의 인터넷 종속성을 지정 합니다.

      - 비대칭 경로 방지 하 고 복잡 한 라우팅을 처리 하는 방법입니다.

      - 경계 보안, 가용성 및 응용 프로그램 수준 컨트롤을 통합 하는 방법입니다.

## <a name="begin-by-gathering-requirements"></a>요구 사항 수집 하 여 시작
<a name="requirements"> </a>

시작 하는 기능 및 조직 내에서 채택할 것을 계획 하는 서비스를 확인 합니다. 다른 Office 365 서비스의 기능 사용 되 고 네트워크에 있는 위치 이러한 기능을 사용 하는 사람을 호스트를 결정 해야 합니다. 네트워크 되는 특성을 추가 해야하는 시나리오의 카탈로그를 함께 이러한 시나리오의 각 필요 합니다. 예: 인바운드 및 아웃 바운드 네트워크 트래픽 흐름 및 경우 Office 365 끝점은 사용할 수 있는 ExpressRoute을 통해 또는 하지 않습니다.
  
조직의 요구 사항을 수집 합니다.
  
- 조직에서 사용 하는 Office 365 서비스에 대 한 인바운드 및 아웃 바운드 네트워크 트래픽을 카탈로그 합니다. 다른 Office 365 시나리오를 필요로 하는 흐름에 대 한 설명을 Office 365 Url 및 IP 주소 범위 페이지를 참조 하십시오.

- 내부 WAN 백본 및 토폴로지에 대 한 세부 정보, 위성 사이트, 네트워크 경계 탈출 포인트 및 프록시 서비스를 라우팅, 마지막 마일 사용자 연결의 연결을 표시 하는 기존 네트워크 토폴로지에 대 한 설명서를 수집 합니다.

  - Office 365 및 기타 Microsoft 서비스에 연결 하는, 인터넷 및 제안 된 ExpressRoute 연결 경로 모두 표시 되는 네트워크 다이어그램에서 인바운드 서비스 끝점을 식별 합니다.

  - 모든 지리적 사용자 위치 및 위치는 위치에 아직 인터넷에는 송신 및 ExpressRoute 피어 링 위치는 탈출 해야 하는 위치는 제안 된 함께 간의 WAN 연결을 식별 합니다.

  - 프록시, 방화벽, 등의 모든에 지 장치를 식별 하 고 카탈로그 페이지의 관계에 흐름 인터넷 및 ExpressRoute 위로 이동 합니다.

  - 최종 사용자가 인터넷과 ExpressRoute 모두 흐름에 대 한 직접 라우팅 또는 간접 응용 프로그램 프록시를 통해 Office 365 서비스에 액세스 하는지 여부를 문서화 합니다.

- 테 넌 트의 위치를 추가 하 고 충족-나에 게 네트워크 다이어그램에 위치 합니다.

- 예상 및 관찰 된 네트워크 성능 및 대기 시간 특성 주요 사용자 위치에서 Office 365를 예측 합니다. Office 365는 서비스의 전역 및 분산 집합 하 고 사용자가 자신의 테 넌 트의 위치와에서 다른 될 수 있는 위치에 연결할 모방 일에 유의 합니다. 이러한 이유로 측정 하 고 ExpressRoute 및 인터넷 연결을 통해 사용자와 Microsoft 글로벌 네트워크의 가장 가까운 가장자리 사이의 대기 시간을 최적화 하는 것이 좋습니다. 이 작업을 지원 하기 위해 네트워크 평가 대 한 결과 사용할 수 있습니다.

- 회사 네트워크 보안 및 새 ExpressRoute 연결 된 충족 하는 고가용성 요구 사항을 나열 합니다. 예, 어떻게 수행 사용자를 계속 받을 인터넷 탈출 또는 ExpressRoute 회로 오류 발생 시 Office 365에 대 한 액세스 합니다.

- 문서는 인바운드 및 아웃 바운드 Office 365 네트워크 흐름 인터넷 경로 사용 하면 하 고 ExpressRoute 사용할 하는 키를 누릅니다. 사용자의 지리적 위치 및 온-프레미스 네트워크 토폴로지에 대 한 세부 정보는 구체적인 다른 사용자가 한 명 위치에서 일치 하지 않아도 계획이 필요할 수 있습니다.

### <a name="catalog-your-outbound-and-inbound-network-traffic"></a>카탈로그에 아웃 바운드 및 인바운드 네트워크 트래픽
<a name="trafficCatalog"> </a>

라우팅 및 기타 네트워크 복잡성을 최소화 하려면만 사용 하는 ExpressRoute Office 365에 대 한 규정 요구 사항으로 인해 또는 네트워크 평가의 결과 전용된 연결을 통해 이동 하는 데 필요한 네트워크 트래픽 흐름에 대 한 하는 것이 좋습니다. 또한 구현 프로젝트의 서로 다른 프로세스와 다른 시점으로 ExpressRoute 라우팅 및 접근 방식 아웃 바운드 및 인바운드 네트워크 트래픽 흐름의 범위를 준비 하는 것이 좋습니다. 아웃 바운드 네트워크 트래픽 흐름 및 인터넷을 통해 인바운드 네트워크 트래픽 흐름 토폴로지 복잡성과 추가 소개 (영문)의 위험에 증가 제어 하는 데 도움이 수 나가기 방금 사용자 시작에 대 한 ExpressRoute Office 365에 대 한 배포 비대칭 라우팅 방법을 사용 합니다.
  
네트워크 트래픽 카탈로그 온-프레미스 네트워크와 Microsoft 간의 있어야 하는 모든 인바운드 및 아웃 바운드 네트워크 연결의 목록에 포함 되어야 합니다.
  
- 아웃 바운드 네트워크 트래픽 흐름은 여기에서 연결이 시작 됩니다 온-프레미스 환경에서와 같이 내부 클라이언트 또는 Microsoft 서비스의 대상 서버에서 모든 시나리오입니다. 이러한 연결은 Office 365에 직접 또는 간접적 때 연결 함으로 프록시 서버, 방화벽 또는 다른 네트워킹 장치를 통해 경로에서 Office 365와 같은 수 있습니다.

- 인바운드 네트워크 트래픽 흐름은 Microsoft 클라우드에서 온-프레미스 호스트에 대 한 연결을 시작 하는 있는 모든 시나리오입니다. 이러한 연결은 일반적으로 방화벽 및 외부에서 발생 한 흐름에 대 한 고객 보안 정책 요구 하는 기타 보안 인프라를 통해 이동 해야 합니다.

[Office 365에 대 한 ExpressRoute와 라우팅](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408) 서비스는 인바운드 트래픽을 보냅니다를 찾아서 [Office 365에서에서 **Office 365에 대 한 ExpressRoute** 를 표시 하는 열에 대 한 결정 하는 문서의 **보장 경로 대칭** 섹션을 읽으십시오 끝점](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) 참조 (영문) 문서를 나머지 연결 정보를 확인 합니다.
  
아웃 바운드 연결을 필요로 하는 각 서비스에 대 한 네트워크 라우팅, 프록시 구성, 패킷 검사를 포함 하 여 서비스에 대 한 계획 된 연결을 설명 하기 위해 알면 및 대역폭 요구 합니다.
  
인바운드 연결을 필요로 하는 각 서비스에 대 한 추가 정보가 필요 합니다. Microsoft 클라우드의 서버는 온-프레미스 네트워크에 대 한 연결을 설정 합니다. 연결을 제대로 설정할 확인, 원하는;을 포함 하 여이 연결의 모든 측면을 설명 하기 위해 이러한 인바운드 연결을 허용할 서비스에 대 한 공용 DNS 항목은 CIDR 서식이 지정 된는 ISP 장비는 작업이 포함 되는 IPv4 IP 주소 및 어떻게 인바운드 NAT 또는 이러한 연결에 대 한 원본 NAT 처리 됩니다.
  
인바운드 연결을 검토 하 여 인터넷을 통해 연결 중인 여부에 관계 없이 해야 또는 비대칭 라우팅이 이루어지도록 ExpressRoute 하지 않은 도입 되었습니다. 경우에 따라 온-프레미스 끝점을 Office 365 서비스 5 월에 대 한 인바운드 연결도 시작 해야 다른 Microsoft 및 비 Microsoft 서비스에서 액세스할 수 있습니다. 것이 가장 중요 ExpressRoute 라우팅 Office 365 목적을 위해 이러한 서비스를 사용 하면 다른 시나리오 중단 하지 않습니다. 대부분의 경우 소스 기반 ExpressRoute 사용 하도록 설정한 후 Microsoft에서 인바운드 흐름 대칭으로 유지 되도록 하려면 NAT와 같은 고객이 내부 네트워크에 특정 변경을 구현 해야 합니다.
  
필요한 세부 수준 예제는 다음과 같습니다. 이 경우 Exchange 하이브리드 ExpressRoute을 통해 온-프레미스 시스템에 라우팅합니다.

|**Connection 속성**|**값**|
|:-----|:-----|
|**네트워크 트래픽 방향** <br/> |인바운드  <br/> |
|**서비스** <br/> |Exchange 하이브리드  <br/> |
|**공용 Office 365 끝점 (원본)** <br/> |Exchange Online (IP 주소)  <br/> |
|**공용 온-프레미스 끝점 (대상)** <br/> |5.5.5.5  <br/> |
|**공용 (인터넷) DNS 항목** <br/> |Autodiscover.contoso.com  <br/> |
|**이 온-프레미스 끝점에 사용할 다른 (비-Office 365) Microsoft 서비스에 의해** <br/> |아니요  <br/> |
|**인터넷에서 사용자/시스템에 사용 될이 온-프레미스 끝점** <br/> |예  <br/> |
|**공용 끝점을 통해 게시 되는 내부 시스템** <br/> |Exchange Server 클라이언트 액세스 역할 (온-프레미스) 192.168.101, 192.168.102, 192.168.103  <br/> |
|**공용 끝점의 IP 광고** <br/> |**인터넷**: 5.5.0.0/16  <br/> **ExpressRoute를**: 5.5.5.0/24  <br/> |
|**보안/경계 컨트롤** <br/> |**인터넷 경로**: DeviceID_002  <br/> **ExpressRoute 경로**: DeviceID_003  <br/> |
|**고가용성** <br/> |액티브/액티브 2 지리적으로 분산 중복 별  <br/> ExpressRoute 회로-시카고 및 달라스  <br/> |
|**경로 대칭 컨트롤** <br/> |**방법**: NAT 원본  <br/> **인터넷 경로**: 소스 NAT 인바운드 192.168.5.5에 대 한 연결  <br/> |**ExpressRoute 경로**: 192.168.1.0 (Chicago) 및 192.168.2.0 (달라스)에 대 한 원본 NAT 연결  <br/> |

아웃 바운드만 되는 서비스의 예제는 다음과 같습니다.
|**Connection 속성**|**값**|
|:-----|:-----|
|**네트워크 트래픽 방향** <br/> |아웃바운드  <br/> |
|**서비스** <br/> |SharePoint Online  <br/> |
|**온-프레미스 끝점 (원본)** <br/> |사용자 워크스테이션  <br/> |
|**공용 Office 365 끝점 (대상)** <br/> |SharePoint Online (IP 주소)  <br/> |
|**공용 (인터넷) DNS 항목** <br/> |\*. sharepoint.com (및 추가 Fqdn)  <br/> |
|**CDN 조회** <br/> |cdn.sharepointonline.com (또는 추가 Fqdn)-CDN 공급자가 유지 관리 하는 IP 주소)  <br/> |
|**IP 광고 및 NAT 사용** <br/> |**인터넷 경로/소스 NAT**: 1.1.1.0/24  <br/> **ExpressRoute 경로/소스 NAT**: 1.1.2.0/24 (Chicago) 및 1.1.3.0/24 (달라스)  <br/> |
|**연결 메서드** <br/> |**인터넷**: 계층 7 프록시 (.pac 파일)를 통해  <br/> **ExpressRoute**: 직접 라우팅 (프록시 없음)  <br/> |
|**보안/경계 컨트롤** <br/> |**인터넷 경로**: DeviceID_002  <br/> **ExpressRoute 경로**: DeviceID_003  <br/> |
|**고가용성** <br/> |**인터넷 경로**: 중복 인터넷 송신  <br/> **ExpressRoute 경로**: 2 지리적으로 분산 중복 ExpressRoute 회로-시카고 및 달라스 별 액티브/액티브 ' 곤란 한 ' 라우팅  <br/> |
|**경로 대칭 컨트롤** <br/> |**방법**: 모든 연결에 대 한 NAT 소스  <br/> |

### <a name="your-network-topology-design-with-regional-connectivity"></a>지역 연결이 설정 된 네트워크 토폴로지 디자인
<a name="topology"> </a>

서비스 및 해당 연결 된 네트워크 트래픽 흐름을 이해 하 고 나면 이러한 새 연결 요구 사항을 통합 하 고 Office 365에 대 한 ExpressRoute를 사용 하 여 할 변경 된 내용을 설명 하는 네트워크 다이어그램을 만들 수 있습니다. 다이어그램에는 다음과 같습니다.
  
1. 모든 사용자 위치에서 Office 365 및 기타 서비스를 액세스 하는 위치입니다.

2. 모든 인터넷 및 ExpressRoute 탈출 포인트입니다.

3. 아웃 바운드 및 인바운드 하는 모든 장치 라우터, 방화벽, 응용 프로그램 프록시 서버 및 침입 검색/방지를 포함 하는 네트워크 및 로그 아웃할 때 연결을 관리 합니다.

4. ADFS 웹 응용 프로그램 프록시 서버에서 연결을 허용 하는 내부 ad FS 서버와 같은 모든 인바운드 트래픽에 대 한 내부 대상입니다.

5. 광고가 모든 IP 서브넷의 카탈로그

6. 사용자가 Office 365에서 액세스 하 고는 모임 나열 하는 여기에서 각 위치를 식별-나에 게 ExpressRoute에 사용 되는 위치입니다.

7. 위치 및 일부 ExpressRoute에서 얻은 Microsoft IP 접두사 수락 수를 내부 네트워크 토폴로지를 필터링 하 고 전파 합니다.

8. 네트워크 토폴로지는 각 네트워크 세그먼트의 지리적 위치 및 ExpressRoute 및/또는 인터넷을 통해 Microsoft 네트워크에 연결 하는 방법을 보여주는 해야 합니다.

아래 다이어그램 있는 사람들이 사용할 Office 365에서 Office 365로 인바운드 및 아웃 바운드 라우팅 광고와 함께 각 위치를 보여줍니다.
  
![ExpressRoute 지역 지리적 모임-나에 게](media/d866b36b-49bf-416b-af1b-d054e24989d2.png)
  
아웃 바운드 트래픽에 대 한 사람 세가지 방법 중 하나에서 Office 365에 액세스 합니다.
  
1. 모임을 통해-me 캘리포니아의 사용자를 위한 북미에서의 위치입니다.

2. 모임을 통해-me 홍콩 특별 행정구의 사용자를 위한 홍콩 특별 행정구에서의 위치입니다.

3. 여기에서 더 적은 수의 사용자 및 없음 ExpressRoute 회로 프로 비전 방글라데시에서 인터넷을 통해.

![지역 다이어그램에 대 한 아웃 바운드 연결](media/8319943d-08f0-4781-9ef3-d23de2ad4671.png)
  
마찬가지로, Office 365의 인바운드 네트워크 트래픽을 세가지 방법 중 하나를 반환 합니다.
  
1. 모임을 통해-me 캘리포니아의 사용자를 위한 북미에서의 위치입니다.

2. 모임을 통해-me 홍콩 특별 행정구의 사용자를 위한 홍콩 특별 행정구에서의 위치입니다.

3. 여기에서 더 적은 수의 사용자 및 없음 ExpressRoute 회로 프로 비전 방글라데시에서 인터넷을 통해.

![지역 다이어그램에 대 한 인바운드 연결](media/d6d6160d-bf28-4de3-a787-186c7432b306.png)
  
### <a name="determine-the-appropriate-meet-me-location"></a>적절 한 모임 결정-나에 게 위치

모임 선택-나에 게 ExpressRoute 회로 Microsoft 네트워크에 네트워크를 연결 하는 실제 위치는 위치는 사용자가에서 Office 365에 액세스할 수 있는 위치에 따라 영향을 받습니다. 제공 하는 SaaS,으로 Office 365 IaaS 또는 PaaS 지역 모델에서 Azure는 동일한 방식으로 작동 하지 않습니다. 대신 Office 365 사용자가 여러 데이터 센터와 같은 위치 또는 사용자의 테 넌 트 호스팅되는 지역에 반드시 아닐 수도 있는 영역 끝점에 연결할 할 수 있는 된 분산된 집합, 공동 작업 서비스입니다.
  
즉, 모임을 선택할 때 해야하는 가장 중요 한 고려 사항-나에 게 Office 365에 대 한 ExpressRoute에 대 한 위치에서 조직의 사용자가 연결 하는 위치는 합니다. 일반적인 권장 사항과 최적의 Office 365 연결은 Office 365 서비스에 대 한 사용자 요청 전달 됩니다 Microsoft 네트워크에 가장 짧은 네트워크 경로 통해 있도록 라우팅, 구현에 대 한이 또한 되 고 이라고 ' 곤란 한 ' 라우팅. 대부분의 Office 365 사용자가 하나 또는 두 위치에 있으면 모임을 선택 하는 예-나에 게 해당 사용자의 위치를 가장 가까운 근접 한 위치에 있는 위치 최적의 디자인을 만듭니다. 회사의 많은 다른 지역에서 대규모 사용자 수가 있으면 하려는 경우 여러 ExpressRoute 회로 것을 고려 하 고 충족-나에 게 위치입니다. 일부 사용자 위치에 대 한 작업 Microsoft 네트워크 및 Office 365에 대 한 가장 짧은/가장 최적의 경로은 내부 사용자 WAN 및 ExpressRoute 모임 통해 되지 않을 수 있습니다-가리키는 me 하지만 인터넷을 통해 합니다.
  
종종 시간, 여러 모임 가지-내 사용자에 게 상대 근접 영역 내에서 선택할 수 있는 위치입니다. 결정을 안내 하는 다음 표를 채웁니다.

|**계획 된 ExpressRoute 모임-me 캘리포니아 및 뉴욕 위치에**||
|:-----|:-----|
|위치  <br/> |사용자 수  <br/> |인터넷 송신을 통해 Microsoft 네트워크 대기 시간 예상  <br/> |ExpressRoute 통해 Microsoft 네트워크에 예상된 대기 시간  <br/> |
|로스앤젤레스  <br/> |10,000  <br/> |~ 15ms  <br/> |~ 10ms (실리콘 밸리)를 통해  <br/> |
|워싱턴 DC  <br/> |15, 000  <br/> |~ 20ms  <br/> |~ 10ms (뉴욕)를 통해  <br/> |
|달라스  <br/> |5,000  <br/> |~ 15ms  <br/> |~ 40ms (뉴욕)를 통해  <br/> |

Office 365 영역이 표시 되는 전역 네트워크 아키텍처, ExpressRoute 네트워크 서비스 공급자 충족 되 면-나에 게 위치에 따라 사용자의 수량 및 위치, 개발 된, 모든 최적화를 설정할 수 경우 식별 하기 위해 사용할 수 있습니다. 또한 표시 될 전역 헤어핀 네트워크 연결은 모임에 나오고 트래픽을 멀리 떨어져 있는 위치를 회람 하는 위치-나에 게 위치입니다. 글로벌 네트워크에서 헤어핀 계속 하기 전에 설정을 수 해야 발견 되는지 합니다. 다른 모임 찾기 하나-나에 게 위치 또는 사용 하 여 선택적 인터넷 소 탈출 포인트의 헤어핀을 방지 하기 위해 합니다.
  
첫번째 다이어그램 북미에서 두 실제 위치와 고객의 예를 보여줍니다. 사무실 위치, Office 365 테 넌 트 위치에 대 한 정보를 볼 수 및 ExpressRoute에 대 한 여러 선택 충족-나에 게 위치입니다. 이 예제에서는 고객의 모임이 선택한-me 순서로 두 원칙에 기반 하는 위치:
  
1. 조직에서 사용자를 가장 가까운 근접 합니다.

2. Office 365가 호스팅되는 Microsoft 데이터 센터에 근접에서 가장 가까운 합니다.

![ExpressRoute 미국 지역 모임-나에 게](media/5ec38274-b317-4ec1-91c8-90c2a7fd32ca.png)
  
약간이 개념을 확장 하면 한 자세한 내용은, 두번째 다이어그램에서 볼 수 있는 예제 다국적 고객 비슷한 정보 및 의사 결정에 직면 합니다. 이 고객 지역에 자신의 메모리 사용량이 증가에 초점을 맞춥니다 10 명의 소규모 팀만 함께 방글라데시에 작은 사무실을 있습니다. 모임 방법이-나에 게 체나 및 Office 365와 Microsoft 데이터 센터에서의 위치에에서 호스트 체나 하므로 모임-나에 게 위치는 의미가 있습니다. 그러나 10 명의 사용자에 대 한 추가 회로 비용을 들이지가 부담을 줄여주. 네트워크 연결을 보면으로 네트워크를 통해 네트워크 트래픽을 보낼 관련 된 대기 시간을 다른 ExpressRoute 회로 구입 하려면 자본 지출 보다 더 효율적으로 되었는지 확인 하려면 필요 합니다.
  
방글라데시에 10 명의 사용자가 자신의 네트워크 트래픽을 소개 다이어그램의 결과 따르면 하 고 재현가 내부 네트워크에서 라우팅 것 보다 Microsoft 네트워크에 인터넷을 통해 전송 된 성능을 개선 하려면 위의 겪을 수는 또는 아래 있습니다.
  
![지역 다이어그램에 대 한 아웃 바운드 연결](media/8319943d-08f0-4781-9ef3-d23de2ad4671.png)
  
## <a name="create-your-expressroute-for-office-365-implementation-plan"></a>Office 365 구현 계획에 대 한 사용자 ExpressRoute 만들기
<a name="implementation"> </a>

구현 계획에는 다음과 같은 네트워크에서 다른 모든 인프라를 구성 하는의 세부 정보 뿐아니라 ExpressRoute 구성의 기술 정보 포괄적 이어야 합니다.
  
- ExpressRoute와 인터넷 사이의 분할 하는 서비스를 계획 합니다.

- 대역폭, 보안, 고가용성 및 장애 조치에 대 한 계획 합니다.

- 인바운드 및 아웃 바운드 라우팅, 다른 위치에 대 한 적절 한 라우팅 경로 최적화를 포함 하 여 디자인

- 네트워크에 ExpressRoute 경로 광고가 정도 결정 하 고 인터넷 이나 ExpressRoute 경로;를 선택 하는 클라이언트에 대 한 메커니즘 이란 라우팅 또는 응용 프로그램 프록시를 직접 예입니다.

- [보낸 사람이 정책 프레임 워크](https://technet.microsoft.com/library/dn789058%28v=exchg.150%29.aspx) 항목을 포함 하 여 DNS 레코드 변경을 계획 합니다.

- 아웃 바운드 및 인바운드 원본 NAT.를 포함 하 여 NAT 전략 계획

### <a name="plan-your-routing-with-both-internet-and-expressroute-network-paths"></a>인터넷 및 ExpressRoute 네트워크 경로 모두 사용 하 여 라우팅 계획
<a name="paths"> </a>

- 초기 배포에 대 한 인바운드 전자 메일 또는 하이브리드 연결 등의 모든 인바운드 서비스는 인터넷을 사용 하는 것이 좋습니다.

- 최종 사용자 클라이언트 LAN 라우팅, [PAC/WPAD 파일을 구성](https://aka.ms/manageo365endpoints)하는 등, 기본 경로, 프록시 서버 및 BGP 경로 광고를 계획 합니다.

- 경계 라우팅, 프록시 서버, 방화벽 및 클라우드 프록시를 포함 하 여 계획 합니다.

### <a name="plan-your-bandwidth-security-high-availability-and-failover"></a>대역폭, 보안, 고가용성 및 장애 조치 계획
<a name="availability"> </a>

Office 365의 각 주요 작업에 필요한 대역폭에 대 한 계획을 만듭니다. 비즈니스 온라인 대역폭 요구 사항에 대 한 Exchange Online, SharePoint Online 및 Skype를 개별적으로 예측 합니다. Exchange Online 및 시작 위치로 비즈니스용 Skype 제공 하 고 예측 계산기를 사용할 수 있습니다. 그러나 사용자 프로필 및 위치의 대표 샘플으로 파일럿 테스트는 완벽 하 게 하 여 조직의 대역폭 요구 사항을 이해 하는 데 필요한.
  
각 인터넷 및 계획에 ExpressRoute 탈출 위치에서 보안을 처리 하는 방법을 추가, Office 365에 대 한 모든 ExpressRoute 연결 공용 피어 링을 사용 하 고 외부에 연결 하 여 회사 보안 정책에 따라 보호할 수는 여전히 기억 경고 표시 됩니다.
  
세부 정보 계획에을 추가 하는 방법에 대 한 사용자의 영향 받게될 어떤 유형의 중단 및 방법을 사람들 가장 간단한 방식으로 전체 용량으로 해당 작업을 수행할 수 있게 됩니다.
  
#### <a name="plan-bandwidth-requirements-including-skype-for-business-requirements-on-jitter-latency-congestion-and-headroom"></a>Skype를 포함 하 여 지터, 대기 시간, 정체, 및 여유 공간을 갖는 비즈니스 요구 사항에 대 한 대역폭 요구 사항 계획
  
비즈니스 온라인 용 Skype [미디어 품질 및 비즈니스 온라인 용 Skype에서 네트워크 연결 성능](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917)문서에서 자세히 설명 하는 특정 추가 네트워크 요구 사항에도 있습니다.
  
[Office 365에 대 한 ExpressRoute와 네트워크 계획](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd)에 대 한 **대역폭 Azure ExpressRoute에 대 한 계획** 섹션을 읽어보십시오.
  
파일럿 사용자와 대역폭 평가 수행 하는 경우에 가이드;를 사용 하 여 다음 작업을 수 있습니다. [초기 계획 및 성능 기록을 사용 하 여 office 365 성능 조정](https://support.office.com/article/Office-365-performance-tuning-using-baselines-and-performance-history-1492cb94-bd62-43e6-b8d0-2a61ed88ebae)합니다.
  
#### <a name="plan-for-high-availability-requirements"></a>고가용성 요구 사항에 대 한 계획
  
요구 사항에 맞게 업데이트 된 네트워크 토폴로지 다이어그램에이 통합 하는 고가용성에 대 한 계획을 만듭니다. **고가용성 및 장애 조치 Azure ExpressRoute와** [Office 365에 대 한 ExpressRoute와 네트워크](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd)계획 섹션을 읽어보십시오.
  
#### <a name="plan-for-network-security-requirements"></a>네트워크 보안 요구 사항에 대 한 계획
  
네트워크 보안 요구 사항을 충족 하 고 업데이트 된 네트워크 토폴로지 다이어그램에이 통합 하는 계획을 만듭니다. [Office 365에 대 한 ExpressRoute와 네트워크 계획](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd)에서 **Office 365 시나리오에 대 한 Azure ExpressRoute에 보안 컨트롤을 적용** 섹션을 읽어보십시오.
  
### <a name="design-outbound-service-connectivity"></a>아웃 바운드 서비스 연결을 디자인 합니다.
<a name="outbound"> </a>

Office 365에 대 한 ExpressRoute 친숙 한 되지 않을 수 있는 *아웃 바운드* 네트워크 요구 사항에 있습니다. 특히, IP 주소 탭과 Office 365에 사용자 및 네트워크를 나타내는 역할을 Microsoft에 대 한 아웃 바운드 네트워크 연결에 대 한 원본 끝점을 아래에서 설명 하는 특정 요구 사항을 따라야 합니다.
  
1. 끝점을 회사 또는 ExpressRoute 연결을 제공 하는 통신 회사에 등록 된 공용 IP 주소 여야 합니다.

2. 끝점은 ExpressRoute 하 여 Microsoft에 보급 하 고 유효성을 검사 하 고 허용 이어야 합니다.

3. 같거나 보다 기본 라우팅 메트릭 사용 하 여 인터넷에 끝점을 보급 수 해야 합니다.

4. 끝점을 ExpressRoute을 통해 구성 되지 않은 Microsoft 서비스에 대 한 연결에 대 한 사용 되어야 합니다.

네트워크 디자인 이러한 요구 하는 경우는 높은 위험 수준에 사용자는 Office 365 및 holing 검정 경로 또는 비대칭 라우팅으로 인해 다른 Microsoft 서비스에 연결 오류를 경험 하는 방법이 있습니다. 이 Microsoft 서비스에 대 한 요청 ExpressRoute를 통해 라우팅되는 하지만 인터넷을 통해 다시 또는 그 반대의 경우도 마찬가지 응답 라우팅되는 응답 방화벽 같은 상태 저장 네트워크 장치에 의해 삭제 된 때 발생 합니다.
  
위의 요구를 충족 하기 위해 사용할 수 있는 가장 일반적인 방법은 원본 네트워크의 일부로 구현 또는 ExpressRoute 사업자에서 제공 되는 NAT를 사용 하는 것입니다. 원본 NAT를 사용 하면 자세한 내용 및 개인 IP 주소 지정 인터넷 네트워크의 ExpressRoute에서 추상 및; 적절 한 IP 경로 광고를 더불어는 메커니즘을 제공 쉽게 경로 대칭 되도록 합니다. ExpressRoute 피어 링 위치에만 적용 되는 상태 저장 네트워크 장치를 사용 하는 경우에 각 ExpressRoute 경로 대칭 되도록 피어 링에 대 한 별도 NAT 풀을 구현 해야 합니다.
  
[ExpressRoute NAT 요구 사항](https://azure.microsoft.com/documentation/articles/expressroute-nat/)에 대해 자세히 알아보십시오.
  
네트워크 토폴로지 다이어그램 아웃 바운드 연결에 대 한 변경 내용에 추가 합니다.
  
### <a name="design-inbound-service-connectivity"></a>인바운드 서비스 연결을 디자인 합니다.
<a name="inbound"> </a>

대부분의 Office 365 엔터프라이즈 배포 가정 합니다. 온-프레미스 서비스를 Office 365에서 인바운드 연결의 일부 폼과 같은 Exchange, SharePoint 및 Skype 비즈니스 하이브리드 시나리오, 사서함 마이그레이션 및 ADFS를 사용 하 여 인증에 대 한 인프라입니다. 때 ExpressRoute 아웃 바운드 연결에 대 한 온-프레미스 네트워크와 Microsoft 간의 추가 라우팅 경로 사용 하도록 설정 하면, 이러한 인바운드 연결 수 실수로 수의 영향을 받는 비대칭 라우팅, 이러한 흐름에 계속 포함 하려는 경우에 인터넷을 사용 합니다. 인터넷에 아무런 영향을 주지 기반 온-프레미스 시스템에 Office 365에서 인바운드 흐름은 되도록 아래에서 설명 하는 몇가지 예방 조치를 사용 하는 것이 좋습니다.
  
인바운드 네트워크 트래픽 흐름에 대 한 비대칭 라우팅의 위험을 최소화 하려면 ExpressRoute에 대 한 라우팅 가시성 없는 네트워크의 세그먼트로 라우팅되는 자신이 전에 원본 NAT를 사용 해야 모든 인바운드 연결 합니다. 들어오는 연결 함께 사용할 수 있는 네트워크 세그먼트에 원본 NAT 없이 ExpressRoute에 대 한 라우팅 가시성, 하는 경우 Office 365에서 발생 한 요청은 인터넷에서 들어감 하지만 Office 365로 돌아가 대 한 응답은 ExpressRoute 것을 선호 합니다. 비대칭 라우팅 인해 발생 하는 Microsoft 네트워크에 다시 네트워크 경로입니다.
  
이 요구 사항을 충족 하기 위해 다음과 같은 구현 패턴 중 하나를 고려할 수 있습니다.
  
1. 온-프레미스 시스템에 경로에 대 한 분산 인터넷에서 로드 또는 방화벽와 같은 네트워킹 장비를 사용 하 여 내부 네트워크로 라우팅되는 요청 하기 전에 원본 NAT를 수행 합니다.

2. 확인 ExpressRoute 경로 네트워크 세그먼트 앞 등의 인바운드 서비스 서버를 종료 하거나 역방향 프록시 시스템을 인터넷 연결 상주 처리 위치에 전파 되지 않습니다.

명시적으로 네트워크에서 이러한 시나리오에 대 한 계정 하 고 모든 인바운드 네트워크 트래픽을 지속적으로 업데이트를 배포 하 고 비대칭 라우팅 운영 위험을 최소화 하기 위해 인터넷 도움말을 통해 흐릅니다.
  
사용할 수는 있지만 일부 인바운드 흐름 ExpressRoute 연결을 통해 직접를 선택할 수 있습니다. 이러한 시나리오에 대해 다음 추가 고려 사항을 고려 합니다.
  
1. Office 365에만 대상 온-프레미스 끝점을 공용 Ip를 사용 하는 수 있습니다. 즉, 온-프레미스 인바운드 끝점 ExpressRoute을 통해 Office 365에 노출만, 여전히 해야 공용 IP 연결 된 경우에 합니다.

2. 공용 DNS를 사용 하 여 발생 하는 Office 365 서비스 끝점을 온-프레미스를 해결 하려면 수행 하는 모든 DNS 이름 확인 합니다. 즉, 인바운드 서비스 끝점의 FQDN은 인터넷에서 IP 매핑을 등록 해야 합니다.

3. ExpressRoute을 통해 인바운드 네트워크 연결을 받으려면 이러한 끝점에 대 한 공용 IP 서브넷 ExpressRoute을 통해 Microsoft에 보급 될 해야 합니다.

4. 신중 하 게는 적절 한 보안을 확인 하려면 이러한 인바운드 네트워크 트래픽 흐름을 평가 하 고 네트워크 컨트롤 회사 보안 및 네트워크 정책에 맞게 자신에 게 적용 됩니다.

5. 한번 온-프레미스 인바운드 끝점은 ExpressRoute을 통해 Microsoft에 보급, ExpressRoute는 효과적으로 Office 365를 포함 하는 모든 Microsoft 서비스에 대 한 해당 끝점을 기본 설정된 라우팅 경로입니다. 즉, 이러한 끝점 서브넷 Office 365 서비스 및 Microsoft 네트워크에 없는 다른 서비스와의 통신에만 사용 해야 합니다. 그렇지 않은 경우 설계 비대칭 라우팅 여기서 서비스 라우팅하는 것을 선호 하는 다른 Microsoft의 인바운드 연결의 인바운드 ExpressRoute를 통해 반환 경로 인터넷을 사용 하는 동안 발생 합니다.

6. 이벤트는 ExpressRoute에서 회로 또는 충족-me 작동이 중지 위치, 온-프레미스를 확인 하는데 필요한 인바운드 끝점은 별도 네트워크 경로 통해 요청을 수락 하도록 계속 사용할 수 있습니다. 이 광고 서브넷 여러 ExpressRoute 회로 통해 이러한 끝점에 대 한 것일 수 있습니다.

7. 이러한 흐름 방화벽 같은 상태 저장 네트워크 장치를 교차 하는 경우에 특히 ExpressRoute 통해 네트워크를 입력 하는 모든 인바운드 네트워크 트래픽 흐름에 대 한 NAT 소스를 적용 하는 것이 좋습니다.

8. Ad FS 프록시 또는 Exchange 자동 검색 등의 일부 온-프레미스 서비스는 Office 365 서비스와 인터넷에서 사용자의 인바운드 요청을 받을 수 있습니다. 이러한 요청에 대 한 Office 365 인터넷을 통해 사용자의 요청과 동일한 FQDN을 대상 됩니다. 중요 한 라우팅 복잡성을 나타냅니다 ExpressRoute를 사용 하 여 Office 365 연결 강제 실행 하는 동안 이러한 온-프레미스 끝점을 인터넷에서 인바운드 사용자 연결을 허용 합니다. 대부분의 고객에 대 한 ExpressRoute을 통해 이러한 복잡 한 시나리오를 구현 하지 않기 운영 고려 사항으로 인해 합니다. 이 추가 오버 헤드가 포함, 비대칭 라우팅의 위험을 관리 하 고 신중 하 게 여러 차원에서 라우팅 광고 및 정책을 관리 해야 합니다.

### <a name="update-your-network-topology-plan-to-show-how-you-would-avoid-asymmetric-routes"></a>비대칭 경로 방지이 하는 방법을 표시 하려면 네트워크 토폴로지 계획을 업데이트
<a name="asymmetric"> </a>

조직의 사용자 수 원활 하 게 사용 하 여 다른 중요 한 서비스와 Office 365 인터넷에서 비대칭 라우팅을 방지 하려고 합니다. 비대칭 라우팅 발생 하는 두 일반적인 구성은 고객이 됩니다. 이제는 작업을 사용 하 고 이러한 비대칭 라우팅 시나리오 중 하나가 존재할 수를 확인 하려면 계획 이라면 네트워크 구성을 검토 하려면 좋은 시간입니다.
  
먼저, 다음 네트워크 다이어그램와 관련 된 다양 한 상황을 몇 살펴보겠습니다. 이 다이어그램에서는 인바운드 요청을 수신 하는 모든 서버에서에서 ADFS 또는 온-프레미스 하이브리드 서버 새로 저지 데이터 센터에 및 같은 인터넷으로 보급 됩니다.
  
1. 경계 네트워크를 안전 하는 동안 방법이 소스 NAT 들어오는 요청을 사용할 수 있습니다.

2. 새로 만들기 저지 데이터 센터의 서버 인터넷 창과 ExpressRoute 경로 모두 볼 수 있습니다.

![ExpressRoute 연결 개요 (영문)](media/8f074af6-ef38-44e8-bc5a-8b4d981fbb20.png)
  
것 권한도 부여 제안 문제를 해결 하는 방법에 합니다.
  
#### <a name="problem-1-cloud-to-on-premises-connection-over-the-internet"></a>문제 1: 클라우드 인터넷을 통해 온-프레미스 연결 하려면
  
다음 다이어그램에서는 네트워크 구성에는 인터넷을 통해 Microsoft 클라우드의 인바운드 요청에 대 한 NAT를 제공 하지 않습니다 때 사용 된 비대칭 네트워크 경로를 보여줍니다.
  
1. Office 365의 인바운드 요청 공용 DNS에서 온-프레미스 끝점의 IP 주소를 검색 하 고 경계 네트워크에 요청을 보냅니다.

2. 이 문제가 발생 한 구성에서 구성 된 원본 NAT 되었거나 트래픽을 경계 네트워크에서 사용할 수 있는 전송 되므로 실제 원본 IP 주소 반환 대상으로 사용 되 고 있습니다.

  - 네트워크의 서버에 사용 가능한 모든 ExpressRoute 네트워크 연결을 통해 Office 365로 반환 되는 트래픽이 라우팅합니다.

  - 결과 연결이 끊어진된에서 발생 하는 Office 365에 해당 흐름에 대 한 비대칭 경로입니다.

![ExpressRoute Asymetric 라우팅 문제 1](media/9c210c2a-e0ea-4180-8ede-1bf41746ce7a.png)
  
##### <a name="solution-1a-source-nat"></a>솔루션 1a: NAT 원본
  
단순히 추가 (영문) 원본 NAT는 인바운드 요청을이 잘못 구성 된 네트워크를 확인 합니다. 이 다이어그램:
  
1. 들어오는 요청을 새로 저지 데이터 센터의 경계 네트워크를 통해 입력 계속 합니다. 이 시간 원본 NAT가 사용할 수 있습니다.

2. 연관 된 동일한 네트워크 경로 따라 반환에 대 한 응답의 결과로 만들어진 원본 IP 주소 대신 원본 NAT IP 향해 다시 서버 경로에서 응답 합니다.

![ExpressRoute Asymetric 라우팅 솔루션 1](media/0e87a155-f8de-48ed-92ac-27367b727a82.png)
  
##### <a name="solution-1b-route-scoping"></a>솔루션 1b: 경로 범위 지정
  
또는 수도 있습니다 ExpressRoute BGP 접두사 보급 수를 허용 하지 않으려면 해당 컴퓨터에 대 한 대체 네트워크 경로 제거 합니다. 이 다이어그램:
  
1. 들어오는 요청을 새로 저지 데이터 센터의 경계 네트워크를 통해 입력 계속 합니다. 이 시간 ExpressRoute 회로 통해 Microsoft에서 보급 접두사 새로 저지 데이터 센터에 사용할 수 없습니다.

2. 동일한 네트워크 경로 따라 반환에 대 한 응답에 그 결과 사용할 수 있는 유일한 경로 통해 원래 IP 주소와 연결 된 IP 향해 다시 서버 경로에서 응답 합니다.

![ExpressRoute Asymetric 라우팅 솔루션 2](media/9cb4b2bf-7aa6-487a-bc02-e02af8a979f6.png)
  
#### <a name="problem-2-cloud-to-on-premises-connection-over-expressroute"></a>문제 2: 클라우드 ExpressRoute 통해 온-프레미스 연결 하려면
  
다음 다이어그램에서는 네트워크 구성 ExpressRoute을 통해 Microsoft 클라우드의 인바운드 요청에 대 한 NAT를 제공 하지 않습니다 때 사용 된 비대칭 네트워크 경로를 보여줍니다.
  
1. Office 365의 인바운드 요청 DNS에서 IP 주소를 검색 하 고 경계 네트워크에 요청을 보냅니다.

2. 이 문제가 발생 한 구성에서 구성 된 원본 NAT 되었거나 트래픽을 경계 네트워크에서 사용할 수 있는 전송 되므로 실제 원본 IP 주소 반환 대상으로 사용 되 고 있습니다.

  - 네트워크에 컴퓨터 모든 사용 가능한 ExpressRoute 네트워크 연결을 통해 Office 365로 반환 되는 트래픽이 라우팅합니다.

  - Office 365에 대 한 비대칭 연결이 반환이 됩니다.

![ExpressRoute Asymetric 라우팅 문제 2](media/f6fd155b-bbb7-472a-846e-039a99f09913.png)
  
##### <a name="solution-2-source-nat"></a>해결 방법 2: 소스 NAT
  
단순히 추가 (영문) 원본 NAT는 인바운드 요청을이 잘못 구성 된 네트워크를 확인 합니다. 이 다이어그램:
  
1. 들어오는 요청을 계속 뉴욕 데이터 센터의 경계 네트워크를 통해를 입력 합니다. 이 시간 원본 NAT가 사용할 수 있습니다.

2. 연관 된 동일한 네트워크 경로 따라 반환에 대 한 응답의 결과로 만들어진 원본 IP 주소 대신 원본 NAT IP 향해 다시 서버 경로에서 응답 합니다.

![ExpressRoute Asymetric 라우팅 솔루션 3](media/a5d2b90d-a3ec-4047-afbf-6e6e99f376a7.png)
  
### <a name="paper-verify-that-the-network-design-has-path-symmetry"></a>용지는 네트워크 디자인에 경로 대칭 권한이 있는지 확인

이 시점 확인 용지에 구현 계획에는 사용할 Office 365 다양 한 시나리오에 대 한 경로 대칭을 제공 해야 합니다. 사용자는 서비스의 서로 다른 기능을 사용 하는 경우에 수행할 수 있는 특정 네트워크 경로 식별 합니다. 온-프레미스 네트워크 및 경계 장치로 연결 경로; WAN 라우팅 인터넷 또는 ExpressRoute 및 온라인 끝점에 대 한 연결에 로그온 합니다.
  
이전에 조직을 채택 하는 서비스로 식별 된 Office 365 네트워크 서비스를 모두에 대해이 작업을 수행 해야 합니다.
  
두번째 사용자와 경로 통해이 용지 워크를 수행 하는 데 도움이 됩니다. 각 네트워크 홉 필요한 곳에서 그 다음 경로 가져오고 라우팅 경로 함께 친숙 확인 하 고에 대 한 설명입니다. 기억 ExpressRoute 인터넷 기본 경로 보다 저렴 한 경로 제공 하는 Microsoft 서버 IP 주소에 대 한 더 범위가 지정 된 경로 항상 제공 됩니다.
  
### <a name="design-client-connectivity-configuration"></a>디자인 클라이언트 연결 구성
<a name="asymmetric"> </a>

![ExpressRoute PAC 파일 사용](media/7cfa6482-dbae-416a-ae6f-a45e5f4de23b.png)
  
사용 중인 경우 프록시 서버를 인터넷에 대 한 바운드 트래픽은 다음 모든 PAC 조정할 필요가 또는 네트워크에 있는 클라이언트 컴퓨터를 확인 하려면 클라이언트 구성 파일을 전송 하 하지 않고 Office 365에 원하는 ExpressRoute 트래픽을 보낼 제대로 구성 사용 중인 프록시 서버와 일부 Office 365 트래픽을 포함 하는 나머지 트래픽을 관련 프록시에 전송 됩니다. PAC 파일을 예 [끝점을 Office 365 관리](https://aka.ms/manageo365endpoints) 에 대 한 가이드를 읽어보십시오.
  
> [!NOTE]
> 끝점을 자주, 매주으로 자주 변경합니다. 만 최신 상태를 유지 하도록 해야 변경 횟수를 줄일 수 조직에 채택 하는 기능과 서비스를 기준으로 변경 내용을 확인 해야 합니다. RSS 피드 여기서 변경 된 내용을 발표 하 고 레코드를 유지할의 모든 변경 내용, IP 과거 발표 된 주소에서에서 **해당 날짜** 에 유의 해야를, 보급 되거나 유효 날짜에 도달할 때까지 광고에서 제거 될 수 있습니다.
  
## <a name="build-your-deployment-and-testing-procedures"></a>배포 및 테스트 절차를 작성 합니다.
<a name="testing"> </a>

구현 계획 테스트 및 롤백 계획 모두 포함 되어야 합니다. 가장 적은 영향을 주는 계획을 디자인 해야 구현을 예상 대로 작동 하지 않을, 하는 경우 문제를 검색 하기 전에 사용자의 번호입니다. 다음은 일부 높은 수준의 원칙 계획을 고려해 야 합니다.
  
1. 중단을 최소화 하기 위해 네트워크 세그먼트 및 사용자 서비스 딩을 준비 합니다.

2. Traceroute와 경로 테스트 하기 위한 계획 하 고 별도 인터넷 연결 된 호스트에서 TCP 연결 합니다.

3. 가능 하면, 인바운드 및 아웃 바운드 서비스의 테스트 테스트 Office 365 테 넌 트를 사용 하 여는 격리 된 테스트 네트워크에서 수행 되어야 합니다.

      - 또는 테스트를 수행할 수 프로덕션 네트워크에서 고객은 Office 365를 아직 사용 하지 않거나 파일럿에 있습니다.

      - 또는 테스트 수는 테스트에 대해 별도로 설정 하는 프로덕션 중단 하는 동안 수행 하 고 모니터링만 합니다.

      - 또는 테스트 각 계층 3 라우터 노드에서 각 서비스에 대 한 경로 확인 하 여 수행할 수 있습니다. 이 대체 위험을 소개 하는 실제 테스트의 부족 되므로 가능한이 없는 다른 테스트 하는 경우에 사용 해야 합니다.

### <a name="build-your-deployment-procedures"></a>배포 절차를 작성 합니다.

배포 절차는 더 큰 그룹의 사용자에 게 배포 하기 전에 테스트를 허용 하도록 단계별로 소규모 사용자 그룹 롤아웃 해야 합니다. 다음은 ExpressRoute의 배포를 준비 하는 여러 방법입니다.
  
1. Microsoft 피어 링와 ExpressRoute를 설정 하 고 단일 호스트에 대해서만 착신 전환 경로 광고 테스트 목적으로 준비 합니다.

2. 처음에는 단일 네트워크 세그먼트에 ExpressRoute 네트워크에 대 한 경로가 광고 및 네트워크 세그먼트 또는 지역 경로 광고를 확장 합니다.

3. 처음에 대 한 Office 365를 배포 하는 경우에 소수의 사용자에 대 한 ExpressRoute 네트워크 배포 파일럿으로 사용 합니다.

4. 프록시 서버를 사용 하는 경우 테스트 PAC 파일을 추가 하기 전에 소수의 사용자 ExpressRoute 테스트 및 피드백 사용 하 여 직접 또는 구성할 수 있습니다.

구현 계획을 문서화할 각각의 배포 절차를 수행 해야 하는 또는 네트워킹 구성 배포를 사용 하는 명령을 나열 해야 합니다. 네트워크 중단 시간 모든 미리 작성 된 작성 된 배포 계획 및 피어에서 되어야 만들어지는 변경 내용에 도달할 때를 검토 합니다. ExpressRoute의 기술 구성에 대 한 지침을 참조 하십시오.
  
- 전자 메일을 보내는 계속 하는 온-프레미스 서버에 대 한 IP 주소를 변경 했을 때 경우 SPF TXT 레코드를 업데이트 합니다.

- 새 NAT 구성에 맞게 IP 주소를 변경 했을 때 온-프레미스 서버에 대 한 모든 DNS 항목을 업데이트 합니다.

- RSS 모든 라우팅 또는 프록시 구성을 유지 하기 위해 Office 365 끝점 알림을 대 한 피드를 구독 했는지 확인 합니다.

ExpressRoute 배포가 완료 된 후 테스트 계획의 절차를 실행 해야 합니다. 각 절차에 대 한 결과 기록해 야 합니다. 테스트 계획 결과 구현 하지 못했습니다에 따르면 이벤트에 원래 프로덕션 환경으로 롤백에 대 한 절차를 포함 해야 합니다.
  
### <a name="build-your-test-procedures"></a>빌드 테스트 절차

테스트 절차는 ExpressRoute를 사용 하는 Office 365에 대 한 각 아웃 바운드 및 인바운드 네트워크 서비스와는 그렇지 않은 글꼴로 대 한 테스트를 포함 해야 합니다. 절차는 온-프레미스 회사 LAN에 없는 사용자를 포함 하 여 각 고유 네트워크 위치에서 테스트가 포함 되어야 합니다.
  
테스트 작업의 일부 예는 다음과 같습니다.
  
1. 온-프레미스 라우터에서 네트워크 연산자 라우터에 ping을 사용 합니다.

2. 500 명 이상의 Office 365 및 CRM Online IP 주소는 온-프레미스 라우터가 광고 수신의 유효성을 검사 합니다.

3. 인바운드 사용자의 유효성을 검사 하 고 아웃 바운드 NAT ExpressRoute와 내부 네트워크 사이의 작동 합니다.

4. NAT 경로 라우터에서 보급 되 고 유효성을 검사 합니다.

5. ExpressRoute 프로그램 보급된 접두사를 수락 했습니다의 유효성을 검사 합니다.

      - 다음 cmdlet를 사용 하 여 피어 링 광고를 확인 하려면:

      ```PowerShell
      Get-AzureRmExpressRouteCircuitRouteTable -DevicePath Primary -ExpressRouteCircuitName TestER -ResourceGroupName RG -PeeringType MicrosoftPeering
      ```

6. 공용 NAT IP 범위 ExpressRoute 또는 공용 인터넷 네트워크 회선을 통해 Microsoft에 보급 하지 않거나 하지 않은 경우 이전 예제와 같이 더 큰 범위의 특정 하위 집합의 유효성을 검사 합니다.

7. ExpressRoute 회로 쌍, BGP 세션을 모두 실행 되 고 있는지 확인 합니다.

8. NAT의 내부에 단일 호스트를 설정 하 고 새 회로 호스트 outlook.office365.com 통해 연결을 테스트 하려면 ping, tracert 및 tcpping를 사용 합니다. 또는 Wireshark와 같은 도구를 사용할 수 또는 하면 유효성을 검사 하려면 MSEE 미러된 포트에서 Microsoft 네트워크 모니터 3.4는 outlook.office365.com와 연결 된 IP 주소에 연결할 수 있습니다.

9. Exchange Online에 대 한 응용 프로그램 수준 기능을 테스트 합니다.

  - 테스트 Outlook는 Exchange Online에 연결 하 고 전자 메일 보내기/받기 수 있습니다.

  - 테스트 Outlook이 온라인 모드를 사용할 수 있습니다.

  - Smartphone 연결 하 고 보내기/받기 기능을 테스트 합니다.

10. SharePoint Online에 대 한 응용 프로그램 수준 기능을 테스트 합니다.

  - 비즈니스 동기화 클라이언트에 대 한 OneDrive를 테스트 합니다.

  - SharePoint Online 웹 액세스를 테스트 합니다.

11. 비즈니스 호출 시나리오에 대 한 Skype에 대 한 응용 프로그램 수준 기능을 테스트 합니다.

  - [최종 사용자가 시작한 초대] 인증 된 사용자로 전화 회의에 참가 합니다.

  - [MCU에서 보낸 invite] 전화 회의에 사용자를 초대 합니다.

  - Skype를 사용 하 여 비즈니스 웹 응용 프로그램에 대 한 익명 사용자로 전화 회의 참가 합니다.

  - 유선된 PC 연결, IP 전화 및 모바일 장치에서 통화에 참가 합니다.

  - 페더레이션된 사용자 o PSTN 유효성 검사를 통화에 대 한 호출: 호출이 완료 된, 통화 품질은 적절 한는 연결 시간을 허용할 수 있습니다.

  - 대화 상대에 대 한 현재 상태는 테 넌 트의 두 구성원에 대 한 업데이트 및 페더레이션 사용자를 확인 합니다.

### <a name="common-problems"></a>일반적인 문제

비대칭 라우팅은 가장 일반적인 구현 문제입니다. 일부 일반적인 소스를 찾도록 다음과 같습니다.
  
- 열기 또는 플랫 네트워크 라우팅 토폴로지를 사용 하 여 원본 위치에는 NAT 없이 합니다.

- 하지 SNAT를 사용 하 여 인바운드 라우팅 서비스 인터넷 및 ExpressRoute를 통해 연결 합니다.

- 광범위 하 게 배포 하기 전에 테스트 네트워크에서 ExpressRoute에서 인바운드 서비스를 테스트 하지 않습니다.

## <a name="deploying-expressroute-connectivity-through-your-network"></a>네트워크를 통한 ExpressRoute 연결 배포
<a name="testing"> </a>

연결 새로운 각 네트워크 세그먼트에 대 한 롤백 계획을 사용 하 여 네트워크의 다른 부분을 점진적으로 롤아웃 한번에 하나의 네트워크 세그먼트에 배포를 준비 합니다. 배포 하는 Office 365 배포에 맞추는, 먼저 Office 365 파일럿 사용자에 게 배포 하 고 여기에서 확장 합니다.
  
처음으로 테스트를 위한 및 프로덕션 환경에 대해 다음:
  
- ExpressRoute를 사용 하도록 설정 하는 배포 단계를 실행 합니다.

- 네트워크 경로 예상 대로 표시를 테스트 합니다.

- 각 인바운드 및 아웃 바운드 서비스에 대 한 테스트를 수행 합니다.

- 문제를 발견 하는 경우 롤백입니다.

### <a name="set-up-a-test-connection-to-expressroute-with-a-test-network-segment"></a>테스트 네트워크 세그먼트를 가진 ExpressRoute에 대 한 테스트 연결 설정

이제 용지에 완료 된 플랜이 작은 규모에서 테스트 하는 시간입니다. 이 테스트에서 온-프레미스 네트워크에 테스트 서브넷으로 Microsoft Peering와 단일 ExpressRoute 연결을 설정할를 수 있습니다. 테스트 서브넷에서 연결을 사용 하 여 [평가판 Office 365 테 넌 트](https://go.microsoft.com/fwlink/p/?LinkID=403802) 를 구성 수 있으며 테스트 서브넷에서 프로덕션 환경에서 사용 하는 모든 아웃 바운드 및 인바운드 서비스를 포함할 수 있습니다. 테스트 네트워크 세그먼트에 대 한 DNS를 설정 하 고 모든 인바운드 및 아웃 바운드 서비스를 설정 합니다. 테스트 계획을 실행 하 고 경로 전파 하 고 각 서비스에 대 한 라우팅 익숙한 것을 확인 합니다.
  
### <a name="execute-the-deployment-and-test-plans"></a>배포 및 테스트 계획을 실행

위에서 설명한 항목을 완료 하면 팀 계획 테스트 및 배포를 실행 하기 전에 검토 하 고 완료 하 고 확인 하면 영역 해제 확인 합니다.
  
- 네트워크 변경에 관련 된 아웃 바운드 및 인바운드 서비스의 목록입니다.

- 인터넷 송신 및 ExpressRoute 모임 모두 표시 하는 글로벌 네트워크 아키텍처 다이어그램-나에 게 위치입니다.

- 배포 된 각 서비스에 사용 되는 다양 한 네트워크 경로 보여주는 네트워크 라우팅 다이어그램입니다.

- 필요한 경우 변경 사항 및 롤백을 구현 하는 단계와 배포를 계획 합니다.

- 각 Office 365와 네트워크 서비스를 테스트 하기 위한 테스트 계획 합니다.

- 인바운드 및 아웃 바운드 서비스에 대 한 프로덕션 경로의 용지 유효성 검사를 완료 합니다.

- 가용성 테스트를 포함 하 여 테스트 네트워크 세그먼트를 통해 완료 된 테스트 합니다.

일부 문제를 해결 하는 것에 대 한 시간을 사용할 수 있으며 필요한 경우 다시 롤링에 대 한 시간, 정도로 길다고 전체 배포 계획 및 테스트 계획을 통해 실행 하는 중단 창이 선택 합니다.
  
> [!CAUTION]
> 인터넷 및 ExpressRoute을 통해 라우팅의 복잡 한 특성상 것이 좋습니다 처리 복잡 한 라우팅 문제를 해결 하려면이 창에 추가 추가 버퍼 시간입니다.
  
### <a name="configure-qos-for-skype-for-business-online"></a>QoS에 대 한 구성 Skype 비즈니스에 대 한 온라인

QoS는 Skype에 대 한 온라인 비즈니스에 대 한 음성 및 회의 혜택을 얻을 필요는. ExpressRoute 네트워크 연결이 차단 하 여 다른 Office 365 서비스 액세스 중 하나 하지 하는지 확인 한 후 QoS를 구성할 수 있습니다. QoS에 대 한 구성 [ExpressRoute 및 비즈니스 온라인 용 Skype에서 QoS](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d) 문서에 설명 되어있습니다.
  
## <a name="troubleshooting-your-implementation"></a>구현을 문제해결
<a name="troubleshooting"> </a>

모든 된이 구현 가이드의 단계에는 첫번째 곳은 구현 계획에서 누락 된? 뒤로 이동 하 고 소규모 네트워크의 오류를 복제 하 고 디버깅할 수를 가능한 경우 테스트를 실행 합니다.
  
인바운드 또는 아웃 바운드 테스트 하는 동안 실패 한 서비스를 식별 합니다. 각 실패 하는 서비스에 대 한 IP 주소 및 서브넷 구체적으로 가져옵니다. 차지 코드로 미리 차 이동 하 고 용지에 네트워크 토폴로지 다이어그램을 진행 하 고 라우팅의 유효성을 검사 합니다. 특히 여기서 ExpressRoute 라우팅으로 보급 됩니다를 유효성을 검사, 해당 중단 된 시간 동안 가능한 경우 사용 하 여 라우팅을 추적을 테스트 합니다.
  
각 고객 끝점에 네트워크 추적을 사용 하 여 PSPing를 실행 하 고 예상 대로 되었는지 확인 하려면 원본 및 대상 IP 주소를 평가 합니다. Telnet 포트 25에서 노출 하 고 SNAT 형식이 예상 되는 경우 원래 원본 IP 주소를 숨기고 확인 하는 모든 메일 호스트를 실행 합니다.
  
ExpressRoute에 대 한 네트워크 구성을 확인 하는데 필요한 ExpressRoute 연결 된 Office 365를 배포 하는 동안 최적으로 설계 된 유념 하 고 클라이언트 컴퓨터와 같은 네트워크에 다른 구성 요소를 최적화도 했을 때 키를 누릅니다. 이 계획 가이드를 사용 하 여 부재중 단계 문제를 해결 하려면, 외에 쓴 [성능 문제해결 Office 365에 대 한 계획](https://support.office.com/article/Performance-troubleshooting-plan-for-Office-365-e241e5d9-b1d8-4f1d-a5c8-4106b7325f8c) 합니다.
  
짧은 링크를 다시 사용할 수는 다음과 같습니다.[https://aka.ms/implementexpressroute365](https://aka.ms/implementexpressroute365)
  
## <a name="related-topics"></a>관련 항목

[Office 365에 대한 네트워크 연결](network-connectivity.md)
  
[Office 365용 Azure ExpressRoute](azure-expressroute.md)
  
[Office 365 연결에 대한 ExpressRoute 관리](managing-expressroute-for-connectivity.md)
  
[Office 365용 ExpressRoute를 사용한 라우팅](routing-with-expressroute.md)
  
[Office 365용 ExpressRoute를 사용한 네트워크 계획](network-planning-with-expressroute.md)
  
[ExpressRoute BGP 커뮤니티를 사용 하 여 Office 365 시나리오 (미리 보기)](bgp-communities-in-expressroute.md)
  
[미디어 품질 및 온라인 비즈니스 Skype 네트워크 연결 성능](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[비즈니스 온라인 용 Skype에 대 한 네트워크를 최적화](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)
  
[ExpressRoute 및 온라인 비즈니스에 대 한 Skype에서 QoS](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[ExpressRoute를 사용 하 여 호출 흐름](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[초기 계획 및 성능 기록을 사용하여 Office 365 성능 조정](performance-tuning-using-baselines-and-history.md)
  
[Office 365 성능 문제 해결 계획](performance-troubleshooting-plan.md)
  
[Office 365 URL 및 IP 주소 범위](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Office 365 네트워크 및 성능 조정](network-planning-and-performance.md)
