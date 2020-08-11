---
title: 지역 관리자 추가 또는 제거
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.collection: SPO_Content
localization_priority: Normal
f1.keywords:
- NOCSH
description: 각 지리적 위치에 대해 개별 관리자를 구성 해야 하나요? Microsoft 365 Multi-Geo에서 지역 관리자를 추가하거나 제거하는 방법에 대해 알아봅니다.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: b69ff352ae0e5ceb55200e0ed034e278808cdc9f
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605824"
---
# <a name="add-or-remove-a-geo-administrator-in-microsoft-365-multi-geo"></a><span data-ttu-id="916ce-104">Microsoft 365 Multi-Geo에서 지역 관리자를 추가하거나 제거</span><span class="sxs-lookup"><span data-stu-id="916ce-104">Add or remove a geo administrator in Microsoft 365 Multi-Geo</span></span>

<span data-ttu-id="916ce-105">테넌트가 있는 지리적 위치마다 별도의 관리자를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="916ce-105">You can configure separate administrators for each geo location that you have in your tenant.</span></span> <span data-ttu-id="916ce-106">이러한 관리자는 지리적 위치와 관련된 SharePoint Online 및 OneDrive 설정에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="916ce-106">These administrators will have access to the SharePoint Online and OneDrive settings that are specific to their geo location.</span></span>

<span data-ttu-id="916ce-107">용어 저장소와 같은 일부 서비스는 중앙 위치에서 관리되고 위성 위치로 복제됩니다.</span><span class="sxs-lookup"><span data-stu-id="916ce-107">Some services - such as the term store - are administered from the central location and replicated to satellite locations.</span></span> <span data-ttu-id="916ce-108">중앙 위치의 지역 관리자는 이러한 위치 정보에 액세스할 수 있지만 위성 위치 지역 관리자는 액세스하지 못합니다.</span><span class="sxs-lookup"><span data-stu-id="916ce-108">The geo admin for the central location has access to these, whereas geo admins for satellite locations don't.</span></span>

<span data-ttu-id="916ce-109">전역 관리자와 SharePoint Online 관리자는 중앙 위치 및 모든 위성 위치의 설정에 계속 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="916ce-109">Global administrators and SharePoint Online administrators continue to have access to settings in the central location and all satellite locations.</span></span>

## <a name="configuring-geo-administrators"></a><span data-ttu-id="916ce-110">지역 관리자 구성</span><span class="sxs-lookup"><span data-stu-id="916ce-110">Configuring geo administrators</span></span>

<span data-ttu-id="916ce-111">지역 관리자를 구성하려면 SharePoint Online PowerShell 모듈이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="916ce-111">Configuring geo admins requires SharePoint Online PowerShell module.</span></span>

