---
title: Microsoft SaaS(Office 365)용 하이브리드 클라우드 시나리오
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: db117e59-389f-46f5-a5df-4eeac0040aa8
description: '요약: Microsoft의 SaaS 기반 클라우드 서비스에 대 한 하이브리드 아키텍처 및 시나리오를 이해 합니다 (Office 365).'
ms.openlocfilehash: 90b751e4bbea42d723961eb2ac339d23faf8c259
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487524"
---
# <a name="hybrid-cloud-scenarios-for-microsoft-saas-office-365"></a><span data-ttu-id="51d15-103">Microsoft SaaS(Office 365)용 하이브리드 클라우드 시나리오</span><span class="sxs-lookup"><span data-stu-id="51d15-103">Hybrid cloud scenarios for Microsoft SaaS (Office 365)</span></span>

 <span data-ttu-id="51d15-104">**요약:** Microsoft의 SaaS 기반 클라우드 서비스 (Office 365)에 대 한 하이브리드 아키텍처 및 시나리오를 이해 합니다.</span><span class="sxs-lookup"><span data-stu-id="51d15-104">**Summary:** Understand the hybrid architecture and scenarios for Microsoft's SaaS-based cloud offerings (Office 365).</span></span>
  
<span data-ttu-id="51d15-105">클라우드 마이그레이션 또는 장기적인 통합 전략의 일환으로, Exchange, SharePoint 또는 비즈니스용 Skype를 Office 365의 해당 항목을 사용 하 여 온-프레미스 배포를 결합 합니다.</span><span class="sxs-lookup"><span data-stu-id="51d15-105">Combine on-premises deployments of Exchange, SharePoint, or Skype for Business with their counterparts in Office 365 as part of a cloud migration or long-term integration strategy.</span></span>
  
## <a name="microsoft-saas-hybrid-scenario-architecture"></a><span data-ttu-id="51d15-106">Microsoft SaaS 하이브리드 시나리오 아키텍처</span><span class="sxs-lookup"><span data-stu-id="51d15-106">Microsoft SaaS hybrid scenario architecture</span></span>

<span data-ttu-id="51d15-107">그림 1에서는 Office 365 용 Microsoft SaaS 기반 하이브리드 시나리오의 아키텍처를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="51d15-107">Figure 1 shows the architecture of Microsoft SaaS-based hybrid scenarios for Office 365.</span></span>
  
<span data-ttu-id="51d15-108">**그림 1: Office 365 용 Microsoft SaaS 기반 하이브리드 시나리오**</span><span class="sxs-lookup"><span data-stu-id="51d15-108">**Figure 1: Microsoft SaaS-based hybrid scenarios for Office 365**</span></span>

![Office 365 용 Microsoft SaaS 기반 하이브리드 시나리오](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS.png)
  
<span data-ttu-id="51d15-110">아키텍처의 각 계층에 대해 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="51d15-110">For each layer of the architecture:</span></span>
  
- <span data-ttu-id="51d15-111">앱 및 시나리오</span><span class="sxs-lookup"><span data-stu-id="51d15-111">Apps and scenarios</span></span>
    
    <span data-ttu-id="51d15-112">office Server 제품에 맞추고 office 365 대응 하는 다양 한 SaaS 기반 하이브리드 시나리오를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51d15-112">There are a variety of SaaS-based hybrid scenarios, aligning around Office Server products and their Office 365 counterparts:</span></span>
    
  - <span data-ttu-id="51d15-113">exchange Online과 통합 된 exchange server (exchange server hybrid)</span><span class="sxs-lookup"><span data-stu-id="51d15-113">Exchange Server combined with Exchange Online (Exchange Server hybrid)</span></span>
    
  - <span data-ttu-id="51d15-114">비즈니스용 skype 서버와 skype 온라인 및 새로운 클라우드 PBX 및 클라우드 커넥터 버전 시나리오를 결합</span><span class="sxs-lookup"><span data-stu-id="51d15-114">Skype for Business Server combined with Skype for Business Online and the new Cloud PBX and Cloud Connector Edition scenarios</span></span>
    
  - <span data-ttu-id="51d15-115">sharepoint server 2019, sharepoint server 2016 또는 sharepoint server 2013가 sharepoint Online과 결합 됨 (여러 시나리오)</span><span class="sxs-lookup"><span data-stu-id="51d15-115">SharePoint Server 2019, SharePoint Server 2016, or SharePoint Server 2013 combined with SharePoint Online (multiple scenarios)</span></span>
    
    <span data-ttu-id="51d15-116">제품 간 하이브리드 시나리오인 비즈니스용 Skype 서버 온-프레미스를 사용 하는 Exchange Online도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51d15-116">There is also Exchange Online with Skype for Business Server on-premises, a cross-product hybrid scenario.</span></span>
    
