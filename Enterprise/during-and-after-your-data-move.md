---
title: 데이터 이동 도중 및 이후
ms.author: deniseb
author: denisebmsft
manager: laurawi
ms.date: 03/15/2019
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
search.appverid:
- MET150
localization_priority: Normal
ms.assetid: f47e3e09-b1dc-4b80-b6ea-fd6e0933407f
description: 데이터 이동은 최종 사용자에게 최소의 영향만 미치는 백 엔드 작업입니다. Microsoft에서 사용자의 테넌트의 각 서비스 및 연결된 데이터를 새 데이터 센터 지역으로 이동하는 동안 필요한 작업은 없습니다. 사용자에게 최소한의 영향만 미치면서, 백그라운드에서 사전에 데이터 전송 및 유효성 검사가 진행됩니다.
ms.openlocfilehash: 7635de71e207ff01b24b8b8df8664e3f57f395cf
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487234"
---
# <a name="during-and-after-your-data-move"></a>데이터 이동 도중 및 이후

데이터 이동은 최종 사용자에게 최소의 영향만 미치는 백 엔드 작업입니다. Microsoft에서 사용자의 테넌트의 각 서비스 및 연결된 데이터를 새 데이터 센터 지역으로 이동하는 동안 필요한 작업은 없습니다. 사용자에게 최소한의 영향만 미치면서, 백그라운드에서 사전에 데이터 전송 및 유효성 검사가 진행됩니다.
  
> [!NOTE]
> 서비스마다 다른 시간에 이동이 발생합니다. 결과적으로 다른 시간에 각 서비스의 기능이 제한된다는 설명이 표시될 수 있습니다. 
  
