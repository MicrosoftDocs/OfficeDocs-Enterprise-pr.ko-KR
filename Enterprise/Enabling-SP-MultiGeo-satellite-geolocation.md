---
title: 위성 지리적 위치에서 SharePoint Multi-Geo 사용
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: ''
ms.collection:
- Strat_SP_gtc
- SPO_Content
localization_priority: Priority
description: 위성 지리적 위치에서 SharePoint Multi-Geo 사용
ms.openlocfilehash: e920aae90326e9635204675d6872340f7808143c
ms.sourcegitcommit: 265cc03b600e9015a44c60c3f8bb9075b1c20888
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2020
ms.locfileid: "41973950"
---
# <a name="enabling-sharepoint-multi-geo-in-your-satellite-geo-location"></a><span data-ttu-id="38bc7-103">위성 지리적 위치에서 SharePoint Multi-Geo 사용</span><span class="sxs-lookup"><span data-stu-id="38bc7-103">Enabling SharePoint Multi-Geo in your satellite geo location</span></span>

<span data-ttu-id="38bc7-104">이 문서는 SharePoint Multi-Geo Capabilities가 2019년 3월 27일에 출시되기 **전**에 Multi-Geo 위성 위치를 만들고, 해당 위성 지리적 위치에서 SharePoint Multi-Geo를 사용하도록 설정하지 않은 전역 또는 SharePoint 관리자를 위해 작성되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38bc7-104">This article is for Global or SharePoint administrators who have created a Multi-Geo satellite location **before** SharePoint Multi-Geo capabilities became generally available on March 27, 2019, and who have not enabled SharePoint Multi-Geo in their satellite geo location(s).</span></span> 

>[!Note]
><span data-ttu-id="38bc7-105">**3월 27일** 이후에 새 지리적 위치를 추가한 경우, 새 지리적 위치가 이미 OneDrive 및 SharePoint Multi-Geo용으로 사용하도록 설정되어 있으므로 이 지침을 따라 작업을 수행할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="38bc7-105">If you have added a new geo location **after March 27th**, you do not need to perform these instructions, as your new geo location will already be enabled for OneDrive and SharePoint Multi-Geo.</span></span>

<span data-ttu-id="38bc7-106">이 지침을 따라 작업을 수행하면 위성 위치에서 SharePoint를 사용하도록 설정하여 Multi-Geo 위성 사용자가 O365에서 OneDrive와 SharePoint Multi-Geo Capabilities 모두를 활용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38bc7-106">These instructions will allow you to enable SharePoint in your satellite location, so your Multi-Geo satellite users can take advantage of both OneDrive and SharePoint Multi-Geo capabilities in O365.</span></span> 

>[!IMPORTANT]
><span data-ttu-id="38bc7-107">이 방법은 한 방향 설정만 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="38bc7-107">Please note that this is a one way enablement.</span></span> <span data-ttu-id="38bc7-108">SPO 모드를 설정하면 지원이 포함된 권한 상승 없이 테넌트를 OneDrive 전용 Multi-Geo 모드로 되돌릴 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="38bc7-108">Once you set SPO mode, you will not be able to revert your tenant to OneDrive only Multi-Geo mode without an escalation with support.</span></span> 

## <a name="to-set-a-geo-location-into-spo-mode"></a><span data-ttu-id="38bc7-109">지리적 위치를 SPO 모드로 설정</span><span class="sxs-lookup"><span data-stu-id="38bc7-109">To set a geo location into SPO Mode</span></span>

<span data-ttu-id="38bc7-110">지리적 위치를 SPO 모드로 설정하려면 SPO 모드에서 설정하려는 지리적 위치에 연결하세요.</span><span class="sxs-lookup"><span data-stu-id="38bc7-110">To set a geo location into SPO mode, connect to the geo location you want to set in SPO Mode:</span></span>

1.  <span data-ttu-id="38bc7-111">SharePoint Online 관리 셸을 여세요.</span><span class="sxs-lookup"><span data-stu-id="38bc7-111">Open your SharePoint Online Management Shell</span></span> 
2.  <span data-ttu-id="38bc7-112">Connect-SPOService -URL "https://$tenantGeo-admin.sharepoint.com" -Credential $credential</span><span class="sxs-lookup"><span data-stu-id="38bc7-112">Connect-SPOService -URL "https://$tenantGeo-admin.sharepoint.com" -Credential $credential</span></span>
3.  <span data-ttu-id="38bc7-113">Set-SPOMultiGeoExperience</span><span class="sxs-lookup"><span data-stu-id="38bc7-113">Set-SPOMultiGeoExperience</span></span></br></br>
<span data-ttu-id="38bc7-114">![Set-SPOMultiGeoExperience](media/Set-SPO-MultiGeo.jpg)</span><span class="sxs-lookup"><span data-stu-id="38bc7-114">![Set-SPOMultiGeoExperience](media/Set-SPO-MultiGeo.jpg)</span></span>
4.  <span data-ttu-id="38bc7-115">서비스에서 다양한 게시 작업을 수행하고 테넌트를 다시 표시하는 동안 이 작업은 보통 1시간 정도 걸립니다.</span><span class="sxs-lookup"><span data-stu-id="38bc7-115">This operation usually takes about an hour while we perform various publish backs in the service and re-stamp your tenant.</span></span> <span data-ttu-id="38bc7-116">최소 1시간이 지나면 Get-SPOMultiGeoExperience를 수행해 주세요.</span><span class="sxs-lookup"><span data-stu-id="38bc7-116">After at least 1 hour, please perform a Get-SPOMultiGeoExperience.</span></span>  <span data-ttu-id="38bc7-117">이 작업을 수행하면 지리적 위치가 SPO 모드에 설정되었는지 여부가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="38bc7-117">This will show you whether this geo location is in SPO mode.</span></span></br></br>
<span data-ttu-id="38bc7-118">![Set-SPOMultiGeoExperience](media/Get-SPO-MultiGeo.jpg)</span><span class="sxs-lookup"><span data-stu-id="38bc7-118">![Set-SPOMultiGeoExperience](media/Get-SPO-MultiGeo.jpg)</span></span>

 
 
 
>[!Note]
><span data-ttu-id="38bc7-119">서비스의 특정 캐시를 24시간 마다 업데이트하면 최대 24시간의 기간 동안 위성 지리적 위치가 계속 ODB 모드에 있는 것처럼 간헐적으로 작동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38bc7-119">Certain caches in the service update every 24 hours, so it is possible that for a period of up to 24 hours, your satellite geo may intermittently behave as if it was still in ODB mode.</span></span> <span data-ttu-id="38bc7-120">이 작업으로 인해 기술 문제가 발생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="38bc7-120">This does not cause any technical issues.</span></span> 
 
<span data-ttu-id="38bc7-121">SharePoint Multi-Geo에 관해 더 많은 정보를 확인하려면 [aka.ms/sharepointmultigeo](https://docs.microsoft.com/office365/enterprise/multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="38bc7-121">For additional information regarding SharePoint Multi-Geo, please refer to [aka.ms/sharepointmultigeo](https://docs.microsoft.com/office365/enterprise/multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365)</span></span>


