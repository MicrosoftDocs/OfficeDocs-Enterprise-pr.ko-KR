---
title: 다중-지리적으로 분산 환경 관리
ms.author: tlarsen
author: tklarsen
manager: arnek
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: 다중-지리적으로 분산 환경에서 검색을 구성 하는 방법에 알아봅니다.
ms.openlocfilehash: 0c5c8eaa981c31151c70507da54587a7269f98f5
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/03/2018
---
# <a name="configure-search-for-onedrive-for-business-multi-geo"></a><span data-ttu-id="b522d-103">비즈니스 다중-지리적으로 분산에 대 한 OneDrive에 대 한 검색 구성</span><span class="sxs-lookup"><span data-stu-id="b522d-103">Configure Search for OneDrive for Business Multi-Geo</span></span>

<span data-ttu-id="b522d-104">다중-지리적으로 분산 SharePoint Online (SPO) 환경에서 조직 수 있는 하나의 Office 365 테 넌 트, 되었지만 여러 지리적 위치-에서 자신의 SharePoint 콘텐츠를 저장 한 중앙 위치와 하나 이상의 지리적 위치를 위성 합니다.</span><span class="sxs-lookup"><span data-stu-id="b522d-104">In a Multi-Geo SharePoint Online (SPO) environment, an organization can have one Office 365 tenant, but store their SharePoint content in multiple geographical locations - one central location and one or more satellite geo locations.</span></span>

<span data-ttu-id="b522d-p101">각 지리적 위치에는 자체 검색 인덱스와 검색 센터에 있습니다. 사용자를 검색 하는 경우 쿼리는 모든 인덱스를 정렬 하 고 반환 된 결과 병합 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b522d-p101">Each geographical location has its own search index and Search Center. When a user searches, the query is fanned out to all the indexes, and the returned results are merged.</span></span>

<span data-ttu-id="b522d-p102">예 한 지리적 위치에 있는 사용자는 다른 지리적 위치에 저장 된 콘텐츠 또는 다른 지리적 위치로 제한 되는 SharePoint 사이트에서 콘텐츠를 검색할 수 있습니다. 사용자가이 콘텐츠에 대 한 액세스를 하는 경우 검색 결과 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b522d-p102">For example, a user in one geo location can search for content stored in another geo location, or for content on a SharePoint site that’s restricted to a different geo location. If the user has access to this content, search will show the result.</span></span>

## <a name="which-search-clients-work-in-a-multi-geo-environment"></a><span data-ttu-id="b522d-109">다중-지리적으로 분산 환경에서 클라이언트 작업을 검색 하는?</span><span class="sxs-lookup"><span data-stu-id="b522d-109">Which search clients work in a Multi-Geo environment?</span></span>

<span data-ttu-id="b522d-110">이러한 클라이언트는 모든 지리적 위치에서 결과 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b522d-110">These clients can return results from all geo locations:</span></span>

-   <span data-ttu-id="b522d-111">비즈니스용 OneDrive</span><span class="sxs-lookup"><span data-stu-id="b522d-111">OneDrive for Business</span></span>

-   <span data-ttu-id="b522d-112">Delve</span><span class="sxs-lookup"><span data-stu-id="b522d-112">Delve</span></span>

-   <span data-ttu-id="b522d-113">SharePoint 홈 페이지</span><span class="sxs-lookup"><span data-stu-id="b522d-113">The SharePoint home page</span></span>

-   <span data-ttu-id="b522d-114">검색 센터</span><span class="sxs-lookup"><span data-stu-id="b522d-114">The Search Center</span></span>

-   <span data-ttu-id="b522d-115">SharePoint 검색 API를 사용 하는 사용자 지정 검색 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="b522d-115">Custom search applications that use the SharePoint Search API</span></span>

### <a name="onedrive-for-business"></a><span data-ttu-id="b522d-116">비즈니스용 OneDrive</span><span class="sxs-lookup"><span data-stu-id="b522d-116">OneDrive for Business</span></span>

<span data-ttu-id="b522d-117">다중-지리적으로 분산 환경 설정, OneDrive를 검색 하는 사용자는 즉시 모든 지리적 위치에서 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b522d-117">As soon as the Multi-Geo environment has been set up, users that search in OneDrive get results from all geo locations.</span></span>

### <a name="delve"></a><span data-ttu-id="b522d-118">Delve</span><span class="sxs-lookup"><span data-stu-id="b522d-118">Delve</span></span>

<span data-ttu-id="b522d-119">다중-지리적으로 분산 환경을 Delve에서 검색 하는 사용자를 설정 했으면 하는 즉시 모든 지리적 위치에서 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b522d-119">As soon as the Multi-Geo environment has been set up, users that search in Delve get results from all geo locations.</span></span>

