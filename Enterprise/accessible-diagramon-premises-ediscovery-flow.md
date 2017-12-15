---
title: "액세스할 수 있는 다이어그램-온-프레미스 eDiscovery 흐름"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b9dcd692-0485-4eec-870d-87ab6b89d97b
description: "이 문서에는 온-프레미스 eDiscovery 흐름 라는 다이어그램의 액세스할 수 있는 텍스트 버전입니다."
ms.openlocfilehash: de94fc2af94df47a83f4a7847a84cd18131f637e
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2017
---
# <a name="accessible-diagram---on-premises-ediscovery-flow"></a><span data-ttu-id="f4523-103">액세스할 수 있는 다이어그램-온-프레미스 eDiscovery 흐름</span><span class="sxs-lookup"><span data-stu-id="f4523-103">Accessible diagram - On-premises eDiscovery Flow</span></span>

<span data-ttu-id="f4523-104">**요약:** 이 문서에는 온-프레미스 eDiscovery 흐름 라는 다이어그램의 액세스할 수 있는 텍스트 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="f4523-104">**Summary:** This article is an accessible text version of the diagram named On-premises eDiscovery Flow.</span></span>
  
<span data-ttu-id="f4523-105">이 포스터 서버 제품 간에 아키텍처 및 데이터 흐름에 대 한 세부 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f4523-105">This poster provides details about the architecture and flow of data across server products.</span></span> 
  
## <a name="across-sharepoint-exchange-lync-and-file-shares"></a><span data-ttu-id="f4523-106">SharePoint, Exchange, Lync 및 파일 공유에 걸쳐</span><span class="sxs-lookup"><span data-stu-id="f4523-106">Across SharePoint, Exchange, Lync, and file shares</span></span>

<span data-ttu-id="f4523-p101">다이어그램은 두 서버 팜, SharePoint 2013 엔터프라이즈 응용 프로그램 팜, 및 SharePoint 2013 서비스 팜에 액세스 하는 쿼리를 보내는 사용자를 보여줍니다. SharePoint 2013 콘텐츠 팜, (하는 Lync 2013와 통신 하는) Exchange Server 2013와 통신 하 고 SharePoint 2013 서비스 팜 및 Windows 파일 공유 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4523-p101">The diagram shows a user sending a query that accesses two server farms, a SharePoint 2013 Enterprise App Farm, and a SharePoint 2013 Services Farm. The SharePoint 2013 Services Farm communicates with a SharePoint 2013 Content Farm, Exchange Server 2013 (which communicates with Lync 2013), and Windows File Shares.</span></span> 
  
<span data-ttu-id="f4523-109">EDiscovery 흐름 목록 데이터 및 순서는 eDisovery에서 쿼리 작업 SharePoint, Exchange, Lync 간에 발생 하 고 파일 공유의 흐름을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4523-109">The eDiscovery Flow List describes the flow of data and the order in which eDisovery query actions occur across SharePoint, Exchange, Lync, and file shares.</span></span> 
  
<span data-ttu-id="f4523-110">EDiscovery 흐름 목록에에서 설명 되어 크기로 먼저, 다이어그램에 표시 된 기능에 대 한 자세한 설명을 앞에 오는 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4523-110">The eDiscovery flow list is described in detail first, followed by a detailed description of the features depicted in the diagram.</span></span> 
  
### <a name="ediscovery-flow-list"></a><span data-ttu-id="f4523-111">eDiscovery 흐름 목록</span><span class="sxs-lookup"><span data-stu-id="f4523-111">eDiscovery Flow List</span></span>

<span data-ttu-id="f4523-p102">각이 목록에 설명 된 단계에 대 한 숫자는 다이어그램에 표시 된 단계와 관련이 있습니다. 다이어그램은이 문서 뒷부분에서 자세히 설명 되어있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4523-p102">The numbers for each of the steps described in this list pertain to a step depicted in the diagram. The diagram is described in detail later in this document.</span></span> 
  
