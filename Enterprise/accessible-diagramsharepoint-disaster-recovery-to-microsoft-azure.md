---
title: 액세스 가능한 다이어그램-Microsoft Azure로의 SharePoint 재해 복구
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 4b855224-8e67-4efa-a3a4-908ee0ca6412
description: 이 문서는 Microsoft Azure에 대 한 SharePoint 재해 복구 라는 다이어그램의 액세스 가능한 텍스트 버전입니다.
ms.openlocfilehash: d7df0f44dd4e7f0cbb8580029991bc9280892afb
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068524"
---
# <a name="accessible-diagram---sharepoint-disaster-recovery-to-microsoft-azure"></a><span data-ttu-id="73bc7-103">액세스 가능한 다이어그램-Microsoft Azure로의 SharePoint 재해 복구</span><span class="sxs-lookup"><span data-stu-id="73bc7-103">Accessible diagram - SharePoint Disaster Recovery to Microsoft Azure</span></span>

<span data-ttu-id="73bc7-104">**요약:** 이 문서는 Microsoft Azure에 대 한 SharePoint 재해 복구 라는 다이어그램의 액세스 가능한 텍스트 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-104">**Summary:** This article is an accessible text version of the diagram named SharePoint Disaster Recovery to Microsoft Azure.</span></span>
  
<span data-ttu-id="73bc7-105">이 포스터는 Azure의 복구 환경을 구축 하기 위한 아키텍처의 예를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-105">This poster provides examples of architectures for building a recovery environment in Azure.</span></span> 
  
## <a name="on-premises-environment-with-an-azure-recovery-environment"></a><span data-ttu-id="73bc7-106">Azure 복구 환경을 사용 하는 온-프레미스 환경</span><span class="sxs-lookup"><span data-stu-id="73bc7-106">On-premises environment with an Azure recovery environment</span></span>

<span data-ttu-id="73bc7-107">이 다이어그램에서는 복구를 위해 Azure를 사용 하는 온-프레미스 환경의 프로덕션 환경에 사용 되는 아키텍처의 예를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-107">The diagram shows an example of architecture used for the production environment of an on-premises environment that uses Azure for recovery.</span></span> 
  
### <a name="on-premises-production-environment"></a><span data-ttu-id="73bc7-108">온-프레미스 프로덕션 환경</span><span class="sxs-lookup"><span data-stu-id="73bc7-108">On-premises production environment</span></span>

<span data-ttu-id="73bc7-109">함께 제공 되는 다이어그램에서는 서버 팜의 서버 계층 4 개가 포함 된 실제 프로덕션 환경을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-109">The accompanying diagram shows a live production environment with four tiers of servers in a server farm.</span></span> 
  
#### <a name="tier-1"></a><span data-ttu-id="73bc7-110">계층 1</span><span class="sxs-lookup"><span data-stu-id="73bc7-110">Tier 1</span></span>

<span data-ttu-id="73bc7-111">프런트 엔드 서비스와 쿼리 처리에는 두 가지 서버가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-111">There are two servers for front-end services and query processing.</span></span> <span data-ttu-id="73bc7-112">두 서버의 복제본을 제공 하는 인덱스 파티션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-112">There is an index partition that provides a replica of both servers.</span></span> 
  
#### <a name="tier-2"></a><span data-ttu-id="73bc7-113">계층 2</span><span class="sxs-lookup"><span data-stu-id="73bc7-113">Tier 2</span></span>

<span data-ttu-id="73bc7-114">이 계층에는 분산 캐시에 대 한 서버가 두 개 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-114">There are two servers for distributed cache in this tier.</span></span> 
  
#### <a name="tier-3"></a><span data-ttu-id="73bc7-115">계층 3</span><span class="sxs-lookup"><span data-stu-id="73bc7-115">Tier 3</span></span>

