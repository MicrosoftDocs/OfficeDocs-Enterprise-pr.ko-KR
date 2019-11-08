---
title: 액세스 가능한 다이어그램-SharePoint 용 Microsoft Azure 2013의 예제 인터넷 사이트 디자인
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.collection: Ent_O365
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b91124bc-c7ec-4929-b77c-d6293db9f15e
description: '이 문서는 Design sample: SharePoint 용 Microsoft Azure 2013의 Internet sites 라는 액세스 가능한 텍스트 버전입니다.'
ms.openlocfilehash: 52ae615cbdc6a355155e54e36bc6a3d733d84869
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2019
ms.locfileid: "38027632"
---
# <a name="accessible-diagram---design-sample-internet-sites-in-microsoft-azure-for-sharepoint-2013"></a>액세스 가능한 다이어그램-디자인 샘플: SharePoint 용 Microsoft Azure 2013의 인터넷 사이트

**요약:** 이 문서는 Design sample: SharePoint 용 Microsoft Azure 2013의 Internet sites 라는 액세스 가능한 텍스트 버전입니다.
  
이 디자인 예제를 Azure에서 SharePoint 2013을 사용 하는 인터넷 연결 사이트의 시작 지점으로 사용 합니다.
  
이 포스터는 SharePoint 2013의 다음과 같은 측면을 디자인 하는 방법의 예를 보여 줍니다.
  
- 사용자
    
- 영역 및 인증
    
- 서버 팜
    
- 관리 사이트
    
- 서비스
    
- 응용 프로그램 풀 및 웹 응용 프로그램
    
- 사이트 모음
    
- 사이트
    
- 콘텐츠 데이터베이스
    
- 영역 및 URL
    
## <a name="users-zones-and-authentication"></a>사용자, 영역 및 인증

이 디자인에는 다음과 같은 네 가지 유형의 사용자 계정이 있습니다. 각 계정 유형은 액세스를 위해 사이트와 특정 유형의 인증을 사용 하는 영역에 연결 됩니다. 
  
- 익명 고객-익명 고객은와 https://www.contoso.com같은 사이트를 통해 액세스할 수 있습니다. 사용 하는 영역은 "인터넷 영역/익명"으로, 익명 인증을 사용 합니다.
    
- 인증 된 고객-인증 된 고객이와 https://secure.contoso.com같은 사이트를 통해 액세스할 수 있습니다. 사용 하는 영역은 SAML 인증을 사용 하는 Azure Active Directory를 사용 하는 "엑스트라넷 영역/SAML"입니다.
    
- 사이트 작성자와 개발자 — 사이트 작성자와 개발자는 https://authoring.contoso.com:8000 또는 https://www.contoso.com:8000등의 사이트를 통해 액세스할 수 있습니다. 사용 하는 영역은 AD DS (Active Directory 도메인 서비스)를 사용 하는 "기본 영역/Windows 통합"입니다.
    
- 검색 크롤링 계정-검색 크롤링 계정에 https://authoring.contoso.com:8000 또는 https://www.contoso.com:8000등의 사이트를 통해 액세스할 권한이 있습니다. 이를 사용 하는 영역은 Windows NTLM 인증을 사용 하는 AD DS를 사용 하는 "기본 영역/Windows 통합"입니다.
    
## <a name="server-farm"></a>서버 팜

사용자가 Azure를 통해 서버 팜에 액세스 합니다. 서버 팜에 하나 이상의 웹 서버가 포함 되어 있습니다.
  
## <a name="administration-site"></a>관리 사이트

관리 사이트에는 웹 응용 프로그램 중앙 관리 사이트를 사용 하는 응용 프로그램 풀 (예제의 경우 응용 프로그램 풀 1)과 통신 하는 여러 응용 프로그램 서버가 포함 되어 있습니다. 중앙 관리 사이트는 조직 내의 사이트 모음에 대 한 액세스를 제공 합니다.
  
또한 관리 사이트에는 sql Server를 설치 하 고 sql 클러스터링, 미러링 또는 AlwaysOn을 지원 하도록 구성 된 데이터베이스 서버인 SQL 데이터베이스 서버 (AlwaysOn은 SQL Server 2012에만 적용 됨)가 포함 되어 있습니다.
  
## <a name="services"></a>서비스

