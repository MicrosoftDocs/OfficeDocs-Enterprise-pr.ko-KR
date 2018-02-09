---
title: "액세스할 수 있는 다이어그램-Microsoft Azure에 SharePoint 재해 복구"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 4b855224-8e67-4efa-a3a4-908ee0ca6412
description: "이 문서에는 Microsoft Azure에 SharePoint 재해 복구 라는 다이어그램의 액세스할 수 있는 텍스트 버전입니다."
ms.openlocfilehash: 545aaae05e3becbde60fe01c0e50e5610ee69f98
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/09/2018
---
# <a name="accessible-diagram---sharepoint-disaster-recovery-to-microsoft-azure"></a><span data-ttu-id="f8410-103">액세스할 수 있는 다이어그램-Microsoft Azure에 SharePoint 재해 복구</span><span class="sxs-lookup"><span data-stu-id="f8410-103">Accessible diagram - SharePoint Disaster Recovery to Microsoft Azure</span></span>

<span data-ttu-id="f8410-104">**요약:** 이 문서에는 Microsoft Azure에 SharePoint 재해 복구 라는 다이어그램의 액세스할 수 있는 텍스트 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="f8410-104">**Summary:** This article is an accessible text version of the diagram named SharePoint Disaster Recovery to Microsoft Azure.</span></span>
  
<span data-ttu-id="f8410-105">이 포스터 Azure에서 복구 환경 구축을 위한 아키텍처의 예제를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8410-105">This poster provides examples of architectures for building a recovery environment in Azure.</span></span> 
  
## <a name="on-premises-environment-with-an-azure-recovery-environment"></a><span data-ttu-id="f8410-106">Azure 복구 환경 사용 하는 온-프레미스 환경</span><span class="sxs-lookup"><span data-stu-id="f8410-106">On-premises environment with an Azure recovery environment</span></span>

<span data-ttu-id="f8410-107">다이어그램의 복구를 위한 Azure를 사용 하는 온-프레미스 환경 프로덕션 환경에 사용 되는 아키텍처의 예를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="f8410-107">The diagram shows an example of architecture used for the production environment of an on-premises environment that uses Azure for recovery.</span></span> 
  
### <a name="on-premises-production-environment"></a><span data-ttu-id="f8410-108">온-프레미스 프로덕션 환경</span><span class="sxs-lookup"><span data-stu-id="f8410-108">On-premises production environment</span></span>

<span data-ttu-id="f8410-109">함께 제공 된 다이어그램에서는 서버 팜의 서버 а로 라이브 프로덕션 환경을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="f8410-109">The accompanying diagram shows a live production environment with four tiers of servers in a server farm.</span></span> 
  
#### <a name="tier-1"></a><span data-ttu-id="f8410-110">1 계층</span><span class="sxs-lookup"><span data-stu-id="f8410-110">Tier 1</span></span>

<span data-ttu-id="f8410-p101">프런트엔드 서비스 및 쿼리 처리에 대 한 두 서버가 있습니다. 인덱스 파티션 두 서버의 복제 데이터베이스를 제공 하는 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8410-p101">There are two servers for front-end services and query processing. There is an index partition that provides a replica of both servers.</span></span> 
  
#### <a name="tier-2"></a><span data-ttu-id="f8410-113">2 계층</span><span class="sxs-lookup"><span data-stu-id="f8410-113">Tier 2</span></span>

<span data-ttu-id="f8410-114">이 계층에서 분산된 캐시에 대 한 두 서버가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8410-114">There are two servers for distributed cache in this tier.</span></span> 
  
#### <a name="tier-3"></a><span data-ttu-id="f8410-115">3 계층</span><span class="sxs-lookup"><span data-stu-id="f8410-115">Tier 3</span></span>

<span data-ttu-id="f8410-p102">이 계층 3 명의 서버는 있습니다. 각 서버는 다음과 같은 서비스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f8410-p102">There are three servers in this tier. Each server provides the following services:</span></span> 
  
- <span data-ttu-id="f8410-118">백엔드 서비스</span><span class="sxs-lookup"><span data-stu-id="f8410-118">Backend services</span></span> 
    
- <span data-ttu-id="f8410-119">관리</span><span class="sxs-lookup"><span data-stu-id="f8410-119">Admin</span></span> 
    
- <span data-ttu-id="f8410-120">워크플로 관리자</span><span class="sxs-lookup"><span data-stu-id="f8410-120">Workflow manager</span></span> 
    