<span data-ttu-id="73bc7-116">이 계층에는 3 대의 서버가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-116">There are three servers in this tier.</span></span> <span data-ttu-id="73bc7-117">각 서버에서 제공 하는 서비스는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-117">Each server provides the following services:</span></span> 
  
- <span data-ttu-id="73bc7-118">백 엔드 서비스</span><span class="sxs-lookup"><span data-stu-id="73bc7-118">Backend services</span></span> 
    
- <span data-ttu-id="73bc7-119">관리자</span><span class="sxs-lookup"><span data-stu-id="73bc7-119">Admin</span></span> 
    
- <span data-ttu-id="73bc7-120">워크플로 관리자</span><span class="sxs-lookup"><span data-stu-id="73bc7-120">Workflow manager</span></span> 
    
- <span data-ttu-id="73bc7-121">크롤링</span><span class="sxs-lookup"><span data-stu-id="73bc7-121">Crawl</span></span> 
    
- <span data-ttu-id="73bc7-122">콘텐츠 처리</span><span class="sxs-lookup"><span data-stu-id="73bc7-122">Content processing</span></span> 
    
- <span data-ttu-id="73bc7-123">분석</span><span class="sxs-lookup"><span data-stu-id="73bc7-123">Analytics</span></span> 
    
#### <a name="tier-4"></a><span data-ttu-id="73bc7-124">계층 4</span><span class="sxs-lookup"><span data-stu-id="73bc7-124">Tier 4</span></span>

<span data-ttu-id="73bc7-125">이 계층에는 두 개의 서버가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-125">There are two servers in this tier.</span></span> <span data-ttu-id="73bc7-126">두 서버에는 다음과 같은 세 가지 가용성 그룹이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-126">Both servers have three availability groups, as follows:</span></span> 
  
- <span data-ttu-id="73bc7-127">가용성 그룹 #1는 검색 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-127">Availability group #1 provides search capabilities.</span></span> 
    
- <span data-ttu-id="73bc7-128">가용성 그룹 #2 콘텐츠, 구성 및 서비스 응용 프로그램을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-128">Availability group #2 provides content, configuration, and service applications.</span></span> 
    
- <span data-ttu-id="73bc7-129">가용성 그룹 #3 콘텐츠를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-129">Availability group #3 provides content.</span></span> 
    
<span data-ttu-id="73bc7-130">이 계층에는 파일 공유 서버도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-130">There is also a file sharing server in this tier.</span></span> <span data-ttu-id="73bc7-131">계층 4 서버는 로그 전달을 사용 하 여이 서버와 통신 합니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-131">The tier 4 servers use log shipping to communicate with this server.</span></span> <span data-ttu-id="73bc7-132">그러면이 서버는 다음 섹션에 설명 된 대로, DFSR (분산 파일 시스템 복제)를 통해 Azure 웜 대기 모드 복구 환경의 파일 공유 서버와 통신 합니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-132">This server, in turn, communicates over Distributed File System Replication (DFSR) to a file share server in the Azure warm standby recovery environment, as described in the following section.</span></span> 
  
### <a name="azure-recovery-environment"></a><span data-ttu-id="73bc7-133">Azure 복구 환경</span><span class="sxs-lookup"><span data-stu-id="73bc7-133">Azure recovery environment</span></span>

#### <a name="warm-standby-environment-running-virtual-machines"></a><span data-ttu-id="73bc7-134">가상 컴퓨터를 실행 하는 웜 대기 환경</span><span class="sxs-lookup"><span data-stu-id="73bc7-134">Warm standby environment running virtual machines</span></span>

<span data-ttu-id="73bc7-135">함께 제공 되는 다이어그램에서는 Azure 복구 환경에서 정확히 복제 되는 온-프레미스 환경을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-135">The accompanying diagram shows the on-premises environment replicated exactly in the Azure recovery environment.</span></span> <span data-ttu-id="73bc7-136">이 환경의 파일 공유 서버는 DFSR을 통해 온-프레미스 환경에 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-136">The file share server in this environment is linked to the on-premises environment through DFSR.</span></span> <span data-ttu-id="73bc7-137">DFSR은 파일 공유 서버를 통해 프로덕션 환경에서 복구 환경으로 로그를 전송 합니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-137">DFSR transfers logs from the production environment to the recovery environment through the file share server.</span></span> 
  
