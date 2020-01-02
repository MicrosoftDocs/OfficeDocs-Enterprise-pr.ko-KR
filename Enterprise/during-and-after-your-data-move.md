---
title: 데이터 이동 도중 및 이후
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/10/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.collection: SPO_Content
search.appverid:
- MET150
localization_priority: Normal
ms.assetid: f47e3e09-b1dc-4b80-b6ea-fd6e0933407f
description: 데이터 이동은 최종 사용자에게 최소의 영향만 미치는 백 엔드 작업입니다. Microsoft에서 사용자의 테넌트의 각 서비스 및 연결된 데이터를 새 데이터 센터 지역으로 이동하는 동안 필요한 작업은 없습니다. 사용자에게 최소한의 영향만 미치면서, 백그라운드에서 사전에 데이터 전송 및 유효성 검사가 진행됩니다.
ms.openlocfilehash: f98d3a9aaef1197b1f424ce8cbd23b3d18b7ef2b
ms.sourcegitcommit: 761dd21a6b7a2650ef26fd8d6b303c04fa2546f2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/01/2020
ms.locfileid: "40923860"
---
# <a name="during-and-after-your-data-move"></a><span data-ttu-id="7a031-105">데이터 이동 도중 및 이후</span><span class="sxs-lookup"><span data-stu-id="7a031-105">During and after your data move</span></span>

<span data-ttu-id="7a031-p102">데이터 이동은 최종 사용자에게 최소의 영향만 미치는 백 엔드 작업입니다. Microsoft에서 사용자의 테넌트의 각 서비스 및 연결된 데이터를 새 데이터 센터 지역으로 이동하는 동안 필요한 작업은 없습니다. 사용자에게 최소한의 영향만 미치면서, 백그라운드에서 사전에 데이터 전송 및 유효성 검사가 진행됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a031-p102">Data moves are a back-end operation with minimal impact to end-users. No action is required while Microsoft moves each service and associated data for your tenant to a new datacenter geo. Data transfer and validation occur in the background in advance with minimal impact to users.</span></span>
  
> [!NOTE]
> <span data-ttu-id="7a031-109">서비스마다 다른 시간에 이동이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="7a031-109">Moves occur at different times for each service.</span></span> <span data-ttu-id="7a031-110">결과적으로 다른 시간에 각 서비스의 기능이 제한된다는 설명이 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a031-110">As a result, you'll see the described reduced functionality for each service at a different time.</span></span> 
  
<span data-ttu-id="7a031-111">각 Exchange Online, SharePoint Online 및 비즈니스용 Skype에 대한 이동이 완료되면 Office 365 메시지 센터에서 확인 알림을 찾아보세요.</span><span class="sxs-lookup"><span data-stu-id="7a031-111">Watch the Office 365 Message Center for confirmation when moves for each of Exchange Online, SharePoint Online, and Skype for Business are complete.</span></span> <span data-ttu-id="7a031-112">아래 표에 표시된 것처럼, 등록 기간이 끝나고 특정 지역의 모든 고객에 대해 요청된 모든 데이터 이동을 완료하는 데 24개월까지 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a031-112">As shown in the table below, it can take up to 24 months, after the end of the enrollment period, to complete all the requested data moves for all customers in a specific geo.</span></span> <span data-ttu-id="7a031-113">이동 후 테 넌 트에 문제가 표시 되는 경우 [Office 365 지원](https://go.microsoft.com/fwlink/p/?LinkID=522459) 서비스에 문의 하 여 도움을 받으십시오.</span><span class="sxs-lookup"><span data-stu-id="7a031-113">If you see any issues with your tenant after the move, contact [Office 365 Support](https://go.microsoft.com/fwlink/p/?LinkID=522459) to get assistance.</span></span> 
  

