---
title: 인증되지 않은 공유에 대한 모범 사례
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
localization_priority: Priority
f1.keywords: NOCSH
description: 인증되지 않은 사용자와 파일 및 폴더를 공유하는 모범 사례를 알아봅니다.
ms.openlocfilehash: 38afdcb2d59547144e57656971395c48506bcbbf
ms.sourcegitcommit: 4e50f43857f93f42b71650354d1aec9ed4cc7fe2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/06/2020
ms.locfileid: "42549127"
---
# <a name="best-practices-for-sharing-files-and-folders-with-unauthenticated-users"></a><span data-ttu-id="fe7d3-103">인증되지 않은 사용자와 파일 및 폴더를 공유하는 모범 사례</span><span class="sxs-lookup"><span data-stu-id="fe7d3-103">Best practices for sharing files and folders with unauthenticated users</span></span>

<span data-ttu-id="fe7d3-104">인증되지 않은 공유(*모든 사용자* 링크)는 다양한 상황에서 편리하며 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7d3-104">Unauthenticated sharing (*Anyone* links) can be convenient and is useful in various scenarios.</span></span> <span data-ttu-id="fe7d3-105">*모든 사용자* 링크는 가장 간편하게 공유하는 방법입니다. 사용자가 인증 없이 링크를 열 수 있으며 다른 사용자에게 무료로 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe7d3-105">*Anyone* links are the easiest way to share: people can open the link without authentication and are free to pass it on to others.</span></span>

<span data-ttu-id="fe7d3-106">일반적으로 조직의 모든 콘텐츠가 인증되지 않은 공유에 적합하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fe7d3-106">Usually, not all content in an organization is appropriate for unauthenticated sharing.</span></span> <span data-ttu-id="fe7d3-107">이 문서에서는 사용자가 파일 및 폴더의 인증되지 않은 공유를 할 수 있지만, 조직의 콘텐츠를 보호하는 데 도움이 되는 보호 기능도 포함된 환경을 만들 수 있는 옵션을 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="fe7d3-107">This article covers the options available to help you create an environment where your users can use unauthenticated sharing of files and folders, but where there are safeguards in place to help protect your organization's content.</span></span>

> [!NOTE]
> <span data-ttu-id="fe7d3-108">인증되지 않은 공유가 작동하려면 조직 및 사용자가 사용할 개별 사이트 또는 팀에 대해 이 기능을 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7d3-108">For unauthenticated sharing to work, you must enable it for your organization and for the individual site or team that you'll be using.</span></span> <span data-ttu-id="fe7d3-109">활성화하려는 시나리오를 보려면 [조직 외부 사용자와 공동 작업](collaborating-with-people-outside-your-organization.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fe7d3-109">See [Collaborating with people outside your organization](collaborating-with-people-outside-your-organization.md) for the scenario that you want to enable.</span></span>

## <a name="set-an-expiration-date-for-anyone-links"></a><span data-ttu-id="fe7d3-110">모든 사용자 링크의 만료 날짜를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7d3-110">Set an expiration date for Anyone links</span></span>

<span data-ttu-id="fe7d3-111">파일은 오랜 기간 동안 사이트, 그룹 및 팀에 저장되는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="fe7d3-111">Files are often stored in sites, groups, and teams for long periods of time.</span></span> <span data-ttu-id="fe7d3-112">경우에 따라, 파일을 수년 동안 보존해야 하는 데이터 보존 정책이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe7d3-112">Occasionally there are data retention policies that require files to be retained for years.</span></span> <span data-ttu-id="fe7d3-113">해당 파일을 인증되지 않은 사용자와 공유하는 경우, 나중에 파일에 대한 예기치 않은 액세스 및 변경 내용이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe7d3-113">If such files are shared with unauthenticated people, this could lead to unexpected access and changes to files in the future.</span></span> <span data-ttu-id="fe7d3-114">이와 같은 가능성을 줄이기 위해 *모든 사용자* 링크의 만료 시간을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe7d3-114">To mitigate this possibility, you can configure an expiration time for *Anyone* links.</span></span>

<span data-ttu-id="fe7d3-115">*모든 사용자* 링크가 만료되면 계정을 더 이상 콘텐츠에 액세스하는 데 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fe7d3-115">Once an *Anyone* link expires, it can no longer be used to access content.</span></span>

