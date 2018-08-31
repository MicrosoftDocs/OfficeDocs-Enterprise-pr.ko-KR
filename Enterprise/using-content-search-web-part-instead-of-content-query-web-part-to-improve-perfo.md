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
# <a name="using-content-search-web-part-instead-of-content-query-web-part-to-improve-performance-in-sharepoint-online"></a><span data-ttu-id="12f52-103">콘텐츠 쿼리 웹 파트는 대신 콘텐츠 검색 웹 파트를 사용 하 여 SharePoint Online에서 성능을 개선합니다</span><span class="sxs-lookup"><span data-stu-id="12f52-103">Using Content Search Web Part instead of Content Query Web Part to improve performance in SharePoint Online</span></span>

<span data-ttu-id="12f52-104">이 문서에서는 SharePoint Server 2013 및 SharePoint Online에서 콘텐츠 검색 웹 파트와 콘텐츠 쿼리 웹 파트를 대체 하 여 성능을 개선 하는 방법에 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="12f52-104">This article describes how to increase performance by replacing the Content Query Web Part with the Content Search Web Part in SharePoint Server 2013 and SharePoint Online.</span></span>
  
<span data-ttu-id="12f52-p101">SharePoint Server 2013 및 SharePoint Online의 가장 강력한 새로운 기능 중 하나는 콘텐츠 검색 웹 파트 (CSWP)입니다. 이 웹 파트와 같은 검색 인덱스를 사용 하 여 신속 하 게 사용자에 게 표시 되는 결과 검색 합니다. 대신는 콘텐츠 쿼리 웹 파트 (CQWP) 페이지에서 콘텐츠 검색 웹 파트 사용 하 여 사용자에 대 한 성능 향상을 위해.</span><span class="sxs-lookup"><span data-stu-id="12f52-p101">One of the most powerful new features of SharePoint Server 2013 and SharePoint Online is the Content Search Web Part (CSWP). This Web Part uses the search index to quickly retrieve results which are shown to the user. Use the Content Search Web Part instead of the Content Query Web Part (CQWP) in your pages to improve performance for your users.</span></span>
  
<span data-ttu-id="12f52-p102">콘텐츠 검색 웹 파트를 사용 하 여 콘텐츠 쿼리 웹 파트를 통해 SharePoint Online에서 페이지 부하 성능이 크게 향상 거의 항상 발생 합니다. 오른쪽 쿼리를 가져올 약간의 추가 구성 이지만 성능 향상된 및 만족도 사용자는 보상 됩니다.</span><span class="sxs-lookup"><span data-stu-id="12f52-p102">Using a Content Search Web Part over a Content Query Web Part will almost always result in significantly better page load performance on SharePoint Online. There is a little additional configuration to get the right query, but the rewards are improved performance and happier users.</span></span>
  
## <a name="comparing-the-performance-gain-you-get-from-using-content-search-web-part-instead-of-content-query-web-part"></a><span data-ttu-id="12f52-110">콘텐츠 검색 웹 파트를 사용 하 여 콘텐츠 쿼리 웹 파트는 대신에서 가져올 성능 향상 비교 (영문)</span><span class="sxs-lookup"><span data-stu-id="12f52-110">Comparing the performance gain you get from using Content Search Web Part instead of Content Query Web Part</span></span>

<span data-ttu-id="12f52-p103">다음 예제에서는 콘텐츠 검색 웹 파트를 사용 하 여 콘텐츠 쿼리 웹 파트는 대신 때 나타날 수 상대 성능 향상을 보여줍니다. 효과 복잡 한 사이트 구조와 매우 광범위 한 콘텐츠 쿼리 보다 명확 하 게 합니다.</span><span class="sxs-lookup"><span data-stu-id="12f52-p103">The following examples show the relative performance gains you may receive when you use a Content Search Web Part instead of a Content Query Web Part. The effects are more obvious with a complex site structure and very broad content queries.</span></span>
  
<span data-ttu-id="12f52-113">이 예제에서는 사이트에는 다음과 같은 특징이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12f52-113">This example site has the following characteristics:</span></span>
  
- <span data-ttu-id="12f52-114">하위 사이트 수준의 8입니다.</span><span class="sxs-lookup"><span data-stu-id="12f52-114">8 levels of subsites.</span></span>
    
- <span data-ttu-id="12f52-115">사용자 지정 "과일" 콘텐츠 형식을 사용 하 여 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="12f52-115">Lists using a custom "fruit" content type.</span></span>
    
- <span data-ttu-id="12f52-116">웹 파트에서 콘텐츠 쿼리는 광범위 한 "과일"의 콘텐츠 형식 사용 하는 모든 항목을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="12f52-116">In the Web Part, the content query is broad, returning all items with the content type of "fruit".</span></span>
    
- <span data-ttu-id="12f52-p104">이 예제에서는 8 사이트에 걸쳐 50 개의 항목을만 사용 합니다. 더 많은 콘텐츠가 포함 된 사이트에 대 한 효과 훨씬 더 많이 듭니다 될 됩니다.</span><span class="sxs-lookup"><span data-stu-id="12f52-p104">The example only uses 50 items across the 8 sites. The effects will be even more pronounced for sites with more content.</span></span>
    
