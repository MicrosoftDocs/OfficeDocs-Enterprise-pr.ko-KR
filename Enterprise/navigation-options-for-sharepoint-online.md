---
title: SharePoint Online에 대한 탐색 옵션
ms.author: krowley
author: kccross
manager: laurawi
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: adb92b80-b342-4ecb-99a1-da2a2b4782eb
description: 이 문서에서는 SharePoint 게시 SharePoint Online에서 사용할 수 있는 탐색 옵션 사이트를 설명 합니다. 선택 및 구성 탐색의 성능 및 SharePoint Online에서 사이트의 확장성에 영향을 현저 하 게 됩니다.
ms.openlocfilehash: 08790dcee343e9e69bbaab149cce8a390470e7d6
ms.sourcegitcommit: 5731dce2440e5a7a261f6360e8e2e9639d339d4e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/12/2018
ms.locfileid: "23957453"
---
# <a name="navigation-options-for-sharepoint-online"></a><span data-ttu-id="c366e-104">SharePoint Online에 대한 탐색 옵션</span><span class="sxs-lookup"><span data-stu-id="c366e-104">Navigation options for SharePoint Online</span></span>

<span data-ttu-id="c366e-p102">이 문서에서는 SharePoint 게시 SharePoint Online에서 사용할 수 있는 탐색 옵션 사이트를 설명 합니다. 선택 및 구성 탐색의 성능 및 SharePoint Online에서 사이트의 확장성에 영향을 현저 하 게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c366e-p102">This article describes navigation options sites with SharePoint Publishing enabled in SharePoint Online. The choice and configuration of navigation significantly impacts the performance and scalability of sites in SharePoint Online.</span></span>

## <a name="overview"></a><span data-ttu-id="c366e-107">개요</span><span class="sxs-lookup"><span data-stu-id="c366e-107">Overview</span></span>

<span data-ttu-id="c366e-p103">탐색 공급자 구성 전체 사이트에 대 한 성능에 영향을 줄 크게 수 및 탐색 공급자 및 SharePoint 사이트의 요구 사항에 대 한 효과적으로 확장할 수 있는 구성 선택 하려면 신중 하 게 고려를 수행 해야 합니다. 사용자 지정 탐색 구현을 뿐아니라 두의 기본 탐색 공급자 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c366e-p103">Navigation provider configuration can significantly impact performance for the entire site, and careful consideration must be taken to pick a navigation provider and configuration that scales effectively for the requirements of a SharePoint site. There are two out-of-the-box navigation providers, as well as custom navigation implementations.</span></span>

