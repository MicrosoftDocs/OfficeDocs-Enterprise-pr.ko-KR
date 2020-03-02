---
title: Office 365 Multi-Geo 계획
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
description: Office 365 Multi-Geo, 다중 위치 작동 방식 및 데이터 저장소에 사용할 수 있는 지리적 위치에 대해 알아봅니다.
ms.openlocfilehash: 2875f820b0ce1437a09289e3c5e660287b64dc40
ms.sourcegitcommit: 6ad59ab24a5dc8d27f448ca7fe4f6bdf7ab28066
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/27/2020
ms.locfileid: "42316007"
---
# <a name="plan-for-office-365-multi-geo"></a><span data-ttu-id="fb208-103">Office 365 Multi-Geo 계획</span><span class="sxs-lookup"><span data-stu-id="fb208-103">Plan for Office 365 Multi-Geo</span></span>

<span data-ttu-id="fb208-104">이 설명서는 데이터 상주 요구 사항을 충족해야 하는 회사 현재 상황에 따라 추가적인 지역으로 Office 365 테넌트를 확장하려고 준비하는 MNC(다국적 회사)의 관리자를 대상으로 작성되었습니다.</span><span class="sxs-lookup"><span data-stu-id="fb208-104">This guidance is designed for administrators of multi-national companies (MNCs) who are preparing their Office 365 tenant to be expanded to additional geographies in accordance with the company’s presence to meet data residency requirements.</span></span>

<span data-ttu-id="fb208-105">다중 지리적 구성에서 Office 365 테넌트는 중앙 위치와 하나 이상의 위성 위치로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="fb208-105">In a multi-geo configuration, your Office 365 tenant consists of a central location and one or more satellite locations.</span></span> <span data-ttu-id="fb208-106">이것은 여러 지리적 위치에 걸쳐 있는 단일 테넌트
입니다.</span><span class="sxs-lookup"><span data-stu-id="fb208-106">This is a single tenant that spans across multiple geo locations.</span></span> <span data-ttu-id="fb208-107">지리적 위치를 포함한 테넌트 정보는 Azure Active Directory(AAD)에서 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="fb208-107">Your tenant information, including geo locations, is mastered in Azure Active Directory (AAD).</span></span>

<span data-ttu-id="fb208-108">다음은 구성의 기본 개념을 이해하는 데 도움이 되는 몇 가지 핵심적인 다중 위치 용어입니다.</span><span class="sxs-lookup"><span data-stu-id="fb208-108">Here are some key multi-geo terms to help you understand the basic concepts of the configuration:</span></span>

