---
title: "Azure PaaS에 대 한 하이브리드 클라우드 시나리오"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 5f4f5d0d-4638-48e8-a517-bd804856b617
description: "요약: 경우 서비스로 (PaaS) Microsoft의 플랫폼에 대 한 하이브리드 아키텍처 및 시나리오 이해-Azure의 클라우드 서비스를 기반으로 합니다."
ms.openlocfilehash: 96548b74341474ff2bd0720f982cbdba96b06e4b
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/09/2018
---
# <a name="hybrid-cloud-scenarios-for-azure-paas"></a><span data-ttu-id="bf6a1-103">Azure PaaS에 대 한 하이브리드 클라우드 시나리오</span><span class="sxs-lookup"><span data-stu-id="bf6a1-103">Hybrid cloud scenarios for Azure PaaS</span></span>

 <span data-ttu-id="bf6a1-104">**요약:** 서비스로 (PaaS) Microsoft의 플랫폼에 대 한 하이브리드 아키텍처 및 시나리오 이해-Azure의 클라우드 서비스를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf6a1-104">**Summary:** Understand the hybrid architecture and scenarios for Microsoft's Platform as a Service (PaaS)-based cloud offerings in Azure.</span></span>
  
<span data-ttu-id="bf6a1-105">온-프레미스 데이터를 결합 하 또는 새롭거나 변환 된 응용 프로그램의 기능을 사용할 수 있는 Azure PaaS에서 실행 중인 컴퓨팅 리소스 클라우드 성능, 안정성 및 확장 하 고 모바일 사용자를 위한 향상 된 지원을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf6a1-105">Combine on-premises data or computing resources with new or converted applications running in Azure PaaS, which can take advantage of cloud performance, reliability, and scale and provide better support for mobile users.</span></span> 
  
## <a name="azure-paas-hybrid-scenario-architecture"></a><span data-ttu-id="bf6a1-106">Azure PaaS 하이브리드 시나리오 아키텍처</span><span class="sxs-lookup"><span data-stu-id="bf6a1-106">Azure PaaS hybrid scenario architecture</span></span>

<span data-ttu-id="bf6a1-107">그림 1 Azure의 Microsoft PaaS 기반 하이브리드 시나리오의 아키텍처를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="bf6a1-107">Figure 1 shows the architecture of Microsoft PaaS-based hybrid scenarios in Azure.</span></span>
  
<span data-ttu-id="bf6a1-108">**Azure의 그림 1: Microsoft PaaS 기반 하이브리드 시나리오**</span><span class="sxs-lookup"><span data-stu-id="bf6a1-108">**Figure 1: Microsoft PaaS-based hybrid scenarios in Azure**</span></span>

![Azure의 Microsoft PaaS 기반 하이브리드 시나리오](images/Hybrid_Poster/Hybrid_Cloud_Stack_PaaS.png)
  
<span data-ttu-id="bf6a1-110">아키텍처의 각 레이어에:</span><span class="sxs-lookup"><span data-stu-id="bf6a1-110">For each layer of the architecture:</span></span>
  
- <span data-ttu-id="bf6a1-111">앱 및 시나리오</span><span class="sxs-lookup"><span data-stu-id="bf6a1-111">Apps and scenarios</span></span>
    
    <span data-ttu-id="bf6a1-112">하이브리드 PaaS 응용 프로그램을 Azure에서 실행 하 고 온-프레미스 compute 또는 저장소 리소스를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf6a1-112">A hybrid PaaS application runs in Azure and uses on-premises compute or storage resources.</span></span>
    
- <span data-ttu-id="bf6a1-113">Identity</span><span class="sxs-lookup"><span data-stu-id="bf6a1-113">Identity</span></span>
    
    <span data-ttu-id="bf6a1-114">디렉터리 동기화 또는 타사 id 공급자와의 페더레이션을 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf6a1-114">Consists of either directory synchronization or federation with a third-party identity provider.</span></span>
    
- <span data-ttu-id="bf6a1-115">네트워크</span><span class="sxs-lookup"><span data-stu-id="bf6a1-115">Network</span></span>
    
    <span data-ttu-id="bf6a1-p101">기존 인터넷 파이프 대화 또는 Azure PaaS에 공용 피어 링와 ExpressRoute 연결으로 구성 됩니다. Azure PaaS 응용 프로그램 온-프레미스 compute 또는 저장소 리소스에 액세스 하는 방법을 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf6a1-p101">Consists of either your existing Internet pipe or an ExpressRoute connection with public peering to Azure PaaS. You must include a way for the Azure PaaS application to access the on-premises compute or storage resource.</span></span>
    