<span data-ttu-id="12f52-119">스크린샷 콘텐츠 쿼리 웹 파트의 결과 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="12f52-119">Here is a screen shot of the results of the Content Query Web Part.</span></span>
  
![웹 파트에 대한 콘텐츠 쿼리를 보여 주는 그래픽](media/b3d41f20-dfe5-46ed-9c0a-31057e82de33.png)
  
<span data-ttu-id="12f52-p105">Internet Explorer에서 응답 헤더에 대 한 세부 정보를 살펴보는 F12 개발자 도구에 있는 **네트워크** 탭을 사용 합니다. 다음 화면에,이 페이지 부하에 대 한 **SPRequestDuration** 에 대 한 값은 924 밀리초입니다.</span><span class="sxs-lookup"><span data-stu-id="12f52-p105">In Internet Explorer, use the **Network** tab of the F12 developer tools to look at the details for the response header. In the following screen shot, the value for the **SPRequestDuration** for this page load is 924 milliseconds.</span></span> 
  
![924의 요청 기간을 보여 주는 스크린샷](media/343571f2-a249-4de2-bc11-2cee93498aea.png)
  
 <span data-ttu-id="12f52-p106">**SPRequestDuration** 페이지를 준비 하는 서버에서 작업을 수행 하는 작업의 크기를 나타냅니다. 콘텐츠 검색 웹 파트를 사용 하 여 쿼리 웹 파트에서 콘텐츠를 크게 전환 페이지를 렌더링 하는데 걸리는 시간이 줄어듭니다. 반면, 해당 하는 콘텐츠 검색 웹 파트 페이지 106 시간 (밀리초)이 스크린샷은 같이 **SPRequestDuration** 값이 동일한 결과 수를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="12f52-p106">**SPRequestDuration** indicates the amount of work that is done on the server to prepare the page. Switching Content by Query Web Parts with Content by Search Web Parts dramatically reduces the time it takes to render the page. By contrast, a page with an equivalent Content Search Web Part, returning the same number of results has an **SPRequestDuration** value of 106 milliseconds as shown in this screen shot:</span></span> 
  
![106의 요청 기간을 보여 주는 스크린샷](media/b46387ac-660d-4e5e-a11c-cc430e912962.png)
  
## <a name="adding-a-content-search-web-part-in-sharepoint-online"></a><span data-ttu-id="12f52-128">SharePoint에서 온라인 콘텐츠 검색 웹 파트를 추가</span><span class="sxs-lookup"><span data-stu-id="12f52-128">Adding a Content Search Web Part in SharePoint Online</span></span>

<span data-ttu-id="12f52-p107">콘텐츠 검색 웹 파트를 추가 하는 것은 일반 콘텐츠 쿼리 웹 파트와 매우 유사 합니다. [SharePoint에서 콘텐츠 검색 웹 파트 구성](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a)에서 *"콘텐츠 검색 웹 파트 추가"* 섹션을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="12f52-p107">Adding a Content Search Web Part is very similar to a regular Content Query Web Part. See the section  *"Add a Content Search Web Part"*  in [Configure a Content Search Web Part in SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).</span></span>
  
## <a name="creating-the-right-search-query-for-your-content-search-web-part"></a><span data-ttu-id="12f52-131">콘텐츠 검색 웹 파트에 대 한 올바른 검색 쿼리 만들기 (영문)</span><span class="sxs-lookup"><span data-stu-id="12f52-131">Creating the right search query for your Content Search Web Part</span></span>

<span data-ttu-id="12f52-p108">콘텐츠 검색 웹 파트를 추가 하 고 나면 검색을 구체화할 수 있으며 원하는 항목을 반환할 수 있습니다. 이 작업을 수행 하는 방법에 대 한 자세한 내용은 [Configure SharePoint에서 콘텐츠 검색 웹 파트의](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a)에서 *"콘텐츠 검색 웹 파트에 고급 쿼리를 구성 하 여 콘텐츠 표시"* 섹션을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="12f52-p108">Once you have added a Content Search Web Part, you can refine the search and return the items you want. For detailed instructions on how to do this, see the section,  *"Display content by configuring an advanced query in a Content Search Web Part"*  in [Configure a Content Search Web Part in SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).</span></span>
  
## <a name="query-building-and-testing-tool"></a><span data-ttu-id="12f52-134">쿼리 작성 및 테스트 도구</span><span class="sxs-lookup"><span data-stu-id="12f52-134">Query building and testing tool</span></span>

<span data-ttu-id="12f52-135">구성 하 고 복잡 한 쿼리를 테스트 하는 도구에 대 한 Codeplex에서 [검색 쿼리 도구](https://sp2013searchtool.codeplex.com/) 를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="12f52-135">For a tool to build and test complex queries, see the [Search Query Tool](https://sp2013searchtool.codeplex.com/) on Codeplex.</span></span> 
  