<span data-ttu-id="b522d-p103">Delve 피드와 프로필 카드만 **중앙** 위치에 저장 된 파일의 미리 보기를 표시 합니다. 위성 지리적 위치에 저장 된 파일에 대 한 파일 형식에 대 한 아이콘 대신 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b522d-p103">The Delve feed and the profile card only show previews of files that are stored in the **central** location. For files that are stored in satellite geo locations, the icon for the file type is shown instead.</span></span>

### <a name="the-sharepoint-home-page"></a><span data-ttu-id="b522d-122">SharePoint 홈 페이지</span><span class="sxs-lookup"><span data-stu-id="b522d-122">The SharePoint home page</span></span>

<span data-ttu-id="b522d-p104">다중-지리적으로 분산 환경 설정 된, 하는 즉시 사용자 나타납니다 뉴스, 해당 SharePoint 홈 페이지에 여러 지리적 위치에서 최근 및 열어본 사이트입니다. SharePoint 홈 페이지에서 검색 상자를 사용 하는 경우 이러한만에서 결과 가져올 검색 인덱스에 있는 지리적으로 분산 위치 SPHome 합니다.</span><span class="sxs-lookup"><span data-stu-id="b522d-p104">As soon as the Multi-Geo environment has been set up, users will see news, recent and followed sites from multiple geo locations on their SharePoint home page. If they use search box on the SharePoint home page, they only get results from the geo location SPHome search index is located in.</span></span>

### <a name="the-search-center"></a><span data-ttu-id="b522d-125">검색 센터</span><span class="sxs-lookup"><span data-stu-id="b522d-125">The Search Center</span></span>

