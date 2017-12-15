---
title: "Azure PaaS에 대 한 하이브리드 클라우드 시나리오"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Visuals
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 5f4f5d0d-4638-48e8-a517-bd804856b617
description: "요약: 경우 서비스로 (PaaS) Microsoft의 플랫폼에 대 한 하이브리드 아키텍처 및 시나리오 이해-Azure의 클라우드 서비스를 기반으로 합니다."
ms.openlocfilehash: f6d7d1c9ca04c0b7bbaa020a771cf84734e5d385
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2017
---
# <a name="hybrid-cloud-scenarios-for-azure-paas"></a>Azure PaaS에 대 한 하이브리드 클라우드 시나리오

 **요약:** 서비스로 (PaaS) Microsoft의 플랫폼에 대 한 하이브리드 아키텍처 및 시나리오 이해-Azure의 클라우드 서비스를 기반으로 합니다.
  
온-프레미스 데이터를 결합 하 또는 새롭거나 변환 된 응용 프로그램의 기능을 사용할 수 있는 Azure PaaS에서 실행 중인 컴퓨팅 리소스 클라우드 성능, 안정성 및 확장 하 고 모바일 사용자를 위한 향상 된 지원을 제공 합니다. 
  
## <a name="azure-paas-hybrid-scenario-architecture"></a>Azure PaaS 하이브리드 시나리오 아키텍처

그림 1 Azure의 Microsoft PaaS 기반 하이브리드 시나리오의 아키텍처를 보여줍니다.
  
**Azure의 그림 1: Microsoft PaaS 기반 하이브리드 시나리오**

![Azure의 Microsoft PaaS 기반 하이브리드 시나리오](images/Hybrid_Poster/Hybrid_Cloud_Stack_PaaS.png)
  
아키텍처의 각 레이어에:
  
- 앱 및 시나리오
    
    하이브리드 PaaS 응용 프로그램을 Azure에서 실행 하 고 온-프레미스 compute 또는 저장소 리소스를 사용 합니다.
    
- Identity
    
    디렉터리 동기화 또는 타사 id 공급자와의 페더레이션을 구성 됩니다.
    
- 네트워크
    
    기존 인터넷 파이프 대화 또는 Azure PaaS에 공용 피어 링와 ExpressRoute 연결으로 구성 됩니다. Azure PaaS 응용 프로그램 온-프레미스 compute 또는 저장소 리소스에 액세스 하는 방법을 포함 해야 합니다.
    
- 온-프레미스
    
    Id 및 보안 인프라 및 기간 업무 (LOB) 응용 프로그램 또는 Azure PaaS 응용 프로그램에 안전 하 게 액세스할 수 있는 데이터베이스 서버를 기존 줄으로 구성 됩니다.
    
## <a name="azure-paas-hybrid-application"></a>Azure PaaS 하이브리드 응용 프로그램

그림 2 Azure에서 실행 되는 하이브리드 응용 프로그램의 구성을 보여줍니다.
  
**그림 2: Azure PaaS 기반 하이브리드 응용 프로그램**

![Azure PaaS 기반 하이브리드 응용 프로그램](images/Hybrid_Poster/Hybrid_Cloud_Stack_PaaS_Apps.png)
  
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

![Azure PaaS 기반 하이브리드 응용 프로그램 예제](images/Hybrid_Poster/Hybrid_Cloud_Stack_PaaS_Apps_Ex.png)
  
그림 3에서는 LOB 프로그램는 온-프레미스 네트워크 호스트 app. Azure PaaS 사용자 지정 모바일 응용을 프로그램을 호스팅합니다. 인터넷에서 smartphone 온-프레미스 LOB 응용 프로그램에 데이터 요청을 보내는 Azure에서 사용자 지정 모바일 응용 프로그램에 액세스 합니다.
  
이 예제에서는 Azure PaaS 하이브리드 응용 프로그램은 직원에 최신 연락처 정보를 제공 하는 사용자 지정 모바일 응용 프로그램입니다. 끝-하이브리드 시나리오는 다음으로 구성 됩니다.
  
