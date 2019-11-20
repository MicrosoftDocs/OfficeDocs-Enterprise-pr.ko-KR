---
title: SharePoint Server 2007 지원 로드맵 최종본
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 01/28/2019
audience: ITPro
ms.topic: conceptual
f1_keywords:
- vsemail
- MS_WSS_DirectoryManagement
- MS_WSS_ConfigEmail
- globalemailconfig
- configssc
- AppDefToBDC
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
search.appverid:
- MET150
- OFU120
- SPS150
- OSU140
- WSU120
- OSR120
- SPO160
- PJW120
- SPB160
- OSI150
- OSI160
- BSA160
- OSU160
ms.assetid: ba124775-d5c0-4d68-b88d-8458ad4c3717
description: 2017 년 10 월 10 일에 SharePoint Server 2007에 대 한 지원이 종료 되었습니다. 이 문서를 읽으면 업그레이드 옵션, 문제 해결, 모범 사례, 시스템 요구 사항, 업그레이드 단계 및 Microsoft 파트너 로부터 도움을 받는 방법에 대해 알아볼 수 있습니다.
ms.openlocfilehash: 1b7b2ccf1bbda5210e563a4cd702ebd90b9f8f5d
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2019
ms.locfileid: "38747317"
---
# <a name="sharepoint-server-2007-end-of-support-roadmap"></a><span data-ttu-id="7a749-104">SharePoint Server 2007 지원 로드맵 최종본</span><span class="sxs-lookup"><span data-stu-id="7a749-104">SharePoint Server 2007 end of support roadmap</span></span>

<span data-ttu-id="7a749-105">*이 문서는 Office 365 Enterprise 및 Microsoft 365 Enterprise에 모두 적용 됩니다.*</span><span class="sxs-lookup"><span data-stu-id="7a749-105">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="7a749-106">**2017 년 10 월 10 일**, Microsoft Office SharePoint Server 2007 지원 종료에 도달 했습니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-106">On **October 10, 2017**, Microsoft Office SharePoint Server 2007 reached end of support.</span></span> <span data-ttu-id="7a749-107">SharePoint Server 2007에서 Office 365 또는 최신 버전의 SharePoint Server 온-프레미스로 마이그레이션을 시작한 적이 없다면 이제 계획을 시작 하는 데 걸리는 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-107">If you haven't begun your migration from SharePoint Server 2007 to Office 365 or a newer version of SharePoint Server on-premises, now's the time to start planning.</span></span> <span data-ttu-id="7a749-108">이 문서에서는 사용자가 데이터를 SharePoint Online으로 마이그레이션하거나 SharePoint Server를 온-프레미스로 업그레이드 하는 데 도움이 되는 리소스에 대해 자세히 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-108">This article details resources to help people migrate data to SharePoint Online, or upgrade your SharePoint Server on-premises.</span></span> 
  
## <a name="what-does-end-of-support-mean"></a><span data-ttu-id="7a749-109">지원이 끝나는 것은 무엇을 의미 하나요?</span><span class="sxs-lookup"><span data-stu-id="7a749-109">What does end of support mean?</span></span>

<span data-ttu-id="7a749-110">SharePoint Server에는 거의 모든 Microsoft 제품과 마찬가지로 Microsoft가 새로운 기능, 버그 수정, 보안 픽스 등을 제공 하는 지원 수명 주기가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-110">SharePoint Server, like almost all Microsoft products, has a support lifecycle during which Microsoft provides new features, bug fixes, security fixes, and so on.</span></span> <span data-ttu-id="7a749-111">일반적으로이 수명 주기는 제품 초기 릴리스 날짜 로부터 10 년 동안 지속 되며이 주기의 끝은 제품의 지원 종료 라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-111">This lifecycle typically lasts for 10 years from the date of the product's initial release, and the end of this lifecycle is known as the product's end of support.</span></span> <span data-ttu-id="7a749-112">지원 종료 시 Microsoft는 더 이상 다음을 제공 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-112">At end of support, Microsoft no longer provides:</span></span>
  
- <span data-ttu-id="7a749-113">발생할 수 있는 문제에 대 한 기술 지원</span><span class="sxs-lookup"><span data-stu-id="7a749-113">Technical support for problems that may occur;</span></span>
    
- <span data-ttu-id="7a749-114">검색 된 문제와 서버의 안정성 및 유용성에 영향을 줄 수 있는 문제에 대 한 버그 수정</span><span class="sxs-lookup"><span data-stu-id="7a749-114">Bug fixes for issues that are discovered and that may impact the stability and usability of the server;</span></span>
    
- <span data-ttu-id="7a749-115">검색 되 고 서버에서 보안 위반에 취약 해질 수 있는 취약성에 대 한 보안 수정 사항 한</span><span class="sxs-lookup"><span data-stu-id="7a749-115">Security fixes for vulnerabilities that are discovered and that may make the server vulnerable to security breaches; and</span></span> 
    
- <span data-ttu-id="7a749-116">표준 시간대 업데이트</span><span class="sxs-lookup"><span data-stu-id="7a749-116">Time zone updates.</span></span>
    
<span data-ttu-id="7a749-117">사용자는 SharePoint Server 2007 팜이 여전히 작업을 수행 하 고 2017이 지난 후에도 더 이상 업데이트, 패치 또는 픽스를 제공 하지 않으며, Microsoft Support는 해당 제품에 대 한 지원 노력을 보다 최신 버전의 제품으로 완전히 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-117">Though your SharePoint Server 2007 farm will still be operational after October 10, 2017, no further updates, patches, or fixes will be shipped for the product (including security patches/fixes), and Microsoft Support will have fully shifted its support efforts to more recent versions of the product.</span></span> <span data-ttu-id="7a749-118">설치가 더 이상 지원 되거나 패치 되지 않으므로 지원 되는 방법의 끝으로 제품을 업그레이드 하거나 중요 한 데이터를 마이그레이션해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-118">Because your installation will no longer supported or patched, as end of support approaches you should upgrade the product, or migrate important data.</span></span>
  
