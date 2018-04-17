---
title: Multi-Geo Capabilities in OneDrive and SharePoint Online in Office 365
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/16/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: Strat_SP_gtc
localization_priority: Normal
ms.assetid: 094e86f2-9ff0-40ac-af31-28fcaba00c1d
description: Expand your Office 365 presence to multiple geographic regions with multi-geo capabilities in OneDrive and SharePoint Online.
ms.openlocfilehash: 3f72158fe05aadfe8a08a5520bf65cd2d0aaa1c6
ms.sourcegitcommit: a81d08c7e8771cb2c232435971e3169d4f7428dc
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
---
# <a name="multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365"></a><span data-ttu-id="d100a-103">Multi-Geo Capabilities in OneDrive and SharePoint Online in Office 365</span><span class="sxs-lookup"><span data-stu-id="d100a-103">Multi-Geo Capabilities in OneDrive and SharePoint Online in Office 365</span></span>

<span data-ttu-id="d100a-p101">With multi-geo capabilities in OneDrive and SharePoint Online, your organization can expand its Office 365 presence to multiple geographic regions and/or countries within your existing tenant. Reach out to your Microsoft Account Team to sign up your Multi-National Company for OneDrive for Business Multi-Geo.</span><span class="sxs-lookup"><span data-stu-id="d100a-p101">With multi-geo capabilities in OneDrive and SharePoint Online, your organization can expand its Office 365 presence to multiple geographic regions and/or countries within your existing tenant. Reach out to your Microsoft Account Team to sign up your Multi-National Company for OneDrive for Business Multi-Geo.</span></span>
  
<span data-ttu-id="d100a-106">With OneDrive Multi-Geo, you can provision and store data at rest in the geo locations that you've chosen to meet data residency requirements, and at the same time unlock your global roll out of modern productivity experiences to your workforce.</span><span class="sxs-lookup"><span data-stu-id="d100a-106">With OneDrive Multi-Geo, you can provision and store data at rest in the geo locations that you've chosen to meet data residency requirements, and at the same time unlock your global roll out of modern productivity experiences to your workforce.</span></span>
  
<span data-ttu-id="d100a-107">Here's how multi-geo features can benefit your organization:</span><span class="sxs-lookup"><span data-stu-id="d100a-107">Here's how multi-geo features can benefit your organization:</span></span>
  
- <span data-ttu-id="d100a-108">Operate as one global connected organization with a single Office 365 tenant spanning multiple geo locations.</span><span class="sxs-lookup"><span data-stu-id="d100a-108">Operate as one global connected organization with a single Office 365 tenant spanning multiple geo locations.</span></span>
    
- <span data-ttu-id="d100a-109">Meet data residency requirements by creating and hosting data-at-rest within a specified geo location.</span><span class="sxs-lookup"><span data-stu-id="d100a-109">Meet data residency requirements by creating and hosting data-at-rest within a specified geo location.</span></span>
    
- <span data-ttu-id="d100a-110">Empower your satellite users with the same modern productivity experiences enjoyed by your central location users.</span><span class="sxs-lookup"><span data-stu-id="d100a-110">Empower your satellite users with the same modern productivity experiences enjoyed by your central location users.</span></span>
    
- <span data-ttu-id="d100a-111">Enable your users to move across geo locations as their role changes, while access to their content is kept intact.</span><span class="sxs-lookup"><span data-stu-id="d100a-111">Enable your users to move across geo locations as their role changes, while access to their content is kept intact.</span></span>
    
- <span data-ttu-id="d100a-112">Tailor your sharing policies per geo location and data loss prevention policies per site.</span><span class="sxs-lookup"><span data-stu-id="d100a-112">Tailor your sharing policies per geo location and data loss prevention policies per site.</span></span>
    
- <span data-ttu-id="d100a-113">Designate eDiscovery managers per geo location and allow governing cases tailored to your geo location.</span><span class="sxs-lookup"><span data-stu-id="d100a-113">Designate eDiscovery managers per geo location and allow governing cases tailored to your geo location.</span></span>
    
