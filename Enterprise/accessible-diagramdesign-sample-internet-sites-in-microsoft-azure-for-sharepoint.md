---
title: 액세스 가능한 다이어그램-SharePoint 용 Microsoft Azure 2013의 예제 인터넷 사이트 디자인
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.collection: Ent_O365
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b91124bc-c7ec-4929-b77c-d6293db9f15e
description: '이 문서는 Design sample: SharePoint 용 Microsoft Azure 2013의 Internet sites 라는 액세스 가능한 텍스트 버전입니다.'
ms.openlocfilehash: 0d42a96f80d47b360084557fea47c4155d106d30
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487834"
---
# <a name="accessible-diagram---design-sample-internet-sites-in-microsoft-azure-for-sharepoint-2013"></a><span data-ttu-id="aa9f5-103">액세스 가능한 다이어그램-디자인 샘플: SharePoint 용 Microsoft Azure 2013의 인터넷 사이트</span><span class="sxs-lookup"><span data-stu-id="aa9f5-103">Accessible diagram - Design sample: Internet sites in Microsoft Azure for SharePoint 2013</span></span>

<span data-ttu-id="aa9f5-104">**요약:** 이 문서는 Design sample: SharePoint 용 Microsoft Azure 2013의 Internet sites 라는 액세스 가능한 텍스트 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="aa9f5-104">**Summary:** This article is an accessible text version of the diagram named Design sample: Internet sites in Microsoft Azure for SharePoint 2013.</span></span>
  
<span data-ttu-id="aa9f5-105">이 디자인 예제를 Azure에서 SharePoint 2013을 사용 하는 인터넷 연결 사이트의 시작 지점으로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa9f5-105">Use this design example as a starting point for an Internet-facing site in Azure using SharePoint 2013.</span></span>
  
<span data-ttu-id="aa9f5-106">이 포스터는 SharePoint 2013의 다음과 같은 측면을 디자인 하는 방법의 예를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="aa9f5-106">This poster shows an example of how to design the following aspects of SharePoint 2013:</span></span>
  
- <span data-ttu-id="aa9f5-107">사용자</span><span class="sxs-lookup"><span data-stu-id="aa9f5-107">Users</span></span>
    
- <span data-ttu-id="aa9f5-108">영역 및 인증</span><span class="sxs-lookup"><span data-stu-id="aa9f5-108">Zones and authentication</span></span>
    
- <span data-ttu-id="aa9f5-109">서버 팜</span><span class="sxs-lookup"><span data-stu-id="aa9f5-109">Server farm</span></span>
    
- <span data-ttu-id="aa9f5-110">관리 사이트</span><span class="sxs-lookup"><span data-stu-id="aa9f5-110">Administration site</span></span>
    
- <span data-ttu-id="aa9f5-111">서비스</span><span class="sxs-lookup"><span data-stu-id="aa9f5-111">Services</span></span>
    
- <span data-ttu-id="aa9f5-112">응용 프로그램 풀 및 웹 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="aa9f5-112">Application pools and web applications</span></span>
    
- <span data-ttu-id="aa9f5-113">사이트 모음</span><span class="sxs-lookup"><span data-stu-id="aa9f5-113">Site collections</span></span>
    
- <span data-ttu-id="aa9f5-114">사이트</span><span class="sxs-lookup"><span data-stu-id="aa9f5-114">Sites</span></span>
    
- <span data-ttu-id="aa9f5-115">콘텐츠 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="aa9f5-115">Content databases</span></span>
    
- <span data-ttu-id="aa9f5-116">영역 및 URL</span><span class="sxs-lookup"><span data-stu-id="aa9f5-116">Zones and URLs</span></span>
    
## <a name="users-zones-and-authentication"></a><span data-ttu-id="aa9f5-117">사용자, 영역 및 인증</span><span class="sxs-lookup"><span data-stu-id="aa9f5-117">Users, zones and authentication</span></span>

<span data-ttu-id="aa9f5-118">이 디자인에는 다음과 같은 네 가지 유형의 사용자 계정이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa9f5-118">There are four types of user accounts in this design.</span></span> <span data-ttu-id="aa9f5-119">각 계정 유형은 액세스를 위해 사이트와 특정 유형의 인증을 사용 하는 영역에 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa9f5-119">Each type of account is associated with a site for access and with a zone that uses a specific type of authentication.</span></span> 
  