|<span data-ttu-id="7a031-114">**등록 국가가 있는 고객**</span><span class="sxs-lookup"><span data-stu-id="7a031-114">**Customers with signup country in**</span></span>|<span data-ttu-id="7a031-115">**모든 이동 완료 시기**</span><span class="sxs-lookup"><span data-stu-id="7a031-115">**All moves completed by**</span></span>|
|:-----|:-----|
|<span data-ttu-id="7a031-116">오스트레일리아, 뉴질랜드, 피지</span><span class="sxs-lookup"><span data-stu-id="7a031-116">Australia, New Zealand, Fiji</span></span>  <br/> |<span data-ttu-id="7a031-117">2022 년 7 월 1 일</span><span class="sxs-lookup"><span data-stu-id="7a031-117">July 1, 2022</span></span>  <br/> |
|<span data-ttu-id="7a031-118">일본</span><span class="sxs-lookup"><span data-stu-id="7a031-118">Japan</span></span>  <br/> |<span data-ttu-id="7a031-119">2022 년 7 월 1 일</span><span class="sxs-lookup"><span data-stu-id="7a031-119">July 1, 2022</span></span>  <br/> |
|<span data-ttu-id="7a031-120">인도</span><span class="sxs-lookup"><span data-stu-id="7a031-120">India</span></span>  <br/> |<span data-ttu-id="7a031-121">2022 년 7 월 1 일</span><span class="sxs-lookup"><span data-stu-id="7a031-121">July 1, 2022</span></span>  <br/> |
|<span data-ttu-id="7a031-122">캐나다</span><span class="sxs-lookup"><span data-stu-id="7a031-122">Canada</span></span>  <br/> |<span data-ttu-id="7a031-123">2022 년 7 월 1 일</span><span class="sxs-lookup"><span data-stu-id="7a031-123">July 1, 2022</span></span>  <br/> |
|<span data-ttu-id="7a031-124">대한민국</span><span class="sxs-lookup"><span data-stu-id="7a031-124">South Korea</span></span>  <br/> |<span data-ttu-id="7a031-125">2022 년 7 월 1 일</span><span class="sxs-lookup"><span data-stu-id="7a031-125">July 1, 2022</span></span>  <br/> |
|<span data-ttu-id="7a031-126">영국</span><span class="sxs-lookup"><span data-stu-id="7a031-126">United Kingdom</span></span>  <br/> |<span data-ttu-id="7a031-127">2022 년 7 월 1 일</span><span class="sxs-lookup"><span data-stu-id="7a031-127">July 1, 2022</span></span>  <br/> |
|<span data-ttu-id="7a031-128">프랑스</span><span class="sxs-lookup"><span data-stu-id="7a031-128">France</span></span>  <br/> |<span data-ttu-id="7a031-129">2022 년 7 월 1 일</span><span class="sxs-lookup"><span data-stu-id="7a031-129">July 1, 2022</span></span>  <br/> |
|<span data-ttu-id="7a031-130">아랍에미리트</span><span class="sxs-lookup"><span data-stu-id="7a031-130">United Arab Emirates</span></span>  <br/> |<span data-ttu-id="7a031-131">2022 년 7 월 1 일</span><span class="sxs-lookup"><span data-stu-id="7a031-131">July 1, 2022</span></span>  <br/> |
|<span data-ttu-id="7a031-132">남아프리카 공화국</span><span class="sxs-lookup"><span data-stu-id="7a031-132">South Africa</span></span>  <br/> |<span data-ttu-id="7a031-133">2022 년 7 월 1 일</span><span class="sxs-lookup"><span data-stu-id="7a031-133">July 1, 2022</span></span>  <br/> |
|<span data-ttu-id="7a031-134">스위스, 리히텐슈타인</span><span class="sxs-lookup"><span data-stu-id="7a031-134">Switzerland, Liechtenstein</span></span>  <br/> |<span data-ttu-id="7a031-135">2022 년 7 월 1 일</span><span class="sxs-lookup"><span data-stu-id="7a031-135">July 1, 2022</span></span>  <br/> |
|<span data-ttu-id="7a031-136">독일</span><span class="sxs-lookup"><span data-stu-id="7a031-136">Germany</span></span>  <br/> |<span data-ttu-id="7a031-137">하려고</span><span class="sxs-lookup"><span data-stu-id="7a031-137">Planned</span></span>  <br/> |

