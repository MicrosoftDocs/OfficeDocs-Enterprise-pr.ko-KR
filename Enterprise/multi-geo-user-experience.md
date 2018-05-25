---
title: 다중 위치 환경의 사용자 작업 환경
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
description: 다중 위치 환경의 SharePoint 및 OneDrive 사용자 작업 환경에 대해 알아봅니다.
ms.openlocfilehash: 3c7e4b6802bddc78db016c9c282f5add0c71c491
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/27/2018
---
# <a name="user-experience-in-a-multi-geo-environment"></a><span data-ttu-id="7f898-103">다중 위치 환경의 사용자 작업 환경</span><span class="sxs-lookup"><span data-stu-id="7f898-103">User experience in a multi-geo environment</span></span>

<span data-ttu-id="7f898-104">OneDrive Multi-Geo 구성에 표시되는 내용은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7f898-104">Here’s what your users will see in a OneDrive Multi-Geo configuration:</span></span>

#### <a name="users-onedrive-for-business-location"></a><span data-ttu-id="7f898-105">사용자의 비즈니스용 OneDrive 위치</span><span class="sxs-lookup"><span data-stu-id="7f898-105">User’s OneDrive for Business location</span></span>

<span data-ttu-id="7f898-p101">비즈니스용 OneDrive는 기본 설정 데이터 위치에 프로비전됩니다. 사용자가 잘못된 지리적 위치(예: 이전 지리적 위치의 책갈피)가 포함된 OneDrive URL로 이동하면 자동으로 해당 지리적 위치의 OneDrive로 리디렉션됩니다.</span><span class="sxs-lookup"><span data-stu-id="7f898-p101">Users will have their OneDrive for Business provisioned in their preferred data location. If a user navigates to a OneDrive URL that contains an incorrect geo-location (such as a bookmark from a previous geo-location), they are automatically redirected to the OneDrive in the appropriate geo-location.</span></span>

#### <a name="sharing"></a><span data-ttu-id="7f898-108">공유</span><span class="sxs-lookup"><span data-stu-id="7f898-108">Sharing</span></span>

<span data-ttu-id="7f898-p102">사용자 선택 환경에는 지리적 위치에 관계 없이 모든 사용자가 표시됩니다. 따라서 사용자는 같은 지역 또는 테넌트 지리적 위치의 다른 지역에 있는 다른 사용자와 공유할 수 있습니다. 다른 지리적 위치의 콘텐츠가 비즈니스용 OneDrive의 **공유한 항목** 보기에 표시되며, 호스트된 지리적 위치에 관계없이 Single-Sign-On 환경에서 액세스될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f898-p102">The People Picker experience shows all users regardless of their geo location. This allows a user to share with another user in their same geo or in any other of your tenant’s geo locations. Content from different geo locations will show up in the **Shared with Me** view in the user's OneDrive for Business and can be accessed with Single-Sign-On experience regardless of which geo-location it is hosted in.</span></span>

#### <a name="office-applications"></a><span data-ttu-id="7f898-112">Office 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="7f898-112">Office applications</span></span>

<span data-ttu-id="7f898-p103">Word, Excel 및 PowerPoint와 같은 Office 응용 프로그램은 각 사용자가 로그인할 때 올바른 비즈니스용 OneDrive 지리적 위치를 자동으로 검색합니다. 따라서 사용자는 해당 OneDrive에 대한 지역별 URL을 입력할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7f898-p103">Office applications such as Word, Excel, and PowerPoint will automatically detect the correct OneDrive for Business geo-location for each user when they log in. Users do not need to enter the geo-specific URL for their OneDrive.</span></span>

#### <a name="onedrive-for-business-sync-client"></a><span data-ttu-id="7f898-115">비즈니스용 OneDrive 동기화 클라이언트</span><span class="sxs-lookup"><span data-stu-id="7f898-115">OneDrive for Business Windows Sync client</span></span>

<span data-ttu-id="7f898-116">비즈니스용 OneDrive 동기화 클라이언트(버전 17.3.6943.0625 이상)는 사용자의 올바른 비즈니스용 OneDrive 지리적 위치를 자동으로 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="7f898-116">The OneDrive for Business Sync Client (version 17.3.6943.0625 and later) will automatically detect the correct OneDrive for Business geo location for the user.</span></span>

#### <a name="office-365-app-launcher"></a><span data-ttu-id="7f898-117">Office 365 앱 시작 관리자</span><span class="sxs-lookup"><span data-stu-id="7f898-117">Office 365 app launcher</span></span>

<span data-ttu-id="7f898-p104">앱 시작 관리자는 다중 위치를 인식하며, 각 타일을 워크로드의 해당 지리적 위치에 연결합니다. OneDrive 타일은 사용자의 OneDrive 라이브러리가 호스트된 올바른 지리적 위치를 가리키지만, SharePoint 타일은 모든 사용자를 팀 사이트가 호스트된 중앙 위치에 연결되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f898-p104">The app launcher is Multi-Geo aware and will direct each tile to the appropriate geo location of the workload. The OneDrive tile points to the correct geo location where the user’s OneDrive library is hosted, while the SharePoint tile will point all users to the central location, as team sites are still hosted there.</span></span>

#### <a name="delve-user-profiles"></a><span data-ttu-id="7f898-120">Delve 사용자 프로필</span><span class="sxs-lookup"><span data-stu-id="7f898-120">Delve User profiles</span></span>