- <span data-ttu-id="51d15-117">ID</span><span class="sxs-lookup"><span data-stu-id="51d15-117">Identity</span></span>
    
    <span data-ttu-id="51d15-118">온-프레미스 AD DS (Active directory 도메인 서비스)와 디렉터리 동기화를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51d15-118">Can include directory synchronization with your on-premises Active Directory Domain Services (AD DS).</span></span> <span data-ttu-id="51d15-119">또는 타사 id 공급자와 페더레이션 하도록 Azure AD를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51d15-119">Alternately, you can configure Azure AD to federate with a third-party identity provider.</span></span>
    
- <span data-ttu-id="51d15-120">네트워크</span><span class="sxs-lookup"><span data-stu-id="51d15-120">Network</span></span>
    
    <span data-ttu-id="51d15-121">기존 인터넷 파이프 또는 Office 365 또는 Dynamics 365에 대 한 Microsoft 피어 링과의 express 방식 연결로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="51d15-121">Consists of either your existing Internet pipe or an ExpressRoute connection with Microsoft peering for Office 365 or Dynamics 365.</span></span>
    
- <span data-ttu-id="51d15-122">온-프레미스</span><span class="sxs-lookup"><span data-stu-id="51d15-122">On-premises</span></span>
    
    <span data-ttu-id="51d15-123">Exchange, SharePoint 및 비즈니스용 Skype에 대 한 기존 서버로 구성 하 여 최신 버전으로 업데이트 해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51d15-123">Can consist of existing servers for Exchange, SharePoint, and Skype for Business, which should be updated to their latest versions.</span></span> <span data-ttu-id="51d15-124">그런 다음 하이브리드 시나리오를 위해 이러한 항목을 Office 365과 결합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51d15-124">You can then combine them with their Office 365 counterparts for hybrid scenarios.</span></span>
    
