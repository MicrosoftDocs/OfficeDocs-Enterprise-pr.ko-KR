---
title: OneDrive 및 SharePoint Online의 Multi-Geo 기능
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
ms.assetid: 094e86f2-9ff0-40ac-af31-28fcaba00c1d
description: OneDrive Online의 Multi-Geo 기능으로 여러 지리적 지역으로 Office 365 범위를 확장합니다.
ms.openlocfilehash: 99c265da9c3ace0c2c415289b8db52f97d51b985
ms.sourcegitcommit: 74b6d9fc3ce0873e8564fc4de51fe3afeb122447
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "37046079"
---
# <a name="multi-geo-capabilities-in-onedrive-and-sharepoint-online"></a><span data-ttu-id="da7cc-103">OneDrive 및 SharePoint Online의 Multi-Geo 기능</span><span class="sxs-lookup"><span data-stu-id="da7cc-103">Multi-Geo Capabilities in OneDrive and SharePoint Online</span></span>

<span data-ttu-id="da7cc-104">OneDrive 및 SharePoint Online의 Multi-Geo 기능을 사용하여 SharePoint 팀 사이트 및 Office 365 그룹 사서함이 저장되는 국가 또는 지역 제어가 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="da7cc-104">Multi-Geo capabilities in OneDrive and SharePoint Online enables control of the country or region where shared resources like SharePoint team sites and Office 365 Group mailboxes are stored at rest.</span></span>

<span data-ttu-id="da7cc-105">각 사용자, 그룹 사서함 및 SharePoint 사이트에는 관련 데이터가 저장되는 지리적 위치를 나타내는 기본 설정 데이터 위치(PDL)가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da7cc-105">Each user, Group mailbox, and SharePoint site has a Preferred Data Location (PDL) which denotes the geo location where related data is to be stored.</span></span> <span data-ttu-id="da7cc-106">사용자의 개인 데이터(Exchange 사서함 및 OneDrive)는 물론 생성한 Office 365 그룹 또는 SharePoint 사이트가 데이터 상주 요건 충족을 위해 특정 지리적 위치에 저장될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da7cc-106">Users' personal data (Exchange mailbox and OneDrive) along with any Office 365 Groups or SharePoint sites that they create can be stored in the specified geo location to meet data residency requirements.</span></span> <span data-ttu-id="da7cc-107">[각 지리적 위치에 대해 다른 관리자를 지정](add-a-sharepoint-geo-admin.md)할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da7cc-107">You can [specify different administrators for each geo location](add-a-sharepoint-geo-admin.md).</span></span>

