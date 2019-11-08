---
title: 액세스 가능한 다이어그램-Microsoft Exchange 2013 플랫폼 옵션
ms.author: josephd
author: JoeDavies-MSFT
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 129f4e45-647e-4cf1-92a6-4d86d8396e73
description: 이 문서는 기술 다이어그램에서 사용할 수 있는 Microsoft Exchange 2013 플랫폼 옵션 이라는 액세스 가능한 텍스트 버전입니다.
ms.openlocfilehash: ce1fe525b6a339c64d757b82a6f1c9ea4b82d23e
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2019
ms.locfileid: "38027572"
---
# <a name="accessible-diagram---microsoft-exchange-2013-platform-options"></a><span data-ttu-id="b9da8-103">액세스 가능한 다이어그램-Microsoft Exchange 2013 플랫폼 옵션</span><span class="sxs-lookup"><span data-stu-id="b9da8-103">Accessible diagram - Microsoft Exchange 2013 Platform Options</span></span>

<span data-ttu-id="b9da8-104">**요약:** 이 문서는 [기술 다이어그램](https://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409)에서 사용할 수 있는 Microsoft Exchange 2013 플랫폼 옵션 이라는 액세스 가능한 텍스트 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-104">**Summary:** This article is an accessible text version of the diagram named Microsoft Exchange 2013 Platform Options, which is available at [Technical Diagrams](https://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409).</span></span>
  
<span data-ttu-id="b9da8-105">이 포스터는 Exchange Online 및 Exchange Server 배포와 관련 하 여 다음과 같은 비즈니스 의사 결정권자 (BDMs) 및 설계자가 파악 해야 하는 사항에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-105">This poster describes what business decision makers (BDMs) and architects need to know about Exchange Online and Exchange Server deployments and includes:</span></span> 
  
- <span data-ttu-id="b9da8-106">Exchange Online (Office 365), Exchange 하이브리드, Exchange Server 온-프레미스 및 공급자 호스트 Exchange 2013에 대해 사용 가능한 4 가지 플랫폼 옵션을 비교 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-106">A comparison of four available platform options for Exchange 2013: Exchange Online (Office 365), Exchange Hybrid, Exchange Server on-premises, and Provider-Hosted Exchange.</span></span> 
    
- <span data-ttu-id="b9da8-107">Exchange 2013에 새로 추가 되었거나 업데이트 된 기능에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-107">Descriptions of three new or updated features in Exchange 2013.</span></span> 
    
## <a name="comparison-of-four-different-deployments-for-the-exchange-2013-platform"></a><span data-ttu-id="b9da8-108">Exchange 2013 플랫폼에 대해 서로 다른 네 가지 배포 비교</span><span class="sxs-lookup"><span data-stu-id="b9da8-108">Comparison of four different deployments for the Exchange 2013 platform</span></span>

<span data-ttu-id="b9da8-109">비교에서는 다음 영역의 각 배포 옵션에 대 한 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-109">The comparison provides information about each deployment option in the following areas:</span></span> 
  
- <span data-ttu-id="b9da8-110">다양 한 배포 기능에 대 한 개요</span><span class="sxs-lookup"><span data-stu-id="b9da8-110">An overview of the different deployment features</span></span> 
    
- <span data-ttu-id="b9da8-111">각 배포 옵션을 구현할 때의 장점</span><span class="sxs-lookup"><span data-stu-id="b9da8-111">Benefits of implementing each deployment option</span></span> 
    
- <span data-ttu-id="b9da8-112">라이선스 요구 사항</span><span class="sxs-lookup"><span data-stu-id="b9da8-112">Licensing requirements</span></span> 
    
- <span data-ttu-id="b9da8-113">필수 아키텍처 작업</span><span class="sxs-lookup"><span data-stu-id="b9da8-113">Required architectural tasks</span></span> 
    
- <span data-ttu-id="b9da8-114">각 배포 옵션을 구현 하는 IT 전문가 책임</span><span class="sxs-lookup"><span data-stu-id="b9da8-114">IT Pro responsibilities for implementing each deployment option</span></span> 
    
### <a name="overview"></a><span data-ttu-id="b9da8-115">개요</span><span class="sxs-lookup"><span data-stu-id="b9da8-115">Overview</span></span>

#### <a name="exchange-online-office-365"></a><span data-ttu-id="b9da8-116">Exchange Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="b9da8-116">Exchange Online (Office 365)</span></span>

<span data-ttu-id="b9da8-117">Office 365의 효율성을 확보 하 고 비용을 절감할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-117">You gain efficiency and reduce costs with Office 365.</span></span>
  
<span data-ttu-id="b9da8-118">함께 제공 되는 다이어그램에서는 온-프레미스 AD DS (Active Directory 도메인 서비스) 환경 및 Azure Active Directory 테 넌 트 간의 계정 이름과 암호를 동기화 하는 Azure Active Directory 테 넌 트와의 Exchange Online을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-118">The accompanying diagram shows Exchange Online with an Azure Active Directory tenant which synchronizes account names and passwords between the on-premises Active Directory Domain Services (AD DS) environment and the Azure Active Directory tenant.</span></span> <span data-ttu-id="b9da8-119">Single sign-on에는 AD FS (Active Directory Federation Services)가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-119">Active Directory Federation Services (AD FS) is necessary for single sign-on.</span></span> 
  
<span data-ttu-id="b9da8-120">기능에 대 한 설명:</span><span class="sxs-lookup"><span data-stu-id="b9da8-120">Description of features and functionality:</span></span>
  
- <span data-ttu-id="b9da8-121">서버 및 서버 소프트웨어의 작업은 Microsoft에서 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-121">The operation of servers and server software is handled by Microsoft.</span></span>
    
- <span data-ttu-id="b9da8-122">Exchange Server 2013의 다양 한 기능 집합을 클라우드 기반 서비스로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-122">Rich feature set of Exchange Server 2013 as a cloud-based service.</span></span>
    
- <span data-ttu-id="b9da8-123">최신 기능을 사용 하 여 항상 최신 상태로 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-123">Always up-to-date with the newest features.</span></span>
    
- <span data-ttu-id="b9da8-124">EOP (Exchange Online Protection)는 스팸 방지/맬웨어 방지 보호를 위해 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-124">Exchange Online Protection (EOP) is included for anti-spam/anti-malware protection.</span></span>
    
- <span data-ttu-id="b9da8-125">99.9% SLA (서비스 수준 계약)를 사용한 기본 제공 고가용성</span><span class="sxs-lookup"><span data-stu-id="b9da8-125">Built-in high availability with a 99.9% Service Level Agreement (SLA).</span></span>
    
- <span data-ttu-id="b9da8-126">온-프레미스 AD DS (Active Directory 도메인 서비스) 및 Azure Active Directory 테 넌 트 간의 암호를 포함 하는 디렉터리 동기화</span><span class="sxs-lookup"><span data-stu-id="b9da8-126">Directory synchronization including passwords between the on-premises Active Directory Domain Services (AD DS) and the Azure Active Directory tenant.</span></span> <span data-ttu-id="b9da8-127">Single sign-on에는 AD FS (Active Directory Federation Services)가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-127">Active Directory Federation Services (AD FS) is necessary for single sign-on.</span></span>
    
#### <a name="exchange-hybrid"></a><span data-ttu-id="b9da8-128">Exchange 하이브리드</span><span class="sxs-lookup"><span data-stu-id="b9da8-128">Exchange Hybrid</span></span>

<span data-ttu-id="b9da8-129">Exchange Server 온-프레미스를 유지 관리 하면서 Office 365의 이점을 활용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-129">You can leverage the benefits of Office 365 while maintaining Exchange Server on-premises.</span></span>
  
<span data-ttu-id="b9da8-130">함께 제공 되는 다이어그램에는 일부 사용자가 온-프레미스에 있고 일부 사용자가 온라인 상태에 있는 Office 365에서 Exchange Online이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-130">The accompanying diagram shows Office 365 with Exchange Online where some users are homed on-premises and some users are homed online.</span></span> <span data-ttu-id="b9da8-131">또한 온-프레미스 AD DS (Active Directory 도메인 서비스) 환경 및 Azure Active Directory 테 넌 트 간의 계정 이름과 암호를 동기화 하는 Azure Active Directory 테 넌 트도 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-131">It also shows an Azure Active Directory tenant which synchronizes account names and passwords between the on-premises Active Directory Domain Services (AD DS) environment and the Azure Active Directory tenant.</span></span>
  
<span data-ttu-id="b9da8-132">기능에 대 한 설명:</span><span class="sxs-lookup"><span data-stu-id="b9da8-132">Description of features and functionality:</span></span>
  
- <span data-ttu-id="b9da8-133">일부 사용자가 온-프레미스에 있고 일부 사용자가 온라인 상태이 고 사용자가 같은 전자 메일 주소 공간을 공유 하는 경우</span><span class="sxs-lookup"><span data-stu-id="b9da8-133">Some users are homed on-premises and some users are homed online, and users share the same e-mail address space.</span></span>
    
- <span data-ttu-id="b9da8-134">기존 Exchange Server 인프라를 활용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-134">Leverages your existing Exchange Server infrastructure.</span></span>
    
- <span data-ttu-id="b9da8-135">일정에 따라 시간에 따라 Exchange 온-프레미스에서 Exchange Online으로 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="b9da8-135">Migrate from Exchange on-premises to Exchange Online over time, on your schedule.</span></span>
    
- <span data-ttu-id="b9da8-136">Lync Online 및 SharePoint Online을 비롯 한 다른 Office 365 응용 프로그램과 통합 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-136">Integrate with other Office 365 applications, including Lync Online and SharePoint Online.</span></span>
    
#### <a name="exchange-server-on-premises"></a><span data-ttu-id="b9da8-137">Exchange Server 온-프레미스</span><span class="sxs-lookup"><span data-stu-id="b9da8-137">Exchange Server on-premises</span></span>

<span data-ttu-id="b9da8-138">고유한 Exchange Server 2013 인프라를 디자인 하 고 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-138">You can design and manage your own Exchange Server 2013 infrastructure.</span></span>
  
<span data-ttu-id="b9da8-139">함께 제공 되는 다이어그램에서는 사용자가 온-프레미스에 있는 온-프레미스 AD DS (Active Directory 도메인 서비스) 환경을 사용 하는 Exchange Server 인프라를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-139">The accompanying diagram shows an Exchange Server infrastructure with an on-premises Active Directory Domain Services (AD DS) environment where users are homed on-premises.</span></span>
  
<span data-ttu-id="b9da8-140">기능에 대 한 설명:</span><span class="sxs-lookup"><span data-stu-id="b9da8-140">Description of features and functionality:</span></span>
  
- <span data-ttu-id="b9da8-141">구성에 대 한 가장 적합 한 제어 및 사용자 지정 수준입니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-141">Greatest degree of control and customization for your configuration.</span></span>
    
- <span data-ttu-id="b9da8-142">부하 분산 계층에서 세션 선호도를 유지 관리 하는 방법에 대 한 종속성이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-142">No dependency on maintaining session affinity at the load balancing layer.</span></span>
    
- <span data-ttu-id="b9da8-143">Dag (데이터베이스 사용 가능 그룹)를 사용 하는 단순 고가용성 및 사이트 복구</span><span class="sxs-lookup"><span data-stu-id="b9da8-143">Simple high availability and site resilience using database availability groups (DAGs).</span></span>
    
- <span data-ttu-id="b9da8-144">뛰어난 사용자 환경을 유지 관리 하는 데 도움이 되는 관리 되는 가용성</span><span class="sxs-lookup"><span data-stu-id="b9da8-144">Managed availability that helps you maintain a great user experience.</span></span>
    
- <span data-ttu-id="b9da8-145">기존 하드웨어 및 저장소 인프라를 활용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-145">Leverage existing hardware and storage infrastructure.</span></span>
    
#### <a name="provider-hosted-exchange"></a><span data-ttu-id="b9da8-146">공급자 호스팅 Exchange</span><span class="sxs-lookup"><span data-stu-id="b9da8-146">Provider-Hosted Exchange</span></span>

<span data-ttu-id="b9da8-147">Exchange 서버 작업을 Exchange Server 솔루션 공급자에 게 외주 시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-147">You can outsource your Exchange Server workload to an Exchange Server solutions provider.</span></span>
  
<span data-ttu-id="b9da8-148">함께 제공 되는 다이어그램에는 공급자가 운영 하 고 유지 관리 하는 Exchange Server 환경이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-148">The accompanying diagram shows an Exchange Server environment that is operated and maintained by a provider.</span></span>
  
<span data-ttu-id="b9da8-149">기능에 대 한 설명:</span><span class="sxs-lookup"><span data-stu-id="b9da8-149">Description of features and functionality:</span></span>
  
- <span data-ttu-id="b9da8-150">서버 및 서버 소프트웨어의 작업은 공급자에 의해 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-150">The operation of servers and server software is handled by your provider.</span></span>
    
- <span data-ttu-id="b9da8-151">Exchange Server 인프라에 대 한 계획, 크기 조정, 확장 및 유지 관리가 공급자에 게 위임 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-151">Planning, sizing, scaling, and maintenance of the Exchange Server infrastructure are delegated to your provider.</span></span>
    
- <span data-ttu-id="b9da8-152">서비스 유지 관리는 공급자에 의해 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-152">Service maintenance is handled by your provider.</span></span>
    
- <span data-ttu-id="b9da8-153">Exchange 기능 집합은 공급자가 배포한 소프트웨어 버전으로 제한 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-153">The Exchange feature set is limited to the software version deployed by your provider.</span></span>
    
### <a name="benefits-of-implementing-each-deployment-option"></a><span data-ttu-id="b9da8-154">각 배포 옵션을 구현할 때의 장점</span><span class="sxs-lookup"><span data-stu-id="b9da8-154">Benefits of implementing each deployment option</span></span>

#### <a name="exchange-online-office-365"></a><span data-ttu-id="b9da8-155">Exchange Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="b9da8-155">Exchange Online (Office 365)</span></span>

<span data-ttu-id="b9da8-156">이 배포 옵션은 다음과 같은 경우에 가장 적합 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-156">This deployment option is best for:</span></span>
  
- <span data-ttu-id="b9da8-157">온-프레미스 Exchange 배포에 대 한 운영 비용을 줄이기 위해 조직</span><span class="sxs-lookup"><span data-stu-id="b9da8-157">Organizations looking to reduce operations costs for on-premises Exchange deployments.</span></span>
    
- <span data-ttu-id="b9da8-158">SharePoint Online 및 Lync Online과 같은 다른 Office 365 제품을 활용할 계획을 수립 하는 조직입니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-158">Organizations that plan to leverage other Office 365 offerings, such as SharePoint Online and Lync Online.</span></span>
    
#### <a name="exchange-hybrid"></a><span data-ttu-id="b9da8-159">Exchange 하이브리드</span><span class="sxs-lookup"><span data-stu-id="b9da8-159">Exchange Hybrid</span></span>

<span data-ttu-id="b9da8-160">이 배포 옵션은 다음과 같은 경우에 가장 적합 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-160">This deployment option is best for:</span></span>
  
- <span data-ttu-id="b9da8-161">Exchange 온-프레미스에서 Exchange Online으로의 마이그레이션을 촉진 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-161">Facilitating a migration from Exchange on-premises to Exchange Online.</span></span>
    
- <span data-ttu-id="b9da8-162">지점 인프라에 대해 투자 하지 않고 원격 사이트를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-162">Supporting remote sites without investing in branch office infrastructure.</span></span>
    
- <span data-ttu-id="b9da8-163">데이터를 온-프레미스에 저장 해야 하는 자회사가 있는 다국적 기업</span><span class="sxs-lookup"><span data-stu-id="b9da8-163">Multinational corporations with subsidiaries that require data to reside on-premises.</span></span>
    
#### <a name="exchange-server-on-premises"></a><span data-ttu-id="b9da8-164">Exchange Server 온-프레미스</span><span class="sxs-lookup"><span data-stu-id="b9da8-164">Exchange Server on-premises</span></span>

<span data-ttu-id="b9da8-165">이 배포 옵션은 다음과 같은 경우에 가장 적합 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-165">This deployment option is best for:</span></span>
  
- <span data-ttu-id="b9da8-166">고도로 사용자 지정 된 솔루션</span><span class="sxs-lookup"><span data-stu-id="b9da8-166">Highly customized solutions.</span></span>
    
- <span data-ttu-id="b9da8-167">Exchange Online에서 지원 되지 않는 하드웨어 및 소프트웨어에 따라 다른 타사 구성 요소를 사용 하는 레거시 솔루션</span><span class="sxs-lookup"><span data-stu-id="b9da8-167">Legacy solutions with third-party components that depend on hardware and software that are not supported by Exchange Online.</span></span>
    
- <span data-ttu-id="b9da8-168">조직은 데이터를 온-프레미스에 배치 해야 하는 데이터 거 버 넌 스를 대상으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-168">Organizations subject to data governance regulations that require data to reside on-premises.</span></span>
    
- <span data-ttu-id="b9da8-169">전체 플랫폼과 솔루션의 제어를 유지 하려는 조직</span><span class="sxs-lookup"><span data-stu-id="b9da8-169">Organizations that wish to retain control of the entire platform and solution.</span></span>
    
#### <a name="provider-hosted-exchange"></a><span data-ttu-id="b9da8-170">공급자 호스팅 Exchange</span><span class="sxs-lookup"><span data-stu-id="b9da8-170">Provider-Hosted Exchange</span></span>

<span data-ttu-id="b9da8-171">이 배포 옵션은 다음과 같은 경우에 가장 적합 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-171">This deployment option is best for:</span></span>
  
- <span data-ttu-id="b9da8-172">Exchange Server 기능을 필요로 하지만 배포 및 유지 관리를 아웃소싱 하려는 조직</span><span class="sxs-lookup"><span data-stu-id="b9da8-172">Organizations that need Exchange Server functionality, but want to outsource its deployment and maintenance.</span></span>
    
- <span data-ttu-id="b9da8-173">개인 설정 지원 옵션이 필요한 조직</span><span class="sxs-lookup"><span data-stu-id="b9da8-173">Organizations that need personalized support options.</span></span>
    
- <span data-ttu-id="b9da8-174">공급자가 제공 하는 사용자 지정 응용 프로그램과의 솔루션 및 통합 사용자 지정</span><span class="sxs-lookup"><span data-stu-id="b9da8-174">Customized solutions and integration with custom applications offered by the provider.</span></span>
    
- <span data-ttu-id="b9da8-175">Exchange Online에서 지원 되지 않는 하드웨어 및 소프트웨어에 따라 다른 타사 구성 요소를 사용 하는 레거시 솔루션</span><span class="sxs-lookup"><span data-stu-id="b9da8-175">Legacy solutions with third-party components that depend on hardware and software that are not supported by Exchange Online.</span></span>
    
### <a name="license-requirements"></a><span data-ttu-id="b9da8-176">라이선스 요구 사항</span><span class="sxs-lookup"><span data-stu-id="b9da8-176">License requirements</span></span>

<span data-ttu-id="b9da8-177">다음 표에서는 각 배포 옵션에 대 한 라이선스 요구 사항을 자세히 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-177">The following table details the license requirements for each deployment option.</span></span>
  
|<span data-ttu-id="b9da8-178">**배포 옵션**</span><span class="sxs-lookup"><span data-stu-id="b9da8-178">**Deployment option**</span></span>|<span data-ttu-id="b9da8-179">**라이선스 요구 사항**</span><span class="sxs-lookup"><span data-stu-id="b9da8-179">**License requirements**</span></span>|
|:-----|:-----|
|<span data-ttu-id="b9da8-180">Exchange Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="b9da8-180">Exchange Online (Office 365)</span></span>  <br/> |<span data-ttu-id="b9da8-181">구독 모델</span><span class="sxs-lookup"><span data-stu-id="b9da8-181">Subscription model</span></span>  <br/> |
|<span data-ttu-id="b9da8-182">Exchange 하이브리드</span><span class="sxs-lookup"><span data-stu-id="b9da8-182">Exchange Hybrid</span></span>  <br/> | <span data-ttu-id="b9da8-183">Office 365-구독 모델</span><span class="sxs-lookup"><span data-stu-id="b9da8-183">Office 365 - Subscription model</span></span> <br/>  <span data-ttu-id="b9da8-184">온-프레미스-모든 온-프레미스 라이선스 적용 (온-프레미스의 교환 서버에 대 한 라이선스 검토)</span><span class="sxs-lookup"><span data-stu-id="b9da8-184">On-premises - All on-premises licenses apply (review licenses for Exchanges Server on-premises)</span></span> <br/>  <span data-ttu-id="b9da8-185">하이브리드 서버 라이선스 \*</span><span class="sxs-lookup"><span data-stu-id="b9da8-185">Hybrid server license\*</span></span> <br/> |
|<span data-ttu-id="b9da8-186">Exchange Server 온-프레미스</span><span class="sxs-lookup"><span data-stu-id="b9da8-186">Exchange Server on-premises</span></span>  <br/> | <span data-ttu-id="b9da8-187">서버 운영 체제</span><span class="sxs-lookup"><span data-stu-id="b9da8-187">Server Operating System</span></span> <br/>  <span data-ttu-id="b9da8-188">Exchange 2013 서버 라이선스</span><span class="sxs-lookup"><span data-stu-id="b9da8-188">Exchange 2013 Server License</span></span> <br/>  <span data-ttu-id="b9da8-189">Exchange 2013 클라이언트 액세스 라이선스</span><span class="sxs-lookup"><span data-stu-id="b9da8-189">Exchange 2013 Client Access License</span></span> <br/> |
|<span data-ttu-id="b9da8-190">공급자 호스팅 Exchange</span><span class="sxs-lookup"><span data-stu-id="b9da8-190">Provider-Hosted Exchange</span></span>  <br/> |<span data-ttu-id="b9da8-191">공급자와의 계약에 따라 비용이 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-191">Costs are based on the agreement with the provider</span></span>  <br/> |
   
### <a name="architecture-tasks"></a><span data-ttu-id="b9da8-192">아키텍처 작업</span><span class="sxs-lookup"><span data-stu-id="b9da8-192">Architecture tasks</span></span>

<span data-ttu-id="b9da8-193">이 섹션에서는 각 배포 옵션에 대 한 아키텍처 작업을 소개 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-193">This section lists the architectural tasks for each deployment option.</span></span>
  
#### <a name="exchange-online-office-365"></a><span data-ttu-id="b9da8-194">Exchange Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="b9da8-194">Exchange Online (Office 365)</span></span>

- <span data-ttu-id="b9da8-195">디렉터리 동기화를 계획 하 고 디자인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-195">Plan and design the directory synchronization.</span></span>
    
- <span data-ttu-id="b9da8-196">방화벽, 프록시 서버, 게이트웨이 및 WAN 링크를 통해 네트워크 용량과 연결을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-196">Ensure network capacity and connectivity through firewalls, proxy servers, gateways, and across WAN links.</span></span>
    
#### <a name="exchange-hybrid"></a><span data-ttu-id="b9da8-197">Exchange 하이브리드</span><span class="sxs-lookup"><span data-stu-id="b9da8-197">Exchange Hybrid</span></span>

<span data-ttu-id="b9da8-198">Office 365 및 온-프레미스 환경 둘 다에 대 한 아키텍처 작업 외에도 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-198">In addition to the architecture tasks for both the Office 365 and on-premises environments:</span></span>
  
- <span data-ttu-id="b9da8-199">Single sign-on 환경을 제공할지 여부를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-199">Decide whether to provide a single-sign on experience.</span></span>
    
- <span data-ttu-id="b9da8-200">온-프레미스 조직을 통해 또는 Exchange Online Protection을 통해 인바운드 인터넷 메일을 라우트할 것인지 여부를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-200">Decide whether to route inbound Internet mail through an on-premises organization or through Exchange Online Protection.</span></span>
    
#### <a name="exchange-server-on-premises"></a><span data-ttu-id="b9da8-201">Exchange Server 온-프레미스</span><span class="sxs-lookup"><span data-stu-id="b9da8-201">Exchange Server on-premises</span></span>

- <span data-ttu-id="b9da8-202">Exchange 토폴로지를 디자인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-202">Design the Exchange topology.</span></span>
    
- <span data-ttu-id="b9da8-203">서버 하드웨어에 대 한 용량을 계획 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-203">Plan the capacity for server hardware.</span></span>
    
- <span data-ttu-id="b9da8-204">메시지 라우팅 토폴로지를 디자인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-204">Design the message routing topology.</span></span>
    
- <span data-ttu-id="b9da8-205">클라이언트 액세스 서버에 대 한 부하 분산을 디자인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-205">Design load balancing for Client Access servers.</span></span>
    
- <span data-ttu-id="b9da8-206">데이터베이스 사용 가능 그룹을 사용 하 여 고가용성을 계획 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-206">Plan for high availability using database availability groups.</span></span>
    
#### <a name="provider-hosted-exchange"></a><span data-ttu-id="b9da8-207">공급자 호스팅 Exchange</span><span class="sxs-lookup"><span data-stu-id="b9da8-207">Provider-Hosted Exchange</span></span>

<span data-ttu-id="b9da8-208">공급자가 방화벽, 프록시 서버, 게이트웨이 및 WAN 링크를 통해 네트워크 용량 및 가용성을 사용할 수 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-208">Ensure that the network capacity and availability through firewalls, proxy servers, gateways, and across WAN links are available to your provider.</span></span>
  
### <a name="it-pro-responsibilities"></a><span data-ttu-id="b9da8-209">IT 전문가 책임</span><span class="sxs-lookup"><span data-stu-id="b9da8-209">IT Pro responsibilities</span></span>

<span data-ttu-id="b9da8-210">이 섹션에서는 각 배포 옵션에 대 한 IT 전문가 책임을 소개 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-210">This section lists the IT Pro responsibilities for each deployment option.</span></span>
  
#### <a name="exchange-online-office-365"></a><span data-ttu-id="b9da8-211">Exchange Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="b9da8-211">Exchange Online (Office 365)</span></span>

- <span data-ttu-id="b9da8-212">디렉터리 동기화 계획을 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-212">Implement the directory synchronization plan.</span></span>
    
- <span data-ttu-id="b9da8-213">내부 및 외부 DNS 레코드와 라우팅을 계획 하 고 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-213">Plan and implement internal and external DNS records and routing.</span></span>
    
- <span data-ttu-id="b9da8-214">Office 365 IP 주소 및 URL 요구 사항에 대 한 프록시 서버 또는 방화벽을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-214">Configure the proxy server or firewall for the Office 365 IP address and URL requirements.</span></span>
    
- <span data-ttu-id="b9da8-215">사용자 계정 및 Exchange Online 설정을 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-215">Administer the user accounts and the Exchange Online settings.</span></span>
    
#### <a name="exchange-hybrid"></a><span data-ttu-id="b9da8-216">Exchange 하이브리드</span><span class="sxs-lookup"><span data-stu-id="b9da8-216">Exchange Hybrid</span></span>

<span data-ttu-id="b9da8-217">Office 365 및 온-프레미스 환경 둘 다에 대 한 IT 전문가 책임 외에도 다음을 수행 하세요.</span><span class="sxs-lookup"><span data-stu-id="b9da8-217">In addition to the IT Pro responsibilities for both the Office 365 and on-premises environments:</span></span>
  
- <span data-ttu-id="b9da8-218">필요한 경우 AD FS (Active Directory Federation Services)를 single sign-on으로 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-218">Configure Active Directory Federation Services (AD FS) for single-sign on (if desired).</span></span>
    
- <span data-ttu-id="b9da8-219">Exchange 2013 서버와 Office 365 간의 보안 통신을 위해 Exchange 인증서를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-219">Configure Exchange certificates for secure communications between Exchange 2013 servers and Office 365.</span></span>
    
- <span data-ttu-id="b9da8-220">원하는 인바운드 인터넷 메일 경로에 대 한 DNS 레코드를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-220">Configure DNS records for the desired inbound Internet mail path.</span></span>
    
#### <a name="exchange-server-on-premises"></a><span data-ttu-id="b9da8-221">Exchange Server 온-프레미스</span><span class="sxs-lookup"><span data-stu-id="b9da8-221">Exchange Server on-premises</span></span>

- <span data-ttu-id="b9da8-222">Exchange 서비스에 필요한 인증서를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-222">Configure the necessary certificates for Exchange services.</span></span>
    
- <span data-ttu-id="b9da8-223">서버를 구축 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-223">Provision the servers.</span></span>
    
- <span data-ttu-id="b9da8-224">Exchange 메시지 라우팅 토폴로지를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-224">Implement the Exchange message routing topology.</span></span>
    
- <span data-ttu-id="b9da8-225">데이터베이스 사용 가능 그룹을 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-225">Implement database availability groups.</span></span>
    
- <span data-ttu-id="b9da8-226">Exchange 서버를 업데이트 하 고 유지 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-226">Update and maintain Exchange servers.</span></span>
    
- <span data-ttu-id="b9da8-227">사용률에 따라 필요한 경우 서버를 추가 또는 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-227">Depending on utilization, add or remove servers as needed.</span></span>
    
#### <a name="provider-hosted-exchange"></a><span data-ttu-id="b9da8-228">공급자 호스팅 Exchange</span><span class="sxs-lookup"><span data-stu-id="b9da8-228">Provider-Hosted Exchange</span></span>

<span data-ttu-id="b9da8-229">공급자의 책임은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-229">The provider's responsibilities include:</span></span>
  
- <span data-ttu-id="b9da8-230">시스템 및 서비스 유지 관리</span><span class="sxs-lookup"><span data-stu-id="b9da8-230">System and service maintenance.</span></span>
    
- <span data-ttu-id="b9da8-231">기능 롤아웃</span><span class="sxs-lookup"><span data-stu-id="b9da8-231">Feature rollouts.</span></span>
    
- <span data-ttu-id="b9da8-232">데이터 보호 및 재해 복구</span><span class="sxs-lookup"><span data-stu-id="b9da8-232">Data protection and disaster recovery.</span></span>
    
<span data-ttu-id="b9da8-233">조직에서 IT 직원의 책임은 사용자 계정 만들기 및 관리를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-233">The IT staff's responsibilities in your organization include creating and managing user accounts.</span></span>
  
#### <a name="more-information"></a><span data-ttu-id="b9da8-234">추가 정보</span><span class="sxs-lookup"><span data-stu-id="b9da8-234">More information</span></span>

<span data-ttu-id="b9da8-235">Exchange Online (Office 365)에 대 한 자세한 내용은 다음을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="b9da8-235">To learn more about Exchange Online (Office 365), see the following:</span></span>
  
- [<span data-ttu-id="b9da8-236">Exchange Online 서비스 설명</span><span class="sxs-lookup"><span data-stu-id="b9da8-236">Exchange Online service description</span></span>](https://aka.ms/EXOSD)
    
- [<span data-ttu-id="b9da8-237">TechNet의 Exchange Online 라이브러리</span><span class="sxs-lookup"><span data-stu-id="b9da8-237">Exchange Online library on TechNet</span></span>](https://aka.ms/EXOTN)
    
- [<span data-ttu-id="b9da8-238">Exchange Online 포털</span><span class="sxs-lookup"><span data-stu-id="b9da8-238">Exchange Online portal</span></span>](https://aka.ms/EXO)
    
<span data-ttu-id="b9da8-239">Exchange 하이브리드에 대 한 자세한 내용은 다음 항목을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="b9da8-239">To learn more about Exchange Hybrid, see the following:</span></span>
  
- <span data-ttu-id="b9da8-240">[Exchange 2013 하이브리드 배포](https://aka.ms/ExchangeHybrid)</span><span class="sxs-lookup"><span data-stu-id="b9da8-240">[Exchange 2013 hybrid deployments](https://aka.ms/ExchangeHybrid).</span></span> <span data-ttu-id="b9da8-241">Exchange 2013 하이브리드 서버 및 exchange 2007 조직이 Exchange 2013 또는 Exchange 2010 하이브리드 서버를 사용 하는 2010 경우에는 다음과 같은 시나리오에 하이브리드 서버 라이선스가 필요 하다는 것을 유의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-241">You should note that the Hybrid server license is only required for the following scenarios: Exchange 2010 organization with Exchange 2013 hybrid server and Exchange 2007 organization with Exchange 2013 or Exchange 2010 hybrid server.</span></span>
    
- [<span data-ttu-id="b9da8-242">Office 365 로그인</span><span class="sxs-lookup"><span data-stu-id="b9da8-242">Office 365 Sign in</span></span>](https://aka.ms/HybridKey)
    
<span data-ttu-id="b9da8-243">Exchange Server 온-프레미스에 대 한 자세한 내용은 다음을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="b9da8-243">To learn more about Exchange Server on-premises, see the following:</span></span>
  
- [<span data-ttu-id="b9da8-244">TechNet의 Exchange Server 2013 라이브러리</span><span class="sxs-lookup"><span data-stu-id="b9da8-244">Exchange Server 2013 library on TechNet</span></span>](https://aka.ms/Ex2013TN)
    
- [<span data-ttu-id="b9da8-245">Exchange Server 2013 포털</span><span class="sxs-lookup"><span data-stu-id="b9da8-245">Exchange Server 2013 portal</span></span>](https://aka.ms/Exchange2013)
    
- [<span data-ttu-id="b9da8-246">Exchange Server 2013 아키텍처</span><span class="sxs-lookup"><span data-stu-id="b9da8-246">Exchange Server 2013 architecture</span></span>](https://aka.ms/Ex2013SP1ArchPoster)
    
<span data-ttu-id="b9da8-247">공급자 호스트 Exchange에 대 한 자세한 내용은 다음 항목을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="b9da8-247">To learn more about Provider-Hosted Exchange, see the following:</span></span>
  
[<span data-ttu-id="b9da8-248">Exchange Server 2013 호스팅 및 다중 테 넌 시 솔루션 및 지침</span><span class="sxs-lookup"><span data-stu-id="b9da8-248">Exchange Server 2013 hosting and multi-tenancy solutions and guidance</span></span>](https://aka.ms/Ex2013Hosting)
  
## <a name="descriptions-of-three-new-or-updated-features-in-exchange-2013"></a><span data-ttu-id="b9da8-249">Exchange 2013의 세 가지 새로운 기능 또는 업데이트 된 기능의 설명</span><span class="sxs-lookup"><span data-stu-id="b9da8-249">Descriptions of three new or updated features in Exchange 2013</span></span>

### <a name="exchange-online-protection"></a><span data-ttu-id="b9da8-250">Exchange Online Protection</span><span class="sxs-lookup"><span data-stu-id="b9da8-250">Exchange Online Protection</span></span>

<span data-ttu-id="b9da8-251">EOP (Exchange Online Protection)는 데이터 센터의 전역 네트워크 전체에 배포 되는 보호 기능을 제공 하 여 모든 배포에 대 한 스팸 방지 및 맬웨어 방지 보호를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-251">Exchange Online Protection (EOP) provides anti-spam and anti-malware protection for any deployment by providing a layer of protection features that are deployed across a global network of data centers.</span></span> <span data-ttu-id="b9da8-252">이를 통해 메시징 환경 관리를 단순화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-252">This helps you to simplify the management of your messaging environments.</span></span> <span data-ttu-id="b9da8-253">EOP는 Exchange Online 구독에 포함 되어 있지만 하이브리드 및 온-프레미스 배포에도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-253">EOP is included in Exchange Online subscriptions, but you can also leverage it for hybrid and on-premises deployments.</span></span>
  
<span data-ttu-id="b9da8-254">함께 제공 되는 다이어그램은 전역 네트워크에 EOP 레이어를 포함 하는 Exchange Online, Exchange 하이브리드 및 Exchange 온-프레미스에 대 한 배포를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-254">The accompanying diagrams show deployments for Exchange Online, Exchange Hybrid, and Exchange on-premises that include the EOP layer in the global network.</span></span>
  
### <a name="exchange-server-deployment-assistant"></a><span data-ttu-id="b9da8-255">Exchange Server 배포 도우미</span><span class="sxs-lookup"><span data-stu-id="b9da8-255">Exchange Server Deployment Assistant</span></span>

<span data-ttu-id="b9da8-256">Exchange Server 배포 도우미는 현재 환경에 대 한 몇 가지 질문을 한 다음, 다양 한 유형의 시나리오에 대해 Exchange Server를 배포 하는 데 도움이 되는 사용자 지정 단계별 검사 목록을 생성 하는 웹 기반 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-256">The Exchange Server Deployment Assistant is a web-based tool that asks you a few questions about your current environment, and then generates a custom step-by-step checklist to help you deploy Exchange Server for different types of scenarios.</span></span> <span data-ttu-id="b9da8-257">이전 버전의 Exchange에서 Exchange 2013로 마이그레이션하거나 exchange Online으로 마이그레이션하거나 하이브리드 인프라를 계획 하는 경우 Exchange Server 배포 도우미는 시나리오에 대해 사용자 지정 된 배포 검사 목록을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-257">Whether you are migrating from a previous version of Exchange to Exchange 2013, migrating to Exchange Online, or planning a hybrid infrastructure, the Exchange Server Deployment Assistant creates a customized deployment checklist for your scenario.</span></span>
  
<span data-ttu-id="b9da8-258">다음 스크린샷에는 Exchange Server 배포 도우미를 사용 하 여 만든 예제 검사 목록이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-258">The accompanying screenshot shows an example checklist that was created using the Exchange Server Deployment Assistant.</span></span>
  
### <a name="integration-with-lync-and-sharepoint"></a><span data-ttu-id="b9da8-259">Lync 및 SharePoint와의 통합</span><span class="sxs-lookup"><span data-stu-id="b9da8-259">Integration with Lync and SharePoint</span></span>

<span data-ttu-id="b9da8-260">Exchange Server 2013에는 Lync Server 2013 및 SharePoint Server 2013과 통합 되는 많은 기능이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-260">Exchange Server 2013 includes many features that integrate with Lync Server 2013 and SharePoint Server 2013.</span></span> <span data-ttu-id="b9da8-261">이러한 제품은 다양 한 기능을 제공 하며 조직 전체에서 공동 작업을 개선 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-261">Together, these products offer a rich suite of features and improve collaboration across your organization.</span></span> 
  
<span data-ttu-id="b9da8-262">함께 제공 되는 다이어그램은 서버 간 인증 포스터를 보여 주고 포스터 링크를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-262">An accompanying diagram shows the Server-to-Server Authentication poster and includes a link to the poster.</span></span> 
  
- <span data-ttu-id="b9da8-263">보관, 유지 및 eDiscovery</span><span class="sxs-lookup"><span data-stu-id="b9da8-263">Archiving, hold and eDiscovery</span></span>
    
- <span data-ttu-id="b9da8-264">사이트 사서함</span><span class="sxs-lookup"><span data-stu-id="b9da8-264">Site mailboxes</span></span>
    
- <span data-ttu-id="b9da8-265">통합 연락처 저장소</span><span class="sxs-lookup"><span data-stu-id="b9da8-265">Unified contact store</span></span>
    
- <span data-ttu-id="b9da8-266">고해상도 사용자 사진</span><span class="sxs-lookup"><span data-stu-id="b9da8-266">High-resolution user photos</span></span>
    
- <span data-ttu-id="b9da8-267">Outlook 및 Outlook Web App에서 Lync 현재 상태</span><span class="sxs-lookup"><span data-stu-id="b9da8-267">Lync presence in Outlook and Outlook Web App</span></span>
    
- <span data-ttu-id="b9da8-268">서버 간 인증</span><span class="sxs-lookup"><span data-stu-id="b9da8-268">Server-to-server authentication</span></span>
    
- <span data-ttu-id="b9da8-269">Voicemail</span><span class="sxs-lookup"><span data-stu-id="b9da8-269">Voicemail</span></span>
    
- <span data-ttu-id="b9da8-270">모임 녹음/녹화</span><span class="sxs-lookup"><span data-stu-id="b9da8-270">Meeting recordings</span></span>
    
- <span data-ttu-id="b9da8-271">Exchange 작업 동기화</span><span class="sxs-lookup"><span data-stu-id="b9da8-271">Exchange task synchronization</span></span>
    
<span data-ttu-id="b9da8-272">함께 제공 되는 다이어그램에서는 Exchange Server 2013 SP1 아키텍처 포스터를 보여 주고 포스터 링크를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9da8-272">An accompanying diagram shows the Exchange Server 2013 SP1 Architecture poster and includes a link to the poster.</span></span>
  