### <a name="overview"></a><span data-ttu-id="73bc7-138">개요</span><span class="sxs-lookup"><span data-stu-id="73bc7-138">Overview</span></span>

<span data-ttu-id="73bc7-139">온-프레미스 SharePoint 2013 팜에 대 한 재해 복구 환경을 Azure에서 호스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-139">The disaster recovery environment for an on-premises SharePoint 2013 farm can be hosted in Azure.</span></span> 
  
-  <span data-ttu-id="73bc7-140">Azure 인프라 서비스는 보조 데이터 센터를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-140">Azure Infrastructure Services provides a secondary datacenter.</span></span>
    
- <span data-ttu-id="73bc7-141">사용 하는 자원에 대해서만 결제 합니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-141">Pay only for the resources you use.</span></span> 
    
- <span data-ttu-id="73bc7-142">소규모 복구 팜은 확장 및 용량 목표를 충족 하기 위해 재해가 발생 한 후 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-142">Small recovery farms can be scaled out after a disaster to meet scale and capacity targets.</span></span> 
    
<span data-ttu-id="73bc7-143">Azure의 복구 팜이 프로덕션 온-프레미스 팜과 가능한 동일 하 게 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-143">The recovery farm in Azure is configured as identically as possible to the production on-premises farm.</span></span> 
  
- <span data-ttu-id="73bc7-144">서버 역할의 표현이 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-144">Same representation of server roles.</span></span> 
    
- <span data-ttu-id="73bc7-145">사용자 지정 내용이 동일 하 게 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-145">Same configuration of customizations.</span></span> 
    
- <span data-ttu-id="73bc7-146">동일한 검색 기능 구성 (더 작은 버전의 프로덕션 팜이 있을 수 있음)</span><span class="sxs-lookup"><span data-stu-id="73bc7-146">Same configuration of search features (these can be on a smaller version of the production farm).</span></span> 
    
<span data-ttu-id="73bc7-147">로그 전달 및 DFSR은 데이터베이스 백업 및 트랜잭션 로그를 Azure 팜에 복사 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-147">Log shipping and DFSR are used to copy database backups and transaction logs to the Azure farm.</span></span> 
  
- <span data-ttu-id="73bc7-148">DFSR은 프로덕션 환경에서 복구 환경으로 로그를 전송 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-148">DFSR is used to transfer logs from the production environment to the recovery environment.</span></span> <span data-ttu-id="73bc7-149">WAN 시나리오에서 DFSR은 Azure의 보조 서버로 직접 로그를 전달하는 것보다 더 효율적입니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-149">In a WAN scenario, DFSR is more efficient than shipping the logs directly to the secondary server in Azure.</span></span> 
    
- <span data-ttu-id="73bc7-150">Azure 기반 SQL Server 컴퓨터에 로그가 재생 됩니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-150">Logs are replayed to the Azure-based SQL Server computers.</span></span> 
    
- <span data-ttu-id="73bc7-151">로그 전달 데이터베이스는 복구 작업이 수행 될 때까지 팜에 연결 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-151">Log-shipped databases are not attached to the farm until a recovery exercise is performed.</span></span> 
    
<span data-ttu-id="73bc7-152">장애 조치 (Failover) 절차:</span><span class="sxs-lookup"><span data-stu-id="73bc7-152">Failover procedures:</span></span> 
  
1. <span data-ttu-id="73bc7-153">로그 전달을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-153">Stop log shipping.</span></span> 
    
2. <span data-ttu-id="73bc7-154">기본 팜에 대 한 트래픽을 수락 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-154">Stop accepting traffic to the primary farm.</span></span> 
    
