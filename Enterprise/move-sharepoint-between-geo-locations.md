---
title: SharePoint 사이트를 다른 지리적 위치로 이동
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.collection:
- Strat_SP_gtc
- SPO_Content
localization_priority: Priority
description: SharePoint 사이트를 다른 지리적 위치로 이동하는 방법을 알아봅니다.
ms.openlocfilehash: 3ba95215860646691e511b17d509dbbc49a5a75a
ms.sourcegitcommit: fa900775790eb369db1983cd3868b628b699f145
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2019
ms.locfileid: "38033444"
---
# <a name="move-a-sharepoint-site-to-a-different-geo-location"></a><span data-ttu-id="cf027-103">SharePoint 사이트를 다른 지리적 위치로 이동</span><span class="sxs-lookup"><span data-stu-id="cf027-103">Move a SharePoint site to a different geo location</span></span>

<span data-ttu-id="cf027-104">SharePoint 사이트 지리적 이동으로 SharePoint 사이트를 Multi-Geo 환경 내에서 다른 지리적 위치로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-104">With SharePoint site geo move, you can move SharePoint sites to other geo locations within your multi-geo environment.</span></span>

<span data-ttu-id="cf027-105">다음과 같은 유형의 사이트를 지리적 위치 간에 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-105">The following types of site can be moved between geo locations:</span></span>

- <span data-ttu-id="cf027-106">Office 365 그룹에 연결된 사이트</span><span class="sxs-lookup"><span data-stu-id="cf027-106">Office 365 Group-connected sites</span></span>
- <span data-ttu-id="cf027-107">Office 365 그룹과 연결되지 않은 최신 사이트</span><span class="sxs-lookup"><span data-stu-id="cf027-107">Modern sites without an Office 365 Group association</span></span>
- <span data-ttu-id="cf027-108">클래식 SharePoint 사이트</span><span class="sxs-lookup"><span data-stu-id="cf027-108">Classic SharePoint sites</span></span>
- <span data-ttu-id="cf027-109">커뮤니케이션 사이트</span><span class="sxs-lookup"><span data-stu-id="cf027-109">Communication sites</span></span>

<span data-ttu-id="cf027-110">지리적 위치 간에 사이트를 이동하려면 전역 관리자 또는 SharePoint 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-110">You must be a Global Administrator or SharePoint Administrator to move a site between geo locations.</span></span>

<span data-ttu-id="cf027-111">사이트 콘텐츠에 따라 약 4~6시간이 걸리는 SharePoint 사이트 지리적 이동 기간에 읽기 전용 창이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-111">There is a read-only window during the SharePoint site geo move of approximately 4-6 hours, depending on site contents.</span></span>
 
## <a name="best-practices"></a><span data-ttu-id="cf027-112">모범 사례</span><span class="sxs-lookup"><span data-stu-id="cf027-112">Best practices</span></span>

- <span data-ttu-id="cf027-113">절차에 익숙해지려면 테스트 사이트에서 SharePoint 사이트 이동을 수행해 보세요.</span><span class="sxs-lookup"><span data-stu-id="cf027-113">Try a SharePoint site move on a test site to get familiar with the procedure.</span></span> 
- <span data-ttu-id="cf027-114">이동을 예약하거나 수행하기 전에 사이트를 이동할 수 있는지를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-114">Validate whether the site can be moved prior to scheduling or performing the move.</span></span> 
- <span data-ttu-id="cf027-115">가능한 경우 사용자 영향을 줄이기 위해 업무 외 시간에 지역 간 사이트 이동을 예약합니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-115">When possible schedule cross-geo sites moves for outside business hours to reduce user impact.</span></span>
- <span data-ttu-id="cf027-116">사이트를 이동하기 전에 영향을 받을 사용자에게 정보를 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-116">Communicate with impacted users prior to the sites move.</span></span> 

## <a name="communicating-to-your-users"></a><span data-ttu-id="cf027-117">사용자에게 정보 전달</span><span class="sxs-lookup"><span data-stu-id="cf027-117">Communicating to your users</span></span>

