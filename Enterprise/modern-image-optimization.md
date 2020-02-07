---
title: SharePoint Online 최신 사이트 페이지에서 이미지 최적화
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
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.reviewer: sstewart
search.appverid:
- MET150
description: SharePoint Online 최신 사이트 페이지에서 이미지를 최적화하는 방법을 알아봅니다.
ms.openlocfilehash: b1bb8bab7ee9d5f0972a476e37c35e8c14748bfb
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843749"
---
# <a name="optimize-images-in-sharepoint-online-modern-site-pages"></a><span data-ttu-id="5d598-103">SharePoint Online 최신 사이트 페이지에서 이미지 최적화</span><span class="sxs-lookup"><span data-stu-id="5d598-103">Optimize images in SharePoint Online modern site pages</span></span>

<span data-ttu-id="5d598-104">이 문서는 SharePoint Online 최신 사이트 페이지에서 이미지를 최적화하는 방법의 이해를 돕습니다.</span><span class="sxs-lookup"><span data-stu-id="5d598-104">This article will help you understand how to optimize images in SharePoint Online modern site pages.</span></span>

<span data-ttu-id="5d598-105">클래식 게시 사이트에서 이미지 최적화에 대한 자세한 내용은 [SharePoint Online용 이미지 최적화](image-optimization-for-sharepoint-online.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5d598-105">For information about optimizing images in classic publishing sites, see [Image optimization for SharePoint Online](image-optimization-for-sharepoint-online.md)..</span></span>

>[!NOTE]
><span data-ttu-id="5d598-106">SharePoint Online 최신 포털의 성능에 대한 자세한 내용은 [최신 SharePoint 환경의 성능](https://docs.microsoft.com/sharepoint/modern-experience-performance)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5d598-106">For more information about performance in SharePoint Online modern portals, see [Performance in the modern SharePoint experience](https://docs.microsoft.com/sharepoint/modern-experience-performance).</span></span>

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-image-optimization"></a><span data-ttu-id="5d598-107">SharePoint용 페이지 진단 도구를 사용한 이미지 최적화 분석</span><span class="sxs-lookup"><span data-stu-id="5d598-107">Use the Page Diagnostics for SharePoint tool to analyze image optimization</span></span>

<span data-ttu-id="5d598-108">**Sharepoint용 페이지 진단 도구**는 Chrome 및 [ Microsoft Edge 버전 77 이상](https://www.microsoftedgeinsider.com/download?form=MI13E8&OCID=MI13E8)의 브라우저 확장으로서 Sharepoint 최신 및 클래식 게시 사이트 페이지를 분석하는 데 사용할 수 있습니다. </span><span class="sxs-lookup"><span data-stu-id="5d598-108">The **Page Diagnostics for SharePoint tool** is a browser extension for Chrome and [Microsoft Edge version 77 or later](https://www.microsoftedgeinsider.com/download?form=MI13E8&OCID=MI13E8) you can use to analyze SharePoint both modern and classic publishing site pages.</span></span> <span data-ttu-id="5d598-109">이 도구는 정의된 성능 기준의 집합 대비 페이지 수행 방식을 보여주는 분석된 각 페이지에 대한 보고서를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="5d598-109">The tool provides a report for each analyzed page showing how the page performs against a defined set of performance criteria.</span></span> <span data-ttu-id="5d598-110">SharePoint용 페이지 진단 도구를 설치하고 알아보려면[Sharepoint Online용 페이지 진단 도구 사용](page-diagnostics-for-spo.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5d598-110">To install and learn about the Page Diagnostics for SharePoint tool, visit [Use the Page Diagnostics tool for SharePoint Online](page-diagnostics-for-spo.md).</span></span>

<span data-ttu-id="5d598-111">SharePoint용 페이지 진단 도구를 사용하여 SharePoint 최신 사이트를 분석할 때 _진단 테스트_ 창에서 대용량 이미지에 대한 정보를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d598-111">When you analyze a SharePoint modern site with the Page Diagnostics for SharePoint tool, you can see information about large images in the _Diagnostic tests_ pane.</span></span>

<span data-ttu-id="5d598-112">가능한 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="5d598-112">Possible results include:</span></span>

- <span data-ttu-id="5d598-113">**주의 필요** (빨간색): 페이지에 크기가 300KB 이상인 이미지가 **하나 이상** 포함되어 있음</span><span class="sxs-lookup"><span data-stu-id="5d598-113">**Attention required** (red): The page contains **one or more** images over 300KB in size</span></span>
- <span data-ttu-id="5d598-114">**조치 필요하지 않음** (녹색): 페이지에 크기가 300KB 이상인 이미지가 포함되어 있지 않음</span><span class="sxs-lookup"><span data-stu-id="5d598-114">**No action required** (green): The page contains no images over 300KB in size</span></span>

<span data-ttu-id="5d598-115">**대용량 이미지 검색** 결과가 **주의 필요** 구역에 나타나면 결과를 클릭하여 추가 세부 정보를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d598-115">If the **Large images detected** result appears in the **Attention required** section of the results, you can click the result to see additional details.</span></span>

![페이지 진단 도구 결과](media/modern-portal-optimization/pagediag-large-images.png)

## <a name="remediate-large-image-issues"></a><span data-ttu-id="5d598-117">대용량 이미지 문제 수정</span><span class="sxs-lookup"><span data-stu-id="5d598-117">Remediate large image issues</span></span>

<span data-ttu-id="5d598-118">페이지에 크기가 300KB 이상인 이미지를 포함하는 경우 **대용량 이미지 검색 결과**를 선택하여 대용량 이미지를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="5d598-118">If a page contains images over 300KB in size, select the **Large images detected** result to see which images are too large.</span></span> <span data-ttu-id="5d598-119">최신 SharePoint Online 페이지에서 이미지 변환은 브라우저 창의 크기와 클라이언트 모니터의 해상도에 따라 자동으로 제공되고 크기가 조정됩니다.</span><span class="sxs-lookup"><span data-stu-id="5d598-119">In modern SharePoint Online pages, renditions of images are automatically provided and sized depending on the size of the browser window and the resolution of the client monitor.</span></span> <span data-ttu-id="5d598-120">SharePoint Online에 업로드하기 전에 웹 사용을 위해서는 항상 이미지를 최적화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5d598-120">You should always optimize images for web use prior to upload to SharePoint Online.</span></span> <span data-ttu-id="5d598-121">대용량 이미지의 크기와 해상도가 자동으로 줄어들며 예기치 않은 렌더링 특성이 생길 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d598-121">Very large images will be automatically reduced in size and resolution which can result in unexpected rendering characteristics.</span></span>

<span data-ttu-id="5d598-122">성능 문제 개선을 위해 페이지를 수정하기 전에 분석 결과에 페이지 로드 시간을 기록해 둡니다.</span><span class="sxs-lookup"><span data-stu-id="5d598-122">Before you make page revisions to remediate performance issues, make a note of the page load time in the analysis results.</span></span> <span data-ttu-id="5d598-123">수정 후에 다시 도구를 실행하여 새 결과가 기준선 표준에 포함되는지 확인하고 새 페이지 로드 시간을 확인하여 개선이 되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="5d598-123">Run the tool again after your revision to see if the new result is within the baseline standard, and check the new page load time to see if there was an improvement.</span></span>

![페이지 로드 시간 결과](media/modern-portal-optimization/pagediag-page-load-time.png)

>[!NOTE]
><span data-ttu-id="5d598-125">페이지 로드 시간은 네트워크 부하, 하루 중 시간 및 기타 일시적인 조건과 같은 다양한 요인에 따라 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d598-125">Page load time can vary based on a variety of factors such as network load, time of day, and other transient conditions.</span></span> <span data-ttu-id="5d598-126">결과의 평균을 내는데 도움이 되도록 수정을 하기 전과 후에 페이지 로드 시간을 몇 번 정도 테스트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5d598-126">You should test page load time a few times before and after making changes to help you average the results.</span></span>

## <a name="related-topics"></a><span data-ttu-id="5d598-127">관련 항목</span><span class="sxs-lookup"><span data-stu-id="5d598-127">Related topics</span></span>

[<span data-ttu-id="5d598-128">SharePoint Online 성능 조정</span><span class="sxs-lookup"><span data-stu-id="5d598-128">Tune SharePoint Online performance</span></span>](tune-sharepoint-online-performance.md)

[<span data-ttu-id="5d598-129">Office 365 성능 조정</span><span class="sxs-lookup"><span data-stu-id="5d598-129">Tune Office 365 performance</span></span>](tune-office-365-performance.md)

[<span data-ttu-id="5d598-130">최신 SharePoint 환경의 성능</span><span class="sxs-lookup"><span data-stu-id="5d598-130">Performance in the modern SharePoint experience</span></span>](https://docs.microsoft.com/sharepoint/modern-experience-performance)

[<span data-ttu-id="5d598-131">콘텐츠 배달 네트워크</span><span class="sxs-lookup"><span data-stu-id="5d598-131">Content delivery networks</span></span>](content-delivery-networks.md)

[<span data-ttu-id="5d598-132">sharepoint Online을 활용해 Office 365 콘텐츠 배달 네트워크(CDN) 사용하기</span><span class="sxs-lookup"><span data-stu-id="5d598-132">Use the Office 365 Content Delivery Network (CDN) with SharePoint Online</span></span>](use-office-365-cdn-with-spo.md)
