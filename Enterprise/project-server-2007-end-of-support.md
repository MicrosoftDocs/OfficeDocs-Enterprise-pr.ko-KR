---
title: Project Server 2007 지원 종료 로드맵
ms.author: efrene
author: efrene
manager: laurawi
ms.date: 1/31/2018
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
ms.assetid: d379018f-72b7-4284-b40a-6c23c8ae38fe
description: 2017 년 10 월 10 년에서 Project Server 2007, Project Portfolio Server 및 Project 2007에 대 한 지원을 끝냈습니다. 이 문서를 사용 하 여 지금 업그레이드를 계획 합니다.
ms.openlocfilehash: 5b2fb194d4819b5427cb2844a5189b2b03753800
ms.sourcegitcommit: a9c84d02e94c99ff6b1099b4a9ae695be08210e2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/25/2018
ms.locfileid: "21169900"
---
# <a name="project-server-2007-end-of-support-roadmap"></a>Project Server 2007 지원 종료 로드맵

2017에서 Office 2007 서버 및 응용 프로그램에 대 한 종료 되는 지원 하 고 마이그레이션에 대 한 계획을 고려해 야 합니다. Project Server 2007을 사용 중인 경우에 없으며 이러한 기타 관련된 제품 들 수 있는 다음과 같은 지원의 끝 날짜 note:
  
|**제품**|**지원 날짜의 끝**|
|:-----|:-----|
|Project Server 2007  <br/> |2017년 10월 10일  <br/> |
|Project Portfolio Server 2007  <br/> |2017년 10월 10일  <br/> |
|Project 2007 표준  <br/> |2017년 10월 10일  <br/> |
|Project 2007 Professional  <br/> |2017년 10월 10일  <br/> |
   
퇴직 도달 하는 Office 2007 서버에 대 한 자세한 내용은 [2007 Office 서버 및 클라이언트 제품에서 업그레이드](upgrade-from-office-2007-servers-and-products.md)를 참조 하십시오.
  
## <a name="what-does-end-of-support-mean"></a>지원 의미의 역할 끝 무엇입니까?

Project Server 같은 거의 모든 Microsoft 제품의 새로운 기능, 버그 수정, 보안 픽스 등에 제공 하는 동안 지원 주기가 있습니다. 이 수명 주기는 일반적으로 제품의 초기 릴리스 날짜 로부터 10 년 동안 지속 하 고이 주기 끝이 제품의 지원 종료 라고 합니다. Project Server 2007에 2017 년 10 월 10 년에서 지원의 끝에 도달 하기 때문에 Microsoft 제공 하지 않습니다.
  
- 발생할 수 있는 문제에 대 한 기술 지원 합니다.
    
- 버그 검색 되는 및 안정성과 사용 가능성 서버의 영향을 줄 수 있는 문제를 해결 합니다.
    
- 검색 되는 하 고 서버를 공격에 취약 한 보안 위반에 만들 수 있는 취약점에 대 한 보안은 수정 합니다.
    
- 표준 시간대를 업데이트합니다.
    
Project Server 2007 설치 계속이 날짜 이후에 실행 됩니다. 그러나 위에 나열 된 변경으로 인해 좋습니다 마이그레이션하는 Project Server 2007에서 가능한 한 빨리.
  
## <a name="what-are-my-options"></a>내 옵션은 무엇입니까?

Project Server 2007을 사용 하는 경우에 마이그레이션 옵션을 사용 하 여 탐색 해야.
  
- 프로젝트를 온라인으로 마이그레이션
    
- 새로운 온-프레미스 버전의 Project Server (가능 하면 Project Server 2016)를 마이그레이션하십시오.
    
|**Project Online으로 마이그레이션 선호 하는 이유**|**Project Server 2016 마이그레이션하려면 선호 하는 이유**|
|:-----|:-----|
| 모바일 사용자에 게 했습니다.  <br/>  비용을 마이그레이션할 것은 큰 문제가 (하드웨어, 소프트웨어, 시간 및 등을 구현 하는 수단입니다.)입니다.  <br/>  마이그레이션 후 현재 환경에 맞게 유지 관리 비용의 큰 문제 (예, 자동 업데이트를 가동 시간 등을 보장 합니다.)에 있습니다.  <br/> | 비즈니스 규칙 클라우드에서 내 비즈니스 운영에서 나에 게 제한 합니다.  <br/>  I 업데이트 제어 환경에 맞게 해야합니다.  <br/> |
   