1. <span data-ttu-id="f4523-p103">eDiscovery 사례 생성 하 고 관리, 하 고는 EDC (eDiscovery 센터)에서 사용 됩니다. EDC는 SharePoint 2013 사이트 모음입니다. 이 고 여기서의 경우 정의 된를 추적할 수 있는 원본을 식별 된, 쿼리가 실행 됩니다, 쿼리 결과 검토 하는 콘텐츠에 보류는 배치 되거나 제거 된입니다.</span><span class="sxs-lookup"><span data-stu-id="f4523-p103">eDiscovery cases are created, managed, and used in the eDiscovery center (EDC). The EDC is a SharePoint 2013 site collection. This is where cases are defined, sources to be tracked are identified, queries are issued, query results are reviewed, and holds on content are placed or removed.</span></span> 
    
2. <span data-ttu-id="f4523-p104">EDiscovery 쿼리 또는 보류, ReleaseHold, 또는 GetStatus, 원본 위치와 같은 작업을 엔터프라이즈 응용 프로그램 팜의 검색 서비스 응용 프로그램 (SSA) 프록시는 EDC에서 릴레이 됩니다. SSA 프록시에는 다음 서비스 응용 프로그램 팜의 SSA에 트래픽을 릴레이합니다. 이 예제에서는 요청 "contoso" SharePoint 콘텐츠 팜에서 아무것도 시키려면 대기 파일 이름에는 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4523-p104">The eDiscovery query or action, such as place a Hold, ReleaseHold, or GetStatus, is relayed from the EDC to the Search Service Application (SSA) proxy in the Enterprise App Farm. The SSA proxy then relays the traffic to the SSA in the Services App Farm. In this example, the request is to place anything in the SharePoint Content Farm with "CONTOSO" in the file name on hold.</span></span> 
    
3. <span data-ttu-id="f4523-p105">사례를 쿼리 하는 요청이 인 경우 SSA와 같은 검색 인덱스를 참조 합니다. 그런 다음, eDiscovery 쿼리 결과 집합의 EDC 통해 사용자에 게 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f4523-p105">If the request is to query a case, the SSA consults the search index. Then, the eDiscovery query result set returns to the user through the EDC.</span></span> 
    
4. <span data-ttu-id="f4523-p106">요청은 대기 또는 ReleaseHold, 위치 등의 작업을 하는 경우 해당 작업 Actions_Table SSA 관리 데이터베이스에 기록 됩니다. 이 예제에서는 "contoso" SharePoint 콘텐츠 팜에서에 들어 있는 개체에 대 한 보류 요청은 Actions_Table에 기록 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4523-p106">If the request is an action, such as place a Hold or ReleaseHold, that action is written to the Actions_Table in the SSA Administrative database. In this example, a hold request for anything in the SharePoint Content Farm with "CONTOSO" is written to the Actions_Table.</span></span> 
    
5. <span data-ttu-id="f4523-124">일정 한 간격으로 콘텐츠 팜 eDiscovery 전체 보류에서 타이머 작업 활성화 되어 하 고 보류 중인 작업에 대 한 요청을 생성 하 고 SSA에 SSA 프록시를 통해 상태 업데이트를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="f4523-124">At regular intervals the Content Farm eDiscovery in-place hold timer job wakes up and generates a request for pending actions and sends status updates through the SSA proxy to the SSA.</span></span> 
    
6. <span data-ttu-id="f4523-p107">보류 중인 작업에 대 한 쿼리는 Action_Table 보류 중인 콘텐츠 팜에 대 한 작업에 대 한 참조 하는 중앙 SSA 릴레이 됩니다. 또한 콘텐츠 팜 원본 위치 유지 타이머 작업이 개체와는 ActionsTable에 기록 되는 처리가 수신 하는 작업에 대 한 상태 업데이트를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="f4523-p107">The query for pending actions is relayed to the central SSA, which consults the Action_Table for any pending actions for the Content Farm. The Content Farm in-place hold timer job also sends status updates for objects and actions it has received, which are written to the ActionsTable.</span></span> 
    
