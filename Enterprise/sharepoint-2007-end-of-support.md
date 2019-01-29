---
title: SharePoint Server 2007 지원 종료 로드맵
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 01/28/2019
ms.audience: ITPro
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
ms.collection: Ent_O365
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
description: 2017 년 10 월 10 년에서 SharePoint Server 2007에 대 한 지원을 끝냈습니다. 업그레이드 옵션, 문제해결, 모범 사례, 시스템 요구 사항, 업그레이드 단계 및 Microsoft 파트너 로부터 도움을 받을 하는 방법에 대해 자세히 알아보려면이 문서를 읽어보십시오.
ms.openlocfilehash: b0d3eda690733b45ee82054e145642a5c76125d5
ms.sourcegitcommit: 792fe2ccc860517fe3dcbc9c668bae97f39ae7c8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/29/2019
ms.locfileid: "29604519"
---
# <a name="sharepoint-server-2007-end-of-support-roadmap"></a><span data-ttu-id="032ce-104">SharePoint Server 2007 지원 종료 로드맵</span><span class="sxs-lookup"><span data-stu-id="032ce-104">SharePoint Server 2007 end of support roadmap</span></span>

<span data-ttu-id="032ce-p102">**2017 년 10 월 10 년**Microsoft Office SharePoint Server 2007은 지원의 끝에 도달 했습니다. SharePoint Server 2007에서 Office 365 또는 최신 버전의 SharePoint Server 온-프레미스로 마이그레이션을 시작 하지 않은 경우 지금 계획을 시작 하는 시간 됩니다. 이 문서는 리소스를 사용자가 데이터를 SharePoint Online으로 마이그레이션 또는 SharePoint 서버에서 온-프레미스 업그레이드에 대해 자세히 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-p102">On **October 10, 2017**, Microsoft Office SharePoint Server 2007 reached end of support. If you haven't begun your migration from SharePoint Server 2007 to Office 365 or a newer version of SharePoint Server on-premises, now's the time to start planning. This article details resources to help people migrate data to SharePoint Online, or upgrade your SharePoint Server on-premises.</span></span> 
  
## <a name="what-does-end-of-support-mean"></a><span data-ttu-id="032ce-108">지원 의미의 역할 끝 무엇입니까?</span><span class="sxs-lookup"><span data-stu-id="032ce-108">What does end of support mean?</span></span>

<span data-ttu-id="032ce-p103">SharePoint Server 같은 거의 모든 Microsoft 제품에는 주기가 지원 하는 동안 Microsoft의 새로운 기능, 버그 수정, 보안 픽스 및 등을 제공 합니다. 이 수명 주기는 일반적으로 제품의 초기 릴리스 날짜 로부터 10 년 동안 지속 하 고이 주기 끝이 제품의 지원 종료 라고 합니다. 지원의 끝 Microsoft 더이상 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-p103">SharePoint Server, like almost all Microsoft products, has a support lifecycle during which Microsoft provides new features, bug fixes, security fixes, and so on. This lifecycle typically lasts for 10 years from the date of the product's initial release, and the end of this lifecycle is known as the product's end of support. At end of support, Microsoft no longer provides:</span></span>
  
- <span data-ttu-id="032ce-112">발생할 수 있는 문제에 대 한 기술 지원</span><span class="sxs-lookup"><span data-stu-id="032ce-112">Technical support for problems that may occur;</span></span>
    
- <span data-ttu-id="032ce-113">검색 되는 및 안정성과 서버;의 유용성 영향을 줄 수 있는 문제에 대 한 버그 수정</span><span class="sxs-lookup"><span data-stu-id="032ce-113">Bug fixes for issues that are discovered and that may impact the stability and usability of the server;</span></span>
    
- <span data-ttu-id="032ce-114">검색 되는 하 고 서버를 공격에 취약 한 보안 위반 행위에 만들 수 있는 취약점에 대 한 보안 수정 및</span><span class="sxs-lookup"><span data-stu-id="032ce-114">Security fixes for vulnerabilities that are discovered and that may make the server vulnerable to security breaches; and</span></span> 
    
- <span data-ttu-id="032ce-115">표준 시간대를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-115">Time zone updates.</span></span>
    
<span data-ttu-id="032ce-p104">하지만 SharePoint Server 2007 팜은 여전히 작동할 수 년 10 월 10 2017 년, 없음 추가로 업데이트, 패치, 후 또는 (보안 패치/픽스가 포함), 제품에 대 한 픽스를 전달할 및 Microsoft 기술 지원 서비스는가 완벽 하 게 이동 하 여 해당 지원 노력을 제품의 최신 버전입니다. 설치에는 더이상 지원 또는 패치를 적용 하기 때문에 지원 접근 방법의 끝으로 제품을 업그레이드 하거나 해야 중요 한 데이터를 마이그레이션합니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-p104">Though your SharePoint Server 2007 farm will still be operational after October 10, 2017, no further updates, patches, or fixes will be shipped for the product (including security patches/fixes), and Microsoft Support will have fully shifted its support efforts to more recent versions of the product. Because your installation will no longer supported or patched, as end of support approaches you should upgrade the product, or migrate important data.</span></span>
  
