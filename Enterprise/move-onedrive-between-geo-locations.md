---
title: OneDrive 사이트를 다른 지리적 위치로 이동
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: OneDrive 사이트를 다른 지리적 위치로 이동하는 방법을 알아봅니다.
ms.openlocfilehash: 6bac98cc0707f977b7b585e8ae0a570f4b9662ee
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/27/2018
---
# <a name="move-a-onedrive-site-to-a-different-geo-location"></a><span data-ttu-id="24917-103">OneDrive 사이트를 다른 지리적 위치로 이동</span><span class="sxs-lookup"><span data-stu-id="24917-103">Move a OneDrive site to a different geo-location</span></span> 

<span data-ttu-id="24917-p101">OneDrive 지리적 이동을 사용하면 사용자의 OneDrive를 다른 지리적 위치로 이동할 수 있습니다. OneDrive 지리적 이동은 SharePoint Online 관리자 또는 Office 365 전역 관리자가 수행합니다. OneDrive 지리적 이동을 시작하기 전에 OneDrive을 이동할 사용자에게 알리고 이동하는 동안 모든 파일을 닫도록 권유합니다. (이동하는 동안 Office 클라이언트를 사용하여 문서를 열어 둔 경우 이동이 완료된 후에 문서를 새 위치에 저장해야 합니다.) 원할 경우 나중에 이동하도록 예약할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24917-p101">With OneDrive geo move, you can move a user’s OneDrive to a different geo location. OneDrive geo move is performed by the SharePoint Online administrator or the Office 365 global administrator. Before you start a OneDrive geo move, be sure to notify the user whose OneDrive is being moved and recommend they close all files for the duration of the move. (If the user has a document open using the Office client during the move, then upon move completion the document will need to be saved to the new location.) The move can be scheduled for a future time, if desired.</span></span>

<span data-ttu-id="24917-p102">OneDrive 서비스는 Azure Blob 저장소를 사용하여 콘텐츠를 저장합니다. 사용자의 OneDrive와 연결된 Storage Blob는 대상 OneDrive를 사용할 수 있게 되고 40일 이내에 원본에서 대상 지리적 위치로 이동됩니다. 사용자의 OneDrive에 대한 액세스 권한은 대상 OneDrive가 사용할 수 있게 되는 즉시 복원됩니다.</span><span class="sxs-lookup"><span data-stu-id="24917-p102">The OneDrive service uses Azure Blob Storage to store content. The Storage blob associated with the user’s OneDrive will be moved from the source to destination geo location within 40 days of destination OneDrive being available to the user. The access to the user’s OneDrive will be restored as soon as the destination OneDrive is available.</span></span>

<span data-ttu-id="24917-p103">OneDrive 지리적 이동 기간(약 2 ~ 6시간) 동안 사용자의 OneDrive는 읽기 전용으로 설정됩니다. 사용자는 OneDrive 동기화 클라이언트 또는 SharePoint Online의 OneDrive 사이트를 통해 해당 파일에 계속 액세스할 수 있습니다. OneDrive 지리적 이동이 완료되면 사용자는 Office 365 앱 시작 관리자에서 OneDrive로 이동할 때 대상 지리적 위치에 자동으로 연결됩니다. 동기화 클라이언트는 자동으로 새 위치에서 동기화를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="24917-p103">During OneDrive geo move window (about 2-6 hours) the user's OneDrive is set to read-only. The user can still access their files via the OneDrive sync client or their OneDrive site in SharePoint Online. After OneDrive geo move is complete, the user will be automatically connected to their OneDrive at the destination geo location when they navigate to OneDrive in the Office 365 app launcher. The sync client will automatically begin syncing from the new location.</span></span>

