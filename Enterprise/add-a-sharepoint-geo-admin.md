---
title: 지리적으로 분산 관리자 추가 또는 제거
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: 추가 또는 OneDrive에 대 한 비즈니스 다중-지리적으로 분산 지리적으로 분산 관리자를 제거 하는 방법에 알아봅니다.
ms.openlocfilehash: 0007f1ac3c73fa7a2ada562f8da65215f80744ca
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/03/2018
---
# <a name="add-or-remove-a-geo-administrator-in-onedrive-for-busniess-multi-geo"></a><span data-ttu-id="1a832-103">추가 또는 OneDrive에 대 한 Busniess 다중-지리적으로 분산 지리적으로 분산 관리자 제거</span><span class="sxs-lookup"><span data-stu-id="1a832-103">Add or remove a geo administrator in OneDrive for Busniess Multi-Geo</span></span>

<span data-ttu-id="1a832-p101">테 넌 트에 있는 각 지리적 위치에 대 한 별도 관리자를 구성할 수 있습니다. 이러한 관리자에는 해당 지리적 위치에만 적용 되는 SharePoint Online 및 OneDrive 설정에 액세스할을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a832-p101">You can configure separate administrators for each geo location that you have in your tenant. These administrators will have access to the SharePoint Online and OneDrive settings that are specific to their geo-location.</span></span>

<span data-ttu-id="1a832-p102">용어 저장소-등의 일부 서비스-중앙 위치에서 관리 되며 위성 위치에 복제 됩니다. 중앙 위치에 대 한 지리적으로 분산 관리는 위성 위치에 대 한 지리적으로 분산 admins 하지 하는 반면, 여기에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a832-p102">Some services - such as the term store - are administered from the central location and replicated to satellite locations. The geo admin for the central location has access to these, whereas geo admins for satellite locations don’t.</span></span>

<span data-ttu-id="1a832-108">전역 관리자 및 SharePoint Online 관리자가 모든 지리적 위치에 있는 설정에 대 한 액세스를 계속 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a832-108">Global administrators and SharePoint Online administrators continue to have access to settings in all geo locations.</span></span>

## <a name="configuring-geo-administrators"></a><span data-ttu-id="1a832-109">지리적으로 분산 관리자 구성</span><span class="sxs-lookup"><span data-stu-id="1a832-109">Configuring geo administrators</span></span>

<span data-ttu-id="1a832-110">지리적으로 분산 관리자를 구성 하려면 SharePoint Online PowerShell 모듈이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a832-110">Configuring geo admins requires SharePoint Online PowerShell module.</span></span>

<span data-ttu-id="1a832-111">[Connect-sposervice](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) 를 사용 하 여 지리적으로 분산 관리자를 추가 하려는 지리적으로 분산 위치의 관리 센터에 연결 하려면 (예: Connect-sposervicehttps://ContosoEUR-admin.sharepoint.com.)</span><span class="sxs-lookup"><span data-stu-id="1a832-111">Use [Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) to connect to the admin center of the geo location where you want to add the geo admin. (For example, Connect-SPOService  https://ContosoEUR-admin.sharepoint.com.)</span></span>

<span data-ttu-id="1a832-112">지리적으로 분산 관리 권한으로 사용자를 추가, 실행`Add-SPOGeoAdministrator -UserPrincipalName <UPN>`</span><span class="sxs-lookup"><span data-stu-id="1a832-112">To add a user as a geo admin, run `Add-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

<span data-ttu-id="1a832-113">실행 하는 기존 지리적으로 분산 admins의 위치를 보려면`Get-SPOGeoAdministrators`</span><span class="sxs-lookup"><span data-stu-id="1a832-113">To view the existing geo admins of a location, run `Get-SPOGeoAdministrators`</span></span>

<span data-ttu-id="1a832-114">사용자의 위치를 지리적으로 분산 관리자를 제거 하려면 다음을 실행합니다`Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`</span><span class="sxs-lookup"><span data-stu-id="1a832-114">To remove a user as a Geo Admin of a location, run  `Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

## <a name="see-also"></a><span data-ttu-id="1a832-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1a832-115">See Also</span></span>

[<span data-ttu-id="1a832-116">추가 SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="1a832-116">Add-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/add-spogeoadministrator)

[<span data-ttu-id="1a832-117">Get-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="1a832-117">Get-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spogeoadministrator)

[<span data-ttu-id="1a832-118">SPOGeoAdministrator 제거</span><span class="sxs-lookup"><span data-stu-id="1a832-118">Remove-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/remove-spogeoadministrator)