> [!NOTE]
> <span data-ttu-id="7a031-138">적격 Office 365 국가에 거주 하는 고객은 다른 적합 한 작업에 대 한 마이그레이션에 신호를 보내는 데 사용 되는 2020, 2020 ~ 6 월 1 일부 터 Microsoft 팀 채팅 서비스 데이터 마이그레이션을 옵트인 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a031-138">Customers in eligible Office 365 countries may opt-in for Microsoft Teams chat service data migration from January 1, 2020 through June 30, 2020, which will also signal migration for any other eligible workloads.</span></span>  <span data-ttu-id="7a031-139">2020 이전에 마이그레이션을 위해 옵트인 하면 Exchange Online 및 SharePoint Online/비즈니스용 OneDrive 이동이 원래 기한에 의해 완료 될 것 이며, 팀은 모든 고객에 대해 2022 년 7 월 1 일까지 완료 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a031-139">Customers that opted-in for migration prior to 2020 can expect Exchange Online and SharePoint Online/OneDrive for Business moves to complete by the original deadline, while Teams will complete by July 1, 2022 for all customers.</span></span> 

## <a name="exchange-online"></a><span data-ttu-id="7a031-140">Exchange Online</span><span class="sxs-lookup"><span data-stu-id="7a031-140">Exchange Online</span></span>

<span data-ttu-id="7a031-141">각 사용자를 새 데이터 센터 지역으로 이동하는 데 시간이 걸리므로 일부 사용자는 다른 사용자가 새 데이터 센터 지역으로 이동되는 동안 이전 데이터 센터 지역에 계속 남아 있게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a031-141">Because it takes time to move each user to the new datacenter geo for a single tenant, some users will still be in the old datacenter geo during the move, while others will be in the new datacenter geo.</span></span> <span data-ttu-id="7a031-142">즉, 여러 사서함에 액세스 하는 기능 중 일부는 지난 주까지 이동 프로세스를 진행 하는 동안 제대로 작동 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a031-142">This means that some features that involve accessing multiple mailboxes may not fully work during a period of the move process, which can last weeks.</span></span> <span data-ttu-id="7a031-143">이러한 기능은 다음 섹션에 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a031-143">These features are described in the following sections.</span></span>
  
### <a name="open-shared-folder-in-outlook-web-access"></a><span data-ttu-id="7a031-144">Outlook Web Access에서 "공유 폴더" 열기 </span><span class="sxs-lookup"><span data-stu-id="7a031-144">Open "Shared Folder" in Outlook Web Access</span></span>

<span data-ttu-id="7a031-145">일부 사용자는 "공유 폴더" 기능을 사용 하 여 Outlook Web Access에서 다른 사서함 (사용자가 읽기 또는 쓰기 권한을 가진 공유 메일 폴더)을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="7a031-145">Some users open a shared mail folder from another mailbox (that the user has read or write permissions to) in Outlook Web Access using the "Shared Folder" feature.</span></span> <span data-ttu-id="7a031-146">다음 표에서는 사서함을 이동 하는 동안 공유 폴더에 대 한 액세스를 작동 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a031-146">The following table describes how access to shared folders works during a mailbox move.</span></span> <span data-ttu-id="7a031-147">공유 사서함에 대한 모든 권한이 있는 사용자는 이동하는 동안 Outlook Web Access를 사용하여 사서함을 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a031-147">Please note that users with full permissions to a shared mailbox can open the mailbox by using Outlook Web Access during the move.</span></span> 
  
