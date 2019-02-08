---
title: SharePoint online에서 개체 캐시 사용
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/20/2015
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 38bc9c14-3826-449c-beb6-b1003bcbeaaf
description: 이 문서에서는 SharePoint Server 2013 온-프레미스 및 SharePoint Online에서 개체 캐시를 사용 하 여 간의 차이 설명 합니다.
ms.openlocfilehash: 59f3a69199893cb367d4d28c0c545ebd9dfd1236
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2019
ms.locfileid: "25769857"
---
# <a name="using-the-object-cache-with-sharepoint-online"></a><span data-ttu-id="8094b-103">SharePoint online에서 개체 캐시 사용</span><span class="sxs-lookup"><span data-stu-id="8094b-103">Using the object cache with SharePoint Online</span></span>

<span data-ttu-id="8094b-104">이 문서에서는 SharePoint Server 2013 온-프레미스 및 SharePoint Online에서 개체 캐시를 사용 하 여 간의 차이 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="8094b-104">This article explains the difference between using the object cache in SharePoint Server 2013 on-premises and SharePoint Online.</span></span>
  
<span data-ttu-id="8094b-p101">SharePoint Online 배포에서 개체 캐시에 의존할 경우 큰 문제가 발생합니다. SharePoint Online에서 개체 캐시에 의존하면 페이지의 안정성이 떨어집니다.</span><span class="sxs-lookup"><span data-stu-id="8094b-p101">There is significant negative impact of relying on the object cache in SharePoint Online deployment. Any dependency on object cache in SharePoint Online will reduce the reliability of your page.</span></span> 
  
## <a name="how-the-sharepoint-online-and-sharepoint-server-2013-object-cache-works"></a><span data-ttu-id="8094b-107">SharePoint Online 및 SharePoint Server 2013 개체 캐시의 작동 방식</span><span class="sxs-lookup"><span data-stu-id="8094b-107">How the SharePoint Online and SharePoint Server 2013 object cache works</span></span>

<span data-ttu-id="8094b-p102">호스팅된 온-프레미스 SharePoint Server 2013을 사용 하는 경우 고객 개체 캐시를 호스트 하는 개인 프런트엔드 웹 서버에 있습니다. 즉, 캐시 한 고객 전용 하 고만 사용 가능 하 고 개체 캐시에 할당 된 메모리의 양을에 의해 제한 됩니다. 온-프레미스 시나리오에서 하나만 고객을 처리 하기 때문에 프런트엔드 웹 서버는 일반적으로 반복 해 동일한 사이트에 요청을 수행 하는 사용자를 가집니다. 즉, 캐시 전체 신속 하 게 가져옵니다 목록 쿼리 결과 주기적으로 사용자에 게 요청 하는 SharePoint 개체의 전체 유지 되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="8094b-p102">When SharePoint Server 2013 is hosted on-premises, the customer has private front-end web servers that host the object cache. This means the cache is dedicated to one customer and is only limited by how much memory is available and allocated to the object cache. Because only one customer is served in the on-premises scenario the front-end web servers typically have users making requests to the same sites over and over. This means that the cache gets full quickly and remains full of the list query results and SharePoint objects that your users are requesting on a regular basis.</span></span>
  
![온-프레미스 프런트 엔드 웹 서버에 대한 트래픽 및 로드 표시](media/a0d38b36-4909-4abb-8d4e-4930814bb3de.png)
  
<span data-ttu-id="8094b-p103">결과적으로 사용자가 페이지를 두 번째로 방문하면 페이지 로드 시간이 줄어듭니다. 같은 페이지가 최소 네 번 로드되면 페이지는 모든 프런트 엔드 웹 서버에서 캐시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8094b-p103">As a result, the second time a user visits a page, the page load time improves. After a minimum of four loads of the same page, the page is cached on all of the front-end web servers.</span></span>
  
<span data-ttu-id="8094b-p104">반면, SharePoint Online는 서버를 더 많은 하지만 더 많은 사이트에도 있습니다. 각 사용자 채워진 캐시를 갖고 있지 않은 다른 프런트엔드 웹 서버에 연결할 수 있습니다. 또는 아마도 캐시는 자동으로 입력 한 서버를 포함 하지만 다음 사용자에 대 한 페이지를 해당 프런트엔드 웹 서버 요청을 다른 사이트에서 합니다. 또는 다음 사용자가 같은 페이지에 자신의 이전 방문할 때를 요청 하는 경우에 해당 페이지의 캐시에 없는 다른 프런트엔드 웹 서버에 부하 분산 된 것이 있습니다. 이 지난 경우 캐싱 (영문) 되지 않습니다 사용자 전혀 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8094b-p104">In contrast, in SharePoint Online there are many more servers but also many more sites. Each user may connect to a different front-end web server that doesn't have the cache populated. Or, perhaps the cache does get populated for a server, but the next user to that front-end web server requests a page from a different site. Or, even if the next user requests the same page as on their previous visit, they are load-balanced to a different front-end web server that doesn't have that page in its cache. In this last case, caching doesn't help the users at all.</span></span>
  
