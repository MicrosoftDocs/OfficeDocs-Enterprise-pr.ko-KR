---
title: SharePoint Online에서 성능을 향상 시키기 위해 콘텐츠 쿼리 웹 파트 대신 콘텐츠 검색 웹 파트 사용
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 4/20/2015
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: e8ce6b72-745b-464a-85c7-cbf6eb53391b
description: 이 문서에서는 콘텐츠 쿼리 웹 파트를 SharePoint Server 2013 및 SharePoint Online의 콘텐츠 검색 웹 파트로 대체 하 여 성능을 개선 하는 방법에 대해 설명 합니다.
ms.openlocfilehash: e2a3a1dd5a0010fcf1bbf61a039ca1d23292f70d
ms.sourcegitcommit: 8027254ab4b9ed44a5b0c336f714049859f93f3d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/15/2019
ms.locfileid: "38077947"
---
# <a name="using-content-search-web-part-instead-of-content-query-web-part-to-improve-performance-in-sharepoint-online"></a>SharePoint Online에서 성능을 향상 시키기 위해 콘텐츠 쿼리 웹 파트 대신 콘텐츠 검색 웹 파트 사용

이 문서에서는 콘텐츠 쿼리 웹 파트를 SharePoint Server 2013 및 SharePoint Online의 콘텐츠 검색 웹 파트로 대체 하 여 성능을 개선 하는 방법에 대해 설명 합니다.
  
SharePoint Server 2013 및 SharePoint Online의 가장 강력한 새 기능 중 하나는 콘텐츠 검색 웹 파트 (CSWP)입니다. 이 웹 파트는 검색 인덱스를 사용 하 여 사용자에 게 표시 되는 결과를 빠르게 검색 합니다. 페이지에서 CQWP (콘텐츠 쿼리 웹 파트) 대신 콘텐츠 검색 웹 파트를 사용 하 여 사용자의 성능을 향상 시킬 수 있습니다.
  
콘텐츠 쿼리 웹 파트에서 콘텐츠 검색 웹 파트를 사용 하면 거의 대부분 SharePoint Online의 페이지 로드 성능이 크게 향상 됩니다. 적절 한 쿼리를 가져오는 데에는 약간의 추가 구성이 있지만 성능 향상과 사용자에 대 한 만족도가 향상 됩니다.
  
## <a name="comparing-the-performance-gain-you-get-from-using-content-search-web-part-instead-of-content-query-web-part"></a>콘텐츠 쿼리 웹 파트 대신 콘텐츠 검색 웹 파트를 사용 하 여 얻을 수 있는 성능 향상 비교

다음 예제에서는 콘텐츠 쿼리 웹 파트 대신 콘텐츠 검색 웹 파트를 사용할 때 얻을 수 있는 상대적인 성능 향상을 보여 줍니다. 복잡 한 사이트 구조와 매우 광범위 한 콘텐츠 쿼리를 통해 더 확실 한 결과를 확인할 수 있습니다.
  
이 예제 사이트의 특징은 다음과 같습니다.
  
- 8 개 수준 하위 사이트
    
- 사용자 지정 "과일" 콘텐츠 형식을 사용 하는 목록
    
- 웹 파트에서 콘텐츠 쿼리는 광범위 하며 콘텐츠 형식이 "과일" 인 모든 항목을 반환 합니다.
    
- 이 예제에서는 8 개 사이트에서 50 항목만 사용 합니다. 콘텐츠가 더 많은 사이트의 경우에도 효과가 더 두드러지게 나타납니다.
    
다음은 콘텐츠 쿼리 웹 파트의 결과에 대 한 스크린 샷입니다.
  
![웹 파트에 대한 콘텐츠 쿼리를 보여 주는 그래픽](media/b3d41f20-dfe5-46ed-9c0a-31057e82de33.png)
  
Internet Explorer에서 F12 개발자 도구의 **네트워크** 탭을 사용 하 여 응답 헤더에 대 한 세부 정보를 확인 합니다. 다음 스크린샷에서이 페이지 부하에 대 한 **Sprequestduration** 값은 924 밀리초입니다. 
  
![924의 요청 기간을 보여 주는 스크린샷](media/343571f2-a249-4de2-bc11-2cee93498aea.png)
  
 **Sprequestduration** 은 서버에서 페이지를 준비 하기 위해 수행 하는 작업의 양을 나타냅니다. 검색 웹 파트 별로 콘텐츠를 쿼리 웹 파트 별로 전환 하면 페이지를 렌더링 하는 데 걸리는 시간이 크게 줄어듭니다. 이와 대조적으로 동일한 결과 수를 반환 하는 해당 콘텐츠 검색 웹 파트가 포함 된 페이지에는이 스크린샷에 표시 된 것 처럼 **Sprequestduration** 값이 106 밀리초가 됩니다. 
  
![106의 요청 기간을 보여 주는 스크린샷](media/b46387ac-660d-4e5e-a11c-cc430e912962.png)
  
## <a name="adding-a-content-search-web-part-in-sharepoint-online"></a>SharePoint Online에서 콘텐츠 검색 웹 파트 추가

콘텐츠 검색 웹 파트를 추가 하는 것은 일반 콘텐츠 쿼리 웹 파트와 매우 비슷합니다. [Configure a Content Search Web part In SharePoint의](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a) *"콘텐츠 검색 웹 파트 추가"* 섹션을 참조 하세요.
  
## <a name="creating-the-right-search-query-for-your-content-search-web-part"></a>콘텐츠 검색 웹 파트에 대 한 올바른 검색 쿼리 만들기

콘텐츠 검색 웹 파트를 추가한 후에는 검색을 구체화 하 고 원하는 항목을 반환할 수 있습니다. 이 작업을 수행 하는 방법에 대 한 자세한 내용은 [Configure a Content Search Web part In SharePoint의](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a) *"콘텐츠 검색 웹 파트에서 고급 쿼리를 구성 하 여 콘텐츠 표시"* 섹션을 참조 하십시오.
  
## <a name="query-building-and-testing-tool"></a>쿼리 작성 및 테스트 도구

복잡 한 쿼리를 작성 하 고 테스트 하기 위한 도구는 Codeplex에서 [검색 쿼리 도구](https://sp2013searchtool.codeplex.com/) 를 참조 하세요. 
  

