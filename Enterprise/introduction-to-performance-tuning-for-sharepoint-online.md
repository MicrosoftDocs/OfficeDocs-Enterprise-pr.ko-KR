---
title: SharePoint Online의 성능 조정 소개
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/22/2018
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 81c4be5f-327e-435d-a568-526d68cffef0
description: 이 문서에서는 SharePoint Online에서 최상의 성능을 위해 페이지를 디자인할 때 고려 해야할 어떤 특정 측면에 설명 합니다.
ms.openlocfilehash: 96aeec19a6b582d0dc8701cd2e99329ec8ce156b
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541917"
---
# <a name="introduction-to-performance-tuning-for-sharepoint-online"></a><span data-ttu-id="ec5c2-103">SharePoint Online의 성능 조정 소개</span><span class="sxs-lookup"><span data-stu-id="ec5c2-103">Introduction to performance tuning for SharePoint Online</span></span>

<span data-ttu-id="ec5c2-104">이 문서에서는 SharePoint Online에서 최상의 성능을 위해 페이지를 디자인할 때 고려 해야할 어떤 특정 측면에 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec5c2-104">This article explains what specific aspects you need to consider when designing pages for best performance in SharePoint Online.</span></span>
  
## <a name="in-this-article"></a><span data-ttu-id="ec5c2-105">이 문서의 내용</span><span class="sxs-lookup"><span data-stu-id="ec5c2-105">In this article</span></span>

