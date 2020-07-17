---
title: Office 365 CDN (콘텐츠 배달 네트워크) 빠른 시작
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 06/04/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
description: Office 365 CDN (콘텐츠 배달 네트워크) 빠른 시작
ms.openlocfilehash: 4abaaa5545bc807c4da297c66fd9ad1fb188adc7
ms.sourcegitcommit: 576c3dbdef535f952a861197dea5348908da9504
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/09/2020
ms.locfileid: "44561928"
---
# <a name="office-365-content-delivery-network-cdn-quickstart"></a><span data-ttu-id="c1688-103">Office 365 CDN (콘텐츠 배달 네트워크) 빠른 시작</span><span class="sxs-lookup"><span data-stu-id="c1688-103">Office 365 Content Delivery Network (CDN) Quickstart</span></span>

<span data-ttu-id="c1688-104">기본 제공 **Office 365 CDN (콘텐츠 배달 네트워크** )을 사용 하 여 정적 자산 (이미지, JavaScript, 스타일 시트, woff 파일)을 호스트 하 여 SharePoint Online 페이지의 성능을 향상 시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1688-104">You can use the built-in **Office 365 Content Delivery Network (CDN)** to host static assets (images, JavaScript, Stylesheets, WOFF files) to provide better performance for your SharePoint Online pages.</span></span> <span data-ttu-id="c1688-105">Office 365 CDN은 정적 자산을 요청하는 브라우저에 더 가깝게 캐싱하여 성능을 향상시켜 다운로드 속도를 높이고 대기 시간을 줄이는 데 기여합니다.</span><span class="sxs-lookup"><span data-stu-id="c1688-105">The Office 365 CDN improves performance by caching static assets closer to the browsers requesting them, which helps to speed up downloads and reduce latency.</span></span> <span data-ttu-id="c1688-106">또한 Office 365 CDN은 향상 된 압축 및 HTTP 파이프라이닝을 위해 HTTP/2 프로토콜을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1688-106">Also, the Office 365 CDN uses the HTTP/2 protocol for improved compression and HTTP pipelining.</span></span> <span data-ttu-id="c1688-107">Office 365 CDN 서비스는 SharePoint Online 구독의 일부로 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1688-107">The Office 365 CDN service is included as part of your SharePoint Online subscription.</span></span>

<span data-ttu-id="c1688-108">자세한 내용은 [Use The Office 365 CDN (Content Delivery Network) With SharePoint Online을](use-office-365-cdn-with-spo.md)참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c1688-108">For more detailed information guidance see [Use the Office 365 Content Delivery Network (CDN) with SharePoint Online](use-office-365-cdn-with-spo.md).</span></span>

>[!NOTE]
><span data-ttu-id="c1688-109">Office 365 CDN은 프로덕션 (전 세계) 클라우드의 테 넌 트에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1688-109">The Office 365 CDN is only available to tenants in the production (worldwide) cloud.</span></span> <span data-ttu-id="c1688-110">미국 정부의 테 넌 트, 중국 및 독일 클라우드가 현재 Office 365 CDN을 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c1688-110">Tenants in the US Government, China and Germany clouds do not currently support the Office 365 CDN.</span></span>

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-identify-items-not-in-cdn"></a><span data-ttu-id="c1688-111">SharePoint 도구를 사용 하 여 CDN에 없는 항목을 식별 하는 페이지 진단</span><span class="sxs-lookup"><span data-stu-id="c1688-111">Use the Page Diagnostics for SharePoint tool to identify items not in CDN</span></span>

<span data-ttu-id="c1688-112">SharePoint 도구 브라우저 확장 **의 페이지 진단을** 사용 하 여 CDN 원본에 추가할 수 있는 sharepoint Online 페이지의 자산을 쉽게 나열할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1688-112">You can use the **Page Diagnostics for SharePoint tool** browser extension to easily list assets in your SharePoint Online pages that can be added to a CDN origin.</span></span>

