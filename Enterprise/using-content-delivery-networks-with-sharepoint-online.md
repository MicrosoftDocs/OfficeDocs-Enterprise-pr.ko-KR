---
title: 콘텐츠 배달 네트워크를 사용 하 여 SharePoint Online을 사용한
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 5/8/2017
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: 9a64268c-0b74-4eaa-b971-fb6380b1b165
description: 요약:이 문서에서는 콘텐츠 배달 네트워크 (Cdn) 및 SharePoint Online 성능을 향상 시키기 위해이 사용 하는 방법에 대해 설명 합니다.
ms.openlocfilehash: 63062c08d0c22518eb36ea0a6faa97106fd394b4
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542020"
---
# <a name="using-content-delivery-networks-with-sharepoint-online"></a><span data-ttu-id="8e934-103">콘텐츠 배달 네트워크를 사용 하 여 SharePoint Online을 사용한</span><span class="sxs-lookup"><span data-stu-id="8e934-103">Using content delivery networks with SharePoint Online</span></span>

 <span data-ttu-id="8e934-104">**요약:** 이 문서에서는 콘텐츠 배달 네트워크 (Cdn) 및 SharePoint Online 성능을 향상 시키기 위해이 사용 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e934-104">**Summary:** This article describes Content Delivery Networks (CDNs) and how you can use them to increase SharePoint Online performance.</span></span> 
  
<span data-ttu-id="8e934-p101">오늘날의 웹 개발 커뮤니티에서 많은 일반적인 라이브러리 (예: JavaScript 및 CSS 파일)를 SharePoint 솔루션에 포함할 수 있습니다. 이러한 대부분는 Microsoft가 asp (영문) CDN에 의해 호스팅됩니다. 즉, 이러한 분산된 서버에서 이러한 라이브러리를 참조 하 고 사용자를 가장 가까운 서버를 찾을 수는 인터넷 제공 하는 DNS 기본 제공 라우팅 시스템을 허용 합니다. 이 문서의 예제 asp (영문) CDN과 SharePoint Online 서버에서 인기 있는 라이브러리 jQuery 다운로드 사이의 시간 차이 매우 중요 한 방법을 보여줍니다. 사용자는 파일을 다운로드 하려면 없는 되도록 로컬 컴퓨터에서 캐시 된 CDN 버전을 이미는 될 수 있습니다. 이 사용자의 및 멀리 떨어져 SharePoint Online 사이트를 호스팅하는 데이터 센터에서 배포 된 경우에 중요 한 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e934-p101">In today's web development communities, there are many common libraries (such as JavaScript and CSS files) that you may include in your SharePoint solution. Many of these are hosted by Microsoft on their ASP CDN. This means you can reference these libraries from these distributed servers and allow the internet's built-in DNS routing systems to find the closest server to your user. The examples in this article demonstrate how the time difference between downloading the popular library jQuery from the SharePoint Online server versus the ASP CDN is quite significant. The user also may already have the CDN version cached on the local computer so that they do not have to download the file. This can be important if you have users distributed all over the world and far away from the datacenter that hosts your SharePoint Online site.</span></span>
  
<span data-ttu-id="8e934-p102">SharePoint Online용 페이지를 만들 때 사용자와 SharePoint Online 인스턴스 위치 간의 실제 거리가 대기 시간에 영향을 줄 수 있습니다. 이 특성은 사이트가 한 대륙에 호스팅될 수 있지만 다른 나라 사용자들이 해당 콘텐츠에 액세스하는 글로벌 서비스를 제공하는 조직에서 특히 중요합니다. CDN은 최종 사용자에게 좀 더 가까운 여러 다른 위치에서 인기 있는 특정 웹 자산을 호스팅하여 이러한 상황을 완화하는 데 도움을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8e934-p102">When creating pages for SharePoint Online, latency can be affected by the physical distance between your users and the location of the SharePoint Online instance. This is particularly important for organizations that have a global presence where a site may be hosted on one continent while users on the other side of the world are accessing its content. CDNs help mitigate this situation by hosting certain popular web assets in different locations closer to the end users.</span></span>
  
<span data-ttu-id="8e934-p103">CDN은 같은 파일을 호스팅하는 전 세계 서버 네트워크이므로 클라이언트 컴퓨터에서는 CDN에 저장된 파일에 대한 인터넷 URL을 해석하여 사용자에게 가장 가까운 서버에서 파일을 제공할 수 있도록 합니다. 이렇게 하면 네트워크 왕복 이동으로 인한 지연 시간이 크게 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="8e934-p103">Since a CDN is a worldwide network of servers that host the same files, Internet URLs for files stored on the CDNs are interpreted by the client machine so that the server that is closest to the user serves the file. Doing this significantly reduces delays caused by network round trips.</span></span>
  
