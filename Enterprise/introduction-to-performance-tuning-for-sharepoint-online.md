---
title: SharePoint Online의 성능 조정 소개
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/22/2018
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 81c4be5f-327e-435d-a568-526d68cffef0
description: 이 문서에서는 SharePoint Online에서 최상의 성능을 위해 페이지를 디자인할 때 고려해 야 할 특정 측면에 대해 설명 합니다.
ms.openlocfilehash: d0dc4d6eac1a8711d1c93b97eccbf5474092d3af
ms.sourcegitcommit: 6b4c3a11ef7000480463d43a7a4bc2ced063efce
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/10/2019
ms.locfileid: "35616681"
---
# <a name="introduction-to-performance-tuning-for-sharepoint-online"></a><span data-ttu-id="15aa8-103">SharePoint Online의 성능 조정 소개</span><span class="sxs-lookup"><span data-stu-id="15aa8-103">Introduction to performance tuning for SharePoint Online</span></span>

<span data-ttu-id="15aa8-104">이 문서에서는 SharePoint Online에서 최상의 성능을 위해 페이지를 디자인할 때 고려해 야 할 특정 측면에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="15aa8-104">This article explains what specific aspects you need to consider when designing pages for best performance in SharePoint Online.</span></span>
     
## <a name="sharepoint-online-metrics"></a><span data-ttu-id="15aa8-105">SharePoint Online 메트릭</span><span class="sxs-lookup"><span data-stu-id="15aa8-105">SharePoint Online metrics</span></span>

<span data-ttu-id="15aa8-106">SharePoint Online에 대 한 다음의 광범위 한 메트릭은 성능에 대 한 실제 데이터를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="15aa8-106">The following broad metrics for SharePoint Online provide real world data about performance:</span></span>
  
- <span data-ttu-id="15aa8-107">페이지 로드 속도</span><span class="sxs-lookup"><span data-stu-id="15aa8-107">How fast pages load</span></span>
    
- <span data-ttu-id="15aa8-108">페이지당 필요한 왕복 횟수</span><span class="sxs-lookup"><span data-stu-id="15aa8-108">How many round trips required per page</span></span>
    
- <span data-ttu-id="15aa8-109">서비스 관련 문제</span><span class="sxs-lookup"><span data-stu-id="15aa8-109">Issues with the service</span></span>
    
- <span data-ttu-id="15aa8-110">성능 저하를 발생 시키는 기타 사항</span><span class="sxs-lookup"><span data-stu-id="15aa8-110">Other things that cause performance degradation</span></span>
    
### <a name="conclusions-reached-because-of-the-data"></a><span data-ttu-id="15aa8-111">데이터 때문에 발생 한 결론</span><span class="sxs-lookup"><span data-stu-id="15aa8-111">Conclusions reached because of the data</span></span>

<span data-ttu-id="15aa8-112">데이터는 다음과 같은 정보를 알려 줍니다.</span><span class="sxs-lookup"><span data-stu-id="15aa8-112">The data tells us:</span></span>
  
- <span data-ttu-id="15aa8-113">대부분의 페이지는 SharePoint Online에서 제대로 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="15aa8-113">Most of the pages perform well on SharePoint Online.</span></span>
    
- <span data-ttu-id="15aa8-114">사용자 지정 되지 않은 페이지가 매우 빠르게 로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="15aa8-114">Non-customized pages load very quickly.</span></span>
    
- <span data-ttu-id="15aa8-115">비즈니스용 OneDrive, 팀 사이트 및 시스템 페이지 (예: _layouts 등)가 모두 빠르게 로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="15aa8-115">OneDrive for Business, team sites and system pages, such as _layouts, etc., are all quick to load.</span></span>
    
- <span data-ttu-id="15aa8-116">SharePoint Online 페이지 중 가장 느린 1%가 부하를 로드 하는 데 5000 밀리초 보다 오래 걸립니다.</span><span class="sxs-lookup"><span data-stu-id="15aa8-116">The slowest 1% of SharePoint Online pages take more than 5,000 milliseconds to load.</span></span>
    
