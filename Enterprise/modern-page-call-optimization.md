---
title: SharePoint Online 최신 및 클래식 게시 사이트 페이지에서 페이지 호출 최적화
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 9/18/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
ms.reviewer: sstewart
search.appverid:
- MET150
description: SharePoint online 서비스 끝점 호출 횟수를 제한 하여 SharePoint Online에서 최신 및 클래식 게시 사이트 페이지를 최적화하는 방법에 대해 알아보세요.
ms.openlocfilehash: d44cb2273d550cea3a9ec7bfb1ffaeb10bbdd333
ms.sourcegitcommit: c7764503422922cb333b05d54e8ebbdb894df2f9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2019
ms.locfileid: "37028205"
---
# <a name="optimize-page-calls-in-sharepoint-online-modern-and-classic-publishing-site-pages"></a><span data-ttu-id="eae1f-103">SharePoint Online 최신 및 클래식 게시 사이트 페이지에서 페이지 호출 최적화</span><span class="sxs-lookup"><span data-stu-id="eae1f-103">Optimize page calls in SharePoint Online modern and classic publishing site pages</span></span>

<span data-ttu-id="eae1f-104">SharePoint Online의 최신 게시 사이트와 클래식 게시 사이트에는 SharePoint 기능과 CDNs에서 데이터를 로드 (또는 호출) 하는 링크가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eae1f-104">Both SharePoint Online modern and classic publishing sites contain links that load data from (or make calls to) SharePoint features and CDNs.</span></span> <span data-ttu-id="eae1f-105">페이지가 더 많은 호출을 할수록 페이지를 로딩 하는데 시간이 길어집니다.</span><span class="sxs-lookup"><span data-stu-id="eae1f-105">The more calls made by a page, the longer the page takes to load.</span></span> <span data-ttu-id="eae1f-106">이는 **최종 사용자에게 인식되는 시간** 또는 **EUPL**으로 알려졌습니다.</span><span class="sxs-lookup"><span data-stu-id="eae1f-106">This is known as **end user perceived latency** or **EUPL**.</span></span>

<span data-ttu-id="eae1f-107">이 문서는 모던 및 클래식 게시 사이트 페이지의 외부 끝점으로의 호출의 수와 영향을 확인하는 방법과 최종 사용자에게 인식되는 대기 시간에 미치는 영향을 제한하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="eae1f-107">This article will help you understand how to determine the number and impact of calls to external endpoints from your modern and classic publishing site pages and how to limit their effect on end user perceived latency.</span></span>

