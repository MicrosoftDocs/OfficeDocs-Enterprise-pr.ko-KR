---
title: SharePoint 2010에서 업그레이드
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 2/2/2018
audience: ITPro
ms.topic: conceptual
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- MET150
- WSU140
- OSU140
ms.assetid: 985a357f-6db7-401f-bf7a-1bafdf1f312c
description: SharePoint 2010 및 SharePoint Server 2010는 지원 종료에 가깝습니다. 이 문서를 참조 하 여 SharePoint Online으로 업그레이드 하거나 SharePoint Server 온-프레미스의 최신 버전으로 업그레이드할 수 있습니다.
ms.openlocfilehash: 18522f9abb1514e14a172c6f2d661591826dff22
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070684"
---
# <a name="upgrading-from-sharepoint-2010"></a>SharePoint 2010에서 업그레이드

2020 년 10 월 13 일에는 Microsoft Office SharePoint Server 2010 지원 종료에 도달 했습니다. 이 문서에서는 사용자가 기존 SharePoint Server 2010 데이터를 SharePoint Online으로 마이그레이션하거나 SharePoint Server 온-프레미스를 업그레이드 하는 데 도움이 되는 리소스에 대해 자세히 설명 합니다.
  
## <a name="what-is-end-of-support"></a>지원이 종료 되는 이유는 무엇 인가요?

SharePoint Server 2010 및 SharePoint Foundation 2010 소프트웨어가 지원 수명 주기의 끝 (Microsoft에서 새로운 기능, 버그 수정, 보안 픽스 등을 제공 하는 시간)에 도달 하면이를 소프트웨어의 ' 지원 종료 ' 라고 합니다. 경우에 따라 ' 퇴직 ' 됩니다. 제품 지원 (또는 EOS)의 끝에 따라 실제로 아무 것도 종료 되거나 작동 중지 됩니다. 그러나 소프트웨어 지원이 종료 될 때 Microsoft는 더 이상 다음을 제공 하지 않습니다.
  
- 발생할 수 있는 문제에 대 한 기술 지원
    
- 검색 된 문제와 서버의 안정성 및 유용성에 영향을 줄 수 있는 문제에 대 한 버그 수정
    
- 검색 되 고 서버에서 보안 위반에 취약 해질 수 있는 취약성에 대 한 보안 수정 사항
    
- 표준 시간대 업데이트
    
즉, 보안 패치/수정 사항을 비롯 하 여 제품에 대 한 업데이트, 패치 또는 수정 사항이 더 이상 제공 되지 않으며, Microsoft Support에서 해당 지원 노력을 보다 최신 버전으로 완전히 변경할 수 있게 됩니다. SharePoint Server 2010에 대 한 지원이 종료 되 면 영업 기회를 활용 하 여 제품을 업그레이드 하기 전에 더 이상 필요 하지 않은 데이터를 트리밍 하거나 중요 한 데이터를 마이그레이션하는 것을 고려해 야 합니다.
  