각 Exchange Online, SharePoint Online 및 비즈니스용 Skype에 대한 이동이 완료되면 Office 365 메시지 센터에서 확인 알림을 찾아보세요. 아래 표에 표시된 것처럼, 등록 기간이 끝나고 특정 지역의 모든 고객에 대해 요청된 모든 데이터 이동을 완료하는 데 24개월까지 걸릴 수 있습니다. 이동 후 테 넌 트에 문제가 표시 되는 경우 [Office 365 지원](https://go.microsoft.com/fwlink/p/?LinkID=522459) 서비스에 문의 하 여 도움을 받으십시오. 
  

|**고객의 대금 청구 주소**|**모든 이동 완료 시기**|
|:-----|:-----|
|오스트레일리아, 뉴질랜드, 피지  <br/> |2017년 10월 31일  <br/> |
|일본  <br/> |2018년 10월 31일  <br/> |
|인도  <br/> |2018년 10월 31일  <br/> |
|캐나다  <br/> |2019 년 6 월 30 일  <br/> |
|대한민국  <br/> |2018년 10월 31일  <br/> |
|영국  <br/> |2019년 9월 15일  <br/> |
|프랑스  <br/> |2020년 9월 15일  <br/> |
|아랍에미리트  <br/> |발표할  <br/> |
|남아프리카 공화국  <br/> |발표할  <br/> |
   
## <a name="exchange-online"></a>Exchange Online

각 사용자를 새 데이터 센터 지역으로 이동하는 데 시간이 걸리므로 일부 사용자는 다른 사용자가 새 데이터 센터 지역으로 이동되는 동안 이전 데이터 센터 지역에 계속 남아 있게 됩니다. 즉, 여러 사서함에 액세스 하는 기능 중 일부는 지난 주까지 이동 프로세스를 진행 하는 동안 제대로 작동 하지 않을 수 있습니다. 이러한 기능은 다음 섹션에 설명되어 있습니다.
  
### <a name="open-shared-folder-in-outlook-web-access"></a>Outlook Web Access에서 "공유 폴더" 열기 

일부 사용자는 "공유 폴더" 기능을 사용 하 여 Outlook Web Access에서 다른 사서함 (사용자가 읽기 또는 쓰기 권한을 가진 공유 메일 폴더)을 엽니다. 다음 표에서는 사서함을 이동 하는 동안 공유 폴더에 대 한 액세스를 작동 하는 방법을 설명 합니다. 공유 사서함에 대한 모든 권한이 있는 사용자는 이동하는 동안 Outlook Web Access를 사용하여 사서함을 열 수 있습니다. 
  
|**구성**|**설명**|
|:-----|:-----|
|사용자에게 다른 사서함에 대한 사서함 폴더 권한이 있음  <br/> |제한될 수 있습니다.  <br/> 사용자 a와 사서함 b가 테 넌 트 이동 중에 같은 지역에 있지 않은 경우 사용자 a는 사서함 b의 특정 폴더에 대 한 사용 권한이 있는 경우 Outlook Web Access에서 사서함 b의 폴더를 열 수 없습니다.  <br/> 공유 폴더를 추가하려면 왼쪽 탐색 패널에서 사용자 이름을 마우스 오른쪽 단추로 클릭하고 **공유 폴더 추가**를 선택합니다.  <br/> |
|사용자에게 다른 사서함에 대한 모든 사서함 권한이 있음  <br/> |완전히 지원됩니다.  <br/> 사용자 a에 게 사서함 b에 대 한 "모든 권한" 권한이 있으면 사용자 a가 Outlook Web Access의 왼쪽 탐색 패널에서 공유 폴더를 클릭 하 여 사서함 b가 표시 된 창을 열 수 있습니다.  사용자는 부정적인 영향을 주지 않으면 서 이동 하는 동안 Outlook Web Access를 사용 하 여 공유 사서함을 열 수 있습니다. 이러한 제한 사항은 사서함의 폴더 수준 공유에만 적용됩니다.           |
   
### <a name="public-folders"></a>공용 폴더

공용 폴더 사서함이 액세스 하려고 하는 사용자가 다른 데이터 센터 지역에 일시적으로 있는 경우 사용자가 공용 폴더 사서함에 액세스 하지 못할 수 있습니다. 
  
### <a name="online-archives"></a>온라인 보관 파일

이동이 진행 되는 동안 Outlook for Mac을 통해 연결 하는 사용자가 자신의 온라인 보관 사서함에 연결 하지 못할 수 있습니다. outlook 및 outlook Web Access를 사용 하 여 연결 하는 사용자의 보관 사서함에 대 한 액세스를 지원 합니다.
  
## <a name="sharepoint-online"></a>SharePoint Online

SharePoint Online이 이동 될 때 다음 서비스에 대 한 데이터도 이동 됩니다.
  
- 비즈니스용 OneDrive
    
- Project Online
    
- Project for Office 365
    
- Office 365 비디오 서비스
    
- Office Online
    
- Office 365 ProPlus
    
- Visio Pro for Office 365
    
SharePoint Online 데이터 이동을 완료 한 후에는 다음과 같은 몇 가지 효과를 확인할 수 있습니다.
  
### <a name="office-365-video-services"></a>Office 365 비디오 서비스

- 비디오에서는 SharePoint Online에서 콘텐츠의 나머지 부분에 대 한 이동을 보다 긴 데이터 이동합니다.
    
- SharePoint Online 콘텐츠를 이동한 후에는 비디오를 재생할 수 없을 때 시간 프레임이 나타납니다.
    
- 이전 데이터 센터에서 코드 변환된 복사본을 제거한 후 새로운 데이터 센터에서 다시 코드 변환을 수행하기 때문입니다.
    
### <a name="search"></a>검색

SharePoint Online 데이터를 이동 하는 과정에서 검색 인덱스 및 검색 설정을 새 위치로 마이그레이션합니다. SharePoint Online 데이터 **** 를 이동할 때까지 계속 해 서 사용자에 게 원래 위치에 있는 인덱스를 처리 합니다. SharePoint Online 데이터 이동이 완료 된 후 새 위치에서 검색을 통해 콘텐츠 크롤링이 자동으로 시작 됩니다. 이 시점부터는 마이그레이션된 인덱스에서 고객의 사용자에게 서비스를 제공합니다. 마이그레이션 후 발생하는 콘텐츠 변경 내용은 크롤링하기 전까지 마이그레이션된 인덱스에 포함되지 않습니다. 대부분의 고객은 SharePoint Online 데이터 이동을 완료 한 후 결과가 최신이 아닌 것을 알 수 없지만, 일부 고객의 경우 처음 24-48 시간 동안 최신 상태를 유지 하는 경우가 있습니다. 
  
영향을 받는 기능은 다음과 같습니다.
  
- 검색 결과 및 검색 웹 파트: 마이그레이션 후 발생한 변경 내용은 크롤링하기 전까지 결과에 포함되지 않습니다. 
    
- Delve: 마이그레이션 후 발생한 변경 내용은 크롤링하기 전까지 Delve에 포함되지 않습니다.
    
- 사이트에 대 한 인기 및 검색 보고서: 새 위치에 있는 Excel 보고서의 수에는 SharePoint Online 데이터 이동이 완료 된 후에 실행 된 사용 현황 보고서의 마이그레이션 수와 카운트만 포함 됩니다. 중간 기간의 모든 수는 손실되며 복구할 수 없습니다. 이 기간은 일반적으로 이틀 정도입니다. 일부 고객은 손실되는 기간이 더 짧거나 길 수도 있습니다.
    
- 비디오 포털: 비디오 포털의 조회수 및 통계는 Excel 보고서 통계에 따라 달라지므로 Excel 보고서의 손실 기간만큼 비디오 포털에 대한 조회수 및 통계가 손실됩니다.
    
- eDiscovery: 마이그레이션하는 동안 변경된 항목은 크롤링하기 전까지 표시되지 않습니다.
    
- DLP(데이터 손실 방지): 항목의 변경 내용을 크롤링하기 전까지는 항목에 정책이 적용되지 않습니다.
    
## <a name="skype-for-business"></a>비즈니스용 Skype

단독형 마이그레이션 동안 비즈니스용 Skype 클라이언트 소프트웨어에서 모든 사용자가 로그아웃됩니다. 자동 로그인이 수행되면서 2분 내에 사용자가 다시 연결됩니다.
  
|**전체 이동 중에 작동 하는 기능**|**이동 중에 제한 될 수 있는 기능**|
|:-----|:-----|
| 인스턴트 메시징 및 음성 통화  <br/>  사용자는 대화 상대를 추가하고, 대화 상대 그룹을 추가하고, 모임을 추가하고, 위치를 설정하고, "새로운 소식"을 변경할 수 있습니다.  <br/>  ACP(오디오 회의 공급자) 설정은 대상 데이터 센터 지역으로 복사됩니다. ACP 공급자가 대상 데이터 센터에 있으면 작동하고, 그렇지 않으면 작동하지 않습니다.  <br/> | 관리자는 테넌트 관리자 TRPS(테넌트 원격 PowerShell)를 사용하여 세션을 만들 수 없습니다.  <br/>  관리자는 테넌트 관리자 LAC를 사용하여 로그인하고 사용자 설정을 변경할 수 없습니다.  <br/> |
   
|**이동 후**|
|:-----|
| 모임 데이터(업로드된 프레젠테이션 등)는 이동되지 않으므로 다시 업로드해야 합니다.  <br/>  Lync 2010 클라이언트 및 Mac 2011용 Lync 클라이언트와 같은 이전 버전의 Lync 클라이언트는 DNS 정보를 서비스로 캐시하여 로그인 문제를 일으키는 것으로 알려져 있습니다. 사용자가 최신 비즈니스용 Skype Windows 클라이언트를 사용하지 않는 경우 DNS 캐시를 지워야 할 수 있습니다. 사용자에 게 [문제 해결 마법사](https://support.microsoft.com/en-us/kb/2541980) 를 실행 하도록 요청 하 고 클라이언트 캐시를 지우는 방법에 대 한 지침을 따릅니다. Mac 용 Lync 클라이언트 사용자는 [다음 지침](https://support.microsoft.com/en-us/kb/2629861)을 따라야 합니다.  <br/> |
   
### <a name="skype-for-business-moves-that-involve-a-third-party-audio-conferencing-provider"></a>타사 오디오 회의 공급자를 포함 하는 비즈니스용 Skype 이동
새로운 지역별 데이터 센터에 소속된 사용자는 비즈니스용 Skype에 대한 타사 오디오 회의 공급자 추가 기능 서비스를 사용할 수 없습니다.   타사 오디오 회의 공급자 서비스를 사용하는 기존 고객은 새로운 지역별 데이터 센터로의 이동을 요청하지 않는 것이 좋습니다.   새로운 지역별 데이터 센터에 배포된 신규 고객은 타사 오디오 회의 공급자를 사용하기 위해 지역별 데이터 센터로의 이동을 요청해야 합니다. 

## <a name="data-for-other-services-including-teams-yammer-and-power-bi"></a>팀, Yammer 및 Power BI를 비롯 한 다른 서비스에 대 한 데이터

Exchange online, SharePoint Online 및 비즈니스용 Skype에 대 한 고객 데이터만 이동 합니다. 다른 서비스에 대 한 데이터는 이동 하지 않습니다. 이러한 서비스에 대 한 고객 또는 사용자는 변경 하거나 영향을 받지 않습니다. 이동 프로세스는 이러한 작업에 영향을 주지 않으며, 고객 데이터의 위치는 변경 되지 않은 상태로 유지 됩니다.
  
## <a name="related-topics"></a>관련 항목 
 
[데이터 이동을 요청하는 방법](request-your-data-move.md)
    
[데이터 이동 일반 FAQ](data-move-faq.md)
  
[Microsoft Dynamics CRM Online에 대 한 새로운 데이터 센터 지역](https://go.microsoft.com/fwlink/p/?Linkid=615924)
  
[지역별 Azure services](https://azure.microsoft.com/en-us/regions/)

