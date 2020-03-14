---
title: SharePoint Online 최신 사이트 페이지에서 웹 파트 성능 최적화
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 03/11/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.reviewer: sstewart
search.appverid:
- MET150
description: SharePoint Online 최신 사이트 페이지의 웹 파트 성능을 최적화하는 방법에 대해 배워보세요.
ms.openlocfilehash: 48eba5f638d75cb12b7b4dcf516a9c3833cf8f4d
ms.sourcegitcommit: c024b48115cebfdaadfbc724acc2d065394156e9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/11/2020
ms.locfileid: "42603747"
---
# <a name="optimize-web-part-performance-in-sharepoint-online-modern-site-pages"></a><span data-ttu-id="b7766-103">SharePoint Online 최신 사이트 페이지에서 웹 파트 성능 최적화</span><span class="sxs-lookup"><span data-stu-id="b7766-103">Optimize web part performance in SharePoint Online modern site pages</span></span>

<span data-ttu-id="b7766-104">SharePoint Online 최신 사이트 페이지에는 전체 페이지 로드 시간을 유발할 수 있는 웹 파트가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b7766-104">SharePoint Online modern site pages contain web parts that can contribute to overall page load times.</span></span> <span data-ttu-id="b7766-105">이 문서는 페이지의 웹 파트가 어떻게 사용자가 인식하는 대기 시간에 미치는 영향을 미치는지와 일반적인 문제를 해결하는 방법을 이해하는데 도움을 줄 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b7766-105">This article will help you understand how to determine how web parts in your pages affect user perceived latency, and how to remediate common issues.</span></span>

