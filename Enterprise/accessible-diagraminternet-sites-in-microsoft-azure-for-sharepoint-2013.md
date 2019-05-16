---
title: 액세스 가능한 다이어그램-SharePoint 용 Microsoft Azure 2013의 인터넷 사이트
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 71636974-fb99-487c-ac67-f15e9401acba
description: 이 문서는 SharePoint 2013 용 Microsoft Azure의 인터넷 사이트 라는 액세스 가능한 텍스트 버전입니다.
ms.openlocfilehash: 1d18ad73502c7e21c1c0825e3e56e4faac2a4a09
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068644"
---
# <a name="accessible-diagram---internet-sites-in-microsoft-azure-for-sharepoint-2013"></a><span data-ttu-id="807b8-103">액세스 가능한 다이어그램-SharePoint 용 Microsoft Azure 2013의 인터넷 사이트</span><span class="sxs-lookup"><span data-stu-id="807b8-103">Accessible diagram - Internet sites in Microsoft Azure for SharePoint 2013</span></span>

<span data-ttu-id="807b8-104">**요약:** 이 문서는 SharePoint 2013 용 Microsoft Azure의 인터넷 사이트 라는 액세스 가능한 텍스트 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-104">**Summary:** This article is an accessible text version of the diagram named Internet sites in Microsoft Azure for SharePoint 2013.</span></span>
  
<span data-ttu-id="807b8-105">이 포스터에서는 공용 연결 인터넷 사이트에서 클라우드 회복 력 및 고객 계정의 Azure AD를 활용 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-105">This poster describes and illustrates how public-facing Internet sites benefit from cloud elasticity and Azure AD for customer accounts.</span></span> <span data-ttu-id="807b8-106">Azure에서 제공 하는 인터넷 사이트의 이점에 대해 설명 하는 6 가지 시나리오가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-106">There are six different scenarios that describe how Internet sites benefit from Azure:</span></span> 
  
- <span data-ttu-id="807b8-107">팜 토폴로지를 디자인 하 고 크기를 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-107">Design and size the farm topology.</span></span> 
    
- <span data-ttu-id="807b8-108">Azure에 대 한 미세 조정</span><span class="sxs-lookup"><span data-stu-id="807b8-108">Fine-tune for Azure.</span></span> 
    
- <span data-ttu-id="807b8-109">Active Directory 모델을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-109">Choose the Active Directory model.</span></span> 
    
- <span data-ttu-id="807b8-110">Id 관리, 영역 및 인증을 위한 디자인</span><span class="sxs-lookup"><span data-stu-id="807b8-110">Design for identity management, zones, and authentication.</span></span> 
    
- <span data-ttu-id="807b8-111">교차 사이트 게시용 사이트 및 Url을 디자인 합니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-111">Design sites and URLs for cross-site publishing.</span></span> 
    
- <span data-ttu-id="807b8-112">Azure 환경을 디자인 합니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-112">Design the Azure environment.</span></span> 
    
## <a name="design-and-size-the-farm-topology"></a><span data-ttu-id="807b8-113">팜 토폴로지 디자인 및 크기 조정</span><span class="sxs-lookup"><span data-stu-id="807b8-113">Design and size the farm topology</span></span>

<span data-ttu-id="807b8-114">TechNet의 SharePoint 2013에 대 한 토폴로지, 용량 및 성능 지침을 사용 하 여 팜 토폴로지를 디자인 합니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-114">Use the topology, capacity, and performance guidance for SharePoint 2013 on TechNet to design the farm topology.</span></span> 
  
<span data-ttu-id="807b8-115">디자인 한 팜이 용량 및 성능에 대 한 목표를 충족 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-115">Ensure the farm you design meets the objectives for capacity and performance.</span></span> 
  
### <a name="example-medium-internet-sites-farm-85-page-views-per-second"></a><span data-ttu-id="807b8-116">예: 중간 규모 인터넷 사이트 팜 (초당 ~ 85 페이지 보기)</span><span class="sxs-lookup"><span data-stu-id="807b8-116">Example: Medium Internet Sites farm (~85 page views per second)</span></span>

<span data-ttu-id="807b8-117">이 팜은 340만 항목을 포함 하는 모음에 최적화 된 내결함성 SharePoint 2013 search farm 토폴로지를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-117">This farm provides a fault-tolerant SharePoint 2013 search farm topology that is optimized for a corpus that contains 3,400,000 items.</span></span> 
  