> [!TIP]
> <span data-ttu-id="032ce-p105">마이그레이션 또는 업그레이드에 대 한 계획 된 이미 하지 않은 경우를 참조 하십시오: [SharePoint 2007 마이그레이션 옵션을 고려해 야](sharepoint-2007-migration-options.md)을 시작할 위치를의 몇가지 예입니다. 업그레이드 또는 Office 365 마이그레이션 (또는 둘 모두)를 도와줄 수는 [Microsoft 파트너](https://go.microsoft.com/fwlink/?linkid=841249) 에 대 한 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-p105">If you haven't already planned for upgrade or migration, please see: [SharePoint 2007 migration options to consider](sharepoint-2007-migration-options.md), for some examples of where to begin. You can also search for [Microsoft Partners](https://go.microsoft.com/fwlink/?linkid=841249) who can help with upgrade or Office 365 migration (or both).</span></span> 
  
<span data-ttu-id="032ce-120">Office 2007 서버 지원의 끝에 도달 하는 방법에 대 한 자세한 내용은 [2007 서버와 클라이언트가 Office에서 업그레이드 하는데 도움이 되는 리소스](upgrade-from-office-2007-servers-and-products.md)를 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-120">For more information about Office 2007 servers reaching the end of support, see [Resources to help you upgrade from Office 2007 servers and clients](upgrade-from-office-2007-servers-and-products.md).</span></span>
  
## <a name="what-are-my-options"></a><span data-ttu-id="032ce-121">내 옵션은 무엇입니까?</span><span class="sxs-lookup"><span data-stu-id="032ce-121">What are my options?</span></span>

<span data-ttu-id="032ce-p106">먼저 [제품 수명 주기 사이트](https://go.microsoft.com/fwlink/?linkid=843148)여야 합니다. 일 유예 기간 되는 온-프레미스 Microsoft 제품을 설치한 경우 있는지 확인 해야 지원 날짜의 끝에 대 한 하므로, 1 년 또는-수행 되도록 또는 마이그레이션 또는 업그레이드 마이그레이션을 일반적으로 필요-으로 예약할 수 있습니다. 다음 단계를 선택할 때는 충분 한 수, 효율적 운영, 및 제품 기능을 제공 하는 경우 최상의 기능 면에서 이해에 도움이 될 수 있습니다. 다음은 한 예가입니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-p106">Your first stop should be the [Product Lifecycle site](https://go.microsoft.com/fwlink/?linkid=843148). If you have an on-premises Microsoft product that is aging, you should check for its end of support date so that, a year or so out - or as long as your migrations generally require - you can schedule upgrade or migrations. When choosing the next step, it might help to think in terms of what would be good enough, better, and best when it comes to product features. Here's an example:</span></span>
  
|<span data-ttu-id="032ce-126">**중**</span><span class="sxs-lookup"><span data-stu-id="032ce-126">**Good**</span></span>|<span data-ttu-id="032ce-127">**더 나은**</span><span class="sxs-lookup"><span data-stu-id="032ce-127">**Better**</span></span>|<span data-ttu-id="032ce-128">**최상**</span><span class="sxs-lookup"><span data-stu-id="032ce-128">**Best**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="032ce-129">SharePoint Server 2010</span><span class="sxs-lookup"><span data-stu-id="032ce-129">SharePoint Server 2010</span></span>  <br/> |<span data-ttu-id="032ce-130">SharePoint Server 2013</span><span class="sxs-lookup"><span data-stu-id="032ce-130">SharePoint Server 2013</span></span>  <br/> |<span data-ttu-id="032ce-131">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="032ce-131">SharePoint Online</span></span>  <br/> |
||<span data-ttu-id="032ce-132">SharePoint 하이브리드</span><span class="sxs-lookup"><span data-stu-id="032ce-132">SharePoint Hybrid</span></span>  <br/> |<span data-ttu-id="032ce-133">SharePoint Server 2016</span><span class="sxs-lookup"><span data-stu-id="032ce-133">SharePoint Server 2016</span></span>  <br/> |
|||<span data-ttu-id="032ce-134">SharePoint 하이브리드</span><span class="sxs-lookup"><span data-stu-id="032ce-134">SharePoint Hybrid</span></span>  <br/> |
   
<span data-ttu-id="032ce-p107">SharePoint Server 2007에서 마이그레이션 후 가능한 한 빨리 업그레이드에 대 한 계획을 시작 해야 합니다 (충분 한) 규모의 낮은 끝의 옵션을 기억을 선택 하면 완료 됩니다. (SharePoint Server 2007에 대 한 지원 종료는 2017 년 10 월 10 년입니다. 이러한 날짜 변경 될 수를 확인 하 고 [제품 수명 주기 사이트](https://support.microsoft.com/en-us/lifecycle)를 참고를 하십시오.)</span><span class="sxs-lookup"><span data-stu-id="032ce-p107">If you choose options on the low end of the scale (good enough), remember you will need to begin planning for upgrade very soon after migration from SharePoint Server 2007 is complete. (end of support for SharePoint Server 2007 is October 10, 2017. Please note that these dates are subject to change and check the [Product Lifecycle site](https://support.microsoft.com/en-us/lifecycle).)</span></span>
  
## <a name="where-can-i-go-next"></a><span data-ttu-id="032ce-138">다음 이동할 수는 위치</span><span class="sxs-lookup"><span data-stu-id="032ce-138">Where can I go next?</span></span>

<span data-ttu-id="032ce-p108">SharePoint Server 온-프레미스 설치 자체 서버에 수 하거나 사용할 수 있습니다 SharePoint Online은 Microsoft Office 365의 일부인 온라인 서비스. 하도록 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-p108">SharePoint Server can be installed on-premises on your own servers, or you can use SharePoint Online, which is an online service that is part of Microsoft Office 365. You can choose to:</span></span>
  
- <span data-ttu-id="032ce-141">SharePoint Online으로 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="032ce-141">Migrate to SharePoint Online</span></span>
    
- <span data-ttu-id="032ce-142">업그레이드 SharePoint Server 온-프레미스</span><span class="sxs-lookup"><span data-stu-id="032ce-142">Upgrade SharePoint Server on-premises</span></span>
    
- <span data-ttu-id="032ce-143">위의 두 항목 모두를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-143">Do both of the above</span></span>
    
- <span data-ttu-id="032ce-144">[SharePoint 하이브리드](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx) 솔루션을 구현</span><span class="sxs-lookup"><span data-stu-id="032ce-144">Implement a [SharePoint hybrid](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx) solution</span></span> 
    
<span data-ttu-id="032ce-p109">숨겨진된 비용을 앞으로, 서버 팜을 유지 관리와 관련 된 유지 관리 또는 사용자 지정, 마이그레이션 및 종속 되는 SharePoint 서버 하드웨어를 업그레이드 알고 있어야 합니다. 에 반드시 필요 하다 면 가치 되는 온-프레미스 SharePoint 서버 팜에 필요 그렇지 않은 경우 팜의 굵은 사용자 지정 하지 않고 기존 SharePoint 서버에서 실행 하는 경우 있습니다 활용 하는 계획 된 마이그레이션에서 SharePoint online 합니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-p109">Be aware of hidden costs associated with maintaining a server farm going forward, maintaining or migrating customizations, and upgrading the hardware upon which SharePoint Server depends. Having an on-premises SharePoint Server farm is rewarding if it is a necessity; otherwise, if you run your farm on legacy SharePoint Servers, without heavy customization, you can benefit from a planned migration to SharePoint Online.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="032ce-p110">SharePoint 2007의 콘텐츠를 자주 사용 하는 경우 다른 옵션이 제공 됩니다. 일부 SharePoint 관리자는 새 SharePoint Online 사이트에는 가장 중요 한 카운터 문서의 경우에 수행 [는 Office 365 구독을 만드는](https://go.microsoft.com/fwlink/?linkid=843152)새로운 SharePoint Online 사이트를 설정 하 고 완벽 하 게, 잘라내기 SharePoint 2007에서 선택할 수 있습니다. 여기에서 보관 파일에 데이터 SharePoint 2007 사이트에서 소모 될 수 있습니다. 어떤 방식으로 사용자가 작동 데이터와 SharePoint 2007 설치 이러한 모든 작업을 제공 합니다. 이 문제를 해결 하기 위한 창의적인 방법이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-p110">There is another option if the content in SharePoint 2007 is infrequently used. Some SharePoint Administrators may choose to [create an Office 365 Subscription](https://go.microsoft.com/fwlink/?linkid=843152), set up a brand new SharePoint Online site, and then cut away from SharePoint 2007, cleanly, taking only the most essential documents to the fresh SharePoint Online sites. From there, data may be drained from the SharePoint 2007 site into archives. Give thought to how users work with data your SharePoint 2007 installation. There may be creative ways to resolve this problem!</span></span> 
  
|<span data-ttu-id="032ce-152">**SharePoint Online (SPO)**</span><span class="sxs-lookup"><span data-stu-id="032ce-152">**SharePoint Online (SPO)**</span></span>|<span data-ttu-id="032ce-153">**SharePoint Server 온-프레미스**</span><span class="sxs-lookup"><span data-stu-id="032ce-153">**SharePoint Server on-premises**</span></span>|
|:-----|:-----|
|<span data-ttu-id="032ce-154">시간에 높은 비용 (계획 / 실행 / 확인)</span><span class="sxs-lookup"><span data-stu-id="032ce-154">High cost in time (plan / execution / verification)</span></span>  <br/> |<span data-ttu-id="032ce-155">시간에 높은 비용 (계획 / 실행 / 확인)</span><span class="sxs-lookup"><span data-stu-id="032ce-155">High cost in time (plan / execution / verification)</span></span>  <br/> |
|<span data-ttu-id="032ce-156">자금 (하드웨어 구입 제외)에서 저렴 한 비용</span><span class="sxs-lookup"><span data-stu-id="032ce-156">Lower cost in funds (no hardware purchases)</span></span>  <br/> |<span data-ttu-id="032ce-157">자금에 더 높은 비용 (하드웨어 + 트랜잭션당 / 관리자)</span><span class="sxs-lookup"><span data-stu-id="032ce-157">Higher cost in funds (hardware + devs / admins)</span></span>  <br/> |
|<span data-ttu-id="032ce-158">마이그레이션에 1 회 비용</span><span class="sxs-lookup"><span data-stu-id="032ce-158">One-time cost in migration</span></span>  <br/> |<span data-ttu-id="032ce-159">향후 마이그레이션 당 반복 1 회 비용</span><span class="sxs-lookup"><span data-stu-id="032ce-159">One-time cost repeated per future migration</span></span>  <br/> |
|<span data-ttu-id="032ce-160">총소유 비용을 낮게 / 유지 관리</span><span class="sxs-lookup"><span data-stu-id="032ce-160">Low total cost of ownership / maintenance</span></span>  <br/> |<span data-ttu-id="032ce-161">총소유 비용 감소 높은 / 유지 관리</span><span class="sxs-lookup"><span data-stu-id="032ce-161">High total cost of ownership / maintenance</span></span>  <br/> |
   
<span data-ttu-id="032ce-p111">Office 365로 마이그레이션하는 경우에 일회성 이동 하는 데이터를 구성 하 고 클라우드에서 항목과 뒤에 그대로 두려면 기능을 결정 하는 동안 사전, 과도 한 비용에 해야 합니다. 그러나 업그레이드 시점부터 자동 됩니다, 그리고 하드웨어 및 소프트웨어 업데이트를 관리 해야하는 더 이상 및 Microsoft 서비스 수준 계약 ([SLA](https://go.microsoft.com/fwlink/?linkid=843153)) 하 여 팜의 가동은 백업 합니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-p111">When you migrate to Office 365, the one-time move will have a heavier cost up-front, while you're organizing data and deciding what to take to the cloud and what to leave behind. However, upgrades will be automatic from that point, you will no longer need to manage hardware and software updates, and the up-time of your farm will be backed by a Microsoft Service Level Agreement ([SLA](https://go.microsoft.com/fwlink/?linkid=843153)).</span></span>
  
### <a name="migrate-to-sharepoint-online"></a><span data-ttu-id="032ce-164">SharePoint Online으로 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="032ce-164">Migrate to SharePoint Online</span></span>

<span data-ttu-id="032ce-p112">SharePoint Online에 연결 된 서비스 설명을 검토 하 여 필요한 모든 기능이 있는지 확인 합니다. 다음은 모든 Office 365 서비스 설명에 대 한 링크가입니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-p112">Make sure that SharePoint Online has all the features you need by reviewing the associated service description. Here's the link to all Office 365 Service Descriptions:</span></span>
  
[<span data-ttu-id="032ce-167">Office 365 서비스 설명</span><span class="sxs-lookup"><span data-stu-id="032ce-167">Office 365 Service Descriptions</span></span>](https://go.microsoft.com/fwlink/?linkid=272060)
  
<span data-ttu-id="032ce-p113">SharePoint online, SharePoint 2007에서 마이그레이션할 직접 방법은 없습니다. 이전 SharePoint Online을 수동으로 수행 합니다. SharePoint Server 2013 또는 SharePoint 서버 2016를 업그레이드 하는 경우 이동 하려는 SharePoint 마이그레이션 API를 사용 하 여 (하는 경우 예, 비즈니스용 OneDrive에 대 한 정보를 마이그레이션할) 작업도 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-p113">There is no direct way to migrate from SharePoint 2007 to SharePoint Online; your move to SharePoint Online would be done manually. If you upgrade to SharePoint Server 2013 or SharePoint Server 2016, your move might also involve using the SharePoint Migration API (to migrate information into OneDrive for Business, for example).</span></span>
  
|<span data-ttu-id="032ce-170">**온라인 Pro**</span><span class="sxs-lookup"><span data-stu-id="032ce-170">**Online Pro**</span></span>|<span data-ttu-id="032ce-171">**온라인 사기**</span><span class="sxs-lookup"><span data-stu-id="032ce-171">**Online Con**</span></span>|
|:-----|:-----|
|<span data-ttu-id="032ce-172">Microsoft는 SPO 하드웨어 및 모든 하드웨어 관리를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-172">Microsoft supplies SPO hardware and all hardware administration.</span></span>  <br/> |<span data-ttu-id="032ce-173">사용할 수 있는 기능을 SharePoint Server 온-프레미스 및 SPO 달라질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-173">Available features may be different between SharePoint Server on-premises and SPO.</span></span>  <br/> |
|<span data-ttu-id="032ce-174">구독 라이선스를의 전역 관리자 여야 하 고 SPO 사이트에 관리자를 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-174">You are the global administrator of your subscription, and may assign administrators to SPO sites.</span></span>  <br/> |<span data-ttu-id="032ce-175">존재 하지 않는 (또는 필요 하지 않은) 온-프레미스 SharePoint 서버에서 팜 관리자를 사용 하 여 사용할 수 있는 일부 작업 Office 365의 SharePoint 관리자 역할에 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-175">Some actions available to a Farm Administrator in SharePoint Server on-premises do not exist (or are not necessary) included in the SharePoint Administrator role in Office 365.</span></span>  <br/> |
|<span data-ttu-id="032ce-176">메뉴 및 도구 모음을 Microsoft 패치 적용 수정 기본 하드웨어 및 소프트웨어를 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-176">Microsoft applies patches, fixes and updates to underlying hardware and software.</span></span>  <br/> |<span data-ttu-id="032ce-177">서비스의 내부 파일 시스템에 액세스할 수 없습니다 이기 때문에 일부 사용자 지정 제한 됩니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-177">Because there is no access to the underlying file system in the service, some customizations are limited.</span></span>  <br/> |
|<span data-ttu-id="032ce-178">Microsoft는 [서비스 수준 계약](https://go.microsoft.com/fwlink/?linkid=843153) 에 게시 하 고 서비스 수준 보안 문제를 해결 하려면 신속 하 게 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-178">Microsoft publishes [Service Level Agreements](https://go.microsoft.com/fwlink/?linkid=843153) and moves quickly to resolve service level incidents.</span></span>  <br/> |<span data-ttu-id="032ce-179">SharePoint Online에서 서비스에 의해 백업, 복원 및 기타 복구 옵션은 자동화-백업을 사용 하지 않으면 덮어쓰게 되어 합니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-179">Backup and restore and other recovery options are automated by the service in SharePoint Online - backups are overwritten if not used.</span></span>  <br/> |
|<span data-ttu-id="032ce-180">보안 테스트 및 서버 성능 조정 되는 서비스에 지속적으로에 의해 수행 되 Microsoft 합니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-180">Security testing and server performance tuning are carried out on an ongoing basis in the service by Microsoft.</span></span>  <br/> |<span data-ttu-id="032ce-181">사용자 인터페이스 및 기타 SharePoint 기능 서비스에 의해 설치 되 고 설정 또는 해제 상태를 전환할 수 해야할 수로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-181">Changes to the user interface and other SharePoint features are installed by the service and may need to be toggled on or off.</span></span>  <br/> |
|<span data-ttu-id="032ce-182">많은 산업 표준을 충족 하는 office 365: [Office 365 규정 준수](https://go.microsoft.com/fwlink/?linkid=843165)합니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-182">Office 365 meets many industry standards: [Office 365 Compliance](https://go.microsoft.com/fwlink/?linkid=843165).</span></span>  <br/> |<span data-ttu-id="032ce-183">마이그레이션에 대 한 [FastTrack](https://go.microsoft.com/fwlink/?linkid=518597) 지원 제한 됩니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-183">[FastTrack](https://go.microsoft.com/fwlink/?linkid=518597) assistance for migration is limited.</span></span>  <br/> <span data-ttu-id="032ce-184">업그레이드의 대부분이 수동, 됩니다 또는 SPO 마이그레이션 API를 통해 [SharePoint Online 및 OneDrive 마이그레이션에 대 한 콘텐츠 로드맵](https://go.microsoft.com/fwlink/?linkid=843184)설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-184">Much of the upgrade will be manual, or via the SPO Migration API described in the [SharePoint Online and OneDrive Migration Content Roadmap](https://go.microsoft.com/fwlink/?linkid=843184).</span></span>  <br/> |
|<span data-ttu-id="032ce-185">Microsoft 기술 지원 엔지니어 아니고 직원 데이터 센터에서 관리에 무제한 액세스할 구독 합니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-185">Neither Microsoft Support Engineers nor employees in the datacenter have unrestricted admin access to your subscription.</span></span>  <br/> |<span data-ttu-id="032ce-186">하드웨어 인프라의 SharePoint, 최신 버전을 지원 하도록 업그레이드 해야하는 경우 또는 보조 팜 업그레이드를 위해 필요한 경우에 추가 비용 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-186">There can be additional costs if hardware infrastructure needs to be upgraded to support the newer version of SharePoint, or if a secondary farm is required for upgrade.</span></span>  <br/> |
|<span data-ttu-id="032ce-187">파트너는 SharePoint Online으로 데이터를 마이그레이션하는 일회성 작업 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-187">Partners can assist with the one-time job of migrating your data to SharePoint Online.</span></span>  <br/> ||
|<span data-ttu-id="032ce-188">온라인 제품 기능 사용 중지 될 수 있습니다, 경우에 true이 없는 지원 종료 누구나 서비스 간에 자동으로 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-188">Online products are updated automatically across the service meaning that though features may deprecate, there is no true end of support.</span></span>  <br/> ||
   
<span data-ttu-id="032ce-189">했을 때 새 Office 365 사이트를 만들 하기로 결정 하 고 수동으로 데이터 마이그레이션을 하 여 필요한 경우에 여기에 Office 365 옵션 오른쪽에 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-189">If you've decided to create a new Office 365 site, and will manually migrate data to it as is needed, you can look at your Office 365 options right here:</span></span>
  
[<span data-ttu-id="032ce-190">Office 365 계획 옵션</span><span class="sxs-lookup"><span data-stu-id="032ce-190">Office 365 Plan Options</span></span>](https://go.microsoft.com/fwlink/?linkid=843151)
  
### <a name="upgrade-sharepoint-server-on-premises"></a><span data-ttu-id="032ce-191">업그레이드 SharePoint Server 온-프레미스</span><span class="sxs-lookup"><span data-stu-id="032ce-191">Upgrade SharePoint Server on-premises</span></span>

<span data-ttu-id="032ce-p114">SharePoint Server 2016 릴리스 이후로 개수에 SharePoint 업그레이드의 버전을 건너뛸 수 없으므로 획기적인 방법이 있습니다. 즉, 업그레이드 연속적으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-p114">There is historically no way to skip versions in SharePoint Upgrades, at least not as of the release of SharePoint Server 2016. That means upgrades go serially:</span></span>
  
|||
|:-----|:-----|
||<span data-ttu-id="032ce-194">SharePoint 2007</span><span class="sxs-lookup"><span data-stu-id="032ce-194">SharePoint 2007</span></span> | <span data-ttu-id="032ce-195">SharePoint Server 2010</span><span class="sxs-lookup"><span data-stu-id="032ce-195">SharePoint Server 2010</span></span> | <span data-ttu-id="032ce-196">SharePoint Server 2013</span><span class="sxs-lookup"><span data-stu-id="032ce-196">SharePoint Server 2013</span></span> | <span data-ttu-id="032ce-197">SharePoint Server 2016</span><span class="sxs-lookup"><span data-stu-id="032ce-197">SharePoint Server 2016</span></span> |
   
<span data-ttu-id="032ce-p115">SharePoint 2007에서의 전체 경로 적용할 SharePoint Server 2016 시간의 많은 투자는 것을 의미 하 고 포함 되는 업그레이드 된 하드웨어 (SQL server 업그레이드도 해야 인식 수)의 관점에서 비용, 소프트웨어 및 관리 합니다. 사용자 지정 내용 업그레이드 하거나 기능의 중요도 따라 중단할 수 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-p115">To take the entire path from SharePoint 2007 to SharePoint Server 2016 will mean a significant investment of time and will involve a cost in terms of upgraded hardware (be aware that SQL servers must also be upgraded), software, and administration. Customizations will need to be upgraded or abandoned, according to the criticality of the feature.</span></span>
  
> [!NOTE]
> <span data-ttu-id="032ce-p116">수명 종료 SharePoint 2007 팜을 유지 관리, SharePoint Server 2016 팜 (-나란히를 실행 하는 별도 팜) 있으므로 새 하드웨어에 설치 하 고 다음 계획 하 고 실행 관련 콘텐츠 (다운로드 하 고 다시에 대 한 콘텐츠를 업로드의 수동 마이그레이션 수 예:)입니다. (예: 마지막 수정 된 계정 수동 이동을 수행 하는 계정의 별칭을 가진 교체 하는 문서 이동), 수동 이동 하 고 (예: 사이트, 하위 사이트, 사용 권한 및 목록 다시 만드는 시간 보다 먼저 수행 해야 하는 작업의 주의 사항이 중 일부를 인식 구조)입니다. 다시, 저장소, 또는 더이상 필요, 마이그레이션의 영향을 줄일 수 있는 동작으로 이동할 수 있는 데이터를 고려 하는 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-p116">It's possible to maintain your end-of-life SharePoint 2007 farm, install a SharePoint Server 2016 farm on new hardware (so the separate farms run side-by-side), and then plan and execute a manual migration of content (for downloading and re-uploading content, for example). Be aware of some of the gotchas of manual moves (such as moves of documents replacing the last modified account with the alias of the account doing the manual move), and the work that must be done ahead of time (such as recreating sites, sub-sites, permissions and list structures). Again, this is the time to consider what data you can move into storage, or no longer need, an action that can reduce the impact of migration.</span></span>
  
<span data-ttu-id="032ce-p117">두 방법 모두 사용자의 환경 사전 업그레이드를 정리 합니다. 기존 팜을 업그레이드 하기 전에 기능적 이며 해제 하기 전에 (확인)에 특정 수!</span><span class="sxs-lookup"><span data-stu-id="032ce-p117">Either way, clean your environment prior to upgrade. Be certain your existing farm is functional before you upgrade, and (for sure) before you decommission!</span></span> 
  
<span data-ttu-id="032ce-205">**지원 되는 항목과 지원 되지않는 업그레이드 경로**검토 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-205">Remember to review the **supported and unsupported upgrade paths**:</span></span> 
  
- <span data-ttu-id="032ce-206">
  [SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843156)</span><span class="sxs-lookup"><span data-stu-id="032ce-206">[SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843156)</span></span>
    
- [<span data-ttu-id="032ce-207">SharePoint Server 2010</span><span class="sxs-lookup"><span data-stu-id="032ce-207">SharePoint Server 2010</span></span>](https://go.microsoft.com/fwlink/?linkid=843156)
    
- [<span data-ttu-id="032ce-208">SharePoint Server 2013</span><span class="sxs-lookup"><span data-stu-id="032ce-208">SharePoint Server 2013</span></span>](https://go.microsoft.com/fwlink/?linkid=843157)
    
<span data-ttu-id="032ce-209">**사용자 지정**을 사용 하는 경우에 중요 한 계획을 각 단계에 대 한 업그레이드에에서 있으면 마이그레이션 경로:</span><span class="sxs-lookup"><span data-stu-id="032ce-209">If you have **customizations**, it's critical you have a plan your upgrade for each step in the migration path:</span></span> 
  
- [<span data-ttu-id="032ce-210">SharePoint 2007</span><span class="sxs-lookup"><span data-stu-id="032ce-210">SharePoint 2007</span></span>](https://go.microsoft.com/fwlink/?linkid=843158)
    
- [<span data-ttu-id="032ce-211">SharePoint Server 2010</span><span class="sxs-lookup"><span data-stu-id="032ce-211">SharePoint Server 2010</span></span>](https://go.microsoft.com/fwlink/?linkid=843160)
    
- [<span data-ttu-id="032ce-212">SharePoint Server 2013</span><span class="sxs-lookup"><span data-stu-id="032ce-212">SharePoint Server 2013</span></span>](https://go.microsoft.com/fwlink/?linkid=843162)
    
|<span data-ttu-id="032ce-213">**온-프레미스 Pro**</span><span class="sxs-lookup"><span data-stu-id="032ce-213">**On-premises Pro**</span></span>|<span data-ttu-id="032ce-214">**온-프레미스 사기**</span><span class="sxs-lookup"><span data-stu-id="032ce-214">**On-premises Con**</span></span>|
|:-----|:-----|
|<span data-ttu-id="032ce-215">모든 측면을 서버 하드웨어에서 SharePoint 팜의 모든 권한입니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-215">Full control of all aspects of your SharePoint Farm, from the server hardware up.</span></span>  <br/> |<span data-ttu-id="032ce-216">모든 나누기 및 픽스는 (수 참여할 유료 Microsoft 고객 지원 제품 지원의 끝에 없는 경우) 회사의 책임.</span><span class="sxs-lookup"><span data-stu-id="032ce-216">All breaks and fixes are the responsibility of your company (can engage paid Microsoft Support if your product is not at end of support):</span></span>  <br/> |
|<span data-ttu-id="032ce-217">SharePoint Server의 전체 기능 집합 사용 온-프레미스 하이브리드를 통해 SharePoint Online 구독을 온-프레미스 팜에 연결 하는 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-217">Full feature set of SharePoint Server on-premises with the option to connect your on-premises farm to a SharePoint Online subscription via hybrid.</span></span>  <br/> |<span data-ttu-id="032ce-218">업그레이드, 패치, 보안 픽스 및 SharePoint Server의 모든 유지 관리 온-프레미스를 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-218">Upgrade, patches, security fixes, and all maintenance of SharePoint Server managed on-premises.</span></span>  <br/> |
|<span data-ttu-id="032ce-219">더 많은 사용자 지정에 대 한 전체 액세스 합니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-219">Full access for greater customization.</span></span>  <br/> |<span data-ttu-id="032ce-220">[Office 365에서 지원 되는 준수 표준](https://go.microsoft.com/fwlink/?linkid=843165) 수동으로 구성 된 온-프레미스 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-220">[Compliance standards supported by Office 365](https://go.microsoft.com/fwlink/?linkid=843165) must be manually configured on-premises.</span></span>  <br/> |
|<span data-ttu-id="032ce-221">보안 테스트 하 고 서버 성능 튜닝, 귀하의 구내에서 수행 (제어는).</span><span class="sxs-lookup"><span data-stu-id="032ce-221">Security testing, and server performance tuning, carried out on your premises (is under your control).</span></span>  <br/> |<span data-ttu-id="032ce-222">Office 365 수 기능을 사용할 수 있도록 SharePoint Online는 SharePoint Server 온-프레미스와 상호 운용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-222">Office 365 may make features available to SharePoint Online that do not interoperate with SharePoint Server on-premises</span></span>  <br/> |
|<span data-ttu-id="032ce-223">파트너는 마이그레이션에 도움이 되는 다음 버전의 SharePoint Server (이상)에 대 한 데이터만 합니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-223">Partners can assist with migrating data to the next version of SharePoint Server (and beyond).</span></span>  <br/> |<span data-ttu-id="032ce-224">SharePoint Online에서 표시 된 대로 SharePoint Server 사이트 [SSL/TLS](https://go.microsoft.com/fwlink/?linkid=843167) 인증서를 자동으로 사용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-224">Your SharePoint Server sites will not automatically use [SSL/TLS](https://go.microsoft.com/fwlink/?linkid=843167) certificates as is seen in SharePoint Online.</span></span>  <br/> |
|<span data-ttu-id="032ce-225">명명 규칙, 백업, 복원 및 SharePoint Server 온-프레미스에서 다른 복구 옵션의 전체 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-225">Full control of naming conventions, backup and restore and other recovery options in SharePoint Server on-premises.</span></span>  <br/> |<span data-ttu-id="032ce-226">SharePoint Server 온-프레미스 제품 수명 주기를 중요 한입니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-226">SharePoint Server on-premises is sensitive to product lifecycles.</span></span>  <br/> |
   
### <a name="upgrade-resources"></a><span data-ttu-id="032ce-227">업그레이드 리소스</span><span class="sxs-lookup"><span data-stu-id="032ce-227">Upgrade Resources</span></span>

<span data-ttu-id="032ce-228">하드웨어 및 소프트웨어 요구 사항을 충족 다음에 따라 있습니다 알고 있으면 시작 업그레이드 방법을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-228">Begin by knowing that you meet hardware and software requirements, then follow supported upgrade methods.</span></span>
  
- <span data-ttu-id="032ce-229">**하드웨어/소프트웨어 요구 사항**:</span><span class="sxs-lookup"><span data-stu-id="032ce-229">**Hardware/software requirements for**:</span></span> 
    
    <span data-ttu-id="032ce-230">[SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204) | [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843206) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843207)</span><span class="sxs-lookup"><span data-stu-id="032ce-230">[SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204) | [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843206) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843207)</span></span>
    
- <span data-ttu-id="032ce-231">**소프트웨어 경계 및 제한 사항**:</span><span class="sxs-lookup"><span data-stu-id="032ce-231">**Software boundaries and limits for**:</span></span> 
    
    <span data-ttu-id="032ce-232">[SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843245) | [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843247) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843248) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843249)</span><span class="sxs-lookup"><span data-stu-id="032ce-232">[SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843245) | [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843247) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843248) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843249)</span></span>
    
- <span data-ttu-id="032ce-233">**대 한 업그레이드 프로세스 개요**:</span><span class="sxs-lookup"><span data-stu-id="032ce-233">**The upgrade process overview for**:</span></span> 
    
    <span data-ttu-id="032ce-234">[SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843250) | [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843251) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843252) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843359)</span><span class="sxs-lookup"><span data-stu-id="032ce-234">[SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843250) | [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843251) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843252) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843359)</span></span>
    
### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-on-premises"></a><span data-ttu-id="032ce-235">SharePoint Online 및 온-프레미스 간의 SharePoint 하이브리드 솔루션 만들기</span><span class="sxs-lookup"><span data-stu-id="032ce-235">Create a SharePoint hybrid solution between SharePoint Online and on-premises</span></span>

<span data-ttu-id="032ce-p118">마이그레이션 요구 사항에 대 한 대답 온-프레미스, 및 SharePoint Online에서 제공 하는 총소유 더 낮은 비용으로 제공 둔 간의 곳 이면 통해 연결할 수 있습니다 2016 팜 또는 SharePoint Server 2013 SharePoint online, 하이브리드 합니다. [SharePoint 하이브리드 솔루션에 대 한 설명](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx)</span><span class="sxs-lookup"><span data-stu-id="032ce-p118">If the answer to your migration needs is somewhere between the self-control offered by on-premises, and the lower cost of ownership offered by SharePoint Online, you can connect SharePoint Server 2013 or 2016 farms to SharePoint Online, through hybrids. [Learn about SharePoint hybrid solutions](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx)</span></span>
  
<span data-ttu-id="032ce-238">하이브리드 SharePoint 서버 팜에서 비즈니스 이점이 있는지를 결정 한 경우 숙지 하이브리드 및 온-프레미스 SharePoint 팜과 Office 365 구독 간의 연결을 구성 하는 방법의 기존 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-238">If you decide that a hybrid SharePoint Server farm will benefit your business, familiarize yourself with the existing types of hybrid and how to configure the connection between your on-premises SharePoint farm and your Office 365 subscription.</span></span>
  
<span data-ttu-id="032ce-p119">하나의 좋은 방법은이 작동 하는 방법을 확인 하는 [Office 365 개발/테스트 환경](https://go.microsoft.com/fwlink/?linkid=843152)만들기 (영문)입니다. 평가판 했거나을 Office 365 구독을 구매한 거 야 쉽게 후 데이터를 마이그레이션할 수 있는 SharePoint Online에서 사이트 모음, 웹, 및 문서 라이브러리를 만드는 (중 하나를 수동으로으로 사용 하 여 마이그레이션 API의 또는-마이그레이션할 경우 내 사이트 콘텐츠-비즈니스용 OneDrive를 하이브리드 마법사를 통해).</span><span class="sxs-lookup"><span data-stu-id="032ce-p119">One good way to see how this works is by creating an [Office 365 dev/test environment](https://go.microsoft.com/fwlink/?linkid=843152). Once you have a trial or purchased Office 365 subscription, you'll be on your way to creating the site collections, webs, and document libraries in SharePoint Online to which you can migrate data (either manually, by use of the Migration API, or - if you want to migrate My Site content to OneDrive for Business - through the hybrid wizard).</span></span>
  
> [!NOTE]
> <span data-ttu-id="032ce-241">SharePoint 2007 팜을 업그레이드할 수 해야 합니다 기억 온-프레미스, SharePoint Server 2013 또는 SharePoint Server 2016 하이브리드 옵션을 사용 하려면</span><span class="sxs-lookup"><span data-stu-id="032ce-241">Remember that your SharePoint 2007 farm will need to be upgraded, on-premises, to either SharePoint Server 2013 or SharePoint Server 2016 to use the hybrid option</span></span> 
  
## <a name="related-topics"></a><span data-ttu-id="032ce-242">관련 항목</span><span class="sxs-lookup"><span data-stu-id="032ce-242">Related topics</span></span>

[<span data-ttu-id="032ce-243">문제를 해결 하 고 업그레이드 (Office SharePoint Server 2007)를 다시 시작</span><span class="sxs-lookup"><span data-stu-id="032ce-243">Troubleshoot and resume upgrade (Office SharePoint Server 2007)</span></span>](https://go.microsoft.com/fwlink/?linkid=843192)
  
[<span data-ttu-id="032ce-244">업그레이드 문제해결 (SharePoint Server 2010)</span><span class="sxs-lookup"><span data-stu-id="032ce-244">Troubleshoot upgrade issues (SharePoint Server 2010)</span></span>](https://go.microsoft.com/fwlink/?linkid=843194)
  
[<span data-ttu-id="032ce-245">SharePoint 2013에서 데이터베이스 업그레이드 문제 해결</span><span class="sxs-lookup"><span data-stu-id="032ce-245">Troubleshoot database upgrade issues in SharePoint 2013</span></span>](https://go.microsoft.com/fwlink/?linkid=843195)
  
[<span data-ttu-id="032ce-246">업그레이드를 위해 Microsoft 파트너에 대 한 검색</span><span class="sxs-lookup"><span data-stu-id="032ce-246">Search for Microsoft Partners to help with Upgrade</span></span>](https://go.microsoft.com/fwlink/?linkid=841249)
  
[<span data-ttu-id="032ce-247">2007 서버와 클라이언트에서 Office를 업그레이드 하는데 도움이 되는 리소스</span><span class="sxs-lookup"><span data-stu-id="032ce-247">Resources to help you upgrade from Office 2007 servers and clients</span></span>](upgrade-from-office-2007-servers-and-products.md)
  

