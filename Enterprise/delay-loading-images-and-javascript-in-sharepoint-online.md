---
title: SharePoint Online에서 이미지 및 JavaScript 로드 지연
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 12/29/2016
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 74d327e5-755f-4135-b9a5-7b79578c1bf9
description: 이 문서에서는 이미지를 로드 하는 지연 시간을 JavaScript를 사용 하 여 및 대기 페이지 로드 한 다음 이전에 필수적이 지 않은 JavaScript를 로드 하 여 SharePoint Online 페이지 로드 시간을 줄일 수는 방법을 설명 합니다.
ms.openlocfilehash: b8b052d85c99e51dff4b0fc747b3b52c17de8d8b
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542145"
---
# <a name="delay-loading-images-and-javascript-in-sharepoint-online"></a><span data-ttu-id="1edee-103">SharePoint Online에서 이미지 및 JavaScript 로드 지연</span><span class="sxs-lookup"><span data-stu-id="1edee-103">Delay loading images and JavaScript in SharePoint Online</span></span>

<span data-ttu-id="1edee-104">이 문서에서는 이미지를 로드 하는 지연 시간을 JavaScript를 사용 하 여 및 대기 페이지 로드 한 다음 이전에 필수적이 지 않은 JavaScript를 로드 하 여 SharePoint Online 페이지 로드 시간을 줄일 수는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="1edee-104">This article describes how you can decrease the load time for SharePoint Online pages by using JavaScript to delay loading images and also by waiting to load non-essential JavaScript until after the page loads.</span></span> 
  
<span data-ttu-id="1edee-p101">이미지는 SharePoint Online의 페이지 로드 시 속도가 저하될 수 있습니다. 기본적으로 대부분의 최신 인터넷 브라우저는 HTML 페이지를 로드할 때 이미지를 미리 가져옵니다. 이로 인해 아래로 스크롤할 때까지 이미지가 화면에 표시되지 않을 경우 페이지를 로드할 때 불필요하게 느려질 수 있습니다. 이미지는 브라우저에서 페이지의 보이는 부분을 로드하지 못하게 차단할 수 있습니다. 이 문제를 해결하려면 JavaScript를 사용하여 먼저 이미지 로드를 건너뛰면 됩니다. 또한 필수적이지 않은 JavaScript를 로드하면 SharePoint 페이지의 로드 시간이 느려질 수 있습니다. 이 항목에서는 SharePoint Online에서 JavaScript를 사용하여 페이지 로드 시간을 향상시키는 데 사용할 수 있는 몇 가지 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1edee-p101">Images can negatively affect page load speeds on SharePoint Online. By default, most modern Internet browsers pre-fetch images when loading an HTML page. This can cause the page to be unnecessarily slow to load if the images are not visible on the screen until the user scrolls down. The images can block the browser from loading the visible part of the page. To work around this problem, you can use JavaScript to skip loading the images first. Also, loading non-essential JavaScript can slow down load times on your SharePoint pages too. This topic describes some methods you can use to improve page load times with JavaScript in SharePoint Online.</span></span> 
  
## <a name="improve-page-load-times-by-delaying-image-loading-in-sharepoint-online-pages-by-using-javascript"></a><span data-ttu-id="1edee-112">JavaScript를 사용하여 SharePoint Online 페이지의 이미지 로드를 지연시켜 페이지 로드 시간 개선</span><span class="sxs-lookup"><span data-stu-id="1edee-112">Improve page load times by delaying image loading in SharePoint Online pages by using JavaScript</span></span>

<span data-ttu-id="1edee-p102">사전 반입 이미지에서 웹 브라우저를 방지 하기 위해 JavaScript를 사용할 수 있습니다. 전체 문서 렌더링 속도가 향상 됩니다. src 특성의 값을 제거 하면이 작업을 수행 하는 \<img\> 태그를 지정 하 고 같은 데이터 특성에 파일의 경로를 교체: 데이터 src 합니다. 예를 들어:</span><span class="sxs-lookup"><span data-stu-id="1edee-p102">You can use JavaScript to prevent a web browser from pre-fetching images. This speeds up overall document rendering. To do this you remove the value of the src attribute from the \<img\> tag and replace it with the path to a file in a data attribute such as: data-src. For example:</span></span>
  
```
<img src="" data-src="/sites/NavigationBySearch/_catalogs/masterpage/media/microsoft-white-8.jpg" />
```

