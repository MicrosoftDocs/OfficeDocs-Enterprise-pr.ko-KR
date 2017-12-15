---
title: "액세스할 수 있는 다이어그램-온-프레미스 eDiscovery 흐름"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b9dcd692-0485-4eec-870d-87ab6b89d97b
description: "이 문서에는 온-프레미스 eDiscovery 흐름 라는 다이어그램의 액세스할 수 있는 텍스트 버전입니다."
ms.openlocfilehash: de94fc2af94df47a83f4a7847a84cd18131f637e
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2017
---
# <a name="accessible-diagram---on-premises-ediscovery-flow"></a>액세스할 수 있는 다이어그램-온-프레미스 eDiscovery 흐름

**요약:** 이 문서에는 온-프레미스 eDiscovery 흐름 라는 다이어그램의 액세스할 수 있는 텍스트 버전입니다.
  
이 포스터 서버 제품 간에 아키텍처 및 데이터 흐름에 대 한 세부 정보를 제공합니다. 
  
## <a name="across-sharepoint-exchange-lync-and-file-shares"></a>SharePoint, Exchange, Lync 및 파일 공유에 걸쳐

다이어그램은 두 서버 팜, SharePoint 2013 엔터프라이즈 응용 프로그램 팜, 및 SharePoint 2013 서비스 팜에 액세스 하는 쿼리를 보내는 사용자를 보여줍니다. SharePoint 2013 콘텐츠 팜, (하는 Lync 2013와 통신 하는) Exchange Server 2013와 통신 하 고 SharePoint 2013 서비스 팜 및 Windows 파일 공유 합니다. 
  
EDiscovery 흐름 목록 데이터 및 순서는 eDisovery에서 쿼리 작업 SharePoint, Exchange, Lync 간에 발생 하 고 파일 공유의 흐름을 설명 합니다. 
  
EDiscovery 흐름 목록에에서 설명 되어 크기로 먼저, 다이어그램에 표시 된 기능에 대 한 자세한 설명을 앞에 오는 합니다. 
  
### <a name="ediscovery-flow-list"></a>eDiscovery 흐름 목록

각이 목록에 설명 된 단계에 대 한 숫자는 다이어그램에 표시 된 단계와 관련이 있습니다. 다이어그램은이 문서 뒷부분에서 자세히 설명 되어있습니다. 
  
1. eDiscovery 사례 생성 하 고 관리, 하 고는 EDC (eDiscovery 센터)에서 사용 됩니다. EDC는 SharePoint 2013 사이트 모음입니다. 이 고 여기서의 경우 정의 된를 추적할 수 있는 원본을 식별 된, 쿼리가 실행 됩니다, 쿼리 결과 검토 하는 콘텐츠에 보류는 배치 되거나 제거 된입니다. 
    
2. EDiscovery 쿼리 또는 보류, ReleaseHold, 또는 GetStatus, 원본 위치와 같은 작업을 엔터프라이즈 응용 프로그램 팜의 검색 서비스 응용 프로그램 (SSA) 프록시는 EDC에서 릴레이 됩니다. SSA 프록시에는 다음 서비스 응용 프로그램 팜의 SSA에 트래픽을 릴레이합니다. 이 예제에서는 요청 "contoso" SharePoint 콘텐츠 팜에서 아무것도 시키려면 대기 파일 이름에는 합니다. 
    
3. 사례를 쿼리 하는 요청이 인 경우 SSA와 같은 검색 인덱스를 참조 합니다. 그런 다음, eDiscovery 쿼리 결과 집합의 EDC 통해 사용자에 게 반환합니다. 
    
4. 요청은 대기 또는 ReleaseHold, 위치 등의 작업을 하는 경우 해당 작업 Actions_Table SSA 관리 데이터베이스에 기록 됩니다. 이 예제에서는 "contoso" SharePoint 콘텐츠 팜에서에 들어 있는 개체에 대 한 보류 요청은 Actions_Table에 기록 됩니다. 
    
5. 일정 한 간격으로 콘텐츠 팜 eDiscovery 전체 보류에서 타이머 작업 활성화 되어 하 고 보류 중인 작업에 대 한 요청을 생성 하 고 SSA에 SSA 프록시를 통해 상태 업데이트를 보냅니다. 
    
6. 보류 중인 작업에 대 한 쿼리는 Action_Table 보류 중인 콘텐츠 팜에 대 한 작업에 대 한 참조 하는 중앙 SSA 릴레이 됩니다. 또한 콘텐츠 팜 원본 위치 유지 타이머 작업이 개체와는 ActionsTable에 기록 되는 처리가 수신 하는 작업에 대 한 상태 업데이트를 보냅니다. 
    
