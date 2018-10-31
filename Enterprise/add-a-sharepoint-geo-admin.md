---
title: 지역 관리자 추가 또는 제거
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: 추가 또는 OneDrive에 대 한 비즈니스 다중-지리적으로 분산 지리적으로 분산 관리자를 제거 하는 방법에 알아봅니다.
ms.openlocfilehash: 4e8c8bec148d5a4e7e55ffa2b08a49cd2ea6aa0a
ms.sourcegitcommit: a3e2b2e58c328238c15d3f9daf042ea3de9d66be
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/30/2018
ms.locfileid: "25849814"
---
# <a name="add-or-remove-a-geo-administrator-in-onedrive-for-busniess-multi-geo"></a><span data-ttu-id="8d75c-103">추가 또는 OneDrive에 대 한 Busniess 다중-지리적으로 분산 지리적으로 분산 관리자 제거</span><span class="sxs-lookup"><span data-stu-id="8d75c-103">Add or remove a geo administrator in OneDrive for Busniess Multi-Geo</span></span>

<span data-ttu-id="8d75c-p101">테 넌 트에 있는 각 지리적 위치에 대 한 별도 관리자를 구성할 수 있습니다. 이러한 관리자에는 해당 지리적 위치에만 적용 되는 SharePoint Online 및 OneDrive 설정에 액세스할을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d75c-p101">You can configure separate administrators for each geo location that you have in your tenant. These administrators will have access to the SharePoint Online and OneDrive settings that are specific to their geo location.</span></span>

<span data-ttu-id="8d75c-p102">용어 저장소-등의 일부 서비스-중앙 위치에서 관리 되며 위성 위치에 복제 됩니다. 중앙 위치에 대 한 지리적으로 분산 관리는 위성 위치에 대 한 지리적으로 분산 admins 하지 하는 반면, 여기에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d75c-p102">Some services - such as the term store - are administered from the central location and replicated to satellite locations. The geo admin for the central location has access to these, whereas geo admins for satellite locations don’t.</span></span>

<span data-ttu-id="8d75c-108">전역 관리자 및 SharePoint Online 관리자가 중앙 위치 및 위성 위치를 모두의 설정에 대 한 액세스를 계속 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d75c-108">Global administrators and SharePoint Online administrators continue to have access to settings in the central location and all satellite locations.</span></span>

## <a name="configuring-geo-administrators"></a><span data-ttu-id="8d75c-109">지리적으로 분산 관리자 구성</span><span class="sxs-lookup"><span data-stu-id="8d75c-109">Configuring geo administrators</span></span>

<span data-ttu-id="8d75c-110">지리적으로 분산 관리자를 구성 하려면 SharePoint Online PowerShell 모듈이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d75c-110">Configuring geo admins requires SharePoint Online PowerShell module.</span></span>

