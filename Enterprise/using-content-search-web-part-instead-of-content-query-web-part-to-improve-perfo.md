---
title: SharePoint Online에서 성능을 향상 시키기 위해 콘텐츠 쿼리 웹 파트 대신 콘텐츠 검색 웹 파트 사용
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
description: 이 문서에서는 콘텐츠 쿼리 웹 파트를 sharepoint Server 2013 및 sharepoint Online의 콘텐츠 검색 웹 파트로 대체 하 여 성능을 개선 하는 방법에 대해 설명 합니다.
ms.openlocfilehash: f86a4b75c4bf75ebaa99924411d017c7eb7b6760
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/30/2019
ms.locfileid: "33492178"
---
# <a name="using-content-search-web-part-instead-of-content-query-web-part-to-improve-performance-in-sharepoint-online"></a><span data-ttu-id="1e69d-103">SharePoint Online에서 성능을 향상 시키기 위해 콘텐츠 쿼리 웹 파트 대신 콘텐츠 검색 웹 파트 사용</span><span class="sxs-lookup"><span data-stu-id="1e69d-103">Using Content Search Web Part instead of Content Query Web Part to improve performance in SharePoint Online</span></span>

<span data-ttu-id="1e69d-104">이 문서에서는 콘텐츠 쿼리 웹 파트를 sharepoint Server 2013 및 sharepoint Online의 콘텐츠 검색 웹 파트로 대체 하 여 성능을 개선 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e69d-104">This article describes how to increase performance by replacing the Content Query Web Part with the Content Search Web Part in SharePoint Server 2013 and SharePoint Online.</span></span>
  
<span data-ttu-id="1e69d-105">sharepoint Server 2013 및 sharepoint Online의 가장 강력한 새 기능 중 하나는 콘텐츠 검색 웹 파트 (CSWP)입니다.</span><span class="sxs-lookup"><span data-stu-id="1e69d-105">One of the most powerful new features of SharePoint Server 2013 and SharePoint Online is the Content Search Web Part (CSWP).</span></span> <span data-ttu-id="1e69d-106">이 웹 파트는 검색 인덱스를 사용 하 여 사용자에 게 표시 되는 결과를 빠르게 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e69d-106">This Web Part uses the search index to quickly retrieve results which are shown to the user.</span></span> <span data-ttu-id="1e69d-107">페이지에서 cqwp (콘텐츠 쿼리 웹 파트) 대신 콘텐츠 검색 웹 파트를 사용 하 여 사용자의 성능을 향상 시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e69d-107">Use the Content Search Web Part instead of the Content Query Web Part (CQWP) in your pages to improve performance for your users.</span></span>
  
<span data-ttu-id="1e69d-108">콘텐츠 쿼리 웹 파트에서 콘텐츠 검색 웹 파트를 사용 하면 거의 대부분 SharePoint Online의 페이지 로드 성능이 크게 향상 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e69d-108">Using a Content Search Web Part over a Content Query Web Part will almost always result in significantly better page load performance on SharePoint Online.</span></span> <span data-ttu-id="1e69d-109">적절 한 쿼리를 가져오는 데에는 약간의 추가 구성이 있지만 성능 향상과 사용자에 대 한 만족도가 향상 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e69d-109">There is a little additional configuration to get the right query, but the rewards are improved performance and happier users.</span></span>
  
## <a name="comparing-the-performance-gain-you-get-from-using-content-search-web-part-instead-of-content-query-web-part"></a><span data-ttu-id="1e69d-110">콘텐츠 쿼리 웹 파트 대신 콘텐츠 검색 웹 파트를 사용 하 여 얻을 수 있는 성능 향상 비교</span><span class="sxs-lookup"><span data-stu-id="1e69d-110">Comparing the performance gain you get from using Content Search Web Part instead of Content Query Web Part</span></span>

<span data-ttu-id="1e69d-111">다음 예제에서는 콘텐츠 쿼리 웹 파트 대신 콘텐츠 검색 웹 파트를 사용할 때 얻을 수 있는 상대적인 성능 향상을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1e69d-111">The following examples show the relative performance gains you may receive when you use a Content Search Web Part instead of a Content Query Web Part.</span></span> <span data-ttu-id="1e69d-112">복잡 한 사이트 구조와 매우 광범위 한 콘텐츠 쿼리를 통해 더 확실 한 결과를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e69d-112">The effects are more obvious with a complex site structure and very broad content queries.</span></span>
  
<span data-ttu-id="1e69d-113">이 예제 사이트의 특징은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1e69d-113">This example site has the following characteristics:</span></span>
  
- <span data-ttu-id="1e69d-114">8 개 수준 하위 사이트</span><span class="sxs-lookup"><span data-stu-id="1e69d-114">8 levels of subsites.</span></span>
    
- <span data-ttu-id="1e69d-115">사용자 지정 "과일" 콘텐츠 형식을 사용 하는 목록</span><span class="sxs-lookup"><span data-stu-id="1e69d-115">Lists using a custom "fruit" content type.</span></span>
    
- <span data-ttu-id="1e69d-116">웹 파트에서 콘텐츠 쿼리는 광범위 하며 콘텐츠 형식이 "과일" 인 모든 항목을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e69d-116">In the Web Part, the content query is broad, returning all items with the content type of "fruit".</span></span>
    
