---
title: Microsoft 하이브리드 클라우드 시나리오의 아키텍처
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 06d8c959-39e5-4150-b1ae-aaf0eee4c058
description: '요약: Microsoft의 하이브리드 클라우드 제품 아키텍처를 파악 합니다.'
ms.openlocfilehash: 513e45629a7092803cc644241d84985a37e43876
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068324"
---
# <a name="architecture-of-microsoft-hybrid-cloud-scenarios"></a>Microsoft 하이브리드 클라우드 시나리오의 아키텍처

 **요약:** Microsoft 하이브리드 클라우드 서비스의 아키텍처를 파악 합니다.
  
아키텍처 접근 방식을 사용 하 여 Microsoft 클라우드 서비스 및 플랫폼과 함께 하이브리드 클라우드 시나리오를 계획 하 고 구현 합니다.
  
**그림 1: Microsoft 하이브리드 클라우드 스택**

![Microsoft 하이브리드 클라우드 스택](media/Hybrid-Poster/Hybrid-Cloud-Stack.png)
  
그림 1은 온-프레미스, 네트워크, Id, 앱 및 시나리오, 클라우드 서비스 범주 (Microsoft SaaS, Azure PaaS 및 Azure PaaS)를 포함 하는 Microsoft 하이브리드 클라우드 스택 및 해당 계층을 보여 줍니다.
  
앱 및 시나리오 계층에는이 모델의 추가 문서에 자세히 설명 된 특정 하이브리드 클라우드 시나리오가 포함 되어 있습니다. Id, 네트워크 및 온-프레미스 계층은 클라우드 서비스 (SaaS, PaaS 또는 PaaS)의 범주에 공통 될 수 있습니다.
  
- 온-프레미스
    
    하이브리드 시나리오의 온-프레미스 인프라에는 SharePoint, Exchange, 비즈니스용 Skype 및 lob (기간 업무) 응용 프로그램에 대 한 서버가 포함 될 수 있습니다. 데이터 저장소 (데이터베이스, 목록, 파일)도 포함할 수 있습니다. Express 연결을 사용 하지 않으면 온-프레미스 데이터 저장소에 대 한 액세스를 역방향 프록시를 통해 허용 하거나 DMZ 또는 엑스트라넷에서 서버 또는 데이터에 액세스할 수 있도록 설정 해야 합니다.
    
- 네트워크
    
    Microsoft 클라우드 플랫폼과 서비스에 연결 하는 데는 두 가지 옵션이 있습니다 (기존 인터넷 파이프 및 Express). 예측 가능한 성능이 중요 한 경우에는 Express 연결을 사용 합니다. 하나의 Express 연결을 사용 하 여 Microsoft SaaS 서비스 (Office 365 및 Dynamics 365), Azure PaaS services 및 Azure IaaS 서비스에 직접 연결할 수 있습니다.
    
- ID
    
    클라우드 id 인프라의 경우 Microsoft 클라우드 플랫폼에 따라 두 가지 방법을 사용할 수 있습니다. SaaS 및 Azure PaaS의 경우 Azure AD와 온-프레미스 id 인프라를 통합 하거나 온-프레미스 id 인프라 또는 타사 id 공급자와 페더레이션 합니다. Azure에서 실행 되는 Vm의 경우 AD DS (Active Directory 도메인 서비스)와 같은 온-프레미스 id 인프라를 Vm이 상주 하는 가상 네트워크 (Vnet)로 확장할 수 있습니다.
    
## <a name="hybrid-cloud-scenarios-for-the-three-phase-cloud-adoption-process"></a>3 단계 클라우드 도입 프로세스에 대 한 하이브리드 클라우드 시나리오

Microsoft를 비롯 한 많은 기업에서는 3 단계 접근 방식을 사용 하 여 클라우드를 채택 합니다. 하이브리드 클라우드 시나리오에서는 각 단계에서 역할을 실행할 수 있습니다.
  
1. 업무 부하를 SaaS로 이동
    
    현재 온-프레미스에 있는 생산성 워크 로드의 경우 하이브리드 시나리오를 사용 하 여 해당 클라우드 사용자와 통합할 수 있습니다.
    
2. Azure PaaS에서 새로운 최신 응용 프로그램 개발
    
    Azure PaaS 하이브리드 응용 프로그램은 온-프레미스 서버 또는 저장소 리소스를 안전 하 게 활용할 수 있습니다.
    
3. Azure IaaS로 기존 응용 프로그램 이동
    
    리프트 및 비-클라우드 시나리오의 경우 Azure Vm에서 실행 되는 서버 기반 응용 프로그램은 쉬운 프로 비전 및 확장 기능을 제공 합니다.
    
## <a name="see-also"></a>참고 항목

[Microsoft Hybrid Cloud for Enterprise Architects](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Microsoft 클라우드 IT 아키텍처 리소스](microsoft-cloud-it-architecture-resources.md)