>[!NOTE]
><span data-ttu-id="b7766-106">SharePoint Online 최신 포털의 성능에 대한 자세한 내용은 [최신 SharePoint 환경의 성능](https://docs.microsoft.com/sharepoint/modern-experience-performance)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b7766-106">For more information about performance in SharePoint Online modern portals, see [Performance in the modern SharePoint experience](https://docs.microsoft.com/sharepoint/modern-experience-performance).</span></span>

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-web-parts"></a><span data-ttu-id="b7766-107">SharePoint 용 페이지 진단 도구를 사용한 웹 파트</span><span class="sxs-lookup"><span data-stu-id="b7766-107">Use the Page Diagnostics for SharePoint tool to analyze web parts</span></span>

<span data-ttu-id="b7766-108">SharePoint용 페이지 진단 도구는 새 Microsoft Edge에 대한 브라우저 확장입니다. (SharePoint Online 최신 포털 및 클래식 게시 사이트 페이지를 분석하는 https://www.microsoft.com/edge) 및 Chrome 브라우저)</span><span class="sxs-lookup"><span data-stu-id="b7766-108">The Page Diagnostics for SharePoint tool is a browser extension for the new Microsoft Edge (https://www.microsoft.com/edge) and Chrome browsers that analyzes both SharePoint Online modern portal and classic publishing site pages.</span></span> <span data-ttu-id="b7766-109">이 도구는 정의된 성능 기준의 집합 대비 페이지 수행 방식을 보여주는 분석된 각 페이지에 대한 보고서를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b7766-109">The tool provides a report for each analyzed page showing how the page performs against a defined set of performance criteria.</span></span> <span data-ttu-id="b7766-110">Sharepoint용 페이지 진단 도구에 대해 배우고 설치하려면[Sharepoint Online에 페이지 진단 도구 사용](page-diagnostics-for-spo.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b7766-110">To install and learn about the Page Diagnostics for SharePoint tool, visit [Use the Page Diagnostics tool for SharePoint Online](page-diagnostics-for-spo.md).</span></span>

>[!NOTE]
><span data-ttu-id="b7766-111">페이지 진단 도구는 SharePoint Online에서만 사용할 수 있으며 SharePoint 시스템 페이지에서는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b7766-111">The Page Diagnostics tool only works for SharePoint Online, and cannot be used on a SharePoint system page.</span></span>

<span data-ttu-id="b7766-112">Sharepoint용 페이지 진단 도구를 사용하여 Sharepoint 사이트 페이지를 분석 시 _진단 테스트_ 창의 페이지 **로드 시간 에 영향을 미치는 웹 파트** 결과에서 기준치를 초과하는 웹 파트에 대한 정보를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b7766-112">When you analyze a SharePoint site page with the Page Diagnostics for SharePoint tool, you can see information about web parts that exceed the baseline metric in the **Web parts are impacting page load time** result in the _Diagnostic tests_ pane.</span></span>

<span data-ttu-id="b7766-113">잠정 결과는 다음과 같습니다:</span><span class="sxs-lookup"><span data-stu-id="b7766-113">Possible results include:</span></span>

- <span data-ttu-id="b7766-114">**주의 필요** (빨간색): 로드하는데 **2**초 보다 긴 시간이 걸리는 뷰포트(처음 로드되는 페이지의 화면에 표시되는 부분)에서 볼 수 있는 _사용자 지정_ 웹 파트입니다.</span><span class="sxs-lookup"><span data-stu-id="b7766-114">**Attention required** (red): Any _custom_ web part that is visible in the viewport (screen visible portion of the page which is loaded first) that takes longer than **two** seconds to load.</span></span> <span data-ttu-id="b7766-115">로드하는데 **4**초 보다 긴 시간이 걸리는 뷰포트 외부의 _사용자 지정_ 웹 파트입니다.</span><span class="sxs-lookup"><span data-stu-id="b7766-115">Any _custom_ web parts outside of the viewport that take longer than **four** seconds to load.</span></span> <span data-ttu-id="b7766-116">테스트 결과에 표시되는 총 로드 시간은 모듈 로드, 지연 로드, 초기화 및 렌더링으로 나누어집니다.</span><span class="sxs-lookup"><span data-stu-id="b7766-116">Total load time is displayed in test results and is broken down by module load, lazy load, init and render.</span></span>
- <span data-ttu-id="b7766-117">**개선 기회** (노란색): 페이지 로드 시간에 영향을 미칠 수 있는 항목은 이 섹션에 표시되며 검토하고 모니터링해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7766-117">**Improvement opportunities** (yellow): Items that may be impacting page load time are shown in this section and should be reviewed and monitored.</span></span> <span data-ttu-id="b7766-118">여기에는 "특별” (OOTB) Microsoft 웹 파트가 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b7766-118">This may include "out of the box" (OOTB) Microsoft web parts.</span></span> <span data-ttu-id="b7766-119">이 섹션에 표시된 Microsoft 웹 파트의 결과는 자동으로 Microsoft에 보고되므로 **어떠한 조치도 필요하지 않습니다**.</span><span class="sxs-lookup"><span data-stu-id="b7766-119">Results for any Microsoft web parts shown in this section are automatically reported to Microsoft, so **no action is required**.</span></span> <span data-ttu-id="b7766-120">페이지에서 성능이 매우 느리거나 페이지에 있는 **모든 Microsoft 웹 파트**가 **개선 기회** 섹션의 결과에 표시되는 경우에만 검사에 대한 지원 티켓을 기록해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7766-120">You should only log a support ticket for investigation if you are experiencing very slow performance on the page and **all Microsoft web parts** on the page appear in the results in the **Improvement opportunities** section.</span></span> <span data-ttu-id="b7766-121">차후 SharePoint용 페이지 진단 도구를 업데이트하면 Microsoft 웹 파트의 특정 구성에 따라 결과를 더 세분화합니다.</span><span class="sxs-lookup"><span data-stu-id="b7766-121">Note that a future Page Diagnostics for SharePoint tool update will further break down the results based on the specific configuration of the Microsoft web part.</span></span>
- <span data-ttu-id="b7766-122">**조치가 필요하지 않음** (녹색): 데이터를 반환하는데 어떠한 웹 파트도 **2**초를 초과하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b7766-122">**No action required** (green): No web part is taking longer than **two** seconds to return data.</span></span>

<span data-ttu-id="b7766-123">**페이지 로드 시간 결과에 영향을 미치는 웹 파트**가 **주의가 필요** 또는 **개선 기회** 섹션에 표시되는 경우 결과를 클릭하여 느리게 로드되는 웹 파트에 대한 세부정보를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b7766-123">If the **Web parts are impacting page load time** result appears in either the **Attention required** or **Improvement opportunities** section of the results, click the result to see details about which web parts are loading slowly.</span></span> <span data-ttu-id="b7766-124">차후 SharePoint 용 페이지 진단 도구를 업데이트는 분석 규칙에 대한 업데이트를 포함할 수 있으므로 항상 최신 버전의 도구를 보유하고 있는지 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="b7766-124">Future updates to the Page Diagnostics for SharePoint tool may include updates to analysis rules, so please ensure you always have the latest version of the tool.</span></span>

![페이지 진단 도구 결과](media/modern-portal-optimization/pagediag-web-part.png)

<span data-ttu-id="b7766-126">결과로 제공되는 정보에는 다음이 포함됩니다:</span><span class="sxs-lookup"><span data-stu-id="b7766-126">Information available in the results includes:</span></span>

- <span data-ttu-id="b7766-127">**구축**은 웹 파트가 사용자 지정인지 Microsoft OOTB인지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b7766-127">**Made by** shows whether the web part is custom or Microsoft OOTB</span></span>
- <span data-ttu-id="b7766-128">**이름 및 ID**는 페이지에서 웹 파트를 찾는데 도움이 될 수 있는 식별정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b7766-128">**Name and ID** shows identifying information that can help you find the web part on the page</span></span>
- <span data-ttu-id="b7766-129">**총계**는 웹 파트가 로드되는 총 시간을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7766-129">**Total** shows the total time for the web part to load</span></span>
- <span data-ttu-id="b7766-130">**모듈 부하**는 웹 파트 구성요소를 가지고 와서 로드하는데 걸리는 시간을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b7766-130">**Module Load** shows the time taken to fetch and load the web part components</span></span>
- <span data-ttu-id="b7766-131">**지연 로드**는 페이지의 메인 섹션에 표시되지 않는 웹 파트의 지연 로딩 시간을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b7766-131">**Lazy Load** shows the time for deferred loading of web parts not seen in the main section of the page</span></span>
- <span data-ttu-id="b7766-132">**이니트**는 웹 파트 초기화에 소요되는 시간을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b7766-132">**Init** shows the time taken for web part initialization</span></span>
- <span data-ttu-id="b7766-133">**렌더**는 웹 파트가 결과를 가져와 제공하는 데 걸리는 시간을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="b7766-133">**Render** shows the time taken for the web part to fetch and render results</span></span>

<span data-ttu-id="b7766-134">이 정보는 디자이너 및 개발자가 문제를 해결하는데 도움을 주기 위해 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="b7766-134">This information is provided to help designers and developers troubleshoot issues.</span></span> <span data-ttu-id="b7766-135">이 정보는 디자인 및 개발 팀에 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7766-135">This information should be provided to your design and development team.</span></span>

## <a name="remediate-web-part-performance-issues"></a><span data-ttu-id="b7766-136">웹 파트 성능 문제 해결</span><span class="sxs-lookup"><span data-stu-id="b7766-136">Remediate web part performance issues</span></span>

<span data-ttu-id="b7766-137">**웹 파트가 페이지 로드 시간 결과에 영향을 미칩니다**에 나열된 웹 파트의 성능 문제를 식별하고 해결하려면 이 섹션의 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="b7766-137">Follow the guidance in this section to identify and remediate performance issues with web parts listed in the **Web parts are impacting page load time** results.</span></span>

<span data-ttu-id="b7766-138">웹 파트 성능이 저하되는 세 가지 범주의 원인이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b7766-138">There are three categories of possible causes for poor web part performance.</span></span> <span data-ttu-id="b7766-139">아래의 정보를 사용하여 시나리오에 적용되는 문제를 판단하고 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b7766-139">Use the information below to determine which issues apply to your scenario and remediate them.</span></span>

- <span data-ttu-id="b7766-140">웹 파트 스크립트 크기와 종속성</span><span class="sxs-lookup"><span data-stu-id="b7766-140">Web part script size and dependencies</span></span>
  - <span data-ttu-id="b7766-141">주요 시나리오를 _보기 전용 모드_로 제공하는 초기 스크립트를 최적화합니다.</span><span class="sxs-lookup"><span data-stu-id="b7766-141">Optimize the initial script that renders the mainline scenario for _view mode only_.</span></span>
  - <span data-ttu-id="b7766-142">_가져오기 ()_ 문을 사용하여 낮은 빈도 수의 시나리오와 편집 모드 코드를 (속성 창 등) 이동시켜 분리합니다.</span><span class="sxs-lookup"><span data-stu-id="b7766-142">Move the less frequent scenarios and edit mode code (like the property pane) to separate chunks using the _import()_ statement.</span></span>
  - <span data-ttu-id="b7766-143">_Package.json_ 파일의 종속성을 검토하여 불필요한 코드를 완전히 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="b7766-143">Review dependencies of the _package.json_ file to remove any dead code completely.</span></span> <span data-ttu-id="b7766-144">모든 테스트/빌드 종속성을 devDependencies으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="b7766-144">Move any test/build only dependencies to devDependencies.</span></span>
  - <span data-ttu-id="b7766-145">최적의 정적 리소스 다운로드를 위해서는 Office 365 CDN을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7766-145">Use of the Office 365 CDN is required for optimal static resource download.</span></span> <span data-ttu-id="b7766-146">_Js/css_ 파일에는 공개 CDN 출처의 사용을 선호합니다.</span><span class="sxs-lookup"><span data-stu-id="b7766-146">Public CDN origins are preferable for _js/css_ files.</span></span> <span data-ttu-id="b7766-147">Office 365 CDN을 사용하는 방법에 대한 자세한 내용은 [SharePoint Online를 활용해 Office 365 Content Delivery Network(CDN) 사용하기](use-office-365-cdn-with-spo.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="b7766-147">For more information about using the Office 365 CDN, see [Use the Office 365 Content Delivery Network (CDN) with SharePoint Online](use-office-365-cdn-with-spo.md).</span></span>
  - <span data-ttu-id="b7766-148">SharePoint 프레임워크 (SPFx)의 일부로 제공되는_반응_ 및 _패브릭 가져오기_와 같은 프레임워크를 재사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b7766-148">Reuse frameworks like _React_ and _Fabric imports_ that come as part of the SharePoint Framework (SPFx).</span></span> <span data-ttu-id="b7766-149">자세한 내용은 [SharePoint 프레임워크 개요](https://docs.microsoft.com/sharepoint/dev/spfx/sharepoint-framework-overview)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b7766-149">For more information, see [Overview of the SharePoint Framework](https://docs.microsoft.com/sharepoint/dev/spfx/sharepoint-framework-overview).</span></span>
  - <span data-ttu-id="b7766-150">최신 버전의 SharePoint 프레임워크를 사용하고 있는지 확인하고 새 버전이 가용하게 되면 업그레이드합니다.</span><span class="sxs-lookup"><span data-stu-id="b7766-150">Ensure that you are using the latest version of the SharePoint Framework, and upgrade to new versions as they become available.</span></span>
- <span data-ttu-id="b7766-151">데이터 페칭/캐싱</span><span class="sxs-lookup"><span data-stu-id="b7766-151">Data fetching/caching</span></span>
  - <span data-ttu-id="b7766-152">웹 파트에서 표시할 데이터를 가져오기 위해 추가 서버 호출을 사용하는 경우에는 해당 서버 API가 빠르고 클라이언트 쪽 캐싱을 구현하는지 확인합니다.(규모가 큰 세트에는 _localStorage_ 혹은 _IndexDB_사용 등)</span><span class="sxs-lookup"><span data-stu-id="b7766-152">If the web part relies on extra server calls to fetch data for display, ensure those server APIs are fast and/or implement client side caching (such as using _localStorage_ or _IndexDB_ for larger sets).</span></span>
  - <span data-ttu-id="b7766-153">중요한 데이터를 제공하는데 여러 번의 호출이 필요한 경우 서버에서 일괄 처리를 하거나 요청을 단일 호출로 통합하는 다른 방법을 고려합니다.</span><span class="sxs-lookup"><span data-stu-id="b7766-153">If multiple calls are required to render critical data, consider batching on the server or other methods of consolidating requests to a single call.</span></span>
  - <span data-ttu-id="b7766-154">또는 일부 데이터 요소에 더 느린 API가 필요하지만 초기 렌더링이 중요하지 않은 경우에는 이를 중요한 데이터가 제공된 후 실행되는 별도의 호출로 분리합니다.</span><span class="sxs-lookup"><span data-stu-id="b7766-154">Alternatively, if some elements of data require a slower API, but are not critical to initial rendering, decouple these to a separate call that is executed after critical data is rendered.</span></span>
  - <span data-ttu-id="b7766-155">여러 파트에서 같은 데이터를 사용하는 경우에는 공통 데이터 레이어를 활용하여 중복되는 호출을 방지합니다.</span><span class="sxs-lookup"><span data-stu-id="b7766-155">If multiple parts use the same data, utilize a common data layer to avoid duplicate calls.</span></span>
- <span data-ttu-id="b7766-156">렌더링 시간</span><span class="sxs-lookup"><span data-stu-id="b7766-156">Rendering time</span></span>
  - <span data-ttu-id="b7766-157">이미지 및 비디오와 같은 모든 미디어 소스는 컨테이너, 장치 및/또는 네트워크의 제한사항에 맞게 크기가 조정되어 불필요한 대규모 자산이 다운로드되지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7766-157">Any media sources like images and videos should be sized to the limits of the container, device and/or network to avoid downloading unnecessary large assets.</span></span> <span data-ttu-id="b7766-158">콘텐츠 종속성에 대한 자세한 내용은 [SharePoint Online을 활용해 Office 365 Content Delivery Network(CDN) 사용하기](use-office-365-cdn-with-spo.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="b7766-158">For more information about content dependencies, see [Use the Office 365 Content Delivery Network (CDN) with SharePoint Online](use-office-365-cdn-with-spo.md).</span></span>
  - <span data-ttu-id="b7766-159">리플로우, 복잡한 CSS 규칙이나 복잡한 애니메이션을 발생시키는 API 호출을 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b7766-159">Avoid API calls that cause re-flow, complex CSS rules or complicated animations.</span></span> <span data-ttu-id="b7766-160">자세한 내용은 [브라우저 리플로우 최소화](https://developers.google.com/speed/docs/insights/browser-reflow)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b7766-160">For more information, see [Minimizing browser reflow](https://developers.google.com/speed/docs/insights/browser-reflow).</span></span>
  - <span data-ttu-id="b7766-161">일련의 장기 실행 작업을 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b7766-161">Avoid use of chained long running tasks.</span></span> <span data-ttu-id="b7766-162">대신 장기 실행 작업은 개별적 큐로 분리합니다.</span><span class="sxs-lookup"><span data-stu-id="b7766-162">Instead, break long running tasks apart into separate queues.</span></span> <span data-ttu-id="b7766-163">자세한 내용은 [JavaScript 실행 최적화](https://developers.google.com/web/fundamentals/performance/rendering/optimize-javascript-execution)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b7766-163">For more information, see [Optimize JavaScript Execution](https://developers.google.com/web/fundamentals/performance/rendering/optimize-javascript-execution).</span></span>
  - <span data-ttu-id="b7766-164">프레임의 생략이나 끊김현상을 방지하기 위해 비동기식 렌더링 미디어나 시각적 요소에는 해당 공간을 비축해둡니다. (_jank_로도 알려짐)</span><span class="sxs-lookup"><span data-stu-id="b7766-164">Reserve corresponding space for asynchronously rendering media or visual elements to avoid skipped frames and stuttering (also known as _jank_).</span></span>
  - <span data-ttu-id="b7766-165">특정 브라우저가 렌더링에 사용되는 기능을 지원 하지 않는 경우 polyfill을 로드하거나 종속 코드의 실행을 제외합니다.</span><span class="sxs-lookup"><span data-stu-id="b7766-165">If a certain browser doesn't support a feature used in rendering, either load a polyfill or exclude running dependent code.</span></span> <span data-ttu-id="b7766-166">기능이 중요하지 않은 경우 메모리 유출을 방지하기 위해 이벤트 핸들러 등의 리소스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="b7766-166">If the feature is not critical, dispose resources such as event handlers to avoid memory leaks.</span></span>

<span data-ttu-id="b7766-167">성능 문제를 개선하기 위해 페이지를 수정하기 전에 분석 결과에 페이지 로드 시간을 기록해 둡니다.</span><span class="sxs-lookup"><span data-stu-id="b7766-167">Before you make page revisions to remediate performance issues, make a note of the page load time in the analysis results.</span></span> <span data-ttu-id="b7766-168">수정 후에 다시 도구를 실행하여 새 결과가 기준선 표준에 포함되는지 확인하고 새 페이지 로드 시간을 확인하여 개선이 되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b7766-168">Run the tool again after your revision to see if the new result is within the baseline standard, and check the new page load time to see if there was an improvement.</span></span>

![페이지 로드 시간 결과](media/modern-portal-optimization/pagediag-page-load-time.png)

>[!NOTE]
><span data-ttu-id="b7766-170">페이지 로드 시간은 네트워크 부하, 하루 중 시간 및 기타 일시적인 조건과 같은 다양한 요인에 따라 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b7766-170">Page load time can vary based on a variety of factors such as network load, time of day, and other transient conditions.</span></span> <span data-ttu-id="b7766-171">결과의 평균을 내는데 도움이 되도록 수정을 하기 전과 후에 페이지 로드 시간을 몇 번 정도 테스트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7766-171">You should test page load time a few times before and after making changes to help you average the results.</span></span>

## <a name="related-topics"></a><span data-ttu-id="b7766-172">관련 항목</span><span class="sxs-lookup"><span data-stu-id="b7766-172">Related topics</span></span>

[<span data-ttu-id="b7766-173">SharePoint Online 성능 조정</span><span class="sxs-lookup"><span data-stu-id="b7766-173">Tune SharePoint Online performance</span></span>](tune-sharepoint-online-performance.md)

[<span data-ttu-id="b7766-174">Office 365 성능 조정</span><span class="sxs-lookup"><span data-stu-id="b7766-174">Tune Office 365 performance</span></span>](tune-office-365-performance.md)

[<span data-ttu-id="b7766-175">최신 SharePoint 환경의 성능</span><span class="sxs-lookup"><span data-stu-id="b7766-175">Performance in the modern SharePoint experience</span></span>](https://docs.microsoft.com/sharepoint/modern-experience-performance)

[<span data-ttu-id="b7766-176">콘텐츠 배달 네트워크</span><span class="sxs-lookup"><span data-stu-id="b7766-176">Content delivery networks</span></span>](content-delivery-networks.md)

[<span data-ttu-id="b7766-177">sharepoint Online을 활용해 Office 365 콘텐츠 배달 네트워크(CDN) 사용하기</span><span class="sxs-lookup"><span data-stu-id="b7766-177">Use the Office 365 Content Delivery Network (CDN) with SharePoint Online</span></span>](use-office-365-cdn-with-spo.md)