<span data-ttu-id="15aa8-117">간단한 벤치 마크 테스트를 사용할 수 있는 한 가지 방법은 사용자 지정 기능을 사용 하 여 개별 포털의 로드 시간을 비즈니스용 OneDrive 홈 페이지의 로드 시간과 비교 하 여 성능을 측정 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="15aa8-117">One simple benchmark test you can use would be to measure performance by comparing the load time of your own portal against the load time of the OneDrive for Business home page as it uses few customized features.</span></span> <span data-ttu-id="15aa8-118">이는 일반적으로 네트워크 성능 문제를 해결 하는 경우 완료를 요구 하는 첫 번째 단계 지원입니다.</span><span class="sxs-lookup"><span data-stu-id="15aa8-118">This will often be the first step Support will ask you to complete when troubleshooting network performance issues.</span></span>
  
## <a name="use-a-standard-user-account-when-checking-performance"></a><span data-ttu-id="15aa8-119">성능을 확인할 때 표준 사용자 계정 사용</span><span class="sxs-lookup"><span data-stu-id="15aa8-119">Use a standard user account when checking performance</span></span>

<span data-ttu-id="15aa8-120">사이트 모음 관리자, 사이트 소유자, 편집자 또는 기여자는 추가 보안 그룹에 속하며 추가 사용 권한을 가지 므로 SharePoint에서 페이지에 로드 하는 추가 요소를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="15aa8-120">A Site Collection Administrator, Site Owner, Editor, or Contributor belong to additional security groups, have additional permissions, and therefore have additional elements that SharePoint loads on a page.</span></span>
  
<span data-ttu-id="15aa8-121">이는 sharepoint 온-프레미스 및 SharePoint Online에 적용 되지만, 온-프레미스 시나리오에서는 SharePoint Online 에서처럼 차이점이 쉽게 발견 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="15aa8-121">This is applicable to SharePoint on-premises and SharePoint Online but in an on-premises scenario the differences will not be as easily noticed as in SharePoint Online.</span></span>
  
<span data-ttu-id="15aa8-122">사용자에 대해 페이지가 어떻게 실행 되는 방식을 올바르게 평가 하려면 표준 사용자 계정을 사용 하 여 제작 컨트롤 및 보안 그룹과 관련 된 추가 트래픽을 로드 하지 않도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="15aa8-122">In order to correctly evaluate how a page will perform for users, you should use a standard user account to avoid loading the authoring controls and additional traffic related to security groups.</span></span>
  
## <a name="connection-categories-for-performance-tuning"></a><span data-ttu-id="15aa8-123">성능 조정에 대 한 연결 범주</span><span class="sxs-lookup"><span data-stu-id="15aa8-123">Connection categories for performance tuning</span></span>

<span data-ttu-id="15aa8-124">서버와 사용자 간의 연결을 세 가지 주요 구성 요소로 분류할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15aa8-124">You can categorize the connections between the server and the user into three main components.</span></span> <span data-ttu-id="15aa8-125">로드 시간에 대 한 자세한 정보를 보려면 SharePoint Online 페이지를 디자인할 때 고려해 야 합니다.</span><span class="sxs-lookup"><span data-stu-id="15aa8-125">Consider these when designing SharePoint Online pages for insight into load times.</span></span>
  
- <span data-ttu-id="15aa8-126">**서버** Microsoft가 데이터 센터에서 호스팅하는 서버입니다.</span><span class="sxs-lookup"><span data-stu-id="15aa8-126">**Server** The servers that Microsoft hosts in datacenters.</span></span>
    
- <span data-ttu-id="15aa8-127">**네트워크** Microsoft 네트워크, 인터넷 및 데이터 센터와 사용자 간의 온-프레미스 네트워크</span><span class="sxs-lookup"><span data-stu-id="15aa8-127">**Network** The Microsoft network, the Internet, and your on-premises network between the datacenter and your users.</span></span>
    
