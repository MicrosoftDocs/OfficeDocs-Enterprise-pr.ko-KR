---
title: 액세스 가능한 다이어그램-온-프레미스 eDiscovery 흐름
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b9dcd692-0485-4eec-870d-87ab6b89d97b
description: 이 문서는 온-프레미스 eDiscovery 흐름 이라는 다이어그램의 액세스 가능한 텍스트 버전입니다.
ms.openlocfilehash: e137a75fb80c9198a332144d82fe405c6884aa52
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487704"
---
# <a name="accessible-diagram---on-premises-ediscovery-flow"></a>액세스 가능한 다이어그램-온-프레미스 eDiscovery 흐름

**요약:** 이 문서는 온-프레미스 eDiscovery 흐름 이라는 다이어그램의 액세스 가능한 텍스트 버전입니다.
  
이 포스터는 서버 제품 간의 데이터 아키텍처 및 흐름에 대 한 세부 정보를 제공 합니다. 
  
## <a name="across-sharepoint-exchange-lync-and-file-shares"></a>SharePoint, Exchange, Lync 및 파일 공유에서

이 다이어그램에서는 두 서버 팜, sharepoint 2013 엔터프라이즈 응용 프로그램 팜 및 sharepoint 2013 서비스 팜에 액세스 하는 쿼리를 전송 하는 사용자를 보여 줍니다. sharepoint 2013 서비스 팜은 sharepoint 2013 콘텐츠 팜, Exchange Server 2013 (Lync 2013와 통신) 및 Windows 파일 공유와 통신 합니다. 
  
eDiscovery 흐름 목록에서는 데이터 흐름 및 SharePoint, Exchange, Lync 및 파일 공유에서 eDisovery 쿼리 동작이 수행 되는 순서를 설명 합니다. 
  
eDiscovery 흐름 목록은 먼저 자세히 설명한 다음 다이어그램에 표시 된 기능에 대 한 자세한 설명을 참조 합니다. 
  
### <a name="ediscovery-flow-list"></a>eDiscovery 흐름 목록

이 목록에서 설명 하는 각 단계의 번호는 다이어그램에 표시 된 단계와 관련이 있습니다. 다이어그램은이 문서 뒷부분에 자세히 설명 되어 있습니다. 
  
1. ediscovery 사례를 만들고 관리 하며 ediscovery 센터 (EDC)에서 사용 합니다. EDC은 SharePoint 2013 사이트 모음입니다. 사례를 정의 하 고, 추적할 원본을 식별 하 고, 쿼리를 실행 하 고, 쿼리 결과를 검토 하 고, 콘텐츠에 대 한 보류를 설정 하거나 제거 하는 경우입니다. 
    
2. 보류 위치, releasehold 나 GetStatus 등의 eDiscovery 쿼리 또는 작업은 EDC에서 엔터프라이즈 앱 팜의 SSA (Search Service Application) 프록시로 릴레이 됩니다. 그런 다음 ssa 프록시는 서비스 응용 프로그램 팜의 SSA로 트래픽을 릴레이 합니다. 이 예에서 요청은 보류 중인 파일 이름에 "CONTOSO"를 포함 하는 항목을 SharePoint 콘텐츠 팜에 배치 하는 것입니다. 
    
3. 요청이 사례를 쿼리 하는 경우 SSA는 검색 인덱스를 찾습니다. 그런 다음 eDiscovery 쿼리 결과 집합은 EDC를 통해 사용자에 게 반환 됩니다. 
    
4. 보류 또는 releasehold 있는 등의 작업을 수행 하는 경우 해당 작업이 SSA 관리 데이터베이스의 Actions_Table에 기록 됩니다. 이 예제에서는 "CONTOSO"가 포함 된 SharePoint 콘텐츠 팜의 모든 항목에 대 한 보류 요청이 Actions_Table에 기록 됩니다. 
    
5. 정기적으로 콘텐츠 팜 eDiscovery 원본 위치 유지 타이머 작업이 작동을 중단 하 고 보류 중인 작업에 대 한 요청을 생성 하 고 ssa 프록시를 통해 상태 업데이트를 ssa로 보냅니다. 
    
6. 보류 중인 작업에 대 한 쿼리는 콘텐츠 팜에 대 한 보류 중인 작업에 대 한 Action_Table를 검색 하는 중앙 SSA로 릴레이 됩니다. 또한 콘텐츠 팜 원본 위치 유지 타이머 작업은 개체 및 받은 작업에 대 한 상태 업데이트를 전송 하 여 actionstable에 기록 합니다. 
    
