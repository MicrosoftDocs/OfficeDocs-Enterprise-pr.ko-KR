---
title: 비즈니스용 OneDrive Multi-Geo 검색 구성
ms.author: tlarsen
author: tklarsen
manager: arnek
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: 다중 위치 환경에서 검색을 구성하는 방법을 알아봅니다.
ms.openlocfilehash: d7e9109eaa7afcf36ea047d00c0bba8f16dd0fde
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/27/2018
ms.locfileid: "18908332"
---
# <a name="configure-search-for-onedrive-for-business-multi-geo"></a><span data-ttu-id="3530a-103">비즈니스용 OneDrive Multi-Geo 검색 구성</span><span class="sxs-lookup"><span data-stu-id="3530a-103">Configure Search for OneDrive for Business Multi-Geo</span></span>

<span data-ttu-id="3530a-104">Multi-Geo SPO(SharePoint Online) 환경에서 조직은 하나의 Office 365 테넌트를 유지할 수 있지만 하나의 중앙 위치와 하나 이상의 위성 지리적 위치로 이루어진 다중 지리적 위치에 해당 SharePoint 콘텐츠를 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3530a-104">In a Multi-Geo SharePoint Online (SPO) environment, an organization can have one Office 365 tenant, but store their SharePoint content in multiple geographical locations - one central location and one or more satellite geo locations.</span></span>

<span data-ttu-id="3530a-p101">각 지리적 위치에는 자체 검색 인덱스 및 검색 센터가 있습니다. 사용자가 검색을 하면 쿼리가 모드 인덱스로 팬아웃되고 반환된 결과는 병합됩니다.</span><span class="sxs-lookup"><span data-stu-id="3530a-p101">Each geographical location has its own search index and Search Center. When a user searches, the query is fanned out to all the indexes, and the returned results are merged.</span></span>

<span data-ttu-id="3530a-p102">예를 들어, 한 지리적 위치에 있는 사용자가 다른 지리적 위치에 저장된 콘텐츠를 검색하거나, 다른 지리적 위치로 제한된 SharePoint 사이트에서 콘텐츠를 검색할 수 있습니다. 사용자가 이 콘텐츠에 액세스할 수 있으면 검색에 해당 결과가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3530a-p102">For example, a user in one geo location can search for content stored in another geo location, or for content on a SharePoint site that’s restricted to a different geo location. If the user has access to this content, search will show the result.</span></span>

## <a name="which-search-clients-work-in-a-multi-geo-environment"></a><span data-ttu-id="3530a-109">Multi-Geo 환경에서는 어떤 검색 클라이언트가 사용되나요?</span><span class="sxs-lookup"><span data-stu-id="3530a-109">Which search clients work in a Multi-Geo environment?</span></span>

<span data-ttu-id="3530a-110">이러한 클라이언트는 모든 지리적 위치의 결과를 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3530a-110">These clients can return results from all geo locations:</span></span>

-   <span data-ttu-id="3530a-111">비즈니스용 OneDrive</span><span class="sxs-lookup"><span data-stu-id="3530a-111">OneDrive for Business</span></span>

-   <span data-ttu-id="3530a-112">Delve</span><span class="sxs-lookup"><span data-stu-id="3530a-112">Delve</span></span>

-   <span data-ttu-id="3530a-113">SharePoint 홈페이지</span><span class="sxs-lookup"><span data-stu-id="3530a-113">The SharePoint Central Administration Web site home page opens.</span></span>

-   <span data-ttu-id="3530a-114">검색 센터</span><span class="sxs-lookup"><span data-stu-id="3530a-114">The Search Center</span></span>

-   <span data-ttu-id="3530a-115">SharePoint 검색 API를 사용하는 사용자 지정 검색 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="3530a-115">Custom search applications that use the SharePoint Search API</span></span>

### <a name="onedrive-for-business"></a><span data-ttu-id="3530a-116">비즈니스용 OneDrive</span><span class="sxs-lookup"><span data-stu-id="3530a-116">OneDrive for Business</span></span>

<span data-ttu-id="3530a-117">Multi-Geo 환경이 설정되는 즉시, OneDrive에서 검색하는 사용자는 모든 지리적 위치에서 결과를 얻습니다.</span><span class="sxs-lookup"><span data-stu-id="3530a-117">As soon as the Multi-Geo environment has been set up, users that search in OneDrive get results from all geo locations.</span></span>

