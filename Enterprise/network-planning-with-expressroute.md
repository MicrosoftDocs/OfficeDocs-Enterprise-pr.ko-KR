---
title: Office 365용 ExpressRoute를 통한 네트워크 계획
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 2/14/2018
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
ms.assetid: 103208f1-e788-4601-aa45-504f896511cd
description: Office 365 용 Express를 통해 네트워크와 Microsoft의 데이터 센터 간에 계층 3 연결이 제공 됩니다. 회로는 Office 365의 프런트 엔드 서버에 대 한 BGP (Border Gateway Protocol) 경로 알림을 사용 합니다. 온-프레미스 장치를 사용 하 여 Office 365에 대 한 올바른 TCP/IP 경로를 선택 해야 하는 경우에는 Azure Express를 인터넷 대신 사용할 수 있는 것으로 간주 됩니다.
ms.openlocfilehash: f147003491b2186a05edbaf73acc86e60dbe3110
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230884"
---
# <a name="network-planning-with-expressroute-for-office-365"></a>Office 365용 ExpressRoute를 통한 네트워크 계획

*이 문서는 Microsoft 365 Enterprise 및 Office 365 Enterprise에 모두 적용 됩니다.*

Office 365 용 Express를 통해 네트워크와 Microsoft의 데이터 센터 간에 계층 3 연결이 제공 됩니다. 회로는 Office 365의 프런트 엔드 서버에 대 한 BGP (Border Gateway Protocol) 경로 알림을 사용 합니다. 온-프레미스 장치를 사용 하 여 Office 365에 대 한 올바른 TCP/IP 경로를 선택 해야 하는 경우에는 Azure Express를 인터넷 대신 사용할 수 있는 것으로 간주 됩니다.
  
Azure Express에서는 Microsoft의 데이터 센터 내에서 Office 365 서버에서 제공 하는 지원 되는 특정 기능 집합에 대 한 직접 경로를 추가 합니다. Azure Express 서버는 Microsoft 데이터 센터 또는 기본 인터넷 서비스 (예: 도메인 이름 확인)에 인터넷 연결을 대체 하지 않습니다. Azure Express 경로와 인터넷 회로는 안전 하 고 중복 되어야 합니다.
  
다음 표에는 Office 365의 컨텍스트에서 인터넷 및 Azure Express 경로 연결 사이의 몇 가지 차이점이 강조 되어 있습니다.

