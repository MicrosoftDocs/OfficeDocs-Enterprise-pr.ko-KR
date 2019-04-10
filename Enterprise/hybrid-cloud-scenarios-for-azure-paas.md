---
title: Azure PaaS용 하이브리드 클라우드 시나리오
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
ms.assetid: 5f4f5d0d-4638-48e8-a517-bd804856b617
description: '요약: Azure의 Microsoft PaaS (Platform as a Service) 기반 클라우드 제품에 대 한 하이브리드 아키텍처 및 시나리오를 이해 합니다.'
ms.openlocfilehash: f4d90d51a7627063fae6fd168681bdf96cb4d6bc
ms.sourcegitcommit: 682b180061dc63cd602bee567d5414eae6942572
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/09/2019
ms.locfileid: "31741374"
---
# <a name="hybrid-cloud-scenarios-for-azure-paas"></a><span data-ttu-id="713c0-103">Azure PaaS용 하이브리드 클라우드 시나리오</span><span class="sxs-lookup"><span data-stu-id="713c0-103">Hybrid cloud scenarios for Azure PaaS</span></span>

 <span data-ttu-id="713c0-104">**요약:** Azure의 PaaS (Platform as a Service) 기반 클라우드 제품에 대 한 하이브리드 아키텍처 및 시나리오를 이해 합니다.</span><span class="sxs-lookup"><span data-stu-id="713c0-104">**Summary:** Understand the hybrid architecture and scenarios for Microsoft's Platform as a Service (PaaS)-based cloud offerings in Azure.</span></span>
  
<span data-ttu-id="713c0-105">온-프레미스 데이터 또는 컴퓨팅 리소스를 Azure PaaS에서 실행 되는 새로운 또는 변환 된 응용 프로그램으로 결합 하 여 클라우드 성능, 안정성 및 확장성을 활용 하 고 모바일 사용자에 대 한 향상 된 지원을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="713c0-105">Combine on-premises data or computing resources with new or converted applications running in Azure PaaS, which can take advantage of cloud performance, reliability, and scale and provide better support for mobile users.</span></span> 
  
## <a name="azure-paas-hybrid-scenario-architecture"></a><span data-ttu-id="713c0-106">Azure PaaS 하이브리드 시나리오 아키텍처</span><span class="sxs-lookup"><span data-stu-id="713c0-106">Azure PaaS hybrid scenario architecture</span></span>

<span data-ttu-id="713c0-107">그림 1에서는 Azure의 Microsoft PaaS 기반 하이브리드 시나리오 아키텍처를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="713c0-107">Figure 1 shows the architecture of Microsoft PaaS-based hybrid scenarios in Azure.</span></span>
  
**<span data-ttu-id="713c0-108">그림 1: Azure의 Microsoft PaaS 기반 하이브리드 시나리오</span><span class="sxs-lookup"><span data-stu-id="713c0-108">Figure 1: Microsoft PaaS-based hybrid scenarios in Azure</span></span>**

![Azure의 Microsoft PaaS 기반 하이브리드 시나리오](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS.png)
  
<span data-ttu-id="713c0-110">아키텍처의 각 계층에 대해 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="713c0-110">For each layer of the architecture:</span></span>
  
- <span data-ttu-id="713c0-111">앱 및 시나리오</span><span class="sxs-lookup"><span data-stu-id="713c0-111">Apps and scenarios</span></span>
    
    <span data-ttu-id="713c0-112">하이브리드 PaaS 응용 프로그램은 Azure에서 실행 되며 온-프레미스 계산 또는 저장소 리소스를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="713c0-112">A hybrid PaaS application runs in Azure and uses on-premises compute or storage resources.</span></span>
    
- <span data-ttu-id="713c0-113">ID</span><span class="sxs-lookup"><span data-stu-id="713c0-113">Identity</span></span>
    
    <span data-ttu-id="713c0-114">디렉터리 동기화 또는 타사 id 공급자와의 페더레이션으로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="713c0-114">Consists of either directory synchronization or federation with a third-party identity provider.</span></span>
    