3. <span data-ttu-id="73bc7-155">최종 트랜잭션 로그를 재생 합니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-155">Replay the final transaction logs.</span></span> 
    
4. <span data-ttu-id="73bc7-156">콘텐츠 데이터베이스를 팜에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-156">Attach the content databases to the farm.</span></span> 
    
5. <span data-ttu-id="73bc7-157">전체 크롤링을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-157">Start a full crawl.</span></span> 
    
6. <span data-ttu-id="73bc7-158">복제 된 서비스 데이터베이스에서 서비스 응용 프로그램을 복원 합니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-158">Restore service applications from the replicated services databases.</span></span> 
    
<span data-ttu-id="73bc7-159">이 솔루션에서 제공 하는 복구 목표는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-159">Recovery objectives provided by this solution include:</span></span> 
  
- <span data-ttu-id="73bc7-160">사이트 및 콘텐츠</span><span class="sxs-lookup"><span data-stu-id="73bc7-160">Sites and content</span></span> 
    
- <span data-ttu-id="73bc7-161">검색 (다시 크롤링, 검색 기록 없음)</span><span class="sxs-lookup"><span data-stu-id="73bc7-161">Search (re-crawled, no search history)</span></span> 
    
- <span data-ttu-id="73bc7-162">서비스</span><span class="sxs-lookup"><span data-stu-id="73bc7-162">Services</span></span>
    
<span data-ttu-id="73bc7-163">Microsoft 컨설팅 서비스 또는 파트너가 처리할 수 있는 추가 항목:</span><span class="sxs-lookup"><span data-stu-id="73bc7-163">Additional items that can be addressed by Microsoft Consulting Services or a partner:</span></span> 
  
- <span data-ttu-id="73bc7-164">사용자 지정 팜 솔루션 동기화</span><span class="sxs-lookup"><span data-stu-id="73bc7-164">Synchronizing custom farm solutions</span></span> 
    
- <span data-ttu-id="73bc7-165">온-프레미스 데이터 원본에 대 한 연결 (BDC (Business Data Connectivity) 및 search content sources)</span><span class="sxs-lookup"><span data-stu-id="73bc7-165">Connections to data sources on premises (Business Data Connectivity (BDC) and search content sources)</span></span> 
    
- <span data-ttu-id="73bc7-166">검색 복원 시나리오</span><span class="sxs-lookup"><span data-stu-id="73bc7-166">Search restore scenarios</span></span> 
    
- <span data-ttu-id="73bc7-167">RTO (복구 시간 목표) 및 RPO (복구 지점 목표)</span><span class="sxs-lookup"><span data-stu-id="73bc7-167">Recovery Time Objectives (RTO) and Recovery Point Objectives (RPO)</span></span> 
    
#### <a name="cold-standby-environment-running-virtual-machines"></a><span data-ttu-id="73bc7-168">가상 컴퓨터를 실행 하는 콜드 대기 환경</span><span class="sxs-lookup"><span data-stu-id="73bc7-168">Cold standby environment running virtual machines</span></span>

<span data-ttu-id="73bc7-169">콜드 대기 환경은 시작 하는 데 시간이 오래 걸리지만 비용이 저렴 합니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-169">Cold standby environments take longer to start but are less expensive.</span></span> 
  
- <span data-ttu-id="73bc7-170">팜은 완전히 구축 되었지만 팜을 만든 후에는 가상 컴퓨터를 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-170">The farm is fully built, but the virtual machines are stopped after the farm is created.</span></span> <span data-ttu-id="73bc7-171">가상 컴퓨터를 실행 하는 경우에만 처리 비용을 지불 하지만 저장소 및 네트워크 데이터 전송 비용이 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-171">You pay only processing costs when the virtual machines are running, but storage and network data transfer costs apply.</span></span> 
    