- <span data-ttu-id="ec5c2-106">[SharePoint Online의 메트릭](introduction-to-performance-tuning-for-sharepoint-online.md#spometrics) 및 [데이터 때문에 도달 결론](introduction-to-performance-tuning-for-sharepoint-online.md#data)</span><span class="sxs-lookup"><span data-stu-id="ec5c2-106">[SharePoint Online metrics](introduction-to-performance-tuning-for-sharepoint-online.md#spometrics) and [Conclusions reached because of the data](introduction-to-performance-tuning-for-sharepoint-online.md#data)</span></span>
    
- [<span data-ttu-id="ec5c2-107">성능 확인할 때 표준 사용자 계정을 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="ec5c2-107">Use a standard user account when checking performance</span></span>](introduction-to-performance-tuning-for-sharepoint-online.md#standuser)
    
- <span data-ttu-id="ec5c2-108">[성능 조정에 대 한 연결 종류](introduction-to-performance-tuning-for-sharepoint-online.md#connect): [서버 연결](introduction-to-performance-tuning-for-sharepoint-online.md#server), [네트워크 연결](introduction-to-performance-tuning-for-sharepoint-online.md#network)및 [브라우저 연결](introduction-to-performance-tuning-for-sharepoint-online.md#browser)</span><span class="sxs-lookup"><span data-stu-id="ec5c2-108">[Connection categories for performance tuning](introduction-to-performance-tuning-for-sharepoint-online.md#connect): [Server connection](introduction-to-performance-tuning-for-sharepoint-online.md#server), [Network connection](introduction-to-performance-tuning-for-sharepoint-online.md#network), and [Browser connection](introduction-to-performance-tuning-for-sharepoint-online.md#browser)</span></span>
    
## <a name="sharepoint-online-metrics"></a><span data-ttu-id="ec5c2-109">SharePoint Online 메트릭</span><span class="sxs-lookup"><span data-stu-id="ec5c2-109">SharePoint Online metrics</span></span>
<span data-ttu-id="ec5c2-110"><a name="spometrics"> </a></span><span class="sxs-lookup"><span data-stu-id="ec5c2-110"></span></span>

<span data-ttu-id="ec5c2-111">SharePoint Online에 대한 다음의 광범위한 메트릭은 성능의 실제 데이터를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ec5c2-111">The following broad metrics for SharePoint Online provide real world data about performance:</span></span>
  
- <span data-ttu-id="ec5c2-112">페이지 로드 속도</span><span class="sxs-lookup"><span data-stu-id="ec5c2-112">How fast pages load</span></span>
    
- <span data-ttu-id="ec5c2-113">페이지당 필요한 왕복 횟수</span><span class="sxs-lookup"><span data-stu-id="ec5c2-113">How many round trips required per page</span></span>
    
- <span data-ttu-id="ec5c2-114">서비스 관련 문제</span><span class="sxs-lookup"><span data-stu-id="ec5c2-114">Issues with the service</span></span>
    
- <span data-ttu-id="ec5c2-115">성능 저하를 유발하는 기타 사항</span><span class="sxs-lookup"><span data-stu-id="ec5c2-115">Other things that cause performance degradation</span></span>
    
### <a name="conclusions-reached-because-of-the-data"></a><span data-ttu-id="ec5c2-116">데이터로 인해 도달한 결론</span><span class="sxs-lookup"><span data-stu-id="ec5c2-116">Conclusions reached because of the data</span></span>
<span data-ttu-id="ec5c2-117"><a name="data"> </a></span><span class="sxs-lookup"><span data-stu-id="ec5c2-117"></span></span>

<span data-ttu-id="ec5c2-118">데이터를 통해 알 수 있는 사항은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ec5c2-118">The data tells us:</span></span>
  
- <span data-ttu-id="ec5c2-119">대부분의 페이지가 SharePoint Online에서 제대로 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="ec5c2-119">Most of the pages perform well on SharePoint Online.</span></span>
    
- <span data-ttu-id="ec5c2-120">사용자 지정되지 않은 페이지가 매우 빠르게 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="ec5c2-120">Non-customized pages load very quickly.</span></span>
    
- <span data-ttu-id="ec5c2-121">비즈니스용 OneDrive, 팀 사이트 및 시스템 페이지(_layouts 등)가 모두 신속하게 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="ec5c2-121">OneDrive for Business, team sites and system pages, such as _layouts, etc., are all quick to load.</span></span>
    
- <span data-ttu-id="ec5c2-122">SharePoint Online 페이지 중 가장 느린 1%를 로드하는 데 5,000밀리초가 넘게 걸립니다.</span><span class="sxs-lookup"><span data-stu-id="ec5c2-122">The slowest 1% of SharePoint Online pages take more than 5,000 milliseconds to load.</span></span>
    
<span data-ttu-id="ec5c2-p101">사용할 수 있는 한 가지 간단한 벤치마크 테스트는 사용자 지정된 일부 기능을 사용하면서 자체 포털의 로드 시간을 비즈니스용 OneDrive 홈 페이지의 로드 시간과 비교하여 성능을 측정하는 것입니다. 지원 서비스에서 사용자가 네트워크 성능 문제를 해결할 때 필요한 첫 번째 단계가 바로 여기에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="ec5c2-p101">One simple benchmark test you can use would be to measure performance by comparing the load time of your own portal against the load time of the OneDrive for Business home page as it uses few customized features. This will often be the first step Support will ask you to complete when troubleshooting network performance issues.</span></span>
  
## <a name="use-a-standard-user-account-when-checking-performance"></a><span data-ttu-id="ec5c2-125">성능 확인할 때 표준 사용자 계정을 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="ec5c2-125">Use a standard user account when checking performance</span></span>
<span data-ttu-id="ec5c2-126"><a name="standuser"> </a></span><span class="sxs-lookup"><span data-stu-id="ec5c2-126"></span></span>

<span data-ttu-id="ec5c2-127">사이트 모음 관리자, 사이트 소유자, 편집기 또는 참가자 추가 보안 그룹에 속해, 추가 권한이 되어 있으므로 SharePoint 페이지에 로드 되는 추가 요소 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec5c2-127">A Site Collection Administrator, Site Owner, Editor, or Contributor belong to additional security groups, have additional permissions, and therefore have additional elements that SharePoint loads on a page.</span></span>
  
<span data-ttu-id="ec5c2-128">SharePoint 온-프레미스 및 SharePoint Online에 적용할 수 있는 반드시 온-프레미스 시나리오에서 차이 그만큼 쉽게 발견 되지 SharePoint Online에서 같이 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec5c2-128">This is applicable to SharePoint on-premises and SharePoint Online but in an on-premises scenario the differences will not be as easily noticed as in SharePoint Online.</span></span>
  
<span data-ttu-id="ec5c2-129">올바르게 페이지는 사용자에 대해 수행 하는 방식 평가 하기 위해 제작 컨트롤 및 보안 그룹에 관련 된 추가 트래픽 로드를 방지 하기 위해 표준 사용자 계정을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec5c2-129">In order to correctly evaluate how a page will perform for users, you should use a standard user account to avoid loading the authoring controls and additional traffic related to security groups.</span></span>
  
## <a name="connection-categories-for-performance-tuning"></a><span data-ttu-id="ec5c2-130">성능 조정에 대한 연결 범주</span><span class="sxs-lookup"><span data-stu-id="ec5c2-130">Connection categories for performance tuning</span></span>
<span data-ttu-id="ec5c2-131"><a name="connect"> </a></span><span class="sxs-lookup"><span data-stu-id="ec5c2-131"></span></span>

<span data-ttu-id="ec5c2-p102">서버와 사용자 간의 연결을 세 가지 주요 구성 요소로 분류할 수 있습니다. 로드 시간을 고려하여 SharePoint Online 페이지를 설계할 때는 다음 사항에 유의하세요.</span><span class="sxs-lookup"><span data-stu-id="ec5c2-p102">You can categorize the connections between the server and the user into three main components. Consider these when designing SharePoint Online pages for insight into load times.</span></span>
  
- <span data-ttu-id="ec5c2-134">**서버.** Microsoft 데이터 센터에서 호스팅하는 서버입니다.</span><span class="sxs-lookup"><span data-stu-id="ec5c2-134">**Server.** The servers that Microsoft hosts in datacenters.</span></span>
    
- <span data-ttu-id="ec5c2-135">**네트워크.** Microsoft 네트워크, 인터넷 및 온-프레미스 네트워크 간에 데이터 센터 및 사용자에 게 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec5c2-135">**Network.** The Microsoft network, the Internet, and your on-premises network between the datacenter and your users.</span></span>
    
- <span data-ttu-id="ec5c2-136">**브라우저.** 여기서는 페이지가 로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ec5c2-136">**Browser.** Where the page is loaded.</span></span>
    
<span data-ttu-id="ec5c2-p103">이러한 세 가지 연결에서 느린 페이지의 95%를 차지하는 5가지 일반적인 원인이 있습니다. 다음과 같은 각 원인이 이 문서에 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ec5c2-p103">Within these three connections there are typically five reasons that cause 95% of slow pages. Each of these reasons is discussed in this article:</span></span>
  
- <span data-ttu-id="ec5c2-139">탐색 문제</span><span class="sxs-lookup"><span data-stu-id="ec5c2-139">Navigation issues</span></span>
    
- <span data-ttu-id="ec5c2-140">콘텐츠 롤업</span><span class="sxs-lookup"><span data-stu-id="ec5c2-140">Content roll up</span></span>
    
- <span data-ttu-id="ec5c2-141">대용량 파일</span><span class="sxs-lookup"><span data-stu-id="ec5c2-141">Large files</span></span>
    
- <span data-ttu-id="ec5c2-142">서버에 대한 많은 요청</span><span class="sxs-lookup"><span data-stu-id="ec5c2-142">Many requests to the server</span></span>
    
- <span data-ttu-id="ec5c2-143">웹 파트 처리</span><span class="sxs-lookup"><span data-stu-id="ec5c2-143">Web Part processing</span></span>
    
### <a name="server-connection"></a><span data-ttu-id="ec5c2-144">서버 연결</span><span class="sxs-lookup"><span data-stu-id="ec5c2-144">Server connection</span></span>
<span data-ttu-id="ec5c2-145"><a name="server"> </a></span><span class="sxs-lookup"><span data-stu-id="ec5c2-145"></span></span>

<span data-ttu-id="ec5c2-146">SharePoint 온-프레미스의 성능에 영향을 주는 많은 문제가 SharePoint Online에도 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ec5c2-146">Many of the issues that affect performance with SharePoint on-premises also apply to SharePoint Online.</span></span>
  
<span data-ttu-id="ec5c2-p104">예상할 수 있듯이 온-프레미스 SharePoint를 사용하면 서버의 성능을 훨씬 더 강력하게 제어할 수 있습니다. SharePoint Online을 사용하는 경우 상황이 약간 달라집니다. 서버가 수행하는 작업이 많을수록 페이지를 렌더링하는 데 더 오래 걸립니다. SharePoint를 사용하는 경우 이러한 측면에서 가장 큰 원인은 여러 웹 파트가 있는 복잡한 페이지입니다.</span><span class="sxs-lookup"><span data-stu-id="ec5c2-p104">As you would expect, you have far more control over how servers perform with on-premises SharePoint. With SharePoint Online things are a little different. The more work you make a server do, the longer it takes to render a page. With SharePoint, the biggest culprit in this respect are complex pages with multiple web parts.</span></span>
  
<span data-ttu-id="ec5c2-151">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ec5c2-151">SharePoint Online</span></span>
  
![온라인 서버의 스크린샷](media/a8e9b646-cdff-4131-976a-b5f891da44ac.png)
  
<span data-ttu-id="ec5c2-153">SharePoint</span><span class="sxs-lookup"><span data-stu-id="ec5c2-153">SharePoint</span></span>
  
![온-프레미스 서버의 스크린샷](media/46b27ded-d8a4-4287-b3e0-2603a764b8f8.png)
  
<span data-ttu-id="ec5c2-p105">SharePoint Online을 사용하는 경우에는 특정 페이지 요청이 실제로 여러 서버 호출을 발생할 수 있습니다. 개별 요청에 대해 서버 간에 단계별 요청 구조가 발생할 수 있습니다. 이러한 상호 작용은 페이지 부하 측면에서는 많은 비용을 초래하며 속도를 저하시킵니다.</span><span class="sxs-lookup"><span data-stu-id="ec5c2-p105">With SharePoint Online, certain page requests may actually end up calling multiple servers. You could end up with a matrix of requests between servers for an individual request. These interactions are expensive from a page load perspective and will make things slow.</span></span>
  
<span data-ttu-id="ec5c2-158">이러한 서버 간 상호 작용의 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ec5c2-158">Examples of these server to server interactions are:</span></span>
  
- <span data-ttu-id="ec5c2-159">웹 - SQL 서버</span><span class="sxs-lookup"><span data-stu-id="ec5c2-159">Web to SQL Servers</span></span>
    
- <span data-ttu-id="ec5c2-160">웹 - 응용 프로그램 서버</span><span class="sxs-lookup"><span data-stu-id="ec5c2-160">Web to application servers</span></span>
    
<span data-ttu-id="ec5c2-p106">서버 상호 작용을 저하시킬 수 있는 기타 요인으로는 캐시 누락이 있습니다. 온-프레미스 SharePoint와 달리, 이전에 방문한 페이지에 동일한 서버가 사용될 가능성이 아주 적으므로 개체 캐싱이 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ec5c2-p106">The other thing that can slow down server interactions is cache misses. Unlike on-premises SharePoint, there is a very slim chance that you will hit the same server for a page that you have visited previously; this makes object caching obsolete.</span></span>
  
### <a name="network-connection"></a><span data-ttu-id="ec5c2-163">네트워크 연결</span><span class="sxs-lookup"><span data-stu-id="ec5c2-163">Network connection</span></span>
<span data-ttu-id="ec5c2-164"><a name="network"> </a></span><span class="sxs-lookup"><span data-stu-id="ec5c2-164"></span></span>

<span data-ttu-id="ec5c2-p107">사용할 수 있도록 하지 WAN의 온-프레미스 sharepoint를 데이터 센터와 최종 사용자에 게 간의 고속 연결을 사용할 수 있습니다. 일반적으로 작업에는 네트워크의 관점에서 관리 하기 어렵습니다.</span><span class="sxs-lookup"><span data-stu-id="ec5c2-p107">With on-premises SharePoint that doesn't make use of a WAN, you may use a high-speed connection between datacenter and end-users. Generally, things are easy to manage from a network perspective.</span></span>
  
<span data-ttu-id="ec5c2-167">SharePoint Online을 사용하는 경우 다음과 같은 몇 가지 요인을 더 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec5c2-167">With SharePoint Online, there are a few more factors to consider; for example:</span></span>
  
- <span data-ttu-id="ec5c2-168">Microsoft 네트워크</span><span class="sxs-lookup"><span data-stu-id="ec5c2-168">The Microsoft network</span></span>
    
- <span data-ttu-id="ec5c2-169">인터넷</span><span class="sxs-lookup"><span data-stu-id="ec5c2-169">The Internet</span></span>
    
- <span data-ttu-id="ec5c2-170">ISP</span><span class="sxs-lookup"><span data-stu-id="ec5c2-170">The ISP</span></span>
    
<span data-ttu-id="ec5c2-171">사용 중인 SharePoint 버전(및 네트워크)와 관계없이, 일반적으로 네트워크의 사용량을 높이는 항목은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ec5c2-171">Regardless of which version of SharePoint (and which network) you are using, things that will typically cause the network to be busy include:</span></span>
  
- <span data-ttu-id="ec5c2-172">대형 페이로드</span><span class="sxs-lookup"><span data-stu-id="ec5c2-172">Large payload</span></span>
    
- <span data-ttu-id="ec5c2-173">많은 수의 파일</span><span class="sxs-lookup"><span data-stu-id="ec5c2-173">Many files</span></span>
    
- <span data-ttu-id="ec5c2-174">서버와의 큰 실제 거리</span><span class="sxs-lookup"><span data-stu-id="ec5c2-174">Large physical distance to the server</span></span>
    
<span data-ttu-id="ec5c2-p108">SharePoint Online에서 활용할 수 있는 기능 중 하나는 Microsoft CDN (콘텐츠 배달 네트워크)입니다. CDN는 기본적으로 여러 데이터 센터에 배포 된 서버의 분산된 컬렉션입니다. CDN와 경우에 클라이언트 멀리 떨어져 원래 SharePoint 서버에서 클라이언트에 근접 한 서버에서 페이지에 콘텐츠를 호스팅할 수 있습니다. Microsoft 됩니다 수를 사용 하 여이 더 나중에 SharePoint Online 관리자 홈 페이지 같은 수 없는 사용자 지정할 수 있는 페이지의 로컬 인스턴스를 저장 합니다. Cdn 하는 방법에 대 한 자세한 내용은 [콘텐츠 배달 네트워크](https://support.office.com/article/Content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="ec5c2-p108">One feature that you can leverage in SharePoint Online is the Microsoft CDN (Content Delivery Network). A CDN is basically a distributed collection of servers deployed across multiple datacenters. With a CDN, content on pages can be hosted on a server close to the client even if the client is far away from the originating SharePoint Server. Microsoft will be using this more in the future to store local instances of pages which cannot be customized, for example the SharePoint Online admin home page. For more information about CDNs, see [Content delivery networks](https://support.office.com/article/Content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f).</span></span>
  
<span data-ttu-id="ec5c2-p109">고려해야 하지만 많은 작업을 수행할 수는 없는 측면이 바로 ISP의 연결 속도입니다. 간단한 속도 테스트 도구로 연결 속도를 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ec5c2-p109">Something that you need to be aware of but may not be able to do much about is the connection speed of your ISP. A simple speed test tool will tell you the connection speed.</span></span>
  
### <a name="browser-connection"></a><span data-ttu-id="ec5c2-182">브라우저 연결</span><span class="sxs-lookup"><span data-stu-id="ec5c2-182">Browser connection</span></span>
<span data-ttu-id="ec5c2-183"><a name="browser"> </a></span><span class="sxs-lookup"><span data-stu-id="ec5c2-183"></span></span>

<span data-ttu-id="ec5c2-184">성능 측면에서 웹 브라우저에 대해 고려해야 할 몇 가지 요소가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ec5c2-184">There are a few factors to consider with web browsers from a performance perspective.</span></span>
  
<span data-ttu-id="ec5c2-p110">복잡 한 페이지를 방문 하는 것 성능에 영향을 줍니다. 대부분의 브라우저에 하나만 평균 하는 동안 작은 캐시 (약 90 MB), 웹 페이지는 일반적으로 약 1.6 MB입니다. 이 사용 하는 데 긴 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ec5c2-p110">Visiting complex pages will affect performance. Most browsers only have a small cache (around 90MB), while the average web page is typically around 1.6MB. This doesn't take long to get used up.</span></span>
  
<span data-ttu-id="ec5c2-p111">대역폭이 문제가 될 수도 있습니다. 예, 사용자가 다른 세션에 비디오를 보고,이 SharePoint 페이지의 성능을 적용 됩니다. 스트리밍 미디어에서 사용자를 방지 수 없는 사용자에 대 한 페이지를 로드 하는 방식을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ec5c2-p111">Bandwidth may also be an issue. For example, if a user is watching videos in another session, this will affect the performance of your SharePoint page. While you can't prevent users from streaming media, you can control the way a page will load for users.</span></span>
  
<span data-ttu-id="ec5c2-191">다른 SharePoint Online 페이지 사용자 지정 방법에 대 한 다음 문서 및 기타 모범 사례 최적의 성능을 얻을 수 있도록 체크아웃 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec5c2-191">Check out the following articles for different SharePoint Online page customization techniques and other best practices to help you achieve optimal performance.</span></span>
  
- [<span data-ttu-id="ec5c2-192">SharePoint Online에 대한 탐색 옵션</span><span class="sxs-lookup"><span data-stu-id="ec5c2-192">Navigation options for SharePoint Online</span></span>](navigation-options-for-sharepoint-online.md)
    
- [<span data-ttu-id="ec5c2-193">SharePoint Online에 대 한 페이지 진단 도구를 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="ec5c2-193">Use the Page Diagnostics tool for SharePoint Online</span></span>](page-diagnostics-for-spo.md)
    
- [<span data-ttu-id="ec5c2-194">SharePoint Online에 대한 이미지 최적화</span><span class="sxs-lookup"><span data-stu-id="ec5c2-194">Image optimization for SharePoint Online</span></span>](image-optimization-for-sharepoint-online.md)
    
- [<span data-ttu-id="ec5c2-195">SharePoint Online에서 이미지 및 JavaScript 로드 지연</span><span class="sxs-lookup"><span data-stu-id="ec5c2-195">Delay loading images and JavaScript in SharePoint Online</span></span>](delay-loading-images-and-javascript-in-sharepoint-online.md)
    
- [<span data-ttu-id="ec5c2-196">SharePoint Online의 축소 및 묶음</span><span class="sxs-lookup"><span data-stu-id="ec5c2-196">Minification and bundling in SharePoint Online</span></span>](minification-and-bundling-in-sharepoint-online.md)
    
- [<span data-ttu-id="ec5c2-197">콘텐츠 배달 네트워크 사용</span><span class="sxs-lookup"><span data-stu-id="ec5c2-197">Using content delivery networks</span></span>](using-content-delivery-networks-with-sharepoint-online.md)
    
- [<span data-ttu-id="ec5c2-198">콘텐츠 쿼리 웹 파트는 대신 콘텐츠 검색 웹 파트를 사용 하 여 SharePoint Online에서 성능을 개선합니다</span><span class="sxs-lookup"><span data-stu-id="ec5c2-198">Using Content Search Web Part instead of Content Query Web Part to improve performance in SharePoint Online</span></span>](using-content-search-web-part-instead-of-content-query-web-part-to-improve-perfo.md)
    
- [<span data-ttu-id="ec5c2-199">용량 계획 및 부하 테스트를 SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ec5c2-199">Capacity planning and load testing SharePoint Online</span></span>](capacity-planning-and-load-testing-sharepoint-online.md)
    
- [<span data-ttu-id="ec5c2-200">SharePoint Online의 성능 문제 진단</span><span class="sxs-lookup"><span data-stu-id="ec5c2-200">Diagnosing performance issues with SharePoint Online</span></span>](diagnosing-performance-issues-with-sharepoint-online.md)
    
- [<span data-ttu-id="ec5c2-201">SharePoint online에서 개체 캐시 사용</span><span class="sxs-lookup"><span data-stu-id="ec5c2-201">Using the object cache with SharePoint Online</span></span>](using-the-object-cache-with-sharepoint-online.md)
    
- [<span data-ttu-id="ec5c2-202">방법: SharePoint Online에서 제한 또는 차단되지 않도록 방지</span><span class="sxs-lookup"><span data-stu-id="ec5c2-202">How to: Avoid getting throttled or blocked in SharePoint Online</span></span>](https://msdn.microsoft.com/en-us/library/office/dn889829.aspx)
    

