---
title: 액세스 가능한 다이어그램-온-프레미스 eDiscovery 흐름
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b9dcd692-0485-4eec-870d-87ab6b89d97b
description: 이 문서는 온-프레미스 eDiscovery 흐름 이라는 다이어그램의 액세스 가능한 텍스트 버전입니다.
ms.openlocfilehash: bdaf46c552b346d0e6966cd3589f239146ddadc5
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068534"
---
# <a name="accessible-diagram---on-premises-ediscovery-flow"></a><span data-ttu-id="5cd84-103">액세스 가능한 다이어그램-온-프레미스 eDiscovery 흐름</span><span class="sxs-lookup"><span data-stu-id="5cd84-103">Accessible diagram - On-premises eDiscovery Flow</span></span>

<span data-ttu-id="5cd84-104">**요약:** 이 문서는 온-프레미스 eDiscovery 흐름 이라는 다이어그램의 액세스 가능한 텍스트 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="5cd84-104">**Summary:** This article is an accessible text version of the diagram named On-premises eDiscovery Flow.</span></span>
  
<span data-ttu-id="5cd84-105">이 포스터는 서버 제품 간의 데이터 아키텍처 및 흐름에 대 한 세부 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cd84-105">This poster provides details about the architecture and flow of data across server products.</span></span> 
  
## <a name="across-sharepoint-exchange-lync-and-file-shares"></a><span data-ttu-id="5cd84-106">SharePoint, Exchange, Lync 및 파일 공유에서</span><span class="sxs-lookup"><span data-stu-id="5cd84-106">Across SharePoint, Exchange, Lync, and file shares</span></span>

<span data-ttu-id="5cd84-107">이 다이어그램에서는 두 서버 팜, SharePoint 2013 엔터프라이즈 응용 프로그램 팜 및 SharePoint 2013 서비스 팜에 액세스 하는 쿼리를 전송 하는 사용자를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5cd84-107">The diagram shows a user sending a query that accesses two server farms, a SharePoint 2013 Enterprise App Farm, and a SharePoint 2013 Services Farm.</span></span> <span data-ttu-id="5cd84-108">SharePoint 2013 서비스 팜은 SharePoint 2013 콘텐츠 팜, Exchange Server 2013 (Lync 2013와 통신) 및 Windows 파일 공유와 통신 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cd84-108">The SharePoint 2013 Services Farm communicates with a SharePoint 2013 Content Farm, Exchange Server 2013 (which communicates with Lync 2013), and Windows File Shares.</span></span> 
  
<span data-ttu-id="5cd84-109">EDiscovery 흐름 목록에서는 데이터 흐름 및 SharePoint, Exchange, Lync 및 파일 공유에서 eDisovery 쿼리 동작이 수행 되는 순서를 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cd84-109">The eDiscovery Flow List describes the flow of data and the order in which eDisovery query actions occur across SharePoint, Exchange, Lync, and file shares.</span></span> 
  
<span data-ttu-id="5cd84-110">EDiscovery 흐름 목록은 먼저 자세히 설명한 다음 다이어그램에 표시 된 기능에 대 한 자세한 설명을 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cd84-110">The eDiscovery flow list is described in detail first, followed by a detailed description of the features depicted in the diagram.</span></span> 
  
### <a name="ediscovery-flow-list"></a><span data-ttu-id="5cd84-111">eDiscovery 흐름 목록</span><span class="sxs-lookup"><span data-stu-id="5cd84-111">eDiscovery Flow List</span></span>

<span data-ttu-id="5cd84-112">이 목록에서 설명 하는 각 단계의 번호는 다이어그램에 표시 된 단계와 관련이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cd84-112">The numbers for each of the steps described in this list pertain to a step depicted in the diagram.</span></span> <span data-ttu-id="5cd84-113">다이어그램은이 문서 뒷부분에 자세히 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cd84-113">The diagram is described in detail later in this document.</span></span> 
  