- <span data-ttu-id="f8410-121">크롤링</span><span class="sxs-lookup"><span data-stu-id="f8410-121">Crawl</span></span> 
    
- <span data-ttu-id="f8410-122">콘텐츠 처리</span><span class="sxs-lookup"><span data-stu-id="f8410-122">Content processing</span></span> 
    
- <span data-ttu-id="f8410-123">분석</span><span class="sxs-lookup"><span data-stu-id="f8410-123">Analytics</span></span> 
    
#### <a name="tier-4"></a><span data-ttu-id="f8410-124">계층 4</span><span class="sxs-lookup"><span data-stu-id="f8410-124">Tier 4</span></span>

<span data-ttu-id="f8410-p103">이 계층의 서버 두 대 있습니다. 두 서버는 다음과 같은 세 사용 가능 그룹을 갖고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8410-p103">There are two servers in this tier. Both servers have three availability groups, as follows:</span></span> 
  
- <span data-ttu-id="f8410-127">가용성 그룹 #1 검색 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f8410-127">Availability group #1 provides search capabilities.</span></span> 
    
- <span data-ttu-id="f8410-128">가용성 그룹 #2 콘텐츠, 구성 및 서비스 응용 프로그램을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8410-128">Availability group #2 provides content, configuration, and service applications.</span></span> 
    
- <span data-ttu-id="f8410-129">가용성 그룹 #3 콘텐츠를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8410-129">Availability group #3 provides content.</span></span> 
    
<span data-ttu-id="f8410-p104">파일 공유이 계층의 서버 이기도 합니다. 계층 4 서버 로그 전달을 사용 하 여이 서버와 통신할 수 있습니다. 차례로이 서버는 다음 섹션의 설명에 따라 분산 파일 시스템 복제 (DFSR)을 통해 Azure의 웜 대기 복구 환경에 있는 파일 공유 서버에 게 통신 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8410-p104">There is also a file sharing server in this tier. The tier 4 servers use log shipping to communicate with this server. This server, in turn, communicates over Distributed File System Replication (DFSR) to a file share server in the Azure warm standby recovery environment, as described in the following section.</span></span> 
  
### <a name="azure-recovery-environment"></a><span data-ttu-id="f8410-133">Azure 복구 환경</span><span class="sxs-lookup"><span data-stu-id="f8410-133">Azure recovery environment</span></span>

#### <a name="warm-standby-environment-running-virtual-machines"></a><span data-ttu-id="f8410-134">가상 컴퓨터를 실행 하는 웜 대기 환경</span><span class="sxs-lookup"><span data-stu-id="f8410-134">Warm standby environment running virtual machines</span></span>

<span data-ttu-id="f8410-p105">함께 제공 된 다이어그램 Azure 복구 환경에 정확 하 게 복제 하는 온-프레미스 환경을 보여줍니다. 이 환경에서 파일 공유 서버는 DFSR 통해 온-프레미스 환경에 연결 됩니다. DFSR 파일 공유 서버를 통해 복구 환경에 프로덕션 환경에서 로그를 전송합니다.</span><span class="sxs-lookup"><span data-stu-id="f8410-p105">The accompanying diagram shows the on-premises environment replicated exactly in the Azure recovery environment. The file share server in this environment is linked to the on-premises environment through DFSR. DFSR transfers logs from the production environment to the recovery environment through the file share server.</span></span> 
  
### <a name="overview"></a><span data-ttu-id="f8410-138">개요</span><span class="sxs-lookup"><span data-stu-id="f8410-138">Overview</span></span>

<span data-ttu-id="f8410-139">온-프레미스 SharePoint 2013 팜에 대 한 재해 복구 환경 Azure의 호스팅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8410-139">The disaster recovery environment for an on-premises SharePoint 2013 farm can be hosted in Azure.</span></span> 
  
-  <span data-ttu-id="f8410-140">Azure 인프라 서비스 보조 데이터 센터를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f8410-140">Azure Infrastructure Services provides a secondary datacenter.</span></span>
    
- <span data-ttu-id="f8410-141">사용 하는 리소스에 대해서만 지불 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8410-141">Pay only for the resources you use.</span></span> 
    
- <span data-ttu-id="f8410-142">작은 복구 팜 규모 및 용량 목표를 충족 하기 위해 재해가 발생 한 후 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8410-142">Small recovery farms can be scaled out after a disaster to meet scale and capacity targets.</span></span> 
    
