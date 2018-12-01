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
description: '요약: 경우 서비스로 (PaaS) Microsoft의 플랫폼에 대 한 하이브리드 아키텍처 및 시나리오 이해-Azure의 클라우드 서비스를 기반으로 합니다.'
ms.openlocfilehash: e536d81b6b14b05bef49d7c91b0404faec64303b
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123335"
---
# <a name="hybrid-cloud-scenarios-for-azure-paas"></a>Azure PaaS용 하이브리드 클라우드 시나리오

 **요약:** 서비스로 (PaaS) Microsoft의 플랫폼에 대 한 하이브리드 아키텍처 및 시나리오 이해-Azure의 클라우드 서비스를 기반으로 합니다.
  
온-프레미스 데이터를 결합 하 또는 새롭거나 변환 된 응용 프로그램의 기능을 사용할 수 있는 Azure PaaS에서 실행 중인 컴퓨팅 리소스 클라우드 성능, 안정성 및 확장 하 고 모바일 사용자를 위한 향상 된 지원을 제공 합니다. 
  
## <a name="azure-paas-hybrid-scenario-architecture"></a>Azure PaaS 하이브리드 시나리오 아키텍처

그림 1 Azure의 Microsoft PaaS 기반 하이브리드 시나리오의 아키텍처를 보여줍니다.
  
**Azure의 그림 1: Microsoft PaaS 기반 하이브리드 시나리오**

![Azure의 Microsoft PaaS 기반 하이브리드 시나리오](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS.png)
  
아키텍처의 각 레이어에:
  
- 앱 및 시나리오
    
    하이브리드 PaaS 응용 프로그램을 Azure에서 실행 하 고 온-프레미스 compute 또는 저장소 리소스를 사용 합니다.
    
- ID
    
    디렉터리 동기화 또는 타사 id 공급자와의 페더레이션을 구성 됩니다.
    
- 네트워크
    
    기존 인터넷 파이프 대화 또는 Azure PaaS에 공용 피어 링와 ExpressRoute 연결으로 구성 됩니다. Azure PaaS 응용 프로그램 온-프레미스 compute 또는 저장소 리소스에 액세스 하는 방법을 포함 해야 합니다.
    
- 온-프레미스
    
    Id 및 보안 인프라 및 기간 업무 (LOB) 응용 프로그램 또는 Azure PaaS 응용 프로그램에 안전 하 게 액세스할 수 있는 데이터베이스 서버를 기존 줄으로 구성 됩니다.
    
## <a name="azure-paas-hybrid-application"></a>Azure PaaS 하이브리드 응용 프로그램

그림 2 Azure에서 실행 되는 하이브리드 응용 프로그램의 구성을 보여줍니다.
  
**그림 2: Azure PaaS 기반 하이브리드 응용 프로그램**

![Azure PaaS 기반 하이브리드 응용 프로그램](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS-Apps.png)
  
그림 2의 온-프레미스 네트워크 저장소 또는 서버와 프록시 서버를 포함 하는 DMZ에서 앱을 호스팅합니다. 인터넷을 통해 나 ExpressRoute 연결을 사용 하 여 Azure PaaS 서비스에 연결 됩니다.
  
조직 수 하 여 Azure PaaS 하이브리드 응용 프로그램에 사용할 수 있는 compute 또는 저장소 리소스를 확인 합니다.
  
- DMZ 서버에서 리소스를 호스트 합니다.
    
- 있는 온-프레미스 리소스에 대 한 인증 된, 인바운드, HTTPS 기반 요청을 허용 하는 DMZ에 역방향 프록시 서버를 호스팅, 합니다.
    
Azure 응용 프로그램에서 자격 증명을 사용할 수 있습니다.
  
- Windows Server AD와 같은 하도록 온-프레미스 id 공급자와 동기화 할 수 있는 azure AD
    
- 타사 id 공급자입니다.
    
### <a name="example-azure-paas-hybrid-application"></a>예제 Azure PaaS 하이브리드 응용 프로그램

그림 3은 Azure에서 실행 하는 예제 하이브리드 응용 프로그램을 보여줍니다.
  
**그림 3: 예 Azure PaaS 기반 하이브리드 응용 프로그램**

![Azure PaaS 기반 하이브리드 응용 프로그램 예제](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS-Apps-Ex.png)
  
그림 3에서는 LOB 프로그램는 온-프레미스 네트워크 호스트 app. Azure PaaS 사용자 지정 모바일 응용을 프로그램을 호스팅합니다. 인터넷에서 smartphone 온-프레미스 LOB 응용 프로그램에 데이터 요청을 보내는 Azure에서 사용자 지정 모바일 응용 프로그램에 액세스 합니다.
  
이 예제에서는 Azure PaaS 하이브리드 응용 프로그램은 직원에 최신 연락처 정보를 제공 하는 사용자 지정 모바일 응용 프로그램입니다. 끝-하이브리드 시나리오는 다음으로 구성 됩니다.
  
- Smartphone 응용 프로그램에 필요한 유효성을 검사를 실행 하려면 온-프레미스 자격 증명입니다.
    
- 사용자 지정 모바일 응용 프로그램 사용자의 smartphone 응용 프로그램에서 쿼리를 기초로 하는 특정 직원에 대 한 정보를 요청 하는 Azure PaaS에서 실행 합니다.
    
- 사용자 지정 모바일 응용 프로그램의 유효성을 검사 하 고 요청을 전달 하는 DMZ에서 역방향 프록시 서버입니다.
    
- 사용자 계정의 권한에 따라 달라 집니다 연락처 요청을 처리 하는 LOB 응용 프로그램 서버 팜.
    
온-프레미스 id 공급자를 Azure AD와 동기화 하기 때문에 사용자 지정 모바일 응용 프로그램 및 LOB 응용 프로그램을 모두 요청 하는 사용자의 계정 이름을 확인할 수 있습니다.
  
## <a name="see-also"></a>참고 항목

[Microsoft Hybrid Cloud for Enterprise Architects](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Microsoft 클라우드 IT 아키텍처 리소스](microsoft-cloud-it-architecture-resources.md)

