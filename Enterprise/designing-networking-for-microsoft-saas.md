---
title: Microsoft SaaS에 대한 네트워킹 디자인
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
ms.assetid: 4194020a-3847-4259-9f2d-5c556a4510f9
description: '요약: Office 365, Microsoft Intune 및 Dynamics 365 포함 한 Microsoft의 SaaS 서비스에 대 한 액세스에 대 한 네트워크를 최적화 하는 방법을 이해 합니다.'
ms.openlocfilehash: 3d47c53de1bc1121ef72eb519c51c0ad9423fff9
ms.sourcegitcommit: 25a022f4ef4e56c5407e8e3a8a34265f8fc94264
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/29/2018
ms.locfileid: "26872269"
---
# <a name="designing-networking-for-microsoft-saas"></a>Microsoft SaaS에 대한 네트워킹 디자인

 **요약:** Office 365, Microsoft Intune 및 Dynamics 365 포함 한 Microsoft의 SaaS 서비스에 대 한 액세스에 대 한 네트워크를 최적화 하는 방법을 이해 합니다.
  
Microsoft SaaS 서비스에 대 한 네트워크 최적화의 내부 구성 데이터베이스 및 Microsoft SaaS 서비스 트래픽의 다양 한 범주 회람 하는 지 장치 필요 합니다.
  
## <a name="steps-to-prepare-your-network-for-microsoft-saas-services"></a>Microsoft SaaS 서비스에 대 한 네트워크를 준비 하는 단계

Microsoft SaaS 서비스에 대 한 네트워크를 최적화 하기 위해 다음이 단계를 수행 합니다.
  
1. [Microsoft 클라우드 연결의 공통 요소](common-elements-of-microsoft-cloud-connectivity.md)에 **Microsoft 클라우드 서비스에 대 한 네트워크를 준비 하는 단계** 섹션을 통해 이동 합니다.
    
2. 사무실 각각에 대 한 인터넷 연결을 추가 합니다.
    
3. 모든 인터넷 연결에 대 한 Isp를 사용 하는 DNS 서버를 로컬 IP 주소를 확인 합니다.
    
4. 네트워크 hairpins, 보안 클라우드 기반 서비스와 같은 중간 대상을 검사 하 고 가능한 경우 제거 합니다.
    
5. 최적화에 대 한 처리를 무시 하 고 Microsoft SaaS 트래픽의 범주를 허용 하 여에 지 장치를 구성 합니다.

## <a name="optimizing-traffic-to-microsofts-saas-services"></a>Microsoft의 SaaS 서비스에 대 한 트래픽 최적화    

Microsoft SaaS 트래픽의 편리할 수 있습니다.

- 최적화

  모든 Microsoft SaaS 서비스 및 Microsoft SaaS 대역폭, 연결 및 데이터 볼륨의 나타내는 75% 이상에 대 한 연결에 필요합니다.

- 허용

  특정에 대 한 연결에 필요한 Microsoft SaaS 서비스 및 기능 설명 비디오 되지 않은 네트워크 성능 및 최적화 범주에 나타난 대기 시간에 민감한 같이 합니다.

- 기본

  Microsoft SaaS 서비스 및 모든 최적화 필요 하지 않은 의존 관계를 나타냅니다. 일반 인터넷 트래픽와 같은 기본 범주 트래픽을 처리할 수 있습니다.


**그림 1: 권장 하는 모든 사무실에 대 한 Microsoft SaaS 트래픽에 대 한 구성**

![그림 1: 권장 하는 모든 사무실에 대 한 Microsoft SaaS 트래픽에 대 한 구성](media/Network-Poster/SaaS1.png)

그림 1 지사 하 고 있는 지역 또는 중앙 위치를 포함 하 여 모든 사무실을의 권장된 구성을 보여줍니다.

- **기본** 범주 및 일반 인터넷 트래픽을 프록시 서버와 다른 지 장치를 인터넷 기반 보안 위험 으로부터 보호 기능을 제공 하는 사무실으로 라우팅됩니다.
- **최적화** 하 고 **허용** 범주 트래픽은 Microsoft 네트워크 프런트엔드 연결 하는 사용자, 프록시 서버와 다른 지 장치 우회 하 여 포함 된 office와 가장 가까운 가장자리에 직접 전달 됩니다.

지사에서 소프트웨어 정의 광역 네트워크 (SD WAN) 장치 트래픽을 분리 되도록 합니다. 

- **기본** 범주 및 일반 인터넷 트래픽은 중앙 또는 지역 영업소 WAN 백본으로 합니다. 
- **최적화** 하 고 **허용** 범주 트래픽은 로컬 인터넷 연결을 제공 하는 ISP에 합니다.
  
자세한 내용은 다음을 참조하세요.
  
- [네트워크 연결 원칙](https://aka.ms/expressrouteoffice365)

- [Office 365의 네트워크 및 마이그레이션 계획](https://aka.ms/tune)
    
## <a name="next-step"></a>다음 단계

[Microsoft Azure PaaS에 대한 네트워킹 디자인](designing-networking-for-microsoft-azure-paas.md)
    
## <a name="see-also"></a>참고 항목

[Microsoft Cloud Networking for Enterprise Architects](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Microsoft 클라우드 IT 아키텍처 리소스](microsoft-cloud-it-architecture-resources.md)

