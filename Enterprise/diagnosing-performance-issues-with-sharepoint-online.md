---
title: SharePoint Online의 성능 문제 진단
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 2/23/2018
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 3c364f9e-b9f6-4da4-a792-c8e8c8cd2e86
description: 이 문서에서는 Internet Explorer 개발자 도구를 사용 하 여 SharePoint Online 사이트와의 공통 문제를 진단할 수는 방법을 보여줍니다.
ms.openlocfilehash: 89d4544bfabf6424b5f401bad7d63bd7fa41b5ca
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542064"
---
# <a name="diagnosing-performance-issues-with-sharepoint-online"></a><span data-ttu-id="9f87a-103">SharePoint Online의 성능 문제 진단</span><span class="sxs-lookup"><span data-stu-id="9f87a-103">Diagnosing performance issues with SharePoint Online</span></span>

<span data-ttu-id="9f87a-104">이 문서에서는 Internet Explorer 개발자 도구를 사용 하 여 SharePoint Online 사이트와의 공통 문제를 진단할 수는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="9f87a-104">This article shows you how you can diagnose common issues with your SharePoint Online site using Internet Explorer developer tools.</span></span>
  
<span data-ttu-id="9f87a-105">SharePoint Online 사이트의 페이지에서 사용자 지정을 수행할 때 발생하는 성능 문제는 다음과 같은 세 가지 방법으로 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f87a-105">There are three different ways that you can identify that a page on a SharePoint Online site has a performance problem with the customizations.</span></span>
  
- <span data-ttu-id="9f87a-106">F12 도구 모음 네트워크 모니터</span><span class="sxs-lookup"><span data-stu-id="9f87a-106">The F12 tool bar network monitor</span></span>
    
- <span data-ttu-id="9f87a-107">사용자 지정하지 않은 기준과 비교</span><span class="sxs-lookup"><span data-stu-id="9f87a-107">Comparison to a non-customized baseline</span></span>
    
- <span data-ttu-id="9f87a-108">SharePoint Online 응답 헤더 메트릭</span><span class="sxs-lookup"><span data-stu-id="9f87a-108">SharePoint Online response header metrics</span></span>
    
<span data-ttu-id="9f87a-p101">이 항목에서는 이러한 각 메서드를 사용 하 여 성능 문제를 진단 하는 방법에 설명 합니다. 쪽에서 찾을 수 있는 SharePoint 성능을 개선 하는 방법에 대 한 문서를 사용 하는 솔루션으로 작업할 수 문제의 원인이 계산 했습니다, 일단 http://aka.ms/tune합니다.</span><span class="sxs-lookup"><span data-stu-id="9f87a-p101">This topic describes how to use each of these methods to diagnose performance issues. Once you've figured out the cause of the problem, you can work toward a solution using the articles about improving SharePoint performance that you can find on http://aka.ms/tune.</span></span>
  
## <a name="using-the-f12-tool-bar-to-diagnose-performance-in-sharepoint-online"></a><span data-ttu-id="9f87a-111">F12 도구 모음을 사용하여 SharePoint Online의 성능 진단</span><span class="sxs-lookup"><span data-stu-id="9f87a-111">Using the F12 tool bar to diagnose performance in SharePoint Online</span></span>
<span data-ttu-id="9f87a-112"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="9f87a-112"></span></span>

<span data-ttu-id="9f87a-p102">이 문서에서는 Internet Explorer 11을 사용합니다. 다른 브라우저의 F12 개발자 도구 버전은 약간 다르게 보일 수 있지만 유사한 기능을 제공합니다. F12 개발자 도구에 대한 자세한 내용은 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9f87a-p102">In this article we use Internet Explorer 11. Versions of the F12 developer tools on other browsers have similar features though they may look slightly different. For information on the F12 developer tools, see:</span></span>
  
