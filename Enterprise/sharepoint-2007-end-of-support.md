---
title: SharePoint Server 2007 지원 로드맵 최종본
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 01/28/2019
audience: ITPro
ms.topic: conceptual
f1_keywords:
- vsemail
- MS_WSS_DirectoryManagement
- MS_WSS_ConfigEmail
- globalemailconfig
- configssc
- AppDefToBDC
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- MET150
- OFU120
- SPS150
- OSU140
- WSU120
- OSR120
- SPO160
- PJW120
- SPB160
- OSI150
- OSI160
- BSA160
- OSU160
ms.assetid: ba124775-d5c0-4d68-b88d-8458ad4c3717
description: 2017 년 10 월 10 일에 SharePoint Server 2007에 대 한 지원이 종료 되었습니다. 이 문서를 읽으면 업그레이드 옵션, 문제 해결, 모범 사례, 시스템 요구 사항, 업그레이드 단계 및 Microsoft 파트너 로부터 도움을 받는 방법에 대해 알아볼 수 있습니다.
ms.openlocfilehash: 4054ca5c0b502c2008556021a80d3a939a979bb3
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2019
ms.locfileid: "38030913"
---
# <a name="sharepoint-server-2007-end-of-support-roadmap"></a>SharePoint Server 2007 지원 로드맵 최종본

**2017 년 10 월 10 일**, Microsoft Office SharePoint Server 2007 지원 종료에 도달 했습니다. SharePoint Server 2007에서 Office 365 또는 최신 버전의 SharePoint Server 온-프레미스로 마이그레이션을 시작한 적이 없다면 이제 계획을 시작 하는 데 걸리는 시간입니다. 이 문서에서는 사용자가 데이터를 SharePoint Online으로 마이그레이션하거나 SharePoint Server를 온-프레미스로 업그레이드 하는 데 도움이 되는 리소스에 대해 자세히 설명 합니다. 
  
## <a name="what-does-end-of-support-mean"></a>지원이 끝나는 것은 무엇을 의미 하나요?

SharePoint Server에는 거의 모든 Microsoft 제품과 마찬가지로 Microsoft가 새로운 기능, 버그 수정, 보안 픽스 등을 제공 하는 지원 수명 주기가 있습니다. 일반적으로이 수명 주기는 제품 초기 릴리스 날짜 로부터 10 년 동안 지속 되며이 주기의 끝은 제품의 지원 종료 라고 합니다. 지원 종료 시 Microsoft는 더 이상 다음을 제공 하지 않습니다.
  
- 발생할 수 있는 문제에 대 한 기술 지원
    
- 검색 된 문제와 서버의 안정성 및 유용성에 영향을 줄 수 있는 문제에 대 한 버그 수정
    
- 검색 되 고 서버에서 보안 위반에 취약 해질 수 있는 취약성에 대 한 보안 수정 사항 한 
    
- 표준 시간대 업데이트
    
사용자는 SharePoint Server 2007 팜이 여전히 작업을 수행 하 고 2017이 지난 후에도 더 이상 업데이트, 패치 또는 픽스를 제공 하지 않으며, Microsoft Support는 해당 제품에 대 한 지원 노력을 보다 최신 버전의 제품으로 완전히 이동할 수 있습니다. 설치가 더 이상 지원 되거나 패치 되지 않으므로 지원 되는 방법의 끝으로 제품을 업그레이드 하거나 중요 한 데이터를 마이그레이션해야 합니다.
  
