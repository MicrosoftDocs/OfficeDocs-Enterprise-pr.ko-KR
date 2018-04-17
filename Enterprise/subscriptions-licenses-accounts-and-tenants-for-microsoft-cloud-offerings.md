---
title: 구독, 라이선스, 계정 및 Microsoft의 클라우드 서비스에 대 한 테 넌 트
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Architecture
ms.assetid: c720cffc-f9b5-4f43-9100-422f86a1027c
description: '요약: Microsoft의 클라우드 서비스에서 조직, 구독, 라이선스, 사용자 계정 및 테 넌 트의 관계를 이해 합니다.'
ms.openlocfilehash: ff4854bc66f9a500715bbcd2da696b9a4519aa82
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
---
# <a name="subscriptions-licenses-accounts-and-tenants-for-microsofts-cloud-offerings"></a><span data-ttu-id="d81ba-103">구독, 라이선스, 계정 및 Microsoft의 클라우드 서비스에 대 한 테 넌 트</span><span class="sxs-lookup"><span data-stu-id="d81ba-103">Subscriptions, licenses, accounts, and tenants for Microsoft's cloud offerings</span></span>

 <span data-ttu-id="d81ba-104">**요약:** Microsoft의 클라우드 서비스에서 조직, 구독, 라이선스, 사용자 계정 및 테 넌 트의 관계를 이해 합니다.</span><span class="sxs-lookup"><span data-stu-id="d81ba-104">**Summary:** Understand the relationships of organizations, subscriptions, licenses, user accounts, and tenants across Microsoft's cloud offerings.</span></span>
  
<span data-ttu-id="d81ba-105">Microsoft에서는 해당 클라우드 서비스 간에 id 및 대금 청구의 일관 된 사용에 대 한 조직, 구독, 라이선스 및 사용자 계정을의 계층 구조를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d81ba-105">Microsoft provides a hierarchy of organizations, subscriptions, licenses, and user accounts for consistent use of identities and billing across its cloud offerings:</span></span>
  
