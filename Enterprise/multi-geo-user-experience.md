---
title: Multgeo 환경에서 사용자 환경
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: 다중-지리적으로 분산 환경에서 SharePoint와 OneDrive 사용자 환경에 알아봅니다.
ms.openlocfilehash: 91837883ef7c970674a500afa4fda9adfafc6d5b
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/03/2018
---
# <a name="user-experience-in-a-multi-geo-environment"></a><span data-ttu-id="1505c-103">다중-지리적으로 분산 환경에서 사용자 환경</span><span class="sxs-lookup"><span data-stu-id="1505c-103">User experience in a multi-geo environment</span></span>

<span data-ttu-id="1505c-104">OneDrive 다중-지리적으로 분산 구성에서 참조 하는 사용자에 게는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1505c-104">Here’s what your users will see in a OneDrive Multi-Geo configuration:</span></span>

#### <a name="users-onedrive-for-business-location"></a><span data-ttu-id="1505c-105">비즈니스 위치에 대 한 사용자의 OneDrive</span><span class="sxs-lookup"><span data-stu-id="1505c-105">User’s OneDrive for Business location</span></span>

<span data-ttu-id="1505c-p101">사용자는 자신의 OneDrive for Business의 기본 데이터 위치에 프로 비전을 갖게 됩니다. 사용자가 OneDrive URL (예: 이전 지리적 위치에서 책갈피) 잘못 된 지리적 위치를 포함 하는 탐색 하는 경우 자동으로 적절 한 지리적 위치에 OneDrive로 리디렉션됩니다 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1505c-p101">Users will have their OneDrive for Business provisioned in their preferred data location. If a user navigates to a OneDrive URL that contains an incorrect geo-location (such as a bookmark from a previous geo-location), they are automatically redirected to the OneDrive in the appropriate geo-location.</span></span>

#### <a name="sharing"></a><span data-ttu-id="1505c-108">공유</span><span class="sxs-lookup"><span data-stu-id="1505c-108">Sharing</span></span>

<span data-ttu-id="1505c-p102">사용자 선택 경험의 지리적 위치에 관계 없이 모든 사용자를 표시합니다. 이 사용자를 동일한 지리적으로 분산 또는 테 넌 트의 지리적 위치의 다른 모든 다른 사용자와 공유할 수 있습니다. 콘텐츠에서 서로 다른 지리적으로 분산 위치 비즈니스에 대 한 사용자의 OneDrive에서 **공유 항목** 보기에서 볼 수 있으며 Single Sign-on 환경에서 호스팅되는 어떤 지리적 위치에 관계 없이 사용 하 여 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1505c-p102">The People Picker experience shows all users regardless of their geo location. This allows a user to share with another user in their same geo or in any other of your tenant’s geo locations. Content from different geo locations will show up in the **Shared with Me** view in the user's OneDrive for Business and can be accessed with Single-Sign-On experience regardless of which geo-location it is hosted in.</span></span>

#### <a name="office-applications"></a><span data-ttu-id="1505c-112">Office 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="1505c-112">Office applications</span></span>

<span data-ttu-id="1505c-p103">Word, Excel 및 PowerPoint와 같은 office 응용 프로그램 로그인 할 때 비즈니스 지리적으로 분산-각 사용자에 대 한 위치에 대 한 올바른 OneDrive을 자동으로 검색 됩니다. 사용자가 자신의 onedrive 지리적으로 분산 특정 URL을 입력 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1505c-p103">Office applications such as Word, Excel, and PowerPoint will automatically detect the correct OneDrive for Business geo-location for each user when they log in. Users do not need to enter the geo-specific URL for their OneDrive.</span></span>

#### <a name="onedrive-for-business-sync-client"></a><span data-ttu-id="1505c-115">비즈니스용 OneDrive 비즈니스 동기화 클라이언트</span><span class="sxs-lookup"><span data-stu-id="1505c-115">OneDrive for Business Sync Client</span></span>

<span data-ttu-id="1505c-116">비즈니스 동기화 클라이언트에 대 한 OneDrive (버전 17.3.6943.0625 이상)의 사용자에 대 한 비즈니스 지리적 위치에 대 한 올바른 OneDrive를 자동으로 검색 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1505c-116">The OneDrive for Business Sync Client (version 17.3.6943.0625 and later) will automatically detect the correct OneDrive for Business geo location for the user.</span></span>

#### <a name="office-365-app-launcher"></a><span data-ttu-id="1505c-117">Office 365 앱 시작 관리자</span><span class="sxs-lookup"><span data-stu-id="1505c-117">Office 365 app launcher</span></span>

<span data-ttu-id="1505c-p104">응용 프로그램 시작 관리자를 인식 다중 지리적 이며 각 타일 작업량의 적절 한 지리적 위치에 직접 보내도록 지정 합니다. OneDrive는 사용자의 OneDrive 라이브러리 호스팅되, SharePoint 타일은 위치를 가리키도록 모든 사용자에 게 중앙, 팀 사이트는 다음과 같은 호스팅됩니다 여전히으로 하는 동안 올바른 지리적 위치에 있는 점을 바둑판식으로 배열 합니다.</span><span class="sxs-lookup"><span data-stu-id="1505c-p104">The app launcher is Multi-Geo aware and will direct each tile to the appropriate geo location of the workload. The OneDrive tile points to the correct geo location where the user’s OneDrive library is hosted, while the SharePoint tile will point all users to the central location, as team sites are still hosted there.</span></span>