<span data-ttu-id="8094b-p105">다음 그림에서 각 점은 사용자가 요청을 하고 캐시되는 페이지를 나타냅니다. SaaS 인프라를 공유하여 사용하는 여러 다른 고객이 다른 색상으로 표시되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8094b-p105">In the following figure, each dot represents a page that a user is requesting and where it cached. Different colors represent different customers making shared use of the SaaS infrastructure.</span></span>
  
![SharePoint Online의 개체 캐시 결과 표시](media/25d04011-ef83-4cb7-9e04-a6ed490f63c3.png)
  
<span data-ttu-id="8094b-p106">다이어그램에서 볼 수 있듯이 해당 페이지의 캐시 된 버전으로 서버를 방문 하는 특정된 사용자의 경우 가능성 많지 않습니다. 또한 큰 처리량과 서버 다 수의 사이트 간에 공유 되는 팩트,으로 인해 사용 가능한 캐싱 (영문)에 대 한 보다 공간에만 있기 때문에 긴 캐시 지속 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8094b-p106">As you can see from the diagram, the chances of any given user hitting a server with the cached version of their page are slim. Also, due to the large throughput and fact that the servers are shared between many sites, the cache doesn't last long since there is only so much space for caching available.</span></span>
  
<span data-ttu-id="8094b-125">이러한 모든 이유로, 캐시된 개체를 가져오는 사용자에게 의존하는 방식은 SharePoint Online에서 좋은 사용자 환경과 적절한 페이지 로드 시간을 유지할 수 있는 효과적인 방법이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="8094b-125">For all of these reasons, relying on users getting cached objects is not an effective way to ensure a quality user experience and page load times in SharePoint Online.</span></span>
  
## <a name="if-we-cant-rely-on-the-object-cache-to-improve-performance-in-sharepoint-online-what-do-we-use-instead"></a><span data-ttu-id="8094b-126">SharePoint Online에서 성능을 향상시키기 위해 개체 캐시에 의존할 수 없다면 대신 어떤 작업을 수행해야 합니까?</span><span class="sxs-lookup"><span data-stu-id="8094b-126">If we can't rely on the object cache to improve performance in SharePoint Online, what do we use instead?</span></span>

<span data-ttu-id="8094b-p107">SharePoint Online에서 캐싱에 의존할 수 없다면 개체 캐시를 사용하는 SharePoint 사용자 지정을 위한 대체 디자인 접근 방식을 평가해야 합니다. 즉, 개체 캐싱에 의존하지 않으면서 사용자에게 적합한 결과를 줄 수 있는 성능 향상을 위한 접근 방법을 찾아야 합니다. 이 내용은 본 시리즈의 다른 일부 문서에 나와 있으며 다음 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8094b-p107">Since you shouldn't rely on caching in SharePoint Online, you should evaluate alternative design approaches for SharePoint customizations that use the object cache. This means using approaches for performance issues which do not rely on the object caching in order to produce good results for users. This is described in some of the other articles in this series and include:</span></span>
  
- [<span data-ttu-id="8094b-130">SharePoint Online에 대한 탐색 옵션</span><span class="sxs-lookup"><span data-stu-id="8094b-130">Navigation options for SharePoint Online</span></span>](navigation-options-for-sharepoint-online.md)
    
- [<span data-ttu-id="8094b-131">SharePoint Online의 축소 및 묶음</span><span class="sxs-lookup"><span data-stu-id="8094b-131">Minification and bundling in SharePoint Online</span></span>](minification-and-bundling-in-sharepoint-online.md)
    
- [<span data-ttu-id="8094b-132">콘텐츠 배달 네트워크 사용</span><span class="sxs-lookup"><span data-stu-id="8094b-132">Using content delivery networks</span></span>](using-content-delivery-networks-with-sharepoint-online.md)
    
- [<span data-ttu-id="8094b-133">SharePoint Online에서 이미지 및 JavaScript 로드 지연</span><span class="sxs-lookup"><span data-stu-id="8094b-133">Delay loading images and JavaScript in SharePoint Online</span></span>](delay-loading-images-and-javascript-in-sharepoint-online.md)
    