1. <span data-ttu-id="5cd84-114">eDiscovery 사례를 만들고 관리 하며 eDiscovery 센터 (EDC)에서 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cd84-114">eDiscovery cases are created, managed, and used in the eDiscovery center (EDC).</span></span> <span data-ttu-id="5cd84-115">EDC은 SharePoint 2013 사이트 모음입니다.</span><span class="sxs-lookup"><span data-stu-id="5cd84-115">The EDC is a SharePoint 2013 site collection.</span></span> <span data-ttu-id="5cd84-116">사례를 정의 하 고, 추적할 원본을 식별 하 고, 쿼리를 실행 하 고, 쿼리 결과를 검토 하 고, 콘텐츠에 대 한 보류를 설정 하거나 제거 하는 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="5cd84-116">This is where cases are defined, sources to be tracked are identified, queries are issued, query results are reviewed, and holds on content are placed or removed.</span></span> 
    
2. <span data-ttu-id="5cd84-117">보류 위치, ReleaseHold 나 GetStatus 등의 eDiscovery 쿼리 또는 작업은 EDC에서 엔터프라이즈 앱 팜의 SSA (Search Service Application) 프록시로 릴레이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cd84-117">The eDiscovery query or action, such as place a Hold, ReleaseHold, or GetStatus, is relayed from the EDC to the Search Service Application (SSA) proxy in the Enterprise App Farm.</span></span> <span data-ttu-id="5cd84-118">그런 다음 SSA 프록시는 서비스 응용 프로그램 팜의 SSA로 트래픽을 릴레이 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cd84-118">The SSA proxy then relays the traffic to the SSA in the Services App Farm.</span></span> <span data-ttu-id="5cd84-119">이 예에서 요청은 보류 중인 파일 이름에 "CONTOSO"를 포함 하는 항목을 SharePoint 콘텐츠 팜에 배치 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="5cd84-119">In this example, the request is to place anything in the SharePoint Content Farm with "CONTOSO" in the file name on hold.</span></span> 
    
3. <span data-ttu-id="5cd84-120">요청이 사례를 쿼리 하는 경우 SSA는 검색 인덱스를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="5cd84-120">If the request is to query a case, the SSA consults the search index.</span></span> <span data-ttu-id="5cd84-121">그런 다음 eDiscovery 쿼리 결과 집합은 EDC를 통해 사용자에 게 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cd84-121">Then, the eDiscovery query result set returns to the user through the EDC.</span></span> 
    
4. <span data-ttu-id="5cd84-122">보류 또는 ReleaseHold 있는 등의 작업을 수행 하는 경우 해당 작업이 SSA 관리 데이터베이스의 Actions_Table에 기록 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cd84-122">If the request is an action, such as place a Hold or ReleaseHold, that action is written to the Actions_Table in the SSA Administrative database.</span></span> <span data-ttu-id="5cd84-123">이 예제에서는 "CONTOSO"가 포함 된 SharePoint 콘텐츠 팜의 모든 항목에 대 한 보류 요청이 Actions_Table에 기록 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cd84-123">In this example, a hold request for anything in the SharePoint Content Farm with "CONTOSO" is written to the Actions_Table.</span></span> 
    
5. <span data-ttu-id="5cd84-124">정기적으로 콘텐츠 팜 eDiscovery 원본 위치 유지 타이머 작업이 작동을 중단 하 고 보류 중인 작업에 대 한 요청을 생성 하 고 SSA 프록시를 통해 상태 업데이트를 SSA로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="5cd84-124">At regular intervals the Content Farm eDiscovery in-place hold timer job wakes up and generates a request for pending actions and sends status updates through the SSA proxy to the SSA.</span></span> 
    
6. <span data-ttu-id="5cd84-125">보류 중인 작업에 대 한 쿼리는 콘텐츠 팜에 대 한 보류 중인 작업에 대 한 Action_Table를 검색 하는 중앙 SSA로 릴레이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cd84-125">The query for pending actions is relayed to the central SSA, which consults the Action_Table for any pending actions for the Content Farm.</span></span> <span data-ttu-id="5cd84-126">또한 콘텐츠 팜 원본 위치 유지 타이머 작업은 개체 및 받은 작업에 대 한 상태 업데이트를 전송 하 여 ActionsTable에 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cd84-126">The Content Farm in-place hold timer job also sends status updates for objects and actions it has received, which are written to the ActionsTable.</span></span> 
    
