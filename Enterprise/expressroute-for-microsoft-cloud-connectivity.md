---
title: Microsoft 클라우드 연결을 위한 ExpressRoute
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/03/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: bf2295c4-d411-49cd-aaa5-116a4a456c5a
description: '요약: ExpressRoute 하는 방법 더욱 빠르고 안정적 연결을 포함 하는 Microsoft의 클라우드 서비스와 플랫폼을 이해 합니다.'
ms.openlocfilehash: d3a19dcd3ce8732b3349c5cacce5b64159850682
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915493"
---
# <a name="expressroute-for-microsoft-cloud-connectivity"></a>Microsoft 클라우드 연결을 위한 ExpressRoute

 **요약:** ExpressRoute 하는 방법 더욱 빠르고 안정적 연결을 포함 하는 Microsoft의 클라우드 서비스와 플랫폼을 이해 합니다.
  
ExpressRoute는 Microsoft 클라우드에 대해 개인, 전용, 고처리량의 네트워크 연결을 제공합니다.
  
## <a name="expressroute-to-the-microsoft-cloud"></a>Microsoft 클라우드로 ExpressRoute

ExpressRoute에 연결 하지 않고 Microsoft 클라우드 네트워킹 경로 다음과 같습니다.
  
**그림 1: ExpressRoute가 없는 네트워킹 경로**

![그림 1: ExpressRoute가 없는 네트워킹 경로](media/Network-Poster/ExpressRoute.png)
  
그림 1는 온-프레미스 네트워크 및 Microsoft 클라우드 간에 일반적인 경로 표시 합니다. WAN 통해 인터넷에 연결 하는 온-프레미스 네트워크에 지는 ISP에 대 한 링크입니다. 다음의 트래픽은 인터넷을 통해 Microsoft 클라우드의 가장자리에 있습니다. Microsoft 클라우드 내에서 클라우드 서비스에는 Office 365, Microsoft Azure, Microsoft Intune 및 Dynamics 365 포함 합니다. 조직의 사용자는 온-프레미스 네트워크 또는 인터넷에 있을 수 있습니다.
  
부분만 ExpressRoute 연결 하지 않고 수를 제어 (하는 서비스 공급자와 관계가)은 ISP와 사용자 온-프레미스 네트워크 가장자리 사이의 연결 하 여 Microsoft 클라우드 트래픽 경로입니다. 
  
ISP와 Microsoft 클라우드 가장자리 사이의 경로 최상의 배달 시스템 인터넷 중단, 교통 혼잡 사실 및 악의적인 사용자가 모니터링에 따라 달라 집니다.
  
로밍 또는 원격 사용자와 같은 인터넷 사용자가 인터넷을 통해 Microsoft 클라우드 자신의 트래픽을 보냅니다.
  
다음은 ExpressRoute 연결을 사용 하 여 Microsoft 클라우드 네트워킹 경로입니다.
  
**그림 2: ExpressRoute 사용한 네트워킹 경로**

![그림 2: ExpressRoute 사용한 네트워킹 경로](media/Network-Poster/ExpressRoute-post.png)
  
그림 2는 두 네트워킹 경로 보여줍니다. Microsoft Intune로의 트래픽은 기본 인터넷 트래픽와 같은 경로입니다. ExpressRoute 연결, 온-프레미스 네트워크의 가장자리와 Microsoft 클라우드 가장자리 사이의 전용된 경로 통해 Office 365, Microsoft Azure 및 Dynamics 365 여행에 대 한 트래픽입니다.
  
