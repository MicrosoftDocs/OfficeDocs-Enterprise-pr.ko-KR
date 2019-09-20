---
title: SharePoint Online 최신 사이트 페이지에서 페이지부하 최적화
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
description: SharePoint Online 최신 사이트 페이지에서 페이지 부하를 최적화하는 방법을 학습하세요.
ms.openlocfilehash: 5e2231468363f58faeac1d7b21e06cd4fa790cf8
ms.sourcegitcommit: c7764503422922cb333b05d54e8ebbdb894df2f9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2019
ms.locfileid: "37028215"
---
# <a name="optimize-page-weight-in-sharepoint-online-modern-site-pages"></a><span data-ttu-id="36e4b-103">SharePoint Online 최신 사이트 페이지에서 페이지부하 최적화</span><span class="sxs-lookup"><span data-stu-id="36e4b-103">Optimize page weight in SharePoint Online modern site pages</span></span>

<span data-ttu-id="36e4b-104">SharePoint Online 최신 사이트 페이지에는 이미지, 텍스트, 탐색/명령 모음 아래의 콘텐츠 영역에 있는 개체와 페이지의 프레임 워크를 구성하는 기타 HTML 코드를 포함하여 페이지의 페이지 콘텐츠를 제공하는데 필요한 연재된 코드가 포함되어 있습니다.  </span><span class="sxs-lookup"><span data-stu-id="36e4b-104">SharePoint Online modern site pages contain serialized code that is required to render page content of the page, including images, text, objects in the content area underneath navigation/command bars and other HTML code that forms the framework of the page.</span></span> <span data-ttu-id="36e4b-105">페이지 부하는 이 HTML 코드에 대한 측정치며 페이지 로드 시간을 최적화하기 위해 제한되어 야 합니다.</span><span class="sxs-lookup"><span data-stu-id="36e4b-105">Page weight is a measurement of this HTML code, and should be limited to ensure optimal page load times.</span></span>

<span data-ttu-id="36e4b-106">이 문서는 최신 사이트 페이지에서 페이지 부하를 줄이는 방법을 이해하는데 도움을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="36e4b-106">This article will help you understand how to reduce page weight in your modern site pages.</span></span>

