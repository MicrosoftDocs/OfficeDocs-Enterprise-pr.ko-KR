---
title: "구독, 라이선스 및 Contoso Corporation에 대 한 사용자 계정"
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
ms.assetid: ec3b08f0-288c-4ba3-b822-dbf6352fa761
description: "요약: Contoso의 클라우드 구독, 라이선스, 사용자 계정 및 테 넌 트의 구조를 이해 합니다."
ms.openlocfilehash: 6e62fbbc0f52019e5d233fc73992b000952344f5
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/09/2018
---
# <a name="subscriptions-licenses-and-user-accounts-for-the-contoso-corporation"></a>구독, 라이선스 및 Contoso Corporation에 대 한 사용자 계정

 **요약:** Contoso의 클라우드 구독, 라이선스, 사용자 계정 및 테 넌 트의 구조를 이해 합니다.
  
모든 클라우드 서비스에 대 한 id 및 대금 청구의 일관 된 사용을 제공 하려면 Microsoft는 조직/구독/라이선스/사용자 계정을 계층 구조를 제공 합니다.
  
- 조직
    
    Contoso.com와 같은 공용 DNS 도메인 이름에 따라 일반적으로 식별 되는 Microsoft 클라우드 서비스를 사용 하는 비즈니스 엔터티.
    
- 구독
    
    Microsoft SaaS 클라우드 제품 (Office 365, Intune/EMS 및 Dynamics 365), 구독 되는 특정 제품 및 사용자 라이선스를 구입한 집합입니다. Azure, 구독을 조직에 소비 된 클라우드 서비스의 대금 청구를 허용합니다.
    
- 라이선스
    
    Microsoft SaaS 클라우드 서비스에 대 한 라이선스에는 클라우드 서비스를 사용 하 여 특정 사용자 계정을 수 있습니다. Azure, 소프트웨어 라이선스 서비스 가격으로 하지만 추가 소프트웨어 라이선스를 구입 해야하는 경우에 따라 기본 제공 됩니다.
    
- 사용자 계정
    
    사용자 계정을 Azure AD 테 넌 트에 저장 되 고 Windows Server AD와 같은 온-프레미스 id 공급자에서 동기화 할 수 있습니다.
    
## <a name="contosos-structure"></a>Contoso의 구조

Contoso는 조직 및 해당 구독, 라이선스, 계정 및 테 넌 트에 대 한 다음과 같은 구조를 결정 합니다.
  
**그림 1: Contoso의 조직, 구독, 라이선스, 사용자 계정 및 테 넌 트**

![Contoso의 조직, 구독, 라이선스, 사용자 계정 및 테넌트](images/Contoso_Poster/Subscriptions.png)
  
그림 1에는 Contoso 조직 여러 구독을 포함 하 고 Windows Server AD 포리스트 contoso.com에서 동기화 하는 사용자 계정이 포함 된 일반적인 Azure AD 테 넌에 연결 하는 방법을 보여줍니다.
  
- **조직** Contoso Corporation contoso.com 해당 공용 도메인 이름으로 식별 됩니다.
    
  - **구독 및 라이선스** Contoso Corporation 다음 사용 합니다.
    
  - 5, 000 라이선스와 Office 365 Enterprise E3 제품
    
  - 200 라이선스와 Office 365 Enterprise E5 제품
    
  - 5, 000 라이선스 EMS 제품
    
  - 100 라이선스 Dynamics 365 제품
    
  - 지역에 따라 여러 Azure 구독
    
  - **사용자 계정** 일반적인 Azure AD 테 넌 트 사용자 계정 목록을 포함 하 고 Azure 구독 개발/테스트를 제외 하 고 Contoso의 구독의 모든 그룹 사용 합니다.
    
Contoso의 테 넌:
  
- SaaS 클라우드 서비스에 대 한 테 넌 트 클라우드 서비스를 제공 하는 서버를 보관 하는 지역 위치입니다. Contoso의 Office 365, EMS, 및 Dynamics 365 테 넌 트를 호스팅할 유럽 지역 선택 했습니다. 
    
- Azure PaaS 서비스 및 응용 프로그램 및 IaaS IT 작업 전세계 모든 Azure 데이터 센터의 테 넌 시를 가질 수 있습니다. Azure AD 테 넌 트는 계정 및 그룹을 포함 하는 Azure AD의 특정 인스턴스.
    
- 일반적인 Azure AD 테 넌 트 Contoso Windows Server AD 포리스트에 대 한 동기화 된 계정이 포함 된 Microsoft의 클라우드 서비스 간에 IDaaS를 제공 합니다.
    
자세한 내용은 [구독, 라이선스, 계정 및 Microsoft의 클라우드 서비스에 대 한 테 넌 트를](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md)참조 하십시오.
  
## <a name="contosos-azure-subscriptions"></a>Contoso의 Azure 구독

그림 2에서는 Contoso의 Azure 구독의 계층 구조 디자인을 보여줍니다.
  
**Azure 구독에 대 한 그림 2: Contoso의 구조**

![Azure Subscription에 대한 Contoso의 구조](images/Contoso_Poster/Subscriptions_Nested.png)
  
- Contoso의 위쪽에는 Microsoft와 해당 기업 계약에 따라 합니다.
    
- Contoso의 Windows Server AD 포리스트의 도메인에 따라 전세계 Contoso Corporation의 서로 다른 영역에 해당 계정 집합이 있습니다.
    
- 각 지역 내에서 지역의 개발, 테스트 및 프로덕션 배포 요구 사항에 따라 하나 이상의 구독 있습니다.
    
각 Azure 구독 단일 연관 될 수 인증 및 권한 부여 Azure 서비스를 위한 사용자 계정 및 그룹을 포함 하는 Azure AD 테 넌 트입니다. 프로덕션 구독 일반적인 Contoso Azure AD 테 넌 트를 사용합니다.
  
## <a name="see-also"></a>참고 항목

[Microsoft 클라우드의 Contoso](contoso-in-the-microsoft-cloud.md)
  
[Microsoft 클라우드 IT 아키텍처 리소스](microsoft-cloud-it-architecture-resources.md)

[Microsoft의 엔터프라이즈 클라우드 로드맵: IT 의사 결정권자를 위한 리소스](https://sway.com/FJ2xsyWtkJc2taRD)