<span data-ttu-id="807b8-118">예제 팜은 언어에 따라 초당 100-200 문서를 처리 하 고 초당 85 페이지 보기와 초당 100 쿼리를 수용 합니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-118">The example farm processes 100-200 documents per second, depending on the language, and it accommodates 85 page views per second and 100 queries per second.</span></span> 
  
<span data-ttu-id="807b8-119">다음 다이어그램에는 세 가지 유형의 서버가 있는 중간 규모의 인터넷 사이트 팜이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-119">The accompanying diagram shows a medium internet sites farm with three types of servers:</span></span> 
  
- <span data-ttu-id="807b8-120">웹 서버</span><span class="sxs-lookup"><span data-stu-id="807b8-120">Web servers</span></span> 
    
- <span data-ttu-id="807b8-121">응용 프로그램 서버</span><span class="sxs-lookup"><span data-stu-id="807b8-121">Application servers</span></span> 
    
- <span data-ttu-id="807b8-122">데이터베이스 서버</span><span class="sxs-lookup"><span data-stu-id="807b8-122">Database servers</span></span> 
    
#### <a name="web-servers"></a><span data-ttu-id="807b8-123">웹 서버</span><span class="sxs-lookup"><span data-stu-id="807b8-123">Web servers</span></span>

<span data-ttu-id="807b8-124">웹 서버 섹션에는 호스트 A, 호스트 B 및 호스트 C의 세 가지 웹 서버가 있습니다. 각 웹 서버에는 분산 캐시, 사용자 프로필, 관리 되는 메타 데이터 및 쿼리 처리 기능이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-124">In the web servers section, there are three web servers, Host A, Host B, and Host C. Each web server contains a distributed cache, user profiles, managed metadata, and query processing capabilities.</span></span> <span data-ttu-id="807b8-125">각 서버에 있는 인덱스 파티션 복제 데이터베이스도 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-125">They also contain an index partition replica that is in each server.</span></span> 
  
<span data-ttu-id="807b8-126">수평 확장 하려면 다음의 추가 28 페이지 보기를 허용 하는 동일한 기능을 사용 하 여 추가 웹 서버를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-126">To scale out, add an additional web server with the same capabilities, which allows for an additional 28 page views per second.</span></span> 
  
#### <a name="application-servers"></a><span data-ttu-id="807b8-127">응용 프로그램 서버</span><span class="sxs-lookup"><span data-stu-id="807b8-127">Application servers</span></span>

<span data-ttu-id="807b8-128">응용 프로그램 서버 섹션에는 3 개의 응용 프로그램 서버 (호스트 D, 호스트 E 및 호스트 F)가 있습니다. 호스트 D에는 크롤링, 관리, 분석 및 콘텐츠 처리 구성 요소가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-128">In the application servers section, there are three application servers, Host D, Host E, and Host F. Host D contains Crawl, Admin, Analytics, and Content processing components.</span></span> <span data-ttu-id="807b8-129">호스트 E에는 크롤링, 관리 및 콘텐츠 처리 구성 요소가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-129">Host E contains Crawl, Admin, and Content processing components.</span></span> <span data-ttu-id="807b8-130">호스트 F에는 크롤링 및 콘텐츠 처리 구성 요소가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-130">Host F contains Crawl and Content processing components.</span></span> 
  
<span data-ttu-id="807b8-131">수평 확장 하려면 크롤링 구성 요소가 포함 된 응용 프로그램 서버 한 대와 콘텐츠 처리 구성 요소를 추가 하 여 초당 추가 40 문서를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-131">To scale out, add one application server with a crawl component and a content processing component to process an additional 40 documents per second.</span></span> 
  
#### <a name="database-servers"></a><span data-ttu-id="807b8-132">데이터베이스 서버</span><span class="sxs-lookup"><span data-stu-id="807b8-132">Database servers</span></span>

<span data-ttu-id="807b8-133">데이터베이스 서버 섹션에는 호스트 G와 호스트 H의 두 서버가 있습니다. 데이터베이스 서버는 내결함성을 위한 쌍을 이룬 호스트에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-133">In the database servers section, there are two servers, Host G and Host H. The database servers are in paired hosts for fault tolerance.</span></span> 
  
