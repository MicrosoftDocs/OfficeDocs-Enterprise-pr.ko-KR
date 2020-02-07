---
title: SharePoint Online의 성능 문제 진단
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 7/9/2019
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 3c364f9e-b9f6-4da4-a792-c8e8c8cd2e86
description: 이 문서에서는 Internet Explorer 개발자 도구를 사용 하 여 SharePoint Online 사이트의 일반적인 문제를 진단할 수 있는 방법을 보여 줍니다.
ms.openlocfilehash: 6061af0f3fa032274f03d0d531b42d1f8db05b70
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41840435"
---
# <a name="diagnosing-performance-issues-with-sharepoint-online"></a><span data-ttu-id="2b5e1-103">SharePoint Online의 성능 문제 진단</span><span class="sxs-lookup"><span data-stu-id="2b5e1-103">Diagnosing performance issues with SharePoint Online</span></span>

<span data-ttu-id="2b5e1-104">이 문서에서는 Internet Explorer 개발자 도구를 사용 하 여 SharePoint Online 사이트의 일반적인 문제를 진단할 수 있는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2b5e1-104">This article shows you how you can diagnose common issues with your SharePoint Online site using Internet Explorer developer tools.</span></span>
  
<span data-ttu-id="2b5e1-105">SharePoint Online 사이트의 페이지에서 사용자 지정 내용에 대 한 성능 문제가 발생 하는 것을 확인할 수 있는 세 가지 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5e1-105">There are three different ways that you can identify that a page on a SharePoint Online site has a performance problem with the customizations.</span></span>
  
- <span data-ttu-id="2b5e1-106">F12 도구 모음 네트워크 모니터</span><span class="sxs-lookup"><span data-stu-id="2b5e1-106">The F12 tool bar network monitor</span></span>

- <span data-ttu-id="2b5e1-107">사용자 지정 하지 않은 기준과 비교</span><span class="sxs-lookup"><span data-stu-id="2b5e1-107">Comparison to a non-customized baseline</span></span>

- <span data-ttu-id="2b5e1-108">SharePoint Online 응답 헤더 메트릭</span><span class="sxs-lookup"><span data-stu-id="2b5e1-108">SharePoint Online response header metrics</span></span>

<span data-ttu-id="2b5e1-109">이 항목에서는 이러한 각 방법을 사용 하 여 성능 문제를 진단 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5e1-109">This topic describes how to use each of these methods to diagnose performance issues.</span></span> <span data-ttu-id="2b5e1-110">문제의 원인을 파악 한 후에 https://aka.ms/tune는 찾을 수 있는 SharePoint 성능 향상에 대 한 문서를 사용 하 여 솔루션으로 작업할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5e1-110">Once you've figured out the cause of the problem, you can work toward a solution using the articles about improving SharePoint performance that you can find on https://aka.ms/tune.</span></span>
  
## <a name="using-the-f12-tool-bar-to-diagnose-performance-in-sharepoint-online"></a><span data-ttu-id="2b5e1-111">F12 도구 모음을 사용 하 여 SharePoint Online의 성능 진단</span><span class="sxs-lookup"><span data-stu-id="2b5e1-111">Using the F12 tool bar to diagnose performance in SharePoint Online</span></span>
<span data-ttu-id="2b5e1-112"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="2b5e1-112"><a name="F12ToolInfo"> </a></span></span>

<span data-ttu-id="2b5e1-113">이 문서에서는 Internet Explorer 11을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5e1-113">In this article we use Internet Explorer 11.</span></span> <span data-ttu-id="2b5e1-114">다른 브라우저의 F12 개발자 도구 버전은 약간 다르게 보일 수 있지만 비슷한 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5e1-114">Versions of the F12 developer tools on other browsers have similar features though they may look slightly different.</span></span> <span data-ttu-id="2b5e1-115">F12 개발자 도구에 대 한 자세한 내용은 다음 항목을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="2b5e1-115">For information on the F12 developer tools, see:</span></span>
  