> [!NOTE]
> 일반적으로 소프트웨어 수명 주기는 제품 초기 릴리스 날짜 로부터 10 년 동안 지속 됩니다. 다음 버전의 소프트웨어 또는 Office 365 마이그레이션 (또는 둘 다)으로 업그레이드 하는 데 도움을 받을 수 있는 [Microsoft 파트너](https://go.microsoft.com/fwlink/?linkid=841249) 를 검색할 수 있습니다. 중요 기본 기술에 대 한 지원 종료에 대 한 자세한 내용은 물론, 특히 SharePoint에서 사용 중인 SQL server 버전을 알고 있어야 합니다. 
  
## <a name="what-are-my-options"></a>내 옵션 이란?

먼저 [제품 수명 주기 사이트](https://support.microsoft.com/en-us/lifecycle/search?alpha=SharePoint%20Server%202010)에서 지원이 종료 되는 날짜를 확인 합니다. 다음으로,이 날짜에 대 한 지식이 있는 업그레이드 또는 마이그레이션 시간을 계획 해야 합니다. 제품은 나열 된 날짜에는 *중지 되지* 않으며, 해당 날짜 이후에는 설치에 더 이상 패치가 적용 되지 않으므로 다음 버전으로 보다 원활 하 게 전환할 수 있도록 하는 전략이 필요 합니다. 합니다. 
  
이 매트릭스는 제품 기능 및 사용자 데이터를 마이그레이션할 때 코스를 그리는 데 도움이 됩니다.
  
|**지원 종료 제품**|**좋습니다**|**방법은**|
|:-----|:-----|:-----|
|SharePoint Server 2010  <br/> |SharePoint Server 2013  <br/> |SharePoint Online  <br/> |
||SharePoint 하이브리드  <br/> |SharePoint Server 2016 (온-프레미스)  <br/> |
|||SharePoint 클라우드 하이브리드 검색  <br/> |
   
확장의 낮은 끝에 있는 옵션을 선택 하는 경우 (좋은 옵션) SharePoint Server 2010에서 마이그레이션한 후에 다른 업그레이드 계획을 시작 해야 합니다. (SharePoint Server 2010 및 SharePoint Foundation 2010에 대 한 지원 종료는 2020 년 10 월 13 일에 ** 예정 되어 있지만, 항상 가장 정확한 날짜에 대 한 [제품 수명 주기 사이트](https://support.microsoft.com/en-us/lifecycle) 를 확인 해야 합니다.) 
  
## <a name="where-should-i-go-next"></a>다음으로 이동 해야 하는 위치

SharePoint Server 2013 및 SharePoint Foundation 2013은 자체 서버에 온-프레미스로 설치할 수 있습니다. 그렇지 않으면 Microsoft Office 365의 일부인 온라인 서비스인 SharePoint Online을 사용할 수 있습니다. 다음을 선택할 수 있습니다.
  
- SharePoint Online으로 마이그레이션
    
- SharePoint Server 또는 SharePoint Foundation 온-프레미스 업그레이드
    
- 위의 두 작업을 모두 수행 합니다.
    
- [SharePoint 하이브리드](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx) 솔루션 구현 
    
앞으로 또는 사용자 지정 내용을 유지 관리 하거나 마이그레이션하고 SharePoint Server가 의존 하는 하드웨어를 업그레이드 하는 경우 서버 팜 유지 관리와 관련 된 숨겨진 비용을 염두에 두어야 합니다. 이러한 모든 것을 알고 있고 이러한 모든 사항을 고려 하 고 있다면 온-프레미스 업그레이드를 계속 하는 것이 더 쉽습니다. 그렇지 않으면 이전 버전의 사용자 지정을 수행 하지 않고 팜을 레거시 SharePoint 서버에서 실행 하는 경우 계획 된 마이그레이션에서 SharePoint Online으로의 이점을 누릴 수 있습니다. 또한 온-프레미스 SharePoint Server 상점에서 모든 데이터를 온-프레미스로 유지 하는 하드웨어 관리의 양을 줄이기 위해 일부 데이터를 SharePoint Online에 추가 하도록 선택할 수 있습니다. 일부 데이터를 SharePoint Online으로 이동 하는 것이 보다 경제적입니다.
  
> [!NOTE]
> SharePoint 관리자는 [Office 365 구독을 만들고](https://go.microsoft.com/fwlink/?linkid=843152), 새 sharepoint online 사이트를 설정한 다음, sharepoint Server 2010에서 새로운 sharepoint online 사이트에 가장 중요 한 문서만을 제거 하는 작업을 완전히 잘라낼 수 있습니다. 여기서는 남아 있는 모든 데이터를 SharePoint Server 2010 사이트에서 온-프레미스 보관으로도 제거할 수 있습니다. 
  
|**SharePoint Online (SPO)**|**SharePoint Server 온-프레미스**|
|:-----|:-----|
|높은 비용 (계획/실행/확인)  <br/> |높은 비용 (계획/실행/확인)  <br/> |
|저렴 한 비용 (하드웨어 구입 없음)  <br/> |자금 비용 (하드웨어 구입)  <br/> |
|마이그레이션 1 회 비용  <br/> |향후 마이그레이션 당 1 회 비용 반복  <br/> |
|낮은 총 소유 비용/유지 관리  <br/> |높은 총 소유 비용/유지 관리  <br/> |
   
Office 365로 마이그레이션할 때 일회성 이동은 계획, 업, 즉 데이터를 구성 하 고 클라우드로 가져올 항목을 결정 하는 데 소요 되는 비용이 더 많아집니다. 그러나 데이터를 마이그레이션한 후에는 해당 지점부터 업그레이드를 자동으로 진행 하며, 하드웨어 및 소프트웨어 업데이트를 더 이상 관리할 필요가 없으며 팜의 가동 시간이 Microsoft[SLA](https://go.microsoft.com/fwlink/?linkid=843153)(서비스 수준 계약)를 통해 지원 됩니다.
  
### <a name="migrate-to-sharepoint-online"></a>SharePoint Online으로 마이그레이션

연결 된 서비스 설명을 검토 하 여 SharePoint Online에서 필요한 모든 기능을 제공 해야 합니다. 다음은 모든 Office 365 서비스 설명에 대 한 링크입니다.
  
[Office 365 서비스 설명](https://go.microsoft.com/fwlink/?linkid=272060)
  
현재로 서는 SharePoint Server 2010 (또는 SharePoint Foundation 2010)에서 SharePoint Online으로 직접 마이그레이션하는 방법을 사용할 수 있으므로 대부분의 작업은 수동입니다. 이렇게 하면 이동 하기 전에 더 이상 필요 하지 않은 데이터 및 사이트를 보관 하 고 잘라낼 수 있습니다. 다른 데이터를 저장소에 보관할 수 있습니다. 또한 SharePoint Server 2010 또는 SharePoint Foundation 2010은 지원 종료 시에 중지 되지 않으며, 관리자가 일부 데이터를 이동 하는 것을 잊은 경우에는 SharePoint가 계속 실행 되는 기간을 확인할 수 있습니다.
  
Sharepoint Server 2013 또는 SharePoint Server 2016로 업그레이드 하 고 데이터를 SharePoint Online에 추가 하기로 결정 하는 경우에는 이동 과정에서 [Sharepoint 마이그레이션 API](https://support.office.com/en-us/article/Upload-on-premises-content-to-SharePoint-Online-using-PowerShell-cmdlets-555049c6-15ef-45a6-9a1f-a1ef673b867c?ui=en-US&amp;rs=en-US&amp;ad=US) (비즈니스용 OneDrive로 정보 마이그레이션)를 사용 해야 할 수도 있습니다. 
  
|**온라인 Pro**|**온라인 Con**|
|:-----|:-----|
|Microsoft는 SPO 하드웨어 및 모든 하드웨어 관리를 제공 합니다.  <br/> |사용 가능한 기능은 SharePoint Server 온-프레미스와 SPO 간에 다를 수 있습니다.  <br/> |
|구독의 전역 관리자 이며 관리자에 게 SPO 사이트를 할당할 수 있습니다.  <br/> |Office 365의 SharePoint 관리자 역할에서 sharepoint Server 온-프레미스의 팜 관리자가 사용할 수 있는 일부 작업은 존재 하지 않거나 필요 하지 않지만 SharePoint 관리, 사이트 모음 관리 및 사이트 소유권은 다음과 같습니다. 조직.  <br/> |
|Microsoft는 기본 하드웨어 및 소프트웨어 (SharePoint Online이 실행 되는 SQL server 포함)에 패치, 수정 사항 및 업데이트를 적용 합니다.  <br/> |서비스의 기본 파일 시스템에 대 한 액세스 권한이 없기 때문에 일부 사용자 지정 내용이 제한 됩니다.  <br/> |
|Microsoft는 서비스 수준 [계약](https://go.microsoft.com/fwlink/?linkid=843153) 을 게시 하 고 신속 하 게 이동 하 여 서비스 수준 인시던트를 해결 합니다.  <br/> |백업 및 복원 및 기타 복구 옵션은 SharePoint Online의 서비스에 의해 자동화 되며, 사용 되지 않는 경우에는 백업이 덮어쓰여집니다.  <br/> |
|보안 테스트 및 서버 성능 조정은 Microsoft의 서비스에서 지속적으로 수행 됩니다.  <br/> |사용자 인터페이스 및 기타 SharePoint 기능의 변경 내용은 서비스에 의해 설치 되며 설정 또는 해제 해야 할 수 있습니다.  <br/> |
|Office 365은 다양 한 업계 표준을 충족 합니다 365.  <br/> |마이그레이션에 대 한 [Fasttrack](https://go.microsoft.com/fwlink/?linkid=518597) 지원은 제한 됩니다.  <br/> 업그레이드의 대부분은 수동 또는 [SharePoint Online 및 OneDrive 마이그레이션 콘텐츠 로드맵](https://go.microsoft.com/fwlink/?linkid=843184)에 설명 된 SPO 마이그레이션 API를 통해 진행 됩니다.  <br/> |
|Microsoft 지원 엔지니어 또는 데이터 센터의 직원은 구독에 대 한 무제한 관리자 액세스 권한을 갖지 않습니다.  <br/> |최신 버전의 SharePoint를 지원 하도록 하드웨어 인프라를 업그레이드 해야 하거나 업그레이드에 보조 팜이 필요한 경우에는 추가 비용이 있을 수 있습니다.  <br/> |
|파트너는 데이터를 SharePoint Online으로 마이그레이션하는 일회성 작업을 지원할 수 있습니다.  <br/> |일부 SharePoint Online 변경 내용은 사용자의 컨트롤 내에 포함 되지 않습니다. 마이그레이션 후 메뉴, 라이브러리 및 기타 기능의 디자인 차이점은 사용 편리성에 일시적으로 영향을 줄 수 있습니다.  <br/> |
|온라인 제품은 기능에 의해 자동으로 업데이트 되는 반면, 기능은 사용 중지 수 있지만 실제 지원 수명 주기가 끝나지 않는다는 것을 의미 합니다.  <br/> |기본 SQL server 및 SharePoint Server (또는 SharePoint Foundation)에 대 한 지원 기간이 종료 되었습니다.  <br/> |
   
새 Office 365 사이트를 만들려고 했으며 필요한 경우 데이터를 수동으로 마이그레이션하는 경우에는 여기에서 Office 365 옵션을 확인할 수 있습니다.
  
[Office 365 계획 옵션](https://go.microsoft.com/fwlink/?linkid=843151)
  
### <a name="upgrade-sharepoint-server-on-premises"></a>SharePoint Server 온-프레미스 업그레이드

최신 버전의 SharePoint 온-프레미스 제품 (SharePoint Server 2016) 중에서 SharePoint server 업그레이드는 *순차적* 으로 수행 되어야 하며, 따라서 sharepoint server 2010에서 sharepoint server 2016으로 직접 업그레이드할 방법이 없습니다. 
  
|||
|:-----|:-----|
||직렬 업그레이드 경로 * * * *: SharePoint Server 2010 **\>** sharepoint server 2013 **\>** sharepoint server 2016 |
   
SharePoint 2010에서 SharePoint Server 2016로의 전체 경로를 따르도록 선택한 경우 시간 및 계획이 계획 됩니다. 업그레이드에는 업그레이드 된 하드웨어 측면에서 비용이 소요 됩니다 (SQL server도 업그레이드 해야 한다는 점을 염두에 두어야 함), 소프트웨어 및 관리를 포함 합니다. 또한 사용자 지정 내용을 업그레이드 하거나 중단 해야 할 수도 있습니다. SharePoint Server 팜을 업그레이드 하기 전에 모든 중요 한 사용자 지정 내용에 대 한 메모를 수집 해야 합니다.
  
> [!NOTE]
> SharePoint 2010 팜 지원 종료를 유지 하 고, 새 하드웨어에 SharePoint Server 2016 팜을 설치한 다음 (별도의 팜을 나란히 실행), 콘텐츠를 다운로드 하 고 다시 업로드 하기 위해 콘텐츠의 수동 마이그레이션을 계획 및 실행 하는 것이 가능 합니다. 예제) 이러한 수동 이동에 대 한 잠재적인 주의 사항 (예: 2010부터 수동 이동을 수행 하는 계정의 별칭을 사용 하 여 마지막으로 수정한 계정이 있음)이 있으며, 몇 가지 작업을 미리 수행 해야 합니다 (사이트, 하위 사이트, 사용 권한 및 목록 구조). 저장소로 이동할 수 있거나 더 이상 필요 하지 않은 데이터를 고려 하는 것이 좋습니다. 이렇게 하면 마이그레이션의 영향을 줄일 수 있습니다. 두 방법 중 하나를 수행 하 여 업그레이드 전에 환경을 정리 합니다. 업그레이드를 수행 하기 전에 기존 팜이 제대로 작동 하 고 있어야 합니다. 
  
**지원 및 지원 되지 않는 업그레이드 경로**를 검토 해야 합니다. 
  
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843156)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843157)
    
**사용자 지정**내용이 있는 경우 마이그레이션 경로의 각 단계에 대 한 업그레이드 계획을 수립 하는 것이 중요 합니다. 
  
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843160)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843162)
    
|**온-프레미스 Pro**|**온-프레미스 Con**|
|:-----|:-----|
|서버 하드웨어에서 SharePoint 팜의 모든 측면과 SQL을 완벽 하 게 제어할 수 있습니다.  <br/> |모든 휴식 및 수정 사항은 회사의 책임 이지만, 제품이 지원 되지 않는 경우에는 Microsoft Support를 지불한 것이 좋습니다.  <br/> |
|하이브리드를 통해 온-프레미스 팜을 SharePoint Online 구독에 연결 하는 옵션을 사용 하는 SharePoint Server 온-프레미스의 전체 기능 집합입니다.  <br/> |업그레이드, 패치, 보안 픽스, 하드웨어 업그레이드 및 모든 SharePoint Server 및 해당 SQL 팜의 유지 관리는 온-프레미스에서 관리 됩니다.  <br/> |
|SharePoint Online 보다 더 강력한 사용자 지정 옵션에 대 한 모든 권한  <br/> |[Office 365에서 지 원하는 규정 준수 표준은](https://go.microsoft.com/fwlink/?linkid=843165) 온-프레미스에서 수동으로 구성 해야 합니다.  <br/> |
|보안 테스트 및 서버 성능 조정 (컨트롤 아래)에서 온-프레미스에 수행 됩니다.  <br/> |Office 365은 sharepoint Online에서 SharePoint Server 온-프레미스와 상호 운용 되지 않는 기능을 사용할 수 있도록 합니다.  <br/> |
|파트너는 다음 버전의 SharePoint Server (및 이후)로 데이터 마이그레이션을 지원할 수 있습니다.  <br/> |Sharepoint Server 사이트에서는 SharePoint Online에 표시 되는 대로 [SSL/TLS](https://go.microsoft.com/fwlink/?linkid=843167) 인증서를 자동으로 사용 하지 않습니다.  <br/> |
|SharePoint Server 온-프레미스의 명명 규칙, 백업 및 복원 및 기타 복구 옵션에 대 한 모든 권한  <br/> |SharePoint Server 온-프레미스는 제품 수명 주기에 중요 합니다.  <br/> |
   
### <a name="upgrade-resources"></a>리소스 업그레이드

먼저 하드웨어 및 소프트웨어 요구 사항을 비교 합니다. 현재 하드웨어의 업그레이드에 대 한 기본 요구 사항을 충족 하지 않는 경우에는 먼저 팜 또는 SQL server의 하드웨어를 업그레이드 해야 하거나 사이트의 일부 비율을 SharePoint Online의 ' c ' 하드웨어로 이동 하는 것을 결정할 수 있습니다. 평가를 마친 후에는 지원 되는 업그레이드 경로와 방법을 따릅니다.
  
- 다음 **에 대 한 하드웨어/소프트웨어 요구 사항**: 
    
    [Sharepoint server 2010](https://go.microsoft.com/fwlink/?linkid=843204) | [sharepoint server 2013](https://go.microsoft.com/fwlink/?linkid=843206) | [sharepoint server 2016](https://go.microsoft.com/fwlink/?linkid=843207)
    
- 다음 **에 대 한 소프트웨어 경계 및 제한**사항: 
    
    [Sharepoint server 2010](https://go.microsoft.com/fwlink/?linkid=843247) | [sharepoint server 2013](https://go.microsoft.com/fwlink/?linkid=843248) | [sharepoint server 2016](https://go.microsoft.com/fwlink/?linkid=843249)
    
- **업그레이드 프로세스 개요**: 
    
    [Sharepoint server 2010](https://go.microsoft.com/fwlink/?linkid=843251) | [sharepoint server 2013](https://go.microsoft.com/fwlink/?linkid=843252) | [sharepoint server 2016](https://go.microsoft.com/fwlink/?linkid=843359)
    
### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-sharepoint-server-on-premises"></a>Sharepoint Online과 SharePoint Server 온-프레미스 간에 SharePoint 하이브리드 솔루션을 만듭니다.

다른 옵션 (일부 마이그레이션 요구에 대해 온-프레미스 및 온라인 환경 모두에서 가장 적합 함)이 하이브리드 인 경우 sharepoint Server 2013 또는 2016 팜을 sharepoint Online에 연결 하 여 sharepoint 하이브리드를 만들 수 있습니다. [sharepoint 하이브리드 솔루션에 대해 알아보기 ](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx).
  
하이브리드 SharePoint Server 팜이 마이그레이션 목표 인지를 결정 한 경우 온라인으로 이동 해야 하는 사이트와 사용자 및 온-프레미스를 유지 해야 하는 위치를 계획 해야 합니다. SharePoint Server 팜의 콘텐츠를 검토 하 고 순위를 결정 하는 것 (회사에 대 한 높은, 중간 또는 낮은 영향 확인)은이 결정을 내리는 데 도움이 될 수 있습니다. SharePoint Online과 공유 해야 하는 경우에는 (a) 로그인을 위한 사용자 계정, 그리고 (b) SharePoint Server 검색 인덱스--사이트가 사용 되는 방식을 확인할 때까지 명확 하지 않을 수 있습니다. 나중에 회사에서 모든 콘텐츠를 SharePoint Online으로 마이그레이션하는 경우 나머지 모든 계정 및 데이터를 온라인으로 이동 하 고 온-프레미스 팜을 해제할 수 있으며 SharePoint 팜의 관리/관리가 Office 365를 통해 수행 됩니다. 이 시점부터의 콘솔
  
기존 유형의 하이브리드를 숙지 하 고 온-프레미스 SharePoint 팜과 Office 365 구독 간의 연결을 구성 하는 방법에 대해 잘 알고 있어야 합니다.
  
하이브리드 SharePoint 팜이 작동 하는 방식을 확인 하는 좋은 방법 중 하나는 [Office 365 개발/테스트 환경을](https://go.microsoft.com/fwlink/?linkid=843152)만드는 것입니다. 평가판이 있거나 Office 365 구독을 구매한 후에는 직접 데이터를 마이그레이션할 수 있는 SharePoint Online의 사이트 모음, 웹 및 문서 라이브러리를 만드는 방법, 즉 마이그레이션 API를 사용 하 여 수동으로 또는-My를 마이그레이션하려고 합니다. 하이브리드 마법사를 통해 비즈니스용 OneDrive에 사이트 콘텐츠를 추가할 수 있습니다.
  
> [!NOTE]
> SharePoint Server 2010 팜은 먼저 하이브리드 옵션을 사용 하도록 sharepoint server 2013 또는 SharePoint Server 2016에 대해 온-프레미스로 업그레이드 해야 합니다. Sharepoint Foundation 2010 및 SharePoint Foundation 2013에서는 SharePoint Online과의 하이브리드 연결을 만들 수 없습니다. 
  
## <a name="related-topics"></a>관련 항목

[Office 2007 또는 2010 서버 및 클라이언트에서 업그레이드 하는 데 도움이 되는 리소스](upgrade-from-office-2010-servers-and-products.md)
  
[Overview of the upgrade process from SharePoint 2010 to SharePoint 2013](https://technet.microsoft.com/en-us/library/mt493301%28v=office.16%29.aspx)
  
[SharePoint 2010에서 SharePoint 2013으로의 업그레이드 모범 사례](https://technet.microsoft.com/en-us/library/mt493305%28v=office.16%29.aspx)
  
[SharePoint 2013에서 데이터베이스 업그레이드 문제 해결](https://go.microsoft.com/fwlink/?linkid=843195)
  
[업그레이드에 도움이 되는 Microsoft 파트너를 검색 합니다.](https://go.microsoft.com/fwlink/?linkid=841249)
  
[SharePoint Server 2013에 대해 업데이트된 제품 서비스 정책](https://technet.microsoft.com/en-us/library/mt493253%28v=office.16%29.aspx)
  
[SharePoint Server 2016에 대해 업데이트된 제품 서비스 정책](https://technet.microsoft.com/en-us/library/mt782882%28v=office.16%29.aspx)
  