<span data-ttu-id="1edee-p103">이 메서드를 사용 하 여 브라우저에서 이미지를 즉시 다운로드 하지 않습니다. 이미지의 뷰포트에 이미 있으면 JavaScript 데이터 특성에서 URL을 검색 하 고 src 특성에 대 한 값으로 삽입 브라우저에 지시 합니다. 까지 스크롤하면으로만 로드 하는 이미지 및 보기에 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="1edee-p103">By using this method, the browser doesn't download the images immediately. If the image is already in the viewport, JavaScript tells the browser to retrieve the URL from the data attribute and insert it as the value for the src attribute. The image only loads as the user scrolls and it comes into view.</span></span>
  
<span data-ttu-id="1edee-119">이 모든 것을 확인 하려면 들 해야 JavaScript를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1edee-119">To make all of this happen, you'll need to use JavaScript.</span></span>
  
<span data-ttu-id="1edee-120">텍스트 파일에서 **isElementInViewport()** 함수를 정의하여 요소가 사용자에게 표시되는 브라우저의 일부인지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="1edee-120">In a text file, define the **isElementInViewport()** function to check whether or not an element is in the part of the browser that is visible to the user.</span></span> 
  
```
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

<span data-ttu-id="1edee-p104">그런 다음 **loadItemsInView()** 함수에 **isElementInViewport()** 를 사용합니다. **loadItemsInView()** 함수는 이미지가 사용자에게 표시되는 브라우저의 일부인 경우 data-src 특성 값이 있는 모든 이미지를 로드합니다. 텍스트 파일에 다음 함수를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="1edee-p104">Next, use **isElementInViewport()** in the **loadItemsInView()** function. The **loadItemsInView()** function will load all images that have a value for the data-src attribute if they are in the part of the browser that is visible to the user. Add the following function to the text file:</span></span> 
  
```
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

<span data-ttu-id="1edee-p105">마지막으로 다음 예제와 같이 **window.onscroll()** 내에서 **loadItemsInView()** 를 호출합니다. 이렇게 하면 뷰포트의 이미지가 사용자에게 필요하기 전까지 로드되지 않습니다. 텍스트 파일에 다음을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="1edee-p105">Finally, call **loadItemsInView()** from within **window.onscroll()** as shown in the following example. This ensures that any images that are in the viewport are loaded as the user needs them, but not before. Add the following to the text file:</span></span> 
  
```
//Example of calling loadItemsInView() from within window.onscroll()
$(window).on("scroll", function () {
    loadItemsInView();
});

```

<span data-ttu-id="1edee-p106">SharePoint Online에 대 한 다음 함수는 스크롤 이벤트는 #s4-작업에 연결 해야하는 \<div\> 태그입니다. 즉, 창 이벤트는 페이지의 위쪽에 연결 된 리본 메뉴 유지 하기 위해 재정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1edee-p106">For SharePoint Online, you need to attach the following function to the scroll event on the #s4-workspace \<div\> tag. This is because the window events are overridden in order to ensure the ribbon remains attached to the top of the page.</span></span>
  
```
//Keep the ribbon at the top of the page
$('#s4-workspace').on("scroll", function () {
    loadItemsInView();
});
```

<span data-ttu-id="1edee-129">텍스트 파일을 확장명이 .js인 JavaScript 파일(예: delayLoadImages.js)로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="1edee-129">Save the text file as a JavaScript file with the extension .js, for example delayLoadImages.js.</span></span>
  
<span data-ttu-id="1edee-p107">DelayLoadImages.js 작성 (영문)을 완료 한 후에 SharePoint Online에서 마스터 페이지에 파일의 내용을 추가할 수 있습니다. 마스터 페이지의 머리글에 스크립트 링크를 추가 하 여이 작업을 수행 합니다. 다음은 마스터 페이지, 되 면 해당 마스터 페이지 레이아웃을 사용 하는 SharePoint Online 사이트의 모든 페이지에 JavaScript 적용 됩니다. 또는 사이트의 한 페이지에만이 사용 하려는 경우 사용 하 여 스크립트 편집기 웹 파트 페이지에 JavaScript를 포함 합니다. 자세한 내용은 다음이 항목을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="1edee-p107">Once you've finished writing delayLoadImages.js, you can add the contents of the file to a master page in SharePoint Online. You do this by adding a script link to the header in the master page. Once it's in a master page, the JavaScript will be applied to all pages in your SharePoint Online site that use that master page layout. Alternatively, if you intend to only use this on one page of your site, use the script editor Web Part to embed the JavaScript into the page. See these topics for more information:</span></span>
  
- [<span data-ttu-id="1edee-135">방법: 마스터 페이지를 SharePoint 2013에서 사이트에 적용</span><span class="sxs-lookup"><span data-stu-id="1edee-135">How to: Apply a master page to a site in SharePoint 2013</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=525627)
    