## <a name="the-challenge-of-hosting-sharepoint-online-sites-for-a-global-audience"></a><span data-ttu-id="8e934-116">전역 대상 그룹을 위해 SharePoint Online 사이트를 호스팅하는 문제</span><span class="sxs-lookup"><span data-stu-id="8e934-116">The challenge of hosting SharePoint Online sites for a global audience</span></span>

<span data-ttu-id="8e934-p104">SharePoint Online 사이트는 Office 365에 등록할 때 선택한 위치(사용자가 지정)를 기준으로 데이터 센터에 호스팅됩니다. 예를 들어 사이트가 미국의 서버에 있고 동아시아 지역에서 해당 사이트에 액세스하는 사용자가 있는 경우, 데이터가 광섬유 케이블을 통해 이동해야 하는 거리 때문에 대기 시간 문제가 발생할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e934-p104">SharePoint Online sites are hosted at datacenters relative to the location (specified by the user) selected when you signed up with Office 365. For example, if your site is on servers in the United States and you have users accessing the site from East Asia, latency issues might arise due to the distance the data has to travel over fiber optic cable.</span></span>
  
<span data-ttu-id="8e934-p105">기본 SharePoint 사용자 인터페이스에 사용 되는 많은 정적 파일 Cdn의 Microsoft의 전세계 네트워크에 이미 호스팅됩니다. 이 시간에 따른 성능을 향상 시킬 수 있습니다. 그러나 (예; 자주 사용 되는 모든 JavaScript 및 CSS 자산을 사용 하는 경우, JQuery, Modernizr, 부트스트랩, 또는 ASP.NET Ajax) 무료로 사용할 수 있지만 Cdn를 사용 하 여 이러한 파일의 로드 시간을 향상 시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e934-p105">Many static files used by the default SharePoint user interface are already hosted on Microsoft's worldwide network of CDNs. This will improve performance over time. However, if you use any popular JavaScript and CSS assets (for example; JQuery, Modernizr, Bootstrap, or ASP.NET Ajax) you can improve the loading times of these files by using freely available CDNs.</span></span>
  
## <a name="advantages-of-using-cdns-to-improve-download-speed"></a><span data-ttu-id="8e934-122">다운로드 속도를 향상시키는 CDN을 사용할 때의 이점</span><span class="sxs-lookup"><span data-stu-id="8e934-122">Advantages of using CDNs to improve download speed</span></span>

<span data-ttu-id="8e934-p106">Cdn를 사용 하 여 다양 한 이유 때문에 대 한 페이지 로드 시간을 향상 시킬 수 있습니다. 이유 중 하나는 CDN와 사용자 사이의 거리를 SharePoint Online 인스턴스 거리 보다 더 짧은 수 있습니다. 이러한 네트워크는 고도로 분산 및은 또한 매우 높은 가용성 및 응답 시간 하도록 설계 되었습니다. 다른 이유 하는 경우 CSS 파일의 인기 있는 라이브러리를 사용 하는, CDN 함께, 사용자 캐시 된 라이브러리를 이미 있을 수도 및 전혀 다운로드 하는데 필요한도 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8e934-p106">Using CDNs can improve page load times for a variety of reasons. One reason is that the distance between the CDN and the user may be shorter than the distance to the SharePoint Online instance. These networks are highly distributed and are also designed to have very high availability and response times. Another reason is that if you are using a popular library of CSS files, in conjunction with a CDN, the user may already have the library cached and they won't even need to download it at all.</span></span>
  
<span data-ttu-id="8e934-p107">다음 스크린샷에서 Cdn를 사용 하 여의 이점을 설명 합니다. Internet Explorer 11 개발자 도구에 있는 **네트워크** 탭에서 이러한 스크린샷에서 합니다. 다음 스크린샷에서 인기 있는 라이브러리 jQuery에서 대기 시간을 보여줍니다. Internet Explorer에서이 화면에서 불러올 수 **F12** 키를 눌러 하 고 Wi-fi 아이콘과 함께 symbolized 하는 **네트워크** 탭을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e934-p107">The following screen shots illustrate the advantages of using CDNs. These screen shots are from the **Network** tab in the Internet Explorer 11 developer tools. These screen shots show the latency on the popular library jQuery. To bring up this screen, in Internet Explorer, press **F12** and select the **Network** tab which is symbolized with a Wi-Fi icon.</span></span> 
  
![F12 네트워크의 스크린샷](media/930541fd-af9b-434a-ae18-7bda867be128.png)
  
<span data-ttu-id="8e934-p108">이 스크린샷은 SharePoint Online 사이트 자체에 마스터 페이지 갤러리에 업로드 하는 라이브러리를 보여줍니다. 라이브러리를 업로드 하려면 걸린 시간은 1.51 초입니다.</span><span class="sxs-lookup"><span data-stu-id="8e934-p108">This screen shot shows the library uploaded to the master page gallery on the SharePoint Online site itself. The time it took to upload the library is 1.51 seconds.</span></span>
  
