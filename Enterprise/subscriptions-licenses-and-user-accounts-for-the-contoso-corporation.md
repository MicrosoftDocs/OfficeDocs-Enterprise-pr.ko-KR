---
title: "구독, 라이선스 및 Contoso Corporation에 대 한 사용자 계정"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: ec3b08f0-288c-4ba3-b822-dbf6352fa761
description: "요약: Contoso의 클라우드 구독, 라이선스, 사용자 계정 및 테 넌 트의 구조를 이해 합니다."
ms.openlocfilehash: 6bc90d7b166d5e0983eac8ed47ba16bede57426d
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2017
---
# <a name="subscriptions-licenses-and-user-accounts-for-the-contoso-corporation"></a><span data-ttu-id="0e173-103">구독, 라이선스 및 Contoso Corporation에 대 한 사용자 계정</span><span class="sxs-lookup"><span data-stu-id="0e173-103">Subscriptions, licenses, and user accounts for the Contoso Corporation</span></span>

 <span data-ttu-id="0e173-104">**요약:** Contoso의 클라우드 구독, 라이선스, 사용자 계정 및 테 넌 트의 구조를 이해 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e173-104">**Summary:** Understand the structure of Contoso's cloud subscriptions, licenses, user accounts, and tenants.</span></span>
  
<span data-ttu-id="0e173-105">모든 클라우드 서비스에 대 한 id 및 대금 청구의 일관 된 사용을 제공 하려면 Microsoft는 조직/구독/라이선스/사용자 계정을 계층 구조를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e173-105">To provide a consistent use of identities and billing for all cloud offerings, Microsoft provides an organization/subscriptions/licenses/user accounts hierarchy:</span></span>
  
- <span data-ttu-id="0e173-106">조직</span><span class="sxs-lookup"><span data-stu-id="0e173-106">Organization</span></span>
    
    <span data-ttu-id="0e173-107">Contoso.com와 같은 공용 DNS 도메인 이름에 따라 일반적으로 식별 되는 Microsoft 클라우드 서비스를 사용 하는 비즈니스 엔터티.</span><span class="sxs-lookup"><span data-stu-id="0e173-107">The business entity that is using Microsoft cloud offerings, typically identified by a public DNS domain name, such as contoso.com.</span></span>
    
- <span data-ttu-id="0e173-108">구독</span><span class="sxs-lookup"><span data-stu-id="0e173-108">Subscriptions</span></span>
    
    <span data-ttu-id="0e173-p101">Microsoft SaaS 클라우드 제품 (Office 365, Intune/EMS 및 Dynamics 365), 구독 되는 특정 제품 및 사용자 라이선스를 구입한 집합입니다. Azure, 구독을 조직에 소비 된 클라우드 서비스의 대금 청구를 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="0e173-p101">For Microsoft SaaS cloud offerings (Office 365, Intune/EMS, and Dynamics 365), a subscription is a specific product and a purchased set of user licenses. For Azure, a subscription allows for billing of consumed cloud services to the organization.</span></span>
    
- <span data-ttu-id="0e173-111">라이선스</span><span class="sxs-lookup"><span data-stu-id="0e173-111">Licenses</span></span>
    
    <span data-ttu-id="0e173-p102">Microsoft SaaS 클라우드 서비스에 대 한 라이선스에는 클라우드 서비스를 사용 하 여 특정 사용자 계정을 수 있습니다. Azure, 소프트웨어 라이선스 서비스 가격으로 하지만 추가 소프트웨어 라이선스를 구입 해야하는 경우에 따라 기본 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0e173-p102">For Microsoft SaaS cloud offerings, a license allows a specific user account to use cloud services. For Azure, software licenses are built into service pricing, but in some cases you will need to purchase additional software licenses.</span></span>
    
- <span data-ttu-id="0e173-114">사용자 계정</span><span class="sxs-lookup"><span data-stu-id="0e173-114">User accounts</span></span>
    
    <span data-ttu-id="0e173-115">사용자 계정을 Azure AD 테 넌 트에 저장 되 고 Windows Server AD와 같은 온-프레미스 id 공급자에서 동기화 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e173-115">User accounts are stored in an Azure AD tenant and can be synchronized from an on-premises identity provider such as Windows Server AD.</span></span>
    