- <span data-ttu-id="bf6a1-118">온-프레미스</span><span class="sxs-lookup"><span data-stu-id="bf6a1-118">On-premises</span></span>
    
    <span data-ttu-id="bf6a1-119">Id 및 보안 인프라 및 기간 업무 (LOB) 응용 프로그램 또는 Azure PaaS 응용 프로그램에 안전 하 게 액세스할 수 있는 데이터베이스 서버를 기존 줄으로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf6a1-119">Consists of identity and security infrastructure and existing line of business (LOB) applications or database servers, which an Azure PaaS application can securely access.</span></span>
    
## <a name="azure-paas-hybrid-application"></a><span data-ttu-id="bf6a1-120">Azure PaaS 하이브리드 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="bf6a1-120">Azure PaaS hybrid application</span></span>

<span data-ttu-id="bf6a1-121">그림 2 Azure에서 실행 되는 하이브리드 응용 프로그램의 구성을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="bf6a1-121">Figure 2 shows the configuration of a hybrid application running in Azure.</span></span>
  
<span data-ttu-id="bf6a1-122">**그림 2: Azure PaaS 기반 하이브리드 응용 프로그램**</span><span class="sxs-lookup"><span data-stu-id="bf6a1-122">**Figure 2: Azure PaaS-based hybrid application**</span></span>

![Azure PaaS 기반 하이브리드 응용 프로그램](images/Hybrid_Poster/Hybrid_Cloud_Stack_PaaS_Apps.png)
  
<span data-ttu-id="bf6a1-p102">그림 2의 온-프레미스 네트워크 저장소 또는 서버와 프록시 서버를 포함 하는 DMZ에서 앱을 호스팅합니다. 인터넷을 통해 나 ExpressRoute 연결을 사용 하 여 Azure PaaS 서비스에 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf6a1-p102">In Figure 2, an on-premises network hosts storage or apps on servers and a DMZ containing a proxy server. It is connected to Azure PaaS services either over the Internet or with an ExpressRoute connection.</span></span>
  
<span data-ttu-id="bf6a1-126">조직 수 하 여 Azure PaaS 하이브리드 응용 프로그램에 사용할 수 있는 compute 또는 저장소 리소스를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf6a1-126">An organization can make its compute or storage resources available to the Azure PaaS hybrid application by:</span></span>
  
- <span data-ttu-id="bf6a1-127">DMZ 서버에서 리소스를 호스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf6a1-127">Hosting the resource on servers in the DMZ.</span></span>
    
- <span data-ttu-id="bf6a1-128">있는 온-프레미스 리소스에 대 한 인증 된, 인바운드, HTTPS 기반 요청을 허용 하는 DMZ에 역방향 프록시 서버를 호스팅, 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf6a1-128">Hosting a reverse proxy server in the DMZ, which allows authenticated, inbound, HTTPS-based requests to the resource that is located on-premises.</span></span>
    
<span data-ttu-id="bf6a1-129">Azure 응용 프로그램에서 자격 증명을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf6a1-129">The Azure app can use credentials from:</span></span>
  
- <span data-ttu-id="bf6a1-130">Windows Server AD와 같은 하도록 온-프레미스 id 공급자와 동기화 할 수 있는 azure AD</span><span class="sxs-lookup"><span data-stu-id="bf6a1-130">Azure AD, which can be synchronized with your on-premises identity provider, such as Windows Server AD.</span></span>
    
- <span data-ttu-id="bf6a1-131">타사 id 공급자입니다.</span><span class="sxs-lookup"><span data-stu-id="bf6a1-131">A third-party identity provider.</span></span>
    
### <a name="example-azure-paas-hybrid-application"></a><span data-ttu-id="bf6a1-132">예제 Azure PaaS 하이브리드 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="bf6a1-132">Example Azure PaaS hybrid application</span></span>

<span data-ttu-id="bf6a1-133">그림 3은 Azure에서 실행 하는 예제 하이브리드 응용 프로그램을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="bf6a1-133">Figure 3 shows an example hybrid application running in Azure.</span></span>
  
