---
title: Office 365에서 디렉터리 동기화 상태 보기
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: 18be3b98-34ae-47be-9337-ab6c3fb372ac
description: 디렉터리 동기화를 비활성화 하는 방법에 대해 알아보세요. 또한 해당 상태를 볼 수 있습니다.
ms.openlocfilehash: a38b723db6f5bafe246e774972ca89c65bc9c846
ms.sourcegitcommit: 29f937b7430c708c9dbec23bdc4089e86c37c225
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/29/2019
ms.locfileid: "31001571"
---
# <a name="view-directory-synchronization-status-in-office-365"></a><span data-ttu-id="3601d-104">Office 365에서 디렉터리 동기화 상태 보기</span><span class="sxs-lookup"><span data-stu-id="3601d-104">View directory synchronization status in Office 365</span></span>

<span data-ttu-id="3601d-105">온-프레미스 환경을 Office 365와 동기화 하 여 온-프레미스 Active Directory를 Azure AD와 통합 한 경우에도 동기화 상태를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3601d-105">If you have integrated your on-premises Active Directory with Azure AD by synchronizing your on-premises environment with Office 365, you can also check the status of your synchronization.</span></span>
  
## <a name="view-directory-synchronization-status"></a><span data-ttu-id="3601d-106">디렉터리 동기화 상태 보기</span><span class="sxs-lookup"><span data-stu-id="3601d-106">View directory synchronization status</span></span>

