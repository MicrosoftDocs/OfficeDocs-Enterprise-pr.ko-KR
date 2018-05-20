---
title: 하이브리드 클라우드 개요
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
ms.assetid: 3ea3ee10-411e-4690-b9e5-f1b46f1f4d59
description: '요약: 정 및 Microsoft 하이브리드 클라우드의 요소를 이해 합니다.'
ms.openlocfilehash: 6d23f4f759e882ed925bd8bcb4c21ee365b231a0
ms.sourcegitcommit: 8fcf6fd9f0c45a5445654ef811410fca3f4f5512
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2018
---
# <a name="hybrid-cloud-overview"></a>하이브리드 클라우드 개요

 **요약:** 정 및 Microsoft 하이브리드 클라우드의 요소를 이해 합니다.
  
하이브리드 클라우드 클라우드 및 온-프레미스 네트워크에서 compute 또는 저장소 리소스를 사용합니다. 하이브리드 클라우드도 비즈니스 및 IT 필요에 맞게 클라우드로 마이그레이션할 또는 기존와 클라우드 플랫폼 및 서비스를 통합에 대 한 경로 온-프레미스 인프라 전반적인 IT 전략의 일부분으로 사용할 수 있습니다.
  
## <a name="microsoft-hybrid-cloud"></a>Microsoft 하이브리드 클라우드

Microsoft 하이브리드 클라우드에는 온-프레미스 구성 요소와 같은 Microsoft 클라우드 플랫폼을 결합 하는 비즈니스 시나리오의 집합입니다. 
  
- Office 365의 SharePoint Online에서 및 온-프레미스 SharePoint 팜에서 콘텐츠에서 검색 결과를 가져왔습니다.
    
- 온-프레미스 데이터 저장소를 쿼리 하는 Azure에서 실행 되는 모바일 앱입니다.
    
- IT 인트라넷 Azure 가상 컴퓨터에서 실행 되는 작업입니다.
    
**Microsoft 하이브리드 클라우드의 그림 1: 구성 요소**

![Microsoft 하이브리드 클라우드의 구성 요소](images/Hybrid_Poster/MS_Hybrid_Cloud.png)
  
그림 1은 인터넷 이나 ExpressRoute 연결에서 Microsoft 하이브리드 클라우드 서비스로 (PaaS) Azure 플랫폼 및 사용할 수 있는 서비스 (IaaS) 서비스로 Azure 인프라 Office 365의 집합에는 온-프레미스 네트워크에서의 구성 요소를 보여줍니다.
  
Microsoft 시장에서 가장 전체 클라우드 솔루션을 갖기 때문에-소프트웨어를 포함 하 여 서비스 (SaaS), PaaS, 및 IaaS-을 수행할 수 있습니다.
  
- 작업 및 응용 프로그램은 클라우드로 마이그레이션할 때 기존 온-프레미스 투자를 활용 합니다.
    
- 통합할 하이브리드 클라우드 시나리오 장기 IT 계획, 예, 규정 또는 정책 하지 못하도록 하 여 클라우드 작업 또는 특정 데이터를 이동 하는 경우.
    
- 여러 Microsoft 클라우드 서비스 및 플랫폼을 포함 하는 추가 하이브리드 시나리오를 만듭니다.
    
하이브리드 클라우드로 Microsoft 클라우드 서비스에 대 한 시나리오는 플랫폼에 따라 다릅니다.
  
- SaaS
    
    Microsoft SaaS 서비스는 Office 365, Microsoft Intune 및 Microsoft Dynamics 365 포함 됩니다. 온-프레미스 서비스 또는 응용 프로그램을 이러한 서비스를 결합 하는 Microsoft SaaS를 사용한 하이브리드 클라우드 시나리오입니다. 예, Office 365에서 실행 되는 Exchange Online와 통합 될 수는 온-프레미스로 배포 하는 비즈니스 2015 용 Skype 합니다.
    