<span data-ttu-id="bf6a1-134">**그림 3: 예 Azure PaaS 기반 하이브리드 응용 프로그램**</span><span class="sxs-lookup"><span data-stu-id="bf6a1-134">**Figure 3: An example Azure PaaS-based hybrid application**</span></span>

![Azure PaaS 기반 하이브리드 응용 프로그램 예제](images/Hybrid_Poster/Hybrid_Cloud_Stack_PaaS_Apps_Ex.png)
  
<span data-ttu-id="bf6a1-p103">그림 3에서는 LOB 프로그램는 온-프레미스 네트워크 호스트 app. Azure PaaS 사용자 지정 모바일 응용을 프로그램을 호스팅합니다. 인터넷에서 smartphone 온-프레미스 LOB 응용 프로그램에 데이터 요청을 보내는 Azure에서 사용자 지정 모바일 응용 프로그램에 액세스 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf6a1-p103">In Figure 3, an on-premises network hosts an LOB app. Azure PaaS hosts a custom mobile app. A smartphone on the Internet accesses the custom mobile app in Azure, which sends data requests to the on-premises LOB app.</span></span>
  
<span data-ttu-id="bf6a1-p104">이 예제에서는 Azure PaaS 하이브리드 응용 프로그램은 직원에 최신 연락처 정보를 제공 하는 사용자 지정 모바일 응용 프로그램입니다. 끝-하이브리드 시나리오는 다음으로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf6a1-p104">This example Azure PaaS hybrid application is a custom mobile app that provides up-to-date contact information on employees. The end-to-end hybrid scenario consists of:</span></span>
  
- <span data-ttu-id="bf6a1-141">Smartphone 응용 프로그램에 필요한 유효성을 검사를 실행 하려면 온-프레미스 자격 증명입니다.</span><span class="sxs-lookup"><span data-stu-id="bf6a1-141">A smartphone app that requires validated, on-premises credentials to run.</span></span>
    
- <span data-ttu-id="bf6a1-142">사용자 지정 모바일 응용 프로그램 사용자의 smartphone 응용 프로그램에서 쿼리를 기초로 하는 특정 직원에 대 한 정보를 요청 하는 Azure PaaS에서 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf6a1-142">A custom mobile app running in Azure PaaS, which requests information about specific employees based on queries from a user's smartphone app.</span></span>
    
- <span data-ttu-id="bf6a1-143">사용자 지정 모바일 응용 프로그램의 유효성을 검사 하 고 요청을 전달 하는 DMZ에서 역방향 프록시 서버입니다.</span><span class="sxs-lookup"><span data-stu-id="bf6a1-143">A reverse proxy server in the DMZ that validates the custom mobile app and forwards the request.</span></span>
    
- <span data-ttu-id="bf6a1-144">사용자 계정의 권한에 따라 달라 집니다 연락처 요청을 처리 하는 LOB 응용 프로그램 서버 팜.</span><span class="sxs-lookup"><span data-stu-id="bf6a1-144">An LOB application server farm that services the contact request, subject to the permissions of the user's account.</span></span>
    
<span data-ttu-id="bf6a1-145">온-프레미스 id 공급자를 Azure AD와 동기화 하기 때문에 사용자 지정 모바일 응용 프로그램 및 LOB 응용 프로그램을 모두 요청 하는 사용자의 계정 이름을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf6a1-145">Because the on-premises identity provider has been synchronized with Azure AD, both the custom mobile app and the LOB app can validate the requesting user's account name.</span></span>
  
## <a name="stretch-database-with-sql-server-2016"></a><span data-ttu-id="bf6a1-146">SQL Server 2016에 적용된 스트레치 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="bf6a1-146">Stretch Database with SQL Server 2016</span></span>

<span data-ttu-id="bf6a1-147">늘이기 데이터베이스는 투명 하 게 하 고 안전 하 게 Azure에서 SQL 전체 확대/축소 데이터베이스에 고객 주문 정보를 포함 하는 대규모 테이블에서 닫힌된 비즈니스 데이터와 같은 정지 데이터를 이동할 수 있도록 하는 SQL Server 2016의 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="bf6a1-147">Stretch database is a feature of SQL Server 2016 that allows you to transparently and securely move cold data, such as closed business data in a large table that contains customer order information, to a SQL Stretch database in Azure.</span></span>
  
