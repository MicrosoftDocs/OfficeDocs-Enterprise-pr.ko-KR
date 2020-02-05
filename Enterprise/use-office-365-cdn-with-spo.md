---
title: sharepoint Online을 활용해 Office 365 콘텐츠 배달 네트워크(CDN) 사용하기
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/10/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: bebb285f-1d54-4f79-90a5-94985afc6af8
description: Office 365 CDN (콘텐츠 배달 네트워크)을 사용 하 여 위치에 관계 없이 모든 사용자에 게 SharePoint Online 자산을 빠르게 배달 하는 방법에 대해 설명 하 고 콘텐츠에 액세스 하는 방법을 알아봅니다.
ms.openlocfilehash: 829903919d0a6222b213fe08a610ff6ebe9b985d
ms.sourcegitcommit: 226989f5a6a252e67debf7613bf13aa679a43f92
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/04/2020
ms.locfileid: "41721939"
---
# <a name="use-the-office-365-content-delivery-network-cdn-with-sharepoint-online"></a><span data-ttu-id="83a48-103">sharepoint Online을 활용해 Office 365 콘텐츠 배달 네트워크(CDN) 사용하기</span><span class="sxs-lookup"><span data-stu-id="83a48-103">Use the Office 365 Content Delivery Network (CDN) with SharePoint Online</span></span>