7. SharePoint 2013 콘텐츠 팜의 이름에 "contoso" 모든 콘텐츠에 대 한 보류 요청 콘텐츠 팜에 있는 eDiscovery의 원본 위치 유지 타이머 작업을 SSA에서 전송 됩니다. 
    
8. eDiscovery 원본 위치 유지 타이머 작업 places "CONTOSO 사이트" 및 "CONTOSO content"에 유지 합니다. 
    
9. 엔터프라이즈 응용 프로그램 팜의 검색 작업의 상태를 확인 하 고 상태를 업데이트 하려면 eDiscovery 원본 위치 유지 타이머 작업이 정기적으로 실행 합니다. 
    
10. 상태 쿼리는 SharePoint Services 팜 SSA에 엔터프라이즈 응용 프로그램 팜의 SSA 프록시를 통해 릴레이 됩니다. 
    
11. SSA 작업 테이블에서 상태를 검색 하 고는 EDC에 상태 업데이트를 올려놓습니다 하는 엔터프라이즈 응용 프로그램 팜의 타이머 작업을 반환 합니다. 
    
12. 때 eDiscovery 사용자가 검색 (또는 작업을 수행) 사서함 또는 보관 된 Lync 콘텐츠 등의 Exchange 원본에 대 한 중앙 SSA를 사용 하 여 Exchange 웹 서비스 쿼리를 Exchange 웹 서비스 (EWS) 프록시 합니다. Exchange 자체 검색 및 eDiscovery 인프라 있으며 eDiscovery에 대 한 모든 호출을 내부적으로 관리 됩니다. 
    
13. Exchange 웹 서비스는 eDiscovery 검색 결과 또는 EDC 사람에 게 차례로 릴레이 가져옵니다 하는 쿼리 기반 보존에 대 한 상태 요청에 대 한 응답 SSA에 응답 합니다. 
    
#### <a name="prerequisites"></a>필수 구성 요소

- SharePoint 엔터프라이즈 검색 구성, 검색 크롤링을 콘텐츠 원본 (SharePoint 및 Windows 파일 공유)에 성공적으로 발생 하는, 되 고 되어야 인덱스에는 모든 콘텐츠 원본입니다. 
    
- SharePoint Services 팜 사이의 Exchange 및 Exchange 및 Lync 간의 서버 간 트러스트 및 인증을 구성 되어야 합니다. 
    
### <a name="description-of-components-in-the-diagram"></a>구성 요소는 다이어그램에 대 한 설명

다이어그램은 두 서버 팜, SharePoint 2013 엔터프라이즈 응용 프로그램 팜 및 SharePoint 2013 서비스 팜에 액세스 하는 쿼리를 보내는 사용자를 보여줍니다. SharePoint 2013 콘텐츠 팜, (하는 인터페이스 (영문) Lync 2013과 함께) Exchange Server 2013, SharePoint Services 팜 교류 및 Windows 파일 공유 합니다. 
  
#### <a name="sharepoint-2013-enterprise-app-farm"></a>SharePoint 2013 엔터프라이즈 응용 프로그램 팜

SharePoint 2013 엔터프라이즈 응용 프로그램 팜의 다음과 같은 구성 요소가 포함 됩니다. 
  
- EDC
    
- SSA 프록시 
    
- 타이머 작업 
    
쿼리 또는 사용자가 보낸 작업이 엔터프라이즈 응용 프로그램 팜의 EDC에 전송 됩니다. 다음과 같은 작업이 수행 됩니다. 
  
- 쿼리 또는 동작 SSA 프록시로 이동 합니다. 
    
- SSA 프록시 엔터프라이즈 응용 프로그램 팜의 상태 쿼리 또는 타이머 작업에 대 한 응답을 전송 하 고도 보냅니다 상태 쿼리 또는 SSA 서비스에 대 한 응답 SharePoint Services 팜의. 이 통해 생성 되는 작업은 SharePoint Services 팜 하는 방법에 대 한 섹션에 설명 되어있습니다. 
    
- 응답을 받으면 SSA 프록시 하 고는 EDC 타이머 작업에 대 한 응답을 보냅니다. 
    
- 쿼리 또는 작업에서 모든 결과 EDC에서 사용자에 게 전송 됩니다. 
    
#### <a name="sharepoint-2013-services-farm"></a>SharePoint 2013 서비스 팜

SharePoint 2013 서비스 팜은 다음과 같은 구성 요소가 포함 됩니다. 
  
- SSA 서비스 
    
- 검색 인덱스 데이터베이스 
    
- SSA admin_db 데이터베이스입니다. 이 데이터베이스에서 작업 테이블에는 포함: 릴리스 유지 GetStatus 유지 
    
- EWS 프록시 
    