-   <span data-ttu-id="fb208-109">**테넌트** – Office 365에서 일반적으로 하나 이상의 도메인에 연결되어 있는 조직을 나타내는 표현입니다(예: https://contoso.sharepoint.com).</span><span class="sxs-lookup"><span data-stu-id="fb208-109">**Tenant** – An organization's representation in Office 365 which typically has one or more domains associated with it (for example, https://contoso.sharepoint.com).</span></span> 

-   <span data-ttu-id="fb208-110">**지리적 위치** – Office 365 테넌트에서 데이터를 호스트하는 데 사용할 수 있는 지리적 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="fb208-110">**Geo locations** – The geographic locations available to host data in an Office 365 tenant.</span></span>

-   <span data-ttu-id="fb208-111">**위치 위성** - Office 365 테넌트에서 데이터를 호스팅하도록 구성된 추가 지리적 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="fb208-111">**Satellite locations** – The additional geo locations that you have configured to host data in your Office 365 tenant.</span></span> <span data-ttu-id="fb208-112">다중 지역 테넌트는 북미 및 유럽과 같이 둘 이상의 지리적 위치에 걸쳐 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb208-112">Multi-geo tenants span more than one geo location, for example, North America and Europe.</span></span>

-   <span data-ttu-id="fb208-113">**기본 데이터 위치(PDL)** - 개별 사용자의 Exchange 및 OneDrive 데이터가 저장되는 위치 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="fb208-113">**Preferred Data Location (PDL)** – The geo location where an individual user's Exchange and OneDrive data is stored.</span></span> <span data-ttu-id="fb208-114">이는 관리자가 테넌트을 위해 구성된 지리적 위치 에 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb208-114">This can be set by the administrator to any of the geo locations that have been configured for the tenant.</span></span> <span data-ttu-id="fb208-115">OneDrive 사이트가 이미 있는 사용자의 PDL을 변경하면 OneDrive 데이터가 자동으로 새 지리적 위치로 이동되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fb208-115">Note that if you change the PDL for a user who already has a OneDrive site, their OneDrive data is not moved to the new geo location automatically.</span></span> <span data-ttu-id="fb208-116">자세한 내용은 [OneDrive 라이브러리를 다른 지리적 위치로 이동](move-onedrive-between-geo-locations.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="fb208-116">See [Move a OneDrive library to a different geo-location](move-onedrive-between-geo-locations.md) for more information.</span></span> <span data-ttu-id="fb208-117">Exchange 사서함이있는 경우 사서함은 새 기본 설정 데이터 위치로 자동 이동됩니다.</span><span class="sxs-lookup"><span data-stu-id="fb208-117">If they have an Exchange mailbox, the mailbox is moved to the new preferred data location automatically.</span></span>

<span data-ttu-id="fb208-118">Multi-Geo를 사용하려면 다음 4가지 주요 단계가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="fb208-118">Enabling Multi-Geo requires four key steps:</span></span>

1.  <span data-ttu-id="fb208-119">계정 팀과 협의하여 추가 하려면 계정 팀에서 작업 하는 _Office 365의 Multi-Geo 기능_ 서비스 계획을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="fb208-119">Work with your account team to add the _Multi-Geo Capabilities in Office 365_ service plan.</span></span>

2.  <span data-ttu-id="fb208-120">원하는 위성 위치를 선택하고 테넌트에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="fb208-120">Choose your desired satellite location(s) and add them to your tenant.</span></span>

3.  <span data-ttu-id="fb208-121">사용자가 선호하는 데이터 위치를 원하는 위성 위치로 설정하십시오.</span><span class="sxs-lookup"><span data-stu-id="fb208-121">Set your users' preferred data location to the desired satellite location.</span></span> <span data-ttu-id="fb208-122">새 OneDrive 사이트 또는 Exchange 사서함이 사용자에게 제공되면 PDL에 프로비저닝됩니다.</span><span class="sxs-lookup"><span data-stu-id="fb208-122">When a new OneDrive site or Exchange mailbox is provisioned for a user, it is provisioned to their PDL.</span></span>

4.  <span data-ttu-id="fb208-123">필요에 따라 중앙 위치에 있는 사용자의 기존 OneDrive 사이트를 기본 설정 데이터 위치로 마이그레이션합니다.</span><span class="sxs-lookup"><span data-stu-id="fb208-123">Migrate your users' existing OneDrive sites from the central location to their preferred data location as needed.</span></span> <span data-ttu-id="fb208-124">(Exchange 사서함은 사용자의 PDL을 설정할 때 자동으로 마이그레이션됩니다.)</span><span class="sxs-lookup"><span data-stu-id="fb208-124">(Exchange mailboxes are migrated automatically when you set a user's PDL.)</span></span>