<span data-ttu-id="807b8-134">호스트 G에는 검색 관리 데이터베이스, 링크 데이터베이스, 두 개의 크롤링 데이터베이스, 분석 데이터베이스 및 기타 모든 SharePoint 데이터베이스를 비롯 한 모든 SharePoint 데이터베이스가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-134">Host G contains all SharePoint database, including Search admin database, Link database, two Crawl databases, an Analytics database, and all other SharePoint databases.</span></span> <span data-ttu-id="807b8-135">호스트 H에는 SQL 클러스터링, 미러링 또는 SQL Server 2012 AlwaysOn을 사용 하 여 모든 데이터베이스의 중복 복사본을 포함 하 여 모든 SharePoint 데이터베이스가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-135">Host H contains all SharePoint databases, including redundant copies of all databases using SQL clustering, mirroring, or SQL Server 2012 AlwaysOn.</span></span> 
  
## <a name="fine-tune-for-azure"></a><span data-ttu-id="807b8-136">Azure에 대 한 미세 조정</span><span class="sxs-lookup"><span data-stu-id="807b8-136">Fine-tune for Azure</span></span>

<span data-ttu-id="807b8-137">Azure 플랫폼에서 가용성 집합에 맞게 SharePoint 팜을 미세 조정 해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-137">The SharePoint farm might need to be fine-tuned for availability sets in the Azure platform.</span></span> <span data-ttu-id="807b8-138">모든 구성 요소의 고가용성을 보장 하려면 서버 역할이 모두 동일 하 게 구성 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-138">To ensure high availability of all components, ensure that the server roles are all identically configured.</span></span> 
  
<span data-ttu-id="807b8-139">다이어그램의 예제 토폴로지:</span><span class="sxs-lookup"><span data-stu-id="807b8-139">In the example topology in the diagram:</span></span> 
  
- <span data-ttu-id="807b8-140">웹 서버와 데이터베이스 서버는 동일 하 게 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-140">The web servers and the database servers are identically configured.</span></span> 
    
- <span data-ttu-id="807b8-141">세 응용 프로그램 서버가 동일 하 게 구성 되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-141">The three application servers are not identically configured.</span></span> <span data-ttu-id="807b8-142">이러한 서버 역할을 사용 하려면 Azure의 가용성 집합에 대 한 미세 조정이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-142">These server roles require fine tuning for availability sets in Azure.</span></span> 
    
### <a name="before"></a><span data-ttu-id="807b8-143">Before</span><span class="sxs-lookup"><span data-stu-id="807b8-143">Before</span></span>

<span data-ttu-id="807b8-144">다이어그램 윗부분에는 Azure의 가용성 집합에 대해 미세 조정 되기 전에 SharePoint 팜이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-144">The top portion of the diagram shows the SharePoint farm before it has been fine-tuned for availability sets in Azure.</span></span> <span data-ttu-id="807b8-145">다이어그램에서 세 개의 호스트 응용 프로그램 서버가 동일 하 게 구성 되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-145">In the diagram, the three host application servers are not identically configured.</span></span> <span data-ttu-id="807b8-146">구성 요소 수는 팜의 성능 및 용량 목표에 따라 결정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-146">The number of components is determined by the performance and capacity targets for the farm.</span></span> <span data-ttu-id="807b8-147">세 서버는 다음과 같이 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-147">The three servers are configured as follows:</span></span> 
  
- <span data-ttu-id="807b8-148">호스트 D 응용 프로그램 서버는 크롤링, 관리, 분석 및 콘텐츠 처리 역할로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-148">Host D application server is configured with Crawl, Admin, Analytics, and Content processing roles.</span></span> 
    
- <span data-ttu-id="807b8-149">호스트 E 응용 프로그램 서버는 크롤링, 관리자 및 콘텐츠 처리 역할로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-149">Host E application server is configured with Crawl, Admin, and Content processing roles.</span></span> 
    
- <span data-ttu-id="807b8-150">호스트 F 응용 프로그램 서버는 크롤링 및 콘텐츠 처리 역할로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-150">Host F application server is configured with Crawl and Content processing roles.</span></span> 
    
### <a name="after"></a><span data-ttu-id="807b8-151">마치면</span><span class="sxs-lookup"><span data-stu-id="807b8-151">After</span></span>