<span data-ttu-id="51d15-125">자체 office 365 개발/테스트 환경을 설정 하려면 [office 365 테스트 랩 가이드](cloud-adoption-test-lab-guides-tlgs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="51d15-125">Set up your own Office 365 dev/test environment, see [Office 365 Test Lab Guides](cloud-adoption-test-lab-guides-tlgs.md).</span></span>
  
## <a name="skype-for-business-hybrid"></a><span data-ttu-id="51d15-126">비즈니스용 Skype 하이브리드</span><span class="sxs-lookup"><span data-stu-id="51d15-126">Skype for Business Hybrid</span></span>

<span data-ttu-id="51d15-127">비즈니스용 skype 하이브리드를 사용 하 여 기존 온-프레미스 배포를 비즈니스용 skype Online과 결합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51d15-127">Skype for Business Hybrid lets you combine an existing on-premises deployment with Skype for Business Online.</span></span> <span data-ttu-id="51d15-128">일부 사용자는 온-프레미스에 있고 일부 사용자는 온라인으로 설정 되지만, 사용자는 contoso.com과 같은 동일한 SIP (세션 시작 프로토콜) 도메인을 공유 합니다.</span><span class="sxs-lookup"><span data-stu-id="51d15-128">Some users are homed on-premises and some users are homed online, but the users share the same Session Initiation Protocol (SIP) domain, such as contoso.com.</span></span> <span data-ttu-id="51d15-129">일정에 따라이 하이브리드 구성을 사용 하 여 시간에 따라 온-프레미스에서 Office 365로 마이그레이션할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51d15-129">You can use this hybrid configuration to migrate from on-premises to Office 365 over time, on your schedule.</span></span> <span data-ttu-id="51d15-130">비즈니스용 Skype도 [Exchange Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/integration-with-exchange-and-sharepoint)과 통합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51d15-130">Skype for Business can also be integrated with [Exchange Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/integration-with-exchange-and-sharepoint).</span></span>
  
<span data-ttu-id="51d15-131">**그림 2: 비즈니스용 Skype 하이브리드 구성**</span><span class="sxs-lookup"><span data-stu-id="51d15-131">**Figure 2: The Skype for Business hybrid configuration**</span></span>

![비즈니스용 Skype 하이브리드 구성](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SfB.png)
  
<span data-ttu-id="51d15-133">그림 2는 Office 365에서 비즈니스용 skype Online과 통신 하는 온-프레미스 비즈니스용 skype 프런트 엔드 풀 및에 지 서버로 구성 된 비즈니스용 skype 하이브리드 구성을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="51d15-133">Figure 2 shows the Skype for Business hybrid configuration, consisting of an on-premises Skype for Business front end pool and edge server communicating with Skype for Business Online in Office 365.</span></span>
  
<span data-ttu-id="51d15-134">자세한 내용은 비즈니스용 [skype 서버 및 비즈니스용 skype Online 간의 하이브리드 연결 계획](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="51d15-134">For more information, see [Plan hybrid connectivity between Skype for Business Server and Skype for Business Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity).</span></span>
    
## <a name="cloud-pbx-with-skype-for-business-server"></a><span data-ttu-id="51d15-135">비즈니스용 Skype 서버가 포함 된 클라우드 PBX</span><span class="sxs-lookup"><span data-stu-id="51d15-135">Cloud PBX with Skype for Business Server</span></span>

<span data-ttu-id="51d15-136">비즈니스용 skype 서버가 포함 된 클라우드 PBX를 사용 하 여 기존 비즈니스용 skype 서버 온-프레미스 배포를 온-프레미스 PSTN (공중 전화망) 연결을 사용 하는 토폴로지로 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51d15-136">Cloud PBX with Skype for Business Server lets you transition an existing Skype for Business Server on-premises deployment to a topology with on-premises Public Switched Telephone Network (PSTN) connectivity.</span></span> 
  
<span data-ttu-id="51d15-137">**그림 3: 비즈니스용 Skype 서버가 포함 된 클라우드 PBX**</span><span class="sxs-lookup"><span data-stu-id="51d15-137">**Figure 3: Cloud PBX with Skype for Business Server**</span></span>

![비즈니스용 Skype 서버가 포함 된 클라우드 PBX](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SfB-CloudPBX.png)
  
<span data-ttu-id="51d15-139">그림 3에서는 비즈니스용 skype를 포함 하 여 Office 365에서 Microsoft 클라우드 PBX에 연결 된 온-프레미스 pbx 또는 Telco 게이트웨이, 비즈니스용 skype 서버로 구성 되는 비즈니스용 skype 서버 구성이 포함 된 클라우드 pbx를 보여 줍니다. 온라인.</span><span class="sxs-lookup"><span data-stu-id="51d15-139">Figure 3 shows the Cloud PBX with Skype for Business Server configuration, consisting of an on-premises existing PBX or Telco gateway, a Skype for Business Server, and the PSTN connected to the Microsoft Cloud PBX in Office 365, which includes Skype for Business Online.</span></span>
  
<span data-ttu-id="51d15-140">클라우드에 있는 조직의 사용자는 신호 및 음성 메일을 포함 하는 Microsoft 클라우드에서 PBX (private branch exchange) 서비스를 받을 수 있지만 온-프레미스에서 Enterprise Voice를 통해 PSTN 연결 (발신음)이 제공 됩니다. 비즈니스용 Skype 서버 배포</span><span class="sxs-lookup"><span data-stu-id="51d15-140">Users in the organization who are homed in the cloud can receive private branch exchange (PBX) services from the Microsoft cloud that include signaling and voicemail, but PSTN connectivity (dial tone) is provided through Enterprise Voice from your on-premises Skype for Business Server deployment.</span></span>
  
<span data-ttu-id="51d15-141">이 예제는 클라우드 기반 서비스로 점진적으로 마이그레이션할 수 있도록 하는 하이브리드 구성의 좋은 예입니다.</span><span class="sxs-lookup"><span data-stu-id="51d15-141">This is a great example of a hybrid configuration that lets you gradually migrate to a cloud-based service.</span></span> <span data-ttu-id="51d15-142">비즈니스용 Skype Online으로 이동 하기 시작할 때 사용자의 음성 기능을 유지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51d15-142">You can retain your users' voice capabilities as you begin to move them to Skype for Business Online.</span></span> <span data-ttu-id="51d15-143">사용자를 원하는 속도로 이동 하 여 자신의 음성 기능이 홈 위치에 관계 없이 계속 해 서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51d15-143">You can move your users at your own pace, knowing that their voice features will continue no matter where they are homed.</span></span> 
  
<span data-ttu-id="51d15-144">자세한 내용은 비즈니스용 [skype 서버 및 비즈니스용 skype Online 간의 하이브리드 연결 계획](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="51d15-144">For more information, see [Plan hybrid connectivity between Skype for Business Server and Skype for Business Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity).</span></span>
  
<span data-ttu-id="51d15-145">기존 Lync server 또는 비즈니스용 skype 서버 배포가 아직 없는 경우 비즈니스용 skype 클라우드 커넥터 Edition, 클라우드 PBX로 온-프레미스 PSTN 연결을 구현 하는 패키지 vm (가상 컴퓨터) 집합을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51d15-145">If you do not already have an existing Lync Server or Skype for Business Server deployment, you can use Skype for Business Cloud Connector Edition, a set of packaged virtual machines (VMs) that implement on-premises PSTN connectivity with Cloud PBX.</span></span>
  
<span data-ttu-id="51d15-146">자세한 내용은 [비즈니스용 Skype 클라우드 Connector Edition 계획](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-skype-for-business-cloud-connector-edition)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="51d15-146">For more information, see [Plan for Skype for Business Cloud Connector Edition](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-skype-for-business-cloud-connector-edition).</span></span>

  
## <a name="sharepoint-hybrid"></a><span data-ttu-id="51d15-147">SharePoint 하이브리드</span><span class="sxs-lookup"><span data-stu-id="51d15-147">SharePoint Hybrid</span></span>

<span data-ttu-id="51d15-148">sharepoint 하이브리드는 연결 된 세계 최고의 환경을 위해 Office 365의 sharepoint Online을 온-프레미스 sharepoint 팜과 결합 합니다.</span><span class="sxs-lookup"><span data-stu-id="51d15-148">SharePoint hybrid combines SharePoint Online in Office 365 with your on-premises SharePoint farm for a best of both worlds, connected experience.</span></span>
  
<span data-ttu-id="51d15-149">**그림 4: SharePoint 하이브리드 구성**</span><span class="sxs-lookup"><span data-stu-id="51d15-149">**Figure 4: The SharePoint hybrid configuration**</span></span>

![SharePoint 하이브리드 구성](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SP.png)
  
<span data-ttu-id="51d15-151">그림 4에서는 Office 365에서 sharepoint Online과 통신 하는 온-프레미스 sharepoint 팜으로 구성 된 sharepoint 하이브리드 구성을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="51d15-151">Figure 4 shows the SharePoint hybrid configuration, consisting of an on-premises SharePoint farm communicating with SharePoint Online in Office 365.</span></span>
  
<span data-ttu-id="51d15-152">SharePoint 하이브리드 시나리오:</span><span class="sxs-lookup"><span data-stu-id="51d15-152">SharePoint hybrid scenarios:</span></span>
  
- [<span data-ttu-id="51d15-153">하이브리드 비즈니스용 OneDrive</span><span class="sxs-lookup"><span data-stu-id="51d15-153">Hybrid OneDrive for Business</span></span>](https://docs.microsoft.com/SharePoint/hybrid/configure-hybrid-onedrive-for-businessroadmap)
    
- [<span data-ttu-id="51d15-154">하이브리드 엑스트라넷 B2B</span><span class="sxs-lookup"><span data-stu-id="51d15-154">Hybrid Extranet B2B</span></span>](https://docs.microsoft.com/sharepoint/create-b2b-extranet)
    
- [<span data-ttu-id="51d15-155">하이브리드 검색</span><span class="sxs-lookup"><span data-stu-id="51d15-155">Hybrid search</span></span>](https://docs.microsoft.com/SharePoint/hybrid/configure-cloud-hybrid-searchroadmap)
    
- [<span data-ttu-id="51d15-156">하이브리드 프로필</span><span class="sxs-lookup"><span data-stu-id="51d15-156">Hybrid profiles</span></span>](https://docs.microsoft.com/SharePoint/hybrid/plan-hybrid-profiles)
    
- [<span data-ttu-id="51d15-157">하이브리드 선택기</span><span class="sxs-lookup"><span data-stu-id="51d15-157">Hybrid Picker</span></span>](https://docs.microsoft.com/SharePoint/hybrid/hybrid-picker-in-the-sharepoint-online-admin-center)
    
    <span data-ttu-id="51d15-158">Office 365의 SharePoint Online 관리 센터에서 사용할 수 있는 하이브리드 구성을 자동화 하는 마법사를 사용 하 여 하이브리드 시나리오를 간편 하 게 활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51d15-158">It is easy to enable hybrid scenarios using the wizards that automate hybrid configuration, available from the SharePoint Online admin center in Office 365.</span></span>
    
- [<span data-ttu-id="51d15-159">확장 가능한 하이브리드 앱 시작 관리자</span><span class="sxs-lookup"><span data-stu-id="51d15-159">Extensible hybrid app launcher</span></span>](https://docs.microsoft.com/SharePoint/hybrid/the-extensible-hybrid-app-launcher)
    
    <span data-ttu-id="51d15-160">사용자가 온-프레미스 SharePoint 팜의 페이지 내에서 Office 365 비디오 및 Delve 앱과 경험을 보고 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51d15-160">Allows users to view and use Office 365 video and Delve apps and experiences within the pages of their on-premises SharePoint farm.</span></span>
    
<span data-ttu-id="51d15-161">확장 가능한 하이브리드 앱 시작 관리자를 제외한 이러한 모든 sharepoint 하이브리드 시나리오는 sharepoint 2016 및 sharepoint 2013 사용자 모두에 게 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="51d15-161">All of these SharePoint hybrid scenarios, except the Extensible hybrid app launcher, are available for both SharePoint 2016 and SharePoint 2013 users.</span></span>
  
## <a name="exchange-server-2016-hybrid"></a><span data-ttu-id="51d15-162">Exchange Server 2016 하이브리드</span><span class="sxs-lookup"><span data-stu-id="51d15-162">Exchange Server 2016 Hybrid</span></span>

<span data-ttu-id="51d15-163">exchange server 2016 Hybrid에서는 온-프레미스 사용자가 기존 exchange Server 인프라를 계속 사용 하는 동안 온라인 사용자를 위해 Office 365에서 exchange online의 이점을 실현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51d15-163">With Exchange Server 2016 Hybrid, you can realize the benefits of Exchange Online in Office 365 for online users while on-premises users continue to use existing Exchange Server infrastructure.</span></span> 
  
<span data-ttu-id="51d15-164">**그림 5: Exchange 2016 하이브리드 구성**</span><span class="sxs-lookup"><span data-stu-id="51d15-164">**Figure 5: The Exchange 2016 hybrid configuration**</span></span>

![Exchange 2016 하이브리드 구성](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-EX.png)
  
<span data-ttu-id="51d15-166">그림 5에서는 exchange Online Protection과 통신 하는 온-프레미스 Exchange 사서함 서버와 Office 365의 사서함으로 구성 되는 exchange 2016 하이브리드 구성을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="51d15-166">Figure 5 shows the Exchange 2016 hybrid configuration, consisting of on-premises Exchange mailbox servers communicating with Exchange Online Protection and mailboxes in Office 365.</span></span>
  
<span data-ttu-id="51d15-167">일부 사용자에 게는 온-프레미스 전자 메일 서버가 있으며 일부 사용자는 Exchange Online을 사용 하지만 모든 사용자는 같은 전자 메일 주소 공간을 공유 합니다.</span><span class="sxs-lookup"><span data-stu-id="51d15-167">Some users have an on-premises email server and some users use Exchange Online, but all users share the same e-mail address space.</span></span> 
  
<span data-ttu-id="51d15-168">다음과 같은 하이브리드 구성을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="51d15-168">This hybrid configuration:</span></span>
  
- <span data-ttu-id="51d15-169">일정에 따라 시간에 따라 exchange Online으로 마이그레이션하는 동안 기존 exchange Server 인프라를 활용 합니다.</span><span class="sxs-lookup"><span data-stu-id="51d15-169">Leverages your existing Exchange Server infrastructure while you migrate to Exchange Online over time, on your schedule.</span></span>
    
- <span data-ttu-id="51d15-170">지점 인프라에 대 한 투자 없이 원격 사이트를 지원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51d15-170">Allows you to support remote sites without investing in branch office infrastructure.</span></span>
    
- <span data-ttu-id="51d15-171">Office 365에서 Exchange Online Protection을 통해 들어오는 인터넷 전자 메일을 라우팅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51d15-171">Allows you to route incoming Internet email through Exchange Online Protection in Office 365.</span></span>
    
- <span data-ttu-id="51d15-172">데이터를 온-프레미스에 배치 해야 하는 자회사와 다국적 조직의 요구 사항을 충족 합니다.</span><span class="sxs-lookup"><span data-stu-id="51d15-172">Serves the needs of multinational organizations with subsidiaries that require data to reside on-premises.</span></span>
    
<span data-ttu-id="51d15-173">또한이 하이브리드 구성을 비즈니스용 Skype online 및 SharePoint Online을 포함 하 여 다른 Microsoft Office 365 응용 프로그램에 통합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51d15-173">You can also integrate this hybrid configuration with other Microsoft Office 365 applications, including Skype for Business Online and SharePoint Online.</span></span>
  
<span data-ttu-id="51d15-174">자세한 내용은 [Exchange Server 하이브리드 배포](https://docs.microsoft.com/exchange/exchange-hybrid)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="51d15-174">For more information, see [Exchange Server Hybrid Deployments](https://docs.microsoft.com/exchange/exchange-hybrid).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="51d15-175">참고 항목</span><span class="sxs-lookup"><span data-stu-id="51d15-175">See Also</span></span>

[<span data-ttu-id="51d15-176">Microsoft Hybrid Cloud for Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="51d15-176">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="51d15-177">Microsoft 클라우드 IT 아키텍처 리소스</span><span class="sxs-lookup"><span data-stu-id="51d15-177">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