<span data-ttu-id="da7cc-108">사용자는 Office 응용 프로그램, OneDrive 및 검색을 포함한 Office 365 서비스를 사용할 때 원활한 환경을 이용합니다.</span><span class="sxs-lookup"><span data-stu-id="da7cc-108">Users get a seamless experience when using Office 365 services, including Office applications, OneDrive, and Search.</span></span> <span data-ttu-id="da7cc-109">자세한 내용은 [Multi-Geo 환경의 사용자 작업 환경](multi-geo-user-experience.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="da7cc-109">See [User experience in a multi-geo environment](multi-geo-user-experience.md) for details.</span></span>

## <a name="onedrive"></a><span data-ttu-id="da7cc-110">OneDrive</span><span class="sxs-lookup"><span data-stu-id="da7cc-110">OneDrive</span></span>

<span data-ttu-id="da7cc-111">각 사용자의 OneDrive는 사용자의 PDL에 따라 위성 위치로 프로비저닝 또는 [관리자 이동](move-onedrive-between-geo-locations.md)이 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="da7cc-111">Each user's OneDrive can be provisioned in or [moved by an administrator](move-onedrive-between-geo-locations.md) to a satellite location in accordance with the user's PDL.</span></span> <span data-ttu-id="da7cc-112">개인 파일은 해당 지리적 위치에 보관됩니다. 단, 다른 지리적 위치의 사용자와 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da7cc-112">Personal files are then kept in that geo location, though they can be shared with users in other geo locations.</span></span>

## <a name="sharepoint-sites-and-groups"></a><span data-ttu-id="da7cc-113">SharePoint 사이트 및 그룹</span><span class="sxs-lookup"><span data-stu-id="da7cc-113">SharePoint Sites and Groups</span></span>

<span data-ttu-id="da7cc-114">SharePoint Online 관리 센터에서 Multi-Geo 기능 관리를 이용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da7cc-114">Management of the Multi-Geo feature is available through the SharePoint admin center.</span></span> <span data-ttu-id="da7cc-115">자세한 내용은 [해당 블로그 게시물](https://techcommunity.microsoft.com/t5/Office-365-Blog/Now-available-Multi-Geo-in-SharePoint-and-Office-365-Groups/ba-p/263302)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="da7cc-115">Detailed information can be found in the [corresponding blog post](https://techcommunity.microsoft.com/t5/Office-365-Blog/Now-available-Multi-Geo-in-SharePoint-and-Office-365-Groups/ba-p/263302).</span></span>

<span data-ttu-id="da7cc-116">사용자가 다중 지역 환경에서 SharePoint 그룹 연결 사이트를 생성할 때 사용자의 PDL은 사이트 및 관련 그룹 사서함이 생성되는 지리적 위치를 결정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="da7cc-116">When a user creates a SharePoint group-connected site, their PDL is used to determine the geo location where the site and its associated Group mailbox is created.</span></span> <span data-ttu-id="da7cc-117">(사용자의 PDL 값이 설정되지 않았거나 위성 위치로 구성되지 않은 지리적 위치로 설정된 경우 사이트 및 사서함은 중앙 위치에 생성됩니다.)</span><span class="sxs-lookup"><span data-stu-id="da7cc-117">(If the user's PDL value hasn't been set, or has been set to geo location that hasn't been configured as a satellite location, then the site and mailbox are created in the central location.)</span></span>

<span data-ttu-id="da7cc-118">Exchange, OneDrive 및 SharePoint를 제외한 Office 365 서비스는 Multi-Geo가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="da7cc-118">Office 365 services other than Exchange, OneDrive, and SharePoint are not Multi-Geo.</span></span> <span data-ttu-id="da7cc-119">하지만 이러한 서비스에 의해 생성된 Office 365 그룹은 생성자의 PDL 스탬프가 지정되고, Exchange 그룹 사서함 및 SharePoint O365 그룹 사이트는 해당 지리적 위치에 프로비저닝됩니다.</span><span class="sxs-lookup"><span data-stu-id="da7cc-119">However, Office 365 Groups that are created by these services will be stamped with the PDL of the creator and their Exchange Group mailbox and SharePoint O365 Group Site provisioned in the corresponding geo.</span></span> 

## <a name="managing-the-multi-geo-environment"></a><span data-ttu-id="da7cc-120">다중 지역 환경 관리</span><span class="sxs-lookup"><span data-stu-id="da7cc-120">Managing the multi-geo environment</span></span>

<span data-ttu-id="da7cc-121">다중 지역 환경 설정 및 관리는 SharePoint 관리 센터를 통해 이루어집니다.</span><span class="sxs-lookup"><span data-stu-id="da7cc-121">Setting up and managing your multi-geo environment is done through the SharePoint admin center.</span></span> 

![SharePoint 관리 센터의 지리적 위치 페이지 스크린샷](media/sharepoint-multi-geo-admin-center.png)

<span data-ttu-id="da7cc-123">(SharePoint 사이트 또는 OneDrive 사이트 이동과 같은 일부 작업은 Microsoft PowerShell을 필요로 합니다.)</span><span class="sxs-lookup"><span data-stu-id="da7cc-123">(Some actions, such as moving a SharePoint site or a OneDrive site require Microsoft PowerShell.)</span></span>

## <a name="see-also"></a><span data-ttu-id="da7cc-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="da7cc-124">See also</span></span>

[<span data-ttu-id="da7cc-125">SharePoint 및 Office 365 그룹의 Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="da7cc-125">Multi-Geo in SharePoint and Office 365 Groups</span></span>](https://techcommunity.microsoft.com/t5/Office-365-Blog/Now-available-Multi-Geo-in-SharePoint-and-Office-365-Groups/ba-p/263302)

[<span data-ttu-id="da7cc-126">다중 지역 환경 관리</span><span class="sxs-lookup"><span data-stu-id="da7cc-126">Administering a multi-geo environment</span></span>](administering-a-multi-geo-environment.md)

[<span data-ttu-id="da7cc-127">다중 지역 환경에서 SharePoint 저장소 할당량</span><span class="sxs-lookup"><span data-stu-id="da7cc-127">SharePoint storage quotas in multi-geo environments</span></span>](sharepoint-multi-geo-storage-quota.md)

[<span data-ttu-id="da7cc-128">Multi-Geo 환경에서 Exchange Online 사서함 관리</span><span class="sxs-lookup"><span data-stu-id="da7cc-128">Administering Exchange Online mailboxes in a multi-geo environment</span></span>](administering-exchange-online-multi-geo.md)