<span data-ttu-id="b522d-p105">다중-지리적으로 분산 후 환경에 설정 된, 각 검색 센터는 자신의 지리적 위치에서 결과 표시만 계속입니다. 관리자가 모든 지리적 위치에서 결과를 가져오는 [각 검색 센터의 설정을 변경](#_Set_up_a_1) 해야 합니다. 이후에, 검색 센터에서 검색 하는 사용자가 모든 지리적 위치에서 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b522d-p105">After the Multi-Geo environment has been set up, each Search Center continues to only show results from their own geo location. Admins must [change the settings of each Search Center](#_Set_up_a_1) to get results from all geo locations. Afterwards, users that search in the Search Center get results from all geo locations.</span></span>

### <a name="custom-search-applications"></a><span data-ttu-id="b522d-129">사용자 지정 검색 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="b522d-129">Custom search applications</span></span>

<span data-ttu-id="b522d-p106">평소와 같이 사용자 지정 검색 응용 프로그램을 기존 SharePoint 검색 REST Api를 사용 하 여 검색 인덱스와 상호작용 합니다. 일부 또는 전체, 지리적 위치에서 결과 얻으려면, 응용 프로그램 [API를 호출 하 고 새 다중-지리적으로 분산 쿼리 매개 변수를 포함할](#_Get_custom_search) 요청에 있어야 합니다. 모든 지리적 위치를 쿼리 로그 아웃 팬을 트리거합니다.</span><span class="sxs-lookup"><span data-stu-id="b522d-p106">As usual, custom search applications interact with the search indexes by using the existing SharePoint Search REST APIs. To get results from all, or some geo locations, the application must [call the API and include the new Multi-Geo query parameters](#_Get_custom_search) in the request. This triggers a fan out of the query to all geo locations.</span></span>

### <a name="whats-different-about-search-in-a-multi-geo-environment"></a><span data-ttu-id="b522d-133">다중-지리적으로 분산 환경에서 검색 하는 방법에 대 한 서로 다른 이란?</span><span class="sxs-lookup"><span data-stu-id="b522d-133">What’s different about search in a Multi-Geo environment?</span></span>

<span data-ttu-id="b522d-134">일부 검색 기능을 잘 알고 있어야 수 있습니다는 다중-지리적으로 분산 환경에서 다르게 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="b522d-134">Some search features you might be familiar with, work differently in a Multi-Geo environment.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="b522d-135"><strong>기능</strong></span><span class="sxs-lookup"><span data-stu-id="b522d-135"><strong>Feature</strong></span></span></th>
<th align="left"><span data-ttu-id="b522d-136"><strong>어떻게 작동 합니까</strong></span><span class="sxs-lookup"><span data-stu-id="b522d-136"><strong>How does it work</strong></span></span></th>
<th align="left"><span data-ttu-id="b522d-137"><strong>해결 방법</strong></span><span class="sxs-lookup"><span data-stu-id="b522d-137"><strong>Workaround</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="b522d-138">승격 된 결과</span><span class="sxs-lookup"><span data-stu-id="b522d-138">Promoted results</span></span></td>
<td align="left"><span data-ttu-id="b522d-p107">여러 수준에서 승격 된 결과 함께 쿼리 규칙을 만들 수: 전체 테 넌 트, 사이트 모음 또는 사이트에 대 한 합니다. 다중-지리적으로 분산 환경에서 <strong>모든</strong> 지리적 위치에서 검색 센터에 결과 낼 하려는 경우 <strong>테 넌 트</strong> 수준에서 승격 된 결과 정의 합니다. 원할 경우 <strong></strong> 을 사이트 모음 또는 사이트의 지리적 위치에 있는 검색 센터에서 결과 개선 하기 위한 <strong>사이트 모음</strong> 또는 <strong>사이트</strong> 수준에서 결과 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b522d-p107">You can create query rules with promoted results at different levels: for the whole tenant, for a site collection, or for a site. In a Multi-Geo environment, define promoted results at the <strong>tenant</strong> level if you want to promote the results to the Search Centers in <strong>all</strong> geo locations. If you <strong>only</strong> want to promote results in the Search Center that’s in the geo location of the site collection or site, define the results at the <strong>site collection</strong> or <strong>site</strong> level.</span></span></td>
<td align="left"><span data-ttu-id="b522d-142">지리적으로 분산 위치를 이동 하 고, 같은 다른 규칙 마다 서로 다른 승격 된 결과 필요 하지 않으면 승격 된 테 넌 트 수준에서 결과 정의 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b522d-142">If you don’t need different promoted results per geo location, for example different rules for traveling, we recommend defining promoted results at the tenant level.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="b522d-143">검색 구체화</span><span class="sxs-lookup"><span data-stu-id="b522d-143">Search refiners</span></span></td>
<td align="left"><span data-ttu-id="b522d-p108">테 넌 트의 지리적 위치를 모두에서 구체화를 반환 하 고 집계 하 게 하는 검색 합니다. 집계는 최선을 다, 구체화 개수 100% 정확 하지 못할 수도 있습니다. 대부분의 검색 기반 시나리오가 정확 하이 게도 충분 합니다.</span><span class="sxs-lookup"><span data-stu-id="b522d-p108">Search returns refiners from all the geo locations of a tenant and then aggregates them. The aggregation is a best effort, meaning that the refiner counts might not be 100% accurate. For most search-driven scenarios, this accuracy is sufficient.</span></span></td>
<td align="left"><span data-ttu-id="b522d-147">검색 기반 응용 프로그램의 구체화 완전성을 활용 하는 경우 쿼리 하지 각 지리적 위치 독립적으로 다중-지리적으로 분산 된 팬아웃을 사용 하지 않고 합니다.</span><span class="sxs-lookup"><span data-stu-id="b522d-147">For search-driven applications that depend on refiner completeness, query each geo location independently without using Multi-Geo fan-out.</span></span></td>
</tr>
<tr class="odd">
<td align="left"></td>
<td align="left"><span data-ttu-id="b522d-148">다중-지리적으로 분산 검색 숫자 구체화에 대 한 동적 버킷팅은 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b522d-148">Multi-Geo search doesn’t support dynamic bucketing for numerical refiners.</span></span></td>
<td align="left"><span data-ttu-id="b522d-149">숫자 구체화에 대 한 <a href="https://docs.microsoft.com/en-us/sharepoint/dev/general-development/query-refinement-in-sharepoint">"Discretize" 매개 변수</a> 를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b522d-149">Use the <a href="https://docs.microsoft.com/en-us/sharepoint/dev/general-development/query-refinement-in-sharepoint">“Discretize” parameter</a> for numerical refiners.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="b522d-150">문서 Id</span><span class="sxs-lookup"><span data-stu-id="b522d-150">Document IDs</span></span></td>
<td align="left"><span data-ttu-id="b522d-151">문서 Id에 의존 하는 검색 기반 응용 프로그램을 개발 하는 경우에 여러 지리적 위치에 걸친 다중-지리적으로 분산 환경에서 문서 Id 고유 하지, 지리적 위치 마다 고유 하다는 note 합니다.</span><span class="sxs-lookup"><span data-stu-id="b522d-151">If you’re developing a search-driven application that depends on document IDs, note that document IDs in a Multi-Geo environment aren’t unique across geo locations, they are unique per geo location.</span></span></td>
<td align="left"><span data-ttu-id="b522d-p109">지리적 위치를 식별 하는 열을 추가 했습니다. 고유성을 달성 하기 위해이 열을 사용 합니다. 이 열에는 "GeoLocationSource" 라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="b522d-p109">We’ve added a column that identifies the geo location. Use this column to achieve uniqueness. This column is named “GeoLocationSource”.</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="b522d-155">결과의 수</span><span class="sxs-lookup"><span data-stu-id="b522d-155">Number of results</span></span></td>
<td align="left"><span data-ttu-id="b522d-156">지리적으로 분산 위치의 결합 된 결과 표시 하는 검색 결과 페이지 하지만 500 결과 이외 페이지 불가능 합니다.</span><span class="sxs-lookup"><span data-stu-id="b522d-156">The search results page shows combined results from the geo locations, but it’s not possible to page beyond 500 results.</span></span></td>
<td align="left"></td>
</tr>
</tbody>
</table>

### <a name="whats-not-supported-for-search-in-a-multi-geo-environment"></a><span data-ttu-id="b522d-157">항목 수는 없습니다 다중-지리적으로 분산 환경에서 검색을 위한?</span><span class="sxs-lookup"><span data-stu-id="b522d-157">What’s not supported for search in a Multi-Geo environment?</span></span>

<span data-ttu-id="b522d-158">친숙 한 수도 있습니다 검색 기능 중 일부는 다중-지리적으로 분산 환경에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b522d-158">Some of the search features you might be familiar with, aren’t supported in a Multi-Geo environment.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="b522d-159"><strong>검색 기능</strong></span><span class="sxs-lookup"><span data-stu-id="b522d-159"><strong>Search feature</strong></span></span></th>
<th align="left"><span data-ttu-id="b522d-160"><strong>참고</strong></span><span class="sxs-lookup"><span data-stu-id="b522d-160"><strong>Note</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="b522d-161">응용 프로그램 전용 인증</span><span class="sxs-lookup"><span data-stu-id="b522d-161">App-only authentication</span></span></td>
<td align="left"><span data-ttu-id="b522d-162">응용 프로그램 전용 인증 (서비스에서 액세스 권한을된) 다중-지리적으로 분산 검색에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b522d-162">App-only authentication (privileged access from services) isn’t supported in Multi-Geo search.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="b522d-163">게스트 사용자</span><span class="sxs-lookup"><span data-stu-id="b522d-163">Guest users</span></span></td>
<td align="left"><span data-ttu-id="b522d-164">게스트 사용자는만에서 찾고 지리적 위치에서 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b522d-164">Guest users only get results from the geo location that they’re searching from.</span></span></td>
</tr>
</tbody>
</table>

### <a name="how-does-search-work-in-a-multi-geo-environment"></a><span data-ttu-id="b522d-165">어떻게 역할 검색 다중-지리적으로 분산 환경에서 작동 합니까?</span><span class="sxs-lookup"><span data-stu-id="b522d-165">How does search work in a Multi-Geo environment?</span></span>

<span data-ttu-id="b522d-166">**모든** 검색 클라이언트 기존 SharePoint 검색 REST Api와 상호작용 하는데 사용할 검색 인덱스입니다.</span><span class="sxs-lookup"><span data-stu-id="b522d-166">**All** the search clients use the existing SharePoint Search REST APIs to interact with the search indexes.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><p><img src="media/configure-search-for-multi-geo_image1.png" /></p>
<p><span data-ttu-id="b522d-167">그림 1: 세 지리적 위치를 가진 테 넌 트 간에 검색</span><span class="sxs-lookup"><span data-stu-id="b522d-167">Figure 1: Searching across a tenant with three geo locations</span></span></p></th>
<th align="left"><p><span data-ttu-id="b522d-168">쿼리 속성 EnableMultiGeoSearch와 검색 REST 끝점을 호출 하는 검색 클라이언트 = true입니다.</span><span class="sxs-lookup"><span data-stu-id="b522d-168">Search client calls the Search REST endpoint with the query property EnableMultiGeoSearch= true.</span></span></p>
<p><span data-ttu-id="b522d-169">쿼리는 테 넌 트의 모든 지리적 위치에 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b522d-169">The query is sent to all geo locations in the tenant.</span></span></p>
<p><span data-ttu-id="b522d-170">각 지리적 위치에서 검색 결과 병합 하 고 순위가 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b522d-170">Search results from each geo location are merged and ranked.</span></span></p>
<p><span data-ttu-id="b522d-171">클라이언트 통합된 검색 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b522d-171">Client gets unified search results.</span></span></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table><span data-ttu-id="b522d-p110">

<span id="_Set_up_a" class="anchor"><span id="_Ref501388384" class="anchor"></span></span>다중-지리적으로 분산 검색 각 geos에서 각 검색 끝점을 호출 하 여 작동 합니다. 병합 작업을 수행할 수는 전에 회신 가장 느린 레그에 대 한 리더 우리는 병합 (영문) 될 수행,에 게 원격 이동에 대 한 요청을 동시에 수행 됩니다. 다중-지리적으로 분산을 알 수 있듯이이 검색 환경에 추가 대기 시간을 추가 합니다.  <span id="_Set_up_a_1" class="anchor"><span id="_Ref505252370" class="anchor"></span></span> 
### 모든 지리적 위치에서 결과 표시 하도록 검색 센터를 가져오려면</span><span class="sxs-lookup"><span data-stu-id="b522d-p110">

<span id="_Set_up_a" class="anchor"><span id="_Ref501388384" class="anchor"></span></span>Multi-Geo Search works by calling each search endpoint in each geos. The requests to remote goes are performed in parallel, but to merging to happen, we wait for the slowest leg to reply before we can do the merging. This implies multi-geo add additional latency to the search experience.  <span id="_Set_up_a_1" class="anchor"><span id="_Ref505252370" class="anchor"></span></span>
### Get a Search Center to show results from all geo locations</span></span>

<span data-ttu-id="b522d-176">각 검색 센터는 여러 분야별 하 고 각 범주를 개별적으로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b522d-176">Each Search Center has several verticals and you have to set up each vertical individually.</span></span>

1.  <span data-ttu-id="b522d-177">검색 결과 페이지 및 검색 결과 웹 파트를 편집할 수 있는 권한이 있는 계정으로 다음이 단계를 수행 하는 것을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b522d-177">Ensure that you perform these steps with an account that has permission to edit the search results page and the Search Result Web Part.</span></span>

2.  <span data-ttu-id="b522d-178">검색 결과 페이지로 이동 ( [목록](https://support.office.com/article/174d36e0-2f85-461a-ad9a-8b3f434a4213) 검색 결과 페이지 참조)</span><span class="sxs-lookup"><span data-stu-id="b522d-178">Navigate to the search results page (see the [list](https://support.office.com/article/174d36e0-2f85-461a-ad9a-8b3f434a4213) of search results pages)</span></span>

3.  <span data-ttu-id="b522d-179">설정, 오른쪽, 위쪽 모서리에서 **설정** 기어 아이콘을 클릭 한 다음 **페이지 편집**을 클릭 하 여 세로 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b522d-179">Select the vertical to set up, click **Settings** gear icon in the upper, right corner, and then click **Edit Page**.</span></span>

> ![](media/configure-search-for-multi-geo_image2.png)
>
> <span data-ttu-id="b522d-180">검색 결과 페이지가 편집 모드로 열립니다.</span><span class="sxs-lookup"><span data-stu-id="b522d-180">The search results page opens in Edit mode.</span></span>

1.  <span data-ttu-id="b522d-181">검색 결과 웹 파트에 포인터를 위, 웹 파트의 오른쪽 모서리는 화살표를 클릭 한 다음 메뉴에서 **웹 파트 편집** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b522d-181">In the Search Results Web Part, move the pointer to the upper, right corner of the Web Part, click the arrow, and then click **Edit Web Part** on the menu.</span></span> ![](media/configure-search-for-multi-geo_image3.png)

> <span data-ttu-id="b522d-182">위쪽에서 리본 메뉴에서 검색 결과 웹 파트 도구 창이 열립니다 페이지의 오른쪽입니다.</span><span class="sxs-lookup"><span data-stu-id="b522d-182">The Search Results Web Part tool pane opens under the ribbon in the top right of the page.</span></span>

1.  <span data-ttu-id="b522d-183">웹 파트 도구 창의 **결과 설정을 제어**, 아래에서 **설정** 섹션에서 모든 지리적 위치에서 결과 표시 하도록 검색 결과 웹 파트를 가져올 **결과 표시 다중-지리적으로 분산** 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b522d-183">In the Web Part tool pane, in the **Settings** section, under **Results control settings**, select **Show Multi-Geo results** to get the Search Results Web Part to show results from all geo locations.</span></span>

2.  <span data-ttu-id="b522d-184">하 여 변경 내용을 저장 하 고 웹 파트 도구 창을 닫습니다 **확인** 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b522d-184">Click **OK** to save your change and close the Web Part tool pane.</span></span>

3.  <span data-ttu-id="b522d-185">주 메뉴의 페이지 탭에서 **체크인** 을 클릭 하 여 검색 결과 웹 파트에 변경 내용을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b522d-185">Check your changes to the Search Results Web Part by clicking **Check-In** on the Page tab of the main menu.</span></span>

4.  <span data-ttu-id="b522d-186">페이지 맨 마지막에 나오는 참고에서 제공 하는 링크를 사용 하 여 변경 내용을 게시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b522d-186">Publish the changes by using the link provided in the note at the top of the page.</span></span>

<span id="_Get_custom_search" class="anchor"><span id="_Ref501388387" class="anchor"></span></span>
### <a name="get-custom-search-applications-to-show-results-from-all-or-some-geo-locations"></a><span data-ttu-id="b522d-187">일부 또는 전체 지리적 위치에서 결과 표시 하도록 사용자 지정 검색 응용 프로그램 가져오기</span><span class="sxs-lookup"><span data-stu-id="b522d-187">Get custom search applications to show results from all or some geo locations</span></span>

<span data-ttu-id="b522d-p111">사용자 지정 검색 응용 프로그램 모두 또는 일부를 지리적으로 분산 위치에서 SharePoint 검색 REST API에 요청 된 쿼리 매개 변수를 지정 하 여 결과 가져올 합니다. 쿼리 매개 변수를에 따라 쿼리 모든 지리적 위치에 나 일부 지리적 위치에 정렬 됩니다. 예, 지리적 위치 관련 정보를 찾을 수의 하위 집합을 쿼리할 해야하는 경우에 이러한 아웃 팬을 제어할 수 있습니다. 요청이 성공 하는 경우 SharePoint 검색 REST API 응답 데이터를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="b522d-p111">Custom search applications get results from all, or some, geo locations by specifying query parameters with the request to the SharePoint Search REST API. Depending on the query parameters, the query is fanned out to all geo locations, or to some geo locations. For example, if you only need to query a subset of geo locations to find relevant information, you can control the fan out to only these. If the request succeeds, the SharePoint Search REST API returns response data.</span></span>

### <a name="query-parameters"></a><span data-ttu-id="b522d-192">쿼리 매개 변수</span><span class="sxs-lookup"><span data-stu-id="b522d-192">Query parameters</span></span>

<span data-ttu-id="b522d-p112">**EnableMultiGeoSearch** -쿼리를 Geo 다중 테 넌 트의 다른 지리적 위치를 인덱스에 정렬 항목과 여부를 지정 하는 부울 값입니다. **True** 를 쿼리; 아웃 펼쳐서로 설정 **false** 를 쿼리 아웃 펼쳐서 하지 않습니다. 기본값은 **false**입니다. 쿼리는이 매개 변수를 포함 하지 않으면 다른 지리적 위치에 정렬 **되지 않습니다** . 다중-지리적으로 분산 없는 환경에서 매개 변수를 사용 하는 경우에 매개 변수는 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b522d-p112">**EnableMultiGeoSearch** - This is a Boolean value that specifies whether the query shall be fanned out to the indexes of other geo locations of the Multi-Geo tenant. Set it to **true** to fan out the query; **false** to not fan out the query. The default value is **false**. If you don’t include this parameter, the query is **not** fanned out to other geo locations. If you use the parameter in an environment that isn’t Multi-Geo, the parameter is ignored.</span></span>

<span data-ttu-id="b522d-p113">**ClientType** -문자열입니다. 각 검색 응용 프로그램에 대 한 고유 클라이언트 이름을 입력 합니다. 쿼리는이 매개 변수를 포함 하지 않으면 다른 지리적 위치에 정렬 **되지 않습니다** .</span><span class="sxs-lookup"><span data-stu-id="b522d-p113">**ClientType** - This is a string. Enter a unique client name for each search application. If you don’t include this parameter, the query is **not** fanned out to other geo locations.</span></span>

<span data-ttu-id="b522d-p114">**MultiGeoSearchConfiguration** -는 지리적으로 분산의 다중 지리적 위치 테 넌 트를 ** **EnableMultiGeoSearch** 참인 경우**에 쿼리 펼쳐서 선택 목록입니다. 이 매개 변수를 포함 하지 않거나는 비워둡니다 하지 않는 경우 쿼리 모든 지리적 위치에 정렬 됩니다. 각 지리적 위치에 대 한 JSON 형식에는 다음 항목을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="b522d-p114">**MultiGeoSearchConfiguration** - This is an optional list of which geo locations in the Multi-Geo tenant to fan the query out to when **EnableMultiGeoSearch** is **true**. If you don’t include this parameter, or leave it blank, the query is fanned out to all geo locations. For each geo location, enter the following items, in JSON format:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="b522d-204">항목</span><span class="sxs-lookup"><span data-stu-id="b522d-204">Item</span></span></th>
<th align="left"><span data-ttu-id="b522d-205">설명</span><span class="sxs-lookup"><span data-stu-id="b522d-205">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="b522d-206">DataLocation</span><span class="sxs-lookup"><span data-stu-id="b522d-206">DataLocation</span></span></td>
<td align="left"><span data-ttu-id="b522d-207">지리적으로 분산 위치 이름 예입니다.</span><span class="sxs-lookup"><span data-stu-id="b522d-207">The geo location, for example NAM.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="b522d-208">끝점</span><span class="sxs-lookup"><span data-stu-id="b522d-208">EndPoint</span></span></td>
<td align="left"><span data-ttu-id="b522d-209">예, 연결할 끝점https://contoso.sharepoint.com</span><span class="sxs-lookup"><span data-stu-id="b522d-209">The endpoint to connect to, for example https://contoso.sharepoint.com</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="b522d-210">SourceId</span><span class="sxs-lookup"><span data-stu-id="b522d-210">SourceId</span></span></td>
<td align="left"><span data-ttu-id="b522d-211">결과 원본에 같은 B81EAB55-3140-4312-B0F4-9459D1B4FFEE의 GUID입니다.</span><span class="sxs-lookup"><span data-stu-id="b522d-211">The GUID of the result source, for example B81EAB55-3140-4312-B0F4-9459D1B4FFEE.</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="b522d-p115">DataLocation 또는 끝점을 생략 하면 또는 DataLocation 중복 될 경우에 요청이 실패 합니다. [다음은 Microsoft Graph를 사용 하 여 테 넌 트의 지리적 위치 끝점에 대 한 정보를 얻을 수 있습니다](https://docs.microsoft.com/en-us/sharepoint/dev/solution-guidance/multigeo-discovery).</span><span class="sxs-lookup"><span data-stu-id="b522d-p115">If you omit DataLocation or EndPoint, or if a DataLocation is duplicated, the request fails. [You can get information about the endpoint of a tenant's geo locations by using Microsoft Graph](https://docs.microsoft.com/en-us/sharepoint/dev/solution-guidance/multigeo-discovery).</span></span>

### <a name="response-data"></a><span data-ttu-id="b522d-214">응답 데이터</span><span class="sxs-lookup"><span data-stu-id="b522d-214">Response data</span></span>

<span data-ttu-id="b522d-p116">**MultiGeoSearchStatus** – SharePoint 검색 API는 요청에 대 한 응답으로 반환 하는 속성입니다. 속성의 값은 문자열 및 SharePoint 검색 API를 반환 하는 결과 대 한 다음 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b522d-p116">**MultiGeoSearchStatus** – This is a property that the SharePoint Search API returns in response to a request. The value of the property is a string and gives the following information about the results that the SharePoint Search API returns:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="b522d-217">값</span><span class="sxs-lookup"><span data-stu-id="b522d-217">Value</span></span></th>
<th align="left"><span data-ttu-id="b522d-218">설명</span><span class="sxs-lookup"><span data-stu-id="b522d-218">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="b522d-219">전체</span><span class="sxs-lookup"><span data-stu-id="b522d-219">Full</span></span></td>
<td align="left"><span data-ttu-id="b522d-220">모든 결과를 <strong>모든</strong> 지리적 위치 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b522d-220">Full results from <strong>all</strong> the geo locations.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="b522d-221">부분</span><span class="sxs-lookup"><span data-stu-id="b522d-221">Partial</span></span></td>
<td align="left"><span data-ttu-id="b522d-p117">하나 이상의 지리적 위치에서 일부 결과입니다. 결과 일시적인 오류로 인해 완전 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b522d-p117">Partial results from one or more geo locations. The results are incomplete due to a transient error.</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="b522d-224">없음</span><span class="sxs-lookup"><span data-stu-id="b522d-224">None</span></span></td>
<td align="left"><span data-ttu-id="b522d-225">쿼리 다중-지리적으로 분산 쿼리 없으며 다른 지리적 위치를 정렬 하지 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b522d-225">The query was not a Multi-Geo query and was not fanned out to the other geo locations.</span></span></td>
</tr>
</tbody>
</table>

### <a name="query-using-the-rest-service"></a><span data-ttu-id="b522d-226">REST 서비스를 사용 하 여 쿼리</span><span class="sxs-lookup"><span data-stu-id="b522d-226">Query using the REST service</span></span>

<span data-ttu-id="b522d-p118">GET 요청을 하는 URL에 쿼리 매개 변수를 지정 합니다. POST 요청으로 표기법 JSON (JavaScript Object) 형식에서 본문에 쿼리 매개 변수를 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="b522d-p118">With a GET request, you specify the query parameters in the URL. With a POST request, you pass the query parameters in the body in JavaScript Object Notation (JSON) format.</span></span>

#### <a name="request-headers"></a><span data-ttu-id="b522d-229">요청 헤더</span><span class="sxs-lookup"><span data-stu-id="b522d-229">Request headers</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="b522d-230">이름</span><span class="sxs-lookup"><span data-stu-id="b522d-230">Name</span></span></th>
<th align="left"><span data-ttu-id="b522d-231">값</span><span class="sxs-lookup"><span data-stu-id="b522d-231">Value</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="b522d-232">Content-Type</span><span class="sxs-lookup"><span data-stu-id="b522d-232">Content-Type</span></span></td>
<td align="left"><span data-ttu-id="b522d-233">응용 프로그램/json; odata = 자세한 정보 표시</span><span class="sxs-lookup"><span data-stu-id="b522d-233">application/json;odata=verbose</span></span></td>
</tr>
</tbody>
</table>

#### <a name="sample-get-request-thats-fanned-out-to-all-geo-locations"></a><span data-ttu-id="b522d-234">**모든** 지리적 위치에 정렬 되는 샘플 GET 요청</span><span class="sxs-lookup"><span data-stu-id="b522d-234">Sample GET request that’s fanned out to **all** geo locations</span></span>

<span data-ttu-id="b522d-235">https:// \<테 넌 트\>/\_api/검색/query?querytext ''.value = 속성 'EnableMultiGeoSearch:true' & ClientType = =' 내\_클라이언트\_id'</span><span class="sxs-lookup"><span data-stu-id="b522d-235">https:// \<tenant\>/\_api/search/query?querytext='sharepoint'&Properties='EnableMultiGeoSearch:true'&ClientType='my\_client\_id'</span></span>

#### <a name="sample-get-request-to-fan-out-to-some-geo-locations"></a><span data-ttu-id="b522d-236">샘플 GET 요청을 **일부** 지리적 위치를 팬 하</span><span class="sxs-lookup"><span data-stu-id="b522d-236">Sample GET request to fan out to **some** geo locations</span></span>

<span data-ttu-id="b522d-237">https:// <tenant>/_api/search/query?querytext '사이트' & ClientType = 'my_client_id' & 속성 = ='EnableMultiGeoSearch:true, MultiGeoSearchConfiguration: [{DataLocation\:"이름"\,끝점\:"https\: contosoNAM.sharepoint.com"\,SourceId\:"B81EAB55-3140-4312-B0F4-9459D1B4FFEE"}\,{DataLocation\:"수"\,끝점\:" https\://contosoCAN.sharepoint-df.com "}]'</span><span class="sxs-lookup"><span data-stu-id="b522d-237">https:// <tenant>/_api/search/query?querytext='site'&ClientType='my_client_id'&Properties='EnableMultiGeoSearch:true, MultiGeoSearchConfiguration:[{DataLocation\:"NAM"\,Endpoint\:"https\://contosoNAM.sharepoint.com"\,SourceId\:"B81EAB55-3140-4312-B0F4-9459D1B4FFEE"}\,{DataLocation\:"CAN"\,Endpoint\:"https\://contosoCAN.sharepoint-df.com"}]'</span></span>

#### <a name="sample-post-request-thats-fanned-out-to-all-geo-locations"></a><span data-ttu-id="b522d-238">**모든** 지리적 위치에 정렬 되는 샘플 POST 요청</span><span class="sxs-lookup"><span data-stu-id="b522d-238">Sample POST request that’s fanned out to **all** geo locations</span></span>

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


#### <a name="sample-post-request-thats-fanned-out-to-some-geo-locations"></a><span data-ttu-id="b522d-239">**일부** 지리적 위치에 정렬 되는 샘플 POST 요청</span><span class="sxs-lookup"><span data-stu-id="b522d-239">Sample POST request that’s fanned out to **some** geo locations</span></span>


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

### <a name="query-using-csom"></a><span data-ttu-id="b522d-240">CSOM을 사용 하 여 쿼리</span><span class="sxs-lookup"><span data-stu-id="b522d-240">Query using CSOM</span></span>

<span data-ttu-id="b522d-241">**모든** 지리적 위치에 정렬 되는 샘플 CSOM 쿼리는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b522d-241">Here’s a sample CSOM query that’s fanned out to **all** geo locations:</span></span>

    var keywordQuery = new KeywordQuery(ctx);
    keywordQuery.QueryText = query.SearchQueryText;
    keywordQuery.ClientType = <enter a string here>;
    keywordQuery["EnableMultiGeoSearch"] = true;