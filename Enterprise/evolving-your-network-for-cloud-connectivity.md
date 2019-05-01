---
title: 클라우드 연결을 위해 네트워크 개선
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/28/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 83e2859a-c673-47c4-880a-01cdfdadb93e
description: '요약: 클라우드 채택으로 인해 네트워크 인프라 투자에 대 한 새로운 접근 방법이 필요한 방식에 대해 설명 합니다.'
ms.openlocfilehash: c8fba120292b89894850312a84fd6067d925a07f
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487244"
---
# <a name="evolving-your-network-for-cloud-connectivity"></a>클라우드 연결을 위해 네트워크 개선

 **요약:** 클라우드 채택에서 네트워크 인프라 투자에 대 한 새로운 접근 방식을 필요로 하는 방식을 이해 합니다.
  
클라우드 마이그레이션으로 인해 회사 네트워크 내부 및 외부의 트래픽 흐름 양과 특성이 달라지고 있습니다. 또한 보안 위험을 완화시키는 방법도 영향을 받고 있습니다.
  
- 클라우드 이전
    
    대부분의 네트워킹 인프라 투자가 온-프레미스 데이터 센터에 대 한 사용 가능, 안정성 및 안정적인 연결을 보장 하는 데 소요 되었습니다. 대부분의 조직에서 내부 비즈니스 운영에는 인터넷 연결이 중요 하지 않습니다. 네트워크 경계는 보안 침해에 대 한 기본 방어책 이었습니다.
    
- 클라우드 후
    
    신규 및 마이그레이션된 생산성 및 IT 워크 로드를 클라우드에서 실행 하면 인프라 투자가 온-프레미스 데이터 센터에서 인터넷 연결로 전환 되므로, 이제 내부 비즈니스 운영에 중요 합니다. 페더레이션 연결은 id 및 데이터를 보호 하는 보안 전략을 네트워크를 통해 전달 하 고 Microsoft 클라우드 서비스에 대 한 연결을 가리키기 위해 이동 합니다.
    
네트워크 인프라 투자가 연결로 시작 됩니다. 추가 투자는 클라우드 서비스의 범주에 따라 달라 집니다.
  
- **SaaS (Software as a Service)** microsoft SaaS 서비스에는 Office 365, microsoft Intune 및 microsoft Dynamics 365가 포함 됩니다. 사용자가 SaaS 서비스를 성공적으로 채택 해야 하는 경우에는 가용성이 높고 인터넷에 대 한 고성능 연결을 사용 하거나 Microsoft 클라우드 서비스에 직접 의존 해야 합니다.
    
    네트워크 아키텍처는 안정적이 고 중복 된 연결 및 충분 한 대역폭을 중심으로 합니다. 지속적인 투자에는 성능 모니터링 및 조정 등이 포함 됩니다.
    
- **Azure PaaS (Platform as a Service)** Microsoft SaaS 서비스에 대 한 투자 외에도 다중 사이트 또는 지리적으로 분산 된 PaaS 응용 프로그램은 클라이언트 트래픽을 분산 하기 위해 Azure traffic Manager를 설계 해야 할 수 있습니다. 지속적인 투자에는 성능 및 트래픽 분산 모니터링 및 장애 조치 (failover) 테스트가 포함 됩니다.
    
- **Azure IaaS (인프라 as a Service)** Microsoft SaaS 및 PaaS 서비스에 대 한 투자 외에도, IaaS에서 IT 작업을 실행 하는 경우 가상 컴퓨터를 호스트 하는 Azure virtual network의 디자인 및 구성, 라우팅, IP에서 실행 되는 응용 프로그램에 대 한 보안 연결 필요 주소 지정, DNS 및 부하 분산 지속적인 투자에는 성능 및 보안 모니터링과 문제 해결이 포함 됩니다.