|<span data-ttu-id="7a031-148">**구성**</span><span class="sxs-lookup"><span data-stu-id="7a031-148">**Configuration**</span></span>|<span data-ttu-id="7a031-149">**설명**</span><span class="sxs-lookup"><span data-stu-id="7a031-149">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="7a031-150">사용자에게 다른 사서함에 대한 사서함 폴더 권한이 있음</span><span class="sxs-lookup"><span data-stu-id="7a031-150">User has mailbox folder permission to another mailbox</span></span>  <br/> |<span data-ttu-id="7a031-151">제한될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a031-151">Potentially limited.</span></span>  <br/> <span data-ttu-id="7a031-152">사용자 a와 사서함 B가 테 넌 트 이동 중에 같은 지역에 있지 않은 경우 사용자 a는 사서함 B의 특정 폴더에 대 한 사용 권한이 있는 경우 Outlook Web Access에서 사서함 B의 폴더를 열 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7a031-152">If User A and Mailbox B aren't in the same geo during the tenant move, User A can't open Mailbox B's folder in Outlook Web Access if User A only has permission to a specific folder in Mailbox B.</span></span>  <br/> <span data-ttu-id="7a031-153">공유 폴더를 추가하려면 왼쪽 탐색 패널에서 사용자 이름을 마우스 오른쪽 단추로 클릭하고 **공유 폴더 추가**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7a031-153">To add a shared folder, right-click the user name in the left navigation panel and select **Add shared folder**.</span></span>  <br/> |
|<span data-ttu-id="7a031-154">사용자에게 다른 사서함에 대한 모든 사서함 권한이 있음</span><span class="sxs-lookup"><span data-stu-id="7a031-154">User with full mailbox permission to another mailbox</span></span>  <br/> |<span data-ttu-id="7a031-155">완전히 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a031-155">Fully supported.</span></span>  <br/> <span data-ttu-id="7a031-156">사용자 A에 게 사서함 B에 대 한 "모든 권한" 권한이 있으면 사용자 A가 Outlook Web Access의 왼쪽 탐색 패널에서 공유 폴더를 클릭 하 여 사서함 B가 표시 된 창을 열 수 있습니다.  사용자는 부정적인 영향을 주지 않으면 서 이동 하는 동안 Outlook Web Access를 사용 하 여 공유 사서함을 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a031-156">If User A has "Full Access" permission to Mailbox B, then User A can click the shared folder in the left navigation panel in Outlook Web Access to open a window showing Mailbox B.  A user can open a shared mailbox using Outlook Web Access during the move without any adverse impact.</span></span> <span data-ttu-id="7a031-157">이러한 제한 사항은 사서함의 폴더 수준 공유에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a031-157">The limitation only applies to folder-level sharing in a mailbox.</span></span>           |
  
## <a name="sharepoint-online"></a><span data-ttu-id="7a031-158">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="7a031-158">SharePoint Online</span></span>

<span data-ttu-id="7a031-159">SharePoint Online이 이동 될 때 다음 서비스에 대 한 데이터도 이동 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a031-159">When SharePoint Online is moved, data for the following services is also moved:</span></span>
  
- <span data-ttu-id="7a031-160">비즈니스용 OneDrive</span><span class="sxs-lookup"><span data-stu-id="7a031-160">One Drive for Business</span></span>
    
- <span data-ttu-id="7a031-161">Project Online</span><span class="sxs-lookup"><span data-stu-id="7a031-161">Project Online</span></span>
    
- <span data-ttu-id="7a031-162">Project for Office 365</span><span class="sxs-lookup"><span data-stu-id="7a031-162">Project for Office 365</span></span>
    
- <span data-ttu-id="7a031-163">Office 365 비디오 서비스</span><span class="sxs-lookup"><span data-stu-id="7a031-163">Office 365 Video services</span></span>
    
- <span data-ttu-id="7a031-164">S 브라우저의 Office</span><span class="sxs-lookup"><span data-stu-id="7a031-164">Office in s browser</span></span>
    
- <span data-ttu-id="7a031-165">Office 365 ProPlus</span><span class="sxs-lookup"><span data-stu-id="7a031-165">Office 365 ProPlus</span></span>
    
- <span data-ttu-id="7a031-166">Visio Pro for Office 365</span><span class="sxs-lookup"><span data-stu-id="7a031-166">Visio Pro for Office 365</span></span>
    
<span data-ttu-id="7a031-167">SharePoint Online 데이터 이동을 완료 한 후에는 다음과 같은 몇 가지 효과를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a031-167">After we've completed moving your SharePoint Online data, you might see the some of the following effects.</span></span>
  
### <a name="office-365-video-services"></a><span data-ttu-id="7a031-168">Office 365 비디오 서비스</span><span class="sxs-lookup"><span data-stu-id="7a031-168">Office 365 Video Services</span></span>

- <span data-ttu-id="7a031-169">비디오에서는 SharePoint Online에서 콘텐츠의 나머지 부분에 대 한 이동을 보다 긴 데이터 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="7a031-169">The data move for video takes longer than the moves for the rest of your content in SharePoint Online.</span></span>
    
- <span data-ttu-id="7a031-170">SharePoint Online 콘텐츠를 이동한 후에는 비디오를 재생할 수 없을 때 시간 프레임이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="7a031-170">After the SharePoint Online content is moved, there will be a time frame when videos aren't able to be played.</span></span>
    
