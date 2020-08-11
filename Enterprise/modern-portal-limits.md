---
title: SharePoint Online 최신 포털 사이트 제한
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 10/9/2019
audience: Admin
ms.topic: interactive-tutorial
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Strat_O365_Enterprise
- SPO_Content
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
description: 'Sharepoint Online의 최신 사이트에 대 한 성능 권장 사항에 대해 설명 하 고 (예: 외부 끝점에 대 한 통화 제한)에 대해 알아봅니다.'
ms.openlocfilehash: 1ec6dfb4b32a8915528adce168badf3645c26e48
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606884"
---
# <a name="sharepoint-online-modern-portal-site-limits"></a>SharePoint Online 최신 포털 사이트 제한

이 문서에서는 SharePoint Online의 최신 포털 사이트에 대 한 성능 권장 사항을 제공 합니다. 이 문서의 지침을 사용 하 여 최신 포털 사이트 성능을 최적화 하 고 일반적인 성능 문제를 방지할 수 있습니다.

## <a name="performance-considerations-for-modern-portal-sites"></a>최신 포털 사이트에 대 한 성능 고려 사항

성능 최적화 측면에서 최신 포털 사이트를 고유 하 게 만드는 몇 가지 특징이 있습니다. SharePoint Online에서 공동 작업과 포털 사이트의 주요 차이점은 단위입니다. 일반적으로 포털 사이트는 공동 작업 사이트 보다 더 많은 수의 사용자에 게 페이지 보기를 많이 제공 하며, 정적 콘텐츠 및 편집 가능한 리소스의 수가 더 적습니다. 또한 최신 사이트의 아키텍처는 렌더링 페이지와 코드 실행에 수반 되는 대부분의 처리가 서버가 아닌 클라이언트에서 수행 된다는 점에서 클래식 사이트와 다릅니다.

최신 포털 사이트에 대 한 성능 최적화는 주로 다음과 같은 몇 가지 전반적인 목표를 중심으로 합니다.

- 각 사이트 페이지의 구성 요소 전체 크기 줄이기
- 이미지, 스타일 시트, 스크립트 등의 일반적인 정적 파일을 CDN에 호스팅
- SharePoint 및 외부 끝점에 대 한 호출만 필요한 것으로 제한
- 동일한 콘텐츠에 대 한 중복 요청 방지

이 문서에 나오는 대부분의 지침은 SharePoint Online에 대 한 호출을 최소화 하 고 최적화 하는 데 중점을 둔 것입니다. 페이지를 로드할 때마다 반복 되는 통화를 설정 하면 변경 되지 않았더라도 서비스에서 정보가 검색 됨에 따라 사용자의 성능에 영향을 줍니다. 따라서 SharePoint에 대 한 요청은 모든 사용자에 게 공통적으로 사용 되는 호출이 나 개별 사용자에 게 필요한 통화 중 하나로 분류할 수 있습니다. 사용자 환경을 최적화 하기 위해 이러한 두 통화 범주의 결과를 캐시 해야 합니다.