- <span data-ttu-id="15aa8-128">**Browser** 페이지가 로드 되는 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="15aa8-128">**Browser** Where the page is loaded.</span></span>
    
<span data-ttu-id="15aa8-129">이러한 세 가지 연결에는 일반적으로 느린 페이지의 95%가 발생 하는 다섯 가지 이유가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15aa8-129">Within these three connections there are typically five reasons that cause 95% of slow pages.</span></span> <span data-ttu-id="15aa8-130">이 문서에서는 이러한 각 이유에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="15aa8-130">Each of these reasons is discussed in this article:</span></span>
  
- <span data-ttu-id="15aa8-131">탐색 문제</span><span class="sxs-lookup"><span data-stu-id="15aa8-131">Navigation issues</span></span>
    
- <span data-ttu-id="15aa8-132">콘텐츠 롤업</span><span class="sxs-lookup"><span data-stu-id="15aa8-132">Content roll up</span></span>
    
- <span data-ttu-id="15aa8-133">큰 파일</span><span class="sxs-lookup"><span data-stu-id="15aa8-133">Large files</span></span>
    
- <span data-ttu-id="15aa8-134">서버에 대 한 많은 요청</span><span class="sxs-lookup"><span data-stu-id="15aa8-134">Many requests to the server</span></span>
    
- <span data-ttu-id="15aa8-135">웹 파트 처리</span><span class="sxs-lookup"><span data-stu-id="15aa8-135">Web Part processing</span></span>
    
### <a name="server-connection"></a><span data-ttu-id="15aa8-136">서버 연결</span><span class="sxs-lookup"><span data-stu-id="15aa8-136">Server connection</span></span>

<span data-ttu-id="15aa8-137">SharePoint 온-프레미스의 성능에 영향을 주는 많은 문제가 SharePoint Online에도 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="15aa8-137">Many of the issues that affect performance with SharePoint on-premises also apply to SharePoint Online.</span></span>
  
<span data-ttu-id="15aa8-138">예상 대로 서버에서 온-프레미스 SharePoint를 수행 하는 방법을 보다 강력 하 게 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15aa8-138">As you would expect, you have far more control over how servers perform with on-premises SharePoint.</span></span> <span data-ttu-id="15aa8-139">SharePoint Online을 사용 하는 경우는 약간 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="15aa8-139">With SharePoint Online things are a little different.</span></span> <span data-ttu-id="15aa8-140">서버에서 수행 하는 작업이 많을 수록 페이지를 렌더링 하는 데 시간이 오래 걸립니다.</span><span class="sxs-lookup"><span data-stu-id="15aa8-140">The more work you make a server do, the longer it takes to render a page.</span></span> <span data-ttu-id="15aa8-141">SharePoint를 사용 하는 경우 이러한 측면에서 가장 큰 이유는 여러 웹 파트를 포함 하는 복잡 한 페이지입니다.</span><span class="sxs-lookup"><span data-stu-id="15aa8-141">With SharePoint, the biggest culprit in this respect are complex pages with multiple web parts.</span></span>
  
<span data-ttu-id="15aa8-142">SharePoint Server 온-프레미스</span><span class="sxs-lookup"><span data-stu-id="15aa8-142">SharePoint Server on-premises</span></span>
  
![온-프레미스 서버의 스크린샷](media/a8e9b646-cdff-4131-976a-b5f891da44ac.png)
  
<span data-ttu-id="15aa8-144">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="15aa8-144">SharePoint Online</span></span>
  
![온라인 서버의 스크린샷](media/46b27ded-d8a4-4287-b3e0-2603a764b8f8.png)
  
