---
title: "액세스할 수 있는 다이어그램-SharePoint 2013에 대 한 Microsoft Azure의 디자인 샘플 인터넷 사이트"
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
description: "이 문서는 디자인 sample 다이어그램의 액세스할 수 있는 텍스트 버전: SharePoint 2013에 대 한 Microsoft Azure의 인터넷 사이트입니다."
ms.openlocfilehash: 0d42a96f80d47b360084557fea47c4155d106d30
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/09/2018
---
# <a name="accessible-diagram---design-sample-internet-sites-in-microsoft-azure-for-sharepoint-2013"></a><span data-ttu-id="6c11b-103">액세스할 수 있는 다이어그램-디자인 예제: SharePoint 2013에 대 한 Microsoft Azure의 인터넷 사이트</span><span class="sxs-lookup"><span data-stu-id="6c11b-103">Accessible diagram - Design sample: Internet sites in Microsoft Azure for SharePoint 2013</span></span>

<span data-ttu-id="6c11b-104">**요약:** 이 문서는 디자인 sample 다이어그램의 액세스할 수 있는 텍스트 버전: SharePoint 2013에 대 한 Microsoft Azure의 인터넷 사이트입니다.</span><span class="sxs-lookup"><span data-stu-id="6c11b-104">**Summary:** This article is an accessible text version of the diagram named Design sample: Internet sites in Microsoft Azure for SharePoint 2013.</span></span>
  
<span data-ttu-id="6c11b-105">SharePoint 2013을 사용 하 여 Azure에는 인터넷 사이트에 대 한 시작 지점으로이 디자인 예제를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c11b-105">Use this design example as a starting point for an Internet-facing site in Azure using SharePoint 2013.</span></span>
  
<span data-ttu-id="6c11b-106">이 포스터에서는 SharePoint 2013의 다음과 같은 측면을 디자인 하는 방법의 예를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="6c11b-106">This poster shows an example of how to design the following aspects of SharePoint 2013:</span></span>
  
- <span data-ttu-id="6c11b-107">사용자</span><span class="sxs-lookup"><span data-stu-id="6c11b-107">Users</span></span>
    
- <span data-ttu-id="6c11b-108">영역 및 인증</span><span class="sxs-lookup"><span data-stu-id="6c11b-108">Zones and authentication</span></span>
    
- <span data-ttu-id="6c11b-109">서버 팜</span><span class="sxs-lookup"><span data-stu-id="6c11b-109">Server farm</span></span>
    
- <span data-ttu-id="6c11b-110">관리 사이트</span><span class="sxs-lookup"><span data-stu-id="6c11b-110">Administration site</span></span>
    
- <span data-ttu-id="6c11b-111">서비스</span><span class="sxs-lookup"><span data-stu-id="6c11b-111">Services</span></span>
    
- <span data-ttu-id="6c11b-112">응용 프로그램 풀 및 웹 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="6c11b-112">Application pools and web applications</span></span>
    
- <span data-ttu-id="6c11b-113">사이트 모음</span><span class="sxs-lookup"><span data-stu-id="6c11b-113">Site collections</span></span>
    
- <span data-ttu-id="6c11b-114">사이트</span><span class="sxs-lookup"><span data-stu-id="6c11b-114">Sites</span></span>
    
- <span data-ttu-id="6c11b-115">콘텐츠 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="6c11b-115">Content databases</span></span>
    
- <span data-ttu-id="6c11b-116">영역 및 URL</span><span class="sxs-lookup"><span data-stu-id="6c11b-116">Zones and URLs</span></span>
    
## <a name="users-zones-and-authentication"></a><span data-ttu-id="6c11b-117">사용자, 영역 및 인증</span><span class="sxs-lookup"><span data-stu-id="6c11b-117">Users, zones and authentication</span></span>

<span data-ttu-id="6c11b-p101">이 디자인의 사용자 계정에 다음과 같은 네가지 유형의 있습니다. 각 유형의 계정 액세스에 대 한 사이트와 특정 유형의 인증을 사용 하는 영역에 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c11b-p101">There are four types of user accounts in this design. Each type of account is associated with a site for access and with a zone that uses a specific type of authentication.</span></span> 
  