이 디자인 예제에는 IIS (인터넷 정보 서비스) 웹 사이트, SharePoint Web Services가 표시 됩니다. SharePoint 웹 서비스에는 세 가지 서비스, 사용자 프로필, 검색 및 관리 되는 메타 데이터가 포함 된 응용 프로그램 풀 (응용 프로그램 풀 2)이 포함 되어 있습니다.
  
인터넷 사이트용 서비스에 대 한 참고 사항:
  
> Managed Metadata- **이 서비스 응용 프로그램은 열 관련 용어 집합의 기본 저장 위치**입니다 .를 선택 해야 합니다.
    
> 앱 관리 — Azure의 공용 인터넷 사이트에서 앱을 사용 하지 않는 것이 좋습니다.
    
## <a name="application-pools-and-web-applications"></a>응용 프로그램 풀 및 웹 응용 프로그램

Azure의 기본 그룹에는 Contoso Sites 라는 웹 응용 프로그램이 포함 된 응용 프로그램 풀 3이 표시 됩니다. 이 경로 기반 사이트 모음은에 https://internal:8000있습니다.
  
## <a name="site-collections-and-sites"></a>사이트 모음 및 사이트

응용 프로그램 풀에 포함 된 사이트 모음에는 다음이 포함 됩니다.
  
- 크롤링에 대 한 호스트 이름으로 된 사이트 모음 1 (예제 위치https://authoring.contoso.com:8000)
    
- 쿼리에 대 한 호스트 이름으로 된 사이트 모음 2 ( https://www.contoso.com샘플 https://secure.contoso.com위치,https://www.contoso.com:8000)
    
- 쿼리에 대 한 호스트 이름으로 된 사이트 모음 3 개 https://assets.contoso.com( https://secureassets.contoso.com샘플 위치,https://assets.contoso.com:8000)
    
## <a name="content-databases"></a>콘텐츠 데이터베이스

이 예제에서는 두 개의 콘텐츠 데이터베이스를 보여 줍니다. 하나는 크롤링에 사용 되는 사이트 모음 1입니다https://authoring.contoso.com:8000)(. 다른 하나는 쿼리에 사용 되는 두 개의 사이트 모음 2와 3입니다https://www.contoso.com( https://secure.contoso.com, https://www.contoso.com:8000, 또는 https://assets.contoso.com, https://secureassets.contoso.com, https://assets.contoso.com:8000),).
  
## <a name="zones-and-urls"></a>영역 및 URL

이 예제에서는 서로 다른 사용자 계정에서 사용 하는 연결 된 부하 분산 Url이 포함 된 세 개의 영역을 보여 줍니다. 
  
영역 및 Url의 첫 목록은 사이트 모음 1과 관련 되며 다음 정보를 포함 합니다.
  
- 사용자-사이트 작성자
    
- 영역-기본값
    
- 부하 분산 된 URL-https://authoring.contoso.com:8000
    
영역과 Url의 두 번째 목록에는 세 가지 영역에 서로 다른 세 가지 유형의 사용자가 있습니다. 이는 사이트 모음 2와 관련 되며 다음과 같은 정보를 포함 합니다.
  
첫 번째 영역:
  
- 사용자-사이트 작성자
    
- 영역-기본값
    
- 부하 분산 된 URL-https://www.contoso.com:8000
    
두 번째 영역:
  
- 사용자-익명 고객
    
- 영역-인터넷
    
- 부하 분산 된 URL-https://www.contoso.com
    
세 번째 영역:
  
- 사용자 인증 고객
    
- 영역 엑스트라넷
    
- 부하 분산 된 URL-https://secure.contoso.com
    
영역 및 Url의 세 번째 목록에는 세 가지 다른 영역에서 세 가지 유형의 사용자가 있습니다. 이는 사이트 모음 3과 관련 되며 다음과 같은 정보를 포함 합니다.
  
첫 번째 영역:
  
- 사용자-사이트 작성자
    
- 영역-인터넷
    
- 부하 분산 된 URL-https://assets.contoso.com:8000
    
두 번째 영역:
  
- 사용자-익명 고객
    
- 영역-인터넷
    
- 부하 분산 된 URL-https://assets.contoso.com
    
세 번째 영역:
  
- 사용자 인증 고객
    
- 영역 엑스트라넷
    
- 부하 분산 된 URL-https://secureassets.contoso.com
    