- <span data-ttu-id="7a031-171">이전 데이터 센터에서 코드 변환된 복사본을 제거한 후 새로운 데이터 센터에서 다시 코드 변환을 수행하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="7a031-171">We're removing the trans-coded copies from the previous datacenter and transcoding them again in the new datacenter.</span></span>
    
### <a name="search"></a><span data-ttu-id="7a031-172">검색</span><span class="sxs-lookup"><span data-stu-id="7a031-172">Search</span></span>

<span data-ttu-id="7a031-173">SharePoint Online 데이터를 이동 하는 과정에서 검색 인덱스 및 검색 설정을 새 위치로 마이그레이션합니다.</span><span class="sxs-lookup"><span data-stu-id="7a031-173">In the course of moving your SharePoint Online data, we migrate your search index and search settings to a new location.</span></span> <span data-ttu-id="7a031-174">SharePoint Online 데이터를 이동할 때까지 계속 해 서 사용자에 게 원래 위치에 있는 인덱스를 **처리 합니다.**</span><span class="sxs-lookup"><span data-stu-id="7a031-174">Until we've **completed** the move of your SharePoint Online data, we continue to serve your users from the index in the original location.</span></span> <span data-ttu-id="7a031-175">SharePoint Online 데이터 이동이 완료 된 후 새 위치에서 검색을 통해 콘텐츠 크롤링이 자동으로 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a031-175">In the new location, search automatically starts crawling your content after we've completed moving your SharePoint Online data.</span></span> <span data-ttu-id="7a031-176">이 시점부터는 마이그레이션된 인덱스에서 고객의 사용자에게 서비스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7a031-176">From this point and onwards we serve your users from the migrated index.</span></span> <span data-ttu-id="7a031-177">마이그레이션 후 발생하는 콘텐츠 변경 내용은 크롤링하기 전까지 마이그레이션된 인덱스에 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7a031-177">Changes to your content that occurred after the migration aren't included in the migrated index until crawling picks them up.</span></span> <span data-ttu-id="7a031-178">대부분의 고객은 SharePoint Online 데이터 이동을 완료 한 후 결과가 최신이 아닌 것을 알 수 없지만, 일부 고객의 경우 처음 24-48 시간 동안 최신 상태를 유지 하는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a031-178">Most customers don't notice that results are less fresh right after we've completed moving their SharePoint Online data, but some customers might experience reduced freshness in the first 24-48 hours</span></span> 
  
<span data-ttu-id="7a031-179">영향을 받는 기능은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7a031-179">The following search features are affected:</span></span>
  
- <span data-ttu-id="7a031-180">검색 결과 및 검색 웹 파트: 마이그레이션 후 발생한 변경 내용은 크롤링하기 전까지 결과에 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7a031-180">Search results and Search Web Parts: Results don't include changes that occurred after the migration until crawling picks them up.</span></span> 
    
- <span data-ttu-id="7a031-181">Delve: 마이그레이션 후 발생한 변경 내용은 크롤링하기 전까지 Delve에 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7a031-181">Delve: Delve doesn't include changes that occurred after the migration until crawling picks them up.</span></span>
    
- <span data-ttu-id="7a031-182">사이트에 대 한 인기 및 검색 보고서: 새 위치에 있는 Excel 보고서의 수에는 SharePoint Online 데이터 이동이 완료 된 후에 실행 된 사용 현황 보고서의 마이그레이션 수와 카운트만 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a031-182">Popularity and Search Reports for the site: Counts for Excel reports in the new location only include migrated counts and counts from usage reports that have run after we completed moving your SharePoint Online data.</span></span> <span data-ttu-id="7a031-183">중간 기간의 모든 수는 손실되며 복구할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7a031-183">Any counts from the interim period are lost and can't be recovered.</span></span> <span data-ttu-id="7a031-184">이 기간은 일반적으로 이틀 정도입니다.</span><span class="sxs-lookup"><span data-stu-id="7a031-184">This period is typically a couple of days.</span></span> <span data-ttu-id="7a031-185">일부 고객은 손실되는 기간이 더 짧거나 길 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a031-185">Some customers might experience shorter or longer losses.</span></span>
    
- <span data-ttu-id="7a031-186">비디오 포털: 비디오 포털의 조회수 및 통계는 Excel 보고서 통계에 따라 달라지므로 Excel 보고서의 손실 기간만큼 비디오 포털에 대한 조회수 및 통계가 손실됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a031-186">Video Portal: View counts and statistics for the Video Portal depend on the statistics for Excel Reports, so view counts and statistics for the Video Portal are lost for the same time period as for the Excel reports.</span></span>
    
