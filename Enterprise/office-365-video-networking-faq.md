---
title: Office 365 비디오 네트워킹에 대 한 질문과 대답
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 3/14/2019
audience: Admin
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
description: Office 365 비디오 리포지토리와 스트리밍 서비스는 조직 내에서 비디오를 간단 하 게 저장 하 고 스트리밍하는 작업을 수행 합니다. Office 365 비디오에 대 한 많은 유용한 정보가 있습니다. 이 네트워킹 FAQ는 대역폭 계획, 암호화 및 서비스가 CDNs (콘텐츠 배달 네트워크)를 활용 하는 방법에 대 한 가장 일반적인 질문에 대 한 답변을 제공 하도록 설계 되었습니다.
ms.openlocfilehash: 93f55e0c1e4d065e02a9cc41e5aaaab89b459a0d
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069474"
---
# <a name="office-365-video-networking-frequently-asked-questions"></a><span data-ttu-id="f9d40-104">Office 365 비디오 네트워킹에 대 한 질문과 대답</span><span class="sxs-lookup"><span data-stu-id="f9d40-104">Office 365 Video networking Frequently Asked Questions</span></span>

<span data-ttu-id="f9d40-105">Office 365 비디오 리포지토리와 스트리밍 서비스는 조직 내에서 비디오를 간단 하 게 저장 하 고 스트리밍하는 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9d40-105">The Office 365 Video repository and streaming services make storing and streaming videos within your organization simple.</span></span> <span data-ttu-id="f9d40-106">[Office 365 비디오에 대 한](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50)많은 유용한 정보가 있습니다. 이 네트워킹 FAQ는 대역폭 계획, 암호화 및 서비스가 cdns ( [콘텐츠 배달 네트워크](content-delivery-networks.md) )를 활용 하는 방법에 대 한 가장 일반적인 질문에 대 한 답변을 제공 하도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f9d40-106">There's a lot of great [information about Office 365 Video](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50); this networking FAQ is designed to answer the most common questions around bandwidth planning, encryption, and how the service leverages [Content Delivery Networks](content-delivery-networks.md) (CDNs).</span></span>
  
