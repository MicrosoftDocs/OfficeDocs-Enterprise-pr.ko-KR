---
title: "Contoso Corporation에 대 한 네트워킹"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 014b3710-e6e9-485c-8550-975d510eb2fc
description: "요약: 정 및 Microsoft 하이브리드 클라우드의 요소를 이해 합니다."
ms.openlocfilehash: 0943864c8a9982eba00a139617ebe17d39cdde4e
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/11/2018
---
# <a name="networking-for-the-contoso-corporation"></a>Contoso Corporation에 대 한 네트워킹

 **요약:** 정 및 Microsoft 하이브리드 클라우드의 요소를 이해 합니다.
  
클라우드 (포함) 인프라를 채택 하는를 Contoso의 네트워크 엔지니어 네트워크 트래픽을 클라우드 기반 서비스 여행 하는 방식으로 기본 shift을 실현 합니다. 온-프레미스 서버와 데이터 센터에 대 한 트래픽만 최적화 하는 대신 인터넷 가장자리 및 인터넷을 통해 트래픽을 최적화와 같은 주의 지불 해야 합니다.
  
## <a name="contosos-networking-infrastructure"></a>Contoso의 네트워킹 인프라

Contoso는 그림 1에 표시 된 네트워킹 인프라입니다.
  
**그림 1: Contoso의 WAN 인프라**

![본사, 지역 허브 및 위성 사무실을 연결하는 Contoso의 WAN 인프라](images/Contoso_Poster/Contoso_WW_Net.png)
  
그림 1 전세계로 및 국가 집합이 및 위성 사무실 사이트간 WAN 링크가 Contoso의 사무실을 보여줍니다.
  
자신의 네트워크의 추가 요소는 다음과 같습니다.
  
- 온-프레미스 네트워크
    
    WAN 링크를 통해 지역 사무실과 지사 허브 및 스포크 구성에서 위성 사무실에 파리 본사를 연결합니다. 각 office 내에서 라우터를 호스트 또는 개인 IP 주소 공간을 사용 하는 서브넷에 무선 액세스 지점 트래픽을 제공 합니다.
    
- 인터넷 연결
    
    각 office는 프록시 서버를 통해 자체 인터넷에 연결 합니다. 이 속성은 일반적으로 WAN으로 구현 됩니다도 프록시 서버에 대 한 공용 IP 주소를 제공 하는 로컬 ISP에 연결 합니다.
    
- 인터넷 소개
    
    Contoso는 contoso.com 공용 도메인 이름을 소유합니다. 제품 주문에 대 한 공용 Contoso 웹사이트는 파리 캠퍼스에서 인터넷에 연결 된 데이터 센터의 서버 집합입니다. Contoso는 /24를 사용 하 여 인터넷에서 공용 IP 주소 범위입니다.
    
## <a name="contosos-app-infrastructure"></a>Contoso의 앱 인프라

Contoso는 다음 해당 응용 프로그램 및 서버 인프라를 설계 했습니다.
  
**내부 응용 프로그램에 대 한 그림 2: Contoso의 인프라**

![내부 응용 프로그램에 대한 Contoso의 인프라](images/Contoso_Poster/App_Infra.png)
  
- 내부 웹 사이트 및 자주 액세스 하는 문서를 저장할 로컬 캐싱 서버를 사용 하는 위성 사무실 합니다.
    
- 지역 허브는 국가 대 한 국가별 응용 프로그램 서버 및 위성 사무실을 사용 합니다. 이러한 서버 파리 본사의 서버와 동기화합니다.
    
- 파리 캠퍼스 전체 조직 역할을 하는 중앙 집중화 된 응용 프로그램 서버를 포함 하는 데이터 센터를 있습니다.
    
또는 사용자에 대해 위성 지역 허브 사무실, 위성 및 지역 허브 office 서버에서 직원에 필요한 리소스의 60%를 제공할 수 있습니다. WAN을 통한 요청 다음에 야 하는 리소스의 추가 40% 파리 캠퍼스에 연결 합니다.
  
