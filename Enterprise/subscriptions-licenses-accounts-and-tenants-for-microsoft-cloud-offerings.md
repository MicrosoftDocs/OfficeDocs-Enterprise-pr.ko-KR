---
title: Microsoft 클라우드 제품용 구독, 라이선스, 계정 및 테넌트
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/08/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Architecture
ms.assetid: c720cffc-f9b5-4f43-9100-422f86a1027c
description: '요약: Microsoft의 클라우드 제품에서 조직, 구독, 라이선스, 사용자 계정 및 테넌트의 관계를 이해합니다.'
ms.openlocfilehash: c6c6aa02701d47c5818f66d2f0e499e7a85cb902
ms.sourcegitcommit: 546080809d4f8ee4954943738906eec6c9bac1d8
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/21/2019
ms.locfileid: "37616151"
---
# <a name="subscriptions-licenses-accounts-and-tenants-for-microsofts-cloud-offerings"></a><span data-ttu-id="f7428-103">Microsoft 클라우드 제품용 구독, 라이선스, 계정 및 테넌트</span><span class="sxs-lookup"><span data-stu-id="f7428-103">Subscriptions, licenses, accounts, and tenants for Microsoft's cloud offerings</span></span>

 <span data-ttu-id="f7428-104">**요약:** Microsoft의 클라우드 제품에서 조직, 구독, 라이선스, 사용자 계정 및 테넌트의 관계를 이해합니다.</span><span class="sxs-lookup"><span data-stu-id="f7428-104">**Summary:** Understand the relationships of organizations, subscriptions, licenses, user accounts, and tenants across Microsoft's cloud offerings.</span></span>
  
<span data-ttu-id="f7428-105">Microsoft는 해당 클라우드 제품 간에 일관된 ID 사용 및 요금 청구를 위해 조직, 구독, 라이선스 및 사용자 계정을 포함하는 계층 구조를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f7428-105">Microsoft provides a hierarchy of organizations, subscriptions, licenses, and user accounts for consistent use of identities and billing across its cloud offerings:</span></span>
  
- <span data-ttu-id="f7428-106">Microsoft Office 365</span><span class="sxs-lookup"><span data-stu-id="f7428-106">Microsoft Office 365</span></span>
- <span data-ttu-id="f7428-107">Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="f7428-107">Microsoft Azure</span></span>
- <span data-ttu-id="f7428-108">Microsoft Intune 및 EMS(Enterprise Mobility + Security)</span><span class="sxs-lookup"><span data-stu-id="f7428-108">Microsoft Intune and the Enterprise Mobility + Security (EMS)</span></span>
- <span data-ttu-id="f7428-109">Microsoft Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="f7428-109">Microsoft Dynamics 365</span></span>

