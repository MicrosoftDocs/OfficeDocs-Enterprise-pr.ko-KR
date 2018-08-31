---
title: 콘텐츠 쿼리 웹 파트는 대신 콘텐츠 검색 웹 파트를 사용 하 여 SharePoint Online에서 성능을 개선합니다
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/20/2015
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: e8ce6b72-745b-464a-85c7-cbf6eb53391b
description: 이 문서에서는 SharePoint Server 2013 및 SharePoint Online에서 콘텐츠 검색 웹 파트와 콘텐츠 쿼리 웹 파트를 대체 하 여 성능을 개선 하는 방법에 설명 합니다.
ms.openlocfilehash: f86a4b75c4bf75ebaa99924411d017c7eb7b6760
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542227"
---
# <a name="using-content-search-web-part-instead-of-content-query-web-part-to-improve-performance-in-sharepoint-online"></a>콘텐츠 쿼리 웹 파트는 대신 콘텐츠 검색 웹 파트를 사용 하 여 SharePoint Online에서 성능을 개선합니다

이 문서에서는 SharePoint Server 2013 및 SharePoint Online에서 콘텐츠 검색 웹 파트와 콘텐츠 쿼리 웹 파트를 대체 하 여 성능을 개선 하는 방법에 설명 합니다.
  
SharePoint Server 2013 및 SharePoint Online의 가장 강력한 새로운 기능 중 하나는 콘텐츠 검색 웹 파트 (CSWP)입니다. 이 웹 파트와 같은 검색 인덱스를 사용 하 여 신속 하 게 사용자에 게 표시 되는 결과 검색 합니다. 대신는 콘텐츠 쿼리 웹 파트 (CQWP) 페이지에서 콘텐츠 검색 웹 파트 사용 하 여 사용자에 대 한 성능 향상을 위해.
  
콘텐츠 검색 웹 파트를 사용 하 여 콘텐츠 쿼리 웹 파트를 통해 SharePoint Online에서 페이지 부하 성능이 크게 향상 거의 항상 발생 합니다. 오른쪽 쿼리를 가져올 약간의 추가 구성 이지만 성능 향상된 및 만족도 사용자는 보상 됩니다.
  
## <a name="comparing-the-performance-gain-you-get-from-using-content-search-web-part-instead-of-content-query-web-part"></a>콘텐츠 검색 웹 파트를 사용 하 여 콘텐츠 쿼리 웹 파트는 대신에서 가져올 성능 향상 비교 (영문)

다음 예제에서는 콘텐츠 검색 웹 파트를 사용 하 여 콘텐츠 쿼리 웹 파트는 대신 때 나타날 수 상대 성능 향상을 보여줍니다. 효과 복잡 한 사이트 구조와 매우 광범위 한 콘텐츠 쿼리 보다 명확 하 게 합니다.
  
이 예제에서는 사이트에는 다음과 같은 특징이 있습니다.
  
- 하위 사이트 수준의 8입니다.
    
- 사용자 지정 "과일" 콘텐츠 형식을 사용 하 여 나열 합니다.
    
- 웹 파트에서 콘텐츠 쿼리는 광범위 한 "과일"의 콘텐츠 형식 사용 하는 모든 항목을 반환 합니다.
    
- 이 예제에서는 8 사이트에 걸쳐 50 개의 항목을만 사용 합니다. 더 많은 콘텐츠가 포함 된 사이트에 대 한 효과 훨씬 더 많이 듭니다 될 됩니다.
    
스크린샷 콘텐츠 쿼리 웹 파트의 결과 다음과 같습니다.
  
![웹 파트에 대한 콘텐츠 쿼리를 보여 주는 그래픽](media/b3d41f20-dfe5-46ed-9c0a-31057e82de33.png)
  
Internet Explorer에서 응답 헤더에 대 한 세부 정보를 살펴보는 F12 개발자 도구에 있는 **네트워크** 탭을 사용 합니다. 다음 화면에,이 페이지 부하에 대 한 **SPRequestDuration** 에 대 한 값은 924 밀리초입니다. 
  
![924의 요청 기간을 보여 주는 스크린샷](media/343571f2-a249-4de2-bc11-2cee93498aea.png)
  
 **SPRequestDuration** 페이지를 준비 하는 서버에서 작업을 수행 하는 작업의 크기를 나타냅니다. 콘텐츠 검색 웹 파트를 사용 하 여 쿼리 웹 파트에서 콘텐츠를 크게 전환 페이지를 렌더링 하는데 걸리는 시간이 줄어듭니다. 반면, 해당 하는 콘텐츠 검색 웹 파트 페이지 106 시간 (밀리초)이 스크린샷은 같이 **SPRequestDuration** 값이 동일한 결과 수를 반환 합니다. 
  
![106의 요청 기간을 보여 주는 스크린샷](media/b46387ac-660d-4e5e-a11c-cc430e912962.png)
  
## <a name="adding-a-content-search-web-part-in-sharepoint-online"></a>SharePoint에서 온라인 콘텐츠 검색 웹 파트를 추가

콘텐츠 검색 웹 파트를 추가 하는 것은 일반 콘텐츠 쿼리 웹 파트와 매우 유사 합니다. [SharePoint에서 콘텐츠 검색 웹 파트 구성](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a)에서 *"콘텐츠 검색 웹 파트 추가"* 섹션을 참조 하십시오.
  
## <a name="creating-the-right-search-query-for-your-content-search-web-part"></a>콘텐츠 검색 웹 파트에 대 한 올바른 검색 쿼리 만들기 (영문)

콘텐츠 검색 웹 파트를 추가 하 고 나면 검색을 구체화할 수 있으며 원하는 항목을 반환할 수 있습니다. 이 작업을 수행 하는 방법에 대 한 자세한 내용은 [Configure SharePoint에서 콘텐츠 검색 웹 파트의](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a)에서 *"콘텐츠 검색 웹 파트에 고급 쿼리를 구성 하 여 콘텐츠 표시"* 섹션을 참조 하십시오.
  
## <a name="query-building-and-testing-tool"></a>쿼리 작성 및 테스트 도구

구성 하 고 복잡 한 쿼리를 테스트 하는 도구에 대 한 Codeplex에서 [검색 쿼리 도구](https://sp2013searchtool.codeplex.com/) 를 참조 하십시오. 
  