- <span data-ttu-id="d81ba-106">Microsoft Office 365</span><span class="sxs-lookup"><span data-stu-id="d81ba-106">Microsoft Office 365</span></span>
    
    <span data-ttu-id="d81ba-107">[사업 계획 및 가격](https://products.office.com/business/compare-office-365-for-business-plans) 에 대 한 자세한 내용은 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="d81ba-107">See [business plans and pricing](https://products.office.com/business/compare-office-365-for-business-plans) for more information.</span></span>
    
- <span data-ttu-id="d81ba-108">Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="d81ba-108">Microsoft Azure</span></span>
    
    <span data-ttu-id="d81ba-109">자세한 내용은 [Azure 가격](https://azure.microsoft.com/pricing/) 을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="d81ba-109">See [Azure pricing](https://azure.microsoft.com/pricing/) for more information.</span></span>
    
- <span data-ttu-id="d81ba-110">Microsoft Intune 및 엔터프라이즈 이동성 + 보안 (EMS)</span><span class="sxs-lookup"><span data-stu-id="d81ba-110">Microsoft Intune and the Enterprise Mobility + Security (EMS)</span></span>
    
    <span data-ttu-id="d81ba-111">자세한 내용은 [Intune 가격](https://www.microsoft.com/cloud-platform/microsoft-intune-pricing) 을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="d81ba-111">See [Intune pricing](https://www.microsoft.com/cloud-platform/microsoft-intune-pricing) for more information.</span></span>
    
- <span data-ttu-id="d81ba-112">Microsoft Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="d81ba-112">Microsoft Dynamics 365</span></span>
    
    <span data-ttu-id="d81ba-113">자세한 내용은 [Dynamics 365 가격](https://dynamics.microsoft.com/) 을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="d81ba-113">See [Dynamics 365 pricing](https://dynamics.microsoft.com/) for more information.</span></span>
    
## <a name="elements-of-the-hierarchy"></a><span data-ttu-id="d81ba-114">계층 구조 요소</span><span class="sxs-lookup"><span data-stu-id="d81ba-114">Elements of the hierarchy</span></span>

<span data-ttu-id="d81ba-115">계층의 요소는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d81ba-115">Here are the elements of the hierarchy:</span></span>
  
### <a name="organization"></a><span data-ttu-id="d81ba-116">조직</span><span class="sxs-lookup"><span data-stu-id="d81ba-116">Organization</span></span>

<span data-ttu-id="d81ba-117">조직에서 일반적으로 contoso.com와 같은 공용 도메인 이름 시스템 (DNS) 도메인 이름으로 식별 되는 Microsoft 클라우드 서비스를 사용 하는 비즈니스 엔터티를 나타냅니다. 조직에는 구독에 대 한 컨테이너입니다.</span><span class="sxs-lookup"><span data-stu-id="d81ba-117">An organization represents a business entity that is using Microsoft cloud offerings, typically identified by a public Domain Name System (DNS) domain name such as contoso.com. The organization is a container for subscriptions.</span></span>
  
### <a name="subscriptions"></a><span data-ttu-id="d81ba-118">구독</span><span class="sxs-lookup"><span data-stu-id="d81ba-118">Subscriptions</span></span>

<span data-ttu-id="d81ba-p101">구독에는 하나를 사용 하 여 Microsoft와 계약 또는 Microsoft 클라우드 플랫폼 수를 늘리거나 요금을 계산 하는 작업에 대 한 서비스 사용자 단위 라이선스 요금 또는 클라우드 기반 리소스 사용에 따라 합니다. Microsoft의 소프트웨어를 서비스로 (SaaS)-(Office 365, Intune/EMS 및 Dynamics 365) 기반된 클라우드 서비스 요금을 사용자 단위 라이선스입니다. Microsoft의 플랫폼 서비스 (PaaS) 및 인프라 서비스 (IaaS) 클라우드 (Azure) 제품 제공물 클라우드 리소스 사용을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="d81ba-p101">A subscription is an agreement with Microsoft to use one or more Microsoft cloud platforms or services, for which charges accrue based on either a per-user license fee or on cloud-based resource consumption. Microsoft's Software as a Service (SaaS)-based cloud offerings (Office 365, Intune/EMS, and Dynamics 365) charge per-user license fees. Microsoft's Platform as a Service (PaaS) and Infrastructure as a Service (IaaS) cloud offerings (Azure) charge based on cloud resource consumption.</span></span>
  
<span data-ttu-id="d81ba-p102">평가판 구독을 사용할 수도 있습니다 하지만 시간이 경과 된 후 특정 시간 또는 소비 요금 구독이 만료 됩니다. 평가판 구독을 유료 구독으로 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d81ba-p102">You can also use a trial subscription, but the subscription expires after a specific amount of time or consumption charges. You can convert a trial subscription to a paid subscription.</span></span>
  
<span data-ttu-id="d81ba-p103">조직에서는 Microsoft의 클라우드 서비스에 대 한 여러 구독을 가질 수 있습니다. 그림 1 예가 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d81ba-p103">Organizations can have multiple subscriptions for Microsoft's cloud offerings. Figure 1 shows an example.</span></span>
  
<span data-ttu-id="d81ba-126">**그림 1: 조직에 대 한 여러 구독의 예**</span><span class="sxs-lookup"><span data-stu-id="d81ba-126">**Figure 1: Example of multiple subscriptions for an organization**</span></span>

![Microsoft의 클라우드 서비스용 구독이 여러 개 있는 예제 조직입니다.](images/Subscriptions/Subscriptions_Fig1.png)

  
<span data-ttu-id="d81ba-128">그림 1은 여러 Office 365 구독, Intune 구독, Dynamics 365 구독 및 여러 Azure 구독이 있는 단일 조직을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="d81ba-128">Figure 1 shows a single organization that has multiple Office 365 subscriptions, an Intune subscription, a Dynamics 365 subscription, and multiple Azure subscriptions.</span></span>
  
### <a name="licenses"></a><span data-ttu-id="d81ba-129">라이선스</span><span class="sxs-lookup"><span data-stu-id="d81ba-129">Licenses</span></span>

<span data-ttu-id="d81ba-p104">Microsoft의 SaaS 클라우드 서비스에 대 한 라이선스 허용 클라우드 서비스를 사용 하 여 특정 사용자 계정을 제공 합니다. 구독의 일부로 고정된 월별 요금을 청구 됩니다. 관리자는 구독에 있는 개별 사용자 계정에 라이선스를 할당합니다. 그림 2의 예제에서는 Contoso Corporation에는 엔터프라이즈 e 5 기능 및 서비스를 사용 하 여 최대 100 개의 개별 사용자 계정에 허용 하는 100 라이선스는 Office 365 Enterprise E5 구독 합니다.</span><span class="sxs-lookup"><span data-stu-id="d81ba-p104">For Microsoft's SaaS cloud offerings, a license allows a specific user account to use the services of the cloud offering. You are charged a fixed monthly fee as part of your subscription. Administrators assign licenses to individual user accounts in the subscription. For the example in Figure 2, the Contoso Corporation has an Office 365 Enterprise E5 subscription with 100 licenses, which allows to up to 100 individual user accounts to use Enterprise E5 features and services.</span></span>
  
<span data-ttu-id="d81ba-134">**조직에 대 한 SaaS 기반 구독 내 그림 2: 라이선스**</span><span class="sxs-lookup"><span data-stu-id="d81ba-134">**Figure 2: Licenses within the SaaS-based subscriptions for an organization**</span></span>

![Microsoft의 SaaS 기반 클라우드 서비스용 구독에 포함된 여러 라이선스 예제입니다.](images/Subscriptions/Subscriptions_Fig2.png)
  
<span data-ttu-id="d81ba-136">Azure PaaS 기반 클라우드 서비스에 대 한 소프트웨어 라이선스 서비스 가격으로 작성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d81ba-136">For Azure PaaS-based cloud services, software licenses are built into the service pricing.</span></span>
  
<span data-ttu-id="d81ba-p105">Azure IaaS 기반 가상 컴퓨터에 대 한 소프트웨어 또는 가상 컴퓨터 이미지에 설치 하는 응용 프로그램을 사용 하 여 추가 라이선스 필요할 수 있습니다. 일부 가상 시스템 이미지가 사용이 허가 된 버전의 소프트웨어를 설치 하 고 비용 서버에 대 한 분당 속도에 포함 됩니다. 예는 SQL Server 2014 및 SQL Server 2016에 대 한 가상 컴퓨터 이미지입니다.</span><span class="sxs-lookup"><span data-stu-id="d81ba-p105">For Azure IaaS-based virtual machines, additional licenses to use the software or application installed on a virtual machine image might be required. Some virtual machine images have licensed versions of software installed and the cost is included in the per-minute rate for the server. Examples are the virtual machine images for SQL Server 2014 and SQL Server 2016.</span></span> 
  
<span data-ttu-id="d81ba-p106">일부 가상 시스템 이미지 설치 하는 응용 프로그램의 평가판 버전 있고 평가판 기간 이후에도 사용 하기 위해 추가 소프트웨어 응용 프로그램 라이선스가 필요 합니다. 등 SharePoint Server 2016 평가판 가상 컴퓨터 이미지를 미리 설치 된 SharePoint Server 2016의 평가판 버전을 포함 합니다. SharePoint Server 2016를 사용 하 여 내역 만료 날짜 이후에 계속 하려면 Microsoft에서 SharePoint Server 2016 라이선스 및 클라이언트 라이선스를 구입 해야 합니다. 이러한 요금은 Azure 구독을 별도로 및 가상 컴퓨터를 실행 하려면 분당 속도 계속 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d81ba-p106">Some virtual machine images have trial versions of applications installed and need additional software application licenses for use beyond the trial period. For example, the SharePoint Server 2016 Trial virtual machine image includes a trial version of SharePoint Server 2016 pre-installed. To continue using SharePoint Server 2016 after the trail expiration date, you must purchase a SharePoint Server 2016 license and client licenses from Microsoft. These charges are separate from the Azure subscription and the per-minute rate to run the virtual machine still applies.</span></span>
  
### <a name="user-accounts"></a><span data-ttu-id="d81ba-144">사용자 계정</span><span class="sxs-lookup"><span data-stu-id="d81ba-144">User accounts</span></span>

<span data-ttu-id="d81ba-p107">Microsoft의 클라우드 서비스의 모든 사용자 계정은 사용자 계정 및 그룹을 포함 하는 Azure Active Directory (AD) 보유자를에 저장 됩니다. Azure AD 테 넌 트 Azure AD 연결, Windows 서버 기반 서비스를 사용 하 여 기존 Windows Server AD 계정을와 동기화 할 수 있습니다. 이 디렉터리 동기화 (DirSync) 이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="d81ba-p107">User accounts for all of Microsoft's cloud offerings are stored in an Azure Active Directory (AD) tenant, which contains user accounts and groups. An Azure AD tenant can be synchronized with your existing Windows Server AD accounts using Azure AD Connect, a Windows server-based service. This is known as directory synchronization (DirSync).</span></span>
  
<span data-ttu-id="d81ba-148">그림 3에는 일반적인 Azure AD 테 넌 트 조직의 계정이 포함 된를 사용 하 여 조직의 여러 구독의 예가 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d81ba-148">Figure 3 shows an example of multiple subscriptions of an organization using a common Azure AD tenant that contains the organization's accounts.</span></span>
  
<span data-ttu-id="d81ba-149">**그림 3: 여러 구독 하는 조직의 동일한 Azure AD 테 넌 트를 사용 하는**</span><span class="sxs-lookup"><span data-stu-id="d81ba-149">**Figure 3: Multiple subscriptions of an organization that use the same Azure AD tenant**</span></span>

![모두 동일한 Azure 테넌트를 사용하는 여러 개의 구독이 있는 예제 조직입니다.](images/Subscriptions/Subscriptions_Fig3.png)
  
### <a name="tenants"></a><span data-ttu-id="d81ba-151">테 넌 트</span><span class="sxs-lookup"><span data-stu-id="d81ba-151">Tenants</span></span>

<span data-ttu-id="d81ba-p108">SaaS 클라우드 서비스에 대 한 테 넌 트 클라우드 서비스를 제공 하는 서버를 보관 하는 지역 위치입니다. 예, Contoso Corporation를 호스팅하는 Office 365, EMS, 및 Dynamics 365 테 넌 트 자신의 파리 본사에서 15, 000 작업자에 대 한 유럽 지역 선택 했습니다.</span><span class="sxs-lookup"><span data-stu-id="d81ba-p108">For SaaS cloud offerings, the tenant is the regional location that houses the servers providing cloud services. For example, the Contoso Corporation chose the European region to host its Office 365, EMS, and Dynamics 365 tenants for the 15,000 workers in their Paris headquarters.</span></span>
  
<span data-ttu-id="d81ba-p109">Azure PaaS 서비스와 Azure IaaS에서 호스팅되는 가상 컴퓨터 기반 작업 전세계 모든 Azure 데이터 센터의 테 넌 시를 가질 수 있습니다. Azure PaaS 응용 프로그램 또는 서비스 또는 IaaS 작업량의 요소를 만들 때 해당 위치 라고 Azure 데이터 센터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d81ba-p109">Azure PaaS services and virtual machine-based workloads hosted in Azure IaaS can have tenancy in any Azure datacenter across the world. You specify the Azure datacenter, known as the location, when you create the Azure PaaS app or service or element of an IaaS workload.</span></span>
  
<span data-ttu-id="d81ba-p110">Azure AD 테 넌 트는 계정 및 그룹을 포함 하는 Azure AD의 특정 인스턴스. Office 365, Dynamics 365 또는 Intune/EMS 유료 또는 평가판 구독에 포함 무료 Azure AD 테 넌 트입니다. 이 Azure AD 테 넌 트 다른 Azure 서비스를 포함 하지 않는 및 Azure에 평가판 또는 유료 구독으로 같지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d81ba-p110">An Azure AD tenant is a specific instance of Azure AD containing accounts and groups. Paid or trial subscriptions of Office 365, Dynamics 365, or Intune/EMS include a free Azure AD tenant. This Azure AD tenant does not include other Azure services and is not the same as an Azure trial or paid subscription.</span></span>
  
### <a name="summary-of-the-hierarchy"></a><span data-ttu-id="d81ba-159">계층 구조 요약</span><span class="sxs-lookup"><span data-stu-id="d81ba-159">Summary of the hierarchy</span></span>

<span data-ttu-id="d81ba-160">빠른 다시 살펴보기 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d81ba-160">Here is a quick recap:</span></span>
  
- <span data-ttu-id="d81ba-161">조직에 여러 구독이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d81ba-161">An organization can have multiple subscriptions</span></span>
    
  - <span data-ttu-id="d81ba-162">구독에 여러 라이선스를 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d81ba-162">A subscription can have multiple licenses</span></span>
    
  - <span data-ttu-id="d81ba-163">개별 사용자 계정에 라이선스를 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d81ba-163">Licenses can be assigned to individual user accounts</span></span>
    
  - <span data-ttu-id="d81ba-164">Azure AD 테 넌 트에 저장 된 사용자 계정</span><span class="sxs-lookup"><span data-stu-id="d81ba-164">User accounts are stored in an Azure AD tenant</span></span>
    
<span data-ttu-id="d81ba-165">조직, 구독, 라이선스 및 사용자 계정의 관계의 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d81ba-165">Here is an example of the relationship of organizations, subscriptions, licenses, and user accounts:</span></span>
  
- <span data-ttu-id="d81ba-166">공용 도메인 이름을 사용 하 여 식별 하는 조직입니다.</span><span class="sxs-lookup"><span data-stu-id="d81ba-166">An organization identified by its public domain name.</span></span>
    
  - <span data-ttu-id="d81ba-167">사용자 라이선스는 Office 365 Enterprise E3 구독 합니다.</span><span class="sxs-lookup"><span data-stu-id="d81ba-167">An Office 365 Enterprise E3 subscription with user licenses.</span></span>
    
    <span data-ttu-id="d81ba-168">사용자 라이선스는 Office 365 Enterprise E5 구독 합니다.</span><span class="sxs-lookup"><span data-stu-id="d81ba-168">An Office 365 Enterprise E5 subscription with user licenses.</span></span>
    
    <span data-ttu-id="d81ba-169">사용자 라이선스에 EMS 구독 합니다.</span><span class="sxs-lookup"><span data-stu-id="d81ba-169">An EMS subscription with user licenses.</span></span>
    
    <span data-ttu-id="d81ba-170">사용자 라이선스 Dynamics 365 구독 합니다.</span><span class="sxs-lookup"><span data-stu-id="d81ba-170">A Dynamics 365 subscription with user licenses.</span></span>
    
    <span data-ttu-id="d81ba-171">여러 Azure 구독 합니다.</span><span class="sxs-lookup"><span data-stu-id="d81ba-171">Multiple Azure subscriptions.</span></span>
    
  - <span data-ttu-id="d81ba-172">일반적인 Azure AD 테 넌 트에는 조직의 사용자 계정입니다.</span><span class="sxs-lookup"><span data-stu-id="d81ba-172">The organization's user accounts in a common Azure AD tenant.</span></span>
    
<span data-ttu-id="d81ba-p111">구독을 제공 하는 여러 Microsoft 클라우드 동일한 Azure AD 테 넌 트 id 공급자를 공통으로 작동 하는 사용할 수 있습니다. 중앙 온-프레미스 Windows Server AD의 동기화 된 계정이 포함 된 Azure AD 테 넌 트 조직에 대 한 서비스 (IDaaS)으로 클라우드 기반 Id를 제공 합니다. 이 그림 4에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d81ba-p111">Multiple Microsoft cloud offering subscriptions can use the same Azure AD tenant that acts as a common identity provider. A central Azure AD tenant that contains the synchronized accounts of your on-premises Windows Server AD provides cloud-based Identity as a Service (IDaaS) for your organization. This is shown in Figure 4.</span></span>
  
<span data-ttu-id="d81ba-176">**그림 4: 동기화 된 온-프레미스 계정 하 고 조직에 대 한 IDaaS**</span><span class="sxs-lookup"><span data-stu-id="d81ba-176">**Figure 4: Synchronized on-premises accounts and IDaaS for an organization**</span></span>

![조직에 대한 IaaS(Identity as a Service) IDaaS입니다.](images/Subscriptions/Subscriptions_Fig4.png)
  
<span data-ttu-id="d81ba-p112">그림 4는 Microsoft의 SaaS 클라우드 서비스, Azure PaaS 응용 프로그램 및 Azure AD 도메인 서비스를 사용 하 여 Azure IaaS에 가상 컴퓨터에서 일반적인 Azure AD 테 넌 트를 활용 하는 방법을 보여줍니다. Azure AD 연결 Azure AD 테 넌 트와 온-프레미스 Windows Server AD 포리스트를 동기화합니다.</span><span class="sxs-lookup"><span data-stu-id="d81ba-p112">Figure 4 shows how a common Azure AD tenant is utilized by Microsoft's SaaS cloud offerings, Azure PaaS apps, and virtual machines in Azure IaaS that use Azure AD Domain Services. Azure AD Connect synchronizes the on-premises Windows Server AD forest with the Azure AD tenant.</span></span>
  
<span data-ttu-id="d81ba-180">Microsoft의 클라우드 서비스에서 identity 통합 하는 방법에 대 한 자세한 내용은 [엔터프라이즈 설계자에 대 한 Microsoft 클라우드 Id](https://aka.ms/cloudarchidentity)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="d81ba-180">For more information about identity integration across Microsoft's cloud offerings, see [Microsoft Cloud Identity for Enterprise Architects](https://aka.ms/cloudarchidentity).</span></span>
  
## <a name="combining-subscriptions-for-multiple-microsoft-cloud-offerings"></a><span data-ttu-id="d81ba-181">여러 Microsoft 클라우드 서비스에 대 한 구독을 결합</span><span class="sxs-lookup"><span data-stu-id="d81ba-181">Combining subscriptions for multiple Microsoft cloud offerings</span></span>

<span data-ttu-id="d81ba-182">다음 표에서 이미 구독을 필요에 따라 여러 Microsoft 클라우드 서비스를 결합 하는 방법과 한 가지 유형의 (첫째 열을 아래로 레이블)를 제공 하 고 다른 클라우드를 위한 구독을 추가 하는 클라우드에 대 한 제공 (간에 이동 합니다. 열)입니다.</span><span class="sxs-lookup"><span data-stu-id="d81ba-182">The following table describes how you can combine multiple Microsoft cloud offerings based on already having a subscription for one type of cloud offering (the labels going down the first column) and adding a subscription for a different cloud offering (going across the columns).</span></span>
  
||<span data-ttu-id="d81ba-183">**Office 365**</span><span class="sxs-lookup"><span data-stu-id="d81ba-183">**Office 365**</span></span>|<span data-ttu-id="d81ba-184">**Azure**</span><span class="sxs-lookup"><span data-stu-id="d81ba-184">**Azure**</span></span>|<span data-ttu-id="d81ba-185">**Intune/EMS**</span><span class="sxs-lookup"><span data-stu-id="d81ba-185">**Intune/EMS**</span></span>|<span data-ttu-id="d81ba-186">**Dynamics 365**</span><span class="sxs-lookup"><span data-stu-id="d81ba-186">**Dynamics 365**</span></span>|
|:-----|:-----|:-----|:-----|:-----|
|<span data-ttu-id="d81ba-187">**Office 365**</span><span class="sxs-lookup"><span data-stu-id="d81ba-187">**Office 365**</span></span> <br/> |<span data-ttu-id="d81ba-188">해당 없음</span><span class="sxs-lookup"><span data-stu-id="d81ba-188">NA</span></span>  <br/> |<span data-ttu-id="d81ba-189">Azure 포털에서 조직에 Azure에 구독을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="d81ba-189">You add an Azure subscription to your organization from the Azure portal.</span></span>  <br/> |<span data-ttu-id="d81ba-190">Office 365 포털에서 조직에 Intune/EMS 구독을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="d81ba-190">You add an Intune/EMS subscription to your organization from the Office 365 portal.</span></span>  <br/> |<span data-ttu-id="d81ba-191">Office 365 포털에서 조직에 Dynamics 365 구독을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="d81ba-191">You add a Dynamics 365 subscription to your organization from the Office 365 portal.</span></span>  <br/> |
|<span data-ttu-id="d81ba-192">**Azure**</span><span class="sxs-lookup"><span data-stu-id="d81ba-192">**Azure**</span></span> <br/> |<span data-ttu-id="d81ba-193">조직에 Office 365 구독을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="d81ba-193">You add an Office 365 subscription to your organization.</span></span>  <br/> |<span data-ttu-id="d81ba-194">해당 없음</span><span class="sxs-lookup"><span data-stu-id="d81ba-194">NA</span></span>  <br/> |<span data-ttu-id="d81ba-195">조직에 Intune/EMS 구독을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="d81ba-195">You add an Intune/EMS subscription to your organization.</span></span>  <br/> |<span data-ttu-id="d81ba-196">조직에 Dynamics 365 구독을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="d81ba-196">You add a Dynamics 365 subscription to your organization.</span></span>  <br/> |
|<span data-ttu-id="d81ba-197">**Intune/EMS**</span><span class="sxs-lookup"><span data-stu-id="d81ba-197">**Intune/EMS**</span></span> <br/> |<span data-ttu-id="d81ba-198">조직에 Office 365 구독을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="d81ba-198">You add an Office 365 subscription to your organization.</span></span>  <br/> |<span data-ttu-id="d81ba-199">Azure 포털에서 조직에 Azure에 구독을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="d81ba-199">You add an Azure subscription to your organization from the Azure portal.</span></span>  <br/> |<span data-ttu-id="d81ba-200">해당 없음</span><span class="sxs-lookup"><span data-stu-id="d81ba-200">NA</span></span>  <br/> |<span data-ttu-id="d81ba-201">조직에 Dynamics 365 구독을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="d81ba-201">You add a Dynamics 365 subscription to your organization.</span></span>  <br/> |
|<span data-ttu-id="d81ba-202">**Dynamics 365**</span><span class="sxs-lookup"><span data-stu-id="d81ba-202">**Dynamics 365**</span></span> <br/> |<span data-ttu-id="d81ba-203">조직에 Office 365 구독을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="d81ba-203">You add an Office 365 subscription to your organization.</span></span>  <br/> |<span data-ttu-id="d81ba-204">Azure 포털에서 조직에 Azure에 구독을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="d81ba-204">You add an Azure subscription to your organization from the Azure portal.</span></span>  <br/> |<span data-ttu-id="d81ba-205">조직에 Intune/EMS 구독을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="d81ba-205">You add an Intune/EMS subscription to your organization.</span></span>  <br/> |<span data-ttu-id="d81ba-206">해당 없음</span><span class="sxs-lookup"><span data-stu-id="d81ba-206">NA</span></span>  <br/> |
   
<span data-ttu-id="d81ba-207">Office 365 관리 센터를 통해 Microsoft SaaS 기반 서비스에 대 한 조직에 구독을 추가 하는 간편한 방법이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d81ba-207">An easy way to add subscriptions to your organization for Microsoft SaaS-based services is through the Office 365 Admin center:</span></span>
  
1. <span data-ttu-id="d81ba-208">Office 365 포털에 로그인 ([https://portal.office.com](https://portal.office.com)) 전역 관리자, 계정 하 고 다음 **관리**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d81ba-208">Sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) with your global administrator account, and then click **Admin**.</span></span>
    
2. <span data-ttu-id="d81ba-209">**관리 센터** 홈페이지의 왼쪽된 탐색 모음에서 **대금 청구**및 **구매 서비스**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d81ba-209">From the left navigation of the **Admin center** home page, click **Billing**, and then **Purchase services**.</span></span>
    
3. <span data-ttu-id="d81ba-210">**구매 서비스** 페이지에서 새 구독을 구입 합니다.</span><span class="sxs-lookup"><span data-stu-id="d81ba-210">On the **Purchase services** page, purchase your new subscriptions.</span></span>
    
<span data-ttu-id="d81ba-211">Office 365 관리 센터 SaaS 기반 클라우드 서비스에 대 한 새 등록에 조직 및 Office 365 구독 Azure AD 테 넌 트를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="d81ba-211">The Office 365 Admin center assigns the organization and Azure AD tenant of your Office 365 subscription to the new subscriptions for SaaS-based cloud offerings.</span></span>
  
<span data-ttu-id="d81ba-212">Office 365 구독으로 Azure AD 테 넌 트와 같은 조직에 Azure 구독을 추가:</span><span class="sxs-lookup"><span data-stu-id="d81ba-212">To add an Azure subscription with the same organization and Azure AD tenant as your Office 365 subscription:</span></span>
  
1. <span data-ttu-id="d81ba-213">Azure 포털에 로그인 ([https://portal.azure.com](https://portal.azure.com)) Office 365 전역 관리자 계정을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d81ba-213">Sign in to the Azure portal ([https://portal.azure.com](https://portal.azure.com)) with your Office 365 global administrator account.</span></span>
    
2. <span data-ttu-id="d81ba-214">왼쪽 탐색 영역에서 **구독**을 클릭 하 고 **추가**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d81ba-214">In the left navigation, click **Subscriptions**, and then click **Add**.</span></span>
    
3. <span data-ttu-id="d81ba-215">**추가 구독** 페이지에서 제공 하는 서비스를 선택 하 고 지불 정보 및 계약을 완료 합니다.</span><span class="sxs-lookup"><span data-stu-id="d81ba-215">On the **Add subscription** page, select an offer and complete the payment information and agreement.</span></span>
    
<span data-ttu-id="d81ba-216">Azure 및 Office 365 구독을 별도로 구입 하 고 Azure 구독에서 Office 365 Azure AD 테 넌 트에 액세스 하는 경우 [는 Office 365 테 넌 트 Azure에 가입 연결](https://channel9.msdn.com/Series/Microsoft-Azure-Tutorials/Associate-an-Office-365-tenant-with-an-Azure-subscription)의 지침을 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="d81ba-216">If you purchased Azure and Office 365 subscriptions separately and want to access the Office 365 Azure AD tenant from your Azure subscription, see the instructions in [Associate an Office 365 tenant with an Azure subscription](https://channel9.msdn.com/Series/Microsoft-Azure-Tutorials/Associate-an-Office-365-tenant-with-an-Azure-subscription).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="d81ba-217">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d81ba-217">See Also</span></span>

[<span data-ttu-id="d81ba-218">Microsoft 클라우드 IT 아키텍처 리소스</span><span class="sxs-lookup"><span data-stu-id="d81ba-218">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)
  
[<span data-ttu-id="d81ba-219">클라우드 도입 TLG(테스트 랩 가이드)</span><span class="sxs-lookup"><span data-stu-id="d81ba-219">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="d81ba-220">Exchange, SharePoint, 비즈니스용 Skype 및 Lync에 대한 아키텍처 모델</span><span class="sxs-lookup"><span data-stu-id="d81ba-220">Architectural models for SharePoint, Exchange, Skype for Business, and Lync</span></span>](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[<span data-ttu-id="d81ba-221">하이브리드 솔루션</span><span class="sxs-lookup"><span data-stu-id="d81ba-221">Hybrid solutions</span></span>](hybrid-solutions.md)
  
[<span data-ttu-id="d81ba-222">구독, 라이선스 및 Contoso Corporation에 대 한 사용자 계정</span><span class="sxs-lookup"><span data-stu-id="d81ba-222">Subscriptions, licenses, and user accounts for the Contoso Corporation</span></span>](subscriptions-licenses-and-user-accounts-for-the-contoso-corporation.md)