<span data-ttu-id="807b8-152">이 다이어그램의 부분에는 Azure의 가용성 집합에 대해 미세 조정 된 SharePoint 팜이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-152">This part of the diagram shows the SharePoint farm after it has been fine-tuned for availability sets in Azure.</span></span> <span data-ttu-id="807b8-153">Azure에 대해이 아키텍처를 조정 하기 위해 3 대의 모든 서버에서 네 개의 구성 요소를 복제 합니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-153">To adapt this architecture for Azure, we'll replicate the four components across all three servers.</span></span> <span data-ttu-id="807b8-154">이렇게 하면 성능 및 용량에 필요한 구성 요소의 수가 늘어납니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-154">This increases the number of components beyond what is necessary for performance and capacity.</span></span> <span data-ttu-id="807b8-155">이러한 단점은 이러한 세 가지 가상 컴퓨터가 가용성 집합에 할당 될 때 Azure 플랫폼에 있는 네 가지 구성 요소의 고가용성을 보장 한다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-155">The tradeoff is that this design ensures high availability of all four components in the Azure platform when these three virtual machines are assigned to an availability set.</span></span> 
  
<span data-ttu-id="807b8-156">세 서버는 모두 크롤링, 관리, 분석 및 콘텐츠 처리 역할을 갖도록 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-156">The three servers are configured to all have the Crawl, Admin, Analytics, and Content processing roles.</span></span> 
  
## <a name="choose-the-active-directory-model"></a><span data-ttu-id="807b8-157">Active Directory 모델 선택</span><span class="sxs-lookup"><span data-stu-id="807b8-157">Choose the Active Directory model</span></span>

<span data-ttu-id="807b8-158">모든 SharePoint 솔루션에는 Windows AD DS (Active Directory 도메인 서비스)가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-158">All SharePoint solutions require Windows Active Directory Domain Services (AD DS).</span></span> <span data-ttu-id="807b8-159">현재 Azure의 SharePoint 솔루션에는 두 가지 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-159">At this time, there are two options for SharePoint solutions in Azure.</span></span> 
  
- <span data-ttu-id="807b8-160">옵션 1: 전용 도메인-SharePoint 팜을 지원 하기 위해 Azure에 전용 및 격리 된 도메인을 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-160">Option 1: Dedicated domain — You can deploy a dedicated and isolated domain to Azure to support a SharePoint farm.</span></span> <span data-ttu-id="807b8-161">이 옵션은 공용 인터넷 사이트에 적합 합니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-161">This is a good choice for public-facing Internet sites.</span></span> 
    
- <span data-ttu-id="807b8-162">옵션 2: 사이트 간 VPN 연결을 통해 온-프레미스 도메인을 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-162">Option 2: Extend the on-premises domain through a site-to-site VPN connection.</span></span> <span data-ttu-id="807b8-163">사이트 간 VPN 연결을 통해 온-프레미스 도메인을 확장 하면 사용자는 온-프레미스에 호스트 된 것 처럼 SharePoint 팜에 액세스 합니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-163">When you extend the on-premises domain through a site-to-site VPN connection, users access the SharePoint farm as if it were hosted on-premises.</span></span> <span data-ttu-id="807b8-164">기존 Active Directory 및 DNS 구현을 활용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-164">You can take advantage of your existing Active Directory and DNS implementations.</span></span> 
    
## <a name="design-for-identity-management-zones-and-authentication"></a><span data-ttu-id="807b8-165">Id 관리, 영역 및 인증을 위한 디자인</span><span class="sxs-lookup"><span data-stu-id="807b8-165">Design for identity management, zones, and authentication</span></span>

### <a name="design-for-accounts-and-authentication"></a><span data-ttu-id="807b8-166">계정 및 인증에 대 한 디자인</span><span class="sxs-lookup"><span data-stu-id="807b8-166">Design for accounts and authentication</span></span>

<span data-ttu-id="807b8-167">계정을 관리 하는 방법 및 사용 되는 인증 유형을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-167">Determine how accounts will be managed and which type of authentication will be used.</span></span> 
  
#### <a name="accounts-for-site-developers-and-authors"></a><span data-ttu-id="807b8-168">사이트 개발자 및 제작자를 위한 계정</span><span class="sxs-lookup"><span data-stu-id="807b8-168">Accounts for site developers and authors</span></span>

- <span data-ttu-id="807b8-169">Azure의 도메인에 계정을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-169">Add accounts to the domain in Azure.</span></span> 
    