> [!TIP]
> <span data-ttu-id="7a749-119">업그레이드 또는 마이그레이션을 아직 계획 하지 않은 경우에는 [SharePoint 2007 마이그레이션 옵션을 고려 하](sharepoint-2007-migration-options.md)여 시작 위치에 대 한 몇 가지 예를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7a749-119">If you haven't already planned for upgrade or migration, please see: [SharePoint 2007 migration options to consider](sharepoint-2007-migration-options.md), for some examples of where to begin.</span></span> <span data-ttu-id="7a749-120">또한 업그레이드 또는 Office 365 마이그레이션 (또는 둘 다)을 통해 도움을 받을 수 있는 [Microsoft 파트너](https://go.microsoft.com/fwlink/?linkid=841249) 를 검색할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-120">You can also search for [Microsoft Partners](https://go.microsoft.com/fwlink/?linkid=841249) who can help with upgrade or Office 365 migration (or both).</span></span> 
  
<span data-ttu-id="7a749-121">지원 종료에 도달 하는 Office 2007 서버에 대 한 자세한 내용은 [office 2007 서버 및 클라이언트에서 업그레이드 하는 데 도움이 되는 리소스를](upgrade-from-office-2007-servers-and-products.md)참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="7a749-121">For more information about Office 2007 servers reaching the end of support, see [Resources to help you upgrade from Office 2007 servers and clients](upgrade-from-office-2007-servers-and-products.md).</span></span>
  
## <a name="what-are-my-options"></a><span data-ttu-id="7a749-122">내 옵션 이란?</span><span class="sxs-lookup"><span data-stu-id="7a749-122">What are my options?</span></span>

<span data-ttu-id="7a749-123">첫 번째 중지는 [제품 수명 주기 사이트](https://go.microsoft.com/fwlink/?linkid=843148)여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-123">Your first stop should be the [Product Lifecycle site](https://go.microsoft.com/fwlink/?linkid=843148).</span></span> <span data-ttu-id="7a749-124">기한에 해당 하는 온-프레미스 Microsoft 제품을 사용 하는 경우에는 마이그레이션에 필요한 최신 날짜를 확인 하 여 업그레이드 또는 마이그레이션을 예약할 수 있도록, 1 년 이상 동안 마이그레이션을 수행 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-124">If you have an on-premises Microsoft product that is aging, you should check for its end of support date so that, a year or so out - or as long as your migrations generally require - you can schedule upgrade or migrations.</span></span> <span data-ttu-id="7a749-125">다음 단계를 선택 하는 경우 제품 기능에 대 한 적절 하 고 개선 되 고 유용한 것으로 생각 하는 데 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-125">When choosing the next step, it might help to think in terms of what would be good enough, better, and best when it comes to product features.</span></span> <span data-ttu-id="7a749-126">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-126">Here's an example:</span></span>
  
|<span data-ttu-id="7a749-127">**좋습니다**</span><span class="sxs-lookup"><span data-stu-id="7a749-127">**Good**</span></span>|<span data-ttu-id="7a749-128">**바람직합니다**</span><span class="sxs-lookup"><span data-stu-id="7a749-128">**Better**</span></span>|<span data-ttu-id="7a749-129">**방법은**</span><span class="sxs-lookup"><span data-stu-id="7a749-129">**Best**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="7a749-130">SharePoint Server 2010</span><span class="sxs-lookup"><span data-stu-id="7a749-130">SharePoint Server 2010</span></span>  <br/> |<span data-ttu-id="7a749-131">SharePoint Server 2013</span><span class="sxs-lookup"><span data-stu-id="7a749-131">SharePoint Server 2013</span></span>  <br/> |<span data-ttu-id="7a749-132">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="7a749-132">SharePoint Online</span></span>  <br/> |
||<span data-ttu-id="7a749-133">SharePoint 하이브리드</span><span class="sxs-lookup"><span data-stu-id="7a749-133">SharePoint Hybrid</span></span>  <br/> |<span data-ttu-id="7a749-134">SharePoint Server 2016</span><span class="sxs-lookup"><span data-stu-id="7a749-134">SharePoint Server 2016</span></span>  <br/> |
|||<span data-ttu-id="7a749-135">SharePoint 하이브리드</span><span class="sxs-lookup"><span data-stu-id="7a749-135">SharePoint Hybrid</span></span>  <br/> |
   
<span data-ttu-id="7a749-136">확장의 낮은 끝에서 옵션을 선택 하는 경우에는 SharePoint Server 2007에서 마이그레이션이 완료 된 후에 업그레이드 계획을 시작 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-136">If you choose options on the low end of the scale (good enough), remember you will need to begin planning for upgrade very soon after migration from SharePoint Server 2007 is complete.</span></span> <span data-ttu-id="7a749-137">(SharePoint Server 2007에 대 한 지원 종료는 2017입니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-137">(end of support for SharePoint Server 2007 is October 10, 2017.</span></span> <span data-ttu-id="7a749-138">이러한 날짜는 변경 될 수 있으며 [제품 수명 주기 사이트](https://support.microsoft.com/lifecycle)를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-138">Please note that these dates are subject to change and check the [Product Lifecycle site](https://support.microsoft.com/lifecycle).)</span></span>
  
## <a name="where-can-i-go-next"></a><span data-ttu-id="7a749-139">다음으로 이동할 위치</span><span class="sxs-lookup"><span data-stu-id="7a749-139">Where can I go next?</span></span>

<span data-ttu-id="7a749-140">SharePoint Server는 자체 서버에 온-프레미스로 설치할 수 있거나 Microsoft Office 365의 일부인 온라인 서비스인 SharePoint Online을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-140">SharePoint Server can be installed on-premises on your own servers, or you can use SharePoint Online, which is an online service that is part of Microsoft Office 365.</span></span> <span data-ttu-id="7a749-141">다음을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-141">You can choose to:</span></span>
  
- <span data-ttu-id="7a749-142">SharePoint Online으로 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="7a749-142">Migrate to SharePoint Online</span></span>
    
- <span data-ttu-id="7a749-143">SharePoint Server 온-프레미스 업그레이드</span><span class="sxs-lookup"><span data-stu-id="7a749-143">Upgrade SharePoint Server on-premises</span></span>
    
- <span data-ttu-id="7a749-144">위의 두 작업을 모두 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-144">Do both of the above</span></span>
    
- <span data-ttu-id="7a749-145">[SharePoint 하이브리드](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx) 솔루션 구현</span><span class="sxs-lookup"><span data-stu-id="7a749-145">Implement a [SharePoint hybrid](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx) solution</span></span> 
    
<span data-ttu-id="7a749-146">앞으로 또는 사용자 지정 내용을 유지 관리 하거나 마이그레이션하고 SharePoint Server가 의존 하는 하드웨어를 업그레이드 하는 경우 서버 팜 유지 관리와 관련 된 숨겨진 비용을 염두에 두어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-146">Be aware of hidden costs associated with maintaining a server farm going forward, maintaining or migrating customizations, and upgrading the hardware upon which SharePoint Server depends.</span></span> <span data-ttu-id="7a749-147">필요 하다 면 온-프레미스 SharePoint Server 팜을 사용 하는 것이 rewarding 그렇지 않고 이전 SharePoint 서버에서 팜을 실행 하 여 사용자 지정을 많이 수행 하지 않으면 SharePoint Online으로 계획 된 마이그레이션을 활용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-147">Having an on-premises SharePoint Server farm is rewarding if it is a necessity; otherwise, if you run your farm on legacy SharePoint Servers, without heavy customization, you can benefit from a planned migration to SharePoint Online.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="7a749-148">SharePoint 2007의 콘텐츠가 자주 사용 되지 않는 경우에도 다른 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-148">There is another option if the content in SharePoint 2007 is infrequently used.</span></span> <span data-ttu-id="7a749-149">일부 SharePoint 관리자는 [Office 365 구독을 만들고](https://go.microsoft.com/fwlink/?linkid=843152), 새 sharepoint online 사이트를 설정한 다음, sharepoint 2007에서 새로운 sharepoint online 사이트에 가장 중요 한 문서만을 제거 하도록 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-149">Some SharePoint Administrators may choose to [create an Office 365 Subscription](https://go.microsoft.com/fwlink/?linkid=843152), set up a brand new SharePoint Online site, and then cut away from SharePoint 2007, cleanly, taking only the most essential documents to the fresh SharePoint Online sites.</span></span> <span data-ttu-id="7a749-150">여기서는 데이터가 SharePoint 2007 사이트에서 보관 사서함으로 배출 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-150">From there, data may be drained from the SharePoint 2007 site into archives.</span></span> <span data-ttu-id="7a749-151">사용자가 SharePoint 2007 설치 데이터로 데이터 작업을 수행 하는 방법을 생각해 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-151">Give thought to how users work with data your SharePoint 2007 installation.</span></span> <span data-ttu-id="7a749-152">이 문제를 해결 하는 방법이 독창적인 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-152">There may be creative ways to resolve this problem!</span></span> 
  
|<span data-ttu-id="7a749-153">**SharePoint Online (SPO)**</span><span class="sxs-lookup"><span data-stu-id="7a749-153">**SharePoint Online (SPO)**</span></span>|<span data-ttu-id="7a749-154">**SharePoint Server 온-프레미스**</span><span class="sxs-lookup"><span data-stu-id="7a749-154">**SharePoint Server on-premises**</span></span>|
|:-----|:-----|
|<span data-ttu-id="7a749-155">높은 비용 (계획/실행/확인)</span><span class="sxs-lookup"><span data-stu-id="7a749-155">High cost in time (plan / execution / verification)</span></span>  <br/> |<span data-ttu-id="7a749-156">높은 비용 (계획/실행/확인)</span><span class="sxs-lookup"><span data-stu-id="7a749-156">High cost in time (plan / execution / verification)</span></span>  <br/> |
|<span data-ttu-id="7a749-157">저렴 한 비용 (하드웨어 구입 없음)</span><span class="sxs-lookup"><span data-stu-id="7a749-157">Lower cost in funds (no hardware purchases)</span></span>  <br/> |<span data-ttu-id="7a749-158">자금 비용 (하드웨어 + devs/관리자)</span><span class="sxs-lookup"><span data-stu-id="7a749-158">Higher cost in funds (hardware + devs / admins)</span></span>  <br/> |
|<span data-ttu-id="7a749-159">마이그레이션 1 회 비용</span><span class="sxs-lookup"><span data-stu-id="7a749-159">One-time cost in migration</span></span>  <br/> |<span data-ttu-id="7a749-160">향후 마이그레이션 당 1 회 비용 반복</span><span class="sxs-lookup"><span data-stu-id="7a749-160">One-time cost repeated per future migration</span></span>  <br/> |
|<span data-ttu-id="7a749-161">낮은 총 소유 비용/유지 관리</span><span class="sxs-lookup"><span data-stu-id="7a749-161">Low total cost of ownership / maintenance</span></span>  <br/> |<span data-ttu-id="7a749-162">높은 총 소유 비용/유지 관리</span><span class="sxs-lookup"><span data-stu-id="7a749-162">High total cost of ownership / maintenance</span></span>  <br/> |
   
<span data-ttu-id="7a749-163">Office 365로 마이그레이션하면 데이터를 구성 하 고 클라우드로 수행 해야 하는 작업을 결정 하는 동시에 일회성 이동 비용이 더 많이 듭니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-163">When you migrate to Office 365, the one-time move will have a heavier cost up-front, while you're organizing data and deciding what to take to the cloud and what to leave behind.</span></span> <span data-ttu-id="7a749-164">그러나 업그레이드는 해당 지점부터 자동으로 진행 되며, 더 이상 하드웨어 및 소프트웨어 업데이트를 관리할 필요가 없으며 팜의 최신 시간이[SLA](https://go.microsoft.com/fwlink/?linkid=843153)(서비스 수준 계약)를 통해 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-164">However, upgrades will be automatic from that point, you will no longer need to manage hardware and software updates, and the up-time of your farm will be backed by a Microsoft Service Level Agreement ([SLA](https://go.microsoft.com/fwlink/?linkid=843153)).</span></span>
  
### <a name="migrate-to-sharepoint-online"></a><span data-ttu-id="7a749-165">SharePoint Online으로 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="7a749-165">Migrate to SharePoint Online</span></span>

<span data-ttu-id="7a749-166">연결 된 서비스 설명을 검토 하 여 SharePoint Online에 필요한 모든 기능이 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-166">Make sure that SharePoint Online has all the features you need by reviewing the associated service description.</span></span> <span data-ttu-id="7a749-167">다음은 모든 Office 365 서비스 설명에 대 한 링크입니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-167">Here's the link to all Office 365 Service Descriptions:</span></span>
  
[<span data-ttu-id="7a749-168">Office 365 서비스 설명</span><span class="sxs-lookup"><span data-stu-id="7a749-168">Office 365 Service Descriptions</span></span>](https://go.microsoft.com/fwlink/?linkid=272060)
  
<span data-ttu-id="7a749-169">SharePoint 2007에서 SharePoint Online으로 마이그레이션하는 직접적인 방법은 없습니다. SharePoint Online으로 이동 하는 작업은 수동으로 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-169">There is no direct way to migrate from SharePoint 2007 to SharePoint Online; your move to SharePoint Online would be done manually.</span></span> <span data-ttu-id="7a749-170">SharePoint Server 2013 또는 SharePoint Server 2016로 업그레이드 하는 경우 이동 과정에서 SharePoint 마이그레이션 API (예: 비즈니스용 OneDrive로 정보 마이그레이션)를 사용 하는 것이 포함 될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-170">If you upgrade to SharePoint Server 2013 or SharePoint Server 2016, your move might also involve using the SharePoint Migration API (to migrate information into OneDrive for Business, for example).</span></span>
  
|<span data-ttu-id="7a749-171">**온라인 Pro**</span><span class="sxs-lookup"><span data-stu-id="7a749-171">**Online Pro**</span></span>|<span data-ttu-id="7a749-172">**온라인 Con**</span><span class="sxs-lookup"><span data-stu-id="7a749-172">**Online Con**</span></span>|
|:-----|:-----|
|<span data-ttu-id="7a749-173">Microsoft는 SPO 하드웨어 및 모든 하드웨어 관리를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-173">Microsoft supplies SPO hardware and all hardware administration.</span></span>  <br/> |<span data-ttu-id="7a749-174">사용 가능한 기능은 SharePoint Server 온-프레미스와 SPO 간에 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-174">Available features may be different between SharePoint Server on-premises and SPO.</span></span>  <br/> |
|<span data-ttu-id="7a749-175">구독의 전역 관리자 이며 관리자에 게 SPO 사이트를 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-175">You are the global administrator of your subscription, and may assign administrators to SPO sites.</span></span>  <br/> |<span data-ttu-id="7a749-176">SharePoint Server 온-프레미스에서 팜 관리자가 사용할 수 있는 일부 작업이 Office 365의 SharePoint 관리자 역할에 포함 되지 않거나 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-176">Some actions available to a Farm Administrator in SharePoint Server on-premises do not exist (or are not necessary) included in the SharePoint Administrator role in Office 365.</span></span>  <br/> |
|<span data-ttu-id="7a749-177">Microsoft는 기본 하드웨어 및 소프트웨어에 패치, 수정 사항 및 업데이트를 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-177">Microsoft applies patches, fixes and updates to underlying hardware and software.</span></span>  <br/> |<span data-ttu-id="7a749-178">서비스의 기본 파일 시스템에 대 한 액세스 권한이 없기 때문에 일부 사용자 지정 내용이 제한 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-178">Because there is no access to the underlying file system in the service, some customizations are limited.</span></span>  <br/> |
|<span data-ttu-id="7a749-179">Microsoft는 서비스 수준 [계약](https://go.microsoft.com/fwlink/?linkid=843153) 을 게시 하 고 신속 하 게 이동 하 여 서비스 수준 인시던트를 해결 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-179">Microsoft publishes [Service Level Agreements](https://go.microsoft.com/fwlink/?linkid=843153) and moves quickly to resolve service level incidents.</span></span>  <br/> |<span data-ttu-id="7a749-180">백업 및 복원 및 기타 복구 옵션은 SharePoint Online의 서비스에 의해 자동화 되며, 사용 되지 않는 경우에는 백업이 덮어쓰여집니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-180">Backup and restore and other recovery options are automated by the service in SharePoint Online - backups are overwritten if not used.</span></span>  <br/> |
|<span data-ttu-id="7a749-181">보안 테스트 및 서버 성능 조정은 Microsoft의 서비스에서 지속적으로 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-181">Security testing and server performance tuning are carried out on an ongoing basis in the service by Microsoft.</span></span>  <br/> |<span data-ttu-id="7a749-182">사용자 인터페이스 및 기타 SharePoint 기능의 변경 내용은 서비스에 의해 설치 되며 설정 또는 해제 해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-182">Changes to the user interface and other SharePoint features are installed by the service and may need to be toggled on or off.</span></span>  <br/> |
|<span data-ttu-id="7a749-183">Office 365은 다양 한 업계 표준을 충족 합니다 [365](https://go.microsoft.com/fwlink/?linkid=843165).</span><span class="sxs-lookup"><span data-stu-id="7a749-183">Office 365 meets many industry standards: [Office 365 Compliance](https://go.microsoft.com/fwlink/?linkid=843165).</span></span>  <br/> |<span data-ttu-id="7a749-184">마이그레이션에 대 한 [Fasttrack](https://go.microsoft.com/fwlink/?linkid=518597) 지원은 제한 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-184">[FastTrack](https://go.microsoft.com/fwlink/?linkid=518597) assistance for migration is limited.</span></span>  <br/> <span data-ttu-id="7a749-185">업그레이드의 대부분은 수동 또는 [SharePoint Online 및 OneDrive 마이그레이션 콘텐츠 로드맵](https://go.microsoft.com/fwlink/?linkid=843184)에 설명 된 SPO 마이그레이션 API를 통해 진행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-185">Much of the upgrade will be manual, or via the SPO Migration API described in the [SharePoint Online and OneDrive Migration Content Roadmap](https://go.microsoft.com/fwlink/?linkid=843184).</span></span>  <br/> |
|<span data-ttu-id="7a749-186">Microsoft 지원 엔지니어 또는 데이터 센터의 직원은 구독에 대 한 무제한 관리자 액세스 권한을 갖지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-186">Neither Microsoft Support Engineers nor employees in the datacenter have unrestricted admin access to your subscription.</span></span>  <br/> |<span data-ttu-id="7a749-187">최신 버전의 SharePoint를 지원 하도록 하드웨어 인프라를 업그레이드 해야 하거나 업그레이드에 보조 팜이 필요한 경우에는 추가 비용이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-187">There can be additional costs if hardware infrastructure needs to be upgraded to support the newer version of SharePoint, or if a secondary farm is required for upgrade.</span></span>  <br/> |
|<span data-ttu-id="7a749-188">파트너는 데이터를 SharePoint Online으로 마이그레이션하는 일회성 작업을 지원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-188">Partners can assist with the one-time job of migrating your data to SharePoint Online.</span></span>  <br/> ||
|<span data-ttu-id="7a749-189">온라인 제품은 기능에 의해 자동으로 업데이트 되며, 기능은 사용 중지 수 있지만 실제 지원은 제공 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-189">Online products are updated automatically across the service meaning that though features may deprecate, there is no true end of support.</span></span>  <br/> ||
   
<span data-ttu-id="7a749-190">새 Office 365 사이트를 만들려고 했으며 필요한 경우 데이터를 수동으로 마이그레이션하는 경우에는 여기에서 Office 365 옵션을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-190">If you've decided to create a new Office 365 site, and will manually migrate data to it as is needed, you can look at your Office 365 options right here:</span></span>
  
[<span data-ttu-id="7a749-191">Office 365 계획 옵션</span><span class="sxs-lookup"><span data-stu-id="7a749-191">Office 365 Plan Options</span></span>](https://go.microsoft.com/fwlink/?linkid=843151)
  
### <a name="upgrade-sharepoint-server-on-premises"></a><span data-ttu-id="7a749-192">SharePoint Server 온-프레미스 업그레이드</span><span class="sxs-lookup"><span data-stu-id="7a749-192">Upgrade SharePoint Server on-premises</span></span>

<span data-ttu-id="7a749-193">과거에는 sharepoint 업그레이드에서 버전을 건너뛰어도 서 SharePoint Server 2016의 릴리스를 제외 하는 방법을 더 이상 제공 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-193">There is historically no way to skip versions in SharePoint Upgrades, at least not as of the release of SharePoint Server 2016.</span></span> <span data-ttu-id="7a749-194">즉, 업그레이드가 순차적으로 진행 됨을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-194">That means upgrades go serially:</span></span>
  
|||
|:-----|:-----|
||<span data-ttu-id="7a749-195">SharePoint 2007</span><span class="sxs-lookup"><span data-stu-id="7a749-195">SharePoint 2007</span></span> | <span data-ttu-id="7a749-196">SharePoint Server 2010</span><span class="sxs-lookup"><span data-stu-id="7a749-196">SharePoint Server 2010</span></span> | <span data-ttu-id="7a749-197">SharePoint Server 2013</span><span class="sxs-lookup"><span data-stu-id="7a749-197">SharePoint Server 2013</span></span> | <span data-ttu-id="7a749-198">SharePoint Server 2016</span><span class="sxs-lookup"><span data-stu-id="7a749-198">SharePoint Server 2016</span></span> |
   
<span data-ttu-id="7a749-199">SharePoint 2007에서 SharePoint Server 2016로 전체 경로를 사용 하기 위해서는 상당한 시간이 투자 되 고, 업그레이드 된 하드웨어 측면에서 비용이 수반 됩니다 (SQL server도 업그레이드 해야 한다는 점을 유의 해야 함), 소프트웨어 및 관리를 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-199">To take the entire path from SharePoint 2007 to SharePoint Server 2016 will mean a significant investment of time and will involve a cost in terms of upgraded hardware (be aware that SQL servers must also be upgraded), software, and administration.</span></span> <span data-ttu-id="7a749-200">기능의 중요도에 따라 사용자 지정 내용이 업그레이드 되거나 중단 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-200">Customizations will need to be upgraded or abandoned, according to the criticality of the feature.</span></span>
  
> [!NOTE]
> <span data-ttu-id="7a749-201">수명 종료 SharePoint 2007 팜을 유지 관리 하 고, 새 하드웨어에 SharePoint Server 2016 팜을 설치한 다음 (별도의 팜을 나란히 실행), 콘텐츠를 다운로드 하 고 다시 업로드 하기 위해 콘텐츠의 수동 마이그레이션을 계획 및 실행 하는 것이 가능 합니다. 예제)</span><span class="sxs-lookup"><span data-stu-id="7a749-201">It's possible to maintain your end-of-life SharePoint 2007 farm, install a SharePoint Server 2016 farm on new hardware (so the separate farms run side-by-side), and then plan and execute a manual migration of content (for downloading and re-uploading content, for example).</span></span> <span data-ttu-id="7a749-202">마지막으로 수정한 계정을 수동으로 이동 하는 계정의 별칭으로 이동 하는 것과 같은 수동 이동의 몇 가지 gotchas, 미리 수행 해야 하는 작업 (예: 사이트, 하위 사이트, 사용 권한 및 목록 다시 만들기)에 대해 알아야 합니다. 구조).</span><span class="sxs-lookup"><span data-stu-id="7a749-202">Be aware of some of the gotchas of manual moves (such as moves of documents replacing the last modified account with the alias of the account doing the manual move), and the work that must be done ahead of time (such as recreating sites, sub-sites, permissions and list structures).</span></span> <span data-ttu-id="7a749-203">이는 저장소로 이동할 수 있는 데이터를 고려 하거나 더 이상 필요 하지 않은 마이그레이션에 대 한 영향을 줄일 수 있는 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-203">Again, this is the time to consider what data you can move into storage, or no longer need, an action that can reduce the impact of migration.</span></span>
  
<span data-ttu-id="7a749-204">두 방법 중 하나를 수행 하 여 업그레이드 전에 환경을 정리 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-204">Either way, clean your environment prior to upgrade.</span></span> <span data-ttu-id="7a749-205">업그레이드를 수행 하기 전에 기존 팜이 제대로 작동 하 고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-205">Be certain your existing farm is functional before you upgrade, and (for sure) before you decommission!</span></span> 
  
<span data-ttu-id="7a749-206">**지원 및 지원 되지 않는 업그레이드 경로**를 검토 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-206">Remember to review the **supported and unsupported upgrade paths**:</span></span> 
  
- [<span data-ttu-id="7a749-207">SharePoint Server 2007</span><span class="sxs-lookup"><span data-stu-id="7a749-207">SharePoint Server 2007</span></span>](https://go.microsoft.com/fwlink/?linkid=843156)
    
- [<span data-ttu-id="7a749-208">SharePoint Server 2010</span><span class="sxs-lookup"><span data-stu-id="7a749-208">SharePoint Server 2010</span></span>](https://go.microsoft.com/fwlink/?linkid=843156)
    
- [<span data-ttu-id="7a749-209">SharePoint Server 2013</span><span class="sxs-lookup"><span data-stu-id="7a749-209">SharePoint Server 2013</span></span>](https://go.microsoft.com/fwlink/?linkid=843157)
    
<span data-ttu-id="7a749-210">**사용자 지정**내용이 있는 경우 마이그레이션 경로의 각 단계에 대 한 업그레이드 계획을 수립 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-210">If you have **customizations**, it's critical you have a plan your upgrade for each step in the migration path:</span></span> 
  
- [<span data-ttu-id="7a749-211">SharePoint 2007</span><span class="sxs-lookup"><span data-stu-id="7a749-211">SharePoint 2007</span></span>](https://go.microsoft.com/fwlink/?linkid=843158)
    
- [<span data-ttu-id="7a749-212">SharePoint Server 2010</span><span class="sxs-lookup"><span data-stu-id="7a749-212">SharePoint Server 2010</span></span>](https://go.microsoft.com/fwlink/?linkid=843160)
    
- [<span data-ttu-id="7a749-213">SharePoint Server 2013</span><span class="sxs-lookup"><span data-stu-id="7a749-213">SharePoint Server 2013</span></span>](https://go.microsoft.com/fwlink/?linkid=843162)
    
|<span data-ttu-id="7a749-214">**온-프레미스 Pro**</span><span class="sxs-lookup"><span data-stu-id="7a749-214">**On-premises Pro**</span></span>|<span data-ttu-id="7a749-215">**온-프레미스 Con**</span><span class="sxs-lookup"><span data-stu-id="7a749-215">**On-premises Con**</span></span>|
|:-----|:-----|
|<span data-ttu-id="7a749-216">서버 하드웨어에서 SharePoint 팜의 모든 측면에 대 한 모든 권한</span><span class="sxs-lookup"><span data-stu-id="7a749-216">Full control of all aspects of your SharePoint Farm, from the server hardware up.</span></span>  <br/> |<span data-ttu-id="7a749-217">모든 휴식 및 수정 사항은 회사의 책임입니다 (제품을 지원 하지 않을 경우 Microsoft가 지 원하는 경우 대금을 지불 해야 할 수 있음).</span><span class="sxs-lookup"><span data-stu-id="7a749-217">All breaks and fixes are the responsibility of your company (can engage paid Microsoft Support if your product is not at end of support):</span></span>  <br/> |
|<span data-ttu-id="7a749-218">하이브리드를 통해 온-프레미스 팜을 SharePoint Online 구독에 연결 하는 옵션을 사용 하는 SharePoint Server 온-프레미스의 전체 기능 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-218">Full feature set of SharePoint Server on-premises with the option to connect your on-premises farm to a SharePoint Online subscription via hybrid.</span></span>  <br/> |<span data-ttu-id="7a749-219">업그레이드, 패치, 보안 픽스 및 모든 SharePoint Server의 온-프레미스 유지 관리</span><span class="sxs-lookup"><span data-stu-id="7a749-219">Upgrade, patches, security fixes, and all maintenance of SharePoint Server managed on-premises.</span></span>  <br/> |
|<span data-ttu-id="7a749-220">보다 강력한 사용자 지정을 위한 모든 권한</span><span class="sxs-lookup"><span data-stu-id="7a749-220">Full access for greater customization.</span></span>  <br/> |<span data-ttu-id="7a749-221">[Office 365에서 지 원하는 규정 준수 표준은](https://go.microsoft.com/fwlink/?linkid=843165) 온-프레미스에서 수동으로 구성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-221">[Compliance standards supported by Office 365](https://go.microsoft.com/fwlink/?linkid=843165) must be manually configured on-premises.</span></span>  <br/> |
|<span data-ttu-id="7a749-222">온-프레미스에서 수행 되는 보안 테스트 및 서버 성능 조정</span><span class="sxs-lookup"><span data-stu-id="7a749-222">Security testing, and server performance tuning, carried out on your premises (is under your control).</span></span>  <br/> |<span data-ttu-id="7a749-223">Office 365은 sharepoint Online에서 SharePoint Server 온-프레미스와 상호 운용 되지 않는 기능을 사용할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-223">Office 365 may make features available to SharePoint Online that do not interoperate with SharePoint Server on-premises</span></span>  <br/> |
|<span data-ttu-id="7a749-224">파트너는 다음 버전의 SharePoint Server (및 이후)로 데이터 마이그레이션을 지원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-224">Partners can assist with migrating data to the next version of SharePoint Server (and beyond).</span></span>  <br/> |<span data-ttu-id="7a749-225">Sharepoint Server 사이트에서는 SharePoint Online에 표시 되는 대로 [SSL/TLS](https://go.microsoft.com/fwlink/?linkid=843167) 인증서를 자동으로 사용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-225">Your SharePoint Server sites will not automatically use [SSL/TLS](https://go.microsoft.com/fwlink/?linkid=843167) certificates as is seen in SharePoint Online.</span></span>  <br/> |
|<span data-ttu-id="7a749-226">SharePoint Server 온-프레미스의 명명 규칙, 백업 및 복원 및 기타 복구 옵션에 대 한 모든 권한</span><span class="sxs-lookup"><span data-stu-id="7a749-226">Full control of naming conventions, backup and restore and other recovery options in SharePoint Server on-premises.</span></span>  <br/> |<span data-ttu-id="7a749-227">SharePoint Server 온-프레미스는 제품 수명 주기에 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-227">SharePoint Server on-premises is sensitive to product lifecycles.</span></span>  <br/> |
   
### <a name="upgrade-resources"></a><span data-ttu-id="7a749-228">리소스 업그레이드</span><span class="sxs-lookup"><span data-stu-id="7a749-228">Upgrade Resources</span></span>

<span data-ttu-id="7a749-229">먼저 하드웨어 및 소프트웨어 요구 사항을 충족 하는지 파악 한 다음 지원 되는 업그레이드 방법을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-229">Begin by knowing that you meet hardware and software requirements, then follow supported upgrade methods.</span></span>
  
- <span data-ttu-id="7a749-230">다음 **에 대 한 하드웨어/소프트웨어 요구 사항**:</span><span class="sxs-lookup"><span data-stu-id="7a749-230">**Hardware/software requirements for**:</span></span> 
    
    <span data-ttu-id="7a749-231">[Sharepoint server 2010](https://go.microsoft.com/fwlink/?linkid=843204) | [sharepoint server 2010](https://go.microsoft.com/fwlink/?linkid=843204) | [sharepoint server 2013](https://go.microsoft.com/fwlink/?linkid=843206) | [sharepoint server 2016](https://go.microsoft.com/fwlink/?linkid=843207)</span><span class="sxs-lookup"><span data-stu-id="7a749-231">[SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204) | [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843206) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843207)</span></span>
    
- <span data-ttu-id="7a749-232">다음 **에 대 한 소프트웨어 경계 및 제한**사항:</span><span class="sxs-lookup"><span data-stu-id="7a749-232">**Software boundaries and limits for**:</span></span> 
    
    <span data-ttu-id="7a749-233">[Sharepoint server 2007](https://go.microsoft.com/fwlink/?linkid=843245) | [sharepoint server 2010](https://go.microsoft.com/fwlink/?linkid=843247) | [sharepoint server 2013](https://go.microsoft.com/fwlink/?linkid=843248) | [sharepoint server 2016](https://go.microsoft.com/fwlink/?linkid=843249)</span><span class="sxs-lookup"><span data-stu-id="7a749-233">[SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843245) | [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843247) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843248) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843249)</span></span>
    
- <span data-ttu-id="7a749-234">**업그레이드 프로세스 개요**:</span><span class="sxs-lookup"><span data-stu-id="7a749-234">**The upgrade process overview for**:</span></span> 
    
    <span data-ttu-id="7a749-235">[Sharepoint server 2007](https://go.microsoft.com/fwlink/?linkid=843250) | [sharepoint server 2010](https://go.microsoft.com/fwlink/?linkid=843251) | [sharepoint server 2013](https://go.microsoft.com/fwlink/?linkid=843252) | [sharepoint server 2016](https://go.microsoft.com/fwlink/?linkid=843359)</span><span class="sxs-lookup"><span data-stu-id="7a749-235">[SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843250) | [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843251) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843252) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843359)</span></span>
    
### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-on-premises"></a><span data-ttu-id="7a749-236">SharePoint Online과 온-프레미스 간에 SharePoint 하이브리드 솔루션 만들기</span><span class="sxs-lookup"><span data-stu-id="7a749-236">Create a SharePoint hybrid solution between SharePoint Online and on-premises</span></span>

<span data-ttu-id="7a749-237">마이그레이션 요구 사항에 대 한 대답이 온-프레미스에서 제공 되는 자체 제어와 SharePoint Online에서 제공 하는 소유 비용이 더 많은 경우에는 하이브리드를 통해 SharePoint Server 2013 또는 2016 팜을 SharePoint Online에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-237">If the answer to your migration needs is somewhere between the self-control offered by on-premises, and the lower cost of ownership offered by SharePoint Online, you can connect SharePoint Server 2013 or 2016 farms to SharePoint Online, through hybrids.</span></span> [<span data-ttu-id="7a749-238">SharePoint 하이브리드 솔루션에 대 한 자세한 정보</span><span class="sxs-lookup"><span data-stu-id="7a749-238">Learn about SharePoint hybrid solutions</span></span>](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx)
  
<span data-ttu-id="7a749-239">하이브리드 SharePoint Server 팜이 비즈니스에 이익이 되는 경우 기존 유형의 하이브리드를 숙지 하 고 온-프레미스 SharePoint 팜과 Office 365 구독 간에 연결을 구성 하는 방법에 익숙해져야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-239">If you decide that a hybrid SharePoint Server farm will benefit your business, familiarize yourself with the existing types of hybrid and how to configure the connection between your on-premises SharePoint farm and your Office 365 subscription.</span></span>
  
<span data-ttu-id="7a749-240">[Office 365 개발/테스트 환경을](https://go.microsoft.com/fwlink/?linkid=843152)만들어 어떻게 작동 하는지 확인할 수 있는 좋은 방법 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-240">One good way to see how this works is by creating an [Office 365 dev/test environment](https://go.microsoft.com/fwlink/?linkid=843152).</span></span> <span data-ttu-id="7a749-241">평가판이 있거나 Office 365 구독을 구매한 후에는 직접 데이터를 마이그레이션할 수 있는 SharePoint Online의 사이트 모음, 웹 및 문서 라이브러리를 만드는 방법, 즉 마이그레이션 API를 사용 하 여 수동으로 또는-My를 마이그레이션하려고 합니다. 하이브리드 마법사를 통해 비즈니스용 OneDrive에 사이트 콘텐츠를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-241">Once you have a trial or purchased Office 365 subscription, you'll be on your way to creating the site collections, webs, and document libraries in SharePoint Online to which you can migrate data (either manually, by use of the Migration API, or - if you want to migrate My Site content to OneDrive for Business - through the hybrid wizard).</span></span>
  
> [!NOTE]
> <span data-ttu-id="7a749-242">하이브리드 옵션을 사용 하려면 SharePoint 2007 팜을 온-프레미스에서 SharePoint Server 2013 또는 SharePoint Server 2016로 업그레이드 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-242">Remember that your SharePoint 2007 farm will need to be upgraded, on-premises, to either SharePoint Server 2013 or SharePoint Server 2016 to use the hybrid option</span></span> 
  
## <a name="related-topics"></a><span data-ttu-id="7a749-243">관련 항목</span><span class="sxs-lookup"><span data-stu-id="7a749-243">Related topics</span></span>

[<span data-ttu-id="7a749-244">업그레이드 문제 해결 및 다시 시작 (Office SharePoint Server 2007)</span><span class="sxs-lookup"><span data-stu-id="7a749-244">Troubleshoot and resume upgrade (Office SharePoint Server 2007)</span></span>](https://go.microsoft.com/fwlink/?linkid=843192)
  
[<span data-ttu-id="7a749-245">업그레이드 문제 해결 (SharePoint Server 2010)</span><span class="sxs-lookup"><span data-stu-id="7a749-245">Troubleshoot upgrade issues (SharePoint Server 2010)</span></span>](https://go.microsoft.com/fwlink/?linkid=843194)
  
[<span data-ttu-id="7a749-246">SharePoint 2013에서 데이터베이스 업그레이드 문제 해결</span><span class="sxs-lookup"><span data-stu-id="7a749-246">Troubleshoot database upgrade issues in SharePoint 2013</span></span>](https://go.microsoft.com/fwlink/?linkid=843195)
  
[<span data-ttu-id="7a749-247">업그레이드에 도움이 되는 Microsoft 파트너를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a749-247">Search for Microsoft Partners to help with Upgrade</span></span>](https://go.microsoft.com/fwlink/?linkid=841249)
  
[<span data-ttu-id="7a749-248">Office 2007 서버 및 클라이언트에서 업그레이드 하는 데 도움이 되는 리소스</span><span class="sxs-lookup"><span data-stu-id="7a749-248">Resources to help you upgrade from Office 2007 servers and clients</span></span>](upgrade-from-office-2007-servers-and-products.md)
  

