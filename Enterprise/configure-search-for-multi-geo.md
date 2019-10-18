---
title: Office 365 Multi-Geo 검색 구성
ms.author: tlarsen
author: tklarsen
manager: arnek
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: 다중 위치 환경에서 검색을 구성하는 방법을 알아봅니다.
ms.openlocfilehash: 39493c4df48af239306d8b22de451d6db6e3bcf9
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068074"
---
# <a name="configure-search-for-office-365-multi-geo"></a><span data-ttu-id="fab54-103">Office 365 Multi-Geo 검색 구성</span><span class="sxs-lookup"><span data-stu-id="fab54-103">Configure Search for Office 365 Multi-Geo</span></span>

<span data-ttu-id="fab54-104">다중 지역 환경에서 각 지리적 위치에는 자체 검색 인덱스와 검색 센터가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fab54-104">In a multi-geo environment, each geo location has its own search index and Search Center.</span></span> <span data-ttu-id="fab54-105">사용자가 검색을 하면 쿼리가 모드 인덱스로 팬아웃되고 반환된 결과는 병합됩니다.</span><span class="sxs-lookup"><span data-stu-id="fab54-105">When a user searches, the query is fanned out to all the indexes, and the returned results are merged.</span></span>

<span data-ttu-id="fab54-106">예를 들어, 한 지리적 위치에 있는 사용자가 다른 지리적 위치에 저장된 콘텐츠를 검색하거나, 다른 지리적 위치로 제한된 SharePoint 사이트에서 콘텐츠를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fab54-106">For example, a user in one geo location can search for content stored in another geo location, or for content on a SharePoint site that's restricted to a different geo location.</span></span> <span data-ttu-id="fab54-107">사용자가 이 콘텐츠에 액세스할 수 있으면 검색 결과가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="fab54-107">If the user has access to this content, search will show the result.</span></span>

## <a name="which-search-clients-work-in-a-multi-geo-environment"></a><span data-ttu-id="fab54-108">Multi-Geo 환경에서는 어떤 검색 클라이언트가 사용되나요?</span><span class="sxs-lookup"><span data-stu-id="fab54-108">Which search clients work in a multi-geo environment?</span></span>

<span data-ttu-id="fab54-109">이러한 클라이언트는 모든 지리적 위치의 결과를 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fab54-109">These clients can return results from all geo locations:</span></span>

-   <span data-ttu-id="fab54-110">비즈니스용 OneDrive</span><span class="sxs-lookup"><span data-stu-id="fab54-110">OneDrive for Business</span></span>

-   <span data-ttu-id="fab54-111">Delve</span><span class="sxs-lookup"><span data-stu-id="fab54-111">Delve</span></span>

-   <span data-ttu-id="fab54-112">SharePoint 홈페이지</span><span class="sxs-lookup"><span data-stu-id="fab54-112">The SharePoint home page</span></span>

-   <span data-ttu-id="fab54-113">검색 센터</span><span class="sxs-lookup"><span data-stu-id="fab54-113">The Search Center</span></span>

-   <span data-ttu-id="fab54-114">SharePoint 검색 API를 사용하는 사용자 지정 검색 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="fab54-114">Custom search applications that use the SharePoint Search API</span></span>

### <a name="onedrive-for-business"></a><span data-ttu-id="fab54-115">비즈니스용 OneDrive</span><span class="sxs-lookup"><span data-stu-id="fab54-115">OneDrive for Business</span></span>

<span data-ttu-id="fab54-116">Multi-Geo 환경이 설정되는 즉시, OneDrive에서 검색하는 사용자는 모든 지리적 위치에서 결과를 얻습니다.</span><span class="sxs-lookup"><span data-stu-id="fab54-116">As soon as the multi-geo environment has been set up, users that search in OneDrive get results from all geo locations.</span></span>

### <a name="delve"></a><span data-ttu-id="fab54-117">Delve</span><span class="sxs-lookup"><span data-stu-id="fab54-117">Delve</span></span>

<span data-ttu-id="fab54-118">Multi-Geo 환경이 설정되는 즉시, Delve에서 검색하는 사용자는 모든 지리적 위치에서 결과를 얻습니다.</span><span class="sxs-lookup"><span data-stu-id="fab54-118">As soon as the multi-geo environment has been set up, users that search in Delve get results from all geo locations.</span></span>

<span data-ttu-id="fab54-119">Delve 피드 및 프로필 카드는 중앙 위치에 저장된 파일의 미리보기만 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="fab54-119">The Delve feed and the profile card only show previews of files that are stored in the central location.</span></span> <span data-ttu-id="fab54-120">위성 위치에 저장된 파일의 경우 파일 유형 아이콘이 대신 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="fab54-120">For files that are stored in satellite locations, the icon for the file type is shown instead.</span></span>

### <a name="the-sharepoint-home-page"></a><span data-ttu-id="fab54-121">SharePoint 홈페이지</span><span class="sxs-lookup"><span data-stu-id="fab54-121">The SharePoint home page</span></span>