<span data-ttu-id="916ce-112">[Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService)를 사용하여 지역 관리자를 추가할 지리적 위치의 관리 센터에 연결합니다. (예 : Connect-SPOService  https://ContosoEUR-admin.sharepoint.com.)</span><span class="sxs-lookup"><span data-stu-id="916ce-112">Use [Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) to connect to the admin center of the geo location where you want to add the geo admin. (For example, Connect-SPOService  https://ContosoEUR-admin.sharepoint.com.)</span></span>

<span data-ttu-id="916ce-113">어떤 위치의 기존 지역 관리자를 보려면 다음을 실행하세요. `Get-SPOGeoAdministrator` </span><span class="sxs-lookup"><span data-stu-id="916ce-113">To view the existing geo admins of a location, run `Get-SPOGeoAdministrator`</span></span>

### <a name="adding-a-user-as-a-geo-admin"></a><span data-ttu-id="916ce-114">지역 관리자 권한으로 사용자를 추가</span><span class="sxs-lookup"><span data-stu-id="916ce-114">Adding a user as a geo admin</span></span>

<span data-ttu-id="916ce-115">지역 관리자 권한으로로 사용자를 추가하려면 다음을 실행하세요. `Add-SPOGeoAdministrator -UserPrincipalName <UPN>`</span><span class="sxs-lookup"><span data-stu-id="916ce-115">To add a user as a geo admin, run `Add-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

<span data-ttu-id="916ce-116">한 위치의 지역 관리자를 제거하려면 다음을 실행하세요.  `Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`</span><span class="sxs-lookup"><span data-stu-id="916ce-116">To remove a user as a Geo Admin of a location, run  `Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

### <a name="adding-a-group-as-a-geo-admin"></a><span data-ttu-id="916ce-117">지역 관리자 권한으로 그룹을 추가</span><span class="sxs-lookup"><span data-stu-id="916ce-117">Adding a group as a geo admin</span></span>

<span data-ttu-id="916ce-118">지역 관리자 권한으로 보안 그룹이나 메일 사용 가능 보안 그룹을 추가할 수 있습니다. (메일 그룹 및 Microsoft 365 그룹은 지원되지 않습니다.)</span><span class="sxs-lookup"><span data-stu-id="916ce-118">You can add a security group or a mail-enabled security group as a geo admin. (Distribution groups and Microsoft 365 Groups are not supported.)</span></span>

<span data-ttu-id="916ce-119">지역 관리자 권한으로 그룹을 추가하려면 다음을 실행하세요. `Add-SPOGeoAdministrator -GroupAlias <alias>`</span><span class="sxs-lookup"><span data-stu-id="916ce-119">To add a group as a geo administrator, run `Add-SPOGeoAdministrator -GroupAlias <alias>`</span></span>

<span data-ttu-id="916ce-120">지역 관리자 권한으로 그룹을 제거하려면 다음을 실행하세요. `Remove-SPOGeoAdministrator -GroupAlias <alias>`</span><span class="sxs-lookup"><span data-stu-id="916ce-120">To remove a group as a geo administrator, run `Remove-SPOGeoAdministrator -GroupAlias <alias>`</span></span>

<span data-ttu-id="916ce-121">모든 보안 그룹이 그룹 별칭이 있는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="916ce-121">Note that not all security groups have a group alias.</span></span> <span data-ttu-id="916ce-122">별칭이 없는 보안 그룹을 추가하려면 [Get-MsolGroup](https://docs.microsoft.com/powershell/module/msonline/get-msolgroup)을 실행하여 그룹 목록을 검색하고 보안 그룹의 ObjectID를 찾은 다음 다음을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="916ce-122">If you want to add a security group that does not have an alias, run [Get-MsolGroup](https://docs.microsoft.com/powershell/module/msonline/get-msolgroup) to retrieve a list of groups, find your security group's ObjectID, and then run:</span></span>

`Add-SPOGeoAdministrator -ObjectID <ObjectID>`

<span data-ttu-id="916ce-123">ObjectID를 사용하여 그룹을 제거하려면 다음을 실행하세요. `Remove-SPOGeoAdministrator -ObjectID <ObjectID>`</span><span class="sxs-lookup"><span data-stu-id="916ce-123">To remove a group by using the ObjectID, run `Remove-SPOGeoAdministrator -ObjectID <ObjectID>`</span></span>

## <a name="related-topics"></a><span data-ttu-id="916ce-124">관련 항목</span><span class="sxs-lookup"><span data-stu-id="916ce-124">Related topics</span></span>

[<span data-ttu-id="916ce-125">Add-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="916ce-125">Add-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/add-spogeoadministrator)

[<span data-ttu-id="916ce-126">Get-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="916ce-126">Get-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spogeoadministrator)

[<span data-ttu-id="916ce-127">Remove-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="916ce-127">Remove-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/remove-spogeoadministrator)

[<span data-ttu-id="916ce-128">보안 그룹에 대한 별칭(MailNickName) 설정</span><span class="sxs-lookup"><span data-stu-id="916ce-128">Set an alias (MailNickName) for a security group</span></span>](https://docs.microsoft.com/powershell/module/azuread/set-azureadgroup)