- <span data-ttu-id="807b8-170">온-프레미스 AD FS (Active Directory Federation Services)를 사용 하 여 내부 계정을 Azure의 도메인에 페더레이션 합니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-170">Use Active Directory Federation Services (AD FS) on premises to federate the internal accounts to the domain in Azure.</span></span> 
    
- <span data-ttu-id="807b8-171">디자인에 사이트 간 VPN 연결이 포함 되어 있으면 내부 계정을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-171">If the design includes a site-to-site VPN connection, use the internal accounts.</span></span> 
    
#### <a name="accounts-for-customers"></a><span data-ttu-id="807b8-172">고객을 위한 계정</span><span class="sxs-lookup"><span data-stu-id="807b8-172">Accounts for customers</span></span>

- <span data-ttu-id="807b8-173">Azure Active Directory를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-173">Use Azure Active Directory.</span></span> 
    
- <span data-ttu-id="807b8-174">다른 SAML 기반 공급자를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-174">Use a different SAML-based provider.</span></span> 
    
### <a name="design-for-zones"></a><span data-ttu-id="807b8-175">영역 디자인</span><span class="sxs-lookup"><span data-stu-id="807b8-175">Design for zones</span></span>

<span data-ttu-id="807b8-176">SharePoint 2013에서 id 관리는 영역 및 인증 구성에 대 한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-176">In SharePoint 2013, identity management is factored into the configuration of zones and authentication.</span></span> 
  
<span data-ttu-id="807b8-177">이 디자인을 통해 다른 모든 계정과 고객 계정을 명확 하 게 분리할 수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-177">This design provides clear separation of customer accounts from all other accounts.</span></span> 
  
- <span data-ttu-id="807b8-178">고객 계정을 작성자 및 사이트 개발자를 위한 내부 계정과 완전히 다른 것으로 간주 하려면이 디자인을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-178">Use this design if you want customer accounts to be treated entirely different from the internal accounts for authors and site developers.</span></span> 
    
- <span data-ttu-id="807b8-179">이 디자인을 사용 하 여 영역 정책을 사용 하 여 웹 응용 프로그램 내에서 고객 작업을 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-179">By using this design, you can use zone policies to limit customer actions within a web application.</span></span> 
    
- <span data-ttu-id="807b8-180">이 디자인은 고객 계정 및 내부 계정에 대해 서로 다른 Url을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-180">This design results in different URLs for customer accounts and internal accounts.</span></span> 
    
<span data-ttu-id="807b8-181">이 예제의 특징은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-181">In this example:</span></span> 
  
- <span data-ttu-id="807b8-182">내부 계정의 기본 영역을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-182">Configure the default zone for internal accounts.</span></span> 
    
- <span data-ttu-id="807b8-183">고객 인증 액세스를 위한 엑스트라넷 영역을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-183">Configure the extranet zone for customer authenticated access.</span></span> <span data-ttu-id="807b8-184">고객 계정에 대해 Azure Active Directory (AD)를 사용 하거나 다른 SAML 기반 공급자를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-184">Use Azure Active Directory (AD) for customer accounts, or use a different SAML-based provider.</span></span> 
    
- <span data-ttu-id="807b8-185">익명 액세스를 사용 하도록 인터넷 영역을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-185">Configure the Internet zone for anonymous access.</span></span> 
    
<span data-ttu-id="807b8-186">인증 된 모든 사용자가 기본 영역을 사용 하도록 구성 되어 있는 두 영역 디자인을 사용 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="807b8-186">Don't use a two-zone design in which all authenticated users are configured to use the default zone.</span></span> 
  
<span data-ttu-id="807b8-187">함께 제공 되는 다이어그램에서는 내부 및 고객 계정이 분리 된 3 영역 디자인을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-187">The accompanying diagram shows a three-zone design with separation of internal and customer accounts.</span></span> 
  
<span data-ttu-id="807b8-188">방문자 및 고객은 두 영역 중 하나에서 웹 응용 프로그램을 통해 SharePoint 2013 팜의 Azure AD 테 넌 트에 액세스 합니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-188">Visitors and customers access the Azure AD Tenant in the SharePoint 2013 farm through web applications in one of two zones.</span></span> <span data-ttu-id="807b8-189">두 영역에는 다음이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-189">The two zones include:</span></span> 
  