- Smartphone 응용 프로그램에 필요한 유효성을 검사를 실행 하려면 온-프레미스 자격 증명입니다.
    
- 사용자 지정 모바일 응용 프로그램 사용자의 smartphone 응용 프로그램에서 쿼리를 기초로 하는 특정 직원에 대 한 정보를 요청 하는 Azure PaaS에서 실행 합니다.
    
- 사용자 지정 모바일 응용 프로그램의 유효성을 검사 하 고 요청을 전달 하는 DMZ에서 역방향 프록시 서버입니다.
    
- 사용자 계정의 권한에 따라 달라 집니다 연락처 요청을 처리 하는 LOB 응용 프로그램 서버 팜.
    
온-프레미스 id 공급자를 Azure AD와 동기화 하기 때문에 사용자 지정 모바일 응용 프로그램 및 LOB 응용 프로그램을 모두 요청 하는 사용자의 계정 이름을 확인할 수 있습니다.
  
## <a name="stretch-database-with-sql-server-2016"></a>SQL Server 2016에 적용된 스트레치 데이터베이스

늘이기 데이터베이스는 투명 하 게 하 고 안전 하 게 Azure에서 SQL 전체 확대/축소 데이터베이스에 고객 주문 정보를 포함 하는 대규모 테이블에서 닫힌된 비즈니스 데이터와 같은 정지 데이터를 이동할 수 있도록 하는 SQL Server 2016의 기능입니다.
  
SQL Server 인스턴스, 데이터베이스 또는 단일 테이블도의 내용을 맞춰지거나 때 SQL Server 2016 서버에서 로컬 데이터와 Azure에서 원격 데이터의 조합 합니다. 전체 확대/축소에 대 한 대상이 되는 데이터는 SQL Server 2016 하 여 Azure에 자동으로 이동 됩니다.
  
그림 4 SQL Server 2016를 사용 하 여 전체 확대/축소 데이터베이스를 보여줍니다.
  
**그림 4: SQL server 2016 늘이기 데이터베이스**

![SQL Server 2016에 적용된 스트레치 데이터베이스](images/Hybrid_Poster/Hybrid_Cloud_Stack_PaaS_Apps_SQL.png)
  
그림 4는 온-프레미스 네트워크 작은 로컬 데이터베이스가 있는 SQL Server 2016를 실행 하는 서버를 호스트 합니다. Azure PaaS 데이터베이스의 확장 된 부분으로 Azure SQL Server 전체 확대/축소 데이터베이스의 인스턴스를 호스팅합니다. 온-프레미스 SQL server로 전송 하는 온-프레미스 사용자 로부터 T-SQL 쿼리는 안전 하 게 요청 하는 사용자에 게 결과 반환 하는 Azure SQL 전체 확대/축소 데이터베이스에 전달 됩니다.
  
 Azure SQL 전체 확대/축소 데이터베이스에 기록 데이터를 포함 하는 사용자 쿼리를 전달 투명 하 게 됩니다. 쿼리는 테이블을 확대 하는 경우에를 다시 쓰도록 필요는 없습니다.
  
늘이기 데이터베이스 장기 저장소 및 기록 데이터를 투명 하 게 액세스를 위한 비용 효율적인 옵션을 제공합니다. 또한 성능과 테이블 매우 큰 될 때 발생 하는 가용성 문제를 해결 합니다.
  
자세한 내용은 [전체 확대/축소 데이터베이스](https://msdn.microsoft.com/library/dn935011.aspx)를 참조 하십시오.
  
## <a name="see-also"></a>See Also

[엔터프라이즈 설계자 용 Microsoft 하이브리드 클라우드](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Microsoft 클라우드 IT 아키텍처 리소스](microsoft-cloud-it-architecture-resources.md)

[Microsoft의 엔터프라이즈 클라우드 로드맵: IT 의사 결정권자를 위한 리소스](https://sway.com/FJ2xsyWtkJc2taRD)