<span data-ttu-id="f8410-143">Azure의 복구 팜에 프로덕션 온-프레미스 팜에 최대한 동일 하 게로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f8410-143">The recovery farm in Azure is configured as identically as possible to the production on-premises farm.</span></span> 
  
- <span data-ttu-id="f8410-144">서버 역할의 동일한 표현 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8410-144">Same representation of server roles.</span></span> 
    
- <span data-ttu-id="f8410-145">동일한 구성의 사용자 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8410-145">Same configuration of customizations.</span></span> 
    
- <span data-ttu-id="f8410-146">동일한 구성의 검색 기능 (이러한 프로덕션 팜 중 더 작은 버전에서 사용 가능).</span><span class="sxs-lookup"><span data-stu-id="f8410-146">Same configuration of search features (these can be on a smaller version of the production farm).</span></span> 
    
<span data-ttu-id="f8410-147">로그 전달 및 DFSR는 Azure 팜으로 데이터베이스 백업과 트랜잭션 로그를 복사 하는데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f8410-147">Log shipping and DFSR are used to copy database backups and transaction logs to the Azure farm.</span></span> 
  
- <span data-ttu-id="f8410-p106">DFSR는 복구 환경에 프로덕션 환경에서 로그를 전송 하는데 사용 됩니다. WAN 시나리오에서는 DFSR Azure에서 직접 보조 서버로 로그를 전달 하는 보다 더 효율적입니다.</span><span class="sxs-lookup"><span data-stu-id="f8410-p106">DFSR is used to transfer logs from the production environment to the recovery environment. In a WAN scenario, DFSR is more efficient than shipping the logs directly to the secondary server in Azure.</span></span> 
    
- <span data-ttu-id="f8410-150">SQL Server Azure 기반 컴퓨터에 로그 재생 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f8410-150">Logs are replayed to the Azure-based SQL Server computers.</span></span> 
    
- <span data-ttu-id="f8410-151">로그 전달 데이터베이스는 복구 작업이 수행 될 때까지 팜에 연결 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f8410-151">Log-shipped databases are not attached to the farm until a recovery exercise is performed.</span></span> 
    
<span data-ttu-id="f8410-152">장애 조치 절차:</span><span class="sxs-lookup"><span data-stu-id="f8410-152">Failover procedures:</span></span> 
  
1. <span data-ttu-id="f8410-153">로그 전달을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8410-153">Stop log shipping.</span></span> 
    
2. <span data-ttu-id="f8410-154">기본 팜에 대 한 트래픽이 수락을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8410-154">Stop accepting traffic to the primary farm.</span></span> 
    
3. <span data-ttu-id="f8410-155">마지막 트랜잭션 로그를 재생 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8410-155">Replay the final transaction logs.</span></span> 
    
4. <span data-ttu-id="f8410-156">콘텐츠 데이터베이스를 팜에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8410-156">Attach the content databases to the farm.</span></span> 
    
5. <span data-ttu-id="f8410-157">전체 크롤링을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8410-157">Start a full crawl.</span></span> 
    
6. <span data-ttu-id="f8410-158">복제 된 서비스 데이터베이스에서 서비스 응용 프로그램을 복원 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8410-158">Restore service applications from the replicated services databases.</span></span> 
    
<span data-ttu-id="f8410-159">이 솔루션에서 제공 하는 복구 목표는 다음과 같은 종류가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8410-159">Recovery objectives provided by this solution include:</span></span> 
  
- <span data-ttu-id="f8410-160">사이트 및 콘텐츠</span><span class="sxs-lookup"><span data-stu-id="f8410-160">Sites and content</span></span> 
    
- <span data-ttu-id="f8410-161">검색 (다시 크롤링, 검색 기록을 없음)</span><span class="sxs-lookup"><span data-stu-id="f8410-161">Search (re-crawled, no search history)</span></span> 
    
- <span data-ttu-id="f8410-162">서비스</span><span class="sxs-lookup"><span data-stu-id="f8410-162">Services</span></span>
    
<span data-ttu-id="f8410-163">Microsoft Consulting Services 또는 파트너 하 여 해결할 수 있는 추가 항목:</span><span class="sxs-lookup"><span data-stu-id="f8410-163">Additional items that can be addressed by Microsoft Consulting Services or a partner:</span></span> 
  