- <span data-ttu-id="1e69d-117">이 예제에서는 8 개 사이트에서 50 항목만 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e69d-117">The example only uses 50 items across the 8 sites.</span></span> <span data-ttu-id="1e69d-118">콘텐츠가 더 많은 사이트의 경우에도 효과가 더 두드러지게 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="1e69d-118">The effects will be even more pronounced for sites with more content.</span></span>
    
<span data-ttu-id="1e69d-119">다음은 콘텐츠 쿼리 웹 파트의 결과에 대 한 스크린 샷입니다.</span><span class="sxs-lookup"><span data-stu-id="1e69d-119">Here is a screen shot of the results of the Content Query Web Part.</span></span>
  
![웹 파트에 대한 콘텐츠 쿼리를 보여 주는 그래픽](media/b3d41f20-dfe5-46ed-9c0a-31057e82de33.png)
  
<span data-ttu-id="1e69d-121">Internet Explorer에서 F12 개발자 도구의 **네트워크** 탭을 사용 하 여 응답 헤더에 대 한 세부 정보를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e69d-121">In Internet Explorer, use the **Network** tab of the F12 developer tools to look at the details for the response header.</span></span> <span data-ttu-id="1e69d-122">다음 스크린샷에서이 페이지 부하에 대 한 **sprequestduration** 값은 924 밀리초입니다.</span><span class="sxs-lookup"><span data-stu-id="1e69d-122">In the following screen shot, the value for the **SPRequestDuration** for this page load is 924 milliseconds.</span></span> 
  
![924의 요청 기간을 보여 주는 스크린샷](media/343571f2-a249-4de2-bc11-2cee93498aea.png)
  
 <span data-ttu-id="1e69d-124">**sprequestduration** 은 서버에서 페이지를 준비 하기 위해 수행 하는 작업의 양을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1e69d-124">**SPRequestDuration** indicates the amount of work that is done on the server to prepare the page.</span></span> <span data-ttu-id="1e69d-125">검색 웹 파트 별로 콘텐츠를 쿼리 웹 파트 별로 전환 하면 페이지를 렌더링 하는 데 걸리는 시간이 크게 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="1e69d-125">Switching Content by Query Web Parts with Content by Search Web Parts dramatically reduces the time it takes to render the page.</span></span> <span data-ttu-id="1e69d-126">이와 대조적으로 동일한 결과 수를 반환 하는 해당 콘텐츠 검색 웹 파트가 포함 된 페이지에는이 스크린샷에 표시 된 것 처럼 **sprequestduration** 값이 106 밀리초가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e69d-126">By contrast, a page with an equivalent Content Search Web Part, returning the same number of results has an **SPRequestDuration** value of 106 milliseconds as shown in this screen shot:</span></span> 
  
![106의 요청 기간을 보여 주는 스크린샷](media/b46387ac-660d-4e5e-a11c-cc430e912962.png)
  
## <a name="adding-a-content-search-web-part-in-sharepoint-online"></a><span data-ttu-id="1e69d-128">SharePoint Online에서 콘텐츠 검색 웹 파트 추가</span><span class="sxs-lookup"><span data-stu-id="1e69d-128">Adding a Content Search Web Part in SharePoint Online</span></span>

<span data-ttu-id="1e69d-129">콘텐츠 검색 웹 파트를 추가 하는 것은 일반 콘텐츠 쿼리 웹 파트와 매우 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="1e69d-129">Adding a Content Search Web Part is very similar to a regular Content Query Web Part.</span></span> <span data-ttu-id="1e69d-130">[Configure a content search web part in SharePoint의](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a) *"콘텐츠 검색 웹 파트 추가"* 섹션을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1e69d-130">See the section  *"Add a Content Search Web Part"*  in [Configure a Content Search Web Part in SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).</span></span>
  
## <a name="creating-the-right-search-query-for-your-content-search-web-part"></a><span data-ttu-id="1e69d-131">콘텐츠 검색 웹 파트에 대 한 올바른 검색 쿼리 만들기</span><span class="sxs-lookup"><span data-stu-id="1e69d-131">Creating the right search query for your Content Search Web Part</span></span>

<span data-ttu-id="1e69d-132">콘텐츠 검색 웹 파트를 추가한 후에는 검색을 구체화 하 고 원하는 항목을 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e69d-132">Once you have added a Content Search Web Part, you can refine the search and return the items you want.</span></span> <span data-ttu-id="1e69d-133">이 작업을 수행 하는 방법에 대 한 자세한 내용은 [Configure a content search web part in SharePoint의](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a) *"콘텐츠 검색 웹 파트에서 고급 쿼리를 구성 하 여 콘텐츠 표시"* 섹션을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="1e69d-133">For detailed instructions on how to do this, see the section,  *"Display content by configuring an advanced query in a Content Search Web Part"*  in [Configure a Content Search Web Part in SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).</span></span>
  
## <a name="query-building-and-testing-tool"></a><span data-ttu-id="1e69d-134">쿼리 작성 및 테스트 도구</span><span class="sxs-lookup"><span data-stu-id="1e69d-134">Query building and testing tool</span></span>

<span data-ttu-id="1e69d-135">복잡 한 쿼리를 작성 하 고 테스트 하기 위한 도구는 Codeplex에서 [검색 쿼리 도구](https://sp2013searchtool.codeplex.com/) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1e69d-135">For a tool to build and test complex queries, see the [Search Query Tool](https://sp2013searchtool.codeplex.com/) on Codeplex.</span></span> 
  

