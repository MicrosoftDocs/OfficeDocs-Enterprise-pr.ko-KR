---
title: SharePoint 2007 마이그레이션 옵션을 고려해 야
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 1/31/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- MET150
- SPS150
- OSU140
- SPO160
- SPB160
- OSI150
- OSI160
- BSA160
- OSU160
ms.assetid: 66325a43-5816-4f8e-81ba-c11b71345b7c
description: SharePoint Server 2007에는 지원의 끝에 도달 했습니다 이며 업그레이드 하는 시간입니다. 이 문서를 사용 하 여 계획을 수립 하는 데 도움이 됩니다.
ms.openlocfilehash: 4395bc330efd97ae8865e0fb75f93f04fd162ecd
ms.sourcegitcommit: a9c84d02e94c99ff6b1099b4a9ae695be08210e2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/25/2018
ms.locfileid: "21169880"
---
# <a name="sharepoint-2007-migration-options-to-consider"></a>SharePoint 2007 마이그레이션 옵션을 고려해 야

Microsoft SharePoint 2007과 SharePoint Server 2007 지원의 끝에 도달 했습니다. 업그레이드 하는! 이 문서에서는 사용자가 마이그레이션 옵션에 대 한 정보를 제공 합니다.
  
## <a name="common-upgrade-strategies-for-sharepoint"></a>SharePoint에 대 한 일반적인 업그레이드 전략

SharePoint Server 환경을 업그레이드 하는 방법은 여러 가지가 있습니다. Microsoft Office SharePoint Server 2007 팜이 있는 경우 업그레이드 방법에 대 한 예가 다음과 같습니다.
  
- 데이터베이스 연결
    
- 수평적으로 업그레이드
    
- 전체 업그레이드
    
- 혼합 업그레이드 (분리 된 데이터베이스를 사용한 전체 / 별도 데이터베이스 연결)
    
- SharePoint 하이브리드 (온-프레미스 sharepoint online 연결)
    
- 사이트 모음 또는 라이브러리 간에 데이터를 수동으로 이동합니다.
    