## <a name="contosos-network-analysis"></a>Contoso의 네트워크 분석

Microsoft의 클라우드 서비스의 다양 한 범주를 수용 하기 위해 해당 네트워크에 필요한 변경의 Contoso의 분석의 결과 다음과 같습니다.
  
|**SaaS 클라우드 제품: Office 365, EMS, 및 Dynamics 365**|**Azure PaaS: 모바일 응용 프로그램**|**Azure IaaS: 서버 기반 작업**|
|:-----|:-----|:-----|
|사용자가 SaaS 서비스의 성공적인 채택 했는지에 따라 항상 사용 가능 하 고 성능이 연결에서 인터넷 또는 Microsoft 클라우드 서비스에 직접 합니다.  <br/> 모바일 사용자에 대 한 현재의 인터넷 액세스는 적절 한 것으로 간주 됩니다.  <br/> Contoso 인트라넷에서 사용자를 위해에 각 office는 분석 하 고 인터넷에 대 한 처리량 및 Office 365, EMS, 및 Dynamics 365 테 넌 트를 호스팅하는 Microsoft의 유럽 데이터 센터에 대 한 왕복 시간에 최적화 된 수 해야 합니다.  <br/> |더 나은 지원 모바일 근로자, 레거시 응용 프로그램 및 사이트를 공유 하는 일부 파일을 수정 하 고 Azure PaaS 앱으로 배포 되는 합니다. 최적의 성능을 위해 Contoso는 전세계 여러 Azure 데이터 센터에서 새 응용 프로그램을 배포 하도록 계획 합니다. Azure 트래픽 관리자에서 발생 한 것 모바일 사용자 또는 컴퓨터에는 office 응용 프로그램을 호스팅하는 가장 가까운 Azure 데이터 센터에 있는지 여부를 클라이언트 응용 프로그램 요청을 보낼 수 있습니다.  <br/>  IT 부서에서 자신의 네트워크 상태 모니터링 솔루션에 PaaS 응용 프로그램의 성능 및 트래픽 분포를 추가 해야 합니다. <br/> |파리 캠퍼스 데이터 센터에서 일부 레거시 및 보관 서버를 이동 하 고 분기 최종 처리를 위해 필요에 따라 서버를 추가 하려면 Contoso Azure 인프라 서비스에서 실행 중인 가상 컴퓨터를 사용 하 여 계획입니다.  <br/> 이러한 서버를 포함 하는 Azure 가상 네트워크 겹치지 않는 주소 공간, 라우팅, 및 통합 된 DNS에 대 한 설계 해야 합니다.  <br/> IT 부서에서 자신의 네트워크 관리 및 모니터링 시스템에 이러한 새 서버를 포함 해야 합니다.  <br/> |
   
## <a name="contosos-use-of-expressroute"></a>Contoso의 ExpressRoute 사용

ExpressRoute에는 Microsoft 클라우드 네트워크에 네트워크에 연결 하는 Microsoft 피어 링 위치를 현재 위치에서 전용된 WAN 연결입니다. ExpressRoute 연결 예측 가능한 성능 및 99.9% 가동 시간 SLA 제공 합니다. .
  
ExpressRoute 연결을 사용할 경우 Microsoft 클라우드 네트워크와 동일한 대륙의 모든 Microsoft 데이터 센터 위치에 연결 되어 있습니다. 클라우드 피어 링 위치와 대상 Microsoft 데이터 센터 간의 트래픽은 Microsoft 클라우드 네트워크를 통해 수행 되는
  
**그림 3: Microsoft 클라우드 네트워크 전세계**

![Microsoft 클라우드 네트워크 월드와이드](images/Contoso_Poster/MS_WW_Cloud.png)
  
그림 3은 전세계의 다양 한 지역에 대 한 상호 연결 된 Microsoft 클라우드 네트워크를 보여줍니다.
  
ExpressRoute 프리미엄와 모든 대륙에 어떤 Microsoft 피어 링 위치에서 모든 대륙에 모든 Microsoft 데이터 센터에 도달할 수 있습니다. 대륙 간의 트래픽은 Microsoft 클라우드 네트워크를 통해 수행 됩니다.
  
