---
title: Office 365에서 디렉터리 동기화 상태 보기
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: 18be3b98-34ae-47be-9337-ab6c3fb372ac
description: 디렉터리 동기화를 비활성화 하는 방법에 알아봅니다. 또한 해당 상태를 볼 수 있습니다.
ms.openlocfilehash: c843fa4d71976cbdd0d6d3d10720e2845b26796c
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542217"
---
# <a name="view-directory-synchronization-status-in-office-365"></a><span data-ttu-id="5cafd-104">Office 365에서 디렉터리 동기화 상태 보기</span><span class="sxs-lookup"><span data-stu-id="5cafd-104">View directory synchronization status in Office 365</span></span>
<span data-ttu-id="5cafd-105">온-프레미스 환경의 Office 365와 동기화 하 여 Azure AD와 온-프레미스 Active Directory 통합 했는지를 하는 경우에 사용자 동기화의 상태를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cafd-105">If you have integrated your on-premises Active Directory with Azure AD by synchronizing your on-premises environment with Office 365, you can also check the status of your synchronization.</span></span>
  
## <a name="view-directory-synchronization-status"></a><span data-ttu-id="5cafd-106">디렉터리 동기화 상태 보기</span><span class="sxs-lookup"><span data-stu-id="5cafd-106">View directory synchronization status</span></span>
- <span data-ttu-id="5cafd-107">Office 365 관리 센터에 로그인 하 고 홈 페이지에서 **디렉터리 동기화 상태** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cafd-107">Sign in to the Office 365 admin center and choose **DirSync Status** on the home page.</span></span> 
- <span data-ttu-id="5cafd-p102">또는 **사용자** 에 게 이동할 수 있습니다 \> **현재 사용자가** **현재 사용자** 페이지에서 **더 많은** 선택 하 고 \> **디렉터리 동기화**합니다. **디렉터리 동기화** 창에서 **디렉터리 동기화 관리로 이동**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cafd-p102">Alternately, you can go to **Users** \> **Active users**, and on the **Active users** page, choose **More** \> **Directory synchronization**. On the **Directory Synchronization** pane, choose **Go to DirSync management**.</span></span>
    
## <a name="information-on-the-manage-directory-synchronization-page"></a><span data-ttu-id="5cafd-110">디렉터리 동기화 관리 페이지에 대 한 정보</span><span class="sxs-lookup"><span data-stu-id="5cafd-110">Information on the Manage directory synchronization page</span></span>

<span data-ttu-id="5cafd-111">다음 표에서 페이지에 대 한 정보를 얻을 수 기능을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="5cafd-111">The following table lists the features you can get information about on the page.</span></span>
  
<span data-ttu-id="5cafd-p103">디렉터리 동기화에 문제가 있으면이 페이지는 오류가 나열 됩니다. 다른 오류가 발생할 수 있는 방법에 대 한 자세한 내용은 [Office 365에서 디렉터리 동기화 오류 식별을](identify-directory-synchronization-errors.md)참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="5cafd-p103">If there is a problem with your directory synchronization, the errors are listed on this page as well. For more information about different errors you might encounter, see [Identify directory synchronization errors in Office 365](identify-directory-synchronization-errors.md).</span></span>
  
|<span data-ttu-id="5cafd-114">**항목**</span><span class="sxs-lookup"><span data-stu-id="5cafd-114">**Item**</span></span>|<span data-ttu-id="5cafd-115">**이 대 한**</span><span class="sxs-lookup"><span data-stu-id="5cafd-115">**What it's for**</span></span>|
|:-----|:-----|
|<span data-ttu-id="5cafd-116">**도메인 확인**</span><span class="sxs-lookup"><span data-stu-id="5cafd-116">**Domains verified**</span></span> | <span data-ttu-id="5cafd-117">도메인 확인 한 경우 Office 365 테 넌 트의 수를 소유 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cafd-117">Number of domains in your Office 365 tenant that you have verified you own.</span></span> |
|<span data-ttu-id="5cafd-118">**확인 되지 않은 도메인**</span><span class="sxs-lookup"><span data-stu-id="5cafd-118">**Domains not verified**</span></span> | <span data-ttu-id="5cafd-119">도메인에 추가 되었지만 확인할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5cafd-119">Domains you have added, but not verified.</span></span> |
|<span data-ttu-id="5cafd-120">**디렉터리 동기화를 사용 하도록 설정**</span><span class="sxs-lookup"><span data-stu-id="5cafd-120">**Directory sync enabled**</span></span> |<span data-ttu-id="5cafd-p104">True 또는 false로 설정 합니다. 디렉터리 동기화를 사용할 수 있는지 여부를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cafd-p104">True or False. Specifies whether you have enabled directory sync.</span></span> |
|<span data-ttu-id="5cafd-123">**최신 디렉터리 동기화**</span><span class="sxs-lookup"><span data-stu-id="5cafd-123">**Latest directory sync**</span></span> | <span data-ttu-id="5cafd-p105">디렉터리 동기화를 실행 하는 마지막 시간입니다. 표시 됩니다 경고 및 링크는 문제해결 도구 마지막 동기화 된 3 일이 경과 하는 경우.</span><span class="sxs-lookup"><span data-stu-id="5cafd-p105">Last time directory sync ran. Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="5cafd-126">**암호 동기화를 사용 하도록 설정**</span><span class="sxs-lookup"><span data-stu-id="5cafd-126">**Password sync enabled**</span></span> | <span data-ttu-id="5cafd-p106">True 또는 false로 설정 합니다. 사용해 온-프레미스 및 Office 365 테 넌 트 간에 암호 해시 동기화 해야 하는지 여부를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cafd-p106">True or False. Specifies whether you have password hash sync between our on-premises and your Office 365 tenant.</span></span> |
|<span data-ttu-id="5cafd-129">**마지막 암호 동기화**</span><span class="sxs-lookup"><span data-stu-id="5cafd-129">**Last Password Sync**</span></span> | <span data-ttu-id="5cafd-p107">마지막으로 암호 해시 동기화를 실행 합니다. 표시 됩니다 경고 및 링크는 문제해결 도구 마지막 동기화 된 3 일이 경과 하는 경우.</span><span class="sxs-lookup"><span data-stu-id="5cafd-p107">Last time password hash sync ran. Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="5cafd-132">**디렉터리 동기화 클라이언트 버전**</span><span class="sxs-lookup"><span data-stu-id="5cafd-132">**Directory sync client version**</span></span> | <span data-ttu-id="5cafd-133">Azure AD 연결의 새 버전을 해제 된 경우에 다운로드 링크를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cafd-133">Contains a download link if a new version of Azure AD Connect has been released.</span></span> |
|<span data-ttu-id="5cafd-134">**IDFix 도구**</span><span class="sxs-lookup"><span data-stu-id="5cafd-134">**IDFix Tool**</span></span> | <span data-ttu-id="5cafd-135">[IDFix](install-and-run-idfix.md), 로컬 Active Directory를 확인 하는 데 사용할 수 있는 도구에 링크를 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cafd-135">Download link to [IDFix](install-and-run-idfix.md), a tool you can use to check you local Active Directory.</span></span> |
|<span data-ttu-id="5cafd-136">**디렉터리 동기화 서비스 계정**</span><span class="sxs-lookup"><span data-stu-id="5cafd-136">**Directory sync service account**</span></span> | <span data-ttu-id="5cafd-137">Office 365 디렉터리 동기화 서비스 계정 하의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5cafd-137">Displays the name of you Office 365 directory sync service account.</span></span> |