<span data-ttu-id="8d75c-111">[Connect-sposervice](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) 를 사용 하 여 지리적으로 분산 관리자를 추가 하려는 지리적으로 분산 위치의 관리 센터에 연결 하려면 (예: Connect-sposervicehttps://ContosoEUR-admin.sharepoint.com.)</span><span class="sxs-lookup"><span data-stu-id="8d75c-111">Use [Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) to connect to the admin center of the geo location where you want to add the geo admin. (For example, Connect-SPOService  https://ContosoEUR-admin.sharepoint.com.)</span></span>

<span data-ttu-id="8d75c-112">실행 하는 기존 지리적으로 분산 admins의 위치를 보려면`Get-SPOGeoAdministrator`</span><span class="sxs-lookup"><span data-stu-id="8d75c-112">To view the existing geo admins of a location, run `Get-SPOGeoAdministrator`</span></span>

### <a name="adding-a-user-as-a-geo-admin"></a><span data-ttu-id="8d75c-113">지리적으로 분산 관리 권한으로 사용자 추가 (영문)</span><span class="sxs-lookup"><span data-stu-id="8d75c-113">Adding a user as a geo admin</span></span>

<span data-ttu-id="8d75c-114">지리적으로 분산 관리 권한으로 사용자를 추가, 실행`Add-SPOGeoAdministrator -UserPrincipalName <UPN>`</span><span class="sxs-lookup"><span data-stu-id="8d75c-114">To add a user as a geo admin, run `Add-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

<span data-ttu-id="8d75c-115">사용자의 위치를 지리적으로 분산 관리자를 제거 하려면 다음을 실행합니다`Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`</span><span class="sxs-lookup"><span data-stu-id="8d75c-115">To remove a user as a Geo Admin of a location, run  `Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

### <a name="adding-a-group-as-a-geo-admin"></a><span data-ttu-id="8d75c-116">지리적으로 분산 관리자 그룹 추가 (영문)</span><span class="sxs-lookup"><span data-stu-id="8d75c-116">Adding a group as a geo admin</span></span>

<span data-ttu-id="8d75c-117">지리적으로 분산 관리자로 보안 그룹 또는 메일 사용이 가능한 보안 그룹을 추가할 수 있습니다. (메일 그룹 및 Office 365 그룹 지원 되지 않습니다.)</span><span class="sxs-lookup"><span data-stu-id="8d75c-117">You can add a security group or a mail-enabled security group as a geo admin. (Distribution groups and Office 365 Groups are not supported.)</span></span>

<span data-ttu-id="8d75c-118">지리적으로 분산 관리자 권한으로 그룹을 추가 하려면 실행`Add-SPOGeoAdministrator -GroupAlias <alias>`</span><span class="sxs-lookup"><span data-stu-id="8d75c-118">To add a group as a geo administrator, run `Add-SPOGeoAdministrator -GroupAlias <alias>`</span></span>

<span data-ttu-id="8d75c-119">지리적으로 분산 관리자 권한으로 그룹을 제거 하려면 다음을 실행합니다`Remove-SPOGeoAdministrator -GroupAlias <alias>`</span><span class="sxs-lookup"><span data-stu-id="8d75c-119">To remove a group as a geo administrator, run `Remove-SPOGeoAdministrator -GroupAlias <alias>`</span></span>

<span data-ttu-id="8d75c-p103">참고는 일부 보안 그룹의 경우 그룹 별칭입니다. 그룹 목록을 검색 하려면 [Get MsolGroup](https://docs.microsoft.com/en-us/powershell/module/msonline/get-msolgroup) 실행 하는 별칭 없는 보안 그룹을 추가 하려는 경우 보안 그룹의 ObjectID 찾아 다음을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d75c-p103">Note that not all security groups have a group alias. If you want to add a security group that does not have an alias, run [Get-MsolGroup](https://docs.microsoft.com/en-us/powershell/module/msonline/get-msolgroup) to retrieve a list of groups, find your security group's ObjectID, and then run:</span></span>

`Add-SPOGeoAdministrator -ObjectID <ObjectID>`

<span data-ttu-id="8d75c-122">실행 하는 ObjectID를 사용 하 여 그룹을 제거 하려면`Remove-SPOGeoAdministrator -ObjectID <ObjectID>`</span><span class="sxs-lookup"><span data-stu-id="8d75c-122">To remove a group by using the ObjectID, run `Remove-SPOGeoAdministrator -ObjectID <ObjectID>`</span></span>

### <a name="accessing-the-admin-center-for-a-specific-geo-location"></a><span data-ttu-id="8d75c-123">특정 지리적 위치에 대 한 관리 센터 액세스 (영문)</span><span class="sxs-lookup"><span data-stu-id="8d75c-123">Accessing the admin center for a specific geo-location</span></span>

<span data-ttu-id="8d75c-124">지리적 위치에 대 한 OneDrive 설정을 관리 하려면 관리자가 다음 URL 형식을 사용 하 여 직접 OneDrive 관리 센터에 액세스 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d75c-124">To administer OneDrive settings for their geo location, admins must access the OneDrive admin center directly using the following URL format:</span></span>

<span data-ttu-id="8d75c-125">https://admin.onedrive.com/?geo=<*지리적으로 분산*></span><span class="sxs-lookup"><span data-stu-id="8d75c-125">https://admin.onedrive.com/?geo=<*geo*></span></span>

<span data-ttu-id="8d75c-126">캐나다에 대 한 OneDrive 관리 센터에는 예: https://admin.onedrive.com/?geo=CAN합니다.</span><span class="sxs-lookup"><span data-stu-id="8d75c-126">For example, the OneDrive admin center for Canada is located at: https://admin.onedrive.com/?geo=CAN.</span></span>

## <a name="see-also"></a><span data-ttu-id="8d75c-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8d75c-127">See Also</span></span>

[<span data-ttu-id="8d75c-128">추가 SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="8d75c-128">Add-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/add-spogeoadministrator)

[<span data-ttu-id="8d75c-129">Get-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="8d75c-129">Get-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spogeoadministrator)

[<span data-ttu-id="8d75c-130">SPOGeoAdministrator 제거</span><span class="sxs-lookup"><span data-stu-id="8d75c-130">Remove-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/remove-spogeoadministrator)

[<span data-ttu-id="8d75c-131">보안 그룹에 대 한 별칭 (MailNickName) 설정</span><span class="sxs-lookup"><span data-stu-id="8d75c-131">Set an alias (MailNickName) for a security group</span></span>](https://docs.microsoft.com/en-us/powershell/module/azuread/set-azureadgroup)