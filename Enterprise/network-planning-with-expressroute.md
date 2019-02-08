---
title: Office 365용 ExpressRoute를 사용한 네트워크 계획
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 2/14/2018
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
ms.assetid: 103208f1-e788-4601-aa45-504f896511cd
description: 간의 계층 3 연결을 제공 하는 Office 365에 대 한 ExpressRoute는 네트워크 및 Microsoft의 데이터 센터입니다. 회로 테두리 게이트웨이 프로토콜 (BGP) 경로 광고 Office 365의 프런트엔드 서버를 사용합니다. 온-프레미스 장치로의 관점에서 Office 365 올바른 TCP/IP 경로 선택 하는 데 필요한 Azure ExpressRoute 인터넷 하는 대신 표시 됩니다.
ms.openlocfilehash: 7a2c9cb8ee562c0527416aa83184de90cd204476
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897231"
---
# <a name="network-planning-with-expressroute-for-office-365"></a>Office 365용 ExpressRoute를 사용한 네트워크 계획

간의 계층 3 연결을 제공 하는 Office 365에 대 한 ExpressRoute는 네트워크 및 Microsoft의 데이터 센터입니다. 회로 테두리 게이트웨이 프로토콜 (BGP) 경로 광고 Office 365의 프런트엔드 서버를 사용합니다. 온-프레미스 장치로의 관점에서 Office 365 올바른 TCP/IP 경로 선택 하는 데 필요한 Azure ExpressRoute 인터넷 하는 대신 표시 됩니다.
  
Azure ExpressRoute 지원 되는 기능 및 Microsoft의 데이터 센터 내에서 Office 365 서버에 의해 제공 되는 서비스의 특정 집합에 직접 경로 추가 합니다. Azure ExpressRoute 인터넷을 통해 연결 Microsoft 데이터 센터 또는 도메인 이름 확인 등의 기본 인터넷 서비스를 대신 하지 않습니다. Azure ExpressRoute 및 인터넷 회로 보안 및 중복 되어야 합니다.
  
다음 표에서 인터넷 및 Office 365의 컨텍스트에서 Azure ExpressRoute 연결 간의 몇가지 차이점을 강조 표시 됩니다.