- <span data-ttu-id="3601d-107">[Microsoft 365 관리 센터](https://admin.microsoft.com) 에 로그인 하 고 홈 페이지에서 **DirSync 상태** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="3601d-107">Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com) and choose **DirSync Status** on the home page.</span></span>
- <span data-ttu-id="3601d-108">또는 **사용자** \> **활성 사용자**로 이동 하 여 **활성 사용자** 페이지에서 **더 많은** \> **디렉터리 동기화**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="3601d-108">Alternately, you can go to **Users** \> **Active users**, and on the **Active users** page, choose **More** \> **Directory synchronization**.</span></span> <span data-ttu-id="3601d-109">**디렉터리 동기화** 창에서 **DirSync 관리로 이동을**선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="3601d-109">On the **Directory Synchronization** pane, choose **Go to DirSync management**.</span></span>

## <a name="information-on-the-manage-directory-synchronization-page"></a><span data-ttu-id="3601d-110">디렉터리 동기화 관리 페이지에 대 한 정보</span><span class="sxs-lookup"><span data-stu-id="3601d-110">Information on the Manage directory synchronization page</span></span>

<span data-ttu-id="3601d-111">다음 표에서는 페이지에 대 한 정보를 얻을 수 있는 기능을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3601d-111">The following table lists the features you can get information about on the page.</span></span>
  
<span data-ttu-id="3601d-112">디렉터리 동기화에 문제가 있으면 오류가이 페이지에도 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3601d-112">If there is a problem with your directory synchronization, the errors are listed on this page as well.</span></span> <span data-ttu-id="3601d-113">발생할 수 있는 다양 한 오류에 대 한 자세한 내용은 [Office 365에서 디렉터리 동기화 오류 파악](identify-directory-synchronization-errors.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3601d-113">For more information about different errors you might encounter, see [Identify directory synchronization errors in Office 365](identify-directory-synchronization-errors.md).</span></span>
  
|<span data-ttu-id="3601d-114">**항목**</span><span class="sxs-lookup"><span data-stu-id="3601d-114">**Item**</span></span>|<span data-ttu-id="3601d-115">**용도**</span><span class="sxs-lookup"><span data-stu-id="3601d-115">**What it's for**</span></span>|
|:-----|:-----|
|<span data-ttu-id="3601d-116">**확인 된 도메인**</span><span class="sxs-lookup"><span data-stu-id="3601d-116">**Domains verified**</span></span> | <span data-ttu-id="3601d-117">사용자가 본인을 확인 한 Office 365 테 넌 트의 도메인 수입니다.</span><span class="sxs-lookup"><span data-stu-id="3601d-117">Number of domains in your Office 365 tenant that you have verified you own.</span></span> |
|<span data-ttu-id="3601d-118">**도메인이 확인 되지 않음**</span><span class="sxs-lookup"><span data-stu-id="3601d-118">**Domains not verified**</span></span> | <span data-ttu-id="3601d-119">추가한 도메인 (확인 되지 않음)</span><span class="sxs-lookup"><span data-stu-id="3601d-119">Domains you have added, but not verified.</span></span> |
|<span data-ttu-id="3601d-120">**디렉터리 동기화 사용**</span><span class="sxs-lookup"><span data-stu-id="3601d-120">**Directory sync enabled**</span></span> |<span data-ttu-id="3601d-121">True 또는 False입니다.</span><span class="sxs-lookup"><span data-stu-id="3601d-121">True or False.</span></span> <span data-ttu-id="3601d-122">디렉터리 동기화를 사용 하도록 설정 했는지 여부를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3601d-122">Specifies whether you have enabled directory sync.</span></span> |
|<span data-ttu-id="3601d-123">**최신 디렉터리 동기화**</span><span class="sxs-lookup"><span data-stu-id="3601d-123">**Latest directory sync**</span></span> | <span data-ttu-id="3601d-124">디렉터리 동기화를 마지막으로 실행 한 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="3601d-124">Last time directory sync ran.</span></span> <span data-ttu-id="3601d-125">마지막 동기화가 3 일 전까지 경고 및 문제 해결 도구에 대 한 링크를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="3601d-125">Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="3601d-126">**암호 동기화 사용**</span><span class="sxs-lookup"><span data-stu-id="3601d-126">**Password sync enabled**</span></span> | <span data-ttu-id="3601d-127">True 또는 False입니다.</span><span class="sxs-lookup"><span data-stu-id="3601d-127">True or False.</span></span> <span data-ttu-id="3601d-128">온-프레미스와 Office 365 테 넌 트 간에 암호 해시 동기화가 있는지 여부를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3601d-128">Specifies whether you have password hash sync between our on-premises and your Office 365 tenant.</span></span> |
|<span data-ttu-id="3601d-129">**마지막 암호 동기화**</span><span class="sxs-lookup"><span data-stu-id="3601d-129">**Last Password Sync**</span></span> | <span data-ttu-id="3601d-130">암호 해시 동기화를 마지막으로 실행 한 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="3601d-130">Last time password hash sync ran.</span></span> <span data-ttu-id="3601d-131">마지막 동기화가 3 일 전까지 경고 및 문제 해결 도구에 대 한 링크를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="3601d-131">Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="3601d-132">**디렉터리 동기화 클라이언트 버전**</span><span class="sxs-lookup"><span data-stu-id="3601d-132">**Directory sync client version**</span></span> | <span data-ttu-id="3601d-133">새 버전의 Azure AD Connect가 릴리스되면 다운로드 링크를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="3601d-133">Contains a download link if a new version of Azure AD Connect has been released.</span></span> |
|<span data-ttu-id="3601d-134">**idfix 도구**</span><span class="sxs-lookup"><span data-stu-id="3601d-134">**IDFix Tool**</span></span> | <span data-ttu-id="3601d-135">로컬 Active Directory를 확인 하는 데 사용할 수 있는 도구인 [idfix](install-and-run-idfix.md)에 대 한 링크를 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="3601d-135">Download link to [IDFix](install-and-run-idfix.md), a tool you can use to check you local Active Directory.</span></span> |
|<span data-ttu-id="3601d-136">**디렉터리 동기화 서비스 계정**</span><span class="sxs-lookup"><span data-stu-id="3601d-136">**Directory sync service account**</span></span> | <span data-ttu-id="3601d-137">Office 365 디렉터리 동기화 서비스 계정의 이름을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="3601d-137">Displays the name of you Office 365 directory sync service account.</span></span> |