> [!TIP]
> 업그레이드 또는 마이그레이션을 아직 계획 하지 않은 경우에는 [SharePoint 2007 마이그레이션 옵션을 고려 하](sharepoint-2007-migration-options.md)여 시작 위치에 대 한 몇 가지 예를 참조 하세요. 또한 업그레이드 또는 Office 365 마이그레이션 (또는 둘 다)을 통해 도움을 받을 수 있는 [Microsoft 파트너](https://go.microsoft.com/fwlink/?linkid=841249) 를 검색할 수도 있습니다. 
  
지원 종료에 도달 하는 Office 2007 서버에 대 한 자세한 내용은 [office 2007 서버 및 클라이언트에서 업그레이드 하는 데 도움이 되는 리소스를](upgrade-from-office-2007-servers-and-products.md)참조 하십시오.
  
## <a name="what-are-my-options"></a>내 옵션 이란?

첫 번째 중지는 [제품 수명 주기 사이트](https://go.microsoft.com/fwlink/?linkid=843148)여야 합니다. 기한에 해당 하는 온-프레미스 Microsoft 제품을 사용 하는 경우에는 마이그레이션에 필요한 최신 날짜를 확인 하 여 업그레이드 또는 마이그레이션을 예약할 수 있도록, 1 년 이상 동안 마이그레이션을 수행 하는 것이 좋습니다. 다음 단계를 선택 하는 경우 제품 기능에 대 한 적절 하 고 개선 되 고 유용한 것으로 생각 하는 데 도움이 될 수 있습니다. 예를 들면 다음과 같습니다.
  
|**좋습니다**|**바람직합니다**|**방법은**|
|:-----|:-----|:-----|
|SharePoint Server 2010  <br/> |SharePoint Server 2013  <br/> |SharePoint Online  <br/> |
||SharePoint 하이브리드  <br/> |SharePoint Server 2016  <br/> |
|||SharePoint 하이브리드  <br/> |
   
확장의 낮은 끝에서 옵션을 선택 하는 경우에는 SharePoint Server 2007에서 마이그레이션이 완료 된 후에 업그레이드 계획을 시작 해야 합니다. (SharePoint Server 2007에 대 한 지원 종료는 2017입니다. 이러한 날짜는 변경 될 수 있으며 [제품 수명 주기 사이트](https://support.microsoft.com/lifecycle)를 확인 합니다.
  
## <a name="where-can-i-go-next"></a>다음으로 이동할 위치

SharePoint Server는 자체 서버에 온-프레미스로 설치할 수 있거나 Microsoft Office 365의 일부인 온라인 서비스인 SharePoint Online을 사용할 수 있습니다. 다음을 선택할 수 있습니다.
  
- SharePoint Online으로 마이그레이션
    
- SharePoint Server 온-프레미스 업그레이드
    
- 위의 두 작업을 모두 수행 합니다.
    
- [SharePoint 하이브리드](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx) 솔루션 구현 
    
앞으로 또는 사용자 지정 내용을 유지 관리 하거나 마이그레이션하고 SharePoint Server가 의존 하는 하드웨어를 업그레이드 하는 경우 서버 팜 유지 관리와 관련 된 숨겨진 비용을 염두에 두어야 합니다. 필요 하다 면 온-프레미스 SharePoint Server 팜을 사용 하는 것이 rewarding 그렇지 않고 이전 SharePoint 서버에서 팜을 실행 하 여 사용자 지정을 많이 수행 하지 않으면 SharePoint Online으로 계획 된 마이그레이션을 활용할 수 있습니다.
  
> [!IMPORTANT]
> SharePoint 2007의 콘텐츠가 자주 사용 되지 않는 경우에도 다른 옵션을 사용할 수 있습니다. 일부 SharePoint 관리자는 [Office 365 구독을 만들고](https://go.microsoft.com/fwlink/?linkid=843152), 새 sharepoint online 사이트를 설정한 다음, sharepoint 2007에서 새로운 sharepoint online 사이트에 가장 중요 한 문서만을 제거 하도록 선택할 수 있습니다. 여기서는 데이터가 SharePoint 2007 사이트에서 보관 사서함으로 배출 될 수 있습니다. 사용자가 SharePoint 2007 설치 데이터로 데이터 작업을 수행 하는 방법을 생각해 볼 수 있습니다. 이 문제를 해결 하는 방법이 독창적인 경우도 있습니다. 
  
|**SharePoint Online (SPO)**|**SharePoint Server 온-프레미스**|
|:-----|:-----|
|높은 비용 (계획/실행/확인)  <br/> |높은 비용 (계획/실행/확인)  <br/> |
|저렴 한 비용 (하드웨어 구입 없음)  <br/> |자금 비용 (하드웨어 + devs/관리자)  <br/> |
|마이그레이션 1 회 비용  <br/> |향후 마이그레이션 당 1 회 비용 반복  <br/> |
|낮은 총 소유 비용/유지 관리  <br/> |높은 총 소유 비용/유지 관리  <br/> |
   
Office 365로 마이그레이션하면 데이터를 구성 하 고 클라우드로 수행 해야 하는 작업을 결정 하는 동시에 일회성 이동 비용이 더 많이 듭니다. 그러나 업그레이드는 해당 지점부터 자동으로 진행 되며, 더 이상 하드웨어 및 소프트웨어 업데이트를 관리할 필요가 없으며 팜의 최신 시간이[SLA](https://go.microsoft.com/fwlink/?linkid=843153)(서비스 수준 계약)를 통해 지원 됩니다.
  
### <a name="migrate-to-sharepoint-online"></a>SharePoint Online으로 마이그레이션

연결 된 서비스 설명을 검토 하 여 SharePoint Online에 필요한 모든 기능이 있는지 확인 합니다. 다음은 모든 Office 365 서비스 설명에 대 한 링크입니다.
  
[Office 365 서비스 설명](https://go.microsoft.com/fwlink/?linkid=272060)
  
SharePoint 2007에서 SharePoint Online으로 마이그레이션하는 직접적인 방법은 없습니다. SharePoint Online으로 이동 하는 작업은 수동으로 수행 해야 합니다. SharePoint Server 2013 또는 SharePoint Server 2016로 업그레이드 하는 경우 이동 과정에서 SharePoint 마이그레이션 API (예: 비즈니스용 OneDrive로 정보 마이그레이션)를 사용 하는 것이 포함 될 수도 있습니다.
  
|**온라인 Pro**|**온라인 Con**|
|:-----|:-----|
|Microsoft는 SPO 하드웨어 및 모든 하드웨어 관리를 제공 합니다.  <br/> |사용 가능한 기능은 SharePoint Server 온-프레미스와 SPO 간에 다를 수 있습니다.  <br/> |
|구독의 전역 관리자 이며 관리자에 게 SPO 사이트를 할당할 수 있습니다.  <br/> |SharePoint Server 온-프레미스에서 팜 관리자가 사용할 수 있는 일부 작업이 Office 365의 SharePoint 관리자 역할에 포함 되지 않거나 필요 하지 않습니다.  <br/> |
|Microsoft는 기본 하드웨어 및 소프트웨어에 패치, 수정 사항 및 업데이트를 적용 합니다.  <br/> |서비스의 기본 파일 시스템에 대 한 액세스 권한이 없기 때문에 일부 사용자 지정 내용이 제한 됩니다.  <br/> |
|Microsoft는 서비스 수준 [계약](https://go.microsoft.com/fwlink/?linkid=843153) 을 게시 하 고 신속 하 게 이동 하 여 서비스 수준 인시던트를 해결 합니다.  <br/> |백업 및 복원 및 기타 복구 옵션은 SharePoint Online의 서비스에 의해 자동화 되며, 사용 되지 않는 경우에는 백업이 덮어쓰여집니다.  <br/> |
|보안 테스트 및 서버 성능 조정은 Microsoft의 서비스에서 지속적으로 수행 됩니다.  <br/> |사용자 인터페이스 및 기타 SharePoint 기능의 변경 내용은 서비스에 의해 설치 되며 설정 또는 해제 해야 할 수 있습니다.  <br/> |
|Office 365은 다양 한 업계 표준을 충족 합니다 [365](https://go.microsoft.com/fwlink/?linkid=843165).  <br/> |마이그레이션에 대 한 [Fasttrack](https://go.microsoft.com/fwlink/?linkid=518597) 지원은 제한 됩니다.  <br/> 업그레이드의 대부분은 수동 또는 [SharePoint Online 및 OneDrive 마이그레이션 콘텐츠 로드맵](https://go.microsoft.com/fwlink/?linkid=843184)에 설명 된 SPO 마이그레이션 API를 통해 진행 됩니다.  <br/> |
|Microsoft 지원 엔지니어 또는 데이터 센터의 직원은 구독에 대 한 무제한 관리자 액세스 권한을 갖지 않습니다.  <br/> |최신 버전의 SharePoint를 지원 하도록 하드웨어 인프라를 업그레이드 해야 하거나 업그레이드에 보조 팜이 필요한 경우에는 추가 비용이 있을 수 있습니다.  <br/> |
|파트너는 데이터를 SharePoint Online으로 마이그레이션하는 일회성 작업을 지원할 수 있습니다.  <br/> ||
|온라인 제품은 기능에 의해 자동으로 업데이트 되며, 기능은 사용 중지 수 있지만 실제 지원은 제공 되지 않습니다.  <br/> ||
   
새 Office 365 사이트를 만들려고 했으며 필요한 경우 데이터를 수동으로 마이그레이션하는 경우에는 여기에서 Office 365 옵션을 확인할 수 있습니다.
  
[Office 365 계획 옵션](https://go.microsoft.com/fwlink/?linkid=843151)
  
### <a name="upgrade-sharepoint-server-on-premises"></a>SharePoint Server 온-프레미스 업그레이드

과거에는 sharepoint 업그레이드에서 버전을 건너뛰어도 서 SharePoint Server 2016의 릴리스를 제외 하는 방법을 더 이상 제공 하지 않습니다. 즉, 업그레이드가 순차적으로 진행 됨을 의미 합니다.
  
|||
|:-----|:-----|
||SharePoint 2007 | SharePoint Server 2010 | SharePoint Server 2013 | SharePoint Server 2016 |
   
SharePoint 2007에서 SharePoint Server 2016로 전체 경로를 사용 하기 위해서는 상당한 시간이 투자 되 고, 업그레이드 된 하드웨어 측면에서 비용이 수반 됩니다 (SQL server도 업그레이드 해야 한다는 점을 유의 해야 함), 소프트웨어 및 관리를 의미 합니다. 기능의 중요도에 따라 사용자 지정 내용이 업그레이드 되거나 중단 되어야 합니다.
  
> [!NOTE]
> 수명 종료 SharePoint 2007 팜을 유지 관리 하 고, 새 하드웨어에 SharePoint Server 2016 팜을 설치한 다음 (별도의 팜을 나란히 실행), 콘텐츠를 다운로드 하 고 다시 업로드 하기 위해 콘텐츠의 수동 마이그레이션을 계획 및 실행 하는 것이 가능 합니다. 예제) 마지막으로 수정한 계정을 수동으로 이동 하는 계정의 별칭으로 이동 하는 것과 같은 수동 이동의 몇 가지 gotchas, 미리 수행 해야 하는 작업 (예: 사이트, 하위 사이트, 사용 권한 및 목록 다시 만들기)에 대해 알아야 합니다. 구조). 이는 저장소로 이동할 수 있는 데이터를 고려 하거나 더 이상 필요 하지 않은 마이그레이션에 대 한 영향을 줄일 수 있는 작업입니다.
  
두 방법 중 하나를 수행 하 여 업그레이드 전에 환경을 정리 합니다. 업그레이드를 수행 하기 전에 기존 팜이 제대로 작동 하 고 있어야 합니다. 
  
**지원 및 지원 되지 않는 업그레이드 경로**를 검토 해야 합니다. 
  
- [SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843156)
    
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843156)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843157)
    
**사용자 지정**내용이 있는 경우 마이그레이션 경로의 각 단계에 대 한 업그레이드 계획을 수립 하는 것이 중요 합니다. 
  
- [SharePoint 2007](https://go.microsoft.com/fwlink/?linkid=843158)
    
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843160)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843162)
    
|**온-프레미스 Pro**|**온-프레미스 Con**|
|:-----|:-----|
|서버 하드웨어에서 SharePoint 팜의 모든 측면에 대 한 모든 권한  <br/> |모든 휴식 및 수정 사항은 회사의 책임입니다 (제품을 지원 하지 않을 경우 Microsoft가 지 원하는 경우 대금을 지불 해야 할 수 있음).  <br/> |
|하이브리드를 통해 온-프레미스 팜을 SharePoint Online 구독에 연결 하는 옵션을 사용 하는 SharePoint Server 온-프레미스의 전체 기능 집합입니다.  <br/> |업그레이드, 패치, 보안 픽스 및 모든 SharePoint Server의 온-프레미스 유지 관리  <br/> |
|보다 강력한 사용자 지정을 위한 모든 권한  <br/> |[Office 365에서 지 원하는 규정 준수 표준은](https://go.microsoft.com/fwlink/?linkid=843165) 온-프레미스에서 수동으로 구성 해야 합니다.  <br/> |
|온-프레미스에서 수행 되는 보안 테스트 및 서버 성능 조정  <br/> |Office 365은 sharepoint Online에서 SharePoint Server 온-프레미스와 상호 운용 되지 않는 기능을 사용할 수 있도록 합니다.  <br/> |
|파트너는 다음 버전의 SharePoint Server (및 이후)로 데이터 마이그레이션을 지원할 수 있습니다.  <br/> |Sharepoint Server 사이트에서는 SharePoint Online에 표시 되는 대로 [SSL/TLS](https://go.microsoft.com/fwlink/?linkid=843167) 인증서를 자동으로 사용 하지 않습니다.  <br/> |
|SharePoint Server 온-프레미스의 명명 규칙, 백업 및 복원 및 기타 복구 옵션에 대 한 모든 권한  <br/> |SharePoint Server 온-프레미스는 제품 수명 주기에 중요 합니다.  <br/> |
   
### <a name="upgrade-resources"></a>리소스 업그레이드

먼저 하드웨어 및 소프트웨어 요구 사항을 충족 하는지 파악 한 다음 지원 되는 업그레이드 방법을 따릅니다.
  
- 다음 **에 대 한 하드웨어/소프트웨어 요구 사항**: 
    
    [Sharepoint server 2010](https://go.microsoft.com/fwlink/?linkid=843204) | [sharepoint server 2010](https://go.microsoft.com/fwlink/?linkid=843204) | [sharepoint server 2013](https://go.microsoft.com/fwlink/?linkid=843206) | [sharepoint server 2016](https://go.microsoft.com/fwlink/?linkid=843207)
    
- 다음 **에 대 한 소프트웨어 경계 및 제한**사항: 
    
    [Sharepoint server 2007](https://go.microsoft.com/fwlink/?linkid=843245) | [sharepoint server 2010](https://go.microsoft.com/fwlink/?linkid=843247) | [sharepoint server 2013](https://go.microsoft.com/fwlink/?linkid=843248) | [sharepoint server 2016](https://go.microsoft.com/fwlink/?linkid=843249)
    
- **업그레이드 프로세스 개요**: 
    
    [Sharepoint server 2007](https://go.microsoft.com/fwlink/?linkid=843250) | [sharepoint server 2010](https://go.microsoft.com/fwlink/?linkid=843251) | [sharepoint server 2013](https://go.microsoft.com/fwlink/?linkid=843252) | [sharepoint server 2016](https://go.microsoft.com/fwlink/?linkid=843359)
    
### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-on-premises"></a>SharePoint Online과 온-프레미스 간에 SharePoint 하이브리드 솔루션 만들기

마이그레이션 요구 사항에 대 한 대답이 온-프레미스에서 제공 되는 자체 제어와 SharePoint Online에서 제공 하는 소유 비용이 더 많은 경우에는 하이브리드를 통해 SharePoint Server 2013 또는 2016 팜을 SharePoint Online에 연결할 수 있습니다. [SharePoint 하이브리드 솔루션에 대 한 자세한 정보](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx)
  
하이브리드 SharePoint Server 팜이 비즈니스에 이익이 되는 경우 기존 유형의 하이브리드를 숙지 하 고 온-프레미스 SharePoint 팜과 Office 365 구독 간에 연결을 구성 하는 방법에 익숙해져야 합니다.
  
[Office 365 개발/테스트 환경을](https://go.microsoft.com/fwlink/?linkid=843152)만들어 어떻게 작동 하는지 확인할 수 있는 좋은 방법 중 하나입니다. 평가판이 있거나 Office 365 구독을 구매한 후에는 직접 데이터를 마이그레이션할 수 있는 SharePoint Online의 사이트 모음, 웹 및 문서 라이브러리를 만드는 방법, 즉 마이그레이션 API를 사용 하 여 수동으로 또는-My를 마이그레이션하려고 합니다. 하이브리드 마법사를 통해 비즈니스용 OneDrive에 사이트 콘텐츠를 추가할 수 있습니다.
  
> [!NOTE]
> 하이브리드 옵션을 사용 하려면 SharePoint 2007 팜을 온-프레미스에서 SharePoint Server 2013 또는 SharePoint Server 2016로 업그레이드 해야 합니다. 
  
## <a name="related-topics"></a>관련 항목

[업그레이드 문제 해결 및 다시 시작 (Office SharePoint Server 2007)](https://go.microsoft.com/fwlink/?linkid=843192)
  
[업그레이드 문제 해결 (SharePoint Server 2010)](https://go.microsoft.com/fwlink/?linkid=843194)
  
[SharePoint 2013에서 데이터베이스 업그레이드 문제 해결](https://go.microsoft.com/fwlink/?linkid=843195)
  
[업그레이드에 도움이 되는 Microsoft 파트너를 검색 합니다.](https://go.microsoft.com/fwlink/?linkid=841249)
  
[Office 2007 서버 및 클라이언트에서 업그레이드 하는 데 도움이 되는 리소스](upgrade-from-office-2007-servers-and-products.md)
  

