---
title: 액세스 가능한 다이어그램-Microsoft Lync 2013 플랫폼 옵션
ms.author: josephd
author: JoeDavies-MSFT
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 2858d1e7-be37-4484-b121-a99779742a38
f1.keywords:
- NOCSH
description: 이 문서는 기술 다이어그램에서 사용할 수 있는 Microsoft Lync 2013 Platform Options 라는 액세스 가능한 텍스트 버전입니다.
ms.openlocfilehash: ff03899a57ff7fbd902cd3cacfc2005d27595c55
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844639"
---
# <a name="accessible-diagram---microsoft-lync-2013-platform-options"></a><span data-ttu-id="84d81-103">액세스 가능한 다이어그램-Microsoft Lync 2013 플랫폼 옵션</span><span class="sxs-lookup"><span data-stu-id="84d81-103">Accessible diagram - Microsoft Lync 2013 Platform Options</span></span>

<span data-ttu-id="84d81-104">**요약:** 이 문서는 [기술 다이어그램](https://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409)에서 사용할 수 있는 Microsoft Lync 2013 Platform Options 라는 액세스 가능한 텍스트 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-104">**Summary:** This article is an accessible text version of the diagram named Microsoft Lync 2013 Platform Options, which is available at [Technical Diagrams](https://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409).</span></span>
  
<span data-ttu-id="84d81-105">이 포스터는 BDMs (비즈니스 의사 결정권자) 및 설계자가 Lync Online (Office 365) 및 Lync Server 배포에 대해 알아야 할 사항에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-105">This poster describes what business decision makers (BDMs) and architects need to know about Lync Online (Office 365) and Lync Server deployments and includes:</span></span>
  
- <span data-ttu-id="84d81-106">Lync Online (Office 365), Lync Online/Server Hybrid, Lync Server 및 Provider Hosted Lync Server의 네 가지 서로 다른 배포 옵션을 비교 합니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-106">A comparison of four different deployment options: Lync Online (Office 365), Lync Online/Server Hybrid, Lync Server, and Provider-Hosted Lync Server.</span></span> 
    
- <span data-ttu-id="84d81-107">Lync 2013 배포에 대 한 두 가지 예제 시나리오</span><span class="sxs-lookup"><span data-stu-id="84d81-107">Two example scenarios for deploying Lync 2013.</span></span>
    
## <a name="comparison-of-four-different-deployments-for-the-lync-2013-platform"></a><span data-ttu-id="84d81-108">Lync 2013 플랫폼에 대해 네 가지 서로 다른 배포 비교</span><span class="sxs-lookup"><span data-stu-id="84d81-108">Comparison of four different deployments for the Lync 2013 platform</span></span>

<span data-ttu-id="84d81-109">비교에서는 다음 영역의 각 배포 옵션에 대 한 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-109">The comparison provides information about each deployment option in the following areas:</span></span> 
  
- <span data-ttu-id="84d81-110">다양 한 배포 기능에 대 한 개요</span><span class="sxs-lookup"><span data-stu-id="84d81-110">An overview of the different deployment features</span></span>
    
- <span data-ttu-id="84d81-111">각 배포 옵션을 구현할 때의 장점</span><span class="sxs-lookup"><span data-stu-id="84d81-111">Benefits of implementing each deployment option</span></span>
    
- <span data-ttu-id="84d81-112">라이선스 요구 사항</span><span class="sxs-lookup"><span data-stu-id="84d81-112">Licensing requirements</span></span>
    
- <span data-ttu-id="84d81-113">필수 아키텍처 작업</span><span class="sxs-lookup"><span data-stu-id="84d81-113">Required architectural tasks</span></span>
    
- <span data-ttu-id="84d81-114">각 배포 옵션을 구현 하는 IT 전문가 책임</span><span class="sxs-lookup"><span data-stu-id="84d81-114">IT Pro responsibilities for implementing each deployment option</span></span>
    
### <a name="overview"></a><span data-ttu-id="84d81-115">개요</span><span class="sxs-lookup"><span data-stu-id="84d81-115">Overview</span></span>

#### <a name="lync-online-office-365"></a><span data-ttu-id="84d81-116">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="84d81-116">Lync Online (Office 365)</span></span>

<span data-ttu-id="84d81-117">Office 365 다중 테 넌 트 요금제를 사용 하 여 비용을 효율성과 최적화 합니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-117">You gain efficiency and optimize for cost with Office 365 multitenant plans.</span></span>
  
<span data-ttu-id="84d81-118">함께 제공 되는 다이어그램에는 온-프레미스 AD DS (Active Directory 도메인 서비스) 환경 및 Azure Active Directory 테 넌 트 간의 계정 이름과 암호를 동기화 하는 Azure Active Directory 테 넌 트를 사용한 Lync Online이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-118">The accompanying diagram shows Lync Online with an Azure Active Directory tenant, which synchronizes account names and passwords between the on-premises Active Directory Domain Services (AD DS) environment and the Azure Active Directory tenant.</span></span> 
  
<span data-ttu-id="84d81-119">기능에 대 한 설명:</span><span class="sxs-lookup"><span data-stu-id="84d81-119">Description of features and functionality:</span></span>
  
- <span data-ttu-id="84d81-120">SaaS (Software as a Service)입니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-120">Software as a Service (SaaS).</span></span>
    
- <span data-ttu-id="84d81-121">항상 최신 상태로 유지 되는 다양 한 기능 집합</span><span class="sxs-lookup"><span data-stu-id="84d81-121">Rich feature set that is always up to date.</span></span>
    
- <span data-ttu-id="84d81-122">다른 응용 프로그램과 함께 사용할 수 있는 온라인 계정에 대 한 Azure Active Directory 테 넌 트를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-122">Includes an Azure Active Directory tenant for online accounts, which can be used with other applications.</span></span> 
    
- <span data-ttu-id="84d81-123">디렉터리 통합에는 온-프레미스 AD DS (Active Directory 도메인 서비스) 환경 및 Azure Active Directory 테 넌 트 사이에 계정 이름과 암호를 동기화 하는 작업이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-123">Directory integration includes synchronizing account names and passwords between the on-premises Active Directory Domain Services (AD DS) environment and the Azure Active Directory tenant.</span></span>
    
- <span data-ttu-id="84d81-124">SSO (single sign-on)가 요구 되는 경우에는 AD FS (Active Directory Federation Services)를 구현 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-124">If single sign-on (SSO) is a requirement, Active Directory Federation Services (AD FS) must be implemented.</span></span> 
    
- <span data-ttu-id="84d81-125">인터넷을 통한 클라이언트 통신은 암호화 되 고 인증 됩니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-125">Client communication over the Internet is encrypted and authenticated.</span></span>
    
- <span data-ttu-id="84d81-126">레거시 전화 장비, PSTN (공중 전화망), 타사 공급자를 통해 연결을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-126">Legacy phone equipment, public switched telephone network (PSTN), connectivity is available through third-party providers.</span></span>
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="84d81-127">Lync Online/Server Hybrid (분할 도메인)</span><span class="sxs-lookup"><span data-stu-id="84d81-127">Lync Online/Server Hybrid (split domain)</span></span>

<span data-ttu-id="84d81-128">Office 365의 혜택을 온-프레미스 Lync 2013 배포와 결합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-128">You can combine the benefits of Office 365 with an on-premises deployment of Lync 2013.</span></span>
  
<span data-ttu-id="84d81-129">함께 제공 되는 다이어그램에는 일부 사용자가 온-프레미스에 있고 일부 사용자가 온라인 상태에 있는 Office 365에서 Lync Online이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-129">The accompanying diagram shows Office 365 with Lync Online where some users are homed on-premises and some users are homed online.</span></span> <span data-ttu-id="84d81-130">온-프레미스에 배포 된에 지 서버도 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-130">An Edge Server that is deployed on-premises is also shown.</span></span>
  
<span data-ttu-id="84d81-131">기능에 대 한 설명:</span><span class="sxs-lookup"><span data-stu-id="84d81-131">Description of features and functionality:</span></span>
  
- <span data-ttu-id="84d81-132">일부 사용자가 온-프레미스에 있고 일부 사용자가 온라인 상태 이지만, 사용자가 같은 SIP 도메인 (예: contoso.com)을 공유 하는 경우</span><span class="sxs-lookup"><span data-stu-id="84d81-132">Some users are homed on premises and some users are homed online, but the users share the same SIP domain (such as contoso.com).</span></span>
    
- <span data-ttu-id="84d81-133">PSTN에 대 한 연결을 포함 하 여 기존 Lync Server 2013 인프라를 활용 합니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-133">Leverage your existing Lync Server 2013 infrastructure, including the connections to the PSTN.</span></span>
    
- <span data-ttu-id="84d81-134">PSTN이 필요 하지 않은 경우 새 Lync Online 사용자를 쉽게 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-134">Add new Lync Online users easily when they do not require PSTN.</span></span>
    
- <span data-ttu-id="84d81-135">일정에 따라 Lync 온-프레미스에서 Lync Online으로 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="84d81-135">Migrate from Lync on-premises to Lync Online over time, on your schedule.</span></span>
    
- <span data-ttu-id="84d81-136">Exchange Online 및 SharePoint Online을 비롯 한 다른 Office 365 응용 프로그램과 통합 됩니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-136">Integrate with other Office 365 applications, including Exchange Online and SharePoint Online.</span></span>
    
#### <a name="lync-server"></a><span data-ttu-id="84d81-137">Lync Server</span><span class="sxs-lookup"><span data-stu-id="84d81-137">Lync Server</span></span>

<span data-ttu-id="84d81-138">이 배포에서는 모든 것을 소유 합니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-138">In this deployment, you own everything.</span></span> <span data-ttu-id="84d81-139">함께 제공 되는 다이어그램에서는 사용자가 온-프레미스에 있는 온-프레미스 AD DS (Active Directory 도메인 서비스) 환경을 사용 하는 Lync Server 인프라를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-139">The accompanying diagram shows a Lync Server infrastructure with an on-premises Active Directory Domain Services (AD DS) environment where users are homed on-premises.</span></span>
  
<span data-ttu-id="84d81-140">기능에 대 한 설명:</span><span class="sxs-lookup"><span data-stu-id="84d81-140">Description of features and functionality:</span></span>
  
- <span data-ttu-id="84d81-141">용량 계획 및 크기 조정</span><span class="sxs-lookup"><span data-stu-id="84d81-141">Capacity planning and sizing.</span></span>
    
- <span data-ttu-id="84d81-142">서버 인식 및 설정</span><span class="sxs-lookup"><span data-stu-id="84d81-142">Server acquisition and setup.</span></span>
    
- <span data-ttu-id="84d81-143">배포.</span><span class="sxs-lookup"><span data-stu-id="84d81-143">Deployment.</span></span>
    
- <span data-ttu-id="84d81-144">수평 확장, 패치 및 작업</span><span class="sxs-lookup"><span data-stu-id="84d81-144">Scaling out, patching, and operations.</span></span>
    
- <span data-ttu-id="84d81-145">데이터 백업</span><span class="sxs-lookup"><span data-stu-id="84d81-145">Backing up data.</span></span>
    
- <span data-ttu-id="84d81-146">장애 조치 (failover) 및 재해 복구 유지 관리</span><span class="sxs-lookup"><span data-stu-id="84d81-146">Maintaining failover and disaster recovery.</span></span>
    
- <span data-ttu-id="84d81-147">Lync Server 2013 인프라를 PSTN에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-147">Connecting your Lync Server 2013 infrastructure to the PSTN.</span></span>
    
- <span data-ttu-id="84d81-148">Pbx (private branch 교환의)와 같은 기존 전화 장비와의 통합</span><span class="sxs-lookup"><span data-stu-id="84d81-148">Integration with existing phone equipment, such as private branch exchanges (PBXs).</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="84d81-149">공급자 호스트 Lync Server</span><span class="sxs-lookup"><span data-stu-id="84d81-149">Provider-Hosted Lync Server</span></span>

<span data-ttu-id="84d81-150">이 배포에서 공급자는 모든 항목을 소유 합니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-150">In this deployment, your provider owns everything.</span></span> <span data-ttu-id="84d81-151">함께 제공 되는 다이어그램에서는 온-프레미스 환경에 대 한 연결을 사용 하 여 서버 및 장비를 포함 하는 공급자의 네트워크를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-151">The accompanying diagram shows a provider's network including their servers and equipment with a connection to an on-premises environment.</span></span>
  
<span data-ttu-id="84d81-152">기능에 대 한 설명:</span><span class="sxs-lookup"><span data-stu-id="84d81-152">Description of features and functionality:</span></span>
  
- <span data-ttu-id="84d81-153">용량 계획 및 크기 조정</span><span class="sxs-lookup"><span data-stu-id="84d81-153">Capacity planning and sizing.</span></span>
    
- <span data-ttu-id="84d81-154">서버 인식 및 설정</span><span class="sxs-lookup"><span data-stu-id="84d81-154">Server acquisition and setup.</span></span>
    
- <span data-ttu-id="84d81-155">배포.</span><span class="sxs-lookup"><span data-stu-id="84d81-155">Deployment.</span></span>
    
- <span data-ttu-id="84d81-156">수평 확장, 패치 및 작업</span><span class="sxs-lookup"><span data-stu-id="84d81-156">Scaling out, patching, and operations.</span></span>
    
- <span data-ttu-id="84d81-157">데이터 백업</span><span class="sxs-lookup"><span data-stu-id="84d81-157">Backing up data.</span></span>
    
- <span data-ttu-id="84d81-158">장애 조치 (failover) 및 재해 복구 유지 관리</span><span class="sxs-lookup"><span data-stu-id="84d81-158">Maintaining failover and disaster recovery.</span></span>
    
- <span data-ttu-id="84d81-159">Pbx (private branch 교환의)와 같은 기존 전화 장비와의 통합</span><span class="sxs-lookup"><span data-stu-id="84d81-159">Integration with existing phone equipment, such as private branch exchanges (PBXs).</span></span>
    
- <span data-ttu-id="84d81-160">또한 공급자는 다음과 같은 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-160">In addition, the provider can:</span></span>
    
  - <span data-ttu-id="84d81-161">온-프레미스 (실선) 연결을 사용 하 여 자체 네트워크에 서버 및 장비를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-161">Install their servers and equipment in their own network with a connection to your premises (solid line).</span></span>
    
  - <span data-ttu-id="84d81-162">온-프레미스 (점선)에 서버를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-162">Install their servers on your premises (dotted line).</span></span>
    
### <a name="benefits-of-implementing-each-deployment-option"></a><span data-ttu-id="84d81-163">각 배포 옵션을 구현할 때의 장점</span><span class="sxs-lookup"><span data-stu-id="84d81-163">Benefits of implementing each deployment option</span></span>

#### <a name="lync-online-office-365"></a><span data-ttu-id="84d81-164">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="84d81-164">Lync Online (Office 365)</span></span>

- <span data-ttu-id="84d81-165">온-프레미스 서버 또는 서버 소프트웨어의 작동 부담을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-165">No operational burden of on-premises servers or server software.</span></span>
    
- <span data-ttu-id="84d81-166">Lync Server 2013의 통신 기능은 클라우드 기반 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-166">Communication capabilities of Lync Server 2013 as a cloud-based service.</span></span>
    
- <span data-ttu-id="84d81-167">Lync 현재 상태, 인스턴트 메시징, 오디오 및 비디오 통화, 리치 온라인 모임, 다양 한 웹 회의 기능</span><span class="sxs-lookup"><span data-stu-id="84d81-167">Lync presence, instant messaging, audio and video calling, rich online meetings, and extensive web conferencing capabilities.</span></span>
    
- <span data-ttu-id="84d81-168">지리적으로 분산 된 조직이 나 주로 모바일 직원과 함께 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-168">Used with geographically-dispersed organizations or with primarily mobile employees.</span></span>
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="84d81-169">Lync Online/Server Hybrid (분할 도메인)</span><span class="sxs-lookup"><span data-stu-id="84d81-169">Lync Online/Server Hybrid (split domain)</span></span>

- <span data-ttu-id="84d81-170">원격 사용자에 대해 Lync Online을 사용 하 고 비즈니스 파트너와 통합 합니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-170">Use Lync Online for remote users and integration with business partners.</span></span>
    
- <span data-ttu-id="84d81-171">Lync 온-프레미스에서 Lync Online으로 쉽게 마이그레이션할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-171">Facilitate a migration from Lync on-premises to Lync Online.</span></span>
    
- <span data-ttu-id="84d81-172">Branch office 어플라이언스를 사용 하지 않고 원격 사이트를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-172">Support remote sites without using a branch office appliance.</span></span>
    
- <span data-ttu-id="84d81-173">새로운 비즈니스 인수에 대 한 Lync 지원을 쉽게 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-173">Ease of adding Lync support for new business acquisitions.</span></span>
    
#### <a name="lync-server"></a><span data-ttu-id="84d81-174">Lync Server</span><span class="sxs-lookup"><span data-stu-id="84d81-174">Lync Server</span></span>

- <span data-ttu-id="84d81-175">사설 클라우드 솔루션</span><span class="sxs-lookup"><span data-stu-id="84d81-175">Private cloud solutions.</span></span>
    
- <span data-ttu-id="84d81-176">고도로 사용자 지정 된 솔루션</span><span class="sxs-lookup"><span data-stu-id="84d81-176">Highly customized solutions.</span></span>
    
- <span data-ttu-id="84d81-177">Lync Online에서 지원 되지 않는 하드웨어 및 소프트웨어에 따라 다른 타사 구성 요소를 사용 하는 레거시 솔루션</span><span class="sxs-lookup"><span data-stu-id="84d81-177">Legacy solutions with third-party components that depend on hardware and software that are not supported by Lync Online.</span></span>
    
- <span data-ttu-id="84d81-178">Office 365와의 AD DS 계정을 동기화 하지 못하도록 하는 개인 정보 제한입니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-178">Privacy restrictions that prevent synchronization of AD DS accounts with Office 365.</span></span>
    
- <span data-ttu-id="84d81-179">전체 플랫폼과 솔루션의 제어를 원하는 조직</span><span class="sxs-lookup"><span data-stu-id="84d81-179">Organizations that desire control of the entire platform and solution.</span></span>
    
- <span data-ttu-id="84d81-180">Lync Enterprise Voice를 사용한 PBX 교체</span><span class="sxs-lookup"><span data-stu-id="84d81-180">PBX replacement with Lync Enterprise Voice.</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="84d81-181">공급자 호스트 Lync Server</span><span class="sxs-lookup"><span data-stu-id="84d81-181">Provider-Hosted Lync Server</span></span>

- <span data-ttu-id="84d81-182">Lync Server 기능을 관리 하지만 배포 및 유지 관리를 아웃소싱 하려는 조직</span><span class="sxs-lookup"><span data-stu-id="84d81-182">Organizations that want Lync Server functionality but want to outsource its deployment and maintenance.</span></span>
    
- <span data-ttu-id="84d81-183">공급자 기반 솔루션</span><span class="sxs-lookup"><span data-stu-id="84d81-183">Provider-based solutions.</span></span>
    
- <span data-ttu-id="84d81-184">고도로 사용자 지정 된 솔루션</span><span class="sxs-lookup"><span data-stu-id="84d81-184">Highly customized solutions.</span></span>
    
- <span data-ttu-id="84d81-185">Lync Online에서 지원 되지 않는 하드웨어 및 소프트웨어에 따라 다른 타사 구성 요소를 사용 하는 레거시 솔루션</span><span class="sxs-lookup"><span data-stu-id="84d81-185">Legacy solutions with third-party components that depend on hardware and software that are not supported by Lync Online.</span></span>
    
- <span data-ttu-id="84d81-186">Lync Enterprise Voice를 사용한 PBX 교체</span><span class="sxs-lookup"><span data-stu-id="84d81-186">PBX replacement with Lync Enterprise Voice.</span></span>
    
### <a name="license-requirements"></a><span data-ttu-id="84d81-187">라이선스 요구 사항</span><span class="sxs-lookup"><span data-stu-id="84d81-187">License requirements</span></span>

#### <a name="lync-online-office-365"></a><span data-ttu-id="84d81-188">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="84d81-188">Lync Online (Office 365)</span></span>

<span data-ttu-id="84d81-189">구독 모델</span><span class="sxs-lookup"><span data-stu-id="84d81-189">Subscription model.</span></span>
  
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="84d81-190">Lync Online/Server Hybrid (분할 도메인)</span><span class="sxs-lookup"><span data-stu-id="84d81-190">Lync Online/Server Hybrid (split domain)</span></span>

- <span data-ttu-id="84d81-191">Office 365 — 구독 모델</span><span class="sxs-lookup"><span data-stu-id="84d81-191">Office 365 — Subscription model.</span></span> <span data-ttu-id="84d81-192">추가 라이선스가 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-192">No additional licenses needed.</span></span> 
    
- <span data-ttu-id="84d81-193">온-프레미스-모든 온-프레미스 라이선스가 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-193">On-premises — All on-premises licenses apply.</span></span> 
    
#### <a name="lync-server"></a><span data-ttu-id="84d81-194">Lync Server</span><span class="sxs-lookup"><span data-stu-id="84d81-194">Lync Server</span></span>

- <span data-ttu-id="84d81-195">서버 운영 체제</span><span class="sxs-lookup"><span data-stu-id="84d81-195">Server Operating System</span></span>
    
- <span data-ttu-id="84d81-196">SQL Server</span><span class="sxs-lookup"><span data-stu-id="84d81-196">SQL Server</span></span>
    
- <span data-ttu-id="84d81-197">Lync 2013 서버 라이선스</span><span class="sxs-lookup"><span data-stu-id="84d81-197">Lync 2013 Server License</span></span>
    
- <span data-ttu-id="84d81-198">Lync 2013 클라이언트 액세스 라이선스</span><span class="sxs-lookup"><span data-stu-id="84d81-198">Lync 2013 Client Access License</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="84d81-199">공급자 호스트 Lync Server</span><span class="sxs-lookup"><span data-stu-id="84d81-199">Provider-Hosted Lync Server</span></span>

<span data-ttu-id="84d81-200">비용은 Lync 솔루션 공급자와의 계약을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-200">Costs are based on the agreement with your Lync solution provider.</span></span>
  
### <a name="architecture-tasks"></a><span data-ttu-id="84d81-201">아키텍처 작업</span><span class="sxs-lookup"><span data-stu-id="84d81-201">Architecture tasks</span></span>

<span data-ttu-id="84d81-202">이 섹션에서는 각 배포 옵션에 대 한 아키텍처 작업을 소개 합니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-202">This section lists the architectural tasks for each deployment option.</span></span>
  
#### <a name="lync-online-office-365"></a><span data-ttu-id="84d81-203">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="84d81-203">Lync Online (Office 365)</span></span>

- <span data-ttu-id="84d81-204">디렉터리 동기화를 계획 및 디자인 합니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-204">Plan and design directory synchronization.</span></span>
    
- <span data-ttu-id="84d81-205">방화벽, 프록시 서버, 게이트웨이 및 WAN 링크를 통해 네트워크 용량과 사용 가능 여부를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-205">Ensure network capacity and availability through firewalls, proxy servers, gateways, and across WAN links.</span></span>
    
- <span data-ttu-id="84d81-206">타사 SSL 인증서를 취득 하 여 Office 365 서비스 제품에 대해 엔터프라이즈 보안을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-206">Acquire third-party SSL certificates to provide enterprise-security for Office 365 service offerings.</span></span>
    
- <span data-ttu-id="84d81-207">IPv6 (인터넷 프로토콜 버전 6)을 사용 하 여 Office 365에 연결할지 여부를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-207">Decide if you want to connect to Office 365 with Internet Protocol version 6 (IPv6).</span></span>
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="84d81-208">Lync Online/Server Hybrid (분할 도메인)</span><span class="sxs-lookup"><span data-stu-id="84d81-208">Lync Online/Server Hybrid (split domain)</span></span>

<span data-ttu-id="84d81-209">Office 365 및 온-프레미스 환경 둘 다에 대 한 작업 외에도 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-209">In addition to tasks for both the Office 365 and on-premises environments:</span></span>
  
- <span data-ttu-id="84d81-210">Exchange Server 및 SharePoint의 온-프레미스 및 온라인 버전에서 사용할 기능 통합 용량을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-210">Determine how much feature integration you want to use with on-premises and online versions of Exchange Server and SharePoint.</span></span>
    
- <span data-ttu-id="84d81-211">필요한 경우 Office 365의 요청에 사용할 프록시 서버 장치를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-211">If required, determine which proxy server device will be used for requests from Office 365.</span></span>
    
#### <a name="lync-server"></a><span data-ttu-id="84d81-212">Lync Server</span><span class="sxs-lookup"><span data-stu-id="84d81-212">Lync Server</span></span>

<span data-ttu-id="84d81-213">기존 온-프레미스 환경에서 Lync 환경을 디자인 합니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-213">Design the Lync environment in an existing on-premises environment:</span></span>
  
- <span data-ttu-id="84d81-214">중앙 및 지사의 Lync 토폴로지</span><span class="sxs-lookup"><span data-stu-id="84d81-214">Lync topology for central and branch offices.</span></span>
    
- <span data-ttu-id="84d81-215">가상화를 비롯 한 서버 하드웨어</span><span class="sxs-lookup"><span data-stu-id="84d81-215">Server hardware, including virtualization.</span></span>
    
- <span data-ttu-id="84d81-216">AD DS (Active Directory 도메인 서비스) 및 DNS와의 통합</span><span class="sxs-lookup"><span data-stu-id="84d81-216">Integration with Active Directory Domain Services (AD DS) and DNS.</span></span>
    
- <span data-ttu-id="84d81-217">Lync server 풀에 대 한 부하 분산</span><span class="sxs-lookup"><span data-stu-id="84d81-217">Load balancing for Lync server pools.</span></span>
    
- <span data-ttu-id="84d81-218">장애 조치 (Failover) 및 재해 복구</span><span class="sxs-lookup"><span data-stu-id="84d81-218">Failover and disaster recovery.</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="84d81-219">공급자 호스트 Lync Server</span><span class="sxs-lookup"><span data-stu-id="84d81-219">Provider-Hosted Lync Server</span></span>

- <span data-ttu-id="84d81-220">클라우드 기반 설치의 경우 서비스 공급자의 네트워크에 대 한 연결을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-220">For a cloud-based installation, determine the connection to the service provider's network.</span></span>
    
- <span data-ttu-id="84d81-221">온-프레미스 설치의 경우 네트워크에서 공급자의 Lync server 배치를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-221">For an on-premises installation, determine the placement of the provider's Lync servers on your network.</span></span>
    
- <span data-ttu-id="84d81-222">두 유형 모두에 대해 AD DS 및 PBX 장비와의 통합을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-222">For both types, determine the integration with AD DS and your PBX equipment.</span></span>
    
### <a name="it-pro-responsibilities"></a><span data-ttu-id="84d81-223">IT 전문가 책임</span><span class="sxs-lookup"><span data-stu-id="84d81-223">IT Pro responsibilities</span></span>

<span data-ttu-id="84d81-224">이 섹션에서는 각 배포 옵션에 대 한 IT 전문가 책임을 소개 합니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-224">This section lists the IT Pro responsibilities for each deployment option.</span></span>
  
#### <a name="lync-online-office-365"></a><span data-ttu-id="84d81-225">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="84d81-225">Lync Online (Office 365)</span></span>

<span data-ttu-id="84d81-226">Lync Online 배포 및 관리 (Office 365):</span><span class="sxs-lookup"><span data-stu-id="84d81-226">Deploy and manage Lync Online (Office 365):</span></span>
  
- <span data-ttu-id="84d81-227">디렉터리 동기화 계획을 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-227">Implement the directory synchronization plan.</span></span>
    
- <span data-ttu-id="84d81-228">내부 및 외부 DNS 레코드와 라우팅을 계획 하 고 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-228">Plan and implement internal and external DNS records and routing.</span></span>
    
- <span data-ttu-id="84d81-229">Office 365 IP 주소 및 URL 요구 사항에 맞게 프록시나 방화벽을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-229">Configure your proxy or firewall for Office 365 IP address and URL requirements.</span></span>
    
- <span data-ttu-id="84d81-230">사용자 계정 및 Lync Online 설정을 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-230">Administer user accounts and Lync Online settings.</span></span>
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="84d81-231">Lync Online/Server Hybrid (분할 도메인)</span><span class="sxs-lookup"><span data-stu-id="84d81-231">Lync Online/Server Hybrid (split domain)</span></span>

<span data-ttu-id="84d81-232">Office 365 및 온-프레미스 환경 둘 다에 대 한 작업 외에도 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-232">In addition to tasks for both the Office 365 and on-premises environments:</span></span>
  
- <span data-ttu-id="84d81-233">필요한 경우 프록시 서버 장치를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-233">Configure the proxy server device, if required.</span></span>
    
- <span data-ttu-id="84d81-234">기능을 온-프레미스 및 온라인 버전의 Exchange Server 및 SharePoint와 통합을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-234">Configure the integration of features with on-premises and online versions of Exchange Server and SharePoint.</span></span>
    
#### <a name="lync-server"></a><span data-ttu-id="84d81-235">Lync Server</span><span class="sxs-lookup"><span data-stu-id="84d81-235">Lync Server</span></span>

<span data-ttu-id="84d81-236">온-프레미스 환경에서 Lync Server를 배포 하 고 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-236">Deploy and manage Lync Server in an on-premises environment:</span></span>
  
- <span data-ttu-id="84d81-237">서버를 구축 합니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-237">Provision the servers.</span></span>
    
- <span data-ttu-id="84d81-238">Lync 토폴로지를 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-238">Deploy the Lync topology.</span></span>
    
- <span data-ttu-id="84d81-239">Lync server를 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-239">Update Lync servers.</span></span>
    
- <span data-ttu-id="84d81-240">사용률에 따라 필요에 따라 토폴로지 서버를 추가 하거나 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-240">Add or remove topology servers as needed based on utilization.</span></span>
    
- <span data-ttu-id="84d81-241">장애 조치 (failover) 및 재해 복구 환경을 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-241">Implement the failover and disaster recovery environment.</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="84d81-242">공급자 호스트 Lync Server</span><span class="sxs-lookup"><span data-stu-id="84d81-242">Provider-Hosted Lync Server</span></span>

<span data-ttu-id="84d81-243">공급자와 협력 하 여 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-243">Work with the provider to:</span></span>
  
- <span data-ttu-id="84d81-244">Lync Server를 네트워크에 통합 합니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-244">Integrate Lync Server into your network.</span></span>
    
- <span data-ttu-id="84d81-245">Lync Server를 다른 Microsoft 제품 또는 사용자 지정 솔루션과 통합 합니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-245">Integrate Lync Server with other Microsoft products or custom solutions.</span></span>
    
- <span data-ttu-id="84d81-246">SLA (서비스 수준 계약) 준수를 모니터링 합니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-246">Monitor adherence with provider service level agreement (SLA).</span></span>
    
## <a name="two-example-scenarios-for-deploying-lync-2013"></a><span data-ttu-id="84d81-247">Lync 2013 배포를 위한 두 가지 예제 시나리오</span><span class="sxs-lookup"><span data-stu-id="84d81-247">Two example scenarios for deploying Lync 2013</span></span>

### <a name="directory-synchronization-components-in-microsoft-azure"></a><span data-ttu-id="84d81-248">Microsoft Azure의 디렉터리 동기화 구성 요소</span><span class="sxs-lookup"><span data-stu-id="84d81-248">Directory Synchronization components in Microsoft Azure</span></span>

<span data-ttu-id="84d81-249">요청 시 가상 컴퓨터를 배포 하는 기능으로 인해 Azure에서 Office 365 디렉터리 동기화 구성 요소를 배포 하는 것이 더 빠릅니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-249">Deploying Office 365 directory synchronization components in Azure is faster due to the ability to deploy virtual machines on-demand.</span></span>
  
<span data-ttu-id="84d81-250">함께 제공 되는 다이어그램에는 온-프레미스 Active Directory 환경과 Azure Active Directory 테 넌 트 간의 계정 이름과 암호를 동기화 하는 Azure Active Directory 테 넌 트를 사용한 Lync Online이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-250">The accompanying diagram shows Lync Online with an Azure Active Directory tenant, which synchronizes account names and passwords between the on-premises Active Directory environment and the Azure Active Directory tenant.</span></span>
  
 <span data-ttu-id="84d81-251">**디렉터리 동기화 서버에만**해당 합니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-251">**Directory synchronization server only**.</span></span> <span data-ttu-id="84d81-252">온-프레미스 환경에 64 비트 디렉터리 동기화 서버를 배포 하는 대신, 인터넷을 통해 Azure에서 가상 컴퓨터를 프로 비전 합니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-252">Instead of deploying the 64-bit directory synchronization server in your on-premises environment, you provision a virtual machine in Azure over the Internet.</span></span>
  
 <span data-ttu-id="84d81-253">**디렉터리 동기화 + AD FS**</span><span class="sxs-lookup"><span data-stu-id="84d81-253">**Directory synchronization + AD FS**.</span></span> <span data-ttu-id="84d81-254">이 옵션을 사용 하면 온-프레미스 인프라에 하드웨어를 추가 하지 않고 Office 365 페더레이션 id (SSO)를 지원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-254">This option allows you to support Office 365 federated identities (SSO) without adding hardware to your on-premises infrastructure.</span></span> <span data-ttu-id="84d81-255">또한 온-프레미스 Active Directory 환경을 사용할 수 없는 경우에도 복구 력을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-255">It also provides resiliency if the on-premises Active Directory environment is unavailable.</span></span> <span data-ttu-id="84d81-256">이 옵션의 기능은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-256">The features of this option include:</span></span>
  
- <span data-ttu-id="84d81-257">디렉터리 통합 구성 요소는 Azure 가상 컴퓨터로 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-257">Directory integration components run as Azure virtual machines.</span></span>
    
- <span data-ttu-id="84d81-258">Azure 가상 컴퓨터로 실행 되는 AD fs 프록시를 통해 AD FS가 인터넷에 게시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-258">AD FS is published to the Internet through AD FS proxies running as Azure virtual machines.</span></span>
    
- <span data-ttu-id="84d81-259">모든 위치에서 연결 하는 사용자에 대 한 클라이언트 인증 트래픽은 Azure 가상 컴퓨터로 배포 되는 AD FS 서버 및 프록시에서 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-259">Client authentication traffic, for users that are connecting from any location, is handled by AD FS servers and proxies that are deployed as Azure virtual machines.</span></span>
    
### <a name="lync-integration-with-exchange-and-sharepoint-in-office-365"></a><span data-ttu-id="84d81-260">Office 365의 Exchange 및 SharePoint와의 Lync 통합</span><span class="sxs-lookup"><span data-stu-id="84d81-260">Lync integration with Exchange and SharePoint in Office 365</span></span>

#### <a name="lync-server-with-exchange-online-and-sharepoint-online"></a><span data-ttu-id="84d81-261">Exchange Online 및 SharePoint Online을 사용 하는 Lync Server</span><span class="sxs-lookup"><span data-stu-id="84d81-261">Lync Server with Exchange Online and SharePoint Online</span></span>

<span data-ttu-id="84d81-262">함께 제공 되는 다이어그램에는 온-프레미스 Lync Server 2013 팜에 연결 된 Exchange Online 및 SharePoint Online의 Office 365이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-262">The accompanying diagram shows Office 365 with Exchange Online and SharePoint Online connected to an on-premises Lync Server 2013 farm.</span></span>
  
<span data-ttu-id="84d81-263">이 배포를 사용 하면 다음과 같은 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-263">The advantages of this deployment allow you to:</span></span>
  
- <span data-ttu-id="84d81-264">Lync Server 2013의 전체 기능 집합을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-264">Use the full feature set of Lync Server 2013.</span></span>
    
- <span data-ttu-id="84d81-265">Pbx와 같은 기존 온-프레미스 전화 장비를 활용 합니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-265">Leverage your existing on-premises phone equipment, such as PBXs.</span></span>
    
- <span data-ttu-id="84d81-266">전자 메일에 대 한 Exchange Online을 사용 하 여 온-프레미스 전자 메일 서버 및 저장소에 대 한 부담을 오프에서 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-266">Use Exchange Online for email, off-loading the burden of on-premises email servers and storage.</span></span>
    
- <span data-ttu-id="84d81-267">공동 작업을 위해 SharePoint Online을 사용 하 여 온-프레미스 SharePoint 서버를 유지 관리 하는 부담을 해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-267">Use SharePoint Online for collaboration, off-loading the burden of maintaining on-premises SharePoint servers.</span></span>
    
- <span data-ttu-id="84d81-268">Office 365의 UM (통합 메시징)을 포함 하 여 Lync, Exchange 및 SharePoint 통합 기능을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-268">Use Lync, Exchange, and SharePoint integrated features, including Unified Messaging (UM) in Office 365.</span></span>
    
#### <a name="exchange-server-with-lync-online"></a><span data-ttu-id="84d81-269">Lync Online을 사용 하는 Exchange Server</span><span class="sxs-lookup"><span data-stu-id="84d81-269">Exchange Server with Lync Online</span></span>

<span data-ttu-id="84d81-270">함께 제공 되는 다이어그램에서는 온-프레미스 Exchange Server 팜에 Lync Online이 연결 된 Office 365를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-270">The accompanying diagram shows Office 365 with Lync Online connected to an on-premises Exchange Server farm.</span></span>
  
<span data-ttu-id="84d81-271">이 배포를 사용 하면 다음과 같은 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-271">The advantages of this deployment allow you to:</span></span>
  
- <span data-ttu-id="84d81-272">기존 Exchange 인프라를 활용 합니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-272">Leverage your existing Exchange infrastructure.</span></span>
    
- <span data-ttu-id="84d81-273">현재 상태, 인스턴트 메시징 및 회의 기능을 위해 Lync Online을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="84d81-273">Use Lync Online for presence, instant messaging, and conferencing capabilities.</span></span>
    