- [<span data-ttu-id="9f87a-116">F12 도구의 새로운 기능</span><span class="sxs-lookup"><span data-stu-id="9f87a-116">What's new in F12 Tools</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=522545)
    
- [<span data-ttu-id="9f87a-117">F12 개발자 도구를 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="9f87a-117">Using the F12 developer tools</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=522546)
    
<span data-ttu-id="9f87a-118">개발자 도구를 불러오려면 **F12** 키를 누르고 Wi-Fi 아이콘을 클릭합니다. 
</span><span class="sxs-lookup"><span data-stu-id="9f87a-118">To bring up the developer tools press **F12** and then click the Wi-Fi icon:</span></span> 
  
![F12 개발자 도구 Wi-Fi 아이콘 스크린샷](media/27acacbb-5688-459a-aa2f-5c8c5f17b76e.png)
  
<span data-ttu-id="9f87a-p103">**네트워크** 탭에서 페이지를 로드하기 위한 녹색 재생 단추를 누릅니다. 이 도구는 요청한 페이지를 표시하기 위해 브라우저가 요구하는 모든 파일을 반환합니다. 다음 스크린샷에 이러한 목록이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f87a-p103">On the **Network** tab, press the green play button to load a page. The tool returns all of the files that the browser requests in order to get the page you asked for. The following screen shot shows one such list.</span></span> 
  
![페이지 요청을 통해 반환되는 파일 목록의 스크린샷](media/247a9422-76da-4b0c-bed3-ce77b05e4560.png)
  
<span data-ttu-id="9f87a-124">또한 이 스크린샷에 나와 있는 것처럼 오른쪽에서는 파일의 다운로드 시간을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f87a-124">You can also see the download times of the files on the right side as shown in this screen shot.</span></span>
  
![SharePoint에서 요청된 페이지를 로드하는 데 걸리는 시간을 보여 주는 다이어그램](media/d71ad1fa-9018-4fae-82eb-c1838e7db0ff.png)
  
<span data-ttu-id="9f87a-p104">이를 통해 파일 로드 시간을 확인할 수 있습니다. 브라우저에서 페이지를 렌더링할 준비가 되면 녹색 선이 표시됩니다. 따라서 사이트에서 페이지 로드를 느리게 하는 다양한 파일을 빠르게 확인할 수 있습니다.

</span><span class="sxs-lookup"><span data-stu-id="9f87a-p104">This gives you a visual representation of how long the file took to load. The green line represents when the page is ready to be rendered by the browser. This can give you a quick view of the different files that might be causing slow page loads on your site.</span></span>
  
## <a name="setting-up-a-non-customized-baseline-for-sharepoint-online"></a><span data-ttu-id="9f87a-129">SharePoint Online에 대 한 사용자 지정 되지 않은 초기 계획을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9f87a-129">Setting up a non-customized baseline for SharePoint Online</span></span>
<span data-ttu-id="9f87a-130"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="9f87a-130"></span></span>

<span data-ttu-id="9f87a-p105">사이트의 성능에 대 한 약점 정보를 확인 하려면 SharePoint Online에서 완전히 out (영문)의-기본 사이트 모음을 설정 하는 가장 좋은 방법은 합니다. 이러한 방식으로 페이지에서 사용자 지정 내용이 없는 얻을 것으로 사이트의 모든 다양 한 측면을 비교할 수 있습니다. 비즈니스 홈페이지에 대 한 OneDrive는 모든 사용자 지정 내용을 가능성이 있는 별도 사이트 모음의 좋은 예입니다.</span><span class="sxs-lookup"><span data-stu-id="9f87a-p105">The best way to determine your site's performance weak points is to set up a completely out-of-the-box site collection in SharePoint Online. This way you can compare all the various aspects of your site with what you would get with no customization on the page. The OneDrive for Business home page is a good example of a separate site collection that is unlikely to have any customizations.</span></span>
  
## <a name="viewing-sharepoint-response-header-information"></a><span data-ttu-id="9f87a-134">SharePoint 응답 헤더 정보 보기</span><span class="sxs-lookup"><span data-stu-id="9f87a-134">Viewing SharePoint response header information</span></span>
<span data-ttu-id="9f87a-135"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="9f87a-135"></span></span>

<span data-ttu-id="9f87a-p106">SharePoint Online 및 SharePoint Server 2013에서는 각 파일에 대한 응답 헤더에서 브라우저로 다시 전송되는 정보에 액세스할 수 있습니다. 성능 문제를 진단하는 데 가장 유용한 두 가지 값은 SPRequestDuration과 X SharePointHealthScore입니다.</span><span class="sxs-lookup"><span data-stu-id="9f87a-p106">In SharePoint Online and SharePoint Server 2013 you can access the information that is sent back to the browser in the response header for each file. The two most useful values for diagnosing performance issues are SPRequestDuration and X-SharePointHealthScore:</span></span>
  
- <span data-ttu-id="9f87a-138">**SPRequestDuration**</span><span class="sxs-lookup"><span data-stu-id="9f87a-138">**SPRequestDuration**</span></span>
    
    <span data-ttu-id="9f87a-p107">서버에서 요청을 처리하는 데 걸린 시간입니다. 이 값은 요청이 많은 작업인지, 그리고 리소스를 많이 사용하는지를 파악하는 데 도움이 될 수 있습니다. 이 값은 서버가 페이지를 제공하기 위해 수행하는 작업의 양을 이해하는 데 가장 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="9f87a-p107">This is the amount of time that the request took on the server to be processed. This can help determine if the request is very heavy and resource intensive. This is the best insight you have into how much work the server is doing to serve the page.</span></span>
    
- <span data-ttu-id="9f87a-142">**X-SharePointHealthScore**</span><span class="sxs-lookup"><span data-stu-id="9f87a-142">**X-SharePointHealthScore**</span></span>
    
    <span data-ttu-id="9f87a-p108">이 서버 또는 SharePoint 인스턴스가 실행 되는 CPU 사용률을 나타냅니다. 이 번호 범위는 0에서 10 여기서 0 나타내고 서버를 사용 하지 않을 10 나타냅니다 서버 사용량이 매우 많습니다. 지속적으로 9 또는 10 인 상태 점수입니다 서버와 지속적인 성능 문제를 나타낼 수 있습니다. 다른 번호 예상된 범위 내에서 작동 하는 해당 서버를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9f87a-p108">This indicates the utilization of the server, or CPU, on which your SharePoint instance runs. This number ranges from 0 to 10 where 0 indicates the server is idle and 10 indicates the server is very busy. A HealthScore that is consistently 9 or 10 might indicate an ongoing performance issue with the server. Any other number indicates that server is operating within the expected range.</span></span>
    
 <span data-ttu-id="9f87a-147">**SharePoint 응답 헤더 정보를 보려면**</span><span class="sxs-lookup"><span data-stu-id="9f87a-147">**To view SharePoint response header information**</span></span>
  
1. <span data-ttu-id="9f87a-p109">F12 도구를 설치 했는지 확인 합니다. 다운로드 하 고 이러한 도구를 설치에 대 한 자세한 내용은 [F12 도구의 새로운 란](https://go.microsoft.com/fwlink/p/?LinkId=522545)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="9f87a-p109">Ensure that you have the F12 tools installed. For more information on downloading and installing these tools, see [What's new in F12 tools](https://go.microsoft.com/fwlink/p/?LinkId=522545).</span></span>
    
2. <span data-ttu-id="9f87a-150">F12 도구의 **네트워크** 탭에서 녹색 재생 단추를 눌러 페이지를 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="9f87a-150">In the F12 tools, on the **Network** tab, press the green play button to load a page.</span></span> 
    
3. <span data-ttu-id="9f87a-151">이 도구가 반환하는 .aspx 파일 하나와 **세부 정보**를 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9f87a-151">Click one of the .aspx files returned by the tool and then click **DETAILS**.</span></span> 
    
    ![응답 헤더의 세부 정보 표시](media/1f8a044a-caf8-4613-be2b-7e064141ac8a.png)
  
4. <span data-ttu-id="9f87a-153">**응답 헤더**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9f87a-153">Click **Response headers**.</span></span> 
    
    ![응답 헤더의 URL을 보여 주는 다이어그램](media/efc7076e-447e-447e-882a-ae3aa721e2c3.png)
  
## <a name="whats-causing-performance-issues-in-sharepoint-online"></a><span data-ttu-id="9f87a-155">SharePoint Online에서 성능 문제를 일으키는 원인은 무엇입니까?</span><span class="sxs-lookup"><span data-stu-id="9f87a-155">What's causing performance issues in SharePoint Online?</span></span>
<span data-ttu-id="9f87a-156"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="9f87a-156"></span></span>

<span data-ttu-id="9f87a-p110">[SharePoint Online에 대 한 탐색 옵션](navigation-options-for-sharepoint-online.md) 문서 SPRequestDuration 값을 사용 하 여 복잡 한 구조적 탐색 페이지를 서버에서 처리 하는 데 시간이 오래 걸릴 인해 발생 된 되었는지 확인 하려면 예를 보여줍니다. 사용자 지정) (없이 기본 사이트에 대 한 값을 수행 하 여 지정 된 모든 파일을 로드 하는데 시간이 오래 수행 됨 하는 경우 확인할 수 있습니다. [SharePoint Online에 대 한 탐색 옵션](navigation-options-for-sharepoint-online.md) 에서 사용 되는 예제에는 주.aspx 파일입니다. 해당 파일 대부분의 페이지를 로드 하 여 실행 되는 ASP.NET 코드를 포함 합니다. 사용할 사이트 서식 파일에 따라 때문일 수 있습니다 start.aspx, home.aspx, default.aspx, 또는 다른 이름 홈 페이지를 사용자 지정 하는 경우. 이 번호는 초기 사이트 보다 훨씬 더 높은, 인해 성능 문제가 발생 하는 페이지의 진행 상황 복잡 한 무엇 인가 발생 한다는 좋은 상태가 표시는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="9f87a-p110">The article [Navigation options for SharePoint Online](navigation-options-for-sharepoint-online.md) shows an example of using the SPRequestDuration value to determine that the complicated structural navigation was causing the page to take a long time to process on the server. By taking a value for a baseline site (without customization), it is possible to determine if any given file is taking a long time to load. The example used in [Navigation options for SharePoint Online](navigation-options-for-sharepoint-online.md) is the main .aspx file. That file contains most of the ASP.NET code that runs for your page load. Depending on the site template you use, this could be start.aspx, home.aspx, default.aspx, or another name if you customize the home page. If this number is considerably higher than your baseline site, then it's a good indication that there is something complex going on in your page that is causing performance issues.</span></span> 
  
<span data-ttu-id="9f87a-p111">사이트에 국한된 문제임이 확인될 경우 성능 문제의 원인을 찾기 위해 권장되는 방법은 페이지 사용자 지정과 같은 가능한 원인을 모두 제거한 다음 하나씩 사이트에 다시 추가하는 것입니다. 페이지의 성능이 제대로 나타날 때까지 사용자 지정을 제거한 후에는 하나씩 다시 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f87a-p111">Once you have identified that an issue specific to your site, the recommended way to figure out what is causing poor performance is to eliminate all of the possible causes, like page customizations, and then add them back to the site one by one. Once you have removed enough customizations that the page is performing well, you can then add back specific customizations one by one.</span></span>
  
<span data-ttu-id="9f87a-p112">예를 들어 매우 복잡한 탐색 시도를 수행한 경우 하위 사이트를 표시하지 않도록 탐색을 변경한 다음, 개발자 도구를 확인하여 차이가 있는지 알아봅니다. 또는 대량의 콘텐츠 롤업이 있는 경우 페이지에서 제거한 후 성능이 개선되었는지 확인합니다. 가능한 모든 원인을 제거한 후 한 번에 하나씩 추가하면 가장 큰 문제를 발생시킨 기능을 쉽게 파악하고 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f87a-p112">For example, if you have a very complex navigation try changing the navigation to not show sub-sites then check the developer tools to see if this makes a difference. Or if you have a large amount of content roll-ups try removing them from your page and see if this improves things. If you eliminate all of the possible causes and add them back in one at a time, you can easily identify which features are the biggest problem and then work towards a solution.</span></span>
  