<span data-ttu-id="c1688-113">**Sharepoint 용 페이지 진단 도구** 는 새 Microsoft Edge ( https://www.microsoft.com/edge) 및 sharepoint Online 최신 포털 및 클래식 게시 사이트 페이지 모두를 분석 하는 크롬 브라우저)에 대 한 브라우저 확장입니다.</span><span class="sxs-lookup"><span data-stu-id="c1688-113">The **Page Diagnostics for SharePoint tool** is a browser extension for the new Microsoft Edge (https://www.microsoft.com/edge) and Chrome browsers that analyzes both SharePoint Online modern portal and classic publishing site pages.</span></span> <span data-ttu-id="c1688-114">이 도구는 정의된 성능 기준의 집합 대비 페이지 수행 방식을 보여주는 분석된 각 페이지에 대한 보고서를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c1688-114">The tool provides a report for each analyzed page showing how the page performs against a defined set of performance criteria.</span></span> <span data-ttu-id="c1688-115">Sharepoint용 페이지 진단 도구에 대해 배우고 설치하려면[Sharepoint Online에 페이지 진단 도구 사용](https://aka.ms/perftool)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c1688-115">To install and learn about the Page Diagnostics for SharePoint tool, visit [Use the Page Diagnostics tool for SharePoint Online](https://aka.ms/perftool).</span></span>

<span data-ttu-id="c1688-116">SharePoint Online 페이지에서 SharePoint 용 페이지 진단 도구를 실행 하는 경우 **진단 테스트** 탭을 클릭 하 여 CDN에서 호스팅하지 않는 자산의 목록을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1688-116">When you run the Page Diagnostics for SharePoint tool on a SharePoint Online page, you can click the **Diagnostic Tests** tab to see a list of assets not being hosted by the CDN.</span></span> <span data-ttu-id="c1688-117">이러한 자산은 아래 스크린샷에 표시 된 대로 제목 **CDN (콘텐츠 배달 네트워크) 검사** 아래에 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1688-117">These assets will be listed under the heading **Content Delivery Network (CDN) check** as shown in the screenshot below.</span></span>

![페이지 진단](media/page-diagnostics-for-spo/pagediag-results-general.PNG)

>[!NOTE]
><span data-ttu-id="c1688-119">페이지 진단 도구는 SharePoint Online에서만 사용할 수 있으며 SharePoint 시스템 페이지에서는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c1688-119">The Page Diagnostics tool only works for SharePoint Online, and cannot be used on a SharePoint system page.</span></span>

## <a name="cdn-overview"></a><span data-ttu-id="c1688-120">CDN 개요</span><span class="sxs-lookup"><span data-stu-id="c1688-120">CDN Overview</span></span>

<span data-ttu-id="c1688-121">Office 365 CDN은 고속 글로벌 네트워크를 통해 이미지 및 javascript 파일 같은 자주 액세스 하는 개체를 배포 하 여 페이지 로드 시간을 줄이고 호스트 된 개체에 대 한 액세스 권한을 사용자에 게 제공 하 여 사용자의 성능을 최적화 하도록 디자인 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c1688-121">The Office 365 CDN is designed to optimize performance for users by distributing frequently accessed objects like images and javascript files over a high-speed global network, reducing page load time and providing access to hosted objects as close as possible to the user.</span></span> <span data-ttu-id="c1688-122">CDN은 _근원_이라는 위치에서 자산을 페치합니다.</span><span class="sxs-lookup"><span data-stu-id="c1688-122">The CDN fetches your assets from a location called an _origin_.</span></span> <span data-ttu-id="c1688-123">원본은 URL에서 액세스할 수 있는 SharePoint 사이트, 문서 라이브러리 또는 폴더가 될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1688-123">An origin can be a SharePoint site, document library or folder that is accessible by a URL.</span></span>

<span data-ttu-id="c1688-124">Office 365 CDN은 다음과 같은 두 가지 기본 형식으로 구분 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1688-124">The Office 365 CDN is separated into two basic types:</span></span>

- <span data-ttu-id="c1688-125">**공용 CDN** 은 JS (JavaScript), CSS (스타일 시트), 웹 글꼴 파일 (woff, WOFF2) 및 회사 로고와 같은 비 소유 이미지에 사용 하도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c1688-125">**Public CDN** is designed to be used for JS (JavaScript), CSS (StyleSheets), Web Font File (WOFF, WOFF2) and non-proprietary images like company logos.</span></span>
- <span data-ttu-id="c1688-126">**PRIVATE CDN** 은 이미지 (PNG, JPG, JPEG 등)에 사용 하도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c1688-126">**Private CDN** is designed to be used for images (PNG, JPG, JPEG, etc.).</span></span>

<span data-ttu-id="c1688-127">조직의 공용 또는 개인 원본을 둘 다 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1688-127">You can choose to have both public or private origins for your organization.</span></span> <span data-ttu-id="c1688-128">대부분의 조직에서는 두 가지를 조합 하 여 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1688-128">Most organizations will choose to implement a combination of the two.</span></span> <span data-ttu-id="c1688-129">공용 및 개인 옵션은 모두 비슷한 성능을 제공 하지만 각각에 고유한 특성 및 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1688-129">Both public and private options provide similar performance gains, but each has unique attributes and advantages.</span></span> <span data-ttu-id="c1688-130">공용 및 개인 CDN 원본에 대 한 자세한 내용은 [각 출처를 public 또는 private로 지정](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c1688-130">For more information about public and private CDN origins, see [Choose whether each origin should be public or private](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate).</span></span>

## <a name="how-to-enable-public-and-private-cdn-with-the-default-configuration"></a><span data-ttu-id="c1688-131">기본 구성으로 공용 및 개인 CDN을 사용 하도록 설정 하는 방법</span><span class="sxs-lookup"><span data-stu-id="c1688-131">How to enable Public and Private CDN with the default configuration</span></span>
<span data-ttu-id="c1688-132">테 넌 트 CDN 설정을 변경 하기 전에 조직의 준수, 보안 및 개인 정보 취급 방침을 충족 하는지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1688-132">Before you make changes to the tenant CDN settings, you should verify that it meets compliance, security and privacy policies of your organization.</span></span>

<span data-ttu-id="c1688-133">보다 자세한 구성 설정에 대 한 자세한 내용을 설명 하거나 CDN을 이미 사용 하도록 설정한 상태에서 추가 위치 (원본)를 추가 하려면 [SharePoint Online 관리 셸을 사용 하 여 Office 365 CDN 설정 및 구성](use-office-365-cdn-with-spo.md#set-up-and-configure-the-office-365-cdn-by-using-the-sharepoint-online-management-shell) 섹션을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c1688-133">For more detailed configuration settings, or if you have already enabled CDN and want to add additional locations (origins), please see the section [Set up and configure the Office 365 CDN by using the SharePoint Online Management Shell](use-office-365-cdn-with-spo.md#set-up-and-configure-the-office-365-cdn-by-using-the-sharepoint-online-management-shell)</span></span>

<span data-ttu-id="c1688-134">SharePoint Online 관리 셸을 사용 하 여 테 넌 트에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1688-134">Connect to your tenant using the SharePoint Online Management Shell:</span></span>

```PowerShell
Connect-SPOService -Url https://<YourTenantName>-admin.sharepoint.com
```

<span data-ttu-id="c1688-135">조직이 기본 구성으로 공용 및 개인 원본을 모두 사용 하도록 설정 하려면 다음 명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1688-135">To enable your organization to use both public and private origins with the default configuration, type the following command:</span></span>

```PowerShell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true
```

<span data-ttu-id="c1688-136">이러한 cmdlet의 출력은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c1688-136">Output of these cmdlets should look like the following:</span></span>

![SPOTenantCdnEnabled의 출력](media/O365-CDN/o365-cdn-enable-output.png)

## <a name="see-also"></a><span data-ttu-id="c1688-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c1688-138">See also</span></span>

[<span data-ttu-id="c1688-139">SharePoint Online 용 페이지 진단 도구 사용</span><span class="sxs-lookup"><span data-stu-id="c1688-139">Use the Page Diagnostics tool for SharePoint Online</span></span>](https://aka.ms/perftool)

[<span data-ttu-id="c1688-140">sharepoint Online을 활용해 Office 365 콘텐츠 배달 네트워크(CDN) 사용하기</span><span class="sxs-lookup"><span data-stu-id="c1688-140">Use the Office 365 Content Delivery Network (CDN) with SharePoint Online</span></span>](use-office-365-cdn-with-spo.md)

[<span data-ttu-id="c1688-141">콘텐츠 배달 네트워크</span><span class="sxs-lookup"><span data-stu-id="c1688-141">Content Delivery Networks</span></span>](https://aka.ms/o365cdns)

[<span data-ttu-id="c1688-142">Office 365의 네트워크 계획 및 성능 조정</span><span class="sxs-lookup"><span data-stu-id="c1688-142">Network planning and performance tuning for Office 365</span></span>](https://aka.ms/tune)

[<span data-ttu-id="c1688-143">SharePoint 성능 시리즈-Office 365 CDN 비디오 시리즈</span><span class="sxs-lookup"><span data-stu-id="c1688-143">SharePoint Performance Series - Office 365 CDN video series</span></span>](https://www.youtube.com/playlist?list=PLR9nK3mnD-OWMfr1BA9mr5oCw2aJXw4WA)