- <span data-ttu-id="6c11b-120">익명 고객-익명 고객 예: http://www.contoso.com 사이트를 통해 액세스 권한이 있습니다. 자신이 사용 하 여 영역은 "인터넷 영역 익명 /", 익명 인증을 사용 하는 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c11b-120">Anonymous customers — Anonymous customers have access through a site such as http://www.contoso.com. The zone they use is the "Internet zone / anonymous", which uses anonymous authentication.</span></span>
    
- <span data-ttu-id="6c11b-121">고객 인증-인증 된 고객 https://secure.contoso.com와 같은 사이트를 통해 액세스 권한이 있습니다. 자신이 사용 하 여 영역은 "익스트라넷 영역 / SAML", Azure Active Directory를 사용 하 여 SAML 인증을 사용 하는 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c11b-121">Authenticated customers — Authenticated customers have access through a site such as https://secure.contoso.com. The zone they use is the "Extranet zone / SAML", which uses Azure Active Directory with SAML authentication.</span></span>
    
- <span data-ttu-id="6c11b-p102">사이트 작성자 및 개발자 — 사이트 작성자와 개발자가 http://authoring.contoso.com:8000 또는 http://www.contoso.com:8000 등의 사이트를 통해 액세스할 수 있습니다. 자신이 사용 하 여 영역은 "기본 영역 Windows 통합 /", Active Directory 도메인 서비스 (AD DS)를 사용 하는 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c11b-p102">Site authors and developers — Site authors and developers have access through sites such as http://authoring.contoso.com:8000 or http://www.contoso.com:8000. The zone they use is the "Default zone / Windows integrated", which uses Active Directory Domain Services (AD DS).</span></span>
    
- <span data-ttu-id="6c11b-p103">검색 크롤링 계정-검색 크롤링 계정에 액세스 권한이 http://authoring.contoso.com:8000 또는 http://www.contoso.com:8000 등의 사이트를 통해 합니다. 사용 하 여 영역은 "기본 영역 Windows 통합 /", 하는 AD DS를 사용 하 여 Windows NTLM 인증을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c11b-p103">Search Crawl Account — The search crawl account has access through sites such as http://authoring.contoso.com:8000 or http://www.contoso.com:8000. The zone it uses is the "Default zone / Windows integrated", which uses AD DS with Windows NTLM authentication.</span></span>
    
## <a name="server-farm"></a><span data-ttu-id="6c11b-126">서버 팜</span><span class="sxs-lookup"><span data-stu-id="6c11b-126">Server farm</span></span>

<span data-ttu-id="6c11b-p104">서버 팜 Azure를 통해 액세스 하는 사용자입니다. 서버 팜 하나 이상의 웹 서버를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="6c11b-p104">The users access the server farm through Azure. The server farm contains one or more Web servers.</span></span>
  
## <a name="administration-site"></a><span data-ttu-id="6c11b-129">관리 사이트</span><span class="sxs-lookup"><span data-stu-id="6c11b-129">Administration site</span></span>

<span data-ttu-id="6c11b-p105">관리 사이트 중앙 관리 사이트 웹 응용 프로그램을 사용 하는 응용 프로그램 풀 (이 예제에서 응용 프로그램 풀 1)와 통신 하는 여러 응용 프로그램 서버를 포함 합니다. 중앙 관리 사이트는 조직 내에서 사이트 모음에 대 한 액세스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6c11b-p105">The administration site contains several application servers, which communicate with an Application Pool (Application Pool 1 in the example) that uses the web application Central Administration Site. The Central Administration Site provides access to site collections within the organization.</span></span>
  
