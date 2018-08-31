---
title: 질문과 대답 네트워킹 office 365 비디오
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/13/2016
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 2bed67a1-4052-49ff-a4ce-b7e6530eb98e
description: Office 365 비디오 리포지토리와 스트리밍 서비스를 보다 손쉽게 저장 하 고 조직 내에서 비디오를 스트리밍합니다. Office 365 비디오;에 대 한 유용한 정보 많이 이 네트워킹 FAQ는 암호화 및 서비스 콘텐츠 배달 네트워크 (Cdn)를 활용 하는 방법을 계획 하는 대역폭 주위 가장 일반적인 질문에 대답 하도록 설계 되었습니다.
ms.openlocfilehash: bea9838277b5752e4c9905162c0e8525e8aded04
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541979"
---
# <a name="office-365-video-networking-frequently-asked-questions"></a><span data-ttu-id="0e248-104">질문과 대답 네트워킹 office 365 비디오</span><span class="sxs-lookup"><span data-stu-id="0e248-104">Office 365 Video networking Frequently Asked Questions</span></span>

<span data-ttu-id="0e248-p102">Office 365 비디오 리포지토리와 스트리밍 서비스를 보다 손쉽게 저장 하 고 조직 내에서 비디오를 스트리밍합니다. [Office 365 비디오에 대 한 정보](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50)뛰어난; 많이 이 네트워킹 FAQ는 암호화 및 서비스 [콘텐츠 배달 네트워크 (Cdn)를](https://support.office.com/article/Content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f)활용 하는 방법을 계획 하는 대역폭 주위 가장 일반적인 질문에 대답 하도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0e248-p102">The Office 365 Video repository and streaming services make storing and streaming videos within your organization simple. There's a lot of great [information about Office 365 Video](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50); this networking FAQ is designed to answer the most common questions around bandwidth planning, encryption, and how the service leverages [content delivery networks (CDNs)](https://support.office.com/article/Content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f).</span></span>
  
<span data-ttu-id="0e248-107">이미에 비디오를 업로드할 때 수행 하는 작업의 철저 하 게 이해할 수 있습니다 또는 재생,이 비디오에 대 한 정보를 포함 하지는 배치 함께 [Office 365 비디오에 업로드 하는 경우 비디오 파일을 수행 하는 작업](https://www.youtube.com/watch?v=HXSZ0jYBKlM)입니다.</span><span class="sxs-lookup"><span data-stu-id="0e248-107">If you don't already have a thorough understanding of what happens when a video is uploaded or played back, have a look at this video we put together, [What happens to a video file when uploaded to Office 365 Video](https://www.youtube.com/watch?v=HXSZ0jYBKlM).</span></span>
  
## <a name="what-are-the-office-365-video-bandwidth-requirements"></a><span data-ttu-id="0e248-108">Office 365 비디오 대역폭 요구 사항은 무엇입니까?</span><span class="sxs-lookup"><span data-stu-id="0e248-108">What are the Office 365 Video bandwidth requirements?</span></span>

<span data-ttu-id="0e248-p103">수많은 [지원 되는 비디오 형식](https://support.office.com/article/dd1af01c-fd8e-4640-b17b-93ee02b9b817) Office 365에 업로드 될 수 있습니다. 다음 각 비디오 파일 재생에 대 한 여러 다른 비디오 품질와 표준 형식으로 인코딩됩니다. Office 365 비디오 스트리밍 비디오 플레이어의 크기와 사용 가능한 네트워크 대역폭에 따라 최상의 비디오 재생 품질을 선택 하는 환경에 적합 한 비트 전송률을 사용 합니다. 이 작업을 수행 하려면 플레이어 처음 가장 낮은 재생 품질을 요청 합니다. 다음 서비스는 비디오 플레이어를 2 초 비디오 세그먼트를 보낼 시작 합니다. 플레이어 수를 기반으로 각 세그먼트 배달 되는 얼마나 빨리 높거나 낮게 재생 품질을 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e248-p103">There are a numerous [supported video formats](https://support.office.com/article/dd1af01c-fd8e-4640-b17b-93ee02b9b817) that can be uploaded to Office 365. Each video file is then encoded to a standard format with several different video qualities for playback. Office 365 Video uses adaptive bitrate streaming to select the best video playback quality based on the available network bandwidth and size of the video player. To do this, the player initially requests the lowest playback quality. The service then begins sending 2-second video segments to the video player. The player can then request higher or lower playback quality based on how quickly each segment is delivered.</span></span>
  
<span data-ttu-id="0e248-p104">환경에 적합 한 비트 전송률 스트리밍이 작업을 수행 모든 백그라운드에서 최소한의 중단 또는 버퍼링와 비디오를 재생 하는 동안 합니다. 비디오 재생 하는 동안 비디오 플레이어를 수동으로 특정 비디오 재생 품질을 선택 하는 자동 재생 품질을 재정의 하려면 뷰어를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e248-p104">The adaptive bitrate streaming does all this in the background while the video plays with the least amount of disruption or buffering. During video playback, the video player allows the viewer to manually override the automatic playback quality, to select a specific video playback quality.</span></span>
  
<span data-ttu-id="0e248-p105">빠른 테이블에서는 각 비디오 재생 품질에 대 한 네트워크 요구 사항에 설명 하는 다음과 같습니다. 비디오를 재생 하는 데 필요한 사용자 당 최소 대역폭은 802 Kbps입니다.</span><span class="sxs-lookup"><span data-stu-id="0e248-p105">Here's a quick table that outlines the network requirements for each of the video playback qualities. The minimum bandwidth per person needed to play a video is 802Kbps.</span></span>
  
|||
|:-----|:-----|
|<span data-ttu-id="0e248-119">**재생 품질**</span><span class="sxs-lookup"><span data-stu-id="0e248-119">**Playback Quality**</span></span> <br/> |<span data-ttu-id="0e248-120">**네트워크 속도**</span><span class="sxs-lookup"><span data-stu-id="0e248-120">**Network Speed**</span></span> <br/> |
|<span data-ttu-id="0e248-121">288 p</span><span class="sxs-lookup"><span data-stu-id="0e248-121">288p</span></span>  <br/> |<span data-ttu-id="0e248-122">802 k b p s</span><span class="sxs-lookup"><span data-stu-id="0e248-122">802Kbps</span></span>  <br/> |
|<span data-ttu-id="0e248-123">360 p</span><span class="sxs-lookup"><span data-stu-id="0e248-123">360p</span></span>  <br/> |<span data-ttu-id="0e248-124">1.2 Mbps</span><span class="sxs-lookup"><span data-stu-id="0e248-124">1.2 Mbps</span></span>  <br/> |
|<span data-ttu-id="0e248-125">576 p</span><span class="sxs-lookup"><span data-stu-id="0e248-125">576p</span></span>  <br/> |<span data-ttu-id="0e248-126">2.5 Mbps</span><span class="sxs-lookup"><span data-stu-id="0e248-126">2.5 Mbps</span></span>  <br/> |
|<span data-ttu-id="0e248-127">720p</span><span class="sxs-lookup"><span data-stu-id="0e248-127">720p</span></span>  <br/> |<span data-ttu-id="0e248-128">3.8 Mbps</span><span class="sxs-lookup"><span data-stu-id="0e248-128">3.8 Mbps</span></span>  <br/> |

<span data-ttu-id="0e248-129">([맨위로 이동](office-365-video-networking-faq.md))</span><span class="sxs-lookup"><span data-stu-id="0e248-129">([Back to top](office-365-video-networking-faq.md))</span></span>
  
## <a name="how-do-cdns-help-video-playback"></a><span data-ttu-id="0e248-130">Cdn 비디오 재생을 통해 방법을</span><span class="sxs-lookup"><span data-stu-id="0e248-130">How do CDNs help video playback?</span></span>

<span data-ttu-id="0e248-p106">동일한 지리적 위치 내에서 같은 조직에서 여러 사용자는 동일한 비디오 스트리밍의 경우, Cdn 해당 지리적 영역에 더 가깝게 위치에 이러한 비디오의 복사본을 저장 합니다. 비디오, 저장 또는 가장 가까운 위치에 캐시 된 각 사용자 위치를 추가 하는 대신 자신에 게 가장 가까운 위치에서 비디오를 자리 비움으로 스트리밍합니다. Office 365 비디오 Azure Media 서비스를 사용 하 여 어떤 캐싱되 Azure Cdn에서 및 방법에 대 한 긴 관리. Azure 미디어 서비스 [Azure CDN 위치](https://azure.microsoft.com/documentation/articles/cdn-pop-locations/) 중 하나를 사용 하 여 비디오 조각 및 며칠에 대 한 매니페스트를 캐시 수 있습니다. 조직의 사용자에 게 계속 제공 되는 캐시 된 비디오를 시청 하는 경우 캐시 유지할 표시 됩니다. 며칠 비디오에 대 한 비디오 결국 없는 하나의 액세스 하는 경우 드롭 캐시에서 삭제할 수 있습니다. 다음 비디오를 시청 하 려 것은 다시 한번 캐시 시간 가장 가까운 CDN 위치에 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e248-p106">If several people from the same organization within the same geographic location are streaming the same video(s), CDNs will store a copy of these videos in a location closer to that geographic region. With the video stored, or cached at the closest location, each person streams the video from the location closest to them instead of a location further away. Office 365 Video uses Azure Media Services to manage what is cached in the Azure CDNs, and for how long. Azure Media Services can use any of the [Azure CDN locations](https://azure.microsoft.com/documentation/articles/cdn-pop-locations/) to cache video fragments and manifests for a few days. If people in your organization continue to watch the cached videos they'll stay in the cache. If no one accesses the video for several days, the video will eventually drop be dropped from the cache. The next time someone attempts to watch the video it's once again cached at the nearest CDN location.</span></span>
  
<span data-ttu-id="0e248-p107">콘텐츠 하는 동안 비디오를 시청 하려고 하는 모든 사람 근처 CDN 혜택 되 가깝게, 비디오 및 홉, 자리 비움 덜 대부분의 경우에 캐시 됩니다. 이렇게 하면 비디오 재생 속도를; 향상 됩니다. 그러나 비디오를 재생 하려면 네트워크 요구 사항은 바뀌지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0e248-p107">Everyone who attempts to watch the video while the content is cached at a nearby CDN benefits from the video being closer, and in most cases less hops, away. This improves video playback speed; however, it doesn't change the network requirement to play the video.</span></span>
  
> [!NOTE]
> <span data-ttu-id="0e248-140">중인에 도달 하면, 3 일에 도달 했습니다 전에 비디오 제거 될 수 있습니다를 사용해 용량 제한 등 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e248-140">There are some circumstances, such as our capacity limit being reached, where the video may be removed before the three days has been reached.</span></span>
  
<span data-ttu-id="0e248-141">([맨위로 이동](office-365-video-networking-faq.md))</span><span class="sxs-lookup"><span data-stu-id="0e248-141">([Back to top](office-365-video-networking-faq.md))</span></span>
  
## <a name="can-i-cache-the-videos-locally-for-faster-playback"></a><span data-ttu-id="0e248-142">더 빠른 재생에 대 한 로컬에서 제공 되는 비디오를 캐시할 수 있습니까?</span><span class="sxs-lookup"><span data-stu-id="0e248-142">Can I cache the videos locally for faster playback?</span></span>

<span data-ttu-id="0e248-p108">예입니다. Office 365 로컬 CDN 또는 캐싱 프록시를 사용 하 여 가져올 비디오 또는 다른 Office 365 콘텐츠 빠른 액세스에 대 한 로컬 네트워크에서 차단 되지 않습니다. 네트워크에서 로컬 캐싱 솔루션을 구현 하는 여러가지 방법으로, 가장 일반적인 방법은 콘텐츠를 로컬로 캐시 하는 프록시 솔루션을 사용 하는 것입니다. 프록시 또는 개인 CDN가 비디오 조각 및 매니페스트 캐시, 되 면 프록시 또는 개인 CDN를 통해 라우팅되며 이러한 파일에 대 한 이후 요청, 로컬 캐시에서 가져온를 업데이트 하 고 인터넷의 특정 위치에서 추출 되지 됩니다. 다음과 같은 솔루션의 계획 하는 동안 네트워크 대역폭, 용량 및 비디오 재생 동시성을 고려 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e248-p108">Yes. Office 365 won't prevent you from using a local CDN or a caching proxy to bring video or other Office 365 content into your local network for faster access. There are several ways to implement a local caching solution on your network, the most common method is to use a proxy solution that caches content locally. Once a proxy or private CDN has cached the video fragments and manifests, future requests for those files that route through the proxy or private CDN are pulled from the local cache and not pulled from an internet location. Consider network bandwidth, capacity, and video playback concurrency during the planning of a solution like this.</span></span>
  
<span data-ttu-id="0e248-148">([맨위로 이동](office-365-video-networking-faq.md))</span><span class="sxs-lookup"><span data-stu-id="0e248-148">([Back to top](office-365-video-networking-faq.md))</span></span>
  
## <a name="how-videos-are-encrypted-and-secured"></a><span data-ttu-id="0e248-149">방법 비디오 암호화 하 고 보호 하는?</span><span class="sxs-lookup"><span data-stu-id="0e248-149">How videos are encrypted and secured?</span></span>

<span data-ttu-id="0e248-p109">Office 365 비디오 안전 하 고 개인 데이터를 유지 하는 얼마나 중요 한지 알 수 있습니다. [Office 365 보안 센터](https://products.office.com/business/office-365-trust-center-cloud-computing-security) 개인정보 및 콘텐츠의 보안을 위한 노력을 설명합니다. 비디오 재생 속도 환경을 향상 시키면서;에 대 한 중요 한 그러나 보안 또는 속도 위해 exchange에서 정보 공개는 손상을 주지 않도록 합니다. 속도, 보안 및 개인정보 보호 방법 수용는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0e248-p109">Office 365 Video knows how important it is to keep your data secure and private. [The Office 365 Trust Center](https://products.office.com/business/office-365-trust-center-cloud-computing-security) describes our commitment to the privacy and security of your content. With video playback, speed is important for a good experience; however, we don't compromise your security or privacy in exchange for speed. Here's how we accommodate speed, security and privacy.</span></span>
  
<span data-ttu-id="0e248-p110">하면 사용자나 관리자가 조직에서 새로운 비디오 업로드, 해당 비디오 코드 변환 된, AES 128 암호화를 사용 하 여 암호화 하 고 Azure 미디어 서비스에 저장 됩니다. 즉,에서 전송 및 나머지 부분에서 제공 되는 비디오 암호화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0e248-p110">When you or someone in your organization uploads a new video, that video is transcoded, encrypted with AES-128 encryption, and stored in Azure Media Services. This means the videos are encrypted both in transit and at rest.</span></span>
  
<span data-ttu-id="0e248-156">새 비디오를 시청 하려고 하면 조직에서 다른 사용자 할 때은 다음이 단계를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="0e248-156">When someone in your organization attempts to watch a new video, they follow these steps:</span></span>
  
1. <span data-ttu-id="0e248-157">SharePoint Online 비디오를 볼 수 있는 권한이 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e248-157">Ask SharePoint Online if they have permission to view the video.</span></span>

2. <span data-ttu-id="0e248-158">SharePoint Online 사용 하 여 파일 사용 권한을 결정 사용자 비디오 시청 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e248-158">SharePoint Online uses the file permissions to determine if the person can watch the video.</span></span>

3. <span data-ttu-id="0e248-159">허용 되는 경우 SharePoint Online 토큰에서에서 검색 Azure에 비디오 플레이어를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e248-159">If they're allowed, SharePoint Online retrieves a token from Azure to give to the video player.</span></span>

4. <span data-ttu-id="0e248-160">다음 비디오 플레이어 토큰을 사용 하 여 Azure에서 암호 해독 키를 요청 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e248-160">The video player then uses the token to request the decryption key from Azure.</span></span>

5. <span data-ttu-id="0e248-161">손에서 암호 해독 키를 사용 하는 비디오 플레이어는 비디오 스트림 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e248-161">With the decryption key in hand, the video player is able to stream the video.</span></span>

![O365 비디오 재생](media/9d3c6e76-151d-48a3-a30e-ba8dd07db0b7.png)
  
<span data-ttu-id="0e248-163">([맨위로 이동](office-365-video-networking-faq.md))</span><span class="sxs-lookup"><span data-stu-id="0e248-163">([Back to top](office-365-video-networking-faq.md))</span></span>
  
## <a name="what-are-the-requirements-to-playback-office-365-video"></a><span data-ttu-id="0e248-164">Office 365 비디오 재생에 대 한 요구 사항은 무엇입니까?</span><span class="sxs-lookup"><span data-stu-id="0e248-164">What are the requirements to playback Office 365 Video?</span></span>

<span data-ttu-id="0e248-p111">Office 365 비디오 지원 되는 운영 체제 및 웹 브라우저는 [Office 365 시스템 요구 사항](https://support.office.com/article/Office-365-system-requirements-719254c0-2671-4648-9c84-c6a3d4f3be45)에서 SharePoint Online 요구와 동일 합니다. 운영 체제 및 웹에 따라 브라우저 구성 해야 비디오 플레이어의 특정 요구를 결정 합니다. [비디오 재생 요구 사항](https://support.office.com/article/ca1cc1a9-a615-46e1-b6a3-40dbd99939a6)에 대 한 자세한 내용은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0e248-p111">Office 365 Video supported operating systems and web browsers are the same as the SharePoint Online requirements in [Office 365 system requirements](https://support.office.com/article/Office-365-system-requirements-719254c0-2671-4648-9c84-c6a3d4f3be45). Depending on which operating system and web browser configuration you have will determine the specific needs of the video player. Here's more information on [video playback requirements](https://support.office.com/article/ca1cc1a9-a615-46e1-b6a3-40dbd99939a6).</span></span>
  
<span data-ttu-id="0e248-168">([맨위로 이동](office-365-video-networking-faq.md))</span><span class="sxs-lookup"><span data-stu-id="0e248-168">([Back to top](office-365-video-networking-faq.md))</span></span>
  
## <a name="i-cant-get-office-365-video-to-work-where-should-i-start"></a><span data-ttu-id="0e248-169">Office 365 비디오 작동 하려면 어디서부터 시작 해야를 가져올 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0e248-169">I can't get Office 365 video to work, where should I start?</span></span>

<span data-ttu-id="0e248-p112">Office 365 비디오에 대 한 연결 문제를 해결 네트워크, 사용자 ISP(s) 및 Office 365의 구성 문제를 해결 해야 합니다. 시작 하려면 먼저 서비스 상태 대시보드는입니다. 이 여부에 문제가 발생 하면 Office 365 비디오를 안내 합니다. 모든 보이면 다음과 같은 경우 하는데 도움이 되는 일부 추가 리소스 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0e248-p112">Troubleshooting connectivity to Office 365 Video involves troubleshooting your network, your ISP(s), and your configuration of Office 365. The first place to start is the service health dashboard. This will tell you of Office 365 Video is having a problem or not. If everything looks great there, here's some additional resources to help you.</span></span>
  
- <span data-ttu-id="0e248-174">[Office 365 비디오에 필요한 네트워크 끝점](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2)에 연결할 수 있는지 확인 하십시오.</span><span class="sxs-lookup"><span data-stu-id="0e248-174">Make sure you can connect to the [network endpoints required for Office 365 Video](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2).</span></span>

- <span data-ttu-id="0e248-175">이 [가이드의 문제를 해결 하는 Office 365 네트워크](https://support.office.com/article/Office-365-performance-tuning-and-troubleshooting-Admin-and-IT-Pro-1492cb94-bd62-43e6-b8d0-2a61ed88ebae)를 사용 하 여 네트워크 연결을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e248-175">Check your network connectivity using our [Office 365 network troubleshooting guide](https://support.office.com/article/Office-365-performance-tuning-and-troubleshooting-Admin-and-IT-Pro-1492cb94-bd62-43e6-b8d0-2a61ed88ebae).</span></span>

- <span data-ttu-id="0e248-176">이 [저속 네트워크에서 Office 365를 사용 하는 것에 대 한 모범 사례](https://support.office.com/article/Best-practices-for-using-Office-365-on-a-slow-network-fd16c8d2-4799-4c39-8fd7-045f06640166)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="0e248-176">See our [best practices for using Office 365 on a slow network](https://support.office.com/article/Best-practices-for-using-Office-365-on-a-slow-network-fd16c8d2-4799-4c39-8fd7-045f06640166).</span></span>

- <span data-ttu-id="0e248-177">[Office 365 비디오 구성에 대 한 도움말](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50)을 찾아보십시오.</span><span class="sxs-lookup"><span data-stu-id="0e248-177">Find [help about Office 365 Video configuration](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50).</span></span>

<span data-ttu-id="0e248-178">([맨위로 이동](office-365-video-networking-faq.md))</span><span class="sxs-lookup"><span data-stu-id="0e248-178">([Back to top](office-365-video-networking-faq.md))</span></span>
  
## <a name="office-365-video-resources"></a><span data-ttu-id="0e248-179">Office 365 비디오 리소스</span><span class="sxs-lookup"><span data-stu-id="0e248-179">Office 365 Video resources</span></span>

<span data-ttu-id="0e248-p113">항목을 평가 하 고는 질문에 응답 하는 경우 또는 대답 여전히 찾는 경우 알려주시면에 대 한 설명을 그대로 둡니다. 성공적으로 배포 하 고 Office 365 비디오를 사용할 수 있도록이 다른 리소스 중 일부는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0e248-p113">Rate the topic and leave a comment to let us know if we answered your questions or if you're still looking for answers. Here's a few of our other resources to help you successfully deploy and use Office 365 Video:</span></span>
  
<span data-ttu-id="0e248-182">[Office 365 비디오 구성에 대 한 도움말을 찾습니다](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50).</span><span class="sxs-lookup"><span data-stu-id="0e248-182">[Find help about Office 365 Video configuration](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50).</span></span>
  
[<span data-ttu-id="0e248-183">Office 365 비디오를 충족 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e248-183">Meet Office 365 Video</span></span>](https://support.office.com/article/Meet-Office-365-Video-ca1cc1a9-a615-46e1-b6a3-40dbd99939a6)
  
[<span data-ttu-id="0e248-184">만들기 및 Office 365 비디오에서 채널 관리</span><span class="sxs-lookup"><span data-stu-id="0e248-184">Create and manage a channel in Office 365 Video</span></span>](https://support.office.com/article/Create-and-manage-a-channel-in-Office-365-Video-1fede4cc-13c0-435a-b585-e7fbf1c83bb2)
  
[<span data-ttu-id="0e248-185">Office 365 비디오 포털 관리</span><span class="sxs-lookup"><span data-stu-id="0e248-185">Manage your Office 365 Video portal</span></span>](https://support.office.com/article/Manage-your-Office-365-Video-portal-c059465b-eba9-44e1-b8c7-8ff7793ff5da)
  
[<span data-ttu-id="0e248-186">Office 365 비디오에서 작동 하는 비디오 형식</span><span class="sxs-lookup"><span data-stu-id="0e248-186">Video formats that work in Office 365 Video</span></span>](https://support.office.com/article/Video-formats-that-work-in-Office-365-Video-dd1af01c-fd8e-4640-b17b-93ee02b9b817)
  
<span data-ttu-id="0e248-187">([맨위로 이동](office-365-video-networking-faq.md))</span><span class="sxs-lookup"><span data-stu-id="0e248-187">([Back to top](office-365-video-networking-faq.md))</span></span>
  
<span data-ttu-id="0e248-188">짧은 링크를 다시 사용할 수는 다음과 같습니다.[https://aka.ms/video365networkfaq](https://aka.ms/video365networkfaq)</span><span class="sxs-lookup"><span data-stu-id="0e248-188">Here's a short link you can use to come back: [https://aka.ms/video365networkfaq](https://aka.ms/video365networkfaq)</span></span>