Microsoft의 클라우드 서비스에 현재 및 미래의 트래픽을 분석에 따르면 Contoso가 네트워크 평가 수행 하 고 구현 하는 개인 및 공용 피어 링와 Azure 리소스에 대 한 액세스에 대 한 모든-를-모든 ExpressRoute (MPLS 기반) 연결 유럽의 Microsoft 피어 링 위치로 파리 본사의 관계입니다.
  
이 연결에서 Contoso의를 제공 하는 IT 부서:
  
- 배포 된 Azure PaaS 응용 프로그램의 관리에 대 한 일관 된 성능
    
    모든 관리자는 Contoso의 응용 프로그램 개발자와 IT 핵심 인프라의 파리 캠퍼스에 있습니다. Azure PaaS apps 전세계 다른 Azure 데이터 센터에 배포 된, Contoso는 응용 프로그램 및 문서 t B로 구성 된 해당 저장소 리소스를 관리 하기 파리 캠퍼스에서 일관성 있는 성능이 필요 합니다.
    
- Azure IaaS 서버 관리에 대 한 일관 된 성능
    
    Contoso의 데이터 센터 관리자 파리 캠퍼스에 있고 Azure에 배포 하는 서버는 파리 데이터 센터의 확장 합니다. Contoso 레거시 앱 및 보관 저장소에 대 한 액세스 및 분기의 최종 처리를 위해 이러한 새 서버에 일관성 있는 성능이 필요합니다.
    
## <a name="contosos-path-to-cloud-networking-readiness"></a>클라우드 네트워킹 준비에 대 한 Contoso의 경로

Contoso는 Microsoft 클라우드 하기 위해 네트워크를 준비 하려면 다음 단계를 사용 합니다.
  
1. 인터넷 액세스에 대 한 직원 컴퓨터를 최적화 합니다.
    
    최신 TCP/IP 스택을, 브라우저, NIC 드라이버 및 보안 및 운영 체제 업데이트를 설치 되었는지 확인 하려면 개별 컴퓨터를 확인 합니다.
    
2. 각 office에서 인터넷 연결 사용률을 분석 하 고 필요에 따라 증가
    
    현재 인터넷 사용에 대 한 각 office는 분석할 및 70% 이상 사용률을 작동 하는 경우 WAN 링크의 대역폭을 늘려야 합니다.
    
3. 최적의 성능을 위해 각 office에서 DMZ 시스템 분석
    
    최적의 성능을 위해 방화벽, IDSs, 및 기타 시스템의 인터넷 경로 분석 합니다. 프록시 서버를 업데이트 하거나 필요에 따라 업그레이드 됩니다.
    
4. ExpressRoute 파리 캠퍼스에 대 한 추가
    
    Azure PaaS 및 IaaS 작업 부하의 관리를 위한 Azure 리소스에 대 한 일관 된 액세스를 제공합니다.
    
5. Azure PaaS 앱에 대 한 Azure 트래픽 관리자 프로필을 테스트 하 고 만들기
    
    지역 위치에 대 한 인터넷 트래픽 배포 경험해볼 수 성능 라우팅 메서드를 사용 하 여 Azure 트래픽 관리자 프로필을 테스트 합니다.
    
6. Azure VNets에 대 한 개인 주소 공간을 예약 합니다.
    
    Azure IaaS 예상된 장단기 서버 수가에 based, Azure VNets 및 해당 서브넷에 대 한 개인 주소 공간을 예약해 둡니다.
    
## <a name="see-also"></a>참고 항목

[Microsoft 클라우드의 Contoso](contoso-in-the-microsoft-cloud.md)
  
[Microsoft 클라우드 IT 아키텍처 리소스](microsoft-cloud-it-architecture-resources.md)

[Microsoft의 엔터프라이즈 클라우드 로드맵: IT 의사 결정권자를 위한 리소스](https://sway.com/FJ2xsyWtkJc2taRD)