7. <span data-ttu-id="5cd84-127">SharePoint 2013 콘텐츠 팜의 이름에 "CONTOSO"가 포함 된 콘텐츠에 대 한 보류 요청은 콘텐츠 팜의 eDiscovery 원본 위치 유지 타이머 작업으로 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cd84-127">The hold request for any content with "CONTOSO" in the name in the SharePoint 2013 Content Farm is sent by the SSA to the eDiscovery in-place hold timer job in the Content Farm.</span></span> 
    
8. <span data-ttu-id="5cd84-128">EDiscovery 원본 위치 유지 타이머 작업은 "CONTOSO Site" 및 "CONTOSO content"를 보류 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cd84-128">The eDiscovery in-place hold timer job places the "CONTOSO Site" and "CONTOSO content" on hold.</span></span> 
    
9. <span data-ttu-id="5cd84-129">EDiscovery 원본 위치 유지 타이머 작업이 엔터프라이즈 앱 팜에서 주기적으로 실행 되어 검색 작업의 상태를 확인 하 고 상태를 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cd84-129">The eDiscovery in-place hold timer job periodically runs in the Enterprise App Farm to check the status of discovery actions and to update the status.</span></span> 
    
10. <span data-ttu-id="5cd84-130">상태 쿼리가 엔터프라이즈 앱 팜 SSA 프록시를 통해 SharePoint Services 팜 SSA로 릴레이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cd84-130">The status query is relayed through the Enterprise App Farm SSA proxy to the SharePoint Services Farm SSA.</span></span> 
    
11. <span data-ttu-id="5cd84-131">SSA가 작업 테이블에서 상태를 검색 하 고 엔터프라이즈 앱 팜의 타이머 작업으로 반환 하 여 상태 업데이트를 EDC에 밀어넣습니다.</span><span class="sxs-lookup"><span data-stu-id="5cd84-131">The SSA retrieves the status from the Actions table and returns it to the timer job in the Enterprise App Farm, which pushes the status updates to the EDC.</span></span> 
    
12. <span data-ttu-id="5cd84-132">EDiscovery 사용자가 사서함 또는 보관 된 Lync 콘텐츠와 같은 Exchange 원본에 대해 검색 하거나 작업을 수행 하는 경우 중앙 SSA는 EWS (Exchange 웹 서비스) 프록시를 사용 하 여 Exchange 웹 서비스를 쿼리 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cd84-132">When the eDiscovery user is searching (or performing an action) for Exchange sources, such as a mailbox or archived Lync content, the central SSA uses Exchange Web Services (EWS) proxy to query Exchange Web Services.</span></span> <span data-ttu-id="5cd84-133">Exchange에는 자체 검색 및 eDiscovery 인프라가 있으며 모든 eDiscovery 통화를 내부적으로 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cd84-133">Exchange has its own search and eDiscovery infrastructure and manages all eDiscovery calls internally.</span></span> 
    
13. <span data-ttu-id="5cd84-134">Exchange 웹 서비스는 eDiscovery 검색 결과를 포함 하는 SSA에 응답 하 고 쿼리 기반 보존에 대 한 상태 요청에 대 한 응답을 차례로 EDC로 릴레이 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cd84-134">Exchange Web Services responds to SSA with eDiscovery search results or a response to a status request for a query-based hold, which, in turn, gets relayed to the EDC.</span></span> 
    
#### <a name="prerequisites"></a><span data-ttu-id="5cd84-135">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="5cd84-135">Prerequisites</span></span>

- <span data-ttu-id="5cd84-136">SharePoint 엔터프라이즈 검색을 구성 해야 하 고, 콘텐츠 원본 (SharePoint 및 Windows 파일 공유)에 대 한 검색 크롤링이 성공적으로 수행 되며, 모든 콘텐츠 원본이 인덱스에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cd84-136">SharePoint Enterprise Search must be configured, search crawls on content sources (SharePoint and Windows file shares) are successfully occurring, and all content sources are in the index.</span></span> 
    