<span data-ttu-id="cf027-118">지리적 위치 간에 SharePoint 사이트를 이동할 때 사이트의 사용자(일반적으로 사이트를 편집할 수 있는 사용자)에게 앞으로 일어날 일에 대한 정보를 알려주는 것이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-118">When moving SharePoint sites between geo locations, it's important to communicate to the sites' users (generally anyone with the ability to edit the site) what to expect.</span></span> <span data-ttu-id="cf027-119">그러면 사용자의 혼란을 막고 문의 전화를 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-119">This can help reduce user confusion and calls to your help desk.</span></span> <span data-ttu-id="cf027-120">이동하기 전에 사이트의 사용자에게 이메일로 다음 정보를 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-120">Email your sites' users before the move and let them know the following information:</span></span>

- <span data-ttu-id="cf027-121">이동 시작 시간 및 소요 시간</span><span class="sxs-lookup"><span data-stu-id="cf027-121">When the move is expected to start and how long it is expected to take</span></span>
- <span data-ttu-id="cf027-122">사이트가 이동할 지리적 위치 및 새 위치에 액세스하기 위한 URL</span><span class="sxs-lookup"><span data-stu-id="cf027-122">What geo location their site is moving to, and the URL to access the new location</span></span>
- <span data-ttu-id="cf027-123">이동 중에는 파일을 닫고 편집하지 말아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-123">They should close their files and not make edits during the move.</span></span>
- <span data-ttu-id="cf027-124">이동해도 파일 권한 및 공유는 달라지지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-124">File permissions and sharing will not change because of the move.</span></span>
- <span data-ttu-id="cf027-125">Multi-Geo 환경의 사용자 환경에서 예상할 점</span><span class="sxs-lookup"><span data-stu-id="cf027-125">What to expect from the user experience in a multi-geo environment</span></span>

<span data-ttu-id="cf027-126">이동이 완료되면 사이트의 사용자에게 이메일을 보내 이제 사이트에서 작업을 다시 시작할 수 있음을 알려야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-126">Be sure to send your sites' users an email when the move has successfully completed informing them that they can resume working on their sites.</span></span>

## <a name="scheduling-sharepoint-site-moves"></a><span data-ttu-id="cf027-127">SharePoint 사이트 이동 예약</span><span class="sxs-lookup"><span data-stu-id="cf027-127">Scheduling SharePoint site moves</span></span>

<span data-ttu-id="cf027-128">SharePoint 사이트 이동을 사전에 예약할 수 있습니다(이 문서의 뒷부분에서 설명).</span><span class="sxs-lookup"><span data-stu-id="cf027-128">You can schedule SharePoint site moves in advance (described later in this article).</span></span> <span data-ttu-id="cf027-129">이동 작업은 다음과 같이 예약할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-129">You can schedule moves as follows:</span></span>

- <span data-ttu-id="cf027-130">한 번에 이동을 최대 4,000개 예약할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-130">You can schedule up to 4,000 moves at a time.</span></span>
- <span data-ttu-id="cf027-131">이동이 시작되면 큐와 주어진 시간에 보류 중인 이동 최대 4,000개를 추가로 예약할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-131">As the moves begin, you can schedule more, with a maximum of 4,000 pending moves in the queue and any given time.</span></span>
 
<span data-ttu-id="cf027-132">SharePoint 사이트 지리적 이동 일정을 나중으로 예약하려면 이동하기 시작할 때 다음 매개 변수 중 하나를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-132">To schedule a SharePoint site geo move for a later time, include one of the following parameters when you start the move:</span></span>
- <span data-ttu-id="cf027-133">`PreferredMoveBeginDate` - 이 지정 시간에 이동하기 시작할 가능성이 높습니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-133">`PreferredMoveBeginDate` – The move will likely begin at this specified time.</span></span>
- <span data-ttu-id="cf027-134">`PreferredMoveEndDate` - 최선의 노력에 따라, 이 지정 시간에 이동을 완료할 가능성이 높습니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-134">`PreferredMoveEndDate` – The move will likely be completed by this specified time, on a best effort basis.</span></span> 

<span data-ttu-id="cf027-135">두 매개 변수 모두 시간이 UTC(협정 세계시)로 지정되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-135">Time must be specified in Coordinated Universal Time (UTC) for both parameters.</span></span>

## <a name="moving-the-site"></a><span data-ttu-id="cf027-136">사이트 이동</span><span class="sxs-lookup"><span data-stu-id="cf027-136">Moving the site</span></span>

<span data-ttu-id="cf027-137">SharePoint 사이트 지리적 이동을 수행하려면 사이트가 있는 지리적 위치의 SharePoint 관리자 URL에서 연결 후 이동을 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-137">SharePoint site geo move requires that you connect and perform the move from the SharePoint Admin URL in the geo location where the site is.</span></span>