<span data-ttu-id="bf6a1-p105">SQL Server 인스턴스, 데이터베이스 또는 단일 테이블도의 내용을 맞춰지거나 때 SQL Server 2016 서버에서 로컬 데이터와 Azure에서 원격 데이터의 조합 합니다. 전체 확대/축소에 대 한 대상이 되는 데이터는 SQL Server 2016 하 여 Azure에 자동으로 이동 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf6a1-p105">When stretched, the contents of a SQL Server instance, a database, or even a single table is the combination of local data in SQL Server 2016 server and remote data in Azure. Data that becomes eligible for stretch is automatically moved to Azure by SQL Server 2016.</span></span>
  
<span data-ttu-id="bf6a1-150">그림 4 SQL Server 2016를 사용 하 여 전체 확대/축소 데이터베이스를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="bf6a1-150">Figure 4 shows Stretch Database with SQL Server 2016.</span></span>
  
<span data-ttu-id="bf6a1-151">**그림 4: SQL server 2016 늘이기 데이터베이스**</span><span class="sxs-lookup"><span data-stu-id="bf6a1-151">**Figure 4: Stretch Database with SQL Server 2016**</span></span>

![SQL Server 2016에 적용된 스트레치 데이터베이스](images/Hybrid_Poster/Hybrid_Cloud_Stack_PaaS_Apps_SQL.png)
  
<span data-ttu-id="bf6a1-p106">그림 4는 온-프레미스 네트워크 작은 로컬 데이터베이스가 있는 SQL Server 2016를 실행 하는 서버를 호스트 합니다. Azure PaaS 데이터베이스의 확장 된 부분으로 Azure SQL Server 전체 확대/축소 데이터베이스의 인스턴스를 호스팅합니다. 온-프레미스 SQL server로 전송 하는 온-프레미스 사용자 로부터 T-SQL 쿼리는 안전 하 게 요청 하는 사용자에 게 결과 반환 하는 Azure SQL 전체 확대/축소 데이터베이스에 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf6a1-p106">In Figure 4, an on-premises network hosts a server running SQL Server 2016 with a small local database. Azure PaaS hosts an instance of Azure SQL Server Stretch Database with the stretched portion of the database. T-SQL queries from an on-premises user sent to the on-premises SQL server are securely forwarded to the Azure SQL Stretch Database, which returns the results to the requesting user.</span></span>
  
 <span data-ttu-id="bf6a1-p107">Azure SQL 전체 확대/축소 데이터베이스에 기록 데이터를 포함 하는 사용자 쿼리를 전달 투명 하 게 됩니다. 쿼리는 테이블을 확대 하는 경우에를 다시 쓰도록 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bf6a1-p107">User queries that include the historical data are transparently forwarded to Azure SQL Stretch database. The queries do not need to be re-written, even though the table is stretched.</span></span>
  
<span data-ttu-id="bf6a1-p108">늘이기 데이터베이스 장기 저장소 및 기록 데이터를 투명 하 게 액세스를 위한 비용 효율적인 옵션을 제공합니다. 또한 성능과 테이블 매우 큰 될 때 발생 하는 가용성 문제를 해결 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf6a1-p108">Stretch database provides a cost-effective option for long-term storage and transparent access to historical data. It also solves performance and availability problems that arise when tables become very large.</span></span>
  
<span data-ttu-id="bf6a1-160">자세한 내용은 [전체 확대/축소 데이터베이스](https://msdn.microsoft.com/library/dn935011.aspx)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="bf6a1-160">For more information, see [Stretch Database](https://msdn.microsoft.com/library/dn935011.aspx).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="bf6a1-161">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bf6a1-161">See Also</span></span>

[<span data-ttu-id="bf6a1-162">Microsoft Hybrid Cloud for Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="bf6a1-162">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="bf6a1-163">Microsoft 클라우드 IT 아키텍처 리소스</span><span class="sxs-lookup"><span data-stu-id="bf6a1-163">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="bf6a1-164">Microsoft의 엔터프라이즈 클라우드 로드맵: IT 의사 결정권자를 위한 리소스</span><span class="sxs-lookup"><span data-stu-id="bf6a1-164">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