<span data-ttu-id="fe7d3-116">모든 사용자 링크의 만료 날짜를 설정하려면 다음 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7d3-116">To set an expiration date for Anyone links</span></span>
1. <span data-ttu-id="fe7d3-117">SharePoint Online 관리 센터을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="fe7d3-117">Open the SharePoint Online admin center.</span></span>
2. <span data-ttu-id="fe7d3-118">왼쪽 탐색 창에서 **공유**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7d3-118">In the left navigation, click **Sharing**.</span></span>
3. <span data-ttu-id="fe7d3-119">**"모든 사용자" 링크의 고급 설정**에서 **이러한 링크는 다음 기간 내에 만료되어야 합니다** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7d3-119">Under **Advanced settings for "Anyone" links**, select the **These links must expire within this many days** check box.</span></span></br>
   <span data-ttu-id="fe7d3-120">![SharePoint 조직 수준 모든 사용자 링크 만료 설정 스크린샷](media/sharepoint-organization-anyone-link-expiration.png)</span><span class="sxs-lookup"><span data-stu-id="fe7d3-120">![Screenshot of SharePoint organization-level Anyone link expiration settings](media/sharepoint-organization-anyone-link-expiration.png)</span></span>
4. <span data-ttu-id="fe7d3-121">상자에 일 수를 입력한 다음 **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7d3-121">Type a number of days in the box, and then click **Save**.</span></span>

<span data-ttu-id="fe7d3-122">*모든 사용자* 링크가 만료되면 파일이나 폴더를 새 *모든 사용자* 링크와 다시 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe7d3-122">Note that once an *Anyone* link expires, the file or folder can be re-shared with a new *Anyone* link.</span></span>

## <a name="set-link-permissions"></a><span data-ttu-id="fe7d3-123">링크 사용 권한 설정</span><span class="sxs-lookup"><span data-stu-id="fe7d3-123">Set link permissions</span></span>

<span data-ttu-id="fe7d3-124">파일의 *모든 사용자* 링크를 사용하여 파일을 편집할 수 있으며, 폴더의 *모든 사용자* 링크를 통해 파일을 확인하고 편집하며 새 파일을 해당 폴더에 업로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe7d3-124">By default, *Anyone* links for a file allow people to edit the file, and *Anyone* links for a folder allow people to edit and view files, and upload new files to the folder.</span></span> <span data-ttu-id="fe7d3-125">파일 및 폴더에 대한 사용 권한을 보기 전용으로 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe7d3-125">You can change these permissions for files and for folders independently to view-only.</span></span>

<span data-ttu-id="fe7d3-126">인증되지 않은 공유를 허용하지만, 인증되지 않은 사용자가 조직의 콘텐츠를 수정하는 것이 우려되는 경우, 파일 및 폴더 사용 권한을 **보기**로 설정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="fe7d3-126">If you want to allow unauthenticated sharing, but are concerned about unauthenticated people modifying your organization's content, consider setting the file and folder permissions to **View**.</span></span>

<span data-ttu-id="fe7d3-127">모든 사용자 링크에 대한 사용 권한을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="fe7d3-127">To set permissions for Anyone links</span></span>
1. <span data-ttu-id="fe7d3-128">SharePoint Online 관리 센터을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="fe7d3-128">Open the SharePoint Online admin center.</span></span>
2. <span data-ttu-id="fe7d3-129">왼쪽 탐색 창에서 **공유**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7d3-129">In the left navigation, click **Sharing**.</span></span>
3. <span data-ttu-id="fe7d3-130">**"모든 사용자" 링크의 고급 설정**에서 사용할 파일 및 폴더 사용 권한을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7d3-130">Under **Advanced settings for "Anyone" links**, select the file and folder permissions that you want to use.</span></span></br>
   <span data-ttu-id="fe7d3-131">![SharePoint 조직 수준 모든 사용자 링크 사용 권한 설정 스크린샷](media/sharepoint-organization-anyone-link-permissions.png)</span><span class="sxs-lookup"><span data-stu-id="fe7d3-131">![Screenshot of SharePoint organization-level Anyone link permissions settings](media/sharepoint-organization-anyone-link-permissions.png)</span></span>

<span data-ttu-id="fe7d3-132">*모든 사용자* 링크가 **보기**로 설정된 경우, 게스트와 파일 및 폴더를 계속 공유하고 *특정 사용자* 링크를 사용하여 편집 권한을 부여할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe7d3-132">With *Anyone* links set to **View**, users can still share files and folders with guests and give them edit permissions by using *Specific people* links.</span></span> <span data-ttu-id="fe7d3-133">이러한 링크를 사용하려면 조직 외부의 사용자가 게스트로 인증해야 하며, 이 링크와 공유되는 파일 및 폴더에서 게스트 활동을 추적하고 감사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe7d3-133">These links require people outside your organization to authenticate as guests, and you can track and audit guest activity on files and folders shared with these links.</span></span>

## <a name="set-default-link-type-to-only-work-for-people-in-your-organization"></a><span data-ttu-id="fe7d3-134">기본 링크 유형이 조직에 있는 사용자에 대해서만 작동하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7d3-134">Set default link type to only work for people in your organization</span></span>

