---
title: 고려할 SharePoint 2007 마이그레이션 옵션
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 1/31/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
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
description: SharePoint Server 2007는 지원 종료에 도달 했으며 업그레이드 하는 데 걸리는 시간입니다. 이 문서를 사용 하 여 계획을 만드는 데 도움을 받을 수 있습니다.
ms.openlocfilehash: 6315c06f034464cf12224582c9dcd0257bf43961
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2019
ms.locfileid: "38748035"
---
# <a name="sharepoint-2007-migration-options-to-consider"></a>고려할 SharePoint 2007 마이그레이션 옵션

*이 문서는 Office 365 Enterprise 및 Microsoft 365 Enterprise에 모두 적용 됩니다.*

Microsoft SharePoint 2007 및 SharePoint Server 2007가 지원 종료에 도달 했습니다. 업그레이드 하는 데 걸리는 시간입니다. 이 문서에서는 마이그레이션 옵션에 대 한 정보를 제공 합니다.
  
## <a name="common-upgrade-strategies-for-sharepoint"></a>SharePoint에 대 한 일반적인 업그레이드 전략

SharePoint Server 환경을 업그레이드 하는 방법에는 여러 가지가 있습니다. Microsoft Office SharePoint Server 2007 팜이 있는 경우 업그레이드 방법의 몇 가지 예는 다음과 같습니다.
  
- 데이터베이스 연결
    
- 병렬 업그레이드
    
- 전체 업그레이드
    
- 하이브리드 업그레이드 (현재 위치에 분리 된 데이터베이스/별도의 데이터베이스 연결)
    
- SharePoint 하이브리드 (온-프레미스 SharePoint에 온라인으로 연결)
    
- 사이트 모음 또는 라이브러리 간 데이터 수동 이동
    