- <span data-ttu-id="713c0-115">네트워크</span><span class="sxs-lookup"><span data-stu-id="713c0-115">Network</span></span>
    
    <span data-ttu-id="713c0-116">기존 인터넷 파이프 또는 공용 피어 링을 통해 Azure PaaS로가는 express 연결로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="713c0-116">Consists of either your existing Internet pipe or an ExpressRoute connection with public peering to Azure PaaS.</span></span> <span data-ttu-id="713c0-117">Azure PaaS 응용 프로그램에서 온-프레미스 계산 또는 저장소 리소스에 액세스 하는 방법을 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="713c0-117">You must include a way for the Azure PaaS application to access the on-premises compute or storage resource.</span></span>
    
- <span data-ttu-id="713c0-118">온-프레미스</span><span class="sxs-lookup"><span data-stu-id="713c0-118">On-premises</span></span>
    
    <span data-ttu-id="713c0-119">id 및 보안 인프라와 Azure PaaS 응용 프로그램에서 안전 하 게 액세스할 수 있는 기존 LOB (기간 업무) 응용 프로그램 또는 데이터베이스 서버로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="713c0-119">Consists of identity and security infrastructure and existing line of business (LOB) applications or database servers, which an Azure PaaS application can securely access.</span></span>
    
## <a name="azure-paas-hybrid-application"></a><span data-ttu-id="713c0-120">Azure PaaS hybrid 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="713c0-120">Azure PaaS hybrid application</span></span>

<span data-ttu-id="713c0-121">그림 2에서는 Azure에서 실행 되는 하이브리드 응용 프로그램의 구성을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="713c0-121">Figure 2 shows the configuration of a hybrid application running in Azure.</span></span>
  
**<span data-ttu-id="713c0-122">그림 2: Azure PaaS 기반 하이브리드 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="713c0-122">Figure 2: Azure PaaS-based hybrid application</span></span>**

![Azure PaaS 기반 하이브리드 응용 프로그램](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS-Apps.png)
  
<span data-ttu-id="713c0-124">그림 2에서는 온-프레미스 네트워크가 서버의 저장소 또는 앱과 프록시 서버를 포함 하는 DMZ를 호스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="713c0-124">In Figure 2, an on-premises network hosts storage or apps on servers and a DMZ containing a proxy server.</span></span> <span data-ttu-id="713c0-125">인터넷을 통해 또는 express 연결을 통해 Azure PaaS 서비스에 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="713c0-125">It is connected to Azure PaaS services either over the Internet or with an ExpressRoute connection.</span></span>
  
<span data-ttu-id="713c0-126">조직은 다음을 수행 하 여 Azure PaaS hybrid 응용 프로그램에서 해당 계산 또는 저장소 리소스를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="713c0-126">An organization can make its compute or storage resources available to the Azure PaaS hybrid application by:</span></span>
  
- <span data-ttu-id="713c0-127">DMZ의 서버에서 리소스 호스팅</span><span class="sxs-lookup"><span data-stu-id="713c0-127">Hosting the resource on servers in the DMZ.</span></span>
    
- <span data-ttu-id="713c0-128">DMZ에서 역방향 프록시 서버 호스팅 온-프레미스에 있는 리소스에 대해 인증 되 고 인바운드 되는 HTTPS 기반 요청을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="713c0-128">Hosting a reverse proxy server in the DMZ, which allows authenticated, inbound, HTTPS-based requests to the resource that is located on-premises.</span></span>
    
<span data-ttu-id="713c0-129">Azure 앱은 다음의 자격 증명을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="713c0-129">The Azure app can use credentials from:</span></span>
  
- <span data-ttu-id="713c0-130">Azure ad: ad DS (Active Directory 도메인 서비스)와 같은 온-프레미스 id 공급자와 동기화 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="713c0-130">Azure AD, which can be synchronized with your on-premises identity provider, such as Active Directory Domain Services (AD DS).</span></span>
    
- <span data-ttu-id="713c0-131">타사 id 공급자</span><span class="sxs-lookup"><span data-stu-id="713c0-131">A third-party identity provider.</span></span>
    
### <a name="example-azure-paas-hybrid-application"></a><span data-ttu-id="713c0-132">예제 Azure PaaS hybrid application</span><span class="sxs-lookup"><span data-stu-id="713c0-132">Example Azure PaaS hybrid application</span></span>

