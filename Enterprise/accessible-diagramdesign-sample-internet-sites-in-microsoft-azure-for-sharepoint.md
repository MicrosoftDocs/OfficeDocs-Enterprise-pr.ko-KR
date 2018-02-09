---
title: "액세스할 수 있는 다이어그램-SharePoint 2013에 대 한 Microsoft Azure의 디자인 샘플 인터넷 사이트"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.collection: Ent_O365
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b91124bc-c7ec-4929-b77c-d6293db9f15e
description: "이 문서는 디자인 sample 다이어그램의 액세스할 수 있는 텍스트 버전: SharePoint 2013에 대 한 Microsoft Azure의 인터넷 사이트입니다."
ms.openlocfilehash: 0d42a96f80d47b360084557fea47c4155d106d30
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/09/2018
---
# <a name="accessible-diagram---design-sample-internet-sites-in-microsoft-azure-for-sharepoint-2013"></a>액세스할 수 있는 다이어그램-디자인 예제: SharePoint 2013에 대 한 Microsoft Azure의 인터넷 사이트

**요약:** 이 문서는 디자인 sample 다이어그램의 액세스할 수 있는 텍스트 버전: SharePoint 2013에 대 한 Microsoft Azure의 인터넷 사이트입니다.
  
SharePoint 2013을 사용 하 여 Azure에는 인터넷 사이트에 대 한 시작 지점으로이 디자인 예제를 사용 합니다.
  
이 포스터에서는 SharePoint 2013의 다음과 같은 측면을 디자인 하는 방법의 예를 보여줍니다.
  
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

이 디자인의 사용자 계정에 다음과 같은 네가지 유형의 있습니다. 각 유형의 계정 액세스에 대 한 사이트와 특정 유형의 인증을 사용 하는 영역에 연결 됩니다. 
  
- 익명 고객-익명 고객 예: http://www.contoso.com 사이트를 통해 액세스 권한이 있습니다. 자신이 사용 하 여 영역은 "인터넷 영역 익명 /", 익명 인증을 사용 하는 합니다.
    
- 고객 인증-인증 된 고객 https://secure.contoso.com와 같은 사이트를 통해 액세스 권한이 있습니다. 자신이 사용 하 여 영역은 "익스트라넷 영역 / SAML", Azure Active Directory를 사용 하 여 SAML 인증을 사용 하는 합니다.
    
- 사이트 작성자 및 개발자 — 사이트 작성자와 개발자가 http://authoring.contoso.com:8000 또는 http://www.contoso.com:8000 등의 사이트를 통해 액세스할 수 있습니다. 자신이 사용 하 여 영역은 "기본 영역 Windows 통합 /", Active Directory 도메인 서비스 (AD DS)를 사용 하는 합니다.
    
- 검색 크롤링 계정-검색 크롤링 계정에 액세스 권한이 http://authoring.contoso.com:8000 또는 http://www.contoso.com:8000 등의 사이트를 통해 합니다. 사용 하 여 영역은 "기본 영역 Windows 통합 /", 하는 AD DS를 사용 하 여 Windows NTLM 인증을 사용 합니다.
    
## <a name="server-farm"></a>서버 팜

서버 팜 Azure를 통해 액세스 하는 사용자입니다. 서버 팜 하나 이상의 웹 서버를 포함합니다.
  
## <a name="administration-site"></a>관리 사이트

관리 사이트 중앙 관리 사이트 웹 응용 프로그램을 사용 하는 응용 프로그램 풀 (이 예제에서 응용 프로그램 풀 1)와 통신 하는 여러 응용 프로그램 서버를 포함 합니다. 중앙 관리 사이트는 조직 내에서 사이트 모음에 대 한 액세스를 제공합니다.
  
관리 사이트에도 SQL 클러스터링, 미러링 또는 AlwaysOn을 지원 하도록 SQL server 설치 및 구성 데이터베이스 서버는 SQL 데이터베이스 서버를 포함 (AlwaysOn 적용 하는 SQL Server 2012에만 해당).
  
## <a name="services"></a>서비스