- <span data-ttu-id="807b8-190">영역: 익명 사용자의 인터넷</span><span class="sxs-lookup"><span data-stu-id="807b8-190">Zone: Internet for anonymous users</span></span> 
    
- <span data-ttu-id="807b8-191">영역: 인증 된 사용자에 대 한 엑스트라넷</span><span class="sxs-lookup"><span data-stu-id="807b8-191">Zone: Extranet for authenticated users</span></span> 
    
<span data-ttu-id="807b8-192">내부 계정이 있는 사용자는 Azure AD에 대 한 VPN 터널을 통해 온-프레미스 환경에서 AD DS 및 AD FS의 Azure Active Directory 테 넌 트에 액세스 합니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-192">Users with internal accounts access the Azure Active Directory Tenant from AD DS and AD FS in the on-premises environment through the VPN tunnel to Azure AD.</span></span> <span data-ttu-id="807b8-193">기본 영역은 Windows 인증 (NTLM)을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-193">The Default zone provides Windows Authentication (NTLM).</span></span> 
  
### <a name="design-for-connecting-to-azure-ad"></a><span data-ttu-id="807b8-194">Azure AD에 연결 하기 위한 디자인</span><span class="sxs-lookup"><span data-stu-id="807b8-194">Design for connecting to Azure AD</span></span>

 <span data-ttu-id="807b8-195">Azure AD는 클라우드 서비스에 대 한 id 관리 및 액세스 제어 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-195">Azure AD provides identity management and access control capabilities for cloud services.</span></span> <span data-ttu-id="807b8-196">기능에는 디렉터리 데이터를 위한 클라우드 기반 저장소와 사용자 로그온 프로세스, 인증 서비스 및 AD FS 등의 핵심 id 서비스가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-196">Capabilities include a cloud-based store for directory data and a core set of identity services, including user logon processes, authentication services, and AD FS.</span></span> <span data-ttu-id="807b8-197">Azure AD에 포함 된 id 서비스는 온-프레미스 AD DS 배포와 쉽게 통합 되며 타사 id 공급자를 완벽 하 게 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-197">The identity services that are included with Azure AD easily integrate with your on-premises AD DS deployments and fully support third-party identity providers.</span></span>
  
<span data-ttu-id="807b8-198">함께 제공 되는 다이어그램에서는 다음과 같은 시나리오를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-198">The accompanying diagram shows the following scenario:</span></span> 
  
<span data-ttu-id="807b8-199">Azure Active Directory와 함께 SharePoint 2013을 통합 하는 경우에는 ACS (액세스 제어 서비스)가 다음과 같은 두 가지 용도로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-199">When integrating SharePoint 2013 with Azure Active Directory, an Azure Access Control Service (ACS) serves two purposes:</span></span> 
  
-  <span data-ttu-id="807b8-200">Azure AD는 SAML 2.0을 사용 하며, SharePoint는 SAML 1.1 에서만 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-200">Azure AD uses SAML 2.0, and SharePoint only works with SAML 1.1.</span></span> <span data-ttu-id="807b8-201">ACS는 두 가지 형식을 모두 이해 하 고 SharePoint 및 Azure AD 간에 토큰 형식을 변환 하기 위한 중개 역할을 합니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-201">ACS understands both formats and serves as the intermediary to transform the token formats between SharePoint and Azure AD.</span></span>
    
- <span data-ttu-id="807b8-202">ACS는이 SAML 시나리오에 대해 id 공급자 STS (security token service)에 대 한 요구를 대체 합니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-202">ACS replaces the need for the identity provider security token service (IP-STS) for this SAML scenario.</span></span> 
    
<span data-ttu-id="807b8-203">자세한 내용은 TechNet 라이브러리에서 SharePoint 2013을 사용 하 여 Azure AD 구성를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="807b8-203">For more information, see Configure Azure AD with SharePoint 2013 in the TechNet library.</span></span> 
  
## <a name="design-sites-and-urls-for-cross-site-publishing"></a><span data-ttu-id="807b8-204">교차 사이트 게시용 사이트 및 Url 디자인</span><span class="sxs-lookup"><span data-stu-id="807b8-204">Design sites and URLs for cross-site publishing</span></span>

<span data-ttu-id="807b8-205">게시 시나리오에는 하나의 웹 응용 프로그램 디자인을 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-205">A one web-application design is recommended for publishing scenarios.</span></span> 
  