<span data-ttu-id="15aa8-146">SharePoint Online에서는 특정 페이지 요청이 실제로 여러 서버를 호출 하는 작업을 완료할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15aa8-146">With SharePoint Online, certain page requests may actually end up calling multiple servers.</span></span> <span data-ttu-id="15aa8-147">개별 요청에 대 한 서버 간 요청 매트릭스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15aa8-147">You could end up with a matrix of requests between servers for an individual request.</span></span> <span data-ttu-id="15aa8-148">이러한 상호 작용은 페이지 로드 측면에서 비싼 작업을 수행 하는 데 시간이 오래 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15aa8-148">These interactions are expensive from a page load perspective and will make things slow.</span></span>
  
<span data-ttu-id="15aa8-149">이러한 서버 간 상호 작용의 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="15aa8-149">Examples of these server to server interactions are:</span></span>
  
- <span data-ttu-id="15aa8-150">웹-SQL 서버</span><span class="sxs-lookup"><span data-stu-id="15aa8-150">Web to SQL Servers</span></span>
    
- <span data-ttu-id="15aa8-151">웹-응용 프로그램 서버</span><span class="sxs-lookup"><span data-stu-id="15aa8-151">Web to application servers</span></span>
    
<span data-ttu-id="15aa8-152">서버 상호 작용 속도를 저하 시킬 수 있는 또 다른 방법은 캐시 누락입니다.</span><span class="sxs-lookup"><span data-stu-id="15aa8-152">The other thing that can slow down server interactions is cache misses.</span></span> <span data-ttu-id="15aa8-153">온-프레미스 SharePoint와 달리 이전에 방문 했던 페이지에 대해 동일한 서버를 방문 하는 것은 매우 슬림 한 기회입니다. 이렇게 하면 개체 캐싱이 더 이상 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="15aa8-153">Unlike on-premises SharePoint, there is a very slim chance that you will hit the same server for a page that you have visited previously; this makes object caching obsolete.</span></span>
  
### <a name="network-connection"></a><span data-ttu-id="15aa8-154">네트워크 연결</span><span class="sxs-lookup"><span data-stu-id="15aa8-154">Network connection</span></span>

<span data-ttu-id="15aa8-155">WAN을 사용 하지 않는 온-프레미스 SharePoint를 사용 하는 경우에는 데이터 센터와 최종 사용자 간에 고속 연결을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15aa8-155">With on-premises SharePoint that doesn't make use of a WAN, you may use a high-speed connection between datacenter and end-users.</span></span> <span data-ttu-id="15aa8-156">일반적으로 네트워크 측면에서 작업을 쉽게 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15aa8-156">Generally, things are easy to manage from a network perspective.</span></span>
  
<span data-ttu-id="15aa8-157">SharePoint Online에서는 몇 가지 요인을 더 고려해 야 합니다. 예를 들어:</span><span class="sxs-lookup"><span data-stu-id="15aa8-157">With SharePoint Online, there are a few more factors to consider; for example:</span></span>
  
- <span data-ttu-id="15aa8-158">Microsoft 네트워크</span><span class="sxs-lookup"><span data-stu-id="15aa8-158">The Microsoft network</span></span>
    
- <span data-ttu-id="15aa8-159">인터넷</span><span class="sxs-lookup"><span data-stu-id="15aa8-159">The Internet</span></span>
    
- <span data-ttu-id="15aa8-160">ISP</span><span class="sxs-lookup"><span data-stu-id="15aa8-160">The ISP</span></span>
    
<span data-ttu-id="15aa8-161">사용 중인 SharePoint 버전 (및 네트워크)에 관계 없이 네트워크 사용량이 많은 경우에는 다음과 같은 항목이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="15aa8-161">Regardless of which version of SharePoint (and which network) you are using, things that will typically cause the network to be busy include:</span></span>
  
- <span data-ttu-id="15aa8-162">대형 페이로드</span><span class="sxs-lookup"><span data-stu-id="15aa8-162">Large payload</span></span>
    
- <span data-ttu-id="15aa8-163">많은 파일</span><span class="sxs-lookup"><span data-stu-id="15aa8-163">Many files</span></span>
    
- <span data-ttu-id="15aa8-164">서버에 대 한 큰 실제 거리</span><span class="sxs-lookup"><span data-stu-id="15aa8-164">Large physical distance to the server</span></span>
    