<span data-ttu-id="7f898-p105">사용자 프로필 정보는 사용자의 지리적 위치에서 마스터됩니다. 사용자를 선택하면 해당 사용자의 해당 지리적 위치로 이동되며, 여기에서 전체 프로필 세부 정보를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f898-p105">User profile information is mastered in the user's geo location. When selecting a user, you will be directed to the appropriate geo location for the user, where you will see their full profile details.</span></span>

<span data-ttu-id="7f898-123">Delve를 끄면 SharePoint에서 다중 위치를 인식하지 않는 클래식 프로필 환경이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7f898-123">If Delve is turned off, you will see the classic profile experience in SharePoint, which is not multi-geo aware.</span></span>

#### <a name="delve"></a><span data-ttu-id="7f898-124">Delve</span><span class="sxs-lookup"><span data-stu-id="7f898-124">Delve</span></span>

<span data-ttu-id="7f898-125">위성 인스턴스에 있는 Office 365 사용자의 경우, Delve가 다른 지역의 사용자가 쓴 SharePoint 블로그 게시물에는 연결되지 않고, 해당 SharePoint 블로그 사이트에만 연결된다는 점을 제외하고, Delve Multi-Geo가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="7f898-125">For Office 365 users who are in the satellite instances, Delve Multi-Geo is supported, with the limitation that Delve doesn’t link to SharePoint blog posts written by users in other regions, only to their SharePoint blog sites.</span></span>

#### <a name="search"></a><span data-ttu-id="7f898-126">검색</span><span class="sxs-lookup"><span data-stu-id="7f898-126">Search</span></span>

<span data-ttu-id="7f898-p106">각 지리적 위치에는 자체의 검색 인덱스와 검색 센터가 있습니다. 사용자가 검색을 하면 쿼리가 모든 지리적 위치로 전송되고 반환된 결과는 병합된 후 순위가 지정되므로 사용자는 통합된 결과를 얻게 됩니다. 사용자가 자신의 지리적 위치에 관계없이 모든 지리적 위치에서 결과를 가져옵니다. 구체적인 내용에 대해서는 [비즈니스용 OneDrive Multi-Geo에 대한 검색 구성](configure-search-for-multi-geo.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7f898-p106">Each geo location has its own search index and Search Center. When a user searches, the query is sent to all the geo locations, and the returned results are merged and then ranked so the user gets unified results. Users get results from all geo locations regardless of their own geo location. See [Configure Search for OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) for specifics.</span></span>

<span data-ttu-id="7f898-131">다음과 같은 검색 클라이언트가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="7f898-131">The following search clients are supported:</span></span>

-   <span data-ttu-id="7f898-132">비즈니스용 OneDrive</span><span class="sxs-lookup"><span data-stu-id="7f898-132">OneDrive for Business</span></span>

-   <span data-ttu-id="7f898-133">Delve</span><span class="sxs-lookup"><span data-stu-id="7f898-133">Delve</span></span>

-   <span data-ttu-id="7f898-134">SharePoint 홈</span><span class="sxs-lookup"><span data-stu-id="7f898-134">SharePoint Home</span></span>

-   <span data-ttu-id="7f898-135">검색 센터</span><span class="sxs-lookup"><span data-stu-id="7f898-135">The Search Center</span></span>

-   <span data-ttu-id="7f898-136">SharePoint 검색 API를 사용하는 사용자 지정 검색 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="7f898-136">Custom search applications that use the SharePoint Search API</span></span>

#### <a name="onedrive-ios-and-android"></a><span data-ttu-id="7f898-137">OneDrive iOS 및 Android</span><span class="sxs-lookup"><span data-stu-id="7f898-137">OneDrive iOS and Android</span></span> 

<span data-ttu-id="7f898-p107">OneDrive iOS 및 Android 모바일 앱은 지리적 위치에 관계없이 OneDrive 파일 및 공유되는 파일을 표시합니다. OneDrive 모바일 앱에서 검색하면 모든 지리적 위치의 관련 결과가 표시됩니다. 이러한 앱의 최신 버전을 다운로드하세요.</span><span class="sxs-lookup"><span data-stu-id="7f898-p107">The OneDrive iOS and Android mobile apps will show you your OneDrive files and files shared with you regardless of their geo location. Search from the OneDrive mobile apps will show relevant results from all geo locations. Please download the latest version of these apps.</span></span>

<span data-ttu-id="7f898-141">자세한 내용은 [iOS의 OneDrive](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247) 및 [Android용 OneDrive 사용](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7f898-141">See Use [OneDrive on iOS](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247) and [Use OneDrive for Android](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36) for more information.</span></span>

#### <a name="teams-experience"></a><span data-ttu-id="7f898-142">팀 환경</span><span class="sxs-lookup"><span data-stu-id="7f898-142">Teams Experience</span></span>

<span data-ttu-id="7f898-p108">팀은 다중 위치를 인식합니다. OneDrive 파일 및 최근에 본 파일은 사용자의 지리적 위치에 관계 없이 표시됩니다. @ 멘션은 모든 지리적 위치의 사용자에게 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7f898-p108">Teams is multi-geo aware. OneDrive files and recently viewed files are shown regardless of the user’s geo location. @ mentions work with users from all geo-locations.</span></span>