- <span data-ttu-id="aa9f5-120">익명 고객-익명 고객은와 http://www.contoso.com같은 사이트를 통해 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa9f5-120">Anonymous customers — Anonymous customers have access through a site such as http://www.contoso.com.</span></span> <span data-ttu-id="aa9f5-121">사용 하는 영역은 "인터넷 영역/익명"으로, 익명 인증을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa9f5-121">The zone they use is the "Internet zone / anonymous", which uses anonymous authentication.</span></span>
    
- <span data-ttu-id="aa9f5-122">인증 된 고객-인증 된 고객이와 https://secure.contoso.com같은 사이트를 통해 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa9f5-122">Authenticated customers — Authenticated customers have access through a site such as https://secure.contoso.com.</span></span> <span data-ttu-id="aa9f5-123">사용 하는 영역은 saml 인증을 사용 하는 Azure Active Directory를 사용 하는 "엑스트라넷 영역/SAML"입니다.</span><span class="sxs-lookup"><span data-stu-id="aa9f5-123">The zone they use is the "Extranet zone / SAML", which uses Azure Active Directory with SAML authentication.</span></span>
    
- <span data-ttu-id="aa9f5-124">사이트 작성자와 개발자 — 사이트 작성자와 개발자는 http://authoring.contoso.com:8000 또는 http://www.contoso.com:8000등의 사이트를 통해 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa9f5-124">Site authors and developers — Site authors and developers have access through sites such as http://authoring.contoso.com:8000 or http://www.contoso.com:8000.</span></span> <span data-ttu-id="aa9f5-125">사용 하는 영역은 AD DS (Active Directory 도메인 서비스)를 사용 하는 "기본 영역/Windows 통합"입니다.</span><span class="sxs-lookup"><span data-stu-id="aa9f5-125">The zone they use is the "Default zone / Windows integrated", which uses Active Directory Domain Services (AD DS).</span></span>
    
- <span data-ttu-id="aa9f5-126">검색 크롤링 계정-검색 크롤링 계정에 http://authoring.contoso.com:8000 또는 http://www.contoso.com:8000등의 사이트를 통해 액세스할 권한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa9f5-126">Search Crawl Account — The search crawl account has access through sites such as http://authoring.contoso.com:8000 or http://www.contoso.com:8000.</span></span> <span data-ttu-id="aa9f5-127">이를 사용 하는 영역은 windows NTLM 인증을 사용 하는 AD DS를 사용 하는 "기본 영역/windows 통합"입니다.</span><span class="sxs-lookup"><span data-stu-id="aa9f5-127">The zone it uses is the "Default zone / Windows integrated", which uses AD DS with Windows NTLM authentication.</span></span>
    
## <a name="server-farm"></a><span data-ttu-id="aa9f5-128">서버 팜</span><span class="sxs-lookup"><span data-stu-id="aa9f5-128">Server farm</span></span>

<span data-ttu-id="aa9f5-129">사용자가 Azure를 통해 서버 팜에 액세스 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa9f5-129">The users access the server farm through Azure.</span></span> <span data-ttu-id="aa9f5-130">서버 팜에 하나 이상의 웹 서버가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa9f5-130">The server farm contains one or more Web servers.</span></span>
  
## <a name="administration-site"></a><span data-ttu-id="aa9f5-131">관리 사이트</span><span class="sxs-lookup"><span data-stu-id="aa9f5-131">Administration site</span></span>

<span data-ttu-id="aa9f5-132">관리 사이트에는 웹 응용 프로그램 중앙 관리 사이트를 사용 하는 응용 프로그램 풀 (예제의 경우 응용 프로그램 풀 1)과 통신 하는 여러 응용 프로그램 서버가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa9f5-132">The administration site contains several application servers, which communicate with an Application Pool (Application Pool 1 in the example) that uses the web application Central Administration Site.</span></span> <span data-ttu-id="aa9f5-133">중앙 관리 사이트는 조직 내의 사이트 모음에 대 한 액세스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa9f5-133">The Central Administration Site provides access to site collections within the organization.</span></span>
  