- <span data-ttu-id="7a031-187">eDiscovery: 마이그레이션하는 동안 변경된 항목은 크롤링하기 전까지 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7a031-187">eDiscovery: Items that changed during the migration aren't shown until crawling picks up the changes.</span></span>
    
- <span data-ttu-id="7a031-188">DLP(데이터 손실 방지): 항목의 변경 내용을 크롤링하기 전까지는 항목에 정책이 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7a031-188">Data Loss Protection (DLP): Policies aren't enforced on items that change until crawling picks up the changes.</span></span>

## <a name="microsoft-teams"></a><span data-ttu-id="7a031-189">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="7a031-189">Microsoft Teams</span></span>

<span data-ttu-id="7a031-190">적합 한 Office 365 국가의 고객은 2020에서 Microsoft 팀 채팅 서비스 데이터 마이그레이션을 옵트인 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a031-190">Customers in eligible Office 365 countries may opt-in for Microsoft Teams chat service data migration as of January 1, 2020.</span></span>  

## <a name="skype-for-business"></a><span data-ttu-id="7a031-191">비즈니스용 Skype</span><span class="sxs-lookup"><span data-stu-id="7a031-191">Skype for Business</span></span>

<span data-ttu-id="7a031-p111">단독형 마이그레이션 동안 비즈니스용 Skype 클라이언트 소프트웨어에서 모든 사용자가 로그아웃됩니다. 자동 로그인이 수행되면서 2분 내에 사용자가 다시 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a031-p111">All users will be signed out from the Skype for Business client software during cut-over. The automatic sign-in will reconnect users within two minutes.</span></span>
  
|<span data-ttu-id="7a031-194">**전체 이동 중에 작동 하는 기능**</span><span class="sxs-lookup"><span data-stu-id="7a031-194">**Features that work during entire move**</span></span>|<span data-ttu-id="7a031-195">**이동 중에 제한 될 수 있는 기능**</span><span class="sxs-lookup"><span data-stu-id="7a031-195">**Features that may be limited during a portion of the move**</span></span>|
|:-----|:-----|
| <span data-ttu-id="7a031-196">인스턴트 메시징 및 음성 통화</span><span class="sxs-lookup"><span data-stu-id="7a031-196">Instant messaging and voice calls</span></span>  <br/>  <span data-ttu-id="7a031-197">사용자는 대화 상대를 추가하고, 대화 상대 그룹을 추가하고, 모임을 추가하고, 위치를 설정하고, "새로운 소식"을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a031-197">Users can add contacts, add contact groups, add meetings, set their location, and change "What's Happening Today".</span></span>  <br/>  <span data-ttu-id="7a031-p112">ACP(오디오 회의 공급자) 설정은 대상 데이터 센터 지역으로 복사됩니다. ACP 공급자가 대상 데이터 센터에 있으면 작동하고, 그렇지 않으면 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7a031-p112">Audio Conferencing Provider (ACP) settings are copied to the target datacenter geo. If the ACP provider is present in the target datacenter, it will work. Otherwise, it will not.</span></span>  <br/> | <span data-ttu-id="7a031-201">관리자는 테넌트 관리자 TRPS(테넌트 원격 PowerShell)를 사용하여 세션을 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7a031-201">Tenant Admin TRPS (Tenant Remote PowerShell) will not be available for administrators to create sessions.</span></span>  <br/>  <span data-ttu-id="7a031-202">관리자는 테넌트 관리자 LAC를 사용하여 로그인하고 사용자 설정을 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7a031-202">Tenant administrator LAC will not be available for administrators to sign in and change user settings.</span></span>  <br/> |
   
