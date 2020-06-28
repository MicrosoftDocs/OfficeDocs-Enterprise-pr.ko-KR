---
title: Microsoft 클라우드 제품용 구독, 라이선스, 계정 및 테넌트
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 06/25/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_Architecture
ms.assetid: c720cffc-f9b5-4f43-9100-422f86a1027c
description: '요약: Microsoft의 클라우드 제품에서 조직, 구독, 라이선스, 사용자 계정 및 테넌트의 관계를 이해합니다.'
ms.openlocfilehash: 52857196f53a44196c96f60bd70564f5e3221b80
ms.sourcegitcommit: 0f7607b5e88b78ae250900ce7ce1b019cd245aa1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/26/2020
ms.locfileid: "44906283"
---
# <a name="subscriptions-licenses-accounts-and-tenants-for-microsofts-cloud-offerings"></a><span data-ttu-id="d2889-103">Microsoft 클라우드 제품용 구독, 라이선스, 계정 및 테넌트</span><span class="sxs-lookup"><span data-stu-id="d2889-103">Subscriptions, licenses, accounts, and tenants for Microsoft's cloud offerings</span></span>

<span data-ttu-id="d2889-104">Microsoft는 해당 클라우드 제품 간에 일관된 ID 사용 및 요금 청구를 위해 조직, 구독, 라이선스 및 사용자 계정을 포함하는 계층 구조를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d2889-104">Microsoft provides a hierarchy of organizations, subscriptions, licenses, and user accounts for consistent use of identities and billing across its cloud offerings:</span></span>
  
- <span data-ttu-id="d2889-105">Microsoft 365 및 Microsoft Office 365</span><span class="sxs-lookup"><span data-stu-id="d2889-105">Microsoft 365 and Microsoft Office 365</span></span>
- <span data-ttu-id="d2889-106">Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="d2889-106">Microsoft Azure</span></span>
- <span data-ttu-id="d2889-107">Microsoft Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="d2889-107">Microsoft Dynamics 365</span></span>

## <a name="elements-of-the-hierarchy"></a><span data-ttu-id="d2889-108">계층 구조의 요소</span><span class="sxs-lookup"><span data-stu-id="d2889-108">Elements of the hierarchy</span></span>

<span data-ttu-id="d2889-109">다음은 계층 구조의 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="d2889-109">Here are the elements of the hierarchy:</span></span>
  
### <a name="organization"></a><span data-ttu-id="d2889-110">조직</span><span class="sxs-lookup"><span data-stu-id="d2889-110">Organization</span></span>

<span data-ttu-id="d2889-111">An organization represents a business entity that is using Microsoft cloud offerings, typically identified by one or more public Domain Name System (DNS) domain names, such as contoso.com.</span><span class="sxs-lookup"><span data-stu-id="d2889-111">An organization represents a business entity that is using Microsoft cloud offerings, typically identified by one or more public Domain Name System (DNS) domain names, such as contoso.com.</span></span> <span data-ttu-id="d2889-112">The organization is a container for subscriptions.</span><span class="sxs-lookup"><span data-stu-id="d2889-112">The organization is a container for subscriptions.</span></span>
  
### <a name="subscriptions"></a><span data-ttu-id="d2889-113">구독</span><span class="sxs-lookup"><span data-stu-id="d2889-113">Subscriptions</span></span>

<span data-ttu-id="d2889-114">구독은 하나 혹은 이상의 Microsoft 클라우드 플랫폼 또는 서비스를 사용하기 위한 Microsoft와의 약정이며 사용자 단위 라이선스 요금이나 클라우드 기반 리소스 소비량을 기준으로 요금이 부과됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2889-114">A subscription is an agreement with Microsoft to use one or more Microsoft cloud platforms or services, for which charges accrue based on either a per-user license fee or on cloud-based resource consumption.</span></span> 