7. SharePoint 2013 콘텐츠 팜의 이름에 "CONTOSO"가 포함 된 콘텐츠에 대 한 보류 요청은 콘텐츠 팜의 eDiscovery 원본 위치 유지 타이머 작업으로 전송 됩니다. 
    
8. eDiscovery 원본 위치 유지 타이머 작업은 "contoso Site" 및 "contoso content"를 보류 합니다. 
    
9. eDiscovery 원본 위치 유지 타이머 작업이 엔터프라이즈 앱 팜에서 주기적으로 실행 되어 검색 작업의 상태를 확인 하 고 상태를 업데이트 합니다. 
    
10. 상태 쿼리가 엔터프라이즈 앱 팜 ssa 프록시를 통해 SharePoint Services 팜 ssa로 릴레이 됩니다. 
    
11. SSA가 작업 테이블에서 상태를 검색 하 고 엔터프라이즈 앱 팜의 타이머 작업으로 반환 하 여 상태 업데이트를 EDC에 밀어넣습니다. 
    
12. eDiscovery 사용자가 사서함 또는 보관 된 Lync 콘텐츠와 같은 exchange 원본에 대해 검색 하거나 작업을 수행 하는 경우 중앙 SSA는 EWS (exchange 웹 서비스) 프록시를 사용 하 여 exchange 웹 서비스를 쿼리 합니다. Exchange에는 자체 검색 및 ediscovery 인프라가 있으며 모든 eDiscovery 통화를 내부적으로 관리 합니다. 
    
13. Exchange 웹 서비스는 eDiscovery 검색 결과를 포함 하는 SSA에 응답 하 고 쿼리 기반 보존에 대 한 상태 요청에 대 한 응답을 차례로 EDC로 릴레이 합니다. 
    
#### <a name="prerequisites"></a>필수 구성 요소

- sharepoint 엔터프라이즈 검색을 구성 해야 하 고, 콘텐츠 원본 (sharepoint 및 Windows 파일 공유)에 대 한 검색 크롤링이 성공적으로 수행 되며, 모든 콘텐츠 원본이 인덱스에 있습니다. 
    
- 서버 간 트러스트 및 인증은 SharePoint Services 팜과 exchange와 exchange 및 Lync 간에 구성 되어야 합니다. 
    
### <a name="description-of-components-in-the-diagram"></a>다이어그램의 구성 요소 설명

이 다이어그램에서는 sharepoint 2013 엔터프라이즈 응용 프로그램 팜과 sharepoint 2013 서비스 팜의 두 서버 팜에 액세스 하는 쿼리를 보내는 사용자를 보여 줍니다. sharepoint Services 팜 인터페이스를 사용 하는 경우 (예를 들어, Lync 2013과의 인터페이스), Windows 파일 공유 
  
#### <a name="sharepoint-2013-enterprise-app-farm"></a>SharePoint 2013 엔터프라이즈 응용 프로그램 팜

SharePoint 2013 엔터프라이즈 응용 프로그램 팜에 포함 되는 구성 요소는 다음과 같습니다. 
  
- EDC
    
- SSA 프록시 
    
- 타이머 작업 
    
사용자가 보낸 쿼리 또는 작업이 엔터프라이즈 앱 팜의 EDC에 전송 됩니다. 다음 작업이 수행 됩니다. 
  
- 쿼리 또는 작업이 SSA 프록시로 이동 합니다. 
    
- SSA 프록시는 엔터프라이즈 앱 팜의 타이머 작업에 상태 쿼리 또는 응답을 보내며 SharePoint Services 팜의 SSA 서비스에도 상태 쿼리 또는 응답을 보냅니다. 여기에서 생성 되는 작업은 SharePoint Services 팜 관련 섹션에 설명 되어 있습니다. 
    
- 응답을 받으면 타이머 작업은 SSA 프록시 및 EDC에 대 한 응답을 보냅니다. 
    
- 쿼리나 작업의 결과가 EDC에서 사용자에 게 전송 됩니다. 
    
#### <a name="sharepoint-2013-services-farm"></a>SharePoint 2013 서비스 팜

SharePoint 2013 서비스 팜은 다음과 같은 구성 요소를 포함 합니다. 
  
- SSA 서비스 
    
- 검색 인덱스 데이터베이스 
    
- SSA admin_db 데이터베이스 이 데이터베이스의 Actions 테이블에 포함 된 내용: 보류 릴리스 보류 GetStatus 
    
- EWS 프록시 
    
