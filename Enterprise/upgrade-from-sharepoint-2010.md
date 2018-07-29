---
title: SharePoint 2010에서 업그레이드
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 2/2/2018
ms.audience: ITPro
ms.topic: conceptual
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- MET150
- WSU140
- OSU140
ms.assetid: 985a357f-6db7-401f-bf7a-1bafdf1f312c
description: SharePoint 2010 및 SharePoint Server 2010 거의 가득 차지 지원 종료 합니다. 지침으로이 문서를 사용 하 여 SharePoint Online 또는 SharePoint Server 온-프레미스의 최신 버전으로 업그레이드 합니다.
ms.openlocfilehash: c88c6010aa398d8076fce59976bf6f5c0aa1a743
ms.sourcegitcommit: a9c84d02e94c99ff6b1099b4a9ae695be08210e2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/25/2018
ms.locfileid: "21169870"
---
# <a name="upgrading-from-sharepoint-2010"></a>SharePoint 2010에서 업그레이드

2020, 10 월 13에서 Microsoft Office SharePoint Server 2010에는 지원의 끝에 도달 합니다. 이 문서는 리소스를 사용자가 자신의 기존 SharePoint Server 2010 데이터를 SharePoint Online으로 마이그레이션 또는 SharePoint 서버에서 온-프레미스 업그레이드에 대해 자세히 설명 합니다.
  
## <a name="what-is-end-of-support"></a>지원 종료 이란?

이 소프트웨어의 '지원 '를 마치고 라고 SharePoint Server 2010, 및 SharePoint Foundation 2010 소프트웨어 지원 주기 (하는 동안 Microsoft의 새로운 기능, 버그 수정, 보안 픽스 및 등을 제공 하는 시간)의 끝에 도달 하거나, 경우에 따라 해당 ' 퇴직 ' 합니다. 지원 (또는 EOS)는 제품의 끝에 따라 nothing 실제로 종료 하거나 중지 (영문); 그러나 소프트웨어 지원 끝날 때 Microsoft 더이상 제공합니다.
  
- 발생할 수 있는 문제에 대 한 기술 지원
    
- 검색 되는 및 안정성과 서버;의 유용성 영향을 줄 수 있는 문제에 대 한 버그 수정
    
- 검색 되는 하 고 서버를 공격에 취약 한 보안 위반 행위에 만들 수 있는 취약점에 대 한 보안 수정
    
- 표준 시간대를 업데이트합니다.
    
즉, 있을 것 더 이상 업데이트, 패치, 또는 (보안 패치/픽스가 포함), 제품에 대 한 픽스를 전달할 및 Microsoft 기술 지원 서비스는가 완벽 하 게 이동 하 여 해당 지원 노력 보다 최신 버전을 합니다. SharePoint Server 2010의 지원의 끝에 도달 하는 대로 업그레이드 하는 제품 및/또는 중요 한 데이터를 마이그레이션하기 전에 필요 없는 데이터를 높이고 수 있는 기회를 활용을 취해야 합니다.
  