<span data-ttu-id="fb208-125">이러한 각 단계에 대한 자세한 내용은 [Office 365 Multi-Geo 구성](multi-geo-tenant-configuration.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fb208-125">See [Configure Office 365 Multi-Geo](multi-geo-tenant-configuration.md) for details on each of these steps.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fb208-126">Office 365 Multi-Geo는 성능 최적화를 위해 설계되지 않았고 데이터 거주 요구 사항을 충족하도록 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="fb208-126">Note that Office 365 Multi-Geo is not designed for performance optimization, it is designed to meet data residency requirements.</span></span> <span data-ttu-id="fb208-127">Office 365의 성능 최적화에 대한 자세한 내용은 [Office 365의 네트워크 계획 및 성능 조정](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848)을 참조하거나 지원 그룹에 문의하세요.</span><span class="sxs-lookup"><span data-stu-id="fb208-127">For information about performance optimization for Office 365, see [Network planning and performance tuning for Office 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) or contact your support group.</span></span>

<span data-ttu-id="fb208-128">다음 위치 중 하나를 OneDrive 및 SharePoint 사이트를 호스팅 할 수있는 위성 위치로 구성하고 Exchange 사서함을 구성 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb208-128">You can configure any of the following locations to be satellite locations where you can host OneDrive and SharePoint sites, and Exchange mailboxes.</span></span> <span data-ttu-id="fb208-129">다중 지역을 계획할 때 Office 365 테넌트에 추가 할 위치 목록을 만드십시오.</span><span class="sxs-lookup"><span data-stu-id="fb208-129">As you plan for multi-geo, make a list of the locations that you want to add to your Office 365 tenant.</span></span> <span data-ttu-id="fb208-130">하나 또는 두 개의 위성 위치로 시작한 다음 필요한 경우 더 많은 지역 위치로 점진적으로 확장하는 것을 권장합니다.</span><span class="sxs-lookup"><span data-stu-id="fb208-130">We recommend starting with one or two satellite locations and then gradually expanding to more geo locations, if needed.</span></span>

[!INCLUDE [Office 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

<span data-ttu-id="fb208-p108">다중 위치를 구성할 경우 Office 365로 마이그레이션하는 동안 온-프레미스 인프라를 통합할 기회를 고려하는 것이 좋습니다. 예를 들어, 싱가포르 및 말레이시아에 온-프레미스 팜이 있는 경우, 데이터 상주 요구에 맞을 경우 APC 위성 위치로 통합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb208-p108">When you configure multi-geo, consider taking the opportunity to consolidate your on-premises infrastructure while migrating to Office 365. For example, if you have on-premises farms in Singapore and Malaysia, then you can consolidate them to the APC satellite location, provided data residency requirements allow you to do so.</span></span>

## <a name="best-practices"></a><span data-ttu-id="fb208-133">모범 사례</span><span class="sxs-lookup"><span data-stu-id="fb208-133">Best practices</span></span>

<span data-ttu-id="fb208-134">몇 가지 초기 테스트를 수행하기 위해 Office 365에서 테스트 사용자를 만드는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="fb208-134">We recommend that you create a test user in Office 365 to do some initial testing.</span></span> <span data-ttu-id="fb208-135">프로덕션 사용자에게 Office 365 Multi-Geo로 진행하기 전에 이 사용자와의 몇 가지 테스트 및 확인 단계를 거칩니다.</span><span class="sxs-lookup"><span data-stu-id="fb208-135">We’ll walk through some testing and verification steps with this user before you proceed to onboard production users into Office 365 Multi-Geo.</span></span>

<span data-ttu-id="fb208-136">테스트 사용자와 테스트를 마친 후에는 IT 부서의 파일럿 그룹을 선택하여 새로운 지리적 위치에서 OneDrive 및 Exchange를 가장 먼저 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb208-136">Once you’ve completed testing with the test user, select a pilot group – perhaps from your IT department – to be the first to use OneDrive and Exchange in a new geo location.</span></span> <span data-ttu-id="fb208-137">이 첫 번째 그룹에서는 아직 OneDrive가 없는 사용자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fb208-137">For this first group, select users who do not yet have a OneDrive.</span></span> <span data-ttu-id="fb208-138">이 초기 그룹에 5명 이하를 두고 일괄 공개 접근 방식을 따라 점차적으로 확장하는 것을 권장합니다.</span><span class="sxs-lookup"><span data-stu-id="fb208-138">We recommend no more than five people in this initial group and gradually expand following a batched rollout approach.</span></span>

<span data-ttu-id="fb208-p111">Office 365에서 해당 OneDrive를 프로비전할 지리적 위치를 결정할 수 있도록 각 사용자에게는 PDL(*기본 설정 데이터 위치*)이 설정되어 있어야 합니다. 사용자의 기본 설정 데이터 위치는 선택한 위성 위치 중 하나 또는 사용자의 중앙 위치와 일치해야 합니다. PDL 필드는 필수는 아니지만 모든 사용자에 대해 PDL을 설정하는 것이 좋습니다. PDL이 없는 사용자의 워크로드는 중앙 위치에 프로비전됩니다.</span><span class="sxs-lookup"><span data-stu-id="fb208-p111">Each user should have a *preferred data location* (PDL) set so that Office 365 can determine in which geo location to provision their OneDrive. The user's preferred data location must match one of your chosen satellite locations or your central location. While the PDL field is not mandatory, we recommend that a PDL be set for all users. Workloads of a user without a PDL will be provisioned in the central location.</span></span>

<span data-ttu-id="fb208-p112">사용자 목록을 만들고, 해당 UPN(사용자 주체 이름)과 해당 기본 설정 데이터 위치에 대한 위치 코드를 포함합니다. 시작할 테스트 사용자와 초기 파일럿 그룹을 포함합니다. 구성 절차를 위해 이 목록이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="fb208-p112">Create a list of your users, and include their user principal name (UPN) and the location code for the appropriate preferred data location. Include your test user and your initial pilot group to start with. You'll need this list for the configuration procedures.</span></span>

<span data-ttu-id="fb208-146">사용자가 온 - 프레미스 Active Directory 시스템에서 Azure Active Directory로 동기화되는 경우 기본 데이터 위치를 Active Directory 특성으로 설정하고 Azure Active Directory Connect를 사용하여 동기화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb208-146">If your users are synchronized from an on-premises Active Directory system to Azure Active Directory, you must set the preferred data location as an Active Directory attribute and synchronize it by using Azure Active Directory Connect.</span></span> <span data-ttu-id="fb208-147">Azure AD PowerShell을 사용하여 동기화된 사용자의 기본 데이터 위치를 직접 구성할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fb208-147">You cannot directly configure the preferred data location for synchronized users using Azure AD PowerShell.</span></span> <span data-ttu-id="fb208-148">Active Directory에서 PDL을 설정하고 동기화하는 단계는 [Azure Active Directory Connect 동기화: Office 365 리소스의 기본 데이터 위치 구성](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation)에서 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="fb208-148">The steps to set up PDL in Active Directory and Synchronize it are covered in [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span>

<span data-ttu-id="fb208-p114">SharePoint 및 OneDrive 설정과 서비스가 다중 위치를 인식하므로 다중 위치 테넌트의 관리는 다중 위치가 아닌 테넌트의 관리와 다를 수 있습니다. 구성을 계속하기 전에 [다중 위치 환경 관리](administering-a-multi-geo-environment.md)를 검토하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="fb208-p114">The administration of a multi-geo tenant can differ from a non-multi-geo tenant, as many of the SharePoint and OneDrive settings and services are multi-geo aware. We recommend that you review [Administering a multi-geo environment](administering-a-multi-geo-environment.md) before you proceed with your configuration.</span></span>

<span data-ttu-id="fb208-151">다중 위치 환경의 최종 사용자 경험에 대한 자세한 내용은 [다중 위치 환경의 사용자 경험](multi-geo-user-experience.md)을 읽어보세요.</span><span class="sxs-lookup"><span data-stu-id="fb208-151">Read [User experience in a mult-geo environment](multi-geo-user-experience.md) for details about your end users' experience in a multi-geo environment.</span></span>

<span data-ttu-id="fb208-152">Office 365 다중 지역 테넌시의 Teams 경험에 대한 자세한 내용은 [Office 365 OneDrive 및 SharePoint Online 다중 지역 지원 테넌시 Teams 경험](https://docs.microsoft.com/microsoftteams/teams-experience-o365odb-spo-multi-geo)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="fb208-152">For details about the Teams experience in an Office 365 multi-geo tenancy, see [Teams experience in an Office 365 OneDrive and SharePoint Online Multi-Geo-enabled tenancy](https://docs.microsoft.com/microsoftteams/teams-experience-o365odb-spo-multi-geo).</span></span>

<span data-ttu-id="fb208-153">Office 365 Multi-Geo를 구성하려면 [Office 365 Multi-Geo 구성](multi-geo-tenant-configuration.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="fb208-153">To get started configuring Office 365 Multi-Geo, see [Configure Office 365 Multi-Geo](multi-geo-tenant-configuration.md).</span></span>

<span data-ttu-id="fb208-154">구성을 완료한 경우 기본 설정 데이터 위치에서 작업할 때 필요하므로 [사용자의 OneDrive 라이브러리를 마이그레이션](move-onedrive-between-geo-locations.md)해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb208-154">Once you've completed the configuration, remember to [migrate your users' OneDrive libraries](move-onedrive-between-geo-locations.md) as needed to get your users working from their preferred data locations.</span></span>