|**네트워크 계획의 차이점**|**인터넷 네트워크 연결**|**Express 하기 네트워크 연결**|
|:-----|:-----|:-----|
| 다음을 포함 하 여 필요한 인터넷 서비스에 대 한 액세스 권한  <br/>  DNS 이름 확인  <br/>  인증서 해지 확인  <br/>  콘텐츠 배달 네트워크(CDN)  <br/> |예  <br/> |Microsoft에서 소유한 DNS 및/또는 CDN 인프라에 대 한 요청은 Express 경로 네트워크를 사용할 수 있습니다.  <br/> |
| 다음을 포함 하는 Office 365 서비스에 대 한 액세스 권한  <br/>  Exchange Online  <br/>  SharePoint Online  <br/>  비즈니스용 Skype Online  <br/>  브라우저에서 Office  <br/>  Office 365 포털 및 인증  <br/> |예, 모든 응용 프로그램 및 기능  <br/> |예, [특정 응용 프로그램 및 기능](https://aka.ms/o365endpoints) <br/> |
|주변에 온-프레미스 보안  <br/> |예  <br/> |예  <br/> |
|고가용성 계획  <br/> |대체 인터넷 네트워크 연결에 대 한 장애 조치 (Failover)  <br/> |대체 Express 연결에 대 한 장애 조치 (Failover)  <br/> |
|예측 가능한 네트워크 프로필과 직접 연결  <br/> |아니요  <br/> |예  <br/> |
|IPv6 연결  <br/> |예  <br/> |예  <br/> |

더 많은 네트워크 계획 지침을 보려면 아래 제목을 확장 합니다. 또한 더 심층적이 dives 하는 [Office 365 교육 시리즈에 대 한](https://channel9.msdn.com/series/aer) 10 개 부분으로 된 Azure express를 기록 했습니다.

## <a name="existing-azure-expressroute-customers"></a>기존 Azure Express 고객

기존 Azure Express 경로를 사용 하는 경우이 회로를 통해 Office 365 연결을 추가 하려는 경우 회로의 수, 송신 위치 및 크기를 확인 하 여 Office 365 사용에 대 한 요구 사항을 충족 하는지 확인 해야 합니다. 대부분의 고객에 게는 추가 대역폭이 필요 하며, 추가 회로가 필요 합니다.
  
기존 Azure Express 경로에서 Office 365에 대 한 액세스를 사용 하도록 설정 하려면 Office 365 서비스에 액세스할 수 있도록 [라우트 필터를 구성](https://docs.microsoft.com/azure/expressroute/how-to-routefilter-portal) 합니다.
  
Azure Express 기반 구독은 고객 중심 이며 구독은 고객과 연결 됩니다. 고객은 여러 Azure Express 경로를 사용할 수 있으며 이러한 회로를 통해 여러 Microsoft 클라우드 리소스에 액세스할 수 있습니다. 예를 들어 중복 Azure Express 경로 쌍을 통해 Azure 호스트 된 가상 컴퓨터, Office 365 테스트 테 넌 트 및 Office 365 프로덕션 테 넌 트에 액세스 하도록 선택할 수 있습니다.
  
이 표에서는 회로에 대해 구현 하도록 선택할 수 있는 두 가지 유형의 피어 링 관계를 간략하게 보여 줍니다.

|**피어 링 관계**|**Azure Private**|**Microsoft**|
|:-----|:-----|:-----|
|**서비스** <br/> |IaaS: Azure 가상 컴퓨터  <br/> |PaaS: Azure 공용 서비스  <br/> SaaS: Office 365  <br/> SaaS: Dynamics 365  <br/> |
|연결 초기화 * * * * <br/> |고객-Microsoft  <br/> Microsoft-고객  <br/> |고객-Microsoft  <br/> Microsoft-고객  <br/> |
|**QoS 지원** <br/> |QoS 없음  <br/> |QoS<sup>1</sup> <br/> |

<sup>1</sup> 이번에는 QoS에서 비즈니스용 Skype만 지원 합니다.
  
## <a name="bandwidth-planning-for-azure-expressroute"></a>Azure Express 경로에 대 한 대역폭 계획

각 Office 365 고객은 각 위치에 있는 사용자 수, 각 Office 365 응용 프로그램에서 활성 상태인 방식, 온-프레미스 또는 하이브리드 장비 및 네트워크 보안 구성 사용과 같은 기타 요인에 따라 고유한 대역폭 요구 사항을 충족 해야 합니다.
  
대역폭이 너무 적으면 혼잡, 데이터 재전송 및 예기치 않은 지연이 발생 합니다. 대역폭이 너무 많으면 불필요 한 비용이 발생 합니다. 기존 네트워크에서 대역폭은 회로에서 사용 가능한 여유 공간에 대 한 백분율로 지칭 되는 경우가 많습니다. 이러한 여유가 10% 인 경우 혼잡이 발생 하며, 일반적으로는 불필요 한 비용이 80%가 됩니다. 일반적인 여유 대상 할당은 20%에서 50%로 지정 됩니다.
  
적절 한 대역폭 수준을 확인 하려면 기존 네트워크 사용량을 테스트 하는 것이 가장 좋습니다. 이는 모든 네트워크 구성 및 응용 프로그램이 어떤 점에서 고유한 지에 대 한 실제 사용량을 측정 하는 유일한 방법입니다. 측정 시 네트워크 요구 사항을 이해 하기 위해 총 대역폭 소비, 대기 시간 및 TCP 혼잡 주의를 기울여야 합니다.
  
모든 네트워크 응용 프로그램을 포함 하는 예상 초기 계획을 사용 하는 경우, 실제 사용량을 확인 하기 위해 조직의 여러 사용자 프로필을 구성 하는 소규모 그룹과 함께 파일럿 Office 365을 수행 하 고, 두 측정값을 활용 하 여 각 사무실 위치에 필요한 대역폭의 양을 추정 합니다. 테스트 중에 발견 되는 대기 시간이 나 TCP 혼잡 문제가 있는 경우에는 egress를 Office 365을 사용 하는 사용자에 게 보다 가깝게 이동 하거나, SSL 암호 해독/검사와 같은 집중적인 네트워크 검색을 제거 해야 할 수 있습니다.
  
권장 되는 네트워크 처리 유형에 대 한 모든 권장 사항은 대상 및 인터넷 회로 둘 다에 적용 됩니다. [성능 조정 사이트](https://aka.ms/tune)의 나머지 지침 에서도 마찬가지입니다.
  
## <a name="applying-security-controls-to-azure-expressroute-for-office-365-scenarios"></a>Office 365 시나리오에 대 한 Azure Express 경로에 보안 제어 적용

Azure Express 연결의 보안은 인터넷 연결 보안과 같은 원칙으로 시작 됩니다. 대부분의 고객은 온-프레미스 네트워크를 Office 365 및 기타 Microsoft 클라우드에 연결 하는 Express 경로를 따라 네트워크 및 경계 컨트롤을 배포 하도록 선택 합니다. 이러한 컨트롤에는 방화벽, 응용 프로그램 프록시, 데이터 누출 방지, 침입 감지, 침입 방지 시스템 등이 포함 될 수 있습니다. 대부분의 경우 고객이 온-프레미스에서 시작 되는 트래픽에 서로 다른 수준의 제어를 적용 하 고, Microsoft에서 고객의 온-프레미스 네트워크로 시작 된 트래픽과 온-프레미스에서 일반 인터넷 목적지로 시작 되는 트래픽을 비교 합니다.
  
다음은 배포 하도록 선택한 [express 연결 모델](https://docs.microsoft.com/azure/expressroute/expressroute-connectivity-models) 에 보안을 통합 하는 몇 가지 예입니다.

|**Express 경로 통합 옵션**|**네트워크 보안 경계 모델**|
|:-----|:-----|
|클라우드 exchange에 배치  <br/> |새 대상 연결을 설정 하는 공동 위치 기능에서 기존 보안/주변 인프라를 새로 설치 하거나 활용 합니다.  <br/> 라우팅/상호 연결 목적 으로만 공동 위치 기능을 사용 하 고, 공동 위치 기능에서 온-프레미스 보안/주변 인프라에 대 한이를 다시 사용 합니다.  <br/> |
|지점 간 이더넷  <br/> |기존 온-프레미스 보안/주변 인프라 위치에서 지점간 데이터 수준 간 연결을 종료 합니다.  <br/> Express 경로에 따라 새 보안/주변 인프라를 설치 하 고 점 대 점 연결을 종료 합니다.  <br/> |
|임의 IP VPN  <br/> |Office 365 연결에 대 한 비트를 위한 IP VPN에 사용 되는 모든 위치의 기존 온-프레미스 보안/주변 인프라를 활용 합니다.  <br/> 헤어핀는 Office 365 용 Express에 사용 되는 IPVPN을 보안/주변으로 작동 하도록 지정 된 특정 온-프레미스 위치에 제공 합니다.  <br/> |

또한 일부 서비스 공급자는 통합 솔루션의 일부로 Azure Express를 사용 하 여 관리 되는 보안/주변 기능을 제공 합니다.
  
Office 365 연결에 대 한 Express에서 사용 되는 네트워크/보안 경계 옵션의 토폴로지 위치를 고려할 때는 다음 사항을 고려 하십시오.
  
- Depth 및 type network/security 컨트롤은 Office 365 사용자 환경에 대 한 성능 및 확장성에 영향을 줄 수 있습니다.

- 아웃 바운드 (온-프레미스- \> microsoft) 및 인바운드 (microsoft 온- \> 프레미스), [사용 하도록 설정 된 경우] 흐름의 요구 사항이 서로 다를 수 있습니다. 이는 일반 인터넷 대상에 대 한 아웃 바운드와 다를 수 있습니다.

- Office 365-포트/프로토콜 및 필수 IP 서브넷에 대 한 요구 사항은 트래픽이 Office 365 또는 인터넷을 통해 라우팅할 수 있는 것과 관계 없이 동일 합니다.

- 고객 네트워크/보안 제어의 토폴로지 위치는 사용자 및 Office 365 서비스 간의 최종적인 최종 네트워크를 결정 하며 네트워크 대기 시간 및 혼잡에 상당한 영향을 줄 수 있습니다.

- 고객은 중복성, 고가용성 및 재해 복구에 대 한 모범 사례에 따라 Office 365 용 Express 경로에 사용할 보안/주변 토폴로지를 디자인 하는 것이 좋습니다.

다음은 서로 다른 Azure Express 경로 연결 옵션과 위에서 설명한 경계 보안 모델을 비교 하는 Woodgrove 은행의 예입니다.
  
### <a name="example-1-securing-azure-expressroute"></a>예 1: Azure Express 경로 보호
  
Woodgrove 은행은 Azure Express를 구현 하는 것을 고려 하 고 있으며, [Office 365에 대 한 express](routing-with-expressroute.md) 를 사용 하 여 라우팅에 최적의 아키텍처를 계획 하 고, 위의 지침에 따라 대역폭 요구 사항을 파악 한 후에는 주변을 보호 하는 가장 좋은 방법을 결정
  
Woodgrove의 경우 여러 지역에 위치 하는 다국적 조직의 경우 보안은 모든 perimeters에 걸쳐 있어야 합니다. Woodgrove에 대 한 최적의 연결 옵션은 각 대륙에서 직원의 요구 사항을 처리 하기 위해 전 세계의 여러 피어 링 위치를 포함 하는 다중 지점 연결입니다. 각 대륙에는 대륙 내에 중복 된 Azure Express 회로가 포함 되어 있으며 보안은 이러한 모든 것을 확장 해야 합니다.
  
Woodgrove의 기존 인프라는 안정적 이며 추가 작업을 처리할 수 있으므로 Woodgrove 은행은 Azure Express 및 인터넷 경계 보안을 위해 인프라를 사용 하는 것이 가능 합니다. 그렇지 않을 경우 Woodgrove는 기존 장비를 보완 하거나 다른 유형의 연결을 처리 하기 위해 추가 장비를 구입할 수 있습니다.
  
## <a name="high-availability-and-failover-with-azure-expressroute"></a>고가용성 및 Azure Express를 사용한 장애 조치 (failover)
<a name="BKMK_high-availability"> </a>

각 egress에서 두 개 이상의 활성 회로를 프로 비전 가능 공급자에 게 제공 하는 것이 좋습니다. 고객에 대 한 오류가 표시 되는 가장 일반적인 위치 이며, 활성/활성 Express 경로를 프로 비전 하 여이를 쉽게 피할 수 있습니다. 또한 많은 Office 365 서비스는 인터넷을 통해서만 사용할 수 있으므로 두 개 이상의 활성/활성 인터넷 회선이 권장 됩니다.
  
네트워크의 egress 지점 내부에는 사용자의 사용 가능 여부를 증명 하는 방식으로 중요 한 역할을 하는 다양 한 장치 및 회로가 있습니다. 연결 시나리오 중 이러한 부분에는 대상 \ 사용자 또는 Office 365 Sla가 포함 되지 않지만, 최종-엔드 서비스에서 중요 한 역할을 수행 하는 것은 조직 내 사람들이 인식 합니다.
  
Office 365을 사용 하 고 운영 하는 사용자에 게 집중할 수 있으며, 한 구성 요소의 장애가 서비스를 사용 하는 peoples의 환경에 영향을 주는 경우 영향을 받는 사용자의 총 비율을 제한 하는 방법을 찾아보십시오. 장애 조치 (failover) 모드가 운용 복잡 한 경우 복구에 대 한 peoples의 환경을 고려 하 고 운용 단순 및 자동 장애 조치 (failover) 모드를 찾아보십시오.
  
네트워크 외부, Office 365, Express 경로 및 사용자 간의 공급자에는 모두 다른 수준의 가용성이 있습니다.
  
### <a name="service-availability"></a>서비스 가용성
  
- Office 365 서비스에는 개별 서비스에 대 한 가동 시간 및 가용성 메트릭이 포함 된 잘 정의 된 [서비스 수준 계약](https://technet.microsoft.com/library/office-365-service-level-agreement.aspx)에 포함 됩니다. Office 365에서 이러한 고가용성 수준을 유지 관리할 수 있는 한 가지 이유는 전역 Microsoft 네트워크를 사용 하 여 여러 Microsoft 데이터 센터 간에 장애 조치 (failover)를 수행 하는 개별 구성 요소입니다. 이 장애 조치 (failover)는 데이터 센터 및 네트워크에서 다중 인터넷 송신 지점으로 확장 되며,이 서비스를 사용 하는 사용자의 관점에서 장애 조치 (failover)를 사용할 수 있습니다.

- Express는 Microsoft 네트워크에 지와 Express 간 공급자 또는 파트너 인프라 간의 개별 전용 회로에 [99.9% 가용성 SLA를 제공](https://azure.microsoft.com/support/legal/sla/expressroute/v1_0/) 합니다. 이러한 서비스 수준은 각 피어 링 위치에서 중복 Microsoft 장비 및 네트워크 공급자 장비 간에 서로 다른 [두 개의 상호](https://azure.microsoft.com/documentation/articles/expressroute-introduction/) 구성으로 구성 되는, express 회로 수준에서 적용 됩니다.

### <a name="provider-availability"></a>공급자 가용성
  
- Microsoft의 서비스 수준 배치는가을-로 하는 공급자 또는 파트너에서 중지 됩니다. 이를 통해 가용성 수준에 영향을 주는 항목을 선택할 수도 있습니다. 이 경우에는 각 Microsoft 피어 링 위치에서 네트워크 경계와 공급자 연결 사이에 있는에 지 사항 공급자가 제공 하는 아키텍처, 가용성 및 복구 특성을 면밀 하 게 평가 해야 합니다. 중복성, 피어 링 장비의 논리적 및 물리적 측면, 운송 업체 제공 된 WAN 회로 및 추가 가치 서비스 추가 (예: NAT 서비스 또는 관리 되는 방화벽)에 대 한 세심 한 주의를 기울여야 합니다.

### <a name="designing-your-availability-plan"></a>가용성 계획 디자인
  
Office 365에 대 한 종단 간 연결 시나리오에 고가용성 및 복구 기능을 계획 하 고 디자인 하는 것이 좋습니다. 디자인에는 다음이 포함 되어야 합니다.
  
- 인터넷 및 Express 경로를 모두 포함 하 여 단일 오류 지점이 없습니다.

- 해당 하는 대부분의 실패 모드에 대 한 영향을 받는 사용자 수 및 해당 기간을 최소화 합니다.

- 가장 많이 발생 하는 오류 모드에서 단순 하 고 반복 가능 하며 자동 복구 프로세스를 최적화 합니다.

- 중요 한 성능 저하 없이 중복 경로를 통해 네트워크 트래픽 및 기능에 대 한 전체 요구 사항을 지원 합니다.

연결 시나리오에는 Office 365에 대 한 여러 독립 및 활성 네트워크 경로에 최적화 된 네트워크 토폴로지가 포함 되어야 합니다. 따라서 개별 장치 또는 장비 수준에서 중복성을 위해 최적화 된 토폴로지 보다 종단 간 가용성이 향상 됩니다.
  
> [!TIP]
> 사용자가 여러 대륙 또는 지역에 분산 되어 있고, 이러한 각 위치에서 단일 대상 회로가 있는 단일 온-프레미스 위치에 중복 WAN 회로를 연결 하는 경우, 사용자에 게는 서로 다른 지역을 가장 가까운 피어 링 위치에 연결 하는 독립 비트 단위 회로를 포함 하는 네트워크 토폴로지 디자인 보다 종단 간 서비스 가용성이 낮아집니다.
  
각 회선이 서로 다른 지리적 피어 링 위치로 연결 되는 두 개 이상의 Express 회로를 프로 비전 하는 것이 좋습니다. 사용자가 Office 365 서비스에 대 한 간 연결을 사용 하는 모든 지역에이 활성 활성 회로 쌍을 프로 비전 해야 합니다. 이를 통해 데이터 센터 또는 피어 링 위치와 같은 주요 위치에 영향을 주는 재해 동안 각 지역이 연결 된 상태로 유지 됩니다. 활성/활성으로 구성 하면 최종 사용자 트래픽이 여러 네트워크 경로에 분산 될 수 있습니다. 이렇게 하면 장치 또는 네트워크 장비 중단 시 영향을 받는 사용자의 범위가 줄어듭니다.
  
인터넷에서 하나의를 백업으로 사용 하는 것이 좋습니다.
  
### <a name="example-2-failover-and-high-availability"></a>예 2: 장애 조치 (Failover) 및 고가용성
  
Woodgrove 은행의 여러 지리적 디자인은 라우팅, 대역폭, 보안을 검토 했으며 이제 고가용성 검토를 진행 해야 합니다. Woodgrove는 세 가지 범주를 다루는 고가용성을 생각 합니다. 복구, 안정성 및 중복성
  
복구를 통해 Woodgrove가 오류를 빠르게 복구할 수 있습니다. 안정성은 Woodgrove가 시스템 내에서 일관 된 결과를 제공할 수 있도록 합니다. 중복성을 사용 하면 Woodgrove가 하나 이상의 미러된 인프라 인스턴스 간을 이동할 수 있습니다.
  
각에 지 구성 내에서 Woodgrove에는 중복 된 방화벽, 프록시 및 ID가 있습니다. 북미의 경우 Woodgrove는 자신의 달라스 데이터 센터에 하나의 edge 구성을 가지 며 해당 Virginia datacenter에는 다른 edge 구성을 포함 합니다. 각 위치에 여분의 장비가 있으면 해당 위치에 대 한 복원성이 제공 됩니다.
  
Woodgrove 은행의 네트워크 구성은 몇 가지 주요 원칙을 기반으로 작성 됩니다.
  
- 각 지역 내에는 여러 Azure Express 회로가 있습니다.

- 지역 내의 각 회로는 해당 지역 내의 모든 네트워크 트래픽을 지원할 수 있습니다.

- 라우팅은 가용성, 위치 등에 따라 하나 또는 다른 경로를 명확 하 게 사용 합니다.

- Azure Express 간 회로 간의 장애 조치 (Failover)는 Woodgrove에 필요한 추가 구성 또는 작업 없이 자동으로 수행 됩니다.

- 인터넷 회로 간의 장애 조치 (Failover)는 Woodgrove에 필요한 추가 구성 또는 작업 없이 자동으로 수행 됩니다.

이 구성에서는 실제 및 가상 수준에서의 중복성을 사용 하 여 Woodgrove 은행은 안정적인 방식으로 로컬 복구, 지역 복구 및 전역 복구를 제공할 수 있습니다. Woodgrove는 지역별 단일 Azure Express 경로를 평가 하 고 인터넷 장애 조치 (failover) 가능성을 확인 한 후이 구성을 선택 했습니다.
  
Woodgrove에 지역별 Azure Express 경로를 여러 개 사용할 수 없는 경우 북미 태평양의 Azure Express 회로에의 한 라우팅 트래픽이 허용 되지 않는 대기 시간을 더하고 필요한 DNS 전달자 구성에 따라 복잡성이 증가 합니다.
  
인터넷을 백업 구성으로 활용 하는 것은 권장 되지 않습니다. 이로 인해 Woodgrove의 안정성 원칙이 끊어지고 연결을 사용 하는 일관 된 환경이 제공 됩니다. 또한 수동 구성은 구성 된 BGP 광고 (NAT 구성, DNS 구성 및 프록시 구성)를 고려 하 여 장애 조치 (failover)를 수행 해야 합니다. 장애 조치 (failover) 복잡성이 추가 되 면 복구 시간이 증가 하 고 관련 단계를 진단 하 고 문제 해결 하는 기능이 저하 됩니다.
  
트래픽 관리 또는 Azure Express 경로를 계획 하 고 구현 하는 방법에 대 한 질문이 있나요? [네트워크 및 성능 지침](https://aka.ms/tune) 의 나머지 부분을 읽거나 [AZURE express 경로 FAQ](https://azure.microsoft.com/documentation/articles/expressroute-faqs/)를 읽습니다.
  
## <a name="working-with-azure-expressroute-providers"></a>Azure Express 경로 공급자 사용
<a name="BKMK_high-availability"> </a>

대역폭, 대기 시간, 보안 및 고가용성 계획을 기준으로 회로 위치를 선택 합니다. 회로를 배치할 최적의 위치를 확인 한 후에 [지역별 현재 공급자 목록을 검토](https://azure.microsoft.com/documentation/articles/expressroute-locations/)합니다.
  
공급자 또는 공급자와 협력 하 여 가장 적합 한 연결 옵션, 지점간, 다중 지점 또는 호스트를 선택 합니다. 대역폭 및 기타 중복 구성 요소가 라우팅 및 고가용성 디자인을 지 원하는 경우에는 연결 옵션을 혼합 하 고 일치 시킬 수 있습니다.
  
다음의 간단한 링크를 사용할 수 있습니다. [https://aka.ms/planningexpressroute365](https://aka.ms/planningexpressroute365)
  
## <a name="related-topics"></a>관련 항목
<a name="BKMK_high-availability"> </a>

[Office 365 네트워크 연결 평가](assessing-network-connectivity.md) 
  
[Office 365용 Azure ExpressRoute](azure-expressroute.md)
  
[Office 365 연결에 대한 ExpressRoute 관리](managing-expressroute-for-connectivity.md)
  
[Office 365용 ExpressRoute를 사용한 라우팅](routing-with-expressroute.md)
  
[Office 365용 ExpressRoute 구현](implementing-expressroute.md)
  
[Office 365 시나리오에서 (으)로의 BGP 커뮤니티 사용](bgp-communities-in-expressroute.md)
  
[비즈니스용 Skype Online의 미디어 품질 및 네트워크 연결 성능](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[비즈니스용 Skype Online의 네트워크 최적화](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)
  
[비즈니스용 Skype Online의 ExpressRoute 및 QoS](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[ExpressRoute를 사용하는 호출 흐름](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[초기 계획 및 성능 기록을 사용하여 Office 365 성능 조정](performance-tuning-using-baselines-and-history.md)
  
[Office 365 성능 문제 해결 계획](performance-troubleshooting-plan.md)
  
[Office 365 URL 및 IP 주소 범위](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Office 365 네트워크 및 성능 조정](network-planning-and-performance.md)
  
[Office 365 끝점 FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
