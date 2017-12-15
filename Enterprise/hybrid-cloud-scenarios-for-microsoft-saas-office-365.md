---
title: "Microsoft SaaS (Office 365)에 대 한 하이브리드 클라우드 시나리오"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Visuals
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: db117e59-389f-46f5-a5df-4eeac0040aa8
description: "요약: Microsoft의 SaaS 기반에 대 한 하이브리드 아키텍처 및 시나리오 이해 클라우드 제품 (Office 365)."
ms.openlocfilehash: 5f50573376b70ad94b3b1cd4b86ce3ef1fdc67dd
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2017
---
# <a name="hybrid-cloud-scenarios-for-microsoft-saas-office-365"></a><span data-ttu-id="37659-103">Microsoft SaaS (Office 365)에 대 한 하이브리드 클라우드 시나리오</span><span class="sxs-lookup"><span data-stu-id="37659-103">Hybrid cloud scenarios for Microsoft SaaS (Office 365)</span></span>

 <span data-ttu-id="37659-104">**요약:** Microsoft의 SaaS 기반에 대 한 하이브리드 아키텍처 및 시나리오 이해 클라우드 제품 (Office 365).</span><span class="sxs-lookup"><span data-stu-id="37659-104">**Summary:** Understand the hybrid architecture and scenarios for Microsoft's SaaS-based cloud offerings (Office 365).</span></span>
  
<span data-ttu-id="37659-105">자신의 대응 하는 클라우드 마이그레이션 또는 장기 통합 전략의 일부분으로 Office 365를 사용한 Exchange, SharePoint, 또는 비즈니스를 위한 Skype의 온-프레미스 배포를 결합 합니다.</span><span class="sxs-lookup"><span data-stu-id="37659-105">Combine on-premises deployments of Exchange, SharePoint, or Skype for Business with their counterparts in Office 365 as part of a cloud migration or long-term integration strategy.</span></span>
  
## <a name="microsoft-saas-hybrid-scenario-architecture"></a><span data-ttu-id="37659-106">Microsoft SaaS 하이브리드 시나리오 아키텍처</span><span class="sxs-lookup"><span data-stu-id="37659-106">Microsoft SaaS hybrid scenario architecture</span></span>

<span data-ttu-id="37659-107">그림 1 Office 365에 대 한 Microsoft SaaS 기반 하이브리드 시나리오의 아키텍처를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="37659-107">Figure 1 shows the architecture of Microsoft SaaS-based hybrid scenarios for Office 365.</span></span>
  
<span data-ttu-id="37659-108">**Office 365에 대 한 그림 1: Microsoft SaaS 기반 하이브리드 시나리오**</span><span class="sxs-lookup"><span data-stu-id="37659-108">**Figure 1: Microsoft SaaS-based hybrid scenarios for Office 365**</span></span>

![Office 365용 Microsoft SaaS 기반 하이브리드 시나리오](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS.png)
  
<span data-ttu-id="37659-110">아키텍처의 각 레이어에:</span><span class="sxs-lookup"><span data-stu-id="37659-110">For each layer of the architecture:</span></span>
  
- <span data-ttu-id="37659-111">앱 및 시나리오</span><span class="sxs-lookup"><span data-stu-id="37659-111">Apps and scenarios</span></span>
    
    <span data-ttu-id="37659-112">SaaS 기반 하이브리드 시나리오를 중심으로 Office 서버 제품 및 Office 365 대응 하는 해당 맞춤의 다양 한 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37659-112">There are a variety of SaaS-based hybrid scenarios, aligning around Office Server products and their Office 365 counterparts:</span></span>
    
  - <span data-ttu-id="37659-113">Exchange Online (Exchange Server 하이브리드)와 결합 하는 Exchange Server</span><span class="sxs-lookup"><span data-stu-id="37659-113">Exchange Server combined with Exchange Online (Exchange Server hybrid)</span></span>
    
  - <span data-ttu-id="37659-114">Skype 비즈니스 서버에 대 한 비즈니스 온라인 및 새로운 클라우드 PBX와 클라우드 커넥터 Edition 시나리오에 대 한 Skype와 결합합니다.</span><span class="sxs-lookup"><span data-stu-id="37659-114">Skype for Business Server combined with Skype for Business Online and the new Cloud PBX and Cloud Connector Edition scenarios</span></span>
    
  - <span data-ttu-id="37659-115">SharePoint Server 2016 또는 SharePoint Server 2013 결합 된 SharePoint Online (여러 시나리오)</span><span class="sxs-lookup"><span data-stu-id="37659-115">SharePoint Server 2016 or SharePoint Server 2013 combined with SharePoint Online (multiple scenarios)</span></span>
    
    <span data-ttu-id="37659-116">방법이 Skype와 Exchange Online Business Server 온-프레미스, 제품 간 하이브리드 시나리오에 대 한입니다.</span><span class="sxs-lookup"><span data-stu-id="37659-116">There is also Exchange Online with Skype for Business Server on-premises, a cross-product hybrid scenario.</span></span>
    