디자인 예제는 인터넷 정보 서비스 (IIS) 웹사이트, SharePoint 웹 서비스를 보여줍니다. SharePoint 웹 서비스는 세개의 서비스, 사용자 프로필, 검색 및 관리 되는 메타 데이터와 응용 프로그램 풀 (응용 프로그램 풀 2)를 포함합니다.
  
인터넷 사이트에 대 한 서비스에 대 한 참고 사항:
  
> 관리 되는 메타 데이터- **이 서비스 응용 프로그램은 열 관련 용어 집합에 대 한 기본 저장소 위치를**선택 해야 합니다.
    
> 응용 프로그램 관리-좋지 않습니다 Azure에서 공용 인터넷 사이트에서 앱을 사용 하 여 합니다.
    
## <a name="application-pools-and-web-applications"></a>응용 프로그램 풀 및 웹 응용 프로그램

Azure의 기본 그룹 Contoso 사이트 이름이 지정 된 웹 응용 프로그램을 포함 하는 응용 프로그램 풀 3을 표시 합니다. 이 경로 기반 사이트 모음은 http://internal:8000에 있습니다.
  
## <a name="site-collections-and-sites"></a>사이트 모음 및 사이트

응용 프로그램 풀에 포함 된 사이트 모음에는 다음이 포함 됩니다.
  
- 호스트 이름이 지정 된 사이트 모음 1 위치에 대 한 크롤링 (예제 http://authoring.contoso.com:8000)
    
- 쿼리 (샘플 위치 http://www.contoso.com, https://secure.contoso.com, http://www.contoso.com:8000)에 대 한 호스트 이름이 지정 된 사이트 모음 2
    
- 쿼리 (샘플 위치 http://assets.contoso.com, https://secureassets.contoso.com, http://assets.contoso.com:8000)에 대 한 호스트 이름이 지정 된 사이트 모음 3
    
## <a name="content-databases"></a>콘텐츠 데이터베이스

이 예제에서는 두 콘텐츠 데이터베이스를 보여줍니다. 하나는 사이트 모음 크롤링 (http://authoring.contoso.com:8000)에 사용 되는 1입니다. 다른 두 사이트 모음 2 및 3 쿼리 (http://www.contoso.com, https://secure.contoso.com, http://www.contoso.com:8000, 또는 http://assets.contoso.com, https://secureassets.contoso.com, http://assets.contoso.com:8000)에 사용 되는 단계입니다.
  
## <a name="zones-and-urls"></a>영역 및 URL

이 예제에서는 서로 다른 사용자 계정에서 사용 되는 연결 된 부하 분산 된 Url이 포함 된 세 영역을 보여줍니다. 
  
사이트 모음 1, 영역 및 Url의 첫째 목록와 관련 된 하 고 다음 정보를 포함 합니다.
  
- 사용자가-사이트 작성자
    
- 영역-기본
    
- 부하 분산 된 URL-http://authoring.contoso.com:8000
    
영역 및 Url의 두번째 목록 3 개의 다른 영역에서 서로 다른 세가지 유형의 사용자에 있습니다. 사이트 모음 2와 관련 된 하 고 다음 정보를 포함 합니다.
  
첫번째 영역:
  
- 사용자가-사이트 작성자
    
- 영역-기본
    
- 부하 분산 된 URL-http://www.contoso.com:8000
    
두번째 영역:
  
- 사용자가-익명 고객
    
- 영역-인터넷
    
- 부하 분산 된 URL-http://www.contoso.com
    
세번째 영역:
  
- 사용자가-인증 된 고객
    
- 영역-엑스트라넷
    
- 부하 분산 된 URL-https://secure.contoso.com
    
영역 및 Url의 세번째 목록 3 개의 다른 영역에서 서로 다른 세가지 유형의 사용자에 있습니다. 사이트 모음 3와 관련 된 하 고는 다음 정보를 제공 합니다.
  
첫번째 영역:
  
- 사용자가-사이트 작성자
    
- 영역-인터넷
    
- 부하 분산 된 URL-http://assets.contoso.com:8000
    
두번째 영역:
  
- 사용자가-익명 고객
    
- 영역-인터넷
    
- 부하 분산 된 URL-http://assets.contoso.com
    
세번째 영역:
  
- 사용자가-인증 된 고객
    
- 영역-엑스트라넷
    
- 부하 분산 된 URL-http://secureassets.contoso.com
    