- [<span data-ttu-id="2b5e1-116">F12 도구의 새로운 기능</span><span class="sxs-lookup"><span data-stu-id="2b5e1-116">What's new in F12 Tools</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=522545)

- [<span data-ttu-id="2b5e1-117">F12 개발자 도구 사용</span><span class="sxs-lookup"><span data-stu-id="2b5e1-117">Using the F12 developer tools</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=522546)

<span data-ttu-id="2b5e1-118">개발자 도구를 가져오려면 **F12** 키를 누르고 wi-fi 아이콘을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5e1-118">To bring up the developer tools press **F12** and then click the Wi-Fi icon:</span></span>
  
![F12 개발자 도구 Wi-Fi 아이콘 스크린샷](media/27acacbb-5688-459a-aa2f-5c8c5f17b76e.png)
  
<span data-ttu-id="2b5e1-120">**네트워크** 탭에서 녹색 재생 단추를 눌러 페이지를 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5e1-120">On the **Network** tab, press the green play button to load a page.</span></span> <span data-ttu-id="2b5e1-121">이 도구는 요청한 페이지를 가져오기 위해 브라우저에서 요청 하는 모든 파일을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5e1-121">The tool returns all of the files that the browser requests in order to get the page you asked for.</span></span> <span data-ttu-id="2b5e1-122">다음 스크린샷은 이러한 목록 중 하나를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2b5e1-122">The following screen shot shows one such list.</span></span>
  
![페이지 요청을 통해 반환되는 파일 목록의 스크린샷](media/247a9422-76da-4b0c-bed3-ce77b05e4560.png)
  
<span data-ttu-id="2b5e1-124">또한이 스크린샷에 표시 된 것 처럼 오른쪽에 있는 파일의 다운로드 시간도 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5e1-124">You can also see the download times of the files on the right side as shown in this screen shot.</span></span>
  
![SharePoint에서 요청된 페이지를 로드하는 데 걸리는 시간을 보여 주는 다이어그램](media/d71ad1fa-9018-4fae-82eb-c1838e7db0ff.png)
  
<span data-ttu-id="2b5e1-126">이를 통해 파일을 로드 하는 데 걸린 시간을 시각적으로 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5e1-126">This gives you a visual representation of how long the file took to load.</span></span> <span data-ttu-id="2b5e1-127">녹색 줄은 페이지를 브라우저에서 렌더링할 준비가 된 시기를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2b5e1-127">The green line represents when the page is ready to be rendered by the browser.</span></span> <span data-ttu-id="2b5e1-128">이를 통해 사이트에서 느린 페이지 로드를 유발할 수 있는 다양 한 파일을 빠르게 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5e1-128">This can give you a quick view of the different files that might be causing slow page loads on your site.</span></span>
  
## <a name="setting-up-a-non-customized-baseline-for-sharepoint-online"></a><span data-ttu-id="2b5e1-129">SharePoint Online에 대해 사용자 지정 되지 않은 기준 설정</span><span class="sxs-lookup"><span data-stu-id="2b5e1-129">Setting up a non-customized baseline for SharePoint Online</span></span>
<span data-ttu-id="2b5e1-130"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="2b5e1-130"><a name="F12ToolInfo"> </a></span></span>

<span data-ttu-id="2b5e1-131">사이트의 성능에 취약 한 지점을 확인 하는 가장 좋은 방법은 SharePoint Online에서 완전히 기본 사이트 모음을 설정 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="2b5e1-131">The best way to determine your site's performance weak points is to set up a completely out-of-the-box site collection in SharePoint Online.</span></span> <span data-ttu-id="2b5e1-132">이렇게 하면 페이지에서 사용자 지정 하지 않은 경우와 같이 사이트의 다양 한 측면을 비교할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5e1-132">This way you can compare all the various aspects of your site with what you would get with no customization on the page.</span></span> <span data-ttu-id="2b5e1-133">비즈니스용 OneDrive 홈 페이지는 사용자 지정 내용이 있을 가능성이 없는 별도의 사이트 모음에 대 한 좋은 예입니다.</span><span class="sxs-lookup"><span data-stu-id="2b5e1-133">The OneDrive for Business home page is a good example of a separate site collection that is unlikely to have any customizations.</span></span>
  
## <a name="viewing-sharepoint-response-header-information"></a><span data-ttu-id="2b5e1-134">SharePoint 응답 헤더 정보 보기</span><span class="sxs-lookup"><span data-stu-id="2b5e1-134">Viewing SharePoint response header information</span></span>
<span data-ttu-id="2b5e1-135"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="2b5e1-135"><a name="F12ToolInfo"> </a></span></span>

<span data-ttu-id="2b5e1-136">SharePoint Online에서는 각 파일의 응답 헤더에 브라우저로 다시 전송 되는 정보에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5e1-136">In SharePoint Online, you can access the information that is sent back to the browser in the response header for each file.</span></span> <span data-ttu-id="2b5e1-137">성능 문제를 진단 하는 데 가장 유용한 값은 **Sprequestduration**이며, 서버에서 요청을 처리 하는 데 걸린 시간이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b5e1-137">The most useful value for diagnosing performance issues is **SPRequestDuration**, which displays the amount of time that the request took on the server to be processed.</span></span> <span data-ttu-id="2b5e1-138">이를 통해 요청이 매우 많고 리소스가 많이 필요한 지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5e1-138">This can help determine if the request is very heavy and resource intensive.</span></span> <span data-ttu-id="2b5e1-139">이는 서버가 페이지를 처리 하기 위해 수행 하는 작업의 정도를 파악 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="2b5e1-139">This is the best insight you have into how much work the server is doing to serve the page.</span></span>

### <a name="to-view-sharepoint-response-header-information"></a><span data-ttu-id="2b5e1-140">SharePoint 응답 헤더 정보를 보려면</span><span class="sxs-lookup"><span data-stu-id="2b5e1-140">To view SharePoint response header information</span></span>
  
1. <span data-ttu-id="2b5e1-141">F12 도구를 설치 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5e1-141">Ensure that you have the F12 tools installed.</span></span> <span data-ttu-id="2b5e1-142">이러한 도구를 다운로드 하 고 설치 하는 방법에 대 한 자세한 내용은 [F12 도구의 새로운 기능](https://go.microsoft.com/fwlink/p/?LinkId=522545)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="2b5e1-142">For more information on downloading and installing these tools, see [What's new in F12 tools](https://go.microsoft.com/fwlink/p/?LinkId=522545).</span></span>

2. <span data-ttu-id="2b5e1-143">F12 도구의 **네트워크** 탭에서 녹색 재생 단추를 클릭 하 여 페이지를 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5e1-143">In the F12 tools, on the **Network** tab, press the green play button to load a page.</span></span>

3. <span data-ttu-id="2b5e1-144">도구에서 반환 된 .aspx 파일 중 하나를 클릭 한 다음 **세부 정보**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5e1-144">Click one of the .aspx files returned by the tool and then click **DETAILS**.</span></span>

    ![응답 헤더의 세부 정보 표시](media/1f8a044a-caf8-4613-be2b-7e064141ac8a.png)
  
4. <span data-ttu-id="2b5e1-146">**응답 헤더**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5e1-146">Click **Response headers**.</span></span>

    ![응답 헤더의 URL을 보여 주는 다이어그램](media/efc7076e-447e-447e-882a-ae3aa721e2c3.png)
  
## <a name="whats-causing-performance-issues-in-sharepoint-online"></a><span data-ttu-id="2b5e1-148">SharePoint Online에서 성능 문제가 발생 하는 이유는 무엇 인가요?</span><span class="sxs-lookup"><span data-stu-id="2b5e1-148">What's causing performance issues in SharePoint Online?</span></span>
<span data-ttu-id="2b5e1-149"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="2b5e1-149"><a name="F12ToolInfo"> </a></span></span>

<span data-ttu-id="2b5e1-150">[SharePoint Online의 탐색 옵션](navigation-options-for-sharepoint-online.md) 은 SPRequestDuration 값을 사용 하 여 복잡 한 구조적 탐색로 인해 서버에서 처리 하는 데 시간이 오래 걸리는 지를 확인 하는 예제를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2b5e1-150">The article [Navigation options for SharePoint Online](navigation-options-for-sharepoint-online.md) shows an example of using the SPRequestDuration value to determine that the complicated structural navigation was causing the page to take a long time to process on the server.</span></span> <span data-ttu-id="2b5e1-151">기본 사이트 (사용자 지정 하지 않음)에 대 한 값을 사용 하 여 특정 파일을 로드 하는 데 오래 걸리는 시간을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5e1-151">By taking a value for a baseline site (without customization), it is possible to determine if any given file is taking a long time to load.</span></span> <span data-ttu-id="2b5e1-152">[SharePoint Online의 탐색 옵션](navigation-options-for-sharepoint-online.md) 에 사용 되는 예제는 기본 .aspx 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="2b5e1-152">The example used in [Navigation options for SharePoint Online](navigation-options-for-sharepoint-online.md) is the main .aspx file.</span></span> <span data-ttu-id="2b5e1-153">이 파일에는 페이지를 로드 하기 위해 실행 되는 대부분의 ASP.NET 코드가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5e1-153">That file contains most of the ASP.NET code that runs for your page load.</span></span> <span data-ttu-id="2b5e1-154">사용 하는 사이트 서식 파일에 따라 .aspx, home.aspx, default.aspx 또는 홈 페이지를 사용자 지정 하는 경우 다른 이름을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5e1-154">Depending on the site template you use, this could be start.aspx, home.aspx, default.aspx, or another name if you customize the home page.</span></span> <span data-ttu-id="2b5e1-155">이 수가 기본 사이트 보다 훨씬 높으면 페이지에서 성능 문제가 발생 하는 작업이 복잡해 지는 것을 나타내는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5e1-155">If this number is considerably higher than your baseline site, then it's a good indication that there is something complex going on in your page that is causing performance issues.</span></span>
  
<span data-ttu-id="2b5e1-156">사이트 관련 문제를 파악 한 후에는 페이지 사용자 지정 같은 모든 가능한 원인을 제거한 다음 사이트에 하나씩 다시 추가 하는 것이 가장 좋은 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="2b5e1-156">Once you have identified that an issue specific to your site, the recommended way to figure out what is causing poor performance is to eliminate all of the possible causes, like page customizations, and then add them back to the site one by one.</span></span> <span data-ttu-id="2b5e1-157">페이지에서 제대로 작동 하는 사용자 지정 내용을 충분히 제거한 후에는 특정 사용자 지정 내용을 하나씩 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5e1-157">Once you have removed enough customizations that the page is performing well, you can then add back specific customizations one by one.</span></span>
  
<span data-ttu-id="2b5e1-158">예를 들어 탐색이 매우 복잡 한 경우 하위 사이트가 표시 되지 않도록 탐색을 변경 하 고 개발자 도구를 확인 하 여이로 인해 차이가 있는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5e1-158">For example, if you have a very complex navigation try changing the navigation to not show sub-sites then check the developer tools to see if this makes a difference.</span></span> <span data-ttu-id="2b5e1-159">또는 콘텐츠 롤업을 많이 사용 하는 경우에는 페이지에서이를 제거 하 고 성능이 향상 되는지 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="2b5e1-159">Or if you have a large amount of content roll-ups try removing them from your page and see if this improves things.</span></span> <span data-ttu-id="2b5e1-160">가능한 모든 원인을 제거한 후 한 번에 하나씩 다시 추가 하면 가장 큰 문제가 되는 기능을 쉽게 식별 한 다음 솔루션으로 작업할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5e1-160">If you eliminate all of the possible causes and add them back in one at a time, you can easily identify which features are the biggest problem and then work towards a solution.</span></span>