[Microsoft 365](https://www.microsoft.com/microsoft-365) 는 Office 365, EMS (Enterprise Management + Security) 및 Windows 10의 조합입니다. Microsoft 365에서는 여러 SaaS 및 Azure 서비스를 함께 사용 하 여 모든 사람이 창조적이 고 안전 하 게 함께 작업할 수 있도록 하는 완벽 한 지능형 솔루션을 결합 합니다.
    
## <a name="areas-of-networking-investment-for-success-in-the-cloud"></a>클라우드의 성공에 대 한 네트워킹 투자 영역

엔터프라이즈 조직은 체계적인 접근 방식을 사용 하 여 인트라넷 및 인터넷에서 네트워크 처리량을 최적화 하는 것을 이점이 있습니다. 또한가 수 연결을 통해 혜택을 얻을 수도 있습니다.
  
### <a name="optimize-intranet-connectivity-to-your-edge-network"></a>에 지 네트워크에 대 한 인트라넷 연결 최적화

대부분의 조직에서는 온-프레미스 데이터 센터에서 실행 되는 응용 프로그램에 대 한 인트라넷 연결 및 성능을 최적화 했습니다. Microsoft 클라우드에서 생산성과 IT 작업을 실행 하는 경우 추가 투자가 높은 연결 가용성을 보장 하 고,에 지 네트워크와 인트라넷 사용자 간의 트래픽 성능이 최적이 되도록 해야 합니다.
  
### <a name="optimize-throughput-at-your-edge-network"></a>에 지 네트워크에서 처리량 최적화

일상 생산성 트래픽이 클라우드로 이동 하는 경우에도 최신 상태를 유지 하 고 고가용성을 제공 하 고 최대 부하를 충족 하기에 충분 한 용량을 갖게 하려면에 지 네트워크의 시스템 집합을 면밀 하 게 검토 해야 합니다.
  
### <a name="for-a-high-sla-to-azure-office-365-and-dynamics-365-use-expressroute"></a>Azure, Office 365 및 Dynamics 365에 대 한 높은 SLA를 보려면 express를 사용 합니다.

에 지 네트워크에서 현재 인터넷 연결을 사용할 수 있지만 Microsoft 클라우드 서비스와의 트래픽은 인터넷으로 들어오는 다른 인트라넷 트래픽과 파이프를 공유 해야 합니다. 또한 Microsoft 클라우드 서비스에 대 한 트래픽은 인터넷 트래픽 혼잡의 영향을 받습니다.
  
높은 SLA 및 최적의 성능을 위해서는 네트워크와 Azure, Office 365, Dynamics 365 또는 3 모두 간의 전용 WAN 연결을 사용 하는 방법 \ 사용자를 사용할 것을 권장 합니다. 
  
express에서 전용 연결을 위해 기존 네트워크 공급자를 활용할 수 있습니다. 이 방법으로는 국내 분산 조직의 경우에도, 기본적으로로 연결 된 리소스는 WAN에 있는 것 처럼 나타납니다.
  
자세한 내용은 [Microsoft 클라우드 연결용 express](expressroute-for-microsoft-cloud-connectivity.md)를 참조 하세요.
  
## <a name="scope-of-network-investments"></a>네트워크 투자 범위

네트워크 투자 범위는 클라우드 서비스 범주에 따라 다릅니다. Microsoft 클라우드를 통한 투자는 네트워킹 팀에 대 한 투자를 극대화 합니다. 예를 들어, IaaS 서비스용 투자는 모든 투자 영역에 적용 됩니다.
  
|||||
|:-----|:-----|:-----|:-----|
|투자 영역  <br/> |SaaS  <br/> |PaaS  <br/> |IaaS  <br/> |
|신뢰할 수 있는 안정적인 인터넷 연결 설계자 (충분 한 대역폭 포함)  <br/> |적용  <br/> |적용  <br/> |적용  <br/> |
|성능에 대 한 인터넷 처리량 모니터링 및 조정  <br/> |적용  <br/> |적용  <br/> |적용  <br/> |
|인터넷 연결 및 처리량 문제 해결  <br/> |적용  <br/> |적용  <br/> |적용  <br/> |
|다른 끝점에 대 한 트래픽의 부하를 분산 하도록 Azure Traffic Manager 디자인  <br/> ||적용  <br/> |적용  <br/> |
|Azure virtual network에 대 한 신뢰할 수 있는 중복 및 안정적인 연결 설계자  <br/> |||적용  <br/> |
|Azure 가상 컴퓨터에 대 한 안전한 연결 디자인  <br/> |||적용  <br/> |
|온-프레미스 위치와 가상 네트워크 간의 라우팅 디자인 및 구현  <br/> |||적용  <br/> |
|내부 및 인터넷 연결 IT 워크 로드에 대 한 부하 분산 설계 및 구현  <br/> |||적용  <br/> |
|가상 컴퓨터 연결 및 처리량 문제 해결  <br/> |||적용  <br/> |
   
## <a name="next-step"></a>다음 단계

[Microsoft 클라우드 연결의 일반적인 요소](common-elements-of-microsoft-cloud-connectivity.md)

## <a name="see-also"></a>참고 항목

[Microsoft Cloud Networking for Enterprise Architects](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Microsoft 클라우드 IT 아키텍처 리소스](microsoft-cloud-it-architecture-resources.md)