- <span data-ttu-id="807b8-206">두 제작 사이트와 게시 사이트가 같은 웹 응용 프로그램에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-206">Both authoring and publishing sites are in the same web application.</span></span> 
    
- <span data-ttu-id="807b8-207">교차 사이트 게시는 자산을 게시 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-207">Cross-site publishing is used to publish assets.</span></span> 
    
<span data-ttu-id="807b8-208">경로 기반 및 호스트 이름으로 된 사이트 모음을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-208">Use path-based and host-named site collections.</span></span> 
  
- <span data-ttu-id="807b8-209">루트 사이트 모음은 필수 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-209">A root site collection is a requirement.</span></span> <span data-ttu-id="807b8-210">이 사이트를 경로 기반 사이트로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-210">Create this site as a path-based site.</span></span> 
    
- <span data-ttu-id="807b8-211">다른 모든 사이트 모음을 호스트 이름으로 된 사이트 모음으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-211">Create all other site collections as host-named site collections.</span></span> 
    
<span data-ttu-id="807b8-212">웹 응용 프로그램 및 루트 사이트 Url</span><span class="sxs-lookup"><span data-stu-id="807b8-212">Web application and root site URLs</span></span> 
  
- <span data-ttu-id="807b8-213">웹 응용 프로그램 URL에 내부 이름을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-213">Use an internal name for the web application URL.</span></span> <span data-ttu-id="807b8-214">다른 이름이 지정 되지 않은 경우 SharePoint에서 로컬 컴퓨터 이름을 기본 이름으로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-214">SharePoint uses the local machine name as the default name unless a different name is specified.</span></span> <span data-ttu-id="807b8-215">내부 네트워크 환경에 예약 된 도메인 이름을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-215">You can use a domain name that is reserved for the internal network environment.</span></span> 
    
- <span data-ttu-id="807b8-216">SharePoint는 웹 응용 프로그램을 만들 때 비표준 포트 번호를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-216">SharePoint assigns a nonstandard port number when the web application is created.</span></span> <span data-ttu-id="807b8-217">포트 80 또는 포트 443 대신이 포트 번호를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-217">Use this port number instead of port 80 or port 443.</span></span> <span data-ttu-id="807b8-218">또는 다른 비표준 포트 번호를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-218">Or use a different but nonstandard port number.</span></span> 
    
- <span data-ttu-id="807b8-219">루트 사이트 모음에는 경로 기반 사이트 모음에 해당 하는 이름과 포트 번호를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-219">Use the same name and port number for the root site collection, which is a path-based site collection.</span></span> 
    
<span data-ttu-id="807b8-220">함께 제공 되는 다이어그램은 웹 응용 프로그램을 사용 하 여 사이트 모음과 상호 작용 하는 검색 같은 응용 프로그램 풀 서비스를 보여줍니다</span><span class="sxs-lookup"><span data-stu-id="807b8-220">The accompanying diagram shows application pool services such as Search interacting with site collections using web applications.</span></span> <span data-ttu-id="807b8-221">다음과 같은 사이트 모음이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-221">The site collections shown include:</span></span> 
  
- <span data-ttu-id="807b8-222">(루트 사이트)에 http://internal:8000 있는 경로 기반 사이트 모음입니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-222">Path-based site collection located at http://internal:8000 (root site).</span></span> 
    
- <span data-ttu-id="807b8-223">크롤링:와 같은 주소에 있는 호스트 이름으로 https://authoring.contoso.com:8000된 사이트 모음입니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-223">Crawl: Host-named site collections located at an address such as https://authoring.contoso.com:8000.</span></span> 
    
- <span data-ttu-id="807b8-224">쿼리: 2 주소에 있는 별도의 호스트 이름이 지정 된 사이트 모음:</span><span class="sxs-lookup"><span data-stu-id="807b8-224">Queries: 2 separate Host-named site collections located at addresses such as:</span></span> 
    
  - http://www.contoso.com 
    
  - https://secure.contoso.com 
    
  - http://www.contoso.com:8000 
    
  - http://assets.contoso.com 
    
  - https://secureassets.contoso.com 
    
  - http://assets.contoso.com:8000 
    
