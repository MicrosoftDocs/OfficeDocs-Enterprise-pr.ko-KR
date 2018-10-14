---
title: Project Server 2010 지원의 최종 로드맵
ms.author: efrene
author: efrene
manager: pamg
ms.date: 10/12/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: IT_ProjectAdmin
search.appverid:
- MET150
- ZPJ120
- PJU120
- PJW120
description: 2020, 10 월 13에 Project Server 2010에 대 한 끝을 지원 합니다. 이 문서를 사용 하 여 지금 업그레이드를 계획 합니다.
ms.openlocfilehash: bdfc4dd81dca7fe137be5780e54252eba961910f
ms.sourcegitcommit: e89b5306338ecdb40ad88efcf9cae3b8d5692924
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2018
ms.locfileid: "25549789"
---
# <a name="project-server-2010-end-of-support-roadmap"></a>Project Server 2010 끝날 지원 로드맵

2010, Office 2010 서버 및 응용 프로그램에 대 한 종료 되는 지원 하 고 마이그레이션에 대 한 계획을 고려해 야 합니다. Project Server 2010을 사용 중인 경우 note 것 소유자 및 기타 관련된 제품의 지원 날짜 다음 최종 갖게 됩니다.
  
|**제품**|**지원 날짜의 끝**|
|:-----|:-----|
|Project Server 2010  <br/> |2020 년 10 월 13,  <br/> |
|Project Portfolio Server 2010  <br/> |2020 년 10 월 13,  <br/> |
|Project 2010 표준  <br/> |2020 년 10 월 13,  <br/> |
|Project 2010 Professional  <br/> |2020 년 10 월 13,  <br/> |
   
