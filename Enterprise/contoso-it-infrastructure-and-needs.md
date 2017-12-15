---
title: "Contoso의 IT 인프라 및 필요한"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 5d6a58b8-bec3-4629-9737-8733c7b7ec92
description: "요약: Contoso의 기본 구조는 온-프레미스 IT 인프라 및 방법의 비즈니스 요구 하 여 충족할 수 Microsoft의 클라우드 서비스를 이해 합니다."
ms.openlocfilehash: 98ead7ffa3164c3cd57ec50def836b690881ba63
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2017
---
# <a name="contosos-it-infrastructure-and-needs"></a><span data-ttu-id="34075-103">Contoso의 IT 인프라 및 필요한</span><span class="sxs-lookup"><span data-stu-id="34075-103">Contoso's IT infrastructure and needs</span></span>

 <span data-ttu-id="34075-104">**요약:** Contoso의 기본 구조는 온-프레미스 IT 인프라 및 방법의 비즈니스 요구 하 여 충족할 수 Microsoft의 클라우드 서비스를 이해 합니다.</span><span class="sxs-lookup"><span data-stu-id="34075-104">**Summary:** Understand the basic structure of Contoso's on-premises IT infrastructure and how its business needs can be met by Microsoft's cloud offerings.</span></span>
  
<span data-ttu-id="34075-105">Contoso가 온-프레미스에서 전환, 개인의 생산성 클라우드 기반 작업, 응용 프로그램 및 하이브리드 시나리오를 지 원하는 클라우드 (포함) 하나를 중앙 집중화 된 IT 인프라 관리 하는 중입니다.</span><span class="sxs-lookup"><span data-stu-id="34075-105">Contoso is in the process of transitioning from an on-premises, centralized IT infrastructure to a cloud-inclusive one that incorporates cloud-based personal productivity workloads, applications, and hybrid scenarios.</span></span>
  
## <a name="contosos-existing-it-infrastructure"></a><span data-ttu-id="34075-106">Contoso의 기존 IT 인프라</span><span class="sxs-lookup"><span data-stu-id="34075-106">Contoso's existing IT infrastructure</span></span>

<span data-ttu-id="34075-107">Contoso는 대부분의 중앙 사용 하 여 온-프레미스 파리 본사에서 응용 프로그램 데이터 센터와 IT 인프라 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="34075-107">Contoso uses a mostly centralized on-premises IT infrastructure, with application datacenters in the Paris headquarters.</span></span>
  
<span data-ttu-id="34075-108">**그림 1: Contoso의 기존 IT 인프라 관리**</span><span class="sxs-lookup"><span data-stu-id="34075-108">**Figure 1: Contoso's existing IT infrastructure**</span></span>

![Contoso의 기존 IT 인프라](images/Contoso_Poster/Existing_IT.png)
  
<span data-ttu-id="34075-110">그림 1은 응용 프로그램 데이터 센터, DMZ, 및 인터넷 사용 하 여 중앙 사무소를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="34075-110">Figure 1 shows a headquarters office with application datacenters, a DMZ, and the Internet.</span></span>
  
<span data-ttu-id="34075-111">Contoso의 DMZ에서 서로 다른 서버 집합을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="34075-111">In Contoso's DMZ, different sets of servers provide:</span></span>
  
- <span data-ttu-id="34075-112">파리 본사에서 작업자에 대 한 Contoso 인트라넷 및 웹 프록시에 원격 액세스 합니다.</span><span class="sxs-lookup"><span data-stu-id="34075-112">Remote access to the Contoso intranet and web proxying for workers in the Paris headquarters.</span></span>
    
- <span data-ttu-id="34075-113">Contoso 공용 웹사이트에 대 한 호스팅, 어떤 고객 으로부터 주문할 수 제품, 부품 또는 공급 합니다.</span><span class="sxs-lookup"><span data-stu-id="34075-113">Hosting for the Contoso public web site, from which customers can order products, parts, or supplies.</span></span>
    
- <span data-ttu-id="34075-114">파트너 통신 및 공동 작업에 대 한 엑스트라넷 Contoso 파트너에 대 한 호스팅.</span><span class="sxs-lookup"><span data-stu-id="34075-114">Hosting for the Contoso partner extranet for partner communication and collaboration.</span></span>
    
## <a name="contosos-business-needs"></a><span data-ttu-id="34075-115">Contoso의 비즈니스 요구 사항</span><span class="sxs-lookup"><span data-stu-id="34075-115">Contoso's business needs</span></span>

<span data-ttu-id="34075-116">우선순위에 따라 Contoso의 비즈니스 요구 사항은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="34075-116">Here are Contoso's business needs in priority order:</span></span>
  