- <span data-ttu-id="5cd84-137">서버 간 트러스트 및 인증은 SharePoint Services 팜과 Exchange와 Exchange 및 Lync 간에 구성 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cd84-137">Server-to-server trust and authentication must be configured between the SharePoint Services Farm and Exchange and also between Exchange and Lync.</span></span> 
    
### <a name="description-of-components-in-the-diagram"></a><span data-ttu-id="5cd84-138">다이어그램의 구성 요소 설명</span><span class="sxs-lookup"><span data-stu-id="5cd84-138">Description of components in the diagram</span></span>

<span data-ttu-id="5cd84-139">이 다이어그램에서는 SharePoint 2013 엔터프라이즈 응용 프로그램 팜과 SharePoint 2013 서비스 팜의 두 서버 팜에 액세스 하는 쿼리를 보내는 사용자를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5cd84-139">The diagram shows a user sending a query, which accesses two server farms, a SharePoint 2013 Enterprise App Farm and a SharePoint 2013 Services Farm.</span></span> <span data-ttu-id="5cd84-140">Sharepoint Services 팜 인터페이스 2013를 사용 2013 하는 경우 (예를 들어, Lync 2013과의 인터페이스), Windows 파일 공유</span><span class="sxs-lookup"><span data-stu-id="5cd84-140">The SharePoint Services Farm interfaces with a SharePoint 2013 Content Farm, Exchange Server 2013 (which interfaces with Lync 2013), and Windows File Shares.</span></span> 
  
#### <a name="sharepoint-2013-enterprise-app-farm"></a><span data-ttu-id="5cd84-141">SharePoint 2013 엔터프라이즈 응용 프로그램 팜</span><span class="sxs-lookup"><span data-stu-id="5cd84-141">SharePoint 2013 Enterprise App Farm</span></span>

<span data-ttu-id="5cd84-142">SharePoint 2013 엔터프라이즈 응용 프로그램 팜에 포함 되는 구성 요소는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="5cd84-142">The SharePoint 2013 Enterprise App Farm contains the following components:</span></span> 
  
- <span data-ttu-id="5cd84-143">EDC</span><span class="sxs-lookup"><span data-stu-id="5cd84-143">EDC</span></span>
    
- <span data-ttu-id="5cd84-144">SSA 프록시</span><span class="sxs-lookup"><span data-stu-id="5cd84-144">SSA proxy</span></span> 
    
- <span data-ttu-id="5cd84-145">타이머 작업</span><span class="sxs-lookup"><span data-stu-id="5cd84-145">Timer job</span></span> 
    
<span data-ttu-id="5cd84-146">사용자가 보낸 쿼리 또는 작업이 엔터프라이즈 앱 팜의 EDC에 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cd84-146">A query or action sent by the user is sent to the EDC in the Enterprise App Farm.</span></span> <span data-ttu-id="5cd84-147">다음 작업이 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cd84-147">The following actions occur:</span></span> 
  
- <span data-ttu-id="5cd84-148">쿼리 또는 작업이 SSA 프록시로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cd84-148">The query or action goes to the SSA proxy.</span></span> 
    
- <span data-ttu-id="5cd84-149">SSA 프록시는 엔터프라이즈 앱 팜의 타이머 작업에 상태 쿼리 또는 응답을 보내며 SharePoint Services 팜의 SSA 서비스에도 상태 쿼리 또는 응답을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="5cd84-149">The SSA proxy sends a status query or response to the Timer job in the Enterprise App Farm, and it also sends a status query or response to the SSA service in the SharePoint Services Farm.</span></span> <span data-ttu-id="5cd84-150">여기에서 생성 되는 작업은 SharePoint Services 팜 관련 섹션에 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cd84-150">The actions that result from this are described in the section about the SharePoint Services Farm.</span></span> 
    
