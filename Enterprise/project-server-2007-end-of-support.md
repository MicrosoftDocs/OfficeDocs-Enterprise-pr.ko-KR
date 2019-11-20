---
title: Project Server 2007 지원 종료 로드맵
ms.author: efrene
author: efrene
manager: laurawi
ms.date: 1/31/2018
audience: ITPro
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
ms.assetid: d379018f-72b7-4284-b40a-6c23c8ae38fe
description: 2017 년 10 월 10 일에 Project Server 2007, Project 포트폴리오 서버 및 프로젝트 2007에 대 한 지원이 종료 되었습니다. 이 문서를 사용 하 여 지금 업그레이드를 계획 합니다.
ms.openlocfilehash: c21d9d1c2539f66587243f04d4d874649d6bf460
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2019
ms.locfileid: "38746241"
---
# <a name="project-server-2007-end-of-support-roadmap"></a>Project Server 2007 지원 종료 로드맵

*이 문서는 Office 365 Enterprise 및 Microsoft 365 Enterprise에 모두 적용 됩니다.*

2017의 Office 2007 서버 및 응용 프로그램에 대 한 지원이 종료 되었으며 마이그레이션 계획을 고려해 야 합니다. 현재 Project Server 2007을 사용 하는 경우에는 it 및 기타 관련 제품에 다음과 같은 지원 종료 날짜가 포함 되어 있습니다.
  
|**제품**|**지원 종료 날짜**|
|:-----|:-----|
|Project Server 2007  <br/> |2017년 10월 10일  <br/> |
|프로젝트 포트폴리오 서버 2007  <br/> |2017년 10월 10일  <br/> |
|Project 2007 Standard  <br/> |2017년 10월 10일  <br/> |
|Project 2007 Professional  <br/> |2017년 10월 10일  <br/> |
   
만료 되는 Office 2007 서버에 대 한 자세한 내용은 [Upgrade From office 2007 server and client products](upgrade-from-office-2007-servers-and-products.md)을 참조 하십시오.
  
## <a name="what-does-end-of-support-mean"></a>지원이 끝나는 것은 무엇을 의미 하나요?

Project Server에는 거의 모든 Microsoft 제품과 마찬가지로 새로운 기능, 버그 수정, 보안 픽스 등을 제공 하는 지원 주기가 있습니다. 일반적으로이 수명 주기는 제품 초기 릴리스 날짜 로부터 10 년 동안 지속 되며이 주기의 끝은 제품의 지원 종료 라고 합니다. Project Server 2007에서는 Microsoft가 2017 년 10 월 10 일에 대 한 지원 종료에 도달 했으므로 더 이상 다음이 제공 되지 않습니다.
  
- 발생할 수 있는 문제에 대 한 기술 지원
    
- 검색 된 문제와 서버의 안정성 및 유용성에 영향을 줄 수 있는 문제에 대 한 버그 수정
    
- 검색 되어 서버에서 보안 위반에 취약 해질 수 있는 취약성에 대 한 보안 수정
    
- 표준 시간대 업데이트
    
이 날짜 후에는 Project Server 2007의 설치가 계속 실행 됩니다. 그러나 위에 나열 된 변경 사항으로 인해 가능한 한 빨리 Project Server 2007에서 마이그레이션하는 것이 좋습니다.
  
## <a name="what-are-my-options"></a>내 옵션 이란?

Project Server 2007을 사용 하는 경우 다음과 같은 마이그레이션 옵션을 검토 해야 합니다.
  
- Project Online으로 마이그레이션
    
- 새 온-프레미스 버전의 Project Server로 마이그레이션 (특히 Project Server 2016)
    