- [<span data-ttu-id="1edee-136">방법: SharePoint 2013의 페이지 레이아웃 만들기</span><span class="sxs-lookup"><span data-stu-id="1edee-136">How to: Create a page layout in SharePoint 2013</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=525628)
    
 <span data-ttu-id="1edee-137">**예: SharePoint Online의 마스터 페이지에서 JavaScript delayLoadImages.js 파일 참조**</span><span class="sxs-lookup"><span data-stu-id="1edee-137">**Example: Referencing the JavaScript delayLoadImages.js file from a master page in SharePoint Online**</span></span>
  
<span data-ttu-id="1edee-p108">이를 위해서는 마스터 페이지에서 jQuery를 참조해야 합니다. 다음 예는 초기 페이지 로드에서 이미지가 하나만 로드되었으나 페이지에 여러 이미지가 더 있는 상황을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="1edee-p108">In order for this to work, you also need to reference jQuery in the master page. In the following example, you can see in the initial page load that there is only one image loaded but there are several more on the page.</span></span>
  
![페이지에 로드된 하나의 이미지를 보여 주는 스크린샷](media/3d177ddb-67e5-43a7-b327-c9f9566ca937.png)
  
<span data-ttu-id="1edee-141">다음 스크린샷에는 보기로 스크롤한 후에 다운로드되는 나머지 이미지가 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1edee-141">The following screen shot shows the rest of the images that are downloaded after they scroll into view.</span></span>
  
![페이지에 로드된 여러 페이지를 보여 주는 스크린샷](media/95eb2b14-f6a1-4eac-a5cb-96097e49514c.png)
  
<span data-ttu-id="1edee-p109">JavaScript를 사용하여 이미지 로드를 지연시키는 방식은 성능이 향상되는 효과적인 방법이 될 수 있지만, 이 방법을 공용 웹 사이트에 적용하면 검색 엔진이 일반적인 형식의 이미지를 크롤링할 때와 같은 방식으로 이미지를 크롤링할 수 없습니다. 이 경우 이미지 자체의 메타데이터가 페이지를 로드할 때까지는 실제로 존재하지 않으므로 검색 엔진의 순위에 영향을 줄 수 있습니다. 검색 엔진 크롤러는 HTML만 읽으므로 이미지가 페이지의 콘텐츠로 표시되지 않습니다. 이미지는 검색 결과에서 페이지 순위를 매기는 데 사용되는 요소 중 하나입니다. 이 문제를 해결하는 한 가지 방법은 이미지에 대한 소개 텍스트를 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="1edee-p109">Delaying image loading by using JavaScript can be an effective technique in increasing performance; however, if the technique is applied on a public website then search engines are not able to crawl the images in the same way they would crawl a regularly formed image. This can affect rankings on search engines because metadata on the image itself is not really there until the page loads. Search engine crawlers only read the HTML and therefore will not see the images as content on the page. Images are one of the factors used to rank pages in search results. One way to work around this is to use introductory text for your images.</span></span>
  
## <a name="github-code-sample-injecting-javascript-to-improve-performance"></a><span data-ttu-id="1edee-148">GitHub 코드 샘플: JavaScript를 삽입하여 성능 향상</span><span class="sxs-lookup"><span data-stu-id="1edee-148">GitHub code sample: Injecting JavaScript to improve performance</span></span>

<span data-ttu-id="1edee-149">GitHub에서 제공 하는 [JavaScript 주입](https://go.microsoft.com/fwlink/p/?LinkId=524759) 에서 문서 및 코드 샘플을 놓치지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="1edee-149">Don't miss the article and code sample on [JavaScript injection](https://go.microsoft.com/fwlink/p/?LinkId=524759) provided on GitHub.</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="1edee-150">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1edee-150">See also</span></span>

[<span data-ttu-id="1edee-151">Office 365 ProPlus 및 Office 2013에서 지원 되는 브라우저</span><span class="sxs-lookup"><span data-stu-id="1edee-151">Supported browsers in Office 2013 and Office 365 ProPlus</span></span>](https://support.office.com/article/57342811-0dc4-4316-b773-20082ced8a82)
  
[<span data-ttu-id="1edee-152">방법: 마스터 페이지를 SharePoint 2013에서 사이트에 적용</span><span class="sxs-lookup"><span data-stu-id="1edee-152">How to: Apply a master page to a site in SharePoint 2013</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=525627)
  
[<span data-ttu-id="1edee-153">방법: SharePoint 2013의 페이지 레이아웃 만들기</span><span class="sxs-lookup"><span data-stu-id="1edee-153">How to: Create a page layout in SharePoint 2013</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=525628)

