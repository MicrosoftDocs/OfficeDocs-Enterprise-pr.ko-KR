---
title: 다중 위치 환경의 사용자 작업 환경
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.collection: Strat_SP_gtc
f1.keywords:
- NOCSH
ms.custom: ''
localization_priority: Normal
description: 다중 위치 환경의 SharePoint, OneDrive 및 Exchange 사용자 작업 환경에 대해 알아봅니다.
ms.openlocfilehash: 55c3f431474715ce03cc313a5d8d208d76b60b78
ms.sourcegitcommit: aac21bb1a7c1dfc3ba76a2db883e0457037c5667
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/28/2020
ms.locfileid: "45433799"
---
# <a name="user-experience-in-a-multi-geo-environment"></a><span data-ttu-id="6c985-103">다중 위치 환경의 사용자 작업 환경</span><span class="sxs-lookup"><span data-stu-id="6c985-103">User experience in a multi-geo environment</span></span>

<span data-ttu-id="6c985-104">OneDrive Multi-Geo 구성에 표시되는 내용은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="6c985-104">Here's what your users will see in a OneDrive Multi-Geo configuration:</span></span>

## <a name="exchange-mailbox"></a><span data-ttu-id="6c985-105">Exchange 사서함
</span><span class="sxs-lookup"><span data-stu-id="6c985-105">Exchange mailbox</span></span>

<span data-ttu-id="6c985-106">사용자의 Exchange 사서함은 원하는 데이터 위치에 프로비저닝되고 PDL이 변경되면 자동으로 재배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c985-106">A user's Exchange mailbox is provisioned to their preferred data location, and is automatically relocated if their PDL changes.</span></span> <span data-ttu-id="6c985-107">사용자는 일반적으로 다중 지역 환경에서 사용자 환경을 변경하지 않고도 웹에서 Outlook 및 Outlook을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c985-107">Users can use Outlook and Outlook on the web normally with no change in user experience in a multi-geo environment.</span></span>

## <a name="hub-sites"></a><span data-ttu-id="6c985-108">허브 사이트</span><span class="sxs-lookup"><span data-stu-id="6c985-108">Hub sites</span></span>

<span data-ttu-id="6c985-109">SharePoint 허브 사이트는 직원의 콘텐츠 검색 및 참여를 향상시키는 한편 프로젝트, 부서 또는 지역을 완전하고 일관성있게 표현합니다.</span><span class="sxs-lookup"><span data-stu-id="6c985-109">SharePoint Hub sites enhances the discovery and engagement with content for employees, while creating a complete and consistent representation of projects, departments or regions.</span></span> <span data-ttu-id="6c985-110">다중 지역 환경에서 인공위성 위치의 사이트는 허브 사이트의 위치 정보와 상관없이 허브 사이트와 쉽게 연관될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c985-110">In a multi-geo environment, sites from satellite locations can easily be associated with a hub site regardless the hub site's geo location.</span></span> <span data-ttu-id="6c985-111">사용자는 사이트의 지리적 위치에 관계없이 단일 검색 환경을 통해 허브에서 검색하고 결과를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c985-111">Users can search and get results across the hub through a single search experience, regardless of the geo location of the sites.</span></span>

## <a name="microsoft-365-app-launcher"></a><span data-ttu-id="6c985-112">Microsoft 365 앱 시작 관리자</span><span class="sxs-lookup"><span data-stu-id="6c985-112">Microsoft 365 app launcher</span></span>

<span data-ttu-id="6c985-113">앱 시작 관리자는 다중 지역을 인식하고 각 타일을 작업 부하의 적절한 지리적 위치로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6c985-113">The app launcher is multi-geo aware and will direct each tile to the appropriate geo location of the workload.</span></span> <span data-ttu-id="6c985-114">SharePoint 및 OneDrive 타일은 사용자가 제공한 지리적 위치에 해당하는 위치를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="6c985-114">The SharePoint and OneDrive tiles will point the user to the location corresponding to the user's provisioned geo location.</span></span> <span data-ttu-id="6c985-115">즉, 사용자가 중앙 위치에 OneDrive를 가지고 있고, SharePoint 타일이 중앙 위치의 SP Home을 가리키지만 해당 그룹 사이트는 PDL에 해당하는 위치에 프로비저닝됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c985-115">This means that is the user has a OneDrive in the central location, their SharePoint tile will point them to SP Home in the central location but their group site will be provisioned in the location corresponding to their PDL.</span></span> 