- <span data-ttu-id="73bc7-172">재해가 발생 하면 팜의 모든 가상 컴퓨터를 시작 하 고 패치를 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-172">In the event of a disaster, all the virtual machines in the farm are started and patched.</span></span> 
    
- <span data-ttu-id="73bc7-173">백업 및 트랜잭션 로그가 팜 데이터베이스에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-173">Backups and transaction logs are applied to the farm databases.</span></span> 
    
<span data-ttu-id="73bc7-174">다음 목록에서는 콜드 대기 환경에 대 한 추가 절차에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-174">The following list describes additional procedures for cold standby environments:</span></span> 
  
- <span data-ttu-id="73bc7-175">가상 컴퓨터를 정기적으로 켜서 환경을 패치, 업데이트 및 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-175">Turn on virtual machines regularly to patch, update, and verify the environment.</span></span> 
    
- <span data-ttu-id="73bc7-176">DNS 및 IP 주소를 새로 고치는 절차를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-176">Run procedures to refresh DNS and IP addresses.</span></span> 
    
- <span data-ttu-id="73bc7-177">장애 조치 (failover) 후 SQL AlwaysOn을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-177">Set up SQL AlwaysOn after a failover.</span></span> 
    
<span data-ttu-id="73bc7-178">함께 제공 되는 다이어그램에는 가상 컴퓨터에 대 한 복제 된 복구 환경이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-178">The accompanying diagram shows a replicated recovery environment on virtual machines.</span></span> <span data-ttu-id="73bc7-179">콜드 대기 환경으로 장애 조치 (failover) 후에는 모든 가상 컴퓨터가 시작 되 고 가용성 그룹은 재생 로그를 사용 하 여 데이터베이스 서버를 사용할 수 있게 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-179">After failover to a cold standby environment, all virtual machines are started, and the availability groups are configured using replay logs to make the database servers available.</span></span> 
  
## <a name="sharepoint-recovery-environment-in-azure"></a><span data-ttu-id="73bc7-180">Azure의 SharePoint 복구 환경</span><span class="sxs-lookup"><span data-stu-id="73bc7-180">SharePoint recovery environment in Azure</span></span>

<span data-ttu-id="73bc7-181">Azure에서 장애 조치 (failover) 환경 설계 및 구축</span><span class="sxs-lookup"><span data-stu-id="73bc7-181">Design and build the failover environment in Azure.</span></span> 
  
- <span data-ttu-id="73bc7-182">Azure에서 가상 네트워크를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-182">Create a virtual network in Azure.</span></span> 
    
- <span data-ttu-id="73bc7-183">사이트 간 VPN 연결을 사용 하 여 온-프레미스 네트워크를 Azure의 가상 네트워크와 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-183">Connect the on-premises network with the virtual network in Azure with a site-to-site VPN connection.</span></span> <span data-ttu-id="73bc7-184">이 연결은 Azure에서 동적 게이트웨이를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-184">This connection uses a dynamic gateway in Azure.</span></span> 
    
- <span data-ttu-id="73bc7-185">하나 이상의 도메인 컨트롤러를 Azure virtual network에 배포 하 고 온-프레미스 도메인과 함께 작동 하도록이를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-185">Deploy one or more domain controllers to the Azure virtual network, and configure these to work with your on-premises domain.</span></span> <span data-ttu-id="73bc7-186">이러한 도메인 컨트롤러는 카탈로그 서버입니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-186">These domain controllers are catalog servers.</span></span> 
    
- <span data-ttu-id="73bc7-187">클라우드 서비스 및 가용성 집합에 대 한 SharePoint 팜을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-187">Adapt the SharePoint farm for cloud services and availability sets.</span></span> 
    
- <span data-ttu-id="73bc7-188">파일 공유를 호스트 하기 위해 SharePoint 팜과 파일 서버를 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-188">Deploy the SharePoint farm plus a file server to host file shares.</span></span> 
    
