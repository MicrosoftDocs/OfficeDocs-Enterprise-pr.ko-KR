---
title: SharePoint Online에서 이미지 및 JavaScript 로드 지연
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/3/2019
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 74d327e5-755f-4135-b9a5-7b79578c1bf9
description: 이 문서에서는 페이지를 로드할 때까지 JavaScript를 사용 하 여 이미지 로드를 지연 시키고 불필요 한 JavaScript 로드를 기다리는 방법으로 SharePoint Online 페이지의 로드 시간을 줄이는 방법에 대해 설명 합니다.
ms.openlocfilehash: 86efb767e80927f7d3f5d8055676e6d99da4d667
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41840565"
---
# <a name="delay-loading-images-and-javascript-in-sharepoint-online"></a>SharePoint Online에서 이미지 및 JavaScript 로드 지연

이 문서에서는 페이지를 로드할 때까지 JavaScript를 사용 하 여 이미지 로드를 지연 시키고 불필요 한 JavaScript 로드를 기다리는 방법으로 SharePoint Online 페이지의 로드 시간을 줄이는 방법에 대해 설명 합니다.
  
이미지는 SharePoint Online의 페이지 로드 속도에 부정적인 영향을 줄 수 있습니다. 기본적으로 대부분의 최신 인터넷 브라우저는 HTML 페이지를 로드할 때 이미지를 미리 페치 합니다. 이로 인해 사용자가 아래로 스크롤할 때까지 이미지가 화면에 표시 되지 않는 경우 페이지가 불필요 하 게 더 느리게 로드 될 수 있습니다. 이미지는 브라우저가 페이지의 표시 되는 부분을 로드 하지 못하게 차단할 수 있습니다. 이 문제를 해결 하려면 JavaScript를 사용 하 여 이미지 로드를 먼저 건너뛸 수 있습니다. 또한 중요 하지 않은 JavaScript를 로드 하면 SharePoint 페이지의 로드 시간도 느려질 수 있습니다. 이 항목에서는 SharePoint Online에서 JavaScript의 페이지 로드 시간을 개선 하는 데 사용할 수 있는 몇 가지 방법에 대해 설명 합니다.
  
## <a name="improve-page-load-times-by-delaying-image-loading-in-sharepoint-online-pages-by-using-javascript"></a>JavaScript를 사용 하 여 SharePoint Online 페이지에서 이미지 로드를 지연 시켜 페이지 로드 시간 개선

JavaScript를 사용 하 여 웹 브라우저에서 이미지를 미리 가져오는 것을 방지할 수 있습니다. 이렇게 하면 전반적인 문서 렌더링이 향상 됩니다. 이렇게 하려면 \<img\> 태그에서 src 특성 값을 제거 하 고 데이터-src와 같은 데이터 특성에 있는 파일에 대 한 경로로 대체 합니다. 예시는 다음과 같습니다:
  
```html
<img src="" data-src="/sites/NavigationBySearch/_catalogs/masterpage/media/microsoft-white-8.jpg" />
```

이 메서드를 사용 하면 브라우저에서 이미지를 즉시 다운로드 하지 않습니다. 이미지가 이미 뷰포트에 있으면 JavaScript가 데이터 특성에서 URL을 검색 하 고이를 src 특성 값으로 삽입 하도록 브라우저에 지시 합니다. 사용자가 스크롤하면 이미지가 스크롤되어 표시 됩니다.
  
이러한 모든 작업을 수행 하려면 JavaScript를 사용 해야 합니다.
  
텍스트 파일에서 **Iselementinviewport ()** 함수를 정의 하 여 요소가 사용자에 게 표시 되는 브라우저의 일부 인지 여부를 확인 합니다.
  
```javascript
function isElementInViewport(el) {
  if (!el)
    return false;
  var rect = el.getBoundingClientRect();
  return (
    rect.top >= 0 &amp;&amp;
    rect.left >= 0 &amp;&amp;
    rect.bottom <= (window.innerHeight || document.documentElement.clientHeight) &amp;&amp;
    rect.right <= (window.innerWidth || document.documentElement.clientWidth)
  );
}
```

그런 다음 **Loaditemsinview ()** 함수에서 **Iselementinviewport ()** 를 사용 합니다. 사용자에 게 표시 되는 브라우저 부분에 있는 경우 **Loaditemsinview ()** 함수는 데이터 src 특성에 대 한 값이 있는 모든 이미지를 로드 합니다. 텍스트 파일에 다음 함수를 추가 합니다.
  
```javascript
function loadItemsInView() {
  //Select elements by the row id.
  $("#row [data-src]").each(function () {
      var isVisible = isElementInViewport(this);
      if (isVisible) {
          if ($(this).attr("src") == undefined) {
              $(this).attr("src", $(this).data("src"));
          }
      }
  });
}
```