- <span data-ttu-id="f8410-164">사용자 지정 팜 솔루션 동기화 (영문)</span><span class="sxs-lookup"><span data-stu-id="f8410-164">Synchronizing custom farm solutions</span></span> 
    
- <span data-ttu-id="f8410-165">온-프레미스 (비즈니스 데이터 연결 (BDC) 및 검색 콘텐츠 원본) 데이터 원본에 대 한 연결</span><span class="sxs-lookup"><span data-stu-id="f8410-165">Connections to data sources on premises (Business Data Connectivity (BDC) and search content sources)</span></span> 
    
- <span data-ttu-id="f8410-166">검색 복원 시나리오</span><span class="sxs-lookup"><span data-stu-id="f8410-166">Search restore scenarios</span></span> 
    
- <span data-ttu-id="f8410-167">복구 시간 목표 (RTO) 및 복구 지점 목표 (RPO)</span><span class="sxs-lookup"><span data-stu-id="f8410-167">Recovery Time Objectives (RTO) and Recovery Point Objectives (RPO)</span></span> 
    
#### <a name="cold-standby-environment-running-virtual-machines"></a><span data-ttu-id="f8410-168">가상 컴퓨터를 실행 하는 콜드 대기 환경</span><span class="sxs-lookup"><span data-stu-id="f8410-168">Cold standby environment running virtual machines</span></span>

<span data-ttu-id="f8410-169">콜드 대기 환경 시작 시간이 오래 걸리지만 저렴 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8410-169">Cold standby environments take longer to start but are less expensive.</span></span> 
  
- <span data-ttu-id="f8410-p107">팜은 완벽 하 게, 작성 되었지만 팜에서 만들어진 후 가상 컴퓨터가 중지 되는 합니다. 가상 컴퓨터를 실행 하는 하지만 저장소 및 네트워크 데이터 전송 비용 적용 하는 경우에 처리 비용을 지불 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8410-p107">The farm is fully built, but the virtual machines are stopped after the farm is created. You pay only processing costs when the virtual machines are running, but storage and network data transfer costs apply.</span></span> 
    
- <span data-ttu-id="f8410-172">재해 발생 시 팜의 모든 가상 컴퓨터 시작 및 패치를 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8410-172">In the event of a disaster, all the virtual machines in the farm are started and patched.</span></span> 
    
- <span data-ttu-id="f8410-173">백업 및 트랜잭션 로그에는 팜의 데이터베이스에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f8410-173">Backups and transaction logs are applied to the farm databases.</span></span> 
    
<span data-ttu-id="f8410-174">다음 목록에서는 콜드 대기 환경에 대 한 추가 절차에 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8410-174">The following list describes additional procedures for cold standby environments:</span></span> 
  
- <span data-ttu-id="f8410-175">패치를 적용 하 고 업데이트 하 고, 환경 확인을 정기적으로 가상 컴퓨터를 켭니다.</span><span class="sxs-lookup"><span data-stu-id="f8410-175">Turn on virtual machines regularly to patch, update, and verify the environment.</span></span> 
    
- <span data-ttu-id="f8410-176">DNS 및 IP 주소를 새로 고치는 절차를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8410-176">Run procedures to refresh DNS and IP addresses.</span></span> 
    
- <span data-ttu-id="f8410-177">장애 조치 후 SQL AlwaysOn를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8410-177">Set up SQL AlwaysOn after a failover.</span></span> 
    
<span data-ttu-id="f8410-p108">함께 제공 된 다이어그램에서는 가상 컴퓨터에서 복제 된 복구 환경을 보여줍니다. 콜드 대기 환경에 장애 조치 후 모든 가상 컴퓨터를 시작 하 고 사용 가능 그룹 재생 로그를 사용 하 여 데이터베이스 서버를 사용할 수 있도록 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f8410-p108">The accompanying diagram shows a replicated recovery environment on virtual machines. After failover to a cold standby environment, all virtual machines are started, and the availability groups are configured using replay logs to make the database servers available.</span></span> 
  
## <a name="sharepoint-recovery-environment-in-azure"></a><span data-ttu-id="f8410-180">Azure의 SharePoint 복구 환경</span><span class="sxs-lookup"><span data-stu-id="f8410-180">SharePoint recovery environment in Azure</span></span>

<span data-ttu-id="f8410-181">디자인 하 고 Azure에서 장애 조치 환경에 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8410-181">Design and build the failover environment in Azure.</span></span> 
  