### <a name="delve"></a><span data-ttu-id="3530a-118">Delve</span><span class="sxs-lookup"><span data-stu-id="3530a-118">Delve</span></span>

<span data-ttu-id="3530a-119">Multi-Geo 환경이 설정되는 즉시, Delve에서 검색하는 사용자는 모든 지리적 위치에서 결과를 얻습니다.</span><span class="sxs-lookup"><span data-stu-id="3530a-119">As soon as the Multi-Geo environment has been set up, users that search in Delve get results from all geo locations.</span></span>

<span data-ttu-id="3530a-p103">Delve 피드 및 프로필 카드는 **중앙** 위치에 저장된 파일의 미리 보기만 표시합니다. 위성 지리적 위치에 저장된 파일의 경우 대신 해당 파일 형식에 대한 아이콘이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3530a-p103">The Delve feed and the profile card only show previews of files that are stored in the **central** location. For files that are stored in satellite geo locations, the icon for the file type is shown instead.</span></span>

### <a name="the-sharepoint-home-page"></a><span data-ttu-id="3530a-122">SharePoint 홈페이지</span><span class="sxs-lookup"><span data-stu-id="3530a-122">The SharePoint Central Administration Web site home page opens.</span></span>

<span data-ttu-id="3530a-p104">Multi-Geo 환경이 설정되는 즉시, 사용자는 SharePoint 홈페이지에서 다중 지리적 위치의 뉴스, 최근 사이트 및 팔로우된 사이트를 볼 수 있습니다. SharePoint 홈페이지의 검색 상자를 사용하는 경우 다중 지리적 위치에서 병합된 결과를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3530a-p104">As soon as the Multi-Geo environment has been set up, users will see news, recent and followed sites from multiple geo locations on their SharePoint home page. If they use the search box on the SharePoint home page, they'll get merged results from multiple geo locations.</span></span>

### <a name="the-search-center"></a><span data-ttu-id="3530a-125">검색 센터</span><span class="sxs-lookup"><span data-stu-id="3530a-125">The Search Center</span></span>