- <span data-ttu-id="d100a-114">Choose unique URL namespaces (for example, ContosoEUR.sharepoint.com) for your additional geo locations.</span><span class="sxs-lookup"><span data-stu-id="d100a-114">Choose unique URL namespaces (for example, ContosoEUR.sharepoint.com) for your additional geo locations.</span></span>
    
- <span data-ttu-id="d100a-115">Consolidate your regional on-premises data into your Office 365 multi-geo tenant.</span><span class="sxs-lookup"><span data-stu-id="d100a-115">Consolidate your regional on-premises data into your Office 365 multi-geo tenant.</span></span>
    
<span data-ttu-id="d100a-p102">In a multi-geo configuration, your Office 365 tenant consists of a central location (also known as the default location) and one or more satellite geo locations. The key concept of multi-geo is that a single tenancy will span across one multiple geo locations. In a multi-geo tenant, the information about geo locations, groups, and user information, is mastered in Azure Active Directory (AAD). Because your tenant information is mastered centrally and synchronized into each geo location, sharing and experiences involving anyone from your company contain global awareness.</span><span class="sxs-lookup"><span data-stu-id="d100a-p102">In a multi-geo configuration, your Office 365 tenant consists of a central location (also known as the default location) and one or more satellite geo locations. The key concept of multi-geo is that a single tenancy will span across one multiple geo locations. In a multi-geo tenant, the information about geo locations, groups, and user information, is mastered in Azure Active Directory (AAD). Because your tenant information is mastered centrally and synchronized into each geo location, sharing and experiences involving anyone from your company contain global awareness.</span></span>
  
## <a name="sample-multi-geo-tenant-configuration"></a><span data-ttu-id="d100a-120">Sample multi-geo tenant configuration</span><span class="sxs-lookup"><span data-stu-id="d100a-120">Sample multi-geo tenant configuration</span></span>

<span data-ttu-id="d100a-121">By using a multi-geo tenant, Contoso, with a central location of North America, can expand to satellite geo locations in Europe, and Australia under the single organization umbrella of Contoso.com. Users with their preferred data location set to Europe will have their OneDrive in Europe while users with their preferred data location in North America will have their OneDrive in the US.</span><span class="sxs-lookup"><span data-stu-id="d100a-121">By using a multi-geo tenant, Contoso, with a central location of North America, can expand to satellite geo locations in Europe, and Australia under the single organization umbrella of Contoso.com. Users with their preferred data location set to Europe will have their OneDrive in Europe while users with their preferred data location in North America will have their OneDrive in the US.</span></span>
  
![Map of the world, showing geo locations for Contoso and other available geo locations](images/df317ccc-2e53-411d-9211-a5aee63ca1e5.png)
  
## <a name="get-multi-geo-features-in-three-simple-steps"></a><span data-ttu-id="d100a-123">Get multi-geo features in three simple steps</span><span class="sxs-lookup"><span data-stu-id="d100a-123">Get multi-geo features in three simple steps</span></span>

<span data-ttu-id="d100a-124">Configuring multi-geo is easy:</span><span class="sxs-lookup"><span data-stu-id="d100a-124">Configuring multi-geo is easy:</span></span>
  
1. <span data-ttu-id="d100a-p103">Work with your account team to add the _Multi-Geo Capabilities in Office 365_ service plan. They will guide you to add the number of licenses needed.</span><span class="sxs-lookup"><span data-stu-id="d100a-p103">Work with your account team to add the _Multi-Geo Capabilities in Office 365_ service plan. They will guide you to add the number of licenses needed.</span></span>
    
2. <span data-ttu-id="d100a-127">Add your satellite locations.</span><span class="sxs-lookup"><span data-stu-id="d100a-127">Add your satellite locations.</span></span>
    