- <span data-ttu-id="5cd84-151">응답을 받으면 타이머 작업은 SSA 프록시 및 EDC에 대 한 응답을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="5cd84-151">When it receives a response, the Timer job sends the response to the SSA proxy and to the EDC.</span></span> 
    
- <span data-ttu-id="5cd84-152">쿼리나 작업의 결과가 EDC에서 사용자에 게 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cd84-152">Any results from the query or action are sent to the user from the EDC.</span></span> 
    
#### <a name="sharepoint-2013-services-farm"></a><span data-ttu-id="5cd84-153">SharePoint 2013 서비스 팜</span><span class="sxs-lookup"><span data-stu-id="5cd84-153">SharePoint 2013 Services Farm</span></span>

<span data-ttu-id="5cd84-154">SharePoint 2013 서비스 팜은 다음과 같은 구성 요소를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cd84-154">The SharePoint 2013 Services Farm contains the following components:</span></span> 
  
- <span data-ttu-id="5cd84-155">SSA 서비스</span><span class="sxs-lookup"><span data-stu-id="5cd84-155">SSA Service</span></span> 
    
- <span data-ttu-id="5cd84-156">검색 인덱스 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="5cd84-156">Search index database</span></span> 
    
- <span data-ttu-id="5cd84-157">SSA admin_db 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="5cd84-157">SSA admin_db database.</span></span> <span data-ttu-id="5cd84-158">이 데이터베이스의 Actions 테이블에 포함 된 내용: 보류 릴리스 보류 GetStatus</span><span class="sxs-lookup"><span data-stu-id="5cd84-158">The Actions Table in this database contains: Hold Release Hold GetStatus</span></span> 
    
- <span data-ttu-id="5cd84-159">EWS 프록시</span><span class="sxs-lookup"><span data-stu-id="5cd84-159">EWS proxy</span></span> 
    
<span data-ttu-id="5cd84-160">SharePoint 엔터프라이즈 앱 팜의 SSA 프록시가 SharePoint Services 팜의 SSA로 상태 쿼리를 보내면 다음 작업이 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cd84-160">When the SSA proxy in the SharePoint Enterprise App Farm sends a status query to the SSA in the SharePoint Services Farm, the following actions occur:</span></span> 
  
- <span data-ttu-id="5cd84-161">요청이 쿼리 인 경우 SSA는 검색 인덱스를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="5cd84-161">If the request is a query, the SSA consults the search index.</span></span> <span data-ttu-id="5cd84-162">검색 응답은 SSA로 반환 되 고 EDC를 통해 사용자에 게 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cd84-162">The discovery response is returned to the SSA and then to the user through the EDC.</span></span> 
    
- <span data-ttu-id="5cd84-163">요청이 쓰기 작업 인 경우 SSA 서비스는 admin_db에 게 write 작업을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="5cd84-163">If the request is a write action, the SSA service sends the write action to the SSA admin_db.</span></span> 
    
- <span data-ttu-id="5cd84-164">크롤링 및 응답 결과 요청이 SSA에서 SharePoint 2013 콘텐츠 팜으로 전송 되 고 응답이 SSA로 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cd84-164">A crawl and responding results request is sent from the SSA to the SharePoint 2013 Content Farm and a response is returned to the SSA.</span></span> 
    
- <span data-ttu-id="5cd84-165">크롤링 및 응답 결과 요청이 SSA에서 Windows 파일 공유로 전송 되 고 응답이 SSA로 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cd84-165">A crawl and responding results request is sent from the SSA to the Windows File Shares, and a response is returned to the SSA.</span></span> 
    
- <span data-ttu-id="5cd84-166">보류 중인 작업 (s), 응답 또는 상태 업데이트에 대 한 쿼리는 SSA에서 SharePoint 콘텐츠 팜의 SSA 프록시로 전송 되며 SSA에 대 한 응답이 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cd84-166">A query for pending action(s), responses, or status updates is sent from the SSA to the SSA proxy in the SharePoint Content Farm, and a response is returned to the SSA.</span></span> 
    
