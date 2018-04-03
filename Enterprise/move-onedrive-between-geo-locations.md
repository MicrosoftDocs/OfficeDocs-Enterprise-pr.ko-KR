---
title: OneDrive 사이트를 다른 지리적 위치를 이동
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: OneDrive 사이트를 다른 지리적 위치로 이동 하는 방법에 알아봅니다.
ms.openlocfilehash: a31f683170fdb83dac90e9d09884c3020d1a47b1
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/03/2018
---
# <a name="move-a-onedrive-site-to-a-different-geo-location"></a><span data-ttu-id="7ccb0-103">OneDrive 사이트를 다른 지리적 위치를 이동</span><span class="sxs-lookup"><span data-stu-id="7ccb0-103">Move a OneDrive site to a different geo-location</span></span> 

<span data-ttu-id="7ccb0-p101">지리적으로 분산 이동, OneDrive와 사용자의 OneDrive 다른 지리적 위치를 이동할 수 있습니다. OneDrive 지리적으로 분산 이동 Office 365 전역 관리자 또는 SharePoint Online 관리자가 수행 됩니다. 지리적으로 분산 이동 OneDrive를 시작 하기 전에 해야 해당 OneDrive를 이동 하는 사용자에 게 알리고 이동의 기간에 대 한 파일을 모두 닫고 자신이 하는 것이 좋습니다. (사용자에 게 하는 경우에 따라 다음 이동 하는 동안 Office 클라이언트를 사용 하 여 문서를 연 이동 완료 문서의 새 위치에 저장 해야 합니다.) 원하는 경우에 나중에 대 한 이동을 예약할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ccb0-p101">With OneDrive geo move, you can move a user’s OneDrive to a different geo location. OneDrive geo move is performed by the SharePoint Online administrator or the Office 365 global administrator. Before you start a OneDrive geo move, be sure to notify the user whose OneDrive is being moved and recommend they close all files for the duration of the move. (If the user has a document open using the Office client during the move, then upon move completion the document will need to be saved to the new location.) The move can be scheduled for a future time, if desired.</span></span>

<span data-ttu-id="7ccb0-p102">Azure Blob 저장소를 사용 하 여 콘텐츠를 저장 하는 OneDrive 서비스입니다. 사용자의 OneDrive와 연결 된 저장소 blob 이동할 원본에서 대상 지리적 위치에 대상 사용자에 게 제공 되는 OneDrive의 40 일 이내입니다. 대상 OneDrive를 사용할 수는 즉시 사용자의 OneDrive에 대 한 액세스를 복원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ccb0-p102">The OneDrive service uses Azure Blob Storage to store content. The Storage blob associated with the user’s OneDrive will be moved from the source to destination geo location within 40 days of destination OneDrive being available to the user. The access to the user’s OneDrive will be restored as soon as the destination OneDrive is available.</span></span>

<span data-ttu-id="7ccb0-p103">OneDrive 지리적으로 분산 이동 창 (약 2-6 시간) 하는 동안 사용자의 OneDrive 설정은 읽기 전용으로 설정 합니다. 사용자는 OneDrive 동기화 클라이언트 또는 SharePoint Online에서 자신의 OneDrive 사이트를 통해 해당 파일에 계속 액세스할 수 있습니다. OneDrive 지리적으로 분산 이동을 완료 되 면 사용자가 자동으로 연결할 수 대상 지리적 위치에 자신의 OneDrive Office 365 응용 프로그램 시작 관리자의 OneDrive을 탐색할 때. 동기화 클라이언트는 새 위치에서 동기화 하는 중에 자동으로 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ccb0-p103">During OneDrive geo move window (about 2-6 hours) the user's OneDrive is set to read-only. The user can still access their files via the OneDrive sync client or their OneDrive site in SharePoint Online. After OneDrive geo move is complete, the user will be automatically connected to their OneDrive at the destination geo location when they navigate to OneDrive in the Office 365 app launcher. The sync client will automatically begin syncing from the new location.</span></span>