- <span data-ttu-id="f8410-182">Azure에 가상 네트워크를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f8410-182">Create a virtual network in Azure.</span></span> 
    
- <span data-ttu-id="f8410-p109">사이트 마다 VPN 연결을 사용 하 여 Azure에 가상 네트워크와 온-프레미스 네트워크에 연결 합니다. 이 연결은 Azure의 동적 게이트웨이 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f8410-p109">Connect the on-premises network with the virtual network in Azure with a site-to-site VPN connection. This connection uses a dynamic gateway in Azure.</span></span> 
    
- <span data-ttu-id="f8410-p110">Azure 가상 네트워크에 하나 이상의 도메인 컨트롤러를 배포 하 고 이러한 온-프레미스 도메인에서 작동 하도록 구성 합니다. 이러한 도메인 컨트롤러는 카탈로그 서버입니다.</span><span class="sxs-lookup"><span data-stu-id="f8410-p110">Deploy one or more domain controllers to the Azure virtual network, and configure these to work with your on-premises domain. These domain controllers are catalog servers.</span></span> 
    
- <span data-ttu-id="f8410-187">클라우드 서비스 및 가용성 집합에 대 한 SharePoint 팜을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8410-187">Adapt the SharePoint farm for cloud services and availability sets.</span></span> 
    
- <span data-ttu-id="f8410-188">호스트 파일 공유를 SharePoint 팜 및 파일 서버를 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8410-188">Deploy the SharePoint farm plus a file server to host file shares.</span></span> 
    
- <span data-ttu-id="f8410-189">온-프레미스 환경과 Azure 기반 복구 환경 간에 로그 전달 및 DFSR 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8410-189">Set up log shipping and DFSR between the on-premises environment and the Azure-based recovery environment.</span></span> 
    
<span data-ttu-id="f8410-190">함께 제공 되는 다이어그램 온-프레미스 환경 및 다음과 같은 기능을 사용 하 여 Azure 가상 네트워크를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="f8410-190">The accompanying diagram shows the on-premises environment and the Azure virtual network with the following features:</span></span> 
  
### <a name="on-premises-environment"></a><span data-ttu-id="f8410-191">온-프레미스 환경</span><span class="sxs-lookup"><span data-stu-id="f8410-191">On-premises environment</span></span>

- <span data-ttu-id="f8410-192">Windows Server 2012 RRAS</span><span class="sxs-lookup"><span data-stu-id="f8410-192">Windows Server 2012 RRAS</span></span> 
    
- <span data-ttu-id="f8410-193">Active Directory 서버</span><span class="sxs-lookup"><span data-stu-id="f8410-193">Active Directory server</span></span> 
    
<span data-ttu-id="f8410-194">가상 사설망 (VPN) 게이트웨이 통해 Azure 가상 네트워크와 온-프레미스 네트워크 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="f8410-194">The on-premises network interfaces with the Azure virtual network over a virtual private network (VPN) gateway.</span></span> 
  
### <a name="azure-virtual-network"></a><span data-ttu-id="f8410-195">Azure 가상 네트워크</span><span class="sxs-lookup"><span data-stu-id="f8410-195">Azure virtual network</span></span>

<span data-ttu-id="f8410-196">현재는 VPN 게이트웨이 서브넷과 VPN 게이트웨이 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="f8410-196">The VPN gateway interfaces with an active VPN gateway subnet.</span></span> 
  
<span data-ttu-id="f8410-197">Azure 가상 네트워크에 세 클라우드 서비스를 가지 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8410-197">There are three cloud services in the Azure virtual network:</span></span> 
  
- <span data-ttu-id="f8410-198">첫번째 클라우드 서비스 설정 하는 두 Active Directory 형식 및 한 가용성와 DNS 서버에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8410-198">The first cloud service has two Active Directory and DNS servers with an availability set.</span></span> 
    
- <span data-ttu-id="f8410-p111">두번째 클라우드 서비스는 3 개 서버: 2 분산 캐시 서버 가용성 집합입니다. 가용성 집합으로 프런트엔드 서버 두 대 가용성 집합으로 세 백엔드 서버입니다.</span><span class="sxs-lookup"><span data-stu-id="f8410-p111">The second cloud service has three sets of servers: Two distributed cache servers with an availability set. Two front-end servers with an availability set. Three backend servers with an availability set.</span></span>
    