- FastTrack Wizard를 Office 365으로 업그레이드 ([SharePoint Online 배포 관리자](https://aka.ms/spoguidance))
    
- Office 365의 마이그레이션 API-SharePoint Online (SPO)
    
가장 적합 한 것은 무엇 인가요?
  
팜에서 수행 하는 작업에 대 한 지식과 사용 방법은 업그레이드 시의 전략적 수준입니다. 사용자는 SharePoint 팜을 사용 하는 방법으로 옵션을 선택할 수 있습니다.
  
> [!TIP]
> Microsoft Office SharePoint Server 2007에는 여기에서 다루지 않는 점진적 업그레이드도 포함 되어 있습니다. 단계별 업그레이드 문서 목록을 보려면 [SharePoint Server 2007의 지원 종료 로드맵](sharepoint-2007-end-of-support.md)를 참조 하세요. 
  
업그레이드 하려는 SharePoint 버전에 대 한 [제품 수명 주기](https://support.microsoft.com/lifecycle/search) 및 시스템 요구 사항을 확인 해야 합니다. 이는 다음 업그레이드가 필요한 경우 (예: SharePoint Server 2010와 같은 레거시 제품을 일시 중지 하 여 더 많은 업그레이드를 계획 하는 경우 지원 날짜 종료 확인), 요금제를 지 원하는 하드웨어를 확보 해야 하는 경우를 고려해 야 합니다. 
  
SharePoint 사이트의 일부 또는 전체를 클라우드에서 Office 365로 전환할 계획 이라면 [office 365에 대 한 서비스 설명](https://technet.microsoft.com/library/office-365-service-descriptions.aspx)링크를 책갈피로 설정할 수 있습니다. SharePoint Online 기능 및이 기능이 온-프레미스 SharePoint Server와 다를 수 있는 방식에 대해 자세히 알아보려면 서비스 설명이 필요 합니다. 업그레이드 기능 Microsoft Office SharePoint Server 2007 팜 설치에 손상 된 사이트가 있으면 업그레이드 전에 해당 사이트를 수정 합니다.
  
## <a name="a-note-about-managing-risk"></a>위험 관리에 대 한 참고 사항

' 나란히 ' 등의 메서드는 업그레이드 논리의 체계에서 중요 합니다. Side-by-side로 업그레이드 하는 경우 Microsoft Office SharePoint Server 2007 팜을 유지 관리 하지만 새 하드웨어에서 팜 (SharePoint Server 2010)의 다음 버전인 팜을 구축 합니다. 이를 통해 다음과 같은 세 가지 방법을 활용할 수 있습니다.
  
1. 데이터베이스 연결을 사용 하 여 Microsoft Office SharePoint Server 2007 데이터베이스를 따로 백업 하 여 업그레이드를 수행할 수 있는 위치입니다.
    
2. Microsoft Office SharePoint Server 2007 팜에서 소수의 중요 문서 라이브러리 및 기타 정보를 사용 하는 경우에는 Microsoft Office SharePoint Server 2007에서 SharePoint Server 2010으로 데이터를 수동으로 이동 하도록 선택할 수 있습니다. 하거나 다음 버전을 사용 하 여 작업을 보다 쉽게 수행할 수 있습니다.
    
3. Microsoft Office SharePoint Server 2007 서버 팜에서 직접 수행 하는 작업은 업그레이드할 때 팜에 포함 되는 데이터를 보다 안전 하 게 사용할 수 있습니다.
    
현재 위치 업그레이드와 같은 방법은 Microsoft Office SharePoint Server 2007 팜에서 직접 작업 하므로 경로를 중단 하 고 초기 환경으로 다시 시작할 수 있는 쉬운 옵션을 제공 하지 않을 수 있습니다. 가능한 한 많은 보안 조치 (원본 환경에 대 한 백업 가져오기 및 테스트)를 구축 합니다. 예를 들어 Microsoft Office SharePoint Server 2007 팜이 가상이 고 백업 및 복원을 위해 복제 된 경우에는 업그레이드를 위해 서비스 창 앞에 있는 최신 데이터베이스를 백업 하 고 복원 합니다. 데이터베이스 백업을 복원 하는 옵션이 있다는 것은 안전 하 게 복구를 제공 하는 것이 아니라 안심 하 고 사용할 수 있다는 것입니다.
  
> [!TIP]
> 모범 사례 업그레이드에 대 한 문서는 [Microsoft Office Sharepoint server 2007](https://technet.microsoft.com/library/cc261992%28v=office.12%29.aspx), [sharepoint server 2010](https://technet.microsoft.com/library/cc261992%28v=office.14%29.aspx), [Sharepoint server 2013](https://technet.microsoft.com/library/cc261992%28v=office.15%29.aspx)및 [sharepoint server 2016](https://technet.microsoft.com/library/cc261992%28v=office.16%29.aspx)에 대 한 정보입니다. 업그레이드 또는 Office 365 마이그레이션 경험이 있는 [Microsoft 파트너](https://partnercenter.microsoft.com/pcv/search) 를 검색할 수도 있습니다. 
  
## <a name="make-your-plan"></a>계획 만들기

업그레이드 해야 하는 경우 계획이 필요 하며,이 경우에는 한 가지 크기에 모두 적합 하지는 않습니다. 계획은 ' SharePoint Online을 사용 하 여 Office 365 구독 만들기, 도메인 등록 및 사용자가 파일을 저장 하도록 리디렉션 '으로 간단할 수 있습니다. 이는 그렇지 않을 수 있습니다. 이 의사 결정은 사용자에 게 필요한 작업을 수행 하는 데 도움이 됩니다.
  
> [!NOTE]
> 주기가 종료 된 소프트웨어에서 실행 하는 것은 위험 합니다. 문제가 발견 되는 경우 지원 되지 않는 제품은 더 이상 패치 되지 않습니다. 또한 새 보안 위협이 발생 하는 경우에는 수명 주기 제품이 더 이상 지원 되지 않으므로 보안 패치나 수정 된 사항은 없습니다. 해당 상황을 방지 하세요. 
  
### <a name="first-know-your-farm"></a>먼저, 팜을 파악 합니다.

업그레이드 시에는 사용자의 조직이 조직에 대해 수행 하는 작업을 기반으로 결정을 내려야 합니다. 충족 해야 하는 작업 역할 이란? 회사의 각 팜에 서로 다른 역할이 있을 수 있습니다. 일부 SharePoint *팜은 파일 보관이 될* 수 있으며,이 경우 안전한 보관이 가능 합니다. 또는 팜이 여러 역할을 한 번에 채우는 경우에는 사이트 모음, 웹 또는 문서 라이브러리에 포함 된 모든 사용자 지정 내용 및 중요도를 알아야 할 수 있습니다. 이 수준에서 데이터를 분석 하는 것은 많은 작업을 수행 하는 것 처럼 보이지만 업그레이드 하거나 마이그레이션하기 전에 도메인을 마스터 하기 위한 시간과 노력을 절감할 수 있습니다. 모든 이동 부분 및 가장 중요 한 비트를 알게 되 면 outgrown를 파악 하 고 뒤에 남길 수 있습니다. 이 정보는 향후에만 도움이 됩니다. 
  
따라서 사용자 들이 SharePoint Server 팜에 대해 가장 중요 한 점은 무엇 인가요?
  
- 기본 제공 SharePoint 기능
    
- 대용량 데이터 모음 (예: 파일 보관 함)
    
- 사용 가능
    
- 중요 앱, 웹 파트 또는 팜의 문서 (미션 크리티컬 팜)
    
- 준수 표준 충족
    
- 사용자 지정 기능
    
SharePoint 팜에서 비즈니스에 필요한 작업을 실행 하는 경우 클라이언트 서비스 요구 사항에 대 한 중요 한 데이터의 큰 카탈로그 처럼 작동 한다고 말하면 ' 중요 한 앱 ' 옆에 틱을 배치 하 고 ' 가용성 '도 사용할 수 있습니다. 한 동안 SharePoint를 사용할 수 없는 경우 영향을 받습니다. 마찬가지로 팜이 제공 하는 중요 서비스가 사용자 지정 코드, 사이트 정의 또는 함께 작동 하는 여러 사용자 지정을 기반으로 하기 때문에 ' 사용자 지정 '을 확인할 수 있습니다.
  
소프트웨어에 대 한 기본 제공 기능을 사용 하지 않고 SharePoint에서 이러한 요구 사항을 충족 하 고 일반적으로이를 업데이트 하 고 일반적인 관리 및 유지 관리를 수행 하는 경우에는 ' 기본 제공 SharePoint '를 선택 했을 수 있습니다. 이전 버전의 SharePoint에서 앉아 있는 이유입니다. 즉, Microsoft Office SharePoint Server 2007의 지원 종료에서 현재까지 필요한 작업을 수행 했으며 지금까지 업그레이드할 필요가 없습니다.
  
이러한 항목을 글머리 기호로 표시 하면 업그레이드 조건을 만들 수 있습니다. 즉, 모든 업그레이드에서이 모음을 충족 해야 합니다. 이렇게 하면 현재 요구 사항에 적합 하지 않은 방법을 규칙 할 수 있습니다.
  
### <a name="a-simple-sample-plan"></a>간단한 예제 계획

SharePoint 업그레이드에 소요 되는 경로에 대 한 리더십 및 기타 관리자와의 합의도 더 많이 받아야 할 수 있습니다. SharePoint Server 관리자는 Microsoft SQL Server admins, 네트워킹 및 보안 팀과 공동 작업을 수행 하는 경우가 많습니다. 이해 관계자가 많은 경우에는 업그레이드 및 마이그레이션 계획에 대 한 계약을 작성 하거나 조정 해야 할 수 있습니다. 예를 들어 회사의 일부 Office 365에서 SharePoint Online을 사용 하도록 데이터를 마이그레이션하는 경우 네트워크 내부에 성능 조정 이나 테스트를 수행 해야 할 수 있습니다. 영향을 받는 팀에 게 미리 알려야 합니다.
  
간단한 예제에서는 SharePoint 관리자의 제안서를 표시 한 다음 모든 관련자 들이 동의한 계획을 나열 합니다. 이해를 돕기 위해 계약과 결정 사항을 문서화 합니다.
  
이 계획은 팜의 심도 깊은 분석을 수행한 후에 시작 되며, 팜의 역할, 불만 사항 및 일부 업그레이드 옵션의 범위를 좁히는 데 도움이 되는 기타 중요 한 정보를 식별 하려고 합니다. 나중에 SharePoint 관리자가 업그레이드 제안서를 작성 하 고, 관련자는 작업 계획에 동의 합니다.
  
바로 위의 ' 중요 ' 글머리 기호 목록:
  
- 가용성, SharePoint에 기본 제공 되는 기능 및 규정 준수 표준
    
- 대부분의 데이터는 세 개의 사이트 모음에 있으며, 개발 팀에서 사용 하는 모임 작업 영역은 특히 중요 하며 여러 표준 시간대에서 많이 사용 되 고 있습니다.
    
- 널리 사용 되는 seventeen 기타 사이트가 있습니다.
    
- 두 개의 문서 라이브러리 (모임 작업 영역과 루트 사이트 모음의 문서)는 가장 큰 값입니다 (각각 8000 개 문서). 스프레드시트 첨부 파일이 있는 보관 된 문서 및 목록에 다 수의 내용이 있습니다.
    
- 중요 한 데이터가 포함 된 라이브러리의 fourteen 목록에는 준수 해야 합니다.
    
- 이 경우에는 언제 든 지 보류 및 전자 검색을 수행할 수 있어야 합니다.
    
- 이 데이터 중 일부는 InfoSec 규칙으로 인해 온-프레미스에 유지 되어야 합니다.
    
 **내 업그레이드 및 마이그레이션 선택 사항:**
  
|||
|:-----|:-----|
|**예** <br/> |**아니요** <br/> |
|데이터베이스 연결을 사용 하 여 데이터베이스 업그레이드  <br/> |전체 업그레이드  <br/> |
|팜 및 side-by-side로 업그레이드  <br/> |하이브리드 업그레이드  <br/> |
|Office 365에서 SPO로의 마이그레이션 API (개인 사이트 데이터에 대 한)  <br/> |SharePoint 하이브리드 (아직 필요 하지 않음)  <br/> |
|일부 수동 데이터는 중요 한 데이터에 대 한 SharePoint Online으로 마이그레이션  <br/> |FastTrack 마법사에서 Office 365로 업그레이드  <br/> |
   
 **제안 된 계획:**
  
데이터베이스를 먼저 업그레이드할 수 있도록 SharePoint 버전을 동시에 사용 하 여 온-프레미스로 업그레이드 합니다. SharePoint 2007에서 SharePoint 2010로 이동 합니다. 관리자 및 Devs 결과 팜을 테스트 합니다. 사용자가 결과 팜을 테스트 합니다. 이 시간 동안에는 모든 쇼를 중지 하는 문제를 해결 합니다. 동시에 SharePoint 2010 데이터베이스를 SharePoint 2013로 업그레이드 합니다. 테스트. 사용자 테스트/파일럿 이 시간 동안에는 모든 쇼를 중지 하는 문제를 해결 합니다.
  
- SPO와의 검색 페더레이션 하이브리드가 사용자의 요구를 충족 하는지 고려 합니다.
    
- 여기에서 SharePoint Online으로 업그레이드 하려는 경우 [Fasttrack 지원을](https://fasttrack.microsoft.com) 고려 합니다. 
    
- 사이트 모음을 Office 365 구독으로 오프 로드할 수 있는지 확인 합니다. (Office 365은 다양 한 [준수 표준을](https://technet.microsoft.com/library/office-365-compliance.aspx)충족 합니다. Office 365는 [eDiscovery](https://support.office.com/article/edea80d6-20a7-40fb-b8c4-5e8c8395f6da) 를 포함 하며 준수 센터를 통해 [유지](https://support.office.com/article/A18F8975-AA7F-43B4-A7D6-001D14744D8E) 될 수 있습니다. 
    
그렇지 않으면 SharePoint Server 2016로의 side-by-side 업그레이드를 계속 수행 합니다.
  
> [!NOTE]
> 업그레이드를 계획 하는 관리자가 수행 하는 권장 사항과 실제 프로세스는 업그레이드가 의존 하는 다른 관련자 들이 수행 하는 대화입니다. 예를 들어 경제 강제 관리자가 계획을 변경 하는 경우도 있습니다. 최종적으로 결정 되는 사항에 관계 없이 합의 된 계획의 내용을 문서화 해야 합니다. 다음과 같은 화면이 표시 될 수 있습니다. 
  
 **내 작업 계획:**
  
온-프레미스에서는 가상 환경을 사용 하 여 기본 SharePoint Server 2010 및 2013을 작성 합니다. SharePoint Server 2016는 2016에 대 한 시스템 요구 사항을 충족 하는 새로운 하드웨어를 기반으로 구축 될 예정입니다. 데이터베이스를 연결 하 여 SharePoint 2007에서 it 및 SharePoint Server 2016 간의 모든 버전을 통해 데이터베이스를 업그레이드 합니다. 핵심 사용자 지정 기능은 지금까지 SharePoint Server 2016 환경에서 다시 만들어지고 테스트 됩니다. 이 작업을 성공적으로 수행 하면 업그레이드 된 데이터베이스를 사용 하는 새 하드웨어에 온-프레미스 팜이 제공 되 고 사용자 지정 내용이 더 적어집니다. 업그레이드 된 콘텐츠 데이터베이스를 SharePoint Server 2013, test, user test/파일럿의 새 사이트 모음에 연결 하 고 live 사용을 위해 새 SharePoint Server 2016 환경으로 DNS를 중단 합니다.
  
- 지금은 SharePoint Server 2016와 SharePoint Online 간에 페더레이션 하이브리드를 고려 하지 않습니다.
    
- 예상 35%의 사이트는 베 니 티 도메인을 가진 새 SPO 사이트로, 궁극적으로는 비즈니스용 OneDrive 저장소로 설정할 수 있습니다. 사이트를 변환 하거나 새 사이트를 SPO로 라우팅하는 다른 기회를 찾고 있습니다.
    
- 이러한 마이그레이션 부분 중 일부는 끌어서 놓기를 사용 하 여 비즈니스용 OneDrive 개인 사이트 및 마이그레이션 API를 통해 수동으로 진행 됩니다.
    
자세한 단계 또는 특정 업그레이드 지침에 대 한 여러 링크가 계획을 따라야 합니다. MOSS 2007 컴퓨터는 해제 하지 않아야 하며, 가상 환경을 비교 하기 위해 유지 관리 해야 합니다. 그러나 사용자가 SharePoint Server 2016로 리디렉션될 때 업그레이드가 완료 됩니다.
  
방법을 선택할 때의 주요 요인은 업그레이드의 총 비용 및 시간에 따른 비용 (SharePoint 마이그레이션 로드맵 문서에 자세히 나와 있습니다.) 그러나 사전 계획을 세울 때는 기대치를 매우 효율적으로 설정 하 고, 신중 하 게 선택 하 고, 성공 여부를 파악 하는 것이 좋습니다.
  
## <a name="related-links"></a>관련 링크

[Office 2007 서버 및 클라이언트에서 업그레이드 하는 데 도움이 되는 리소스](upgrade-from-office-2007-servers-and-products.md)
  
[Microsoft 수명 주기 정책 및 수명 주기 검색](https://support.microsoft.com/lifecycle)
  
[업그레이드 또는 마이그레이션에 대 한 도움을 받을 수 있는 Microsoft 파트너 검색](https://partnercenter.microsoft.com/pcv/search)
  