<span data-ttu-id="7ccb0-115">이 문서의 절차에는 [Microsoft SharePoint Online PowerShell 모듈](https://www.microsoft.com/en-us/download/details.aspx?id=35588)필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ccb0-115">The procedures in this article require the [Microsoft SharePoint Online PowerShell Module](https://www.microsoft.com/en-us/download/details.aspx?id=35588).</span></span>

## <a name="moving-a-onedrive-site"></a><span data-ttu-id="7ccb0-116">OneDrive 사이트를 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="7ccb0-116">Moving a OneDrive site</span></span>

<span data-ttu-id="7ccb0-p104">지리적으로 분산 이동, 프로그램 OneDrive를 수행 하려면 적절 한 지리적 위치로 테 넌 트 관리자가 사용자의 기본 설정 데이터 위치 (PDL)를 먼저 설정 해야 합니다. PDL가 설정 되 면 OneDrive 지리적으로 분산 이동을 시작 하기 전에 여러 지리적 위치에 걸친 동기화 할 PDL 업데이트에 대 한 최소 24 시간까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="7ccb0-p104">To perform a OneDrive geo move, the tenant administrator must first set the user’s Preferred Data Location (PDL) to the appropriate geo location. Once the PDL is set, wait for at least 24 hours for the PDL update to sync across the geo locations before starting the OneDrive geo move.</span></span>

<span data-ttu-id="7ccb0-119">지리적으로 분산을 사용 하 여 cmdlet를 이동 하는 경우 다음 구문을 사용 하 여 사용자의 현재 OneDrive 지리적 위치에 SPO 서비스에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ccb0-119">When using the geo move cmdlets, connect to SPO Service at the user’s current OneDrive geo location, using the following syntax:</span></span>

`connect-sposervice -url https://<tenantName>-admin.sharepoint.com`

<span data-ttu-id="7ccb0-120">예: 'Matt@contosoenergy.onmicrosoft.com' 사용자의 OneDrive를 이동 하려면 연결 EUR SharePoint 관리 센터에는 사용자의 OneDrive EUR 지리적 위치에 있는 그대로:</span><span class="sxs-lookup"><span data-stu-id="7ccb0-120">For example: To move OneDrive of user ‘Matt@contosoenergy.onmicrosoft.com’, connect to EUR SharePoint Admin center as the user’s OneDrive is in EUR geo location:</span></span>

`connect-sposervice -url https://contosoenergyeur-admin.sharepoint.com`

![](media/move-onedrive-between-geo-locations_image1.png)

## <a name="validating-the-environment"></a><span data-ttu-id="7ccb0-121">유효성을 검사 하는 환경</span><span class="sxs-lookup"><span data-stu-id="7ccb0-121">Validating the environment</span></span>

<span data-ttu-id="7ccb0-122">시작 하기 전에 OneDrive geo 이동, 환경 유효성을 검사 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="7ccb0-122">Before you start a OneDrive geo move, we recommend that you validate the environment.</span></span>

<span data-ttu-id="7ccb0-123">모든 지리적 위치 호환 되는지 확인, 다음을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ccb0-123">To ensure that all geo locations are compatible, run:</span></span>

`Get-SPOGeoMoveCompatibilityStatus -AllLocations 1`

<span data-ttu-id="7ccb0-p105">법적 보유에서 사용 되는 OneDrive 또는 하위 사이트를 포함 하는 경우에 이동할 수 없습니다. OneDrive가 이동 될 수의 유효성을 검사 하는-ValidationOnly 매개 변수와 함께 시작 SPOUserAndContentMove cmdlet을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ccb0-p105">If a OneDrive is under legal hold or if it contains a subsite, it cannot be moved. You can use the Start-SPOUserAndContentMove cmdlet with the -ValidationOnly parameter to validate if the OneDrive is able to be moved:</span></span>

`Start-SPOUserAndContentMove -UserPrincipalName <UPN> -DestinationDataLocation <DestinationDataLocation> -ValidationOnly`

<span data-ttu-id="7ccb0-p106">OneDrive은 이동 또는 법적 보존 또는 하위 사이트 이동 하는 것을 방지할 수 있는 경우 실패를 준비 하는 경우 성공이 반환 됩니다. OneDrive 이동 하려면를 수행할 준비가 되었는지 확인 한 후에 이동을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ccb0-p106">This will return Success if the OneDrive is ready to be moved or Fail if there is a legal hold or subsite that would prevent the move. Once you have validated that the OneDrive is ready to move, you can start the move.</span></span>

## <a name="start-a-onedrive-geo-move"></a><span data-ttu-id="7ccb0-128">OneDrive 지리적으로 분산 이동 시작</span><span class="sxs-lookup"><span data-stu-id="7ccb0-128">Start a OneDrive geo move</span></span>

<span data-ttu-id="7ccb0-129">이동을 시작 하려면 다음을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ccb0-129">To start the move, run:</span></span>  

`Start-SPOUserAndContentMove -UserPrincipalName <UserPrincipalName> -DestinationDataLocation <DestinationDataLocation>`

<span data-ttu-id="7ccb0-130">이러한 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ccb0-130">Using these parameters:</span></span>

-   <span data-ttu-id="7ccb0-131">_UserPrincipalName_ – 해당 OneDrive를 이동 하는 사용자의 UPN 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ccb0-131">_UserPrincipalName_ – UPN of the user whose OneDrive is being moved.</span></span>

-   <span data-ttu-id="7ccb0-p107">_DestinationDataLocation_ – 지리적 위치 OneDrive 위치 이동 해야 합니다. 이 사용자의 기본 데이터 위치와 동일 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ccb0-p107">_DestinationDataLocation_ – Geo-Location where the OneDrive needs to be moved. This should be same as the user’s preferred data location.</span></span>

> [!NOTE]
> <span data-ttu-id="7ccb0-134">실행 하는 것이 좋습니다 `Get-SPOGeoMoveStateCompatibility` 와 `ValidationOnly` OneDrive를 시작 하기 전에 지리적으로 분산 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ccb0-134">We recommend running `Get-SPOGeoMoveStateCompatibility` with `ValidationOnly` prior to initiating OneDrive geo move.</span></span>

<span data-ttu-id="7ccb0-135">예, matt@contosoenergy.onmicrosoft.com의 OneDrive EUR에서 오스트레일리아를 이동 하려면 다음을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ccb0-135">For example, to move the OneDrive of matt@contosoenergy.onmicrosoft.com from EUR to AUS, run:</span></span>

`Start-SPOUserAndContentMove -UserPrincipalName matt@contosoenergy.onmicrosoft.com -DestinationDataLocation AUS`

![](media/move-onedrive-between-geo-locations_image2.png)

<span data-ttu-id="7ccb0-136">나중에 대 한 지리적으로 분산 이동을 예약 하려면 다음 매개 변수 중 하나를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ccb0-136">To schedule a geo move for a later time, use one of the following parameters:</span></span>

-   <span data-ttu-id="7ccb0-137">이 지정 된 시간에서 시작 됩니다 _PreferredMoveBeginDate_ -가능성이 이동 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ccb0-137">_PreferredMoveBeginDate_ – The move will likely begin at this specified time.</span></span>

-   <span data-ttu-id="7ccb0-138">_PreferredMoveEndDate_ -가능성이 이동 하면 됩니다 최상의 노력 별로이 지정한 시간까지 완료 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ccb0-138">_PreferredMoveEndDate_ – The move will likely be completed by this specified time, on a best effort basis.</span></span>

## <a name="cancel-a-onedrive-geo-move"></a><span data-ttu-id="7ccb0-139">OneDrive 지리적으로 분산 이동을 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ccb0-139">Cancel a OneDrive geo move</span></span> 

<span data-ttu-id="7ccb0-140">이동 하는 진행 중인 아닌 경우 사용자의 OneDrive의 지리적으로 분산 이동을 중지할 수 또는 cmdlet을 사용 하 여 완료 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ccb0-140">You can stop the geo move of a user’s OneDrive, provided the move is not in progress or completed by using the cmdlet:</span></span>

`Stop-SPOUserAndContentMove – UserPrincipalName <UserPrincipalName>`

<span data-ttu-id="7ccb0-141">여기서 _UserPrincipalName_ 은 해당 OneDrive 중지 하려는 이동 하는 사용자의 UPN입니다.</span><span class="sxs-lookup"><span data-stu-id="7ccb0-141">Where _UserPrincipalName_ is the UPN of the user whose OneDrive move you want to stop.</span></span>

## <a name="determining-current-status"></a><span data-ttu-id="7ccb0-142">현재 상태를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="7ccb0-142">Determining current status</span></span>

<span data-ttu-id="7ccb0-143">지리적으로 분산 이동 또는 Get SPOUserAndContentMoveState cmdlet을 사용 하 여에 연결 된 지리적으로 분산 로그 OneDrive의 상태를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ccb0-143">You can check the status of a OneDrive geo move in or out of the geo that you’re connected to by using the Get-SPOUserAndContentMoveState cmdlet.</span></span>

<span data-ttu-id="7ccb0-144">이동 상태를 확인 하는 다음 표에 설명 되어있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ccb0-144">The move statuses are described in the following table.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="7ccb0-145"><strong>Status</strong></span><span class="sxs-lookup"><span data-stu-id="7ccb0-145"><strong>Status</strong></span></span></th>
<th align="left"><span data-ttu-id="7ccb0-146"><strong>설명</strong></span><span class="sxs-lookup"><span data-stu-id="7ccb0-146"><strong>Description</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="7ccb0-147">이 notstarted 인</span><span class="sxs-lookup"><span data-stu-id="7ccb0-147">NotStarted</span></span></td>
<td align="left"><span data-ttu-id="7ccb0-148">이동 하는 시작 되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="7ccb0-148">The move has not started.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="7ccb0-149">진행 중 (<em></em>n/4)</span><span class="sxs-lookup"><span data-stu-id="7ccb0-149">InProgress (<em>n</em>/4)</span></span></td>
<td align="left"><span data-ttu-id="7ccb0-150">이동이 상태는 다음 중 하나에서 진행 중인: 유효성 검사 (1/4) (2/4)를 백업, 복원 (3/4) 정리 (4/4).</span><span class="sxs-lookup"><span data-stu-id="7ccb0-150">The move is in progress in one of the following states: Validation (1/4), Backup (2/4), Restore (3/4), Cleanup (4/4).</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="7ccb0-151">성공</span><span class="sxs-lookup"><span data-stu-id="7ccb0-151">Success</span></span></td>
<td align="left"><span data-ttu-id="7ccb0-152">이동이 성공적으로 완료 했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ccb0-152">The move has completed successfully.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="7ccb0-153">Failed</span><span class="sxs-lookup"><span data-stu-id="7ccb0-153">Failed</span></span></td>
<td align="left"><span data-ttu-id="7ccb0-154">이동에 실패 했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ccb0-154">The move failed.</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="7ccb0-155">특정 사용자를 이동의 상태를 찾으려면 UserPrincipalName 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ccb0-155">To find the status of a specific user’s move, use the UserPrincipalName parameter:</span></span>

`Get-SPOUserAndContentMoveState -UserPrincipalName <UPN>`

<span data-ttu-id="7ccb0-156">모든는 이동의 상태를 찾으려면 또는 지리적 위치에 연결 된 로그는 다음 값 중 하나로 MoveState 매개 변수를 사용:이 notstarted 인, 진행 중, 성공, 실패, 모든 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ccb0-156">To find the status of all of the moves in or out of the geo location that you’re connected to, use the MoveState parameter with one of the following values: NotStarted, InProgress, Success, Failed, All.</span></span>

`Get-SPOUserAndContentMoveState -MoveState <value>`

<span data-ttu-id="7ccb0-157">추가할 수 있습니다는 `-Verbose` 에 대 한 더 자세한 설명은 이동 상태 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="7ccb0-157">You can also add the `-Verbose` parameter for more verbose descriptions of the move state.</span></span>

## <a name="user-experience"></a><span data-ttu-id="7ccb0-158">사용자 환경</span><span class="sxs-lookup"><span data-stu-id="7ccb0-158">User Experience</span></span>

<span data-ttu-id="7ccb0-p108">자신의 OneDrive 다른 지리적 위치로 이동 하는 경우 OneDrive의 사용자가 영향을 최소화 하는 것을 알 해야 합니다. 간단한 읽기 전용 상태를 이동 하는 동안 외에도 이동이 완료 되 면 예상 대로 작동 하도록 기존 링크 및 사용 권한을 계속 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ccb0-p108">Users of OneDrive should notice minimal disruption if their OneDrive is moved to a different geo location. Aside from a brief read-only state during the move, existing links and permissions will continue to work as expected once the move is completed.</span></span>

### <a name="onedrive-for-business"></a><span data-ttu-id="7ccb0-161">비즈니스용 OneDrive</span><span class="sxs-lookup"><span data-stu-id="7ccb0-161">OneDrive for Business</span></span>

<span data-ttu-id="7ccb0-p109">진행 중인으로 이동 하는 동안에 읽기 전용 사용자의 OneDrive 설정 됩니다. 이동이 완료 되 면 Office 365 응용 프로그램 시작 관리자 또는 웹 브라우저를 OneDrive을 탐색할 때 사용자가 새로운 지리적 위치에 자신의 OneDrive로 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ccb0-p109">While the move is in progress the user’s OneDrive is set to read-only. Once the move is completed, the user is directed to their OneDrive in the new geo location when they navigate to OneDrive the Office 365 app launcher or a web browser.</span></span>

### <a name="permissions-on-onedrive-content"></a><span data-ttu-id="7ccb0-164">OneDrive 내용에 대 한 권한</span><span class="sxs-lookup"><span data-stu-id="7ccb0-164">Permissions on OneDrive content</span></span>

<span data-ttu-id="7ccb0-165">OneDrive 콘텐츠에 대 한 사용 권한 가진 사용자는 이동 하는 동안 및 완료 된 후 콘텐츠에 액세스할 수 있도록 계속 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ccb0-165">Users with permissions to OneDrive content will continue to have access to the content during the move and after it’s complete.</span></span>

### <a name="onedrive-sync-client"></a><span data-ttu-id="7ccb0-166">OneDrive 동기화 클라이언트</span><span class="sxs-lookup"><span data-stu-id="7ccb0-166">OneDrive Sync Client</span></span> 

<span data-ttu-id="7ccb0-p110">OneDrive 동기화 클라이언트는 자동으로 검색 하 고 원활 하 게 OneDrive 지리적으로 분산 이동이 완료 되 면 새 OneDrive 위치에 동기화를 전송 됩니다. 사용자 다시 로그인 하거나 다른 작업을 수행할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7ccb0-p110">The OneDrive sync client will automatically detect and seamlessly transfer syncing to the new OneDrive location once the OneDrive geo move is complete. The user does not need to sign-in again or take any other action.</span></span>

<span data-ttu-id="7ccb0-169">OneDrive 지리적으로 분산 이동 하는 진행 중인 동안 파일을 업데이트 하는 사용자, 하는 경우 동기화 클라이언트에서이 알려줍니다 하기 때문에 보류 중인 파일 업로드가 이동이 진행 되는 동안 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ccb0-169">If a user updates a file while the OneDrive geo move is in progress, the sync client will notify them that file uploads are pending while the move is underway.</span></span>

### <a name="sharing-links"></a><span data-ttu-id="7ccb0-170">링크를 공유합니다.</span><span class="sxs-lookup"><span data-stu-id="7ccb0-170">Sharing links</span></span> 

<span data-ttu-id="7ccb0-171">OneDrive 지리적으로 분산 시 완료를 이동, 이동 된 파일에 대 한 기존 공유 링크는 새로운 지리적 위치에 자동으로 리디렉션합니다.</span><span class="sxs-lookup"><span data-stu-id="7ccb0-171">Upon OneDrive geo move completion, the existing shared links for the files that were moved will automatically redirect to the new geo location.</span></span>

### <a name="onenote-experience"></a><span data-ttu-id="7ccb0-172">OneNote 환경</span><span class="sxs-lookup"><span data-stu-id="7ccb0-172">OneNote Experience</span></span> 

<span data-ttu-id="7ccb0-p111">OneNote win32 클라이언트와 UWP (범용) App 자동으로 검색 하 고 원활 하 게 OneDrive 지리적으로 분산 이동이 완료 되 면 새 OneDrive 위치로 전자 필기장을 동기화 됩니다. 사용자 다시 로그인 하거나 다른 작업을 수행할 필요가 없습니다. 사용자에 게 표시 되는 항목만 표시기가 OneDrive 지리적으로 분산 이동이 진행 중인 경우 전자 필기장 동기화 실패 하 게 합니다. 이 작업이 다음 버전의 OneNote 클라이언트에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ccb0-p111">OneNote win32 client and UWP (Universal) App will automatically detect and seamlessly sync notebooks to the new OneDrive location once OneDrive geo move is complete. The user does not need to sign-in again or take any other action. The only visible indicator to the user is notebook sync would fail when OneDrive geo move is in progress. This experience is available on the following OneNote client versions:</span></span>

-   <span data-ttu-id="7ccb0-177">OneNote win32 – 버전 16.0.8326.2096 (및 이상)</span><span class="sxs-lookup"><span data-stu-id="7ccb0-177">OneNote win32 – Version 16.0.8326.2096 (and later)</span></span>

-   <span data-ttu-id="7ccb0-178">OneNote UWP – 버전 16.0.8431.1006 (및 이상)</span><span class="sxs-lookup"><span data-stu-id="7ccb0-178">OneNote UWP – Version 16.0.8431.1006 (and later)</span></span>

-   <span data-ttu-id="7ccb0-179">OneNote Mobile App – 버전 16.0.8431.1011 (및 이상)</span><span class="sxs-lookup"><span data-stu-id="7ccb0-179">OneNote Mobile App – Version 16.0.8431.1011 (and later)</span></span>

### <a name="teams-app"></a><span data-ttu-id="7ccb0-180">팀이 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="7ccb0-180">Teams app</span></span>

<span data-ttu-id="7ccb0-p112">OneDrive 지리적으로 분산 시 완료를 이동 하 고, 사용자는 액세스할 자신의 OneDrive 파일에 팀 app. 또한 하 고, 지리적으로 분산 이동 하기 전에 해당 OneDrive에서 팀 채팅을 통해 공유 하는 파일 이동이 완료 한 후에 작동을 계속 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ccb0-p112">Upon OneDrive geo move completion, users will have access to their OneDrive files on the Teams app. Additionally, files shared via Teams chat from their OneDrive prior to geo move will continue to work after move is complete.</span></span>

### <a name="onedrive-for-business-mobile-app-ios"></a><span data-ttu-id="7ccb0-183">비즈니스 모바일 응용 프로그램 (iOS)에 대 한 OneDrive</span><span class="sxs-lookup"><span data-stu-id="7ccb0-183">OneDrive for Business Mobile App (iOS)</span></span> 

<span data-ttu-id="7ccb0-184">OneDrive 지리적으로 분산 시 완료를 이동, 로그 아웃 하 고 다시 로그인 iOS 모바일 응용 프로그램에 새 OneDrive 위치를 동기화 하는 사용자가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ccb0-184">Upon OneDrive geo move completion, the user would need to sign out and sign in again on the iOS Mobile App to sync to the new OneDrive location.</span></span>

### <a name="existing-followed-groups-and-sites"></a><span data-ttu-id="7ccb0-185">그룹 및 사이트 뒤에 기존</span><span class="sxs-lookup"><span data-stu-id="7ccb0-185">Existing followed groups and sites</span></span>

<span data-ttu-id="7ccb0-p113">열어본된 사이트 및 그룹의 지리적 위치에 관계 없이 비즈니스에 대 한 사용자의 OneDrive에 표시 됩니다. 사이트 및 다른 지리적 위치에 호스트 그룹을 별도 탭에서 열립니다.</span><span class="sxs-lookup"><span data-stu-id="7ccb0-p113">Followed sites and groups will show up in the user's OneDrive for business regardless of their geo location. Sites and Groups hosted in another geo location will open in a separate tab.</span></span>