<span data-ttu-id="aa9f5-134">또한 관리 사이트에는 sql server를 설치 하 고 sql 클러스터링, 미러링 또는 alwayson을 지원 하도록 구성 된 데이터베이스 서버인 sql 데이터베이스 서버 (alwayson은 sql server 2012에만 적용 됨)가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa9f5-134">The administration site also contains SQL Database servers, which are database servers with SQL Server installed and configured to support SQL clustering, mirroring, or AlwaysOn (AlwaysOn applies to SQL Server 2012 only).</span></span>
  
## <a name="services"></a><span data-ttu-id="aa9f5-135">서비스</span><span class="sxs-lookup"><span data-stu-id="aa9f5-135">Services</span></span>

<span data-ttu-id="aa9f5-136">이 디자인 예제에는 IIS (인터넷 정보 서비스) 웹 사이트, SharePoint Web Services가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa9f5-136">The design example shows an Internet Information Services (IIS) website, SharePoint Web Services.</span></span> <span data-ttu-id="aa9f5-137">SharePoint 웹 서비스에는 세 가지 서비스, 사용자 프로필, 검색 및 관리 되는 메타 데이터가 포함 된 응용 프로그램 풀 (응용 프로그램 풀 2)이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa9f5-137">SharePoint Web Services contains an application pool (Application Pool 2) with three services, User Profile, Search, and Managed Metadata.</span></span>
  
<span data-ttu-id="aa9f5-138">인터넷 사이트용 서비스에 대 한 참고 사항:</span><span class="sxs-lookup"><span data-stu-id="aa9f5-138">Notes on Services for Internet sites:</span></span>
  
> <span data-ttu-id="aa9f5-139">Managed Metadata- **이 서비스 응용 프로그램은 열 관련 용어 집합의 기본 저장 위치**입니다 .를 선택 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa9f5-139">Managed Metadata — Be sure to select **This service application is the default storage location for column specific term sets**.</span></span>
    
> <span data-ttu-id="aa9f5-140">앱 관리 — Azure의 공용 인터넷 사이트에서 앱을 사용 하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="aa9f5-140">App Management — We do not recommend using apps in a public-facing Internet site in Azure.</span></span>
    
## <a name="application-pools-and-web-applications"></a><span data-ttu-id="aa9f5-141">응용 프로그램 풀 및 웹 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="aa9f5-141">Application pools and web applications</span></span>

<span data-ttu-id="aa9f5-142">Azure의 기본 그룹에는 Contoso Sites 라는 웹 응용 프로그램이 포함 된 응용 프로그램 풀 3이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa9f5-142">The Default Group in Azure shows Application Pool 3, which contains a web application named Contoso Sites.</span></span> <span data-ttu-id="aa9f5-143">이 경로 기반 사이트 모음은에 http://internal:8000있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa9f5-143">This path-based site collection is located at http://internal:8000.</span></span>
  
## <a name="site-collections-and-sites"></a><span data-ttu-id="aa9f5-144">사이트 모음 및 사이트</span><span class="sxs-lookup"><span data-stu-id="aa9f5-144">Site collections and sites</span></span>

<span data-ttu-id="aa9f5-145">응용 프로그램 풀에 포함 된 사이트 모음에는 다음이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa9f5-145">The site collections contained in the application pool include:</span></span>
  