ExpressRoute 연결을 사용할 경우 서비스 공급자와 관계를 통해 제어 이제, microsoft 프로그램 가장자리에서 전체 트래픽 경로 통해 클라우드 지 합니다. 이 연결에는 예측 가능한 성능과 [99.95% 가동 시간 SLA](https://azure.microsoft.com/support/legal/sla/expressroute/v1_3/)제공할 수 있습니다.
  
이제 예측 가능한 처리량과 대기 시간을 Office 365, Azure, 및 Dynamics 365 서비스에 대 한 서비스 공급자의 연결을 기반으로 계산할 수 있습니다. 이 이번에는 Microsoft Intune에 대 한 ExpressRoute 연결 지원 되지 않습니다.
  
ExpressRoute 연결을 통해 전송 되는 트래픽 더이상 인터넷 중단, 교통 혼잡 사실 및 모니터링에 따라 달라 집니다.
  
로밍 또는 원격 사용자와 같은 인터넷의 사용자에는 인터넷을 통해 Microsoft 클라우드 자신의 트래픽을 여전히 보냅니다. 온-프레미스 네트워크에 대 한 원격 액세스 연결을 통해 ExpressRoute 연결을 통해 전송 되는 Azure IaaS에서 호스팅되는 비즈니스 응용 프로그램의 인트라넷 라인에 대 한 트래픽은 예외가입니다.
  
ExpressRoute 연결의 경우와 인증서 해지 목록 확인 하 고, 일부 트래픽이 여전히 DNS 쿼리 예: 인터넷을 통해 전송 하 고 콘텐츠 배달 네트워크 (CDN)을 요청 합니다.
  
자세한 내용은 다음의 추가 리소스를 참조 하십시오.
  
- [Office 365용 Express 경로](https://aka.ms/expressrouteoffice365)
    
- [Azure에 대 한 ExpressRoute](https://azure.microsoft.com/services/expressroute/)
    
## <a name="advantages-of-expressroute-for-azure"></a>Azure에 대 한 ExpressRoute의 장점

ExpressRoute를 사용 하 여 Azure 기반 클라우드 서비스에 대 한 경우의 몇가지 이점은 다음과 같습니다.
  
- **예측 가능한 성능:** Microsoft 클라우드의 가장자리를 전용된 경로 사용 하 여 성적 인터넷 공급자 중단 될 수 없는 및 인터넷 트래픽이 급격히 증가할 합니다. 확인할 수 있으며 Microsoft 클라우드 처리량과 대기 시간 SLA에 책임이 있는 공급자를 보관할 수 있습니다.
    
- **대화 트래픽에 대 한 데이터 개인정보:** 전용된 ExpressRoute 대 한 연결을 통해 보내는 트래픽을 인터넷 모니터링 또는 패킷 캡처 및 분석 악의적인 사용자에 게 영향을 받지 않습니다. 멀티 프로토콜 레이블 전환 MPLS 기반 WAN 링크를 사용 하는 것 만큼 안전 것입니다.
    
- **높은 처리량 연결:** Exchange 공급자 및 네트워크 서비스 공급자가 ExpressRoute 연결에 대 한 전체 지원이 포함 된 최대 10 개의 g b p s 링크 Microsoft 클라우드를 얻을 수 있습니다.
    
- **일부 구성에 대 한 비용 절감:** ExpressRoute 연결에는 추가 비용 변수가 이기는 하지만 일부 경우에 단일 ExpressRoute 연결 수 비용을 줄일 Microsoft 클라우드 서비스에 대 한 적절 한 처리량을 제공 하 여 조직의 여러 위치에서 인터넷 용량 증가 보다 합니다.
    
ExpressRoute 연결 된 모든 구성에 더 높은 성능은 보장 되지 않습니다. 지역 Microsoft 데이터 센터에서 소수의 홉만 고대역폭 인터넷 연결을 보다 낮은 대역폭 ExpressRoute 연결을 통해 더 낮은 성능을 제공 하는 것이 불가능 합니다.
  
Office 365와 함께 ExpressRoute를 사용 하는 것에 대 한 최신 권장 사항에 대 한 [Office 365에 대 한 ExpressRoute](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd)를 참조 합니다.
  
## <a name="expressroute-connectivity-models"></a>ExpressRoute 연결 모델

표 1은 ExpressRoute 연결에 대 한 세가지 기본 연결 모델을 보여줍니다.
  
|**클라우드 exchange에 함께 배치**|**지점간 이더넷**|**모든-를-모든 (IP VPN) 연결**|
|:-----|:-----|:-----|
|![ExpressRoute 연결 모델: 클라우드 Exchange에 공동으로 배치됨](media/Network-Poster/ER-Conn1.png)|![ExpressRoute 연결 모델: 지점 간 이더넷](media/Network-Poster/ER-Conn2.png)|![ExpressRoute 연결 모델: Any-to-Any(IP VPN) 연결 ](media/Network-Poster/ER-Conn3.png)|
|데이터 센터는 클라우드 exchange와 시설에 있는 공동, 하는 경우에 대 한 가상 크로스-연결 공동 위치 공급자의 이더넷 exchange 통해 Microsoft 클라우드를 주문할 수 있습니다.  <br/> |데이터 센터를 귀하의 구내에 있는 경우에 Microsoft 클라우드에 연결할 지점간 이더넷 링크를 사용할 수 있습니다.  <br/> |이미 조직의 사이트를 연결 하려면 IP VPN (MPLS) 공급자를 사용 하는, 사용자의 개인 WAN에서 다른 위치로 처럼 작동 하는 Microsoft 클라우드에 대 한 ExpressRoute 연결.  <br/> |
   
 **표 1: ExpressRoute 연결 모델**
  
## <a name="expressroute-peering-relationships-to-microsoft-cloud-services"></a>Microsoft 클라우드 서비스에 대 한 ExpressRoute 피어 링 관계

단일 ExpressRoute 연결에 최대 3 개의 서로 다른 테두리 게이트웨이 프로토콜 (BGP) 피어 링 관계 Microsoft 클라우드의 다른 부분을 지원합니다. BPG 피어 관계를 사용 하 여 트러스트를 설정 하 고 라우팅 정보를 교환 합니다.
  
**그림 3: 단일 ExpressRoute 연결의 세 가지 다른 BGP 관계**

![그림 3: 단일 ExpressRoute 연결의 세 가지 다른 BGP 관계](media/Network-Poster/ERPeering.png)
  
그림 3에 대 한 ExpressRoute 연결을 온-프레미스 네트워크에서 나옵니다. ExpressRoute 연결 세 논리 피어 관계를 포함합니다. Office 365 및 Dynamcs CRM Online 등의 Microsoft SaaS 서비스 Microsoft 피어 링 관계를 이동 합니다. Azure PaaS 서비스 공용 피어 링 관계를 이동합니다. 개인 피어 링 관계 Azure IaaS 하 고 가상 컴퓨터를 호스팅하는 가상 네트워크 게이트웨이 이동 합니다.
  
Microsoft 피어 링 BGP 관계: 
  
- Office 365 및 Dynamics 365 서비스의 공용 주소로 DMZ에서 라우터에서 시작 됩니다. 
    
- 양방향 시작 하는 통신을 지원합니다.
    
공용 피어 링 BGP 관계:
  
- Azure 서비스 공용 IP 주소를 DMZ에서 라우터에서 시작 됩니다.
    
- 온-프레미스 시스템에만에서 시작 된 단방향 통신을 지원 합니다. 피어 링 관계 Azure PaaS 서비스에서 시작 된 통신을 지원 하지 않습니다.
    
개인 피어 링 BGP 관계:
  
- Azure VNets에 할당 하는 개인 IP 주소에 조직의 네트워크의에 지에 라우터에서 시작 됩니다.
    
- 양방향 시작 하는 통신을 지원합니다.
    
- 조직 네트워크 내부적으로 일관 된 주소 지정 및 라우팅을 사용 하 여 전체 Microsoft 클라우드를 확장 한 것입니다.
    
## <a name="example-of-application-deployment-and-traffic-flow-with-expressroute"></a>ExpressRoute 사용 하 여 응용 프로그램 배포 및 트래픽 흐름의 예

방법의 트래픽은 ExpressRoute 연결 전체에 걸쳐 및 Microsoft 클라우드 내에서 원본 및 대상 및 응용 프로그램 동작 간의 경로의 홉에서 경로의 함수입니다. 사이트 마다 VPN 연결을 통해는 온-프레미스 SharePoint 팜의 액세스 하는 Azure 가상 컴퓨터에서 실행 중인 응용 프로그램의 예는 다음과 같습니다.
  
**그림 4: 온-프레미스 SharePoint 팜에 액세스하는 Azure 가상 컴퓨터의 응용 프로그램**

![그림 4: 온-프레미스 SharePoint 팜에 액세스하는 Azure 가상 컴퓨터의 응용 프로그램](media/Network-Poster/ER-App-Flow1.png)

  
그림 4에서는 응용 프로그램 서버 간에 온-프레미스 SharePoint 팜, 온-프레미스 네트워크 및 Azure IaaS, Azure IaaS 가상 컴퓨터를 사용 하는 트래픽과으로 실행 되는 응용 프로그램 서버에서에서 가상 네트워크 간의 사이트 마다 VPN 연결 흐름 및 SharePoint 팜 합니다.
  
응용 프로그램의 온-프레미스 DNS를 사용 하 여 SharePoint 팜의 IP 주소를 찾아 사이트 마다 VPN 연결을 통해 모든 트래픽은 합니다.
  
이 조직 Office 365의 SharePoint Online으로 온-프레미스 SharePoint 팜의 마이그레이션되며 ExpressRoute 연결을 배포 합니다.
  
**그림 5: 온-프레미스 SharePoint 팜을 SharePoint Online으로 이동**

![그림 5: 온-프레미스 SharePoint 팜을 SharePoint Online으로 이동](media/Network-Poster/Hairpin1.png)
  
그림 5 표시 피어 링 관계를 가진 ExpressRoute 연결의 추가 Microsoft SaaS 및 Office 365 하 고 Azure IaaS 가상 네트워크에서 응용 프로그램 서버를 포함 합니다. SharePoint 온-프레미스 팜에 Office 365로 마이그레이션 되었습니다.
  
Microsoft 및 개인 피어 관계:
  
- Azure 가상 네트워크 게이트웨이에서 온-프레미스 위치는 ExpressRoute 연결을 통해 사용할 수 있습니다.
    
- Office 365 구독에서 프록시 서버와 같은 지 장치의 공용 IP 주소는 ExpressRoute 연결을 통해 사용할 수 있습니다.
    
- 온-프레미스 네트워크에서에 지, Azure VNet의 개인 IP 주소 및 Office 365의 공용 IP 주소는 사용할 수 있는 ExpressRoute 연결을 통해입니다.
    
응용 프로그램 액세스 하는 Url의 SharePoint Online, 프록시 서버는 지에 ExpressRoute 연결을 통해 해당 트래픽을 전달 합니다. 
  
프록시 서버에서 SharePoint Online의 IP 주소를 찾으면 ExpressRoute 연결을 통해 다시 트래픽을 전달 합니다. 응답 트래픽은 역방향 경로 이동 합니다.
  
**그림 6: SharePoint 팜이 Office 365의 SharePoint Online으로 마이그레이션되었을 때의 트래픽 흐름**

![그림 6: SharePoint 팜이 Office 365의 SharePoint Online으로 마이그레이션되었을 때의 트래픽 흐름](media/Network-Poster/Hairpin2.png)

  
그림 6 응용 프로그램 서버와 Office 365의 SharePoint Online 간의 트래픽을 개인 피어 링 관계 온-프레미스 네트워크 경계를 응용 프로그램 서버에서 한 가장자리에서 다음을 통해 Microsoft 피어 링 관계를 통해 흐르는 하는 방법을 보여줍니다. Office 365 합니다.
  
라우팅 및 응용 프로그램 동작의 결과 고정 하는 머리가 반환이 됩니다.
  
## <a name="expressroute-and-microsofts-cloud-network"></a>ExpressRoute 및 Microsoft의 클라우드 네트워크

ExpressRoute 연결 서로 다른 두 버전에서 사용할 수 있는: ExpressRoute 및 ExpressRoute 프리미엄 합니다.
  
### <a name="expressroute"></a>ExpressRoute

방법의 트래픽은 조직 네트워크 사이의 Microsoft 데이터 센터의 조합입니다.
  
- 사용자 위치입니다.
    
- Microsoft 클라우드 피어 링 위치 (Microsoft 지에 연결 하는 실제 위치).
    
- Microsoft 데이터 센터 위치입니다.
    
Microsoft 데이터 센터 및 위치를 피어 링 클라우드는 모든 Microsoft 클라우드 네트워크에 연결 됩니다.
  
Microsoft 클라우드 피어 링 위치에 대 한 ExpressRoute 연결을 만들 때에 Microsoft 클라우드 네트워크와 동일한 대륙의 모든 Microsoft 데이터 센터 위치에 연결 된 있습니다. Microsoft 클라우드 네트워크를 통해 클라우드 피어 링 위치와 대상 Microsoft 데이터 센터 간의 트래픽의 수행 합니다.
  
이 모든-를-모든 연결 모델에 대 한 로컬 Microsoft 데이터 센터에 최적이 아닌 배달 될 수 있습니다.
  
**그림 7: 단일 ExpressRoute 연결을 사용하는 지리적으로 분산된 조직의 예**

![그림 7: 단일 ExpressRoute 연결을 사용하는 지리적으로 분산된 조직의 예](media/Network-Poster/MSNet1.png)
  
그림 7 두 위치와 조직 미국, 대한민국 북서쪽에서 위치 1 및 북동쪽에서 위치 2를 보여줍니다. 모든-를-모든 WAN 공급자에서 연결 합니다. 이 조직에 서울에 Microsoft 피어 링 위치로 ExpressRoute 연결이 합니다. 위치 2에서는 동부 지역 데이터 센터에 대해 북동쪽에서 해야 서 부 지역 Microsoft 피어 링 위치에 이르는 모든 조직의 WAN에서 출장 트래픽과 했다가 다시 국가에서 Microsoft 클라우드 네트워크를 통해 동부 데이터 센터입니다.
  
최적의 배달에 대 한 지역 Microsoft 클라우드 피어 링 위치를 여러 ExpressRoute 연결을 사용 합니다. 
  
**그림 8: 지역 데이터 센터로의 최적 전달을 위한 여러 개의 ExpressRoute 연결 사용**

![그림 8: 지역 데이터 센터로의 최적 전달을 위한 여러 개의 ExpressRoute 연결 사용](media/Network-Poster/MSNet2.png)
  
그림 8 지역별로 로컬 Microsoft 피어 링 위치를 각 위치에 대 한 두 ExpressRoute 연결 된 동일한 조직에 나와 있습니다. 이 구성에서 위치 2에서는 동부 지역 데이터 센터에 대해 북동쪽에서 트래픽은 동부 피어 링 위치에 직접, Microsoft 클라우드 네트워크를 다음 동부 지역 데이터 센터에 있습니다.
  
여러 ExpressRoute 연결을 제공할 수 있습니다.
  
- 지역별로 로컬 Microsoft 데이터 센터 위치를 성능이 향상 됩니다.
    
- 로컬 ExpressRoute 연결을 사용할 수 없게 하는 경우 Microsoft 클라우드로 가용성을 향상 합니다.
    
이 동일한 대륙에는 조직에 적합 한 작동합니다. 그러나 조직의 대륙 외부 Microsoft 데이터 센터에 대 한 트래픽 인터넷을 통해 이동 합니다.
  
Microsoft 클라우드 네트워크를 통해 intercontinental 트래픽에 대 한 ExpressRoute 프리미엄 연결을 사용 해야 합니다.
  
### <a name="expressroute-premium"></a>ExpressRoute 프리미엄

대륙에 분산 전역적으로 하는 조직에서는 ExpressRoute Premium을 사용할 수 있습니다. 
  
ExpressRoute 프리미엄와 모든 대륙에 어떤 Microsoft 피어 링 위치에서 모든 대륙에 모든 Microsoft 데이터 센터에 도달할 수 있습니다. 대륙 간의 트래픽은 Microsoft 클라우드 네트워크를 통해 수행 됩니다.
  
여러 ExpressRoute 프리미엄 연결이 설정 된 다음을 포함할 수 있습니다.
  
- Continentally 로컬 Microsoft 데이터 센터에 성능이 향상 됩니다.
    
- 로컬 ExpressRoute 연결을 사용할 수 없게 하는 경우 전역 Microsoft 클라우드로 가용성을 향상 합니다.
    
ExpressRoute 프리미엄 Office 365 기반 ExpressRoute 연결에 필요 합니다. 그러나 500 개 보다 사용이 허가 된 사용자와 기업에 대 한 추가 비용 없이 방법이 있습니다.
  
**전세계 Microsoft 클라우드 네트워크의 그림 9:**

![그림 9: 전 세계 Microsoft 클라우드 네트워크](media/Network-Poster/MSNet3.png)
  
그림 9 대륙 및 세계와의 상호 연결의 지역에 걸쳐 있는 네트워크를 사용 하 여 전세계 Microsoft 클라우드 네트워크의 논리 다이어그램을 보여줍니다. 각 대륙에 Microsoft 클라우드 네트워크의 부분을 함께 글로벌 엔터프라이즈 연결을 만듦 ExpressRoute 프리미엄 해당 지역 허브 사무실에서 로컬 Microsoft 피어 링 위치를
  
지역 사무소에 대 한 Office 365 트래픽을 적절 한:
  
- Office 365 데이터 센터를 대륙 대륙 내에서 Microsoft 클라우드 네트워크를 통해 전달 됩니다.
    
- 다른 대륙에 office 365 데이터 센터 intercontinental Microsoft 클라우드 네트워크를 통해 전달 됩니다.
    
자세한 내용은 다음 항목을 참조하십시오.
  
- [Office 365 교육에 대 한 azure ExpressRoute](https://channel9.msdn.com/series/aer/)
    
- [Office 365의 네트워크 계획 및 성능 조정](https://aka.ms/tune)
    
- [Office 365 성능 관리](https://mva.microsoft.com/en-US/training-courses/office-365-performance-management-8416)
    
## <a name="expressroute-options"></a>ExpressRoute 옵션

또한 ExpressRoute 배포는 다음 옵션을 통합할 수 있습니다.
  
- **에 지에 대 한 보안:** 예: 트래픽 검사 또는 침입/맬웨어 감지 ExpressRoute 연결을 통해 보내고 받은 트래픽에 대 한 고급 보안을 제공 하려면 보안 어플라이언스 DMZ 내에서 또는 인트라넷의 테두리에 트래픽 경로에 배치 합니다.
    
    Azure Vm 인터넷 위치를 사용 하 여 직접 트래픽을 시작 하지 못하도록 하려면 Vm에 대 한 인터넷 트래픽을 Microsoft에 기본 경로 알립니다. 인터넷에 대 한 트래픽 ExpressRoute 연결을 통해 및 온-프레미스 프록시 서버를 통해 라우팅됩니다. Azure Vm 트래픽은 Azure PaaS 서비스 또는 Office 365 ExpressRoute 연결을 통해 다시 라우팅됩니다.
    
- **WAN 최적화 프로그램이:** 크로스-프레미스 Azure에 대 한 개인 피어 링 연결의 양쪽에 WAN 최적화 프로그램이 배포할 수 가상 네트워크 (VNet). Azure VNet 내부 Azure 마켓플레이스 및 라우팅 사용자 정의에서 WAN 최적화 프로그램이 네트워크 기기 기기를 통해 트래픽을 라우팅 하는데 사용 합니다.
    
- **서비스의 품질:** IPv4 헤더의 트래픽 코드 포인트 DSCP (Differentiated Services) 값을 사용 하 여 음성, 비디오/대화형, 또는 최상의 배달에 대 한 표시 합니다. 이 비즈니스 온라인 트래픽에 대 한 Microsoft 피어 링 관계 및 Skype 특히 중요 합니다.
    
자세한 내용은 다음의 추가 리소스를 참조 하십시오.
  
- [Office 365용 Express 경로](https://aka.ms/expressrouteoffice365)
    
- [Office 365 교육에 대 한 azure ExpressRoute](https://channel9.msdn.com/series/aer/)
    
- [Azure에 대 한 ExpressRoute](https://azure.microsoft.com/services/expressroute/)
    
## <a name="next-step"></a>다음 단계

[Microsoft SaaS에 대한 네트워킹 디자인](designing-networking-for-microsoft-saas.md)

## <a name="see-also"></a>참고 항목

[Microsoft Cloud Networking for Enterprise Architects](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Microsoft 클라우드 IT 아키텍처 리소스](microsoft-cloud-it-architecture-resources.md)

[Microsoft의 엔터프라이즈 클라우드 로드맵: IT 의사 결정권자를 위한 리소스](https://sway.com/FJ2xsyWtkJc2taRD)



