---
title: "Microsoft Azure PaaS에 대 한 네트워킹 디자인 (영문)"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 19568184-705b-493b-b713-b484367adba9
description: "요약: Microsoft Azure PaaS에 대 한 액세스에 대 한 네트워크를 최적화 하는 방법을 이해 합니다."
ms.openlocfilehash: d63a7a20d4648b0044a24ea86ad4e9125779a027
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2017
---
# <a name="designing-networking-for-microsoft-azure-paas"></a>Microsoft Azure PaaS에 대 한 네트워킹 디자인 (영문)

 **요약:** Microsoft Azure PaaS에 대 한 액세스에 대 한 네트워크를 최적화 하는 방법을 이해 합니다.
  
Azure PaaS 앱용 네트워킹을 최적화하려면 적절한 인터넷 대역폭이 필요하고 여러 사이트 또는 앱 간에 네트워크 트래픽을 분산해야 합니다.
  
## <a name="planning-steps-for-hosting-organization-paas-applications-in-azure"></a>Azure의 조직 PaaS 응용 프로그램 호스팅에 대 한 계획 단계

여기에 섹션 본문을 삽입합니다.
  
1. [Microsoft 클라우드 연결의 공통 요소](common-elements-of-microsoft-cloud-connectivity.md)에 **Microsoft 클라우드 서비스에 대 한 네트워크를 준비 하는 단계** 섹션을 통해 이동 합니다.
    
2. [Microsoft SaaS에 대 한 네트워킹 디자인 (영문)](designing-networking-for-microsoft-saas.md)에서 **Microsoft SaaS 서비스에 대 한 네트워크를 준비 하는 단계** 섹션의 2-4 단계를 사용 하 여 인터넷 대역폭을 최적화 합니다.
    
3. Azure에 대 한 ExpressRoute 연결의 필요 여부를 결정 합니다.
    
4. 웹 기반 작업에 대 한 Azure 응용 프로그램 게이트웨이 필요 여부를 결정 합니다.
    
5. 서로 다른 데이터 센터의 다른 끝점에 대 한 트래픽 배포용 Azure 트래픽 관리자의 필요 여부를 결정 합니다.
    
## <a name="internet-bandwidth-for-organization-paas-applications"></a>조직 PaaS 응용 프로그램에 대 한 인터넷 대역폭

Azure PaaS에서 호스팅되는 조직 응용 프로그램의 경우 인트라넷 사용자에 대 한 인터넷 대역폭을 필요 합니다. 두 옵션이 있습니다.
  
- **옵션 1:** 최대 부하를 처리 하기 용량을 사용 하 여 인터넷 트래픽을 위해 최적화 하 여 기존 파이프를 사용 합니다. 인터넷에 지, 클라이언트 사용 현황 및 IT 운영 고려 사항에 대 한[Microsoft SaaS에 대 한 네트워킹 디자인 (영문)을](designing-networking-for-microsoft-saas.md) 참조 하십시오.
    
- **옵션 2:** 고대역폭 또는 낮은 대기 시간 요구 Azure에 ExpressRoute 연결을 사용 합니다.
    
**Azure PaaS 서비스를 연결 하기 위한 그림 1: 연결 옵션**

![그림 1: Azure PaaS 서비스에 대한 연결 옵션](images/Network_Poster/PaaS1.png)
  
그림 1 인터넷 파이프 또는 ExpressRoute을 통해 Azure PaaS 서비스에 연결 하는 온-프레미스 네트워크를 보여줍니다.
  
## <a name="azure-application-gateway"></a>Azure 응용 프로그램 게이트웨이

응용 프로그램 수준에서 라우팅 및 부하 분산 서비스 수 있도록 하는 확장 가능 하 고 항상 사용 가능 웹 프런트엔드 Azure에서 웹 앱, 클라우드 서비스와 가상 컴퓨터에 대 한 작성 합니다. 
  
**그림 2: Azure 응용 프로그램 게이트웨이**

![그림 2: Azure 응용 프로그램 Gateway 서비스](images/Network_Poster/PaaS2.png)
  
그림 2에서는 Azure 응용 프로그램 게이트웨이 및 인터넷에서 사용자 요청 하는 방식 Azure 웹 앱, 클라우드 서비스 또는 가상 컴퓨터를 라우팅할 수 있습니다.
  
현재 응용 프로그램 게이트웨이 다음에 대 한 계층 7 응용 프로그램 배달을 지원합니다.
  
- HTTP 부하 분산
    
- 세션 쿠키 기반 선호도
    
- SSL 오프 로드
    
자세한 내용은 [응용 프로그램 게이트웨이](https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction)참조 하십시오.
  
## <a name="azure-traffic-manager"></a>Azure 트래픽 관리자

클라우드 서비스 또는 다른 데이터 센터 또는 끝점을 외부에 있는 Azure 웹 응용 프로그램을 포함할 수 있는 다른 끝점에 대 한 트래픽의 배포 합니다.
  
트래픽 관리자는 다음과 같은 라우팅 방법을 사용합니다.
  
- **장애 조치:** 끝점을 동일한 컴퓨터나 다른 Azure 데이터 센터에 있으며 모든 트래픽에 대 한 기본 끝점을 사용 하지만 기본 또는 백업 끝점을 사용할 수 없는 경우 백업을 제공 하려는 합니다.
    
- **라운드 로빈:** 동일한 데이터 센터에는 끝점의 집합을 통해 또는 다른 데이터 센터 간에 부하를 분산 하려는 경우
    
- **성능:** 끝점을 다른 지리적 위치에 있고 가장 낮은 대기 시간 측면에서 "가장 가까운" 끝점을 사용 하 여 요청 클라이언트를 원하는 합니다.
    
세 지리적으로 분산 된 웹 응용 프로그램에 대 한 예는 다음과 같습니다.
  
**그림 3: Azure 트래픽 관리자**

![그림 3: Azure 트래픽 관리자](images/Network_Poster/PaaS3.png)
  
그림 3은 트래픽 관리자 미국, 유럽 및 아시아에서는 세가지 다른 Azure 웹 응용 프로그램에 대 한 경로 요청을 사용 하 여 기본 프로세스를 보여줍니다. 예제:
  
1. URL을 Azure 트래픽 관리자, 지역 웹 응용 프로그램의 이름을 반환 하는 요청을 가져옵니다 웹사이트에 대 한 사용자 DNS 쿼리 성능 라우팅 방법을 기반으로 합니다.
    
2. 유럽에서 지역 웹 응용 프로그램을 사용 하 여 트래픽을 시작 하는 사용자입니다.
    
자세한 내용은 [트래픽 관리자](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview)를 참조 하십시오.
  
## <a name="see-also"></a>See Also

[Microsoft 클라우드 엔터프라이즈 설계자에 대 한 네트워킹](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Microsoft 클라우드 IT 아키텍처 리소스](microsoft-cloud-it-architecture-resources.md)

[Microsoft의 엔터프라이즈 클라우드 로드맵: IT 의사 결정권자를 위한 리소스](https://sway.com/FJ2xsyWtkJc2taRD)



