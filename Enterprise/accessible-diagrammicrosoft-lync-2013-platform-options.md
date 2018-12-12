---
title: 액세스할 수 있는 다이어그램-Microsoft Lync 2013 플랫폼 옵션
ms.author: josephd
author: JoeDavies-MSFT
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 2858d1e7-be37-4484-b121-a99779742a38
description: 이 문서에는 기술 다이어그램에서 사용할 수 있는 Microsoft Lync 2013 플랫폼 옵션 라는 다이어그램의 액세스할 수 있는 텍스트 버전입니다.
ms.openlocfilehash: 4a660df4bfacad2a00f5d9fbb5e1b668840e3b9f
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/09/2018
ms.locfileid: "17504091"
---
# <a name="accessible-diagram---microsoft-lync-2013-platform-options"></a><span data-ttu-id="545d6-103">액세스할 수 있는 다이어그램-Microsoft Lync 2013 플랫폼 옵션</span><span class="sxs-lookup"><span data-stu-id="545d6-103">Accessible diagram - Microsoft Lync 2013 Platform Options</span></span>

<span data-ttu-id="545d6-104">**요약:** 이 문서에는 [기술 다이어그램](http://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409)에서 사용할 수 있는 Microsoft Lync 2013 플랫폼 옵션 라는 다이어그램의 액세스할 수 있는 텍스트 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-104">**Summary:** This article is an accessible text version of the diagram named Microsoft Lync 2013 Platform Options, which is available at [Technical Diagrams](http://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409).</span></span>
  
<span data-ttu-id="545d6-105">이 포스터 비즈니스 의사 결정권자 (Bdm) 하 고 구축한 알아야 내용 Lync Online (Office 365) 및 Lync Server 배포 하는 방법에 대 한 설명 하 고 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-105">This poster describes what business decision makers (BDMs) and architects need to know about Lync Online (Office 365) and Lync Server deployments and includes:</span></span>
  
- <span data-ttu-id="545d6-106">4 개의 다양 한 배포 옵션 비교: Lync Online (Office 365), Lync Online/서버 하이브리드, Lync Server 및 Lync Server Provider-Hosted 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-106">A comparison of four different deployment options: Lync Online (Office 365), Lync Online/Server Hybrid, Lync Server, and Provider-Hosted Lync Server.</span></span> 
    
- <span data-ttu-id="545d6-107">Lync 2013을 배포 하기 위한 두 예제 시나리오입니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-107">Two example scenarios for deploying Lync 2013.</span></span>
    
## <a name="comparison-of-four-different-deployments-for-the-lync-2013-platform"></a><span data-ttu-id="545d6-108">Lync 2013 플랫폼에 대 한 4 개의 서로 다른 배포의 비교</span><span class="sxs-lookup"><span data-stu-id="545d6-108">Comparison of four different deployments for the Lync 2013 platform</span></span>

<span data-ttu-id="545d6-109">비교는 다음 영역에서 각 배포 옵션에 대 한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-109">The comparison provides information about each deployment option in the following areas:</span></span> 
  
- <span data-ttu-id="545d6-110">다양 한 배포 기능에 대 한 개요</span><span class="sxs-lookup"><span data-stu-id="545d6-110">An overview of the different deployment features</span></span>
    
- <span data-ttu-id="545d6-111">각 배포 옵션을 구현 하는의 이점</span><span class="sxs-lookup"><span data-stu-id="545d6-111">Benefits of implementing each deployment option</span></span>
    
- <span data-ttu-id="545d6-112">라이선스 요구 사항</span><span class="sxs-lookup"><span data-stu-id="545d6-112">Licensing requirements</span></span>
    
- <span data-ttu-id="545d6-113">필수 아키텍처 작업</span><span class="sxs-lookup"><span data-stu-id="545d6-113">Required architectural tasks</span></span>
    
- <span data-ttu-id="545d6-114">각 배포 옵션을 구현 하기 위한 IT Pro 책임</span><span class="sxs-lookup"><span data-stu-id="545d6-114">IT Pro responsibilities for implementing each deployment option</span></span>
    
### <a name="overview"></a><span data-ttu-id="545d6-115">개요</span><span class="sxs-lookup"><span data-stu-id="545d6-115">Overview</span></span>

#### <a name="lync-online-office-365"></a><span data-ttu-id="545d6-116">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="545d6-116">Lync Online (Office 365)</span></span>

<span data-ttu-id="545d6-117">효율성을 확보 하 고이 정보를 Office 365 다중 테 넌 트 계획 된 비용에 대 한 최적화 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-117">You gain efficiency and optimize for cost with Office 365 multitenant plans.</span></span>
  
<span data-ttu-id="545d6-118">함께 제공 되는 다이어그램에서는 계정 이름 및 온-프레미스 Active Directory 도메인 서비스 (AD DS) 환경과 Azure Active Directory 테 넌 트 간에 암호를 동기화 하는 Azure Active Directory 보유자를를 Lync Online 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-118">The accompanying diagram shows Lync Online with an Azure Active Directory tenant, which synchronizes account names and passwords between the on-premises Active Directory Domain Services (AD DS) environment and the Azure Active Directory tenant.</span></span> 
  
<span data-ttu-id="545d6-119">기능 및 기능을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-119">Description of features and functionality:</span></span>
  
- <span data-ttu-id="545d6-120">(SaaS) 서비스로 소프트웨어입니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-120">Software as a Service (SaaS).</span></span>
    
- <span data-ttu-id="545d6-121">서식 있는 집합은 항상 최신 상태로 유지 하는 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-121">Rich feature set that is always up to date.</span></span>
    
- <span data-ttu-id="545d6-122">다른 응용 프로그램과 함께 사용할 수 있는 온라인 계정에 대 한 Azure Active Directory 보유자를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-122">Includes an Azure Active Directory tenant for online accounts, which can be used with other applications.</span></span> 
    
- <span data-ttu-id="545d6-123">디렉터리 통합 계정 이름 및 암호 Azure Active Directory 테 넌 트 및 온-프레미스 Active Directory 도메인 서비스 (AD DS) 환경 간의 동기화를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-123">Directory integration includes synchronizing account names and passwords between the on-premises Active Directory Domain Services (AD DS) environment and the Azure Active Directory tenant.</span></span>
    
- <span data-ttu-id="545d6-124">Single sign-on 및 SSO ()는 요구 사항, Active Directory Federation Services (AD FS)를 구현 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-124">If single sign-on (SSO) is a requirement, Active Directory Federation Services (AD FS) must be implemented.</span></span> 
    
- <span data-ttu-id="545d6-125">인터넷을 통해 클라이언트 통신은 암호화 및 인증 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-125">Client communication over the Internet is encrypted and authenticated.</span></span>
    
- <span data-ttu-id="545d6-126">레거시 전화 장비 공용 전화망 (PSTN)을 연결 타사 공급자를 통해 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-126">Legacy phone equipment, public switched telephone network (PSTN), connectivity is available through third-party providers.</span></span>
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="545d6-127">Lync Online/서버 하이브리드 (분할 도메인)</span><span class="sxs-lookup"><span data-stu-id="545d6-127">Lync Online/Server Hybrid (split domain)</span></span>

<span data-ttu-id="545d6-128">Lync 2013의 온-프레미스 배포와 Office 365의 혜택을 결합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-128">You can combine the benefits of Office 365 with an on-premises deployment of Lync 2013.</span></span>
  
<span data-ttu-id="545d6-p101">함께 제공 되는 다이어그램 여기에서 일부 사용자는 홈된 온-프레미스 하 고 일부 사용자가 온라인에 있는 온라인를 Lync를 사용 하 여 Office 365를 보여줍니다. 온-프레미스로 배포 된에 지 서버도 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-p101">The accompanying diagram shows Office 365 with Lync Online where some users are homed on-premises and some users are homed online. An Edge Server that is deployed on-premises is also shown.</span></span>
  
<span data-ttu-id="545d6-131">기능 및 기능을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-131">Description of features and functionality:</span></span>
  
- <span data-ttu-id="545d6-132">일부 사용자가 내부에 있는 및 일부 사용자가 온라인으로 있는 하지만 사용자는 동일한 SIP 도메인 (예: contoso.com)을 공유 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-132">Some users are homed on premises and some users are homed online, but the users share the same SIP domain (such as contoso.com).</span></span>
    
- <span data-ttu-id="545d6-133">PSTN에 대 한 연결을 포함 하 여 기존 Lync Server 2013 인프라를 활용 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-133">Leverage your existing Lync Server 2013 infrastructure, including the connections to the PSTN.</span></span>
    
- <span data-ttu-id="545d6-134">PSTN을 필요 하지 않은 경우에 새 Lync Online 사용자를 쉽게 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-134">Add new Lync Online users easily when they do not require PSTN.</span></span>
    
- <span data-ttu-id="545d6-135">Lync 온-프레미스에서 Lync Online에 일정에 시간별로 마이그레이션하십시오.</span><span class="sxs-lookup"><span data-stu-id="545d6-135">Migrate from Lync on-premises to Lync Online over time, on your schedule.</span></span>
    
- <span data-ttu-id="545d6-136">Exchange Online 및 SharePoint Online을 포함 하 여 다른 Office 365 응용 프로그램과 통합 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-136">Integrate with other Office 365 applications, including Exchange Online and SharePoint Online.</span></span>
    
#### <a name="lync-server"></a><span data-ttu-id="545d6-137">Lync Server</span><span class="sxs-lookup"><span data-stu-id="545d6-137">Lync Server</span></span>

<span data-ttu-id="545d6-p102">이 배포에서 소유 하 고 모든 작업입니다. 함께 제공 된 다이어그램은 사용자의 홈된 온-프레미스가 온-프레미스 Active Directory 도메인 서비스 (AD DS) 환경 사용 하는 Lync 서버 인프라를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-p102">In this deployment, you own everything. The accompanying diagram shows a Lync Server infrastructure with an on-premises Active Directory Domain Services (AD DS) environment where users are homed on-premises.</span></span>
  
<span data-ttu-id="545d6-140">기능 및 기능을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-140">Description of features and functionality:</span></span>
  
- <span data-ttu-id="545d6-141">용량 계획 및 크기 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-141">Capacity planning and sizing.</span></span>
    
- <span data-ttu-id="545d6-142">서버 취득 하 고 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-142">Server acquisition and setup.</span></span>
    
- <span data-ttu-id="545d6-143">배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-143">Deployment.</span></span>
    
- <span data-ttu-id="545d6-144">수평 확장, 패치 및 작업 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-144">Scaling out, patching, and operations.</span></span>
    
- <span data-ttu-id="545d6-145">데이터를 백업 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-145">Backing up data.</span></span>
    
- <span data-ttu-id="545d6-146">장애 조치 및 재해 복구를 유지 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-146">Maintaining failover and disaster recovery.</span></span>
    
- <span data-ttu-id="545d6-147">Lync Server 2013 인프라가 PSTN에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-147">Connecting your Lync Server 2013 infrastructure to the PSTN.</span></span>
    
- <span data-ttu-id="545d6-148">Private branch exchange (Pbx)와 같은 기존 전화 장비와의 통합 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-148">Integration with existing phone equipment, such as private branch exchanges (PBXs).</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="545d6-149">Lync 서버 공급자 호스팅</span><span class="sxs-lookup"><span data-stu-id="545d6-149">Provider-Hosted Lync Server</span></span>

<span data-ttu-id="545d6-p103">공급자에이 배포에 모든 작업을 담당합니다. 함께 제공 되는 다이어그램의 서버 및 온-프레미스 환경에 대 한 연결 된 장비를 비롯 하 여 공급자의 네트워크를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-p103">In this deployment, your provider owns everything. The accompanying diagram shows a provider's network including their servers and equipment with a connection to an on-premises environment.</span></span>
  
<span data-ttu-id="545d6-152">기능 및 기능을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-152">Description of features and functionality:</span></span>
  
- <span data-ttu-id="545d6-153">용량 계획 및 크기 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-153">Capacity planning and sizing.</span></span>
    
- <span data-ttu-id="545d6-154">서버 취득 하 고 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-154">Server acquisition and setup.</span></span>
    
- <span data-ttu-id="545d6-155">배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-155">Deployment.</span></span>
    
- <span data-ttu-id="545d6-156">수평 확장, 패치 및 작업 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-156">Scaling out, patching, and operations.</span></span>
    
- <span data-ttu-id="545d6-157">데이터를 백업 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-157">Backing up data.</span></span>
    
- <span data-ttu-id="545d6-158">장애 조치 및 재해 복구를 유지 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-158">Maintaining failover and disaster recovery.</span></span>
    
- <span data-ttu-id="545d6-159">Private branch exchange (Pbx)와 같은 기존 전화 장비와의 통합 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-159">Integration with existing phone equipment, such as private branch exchanges (PBXs).</span></span>
    
- <span data-ttu-id="545d6-160">또한 공급자는 다음과 같은 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-160">In addition, the provider can:</span></span>
    
  - <span data-ttu-id="545d6-161">귀하의 구내 (실선)에 대 한 연결을 사용 하 여 자신의 네트워크에서 해당 서버 및 장비를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-161">Install their servers and equipment in their own network with a connection to your premises (solid line).</span></span>
    
  - <span data-ttu-id="545d6-162">귀하의 구내 (점선)에서 해당 서버를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-162">Install their servers on your premises (dotted line).</span></span>
    
### <a name="benefits-of-implementing-each-deployment-option"></a><span data-ttu-id="545d6-163">각 배포 옵션을 구현 하는의 이점</span><span class="sxs-lookup"><span data-stu-id="545d6-163">Benefits of implementing each deployment option</span></span>

#### <a name="lync-online-office-365"></a><span data-ttu-id="545d6-164">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="545d6-164">Lync Online (Office 365)</span></span>

- <span data-ttu-id="545d6-165">온-프레미스 서버 또는 서버 소프트웨어의 없음 운영 부담이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-165">No operational burden of on-premises servers or server software.</span></span>
    
- <span data-ttu-id="545d6-166">클라우드 기반 서비스로 Lync Server 2013의 통신 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-166">Communication capabilities of Lync Server 2013 as a cloud-based service.</span></span>
    
- <span data-ttu-id="545d6-167">Lync 현재 상태, 인스턴트 메시징, 오디오 및 비디오 풍부한 온라인 모임 및 광범위 한 웹 회의 기능을 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-167">Lync presence, instant messaging, audio and video calling, rich online meetings, and extensive web conferencing capabilities.</span></span>
    
- <span data-ttu-id="545d6-168">지리적으로 분산 된 조직과 또는 주로 모바일 직원을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-168">Used with geographically-dispersed organizations or with primarily mobile employees.</span></span>
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="545d6-169">Lync Online/서버 하이브리드 (분할 도메인)</span><span class="sxs-lookup"><span data-stu-id="545d6-169">Lync Online/Server Hybrid (split domain)</span></span>

- <span data-ttu-id="545d6-170">원격 사용자와 비즈니스 파트너와의 통합에 대 한 Lync Online을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-170">Use Lync Online for remote users and integration with business partners.</span></span>
    
- <span data-ttu-id="545d6-171">Lync 온-프레미스에서 Lync Online로 마이그레이션을 용이 하 게 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-171">Facilitate a migration from Lync on-premises to Lync Online.</span></span>
    
- <span data-ttu-id="545d6-172">Branch office appliance를 사용 하지 않고 원격 사이트를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-172">Support remote sites without using a branch office appliance.</span></span>
    
- <span data-ttu-id="545d6-173">새 비즈니스 인수에 대 한 Lync 지원을 추가 (영문) 편리성 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-173">Ease of adding Lync support for new business acquisitions.</span></span>
    
#### <a name="lync-server"></a><span data-ttu-id="545d6-174">Lync Server</span><span class="sxs-lookup"><span data-stu-id="545d6-174">Lync Server</span></span>

- <span data-ttu-id="545d6-175">개인 클라우드 솔루션입니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-175">Private cloud solutions.</span></span>
    
- <span data-ttu-id="545d6-176">고도로 사용자 지정 된 솔루션입니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-176">Highly customized solutions.</span></span>
    
- <span data-ttu-id="545d6-177">타사 구성 요소 하드웨어 및 소프트웨어를 활용 하는 Lync Online에서 지원 하지 않는 사용 하 여 레거시 솔루션입니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-177">Legacy solutions with third-party components that depend on hardware and software that are not supported by Lync Online.</span></span>
    
- <span data-ttu-id="545d6-178">Office 365와 AD DS 계정 동기화를 차단 하는 정보 공개 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-178">Privacy restrictions that prevent synchronization of AD DS accounts with Office 365.</span></span>
    
- <span data-ttu-id="545d6-179">전체 플랫폼 및 솔루션의 제어 하려고 하는 조직입니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-179">Organizations that desire control of the entire platform and solution.</span></span>
    
- <span data-ttu-id="545d6-180">Lync Enterprise Voice와 PBX 대체 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-180">PBX replacement with Lync Enterprise Voice.</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="545d6-181">Lync 서버 공급자 호스팅</span><span class="sxs-lookup"><span data-stu-id="545d6-181">Provider-Hosted Lync Server</span></span>

- <span data-ttu-id="545d6-182">Lync Server 기능을 사용할 하지만 해당 배포 및 유지 관리를 아웃소싱 할 하려는 하는 조직입니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-182">Organizations that want Lync Server functionality but want to outsource its deployment and maintenance.</span></span>
    
- <span data-ttu-id="545d6-183">공급자 기반 솔루션입니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-183">Provider-based solutions.</span></span>
    
- <span data-ttu-id="545d6-184">고도로 사용자 지정 된 솔루션입니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-184">Highly customized solutions.</span></span>
    
- <span data-ttu-id="545d6-185">타사 구성 요소 하드웨어 및 소프트웨어를 활용 하는 Lync Online에서 지원 하지 않는 사용 하 여 레거시 솔루션입니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-185">Legacy solutions with third-party components that depend on hardware and software that are not supported by Lync Online.</span></span>
    
- <span data-ttu-id="545d6-186">Lync Enterprise Voice와 PBX 대체 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-186">PBX replacement with Lync Enterprise Voice.</span></span>
    
### <a name="license-requirements"></a><span data-ttu-id="545d6-187">라이선스 요구 사항</span><span class="sxs-lookup"><span data-stu-id="545d6-187">License requirements</span></span>

#### <a name="lync-online-office-365"></a><span data-ttu-id="545d6-188">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="545d6-188">Lync Online (Office 365)</span></span>

<span data-ttu-id="545d6-189">구독 모델입니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-189">Subscription model.</span></span>
  
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="545d6-190">Lync Online/서버 하이브리드 (분할 도메인)</span><span class="sxs-lookup"><span data-stu-id="545d6-190">Lync Online/Server Hybrid (split domain)</span></span>

- <span data-ttu-id="545d6-p104">Office 365-구독 모델입니다. 추가 라이센스 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-p104">Office 365 — Subscription model. No additional licenses needed.</span></span> 
    
- <span data-ttu-id="545d6-193">온-프레미스-모든 온-프레미스 라이선스 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-193">On-premises — All on-premises licenses apply.</span></span> 
    
#### <a name="lync-server"></a><span data-ttu-id="545d6-194">Lync Server</span><span class="sxs-lookup"><span data-stu-id="545d6-194">Lync Server</span></span>

- <span data-ttu-id="545d6-195">서버 운영 체제</span><span class="sxs-lookup"><span data-stu-id="545d6-195">Server Operating System</span></span>
    
- <span data-ttu-id="545d6-196">SQL Server</span><span class="sxs-lookup"><span data-stu-id="545d6-196">SQL Server</span></span>
    
- <span data-ttu-id="545d6-197">Lync 2013 서버 라이선스</span><span class="sxs-lookup"><span data-stu-id="545d6-197">Lync 2013 Server License</span></span>
    
- <span data-ttu-id="545d6-198">Lync 2013 클라이언트 액세스 라이선스</span><span class="sxs-lookup"><span data-stu-id="545d6-198">Lync 2013 Client Access License</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="545d6-199">Lync 서버 공급자 호스팅</span><span class="sxs-lookup"><span data-stu-id="545d6-199">Provider-Hosted Lync Server</span></span>

<span data-ttu-id="545d6-200">비용에 Lync 솔루션 공급자와 계약을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-200">Costs are based on the agreement with your Lync solution provider.</span></span>
  
### <a name="architecture-tasks"></a><span data-ttu-id="545d6-201">아키텍처 작업</span><span class="sxs-lookup"><span data-stu-id="545d6-201">Architecture tasks</span></span>

<span data-ttu-id="545d6-202">이 섹션에서는 각 배포 옵션에 대 한 아키텍처 작업을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-202">This section lists the architectural tasks for each deployment option.</span></span>
  
#### <a name="lync-online-office-365"></a><span data-ttu-id="545d6-203">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="545d6-203">Lync Online (Office 365)</span></span>

- <span data-ttu-id="545d6-204">디렉터리 동기화를 계획 하 고 디자인 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-204">Plan and design directory synchronization.</span></span>
    
- <span data-ttu-id="545d6-205">네트워크 용량 및 방화벽, 프록시 서버, 게이트웨이 통해 및 WAN 링크에서 사용 가능 여부를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-205">Ensure network capacity and availability through firewalls, proxy servers, gateways, and across WAN links.</span></span>
    
- <span data-ttu-id="545d6-206">Office 365 서비스 제품에 대 한 엔터프라이즈 보안을 제공 하려면 타사 SSL 인증서를 구입 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-206">Acquire third-party SSL certificates to provide enterprise-security for Office 365 service offerings.</span></span>
    
- <span data-ttu-id="545d6-207">인터넷 프로토콜 버전 6 (IPv6)와 함께 Office 365에 연결 하는 경우를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-207">Decide if you want to connect to Office 365 with Internet Protocol version 6 (IPv6).</span></span>
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="545d6-208">Lync Online/서버 하이브리드 (분할 도메인)</span><span class="sxs-lookup"><span data-stu-id="545d6-208">Lync Online/Server Hybrid (split domain)</span></span>

<span data-ttu-id="545d6-209">Office 365와 온-프레미스 환경에 대 한 작업 외에도:</span><span class="sxs-lookup"><span data-stu-id="545d6-209">In addition to tasks for both the Office 365 and on-premises environments:</span></span>
  
- <span data-ttu-id="545d6-210">사용 하려는 얼마나 많은 기능 통합 온-프레미스 및 온라인 버전의 Exchange Server 및 SharePoint를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-210">Determine how much feature integration you want to use with on-premises and online versions of Exchange Server and SharePoint.</span></span>
    
- <span data-ttu-id="545d6-211">필요한 경우에 프록시 서버 장치를 사용 하 여 Office 365의 요청에 대 한가 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-211">If required, determine which proxy server device will be used for requests from Office 365.</span></span>
    
#### <a name="lync-server"></a><span data-ttu-id="545d6-212">Lync Server</span><span class="sxs-lookup"><span data-stu-id="545d6-212">Lync Server</span></span>

<span data-ttu-id="545d6-213">기존 온-프레미스 환경에서 Lync 환경 디자인 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-213">Design the Lync environment in an existing on-premises environment:</span></span>
  
- <span data-ttu-id="545d6-214">중앙에 대 한 Lync 토폴로지 및 지점입니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-214">Lync topology for central and branch offices.</span></span>
    
- <span data-ttu-id="545d6-215">가상화를 포함 하 여 서버 하드웨어를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-215">Server hardware, including virtualization.</span></span>
    
- <span data-ttu-id="545d6-216">Active Directory 도메인 서비스 (AD DS)와 통합 및 DNS 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-216">Integration with Active Directory Domain Services (AD DS) and DNS.</span></span>
    
- <span data-ttu-id="545d6-217">Lync server 풀에 대 한 분산을 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-217">Load balancing for Lync server pools.</span></span>
    
- <span data-ttu-id="545d6-218">장애 조치 및 재해 복구 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-218">Failover and disaster recovery.</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="545d6-219">Lync 서버 공급자 호스팅</span><span class="sxs-lookup"><span data-stu-id="545d6-219">Provider-Hosted Lync Server</span></span>

- <span data-ttu-id="545d6-220">클라우드 기반 설치를 위해 서비스 공급자의 네트워크에 대 한 연결을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-220">For a cloud-based installation, determine the connection to the service provider's network.</span></span>
    
- <span data-ttu-id="545d6-221">온-프레미스 설치에 대 한 네트워크에 있는 공급자의 Lync 서버 배치를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-221">For an on-premises installation, determine the placement of the provider's Lync servers on your network.</span></span>
    
- <span data-ttu-id="545d6-222">두 형식에 대 한 AD DS와 PBX 장비와 통합을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-222">For both types, determine the integration with AD DS and your PBX equipment.</span></span>
    
### <a name="it-pro-responsibilities"></a><span data-ttu-id="545d6-223">IT 전문가 책임</span><span class="sxs-lookup"><span data-stu-id="545d6-223">IT Pro responsibilities</span></span>

<span data-ttu-id="545d6-224">이 섹션에서는 각 배포 옵션에 대 한 IT 전문가 용 책임을 부여 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-224">This section lists the IT Pro responsibilities for each deployment option.</span></span>
  
#### <a name="lync-online-office-365"></a><span data-ttu-id="545d6-225">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="545d6-225">Lync Online (Office 365)</span></span>

<span data-ttu-id="545d6-226">배포 하 고 Lync Online (Office 365)을 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-226">Deploy and manage Lync Online (Office 365):</span></span>
  
- <span data-ttu-id="545d6-227">디렉터리 동기화 계획을 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-227">Implement the directory synchronization plan.</span></span>
    
- <span data-ttu-id="545d6-228">계획 하 고 내부 및 외부 DNS 레코드 및 라우팅을 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-228">Plan and implement internal and external DNS records and routing.</span></span>
    
- <span data-ttu-id="545d6-229">프록시 또는 Office 365 IP 주소 및 URL 요구 사항에 대 한 방화벽을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-229">Configure your proxy or firewall for Office 365 IP address and URL requirements.</span></span>
    
- <span data-ttu-id="545d6-230">사용자 계정 및 Lync Online 설정을 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-230">Administer user accounts and Lync Online settings.</span></span>
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="545d6-231">Lync Online/서버 하이브리드 (분할 도메인)</span><span class="sxs-lookup"><span data-stu-id="545d6-231">Lync Online/Server Hybrid (split domain)</span></span>

<span data-ttu-id="545d6-232">Office 365와 온-프레미스 환경에 대 한 작업 외에도:</span><span class="sxs-lookup"><span data-stu-id="545d6-232">In addition to tasks for both the Office 365 and on-premises environments:</span></span>
  
- <span data-ttu-id="545d6-233">필요한 경우 프록시 서버 장치를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-233">Configure the proxy server device, if required.</span></span>
    
- <span data-ttu-id="545d6-234">온-프레미스 및 온라인 버전의 Exchange Server 및 SharePoint의 기능 통합을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-234">Configure the integration of features with on-premises and online versions of Exchange Server and SharePoint.</span></span>
    
#### <a name="lync-server"></a><span data-ttu-id="545d6-235">Lync Server</span><span class="sxs-lookup"><span data-stu-id="545d6-235">Lync Server</span></span>

<span data-ttu-id="545d6-236">배포 하 고 온-프레미스 환경에서 Lync Server를 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-236">Deploy and manage Lync Server in an on-premises environment:</span></span>
  
- <span data-ttu-id="545d6-237">서버를 구축 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-237">Provision the servers.</span></span>
    
- <span data-ttu-id="545d6-238">Lync 토폴로지를 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-238">Deploy the Lync topology.</span></span>
    
- <span data-ttu-id="545d6-239">Lync 서버를 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-239">Update Lync servers.</span></span>
    
- <span data-ttu-id="545d6-240">서버 추가 또는 제거 토폴로지 필요에 따라 사용률에 기반 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-240">Add or remove topology servers as needed based on utilization.</span></span>
    
- <span data-ttu-id="545d6-241">장애 조치 및 재해 복구 환경을 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-241">Implement the failover and disaster recovery environment.</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="545d6-242">Lync 서버 공급자 호스팅</span><span class="sxs-lookup"><span data-stu-id="545d6-242">Provider-Hosted Lync Server</span></span>

<span data-ttu-id="545d6-243">공급자와 함께 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-243">Work with the provider to:</span></span>
  
- <span data-ttu-id="545d6-244">네트워크에 Lync Server를 통합 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-244">Integrate Lync Server into your network.</span></span>
    
- <span data-ttu-id="545d6-245">다른 Microsoft 제품 또는 사용자 지정 솔루션 Lync Server를 통합 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-245">Integrate Lync Server with other Microsoft products or custom solutions.</span></span>
    
- <span data-ttu-id="545d6-246">공급자 서비스 수준 계약 (SLA)와 준수 하는지를 모니터링 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-246">Monitor adherence with provider service level agreement (SLA).</span></span>
    
## <a name="two-example-scenarios-for-deploying-lync-2013"></a><span data-ttu-id="545d6-247">Lync 2013을 배포 하기 위한 두 예제 시나리오</span><span class="sxs-lookup"><span data-stu-id="545d6-247">Two example scenarios for deploying Lync 2013</span></span>

### <a name="directory-synchronization-components-in-microsoft-azure"></a><span data-ttu-id="545d6-248">Microsoft Azure의 디렉터리 동기화 구성 요소</span><span class="sxs-lookup"><span data-stu-id="545d6-248">Directory Synchronization components in Microsoft Azure</span></span>

<span data-ttu-id="545d6-249">Azure의 Office 365 디렉터리 동기화 구성 요소를 배포 보다 빠르게 주문형 가상 컴퓨터를 배포 하는 기능으로 인해 있습니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-249">Deploying Office 365 directory synchronization components in Azure is faster due to the ability to deploy virtual machines on-demand.</span></span>
  
<span data-ttu-id="545d6-250">함께 제공 되는 다이어그램에서는 계정 이름 및 암호는 온-프레미스 Active Directory 환경 및 Azure Active Directory 테 넌 트 간에 동기화 Azure Active Directory 보유자를를 Lync Online 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-250">The accompanying diagram shows Lync Online with an Azure Active Directory tenant, which synchronizes account names and passwords between the on-premises Active Directory environment and the Azure Active Directory tenant.</span></span>
  
 <span data-ttu-id="545d6-p105">**디렉터리 동기화 서버에 해당**합니다. 온-프레미스 환경에서 64 비트 디렉터리 동기화 서버를 배포 하는 대신 인터넷을 통해 Azure에 가상 컴퓨터를 구축 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-p105">**Directory synchronization server only**. Instead of deploying the 64-bit directory synchronization server in your on-premises environment, you provision a virtual machine in Azure over the Internet.</span></span>
  
 <span data-ttu-id="545d6-p106">**디렉터리 동기화 + AD FS**합니다. 이 옵션을 사용 하면 온-프레미스 인프라에 하드웨어를 추가 하지 않고 Office 365 페더레이션 id가 SSO ()를 지원할 수 있습니다. 또한 온-프레미스 Active Directory 환경에 사용할 수 없는 경우 복구를 제공 합니다. 이 옵션의 기능은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-p106">**Directory synchronization + AD FS**. This option allows you to support Office 365 federated identities (SSO) without adding hardware to your on-premises infrastructure. It also provides resiliency if the on-premises Active Directory environment is unavailable. The features of this option include:</span></span>
  
- <span data-ttu-id="545d6-257">디렉터리 통합 구성 요소를 Azure 가상 컴퓨터를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-257">Directory integration components run as Azure virtual machines.</span></span>
    
- <span data-ttu-id="545d6-258">AD FS Azure 가상 컴퓨터와를 실행 하는 AD FS 프록시를 통해 인터넷에 게시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-258">AD FS is published to the Internet through AD FS proxies running as Azure virtual machines.</span></span>
    
- <span data-ttu-id="545d6-259">모든 위치에서 연결 하는 사용자에 대 한 클라이언트 인증 트래픽 AD FS 서버 및 Azure 가상 컴퓨터도 배포 되는 프록시에 의해 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-259">Client authentication traffic, for users that are connecting from any location, is handled by AD FS servers and proxies that are deployed as Azure virtual machines.</span></span>
    
### <a name="lync-integration-with-exchange-and-sharepoint-in-office-365"></a><span data-ttu-id="545d6-260">Exchange 및 Office 365의 SharePoint와 Lync 통합</span><span class="sxs-lookup"><span data-stu-id="545d6-260">Lync integration with Exchange and SharePoint in Office 365</span></span>

#### <a name="lync-server-with-exchange-online-and-sharepoint-online"></a><span data-ttu-id="545d6-261">Exchange Online과 Lync Server 및 SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="545d6-261">Lync Server with Exchange Online and SharePoint Online</span></span>

<span data-ttu-id="545d6-262">함께 제공 되는 다이어그램 Exchange Online 및 SharePoint Online을 사용 하 여 Office 365를 온-프레미스 Lync Server 2013 팜에 연결을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-262">The accompanying diagram shows Office 365 with Exchange Online and SharePoint Online connected to an on-premises Lync Server 2013 farm.</span></span>
  
<span data-ttu-id="545d6-263">이 배포의 장점 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-263">The advantages of this deployment allow you to:</span></span>
  
- <span data-ttu-id="545d6-264">Lync Server 2013의 전체 기능 집합을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-264">Use the full feature set of Lync Server 2013.</span></span>
    
- <span data-ttu-id="545d6-265">Pbx와 같은 기존 온-프레미스 전화 장비를 활용 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-265">Leverage your existing on-premises phone equipment, such as PBXs.</span></span>
    
- <span data-ttu-id="545d6-266">온-프레미스 전자 메일 서버 및 저장소의 부담을 오프 로드 하는 전자 메일에 대 한 Exchange Online을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-266">Use Exchange Online for email, off-loading the burden of on-premises email servers and storage.</span></span>
    
- <span data-ttu-id="545d6-267">온-프레미스 SharePoint 서버를 유지 관리 부담을 오프 로드 하는 공동 작업을 위한 SharePoint Online을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-267">Use SharePoint Online for collaboration, off-loading the burden of maintaining on-premises SharePoint servers.</span></span>
    
- <span data-ttu-id="545d6-268">사용 하 여 Lync, Exchange 및 SharePoint 기능을 비롯 하 여 UM (통합 메시징) Office 365의 통합.</span><span class="sxs-lookup"><span data-stu-id="545d6-268">Use Lync, Exchange, and SharePoint integrated features, including Unified Messaging (UM) in Office 365.</span></span>
    
#### <a name="exchange-server-with-lync-online"></a><span data-ttu-id="545d6-269">Lync Online 포함 Exchange 서버</span><span class="sxs-lookup"><span data-stu-id="545d6-269">Exchange Server with Lync Online</span></span>

<span data-ttu-id="545d6-270">함께 제공 된 다이어그램 온-프레미스 Exchange 서버 팜에 연결 된 Lync Online을 사용 하 여 Office 365를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-270">The accompanying diagram shows Office 365 with Lync Online connected to an on-premises Exchange Server farm.</span></span>
  
<span data-ttu-id="545d6-271">이 배포의 장점 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-271">The advantages of this deployment allow you to:</span></span>
  
- <span data-ttu-id="545d6-272">기존 Exchange 인프라를 활용 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-272">Leverage your existing Exchange infrastructure.</span></span>
    
- <span data-ttu-id="545d6-273">현재 상태, 인스턴트 메시징 및 회의 기능에 대 한 Lync Online을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="545d6-273">Use Lync Online for presence, instant messaging, and conferencing capabilities.</span></span>
    

