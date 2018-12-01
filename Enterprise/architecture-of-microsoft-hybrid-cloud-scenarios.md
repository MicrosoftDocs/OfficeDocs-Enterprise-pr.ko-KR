---
title: Microsoft 하이브리드 클라우드 시나리오의 아키텍처
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 06d8c959-39e5-4150-b1ae-aaf0eee4c058
description: '요약: Microsoft의 하이브리드 클라우드 서비스의 아키텍처를 이해 합니다.'
ms.openlocfilehash: 74fc046d1f60b29338e7f12184dec018538ba9da
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123395"
---
# <a name="architecture-of-microsoft-hybrid-cloud-scenarios"></a>Microsoft 하이브리드 클라우드 시나리오의 아키텍처

 **요약:** Microsoft의 하이브리드 클라우드 서비스의 아키텍처를 이해 합니다.
  
계획 하 고 Microsoft 클라우드 서비스 및 플랫폼 하이브리드 클라우드 시나리오를 구현 하는 아키텍처 접근 방법을 사용 합니다.
  
**Microsoft 하이브리드 클라우드 스택의 그림 1:**

![Microsoft 하이브리드 클라우드 스택](media/Hybrid-Poster/Hybrid-Cloud-Stack.png)
  
그림 1 온-프레미스, 네트워크, Identity, 앱 및 시나리오 및 클라우드 서비스 (Microsoft SaaS, Azure PaaS 및 Azure PaaS)의 범주를 포함 하는 Microsoft 하이브리드 클라우드 스택 및 해당 레이어를 표시 합니다.
  
앱 및 시나리오 레이어가이 모델의 추가 문서에 자세히 설명 된 특정 하이브리드 클라우드 시나리오에 있습니다. Identity, 네트워크 및 온-프레미스 레이어 클라우드 서비스 (SaaS, PaaS, 또는 PaaS)의 범주에 공통 될 수 있습니다.
  
- 온-프레미스
    
    온-프레미스 인프라 하이브리드 시나리오에 대 한 비즈니스 및 비즈니스 응용 프로그램의 줄에 대 한 개발자를 위한 SharePoint, Exchange, Skype 서버를 포함할 수 있습니다. 데이터 저장소 (데이터베이스, 목록, 파일)를 포함할 수도 있습니다. ExpressRoute 연결 하지 않고 역방향 프록시를 통해 또는 DMZ에 액세스할 수 있는 또는 엑스트라넷 서버 또는 데이터를 요청 하 여 온-프레미스 데이터 저장소에 대 한 액세스를 허용 합니다.
    
- 네트워크
    
    Microsoft 클라우드 플랫폼 및 서비스에 대 한 연결에 대 한 두 선택 사항이: 기존 인터넷 파이프 및 ExpressRoute 합니다. 예측 가능한 성능 문제가 중요 한 경우 ExpressRoute 연결을 사용 합니다. Microsoft SaaS 서비스 (Office 365 및 Dynamics 365), Azure PaaS 서비스 및 Azure IaaS 서비스에 직접 연결을 하나의 ExpressRoute 연결을 사용할 수 있습니다.
    
- ID
    
    클라우드 id 인프라에 대 한 두가지를 Microsoft 클라우드 플랫폼에 따라 이동 하 고 있습니다. SaaS 및 Azure PaaS Azure AD와 온-프레미스 identity 인프라가 통합 또는 사용자 온-프레미스 identity 인프라 또는 타사 id 공급자와 페더레이션. Vm Azure에서 실행을 위한 Windows Server AD, Vm에 있는 가상 네트워크 (VNets)와 같은 사용자 온-프레미스 id 인프라를 확장할 수 있습니다.
    
## <a name="hybrid-cloud-scenarios-for-the-three-phase-cloud-adoption-process"></a>3 단계 클라우드 채택 프로세스에 대 한 하이브리드 클라우드 시나리오

클라우드 이유는 3 단계 방식을 사용 하는 Microsoft를 포함 한 대부분의 기업은 합니다. 하이브리드 클라우드 시나리오는 각 단계에는 역할을 수행할 수 있습니다.
  
1. SaaS 생산성 작업 이동
    
    현재는 또는 온-프레미스 유지 되어야 하는 생산성 작업 부하에 대 한 하이브리드 시나리오를 사용 하면 해당 클라우드 대응 하는와 통합 될 수 있도록 합니다.
    
2. Azure PaaS에 새로 추가 되거나 현대 응용 프로그램 개발 (영문)
    
    Azure PaaS 하이브리드 응용 프로그램에서 온-프레미스 서버 또는 저장소 리소스를 활용 안전 하 게 수 있습니다.
    
3. 기존 응용 프로그램을 Azure IaaS 이동
    
    리프트 shift 및 빌드 클라우드 시나리오에 대 한 Azure Vm에서 실행 중인 서버 기반 응용 프로그램 쉽게 구축 및 확장성을 제공 합니다.
    
## <a name="see-also"></a>참고 항목

[Microsoft Hybrid Cloud for Enterprise Architects](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Microsoft 클라우드 IT 아키텍처 리소스](microsoft-cloud-it-architecture-resources.md)

