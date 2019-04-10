---
title: Azure PaaS용 하이브리드 클라우드 시나리오
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 5f4f5d0d-4638-48e8-a517-bd804856b617
description: '요약: Azure의 Microsoft PaaS (Platform as a Service) 기반 클라우드 제품에 대 한 하이브리드 아키텍처 및 시나리오를 이해 합니다.'
ms.openlocfilehash: f4d90d51a7627063fae6fd168681bdf96cb4d6bc
ms.sourcegitcommit: 682b180061dc63cd602bee567d5414eae6942572
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/09/2019
ms.locfileid: "31741374"
---
# <a name="hybrid-cloud-scenarios-for-azure-paas"></a>Azure PaaS용 하이브리드 클라우드 시나리오

 **요약:** Azure의 PaaS (Platform as a Service) 기반 클라우드 제품에 대 한 하이브리드 아키텍처 및 시나리오를 이해 합니다.
  
온-프레미스 데이터 또는 컴퓨팅 리소스를 Azure PaaS에서 실행 되는 새로운 또는 변환 된 응용 프로그램으로 결합 하 여 클라우드 성능, 안정성 및 확장성을 활용 하 고 모바일 사용자에 대 한 향상 된 지원을 제공 합니다. 
  
## <a name="azure-paas-hybrid-scenario-architecture"></a>Azure PaaS 하이브리드 시나리오 아키텍처

그림 1에서는 Azure의 Microsoft PaaS 기반 하이브리드 시나리오 아키텍처를 보여 줍니다.
  
**그림 1: Azure의 Microsoft PaaS 기반 하이브리드 시나리오**

![Azure의 Microsoft PaaS 기반 하이브리드 시나리오](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS.png)
  
아키텍처의 각 계층에 대해 다음을 수행 합니다.
  
- 앱 및 시나리오
    
    하이브리드 PaaS 응용 프로그램은 Azure에서 실행 되며 온-프레미스 계산 또는 저장소 리소스를 사용 합니다.
    
- ID
    
    디렉터리 동기화 또는 타사 id 공급자와의 페더레이션으로 구성 됩니다.
    
- 네트워크
    
    기존 인터넷 파이프 또는 공용 피어 링을 통해 Azure PaaS로가는 express 연결로 구성 됩니다. Azure PaaS 응용 프로그램에서 온-프레미스 계산 또는 저장소 리소스에 액세스 하는 방법을 포함 해야 합니다.
    
- 온-프레미스
    
    id 및 보안 인프라와 Azure PaaS 응용 프로그램에서 안전 하 게 액세스할 수 있는 기존 LOB (기간 업무) 응용 프로그램 또는 데이터베이스 서버로 구성 됩니다.
    
## <a name="azure-paas-hybrid-application"></a>Azure PaaS hybrid 응용 프로그램

그림 2에서는 Azure에서 실행 되는 하이브리드 응용 프로그램의 구성을 보여 줍니다.
  
**그림 2: Azure PaaS 기반 하이브리드 응용 프로그램**

![Azure PaaS 기반 하이브리드 응용 프로그램](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS-Apps.png)
  
그림 2에서는 온-프레미스 네트워크가 서버의 저장소 또는 앱과 프록시 서버를 포함 하는 DMZ를 호스트 합니다. 인터넷을 통해 또는 express 연결을 통해 Azure PaaS 서비스에 연결 됩니다.
  
조직은 다음을 수행 하 여 Azure PaaS hybrid 응용 프로그램에서 해당 계산 또는 저장소 리소스를 사용할 수 있습니다.
  
- DMZ의 서버에서 리소스 호스팅
    
- DMZ에서 역방향 프록시 서버 호스팅 온-프레미스에 있는 리소스에 대해 인증 되 고 인바운드 되는 HTTPS 기반 요청을 허용 합니다.
    
Azure 앱은 다음의 자격 증명을 사용할 수 있습니다.
  
- Azure ad: ad DS (Active Directory 도메인 서비스)와 같은 온-프레미스 id 공급자와 동기화 할 수 있습니다.
    
- 타사 id 공급자
    
### <a name="example-azure-paas-hybrid-application"></a>예제 Azure PaaS hybrid application

그림 3에서는 Azure에서 실행 되는 하이브리드 응용 프로그램의 예를 보여 줍니다.
  
**그림 3: Azure PaaS 기반 하이브리드 응용 프로그램의 예**

![Azure PaaS 기반 하이브리드 application의 예](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS-Apps-Ex.png)
  
그림 3에서는 온-프레미스 네트워크가 LOB 앱을 호스트 합니다. Azure PaaS가 사용자 지정 모바일 앱을 호스트 합니다. 인터넷에서 smartphone은 온-프레미스 LOB 앱에 데이터 요청을 전송 하는 Azure의 사용자 지정 모바일 앱에 액세스 합니다.
  
이 예제 Azure PaaS 하이브리드 응용 프로그램은 직원에 게 최신 연락처 정보를 제공 하는 사용자 지정 모바일 앱입니다. 종단 간 하이브리드 시나리오는 다음으로 구성 됩니다.
  
- 유효성을 검사 하 고 실행할 온-프레미스 자격 증명을 확인 해야 하는 smartphone 앱입니다.
    
- 사용자의 smartphone 앱에 대 한 쿼리를 기반으로 특정 직원에 대 한 정보를 요청 하는 Azure PaaS에서 실행 되는 사용자 지정 모바일 앱입니다.
    
- DMZ에서 사용자 지정 모바일 앱의 유효성을 검사 하 고 요청을 전달 하는 역방향 프록시 서버입니다.
    
- 사용자 계정의 사용 권한에 따라 연락처 요청을 서비스 하는 LOB 응용 프로그램 서버 팜
    
온-프레미스 id 공급자가 Azure AD와 동기화 되었기 때문에 사용자 지정 모바일 앱과 LOB 앱이 모두 요청 하는 사용자의 계정 이름에 대 한 유효성을 검사할 수 있습니다.
  
## <a name="see-also"></a>참고 항목

[Microsoft Hybrid Cloud for Enterprise Architects](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Microsoft 클라우드 IT 아키텍처 리소스](microsoft-cloud-it-architecture-resources.md)