<span data-ttu-id="cf027-138">예를 들어 사이트 URL이 https://contosohealthcare.sharepoint.com/sites/Turbines인 경우, https://contosohealthcare-admin.sharepoint.com:에서 SharePoint 관리자 URL에 연결</span><span class="sxs-lookup"><span data-stu-id="cf027-138">For example, if the site URL is https://contosohealthcare.sharepoint.com/sites/Turbines, connect to the SharePoint Admin URL at https://contosohealthcare-admin.sharepoint.com:</span></span>

`connect-sposervice -url https://contosohealthcare-admin.sharepoint.com`

![](media/move-onedrive-between-geo-locations-image1.png)
 
### <a name="validating-the-environment"></a><span data-ttu-id="cf027-139">환경 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="cf027-139">Validating the environment</span></span>

<span data-ttu-id="cf027-140">사이트 이동을 예약하기 전에 먼저 유효성 검사를 수행하여 사이트를 이동할 수 있는지를 확인하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-140">We recommend that before scheduling any site move, you perform a validation to ensure that the site can be moved.</span></span>

<span data-ttu-id="cf027-141">다음을 사용한 사이트 이동은 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-141">We do not support moving sites with:</span></span>
-   <span data-ttu-id="cf027-142">Business Connectivity Services</span><span class="sxs-lookup"><span data-stu-id="cf027-142">Business Connectivity Services</span></span>
-   <span data-ttu-id="cf027-143">InfoPath 양식</span><span class="sxs-lookup"><span data-stu-id="cf027-143">InfoPath forms</span></span> 

<span data-ttu-id="cf027-144">모든 지리적 위치가 호환되는지 확인하려면 `Get-SPOGeoMoveCrossCompatibilityStatus`를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-144">To ensure all geo locations are compatible, run `Get-SPOGeoMoveCrossCompatibilityStatus`.</span></span> <span data-ttu-id="cf027-145">그러면 모든 지리적 위치가 표시되고 환경이 대상 지리적 위치와 호환되는지 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-145">This will display all your geo locations and whether the environment is compatible with the destination geo location.</span></span>

<span data-ttu-id="cf027-146">사이트의 유효성만을 검사하려면 `Start-SPOSiteContentMove`와 `-ValidationOnly` 매개 변수를 사용하여 사이트를 이동할 수 있는지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-146">To perform a validation-only check on your site, use `Start-SPOSiteContentMove` with the `-ValidationOnly` parameter to validate if the site is able to be moved.</span></span> <span data-ttu-id="cf027-147">예:</span><span class="sxs-lookup"><span data-stu-id="cf027-147">For example:</span></span>

```PowerShell
Start-SPOSiteContentMove -SourceSiteUrl <SourceSiteUrl> -ValidationOnly -DestinationDataLocation <DestinationLocation>
```

<span data-ttu-id="cf027-148">이 경우 사이트가 이동 가능한 상태면 *성공*을 반환하고, 차단된 조건이 하나라도 있으면 *실패*를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-148">This will return *Success* if the site is ready to be moved or *Fail* if any of blocked conditions are present.</span></span>

### <a name="start-a-sharepoint-site-geo-move-for-a-site-with-no-associated-office-365-group"></a><span data-ttu-id="cf027-149">Office 365 그룹에 연결되지 않은 사이트의 SharePoint 사이트 지리적 이동 시작</span><span class="sxs-lookup"><span data-stu-id="cf027-149">Start a SharePoint site geo move for a site with no associated Office 365 Group</span></span>

<span data-ttu-id="cf027-150">기본적으로 사이트의 초기 URL이 대상 지리적 위치의 URL로 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-150">By default, initial URL for the site will change to the URL of the destination geo location.</span></span> <span data-ttu-id="cf027-151">예:</span><span class="sxs-lookup"><span data-stu-id="cf027-151">For example:</span></span>

<span data-ttu-id="cf027-152">https://Contoso.sharepoint.com/sites/projectx에서 https://ContosoEUR.sharepoint.com/sites/projectx로</span><span class="sxs-lookup"><span data-stu-id="cf027-152">https://Contoso.sharepoint.com/sites/projectx to https://ContosoEUR.sharepoint.com/sites/projectx</span></span>