7. <span data-ttu-id="f4523-127">SharePoint 2013 콘텐츠 팜의 이름에 "contoso" 모든 콘텐츠에 대 한 보류 요청 콘텐츠 팜에 있는 eDiscovery의 원본 위치 유지 타이머 작업을 SSA에서 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4523-127">The hold request for any content with "CONTOSO" in the name in the SharePoint 2013 Content Farm is sent by the SSA to the eDiscovery in-place hold timer job in the Content Farm.</span></span> 
    
8. <span data-ttu-id="f4523-128">eDiscovery 원본 위치 유지 타이머 작업 places "CONTOSO 사이트" 및 "CONTOSO content"에 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4523-128">The eDiscovery in-place hold timer job places the "CONTOSO Site" and "CONTOSO content" on hold.</span></span> 
    
9. <span data-ttu-id="f4523-129">엔터프라이즈 응용 프로그램 팜의 검색 작업의 상태를 확인 하 고 상태를 업데이트 하려면 eDiscovery 원본 위치 유지 타이머 작업이 정기적으로 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4523-129">The eDiscovery in-place hold timer job periodically runs in the Enterprise App Farm to check the status of discovery actions and to update the status.</span></span> 
    
10. <span data-ttu-id="f4523-130">상태 쿼리는 SharePoint Services 팜 SSA에 엔터프라이즈 응용 프로그램 팜의 SSA 프록시를 통해 릴레이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4523-130">The status query is relayed through the Enterprise App Farm SSA proxy to the SharePoint Services Farm SSA.</span></span> 
    
11. <span data-ttu-id="f4523-131">SSA 작업 테이블에서 상태를 검색 하 고는 EDC에 상태 업데이트를 올려놓습니다 하는 엔터프라이즈 응용 프로그램 팜의 타이머 작업을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4523-131">The SSA retrieves the status from the Actions table and returns it to the timer job in the Enterprise App Farm, which pushes the status updates to the EDC.</span></span> 
    
12. <span data-ttu-id="f4523-p108">때 eDiscovery 사용자가 검색 (또는 작업을 수행) 사서함 또는 보관 된 Lync 콘텐츠 등의 Exchange 원본에 대 한 중앙 SSA를 사용 하 여 Exchange 웹 서비스 쿼리를 Exchange 웹 서비스 (EWS) 프록시 합니다. Exchange 자체 검색 및 eDiscovery 인프라 있으며 eDiscovery에 대 한 모든 호출을 내부적으로 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4523-p108">When the eDiscovery user is searching (or performing an action) for Exchange sources, such as a mailbox or archived Lync content, the central SSA uses Exchange Web Services (EWS) proxy to query Exchange Web Services. Exchange has its own search and eDiscovery infrastructure and manages all eDiscovery calls internally.</span></span> 
    
13. <span data-ttu-id="f4523-134">Exchange 웹 서비스는 eDiscovery 검색 결과 또는 EDC 사람에 게 차례로 릴레이 가져옵니다 하는 쿼리 기반 보존에 대 한 상태 요청에 대 한 응답 SSA에 응답 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4523-134">Exchange Web Services responds to SSA with eDiscovery search results or a response to a status request for a query-based hold, which, in turn, gets relayed to the EDC.</span></span> 
    
#### <a name="prerequisites"></a><span data-ttu-id="f4523-135">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="f4523-135">Prerequisites</span></span>

- <span data-ttu-id="f4523-136">SharePoint 엔터프라이즈 검색 구성, 검색 크롤링을 콘텐츠 원본 (SharePoint 및 Windows 파일 공유)에 성공적으로 발생 하는, 되 고 되어야 인덱스에는 모든 콘텐츠 원본입니다.</span><span class="sxs-lookup"><span data-stu-id="f4523-136">SharePoint Enterprise Search must be configured, search crawls on content sources (SharePoint and Windows file shares) are successfully occurring, and all content sources are in the index.</span></span> 
    
