---
title: 독일 Microsoft 클라우드(도이칠란드 Microsoft 클라우드)에서 Office 365 서비스 독일 신규 데이터 센터 지역으로의 마이그레이션
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/09/2019
audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 706d5449-45e5-4b0c-a012-ab60501899ad
description: '요약: 독일 Microsoft 클라우드(도이칠란드 Microsoft 클라우드)에서 Office 365 서비스 독일 신규 데이터 센터 지역으로의 마이그레이션 이해 '
ms.openlocfilehash: 95edbeeb79549957ff49afa8b8a96160945b0f20
ms.sourcegitcommit: 77b8fd702d3a1010d3906d4024d272ad2097f54f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2019
ms.locfileid: "39962445"
---
# <a name="migration-from-microsoft-cloud-germany-microsoft-cloud-deutschland-to-office-365-services-in-the-new-german-datacenter-regions"></a><span data-ttu-id="10dcc-103">독일 Microsoft 클라우드(도이칠란드 Microsoft 클라우드)에서 Office 365 서비스 독일 신규 데이터 센터 지역으로의 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="10dcc-103">Migration from Microsoft Cloud Germany (Microsoft Cloud Deutschland) to Office 365 services in the new German datacenter regions</span></span>


>[!Note]
><span data-ttu-id="10dcc-104">이 문서는 적격 독일/도이칠란드 Microsoft 클라우드 고객에게만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10dcc-104">This article only applies to eligible Microsoft Cloud Germany/Deutschland customers.</span></span>
>

## <a name="cloud-service-offerings-in-germany"></a><span data-ttu-id="10dcc-105">독일에서 제공되는 클라우드 서비스 </span><span class="sxs-lookup"><span data-stu-id="10dcc-105">Cloud service offerings in Germany</span></span>

<span data-ttu-id="10dcc-106">2018년 8월, 보다 원활한 고객의 디지털 변환을 위해 독일의 새로운 클라우드 지역에서 Azure, Office 365, Dynamics 365 및 Power Platform 등을 포함하는 통합 Microsoft 클라우드 서비스 계획을 발표했습니다. </span><span class="sxs-lookup"><span data-stu-id="10dcc-106">In August 2018, we announced our intention to deliver the complete Microsoft cloud – Azure, Office 365, Dynamics 365 and Power Platform – from new cloud regions in Germany to better enable the digital transformation of our customers.</span></span> <span data-ttu-id="10dcc-107">2019년 8월, 독일의 신규 클라우드 지역 출범을 발표합니다.  </span><span class="sxs-lookup"><span data-stu-id="10dcc-107">In August 2019, we announced we are now in the process of opening of the new cloud regions in Germany.</span></span> <span data-ttu-id="10dcc-108">Azure는 8월부터 Office 365는 12월부터 사용 가능합니다. </span><span class="sxs-lookup"><span data-stu-id="10dcc-108">We announced the availability of Azure in August and Office 365 became available in December.</span></span>  <span data-ttu-id="10dcc-109">Dynamics 365 및 Power Platform은 2020 1분기부터 가능할 것으로 예상됩니다. </span><span class="sxs-lookup"><span data-stu-id="10dcc-109">Dynamics 365 and Power Platform are anticipated to become available in the first quarter of 2020.</span></span>  

<span data-ttu-id="10dcc-110">신규 지역은 더 나은 유연성, 최신 인테리전트 클라우드 서비스, 글로벌 크라우드와의 완벽한 연결성 및 데이터 보존을 원하는 진화하는 독일 고객의 니즈를 충족하도록 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="10dcc-110">The new regions are designed to address the evolving needs of German customers with the greater flexibly, the latest intelligent cloud services, and full connectivity to our global cloud network as well as customer data residency within Germany.</span></span>

## <a name="moving-to-the-new-german-regions"></a><span data-ttu-id="10dcc-111">신규 독일 지역으로 이전 </span><span class="sxs-lookup"><span data-stu-id="10dcc-111">Moving to the new German regions</span></span>

<span data-ttu-id="10dcc-112">기존 독일 Microsoft 클라우드(도이칠란드 Microsoft 클라우드) 고객은 이제 Office 365, Dynamics 365 고객 참여 및 Power Platform BI 고객 마이그레이션을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10dcc-112">Existing Microsoft Cloud Germany (Microsoft Cloud Deutschland) customers can now begin to migrate their Office 365, Dynamics 365 Customer Engagement, and Power Platform BI customers.</span></span>  <span data-ttu-id="10dcc-113">첫 번째 단계는 Microsoft 주도 신규 독일 데이터 센터 지역으로의 [마이그레이션에 동의](https://aka.ms/office365germanymoveoptin)하는 것입니다. </span><span class="sxs-lookup"><span data-stu-id="10dcc-113">The first step is to [opt-in to a Microsoft-led migration](https://aka.ms/office365germanymoveoptin) to our new German datacenter regions.</span></span>

<span data-ttu-id="10dcc-114">Microsoft 주도 방식에 동의하면 2020년에 마이그레이션 됩니다. </span><span class="sxs-lookup"><span data-stu-id="10dcc-114">For organizations who opt-in to the Microsoft-driven approach, migrations are expected to take place in 2020.</span></span> <span data-ttu-id="10dcc-115">마이그레이션이 되면 핵심 고객 데이터 및 구독정보는 신규 독일 지역으로 이전됩니다. </span><span class="sxs-lookup"><span data-stu-id="10dcc-115">As a result of the migration, core customer data and subscriptions are moved to the new German regions.</span></span> 

<span data-ttu-id="10dcc-116">Microsoft 주도 방식에 동의하면 다음 서비스도 함께 마이그레이션됩니다.</span><span class="sxs-lookup"><span data-stu-id="10dcc-116">The following services will be migrated as part of the Microsoft-driven approach:</span></span>

