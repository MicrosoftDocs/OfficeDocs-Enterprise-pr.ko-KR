---
title: Office 365 클라이언트 앱 지원-모바일 응용 프로그램 관리
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: Office 365 Administration
localization_priority: Normal
ms.collection:
- Strat_O365_Enterprise
- M365-subscription-management
search.appverid:
- MET150
description: 모바일 응용 프로그램 관리에 대 한 Office 365 클라이언트 앱 지원 이해
ms.openlocfilehash: b75b992bf45ff1a899e71a9f6b7903e3f78a34d4
ms.sourcegitcommit: 80bc767a9c88a259facb3894b9a168c85d35eb70
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2019
ms.locfileid: "31517552"
---
# <a name="office-365-client-app-support---mobile-application-management"></a><span data-ttu-id="ac444-103">Office 365 클라이언트 앱 지원-모바일 응용 프로그램 관리</span><span class="sxs-lookup"><span data-stu-id="ac444-103">Office 365 Client App Support - Mobile Application Management</span></span>

<span data-ttu-id="ac444-104">Intune 관리 기능 제품군을 활용 하면 MAM (모바일 응용 프로그램 관리)를 사용 하 여 사용자의 모바일 앱을 게시, 푸시, 구성, 보호, 모니터링 및 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac444-104">Leveraging the suite of Intune management features, mobile application management (MAM) lets you publish, push, configure, secure, monitor, and update mobile apps for your users.</span></span> <span data-ttu-id="ac444-105">MAM는 Intune에 등록 되어 있는 경우에 상관 없이 모든 장치에 대 한 응용 프로그램 내에서 조직의 데이터를 보호할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac444-105">MAM can protect an organization's data within an application for all devices, whether enrolled in Intune or not.</span></span>