3. <span data-ttu-id="d100a-128">Configure your user accounts for the appropriate location.</span><span class="sxs-lookup"><span data-stu-id="d100a-128">Configure your user accounts for the appropriate location.</span></span>
    
## <a name="multi-geo-status-and-availability"></a><span data-ttu-id="d100a-129">Multi-Geo status and availability</span><span class="sxs-lookup"><span data-stu-id="d100a-129">Multi-Geo status and availability</span></span>

<span data-ttu-id="d100a-130">OneDrive Multi-Geo is currently offered in these regions and countries:</span><span class="sxs-lookup"><span data-stu-id="d100a-130">OneDrive Multi-Geo is currently offered in these regions and countries:</span></span>
  
- <span data-ttu-id="d100a-131">Asia-Pacific</span><span class="sxs-lookup"><span data-stu-id="d100a-131">Asia-Pacific</span></span>
    
- <span data-ttu-id="d100a-132">오스트레일리아</span><span class="sxs-lookup"><span data-stu-id="d100a-132">Australia</span></span>
    
- <span data-ttu-id="d100a-133">캐나다</span><span class="sxs-lookup"><span data-stu-id="d100a-133">Canada</span></span>
    
- <span data-ttu-id="d100a-134">European Union (EMEA)</span><span class="sxs-lookup"><span data-stu-id="d100a-134">European Union (EMEA)</span></span>
    
- <span data-ttu-id="d100a-135">일본</span><span class="sxs-lookup"><span data-stu-id="d100a-135">Japan</span></span>
    
- <span data-ttu-id="d100a-136">영국</span><span class="sxs-lookup"><span data-stu-id="d100a-136">United Kingdom</span></span>
    
- <span data-ttu-id="d100a-137">United States (North America)</span><span class="sxs-lookup"><span data-stu-id="d100a-137">United States (North America)</span></span>
    
- <span data-ttu-id="d100a-138">한국</span><span class="sxs-lookup"><span data-stu-id="d100a-138">Korea</span></span>
      
<span data-ttu-id="d100a-139">Upcoming geo locations:</span><span class="sxs-lookup"><span data-stu-id="d100a-139">Upcoming geo locations:</span></span>
  
- <span data-ttu-id="d100a-140">프랑스</span><span class="sxs-lookup"><span data-stu-id="d100a-140">France</span></span>
- <span data-ttu-id="d100a-141">인도</span><span class="sxs-lookup"><span data-stu-id="d100a-141">India</span></span>
    
## <a name="getting-started"></a><span data-ttu-id="d100a-142">시작</span><span class="sxs-lookup"><span data-stu-id="d100a-142">Getting started</span></span>

<span data-ttu-id="d100a-p104">To get started with OneDrive for Business Multi-Geo, the first step is to [plan your OneDrive for Business Multi-Geo environment](plan-for-multi-geo.md). Next, [learn about administering a multi-geo environment](administering-a-multi-geo-environment.md) and [how your users will experience a multi-geo environment](multi-geo-user-experience.md). When you are ready to set up OneDrive for Business Multi-Geo, [configure your tenant for multi-geo](multi-geo-tenant-configuration.md), then [move any existing OneDrive sites to thier new geo-locations](move-onedrive-between-geo-locations.md) and [set up search](configure-search-for-multi-geo.md).</span><span class="sxs-lookup"><span data-stu-id="d100a-p104">To get started with OneDrive for Business Multi-Geo, the first step is to [plan your OneDrive for Business Multi-Geo environment](plan-for-multi-geo.md). Next, [learn about administering a multi-geo environment](administering-a-multi-geo-environment.md) and [how your users will experience a multi-geo environment](multi-geo-user-experience.md). When you are ready to set up OneDrive for Business Multi-Geo, [configure your tenant for multi-geo](multi-geo-tenant-configuration.md), then [move any existing OneDrive sites to thier new geo-locations](move-onedrive-between-geo-locations.md) and [set up search](configure-search-for-multi-geo.md).</span></span>
