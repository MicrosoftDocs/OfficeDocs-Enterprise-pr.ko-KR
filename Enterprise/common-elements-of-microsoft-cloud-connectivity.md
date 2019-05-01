---
title: Microsoft 클라우드 연결의 공통 요소
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
ms.assetid: 061d4507-7360-4029-8f4b-3d4bc6b4ade0
description: '요약: 네트워킹 인프라의 공통 요소와 네트워크를 준비 하는 방법에 대해 설명 합니다.'
ms.openlocfilehash: e00ad8820ef37c818c270323cf2aa036bb86a804
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/30/2019
ms.locfileid: "33490202"
---
# <a name="common-elements-of-microsoft-cloud-connectivity"></a>Microsoft 클라우드 연결의 공통 요소

 **요약:** 네트워킹 인프라의 공통 요소와 네트워크를 준비 하는 방법을 이해 합니다.
  
네트워킹을 Microsoft 클라우드와 통합하면 보다 폭넓은 서비스에 최적 상태로 액세스할 수 있습니다.
  
## <a name="steps-to-prepare-your-network-for-microsoft-cloud-services"></a>Microsoft 클라우드 서비스용 네트워크를 준비 하는 단계
<a name="steps"> </a>

온-프레미스 네트워크에 대해 다음을 수행 합니다.
  
1. 클라이언트 컴퓨터를 분석 하 고 네트워크 하드웨어, 소프트웨어 드라이버, 프로토콜 설정 및 인터넷 브라우저에 맞게 최적화 합니다.
    
2. 인터넷에 지 장치에 대 한 트래픽 대기 시간 및 최적의 라우팅을 위해 온-프레미스 네트워크를 분석 합니다.
    
3. 인터넷에 지 장치의 용량 및 성능을 분석 하 고 더 높은 트래픽 수준에 맞게 최적화 합니다.
    
인터넷 연결의 경우:
  
1. 외부 방화벽과 같은 인터넷에 지 장치 및 연결할 Microsoft 클라우드 서비스의 지역별 위치 간의 대기 시간을 분석 합니다.
    
2. 현재 인터넷 연결의 용량 및 사용률을 분석 하 고 필요한 경우 용량을 추가 합니다. 또는, express 경로 연결을 추가 합니다.
    
## <a name="microsoft-cloud-connectivity-options"></a>Microsoft 클라우드 연결 옵션
<a name="steps"> </a>

기존 인터넷 파이프 또는 Office 365, Azure 및 Dynamics 365에 대 한 express 연결을 사용 합니다.
  
**그림 1: Microsoft 클라우드 연결에 대 한 옵션**

![그림 1: Microsoft 클라우드 연결에 대 한 옵션](media/Network-Poster/CommonElements.png)

  
그림 1에서는 기존 인터넷 파이프 또는 비트 경로를 사용 하 여 온-프레미스 네트워크를 Microsoft 클라우드 제품에 연결 하는 방법을 보여 줍니다. 인터넷 파이프는 DMZ를 나타내며 다음과 같은 구성 요소를 포함할 수 있습니다.
  
- **내부 방화벽:** 신뢰할 수 있는 네트워크와 트러스트 되지 않은 네트워크가 서로 다른 장벽입니다. 규칙에 따라 트래픽 필터링 및 모니터링을 수행 합니다.
    
- **외부 작업:** 인터넷에서 외부 사용자가 사용할 수 있는 웹 사이트 또는 기타 작업
    
- **프록시 서버:** 서비스 인트라넷 사용자를 대신 하 여 웹 콘텐츠를 요청 합니다. 역방향 프록시는 원치 않는 인바운드 요청을 허용 합니다.
    
- **외부 방화벽:** 아웃 바운드 트래픽 및 지정 된 인바운드 트래픽을 허용 합니다. 주소 변환, 패킷 검사, SSL 중단 및 검사, 데이터 손실 방지 등을 수행할 수 있습니다.
    
- **ISP에 대 한 WAN 연결:** 인터넷을 통해 연결 하 고 라우팅할 때 ISP에 대 한 반송파 기반 연결
    
## <a name="areas-of-networking-common-to-all-microsoft-cloud-services"></a>모든 Microsoft 클라우드 서비스에 공통 되는 네트워킹 영역
<a name="steps"> </a>

Microsoft의 클라우드 서비스를 채택할 때 이러한 네트워킹 영역을 고려해 야 합니다.
  
- **인트라넷 성능:** 클라이언트 컴퓨터를 포함 하는 인트라넷이 최적화 되지 않으면 인터넷 기반 리소스에 대 한 성능이 저하 될 수 있습니다.
    
- 에 **지 장치:** 네트워크의 가장자리에 있는 장치는 egress 지점으로, nat (network Address 번역가), 프록시 서버 (역방향 프록시 포함), 방화벽, 침입 감지 장치 또는 조합 등을 포함할 수 있습니다.
    
- **인터넷 연결:** ISP와 인터넷에 대 한 WAN 연결에서는 최대 부하를 처리할 수 있는 충분 한 용량을 가져야 합니다. 또한 express 경로 연결을 사용할 수 있습니다.
    
- **인터넷 DNS:** Microsoft 클라우드 또는 클라우드에서 호스트 되는 서비스를 찾기 위한 A, AAAA, CNAME, MX, PTR 및 기타 레코드입니다. 예를 들어 Azure PaaS에 호스트 되는 앱에 대 한 CNAME 레코드가 필요할 수 있습니다.
    

## <a name="next-step"></a>다음 단계

[Microsoft 클라우드 연결에 대한 ExpressRoute](expressroute-for-microsoft-cloud-connectivity.md)

## <a name="see-also"></a>참고 항목

<a name="steps"> </a>

[Microsoft Cloud Networking for Enterprise Architects](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Microsoft 클라우드 IT 아키텍처 리소스](microsoft-cloud-it-architecture-resources.md)