## <a name="contosos-structure"></a><span data-ttu-id="0e173-116">Contoso의 구조</span><span class="sxs-lookup"><span data-stu-id="0e173-116">Contoso's structure</span></span>

<span data-ttu-id="0e173-117">Contoso는 조직 및 해당 구독, 라이선스, 계정 및 테 넌 트에 대 한 다음과 같은 구조를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e173-117">Contoso determined the following structure for the organization and its subscriptions, licenses, accounts, and tenants:</span></span>
  
<span data-ttu-id="0e173-118">**그림 1: Contoso의 조직, 구독, 라이선스, 사용자 계정 및 테 넌 트**</span><span class="sxs-lookup"><span data-stu-id="0e173-118">**Figure 1: Contoso's organization, subscriptions, licenses, user accounts and tenants**</span></span>

![Contoso의 조직, 구독, 라이선스, 사용자 계정 및 테넌트](images/Contoso_Poster/Subscriptions.png)
  
<span data-ttu-id="0e173-120">그림 1에는 Contoso 조직 여러 구독을 포함 하 고 Windows Server AD 포리스트 contoso.com에서 동기화 하는 사용자 계정이 포함 된 일반적인 Azure AD 테 넌에 연결 하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="0e173-120">Figure 1 shows how the Contoso organization includes multiple subscriptions and is tied to a common Azure AD tenant that contains the user accounts synchronized from the contoso.com Windows Server AD forest.</span></span>
  
- <span data-ttu-id="0e173-121">**조직** Contoso Corporation contoso.com 해당 공용 도메인 이름으로 식별 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0e173-121">**Organization** The Contoso Corporation is identified by its public domain name contoso.com.</span></span>
    
  - <span data-ttu-id="0e173-122">**구독 및 라이선스** Contoso Corporation 다음 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e173-122">**Subscriptions and licenses** The Contoso Corporation is using the following:</span></span>
    
  - <span data-ttu-id="0e173-123">5, 000 라이선스와 Office 365 Enterprise E3 제품</span><span class="sxs-lookup"><span data-stu-id="0e173-123">The Office 365 Enterprise E3 product with 5,000 licenses</span></span>
    
  - <span data-ttu-id="0e173-124">200 라이선스와 Office 365 Enterprise E5 제품</span><span class="sxs-lookup"><span data-stu-id="0e173-124">The Office 365 Enterprise E5 product with 200 licenses</span></span>
    
  - <span data-ttu-id="0e173-125">5, 000 라이선스 EMS 제품</span><span class="sxs-lookup"><span data-stu-id="0e173-125">The EMS product with 5,000 licenses</span></span>
    
  - <span data-ttu-id="0e173-126">100 라이선스 Dynamics 365 제품</span><span class="sxs-lookup"><span data-stu-id="0e173-126">The Dynamics 365 product with 100 licenses</span></span>
    
  - <span data-ttu-id="0e173-127">지역에 따라 여러 Azure 구독</span><span class="sxs-lookup"><span data-stu-id="0e173-127">Multiple Azure subscriptions based on regions</span></span>
    
  - <span data-ttu-id="0e173-128">**사용자 계정** 일반적인 Azure AD 테 넌 트 사용자 계정 목록을 포함 하 고 Azure 구독 개발/테스트를 제외 하 고 Contoso의 구독의 모든 그룹 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e173-128">**User accounts** A common Azure AD tenant contains the list of user accounts and groups used by all of Contoso's subscriptions, with the exception of dev/test Azure subscriptions.</span></span>
    
<span data-ttu-id="0e173-129">Contoso의 테 넌:</span><span class="sxs-lookup"><span data-stu-id="0e173-129">For Contoso's tenants:</span></span>
  
- <span data-ttu-id="0e173-p103">SaaS 클라우드 서비스에 대 한 테 넌 트 클라우드 서비스를 제공 하는 서버를 보관 하는 지역 위치입니다. Contoso의 Office 365, EMS, 및 Dynamics 365 테 넌 트를 호스팅할 유럽 지역 선택 했습니다.</span><span class="sxs-lookup"><span data-stu-id="0e173-p103">For SaaS cloud offerings, the tenant is the regional location that houses the servers providing cloud services. Contoso chose the European region to host its Office 365, EMS, and Dynamics 365 tenants.</span></span> 
    
