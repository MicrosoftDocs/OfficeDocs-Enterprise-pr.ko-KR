---
title: Microsoft SaaS에 대한 네트워킹 디자인
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/28/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 4194020a-3847-4259-9f2d-5c556a4510f9
description: '요약: Office 365, Microsoft Intune 및 Dynamics 365를 포함 하 여 Microsoft의 SaaS 서비스에 액세스할 수 있도록 네트워크를 최적화 하는 방법을 알아봅니다.'
ms.openlocfilehash: 695e3255bf1afcb5314985caccb15ead410d93f6
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067774"
---
# <a name="designing-networking-for-microsoft-saas"></a>Microsoft SaaS에 대한 네트워킹 디자인

 **요약:** Office 365, Microsoft Intune 및 Dynamics 365를 포함 하 여 Microsoft의 SaaS 서비스에 액세스 하기 위해 네트워크를 최적화 하는 방법을 이해 합니다.
  
Microsoft SaaS 서비스를 위해 네트워크를 최적화하려면 Microsoft SaaS 서비스로 다양한 범주의 트래픽을 라우팅하기 위해 내부 장치와 에지 장치를 구성해야 합니다.
  
## <a name="steps-to-prepare-your-network-for-microsoft-saas-services"></a>Microsoft SaaS 서비스용 네트워크를 준비 하는 단계

다음 단계에 따라 Microsoft SaaS 서비스에 대 한 네트워크를 최적화 합니다.
  
1. [Microsoft 클라우드 연결의 공통 요소](common-elements-of-microsoft-cloud-connectivity.md)에 있는 **microsoft 클라우드 서비스용 네트워크 섹션을 준비 하는 단계** 를 진행 합니다.
    
2. 각 사무실에 인터넷 연결을 추가 합니다.
    
3. 모든 인터넷 연결에 대 한 Isp에서 로컬 IP 주소가 있는 DNS 서버를 사용 하는지 확인 합니다.
    
4. 네트워크 헤어핀 방지 클라우드 기반 보안 서비스와 같은 중간 대상을 검사 하 고 가능한 경우 제거 합니다.
    
5. Microsoft SaaS 트래픽의 최적화 및 허용 범주에 대 한 처리를 우회 하도록에 지 장치를 구성 합니다.

## <a name="optimizing-traffic-to-microsofts-saas-services"></a>Microsoft의 SaaS 서비스에 대 한 트래픽 최적화    

Microsoft SaaS 트래픽의 범주에는 다음 세 가지가 있습니다.

- 최적화

  모든 Microsoft SaaS 서비스에 연결 하 고 Microsoft SaaS 대역폭, 연결 및 데이터 양을 75% 이상으로 표시 하는 데 필요 합니다.

- 허용

  특정 Microsoft SaaS 서비스 및 기능에 연결 하는 데 필요 하지만, 최적화 범주에 있는 것 처럼 네트워크 성능 및 대기 시간을 구분 하지 않습니다.

- 기본

  최적화가 필요 하지 않은 Microsoft SaaS 서비스 및 종속성을 나타냅니다. 기본 범주 트래픽을 일반적인 인터넷 트래픽과 같이 취급할 수 있습니다.


**그림 1: 모든 사무실에 대 한 Microsoft SaaS 트래픽에 권장 되는 구성**

![그림 1: 모든 사무실에 대 한 Microsoft SaaS 트래픽에 권장 되는 구성](media/Network-Poster/SaaS1.png)

그림 1에는 다음과 같은 지사, 지역 또는 중앙 it를 비롯 한 모든 사무실의 권장 구성이 나와 있습니다.

- **기본** 범주 및 일반 인터넷 트래픽은 인터넷 기반 보안 위험 으로부터 보호를 제공 하기 위해 프록시 서버 및 기타에 지 장치를 포함 하는 사무실로 라우팅됩니다.
- **최적화** 및 **허용** 범주 트래픽은 프록시 서버 및 기타에 지 장치를 바이패스 하 여 연결 하는 사용자를 포함 하는 Office에 가장 가까운 Microsoft 네트워크 프런트 엔드의 모서리로 바로 전달 됩니다.

지사의 SD (wide area network) 장치에는 다음과 같은 개별 트래픽이 사용 되도록 별도의 트래픽을 사용 합니다. 

- **기본** 범주 및 일반 인터넷 트래픽은 WAN 백본으로 중앙 또는 지역별 사무실로 이동 합니다. 
- **최적화** 및 **허용** 범주 트래픽은 로컬 인터넷 연결을 제공 하는 ISP로 이동 합니다.
  
자세한 내용은 다음을 참조하세요.
  
- [네트워크 연결 원칙](https://aka.ms/expressrouteoffice365)

- [Office 365의 네트워크 및 마이그레이션 계획](https://aka.ms/tune)
    
## <a name="next-step"></a>다음 단계

[Microsoft Azure PaaS에 대한 네트워킹 디자인](designing-networking-for-microsoft-azure-paas.md)
    
## <a name="see-also"></a>참고 항목

[Microsoft Cloud Networking for Enterprise Architects](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Microsoft 클라우드 IT 아키텍처 리소스](microsoft-cloud-it-architecture-resources.md)