## <a name="office-applications"></a><span data-ttu-id="6c985-116">Office 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="6c985-116">Office applications</span></span>

<span data-ttu-id="6c985-117">Word, Excel 및 PowerPoint와 같은 Office 응용 프로그램은 각 사용자가 로그인할 때 올바른 비즈니스용 OneDrive 지리적 위치를 자동으로 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="6c985-117">Office applications such as Word, Excel, and PowerPoint will automatically detect the correct OneDrive for Business geo-location for each user when they log in.</span></span> <span data-ttu-id="6c985-118">사용자는 OneDrive 또는 SharePoint 사이트에 대한 지역별 URL을 입력할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6c985-118">Users do not need to enter the geo-specific URL for their OneDrive or SharePoint sites.</span></span>

## <a name="onedrive-for-business-sync-client"></a><span data-ttu-id="6c985-119">비즈니스용 OneDrive 동기화 클라이언트</span><span class="sxs-lookup"><span data-stu-id="6c985-119">OneDrive for Business Sync Client</span></span>

<span data-ttu-id="6c985-120">비즈니스용 OneDrive 동기화 클라이언트(버전 17.3.6943.0625 이상)는 사용자의 올바른 비즈니스용 OneDrive 지리적 위치를 자동으로 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="6c985-120">The OneDrive for Business Sync Client (version 17.3.6943.0625 and later) will automatically detect the correct OneDrive for Business geo location for the user.</span></span> <span data-ttu-id="6c985-121">동기화 클라이언트 지원에는 지리적 위치에 관계없이 그룹 기반 사이트를 동기화하는 기능이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c985-121">Synch client support includes the ability to sync groups-based sites regardless of their geo location.</span></span> <span data-ttu-id="6c985-122">참고로 Groove 동기화 클라이언트는 다중 지역에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6c985-122">Note that the Groove sync client is not supported for multi-geo.</span></span> 

## <a name="onedrive-for-business-location"></a><span data-ttu-id="6c985-123">비즈니스용 OneDrive 위치</span><span class="sxs-lookup"><span data-stu-id="6c985-123">OneDrive for Business location</span></span>

<span data-ttu-id="6c985-p106">비즈니스용 OneDrive는 기본 설정 데이터 위치에 프로비전됩니다. 사용자가 잘못된 지리적 위치(예: 이전 지리적 위치의 책갈피)가 포함된 OneDrive URL로 이동하면 자동으로 해당 지리적 위치의 OneDrive로 리디렉션됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c985-p106">Users will have their OneDrive for Business provisioned in their preferred data location. If a user navigates to a OneDrive URL that contains an incorrect geo location (such as a bookmark from a previous geo location), they are automatically redirected to the OneDrive in the appropriate geo location.</span></span>

## <a name="onedrive-ios-and-android"></a><span data-ttu-id="6c985-126">OneDrive iOS 및 Android</span><span class="sxs-lookup"><span data-stu-id="6c985-126">OneDrive iOS and Android</span></span> 

<span data-ttu-id="6c985-p107">OneDrive iOS 및 Android 모바일 앱은 지리적 위치에 관계없이 OneDrive 파일 및 공유되는 파일을 표시합니다. OneDrive 모바일 앱에서 검색하면 모든 지리적 위치의 관련 결과가 표시됩니다. 이러한 앱의 최신 버전을 다운로드하세요.</span><span class="sxs-lookup"><span data-stu-id="6c985-p107">The OneDrive iOS and Android mobile apps will show you your OneDrive files and files shared with you regardless of their geo location. Search from the OneDrive mobile apps will show relevant results from all geo locations. Please download the latest version of these apps.</span></span>