#### <a name="delve-user-profiles"></a><span data-ttu-id="1505c-120">사용자 프로필을 굴</span><span class="sxs-lookup"><span data-stu-id="1505c-120">Delve User profiles</span></span>

<span data-ttu-id="1505c-p105">사용자 프로필 정보를 사용자의 지리적 위치에 마스터 됩니다. 사용자를 선택할 때는 자신의 전체 프로필 정보 표시는 사용자에 대 한 적절 한 지리적 위치에 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1505c-p105">User profile information is mastered in the user's geo location. When selecting a user, you will be directed to the appropriate geo location for the user, where you will see their full profile details.</span></span>

<span data-ttu-id="1505c-123">Delve를 해제 하는 다중-지리적으로 분산 인식 없는 SharePoint, 경험 클래식 프로필을 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1505c-123">If Delve is turned off, you will see the classic profile experience in SharePoint, which is not multi-geo aware.</span></span>

#### <a name="delve"></a><span data-ttu-id="1505c-124">Delve</span><span class="sxs-lookup"><span data-stu-id="1505c-124">Delve</span></span>

<span data-ttu-id="1505c-125">Office 365에 있는 사용자가 위성 인스턴스에 대 한 다중 Geo 굴 Delve SharePoint 블로그 사이트에만 다른 지역에서 사용자가 작성 하는 SharePoint 블로그 게시물에 연결 하지는 제한 된 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1505c-125">For Office 365 users who are in the satellite instances, Delve Multi-Geo is supported, with the limitation that Delve doesn’t link to SharePoint blog posts written by users in other regions, only to their SharePoint blog sites.</span></span>

#### <a name="search"></a><span data-ttu-id="1505c-126">검색</span><span class="sxs-lookup"><span data-stu-id="1505c-126">Search</span></span>

<span data-ttu-id="1505c-p106">각 지리적 위치에는 자체 검색 인덱스와 검색 센터에 있습니다. 사용자를 검색 하는 경우 쿼리 지리적 위치를 모두에 전송 되 고 반환 된 결과 병합 된 셀 및 사용자 가져옵니다 통합된 결과 하므로 순위를 지정한 다음. 사용자가 자신의 지리적 위치에 관계 없이 모든 지리적 위치에서 결과를 가져옵니다. 자세한 내용은 [OneDrive에 대 한 비즈니스 다중-지리적으로 분산에 대 한 검색 구성](configure-search-for-multi-geo.md) 을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="1505c-p106">Each geo location has its own search index and Search Center. When a user searches, the query is sent to all the geo locations, and the returned results are merged and then ranked so the user gets unified results. Users get results from all geo locations regardless of their own geo location. See [Configure Search for OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) for specifics.</span></span>

<span data-ttu-id="1505c-131">다음과 같은 검색 클라이언트가 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1505c-131">The following search clients are supported:</span></span>

-   <span data-ttu-id="1505c-132">비즈니스용 OneDrive</span><span class="sxs-lookup"><span data-stu-id="1505c-132">OneDrive for Business</span></span>

-   <span data-ttu-id="1505c-133">Delve</span><span class="sxs-lookup"><span data-stu-id="1505c-133">Delve</span></span>

-   <span data-ttu-id="1505c-134">SharePoint 홈</span><span class="sxs-lookup"><span data-stu-id="1505c-134">SharePoint Home</span></span>

-   <span data-ttu-id="1505c-135">검색 센터</span><span class="sxs-lookup"><span data-stu-id="1505c-135">The Search Center</span></span>

-   <span data-ttu-id="1505c-136">SharePoint 검색 API를 사용 하는 사용자 지정 검색 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="1505c-136">Custom search applications that use the SharePoint Search API</span></span>

#### <a name="onedrive-ios-and-android"></a><span data-ttu-id="1505c-137">OneDrive iOS 및 Android</span><span class="sxs-lookup"><span data-stu-id="1505c-137">OneDrive iOS and Android</span></span> 

<span data-ttu-id="1505c-p107">OneDrive iOS 및 Android 모바일 앱 안내해 OneDrive 파일 및 해당 지리적 위치에 관계 없이 사용자와 공유 하는 파일입니다. OneDrive 모바일 응용 프로그램에서 검색에는 모든 지리적 위치에서 관련이 있는 결과 표시 됩니다. 이러한 응용 프로그램의 최신 버전을 다운로드 하십시오.</span><span class="sxs-lookup"><span data-stu-id="1505c-p107">The OneDrive iOS and Android mobile apps will show you your OneDrive files and files shared with you regardless of their geo location. Search from the OneDrive mobile apps will show relevant results from all geo locations. Please download the latest version of these apps.</span></span>

<span data-ttu-id="1505c-141">자세한 내용은 사용 [iOS에 OneDrive](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247) 및 [Android에 대 한 사용 OneDrive](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36) 를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="1505c-141">See Use [OneDrive on iOS](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247) and [Use OneDrive for Android](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36) for more information.</span></span>

#### <a name="teams-experience"></a><span data-ttu-id="1505c-142">팀 환경</span><span class="sxs-lookup"><span data-stu-id="1505c-142">Teams Experience</span></span>

<span data-ttu-id="1505c-p108">팀은 다중-지리적으로 분산을 인식 합니다. OneDrive 파일 및 최근에 본된 파일은 사용자의 지리적 위치에 관계 없이 표시 됩니다. @ 모든 지리적 위치에서 사용자와 멘 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="1505c-p108">Teams is multi-geo aware. OneDrive files and recently viewed files are shown regardless of the user’s geo location. @ mentions work with users from all geo-locations.</span></span>