- <span data-ttu-id="5cd84-167">Exchange 작업/상태 요청은 SSA에서 EWS 프록시로 전송 되며 exchange 2013 서버의 exchange 웹 서비스로 Exchange 쿼리 동작/상태 요청을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="5cd84-167">An Exchange action/status request is sent from the SSA to the EWS proxy, which sends an Exchange Query action/status request to the Exchange Web Service on the Exchange 2013 server.</span></span> 
    
- <span data-ttu-id="5cd84-168">상태 쿼리/응답은 SSA에서 SSA로 전송 되 고 SSA로 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cd84-168">A status query/response is sent from the SSA to the SSA admin_db and is returned to the SSA.</span></span> 
    
- <span data-ttu-id="5cd84-169">보류 중인 실행 쿼리/응답은 SSA에서 SSA로 전송 되 고 SSA로 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cd84-169">A pending action query/response is sent from the SSA to the SSA admin_db and is returned to the SSA.</span></span> 
    
#### <a name="sharepoint-2013-content-farm"></a><span data-ttu-id="5cd84-170">SharePoint 2013 콘텐츠 팜</span><span class="sxs-lookup"><span data-stu-id="5cd84-170">SharePoint 2013 Content Farm</span></span>

<span data-ttu-id="5cd84-171">SharePoint 2013 콘텐츠 팜에 포함 되는 구성 요소는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="5cd84-171">The SharePoint 2013 Content Farm contains the following components:</span></span> 
  
- <span data-ttu-id="5cd84-172">SSA 프록시</span><span class="sxs-lookup"><span data-stu-id="5cd84-172">SSA proxy</span></span> 
    
- <span data-ttu-id="5cd84-173">타이머 작업</span><span class="sxs-lookup"><span data-stu-id="5cd84-173">Timer job</span></span> 
    
- <span data-ttu-id="5cd84-174">Contoso SharePoint 사이트</span><span class="sxs-lookup"><span data-stu-id="5cd84-174">Contoso SharePoint site</span></span> 
    
- <span data-ttu-id="5cd84-175">Contoso SharePoint 콘텐츠</span><span class="sxs-lookup"><span data-stu-id="5cd84-175">Contoso SharePoint content</span></span> 
    
<span data-ttu-id="5cd84-176">SharePoint Services 팜의 SSA가 SharePoint 콘텐츠 팜의 SSA 프록시로 상태 쿼리를 보내면 다음 작업이 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cd84-176">When the SSA in the SharePoint Services Farm sends a status query to the SSA Proxy in the SharePoint Content Farm, the following actions occur:</span></span> 
  
- <span data-ttu-id="5cd84-177">SharePoint 콘텐츠 팜의 SSA 프록시가 타이머 작업에 대 한 보류 중인 작업/상태 응답 쿼리를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="5cd84-177">The SSA proxy in the SharePoint Content Farm sends a query for pending actions/status response to the Timer job.</span></span> 
    
- <span data-ttu-id="5cd84-178">타이머 작업이 contoso sharepoint 사이트에 대 한 요청을 보내 Contoso SharePoint 콘텐츠를 검토 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cd84-178">The Timer job sends a request to the Contoso SharePoint site, which reviews the Contoso SharePoint content.</span></span> 
    
- <span data-ttu-id="5cd84-179">보류 중인 작업/상태 쿼리에 대 한 응답은 타이머 작업에서 SharePoint 콘텐츠 팜의 SSA 프록시로 전송 된 다음 SharePoint Services 팜의 SSA 서비스로 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cd84-179">The response to the pending actions/status query is sent from the Timer job to the SSA proxy in the SharePoint Content Farm, and then it is sent to the SSA service in the SharePoint Services Farm</span></span> 
    
#### <a name="exchange-2013"></a><span data-ttu-id="5cd84-180">Exchange 2013</span><span class="sxs-lookup"><span data-stu-id="5cd84-180">Exchange 2013</span></span>

<span data-ttu-id="5cd84-181">Exchange 2013 서버 구성 요소에는 Exchange 웹 서비스가 포함 되어 있으며 다음이 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cd84-181">The Exchange 2013 server component contains the Exchange Web Service and provides the following:</span></span> 
  