<span data-ttu-id="fab54-p104">Multi-Geo 환경이 설정되는 즉시, 사용자는 SharePoint 홈페이지에서 다중 지리적 위치의 뉴스, 최근 사이트 및 팔로우된 사이트를 볼 수 있습니다. SharePoint 홈페이지의 검색 상자를 사용하는 경우 다중 지리적 위치에서 병합된 결과를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fab54-p104">As soon as the multi-geo environment has been set up, users will see news, recent and followed sites from multiple geo locations on their SharePoint home page. If they use the search box on the SharePoint home page, they'll get merged results from multiple geo locations.</span></span>

### <a name="the-search-center"></a><span data-ttu-id="fab54-124">검색 센터</span><span class="sxs-lookup"><span data-stu-id="fab54-124">The Search Center</span></span>

<span data-ttu-id="fab54-p105">Multi-Geo 환경이 설정된 후에 각 검색 센터는 자체 지리적 위치의 결과만 계속 표시합니다. 관리자는 모든 지리적 위치에서 결과를 가져오려면 [각 검색 센터의 설정을 변경](#_Set_up_a_1)해야 합니다. 그런 후에 검색 센터에서 검색을 하는 사용자는 모든 지리적 위치에서 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="fab54-p105">After the multi-geo environment has been set up, each Search Center continues to only show results from their own geo location. Admins must [change the settings of each Search Center](#_Set_up_a_1) to get results from all geo locations. Afterwards, users that search in the Search Center get results from all geo locations.</span></span>

### <a name="custom-search-applications"></a><span data-ttu-id="fab54-128">사용자 지정 검색 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="fab54-128">Custom search applications</span></span>

<span data-ttu-id="fab54-p106">일반적인 경우처럼, 사용자 지정 검색 응용 프로그램은 기존 SharePoint 검색 REST API를 사용하여 검색 인덱스와 상호 작용합니다. 모든 또는 일부 지리적 위치에서 결과를 얻으려면 응용 프로그램은 [API를 호출하고 요청에 새 Multi-Geo 쿼리 매개 변수를 포함](#_Get_custom_search)해야 합니다. 이렇게 하면 모든 지리적 위치로의 쿼리 팬아웃이 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="fab54-p106">As usual, custom search applications interact with the search indexes by using the existing SharePoint Search REST APIs. To get results from all, or some geo locations, the application must [call the API and include the new Multi-Geo query parameters](#_Get_custom_search) in the request. This triggers a fan out of the query to all geo locations.</span></span>

## <a name="whats-different-about-search-in-a-multi-geo-environment"></a><span data-ttu-id="fab54-132">Multi-Geo 환경에서 검색의 차이점은 무엇인가요?</span><span class="sxs-lookup"><span data-stu-id="fab54-132">What's different about search in a multi-geo environment?</span></span>

<span data-ttu-id="fab54-133">이미 익숙할 수 있는 일부 검색 기능이 Multi-Geo 환경에서는 다르게 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="fab54-133">Some search features you might be familiar with, work differently in a multi-geo environment.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="fab54-134"><strong>기능</strong></span><span class="sxs-lookup"><span data-stu-id="fab54-134"><strong>Feature</strong></span></span></th>
<th align="left"><span data-ttu-id="fab54-135"><strong>작동 방법</strong></span><span class="sxs-lookup"><span data-stu-id="fab54-135"><strong>How it works</strong></span></span></th>
<th align="left"><span data-ttu-id="fab54-136"><strong>해결 방법</strong></span><span class="sxs-lookup"><span data-stu-id="fab54-136"><strong>Workaround</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="fab54-137">승격된 결과</span><span class="sxs-lookup"><span data-stu-id="fab54-137">Promoted results</span></span></td>
<td align="left"><span data-ttu-id="fab54-138">전체 수준의 테넌트, 사이트 모음 또는 사이트에 대해 승격된 결과가 포함 된 쿼리 규칙을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fab54-138">You can create query rules with promoted results at different levels: for the whole tenant, for a site collection, or for a site.</span></span> <span data-ttu-id="fab54-139">Multi-Geo 환경에서 테넌트 수준의 승격된 결과를 정의하여 모든 지역의 검색 센터로 결과를 승격하십시오.</span><span class="sxs-lookup"><span data-stu-id="fab54-139">In a multi-geo environment, define promoted results at the tenant level to promote the results to the Search Centers in all geo locations.</span></span> <span data-ttu-id="fab54-140">사이트 모음 또는 사이트의 위치에 있는 검색 센터에서만 결과를 승격하려면 사이트 모음 또는 사이트 수준에서 승격된 결과를 정의하십시오.</span><span class="sxs-lookup"><span data-stu-id="fab54-140">If you only want to promote results in the Search Center that's in the geo location of the site collection or site, define the promoted results at the site collection or site level.</span></span> <span data-ttu-id="fab54-141">이 결과는 다른 지리적 위치에서 승격되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fab54-141">These results are not promoted in other geo locations.</span></span></td>
<td align="left"><span data-ttu-id="fab54-142">지리적 위치별로 승격된 다른 결과가 필요하지 않을 경우(예: 여행에 대해 다른 규칙 지정) 테넌트 수준에서 승격된 결과를 정의하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="fab54-142">If you don't need different promoted results per geo location, for example different rules for traveling, we recommend defining promoted results at the tenant level.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="fab54-143">검색 구체화</span><span class="sxs-lookup"><span data-stu-id="fab54-143">Search refiners</span></span></td>
<td align="left"><span data-ttu-id="fab54-p108">검색은 테넌트의 모든 지리적 위치에서 구체화 결과를 반환한 후 집계합니다. 이러한 집계에는 가능한 최선의 노력이 수반되며, 구체화 개수가 100% 정확하지 않을 수도 있습니다. 대부분의 검색 기반 시나리오에서는 이 정도의 정확도로 충분합니다. </span><span class="sxs-lookup"><span data-stu-id="fab54-p108">Search returns refiners from all the geo locations of a tenant and then aggregates them. The aggregation is a best effort, meaning that the refiner counts might not be 100% accurate. For most search-driven scenarios, this accuracy is sufficient. </span></span></td>
<td align="left"><span data-ttu-id="fab54-147">구체화 완성도에 의존하는 검색 기반 응용 프로그램의 경우 개별적으로 각 지리적 위치를 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="fab54-147">For search-driven applications that depend on refiner completeness, query each geo location independently.</span></span></td>
</tr>
<tr class="odd">
<td align="left"></td>
<td align="left"><span data-ttu-id="fab54-148">Multi-Geo 검색은 수치 구체화에 대한 동적 버킷팅을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fab54-148">Multi-geo search doesn't support dynamic bucketing for numerical refiners.</span></span></td>
<td align="left"><span data-ttu-id="fab54-149">숫자 구체화에 대해 <a href="https://docs.microsoft.com/en-us/sharepoint/dev/general-development/query-refinement-in-sharepoint">"Discretize" 매개 변수</a>를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="fab54-149">Use the <a href="https://docs.microsoft.com/en-us/sharepoint/dev/general-development/query-refinement-in-sharepoint">“Discretize” parameter</a> for numerical refiners.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="fab54-150">문서 ID</span><span class="sxs-lookup"><span data-stu-id="fab54-150">Document IDs</span></span></td>
<td align="left"><span data-ttu-id="fab54-151">문서 ID에 의존하는 검색 기반 응용 프로그램을 개발하는 경우 Multi-Geo 환경의 문서 ID가 지리적 위치 간에 고유하지 않으며 지리적 위치별로 고유합니다.</span><span class="sxs-lookup"><span data-stu-id="fab54-151">If you're developing a search-driven application that depends on document IDs, note that document IDs in a multi-geo environment aren't unique across geo locations, they are unique per geo location.</span></span></td>
<td align="left"><span data-ttu-id="fab54-152">위치 정보를 식별 할 수 있는 열을 추가했습니다.</span><span class="sxs-lookup"><span data-stu-id="fab54-152">We've added a column that identifies the geo location.</span></span> <span data-ttu-id="fab54-153">고유성을 얻으려면 이 열을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="fab54-153">Use this column to achieve uniqueness.</span></span> <span data-ttu-id="fab54-154">이 열은 "GeoLocationSource"라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="fab54-154">This column is named “GeoLocationSource”.</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="fab54-155">결과의 수</span><span class="sxs-lookup"><span data-stu-id="fab54-155">Number of results</span></span></td>
<td align="left"><span data-ttu-id="fab54-156">검색 결과 페이지에는 지리적 위치의 결합된 결과가 표시되지만 500개가 넘는 결과는 여러 페이지로 표시할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fab54-156">The search results page shows combined results from the geo locations, but it's not possible to page beyond 500 results.</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="fab54-157">Hybrid search</span><span class="sxs-lookup"><span data-stu-id="fab54-157">Hybrid search</span></span></td>
<td align="left"><span data-ttu-id="fab54-158"><a href="https://docs.microsoft.com/sharepoint/hybrid/learn-about-cloud-hybrid-search-for-sharepoint">클라우드 하이브리드 검색</a>이 있는 하이브리드 SharePoint 환경에서는 온-프레미스 콘텐츠가 중앙 위치의 Office 365 인덱스에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="fab54-158">In a hybrid SharePoint environment with <a href="https://docs.microsoft.com/sharepoint/hybrid/learn-about-cloud-hybrid-search-for-sharepoint">cloud hybrid search</a>,  on-premises content is added to the Office 365 index of the central location.</span></span></td>
<td align="left"></td>
</tr>
</tbody>
</table>

## <a name="whats-not-supported-for-search-in-a-multi-geo-environment"></a><span data-ttu-id="fab54-159">Multi-Geo 환경에서 지원되지 않는 검색은 어떤 것인가요?</span><span class="sxs-lookup"><span data-stu-id="fab54-159">What's not supported for search in a multi-geo environment?</span></span>

<span data-ttu-id="fab54-160">기존에 친숙하던 일부 검색 기능이 Multi-Geo 환경에서 지원되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fab54-160">Some of the search features you might be familiar with, aren't supported in a multi-geo environment.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="fab54-161"><strong>검색 기능</strong></span><span class="sxs-lookup"><span data-stu-id="fab54-161"><strong>Search feature</strong></span></span></th>
<th align="left"><span data-ttu-id="fab54-162"><strong>참고</strong></span><span class="sxs-lookup"><span data-stu-id="fab54-162"><strong>Note</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="fab54-163">앱 전용 인증</span><span class="sxs-lookup"><span data-stu-id="fab54-163">App-only authentication</span></span></td>
<td align="left"><span data-ttu-id="fab54-164">앱 전용 인증(서비스의 권한 있는 액세스)은 Multi-Geo 검색에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fab54-164">App-only authentication (privileged access from services) isn't supported in multi-geo search.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="fab54-165">게스트 사용자</span><span class="sxs-lookup"><span data-stu-id="fab54-165">Guest users</span></span></td>
<td align="left"><span data-ttu-id="fab54-166">게스트 사용자는 검색하는 지리적 위치에서만 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="fab54-166">Guest users only get results from the geo location that they're searching from.</span></span></td>
</tr>
</tbody>
</table>

## <a name="how-does-search-work-in-a-multi-geo-environment"></a><span data-ttu-id="fab54-167">Multi-Geo 환경에서 검색은 어떤 방식으로 작동하나요?</span><span class="sxs-lookup"><span data-stu-id="fab54-167">How does search work in a multi-geo environment?</span></span>

<span data-ttu-id="fab54-168">모든 검색 클라이언트는 기존 SharePoint 검색 REST API를 사용하여 검색 인덱스와 상호 작용합니다.</span><span class="sxs-lookup"><span data-stu-id="fab54-168">All the search clients use the existing SharePoint Search REST APIs to interact with the search indexes.</span></span>

<img src="media/configure-search-for-multi-geo-image1-1.png" />

1. <span data-ttu-id="fab54-169">검색 클라이언트는 쿼리 속성 EnableMultiGeoSearch가 true인 검색 REST 끝점을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="fab54-169">A search client calls the Search REST endpoint with the query property EnableMultiGeoSearch= true.</span></span>
2. <span data-ttu-id="fab54-170">쿼리는 테넌트의 모든 지리적 위치로 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="fab54-170">The query is sent to all geo locations in the tenant.</span></span>
3. <span data-ttu-id="fab54-171">각 지리적 위치의 검색 결과가 병합되고 순위가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="fab54-171">Search results from each geo location are merged and ranked.</span></span>
4. <span data-ttu-id="fab54-172">클라이언트는 통합된 검색 결과를 얻습니다.</span><span class="sxs-lookup"><span data-stu-id="fab54-172">The client gets unified search results.</span></span>



<span data-ttu-id="fab54-173"><span id="_Set_up_a" class="anchor"><span id="_Ref501388384" class="anchor"></span></span>Microsoft는 모든 지리적 위치에서 결과를 얻을 때까지 검색 결과를 병합하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fab54-173"><span id="_Set_up_a" class="anchor"><span id="_Ref501388384" class="anchor"></span></span>Notice that we don't merge the search results until we've received results from all the geo locations.</span></span> <span data-ttu-id="fab54-174">즉, Multi-Geo 정보 검색은 지리적 위치가 하나뿐인 환경에서의 검색보다 대기 시간이 길어집니다.</span><span class="sxs-lookup"><span data-stu-id="fab54-174">This means that multi-geo searches have additional latency compared to searches in an environment with only one geo location.</span></span>

<span id="_Set_up_a_1" class="anchor"><span id="_Ref505252370" class="anchor"></span></span>
## <a name="get-a-search-center-to-show-results-from-all-geo-locations"></a><span data-ttu-id="fab54-175">검색 센터에서 모든 지리적 위치의 결과를 표시하도록 지정</span><span class="sxs-lookup"><span data-stu-id="fab54-175">Get a Search Center to show results from all geo locations</span></span>

<span data-ttu-id="fab54-176">각 검색 센터에는 여러 범주가 있으며 각 범주를 개별적으로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fab54-176">Each Search Center has several verticals and you have to set up each vertical individually.</span></span>

1.  <span data-ttu-id="fab54-177">검색 결과 페이지 및 검색 결과 웹 파트를 편집할 수 있는 권한이 있는 계정으로 다음 단계를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fab54-177">Ensure that you perform these steps with an account that has permission to edit the search results page and the Search Result Web Part.</span></span>

2.  <span data-ttu-id="fab54-178">검색 결과 페이지로 이동합니다(검색 결과 페이지의 [목록](https://support.office.com/article/174d36e0-2f85-461a-ad9a-8b3f434a4213) 참조).</span><span class="sxs-lookup"><span data-stu-id="fab54-178">Navigate to the search results page (see the [list](https://support.office.com/article/174d36e0-2f85-461a-ad9a-8b3f434a4213) of search results pages)</span></span>

3.  <span data-ttu-id="fab54-p111">설정할 범주를 선택하고 오른쪽 위 모서리에 있는 **설정** 톱니바퀴 아이콘을 클릭한 후 **페이지 편집**을 클릭합니다. 검색 결과 페이지가 편집 모드에서 열립니다.</span><span class="sxs-lookup"><span data-stu-id="fab54-p111">Select the vertical to set up, click **Settings** gear icon in the upper, right corner, and then click **Edit Page**. The search results page opens in Edit mode.</span></span>

     ![](media/configure-search-for-multi-geo-image2.png)
1.  <span data-ttu-id="fab54-181">검색 결과 웹 파트에서 웹 파트 오른쪽 위 모서리로 포인터를 이동하고 화살표를 클릭한 후 메뉴에서 **웹 파트 편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fab54-181">In the Search Results Web Part, move the pointer to the upper, right corner of the web part, click the arrow, and then click **Edit Web Part** on the menu.</span></span> <span data-ttu-id="fab54-182">검색 결과 웹 파트 도구 창은 페이지 오른쪽 위에 있는 리본 아래에 열립니다.</span><span class="sxs-lookup"><span data-stu-id="fab54-182">The Search Results Web Part tool pane opens under the ribbon in the top right of the page.</span></span> ![](media/configure-search-for-multi-geo-image3.png)

1.  <span data-ttu-id="fab54-183">웹 파트 도구 창의 **설정** 섹션에 있는 **결과 제어 설정**에서 **Multi-Geo 결과 표시**를 선택하여 검색 결과 웹 파트에 모든 지리적 위치의 결과를 표시하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="fab54-183">In the Web Part tool pane, in the **Settings** section, under **Results control settings**, select **Show Multi-Geo results** to get the Search Results Web Part to show results from all geo locations.</span></span>

2.  <span data-ttu-id="fab54-184">**확인**을 클릭하여 변경 내용을 저장하고 웹 파트 도구 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="fab54-184">Click **OK** to save your change and close the Web Part tool pane.</span></span>

3.  <span data-ttu-id="fab54-185">주 메뉴의 페이지 탭에서 **체크 인**을 클릭하여 검색 결과 웹 파트에 대한 변경 내용을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="fab54-185">Check your changes to the Search Results Web Part by clicking **Check-In** on the Page tab of the main menu.</span></span>

4.  <span data-ttu-id="fab54-186">페이지 위쪽의 메모에 제공된 링크를 사용하여 변경 내용을 게시합니다.</span><span class="sxs-lookup"><span data-stu-id="fab54-186">Publish the changes by using the link provided in the note at the top of the page.</span></span>

<span id="_Get_custom_search" class="anchor"><span id="_Ref501388387" class="anchor"></span></span>
## <a name="get-custom-search-applications-to-show-results-from-all-or-some-geo-locations"></a><span data-ttu-id="fab54-187">사용자 지정 검색 응용 프로그램에서 전체 또는 일부 지리적 위치의 결과를 표시하도록 지정</span><span class="sxs-lookup"><span data-stu-id="fab54-187">Get custom search applications to show results from all or some geo locations</span></span>

<span data-ttu-id="fab54-p113">사용자 지정 검색 응용 프로그램은 SharePoint 검색 REST API에 대한 요청을 통해 쿼리 매개 변수를 지정하여 전체 또는 일부 지리적 위치에서 결과를 가져옵니다. 쿼리 매개 변수에 따라, 쿼리는 모든 지리적 위치 또는 일부 지리적 위치로 팬아웃됩니다. 예를 들어, 관련 정보를 찾기 위해 지리적 위치의 하위 집합만 쿼리하면 될 경우 팬아웃을 이러한 위치로만 제어할 수 있습니다. 요청이 성공하면 SharePoint 검색 REST API가 응답 데이터를 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="fab54-p113">Custom search applications get results from all, or some, geo locations by specifying query parameters with the request to the SharePoint Search REST API. Depending on the query parameters, the query is fanned out to all geo locations, or to some geo locations. For example, if you only need to query a subset of geo locations to find relevant information, you can control the fan out to only these. If the request succeeds, the SharePoint Search REST API returns response data.</span></span>

<span data-ttu-id="fab54-192">**요구 사항**</span><span class="sxs-lookup"><span data-stu-id="fab54-192">**Requirement**</span></span>

<span data-ttu-id="fab54-p114">각 지역 위치의 경우 조직의 모든 사용자가 루트 웹 사이트(예: contoso**APAC**.sharepoint.com/ 및 contoso**EU**.sharepoint.com/) **읽기** 권한 수준을 받아야 합니다. [권한에 대해 자세히 알아보세요](https://support.office.com/en-us/article/understanding-permission-levels-in-sharepoint-87ecbb0e-6550-491a-8826-c075e4859848).</span><span class="sxs-lookup"><span data-stu-id="fab54-p114">For each geo location, you must ensure that all users in the organization have been granted the **Read** permission level for the root website (for example contoso**APAC**.sharepoint.com/ and contoso**EU**.sharepoint.com/). [Learn about permissions](https://support.office.com/en-us/article/understanding-permission-levels-in-sharepoint-87ecbb0e-6550-491a-8826-c075e4859848).</span></span>

### <a name="query-parameters"></a><span data-ttu-id="fab54-195">쿼리 매개 변수</span><span class="sxs-lookup"><span data-stu-id="fab54-195">Query parameters</span></span>

<span data-ttu-id="fab54-196">EnableMultiGeoSearch - 이 쿼리는 Multi-Geo 테넌트의 다른 지리적 위치의 인덱스로 쿼리를 팬아웃할지 여부를 지정하는 부울 값입니다.</span><span class="sxs-lookup"><span data-stu-id="fab54-196">EnableMultiGeoSearch - This is a Boolean value that specifies whether the query shall be fanned out to the indexes of other geo locations of the multi-geo tenant.</span></span> <span data-ttu-id="fab54-197">**true**로 설정하면 쿼리가 적용됩니다. **false**로 설정하면 쿼리가 팬 아웃되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fab54-197">Set it to **true** to fan out the query; **false** to not fan out the query.</span></span> <span data-ttu-id="fab54-198">기본값은 **false**입니다.</span><span class="sxs-lookup"><span data-stu-id="fab54-198">The default value is **false**.</span></span> <span data-ttu-id="fab54-199">이 매개 변수를 포함하지 않으면 쿼리가 다른 지리적 위치로 이동되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fab54-199">If you don't include this parameter, the query is not fanned out to other geo locations.</span></span> <span data-ttu-id="fab54-200">Multi-Geo가 아닌 환경에서 매개 변수를 사용하면 매개 변수가 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="fab54-200">If you use the parameter in an environment that isn't multi-geo, the parameter is ignored.</span></span>

<span data-ttu-id="fab54-201">ClientType - 이것은 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="fab54-201">ClientType - This is a string.</span></span> <span data-ttu-id="fab54-202">각 검색 응용 프로그램에 대해 고유한 클라이언트 이름을 입력하십시오.</span><span class="sxs-lookup"><span data-stu-id="fab54-202">Enter a unique client name for each search application.</span></span> <span data-ttu-id="fab54-203">이 매개 변수를 포함하지 않으면 쿼리가 다른 지리적 위치로 이동되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fab54-203">If you don't include this parameter, the query is not fanned out to other geo locations.</span></span>

<span data-ttu-id="fab54-204">MultiGeoSearchConfiguration -\*\*EnableMultiGeoSearch \*\*가 **true**일 때 쿼리를 내보내는 Multi-Geo 테넌트의 지리적 위치에 대한 선택적 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="fab54-204">MultiGeoSearchConfiguration - This is an optional list of which geo locations in the multi-geo tenant to fan the query out to when **EnableMultiGeoSearch** is **true**.</span></span> <span data-ttu-id="fab54-205">이 매개 변수를 포함하지 않거나 공백으로 두면 모든 지리적 위치로 쿼리가 이동됩니다.</span><span class="sxs-lookup"><span data-stu-id="fab54-205">If you don't include this parameter, or leave it blank, the query is fanned out to all geo locations.</span></span> <span data-ttu-id="fab54-206">각 지리적 위치에 대해 JSON 형식으로 다음 항목을 입력하십시오.</span><span class="sxs-lookup"><span data-stu-id="fab54-206">For each geo location, enter the following items, in JSON format:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="fab54-207">항목</span><span class="sxs-lookup"><span data-stu-id="fab54-207">Item</span></span></th>
<th align="left"><span data-ttu-id="fab54-208">설명</span><span class="sxs-lookup"><span data-stu-id="fab54-208">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="fab54-209">DataLocation</span><span class="sxs-lookup"><span data-stu-id="fab54-209">DataLocation</span></span></td>
<td align="left"><span data-ttu-id="fab54-210">지리적 위치(예: NAM)</span><span class="sxs-lookup"><span data-stu-id="fab54-210">The geo location, for example NAM.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="fab54-211">EndPoint</span><span class="sxs-lookup"><span data-stu-id="fab54-211">EndPoint</span></span></td>
<td align="left"><span data-ttu-id="fab54-212">연결할 끝점(예: https://contoso.sharepoint.com)</span><span class="sxs-lookup"><span data-stu-id="fab54-212">The endpoint to connect to, for example https://contoso.sharepoint.com</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="fab54-213">SourceId</span><span class="sxs-lookup"><span data-stu-id="fab54-213">SourceId</span></span></td>
<td align="left"><span data-ttu-id="fab54-214">결과 원본의 GUID(예: B81EAB55-3140-4312-B0F4-9459D1B4FFEE)</span><span class="sxs-lookup"><span data-stu-id="fab54-214">The GUID of the result source, for example B81EAB55-3140-4312-B0F4-9459D1B4FFEE.</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="fab54-p118">DataLocation 또는 EndPoint를 생략하거나 DataLocation이 중복되면 요청이 실패합니다. [Microsoft Graph를 사용하여 테넌트의 지리적 위치 끝점에 대한 정보를 얻을 수 있습니다](https://docs.microsoft.com/en-us/sharepoint/dev/solution-guidance/multigeo-discovery).</span><span class="sxs-lookup"><span data-stu-id="fab54-p118">If you omit DataLocation or EndPoint, or if a DataLocation is duplicated, the request fails. [You can get information about the endpoint of a tenant's geo locations by using Microsoft Graph](https://docs.microsoft.com/en-us/sharepoint/dev/solution-guidance/multigeo-discovery).</span></span>

### <a name="response-data"></a><span data-ttu-id="fab54-217">응답 데이터</span><span class="sxs-lookup"><span data-stu-id="fab54-217">Response data</span></span>

<span data-ttu-id="fab54-p119">MultiGeoSearchStatus – SharePoint 검색 API가 요청에 대한 응답으로 반환하는 속성입니다. 속성의 값은 문자열이며 SharePoint 검색 API가 반환하는 결과에 대해 다음과 같은 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="fab54-p119">MultiGeoSearchStatus – This is a property that the SharePoint Search API returns in response to a request. The value of the property is a string and gives the following information about the results that the SharePoint Search API returns:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="fab54-220">값</span><span class="sxs-lookup"><span data-stu-id="fab54-220">Value</span></span></th>
<th align="left"><span data-ttu-id="fab54-221">설명</span><span class="sxs-lookup"><span data-stu-id="fab54-221">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="fab54-222">Full</span><span class="sxs-lookup"><span data-stu-id="fab54-222">Full</span></span></td>
<td align="left"><span data-ttu-id="fab54-223"><strong>모든</strong> 지리적 위치의 전체 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="fab54-223">Full results from <strong>all</strong> the geo locations.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="fab54-224">Partial</span><span class="sxs-lookup"><span data-stu-id="fab54-224">Partial</span></span></td>
<td align="left"><span data-ttu-id="fab54-p120">하나 이상의 지리적 위치에서 가져온 부분적인 결과입니다. 일시적인 오류로 인해 결과가 불완전합니다.</span><span class="sxs-lookup"><span data-stu-id="fab54-p120">Partial results from one or more geo locations. The results are incomplete due to a transient error.</span></span></td>
</tr>

</tbody>
</table>

### <a name="query-using-the-rest-service"></a><span data-ttu-id="fab54-227">REST 서비스를 사용하는 쿼리</span><span class="sxs-lookup"><span data-stu-id="fab54-227">Query using the REST service</span></span>

<span data-ttu-id="fab54-p121">GET 요청을 사용하여 URL에 쿼리 매개 변수를 지정합니다. POST 요청을 사용하여 본문에 JSON(JavaScript 개체 표기법) 형식으로 쿼리 매개 변수를 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="fab54-p121">With a GET request, you specify the query parameters in the URL. With a POST request, you pass the query parameters in the body in JavaScript Object Notation (JSON) format.</span></span>


#### <a name="request-headers"></a><span data-ttu-id="fab54-230">요청 헤더</span><span class="sxs-lookup"><span data-stu-id="fab54-230">Request headers</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="fab54-231">이름</span><span class="sxs-lookup"><span data-stu-id="fab54-231">Name</span></span></th>
<th align="left"><span data-ttu-id="fab54-232">값</span><span class="sxs-lookup"><span data-stu-id="fab54-232">Value</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="fab54-233">Content-Type</span><span class="sxs-lookup"><span data-stu-id="fab54-233">Content-Type</span></span></td>
<td align="left"><span data-ttu-id="fab54-234">application/json;odata=verbose</span><span class="sxs-lookup"><span data-stu-id="fab54-234">application/json;odata=verbose</span></span></td>
</tr>
</tbody>
</table>

#### <a name="sample-get-request-thats-fanned-out-to-all-geo-locations"></a><span data-ttu-id="fab54-235">**모든** 지리적 위치로 팬아웃되는 샘플 GET 요청</span><span class="sxs-lookup"><span data-stu-id="fab54-235">Sample GET request that's fanned out to **all** geo locations</span></span>

<span data-ttu-id="fab54-236">https:// \<tenant\>/\_api/search/query?querytext='sharepoint'&Properties='EnableMultiGeoSearch:true'&ClientType='my\_client\_id'</span><span class="sxs-lookup"><span data-stu-id="fab54-236">https:// \<tenant\>/\_api/search/query?querytext='sharepoint'&Properties='EnableMultiGeoSearch:true'&ClientType='my\_client\_id'</span></span>

#### <a name="sample-get-request-to-fan-out-to-some-geo-locations"></a><span data-ttu-id="fab54-237">**일부** 지리적 위치로 팬아웃할 샘플 GET 요청</span><span class="sxs-lookup"><span data-stu-id="fab54-237">Sample GET request to fan out to **some** geo locations</span></span>

<span data-ttu-id="fab54-238">https:// \<tenant\>/\_api/search/query?querytext='site'&ClientType='my_client_id'&Properties='EnableMultiGeoSearch:true, MultiGeoSearchConfiguration:[{DataLocation\\:"NAM"\\Endpoint\\:"https\\://contosoNAM.sharepoint.com"\\,SourceId\\:"B81EAB55-3140-4312-B0F4-9459D1B4FFEE"}\\,{DataLocation\\:"CAN"\\,Endpoint\\:"https\\://contosoCAN.sharepoint-df.com"}]'</span><span class="sxs-lookup"><span data-stu-id="fab54-238">https:// \<tenant\>/\_api/search/query?querytext='site'&ClientType='my_client_id'&Properties='EnableMultiGeoSearch:true, MultiGeoSearchConfiguration:[{DataLocation\\:"NAM"\\,Endpoint\\:"https\\://contosoNAM.sharepoint.com"\\,SourceId\\:"B81EAB55-3140-4312-B0F4-9459D1B4FFEE"}\\,{DataLocation\\:"CAN"\\,Endpoint\\:"https\\://contosoCAN.sharepoint-df.com"}]'</span></span>

> [!NOTE]
> <span data-ttu-id="fab54-239">MultiGeoSearchConfiguration 속성의 지리적 위치 목록에 있는 쉼표와 콜론 앞에는 **백슬래시** 문자가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fab54-239">Commas and colons in the list of geo locations for the MultiGeoSearchConfiguration property are preceded by the **backslash** character.</span></span> <span data-ttu-id="fab54-240">이는 GET 요청이 콜론을 사용하여 속성과 쉼표를 구분하여 속성 인수를 구분하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="fab54-240">This is because GET requests use colons to separate properties and commas to separate arguments of properties.</span></span> <span data-ttu-id="fab54-241">이스케이프 문자로 백슬래시가 없으면 MultiGeoSearchConfiguration 속성이 잘못 해석됩니다.</span><span class="sxs-lookup"><span data-stu-id="fab54-241">Without the backslash as an escape character, the MultiGeoSearchConfiguration property is interpreted wrongly.</span></span>

#### <a name="sample-post-request-thats-fanned-out-to-all-geo-locations"></a><span data-ttu-id="fab54-242">**모든** 지리적 위치로 팬아웃되는 샘플 POST 요청</span><span class="sxs-lookup"><span data-stu-id="fab54-242">Sample POST request that's fanned out to **all** geo locations</span></span>

    {
        "request": {
            "__metadata": {
            "type": "Microsoft.Office.Server.Search.REST.SearchRequest"
        },
        "Querytext": "sharepoint",
        "Properties": {
            "results": [
                {
                    "Name": "EnableMultiGeoSearch",
                    "Value": {
                        "QueryPropertyValueTypeIndex": 3,
                        "BoolVal": true
                    }
                }
            ]
        },
        "ClientType": "my_client_id"
        }
    }


#### <a name="sample-post-request-thats-fanned-out-to-some-geo-locations"></a><span data-ttu-id="fab54-243">**일부** 지리적 위치로 팬아웃되는 샘플 POST 요청</span><span class="sxs-lookup"><span data-stu-id="fab54-243">Sample POST request that's fanned out to **some** geo locations</span></span>


    {
        "request": {
            "Querytext": "SharePoint",
            "ClientType": "my_client_id",
            "Properties": {
                "results": [
                    {
                        "Name": "EnableMultiGeoSearch",
                        "Value": {
                            "QueryPropertyValueTypeIndex": 3,
                            "BoolVal": true
                        }
                    },
                    {
                        "Name": "MultiGeoSearchConfiguration",
                        "Value": {
                        "StrVal": "[{\"DataLocation\":\"NAM\",\"Endpoint\":\"https://contoso.sharepoint.com\",\"SourceId\":\"B81EAB55-3140-4312-B0F4-9459D1B4FFEE\"},{\"DataLocation\":\"CAN\",\"Endpoint\":\"https://contosoCAN.sharepoint.com\"}]",
                            "QueryPropertyValueTypeIndex": 1
                        }
                    }
                ]
            }
        }
    }

### <a name="query-using-csom"></a><span data-ttu-id="fab54-244">CSOM을 사용하는 쿼리</span><span class="sxs-lookup"><span data-stu-id="fab54-244">Query using CSOM</span></span>

<span data-ttu-id="fab54-245">다음은 **모든** 지리적 위치로 팬아웃되는 샘플 CSOM 쿼리입니다.</span><span class="sxs-lookup"><span data-stu-id="fab54-245">Here's a sample CSOM query that's fanned out to **all** geo locations:</span></span>

    var keywordQuery = new KeywordQuery(ctx);
    keywordQuery.QueryText = query.SearchQueryText;
    keywordQuery.ClientType = <enter a string here>;
    keywordQuery["EnableMultiGeoSearch"] = true;