|**Project Online으로 마이그레이션하는 이유**|**Project Server 2016로 마이그레이션하는 이유**|
|:-----|:-----|
| 모바일 사용자가 있는 경우  <br/>  마이그레이션 비용은 중요 한 관심사 (예를 들면 하드웨어, 소프트웨어, 시간 및 구현 노력 등)입니다.  <br/>  마이그레이션 후 내 환경을 유지 관리 하는 비용은 대규모 관심사 (예: 자동 업데이트, 보장 된 가동 시간 등)입니다.  <br/> | 비즈니스 규칙 클라우드에서 내 비즈니스를 운영 하는 것을 제한 합니다.  <br/>  내 환경에 대 한 업데이트를 제어 해야 합니다.  <br/> |
   
> [!NOTE]
> Office 2007 서버에서 이동 하는 방법에 대 한 자세한 내용은 [office 2007 서버 및 클라이언트에서 업그레이드 하는 데 도움이](upgrade-from-office-2007-servers-and-products.md)되는 리소스를 참조 하십시오. Project Server 및 Project Online에서는 동일한 자원 그룹을 공유할 수 없으므로 Project Server에서는 하이브리드 구성을 지원 하지 않습니다. 
  
## <a name="important-considerations-you-need-to-make-when-planning-to-migrate-from-project-server-2007"></a>Project Server 2007에서 마이그레이션을 계획할 때 수행 해야 하는 중요 고려 사항

Project Server 2007에서 마이그레이션을 계획할 때 고려해 야 할 사항은 다음과 같습니다.
  