- <span data-ttu-id="d2889-115">Microsoft의 SaaS (Software as a Service) 기반 클라우드 서비스 (Microsoft 365 및 Dynamics 365) 최종 사용자 사용권 수수료</span><span class="sxs-lookup"><span data-stu-id="d2889-115">Microsoft's Software as a Service (SaaS)-based cloud offerings (Microsoft 365 and Dynamics 365) charge per-user license fees.</span></span> 
- <span data-ttu-id="d2889-116">Microsoft의 서비스로서의 플랫폼 (PaaS) 및 서비스로서의 인프라 (IaaS) 클라우드 서비스는 (Azure) 클라우드 리소스 소비량을 기반으로 요금을 부과합니다.</span><span class="sxs-lookup"><span data-stu-id="d2889-116">Microsoft's Platform as a Service (PaaS) and Infrastructure as a Service (IaaS) cloud offerings (Azure) charge based on cloud resource consumption.</span></span>
 
<span data-ttu-id="d2889-117">You can also use a trial subscription, but the subscription expires after a specific amount of time or consumption charges.</span><span class="sxs-lookup"><span data-stu-id="d2889-117">You can also use a trial subscription, but the subscription expires after a specific amount of time or consumption charges.</span></span> <span data-ttu-id="d2889-118">You can convert a trial subscription to a paid subscription.</span><span class="sxs-lookup"><span data-stu-id="d2889-118">You can convert a trial subscription to a paid subscription.</span></span>
  
<span data-ttu-id="d2889-119">조직은 다수의 Microsoft의 클라우드 서비스를 구독할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2889-119">Organizations can have multiple subscriptions for Microsoft's cloud offerings.</span></span> <span data-ttu-id="d2889-120">그림 1에는 여러 Microsoft 365 구독, Dynamics 365 구독 및 여러 Azure 구독이 있는 단일 조직이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2889-120">Figure 1 shows a single organization that has multiple Microsoft 365 subscriptions, a Dynamics 365 subscription, and multiple Azure subscriptions.</span></span>

<span data-ttu-id="d2889-121">**그림 1: 여러 개의 조직용 구독 예**</span><span class="sxs-lookup"><span data-stu-id="d2889-121">**Figure 1: Example of multiple subscriptions for an organization**</span></span>

![Microsoft의 클라우드 서비스용 구독이 여러 개 있는 예제 조직입니다.](media/Subscriptions/Subscriptions-Fig1.png)
  
### <a name="licenses"></a><span data-ttu-id="d2889-123">라이선스</span><span class="sxs-lookup"><span data-stu-id="d2889-123">Licenses</span></span>

<span data-ttu-id="d2889-124">Microsoft의 SaaS 클라우드 제품의 경우 라이선스를 통해 특정 사용자 계정이 클라우드 서비스를 사용할 수 있도록 해줍니다.</span><span class="sxs-lookup"><span data-stu-id="d2889-124">For Microsoft's SaaS cloud offerings, a license allows a specific user account to use the services of the cloud offering.</span></span> <span data-ttu-id="d2889-125">구독의 일부로서 구독자에게 고정 월별 요금이 청구됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2889-125">You are charged a fixed monthly fee as part of your subscription.</span></span> <span data-ttu-id="d2889-126">관리자는 구독의 개별 사용자 계정에 라이선스를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="d2889-126">Administrators assign licenses to individual user accounts in the subscription.</span></span> <span data-ttu-id="d2889-127">그림 2의 예를 들어 Contoso Corporation에는 365 Microsoft 365 E5 기능 및 서비스를 사용 하기 위해 최대 100의 개별 사용자 계정에 대 한 100 라이선스가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2889-127">For the example in Figure 2, the Contoso Corporation has a Microsoft 365 E5 subscription with 100 licenses, which allows to up to 100 individual user accounts to use Microsoft 365 E5 features and services.</span></span>
  
<span data-ttu-id="d2889-128">**그림 2: 조직을 위한 SaaS 기반 구독에 포함된 라이선스**</span><span class="sxs-lookup"><span data-stu-id="d2889-128">**Figure 2: Licenses within the SaaS-based subscriptions for an organization**</span></span>