마지막으로, 다음 예와 같이 **window. onscroll ()** 내에서 **Loaditemsinview ()** 를 호출 합니다. 이렇게 하면 사용자가 필요에 따라 뷰포트의 모든 이미지가 로드 되 고 앞에는 표시 되지 않습니다. 텍스트 파일에 다음을 추가 합니다.
  
```javascript
//Example of calling loadItemsInView() from within window.onscroll()
$(window).on("scroll", function () {
    loadItemsInView();
});

```

SharePoint Online의 경우 #s4-workspace \<div\> 태그의 scroll 이벤트에 다음 함수를 연결 해야 합니다. 이는 리본 메뉴가 페이지 맨 위에 계속 연결 되도록 하기 위해 창 이벤트가 재정의 되기 때문입니다.
  
```javascript
//Keep the ribbon at the top of the page
$('#s4-workspace').on("scroll", function () {
    loadItemsInView();
});
```

확장명이 .js 인 JavaScript 파일로 텍스트 파일을 저장 합니다 (예: Delayloadimages.js)로).
  
Delayloadimages.js)로를 작성 한 후에는 SharePoint Online의 마스터 페이지에 파일 내용을 추가할 수 있습니다. 마스터 페이지의 머리글에 스크립트 링크를 추가 하 여이 작업을 수행 합니다. 마스터 페이지에 있는 JavaScript는 해당 마스터 페이지 레이아웃을 사용 하는 SharePoint Online 사이트의 모든 페이지에 적용 됩니다. 또는 사이트의 한 페이지 에서만이 항목을 사용 하려는 경우 스크립트 편집기 웹 파트를 사용 하 여 JavaScript를 페이지에 포함 합니다. 자세한 내용은 다음 항목을 참조 하십시오.
  
- [방법: SharePoint 2013에서 사이트에 마스터 페이지 적용](https://go.microsoft.com/fwlink/p/?LinkId=525627)

- [방법: SharePoint 2013에서 페이지 레이아웃 만들기](https://go.microsoft.com/fwlink/p/?LinkId=525628)

### <a name="example-referencing-the-javascript-delayloadimagesjs-file-from-a-master-page-in-sharepoint-online"></a>예제: SharePoint Online의 마스터 페이지에서 JavaScript Delayloadimages.js)로 파일 참조
  
이 작업을 수행 하려면 마스터 페이지에서 jQuery도 참조 해야 합니다. 다음 예제에서는 이미지가 하나만 로드 되었지만 페이지에 몇 개 더 추가 된 초기 페이지 로드를 볼 수 있습니다.
  
![페이지에 로드된 하나의 이미지를 보여 주는 스크린샷](media/3d177ddb-67e5-43a7-b327-c9f9566ca937.png)
  
다음 스크린샷은 보기로 스크롤한 후에 다운로드 되는 나머지 이미지를 보여 줍니다.
  
![페이지에 로드된 여러 페이지를 보여 주는 스크린샷](media/95eb2b14-f6a1-4eac-a5cb-96097e49514c.png)
  
JavaScript를 사용 하 여 이미지 로드를 지연 시키는 것은 성능 향상의 효과적인 방법이 될 수 있습니다. 그러나 공용 웹 사이트에이 기술이 적용 되는 경우에는 검색 엔진에서 정기적으로 구성 된 이미지를 크롤링하는 것과 같은 방식으로 이미지를 크롤링할 수 없습니다. 이는 페이지를 로드 하기 전 까지는 이미지 자체의 메타 데이터가 실제로 나타나지 않으므로 검색 엔진의 순위에 영향을 줄 수 있습니다. 검색 엔진 크롤러에는 HTML만 읽고 있으므로 페이지에서 이미지를 콘텐츠로 표시 하지 않습니다. 이미지는 검색 결과에서 페이지의 순위를 지정 하는 데 사용 되는 요인 중 하나입니다. 이 문제를 해결 하는 한 가지 방법은 이미지에 소개 텍스트를 사용 하는 것입니다.
  
## <a name="github-code-sample-injecting-javascript-to-improve-performance"></a>GitHub 코드 샘플: JavaScript를 삽입 하 여 성능 개선

GitHub에서 제공 되는 [JavaScript 주입](https://go.microsoft.com/fwlink/p/?LinkId=524759) 에 대 한 문서 및 코드 예제를 놓치지 마세요.
  
## <a name="see-also"></a>참고 항목

[Office 2013 및 Office 365 ProPlus의 지원 되는 브라우저](https://support.office.com/article/57342811-0dc4-4316-b773-20082ced8a82)
  
[방법: SharePoint 2013에서 사이트에 마스터 페이지 적용](https://go.microsoft.com/fwlink/p/?LinkId=525627)
  
[방법: SharePoint 2013에서 페이지 레이아웃 만들기](https://go.microsoft.com/fwlink/p/?LinkId=525628)