>[!NOTE]
><span data-ttu-id="36e4b-107">SharePoint Online 최신 포털의 성능에 대한 자세한 내용은 [최신 SharePoint 환경의 성능](https://docs.microsoft.com/ko-KR/sharepoint/modern-experience-performance)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="36e4b-107">For more information about performance in SharePoint Online modern portals, see [Performance in the modern SharePoint experience](https://docs.microsoft.com/ko-KR/sharepoint/modern-experience-performance).</span></span>

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-page-weight"></a><span data-ttu-id="36e4b-108">SharePoint 용 페이지 진단 도구를 사용한 페이지 부하 분석</span><span class="sxs-lookup"><span data-stu-id="36e4b-108">Use the Page Diagnostics for SharePoint tool to analyze page weight</span></span>

<span data-ttu-id="36e4b-109">**Sharepoint 페이지 진단 도구**는 Chrome 및 [ Microsoft Edge 버전 77 이상](https://www.microsoftedgeinsider.com/en-us/download?form=MI13E8&OCID=MI13E8)의 브라우저 확장으로서 Sharepoint 최신 및 클래식 게시 사이트 페이지를 분석하는데 사용할 수 있습니다. </span><span class="sxs-lookup"><span data-stu-id="36e4b-109">The **Page Diagnostics for SharePoint tool** is a browser extension for Chrome and [Microsoft Edge version 77 or later](https://www.microsoftedgeinsider.com/en-us/download?form=MI13E8&OCID=MI13E8) you can use to analyze SharePoint both modern and classic publishing site pages.</span></span> <span data-ttu-id="36e4b-110">이 도구는 정의된 성능 기준의 집합 대비 페이지 수행 방식을 보여주는 분석된 각 페이지에 대한 보고서를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="36e4b-110">The tool provides a report for each analyzed page showing how the page performs against a defined set of performance criteria.</span></span> <span data-ttu-id="36e4b-111">Sharepoint용 페이지 진단 도구에 대해 배우고 설치하려면[Sharepoint Online에 페이지 진단 도구 사용](page-diagnostics-for-spo.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="36e4b-111">To install and learn about the Page Diagnostics for SharePoint tool, visit [Use the Page Diagnostics tool for SharePoint Online](page-diagnostics-for-spo.md).</span></span>

<span data-ttu-id="36e4b-112">Sharepoint용 페이지 진단 도구를 사용하여 Sharepoint 사이트 페이지를 분석 시 _진단 테스트_ 창의 **500KB 미만의 페이지 부하** 결과에서 페이지에 대한 정보를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36e4b-112">When you analyze a SharePoint site page with the Page Diagnostics for SharePoint tool, you can see information about page in the **Page weight under 500KB** result of the _Diagnostic tests_ pane.</span></span> <span data-ttu-id="36e4b-113">페이지 부하가 기준선 값 아래에 있으면 결과는 녹색이 되고, 페이지 부하가 기준선 값을 초과하는 경우 빨간색으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="36e4b-113">The result will appear in green if the page weight is under the baseline value, and red if the page weight exceeds the baseline value.</span></span>

<span data-ttu-id="36e4b-114">잠정 결과는 다음과 같습니다:</span><span class="sxs-lookup"><span data-stu-id="36e4b-114">Possible results include:</span></span>

- <span data-ttu-id="36e4b-115">**주의 필요** (빨간색): 페이지 부하가 500KB를 초과</span><span class="sxs-lookup"><span data-stu-id="36e4b-115">**Attention required** (red): Page weight exceeds 500KB</span></span>
- <span data-ttu-id="36e4b-116">**조치가 필요하지 않음** (녹색): 페이지 부하가 500KB 미만</span><span class="sxs-lookup"><span data-stu-id="36e4b-116">**No action required** (green): Page weight is under 500KB</span></span>

<span data-ttu-id="36e4b-117">페이지 부하가 500KB 미만\*\* 결과가 주의 필요\*\* 섹션에 표시되는 경우 클릭하여 세부 정보를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36e4b-117">If the **Page weight under 500KB** result appears in the **Attention required** section, you can click the result for details.</span></span>

![SharePoint 결과에 대한 요청](media/modern-portal-optimization/pagediag-page-weight.png)

## <a name="remediate-page-weight-issues"></a><span data-ttu-id="36e4b-119">페이지 부하 문제 수정</span><span class="sxs-lookup"><span data-stu-id="36e4b-119">Remediate page weight issues</span></span>

<span data-ttu-id="36e4b-120">페이지 부하가 500KB를 초과하는 경우 웹 파트 수를 줄이고 페이지 콘텐츠를 적절한 수준으로 제한하여 전반적인 페이지 로드 시간을 개선할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36e4b-120">If page weight exceeds 500KB, you can improve overall page load time by reducing the number of web parts and limiting page content to an appropriate degree.</span></span>

<span data-ttu-id="36e4b-121">페이지 부하 줄이기에 대한 일반적인 지침은 다음과 같습니다:</span><span class="sxs-lookup"><span data-stu-id="36e4b-121">General guidance for reducing page weight includes:</span></span>

- <span data-ttu-id="36e4b-122">페이지 콘텐츠를 적정 분량으로 제한하고 관련 콘텐츠는 여러 페이지를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="36e4b-122">Limit the page content to a reasonable amount and use multiple pages for related content.</span></span>
- <span data-ttu-id="36e4b-123">큰 속성 백이 있는 웹 파트의 사용을 최소화합니다.</span><span class="sxs-lookup"><span data-stu-id="36e4b-123">Minimize the use of web parts that have large property bags.</span></span>
- <span data-ttu-id="36e4b-124">가능하면 비 대화형 롤업 보기를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="36e4b-124">Use non-interactive rollup views when possible.</span></span>
- <span data-ttu-id="36e4b-125">압축 이미지 형식을 사용하여 이미지 크기를 적절하게 조정하고 이미지가 CDN에서 다운로드 되는지 확인하여 이미지 크기를 최적화합니다.</span><span class="sxs-lookup"><span data-stu-id="36e4b-125">Optimize image sizes by sizing images appropriately, using compressed image formats and ensuring that they are downloaded from a CDN.</span></span>

<span data-ttu-id="36e4b-126">다음의 문서에서 페이지 부하를 제한하는 방법에 대한 추가 지침을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36e4b-126">You can find additional guidance for limiting page weight in the following article:</span></span>

- [<span data-ttu-id="36e4b-127">SharePoint에서 페이지 성능 최적화</span><span class="sxs-lookup"><span data-stu-id="36e4b-127">Optimize page performance in SharePoint</span></span>](https://docs.microsoft.com/ko-KR/sharepoint/dev/general-development/optimize-page-performance-in-sharepoint)

<span data-ttu-id="36e4b-128">성능 문제를 개선하기 위해 페이지를 수정하기 전에 분석 결과에 페이지 로드 시간을 기록해 둡니다.</span><span class="sxs-lookup"><span data-stu-id="36e4b-128">Before you make page revisions to remediate performance issues, make a note of the page load time in the analysis results.</span></span> <span data-ttu-id="36e4b-129">수정 후에 다시 도구를 실행하여 새 결과가 기준선 표준에 포함되는지 확인하고 새 페이지 로드 시간을 확인하여 개선이 되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="36e4b-129">Run the tool again after your revision to see if the new result is within the baseline standard, and check the new page load time to see if there was an improvement.</span></span>

![페이지 로드 시간 결과](media/modern-portal-optimization/pagediag-page-load-time.png)

>[!NOTE]
><span data-ttu-id="36e4b-131">페이지 로드 시간은 네트워크 부하, 하루 중 시간 및 기타 일시적인 조건과 같은 다양한 요인에 따라 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36e4b-131">Page load time can vary based on a variety of factors such as network load, time of day, and other transient conditions.</span></span> <span data-ttu-id="36e4b-132">결과의 평균을 내는데 도움이 되도록 수정을 하기 전과 후에 페이지 로드 시간을 몇 번 정도 테스트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="36e4b-132">You should test page load time a few times before and after making changes to help you average the results.</span></span>

## <a name="related-topics"></a><span data-ttu-id="36e4b-133">관련 항목</span><span class="sxs-lookup"><span data-stu-id="36e4b-133">Related topics</span></span>

[<span data-ttu-id="36e4b-134">SharePoint Online 성능 조정</span><span class="sxs-lookup"><span data-stu-id="36e4b-134">Tune SharePoint Online performance</span></span>](tune-sharepoint-online-performance.md)

[<span data-ttu-id="36e4b-135">Office 365 성능 조정</span><span class="sxs-lookup"><span data-stu-id="36e4b-135">Tune Office 365 performance</span></span>](tune-office-365-performance.md)

[<span data-ttu-id="36e4b-136">최신 SharePoint 환경의 성능</span><span class="sxs-lookup"><span data-stu-id="36e4b-136">Performance in the modern SharePoint experience</span></span>](https://docs.microsoft.com/ko-KR/sharepoint/modern-experience-performance.md)

[<span data-ttu-id="36e4b-137">콘텐츠 전달 네트워크</span><span class="sxs-lookup"><span data-stu-id="36e4b-137">Content delivery networks</span></span>](content-delivery-networks.md)

[<span data-ttu-id="36e4b-138">sharepoint Online을 활용해 Office 365 콘텐츠 배달 네트워크(CDN) 사용하기</span><span class="sxs-lookup"><span data-stu-id="36e4b-138">Use the Office 365 Content Delivery Network (CDN) with SharePoint Online</span></span>](use-office-365-cdn-with-spo.md)