![Microsoft의 SaaS 기반 클라우드 서비스용 구독에 포함된 여러 라이선스 예제입니다.](media/Subscriptions/Subscriptions-Fig2.png)
  
<span data-ttu-id="d2889-130">Azure PaaS 기반 클라우드 서비스의 경우 소프트웨어 라이선스가 서비스 가격에 기본적으로 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2889-130">For Azure PaaS-based cloud services, software licenses are built into the service pricing.</span></span>
  
<span data-ttu-id="d2889-131">For Azure IaaS-based virtual machines, additional licenses to use the software or application installed on a virtual machine image might be required.</span><span class="sxs-lookup"><span data-stu-id="d2889-131">For Azure IaaS-based virtual machines, additional licenses to use the software or application installed on a virtual machine image might be required.</span></span> <span data-ttu-id="d2889-132">Some virtual machine images have licensed versions of software installed and the cost is included in the per-minute rate for the server.</span><span class="sxs-lookup"><span data-stu-id="d2889-132">Some virtual machine images have licensed versions of software installed and the cost is included in the per-minute rate for the server.</span></span> <span data-ttu-id="d2889-133">Examples are the virtual machine images for SQL Server 2014 and SQL Server 2016.</span><span class="sxs-lookup"><span data-stu-id="d2889-133">Examples are the virtual machine images for SQL Server 2014 and SQL Server 2016.</span></span> 
  
<span data-ttu-id="d2889-134">Some virtual machine images have trial versions of applications installed and need additional software application licenses for use beyond the trial period.</span><span class="sxs-lookup"><span data-stu-id="d2889-134">Some virtual machine images have trial versions of applications installed and need additional software application licenses for use beyond the trial period.</span></span> <span data-ttu-id="d2889-135">For example, the SharePoint Server 2016 Trial virtual machine image includes a trial version of SharePoint Server 2016 pre-installed.</span><span class="sxs-lookup"><span data-stu-id="d2889-135">For example, the SharePoint Server 2016 Trial virtual machine image includes a trial version of SharePoint Server 2016 pre-installed.</span></span> <span data-ttu-id="d2889-136">To continue using SharePoint Server 2016 after the trial expiration date, you must purchase a SharePoint Server 2016 license and client licenses from Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d2889-136">To continue using SharePoint Server 2016 after the trial expiration date, you must purchase a SharePoint Server 2016 license and client licenses from Microsoft.</span></span> <span data-ttu-id="d2889-137">These charges are separate from the Azure subscription and the per-minute rate to run the virtual machine still applies.</span><span class="sxs-lookup"><span data-stu-id="d2889-137">These charges are separate from the Azure subscription and the per-minute rate to run the virtual machine still applies.</span></span>
  
### <a name="user-accounts"></a><span data-ttu-id="d2889-138">사용자 계정</span><span class="sxs-lookup"><span data-stu-id="d2889-138">User accounts</span></span>

<span data-ttu-id="d2889-139">모든 Microsoft 클라우드 서비스의 사용자 계정은 사용자 계정 및 그룹이 포함되어 있는 Azure AD (Azure 액티브 디렉터리) 테넌트에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2889-139">User accounts for all of Microsoft's cloud offerings are stored in an Azure Active Directory (Azure AD) tenant, which contains user accounts and groups.</span></span> <span data-ttu-id="d2889-140">Azure AD 테넌트는 Windows server 기반의 서비스인 Azure AD Connect를 사용하여 기존의 AD DS (액티브 디렉터리 도메인 서비스) 계정과 동기화될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2889-140">An Azure AD tenant can be synchronized with your existing Active Directory Domain Services (AD DS) accounts using Azure AD Connect, a Windows server-based service.</span></span> <span data-ttu-id="d2889-141">이를 디렉터리 동기화라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2889-141">This is known as directory synchronization.</span></span>
  
<span data-ttu-id="d2889-142">그림 3은 조직 계정이 포함된 일반적인 Azure 테넌트를 사용하는 조직의 여러 구독 예를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="d2889-142">Figure 3 shows an example of multiple subscriptions of an organization using a common Azure AD tenant that contains the organization's accounts.</span></span>
  