<span data-ttu-id="6c11b-132">관리 사이트에도 SQL 클러스터링, 미러링 또는 AlwaysOn을 지원 하도록 SQL server 설치 및 구성 데이터베이스 서버는 SQL 데이터베이스 서버를 포함 (AlwaysOn 적용 하는 SQL Server 2012에만 해당).</span><span class="sxs-lookup"><span data-stu-id="6c11b-132">The administration site also contains SQL Database servers, which are database servers with SQL Server installed and configured to support SQL clustering, mirroring, or AlwaysOn (AlwaysOn applies to SQL Server 2012 only).</span></span>
  
## <a name="services"></a><span data-ttu-id="6c11b-133">서비스</span><span class="sxs-lookup"><span data-stu-id="6c11b-133">Services</span></span>

<span data-ttu-id="6c11b-p106">디자인 예제는 인터넷 정보 서비스 (IIS) 웹사이트, SharePoint 웹 서비스를 보여줍니다. SharePoint 웹 서비스는 세개의 서비스, 사용자 프로필, 검색 및 관리 되는 메타 데이터와 응용 프로그램 풀 (응용 프로그램 풀 2)를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="6c11b-p106">The design example shows an Internet Information Services (IIS) website, SharePoint Web Services. SharePoint Web Services contains an application pool (Application Pool 2) with three services, User Profile, Search, and Managed Metadata.</span></span>
  
<span data-ttu-id="6c11b-136">인터넷 사이트에 대 한 서비스에 대 한 참고 사항:</span><span class="sxs-lookup"><span data-stu-id="6c11b-136">Notes on Services for Internet sites:</span></span>
  
> <span data-ttu-id="6c11b-137">관리 되는 메타 데이터- **이 서비스 응용 프로그램은 열 관련 용어 집합에 대 한 기본 저장소 위치를**선택 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c11b-137">Managed Metadata — Be sure to select **This service application is the default storage location for column specific term sets**.</span></span>
    
> <span data-ttu-id="6c11b-138">응용 프로그램 관리-좋지 않습니다 Azure에서 공용 인터넷 사이트에서 앱을 사용 하 여 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c11b-138">App Management — We do not recommend using apps in a public-facing Internet site in Azure.</span></span>
    
## <a name="application-pools-and-web-applications"></a><span data-ttu-id="6c11b-139">응용 프로그램 풀 및 웹 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="6c11b-139">Application pools and web applications</span></span>

<span data-ttu-id="6c11b-p107">Azure의 기본 그룹 Contoso 사이트 이름이 지정 된 웹 응용 프로그램을 포함 하는 응용 프로그램 풀 3을 표시 합니다. 이 경로 기반 사이트 모음은 http://internal:8000에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c11b-p107">The Default Group in Azure shows Application Pool 3, which contains a web application named Contoso Sites. This path-based site collection is located at http://internal:8000.</span></span>
  
## <a name="site-collections-and-sites"></a><span data-ttu-id="6c11b-142">사이트 모음 및 사이트</span><span class="sxs-lookup"><span data-stu-id="6c11b-142">Site collections and sites</span></span>

<span data-ttu-id="6c11b-143">응용 프로그램 풀에 포함 된 사이트 모음에는 다음이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c11b-143">The site collections contained in the application pool include:</span></span>
  