|**네트워크 계획의 차이점**|**인터넷 네트워크 연결**|**ExpressRoute 네트워크 연결**|
|:-----|:-----|:-----|
| 필요한 인터넷 서비스를 포함 하 여;에 대 한 액세스  <br/>  DNS 이름 확인  <br/>  인증서 해지 확인  <br/>  콘텐츠 배달 네트워크  <br/> |예  <br/> |Microsoft에 대 한 요청 소유 하 고 DNS 및/또는 CDN 인프라 ExpressRoute 네트워크를 사용할 수 있습니다.  <br/> |
| Office 365 서비스를 포함 하 여;에 대 한 액세스  <br/>  Exchange Online  <br/>  SharePoint Online  <br/>  비즈니스용 Skype Online  <br/>  Office Online  <br/>  Office 365 포털 및 인증  <br/> |예, 모든 응용 프로그램 및 기능  <br/> |예, [특정 응용 프로그램 및 기능](https://aka.ms/o365endpoints) <br/> |
|온-프레미스 보안 경계에 있습니다.  <br/> |예  <br/> |예   <br/> |
|고가용성 계획 합니다.  <br/> |대체 인터넷 네트워크 연결에 대 한 장애 조치  <br/> |장애 조치에 대 한 대체 ExpressRoute 연결 하려면  <br/> |
|예측 가능한 네트워크 프로필을 사용 하 여 직접 연결 합니다.  <br/> |아니요  <br/> |예  <br/> |
|IPv6 연결 합니다.  <br/> |예  <br/> |예   <br/> |

더 많은 네트워크 계획 지침에 대 한 제목 아래를 확장 합니다. 정보 (영문) 보다 심도 있는 10 부 [Office 365 교육에 대 한 Azure ExpressRoute](https://channel9.msdn.com/series/aer) 시리즈를 기록 했을 때 했습니다.

## <a name="existing-azure-expressroute-customers"></a>기존 Azure ExpressRoute 고객

이런이 회로 통해 Office 365 연결을 추가 하려면를 기존 Azure ExpressRoute 회로 사용 하는 경우 수 회로, 탈출 위치 및 Office 365 사용의 요구 사항을 충족 것을 위해 회로의 크기를 확인 해야 합니다. 추가 대역폭을 필요로 하는 대부분의 고객 및 추가 회로 대부분 필요 합니다.
  
기존 Azure ExpressRoute 회로 통해 Office 365에 대 한 액세스를 사용 하도록 설정 하려면 [경로 필터를 구성 하](https://docs.microsoft.com/azure/expressroute/how-to-routefilter-portal) 는 Office 365 서비스를 확인 하려면 액세스할 수 있습니다.
  
Azure ExpressRoute 구독은 고객 중심 의미 구독 고객에 게 연결 됩니다. 고객으로 여러 Azure ExpressRoute 회로 가질 수 있으며 이러한 회로 통해 많은 Microsoft 클라우드 리소스에 액세스할 수 있습니다. 예는 Azure에 액세스 하도록 선택할 수 있습니다 한 쌍의 중복 Azure ExpressRoute 회로 통해 호스팅되는 가상 컴퓨터는 Office 365 테스트 테 넌 트 및 Office 365 프로덕션 테 넌 트입니다.
  
이 표에서 두 유형의 피어 관계 회로 통해 구현 하도록 선택할 수 있습니다를 설명 합니다.

|**피어 링 관계**|**Azure 전용**|**Microsoft**|
|:-----|:-----|:-----|
|**서비스** <br/> |IaaS: Azure 가상 컴퓨터  <br/> |PaaS: Azure 공용 서비스  <br/> SaaS: Office 365  <br/> SaaS: Dynamics 365  <br/> |
|연결 시작 * * * <br/> |고객-Microsoft  <br/> Microsoft-고객  <br/> |고객-Microsoft  <br/> Microsoft-고객  <br/> |
|**QoS 지원** <br/> |QoS 없음  <br/> |QoS<sup>1</sup> <br/> |

<sup>1</sup> QoS 비즈니스 Skype이 이번에만 지원합니다.
  
## <a name="bandwidth-planning-for-azure-expressroute"></a>대역폭 Azure ExpressRoute에 대 한 계획

모든 Office 365 고객 각 위치에 각 Office 365 응용 프로그램 및 온-프레미스 또는 하이브리드 장비 및 네트워크 보안 구성을 사용 하 여 등의 다른 요소는 활성 사용자 수에 따라 고유한 대역폭 요구 사항에 있습니다.
  
너무 적은 대역폭을 가진 정체, 데이터 및 예측할 수 없는 지연의 재전송 될 수 있습니다. 너무 많은 대역폭을 가진 불필요 한 비용이 발생 합니다. 기존 네트워크에서 대역폭은 이라고 회로에 사용할 수 있는 여유 공간 양을 측면에서 백분율입니다. 10% 공간 정체 될 가능성이 하 고 불필요 한 비용을 의미 여유가 80%를 일반적으로 필요 합니다. 일반적인 여유가 대상 할당은 20% ~ 50%입니다.
  
적절 한 수준의 대역폭을 찾으려면 최상의 메커니즘에 기존 네트워크 소비를 테스트 하는 것입니다. 사용 하려면 true로 측정을 가져오고 모든 네트워크 구성으로 필요한 유일한 방법은 및 응용 프로그램은 일부 같은 방법으로 고유 합니다. 필요한 경우 측정 하는 것이 좋습니다 총 대역폭 소비, 대기 시간 및 네트워크를 이해 하려면 TCP 정체에 주의 해야 합니다.
  
한번 모든 네트워크 응용 프로그램을 실제 사용량을 확인 하 여 조직에서 사용자의 다른 프로필을 구성 하는 소규모 그룹을 사용 하 여 파일럿 Office 365를 포함 하는 예상된 초기 있고 두 측정 단위를 사용 하 여의 양을 예측 대역폭 각 사무실 위치에 대 한 필요할 수 있습니다. 모든 대기 시간 또는 TCP 정체 문제 테스트에서 발견 된 경우 Office 365를 사용 하는 사람들에 게 탈출을 더 가깝게 이동 하거나 SSL 암호 해독/검사 등 검사 위주의 네트워크를 제거 해야할 수 있습니다.
  
권장 되는 어떤 유형의 네트워크 처리를 사용 하는 것이 좋습니다의 모든 ExpressRoute와 인터넷 회로에 적용 됩니다. 이 [성능 튜닝 사이트](https://aka.ms/tune)에 대 한 지침의 나머지 부분에 대 한도 마찬가지입니다.
  
## <a name="applying-security-controls-to-azure-expressroute-for-office-365-scenarios"></a>Office 365 시나리오에 대 한 보안 제어 기능을 Azure ExpressRoute을 적용합니다.

Azure ExpressRoute 연결 보안 인터넷 연결 보호와 같은 원칙으로 시작 됩니다. 대부분의 고객 Office 365 및 기타 Microsoft 구름 모양에 자신의 온-프레미스 네트워크 연결 ExpressRoute 경로 따라 네트워크 및 경계 컨트롤을 배포 하는 선택 합니다. 이러한 컨트롤에는 방화벽, 응용 프로그램 프록시, 데이터 유출 방지, 침입 검색, 침입 방지 시스템 등에 포함 될 수 있습니다. 대부분의 경우에서 고객 트래픽에 적용 다양 한 수준의 컨트롤에서 온-프레미스 Microsoft에서는 고객 온-프레미스 네트워크 트래픽 온-프레미스 일반 하려고에서 시작 된 비교 하려고 하는 Microsoft에서 시작 하는 트래픽 비교 하려고 시작 인터넷 대상입니다.
  
배포 하려는 [ExpressRoute 연결 모델](https://docs.microsoft.com/en-us/azure/expressroute/expressroute-connectivity-models) 을 사용한 보안 통합 (영문)의 몇가지 예는 다음과 같습니다.

|**ExpressRoute 통합 옵션**|**네트워크 보안 경계 모델**|
|:-----|:-----|
|클라우드 exchange에 함께 배치  <br/> |새로 설치 하거나 ExpressRoute 연결이 설정 되는 여기서 공동 위치 시설에서 기존 보안/경계 인프라를 활용 합니다.  <br/> 목적으로 라우팅/상호 연결 및 온-프레미스 보안/경계 인프라에 대 한 공동 시설에서 역방향 단거리 연결을 위한 순수 하 게 공동 위치 기능을 활용 하는 방법입니다.  <br/> |
|지점간 이더넷  <br/> |기존 온-프레미스 보안/경계 인프라 위치에서 지점간 ExpressRoute 연결을 종료 합니다.  <br/> ExpressRoute 경로에 새 보안/경계 인프라를 설치 하 고는 지점간 연결을 종료 합니다.  <br/> |
|모든-를-모든 IPVPN  <br/> |탈출 ExpressRoute에 대 한 사용 하 여 Office 365 연결에 대 한 IPVPN에 있는 모든 위치에서 기존 온-프레미스 보안/경계 인프라를 활용 합니다.  <br/> 헤어핀 특정 한 온-프레미스 위치를 Office 365에 대 한 ExpressRoute에 사용 되는 IPVPN 보안/경계 사용 하도록 지정 합니다.  <br/> |

일부 서비스 공급자는 또한 Azure ExpressRoute를 사용 하 여 자신의 통합 솔루션의 일부로 관리 되는 보안/경계 기능을 제공 합니다.
  
다음은 추가 고려 사항 ExpressRoute에 대 한 사용 하 여 Office 365 연결에 대 한 네트워크/보안 경계 옵션의 토폴로지 배치를 고려 하는 경우
  
- 깊이 유형 네트워크/보안 컨트롤에는 성능 및 확장성을 Office 365 사용자 환경에 미치는 영향이 있을 수 있습니다.

- 아웃 바운드 (온-프레미스-\>Microsoft) 트래픽과 인바운드 (Microsoft-\>온-프레미스) [하 게 되어있으면] 흐름에는 서로 다른 요구 사항이 있을 수 있습니다. 이러한 경우가 다른 아웃 바운드 보다 일반적인 인터넷 대상으로 합니다.

- Office 365 요구 사항 포트/프로토콜 및 필요한 IP 서브넷에 대 한 Office 365에 대 한 ExpressRoute를 통해 또는 인터넷을 통해 트래픽이 라우팅될 여부 동일 합니다.

- 고객 네트워크/보안 컨트롤의 토폴로지 배치 사용자와 Office 365 서비스 간의 궁극적인 종단간 네트워크를 결정 및 네트워크 대기 시간 및 혼잡에 상당한 영향을 줄 수 있습니다.

- 고객에 게는 중복, 고가용성 및 재해 복구에 대 한 모범 사례에 따라 Office 365에 대 한 ExpressRoute 함께 사용 하기 위해 해당 보안/경계 토폴로지를 디자인 하는 것이 좋습니다.

위에서 설명한 경계 보안 모델에는 다양 한 Azure ExpressRoute 연결 옵션을 비교 하는 Woodgrove Bank의 예는 다음과 같습니다.
  
### <a name="example-1-securing-azure-expressroute"></a>예 1: Azure ExpressRoute 보호
  
Woodgrove Bank Azure ExpressRoute 구현 고려 하는 및 결정는 [Office 365에 대 한 ExpressRoute와 라우팅](routing-with-expressroute.md) 에 대 한 최적의 아키텍처를 계획 한 후, 전환 및 후 위 지침을 사용 하 여 대역폭 요구 사항을 이해 하는 자신의 경계를 보호 하기 위한 최상의 방법입니다.
  
Woodgrove, 여러 대륙의 위치를 가진 다국적 조직에 대 한 보안 모든 경계에 걸쳐 해야 합니다. Woodgrove에 대 한 최적의 연결 옵션에는 각 대륙에 직원 들의 요구를 처리 하 여 전세계 여러 피어 링 위치와 다중 포인트 연결입니다. 각 대륙 대륙 내에서 중복 Azure ExpressRoute 회로 포함 하 고 대부분의 보안 확장 해야 합니다.
  
Woodgrove의 기존 인프라 안정적이 고 추가 작업을 처리할 수 있는, 결과적으로, Woodgrove Bank가 자신의 Azure ExpressRoute 및 인터넷 경계 보안에 대 한 인프라를 사용할 수 있습니다. 대/소문자를 받지이 하는 경우에 Woodgrove가 기존 장비를 보완 하기 위해 또는 다른 종류의 연결을 처리 하려면 추가 장비를 구입 하도록 선택할 수 있습니다.
  
## <a name="high-availability-and-failover-with-azure-expressroute"></a>고가용성 및 장애 조치 Azure ExpressRoute와
<a name="BKMK_high-availability"> </a>

ExpressRoute 공급자에 게 ExpressRoute와 각 탈출에서 적어도 두 활성 회로 프로 비전 하는 것이 좋습니다. 이것은 가장 일반적인 위치 및 고객에 대 한 오류를 참조는 한 쌍의 액티브/액티브 ExpressRoute 회로 프로 비전 하 여 쉽게 방지할 수 있습니다. 또한 것이 좋습니다 적어도 두 액티브/액티브 인터넷 회로 많은 Office 365 서비스가 인터넷을 통해 사용할 수만 있기 때문에 있습니다.
  
내부 네트워크의 탈출 지점의 다른 많은 장치 및 사용자 가용성을 생각 하는 방법에 중요 한 역할을 하는 회로 됩니다. 연결 시나리오의 이러한 부분 ExpressRoute 또는 Office 365 Sla에 포함 되지 않습니다 하지만 조직의 사용자가 인식 한 대로 끝 서비스 가용성에서 중요 한 역할을 수행 있습니다.
  
사용 하 여 사용자에 초점을 맞춥니다 및 서비스를 사용 하 여 환경을 인증서를 영향을 받는 사람의 총 백분율을 제한 하는 방법에 대 한 확인 오류가 발생 한 모든 구성 요소는 사용자의에 영향을 하는 경우 Office 365 작동 합니다. 장애 조치 모드 운영상 복잡 한 경우의 복구 하는데 시간이 오래 사용자의 경험을 고려 하 고 운영상 간단 하 고 자동 장애 조치 모드에 대 한 찾습니다.
  
외부 네트워크, Office 365, ExpressRoute, 및 ExpressRoute 공급자의 다양 한 수준의 가용성 있는 모든 합니다.
  
### <a name="service-availability"></a>서비스 가용성
  
- Office 365 서비스 개별 서비스에 대 한 가동 시간 및 가용성 메트릭을 포함 하는 잘 정의 된 [서비스 수준 계약](https://technet.microsoft.com/library/office-365-service-level-agreement.aspx)에 포함 합니다. 한 가지 이유를 Office 365 이러한 높은 서비스 가용성 수준은 원활 하 게 장애 조치는 많은 Microsoft 데이터 센터, 전역 Microsoft 네트워크를 사용 하 여 사이 개별 구성 요소에 대 한 기능을 유지할 수 있습니다. 이 장애 조치 데이터 센터와 네트워크에서 여러 인터넷 탈출 포인트를 확장 하 고 원활 하 게 서비스를 사용 하는 사용자의 관점에서 볼 때 장애 조치를 수 있습니다.

- ExpressRoute ExpressRoute 공급자 또는 파트너 인프라와 Microsoft 네트워크 가장자리 사이의 개별 전용된 회로에서 [99.9%의 가용성 SLA를 제공](https://azure.microsoft.com/support/legal/sla/expressroute/v1_0/) 합니다. 이러한 서비스 수준은 중복 Microsoft 장비 및 각 피어 링 위치에서 네트워크 공급자 장비 사이의 [두 독립적인 상호 연결](https://azure.microsoft.com/documentation/articles/expressroute-introduction/) 을 구성 하는 ExpressRoute 회로 수준에서 적용 됩니다.

### <a name="provider-availability"></a>공급자 사용 가능 여부
  
- Microsoft의 서비스 수준 계약의 경우 ExpressRoute 공급자 또는 파트너에서 중지합니다. 가용성 수준에 영향을 주는 선택 지정할 수 있습니다를 처음 이기도 합니다. 아키텍처, 가용성 및 ExpressRoute 공급자가 제공 하는 복구 특성 네트워크 경계와 각 Microsoft 피어 링 위치에 대 한 연결 공급자 간의 밀접 하 게 평가 해야 합니다. 중복, 피어 링 장비, 제공 하는 통신 회사 WAN 회로의 논리적 / 물리적 측면에 주의 하 고 모든 추가 값 NAT 서비스 또는 관리 되는 방화벽 등의 서비스를 추가 합니다.

### <a name="designing-your-availability-plan"></a>가용성 계획을 디자인
  
계획 하 고 Office 365에 대 한 끝-연결 시나리오에 높은 가용성 및 복구를 디자인 하는 것이 좋습니다. 디자인을 포함 해야 합니다.
  
- 오류, 인터넷 및 ExpressRoute 모두 회로 포함 하 여 단일 지점이 없습니다.

- 영향을 받는 사용자의 수 및 가장 예상된 오류 모드에 대 한 영향을 미치는의 기간을 최소화 합니다.

- 가장 예상된 오류 모드에서 간단 하 고, 반복 가능 하며, 자동 복구 프로세스에 대 한 최적화 합니다.

- 전체 요구 네트워크 트래픽와 많이 저하 없이 중복 된 경로 통해 기능을 지원합니다.

연결 시나리오에는 Office 365에 대 한 여러 독립적 및 활성 네트워크 경로 위해 최적화 된 네트워크 토폴로지를 포함 해야 합니다. 보다 잘 끝-가용성 중복 개별 장치 또는 장비 수준에 대해서만 최적화 된 토폴로지를 보다 생길 수 있습니다.
  
> [!TIP]
> 사용자에 게는 여러 대륙 또는 지리적 위치에 분산 하 고 단일 ExpressRoute 회로 있는 단일 온-프레미스 위치로 중복 WAN 회로 통해 연결 하는 각 위치, 사용자 환경은 작으면 가장 가까운 피어 링를 서로 다른 영역을 연결 하는 독립적인 ExpressRoute 회로 포함 하는 네트워크 토폴로지 디자인을 보다 끝-서비스 가용성 위치입니다.
  
각 회선에 연결 해야 다른 지리적 피어 링 위치와 ExpressRoute 회로 둘 이상 구축 하는 것이 좋습니다. 이 액티브 / 액티브 쌍의 회로 사람들이 ExpressRoute 연결을 사용 하는 Office 365 서비스에 대 한는 있는 모든 지역에 대 한 프로 비전 해야 합니다. 따라서 각 지역을 데이터 센터와 같은 주요 위치 또는 피어 링 위치에 영향을 주는 재해가 발생 한 동안 연결 된 상태로 유지 수 있습니다. 액티브/액티브도 구성에 최종 사용자 트래픽을 여러 네트워크 경로 걸쳐 분산 될 수 있습니다. 장치 또는 네트워크 장비 중단 하는 동안 영향을 받는 사용자의 범위를 줄입니다.
  
인터넷을 통한 단일 ExpressRoute 회로 사용 하 여 백업으로 하지 것이 좋습니다.
  
### <a name="example-2-failover-and-high-availability"></a>예 2: 장애 조치 및 고가용성
  
Woodgrove Bank 여러 지리적 라우팅, 대역폭, 보안, 검토의 경우 되었기 때문에 디자인과 지금 고가용성 검토를 통해 이동 해야 합니다. Woodgrove는 편리할; 다루는으로 고가용성에 대 한 것으로 생각 복구, 안정성 및 중복 됩니다.
  
복구 신속 하 게 오류 로부터 복구 하는 Woodgrove 수 있습니다. 안정성은 시스템 내에서 일관 된 결과 제공 하는 Woodgrove 수 있습니다. 중복은 인프라의 하나 이상의 미러 인스턴스 간에 이동 Woodgrove 수 있습니다.
  
각에 지 구성 내에서 Woodgrove 중복 방화벽, 프록시 및 ID가 있습니다. 북미 지역에 대 한 Woodgrove가 달라스 데이터 센터에서 한에 지 구성 하 고 자신의 버지니아 데이터 센터의 다른에 지 구성 했습니다. 각 위치에 중복 장비는 해당 위치에 복구를 제공합니다.
  
Woodgrove Bank에서 네트워크 구성은 몇가지 주요 원칙에 기반으로 구축 됩니다.
  
- 각 지리적 영역 내에서 여러 Azure ExpressRoute 회로 있습니다.

- 각 회로 영역 내에서 해당 영역 내에서 네트워크 트래픽 모두를 지원할 수 있습니다.

- 라우팅 해도 하나 또는 가용성, 위치에 따라 다른 경로 선호 및 등 명확 하 게 합니다.

- Azure ExpressRoute 회로 간에 장애 조치 추가 구성 또는 Woodgrove가 작업을 수행 하지 않고 자동으로 발생 합니다.

- 인터넷 회로 간에 장애 조치 추가 구성 또는 Woodgrove가 작업을 수행 하지 않고 자동으로 발생 합니다.

이 구성에서 실제 및 가상 수준에서 중복 된 Woodgrove Bank는 신뢰할 수 있는 방식으로 로컬 복구, 지역 복구 및 전체 복구를 제공 수 있습니다. Woodgrove 선택한 지역으로 인터넷에 대 한 장애 조치 가능성을 사전 당 단일 Azure ExpressRoute 회선을 확인 한 후이 구성 합니다.
  
아시아 태평양에서 Azure ExpressRoute 회로에 북미에서 시작 되는 라우팅 트래픽을 수용할 수 없는 수준 대기 시간 및 필요한 DNS 전달 자가 구성의 추가 Woodgrove, 여러 Azure ExpressRoute 회로 지역별로 할 수 없는 경우 복잡성을 추가합니다.
  
백업 구성으로 인터넷을 활용 하 여 권장 되지 않습니다. Woodgrove의 안정성 원칙, 연결을 사용 하는 일치 하지 않는 환경에서 발생을 중단 합니다. 또한 수동 구성 구성 된 BGP 광고 고려 하 고 장애 조치, NAT 구성, DNS 구성 및 프록시 구성에 필요한 것입니다. 이 추가 장애 조치 복잡성 복구 하는 시간을 증가 하 고 능력을 진단 하 고 해결 하는 단계를 줄입니다.
  
아직도 질문이 대 한 계획 및 트래픽 관리 또는 Azure ExpressRoute를 구현 하는 방법에 대 한? 이 [네트워크 및 성능 지침](https://aka.ms/tune) 또는 [Azure ExpressRoute FAQ](https://azure.microsoft.com/documentation/articles/expressroute-faqs/)의 나머지 부분을 읽어보십시오.
  
## <a name="working-with-azure-expressroute-providers"></a>Azure ExpressRoute 공급자 (영문)
<a name="BKMK_high-availability"> </a>

대역폭, 대기 시간, 보안, 및 고가용성 계획에 기반 하 여 회로의 위치를 선택 합니다. 배치 하려는 최적의 위치를 알고 있으면 회로, [지역에 따라 공급자의 현재 목록을 검토](https://azure.microsoft.com/documentation/articles/expressroute-locations/)합니다.
  
지점간, 다중 포인트 또는 호스팅된 최상의 연결 옵션을 선택 하 여 공급자 또는 공급자를 사용 합니다. 혼합 하 고 대역폭 및 기타 중복 구성 요소 지원 라우팅 및 높은 가용성 디자인을 연결 옵션을 일치 해야 합니다.
  
다음의 간단한 링크를 사용할 수 있습니다. [https://aka.ms/planningexpressroute365](https://aka.ms/planningexpressroute365)
  
## <a name="related-topics"></a>관련 항목
<a name="BKMK_high-availability"> </a>

[Office 365에 대한 네트워크 연결](network-connectivity.md)
  
[Office 365용 Azure ExpressRoute](azure-expressroute.md)
  
[Office 365 연결에 대한 ExpressRoute 관리](managing-expressroute-for-connectivity.md)
  
[Office 365용 ExpressRoute를 사용한 라우팅](routing-with-expressroute.md)
  
[Office 365용 ExpressRoute 구현](implementing-expressroute.md)
  
[Office 365용 ExpressRoute 시나리오에서 BGP 커뮤니티 사용(미리 보기)](bgp-communities-in-expressroute.md)
  
[비즈니스용 Skype Online의 미디어 품질 및 네트워크 연결 성능](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[비즈니스용 Skype Online의 네트워크 최적화](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)
  
[비즈니스용 Skype Online의 ExpressRoute 및 QoS](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[ExpressRoute를 사용하는 호출 흐름](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[초기 계획 및 성능 기록을 사용하여 Office 365 성능 조정](performance-tuning-using-baselines-and-history.md)
  
[Office 365 성능 문제 해결 계획](performance-troubleshooting-plan.md)
  
[Office 365 URL 및 IP 주소 범위](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Office 365 네트워크 및 성능 조정](network-planning-and-performance.md)
  
[Office 365 끝점 FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