>[!NOTE]
>Sharepoint Online 사이트 페이지에서 특정 성능 메트릭 분석을 시작 하는 출발점으로 [페이지 진단 도구](https://aka.ms/perftool) 를 사용 합니다.

## <a name="modern-portal-site-limits-and-recommendations"></a>최신 포털 사이트 제한 및 권장 사항

|**제한 유형**|**최대 권장 값**|**참고**|
|:-----|:-----|:-----|:-----|
|페이지 및 뉴스 항목  <br/> |사이트당 5,000개  <br/> |최신 포털 사이트의 페이지 및 뉴스 항목 수를 5000 미만으로 제한 하는 것이 좋습니다.  <br/> |
|페이지의 웹 파트  <br/> |페이지당 20 개  <br/> |기본 Microsoft 웹 파트와 사용자 지정 웹 파트를 모두 포함 하 여 페이지 마다 20 개 이하의 전체 웹 파트를 사용 하는 것이 좋습니다. <br/> 자세한 내용은 [SharePoint Online 최신 사이트 페이지에서 웹 파트 성능 최적화](modern-web-part-optimization.md)를 참조 하세요.  <br/> |
|페이지의 동적 웹 파트  <br/> |페이지당 4 개  <br/> |SharePoint에 대해 하나 이상의 쿼리를 수행 하 여 최신 데이터를 페치 하는 동적 웹 파트는 페이지당 4 개로 제한 됩니다. _뉴스_ 웹 파트는 동적 웹 파트의 예입니다. <br/> 자세한 내용은 [SharePoint Online 최신 사이트 페이지에서 웹 파트 성능 최적화](modern-web-part-optimization.md)를 참조 하세요.    <br/> |
|보안 그룹  <br/> |사이트당 20 개  <br/> |보안 그룹의 수는 최신 포털 사이트에서 많은 쿼리 확장에 영향을 줍니다. 보안 그룹의 수는 사이트 당 20 개 이하의 가능한 한 작은 집합으로 제한 하는 것이 좋습니다.  <br/> |
|사이트 탐색의 항목  <br/> |사이트당 100  <br/> |사이트 탐색에는 100 개 미만의 항목을 추가 하 고 기본 탐색 컨트롤을 사용 하는 것이 좋습니다.  <br/> 자세한 내용은 [SharePoint Online 최신 사이트 페이지에서 페이지 가중치 최적화](modern-page-weight-optimization.md)를 참조 하세요. <br/> |
|최대 이미지 크기  <br/> |이미지 당 300  <br/> |이미지, 스타일 시트 및 스크립트를 호스트 하는 데 CDN을 사용 하는 것이 좋습니다. <br/>자세한 내용은 [Sharepoint online 최신 사이트 페이지에서 이미지 최적화](modern-image-optimization.md) 및 [Office 365 CDN (Content Delivery Network)을 sharepoint Online과 함께 사용](use-office-365-cdn-with-spo.md)을 참조 하세요.  <br/> |
|편집 권한이 있는 사용자  <br/> |사이트 당 사용자 200 명  <br/> |SharePoint 포털 사이트는 콘텐츠 보기 및 소비를 위해 최적화 됩니다. 편집 권한은 추가 컨트롤을 다운로드 하므로 해당 사용자에 대해 더 느리게 수행 되므로 포털에 대 한 편집 권한은 제한 된 사용자 그룹으로 제한 됩니다. 따라서 편집 권한이 있는 사용자 수가 지나치게 많으면 전체 환경에 영향을 줍니다. <br/> |
|타사 Iframe  <br/> |페이지당 2 개  <br/> |Iframe은 javascript, CSS 및 framework 요소와 같은 연결 된 모든 콘텐츠를 포함 하 여 별도의 외부 페이지를 로드 하므로 예기치 않게 속도가 느립니다. Iframe을 사용 해야 하는 경우 페이지당 개수를 2 개 이하로 제한 합니다.<br/> 자세한 내용은 [SharePoint Online 최신 및 클래식 게시 사이트 페이지에서 Iframe 최적화](modern-iframe-optimization.md)를 참조 하세요. <br/> |
|UPA 서비스에 대 한 호출  <br/> |시간당 사용자 당 1 회  <br/> |UPA (사용자 프로필 응용 프로그램) 서비스에 대 한 _요청당 요청만_ 하지 않도록 설정 하는 것이 좋습니다. [Microsoft GRAPH API](https://docs.microsoft.com/graph/call-api) 및 [pagecontext](https://docs.microsoft.com/javascript/api/sp-page-context/pagecontext?view=sp-typescript-latest) 를 사용 하 여 사용자 정보를 쿼리할 수 있습니다.  <br/> UPA 서비스 호출이 필요한 경우 필요한 경우 단일 통화를 수행한 다음 동일한 세션에서 다시 사용할 수 있도록 정보를 캐시 합니다. |
|분류 서비스에 대 한 호출  <br/> |시간당 사용자 당 5 명  <br/> |분류 서비스에 대해 _요청당 요청_ 수를 만드는 것이 좋습니다. 분류 서비스 호출이 필요한 경우에는 동일한 세션에서 다시 사용할 수 있도록 정보를 캐시 합니다. <br/> 자세한 내용은 [SharePoint Online 최신 및 클래식 게시 사이트 페이지에서 페이지 통화 최적화](modern-page-call-optimization.md)를 참조 하세요. <br/> |

## <a name="related-topics"></a>관련 항목

[정상 SharePoint 포털 만들기](https://docs.microsoft.com/sharepoint/portal-health)

[SharePoint Online 성능 조정](tune-sharepoint-online-performance.md)

[Office 365 성능 조정](tune-office-365-performance.md)

[SharePoint Online 제한 사항](https://docs.microsoft.com/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-limits)

[최신 SharePoint 환경의 성능](https://docs.microsoft.com/sharepoint/modern-experience-performance)

[SharePoint Online 포털에 대한 성능 지침](https://docs.microsoft.com/sharepoint/dev/solution-guidance/portal-performance)