- <span data-ttu-id="f4523-137">SharePoint Services 팜 사이의 Exchange 및 Exchange 및 Lync 간의 서버 간 트러스트 및 인증을 구성 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4523-137">Server-to-server trust and authentication must be configured between the SharePoint Services Farm and Exchange and also between Exchange and Lync.</span></span> 
    
### <a name="description-of-components-in-the-diagram"></a><span data-ttu-id="f4523-138">구성 요소는 다이어그램에 대 한 설명</span><span class="sxs-lookup"><span data-stu-id="f4523-138">Description of components in the diagram</span></span>

<span data-ttu-id="f4523-p109">다이어그램은 두 서버 팜, SharePoint 2013 엔터프라이즈 응용 프로그램 팜 및 SharePoint 2013 서비스 팜에 액세스 하는 쿼리를 보내는 사용자를 보여줍니다. SharePoint 2013 콘텐츠 팜, (하는 인터페이스 (영문) Lync 2013과 함께) Exchange Server 2013, SharePoint Services 팜 교류 및 Windows 파일 공유 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4523-p109">The diagram shows a user sending a query, which accesses two server farms, a SharePoint 2013 Enterprise App Farm and a SharePoint 2013 Services Farm. The SharePoint Services Farm interfaces with a SharePoint 2013 Content Farm, Exchange Server 2013 (which interfaces with Lync 2013), and Windows File Shares.</span></span> 
  
#### <a name="sharepoint-2013-enterprise-app-farm"></a><span data-ttu-id="f4523-141">SharePoint 2013 엔터프라이즈 응용 프로그램 팜</span><span class="sxs-lookup"><span data-stu-id="f4523-141">SharePoint 2013 Enterprise App Farm</span></span>

<span data-ttu-id="f4523-142">SharePoint 2013 엔터프라이즈 응용 프로그램 팜의 다음과 같은 구성 요소가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4523-142">The SharePoint 2013 Enterprise App Farm contains the following components:</span></span> 
  
- <span data-ttu-id="f4523-143">EDC</span><span class="sxs-lookup"><span data-stu-id="f4523-143">EDC</span></span>
    
- <span data-ttu-id="f4523-144">SSA 프록시</span><span class="sxs-lookup"><span data-stu-id="f4523-144">SSA proxy</span></span> 
    
- <span data-ttu-id="f4523-145">타이머 작업</span><span class="sxs-lookup"><span data-stu-id="f4523-145">Timer job</span></span> 
    
<span data-ttu-id="f4523-p110">쿼리 또는 사용자가 보낸 작업이 엔터프라이즈 응용 프로그램 팜의 EDC에 전송 됩니다. 다음과 같은 작업이 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4523-p110">A query or action sent by the user is sent to the EDC in the Enterprise App Farm. The following actions occur:</span></span> 
  
- <span data-ttu-id="f4523-148">쿼리 또는 동작 SSA 프록시로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4523-148">The query or action goes to the SSA proxy.</span></span> 
    
- <span data-ttu-id="f4523-p111">SSA 프록시 엔터프라이즈 응용 프로그램 팜의 상태 쿼리 또는 타이머 작업에 대 한 응답을 전송 하 고도 보냅니다 상태 쿼리 또는 SSA 서비스에 대 한 응답 SharePoint Services 팜의. 이 통해 생성 되는 작업은 SharePoint Services 팜 하는 방법에 대 한 섹션에 설명 되어있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4523-p111">The SSA proxy sends a status query or response to the Timer job in the Enterprise App Farm, and it also sends a status query or response to the SSA service in the SharePoint Services Farm. The actions that result from this are described in the section about the SharePoint Services Farm.</span></span> 
    
- <span data-ttu-id="f4523-151">응답을 받으면 SSA 프록시 하 고는 EDC 타이머 작업에 대 한 응답을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="f4523-151">When it receives a response, the Timer job sends the response to the SSA proxy and to the EDC.</span></span> 
    