<span data-ttu-id="c366e-p104">첫번째 옵션 [**(메타 데이터) 관리 되는 탐색**](#using-managed-navigation-and-metadata-in-sharepoint-online)것이 좋으며, SharePoint Online에서 기본 옵션 중 하나입니다. 그러나 보안 조정 필요 하지 않은 경우 사용할 수 없도록 하는 것이 좋습니다. 이 탐색 공급자 간의 보안 기본 설정으로 상태가 보안 조정 그러나 대부분의 사이트 탐색 요소를 자주 사이트의 모든 사용자에 대해 일관성는 이후 보안 조정의 오버 헤드를 필요 하지 않습니다. 보안 조정을 사용 하지 않으려면 권장 구성과이 탐색 공급자 사이트 구조를 열거 하는 것 필요 하지 않은 이며 적절 한 성능 영향을 주는 뛰어납니다.</span><span class="sxs-lookup"><span data-stu-id="c366e-p104">The first option, [**Managed (Metadata) navigation**](#using-managed-navigation-and-metadata-in-sharepoint-online), is recommended, and is one of the default options in SharePoint Online; however, we recommend that security trimming be disabled unless required. Security trimming is enabled as a secure-by-default setting for this navigation provider; however, many sites do not require the overhead of security trimming since navigation elements often are consistent for all users of the site. With the recommended configuration to disable security trimming, this navigation provider does not require enumerating site structure and is highly scalable with acceptable performance impact.</span></span>

<span data-ttu-id="c366e-p105">두번째 옵션, [**구조적 탐색**](#using-structural-navigation-in-sharepoint-online) **하지 SharePoint Online에서 권장된 탐색 옵션입니다**. 이 탐색 공급자는 온-프레미스 토폴로지를 제한적으로 SharePoint Online에서 지원에 대 한 설계 되었습니다. 일부 추가 집합의 다른 탐색 옵션 비교 기능을 제공 하는 동시에 보안 조정 및 사이트 구조 열거형을 포함 하 여 이러한 기능을 사용 하는 경우 과도 한 서버 통화 및 영향 확장성 및 성능 비용에 가져옵니다. 과도 한 리소스를 사용 하는 사이트 structed 탐색을 사용 하 여 제한에 따라 달라 집니다 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c366e-p105">The second option, [**Structural navigation**](#using-structural-navigation-in-sharepoint-online), **is NOT a recommended navigation option in SharePoint Online**. This navigation provider was designed for an on-premises topology has limited support in SharePoint Online. While it provides some additional set of capabilities versus other navigation options, these features, including security trimming and site structure enumeration, comes at a cost of excessive server calls and impacts scalability and performance when it is used. Sites using structed navigation that consume excessive resources may be subject to throttling.</span></span>

<span data-ttu-id="c366e-p106">다 수의 고객의 기본 탐색 공급자 외에도 대체 사용자 지정 탐색 구현을 성공적으로 구현 했습니다. 탐색 노드의 로컬 캐시를 저장 하는 클라이언트 렌더링 된 디자인 패턴 채택 하는 사용자 지정 탐색 구현의 일반적인 클래스 중 하나입니다. ( **[검색 기반 클라이언트쪽 스크립팅](#using-search-driven-client-side-scripting)** 이 문서에서 참조 합니다.)</span><span class="sxs-lookup"><span data-stu-id="c366e-p106">In addition to the out-of-the-box navigation providers, many customers have successfully implemented alternative custom navigation implementations. One common class of custom navigation implementations embraces client-rendered design patterns that store a local cache of navigation nodes. (See **[Search-driven client-side scripting](#using-search-driven-client-side-scripting)** in this article.)</span></span>

<span data-ttu-id="c366e-120">이러한 탐색 공급자가 메시지를 몇 주요 장점:</span><span class="sxs-lookup"><span data-stu-id="c366e-120">These navigation providers have a couple of key advantages:</span></span> 
- <span data-ttu-id="c366e-121">일반적으로 응답 페이지 디자인을 제대로 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="c366e-121">They generally work well with responsive page designs.</span></span>
- <span data-ttu-id="c366e-122">매우 확장성 및 성능이 자신이 못할 수 있기 때문에 자원 비용 (없고 시간이 초과 후 백그라운드에서 새로고침).</span><span class="sxs-lookup"><span data-stu-id="c366e-122">They are extremely scalable and performant because they can render with no resource cost (and refresh in the background after a timeout).</span></span> 
- <span data-ttu-id="c366e-123">이러한 탐색 공급자는 단순한 정적 구성에서 다양 한 동적 데이터 공급자에 이르기까지 다양 한 전략을 사용 하 여 탐색 데이터를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c366e-123">These navigation providers can retrieve navigation data using various strategies, ranging from simple static configurations to various dynamic data providers.</span></span> 

<span data-ttu-id="c366e-124">데이터 공급자의 예로는 **검색 기반 탐색**, 탐색 노드를 열거 하 고 효율적으로 조정 하는 보안 처리에 대 한 유연성을 허용 하는 사용 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c366e-124">An example of a data provider is to use a **Search-driven navigation**, which allows flexibility for enumerating navigation nodes and handling security trimming efficiently.</span></span> 

<span data-ttu-id="c366e-p107">**사용자 정의 탐색 공급자**작성 인기 있는 다른 옵션이 있습니다. 사용자 정의 탐색 공급자 만들기 (영문)에 대 한 추가 지침에 대 한 [SharePoint 온라인 포털에 대 한 탐색 솔루션](https://docs.microsoft.com/sharepoint/dev/solution-guidance/portal-navigation) 을 검토 하십시오.</span><span class="sxs-lookup"><span data-stu-id="c366e-p107">There are other popular options to build **Custom navigation providers**. Please review [Navigation solutions for SharePoint Online portals](https://docs.microsoft.com/sharepoint/dev/solution-guidance/portal-navigation) for further guidance on building a Custom navigation provider.</span></span>
  
## <a name="pros-and-cons-of-sharepoint-online-navigation-options"></a><span data-ttu-id="c366e-127">전문가 및 SharePoint Online의 단점 탐색 옵션</span><span class="sxs-lookup"><span data-stu-id="c366e-127">Pros and Cons of SharePoint Online navigation options</span></span>

<span data-ttu-id="c366e-128">다음 표에 각 옵션의 장단점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c366e-128">The following table summarizes the pros and cons of each option.</span></span> 


|<span data-ttu-id="c366e-129">관리 탐색</span><span class="sxs-lookup"><span data-stu-id="c366e-129">Managed navigation</span></span>  |<span data-ttu-id="c366e-130">구조적 탐색</span><span class="sxs-lookup"><span data-stu-id="c366e-130">Structural navigation</span></span>  |<span data-ttu-id="c366e-131">검색 기반 탐색</span><span class="sxs-lookup"><span data-stu-id="c366e-131">Search-driven navigation</span></span>  |<span data-ttu-id="c366e-132">사용자 정의 탐색 공급자</span><span class="sxs-lookup"><span data-stu-id="c366e-132">Custom-navigation provider</span></span>  |
|---------|---------|---------|---------|
|<span data-ttu-id="c366e-133">장점:</span><span class="sxs-lookup"><span data-stu-id="c366e-133">Pros:</span></span><br/><br/><span data-ttu-id="c366e-134">쉬운 유지 관리</span><span class="sxs-lookup"><span data-stu-id="c366e-134">Easy to maintain</span></span><br/><span data-ttu-id="c366e-135">권장 되는 옵션</span><span class="sxs-lookup"><span data-stu-id="c366e-135">Recommended option</span></span><br/>     |<span data-ttu-id="c366e-136">장점:</span><span class="sxs-lookup"><span data-stu-id="c366e-136">Pros:</span></span><br/><br/><span data-ttu-id="c366e-137">쉬운 구성</span><span class="sxs-lookup"><span data-stu-id="c366e-137">Easy to configure</span></span><br/><span data-ttu-id="c366e-138">보안 조정이 적용</span><span class="sxs-lookup"><span data-stu-id="c366e-138">Security trimmed</span></span><br/><span data-ttu-id="c366e-139">콘텐츠 추가 됨에 따라 자동으로 업데이트</span><span class="sxs-lookup"><span data-stu-id="c366e-139">Automatically updates as content is added</span></span><br/>|<span data-ttu-id="c366e-140">장점:</span><span class="sxs-lookup"><span data-stu-id="c366e-140">Pros:</span></span><br/><br/><span data-ttu-id="c366e-141">보안 조정이 적용</span><span class="sxs-lookup"><span data-stu-id="c366e-141">Security trimmed</span></span><br/><span data-ttu-id="c366e-142">사이트를 추가할 때 자동으로 업데이트</span><span class="sxs-lookup"><span data-stu-id="c366e-142">Automatically updates as sites are added</span></span><br/><span data-ttu-id="c366e-143">빠른 로드 시간 및 로컬로 캐시된 탐색 구조</span><span class="sxs-lookup"><span data-stu-id="c366e-143">Fast loading time and locally cached navigation structure</span></span><br/>|<span data-ttu-id="c366e-144">장점:</span><span class="sxs-lookup"><span data-stu-id="c366e-144">Pros:</span></span><br/><br/><span data-ttu-id="c366e-145">사용 가능한 옵션에 더 넓은 선택</span><span class="sxs-lookup"><span data-stu-id="c366e-145">Wider choice of options available</span></span><br/><span data-ttu-id="c366e-146">Fast 캐싱 때 로드 되는 올바르게</span><span class="sxs-lookup"><span data-stu-id="c366e-146">Fast loading when caching is used correctly</span></span><br/><span data-ttu-id="c366e-147">다양 한 옵션 응답 페이지 디자인 잘 작동</span><span class="sxs-lookup"><span data-stu-id="c366e-147">Many options work well with responsive page design</span></span><br/>|
|<span data-ttu-id="c366e-148">단점:</span><span class="sxs-lookup"><span data-stu-id="c366e-148">Cons:</span></span><br/><br/><span data-ttu-id="c366e-149">사이트 구조를 반영하도록 자동으로 업데이트되지 않음</span><span class="sxs-lookup"><span data-stu-id="c366e-149">Not automatically updated to reflect site structure</span></span><br/><span data-ttu-id="c366e-150">보안 조정을 사용 하도록 설정 하는 경우 성능에 미치는</span><span class="sxs-lookup"><span data-stu-id="c366e-150">Impacts performance if security trimming is enabled</span></span><br/>|<span data-ttu-id="c366e-151">단점:</span><span class="sxs-lookup"><span data-stu-id="c366e-151">Cons:</span></span><br/><br/><span data-ttu-id="c366e-152">**권장하지 않음**</span><span class="sxs-lookup"><span data-stu-id="c366e-152">**Not recommended**</span></span><br/><span data-ttu-id="c366e-153">**영향을 미치는 성능 및 확장성**</span><span class="sxs-lookup"><span data-stu-id="c366e-153">**Impacts performance and scalability**</span></span><br/><span data-ttu-id="c366e-154">**제한 적용**</span><span class="sxs-lookup"><span data-stu-id="c366e-154">**Subject to throttling**</span></span><br/>|<span data-ttu-id="c366e-155">단점:</span><span class="sxs-lookup"><span data-stu-id="c366e-155">Cons:</span></span><br/><br/><span data-ttu-id="c366e-156">사이트를 쉽게 정렬하는 기능이 없음</span><span class="sxs-lookup"><span data-stu-id="c366e-156">No ability to easily order sites</span></span><br/><span data-ttu-id="c366e-157">마스터 페이지의 사용자 지정 필요(기술 필요)</span><span class="sxs-lookup"><span data-stu-id="c366e-157">Requires customization of the master page (technical skills required)</span></span><br/>|<span data-ttu-id="c366e-158">단점:</span><span class="sxs-lookup"><span data-stu-id="c366e-158">Cons:</span></span><br/><br/><span data-ttu-id="c366e-159">사용자 지정 개발이 필요</span><span class="sxs-lookup"><span data-stu-id="c366e-159">Custom development is required</span></span><br/><span data-ttu-id="c366e-160">외부 데이터 원본을 저장 캐시 필요한 / 예: Azure</span><span class="sxs-lookup"><span data-stu-id="c366e-160">External data source / cache stored is needed e.g. Azure</span></span><br/>|

<span data-ttu-id="c366e-p108">사이트에 대 한 가장 적절 한 옵션에는 사이트 요구 사항 및 기술 사용자 기능에 따라 달라 집니다. 확장 가능한의 기본 탐색 공급자를 사용할 경우 사용 하지 않도록 설정 하는 보안 조정을 사용 하 여 관리 되는 탐색 매우 유용한 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="c366e-p108">The most appropriate option for your site will depend on your site requirements and on your technical capability. If you want a scalable out-of-the-box navigation provider, then Managed navigation with security trimming disabled is a very good option.</span></span> 

<span data-ttu-id="c366e-p109">관리 되는 탐색 옵션을 통해 유지할 수 구성, 코드 사용자 지정 파일을 포함 하지 않는 한 구조적 탐색 보다 훨씬 빠릅니다. 보안 조정 필요 및 사용자 지정 마스터 페이지를 사용 하 여 능숙 하 게은 SharePoint Online에 대 한 기본 마스터 페이지에서 발생할 수 있는 변경 내용을 유지 관리 하기 위해 조직에서 일부 기능이 있어야 하는 경우 다음 검색을 통해 구동 옵션 생성 될 수 있습니다를 좋음 사용자 경험 합니다. 보다 복잡 한 요구 사항에 있는 사용자 지정 탐색 공급자에서 올바른 선택을 수 있습니다. 구조적 탐색 권장 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c366e-p109">The Managed navigation option can be maintained through configuration, does not involve code customization files, and it is significantly faster than structural navigation. If you require security trimming and are comfortable using a custom master page and have some capability in the organization to maintain the changes that may occur in the default master page for SharePoint Online, then the Search-driven option may produce a better user experience. If you have more complex requirements, then a custom navigation provider may be the right choice. Structural navigation is NOT recommended.</span></span>

<span data-ttu-id="c366e-p110">마지막으로 추가 탐색 공급자 및 기능 보다 플랫된 사이트 계층 구조 및 SharePoint 허브 사이트를 사용 하 여 허브 및 스포크 모델을 활용 하는 현대 SharePoint 사이트 아키텍처에 대 한 SharePoint를 추가 하는 것이 중요 합니다. 이 통해 다양 한 시나리오를 구현할 수 필요가 없는 경우 SharePoint 게시 기능을 사용 하 고 이러한 탐색 구성은 확장성과 SharePoint Online 내 대기 시간에 대해 최적화 된 키를 누릅니다. 볼록한 구조를 SharePoint 게시 사이트의 전체 구조를 단순화 하는 동일한 원칙-적용 자주 전반적인 쿼리 성능을 높일 기록한도 확장 합니다. 이 것을 의미는 수백 개의 사이트 (하위 웹)와 단일 사이트 모음을 대신 더 나은 방법은 거의 하위 사이트 (하위 웹) 포함 하는 여러 사이트 모음을 합니다.</span><span class="sxs-lookup"><span data-stu-id="c366e-p110">Finally, it’s important to note that SharePoint is adding additional navigation providers and functionality for modern SharePoint site architectures leveraging a more flattened site hierarchy and a hub-and-spoke model with SharePoint hub sites. This allows many scenarios to be achieved that do NOT require the use of SharePoint Publishing feature, and these navigation configurations are optimized for scalability and latency within SharePoint Online. Note that applying the same principle - simplifying the overall structure of your SharePoint Publishing site to a flatter structure, often helps with overall performance and scale as well. What this means is that instead of having a single Site Collection with hundreds of sites (subwebs), a better approach is to have many site collections with very few subsites (subwebs).</span></span>


## <a name="using-managed-navigation-and-metadata-in-sharepoint-online"></a><span data-ttu-id="c366e-171">SharePoint Online에서 관리 되는 탐색 및 메타 데이터를 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="c366e-171">Using managed navigation and metadata in SharePoint Online</span></span>

<span data-ttu-id="c366e-p111">관리 되는 탐색은 대부분의 구조적 탐색와 동일한 기능을 다시 사용할 수 있는 다른의 기본 옵션입니다. 보안 조정 사용 하거나 사용 하지 않도록 설정 하려면 관리 되는 메타 데이터를 구성할 수 있습니다. 사용 하지 않도록 설정 하는 보안 조정을 구성 하는 경우 서버 통화 상수 번호와 함께 모든 탐색 링크를 로드 하는 것 처럼 관리 되는 탐색이 매우 효율적입니다. 그러나 관리 되는 탐색의 장점 중 일부를 부정 보안 조정 사용 하도록 설정 하 고 고객 최적의 성능 및 확장성에 대 한 사용자 지정 탐색 솔루션 중 하나를 탐색 하도록 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c366e-p111">Managed navigation is another out-of-the-box option that you can use to recreate most of the same functionality as structural navigation. Managed metadata can be configured to have security trimming enabled or disabled. When configured with security trimming disabled, managed navigation is fairly efficient as it loads all the navigation links with a constant number of server calls. Enabling security trimming, however, negates some of the advantages of managed navigation, and customers may choose to explore one of the custom navigation solutions for optimal performance and scalability.</span></span>

<span data-ttu-id="c366e-p112">대부분의 사이트의 탐색 구조는 사이트의 모든 사용자에 대해 일관성 종종으로 보안 조정을 필요 하지 않습니다. 보안 조정을 사용 하지 않으면 모든 사용자가 액세스할 수 있는 탐색 링크가 추가 하는 경우 링크에는 여전히 표시 되지만 액세스 거부 메시지가 하 게 될 합니다. 콘텐츠를 실수로 액세스의 위험은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c366e-p112">Many sites do not require security trimming, as the navigation structure is often consistent for all users of the site. If security trimming is disabled and a link is added to navigation that not all users have access to, the link will still show but will lead to an access denied message. There is no risk of inadvertent access to the content.</span></span>

### <a name="how-to-implement-managed-navigation-and-the-results"></a><span data-ttu-id="c366e-179">관리 탐색 및 결과의 구현 방법</span><span class="sxs-lookup"><span data-stu-id="c366e-179">How to implement managed navigation and the results</span></span>

<span data-ttu-id="c366e-180">여러 문서에는 Docs.Microsoft.com 관리 되는 탐색의 세부 정보에 대 한 예 [SharePoint Server의 관리 탐색 개요 (영문)를](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation)참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="c366e-180">There are several articles on Docs.Microsoft.com about the details of managed navigation, for example, see [Overview of managed navigation in SharePoint Server](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation).</span></span>

<span data-ttu-id="c366e-p113">관리 되는 탐색을 구현 하기 위해 설정한 용어 Url이 포함 된 사이트의 탐색 구조에 해당 합니다. 관리 되는 탐색 대부분의 경우에서 구조적 탐색을 바꾸려면 수동으로 curated도 수 있습니다. 예를 들어:</span><span class="sxs-lookup"><span data-stu-id="c366e-p113">In order to implement managed navigation, you set up terms with URLs corresponding to the navigation structure of  the site. Managed navigation can even be manually curated to replace structural navigation in many cases. For example:</span></span>

![SharePoint Online 사이트 구조](media/SPONavOptionsListOfSites.png)

<span data-ttu-id="c366e-185">아래 예에서는 관리 탐색을 사용한 경우의 복잡한 탐색의 성능을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c366e-185">The following example shows the performance of the complex navigation using managed navigation.</span></span>

![관리 되는 탐색을 사용 하 여 복잡 한 탐색의 성능](media/SPONavOptionsComplexNavPerf.png)

<span data-ttu-id="c366e-187">지속적으로 관리 되는 탐색을 사용 하 여 구조적 탐색 접근 방식에 비해 성능이 향상 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c366e-187">Using managed navigation consistently improves performance compared to the structural navigation approach.</span></span>
  
## <a name="using-structural-navigation-in-sharepoint-online"></a><span data-ttu-id="c366e-188">SharePoint Online에서 구조적 탐색 사용</span><span class="sxs-lookup"><span data-stu-id="c366e-188">Using structural navigation in SharePoint Online</span></span>

<span data-ttu-id="c366e-p114">이것은 기본적으로 사용의 기본 탐색 하 고는 가장 간단한 솔루션 했으나 이와 같이 비용이 많이 드는 성능이 떨어질 있습니다. 모든 사용자 지정이 필요 하지 않습니다 및 비 기술적인 사용자 수도 쉽게 항목을 추가, 항목을 숨기려면 설정 페이지에서 탐색을 관리 합니다. 그러나도 쉽게 관리 하 고 수와 제어 하는 true 되므로으로 관리 되는 탐색을 사용 하는 것이 좋습니다. 관리 되는 탐색에 대 한 향상 된 성능입니다.</span><span class="sxs-lookup"><span data-stu-id="c366e-p114">This is the out-of-the-box navigation used by default and is the most straightforward solution but as such has an expensive performance trade-off. It does not require any customization and a non-technical user can also easily add items, hide items, and manage the navigation from the settings page. This is however also true for Managed Navigation so it is recommended to use Managed Navigation as that can also be easily managed and controlled as well with improved performance.</span></span>

![선택한 표시 하위 사이트를 사용 하 여 구조적 탐색](media/SPONavOptionsStructuredShowSubsites.png)
  
### <a name="turning-on-structural-navigation-in-sharepoint-online"></a><span data-ttu-id="c366e-193">SharePoint Online에서 구조적 탐색 설정</span><span class="sxs-lookup"><span data-stu-id="c366e-193">Turning on structural navigation in SharePoint Online</span></span>

<span data-ttu-id="c366e-p115">구조적 탐색 하 고 표시 된 표준 SharePoint Online 솔루션에서 성능 옵션을 하위 하는 방법을 설명 하기 위해 설정 합니다. 다음은 **사이트 설정** 페이지에서 찾은 설정 스크린샷 \> **탐색**합니다.</span><span class="sxs-lookup"><span data-stu-id="c366e-p115">To illustrate how the performance in a standard SharePoint Online solution with structural navigation and the show subsites option turned on. Below is a screenshot of settings found on the page **Site Settings** \> **Navigation**.</span></span>
  
![하위 사이트를 보여 주는 스크린샷](media/5b6a8841-34ed-4f61-b6d3-9d3e78d393e7.png)
  
### <a name="analyzing-structural-navigation-performance-in-sharepoint-online"></a><span data-ttu-id="c366e-197">SharePoint Online의 구조적 탐색 성능 분석</span><span class="sxs-lookup"><span data-stu-id="c366e-197">Analyzing structural navigation performance in SharePoint Online</span></span>

<span data-ttu-id="c366e-198">SharePoint 페이지의 성능 분석, Internet Explorer에서 F12 개발자 도구에 있는 **네트워크** 탭을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c366e-198">To analyze the performance of a SharePoint page, use the **Network** tab of the F12 developer tools in Internet Explorer.</span></span> 
  
![F12 개발자 도구 네트워크 탭을 보여 주는 스크린샷](media/SPONavOptionsNetworks.png)
  
1. <span data-ttu-id="c366e-200">**네트워크** 탭에서 로드할 .aspx 페이지와 **세부 정보** 탭을 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c366e-200">On the **Network** tab, click on the .aspx page that is being loaded and then click on the **Details** tab.</span></span><br/> <span data-ttu-id="c366e-201">![세부 정보 탭을 보여 주는 스크린샷](media/ad85cefb-7bc5-4932-b29c-25f61b4ceeb2.png)</span><span class="sxs-lookup"><span data-stu-id="c366e-201">![Screenshot showing the details tab](media/ad85cefb-7bc5-4932-b29c-25f61b4ceeb2.png)</span></span><br/>
2. <span data-ttu-id="c366e-202">**응답 헤더**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c366e-202">Click **Response headers**.</span></span> <br/><span data-ttu-id="c366e-203">![세부 정보 탭의 스크린샷](media/c47770ac-5b2b-4941-9830-c57565dec4cc.png)</span><span class="sxs-lookup"><span data-stu-id="c366e-203">![Screenshot of Details tab](media/c47770ac-5b2b-4941-9830-c57565dec4cc.png)</span></span><br/><span data-ttu-id="c366e-204">SharePoint 응답 헤더에 유용한 진단 정보를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c366e-204">SharePoint returns some useful diagnostic information in its response headers.</span></span> 
3. <span data-ttu-id="c366e-p116">**SPRequestDuration** 요청 되는데 걸린 시간 서버에서 프로세스의 밀리초에서 값은 정보의 가장 유용한 항목 중 하나입니다. 다음 스크린샷에 **표시 하위** 선택 되지 않습니다 구조적 탐색에 대 한. 전역 탐색에서 사이트 모음 링크는 것을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="c366e-p116">One of the most useful pieces of information is **SPRequestDuration** which is the value, in milliseconds, of how long a request took to process on the server. In the following screenshot **show subsites** is unchecked for the structural navigation. This means that there is only the site collection link in the global navigation:</span></span><br/><span data-ttu-id="c366e-208">![부하 시간을 요청 기간으로 나타내는 스크린샷](media/3422b2e8-15ec-4bb9-ba86-0965b6b49b01.png)</span><span class="sxs-lookup"><span data-stu-id="c366e-208">![Screenshot showing load times as request duration](media/3422b2e8-15ec-4bb9-ba86-0965b6b49b01.png)</span></span><br/>
4. <span data-ttu-id="c366e-p117">**SPRequestDuration** 키 245 시간 (밀리초)의 값을 갖습니다. 요청을 반환 하는데 걸린 시간을 나타냅니다. 사이트 탐색 항목을 하나만 이므로 SharePoint Online 수행 되는 방법을 굵은 탐색 하지 않고에 대 한 좋은 벤치 마크입니다. 다음 스크린샷은 추가 (영문)의 하위 사이트에서이 키에 주는 영향을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="c366e-p117">The **SPRequestDuration** key has a value of 245 milliseconds. This represents the time it took to return the request. Since there is only one navigation item on the site, this is a good benchmark for how SharePoint Online performs without heavy navigation. The next screen shot shows how adding in the subsites affects this key.</span></span><br/><span data-ttu-id="c366e-213">![2502ms의 요청 기간을 나타내는 스크린샷](media/618ee4e9-2ffa-4a22-b638-fa77b72292b8.png)</span><span class="sxs-lookup"><span data-stu-id="c366e-213">![Screenshot showing a request duration of 2502 ms](media/618ee4e9-2ffa-4a22-b638-fa77b72292b8.png)</span></span><br/>
  
<span data-ttu-id="c366e-p118">하위 사이트 추가 (영문)이 비교적 간단 샘플 사이트에 대 한 페이지 요청을 반환 하는데 걸리는 시간을 크게 증가 했습니다. 복잡 한 사이트 계층 구조, 탐색 영역에서 페이지 및 기타 구성 및 토폴로지 옵션을 포함 하 여에이 영향을 더욱 크게 향상 시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c366e-p118">Adding the subsites has significantly increased the time it takes to return the page request for this relatively simple sample site. Complex site hierarchies, including pages in navigation, and other configuration and topology options can dramatically increase this impact even further.</span></span>

## <a name="using-search-driven-client-side-scripting"></a><span data-ttu-id="c366e-216">검색 기반 클라이언트 쪽 스크립팅 사용</span><span class="sxs-lookup"><span data-stu-id="c366e-216">Using Search-driven client-side scripting</span></span>

<span data-ttu-id="c366e-p119">검색을 사용 하는 연속 크롤링을 사용 하 여 백그라운드에서 제작 하는 인덱스를 활용할 수 있습니다. 검색 인덱스에서 검색 결과 가져오는 및 결과 보안 조정이 적용 됩니다. 보안 조정 필요할 때 일반적으로의 기본 탐색 공급자 보다 더 빠릅니다입니다. 구조적 탐색에 대 한 검색을 사용 하는 복잡 한 사이트 구조를 포함 하는 경우에 특히 더 빠르게 처리할 페이지 로드 시간이 훨씬 합니다. 관리 되는 탐색을 통해이의 주요 이점은 보안 조정에서 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c366e-p119">Using search you can leverage the indexes that are built up in the background using continuous crawl. The search results are pulled from the search index and the results are security-trimmed. This is generally faster than out-of-the-box navigation providers when security trimming is required. Using search for structural navigation, especially if you have a complex site structure, will speed up page loading time considerably. The main advantage of this over managed navigation is that you benefit from security trimming.</span></span>

<span data-ttu-id="c366e-p120">이 방법은 사용자 지정 마스터 페이지를 만들고 사용자 지정 HTML의 기본 탐색 코드 바꿉니다 수 있습니다. 파일에서 탐색 코드를 교체 하려면 다음 예제에 설명 된이 절차에 따라 `seattle.html`합니다. 하면이 예제에서는 열립니다는 `seattle.html` 파일 및 전체 요소 `id=”DeltaTopNavigation”` 사용자 지정 HTML 코드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c366e-p120">This approach involves creating a custom master page and replacing the out-of-the-box navigation code with custom HTML. Follow this procedure outlined in the following example to replace the navigation code in the file `seattle.html`. In this example, you will open the `seattle.html` file and replace the whole element `id=”DeltaTopNavigation”` with custom HTML code.</span></span>

### <a name="example-replace-the-out-of-the-box-navigation-code-in-a-master-page"></a><span data-ttu-id="c366e-225">예: 마스터 페이지에서의 기본 탐색 코드를 대체 합니다.</span><span class="sxs-lookup"><span data-stu-id="c366e-225">Example: Replace the out-of-the-box navigation code in a master page</span></span>

1.  <span data-ttu-id="c366e-226">사이트 설정 페이지로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="c366e-226">Navigate to the Site Settings page.</span></span>
2.  <span data-ttu-id="c366e-227">**마스터 페이지**를 클릭하여 마스터 페이지 갤러리를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="c366e-227">Open the master page gallery by clicking **Master Pages**.</span></span>
3.  <span data-ttu-id="c366e-228">여기에서 라이브러리를 통해 이동 및 파일을 다운로드할 수 있는 `seattle.master`합니다.</span><span class="sxs-lookup"><span data-stu-id="c366e-228">From here you can navigate through the library and download the file `seattle.master`.</span></span>
4.  <span data-ttu-id="c366e-229">텍스트 편집기를 사용하여 코드를 편집하고 아래의 스크린샷과 같이 코드 블록을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="c366e-229">Edit the code using a text editor and delete the code block in the following screen shot.</span></span><br/>![표시 된 코드 블록을 삭제 합니다.](media/SPONavOptionsDeleteCodeBlock.png)<br/>
5. <span data-ttu-id="c366e-231">사이 코드를 제거는 `<SharePoint:AjaxDelta id=”DeltaTopNavigation”>` 및 `<\SharePoint:AjaxDelta>` 태그를 지정 하 고 다음 코드 조각으로 대체 합니다.</span><span class="sxs-lookup"><span data-stu-id="c366e-231">Remove the code between the `<SharePoint:AjaxDelta id=”DeltaTopNavigation”>` and `<\SharePoint:AjaxDelta>` tags and replace it with the following snippet:</span></span><br/>

```
<div id="loading">
  <!--Replace with path to loading image.-->
  <div style="background-image: url(''); height: 22px; width: 22px; ">
  </div>
</div>
<!-- Main Content-->
<div id="navContainer" style="display:none">
    <div data-bind="foreach: hierarchy" class="noindex ms-core-listMenu-horizontalBox">
        <a class="dynamic menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">
            <span class="menu-item-text" data-bind="text: item.Title">
            </span>
        </a>
        <ul id="menu" data-bind="foreach: $data.children" style="padding-left:20px">
            <li class="static dynamic-children level1">
                <a class="static dynamic-children menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">
               
                 <!-- ko if: children.length > 0-->
                    <span aria-haspopup="true" class="additional-background ms-navedit-flyoutArrow dynamic-children">
                        <span class="menu-item-text" data-bind="text: item.Title">
                        </span>
                    </span>
                <!-- /ko -->
                <!-- ko if: children.length == 0-->   
                    <span aria-haspopup="true" class="ms-navedit-flyoutArrow dynamic-children">
                        <span class="menu-item-text" data-bind="text: item.Title">
                        </span>
                    </span>
                <!-- /ko -->   
                </a>
               
                <!-- ko if: children.length > 0-->                                                       
                <ul id="menu"  data-bind="foreach: children;" class="dynamic  level2" >
                    <li class="dynamic level2">
                        <a class="dynamic menu-item ms-core-listMenu-item ms-displayInline  ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">
         
          <!-- ko if: children.length > 0-->
          <span aria-haspopup="true" class="additional-background ms-navedit-flyoutArrow dynamic-children">
           <span class="menu-item-text" data-bind="text: item.Title">
           </span>
          </span>
           <!-- /ko -->
          <!-- ko if: children.length == 0-->
          <span aria-haspopup="true" class="ms-navedit-flyoutArrow dynamic-children">
           <span class="menu-item-text" data-bind="text: item.Title">
           </span>
          </span>                 
          <!-- /ko -->   
                        </a>
          <!-- ko if: children.length > 0-->
         <ul id="menu" data-bind="foreach: children;" class="dynamic level3" >
          <li class="dynamic level3">
           <a class="dynamic menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">
            <span class="menu-item-text" data-bind="text: item.Title">
            </span>
           </a>
          </li>
         </ul>
           <!-- /ko -->
                    </li>
                </ul>
                <!-- /ko -->
            </li>
        </ul>
    </div>
</div>
```
<br/>
6. <span data-ttu-id="c366e-p121">대체 URL을 로드 하는 사이트 모음에 로드 이미지에 대 한 링크와 시작 부분에 앵커 태그 이미지입니다. 변경 된 내용을 변경한 파일 이름을 바꾼 다음 마스터 페이지 갤러리에 업로드 합니다. 새.master 파일을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="c366e-p121">Replace the URL in the loading image anchor tag at the beginning, with a link to a loading image in your site collection. After you have made the changes, rename the file and then upload it to the master page gallery. This generates a new .master file.</span></span><br/>
7. <span data-ttu-id="c366e-p122">이 HTML은 JavaScript 코드에서 반환 하는 검색 결과에서 채울 하는 기본 태그입니다. Var 루트에 대 한 값을 변경 하는 코드 편집 해야하는 다음 코드 조각에서 볼 수 있듯이 "사이트 모음 URL" =:</span><span class="sxs-lookup"><span data-stu-id="c366e-p122">This HTML is the basic markup that will be populated by the search results returned from JavaScript code. You will need to edit the code to change the value for var root = “site collection URL” as demonstrated in the following snippet:</span></span><br/>

```
var root = “https://spperformance.sharepoint.com/sites/NavigationBySearch”;
```
<br/>
8. <span data-ttu-id="c366e-p123">결과 self.nodes 배열에 할당 된 및 배열 self.heirarchy에 출력을 할당 하는 linq.js를 사용 하 여 개체에서 계층 구조를 작성 합니다. 이 배열에는 HTML에 바인딩된 개체입니다. 이 작업은 toggleView() 함수에서 ko.applyBinding() 함수에는 자체 개체를 전달 하 여 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c366e-p123">The results are assigned to the self.nodes array and a hierarchy is built out of the objects using linq.js assigning the output to an array self.heirarchy. This array is the object that is bound to the HTML. This is done in the toggleView() function by passing the self object to the ko.applyBinding() function.</span></span><br/><span data-ttu-id="c366e-240">그런 다음이 위치를 선택 하면 계층 구조 배열의 다음 HTML에 바인딩할 수 있습니다:</span><span class="sxs-lookup"><span data-stu-id="c366e-240">This then causes the hierarchy array to be bound to the following HTML:</span></span><br/>

```
<div data-bind=”foreach: hierarchy” class=”noindex ms-core-listMenu-horizontalBox”>
```

<span data-ttu-id="c366e-241">에 대 한 이벤트 처리기 `mouseenter` 및 `mouseexit` 에서 작업을 수행 하는 하위 사이트 드롭다운 메뉴를 처리할 수 있는 최상위 탐색 모음에 추가 되는 `addEventsToElements()` 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="c366e-241">The event handlers for `mouseenter` and `mouseexit` are added to the top-level navigation to handle the subsite drop-down menus which is done in the `addEventsToElements()` function.</span></span>

<span data-ttu-id="c366e-242">복잡 한 탐색이 예제에서는 새 페이지는 관리 되는 탐색 방식으로 비슷한 결과 얻을 수 벤치 마크 구조적 탐색에서 서버에 소요 된 시간 줄이기 된 로컬 캐싱 표시 하지 않고 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="c366e-242">In our complex navigation example, a fresh page load without the local caching shows the time spent on the server has been cut down from the benchmark structural navigation to get a similar result as the managed navigation approach.</span></span>

### <a name="about-the-javascript-file"></a><span data-ttu-id="c366e-243">JavaScript 파일에 대 한...</span><span class="sxs-lookup"><span data-stu-id="c366e-243">About the JavaScript file...</span></span>

<span data-ttu-id="c366e-244">전체 JavaScript 파일은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c366e-244">The entire JavaScript file is as follows:</span></span>

```
//Models and Namespaces
var SPOCustom = SPOCustom || {};
SPOCustom.Models = SPOCustom.Models || {}
SPOCustom.Models.NavigationNode = function () {

    this.Url = ko.observable("");
    this.Title = ko.observable("");
    this.Parent = ko.observable("");

};

var root = "https://spperformance.sharepoint.com/sites/NavigationBySearch";
var baseUrl = root + "/_api/search/query?querytext=";
var query = baseUrl + "'contentClass=\"STS_Web\"+path:" + root + "'&trimduplicates=false&rowlimit=300";

var baseRequest = {
    url: "",
    type: ""
};


//Parses a local object from JSON search result.
function getNavigationFromDto(dto) {
    var item = new SPOCustom.Models.NavigationNode();
    if (dto != undefined) {

        var webTemplate = getSearchResultsValue(dto.Cells.results, 'WebTemplate');

        if (webTemplate != "APP") {
            item.Title(getSearchResultsValue(dto.Cells.results, 'Title')); //Key = Title
            item.Url(getSearchResultsValue(dto.Cells.results, 'Path')); //Key = Path
            item.Parent(getSearchResultsValue(dto.Cells.results, 'ParentLink')); //Key = ParentLink
        }

    }
    return item;
}

function getSearchResultsValue(results, key) {

    for (i = 0; i < results.length; i++) {
        if (results[i].Key == key) {
            return results[i].Value;
        }
    }
    return null;
}

//Parse a local object from the serialized cache.
function getNavigationFromCache(dto) {
    var item = new SPOCustom.Models.NavigationNode();

    if (dto != undefined) {

        item.Title(dto.Title);
        item.Url(dto.Url);
        item.Parent(dto.Parent);
    }

    return item;
}

/* create a new OData request for JSON response */
function getRequest(endpoint) {
    var request = baseRequest;
    request.type = "GET";
    request.url = endpoint;
    request.headers = { ACCEPT: "application/json;odata=verbose" };
    return request;
};

/* Navigation Module*/
function NavigationViewModel() {
    "use strict";
    var self = this;
    self.nodes = ko.observableArray([]);
    self.hierarchy = ko.observableArray([]);;
    self.loadNavigatioNodes = function () {
        //Check local storage for cached navigation datasource.
        var fromStorage = localStorage["nodesCache"];
        if (false) {
            var cachedNodes = JSON.parse(localStorage["nodesCache"]);

            if (cachedNodes && timeStamp) {
                //Check for cache expiration. Currently set to 3 hrs.
                var now = new Date();
                var diff = now.getTime() - timeStamp;
                if (Math.round(diff / (1000 * 60 * 60)) < 3) {

                    //return from cache.
                    var cacheResults = [];
                    $.each(cachedNodes, function (i, item) {
                        var nodeitem = getNavigationFromCache(item, true);
                        cacheResults.push(nodeitem);
                    });

                    self.buildHierarchy(cacheResults);
                    self.toggleView();
                    addEventsToElements();
                    return;
                }
            }
        }
        //No cache hit, REST call required.
        self.queryRemoteInterface();
    };

    //Executes a REST call and builds the navigation hierarchy.
    self.queryRemoteInterface = function () {
        var oDataRequest = getRequest(query);
        $.ajax(oDataRequest).done(function (data) {
            var results = [];
            $.each(data.d.query.PrimaryQueryResult.RelevantResults.Table.Rows.results, function (i, item) {

                if (i == 0) {
                    //Add root element.
                    var rootItem = new SPOCustom.Models.NavigationNode();
                    rootItem.Title("Root");
                    rootItem.Url(root);
                    rootItem.Parent(null);
                    results.push(rootItem);
                }
                var navItem = getNavigationFromDto(item);
                results.push(navItem);
            });
            //Add to local cache
            localStorage["nodesCache"] = ko.toJSON(results);

            localStorage["nodesCachedAt"] = new Date().getTime();
            self.nodes(results);
            if (self.nodes().length > 0) {
                var unsortedArray = self.nodes();
                var sortedArray = unsortedArray.sort(self.sortObjectsInArray);

                self.buildHierarchy(sortedArray);
                self.toggleView();
                addEventsToElements();
            }
        }).fail(function () {
            //Handle error here!!
            $("#loading").hide();
            $("#error").show();
        });
    };
    self.toggleView = function () {
        var navContainer = document.getElementById("navContainer");
        ko.applyBindings(self, navContainer);
        $("#loading").hide();
        $("#navContainer").show();

    };
    //Uses linq.js to build the navigation tree.
    self.buildHierarchy = function (enumerable) {
        self.hierarchy(Enumerable.From(enumerable).ByHierarchy(function (d) {
            return d.Parent() == null;
        }, function (parent, child) {
            if (parent.Url() == null || child.Parent() == null)
                return false;
            return parent.Url().toUpperCase() == child.Parent().toUpperCase();
        }).ToArray());

        self.sortChildren(self.hierarchy()[0]);
    };


    self.sortChildren = function (parent) {

        // sjip processing if no children
        if (!parent || !parent.children || parent.children.length === 0) {
            return;
        }

        parent.children = parent.children.sort(self.sortObjectsInArray2);

        for (var i = 0; i < parent.children.length; i++) {
            var elem = parent.children[i];

            if (elem.children && elem.children.length > 0) {
                self.sortChildren(elem);
            }
        }
    };

    // ByHierarchy method breaks the sorting in chrome and firefix 
    // we need to resort  as ascending
    self.sortObjectsInArray2 = function (a, b) {
        if (a.item.Title() > b.item.Title())
            return 1;
        if (a.item.Title() < b.item.Title())
            return -1;
        return 0;
    };


    self.sortObjectsInArray = function (a, b) {
        if (a.Title() > b.Title())
            return -1;
        if (a.Title() < b.Title())
            return 1;
        return 0;
    }
}

//Loads the navigation on load and binds the event handlers for mouse interaction.
function InitCustomNav() {
    var viewModel = new NavigationViewModel();
    viewModel.loadNavigatioNodes();
}

function addEventsToElements() {
    //events.
      $("li.level1").mouseover(function () {
          var position = $(this).position();
          $(this).find("ul.level2").css({ width: 100, left: position.left + 10, top: 50 });
      })
   .mouseout(function () {
     $(this).find("ul.level2").css({  left: -99999, top: 0 });
   
    });
   
     $("li.level2").mouseover(function () {
          var position = $(this).position();
          console.log(JSON.stringify(position));
          $(this).find("ul.level3").css({ width: 100, left: position.left + 95, top:  position.top});
      })
   .mouseout(function () {
     $(this).find("ul.level3").css({  left: -99999, top: 0 });
    });
} _spBodyOnLoadFunctionNames.push("InitCustomNav");

``` 

<span data-ttu-id="c366e-p124">위에 표시 된 코드를 요약 하는 `jQuery $(document).ready` 방법이 함수는 `viewModel object` 만든 다음는 `loadNavigationNodes()` 해당 개체에 대해 함수를 호출 합니다. 이 함수는 클라이언트 브라우저의 HTML5 로컬 저장소에 저장 된 이전에 작성된 된 탐색 계층 구조를 로드 하는 중 하나 또는 함수를 호출 하 `queryRemoteInterface()`합니다.</span><span class="sxs-lookup"><span data-stu-id="c366e-p124">To summarize the code shown above in the `jQuery $(document).ready` function there is a `viewModel object` created and then the `loadNavigationNodes()` function on that object is called. This function either loads the previously built navigation hierarchy stored in the HTML5 local storage of the client browser or it calls the function `queryRemoteInterface()`.</span></span>

<span data-ttu-id="c366e-p125">`QueryRemoteInterface()`사용 하 여 요청을 작성은 `getRequest()` 함수는 쿼리 매개 변수와 함께 스크립트 앞부분에서 정의한 하 고 다음 서버에서 데이터를 반환 합니다. 이 데이터는 기본적으로 다양 한 속성으로 표시 되는 데이터 전송 개체로 표현 하는 사이트 모음에 있는 모든 사이트의 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="c366e-p125">`QueryRemoteInterface()` builds a request using the `getRequest()` function with the query parameter defined earlier in the script and then returns data from the server. This data is essentially an array of all the sites in the site collection represented as data transfer objects with various properties.</span></span> 

<span data-ttu-id="c366e-249">이 데이터는 다음 구문 분석 되는 이전에 정의 된으로 `SPO.Models.NavigationNode` 개체를 사용 하는 `Knockout.js` 데이터 이전에 정의한 하는 HTML로 값 바인딩 (영문)에서 사용 하기 위해 눈에 띄는 속성을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c366e-249">This data is then parsed into the previously defined `SPO.Models.NavigationNode` objects which use `Knockout.js` to create observable properties for use by data binding the values into the HTML that we defined earlier.</span></span> 

<span data-ttu-id="c366e-p126">그런 다음 개체는 결과 배열에 배치 됩니다. 이 배열은 녹아웃을 사용 하 여 JSON으로 구문 분석 되 고 이후 페이지 로드에서 성능 향상된을 위해 로컬 브라우저 저장소에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="c366e-p126">The objects are then put into a results array. This array is parsed into JSON using Knockout and stored in the local browser storage for improved performance on future page loads.</span></span>

### <a name="benefits-of-this-approach"></a><span data-ttu-id="c366e-252">이 방법을 사용의 이점</span><span class="sxs-lookup"><span data-stu-id="c366e-252">Benefits of this approach</span></span>

<span data-ttu-id="c366e-p127">[이 방법](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page) 의 주요 이점 중 하나는 HTML5 로컬 저장소를 사용 하 여 탐색 저장 되어 로컬로 사용자에 대 한 다음에 페이지를 로드 합니다. 검색 API를 사용 하 여 구조적 탐색;에 대 한 주요 성능 향상을 얻게 그러나 일부 기술 기능을 실행 하 고이 기능을 사용자 지정을 걸립니다.</span><span class="sxs-lookup"><span data-stu-id="c366e-p127">One major benefit of [this approach](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page) is that by using HTML5 local storage, the navigation is stored locally for the user the next time they load the page. We get major performance improvements from using the search API for structural navigation; however, it takes some technical capability to execute and customize this functionality.</span></span> 

<span data-ttu-id="c366e-p128">[구현 하는 예제](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page)사이트의 기본 구조적 탐색;와 동일한 방식으로 정렬 됩니다. 사전순으로 보여줍니다. 이 순서에서 파생 하는 하고자 하는 경우는 것이 더 복잡 하 고 유지 관리, 개발 합니다. 또한이 방법을 사용을 사용 하면 지원 되는 마스터 페이지에서 파생 하는으로 해야 합니다. 사용자 지정 마스터 페이지, 유지 하지 않는 경우 사이트를에 업데이트 및 마스터 페이지를 Microsoft에 게 하는 향상 된 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="c366e-p128">In the [example implementation](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page), the sites are ordered in the same way as the out-of-the-box structural navigation; alphabetical order. If you wanted to deviate from this order, it would be more complicated to develop and maintain. Also, this approach requires you to deviate from the supported master pages. If the custom master page is not maintained, your site will miss out on updates and improvements that Microsoft makes to the master pages.</span></span>

<span data-ttu-id="c366e-259">[위의 코드는](#about-the-javascript-file) 다음과 같은 종속성에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c366e-259">The [above code](#about-the-javascript-file) has the following dependencies:</span></span>

- <span data-ttu-id="c366e-260">jQuery-http://jquery.com/</span><span class="sxs-lookup"><span data-stu-id="c366e-260">jQuery - http://jquery.com/</span></span>
- <span data-ttu-id="c366e-261">KnockoutJS-http://knockoutjs.com/</span><span class="sxs-lookup"><span data-stu-id="c366e-261">KnockoutJS - http://knockoutjs.com/</span></span>
- <span data-ttu-id="c366e-262">Linq.js- http://linqjs.codeplex.com/, 또는 github.com/neuecc/linq.js</span><span class="sxs-lookup"><span data-stu-id="c366e-262">Linq.js - http://linqjs.codeplex.com/, or github.com/neuecc/linq.js</span></span>

<span data-ttu-id="c366e-p129">LinqJS의 현재 버전 위의 코드에 사용 되는 ByHierarchy 메서드를 포함 하지 않는 및 탐색 코드의 연결이 끊어집니다. 이 문제를 해결 하려면 다음 메서드를 줄 앞 Linq.js 파일에 추가 `Flatten: function ()`합니다.</span><span class="sxs-lookup"><span data-stu-id="c366e-p129">The current version of LinqJS does not contain the ByHierarchy method used in the above code and will break the navigation code. To fix this, add the following method to the Linq.js file before the line `Flatten: function ()`.</span></span>

```
ByHierarchy: function(firstLevel, connectBy, orderBy, ascending, parent) {
     ascending = ascending == undefined ? true : ascending;
     var orderMethod = ascending == true ? 'OrderBy' : 'OrderByDescending';
     var source = this;
     firstLevel = Utils.CreateLambda(firstLevel);
     connectBy = Utils.CreateLambda(connectBy);
     orderBy = Utils.CreateLambda(orderBy);
    
     //Initiate or increase level
     var level = parent === undefined ? 1 : parent.level + 1;

    return new Enumerable(function() {
         var enumerator;
         var index = 0;

        var createLevel = function() {
                 var obj = {
                     item: enumerator.Current(),
                     level : level
                 };
                 obj.children = Enumerable.From(source).ByHierarchy(firstLevel, connectBy, orderBy, ascending, obj);
                 if (orderBy !== undefined) {
                     obj.children = obj.children[orderMethod](function(d) {
                         return orderBy(d.item); //unwrap the actual item for sort to work
                     });
                 }
                 obj.children = obj.children.ToArray();
                 Enumerable.From(obj.children).ForEach(function(child) {
                     child.getParent = function() {
                         return obj;
                     };
                 });
                 return obj;
             };

        return new IEnumerator(

        function() {
             enumerator = source.GetEnumerator();
         }, function() {
             while (enumerator.MoveNext()) {
                 var returnArr;
                 if (!parent) {
                     if (firstLevel(enumerator.Current(), index++)) {
                         return this.Yield(createLevel());
                     }

                } else {
                     if (connectBy(parent.item, enumerator.Current(), index++)) {
                         return this.Yield(createLevel());
                     }
                 }
             }
             return false;
         }, function() {
             Utils.Dispose(enumerator);
         })
     });
 },

```
  
## <a name="related-topics"></a><span data-ttu-id="c366e-265">관련 항목</span><span class="sxs-lookup"><span data-stu-id="c366e-265">Related topics</span></span>

[<span data-ttu-id="c366e-266">SharePoint Server의 관리 탐색 개요</span><span class="sxs-lookup"><span data-stu-id="c366e-266">Overview of managed navigation in SharePoint Server</span></span>](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation)