- Office 365 ([SharePoint Online 배포 관리자](https://aka.ms/spoguidance))에 FastTrack 마법사 업그레이드
    
- SharePoint Online (SPO) Office 365의에서 마이그레이션 API
    
어떤 적합 한?
  
팜의 않습니다 및에 대 한 사용에 대 한 지식이 전략적 강도 때 업그레이드를 제공 합니다. 사용자는 SharePoint 팜에서 사용 하는 방식을 사용자 옵션 중에서 선택할 수는 데 도움이 됩니다.
  
> [!TIP]
> Microsoft Office SharePoint Server 2007에는 또한 여기에서 설명 하지 점진적 업그레이드를가지고 있습니다. 단계별 업그레이드의 목록을 보려면 문서 [끝에 SharePoint Server 2007 지원 로드맵](sharepoint-2007-end-of-support.md)참조 하십시오. 
  
SharePoint 업그레이드 하는 경우의 모든 버전에 대 한 [제품 수명 주기](https://support.microsoft.com/en-us/lifecycle/search) 및 시스템 요구 사항을 확인 해야 합니다. 이 다음 업그레이드 해야 합니다 (예: 더 많은 업그레이드에 대 한 계획, 지원 날짜의 끝을 잘 알고 있어야 하는 SharePoint Server 2010과 같은 레거시 제품에서 일시 중지 하는 경우) 때 인식 수 있도록 계획을 지 원하는 하드웨어를 있을 수 있습니다. 
  
일부 또는 전부 SharePoint 사이트의 클라우드에서 Office 365로의 전환 하려면 계획 하는 경우 [Office 365 서비스 설명](https://technet.microsoft.com/en-us/library/office-365-service-descriptions.aspx)에 대 한 링크에 책갈피를 시간입니다. SharePoint Online 기능에 대해 자세히 알아보려면 서비스 설명 해야 하 고에서 다 수는 어떻게 온-프레미스 SharePoint Server 합니다. Microsoft Office SharePoint Server 2007 팜 기능을 업그레이드 합니다. 설치에 손상 된 사이트가 있으면 업그레이드 이전에 수정 합니다.
  
## <a name="a-note-about-managing-risk"></a>위험을 관리 하는 방법에 대 한 메모

'--나란히 '와 같은 메서드는 업그레이드 논리의 구성표에 중요 합니다. 나란히를 업그레이드 하는 경우에 Microsoft Office SharePoint Server 2007 팜의 유지 관리 하지만 팜을 작성 다음 버전 (SharePoint Server 2010)에서 새 하드웨어에 합니다. 이 세가지 방법으로 도움이 됩니다.
  
1. 개별적으로 업그레이드, 데이터베이스를 사용 하 여 연결 하 여 Microsoft Office SharePoint Server 2007 데이터베이스의 백업을 수행할 수 있는 위치를 해야 합니다.
    
2. 소수의 중요 한 문서 라이브러리 및 기타 정보에는 Microsoft Office SharePoint Server 2007 팜에 사용에는 기 하는 경우 Microsoft Office SharePoint Server 2007에서 SharePoint Server 2010으로 데이터를 수동으로 이동 하도록 선택할 수 있습니다. 또는 특정 사이트 및 웹 구성 된 다음 버전 (작업을 손쉽게 수행할 수)를 수행 합니다.
    
3. Microsoft Office SharePoint Server 2007 서버 팜으로, 직접,는 안전 하 게 업그레이드를 팜 데이터를 포함 할 줄어듭니다.
    
전체 업그레이드와 같은 메서드 작동할 직접에 Microsoft Office SharePoint Server 2007 팜에 대 한 경로 포기 하 고 초기 환경으로 다시 시작을 쉽게 옵션 수가 감소 하 게 합니다. 가능한, 일부 보안 방식 (예: 라인으로 전환 하 고 원래 환경의 백업 테스트)을 작성 합니다. 예, Microsoft Office SharePoint Server 2007 팜 가상, 백업 및 복원의 목적을 위해 중복 될 경우를 백업한 후 하 고 업그레이드를 위한 서비스 윈도 대화 하기 전에 최신 데이터베이스를 복원 합니다. 백업 하지는 데이터베이스를 복원 하는 옵션 한다고 알면만 안전한 제공, 파악 하는 안심 합니다.
  
> [!TIP]
> 업그레이드를 위한 모범 사례 문서 [Microsoft Office SharePoint Server 2007](https://technet.microsoft.com/en-us/library/cc261992%28v=office.12%29.aspx), [SharePoint Server 2010](https://technet.microsoft.com/en-us/library/cc261992%28v=office.14%29.aspx), [SharePoint Server 2013](https://technet.microsoft.com/en-us/library/cc261992%28v=office.15%29.aspx)및 [SharePoint Server 2016](https://technet.microsoft.com/en-us/library/cc261992%28v=office.16%29.aspx)존재합니다. 업그레이드 또는 Office 365 마이그레이션 경험을가지고 있는 [Microsoft 파트너](https://partnercenter.microsoft.com/en-us/pcv/search) 에 대 한 검색할 수 있습니다. 
  
## <a name="make-your-plan"></a>계획 만들기

업그레이드 해야하는 경우는 계획 해야 하 고 이러한 경우에는 모든 1 크기에 맞게 하지 않습니다. 계획을 문서화할 'SharePoint Online을 사용 하 여 Office 365 구독을 만들기, 도메인을 등록 하 고 다음과 같은 파일을 저장 하는 사용자를 리디렉션할' 처럼 간단할 수 있습니다. 및 되지 않을 수 있습니다. 결정 사용자가 임의로, 아니며으로 기능 및 사용자에 게 필요 합니다.
  
> [!NOTE]
> 것은 해당 수명 주기 끝난 소프트웨어를 실행 하려면 위험 합니다. 문제가 발견 되 면에서 지원 되는 제품에는 더이상 패치가 적용 됩니다. 즉, 새 보안 위협 발생 하는 경우 것 없는 보안 패치 또는 수정 프로그램 수명 주기의 끝에 포함 된 제품은 더이상 지원 되지 않으므로 합니다. 해당 상황이 발생 하지 않도록 하십시오! 
  
### <a name="first-know-your-farm"></a>먼저, 팜의 알고 있습니다

를 업그레이드 하는 경우 결정 된 사항을 기반으로 해야 조직에 대 한 사용자의 팜이 수행 하는 작업입니다. 어떤 요구를 충족 않는? 역할은 무엇입니까? 회사에서 각 팜에 다른 역할이 있을 수 있습니다. SharePoint 팜 중 일부 *중요 한* 못할 일부 파일 보관-보관에 대 한 있을 수 있습니다. 또는 팜의 한번에 여러 역할을 채우는, 하는 경우 다음 해야할 수 있습니다 어떤 사이트 모음, 웹, 또는 문서 라이브러리도 수행, 모든 사용자 지정 및 자신이 얼마나 중요 한지 확인 합니다. 이 수준에서 데이터를 분석 하는 다른 많은 작업 처럼 보이지만 시간과 노력 업그레이드 또는 마이그레이션 전에 도메인을 완벽 하 게 저장 하는 것이 있습니다. 모든 이동 파트와 가장 중요 한 비트 알면 하면 초과 한다면 했을 때 항목과 뒤에 남길 수 알 수 있습니다. 해당 기술만 둡니다 앞으로 이동 합니다. 
  
따라서는 사용자가 말 SharePoint 서버 팜에 대 한 가장 중요 한?
  
- 기본 제공 SharePoint 기능
    
- 큰 데이터 모음 (예: 파일의 보관)
    
- 사용 가능
    
- 중요 한 앱, 웹 파트 또는 팜 (임무 중요 한 팜)에서 문서
    
- 충족 준수 표준
    
- 사용자 지정 기능
    
SharePoint 팜에서 비즈니스에 필수적 무언가 실행 하는 경우 클라이언트 서비스 요구 사항에 대 한 중요 한 데이터의 큰 카탈로그 처럼 작동 하는 것, '중요 한 앱' 옆에 있는 눈금을 배치할 수 있지만 '가용성-', 즉 비즈니스 수도 라고 표시 잠시 자리를 SharePoint를 사용할 수 없 었 하는 경우의 영향을 받는 합니다. 마찬가지로,는 중요 한 기능을 제공 된 사용자 지정 코드, 사이트 정의 또는 함께 작동 하는 사용자 지정 숫자를 기반으로 하며 팜의 서비스 때문에 '사용자'를 확인할 수 있습니다.
  
SharePoint는 소프트웨어에 기본 제공 이란를 사용 하 여 외부에서 아무 작업도 수행 하지 않아도 이러한 요구를 충족 하 고 일반적으로 업데이트 하 고 기본 관리 및 유지 관리 수행 하기 위해, ' 기본 제공 SharePoint'을 선택 했으면-수도 있습니다. 하는 경우 사용자 이전 버전의 SharePoint에서 전화에 대 한 설명입니다. 즉, 필요한 정보를 이미 수행 하 고 지원의 Microsoft Office SharePoint Server 2007 끝 이제에 업그레이드 하는 데 필요한 하지 않은 합니다.
  
때 하면 글머리 기호 목록 업그레이드에 대 한 조건을 만들려면이 기능을 합니다. 즉,이 막대 것으로 간주를 충족 하기 위해 모든 업그레이드 해야 합니다. 현재 사용자의 요구에 맞지 않는 방법 발생 하지 않도록 하는 방법을 제공 합니다.
  
### <a name="a-simple-sample-plan"></a>간단한 예제 계획

있습니다 리더와 넓을 합 및 다른 관리자가 SharePoint 업그레이드에 소요 되는 경로 할 수도 있습니다. SharePoint 서버 관리자는 종종 Microsoft SQL Server 관리자와 상호 운용 되어, 네트워킹 및 보안 팀 등을 사용 합니다. 이해 관계자에 게 많은 있는 계약을 구축 하거나 업그레이드 및 마이그레이션 계획을 조정 해야할 수 있습니다. 예, 회사의 일부 Office 365의 SharePoint Online 사용 하도록 데이터를 마이그레이션할 다음과 같은 가능성이 할 경우 성능 조정 또는 네트워크 내에 테스트 합니다. 사전에 영향을 받는 팀을 알려야 합니다.
  
내 간단한 예제에는 SharePoint 관리자의 제안 표시 하는 모든 이해 관계자에 게 합의 하는 전체 계획을 표시 합니다. 명확 하 게, 계약 및 결정 사항을 문서화 합니다.
  
계획은 팜에 대 한 심도 깊은 분석 후에 시작 하 고 역할은 팜, 불만 사항 및 유도 일부 업그레이드 옵션 아래쪽으로 제한 하는 기타 중요 한 정보를 확인 하려고 시도 합니다. 나중에 업그레이드 제안 SharePoint 관리자에 의해 이루어집니다 및 이해 관계자에 게 작업 계획에 동의 합니다.
  
내 '가장 중요 한' 글머리 기호 목록:
  
- 가용성, SharePoint에 기본 제공 기능 및 규정 준수 표준입니다.
    
- 대부분의 데이터는 하나의 모임 작업 영역에서에서 사용 되는 개발 팀이 특히 중요 하 여 여러 시간대에서 너무 많이 사용 하면 전세계와 3 개의 사이트 모음에 있습니다.
    
- 널리 사용 되는 다른 사이트 17 있습니다.
    
- 두 문서 라이브러리 (모임 작업 영역 및 루트 사이트 모음에 있는 문서)은 가장 큰 (넘는 8000 문서 각). 많은 수의 보관 된 문서와 스프레드시트 첨부 파일을 사용 하 여 목록 했습니다.
    
- 규정 준수에 유지 되어야 하는 중요 한 데이터가 포함 된 라이브러리 14 목록이 있습니다.
    
- 우리는 어디서 든 보류 및 e-검색을 수행 하는 기능이 있어야 합니다.
    
- 이 데이터 중 일부를 온-프레미스, 정보 보안 과도 규칙으로 인해 유지 해야 합니다.
    
 **내 업그레이드 및 마이그레이션 선택 사항:**
  
|||
|:-----|:-----|
|**예** <br/> |**아니요** <br/> |
|데이터베이스를 사용 하 여 업그레이드 데이터베이스 연결  <br/> |전체 업그레이드  <br/> |
|팜--나란히도 업그레이드  <br/> |혼합 업그레이드  <br/> |
|마이그레이션 API Office 365의 SPO로 (개인 사이트 데이터)  <br/> |SharePoint 하이브리드 (아직 필요 없음)  <br/> |
|중요 한 데이터에 대 한 SharePoint online 일부 수동 데이터 마이그레이션  <br/> |Office 365로 FastTrack 마법사 업그레이드  <br/> |
   
 **내 제안 된 계획 합니다.**
  
업그레이드 온-프레미스, SharePoint--나란히, 가상화는 데이터베이스를 먼저 업그레이드할 수 있도록 일부의 버전입니다. SharePoint 2007에서 SharePoint 2010으로 이동 합니다. 테스트 결과 팜 관리자 및 트랜잭션당 합니다. 결과 팜을 테스트 하는 사용자입니다. 이 시간 동안 표시 중지 문제를 해결 합니다. 마찬가지로-나란히, 업그레이드 SharePoint 2010 데이터베이스를 SharePoint 2013 합니다. 파일럿/검정에 근거한 사용자 테스트 합니다. 이 시간 동안 표시 중지 문제를 해결 합니다.
  
- SPO와 검색 페더레이션 하이브리드 요구를 충족 하는 경우 하는 것이 좋습니다.
    
- 여기에서 SharePoint online 업그레이드 하려는 경우 [FastTrack 지원](https://fasttrack.microsoft.com) 것이 좋습니다. 
    
- 모든 사이트 모음에 Office 365 구독을 오프 로드할 수 하는 경우를 결정 합니다. (Office 365 많은 [준수 표준](https://technet.microsoft.com/library/office-365-compliance.aspx)을 충족 하는 데 사용 됩니다. Office 365 [eDiscovery](https://support.office.com/article/edea80d6-20a7-40fb-b8c4-5e8c8395f6da) 있으며 준수 센터를 통해 [을 포함 하 고](https://support.office.com/article/A18F8975-AA7F-43B4-A7D6-001D14744D8E) 작업을 수행할 수 있습니다.) 
    
그렇지 않은 경우 SharePoint Server 2016-나란히 업그레이드를 계속 합니다.
  
> [!NOTE]
> 업그레이드 및 실제 프로세스는 권장 사항을 계획 하는 관리자가 변경한 시점 업그레이드 의존 하는 다른 관련자와 발생 하는 대화는입니다. 등 경우가 종종 경제성 강제로 관리자가 자신의 계획을 변경할 수 있습니다. 모든 최종 결정은 합의 계획은 무엇을 문서화 해야 앞으로 이동 합니다. 형식은 다음과 같습니다. 
  
 **내 작업 계획 합니다.**
  
온-프레미스, 기본 SharePoint Server 2010 및 2013을 구축 하는 가상 환경을 사용 합니다. SharePoint Server 2016 2016에 대 한 시스템 요구 사항에 맞는 새로운 하드웨어 기반으로 구축 됩니다. 수행 하기 위해 데이터베이스와 SharePoint 서버 2016 사이의 모든 버전을 통해 SharePoint 2007에서 데이터베이스를 업그레이드 하는 연결 합니다. 핵심 사용자 지정에 대 한 다시 하며 SharePoint 서버에서 2016 환경에서 테스트이 시간 네이티브 기능 요구 사항을 충족 이미 하지 하는 경우. 우리는 성공 하는 경우에 업그레이드 된 데이터베이스와 새 하드웨어에 온-프레미스 팜과 더 적은 수의 사용자 지정은이 갖습니다. SharePoint Server 2013, 테스트, 사용자 테스트/파일럿에서에서 새 사이트 모음을 업그레이드 된 콘텐츠 데이터베이스를 연결 하는 하 고을 수행 DNS 단독형 라이브 사용에 대 한 새 SharePoint 서버 2016 환경입니다.
  
- 고려 하지 않습니다 SharePoint Server 2016 및 SharePoint Online 간의 하이브리드 페더레이션 지금은 합니다.
    
- 이 사이트의 예상된 35%는 베 니 티 도메인으로 구성 된 새 SPO 사이트를 설정 하거나 수, 궁극적으로, 비즈니스 저장소에 대 한 OneDrive 될 합니다. 사이트,으로 변환 하거나 새 사이트를 SPO로 라우팅할 수 있는 다른 기회를 찾고 있습니다.
    
- 이 부분에서는 마이그레이션 중 일부는 끌어서 놓기 OneDrive에 비즈니스 개인 사이트에 대 한 및 마이그레이션 API에 의해 일부 하 여 수동 수 있습니다.
    
자세한 단계, 또는 업그레이드에 표시 되는 특정 지침에 대 한 링크의 수를 계획을 따라야 합니다. MOSS 2007 컴퓨터를 해제할 수 해야, 및 비교;을 위해 가상 환경을 유지 해야 그러나 사용자가 SharePoint Server 2016 리디렉션됩니다 때 업그레이드는 완료 됩니다.
  
방법 선택에서 종종 주요 요소는 업그레이드의 총 비용 및 시간 (배웁니다이 대 한 추가 SharePoint 마이그레이션 로드맵 문서의) 비용입니다. 그러나 계획 차지 코드로 미리 차 됩니다 및 이점을 제공 하면 크게 알리기 신중 하 게 선택에서 어떤 성공 프레이밍은 다음과 유사 합니다.
  
## <a name="related-links"></a>관련 링크

[2007 서버와 클라이언트에서 Office를 업그레이드 하는데 도움이 되는 리소스](upgrade-from-office-2007-servers-and-products.md)
  
[Microsoft 수명 주기 정책 및 수명 주기 검색](https://support.microsoft.com/en-us/lifecycle)
  
[마이그레이션 또는 업그레이드를 도와줄 수는 Microsoft 파트너에 대 한 검색](https://partnercenter.microsoft.com/en-us/pcv/search)
  