<span data-ttu-id="83a48-104">기본 제공 Office 365 Content Delivery Network(CDN)을 사용하여 정적 자산을 호스팅하여 SharePoint Online 페이지의 성능을 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-104">You can use the built-in Office 365 Content Delivery Network (CDN) to host static assets to provide better performance for your SharePoint Online pages.</span></span> <span data-ttu-id="83a48-105">Office 365 CDN은 정적 자산을 요청하는 브라우저에 더 가깝게 캐싱하여 성능을 향상시켜 다운로드 속도를 높이고 대기 시간을 줄이는 데 기여합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-105">The Office 365 CDN improves performance by caching static assets closer to the browsers requesting them, which helps to speed up downloads and reduce latency.</span></span> <span data-ttu-id="83a48-106">또한 Office 365 CDN은 향상 된 압축 및 HTTP 파이프라이닝을 위해 [http/2 프로토콜](https://en.wikipedia.org/wiki/HTTP/2) 을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-106">Also, the Office 365 CDN uses the [HTTP/2 protocol](https://en.wikipedia.org/wiki/HTTP/2) for improved compression and HTTP pipelining.</span></span> <span data-ttu-id="83a48-107">Office 365 CDN 서비스는 SharePoint Online 구독의 일부로 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-107">The Office 365 CDN service is included as part of your SharePoint Online subscription.</span></span>

> [!NOTE]
> <span data-ttu-id="83a48-108">Office 365 CDN은 **프로덕션** (전 세계) 클라우드의 테 넌 트에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-108">The Office 365 CDN is only available to tenants in the **Production** (worldwide) cloud.</span></span> <span data-ttu-id="83a48-109">미국 정부의 테 넌 트, 중국 및 독일 클라우드가 현재 Office 365 CDN을 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-109">Tenants in the US Government, China and Germany clouds do not currently support the Office 365 CDN.</span></span>

<span data-ttu-id="83a48-110">Office 365 CDN은 여러 위치, 즉 _출발지_에 정적 자산을 호스트하고 글로벌 고속 네트워크에서 제공할 수 있는 여러 CDN으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-110">The Office 365 CDN is composed of multiple CDNs that allow you to host static assets in multiple locations, or _origins_, and serve them from global high-speed networks.</span></span> <span data-ttu-id="83a48-111">Office 365 CDN에서 호스팅하려는 콘텐츠의 종류에 따라 **공개** 출처, **비공개** 출처 또는 둘 다를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-111">Depending on the kind of content you want to host in the Office 365 CDN, you can add **public** origins, **private** origins or both.</span></span> <span data-ttu-id="83a48-112">Public 및 private 원점과의 차이점에 대 한 자세한 내용은 [각 원점을 public 또는 private](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate) 중에서 선택 합니다 .를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="83a48-112">See [Choose whether each origin should be public or private](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate) for more information on the difference between public and private origins.</span></span>

<span data-ttu-id="83a48-113">![Office 365 CDN 개념 다이어그램](media/O365-CDN/o365-cdn-flow-transparent.svg "Office 365 CDN 개념 다이어그램")</span><span class="sxs-lookup"><span data-stu-id="83a48-113">![Office 365 CDN conceptual diagram](media/O365-CDN/o365-cdn-flow-transparent.svg "Office 365 CDN conceptual diagram")</span></span>

<span data-ttu-id="83a48-114">CDNs가 작동 하는 방식에 이미 익숙한 경우 테 넌 트에 Office 365 CDN을 사용 하도록 설정 하려면 몇 단계만 완료 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-114">If you are already familiar with the way that CDNs work, you only need to complete a few steps to enable the Office 365 CDN for your tenant.</span></span> <span data-ttu-id="83a48-115">이 항목에서는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-115">This topic describes how.</span></span> <span data-ttu-id="83a48-116">정적 자산 호스팅을 시작 하는 방법에 대 한 자세한 내용을 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="83a48-116">Read on for information about how to get started hosting your static assets.</span></span>

> [!TIP]
> <span data-ttu-id="83a48-117">특수 사용 시나리오에서는 Office 365와 함께 사용할 수 있는 Microsoft에서 호스팅하는 다른 CDNs가 있지만,이 항목에서는 Office 365 CDN 범위를 벗어나므로 여기서 설명 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-117">There are other Microsoft-hosted CDNs that can be used with Office 365 for specialized usage scenarios, but are not discussed in this topic because they fall outside the scope of the Office 365 CDN.</span></span> <span data-ttu-id="83a48-118">자세한 내용은 [다른 Microsoft CDNs](content-delivery-networks.md#other-microsoft-cdns)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="83a48-118">For more information, see [Other Microsoft CDNs](content-delivery-networks.md#other-microsoft-cdns).</span></span>

 <span data-ttu-id="83a48-119">**[Office 365의 네트워크 계획 및 성능 조정](https://aka.ms/tune)으로 돌아갑니다.**</span><span class="sxs-lookup"><span data-stu-id="83a48-119">**Head back to [Network planning and performance tuning for Office 365](https://aka.ms/tune).**</span></span>

## <a name="overview-of-working-with-the-office-365-cdn-in-sharepoint-online"></a><span data-ttu-id="83a48-120">SharePoint Online에서 Office 365 CDN 사용에 대 한 개요</span><span class="sxs-lookup"><span data-stu-id="83a48-120">Overview of working with the Office 365 CDN in SharePoint Online</span></span>

<span data-ttu-id="83a48-121">조직에 대해 Office 365 CDN을 설정 하려면 다음 기본 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-121">To set up the Office 365 CDN for your organization, you follow these basic steps:</span></span>

+ [<span data-ttu-id="83a48-122">Office 365 CDN 배포 계획</span><span class="sxs-lookup"><span data-stu-id="83a48-122">Plan for deployment of the Office 365 CDN</span></span>](use-office-365-cdn-with-spo.md#plan-for-deployment-of-the-office-365-cdn)

  + <span data-ttu-id="83a48-123">[CDN에서 호스트할 정적 자산을 결정](use-office-365-cdn-with-spo.md#CDNAssets)합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-123">[Determine which static assets you want to host on the CDN](use-office-365-cdn-with-spo.md#CDNAssets).</span></span>
  + <span data-ttu-id="83a48-124">[자산을 저장할 위치를 결정](use-office-365-cdn-with-spo.md#CDNStoreAssets)합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-124">[Determine where you want to store your assets](use-office-365-cdn-with-spo.md#CDNStoreAssets).</span></span> <span data-ttu-id="83a48-125">이 위치는 SharePoint 사이트, 라이브러리 또는 폴더 일 수 있으며 _출처_라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-125">This location can be a SharePoint site, library or folder and is called an _origin_.</span></span>
  + <span data-ttu-id="83a48-126">[각 원본이 공용 또는 개인 인지 여부를 선택](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate)합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-126">[Choose whether each origin should be public or private](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate).</span></span> <span data-ttu-id="83a48-127">공용 및 개인 형식 둘 다의 원본을 여러 개 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-127">You can add multiple origins of both public and private types.</span></span>

+ <span data-ttu-id="83a48-128">PowerShell 또는 SharePoint Online CLI를 사용 하 여 CDN을 설정 하 고 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-128">Set up and configure the CDN, using either PowerShell or the SharePoint Online CLI</span></span>

  + [<span data-ttu-id="83a48-129">SharePoint Online 관리 셸을 사용 하 여 CDN을 설정 하 고 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-129">Set up and configure the CDN by using the SharePoint Online Management Shell</span></span>](use-office-365-cdn-with-spo.md#CDNSetupinPShell)
  + [<span data-ttu-id="83a48-130">PnP PowerShell을 사용 하 여 CDN을 설정 하 고 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-130">Set up and configure the CDN by using PnP PowerShell</span></span>](use-office-365-cdn-with-spo.md#CDNSetupinPnPPosh)
  + [<span data-ttu-id="83a48-131">Office 365 CLI를 사용 하 여 CDN을 설정 하 고 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-131">Set up and configure the CDN by using the Office 365 CLI</span></span>](use-office-365-cdn-with-spo.md#CDNSetupinCLI)

  <span data-ttu-id="83a48-132">이 단계를 완료 하면 다음이 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-132">When you complete this step, you will have:</span></span>

  + <span data-ttu-id="83a48-133">조직에 CDN을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-133">Enabled the CDN for your organization.</span></span>
  + <span data-ttu-id="83a48-134">각 원점을 공용 또는 개인으로 식별 하는 출처를 추가 했습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-134">Added your origins, identifying each origin as public or private.</span></span>

<span data-ttu-id="83a48-135">설치를 완료 한 후에는 시간에 따른 [Office 365 CDN을 관리할](use-office-365-cdn-with-spo.md#CDNManage) 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-135">Once you're done with setup, you can [Manage the Office 365 CDN](use-office-365-cdn-with-spo.md#CDNManage) over time by:</span></span>
  
+ <span data-ttu-id="83a48-136">자산 추가, 업데이트 및 제거</span><span class="sxs-lookup"><span data-stu-id="83a48-136">Adding, updating, and removing assets</span></span>
+ <span data-ttu-id="83a48-137">원본 추가 및 제거</span><span class="sxs-lookup"><span data-stu-id="83a48-137">Adding and removing origins</span></span>
+ <span data-ttu-id="83a48-138">CDN 정책 구성</span><span class="sxs-lookup"><span data-stu-id="83a48-138">Configuring CDN policies</span></span>
+ <span data-ttu-id="83a48-139">필요한 경우 CDN을 사용 하지 않도록 설정</span><span class="sxs-lookup"><span data-stu-id="83a48-139">If necessary, disabling the CDN</span></span>

<span data-ttu-id="83a48-140">마지막으로, [cdn 자산을 사용](use-office-365-cdn-with-spo.md#using-your-cdn-assets) 하 여 공용 및 개인 원본 모두에서 cdn 자산에 액세스 하는 방법에 대해 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="83a48-140">Finally, see [Using your CDN assets](use-office-365-cdn-with-spo.md#using-your-cdn-assets) to learn about accessing your CDN assets from both public and private origins.</span></span>

<span data-ttu-id="83a48-141">일반적인 문제를 해결 하는 방법에 대 한 지침은 [Office 365 CDN 문제 해결](use-office-365-cdn-with-spo.md#CDNTroubleshooting) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="83a48-141">See [Troubleshooting the Office 365 CDN](use-office-365-cdn-with-spo.md#CDNTroubleshooting) for guidance on resolving common issues.</span></span>

## <a name="plan-for-deployment-of-the-office-365-cdn"></a><span data-ttu-id="83a48-142">Office 365 CDN 배포 계획</span><span class="sxs-lookup"><span data-stu-id="83a48-142">Plan for deployment of the Office 365 CDN</span></span>

<span data-ttu-id="83a48-143">Office 365 테 넌 트에 대 한 Office 365 CDN을 배포 하기 전에 계획 프로세스의 일부로 다음과 같은 요인을 고려해 야 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-143">Before you deploy the Office 365 CDN for your Office 365 tenant, you should consider the following factors as part of your planning process.</span></span>

  + [<span data-ttu-id="83a48-144">CDN에서 호스트할 정적 자산 확인</span><span class="sxs-lookup"><span data-stu-id="83a48-144">Determine which static assets you want to host on the CDN</span></span>](use-office-365-cdn-with-spo.md#CDNAssets)
  + [<span data-ttu-id="83a48-145">자산을 저장할 위치 결정</span><span class="sxs-lookup"><span data-stu-id="83a48-145">Determine where you want to store your assets</span></span>](use-office-365-cdn-with-spo.md#CDNStoreAssets)
  + [<span data-ttu-id="83a48-146">각 출처를 public 또는 private로 설정할지를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-146">Choose whether each origin should be public or private</span></span>](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate)

<span data-ttu-id="83a48-147"><a name="CDNAssets"> </a></span><span class="sxs-lookup"><span data-stu-id="83a48-147"><a name="CDNAssets"> </a></span></span>
### <a name="determine-which-static-assets-you-want-to-host-on-the-cdn"></a><span data-ttu-id="83a48-148">CDN에서 호스트할 정적 자산 확인</span><span class="sxs-lookup"><span data-stu-id="83a48-148">Determine which static assets you want to host on the CDN</span></span>

<span data-ttu-id="83a48-149">일반적으로 CDNs는 _정적 자산_을 호스트 하거나 자주 변경 되지 않는 자산을 호스팅하는 데 가장 효과적입니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-149">In general, CDNs are most effective for hosting _static assets_, or assets that don't change very often.</span></span> <span data-ttu-id="83a48-150">다음과 같은 조건 중 일부 또는 전부를 충족 하는 파일을 식별 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-150">A good rule of thumb is to identify files that meet some or all of these conditions:</span></span>

+ <span data-ttu-id="83a48-151">페이지 로드 시간에 큰 영향을 줄 수 있는 페이지 (스크립트 및 이미지 등)에 포함 된 정적 파일</span><span class="sxs-lookup"><span data-stu-id="83a48-151">Static files embedded in a page (like scripts and images) that may have a significant incremental impact on page load times</span></span>
+ <span data-ttu-id="83a48-152">실행 파일 및 설치 파일과 같은 큰 파일</span><span class="sxs-lookup"><span data-stu-id="83a48-152">Large files like executables and installation files</span></span>
+ <span data-ttu-id="83a48-153">클라이언트 쪽 코드를 지 원하는 리소스 라이브러리</span><span class="sxs-lookup"><span data-stu-id="83a48-153">Resource libraries that support client-side code</span></span>

<span data-ttu-id="83a48-154">예를 들어 사이트 이미지 및 스크립트와 마찬가지로 반복적으로 요청 되는 작은 파일은 사이트 렌더링 성능을 크게 향상 시키고, CDN 원본에 추가 하는 경우 SharePoint Online 사이트의 부하를 점차적으로 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-154">For example, small files that are repeatedly requested like site images and scripts can significantly improve site rendering performance and incrementally reduce the load on your SharePoint Online sites when you add them to a CDN origin.</span></span> <span data-ttu-id="83a48-155">설치 실행 파일과 같은 더 큰 파일을 CDN에서 다운로드할 수 있으므로 성능에 긍정적인 영향을 주는 것은 물론 SharePoint Online 사이트에 대 한 부하의 부하가 감소 하 여 자주 액세스 하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-155">Larger files such as installation executables can be downloaded from the CDN, delivering a positive performance impact and subsequent reduction of the load on your SharePoint Online site, even if they are not accessed as often.</span></span>

<span data-ttu-id="83a48-156">파일을 기준으로 성능 향상은 가장 가까운 CDN 끝점에 대 한 클라이언트의 근접성, 로컬 네트워크의 일시적 조건 등의 다양 한 요인에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-156">Performance improvement on a per-file basis is dependent on many factors, including the client's proximity to the nearest CDN endpoint, transient conditions on the local network, and so forth.</span></span> <span data-ttu-id="83a48-157">많은 정적 파일은 매우 작으며 Office 365에서 1 초 이내에 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-157">Many static files are quite small, and can be downloaded from Office 365 in less than a second.</span></span> <span data-ttu-id="83a48-158">그러나 웹 페이지에는 다운로드 시간이 누적 되는 여러 개의 포함 된 파일이 몇 초 동안 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-158">However, a web page may contain many embedded files with a cumulative download time of several seconds.</span></span> <span data-ttu-id="83a48-159">CDN에서 이러한 파일을 처리 하면 전체 페이지 로드 시간이 크게 줄어들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-159">Serving these files from the CDN can significantly reduce the overall page load time.</span></span> <span data-ttu-id="83a48-160">[CDN에서 제공 하는 성능 향상은 무엇 인가요?](content-delivery-networks.md#what-performance-gains-does-a-cdn-provide) 예를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="83a48-160">See [What performance gains does a CDN provide?](content-delivery-networks.md#what-performance-gains-does-a-cdn-provide) for an example.</span></span>

<span data-ttu-id="83a48-161"><a name="CDNStoreAssets"> </a></span><span class="sxs-lookup"><span data-stu-id="83a48-161"><a name="CDNStoreAssets"> </a></span></span>
### <a name="determine-where-you-want-to-store-your-assets"></a><span data-ttu-id="83a48-162">자산을 저장할 위치 결정</span><span class="sxs-lookup"><span data-stu-id="83a48-162">Determine where you want to store your assets</span></span>

<span data-ttu-id="83a48-163">CDN은 _근원_이라는 위치에서 자산을 페치합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-163">The CDN fetches your assets from a location called an _origin_.</span></span> <span data-ttu-id="83a48-164">원본은 URL에서 액세스할 수 있는 SharePoint 사이트, 문서 라이브러리 또는 폴더가 될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-164">An origin can be a SharePoint site, document library or folder that is accessible by a URL.</span></span> <span data-ttu-id="83a48-165">조직의 원본을 지정할 때 유연성이 뛰어납니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-165">You have great flexibility when you specify origins for your organization.</span></span> <span data-ttu-id="83a48-166">예를 들어 모든 CDN 자산을 추가 하려는 원본이 여러 개 있거나 하나만 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-166">For example, you can specify multiple origins or a single origin where you want to put all your CDN assets.</span></span> <span data-ttu-id="83a48-167">조직의 공용 또는 개인 원본을 둘 다 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-167">You can choose to have both public or private origins for your organization.</span></span> <span data-ttu-id="83a48-168">대부분의 조직에서는 두 가지를 조합 하 여 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-168">Most organizations will choose to implement a combination of the two.</span></span>

<span data-ttu-id="83a48-169">폴더 또는 문서 라이브러리와 같은 원본에 대 한 새 컨테이너를 만들고 CDN에서 사용 가능 하도록 설정할 파일을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-169">You can create new container for your origins such as folders or document libraries, and add files you want to make available from the CDN.</span></span> <span data-ttu-id="83a48-170">CDN에서 사용 하려는 특정 자산의 집합이 있고 CDN 자산 집합을 컨테이너의 해당 파일로 제한 하려는 경우에는이 방법이 좋은 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-170">This is a good approach if you have a specific set of assets you want to be available from the CDN, and want to restrict the set of CDN assets to only those files in the container.</span></span>

<span data-ttu-id="83a48-171">기존 사이트 모음, 사이트, 라이브러리 또는 폴더를 원본으로 구성 하 여 해당 컨테이너의 모든 적합 한 자산을 CDN에서 사용할 수 있도록 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-171">You can also configure an existing site collection, site, library or folder as an origin, which will make all eligible assets in the container available from the CDN.</span></span> <span data-ttu-id="83a48-172">기존 컨테이너를 원본으로 추가 하기 전에 익명 액세스 또는 권한 없는 사용자에 게 자산을 실수로 노출 하지 않도록 하기 위해 해당 콘텐츠 및 사용 권한을 알고 있는지 확인 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-172">Before you add an existing container as an origin, it's important to make sure you are aware of its contents and permissions so you do not inadvertently expose assets to anonymous access or unauthorized users.</span></span>

<span data-ttu-id="83a48-173">Cdn에서 원본에 있는 콘텐츠를 제외 하도록 _cdn 정책을_ 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-173">You can define _CDN policies_ to exclude content in your origins from the CDN.</span></span> <span data-ttu-id="83a48-174">CDN 정책은 공용 또는 개인 원본에서 _파일 형식_ 및 _사이트 분류_와 같은 특성을 통해 자산을 제외 하 고, 정책에 지정 하는 cdntype (private 또는 public)의 모든 원본에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-174">CDN policies exclude assets in public or private origins by attributes such as _file type_ and _site classification_, and are applied to all origins of the CdnType (private or public) you specify in the policy.</span></span> <span data-ttu-id="83a48-175">예를 들어 여러 하위 사이트가 포함 된 사이트로 구성 된 개인 출처를 추가 하는 경우 해당 분류가 적용 된 사이트의 콘텐츠가 CDN에서 처리 되지 않도록 **비밀 우편** 으로 표시 된 사이트를 제외 하는 정책을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-175">For example, if you add a private origin consisting of a site that contains multiple subsites, you can define a policy to exclude sites marked as **Confidential** so content from sites with that classification applied will not be served from the CDN.</span></span> <span data-ttu-id="83a48-176">정책은 CDN에 추가한 _모든_ 개인 출처의 콘텐츠에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-176">The policy will apply to content from _all_ private origins you have added to the CDN.</span></span>
  
<span data-ttu-id="83a48-177">원본 수가 많을 수록 CDN 서비스에서 요청을 처리 하는 데 소요 되는 시간에 더 많은 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-177">Keep in mind that the greater the number of origins, the greater the impact on the time it takes the CDN service to process requests.</span></span> <span data-ttu-id="83a48-178">원본 수를 가능한 한 많이 제한 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-178">We recommend that you limit the number of origins as much as possible.</span></span>
  
<span data-ttu-id="83a48-179"><a name="CDNOriginChoosePublicPrivate"> </a></span><span class="sxs-lookup"><span data-stu-id="83a48-179"><a name="CDNOriginChoosePublicPrivate"> </a></span></span>
### <a name="choose-whether-each-origin-should-be-public-or-private"></a><span data-ttu-id="83a48-180">각 출처를 public 또는 private로 설정할지를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-180">Choose whether each origin should be public or private</span></span>

<span data-ttu-id="83a48-181">출처를 식별할 때는 _공용_ 또는 _비공개로_설정할 지 여부를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-181">When you identify an origin, you specify whether it should be made _public_ or _private_.</span></span> <span data-ttu-id="83a48-182">공용 원본에서 CDN 자산에 대 한 액세스는 익명으로 진행 되며 개인 원본에 있는 CDN 콘텐츠는 보안을 강화 하기 위해 동적으로 생성 된 토큰에 의해 보호 됩니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-182">Access to CDN assets in public origins is anonymous, and CDN content in private origins is secured by dynamically generated tokens for greater security.</span></span> <span data-ttu-id="83a48-183">선택 하는 옵션에 관계 없이 Microsoft는 CDN 자체를 관리 하는 경우 모든 사용자를 대상으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-183">Regardless of which option you choose, Microsoft does all the heavy lifting for you when it comes to administration of the CDN itself.</span></span> <span data-ttu-id="83a48-184">또한 CDN을 설정 하 고 원본을 식별 한 후 나중에 생각이 바뀔 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-184">Also, you can change your mind later, after you've set up the CDN and identified your origins.</span></span>

<span data-ttu-id="83a48-185">공용 및 개인 옵션은 모두 비슷한 성능을 제공 하지만 각각에 고유한 특성 및 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-185">Both public and private options provide similar performance gains, but each has unique attributes and advantages.</span></span>

<span data-ttu-id="83a48-186">Office 365 CDN 내의 **공용** 원본에는 익명으로 액세스할 수 있으며 자산에 대 한 URL을 가진 모든 사용자가 호스트 된 자산에 액세스 하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-186">**Public** origins within the Office 365 CDN are accessible anonymously, and hosted assets can be accessed by anyone who has the URL to the asset.</span></span> <span data-ttu-id="83a48-187">공개 출처의 콘텐츠에 대한 액세스는 익명이기 때문에 캐시 javascript 파일, 스크립트, 아이콘 및 이미지와 같은 중요하지 않은 일반 콘텐츠에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-187">Because access to content in public origins is anonymous, you should only use them to cache non-sensitive generic content such as javascript files, scripts, icons and images.</span></span>

<span data-ttu-id="83a48-188">Office 365 CDN 내의 **비공개** 원본을 사용 하면 SharePoint Online 문서 라이브러리, 사이트 및 독점적인 이미지 등의 사용자 콘텐츠에 대 한 비공개 액세스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-188">**Private** origins within the Office 365 CDN provide private access to user content such as SharePoint Online document libraries, sites and proprietary images.</span></span> <span data-ttu-id="83a48-189">원본 문서 라이브러리나 저장 위치에 대 한 사용 권한이 있는 사용자만 액세스할 수 있도록 개인 원본의 콘텐츠에 대 한 액세스를 동적으로 생성 된 토큰으로 보호 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-189">Access to content in private origins is secured by dynamically generated tokens so it can only be accessed by users with permissions to the original document library or storage location.</span></span> <span data-ttu-id="83a48-190">Office 365 CDN의 비공개 출처는 SharePoint Online 콘텐츠에만 사용할 수 있으며, SharePoint Online 테 넌 트에서 리디렉션을 통해서만 개인 원본에 있는 자산에만 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-190">Private origins in the Office 365 CDN can only be used for SharePoint Online content, and you can only access assets in private origins through redirection from your SharePoint Online tenant.</span></span>

<span data-ttu-id="83a48-191">비공개 원본의 자산에 대 한 CDN 액세스에 대 한 자세한 내용은 전용 원본 [에 자산 사용](use-office-365-cdn-with-spo.md#using-assets-in-private-origins)에서 작업을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="83a48-191">You can read more about how CDN access to assets in a private origin works in [Using assets in private origins](use-office-365-cdn-with-spo.md#using-assets-in-private-origins).</span></span>

#### <a name="attributes-and-advantages-of-hosting-assets-in-public-origins"></a><span data-ttu-id="83a48-192">공개 원본에서의 자산 호스팅 특성 및 장점</span><span class="sxs-lookup"><span data-stu-id="83a48-192">Attributes and advantages of hosting assets in public origins</span></span>
  
+ <span data-ttu-id="83a48-193">공용 원본에 표시 되는 자산은 모든 사용자가 익명으로 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-193">Assets exposed in a public origin are accessible by everyone anonymously.</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="83a48-194">사용자 정보가 포함 된 리소스를 배치 하거나 조직에서 공용 원본으로 중요 한 것으로 간주 해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-194">You should never place resources that contain user information or are considered sensitive to your organization in a public origin.</span></span>
+ <span data-ttu-id="83a48-195">공개 원점에서 자산을 제거 하는 경우에는 해당 자산을 캐시에서 최대 30 일 동안 계속 사용할 수 있습니다. 그러나 15 분 내에 CDN의 자산에 대 한 링크가 무효화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-195">If you remove an asset from a public origin, the asset may continue to be available for up to 30 days from the cache; however, we will invalidate links to the asset in the CDN within 15 minutes.</span></span>
+ <span data-ttu-id="83a48-196">공용 원점에 스타일 시트 (CSS 파일)를 호스트 하는 경우 코드 내에 상대 경로와 Uri를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-196">When you host style sheets (CSS files) in a public origin, you can use relative paths and URIs within the code.</span></span> <span data-ttu-id="83a48-197">즉, 배경 이미지 및 다른 개체를 호출 하는 자산의 위치를 기준으로 해당 위치를 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-197">This means that you can reference the location of background images and other objects relative to the location of the asset that's calling it.</span></span>
+ <span data-ttu-id="83a48-198">공용 원본의 URL을 하드 코딩 하는 것은 좋지만, 이렇게 하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-198">While you can hard code a public origin's URL, doing so is not recommended.</span></span> <span data-ttu-id="83a48-199">이는 CDN에 대 한 액세스를 사용할 수 없는 경우 URL이 SharePoint Online에서 조직에 자동으로 확인 되지 않으며 링크 및 기타 오류가 발생할 수 있기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-199">The reason for this is that if access to the CDN becomes unavailable, the URL will not automatically resolve to your organization in SharePoint Online and might result in broken links and other errors.</span></span>
+ <span data-ttu-id="83a48-200">공용 원본에 대해 포함 되는 기본 파일 형식은 .css, eot, .gif, .ico, .jpeg, .jpg,. ttf 및. w o v,. p s v,.</span><span class="sxs-lookup"><span data-stu-id="83a48-200">The default file types that are included for public origins are .css, .eot, .gif, .ico, .jpeg, .jpg, .js, .map, .png, .svg, .ttf, and .woff.</span></span> <span data-ttu-id="83a48-201">추가 파일 형식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-201">You can specify additional file types.</span></span>
+ <span data-ttu-id="83a48-202">지정한 사이트 분류에 의해 식별 된 자산을 제외 하도록 정책을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-202">You can configure a policy to exclude assets that have been identified by site classifications that you specify.</span></span> <span data-ttu-id="83a48-203">예를 들어, 허용 되는 파일 형식이 고 공용 원본에 있는 경우에도 "기밀" 또는 "제한"으로 표시 된 모든 자산을 제외 하도록 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-203">For example, you can choose to exclude all assets that are marked as "confidential" or "restricted" even if they are an allowed file type and are located in a public origin.</span></span>

#### <a name="attributes-and-advantages-of-hosting-assets-in-private-origins"></a><span data-ttu-id="83a48-204">전용 원본에서의 자산 호스팅의 특성 및 장점</span><span class="sxs-lookup"><span data-stu-id="83a48-204">Attributes and advantages of hosting assets in private origins</span></span>

+ <span data-ttu-id="83a48-205">비공개 출처는 SharePoint Online 자산에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-205">Private origins can only be used for SharePoint Online assets.</span></span>
+ <span data-ttu-id="83a48-206">사용자는 컨테이너에 대 한 액세스 권한이 있는 경우에만 비공개 원본의 자산에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-206">Users can only access the assets from a private origin if they have permissions to access the container.</span></span> <span data-ttu-id="83a48-207">이러한 자산에 대 한 익명 액세스는 차단 됩니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-207">Anonymous access to these assets is prevented.</span></span>
+ <span data-ttu-id="83a48-208">개인 원본에 있는 자산은 SharePoint Online 테 넌 트에서 참조 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-208">Assets in private origins must be referred from the SharePoint Online tenant.</span></span> <span data-ttu-id="83a48-209">사설 CDN 자산에 직접 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-209">Direct access to private CDN assets does not work.</span></span>
+ <span data-ttu-id="83a48-210">비공개 원본에서 자산을 제거 하는 경우에는 자산을 캐시에서 한 시간까지 계속 사용할 수 있습니다. 그러나 자산의 제거 후 15 분 이내에 CDN의 자산에 대 한 링크가 무효화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-210">If you remove an asset from the private origin, the asset may continue to be available for up to an hour from the cache; however, we will invalidate links to the asset in the CDN within 15 minutes of the asset's removal.</span></span>
+ <span data-ttu-id="83a48-211">전용 원본에 대해 포함 되는 기본 파일 형식은 .gif, .ico, .jpeg, .jpg, .js 및 .png입니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-211">The default file types that are included for private origins are .gif, .ico, .jpeg, .jpg, .js, and .png.</span></span> <span data-ttu-id="83a48-212">추가 파일 형식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-212">You can specify additional file types.</span></span>
+ <span data-ttu-id="83a48-213">공용 출처와 마찬가지로 와일드 카드를 사용 하 여 폴더 또는 문서 라이브러리 내의 모든 자산을 포함 하는 경우에도 사용자가 지정한 사이트 분류에 의해 식별 된 자산을 제외 하도록 정책을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-213">Just like with public origins, you can configure a policy to exclude assets that have been identified by site classifications that you specify even if you use wildcards to include all assets within a folder or document library.</span></span>

<span data-ttu-id="83a48-214">Office 365 CDN, 일반 CDN 개념 및 Office 365 테 넌 트에서 사용할 수 있는 기타 Microsoft CDNs를 사용 하는 이유에 대 한 자세한 내용은 [콘텐츠 배달 네트워크](content-delivery-networks.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="83a48-214">For more information about why to use the Office 365 CDN, general CDN concepts, and other Microsoft CDNs you can use with your Office 365 tenant, see [Content Delivery Networks](content-delivery-networks.md).</span></span>

### <a name="default-cdn-origins"></a><span data-ttu-id="83a48-215">기본 CDN 원본</span><span class="sxs-lookup"><span data-stu-id="83a48-215">Default CDN origins</span></span>

<span data-ttu-id="83a48-216">별도로 지정 하지 않으면 office 365에서 Office 365 CDN을 사용 하도록 설정할 때 기본 원본을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-216">Unless you specify otherwise, Office 365 sets up some default origins for you when you enable the Office 365 CDN.</span></span> <span data-ttu-id="83a48-217">처음에 프로 비전 하지 않을 경우에는 설치를 완료 한 후 이러한 원본을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-217">If you initially opt not to provision them, you can add these origins after you complete setup.</span></span> <span data-ttu-id="83a48-218">기본 원본에 대 한 설정을 건너뛰고이를 수행 하는 특별 한 이유가 있는 경우를 이해 하지 않으면 CDN을 사용 하도록 설정할 때이 설정의 생성을 허용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-218">Unless you understand the consequences of skipping the setup of default origins and have a specific reason for doing so, you should allow them to be created when you enable the CDN.</span></span>
  
<span data-ttu-id="83a48-219">기본 개인 CDN 원본:</span><span class="sxs-lookup"><span data-stu-id="83a48-219">Default private CDN origins:</span></span>
  
+ <span data-ttu-id="83a48-220">\*/userphoto.aspx</span><span class="sxs-lookup"><span data-stu-id="83a48-220">\*/userphoto.aspx</span></span>
+ <span data-ttu-id="83a48-221">\*/cusets</span><span class="sxs-lookup"><span data-stu-id="83a48-221">\*/siteassets</span></span>

<span data-ttu-id="83a48-222">기본 공용 CDN 원본:</span><span class="sxs-lookup"><span data-stu-id="83a48-222">Default public CDN origins:</span></span>
  
+ <span data-ttu-id="83a48-223">\*/masterpage</span><span class="sxs-lookup"><span data-stu-id="83a48-223">\*/masterpage</span></span>
+ <span data-ttu-id="83a48-224">\*/restyle 라이브러리</span><span class="sxs-lookup"><span data-stu-id="83a48-224">\*/style library</span></span>
+ <span data-ttu-id="83a48-225">\*/reclient자산과 자산</span><span class="sxs-lookup"><span data-stu-id="83a48-225">\*/clientsideassets</span></span>

> [!NOTE]
> <span data-ttu-id="83a48-226">_clientsideassets_ 12 월 2017에 OFFICE 365 CDN 서비스에 추가 된 기본 공용 원본입니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-226">_clientsideassets_ is a default public origin that was added to the Office 365 CDN service in December 2017.</span></span> <span data-ttu-id="83a48-227">CDN에서 SharePoint Framework 솔루션이 작동 하려면이 원본이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-227">This origin must be present in order for SharePoint Framework solutions in the CDN to work.</span></span> <span data-ttu-id="83a48-228">Office 365 CDN을 12 월 2017 이전에 사용 하도록 설정 했거나 CDN을 사용 하도록 설정 했을 때 기본 원본 설치를 건너뛴 경우이 원본을 수동으로 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-228">If you enabled the Office 365 CDN prior to December 2017, or if you skipped setup of default origins when you enabled the CDN, you can manually add this origin.</span></span> <span data-ttu-id="83a48-229">자세한 내용은 [내 클라이언트 쪽 웹 파트 또는 SharePoint Framework 솔루션이 작동 하지 않는](use-office-365-cdn-with-spo.md#my-client-side-web-part-or-sharepoint-framework-solution-isnt-working)경우를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="83a48-229">For more information, see [My client-side web part or SharePoint Framework solution isn't working](use-office-365-cdn-with-spo.md#my-client-side-web-part-or-sharepoint-framework-solution-isnt-working).</span></span>

<span data-ttu-id="83a48-230"><a name="CDNSetupinPShell"> </a></span><span class="sxs-lookup"><span data-stu-id="83a48-230"><a name="CDNSetupinPShell"> </a></span></span>
## <a name="set-up-and-configure-the-office-365-cdn-by-using-the-sharepoint-online-management-shell"></a><span data-ttu-id="83a48-231">SharePoint Online 관리 셸을 사용 하 여 Office 365 CDN을 설정 하 고 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-231">Set up and configure the Office 365 CDN by using the SharePoint Online Management Shell</span></span>

<span data-ttu-id="83a48-232">이 섹션의 절차를 수행 하려면 SharePoint Online 관리 셸을 사용 하 여 SharePoint Online에 연결 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-232">The procedures in this section require you to use the SharePoint Online Management Shell to connect to SharePoint Online.</span></span> <span data-ttu-id="83a48-233">자세한 내용은 [SharePoint Online PowerShell에 연결을](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="83a48-233">For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span></span>

<span data-ttu-id="83a48-234">Sharepoint online 관리 셸을 사용 하 여 SharePoint Online에서 자산을 호스트 하도록 CDN을 설정 및 구성 하려면 다음 단계를 완료 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-234">Complete these steps to set up and configure the CDN to host your assets in SharePoint Online using the SharePoint Online Management Shell.</span></span>

<details>
  <summary><span data-ttu-id="83a48-235">클릭 하 여 확장</span><span class="sxs-lookup"><span data-stu-id="83a48-235">Click to expand</span></span></summary>

### <a name="enable-your-organization-to-use-the-office-365-cdn"></a><span data-ttu-id="83a48-236">조직이 Office 365 CDN을 사용 하도록 설정</span><span class="sxs-lookup"><span data-stu-id="83a48-236">Enable your organization to use the Office 365 CDN</span></span>

<span data-ttu-id="83a48-237">테 넌 트 CDN 설정을 변경 하기 전에 Office 365 테 넌 트에서 개인 CDN 구성의 현재 상태를 검색 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-237">Before you make changes to the tenant CDN settings, you should retrieve the current status of the private CDN configuration in your Office 365 tenant.</span></span> <span data-ttu-id="83a48-238">SharePoint Online 관리 셸을 사용 하 여 테 넌 트에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-238">Connect to your tenant using the SharePoint Online Management Shell:</span></span>

``` powershell
Connect-SPOService -Url https://contoso-admin.sharepoint.com
```

<span data-ttu-id="83a48-239">이제 **SPOTenantCdnEnabled** cmdlet을 사용 하 여 테 넌 트에서 CDN 상태 설정을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-239">Now use the **Get-SPOTenantCdnEnabled** cmdlet to retrieve the CDN status settings from the tenant:</span></span>

``` powershell
Get-SPOTenantCdnEnabled -CdnType <Public | Private>
```

<span data-ttu-id="83a48-240">지정한 CdnType에 대 한 CDN의 상태가 화면에 출력 됩니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-240">The status of the CDN for the specified CdnType will output to the screen.</span></span>

<span data-ttu-id="83a48-241">**SPOTenantCdnEnabled** cmdlet을 사용 하 여 조직에서 OFFICE 365 CDN을 사용 하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-241">Use the **Set-SPOTenantCdnEnabled** cmdlet to enable your organization to use the Office 365 CDN.</span></span> <span data-ttu-id="83a48-242">조직이 공용 원본, 전용 원본 또는 두 가지 모두를 한 번에 사용 하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-242">You can enable your organization to use public origins, private origins, or both at once.</span></span> <span data-ttu-id="83a48-243">또한이 기능을 사용 하도록 설정 하면 기본 원본 설정을 건너뛰도록 CDN을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-243">You can also configure the CDN to skip the setup of default origins when you enable it.</span></span> <span data-ttu-id="83a48-244">이 항목의 설명에 따라 나중에 이러한 원본을 언제 든 지 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-244">You can always add these origins later as described in this topic.</span></span>
  
<span data-ttu-id="83a48-245">SharePoint Online 용 Windows Powershell:</span><span class="sxs-lookup"><span data-stu-id="83a48-245">In Windows Powershell for SharePoint Online:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType <Public | Private | Both> -Enable $true
```

<span data-ttu-id="83a48-246">예를 들어 조직에서 공용 및 개인 원본을 둘 다 사용할 수 있도록 설정 하려면 다음 명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-246">For example, to enable your organization to use both public and private origins, type the following command:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true
```

<span data-ttu-id="83a48-247">조직이 공용 및 개인 원본을 모두 사용할 수 있도록 설정 하 고 기본 원본을 설정 하지 않으려면 다음 명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-247">To enable your organization to use both public and private origins but skip setting up the default origins, type the following command:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true -NoDefaultOrigins
```

<span data-ttu-id="83a48-248">Office 365 CDN을 사용 하도록 설정 하는 경우 기본적으로 프로 비전 되는 원본에 대 한 정보 및 기본 원본 설정을 건너뛰는 경우 발생할 수 있는 영향에 대 한 자세한 내용은 [DEFAULT CDN 원본임](use-office-365-cdn-with-spo.md#default-cdn-origins) 을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="83a48-248">See [Default CDN origins](use-office-365-cdn-with-spo.md#default-cdn-origins) for information about the origins that are provisioned by default when you enable the Office 365 CDN, and the potential impact of skipping the setup of default origins.</span></span>

<span data-ttu-id="83a48-249">조직에서 공용 원본을 사용 하도록 설정 하려면 다음 명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-249">To enable your organization to use public origins, type the following command:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType Public -Enable $true
```

<span data-ttu-id="83a48-250">조직에서 전용 원본을 사용 하도록 설정 하려면 다음 명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-250">To enable your organization to use private origins, type the following command:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType Private -Enable $true
```

<span data-ttu-id="83a48-251">이 cmdlet에 대 한 자세한 내용은 [SPOTenantCdnEnabled](https://technet.microsoft.com/library/mt790765.aspx)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="83a48-251">For more information about this cmdlet, see [Set-SPOTenantCdnEnabled](https://technet.microsoft.com/library/mt790765.aspx).</span></span>

<span data-ttu-id="83a48-252"><a name="Office365CDNforSPOFileType"> </a></span><span class="sxs-lookup"><span data-stu-id="83a48-252"><a name="Office365CDNforSPOFileType"> </a></span></span>
### <a name="change-the-list-of-file-types-to-include-in-the-office-365-cdn-optional"></a><span data-ttu-id="83a48-253">Office 365 CDN에 포함할 파일 형식 목록 변경 (선택 사항)</span><span class="sxs-lookup"><span data-stu-id="83a48-253">Change the list of file types to include in the Office 365 CDN (Optional)</span></span>

> [!TIP]
> <span data-ttu-id="83a48-254">**SPOTenantCdnPolicy** cmdlet을 사용 하 여 파일 형식을 정의 하는 경우 현재 정의 된 목록을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-254">When you define file types by using the **Set-SPOTenantCdnPolicy** cmdlet, you overwrite the currently defined list.</span></span> <span data-ttu-id="83a48-255">목록에 다른 파일 형식을 추가 하려면 먼저 cmdlet을 사용 하 여 이미 허용 된 파일 형식을 확인 하 여 새 파일과 함께 목록에 포함 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-255">If you want to add additional file types to the list, use the cmdlet first to find out what file types are already allowed and include them in the list along with your new ones.</span></span>
  
<span data-ttu-id="83a48-256">**SPOTenantCdnPolicy** cmdlet을 사용 하 여 CDN에서 공용 및 전용 원본으로 호스팅할 수 있는 정적 파일 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-256">Use the **Set-SPOTenantCdnPolicy** cmdlet to define static file types that can be hosted by public and private origins in the CDN.</span></span> <span data-ttu-id="83a48-257">기본적으로 일반 에셋 유형 (예: .css, .gif, .jpg, .js)을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-257">By default, common asset types are allowed, for example .css, .gif, .jpg, and .js.</span></span>

<span data-ttu-id="83a48-258">SharePoint Online 용 Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="83a48-258">In Windows PowerShell for SharePoint Online:</span></span>

``` powershell
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType IncludeFileExtensions -PolicyValue "<Comma-separated list of file types >"
```

<span data-ttu-id="83a48-259">예를 들어 CDN에서 .css 및 .png 파일을 호스팅할 수 있도록 설정 하려면 다음 명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-259">For example, to enable the CDN to host .css and .png files, you would enter the command:</span></span>

``` powershell
Set-SPOTenantCdnPolicy -CdnType Private -PolicyType IncludeFileExtensions -PolicyValue "CSS,PNG"
```

<span data-ttu-id="83a48-260">CDN에서 현재 허용 되는 파일 형식을 확인 하려면 **SPOTenantCdnPolicies** cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-260">To see what file types are currently allowed by the CDN, use the **Get-SPOTenantCdnPolicies** cmdlet:</span></span>

``` powershell
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

<span data-ttu-id="83a48-261">이러한 cmdlet에 대 한 자세한 내용은 [SPOTenantCdnPolicy](https://technet.microsoft.com/library/mt800839.aspx) 및 [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/library/mt800838.aspx)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="83a48-261">For more information about these cmdlets, see [Set-SPOTenantCdnPolicy](https://technet.microsoft.com/library/mt800839.aspx) and [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/library/mt800838.aspx).</span></span>

<span data-ttu-id="83a48-262"><a name="Office365CDNforSPOSiteClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="83a48-262"><a name="Office365CDNforSPOSiteClassification"> </a></span></span>
### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn-optional"></a><span data-ttu-id="83a48-263">Office 365 CDN에서 제외 하려는 사이트 분류 목록 변경 (선택 사항)</span><span class="sxs-lookup"><span data-stu-id="83a48-263">Change the list of site classifications you want to exclude from the Office 365 CDN (Optional)</span></span>

> [!TIP]
> <span data-ttu-id="83a48-264">**SPOTenantCdnPolicy** cmdlet을 사용 하 여 사이트 분류를 제외 하는 경우 현재 정의 된 목록을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-264">When you exclude site classifications by using the **Set-SPOTenantCdnPolicy** cmdlet, you overwrite the currently defined list.</span></span> <span data-ttu-id="83a48-265">추가 사이트 분류를 제외 하려면 먼저 cmdlet을 사용 하 여 이미 제외 된 분류를 확인 한 다음 새 항목과 함께 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-265">If you want to exclude additional site classifications, use the cmdlet first to find out what classifications are already excluded and then add them along with your new ones.</span></span>

<span data-ttu-id="83a48-266">**SPOTenantCdnPolicy** cmdlet을 사용 하 여 CDN을 통해 사용 하지 않도록 설정할 사이트 분류를 제외 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-266">Use the **Set-SPOTenantCdnPolicy** cmdlet to exclude site classifications that you do not want to make available over the CDN.</span></span> <span data-ttu-id="83a48-267">기본적으로 사이트 분류는 제외 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-267">By default, no site classifications are excluded.</span></span>

<span data-ttu-id="83a48-268">SharePoint Online 용 Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="83a48-268">In Windows PowerShell for SharePoint Online:</span></span>

``` powershell
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType ExcludeRestrictedSiteClassifications  -PolicyValue "<Comma-separated list of site classifications >"
```

<span data-ttu-id="83a48-269">현재 제한 된 사이트 분류를 확인 하려면 **SPOTenantCdnPolicies** cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-269">To see what site classifications are currently restricted, use the **Get-SPOTenantCdnPolicies** cmdlet:</span></span>

``` powershell
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

<span data-ttu-id="83a48-270">반환 되는 속성은 _IncludeFileExtensions_, _ExcludeRestrictedSiteClassifications_ 및 _excludeifnoscriptdisabled_입니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-270">The properties that will be returned are _IncludeFileExtensions_, _ExcludeRestrictedSiteClassifications_ and _ExcludeIfNoScriptDisabled_.</span></span>

<span data-ttu-id="83a48-271">_IncludeFileExtensions_ 속성에는 CDN에서 처리할 파일 확장명 목록이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-271">The _IncludeFileExtensions_ property contains the list of file extensions that will be served from the CDN.</span></span>

> [!NOTE]
> <span data-ttu-id="83a48-272">기본 파일 확장명은 public 및 private과 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-272">The default file extensions are different between public and private.</span></span>

<span data-ttu-id="83a48-273">_ExcludeRestrictedSiteClassifications_ 속성은 CDN에서 제외 하려는 사이트 분류를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-273">The _ExcludeRestrictedSiteClassifications_ property contains the site classifications that you want to exclude from the CDN.</span></span> <span data-ttu-id="83a48-274">예를 들어 해당 분류가 적용 된 사이트의 콘텐츠가 CDN에서 처리 되지 않도록 **비밀 우편** 으로 표시 된 사이트를 제외할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-274">For example, you can exclude sites marked as **Confidential** so content from sites with that classification applied will not be served from the CDN.</span></span>

<span data-ttu-id="83a48-275">_Excludeifnoscriptdisabled_ 속성은 사이트 수준 _noscript_ 특성 설정에 따라 CDN에서 콘텐츠를 제외 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-275">The _ExcludeIfNoScriptDisabled_ property excludes content from the CDN based on the site-level _NoScript_ attribute settings.</span></span> <span data-ttu-id="83a48-276">기본적으로 _최신_ 사이트에는 _Noscript_ 특성이 **사용** 으로 설정 되 고 _클래식_ 사이트에는 사용 **되지** 않습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-276">By default, the _NoScript_ attribute is set to **Enabled** for _Modern_ sites and **Disabled** for _Classic_ sites.</span></span> <span data-ttu-id="83a48-277">이것은 테 넌 트 설정에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-277">This depends on your tenant settings.</span></span>

<span data-ttu-id="83a48-278">이러한 cmdlet에 대 한 자세한 내용은 [SPOTenantCdnPolicy](https://technet.microsoft.com/library/mt800839.aspx) 및 [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/library/mt800838.aspx)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="83a48-278">For more information about these cmdlets, see [Set-SPOTenantCdnPolicy](https://technet.microsoft.com/library/mt800839.aspx) and [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/library/mt800838.aspx).</span></span>

<span data-ttu-id="83a48-279"><a name="Office365CDNforSPOOrigin"> </a></span><span class="sxs-lookup"><span data-stu-id="83a48-279"><a name="Office365CDNforSPOOrigin"> </a></span></span>
### <a name="add-an-origin-for-your-assets"></a><span data-ttu-id="83a48-280">자산에 대 한 근원 추가</span><span class="sxs-lookup"><span data-stu-id="83a48-280">Add an origin for your assets</span></span>

<span data-ttu-id="83a48-281">**SPOTenantCdnOrigin** cmdlet을 사용 하면 원점을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-281">Use the **Add-SPOTenantCdnOrigin** cmdlet to define an origin.</span></span> <span data-ttu-id="83a48-282">여러 원본을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-282">You can define multiple origins.</span></span> <span data-ttu-id="83a48-283">원점은 CDN에서 호스팅할 자산이 포함 된 SharePoint 라이브러리 또는 폴더를 가리키는 URL입니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-283">The origin is a URL that points to a SharePoint library or folder that contains the assets that you want to be hosted by the CDN.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="83a48-284">사용자 정보가 포함 된 리소스를 배치 하거나 조직에서 공용 원본으로 중요 한 것으로 간주 해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-284">You should never place resources that contain user information or are considered sensitive to your organization in a public origin.</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType <Public | Private> -OriginUrl <path>
```

<span data-ttu-id="83a48-285">_Path_ 값은 자산이 포함 된 라이브러리 또는 폴더에 대 한 상대 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-285">The value of _path_ is the relative path to the library or folder that contains the assets.</span></span> <span data-ttu-id="83a48-286">상대 경로 외에도 와일드 카드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-286">You can use wildcards in addition to relative paths.</span></span> <span data-ttu-id="83a48-287">원본 URL 앞에는 와일드 카드를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-287">Origins support wildcards prepended to the URL.</span></span> <span data-ttu-id="83a48-288">이를 통해 여러 사이트에 걸쳐 있는 원본을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-288">This allows you to create origins that span multiple sites.</span></span> <span data-ttu-id="83a48-289">예를 들어 모든 사이트에 대 한 masterpages 폴더의 모든 자산을 CDN 내의 공용 근원으로 포함 하려면 다음 명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-289">For example, to include all of the assets in the masterpages folder for all of your sites as a public origin within the CDN, type the following command:</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
```

+ <span data-ttu-id="83a48-290">와일드 카드 수정자 \***/** 는 경로의 시작 부분 에서만 사용할 수 있으며 지정 된 url의 모든 URL 세그먼트와 일치 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-290">The wildcard modifier \***/** can only be used at the beginning of the path, and will match all URL segments under the specified URL.</span></span>
+ <span data-ttu-id="83a48-291">경로는 문서 라이브러리, 폴더 또는 사이트를 가리킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-291">The path can point to a document library, folder or site.</span></span> <span data-ttu-id="83a48-292">예를 들어 경로 _\*/site1_ 은 사이트 아래의 모든 문서 라이브러리와 일치 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-292">For example, the path _\*/site1_ will match all the document libraries under the site.</span></span>

<span data-ttu-id="83a48-293">특정 상대 경로를 사용 하 여 원본을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-293">You can add an origin with a specific relative path.</span></span> <span data-ttu-id="83a48-294">전체 경로를 사용 하 여 원점을 추가할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-294">You cannot add an origin using the full path.</span></span>

<span data-ttu-id="83a48-295">이 예제에서는 특정 사이트에 siteassets 라이브러리의 개인 출처를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-295">This example adds a private origin of the siteassets library on a specific site:</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

<span data-ttu-id="83a48-296">이 예제에서는 사이트 모음의 사이트 자산 라이브러리에 _folder1_ 폴더의 개인 출처를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-296">This example adds a private origin of the _folder1_ folder in the site collection's site assets library:</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/test/siteassets/folder1
```

<span data-ttu-id="83a48-297">경로에 공백이 있으면 경로를 큰따옴표로 묶고 URL 인코딩 %20로 공간을 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-297">If there is a space in the path, you can either surround the path in double quotes or replace the space with the URL encoding %20.</span></span> <span data-ttu-id="83a48-298">다음은 사이트 모음의 사이트 자산 라이브러리에서 _폴더 1_ 폴더의 개인 출처를 추가 하는 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-298">The following examples add a private origin of the _folder 1_ folder in the site collection's site assets library:</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/test/siteassets/folder%201
```

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl "sites/test/siteassets/folder 1"
```

<span data-ttu-id="83a48-299">이 명령 및 구문에 대 한 자세한 내용은 [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/library/mt790772.aspx)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="83a48-299">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/library/mt790772.aspx).</span></span>

> [!NOTE]
> <span data-ttu-id="83a48-300">비공개 원본의 경우 원본에서 공유 되는 자산은 CDN에서 액세스 하려면 먼저 주 버전을 게시 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-300">In private origins, assets being shared from an origin must have a major version published before they can be accessed from the CDN.</span></span>
  
<span data-ttu-id="83a48-301">명령을 실행 하면 시스템에서 데이터 센터 전체에서 구성을 동기화 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-301">Once you've run the command, the system synchronizes the configuration across the datacenter.</span></span> <span data-ttu-id="83a48-302">최대 15 분까지 소요 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-302">This can take up to 15 minutes.</span></span>

<span data-ttu-id="83a48-303"><a name="ExamplePublicOrigin"> </a></span><span class="sxs-lookup"><span data-stu-id="83a48-303"><a name="ExamplePublicOrigin"> </a></span></span>
### <a name="example-configure-a-public-origin-for-your-master-pages-and-for-your-style-library-for-sharepoint-online"></a><span data-ttu-id="83a48-304">예: 마스터 페이지에 대 한 공용 원점과 SharePoint Online에 대 한 스타일 라이브러리에 대해 구성</span><span class="sxs-lookup"><span data-stu-id="83a48-304">Example: Configure a public origin for your master pages and for your style library for SharePoint Online</span></span>

<span data-ttu-id="83a48-305">일반적으로 이러한 출처는 Office 365 CDN을 사용 하도록 설정 하면 기본적으로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-305">Normally, these origins are set up for you by default when you enable the Office 365 CDN.</span></span> <span data-ttu-id="83a48-306">그러나 수동으로 사용 하도록 설정 하려는 경우 다음 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-306">However, if you want to enable them manually, follow these steps.</span></span>
  
+ <span data-ttu-id="83a48-307">**SPOTenantCdnOrigin** cmdlet을 사용 하면 스타일 라이브러리를 공용 원점으로 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-307">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the style library as a public origin.</span></span>

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */style%20library
  ```

+ <span data-ttu-id="83a48-308">**SPOTenantCdnOrigin** cmdlet을 사용 하면 마스터 페이지를 공공 원점으로 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-308">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the master pages as a public origin.</span></span>

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
  ```

<span data-ttu-id="83a48-309">이 명령 및 구문에 대 한 자세한 내용은 [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/library/mt790772.aspx)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="83a48-309">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/library/mt790772.aspx).</span></span>

<span data-ttu-id="83a48-310">명령을 실행 하면 시스템에서 데이터 센터 전체에서 구성을 동기화 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-310">Once you've run the command, the system synchronizes the configuration across the datacenter.</span></span> <span data-ttu-id="83a48-311">최대 15 분까지 소요 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-311">This can take up to 15 minutes.</span></span>

<span data-ttu-id="83a48-312"><a name="ExamplePrivateOrigin"> </a></span><span class="sxs-lookup"><span data-stu-id="83a48-312"><a name="ExamplePrivateOrigin"> </a></span></span>
### <a name="example-configure-a-private-origin-for-your-site-assets-site-pages-and-publishing-images-for-sharepoint-online"></a><span data-ttu-id="83a48-313">예: SharePoint Online에 대 한 사이트 자산, 사이트 페이지 및 게시 이미지에 대 한 개인 출처 구성</span><span class="sxs-lookup"><span data-stu-id="83a48-313">Example: Configure a private origin for your site assets, site pages, and publishing images for SharePoint Online</span></span>

+ <span data-ttu-id="83a48-314">**SPOTenantCdnOrigin** cmdlet을 사용 하면 사이트 자산 폴더를 전용 원본으로 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-314">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the site assets folder as a private origin.</span></span>

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */siteassets
  ```

+ <span data-ttu-id="83a48-315">**SPOTenantCdnOrigin** cmdlet을 사용 하면 사이트 페이지 폴더를 전용 원본으로 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-315">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the site pages folder as a private origin.</span></span>

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */sitepages
  ```

+ <span data-ttu-id="83a48-316">**SPOTenantCdnOrigin** cmdlet을 사용 하면 게시 이미지 폴더를 전용 원본으로 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-316">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the publishing images folder as a private origin.</span></span>

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */publishingimages
  ```

<span data-ttu-id="83a48-317">이 명령 및 구문에 대 한 자세한 내용은 [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/library/mt790772.aspx)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="83a48-317">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/library/mt790772.aspx).</span></span>

<span data-ttu-id="83a48-318">명령을 실행 하면 시스템에서 데이터 센터 전체에서 구성을 동기화 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-318">Once you've run the command, the system synchronizes the configuration across the datacenter.</span></span> <span data-ttu-id="83a48-319">최대 15 분까지 소요 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-319">This can take up to 15 minutes.</span></span>

<span data-ttu-id="83a48-320"><a name="ExamplePrivateOriginSiteCollection"> </a></span><span class="sxs-lookup"><span data-stu-id="83a48-320"><a name="ExamplePrivateOriginSiteCollection"> </a></span></span>
### <a name="example-configure-a-private-origin-for-a-site-collection-for-sharepoint-online"></a><span data-ttu-id="83a48-321">예: SharePoint Online에 대 한 사이트 모음에 대 한 개인 원본 구성</span><span class="sxs-lookup"><span data-stu-id="83a48-321">Example: Configure a private origin for a site collection for SharePoint Online</span></span>

<span data-ttu-id="83a48-322">**SPOTenantCdnOrigin** cmdlet을 사용 하면 사이트 모음을 전용 원본으로 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-322">Use the **Add-SPOTenantCdnOrigin** cmdlet to define a site collection as a private origin.</span></span> <span data-ttu-id="83a48-323">예:</span><span class="sxs-lookup"><span data-stu-id="83a48-323">For example:</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

<span data-ttu-id="83a48-324">이 명령 및 구문에 대 한 자세한 내용은 [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/library/mt790772.aspx)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="83a48-324">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/library/mt790772.aspx).</span></span>
  
<span data-ttu-id="83a48-325">명령을 실행 하면 시스템에서 데이터 센터 전체에서 구성을 동기화 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-325">Once you've run the command, the system synchronizes the configuration across the datacenter.</span></span> <span data-ttu-id="83a48-326">SharePoint Online 테 넌 트가 CDN 서비스에 연결할 때 예상 되는 _구성 보류 중인_ 메시지가 표시 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-326">You may see a _Configuration pending_ message which is expected as the SharePoint Online tenant connects to the CDN service.</span></span> <span data-ttu-id="83a48-327">최대 15 분까지 소요 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-327">This can take up to 15 minutes.</span></span>

<span data-ttu-id="83a48-328"><a name="CDNManage"> </a></span><span class="sxs-lookup"><span data-stu-id="83a48-328"><a name="CDNManage"> </a></span></span>
### <a name="manage-the-office-365-cdn"></a><span data-ttu-id="83a48-329">Office 365 CDN 관리</span><span class="sxs-lookup"><span data-stu-id="83a48-329">Manage the Office 365 CDN</span></span>

<span data-ttu-id="83a48-330">CDN을 설정한 후에는이 섹션에 설명 된 대로 콘텐츠를 업데이트 하거나 필요에 따라 변경 하 여 구성을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-330">Once you've set up the CDN, you can make changes to your configuration as you update content or as your needs change, as described in this section.</span></span>
  
<span data-ttu-id="83a48-331"><a name="Office365CDNforSPOaddremoveasset"> </a></span><span class="sxs-lookup"><span data-stu-id="83a48-331"><a name="Office365CDNforSPOaddremoveasset"> </a></span></span>
#### <a name="add-update-or-remove-assets-from-the-office-365-cdn"></a><span data-ttu-id="83a48-332">Office 365 CDN에서 자산 추가, 업데이트 또는 제거</span><span class="sxs-lookup"><span data-stu-id="83a48-332">Add, update, or remove assets from the Office 365 CDN</span></span>

<span data-ttu-id="83a48-333">설정 단계를 완료 한 후에는 새 자산을 추가 하 고 원할 때마다 기존 자산을 업데이트 하거나 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-333">Once you've completed the setup steps, you can add new assets, and update or remove existing assets whenever you want.</span></span> <span data-ttu-id="83a48-334">폴더 또는 SharePoint 라이브러리에서 원본으로 식별 한 자산을 변경 하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-334">Just make your changes to the assets in the folder or SharePoint library that you identified as an origin.</span></span> <span data-ttu-id="83a48-335">새 자산을 추가 하는 경우에는 CDN을 통해 즉시 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-335">If you add a new asset, it is available through the CDN immediately.</span></span> <span data-ttu-id="83a48-336">그러나 자산을 업데이트 하는 경우 새 복사본을 전파 하 고 CDN에서 사용할 수 있게 되는 데 최대 15 분이 걸립니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-336">However, if you update the asset, it will take up to 15 minutes for the new copy to propagate and become available in the CDN.</span></span>
  
<span data-ttu-id="83a48-337">원본 위치를 검색 해야 하는 경우 **SPOTenantCdnOrigins** cmdlet을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-337">If you need to retrieve the location of the origin, you can use the **Get-SPOTenantCdnOrigins** cmdlet.</span></span> <span data-ttu-id="83a48-338">이 cmdlet을 사용 하는 방법에 대 한 자세한 내용은 [SPOTenantCdnOrigins](https://technet.microsoft.com/library/mt790770.aspx)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="83a48-338">For information on how to use this cmdlet, see [Get-SPOTenantCdnOrigins](https://technet.microsoft.com/library/mt790770.aspx).</span></span>

<span data-ttu-id="83a48-339"><a name="Office365CDNforSPORemoveOrigin"> </a></span><span class="sxs-lookup"><span data-stu-id="83a48-339"><a name="Office365CDNforSPORemoveOrigin"> </a></span></span>
#### <a name="remove-an-origin-from-the-office-365-cdn"></a><span data-ttu-id="83a48-340">Office 365 CDN에서 원본 제거</span><span class="sxs-lookup"><span data-stu-id="83a48-340">Remove an origin from the Office 365 CDN</span></span>

<span data-ttu-id="83a48-341">원본으로 식별 한 폴더 또는 SharePoint 라이브러리에 대 한 액세스 권한을 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-341">You can remove access to a folder or SharePoint library that you identified as an origin.</span></span> <span data-ttu-id="83a48-342">이 작업을 수행 하려면 **SPOTenantCdnOrigin** cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-342">To do this, use the **Remove-SPOTenantCdnOrigin** cmdlet.</span></span>

``` powershell
Remove-SPOTenantCdnOrigin -OriginUrl <path> -CdnType <Public | Private | Both>
```

<span data-ttu-id="83a48-343">이 cmdlet을 사용 하는 방법에 대 한 자세한 내용은 [SPOTenantCdnOrigin](https://technet.microsoft.com/library/mt790761.aspx)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="83a48-343">For information on how to use this cmdlet, see [Remove-SPOTenantCdnOrigin](https://technet.microsoft.com/library/mt790761.aspx).</span></span>

<span data-ttu-id="83a48-344"><a name="Office365CDNforSPORemoveOrigin"> </a></span><span class="sxs-lookup"><span data-stu-id="83a48-344"><a name="Office365CDNforSPORemoveOrigin"> </a></span></span>
#### <a name="modify-an-origin-in-the-office-365-cdn"></a><span data-ttu-id="83a48-345">Office 365 CDN에서 원본 수정</span><span class="sxs-lookup"><span data-stu-id="83a48-345">Modify an origin in the Office 365 CDN</span></span>

<span data-ttu-id="83a48-346">만든 출처는 수정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-346">You cannot modify an origin you've created.</span></span> <span data-ttu-id="83a48-347">대신 원점을 제거한 다음 새 원본을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-347">Instead, remove the origin and then add a new one.</span></span> <span data-ttu-id="83a48-348">자세한 내용은 [Office 365 CDN에서 출처를 제거](use-office-365-cdn-with-spo.md#Office365CDNforSPORemoveOrigin) 하 고 [자산의 출처를 추가](use-office-365-cdn-with-spo.md#Office365CDNforSPOOrigin)하는 방법을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="83a48-348">For more information, see [To remove an origin from the Office 365 CDN](use-office-365-cdn-with-spo.md#Office365CDNforSPORemoveOrigin) and [To add an origin for your assets](use-office-365-cdn-with-spo.md#Office365CDNforSPOOrigin).</span></span>

<span data-ttu-id="83a48-349"><a name="Office365CDNforSPODisable"> </a></span><span class="sxs-lookup"><span data-stu-id="83a48-349"><a name="Office365CDNforSPODisable"> </a></span></span>
#### <a name="disable-the-office-365-cdn"></a><span data-ttu-id="83a48-350">Office 365 CDN 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="83a48-350">Disable the Office 365 CDN</span></span>

<span data-ttu-id="83a48-351">**SPOTenantCdnEnabled** cmdlet을 사용 하 여 조직에 CDN을 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-351">Use the **Set-SPOTenantCdnEnabled** cmdlet to disable the CDN for your organization.</span></span> <span data-ttu-id="83a48-352">CDN에 대 한 공용 및 전용 원본을 모두 사용 하는 경우에는 다음 예제와 같이 cmdlet을 두 번 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-352">If you have both the public and private origins enabled for the CDN, you need to run the cmdlet twice as shown in the following examples.</span></span>
  
<span data-ttu-id="83a48-353">CDN에서 public 원본임을 사용 하지 않도록 설정 하려면 다음 명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-353">To disable use of public origins in the CDN, enter the following command:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType Public -Enable $false
```

<span data-ttu-id="83a48-354">CDN에서 비공개 원본을 사용 하지 않도록 설정 하려면 다음 명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-354">To disable use of the private origins in the CDN, enter the following command:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType Private -Enable $false
```

<span data-ttu-id="83a48-355">이 cmdlet에 대 한 자세한 내용은 [SPOTenantCdnEnabled](https://technet.microsoft.com/library/mt790765.aspx)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="83a48-355">For more information about this cmdlet, see [Set-SPOTenantCdnEnabled](https://technet.microsoft.com/library/mt790765.aspx).</span></span>

</details>

<span data-ttu-id="83a48-356"><a name="CDNSetupinPnPPosh"> </a></span><span class="sxs-lookup"><span data-stu-id="83a48-356"><a name="CDNSetupinPnPPosh"> </a></span></span>
## <a name="set-up-and-configure-the-office-365-cdn-by-using-pnp-powershell"></a><span data-ttu-id="83a48-357">PnP PowerShell을 사용 하 여 Office 365 CDN을 설정 하 고 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-357">Set up and configure the Office 365 CDN by using PnP PowerShell</span></span>

<span data-ttu-id="83a48-358">이 섹션의 절차에서는 PnP PowerShell을 사용 하 여 SharePoint Online에 연결 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-358">The procedures in this section require you to use PnP PowerShell to connect to SharePoint Online.</span></span> <span data-ttu-id="83a48-359">자세한 내용은 [PnP PowerShell 시작](https://github.com/SharePoint/PnP-PowerShell#getting-started)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="83a48-359">For instructions, see [Getting started with PnP PowerShell](https://github.com/SharePoint/PnP-PowerShell#getting-started).</span></span>

<span data-ttu-id="83a48-360">다음 단계에 따라 PnP PowerShell을 사용 하 여 SharePoint Online에서 자산을 호스트 하도록 CDN을 설정 하 고 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-360">Complete these steps to set up and configure the CDN to host your assets in SharePoint Online using PnP PowerShell.</span></span>

<details>
  <summary><span data-ttu-id="83a48-361">클릭 하 여 확장</span><span class="sxs-lookup"><span data-stu-id="83a48-361">Click to expand</span></span></summary>

### <a name="enable-your-organization-to-use-the-office-365-cdn"></a><span data-ttu-id="83a48-362">조직이 Office 365 CDN을 사용 하도록 설정</span><span class="sxs-lookup"><span data-stu-id="83a48-362">Enable your organization to use the Office 365 CDN</span></span>

<span data-ttu-id="83a48-363">테 넌 트 CDN 설정을 변경 하기 전에 Office 365 테 넌 트에서 개인 CDN 구성의 현재 상태를 검색 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-363">Before you make changes to the tenant CDN settings, you should retrieve the current status of the private CDN configuration in your Office 365 tenant.</span></span> <span data-ttu-id="83a48-364">PnP PowerShell을 사용 하 여 테 넌 트에 연결:</span><span class="sxs-lookup"><span data-stu-id="83a48-364">Connect to your tenant using PnP PowerShell:</span></span>

``` powershell
Connect-PnPOnline -Url https://contoso-admin.sharepoint.com -UseWebLogin
```

<span data-ttu-id="83a48-365">이제 **-Pnpten앤틸리스 Cdnenabled** cmdlet을 사용 하 여 테 넌 트에서 CDN 상태 설정을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-365">Now use the **Get-PnPTenantCdnEnabled** cmdlet to retrieve the CDN status settings from the tenant:</span></span>

``` powershell
Get-PnPTenantCdnEnabled -CdnType <Public | Private>
```

<span data-ttu-id="83a48-366">지정한 CdnType에 대 한 CDN의 상태가 화면에 출력 됩니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-366">The status of the CDN for the specified CdnType will output to the screen.</span></span>

<span data-ttu-id="83a48-367">조직이 Office 365 CDN을 사용 하도록 설정 하려면 **Pnpten앤틸리스 Cdnenabled** cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-367">Use the **Set-PnPTenantCdnEnabled** cmdlet to enable your organization to use the Office 365 CDN.</span></span> <span data-ttu-id="83a48-368">조직의 공용 원본, 전용 원본 또는 두 가지 모두를 동시에 사용 하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-368">You can enable your organization to use public origins, private origins, or both at at the same time.</span></span> <span data-ttu-id="83a48-369">또한이 기능을 사용 하도록 설정 하면 기본 원본 설정을 건너뛰도록 CDN을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-369">You can also configure the CDN to skip the setup of default origins when you enable it.</span></span> <span data-ttu-id="83a48-370">이 항목의 설명에 따라 나중에 이러한 원본을 언제 든 지 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-370">You can always add these origins later as described in this topic.</span></span>
  
<span data-ttu-id="83a48-371">PnP PowerShell:</span><span class="sxs-lookup"><span data-stu-id="83a48-371">In PnP PowerShell:</span></span>

``` powershell
Set-PnPTenantCdnEnabled -CdnType <Public | Private | Both> -Enable $true
```

<span data-ttu-id="83a48-372">예를 들어 조직에서 공용 및 개인 원본을 둘 다 사용할 수 있도록 설정 하려면 다음 명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-372">For example, to enable your organization to use both public and private origins, type the following command:</span></span>

``` powershell
Set-PnPTenantCdnEnabled -CdnType Both -Enable $true
```

<span data-ttu-id="83a48-373">조직이 공용 및 개인 원본을 모두 사용할 수 있도록 설정 하 고 기본 원본을 설정 하지 않으려면 다음 명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-373">To enable your organization to use both public and private origins but skip setting up the default origins, type the following command:</span></span>

``` powershell
Set-PnPTenantCdnEnabled -CdnType Both -Enable $true -NoDefaultOrigins
```

<span data-ttu-id="83a48-374">Office 365 CDN을 사용 하도록 설정 하는 경우 기본적으로 프로 비전 되는 원본에 대 한 정보 및 기본 원본 설정을 건너뛰는 경우 발생할 수 있는 영향에 대 한 자세한 내용은 [DEFAULT CDN 원본임](use-office-365-cdn-with-spo.md#default-cdn-origins) 을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="83a48-374">See [Default CDN origins](use-office-365-cdn-with-spo.md#default-cdn-origins) for information about the origins that are provisioned by default when you enable the Office 365 CDN, and the potential impact of skipping the setup of default origins.</span></span>

<span data-ttu-id="83a48-375">조직에서 공용 원본을 사용 하도록 설정 하려면 다음 명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-375">To enable your organization to use public origins, type the following command:</span></span>

``` powershell
Set-PnPTenantCdnEnabled -CdnType Public -Enable $true
```

<span data-ttu-id="83a48-376">조직에서 전용 원본을 사용 하도록 설정 하려면 다음 명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-376">To enable your organization to use private origins, type the following command:</span></span>

``` powershell
Set-PnPTenantCdnEnabled -CdnType Private -Enable $true
```

<span data-ttu-id="83a48-377">이 cmdlet에 대 한 자세한 내용은 [Set-Pnpten앤틸리스 Cdnenabled](https://docs.microsoft.com/powershell/module/sharepoint-pnp/set-pnptenantcdnenabled)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="83a48-377">For more information about this cmdlet, see [Set-PnPTenantCdnEnabled](https://docs.microsoft.com/powershell/module/sharepoint-pnp/set-pnptenantcdnenabled).</span></span>

<span data-ttu-id="83a48-378"><a name="Office365CDNforPnPPoshFileType"> </a></span><span class="sxs-lookup"><span data-stu-id="83a48-378"><a name="Office365CDNforPnPPoshFileType"> </a></span></span>
### <a name="change-the-list-of-file-types-to-include-in-the-office-365-cdn-optional"></a><span data-ttu-id="83a48-379">Office 365 CDN에 포함할 파일 형식 목록 변경 (선택 사항)</span><span class="sxs-lookup"><span data-stu-id="83a48-379">Change the list of file types to include in the Office 365 CDN (Optional)</span></span>

> [!TIP]
> <span data-ttu-id="83a48-380">**Pnpten앤틸리스 Cdnpolicy** cmdlet을 사용 하 여 파일 형식을 정의 하는 경우 현재 정의 된 목록을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-380">When you define file types by using the **Set-PnPTenantCdnPolicy** cmdlet, you overwrite the currently defined list.</span></span> <span data-ttu-id="83a48-381">목록에 다른 파일 형식을 추가 하려면 먼저 cmdlet을 사용 하 여 이미 허용 된 파일 형식을 확인 하 여 새 파일과 함께 목록에 포함 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-381">If you want to add additional file types to the list, use the cmdlet first to find out what file types are already allowed and include them in the list along with your new ones.</span></span>
  
<span data-ttu-id="83a48-382">**설정-Pnpten앤틸리스 Cdnpolicy** cmdlet을 사용 하 여 CDN에서 공용 및 전용 원본으로 호스트할 수 있는 정적 파일 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-382">Use the **Set-PnPTenantCdnPolicy** cmdlet to define static file types that can be hosted by public and private origins in the CDN.</span></span> <span data-ttu-id="83a48-383">기본적으로 일반 에셋 유형 (예: .css, .gif, .jpg, .js)을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-383">By default, common asset types are allowed, for example .css, .gif, .jpg, and .js.</span></span>

<span data-ttu-id="83a48-384">PnP PowerShell:</span><span class="sxs-lookup"><span data-stu-id="83a48-384">In PnP PowerShell:</span></span>

``` powershell
Set-PnPTenantCdnPolicy -CdnType <Public | Private> -PolicyType IncludeFileExtensions -PolicyValue "<Comma-separated list of file types >"
```

<span data-ttu-id="83a48-385">예를 들어 CDN에서 .css 및 .png 파일을 호스팅할 수 있도록 설정 하려면 다음 명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-385">For example, to enable the CDN to host .css and .png files, you would enter the command:</span></span>

``` powershell
Set-PnPTenantCdnPolicy -CdnType Private -PolicyType IncludeFileExtensions -PolicyValue "CSS,PNG"
```

<span data-ttu-id="83a48-386">CDN에서 현재 허용 되는 파일 형식을 확인 하려면 **Get-Pnpten앤틸리스 Cdn정책만** cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-386">To see what file types are currently allowed by the CDN, use the **Get-PnPTenantCdnPolicies** cmdlet:</span></span>

``` powershell
Get-PnPTenantCdnPolicies -CdnType <Public | Private>
```

<span data-ttu-id="83a48-387">이러한 cmdlet에 대 한 자세한 내용은 [Set-Pnpten앤틸리스 Cdnpolicy](https://docs.microsoft.com/powershell/module/sharepoint-pnp/set-pnptenantcdnpolicy) 및 [Get-Pnpten앤틸리스 cdn정책도](https://docs.microsoft.com/powershell/module/sharepoint-pnp/get-pnptenantcdnpolicies)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="83a48-387">For more information about these cmdlets, see [Set-PnPTenantCdnPolicy](https://docs.microsoft.com/powershell/module/sharepoint-pnp/set-pnptenantcdnpolicy) and [Get-PnPTenantCdnPolicies](https://docs.microsoft.com/powershell/module/sharepoint-pnp/get-pnptenantcdnpolicies).</span></span>

<span data-ttu-id="83a48-388"><a name="Office365CDNforPnPPoshSiteClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="83a48-388"><a name="Office365CDNforPnPPoshSiteClassification"> </a></span></span>
### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn-optional"></a><span data-ttu-id="83a48-389">Office 365 CDN에서 제외 하려는 사이트 분류 목록 변경 (선택 사항)</span><span class="sxs-lookup"><span data-stu-id="83a48-389">Change the list of site classifications you want to exclude from the Office 365 CDN (Optional)</span></span>

> [!TIP]
> <span data-ttu-id="83a48-390">**-Pnpten앤틸리스 Cdnpolicy** cmdlet을 사용 하 여 사이트 분류를 제외 하는 경우 현재 정의 된 목록을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-390">When you exclude site classifications by using the **Set-PnPTenantCdnPolicy** cmdlet, you overwrite the currently defined list.</span></span> <span data-ttu-id="83a48-391">추가 사이트 분류를 제외 하려면 먼저 cmdlet을 사용 하 여 이미 제외 된 분류를 확인 한 다음 새 항목과 함께 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-391">If you want to exclude additional site classifications, use the cmdlet first to find out what classifications are already excluded and then add them along with your new ones.</span></span>

<span data-ttu-id="83a48-392">사용자가 CDN을 통해 사용 하지 않도록 하려는 사이트 분류를 제외 하려면 **Pnpten앤틸리스 Cdnpolicy** cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-392">Use the **Set-PnPTenantCdnPolicy** cmdlet to exclude site classifications that you do not want to make available over the CDN.</span></span> <span data-ttu-id="83a48-393">기본적으로 사이트 분류는 제외 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-393">By default, no site classifications are excluded.</span></span>

<span data-ttu-id="83a48-394">PnP PowerShell:</span><span class="sxs-lookup"><span data-stu-id="83a48-394">In PnP PowerShell:</span></span>

``` powershell
Set-PnPTenantCdnPolicy -CdnType <Public | Private> -PolicyType ExcludeRestrictedSiteClassifications  -PolicyValue "<Comma-separated list of site classifications>"
```

<span data-ttu-id="83a48-395">현재 제한 되는 사이트 분류를 확인 하려면 **Get-Pnpten앤틸리스 Cdn정책만** cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-395">To see what site classifications are currently restricted, use the **Get-PnPTenantCdnPolicies** cmdlet:</span></span>

``` powershell
Get-PnPTenantCdnPolicies -CdnType <Public | Private>
```

<span data-ttu-id="83a48-396">반환 되는 속성은 _IncludeFileExtensions_, _ExcludeRestrictedSiteClassifications_ 및 _excludeifnoscriptdisabled_입니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-396">The properties that will be returned are _IncludeFileExtensions_, _ExcludeRestrictedSiteClassifications_ and _ExcludeIfNoScriptDisabled_.</span></span>

<span data-ttu-id="83a48-397">_IncludeFileExtensions_ 속성에는 CDN에서 처리할 파일 확장명 목록이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-397">The _IncludeFileExtensions_ property contains the list of file extensions that will be served from the CDN.</span></span>

> [!NOTE]
> <span data-ttu-id="83a48-398">기본 파일 확장명은 public 및 private과 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-398">The default file extensions are different between public and private.</span></span>

<span data-ttu-id="83a48-399">_ExcludeRestrictedSiteClassifications_ 속성은 CDN에서 제외 하려는 사이트 분류를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-399">The _ExcludeRestrictedSiteClassifications_ property contains the site classifications that you want to exclude from the CDN.</span></span> <span data-ttu-id="83a48-400">예를 들어 해당 분류가 적용 된 사이트의 콘텐츠가 CDN에서 처리 되지 않도록 **비밀 우편** 으로 표시 된 사이트를 제외할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-400">For example, you can exclude sites marked as **Confidential** so content from sites with that classification applied will not be served from the CDN.</span></span>

<span data-ttu-id="83a48-401">_Excludeifnoscriptdisabled_ 속성은 사이트 수준 _noscript_ 특성 설정에 따라 CDN에서 콘텐츠를 제외 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-401">The _ExcludeIfNoScriptDisabled_ property excludes content from the CDN based on the site-level _NoScript_ attribute settings.</span></span> <span data-ttu-id="83a48-402">기본적으로 _최신_ 사이트에는 _Noscript_ 특성이 **사용** 으로 설정 되 고 _클래식_ 사이트에는 사용 **되지** 않습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-402">By default, the _NoScript_ attribute is set to **Enabled** for _Modern_ sites and **Disabled** for _Classic_ sites.</span></span> <span data-ttu-id="83a48-403">이것은 테 넌 트 설정에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-403">This depends on your tenant settings.</span></span>

<span data-ttu-id="83a48-404">이러한 cmdlet에 대 한 자세한 내용은 [Set-Pnpten앤틸리스 Cdnpolicy](https://docs.microsoft.com/powershell/module/sharepoint-pnp/set-pnptenantcdnpolicy) 및 [Get-Pnpten앤틸리스 cdn정책도](https://docs.microsoft.com/powershell/module/sharepoint-pnp/get-pnptenantcdnpolicies)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="83a48-404">For more information about these cmdlets, see [Set-PnPTenantCdnPolicy](https://docs.microsoft.com/powershell/module/sharepoint-pnp/set-pnptenantcdnpolicy) and [Get-PnPTenantCdnPolicies](https://docs.microsoft.com/powershell/module/sharepoint-pnp/get-pnptenantcdnpolicies).</span></span>

<span data-ttu-id="83a48-405"><a name="Office365CDNforPnPPoshOrigin"> </a></span><span class="sxs-lookup"><span data-stu-id="83a48-405"><a name="Office365CDNforPnPPoshOrigin"> </a></span></span>
### <a name="add-an-origin-for-your-assets"></a><span data-ttu-id="83a48-406">자산에 대 한 근원 추가</span><span class="sxs-lookup"><span data-stu-id="83a48-406">Add an origin for your assets</span></span>

<span data-ttu-id="83a48-407">**추가-Pnpten앤틸리스 Cdn근원** cmdlet을 사용 하 여 원본을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-407">Use the **Add-PnPTenantCdnOrigin** cmdlet to define an origin.</span></span> <span data-ttu-id="83a48-408">여러 원본을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-408">You can define multiple origins.</span></span> <span data-ttu-id="83a48-409">원점은 CDN에서 호스팅할 자산이 포함 된 SharePoint 라이브러리 또는 폴더를 가리키는 URL입니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-409">The origin is a URL that points to a SharePoint library or folder that contains the assets that you want to be hosted by the CDN.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="83a48-410">사용자 정보가 포함 된 리소스를 배치 하거나 조직에서 공용 원본으로 중요 한 것으로 간주 해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-410">You should never place resources that contain user information or are considered sensitive to your organization in a public origin.</span></span>

``` powershell
Add-PnPTenantCdnOrigin -CdnType <Public | Private> -OriginUrl <path>
```

<span data-ttu-id="83a48-411">_Path_ 값은 자산이 포함 된 라이브러리 또는 폴더에 대 한 상대 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-411">The value of _path_ is the relative path to the library or folder that contains the assets.</span></span> <span data-ttu-id="83a48-412">상대 경로 외에도 와일드 카드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-412">You can use wildcards in addition to relative paths.</span></span> <span data-ttu-id="83a48-413">원본 URL 앞에는 와일드 카드를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-413">Origins support wildcards prepended to the URL.</span></span> <span data-ttu-id="83a48-414">이를 통해 여러 사이트에 걸쳐 있는 원본을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-414">This allows you to create origins that span multiple sites.</span></span> <span data-ttu-id="83a48-415">예를 들어 모든 사이트에 대 한 masterpages 폴더의 모든 자산을 CDN 내의 공용 근원으로 포함 하려면 다음 명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-415">For example, to include all of the assets in the masterpages folder for all of your sites as a public origin within the CDN, type the following command:</span></span>

``` powershell
Add-PnPTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
```

+ <span data-ttu-id="83a48-416">와일드 카드 수정자 \***/** 는 경로의 시작 부분 에서만 사용할 수 있으며 지정 된 url의 모든 URL 세그먼트와 일치 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-416">The wildcard modifier \***/** can only be used at the beginning of the path, and will match all URL segments under the specified URL.</span></span>
+ <span data-ttu-id="83a48-417">경로는 문서 라이브러리, 폴더 또는 사이트를 가리킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-417">The path can point to a document library, folder or site.</span></span> <span data-ttu-id="83a48-418">예를 들어 경로 _\*/site1_ 은 사이트 아래의 모든 문서 라이브러리와 일치 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-418">For example, the path _\*/site1_ will match all the document libraries under the site.</span></span>

<span data-ttu-id="83a48-419">특정 상대 경로를 사용 하 여 원본을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-419">You can add an origin with a specific relative path.</span></span> <span data-ttu-id="83a48-420">전체 경로를 사용 하 여 원점을 추가할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-420">You cannot add an origin using the full path.</span></span>

<span data-ttu-id="83a48-421">다음은 사이트 자산 라이브러리의 개인 출처를 특정 사이트에 추가 하는 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-421">This example adds a private origin of the site assets library on a specific site:</span></span>

``` powershell
Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

<span data-ttu-id="83a48-422">이 예제에서는 사이트 모음의 사이트 자산 라이브러리에 _folder1_ 폴더의 개인 출처를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-422">This example adds a private origin of the _folder1_ folder in the site collection's site assets library:</span></span>

``` powershell
Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl sites/test/siteassets/folder1
```

<span data-ttu-id="83a48-423">경로에 공백이 있으면 경로를 큰따옴표로 묶고 URL 인코딩 %20로 공간을 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-423">If there is a space in the path, you can either surround the path in double quotes or replace the space with the URL encoding %20.</span></span> <span data-ttu-id="83a48-424">다음은 사이트 모음의 사이트 자산 라이브러리에서 _폴더 1_ 폴더의 개인 출처를 추가 하는 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-424">The following examples add a private origin of the _folder 1_ folder in the site collection's site assets library:</span></span>

``` powershell
Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl sites/test/siteassets/folder%201
```

``` powershell
Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl "sites/test/siteassets/folder 1"
```

<span data-ttu-id="83a48-425">이 명령 및 구문에 대 한 자세한 내용은 [추가-Pnpten앤틸리스 Cdn근원](https://docs.microsoft.com/powershell/module/sharepoint-pnp/add-pnptenantcdnorigin)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="83a48-425">For more information about this command and its syntax, see [Add-PnPTenantCdnOrigin](https://docs.microsoft.com/powershell/module/sharepoint-pnp/add-pnptenantcdnorigin).</span></span>

> [!NOTE]
> <span data-ttu-id="83a48-426">비공개 원본의 경우 원본에서 공유 되는 자산은 CDN에서 액세스 하려면 먼저 주 버전을 게시 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-426">In private origins, assets being shared from an origin must have a major version published before they can be accessed from the CDN.</span></span>
  
<span data-ttu-id="83a48-427">명령을 실행 하면 시스템에서 데이터 센터 전체에서 구성을 동기화 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-427">Once you've run the command, the system synchronizes the configuration across the datacenter.</span></span> <span data-ttu-id="83a48-428">최대 15 분까지 소요 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-428">This can take up to 15 minutes.</span></span>

<span data-ttu-id="83a48-429"><a name="ExamplePublicOriginPnPPosh"> </a></span><span class="sxs-lookup"><span data-stu-id="83a48-429"><a name="ExamplePublicOriginPnPPosh"> </a></span></span>
### <a name="example-configure-a-public-origin-for-your-master-pages-and-for-your-style-library-for-sharepoint-online"></a><span data-ttu-id="83a48-430">예: 마스터 페이지에 대 한 공용 원점과 SharePoint Online에 대 한 스타일 라이브러리에 대해 구성</span><span class="sxs-lookup"><span data-stu-id="83a48-430">Example: Configure a public origin for your master pages and for your style library for SharePoint Online</span></span>

<span data-ttu-id="83a48-431">일반적으로 이러한 출처는 Office 365 CDN을 사용 하도록 설정 하면 기본적으로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-431">Normally, these origins are set up for you by default when you enable the Office 365 CDN.</span></span> <span data-ttu-id="83a48-432">그러나 수동으로 사용 하도록 설정 하려는 경우 다음 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-432">However, if you want to enable them manually, follow these steps.</span></span>
  
+ <span data-ttu-id="83a48-433">**추가-Pnpten앤틸리스 Cdn근원** cmdlet을 사용 하 여 스타일 라이브러리를 공용 원점으로 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-433">Use the **Add-PnPTenantCdnOrigin** cmdlet to define the style library as a public origin.</span></span>

``` powershell
  Add-PnPTenantCdnOrigin -CdnType Public -OriginUrl */style%20library
  ```

+ <span data-ttu-id="83a48-434">**추가-Pnpten앤틸리스 Cdn근원** cmdlet을 사용 하 여 마스터 페이지를 공공 원점으로 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-434">Use the **Add-PnPTenantCdnOrigin** cmdlet to define the master pages as a public origin.</span></span>

``` powershell
  Add-PnPTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
  ```

<span data-ttu-id="83a48-435">이 명령 및 구문에 대 한 자세한 내용은 [추가-Pnpten앤틸리스 Cdn근원](https://docs.microsoft.com/powershell/module/sharepoint-pnp/add-pnptenantcdnorigin)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="83a48-435">For more information about this command and its syntax, see [Add-PnPTenantCdnOrigin](https://docs.microsoft.com/powershell/module/sharepoint-pnp/add-pnptenantcdnorigin).</span></span>

<span data-ttu-id="83a48-436">명령을 실행 하면 시스템에서 데이터 센터 전체에서 구성을 동기화 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-436">Once you've run the command, the system synchronizes the configuration across the datacenter.</span></span> <span data-ttu-id="83a48-437">최대 15 분까지 소요 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-437">This can take up to 15 minutes.</span></span>

<span data-ttu-id="83a48-438"><a name="ExamplePrivateOriginPnPPosh"> </a></span><span class="sxs-lookup"><span data-stu-id="83a48-438"><a name="ExamplePrivateOriginPnPPosh"> </a></span></span>
### <a name="example-configure-a-private-origin-for-your-site-assets-site-pages-and-publishing-images-for-sharepoint-online"></a><span data-ttu-id="83a48-439">예: SharePoint Online에 대 한 사이트 자산, 사이트 페이지 및 게시 이미지에 대 한 개인 출처 구성</span><span class="sxs-lookup"><span data-stu-id="83a48-439">Example: Configure a private origin for your site assets, site pages, and publishing images for SharePoint Online</span></span>

+ <span data-ttu-id="83a48-440">**추가-Pnpten앤틸리스 Cdn근원** cmdlet을 사용 하 여 사이트 자산 폴더를 전용 원본으로 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-440">Use the **Add-PnPTenantCdnOrigin** cmdlet to define the site assets folder as a private origin.</span></span>

``` powershell
  Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl */siteassets
  ```

+ <span data-ttu-id="83a48-441">**추가-Pnpten앤틸리스 Cdn근원** cmdlet을 사용 하 여 사이트 페이지 폴더를 전용 원본으로 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-441">Use the **Add-PnPTenantCdnOrigin** cmdlet to define the site pages folder as a private origin.</span></span>

``` powershell
  Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl */sitepages
  ```

+ <span data-ttu-id="83a48-442">**추가-Pnpten앤틸리스 Cdn근원** cmdlet을 사용 하 여 게시 이미지 폴더를 전용 원본으로 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-442">Use the **Add-PnPTenantCdnOrigin** cmdlet to define the publishing images folder as a private origin.</span></span>

``` powershell
  Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl */publishingimages
  ```

<span data-ttu-id="83a48-443">이 명령 및 구문에 대 한 자세한 내용은 [추가-Pnpten앤틸리스 Cdn근원](https://docs.microsoft.com/powershell/module/sharepoint-pnp/add-pnptenantcdnorigin)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="83a48-443">For more information about this command and its syntax, see [Add-PnPTenantCdnOrigin](https://docs.microsoft.com/powershell/module/sharepoint-pnp/add-pnptenantcdnorigin).</span></span>

<span data-ttu-id="83a48-444">명령을 실행 하면 시스템에서 데이터 센터 전체에서 구성을 동기화 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-444">Once you've run the command, the system synchronizes the configuration across the datacenter.</span></span> <span data-ttu-id="83a48-445">최대 15 분까지 소요 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-445">This can take up to 15 minutes.</span></span>

<span data-ttu-id="83a48-446"><a name="ExamplePrivateOriginSiteCollectionPnPPosh"> </a></span><span class="sxs-lookup"><span data-stu-id="83a48-446"><a name="ExamplePrivateOriginSiteCollectionPnPPosh"> </a></span></span>
### <a name="example-configure-a-private-origin-for-a-site-collection-for-sharepoint-online"></a><span data-ttu-id="83a48-447">예: SharePoint Online에 대 한 사이트 모음에 대 한 개인 원본 구성</span><span class="sxs-lookup"><span data-stu-id="83a48-447">Example: Configure a private origin for a site collection for SharePoint Online</span></span>

<span data-ttu-id="83a48-448">**추가-Pnpten앤틸리스 Cdn근원** cmdlet을 사용 하 여 사이트 모음을 전용 원본으로 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-448">Use the **Add-PnPTenantCdnOrigin** cmdlet to define a site collection as a private origin.</span></span> <span data-ttu-id="83a48-449">예:</span><span class="sxs-lookup"><span data-stu-id="83a48-449">For example:</span></span>

``` powershell
Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

<span data-ttu-id="83a48-450">이 명령 및 구문에 대 한 자세한 내용은 [추가-Pnpten앤틸리스 Cdn근원](https://docs.microsoft.com/powershell/module/sharepoint-pnp/add-pnptenantcdnorigin)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="83a48-450">For more information about this command and its syntax, see [Add-PnPTenantCdnOrigin](https://docs.microsoft.com/powershell/module/sharepoint-pnp/add-pnptenantcdnorigin).</span></span>
  
<span data-ttu-id="83a48-451">명령을 실행 하면 시스템에서 데이터 센터 전체에서 구성을 동기화 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-451">Once you've run the command, the system synchronizes the configuration across the datacenter.</span></span> <span data-ttu-id="83a48-452">SharePoint Online 테 넌 트가 CDN 서비스에 연결할 때 예상 되는 _구성 보류 중인_ 메시지가 표시 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-452">You may see a _Configuration pending_ message which is expected as the SharePoint Online tenant connects to the CDN service.</span></span> <span data-ttu-id="83a48-453">최대 15 분까지 소요 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-453">This can take up to 15 minutes.</span></span>

<span data-ttu-id="83a48-454"><a name="CDNManagePnPPosh"> </a></span><span class="sxs-lookup"><span data-stu-id="83a48-454"><a name="CDNManagePnPPosh"> </a></span></span>
### <a name="manage-the-office-365-cdn"></a><span data-ttu-id="83a48-455">Office 365 CDN 관리</span><span class="sxs-lookup"><span data-stu-id="83a48-455">Manage the Office 365 CDN</span></span>

<span data-ttu-id="83a48-456">CDN을 설정한 후에는이 섹션에 설명 된 대로 콘텐츠를 업데이트 하거나 필요에 따라 변경 하 여 구성을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-456">Once you've set up the CDN, you can make changes to your configuration as you update content or as your needs change, as described in this section.</span></span>
  
<span data-ttu-id="83a48-457"><a name="Office365CDNforSPOaddremoveassetPnPPosh"> </a></span><span class="sxs-lookup"><span data-stu-id="83a48-457"><a name="Office365CDNforSPOaddremoveassetPnPPosh"> </a></span></span>
#### <a name="add-update-or-remove-assets-from-the-office-365-cdn"></a><span data-ttu-id="83a48-458">Office 365 CDN에서 자산 추가, 업데이트 또는 제거</span><span class="sxs-lookup"><span data-stu-id="83a48-458">Add, update, or remove assets from the Office 365 CDN</span></span>

<span data-ttu-id="83a48-459">설정 단계를 완료 한 후에는 새 자산을 추가 하 고 원할 때마다 기존 자산을 업데이트 하거나 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-459">Once you've completed the setup steps, you can add new assets, and update or remove existing assets whenever you want.</span></span> <span data-ttu-id="83a48-460">폴더 또는 SharePoint 라이브러리에서 원본으로 식별 한 자산을 변경 하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-460">Just make your changes to the assets in the folder or SharePoint library that you identified as an origin.</span></span> <span data-ttu-id="83a48-461">새 자산을 추가 하는 경우에는 CDN을 통해 즉시 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-461">If you add a new asset, it is available through the CDN immediately.</span></span> <span data-ttu-id="83a48-462">그러나 자산을 업데이트 하는 경우 새 복사본을 전파 하 고 CDN에서 사용할 수 있게 되는 데 최대 15 분이 걸립니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-462">However, if you update the asset, it will take up to 15 minutes for the new copy to propagate and become available in the CDN.</span></span>
  
<span data-ttu-id="83a48-463">근원 위치를 검색 해야 하는 경우에는 **Get-Pnpten앤틸리스 Cdn근원** cmdlet을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-463">If you need to retrieve the location of the origin, you can use the **Get-PnPTenantCdnOrigin** cmdlet.</span></span> <span data-ttu-id="83a48-464">이 cmdlet을 사용 하는 방법에 대 한 자세한 내용은 [Get-Pnpten앤틸리스 Cdn근원](https://docs.microsoft.com/powershell/module/sharepoint-pnp/get-pnptenantcdnorigin)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="83a48-464">For information on how to use this cmdlet, see [Get-PnPTenantCdnOrigin](https://docs.microsoft.com/powershell/module/sharepoint-pnp/get-pnptenantcdnorigin).</span></span>

<span data-ttu-id="83a48-465"><a name="Office365CDNforSPORemoveOriginPnPPosh"> </a></span><span class="sxs-lookup"><span data-stu-id="83a48-465"><a name="Office365CDNforSPORemoveOriginPnPPosh"> </a></span></span>
#### <a name="remove-an-origin-from-the-office-365-cdn"></a><span data-ttu-id="83a48-466">Office 365 CDN에서 원본 제거</span><span class="sxs-lookup"><span data-stu-id="83a48-466">Remove an origin from the Office 365 CDN</span></span>

<span data-ttu-id="83a48-467">원본으로 식별 한 폴더 또는 SharePoint 라이브러리에 대 한 액세스 권한을 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-467">You can remove access to a folder or SharePoint library that you identified as an origin.</span></span> <span data-ttu-id="83a48-468">이 작업을 수행 하려면 **Remove-Pnpten앤틸리스 Cdn근원** cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-468">To do this, use the **Remove-PnPTenantCdnOrigin** cmdlet.</span></span>

``` powershell
Remove-PnPTenantCdnOrigin -OriginUrl <path> -CdnType <Public | Private | Both>
```

<span data-ttu-id="83a48-469">이 cmdlet을 사용 하는 방법에 대 한 자세한 내용은 [Remove-Pnpten앤틸리스 Cdn근원](https://docs.microsoft.com/powershell/module/sharepoint-pnp/remove-pnptenantcdnorigin)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="83a48-469">For information on how to use this cmdlet, see [Remove-PnPTenantCdnOrigin](https://docs.microsoft.com/powershell/module/sharepoint-pnp/remove-pnptenantcdnorigin).</span></span>

<span data-ttu-id="83a48-470"><a name="Office365CDNforSPORemoveOriginPnPPosh"> </a></span><span class="sxs-lookup"><span data-stu-id="83a48-470"><a name="Office365CDNforSPORemoveOriginPnPPosh"> </a></span></span>
#### <a name="modify-an-origin-in-the-office-365-cdn"></a><span data-ttu-id="83a48-471">Office 365 CDN에서 원본 수정</span><span class="sxs-lookup"><span data-stu-id="83a48-471">Modify an origin in the Office 365 CDN</span></span>

<span data-ttu-id="83a48-472">만든 출처는 수정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-472">You cannot modify an origin you've created.</span></span> <span data-ttu-id="83a48-473">대신 원점을 제거한 다음 새 원본을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-473">Instead, remove the origin and then add a new one.</span></span> <span data-ttu-id="83a48-474">자세한 내용은 [Office 365 CDN에서 출처를 제거](use-office-365-cdn-with-spo.md#Office365CDNforSPORemoveOriginPnPPosh) 하 고 [자산의 출처를 추가](use-office-365-cdn-with-spo.md#Office365CDNforSPOOriginPnPPosh)하는 방법을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="83a48-474">For more information, see [To remove an origin from the Office 365 CDN](use-office-365-cdn-with-spo.md#Office365CDNforSPORemoveOriginPnPPosh) and [To add an origin for your assets](use-office-365-cdn-with-spo.md#Office365CDNforSPOOriginPnPPosh).</span></span>

<span data-ttu-id="83a48-475"><a name="Office365CDNforSPODisable"> </a></span><span class="sxs-lookup"><span data-stu-id="83a48-475"><a name="Office365CDNforSPODisable"> </a></span></span>
#### <a name="disable-the-office-365-cdn"></a><span data-ttu-id="83a48-476">Office 365 CDN 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="83a48-476">Disable the Office 365 CDN</span></span>

<span data-ttu-id="83a48-477">**-Pnpten앤틸리스 Cdnenabled** cmdlet을 사용 하 여 조직에 CDN을 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-477">Use the **Set-PnPTenantCdnEnabled** cmdlet to disable the CDN for your organization.</span></span> <span data-ttu-id="83a48-478">CDN에 대 한 공용 및 전용 원본을 모두 사용 하는 경우에는 다음 예제와 같이 cmdlet을 두 번 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-478">If you have both the public and private origins enabled for the CDN, you need to run the cmdlet twice as shown in the following examples.</span></span>
  
<span data-ttu-id="83a48-479">CDN에서 public 원본임을 사용 하지 않도록 설정 하려면 다음 명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-479">To disable use of public origins in the CDN, enter the following command:</span></span>

``` powershell
Set-PnPTenantCdnEnabled -CdnType Public -Enable $false
```

<span data-ttu-id="83a48-480">CDN에서 비공개 원본을 사용 하지 않도록 설정 하려면 다음 명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-480">To disable use of the private origins in the CDN, enter the following command:</span></span>

``` powershell
Set-PnPTenantCdnEnabled -CdnType Private -Enable $false
```

<span data-ttu-id="83a48-481">이 cmdlet에 대 한 자세한 내용은 [Set-Pnpten앤틸리스 Cdnenabled](https://docs.microsoft.com/powershell/module/sharepoint-pnp/set-pnptenantcdnenabled)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="83a48-481">For more information about this cmdlet, see [Set-PnPTenantCdnEnabled](https://docs.microsoft.com/powershell/module/sharepoint-pnp/set-pnptenantcdnenabled).</span></span>

</details>

<span data-ttu-id="83a48-482"><a name="CDNSetupinCLI"> </a></span><span class="sxs-lookup"><span data-stu-id="83a48-482"><a name="CDNSetupinCLI"> </a></span></span>
## <a name="set-up-and-configure-the-office-365-cdn-using-the-office-365-cli"></a><span data-ttu-id="83a48-483">Office 365 CLI를 사용 하 여 Office 365 CDN을 설정 하 고 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-483">Set up and configure the Office 365 CDN using the Office 365 CLI</span></span>

<span data-ttu-id="83a48-484">이 섹션의 절차에서는 [Office 365 CLI](https://aka.ms/o365cli)를 설치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-484">The procedures in this section require that you have installed the [Office 365 CLI](https://aka.ms/o365cli).</span></span> <span data-ttu-id="83a48-485">다음으로 [login](https://pnp.github.io/office365-cli/cmd/login/) 명령을 사용 하 여 Office 365 테 넌 트에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-485">Next, connect to your Office 365 tenant using the [login](https://pnp.github.io/office365-cli/cmd/login/) command.</span></span>

<span data-ttu-id="83a48-486">Office 365 CLI를 사용 하 여 SharePoint Online에서 자산을 호스트 하도록 CDN을 설정 및 구성 하려면 다음 단계를 완료 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-486">Complete these steps to set up and configure the CDN to host your assets in SharePoint Online using the Office 365 CLI.</span></span>

<details>
  <summary><span data-ttu-id="83a48-487">클릭 하 여 확장</span><span class="sxs-lookup"><span data-stu-id="83a48-487">Click to expand</span></span></summary>

### <a name="enable-the-office-365-cdn"></a><span data-ttu-id="83a48-488">Office 365 CDN 사용</span><span class="sxs-lookup"><span data-stu-id="83a48-488">Enable the Office 365 CDN</span></span>

<span data-ttu-id="83a48-489">[Spo CDN set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-set/) 명령을 사용 하 여 테 넌 트에서 OFFICE 365 CDN의 상태를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-489">You can manage the state of the Office 365 CDN in your tenant using the [spo cdn set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-set/) command.</span></span>

<span data-ttu-id="83a48-490">테 넌 트에서 실행 되는 Office 365 공용 CDN을 사용 하도록 설정 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-490">To enable the Office 365 Public CDN in your tenant execute:</span></span>

```sh
spo cdn set --type Public --enabled true
```

<span data-ttu-id="83a48-491">Office 365 SharePoint CDN을 사용 하도록 설정 하려면 다음을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-491">To enable the Office 365 SharePoint CDN, execute:</span></span>

```sh
spo cdn set --type Private --enabled true
```

#### <a name="view-the-current-status-of-the-office-365-cdn"></a><span data-ttu-id="83a48-492">Office 365 CDN의 현재 상태를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-492">View the current status of the Office 365 CDN</span></span>

<span data-ttu-id="83a48-493">특정 유형의 Office 365 CDN을 사용 하거나 사용 하지 않도록 설정할지 여부를 확인 하려면 [spo CDN get](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-get/) 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-493">To check if the particular type of Office 365 CDN is enabled or disabled, use the [spo cdn get](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-get/) command.</span></span>

<span data-ttu-id="83a48-494">Office 365 공용 CDN이 사용 하도록 설정 되어 있는지 확인 하려면 다음을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-494">To check if the Office 365 Public CDN is enabled, execute:</span></span>

```sh
spo cdn get --type Public
```

### <a name="view-the-office-365-cdn-origins"></a><span data-ttu-id="83a48-495">Office 365 CDN 원본 보기</span><span class="sxs-lookup"><span data-stu-id="83a48-495">View the Office 365 CDN origins</span></span>

<span data-ttu-id="83a48-496">현재 구성 된 Office 365 공용 CDN 원본을 실행 하려면 다음을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-496">To view the currently configured Office 365 Public CDN origins execute:</span></span>

```sh
spo cdn origin list --type Public
```

<span data-ttu-id="83a48-497">Office 365 CDN을 사용 하도록 설정 하는 경우 기본적으로 프로 비전 되는 원본에 대 한 자세한 내용은 [DEFAULT CDN 원본을](use-office-365-cdn-with-spo.md#default-cdn-origins) 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="83a48-497">See [Default CDN origins](use-office-365-cdn-with-spo.md#default-cdn-origins) for information about the origins that are provisioned by default when you enable the Office 365 CDN.</span></span>

### <a name="add-an-office-365-cdn-origin"></a><span data-ttu-id="83a48-498">Office 365 CDN 원본 추가</span><span class="sxs-lookup"><span data-stu-id="83a48-498">Add an Office 365 CDN origin</span></span>

> [!IMPORTANT]
> <span data-ttu-id="83a48-499">조직에 중요 한 것으로 간주 되는 리소스를 공공 근원으로 구성 된 SharePoint 문서 라이브러리에 배치 해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-499">You should never place resources that are considered sensitive to your organization in a SharePoint document library configured as a public origin.</span></span>

<span data-ttu-id="83a48-500">[Spo cdn 원본 add](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-add/) 명령을 사용 하 여 cdn 원본을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-500">Use the [spo cdn origin add](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-add/) command to define a CDN origin.</span></span> <span data-ttu-id="83a48-501">여러 원본을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-501">You can define multiple origins.</span></span> <span data-ttu-id="83a48-502">원점은 CDN에서 호스팅할 자산이 포함 된 SharePoint 라이브러리 또는 폴더를 가리키는 URL입니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-502">The origin is a URL that points to a SharePoint library or folder that contains the assets that you want to be hosted by the CDN.</span></span>

```sh
spo cdn origin add --type [Public | Private] --origin <path>
```

<span data-ttu-id="83a48-503">여기서 `path` 은 자산이 포함 된 폴더에 대 한 상대 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-503">Where `path` is the relative path to the folder that contains the assets.</span></span> <span data-ttu-id="83a48-504">상대 경로 외에도 와일드 카드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-504">You can use wildcards in addition to relative paths.</span></span>

<span data-ttu-id="83a48-505">모든 사이트의 **마스터 페이지 갤러리** 에 있는 모든 자산을 공용 원점으로 포함 하려면 다음을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-505">To include all assets in the **Master Page Gallery** of all sites as a public origin, execute:</span></span>

```sh
spo cdn origin add --type Public --origin */masterpage
```

<span data-ttu-id="83a48-506">특정 사이트 모음에 대 한 개인 원점을 구성 하려면 다음을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-506">To configure a private origin for a specific site collection, execute:</span></span>

```sh
spo cdn origin add --type Private --origin sites/site1/siteassets
```

> [!NOTE]
> <span data-ttu-id="83a48-507">CDN 원본을 추가한 후에는 CDN 서비스를 통해 파일을 검색 하는 데 최대 15 분까지 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-507">After adding a CDN origin, it might take up to 15 minutes for you to be able to retrieve files via the CDN service.</span></span> <span data-ttu-id="83a48-508">[Spo cdn 원본 목록](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-list/) 명령을 사용 하 여 특정 원본이 이미 사용 하도록 설정 되었는지 여부를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-508">You can verify if the particular origin has already been enabled using the [spo cdn origin list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-list/) command.</span></span>

### <a name="remove-an-office-365-cdn-origin"></a><span data-ttu-id="83a48-509">Office 365 CDN 원본 제거</span><span class="sxs-lookup"><span data-stu-id="83a48-509">Remove an Office 365 CDN origin</span></span>

<span data-ttu-id="83a48-510">[Spo cdn 원본 제거](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-remove/) 명령을 사용 하 여 지정 된 cdn 유형에 대해 cdn 원본을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-510">Use the [spo cdn origin remove](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-remove/) command to remove a CDN origin for the specified CDN type.</span></span>

<span data-ttu-id="83a48-511">CDN 구성에서 공용 원점을 제거 하려면 다음을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-511">To remove a public origin from the CDN configuration, execute:</span></span>

```sh
spo cdn origin remove --type Public --origin */masterpage
```

> [!NOTE]
> <span data-ttu-id="83a48-512">CDN 원본을 제거 해도 해당 원본과 일치 하는 문서 라이브러리에 저장 된 파일에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-512">Removing a CDN origin doesn't affect the files stored in any document library matching that origin.</span></span> <span data-ttu-id="83a48-513">이러한 자산이 SharePoint URL을 사용 하 여 참조 된 경우 SharePoint는 문서 라이브러리를 가리키는 원래 URL로 자동 전환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-513">If these assets have been referenced using their SharePoint URL, SharePoint will automatically switch back to the original URL pointing to the document library.</span></span> <span data-ttu-id="83a48-514">그러나 공용 CDN URL을 사용 하 여 자산이 참조 된 경우에는 원본을 제거 하면 링크가 끊어지고 수동으로 변경 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-514">If, however, assets have been referenced using a public CDN URL, then removing the origin will break the link and you will need to manually change them.</span></span>

### <a name="modify-an-office-365-cdn-origin"></a><span data-ttu-id="83a48-515">Office 365 CDN 원본 수정</span><span class="sxs-lookup"><span data-stu-id="83a48-515">Modify an Office 365 CDN origin</span></span>

<span data-ttu-id="83a48-516">기존 CDN 원본을 수정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-516">It's not possible to modify an existing CDN origin.</span></span> <span data-ttu-id="83a48-517">대신 `spo cdn origin remove` 명령을 사용 하 여 이전에 정의 된 CDN 원본을 제거 하 고 `spo cdn origin add` 명령을 사용 하 여 새로 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-517">Instead, you should remove the previously defined CDN origin using the `spo cdn origin remove` command and add a new one using the `spo cdn origin add` command.</span></span>

### <a name="change-the-types-of-files-to-include-in-the-office-365-cdn"></a><span data-ttu-id="83a48-518">Office 365 CDN에 포함할 파일 형식 변경</span><span class="sxs-lookup"><span data-stu-id="83a48-518">Change the types of files to include in the Office 365 CDN</span></span>

<span data-ttu-id="83a48-519">기본적으로 CDN에는 다음 파일 형식이 포함 됩니다. _.css, eot, .gif, .ico, .jpeg, .jpg_,. p s t,. w o v,. ttf,.</span><span class="sxs-lookup"><span data-stu-id="83a48-519">By default, the following file types are included in the CDN: _.css, .eot, .gif, .ico, .jpeg, .jpg, .js, .map, .png, .svg, .ttf, and .woff_.</span></span> <span data-ttu-id="83a48-520">CDN에 추가 파일 형식을 포함 해야 하는 경우에는 [spo cdn 정책 set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-set/) 명령을 사용 하 여 cdn 구성을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-520">If you need to include additional file types in the CDN, you can change the CDN configuration using the [spo cdn policy set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-set/) command.</span></span>

> [!NOTE]
> <span data-ttu-id="83a48-521">파일 형식 목록을 변경할 때 현재 정의 된 목록을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-521">When changing the list of file types, you overwrite the currently defined list.</span></span> <span data-ttu-id="83a48-522">추가 파일 형식을 포함 하려면 먼저 [spo cdn 정책 목록](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-list/) 명령을 사용 하 여 현재 구성 되어 있는 파일 형식을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-522">If you want to include additional file types, first use the [spo cdn policy list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-list/) command to find out which file types are currently configured.</span></span>

<span data-ttu-id="83a48-523">공용 CDN에 포함 된 파일 형식의 기본 목록에 _JSON_ 파일 형식을 추가 하려면 다음을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-523">To add the _JSON_ file type to the default list of file types included in the public CDN, execute:</span></span>

```sh
spo cdn policy set --type Public --policy IncludeFileExtensions --value "CSS,EOT,GIF,ICO,JPEG,JPG,JS,MAP,PNG,SVG,TTF,WOFF,JSON"
```

### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn"></a><span data-ttu-id="83a48-524">Office 365 CDN에서 제외 하려는 사이트 분류 목록 변경</span><span class="sxs-lookup"><span data-stu-id="83a48-524">Change the list of site classifications you want to exclude from the Office 365 CDN</span></span>

<span data-ttu-id="83a48-525">[Spo cdn 정책 설정](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-set/) 명령을 사용 하 여 cdn을 통해 사용 하지 않으려는 사이트 분류를 제외 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-525">Use the [spo cdn policy set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-set/) command to exclude site classifications that you do not want to make available over the CDN.</span></span> <span data-ttu-id="83a48-526">기본적으로 사이트 분류는 제외 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-526">By default, no site classifications are excluded.</span></span>

> [!NOTE]
> <span data-ttu-id="83a48-527">제외 된 사이트 분류 목록을 변경할 때 현재 정의 된 목록을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-527">When changing the list of excluded site classifications, you overwrite the currently defined list.</span></span> <span data-ttu-id="83a48-528">추가 분류를 제외 하려면 먼저 [spo cdn 정책 목록](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-list/) 명령을 사용 하 여 현재 구성 된 분류를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-528">If you want to exclude additional classifications, first use the [spo cdn policy list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-list/) command to find out which classifications are currently configured.</span></span>

<span data-ttu-id="83a48-529">_HBI_ 으로 분류 된 사이트를 공용 CDN에서 제외 하려면 다음을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-529">To exclude sites classified as _HBI_ from the public CDN, execute</span></span>

```sh
spo cdn policy set --type Public --policy ExcludeRestrictedSiteClassifications --value "HBI"
```

### <a name="disable-the-office-365-cdn"></a><span data-ttu-id="83a48-530">Office 365 CDN 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="83a48-530">Disable the Office 365 CDN</span></span>

<span data-ttu-id="83a48-531">Office 365 CDN을 사용 하지 않도록 설정 `spo cdn set` 하려면 다음과 같이 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-531">To disable the Office 365 CDN use the `spo cdn set` command, for example:</span></span>

```sh
spo cdn set --type Public --enabled false
```

</details>

## <a name="using-your-cdn-assets"></a><span data-ttu-id="83a48-532">CDN 자산 사용</span><span class="sxs-lookup"><span data-stu-id="83a48-532">Using your CDN assets</span></span>

<span data-ttu-id="83a48-533">CDN 및 구성 된 원본 및 정책을 사용 하도록 설정 했으므로 이제 CDN 자산 사용을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-533">Now that you have enabled the CDN and configured origins and policies, you can begin using your CDN assets.</span></span>

<span data-ttu-id="83a48-534">이 섹션에서는 SharePoint에서 공용 및 사설 원본 모두에 대 한 요청을 CDN으로 리디렉션하는 SharePoint 페이지 및 콘텐츠에서 CDN Url을 사용 하는 방법을 이해 하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-534">This section will help you understand how to use CDN URLs in your SharePoint pages and content so that SharePoint redirects requests for assets in both public and private origins to the CDN.</span></span>

+ [<span data-ttu-id="83a48-535">CDN 자산에 대 한 링크 업데이트</span><span class="sxs-lookup"><span data-stu-id="83a48-535">Updating links to CDN assets</span></span>](use-office-365-cdn-with-spo.md#updating-links-to-cdn-assets)
+ [<span data-ttu-id="83a48-536">공개 원본에서 에셋 사용</span><span class="sxs-lookup"><span data-stu-id="83a48-536">Using assets in public origins</span></span>](use-office-365-cdn-with-spo.md#using-assets-in-public-origins)
+ [<span data-ttu-id="83a48-537">비공개 원본에서 에셋 사용</span><span class="sxs-lookup"><span data-stu-id="83a48-537">Using assets in private origins</span></span>](use-office-365-cdn-with-spo.md#using-assets-in-private-origins)

<span data-ttu-id="83a48-538">클라이언트 쪽 웹 파트 호스팅을 위해 CDN을 사용 하는 방법에 대 한 자세한 내용은 [Office 365 CDN (Hello World part 4)에서 클라이언트 쪽 웹 파트 호스트](https://docs.microsoft.com/sharepoint/dev/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn)항목을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="83a48-538">For information on how to use the CDN for hosting client-side web parts, see the topic [Host your client-side web part from Office 365 CDN (Hello World part 4)](https://docs.microsoft.com/sharepoint/dev/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn).</span></span>

### <a name="updating-links-to-cdn-assets"></a><span data-ttu-id="83a48-539">CDN 자산에 대 한 링크 업데이트</span><span class="sxs-lookup"><span data-stu-id="83a48-539">Updating links to CDN assets</span></span>

<span data-ttu-id="83a48-540">원본에 추가한 자산을 사용 하려면 원본의 파일 경로를 사용 하 여 원본 파일에 대 한 링크를 업데이트 하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-540">To use assets that you have added to an origin, you simply update links to the original file with the path to the file in the origin.</span></span>

+ <span data-ttu-id="83a48-541">출처에 추가한 자산에 대 한 링크를 포함 하는 페이지 또는 콘텐츠를 편집 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-541">Edit the page or content that contains links to assets you have added to an origin.</span></span> <span data-ttu-id="83a48-542">또한 여러 방법 중 하나를 사용 하 여 지정 된 자산에 대 한 링크를 전역으로 검색 하 고 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-542">You can also use one of several methods to globally search and replace links across an enter site or site collection if you want to update the link to a given asset everywhere it appears.</span></span>
+ <span data-ttu-id="83a48-543">원본의 자산에 대 한 각 링크에 대해 경로를 CDN 원본에 있는 파일의 경로로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-543">For each link to an asset in an origin, replace the path with the path to the file in the CDN origin.</span></span> <span data-ttu-id="83a48-544">상대 경로를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-544">You can use relative paths.</span></span>
+ <span data-ttu-id="83a48-545">페이지 또는 콘텐츠를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-545">Save the page or content.</span></span>

<span data-ttu-id="83a48-546">예를 들어 문서 라이브러리 폴더 _/site/CDN_origins/site/_ 로 복사한 이미지 _/site/SiteAssets/images/image.png_을 고려해 보십시오.</span><span class="sxs-lookup"><span data-stu-id="83a48-546">For example, consider the image _/site/SiteAssets/images/image.png_, which you have copied to the document library folder _/site/CDN_origins/public/_.</span></span> <span data-ttu-id="83a48-547">CDN 자산을 사용 하려면 원래 경로를 원본 경로와 함께 이미지 파일 위치로 바꿔 새 URL _/site/CDN_origins/public/.png_를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-547">To use the CDN asset, replace the original path to the image file location with the path to the origin to make the new URL _/site/CDN_origins/public/image.png_.</span></span>

<span data-ttu-id="83a48-548">상대 경로 대신 자산에 대 한 전체 URL을 사용 하려면 다음과 같이 링크를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-548">If you want to use the full URL to the asset instead of a relative path, construct the link like so:</span></span>

`https://<TenantHostName>.sharepoint.com/sites/site/CDN_origins/public/image.png`

> [!NOTE]
> <span data-ttu-id="83a48-549">일반적으로 CDN의 자산에 Url을 직접 하드 코딩 해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-549">In general, you should not hardcode URLs directly to assets in the CDN.</span></span> <span data-ttu-id="83a48-550">그러나 필요한 경우 공개 원본에서 자산에 대 한 Url을 수동으로 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-550">However, you can manually construct URLs for assets in public origins if needed.</span></span> <span data-ttu-id="83a48-551">자세한 내용은 [공용 자산의 하드 코딩 CDN url](use-office-365-cdn-with-spo.md#hardcoding-cdn-urls-for-public-assets)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="83a48-551">For more information, see [Hardcoding CDN URLs for public assets](use-office-365-cdn-with-spo.md#hardcoding-cdn-urls-for-public-assets).</span></span>

<span data-ttu-id="83a48-552">CDN에서 자산이 제공 되 고 있는지 확인 하는 방법에 대 한 자세한 내용은 How the [Office 365 CDN](use-office-365-cdn-with-spo.md#CDNTroubleshooting) 섹션의 ["cdn에서 자산이 제공 되 고 있는지 확인 하는 방법은 무엇입니까?"](use-office-365-cdn-with-spo.md#CDNConfirm) 를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="83a48-552">To learn about how to verify that assets are being served from the CDN, see [How do I confirm that assets are being served by the CDN?](use-office-365-cdn-with-spo.md#CDNConfirm) in the [Troubleshooting the Office 365 CDN](use-office-365-cdn-with-spo.md#CDNTroubleshooting) section.</span></span>

### <a name="using-assets-in-public-origins"></a><span data-ttu-id="83a48-553">공개 원본에서 에셋 사용</span><span class="sxs-lookup"><span data-stu-id="83a48-553">Using assets in public origins</span></span>

<span data-ttu-id="83a48-554">SharePoint Online의 **게시 기능은** SHAREPOINT 대신 cdn 서비스에서 자산이 제공 되도록 공용 원본에 저장 된 자산의 url을 해당 cdn에 맞게 자동으로 다시 씁니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-554">The **Publishing feature** in SharePoint Online automatically rewrites URLs of assets stored in public origins to their CDN equivalents so that assets are served from the CDN service instead of SharePoint.</span></span>

<span data-ttu-id="83a48-555">원본이 게시 기능이 사용 하도록 설정 된 사이트에 있고 CDN에 대해 오프 로드 하려는 자산이 다음 범주 중 하나에 포함 되어 있는 경우 SharePoint에서는 자산이 CDN에서 제외 된 경우에는 원본의 자산에 대 한 Url을 자동으로 다시 씁니다.  정책.</span><span class="sxs-lookup"><span data-stu-id="83a48-555">If your origin is in a site with the Publishing feature enabled, and the assets you want to offload to the CDN are in one of the following categories, SharePoint will automatically rewrite URLs for assets in the origin, provided that the asset has not been excluded by a CDN policy.</span></span>

<span data-ttu-id="83a48-556">다음은 SharePoint 게시 기능에 의해 자동으로 다시 작성 되는 링크에 대 한 간략 한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-556">The following is an overview of which links are automatically rewritten by the SharePoint Publishing feature:</span></span>

+ <span data-ttu-id="83a48-557">클래식 게시 페이지의 HTML 응답에 있는 IMG/LINK/CSS Url</span><span class="sxs-lookup"><span data-stu-id="83a48-557">IMG/LINK/CSS URLs in classic publishing page HTML responses</span></span>
  + <span data-ttu-id="83a48-558">여기에는 페이지의 HTML 콘텐츠 내에서 제작자가 추가한 이미지가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-558">This includes images added by authors within the HTML content of a page</span></span>
+ <span data-ttu-id="83a48-559">그림 라이브러리 슬라이드 쇼 웹 파트 이미지 Url</span><span class="sxs-lookup"><span data-stu-id="83a48-559">Picture Library SlideShow webpart image URLs</span></span>
+ <span data-ttu-id="83a48-560">RenderListDataAsStream (SPList REST API)의 이미지 필드 결과</span><span class="sxs-lookup"><span data-stu-id="83a48-560">Image fields in SPList REST API (RenderListDataAsStream) results</span></span>
  + <span data-ttu-id="83a48-561">새 속성 _Imagefieldstotryrewritetocdnurls_ 을 사용 하 여 쉼표로 구분 된 필드 목록을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-561">Use the new property _ImageFieldsToTryRewriteToCdnUrls_ to provide a comma separated list of fields</span></span>
  + <span data-ttu-id="83a48-562">하이퍼링크 필드 및 PublishingImage 필드 지원</span><span class="sxs-lookup"><span data-stu-id="83a48-562">Supports hyperlink fields and PublishingImage fields</span></span>
+ <span data-ttu-id="83a48-563">SharePoint 이미지 변환</span><span class="sxs-lookup"><span data-stu-id="83a48-563">SharePoint image renditions</span></span>

<span data-ttu-id="83a48-564">다음 다이어그램에서는 SharePoint가 공용 원본의 자산을 포함 하는 페이지에 대 한 요청을 수신 하는 경우의 워크플로를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-564">The following diagram illustrates the workflow when SharePoint receives a request for a page containing assets from a public origin.</span></span>

<span data-ttu-id="83a48-565">![워크플로 다이어그램: 공용 원본의 Office 365 CDN 자산 검색](media/O365-CDN/o365-cdn-public-steps-transparent.svg "워크플로: 공용 원본에서 Office 365 CDN 자산을 검색 하는 경우")</span><span class="sxs-lookup"><span data-stu-id="83a48-565">![Workflow diagram: Retrieving Office 365 CDN assets from a public origin](media/O365-CDN/o365-cdn-public-steps-transparent.svg "Workflow: Retrieving Office 365 CDN assets from a public origin")</span></span>

> [!TIP]
> <span data-ttu-id="83a48-566">페이지의 특정 Url에 대해 자동 다시 쓰기를 사용 하지 않도록 설정 하려는 경우 페이지를 체크 아웃 하 고 쿼리 문자열 매개 변수를 추가할 수 있습니다. \*\* \*\*사용 하지 않도록 설정할 각 링크의 끝에 NoAutoReWrites = true를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-566">If you want to disable auto-rewriting for specific URLs on a page, you can check out the page and add the query string parameter **?NoAutoReWrites=true** to the end of each link you want to disable.</span></span>

#### <a name="hardcoding-cdn-urls-for-public-assets"></a><span data-ttu-id="83a48-567">공용 자산의 CDN Url을 하드 코딩 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-567">Hardcoding CDN URLs for public assets</span></span>

<span data-ttu-id="83a48-568">공개 원점에 대해 _게시_ 기능을 사용할 수 없거나 자산이 cdn 서비스의 자동 재작성 기능에서 지 원하는 링크 형식 중 하나가 아닌 경우에는 자산의 cdn 위치에 대 한 url을 수동으로 구성 하 고 콘텐츠에 이러한 url을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-568">If the _Publishing_ feature is not enabled for a public origin, or the asset is not one of the link types supported by the auto-rewrite feature of the CDN service, you can manually construct URLs to the CDN location of the assets and use these URLs in your content.</span></span>

> [!NOTE]
> <span data-ttu-id="83a48-569">URL의 마지막 섹션을 구성 하는 데 필요한 액세스 토큰이 리소스를 요청할 때 생성 되므로 비공개 원본의 자산에 CDN Url을 하드 제거할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-569">You cannot hardcode CDN URLs to assets in a private origin because the required access token that forms the last section of the URL is generated at the time the resource is requested.</span></span>

<span data-ttu-id="83a48-570">공용 CDN 자산의 경우 URL 형식이 다음과 같이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-570">For public CDN assets, the URL format will look like the following:</span></span>

``` html
https://publiccdn.sharepointonline.com/<TenantHostName>/sites/site/library/asset.png
```

<span data-ttu-id="83a48-571">**TenantHostName** 을 테 넌 트 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-571">Replace **TenantHostName** with your tenant name.</span></span> <span data-ttu-id="83a48-572">예제:</span><span class="sxs-lookup"><span data-stu-id="83a48-572">Example:</span></span>

``` html
https://publiccdn.sharepointonline.com/contoso.sharepoint.com/sites/site/library/asset.png
```

### <a name="using-assets-in-private-origins"></a><span data-ttu-id="83a48-573">비공개 원본에서 에셋 사용</span><span class="sxs-lookup"><span data-stu-id="83a48-573">Using assets in private origins</span></span>

<span data-ttu-id="83a48-574">비공개 원본에서 자산을 사용 하는 데에는 추가 구성이 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-574">No additional configuration is required to use assets in private origins.</span></span> <span data-ttu-id="83a48-575">SharePoint Online은 개인 원본에 있는 자산의 Url을 자동으로 다시 씁니다. 이러한 자산에 대 한 요청은 항상 CDN에서 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-575">SharePoint Online automatically rewrites URLs for assets in private origins so requests for those assets will always be served from the CDN.</span></span> <span data-ttu-id="83a48-576">자산을 요청 하는 경우에는 SharePoint Online에서 자동으로 생성 해야 하는 토큰이 포함 되기 때문에 이러한 Url에는 개인 원본에서 CDN 자산에 대 한 Url을 수동으로 빌드할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-576">You cannot manually build URLs to CDN assets in private origins because these URLs contain tokens that must be auto-generated by SharePoint Online at the time the asset is requested.</span></span>

<span data-ttu-id="83a48-577">비공개 원본의 자산에 대 한 액세스는 원본에 대 한 사용자 권한 및 다음 섹션에서 설명 하는 주의 사항에 따라 동적으로 생성 된 토큰으로 보호 됩니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-577">Access to assets in private origins is protected by dynamically generated tokens based on user permissions to the origin, with the caveats described in the following sections.</span></span> <span data-ttu-id="83a48-578">사용자에 게는 CDN에서 콘텐츠를 렌더링 하기 위한 **읽기** 이상의 원본 액세스 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-578">Users must have at least **read** access to the origins for the CDN to render content.</span></span>

<span data-ttu-id="83a48-579">다음 다이어그램에서는 SharePoint가 비공개 원본의 자산을 포함 하는 페이지에 대 한 요청을 수신 하는 경우의 워크플로를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-579">The following diagram illustrates the workflow when SharePoint receives a request for a page containing assets from a private origin.</span></span>

<span data-ttu-id="83a48-580">![워크플로 다이어그램: 비공개 원본의 Office 365 CDN 자산 검색](media/O365-CDN/o365-cdn-private-steps-transparent.svg "워크플로: 비공개 원본의 Office 365 CDN 자산 검색")</span><span class="sxs-lookup"><span data-stu-id="83a48-580">![Workflow diagram: Retrieving Office 365 CDN assets from a private origin](media/O365-CDN/o365-cdn-private-steps-transparent.svg "Workflow: Retrieving Office 365 CDN assets from a private origin")</span></span>

#### <a name="token-based-authorization-in-private-origins"></a><span data-ttu-id="83a48-581">전용 원본에서의 토큰 기반 권한 부여</span><span class="sxs-lookup"><span data-stu-id="83a48-581">Token-based authorization in private origins</span></span>

<span data-ttu-id="83a48-582">Office 365 CDN의 비공개 원본에 있는 자산에 대 한 액세스는 SharePoint Online에서 생성 된 토큰에 의해 부여 됩니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-582">Access to assets in private origins in the Office 365 CDN is granted by tokens generated by SharePoint Online.</span></span> <span data-ttu-id="83a48-583">원본에서 지정한 폴더나 라이브러리에 대 한 액세스 권한이 이미 있는 사용자에 게는 사용자가 자신의 사용 권한 수준에 따라 파일에 액세스할 수 있도록 허용 하는 토큰이 자동으로 부여 됩니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-583">Users who already have permission to access to the folder or library designated by the origin are automatically granted tokens that permit the user to access the file based on their permission level.</span></span> <span data-ttu-id="83a48-584">이러한 액세스 토큰은 토큰 재생 공격을 방지 하기 위해 생성 된 30 ~ 90 분에 유효 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-584">These access tokens are valid for 30 to 90 minutes after they are generated to help prevent token replay attacks.</span></span>

<span data-ttu-id="83a48-585">액세스 토큰이 생성 되 면 SharePoint Online에서 클라이언트에 대 한 사용자 지정 URI 두 _개 (edge_ 인증 토큰)와 _oat_ (원본 인증 토큰)을 함께 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-585">Once the access token is generated, SharePoint Online returns a custom URI to the client containing two authorization parameters _eat_ (edge authorization token) and _oat_ (origin authorization token).</span></span> <span data-ttu-id="83a48-586">각 토큰의 구조는 _< ' >__< ' 보안 서명 ' >' 만료 시간 '으로 지정 _됩니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-586">The structure of each token is _<'expiration time in Epoch time format'>__<'secure signature'>_.</span></span> <span data-ttu-id="83a48-587">예:</span><span class="sxs-lookup"><span data-stu-id="83a48-587">For example:</span></span>

``` html
https://privatecdn.sharepointonline.com/contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg?eat=1486154359_cc59042c5c55c90b26a2775323c7c8112718431228fe84d568a3795a63912840&oat=1486154359_7d73c2e3ba4b7b1f97242332900616db0d4ffb04312
```

> [!NOTE]
> <span data-ttu-id="83a48-588">토큰을 소유 하는 모든 사용자가 CDN의 리소스에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-588">Anyone in possession of the token can access the resource in the CDN.</span></span> <span data-ttu-id="83a48-589">그러나 이러한 액세스 토큰을 포함 하는 Url은 HTTPS를 통해서만 공유 되므로 토큰이 만료 되기 전에 최종 사용자가 URL을 명시적으로 공유 하지 않으면 권한이 없는 사용자가 해당 자산에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-589">However, URLs containing these access tokens are only shared over HTTPS, so unless the URL is explicitly shared by an end user before the token expires, the asset won’t be accessible to unauthorized users.</span></span>

#### <a name="item-level-permissions-are-not-supported-for-assets-in-private-origins"></a><span data-ttu-id="83a48-590">비공개 원본에 있는 자산에 대해서는 항목 수준 권한이 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-590">Item-level permissions are not supported for assets in private origins</span></span>

<span data-ttu-id="83a48-591">SharePoint Online은 전용 원본에 있는 자산에 대 한 항목 수준 권한을 지원 하지 않는다는 점에 유의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-591">It is important to note that SharePoint Online does not support item-level permissions for assets in private origins.</span></span> <span data-ttu-id="83a48-592">예를 들어에 `https://contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg`있는 파일의 경우 사용자는 다음 조건에 해당 하는 파일에 대 한 유효한 액세스 권한을 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-592">For example, for a file located at `https://contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg`, users have effective access to the file given the following conditions:</span></span>

|<span data-ttu-id="83a48-593">사용자</span><span class="sxs-lookup"><span data-stu-id="83a48-593">User</span></span>  |<span data-ttu-id="83a48-594">사용 권한</span><span class="sxs-lookup"><span data-stu-id="83a48-594">Permissions</span></span>  |<span data-ttu-id="83a48-595">유효한 액세스</span><span class="sxs-lookup"><span data-stu-id="83a48-595">Effective access</span></span>  |
|---------|---------|---------|
|<span data-ttu-id="83a48-596">사용자 1</span><span class="sxs-lookup"><span data-stu-id="83a48-596">User 1</span></span>     |<span data-ttu-id="83a48-597">Folder1에 대 한 액세스 권한</span><span class="sxs-lookup"><span data-stu-id="83a48-597">Has access to folder1</span></span>         |<span data-ttu-id="83a48-598">CDN에서 image1에 액세스할 수 있음</span><span class="sxs-lookup"><span data-stu-id="83a48-598">Can access image1.jpg from the CDN</span></span>         |
|<span data-ttu-id="83a48-599">사용자 2</span><span class="sxs-lookup"><span data-stu-id="83a48-599">User 2</span></span>     |<span data-ttu-id="83a48-600">Folder1에 대 한 액세스 권한이 없음</span><span class="sxs-lookup"><span data-stu-id="83a48-600">Does not have access to folder1</span></span>         |<span data-ttu-id="83a48-601">CDN에서 image1에 액세스할 수 없음</span><span class="sxs-lookup"><span data-stu-id="83a48-601">Cannot access image1.jpg from the CDN</span></span>         |
|<span data-ttu-id="83a48-602">사용자 3</span><span class="sxs-lookup"><span data-stu-id="83a48-602">User 3</span></span>     |<span data-ttu-id="83a48-603">Folder1에 대 한 액세스 권한이 없지만 SharePoint Online에서 image1에 액세스할 수 있는 권한이 명시적으로 부여 됩니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-603">Does not have access to folder1, but is granted explicit permission to access image1.jpg in SharePoint Online</span></span>         |<span data-ttu-id="83a48-604">SharePoint Online에서 직접 자산 image1에 액세스할 수 있으 나 CDN에서 액세스 가능</span><span class="sxs-lookup"><span data-stu-id="83a48-604">Can access the asset image1.jpg directly from SharePoint Online, but not from the CDN</span></span>         |
|<span data-ttu-id="83a48-605">사용자 4</span><span class="sxs-lookup"><span data-stu-id="83a48-605">User 4</span></span>     |<span data-ttu-id="83a48-606">Folder1에 대 한 액세스 권한이 있지만 SharePoint Online에서 image1에 대 한 액세스 권한이 명시적으로 거부 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-606">Has access to folder1, but has been explicitly denied access to image1.jpg in SharePoint Online</span></span>         |<span data-ttu-id="83a48-607">SharePoint Online에서 자산에 액세스할 수는 없지만 SharePoint Online에서 파일에 대 한 액세스가 거부 되더라도 CDN에서 자산에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-607">Cannot access the asset from SharePoint Online, but can access the asset from the CDN despite being denied access to the file in SharePoint Online</span></span>         |

<span data-ttu-id="83a48-608"><a name="CDNTroubleshooting"> </a></span><span class="sxs-lookup"><span data-stu-id="83a48-608"><a name="CDNTroubleshooting"> </a></span></span>
## <a name="troubleshooting-the-office-365-cdn"></a><span data-ttu-id="83a48-609">Office 365 CDN 문제 해결</span><span class="sxs-lookup"><span data-stu-id="83a48-609">Troubleshooting the Office 365 CDN</span></span>

<span data-ttu-id="83a48-610"><a name="CDNConfirm"> </a></span><span class="sxs-lookup"><span data-stu-id="83a48-610"><a name="CDNConfirm"> </a></span></span>
### <a name="how-do-i-confirm-that-assets-are-being-served-by-the-cdn"></a><span data-ttu-id="83a48-611">CDN에서 자산을 제공 하는지 확인 하려면 어떻게 해야 합니까?</span><span class="sxs-lookup"><span data-stu-id="83a48-611">How do I confirm that assets are being served by the CDN?</span></span>

<span data-ttu-id="83a48-612">페이지에 CDN 자산의 링크를 추가한 후에는 해당 페이지로 이동 하 고 이미지를 렌더링 하 고 이미지 URL을 검토 한 후에 해당 페이지를 마우스 오른쪽 단추로 클릭 하 여 해당 자산이 CDN에서 처리 되 고 있는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-612">Once you have added links to CDN assets to a page, you can confirm that the asset is being served from the CDN by browsing to the page, right clicking on the image once it has rendered and reviewing the image URL.</span></span>

<span data-ttu-id="83a48-613">또한 브라우저의 개발자 도구를 사용 하 여 페이지의 각 자산에 대 한 URL을 보거나 타사 네트워크 추적 도구를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-613">You can also use your browser's developer tools to view the URL for each asset on a page, or use a third party network trace tool.</span></span>

> [!NOTE]
> <span data-ttu-id="83a48-614">Fiddler와 같은 네트워크 도구를 사용 하 여 SharePoint 페이지에서 자산을 렌더링 하지 않는 사용자의 자산을 테스트 하는 경우 URL이 SharePoint Online 테 넌 트의 `https://yourdomain.sharepoint.com`루트 URL 인 GET 요청에 referer 헤더 "referer:"를 수동으로 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-614">If you use a network tool such as Fiddler to test your assets outside of rendering the asset from a SharePoint page, you must manually add the referer header “Referer: `https://yourdomain.sharepoint.com`” to the GET request where the URL is the root URL of your SharePoint Online tenant.</span></span>

<span data-ttu-id="83a48-615">SharePoint Online에서 제공 되는 referer가 있어야 하기 때문에 CDN Url을 웹 브라우저에서 직접 테스트할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-615">You cannot test CDN URLs directly in a web browser because you must have a referer coming from SharePoint Online.</span></span> <span data-ttu-id="83a48-616">그러나 SharePoint 페이지에 CDN 자산 URL을 추가한 다음 브라우저에서 페이지를 열면 CDN 자산이 페이지에 렌더링 된 것을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-616">However, if you add the CDN asset URL to a SharePoint page and then open the page in a browser, you will see the CDN asset rendered on the page.</span></span>

<span data-ttu-id="83a48-617">Microsoft Edge 브라우저에서 개발자 도구를 사용 하는 방법에 대 한 자세한 내용은 [Microsoft Edge 개발자 도구](https://docs.microsoft.com/microsoft-edge/devtools-guide)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="83a48-617">For more information on using the developer tools in the Microsoft Edge browser, see [Microsoft Edge Developer Tools](https://docs.microsoft.com/microsoft-edge/devtools-guide).</span></span>

<span data-ttu-id="83a48-618">[SharePoint 개발자 패턴 및 관례](https://aka.ms/sppnp-videos) 에서 호스트 되는 간단한 비디오를 시청 하려면 cdn 채널을 사용 하는 방법에 대 한 자세한 내용은 [cdn 사용법 확인 및 최적의 네트워크 연결](https://www.youtube.com/watch?v=ClCtBAtGjE8&list=PLR9nK3mnD-OWMfr1BA9mr5oCw2aJXw4WA&index=5)확인을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="83a48-618">To watch a short video hosted in the [SharePoint Developer Patterns and Practices YouTube channel](https://aka.ms/sppnp-videos) demonstrating how to verify that your CDN is working, please see [Verifying your CDN usage and ensuring optimal network connectivity](https://www.youtube.com/watch?v=ClCtBAtGjE8&list=PLR9nK3mnD-OWMfr1BA9mr5oCw2aJXw4WA&index=5).</span></span>

### <a name="why-are-assets-from-a-new-origin-unavailable"></a><span data-ttu-id="83a48-619">새 원본의 자산을 사용할 수 없는 이유는 무엇 인가요?</span><span class="sxs-lookup"><span data-stu-id="83a48-619">Why are assets from a new origin unavailable?</span></span>
<span data-ttu-id="83a48-620">새 원본의 자산은 CDN을 통해 등록이 전파 되 고 자산이 원본에서 CDN 저장소로 업로드 되는 시간을 차지 하므로 즉시 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-620">Assets in new origins will not immediately be available for use, as it takes time for the registration to propagate through the CDN and for the assets to be uploaded from the origin to CDN storage.</span></span> <span data-ttu-id="83a48-621">CDN에서 자산을 사용할 수 있어야 하는 시간은 자산의 수와 파일 크기에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-621">The time required for assets to be available in the CDN depends on how many assets and the files sizes.</span></span>

### <a name="my-client-side-web-part-or-sharepoint-framework-solution-isnt-working"></a><span data-ttu-id="83a48-622">클라이언트 쪽 웹 파트 또는 SharePoint Framework 솔루션이 작동 하지 않는 경우</span><span class="sxs-lookup"><span data-stu-id="83a48-622">My client-side web part or SharePoint Framework solution isn't working</span></span>

<span data-ttu-id="83a48-623">공용 원본에 대해 Office 365 CDN을 사용 하도록 설정 하면 CDN 서비스가 다음과 같은 기본 원본을 자동으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-623">When you enable the Office 365 CDN for public origins, the CDN service automatically creates these default origins:</span></span>

+ <span data-ttu-id="83a48-624">\*/MASTERPAGE</span><span class="sxs-lookup"><span data-stu-id="83a48-624">\*/MASTERPAGE</span></span>
+ <span data-ttu-id="83a48-625">\*/VSTYLE 라이브러리</span><span class="sxs-lookup"><span data-stu-id="83a48-625">\*/STYLE LIBRARY</span></span>
+ <span data-ttu-id="83a48-626">\*/CLIENTSIDEASSETS</span><span class="sxs-lookup"><span data-stu-id="83a48-626">\*/CLIENTSIDEASSETS</span></span>

<span data-ttu-id="83a48-627">\*/Clientsideassets 원본이 누락 되 면 SharePoint Framework 솔루션은 실패 하 고 경고 또는 오류 메시지는 생성 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-627">If the \*/clientsideassets origin is missing, SharePoint Framework solutions will fail, and no warning or error messages are generated.</span></span> <span data-ttu-id="83a48-628">**$True**으로 _설정 된 CDN_ 또는 원본이 수동으로 삭제 되었기 때문에이 원본이 누락 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-628">This origin may be missing either because the CDN was enabled with the _-NoDefaultOrigins_ parameter set to **$true**, or because the origin was manually deleted.</span></span>

<span data-ttu-id="83a48-629">다음 PowerShell 명령을 사용 하 여 \*/CLIENTSIDEASSETS 원본이 있는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-629">You can check to see if the \*/CLIENTSIDEASSETS origin is present with the following PowerShell command:</span></span>

``` powershell
Get-SPOTenantCdnOrigin -CdnType Public -OriginUrl */CLIENTSIDEASSETS
```

<span data-ttu-id="83a48-630">또는 Office 365 CLI를 통해 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-630">Or you can check with the Office 365 CLI:</span></span>

``` powershell
spo cdn origin list
```

<span data-ttu-id="83a48-631">PowerShell에서 원점을 추가 하려면:</span><span class="sxs-lookup"><span data-stu-id="83a48-631">To add the origin in PowerShell:</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */CLIENTSIDEASSETS
```

<span data-ttu-id="83a48-632">Office 365 CLI에서 원점을 추가 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-632">To add the origin in the Office 365 CLI:</span></span>

``` powershell
spo cdn origin add --origin */CLIENTSIDEASSETS
```

### <a name="what-powershell-modules-and-cli-shells-do-i-need-to-work-with-the-office-365-cdn"></a><span data-ttu-id="83a48-633">Office 365 CDN과 함께 작동 하는 데 필요한 PowerShell 모듈 및 CLI 셸에는 무엇 인가요?</span><span class="sxs-lookup"><span data-stu-id="83a48-633">What PowerShell modules and CLI shells do I need to work with the Office 365 CDN?</span></span>

<span data-ttu-id="83a48-634">**SharePoint Online 관리 셸** PowerShell 모듈 또는 **office 365 CLI**를 사용 하 여 office 365 CDN 작업을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a48-634">You can choose to work with the Office 365 CDN using either the **SharePoint Online Management Shell** PowerShell module or the **Office 365 CLI**.</span></span>

+ [<span data-ttu-id="83a48-635">SharePoint Online 관리 셸 시작</span><span class="sxs-lookup"><span data-stu-id="83a48-635">Getting started with SharePoint Online Management Shell</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)
+ [<span data-ttu-id="83a48-636">Office 365 CLI 설치</span><span class="sxs-lookup"><span data-stu-id="83a48-636">Installing the Office 365 CLI</span></span>](https://pnp.github.io/office365-cli/user-guide/installing-cli/)

## <a name="see-also"></a><span data-ttu-id="83a48-637">참고 항목</span><span class="sxs-lookup"><span data-stu-id="83a48-637">See also</span></span>

[<span data-ttu-id="83a48-638">콘텐츠 배달 네트워크</span><span class="sxs-lookup"><span data-stu-id="83a48-638">Content Delivery Networks</span></span>](https://aka.ms/o365cdns)

[<span data-ttu-id="83a48-639">Office 365의 네트워크 계획 및 성능 조정</span><span class="sxs-lookup"><span data-stu-id="83a48-639">Network planning and performance tuning for Office 365</span></span>](https://aka.ms/tune)

[<span data-ttu-id="83a48-640">SharePoint 성능 시리즈-Office 365 CDN 비디오 시리즈</span><span class="sxs-lookup"><span data-stu-id="83a48-640">SharePoint Performance Series - Office 365 CDN video series</span></span>](https://www.youtube.com/playlist?list=PLR9nK3mnD-OWMfr1BA9mr5oCw2aJXw4WA)