- <span data-ttu-id="10dcc-117">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="10dcc-117">Azure Active Directory</span></span>
- <span data-ttu-id="10dcc-118">Exchange Online</span><span class="sxs-lookup"><span data-stu-id="10dcc-118">Exchange Online</span></span>
- <span data-ttu-id="10dcc-119">Exchange Online Protection</span><span class="sxs-lookup"><span data-stu-id="10dcc-119">Exchange Online Protection</span></span>
- <span data-ttu-id="10dcc-120">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="10dcc-120">SharePoint Online</span></span>
- <span data-ttu-id="10dcc-121">비즈니스용 OneDrive</span><span class="sxs-lookup"><span data-stu-id="10dcc-121">OneDrive for Business</span></span>
- <span data-ttu-id="10dcc-122">비즈니스용 Skype Online</span><span class="sxs-lookup"><span data-stu-id="10dcc-122">Skype for Business Online</span></span>

<span data-ttu-id="10dcc-123">독일 Microsoft 클라우드에서 독일 데이터 센터 지역으로 마이그레이션하는 동안 기존의 비즈니스용 Skype Online 고객은 Microsoft Teams로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="10dcc-123">As part of the migration from Microsoft Cloud Germany to the German region, existing Skype for Business Online customers will transition to Microsoft Teams.</span></span> <span data-ttu-id="10dcc-124">자세한 내용은 [Microsoft Teams 업그레이드 시작하기](https://aka.ms/SkypeToTeams-Home)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="10dcc-124">See the [Getting started with your Microsoft Teams upgrade](https://aka.ms/SkypeToTeams-Home) for more information.</span></span>

- <span data-ttu-id="10dcc-125">Office 365 그룹</span><span class="sxs-lookup"><span data-stu-id="10dcc-125">Office 365 Groups</span></span>
- <span data-ttu-id="10dcc-126">Dynamics 365 / Power Platform</span><span class="sxs-lookup"><span data-stu-id="10dcc-126">Dynamics 365 / Power Platform</span></span>

<span data-ttu-id="10dcc-127">이들 서비스의 마이그레이션의 필요 조건과 영향에 관한 내용은 [Dynamics 365 고객 참여](https://aka.ms/D365ceOptIn) 문서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="10dcc-127">Pre-requisites and impact of migration for these services are described in the [Dynamics 365 Customer engagement](https://aka.ms/D365ceOptIn) article.</span></span>

## <a name="how-to-prepare-for-migration-to-office-365-services-in-the-new-german-datacenter-regions"></a><span data-ttu-id="10dcc-128">Office 365 서비스 신규 독일 데이터 센터 지역으로의 마이그레이션을 준비하는 방법 </span><span class="sxs-lookup"><span data-stu-id="10dcc-128">How to prepare for migration to Office 365 services in the new German datacenter regions</span></span>

<span data-ttu-id="10dcc-129">첫 번째 단계는 Microsoft가 여러분의 구독 정보 및 독일/도이칠란드 Microsoft 클라우드 데이터를 Office 365 서비스의 신규 독일 데이터 센터로 마이그레이션 할 수 있도록 승인하는 것입니다. </span><span class="sxs-lookup"><span data-stu-id="10dcc-129">The first step is to notify Microsoft so that we have your permission to migrate your subscription and data from Microsoft Cloud Germany/Deutschland to Office 365 services in the new German datacenter regions.</span></span>  <span data-ttu-id="10dcc-130">방법은 [동의 절차를](ms-cloud-germany-migration-opt-in.md) 참조하세요. </span><span class="sxs-lookup"><span data-stu-id="10dcc-130">Please refer to the [opt-in process](ms-cloud-germany-migration-opt-in.md) for instructions.</span></span>

- <span data-ttu-id="10dcc-131">모든 고객은 신규 독일 데이터 센터 지역을 포함한 전 세계 [Office 365 URL 및 IP 주소](urls-and-ip-address-ranges.md)를 확인해야 합니다. </span><span class="sxs-lookup"><span data-stu-id="10dcc-131">All migrating customers need to verify connectivity to the worldwide [Office 365 URLs and IP addresses](urls-and-ip-address-ranges.md), which include the new German datacenter regions.</span></span>
- <span data-ttu-id="10dcc-132">Office 365 플랫폼 서비스 설명서를 검토하고 독일 지역으로의 이전 후 어떤 기능과 서비스가 제공되는지 확인하세요.  </span><span class="sxs-lookup"><span data-stu-id="10dcc-132">Review the Office 365 platform service description to understand which features and services will become available to your organization following the completion to the German region.</span></span> 
- <span data-ttu-id="10dcc-133">유료 구독을 마이그레이션 합니다. </span><span class="sxs-lookup"><span data-stu-id="10dcc-133">The migration will transition paid subscriptions.</span></span>  <span data-ttu-id="10dcc-134">평가판 구독은 마이그레이션할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="10dcc-134">We cannot migrate trial subscriptions.</span></span>

<span data-ttu-id="10dcc-135">고객 불편을 최소화 하기 위해 테넌트 마이그레이션은 백 엔드 서비스 작업으로 실행됩니다.  </span><span class="sxs-lookup"><span data-stu-id="10dcc-135">Tenant migrations are executed as back-end service operations with minimal customer interaction required.</span></span>  <span data-ttu-id="10dcc-136">전반적인 마이그레이션 상태와 고객의 추가 작업 필요 여부는 메시지 센터를 통해 전달됩니다. </span><span class="sxs-lookup"><span data-stu-id="10dcc-136">Any additional customer-led tasks and overall migration status will be communicated via Message Center during the migration process.</span></span>  <span data-ttu-id="10dcc-137">고객 관리 DNS 업데이트나 Exchange Hybrid 고객에 대한 하이브리드 설정 재구성 등을 위해 고객의 추가 작업이 필요할 수 있습니다. </span><span class="sxs-lookup"><span data-stu-id="10dcc-137">Example of tasks may include customer managed DNS updates or reconfiguration of hybrid setup for Exchange hybrid customers.</span></span>

## <a name="customer-experience-during-the-migration-to-office-365-services-in-the-new-german-datacenter-regions"></a><span data-ttu-id="10dcc-138">Office 365 서비스 신규 독일 데이터 센터 지역으로 마이그레이션 하는 동안 고객 경험</span><span class="sxs-lookup"><span data-stu-id="10dcc-138">Customer experience during the migration to Office 365 services in the new German datacenter regions</span></span>

<span data-ttu-id="10dcc-139">테넌트 마이그레이션은 최종 고객 및 관리자에 게 최소의 영향을 미치도록 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="10dcc-139">Tenant migrations are designed to have minimal impact to end customers and administrators.</span></span>  <span data-ttu-id="10dcc-140">하지만, 각 작업과 관련하여 다음 사항에 유의 하세요. </span><span class="sxs-lookup"><span data-stu-id="10dcc-140">However, there are considerations for each workload.</span></span>  

### <a name="azure-active-directory"></a><span data-ttu-id="10dcc-141">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="10dcc-141">Azure Active Directory</span></span>

<span data-ttu-id="10dcc-142">독일 Microsoft 클라우드 Office/Dynamics 구독은 Azure Active Directory (Azure AD) 재배치와 함께 독일 지역으로 전환됩니다. </span><span class="sxs-lookup"><span data-stu-id="10dcc-142">Office/Dynamics subscriptions from Microsoft Cloud Germany are transitioned to the German region with the Azure Active Directory (Azure AD) relocation.</span></span> <span data-ttu-id="10dcc-143">그런 다음 신규 월드와이드 서비스 구독이 반영되도록 업데이트 됩니다. </span><span class="sxs-lookup"><span data-stu-id="10dcc-143">The organization is then updated to reflect new worldwide service subscriptions.</span></span> <span data-ttu-id="10dcc-144">구독을 이전하는 잠깐의 시간 동안 구독 변경이 차단됩니다. </span><span class="sxs-lookup"><span data-stu-id="10dcc-144">During the brief subscription transfer process, changes to subscriptions will be blocked.</span></span>

### <a name="exchange-online"></a><span data-ttu-id="10dcc-145">Exchange Online</span><span class="sxs-lookup"><span data-stu-id="10dcc-145">Exchange Online</span></span>

<span data-ttu-id="10dcc-146">Exchange Online Hybrid 고객은 전환 이전에 하이브리드 구성 마법사를 다시 실행 하여 독일 Microsoft 클라우드에 대한 온프레미스 구성을 업데이트 하고 월드와이드 서비스 정리시 HCW를 재실행 해야 합니다. </span><span class="sxs-lookup"><span data-stu-id="10dcc-146">Exchange Online Hybrid customers must re-run the Hybrid Configuration Wizard to update on-premises configuration against Microsoft Cloud Germany before the transition, and re-execution of the HCW upon cleanup against the worldwide service.</span></span> <span data-ttu-id="10dcc-147">사용자 지정 도메인을 사용 하는 고객은 추가 DNS 업데이트가 요구될 수 있습니다. </span><span class="sxs-lookup"><span data-stu-id="10dcc-147">Additional DNS updates may be required for customers with custom domains.</span></span>

<span data-ttu-id="10dcc-148">사서함은 백 엔드 프로세스로 마이그레이션되며, 사용자는 전환이 진행 되는 동안 독일 Microsoft 클라우드나 독일 지역에 있을 수 있으며, 동일한 Exchange 조직(GAL)에 있습니다. </span><span class="sxs-lookup"><span data-stu-id="10dcc-148">Mailboxes are migrated as a backend process, users in your organization may be in either Microsoft Cloud Germany or German region during the transition and are part of the same Exchange organization (GAL)</span></span>

### <a name="exchange-online-protection"></a><span data-ttu-id="10dcc-149">Exchange Online Protection</span><span class="sxs-lookup"><span data-stu-id="10dcc-149">Exchange Online Protection</span></span>

<span data-ttu-id="10dcc-150">백 엔드 Exchange Online Protection 기능은 신규 독일 지역으로 복사됩니다. </span><span class="sxs-lookup"><span data-stu-id="10dcc-150">Backend Exchange Online Protection features are copied to new Germany region</span></span>

### <a name="sharepoint-online"></a><span data-ttu-id="10dcc-151">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="10dcc-151">SharePoint Online</span></span>

<span data-ttu-id="10dcc-152">SharePoint Online 마이그레이션이 완료 되면 데이터 인덱스가 다시 작성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10dcc-152">Upon completion of the SharePoint Online migration to the German region, data indexes are rebuilt.</span></span> <span data-ttu-id="10dcc-153">검색 인덱스에 종속 된 기능은 인덱스 재작성을 완료 하는 동안 영향을 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10dcc-153">Features dependent on search indexes may be impacted while reindexing completes.</span></span>

<span data-ttu-id="10dcc-154">전환된 기존 sharepoint.de URL은 보존 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10dcc-154">Existing sharepoint.de URLs are preserved for transitioned organizations.</span></span>

### <a name="onedrive-for-business"></a><span data-ttu-id="10dcc-155">비즈니스용 OneDrive</span><span class="sxs-lookup"><span data-stu-id="10dcc-155">OneDrive for Business</span></span>

<span data-ttu-id="10dcc-156">비즈니스용 OneDrive 마이그레이션이 완료 되면 데이터 인덱스가 다시 작성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10dcc-156">Upon completion of the OneDrive for Business migration to the German region, data indexes are rebuilt.</span></span> <span data-ttu-id="10dcc-157">검색 인덱스에 종속 된 기능은 인덱스 재작성을 완료 하는 동안 영향을 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10dcc-157">Features dependent on search indexes may be impacted while reindexing completes.</span></span>

### <a name="skype-for-business-online"></a><span data-ttu-id="10dcc-158">비즈니스용 Skype Online</span><span class="sxs-lookup"><span data-stu-id="10dcc-158">Skype for Business Online</span></span>

<span data-ttu-id="10dcc-159">기존 비즈니스용 Skype Online 고객은 Microsoft 팀으로 이관 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10dcc-159">Existing Skype for Business Online customers will transition to Microsoft Teams.</span></span> <span data-ttu-id="10dcc-160">자세한 내용은 [https://aka.ms/SkypeToTeams-Home](https://aka.ms/SkypeToTeams-Home)을 참조하세요. </span><span class="sxs-lookup"><span data-stu-id="10dcc-160">See [https://aka.ms/SkypeToTeams-Home](https://aka.ms/SkypeToTeams-Home) for more information.</span></span>


## <a name="key-differences-between-microsoft-cloud-germany-microsoft-cloud-deutschland-and-office-365-services-in-the-new-german-datacenter-regions"></a><span data-ttu-id="10dcc-161">독일 Microsoft 클라우드(도이칠란드 Microsoft 클라우드)와 Office 365 서비스 신규 독일 데이터 센터 지역과의 주요 차이 </span><span class="sxs-lookup"><span data-stu-id="10dcc-161">Key differences between Microsoft Cloud Germany (Microsoft Cloud Deutschland) and Office 365 services in the new German datacenter regions</span></span>


|| <span data-ttu-id="10dcc-162">독일 Microsoft 클라우드(도이칠란드 Microsoft 클라우드)</span><span class="sxs-lookup"><span data-stu-id="10dcc-162">Microsoft Cloud Germany (Microsoft Cloud Deutschland)</span></span> | <span data-ttu-id="10dcc-163">신규 독일 데이터 센터 지역에서의 Office 365 서비스</span><span class="sxs-lookup"><span data-stu-id="10dcc-163">Office 365 services in the new German datacenter regions</span></span> |
|:-------|:-----|:-----|
| <span data-ttu-id="10dcc-164">하나의 Office 365 테넌트만으로도 구독 가능한 Microsoft 365 서비스</span><span class="sxs-lookup"><span data-stu-id="10dcc-164">Microsoft 365 services available for subscription with just one Office 365 tenant</span></span> | <span data-ttu-id="10dcc-165">15 개 서비스 (REF 참조)</span><span class="sxs-lookup"><span data-stu-id="10dcc-165">15 services (see REF)</span></span> | <span data-ttu-id="10dcc-166">29 개 서비스 (REF 참조)</span><span class="sxs-lookup"><span data-stu-id="10dcc-166">29 services (see REF)</span></span> |
| <span data-ttu-id="10dcc-167">새로운 기능</span><span class="sxs-lookup"><span data-stu-id="10dcc-167">New features</span></span> | <span data-ttu-id="10dcc-168">새로운 기능은 제공하지 않습니다. </span><span class="sxs-lookup"><span data-stu-id="10dcc-168">No new features are available.</span></span> | <span data-ttu-id="10dcc-169">글로벌 Office 365 서비스와 동일한 새로운 기능이 제공됩니다. </span><span class="sxs-lookup"><span data-stu-id="10dcc-169">New features will be available consistent with global Office 365 services.</span></span> |
| <span data-ttu-id="10dcc-170">데이터 트러스티</span><span class="sxs-lookup"><span data-stu-id="10dcc-170">Data trustee</span></span> | <span data-ttu-id="10dcc-171">예</span><span class="sxs-lookup"><span data-stu-id="10dcc-171">Yes</span></span> | <span data-ttu-id="10dcc-172">아니요</span><span class="sxs-lookup"><span data-stu-id="10dcc-172">No</span></span> |
| <span data-ttu-id="10dcc-173">글로벌 365 테넌트와 협업 </span><span class="sxs-lookup"><span data-stu-id="10dcc-173">Cross-tenant collaboration with global Office 365 tenants</span></span> | <span data-ttu-id="10dcc-174">아니요</span><span class="sxs-lookup"><span data-stu-id="10dcc-174">No</span></span> | <span data-ttu-id="10dcc-175">예</span><span class="sxs-lookup"><span data-stu-id="10dcc-175">Yes</span></span> |
| <span data-ttu-id="10dcc-176">고객 데이터 보존</span><span class="sxs-lookup"><span data-stu-id="10dcc-176">Customer data residency</span></span> | <span data-ttu-id="10dcc-177">고객 데이터는 독일 데이터 센터에만 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10dcc-177">Customer Data will be stored solely within German Data Centers.</span></span> | <span data-ttu-id="10dcc-178">Microsoft는 독일에서만 다음의 사용자 데이터를 저장합니다: Exchange Online 사서함 콘텐츠(전자 메일 본문, 일정, 전자 메일 첨부 파일), SharePoint Online 사이트 콘텐츠 및 사이트에 저장된 파일, 비즈니스용 OneDrive에 업로드 된 파일. </span><span class="sxs-lookup"><span data-stu-id="10dcc-178">Microsoft will store the following Customer Data at rest exclusively within Germany: Exchange Online mailbox content (e-mail body, calendar entries, and the content of e-mail attachments), SharePoint Online site content and the files stored within that site, and files uploaded to OneDrive for Business.</span></span> |
| <span data-ttu-id="10dcc-179">적용 약관 </span><span class="sxs-lookup"><span data-stu-id="10dcc-179">Applicable terms</span></span> | <span data-ttu-id="10dcc-180">[온라인 서비스 약관](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=46)[부록 포함](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=64)</span><span class="sxs-lookup"><span data-stu-id="10dcc-180">[Online Services Terms](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=46) with [supplement](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=64)</span></span> | [<span data-ttu-id="10dcc-181">온라인 서비스 약관</span><span class="sxs-lookup"><span data-stu-id="10dcc-181">Online Services Terms</span></span>](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=46) |
||||

## <a name="frequently-asked-questions"></a><span data-ttu-id="10dcc-182">FAQ</span><span class="sxs-lookup"><span data-stu-id="10dcc-182">Frequently Asked Questions</span></span>

### <a name="is-migration-required"></a><span data-ttu-id="10dcc-183">마이그레이션이 필수인가요? </span><span class="sxs-lookup"><span data-stu-id="10dcc-183">Is migration required?</span></span>

<span data-ttu-id="10dcc-184">Office 365 테넌트의 독일 Microsoft 클라우드(도이칠란드 Microsoft 클라우드)에서 Office 365 서비스 신규 독일 데이터 센터 지역으로의 마이그레이션은 무료입니다. </span><span class="sxs-lookup"><span data-stu-id="10dcc-184">Microsoft offers Office 365 tenant migration from Microsoft Cloud Germany to Office 365 services in the new German datacenter regions at no additional charge.</span></span>  <span data-ttu-id="10dcc-185">신규 독일 데이터 센터 지역으로의 마이그레이션을 강력히 추천드립니다만 독일 Microsoft 클라우드에도 업데이트 등 계속해서 지원을 제공할 예정입니다. </span><span class="sxs-lookup"><span data-stu-id="10dcc-185">While we do strongly recommend that you opt-in to migrate to the new German datacenter regions, we will continue to provide the necessary security updates to the Microsoft Cloud Germany region.</span></span>  

<span data-ttu-id="10dcc-186">Office 365 서비스 신규 독일 데이터 센터 지역의 추가 혜택: </span><span class="sxs-lookup"><span data-stu-id="10dcc-186">Office 365 services in the new German datacenter regions have additional benefits:</span></span>

- <span data-ttu-id="10dcc-187">경쟁력 있는 가격의 [Azure](https://azure.microsoft.com/pricing/calculator/),[Office 365](https://www.microsoft.com/microsoft-365/business/compare-more-office-365-for-business-plans), [Dynamics 365 고객 참여](https://dynamics.microsoft.com/pricing/) 및 [Power BI](https://powerbi.microsoft.com/pricing/)를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="10dcc-187">Offer market competitive pricing for [Azure](https://azure.microsoft.com/pricing/calculator/), [Office 365](https://www.microsoft.com/microsoft-365/business/compare-more-office-365-for-business-plans), [Dynamics 365 Customer Engagement](https://dynamics.microsoft.com/pricing/), and [Power BI](https://powerbi.microsoft.com/pricing/).</span></span> 
- <span data-ttu-id="10dcc-188">수많은 네트워크 엣지 사이트, Peering Location, 송신 지점이 있는 Microsoft 글로벌 네트워크에 연결되어 전세계 어디서나 강력한 사용자 환경을 제공합니다. </span><span class="sxs-lookup"><span data-stu-id="10dcc-188">Are connected to Microsoft global network, offering hundreds of network edge sites, peering locations, and egress points to deliver a robust user experience anywhere in the world.</span></span> 
- <span data-ttu-id="10dcc-189">독일 내 지역 고객 데이터 보관 요구사항을 충족하는데 도움을 줍니다. </span><span class="sxs-lookup"><span data-stu-id="10dcc-189">Help you meet local customer data residency requirements within Germany.</span></span> 
- <span data-ttu-id="10dcc-190">최신 버전 서비스 및 Microsoft 팀과 Office 365 Multi-Geo를 포함한 새로운 기능 등 글로벌 클라우드에 포함된 모든 기능이 제공됩니다.  </span><span class="sxs-lookup"><span data-stu-id="10dcc-190">Deliver our full featured global cloud offering, including the latest version of our services and new capabilities including Microsoft Teams and Multi-Geo in Office 365.</span></span> <span data-ttu-id="10dcc-191">[Azure](https://azure.microsoft.com/global-infrastructure/services/?products=all&regions=germany-non-regional,germany-central,germany-north,germany-northeast,germany-west-central), [Office 365](https://products.office.com/ko-KR/where-is-your-data-located) 및 [Dynamics 365](https://docs.microsoft.com/dynamics365/get-started/availability)의 지역별 상품을 비교하세요. </span><span class="sxs-lookup"><span data-stu-id="10dcc-191">Compare products by region for [Azure](https://azure.microsoft.com/global-infrastructure/services/?products=all&regions=germany-non-regional,germany-central,germany-north,germany-northeast,germany-west-central), [Office 365](https://products.office.com/ko-KR/where-is-your-data-located), and [Dynamics 365](https://docs.microsoft.com/dynamics365/get-started/availability).</span></span>
- <span data-ttu-id="10dcc-192">고객의 준법 및 규정 요구 사항을 충족 할 수 있도록 모든 기능, 엔터프라이즈급 보안 및 종합 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="10dcc-192">Offer full functionality, enterprise-grade security, and comprehensive features to help customers meet compliance and regulatory requirements.</span></span> 
- <span data-ttu-id="10dcc-193">기존 온라인 서비스 계약을 통해 사용 가능합니다. </span><span class="sxs-lookup"><span data-stu-id="10dcc-193">Are accessible through existing online services contracts.</span></span>

#### <a name="what-is-the-service-availability-between-the-different-office-365-cloud-service-offerings"></a><span data-ttu-id="10dcc-194">여러 Office 365 클라우드 서비스 간에 사용할 수 있는 서비스는 무엇인가요?</span><span class="sxs-lookup"><span data-stu-id="10dcc-194">What is the service availability between the different Office 365 cloud service offerings?</span></span>

<span data-ttu-id="10dcc-195">Microsoft Cloud Germany(Microsoft Cloud Deutschland) 클라우드 서비스를 통해 다음의 15가지 서비스를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10dcc-195">The following 15 services are available in the Microsoft Cloud Germany (Microsoft Cloud Deutschland) cloud service offering.</span></span>  <span data-ttu-id="10dcc-196">Microsoft Cloud Germany에는 신규 서비스를 추가하지 않고 있습니다. </span><span class="sxs-lookup"><span data-stu-id="10dcc-196">We are not adding new services to Microsoft Cloud Germany.</span></span>

1. <span data-ttu-id="10dcc-197">Exchange Online</span><span class="sxs-lookup"><span data-stu-id="10dcc-197">Exchange Online</span></span>
2. <span data-ttu-id="10dcc-198">고객 Lockbox (Exchange Online)</span><span class="sxs-lookup"><span data-stu-id="10dcc-198">Customer Lockbox (Exchange Online)</span></span>
3. <span data-ttu-id="10dcc-199">그룹 (모던 그룹)</span><span class="sxs-lookup"><span data-stu-id="10dcc-199">Groups (Modern groups)</span></span>
4. <span data-ttu-id="10dcc-200">Delve 프로필</span><span class="sxs-lookup"><span data-stu-id="10dcc-200">Delve Profile</span></span>
5. <span data-ttu-id="10dcc-201">Exchange Online Protection</span><span class="sxs-lookup"><span data-stu-id="10dcc-201">Exchange Online Protection</span></span>
6. <span data-ttu-id="10dcc-202">ATP (Advanced Threat Protection)</span><span class="sxs-lookup"><span data-stu-id="10dcc-202">Advanced Threat Protection (ATP)</span></span>
7. <span data-ttu-id="10dcc-203">Advanced eDiscovery</span><span class="sxs-lookup"><span data-stu-id="10dcc-203">Advanced eDiscovery</span></span>
8. <span data-ttu-id="10dcc-204">고급 데이터 관리</span><span class="sxs-lookup"><span data-stu-id="10dcc-204">Advance Data Governance</span></span>
9. <span data-ttu-id="10dcc-205">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="10dcc-205">SharePoint Online</span></span>
10. <span data-ttu-id="10dcc-206">고객 Lockbox (SharePoint Online)</span><span class="sxs-lookup"><span data-stu-id="10dcc-206">Customer Lockbox (SharePoint Online)</span></span>
11. <span data-ttu-id="10dcc-207">비즈니스용 OneDrive</span><span class="sxs-lookup"><span data-stu-id="10dcc-207">OneDrive for Business</span></span>
12. <span data-ttu-id="10dcc-208">비즈니스용 Skype</span><span class="sxs-lookup"><span data-stu-id="10dcc-208">Skype for Business</span></span>
13. <span data-ttu-id="10dcc-209">Word Online, Excel Online, PowerPoint, OneNote, Visio Online</span><span class="sxs-lookup"><span data-stu-id="10dcc-209">Word Online, Excel Online, PowerPoint, OneNote, Visio Online</span></span>
14. <span data-ttu-id="10dcc-210">Office 365 Pro Plus</span><span class="sxs-lookup"><span data-stu-id="10dcc-210">Office 365 Pro Plus</span></span>
15. <span data-ttu-id="10dcc-211">Outlook Mobile</span><span class="sxs-lookup"><span data-stu-id="10dcc-211">Outlook Mobile</span></span>

<span data-ttu-id="10dcc-212">현재 새로운 독일 데이터 센터 영역에서 Office 365 서비스의 일부로 29개의 서비스를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10dcc-212">There are currently 29 services available as part of Office 365 services in the new German datacenter regions.</span></span>  <span data-ttu-id="10dcc-213">계속해서 글로벌 Office 365 서비스와 일관된 새로운 기능과 서비스가 제공될 것입니다. </span><span class="sxs-lookup"><span data-stu-id="10dcc-213">New features and services will be available consistent with global Office 365 services on an ongoing basis.</span></span>

1. <span data-ttu-id="10dcc-214">Exchange Online</span><span class="sxs-lookup"><span data-stu-id="10dcc-214">Exchange Online</span></span>
2. <span data-ttu-id="10dcc-215">고객 Lockbox (Exchange Online)</span><span class="sxs-lookup"><span data-stu-id="10dcc-215">Customer Lockbox (Exchange Online)</span></span>
3. <span data-ttu-id="10dcc-216">그룹 (모던 그룹)</span><span class="sxs-lookup"><span data-stu-id="10dcc-216">Groups (Modern groups)</span></span>
4. <span data-ttu-id="10dcc-217">Delve 프로필</span><span class="sxs-lookup"><span data-stu-id="10dcc-217">Delve Profile</span></span>
5. <span data-ttu-id="10dcc-218">MyAnalytics</span><span class="sxs-lookup"><span data-stu-id="10dcc-218">MyAnalytics</span></span>
6. <span data-ttu-id="10dcc-219">Workplace Analytics</span><span class="sxs-lookup"><span data-stu-id="10dcc-219">Workplace Analytics</span></span>
7. <span data-ttu-id="10dcc-220">Exchange Online Protection</span><span class="sxs-lookup"><span data-stu-id="10dcc-220">Exchange Online Protection</span></span>
8. <span data-ttu-id="10dcc-221">ATP (Advanced Threat Protection)</span><span class="sxs-lookup"><span data-stu-id="10dcc-221">Advanced Threat Protection (ATP)</span></span>
9. <span data-ttu-id="10dcc-222">Advanced eDiscovery</span><span class="sxs-lookup"><span data-stu-id="10dcc-222">Advanced eDiscovery</span></span>
10. <span data-ttu-id="10dcc-223">고급 보안 관리</span><span class="sxs-lookup"><span data-stu-id="10dcc-223">Advanced Security Management</span></span>
11. <span data-ttu-id="10dcc-224">정보 권한 관리</span><span class="sxs-lookup"><span data-stu-id="10dcc-224">Information Rights Management</span></span>
12. <span data-ttu-id="10dcc-225">고급 데이터 관리</span><span class="sxs-lookup"><span data-stu-id="10dcc-225">Advance Data Governance</span></span>
13. <span data-ttu-id="10dcc-226">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="10dcc-226">SharePoint Online</span></span>
14. <span data-ttu-id="10dcc-227">고객 Lockbox (SharePoint Online)</span><span class="sxs-lookup"><span data-stu-id="10dcc-227">Customer Lockbox (SharePoint Online)</span></span>
15. <span data-ttu-id="10dcc-228">비즈니스용 OneDrive</span><span class="sxs-lookup"><span data-stu-id="10dcc-228">OneDrive for Business</span></span>
16. <span data-ttu-id="10dcc-229">Microsoft Stream</span><span class="sxs-lookup"><span data-stu-id="10dcc-229">Microsoft Stream</span></span>
17. <span data-ttu-id="10dcc-230">비즈니스용 Skype(마이그레이션 진행 중에 Microsoft Teams로 전환) </span><span class="sxs-lookup"><span data-stu-id="10dcc-230">Skype for Business (will transition to Microsoft Teams during the migration)</span></span>
18. <span data-ttu-id="10dcc-231">클라우드 PBX</span><span class="sxs-lookup"><span data-stu-id="10dcc-231">Cloud PBX</span></span>
19. <span data-ttu-id="10dcc-232">PSTN 회의</span><span class="sxs-lookup"><span data-stu-id="10dcc-232">PSTN Conferencing</span></span>
20. <span data-ttu-id="10dcc-233">PSTN 통화</span><span class="sxs-lookup"><span data-stu-id="10dcc-233">PSTN calling</span></span>
21. <span data-ttu-id="10dcc-234">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="10dcc-234">Microsoft Teams</span></span>
22. <span data-ttu-id="10dcc-235">관리 보고서/사용 현황 보고서</span><span class="sxs-lookup"><span data-stu-id="10dcc-235">Admin Reports / Usage Reports</span></span>
23. <span data-ttu-id="10dcc-236">Word Online, Excel Online, PowerPoint, OneNote 및 Visio Online</span><span class="sxs-lookup"><span data-stu-id="10dcc-236">Word Online, Excel Online, PowerPoint, OneNote, Visio Online</span></span>
24. <span data-ttu-id="10dcc-237">Planner</span><span class="sxs-lookup"><span data-stu-id="10dcc-237">Planner</span></span>
25. <span data-ttu-id="10dcc-238">Sway</span><span class="sxs-lookup"><span data-stu-id="10dcc-238">Sway</span></span>
26. <span data-ttu-id="10dcc-239">Office 365 Pro Plus</span><span class="sxs-lookup"><span data-stu-id="10dcc-239">Office 365 Pro Plus</span></span>
27. <span data-ttu-id="10dcc-240">Outlook Mobile</span><span class="sxs-lookup"><span data-stu-id="10dcc-240">Outlook Mobile</span></span>
28. <span data-ttu-id="10dcc-241">EMS E3 (Azure Active Directory Premium P1 + Intune + 권한 관리 서비스)</span><span class="sxs-lookup"><span data-stu-id="10dcc-241">EMS E3 (Azure Active Directory Premium P1 + Intune + Rights Management Service)</span></span>
29. <span data-ttu-id="10dcc-242">Yammer Online</span><span class="sxs-lookup"><span data-stu-id="10dcc-242">Yammer Online</span></span>

### <a name="when-will-migration-happen"></a><span data-ttu-id="10dcc-243">언제 마이그레이션 되나요? </span><span class="sxs-lookup"><span data-stu-id="10dcc-243">When will migration happen?</span></span>

#### <a name="azure"></a><span data-ttu-id="10dcc-244">Azure</span><span class="sxs-lookup"><span data-stu-id="10dcc-244">Azure</span></span> 

<span data-ttu-id="10dcc-245">지금 Azure 리소스를 다른 지역으로 [마이그레이션](https://docs.microsoft.com/azure/germany/germany-migration-main) 할 수 있습니다. </span><span class="sxs-lookup"><span data-stu-id="10dcc-245">You can begin [migrating](https://docs.microsoft.com/azure/germany/germany-migration-main) your Azure resources to another region today.</span></span> <span data-ttu-id="10dcc-246">Office 365, Dynamics 365 및/또는 Power BI와 함께 Azure를 사용 하는 경우 다음 단계를 따르세요.</span><span class="sxs-lookup"><span data-stu-id="10dcc-246">If you have Azure with Office 365, Dynamics 365, and/or Power BI, please follow the steps below.</span></span>

#### <a name="office-365"></a><span data-ttu-id="10dcc-247">Office 365</span><span class="sxs-lookup"><span data-stu-id="10dcc-247">Office 365</span></span>

<span data-ttu-id="10dcc-248">지금 Microsoft 주도 마이그레이션에 [동의 합니다](https://aka.ms/office365germanymoveoptin). </span><span class="sxs-lookup"><span data-stu-id="10dcc-248">[Opt-in](https://aka.ms/office365germanymoveoptin) to the Microsoft-driven migration today.</span></span> <span data-ttu-id="10dcc-249">마이그레이션을 시작할 준비가 되면 Microsoft 365 관리 센터에서 [메시지 센터를](https://docs.microsoft.com/office365/admin/manage/message-center?view=o365-worldwide) 통해 알려 드립니다. </span><span class="sxs-lookup"><span data-stu-id="10dcc-249">When we are ready to start your migration, we will inform you through the [Message Center](https://docs.microsoft.com/office365/admin/manage/message-center?view=o365-worldwide) in the Microsoft 365 admin center.</span></span>

#### <a name="dynamics-365-and-power-bi"></a><span data-ttu-id="10dcc-250">Dynamics 365 및 Power BI</span><span class="sxs-lookup"><span data-stu-id="10dcc-250">Dynamics 365 and Power BI</span></span>

<span data-ttu-id="10dcc-251">지금 [Dynamics 365 고객 참여](https://aka.ms/D365ceOptIn) 및 [Power BI](https://aka.ms/pbioptin)의 Microsoft 기반 마이그레이션에 동의 하세요. </span><span class="sxs-lookup"><span data-stu-id="10dcc-251">Opt-in to the Microsoft-driven migration for [Dynamics 365 Customer Engagement](https://aka.ms/D365ceOptIn) and [Power BI today](https://aka.ms/pbioptin).</span></span> <span data-ttu-id="10dcc-252">마이그레이션을 시작할 준비가 되면 Microsoft 365 관리 센터에서 [메시지 센터를](https://docs.microsoft.com/office365/admin/manage/message-center?view=o365-worldwide) 통해 알려 드립니다. </span><span class="sxs-lookup"><span data-stu-id="10dcc-252">When we are ready to start your migration, we will inform you through the [Message center](https://docs.microsoft.com/office365/admin/manage/message-center?view=o365-worldwide) in the Microsoft 365 admin center.</span></span>

### <a name="will-the-price-change-for-the-office-services-that-i-use"></a><span data-ttu-id="10dcc-253">사용하고 있는 Office 서비스 가격이 변동되나요? </span><span class="sxs-lookup"><span data-stu-id="10dcc-253">Will the price change for the Office services that I use?</span></span>

<span data-ttu-id="10dcc-254">예. Microsoft의 글로벌 클라우드 지역(신규 데이터 센터 지역 포함)의 가격은 일반적으로 더 저렴합니다. </span><span class="sxs-lookup"><span data-stu-id="10dcc-254">Yes, pricing in Microsoft’s global cloud regions (including the new datacenter regions) is generally lower.</span></span>

### <a name="how-do-i-get-help-from-microsoft-to-migrate-to-a-new-region-or-answer-support-questions"></a><span data-ttu-id="10dcc-255">신규 지역으로 마이그레이션 할 때 도움이 필요하거나 문의 사항이 있으면 어떻게 해야 하나요? </span><span class="sxs-lookup"><span data-stu-id="10dcc-255">How do I get help from Microsoft to migrate to a new region or answer support questions?</span></span>

<span data-ttu-id="10dcc-256">질문이 있는 경우에는 다음을 통해 연락하거나 파트너에게 문의 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10dcc-256">If you have questions, you can contact us as follows, or through your partner:</span></span>

- <span data-ttu-id="10dcc-257">Azure의 경우 Azure 포털에서 [새 지원 요청을](https://portal.microsoftazure.de/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/newsupportrequest) 제출하세요. </span><span class="sxs-lookup"><span data-stu-id="10dcc-257">For Azure, you can submit [new support requests](https://portal.microsoftazure.de/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/newsupportrequest) in the Azure portal.</span></span>
- <span data-ttu-id="10dcc-258">Office 365의 경우 "도움이 필요하신가요?"를 통해 문의 할 수 있습니다. </span><span class="sxs-lookup"><span data-stu-id="10dcc-258">For Office 365, you may submit questions using the “Need Help?”</span></span> <span data-ttu-id="10dcc-259">[Microsoft 365 관리 센터](https://portal.office.de/) 링크</span><span class="sxs-lookup"><span data-stu-id="10dcc-259">link of the [Microsoft 365 admin center](https://portal.office.de/).</span></span>
- <span data-ttu-id="10dcc-260">Office 365가 있는 Dynamics 365 고객 참여 및 Power BI 고객은 "도움이 필요하신가요?"를 통해 문의 할 수 있습니다. </span><span class="sxs-lookup"><span data-stu-id="10dcc-260">For Dynamics 365 Customer Engagement and Power BI customer who also have Office 365, you may submit questions using the “Need Help?”</span></span> <span data-ttu-id="10dcc-261">[Microsoft 365 관리 센터](https://portal.office.de/) 링크</span><span class="sxs-lookup"><span data-stu-id="10dcc-261">link of the [Microsoft 365 admin center](https://portal.office.de/).</span></span> <span data-ttu-id="10dcc-262">Dynamics 365 고객 참여 지원은 [여기](https://docs.microsoft.com/dynamics365/get-started/support/)를 이용하세요. </span><span class="sxs-lookup"><span data-stu-id="10dcc-262">Dynamics 365 Customer Engagement support options are located [here](https://docs.microsoft.com/dynamics365/get-started/support/).</span></span> <span data-ttu-id="10dcc-263">Power BI 지원은 [여기](https://powerbi.microsoft.com/support/)를 이용하세요. </span><span class="sxs-lookup"><span data-stu-id="10dcc-263">Power BI support options are located [here](https://powerbi.microsoft.com/support/).</span></span>

## <a name="more-information"></a><span data-ttu-id="10dcc-264">추가 정보</span><span class="sxs-lookup"><span data-stu-id="10dcc-264">More information</span></span>

- <span data-ttu-id="10dcc-265">[Microsoft Cloud Deutschland 마이그레이션 지원](https://aka.ms/germanymigrateassist)</span><span class="sxs-lookup"><span data-stu-id="10dcc-265">Microsoft Cloud Deutschland Migration Assistance at   </span></span>
- <span data-ttu-id="10dcc-266">[마이그레이션에 대해 옵트인하는 방법](https://aka.ms/office365germanymoveoptin)</span><span class="sxs-lookup"><span data-stu-id="10dcc-266">How to opt-in for migration at   </span></span>
- [<span data-ttu-id="10dcc-267">Dynamics 365 마이그레이션 프로그램 정보</span><span class="sxs-lookup"><span data-stu-id="10dcc-267">Dynamics 365 migration program information</span></span>](https://aka.ms/D365ceOptIn)
- [<span data-ttu-id="10dcc-268">Power BI 마이그레이션 프로그램 정보</span><span class="sxs-lookup"><span data-stu-id="10dcc-268">Power BI migration program information</span></span>](https://aka.ms/pbioptin)
- [<span data-ttu-id="10dcc-269">Office 365 URL 및 IP 주소 범위</span><span class="sxs-lookup"><span data-stu-id="10dcc-269">Office 365 URLs and IP address ranges</span></span>](https://aka.ms/o365endpoints)
- <span data-ttu-id="10dcc-270">[Office 365 하이브리드 구성 마법사](https://aka.ms/HybridWizard)</span><span class="sxs-lookup"><span data-stu-id="10dcc-270">Office 365 Hybrid Configuration Wizard at   </span></span>
- [<span data-ttu-id="10dcc-271">Microsoft Teams 업그레이드 시작하기</span><span class="sxs-lookup"><span data-stu-id="10dcc-271">Getting started with your Microsoft Teams upgrade</span></span>](https://aka.ms/SkypeToTeams-Home)