- <span data-ttu-id="37659-117">Identity</span><span class="sxs-lookup"><span data-stu-id="37659-117">Identity</span></span>
    
    <span data-ttu-id="37659-p101">온-프레미스 Windows Server AD와 디렉터리 동기화를 포함할 수 있습니다. 또는 타사 id 공급자와 페더레이션 할 Azure AD를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37659-p101">Can include directory synchronization with your on-premises Windows Server AD. Alternately, you can configure Azure AD to federate with a third-party identity provider.</span></span>
    
- <span data-ttu-id="37659-120">네트워크</span><span class="sxs-lookup"><span data-stu-id="37659-120">Network</span></span>
    
    <span data-ttu-id="37659-121">Microsoft Office 365 또는 Dynamics 365 대 한 피어 링와 기존 인터넷 파이프 대화 또는 ExpressRoute에 대 한 연결 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="37659-121">Consists of either your existing Internet pipe or an ExpressRoute connection with Microsoft peering for Office 365 or Dynamics 365.</span></span>
    
- <span data-ttu-id="37659-122">온-프레미스</span><span class="sxs-lookup"><span data-stu-id="37659-122">On-premises</span></span>
    
    <span data-ttu-id="37659-p102">Exchange, SharePoint 및 최신 버전으로 업데이트 되어야 하는 비즈니스를 위한 Skype에 대 한 기존 서버의 구성할 수 있습니다. 다음 하이브리드 시나리오를 위한 Office 365 대응 하는 자신의으로 조합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37659-p102">Can consist of existing servers for Exchange, SharePoint, and Skype for Business, which should be updated to their latest versions. You can then combine them with their Office 365 counterparts for hybrid scenarios.</span></span>
    
