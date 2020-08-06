---
title: SharePoint Online 최신 사이트 페이지에서 이미지 최적화
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 03/11/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
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
description: SharePoint Online 최신 사이트 페이지에서 이미지를 최적화하는 방법을 알아봅니다.
ms.openlocfilehash: b5b1af0e78b3be7f84b1ee83048010feabddf82e
ms.sourcegitcommit: a9021ba0800ffc0da21cf2c4da67ab1da2d97099
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "46571131"
---
# <a name="optimize-images-in-sharepoint-online-modern-site-pages"></a><span data-ttu-id="4a7b5-103">SharePoint Online 최신 사이트 페이지에서 이미지 최적화</span><span class="sxs-lookup"><span data-stu-id="4a7b5-103">Optimize images in SharePoint Online modern site pages</span></span>

<span data-ttu-id="4a7b5-104">이 문서는 SharePoint Online 최신 사이트 페이지에서 이미지를 최적화하는 방법의 이해를 돕습니다.</span><span class="sxs-lookup"><span data-stu-id="4a7b5-104">This article will help you understand how to optimize images in SharePoint Online modern site pages.</span></span>

<span data-ttu-id="4a7b5-105">클래식 게시 사이트에서 이미지 최적화에 대한 자세한 내용은 [SharePoint Online용 이미지 최적화](image-optimization-for-sharepoint-online.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4a7b5-105">For information about optimizing images in classic publishing sites, see [Image optimization for SharePoint Online](image-optimization-for-sharepoint-online.md)..</span></span>

>[!NOTE]
><span data-ttu-id="4a7b5-106">SharePoint Online 최신 포털의 성능에 대한 자세한 내용은 [최신 SharePoint 환경의 성능](https://docs.microsoft.com/sharepoint/modern-experience-performance)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4a7b5-106">For more information about performance in SharePoint Online modern portals, see [Performance in the modern SharePoint experience](https://docs.microsoft.com/sharepoint/modern-experience-performance).</span></span>

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-image-optimization"></a><span data-ttu-id="4a7b5-107">SharePoint용 페이지 진단 도구를 사용한 이미지 최적화 분석</span><span class="sxs-lookup"><span data-stu-id="4a7b5-107">Use the Page Diagnostics for SharePoint tool to analyze image optimization</span></span>

<span data-ttu-id="4a7b5-108">SharePoint용 페이지 진단 도구는 새 Microsoft Edge에 대한 브라우저 확장입니다. (SharePoint Online 최신 포털 및 클래식 게시 사이트 페이지를 분석하는 https://www.microsoft.com/edge) 및 Chrome 브라우저)</span><span class="sxs-lookup"><span data-stu-id="4a7b5-108">The Page Diagnostics for SharePoint tool is a browser extension for the new Microsoft Edge (https://www.microsoft.com/edge) and Chrome browsers that analyzes both SharePoint Online modern portal and classic publishing site pages.</span></span> <span data-ttu-id="4a7b5-109">이 도구는 정의된 성능 기준의 집합 대비 페이지 수행 방식을 보여주는 분석된 각 페이지에 대한 보고서를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4a7b5-109">The tool provides a report for each analyzed page showing how the page performs against a defined set of performance criteria.</span></span> <span data-ttu-id="4a7b5-110">Sharepoint용 페이지 진단 도구에 대해 배우고 설치하려면[Sharepoint Online에 페이지 진단 도구 사용](page-diagnostics-for-spo.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4a7b5-110">To install and learn about the Page Diagnostics for SharePoint tool, visit [Use the Page Diagnostics tool for SharePoint Online](page-diagnostics-for-spo.md).</span></span>

>[!NOTE]
><span data-ttu-id="4a7b5-111">페이지 진단 도구는 SharePoint Online에서만 사용할 수 있으며 SharePoint 시스템 페이지에서는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4a7b5-111">The Page Diagnostics tool only works for SharePoint Online, and cannot be used on a SharePoint system page.</span></span>

<span data-ttu-id="4a7b5-112">SharePoint용 페이지 진단 도구를 사용하여 SharePoint 최신 사이트를 분석할 때 _진단 테스트_ 창에서 대용량 이미지에 대한 정보를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a7b5-112">When you analyze a SharePoint modern site with the Page Diagnostics for SharePoint tool, you can see information about large images in the _Diagnostic tests_ pane.</span></span>

<span data-ttu-id="4a7b5-113">가능한 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4a7b5-113">Possible results include:</span></span>

- <span data-ttu-id="4a7b5-114">**주의 필요** (빨간색): 페이지에 크기가 300KB 이상인 이미지가 **하나 이상** 포함되어 있음</span><span class="sxs-lookup"><span data-stu-id="4a7b5-114">**Attention required** (red): The page contains **one or more** images over 300KB in size</span></span>
- <span data-ttu-id="4a7b5-115">**조치 필요하지 않음** (녹색): 페이지에 크기가 300KB 이상인 이미지가 포함되어 있지 않음</span><span class="sxs-lookup"><span data-stu-id="4a7b5-115">**No action required** (green): The page contains no images over 300KB in size</span></span>

<span data-ttu-id="4a7b5-116">**대용량 이미지 검색** 결과가 **주의 필요** 구역에 나타나면 결과를 클릭하여 추가 세부 정보를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a7b5-116">If the **Large images detected** result appears in the **Attention required** section of the results, you can click the result to see additional details.</span></span>

![페이지 진단 도구 결과](media/modern-portal-optimization/pagediag-large-images.png)

## <a name="remediate-large-image-issues"></a><span data-ttu-id="4a7b5-118">대용량 이미지 문제 수정</span><span class="sxs-lookup"><span data-stu-id="4a7b5-118">Remediate large image issues</span></span>

<span data-ttu-id="4a7b5-119">페이지에 크기가 300KB 이상인 이미지를 포함하는 경우 **대용량 이미지 검색 결과**를 선택하여 대용량 이미지를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="4a7b5-119">If a page contains images over 300KB in size, select the **Large images detected** result to see which images are too large.</span></span> <span data-ttu-id="4a7b5-120">최신 SharePoint Online 페이지에서 이미지 변환은 브라우저 창의 크기와 클라이언트 모니터의 해상도에 따라 자동으로 제공되고 크기가 조정됩니다.</span><span class="sxs-lookup"><span data-stu-id="4a7b5-120">In modern SharePoint Online pages, renditions of images are automatically provided and sized depending on the size of the browser window and the resolution of the client monitor.</span></span> <span data-ttu-id="4a7b5-121">SharePoint Online에 업로드하기 전에 웹 사용을 위해서는 항상 이미지를 최적화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4a7b5-121">You should always optimize images for web use prior to upload to SharePoint Online.</span></span> <span data-ttu-id="4a7b5-122">대용량 이미지의 크기와 해상도가 자동으로 줄어들며 예기치 않은 렌더링 특성이 생길 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a7b5-122">Very large images will be automatically reduced in size and resolution which can result in unexpected rendering characteristics.</span></span>

<span data-ttu-id="4a7b5-123">성능 문제 개선을 위해 페이지를 수정하기 전에 분석 결과에 페이지 로드 시간을 기록해 둡니다.</span><span class="sxs-lookup"><span data-stu-id="4a7b5-123">Before you make page revisions to remediate performance issues, make a note of the page load time in the analysis results.</span></span> <span data-ttu-id="4a7b5-124">수정 후에 다시 도구를 실행하여 새 결과가 기준선 표준에 포함되는지 확인하고 새 페이지 로드 시간을 확인하여 개선이 되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="4a7b5-124">Run the tool again after your revision to see if the new result is within the baseline standard, and check the new page load time to see if there was an improvement.</span></span>

![페이지 로드 시간 결과](media/modern-portal-optimization/pagediag-page-load-time.png)

>[!NOTE]
><span data-ttu-id="4a7b5-126">페이지 로드 시간은 네트워크 부하, 하루 중 시간 및 기타 일시적인 조건과 같은 다양한 요인에 따라 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a7b5-126">Page load time can vary based on a variety of factors such as network load, time of day, and other transient conditions.</span></span> <span data-ttu-id="4a7b5-127">결과의 평균을 내는데 도움이 되도록 수정을 하기 전과 후에 페이지 로드 시간을 몇 번 정도 테스트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4a7b5-127">You should test page load time a few times before and after making changes to help you average the results.</span></span>

## <a name="related-topics"></a><span data-ttu-id="4a7b5-128">관련 항목</span><span class="sxs-lookup"><span data-stu-id="4a7b5-128">Related topics</span></span>

[<span data-ttu-id="4a7b5-129">SharePoint Online 성능 조정</span><span class="sxs-lookup"><span data-stu-id="4a7b5-129">Tune SharePoint Online performance</span></span>](tune-sharepoint-online-performance.md)

[<span data-ttu-id="4a7b5-130">Office 365 성능 조정</span><span class="sxs-lookup"><span data-stu-id="4a7b5-130">Tune Office 365 performance</span></span>](tune-office-365-performance.md)

[<span data-ttu-id="4a7b5-131">최신 SharePoint 환경의 성능</span><span class="sxs-lookup"><span data-stu-id="4a7b5-131">Performance in the modern SharePoint experience</span></span>](https://docs.microsoft.com/sharepoint/modern-experience-performance)

[<span data-ttu-id="4a7b5-132">콘텐츠 배달 네트워크</span><span class="sxs-lookup"><span data-stu-id="4a7b5-132">Content delivery networks</span></span>](content-delivery-networks.md)

[<span data-ttu-id="4a7b5-133">sharepoint Online을 활용해 Office 365 콘텐츠 배달 네트워크(CDN) 사용하기</span><span class="sxs-lookup"><span data-stu-id="4a7b5-133">Use the Office 365 Content Delivery Network (CDN) with SharePoint Online</span></span>](use-office-365-cdn-with-spo.md)