- <span data-ttu-id="5cd84-182">서버 간 트러스트/OAuth는 SharePoint 2013 콘텐츠 팜과 Exchange 2013 간에 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cd84-182">Server-to-server Trust/OAuth is handled between the SharePoint 2013 Content Farm and Exchange 2013.</span></span> 
    
- <span data-ttu-id="5cd84-183">서버 간 트러스트/OAuth는 Exchange 2013와 Lync 2013 사이에서 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cd84-183">Server-to-server Trust/OAuth is handled between Exchange 2013 and Lync 2013.</span></span> 
    
#### <a name="lync-2013"></a><span data-ttu-id="5cd84-184">Lync 2013</span><span class="sxs-lookup"><span data-stu-id="5cd84-184">Lync 2013</span></span>

<span data-ttu-id="5cd84-185">Lync 2013 구성 요소는 Lync 콘텐츠를 Exchange 2013에 보관 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cd84-185">The Lync 2013 component archives Lync content in Exchange 2013.</span></span> 
  
#### <a name="windows-file-shares"></a><span data-ttu-id="5cd84-186">Windows 파일 공유</span><span class="sxs-lookup"><span data-stu-id="5cd84-186">Windows File Shares</span></span>

<span data-ttu-id="5cd84-187">Windows 파일 공유 구성 요소는 SharePoint Services 팜의 SSA에 크롤링 결과를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cd84-187">The Windows File Shares component provides crawl results to the SSA in the SharePoint Services Farm.</span></span> 
  
### <a name="legend"></a><span data-ttu-id="5cd84-188">Legend</span><span class="sxs-lookup"><span data-stu-id="5cd84-188">Legend</span></span>

<span data-ttu-id="5cd84-189">이 다이어그램의 범례에는 다음과 같이 서로 다른 색으로 된 줄의 구성 요소에 표시 되는 다양 한 유형의 트래픽이 그래픽으로 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cd84-189">The legend for this diagram graphically shows the different types of traffic depicted among the components in different colored lines as follows:</span></span> 
  
- <span data-ttu-id="5cd84-190">연한 파란색 선: 쿼리/작업-eDiscovery 쿼리 또는 작업 데이터</span><span class="sxs-lookup"><span data-stu-id="5cd84-190">Light blue line: Query/action - eDiscovery query or action data</span></span> 
    
- <span data-ttu-id="5cd84-191">주황색 줄: eDisovery 응답-eDiscovery 쿼리 응답 데이터</span><span class="sxs-lookup"><span data-stu-id="5cd84-191">Orange line: eDisovery response - eDiscovery query response data</span></span> 
    
- <span data-ttu-id="5cd84-192">녹색 줄: 상태 쿼리/응답-eDiscovery 상태 쿼리/응답 데이터</span><span class="sxs-lookup"><span data-stu-id="5cd84-192">Green line: Status query/response - eDiscovery status query/response data</span></span> 
    
- <span data-ttu-id="5cd84-193">자주색 줄: Exchange 작업/상태 요청-Exchange 트래픽의 작업 상태에 대 한 eDiscovery 요청</span><span class="sxs-lookup"><span data-stu-id="5cd84-193">Purple line: Exchange action/status request - eDiscovery request for action status for Exchange traffic.</span></span> 
    
- <span data-ttu-id="5cd84-194">Red line: Exchange 데이터/상태 응답-Exchange 로부터의 eDiscovery 쿼리 또는 상태 응답입니다.</span><span class="sxs-lookup"><span data-stu-id="5cd84-194">Red line: Exchange data/status response - eDiscovery query or status response from Exchange.</span></span> 
    
- <span data-ttu-id="5cd84-195">점선 검정 줄: 서버 간 트러스트/Oauth</span><span class="sxs-lookup"><span data-stu-id="5cd84-195">Dotted black line: Server-to-Server Trust/Oauth</span></span> 
    
- <span data-ttu-id="5cd84-196">검정 실선 (크롤링/결과)</span><span class="sxs-lookup"><span data-stu-id="5cd84-196">Solid black line: Crawl/results</span></span> 
    