- Project Server 2007에서 **Microsoft 파트너가 업그레이드 하는 데 도움이 되는 도움말** 을 확인 하는 것은 어려울 수 있으며 준비 및 계획이 많이 수행 되어야 합니다. 이는 설정 하는 것이 아니라 원래 Project Server 2007을 구성 하는 것이 어려운 경우에 특히 유용 합니다. 다행히 Microsoft 파트너는 Project Server 2016로 마이그레이션을 계획 하 든, Project Online으로 마이그레이션할 지에 관계 없이이 작업을 수행할 수 있는 사용자를 설정할 수도 있습니다. Microsoft 파트너 [센터](https://go.microsoft.com/fwlink/p/?linkid=841249)에서 마이그레이션에 도움을 받을 수 있습니다. *골드 프로젝트 및 포트폴리오 관리* 용어를 검색 하 여 Project에 대 한 전문 지식을 갖춘 모든 Microsoft 파트너 목록을 가져올 수 있습니다. 
    
- **사용자 지정 계획** -project server 2016로 마이그레이션하거나 project Online으로 마이그레이션하는 경우 프로젝트 서버 2007 환경에서 작업 하는 많은 사용자 지정 내용이 작동 하지 않을 수 있다는 점을 염두에 두어야 합니다. 버전 간 Project Server 아키텍처에는 큰 차이점이 있으며, 새 버전에서 작동 하도록 지원 되는 필수 운영 체제, 데이터베이스 서버 및 클라이언트 웹 브라우저에는 차이가 있습니다. 새 환경에서 필요에 따라 사용자 지정 내용을 테스트 하거나 다시 작성 하는 방법에 대 한 계획을 수립 합니다. 업그레이드를 계획할 때는 앞으로 이동할 때 특정 사용자 지정이 실제로 필요한 지를 확인 하는 것도 좋은 기회입니다. [Upgrade for current 사용자 지정 계획 만들기 2013](https://go.microsoft.com/fwlink/p/?linkid=842061) 에서는 업그레이드 시 현재 사용자 지정 내용에 대 한 평가 및 계획에 대 한 몇 가지 일반적인 정보를 제공 합니다. 
    
- **시간 및** 인 업그레이드 계획, 실행 및 테스트에는 특히 Project Server 2016로 업그레이드 하는 경우의 시간과 노력이 많이 소요 됩니다. 예를 들어 Project Server 2007에서 Project Server 2016로 마이그레이션하는 경우 먼저 Project Server 2007에서 Project Server 2010로 마이그레이션한 다음 데이터를 확인 한 다음 각 후속 버전으로 마이그레이션하는 것과 동일한 작업을 수행 해야 합니다. Microsoft 파트너에 게 문의 하 여 비용을 해당 작업을 수행 하는 데 소요 되는 시간과 비용을 비교할 수 있습니다. 
    
## <a name="migrate-to-project-online"></a>Project Online으로 마이그레이션

Project Server 2007에서 Project Online으로 마이그레이션을 선택한 경우 다음을 수행 하 여 프로젝트 계획 데이터를 수동으로 마이그레이션할 수 있습니다.
  
1. Project Server 2003의 프로젝트 계획을에 저장 합니다. MPP 형식
    
2. Project Professional 2013, Project Professional 2016 또는 Project Online 데스크톱 클라이언트를 사용 하 여 각 .mpp 파일을 열고 저장 한 후 Project Online에 게시 합니다.
    
Project Online에서 PWA 구성을 수동으로 만들 수 있습니다 (예: 필요한 사용자 정의 필드 또는 enterprise 달력 새로 만들기). Microsoft 파트너도이를 지원할 수 있습니다.
  
주요 리소스:
  
|**리소스**|**설명**|
|:-----|:-----|
|[Project Online 시작](https://support.office.com/article/e3e5f64f-ada5-4f9d-a578-130b2d4e5f11) <br/> |Project Online을 설정 하 고 사용 하는 방법  <br/> |
|[Project Online 서비스 설명](https://go.microsoft.com/fwlink/p/?linkid=829088) <br/> |사용할 수 있는 다른 Project Online 계획에 대 한 정보입니다.  <br/> |
   
## <a name="migrate-to-a-newer-on-premises-version-of-project-server"></a>새로운 온-프레미스 버전의 Project Server로 마이그레이션

Project Online으로 마이그레이션하는 것이 최상의 가치와 사용자 환경을 얻을 수 있다고 확신 하지만 일부 조직에서는 온-프레미스 환경에서 프로젝트 데이터를 유지 해야 한다는 것도 이해 하 고 있습니다. 프로젝트 데이터를 온-프레미스로 유지 하도록 선택한 경우 Project Server 2007 환경을 Project Server 2010, Project Server 2013 또는 Project Server 2016로 마이그레이션할 수 있습니다.
  
Project Online으로 마이그레이션할 수 없는 경우 Project Server 2016로 마이그레이션하는 것이 좋습니다. Project Server 2016에서는 이전 버전의 Project Server에 포함 된 모든 기능과 향상 된 기능을 비롯 하 여 project online에서 사용할 수 있는 환경과 가장 밀접 하 게 일치 하며 일부 기능은 Project Online 에서만 제공 됩니다.
  
각 마이그레이션을 완료 한 후에는 데이터를 확인 하 여 마이그레이션이 정상적으로 수행 되었는지 확인할 수 있습니다.
  
> [!NOTE]
> Project Server 2010로의 마이그레이션만을 고려 하는 경우 온-프레미스 솔루션 으로만 제한 되는 경우에는 몇 년간의 지원만 남아 있다는 점에 유의 해야 합니다. Project Server 2010 서비스 팩 2 지원 종료 날짜는 10/13/2020입니다. 지원 날짜 종료에 대 한 자세한 내용은 [Microsoft 제품 수명 주기 정책을](https://go.microsoft.com/fwlink/p/?linkid=842066)참조 하세요. 
  
### <a name="how-do-i-migrate-to-project-server-2016"></a>Project Server 2016로 마이그레이션하는 방법

Project Server 2007과 Project Server 2016 간의 아키텍처 차이로 인해 직접 마이그레이션 경로를 사용할 수 없습니다. 즉 project server 2016로 업그레이드할 때까지 Project server 2007 데이터를 project Server의 후속 버전으로 마이그레이션해야 합니다.
  
Project Server 2016로 업그레이드 하려면 다음을 수행 해야 합니다.
  
1. 1 단계: Project Server 2007에서 Project Server 2010로 마이그레이션
    
2. 2 단계: 프로젝트 서버 2010에서 Project Server 2013로 마이그레이션
    
3. 3 단계: Project Server 2013에서 Project Server 2016로 마이그레이션
    
각 마이그레이션을 완료 한 후에는 데이터를 확인 하 여 마이그레이션이 정상적으로 수행 되었는지 확인할 수 있습니다.
  
### <a name="step-1-migrate-from-project-server-2007-to-project-server-2010"></a>1 단계: Project Server 2007에서 Project Server 2010로 마이그레이션

Project Server 2007에서 Project Server 2010로 업그레이드 하기 위해 수행 해야 하는 작업에 대 한 포괄적인 이해를 위해서는 TechNet에서 설정 된 [Project server 2010 콘텐츠 업그레이드](https://go.microsoft.com/fwlink/p/?linkid=841812) 를 참조 하세요. 
  
주요 리소스:
  
|**리소스**|**설명**|
|:-----|:-----|
|[Project Server 2010 업그레이드 개요](https://go.microsoft.com/fwlink/p/?linkid=841813) <br/> |Project Server 2007에서 Project Server 2010로 업그레이드 하기 위해 수행 해야 하는 작업에 대 한 높은 수준의 이해를 알아봅니다.  <br/> |
|[Project Server 2010으로의 업그레이드 계획](https://go.microsoft.com/fwlink/p/?linkid=841815) <br/> |시스템 요구 사항을 포함 하 여 Project Server 2007에서 Project Server 2010로 업그레이드할 때 수행 해야 하는 계획 고려 사항을 확인 합니다.  <br/> |
   
#### <a name="how-do-i-upgrade"></a>업그레이드 방법

업그레이드 방법에 대 한 자세한 내용은 upgrade [To Project Server 2010](https://go.microsoft.com/fwlink/p/?linkid=841812) content set에서 찾을 수 있지만 업그레이드 하는 데 사용할 수 있는 두 가지 방법은 다음과 같습니다. 
  
- **데이터베이스 연결 업그레이드:** 이 메서드는 구성 설정이 아닌 환경의 콘텐츠만 업그레이드 합니다. 32 비트 서버 운영 체제만 지 원하는 하드웨어에 배포 된 Office Project Server 2007에서 업그레이드 하는 경우에 필요 합니다. 데이터베이스 연결 업그레이드 방법에는 다음과 같은 두 가지 유형이 있습니다. 
    
  - **데이터베이스 연결 전체 업그레이드** -Office project Server 2007 데이터베이스에 저장 된 프로젝트 데이터와 SharePoint 콘텐츠 데이터베이스에 저장 되어 있는 Microsoft Project Web APP (PWA) 사이트 데이터를 마이그레이션합니다. 
    
  - **데이터베이스 연결 핵심 업그레이드** -project Server 데이터베이스에 저장 된 프로젝트 데이터만 마이그레이션합니다. 
    
- **전체 업그레이드**: 팜의 구성 데이터와 팜의 모든 콘텐츠가 기존 하드웨어의 고정 순서로 업그레이드 됩니다. 전체 업그레이드 프로세스를 시작 하면 설치가 완료 될 때까지 모든 팜이 오프 라인 상태가 되 고 웹 사이트와 Microsoft Project Web App 사이트를 사용할 수 없게 되 고 설치 프로그램이 서버를 다시 시작 합니다. 전체 업그레이드를 시작한 후에는 업그레이드를 일시 중지하거나 이전 버전으로 롤백할 수 없습니다. 프로덕션 환경의 미러링된 이미지를 만들고 프로덕션 환경이 아닌이 환경에 대 한 전체 업그레이드를 수행 하는 것이 좋습니다. 
    
추가 리소스:
  
- [Microsoft Project Server 2010 업그레이드를 위한 수퍼 흐름](https://go.microsoft.com/fwlink/p/?linkid=841277)
    
- [Project Server 2007에서 Project Server 2010로 마이그레이션](https://go.microsoft.com/fwlink/p/?linkid=841278)
    
- [Project Web App 웹 파트 업그레이드 고려 사항](https://go.microsoft.com/fwlink/p/?linkid=841276)
    
- [Project SDK (소프트웨어 개발 키트)](https://go.microsoft.com/fwlink/p/?linkid=841275)
    
### <a name="step-2-migrate-to-project-server-2013"></a>2 단계: Project Server 2013로 마이그레이션

Project Server 2010로 마이그레이션한 후 데이터가 제대로 마이그레이션 되었는지 확인 한 후에는 데이터를 Project Server 2013로 마이그레이션합니다.
  
Project Server 2010에서 Project Server 2013로 업그레이드 하기 위해 수행 해야 하는 작업에 대 한 포괄적인 이해를 위해서는 TechNet에서 설정 된 [Project server 2013 콘텐츠 업그레이드](https://go.microsoft.com/fwlink/p/?linkid=841822) 를 참조 하세요. 
  
주요 리소스:
  
|**리소스**|**설명**|
|:-----|:-----|
|[Project Server 2013 업그레이드 프로세스 개요](https://go.microsoft.com/fwlink/p/?linkid=841822) <br/> |Project Server 2010에서 Project Server 2013로 업그레이드 하기 위해 수행 해야 하는 작업에 대 한 높은 수준의 이해를 알아봅니다.  <br/> |
|[Project Server 2013으로의 업그레이드 계획](https://go.microsoft.com/fwlink/p/?linkid=841823) <br/> |시스템 요구 사항을 포함 하 여 Project Server 2010에서 Project Server 2013로 업그레이드할 때 수행 해야 하는 계획 고려 사항을 확인 합니다.  <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>이 버전으로 업그레이드 하는 방법에 대해 알아야 할 사항

[Project Server 2013 업그레이드의 새로운 기능](https://go.microsoft.com/fwlink/p/?linkid=841824) 에서는이 버전의 업그레이드에 대 한 몇 가지 중요 한 변경 사항에 대해 설명 합니다 (가장 주목할 만한 것은 다음과 같습니다. 
  
- Project Server 2013에 전체 업그레이드가 적용 되지 않습니다. Project Server 2010에서 Project Server 2013로 업그레이드할 때 유일 하 게 지원 되는 방법으로는 데이터베이스 연결 방법을 사용할 수 있습니다.
    
- 업그레이드 프로세스에서는 Project Server 2010 데이터를 Project Server 2013 형식으로 변환할 뿐만 아니라 4 개의 Project Server 2010 데이터베이스를 단일 Project Web App 데이터베이스에 통합 합니다.
    
- SharePoint Server 2013 및 Project Server 2013이 모두 이전 버전에서 클레임 기반 인증으로 변경 되었습니다. 클래식 인증을 사용 하는 경우 업그레이드할 때 고려해 야 합니다. 자세한 내용은 [SharePoint 2013에서 클래식 모드에서 클레임 기반 인증으로 마이그레이션을](https://go.microsoft.com/fwlink/p/?linkid=841825)참조 하세요.
    
추가 리소스:
  
- [Project Server 2013으로의 업그레이드 프로세스 개요](https://go.microsoft.com/fwlink/p/?linkid=841274)
    
- [데이터베이스 및 Project Web App 사이트 모음 업그레이드(Project Server 2013)](https://go.microsoft.com/fwlink/p/?linkid=841272)
    
- [Microsoft Project Server 업그레이드 프로세스 다이어그램](https://go.microsoft.com/fwlink/p/?linkid=841270)
    
- [편리한 데이터베이스 통합 인 Project Server 2010이 8 단계에서 2013로 마이그레이션](https://go.microsoft.com/fwlink/p/?linkid=841271)
    
### <a name="step-3-migrate-to-project-server-2016"></a>3 단계: Project Server 2016로 마이그레이션

Project Server 2013로 마이그레이션한 후 데이터가 제대로 마이그레이션 되었는지 확인 한 후에는 데이터를 Project Server 2016로 마이그레이션합니다.
  
Project Server 2013에서 Project Server 2016로 업그레이드 하기 위해 수행 해야 하는 작업에 대 한 포괄적인 이해를 위해서는 TechNet에서 설정 된 Project Server 2016 콘텐츠 업그레이드를 참조 하세요.
  
주요 리소스:
  
|**리소스**|**설명**|
|:-----|:-----|
|[Project Server 2016 업그레이드 프로세스 개요](https://go.microsoft.com/fwlink/p/?linkid=841260) <br/> |Project Server 2013에서 Project Server 2016로 업그레이드 하기 위해 수행 해야 하는 작업에 대 한 높은 수준의 이해를 알아봅니다.  <br/> |
|[Project Server 2016으로의 업그레이드 계획](https://go.microsoft.com/fwlink/p/?linkid=841826) <br/> |Project Server 2013에서 Project Server 2016로 업그레이드할 때 수행 해야 하는 계획 고려 사항 (을 포함)을 확인 하십시오.  <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>이 버전으로 업그레이드 하는 방법에 대해 알아야 할 사항

[Project Server 2016 업그레이드에 대해 알아야 할 사항](https://go.microsoft.com/fwlink/p/?linkid=841827) 에는이 버전의 업그레이드에 대 한 몇 가지 중요 한 변경 사항이 포함 되어 있습니다. 
  
- Project server 2013 데이터를 마이그레이션할 Project Server 2016 환경을 만들 때 Project Server 2016 설치 파일이 SharePoint Server 2016에 포함 되어 있음을 확인 합니다. 자세한 내용은 [Deploy Project Server 2016](https://go.microsoft.com/fwlink/p/?linkid=841829)를 참조 하십시오.
    
- Project Server 2016에서는 자원 계획이 더 이상 사용 되지 않습니다. Project Server 2013 자원 계획은 Project Server 2016 및 Project Online에서 리소스 계약으로 마이그레이션됩니다. 자세한 내용은 [Overview (자원 계약](https://support.office.com/article/73eefb5a-81fe-42bf-980e-9532b1bdc870) )를 참조 하세요. 
    
## <a name="migrate-from-portfolio-server-2007"></a>포트폴리오 서버 2007에서 마이그레이션

Project 포트폴리오 서버 2007는 포트폴리오 전략, 우선 순위 지정 및 최적화를 위해 Project Server 2007에서 사용 되었습니다. 이 버전 이후에는 추가 프로젝트 포트폴리오 서버 버전을 만들지 않았습니다. 그러나 포트폴리오 관리 기능은 Project Server 2016과 Project Online Premium 버전에서 모두 사용할 수 있습니다. Project 포트폴리오 서버 2007의 데이터는로 마이그레이션할 수 없습니다. 비즈니스 드라이버와 같은 데이터를 다시 만들어야 합니다.
  
기타 리소스:
  
- [Project Online 서비스 설명](https://go.microsoft.com/fwlink/p/?linkid=841280): project Server 2016 및 Project Online Premium에 포함 된 포트폴리오 관리 기능을 확인할 수 있습니다.
    
- [Microsoft Office Project 포트폴리오 서버 2007 마이그레이션 가이드](https://go.microsoft.com/fwlink/p/?linkid=841279)
    
## <a name="related-topics"></a>관련 항목

[SharePoint Server 2007 지원 로드맵 종료](sharepoint-2007-end-of-support.md)
  
[Office 2007 서버 및 클라이언트에서 업그레이드 하는 데 도움이 되는 리소스](upgrade-from-office-2007-servers-and-products.md)
  