- <span data-ttu-id="73bc7-189">온-프레미스 환경과 Azure 기반 복구 환경 사이에 로그 전달 및 DFSR을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-189">Set up log shipping and DFSR between the on-premises environment and the Azure-based recovery environment.</span></span> 
    
<span data-ttu-id="73bc7-190">함께 제공 되는 다이어그램에서는 다음과 같은 기능을 가진 온-프레미스 환경과 Azure virtual network를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-190">The accompanying diagram shows the on-premises environment and the Azure virtual network with the following features:</span></span> 
  
### <a name="on-premises-environment"></a><span data-ttu-id="73bc7-191">온-프레미스 환경</span><span class="sxs-lookup"><span data-stu-id="73bc7-191">On-premises environment</span></span>

- <span data-ttu-id="73bc7-192">Windows Server 2012 RRAS</span><span class="sxs-lookup"><span data-stu-id="73bc7-192">Windows Server 2012 RRAS</span></span> 
    
- <span data-ttu-id="73bc7-193">Active Directory 서버</span><span class="sxs-lookup"><span data-stu-id="73bc7-193">Active Directory server</span></span> 
    
<span data-ttu-id="73bc7-194">VPN (가상 사설망) 게이트웨이를 통해 Azure virtual network와의 온-프레미스 네트워크 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-194">The on-premises network interfaces with the Azure virtual network over a virtual private network (VPN) gateway.</span></span> 
  
### <a name="azure-virtual-network"></a><span data-ttu-id="73bc7-195">Azure virtual network</span><span class="sxs-lookup"><span data-stu-id="73bc7-195">Azure virtual network</span></span>

<span data-ttu-id="73bc7-196">VPN 게이트웨이는 활성 VPN 게이트웨이 서브넷과 상호 작용 합니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-196">The VPN gateway interfaces with an active VPN gateway subnet.</span></span> 
  
<span data-ttu-id="73bc7-197">Azure virtual network에는 다음과 같은 세 가지 클라우드 서비스가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-197">There are three cloud services in the Azure virtual network:</span></span> 
  
- <span data-ttu-id="73bc7-198">첫 번째 클라우드 서비스에 가용성 집합이 있는 Active Directory 및 DNS 서버가 두 개 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-198">The first cloud service has two Active Directory and DNS servers with an availability set.</span></span> 
    
- <span data-ttu-id="73bc7-199">두 번째 클라우드 서비스는 가용성 집합이 있는 두 개의 분산 캐시 서버와 세 개의 서버 집합을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-199">The second cloud service has three sets of servers: Two distributed cache servers with an availability set.</span></span> <span data-ttu-id="73bc7-200">가용성 집합이 포함 된 프런트 엔드 서버 2 대</span><span class="sxs-lookup"><span data-stu-id="73bc7-200">Two front-end servers with an availability set.</span></span> <span data-ttu-id="73bc7-201">가용성 집합을 포함 하는 세 백 엔드 서버</span><span class="sxs-lookup"><span data-stu-id="73bc7-201">Three backend servers with an availability set.</span></span>
    
- <span data-ttu-id="73bc7-202">세 번째 클라우드 서비스에는 가용성 집합이 있는 데이터베이스 서버가 세 개 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-202">The third cloud service has three database servers with an availability set.</span></span> <span data-ttu-id="73bc7-203">이러한 데이터베이스 서버 중 하나는 로그 전달에 대 한 파일 공유이 고, SQL Server AlwaysOn에 대 한 노드 과반수의 세 번째 노드입니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-203">One of these database servers is a file share for log shipping and a third node of a node majority for SQL Server AlwaysOn.</span></span> 
    
### <a name="build-the-ad-ds-hybrid-environment"></a><span data-ttu-id="73bc7-204">AD DS 하이브리드 환경 구축</span><span class="sxs-lookup"><span data-stu-id="73bc7-204">Build the AD DS hybrid environment</span></span>