1. <span data-ttu-id="34075-117">국가별 규정 요구 사항 준수</span><span class="sxs-lookup"><span data-stu-id="34075-117">Adhere to regional regulatory requirements</span></span>
    
    <span data-ttu-id="34075-118">벌금을 방지 하 고 로컬 정부와 좋은 관계를 유지 관리, 하려면 Contoso 데이터 저장소 및 암호화 규정 준수를 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34075-118">To prevent fines and maintain good relations with local governments, Contoso must ensure compliance with data storage and encryption regulations.</span></span>
    
2. <span data-ttu-id="34075-119">공급 업체와 파트너 관리 개선</span><span class="sxs-lookup"><span data-stu-id="34075-119">Improve vendor and partner management</span></span>
    
    <span data-ttu-id="34075-p101">익스트라넷 파트너 연결 하 고 유지 관리 비용이 매우 많이 됩니다. Contoso는 연결 된 인증을 사용 하는 클라우드 기반 솔루션으로 대체 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="34075-p101">The partner extranet is aging and expensive to maintain. Contoso wants to replace it with a cloud-based solution that uses federated authentication.</span></span>
    
3. <span data-ttu-id="34075-122">모바일 직원 생산성, 장치 관리 및 액세스 향상</span><span class="sxs-lookup"><span data-stu-id="34075-122">Improve mobile workforce productivity, device management, and access</span></span>
    
    <span data-ttu-id="34075-123">Contoso의 모바일 전용 리소스는 확장 하 고 장치 관리 지적 재산 보호 및 리소스에 보다 효율적으로 액세스할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="34075-123">Contoso's mobile-only workforce is expanding and needs device management to ensure intellectual property protection and more efficient access to resources.</span></span>
    
4. <span data-ttu-id="34075-124">원격 액세스 인프라 감소</span><span class="sxs-lookup"><span data-stu-id="34075-124">Reduce remote access infrastructure</span></span>
    
    <span data-ttu-id="34075-125">클라우드로 원격 작업 자가 일반적으로 액세스 되는 리소스를 이동 하 여 Contoso의 원격 액세스 솔루션에 대 한 유지 관리 및 지원 비용을 줄여 비용을 절약할 것입니다.</span><span class="sxs-lookup"><span data-stu-id="34075-125">By moving resources commonly accessed by remote workers to the cloud, Contoso will save money by reducing maintenance and support costs for their remote access solution.</span></span>
    
5. <span data-ttu-id="34075-126">온-프레미스 데이터 센터 아래로 확장</span><span class="sxs-lookup"><span data-stu-id="34075-126">Scale down on-premises datacenters</span></span>
    
    <span data-ttu-id="34075-127">Contoso 데이터 센터 수백 대의 서버, IT 담당자가 높은 비즈니스 값 작업 부하를 유지 관리에서 혼동는 레거시 또는 보관 함수를 실행 하는 중 일부를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="34075-127">The Contoso datacenters contain hundreds of servers, some of which are running legacy or archival functions that distract IT staff from maintaining high business value workloads.</span></span>
    
6. <span data-ttu-id="34075-128">분기의 최종 처리를 위해 수직 확장 컴퓨팅 및 저장소 리소스</span><span class="sxs-lookup"><span data-stu-id="34075-128">Scale-up computing and storage resources for end-of-quarter processing</span></span>
    
    <span data-ttu-id="34075-129">분기의 최종 재무 회계 및 재고 관리와 함께 처리 프로젝션 단기 증가 하면 서버 및 저장소에 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="34075-129">End-of-quarter financial accounting and projection processing along with inventory management requires short-term increases in servers and storage.</span></span>
    
## <a name="mapping-contosos-business-needs-to-microsofts-cloud-offerings"></a><span data-ttu-id="34075-130">Microsoft의 클라우드 서비스에 필요한 Contoso의 비즈니스 매핑 (영문)</span><span class="sxs-lookup"><span data-stu-id="34075-130">Mapping Contoso's business needs to Microsoft's cloud offerings</span></span>

<span data-ttu-id="34075-131">Microsoft의 클라우드 서비스, Contoso의 분석을 바탕의 IT 부서는 다음과 같은 매핑을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="34075-131">Based on an analysis of Microsoft's cloud offerings, Contoso's IT department determined the following mapping:</span></span>
  