<span data-ttu-id="f9d40-107">비디오를 업로드 하거나 재생할 때 수행 되는 작업을 완전히 이해 하지 못한 경우에는이 비디오를 함께 살펴보고 [Office 365 비디오에 업로드할 때 비디오 파일](https://www.youtube.com/watch?v=HXSZ0jYBKlM)을 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="f9d40-107">If you don't already have a thorough understanding of what happens when a video is uploaded or played back, have a look at this video we put together, [What happens to a video file when uploaded to Office 365 Video](https://www.youtube.com/watch?v=HXSZ0jYBKlM).</span></span>
  
## <a name="what-are-the-office-365-video-bandwidth-requirements"></a><span data-ttu-id="f9d40-108">Office 365 비디오 대역폭 요구 사항은 무엇 인가요?</span><span class="sxs-lookup"><span data-stu-id="f9d40-108">What are the Office 365 Video bandwidth requirements?</span></span>

<span data-ttu-id="f9d40-109">Office 365에 업로드할 수 있는 지원 되는 다양 한 [비디오 형식이](https://support.office.com/article/dd1af01c-fd8e-4640-b17b-93ee02b9b817) 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9d40-109">There are a numerous [supported video formats](https://support.office.com/article/dd1af01c-fd8e-4640-b17b-93ee02b9b817) that can be uploaded to Office 365.</span></span> <span data-ttu-id="f9d40-110">각 비디오 파일은 재생을 위해 다양 한 비디오 품질을 사용 하 여 표준 형식으로 인코딩됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9d40-110">Each video file is then encoded to a standard format with several different video qualities for playback.</span></span> <span data-ttu-id="f9d40-111">Office 365 Video에서는 적응 비트 전송률 스트리밍을 사용 하 여 비디오 플레이어의 사용 가능한 네트워크 대역폭과 크기에 따라 가장 적합 한 비디오 재생 품질을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9d40-111">Office 365 Video uses adaptive bitrate streaming to select the best video playback quality based on the available network bandwidth and size of the video player.</span></span> <span data-ttu-id="f9d40-112">이를 위해 플레이어는 처음에는 가장 낮은 재생 품질을 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9d40-112">To do this, the player initially requests the lowest playback quality.</span></span> <span data-ttu-id="f9d40-113">그런 다음 서비스는 비디오 플레이어에 2 초 비디오 세그먼트를 전송 하기 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9d40-113">The service then begins sending 2-second video segments to the video player.</span></span> <span data-ttu-id="f9d40-114">그러면 플레이어에서 각 세그먼트가 배달 되는 속도에 따라 재생 품질이 높거나 낮게 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9d40-114">The player can then request higher or lower playback quality based on how quickly each segment is delivered.</span></span>
  
<span data-ttu-id="f9d40-115">적응 비트 전송률 스트리밍은 최소 중단 또는 버퍼링을 통해 비디오를 재생 하는 동안 백그라운드에서이 모든 시간을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9d40-115">The adaptive bitrate streaming does all this in the background while the video plays with the least amount of disruption or buffering.</span></span> <span data-ttu-id="f9d40-116">비디오 재생 중에 비디오 플레이어에서 자동 재생 품질을 수동으로 재정의 하 여 특정 비디오 재생 품질을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9d40-116">During video playback, the video player allows the viewer to manually override the automatic playback quality, to select a specific video playback quality.</span></span>
  
<span data-ttu-id="f9d40-117">다음은 각 비디오 재생 품질에 대 한 네트워크 요구 사항을 설명 하는 간단한 표입니다.</span><span class="sxs-lookup"><span data-stu-id="f9d40-117">Here's a quick table that outlines the network requirements for each of the video playback qualities.</span></span> <span data-ttu-id="f9d40-118">비디오를 재생 하는 데 필요한 사용자 당 최소 대역폭은 802Kbps입니다.</span><span class="sxs-lookup"><span data-stu-id="f9d40-118">The minimum bandwidth per person needed to play a video is 802Kbps.</span></span>
  
|||
|:-----|:-----|
|<span data-ttu-id="f9d40-119">**재생 품질**</span><span class="sxs-lookup"><span data-stu-id="f9d40-119">**Playback Quality**</span></span> <br/> |<span data-ttu-id="f9d40-120">**네트워크 속도**</span><span class="sxs-lookup"><span data-stu-id="f9d40-120">**Network Speed**</span></span> <br/> |
|<span data-ttu-id="f9d40-121">288p</span><span class="sxs-lookup"><span data-stu-id="f9d40-121">288p</span></span>  <br/> |<span data-ttu-id="f9d40-122">802Kbps</span><span class="sxs-lookup"><span data-stu-id="f9d40-122">802Kbps</span></span>  <br/> |
|<span data-ttu-id="f9d40-123">360p</span><span class="sxs-lookup"><span data-stu-id="f9d40-123">360p</span></span>  <br/> |<span data-ttu-id="f9d40-124">1.2 Mbps</span><span class="sxs-lookup"><span data-stu-id="f9d40-124">1.2 Mbps</span></span>  <br/> |
|<span data-ttu-id="f9d40-125">576p</span><span class="sxs-lookup"><span data-stu-id="f9d40-125">576p</span></span>  <br/> |<span data-ttu-id="f9d40-126">2.5 Mbps</span><span class="sxs-lookup"><span data-stu-id="f9d40-126">2.5 Mbps</span></span>  <br/> |
|<span data-ttu-id="f9d40-127">720p</span><span class="sxs-lookup"><span data-stu-id="f9d40-127">720p</span></span>  <br/> |<span data-ttu-id="f9d40-128">3.8 Mbps</span><span class="sxs-lookup"><span data-stu-id="f9d40-128">3.8 Mbps</span></span>  <br/> |

<span data-ttu-id="f9d40-129">([맨 위로](office-365-video-networking-faq.md)이동)</span><span class="sxs-lookup"><span data-stu-id="f9d40-129">([Back to top](office-365-video-networking-faq.md))</span></span>
  
## <a name="how-do-content-delivery-networks-cdns-help-video-playback"></a><span data-ttu-id="f9d40-130">CDNs (콘텐츠 배달 네트워크)에서 비디오 재생을 지원 하나요?</span><span class="sxs-lookup"><span data-stu-id="f9d40-130">How do Content Delivery Networks (CDNs) help video playback?</span></span>

<span data-ttu-id="f9d40-131">동일한 지리적 위치에 있는 동일한 조직에서 여러 사용자가 동일한 비디오를 스트리밍하는 경우 CDNs는 해당 지역에 가까운 위치에 이러한 비디오의 복사본을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9d40-131">If several people from the same organization within the same geographic location are streaming the same video(s), CDNs will store a copy of these videos in a location closer to that geographic region.</span></span> <span data-ttu-id="f9d40-132">비디오가 저장 되거나 가장 가까운 위치에 캐시 되 면 각 사용자는 위치에 상관 없이 비디오를 더 멀리 떨어진 위치에서 스트리밍합니다.</span><span class="sxs-lookup"><span data-stu-id="f9d40-132">With the video stored, or cached at the closest location, each person streams the video from the location closest to them instead of a location further away.</span></span> <span data-ttu-id="f9d40-133">Office 365 Video는 Azure Media Services를 사용 하 여 Azure CDNs에 캐시 된 항목과 기간을 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9d40-133">Office 365 Video uses Azure Media Services to manage what is cached in the Azure CDNs, and for how long.</span></span> <span data-ttu-id="f9d40-134">Azure 미디어 서비스는 [AZURE CDN 위치](https://azure.microsoft.com/documentation/articles/cdn-pop-locations/) 중 하나를 사용 하 여 며칠 동안 비디오 조각과 매니페스트를 캐시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9d40-134">Azure Media Services can use any of the [Azure CDN locations](https://azure.microsoft.com/documentation/articles/cdn-pop-locations/) to cache video fragments and manifests for a few days.</span></span> <span data-ttu-id="f9d40-135">조직의 사용자가 계속 해 서 캐시에 저장 되 면 캐시에 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9d40-135">If people in your organization continue to watch the cached videos they'll stay in the cache.</span></span> <span data-ttu-id="f9d40-136">며칠 동안 비디오에 액세스 하는 사람이 없는 경우에는 결국 비디오가 캐시에서 삭제 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9d40-136">If no one accesses the video for several days, the video will eventually drop be dropped from the cache.</span></span> <span data-ttu-id="f9d40-137">다음 번에 누군가 비디오 시청을 시도할 때 가장 가까운 CDN 위치에 다시 캐시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9d40-137">The next time someone attempts to watch the video it's once again cached at the nearest CDN location.</span></span>
  
<span data-ttu-id="f9d40-138">콘텐츠가 근처의 CDN에서 캐시 되는 동안 비디오를 시청 하려는 모든 사용자는 비디오가 더 가까이 있고, 대부분의 경우 홉의 수가 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="f9d40-138">Everyone who attempts to watch the video while the content is cached at a nearby CDN benefits from the video being closer, and in most cases less hops, away.</span></span> <span data-ttu-id="f9d40-139">이렇게 하면 비디오 재생 속도가 향상 됩니다. 그러나 비디오 재생을 위한 네트워크 요구 사항은 변경 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f9d40-139">This improves video playback speed; however, it doesn't change the network requirement to play the video.</span></span>
  
> [!NOTE]
> <span data-ttu-id="f9d40-140">용량 제한에 도달 하 여 3 일 전에 비디오를 제거할 수 있는 몇 가지 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9d40-140">There are some circumstances, such as our capacity limit being reached, where the video may be removed before the three days has been reached.</span></span>
  
<span data-ttu-id="f9d40-141">([맨 위로](office-365-video-networking-faq.md)이동)</span><span class="sxs-lookup"><span data-stu-id="f9d40-141">([Back to top](office-365-video-networking-faq.md))</span></span>
  
## <a name="can-i-cache-the-videos-locally-for-faster-playback"></a><span data-ttu-id="f9d40-142">보다 빠른 재생을 위해 비디오를 로컬로 캐시할 수 있나요?</span><span class="sxs-lookup"><span data-stu-id="f9d40-142">Can I cache the videos locally for faster playback?</span></span>

<span data-ttu-id="f9d40-143">예.</span><span class="sxs-lookup"><span data-stu-id="f9d40-143">Yes.</span></span> <span data-ttu-id="f9d40-144">Office 365에서는 로컬 CDN 또는 캐싱 프록시를 사용 하 여 비디오 또는 기타 Office 365 콘텐츠를 빠른 액세스를 위해 로컬 네트워크로 가져올 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f9d40-144">Office 365 won't prevent you from using a local CDN or a caching proxy to bring video or other Office 365 content into your local network for faster access.</span></span> <span data-ttu-id="f9d40-145">네트워크에서 로컬 캐싱 솔루션을 구현 하는 방법에는 여러 가지가 있으며, 가장 일반적인 방법은 콘텐츠를 로컬로 캐시 하는 프록시 솔루션을 사용 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f9d40-145">There are several ways to implement a local caching solution on your network, the most common method is to use a proxy solution that caches content locally.</span></span> <span data-ttu-id="f9d40-146">프록시 또는 개인 CDN에서 비디오 조각 및 매니페스트를 캐시 하면 프록시 또는 개인 CDN을 통해 라우팅되는 파일에 대 한 후속 요청이 로컬 캐시에서 추출 되 고 인터넷 위치에서 추출 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f9d40-146">Once a proxy or private CDN has cached the video fragments and manifests, future requests for those files that route through the proxy or private CDN are pulled from the local cache and not pulled from an internet location.</span></span> <span data-ttu-id="f9d40-147">이와 같은 솔루션을 계획 하는 동안 네트워크 대역폭, 용량 및 비디오 재생 병행성을 고려해 야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9d40-147">Consider network bandwidth, capacity, and video playback concurrency during the planning of a solution like this.</span></span>
  
<span data-ttu-id="f9d40-148">([맨 위로](office-365-video-networking-faq.md)이동)</span><span class="sxs-lookup"><span data-stu-id="f9d40-148">([Back to top](office-365-video-networking-faq.md))</span></span>
  
## <a name="how-videos-are-encrypted-and-secured"></a><span data-ttu-id="f9d40-149">비디오를 암호화 하 고 보호 하는 방법</span><span class="sxs-lookup"><span data-stu-id="f9d40-149">How videos are encrypted and secured?</span></span>

<span data-ttu-id="f9d40-150">Office 365 비디오에서는 데이터를 안전 하 고 개인적으로 유지 하는 것이 얼마나 중요 한지를 알고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9d40-150">Office 365 Video knows how important it is to keep your data secure and private.</span></span> <span data-ttu-id="f9d40-151">[Microsoft 보안 센터](https://products.office.com/business/office-365-trust-center-welcome) 는 콘텐츠의 개인 정보 및 보안에 대 한 약정을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9d40-151">[Microsoft Trust Center](https://products.office.com/business/office-365-trust-center-welcome) describes our commitment to the privacy and security of your content.</span></span> <span data-ttu-id="f9d40-152">비디오 재생을 사용 하면 속도가 매우 중요 한 환경을 경험할 수 있습니다. 그러나 exchange에서 속도를 높이기 위해 보안 또는 개인 정보를 손상 시 키 지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f9d40-152">With video playback, speed is important for a good experience; however, we don't compromise your security or privacy in exchange for speed.</span></span> <span data-ttu-id="f9d40-153">속도, 보안 및 개인 정보를 처리 하는 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f9d40-153">Here's how we accommodate speed, security and privacy.</span></span>
  
<span data-ttu-id="f9d40-154">사용자나 조직의 다른 사람이 새 비디오를 업로드 하면 해당 비디오는 트랜스 코딩 되 고, AES-128 암호화로 암호화 되며, Azure Media Services에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9d40-154">When you or someone in your organization uploads a new video, that video is transcoded, encrypted with AES-128 encryption, and stored in Azure Media Services.</span></span> <span data-ttu-id="f9d40-155">즉, 비디오는 전송 및 휴지에서 모두 암호화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9d40-155">This means the videos are encrypted both in transit and at rest.</span></span>
  
<span data-ttu-id="f9d40-156">조직의 누군가가 새 비디오를 시청 하려고 하면 다음 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9d40-156">When someone in your organization attempts to watch a new video, they follow these steps:</span></span>
  
1. <span data-ttu-id="f9d40-157">SharePoint Online에 비디오를 볼 수 있는 권한이 있는지 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="f9d40-157">Ask SharePoint Online if they have permission to view the video.</span></span>

2. <span data-ttu-id="f9d40-158">SharePoint Online은 파일 사용 권한을 사용 하 여 사용자가 비디오를 시청할 수 있는지 여부를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9d40-158">SharePoint Online uses the file permissions to determine if the person can watch the video.</span></span>

3. <span data-ttu-id="f9d40-159">허용 되는 경우 SharePoint Online은 비디오 플레이어에 게 제공할 Azure에서 토큰을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9d40-159">If they're allowed, SharePoint Online retrieves a token from Azure to give to the video player.</span></span>

4. <span data-ttu-id="f9d40-160">그런 다음 비디오 플레이어에서 토큰을 사용 하 여 Azure에서 암호 해독 키를 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9d40-160">The video player then uses the token to request the decryption key from Azure.</span></span>

5. <span data-ttu-id="f9d40-161">암호 해독 키가 있으면 비디오 재생기에서 비디오를 스트리밍할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9d40-161">With the decryption key in hand, the video player is able to stream the video.</span></span>

![O365 비디오 재생](media/9d3c6e76-151d-48a3-a30e-ba8dd07db0b7.png)
  
<span data-ttu-id="f9d40-163">([맨 위로](office-365-video-networking-faq.md)이동)</span><span class="sxs-lookup"><span data-stu-id="f9d40-163">([Back to top](office-365-video-networking-faq.md))</span></span>
  
## <a name="what-are-the-requirements-to-playback-office-365-video"></a><span data-ttu-id="f9d40-164">Office 365 동영상을 재생 하는 데 필요한 요구 사항은 무엇 인가요?</span><span class="sxs-lookup"><span data-stu-id="f9d40-164">What are the requirements to playback Office 365 Video?</span></span>

<span data-ttu-id="f9d40-165">Office 365 비디오 지원 운영 체제 및 웹 브라우저는 [office 365 시스템 요구 사항](https://support.office.com/article/Office-365-system-requirements-719254c0-2671-4648-9c84-c6a3d4f3be45)에 대 한 SharePoint Online 요구 사항과 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9d40-165">Office 365 Video supported operating systems and web browsers are the same as the SharePoint Online requirements in [Office 365 system requirements](https://support.office.com/article/Office-365-system-requirements-719254c0-2671-4648-9c84-c6a3d4f3be45).</span></span> <span data-ttu-id="f9d40-166">보유 하 고 있는 운영 체제 및 웹 브라우저 구성에 따라 비디오 플레이어의 특정 요구 사항을 결정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9d40-166">Depending on which operating system and web browser configuration you have will determine the specific needs of the video player.</span></span> <span data-ttu-id="f9d40-167">[비디오 재생 요구 사항](https://support.office.com/article/ca1cc1a9-a615-46e1-b6a3-40dbd99939a6)에 대 한 자세한 내용은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f9d40-167">Here's more information on [video playback requirements](https://support.office.com/article/ca1cc1a9-a615-46e1-b6a3-40dbd99939a6).</span></span>
  
<span data-ttu-id="f9d40-168">([맨 위로](office-365-video-networking-faq.md)이동)</span><span class="sxs-lookup"><span data-stu-id="f9d40-168">([Back to top](office-365-video-networking-faq.md))</span></span>
  
## <a name="i-cant-get-office-365-video-to-work-where-should-i-start"></a><span data-ttu-id="f9d40-169">Office 365 비디오를 사용할 수 없음 (시작 해야 하는 경우)</span><span class="sxs-lookup"><span data-stu-id="f9d40-169">I can't get Office 365 video to work, where should I start?</span></span>

<span data-ttu-id="f9d40-170">Office 365의 연결 문제 해결 비디오에는 네트워크, ISP 및 Office 365 구성에 대 한 문제 해결이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9d40-170">Troubleshooting connectivity to Office 365 Video involves troubleshooting your network, your ISP(s), and your configuration of Office 365.</span></span> <span data-ttu-id="f9d40-171">시작 하는 첫 번째 위치는 서비스 상태 대시보드입니다.</span><span class="sxs-lookup"><span data-stu-id="f9d40-171">The first place to start is the service health dashboard.</span></span> <span data-ttu-id="f9d40-172">이를 통해 Office 365 비디오에 문제가 있거나 그렇지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9d40-172">This will tell you of Office 365 Video is having a problem or not.</span></span> <span data-ttu-id="f9d40-173">여기에 모든 내용이 표시 되 면 도움이 되는 몇 가지 추가 리소스가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9d40-173">If everything looks great there, here's some additional resources to help you.</span></span>
  
- <span data-ttu-id="f9d40-174">[Office 365 비디오에 필요한 네트워크 끝점](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2)에 연결할 수 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9d40-174">Make sure you can connect to the [network endpoints required for Office 365 Video](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2).</span></span>

- <span data-ttu-id="f9d40-175">[Office 365 네트워크 문제 해결 가이드](https://support.office.com/article/Office-365-performance-tuning-and-troubleshooting-Admin-and-IT-Pro-1492cb94-bd62-43e6-b8d0-2a61ed88ebae)를 사용 하 여 네트워크 연결을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9d40-175">Check your network connectivity using our [Office 365 network troubleshooting guide](https://support.office.com/article/Office-365-performance-tuning-and-troubleshooting-Admin-and-IT-Pro-1492cb94-bd62-43e6-b8d0-2a61ed88ebae).</span></span>

- <span data-ttu-id="f9d40-176">[저속 네트워크에서 Office 365 사용에 대 한 모범 사례](https://support.office.com/article/Best-practices-for-using-Office-365-on-a-slow-network-fd16c8d2-4799-4c39-8fd7-045f06640166)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f9d40-176">See our [best practices for using Office 365 on a slow network](https://support.office.com/article/Best-practices-for-using-Office-365-on-a-slow-network-fd16c8d2-4799-4c39-8fd7-045f06640166).</span></span>

- <span data-ttu-id="f9d40-177">[Office 365 비디오 구성에 대 한 도움말을 찾아봅니다](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50).</span><span class="sxs-lookup"><span data-stu-id="f9d40-177">[Find help about Office 365 Video configuration](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50).</span></span>

<span data-ttu-id="f9d40-178">([맨 위로](office-365-video-networking-faq.md)이동)</span><span class="sxs-lookup"><span data-stu-id="f9d40-178">([Back to top](office-365-video-networking-faq.md))</span></span>
  
## <a name="office-365-video-resources"></a><span data-ttu-id="f9d40-179">Office 365 비디오 리소스</span><span class="sxs-lookup"><span data-stu-id="f9d40-179">Office 365 Video resources</span></span>

<span data-ttu-id="f9d40-180">다음은 Office 365 비디오를 성공적으로 배포 및 사용 하는 데 도움이 되는 몇 가지 기타 리소스입니다.</span><span class="sxs-lookup"><span data-stu-id="f9d40-180">Here's a few other resources to help you successfully deploy and use Office 365 Video:</span></span>
  
[<span data-ttu-id="f9d40-181">Office 365 비디오 구성에 대 한 도움말 찾기</span><span class="sxs-lookup"><span data-stu-id="f9d40-181">Find help about Office 365 Video configuration</span></span>](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50)
  
[<span data-ttu-id="f9d40-182">Office 365 비디오에 맞추기</span><span class="sxs-lookup"><span data-stu-id="f9d40-182">Meet Office 365 Video</span></span>](https://support.office.com/article/Meet-Office-365-Video-ca1cc1a9-a615-46e1-b6a3-40dbd99939a6)
  
[<span data-ttu-id="f9d40-183">Office 365 동영상에서 채널 만들기 및 관리</span><span class="sxs-lookup"><span data-stu-id="f9d40-183">Create and manage a channel in Office 365 Video</span></span>](https://support.office.com/article/Create-and-manage-a-channel-in-Office-365-Video-1fede4cc-13c0-435a-b585-e7fbf1c83bb2)
  
[<span data-ttu-id="f9d40-184">Office 365 비디오 포털 관리</span><span class="sxs-lookup"><span data-stu-id="f9d40-184">Manage your Office 365 Video portal</span></span>](https://support.office.com/article/Manage-your-Office-365-Video-portal-c059465b-eba9-44e1-b8c7-8ff7793ff5da)
  
[<span data-ttu-id="f9d40-185">Office 365 비디오에서 작동 하는 비디오 형식</span><span class="sxs-lookup"><span data-stu-id="f9d40-185">Video formats that work in Office 365 Video</span></span>](https://support.office.com/article/Video-formats-that-work-in-Office-365-Video-dd1af01c-fd8e-4640-b17b-93ee02b9b817)
  
<span data-ttu-id="f9d40-186">([맨 위로](office-365-video-networking-faq.md)이동)</span><span class="sxs-lookup"><span data-stu-id="f9d40-186">([Back to top](office-365-video-networking-faq.md))</span></span>
  
<span data-ttu-id="f9d40-187">다음의 간단한 링크를 사용할 수 있습니다. [https://aka.ms/video365networkfaq](https://aka.ms/video365networkfaq)</span><span class="sxs-lookup"><span data-stu-id="f9d40-187">Here's a short link you can use to come back: [https://aka.ms/video365networkfaq](https://aka.ms/video365networkfaq)</span></span>