>[!NOTE]
><span data-ttu-id="eae1f-108">SharePoint Online 최신 포털의 성능에 대한 자세한 내용은 [최신 SharePoint 환경의 성능](https://docs.microsoft.com/ko-KR/sharepoint/modern-experience-performance)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="eae1f-108">For more information about performance in SharePoint Online modern portals, see [Performance in the modern SharePoint experience](https://docs.microsoft.com/ko-KR/sharepoint/modern-experience-performance).</span></span>

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-page-calls"></a><span data-ttu-id="eae1f-109">SharePoint 용 페이지 진단 도구를 사용한 페이지 호출 분석</span><span class="sxs-lookup"><span data-stu-id="eae1f-109">Use the Page Diagnostics for SharePoint tool to analyze page calls</span></span>

<span data-ttu-id="eae1f-110">**Sharepoint 페이지 진단 도구**는 Chrome 및 [ Microsoft Edge 버전 77 이상](https://www.microsoftedgeinsider.com/en-us/download?form=MI13E8&OCID=MI13E8)의 브라우저 확장으로서 Sharepoint 최신 및 클래식 게시 사이트 페이지를 분석하는데 사용할 수 있습니다. </span><span class="sxs-lookup"><span data-stu-id="eae1f-110">The **Page Diagnostics for SharePoint tool** is a browser extension for Chrome and [Microsoft Edge version 77 or later](https://www.microsoftedgeinsider.com/en-us/download?form=MI13E8&OCID=MI13E8) you can use to analyze SharePoint both modern and classic publishing site pages.</span></span> <span data-ttu-id="eae1f-111">이 도구는 정의된 성능 기준의 집합 대비 페이지 수행 방식을 보여주는 분석된 각 페이지에 대한 보고서를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="eae1f-111">The tool provides a report for each analyzed page showing how the page performs against a defined set of performance criteria.</span></span> <span data-ttu-id="eae1f-112">Sharepoint용 페이지 진단 도구에 대해 배우고 설치하려면[Sharepoint Online에 페이지 진단 도구 사용](page-diagnostics-for-spo.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="eae1f-112">To install and learn about the Page Diagnostics for SharePoint tool, visit [Use the Page Diagnostics tool for SharePoint Online](page-diagnostics-for-spo.md).</span></span>

<span data-ttu-id="eae1f-113">Sharepoint용 페이지 진단 도구를 사용하여 Sharepoint 사이트 페이지를 분석 시 Sharepoint로의 요청 결과에서 외부 호출에 대한 정보를  진단 테스트_ 창에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eae1f-113">When you analyze a SharePoint site page with the Page Diagnostics for SharePoint tool, you can see information about external calls in the **Requests to SharePoint** result in the _Diagnostic tests_ pane.</span></span> <span data-ttu-id="eae1f-114">사이트 페이지가 기준선 호출 수보다 적은 수를 포함하는 경우 선이 녹색으로 표시되고 페이지가 기준선 숫자를 초과하는 경우 빨간색으로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="eae1f-114">The line will appear in green if the site page contains fewer than the baseline number of calls, and red if the page exceeds the baseline number.</span></span> <span data-ttu-id="eae1f-115">클래식 페이지는 HTTP 1.1 그리고 최신 페이지는 HTTP 2.0을 사용하므로 최신 페이지와 클래식 페이지의 기준선 숫자는 다릅니다:</span><span class="sxs-lookup"><span data-stu-id="eae1f-115">The baseline number is different for modern and classic pages because classic site pages use HTTP1.1 and modern pages use HTTP2.0:</span></span>

- <span data-ttu-id="eae1f-116">최신 사이트 페이지는 **25**개 이하의 호출을 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eae1f-116">Modern site pages should contain no more than **25** calls</span></span>
- <span data-ttu-id="eae1f-117">클래식 게시 페이지는 **6**개 이하의 호출을 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eae1f-117">Classic publishing pages should contain no more than **6** calls</span></span>

<span data-ttu-id="eae1f-118">잠정 결과는 다음과 같습니다:</span><span class="sxs-lookup"><span data-stu-id="eae1f-118">Possible results include:</span></span>

- <span data-ttu-id="eae1f-119">**주의 필요** (빨간색): 페이지가 기준선 호출 수를 초과합니다.</span><span class="sxs-lookup"><span data-stu-id="eae1f-119">**Attention required** (red): The page exceeds the baseline number of calls</span></span>
- <span data-ttu-id="eae1f-120">**조치가 필요하지 않음** (녹색):이 페이지는 기준선 호출 수보다 적은 수의 호출을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="eae1f-120">**No action required** (green): The page contains fewer than the baseline number of calls</span></span>

<span data-ttu-id="eae1f-121">**SharePoint에 대한 요청**결과가 **주의를 요함** 섹션에 표시되는 경우 해당 결과를 클릭하 여 페이지의 총 호출 수와 URL 목록을 포함한 세부 정보를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eae1f-121">If the **Requests to SharePoint** result appears in the **Attention required** section, you can click the result for details, including the total number of calls on the page and a list of the URLs.</span></span>

![SharePoint 결과에 대한 요청](media/modern-portal-optimization/pagediag-requests.png)

## <a name="remediate-performance-issues-related-to-too-many-calls-on-a-page"></a><span data-ttu-id="eae1f-123">페이지에서 너무 많은 호출과 관련된 성능 문제 해결</span><span class="sxs-lookup"><span data-stu-id="eae1f-123">Remediate performance issues related to too many calls on a page</span></span>

<span data-ttu-id="eae1f-124">페이지에 너무 많은 호출이 포함되어 있는 경우 **Sharepoint에 대한 요청** 결과에 있는 URL 목록을 사용하여 반복적으로 되는 호출, 일괄 처리 해야 하는 호출 또는 캐시되어야 하는 데이터를 반환 하는 호출이 있는지 여부를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eae1f-124">If a page contains too many calls, you can use the list of URLs in the **Requests to Sharepoint** results to determine whether there are any repeated calls, calls that should be batched, or calls that return data that should be cached.</span></span>

<span data-ttu-id="eae1f-125">**휴지 (REST) 호출을 일괄 처리** 하면 성능이 저하되는 것을 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eae1f-125">**Batching REST calls** can help to reduce performance overhead.</span></span> <span data-ttu-id="eae1f-126">API 호출 일괄 처리에 대한 자세한 내용은 [REST API를 사용하여 일괄 요청 만들기](https://docs.microsoft.com/ko-KR/sharepoint/dev/sp-add-ins/make-batch-requests-with-the-rest-apis)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="eae1f-126">For more information about API call batching, see [Make batch requests with the REST APIs](https://docs.microsoft.com/ko-KR/sharepoint/dev/sp-add-ins/make-batch-requests-with-the-rest-apis).</span></span>

<span data-ttu-id="eae1f-127">**캐시를 사용**하여 API 호출 결과를 저장하면 이후의 각 페이지 부하에 대한 추가 호출을 하는 대신 클라이언트에서 캐시된 데이터를 사용할 수 있어 웜 요청의 성능이 향상될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eae1f-127">**Using a cache** to store the results of an API call can improve the performance of a warm request by allowing the client to use the cached data instead of making an additional call for each subsequent page load.</span></span> <span data-ttu-id="eae1f-128">비즈니스 요구 사항에 따라 이 솔루션에 접근하는 방법에는 여러 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eae1f-128">There are multiple ways to approach this solution depending on the business requirement.</span></span> <span data-ttu-id="eae1f-129">일반적으로 데이터가 모든 사용자에게 동일한 경우, 사용자가 데이터를 SPO에서 직접 요청하지 않고 캐싱 서비스에서 요청하므로 Azure Redis cache](https://azure.microsoft.com/ko-KR/services/cache/)와 같은 중간 계층 캐싱 서비스를 사용하면 API 트래픽을 크게 줄일 수 있습니다. </span><span class="sxs-lookup"><span data-stu-id="eae1f-129">Typically if the data will be the same for all users, using a middle-tier caching service like [_Azure Redis_ cache](https://azure.microsoft.com/ko-KR/services/cache/) is a great option to significantly reduce API traffic against a site, as the users would request the data from the caching service instead of directly from SPO.</span></span> <span data-ttu-id="eae1f-130">필요한 유일한 SPO 호출은 중간 계층의 캐시를 새로 고치는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="eae1f-130">The only SPO calls needed would be to refresh the middle-tier's cache.</span></span> <span data-ttu-id="eae1f-131">개별 사용자를 기준으로 데이터가 변하는 경우에는 LocalStorage 혹은 심지어 쿠키와 같은 클라이언트 쪽 캐시를 구현하는 것이 좋을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eae1f-131">If the data will fluctuate on an individual user basis, it may be best to implement a client side cache, like LocalStorage or even a Cookie.</span></span> <span data-ttu-id="eae1f-132">이 경우 같은 사용자가 캐시 기간 동안에 수행한 이후의 요청을 제거하여 호출을 줄일 수 있지만 전용 캐싱 서비스 보다는 효율성이 떨어집니다.</span><span class="sxs-lookup"><span data-stu-id="eae1f-132">This will still reduce call volumes by eliminating subsequent requests made by the same user for the cache duration, but will be less efficient than a dedicated caching service.</span></span> <span data-ttu-id="eae1f-133">PnP는 약간의 추가 개발만을 필요로 하고 LocalStorage를 사용할 수 있게 해줍니다.</span><span class="sxs-lookup"><span data-stu-id="eae1f-133">PnP allows you to use LocalStorage with little additional development required.</span></span>

<span data-ttu-id="eae1f-134">성능 문제를 해결하기 위해 페이지 수정을 수행 하기 전에 분석 결과에 페이지 로드 시간을 기록해 둡니다.</span><span class="sxs-lookup"><span data-stu-id="eae1f-134">Before you make page revisions to remediate performance issues, make a note of the page load time in the analysis results.</span></span> <span data-ttu-id="eae1f-135">수정 후에 다시 도구를 실행하여 새 결과가 기준선 표준에 포함되는지 확인하고 새 페이지 로드 시간을 확인하여 개선이 되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="eae1f-135">Run the tool again after your revision to see if the new result is within the baseline standard, and check the new page load time to see if there was an improvement.</span></span>

![페이지 로드 시간 결과](media/modern-portal-optimization/pagediag-page-load-time.png)

>[!NOTE]
><span data-ttu-id="eae1f-137">페이지 로드 시간은 네트워크 부하, 하루 중 시간 및 기타 일시적인 조건과 같은 다양한 요인에 따라 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eae1f-137">Page load time can vary based on a variety of factors such as network load, time of day, and other transient conditions.</span></span> <span data-ttu-id="eae1f-138">결과의 평균을 내는데 도움이 되도록 수정을 하기 전과 후에 페이지 로드 시간을 몇 번 정도 테스트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eae1f-138">You should test page load time a few times before and after making changes to help you average the results.</span></span>

## <a name="related-topics"></a><span data-ttu-id="eae1f-139">관련 주제</span><span class="sxs-lookup"><span data-stu-id="eae1f-139">Related topics</span></span>

[<span data-ttu-id="eae1f-140">SharePoint Online 성능 조정</span><span class="sxs-lookup"><span data-stu-id="eae1f-140">Tune SharePoint Online performance</span></span>](tune-sharepoint-online-performance.md)

[<span data-ttu-id="eae1f-141">Office 365 성능 조정</span><span class="sxs-lookup"><span data-stu-id="eae1f-141">Tune Office 365 performance</span></span>](tune-office-365-performance.md)

[<span data-ttu-id="eae1f-142">최신 SharePoint 환경의 성능</span><span class="sxs-lookup"><span data-stu-id="eae1f-142">Performance in the modern SharePoint experience</span></span>](https://docs.microsoft.com/ko-KR/sharepoint/modern-experience-performance.md)

[<span data-ttu-id="eae1f-143">콘텐츠 전달 네트워크</span><span class="sxs-lookup"><span data-stu-id="eae1f-143">Content delivery networks</span></span>](content-delivery-networks.md)

[<span data-ttu-id="eae1f-144">sharepoint Online을 활용해 Office 365 콘텐츠 배달 네트워크(CDN) 사용하기</span><span class="sxs-lookup"><span data-stu-id="eae1f-144">Use the Office 365 Content Delivery Network (CDN) with SharePoint Online</span></span>](use-office-365-cdn-with-spo.md)