<span data-ttu-id="15aa8-165">SharePoint Online에서 활용할 수 있는 한 가지 기능은 Microsoft CDN (콘텐츠 배달 네트워크)입니다.</span><span class="sxs-lookup"><span data-stu-id="15aa8-165">One feature that you can leverage in SharePoint Online is the Microsoft CDN (Content Delivery Network).</span></span> <span data-ttu-id="15aa8-166">CDN은 기본적으로 여러 데이터 센터에 배포 된 서버의 분산 모음입니다.</span><span class="sxs-lookup"><span data-stu-id="15aa8-166">A CDN is basically a distributed collection of servers deployed across multiple datacenters.</span></span> <span data-ttu-id="15aa8-167">CDN을 사용 하는 경우 클라이언트가 원래 SharePoint 서버와 멀리 떨어진 경우에도 클라이언트에 가까운 서버에서 페이지의 콘텐츠를 호스팅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15aa8-167">With a CDN, content on pages can be hosted on a server close to the client even if the client is far away from the originating SharePoint Server.</span></span> <span data-ttu-id="15aa8-168">Microsoft는 앞으로 사용자 지정할 수 없는 페이지의 로컬 인스턴스 (예: SharePoint Online 관리 홈 페이지)를 저장 하는 데이 더 많은 방법을 사용할 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="15aa8-168">Microsoft will be using this more in the future to store local instances of pages which cannot be customized, for example the SharePoint Online admin home page.</span></span> <span data-ttu-id="15aa8-169">CDNs에 대 한 자세한 내용은 [콘텐츠 배달 네트워크](https://docs.microsoft.com/en-us/office365/enterprise/content-delivery-networks)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="15aa8-169">For more information about CDNs, see [Content delivery networks](https://docs.microsoft.com/en-us/office365/enterprise/content-delivery-networks).</span></span>
  
<span data-ttu-id="15aa8-170">알고 있어야 하지만, ISP의 연결 속도가 더 많은 작업을 수행 하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15aa8-170">Something that you need to be aware of but may not be able to do much about is the connection speed of your ISP.</span></span> <span data-ttu-id="15aa8-171">간단한 속도 테스트 도구를 통해 연결 속도를 파악할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15aa8-171">A simple speed test tool will tell you the connection speed.</span></span>
  
### <a name="browser-connection"></a><span data-ttu-id="15aa8-172">브라우저 연결</span><span class="sxs-lookup"><span data-stu-id="15aa8-172">Browser connection</span></span>

<span data-ttu-id="15aa8-173">성능 측면에서 웹 브라우저에 대해 고려해 야 할 몇 가지 요소가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15aa8-173">There are a few factors to consider with web browsers from a performance perspective.</span></span>
  
<span data-ttu-id="15aa8-174">복잡 한 페이지를 방문 하면 성능에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="15aa8-174">Visiting complex pages will affect performance.</span></span> <span data-ttu-id="15aa8-175">대부분의 브라우저에는 90MB를 초과 하는 작은 캐시만 있지만 평균 웹 페이지는 일반적으로 1.6 MB를 초과 합니다.</span><span class="sxs-lookup"><span data-stu-id="15aa8-175">Most browsers only have a small cache (around 90MB), while the average web page is typically around 1.6MB.</span></span> <span data-ttu-id="15aa8-176">이 작업을 수행 하는 데 시간이 오래 걸리지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="15aa8-176">This doesn't take long to get used up.</span></span>
  
<span data-ttu-id="15aa8-177">대역폭도 문제가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15aa8-177">Bandwidth may also be an issue.</span></span> <span data-ttu-id="15aa8-178">예를 들어 사용자가 다른 세션에서 비디오를 시청 하 고 있으면 SharePoint 페이지의 성능에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="15aa8-178">For example, if a user is watching videos in another session, this will affect the performance of your SharePoint page.</span></span> <span data-ttu-id="15aa8-179">사용자가 미디어를 스트리밍하는 것을 방지할 수는 없지만 사용자가 페이지를 로드 하는 방식을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15aa8-179">While you can't prevent users from streaming media, you can control the way a page will load for users.</span></span>
  