SharePoint 엔터프라이즈 응용 프로그램 팜의 SSA 프록시 SharePoint Services 팜의 SSA를 상태 쿼리를 보내면 다음 작업이 수행 됩니다. 
  
- 쿼리 요청을 사용 하는 경우 SSA와 같은 검색 인덱스를 참조 합니다. 검색에 대 한 응답 SSA 이동한 다음는 EDC 통해 사용자에 게 반환 됩니다. 
    
- 요청은 쓰기 작업을 하는 경우 SSA 서비스 SSA admin_db 하는 쓰기 작업을 보냅니다. 
    
- 크롤링 및 응답 SSA에서 SharePoint 2013 콘텐츠 팜 결과 요청이 전송 되 고 응답 SSA에 반환 됩니다. 
    
- 크롤링 및 응답 결과 요청이 Windows 파일 공유로 SSA에서 전송 되 고 응답 SSA에 반환 됩니다. 
    
- SharePoint 콘텐츠 팜에서 SSA 프록시에 SSA에서 보내는 동작, 응답 또는 상태 업데이트가 보류 중인에 대 한 쿼리 및 응답 SSA로 반환 됩니다. 
    
- Exchange 2013 서버에서 Exchange 웹 서비스에는 Exchange 쿼리 작업/상태 요청을 전송 하는 EWS 프록시에는 Exchange 작업/상태 요청이 SSA에서 보내집니다. 
    
- 상태 쿼리/응답 SSA에서 SSA admin_db에 전송 되 고 SSA에 반환 됩니다. 
    
- 보류 중인 작업 쿼리/응답 SSA에서 SSA admin_db에 전송 되 고 SSA에 반환 됩니다. 
    
#### <a name="sharepoint-2013-content-farm"></a>SharePoint 2013 콘텐츠 팜

SharePoint 2013 콘텐츠 팜 다음과 같은 구성 요소가 포함 됩니다. 
  
- SSA 프록시 
    
- 타이머 작업 
    
- Contoso SharePoint 사이트 
    
- Contoso SharePoint 콘텐츠 
    
SharePoint Services 팜의 SSA가 SharePoint 콘텐츠 팜에서 SSA 프록시에 상태 쿼리를 보낼 때 다음 작업이 수행 됩니다. 
  
- SharePoint 콘텐츠 팜에서 SSA 프록시에 대 한 타이머 작업에 대 한 작업/상태 응답 보류 중인 쿼리를 보냅니다. 
    
- 타이머 작업 Contoso SharePoint 사이트로 Contoso SharePoint 콘텐츠를 검토 하는 요청을 보냅니다. 
    
- SharePoint 콘텐츠 팜에서 SSA 프록시에 대 한 응답을 보류 중인 작업/상태 쿼리 타이머 작업에서 보내는 하 고이 SharePoint Services 팜의 SSA 서비스에 전달 되는 다음 
    
#### <a name="exchange-2013"></a>Exchange 2013

Exchange 2013 서버 구성 요소에서 Exchange 웹 서비스를 포함 하 고 다음을 제공 합니다. 
  
- SharePoint 2013 콘텐츠 팜 사이의 Exchange 2013 서버 간 트러스트/OAuth 처리 됩니다. 
    
- Exchange 2013 및 Lync 2013 간에 서버간-신뢰/OAuth 처리 됩니다. 
    
#### <a name="lync-2013"></a>Lync 2013

Lync 2013 구성 요소 Lync 콘텐츠 Exchange 2013를 보관합니다. 
  
#### <a name="windows-file-shares"></a>Windows 파일 공유

SharePoint Services 팜의 SSA에 크롤링 결과 제공 하는 Windows 파일 공유 구성 요소입니다. 
  
### <a name="legend"></a>범례

이 다이어그램에 대 한 범례 다양 한 유형의 다음과 같이 서로 다른 색이 지정 된 줄의 구성 요소 중에서 설명 하는 트래픽을 그래픽으로 보여줍니다. 
  
- 연한 파랑 선: 쿼리/작업-eDiscovery 쿼리 또는 동작 데이터 
    
- 주황색 줄: eDisovery 응답-eDiscovery 쿼리 응답 데이터 
    
- 선 녹색: 상태 쿼리/응답-eDiscovery 상태 쿼리/응답 데이터 
    
- 선 보라색: Exchange 작업/상태 요청-Exchange 트래픽에 대 한 작업 상태에 대 한 eDiscovery 요청 합니다. 
    
- 빨간색 선: 데이터/상태 응답-Exchange Exchange에서 eDiscovery 쿼리 또는 상태 응답 합니다. 
    
- 검정 선 점선: 서버 간 트러스트/Oauth 
    
- 검정 실선: 크롤링/결과 
    