|<span data-ttu-id="34075-132">**Software as a Service (SaaS)**</span><span class="sxs-lookup"><span data-stu-id="34075-132">**Software as a Service (SaaS)**</span></span>|<span data-ttu-id="34075-133">**(Azure PaaS) 서비스로 플랫폼**</span><span class="sxs-lookup"><span data-stu-id="34075-133">**Platform as a Service (Azure PaaS )**</span></span>|<span data-ttu-id="34075-134">**As a Service (Azure IaaS) 인프라**</span><span class="sxs-lookup"><span data-stu-id="34075-134">**Infrastructure as a Service (Azure IaaS )**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="34075-135">**Office 365:** 클라우드에서 기본 그룹 및 개인 생산성 응용 프로그램입니다.</span><span class="sxs-lookup"><span data-stu-id="34075-135">**Office 365:** Primary personal and group productivity applications in the cloud.</span></span> <br/> <span data-ttu-id="34075-136">비즈니스 요구 사항: 1 3 5</span><span class="sxs-lookup"><span data-stu-id="34075-136">Business needs: 1 3 5</span></span>  <br/> |<span data-ttu-id="34075-137">판매를 호스트 하 고 문서 및 클라우드 기반 앱을 사용 하 여 정보 시스템을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="34075-137">Host sales and support documents and information systems using cloud-based apps.</span></span>  <br/> <span data-ttu-id="34075-138">비즈니스 요구: 3</span><span class="sxs-lookup"><span data-stu-id="34075-138">Business need: 3</span></span>  <br/> |<span data-ttu-id="34075-139">클라우드 기반 서버에 보관 하 고 레거시 시스템을 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="34075-139">Move archival and legacy systems to cloud-based servers.</span></span>  <br/> <span data-ttu-id="34075-140">비즈니스 요구: 5</span><span class="sxs-lookup"><span data-stu-id="34075-140">Business need: 5</span></span>  <br/> |
|<span data-ttu-id="34075-p102">**Dynamics 365:** 클라우드 기반 고객 및 공급 업체 관리를 사용 합니다. DMZ에 익스트라넷 파트너를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="34075-p102">**Dynamics 365:** Use cloud-based customer and vendor management. Remove partner extranet in the DMZ. </span></span><br/> <span data-ttu-id="34075-143">비즈니스 요구: 2</span><span class="sxs-lookup"><span data-stu-id="34075-143">Business need: 2</span></span>  <br/> |<span data-ttu-id="34075-144">모바일 응용 프로그램은 클라우드 기반 데이터 센터 기반 파리가 아닌 합니다.</span><span class="sxs-lookup"><span data-stu-id="34075-144">Mobile applications are cloud-based, rather than Paris datacenter-based.</span></span>  <br/> <span data-ttu-id="34075-145">비즈니스 요구 사항: 3 4</span><span class="sxs-lookup"><span data-stu-id="34075-145">Business needs: 3 4</span></span>  <br/> |<span data-ttu-id="34075-146">자주 사용 앱 및 온-프레미스 데이터 센터에서 데이터를 마이그레이션하십시오.</span><span class="sxs-lookup"><span data-stu-id="34075-146">Migrate low-use apps and data out of on-premises datacenters.</span></span>  <br/> <span data-ttu-id="34075-147">비즈니스 요구: 5</span><span class="sxs-lookup"><span data-stu-id="34075-147">Business need: 5</span></span>  <br/> |
|<span data-ttu-id="34075-148">**Intune/EMS:** IOS 및 Android 장치를 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="34075-148">**Intune/EMS:** Manage iOS and Android devices.</span></span> <br/> <span data-ttu-id="34075-149">비즈니스 요구: 3</span><span class="sxs-lookup"><span data-stu-id="34075-149">Business need: 3</span></span>  <br/> ||<span data-ttu-id="34075-150">임시 서버 및 분기의 끝 처리 요구 사항에 대 한 저장소를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="34075-150">Add temporary servers and storage for end-of-quarter processing needs.</span></span>  <br/> <span data-ttu-id="34075-151">비즈니스 요구: 6</span><span class="sxs-lookup"><span data-stu-id="34075-151">Business need: 6</span></span>  <br/> |
   
## <a name="see-also"></a><span data-ttu-id="34075-152">See Also</span><span class="sxs-lookup"><span data-stu-id="34075-152">See Also</span></span>

[<span data-ttu-id="34075-153">Microsoft 클라우드 Contoso</span><span class="sxs-lookup"><span data-stu-id="34075-153">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="34075-154">Microsoft 클라우드 IT 아키텍처 리소스</span><span class="sxs-lookup"><span data-stu-id="34075-154">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="34075-155">Microsoft의 엔터프라이즈 클라우드 로드맵: IT 의사 결정권자를 위한 리소스</span><span class="sxs-lookup"><span data-stu-id="34075-155">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)