sharepoint 엔터프라이즈 앱 팜의 ssa 프록시가 sharepoint Services 팜의 ssa로 상태 쿼리를 보내면 다음 작업이 수행 됩니다. 
  
- 요청이 쿼리 인 경우 SSA는 검색 인덱스를 찾습니다. 검색 응답은 SSA로 반환 되 고 EDC를 통해 사용자에 게 전달 됩니다. 
    
- 요청이 쓰기 작업 인 경우 ssa 서비스는 admin_db에 게 write 작업을 보냅니다. 
    
- 크롤링 및 응답 결과 요청이 ssa에서 SharePoint 2013 콘텐츠 팜으로 전송 되 고 응답이 SSA로 반환 됩니다. 
    
- 크롤링 및 응답 결과 요청이 ssa에서 Windows 파일 공유로 전송 되 고 응답이 SSA로 반환 됩니다. 
    
- 보류 중인 작업 (s), 응답 또는 상태 업데이트에 대 한 쿼리는 ssa에서 SharePoint 콘텐츠 팜의 ssa 프록시로 전송 되며 ssa에 대 한 응답이 반환 됩니다. 
    
- exchange 작업/상태 요청은 SSA에서 EWS 프록시로 전송 되며 exchange 2013 서버의 exchange 웹 서비스로 exchange 쿼리 동작/상태 요청을 보냅니다. 
    
- 상태 쿼리/응답은 ssa에서 ssa로 전송 되 고 ssa로 반환 됩니다. 
    
- 보류 중인 실행 쿼리/응답은 ssa에서 ssa로 전송 되 고 ssa로 반환 됩니다. 
    
#### <a name="sharepoint-2013-content-farm"></a>SharePoint 2013 콘텐츠 팜

SharePoint 2013 콘텐츠 팜에 포함 되는 구성 요소는 다음과 같습니다. 
  
- SSA 프록시 
    
- 타이머 작업 
    
- Contoso SharePoint 사이트 
    
- Contoso SharePoint 콘텐츠 
    
sharepoint Services 팜의 ssa가 sharepoint 콘텐츠 팜의 ssa 프록시로 상태 쿼리를 보내면 다음 작업이 수행 됩니다. 
  
- SharePoint 콘텐츠 팜의 SSA 프록시가 타이머 작업에 대 한 보류 중인 작업/상태 응답 쿼리를 보냅니다. 
    
- 타이머 작업이 contoso sharepoint 사이트에 대 한 요청을 보내 contoso sharepoint 콘텐츠를 검토 합니다. 
    
- 보류 중인 작업/상태 쿼리에 대 한 응답은 타이머 작업에서 sharepoint 콘텐츠 팜의 ssa 프록시로 전송 된 다음 sharepoint Services 팜의 ssa 서비스로 전송 됩니다. 
    
#### <a name="exchange-2013"></a>Exchange 2013

exchange 2013 서버 구성 요소에는 exchange 웹 서비스가 포함 되어 있으며 다음이 제공 됩니다. 
  
- 서버 간 트러스트/OAuth는 SharePoint 2013 콘텐츠 팜과 Exchange 2013 간에 처리 됩니다. 
    
- 서버 간 트러스트/OAuth는 Exchange 2013와 Lync 2013 사이에서 처리 됩니다. 
    
#### <a name="lync-2013"></a>Lync 2013

lync 2013 구성 요소는 lync 콘텐츠를 Exchange 2013에 보관 합니다. 
  
#### <a name="windows-file-shares"></a>Windows 파일 공유

Windows 파일 공유 구성 요소는 SharePoint Services 팜의 SSA에 크롤링 결과를 제공 합니다. 
  
### <a name="legend"></a>Legend

이 다이어그램의 범례에는 다음과 같이 서로 다른 색으로 된 줄의 구성 요소에 표시 되는 다양 한 유형의 트래픽이 그래픽으로 나와 있습니다. 
  
- 연한 파란색 선: 쿼리/작업-eDiscovery 쿼리 또는 작업 데이터 
    
- 주황색 줄: eDisovery 응답-eDiscovery 쿼리 응답 데이터 
    
- 녹색 줄: 상태 쿼리/응답-eDiscovery 상태 쿼리/응답 데이터 
    
- 자주색 줄: exchange 작업/상태 요청-exchange 트래픽의 작업 상태에 대 한 eDiscovery 요청 
    
- Red line: exchange 데이터/상태 응답-exchange 로부터의 eDiscovery 쿼리 또는 상태 응답입니다. 
    
- 점선 검정 줄: 서버 간 트러스트/Oauth 
    
- 검정 실선 (크롤링/결과) 
    