<span data-ttu-id="3530a-p105">Multi-Geo 환경이 설정된 후에 각 검색 센터는 자체 지리적 위치의 결과만 계속 표시합니다. 관리자는 모든 지리적 위치에서 결과를 가져오려면 [각 검색 센터의 설정을 변경](#_Set_up_a_1)해야 합니다. 그런 후에 검색 센터에서 검색을 하는 사용자는 모든 지리적 위치에서 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3530a-p105">After the Multi-Geo environment has been set up, each Search Center continues to only show results from their own geo location. Admins must [change the settings of each Search Center](#_Set_up_a_1) to get results from all geo locations. Afterwards, users that search in the Search Center get results from all geo locations.</span></span>

### <a name="custom-search-applications"></a><span data-ttu-id="3530a-129">사용자 지정 검색 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="3530a-129">Custom search applications</span></span>

<span data-ttu-id="3530a-p106">일반적인 경우처럼, 사용자 지정 검색 응용 프로그램은 기존 SharePoint 검색 REST API를 사용하여 검색 인덱스와 상호 작용합니다. 모든 또는 일부 지리적 위치에서 결과를 얻으려면 응용 프로그램은 [API를 호출하고 요청에 새 Multi-Geo 쿼리 매개 변수를 포함](#_Get_custom_search)해야 합니다. 이렇게 하면 모든 지리적 위치로의 쿼리 팬아웃이 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="3530a-p106">As usual, custom search applications interact with the search indexes by using the existing SharePoint Search REST APIs. To get results from all, or some geo locations, the application must [call the API and include the new Multi-Geo query parameters](#_Get_custom_search) in the request. This triggers a fan out of the query to all geo locations.</span></span>

## <a name="whats-different-about-search-in-a-multi-geo-environment"></a><span data-ttu-id="3530a-133">Multi-Geo 환경에서 검색의 차이점은 무엇인가요?</span><span class="sxs-lookup"><span data-stu-id="3530a-133">What’s different about search in a Multi-Geo environment?</span></span>

<span data-ttu-id="3530a-134">이미 익숙할 수 있는 일부 검색 기능이 Multi-Geo 환경에서는 다르게 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="3530a-134">Some search features you might be familiar with, work differently in a Multi-Geo environment.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="3530a-135"><strong>기능</strong></span><span class="sxs-lookup"><span data-stu-id="3530a-135"><strong>Feature</strong></span></span></th>
<th align="left"><span data-ttu-id="3530a-136"><strong>작동 방식</strong></span><span class="sxs-lookup"><span data-stu-id="3530a-136"><strong>How does it work?</strong></span></span></th>
<th align="left"><span data-ttu-id="3530a-137"><strong>해결 방법</strong></span><span class="sxs-lookup"><span data-stu-id="3530a-137"><strong>Workaround</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="3530a-138">승격된 결과</span><span class="sxs-lookup"><span data-stu-id="3530a-138">Promoted results</span></span></td>
<td align="left"><span data-ttu-id="3530a-p107">전체 테넌트, 사이트 모음 또는 사이트 등의 여러 다른 수준에서 승격된 결과로 쿼리 규칙을 만들 수 있습니다. Multi-Geo 환경에서 <strong>모든</strong> 지리적 위치의 검색 센터로 승격하려는 경우 <strong>테넌트</strong> 수준에서 승격된 결과를 정의합니다. 사이트 모음 또는 사이트의 지리적 위치에 있는 검색 센터에서<strong>만</strong> 결과를 승격하려는 경우 <strong>사이트 모음</strong> 또는 <strong>사이트</strong> 수준에서 결과를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="3530a-p107">You can create query rules with promoted results at different levels: for the whole tenant, for a site collection, or for a site. In a Multi-Geo environment, define promoted results at the <strong>tenant</strong> level if you want to promote the results to the Search Centers in <strong>all</strong> geo locations. If you <strong>only</strong> want to promote results in the Search Center that’s in the geo location of the site collection or site, define the results at the <strong>site collection</strong> or <strong>site</strong> level.</span></span></td>
<td align="left"><span data-ttu-id="3530a-142">지리적 위치별로 승격된 다른 결과가 필요하지 않을 경우(예: 여행에 대해 다른 규칙 지정) 테넌트 수준에서 승격된 결과를 정의하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="3530a-142">If you don’t need different promoted results per geo location, for example different rules for traveling, we recommend defining promoted results at the tenant level.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="3530a-143">검색 구체화</span><span class="sxs-lookup"><span data-stu-id="3530a-143">Search refiners</span></span></td>
<td align="left"><span data-ttu-id="3530a-p108">검색은 테넌트의 모든 지리적 위치에서 구체화 결과를 반환한 후 집계합니다. 이러한 집계에는 가능한 최선의 노력이 수반되며, 구체화 개수가 100% 정확하지 않을 수도 있습니다. 대부분의 검색 기반 시나리오에서는 이 정도의 정확도로 충분합니다.</span><span class="sxs-lookup"><span data-stu-id="3530a-p108">Search returns refiners from all the geo locations of a tenant and then aggregates them. The aggregation is a best effort, meaning that the refiner counts might not be 100% accurate. For most search-driven scenarios, this accuracy is sufficient.</span></span></td>
<td align="left"><span data-ttu-id="3530a-147">구체화 완성도에 의존하는 검색 기반 응용 프로그램의 경우 Multi-Geo 팬아웃을 사용하지 않고 개별적으로 각 지리적 위치를 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="3530a-147">For search-driven applications that depend on refiner completeness, query each geo location independently without using Multi-Geo fan-out.</span></span></td>
</tr>
<tr class="odd">
<td align="left"></td>
<td align="left"><span data-ttu-id="3530a-148">Multi-Geo 검색은 수치 구체화에 대한 동적 버킷팅을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3530a-148">Multi-Geo search doesn’t support dynamic bucketing for numerical refiners.</span></span></td>
<td align="left"><span data-ttu-id="3530a-149">숫자 구체화에 대해 <a href="https://docs.microsoft.com/en-us/sharepoint/dev/general-development/query-refinement-in-sharepoint">"Discretize" 매개 변수</a>를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3530a-149">Use the <a href="https://docs.microsoft.com/en-us/sharepoint/dev/general-development/query-refinement-in-sharepoint">“Discretize” parameter</a> for numerical refiners.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="3530a-150">문서 ID</span><span class="sxs-lookup"><span data-stu-id="3530a-150">Unique Document IDs</span></span></td>
<td align="left"><span data-ttu-id="3530a-151">문서 ID에 의존하는 검색 기반 응용 프로그램을 개발하는 경우 Multi-Geo 환경의 문서 ID가 지리적 위치 간에 고유하지 않으며 지리적 위치별로 고유합니다.</span><span class="sxs-lookup"><span data-stu-id="3530a-151">If you’re developing a search-driven application that depends on document IDs, note that document IDs in a Multi-Geo environment aren’t unique across geo locations, they are unique per geo location.</span></span></td>
<td align="left"><span data-ttu-id="3530a-p109">지리적 위치를 식별하는 열을 추가했습니다. 이 열을 사용하여 고유성을 구현할 수 있습니다. 이 열의 이름은 "GeoLocationSource"입니다.</span><span class="sxs-lookup"><span data-stu-id="3530a-p109">We’ve added a column that identifies the geo location. Use this column to achieve uniqueness. This column is named “GeoLocationSource”.</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="3530a-155">결과의 수</span><span class="sxs-lookup"><span data-stu-id="3530a-155">Number of results</span></span></td>
<td align="left"><span data-ttu-id="3530a-156">검색 결과 페이지에는 지리적 위치의 결합된 결과가 표시되지만 500개가 넘는 결과는 여러 페이지로 표시할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3530a-156">The search results page shows combined results from the geo locations, but it’s not possible to page beyond 500 results.</span></span></td>
<td align="left"></td>
</tr>
</tbody>
</table>

## <a name="whats-not-supported-for-search-in-a-multi-geo-environment"></a><span data-ttu-id="3530a-157">Multi-Geo 환경에서 지원되지 않는 검색은 어떤 것인가요?</span><span class="sxs-lookup"><span data-stu-id="3530a-157">What’s not supported for search in a Multi-Geo environment?</span></span>

<span data-ttu-id="3530a-158">기존에 친숙하던 일부 검색 기능이 Multi-Geo 환경에서 지원되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3530a-158">Some of the search features you might be familiar with, aren’t supported in a Multi-Geo environment.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="3530a-159"><strong>검색 기능</strong></span><span class="sxs-lookup"><span data-stu-id="3530a-159"><strong>Search feature</strong></span></span></th>
<th align="left"><span data-ttu-id="3530a-160"><strong>참고</strong></span><span class="sxs-lookup"><span data-stu-id="3530a-160"><strong>Note</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="3530a-161">앱 전용 인증</span><span class="sxs-lookup"><span data-stu-id="3530a-161">App-only authentication</span></span></td>
<td align="left"><span data-ttu-id="3530a-162">앱 전용 인증(서비스의 권한 있는 액세스)은 Multi-Geo 검색에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3530a-162">App-only authentication (privileged access from services) isn’t supported in Multi-Geo search.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="3530a-163">게스트 사용자</span><span class="sxs-lookup"><span data-stu-id="3530a-163">Guest users</span></span></td>
<td align="left"><span data-ttu-id="3530a-164">게스트 사용자는 검색하는 지리적 위치에서만 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3530a-164">Guest users only get results from the geo location that they’re searching from.</span></span></td>
</tr>
</tbody>
</table>

## <a name="how-does-search-work-in-a-multi-geo-environment"></a><span data-ttu-id="3530a-165">Multi-Geo 환경에서 검색은 어떤 방식으로 작동하나요?</span><span class="sxs-lookup"><span data-stu-id="3530a-165">How does search work in a Multi-Geo environment?</span></span>

<span data-ttu-id="3530a-166">**모든** 검색 클라이언트는 기존 SharePoint 검색 REST API를 사용하여 검색 인덱스와 상호 작용합니다.</span><span class="sxs-lookup"><span data-stu-id="3530a-166">**All** the search clients use the existing SharePoint Search REST APIs to interact with the search indexes.</span></span>
<img src="media/configure-search-for-multi-geo_image1-1.png" />

1. <span data-ttu-id="3530a-167">검색 클라이언트는 쿼리 속성 EnableMultiGeoSearch가 true인 검색 REST 끝점을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="3530a-167">A search client calls the Search REST endpoint with the query property EnableMultiGeoSearch= true.</span></span>
2. <span data-ttu-id="3530a-168">쿼리는 테넌트의 모든 지리적 위치로 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="3530a-168">The query is sent to all geo locations in the tenant.</span></span>
3. <span data-ttu-id="3530a-169">각 지리적 위치의 검색 결과가 병합되고 순위가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="3530a-169">Search results from each geo location are merged and ranked.</span></span>
4. <span data-ttu-id="3530a-170">클라이언트는 통합된 검색 결과를 얻습니다.</span><span class="sxs-lookup"><span data-stu-id="3530a-170">The client gets unified search results.</span></span>



<span data-ttu-id="3530a-p110"><span id="_Set_up_a" class="anchor"><span id="_Ref501388384" class="anchor"></span></span>모든 지리적 위치에서 결과를 받을 때까지 검색 결과를 병합하지 않습니다. 즉, Multi-Geo 검색은 단일 지리적 위치만 있는 환경의 검색과 비교할 때 추가적인 대기 시간을 초래합니다.</span><span class="sxs-lookup"><span data-stu-id="3530a-p110"><span id="_Set_up_a" class="anchor"><span id="_Ref501388384" class="anchor"></span></span>Notice that we don’t merge the search results until we’ve received results from all the geo locations. This means that Multi-Geo searches have additional latency compared to searches in an environment with only one geo location.</span></span>

<span id="_Set_up_a_1" class="anchor"><span id="_Ref505252370" class="anchor"></span></span>
## <a name="get-a-search-center-to-show-results-from-all-geo-locations"></a><span data-ttu-id="3530a-173">검색 센터에서 모든 지리적 위치의 결과를 표시하도록 지정</span><span class="sxs-lookup"><span data-stu-id="3530a-173">Get a Search Center to show results from all geo locations</span></span>

<span data-ttu-id="3530a-174">각 검색 센터에는 여러 범주가 있으며 각 범주를 개별적으로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3530a-174">Each Search Center has several verticals and you have to set up each vertical individually.</span></span>

1.  <span data-ttu-id="3530a-175">검색 결과 페이지 및 검색 결과 웹 파트를 편집할 수 있는 권한이 있는 계정으로 다음 단계를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3530a-175">Ensure that you perform these steps with an account that has permission to edit the search results page and the Search Result Web Part.</span></span>

2.  <span data-ttu-id="3530a-176">검색 결과 페이지로 이동합니다(검색 결과 페이지의 [목록](https://support.office.com/article/174d36e0-2f85-461a-ad9a-8b3f434a4213) 참조).</span><span class="sxs-lookup"><span data-stu-id="3530a-176">Navigate to the search results page (see the [list](https://support.office.com/article/174d36e0-2f85-461a-ad9a-8b3f434a4213) of search results pages)</span></span>

3.  <span data-ttu-id="3530a-p111">설정할 범주를 선택하고 오른쪽 위 모서리에 있는 **설정** 톱니바퀴 아이콘을 클릭한 후 **페이지 편집**을 클릭합니다. 검색 결과 페이지가 편집 모드에서 열립니다.</span><span class="sxs-lookup"><span data-stu-id="3530a-p111">Select the vertical to set up, click **Settings** gear icon in the upper, right corner, and then click **Edit Page**. The search results page opens in Edit mode.</span></span>

     ![](media/configure-search-for-multi-geo_image2.png)
1.  <span data-ttu-id="3530a-p112">검색 결과 웹 파트에서 웹 파트 오른쪽 위 모서리로 포인터를 이동하고 화살표를 클릭한 후 메뉴에서 **웹 파트 편집**을 클릭합니다. 검색 결과 웹 파트 도구 창이 페이지 오른쪽 위의 리본 아래에 열립니다. ![](media/configure-search-for-multi-geo_image3.png)</span><span class="sxs-lookup"><span data-stu-id="3530a-p112">In the Search Results Web Part, move the pointer to the upper, right corner of the Web Part, click the arrow, and then click **Edit Web Part** on the menu. The Search Results Web Part tool pane opens under the ribbon in the top right of the page. ![](media/configure-search-for-multi-geo_image3.png)</span></span>

1.  <span data-ttu-id="3530a-181">웹 파트 도구 창의 **설정** 섹션에 있는 **결과 제어 설정**에서 **Multi-Geo 결과 표시**를 선택하여 검색 결과 웹 파트에 모든 지리적 위치의 결과를 표시하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="3530a-181">In the Web Part tool pane, in the **Settings** section, under **Results control settings**, select **Show Multi-Geo results** to get the Search Results Web Part to show results from all geo locations.</span></span>

2.  <span data-ttu-id="3530a-182">**확인**을 클릭하여 변경 내용을 저장하고 웹 파트 도구 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="3530a-182">Click **OK** to save your change and close the Web Part tool pane.</span></span>

3.  <span data-ttu-id="3530a-183">주 메뉴의 페이지 탭에서 **체크 인**을 클릭하여 검색 결과 웹 파트에 대한 변경 내용을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="3530a-183">Check your changes to the Search Results Web Part by clicking **Check-In** on the Page tab of the main menu.</span></span>

4.  <span data-ttu-id="3530a-184">페이지 위쪽의 메모에 제공된 링크를 사용하여 변경 내용을 게시합니다.</span><span class="sxs-lookup"><span data-stu-id="3530a-184">Publish the changes by using the link provided in the note at the top of the page.</span></span>

<span id="_Get_custom_search" class="anchor"><span id="_Ref501388387" class="anchor"></span></span>
## <a name="get-custom-search-applications-to-show-results-from-all-or-some-geo-locations"></a><span data-ttu-id="3530a-185">사용자 지정 검색 응용 프로그램에서 전체 또는 일부 지리적 위치의 결과를 표시하도록 지정</span><span class="sxs-lookup"><span data-stu-id="3530a-185">Get custom search applications to show results from all or some geo locations</span></span>

<span data-ttu-id="3530a-p113">사용자 지정 검색 응용 프로그램은 SharePoint 검색 REST API에 대한 요청을 통해 쿼리 매개 변수를 지정하여 전체 또는 일부 지리적 위치에서 결과를 가져옵니다. 쿼리 매개 변수에 따라, 쿼리는 모든 지리적 위치 또는 일부 지리적 위치로 팬아웃됩니다. 예를 들어, 관련 정보를 찾기 위해 지리적 위치의 하위 집합만 쿼리하면 될 경우 팬아웃을 이러한 위치로만 제어할 수 있습니다. 요청이 성공하면 SharePoint 검색 REST API가 응답 데이터를 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="3530a-p113">Custom search applications get results from all, or some, geo locations by specifying query parameters with the request to the SharePoint Search REST API. Depending on the query parameters, the query is fanned out to all geo locations, or to some geo locations. For example, if you only need to query a subset of geo locations to find relevant information, you can control the fan out to only these. If the request succeeds, the SharePoint Search REST API returns response data.</span></span>

### <a name="query-parameters"></a><span data-ttu-id="3530a-190">쿼리 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3530a-190">Query parameters</span></span>

<span data-ttu-id="3530a-p114">EnableMultiGeoSearch - 쿼리가 Multi-Geo 테넌트의 다른 지리적 위치의 인덱스로 팬아웃될 수 있는지 여부를 지정하는 부울 값입니다. 쿼리를 팬아웃하려면 **true**로 설정하고, 쿼리를 팬아웃하지 않으려면 **false**로 설정합니다. 기본값은 **false**입니다. 이 매개 변수를 포함하지 않을 경우 쿼리가 다른 지리적 위치로 팬아웃되지 **않습니다**. Multi-Geo가 아닌 환경에서 이 매개 변수를 사용하는 경우 매개 변수가 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3530a-p114">EnableMultiGeoSearch - This is a Boolean value that specifies whether the query shall be fanned out to the indexes of other geo locations of the Multi-Geo tenant. Set it to **true** to fan out the query; **false** to not fan out the query. The default value is **false**. If you don’t include this parameter, the query is **not** fanned out to other geo locations. If you use the parameter in an environment that isn’t Multi-Geo, the parameter is ignored.</span></span>

<span data-ttu-id="3530a-p115">ClientType - 문자열입니다. 각 검색 응용 프로그램에 대한 고유한 클라이언트 이름을 입력합니다. 이 매개 변수를 포함하지 않으면 쿼리는 다른 지리적 위치로 팬아웃되지 **않습니다**.</span><span class="sxs-lookup"><span data-stu-id="3530a-p115">ClientType - This is a string. Enter a unique client name for each search application. If you don’t include this parameter, the query is **not** fanned out to other geo locations.</span></span>

<span data-ttu-id="3530a-p116">MultiGeoSearchConfiguration - **EnableMultiGeoSearch**가 **true**로 설정되어 있을 때 Multi-Geo 테넌트에서 쿼리를 팬아웃하는 지리적 위치의 선택적 목록입니다. 이 매개 변수를 포함하지 않거나 비워 두면 쿼리는 모든 지리적 위치로 팬아웃됩니다. 각 지리적 위치에 대해 다음 항목을 JSON 형식으로 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3530a-p116">MultiGeoSearchConfiguration - This is an optional list of which geo locations in the Multi-Geo tenant to fan the query out to when **EnableMultiGeoSearch** is **true**. If you don’t include this parameter, or leave it blank, the query is fanned out to all geo locations. For each geo location, enter the following items, in JSON format:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="3530a-202">항목</span><span class="sxs-lookup"><span data-stu-id="3530a-202">Item</span></span></th>
<th align="left"><span data-ttu-id="3530a-203">설명</span><span class="sxs-lookup"><span data-stu-id="3530a-203">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="3530a-204">DataLocation</span><span class="sxs-lookup"><span data-stu-id="3530a-204">DataLocation</span></span></td>
<td align="left"><span data-ttu-id="3530a-205">지리적 위치(예: NAM)</span><span class="sxs-lookup"><span data-stu-id="3530a-205">The geo location, for example NAM.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="3530a-206">EndPoint</span><span class="sxs-lookup"><span data-stu-id="3530a-206">endpoint</span></span></td>
<td align="left"><span data-ttu-id="3530a-207">연결할 끝점(예: https://contoso.sharepoint.com)</span><span class="sxs-lookup"><span data-stu-id="3530a-207">The endpoint to connect to, for example https://contoso.sharepoint.com</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="3530a-208">SourceId</span><span class="sxs-lookup"><span data-stu-id="3530a-208">SourceId</span></span></td>
<td align="left"><span data-ttu-id="3530a-209">결과 원본의 GUID(예: B81EAB55-3140-4312-B0F4-9459D1B4FFEE)</span><span class="sxs-lookup"><span data-stu-id="3530a-209">The GUID of the result source, for example B81EAB55-3140-4312-B0F4-9459D1B4FFEE.</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="3530a-p117">DataLocation 또는 EndPoint를 생략하거나 DataLocation이 중복되면 요청이 실패합니다. [Microsoft Graph를 사용하여 테넌트의 지리적 위치 끝점에 대한 정보를 얻을 수 있습니다](https://docs.microsoft.com/ko-KR/sharepoint/dev/solution-guidance/multigeo-discovery).</span><span class="sxs-lookup"><span data-stu-id="3530a-p117">If you omit DataLocation or EndPoint, or if a DataLocation is duplicated, the request fails. [You can get information about the endpoint of a tenant's geo locations by using Microsoft Graph](https://docs.microsoft.com/ko-KR/sharepoint/dev/solution-guidance/multigeo-discovery).</span></span>

### <a name="response-data"></a><span data-ttu-id="3530a-212">응답 데이터</span><span class="sxs-lookup"><span data-stu-id="3530a-212">Response data</span></span>

<span data-ttu-id="3530a-p118">MultiGeoSearchStatus – SharePoint 검색 API가 요청에 대한 응답으로 반환하는 속성입니다. 속성의 값은 문자열이며 SharePoint 검색 API가 반환하는 결과에 대해 다음과 같은 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3530a-p118">MultiGeoSearchStatus – This is a property that the SharePoint Search API returns in response to a request. The value of the property is a string and gives the following information about the results that the SharePoint Search API returns:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="3530a-215">값</span><span class="sxs-lookup"><span data-stu-id="3530a-215">Value</span></span></th>
<th align="left"><span data-ttu-id="3530a-216">설명</span><span class="sxs-lookup"><span data-stu-id="3530a-216">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="3530a-217">Full</span><span class="sxs-lookup"><span data-stu-id="3530a-217">Full</span></span></td>
<td align="left"><span data-ttu-id="3530a-218"><strong>모든</strong> 지리적 위치의 전체 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="3530a-218">Full results from <strong>all</strong> the geo locations.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="3530a-219">Partial</span><span class="sxs-lookup"><span data-stu-id="3530a-219">Partial outsourcing</span></span></td>
<td align="left"><span data-ttu-id="3530a-p119">하나 이상의 지리적 위치에서 가져온 부분적인 결과입니다. 일시적인 오류로 인해 결과가 불완전합니다.</span><span class="sxs-lookup"><span data-stu-id="3530a-p119">Partial results from one or more geo locations. The results are incomplete due to a transient error.</span></span></td>
</tr>

</tbody>
</table>

### <a name="query-using-the-rest-service"></a><span data-ttu-id="3530a-222">REST 서비스를 사용하는 쿼리</span><span class="sxs-lookup"><span data-stu-id="3530a-222">Query using the REST service</span></span>

<span data-ttu-id="3530a-p120">GET 요청을 사용하여 URL에 쿼리 매개 변수를 지정합니다. POST 요청을 사용하여 본문에 JSON(JavaScript 개체 표기법) 형식으로 쿼리 매개 변수를 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="3530a-p120">With a GET request, you specify the query parameters in the URL. With a POST request, you pass the query parameters in the body in JavaScript Object Notation (JSON) format.</span></span>

#### <a name="request-headers"></a><span data-ttu-id="3530a-225">요청 헤더</span><span class="sxs-lookup"><span data-stu-id="3530a-225">Request headers</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="3530a-226">이름</span><span class="sxs-lookup"><span data-stu-id="3530a-226">Name</span></span></th>
<th align="left"><span data-ttu-id="3530a-227">값</span><span class="sxs-lookup"><span data-stu-id="3530a-227">Value</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="3530a-228">Content-Type</span><span class="sxs-lookup"><span data-stu-id="3530a-228">Content-Type</span></span></td>
<td align="left"><span data-ttu-id="3530a-229">application/json;odata=verbose</span><span class="sxs-lookup"><span data-stu-id="3530a-229">application/json;odata=verbose</span></span></td>
</tr>
</tbody>
</table>

#### <a name="sample-get-request-thats-fanned-out-to-all-geo-locations"></a><span data-ttu-id="3530a-230">**모든** 지리적 위치로 팬아웃되는 샘플 GET 요청</span><span class="sxs-lookup"><span data-stu-id="3530a-230">Sample GET request that’s fanned out to **all** geo locations</span></span>

<span data-ttu-id="3530a-231">https:// \<tenant\>/\_api/search/query?querytext='sharepoint'&Properties='EnableMultiGeoSearch:true'&ClientType='my\_client\_id'</span><span class="sxs-lookup"><span data-stu-id="3530a-231">https:// \<tenant\>/\_api/search/query?querytext='sharepoint'&Properties='EnableMultiGeoSearch:true'&ClientType='my\_client\_id'</span></span>

#### <a name="sample-get-request-to-fan-out-to-some-geo-locations"></a><span data-ttu-id="3530a-232">**일부** 지리적 위치로 팬아웃할 샘플 GET 요청</span><span class="sxs-lookup"><span data-stu-id="3530a-232">Sample GET request to fan out to **some** geo locations</span></span>

<span data-ttu-id="3530a-233">https:// <tenant>/_api/search/query?querytext='site'&ClientType='my_client_id'&Properties='EnableMultiGeoSearch:true, MultiGeoSearchConfiguration:[{DataLocation\:"NAM"\,Endpoint\:"https\://contosoNAM.sharepoint.com"\,SourceId\:"B81EAB55-3140-4312-B0F4-9459D1B4FFEE"}\,{DataLocation\:"CAN"\,Endpoint\:"https\://contosoCAN.sharepoint-df.com"}]'</span><span class="sxs-lookup"><span data-stu-id="3530a-233">https:// <tenant>/_api/search/query?querytext='site'&ClientType='my_client_id'&Properties='EnableMultiGeoSearch:true, MultiGeoSearchConfiguration:[{DataLocation\:"NAM"\,Endpoint\:"https\://contosoNAM.sharepoint.com"\,SourceId\:"B81EAB55-3140-4312-B0F4-9459D1B4FFEE"}\,{DataLocation\:"CAN"\,Endpoint\:"https\://contosoCAN.sharepoint-df.com"}]'</span></span>

#### <a name="sample-post-request-thats-fanned-out-to-all-geo-locations"></a><span data-ttu-id="3530a-234">**모든** 지리적 위치로 팬아웃되는 샘플 POST 요청</span><span class="sxs-lookup"><span data-stu-id="3530a-234">Sample POST request that’s fanned out to **all** geo locations</span></span>

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


#### <a name="sample-post-request-thats-fanned-out-to-some-geo-locations"></a><span data-ttu-id="3530a-235">**일부** 지리적 위치로 팬아웃되는 샘플 POST 요청</span><span class="sxs-lookup"><span data-stu-id="3530a-235">Sample POST request that’s fanned out to **some** geo locations</span></span>


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

### <a name="query-using-csom"></a><span data-ttu-id="3530a-236">CSOM을 사용하는 쿼리</span><span class="sxs-lookup"><span data-stu-id="3530a-236">Query using CSOM</span></span>

<span data-ttu-id="3530a-237">다음은 **모든** 지리적 위치로 팬아웃되는 샘플 CSOM 쿼리입니다.</span><span class="sxs-lookup"><span data-stu-id="3530a-237">Here’s a sample CSOM query that’s fanned out to **all** geo locations:</span></span>

    var keywordQuery = new KeywordQuery(ctx);
    keywordQuery.QueryText = query.SearchQueryText;
    keywordQuery.ClientType = <enter a string here>;
    keywordQuery["EnableMultiGeoSearch"] = true;