<span data-ttu-id="37659-125">사용자가 자신의 [Office 365 개발/테스트 환경](office-365-dev-test-environment.md)설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="37659-125">Set up your own [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
## <a name="skype-for-business-2015-hybrid"></a><span data-ttu-id="37659-126">비즈니스 2015 하이브리드 용 Skype</span><span class="sxs-lookup"><span data-stu-id="37659-126">Skype for Business 2015 Hybrid</span></span>

<span data-ttu-id="37659-p103">비즈니스 2015 하이브리드에 대 한 Skype를 사용 하면 비즈니스 Online 용 Skype 포함 하는 기존 온-프레미스 배포를 결합 하 여 있습니다. 일부 사용자는 홈된 온-프레미스 및 일부 사용자가 온라인 상태에 있는 하지만 사용자가 동일한 프로토콜 SIP (Session Initiation) 도메인 contoso.com 등을 공유 합니다. 이 하이브리드 구성을 마이그레이션하려면 온-프레미스에서 Office 365 시간이 지남에 따라 일정에 사용할 수 있습니다. 비즈니스 2015 용 Skype Exchange Online과 통합 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37659-p103">Skype for Business 2015 Hybrid allows you to combine an existing on-premises deployment with Skype for Business Online. Some users are homed on-premises and some users are homed online, but the users share the same Session Initiation Protocol (SIP) domain, such as contoso.com. You can use this hybrid configuration to migrate from on-premises to Office 365 over time, on your schedule. Skype for Business 2015 can also be integrated with Exchange Online.</span></span>
  
<span data-ttu-id="37659-130">**그림 2: 비즈니스 2015 하이브리드 구성에 대 한 Skype**</span><span class="sxs-lookup"><span data-stu-id="37659-130">**Figure 2: The Skype for Business 2015 hybrid configuration**</span></span>

![비즈니스용 Skype 2015 하이브리드 구성](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS_SfB.png)
  
<span data-ttu-id="37659-132">그림 2는 온-프레미스 Skype 비즈니스 2015 프런트엔드 풀과 Office 365의 온라인 비즈니스에 대 한 Skype와에 지 서버 통신에 대해 구성 된 비즈니스 2015 하이브리드 구성에 대 한 Skype를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="37659-132">Figure 2 shows the Skype for Business 2015 hybrid configuration, consisting of an on-premises Skype for Business 2015 front end pool and edge server communicating with Skype for Business Online in Office 365.</span></span>
  
<span data-ttu-id="37659-133">자세한 내용은 다음을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="37659-133">For more information, see:</span></span>
  
- [<span data-ttu-id="37659-134">비즈니스 서버에 대 한 Skype와 비즈니스 온라인 용 Skype 간의 하이브리드 연결 계획</span><span class="sxs-lookup"><span data-stu-id="37659-134">Plan hybrid connectivity between Skype for Business Server and Skype for Business Online</span></span>](https://technet.microsoft.com/library/jj205403.aspx)
    
- [<span data-ttu-id="37659-135">비즈니스 서버 2015 용 Skype에 대 한 지원 되는 하이브리드 구성</span><span class="sxs-lookup"><span data-stu-id="37659-135">Supported hybrid configurations for Skype for Business Server 2015</span></span>](https://technet.microsoft.com/library/jj945633.aspx)
    
- [<span data-ttu-id="37659-136">비즈니스 하이브리드 용 Skype</span><span class="sxs-lookup"><span data-stu-id="37659-136">Skype for Business Hybrid</span></span>](http://hybrid.office.com/skype-for-business/)
    
## <a name="cloud-pbx-with-skype-for-business-server"></a><span data-ttu-id="37659-137">비즈니스용 Skype 서버가 포함된 클라우드 PBX</span><span class="sxs-lookup"><span data-stu-id="37659-137">Cloud PBX with Skype for Business Server</span></span>

<span data-ttu-id="37659-138">클라우드 비즈니스 서버에 대 한 Skype와 PBX를 사용 하는 기존 Skype 토폴로지로 Business Server 온-프레미스 배포를 위한 온-프레미스 공용 전화 네트워크 (PSTN) 연결이 설정 된 전환 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37659-138">Cloud PBX with Skype for Business Server allows you to transition an existing Skype for Business Server on-premises deployment to a topology with on-premises Public Switched Telephone Network (PSTN) connectivity.</span></span> 
  
<span data-ttu-id="37659-139">**그림 3: 클라우드 비즈니스 서버에 대 한 Skype와 PBX**</span><span class="sxs-lookup"><span data-stu-id="37659-139">**Figure 3: Cloud PBX with Skype for Business Server**</span></span>

![비즈니스용 Skype 서버가 포함된 클라우드 PBX](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS_SfB_CloudPBX.png)
  
<span data-ttu-id="37659-141">그림 3 비즈니스 서버 구성의 경우 온-프레미스 비즈니스를 위한 Skype를 포함 하는 Office 365의 Microsoft 클라우드 PBX에 연결 하는 기존 PBX 또는 Telco 게이트웨이, 비즈니스 서버에 대 한 Skype와 PSTN으로 이루어진 Skype와 클라우드 PBX를 보여줍니다. 온라인.</span><span class="sxs-lookup"><span data-stu-id="37659-141">Figure 3 shows the Cloud PBX with Skype for Business Server configuration, consisting of an on-premises existing PBX or Telco gateway, a Skype for Business Server, and the PSTN connected to the Microsoft Cloud PBX in Office 365, which includes Skype for Business Online.</span></span>
  
<span data-ttu-id="37659-142">조직에 있는 사용자의 클라우드에서 신호 및 음성 메일을 포함 하는 Microsoft 클라우드에서 private branch exchange (PBX) 서비스를 받을 수는 있지만 PSTN 연결 (발신음)에서 온-프레미스에서 Enterprise Voice를 통해 제공 됩니다. Business Server 배포에 대 한 Skype 합니다.</span><span class="sxs-lookup"><span data-stu-id="37659-142">Users in the organization who are homed in the cloud can receive private branch exchange (PBX) services from the Microsoft cloud that include signaling and voicemail, but PSTN connectivity (dial tone) is provided through Enterprise Voice from your on-premises Skype for Business Server deployment.</span></span>
  
<span data-ttu-id="37659-p104">클라우드 기반 서비스를 점진적으로 마이그레이션할 수 있도록 하는 하이브리드 구성의 예입니다. 비즈니스 Online 용 Skype를 이동 하기 시작 하면 사용자의 음성 기능을 유지할 수 있습니다. 속도 자신의 음성 기능 no 계속 될 거 알고 있으면 직접 문제에는 홈 지정 사용자에 게 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37659-p104">This is a great example of a hybrid configuration that allows you to gradually migrate to a cloud-based service. You can retain your users' voice capabilities as you begin to move them to Skype for Business Online. You can move your users at your own pace, knowing that their voice features will continue no matter where they are homed.</span></span> 
  
<span data-ttu-id="37659-146">자세한 내용은 [비즈니스 서버 및 비즈니스 Online 또는 Lync Server 2013에 대 한 Skype Skype 간의 하이브리드 연결 계획](https://technet.microsoft.com/library/jj205403.aspx)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="37659-146">For more information, see [Plan hybrid connectivity between Skype for Business Server and Skype for Business Online or Lync Server 2013](https://technet.microsoft.com/library/jj205403.aspx).</span></span>
  
<span data-ttu-id="37659-147">수행 하지 이미 있는 경우 기존 Lync 서버나 Skype Business Server 배포에 대 한, Skype 비즈니스 클라우드 커넥터 edition의 경우 가공된 Vm (가상 컴퓨터) 클라우드 PBX와의 온-프레미스 PSTN 연결을 구현 하는 집합을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37659-147">If you do not already have an existing Lync Server or Skype for Business Server deployment, you can use Skype for Business Cloud Connector Edition, a set of packaged virtual machines (VMs) that implement on-premises PSTN connectivity with Cloud PBX.</span></span>
  
<span data-ttu-id="37659-148">자세한 내용은 [Skype 비즈니스 클라우드 커넥터 edition에 대 한 계획](https://technet.microsoft.com/library/mt605227.aspx)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="37659-148">For more information, see [Plan for Skype for Business Cloud Connector Edition](https://technet.microsoft.com/library/mt605227.aspx).</span></span>
  
## <a name="sharepoint-hybrid"></a><span data-ttu-id="37659-149">SharePoint 하이브리드</span><span class="sxs-lookup"><span data-stu-id="37659-149">SharePoint Hybrid</span></span>

<span data-ttu-id="37659-150">두 세계, 연결 된 경험의 가장에 대 한 온-프레미스 SharePoint 팜과 SharePoint 하이브리드 Office 365의 SharePoint Online으로 결합합니다.</span><span class="sxs-lookup"><span data-stu-id="37659-150">SharePoint hybrid combines SharePoint Online in Office 365 with your on-premises SharePoint farm for a best of both worlds, connected experience.</span></span>
  
<span data-ttu-id="37659-151">**그림 4: SharePoint 하이브리드 구성**</span><span class="sxs-lookup"><span data-stu-id="37659-151">**Figure 4: The SharePoint hybrid configuration**</span></span>

![SharePoint 하이브리드 구성](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS_SP.png)
  
<span data-ttu-id="37659-153">그림 4에는 Office 365의 SharePoint Online과 통신 하는 온-프레미스 SharePoint 팜 구성 된 SharePoint 하이브리드 구성으로를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="37659-153">Figure 4 shows the SharePoint hybrid configuration, consisting of an on-premises SharePoint farm communicating with SharePoint Online in Office 365.</span></span>
  
<span data-ttu-id="37659-154">SharePoint 하이브리드 시나리오의 경우:</span><span class="sxs-lookup"><span data-stu-id="37659-154">SharePoint hybrid scenarios:</span></span>
  
- [<span data-ttu-id="37659-155">비즈니스를 위한 하이브리드 OneDrive</span><span class="sxs-lookup"><span data-stu-id="37659-155">Hybrid OneDrive for Business</span></span>](https://technet.microsoft.com/library/mt147425%28v=office.16%29.aspx)
    
- [<span data-ttu-id="37659-156">하이브리드 팀 사이트</span><span class="sxs-lookup"><span data-stu-id="37659-156">Hybrid team sites</span></span>](https://technet.microsoft.com/library/mt346110%28v=office.16%29.aspx)
    
- [<span data-ttu-id="37659-157">하이브리드 익스트라넷 B2B</span><span class="sxs-lookup"><span data-stu-id="37659-157">Hybrid Extranet B2B</span></span>](https://support.office.com/article/SharePoint-Business-to-Business-Collaboration-Extranet-for-Partners-with-Office-365-7b087413-165a-4e94-8871-4393e0b9c037)
    
- [<span data-ttu-id="37659-158">하이브리드 검색</span><span class="sxs-lookup"><span data-stu-id="37659-158">Hybrid search</span></span>](https://technet.microsoft.com/library/dn720906%28v=office.16%29.aspx)
    
- [<span data-ttu-id="37659-159">하이브리드 프로필</span><span class="sxs-lookup"><span data-stu-id="37659-159">Hybrid profiles</span></span>](https://support.office.com/article/Plan-hybrid-profiles-96d1eaf0-94eb-40c5-ab76-c82907777db4)
    
- [<span data-ttu-id="37659-160">하이브리드 선택</span><span class="sxs-lookup"><span data-stu-id="37659-160">Hybrid Picker</span></span>](https://support.office.com/article/Hybrid-picker-in-the-SharePoint-Online-admin-center-efce8417-c9bc-4a2c-ac9d-cce6c4e84a9c)
    
    <span data-ttu-id="37659-161">Office 365의 SharePoint Online 관리 센터에서 사용할 수 있는 하이브리드 구성을 자동화 하는 마법사를 사용 하 여 하이브리드 시나리오를 사용 하는 것이 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="37659-161">It is easy to enable hybrid scenarios using the wizards that automate hybrid configuration, available from the SharePoint Online admin center in Office 365.</span></span>
    
- [<span data-ttu-id="37659-162">확장 가능한 하이브리드 응용 프로그램 시작 관리자</span><span class="sxs-lookup"><span data-stu-id="37659-162">Extensible hybrid app launcher</span></span>](https://support.office.com/article/The-extensible-hybrid-app-launcher-617a7cb5-53da-4128-961a-64a840c0ab91)
    
    <span data-ttu-id="37659-163">보고 하 여 Office 365 비디오 및 Delve 앱을 사용 하 여 사용자가 허용 하 고 자신의 온-프레미스 SharePoint 팜의 페이지 내에서 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="37659-163">Allows users to view and use Office 365 video and Delve apps and experiences within the pages of their on-premises SharePoint farm.</span></span>
    
<span data-ttu-id="37659-164">확장할 수 있는 하이브리드 응용 프로그램 시작 관리자를 제외 하 고 이러한 SharePoint 하이브리드 시나리오 모두 SharePoint 2016 및 SharePoint 2013 사용자 모두에 대해 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37659-164">All of these SharePoint hybrid scenarios, except the Extensible hybrid app launcher, are available for both SharePoint 2016 and SharePoint 2013 users.</span></span>
  
<span data-ttu-id="37659-165">자세한 내용은 [SharePoint 하이브리드](http://hybrid.office.com/sharepoint/)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="37659-165">For more information, see [SharePoint Hybrid](http://hybrid.office.com/sharepoint/).</span></span>
  
## <a name="exchange-server-2016-hybrid"></a><span data-ttu-id="37659-166">Exchange Server 2016 하이브리드</span><span class="sxs-lookup"><span data-stu-id="37659-166">Exchange Server 2016 Hybrid</span></span>

<span data-ttu-id="37659-167">Exchange Server 2016 하이브리드 사용 하면 기존 Exchange 서버 인프라를 사용 하 여 온-프레미스 사용자가 계속 되는 동안 온라인 사용자를 위한 Office 365의 Exchange Online의 이점을 인식할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37659-167">With Exchange Server 2016 Hybrid, you can realize the benefits of Exchange Online in Office 365 for online users while on-premises users continue to use existing Exchange Server infrastructure.</span></span> 
  
<span data-ttu-id="37659-168">**그림 5: Exchange 2016 하이브리드 구성**</span><span class="sxs-lookup"><span data-stu-id="37659-168">**Figure 5: The Exchange 2016 hybrid configuration**</span></span>

![Exchange 2016 하이브리드 구성](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS_EX.png)
  
<span data-ttu-id="37659-170">그림 5는 Exchange Online Protection 및 Office 365에서 사서함와 통신 하는 온-프레미스 Exchange 사서함 서버 구성 된 Exchange 2016 하이브리드 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="37659-170">Figure 5 shows the Exchange 2016 hybrid configuration, consisting of on-premises Exchange mailbox servers communicating with Exchange Online Protection and mailboxes in Office 365.</span></span>
  
<span data-ttu-id="37659-171">일부 사용자는 온-프레미스 전자 메일 서버 및 일부 사용자를 사용 하 여 Exchange Online 되었지만 동일한 전자 메일 주소 공간을 공유 하는 모든 사용자에 게 합니다.</span><span class="sxs-lookup"><span data-stu-id="37659-171">Some users have an on-premises email server and some users use Exchange Online, but all users share the same e-mail address space.</span></span> 
  
<span data-ttu-id="37659-172">이 하이브리드 구성:</span><span class="sxs-lookup"><span data-stu-id="37659-172">This hybrid configuration:</span></span>
  
- <span data-ttu-id="37659-173">마이그레이션할 Exchange Online으로 시간이 지남에 따라 일정에 하는 동안 사용 하도록 기존 Exchange 서버 인프라를 활용 합니다.</span><span class="sxs-lookup"><span data-stu-id="37659-173">Leverages your existing Exchange Server infrastructure while you migrate to Exchange Online over time, on your schedule.</span></span>
    
- <span data-ttu-id="37659-174">Branch office 인프라에 투자 하지 않고도 원격 사이트를 지원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37659-174">Allows you to support remote sites without investing in branch office infrastructure.</span></span>
    
- <span data-ttu-id="37659-175">Office 365의 Exchange Online Protection을 통해 들어오는 인터넷 전자 메일을 라우팅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37659-175">Allows you to route incoming Internet email through Exchange Online Protection in Office 365.</span></span>
    
- <span data-ttu-id="37659-176">온-프레미스 상주 하는 데이터를 필요로 하는 자회사와 다국적 조직의 요구를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="37659-176">Serves the needs of multinational organizations with subsidiaries that require data to reside on-premises.</span></span>
    
<span data-ttu-id="37659-177">이 하이브리드 구성 Skype를 포함 하 여 비즈니스 온라인 및 SharePoint Online에 대 한 다른 Microsoft Office 365 응용 프로그램과 통합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37659-177">You can also integrate this hybrid configuration with other Microsoft Office 365 applications, including Skype for Business Online and SharePoint Online.</span></span>
  
<span data-ttu-id="37659-178">자세한 내용은 [Exchange Server 하이브리드 배포](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx) 및 [Exchange 하이브리드](http://hybrid.office.com/exchange/)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="37659-178">For more information, see [Exchange Server Hybrid Deployments](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx) and [Exchange Hybrid](http://hybrid.office.com/exchange/).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="37659-179">See Also</span><span class="sxs-lookup"><span data-stu-id="37659-179">See Also</span></span>

[<span data-ttu-id="37659-180">엔터프라이즈 설계자 용 Microsoft 하이브리드 클라우드</span><span class="sxs-lookup"><span data-stu-id="37659-180">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="37659-181">Microsoft 클라우드 IT 아키텍처 리소스</span><span class="sxs-lookup"><span data-stu-id="37659-181">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="37659-182">Microsoft의 엔터프라이즈 클라우드 로드맵: IT 의사 결정권자를 위한 리소스</span><span class="sxs-lookup"><span data-stu-id="37659-182">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