- <span data-ttu-id="6c11b-144">호스트 이름이 지정 된 사이트 모음 1 위치에 대 한 크롤링 (예제 http://authoring.contoso.com:8000)</span><span class="sxs-lookup"><span data-stu-id="6c11b-144">Host-named site collection 1 for crawling (example location http://authoring.contoso.com:8000)</span></span>
    
- <span data-ttu-id="6c11b-145">쿼리 (샘플 위치 http://www.contoso.com, https://secure.contoso.com, http://www.contoso.com:8000)에 대 한 호스트 이름이 지정 된 사이트 모음 2</span><span class="sxs-lookup"><span data-stu-id="6c11b-145">Host-named site collection 2 for queries (sample locations http://www.contoso.com, https://secure.contoso.com, http://www.contoso.com:8000)</span></span>
    
- <span data-ttu-id="6c11b-146">쿼리 (샘플 위치 http://assets.contoso.com, https://secureassets.contoso.com, http://assets.contoso.com:8000)에 대 한 호스트 이름이 지정 된 사이트 모음 3</span><span class="sxs-lookup"><span data-stu-id="6c11b-146">Host-named site collection 3 for queries (sample locations http://assets.contoso.com, https://secureassets.contoso.com, http://assets.contoso.com:8000)</span></span>
    
## <a name="content-databases"></a><span data-ttu-id="6c11b-147">콘텐츠 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="6c11b-147">Content databases</span></span>

<span data-ttu-id="6c11b-p108">이 예제에서는 두 콘텐츠 데이터베이스를 보여줍니다. 하나는 사이트 모음 크롤링 (http://authoring.contoso.com:8000)에 사용 되는 1입니다. 다른 두 사이트 모음 2 및 3 쿼리 (http://www.contoso.com, https://secure.contoso.com, http://www.contoso.com:8000, 또는 http://assets.contoso.com, https://secureassets.contoso.com, http://assets.contoso.com:8000)에 사용 되는 단계입니다.</span><span class="sxs-lookup"><span data-stu-id="6c11b-p108">The example shows two content databases. One is for the site collection 1 used for crawling (http://authoring.contoso.com:8000). The other is for the two site collections 2 and 3 used for queries (http://www.contoso.com, https://secure.contoso.com, http://www.contoso.com:8000, or http://assets.contoso.com, https://secureassets.contoso.com, http://assets.contoso.com:8000).</span></span>
  
## <a name="zones-and-urls"></a><span data-ttu-id="6c11b-151">영역 및 URL</span><span class="sxs-lookup"><span data-stu-id="6c11b-151">Zones and URLs</span></span>

<span data-ttu-id="6c11b-152">이 예제에서는 서로 다른 사용자 계정에서 사용 되는 연결 된 부하 분산 된 Url이 포함 된 세 영역을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="6c11b-152">The example shows three zones with the associated load-balanced URLs that are used by different user accounts.</span></span> 
  
<span data-ttu-id="6c11b-153">사이트 모음 1, 영역 및 Url의 첫째 목록와 관련 된 하 고 다음 정보를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c11b-153">The first list of zones and URLs is related to site collection 1, and it contains the following information:</span></span>
  
- <span data-ttu-id="6c11b-154">사용자가-사이트 작성자</span><span class="sxs-lookup"><span data-stu-id="6c11b-154">Users - Site authors</span></span>
    
- <span data-ttu-id="6c11b-155">영역-기본</span><span class="sxs-lookup"><span data-stu-id="6c11b-155">Zone - Default</span></span>
    
- <span data-ttu-id="6c11b-156">부하 분산 된 URL-http://authoring.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="6c11b-156">Load-balanced URL - http://authoring.contoso.com:8000</span></span>
    
<span data-ttu-id="6c11b-p109">영역 및 Url의 두번째 목록 3 개의 다른 영역에서 서로 다른 세가지 유형의 사용자에 있습니다. 사이트 모음 2와 관련 된 하 고 다음 정보를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c11b-p109">The second list of zones and URLs has three different types of users in three different zones. It is related to site collection 2, and it contains the following information:</span></span>
  
<span data-ttu-id="6c11b-159">첫번째 영역:</span><span class="sxs-lookup"><span data-stu-id="6c11b-159">First zone:</span></span>
  
- <span data-ttu-id="6c11b-160">사용자가-사이트 작성자</span><span class="sxs-lookup"><span data-stu-id="6c11b-160">Users - Site authors</span></span>
    
- <span data-ttu-id="6c11b-161">영역-기본</span><span class="sxs-lookup"><span data-stu-id="6c11b-161">Zone - Default</span></span>
    
- <span data-ttu-id="6c11b-162">부하 분산 된 URL-http://www.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="6c11b-162">Load-balanced URL - http://www.contoso.com:8000</span></span>
    
<span data-ttu-id="6c11b-163">두번째 영역:</span><span class="sxs-lookup"><span data-stu-id="6c11b-163">Second zone:</span></span>
  
- <span data-ttu-id="6c11b-164">사용자가-익명 고객</span><span class="sxs-lookup"><span data-stu-id="6c11b-164">Users - Anonymous customers</span></span>
    
- <span data-ttu-id="6c11b-165">영역-인터넷</span><span class="sxs-lookup"><span data-stu-id="6c11b-165">Zone - Internet</span></span>
    
- <span data-ttu-id="6c11b-166">부하 분산 된 URL-http://www.contoso.com</span><span class="sxs-lookup"><span data-stu-id="6c11b-166">Load-balanced URL - http://www.contoso.com</span></span>
    
<span data-ttu-id="6c11b-167">세번째 영역:</span><span class="sxs-lookup"><span data-stu-id="6c11b-167">Third zone:</span></span>
  
- <span data-ttu-id="6c11b-168">사용자가-인증 된 고객</span><span class="sxs-lookup"><span data-stu-id="6c11b-168">Users - Authenticated customers</span></span>
    
- <span data-ttu-id="6c11b-169">영역-엑스트라넷</span><span class="sxs-lookup"><span data-stu-id="6c11b-169">Zone - Extranet</span></span>
    
- <span data-ttu-id="6c11b-170">부하 분산 된 URL-https://secure.contoso.com</span><span class="sxs-lookup"><span data-stu-id="6c11b-170">Load-balanced URL - https://secure.contoso.com</span></span>
    
<span data-ttu-id="6c11b-p110">영역 및 Url의 세번째 목록 3 개의 다른 영역에서 서로 다른 세가지 유형의 사용자에 있습니다. 사이트 모음 3와 관련 된 하 고는 다음 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c11b-p110">The third list of zones and URLs has three different types of users in three different zones. It is related to site collection 3, and it contains the following information:</span></span>
  
<span data-ttu-id="6c11b-173">첫번째 영역:</span><span class="sxs-lookup"><span data-stu-id="6c11b-173">First zone:</span></span>
  
- <span data-ttu-id="6c11b-174">사용자가-사이트 작성자</span><span class="sxs-lookup"><span data-stu-id="6c11b-174">Users - Site authors</span></span>
    
- <span data-ttu-id="6c11b-175">영역-인터넷</span><span class="sxs-lookup"><span data-stu-id="6c11b-175">Zone - Internet</span></span>
    
- <span data-ttu-id="6c11b-176">부하 분산 된 URL-http://assets.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="6c11b-176">Load-balanced URL - http://assets.contoso.com:8000</span></span>
    
<span data-ttu-id="6c11b-177">두번째 영역:</span><span class="sxs-lookup"><span data-stu-id="6c11b-177">Second zone:</span></span>
  
- <span data-ttu-id="6c11b-178">사용자가-익명 고객</span><span class="sxs-lookup"><span data-stu-id="6c11b-178">Users - Anonymous customers</span></span>
    
- <span data-ttu-id="6c11b-179">영역-인터넷</span><span class="sxs-lookup"><span data-stu-id="6c11b-179">Zone - Internet</span></span>
    
- <span data-ttu-id="6c11b-180">부하 분산 된 URL-http://assets.contoso.com</span><span class="sxs-lookup"><span data-stu-id="6c11b-180">Load-balanced URL - http://assets.contoso.com</span></span>
    
<span data-ttu-id="6c11b-181">세번째 영역:</span><span class="sxs-lookup"><span data-stu-id="6c11b-181">Third zone:</span></span>
  
- <span data-ttu-id="6c11b-182">사용자가-인증 된 고객</span><span class="sxs-lookup"><span data-stu-id="6c11b-182">Users - Authenticated customers</span></span>
    
- <span data-ttu-id="6c11b-183">영역-엑스트라넷</span><span class="sxs-lookup"><span data-stu-id="6c11b-183">Zone - Extranet</span></span>
    
- <span data-ttu-id="6c11b-184">부하 분산 된 URL-http://secureassets.contoso.com</span><span class="sxs-lookup"><span data-stu-id="6c11b-184">Load-balanced URL - http://secureassets.contoso.com</span></span>
    