<span data-ttu-id="fe7d3-135">*모든 사용자* 공유가 사용자 조직에 사용할 수 있도록 설정된 경우, 기본 공유 링크는 일반적으로 **모든 사용자**로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe7d3-135">When *Anyone* sharing is enabled for your organization, the default sharing link is normally set to **Anyone**.</span></span> <span data-ttu-id="fe7d3-136">이 기능이 사용자에게는 편리하지만, 원하지 않는 인증되지 않는 공유의 위험이 높아질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe7d3-136">While this can be convenient for users, it can increase the risk of unintentional unauthenticated sharing.</span></span> <span data-ttu-id="fe7d3-137">사용자가 중요한 문서를 공유하는 동안 링크 유형을 변경하는 것을 잊어버린 경우, 사용자가 인증이 필요 없는 공유 링크를 실수로 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe7d3-137">If a user forgets to change the link type while sharing a sensitive document, they might accidentally create a sharing link that doesn't require authentication.</span></span>

<span data-ttu-id="fe7d3-138">기본 링크 설정을 조직 내부 사용자만 사용할 수 있는 링크로 변경하여 이 위험을 완화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe7d3-138">You can mitigate this risk by changing the default link setting to a link that only works for people inside your organization.</span></span> <span data-ttu-id="fe7d3-139">인증되지 않은 사용자와 공유하려는 사용자는 해당 옵션을 구체적으로 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7d3-139">Users who want to share with unauthenticated people would then have to specifically select that option.</span></span>

<span data-ttu-id="fe7d3-140">기본 파일 및 폴더 공유 링크를 설정하려면 다음 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7d3-140">To set the default file and folder sharing link</span></span>
1. <span data-ttu-id="fe7d3-141">왼쪽 탐색 창의 SharePoint 관리 센터에서 **공유**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7d3-141">In the SharePoint admin center, in the left navigation, click **Sharing**.</span></span>
2. <span data-ttu-id="fe7d3-142">**파일 및 폴더 링크**에서 **조직 내 사용자만**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7d3-142">Under **File and folder links**, select **Only people in your organization**.</span></span></br>
   <span data-ttu-id="fe7d3-143">![SharePoint 기본 링크 유형 설정 스크린샷](media/sharepoint-default-sharing-link-company-link.png)</span><span class="sxs-lookup"><span data-stu-id="fe7d3-143">![Screenshot of SharePoint default link type setting](media/sharepoint-default-sharing-link-company-link.png)</span></span>
3. <span data-ttu-id="fe7d3-144">**저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7d3-144">Click **Save**</span></span>

## <a name="protect-against-malicious-files"></a><span data-ttu-id="fe7d3-145">악성 파일로부터 보호</span><span class="sxs-lookup"><span data-stu-id="fe7d3-145">Protect against malicious files</span></span>

<span data-ttu-id="fe7d3-146">익명 사용자가 파일을 업로드할 수 있도록 허용하는 경우 악성 파일이 업로드되는 위험이 증가하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe7d3-146">When you allow anonymous users to upload files, you're at an increased risk of someone uploading a malicious file.</span></span> <span data-ttu-id="fe7d3-147">Microsoft 365에서는 고급 위협 방지에서 *안전한 첨부 파일* 기능을 사용하여 업로드된 파일을 자동으로 검사하여 안전하지 않은 파일을 격리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe7d3-147">In Microsoft 365, you can use the *safe attachments* feature in Advanced Threat Protection to automatically scan uploaded files and quarantine files that are found to be unsafe.</span></span>