- <span data-ttu-id="f4523-152">쿼리 또는 작업에서 모든 결과 EDC에서 사용자에 게 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4523-152">Any results from the query or action are sent to the user from the EDC.</span></span> 
    
#### <a name="sharepoint-2013-services-farm"></a><span data-ttu-id="f4523-153">SharePoint 2013 서비스 팜</span><span class="sxs-lookup"><span data-stu-id="f4523-153">SharePoint 2013 Services Farm</span></span>

<span data-ttu-id="f4523-154">SharePoint 2013 서비스 팜은 다음과 같은 구성 요소가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4523-154">The SharePoint 2013 Services Farm contains the following components:</span></span> 
  
- <span data-ttu-id="f4523-155">SSA 서비스</span><span class="sxs-lookup"><span data-stu-id="f4523-155">SSA Service</span></span> 
    
- <span data-ttu-id="f4523-156">검색 인덱스 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="f4523-156">Search index database</span></span> 
    
- <span data-ttu-id="f4523-p112">SSA admin_db 데이터베이스입니다. 이 데이터베이스에서 작업 테이블에는 포함: 릴리스 유지 GetStatus 유지</span><span class="sxs-lookup"><span data-stu-id="f4523-p112">SSA admin_db database. The Actions Table in this database contains: Hold Release Hold GetStatus</span></span> 
    
- <span data-ttu-id="f4523-159">EWS 프록시</span><span class="sxs-lookup"><span data-stu-id="f4523-159">EWS proxy</span></span> 
    
<span data-ttu-id="f4523-160">SharePoint 엔터프라이즈 응용 프로그램 팜의 SSA 프록시 SharePoint Services 팜의 SSA를 상태 쿼리를 보내면 다음 작업이 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4523-160">When the SSA proxy in the SharePoint Enterprise App Farm sends a status query to the SSA in the SharePoint Services Farm, the following actions occur:</span></span> 
  
- <span data-ttu-id="f4523-p113">쿼리 요청을 사용 하는 경우 SSA와 같은 검색 인덱스를 참조 합니다. 검색에 대 한 응답 SSA 이동한 다음는 EDC 통해 사용자에 게 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4523-p113">If the request is a query, the SSA consults the search index. The discovery response is returned to the SSA and then to the user through the EDC.</span></span> 
    
- <span data-ttu-id="f4523-163">요청은 쓰기 작업을 하는 경우 SSA 서비스 SSA admin_db 하는 쓰기 작업을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="f4523-163">If the request is a write action, the SSA service sends the write action to the SSA admin_db.</span></span> 
    
- <span data-ttu-id="f4523-164">크롤링 및 응답 SSA에서 SharePoint 2013 콘텐츠 팜 결과 요청이 전송 되 고 응답 SSA에 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4523-164">A crawl and responding results request is sent from the SSA to the SharePoint 2013 Content Farm and a response is returned to the SSA.</span></span> 
    
- <span data-ttu-id="f4523-165">크롤링 및 응답 결과 요청이 Windows 파일 공유로 SSA에서 전송 되 고 응답 SSA에 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4523-165">A crawl and responding results request is sent from the SSA to the Windows File Shares, and a response is returned to the SSA.</span></span> 
    
- <span data-ttu-id="f4523-166">SharePoint 콘텐츠 팜에서 SSA 프록시에 SSA에서 보내는 동작, 응답 또는 상태 업데이트가 보류 중인에 대 한 쿼리 및 응답 SSA로 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4523-166">A query for pending action(s), responses, or status updates is sent from the SSA to the SSA proxy in the SharePoint Content Farm, and a response is returned to the SSA.</span></span> 
    
- <span data-ttu-id="f4523-167">Exchange 2013 서버에서 Exchange 웹 서비스에는 Exchange 쿼리 작업/상태 요청을 전송 하는 EWS 프록시에는 Exchange 작업/상태 요청이 SSA에서 보내집니다.</span><span class="sxs-lookup"><span data-stu-id="f4523-167">An Exchange action/status request is sent from the SSA to the EWS proxy, which sends an Exchange Query action/status request to the Exchange Web Service on the Exchange 2013 server.</span></span> 
    