<span data-ttu-id="cf027-153">Office 365 그룹에 연결되지 않은 사이트의 경우에도 `-DestinationUrl` 매개 변수를 사용하여 이름을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-153">For sites with no Office 365 Group association, you can also rename the site by using the `-DestinationUrl` parameter.</span></span> <span data-ttu-id="cf027-154">예:</span><span class="sxs-lookup"><span data-stu-id="cf027-154">For example:</span></span>

<span data-ttu-id="cf027-155">https://Contoso.sharepoint.com/sites/projectx에서 https://ContosoEUR.sharepoint.com/sites/projecty로</span><span class="sxs-lookup"><span data-stu-id="cf027-155">https://Contoso.sharepoint.com/sites/projectx to https://ContosoEUR.sharepoint.com/sites/projecty</span></span>

<span data-ttu-id="cf027-156">사이트 이동을 시작하려면 다음을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-156">To start the site move, run:</span></span>

`Start-SPOSiteContentMove -SourceSiteUrl <siteURL> -DestinationDataLocation <DestinationDataLocation> -DestinationUrl <DestinationSiteURL>`

![Start-SPOSiteContentMove cmdlet을 보여주는 PowerShell 창 스크린샷](media/multi-geo-sharepoint-site-move-powershell.png)

### <a name="start-a-sharepoint-site-geo-move-for-an-office-365-group-connected-site"></a><span data-ttu-id="cf027-158">Office 365 그룹에 연결된 사이트의 SharePoint 사이트 지리적 이동 시작</span><span class="sxs-lookup"><span data-stu-id="cf027-158">Start a SharePoint site geo move for an Office 365 Group-connected site</span></span>

<span data-ttu-id="cf027-159">Office 365 그룹에 연결된 사이트를 이동하려면 먼저 전역 관리자가 Office 365 그룹의 PDL(기본 데이터 위치) 특성을 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-159">To move an Office 365 Group-connected site, the global administrator must first change the Preferred Data Location (PDL) attribute for the Office 365 Group.</span></span>

<span data-ttu-id="cf027-160">Office 365 그룹의 PDL을 설정하려면:</span><span class="sxs-lookup"><span data-stu-id="cf027-160">To set the PDL for an Office 365 Group:</span></span>

```PowerShell
Set-SPOUnifiedGroup -PreferredDataLocation <PDL> -GroupAlias <GroupAlias>
Get-SPOUnifiedGroup -GroupAlias <GroupAlias>
```
<span data-ttu-id="cf027-161">PDL을 업데이트하고 나면 사이트 이동을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-161">Once you have updated the PDL, you can start the site move:</span></span> 

```PowerShell
Start-SPOUnifiedGroupMove -GroupAlias <GroupAlias> -DestinationDataLocation <DestinationDataLocation>
```

## <a name="cancel-a-sharepoint-site-geo-move"></a><span data-ttu-id="cf027-162">SharePoint 사이트 지리적 이동 취소</span><span class="sxs-lookup"><span data-stu-id="cf027-162">Cancel a SharePoint site geo move</span></span>

<span data-ttu-id="cf027-163">SharePoint 사이트 지리적 이동이 진행 중이거나 `Stop-SPOSiteContentMove` cmdlet을 통해 완료한 경우가 아니라면 이동을 중지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-163">You can stop a SharePoint site geo move, provided the move is not in progress or completed by using the `Stop-SPOSiteContentMove` cmdlet.</span></span>

## <a name="determining-the-status-of-a-sharepoint-site-geo-move"></a><span data-ttu-id="cf027-164">SharePoint 사이트 지리적 이동의 상태 확인</span><span class="sxs-lookup"><span data-stu-id="cf027-164">Determining the status of a SharePoint site geo move</span></span>

<span data-ttu-id="cf027-165">다음 cmdlet을 사용하면, 연결된 지역 안팎으로 이동하는 사이트의 이동 상태를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-165">You can determine the status of a site move in our out of the geo that you are connected to by using the following cmdlets:</span></span>

- <span data-ttu-id="cf027-166">[Get-SPOSiteContentMoveState](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spositecontentmovestate)(그룹에 연결되지 않은 사이트)</span><span class="sxs-lookup"><span data-stu-id="cf027-166">[Get-SPOSiteContentMoveState](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spositecontentmovestate) (non-Group-connected sites)</span></span>
- <span data-ttu-id="cf027-167">Get-SPOUnifiedGroupMoveState(그룹에 연결된 사이트)</span><span class="sxs-lookup"><span data-stu-id="cf027-167">Get-SPOUnifiedGroupMoveState (Group-connected sites)</span></span>