<span data-ttu-id="15aa8-180">다음 문서에서 다양 한 SharePoint Online 페이지 사용자 지정 기술과 최적의 성능을 얻는 데 도움이 되는 기타 모범 사례를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15aa8-180">Check out the following articles for different SharePoint Online page customization techniques and other best practices to help you achieve optimal performance.</span></span>
  
- [<span data-ttu-id="15aa8-181">SharePoint Online에 대 한 탐색 옵션</span><span class="sxs-lookup"><span data-stu-id="15aa8-181">Navigation options for SharePoint Online</span></span>](navigation-options-for-sharepoint-online.md)
    
- [<span data-ttu-id="15aa8-182">SharePoint Online 용 페이지 진단 도구 사용</span><span class="sxs-lookup"><span data-stu-id="15aa8-182">Use the Page Diagnostics tool for SharePoint Online</span></span>](page-diagnostics-for-spo.md)
    
- [<span data-ttu-id="15aa8-183">SharePoint Online에 대한 이미지 최적화</span><span class="sxs-lookup"><span data-stu-id="15aa8-183">Image optimization for SharePoint Online</span></span>](image-optimization-for-sharepoint-online.md)
    
- [<span data-ttu-id="15aa8-184">SharePoint Online에서 이미지 및 JavaScript 로드 지연</span><span class="sxs-lookup"><span data-stu-id="15aa8-184">Delay loading images and JavaScript in SharePoint Online</span></span>](delay-loading-images-and-javascript-in-sharepoint-online.md)
    
- [<span data-ttu-id="15aa8-185">SharePoint Online의 축소 및 묶음</span><span class="sxs-lookup"><span data-stu-id="15aa8-185">Minification and bundling in SharePoint Online</span></span>](minification-and-bundling-in-sharepoint-online.md)
    
- [<span data-ttu-id="15aa8-186">콘텐츠 배달 네트워크 사용</span><span class="sxs-lookup"><span data-stu-id="15aa8-186">Using content delivery networks</span></span>](using-content-delivery-networks-with-sharepoint-online.md)
    
- [<span data-ttu-id="15aa8-187">SharePoint Online에서 성능을 향상 시키기 위해 콘텐츠 쿼리 웹 파트 대신 콘텐츠 검색 웹 파트 사용</span><span class="sxs-lookup"><span data-stu-id="15aa8-187">Using Content Search Web Part instead of Content Query Web Part to improve performance in SharePoint Online</span></span>](using-content-search-web-part-instead-of-content-query-web-part-to-improve-perfo.md)
    
- [<span data-ttu-id="15aa8-188">용량 계획 및 부하 테스트 SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="15aa8-188">Capacity planning and load testing SharePoint Online</span></span>](capacity-planning-and-load-testing-sharepoint-online.md)
    
- [<span data-ttu-id="15aa8-189">SharePoint Online의 성능 문제 진단</span><span class="sxs-lookup"><span data-stu-id="15aa8-189">Diagnosing performance issues with SharePoint Online</span></span>](diagnosing-performance-issues-with-sharepoint-online.md)
    
- [<span data-ttu-id="15aa8-190">SharePoint online에서 개체 캐시 사용</span><span class="sxs-lookup"><span data-stu-id="15aa8-190">Using the object cache with SharePoint Online</span></span>](using-the-object-cache-with-sharepoint-online.md)
    
- [<span data-ttu-id="15aa8-191">방법: SharePoint Online에서 제한 또는 차단 방지</span><span class="sxs-lookup"><span data-stu-id="15aa8-191">How to: Avoid getting throttled or blocked in SharePoint Online</span></span>](https://msdn.microsoft.com/en-us/library/office/dn889829.aspx)
    