<span data-ttu-id="f7428-110">[Microsoft 365](https://docs.microsoft.com/microsoft-365/)는 Office 365, EMS 및 Windows 10 Enterprise를 단일 구독 및 통합된 서비스 세트로 결합합니다.</span><span class="sxs-lookup"><span data-stu-id="f7428-110">[Microsoft 365](https://docs.microsoft.com/microsoft-365/) combines Office 365, EMS, and Windows 10 Enterprise into a single subscription and set of integrated services.</span></span>

## <a name="elements-of-the-hierarchy"></a><span data-ttu-id="f7428-111">계층 구조의 요소</span><span class="sxs-lookup"><span data-stu-id="f7428-111">Elements of the hierarchy</span></span>

<span data-ttu-id="f7428-112">다음은 계층 구조의 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="f7428-112">Here are the elements of the hierarchy:</span></span>
  
### <a name="organization"></a><span data-ttu-id="f7428-113">조직</span><span class="sxs-lookup"><span data-stu-id="f7428-113">Organization</span></span>

<span data-ttu-id="f7428-p101">조직은 Microsoft 클라우드 서비스를 사용하는 비즈니스 엔터티를 나타내며, 일반적으로 하나 이상의 공용 DNS(Domain Name System) 도메인 이름(예: contoso.com)으로 식별됩니다. 조직은 구독을 위한 컨테이너입니다.</span><span class="sxs-lookup"><span data-stu-id="f7428-p101">An organization represents a business entity that is using Microsoft cloud offerings, typically identified by one or more public Domain Name System (DNS) domain names, such as contoso.com. The organization is a container for subscriptions.</span></span>
  
### <a name="subscriptions"></a><span data-ttu-id="f7428-116">구독</span><span class="sxs-lookup"><span data-stu-id="f7428-116">Subscriptions</span></span>

<span data-ttu-id="f7428-117">구독은 하나 혹은 이상의 Microsoft 클라우드 플랫폼 또는 서비스를 사용하기 위한 Microsoft와의 약정이며 사용자 단위 라이선스 요금이나 클라우드 기반 리소스 소비량을 기준으로 요금이 부과됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7428-117">A subscription is an agreement with Microsoft to use one or more Microsoft cloud platforms or services, for which charges accrue based on either a per-user license fee or on cloud-based resource consumption.</span></span> 

- <span data-ttu-id="f7428-118">Microsoft의 서비스로서의 소프트웨어 (SaaS) 기반 클라우드 서비스는 (Office 365, Intune/EMS, Dynamics 365) 사용자 단위 라이선스 요금을 부과합니다.</span><span class="sxs-lookup"><span data-stu-id="f7428-118">Microsoft's Software as a Service (SaaS)-based cloud offerings (Office 365, Intune/EMS, and Dynamics 365) charge per-user license fees.</span></span> 
- <span data-ttu-id="f7428-119">Microsoft의 서비스로서의 플랫폼 (PaaS) 및 서비스로서의 인프라 (IaaS) 클라우드 서비스는 (Azure) 클라우드 리소스 소비량을 기반으로 요금을 부과합니다.</span><span class="sxs-lookup"><span data-stu-id="f7428-119">Microsoft's Platform as a Service (PaaS) and Infrastructure as a Service (IaaS) cloud offerings (Azure) charge based on cloud resource consumption.</span></span>
 
<span data-ttu-id="f7428-p102">평가판 구독을 사용할 수도 있지만, 일정 기간이 지나거나 이용 요금이 다 사용된 후에는 구독이 만료됩니다. 평가판 구독을 유료 구독으로 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7428-p102">You can also use a trial subscription, but the subscription expires after a specific amount of time or consumption charges. You can convert a trial subscription to a paid subscription.</span></span>
  
<span data-ttu-id="f7428-122">조직은 다수의 Microsoft의 클라우드 서비스를 구독할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7428-122">Organizations can have multiple subscriptions for Microsoft's cloud offerings.</span></span> <span data-ttu-id="f7428-123">그림 1에서는 여러 개의 Office 365 구독, 1개의 Intune 구독, Dynamics 365 구독 및 여러 개의 Azure 구독이 있는 단일 조직을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="f7428-123">Figure 1 shows a single organization that has multiple Office 365 subscriptions, an Intune subscription, a Dynamics 365 subscription, and multiple Azure subscriptions.</span></span>

<span data-ttu-id="f7428-124">**그림 1: 여러 개의 조직용 구독 예**</span><span class="sxs-lookup"><span data-stu-id="f7428-124">**Figure 1: Example of multiple subscriptions for an organization**</span></span>

![Microsoft의 클라우드 서비스용 구독이 여러 개 있는 예제 조직입니다.](media/Subscriptions/Subscriptions-Fig1.png)

  
### <a name="licenses"></a><span data-ttu-id="f7428-126">라이선스</span><span class="sxs-lookup"><span data-stu-id="f7428-126">Licenses</span></span>

<span data-ttu-id="f7428-127">Microsoft의 SaaS 클라우드 제품의 경우 라이선스를 통해 특정 사용자 계정이 클라우드 서비스를 사용할 수 있도록 해줍니다.</span><span class="sxs-lookup"><span data-stu-id="f7428-127">For Microsoft's SaaS cloud offerings, a license allows a specific user account to use the services of the cloud offering.</span></span> <span data-ttu-id="f7428-128">구독의 일부로서 구독자에게 고정 월별 요금이 청구됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7428-128">You are charged a fixed monthly fee as part of your subscription.</span></span> <span data-ttu-id="f7428-129">관리자는 구독의 개별 사용자 계정에 라이선스를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="f7428-129">Administrators assign licenses to individual user accounts in the subscription.</span></span> <span data-ttu-id="f7428-130">예를 들어 그림 2에서 Contoso Corporation는 office 365 Enterprise E5를 구독하고 100개의 라이선스를 보유하고 있어 최대 100개의 개별 사용자 계정을 사용하여 Office 365 Enterprise E5의 기능 및 서비스를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7428-130">For the example in Figure 2, the Contoso Corporation has an Office 365 Enterprise E5 subscription with 100 licenses, which allows to up to 100 individual user accounts to use Office 365 Enterprise E5 features and services.</span></span>
  
<span data-ttu-id="f7428-131">**그림 2: 조직을 위한 SaaS 기반 구독에 포함된 라이선스**</span><span class="sxs-lookup"><span data-stu-id="f7428-131">**Figure 2: Licenses within the SaaS-based subscriptions for an organization**</span></span>

![Microsoft의 SaaS 기반 클라우드 서비스용 구독에 포함된 여러 라이선스 예제입니다.](media/Subscriptions/Subscriptions-Fig2.png)
  
<span data-ttu-id="f7428-133">Azure PaaS 기반 클라우드 서비스의 경우 소프트웨어 라이선스가 서비스 가격에 기본적으로 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7428-133">For Azure PaaS-based cloud services, software licenses are built into the service pricing.</span></span>
  
<span data-ttu-id="f7428-p105">Azure IaaS 기반 가상 머신의 경우 가상 머신 이미지에 설치되어 있는 소프트웨어 또는 이미지를 사용하기 위한 추가 라이선스가 필요할 수도 있습니다. 일부 가상 머신 이미지는 설치된 소프트웨어의 라이선스 버전을 가지며 서버에 대한 분당 요금에 해당 요금이 포함됩니다. 제공된 예제는 SQL Server 2014 및 SQL Server 2016에 대한 가상 머신 이미지입니다.</span><span class="sxs-lookup"><span data-stu-id="f7428-p105">For Azure IaaS-based virtual machines, additional licenses to use the software or application installed on a virtual machine image might be required. Some virtual machine images have licensed versions of software installed and the cost is included in the per-minute rate for the server. Examples are the virtual machine images for SQL Server 2014 and SQL Server 2016.</span></span> 
  
<span data-ttu-id="f7428-p106">일부 가상 머신 이미지에는 평가판 버전의 응용 프로그램이 설치되어 있고 평가 기간 이후에도 사용하려면 추가 소프트웨어 응용 프로그램 라이선스가 필요합니다. 예를 들어, SharePoint Server 2016 평가판 가상 머신 이미지에는 사전 설치된 SharePoint Server 2016 평가판이 포함되어 있습니다. 평가판 만료일 이후에도 SharePoint Server 2016을 계속 사용하려면 Microsoft에서 SharePoint Server 2016 라이선스 및 클라이언트 라이선스를 구입해야 합니다. 이러한 청구 금액은 Azure 구독과는 별개이며, 가상 머신을 실행하는 분당 요금은 여전히 부과됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7428-p106">Some virtual machine images have trial versions of applications installed and need additional software application licenses for use beyond the trial period. For example, the SharePoint Server 2016 Trial virtual machine image includes a trial version of SharePoint Server 2016 pre-installed. To continue using SharePoint Server 2016 after the trail expiration date, you must purchase a SharePoint Server 2016 license and client licenses from Microsoft. These charges are separate from the Azure subscription and the per-minute rate to run the virtual machine still applies.</span></span>
  
### <a name="user-accounts"></a><span data-ttu-id="f7428-141">사용자 계정</span><span class="sxs-lookup"><span data-stu-id="f7428-141">User accounts</span></span>

<span data-ttu-id="f7428-142">모든 Microsoft 클라우드 서비스의 사용자 계정은 사용자 계정 및 그룹이 포함되어 있는 Azure AD (Azure 액티브 디렉터리) 테넌트에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7428-142">User accounts for all of Microsoft's cloud offerings are stored in an Azure Active Directory (Azure AD) tenant, which contains user accounts and groups.</span></span> <span data-ttu-id="f7428-143">Azure AD 테넌트는 Windows server 기반의 서비스인 Azure AD Connect를 사용하여 기존의 AD DS (액티브 디렉터리 도메인 서비스) 계정과 동기화될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7428-143">An Azure AD tenant can be synchronized with your existing Active Directory Domain Services (AD DS) accounts using Azure AD Connect, a Windows server-based service.</span></span> <span data-ttu-id="f7428-144">이를 디렉터리 동기화 (DirSync) 라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7428-144">This is known as directory synchronization (DirSync).</span></span>
  
<span data-ttu-id="f7428-145">그림 3은 조직 계정이 포함된 일반적인 Azure 테넌트를 사용하는 조직의 여러 구독 예를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="f7428-145">Figure 3 shows an example of multiple subscriptions of an organization using a common Azure AD tenant that contains the organization's accounts.</span></span>
  
<span data-ttu-id="f7428-146">**그림 3: 동일한 Azure 테넌트를 사용하는 조직의 여러 구독**</span><span class="sxs-lookup"><span data-stu-id="f7428-146">**Figure 3: Multiple subscriptions of an organization that use the same Azure AD tenant**</span></span>

![모두 동일한 Azure 테넌트를 사용하는 여러 개의 구독이 있는 예제 조직입니다.](media/Subscriptions/Subscriptions-Fig3.png)
  
### <a name="tenants"></a><span data-ttu-id="f7428-148">테넌트</span><span class="sxs-lookup"><span data-stu-id="f7428-148">Tenants</span></span>

<span data-ttu-id="f7428-p108">SaaS 클라우드 제품의 경우 테넌트는 클라우드 서비스를 제공하는 서버가 보관된 지역 위치입니다. 예를 들어, Contoso Corporation은 파리 본사에 있는 15,000명의 근로자를 위해 유럽 지역에서 Office 365, EMS 및 Dynamics 365 테넌트를 호스트하도록 선택했습니다.</span><span class="sxs-lookup"><span data-stu-id="f7428-p108">For SaaS cloud offerings, the tenant is the regional location that houses the servers providing cloud services. For example, the Contoso Corporation chose the European region to host its Office 365, EMS, and Dynamics 365 tenants for the 15,000 workers in their Paris headquarters.</span></span>
  
<span data-ttu-id="f7428-p109">Azure IaaS에 호스트된 Azure PaaS 서비스 및 가상 머신 기반 워크로드는 전 세계의 모든 Azure 데이터 센터에서 테넌시를 둘 수 있습니다. Azure PaaS 앱 또는 서비스를 만들 때는 위치로 사용되고, IaaS 워크로드의 요소로도 알려진 Azure 데이터 센터를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7428-p109">Azure PaaS services and virtual machine-based workloads hosted in Azure IaaS can have tenancy in any Azure datacenter across the world. You specify the Azure datacenter, known as the location, when you create the Azure PaaS app or service or element of an IaaS workload.</span></span>
  
<span data-ttu-id="f7428-p110">Azure AD 테넌트는 계정 및 그룹에 포함된 Azure AD의 특정 인스턴스입니다. Office 365, Dynamics 365 또는 Intune/EMS의 유료 또는 평가판 구독에는 무료 Azure AD 테넌트가 포함되어 있습니다. 이 Azure AD 테넌트는 다른 Azure 서비스를 포함하지 않으며, Azure 평가판 또는 유료 구독과 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="f7428-p110">An Azure AD tenant is a specific instance of Azure AD containing accounts and groups. Paid or trial subscriptions of Office 365, Dynamics 365, or Intune/EMS include a free Azure AD tenant. This Azure AD tenant does not include other Azure services and is not the same as an Azure trial or paid subscription.</span></span>
  
### <a name="summary-of-the-hierarchy"></a><span data-ttu-id="f7428-156">계층 구조의 요약</span><span class="sxs-lookup"><span data-stu-id="f7428-156">Summary of the hierarchy</span></span>

<span data-ttu-id="f7428-157">간단한 설명은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f7428-157">Here is a quick recap:</span></span>
  
- <span data-ttu-id="f7428-158">하나의 조직에 구독이 여러 개일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7428-158">An organization can have multiple subscriptions</span></span>
    
  - <span data-ttu-id="f7428-159">하나의 구독에 라이선스가 여러 개 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7428-159">A subscription can have multiple licenses</span></span>
    
  - <span data-ttu-id="f7428-160">라이선스를 개별 사용자 계정에 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7428-160">Licenses can be assigned to individual user accounts</span></span>
    
  - <span data-ttu-id="f7428-161">사용자 계정은 Azure AD테넌트에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7428-161">User accounts are stored in an Azure AD tenant</span></span>
    
<span data-ttu-id="f7428-162">조직, 구독, 라이선스 및 사용자 계정의 관계를 보여주는 예제는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f7428-162">Here is an example of the relationship of organizations, subscriptions, licenses, and user accounts:</span></span>
  
- <span data-ttu-id="f7428-163">공용 도메인 이름으로 식별되는 조직</span><span class="sxs-lookup"><span data-stu-id="f7428-163">An organization identified by its public domain name.</span></span>
    
  - <span data-ttu-id="f7428-164">사용자 라이선스가 있는 Office 365 Enterprise E3 구독</span><span class="sxs-lookup"><span data-stu-id="f7428-164">An Office 365 Enterprise E3 subscription with user licenses.</span></span>
    
    <span data-ttu-id="f7428-165">사용자 라이선스가 있는 Office 365 Enterprise E5 구독</span><span class="sxs-lookup"><span data-stu-id="f7428-165">An Office 365 Enterprise E5 subscription with user licenses.</span></span>
    
    <span data-ttu-id="f7428-166">사용자 라이선스가 있는 EMS 구독</span><span class="sxs-lookup"><span data-stu-id="f7428-166">An EMS subscription with user licenses.</span></span>
    
    <span data-ttu-id="f7428-167">사용자 라이선스가 있는 Dynamics 365 구독</span><span class="sxs-lookup"><span data-stu-id="f7428-167">A Dynamics 365 subscription with user licenses.</span></span>
    
    <span data-ttu-id="f7428-168">여러 Azure 구독</span><span class="sxs-lookup"><span data-stu-id="f7428-168">Multiple Azure subscriptions.</span></span>
    
  - <span data-ttu-id="f7428-169">일반적인 Azure AD 테넌트에 있는 조직의 사용자 계정</span><span class="sxs-lookup"><span data-stu-id="f7428-169">The organization's user accounts in a common Azure AD tenant.</span></span>
    
<span data-ttu-id="f7428-170">다수의 Microsoft 클라우드 서비스의 구독은 공통 ID제공자 역할을 하는 동일한 Azure AD 테넌트를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7428-170">Multiple Microsoft cloud offering subscriptions can use the same Azure AD tenant that acts as a common identity provider.</span></span> <span data-ttu-id="f7428-171">온-프레미스 AD DS의 동기화된 계정을 포함하는 중앙 Azure AD 테넌트는 조직에 클라우드 기반의 서비스로서의 ID (IDaaS)를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f7428-171">A central Azure AD tenant that contains the synchronized accounts of your on-premises AD DS provides cloud-based Identity as a Service (IDaaS) for your organization.</span></span> 
  
<span data-ttu-id="f7428-172">**그림 4: 조직에 대한 동기화된 온-프레미스 계정 및 IDaaS**</span><span class="sxs-lookup"><span data-stu-id="f7428-172">**Figure 4: Synchronized on-premises accounts and IDaaS for an organization**</span></span>

![조직에 대한 IDaaS(Identity as a Service)입니다.](media/Subscriptions/Subscriptions-Fig4.png)
  
<span data-ttu-id="f7428-p112">그림 4는 일반적인 Azure AD 테넌트가 Azure AD Domains Services를 사용하는 Microsoft의 SaaS 클라우드 서비스, Azure PaaS 앱 및 Azure IaaS의 가상 머신에서 사용되는 방법을 보여 줍니다. Azure AD Connect는 온-프레미스 AD DS(Active Directory Domain Services) 포리스트를 Azure AD 테넌트와 동기화합니다.</span><span class="sxs-lookup"><span data-stu-id="f7428-p112">Figure 4 shows how a common Azure AD tenant is used by Microsoft's SaaS cloud offerings, Azure PaaS apps, and virtual machines in Azure IaaS that use Azure AD Domain Services. Azure AD Connect synchronizes the on-premises AD DS forest with the Azure AD tenant.</span></span>
  
## <a name="combining-subscriptions-for-multiple-microsoft-cloud-offerings"></a><span data-ttu-id="f7428-176">여러 Microsoft 클라우드 서비스에 대한 구독 결합</span><span class="sxs-lookup"><span data-stu-id="f7428-176">Combining subscriptions for multiple Microsoft cloud offerings</span></span>

<span data-ttu-id="f7428-177">다음 표에서는 한 가지 유형의 클라우드 서비스에 대한 구독이 이미 있고(첫 번째 열 아래쪽에 레이블 참조), 다른 클라우드 서비스에 대한 구독을 추가하는 경우(열 가로 방향으로) 여러 Microsoft 클라우드 서비스를 결합하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f7428-177">The following table describes how you can combine multiple Microsoft cloud offerings based on already having a subscription for one type of cloud offering (the labels going down the first column) and adding a subscription for a different cloud offering (going across the columns).</span></span>
  
||<span data-ttu-id="f7428-178">**Office 365**</span><span class="sxs-lookup"><span data-stu-id="f7428-178">**Office 365**</span></span>|<span data-ttu-id="f7428-179">**Azure**</span><span class="sxs-lookup"><span data-stu-id="f7428-179">**Azure**</span></span>|<span data-ttu-id="f7428-180">**Intune/EMS**</span><span class="sxs-lookup"><span data-stu-id="f7428-180">**Intune/EMS**</span></span>|<span data-ttu-id="f7428-181">**Dynamics 365**</span><span class="sxs-lookup"><span data-stu-id="f7428-181">**Dynamics 365**</span></span>|
|:-----|:-----|:-----|:-----|:-----|
|<span data-ttu-id="f7428-182">**Office 365**</span><span class="sxs-lookup"><span data-stu-id="f7428-182">**Office 365**</span></span> <br/> |<span data-ttu-id="f7428-183">해당 없음</span><span class="sxs-lookup"><span data-stu-id="f7428-183">NA</span></span>  <br/> |<span data-ttu-id="f7428-184">Azure Portal에서 조직에 Azure 구독을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f7428-184">You add an Azure subscription to your organization from the Azure portal.</span></span>  <br/> |<span data-ttu-id="f7428-185">Microsoft 365 관리 센터에서 조직에 Intune/EMS 구독을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f7428-185">You add an Intune/EMS subscription to your organization from the Microsoft 365 admin center.</span></span>  <br/> |<span data-ttu-id="f7428-186">Microsoft 365 관리 센터에서 조직에 Dynamics 365 구독을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f7428-186">You add a Dynamics 365 subscription to your organization from the Microsoft 365 admin center.</span></span>  <br/> |
|<span data-ttu-id="f7428-187">**Azure**</span><span class="sxs-lookup"><span data-stu-id="f7428-187">**Azure**</span></span> <br/> |<span data-ttu-id="f7428-188">조직에 Office 365 구독을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f7428-188">You add an Office 365 subscription to your organization.</span></span>  <br/> |<span data-ttu-id="f7428-189">해당 없음</span><span class="sxs-lookup"><span data-stu-id="f7428-189">NA</span></span>  <br/> |<span data-ttu-id="f7428-190">조직에 Intune/EMS 구독을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f7428-190">You add an Intune/EMS subscription to your organization.</span></span>  <br/> |<span data-ttu-id="f7428-191">조직에 Dynamics 365 구독을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f7428-191">You add a Dynamics 365 subscription to your organization.</span></span>  <br/> |
|<span data-ttu-id="f7428-192">**Intune/EMS**</span><span class="sxs-lookup"><span data-stu-id="f7428-192">**Intune/EMS**</span></span> <br/> |<span data-ttu-id="f7428-193">조직에 Office 365 구독을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f7428-193">You add an Office 365 subscription to your organization.</span></span>  <br/> |<span data-ttu-id="f7428-194">Azure Portal에서 조직에 Azure 구독을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f7428-194">You add an Azure subscription to your organization from the Azure portal.</span></span>  <br/> |<span data-ttu-id="f7428-195">해당 없음</span><span class="sxs-lookup"><span data-stu-id="f7428-195">NA</span></span>  <br/> |<span data-ttu-id="f7428-196">조직에 Dynamics 365 구독을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f7428-196">You add a Dynamics 365 subscription to your organization.</span></span>  <br/> |
|<span data-ttu-id="f7428-197">**Dynamics 365**</span><span class="sxs-lookup"><span data-stu-id="f7428-197">**Dynamics 365**</span></span> <br/> |<span data-ttu-id="f7428-198">조직에 Office 365 구독을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f7428-198">You add an Office 365 subscription to your organization.</span></span>  <br/> |<span data-ttu-id="f7428-199">Azure Portal에서 조직에 Azure 구독을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f7428-199">You add an Azure subscription to your organization from the Azure portal.</span></span>  <br/> |<span data-ttu-id="f7428-200">조직에 Intune/EMS 구독을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f7428-200">You add an Intune/EMS subscription to your organization.</span></span>  <br/> |<span data-ttu-id="f7428-201">해당 없음</span><span class="sxs-lookup"><span data-stu-id="f7428-201">NA</span></span>  <br/> |
   
<span data-ttu-id="f7428-202">관리 센터를 사용하면 Microsoft SaaS 기반 서비스를 위해 조직에 구독을 쉽게 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7428-202">An easy way to add subscriptions to your organization for Microsoft SaaS-based services is through the admin center:</span></span>
  
1. <span data-ttu-id="f7428-203">글로벌 관리자 계정을 사용하여 Microsoft 365 관리 센터([https://admin.microsoft.com](https://admin.microsoft.com))에 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="f7428-203">Sign in to the Microsoft 365 admin center ([https://admin.microsoft.com](https://admin.microsoft.com)) with your global administrator account.</span></span>
    
2. <span data-ttu-id="f7428-204">**관리 센터** 홈페이지의 왼쪽 탐색 창에서 **청구**를 클릭하고 **서비스 구매**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f7428-204">From the left navigation of the **Admin center** home page, click **Billing**, and then **Purchase services**.</span></span>
    
3. <span data-ttu-id="f7428-205">**서비스 구매** 페이지에서 새 구독을 구입합니다.</span><span class="sxs-lookup"><span data-stu-id="f7428-205">On the **Purchase services** page, purchase your new subscriptions.</span></span>
    
<span data-ttu-id="f7428-206">관리 센터는 SaaS 기반 클라우드 서비스에 대한 새 구독에 Office 365 구독의 조직 및 Azure 테넌트를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="f7428-206">The admin center assigns the organization and Azure AD tenant of your Office 365 subscription to the new subscriptions for SaaS-based cloud offerings.</span></span>
  
<span data-ttu-id="f7428-207">Office 365 구독과 동일한 조직 및 Azure 테넌트를 갖는 Azure 구독을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="f7428-207">To add an Azure subscription with the same organization and Azure AD tenant as your Office 365 subscription:</span></span>
  
1. <span data-ttu-id="f7428-208">Office 365 전역 관리자 계정을 사용하여 Azure Portal 포털([https://portal.azure.com](https://portal.azure.com))에 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="f7428-208">Sign in to the Azure portal ([https://portal.azure.com](https://portal.azure.com)) with your Office 365 global administrator account.</span></span>
    
2. <span data-ttu-id="f7428-209">왼쪽 탐색 모음에서 **구독**을 클릭하고 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f7428-209">In the left navigation, click **Subscriptions**, and then click **Add**.</span></span>
    
3. <span data-ttu-id="f7428-210">**구독 추가** 페이지에서 서비스를 선택하고 결제 정보 및 계약을 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="f7428-210">On the **Add subscription** page, select an offer and complete the payment information and agreement.</span></span>
    
<span data-ttu-id="f7428-211">Azure 및 Office 365 구독으로 따로 구입했으며 Azure 구독에서 Office 365 Azure AD 테넌트에 액세스하려는 경우 [Azure Active Directory 테넌트에 기존의 Azure 구독을 추가](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-how-subscriptions-associated-directory)의 지침을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f7428-211">If you purchased Azure and Office 365 subscriptions separately and want to access the Office 365 Azure AD tenant from your Azure subscription, see the instructions in [Add an existing Azure subscription to your Azure Active Directory tenant](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-how-subscriptions-associated-directory).</span></span>
 
## <a name="see-also"></a><span data-ttu-id="f7428-212">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f7428-212">See also</span></span>

[<span data-ttu-id="f7428-213">Microsoft 클라우드 IT 아키텍처 리소스</span><span class="sxs-lookup"><span data-stu-id="f7428-213">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)
  
[<span data-ttu-id="f7428-214">Exchange, SharePoint, 비즈니스용 Skype 및 Lync에 대한 아키텍처 모델</span><span class="sxs-lookup"><span data-stu-id="f7428-214">Architectural models for SharePoint, Exchange, Skype for Business, and Lync</span></span>](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[<span data-ttu-id="f7428-215">하이브리드 솔루션</span><span class="sxs-lookup"><span data-stu-id="f7428-215">Hybrid solutions</span></span>](hybrid-solutions.md)

## <a name="next-step"></a><span data-ttu-id="f7428-216">다음 단계</span><span class="sxs-lookup"><span data-stu-id="f7428-216">Next step</span></span>

<span data-ttu-id="f7428-217">[Office 365 네트워크 연결성 평가하기](assessing-network-connectivity.md) </span><span class="sxs-lookup"><span data-stu-id="f7428-217">[Assessing Office 365 network connectivity](assessing-network-connectivity.md)</span></span>
  