Office 2010 서버 퇴직 도달 하는 방법에 대 한 자세한 내용은 [Office 2010 서버 및 클라이언트 제품에서 업그레이드](https://docs.microsoft.com/office365/enterprise/plan-upgrade-previous-versions-office)를 참조 하십시오.
  
## <a name="what-does-end-of-support-mean"></a>지원 의미의 역할 끝 무엇입니까?

Project Server 같은 거의 모든 Microsoft 제품의 새로운 기능, 버그 수정, 보안 픽스 등에 제공 하는 동안 지원 주기가 있습니다. 이 수명 주기는 일반적으로 제품의 초기 릴리스 날짜 로부터 10 년 동안 지속 하 고이 주기 끝이 제품의 지원 종료 라고 합니다. Project Server 2010에 2020, 10 월 10에서 지원의 끝에 도달 하기 때문에 Microsoft 제공 하지 않습니다.
  
- 발생할 수 있는 문제에 대 한 기술 지원 합니다.
    
- 버그 검색 되는 및 안정성과 사용 가능성 서버의 영향을 줄 수 있는 문제를 해결 합니다.
    
- 검색 되는 하 고 서버를 공격에 취약 한 보안 위반에 만들 수 있는 취약점에 대 한 보안은 수정 합니다.
    
- 표준 시간대를 업데이트합니다.
    
Project Server 2010의 설치 계속이 날짜 이후에 실행 됩니다. 그러나 위에 나열 된 변경으로 인해 좋습니다 마이그레이션하는 Project Server 2010에서 가능한 한 빨리.
  
## <a name="what-are-my-options"></a>내 옵션은 무엇입니까?

Project Server 2010을 사용 하는 경우에 마이그레이션 옵션을 사용 하 여 탐색 해야:
  
- 프로젝트를 온라인으로 마이그레이션
    
- 새로운 온-프레미스 버전의 Project Server (가능 하면 Project Server 2019)를 마이그레이션하십시오.
    
|**Project Online으로 마이그레이션 선호 하는 이유**|**Project Server 2019 마이그레이션하려면 선호 하는 이유**|
|:-----|:-----|
| 모바일 사용자에 게 했습니다.  <br/>  비용을 마이그레이션할 것은 큰 문제가 (하드웨어, 소프트웨어, 시간 및 등을 구현 하는 수단입니다.)입니다.  <br/>  마이그레이션 후 현재 환경에 맞게 유지 관리 비용의 큰 문제 (예, 자동 업데이트를 가동 시간 등을 보장 합니다.)에 있습니다.  <br/> | 비즈니스 규칙 클라우드에서 내 비즈니스 운영에서 나에 게 제한 합니다.  <br/>  I 업데이트 제어 환경에 맞게 해야합니다.  <br/> |
   
> [!NOTE]
> Office 2010 서버에서 이동 하기 위한 옵션에 대 한 자세한 내용은 [2010 서버와 클라이언트가 Office에서 업그레이드 하는데 도움이 되는 리소스](https://docs.microsoft.com/office365/enterprise/upgrade-from-office-2010-servers-and-products)를 참조 하십시오. Note Project Server Project Server 이후 하이브리드 구성을 지원 하지 않는 하 고 Project Online 동일한 자원 그룹을 공유할 수 없습니다. 
  
## <a name="important-considerations-you-need-to-make-when-planning-to-migrate-from-project-server-2010"></a>Project Server 2010에서 마이그레이션을 계획할 때 수행 해야하는 중요 한 고려 사항

Project Server 2010에서 마이그레이션을 계획할 때는 다음 사항을 고려 해야 합니다.
  
- **Microsoft 파트너에서 제공 하는 도움말** -Project Server 2010에서 업그레이드 하는 수 있는 것이 어려울 많은 준비 필요 하 고 계획 하 고 있습니다. 설치 하 고 Project Server 2010을 처음 구성할 하나 없었던 경우 특히 어려운 일 수 있습니다. 다행히, Project Server 2019 또는 Project Online으로 마이그레이션하는 방법에 계획 여부 생활,이 작업을 수행 하는 Microsoft 파트너를 만드는데 사용할 수 있습니다. [Microsoft 파트너 센터](https://go.microsoft.com/fwlink/p/?linkid=841249)에서 마이그레이션을 위해 Microsoft 파트너를 검색할 수 있습니다. *Gold 프로젝트 및 포트폴리오 관리* 용어를 검색 하 여 프로젝트에 대 한 전문 지식와 모든 Microsoft 파트너 목록을를 의뢰할 수 있습니다. 
    
- **사용자 지정에 대 한 계획** -는 다양 한 Project Server 2010 환경에서 작업을 한 사용자 지정 작동 하지 않을 수 Project Server 2019 또는 Project Online으로 마이그레이션하는 경우 유의 해야 합니다. 큰 차이가 Project Server 아키텍처 버전으로 필요한 운영 체제, 데이터베이스 서버 및 최신 버전과 함께 사용 하도록 지원 되는 클라이언트 웹 브라우저를 있습니다. 테스트 또는 새 환경에서 필요에 따라 사용자 지정을 다시 작성 하는 방법에 대 한 전체에서 요금제에 가입한 상태입니다. 업그레이드에 대 한 계획 앞으로 이동할 때 특정 사용자 지정 정말 필요한 경우를 확인 하려면 좋은 기회 됩니다. [SharePoint 2013으로 업그레이드 하는 동안 현재 사용자 지정에 대 한 적절 한 계획](https://go.microsoft.com/fwlink/p/?linkid=842061) 을 평가 하 고 업그레이드 시 현재 사용자 지정에 대 한 계획 하는 방법에 대 한 일부 뛰어난 일반 정보를 있습니다. 
    
- **시간 및 인 내** -업그레이드를 계획 하 고, 실행 및 테스트 걸립니다 많은 시간과 노력을 Project Server 2019로 업그레이드 하는 경우에 특히. 예, 경우 Project Server 2010에서 Project Server 2019로 마이그레이션하는 경우, Project Server 2010에서 Project Server 2013으로 마이그레이션 한 후, 데이터를 확인 하려면 먼저를 각 후속 버전 (프로젝트를 마이그레이션할 때 동일한 작업을 수행 합니다. 서버 2016 한 다음 Project Server 2019). 얼마나 오래 걸리는 하 고, 해당 하 고 비용 기능에서 추정과 예상된 비용을 비교 하려면 Microsoft 파트너 수도 있습니다. 
    
## <a name="migrate-to-project-online"></a>프로젝트를 온라인으로 마이그레이션

Project Server 2010에서 Project Online으로 마이그레이션하는 경우에 수동으로 프로젝트 계획 데이터를 마이그레이션하려면 다음을 수행할 수 있습니다.
  
1. Project Server 2010에서 프로젝트 계획을 저장 합니다. MPP 형식입니다.
    
2. Project Professional 2016, Project Professional 2019 또는 프로젝트 온라인 데스크톱 클라이언트를 사용 하 여 각.mpp 파일을 열고 하 고을 저장 하 고 Project Online에 게시 합니다.
    
Project Online에서 PWA 구성을 수동으로 만들 수 있습니다 (예: 필요한 사용자 정의 필드나 enterprise 달력 다시). Microsoft 파트너 대체 되는 도움말 수 있습니다.
  
주요 리소스:
  
|**리소스**|**설명**|
|:-----|:-----|
|[Project Online 시작 하기](https://support.office.com/article/e3e5f64f-ada5-4f9d-a578-130b2d4e5f11) <br/> |설치 하 고 Project Online을 사용 하는 방법입니다.  <br/> |
|[Project Online 서비스 설명](https://go.microsoft.com/fwlink/p/?linkid=829088) <br/> |사용할 수 있는 다른 온라인 프로젝트 계획에 대 한 정보를 제공 합니다.  <br/> |
   
## <a name="migrate-to-a-newer-on-premises-version-of-project-server"></a>새로운 온-프레미스 버전의 Project Server를 마이그레이션하십시오.

Project Online으로 마이그레이션하는 방법으로 최상의 값 및 사용자 경험을 얻을 수 있는을 강력 하 게 광고, 하는 동안는 또한 이해 일부 조직에서는 온-프레미스 환경에서 프로젝트 데이터를 유지 해야 합니다. 프로젝트 데이터에서 온-프레미스 유지 하려는 경우에 Project Server 2013, Project Server 2016 또는 Project Server 2019 Project Server 2010 환경을 마이그레이션할 수 있습니다.
  
Project Online을 마이그레이션할 수 없는 경우 Project Server 2019를 마이그레이션하는 것이 좋습니다. Project Server 2019 기능 및 Project Server의 이전 버전에 포함 된 고급 기능을 통해 대부분의 키를 포함 하 고 (Project Online에 사용할 수 있는 일부 기능) 있지만 Project Online을 사용할 수 있는 환경에서 가장 근접 하 게 일치 합니다.
  
각 마이그레이션을 완료 한 후에 성공적으로 마이그레이션 되었는지 확인 하려면 데이터를 확인 해야 합니다.
  
> [!NOTE]
> 온-프레미스 솔루션으로 제한 하는 경우에 Project Server 2013 마이그레이션를 고려 하는 경우에 지원 왼쪽의 더 많은 몇 년만에 있는지 확인 하는 것이 중요 합니다. Project Server 2013 서비스 팩 2 지원 날짜의 끝이 10/13/2023 합니다. 지원 날짜의 끝에 대 한 자세한 내용은 [Microsoft 제품 수명 주기 정책](https://go.microsoft.com/fwlink/p/?linkid=842066)을 참조 하십시오. 
  
### <a name="how-do-i-migrate-to-project-server-2019"></a>Project Server 2019를 마이그레이션하려면 어떻게 해야 합니까?

Project Server 2010 및 Project Server 2019 아키텍처 차이점 직접 마이그레이션 경로 방지 합니다. 즉, Project Server 2019로 업그레이드할 때까지 다음 연속 된 버전의 Project Server에 Project Server 2010 데이터를 마이그레이션할 해야 합니다.
  
Project Server 2019로 업그레이드 하려면 다음 작업을 수행 해야 합니다.
  
1. 1 단계: Project Server 2013에 Project Server 2010에서 데이터를 마이그레이션하십시오.
    
2. 2 단계: Project Server 2016를 처리할 2013 프로젝트에서에서 데이터를 마이그레이션하십시오.
    
3. 3 단계: Project Server 2019에 Project Server 2016에서 데이터를 마이그레이션하십시오.
    
각 마이그레이션을 완료 한 후에 성공적으로 마이그레이션 되었는지 확인 하려면 데이터를 확인 해야 합니다.
  
    
### <a name="step-1-migrate-to-project-server-2013"></a>1 단계: Project Server 2013으로 마이그레이션

Project Server 2019로 Project Server 2010 데이터 마이그레이션 가장 먼저 먼저 Project Server 2013으로의 마이그레이션에 합니다. 
  
Project Server 2010에서 Project Server 2013으로 업그레이드를 수행 하는데 필요한의 포괄적인 이해 하십시오 TechNet의 [Project Server 2013으로 업그레이드](https://go.microsoft.com/fwlink/p/?linkid=841822) 콘텐츠 설정을 참조 하십시오. 
  
주요 리소스:
  
|**리소스**|**설명**|
|:-----|:-----|
|[개요 (영문) Project Server 2013의 업그레이드 프로세스](https://go.microsoft.com/fwlink/p/?linkid=841822) <br/> |높은 수준의 파악 Project Server 2010에서 Project Server 2013으로 업그레이드 하기 위해 수행 해야 합니다.  <br/> |
|[Project Server 2013으로의 업그레이드 계획](https://go.microsoft.com/fwlink/p/?linkid=841823) <br/> |계획 고려 사항에 Project Server 2013, 시스템 요구 사항을 포함 하 여 Project Server 2010에서 업그레이드 하는 경우를 결정 해야 하는 방법을 살펴봅니다.  <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>이 버전으로 업그레이드에 대해 고려할 사항

[Project Server 2013 업그레이드의 새로운](https://go.microsoft.com/fwlink/p/?linkid=841824) 가장 두드러진 되 고,이 버전에 대 한 업그레이드에 대 한 몇가지 중요 한 변경 내용을 지시 합니다. 
  
- Project Server 2013으로 전체 업그레이드 안함 방법이 있습니다. 데이터베이스 연결 메서드는 Project Server 2010에서 Project Server 2013으로 업그레이드 하는 것에 대 한 지원 되는 유일한 방법입니다.
    
- 업그레이드 프로세스만 Project Server 2010 데이터를 Project Server 2013 형식으로 변환 하지는 하지만 Project Server 2010 데이터베이스를 단일 Project Web App 데이터베이스는 4 개의 통합도 됩니다.
    
- SharePoint Server 2013 및 Project Server 2013 모두는 이전 버전에서 클레임 기반 인증으로 변경 합니다. 클래식 인증을 사용 하는 경우 업그레이드 시 고려 사항을 확인 해야 합니다. 자세한 내용은 [SharePoint 2013의 클레임 기반 인증을 클래식 모드에서 마이그레이션](https://go.microsoft.com/fwlink/p/?linkid=841825)을 참조 합니다.
    
추가 리소스:
  
- [Project Server 2013으로의 업그레이드 프로세스 개요](https://go.microsoft.com/fwlink/p/?linkid=841274)
    
- [데이터베이스 및 Project Web App 사이트 모음 업그레이드(Project Server 2013)](https://go.microsoft.com/fwlink/p/?linkid=841272)
    
- [Microsoft Project Server 업그레이드 프로세스 다이어그램](https://go.microsoft.com/fwlink/p/?linkid=841270)
    
- [쉬운 8 단계에서 Project Server 2010에 2013 마이그레이션 뛰어난 데이터베이스 통합](https://go.microsoft.com/fwlink/p/?linkid=841271)
    
### <a name="step-2-migrate-to-project-server-2016"></a>2 단계에서 Project Server 2016 마이그레이션

다음 단계를 Project Server 2013으로 마이그레이션 및 데이터가 성공적으로 마이그레이션 되었는지 확인 (영문), 후 Project Server 2016에 데이터를 마이그레이션합니다.
  
Project Server 2013에서 Project Server 2016으로 업그레이드를 수행 하는데 필요한의 포괄적인 이해, [Project Server 2016로 업그레이드](https://docs.microsoft.com/en-us/Project/upgrade-to-project-server-2016) 하는 콘텐츠 설정을 참조 하십시오.
  
주요 리소스:
  
|**리소스**|**설명**|
|:-----|:-----|
|[Project Server 2016 업그레이드 프로세스 개요](https://docs.microsoft.com/Project/overview-of-the-project-server-2016-upgrade-process) <br/> |높은 수준의 파악 Project Server 2013에서 Project Server 2016으로 업그레이드 하기 위해 수행 해야 합니다.  <br/> |
|[Project Server 2016으로의 업그레이드 계획](https://docs.microsoft.com/Project/plan-for-upgrade-to-project-server-2016) <br/> |Project Server 2013에서 Project Server 2016로 업그레이드 하는 경우 해야하는 계획 고려 사항을 살펴봅니다.  <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>이 버전으로 업그레이드에 대해 고려할 사항

[Project Server 2016 하는 방법에 대 한 알아두어야 할 사항 업그레이드](https://docs.microsoft.com/project/plan-for-upgrade-to-project-server-2016#thingknow) 를 포함 하는이 버전에 대 한 업그레이드에 대 한 중요 한 일부 변경 지시 합니다. 
  
- Project Server 2016 환경을 Project Server 2013 데이터를 마이그레이션할 사항에 유의 합니다를 만들 때 SharePoint Server 2016에 Project Server 2016 설치 파일이 포함 됩니다. 자세한 내용은 [Project Server 2016 배포](https://go.microsoft.com/fwlink/p/?linkid=841829)를 참조 하십시오.
    
- 자원 계획은 Project Server 2016 사용 되지 않습니다. Project Server 2013 자원 계획을 세울 Project Server 2016 및 Project Online에서 자원의 계약으로 마이그레이션됩니다. 참조 [개요: 자원의 계약](https://support.office.com/article/73eefb5a-81fe-42bf-980e-9532b1bdc870) 에 대 한 자세한 내용은 합니다. 
    
### <a name="step-3-migrate-to-project-server-2019"></a>3 단계에서 Project Server 2019 마이그레이션

다음 단계를 Project Server 2016로 마이그레이션 및 데이터가 성공적으로 마이그레이션 되었는지 확인 (영문), 후 Project Server 2019에 데이터를 마이그레이션합니다.
  
Project Server 2016에서 Project Server 2019로 업그레이드를 수행 하는데 필요한의 포괄적인 이해, [Project Server 2019로 업그레이드](https://docs.microsoft.com/en-us/Project/upgrade-to-project-server-2016) 하는 콘텐츠 설정을 참조 하십시오.
  
주요 리소스:
  
|**리소스**|**설명**|
|:-----|:-----|
|[Project Server 2019 개요 업그레이드 프로세스](https://docs.microsoft.com/project/overview-of-the-project-server-2019-upgrade-process) <br/> |높은 수준의 파악 Project Server 2013에서 Project Server 2016으로 업그레이드 하기 위해 수행 해야 합니다.  <br/> |
|[Project Server 2019로의 업그레이드 계획](https://docs.microsoft.com/project/plan-for-upgrade-to-project-server-2019) <br/> |Project Server 2016에서 Project Server 2019로 업그레이드 하는 경우 해야하는 계획 고려 사항을 살펴봅니다.  <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>이 버전으로 업그레이드에 대해 고려할 사항

[Project Server 2019 하는 방법에 대 한 알아두어야 할 사항 업그레이드](https://go.microsoft.com/fwlink/p/?linkid=841827) 를 포함 하는이 버전에 대 한 업그레이드에 대 한 중요 한 일부 변경 지시 합니다. 
  
- 업그레이드 프로세스는 SharePoint Server 2019 콘텐츠 데이터베이스를 Project Server 2016 데이터베이스에서 데이터를 마이그레이션합니다.  Project Server 2019 더 긴 새 폴더를 만듭니다 SharePoint 서버 팜에 있는 Project Server 데이터베이스를 소유 하 고 있습니다.

- 업그레이드 후 Project Web App에서 여러 변경 사항을 알고 있어야 합니다.  이러한 설명, [Project Server 2019의 새로운 란](https://docs.microsoft.com/en-us/project/what-s-new-for-it-pros-in-project-server-2019#PWAChanges)을 참조 하십시오.


## <a name="migrate-from-portfolio-server-2010"></a>Portfolio Server 2010에서 마이그레이션

Project Portfolio Server 2010 포트폴리오 전략, 우선순위 지정 및 최적화에 대 한 Project Server 2010과 함께 사용 되었습니다. 이 버전 후 없음 추가 버전의 Project Portfolio Server을 만들었습니다. 그러나 포트폴리오 관리 기능을 이상 Project Server 버전 및 Project Online의 프리미엄 버전에서 사용할 수 있습니다. Project Portfolio Server 2010에서 데이터를 마이그레이션할 수 없습니다. 비즈니스 영향 요소 등의 데이터를 다시 만들 해야 합니다.
  
기타 리소스:
  
- [Project Online 서비스 설명](https://go.microsoft.com/fwlink/p/?linkid=841280): Project Server 2016 및 온라인 프리미엄 프로젝트에 포함 된 포트폴리오 관리 기능을 참조 하십시오.
    
- [Microsoft Office Project Portfolio Server 2010의 마이그레이션 가이드](https://go.microsoft.com/fwlink/p/?linkid=841279)
    
## <a name="related-topics"></a>관련 항목

[SharePoint 2010에서 업그레이드](upgrade-from-sharepoint-2010.md)
  
[2010 서버와 클라이언트에서 Office를 업그레이드 하는데 도움이 되는 리소스](upgrade-from-office-2010-servers-and-products.md)
  