> [!NOTE]
> Office 2007 서버에서 이동 하기 위한 옵션에 대 한 자세한 내용은 [2007 서버와 클라이언트가 Office에서 업그레이드 하는데 도움이 되는 리소스](upgrade-from-office-2007-servers-and-products.md)를 참조 합니다. Note Project Server Project Server 이후 하이브리드 구성을 지원 하지 않는 하 고 Project Online 동일한 자원 그룹을 공유할 수 없습니다. 
  
## <a name="important-considerations-you-need-to-make-when-planning-to-migrate-from-project-server-2007"></a>Project Server 2007에서 마이그레이션을 계획할 때 수행 해야하는 중요 한 고려 사항

Project Server 2007에서 마이그레이션을 계획할 때는 다음 사항을 고려 해야 합니다.
  
- **Microsoft 파트너에서 제공 하는 도움말** -Project Server 2007에서 업그레이드 하는 어려울 수 및 준비 및 계획을 많이 필요 합니다. 설치 하 고 Project Server 2007을 처음 구성할 하나 없었던 경우 특히 어려운 일 수 있습니다. 다행히, Project Server 2016 또는 Project Online으로 마이그레이션하는 방법에 계획 여부 생활,이 작업을 수행 하는 Microsoft 파트너를 만드는데 사용할 수 있습니다. [Microsoft 파트너 센터](https://go.microsoft.com/fwlink/p/?linkid=841249)에서 마이그레이션을 위해 Microsoft 파트너를 검색할 수 있습니다. *Gold 프로젝트 및 포트폴리오 관리* 용어를 검색 하 여 프로젝트에 대 한 전문 지식와 모든 Microsoft 파트너 목록을를 의뢰할 수 있습니다. 
    
- **사용자 지정에 대 한 계획** -는 다양 한 Project Server 2007 환경에서 작업을 한 사용자 지정 작동 하지 않을 수 Project Server 2016 또는 Project Online으로 마이그레이션하는 경우 유의 해야 합니다. 큰 차이가 Project Server 아키텍처 버전으로 필요한 운영 체제, 데이터베이스 서버 및 최신 버전과 함께 사용 하도록 지원 되는 클라이언트 웹 브라우저를 있습니다. 테스트 또는 새 환경에서 필요에 따라 사용자 지정을 다시 작성 하는 방법에 대 한 전체에서 요금제에 가입한 상태입니다. 업그레이드에 대 한 계획 앞으로 이동할 때 특정 사용자 지정 정말 필요한 경우를 확인 하려면 좋은 기회 됩니다. [SharePoint 2013으로 업그레이드 하는 동안 현재 사용자 지정에 대 한 적절 한 계획](https://go.microsoft.com/fwlink/p/?linkid=842061) 을 평가 하 고 업그레이드 시 현재 사용자 지정에 대 한 계획 하는 방법에 대 한 일부 뛰어난 일반 정보를 있습니다. 
    
- **시간 및 인 내** -업그레이드를 계획 하 고, 실행 및 테스트는 Project Server 2016으로 업그레이드 하는 경우에 특히 시간과 노력을 많이 수행 됩니다. 예 경우 Project Server 2016로 Project Server 2007에서 마이그레이션하는, Project Server 2007에서 Project Server 2010으로 마이그레이션 한 후, 데이터를 확인 하려면 먼저를 다음 각 이후 버전으로 마이그레이션할 때 동일한 작업을 수행 합니다. 얼마나 오래 걸리는 하 고, 해당 하 고 비용 기능에서 추정과 비용을 비교 하려면 Microsoft 파트너 수도 있습니다. 
    
## <a name="migrate-to-project-online"></a>프로젝트를 온라인으로 마이그레이션

Project online Project Server 2007에서 마이그레이션하는 경우에 수동으로 프로젝트 계획 데이터를 마이그레이션하려면 다음을 수행할 수 있습니다.
  
1. Project Server 2003에서 프로젝트 계획을 저장 합니다. MPP 형식입니다.
    
2. Project Professional 2013, Project Professional 2016 또는 프로젝트 온라인 데스크톱 클라이언트를 사용 하 여 각.mpp 파일을 열고 하 고을 저장 하 고 Project Online에 게시 합니다.
    
Project Online에서 PWA 구성을 수동으로 만들 수 있습니다 (예: 필요한 사용자 정의 필드나 enterprise 달력 다시). Microsoft 파트너 대체 되는 도움말 수 있습니다.
  
주요 리소스:
  
|**리소스**|**설명**|
|:-----|:-----|
|[Project Online 시작 하기](https://support.office.com/article/e3e5f64f-ada5-4f9d-a578-130b2d4e5f11) <br/> |설치 하 고 Project Online을 사용 하는 방법입니다.  <br/> |
|[Project Online 서비스 설명](https://go.microsoft.com/fwlink/p/?linkid=829088) <br/> |사용할 수 있는 다른 온라인 프로젝트 계획에 대 한 정보를 제공 합니다.  <br/> |
   
## <a name="migrate-to-a-newer-on-premises-version-of-project-server"></a>새로운 온-프레미스 버전의 Project Server를 마이그레이션하십시오.

Project Online으로 마이그레이션하는 방법으로 최상의 값 및 사용자 경험을 얻을 수 있는을 강력 하 게 광고, 하는 동안는 또한 이해 일부 조직에서는 온-프레미스 환경에서 프로젝트 데이터를 유지 해야 합니다. 프로젝트 데이터에서 온-프레미스 유지 하려는 경우에 Project Server 2010, Project Server 2013 또는 Project Server 2016 Project Server 2007 환경을 마이그레이션할 수 있습니다.
  
Project Online을 마이그레이션할 수 없는 경우 Project Server 2016를 마이그레이션하는 것이 좋습니다. 모든 기능 및 고급 기능을 통해 Project Server의 이전 버전에 포함 된 project Server 2016를 포함 하 고 (Project Online에 사용할 수 있는 일부 기능) 있지만 Project Online을 사용할 수 있는 환경에서 가장 근접 하 게 일치 합니다.
  
각 마이그레이션을 완료 한 후에 성공적으로 마이그레이션 되었는지 확인 하려면 데이터를 확인 해야 합니다.
  
> [!NOTE]
> 온-프레미스 솔루션으로 제한 하는 경우 Project Server 2010으로 마이그레이션만 고려 하는 경우에 지원 왼쪽의 더 많은 몇 년만에 있는지 확인 하는 것이 중요 합니다. Project Server 2010 서비스 팩 2 지원 날짜의 끝이 10/13/2020 합니다. 지원 날짜의 끝에 대 한 자세한 내용은 [Microsoft 제품 수명 주기 정책](https://go.microsoft.com/fwlink/p/?linkid=842066)을 참조 하십시오. 
  
### <a name="how-do-i-migrate-to-project-server-2016"></a>Project Server 2016를 마이그레이션하려면 어떻게 해야 합니까?

Project Server 2007 및 Project Server 2016 아키텍처 차이점 직접 마이그레이션 경로 방지 합니다. 즉, Project Server 2016로 업그레이드할 때까지 다음 연속 된 버전의 Project Server에 Project Server 2007 데이터를 마이그레이션할 해야 합니다.
  
Project Server 2016로 업그레이드 하려면 다음 작업을 수행 해야 합니다.
  
1. 1 단계: Project Server 2010으로 Project Server 2007에서에서 마이그레이션하십시오.
    
2. 2 단계: Project Server 2013으로 프로젝트 서비스 2010에서에서 마이그레이션하십시오.
    
3. 3 단계: 서버 2016 Project에 Project Server 2013에서에서 마이그레이션하십시오.
    
각 마이그레이션을 완료 한 후에 성공적으로 마이그레이션 되었는지 확인 하려면 데이터를 확인 해야 합니다.
  
### <a name="step-1-migrate-from-project-server-2007-to-project-server-2010"></a>1 단계: Project Server 2010으로 Project Server 2007에서 마이그레이션

Project Server 2007에서 Project Server 2010으로 업그레이드를 수행 하는데 필요한의 포괄적인 이해 하십시오 TechNet의 [Project Server 2010으로 업그레이드](https://go.microsoft.com/fwlink/p/?linkid=841812) 콘텐츠 설정을 참조 하십시오. 
  
주요 리소스:
  
|**리소스**|**설명**|
|:-----|:-----|
|[Project Server 2010 업그레이드 개요](https://go.microsoft.com/fwlink/p/?linkid=841813) <br/> |높은 수준의 파악 Project Server 2007에서 Project Server 2010으로 업그레이드 하기 위해 수행 해야 합니다.  <br/> |
|[Project Server 2010으로의 업그레이드 계획](https://go.microsoft.com/fwlink/p/?linkid=841815) <br/> |계획 고려 사항 Project Server 2010으로 시스템 요구 사항을 포함 하 여 Project Server 2007에서 업그레이드 하는 경우를 결정 해야 하는 방법을 살펴봅니다.  <br/> |
   
#### <a name="how-do-i-upgrade"></a>업그레이드 방법

[Project Server 2010으로의 업그레이드](https://go.microsoft.com/fwlink/p/?linkid=841812) 콘텐츠 집합에서 업그레이드 하는 방법에 대 한 세부 정보를 확인할 수 있습니다, 하는 동안에 업그레이드를 사용할 수 있는 두 고유한 방법 이해 하는 것이 중요: 
  
- **데이터베이스 연결 업그레이드:** 이 메서드는만 환경과 구성 설정에 대 한 콘텐츠를 업그레이드합니다. 32 비트 서버 운영 체제를 지원 하는 하드웨어에 배포 된 Office Project Server 2007에서 업그레이드 하는 경우에 필요를 않습니다. 다음과 같은 두 가지 유형의 데이터베이스 연결 업그레이드 방법: 
    
  - **전체 데이터베이스 연결 업그레이드** -Office Project Server 2007 데이터베이스에 저장 된 프로젝트 데이터와 SharePoint 콘텐츠 데이터베이스에 저장 된 Microsoft Project Web App (PWA) 사이트 데이터를 마이그레이션합니다. 
    
  - **코어 데이터베이스 연결 업그레이드** -Project Server 데이터베이스에 저장 된 프로젝트 데이터만 마이그레이션합니다. 
    
- **전체 업그레이드**: 팜과 팜에서 모든 콘텐츠에 대 한 구성 데이터 고정된 순서에 따라 기존 하드웨어에서 업그레이드 됩니다. 전체 업그레이드 프로세스를 시작 하는 경우 설치 프로그램에서는 전체 팜을 오프 라인 및 웹 사이트 및 Microsoft Project Web App 사이트는 업그레이드가 완료 되 고 설치 프로그램은 서버를 다시 시작 될 때까지 사용할 수 없습니다. 전체 업그레이드를 시작한 후에 업그레이드를 일시 중지 하거나 이전 버전으로 롤백할 수 없습니다. 프로덕션 환경의 미러 이미지를 확인 하 고이 환경 및 프로덕션 환경 하지-기본적으로 전체 업그레이드 매우 좋습니다. 
    
추가 리소스:
  
- [Microsoft Project Server 2010 업그레이드를 위한 superFlow](https://go.microsoft.com/fwlink/p/?linkid=841277)
    
- [Project Server 2010으로 Project Server 2007에서 마이그레이션](https://go.microsoft.com/fwlink/p/?linkid=841278)
    
- [Project Web App 웹 파트 업그레이드 고려 사항](https://go.microsoft.com/fwlink/p/?linkid=841276)
    
- [프로젝트 소프트웨어 개발 키트 (SDK)](https://go.microsoft.com/fwlink/p/?linkid=841275)
    
### <a name="step-2-migrate-to-project-server-2013"></a>2 단계: Project Server 2013으로 마이그레이션

다음 단계를 Project Server 2010으로 마이그레이션 및 데이터가 성공적으로 마이그레이션 되었는지 확인 (영문), 후 Project Server 2013에 데이터를 마이그레이션합니다.
  
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
    
### <a name="step-3-migrate-to-project-server-2016"></a>3 단계: Project Server 2016으로 마이그레이션

다음 단계를 Project Server 2013으로 마이그레이션 및 데이터가 성공적으로 마이그레이션 되었는지 확인 (영문), 후 Project Server 2016에 데이터를 마이그레이션합니다.
  
Project Server 2013에서 Project Server 2016으로 업그레이드를 수행 하는데 필요한의 포괄적인 이해 하십시오 technet을 설정 하는 Project Server 2016 콘텐츠를 업그레이드를 참조 하십시오.
  
주요 리소스:
  
|**리소스**|**설명**|
|:-----|:-----|
|[Project Server 2016 업그레이드 프로세스 개요](https://go.microsoft.com/fwlink/p/?linkid=841260) <br/> |높은 수준의 파악 Project Server 2013에서 Project Server 2016으로 업그레이드 하기 위해 수행 해야 합니다.  <br/> |
|[Project Server 2016으로의 업그레이드 계획](https://go.microsoft.com/fwlink/p/?linkid=841826) <br/> |계획 고려 사항 Project server 2016 포함 하 여 Project Server 2013에서 업그레이드 하는 경우를 결정 해야 하는 방법을 살펴봅니다.  <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>이 버전으로 업그레이드에 대해 고려할 사항

[Project Server 2016 하는 방법에 대 한 알아두어야 할 사항 업그레이드](https://go.microsoft.com/fwlink/p/?linkid=841827) 를 포함 하는이 버전에 대 한 업그레이드에 대 한 중요 한 일부 변경 지시 합니다. 
  
- Project Server 2016 환경을 Project Server 2013 데이터를 마이그레이션할 사항에 유의 합니다를 만들 때 SharePoint Server 2016에 Project Server 2016 설치 파일이 포함 됩니다. 자세한 내용은 [Project Server 2016 배포](https://go.microsoft.com/fwlink/p/?linkid=841829)를 참조 하십시오.
    
- 자원 계획은 Project Server 2016 사용 되지 않습니다. Project Server 2013 자원 계획을 세울 Project Server 2016 및 Project Online에서 자원의 계약으로 마이그레이션됩니다. 참조 [개요: 자원의 계약](https://support.office.com/article/73eefb5a-81fe-42bf-980e-9532b1bdc870) 에 대 한 자세한 내용은 합니다. 
    
## <a name="migrate-from-portfolio-server-2007"></a>Portfolio Server 2007에서 마이그레이션

Project Portfolio Server 2007 포트폴리오 전략, 우선순위 지정 및 최적화에 대 한 Project Server 2007과 함께 사용 되었습니다. 이 버전 후 없음 추가 버전의 Project Portfolio Server을 만들었습니다. 그러나 포트폴리오 관리 기능을 Project Server 2016 및 Project Online의 프리미엄 버전 모두에서 사용할 수 있습니다. Project Portfolio Server 2007에서 데이터를 마이그레이션할 수 없습니다. 비즈니스 영향 요소 등의 데이터를 다시 만들 해야 합니다.
  
기타 리소스:
  
- [Project Online 서비스 설명](https://go.microsoft.com/fwlink/p/?linkid=841280): Project Server 2016 및 온라인 프리미엄 프로젝트에 포함 된 포트폴리오 관리 기능을 참조 하십시오.
    
- [Microsoft Office Project Portfolio Server 2007 마이그레이션 가이드](https://go.microsoft.com/fwlink/p/?linkid=841279)
    
## <a name="related-topics"></a>관련 항목

[SharePoint Server 2007 로드맵 지원 종료](sharepoint-2007-end-of-support.md)
  
[2007 서버와 클라이언트에서 Office를 업그레이드 하는데 도움이 되는 리소스](upgrade-from-office-2007-servers-and-products.md)
  