<span data-ttu-id="ac444-106">[모바일 응용 프로그램 관리](https://docs.microsoft.com/intune/mam-faq) 및 [다중 id MAM](https://docs.microsoft.com/intune/app-protection-policy)에 대해 자세히 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="ac444-106">Learn more about [mobile application management](https://docs.microsoft.com/intune/mam-faq) and [multi-identity MAM](https://docs.microsoft.com/intune/app-protection-policy).</span></span>

## <a name="supported-platforms"></a><span data-ttu-id="ac444-107">지원되는 플랫폼</span><span class="sxs-lookup"><span data-stu-id="ac444-107">Supported platforms</span></span>

 - <span data-ttu-id="ac444-108">Android</span><span class="sxs-lookup"><span data-stu-id="ac444-108">Android</span></span>
 - <span data-ttu-id="ac444-109">iOS<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="ac444-109">iOS<sup>1</sup></span></span>

<span data-ttu-id="ac444-110">office 365의 플랫폼 지원에 대 한 자세한 내용은 [office 365에 대 한 시스템 요구 사항을](https://products.office.com/office-system-requirements)참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ac444-110">For more information about platform support in Office 365, see [System requirements for Office 365](https://products.office.com/office-system-requirements).</span></span>

## <a name="supported-clients"></a><span data-ttu-id="ac444-111">지원되는 클라이언트</span><span class="sxs-lookup"><span data-stu-id="ac444-111">Supported clients</span></span>

<span data-ttu-id="ac444-112">다음 클라이언트의 최신 버전에서는 모바일 응용 프로그램 관리를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac444-112">The latest versions of the following clients support mobile application management:</span></span>

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Dynamics 365 아이콘](media/o365-dynamics365-64x64.png) <br> [<span data-ttu-id="ac444-114">Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="ac444-114">Dynamics 365</span></span>](https://dynamics.microsoft.com) | ![에 지 아이콘](media/o365-edge-64x64.png) <br> [<span data-ttu-id="ac444-116">면</span><span class="sxs-lookup"><span data-stu-id="ac444-116">Edge</span></span>](https://www.microsoft.com/windows/microsoft-edge) | ![Excel 아이콘](media/o365-excel-64x64.png) <br> [<span data-ttu-id="ac444-118">Excel</span><span class="sxs-lookup"><span data-stu-id="ac444-118">Excel</span></span>](https://products.office.com/excel) | ![흐름 아이콘](media/o365-flow-64x64.png) <br> [<span data-ttu-id="ac444-120">흐름</span><span class="sxs-lookup"><span data-stu-id="ac444-120">Flow</span></span>](https://flow.microsoft.com) | ![Kaizala 아이콘](media/o365-kaizala-64x64.png) <br> [<span data-ttu-id="ac444-122">Kaizala</span><span class="sxs-lookup"><span data-stu-id="ac444-122">Kaizala</span></span>](https://products.office.com/en/business/microsoft-kaizala) 
| ![비즈니스용 OneDrive 아이콘](media/o365-OneDrive-64x64.png) <br> [<span data-ttu-id="ac444-124">OneDrive</span><span class="sxs-lookup"><span data-stu-id="ac444-124">OneDrive</span></span>](https://products.office.com/onedrive-for-business/online-cloud-storage) | ![OneNote 아이콘](media/o365-OneNote-64x64.png) <br> [<span data-ttu-id="ac444-126">OneNote</span><span class="sxs-lookup"><span data-stu-id="ac444-126">OneNote</span></span>](https://products.office.com/onenote) | ![Outlook 아이콘](media/o365-outlook-64x64.png) <br> [<span data-ttu-id="ac444-128">Outlook</span><span class="sxs-lookup"><span data-stu-id="ac444-128">Outlook</span></span>](https://products.office.com/outlook) | ![Planner 아이콘](media/o365-planner-64x64.png) <br> [<span data-ttu-id="ac444-130">Planner</span><span class="sxs-lookup"><span data-stu-id="ac444-130">Planner</span></span>](https://products.office.com/business/task-management-software) | ![PowerApps 아이콘](media/o365-powerapps-64x64.png) <br> [<span data-ttu-id="ac444-132">PowerApps</span><span class="sxs-lookup"><span data-stu-id="ac444-132">PowerApps</span></span> ](https://powerapps.microsoft.com) 
| ![PowerBI 아이콘](media/o365-powerbi-64x64.png) <br> [<span data-ttu-id="ac444-134">Power BI</span><span class="sxs-lookup"><span data-stu-id="ac444-134">Power BI</span></span>](https://powerbi.microsoft.com) | ![PowerPoint 아이콘](media/o365-powerpoint-64x64.png) <br> [<span data-ttu-id="ac444-136">PowerPoint</span><span class="sxs-lookup"><span data-stu-id="ac444-136">PowerPoint</span></span>](https://products.office.com/powerpoint) | ![SharePoint 아이콘](media/o365-sharepoint-64x64.png) <br> [<span data-ttu-id="ac444-138">Sharepoint</span><span class="sxs-lookup"><span data-stu-id="ac444-138">Sharepoint</span></span>](https://products.office.com/sharepoint) | ![비즈니스용 Skype 아이콘](media/o365-skypeforbusiness-64x64.png) <br> [<span data-ttu-id="ac444-140"><br> 비즈니스용 Skype</span><span class="sxs-lookup"><span data-stu-id="ac444-140">Skype for <br> Business</span></span>](https://www.skype.com/business/) | ![StaffHub 아이콘](media/o365-staffhub-64x64.png) <br> [<span data-ttu-id="ac444-142">StaffHub</span><span class="sxs-lookup"><span data-stu-id="ac444-142">StaffHub</span></span>](https://products.office.com/microsoft-staffhub/staff-scheduling-software) 
| ![스트림 아이콘](media/o365-stream-64x64.png) <br> [<span data-ttu-id="ac444-144">Stream</span><span class="sxs-lookup"><span data-stu-id="ac444-144">Stream</span></span>](https://stream.microsoft.com) | ![Sway 아이콘](media/o365-sway-64x64.png) <br> [<span data-ttu-id="ac444-146">Sway<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="ac444-146">Sway<sup>1</sup></span></span>](https://sway.com) | ![팀 아이콘](media/o365-teams-64x64.png) <br> [<span data-ttu-id="ac444-148">Teams</span><span class="sxs-lookup"><span data-stu-id="ac444-148">Teams</span></span>](https://products.office.com/microsoft-teams/group-chat-software) | ![할 일 아이콘](media/o365-todo-64x64.png) <br> [<span data-ttu-id="ac444-150">To-Do</span><span class="sxs-lookup"><span data-stu-id="ac444-150">To-Do</span></span>](https://todo.microsoft.com) | ![Visio 아이콘](media/o365-visio-64x64.png) <br> [<span data-ttu-id="ac444-152">Visio</span><span class="sxs-lookup"><span data-stu-id="ac444-152">Visio</span></span>](https://products.office.com/visio/flowchart-software) 
| ![Word 아이콘](media/o365-word-64x64.png) <br> [<span data-ttu-id="ac444-154">Word</span><span class="sxs-lookup"><span data-stu-id="ac444-154">Word</span></span>](https://products.office.com/word) | ![Yammer 아이콘](media/o365-yammer-64x64.png) <br> [<span data-ttu-id="ac444-156">Yammer</span><span class="sxs-lookup"><span data-stu-id="ac444-156">Yammer</span></span>](https://products.office.com/yammer/yammer-overview)

> [!NOTE]
> <span data-ttu-id="ac444-157"><sup>1</sup> iOS의 Sway에 대 한 지원이 곧 제공 될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="ac444-157"><sup>1</sup> Support for Sway on iOS coming soon.</span></span>