<span data-ttu-id="713c0-133">그림 3에서는 Azure에서 실행 되는 하이브리드 응용 프로그램의 예를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="713c0-133">Figure 3 shows an example hybrid application running in Azure.</span></span>
  
**<span data-ttu-id="713c0-134">그림 3: Azure PaaS 기반 하이브리드 응용 프로그램의 예</span><span class="sxs-lookup"><span data-stu-id="713c0-134">Figure 3: An example Azure PaaS-based hybrid application</span></span>**

![Azure PaaS 기반 하이브리드 application의 예](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS-Apps-Ex.png)
  
<span data-ttu-id="713c0-136">그림 3에서는 온-프레미스 네트워크가 LOB 앱을 호스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="713c0-136">In Figure 3, an on-premises network hosts an LOB app.</span></span> <span data-ttu-id="713c0-137">Azure PaaS가 사용자 지정 모바일 앱을 호스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="713c0-137">Azure PaaS hosts a custom mobile app.</span></span> <span data-ttu-id="713c0-138">인터넷에서 smartphone은 온-프레미스 LOB 앱에 데이터 요청을 전송 하는 Azure의 사용자 지정 모바일 앱에 액세스 합니다.</span><span class="sxs-lookup"><span data-stu-id="713c0-138">A smartphone on the Internet accesses the custom mobile app in Azure, which sends data requests to the on-premises LOB app.</span></span>
  
<span data-ttu-id="713c0-139">이 예제 Azure PaaS 하이브리드 응용 프로그램은 직원에 게 최신 연락처 정보를 제공 하는 사용자 지정 모바일 앱입니다.</span><span class="sxs-lookup"><span data-stu-id="713c0-139">This example Azure PaaS hybrid application is a custom mobile app that provides up-to-date contact information on employees.</span></span> <span data-ttu-id="713c0-140">종단 간 하이브리드 시나리오는 다음으로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="713c0-140">The end-to-end hybrid scenario consists of:</span></span>
  
- <span data-ttu-id="713c0-141">유효성을 검사 하 고 실행할 온-프레미스 자격 증명을 확인 해야 하는 smartphone 앱입니다.</span><span class="sxs-lookup"><span data-stu-id="713c0-141">A smartphone app that requires validated, on-premises credentials to run.</span></span>
    
- <span data-ttu-id="713c0-142">사용자의 smartphone 앱에 대 한 쿼리를 기반으로 특정 직원에 대 한 정보를 요청 하는 Azure PaaS에서 실행 되는 사용자 지정 모바일 앱입니다.</span><span class="sxs-lookup"><span data-stu-id="713c0-142">A custom mobile app running in Azure PaaS, which requests information about specific employees based on queries from a user's smartphone app.</span></span>
    
- <span data-ttu-id="713c0-143">DMZ에서 사용자 지정 모바일 앱의 유효성을 검사 하 고 요청을 전달 하는 역방향 프록시 서버입니다.</span><span class="sxs-lookup"><span data-stu-id="713c0-143">A reverse proxy server in the DMZ that validates the custom mobile app and forwards the request.</span></span>
    
- <span data-ttu-id="713c0-144">사용자 계정의 사용 권한에 따라 연락처 요청을 서비스 하는 LOB 응용 프로그램 서버 팜</span><span class="sxs-lookup"><span data-stu-id="713c0-144">An LOB application server farm that services the contact request, subject to the permissions of the user's account.</span></span>
    
<span data-ttu-id="713c0-145">온-프레미스 id 공급자가 Azure AD와 동기화 되었기 때문에 사용자 지정 모바일 앱과 LOB 앱이 모두 요청 하는 사용자의 계정 이름에 대 한 유효성을 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="713c0-145">Because the on-premises identity provider has been synchronized with Azure AD, both the custom mobile app and the LOB app can validate the requesting user's account name.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="713c0-146">참고 항목</span><span class="sxs-lookup"><span data-stu-id="713c0-146">See Also</span></span>

[<span data-ttu-id="713c0-147">Microsoft Hybrid Cloud for Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="713c0-147">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="713c0-148">Microsoft 클라우드 IT 아키텍처 리소스</span><span class="sxs-lookup"><span data-stu-id="713c0-148">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