<span data-ttu-id="d2889-143">**그림 3: 동일한 Azure 테넌트를 사용하는 조직의 여러 구독**</span><span class="sxs-lookup"><span data-stu-id="d2889-143">**Figure 3: Multiple subscriptions of an organization that use the same Azure AD tenant**</span></span>

![모두 동일한 Azure 테넌트를 사용하는 여러 개의 구독이 있는 예제 조직입니다.](media/Subscriptions/Subscriptions-Fig3.png)
  
### <a name="tenants"></a><span data-ttu-id="d2889-145">테넌트</span><span class="sxs-lookup"><span data-stu-id="d2889-145">Tenants</span></span>

<span data-ttu-id="d2889-146">SaaS 클라우드 제품의 경우 테 넌 트는 클라우드 서비스를 제공 하는 서버를 소유 하는 지역 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="d2889-146">For SaaS cloud offerings, the tenant is the regional location that houses the servers providing cloud services.</span></span> <span data-ttu-id="d2889-147">예를 들어 Contoso Corporation은 해당 파리 본사의 15000 작업자에 게 Microsoft 365, EMS 및 Dynamics 365 테 넌 트를 호스트 하기 위해 유럽 지역을 선택 했습니다.</span><span class="sxs-lookup"><span data-stu-id="d2889-147">For example, the Contoso Corporation chose the European region to host its Microsoft 365, EMS, and Dynamics 365 tenants for the 15,000 workers in their Paris headquarters.</span></span>
  
<span data-ttu-id="d2889-148">Azure PaaS services and virtual machine-based workloads hosted in Azure IaaS can have tenancy in any Azure datacenter across the world.</span><span class="sxs-lookup"><span data-stu-id="d2889-148">Azure PaaS services and virtual machine-based workloads hosted in Azure IaaS can have tenancy in any Azure datacenter across the world.</span></span> <span data-ttu-id="d2889-149">You specify the Azure datacenter, known as the location, when you create the Azure PaaS app or service or element of an IaaS workload.</span><span class="sxs-lookup"><span data-stu-id="d2889-149">You specify the Azure datacenter, known as the location, when you create the Azure PaaS app or service or element of an IaaS workload.</span></span>
  
<span data-ttu-id="d2889-150">Azure AD 테 넌 트는 계정과 그룹을 포함 하는 Azure AD의 특정 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="d2889-150">An Azure AD tenant is a specific instance of Azure AD containing accounts and groups.</span></span> <span data-ttu-id="d2889-151">Microsoft 365 또는 Dynamics 365의 유료 또는 평가판 구독에는 무료 Azure AD 테 넌 트가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2889-151">Paid or trial subscriptions of Microsoft 365 or Dynamics 365 include a free Azure AD tenant.</span></span> <span data-ttu-id="d2889-152">이 Azure AD 테 넌 트에는 다른 Azure 서비스가 포함 되지 않으며 Azure 평가판 또는 유료 구독과 동일 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d2889-152">This Azure AD tenant does not include other Azure services and is not the same as an Azure trial or paid subscription.</span></span>
  
### <a name="summary-of-the-hierarchy"></a><span data-ttu-id="d2889-153">계층 구조의 요약</span><span class="sxs-lookup"><span data-stu-id="d2889-153">Summary of the hierarchy</span></span>

<span data-ttu-id="d2889-154">간단한 설명은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d2889-154">Here is a quick recap:</span></span>
  
- <span data-ttu-id="d2889-155">하나의 조직에 구독이 여러 개일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2889-155">An organization can have multiple subscriptions</span></span>
    
  - <span data-ttu-id="d2889-156">하나의 구독에 라이선스가 여러 개 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2889-156">A subscription can have multiple licenses</span></span>
    
  - <span data-ttu-id="d2889-157">라이선스를 개별 사용자 계정에 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2889-157">Licenses can be assigned to individual user accounts</span></span>
    
  - <span data-ttu-id="d2889-158">사용자 계정은 Azure AD테넌트에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2889-158">User accounts are stored in an Azure AD tenant</span></span>
    