<span data-ttu-id="24917-115">이 문서에 나오는 절차를 수행하려면 [Microsoft SharePoint Online PowerShell 모듈](https://www.microsoft.com/en-us/download/details.aspx?id=35588)이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="24917-115">The procedures in this article require the [Microsoft SharePoint Online PowerShell Module](https://www.microsoft.com/en-us/download/details.aspx?id=35588).</span></span>

## <a name="moving-a-onedrive-site"></a><span data-ttu-id="24917-116">OneDrive 사이트 이동</span><span class="sxs-lookup"><span data-stu-id="24917-116">Moving a OneDrive site</span></span>

<span data-ttu-id="24917-p104">OneDrive 지리적 이동을 수행하려면 테넌트 관리자는 먼저 사용자의 PDL(기본 설정 데이터 위치)을 해당 지리적 위치로 설정해야 합니다. PDL이 설정되면 OneDrive 지리적 이동을 시작하기 전에 PDL 업데이트가 지리적 위치 간에 동기화될 때까지 24시간 이상 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="24917-p104">To perform a OneDrive geo move, the tenant administrator must first set the user’s Preferred Data Location (PDL) to the appropriate geo location. Once the PDL is set, wait for at least 24 hours for the PDL update to sync across the geo locations before starting the OneDrive geo move.</span></span>

<span data-ttu-id="24917-119">지리적 이동 cmdlet을 사용할 경우 다음 구문을 사용하여 사용자의 현재 OneDrive 지리적 위치에 있는 SPO 서비스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="24917-119">When using the geo move cmdlets, connect to SPO Service at the user’s current OneDrive geo location, using the following syntax:</span></span>

`connect-sposervice -url https://<tenantName>-admin.sharepoint.com`

<span data-ttu-id="24917-120">예를 들어, 'Matt@contosoenergy.onmicrosoft.com' 사용자의 OneDrive를 이동하려면 이 사용자의 OneDrive는 EUR 지리적 위치에 있으므로 EUR SharePoint 관리 센터에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="24917-120">For example: To move OneDrive of user ‘Matt@contosoenergy.onmicrosoft.com’, connect to EUR SharePoint Admin center as the user’s OneDrive is in EUR geo location:</span></span>

`connect-sposervice -url https://contosoenergyeur-admin.sharepoint.com`

![](media/move-onedrive-between-geo-locations_image1.png)

## <a name="validating-the-environment"></a><span data-ttu-id="24917-121">환경 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="24917-121">Validating the environment</span></span>

<span data-ttu-id="24917-122">OneDrive 지리적 이동을 시작하기 전에 환경이 유효한지 검사하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="24917-122">Before you start a OneDrive geo move, we recommend that you validate the environment.</span></span>

<span data-ttu-id="24917-123">모든 지리적 위치가 호환되는지 확인하려면 다음을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="24917-123">To ensure that all geo locations are compatible, run:</span></span>

`Get-SPOGeoMoveCompatibilityStatus -AllLocations 1`

<span data-ttu-id="24917-p105">OneDrive가 법적 보존 상태이거나 하위 사이트가 포함되어 있으면 이동할 수 없습니다. -ValidationOnly 매개 변수와 함께 Start-SPOUserAndContentMove cmdlet을 사용하여 OneDrive를 이동할 수 있는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24917-p105">If a OneDrive is under legal hold or if it contains a subsite, it cannot be moved. You can use the Start-SPOUserAndContentMove cmdlet with the -ValidationOnly parameter to validate if the OneDrive is able to be moved:</span></span>

`Start-SPOUserAndContentMove -UserPrincipalName <UPN> -DestinationDataLocation <DestinationDataLocation> -ValidationOnly`

<span data-ttu-id="24917-p106">OneDrive를 이동할 준비가 되었으면 Success, 법적 보존 상태이거나 하위 사이트가 포함되어 있어서 이동할 수 없으면 Fail이 반환됩니다. OneDrive를 이동할 준비가 되어 있는지 확인한 후에는 이동을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24917-p106">This will return Success if the OneDrive is ready to be moved or Fail if there is a legal hold or subsite that would prevent the move. Once you have validated that the OneDrive is ready to move, you can start the move.</span></span>

## <a name="start-a-onedrive-geo-move"></a><span data-ttu-id="24917-128">OneDrive 지리적 이동 시작</span><span class="sxs-lookup"><span data-stu-id="24917-128">Start a OneDrive geo move</span></span>

<span data-ttu-id="24917-129">이동을 시작하려면 다음을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="24917-129">To start the move, run:</span></span>  

`Start-SPOUserAndContentMove -UserPrincipalName <UserPrincipalName> -DestinationDataLocation <DestinationDataLocation>`

<span data-ttu-id="24917-130">다음 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="24917-130">Using these parameters:</span></span>

-   <span data-ttu-id="24917-131">_UserPrincipalName_ - OneDrive을 이동할 사용자의 UPN입니다.</span><span class="sxs-lookup"><span data-stu-id="24917-131">_UserPrincipalName_ – UPN of the user whose OneDrive is being moved.</span></span>

-   <span data-ttu-id="24917-p107">_DestinationDataLocation_ - OneDrive를 이동해야 하는 지리적 위치입니다. 사용자의 기본 설정 데이터 위치와 동일해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="24917-p107">_DestinationDataLocation_ – Geo-Location where the OneDrive needs to be moved. This should be same as the user’s preferred data location.</span></span>

> [!NOTE]
> <span data-ttu-id="24917-134">OneDrive 지리적 이동을 시작하기 전에 `ValidationOnly`를 사용하여 `Get-SPOGeoMoveStateCompatibility`를 실행하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="24917-134">We recommend running `Get-SPOGeoMoveStateCompatibility` with `ValidationOnly` prior to initiating OneDrive geo move.</span></span>

<span data-ttu-id="24917-135">예를 들어, matt@contosoenergy.onmicrosoft.com의 OneDrive를 EUR에서 AUS로 이동하려면 다음을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="24917-135">For example, to move the OneDrive of matt@contosoenergy.onmicrosoft.com from EUR to AUS, run:</span></span>

`Start-SPOUserAndContentMove -UserPrincipalName matt@contosoenergy.onmicrosoft.com -DestinationDataLocation AUS`

![](media/move-onedrive-between-geo-locations_image2.png)

<span data-ttu-id="24917-136">지리적 이동을 나중을 수행하기 위해 예약하려면 다음 매개 변수 중 하나를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="24917-136">To schedule a geo move for a later time, use one of the following parameters:</span></span>

-   <span data-ttu-id="24917-p108">_PreferredMoveBeginDate_ – 이 지정된 시간에 이동이 시작되게 됩니다. 시간은 UTC(협정 세계시)로 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="24917-p108">_PreferredMoveBeginDate_ – The move will likely begin at this specified time. Time must be specified in Coordinated Universal Time (UTC).</span></span>

-   <span data-ttu-id="24917-p109">_PreferredMoveEndDate_ – 이 지정된 시간에 최상의 노력 방식으로 이동이 완료되게 됩니다. 시간은 UTC(협정 세계시)로 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="24917-p109">_PreferredMoveEndDate_ – The move will likely be completed by this specified time, on a best effort basis. Time must be specified in Coordinated Universal Time (UTC).</span></span> 

## <a name="cancel-a-onedrive-geo-move"></a><span data-ttu-id="24917-141">OneDrive 지리적 이동 취소</span><span class="sxs-lookup"><span data-stu-id="24917-141">Cancel a OneDrive geo move</span></span> 

<span data-ttu-id="24917-142">사용자 OneDrive의 지리적 이동이 진행 중이거나 cmdlet을 통해 완료된 경우가 아니면 이동을 중지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24917-142">You can stop the geo move of a user’s OneDrive, provided the move is not in progress or completed by using the cmdlet:</span></span>

`Stop-SPOUserAndContentMove – UserPrincipalName <UserPrincipalName>`

<span data-ttu-id="24917-143">여기서 _UserPrincipalName_은 OneDrive 이동을 중지하려는 사용자의 UPN입니다.</span><span class="sxs-lookup"><span data-stu-id="24917-143">Where _UserPrincipalName_ is the UPN of the user whose OneDrive move you want to stop.</span></span>

## <a name="determining-current-status"></a><span data-ttu-id="24917-144">현재 상태 확인</span><span class="sxs-lookup"><span data-stu-id="24917-144">Determining current status</span></span>

<span data-ttu-id="24917-145">Get-SPOUserAndContentMoveState cmdlet을 사용하여 연결된 지리적 위치로 들어오거나 해당 위치에서 나가는 OneDrive 지리적 이동의 상태를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24917-145">You can check the status of a OneDrive geo move in or out of the geo that you’re connected to by using the Get-SPOUserAndContentMoveState cmdlet.</span></span>

<span data-ttu-id="24917-146">다음 표에는 이동 상태에 대한 설명이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24917-146">The fields in alerts are described in the following table.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="24917-147"><strong>상태</strong></span><span class="sxs-lookup"><span data-stu-id="24917-147"><strong>Status</strong></span></span></th>
<th align="left"><span data-ttu-id="24917-148"><strong>설명</strong></span><span class="sxs-lookup"><span data-stu-id="24917-148"><strong>Description</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="24917-149">NotStarted</span><span class="sxs-lookup"><span data-stu-id="24917-149">NotStarted</span></span></td>
<td align="left"><span data-ttu-id="24917-150">이동이 시작되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="24917-150">The move has not started.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="24917-151">InProgress(<em>n</em>/4)</span><span class="sxs-lookup"><span data-stu-id="24917-151">InProgress (<em>n</em>/4)</span></span></td>
<td align="left"><span data-ttu-id="24917-152">이동이 유효성 검사(1/4), 백업(2/4), 복원(3/4), 정리(4/4)의 네 가지 상태 중 하나로 진행 중입니다.</span><span class="sxs-lookup"><span data-stu-id="24917-152">The move is in progress in one of the following states: Validation (1/4), Backup (2/4), Restore (3/4), Cleanup (4/4).</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="24917-153">Success</span><span class="sxs-lookup"><span data-stu-id="24917-153">Success</span></span></td>
<td align="left"><span data-ttu-id="24917-154">이동이 성공적으로 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="24917-154">The move has completed successfully.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="24917-155">Failed</span><span class="sxs-lookup"><span data-stu-id="24917-155">Failed</span></span></td>
<td align="left"><span data-ttu-id="24917-156">이동이 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="24917-156">The move failed.</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="24917-157">특정 사용자 이동의 상태를 확인하려면 UserPrincipalName 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="24917-157">To find the status of a specific user’s move, use the UserPrincipalName parameter:</span></span>

`Get-SPOUserAndContentMoveState -UserPrincipalName <UPN>`

<span data-ttu-id="24917-158">연결된 지리적 위치로 들어오거나 해당 위치에서 나가는 모든 이동의 상태를 확인하려면 NotStarted, InProgress, Success, Failed, All 값 중 하나를 갖는 MoveState 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="24917-158">To find the status of all of the moves in or out of the geo location that you’re connected to, use the MoveState parameter with one of the following values: NotStarted, InProgress, Success, Failed, All.</span></span>

`Get-SPOUserAndContentMoveState -MoveState <value>`

<span data-ttu-id="24917-159">이동 상태에 대한 좀 더 자세한 설명을 보려면 `-Verbose` 매개 변수를 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24917-159">You can also add the `-Verbose` parameter for more verbose descriptions of the move state.</span></span>

## <a name="user-experience"></a><span data-ttu-id="24917-160">사용자 환경</span><span class="sxs-lookup"><span data-stu-id="24917-160">User Experience</span></span>

<span data-ttu-id="24917-p110">OneDrive 사용자는 OneDrive가 다른 지리적 위치로 이동될 경우 최소한의 작업 중단이 발생한다는 것을 알 수 있습니다. 이동하는 동안 잠깐 읽기 전용 상태가 되지만 이동이 완료되면 링크 및 사용 권한은 예상대로 계속 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="24917-p110">Users of OneDrive should notice minimal disruption if their OneDrive is moved to a different geo location. Aside from a brief read-only state during the move, existing links and permissions will continue to work as expected once the move is completed.</span></span>

### <a name="onedrive-for-business"></a><span data-ttu-id="24917-163">비즈니스용 OneDrive</span><span class="sxs-lookup"><span data-stu-id="24917-163">OneDrive for Business</span></span>

<span data-ttu-id="24917-p111">이동이 진행되는 동안 사용자의 OneDrive는 읽기 전용으로 설정됩니다. 이동이 완료된 후 Office 365 앱 시작 관리자 또는 웹 브라우저에서 OneDrive로 가면 새 지리적 위치의 OneDrive로 이동됩니다.</span><span class="sxs-lookup"><span data-stu-id="24917-p111">While the move is in progress the user’s OneDrive is set to read-only. Once the move is completed, the user is directed to their OneDrive in the new geo location when they navigate to OneDrive the Office 365 app launcher or a web browser.</span></span>

### <a name="permissions-on-onedrive-content"></a><span data-ttu-id="24917-166">OneDrive 콘텐츠에 대한 사용 권한</span><span class="sxs-lookup"><span data-stu-id="24917-166">Permissions on OneDrive content</span></span>

<span data-ttu-id="24917-167">이동하는 동안 및 완료된 후, OneDrive 콘텐츠에 대해 사용 권한이 있는 사용자는 해당 콘텐츠에 계속 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24917-167">Users with permissions to OneDrive content will continue to have access to the content during the move and after it’s complete.</span></span>

### <a name="onedrive-sync-client"></a><span data-ttu-id="24917-168">OneDrive 동기화 클라이언트</span><span class="sxs-lookup"><span data-stu-id="24917-168">OneDrive Sync Client</span></span> 

<span data-ttu-id="24917-p112">OneDrive 동기화 클라이언트는 OneDrive 지리적 이동이 완료되면 새 OneDrive 위치를 자동으로 감지하고, 해당 위치에 대한 동기화로 원활하게 전환합니다. 따라서 사용자가 다시 로그인하거나 다른 작업을 수행할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="24917-p112">The OneDrive sync client will automatically detect and seamlessly transfer syncing to the new OneDrive location once the OneDrive geo move is complete. The user does not need to sign-in again or take any other action.</span></span>

<span data-ttu-id="24917-171">OneDrive 지리적 이동이 진행되는 동안 사용자가 파일을 업데이트하는 경우 동기화 클라이언트는 이동이 진행 중일 때 파일 업로드가 보류된다는 사실을 알립니다.</span><span class="sxs-lookup"><span data-stu-id="24917-171">If a user updates a file while the OneDrive geo move is in progress, the sync client will notify them that file uploads are pending while the move is underway.</span></span>

### <a name="sharing-links"></a><span data-ttu-id="24917-172">링크 공유</span><span class="sxs-lookup"><span data-stu-id="24917-172">Sharing links</span></span> 

<span data-ttu-id="24917-173">OneDrive 지리적 이동이 완료되면, 이동된 파일에 대한 기본 공유 링크가 새 위치로 자동으로 리디렉션됩니다.</span><span class="sxs-lookup"><span data-stu-id="24917-173">Upon OneDrive geo move completion, the existing shared links for the files that were moved will automatically redirect to the new geo location.</span></span>

### <a name="onenote-experience"></a><span data-ttu-id="24917-174">OneNote 환경</span><span class="sxs-lookup"><span data-stu-id="24917-174">OneNote Experience</span></span> 

<span data-ttu-id="24917-p113">OneNote win32 클라이언트 및 UWP(유니버설) 앱은 OneDrive 지리적 이동이 완료되면 새 OneDrive 위치를 자동으로 감지하고 전자 필기장을 원활하게 동기화합니다. 따라서 사용자가 다시 로그인하거나 다른 작업을 수행할 필요가 없습니다. 사용자에게 OneDrive 지리적 이동이 진행 중일 때 전자 필기장 동기화가 실패한다는 알림만 표ㅕ시됩니다. 이러한 환경은 다음 OneNote 클라이언트 버전에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24917-p113">OneNote win32 client and UWP (Universal) App will automatically detect and seamlessly sync notebooks to the new OneDrive location once OneDrive geo move is complete. The user does not need to sign-in again or take any other action. The only visible indicator to the user is notebook sync would fail when OneDrive geo move is in progress. This experience is available on the following OneNote client versions:</span></span>

-   <span data-ttu-id="24917-179">OneNote win32 - 버전 16.0.8326.2096 이상</span><span class="sxs-lookup"><span data-stu-id="24917-179">OneNote win32 – Version 16.0.8326.2096 (and later)</span></span>

-   <span data-ttu-id="24917-180">OneNote UWP - 버전 16.0.8431.1006 이상</span><span class="sxs-lookup"><span data-stu-id="24917-180">OneNote UWP – Version 16.0.8431.1006 (and later)</span></span>

-   <span data-ttu-id="24917-181">OneNote 모바일 앱 - 버전 16.0.8431.1011 이상</span><span class="sxs-lookup"><span data-stu-id="24917-181">OneNote Mobile App – Version 16.0.8431.1011 (and later)</span></span>

### <a name="teams-app"></a><span data-ttu-id="24917-182">Teams 앱</span><span class="sxs-lookup"><span data-stu-id="24917-182">Teams app</span></span>

<span data-ttu-id="24917-p114">OneDrive 지리적 이동이 완료되면, Teams 앱의 해당 OneDrive 파일에 액세스할 수 있게 됩니다. 또한 지리적 이동 적에 해당 OneDrive에서 Teams 앱을 통해 공유한 파일은 이동이 완료된 후에도 계속 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="24917-p114">Upon OneDrive geo move completion, users will have access to their OneDrive files on the Teams app. Additionally, files shared via Teams chat from their OneDrive prior to geo move will continue to work after move is complete.</span></span>

### <a name="onedrive-for-business-mobile-app-ios"></a><span data-ttu-id="24917-185">비즈니스용 OneDrive 모바일 앱(iOS)</span><span class="sxs-lookup"><span data-stu-id="24917-185">OneDrive for Business Mobile App (iOS)</span></span> 

<span data-ttu-id="24917-186">OneDrive 지리적 이동이 완료되면, 사용자는 iOS 모바일 앱에서 로그아웃했다가 다시 로그인하여 새 OneDrive 위치와 동기화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="24917-186">Upon OneDrive geo move completion, the user would need to sign out and sign in again on the iOS Mobile App to sync to the new OneDrive location.</span></span>

### <a name="existing-followed-groups-and-sites"></a><span data-ttu-id="24917-187">기존의 팔로우된 그룹 및 사이트</span><span class="sxs-lookup"><span data-stu-id="24917-187">Existing followed groups and sites</span></span>

<span data-ttu-id="24917-p115">팔로우된 사이트 및 그룹은 해당 지리적 위치에 관계없이 사용자의 비즈니스용 OneDrive에 표시됩니다. 다른 지리적 위치에서 호스트된 사이트 및 그룹은 별도 탭에서 열립니다.</span><span class="sxs-lookup"><span data-stu-id="24917-p115">Followed sites and groups will show up in the user's OneDrive for business regardless of their geo location. Sites and Groups hosted in another geo location will open in a separate tab.</span></span>
