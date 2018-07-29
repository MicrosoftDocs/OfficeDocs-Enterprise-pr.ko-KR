---
title: SharePoint 2007 마이그레이션 옵션을 고려해 야
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 1/31/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- MET150
- SPS150
- OSU140
- SPO160
- SPB160
- OSI150
- OSI160
- BSA160
- OSU160
ms.assetid: 66325a43-5816-4f8e-81ba-c11b71345b7c
description: SharePoint Server 2007에는 지원의 끝에 도달 했습니다 이며 업그레이드 하는 시간입니다. 이 문서를 사용 하 여 계획을 수립 하는 데 도움이 됩니다.
ms.openlocfilehash: 4395bc330efd97ae8865e0fb75f93f04fd162ecd
ms.sourcegitcommit: a9c84d02e94c99ff6b1099b4a9ae695be08210e2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/25/2018
ms.locfileid: "21169880"
---
# <a name="sharepoint-2007-migration-options-to-consider"></a><span data-ttu-id="0a6f1-104">SharePoint 2007 마이그레이션 옵션을 고려해 야</span><span class="sxs-lookup"><span data-stu-id="0a6f1-104">SharePoint 2007 migration options to consider</span></span>

<span data-ttu-id="0a6f1-p102">Microsoft SharePoint 2007과 SharePoint Server 2007 지원의 끝에 도달 했습니다. 업그레이드 하는! 이 문서에서는 사용자가 마이그레이션 옵션에 대 한 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f1-p102">Microsoft SharePoint 2007 and SharePoint Server 2007 have reached end of support. It's time to upgrade! This article provides information about your migration options.</span></span>
  
## <a name="common-upgrade-strategies-for-sharepoint"></a><span data-ttu-id="0a6f1-108">SharePoint에 대 한 일반적인 업그레이드 전략</span><span class="sxs-lookup"><span data-stu-id="0a6f1-108">Common upgrade strategies for SharePoint</span></span>

<span data-ttu-id="0a6f1-p103">SharePoint Server 환경을 업그레이드 하는 방법은 여러 가지가 있습니다. Microsoft Office SharePoint Server 2007 팜이 있는 경우 업그레이드 방법에 대 한 예가 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f1-p103">There are multiple methods to upgrade a SharePoint Server environment. If you have a Microsoft Office SharePoint Server 2007 farm, here are some examples of the upgrade methods:</span></span>
  
- <span data-ttu-id="0a6f1-111">데이터베이스 연결</span><span class="sxs-lookup"><span data-stu-id="0a6f1-111">Database attach</span></span>
    
- <span data-ttu-id="0a6f1-112">수평적으로 업그레이드</span><span class="sxs-lookup"><span data-stu-id="0a6f1-112">Side-by-side upgrade</span></span>
    
- <span data-ttu-id="0a6f1-113">전체 업그레이드</span><span class="sxs-lookup"><span data-stu-id="0a6f1-113">In-place upgrade</span></span>
    
- <span data-ttu-id="0a6f1-114">혼합 업그레이드 (분리 된 데이터베이스를 사용한 전체 / 별도 데이터베이스 연결)</span><span class="sxs-lookup"><span data-stu-id="0a6f1-114">Hybrid upgrade (in-place with detached databases / separate database attach)</span></span>
    
- <span data-ttu-id="0a6f1-115">SharePoint 하이브리드 (온-프레미스 sharepoint online 연결)</span><span class="sxs-lookup"><span data-stu-id="0a6f1-115">SharePoint hybrids (connect online to on-premises SharePoint)</span></span>
    
- <span data-ttu-id="0a6f1-116">사이트 모음 또는 라이브러리 간에 데이터를 수동으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f1-116">Manually move data between site collections or libraries</span></span>
    