<span data-ttu-id="d2889-159">조직, 구독, 라이선스 및 사용자 계정의 관계를 보여주는 예제는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d2889-159">Here is an example of the relationship of organizations, subscriptions, licenses, and user accounts:</span></span>
  
- <span data-ttu-id="d2889-160">공용 도메인 이름으로 식별되는 조직</span><span class="sxs-lookup"><span data-stu-id="d2889-160">An organization identified by its public domain name.</span></span>
    
  - <span data-ttu-id="d2889-161">사용자 라이선스가 있는 Microsoft 365 E3 구독</span><span class="sxs-lookup"><span data-stu-id="d2889-161">A Microsoft 365 E3 subscription with user licenses.</span></span>
    
    <span data-ttu-id="d2889-162">사용자 라이선스가 있는 Microsoft 365 E5 구독</span><span class="sxs-lookup"><span data-stu-id="d2889-162">A Microsoft 365 E5 subscription with user licenses.</span></span>
    
    <span data-ttu-id="d2889-163">사용자 라이선스가 있는 Dynamics 365 구독</span><span class="sxs-lookup"><span data-stu-id="d2889-163">A Dynamics 365 subscription with user licenses.</span></span>
    
    <span data-ttu-id="d2889-164">여러 Azure 구독</span><span class="sxs-lookup"><span data-stu-id="d2889-164">Multiple Azure subscriptions.</span></span>
    
  - <span data-ttu-id="d2889-165">일반적인 Azure AD 테넌트에 있는 조직의 사용자 계정</span><span class="sxs-lookup"><span data-stu-id="d2889-165">The organization's user accounts in a common Azure AD tenant.</span></span>
    
<span data-ttu-id="d2889-166">다수의 Microsoft 클라우드 서비스의 구독은 공통 ID제공자 역할을 하는 동일한 Azure AD 테넌트를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2889-166">Multiple Microsoft cloud offering subscriptions can use the same Azure AD tenant that acts as a common identity provider.</span></span> <span data-ttu-id="d2889-167">온-프레미스 AD DS의 동기화된 계정을 포함하는 중앙 Azure AD 테넌트는 조직에 클라우드 기반의 서비스로서의 ID (IDaaS)를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d2889-167">A central Azure AD tenant that contains the synchronized accounts of your on-premises AD DS provides cloud-based Identity as a Service (IDaaS) for your organization.</span></span> 
  
<span data-ttu-id="d2889-168">**그림 4: 조직에 대한 동기화된 온-프레미스 계정 및 IDaaS**</span><span class="sxs-lookup"><span data-stu-id="d2889-168">**Figure 4: Synchronized on-premises accounts and IDaaS for an organization**</span></span>

![조직에 대한 IDaaS(Identity as a Service)입니다.](media/Subscriptions/Subscriptions-Fig4.png)
  
<span data-ttu-id="d2889-170">Figure 4 shows how a common Azure AD tenant is used by Microsoft's SaaS cloud offerings, Azure PaaS apps, and virtual machines in Azure IaaS that use Azure AD Domain Services.</span><span class="sxs-lookup"><span data-stu-id="d2889-170">Figure 4 shows how a common Azure AD tenant is used by Microsoft's SaaS cloud offerings, Azure PaaS apps, and virtual machines in Azure IaaS that use Azure AD Domain Services.</span></span> <span data-ttu-id="d2889-171">Azure AD Connect synchronizes the on-premises AD DS forest with the Azure AD tenant.</span><span class="sxs-lookup"><span data-stu-id="d2889-171">Azure AD Connect synchronizes the on-premises AD DS forest with the Azure AD tenant.</span></span>
  
## <a name="combining-subscriptions-for-multiple-microsoft-cloud-offerings"></a><span data-ttu-id="d2889-172">여러 Microsoft 클라우드 서비스에 대한 구독 결합</span><span class="sxs-lookup"><span data-stu-id="d2889-172">Combining subscriptions for multiple Microsoft cloud offerings</span></span>

