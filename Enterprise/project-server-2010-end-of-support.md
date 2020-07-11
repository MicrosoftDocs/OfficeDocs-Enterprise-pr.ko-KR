---
title: Project Server 2010 지원 종료 로드맵
ms.author: efrene
author: efrene
manager: pamg
ms.date: 04/14/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: IT_ProjectAdmin
search.appverid:
- MET150
- ZPJ120
- PJU120
- PJW120
description: Project Server 2010의 지원 종료는 4 월 13 2021 일에 종료 됩니다. 이 문서를 사용 하 여 Project Online으로 업그레이드 하는 방법 또는 온-프레미스 Project Server의 새 버전으로 업그레이드할 수 있습니다.
ms.openlocfilehash: cd209b51c94abe1a32b5d48bde79a3d1a443a092
ms.sourcegitcommit: d8ca7017b25d5ddc2771e662e02b62ff2058383b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2020
ms.locfileid: "45102596"
---
# <a name="project-server-2010-end-of-support-roadmap"></a>Project Server 2010의 지원 종료 로드맵

*이 문서는 Microsoft 365 Enterprise 및 Office 365 Enterprise에 모두 적용 됩니다.*

Project Server 2010는 **2021 년 4 월 13 일**에 지원 종료에 도달 합니다. 이 날짜는 이전의 지원 종료 날짜에서 2020 년 10 월 13 일까지 연장 되었습니다. 현재 Project Server 2010을 사용 하 고 있는 경우 이러한 기타 관련 제품에는 다음과 같은 지원 종료 날짜가 나와 있습니다.
  
