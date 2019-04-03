---
title: sharepoint Online을 활용해 Office 365 콘텐츠 배달 네트워크(CDN) 사용하기
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 4/2/2019
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: bebb285f-1d54-4f79-90a5-94985afc6af8
description: Office 365 CDN (콘텐츠 배달 네트워크)을 사용 하 여 위치에 관계 없이 모든 사용자에 게 SharePoint Online 자산을 빠르게 배달 하는 방법에 대해 설명 하 고 콘텐츠에 액세스 하는 방법을 알아봅니다.
ms.openlocfilehash: a718c30a40209a8ee0c8e78700ed3eae72c8347c
ms.sourcegitcommit: 43d2b7e1d9932182c6cca5164d4d9096dcf4ed36
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/02/2019
ms.locfileid: "31039505"
---
# <a name="use-the-office-365-content-delivery-network-cdn-with-sharepoint-online"></a><span data-ttu-id="0cbb3-103">sharepoint Online을 활용해 Office 365 콘텐츠 배달 네트워크(CDN) 사용하기</span><span class="sxs-lookup"><span data-stu-id="0cbb3-103">Use the Office 365 Content Delivery Network (CDN) with SharePoint Online</span></span>

<span data-ttu-id="0cbb3-104">기본 제공 Office 365 Content Delivery Network(CDN)을 사용하여 정적 자산을 호스팅하여 SharePoint Online 페이지의 성능을 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-104">You can use the built-in Office 365 Content Delivery Network (CDN) to host static assets to provide better performance for your SharePoint Online pages.</span></span> <span data-ttu-id="0cbb3-105">Office 365 CDN은 정적 자산을 요청하는 브라우저에 더 가깝게 캐싱하여 성능을 향상시켜 다운로드 속도를 높이고 대기 시간을 줄이는 데 기여합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-105">The Office 365 CDN improves performance by caching static assets closer to the browsers requesting them, which helps to speed up downloads and reduce latency.</span></span> <span data-ttu-id="0cbb3-106">또한 Office 365 CDN은 향상 된 압축 및 HTTP 파이프라이닝을 위해 [http/2 프로토콜](https://en.wikipedia.org/wiki/HTTP/2) 을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-106">Also, the Office 365 CDN uses the [HTTP/2 protocol](https://en.wikipedia.org/wiki/HTTP/2) for improved compression and HTTP pipelining.</span></span> <span data-ttu-id="0cbb3-107">Office 365 CDN 서비스는 SharePoint Online 구독의 일부로 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-107">The Office 365 CDN service is included as part of your SharePoint Online subscription.</span></span>

<span data-ttu-id="0cbb3-108">Office 365 CDN은 여러 위치, 즉 _출발지_에 정적 자산을 호스트하고 글로벌 고속 네트워크에서 제공할 수 있는 여러 CDN으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-108">The Office 365 CDN is composed of multiple CDNs that allow you to host static assets in multiple locations, or _origins_, and serve them from global high-speed networks.</span></span> <span data-ttu-id="0cbb3-109">Office 365 CDN에서 호스팅하려는 콘텐츠의 종류에 따라 **공개** 출처, **비공개** 출처 또는 둘 다를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-109">Depending on the kind of content you want to host in the Office 365 CDN, you can add **public** origins, **private** origins or both.</span></span> <span data-ttu-id="0cbb3-110">public 및 private 원점과의 차이점에 대 한 자세한 내용은 [각 원점을 public 또는 private](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate) 중에서 선택 합니다 .를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-110">See [Choose whether each origin should be public or private](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate) for more information on the difference between public and private origins.</span></span>

<span data-ttu-id="0cbb3-111">![Office 365 CDN 개념 다이어그램] (media/O365-CDN/o365-cdn-flow-transparent.svg "Office 365 CDN 개념 다이어그램")</span><span class="sxs-lookup"><span data-stu-id="0cbb3-111">![Office 365 CDN conceptual diagram](media/O365-CDN/o365-cdn-flow-transparent.svg "Office 365 CDN conceptual diagram")</span></span>

<span data-ttu-id="0cbb3-112">cdns가 작동 하는 방식에 이미 익숙한 경우 테 넌 트에 Office 365 CDN을 사용 하도록 설정 하려면 몇 단계만 완료 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-112">If you are already familiar with the way that CDNs work, you only need to complete a few steps to enable the Office 365 CDN for your tenant.</span></span> <span data-ttu-id="0cbb3-113">이 항목에서는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-113">This topic describes how.</span></span> <span data-ttu-id="0cbb3-114">정적 자산 호스팅을 시작 하는 방법에 대 한 자세한 내용을 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-114">Read on for information about how to get started hosting your static assets.</span></span>

> [!TIP]
> <span data-ttu-id="0cbb3-115">특수 사용 시나리오에서는 office 365와 함께 사용할 수 있는 Microsoft에서 호스팅하는 다른 cdns가 있지만,이 항목에서는 office 365 CDN 범위를 벗어나므로 여기서 설명 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-115">There are other Microsoft-hosted CDNs that can be used with Office 365 for specialized usage scenarios, but are not discussed in this topic because they fall outside the scope of the Office 365 CDN.</span></span> <span data-ttu-id="0cbb3-116">자세한 내용은 [다른 Microsoft cdns](content-delivery-networks.md#other-microsoft-cdns)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-116">For more information, see [Other Microsoft CDNs](content-delivery-networks.md#other-microsoft-cdns).</span></span>

 **<span data-ttu-id="0cbb3-117">[Office 365의 네트워크 계획 및 성능 조정](https://aka.ms/tune)으로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-117">Head back to [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>**

## <a name="overview-of-working-with-the-office-365-cdn-in-sharepoint-online"></a><span data-ttu-id="0cbb3-118">SharePoint Online에서 Office 365 CDN 사용에 대 한 개요</span><span class="sxs-lookup"><span data-stu-id="0cbb3-118">Overview of working with the Office 365 CDN in SharePoint Online</span></span>

<span data-ttu-id="0cbb3-119">조직에 대해 Office 365 CDN을 설정 하려면 다음 기본 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-119">To set up the Office 365 CDN for your organization, you follow these basic steps:</span></span>

- [<span data-ttu-id="0cbb3-120">Office 365 CDN 배포 계획</span><span class="sxs-lookup"><span data-stu-id="0cbb3-120">Plan for deployment of the Office 365 CDN</span></span>](use-office-365-cdn-with-spo.md#plan-for-deployment-of-the-office-365-cdn)

  - <span data-ttu-id="0cbb3-121">[CDN에서 호스트할 정적 자산을 결정](use-office-365-cdn-with-spo.md#CDNAssets)합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-121">[Determine which static assets you want to host on the CDN](use-office-365-cdn-with-spo.md#CDNAssets).</span></span>
  - <span data-ttu-id="0cbb3-122">[자산을 저장할 위치를 결정](use-office-365-cdn-with-spo.md#CDNStoreAssets)합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-122">[Determine where you want to store your assets](use-office-365-cdn-with-spo.md#CDNStoreAssets).</span></span> <span data-ttu-id="0cbb3-123">이 위치는 SharePoint 사이트, 라이브러리 또는 폴더 일 수 있으며 _출처_라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-123">This location can be a SharePoint site, library or folder and is called an _origin_.</span></span>
  - <span data-ttu-id="0cbb3-124">[각 원본이 공용 또는 개인 인지 여부를 선택](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate)합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-124">[Choose whether each origin should be public or private](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate).</span></span> <span data-ttu-id="0cbb3-125">공용 및 개인 형식 둘 다의 원본을 여러 개 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-125">You can add multiple origins of both public and private types.</span></span>

- <span data-ttu-id="0cbb3-126">PowerShell 또는 SharePoint Online CLI를 사용 하 여 CDN을 설정 하 고 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-126">Set up and configure the CDN, using either PowerShell or the SharePoint Online CLI</span></span>

  - [<span data-ttu-id="0cbb3-127">SharePoint Online 관리 셸을 사용 하 여 CDN을 설정 하 고 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-127">Set up and configure the CDN by using the SharePoint Online Management Shell</span></span>](use-office-365-cdn-with-spo.md#CDNSetupinPShell)
  - [<span data-ttu-id="0cbb3-128">Office 365 CLI를 사용 하 여 CDN을 설정 하 고 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-128">Set up and configure the CDN by using the Office 365 CLI</span></span>](use-office-365-cdn-with-spo.md#CDNSetupinCLI)

  <span data-ttu-id="0cbb3-129">이 단계를 완료 하면 다음이 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-129">When you complete this step, you will have:</span></span>

  - <span data-ttu-id="0cbb3-130">조직에 CDN을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-130">Enabled the CDN for your organization.</span></span>
  - <span data-ttu-id="0cbb3-131">각 원점을 공용 또는 개인으로 식별 하는 출처를 추가 했습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-131">Added your origins, identifying each origin as public or private.</span></span>

<span data-ttu-id="0cbb3-132">설치를 완료 한 후에는 시간에 따른 [Office 365 CDN을 관리할](use-office-365-cdn-with-spo.md#CDNManage) 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-132">Once you're done with setup, you can [Manage the Office 365 CDN](use-office-365-cdn-with-spo.md#CDNManage) over time by:</span></span>
  
- <span data-ttu-id="0cbb3-133">자산 추가, 업데이트 및 제거</span><span class="sxs-lookup"><span data-stu-id="0cbb3-133">Adding, updating, and removing assets</span></span>
- <span data-ttu-id="0cbb3-134">원본 추가 및 제거</span><span class="sxs-lookup"><span data-stu-id="0cbb3-134">Adding and removing origins</span></span>
- <span data-ttu-id="0cbb3-135">CDN 정책 구성</span><span class="sxs-lookup"><span data-stu-id="0cbb3-135">Configuring CDN policies</span></span>
- <span data-ttu-id="0cbb3-136">필요한 경우 CDN을 사용 하지 않도록 설정</span><span class="sxs-lookup"><span data-stu-id="0cbb3-136">If necessary, disabling the CDN</span></span>

<span data-ttu-id="0cbb3-137">마지막으로, [cdn 자산을 사용](use-office-365-cdn-with-spo.md#using-your-cdn-assets) 하 여 공용 및 개인 원본 모두에서 cdn 자산에 액세스 하는 방법에 대해 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-137">Finally, see [Using your CDN assets](use-office-365-cdn-with-spo.md#using-your-cdn-assets) to learn about accessing your CDN assets from both public and private origins.</span></span>

<span data-ttu-id="0cbb3-138">일반적인 문제를 해결 하는 방법에 대 한 지침은 [Office 365 CDN 문제 해결](use-office-365-cdn-with-spo.md#CDNTroubleshooting) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-138">See [Troubleshooting the Office 365 CDN](use-office-365-cdn-with-spo.md#CDNTroubleshooting) for guidance on resolving common issues.</span></span>

## <a name="plan-for-deployment-of-the-office-365-cdn"></a><span data-ttu-id="0cbb3-139">Office 365 CDN 배포 계획</span><span class="sxs-lookup"><span data-stu-id="0cbb3-139">Plan for deployment of the Office 365 CDN</span></span>

<span data-ttu-id="0cbb3-140">office 365 테 넌 트에 대 한 office 365 CDN을 배포 하기 전에 계획 프로세스의 일부로 다음과 같은 요인을 고려해 야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-140">Before you deploy the Office 365 CDN for your Office 365 tenant, you should consider the following factors as part of your planning process.</span></span>

  - [<span data-ttu-id="0cbb3-141">CDN에서 호스트할 정적 자산 확인</span><span class="sxs-lookup"><span data-stu-id="0cbb3-141">Determine which static assets you want to host on the CDN</span></span>](use-office-365-cdn-with-spo.md#CDNAssets)
  - [<span data-ttu-id="0cbb3-142">자산을 저장할 위치 결정</span><span class="sxs-lookup"><span data-stu-id="0cbb3-142">Determine where you want to store your assets</span></span>](use-office-365-cdn-with-spo.md#CDNStoreAssets)
  - [<span data-ttu-id="0cbb3-143">각 출처를 public 또는 private로 설정할지를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-143">Choose whether each origin should be public or private</span></span>](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate)

### <a name="determine-which-static-assets-you-want-to-host-on-the-cdn"></a><span data-ttu-id="0cbb3-144">CDN에서 호스트할 정적 자산 확인</span><span class="sxs-lookup"><span data-stu-id="0cbb3-144">Determine which static assets you want to host on the CDN</span></span>
<a name="CDNAssets"> </a>

<span data-ttu-id="0cbb3-145">일반적으로 cdns는 _정적 자산_을 호스트 하거나 자주 변경 되지 않는 자산을 호스팅하는 데 가장 효과적입니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-145">In general, CDNs are most effective for hosting _static assets_, or assets that don't change very often.</span></span> <span data-ttu-id="0cbb3-146">다음과 같은 조건 중 일부 또는 전부를 충족 하는 파일을 식별 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-146">A good rule of thumb is to identify files that meet some or all of these conditions:</span></span>

- <span data-ttu-id="0cbb3-147">페이지 로드 시간에 큰 영향을 줄 수 있는 페이지 (스크립트 및 이미지 등)에 포함 된 정적 파일</span><span class="sxs-lookup"><span data-stu-id="0cbb3-147">Static files embedded in a page (like scripts and images) that may have a significant incremental impact on page load times</span></span>
- <span data-ttu-id="0cbb3-148">실행 파일 및 설치 파일과 같은 큰 파일</span><span class="sxs-lookup"><span data-stu-id="0cbb3-148">Large files like executables and installation files</span></span>
- <span data-ttu-id="0cbb3-149">스트리밍 미디어 파일</span><span class="sxs-lookup"><span data-stu-id="0cbb3-149">Streaming media files</span></span>
- <span data-ttu-id="0cbb3-150">클라이언트 쪽 코드를 지 원하는 리소스 라이브러리</span><span class="sxs-lookup"><span data-stu-id="0cbb3-150">Resource libraries that support client-side code</span></span>

<span data-ttu-id="0cbb3-151">예를 들어 사이트 이미지 및 스크립트와 마찬가지로 반복적으로 요청 되는 작은 파일은 사이트 렌더링 성능을 크게 향상 시키고, CDN 원본에 추가 하는 경우 SharePoint Online 사이트의 부하를 점차적으로 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-151">For example, small files that are repeatedly requested like site images and scripts can significantly improve site rendering performance and incrementally reduce the load on your SharePoint Online sites when you add them to a CDN origin.</span></span> <span data-ttu-id="0cbb3-152">설치 실행 파일이 나 비디오 파일과 같은 더 큰 파일을 CDN에서 다운로드 하거나 스트리밍할 수 있으므로, 자주 액세스 하지 않더라도 SharePoint Online 사이트에 대 한 부하를 긍정적으로 줄이는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-152">Larger files such as installation executables or video files can be downloaded or streamed from the CDN, delivering a positive performance impact and subsequent reduction of the load on your SharePoint Online site, even if they are not accessed as often.</span></span>

<span data-ttu-id="0cbb3-153">파일을 기준으로 성능 향상은 가장 가까운 CDN 끝점에 대 한 클라이언트의 근접성, 로컬 네트워크의 일시적 조건 등의 다양 한 요인에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-153">Performance improvement on a per-file basis is dependent on many factors, including the client's proximity to the nearest CDN endpoint, transient conditions on the local network, and so forth.</span></span> <span data-ttu-id="0cbb3-154">많은 정적 파일은 매우 작으며 Office 365에서 1 초 이내에 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-154">Many static files are quite small, and can be downloaded from Office 365 in less than a second.</span></span> <span data-ttu-id="0cbb3-155">그러나 웹 페이지에는 다운로드 시간이 누적 되는 여러 개의 포함 된 파일이 몇 초 동안 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-155">However, a web page may contain many embedded files with a cumulative download time of several seconds.</span></span> <span data-ttu-id="0cbb3-156">CDN에서 이러한 파일을 처리 하면 전체 페이지 로드 시간이 크게 줄어들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-156">Serving these files from the CDN can significantly reduce the overall page load time.</span></span> <span data-ttu-id="0cbb3-157">[CDN에서 제공 하는 성능 향상은 무엇 인가요?](content-delivery-networks.md#what-performance-gains-does-a-cdn-provide) 예를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-157">See [What performance gains does a CDN provide?](content-delivery-networks.md#what-performance-gains-does-a-cdn-provide) for an example.</span></span>

### <a name="determine-where-you-want-to-store-your-assets"></a><span data-ttu-id="0cbb3-158">자산을 저장할 위치 결정</span><span class="sxs-lookup"><span data-stu-id="0cbb3-158">Determine where you want to store your assets</span></span>
<a name="CDNStoreAssets"> </a>

<span data-ttu-id="0cbb3-159">CDN은 _근원_이라는 위치에서 자산을 페치합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-159">The CDN fetches your assets from a location called an _origin_.</span></span> <span data-ttu-id="0cbb3-160">원본은 URL에서 액세스할 수 있는 SharePoint 사이트, 문서 라이브러리 또는 폴더가 될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-160">An origin can be a SharePoint site, document library or folder that is accessible by a URL.</span></span> <span data-ttu-id="0cbb3-161">조직의 원본을 지정할 때 유연성이 뛰어납니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-161">You have great flexibility when you specify origins for your organization.</span></span> <span data-ttu-id="0cbb3-162">예를 들어 모든 cdn 자산을 추가 하려는 원본이 여러 개 있거나 하나만 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-162">For example, you can specify multiple origins or a single origin where you want to put all your CDN assets.</span></span> <span data-ttu-id="0cbb3-163">조직의 공용 또는 개인 원본을 둘 다 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-163">You can choose to have both public or private origins for your organization.</span></span> <span data-ttu-id="0cbb3-164">대부분의 조직에서는 두 가지를 조합 하 여 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-164">Most organizations will choose to implement a combination of the two.</span></span>

<span data-ttu-id="0cbb3-165">폴더 또는 문서 라이브러리와 같은 원본에 대 한 새 컨테이너를 만들고 CDN에서 사용 가능 하도록 설정할 파일을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-165">You can create new container for your origins such as folders or document libraries, and add files you want to make available from the CDN.</span></span> <span data-ttu-id="0cbb3-166">cdn에서 사용 하려는 특정 자산의 집합이 있고 cdn 자산 집합을 컨테이너의 해당 파일로 제한 하려는 경우에는이 방법이 좋은 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-166">This is a good approach if you have a specific set of assets you want to be available from the CDN, and want to restrict the set of CDN assets to only those files in the container.</span></span>

<span data-ttu-id="0cbb3-167">기존 사이트 모음, 사이트, 라이브러리 또는 폴더를 원본으로 구성 하 여 해당 컨테이너의 모든 적합 한 자산을 CDN에서 사용할 수 있도록 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-167">You can also configure an existing site collection, site, library or folder as an origin, which will make all eligible assets in the container available from the CDN.</span></span> <span data-ttu-id="0cbb3-168">기존 컨테이너를 원본으로 추가 하기 전에 익명 액세스 또는 권한 없는 사용자에 게 자산을 실수로 노출 하지 않도록 하기 위해 해당 콘텐츠 및 사용 권한을 알고 있는지 확인 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-168">Before you add an existing container as an origin, it's important to make sure you are aware of its contents and permissions so you do not inadvertently expose assets to anonymous access or unauthorized users.</span></span>

<span data-ttu-id="0cbb3-169">cdn에서 원본에 있는 콘텐츠를 제외 하도록 _cdn 정책을_ 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-169">You can define _CDN policies_ to exclude content in your origins from the CDN.</span></span> <span data-ttu-id="0cbb3-170">CDN 정책은 공용 또는 개인 원본에서 _파일 형식_ 및 _사이트 분류_와 같은 특성을 통해 자산을 제외 하 고, 정책에 지정 하는 cdntype (private 또는 public)의 모든 원본에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-170">CDN policies exclude assets in public or private origins by attributes such as _file type_ and _site classification_, and are applied to all origins of the CdnType (private or public) you specify in the policy.</span></span> <span data-ttu-id="0cbb3-171">예를 들어 여러 하위 사이트가 포함 된 사이트로 구성 된 개인 출처를 추가 하는 경우 해당 분류가 적용 된 사이트의 콘텐츠가 CDN에서 처리 되지 않도록 **비밀 우편** 으로 표시 된 사이트를 제외 하는 정책을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-171">For example, if you add a private origin consisting of a site that contains multiple subsites, you can define a policy to exclude sites marked as **Confidential** so content from sites with that classification applied will not be served from the CDN.</span></span> <span data-ttu-id="0cbb3-172">정책은 CDN에 추가한 _모든_ 개인 출처의 콘텐츠에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-172">The policy will apply to content from _all_ private origins you have added to the CDN.</span></span>
  
<span data-ttu-id="0cbb3-173">원본 수가 많을 수록 CDN 서비스에서 요청을 처리 하는 데 소요 되는 시간에 더 많은 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-173">Keep in mind that the greater the number of origins, the greater the impact on the time it takes the CDN service to process requests.</span></span> <span data-ttu-id="0cbb3-174">원본 수를 가능한 한 많이 제한 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-174">We recommend that you limit the number of origins as much as possible.</span></span>
  
### <a name="choose-whether-each-origin-should-be-public-or-private"></a><span data-ttu-id="0cbb3-175">각 출처를 public 또는 private로 설정할지를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-175">Choose whether each origin should be public or private</span></span>
<a name="CDNOriginChoosePublicPrivate"> </a>

<span data-ttu-id="0cbb3-176">출처를 식별할 때는 _공용_ 또는 _비공개로_설정할 지 여부를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-176">When you identify an origin, you specify whether it should be made _public_ or _private_.</span></span> <span data-ttu-id="0cbb3-177">공용 원본에서 cdn 자산에 대 한 액세스는 익명으로 진행 되며 개인 원본에 있는 cdn 콘텐츠는 보안을 강화 하기 위해 동적으로 생성 된 토큰에 의해 보호 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-177">Access to CDN assets in public origins is anonymous, and CDN content in private origins is secured by dynamically generated tokens for greater security.</span></span> <span data-ttu-id="0cbb3-178">선택 하는 옵션에 관계 없이 Microsoft는 CDN 자체를 관리 하는 경우 모든 사용자를 대상으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-178">Regardless of which option you choose, Microsoft does all the heavy lifting for you when it comes to administration of the CDN itself.</span></span> <span data-ttu-id="0cbb3-179">또한 CDN을 설정 하 고 원본을 식별 한 후 나중에 생각이 바뀔 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-179">Also, you can change your mind later, after you've set up the CDN and identified your origins.</span></span>

<span data-ttu-id="0cbb3-180">공용 및 개인 옵션은 모두 비슷한 성능을 제공 하지만 각각에 고유한 특성 및 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-180">Both public and private options provide similar performance gains, but each has unique attributes and advantages.</span></span>

<span data-ttu-id="0cbb3-181">Office 365 CDN 내의 **공용** 원본에는 익명으로 액세스할 수 있으며 자산에 대 한 URL을 가진 모든 사용자가 호스트 된 자산에 액세스 하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-181">**Public** origins within the Office 365 CDN are accessible anonymously, and hosted assets can be accessed by anyone who has the URL to the asset.</span></span> <span data-ttu-id="0cbb3-182">공개 출처의 콘텐츠에 대한 액세스는 익명이기 때문에 캐시 javascript 파일, 스크립트, 아이콘 및 이미지와 같은 중요하지 않은 일반 콘텐츠에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-182">Because access to content in public origins is anonymous, you should only use them to cache non-sensitive generic content such as javascript files, scripts, icons and images.</span></span>

<span data-ttu-id="0cbb3-183">Office 365 CDN의 **비공개** 출처는 SharePoint Online 문서 라이브러리, 사이트 및 비디오와 같은 미디어와 같은 사용자 콘텐츠에 대한 비공개 액세스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-183">**Private** origins within the Office 365 CDN provide private access to user content such as SharePoint Online document libraries, sites and media such as videos.</span></span> <span data-ttu-id="0cbb3-184">원본 문서 라이브러리나 저장 위치에 대 한 사용 권한이 있는 사용자만 액세스할 수 있도록 개인 원본의 콘텐츠에 대 한 액세스를 동적으로 생성 된 토큰으로 보호 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-184">Access to content in private origins is secured by dynamically generated tokens so it can only be accessed by users with permissions to the original document library or storage location.</span></span> <span data-ttu-id="0cbb3-185">Office 365 CDN의 비공개 출처는 sharepoint online 콘텐츠에만 사용할 수 있으며, sharepoint online 테 넌 트에서 리디렉션을 통해서만 개인 원본에 있는 자산에만 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-185">Private origins in the Office 365 CDN can only be used for SharePoint Online content, and you can only access assets in private origins through redirection from your SharePoint Online tenant.</span></span>

<span data-ttu-id="0cbb3-186">비공개 원본의 자산에 대 한 CDN 액세스에 대 한 자세한 내용은 전용 원본 [에 자산 사용](use-office-365-cdn-with-spo.md#using-assets-in-private-origins)에서 작업을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-186">You can read more about how CDN access to assets in a private origin works in [Using assets in private origins](use-office-365-cdn-with-spo.md#using-assets-in-private-origins).</span></span>

#### <a name="attributes-and-advantages-of-hosting-assets-in-public-origins"></a><span data-ttu-id="0cbb3-187">공개 원본에서의 자산 호스팅 특성 및 장점</span><span class="sxs-lookup"><span data-stu-id="0cbb3-187">Attributes and advantages of hosting assets in public origins</span></span>
  
- <span data-ttu-id="0cbb3-188">공용 원본에 표시 되는 자산은 모든 사용자가 익명으로 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-188">Assets exposed in a public origin are accessible by everyone anonymously.</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="0cbb3-189">사용자 정보가 포함 된 리소스를 배치 하거나 조직에서 공용 원본으로 중요 한 것으로 간주 해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-189">You should never place resources that contain user information or are considered sensitive to your organization in a public origin.</span></span>
- <span data-ttu-id="0cbb3-190">공개 원점에서 자산을 제거 하는 경우에는 해당 자산을 캐시에서 최대 30 일 동안 계속 사용할 수 있습니다. 그러나 15 분 내에 CDN의 자산에 대 한 링크가 무효화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-190">If you remove an asset from a public origin, the asset may continue to be available for up to 30 days from the cache; however, we will invalidate links to the asset in the CDN within 15 minutes.</span></span>
- <span data-ttu-id="0cbb3-191">공용 원점에 스타일 시트 (CSS 파일)를 호스트 하는 경우 코드 내에 상대 경로와 uri를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-191">When you host style sheets (CSS files) in a public origin, you can use relative paths and URIs within the code.</span></span> <span data-ttu-id="0cbb3-192">즉, 배경 이미지 및 다른 개체를 호출 하는 자산의 위치를 기준으로 해당 위치를 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-192">This means that you can reference the location of background images and other objects relative to the location of the asset that's calling it.</span></span>
- <span data-ttu-id="0cbb3-193">공용 원본의 URL을 하드 코딩 하는 것은 좋지만, 이렇게 하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-193">While you can hard code a public origin's URL, doing so is not recommended.</span></span> <span data-ttu-id="0cbb3-194">이는 CDN에 대 한 액세스를 사용할 수 없는 경우 URL이 SharePoint Online에서 조직에 자동으로 확인 되지 않으며 링크 및 기타 오류가 발생할 수 있기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-194">The reason for this is that if access to the CDN becomes unavailable, the URL will not automatically resolve to your organization in SharePoint Online and might result in broken links and other errors.</span></span>
- <span data-ttu-id="0cbb3-195">공용 원본에 대해 포함 되는 기본 파일 형식은 .css, eot, .gif, .ico, .jpeg, .jpg,. ttf 및. w o v,. p s v,.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-195">The default file types that are included for public origins are .css, .eot, .gif, .ico, .jpeg, .jpg, .js, .map, .png, .svg, .ttf, and .woff.</span></span> <span data-ttu-id="0cbb3-196">추가 파일 형식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-196">You can specify additional file types.</span></span>
- <span data-ttu-id="0cbb3-197">지정한 사이트 분류에 의해 식별 된 자산을 제외 하도록 정책을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-197">You can configure a policy to exclude assets that have been identified by site classifications that you specify.</span></span> <span data-ttu-id="0cbb3-198">예를 들어, 허용 되는 파일 형식이 고 공용 원본에 있는 경우에도 "기밀" 또는 "제한"으로 표시 된 모든 자산을 제외 하도록 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-198">For example, you can choose to exclude all assets that are marked as "confidential" or "restricted" even if they are an allowed file type and are located in a public origin.</span></span>

#### <a name="attributes-and-advantages-of-hosting-assets-in-private-origins"></a><span data-ttu-id="0cbb3-199">전용 원본에서의 자산 호스팅의 특성 및 장점</span><span class="sxs-lookup"><span data-stu-id="0cbb3-199">Attributes and advantages of hosting assets in private origins</span></span>

- <span data-ttu-id="0cbb3-200">비공개 출처는 SharePoint Online 자산에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-200">Private origins can only be used for SharePoint Online assets.</span></span>
- <span data-ttu-id="0cbb3-201">사용자는 컨테이너에 대 한 액세스 권한이 있는 경우에만 비공개 원본의 자산에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-201">Users can only access the assets from a private origin if they have permissions to access the container.</span></span> <span data-ttu-id="0cbb3-202">이러한 자산에 대 한 익명 액세스는 차단 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-202">Anonymous access to these assets is prevented.</span></span>
- <span data-ttu-id="0cbb3-203">개인 원본에 있는 자산은 SharePoint Online 테 넌 트에서 참조 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-203">Assets in private origins must be referred from the SharePoint Online tenant.</span></span> <span data-ttu-id="0cbb3-204">사설 CDN 자산에 직접 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-204">Direct access to private CDN assets does not work.</span></span>
- <span data-ttu-id="0cbb3-205">비공개 원본에서 자산을 제거 하는 경우에는 자산을 캐시에서 한 시간까지 계속 사용할 수 있습니다. 그러나 자산의 제거 후 15 분 이내에 CDN의 자산에 대 한 링크가 무효화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-205">If you remove an asset from the private origin, the asset may continue to be available for up to an hour from the cache; however, we will invalidate links to the asset in the CDN within 15 minutes of the asset's removal.</span></span>
- <span data-ttu-id="0cbb3-206">전용 원본에 대해 포함 되는 기본 파일 형식은 .gif, .ico, .jpeg, .jpg, .js 및 .png입니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-206">The default file types that are included for private origins are .gif, .ico, .jpeg, .jpg, .js, and .png.</span></span> <span data-ttu-id="0cbb3-207">추가 파일 형식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-207">You can specify additional file types.</span></span>
- <span data-ttu-id="0cbb3-208">공용 출처와 마찬가지로 와일드 카드를 사용 하 여 폴더 또는 문서 라이브러리 내의 모든 자산을 포함 하는 경우에도 사용자가 지정한 사이트 분류에 의해 식별 된 자산을 제외 하도록 정책을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-208">Just like with public origins, you can configure a policy to exclude assets that have been identified by site classifications that you specify even if you use wildcards to include all assets within a folder or document library.</span></span>

<span data-ttu-id="0cbb3-209">office 365 CDN, 일반 CDN 개념 및 office 365 테 넌 트에서 사용할 수 있는 기타 Microsoft cdns를 사용 하는 이유에 대 한 자세한 내용은 [콘텐츠 배달 네트워크](content-delivery-networks.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-209">For more information about why to use the Office 365 CDN, general CDN concepts, and other Microsoft CDNs you can use with your Office 365 tenant, see [Content Delivery Networks](content-delivery-networks.md).</span></span>

### <a name="default-cdn-origins"></a><span data-ttu-id="0cbb3-210">기본 CDN 원본</span><span class="sxs-lookup"><span data-stu-id="0cbb3-210">Default CDN origins</span></span>

<span data-ttu-id="0cbb3-211">별도로 지정 하지 않으면 office 365에서 office 365 CDN을 사용 하도록 설정할 때 기본 원본을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-211">Unless you specify otherwise, Office 365 sets up some default origins for you when you enable the Office 365 CDN.</span></span> <span data-ttu-id="0cbb3-212">처음에 프로 비전 하지 않을 경우에는 설치를 완료 한 후 이러한 원본을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-212">If you initially opt not to provision them, you can add these origins after you complete setup.</span></span> <span data-ttu-id="0cbb3-213">기본 원본에 대 한 설정을 건너뛰고이를 수행 하는 특별 한 이유가 있는 경우를 이해 하지 않으면 CDN을 사용 하도록 설정할 때이 설정의 생성을 허용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-213">Unless you understand the consequences of skipping the setup of default origins and have a specific reason for doing so, you should allow them to be created when you enable the CDN.</span></span>
  
<span data-ttu-id="0cbb3-214">기본 개인 CDN 원본:</span><span class="sxs-lookup"><span data-stu-id="0cbb3-214">Default private CDN origins:</span></span>
  
- <span data-ttu-id="0cbb3-215">\*/userphoto.aspx</span><span class="sxs-lookup"><span data-stu-id="0cbb3-215">\*/userphoto.aspx</span></span>
- <span data-ttu-id="0cbb3-216">\*/cusets</span><span class="sxs-lookup"><span data-stu-id="0cbb3-216">\*/siteassets</span></span>

<span data-ttu-id="0cbb3-217">기본 공용 CDN 원본:</span><span class="sxs-lookup"><span data-stu-id="0cbb3-217">Default public CDN origins:</span></span>
  
- <span data-ttu-id="0cbb3-218">\*/masterpage</span><span class="sxs-lookup"><span data-stu-id="0cbb3-218">\*/masterpage</span></span>
- <span data-ttu-id="0cbb3-219">\*/restyle 라이브러리</span><span class="sxs-lookup"><span data-stu-id="0cbb3-219">\*/style library</span></span>
- <span data-ttu-id="0cbb3-220">\*/reclient자산과 자산</span><span class="sxs-lookup"><span data-stu-id="0cbb3-220">\*/clientsideassets</span></span>

> [!NOTE]
> <span data-ttu-id="0cbb3-221">_clientsideassets_ 12 월 2017에 Office 365 CDN 서비스에 추가 된 기본 공용 원본입니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-221">_clientsideassets_ is a default public origin that was added to the Office 365 CDN service in December 2017.</span></span> <span data-ttu-id="0cbb3-222">CDN에서 SharePoint Framework 솔루션이 작동 하려면이 원본이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-222">This origin must be present in order for SharePoint Framework solutions in the CDN to work.</span></span> <span data-ttu-id="0cbb3-223">Office 365 cdn을 12 월 2017 이전에 사용 하도록 설정 했거나 cdn을 사용 하도록 설정 했을 때 기본 원본 설치를 건너뛴 경우이 원본을 수동으로 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-223">If you enabled the Office 365 CDN prior to December 2017, or if you skipped setup of default origins when you enabled the CDN, you can manually add this origin.</span></span> <span data-ttu-id="0cbb3-224">자세한 내용은 [내 클라이언트 쪽 웹 파트 또는 SharePoint Framework 솔루션이 작동 하지 않는](use-office-365-cdn-with-spo.md#my-client-side-web-part-or-sharepoint-framework-solution-isnt-working)경우를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-224">For more information, see [My client-side web part or SharePoint Framework solution isn't working](use-office-365-cdn-with-spo.md#my-client-side-web-part-or-sharepoint-framework-solution-isnt-working).</span></span>

## <a name="set-up-and-configure-the-office-365-cdn-by-using-the-sharepoint-online-management-shell"></a><span data-ttu-id="0cbb3-225">SharePoint Online 관리 셸을 사용 하 여 Office 365 CDN을 설정 하 고 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-225">Set up and configure the Office 365 CDN by using the SharePoint Online Management Shell</span></span>
<a name="CDNSetupinPShell"> </a>

<span data-ttu-id="0cbb3-226">이 섹션의 절차를 수행 하려면 sharepoint online 관리 셸을 사용 하 여 sharepoint online에 연결 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-226">The procedures in this section require you to use the SharePoint Online Management Shell to connect to SharePoint Online.</span></span> <span data-ttu-id="0cbb3-227">자세한 내용은 [SharePoint Online PowerShell에 연결을](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-227">For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span></span>
  
<span data-ttu-id="0cbb3-228">sharepoint online 관리 셸을 사용 하 여 sharepoint online에서 자산을 호스트 하도록 CDN을 설정 및 구성 하려면 다음 단계를 완료 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-228">Complete these steps to set up and configure the CDN to host your assets in SharePoint Online using the SharePoint Online Management Shell.</span></span>
  
### <a name="enable-your-organization-to-use-the-office-365-cdn"></a><span data-ttu-id="0cbb3-229">조직이 Office 365 CDN을 사용 하도록 설정</span><span class="sxs-lookup"><span data-stu-id="0cbb3-229">Enable your organization to use the Office 365 CDN</span></span>

<span data-ttu-id="0cbb3-230">테 넌 트 CDN 설정을 변경 하기 전에 Office 365 테 넌 트에서 개인 CDN 구성의 현재 상태를 검색 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-230">Before you make changes to the tenant CDN settings, you should retrieve the current status of the private CDN configuration in your Office 365 tenant.</span></span> <span data-ttu-id="0cbb3-231">SharePoint Online 관리 셸을 사용 하 여 테 넌 트에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-231">Connect to your tenant using the SharePoint Online Management Shell:</span></span>

``` powershell
Connect-SPOService -Url https://contoso-admin.sharepoint.com
```

<span data-ttu-id="0cbb3-232">이제 **SPOTenantCdnEnabled** cmdlet을 사용 하 여 테 넌 트에서 CDN 상태 설정을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-232">Now use the **Get-SPOTenantCdnEnabled** cmdlet to retrieve the CDN status settings from the tenant:</span></span>

``` powershell
Get-SPOTenantCdnEnabled -CdnType <Public | Private>
```

<span data-ttu-id="0cbb3-233">지정한 cdntype에 대 한 CDN의 상태가 화면에 출력 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-233">The status of the CDN for the specified CdnType will output to the screen.</span></span>

<span data-ttu-id="0cbb3-234">**SPOTenantCdnEnabled** cmdlet을 사용 하 여 조직에서 Office 365 CDN을 사용 하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-234">Use the **Set-SPOTenantCdnEnabled** cmdlet to enable your organization to use the Office 365 CDN.</span></span> <span data-ttu-id="0cbb3-235">조직이 공용 원본, 전용 원본 또는 두 가지 모두를 한 번에 사용 하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-235">You can enable your organization to use public origins, private origins, or both at once.</span></span> <span data-ttu-id="0cbb3-236">또한이 기능을 사용 하도록 설정 하면 기본 원본 설정을 건너뛰도록 CDN을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-236">You can also configure the CDN to skip the setup of default origins when you enable it.</span></span> <span data-ttu-id="0cbb3-237">이 항목의 설명에 따라 나중에 이러한 원본을 언제 든 지 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-237">You can always add these origins later as described in this topic.</span></span>
  
<span data-ttu-id="0cbb3-238">SharePoint Online 용 Windows Powershell:</span><span class="sxs-lookup"><span data-stu-id="0cbb3-238">In Windows Powershell for SharePoint Online:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType <Public | Private | Both> -Enable $true
```

<span data-ttu-id="0cbb3-239">예를 들어 조직에서 공용 및 개인 원본을 둘 다 사용할 수 있도록 설정 하려면 다음 명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-239">For example, to enable your organization to use both public and private origins, type the following command:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true
```

<span data-ttu-id="0cbb3-240">조직이 공용 및 개인 원본을 모두 사용할 수 있도록 설정 하 고 기본 원본을 설정 하지 않으려면 다음 명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-240">To enable your organization to use both public and private origins but skip setting up the default origins, type the following command:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true -NoDefaultOrigins
```

<span data-ttu-id="0cbb3-241">Office 365 CDN을 사용 하도록 설정 하는 경우 기본적으로 프로 비전 되는 원본에 대 한 정보 및 기본 원본 설정을 건너뛰는 경우 발생할 수 있는 영향에 대 한 자세한 내용은 [default CDN 원본임](use-office-365-cdn-with-spo.md#default-cdn-origins) 을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-241">See [Default CDN origins](use-office-365-cdn-with-spo.md#default-cdn-origins) for information about the origins that are provisioned by default when you enable the Office 365 CDN, and the potential impact of skipping the setup of default origins.</span></span>

<span data-ttu-id="0cbb3-242">조직에서 공용 원본을 사용 하도록 설정 하려면 다음 명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-242">To enable your organization to use public origins, type the following command:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType Public -Enable $true
```

<span data-ttu-id="0cbb3-243">조직에서 전용 원본을 사용 하도록 설정 하려면 다음 명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-243">To enable your organization to use private origins, type the following command:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType Private -Enable $true
```

<span data-ttu-id="0cbb3-244">이 cmdlet에 대 한 자세한 내용은 [SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-244">For more information about this cmdlet, see [Set-SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx).</span></span>
  
### <a name="change-the-list-of-file-types-to-include-in-the-office-365-cdn-optional"></a><span data-ttu-id="0cbb3-245">Office 365 CDN에 포함할 파일 형식 목록 변경 (선택 사항)</span><span class="sxs-lookup"><span data-stu-id="0cbb3-245">Change the list of file types to include in the Office 365 CDN (Optional)</span></span>
<a name="Office365CDNforSPOFileType"> </a>

> [!TIP]
> <span data-ttu-id="0cbb3-246">**SPOTenantCdnPolicy** cmdlet을 사용 하 여 파일 형식을 정의 하는 경우 현재 정의 된 목록을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-246">When you define file types by using the **Set-SPOTenantCdnPolicy** cmdlet, you overwrite the currently defined list.</span></span> <span data-ttu-id="0cbb3-247">목록에 다른 파일 형식을 추가 하려면 먼저 cmdlet을 사용 하 여 이미 허용 된 파일 형식을 확인 하 여 새 파일과 함께 목록에 포함 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-247">If you want to add additional file types to the list, use the cmdlet first to find out what file types are already allowed and include them in the list along with your new ones.</span></span>
  
<span data-ttu-id="0cbb3-248">**SPOTenantCdnPolicy** cmdlet을 사용 하 여 CDN에서 공용 및 전용 원본으로 호스팅할 수 있는 정적 파일 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-248">Use the **Set-SPOTenantCdnPolicy** cmdlet to define static file types that can be hosted by public and private origins in the CDN.</span></span> <span data-ttu-id="0cbb3-249">기본적으로 일반 에셋 유형 (예: .css, .gif, .jpg, .js)을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-249">By default, common asset types are allowed, for example .css, .gif, .jpg, and .js.</span></span>

<span data-ttu-id="0cbb3-250">SharePoint Online 용 Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="0cbb3-250">In Windows PowerShell for SharePoint Online:</span></span>

``` powershell
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType IncludeFileExtensions -PolicyValue "<Comma-separated list of file types >"
```

<span data-ttu-id="0cbb3-251">예를 들어 CDN에서 .css 및 .png 파일을 호스팅할 수 있도록 설정 하려면 다음 명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-251">For example, to enable the CDN to host .css and .png files, you would enter the command:</span></span>

``` powershell
Set-SPOTenantCdnPolicy -CdnType Private -PolicyType IncludeFileExtensions -PolicyValue "CSS,PNG"
```

<span data-ttu-id="0cbb3-252">CDN에서 현재 허용 되는 파일 형식을 확인 하려면 **SPOTenantCdnPolicies** cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-252">To see what file types are currently allowed by the CDN, use the **Get-SPOTenantCdnPolicies** cmdlet:</span></span>

``` powershell
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

<span data-ttu-id="0cbb3-253">이러한 cmdlet에 대 한 자세한 내용은 [SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) 및 [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-253">For more information about these cmdlets, see [Set-SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) and [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx).</span></span>
  
### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn-optional"></a><span data-ttu-id="0cbb3-254">Office 365 CDN에서 제외 하려는 사이트 분류 목록 변경 (선택 사항)</span><span class="sxs-lookup"><span data-stu-id="0cbb3-254">Change the list of site classifications you want to exclude from the Office 365 CDN (Optional)</span></span>
<a name="Office365CDNforSPOSiteClassification"> </a>

> [!TIP]
> <span data-ttu-id="0cbb3-255">**SPOTenantCdnPolicy** cmdlet을 사용 하 여 사이트 분류를 제외 하는 경우 현재 정의 된 목록을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-255">When you exclude site classifications by using the **Set-SPOTenantCdnPolicy** cmdlet, you overwrite the currently defined list.</span></span> <span data-ttu-id="0cbb3-256">추가 사이트 분류를 제외 하려면 먼저 cmdlet을 사용 하 여 이미 제외 된 분류를 확인 한 다음 새 항목과 함께 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-256">If you want to exclude additional site classifications, use the cmdlet first to find out what classifications are already excluded and then add them along with your new ones.</span></span>

<span data-ttu-id="0cbb3-257">**SPOTenantCdnPolicy** cmdlet을 사용 하 여 CDN을 통해 사용 하지 않도록 설정할 사이트 분류를 제외 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-257">Use the **Set-SPOTenantCdnPolicy** cmdlet to exclude site classifications that you do not want to make available over the CDN.</span></span> <span data-ttu-id="0cbb3-258">기본적으로 사이트 분류는 제외 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-258">By default, no site classifications are excluded.</span></span>

<span data-ttu-id="0cbb3-259">SharePoint Online 용 Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="0cbb3-259">In Windows PowerShell for SharePoint Online:</span></span>

``` powershell
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType ExcludeRestrictedSiteClassifications  -PolicyValue "<Comma-separated list of site classifications >"
```

<span data-ttu-id="0cbb3-260">현재 제한 된 사이트 분류를 확인 하려면 **SPOTenantCdnPolicies** cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-260">To see what site classifications are currently restricted, use the **Get-SPOTenantCdnPolicies** cmdlet:</span></span>

``` powershell
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

<span data-ttu-id="0cbb3-261">반환 되는 속성은 _IncludeFileExtensions_, _ExcludeRestrictedSiteClassifications_ 및 _excludeifnoscriptdisabled_입니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-261">The properties that will be returned are _IncludeFileExtensions_, _ExcludeRestrictedSiteClassifications_ and _ExcludeIfNoScriptDisabled_.</span></span>

<span data-ttu-id="0cbb3-262">_IncludeFileExtensions_ 속성에는 CDN에서 처리할 파일 확장명 목록이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-262">The _IncludeFileExtensions_ property contains the list of file extensions that will be served from the CDN.</span></span>

> [!NOTE]
> <span data-ttu-id="0cbb3-263">기본 파일 확장명은 public 및 private과 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-263">The default file extensions are different between public and private.</span></span>

<span data-ttu-id="0cbb3-264">_ExcludeRestrictedSiteClassifications_ 속성은 CDN에서 제외 하려는 사이트 분류를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-264">The _ExcludeRestrictedSiteClassifications_ property contains the site classifications that you want to exclude from the CDN.</span></span> <span data-ttu-id="0cbb3-265">예를 들어 해당 분류가 적용 된 사이트의 콘텐츠가 CDN에서 처리 되지 않도록 **비밀 우편** 으로 표시 된 사이트를 제외할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-265">For example, you can exclude sites marked as **Confidential** so content from sites with that classification applied will not be served from the CDN.</span></span>

<span data-ttu-id="0cbb3-266">_excludeifnoscriptdisabled_ 속성은 사이트 수준 _noscript_ 특성 설정에 따라 CDN에서 콘텐츠를 제외 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-266">The _ExcludeIfNoScriptDisabled_ property excludes content from the CDN based on the site-level _NoScript_ attribute settings.</span></span> <span data-ttu-id="0cbb3-267">기본적으로 _최신_ 사이트에는 _noscript_ 특성이 **사용** 으로 설정 되 고 _클래식_ 사이트에는 사용 **되지** 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-267">By default, the _NoScript_ attribute is set to **Enabled** for _Modern_ sites and **Disabled** for _Classic_ sites.</span></span> <span data-ttu-id="0cbb3-268">이것은 테 넌 트 설정에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-268">This depends on your tenant settings.</span></span>

<span data-ttu-id="0cbb3-269">이러한 cmdlet에 대 한 자세한 내용은 [SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) 및 [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-269">For more information about these cmdlets, see [Set-SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) and [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx).</span></span>
  
### <a name="add-an-origin-for-your-assets"></a><span data-ttu-id="0cbb3-270">자산에 대 한 근원 추가</span><span class="sxs-lookup"><span data-stu-id="0cbb3-270">Add an origin for your assets</span></span>
<a name="Office365CDNforSPOOrigin"> </a>

<span data-ttu-id="0cbb3-271">**SPOTenantCdnOrigin** cmdlet을 사용 하면 원점을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-271">Use the **Add-SPOTenantCdnOrigin** cmdlet to define an origin.</span></span> <span data-ttu-id="0cbb3-272">여러 원본을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-272">You can define multiple origins.</span></span> <span data-ttu-id="0cbb3-273">원점은 CDN에서 호스팅할 자산이 포함 된 SharePoint 라이브러리 또는 폴더를 가리키는 URL입니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-273">The origin is a URL that points to a SharePoint library or folder that contains the assets that you want to be hosted by the CDN.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="0cbb3-274">사용자 정보가 포함 된 리소스를 배치 하거나 조직에서 공용 원본으로 중요 한 것으로 간주 해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-274">You should never place resources that contain user information or are considered sensitive to your organization in a public origin.</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType <Public | Private> -OriginUrl <path>
```

<span data-ttu-id="0cbb3-275">_path_ 값은 자산이 포함 된 라이브러리 또는 폴더의 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-275">The value of _path_ is the path to the library or folder that contains the assets.</span></span> <span data-ttu-id="0cbb3-276">상대 경로 외에도 와일드 카드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-276">You can use wildcards in addition to relative paths.</span></span> <span data-ttu-id="0cbb3-277">원본 URL 앞에는 와일드 카드를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-277">Origins support wildcards prepended to the URL.</span></span> <span data-ttu-id="0cbb3-278">이를 통해 여러 사이트에 걸쳐 있는 원본을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-278">This allows you to create origins that span multiple sites.</span></span> <span data-ttu-id="0cbb3-279">예를 들어 모든 사이트에 대 한 masterpages 폴더의 모든 자산을 CDN 내의 공용 근원으로 포함 하려면 다음 명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-279">For example, to include all of the assets in the masterpages folder for all of your sites as a public origin within the CDN, type the following command:</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
```

- <span data-ttu-id="0cbb3-280">와일드 카드 수정자 \***/** 는 경로의 시작 부분 에서만 사용할 수 있으며 지정 된 url의 모든 URL 세그먼트와 일치 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-280">The wildcard modifier \***/** can only be used at the beginning of the path, and will match all URL segments under the specified URL.</span></span>
- <span data-ttu-id="0cbb3-281">경로는 문서 라이브러리, 폴더 또는 사이트를 가리킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-281">The path can point to a document library, folder or site.</span></span> <span data-ttu-id="0cbb3-282">예를 들어 경로 _\*/site1_ 은 사이트 아래의 모든 문서 라이브러리와 일치 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-282">For example, the path _\*/site1_ will match all the document libraries under the site.</span></span>

<span data-ttu-id="0cbb3-283">상대 경로 또는 전체 경로를 사용 하 여 특정 경로를 갖는 원점을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-283">You can add an origin with a specific path using either a relative path or a full path.</span></span>

<span data-ttu-id="0cbb3-284">이 예제에서는 상대 경로를 사용 하 여 특정 사이트에 siteassets 라이브러리의 비공개 원본을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-284">This example adds a private origin of the siteassets library on a specific site using a relative path:</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

<span data-ttu-id="0cbb3-285">이 예제에서는 전체 경로를 사용 하 여 사이트 모음의 사이트 자산 라이브러리에 _folder1_ 폴더의 개인 출처를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-285">This example adds a private origin of the _folder1_ folder in the site collection's site assets library using the full path:</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl “https://contoso.sharepoint.com/sites/test/siteassets/folder1”
```

<span data-ttu-id="0cbb3-286">이 명령 및 구문에 대 한 자세한 내용은 [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-286">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span></span>

> [!NOTE]
> <span data-ttu-id="0cbb3-287">비공개 원본의 경우 원본에서 공유 되는 자산은 CDN에서 액세스 하려면 먼저 주 버전을 게시 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-287">In private origins, assets being shared from an origin must have a major version published before they can be accessed from the CDN.</span></span>
  
<span data-ttu-id="0cbb3-288">명령을 실행 하면 시스템에서 데이터 센터 전체에서 구성을 동기화 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-288">Once you've run the command, the system synchronizes the configuration across the datacenter.</span></span> <span data-ttu-id="0cbb3-289">최대 15 분까지 소요 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-289">This can take up to 15 minutes.</span></span>
  
### <a name="example-configure-a-public-origin-for-your-master-pages-and-for-your-style-library-for-sharepoint-online"></a><span data-ttu-id="0cbb3-290">예: 마스터 페이지에 대 한 공용 원점과 SharePoint Online에 대 한 스타일 라이브러리에 대해 구성</span><span class="sxs-lookup"><span data-stu-id="0cbb3-290">Example: Configure a public origin for your master pages and for your style library for SharePoint Online</span></span>
<a name="ExamplePublicOrigin"> </a>

<span data-ttu-id="0cbb3-291">일반적으로 이러한 출처는 Office 365 CDN을 사용 하도록 설정 하면 기본적으로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-291">Normally, these origins are set up for you by default when you enable the Office 365 CDN.</span></span> <span data-ttu-id="0cbb3-292">그러나 수동으로 사용 하도록 설정 하려는 경우 다음 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-292">However, if you want to enable them manually, follow these steps.</span></span>
  
- <span data-ttu-id="0cbb3-293">**SPOTenantCdnOrigin** cmdlet을 사용 하면 스타일 라이브러리를 공용 원점으로 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-293">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the style library as a public origin.</span></span>

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */style%20library
  ```

- <span data-ttu-id="0cbb3-294">**SPOTenantCdnOrigin** cmdlet을 사용 하면 마스터 페이지를 공공 원점으로 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-294">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the master pages as a public origin.</span></span>

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
  ```

<span data-ttu-id="0cbb3-295">이 명령 및 구문에 대 한 자세한 내용은 [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-295">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span></span>

<span data-ttu-id="0cbb3-296">명령을 실행 하면 시스템에서 데이터 센터 전체에서 구성을 동기화 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-296">Once you've run the command, the system synchronizes the configuration across the datacenter.</span></span> <span data-ttu-id="0cbb3-297">최대 15 분까지 소요 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-297">This can take up to 15 minutes.</span></span>

### <a name="example-configure-a-private-origin-for-your-site-assets-site-pages-and-publishing-images-for-sharepoint-online"></a><span data-ttu-id="0cbb3-298">예: SharePoint Online에 대 한 사이트 자산, 사이트 페이지 및 게시 이미지에 대 한 개인 출처 구성</span><span class="sxs-lookup"><span data-stu-id="0cbb3-298">Example: Configure a private origin for your site assets, site pages, and publishing images for SharePoint Online</span></span>
<a name="ExamplePrivateOrigin"> </a>

- <span data-ttu-id="0cbb3-299">**SPOTenantCdnOrigin** cmdlet을 사용 하면 사이트 자산 폴더를 전용 원본으로 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-299">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the site assets folder as a private origin.</span></span>

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */siteassets
  ```

- <span data-ttu-id="0cbb3-300">**SPOTenantCdnOrigin** cmdlet을 사용 하면 사이트 페이지 폴더를 전용 원본으로 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-300">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the site pages folder as a private origin.</span></span>

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */sitepages
  ```

- <span data-ttu-id="0cbb3-301">**SPOTenantCdnOrigin** cmdlet을 사용 하면 게시 이미지 폴더를 전용 원본으로 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-301">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the publishing images folder as a private origin.</span></span>

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */publishingimages
  ```

<span data-ttu-id="0cbb3-302">이 명령 및 구문에 대 한 자세한 내용은 [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-302">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span></span>

<span data-ttu-id="0cbb3-303">명령을 실행 하면 시스템에서 데이터 센터 전체에서 구성을 동기화 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-303">Once you've run the command, the system synchronizes the configuration across the datacenter.</span></span> <span data-ttu-id="0cbb3-304">최대 15 분까지 소요 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-304">This can take up to 15 minutes.</span></span>

### <a name="example-configure-a-private-origin-for-a-site-collection-for-sharepoint-online"></a><span data-ttu-id="0cbb3-305">예: SharePoint Online에 대 한 사이트 모음에 대 한 개인 원본 구성</span><span class="sxs-lookup"><span data-stu-id="0cbb3-305">Example: Configure a private origin for a site collection for SharePoint Online</span></span>
<a name="ExamplePrivateOriginSiteCollection"> </a>

<span data-ttu-id="0cbb3-306">**SPOTenantCdnOrigin** cmdlet을 사용 하면 사이트 모음을 전용 원본으로 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-306">Use the **Add-SPOTenantCdnOrigin** cmdlet to define a site collection as a private origin.</span></span> <span data-ttu-id="0cbb3-307">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-307">For example:</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

<span data-ttu-id="0cbb3-308">이 명령 및 구문에 대 한 자세한 내용은 [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-308">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span></span>
  
<span data-ttu-id="0cbb3-309">명령을 실행 하면 시스템에서 데이터 센터 전체에서 구성을 동기화 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-309">Once you've run the command, the system synchronizes the configuration across the datacenter.</span></span> <span data-ttu-id="0cbb3-310">SharePoint Online 테 넌 트가 CDN 서비스에 연결할 때 예상 되는 _구성 보류 중인_ 메시지가 표시 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-310">You may see a _Configuration pending_ message which is expected as the SharePoint Online tenant connects to the CDN service.</span></span> <span data-ttu-id="0cbb3-311">최대 15 분까지 소요 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-311">This can take up to 15 minutes.</span></span>

### <a name="manage-the-office-365-cdn"></a><span data-ttu-id="0cbb3-312">Office 365 CDN 관리</span><span class="sxs-lookup"><span data-stu-id="0cbb3-312">Manage the Office 365 CDN</span></span>
<a name="CDNManage"> </a>

<span data-ttu-id="0cbb3-313">CDN을 설정한 후에는이 섹션에 설명 된 대로 콘텐츠를 업데이트 하거나 필요에 따라 변경 하 여 구성을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-313">Once you've set up the CDN, you can make changes to your configuration as you update content or as your needs change, as described in this section.</span></span>
  
#### <a name="add-update-or-remove-assets-from-the-office-365-cdn"></a><span data-ttu-id="0cbb3-314">Office 365 CDN에서 자산 추가, 업데이트 또는 제거</span><span class="sxs-lookup"><span data-stu-id="0cbb3-314">Add, update, or remove assets from the Office 365 CDN</span></span>
<a name="Office365CDNforSPOaddremoveasset"> </a>

<span data-ttu-id="0cbb3-315">설정 단계를 완료 한 후에는 새 자산을 추가 하 고 원할 때마다 기존 자산을 업데이트 하거나 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-315">Once you've completed the setup steps, you can add new assets, and update or remove existing assets whenever you want.</span></span> <span data-ttu-id="0cbb3-316">폴더 또는 SharePoint 라이브러리에서 원본으로 식별 한 자산을 변경 하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-316">Just make your changes to the assets in the folder or SharePoint library that you identified as an origin.</span></span> <span data-ttu-id="0cbb3-317">새 자산을 추가 하는 경우에는 CDN을 통해 즉시 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-317">If you add a new asset, it is available through the CDN immediately.</span></span> <span data-ttu-id="0cbb3-318">그러나 자산을 업데이트 하는 경우 새 복사본을 전파 하 고 CDN에서 사용할 수 있게 되는 데 최대 15 분이 걸립니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-318">However, if you update the asset, it will take up to 15 minutes for the new copy to propagate and become available in the CDN.</span></span>
  
<span data-ttu-id="0cbb3-319">원본 위치를 검색 해야 하는 경우 **SPOTenantCdnOrigins** cmdlet을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-319">If you need to retrieve the location of the origin, you can use the **Get-SPOTenantCdnOrigins** cmdlet.</span></span> <span data-ttu-id="0cbb3-320">이 cmdlet을 사용 하는 방법에 대 한 자세한 내용은 [SPOTenantCdnOrigins](https://technet.microsoft.com/en-us/library/mt790770.aspx)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-320">For information on how to use this cmdlet, see [Get-SPOTenantCdnOrigins](https://technet.microsoft.com/en-us/library/mt790770.aspx).</span></span>
  
#### <a name="remove-an-origin-from-the-office-365-cdn"></a><span data-ttu-id="0cbb3-321">Office 365 CDN에서 원본 제거</span><span class="sxs-lookup"><span data-stu-id="0cbb3-321">Remove an origin from the Office 365 CDN</span></span>
<a name="Office365CDNforSPORemoveOrigin"> </a>

<span data-ttu-id="0cbb3-322">원본으로 식별 한 폴더 또는 SharePoint 라이브러리에 대 한 액세스 권한을 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-322">You can remove access to a folder or SharePoint library that you identified as an origin.</span></span> <span data-ttu-id="0cbb3-323">이 작업을 수행 하려면 **SPOTenantCdnOrigin** cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-323">To do this, use the **Remove-SPOTenantCdnOrigin** cmdlet.</span></span>

``` powershell
Remove-SPOTenantCdnOrigin -OriginUrl <path> -CdnType <Public | Private | Both>
```

<span data-ttu-id="0cbb3-324">이 cmdlet을 사용 하는 방법에 대 한 자세한 내용은 [SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790761.aspx)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-324">For information on how to use this cmdlet, see [Remove-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790761.aspx).</span></span>
  
#### <a name="modify-an-origin-in-the-office-365-cdn"></a><span data-ttu-id="0cbb3-325">Office 365 CDN에서 원본 수정</span><span class="sxs-lookup"><span data-stu-id="0cbb3-325">Modify an origin in the Office 365 CDN</span></span>
<a name="Office365CDNforSPORemoveOrigin"> </a>

<span data-ttu-id="0cbb3-326">만든 출처는 수정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-326">You cannot modify an origin you've created.</span></span> <span data-ttu-id="0cbb3-327">대신 원점을 제거한 다음 새 원본을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-327">Instead, remove the origin and then add a new one.</span></span> <span data-ttu-id="0cbb3-328">자세한 내용은 [Office 365 CDN에서 출처를 제거](use-office-365-cdn-with-spo.md#Office365CDNforSPORemoveOrigin) 하 고 [자산의 출처를 추가](use-office-365-cdn-with-spo.md#Office365CDNforSPOOrigin)하는 방법을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-328">For more information, see [To remove an origin from the Office 365 CDN](use-office-365-cdn-with-spo.md#Office365CDNforSPORemoveOrigin) and [To add an origin for your assets](use-office-365-cdn-with-spo.md#Office365CDNforSPOOrigin).</span></span>
  
#### <a name="disable-the-office-365-cdn"></a><span data-ttu-id="0cbb3-329">Office 365 CDN 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="0cbb3-329">Disable the Office 365 CDN</span></span>
<a name="Office365CDNforSPODisable"> </a>

<span data-ttu-id="0cbb3-330">**SPOTenantCdnEnabled** cmdlet을 사용 하 여 조직에 CDN을 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-330">Use the **Set-SPOTenantCdnEnabled** cmdlet to disable the CDN for your organization.</span></span> <span data-ttu-id="0cbb3-331">CDN에 대 한 공용 및 전용 원본을 모두 사용 하는 경우에는 다음 예제와 같이 cmdlet을 두 번 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-331">If you have both the public and private origins enabled for the CDN, you need to run the cmdlet twice as shown in the following examples.</span></span>
  
<span data-ttu-id="0cbb3-332">CDN에서 public 원본임을 사용 하지 않도록 설정 하려면 다음 명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-332">To disable use of public origins in the CDN, enter the following command:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType Public -Enable $false
```

<span data-ttu-id="0cbb3-333">CDN에서 비공개 원본을 사용 하지 않도록 설정 하려면 다음 명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-333">To disable use of the private origins in the CDN, enter the following command:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType Private -Enable $false
```

<span data-ttu-id="0cbb3-334">이 cmdlet에 대 한 자세한 내용은 [SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-334">For more information about this cmdlet, see [Set-SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx).</span></span>

## <a name="set-up-and-configure-the-office-365-cdn-using-the-office-365-cli"></a><span data-ttu-id="0cbb3-335">office 365 CLI를 사용 하 여 office 365 CDN을 설정 하 고 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-335">Set up and configure the Office 365 CDN using the Office 365 CLI</span></span>
<a name="CDNSetupinCLI"> </a>

<span data-ttu-id="0cbb3-336">이 섹션의 절차에서는 [Office 365 CLI](https://aka.ms/o365cli)를 설치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-336">The procedures in this section require that you have installed the [Office 365 CLI](https://aka.ms/o365cli).</span></span> <span data-ttu-id="0cbb3-337">다음으로, [spo connect](https://pnp.github.io/office365-cli/cmd/spo/connect/) 명령을 사용 하 여 SharePoint Online 테 넌 트에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-337">Next, connect to your SharePoint Online tenant using the [spo connect](https://pnp.github.io/office365-cli/cmd/spo/connect/) command.</span></span>

<span data-ttu-id="0cbb3-338">Office 365 CLI를 사용 하 여 SharePoint Online에서 자산을 호스트 하도록 CDN을 설정 및 구성 하려면 다음 단계를 완료 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-338">Complete these steps to set up and configure the CDN to host your assets in SharePoint Online using the Office 365 CLI.</span></span>

### <a name="enable-the-office-365-cdn"></a><span data-ttu-id="0cbb3-339">Office 365 CDN 사용</span><span class="sxs-lookup"><span data-stu-id="0cbb3-339">Enable the Office 365 CDN</span></span>

<span data-ttu-id="0cbb3-340">[spo CDN set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-set/) 명령을 사용 하 여 테 넌 트에서 Office 365 CDN의 상태를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-340">You can manage the state of the Office 365 CDN in your tenant using the [spo cdn set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-set/) command.</span></span>

<span data-ttu-id="0cbb3-341">테 넌 트에서 실행 되는 Office 365 공용 CDN을 사용 하도록 설정 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-341">To enable the Office 365 Public CDN in your tenant execute:</span></span>

```sh
spo cdn set --type Public --enabled true
```

<span data-ttu-id="0cbb3-342">Office 365 SharePoint CDN을 사용 하도록 설정 하려면 다음을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-342">To enable the Office 365 SharePoint CDN, execute:</span></span>

```sh
spo cdn set --type Private --enabled true
```

#### <a name="view-the-current-status-of-the-office-365-cdn"></a><span data-ttu-id="0cbb3-343">Office 365 CDN의 현재 상태를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-343">View the current status of the Office 365 CDN</span></span>

<span data-ttu-id="0cbb3-344">특정 유형의 Office 365 cdn을 사용 하거나 사용 하지 않도록 설정할지 여부를 확인 하려면 [spo CDN get](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-get/) 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-344">To check if the particular type of Office 365 CDN is enabled or disabled, use the [spo cdn get](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-get/) command.</span></span>

<span data-ttu-id="0cbb3-345">Office 365 공용 CDN이 사용 하도록 설정 되어 있는지 확인 하려면 다음을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-345">To check if the Office 365 Public CDN is enabled, execute:</span></span>

```sh
spo cdn get --type Public
```

### <a name="view-the-office-365-cdn-origins"></a><span data-ttu-id="0cbb3-346">Office 365 CDN 원본 보기</span><span class="sxs-lookup"><span data-stu-id="0cbb3-346">View the Office 365 CDN origins</span></span>

<span data-ttu-id="0cbb3-347">현재 구성 된 Office 365 공용 CDN 원본을 실행 하려면 다음을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-347">To view the currently configured Office 365 Public CDN origins execute:</span></span>

```sh
spo cdn origin list --type Public
```

<span data-ttu-id="0cbb3-348">Office 365 CDN을 사용 하도록 설정 하는 경우 기본적으로 프로 비전 되는 원본에 대 한 자세한 내용은 [default CDN 원본을](use-office-365-cdn-with-spo.md#default-cdn-origins) 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-348">See [Default CDN origins](use-office-365-cdn-with-spo.md#default-cdn-origins) for information about the origins that are provisioned by default when you enable the Office 365 CDN.</span></span>

### <a name="add-an-office-365-cdn-origin"></a><span data-ttu-id="0cbb3-349">Office 365 CDN 원본 추가</span><span class="sxs-lookup"><span data-stu-id="0cbb3-349">Add an Office 365 CDN origin</span></span>

> [!NOTE]
> <span data-ttu-id="0cbb3-350">조직에 중요 한 것으로 간주 되는 리소스를 공공 근원으로 구성 된 SharePoint 문서 라이브러리에 배치 해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-350">You should never place resources that are considered sensitive to your organization in a SharePoint document library configured as a public origin.</span></span>

<span data-ttu-id="0cbb3-351">[spo cdn 원본 add](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-add/) 명령을 사용 하 여 cdn 원본을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-351">Use the [spo cdn origin add](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-add/) command to define a CDN origin.</span></span> <span data-ttu-id="0cbb3-352">여러 원본을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-352">You can define multiple origins.</span></span> <span data-ttu-id="0cbb3-353">원점은 CDN에서 호스팅할 자산이 포함 된 SharePoint 라이브러리 또는 폴더를 가리키는 URL입니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-353">The origin is a URL that points to a SharePoint library or folder that contains the assets that you want to be hosted by the CDN.</span></span>

```sh
spo cdn origin add --type [Public | Private] --origin <path>
```

<span data-ttu-id="0cbb3-354">여기서 `path` 은 자산이 포함 된 폴더의 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-354">Where `path` is the path to the folder that contains the assets.</span></span> <span data-ttu-id="0cbb3-355">상대 경로 외에도 와일드 카드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-355">You can use wildcards in addition to relative paths.</span></span>

<span data-ttu-id="0cbb3-356">모든 사이트의 **마스터 페이지 갤러리** 에 있는 모든 자산을 공용 원점으로 포함 하려면 다음을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-356">To include all assets in the **Master Page Gallery** of all sites as a public origin, execute:</span></span>

```sh
spo cdn origin add --type Public --origin */masterpage
```

<span data-ttu-id="0cbb3-357">특정 사이트 모음에 대 한 개인 원점을 구성 하려면 다음을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-357">To configure a private origin for a specific site collection, execute:</span></span>

```sh
spo cdn origin add --type Private --origin sites/site1/siteassets
```

> [!NOTE]
> <span data-ttu-id="0cbb3-358">cdn 원본을 추가한 후에는 cdn 서비스를 통해 파일을 검색 하는 데 최대 15 분까지 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-358">After adding a CDN origin, it might take up to 15 minutes for you to be able to retrieve files via the CDN service.</span></span> <span data-ttu-id="0cbb3-359">[spo cdn 원본 목록](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-list/) 명령을 사용 하 여 특정 원본이 이미 사용 하도록 설정 되었는지 여부를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-359">You can verify if the particular origin has already been enabled using the [spo cdn origin list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-list/) command.</span></span>

### <a name="remove-an-office-365-cdn-origin"></a><span data-ttu-id="0cbb3-360">Office 365 CDN 원본 제거</span><span class="sxs-lookup"><span data-stu-id="0cbb3-360">Remove an Office 365 CDN origin</span></span>

<span data-ttu-id="0cbb3-361">[spo cdn 원본 제거](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-remove/) 명령을 사용 하 여 지정 된 cdn 유형에 대해 cdn 원본을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-361">Use the [spo cdn origin remove](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-remove/) command to remove a CDN origin for the specified CDN type.</span></span>

<span data-ttu-id="0cbb3-362">CDN 구성에서 공용 원점을 제거 하려면 다음을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-362">To remove a public origin from the CDN configuration, execute:</span></span>

```sh
spo cdn origin remove --type Public --origin */masterpage
```

> [!NOTE]
> <span data-ttu-id="0cbb3-363">CDN 원본을 제거 해도 해당 원본과 일치 하는 문서 라이브러리에 저장 된 파일에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-363">Removing a CDN origin doesn't affect the files stored in any document library matching that origin.</span></span> <span data-ttu-id="0cbb3-364">이러한 자산이 sharepoint URL을 사용 하 여 참조 된 경우 sharepoint는 문서 라이브러리를 가리키는 원래 URL로 자동 전환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-364">If these assets have been referenced using their SharePoint URL, SharePoint will automatically switch back to the original URL pointing to the document library.</span></span> <span data-ttu-id="0cbb3-365">그러나 공용 CDN URL을 사용 하 여 자산이 참조 된 경우에는 원본을 제거 하면 링크가 끊어지고 수동으로 변경 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-365">If, however, assets have been referenced using a public CDN URL, then removing the origin will break the link and you will need to manually change them.</span></span>

### <a name="modify-an-office-365-cdn-origin"></a><span data-ttu-id="0cbb3-366">Office 365 CDN 원본 수정</span><span class="sxs-lookup"><span data-stu-id="0cbb3-366">Modify an Office 365 CDN origin</span></span>

<span data-ttu-id="0cbb3-367">기존 CDN 원본을 수정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-367">It's not possible to modify an existing CDN origin.</span></span> <span data-ttu-id="0cbb3-368">대신 `spo cdn origin remove` 명령을 사용 하 여 이전에 정의 된 CDN 원본을 제거 하 고 `spo cdn origin add` 명령을 사용 하 여 새로 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-368">Instead, you should remove the previously defined CDN origin using the `spo cdn origin remove` command and add a new one using the `spo cdn origin add` command.</span></span>

### <a name="change-the-types-of-files-to-include-in-the-office-365-cdn"></a><span data-ttu-id="0cbb3-369">Office 365 CDN에 포함할 파일 형식 변경</span><span class="sxs-lookup"><span data-stu-id="0cbb3-369">Change the types of files to include in the Office 365 CDN</span></span>

<span data-ttu-id="0cbb3-370">기본적으로 CDN에는 다음 파일 형식이 포함 됩니다. _.css, eot, .gif, .ico, .jpeg, .jpg_,. p s t,. w o v,. ttf,.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-370">By default, the following file types are included in the CDN: _.css, .eot, .gif, .ico, .jpeg, .jpg, .js, .map, .png, .svg, .ttf, and .woff_.</span></span> <span data-ttu-id="0cbb3-371">cdn에 추가 파일 형식을 포함 해야 하는 경우에는 [spo cdn 정책 set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-set/) 명령을 사용 하 여 cdn 구성을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-371">If you need to include additional file types in the CDN, you can change the CDN configuration using the [spo cdn policy set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-set/) command.</span></span>

> [!NOTE]
> <span data-ttu-id="0cbb3-372">파일 형식 목록을 변경할 때 현재 정의 된 목록을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-372">When changing the list of file types, you overwrite the currently defined list.</span></span> <span data-ttu-id="0cbb3-373">추가 파일 형식을 포함 하려면 먼저 [spo cdn 정책 목록](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-list/) 명령을 사용 하 여 현재 구성 되어 있는 파일 형식을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-373">If you want to include additional file types, first use the [spo cdn policy list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-list/) command to find out which file types are currently configured.</span></span>

<span data-ttu-id="0cbb3-374">공용 CDN에 포함 된 파일 형식의 기본 목록에 _JSON_ 파일 형식을 추가 하려면 다음을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-374">To add the _JSON_ file type to the default list of file types included in the public CDN, execute:</span></span>

```sh
spo cdn policy set --type Public --policy IncludeFileExtensions --value "CSS,EOT,GIF,ICO,JPEG,JPG,JS,MAP,PNG,SVG,TTF,WOFF,JSON"
```

### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn"></a><span data-ttu-id="0cbb3-375">Office 365 CDN에서 제외 하려는 사이트 분류 목록 변경</span><span class="sxs-lookup"><span data-stu-id="0cbb3-375">Change the list of site classifications you want to exclude from the Office 365 CDN</span></span>

<span data-ttu-id="0cbb3-376">[spo cdn 정책 설정](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-set/) 명령을 사용 하 여 cdn을 통해 사용 하지 않으려는 사이트 분류를 제외 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-376">Use the [spo cdn policy set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-set/) command to exclude site classifications that you do not want to make available over the CDN.</span></span> <span data-ttu-id="0cbb3-377">기본적으로 사이트 분류는 제외 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-377">By default, no site classifications are excluded.</span></span>

> [!NOTE]
> <span data-ttu-id="0cbb3-378">제외 된 사이트 분류 목록을 변경할 때 현재 정의 된 목록을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-378">When changing the list of excluded site classifications, you overwrite the currently defined list.</span></span> <span data-ttu-id="0cbb3-379">추가 분류를 제외 하려면 먼저 [spo cdn 정책 목록](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-list/) 명령을 사용 하 여 현재 구성 된 분류를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-379">If you want to exclude additional classifications, first use the [spo cdn policy list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-list/) command to find out which classifications are currently configured.</span></span>

<span data-ttu-id="0cbb3-380">_HBI_ 으로 분류 된 사이트를 공용 CDN에서 제외 하려면 다음을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-380">To exclude sites classified as _HBI_ from the public CDN, execute</span></span>

```sh
spo cdn policy set --type Public --policy ExcludeRestrictedSiteClassifications --value "HBI"
```

### <a name="disable-the-office-365-cdn"></a><span data-ttu-id="0cbb3-381">Office 365 CDN 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="0cbb3-381">Disable the Office 365 CDN</span></span>

<span data-ttu-id="0cbb3-382">Office 365 CDN을 사용 하지 않도록 설정 `spo cdn set` 하려면 다음과 같이 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-382">To disable the Office 365 CDN use the `spo cdn set` command, for example:</span></span>

```sh
spo cdn set --type Public --enabled false
```

## <a name="using-your-cdn-assets"></a><span data-ttu-id="0cbb3-383">CDN 자산 사용</span><span class="sxs-lookup"><span data-stu-id="0cbb3-383">Using your CDN assets</span></span>

<span data-ttu-id="0cbb3-384">cdn 및 구성 된 원본 및 정책을 사용 하도록 설정 했으므로 이제 cdn 자산 사용을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-384">Now that you have enabled the CDN and configured origins and policies, you can begin using your CDN assets.</span></span>

<span data-ttu-id="0cbb3-385">이 섹션에서는 sharepoint에서 공용 및 사설 원본 모두에 대 한 요청을 cdn으로 리디렉션하는 sharepoint 페이지 및 콘텐츠에서 CDN url을 사용 하는 방법을 이해 하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-385">This section will help you understand how to use CDN URLs in your SharePoint pages and content so that SharePoint redirects requests for assets in both public and private origins to the CDN.</span></span>

- [<span data-ttu-id="0cbb3-386">CDN 자산에 대 한 링크 업데이트</span><span class="sxs-lookup"><span data-stu-id="0cbb3-386">Updating links to CDN assets</span></span>](use-office-365-cdn-with-spo.md#updating-links-to-cdn-assets)
- [<span data-ttu-id="0cbb3-387">공개 원본에서 에셋 사용</span><span class="sxs-lookup"><span data-stu-id="0cbb3-387">Using assets in public origins</span></span>](use-office-365-cdn-with-spo.md#using-assets-in-public-origins)
- [<span data-ttu-id="0cbb3-388">비공개 원본에서 에셋 사용</span><span class="sxs-lookup"><span data-stu-id="0cbb3-388">Using assets in private origins</span></span>](use-office-365-cdn-with-spo.md#using-assets-in-private-origins)

<span data-ttu-id="0cbb3-389">클라이언트 쪽 웹 파트 호스팅을 위해 CDN을 사용 하는 방법에 대 한 자세한 내용은 [Office 365 CDN (Hello World part 4)에서 클라이언트 쪽 웹 파트 호스트](https://docs.microsoft.com/en-us/sharepoint/dev/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn)항목을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-389">For information on how to use the CDN for hosting client-side web parts, see the topic [Host your client-side web part from Office 365 CDN (Hello World part 4)](https://docs.microsoft.com/en-us/sharepoint/dev/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn).</span></span>

### <a name="updating-links-to-cdn-assets"></a><span data-ttu-id="0cbb3-390">CDN 자산에 대 한 링크 업데이트</span><span class="sxs-lookup"><span data-stu-id="0cbb3-390">Updating links to CDN assets</span></span>

<span data-ttu-id="0cbb3-391">원본에 추가한 자산을 사용 하려면 원본의 파일 경로를 사용 하 여 원본 파일에 대 한 링크를 업데이트 하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-391">To use assets that you have added to an origin, you simply update links to the original file with the path to the file in the origin.</span></span>

- <span data-ttu-id="0cbb3-392">출처에 추가한 자산에 대 한 링크를 포함 하는 페이지 또는 콘텐츠를 편집 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-392">Edit the page or content that contains links to assets you have added to an origin.</span></span> <span data-ttu-id="0cbb3-393">또한 여러 방법 중 하나를 사용 하 여 지정 된 자산에 대 한 링크를 전역으로 검색 하 고 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-393">You can also use one of several methods to globally search and replace links across an enter site or site collection if you want to update the link to a given asset everywhere it appears.</span></span>
- <span data-ttu-id="0cbb3-394">원본의 자산에 대 한 각 링크에 대해 경로를 CDN 원본에 있는 파일의 경로로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-394">For each link to an asset in an origin, replace the path with the path to the file in the CDN origin.</span></span> <span data-ttu-id="0cbb3-395">상대 경로를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-395">You can use relative paths.</span></span>
- <span data-ttu-id="0cbb3-396">페이지 또는 콘텐츠를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-396">Save the page or content.</span></span>

<span data-ttu-id="0cbb3-397">예를 들어 문서 라이브러리 폴더 _/site/CDN_origins/public/_ 로 복사한 이미지 _/site/SiteAssets/images/image.png_을 고려해 보십시오.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-397">For example, consider the image _/site/SiteAssets/images/image.png_, which you have copied to the document library folder _/site/CDN_origins/public/_.</span></span> <span data-ttu-id="0cbb3-398">CDN 자산을 사용 하려면 이미지 파일 위치의 원래 경로를 원본 경로와 함께 바꿔 새 URL _/site/CDN_origins/public/image.png_합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-398">To use the CDN asset, replace the original path to the image file location with the path to the origin to make the new URL _/site/CDN_origins/public/image.png_.</span></span>

<span data-ttu-id="0cbb3-399">상대 경로 대신 자산에 대 한 전체 URL을 사용 하려면 다음과 같이 링크를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-399">If you want to use the full URL to the asset instead of a relative path, construct the link like so:</span></span>

`https://<TenantHostName>.sharepoint.com/sites/site/CDN_origins/public/image.png`

> [!NOTE]
> <span data-ttu-id="0cbb3-400">일반적으로 CDN의 자산에 url을 직접 하드 코딩 해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-400">In general, you should not hardcode URLs directly to assets in the CDN.</span></span> <span data-ttu-id="0cbb3-401">그러나 필요한 경우 공개 원본에서 자산에 대 한 url을 수동으로 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-401">However, you can manually construct URLs for assets in public origins if needed.</span></span> <span data-ttu-id="0cbb3-402">자세한 내용은 [공용 자산의 하드 코딩 CDN url](use-office-365-cdn-with-spo.md#hardcoding-cdn-urls-for-public-assets)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-402">For more information, see [Hardcoding CDN URLs for public assets](use-office-365-cdn-with-spo.md#hardcoding-cdn-urls-for-public-assets).</span></span>

<span data-ttu-id="0cbb3-403">cdn에서 자산이 제공 되 고 있는지 확인 하는 방법에 대 한 자세한 내용은 how the [Office 365 CDN](use-office-365-cdn-with-spo.md#CDNTroubleshooting) 섹션의 ["cdn에서 자산이 제공 되 고 있는지 확인 하는 방법은 무엇입니까?"](use-office-365-cdn-with-spo.md#CDNConfirm) 를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-403">To learn about how to verify that assets are being served from the CDN, see [How do I confirm that assets are being served by the CDN?](use-office-365-cdn-with-spo.md#CDNConfirm) in the [Troubleshooting the Office 365 CDN](use-office-365-cdn-with-spo.md#CDNTroubleshooting) section.</span></span>

### <a name="using-assets-in-public-origins"></a><span data-ttu-id="0cbb3-404">공개 원본에서 에셋 사용</span><span class="sxs-lookup"><span data-stu-id="0cbb3-404">Using assets in public origins</span></span>

<span data-ttu-id="0cbb3-405">sharepoint Online의 **게시 기능은** sharepoint 대신 cdn 서비스에서 자산이 제공 되도록 공용 원본에 저장 된 자산의 url을 해당 cdn에 맞게 자동으로 다시 씁니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-405">The **Publishing feature** in SharePoint Online automatically rewrites URLs of assets stored in public origins to their CDN equivalents so that assets are served from the CDN service instead of SharePoint.</span></span>

<span data-ttu-id="0cbb3-406">원본이 게시 기능이 사용 하도록 설정 된 사이트에 있고 cdn에 대해 오프 로드 하려는 자산이 다음 범주 중 하나에 포함 되어 있는 경우 SharePoint에서는 자산이 cdn에서 제외 된 경우에는 원본의 자산에 대 한 url을 자동으로 다시 씁니다.  정책.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-406">If your origin is in a site with the Publishing feature enabled, and the assets you want to offload to the CDN are in one of the following categories, SharePoint will automatically rewrite URLs for assets in the origin, provided that the asset has not been excluded by a CDN policy.</span></span>

<span data-ttu-id="0cbb3-407">다음은 SharePoint 게시 기능에 의해 자동으로 다시 작성 되는 링크에 대 한 간략 한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-407">The following is an overview of which links are automatically rewritten by the SharePoint Publishing feature:</span></span>

- <span data-ttu-id="0cbb3-408">클래식 게시 페이지의 HTML 응답에 있는 IMG/LINK/CSS url</span><span class="sxs-lookup"><span data-stu-id="0cbb3-408">IMG/LINK/CSS URLs in classic publishing page HTML responses</span></span>
  - <span data-ttu-id="0cbb3-409">여기에는 페이지의 HTML 콘텐츠 내에서 제작자가 추가한 이미지가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-409">This includes images added by authors within the HTML content of a page</span></span>
- <span data-ttu-id="0cbb3-410">그림 라이브러리 슬라이드 쇼 웹 파트 이미지 url</span><span class="sxs-lookup"><span data-stu-id="0cbb3-410">Picture Library SlideShow webpart image URLs</span></span>
- <span data-ttu-id="0cbb3-411">renderlistdataasstream (SPList REST API)의 이미지 필드 결과</span><span class="sxs-lookup"><span data-stu-id="0cbb3-411">Image fields in SPList REST API (RenderListDataAsStream) results</span></span>
  - <span data-ttu-id="0cbb3-412">새 속성 _imagefieldstotryrewritetocdnurls_ 을 사용 하 여 쉼표로 구분 된 필드 목록을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-412">Use the new property _ImageFieldsToTryRewriteToCdnUrls_ to provide a comma separated list of fields</span></span>
  - <span data-ttu-id="0cbb3-413">하이퍼링크 필드 및 PublishingImage 필드 지원</span><span class="sxs-lookup"><span data-stu-id="0cbb3-413">Supports hyperlink fields and PublishingImage fields</span></span>
- <span data-ttu-id="0cbb3-414">SharePoint 이미지 변환</span><span class="sxs-lookup"><span data-stu-id="0cbb3-414">SharePoint image renditions</span></span>

<span data-ttu-id="0cbb3-415">다음 다이어그램에서는 SharePoint가 공용 원본의 자산을 포함 하는 페이지에 대 한 요청을 수신 하는 경우의 워크플로를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-415">The following diagram illustrates the workflow when SharePoint receives a request for a page containing assets from a public origin.</span></span>

<span data-ttu-id="0cbb3-416">![워크플로 다이어그램: 공용 원본의 Office 365 CDN 자산 검색] (media/O365-CDN/o365-cdn-public-steps-transparent.svg "워크플로: 공용 원본에서 Office 365 CDN 자산을 검색 하는 경우")</span><span class="sxs-lookup"><span data-stu-id="0cbb3-416">![Workflow diagram: Retrieving Office 365 CDN assets from a public origin](media/O365-CDN/o365-cdn-public-steps-transparent.svg "Workflow: Retrieving Office 365 CDN assets from a public origin")</span></span>

> [!TIP]
> <span data-ttu-id="0cbb3-417">페이지의 특정 url에 대해 자동 다시 쓰기를 사용 하지 않도록 설정 하려는 경우 페이지를 체크 아웃 하 고 사용 하지 않도록 설정할 각 링크의 끝에 쿼리 문자열 매개 변수 **?NoAutoReWrites = true** 를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-417">If you want to disable auto-rewriting for specific URLs on a page, you can check out the page and add the query string parameter **?NoAutoReWrites=true** to the end of each link you want to disable.</span></span>

#### <a name="hardcoding-cdn-urls-for-public-assets"></a><span data-ttu-id="0cbb3-418">공용 자산의 CDN url을 하드 코딩 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-418">Hardcoding CDN URLs for public assets</span></span>

<span data-ttu-id="0cbb3-419">공개 원점에 대해 _게시_ 기능을 사용할 수 없거나 자산이 cdn 서비스의 자동 재작성 기능에서 지 원하는 링크 형식 중 하나가 아닌 경우에는 자산의 cdn 위치에 대 한 url을 수동으로 구성 하 고 콘텐츠에 이러한 url을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-419">If the _Publishing_ feature is not enabled for a public origin, or the asset is not one of the link types supported by the auto-rewrite feature of the CDN service, you can manually construct URLs to the CDN location of the assets and use these URLs in your content.</span></span>

> [!NOTE]
> <span data-ttu-id="0cbb3-420">URL의 마지막 섹션을 구성 하는 데 필요한 액세스 토큰이 리소스를 요청할 때 생성 되므로 비공개 원본의 자산에 CDN url을 하드 제거할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-420">You cannot hardcode CDN URLs to assets in a private origin because the required access token that forms the last section of the URL is generated at the time the resource is requested.</span></span>

<span data-ttu-id="0cbb3-421">공용 CDN 자산의 경우 URL 형식이 다음과 같이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-421">For public CDN assets, the URL format will look like the following:</span></span>

``` html
https://publiccdn.sharepointonline.com/<TenantHostName>/sites/site/library/asset.png
```

<span data-ttu-id="0cbb3-422">**TenantHostName** 을 테 넌 트 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-422">Replace **TenantHostName** with your tenant name.</span></span> <span data-ttu-id="0cbb3-423">예제:</span><span class="sxs-lookup"><span data-stu-id="0cbb3-423">Example:</span></span>

``` html
https://publiccdn.sharepointonline.com/contoso.sharepoint.com/sites/site/library/asset.png
```

### <a name="using-assets-in-private-origins"></a><span data-ttu-id="0cbb3-424">비공개 원본에서 에셋 사용</span><span class="sxs-lookup"><span data-stu-id="0cbb3-424">Using assets in private origins</span></span>

<span data-ttu-id="0cbb3-425">비공개 원본에서 자산을 사용 하는 데에는 추가 구성이 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-425">No additional configuration is required to use assets in private origins.</span></span> <span data-ttu-id="0cbb3-426">SharePoint Online은 개인 원본에 있는 자산의 url을 자동으로 다시 씁니다. 이러한 자산에 대 한 요청은 항상 CDN에서 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-426">SharePoint Online automatically rewrites URLs for assets in private origins so requests for those assets will always be served from the CDN.</span></span> <span data-ttu-id="0cbb3-427">자산을 요청 하는 경우에는 SharePoint Online에서 자동으로 생성 해야 하는 토큰이 포함 되기 때문에 이러한 url에는 개인 원본에서 CDN 자산에 대 한 url을 수동으로 빌드할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-427">You cannot manually build URLs to CDN assets in private origins because these URLs contain tokens that must be auto-generated by SharePoint Online at the time the asset is requested.</span></span>

<span data-ttu-id="0cbb3-428">비공개 원본의 자산에 대 한 액세스는 원본에 대 한 사용자 권한 및 다음 섹션에서 설명 하는 주의 사항에 따라 동적으로 생성 된 토큰으로 보호 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-428">Access to assets in private origins is protected by dynamically generated tokens based on user permissions to the origin, with the caveats described in the following sections.</span></span> <span data-ttu-id="0cbb3-429">사용자에 게는 cdn에서 콘텐츠를 렌더링 하기 위한 **읽기** 이상의 원본 액세스 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-429">Users must have at least **read** access to the origins for the CDN to render content.</span></span>

<span data-ttu-id="0cbb3-430">다음 다이어그램에서는 SharePoint가 비공개 원본의 자산을 포함 하는 페이지에 대 한 요청을 수신 하는 경우의 워크플로를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-430">The following diagram illustrates the workflow when SharePoint receives a request for a page containing assets from a private origin.</span></span>

<span data-ttu-id="0cbb3-431">![워크플로 다이어그램: 비공개 원본의 Office 365 CDN 자산 검색] (media/O365-CDN/o365-cdn-private-steps-transparent.svg "워크플로: 비공개 원본의 Office 365 CDN 자산 검색")</span><span class="sxs-lookup"><span data-stu-id="0cbb3-431">![Workflow diagram: Retrieving Office 365 CDN assets from a private origin](media/O365-CDN/o365-cdn-private-steps-transparent.svg "Workflow: Retrieving Office 365 CDN assets from a private origin")</span></span>

#### <a name="token-based-authorization-in-private-origins"></a><span data-ttu-id="0cbb3-432">전용 원본에서의 토큰 기반 권한 부여</span><span class="sxs-lookup"><span data-stu-id="0cbb3-432">Token-based authorization in private origins</span></span>

<span data-ttu-id="0cbb3-433">Office 365 CDN의 비공개 원본에 있는 자산에 대 한 액세스는 SharePoint Online에서 생성 된 토큰에 의해 부여 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-433">Access to assets in private origins in the Office 365 CDN is granted by tokens generated by SharePoint Online.</span></span> <span data-ttu-id="0cbb3-434">원본에서 지정한 폴더나 라이브러리에 대 한 액세스 권한이 이미 있는 사용자에 게는 사용자가 자신의 사용 권한 수준에 따라 파일에 액세스할 수 있도록 허용 하는 토큰이 자동으로 부여 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-434">Users who already have permission to access to the folder or library designated by the origin are automatically granted tokens that permit the user to access the file based on their permission level.</span></span> <span data-ttu-id="0cbb3-435">이러한 액세스 토큰은 토큰 재생 공격을 방지 하기 위해 생성 된 30 ~ 90 분에 유효 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-435">These access tokens are valid for 30 to 90 minutes after they are generated to help prevent token replay attacks.</span></span>

<span data-ttu-id="0cbb3-436">액세스 토큰이 생성 되 면 SharePoint Online에서 클라이언트에 대 한 사용자 지정 URI 두 개 (edge 인증 __ 토큰)와 _oat_ (원본 인증 토큰)을 함께 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-436">Once the access token is generated, SharePoint Online returns a custom URI to the client containing two authorization parameters _eat_ (edge authorization token) and _oat_ (origin authorization token).</span></span> <span data-ttu-id="0cbb3-437">각 토큰의 구조는 _<'expiration time format'>__<'secure signature'>에서 시간이 오래 걸리는 시간_입니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-437">The structure of each token is _<'expiration time in Epoch time format'>__<'secure signature'>_.</span></span> <span data-ttu-id="0cbb3-438">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-438">For example:</span></span>

``` html
https://privatecdn.sharepointonline.com/contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg?eat=1486154359_cc59042c5c55c90b26a2775323c7c8112718431228fe84d568a3795a63912840&oat=1486154359_7d73c2e3ba4b7b1f97242332900616db0d4ffb04312
```

> [!NOTE]
> <span data-ttu-id="0cbb3-439">토큰을 소유 하는 모든 사용자가 CDN의 리소스에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-439">Anyone in possession of the token can access the resource in the CDN.</span></span> <span data-ttu-id="0cbb3-440">그러나 이러한 액세스 토큰을 포함 하는 url은 HTTPS를 통해서만 공유 되므로 토큰이 만료 되기 전에 최종 사용자가 url을 명시적으로 공유 하지 않으면 권한이 없는 사용자가 해당 자산에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-440">However, URLs containing these access tokens are only shared over HTTPS, so unless the URL is explicitly shared by an end user before the token expires, the asset won’t be accessible to unauthorized users.</span></span>

#### <a name="item-level-permissions-are-not-supported-for-assets-in-private-origins"></a><span data-ttu-id="0cbb3-441">비공개 원본에 있는 자산에 대해서는 항목 수준 권한이 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-441">Item-level permissions are not supported for assets in private origins</span></span>

<span data-ttu-id="0cbb3-442">SharePoint Online은 전용 원본에 있는 자산에 대 한 항목 수준 권한을 지원 하지 않는다는 점에 유의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-442">It is important to note that SharePoint Online does not support item-level permissions for assets in private origins.</span></span> <span data-ttu-id="0cbb3-443">예를 들어에 `https://contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg`있는 파일의 경우 사용자는 다음 조건에 해당 하는 파일에 대 한 유효한 액세스 권한을 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-443">For example, for a file located at `https://contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg`, users have effective access to the file given the following conditions:</span></span>

|<span data-ttu-id="0cbb3-444">사용자</span><span class="sxs-lookup"><span data-stu-id="0cbb3-444">User</span></span>  |<span data-ttu-id="0cbb3-445">사용 권한</span><span class="sxs-lookup"><span data-stu-id="0cbb3-445">Permissions</span></span>  |<span data-ttu-id="0cbb3-446">유효한 액세스</span><span class="sxs-lookup"><span data-stu-id="0cbb3-446">Effective access</span></span>  |
|---------|---------|---------|
|<span data-ttu-id="0cbb3-447">사용자 1</span><span class="sxs-lookup"><span data-stu-id="0cbb3-447">User 1</span></span>     |<span data-ttu-id="0cbb3-448">folder1에 대 한 액세스 권한</span><span class="sxs-lookup"><span data-stu-id="0cbb3-448">Has access to folder1</span></span>         |<span data-ttu-id="0cbb3-449">CDN에서 image1에 액세스할 수 있음</span><span class="sxs-lookup"><span data-stu-id="0cbb3-449">Can access image1.jpg from the CDN</span></span>         |
|<span data-ttu-id="0cbb3-450">사용자 2</span><span class="sxs-lookup"><span data-stu-id="0cbb3-450">User 2</span></span>     |<span data-ttu-id="0cbb3-451">folder1에 대 한 액세스 권한이 없음</span><span class="sxs-lookup"><span data-stu-id="0cbb3-451">Does not have access to folder1</span></span>         |<span data-ttu-id="0cbb3-452">CDN에서 image1에 액세스할 수 없음</span><span class="sxs-lookup"><span data-stu-id="0cbb3-452">Cannot access image1.jpg from the CDN</span></span>         |
|<span data-ttu-id="0cbb3-453">사용자 3</span><span class="sxs-lookup"><span data-stu-id="0cbb3-453">User 3</span></span>     |<span data-ttu-id="0cbb3-454">folder1에 대 한 액세스 권한이 없지만 SharePoint Online에서 image1에 액세스할 수 있는 권한이 명시적으로 부여 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-454">Does not have access to folder1, but is granted explicit permission to access image1.jpg in SharePoint Online</span></span>         |<span data-ttu-id="0cbb3-455">SharePoint Online에서 직접 자산 image1에 액세스할 수 있으 나 CDN에서 액세스 가능</span><span class="sxs-lookup"><span data-stu-id="0cbb3-455">Can access the asset image1.jpg directly from SharePoint Online, but not from the CDN</span></span>         |
|<span data-ttu-id="0cbb3-456">사용자 4</span><span class="sxs-lookup"><span data-stu-id="0cbb3-456">User 4</span></span>     |<span data-ttu-id="0cbb3-457">folder1에 대 한 액세스 권한이 있지만 SharePoint Online에서 image1에 대 한 액세스 권한이 명시적으로 거부 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-457">Has access to folder1, but has been explicitly denied access to image1.jpg in SharePoint Online</span></span>         |<span data-ttu-id="0cbb3-458">sharepoint online에서 자산에 액세스할 수는 없지만 sharepoint online에서 파일에 대 한 액세스가 거부 되더라도 CDN에서 자산에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-458">Cannot access the asset from SharePoint Online, but can access the asset from the CDN despite being denied access to the file in SharePoint Online</span></span>         |

## <a name="troubleshooting-the-office-365-cdn"></a><span data-ttu-id="0cbb3-459">Office 365 CDN 문제 해결</span><span class="sxs-lookup"><span data-stu-id="0cbb3-459">Troubleshooting the Office 365 CDN</span></span>
<a name="CDNTroubleshooting"> </a>

### <a name="how-do-i-confirm-that-assets-are-being-served-by-the-cdn"></a><span data-ttu-id="0cbb3-460">CDN에서 자산을 제공 하는지 확인 하려면 어떻게 해야 합니까?</span><span class="sxs-lookup"><span data-stu-id="0cbb3-460">How do I confirm that assets are being served by the CDN?</span></span>
<a name="CDNConfirm"> </a>

<span data-ttu-id="0cbb3-461">페이지에 CDN 자산의 링크를 추가한 후에는 해당 페이지로 이동 하 고 이미지를 렌더링 하 고 이미지 URL을 검토 한 후에 해당 페이지를 마우스 오른쪽 단추로 클릭 하 여 해당 자산이 cdn에서 처리 되 고 있는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-461">Once you have added links to CDN assets to a page, you can confirm that the asset is being served from the CDN by browsing to the page, right clicking on the image once it has rendered and reviewing the image URL.</span></span>

<span data-ttu-id="0cbb3-462">또한 브라우저의 개발자 도구를 사용 하 여 페이지에서 각 자산의 URL을 보거나 타사 네트워크 추적 도구를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-462">You can also use your browser's developer tools to view the URL for each asset on a page, or use a 3rd party network trace tool.</span></span>

> [!NOTE]
> <span data-ttu-id="0cbb3-463">Fiddler와 같은 네트워크 도구를 사용 하 여 sharepoint 페이지에서 자산을 렌더링 하지 않는 사용자의 자산을 테스트 하는 경우 URL이 sharepoint Online 테 넌 트의 `https://yourdomain.sharepoint.com`루트 URL 인 GET 요청에 참조 페이지 헤더 "참조 페이지"를 수동으로 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-463">If you use a network tool such as Fiddler to test your assets outside of rendering the asset from a SharePoint page, you must manually add the referrer header “Referrer: `https://yourdomain.sharepoint.com`” to the GET request where the URL is the root URL of your SharePoint Online tenant.</span></span>

<span data-ttu-id="0cbb3-464">SharePoint Online에서 제공 되는 참조이 있어야 하므로 CDN url을 웹 브라우저에서 직접 테스트할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-464">You cannot test CDN URLs directly in a web browser because you must have a referrer coming from SharePoint Online.</span></span> <span data-ttu-id="0cbb3-465">그러나 SharePoint 페이지에 cdn 자산 URL을 추가한 다음 브라우저에서 페이지를 열면 cdn 자산이 페이지에 렌더링 된 것을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-465">However, if you add the CDN asset URL to a SharePoint page and then open the page in a browser, you will see the CDN asset rendered on the page.</span></span>

<span data-ttu-id="0cbb3-466">microsoft edge 브라우저에서 개발자 도구를 사용 하는 방법에 대 한 자세한 내용은 [microsoft edge 개발자 도구](https://docs.microsoft.com/en-us/microsoft-edge/devtools-guide)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-466">For more information on using the developer tools in the Microsoft Edge browser, see [Microsoft Edge Developer Tools](https://docs.microsoft.com/en-us/microsoft-edge/devtools-guide).</span></span>

### <a name="why-are-assets-from-a-new-origin-unavailable"></a><span data-ttu-id="0cbb3-467">새 원본의 자산을 사용할 수 없는 이유는 무엇 인가요?</span><span class="sxs-lookup"><span data-stu-id="0cbb3-467">Why are assets from a new origin unavailable?</span></span>
<span data-ttu-id="0cbb3-468">새 원본의 자산은 cdn을 통해 등록이 전파 되 고 자산이 원본에서 cdn 저장소로 업로드 되는 시간을 차지 하므로 즉시 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-468">Assets in new origins will not immediately be available for use, as it takes time for the registration to propagate through the CDN and for the assets to be uploaded from the origin to CDN storage.</span></span> <span data-ttu-id="0cbb3-469">CDN에서 자산을 사용할 수 있어야 하는 시간은 자산의 수와 파일 크기에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-469">The time required for assets to be available in the CDN depends on how many assets and the files sizes.</span></span>

### <a name="my-client-side-web-part-or-sharepoint-framework-solution-isnt-working"></a><span data-ttu-id="0cbb3-470">클라이언트 쪽 웹 파트 또는 SharePoint Framework 솔루션이 작동 하지 않는 경우</span><span class="sxs-lookup"><span data-stu-id="0cbb3-470">My client-side web part or SharePoint Framework solution isn't working</span></span>

<span data-ttu-id="0cbb3-471">공용 원본에 대해 Office 365 CDN을 사용 하도록 설정 하면 CDN 서비스가 다음과 같은 기본 원본을 자동으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-471">When you enable the Office 365 CDN for public origins, the CDN service automatically creates these default origins:</span></span>

- <span data-ttu-id="0cbb3-472">\*/masterpage</span><span class="sxs-lookup"><span data-stu-id="0cbb3-472">\*/MASTERPAGE</span></span>
- <span data-ttu-id="0cbb3-473">\*/VSTYLE 라이브러리</span><span class="sxs-lookup"><span data-stu-id="0cbb3-473">\*/STYLE LIBRARY</span></span>
- <span data-ttu-id="0cbb3-474">\*/clientsideassets</span><span class="sxs-lookup"><span data-stu-id="0cbb3-474">\*/CLIENTSIDEASSETS</span></span>

<span data-ttu-id="0cbb3-475">\*/clientsideassets 원본이 누락 되 면 SharePoint Framework 솔루션은 실패 하 고 경고 또는 오류 메시지는 생성 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-475">If the \*/clientsideassets origin is missing, SharePoint Framework solutions will fail, and no warning or error messages are generated.</span></span> <span data-ttu-id="0cbb3-476">**$true**으로 설정 된 CDN 또는 원본이 수동으로 삭제 되었기 때문에이 __ 원본이 누락 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-476">This origin may be missing either because the CDN was enabled with the _-NoDefaultOrigins_ parameter set to **$true**, or because the origin was manually deleted.</span></span>

<span data-ttu-id="0cbb3-477">다음 PowerShell 명령을 사용 하 여 \*/clientsideassets 원본이 있는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-477">You can check to see if the \*/CLIENTSIDEASSETS origin is present with the following PowerShell command:</span></span>

``` powershell
Get-SPOTenantCdnOrigin -CdnType Public -OriginUrl */CLIENTSIDEASSETS
```

<span data-ttu-id="0cbb3-478">또는 Office 365 CLI를 통해 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-478">Or you can check with the Office 365 CLI:</span></span>

``` powershell
spo cdn origin list
```

<span data-ttu-id="0cbb3-479">PowerShell에서 원점을 추가 하려면:</span><span class="sxs-lookup"><span data-stu-id="0cbb3-479">To add the origin in PowerShell:</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */CLIENTSIDEASSETS
```

<span data-ttu-id="0cbb3-480">Office 365 CLI에서 원점을 추가 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-480">To add the origin in the Office 365 CLI:</span></span>

``` powershell
spo cdn origin add --origin */CLIENTSIDEASSETS
```

### <a name="what-powershell-modules-and-cli-shells-do-i-need-to-work-with-the-office-365-cdn"></a><span data-ttu-id="0cbb3-481">Office 365 CDN과 함께 작동 하는 데 필요한 PowerShell 모듈 및 CLI 셸에는 무엇 인가요?</span><span class="sxs-lookup"><span data-stu-id="0cbb3-481">What PowerShell modules and CLI shells do I need to work with the Office 365 CDN?</span></span>

<span data-ttu-id="0cbb3-482">**SharePoint Online 관리 셸** PowerShell 모듈 또는 **office 365 CLI**를 사용 하 여 office 365 CDN 작업을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cbb3-482">You can choose to work with the Office 365 CDN using either the **SharePoint Online Management Shell** PowerShell module or the **Office 365 CLI**.</span></span>

- [<span data-ttu-id="0cbb3-483">SharePoint Online 관리 셸 시작</span><span class="sxs-lookup"><span data-stu-id="0cbb3-483">Getting started with SharePoint Online Management Shell</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)
- [<span data-ttu-id="0cbb3-484">Office 365 CLI 설치</span><span class="sxs-lookup"><span data-stu-id="0cbb3-484">Installing the Office 365 CLI</span></span>](https://pnp.github.io/office365-cli/user-guide/installing-cli/)

## <a name="see-also"></a><span data-ttu-id="0cbb3-485">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0cbb3-485">See also</span></span>

[<span data-ttu-id="0cbb3-486">콘텐츠 배달 네트워크</span><span class="sxs-lookup"><span data-stu-id="0cbb3-486">Content Delivery Networks</span></span>](https://aka.ms/o365cdns)

[<span data-ttu-id="0cbb3-487">Office 365의 네트워크 계획 및 성능 조정</span><span class="sxs-lookup"><span data-stu-id="0cbb3-487">Network planning and performance tuning for Office 365</span></span>](https://aka.ms/tune)