<span data-ttu-id="cf027-168">`-SourceSiteUrl` 매개 변수를 사용하여 이동 상태를 볼 사이트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-168">Use the `-SourceSiteUrl` parameter to specify the site for which you want to see move status.</span></span>

<span data-ttu-id="cf027-169">다음 표에는 이동 상태에 대한 설명이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-169">The move statuses are described in the following table.</span></span>

|<span data-ttu-id="cf027-170">상태</span><span class="sxs-lookup"><span data-stu-id="cf027-170">Status</span></span>|<span data-ttu-id="cf027-171">설명</span><span class="sxs-lookup"><span data-stu-id="cf027-171">Description</span></span>|
|:-----|:----------|
|<span data-ttu-id="cf027-172">트리거 준비 완료</span><span class="sxs-lookup"><span data-stu-id="cf027-172">Ready to Trigger</span></span>|<span data-ttu-id="cf027-173">이동이 시작되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-173">The move has not started.</span></span>|
|<span data-ttu-id="cf027-174">예약됨</span><span class="sxs-lookup"><span data-stu-id="cf027-174">Scheduled</span></span>|<span data-ttu-id="cf027-175">이동 작업이 큐에 있지만 아직 시작되지는 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-175">The move is in queue but has not yet started.</span></span>|
|<span data-ttu-id="cf027-176">InProgress(n/4)</span><span class="sxs-lookup"><span data-stu-id="cf027-176">InProgress (n/4)</span></span>|<span data-ttu-id="cf027-177">이동이 유효성 검사(1/4), 백업(2/4), 복원(3/4), 정리(4/4)의 네 가지 상태 중 하나로 진행 중입니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-177">The move is in progress in one of the following states: Validation (1/4), Backup (2/4), Restore (3/4), Cleanup (4/4).</span></span>|
|<span data-ttu-id="cf027-178">Success</span><span class="sxs-lookup"><span data-stu-id="cf027-178">Success</span></span>|<span data-ttu-id="cf027-179">이동이 성공적으로 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-179">The move has completed successfully.</span></span>|
|<span data-ttu-id="cf027-180">Failed</span><span class="sxs-lookup"><span data-stu-id="cf027-180">Failed</span></span>|<span data-ttu-id="cf027-181">이동이 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-181">The move failed.</span></span>|

<span data-ttu-id="cf027-182">`-Verbose` 옵션을 적용하여 이동에 대한 추가 정보를 표시할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-182">You can also apply the `-Verbose` option to see additional information about the move.</span></span>

## <a name="user-experience"></a><span data-ttu-id="cf027-183">사용자 환경</span><span class="sxs-lookup"><span data-stu-id="cf027-183">User experience</span></span>

<span data-ttu-id="cf027-184">사이트가 다른 지리적 위치로 이동해도 사이트 사용자는 영향을 별로 느끼지 못할 것입니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-184">Site users should notice minimal disruption when their site is moved to a different geo location.</span></span> <span data-ttu-id="cf027-185">이동 중에 발생하는 일시적인 읽기 전용 상태를 제외하면, 이동 후에도 기존 링크와 권한은 예상대로 계속 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-185">Aside from a brief read-only state during the move, existing links and permissions will continue to work as expected once the move is completed.</span></span>

### <a name="site"></a><span data-ttu-id="cf027-186">사이트</span><span class="sxs-lookup"><span data-stu-id="cf027-186">Site</span></span>

<span data-ttu-id="cf027-187">이동이 진행 중일 때 사이트는 읽기 전용으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-187">While the move is in progress the site is set to read-only.</span></span> <span data-ttu-id="cf027-188">이동이 완료된 후, 책갈피를 클릭하거나 사이트로 연결하는 다른 링크를 클릭하면 사용자가 새 지리적 위치의 새 사이트로 리디렉션됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-188">Once the move is completed, the user is directed to the new site in the new geo location when they click on bookmarks or other links to the site.</span></span>

### <a name="permissions"></a><span data-ttu-id="cf027-189">권한</span><span class="sxs-lookup"><span data-stu-id="cf027-189">Permissions</span></span>

<span data-ttu-id="cf027-190">이동하는 동안 그리고 완료된 후, 사이트에 대한 권한이 있는 사용자는 해당 사이트에 계속 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-190">Users with permissions to site will continue to have access to the site during the move and after it's complete.</span></span>