- <span data-ttu-id="aa9f5-146">크롤링에 대 한 호스트 이름으로 된 사이트 모음 1 (예제 위치http://authoring.contoso.com:8000)</span><span class="sxs-lookup"><span data-stu-id="aa9f5-146">Host-named site collection 1 for crawling (example location http://authoring.contoso.com:8000)</span></span>
    
- <span data-ttu-id="aa9f5-147">쿼리에 대 한 호스트 이름으로 된 사이트 모음 2 ( http://www.contoso.com샘플 https://secure.contoso.com위치,http://www.contoso.com:8000)</span><span class="sxs-lookup"><span data-stu-id="aa9f5-147">Host-named site collection 2 for queries (sample locations http://www.contoso.com, https://secure.contoso.com, http://www.contoso.com:8000)</span></span>
    
- <span data-ttu-id="aa9f5-148">쿼리에 대 한 호스트 이름으로 된 사이트 모음 3 개 http://assets.contoso.com( https://secureassets.contoso.com샘플 위치,http://assets.contoso.com:8000)</span><span class="sxs-lookup"><span data-stu-id="aa9f5-148">Host-named site collection 3 for queries (sample locations http://assets.contoso.com, https://secureassets.contoso.com, http://assets.contoso.com:8000)</span></span>
    
## <a name="content-databases"></a><span data-ttu-id="aa9f5-149">콘텐츠 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="aa9f5-149">Content databases</span></span>

<span data-ttu-id="aa9f5-150">이 예제에서는 두 개의 콘텐츠 데이터베이스를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="aa9f5-150">The example shows two content databases.</span></span> <span data-ttu-id="aa9f5-151">하나는 크롤링에 사용 되는 사이트 모음 1입니다http://authoring.contoso.com:8000)(.</span><span class="sxs-lookup"><span data-stu-id="aa9f5-151">One is for the site collection 1 used for crawling (http://authoring.contoso.com:8000).</span></span> <span data-ttu-id="aa9f5-152">다른 하나는 쿼리에 사용 되는 두 개의 사이트 모음 2와 3입니다http://www.contoso.com( https://secure.contoso.com, http://www.contoso.com:8000, 또는 http://assets.contoso.com, https://secureassets.contoso.com, http://assets.contoso.com:8000),).</span><span class="sxs-lookup"><span data-stu-id="aa9f5-152">The other is for the two site collections 2 and 3 used for queries (http://www.contoso.com, https://secure.contoso.com, http://www.contoso.com:8000, or http://assets.contoso.com, https://secureassets.contoso.com, http://assets.contoso.com:8000).</span></span>
  
## <a name="zones-and-urls"></a><span data-ttu-id="aa9f5-153">영역 및 URL</span><span class="sxs-lookup"><span data-stu-id="aa9f5-153">Zones and URLs</span></span>

<span data-ttu-id="aa9f5-154">이 예제에서는 서로 다른 사용자 계정에서 사용 하는 연결 된 부하 분산 url이 포함 된 세 개의 영역을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="aa9f5-154">The example shows three zones with the associated load-balanced URLs that are used by different user accounts.</span></span> 
  
<span data-ttu-id="aa9f5-155">영역 및 url의 첫 목록은 사이트 모음 1과 관련 되며 다음 정보를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa9f5-155">The first list of zones and URLs is related to site collection 1, and it contains the following information:</span></span>
  
- <span data-ttu-id="aa9f5-156">사용자-사이트 작성자</span><span class="sxs-lookup"><span data-stu-id="aa9f5-156">Users - Site authors</span></span>
    
- <span data-ttu-id="aa9f5-157">영역-기본값</span><span class="sxs-lookup"><span data-stu-id="aa9f5-157">Zone - Default</span></span>
    
- <span data-ttu-id="aa9f5-158">부하 분산 된 URL-http://authoring.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="aa9f5-158">Load-balanced URL - http://authoring.contoso.com:8000</span></span>
    
<span data-ttu-id="aa9f5-159">영역과 url의 두 번째 목록에는 세 가지 영역에 서로 다른 세 가지 유형의 사용자가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa9f5-159">The second list of zones and URLs has three different types of users in three different zones.</span></span> <span data-ttu-id="aa9f5-160">이는 사이트 모음 2와 관련 되며 다음과 같은 정보를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa9f5-160">It is related to site collection 2, and it contains the following information:</span></span>
  
<span data-ttu-id="aa9f5-161">첫 번째 영역:</span><span class="sxs-lookup"><span data-stu-id="aa9f5-161">First zone:</span></span>
  
- <span data-ttu-id="aa9f5-162">사용자-사이트 작성자</span><span class="sxs-lookup"><span data-stu-id="aa9f5-162">Users - Site authors</span></span>
    
- <span data-ttu-id="aa9f5-163">영역-기본값</span><span class="sxs-lookup"><span data-stu-id="aa9f5-163">Zone - Default</span></span>
    
- <span data-ttu-id="aa9f5-164">부하 분산 된 URL-http://www.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="aa9f5-164">Load-balanced URL - http://www.contoso.com:8000</span></span>
    
<span data-ttu-id="aa9f5-165">두 번째 영역:</span><span class="sxs-lookup"><span data-stu-id="aa9f5-165">Second zone:</span></span>
  
- <span data-ttu-id="aa9f5-166">사용자-익명 고객</span><span class="sxs-lookup"><span data-stu-id="aa9f5-166">Users - Anonymous customers</span></span>
    
- <span data-ttu-id="aa9f5-167">영역-인터넷</span><span class="sxs-lookup"><span data-stu-id="aa9f5-167">Zone - Internet</span></span>
    
- <span data-ttu-id="aa9f5-168">부하 분산 된 URL-http://www.contoso.com</span><span class="sxs-lookup"><span data-stu-id="aa9f5-168">Load-balanced URL - http://www.contoso.com</span></span>
    
<span data-ttu-id="aa9f5-169">세 번째 영역:</span><span class="sxs-lookup"><span data-stu-id="aa9f5-169">Third zone:</span></span>
  
- <span data-ttu-id="aa9f5-170">사용자 인증 고객</span><span class="sxs-lookup"><span data-stu-id="aa9f5-170">Users - Authenticated customers</span></span>
    
- <span data-ttu-id="aa9f5-171">영역 엑스트라넷</span><span class="sxs-lookup"><span data-stu-id="aa9f5-171">Zone - Extranet</span></span>
    
- <span data-ttu-id="aa9f5-172">부하 분산 된 URL-https://secure.contoso.com</span><span class="sxs-lookup"><span data-stu-id="aa9f5-172">Load-balanced URL - https://secure.contoso.com</span></span>
    
<span data-ttu-id="aa9f5-173">영역 및 url의 세 번째 목록에는 세 가지 다른 영역에서 세 가지 유형의 사용자가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa9f5-173">The third list of zones and URLs has three different types of users in three different zones.</span></span> <span data-ttu-id="aa9f5-174">이는 사이트 모음 3과 관련 되며 다음과 같은 정보를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa9f5-174">It is related to site collection 3, and it contains the following information:</span></span>
  
<span data-ttu-id="aa9f5-175">첫 번째 영역:</span><span class="sxs-lookup"><span data-stu-id="aa9f5-175">First zone:</span></span>
  
- <span data-ttu-id="aa9f5-176">사용자-사이트 작성자</span><span class="sxs-lookup"><span data-stu-id="aa9f5-176">Users - Site authors</span></span>
    
- <span data-ttu-id="aa9f5-177">영역-인터넷</span><span class="sxs-lookup"><span data-stu-id="aa9f5-177">Zone - Internet</span></span>
    
- <span data-ttu-id="aa9f5-178">부하 분산 된 URL-http://assets.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="aa9f5-178">Load-balanced URL - http://assets.contoso.com:8000</span></span>
    
<span data-ttu-id="aa9f5-179">두 번째 영역:</span><span class="sxs-lookup"><span data-stu-id="aa9f5-179">Second zone:</span></span>
  
- <span data-ttu-id="aa9f5-180">사용자-익명 고객</span><span class="sxs-lookup"><span data-stu-id="aa9f5-180">Users - Anonymous customers</span></span>
    
- <span data-ttu-id="aa9f5-181">영역-인터넷</span><span class="sxs-lookup"><span data-stu-id="aa9f5-181">Zone - Internet</span></span>
    
- <span data-ttu-id="aa9f5-182">부하 분산 된 URL-http://assets.contoso.com</span><span class="sxs-lookup"><span data-stu-id="aa9f5-182">Load-balanced URL - http://assets.contoso.com</span></span>
    
<span data-ttu-id="aa9f5-183">세 번째 영역:</span><span class="sxs-lookup"><span data-stu-id="aa9f5-183">Third zone:</span></span>
  
- <span data-ttu-id="aa9f5-184">사용자 인증 고객</span><span class="sxs-lookup"><span data-stu-id="aa9f5-184">Users - Authenticated customers</span></span>
    
- <span data-ttu-id="aa9f5-185">영역 엑스트라넷</span><span class="sxs-lookup"><span data-stu-id="aa9f5-185">Zone - Extranet</span></span>
    
- <span data-ttu-id="aa9f5-186">부하 분산 된 URL-http://secureassets.contoso.com</span><span class="sxs-lookup"><span data-stu-id="aa9f5-186">Load-balanced URL - http://secureassets.contoso.com</span></span>
    