- <span data-ttu-id="f4523-168">상태 쿼리/응답 SSA에서 SSA admin_db에 전송 되 고 SSA에 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4523-168">A status query/response is sent from the SSA to the SSA admin_db and is returned to the SSA.</span></span> 
    
- <span data-ttu-id="f4523-169">보류 중인 작업 쿼리/응답 SSA에서 SSA admin_db에 전송 되 고 SSA에 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4523-169">A pending action query/response is sent from the SSA to the SSA admin_db and is returned to the SSA.</span></span> 
    
#### <a name="sharepoint-2013-content-farm"></a><span data-ttu-id="f4523-170">SharePoint 2013 콘텐츠 팜</span><span class="sxs-lookup"><span data-stu-id="f4523-170">SharePoint 2013 Content Farm</span></span>

<span data-ttu-id="f4523-171">SharePoint 2013 콘텐츠 팜 다음과 같은 구성 요소가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4523-171">The SharePoint 2013 Content Farm contains the following components:</span></span> 
  
- <span data-ttu-id="f4523-172">SSA 프록시</span><span class="sxs-lookup"><span data-stu-id="f4523-172">SSA proxy</span></span> 
    
- <span data-ttu-id="f4523-173">타이머 작업</span><span class="sxs-lookup"><span data-stu-id="f4523-173">Timer job</span></span> 
    
- <span data-ttu-id="f4523-174">Contoso SharePoint 사이트</span><span class="sxs-lookup"><span data-stu-id="f4523-174">Contoso SharePoint site</span></span> 
    
- <span data-ttu-id="f4523-175">Contoso SharePoint 콘텐츠</span><span class="sxs-lookup"><span data-stu-id="f4523-175">Contoso SharePoint content</span></span> 
    
<span data-ttu-id="f4523-176">SharePoint Services 팜의 SSA가 SharePoint 콘텐츠 팜에서 SSA 프록시에 상태 쿼리를 보낼 때 다음 작업이 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4523-176">When the SSA in the SharePoint Services Farm sends a status query to the SSA Proxy in the SharePoint Content Farm, the following actions occur:</span></span> 
  
- <span data-ttu-id="f4523-177">SharePoint 콘텐츠 팜에서 SSA 프록시에 대 한 타이머 작업에 대 한 작업/상태 응답 보류 중인 쿼리를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="f4523-177">The SSA proxy in the SharePoint Content Farm sends a query for pending actions/status response to the Timer job.</span></span> 
    
- <span data-ttu-id="f4523-178">타이머 작업 Contoso SharePoint 사이트로 Contoso SharePoint 콘텐츠를 검토 하는 요청을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="f4523-178">The Timer job sends a request to the Contoso SharePoint site, which reviews the Contoso SharePoint content.</span></span> 
    
- <span data-ttu-id="f4523-179">SharePoint 콘텐츠 팜에서 SSA 프록시에 대 한 응답을 보류 중인 작업/상태 쿼리 타이머 작업에서 보내는 하 고이 SharePoint Services 팜의 SSA 서비스에 전달 되는 다음</span><span class="sxs-lookup"><span data-stu-id="f4523-179">The response to the pending actions/status query is sent from the Timer job to the SSA proxy in the SharePoint Content Farm, and then it is sent to the SSA service in the SharePoint Services Farm</span></span> 
    
#### <a name="exchange-2013"></a><span data-ttu-id="f4523-180">Exchange 2013</span><span class="sxs-lookup"><span data-stu-id="f4523-180">Exchange 2013</span></span>

<span data-ttu-id="f4523-181">Exchange 2013 서버 구성 요소에서 Exchange 웹 서비스를 포함 하 고 다음을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4523-181">The Exchange 2013 server component contains the Exchange Web Service and provides the following:</span></span> 
  