- Azure PaaS
    
    Microsoft Azure PaaS 서비스를 사용 하면 클라우드 기반 응용 프로그램을 만들 수 있도록 합니다. 온-프레미스 리소스 또는 응용 프로그램을 Azure PaaS app를 결합 하는 Azure PaaS 서비스를 사용한 하이브리드 클라우드 시나리오입니다. 등 Azure PaaS 응용 프로그램을 모바일 응용 프로그램 사용자에 게 표시 하는 데 필요한 정보에 대 한 온-프레미스 데이터 저장소를 쿼리하여 안전 하 게 수 있습니다.
    
- Azure IaaS
    
    Azure IaaS 서비스를 구성 하 고 서버 기반 IT 작업을 실행 하 여 클라우드에서 아니라 온-프레미스 데이터 센터에서 할 수 있습니다. Azure IaaS 서비스를 사용한 하이브리드 클라우드 시나리오 투명 하 게 온-프레미스 네트워크에 연결 되는 IT 작업량 가상 컴퓨터에서 실행 되는 일반적으로 구성 됩니다. 온-프레미스 사용자가 차이 느끼지 못합니다.
    
## <a name="elements-of-hybrid-cloud"></a>하이브리드 클라우드의 요소

클라우드 플랫폼 및 서비스 계획 및 Microsoft와 하이브리드 클라우드 시나리오를 구현 하는 경우에 다음 요소에 대 한 설명 해야 합니다.
  
- 네트워킹
    
    네트워킹 하이브리드 클라우드 시나리오에 대 한 최고 부하에서 성능이 수 있을 만큼 충분 한 대역폭 및 Microsoft 클라우드 플랫폼 및 서비스에 대 한 연결을 포함 합니다. 자세한 내용은 [엔터프라이즈 설계자에 대 한 Microsoft 클라우드 네트워킹](microsoft-cloud-networking-for-enterprise-architects.md)을 참조 하십시오.
    
- Identity
    
    SaaS 및 Azure PaaS 하이브리드 시나리오에 대 한 id는 온-프레미스 Windows Server AD와 동기화 또는 Windows Server AD 또는 다른 id 공급자와 페더레이션 수 있는 일반적인 id 공급자를으로 Azure AD를 포함할 수 있습니다. 또한 Azure IaaS를 사용 하도록 온-프레미스 Identity 인프라를 확장할 수 있습니다. 자세한 내용은 [엔터프라이즈 설계자에 대 한 Microsoft 클라우드 Id](microsoft-cloud-it-architecture-resources.md#identity)를 참조 하십시오.
    
- 보안
    
    하이브리드 클라우드 시나리오에 대 한 보안 보호 및 id, 데이터 보호, 관리 권한 관리, 위협 인식 및 거 버 넌 스 및 보안 정책 구현에 대 한 관리를 포함합니다. 자세한 내용은 [엔터프라이즈 설계자에 대 한 Microsoft 클라우드 보안](https://technet.microsoft.com/library/dn919927.aspx#security)을 참조 하십시오.
    
- 관리
    
    하이브리드 클라우드 시나리오에 대 한 관리 설정, 데이터, 계정, 정책 및 사용 권한 유지 관리 하 고 시나리오 및 성능에 대의 요소는 계속 해 서 상태를 모니터링 하는 기능을 포함 합니다. Azure IaaS에 가상 컴퓨터를 관리 하기 위한 Systems Management Server와 같은 동일한 도구 집합을 사용할 수도 있습니다.
    
## <a name="see-also"></a>참고 항목

[Microsoft Hybrid Cloud for Enterprise Architects](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Microsoft 클라우드 IT 아키텍처 리소스](microsoft-cloud-it-architecture-resources.md)

[Microsoft의 엔터프라이즈 클라우드 로드맵: IT 의사 결정권자를 위한 리소스](https://sway.com/FJ2xsyWtkJc2taRD)
 