> [!NOTE]
> 소프트웨어 수명 주기는 일반적으로 제품의 초기 릴리스 날짜에서 10 년 동안 지속 됩니다. 다음 버전의 소프트웨어로 업그레이드 또는 Office 365 마이그레이션 (또는 둘 모두) 도움이 되는 [Microsoft 파트너](https://go.microsoft.com/fwlink/?linkid=841249) 를 검색할 수 있습니다. 보관할 SharePoint 함께 사용 하는 경우 SQL server 버전의 특히 중요 기반 기술도에서 지원 날짜의 끝 알고 있어야 합니다. 
  
## <a name="what-are-my-options"></a>내 옵션은 무엇입니까?

첫째, [제품 수명 주기 사이트](https://support.microsoft.com/en-us/lifecycle/search?alpha=SharePoint%20Server%202010)에 지원 끝 날짜를 확인 합니다. 다음으로,이 날짜에 대 한 지식와 마이그레이션 또는 업그레이드 일정을 계획 해야 합니다. 해당 날짜 후 설치를 패치해야 더이상 됩니다, 이후 알면 도움이 되는 경우 더 원활 하 게을 다음 버전의 전환 전략 없지만 나열 된 사용자 제품 *작동이 중지 되지 않음* 날짜에 맞게 변경 하 고 해당 사용을 계속할 수 없습니다 제품입니다. 
  
이 매트릭스를 사용할 때 마이그레이션 제품 기능 및 사용자 데이터는 과정을 그리는 도움이 됩니다.
  
|**지원 제품의 끝**|**중**|**최상**|
|:-----|:-----|:-----|
|SharePoint Server 2010  <br/> |SharePoint Server 2013  <br/> |SharePoint Online  <br/> |
||SharePoint 하이브리드  <br/> |SharePoint Server 2016 (온-프레미스)  <br/> |
|||SharePoint 클라우드 하이브리드 검색  <br/> |
   
눈금 (좋은 옵션)의 낮은 끝에서이 옵션을 선택 하는 경우에 SharePoint Server 2010에서 마이그레이션을 완료 한 후에 곧 다른 업그레이드에 대 한 계획을 시작 하려면 필요 합니다. (지원 종료 대 한 SharePoint Server 2010 및 SharePoint Foundation 2010은 *항상 주의 하십시오* 항상 해야 하지만 2020, 10 월 13에 대 한 예약 된 체크 [제품 수명 주기 사이트](https://support.microsoft.com/en-us/lifecycle) 에 가장 정확한 날짜에 대 한!) 
  
## <a name="where-should-i-go-next"></a>다음 이동 해야는 위치

SharePoint Server 2013 및 SharePoint Foundation 2013 온-프레미스 설치 자체 서버에 될 수 있습니다. 그렇지 않은 경우 사용할 수 있습니다 SharePoint Online은 온라인 서비스는 Microsoft Office 365의 일부입니다. 하도록 선택할 수 있습니다.
  
- SharePoint Online으로 마이그레이션
    
- SharePoint Server 또는 SharePoint Foundation 온-프레미스 업그레이드
    
- 위의 두 항목 모두를 수행 합니다.
    
- [SharePoint 하이브리드](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx) 솔루션을 구현 
    
숨겨진된 비용을 앞으로, 서버 팜을 유지 관리와 관련 된 유지 관리 또는 사용자 지정, 마이그레이션 및 종속 되는 SharePoint 서버 하드웨어를 업그레이드 알고 있어야 합니다. 알고 있어야 하 고 대부분의 경우 온-프레미스 업그레이드 계속을 쉽게 됩니다. 그렇지 않은 경우 굵은 사용자 지정 하지 않고 기존 SharePoint 서버에 팜을 실행 하는 경우 혜택을 볼 수는 계획 된 마이그레이션에서 SharePoint online 합니다. 것도 가능 하는 온-프레미스 SharePoint Server의 상점 자신의 데이터 온-프레미스 때는 모든을 유지 하는 하드웨어 관리의 양을 줄일을 SharePoint Online에서 일부 데이터에 선택할 수 있습니다. SharePoint Online으로 이동 하는 데이터의 일부를 더 경제적 수 있습니다.
  
> [!NOTE]
> SharePoint 관리자가 새 SharePoint Online 사이트에는 가장 중요 한 카운터 문서의 경우에 수행 [Office 365 구독을 만들](https://go.microsoft.com/fwlink/?linkid=843152), 새로운 SharePoint Online 사이트를 설정 하 고 완벽 하 게, 잘라내기 SharePoint Server 2010에서 자리 수 있습니다. 여기에서 온-프레미스 보관에 남은 데이터 SharePoint Server 2010 사이트에서 소모 될 수 있습니다. 
  
|**SharePoint Online (SPO)**|**SharePoint Server 온-프레미스**|
|:-----|:-----|
|시간에 높은 비용 (계획 / 실행 / 확인)  <br/> |시간에 높은 비용 (계획 / 실행 / 확인)  <br/> |
|자금 (하드웨어 구입 제외)에서 저렴 한 비용  <br/> |자금 (하드웨어를 구입)에 더 높은 비용  <br/> |
|마이그레이션에 1 회 비용  <br/> |향후 마이그레이션 당 반복 1 회 비용  <br/> |
|총소유 비용을 낮게 / 유지 관리  <br/> |총소유 비용 감소 높은 / 유지 관리  <br/> |
   
Office 365로 마이그레이션할 때의 1 회는 시간에 두꺼운 비용 걸린 계획, 사전 (데이터를 구성 하 고 클라우드에서 항목과 뒤에 그대로 두려면 기능을 결정 하) 동안 이동 합니다. 그러나 데이터 마이그레이션된 후 업그레이드 됩니다 그 시점부터 자동 경험을 참조 하는 것과 하드웨어 및 소프트웨어 업데이트를 관리 해야하는 더이상 팜의 가동 시간을 백업 하는 Microsoft 서비스 수준 계약 ([SLA](https://go.microsoft.com/fwlink/?linkid=843153)) 하 여 됩니다.
  
### <a name="migrate-to-sharepoint-online"></a>SharePoint Online으로 마이그레이션

SharePoint Online은 연결 된 서비스 설명을 검토 하 여 필요한 모든 기능을 제공 해야 합니다. 다음은 모든 Office 365 서비스 설명에 대 한 링크가입니다.
  
[Office 365 서비스 설명](https://go.microsoft.com/fwlink/?linkid=272060)
  
기준이 직접 마이그레이션할 수 SharePoint Server 2010 (또는 SharePoint Foundation 2010)에서 SharePoint Online에 수단 현재 되지, 수동 작업의 대부분이입니다. 이 귀하에 게 기회 보관 및 잘라내기 데이터 및 이동 하기 전에 더 이상 필요 없는 사이트입니다. 다른 데이터 저장소에 보관할 수 있습니다. 또한는 SharePoint Server 2010도 아니고 SharePoint Foundation 2010이 중단 됩니다 지원의 끝에 관리자는 SharePoint 계속 실행 되 고 데이터의 일부를 이동 하 여 고객 잊어버린 경우 마침표를 가질 수 있도록 해야 합니다.
  
SharePoint Server 2013 또는 SharePoint 서버 2016로 업그레이드 하 고 SharePoint Online에 데이터를 배치 하기로 결정 하는 경우 이동 하려는 [SharePoint 마이그레이션 API](https://support.office.com/en-us/article/Upload-on-premises-content-to-SharePoint-Online-using-PowerShell-cmdlets-555049c6-15ef-45a6-9a1f-a1ef673b867c?ui=en-US&amp;rs=en-US&amp;ad=US) 를 사용 하 여 (비즈니스용 OneDrive에 정보를 마이그레이션할) 작업도 될 수 있습니다. 
  
|**온라인 Pro**|**온라인 사기**|
|:-----|:-----|
|Microsoft는 SPO 하드웨어 및 모든 하드웨어 관리를 제공 합니다.  <br/> |사용할 수 있는 기능을 SharePoint Server 온-프레미스 및 SPO 달라질 수 있습니다.  <br/> |
|구독 라이선스를의 전역 관리자 여야 하 고 SPO 사이트에 관리자를 할당할 수 있습니다.  <br/> |존재 하지 않는 (또는 필요 하지 않은) SharePoint Server 온-프레미스에서 팜 관리자를 사용 하 여 사용할 수 있는 일부 작업 Office 365 있지만 SharePoint 관리에서 SharePoint 관리자 역할, 사이트 모음 관리 하 고 사이트 소유권 서로에 대 한 로컬 사용자 조직  <br/> |
|Microsoft 패치를 적용 하 고, 수정, 기본 하드웨어 및 소프트웨어 (SharePoint Online 실행 되는 SQL 서버 포함)을 업데이트 합니다.  <br/> |서비스의 내부 파일 시스템에 액세스할 수 없습니다 이기 때문에 일부 사용자 지정 제한 됩니다.  <br/> |
|Microsoft는 [서비스 수준 계약](https://go.microsoft.com/fwlink/?linkid=843153) 에 게시 하 고 서비스 수준 보안 문제를 해결 하려면 신속 하 게 이동 합니다.  <br/> |SharePoint Online에서 서비스에 의해 백업, 복원 및 기타 복구 옵션은 자동화-백업을 사용 하지 않으면 덮어쓰게 되어 합니다.  <br/> |
|보안 테스트 및 서버 성능 조정 되는 서비스에 지속적으로에 의해 수행 되 Microsoft 합니다.  <br/> |사용자 인터페이스 및 기타 SharePoint 기능 서비스에 의해 설치 되 고 설정 또는 해제 상태를 전환할 수 해야할 수로 변경 합니다.  <br/> |
|많은 산업 표준을 충족 하는 office 365: [Office 365 규정 준수](https://go.microsoft.com/fwlink/?linkid=843165)합니다.  <br/> |마이그레이션에 대 한 [FastTrack](https://go.microsoft.com/fwlink/?linkid=518597) 지원 제한 됩니다.  <br/> 업그레이드의 대부분이 수동, 됩니다 또는 SPO 마이그레이션 API를 통해 [SharePoint Online 및 OneDrive 마이그레이션에 대 한 콘텐츠 로드맵](https://go.microsoft.com/fwlink/?linkid=843184)설명 합니다.  <br/> |
|Microsoft 기술 지원 엔지니어 아니고 직원 데이터 센터에서 관리에 무제한 액세스할 구독 합니다.  <br/> |하드웨어 인프라의 SharePoint, 최신 버전을 지원 하도록 업그레이드 해야하는 경우 또는 보조 팜 업그레이드를 위해 필요한 경우에 추가 비용 수 있습니다.  <br/> |
|파트너는 SharePoint Online으로 데이터를 마이그레이션하는 일회성 작업 도움이 될 수 있습니다.  <br/> |SharePoint Online을 일부 변경 하면 컨트롤 내에서 됩니다. 마이그레이션 후 메뉴, 라이브러리 및 기타 기능에 대 한 디자인 차이점 사용 가능성에 영향을 일시적으로 될 수 있습니다.  <br/> |
|온라인 제품 기능 사용 중지 될 수 있습니다, 경우에 없는 true 지원 수명 주기 끝을 의미 하는 서비스에서 자동으로 업데이트 됩니다.  <br/> |기본 SQL server와 SharePoint 서버 (또는 SharePoint Foundation)에 대 한 지원 수명 주기를 종료 방법이 있습니다.  <br/> |
   
했을 때 새 Office 365 사이트를 만들 하기로 결정 하 고 수동으로 데이터 마이그레이션을 하 여 필요한 경우에 여기에 Office 365 옵션 오른쪽에 볼 수 있습니다.
  
[Office 365 계획 옵션](https://go.microsoft.com/fwlink/?linkid=843151)
  
### <a name="upgrade-sharepoint-server-on-premises"></a>업그레이드 SharePoint Server 온-프레미스

SharePoint 온-프레미스 제품 (SharePoint Server 2016)에서 최신 버전의 SharePoint 서버 업그레이드는 *연속적으로* 이동 해야, 즉, 직접 SharePoint Server 2016에 SharePoint Server 2010에서 업그레이드 방법은 없습니다. 
  
|||
|:-----|:-----|
||직렬 업그레이드 경로 * * *: SharePoint Server 2010 **\>** SharePoint Server 2013 **\>** SharePoint Server 2016 |
   
SharePoint 2010에서 SharePoint Server 2016에 전체 경로 수행 하는 경우이 시간이 및 계획 합니다. 업그레이드 (주의 SQL 서버 업그레이드도 해야) 업그레이드 된 하드웨어, 소프트웨어 및 관리 측면에서 비용을 포함 합니다. 또한, 사용자 지정 내용 업그레이드, 나도 중단 해야 합니다. SharePoint 서버 팜 업그레이드 하기 전에 모든 중요 한 사용자 지정에서 메모를 수집 하는 확인 해야 합니다.
  
> [!NOTE]
> 프로그램 끝날 지원 SharePoint 2010 팜 유지 관리, SharePoint Server 2016 팜 (-나란히를 실행 하는 별도 팜) 있으므로 새 하드웨어에 설치 하 고 다음 계획 하 고 실행 관련 콘텐츠 (다운로드 하 고 다시에 대 한 콘텐츠를 업로드의 수동 마이그레이션 수 예:)입니다. (예: 문서 2010 있는 수동 이동을 수행 하는 계정의 별칭을 가진 현재 마지막 수정 된 계정에서 들리는), 이러한 수동 이동에 발생할 수 있는 문제 및 시간 보다 먼저 일부 작업을 수행 해야 합니다 (사이트, 하위 사이트, 사용 권한 다시 만들기 및 목록 구조)입니다. 것이 좋은 시간을 데이터 저장소로 또는 더이상 이동할 수 필요한 정보를 고려 합니다. 이 마이그레이션의 영향을 줄일 수 있습니다. 두 방법 모두 사용자의 환경 사전 업그레이드를 정리 합니다. 기존 팜을 업그레이드 하기 전에 기능적 이며 해제 하기 전에 (확인)에 특정 수! 
  
**지원 되는 항목과 지원 되지않는 업그레이드 경로**검토 해야 합니다. 
  
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843156)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843157)
    
**사용자 지정**을 사용 하는 경우에 중요 한 계획을 각 단계에 대 한 업그레이드에에서 있으면 마이그레이션 경로: 
  
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843160)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843162)
    
|**온-프레미스 Pro**|**온-프레미스 사기**|
|:-----|:-----|
|모든 위로 서버 하드웨어에서 SharePoint 팜 (및의 SQL)의 모든 측면의 권한입니다.  <br/> |모든 나누기 및 픽스는 회사의 책임 혼합 환경 시나리오도 제품 지원의 끝에 없는 경우 Microsoft 기술 지원 서비스를 유료 참여할 수 있습니다.  <br/> |
|SharePoint Server의 전체 기능 집합 사용 온-프레미스 하이브리드를 통해 SharePoint Online 구독을 온-프레미스 팜에 연결 하는 옵션입니다.  <br/> |업그레이드 "," 패치 "," 보안 픽스 "," 하드웨어 업그레이드 "및" SharePoint Server 및 해당 SQL 팜의 모든 유지 관리에는 관리 되는 온-프레미스 됩니다.  <br/> |
|SharePoint Online을 사용한 보다 더 많은 사용자 지정 옵션에 대 한 전체 액세스 합니다.  <br/> |[Office 365에서 지원 되는 준수 표준](https://go.microsoft.com/fwlink/?linkid=843165) 수동으로 구성 된 온-프레미스 이어야 합니다.  <br/> |
|보안 테스트 하 고 서버 성능 튜닝, 귀하의 구내 (사용자가 제어)에서 수행 합니다.  <br/> |Office 365 수 기능을 사용할 수 있도록 SharePoint Online는 SharePoint Server 온-프레미스와 상호 운용 되지 않습니다.  <br/> |
|파트너는 마이그레이션에 도움이 되는 다음 버전의 SharePoint Server (이상)에 대 한 데이터만 합니다.  <br/> |SharePoint Online에서 표시 된 대로 SharePoint Server 사이트 [SSL/TLS](https://go.microsoft.com/fwlink/?linkid=843167) 인증서를 자동으로 사용 하지 않습니다.  <br/> |
|명명 규칙, 백업, 복원 및 SharePoint Server 온-프레미스에서 다른 복구 옵션의 전체 제어 합니다.  <br/> |SharePoint Server 온-프레미스 제품 수명 주기를 중요 한입니다.  <br/> |
   
### <a name="upgrade-resources"></a>업그레이드 리소스

하드웨어 및 소프트웨어 요구 사항을 비교 하 여 시작 합니다. 현재 하드웨어에서 업그레이드에 대 한 기본 요구 사항이 충족 하지, 팜 또는 SQL server의 하드웨어를 먼저 업그레이드 해야 하거나 SharePoint Online의 '상록' 하드웨어를 사이트의 일부 비율을 이동 하려고 할 수 있는지를 의미할 수 있습니다는 합니다. 평가 수행한 후 지원 되는 업그레이드 경로 및 메서드를 수행 합니다.
  
- **하드웨어/소프트웨어 요구 사항**: 
    
    [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843206) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843207)
    
- **소프트웨어 경계 및 제한 사항**: 
    
    [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843247) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843248) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843249)
    
- **대 한 업그레이드 프로세스 개요**: 
    
    [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843251) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843252) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843359)
    
### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-sharepoint-server-on-premises"></a>온-프레미스 SharePoint Online 및 SharePoint Server 간의 SharePoint 하이브리드 솔루션 만들기

하이브리드 하는 다른 옵션 (온-프레미스 및 일부 마이그레이션에 대 한 온라인 세계 모두의 최고 될 수 있는 하나 필요), SharePoint Server 2013 또는 2016 팜 SharePoint 하이브리드를 만들려면 SharePoint Online에 연결할 수: SharePoint 하이브리드 솔루션에 대 한 설명 [ ](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx).
  
하이브리드 SharePoint 서버 팜은 마이그레이션 목표를 결정 한 경우 어떤 사이트 및 사용자가 온라인으로 이동 하도록 계획 해야 하 고 온-프레미스 유지 되어야 하는 합니다. 검토 및 SharePoint Server 팜의 콘텐츠 (데이터는 회사에 대 한 높은, 중간 규모 또는 낮음 영향 확인)의 순위 이러한 결정을 내리는에 유용할 수 있습니다. 유일한 작업 SharePoint Online과 공유 하는 것은 (a) 사용자 계정 로그인, 및 SharePoint Server 검색 인덱스 (b)-이 아닐 지우기 사이트에 사용 되는 방식에 보일 때까지 수도 있습니다. 결정 한 경우 회사 나중에 SharePoint Online으로 모든 콘텐츠를 마이그레이션할, 온라인 모든 남은 계정 및 데이터를 이동 하 고 사용자 온-프레미스 팜의 역할을 해제 하 고 관리/관리 하는 SharePoint 팜에서의 Office 365를 통해 수행 됩니다. 해당 시점부터 콘솔입니다.
  
기존 유형의 하이브리드 및 온-프레미스 SharePoint 팜과 Office 365 구독 간의 연결을 구성 하는 방법을 숙지 해야 합니다.
  
하이브리드 SharePoint 팜 작동 하는 방법을 보려면 하나의 좋은 방법은 [Office 365 개발/테스트 환경](https://go.microsoft.com/fwlink/?linkid=843152)만들기 (영문)입니다. 평가판 했거나을 Office 365 구독을 구매한 거 야 쉽게 후 데이터를 마이그레이션할 수 있는 SharePoint Online에서 사이트 모음, 웹, 및 문서 라이브러리를 만드는 (중 하나를 수동으로으로 사용 하 여 마이그레이션 API의 또는-마이그레이션할 경우 내 사이트 콘텐츠-비즈니스용 OneDrive를 하이브리드 마법사를 통해).
  
> [!NOTE]
> SharePoint Server 2010 팜을 업그레이드할 수를 먼저 갖추어야 기억 온-프레미스, 하이브리드 옵션을 사용 하 여 SharePoint Server 2013 또는 SharePoint Server 2016 중 하나입니다. SharePoint Foundation 2010 및 SharePoint Foundation 2013 SharePoint Online을 사용한 하이브리드 연결을 만들 수 없습니다. 
  
## <a name="related-topics"></a>관련 항목

[Office 2007에서 업그레이드 하면 또는 2010 서버와 클라이언트에 도움이 되는 리소스](upgrade-from-office-2010-servers-and-products.md)
  
[SharePoint 2010에서 SharePoint 2013으로의 업그레이드 프로세스 개요](https://technet.microsoft.com/en-us/library/mt493301%28v=office.16%29.aspx)
  
[SharePoint 2010에서 SharePoint 2013으로의 업그레이드 모범 사례](https://technet.microsoft.com/en-us/library/mt493305%28v=office.16%29.aspx)
  
[SharePoint 2013에서 데이터베이스 업그레이드 문제 해결](https://go.microsoft.com/fwlink/?linkid=843195)
  
[업그레이드를 위해 Microsoft 파트너에 대 한 검색](https://go.microsoft.com/fwlink/?linkid=841249)
  
[SharePoint Server 2013에 대해 업데이트된 제품 서비스 정책](https://technet.microsoft.com/en-us/library/mt493253%28v=office.16%29.aspx)
  
[SharePoint Server 2016에 대해 업데이트된 제품 서비스 정책](https://technet.microsoft.com/en-us/library/mt782882%28v=office.16%29.aspx)
  