## <a name="design-the-azure-environment"></a><span data-ttu-id="807b8-225">Azure 환경 디자인</span><span class="sxs-lookup"><span data-stu-id="807b8-225">Design the Azure environment</span></span>

<span data-ttu-id="807b8-226">이 예제 아키텍처에는 다음과 같은 요소가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-226">This example architecture includes the following elements:</span></span> 
  
- <span data-ttu-id="807b8-227">사이트 간 VPN 연결은 선택 사항이 며 온-프레미스 Windows AD DS 및 DNS 환경을 Azure의 가상 네트워크로 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-227">A site-to-site VPN connection is optional and extends the on-premises Windows AD DS and DNS environment to the virtual network in Azure.</span></span> 
    
- <span data-ttu-id="807b8-228">필요한 경우 Azure에서 전용 도메인을 사용 하 여 SharePoint 팜을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-228">Optionally, use a dedicated domain in Azure to support the SharePoint farm.</span></span> 
    
- <span data-ttu-id="807b8-229">서버는 역할에 따라 Azure 클라우드 서비스 간에 분할 됩니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-229">Servers are split across Azure cloud services based on role.</span></span> 
    
- <span data-ttu-id="807b8-230">가용성 집합은 동일 하 게 구성 된 서버 역할의 고가용성을 보장 합니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-230">Availability sets ensure high availability of identically configured server roles.</span></span> 
    
<span data-ttu-id="807b8-231">자세한 내용은 TechNet: Azure 아키텍처 for SharePoint 솔루션용의 다음 문서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="807b8-231">For more information, see the following article on TechNet: Azure Architectures for SharePoint Solutions.</span></span> 
  
<span data-ttu-id="807b8-232">함께 제공 되는 다이어그램에는 Azure virtual network와 연결 되는 온-프레미스 환경의 예가 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-232">The accompanying diagram shows an example of an on-premises environment connecting with an Azure virtual network.</span></span> 
  
<span data-ttu-id="807b8-233">Azure 환경의 선택적 요소인 온-프레미스 환경에는 다음과 같은 구성 요소가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-233">Included in the on-premises environment, which is an optional element of the Azure environment, are the following components:</span></span> 
  
- <span data-ttu-id="807b8-234">Windows Server 2012 RRAS</span><span class="sxs-lookup"><span data-stu-id="807b8-234">Windows Server 2012 RRAS</span></span> 
    
- <span data-ttu-id="807b8-235">AD DS</span><span class="sxs-lookup"><span data-stu-id="807b8-235">AD DS</span></span> 
    
- <span data-ttu-id="807b8-236">Windows Server 및 AD DS에서 활성 VPN 게이트웨이 서브넷으로의 VPN 게이트웨이</span><span class="sxs-lookup"><span data-stu-id="807b8-236">A VPN gateway from Windows Server and AD DS to the Active VPN Gateway subnet</span></span> 
    
<span data-ttu-id="807b8-237">Azure virtual network 환경에는 다음과 같은 구성 요소가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="807b8-237">The Azure virtual network environment includes the following components:</span></span> 
  
- <span data-ttu-id="807b8-238">활성 VPN 게이트웨이 서브넷 (해당 하는 경우 온-프레미스 환경과 겹칩니다)</span><span class="sxs-lookup"><span data-stu-id="807b8-238">The Active VPN Gateway subnet (overlapping with the on-premises environment, if applicable)</span></span> 
    
- <span data-ttu-id="807b8-239">AD DS 및 DNS 가용성 집합을 포함 하는 클라우드 서비스 (서버 2 대)</span><span class="sxs-lookup"><span data-stu-id="807b8-239">Cloud service that includes AD DS and DNS availability set (two servers)</span></span> 
    
- <span data-ttu-id="807b8-240">프런트 엔드 서버 가용성 집합 (SharePoint 서버 3 대) 및 앱 서버 가용성 집합 (3 개의 SharePoint 서버)이 포함 된 클라우드 서비스</span><span class="sxs-lookup"><span data-stu-id="807b8-240">Cloud service that include the front-end server availability set (three SharePoint servers) and the App server availability set (three SharePoint servers)</span></span> 
    
- <span data-ttu-id="807b8-241">두 개의 데이터베이스 사용 가능 집합이 포함 된 클라우드 서비스</span><span class="sxs-lookup"><span data-stu-id="807b8-241">Cloud service that contains two database availability sets</span></span> 
    