|**제품**|**지원 종료 날짜**|
|:-----|:-----|
|Project 2010 Standard <br/> |2020 년 10 월 13 일  <br/> |
|Project 2010 Professional  <br/> |2020 년 10 월 13 일  <br/> |

   
지원 종료에 도달 하는 Office 2010 서버에 대 한 자세한 내용은 [Upgrade From office 2010 server and client products](https://docs.microsoft.com/office365/enterprise/plan-upgrade-previous-versions-office)을 참조 하십시오.
  
## <a name="what-does-end-of-support-mean"></a>지원이 끝나는 것은 무엇을 의미 하나요?

Project Server에는 거의 모든 Microsoft 제품과 마찬가지로 새로운 기능, 버그 수정 및 보안 업데이트를 제공 하는 지원 주기가 있습니다. 일반적으로이 수명 주기는 제품 초기 릴리스 날짜 로부터 10 년 동안 지속 되며이 주기의 끝은 제품의 지원 종료 라고 합니다. Project Server 2010가 2021 년 4 월 13 일에 지원 종료에 도달 하면 더 이상 다음이 제공 되지 않습니다.
  
- 발생할 수 있는 문제에 대 한 기술 지원
    
- 검색 된 문제와 서버의 안정성 및 유용성에 영향을 줄 수 있는 문제에 대 한 버그 수정
    
- 검색 되어 서버에서 보안 위반에 취약 해질 수 있는 취약성에 대 한 보안 수정
    
- 표준 시간대 업데이트
    
이 날짜 후에는 Project Server 2010의 설치가 계속 실행 됩니다. 그러나 위에 나열 된 변경 사항으로 인해 가능한 한 빨리 Project Server 2010에서 마이그레이션하는 것이 좋습니다.
  
## <a name="what-are-my-options"></a>내 옵션 이란?

Project Server 2010을 사용 하는 경우 다음과 같은 마이그레이션 옵션을 검토 해야 합니다.
  
- Project Online으로 마이그레이션
    
- 새 온-프레미스 버전의 Project Server로 마이그레이션 (특히 Project Server 2019)

다음은 Project Server 2010에 대 한 지원 종료를 방지 하기 위해 수행할 수 있는 두 가지 경로입니다.

![Project Server 2010 업그레이드 경로](./media/project-server-2010-end-of-support/project-server-2010-end-of-support-timeline.png)

    


|**Project Server 2019로 마이그레이션하는 이유는 무엇 인가요?**|**Project Online으로 마이그레이션하는 이유는 무엇 인가요?**|
|:-----|:-----|
|비즈니스 규칙 클라우드에서 내 비즈니스를 운영 하는 것을 제한 합니다.  <br/>  내 환경에 대 한 업데이트를 제어 해야 합니다.  <br/> | 모바일 또는 원격 사용자가 있는 경우  <br/>  온-프레미스 서버 마이그레이션 비용은 중요 한 관심사 (하드웨어, 소프트웨어, 시간 및 구현 노력 등)입니다.  <br/>  마이그레이션 후 내 환경을 유지 관리 하는 비용은 대규모 관심사 (예: 자동 업데이트, 보장 된 가동 시간 등)입니다.  <br/>  |

   
> [!NOTE]
> Office 2010 서버에서 이동 하는 방법에 대 한 자세한 내용은 [office 2010 서버 및 클라이언트에서 업그레이드 하는 데 도움이](https://docs.microsoft.com/office365/enterprise/upgrade-from-office-2010-servers-and-products)되는 리소스를 참조 하십시오. Project Server 및 Project Online에서는 동일한 자원 그룹을 공유할 수 없으므로 Project Server에서는 하이브리드 구성을 지원 하지 않습니다. 

### <a name="what-are-my-options-for-project-client"></a>Project 클라이언트에 대 한 내 옵션은 무엇입니까?
Project Professional 2010 또는 Project Standard 2010을 사용 하는 경우 마이그레이션 옵션을 탐색 하려면 다음 항목을 선택 해야 합니다.
- 최신 버전의 Project Professional 또는 Project Standard로 이동 하는 경우
- Project Online 또는 웹 프로젝트와 같은 온라인 솔루션으로 전환
 
#### <a name="moving-to-a-newer-version-of-project-client"></a>최신 버전의 Project 클라이언트로 이동

Project Standard 2010에서 마이그레이션하는 경우 최신 버전의 Project Standard (Project Standard 2016 또는 Project Standard 2019)로 마이그레이션할 수 있습니다.  최신 기능을 활용 하도록 최신 버전으로 이동 하는 것이 좋습니다. 또한 최신 버전 (Project Standard 2016)으로 마이그레이션하는 경우 지원 날짜가 완료 되 면이 버전에서 마이그레이션 해야 합니다.

마찬가지로 Project Professional 2010에서 마이그레이션하는 경우에는 최신 버전 (Project Professional 2019 또는 Project Professional 2016)으로 마이그레이션할 수 있습니다. 가능한 경우 최신 버전으로 이동 하는 것이 좋습니다.  Project Professional을 사용 하 여 Project Server에 연결 하는 경우에는 사용 중인 Project Server의 버전과 연결 하기 위해 지원 되는 Project Professional 버전으로 마이그레이션해야 합니다.

Project Professional 2010 사용자는 Project Online 데스크톱 클라이언트로의 마이그레이션도 선택할 수 있습니다. 이는 구독 기반 버전의 Project Professional 2019 이며, 프로젝트 계획 3 및 Project 계획 5 구독에 포함 되어 있습니다. 

#### <a name="moving-to-an-online-solution"></a>온라인 솔루션으로 이동

Project Professional 2010 또는 Project Standard 2010에서 Project의 구독 기반 온라인 솔루션으로 마이그레이션할 수도 있습니다. Project 요금제 3 및 계획 5에는 Project Online과 [웹에 대 한](https://support.office.com/article/what-can-you-do-with-project-for-the-web-b30f5442-be5f-43d2-9072-c95bff778ea1)최신 클라우드 제공이 포함 되어 있습니다. 둘 다 다양 한 새로운 기능과 이점을 제공 합니다.

에 포함 된 기능 및 프로젝트 계획 라이선스에 대 한 자세한 내용은 [Microsoft Project service description](https://docs.microsoft.com/office365/servicedescriptions/project-online-service-description/project-online-service-description)을 참고 하세요.



  
## <a name="important-considerations-you-need-to-make-when-planning-to-migrate-from-project-server-2010"></a>Project Server 2010에서 마이그레이션을 계획할 때 수행 해야 하는 중요 고려 사항

Project Server 2010에서 마이그레이션을 계획할 때 고려해 야 할 사항은 다음과 같습니다.
  
- **Microsoft 솔루션 공급자가 제공 하는 도움말 보기** -Project Server 2010에서 업그레이드 하는 것은 어려울 수 있으며, 준비 및 계획이 많이 필요 합니다. 이는 설정 하는 것이 아니라 원래 Project Server 2010을 구성 하는 것이 어려운 경우에 특히 유용 합니다. 다행 스럽게도, Project Server 2019로 마이그레이션을 계획 하거나 Project Online으로 마이그레이션할 지 여부에 관계 없이이 작업을 수행할 수 있는 Microsoft 솔루션 공급자가 있습니다. Microsoft solution provider를 검색 하 여 사용자의 마이그레이션에 도움을 받을 수 [있습니다.](https://go.microsoft.com/fwlink/p/?linkid=841249) 
    
- **사용자 지정 계획** -project server 2019로 마이그레이션하거나 project Online으로 마이그레이션하는 경우 프로젝트 서버 2010 환경에서 작업 하는 많은 사용자 지정 내용이 작동 하지 않을 수 있다는 점을 염두에 두어야 합니다. 버전 간 Project Server 아키텍처에는 큰 차이점이 있으며, 새 버전에서 작동 하도록 지원 되는 필수 운영 체제, 데이터베이스 서버 및 클라이언트 웹 브라우저에는 차이가 있습니다. 새 환경에서 필요에 따라 사용자 지정 내용을 테스트 하거나 다시 작성 하는 방법에 대 한 계획을 수립 합니다. 업그레이드를 계획할 때는 앞으로 이동할 때 특정 사용자 지정이 실제로 필요한 지를 확인 하는 것도 좋은 기회입니다. [Upgrade for current 사용자 지정 계획 만들기 2013]( https://docs.microsoft.com/SharePoint/upgrade-and-update/create-a-plan-for-current-customizations-during-upgrade-to-sharepoint-2013) 에서는 업그레이드 시 현재 사용자 지정 내용에 대 한 평가 및 계획에 대 한 몇 가지 일반적인 정보를 제공 합니다. 
    
- 특히 Project Server 2019로 업그레이드 하는 경우 **시간 및 고 지** 업그레이드 계획, 실행 및 테스트에 많은 시간과 노력이 소요 될 수 있습니다. 예를 들어 Project Server 2010에서 Project Server 2019로 마이그레이션하는 경우 먼저 Project Server 2010에서 Project Server 2013로 마이그레이션한 다음 데이터를 확인 한 다음, 연속 된 각 버전으로 마이그레이션할 때와 동일한 작업을 수행 해야 합니다 (Project Server 2016, Project Server 2019로 마이그레이션). Microsoft 솔루션 공급자에 게 문의 하 여 예상 비용을 해당 작업을 수행 하는 데 소요 되는 시간과 비용을 비교할 수 있습니다. 
    
## <a name="migrate-to-project-online"></a>Project Online으로 마이그레이션

Project Server 2010에서 Project Online으로 마이그레이션을 선택한 경우 다음을 수행 하 여 프로젝트 계획 데이터를 수동으로 마이그레이션할 수 있습니다.
  
1. Project Server 2010의 프로젝트 계획을에 저장 합니다. MPP 형식
    
2. Project Professional 2016, Project Professional 2019 또는 Project Online 데스크톱 클라이언트를 사용 하 여 각 .mpp 파일을 열고 저장 한 후 Project Online에 게시 합니다.
    
Project Online에서 PWA 구성을 수동으로 만들 수 있습니다 (예: 필요한 사용자 정의 필드 또는 enterprise 달력 새로 만들기). 이를 위해 Microsoft 솔루션 공급자도 도움이 될 수 있습니다.
  
주요 리소스:
  
|**리소스**|**설명**|
|:-----|:-----|
|[Project Online 시작](https://support.office.com/article/e3e5f64f-ada5-4f9d-a578-130b2d4e5f11) <br/> |Project Online을 설정 하 고 사용 하는 방법  <br/> |
|[Project Online 서비스 설명](https://go.microsoft.com/fwlink/p/?linkid=829088) <br/> |사용할 수 있는 다른 Project Online 계획에 대 한 정보입니다.  <br/> |
   
## <a name="migrate-to-a-newer-on-premises-version-of-project-server"></a>새로운 온-프레미스 버전의 Project Server로 마이그레이션

Project Online으로 마이그레이션하는 것이 최상의 가치와 사용자 환경을 얻을 수 있다고 확신 하지만 일부 조직에서는 온-프레미스 환경에서 프로젝트 데이터를 유지 해야 한다는 것도 이해 하 고 있습니다. 프로젝트 데이터를 온-프레미스로 유지 하도록 선택한 경우 Project Server 2010 환경을 Project Server 2013, Project Server 2016 또는 Project Server 2019로 마이그레이션할 수 있습니다.
  
Project Online으로 마이그레이션할 수 없는 경우 Project Server 2019로 마이그레이션하는 것이 좋습니다. Project Server 2019에는 이전 버전의 Project Server에 포함 된 모든 기능 및 개선 사항이 포함 되어 있으며 project online에서 사용할 수 있는 환경에 가장 근접 하 게 일치 합니다 (일부 기능은 Project Online 에서만 제공 됨).
  
각 마이그레이션을 완료 한 후에는 데이터를 확인 하 여 마이그레이션이 정상적으로 수행 되었는지 확인할 수 있습니다.
  
> [!NOTE]
> Project Server 2013로의 마이그레이션만을 고려 하는 경우 온-프레미스 솔루션 으로만 제한 되는 경우에는 몇 년간의 지원만 남아 있다는 점에 유의 해야 합니다. Project Server 2013 서비스 팩 2 지원 종료 날짜는 10/13/2023입니다. 지원 날짜 종료에 대 한 자세한 내용은 [Microsoft 제품 수명 주기 정책을](https://go.microsoft.com/fwlink/p/?linkid=842066)참조 하세요. 
  
### <a name="how-do-i-migrate-to-project-server-2019"></a>Project Server 2019로 마이그레이션하는 방법

Project Server 2010과 Project Server 2019 간의 아키텍처 차이로 인해 직접 마이그레이션 경로를 사용할 수 없습니다. 즉 project server 2019로 업그레이드할 때까지 Project server 2010 데이터를 project Server의 후속 버전으로 마이그레이션해야 합니다.
  
Project Server 2010을 Project Server 2019로 업그레이드 하려면 다음 단계를 수행 해야 합니다.
  
1. Project Server 2013로 마이그레이션합니다.
    
2. Project 2016 Server 2013의 마이그레이션
    
3. Project Server 2016에서 Project Server 2019로 마이그레이션
    
각 마이그레이션을 완료 한 후에는 데이터를 확인 하 여 마이그레이션이 정상적으로 수행 되었는지 확인할 수 있습니다.
  
    
### <a name="step-1-migrate-to-project-server-2013"></a>1 단계: Project Server 2013로 마이그레이션

Project Server 2010 데이터를 Project Server 2019로 마이그레이션하는 첫 번째 단계는 먼저 Project Server 2013로 마이그레이션해야 합니다. 
  
Project Server 2010에서 Project Server 2013로 업그레이드 하기 위해 수행 해야 하는 작업에 대 한 포괄적인 이해를 위해서는 [upgrade To Project server 2013로 업그레이드](https://go.microsoft.com/fwlink/p/?linkid=841822)를 참조 하세요. 
  
주요 리소스:
  
|||
|:-----|:-----|
|[Project Server 2013 업그레이드 프로세스 개요](https://go.microsoft.com/fwlink/p/?linkid=841822) <br/> |Project Server 2010에서 Project Server 2013로 업그레이드 하기 위해 수행 해야 하는 작업에 대 한 높은 수준의 이해를 알아봅니다.  <br/> |
|[Project Server 2013으로의 업그레이드 계획](https://go.microsoft.com/fwlink/p/?linkid=841823) <br/> |시스템 요구 사항을 포함 하 여 Project Server 2010에서 Project Server 2013로 업그레이드할 때 수행 해야 하는 계획 고려 사항을 확인 합니다.  <br/> |
   
[Project Server 2013 업그레이드의 새로운 기능](https://go.microsoft.com/fwlink/p/?linkid=841824) 에서는이 버전의 업그레이드에 대 한 몇 가지 중요 한 변경 사항에 대해 설명 합니다 (가장 주목할 만한 것은 다음과 같습니다. 
  
- Project Server 2013에 전체 업그레이드가 적용 되지 않습니다. Project Server 2010에서 Project Server 2013로 업그레이드할 때 유일 하 게 지원 되는 방법으로는 데이터베이스 연결 방법을 사용할 수 있습니다.
    
- 업그레이드 프로세스에서는 Project Server 2010 데이터를 Project Server 2013 형식으로 변환할 뿐만 아니라 4 개의 Project Server 2010 데이터베이스를 단일 Project Web App 데이터베이스에 통합 합니다.
    
- SharePoint Server 2013 및 Project Server 2013이 모두 이전 버전에서 클레임 기반 인증으로 변경 되었습니다. 클래식 인증을 사용 하는 경우 업그레이드할 때 고려해 야 합니다. 자세한 내용은 [SharePoint 2013에서 클래식 모드에서 클레임 기반 인증으로 마이그레이션을]( https://docs.microsoft.com/sharepoint/upgrade-and-update/migrate-from-classic-mode-to-claims-based-authentication-in-sharepoint-2013)참조 하세요.
    
주요 리소스:
  
- [Project Server 2013으로의 업그레이드 프로세스 개요](https://go.microsoft.com/fwlink/p/?linkid=841274)
    
- [데이터베이스 및 Project Web App 사이트 모음 업그레이드(Project Server 2013)](https://go.microsoft.com/fwlink/p/?linkid=841272)
    
- [Microsoft Project Server 업그레이드 프로세스 다이어그램](https://go.microsoft.com/fwlink/p/?linkid=841270)
    
- [편리한 데이터베이스 통합 인 Project Server 2010이 8 단계에서 2013로 마이그레이션](https://go.microsoft.com/fwlink/p/?linkid=841271)
    
### <a name="step-2-migrate-to-project-server-2016"></a>2 단계: Project Server 2016로 마이그레이션

Project Server 2013로 마이그레이션한 후 데이터가 제대로 마이그레이션 되었는지 확인 한 후에는 데이터를 Project Server 2016로 마이그레이션합니다.
  
Project Server 2013에서 Project Server 2016로 업그레이드 하기 위해 수행 해야 하는 작업에 대 한 포괄적인 이해를 위해서는 [upgrade To Project server 2016로 업그레이드](https://docs.microsoft.com/Project/upgrade-to-project-server-2016)를 참조 하세요.
  
주요 리소스:
  
|||
|:-----|:-----|
|[Project Server 2016 업그레이드 프로세스 개요](https://docs.microsoft.com/Project/overview-of-the-project-server-2016-upgrade-process) <br/> |Project Server 2013에서 Project Server 2016로 업그레이드 하기 위해 수행 해야 하는 작업에 대 한 높은 수준의 이해를 알아봅니다.  <br/> |
|[Project Server 2016으로의 업그레이드 계획](https://docs.microsoft.com/Project/plan-for-upgrade-to-project-server-2016) <br/> |Project Server 2013에서 Project Server 2016로 업그레이드할 때 수행 해야 하는 계획 고려 사항을 확인 합니다.  <br/> |
   
[Project Server 2016 업그레이드에 대해 알아야 할 사항은](https://docs.microsoft.com/project/plan-for-upgrade-to-project-server-2016#thingknow) 다음을 비롯 하 여이 버전으로 업그레이드할 때 중요 한 몇 가지 사항을 확인 해야 합니다. 
  
- Project server 2013 데이터를 마이그레이션할 Project Server 2016 환경을 만들 때 Project Server 2016 설치 파일이 SharePoint Server 2016에 포함 되어 있음을 확인 합니다. 자세한 내용은 [Deploy Project Server 2016](https://go.microsoft.com/fwlink/p/?linkid=841829)를 참조 하십시오.
    
- Project Server 2016에서는 자원 계획이 더 이상 사용 되지 않습니다. Project Server 2013 자원 계획은 Project Server 2016 및 Project Online에서 리소스 계약으로 마이그레이션됩니다. 자세한 내용은 [Overview (자원 계약](https://support.office.com/article/73eefb5a-81fe-42bf-980e-9532b1bdc870) )를 참조 하세요. 
    
### <a name="step-3-migrate-to-project-server-2019"></a>3 단계: Project Server 2019로 마이그레이션

Project Server 2016로 마이그레이션한 후 데이터가 제대로 마이그레이션 되었는지 확인 한 후에는 데이터를 Project Server 2019로 마이그레이션합니다.
  
Project Server 2016에서 Project Server 2019로 업그레이드 하기 위해 수행 해야 하는 작업에 대 한 포괄적인 이해를 위해서는 [upgrade To Project server 2019로 업그레이드](https://docs.microsoft.com/Project/upgrade-to-project-server-2016)를 참조 하세요.
  
주요 리소스:
  
|||
|:-----|:-----|
|[Project Server 2019 업그레이드 프로세스 개요](https://docs.microsoft.com/project/overview-of-the-project-server-2019-upgrade-process) <br/> |Project Server 2013에서 Project Server 2016로 업그레이드 하기 위해 수행 해야 하는 작업에 대 한 높은 수준의 이해를 알아봅니다.  <br/> |
|[Project Server 2019 업그레이드 계획](https://docs.microsoft.com/project/plan-for-upgrade-to-project-server-2019) <br/> |Project Server 2016에서 Project Server 2019로 업그레이드할 때 수행 해야 하는 계획 고려 사항을 확인 합니다.  <br/> |
   
[Project Server 2019 업그레이드에 대해 알아야 할 사항은](https://go.microsoft.com/fwlink/p/?linkid=841827) 다음을 비롯 하 여이 버전으로 업그레이드할 때 중요 한 몇 가지 사항을 확인 해야 합니다. 
  
- 업그레이드 프로세스에서는 Project Server 2016 데이터베이스의 데이터를 SharePoint Server 2019 콘텐츠 데이터베이스로 마이그레이션합니다.  Project Server 2019에서는 더 이상 SharePoint Server 팜에서 자체 Project Server 데이터베이스를 만들지 않습니다.

- 업그레이드 후에는 Project Web App의 여러 변경 사항에 대해 숙지 해야 합니다.  이러한 항목에 대 한 자세한 내용은 [Project Server 2019의 새로운 기능](https://docs.microsoft.com/project/what-s-new-for-it-pros-in-project-server-2019#PWAChanges)을 참조 하십시오.

  
기타 리소스:
  
- [Project Online 서비스 설명](https://go.microsoft.com/fwlink/p/?linkid=841280): project Server 2016 및 Project Online Premium에 포함 된 포트폴리오 관리 기능을 확인할 수 있습니다.
    
- [Microsoft Office Project 포트폴리오 서버 2010 마이그레이션 가이드](https://go.microsoft.com/fwlink/p/?linkid=841279)

## <a name="summary-of-options-for-office-2010-client-and-servers-and-windows-7"></a>Office 2010 클라이언트 및 서버 및 Windows 7의 옵션 요약

Office 2010 클라이언트 및 서버 및 Windows 7의 업그레이드, 마이그레이션 및 클라우드 간 옵션에 대 한 자세한 요약을 보려면 [지원 종료 포스터](./downloads/Office2010Windows7EndOfSupport.pdf)를 참조 하세요.

[![Office 2010 클라이언트 및 서버와 Windows 7에 대한 지원 종료 포스터 이미지](./media/upgrade-from-office-2010-servers-and-products/office2010-windows7-end-of-support.png)](./downloads/Office2010Windows7EndOfSupport.pdf)

이 한 페이지 포스터는 Office 2010 클라이언트 및 서버 제품 및 Windows 7의 지원 종료를 방지 하기 위해 수행할 수 있는 다양 한 경로를 이해 하는 빠른 방법 이며, Microsoft 365 Enterprise의 기본 설정 경로 및 옵션을 통해 강조 표시 됩니다.

또한이 포스터를 [다운로드](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/migration-microsoft-365-enterprise-workload/Office2010Windows7EndOfSupport.pdf) 하 여 letter, legal 또는 tabloid (11 x 17) 형식으로 인쇄할 수 있습니다.
   
## <a name="related-topics"></a>관련 항목

[SharePoint 2010에서 업그레이드](upgrade-from-sharepoint-2010.md)
  
[Office 2010 서버 및 클라이언트에서 업그레이드](upgrade-from-office-2010-servers-and-products.md)
  