<span data-ttu-id="d2889-173">다음 표에서는 한 가지 유형의 클라우드 서비스에 대한 구독이 이미 있고(첫 번째 열 아래쪽에 레이블 참조), 다른 클라우드 서비스에 대한 구독을 추가하는 경우(열 가로 방향으로) 여러 Microsoft 클라우드 서비스를 결합하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d2889-173">The following table describes how you can combine multiple Microsoft cloud offerings based on already having a subscription for one type of cloud offering (the labels going down the first column) and adding a subscription for a different cloud offering (going across the columns).</span></span>
  
||<span data-ttu-id="d2889-174">**Microsoft 365**</span><span class="sxs-lookup"><span data-stu-id="d2889-174">**Microsoft 365**</span></span>|<span data-ttu-id="d2889-175">**Azure**</span><span class="sxs-lookup"><span data-stu-id="d2889-175">**Azure**</span></span>|<span data-ttu-id="d2889-176">**Dynamics 365**</span><span class="sxs-lookup"><span data-stu-id="d2889-176">**Dynamics 365**</span></span>|
|:-----|:-----|:-----|:-----|:-----|
|<span data-ttu-id="d2889-177">**Microsoft 365**</span><span class="sxs-lookup"><span data-stu-id="d2889-177">**Microsoft 365**</span></span> <br/> |<span data-ttu-id="d2889-178">해당 없음</span><span class="sxs-lookup"><span data-stu-id="d2889-178">NA</span></span>  <br/> |<span data-ttu-id="d2889-179">Azure Portal에서 조직에 Azure 구독을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d2889-179">You add an Azure subscription to your organization from the Azure portal.</span></span>  <br/> |<span data-ttu-id="d2889-180">Microsoft 365 관리 센터에서 조직에 Dynamics 365 구독을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d2889-180">You add a Dynamics 365 subscription to your organization from the Microsoft 365 admin center.</span></span>  <br/> |
|<span data-ttu-id="d2889-181">**Azure**</span><span class="sxs-lookup"><span data-stu-id="d2889-181">**Azure**</span></span> <br/> |<span data-ttu-id="d2889-182">조직에 Microsoft 365 구독을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2889-182">You add a Microsoft 365 subscription to your organization.</span></span>  <br/> |<span data-ttu-id="d2889-183">해당 없음</span><span class="sxs-lookup"><span data-stu-id="d2889-183">NA</span></span>  <br/> |<span data-ttu-id="d2889-184">조직에 Dynamics 365 구독을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d2889-184">You add a Dynamics 365 subscription to your organization.</span></span>  <br/> |
|<span data-ttu-id="d2889-185">**Dynamics 365**</span><span class="sxs-lookup"><span data-stu-id="d2889-185">**Dynamics 365**</span></span> <br/> |<span data-ttu-id="d2889-186">조직에 Microsoft 365 구독을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2889-186">You add a Microsoft 365 subscription to your organization.</span></span>  <br/> |<span data-ttu-id="d2889-187">Azure Portal에서 조직에 Azure 구독을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d2889-187">You add an Azure subscription to your organization from the Azure portal.</span></span>  <br/> |<span data-ttu-id="d2889-188">해당 없음</span><span class="sxs-lookup"><span data-stu-id="d2889-188">NA</span></span>  <br/> |
   
<span data-ttu-id="d2889-189">관리 센터를 사용하면 Microsoft SaaS 기반 서비스를 위해 조직에 구독을 쉽게 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2889-189">An easy way to add subscriptions to your organization for Microsoft SaaS-based services is through the admin center:</span></span>
  