<span data-ttu-id="fe7d3-148">안전한 첨부 파일을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="fe7d3-148">To turn on safe attachments</span></span>
1. <span data-ttu-id="fe7d3-149">[Microsoft 365 보안](https://security.microsoft.com) 관리 센터를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="fe7d3-149">Open the [Microsoft 365 security](https://security.microsoft.com) admin center.</span></span>
2. <span data-ttu-id="fe7d3-150">왼쪽 탐색 창에서 **정책**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7d3-150">In the left navigation, click **Policies**.</span></span>
3. <span data-ttu-id="fe7d3-151">**위협 방지**에서 **ATP 안전한 첨부 파일(Office 365)** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7d3-151">Under **Threat protection**, click **ATP safe attachments (Office 365)**.</span></span>
4. <span data-ttu-id="fe7d3-152">**SharePoint, OneDrive 및 Microsoft Teams에 대해 ATP 켜기** 확인란을 선택하고 **저장**을 클릭합니다. </span><span class="sxs-lookup"><span data-stu-id="fe7d3-152">Select the **Turn on ATP for SharePoint, OneDrive, and Microsoft Teams** check box, and then click **Save**.</span></span></br>
   <span data-ttu-id="fe7d3-153">![보안 및 규정 준수 센터의 안전한 첨부 파일 설정 스크린샷](media/safe-attachments-setting.png)</span><span class="sxs-lookup"><span data-stu-id="fe7d3-153">![Screenshot of the safe attachments setting in the Security and Compliance center](media/safe-attachments-setting.png)</span></span>

## <a name="add-copyright-information-to-your-files"></a><span data-ttu-id="fe7d3-154">파일에 저작권 정보 추가</span><span class="sxs-lookup"><span data-stu-id="fe7d3-154">Add copyright information to your files</span></span>

<span data-ttu-id="fe7d3-155">Microsoft 365 규정 준수 관리 센터에서 민감도 레이블을 사용하는 경우, 조직의 Office 문서에 워터마크나 머리글 또는 바닥글을 자동으로 추가하도록 레이블을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe7d3-155">If you use sensitivity labels in the Microsoft 365 Compliance admin center, you can configure your labels to add a watermark or a header or footer automatically to your organization's Office documents.</span></span> <span data-ttu-id="fe7d3-156">따라서 공유된 파일에 저작권 또는 기타 소유권 정보가 포함되도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe7d3-156">In this way, you can make sure that shared files contain copyright or other ownership information.</span></span>

<span data-ttu-id="fe7d3-157">레이블이 지정된 파일에 바닥글을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="fe7d3-157">To add a footer to a labeled file</span></span>
1. <span data-ttu-id="fe7d3-158">[Microsoft 365 규정 준수 관리 센터](https://compliance.microsoft.com)를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="fe7d3-158">Open the [Microsoft 365 compliance admin center](https://compliance.microsoft.com).</span></span>
2. <span data-ttu-id="fe7d3-159">왼쪽 탐색 창의 **분류**에서 **민감도 레이블**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7d3-159">In the left navigation, under **Classification**, click **Sensitivity labels**.</span></span>
3. <span data-ttu-id="fe7d3-160">바닥글을 추가하려는 레이블을 클릭한 다음 **레이블 편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7d3-160">Click the label that you want to have add a footer, and then click **Edit label**.</span></span>
4. <span data-ttu-id="fe7d3-161">**콘텐츠 표시** 탭을 클릭한 다음, 콘텐츠 표시를 **설정**합니다. </span><span class="sxs-lookup"><span data-stu-id="fe7d3-161">Click the **Content marking** tab, and then turn **On** content marking.</span></span>
5. <span data-ttu-id="fe7d3-162">추가하려는 텍스트 유형의 확인란을 선택한 다음, **텍스트 사용자 지정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7d3-162">Select the check box for the type of text you want to add, and then click **Customize text**.</span></span>
6. <span data-ttu-id="fe7d3-163">문서에 추가하려는 텍스트를 입력하고 원하는 텍스트 옵션을 선택한 다음, **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7d3-163">Type the text that you want added to your documents, select the text options that you want, and then click **Save**.</span></span></br>
   <span data-ttu-id="fe7d3-164">![민감도 레이블의 콘텐츠 표시 설정 스크린샷](media/content-marking-for-anonymous-sharing.png)</span><span class="sxs-lookup"><span data-stu-id="fe7d3-164">![Screenshot of the content marking settings for a sensitivity label](media/content-marking-for-anonymous-sharing.png)</span></span>
7. <span data-ttu-id="fe7d3-165">**저장**을 클릭한 다음 **닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7d3-165">Click **Save**, and then click **Close**.</span></span>

<span data-ttu-id="fe7d3-166">레이블에 콘텐츠 표시를 사용하는 경우, 사용자가 해당 레이블을 적용하면 사용자가 지정한 텍스트가 Office 문서에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe7d3-166">With content marking enabled for the label, the text you specified will be added to Office documents when a user applies that label.</span></span>

## <a name="see-also"></a><span data-ttu-id="fe7d3-167">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fe7d3-167">See Also</span></span>


[<span data-ttu-id="fe7d3-168">민감도 레이블 개요</span><span class="sxs-lookup"><span data-stu-id="fe7d3-168">Overview of sensitivity labels</span></span>](https://docs.microsoft.com/Office365/SecurityCompliance/sensitivity-labels)

[<span data-ttu-id="fe7d3-169">게스트와 공유할 때 파일에 실수로 발생하는 노출을 제한</span><span class="sxs-lookup"><span data-stu-id="fe7d3-169">Limit accidental exposure to files when sharing with guests</span></span>](sharing-limit-accidental-exposure.md)

[<span data-ttu-id="fe7d3-170">보안 게스트 공유 환경 만들기</span><span class="sxs-lookup"><span data-stu-id="fe7d3-170">Create a secure guest sharing environment</span></span>](create-a-secure-guest-sharing-environment.md)