|<span data-ttu-id="7a031-203">**이동 후**</span><span class="sxs-lookup"><span data-stu-id="7a031-203">**After the move**</span></span>|
|:-----|
| <span data-ttu-id="7a031-204">모임 데이터(업로드된 프레젠테이션 등)는 이동되지 않으므로 다시 업로드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a031-204">Meeting data (uploaded presentations, etc.) will not move and will need to be re-uploaded.</span></span>  <br/>  <span data-ttu-id="7a031-205">Lync 2010 클라이언트 및 Mac 2011용 Lync 클라이언트와 같은 이전 버전의 Lync 클라이언트는 DNS 정보를 서비스로 캐시하여 로그인 문제를 일으키는 것으로 알려져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a031-205">Older Lync clients, such as the Lync 2010 client and Lync for Mac 2011 client, are known to cache DNS information to the service causing sign-in issues.</span></span> <span data-ttu-id="7a031-206">사용자가 최신 비즈니스용 Skype Windows 클라이언트를 사용하지 않는 경우 DNS 캐시를 지워야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a031-206">Clearing the DNS cache may be required if the user is not on the latest Skype for Business Windows client.</span></span> <span data-ttu-id="7a031-207">[Office 365에서 비즈니스용 Skype 온라인 DNS 구성 문제 해결](https://docs.microsoft.com/skypeforbusiness/troubleshoot/online-configuration/dns-configuration-issue)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7a031-207">See [Troubleshooting Skype for Business Online DNS configuration issues in Office 365](https://docs.microsoft.com/skypeforbusiness/troubleshoot/online-configuration/dns-configuration-issue).</span></span> <span data-ttu-id="7a031-208">Mac 용 Lync 클라이언트 사용자는 [다음 지침](https://support.microsoft.com/kb/2629861)을 따라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a031-208">Lync for Mac client users should follow [these instructions](https://support.microsoft.com/kb/2629861).</span></span>  <br/> |
   
### <a name="skype-for-business-moves-that-involve-a-third-party-audio-conferencing-provider"></a><span data-ttu-id="7a031-209">타사 오디오 회의 공급자를 포함 하는 비즈니스용 Skype 이동</span><span class="sxs-lookup"><span data-stu-id="7a031-209">Skype for Business moves that involve a third-party Audio Conferencing Provider</span></span>
<span data-ttu-id="7a031-210">새로운 지역별 데이터 센터에 소속된 사용자는 비즈니스용 Skype에 대한 타사 오디오 회의 공급자 추가 기능 서비스를 사용할 수 없습니다. </span><span class="sxs-lookup"><span data-stu-id="7a031-210">Third-party Audio Conferencing Provider add-on services for Skype for Business are not available for users homed in new geo-specific data centers.</span></span>  <span data-ttu-id="7a031-211">타사 오디오 회의 공급자 서비스를 사용하는 기존 고객은 새로운 지역별 데이터 센터로의 이동을 요청하지 않는 것이 좋습니다. </span><span class="sxs-lookup"><span data-stu-id="7a031-211">Existing customers using a third-party Audio Conferencing Provider service should not request a move to a new geo-specific data center.</span></span>  <span data-ttu-id="7a031-212">새로운 지역별 데이터 센터에 배포된 신규 고객은 타사 오디오 회의 공급자를 사용하기 위해 지역별 데이터 센터로의 이동을 요청해야 합니다. </span><span class="sxs-lookup"><span data-stu-id="7a031-212">New customers deployed into the new geo-specific data centers will need to request a move to a regional data center to use a third-party Audio Conferencing Provider.</span></span>
  
## <a name="related-topics"></a><span data-ttu-id="7a031-213">관련 항목</span><span class="sxs-lookup"><span data-stu-id="7a031-213">Related topics</span></span> 
 
[<span data-ttu-id="7a031-214">데이터 이동을 요청하는 방법</span><span class="sxs-lookup"><span data-stu-id="7a031-214">How to request your data move</span></span>](request-your-data-move.md)
    
[<span data-ttu-id="7a031-215">데이터 이동 일반 FAQ</span><span class="sxs-lookup"><span data-stu-id="7a031-215">Data move general FAQ</span></span>](data-move-faq.md)
  
[<span data-ttu-id="7a031-216">Microsoft Dynamics CRM Online에 대 한 새로운 데이터 센터 지역</span><span class="sxs-lookup"><span data-stu-id="7a031-216">New datacenter geos for Microsoft Dynamics CRM Online</span></span>](https://go.microsoft.com/fwlink/p/?Linkid=615924)
  
[<span data-ttu-id="7a031-217">지역별 Azure services</span><span class="sxs-lookup"><span data-stu-id="7a031-217">Azure services by region</span></span>](https://azure.microsoft.com/regions/)

