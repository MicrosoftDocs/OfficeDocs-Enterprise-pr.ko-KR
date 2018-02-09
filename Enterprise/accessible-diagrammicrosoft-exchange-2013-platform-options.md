---
title: "액세스할 수 있는 다이어그램-Microsoft Exchange 2013 플랫폼 옵션"
ms.author: josephd
author: JoeDavies-MSFT
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 129f4e45-647e-4cf1-92a6-4d86d8396e73
description: "이 문서에는 기술 다이어그램에서 사용할 수 있는 Microsoft Exchange 2013 플랫폼 옵션 라는 다이어그램의 액세스할 수 있는 텍스트 버전입니다."
ms.openlocfilehash: e1c4957c9152c5a23008c657d7e2d0d47b5cce0f
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/09/2018
---
# <a name="accessible-diagram---microsoft-exchange-2013-platform-options"></a><span data-ttu-id="8bb49-103">액세스할 수 있는 다이어그램-Microsoft Exchange 2013 플랫폼 옵션</span><span class="sxs-lookup"><span data-stu-id="8bb49-103">Accessible diagram - Microsoft Exchange 2013 Platform Options</span></span>

<span data-ttu-id="8bb49-104">**요약:** 이 문서에는 [기술 다이어그램](http://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409)에서 사용할 수 있는 Microsoft Exchange 2013 플랫폼 옵션 라는 다이어그램의 액세스할 수 있는 텍스트 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-104">**Summary:** This article is an accessible text version of the diagram named Microsoft Exchange 2013 Platform Options, which is available at [Technical Diagrams](http://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409).</span></span>
  
<span data-ttu-id="8bb49-105">이 포스터 비즈니스 의사 결정권자 (Bdm) 하 고 구축한 필요한 정보를 Exchange Online 및 Exchange Server 배포에 대해 알고에 대해 설명 하 고 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-105">This poster describes what business decision makers (BDMs) and architects need to know about Exchange Online and Exchange Server deployments and includes:</span></span> 
  
- <span data-ttu-id="8bb49-106">Exchange 2013에 대 한 4 개의 사용 가능한 플랫폼 옵션의 비교: Exchange Online (Office 365), Exchange 하이브리드 Exchange Server 온-프레미스, 및 Provider-Hosted 교환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-106">A comparison of four available platform options for Exchange 2013: Exchange Online (Office 365), Exchange Hybrid, Exchange Server on-premises, and Provider-Hosted Exchange.</span></span> 
    
- <span data-ttu-id="8bb49-107">Exchange 2013의 세 신규 또는 업데이트 된 기능에 대 한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-107">Descriptions of three new or updated features in Exchange 2013.</span></span> 
    
## <a name="comparison-of-four-different-deployments-for-the-exchange-2013-platform"></a><span data-ttu-id="8bb49-108">Exchange 2013 플랫폼에 대 한 4 개의 서로 다른 배포의 비교</span><span class="sxs-lookup"><span data-stu-id="8bb49-108">Comparison of four different deployments for the Exchange 2013 platform</span></span>

<span data-ttu-id="8bb49-109">비교는 다음 영역에서 각 배포 옵션에 대 한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-109">The comparison provides information about each deployment option in the following areas:</span></span> 
  
- <span data-ttu-id="8bb49-110">다양 한 배포 기능에 대 한 개요</span><span class="sxs-lookup"><span data-stu-id="8bb49-110">An overview of the different deployment features</span></span> 
    
- <span data-ttu-id="8bb49-111">각 배포 옵션을 구현 하는의 이점</span><span class="sxs-lookup"><span data-stu-id="8bb49-111">Benefits of implementing each deployment option</span></span> 
    
- <span data-ttu-id="8bb49-112">라이선스 요구 사항</span><span class="sxs-lookup"><span data-stu-id="8bb49-112">Licensing requirements</span></span> 
    
- <span data-ttu-id="8bb49-113">필수 아키텍처 작업</span><span class="sxs-lookup"><span data-stu-id="8bb49-113">Required architectural tasks</span></span> 
    
- <span data-ttu-id="8bb49-114">각 배포 옵션을 구현 하기 위한 IT Pro 책임</span><span class="sxs-lookup"><span data-stu-id="8bb49-114">IT Pro responsibilities for implementing each deployment option</span></span> 
    
### <a name="overview"></a><span data-ttu-id="8bb49-115">개요</span><span class="sxs-lookup"><span data-stu-id="8bb49-115">Overview</span></span>

#### <a name="exchange-online-office-365"></a><span data-ttu-id="8bb49-116">Exchange Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="8bb49-116">Exchange Online (Office 365)</span></span>

<span data-ttu-id="8bb49-117">효율성을 높이 하 고이 정보를 Office 365와 비용을 절감 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-117">You gain efficiency and reduce costs with Office 365.</span></span>
  
<span data-ttu-id="8bb49-p101">함께 제공 되는 다이어그램에서는 계정 이름 및 온-프레미스 Active Directory 도메인 서비스 (AD DS) 환경과 Azure Active Directory 테 넌 트 간에 암호를 동기화 하는 한 Azure Active Directory 테 넌 트를 Exchange Online 보여줍니다. Active Directory Federation Services (AD FS)는 single sign-on 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-p101">The accompanying diagram shows Exchange Online with an Azure Active Directory tenant which synchronizes account names and passwords between the on-premises Active Directory Domain Services (AD DS) environment and the Azure Active Directory tenant. Active Directory Federation Services (AD FS) is necessary for single sign-on.</span></span> 
  
<span data-ttu-id="8bb49-120">기능 및 기능을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-120">Description of features and functionality:</span></span>
  
- <span data-ttu-id="8bb49-121">서버 및 서버 소프트웨어의 작업은 Microsoft에서 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-121">The operation of servers and server software is handled by Microsoft.</span></span>
    
- <span data-ttu-id="8bb49-122">Exchange Server 2013의 클라우드 기반 서비스로 풍부한 기능을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-122">Rich feature set of Exchange Server 2013 as a cloud-based service.</span></span>
    
- <span data-ttu-id="8bb49-123">항상 최신 상태로 유지 최신 기능을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-123">Always up-to-date with the newest features.</span></span>
    
- <span data-ttu-id="8bb49-124">Exchange Online Protection (EOP) 백신-스팸 방지/맬웨어 방지 보호 기능에 대 한 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-124">Exchange Online Protection (EOP) is included for anti-spam/anti-malware protection.</span></span>
    
- <span data-ttu-id="8bb49-125">기본 제공 고가용성 99.9%와 서비스 수준 계약 (SLA).</span><span class="sxs-lookup"><span data-stu-id="8bb49-125">Built-in high availability with a 99.9% Service Level Agreement (SLA).</span></span>
    
- <span data-ttu-id="8bb49-p102">디렉터리 동기화를 온-프레미스 Active Directory 도메인 서비스 (AD DS) 및 Azure Active Directory 테 넌 트 간에 암호를 포함 합니다. Active Directory Federation Services (AD FS)는 single sign-on 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-p102">Directory synchronization including passwords between the on-premises Active Directory Domain Services (AD DS) and the Azure Active Directory tenant. Active Directory Federation Services (AD FS) is necessary for single sign-on.</span></span>
    
#### <a name="exchange-hybrid"></a><span data-ttu-id="8bb49-128">Exchange 하이브리드</span><span class="sxs-lookup"><span data-stu-id="8bb49-128">Exchange Hybrid</span></span>

<span data-ttu-id="8bb49-129">Office 365의 이점을 활용 하 여 Exchange Server 온-프레미스를 유지 하면서 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-129">You can leverage the benefits of Office 365 while maintaining Exchange Server on-premises.</span></span>
  
<span data-ttu-id="8bb49-p103">함께 제공 되는 다이어그램 Exchange Online과 여기에서 일부 사용자는 홈된 온-프레미스 하 고 일부 사용자가 온라인에 있는 Office 365를 보여줍니다. 또한 계정 이름 및 온-프레미스 Active Directory 도메인 서비스 (AD DS) 환경과 Azure Active Directory 테 넌 트 간에 암호를 동기화 하는 한 Azure Active Directory 테 넌 트를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-p103">The accompanying diagram shows Office 365 with Exchange Online where some users are homed on-premises and some users are homed online. It also shows an Azure Active Directory tenant which synchronizes account names and passwords between the on-premises Active Directory Domain Services (AD DS) environment and the Azure Active Directory tenant.</span></span>
  
<span data-ttu-id="8bb49-132">기능 및 기능을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-132">Description of features and functionality:</span></span>
  
- <span data-ttu-id="8bb49-133">일부 사용자는 홈된 온-프레미스 하 고 일부 사용자가 온라인 상태에 있는 사용자가 동일한 전자 메일 주소 공간을 공유 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-133">Some users are homed on-premises and some users are homed online, and users share the same e-mail address space.</span></span>
    
- <span data-ttu-id="8bb49-134">기존 Exchange 서버 인프라를 활용합니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-134">Leverages your existing Exchange Server infrastructure.</span></span>
    
- <span data-ttu-id="8bb49-135">Exchange 온-프레미스에서 Exchange Online에 일정에 시간별로 마이그레이션하십시오.</span><span class="sxs-lookup"><span data-stu-id="8bb49-135">Migrate from Exchange on-premises to Exchange Online over time, on your schedule.</span></span>
    
- <span data-ttu-id="8bb49-136">Lync Online 및 SharePoint Online을 포함 하 여 다른 Office 365 응용 프로그램과 통합 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-136">Integrate with other Office 365 applications, including Lync Online and SharePoint Online.</span></span>
    
#### <a name="exchange-server-on-premises"></a><span data-ttu-id="8bb49-137">Exchange Server 온-프레미스</span><span class="sxs-lookup"><span data-stu-id="8bb49-137">Exchange Server on-premises</span></span>

<span data-ttu-id="8bb49-138">디자인 하 고 직접 Exchange Server 2013 인프라를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-138">You can design and manage your own Exchange Server 2013 infrastructure.</span></span>
  
<span data-ttu-id="8bb49-139">함께 제공 된 다이어그램은 사용자의 홈된 온-프레미스가 온-프레미스 Active Directory 도메인 서비스 (AD DS) 환경 사용 하 여 Exchange Server 인프라를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-139">The accompanying diagram shows an Exchange Server infrastructure with an on-premises Active Directory Domain Services (AD DS) environment where users are homed on-premises.</span></span>
  
<span data-ttu-id="8bb49-140">기능 및 기능을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-140">Description of features and functionality:</span></span>
  
- <span data-ttu-id="8bb49-141">가장 큰 수준의 제어 및 구성에 대 한 사용자 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-141">Greatest degree of control and customization for your configuration.</span></span>
    
- <span data-ttu-id="8bb49-142">부하 분산 계층에서 세션 선호도 유지 관리에 대 한 종속성 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-142">No dependency on maintaining session affinity at the load balancing layer.</span></span>
    
- <span data-ttu-id="8bb49-143">간단한 고가용성 및 사이트 복구 데이터베이스 가용성 그룹 (Dag)를 사용 하 여 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-143">Simple high availability and site resilience using database availability groups (DAGs).</span></span>
    
- <span data-ttu-id="8bb49-144">훌륭한 사용자 환경을 유지 관리 하는데 도움이 되는 가용성을 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-144">Managed availability that helps you maintain a great user experience.</span></span>
    
- <span data-ttu-id="8bb49-145">기존 하드웨어 및 저장소 인프라를 활용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-145">Leverage existing hardware and storage infrastructure.</span></span>
    
#### <a name="provider-hosted-exchange"></a><span data-ttu-id="8bb49-146">Exchange 공급자 호스팅</span><span class="sxs-lookup"><span data-stu-id="8bb49-146">Provider-Hosted Exchange</span></span>

<span data-ttu-id="8bb49-147">Exchange Server 솔루션 공급자에 Exchange 서버 작업 부하를 아웃소싱 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-147">You can outsource your Exchange Server workload to an Exchange Server solutions provider.</span></span>
  
<span data-ttu-id="8bb49-148">함께 제공 된 다이어그램을 운영 하 고 공급자에 의해 유지 관리 하는 Exchange Server 환경을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-148">The accompanying diagram shows an Exchange Server environment that is operated and maintained by a provider.</span></span>
  
<span data-ttu-id="8bb49-149">기능 및 기능을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-149">Description of features and functionality:</span></span>
  
- <span data-ttu-id="8bb49-150">서버 및 서버 소프트웨어의 작업은 공급자에 의해 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-150">The operation of servers and server software is handled by your provider.</span></span>
    
- <span data-ttu-id="8bb49-151">계획, 크기 조정, 배율 및 Exchange 서버 인프라의 유지 관리 공급자에 위임 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-151">Planning, sizing, scaling, and maintenance of the Exchange Server infrastructure are delegated to your provider.</span></span>
    
- <span data-ttu-id="8bb49-152">유지 관리 서비스 공급자에 의해 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-152">Service maintenance is handled by your provider.</span></span>
    
- <span data-ttu-id="8bb49-153">Exchange 기능 집합은 공급자가 배포 된 소프트웨어 버전으로 제한 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-153">The Exchange feature set is limited to the software version deployed by your provider.</span></span>
    
### <a name="benefits-of-implementing-each-deployment-option"></a><span data-ttu-id="8bb49-154">각 배포 옵션을 구현 하는의 이점</span><span class="sxs-lookup"><span data-stu-id="8bb49-154">Benefits of implementing each deployment option</span></span>

#### <a name="exchange-online-office-365"></a><span data-ttu-id="8bb49-155">Exchange Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="8bb49-155">Exchange Online (Office 365)</span></span>

<span data-ttu-id="8bb49-156">이 배포 옵션은 가장 적합 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-156">This deployment option is best for:</span></span>
  
- <span data-ttu-id="8bb49-157">온-프레미스에 대 한 작업 비용 절감을 고려 하는 조직에서는 배포를 교환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-157">Organizations looking to reduce operations costs for on-premises Exchange deployments.</span></span>
    
- <span data-ttu-id="8bb49-158">SharePoint Online 및 Lync Online 같은 다른 Office 365 제품을 활용 하려는 조직에서는 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-158">Organizations that plan to leverage other Office 365 offerings, such as SharePoint Online and Lync Online.</span></span>
    
#### <a name="exchange-hybrid"></a><span data-ttu-id="8bb49-159">Exchange 하이브리드</span><span class="sxs-lookup"><span data-stu-id="8bb49-159">Exchange Hybrid</span></span>

<span data-ttu-id="8bb49-160">이 배포 옵션은 가장 적합 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-160">This deployment option is best for:</span></span>
  
- <span data-ttu-id="8bb49-161">Exchange 온-프레미스에서 Exchange Online로 마이그레이션을 원활 하 게 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-161">Facilitating a migration from Exchange on-premises to Exchange Online.</span></span>
    
- <span data-ttu-id="8bb49-162">Branch office 인프라에 투자 하지 않고도 원격 사이트를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-162">Supporting remote sites without investing in branch office infrastructure.</span></span>
    
- <span data-ttu-id="8bb49-163">온-프레미스 상주 하는 데이터를 필요로 하는 자회사와 다국적 기업입니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-163">Multinational corporations with subsidiaries that require data to reside on-premises.</span></span>
    
#### <a name="exchange-server-on-premises"></a><span data-ttu-id="8bb49-164">Exchange Server 온-프레미스</span><span class="sxs-lookup"><span data-stu-id="8bb49-164">Exchange Server on-premises</span></span>

<span data-ttu-id="8bb49-165">이 배포 옵션은 가장 적합 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-165">This deployment option is best for:</span></span>
  
- <span data-ttu-id="8bb49-166">고도로 사용자 지정 된 솔루션입니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-166">Highly customized solutions.</span></span>
    
- <span data-ttu-id="8bb49-167">타사 구성 요소 하드웨어 및 소프트웨어를 활용 하는 Exchange Online에서 지원 하지 않는 사용 하 여 레거시 솔루션입니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-167">Legacy solutions with third-party components that depend on hardware and software that are not supported by Exchange Online.</span></span>
    
- <span data-ttu-id="8bb49-168">조직에서는 온-프레미스 상주 하는 데이터를 필요로 하는 데이터 관리 규정을 제목입니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-168">Organizations subject to data governance regulations that require data to reside on-premises.</span></span>
    
- <span data-ttu-id="8bb49-169">조직 전체 플랫폼 및 솔루션의 제어를 유지 하려면입니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-169">Organizations that wish to retain control of the entire platform and solution.</span></span>
    
#### <a name="provider-hosted-exchange"></a><span data-ttu-id="8bb49-170">Exchange 공급자 호스팅</span><span class="sxs-lookup"><span data-stu-id="8bb49-170">Provider-Hosted Exchange</span></span>

<span data-ttu-id="8bb49-171">이 배포 옵션은 가장 적합 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-171">This deployment option is best for:</span></span>
  
- <span data-ttu-id="8bb49-172">Exchange 서버 기능을 필요는 없지만 해당 배포 및 유지 관리를 아웃소싱 할 하려고 하는 조직입니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-172">Organizations that need Exchange Server functionality, but want to outsource its deployment and maintenance.</span></span>
    
- <span data-ttu-id="8bb49-173">개인 설정 된 지원 옵션 필요 하는 조직입니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-173">Organizations that need personalized support options.</span></span>
    
- <span data-ttu-id="8bb49-174">사용자 지정 된 솔루션 및 공급자가 제공 하는 사용자 지정 응용 프로그램과 통합 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-174">Customized solutions and integration with custom applications offered by the provider.</span></span>
    
- <span data-ttu-id="8bb49-175">타사 구성 요소 하드웨어 및 소프트웨어를 활용 하는 Exchange Online에서 지원 하지 않는 사용 하 여 레거시 솔루션입니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-175">Legacy solutions with third-party components that depend on hardware and software that are not supported by Exchange Online.</span></span>
    
### <a name="license-requirements"></a><span data-ttu-id="8bb49-176">라이선스 요구 사항</span><span class="sxs-lookup"><span data-stu-id="8bb49-176">License requirements</span></span>

<span data-ttu-id="8bb49-177">다음 표에서 각 배포 옵션에 대 한 라이선스 요구 사항에 자세히 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-177">The following table details the license requirements for each deployment option.</span></span>
  
|<span data-ttu-id="8bb49-178">**배포 옵션**</span><span class="sxs-lookup"><span data-stu-id="8bb49-178">**Deployment option**</span></span>|<span data-ttu-id="8bb49-179">**라이선스 요구 사항**</span><span class="sxs-lookup"><span data-stu-id="8bb49-179">**License requirements**</span></span>|
|:-----|:-----|
|<span data-ttu-id="8bb49-180">Exchange Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="8bb49-180">Exchange Online (Office 365)</span></span>  <br/> |<span data-ttu-id="8bb49-181">구독 모델</span><span class="sxs-lookup"><span data-stu-id="8bb49-181">Subscription model</span></span>  <br/> |
|<span data-ttu-id="8bb49-182">Exchange 하이브리드</span><span class="sxs-lookup"><span data-stu-id="8bb49-182">Exchange Hybrid</span></span>  <br/> | <span data-ttu-id="8bb49-183">Office 365-구독 모델</span><span class="sxs-lookup"><span data-stu-id="8bb49-183">Office 365 - Subscription model</span></span> <br/>  <span data-ttu-id="8bb49-184">온-프레미스-모든 온-프레미스 라이선스 적용 (Exchange Server 온-프레미스에 대 한 검토 라이선스)</span><span class="sxs-lookup"><span data-stu-id="8bb49-184">On-premises - All on-premises licenses apply (review licenses for Exchanges Server on-premises)</span></span> <br/>  <span data-ttu-id="8bb49-185">하이브리드 서버 라이선스 \*</span><span class="sxs-lookup"><span data-stu-id="8bb49-185">Hybrid server license\*</span></span> <br/> |
|<span data-ttu-id="8bb49-186">Exchange Server 온-프레미스</span><span class="sxs-lookup"><span data-stu-id="8bb49-186">Exchange Server on-premises</span></span>  <br/> | <span data-ttu-id="8bb49-187">서버 운영 체제</span><span class="sxs-lookup"><span data-stu-id="8bb49-187">Server Operating System</span></span> <br/>  <span data-ttu-id="8bb49-188">Exchange 2013 서버 라이선스</span><span class="sxs-lookup"><span data-stu-id="8bb49-188">Exchange 2013 Server License</span></span> <br/>  <span data-ttu-id="8bb49-189">Exchange 2013 클라이언트 액세스 라이선스</span><span class="sxs-lookup"><span data-stu-id="8bb49-189">Exchange 2013 Client Access License</span></span> <br/> |
|<span data-ttu-id="8bb49-190">Exchange 공급자 호스팅</span><span class="sxs-lookup"><span data-stu-id="8bb49-190">Provider-Hosted Exchange</span></span>  <br/> |<span data-ttu-id="8bb49-191">비용을 기반으로 공급자와 계약</span><span class="sxs-lookup"><span data-stu-id="8bb49-191">Costs are based on the agreement with the provider</span></span>  <br/> |
   
### <a name="architecture-tasks"></a><span data-ttu-id="8bb49-192">아키텍처 작업</span><span class="sxs-lookup"><span data-stu-id="8bb49-192">Architecture tasks</span></span>

<span data-ttu-id="8bb49-193">이 섹션에서는 각 배포 옵션에 대 한 아키텍처 작업을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-193">This section lists the architectural tasks for each deployment option.</span></span>
  
#### <a name="exchange-online-office-365"></a><span data-ttu-id="8bb49-194">Exchange Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="8bb49-194">Exchange Online (Office 365)</span></span>

- <span data-ttu-id="8bb49-195">계획 하 고 디렉터리 동기화를 디자인 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-195">Plan and design the directory synchronization.</span></span>
    
- <span data-ttu-id="8bb49-196">네트워크 용량 및 방화벽, 프록시 서버, 게이트웨이 통해 및 WAN 링크에서 연결을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-196">Ensure network capacity and connectivity through firewalls, proxy servers, gateways, and across WAN links.</span></span>
    
#### <a name="exchange-hybrid"></a><span data-ttu-id="8bb49-197">Exchange 하이브리드</span><span class="sxs-lookup"><span data-stu-id="8bb49-197">Exchange Hybrid</span></span>

<span data-ttu-id="8bb49-198">Office 365와 온-프레미스 환경에 대 한 아키텍처 작업 외에도:</span><span class="sxs-lookup"><span data-stu-id="8bb49-198">In addition to the architecture tasks for both the Office 365 and on-premises environments:</span></span>
  
- <span data-ttu-id="8bb49-199">환경에는 단일 기호 (+)를 제공 여부를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-199">Decide whether to provide a single-sign on experience.</span></span>
    
- <span data-ttu-id="8bb49-200">온-프레미스 조직을 통해 또는 Exchange Online Protection을 통한 인바운드 인터넷 메일을 라우팅하 여부를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-200">Decide whether to route inbound Internet mail through an on-premises organization or through Exchange Online Protection.</span></span>
    
#### <a name="exchange-server-on-premises"></a><span data-ttu-id="8bb49-201">Exchange Server 온-프레미스</span><span class="sxs-lookup"><span data-stu-id="8bb49-201">Exchange Server on-premises</span></span>

- <span data-ttu-id="8bb49-202">Exchange 토폴로지를 디자인 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-202">Design the Exchange topology.</span></span>
    
- <span data-ttu-id="8bb49-203">서버 하드웨어에 대 한 용량을 계획 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-203">Plan the capacity for server hardware.</span></span>
    
- <span data-ttu-id="8bb49-204">메시지 라우팅 토폴로지를 디자인 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-204">Design the message routing topology.</span></span>
    
- <span data-ttu-id="8bb49-205">클라이언트 액세스 서버에 대해 부하 분산을 디자인 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-205">Design load balancing for Client Access servers.</span></span>
    
- <span data-ttu-id="8bb49-206">데이터베이스 가용성 그룹을 사용 하 여 고가용성을 위한 계획 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-206">Plan for high availability using database availability groups.</span></span>
    
#### <a name="provider-hosted-exchange"></a><span data-ttu-id="8bb49-207">Exchange 공급자 호스팅</span><span class="sxs-lookup"><span data-stu-id="8bb49-207">Provider-Hosted Exchange</span></span>

<span data-ttu-id="8bb49-208">네트워크 용량 및 방화벽, 프록시 서버, 게이트웨이 통해 사용 가능 여부를 확인 하 고 WAN 링크에서 공급자에 사용할 수 있는 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-208">Ensure that the network capacity and availability through firewalls, proxy servers, gateways, and across WAN links are available to your provider.</span></span>
  
### <a name="it-pro-responsibilities"></a><span data-ttu-id="8bb49-209">IT 전문가 책임</span><span class="sxs-lookup"><span data-stu-id="8bb49-209">IT Pro responsibilities</span></span>

<span data-ttu-id="8bb49-210">이 섹션에서는 각 배포 옵션에 대 한 IT 전문가 용 책임을 부여 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-210">This section lists the IT Pro responsibilities for each deployment option.</span></span>
  
#### <a name="exchange-online-office-365"></a><span data-ttu-id="8bb49-211">Exchange Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="8bb49-211">Exchange Online (Office 365)</span></span>

- <span data-ttu-id="8bb49-212">디렉터리 동기화 계획을 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-212">Implement the directory synchronization plan.</span></span>
    
- <span data-ttu-id="8bb49-213">계획 하 고 내부 및 외부 DNS 레코드 및 라우팅을 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-213">Plan and implement internal and external DNS records and routing.</span></span>
    
- <span data-ttu-id="8bb49-214">프록시 서버 또는 Office 365 IP 주소 및 URL 요구 사항에 대 한 방화벽을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-214">Configure the proxy server or firewall for the Office 365 IP address and URL requirements.</span></span>
    
- <span data-ttu-id="8bb49-215">사용자 계정 및 Exchange Online 설정을 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-215">Administer the user accounts and the Exchange Online settings.</span></span>
    
#### <a name="exchange-hybrid"></a><span data-ttu-id="8bb49-216">Exchange 하이브리드</span><span class="sxs-lookup"><span data-stu-id="8bb49-216">Exchange Hybrid</span></span>

<span data-ttu-id="8bb49-217">Office 365와 온-프레미스 환경에 대 한 IT 전문가 용 책임 외에도:</span><span class="sxs-lookup"><span data-stu-id="8bb49-217">In addition to the IT Pro responsibilities for both the Office 365 and on-premises environments:</span></span>
  
- <span data-ttu-id="8bb49-218">(필요한 경우)에서 Active Directory Federation Services (AD FS)에 대 한 단일 기호 (+)를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-218">Configure Active Directory Federation Services (AD FS) for single-sign on (if desired).</span></span>
    
- <span data-ttu-id="8bb49-219">Exchange 2013 서버와 Office 365 간의 보안 통신에 대 한 Exchange 인증서를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-219">Configure Exchange certificates for secure communications between Exchange 2013 servers and Office 365.</span></span>
    
- <span data-ttu-id="8bb49-220">원하는 인바운드 인터넷 메일 경로 대 한 DNS 레코드를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-220">Configure DNS records for the desired inbound Internet mail path.</span></span>
    
#### <a name="exchange-server-on-premises"></a><span data-ttu-id="8bb49-221">Exchange Server 온-프레미스</span><span class="sxs-lookup"><span data-stu-id="8bb49-221">Exchange Server on-premises</span></span>

- <span data-ttu-id="8bb49-222">Exchange 서비스에 대 한 필요한 인증서를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-222">Configure the necessary certificates for Exchange services.</span></span>
    
- <span data-ttu-id="8bb49-223">서버를 구축 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-223">Provision the servers.</span></span>
    
- <span data-ttu-id="8bb49-224">Exchange 메시지 라우팅 토폴로지를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-224">Implement the Exchange message routing topology.</span></span>
    
- <span data-ttu-id="8bb49-225">데이터베이스 가용성 그룹을 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-225">Implement database availability groups.</span></span>
    
- <span data-ttu-id="8bb49-226">업데이트 하 고 Exchange 서버를 유지 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-226">Update and maintain Exchange servers.</span></span>
    
- <span data-ttu-id="8bb49-227">사용률에 따라 추가 또는 필요에 따라 서버를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-227">Depending on utilization, add or remove servers as needed.</span></span>
    
#### <a name="provider-hosted-exchange"></a><span data-ttu-id="8bb49-228">Exchange 공급자 호스팅</span><span class="sxs-lookup"><span data-stu-id="8bb49-228">Provider-Hosted Exchange</span></span>

<span data-ttu-id="8bb49-229">공급자의 책임에는 다음이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-229">The provider's responsibilities include:</span></span>
  
- <span data-ttu-id="8bb49-230">시스템 및 서비스 유지 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-230">System and service maintenance.</span></span>
    
- <span data-ttu-id="8bb49-231">롤아웃 기능을 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-231">Feature rollouts.</span></span>
    
- <span data-ttu-id="8bb49-232">데이터 보호 및 재해 복구 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-232">Data protection and disaster recovery.</span></span>
    
<span data-ttu-id="8bb49-233">조직에서 IT 직원의 책임을 만들고 사용자 계정 관리를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-233">The IT staff's responsibilities in your organization include creating and managing user accounts.</span></span>
  
#### <a name="more-information"></a><span data-ttu-id="8bb49-234">추가 정보</span><span class="sxs-lookup"><span data-stu-id="8bb49-234">More information</span></span>

<span data-ttu-id="8bb49-235">Exchange Online (Office 365)에 대 한 자세한 내용은 다음 항목을 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-235">To learn more about Exchange Online (Office 365), see the following:</span></span>
  
- [<span data-ttu-id="8bb49-236">Exchange Online 서비스 설명</span><span class="sxs-lookup"><span data-stu-id="8bb49-236">Exchange Online service description</span></span>](https://aka.ms/EXOSD)
    
- [<span data-ttu-id="8bb49-237">TechNet 라이브러리의 Exchange Online</span><span class="sxs-lookup"><span data-stu-id="8bb49-237">Exchange Online library on TechNet</span></span>](https://aka.ms/EXOTN)
    
- [<span data-ttu-id="8bb49-238">Exchange Online 포털</span><span class="sxs-lookup"><span data-stu-id="8bb49-238">Exchange Online portal</span></span>](https://aka.ms/EXO)
    
<span data-ttu-id="8bb49-239">Exchange 하이브리드에 대 한 자세한 내용은 다음 항목을 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-239">To learn more about Exchange Hybrid, see the following:</span></span>
  
- <span data-ttu-id="8bb49-p104">[Exchange 2013 하이브리드 배포](https://aka.ms/ExchangeHybrid)합니다. 하이브리드 서버 라이선스만 인지에 주의 해야 다음과 같은 시나리오에 필요한: Exchange 2013 하이브리드 서버 및 Exchange 2007 조직의 Exchange 2013 또는 Exchange 2010 하이브리드 서버와 함께 사용 하 여 Exchange 2010 조직입니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-p104">[Exchange 2013 hybrid deployments](https://aka.ms/ExchangeHybrid). You should note that the Hybrid server license is only required for the following scenarios: Exchange 2010 organization with Exchange 2013 hybrid server and Exchange 2007 organization with Exchange 2013 or Exchange 2010 hybrid server.</span></span>
    
- [<span data-ttu-id="8bb49-242">Office 365 로그인</span><span class="sxs-lookup"><span data-stu-id="8bb49-242">Office 365 Sign in</span></span>](https://aka.ms/HybridKey)
    
<span data-ttu-id="8bb49-243">Exchange Server 온-프레미스에 대 한 자세한 내용은 다음 항목을 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-243">To learn more about Exchange Server on-premises, see the following:</span></span>
  
- [<span data-ttu-id="8bb49-244">Exchange Server 2013 TechNet 라이브러리</span><span class="sxs-lookup"><span data-stu-id="8bb49-244">Exchange Server 2013 library on TechNet</span></span>](https://aka.ms/Ex2013TN)
    
- [<span data-ttu-id="8bb49-245">Exchange Server 2013 포털</span><span class="sxs-lookup"><span data-stu-id="8bb49-245">Exchange Server 2013 portal</span></span>](https://aka.ms/Exchange2013)
    
- [<span data-ttu-id="8bb49-246">Exchange Server 2013의 아키텍처</span><span class="sxs-lookup"><span data-stu-id="8bb49-246">Exchange Server 2013 architecture</span></span>](https://aka.ms/Ex2013SP1ArchPoster)
    
<span data-ttu-id="8bb49-247">Provider-Hosted Exchange에 대 한 자세한 내용은 다음 항목을 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-247">To learn more about Provider-Hosted Exchange, see the following:</span></span>
  
[<span data-ttu-id="8bb49-248">Exchange Server 2013 호스팅 및 다중 테 넌 시 솔루션 및 지침</span><span class="sxs-lookup"><span data-stu-id="8bb49-248">Exchange Server 2013 hosting and multi-tenancy solutions and guidance</span></span>](https://aka.ms/Ex2013Hosting)
  
## <a name="descriptions-of-three-new-or-updated-features-in-exchange-2013"></a><span data-ttu-id="8bb49-249">Exchange 2013의 세 신규 또는 업데이트 된 기능에 대 한 설명이</span><span class="sxs-lookup"><span data-stu-id="8bb49-249">Descriptions of three new or updated features in Exchange 2013</span></span>

### <a name="exchange-online-protection"></a><span data-ttu-id="8bb49-250">Exchange Online Protection</span><span class="sxs-lookup"><span data-stu-id="8bb49-250">Exchange Online Protection</span></span>

<span data-ttu-id="8bb49-p105">Exchange Online Protection (EOP) 계층 데이터 센터의 글로벌 네트워크를 통해 배포 되는 보호 기능을 제공 하 여 모든 배포에 대 한 스팸 방지 및 맬웨어 방지 보호 기능을 제공 합니다. 이 통해 메시징 환경 관리를 단순화할 수 있습니다. EOP Exchange Online 구독에 포함 되어 있지만 하이브리드 및 온-프레미스 배포를 위한도 활용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-p105">Exchange Online Protection (EOP) provides anti-spam and anti-malware protection for any deployment by providing a layer of protection features that are deployed across a global network of data centers. This helps you to simplify the management of your messaging environments. EOP is included in Exchange Online subscriptions, but you can also leverage it for hybrid and on-premises deployments.</span></span>
  
<span data-ttu-id="8bb49-254">함께 제공 되는 다이어그램에 대해 Exchange Online, Exchange 하이브리드 Exchange 온-프레미스 및 전역 네트워크에서 EOP 계층을 포함 하는 배포를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-254">The accompanying diagrams show deployments for Exchange Online, Exchange Hybrid, and Exchange on-premises that include the EOP layer in the global network.</span></span>
  
### <a name="exchange-server-deployment-assistant"></a><span data-ttu-id="8bb49-255">Exchange Server 배포 도우미</span><span class="sxs-lookup"><span data-stu-id="8bb49-255">Exchange Server Deployment Assistant</span></span>

<span data-ttu-id="8bb49-p106">Exchange Server 배포 도우미는 현재 환경에 대 한 몇가지 질문을 요청 하 고 다음 다양 한 유형의 시나리오에 대 한 Exchange 서버를 배포 하는 데 도움이 되도록 사용자 지정 단계별 검사 목록을 생성 하는 웹 기반 도구입니다. 만들지 여부를 Exchange에 Exchange 2013의 이전 버전에서 마이그레이션할 Exchange Online으로 마이그레이션하거나 하이브리드 인프라를 계획 Exchange Server 배포 도우미 시나리오에 대 한 사용자 지정 된 배포 검사 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-p106">The Exchange Server Deployment Assistant is a web-based tool that asks you a few questions about your current environment, and then generates a custom step-by-step checklist to help you deploy Exchange Server for different types of scenarios. Whether you are migrating from a previous version of Exchange to Exchange 2013, migrating to Exchange Online, or planning a hybrid infrastructure, the Exchange Server Deployment Assistant creates a customized deployment checklist for your scenario.</span></span>
  
<span data-ttu-id="8bb49-258">함께 제공 되 스크린샷에서 Exchange Server 배포 도우미를 사용 하 여 만든 예제 검사 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-258">The accompanying screenshot shows an example checklist that was created using the Exchange Server Deployment Assistant.</span></span>
  
### <a name="integration-with-lync-and-sharepoint"></a><span data-ttu-id="8bb49-259">Lync 및 SharePoint와의 통합</span><span class="sxs-lookup"><span data-stu-id="8bb49-259">Integration with Lync and SharePoint</span></span>

<span data-ttu-id="8bb49-p107">Exchange Server 2013 Lync Server 2013 및 SharePoint Server 2013와 통합 하는 다양 한 기능을 포함 합니다. 함께 이러한 제품은 풍부한 기능 집합을 제공 하 고 조직 전체에서 공동 작업을 향상 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-p107">Exchange Server 2013 includes many features that integrate with Lync Server 2013 and SharePoint Server 2013. Together, these products offer a rich suite of features and improve collaboration across your organization.</span></span> 
  
<span data-ttu-id="8bb49-262">함께 제공 되는 다이어그램 서버-서버 인증 포스터를 표시 하 고 포스터에 대 한 링크를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-262">An accompanying diagram shows the Server-to-Server Authentication poster and includes a link to the poster.</span></span> 
  
- <span data-ttu-id="8bb49-263">보관, 보류 및 eDiscovery</span><span class="sxs-lookup"><span data-stu-id="8bb49-263">Archiving, hold and eDiscovery</span></span>
    
- <span data-ttu-id="8bb49-264">사이트 사서함</span><span class="sxs-lookup"><span data-stu-id="8bb49-264">Site mailboxes</span></span>
    
- <span data-ttu-id="8bb49-265">통합 연락처 저장소</span><span class="sxs-lookup"><span data-stu-id="8bb49-265">Unified contact store</span></span>
    
- <span data-ttu-id="8bb49-266">고해상도 사용자 사진</span><span class="sxs-lookup"><span data-stu-id="8bb49-266">High-resolution user photos</span></span>
    
- <span data-ttu-id="8bb49-267">Outlook 및 Outlook Web App의 Lync 현재 상태</span><span class="sxs-lookup"><span data-stu-id="8bb49-267">Lync presence in Outlook and Outlook Web App</span></span>
    
- <span data-ttu-id="8bb49-268">서버 간 인증</span><span class="sxs-lookup"><span data-stu-id="8bb49-268">Server-to-server authentication</span></span>
    
- <span data-ttu-id="8bb49-269">Voicemail</span><span class="sxs-lookup"><span data-stu-id="8bb49-269">Voicemail</span></span>
    
- <span data-ttu-id="8bb49-270">모임 녹음/녹화</span><span class="sxs-lookup"><span data-stu-id="8bb49-270">Meeting recordings</span></span>
    
- <span data-ttu-id="8bb49-271">Exchange 작업 동기화</span><span class="sxs-lookup"><span data-stu-id="8bb49-271">Exchange task synchronization</span></span>
    
<span data-ttu-id="8bb49-272">함께 제공 되는 다이어그램 Exchange Server 2013 SP1 아키텍처 포스터를 표시 하 고 포스터에 대 한 링크를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bb49-272">An accompanying diagram shows the Exchange Server 2013 SP1 Architecture poster and includes a link to the poster.</span></span>
  