1. <span data-ttu-id="d2889-190">글로벌 관리자 계정을 사용하여 Microsoft 365 관리 센터([https://admin.microsoft.com](https://admin.microsoft.com))에 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="d2889-190">Sign in to the Microsoft 365 admin center ([https://admin.microsoft.com](https://admin.microsoft.com)) with your global administrator account.</span></span>
    
2. <span data-ttu-id="d2889-191">**관리 센터** 홈페이지의 왼쪽 탐색 창에서 **청구**를 클릭하고 **서비스 구매**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d2889-191">From the left navigation of the **Admin center** home page, click **Billing**, and then **Purchase services**.</span></span>
    
3. <span data-ttu-id="d2889-192">**서비스 구매** 페이지에서 새 구독을 구입합니다.</span><span class="sxs-lookup"><span data-stu-id="d2889-192">On the **Purchase services** page, purchase your new subscriptions.</span></span>
    
<span data-ttu-id="d2889-193">관리 센터는 SaaS 기반 클라우드 서비스에 대 한 새 구독에 대 한 Microsoft 365 구독의 조직 및 Azure 테 넌 트를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2889-193">The admin center assigns the organization and Azure AD tenant of your Microsoft 365 subscription to the new subscriptions for SaaS-based cloud offerings.</span></span>
  
<span data-ttu-id="d2889-194">Microsoft 365 구독으로 동일한 조직 및 Azure AD 테 넌 트를 사용 하 여 Azure 구독을 추가 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2889-194">To add an Azure subscription with the same organization and Azure AD tenant as your Microsoft 365 subscription:</span></span>
  
1. <span data-ttu-id="d2889-195">[https://portal.azure.com](https://portal.azure.com)Microsoft 365 전역 관리자 계정을 사용 하 여 Azure portal ()에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2889-195">Sign in to the Azure portal ([https://portal.azure.com](https://portal.azure.com)) with your Microsoft 365 global administrator account.</span></span>
    
2. <span data-ttu-id="d2889-196">왼쪽 탐색 모음에서 **구독**을 클릭하고 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d2889-196">In the left navigation, click **Subscriptions**, and then click **Add**.</span></span>
    
3. <span data-ttu-id="d2889-197">**구독 추가** 페이지에서 서비스를 선택하고 결제 정보 및 계약을 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="d2889-197">On the **Add subscription** page, select an offer and complete the payment information and agreement.</span></span>
    
<span data-ttu-id="d2889-198">Azure 및 Microsoft 365 구독을 별도로 구매한 경우 Azure 구독에서 Microsoft 365 Azure AD 테 넌 트에 액세스 하려면의 지침에 따라 [Azure Active Directory 테 넌 트에 기존 azure 구독을 추가](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-how-subscriptions-associated-directory)합니다 .를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d2889-198">If you purchased Azure and Microsoft 365 subscriptions separately and want to access the Microsoft 365 Azure AD tenant from your Azure subscription, see the instructions in [Add an existing Azure subscription to your Azure Active Directory tenant](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-how-subscriptions-associated-directory).</span></span>
 
## <a name="see-also"></a><span data-ttu-id="d2889-199">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d2889-199">See also</span></span>

[<span data-ttu-id="d2889-200">Microsoft 클라우드 IT 아키텍처 리소스</span><span class="sxs-lookup"><span data-stu-id="d2889-200">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)
  
[<span data-ttu-id="d2889-201">Exchange, SharePoint, 비즈니스용 Skype 및 Lync에 대한 아키텍처 모델</span><span class="sxs-lookup"><span data-stu-id="d2889-201">Architectural models for SharePoint, Exchange, Skype for Business, and Lync</span></span>](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[<span data-ttu-id="d2889-202">하이브리드 솔루션</span><span class="sxs-lookup"><span data-stu-id="d2889-202">Hybrid solutions</span></span>](hybrid-solutions.md)

## <a name="next-step"></a><span data-ttu-id="d2889-203">다음 단계</span><span class="sxs-lookup"><span data-stu-id="d2889-203">Next step</span></span>

[<span data-ttu-id="d2889-204">Microsoft 365 네트워크 연결 평가</span><span class="sxs-lookup"><span data-stu-id="d2889-204">Assessing Microsoft 365 network connectivity</span></span>](assessing-network-connectivity.md)
  