- <span data-ttu-id="0e173-p104">Azure PaaS 서비스 및 응용 프로그램 및 IaaS IT 작업 전세계 모든 Azure 데이터 센터의 테 넌 시를 가질 수 있습니다. Azure AD 테 넌 트는 계정 및 그룹을 포함 하는 Azure AD의 특정 인스턴스.</span><span class="sxs-lookup"><span data-stu-id="0e173-p104">Azure PaaS services and apps and IaaS IT workloads can have tenancy in any Azure datacenter across the world. An Azure AD tenant is a specific instance of Azure AD containing accounts and groups.</span></span>
    
- <span data-ttu-id="0e173-134">일반적인 Azure AD 테 넌 트 Contoso Windows Server AD 포리스트에 대 한 동기화 된 계정이 포함 된 Microsoft의 클라우드 서비스 간에 IDaaS를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e173-134">The common Azure AD tenant that contains the synchronized accounts for the Contoso Windows Server AD forest provides IDaaS across Microsoft's cloud offerings.</span></span>
    
<span data-ttu-id="0e173-135">자세한 내용은 [구독, 라이선스, 계정 및 Microsoft의 클라우드 서비스에 대 한 테 넌 트를](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md)참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="0e173-135">For more information, see [Subscriptions, licenses, accounts, and tenants for Microsoft's cloud offerings](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md).</span></span>
  
## <a name="contosos-azure-subscriptions"></a><span data-ttu-id="0e173-136">Contoso의 Azure 구독</span><span class="sxs-lookup"><span data-stu-id="0e173-136">Contoso's Azure subscriptions</span></span>

<span data-ttu-id="0e173-137">그림 2에서는 Contoso의 Azure 구독의 계층 구조 디자인을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="0e173-137">Figure 2 shows the hierarchical design of Contoso's Azure subscriptions:</span></span>
  
<span data-ttu-id="0e173-138">**Azure 구독에 대 한 그림 2: Contoso의 구조**</span><span class="sxs-lookup"><span data-stu-id="0e173-138">**Figure 2: Contoso's structure for Azure subscriptions**</span></span>

![Azure Subscription에 대한 Contoso의 구조](images/Contoso_Poster/Subscriptions_Nested.png)
  
- <span data-ttu-id="0e173-140">Contoso의 위쪽에는 Microsoft와 해당 기업 계약에 따라 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e173-140">Contoso is at the top, based on its Enterprise Agreement with Microsoft.</span></span>
    
- <span data-ttu-id="0e173-141">Contoso의 Windows Server AD 포리스트의 도메인에 따라 전세계 Contoso Corporation의 서로 다른 영역에 해당 계정 집합이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e173-141">There are a set of accounts corresponding to the different regions of the Contoso Corporation around the world, based on the domains of Contoso's Windows Server AD forest.</span></span>
    
- <span data-ttu-id="0e173-142">각 지역 내에서 지역의 개발, 테스트 및 프로덕션 배포 요구 사항에 따라 하나 이상의 구독 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e173-142">Within each region, there are one or more subscriptions based on the region's development, testing, and production deployment needs.</span></span>
    
<span data-ttu-id="0e173-p105">각 Azure 구독 단일 연관 될 수 인증 및 권한 부여 Azure 서비스를 위한 사용자 계정 및 그룹을 포함 하는 Azure AD 테 넌 트입니다. 프로덕션 구독 일반적인 Contoso Azure AD 테 넌 트를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0e173-p105">Each Azure subscription can be associated with a single Azure AD tenant that contains user accounts and groups for authentication and authorization to Azure services. Production subscriptions use the common Contoso Azure AD tenant.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="0e173-145">See Also</span><span class="sxs-lookup"><span data-stu-id="0e173-145">See Also</span></span>

[<span data-ttu-id="0e173-146">Microsoft 클라우드 Contoso</span><span class="sxs-lookup"><span data-stu-id="0e173-146">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="0e173-147">Microsoft 클라우드 IT 아키텍처 리소스</span><span class="sxs-lookup"><span data-stu-id="0e173-147">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="0e173-148">Microsoft의 엔터프라이즈 클라우드 로드맵: IT 의사 결정권자를 위한 리소스</span><span class="sxs-lookup"><span data-stu-id="0e173-148">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)