- <span data-ttu-id="f8410-p112">세번째 클라우드 서비스에는 가용성 집합으로 세 데이터베이스 서버가 있습니다. 이러한 데이터베이스 서버 중 하나에 대 한 SQL Server AlwaysOn 노드 과반수의 로그 전달 및 세번째 노드에 대 한 파일 공유 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="f8410-p112">The third cloud service has three database servers with an availability set. One of these database servers is a file share for log shipping and a third node of a node majority for SQL Server AlwaysOn.</span></span> 
    
### <a name="build-the-ad-ds-hybrid-environment"></a><span data-ttu-id="f8410-204">AD DS 하이브리드 환경을 구축합니다</span><span class="sxs-lookup"><span data-stu-id="f8410-204">Build the AD DS hybrid environment</span></span>

<span data-ttu-id="f8410-205">이 솔루션에 대 한 AD DS의 구성을 AD DS 부분적으로 배포 된 온-프레미스 및 Azure 가상 컴퓨터에 부분적으로 배포 되는 하이브리드 배포 시나리오를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8410-205">The configuration of AD DS for this solution constitutes a hybrid deployment scenario in which AD DS is partly deployed on-premises and partly deployed on Azure virtual machines.</span></span> 
  
<span data-ttu-id="f8410-206">중요 한 — Azure에서 AD DS를 배포 하기 전에 지침을 제공 배포 Windows Server Active Directory를 위한 Microsoft Azure 가상 컴퓨터에서 (http://msdn.microsoft.com/en-us/library/windowsazure/jj156090.aspx).</span><span class="sxs-lookup"><span data-stu-id="f8410-206">Important — Before you deploy AD DS in Azure, read Guidelines for Deploying Windows Server Active Directory on Microsoft Azure Virtual Machines (http://msdn.microsoft.com/en-us/library/windowsazure/jj156090.aspx).</span></span> 
  
<span data-ttu-id="f8410-207">Active Directory 환경을 디자인 및 배포에 대 한 자세한 지침, http://TechNet.microsoft.com을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="f8410-207">For complete guidance on designing and deploying Active Directory environments, see http://TechNet.microsoft.com.</span></span> 
  
<span data-ttu-id="f8410-p113">이 참조 아키텍처는 도메인 컨트롤러로 구성 된 두 가상 컴퓨터를 포함 합니다. 각 작업은 다음과 같이 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f8410-p113">This reference architecture includes two virtual machines configured as domain controllers. Each is configured as follows:</span></span> 
  
- <span data-ttu-id="f8410-210">크기 — 작은 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8410-210">Size — Small.</span></span> 
    
- <span data-ttu-id="f8410-211">운영 체제-Windows Server 2012입니다.</span><span class="sxs-lookup"><span data-stu-id="f8410-211">Operating system — Windows Server 2012.</span></span> 
    
- <span data-ttu-id="f8410-p114">역할-AD DS 도메인 컨트롤러를 글로벌 카탈로그 서버로 지정 합니다. 이 구성은 VPN 연결을 통해 탈출 트래픽을 줄입니다. 함께 많고 변경 비율이 다중 도메인 환경에서 도메인 컨트롤러 온-프레미스 하지 Azure에서 글로벌 카탈로그 서버와 동기화 되도록 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8410-p114">Role — AD DS domain controller designated as a global catalog server. This configuration reduces egress traffic across the VPN connection. In a multi-domain environment with high rates of change, configure domain controllers on-premises to not sync with the global catalog servers in Azure.</span></span> 
    
- <span data-ttu-id="f8410-p115">데이터 디스크-AD DS 데이터베이스, 로그 및 SYSVOL Azure 데이터 디스크에 배치 합니다. 이러한 운영 체제 디스크 또는 Azure에서 제공 하는 임시 디스크에 배치 하지 마십시오. 이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8410-p115">Data disks — Place the AD DS database, logs, and SYSVOL on Azure data disks. Do not place these on the operating system disk or the temporary disks provided by Azure. This is important.</span></span> 
    
- <span data-ttu-id="f8410-218">-역할을 설치 하 고 도메인 컨트롤러에서 Windows DNS를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8410-218">Role — Install and configure Windows DNS on the domain controllers.</span></span> 
    
- <span data-ttu-id="f8410-p116">IP 주소-동적 IP 주소를 사용 합니다. Azure 가상 네트워크를 구성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8410-p116">IP addresses — Use dynamic IP addresses. This requires you to create an Azure Virtual Network.</span></span> 
    