### <a name="sync-client"></a><span data-ttu-id="cf027-191">동기화 클라이언트</span><span class="sxs-lookup"><span data-stu-id="cf027-191">Sync Client</span></span>

<span data-ttu-id="cf027-192">사이트 이동이 완료되고 나면 동기화 클라이언트가 자동 검색 후 원활하게 새 사이트 위치와의 동기화를 전송합니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-192">The sync client will automatically detect and seamlessly transfer syncing to the new site location once the site move is complete.</span></span> <span data-ttu-id="cf027-193">사용자가 다시 로그인하거나 다른 조치를 취할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-193">The user does not need to sign in again or take any other action.</span></span> <span data-ttu-id="cf027-194">동기화 클라이언트 버전 17.3.6943.0625 이상이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-194">(Version 17.3.6943.0625 or later of the sync client required.)</span></span>

<span data-ttu-id="cf027-195">이동이 진행되는 동안 사용자가 파일을 업데이트하는 경우 동기화 클라이언트는 이동이 진행되는 동안에는 파일 업로드가 보류된다는 사실을 알려줍니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-195">If a user updates a file while the move is in progress, the sync client will notify them that file uploads are pending while the move is underway.</span></span>

### <a name="sharing-links"></a><span data-ttu-id="cf027-196">링크 공유</span><span class="sxs-lookup"><span data-stu-id="cf027-196">Sharing links</span></span>

<span data-ttu-id="cf027-197">SharePoint 사이트 지리적 이동이 완료되면, 이동한 파일의 기존 공유 링크가 새로운 지리적 위치로 자동으로 리디렉션됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-197">When the SharePoint site geo move completes, the existing shared links for the files that were moved will automatically redirect to the new geo location.</span></span>

### <a name="most-recently-used-files-in-office-mru"></a><span data-ttu-id="cf027-198">Office에서 MRU(최근에 사용한) 파일</span><span class="sxs-lookup"><span data-stu-id="cf027-198">Most Recently Used files in Office (MRU)</span></span>

<span data-ttu-id="cf027-199">이동이 완료되면 MRU 서비스의 사이트 URL과 해당 콘텐츠 URL이 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-199">The MRU service is updated with the site url and its content URLs once the move completes.</span></span> <span data-ttu-id="cf027-200">이는 Word, Excel, PowerPoint에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-200">This applies to Word, Excel, and PowerPoint.</span></span>

### <a name="onenote-experience"></a><span data-ttu-id="cf027-201">OneNote 환경</span><span class="sxs-lookup"><span data-stu-id="cf027-201">OneNote experience</span></span>

<span data-ttu-id="cf027-202">사이트 이동이 완료되고 나면 OneNote Win32 클라이언트와 UWP(유니버설) 앱이 자동 검색 후 전자 필기장을 원활하게 새 사이트 위치에 동기화합니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-202">OneNote win32 client and UWP (Universal) App will automatically detect and seamlessly sync notebooks to the new site location once site move is complete.</span></span> <span data-ttu-id="cf027-203">사용자가 다시 로그인하거나 다른 조치를 취할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-203">The user does not need to sign in again or take any other action.</span></span> <span data-ttu-id="cf027-204">사이트 이동이 진행 중일 때 사용자에게 보이는 유일한 표시는 전자 필기장 동기화 실패 표시입니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-204">The only visible indicator to the user is notebook sync would fail when site move is in progress.</span></span> <span data-ttu-id="cf027-205">이 환경은 다음 OneNote 클라이언트 버전에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-205">This experience is available on the following OneNote client versions:</span></span>

- <span data-ttu-id="cf027-206">OneNote win32 - 버전 16.0.8326.2096 이상</span><span class="sxs-lookup"><span data-stu-id="cf027-206">OneNote win32 – Version 16.0.8326.2096 (and later)</span></span>
- <span data-ttu-id="cf027-207">OneNote UWP - 버전 16.0.8431.1006 이상</span><span class="sxs-lookup"><span data-stu-id="cf027-207">OneNote UWP – Version 16.0.8431.1006 (and later)</span></span>
- <span data-ttu-id="cf027-208">OneNote 모바일 앱 - 버전 16.0.8431.1011 이상</span><span class="sxs-lookup"><span data-stu-id="cf027-208">OneNote Mobile App – Version 16.0.8431.1011 (and later)</span></span>