<span data-ttu-id="6c985-130">자세한 내용은 [iOS의 OneDrive](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247) 및 [Android용 OneDrive 사용](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6c985-130">See Use [OneDrive on iOS](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247) and [Use OneDrive for Android](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36) for more information.</span></span>

## <a name="onedrive-mobile-client"></a><span data-ttu-id="6c985-131">OneDrive 모바일 클라이언트</span><span class="sxs-lookup"><span data-stu-id="6c985-131">OneDrive Mobile Client</span></span> 

<span data-ttu-id="6c985-132">OneDrive Mobile Client는 다중 지역을 인식하며 모든 지리적 위치의 관련 컨텐츠 및 결과를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="6c985-132">The OneDrive Mobile Client is multi-geo aware and will display pertinent content and results from all geo locations.</span></span>

## <a name="search"></a><span data-ttu-id="6c985-133">검색</span><span class="sxs-lookup"><span data-stu-id="6c985-133">Search</span></span>

<span data-ttu-id="6c985-p108">각 지리적 위치에는 자체의 검색 인덱스와 검색 센터가 있습니다. 사용자가 검색을 하면 쿼리가 모든 지리적 위치로 전송되고 반환된 결과는 병합된 후 순위가 지정되므로 사용자는 통합된 결과를 얻게 됩니다. 사용자가 자신의 지리적 위치에 관계없이 모든 지리적 위치에서 결과를 가져옵니다. 구체적인 내용에 대해서는 [비즈니스용 OneDrive Multi-Geo에 대한 검색 구성](configure-search-for-multi-geo.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6c985-p108">Each geo location has its own search index and Search Center. When a user searches, the query is sent to all the geo locations, and the returned results are merged and then ranked so the user gets unified results. Users get results from all geo locations regardless of their own geo location. See [Configure Search for OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) for specifics.</span></span>

<span data-ttu-id="6c985-138">다음과 같은 검색 클라이언트가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c985-138">The following search clients are supported:</span></span>

-   <span data-ttu-id="6c985-139">비즈니스용 OneDrive</span><span class="sxs-lookup"><span data-stu-id="6c985-139">OneDrive for Business</span></span>

-   <span data-ttu-id="6c985-140">Delve</span><span class="sxs-lookup"><span data-stu-id="6c985-140">Delve</span></span>

-   <span data-ttu-id="6c985-141">SharePoint 홈</span><span class="sxs-lookup"><span data-stu-id="6c985-141">SharePoint Home</span></span>

-   <span data-ttu-id="6c985-142">검색 센터</span><span class="sxs-lookup"><span data-stu-id="6c985-142">The Search Center</span></span>

-   <span data-ttu-id="6c985-143">SharePoint 검색 API를 사용하는 사용자 지정 검색 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="6c985-143">Custom search applications that use the SharePoint Search API</span></span>

## <a name="sharepoint-home"></a><span data-ttu-id="6c985-144">SharePoint 홈</span><span class="sxs-lookup"><span data-stu-id="6c985-144">SharePoint Home</span></span> 

<span data-ttu-id="6c985-145">SharePoint Multi-Geo에서 SharePoint 홈은 비즈니스 위치에 대해 OneDrive가 결정한대로 사용자가 거주하는 위치에서 호스팅됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c985-145">In SharePoint Multi-Geo your SharePoint home is hosted in the location where the user resides as determined by their OneDrive for business location.</span></span> <span data-ttu-id="6c985-146">예를 들어, 사용자가 OneDrive를 유럽 위성 위치에서 호스팅하는 경우 SharePoint 홈은 유럽에서 렌더링됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c985-146">For example: if the user has their OneDrive hosted in an European satellite location, their SharePoint Home will be rendered from Europe.</span></span> <span data-ttu-id="6c985-147">SharePoint 홈에는 지리적 위치와 상관없이 사용자와 관련된 모든 콘텐츠가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c985-147">SharePoint home includes all content relevant to the user regardless of its geo location.</span></span> 

<span data-ttu-id="6c985-148">**팔로우한 사이트, 사이트의 뉴스, 최근 사용 사이트, 자주 사용하는 사이트 및 추천 사이트**</span><span class="sxs-lookup"><span data-stu-id="6c985-148">**Followed Sites, News from Sites, Recent Sites, Frequent Sites, and Suggested sites**</span></span>

<span data-ttu-id="6c985-149">사용자가 해당 콘텐츠에 대한 권한이 있는 한 콘텐츠가 호스팅되는 지역 위치에 관계 없이 이러한 모든 구성 요소가 사용자에게 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c985-149">All of these components will show up for the user regardless of the geo location where the content is hosted, so long as the user has permissions to said content.</span></span> 

<span data-ttu-id="6c985-150">**기능 링크**</span><span class="sxs-lookup"><span data-stu-id="6c985-150">**Features Links**</span></span>

<span data-ttu-id="6c985-151">관리자는 각 지리적 위치에 맞게 SharePoint 홈의 주요 링크를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c985-151">Admins may configure Featured links in SharePoint home as appropriate to each geo location.</span></span> <span data-ttu-id="6c985-152">이를 통해 관리자는 각 지역의 SP Home에서 해당 지역의 사용자에게 적합한 링크를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c985-152">This allows the admin to feature in the SP Home for each region the links that are appropriate for users in the region.</span></span> 

## <a name="sharepoint-mobile-client"></a><span data-ttu-id="6c985-153">SharePoint 모바일 클라이언트
</span><span class="sxs-lookup"><span data-stu-id="6c985-153">SharePoint Mobile Client</span></span> 

<span data-ttu-id="6c985-154">SharePoint Mobile Client는 다중 지역을 인식하며 모든 지리적 위치의 관련 컨텐츠 및 결과를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="6c985-154">The SharePoint Mobile Client is multi-geo aware and will display pertinent content and results from all geo locations.</span></span>

## <a name="sharing"></a><span data-ttu-id="6c985-155">공유</span><span class="sxs-lookup"><span data-stu-id="6c985-155">Sharing</span></span>

<span data-ttu-id="6c985-156">사용자 선택 기능은 지리적 위치에 관계없이 모든 사용자를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="6c985-156">The People Picker experience shows all users regardless of their geo location.</span></span> <span data-ttu-id="6c985-157">이를 통해 사용자는 동일한 지리적 위치 또는 다른 거주자의 지리적 위치에있는 다른 사용자와 공유 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c985-157">This allows a user to share with another user in their same geo or in any other of your tenant's geo locations.</span></span> <span data-ttu-id="6c985-158">서로 다른 지리적 위치의 콘텐츠는 사용자의 비즈니스용 OneDrive의 **공유한 항목** 보기에 표시되며 호스팅되는 지리적 위치와 상관없이 Single Sign-On 환경으로 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c985-158">Content from different geo locations will show up in the **Shared with Me** view in the user's OneDrive for Business and can be accessed with Single Sign-On experience regardless of which geo location it is hosted in.</span></span>

## <a name="teams-experience"></a><span data-ttu-id="6c985-159">팀 환경</span><span class="sxs-lookup"><span data-stu-id="6c985-159">Teams Experience</span></span>

<span data-ttu-id="6c985-160">Teams은 여러 지역 인식합니다.</span><span class="sxs-lookup"><span data-stu-id="6c985-160">Teams is multi-geo aware.</span></span> <span data-ttu-id="6c985-161">OneDrive 파일과 최근에 본 파일은 사용자의 위치 정보와 상관없이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c985-161">OneDrive files and recently viewed files are shown regardless of the user's geo location.</span></span> <span data-ttu-id="6c985-162">@는 모든 지리적 위치의 사용자와 작업합니다.</span><span class="sxs-lookup"><span data-stu-id="6c985-162">@ mentions work with users from all geo-locations.</span></span>

## <a name="user-profiles"></a><span data-ttu-id="6c985-163">사용자 프로필</span><span class="sxs-lookup"><span data-stu-id="6c985-163">User profiles</span></span>

<span data-ttu-id="6c985-p113">사용자 프로필 정보는 사용자의 지리적 위치에서 마스터됩니다. 사용자를 선택하면 해당 사용자의 해당 지리적 위치로 이동되며, 여기에서 전체 프로필 세부 정보를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c985-p113">User profile information is mastered in the user's geo location. When selecting a user, you will be directed to the appropriate geo location for the user, where you will see their full profile details.</span></span>

<span data-ttu-id="6c985-166">Delve를 끄면 SharePoint에서 다중 위치를 인식하지 않는 클래식 프로필 환경이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c985-166">If Delve is turned off, you will see the classic profile experience in SharePoint, which is not multi-geo aware.</span></span>