- <span data-ttu-id="0a6f1-117">Office 365 ([SharePoint Online 배포 관리자](https://aka.ms/spoguidance))에 FastTrack 마법사 업그레이드</span><span class="sxs-lookup"><span data-stu-id="0a6f1-117">FastTrack Wizard upgrade to Office 365 ([SharePoint Online deployment advisor](https://aka.ms/spoguidance))</span></span>
    
- <span data-ttu-id="0a6f1-118">SharePoint Online (SPO) Office 365의에서 마이그레이션 API</span><span class="sxs-lookup"><span data-stu-id="0a6f1-118">Migration API to SharePoint Online (SPO) in Office 365</span></span>
    
<span data-ttu-id="0a6f1-119">어떤 적합 한?</span><span class="sxs-lookup"><span data-stu-id="0a6f1-119">What works best for you?</span></span>
  
<span data-ttu-id="0a6f1-p104">팜의 않습니다 및에 대 한 사용에 대 한 지식이 전략적 강도 때 업그레이드를 제공 합니다. 사용자는 SharePoint 팜에서 사용 하는 방식을 사용자 옵션 중에서 선택할 수는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f1-p104">Your knowledge of what your farm does and is used for is a tactical strength when it comes to upgrade. The way people use the SharePoint Farm will help you choose from your options.</span></span>
  
> [!TIP]
> <span data-ttu-id="0a6f1-p105">Microsoft Office SharePoint Server 2007에는 또한 여기에서 설명 하지 점진적 업그레이드를가지고 있습니다. 단계별 업그레이드의 목록을 보려면 문서 [끝에 SharePoint Server 2007 지원 로드맵](sharepoint-2007-end-of-support.md)참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="0a6f1-p105">Microsoft Office SharePoint Server 2007 also has a gradual upgrade not covered here. To see a list of step-specific upgrade articles see the [SharePoint Server 2007 end of support Roadmap](sharepoint-2007-end-of-support.md).</span></span> 
  
<span data-ttu-id="0a6f1-p106">SharePoint 업그레이드 하는 경우의 모든 버전에 대 한 [제품 수명 주기](https://support.microsoft.com/en-us/lifecycle/search) 및 시스템 요구 사항을 확인 해야 합니다. 이 다음 업그레이드 해야 합니다 (예: 더 많은 업그레이드에 대 한 계획, 지원 날짜의 끝을 잘 알고 있어야 하는 SharePoint Server 2010과 같은 레거시 제품에서 일시 중지 하는 경우) 때 인식 수 있도록 계획을 지 원하는 하드웨어를 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f1-p106">Remember to check the [Product Lifecycle](https://support.microsoft.com/en-us/lifecycle/search) and System Requirements for whatever version of SharePoint you're upgrading to. This is so you'll be aware when the next upgrade will be necessary (for example, if you pause at a legacy product like SharePoint Server 2010 to plan for more upgrades, be sure you know its end of support date), and to be certain you have hardware that supports your plan.</span></span> 
  
<span data-ttu-id="0a6f1-p107">일부 또는 전부 SharePoint 사이트의 클라우드에서 Office 365로의 전환 하려면 계획 하는 경우 [Office 365 서비스 설명](https://technet.microsoft.com/en-us/library/office-365-service-descriptions.aspx)에 대 한 링크에 책갈피를 시간입니다. SharePoint Online 기능에 대해 자세히 알아보려면 서비스 설명 해야 하 고에서 다 수는 어떻게 온-프레미스 SharePoint Server 합니다. Microsoft Office SharePoint Server 2007 팜 기능을 업그레이드 합니다. 설치에 손상 된 사이트가 있으면 업그레이드 이전에 수정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f1-p107">If you're planning to transition some, or all, of your SharePoint sites to Office 365 in the Cloud, this is a time to bookmark a link to the [Service Descriptions for Office 365](https://technet.microsoft.com/en-us/library/office-365-service-descriptions.aspx). You'll need the Service Descriptions to learn about SharePoint Online features and how they might differ from on-premises SharePoint Server. Upgrade functional Microsoft Office SharePoint Server 2007 farms. If your installation has sites that are broken, fix them prior to upgrade.</span></span>
  
## <a name="a-note-about-managing-risk"></a><span data-ttu-id="0a6f1-130">위험을 관리 하는 방법에 대 한 메모</span><span class="sxs-lookup"><span data-stu-id="0a6f1-130">A note about managing risk</span></span>

<span data-ttu-id="0a6f1-p108">'--나란히 '와 같은 메서드는 업그레이드 논리의 구성표에 중요 합니다. 나란히를 업그레이드 하는 경우에 Microsoft Office SharePoint Server 2007 팜의 유지 관리 하지만 팜을 작성 다음 버전 (SharePoint Server 2010)에서 새 하드웨어에 합니다. 이 세가지 방법으로 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f1-p108">Methods like 'side-by-side' are important in the scheme of upgrade logic. When you upgrade side-by-side, you maintain your Microsoft Office SharePoint Server 2007 farm, but build a farm the next version up from it (SharePoint Server 2010) on new hardware. This helps in three ways:</span></span>
  
1. <span data-ttu-id="0a6f1-134">개별적으로 업그레이드, 데이터베이스를 사용 하 여 연결 하 여 Microsoft Office SharePoint Server 2007 데이터베이스의 백업을 수행할 수 있는 위치를 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f1-134">You have a place to take backups of your Microsoft Office SharePoint Server 2007 databases to upgrade them separately, by using database attach.</span></span>
    
2. <span data-ttu-id="0a6f1-135">소수의 중요 한 문서 라이브러리 및 기타 정보에는 Microsoft Office SharePoint Server 2007 팜에 사용에는 기 하는 경우 Microsoft Office SharePoint Server 2007에서 SharePoint Server 2010으로 데이터를 수동으로 이동 하도록 선택할 수 있습니다. 또는 특정 사이트 및 웹 구성 된 다음 버전 (작업을 손쉽게 수행할 수)를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f1-135">If you figure out that only a small number of critical document libraries and other information are in use on your Microsoft Office SharePoint Server 2007 farm, you can choose to manually move data from Microsoft Office SharePoint Server 2007 to SharePoint Server 2010, or take only specific sites and webs to the next version (which can make your job easier).</span></span>
    
3. <span data-ttu-id="0a6f1-136">Microsoft Office SharePoint Server 2007 서버 팜으로, 직접,는 안전 하 게 업그레이드를 팜 데이터를 포함 할 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f1-136">The less you do to the Microsoft Office SharePoint Server 2007 server farm, directly, the safer the data that farm contains as you upgrade.</span></span>
    
<span data-ttu-id="0a6f1-p109">전체 업그레이드와 같은 메서드 작동할 직접에 Microsoft Office SharePoint Server 2007 팜에 대 한 경로 포기 하 고 초기 환경으로 다시 시작을 쉽게 옵션 수가 감소 하 게 합니다. 가능한, 일부 보안 방식 (예: 라인으로 전환 하 고 원래 환경의 백업 테스트)을 작성 합니다. 예, Microsoft Office SharePoint Server 2007 팜 가상, 백업 및 복원의 목적을 위해 중복 될 경우를 백업한 후 하 고 업그레이드를 위한 서비스 윈도 대화 하기 전에 최신 데이터베이스를 복원 합니다. 백업 하지는 데이터베이스를 복원 하는 옵션 한다고 알면만 안전한 제공, 파악 하는 안심 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f1-p109">Methods like In-Place upgrade will act directly on your Microsoft Office SharePoint Server 2007 farm, giving you fewer easy options to abandon a path and begin again with your pristine environment. As much as possible, build in some safety measures (like taking and testing backups of the original environment). For example, if your Microsoft Office SharePoint Server 2007 farm is virtual, and is duplicated for the purposes of backup and restore, then back-up and restore the most current databases prior to your service window for the upgrade. Knowing that you have the option to restore database backups will not only give you a failsafe, it can give you peace of mind.</span></span>
  
> [!TIP]
> <span data-ttu-id="0a6f1-p110">업그레이드를 위한 모범 사례 문서 [Microsoft Office SharePoint Server 2007](https://technet.microsoft.com/en-us/library/cc261992%28v=office.12%29.aspx), [SharePoint Server 2010](https://technet.microsoft.com/en-us/library/cc261992%28v=office.14%29.aspx), [SharePoint Server 2013](https://technet.microsoft.com/en-us/library/cc261992%28v=office.15%29.aspx)및 [SharePoint Server 2016](https://technet.microsoft.com/en-us/library/cc261992%28v=office.16%29.aspx)존재합니다. 업그레이드 또는 Office 365 마이그레이션 경험을가지고 있는 [Microsoft 파트너](https://partnercenter.microsoft.com/en-us/pcv/search) 에 대 한 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f1-p110">Best practices documents for upgrade exist for [Microsoft Office SharePoint Server 2007](https://technet.microsoft.com/en-us/library/cc261992%28v=office.12%29.aspx), [SharePoint Server 2010](https://technet.microsoft.com/en-us/library/cc261992%28v=office.14%29.aspx), [SharePoint Server 2013](https://technet.microsoft.com/en-us/library/cc261992%28v=office.15%29.aspx), and [SharePoint Server 2016](https://technet.microsoft.com/en-us/library/cc261992%28v=office.16%29.aspx). You can also search for [Microsoft Partners](https://partnercenter.microsoft.com/en-us/pcv/search) who have experience with upgrades or Office 365 migrations.</span></span> 
  
## <a name="make-your-plan"></a><span data-ttu-id="0a6f1-143">계획 만들기</span><span class="sxs-lookup"><span data-stu-id="0a6f1-143">Make your plan</span></span>

<span data-ttu-id="0a6f1-p111">업그레이드 해야하는 경우는 계획 해야 하 고 이러한 경우에는 모든 1 크기에 맞게 하지 않습니다. 계획을 문서화할 'SharePoint Online을 사용 하 여 Office 365 구독을 만들기, 도메인을 등록 하 고 다음과 같은 파일을 저장 하는 사용자를 리디렉션할' 처럼 간단할 수 있습니다. 및 되지 않을 수 있습니다. 결정 사용자가 임의로, 아니며으로 기능 및 사용자에 게 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f1-p111">If you need to upgrade, you need a plan, and one-size doesn't fit all in these cases. Your plan may be as simple as 'Create an Office 365 subscription with SharePoint Online, register a domain, and redirect people to save their files there'. And it may not be. That decision is yours, and it's down to what you and your users really need.</span></span>
  
> [!NOTE]
> <span data-ttu-id="0a6f1-p112">것은 해당 수명 주기 끝난 소프트웨어를 실행 하려면 위험 합니다. 문제가 발견 되 면에서 지원 되는 제품에는 더이상 패치가 적용 됩니다. 즉, 새 보안 위협 발생 하는 경우 것 없는 보안 패치 또는 수정 프로그램 수명 주기의 끝에 포함 된 제품은 더이상 지원 되지 않으므로 합니다. 해당 상황이 발생 하지 않도록 하십시오!</span><span class="sxs-lookup"><span data-stu-id="0a6f1-p112">It's risky to run on software whose lifecycle has ended. Products that are out of support are no longer patched when issues are found. This also means that if new security threats arise, there will be no security patches or fixes because the end-of-lifecycle products are no longer supported. Please avoid that situation!</span></span> 
  
### <a name="first-know-your-farm"></a><span data-ttu-id="0a6f1-152">먼저, 팜의 알고 있습니다</span><span class="sxs-lookup"><span data-stu-id="0a6f1-152">First, know your farm</span></span>

<span data-ttu-id="0a6f1-p113">를 업그레이드 하는 경우 결정 된 사항을 기반으로 해야 조직에 대 한 사용자의 팜이 수행 하는 작업입니다. 어떤 요구를 충족 않는? 역할은 무엇입니까? 회사에서 각 팜에 다른 역할이 있을 수 있습니다. SharePoint 팜 중 일부 *중요 한* 못할 일부 파일 보관-보관에 대 한 있을 수 있습니다. 또는 팜의 한번에 여러 역할을 채우는, 하는 경우 다음 해야할 수 있습니다 어떤 사이트 모음, 웹, 또는 문서 라이브러리도 수행, 모든 사용자 지정 및 자신이 얼마나 중요 한지 확인 합니다. 이 수준에서 데이터를 분석 하는 다른 많은 작업 처럼 보이지만 시간과 노력 업그레이드 또는 마이그레이션 전에 도메인을 완벽 하 게 저장 하는 것이 있습니다. 모든 이동 파트와 가장 중요 한 비트 알면 하면 초과 한다면 했을 때 항목과 뒤에 남길 수 알 수 있습니다. 해당 기술만 둡니다 앞으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f1-p113">When upgrading, your decision-making should be based on what your farm does for your organization. What need does it satisfy? What's its role? Each farm in your company may have a different role. Some of your SharePoint farms may be  *critical*  , some may be file archives -- there for safe-keeping. Or, if your farm fills many roles at once, then you may need to know what site collections, webs, or even document libraries do, any customizations, and how important they are. Analyzing your data at this level may seem like a lot of work, but it saves time and effort to master your domain before you upgrade, or migrate, it. Once you know all the moving parts, and the most important bits, you'll also know what you've outgrown and can leave behind. That knowledge will only benefit you going forward.</span></span> 
  
<span data-ttu-id="0a6f1-162">따라서는 사용자가 말 SharePoint 서버 팜에 대 한 가장 중요 한?</span><span class="sxs-lookup"><span data-stu-id="0a6f1-162">So, what are users saying is most important about your SharePoint Server farm?</span></span>
  
- <span data-ttu-id="0a6f1-163">기본 제공 SharePoint 기능</span><span class="sxs-lookup"><span data-stu-id="0a6f1-163">Built-in SharePoint features</span></span>
    
- <span data-ttu-id="0a6f1-164">큰 데이터 모음 (예: 파일의 보관)</span><span class="sxs-lookup"><span data-stu-id="0a6f1-164">The large data corpus (such as an archive of files)</span></span>
    
- <span data-ttu-id="0a6f1-165">사용 가능</span><span class="sxs-lookup"><span data-stu-id="0a6f1-165">Availability</span></span>
    
- <span data-ttu-id="0a6f1-166">중요 한 앱, 웹 파트 또는 팜 (임무 중요 한 팜)에서 문서</span><span class="sxs-lookup"><span data-stu-id="0a6f1-166">Critical apps, web parts, or docs in the farm (Mission critical farm)</span></span>
    
- <span data-ttu-id="0a6f1-167">충족 준수 표준</span><span class="sxs-lookup"><span data-stu-id="0a6f1-167">The Compliance standards met</span></span>
    
- <span data-ttu-id="0a6f1-168">사용자 지정 기능</span><span class="sxs-lookup"><span data-stu-id="0a6f1-168">Customizations</span></span>
    
<span data-ttu-id="0a6f1-p114">SharePoint 팜에서 비즈니스에 필수적 무언가 실행 하는 경우 클라이언트 서비스 요구 사항에 대 한 중요 한 데이터의 큰 카탈로그 처럼 작동 하는 것, '중요 한 앱' 옆에 있는 눈금을 배치할 수 있지만 '가용성-', 즉 비즈니스 수도 라고 표시 잠시 자리를 SharePoint를 사용할 수 없 었 하는 경우의 영향을 받는 합니다. 마찬가지로,는 중요 한 기능을 제공 된 사용자 지정 코드, 사이트 정의 또는 함께 작동 하는 사용자 지정 숫자를 기반으로 하며 팜의 서비스 때문에 '사용자'를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f1-p114">If you run something essential to your business from your SharePoint farm, say it acts like a large catalog of critical data about client service requirements, you may put a tick beside 'Critical apps', but also 'Availability' -- that is, your business would be impacted if you couldn't use SharePoint for a while. Likewise, you might check 'Customizations' because the critical services your farm offers are based on custom code, site definitions, or a number of customizations that work together.</span></span>
  
<span data-ttu-id="0a6f1-p115">SharePoint는 소프트웨어에 기본 제공 이란를 사용 하 여 외부에서 아무 작업도 수행 하지 않아도 이러한 요구를 충족 하 고 일반적으로 업데이트 하 고 기본 관리 및 유지 관리 수행 하기 위해, ' 기본 제공 SharePoint'을 선택 했으면-수도 있습니다. 하는 경우 사용자 이전 버전의 SharePoint에서 전화에 대 한 설명입니다. 즉, 필요한 정보를 이미 수행 하 고 지원의 Microsoft Office SharePoint Server 2007 끝 이제에 업그레이드 하는 데 필요한 하지 않은 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f1-p115">If SharePoint met those needs without your having to do anything outside of using what's built-in to the software, and you generally update it and carry out normal administration and maintenance, you may have chosen 'Built-in SharePoint' -- this may also be your reason for sitting on an older version of SharePoint. In other words, it already does what you need it to and you haven't needed to upgrade until now, at Microsoft Office SharePoint Server 2007 end of support.</span></span>
  
<span data-ttu-id="0a6f1-p116">때 하면 글머리 기호 목록 업그레이드에 대 한 조건을 만들려면이 기능을 합니다. 즉,이 막대 것으로 간주를 충족 하기 위해 모든 업그레이드 해야 합니다. 현재 사용자의 요구에 맞지 않는 방법 발생 하지 않도록 하는 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f1-p116">When you bullet-list these things, you create criteria for your upgrade. In other words, any upgrade would have to meet this bar to be considered. This gives you a way to rule out methods that don't currently fit your needs.</span></span>
  
### <a name="a-simple-sample-plan"></a><span data-ttu-id="0a6f1-176">간단한 예제 계획</span><span class="sxs-lookup"><span data-stu-id="0a6f1-176">A simple sample plan</span></span>

<span data-ttu-id="0a6f1-p117">있습니다 리더와 넓을 합 및 다른 관리자가 SharePoint 업그레이드에 소요 되는 경로 할 수도 있습니다. SharePoint 서버 관리자는 종종 Microsoft SQL Server 관리자와 상호 운용 되어, 네트워킹 및 보안 팀 등을 사용 합니다. 이해 관계자에 게 많은 있는 계약을 구축 하거나 업그레이드 및 마이그레이션 계획을 조정 해야할 수 있습니다. 예, 회사의 일부 Office 365의 SharePoint Online 사용 하도록 데이터를 마이그레이션할 다음과 같은 가능성이 할 경우 성능 조정 또는 네트워크 내에 테스트 합니다. 사전에 영향을 받는 팀을 알려야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f1-p117">There may need to be wider consensus with leadership and other admins on the path your SharePoint Upgrade will take. SharePoint Server Administrators often cooperate with Microsoft SQL Server admins, work with Networking and Security teams, and more. Where there are a lot of stakeholders, you may need to build agreement for, or adjust, your upgrade and migration plan. For example, if you migrate data so that part of your company uses SharePoint Online in Office 365, there will likely need to be performance tuning or testing inside your network. Affected teams should be informed ahead of time.</span></span>
  
<span data-ttu-id="0a6f1-p118">내 간단한 예제에는 SharePoint 관리자의 제안 표시 하는 모든 이해 관계자에 게 합의 하는 전체 계획을 표시 합니다. 명확 하 게, 계약 및 결정 사항을 문서화 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f1-p118">In my simple sample, I show a SharePoint administrator's proposal and then list out the plan that all the stakeholders agreed upon. For clarity, document your agreements and decisions.</span></span>
  
<span data-ttu-id="0a6f1-p119">계획은 팜에 대 한 심도 깊은 분석 후에 시작 하 고 역할은 팜, 불만 사항 및 유도 일부 업그레이드 옵션 아래쪽으로 제한 하는 기타 중요 한 정보를 확인 하려고 시도 합니다. 나중에 업그레이드 제안 SharePoint 관리자에 의해 이루어집니다 및 이해 관계자에 게 작업 계획에 동의 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f1-p119">The plan starts after an in-depth analysis of a farm, and tries to identify the role of the farm, pain points, and other important information that will lead to narrowing down some upgrade options. Afterward, an upgrade proposal is made by SharePoint administrator, and stakeholders agree on an action plan.</span></span>
  
<span data-ttu-id="0a6f1-186">내 '가장 중요 한' 글머리 기호 목록:</span><span class="sxs-lookup"><span data-stu-id="0a6f1-186">My 'most important' bullet list:</span></span>
  
- <span data-ttu-id="0a6f1-187">가용성, SharePoint에 기본 제공 기능 및 규정 준수 표준입니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f1-187">Availability, features built-in to SharePoint, and Compliance standards.</span></span>
    
- <span data-ttu-id="0a6f1-188">대부분의 데이터는 하나의 모임 작업 영역에서에서 사용 되는 개발 팀이 특히 중요 하 여 여러 시간대에서 너무 많이 사용 하면 전세계와 3 개의 사이트 모음에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f1-188">Most of the data is on three site collections, with one Meeting Workspace used by a Dev team particularly important and in heavy use in multiple time-zones worldwide.</span></span>
    
- <span data-ttu-id="0a6f1-189">널리 사용 되는 다른 사이트 17 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f1-189">There are seventeen other sites that are widely used.</span></span>
    
- <span data-ttu-id="0a6f1-p120">두 문서 라이브러리 (모임 작업 영역 및 루트 사이트 모음에 있는 문서)은 가장 큰 (넘는 8000 문서 각). 많은 수의 보관 된 문서와 스프레드시트 첨부 파일을 사용 하 여 목록 했습니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f1-p120">Two document libraries (Meeting Workspace and Documents on the root site collection) are largest (over 8000 docs each). We have a large number of archived docs and list with spreadsheet attachments.</span></span>
    
- <span data-ttu-id="0a6f1-192">규정 준수에 유지 되어야 하는 중요 한 데이터가 포함 된 라이브러리 14 목록이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f1-192">There are fourteen lists of libraries that have sensitive data that MUST stay in Compliance.</span></span>
    
- <span data-ttu-id="0a6f1-193">우리는 어디서 든 보류 및 e-검색을 수행 하는 기능이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f1-193">We MUST have the ability to do holds and e-discovery wherever we go.</span></span>
    
- <span data-ttu-id="0a6f1-194">이 데이터 중 일부를 온-프레미스, 정보 보안 과도 규칙으로 인해 유지 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f1-194">Some of this data MUST stay on-premises, due to InfoSec rules.</span></span>
    
 <span data-ttu-id="0a6f1-195">**내 업그레이드 및 마이그레이션 선택 사항:**</span><span class="sxs-lookup"><span data-stu-id="0a6f1-195">**My upgrade and migration choices:**</span></span>
  
|||
|:-----|:-----|
|<span data-ttu-id="0a6f1-196">**예**</span><span class="sxs-lookup"><span data-stu-id="0a6f1-196">**Yes**</span></span> <br/> |<span data-ttu-id="0a6f1-197">**아니요**</span><span class="sxs-lookup"><span data-stu-id="0a6f1-197">**No**</span></span> <br/> |
|<span data-ttu-id="0a6f1-198">데이터베이스를 사용 하 여 업그레이드 데이터베이스 연결</span><span class="sxs-lookup"><span data-stu-id="0a6f1-198">Upgrade databases with database attach</span></span>  <br/> |<span data-ttu-id="0a6f1-199">전체 업그레이드</span><span class="sxs-lookup"><span data-stu-id="0a6f1-199">In-place upgrade</span></span>  <br/> |
|<span data-ttu-id="0a6f1-200">팜--나란히도 업그레이드</span><span class="sxs-lookup"><span data-stu-id="0a6f1-200">Upgrade with farms side-by-side</span></span>  <br/> |<span data-ttu-id="0a6f1-201">혼합 업그레이드</span><span class="sxs-lookup"><span data-stu-id="0a6f1-201">Hybrid Upgrade</span></span>  <br/> |
|<span data-ttu-id="0a6f1-202">마이그레이션 API Office 365의 SPO로 (개인 사이트 데이터)</span><span class="sxs-lookup"><span data-stu-id="0a6f1-202">Migration API to SPO in Office 365 (for personal site data)</span></span>  <br/> |<span data-ttu-id="0a6f1-203">SharePoint 하이브리드 (아직 필요 없음)</span><span class="sxs-lookup"><span data-stu-id="0a6f1-203">SharePoint Hybrid (not needed yet)</span></span>  <br/> |
|<span data-ttu-id="0a6f1-204">중요 한 데이터에 대 한 SharePoint online 일부 수동 데이터 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="0a6f1-204">Some manual data migrations to SharePoint Online for critical data</span></span>  <br/> |<span data-ttu-id="0a6f1-205">Office 365로 FastTrack 마법사 업그레이드</span><span class="sxs-lookup"><span data-stu-id="0a6f1-205">FastTrack wizard upgrade to Office 365</span></span>  <br/> |
   
 <span data-ttu-id="0a6f1-206">**내 제안 된 계획 합니다.**</span><span class="sxs-lookup"><span data-stu-id="0a6f1-206">**My proposed plan:**</span></span>
  
<span data-ttu-id="0a6f1-p121">업그레이드 온-프레미스, SharePoint--나란히, 가상화는 데이터베이스를 먼저 업그레이드할 수 있도록 일부의 버전입니다. SharePoint 2007에서 SharePoint 2010으로 이동 합니다. 테스트 결과 팜 관리자 및 트랜잭션당 합니다. 결과 팜을 테스트 하는 사용자입니다. 이 시간 동안 표시 중지 문제를 해결 합니다. 마찬가지로-나란히, 업그레이드 SharePoint 2010 데이터베이스를 SharePoint 2013 합니다. 파일럿/검정에 근거한 사용자 테스트 합니다. 이 시간 동안 표시 중지 문제를 해결 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f1-p121">Upgrade on-premises, with versions of SharePoint side-by-side, some virtualized, so that we can upgrade the databases first. Go from SharePoint 2007 to SharePoint 2010. Admins and Devs test the resulting farm. Users test the resulting farm. Fix any show-stopping issues during this time. Again, side-by-side, upgrade SharePoint 2010 databases to SharePoint 2013. Test. User test/pilot. Fix any show-stopping issues during this time.</span></span>
  
- <span data-ttu-id="0a6f1-216">SPO와 검색 페더레이션 하이브리드 요구를 충족 하는 경우 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f1-216">Consider if a Search Federated Hybrid with SPO meets your needs.</span></span>
    
- <span data-ttu-id="0a6f1-217">여기에서 SharePoint online 업그레이드 하려는 경우 [FastTrack 지원](https://fasttrack.microsoft.com) 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f1-217">Consider [FastTrack assistance](https://fasttrack.microsoft.com) if you would like to upgrade to SharePoint Online from here.</span></span> 
    
- <span data-ttu-id="0a6f1-p122">모든 사이트 모음에 Office 365 구독을 오프 로드할 수 하는 경우를 결정 합니다. (Office 365 많은 [준수 표준](https://technet.microsoft.com/library/office-365-compliance.aspx)을 충족 하는 데 사용 됩니다. Office 365 [eDiscovery](https://support.office.com/article/edea80d6-20a7-40fb-b8c4-5e8c8395f6da) 있으며 준수 센터를 통해 [을 포함 하 고](https://support.office.com/article/A18F8975-AA7F-43B4-A7D6-001D14744D8E) 작업을 수행할 수 있습니다.)</span><span class="sxs-lookup"><span data-stu-id="0a6f1-p122">Determine if any site collections can be offloaded to an Office 365 Subscription. (Office 365 meets many [Compliance standards](https://technet.microsoft.com/library/office-365-compliance.aspx). Office 365 has [eDiscovery](https://support.office.com/article/edea80d6-20a7-40fb-b8c4-5e8c8395f6da) and can do [Holds](https://support.office.com/article/A18F8975-AA7F-43B4-A7D6-001D14744D8E) through the Compliance Centre.)</span></span> 
    
<span data-ttu-id="0a6f1-221">그렇지 않은 경우 SharePoint Server 2016-나란히 업그레이드를 계속 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f1-221">Otherwise, continue with a side-by-side upgrade to SharePoint Server 2016.</span></span>
  
> [!NOTE]
> <span data-ttu-id="0a6f1-p123">업그레이드 및 실제 프로세스는 권장 사항을 계획 하는 관리자가 변경한 시점 업그레이드 의존 하는 다른 관련자와 발생 하는 대화는입니다. 등 경우가 종종 경제성 강제로 관리자가 자신의 계획을 변경할 수 있습니다. 모든 최종 결정은 합의 계획은 무엇을 문서화 해야 앞으로 이동 합니다. 형식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f1-p123">In between recommendations made by the administrators planning the upgrade and the actual process are the conversations that happen with other stakeholders on which the upgrade relies. For example, sometimes economics force administrators to change their plans. Whatever the final decision is, you should document what the agreed-upon plan is, going forward. It might look something like this:</span></span> 
  
 <span data-ttu-id="0a6f1-226">**내 작업 계획 합니다.**</span><span class="sxs-lookup"><span data-stu-id="0a6f1-226">**My action plan:**</span></span>
  
<span data-ttu-id="0a6f1-p124">온-프레미스, 기본 SharePoint Server 2010 및 2013을 구축 하는 가상 환경을 사용 합니다. SharePoint Server 2016 2016에 대 한 시스템 요구 사항에 맞는 새로운 하드웨어 기반으로 구축 됩니다. 수행 하기 위해 데이터베이스와 SharePoint 서버 2016 사이의 모든 버전을 통해 SharePoint 2007에서 데이터베이스를 업그레이드 하는 연결 합니다. 핵심 사용자 지정에 대 한 다시 하며 SharePoint 서버에서 2016 환경에서 테스트이 시간 네이티브 기능 요구 사항을 충족 이미 하지 하는 경우. 우리는 성공 하는 경우에 업그레이드 된 데이터베이스와 새 하드웨어에 온-프레미스 팜과 더 적은 수의 사용자 지정은이 갖습니다. SharePoint Server 2013, 테스트, 사용자 테스트/파일럿에서에서 새 사이트 모음을 업그레이드 된 콘텐츠 데이터베이스를 연결 하는 하 고을 수행 DNS 단독형 라이브 사용에 대 한 새 SharePoint 서버 2016 환경입니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f1-p124">On-premises, we use a virtual environment to build default SharePoint Server 2010, and 2013. SharePoint Server 2016 will be built on new hardware that meets system requirements for 2016. We will do database attaches to upgrade databases from SharePoint 2007 through all versions between it and SharePoint Server 2016. Core customizations are being recreated for and tested in the SharePoint Server 2016 environment at this time, if native features don't already meet our needs. If we are successful, we will have an on-premises farm on new hardware with upgraded databases, and fewer customizations. We'll attach the upgraded content databases to new site collections in SharePoint Server 2013, test, user test/pilot, and then do a DNS cut-over to the new SharePoint Server 2016 environment for live use.</span></span>
  
- <span data-ttu-id="0a6f1-233">고려 하지 않습니다 SharePoint Server 2016 및 SharePoint Online 간의 하이브리드 페더레이션 지금은 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f1-233">We will not consider Federated Hybrid between SharePoint Server 2016 and SharePoint Online right now.</span></span>
    
- <span data-ttu-id="0a6f1-p125">이 사이트의 예상된 35%는 베 니 티 도메인으로 구성 된 새 SPO 사이트를 설정 하거나 수, 궁극적으로, 비즈니스 저장소에 대 한 OneDrive 될 합니다. 사이트,으로 변환 하거나 새 사이트를 SPO로 라우팅할 수 있는 다른 기회를 찾고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f1-p125">An estimated 35% of our sites can be turned into new SPO sites with vanity domains, or, ultimately, become OneDrive for Business storage. Looking for other opportunities to convert sites, or route new sites to SPO.</span></span>
    
- <span data-ttu-id="0a6f1-236">이 부분에서는 마이그레이션 중 일부는 끌어서 놓기 OneDrive에 비즈니스 개인 사이트에 대 한 및 마이그레이션 API에 의해 일부 하 여 수동 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f1-236">Some of this part of the migration will be manual, by drag-and-drop to OneDrive for Business personal sites, and some by migration API.</span></span>
    
<span data-ttu-id="0a6f1-p126">자세한 단계, 또는 업그레이드에 표시 되는 특정 지침에 대 한 링크의 수를 계획을 따라야 합니다. MOSS 2007 컴퓨터를 해제할 수 해야, 및 비교;을 위해 가상 환경을 유지 해야 그러나 사용자가 SharePoint Server 2016 리디렉션됩니다 때 업그레이드는 완료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f1-p126">More detailed steps, or a number of links to specific upgrade directions should follow a plan. The MOSS 2007 computer should not be decommissioned, and virtual environments should be maintained for the sake of comparison; however, the upgrade will be complete when users are redirected to SharePoint Server 2016.</span></span>
  
<span data-ttu-id="0a6f1-p127">방법 선택에서 종종 주요 요소는 업그레이드의 총 비용 및 시간 (배웁니다이 대 한 추가 SharePoint 마이그레이션 로드맵 문서의) 비용입니다. 그러나 계획 차지 코드로 미리 차 됩니다 및 이점을 제공 하면 크게 알리기 신중 하 게 선택에서 어떤 성공 프레이밍은 다음과 유사 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f1-p127">Often major factors in choosing a method are the total cost of the upgrade and the cost in time (you'll see more on this in the SharePoint Migration Roadmap article). However, planning ahead will benefit you greatly in setting expectations, choosing wisely, and framing what success will look like.</span></span>
  
## <a name="related-links"></a><span data-ttu-id="0a6f1-241">관련 링크</span><span class="sxs-lookup"><span data-stu-id="0a6f1-241">Related links</span></span>

[<span data-ttu-id="0a6f1-242">2007 서버와 클라이언트에서 Office를 업그레이드 하는데 도움이 되는 리소스</span><span class="sxs-lookup"><span data-stu-id="0a6f1-242">Resources to help you upgrade from Office 2007 servers and clients</span></span>](upgrade-from-office-2007-servers-and-products.md)
  
[<span data-ttu-id="0a6f1-243">Microsoft 수명 주기 정책 및 수명 주기 검색</span><span class="sxs-lookup"><span data-stu-id="0a6f1-243">Microsoft Lifecycle Policy and Lifecycle search</span></span>](https://support.microsoft.com/en-us/lifecycle)
  
[<span data-ttu-id="0a6f1-244">마이그레이션 또는 업그레이드를 도와줄 수는 Microsoft 파트너에 대 한 검색</span><span class="sxs-lookup"><span data-stu-id="0a6f1-244">Search for Microsoft Partners who can help with upgrade or migration</span></span>](https://partnercenter.microsoft.com/en-us/pcv/search)
  