- <span data-ttu-id="f4523-182">SharePoint 2013 콘텐츠 팜 사이의 Exchange 2013 서버 간 트러스트/OAuth 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4523-182">Server-to-server Trust/OAuth is handled between the SharePoint 2013 Content Farm and Exchange 2013.</span></span> 
    
- <span data-ttu-id="f4523-183">Exchange 2013 및 Lync 2013 간에 서버간-신뢰/OAuth 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4523-183">Server-to-server Trust/OAuth is handled between Exchange 2013 and Lync 2013.</span></span> 
    
#### <a name="lync-2013"></a><span data-ttu-id="f4523-184">Lync 2013</span><span class="sxs-lookup"><span data-stu-id="f4523-184">Lync 2013</span></span>

<span data-ttu-id="f4523-185">Lync 2013 구성 요소 Lync 콘텐츠 Exchange 2013를 보관합니다.</span><span class="sxs-lookup"><span data-stu-id="f4523-185">The Lync 2013 component archives Lync content in Exchange 2013.</span></span> 
  
#### <a name="windows-file-shares"></a><span data-ttu-id="f4523-186">Windows 파일 공유</span><span class="sxs-lookup"><span data-stu-id="f4523-186">Windows File Shares</span></span>

<span data-ttu-id="f4523-187">SharePoint Services 팜의 SSA에 크롤링 결과 제공 하는 Windows 파일 공유 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="f4523-187">The Windows File Shares component provides crawl results to the SSA in the SharePoint Services Farm.</span></span> 
  
### <a name="legend"></a><span data-ttu-id="f4523-188">범례</span><span class="sxs-lookup"><span data-stu-id="f4523-188">Legend</span></span>

<span data-ttu-id="f4523-189">이 다이어그램에 대 한 범례 다양 한 유형의 다음과 같이 서로 다른 색이 지정 된 줄의 구성 요소 중에서 설명 하는 트래픽을 그래픽으로 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="f4523-189">The legend for this diagram graphically shows the different types of traffic depicted among the components in different colored lines as follows:</span></span> 
  
- <span data-ttu-id="f4523-190">연한 파랑 선: 쿼리/작업-eDiscovery 쿼리 또는 동작 데이터</span><span class="sxs-lookup"><span data-stu-id="f4523-190">Light blue line: Query/action - eDiscovery query or action data</span></span> 
    
- <span data-ttu-id="f4523-191">주황색 줄: eDisovery 응답-eDiscovery 쿼리 응답 데이터</span><span class="sxs-lookup"><span data-stu-id="f4523-191">Orange line: eDisovery response - eDiscovery query response data</span></span> 
    
- <span data-ttu-id="f4523-192">선 녹색: 상태 쿼리/응답-eDiscovery 상태 쿼리/응답 데이터</span><span class="sxs-lookup"><span data-stu-id="f4523-192">Green line: Status query/response - eDiscovery status query/response data</span></span> 
    
- <span data-ttu-id="f4523-193">선 보라색: Exchange 작업/상태 요청-Exchange 트래픽에 대 한 작업 상태에 대 한 eDiscovery 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4523-193">Purple line: Exchange action/status request - eDiscovery request for action status for Exchange traffic.</span></span> 
    
- <span data-ttu-id="f4523-194">빨간색 선: 데이터/상태 응답-Exchange Exchange에서 eDiscovery 쿼리 또는 상태 응답 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4523-194">Red line: Exchange data/status response - eDiscovery query or status response from Exchange.</span></span> 
    
- <span data-ttu-id="f4523-195">검정 선 점선: 서버 간 트러스트/Oauth</span><span class="sxs-lookup"><span data-stu-id="f4523-195">Dotted black line: Server-to-Server Trust/Oauth</span></span> 
    
- <span data-ttu-id="f4523-196">검정 실선: 크롤링/결과</span><span class="sxs-lookup"><span data-stu-id="f4523-196">Solid black line: Crawl/results</span></span> 
    