<span data-ttu-id="73bc7-205">이 솔루션에 대 한 AD DS의 구성은 AD DS가 부분적으로 온-프레미스에 배포 되 고 Azure 가상 컴퓨터에 부분적으로 배포 되는 하이브리드 배포 시나리오를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-205">The configuration of AD DS for this solution constitutes a hybrid deployment scenario in which AD DS is partly deployed on-premises and partly deployed on Azure virtual machines.</span></span> 
  
<span data-ttu-id="73bc7-206">중요 — Azure에서 AD DS를 배포 하기 전에 Microsoft Azure 가상 컴퓨터 (http://msdn.microsoft.com/en-us/library/windowsazure/jj156090.aspx)에 Windows Server Active Directory를 배포 하기 위한 지침을 읽어 보십시오.</span><span class="sxs-lookup"><span data-stu-id="73bc7-206">Important — Before you deploy AD DS in Azure, read Guidelines for Deploying Windows Server Active Directory on Microsoft Azure Virtual Machines (http://msdn.microsoft.com/en-us/library/windowsazure/jj156090.aspx).</span></span> 
  
<span data-ttu-id="73bc7-207">Active Directory 환경의 디자인 및 배포에 대 한 자세한 지침은를 http://TechNet.microsoft.com참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="73bc7-207">For complete guidance on designing and deploying Active Directory environments, see http://TechNet.microsoft.com.</span></span> 
  
<span data-ttu-id="73bc7-208">이 참조 아키텍처에는 도메인 컨트롤러로 구성 된 두 개의 가상 컴퓨터가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-208">This reference architecture includes two virtual machines configured as domain controllers.</span></span> <span data-ttu-id="73bc7-209">각 형식은 다음과 같이 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-209">Each is configured as follows:</span></span> 
  
- <span data-ttu-id="73bc7-210">크기-작음</span><span class="sxs-lookup"><span data-stu-id="73bc7-210">Size — Small.</span></span> 
    
- <span data-ttu-id="73bc7-211">운영 체제-Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="73bc7-211">Operating system — Windows Server 2012.</span></span> 
    
- <span data-ttu-id="73bc7-212">Role-글로벌 카탈로그 서버로 지정 된 AD DS 도메인 컨트롤러입니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-212">Role — AD DS domain controller designated as a global catalog server.</span></span> <span data-ttu-id="73bc7-213">이 구성은 VPN 연결을 통해 송신 트래픽을 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-213">This configuration reduces egress traffic across the VPN connection.</span></span> <span data-ttu-id="73bc7-214">변경 비율이 높은 다중 도메인 환경에서는 온-프레미스 도메인 컨트롤러를 구성 하 여 Azure의 글로벌 카탈로그 서버와 동기화 되지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-214">In a multi-domain environment with high rates of change, configure domain controllers on-premises to not sync with the global catalog servers in Azure.</span></span> 
    
- <span data-ttu-id="73bc7-215">데이터 디스크-Azure 데이터 디스크에 AD DS 데이터베이스, 로그 및 SYSVOL을 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-215">Data disks — Place the AD DS database, logs, and SYSVOL on Azure data disks.</span></span> <span data-ttu-id="73bc7-216">이를 운영 체제 디스크 또는 Azure에서 제공 하는 임시 디스크에 배치 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="73bc7-216">Do not place these on the operating system disk or the temporary disks provided by Azure.</span></span> <span data-ttu-id="73bc7-217">이는 중요 한 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-217">This is important.</span></span> 
    
- <span data-ttu-id="73bc7-218">역할 — 도메인 컨트롤러에 Windows DNS를 설치 하 고 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-218">Role — Install and configure Windows DNS on the domain controllers.</span></span> 
    
- <span data-ttu-id="73bc7-219">IP 주소-동적 IP 주소를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-219">IP addresses — Use dynamic IP addresses.</span></span> <span data-ttu-id="73bc7-220">이렇게 하려면 Azure Virtual Network를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="73bc7-220">This requires you to create an Azure Virtual Network.</span></span> 
    