### <a name="teams-applicable-to-office-365-group-connected-sites"></a><span data-ttu-id="cf027-209">Teams(Office 365 그룹에 연결된 사이트에 적용 가능)</span><span class="sxs-lookup"><span data-stu-id="cf027-209">Teams (applicable to Office 365 Group connected sites)</span></span>

<span data-ttu-id="cf027-210">SharePoint 사이트 지리적 이동이 완료되면 사용자가 Teams 앱의 Office 365 그룹 사이트 파일에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-210">When the SharePoint site geo move completes, users will have access to their Office 365 Group site files on the Teams app.</span></span> <span data-ttu-id="cf027-211">또한 지리적 이동 이전에 사이트의 Teams 채팅을 통해 공유한 파일은 이동이 완료되 후 계속해서 사용 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-211">Additionally, files shared via Teams chat from their site prior to geo move will continue to work after move is complete.</span></span>

### <a name="sharepoint-mobile-app-iosandroid"></a><span data-ttu-id="cf027-212">SharePoint 모바일 앱(iOS/Android)</span><span class="sxs-lookup"><span data-stu-id="cf027-212">SharePoint Mobile App (iOS/Android)</span></span>

<span data-ttu-id="cf027-213">SharePoint Mobile 앱은 지역 간에 호환되며 사이트의 새 지리적 위치를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-213">The SharePoint Mobile App is cross geo compatible and able to detect the site's new geo location.</span></span>

### <a name="sharepoint-workflows"></a><span data-ttu-id="cf027-214">SharePoint 워크플로</span><span class="sxs-lookup"><span data-stu-id="cf027-214">SharePoint workflows</span></span>

<span data-ttu-id="cf027-215">사이트가 이동하고 나면 SharePoint 2013 워크플로를 다시 게시해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-215">SharePoint 2013 workflows need to be republished after the site move.</span></span> <span data-ttu-id="cf027-216">SharePoint 2010 워크플로는 계속해서 정상적으로 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-216">SharePoint 2010 workflows should continue to function normally.</span></span>

### <a name="apps"></a><span data-ttu-id="cf027-217">앱</span><span class="sxs-lookup"><span data-stu-id="cf027-217">Apps</span></span>

<span data-ttu-id="cf027-218">앱이 포함된 사이트를 이동하는 경우, 대상 지리적 위치에서 앱과 연결을 사용하지 못할 수 있으므로 사이트의 새 지리적 위치에서 앱을 다시 인스턴스화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-218">If you are moving a site with apps, you must re-instantiate the app in the site's new geo location as the app and its connections may not be available in the destination geo location.</span></span>

### <a name="flow"></a><span data-ttu-id="cf027-219">흐름</span><span class="sxs-lookup"><span data-stu-id="cf027-219">Flow</span></span>

<span data-ttu-id="cf027-220">대부분의 경우 SharePoint 사이트 지리적 이동 후에도 흐름이 계속해서 정상적으로 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-220">In most cases Flows will continue to work after a SharePoint site geo move.</span></span> <span data-ttu-id="cf027-221">이동이 완료되면 한 번 테스트하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-221">We recommend that you test them once the move has completed.</span></span>

### <a name="powerapps"></a><span data-ttu-id="cf027-222">PowerApps</span><span class="sxs-lookup"><span data-stu-id="cf027-222">PowerApps</span></span>

<span data-ttu-id="cf027-223">대상 위치에 PowerApps를 다시 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-223">PowerApps need to be recreated in the destination location.</span></span>

### <a name="data-movement-between-geo-locations"></a><span data-ttu-id="cf027-224">지리적 위치 간 데이터 이동</span><span class="sxs-lookup"><span data-stu-id="cf027-224">Data movement between geo locations</span></span>

<span data-ttu-id="cf027-225">SharePoint는 콘텐츠를 Azure Blob Storage에 저장하고, 사이트 및 파일과 연결된 메타데이터는 SharePoint 내에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-225">SharePoint uses Azure Blob storage for its content, while the metadata associated with sites and its files is stored within SharePoint.</span></span> <span data-ttu-id="cf027-226">사이트가 원본 지리적 위치에서 대상 지리적 위치로 이동하고 나면, 서비스도 그와 연결된 Blob Storage를 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-226">After the site is moved from its source geo location to its destination geo location, the service will also move its associated Blob Storage.</span></span> <span data-ttu-id="cf027-227">Blob Storage 이동은 약 40일 후에 완료됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf027-227">Blob Storage moves complete in approximately 40 days.</span></span> 