![1.51초의 로드 시간을 보여 주는 스크린샷](media/64225c79-fa53-480f-81cd-0d351674320e.png)
  
<span data-ttu-id="8e934-p109">두번째 스크린샷에서 Microsoft의에 의해 전달 되는 동일한 파일을 보여주는 CDN 합니다. 이 대기 시간은 약 496 시간 (밀리초)입니다. 이 대규모 향상 된 기능 및 전체 초 페이지 콘텐츠를 다운로드 하려면 총 시간 오프 shaved 되는 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e934-p109">The second screen shot shows the same file delivered by Microsoft's CDN. This time the latency is around 496 milliseconds. This is a large improvement and shows that a whole second is shaved off the total time to download the page content.</span></span>
  
![469밀리초의 로드 시간을 보여 주는 스크린샷](media/6a553cc3-25a0-42c1-aae7-4aebbc2eb4c3.png)
  
## <a name="using-cdns-with-sharepoint-server-2013"></a><span data-ttu-id="8e934-139">SharePoint Server 2013에서 CDN 사용</span><span class="sxs-lookup"><span data-stu-id="8e934-139">Using CDNs with SharePoint Server 2013</span></span>

<span data-ttu-id="8e934-p110">Cdn를 사용 하 여 SharePoint Online 컨텍스트에서 합당 되 고 SharePoint Server 2013과 함께 사용 하지 않아야 합니다. 이 서버에 있는 온-프레미스 이면 true를 유지 하지 않거나 닫으려면 지리적으로 모든 지리적 위치 주위 장점 때문입니다. 또한가 호스팅되는 서버에 대 한 네트워크 연결 하는 경우 다음 사이트 인터넷에 연결 하지 않고 사용 될 수 있습니다 및 CDN 파일을 검색할 수 없습니다. 그렇지 않은 경우 하나 사용할 수 있고 사이트에 라이브러리 및 파일에 대 한 안정적인 필요한 경우에 CDN 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e934-p110">Using CDNs only makes sense in a SharePoint Online context and should be avoided with SharePoint Server 2013. This is because all of the advantages around geographic location do not hold true if the server is located on-premises or geographically close anyway. Additionally, if there is a network connection to the servers where it's hosted, then the site may be used without an Internet connection and therefore cannot retrieve the CDN files. Otherwise, you should use a CDN if there is one available and stable for the library and files you need for your site.</span></span>
  
## <a name="popular-cdns-and-how-to-use-them"></a><span data-ttu-id="8e934-144">인기 있는 CDN 및 사용 방법</span><span class="sxs-lookup"><span data-stu-id="8e934-144">Popular CDNs and how to use them</span></span>

<span data-ttu-id="8e934-145">Microsoft의 Ajax CDN 제공 대부분 jQuery (및 모든 해당 다른 라이브러리)를 포함 하 여 인기 있는 라이브러리의 ASP.NET Ajax, 부트스트랩, Knockout.js, 및 더 많은 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e934-145">Microsoft's Ajax CDN offers most of the popular libraries including jQuery (and all of its other libraries), ASP.NET Ajax, Bootstrap, Knockout.js, and many more.</span></span>
  
<span data-ttu-id="8e934-p111">프로젝트에 이러한 스크립트를 포함하려면 프로젝트 자체에 포함하는 대신, 공개적으로 사용할 수 있는 이러한 라이브러리에 대한 참조를 CDN 주소에 대한 참조로 바꾸면 됩니다. 예를 들어 jQuery에 연결하려면 다음 코드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8e934-p111">To include these scripts in your project, simply replace any references to these publicly available libraries with references to the CDN address instead of including it in your project itself. For example, use the following code to link to jQuery:</span></span>
  
```
<script src=http://ajax.aspnetcdn.com/ajax/jquery-2.1.1.js> </script>
```

<span data-ttu-id="8e934-148">Cdn 하는 방법에 대 한 자세한 내용은 [콘텐츠 배달 네트워크](content-delivery-networks.md)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="8e934-148">For more information about CDNs, see [Content delivery networks](content-delivery-networks.md).</span></span>
  
## <a name="more-topics-about-using-cdns-with-sharepoint"></a><span data-ttu-id="8e934-149">SharePoint와 함께 Cdn를 사용 하는 방법에 대 한 더 많은 항목</span><span class="sxs-lookup"><span data-stu-id="8e934-149">More topics about using CDNs with SharePoint</span></span>

[<span data-ttu-id="8e934-150">Office 365 CDN에서 호스팅 클라이언트쪽 웹 파트</span><span class="sxs-lookup"><span data-stu-id="8e934-150">Hosting client-side web part from Office 365 CDN</span></span>](https://dev.office.com/sharepoint/docs/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn)
  

