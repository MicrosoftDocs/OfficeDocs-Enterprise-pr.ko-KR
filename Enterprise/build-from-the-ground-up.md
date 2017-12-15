---
title: "처음부터 만들기"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 84348d0c-d9d1-4a98-9b99-8433f9b70e45
description: "요약: 클라우드 집합에 대 한 자세한 내용은 직접 저장소 서비스 또는 솔루션 만들기를 사용할 수 있는 저장소 구성 요소를 가져옵니다."
ms.openlocfilehash: 18aa8cb7fa0dda05302a88487dcc69bdbcb174d5
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2017
---
# <a name="build-from-the-ground-up"></a><span data-ttu-id="cd1ab-103">처음부터 만들기</span><span class="sxs-lookup"><span data-stu-id="cd1ab-103">Build from the ground up</span></span>

 <span data-ttu-id="cd1ab-104">**요약:** 클라우드 집합에 정보를 직접 저장소 서비스 또는 솔루션을 만드는데 사용할 수 있는 저장소 구성 요소를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="cd1ab-104">**Summary:** Get the details on the set of cloud storage building blocks that you can use to create your own storage service or solution.</span></span>
  
<span data-ttu-id="cd1ab-105">"처음부터 구축" 저장소 솔루션:</span><span class="sxs-lookup"><span data-stu-id="cd1ab-105">"Build from the ground up" storage solutions:</span></span>
  
- <span data-ttu-id="cd1ab-106">이 기능을 사용 하면 처음부터 직접 저장소 솔루션을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd1ab-106">Allow you to create your own storage solution from scratch.</span></span> 
    
- <span data-ttu-id="cd1ab-107">REST Api를 사용 하 여 프로그래밍이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd1ab-107">Requires programming using the REST APIs.</span></span>
    
- <span data-ttu-id="cd1ab-108">최상의 사용자 지정 및 유연성을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd1ab-108">Provide the ultimate in customization and flexibility.</span></span>
    
<span data-ttu-id="cd1ab-109">다음 섹션에서는 각 "처음부터 구축" 저장소 옵션에 대 한 세부 정보에 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd1ab-109">The following sections describe the details of each "Build from the ground up" storage option.</span></span>
  
## <a name="azure-storage-files"></a><span data-ttu-id="cd1ab-110">Azure 저장소 (파일)</span><span class="sxs-lookup"><span data-stu-id="cd1ab-110">Azure Storage (files)</span></span>

### <a name="features"></a><span data-ttu-id="cd1ab-111">기능</span><span class="sxs-lookup"><span data-stu-id="cd1ab-111">Features</span></span>

- <span data-ttu-id="cd1ab-112">쉽게 클라우드로 레거시 응용 프로그램을 이동 하려면</span><span class="sxs-lookup"><span data-stu-id="cd1ab-112">Makes it easier to move legacy applications to the cloud</span></span>
    
- <span data-ttu-id="cd1ab-113">새 응용 프로그램에 대 한 기본적으로 사용 되는 blob 저장소</span><span class="sxs-lookup"><span data-stu-id="cd1ab-113">Blob storage preferred for new applications</span></span>
    
- <span data-ttu-id="cd1ab-114">Azure 가상 컴퓨터에서 탑재할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd1ab-114">Can mount from an Azure virtual machine</span></span>
    
- <span data-ttu-id="cd1ab-115">온-프레미스 SMB 3.0 탑재할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd1ab-115">Can mount on-premises with SMB 3.0</span></span>
    
- <span data-ttu-id="cd1ab-116">Windows 및 Linux로 작업</span><span class="sxs-lookup"><span data-stu-id="cd1ab-116">Works with Linux and Windows</span></span>
    
- <span data-ttu-id="cd1ab-117">지원 하지 않는 Azure AD 기반 인증 또는 Acl (Azure 저장소 계정 키 인증 및 파일 공유에 대 한 권한이 부여 된 액세스를 제공)</span><span class="sxs-lookup"><span data-stu-id="cd1ab-117">Doesn't support Azure AD-based authentication or ACLs (Azure Storage account keys provide authentication and authorized access to the file share)</span></span>
    
### <a name="common-uses"></a><span data-ttu-id="cd1ab-118">일반적으로 사용</span><span class="sxs-lookup"><span data-stu-id="cd1ab-118">Common uses</span></span>

- <span data-ttu-id="cd1ab-119">파일 공유를 사용 하는 클라우드로 레거시 응용 프로그램 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="cd1ab-119">Migrating legacy applications to the cloud that rely on file shares</span></span>
    
- <span data-ttu-id="cd1ab-120">개발 및 테스트 도구를 공유 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd1ab-120">Share development and testing tools</span></span>
    
- <span data-ttu-id="cd1ab-121">분산된 응용 프로그램에서 로그, 진단 데이터를 저장 하 고 크래시 덤프 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd1ab-121">Distributed apps can store logs, diagnostic data, and crash dumps</span></span>
    
### <a name="key-storage-scenarios"></a><span data-ttu-id="cd1ab-122">키 저장소 시나리오</span><span class="sxs-lookup"><span data-stu-id="cd1ab-122">Key storage scenarios</span></span>

- <span data-ttu-id="cd1ab-123">백업 파일</span><span class="sxs-lookup"><span data-stu-id="cd1ab-123">Backup files</span></span>
    
### <a name="resources"></a><span data-ttu-id="cd1ab-124">리소스</span><span class="sxs-lookup"><span data-stu-id="cd1ab-124">Resources</span></span>

<span data-ttu-id="cd1ab-125">자세한 내용은 [여기](https://msdn.microsoft.com/library/azure/dn166972.aspx)합니다.</span><span class="sxs-lookup"><span data-stu-id="cd1ab-125">For additional information, click [here](https://msdn.microsoft.com/library/azure/dn166972.aspx).</span></span>
  
<span data-ttu-id="cd1ab-126">비용 정보에 대 한 클릭 [여기](http://azure.microsoft.com/pricing/details/storage/)합니다.</span><span class="sxs-lookup"><span data-stu-id="cd1ab-126">For cost information, click [here](http://azure.microsoft.com/pricing/details/storage/).</span></span>
  
## <a name="azure-storage-blobs"></a><span data-ttu-id="cd1ab-127">Azure 저장소 (blob)</span><span class="sxs-lookup"><span data-stu-id="cd1ab-127">Azure Storage (blobs)</span></span>

### <a name="features"></a><span data-ttu-id="cd1ab-128">기능</span><span class="sxs-lookup"><span data-stu-id="cd1ab-128">Features</span></span>

- <span data-ttu-id="cd1ab-129">각 저장소 계정에는 최대 500 TB 보유할 수 있습니다 (하나의 구독 수 계정이 여러 개인 저장소)</span><span class="sxs-lookup"><span data-stu-id="cd1ab-129">Each storage account can hold up to 500 TB (one subscription can have multiple storage accounts)</span></span>
    
- <span data-ttu-id="cd1ab-130">저장소 계정은 자신에 게 적용 되는 보안 하 고 blob가 포함 될 수 있는 컨테이너 구조로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd1ab-130">Storage accounts are organized into containers, which can have security applied to them and can contain blobs</span></span>
    
- <span data-ttu-id="cd1ab-131">블록 blob가 스트리밍에 최적화 된 및 최대 200GB 크기의 개체, 클라우드를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd1ab-131">Block blobs are optimized for streaming and storing cloud objects, up to 200 GB in size</span></span>
    
- <span data-ttu-id="cd1ab-132">페이지 blob가 나타내는 PaaS 디스크에 최적화 된 및 기록 임의 지 원하는 최대 1TB 크기</span><span class="sxs-lookup"><span data-stu-id="cd1ab-132">Page blobs are optimized for representing PaaS disks and supporting random writes, up to 1 TB in size</span></span>
    
- <span data-ttu-id="cd1ab-133">Append blob에 최적화 된 작업을 추가할 최대 195 g B</span><span class="sxs-lookup"><span data-stu-id="cd1ab-133">Append blobs are optimized for append operations, up to 195 GB</span></span>
    
- <span data-ttu-id="cd1ab-134">프리미엄 저장소 SSD 저장소를 통해 더 빠른 IOPS를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="cd1ab-134">Premium Storage provides faster IOPS through SSD storage</span></span>
    
### <a name="common-uses"></a><span data-ttu-id="cd1ab-135">일반적으로 사용</span><span class="sxs-lookup"><span data-stu-id="cd1ab-135">Common uses</span></span>

- <span data-ttu-id="cd1ab-136">파일, 컴퓨터, 데이터베이스 및 장치 이미지 및 웹 응용 프로그램에 대 한 텍스트의 백업</span><span class="sxs-lookup"><span data-stu-id="cd1ab-136">Backups of files, computers, databases, and devices Images and text for web applications</span></span>
    
- <span data-ttu-id="cd1ab-137">클라우드 응용 프로그램에 대 한 구성 데이터</span><span class="sxs-lookup"><span data-stu-id="cd1ab-137">Configuration data for cloud applications</span></span>
    
- <span data-ttu-id="cd1ab-138">예: 로그 및 기타 큰 데이터 집합의 큰 데이터</span><span class="sxs-lookup"><span data-stu-id="cd1ab-138">Big data, such as logs and other large datasets</span></span>
    
- <span data-ttu-id="cd1ab-139">Azure 사용 하 여 blob HDInsight 및 가상 컴퓨터 디스크 등의 자체 서비스에 대 한 저장소</span><span class="sxs-lookup"><span data-stu-id="cd1ab-139">Azure uses blob storage for its own services, such as HDInsight and virtual machine disks</span></span>
    
### <a name="key-storage-scenarios"></a><span data-ttu-id="cd1ab-140">키 저장소 시나리오</span><span class="sxs-lookup"><span data-stu-id="cd1ab-140">Key storage scenarios</span></span>

- <span data-ttu-id="cd1ab-141">데이터 관리</span><span class="sxs-lookup"><span data-stu-id="cd1ab-141">Manage data</span></span>
    
### <a name="resources"></a><span data-ttu-id="cd1ab-142">리소스</span><span class="sxs-lookup"><span data-stu-id="cd1ab-142">Resources</span></span>

<span data-ttu-id="cd1ab-143">자세한 내용은 [여기](https://msdn.microsoft.com/library/azure/dd179376.aspx)합니다.</span><span class="sxs-lookup"><span data-stu-id="cd1ab-143">For additional information, click [here](https://msdn.microsoft.com/library/azure/dd179376.aspx).</span></span>
  
<span data-ttu-id="cd1ab-144">비용 정보에 대 한 클릭 [여기](http://azure.microsoft.com/pricing/details/storage/)합니다.</span><span class="sxs-lookup"><span data-stu-id="cd1ab-144">For cost information, click [here](http://azure.microsoft.com/pricing/details/storage/).</span></span>
  
## <a name="azure-storage-queues"></a><span data-ttu-id="cd1ab-145">Azure 저장소 (큐의 경우)</span><span class="sxs-lookup"><span data-stu-id="cd1ab-145">Azure Storage (queues)</span></span>

### <a name="features"></a><span data-ttu-id="cd1ab-146">기능</span><span class="sxs-lookup"><span data-stu-id="cd1ab-146">Features</span></span>

- <span data-ttu-id="cd1ab-147">저장소 계정에는 큐의 숫자 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd1ab-147">Storage account can contain any number of queues</span></span>
    
- <span data-ttu-id="cd1ab-148">(있을 때까지 저장소 계정의 전체) 큐에서 메시지의 숫자를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd1ab-148">Queue can contain any number of messages (until the storage account is full)</span></span>
    
- <span data-ttu-id="cd1ab-149">메시지 큐는 자동으로 7 일이 지난 후에 삭제 된 값이 없는 경우 검색 및 삭제 된 응용 프로그램에 의해</span><span class="sxs-lookup"><span data-stu-id="cd1ab-149">Queue messages are automatically deleted after seven days if not retrieved and deleted by an application</span></span>
    
- <span data-ttu-id="cd1ab-150">메시지 크기에서 64KB 최대 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd1ab-150">Messages may be up to 64 KB in size</span></span>
    
- <span data-ttu-id="cd1ab-151">저장소 계정 수준 보안</span><span class="sxs-lookup"><span data-stu-id="cd1ab-151">Secured at storage account level</span></span>
    
- <span data-ttu-id="cd1ab-152">큐는 제어 메시지를 하지 원시 데이터를 전달 하기 위한 것</span><span class="sxs-lookup"><span data-stu-id="cd1ab-152">Queues are intended to pass control messages, not raw data</span></span>
    
### <a name="common-uses"></a><span data-ttu-id="cd1ab-153">일반적으로 사용</span><span class="sxs-lookup"><span data-stu-id="cd1ab-153">Common uses</span></span>

- <span data-ttu-id="cd1ab-154">비동기적으로 처리 된 작업의 백로그 만들기</span><span class="sxs-lookup"><span data-stu-id="cd1ab-154">Create a backlog of work to process asynchronously</span></span>
    
- <span data-ttu-id="cd1ab-155">로그 메시지 처리</span><span class="sxs-lookup"><span data-stu-id="cd1ab-155">Processing log messages</span></span>
    
- <span data-ttu-id="cd1ab-156">응용 프로그램을 분리</span><span class="sxs-lookup"><span data-stu-id="cd1ab-156">Decouple applications</span></span>
    
### <a name="key-storage-scenarios"></a><span data-ttu-id="cd1ab-157">키 저장소 시나리오</span><span class="sxs-lookup"><span data-stu-id="cd1ab-157">Key storage scenarios</span></span>

- <span data-ttu-id="cd1ab-158">이벤트를 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd1ab-158">Distribute events</span></span>
    
### <a name="resources"></a><span data-ttu-id="cd1ab-159">리소스</span><span class="sxs-lookup"><span data-stu-id="cd1ab-159">Resources</span></span>

<span data-ttu-id="cd1ab-160">자세한 내용은 [여기](https://msdn.microsoft.com/library/azure/dd179353.aspx)합니다.</span><span class="sxs-lookup"><span data-stu-id="cd1ab-160">For additional information, click [here](https://msdn.microsoft.com/library/azure/dd179353.aspx).</span></span>
  
<span data-ttu-id="cd1ab-161">비용 정보에 대 한 클릭 [여기](http://azure.microsoft.com/pricing/details/storage/)합니다.</span><span class="sxs-lookup"><span data-stu-id="cd1ab-161">For cost information, click [here](http://azure.microsoft.com/pricing/details/storage/).</span></span>
  
## <a name="azure-storage-tables"></a><span data-ttu-id="cd1ab-162">Azure 저장소 (표)</span><span class="sxs-lookup"><span data-stu-id="cd1ab-162">Azure Storage (tables)</span></span>

### <a name="features"></a><span data-ttu-id="cd1ab-163">기능</span><span class="sxs-lookup"><span data-stu-id="cd1ab-163">Features</span></span>

- <span data-ttu-id="cd1ab-164">반구조적된 데이터 집합에 가장 적합 한</span><span class="sxs-lookup"><span data-stu-id="cd1ab-164">Best for semi-structured datasets</span></span>
    
- <span data-ttu-id="cd1ab-165">기존 SQL 보다 일반적으로 더 낮은 비용</span><span class="sxs-lookup"><span data-stu-id="cd1ab-165">Typically lower cost than traditional SQL</span></span>
    
- <span data-ttu-id="cd1ab-166">초고속 값에 대 한 쿼리 하는 경우 느린 키로 이동한 다음에 대 한 쿼리 하는 경우</span><span class="sxs-lookup"><span data-stu-id="cd1ab-166">Very fast if querying for key, slow if querying for value</span></span>
    
- <span data-ttu-id="cd1ab-167">확장성이 매우 높은; 저장소 계정의 제한 최대 테이블의 모든 크기</span><span class="sxs-lookup"><span data-stu-id="cd1ab-167">Massively scalable; any amount of tables up to the limits of the storage account</span></span>
    
- <span data-ttu-id="cd1ab-168">REST API,.NET, 제한 된 oData 프로토콜을 통해 액세스할 수 있음</span><span class="sxs-lookup"><span data-stu-id="cd1ab-168">Accessible through REST API, limited oData protocol, .NET</span></span>
    
- <span data-ttu-id="cd1ab-169">값을 직렬화 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd1ab-169">Values must be serialized</span></span>
    
### <a name="common-uses"></a><span data-ttu-id="cd1ab-170">일반적으로 사용</span><span class="sxs-lookup"><span data-stu-id="cd1ab-170">Common uses</span></span>

- <span data-ttu-id="cd1ab-171">웹 응용 프로그램에 대 한 사용자 데이터</span><span class="sxs-lookup"><span data-stu-id="cd1ab-171">User data for web applications</span></span>
    
- <span data-ttu-id="cd1ab-172">주소록</span><span class="sxs-lookup"><span data-stu-id="cd1ab-172">Address books</span></span>
    
- <span data-ttu-id="cd1ab-173">장치 정보</span><span class="sxs-lookup"><span data-stu-id="cd1ab-173">Device information</span></span>
    
### <a name="key-storage-scenarios"></a><span data-ttu-id="cd1ab-174">키 저장소 시나리오</span><span class="sxs-lookup"><span data-stu-id="cd1ab-174">Key storage scenarios</span></span>

- <span data-ttu-id="cd1ab-175">데이터 관리</span><span class="sxs-lookup"><span data-stu-id="cd1ab-175">Manage data</span></span>
    
### <a name="resources"></a><span data-ttu-id="cd1ab-176">리소스</span><span class="sxs-lookup"><span data-stu-id="cd1ab-176">Resources</span></span>

<span data-ttu-id="cd1ab-177">자세한 내용은 [여기](https://msdn.microsoft.com/library/azure/dd179463.aspx)합니다.</span><span class="sxs-lookup"><span data-stu-id="cd1ab-177">For additional information, click [here](https://msdn.microsoft.com/library/azure/dd179463.aspx).</span></span>
  
<span data-ttu-id="cd1ab-178">비용 정보에 대 한 클릭 [여기](http://azure.microsoft.com/pricing/details/storage/)합니다.</span><span class="sxs-lookup"><span data-stu-id="cd1ab-178">For cost information, click [here](http://azure.microsoft.com/pricing/details/storage/).</span></span>
  
## <a name="microsoft-azure-storage-recommendations"></a><span data-ttu-id="cd1ab-179">Microsoft Azure 저장소 권장 사항</span><span class="sxs-lookup"><span data-stu-id="cd1ab-179">Microsoft Azure Storage recommendations</span></span>

<span data-ttu-id="cd1ab-180">Azure 저장소와 사용자 지정 저장소 솔루션을 디자인할 때 다음 사항에 유의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd1ab-180">When designing your custom storage solution with Azure Storage, keep the following in mind:</span></span>
  
- <span data-ttu-id="cd1ab-181">여러 저장소 계정을 증가 크기 (> 100 테라바이트)에 대 한 또는 더 많은 처리량 (초당 5, 000 개 > 작업)에 대 한 확장성이 높아집니다을 활용 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd1ab-181">Leverage multiple storage accounts for greater scalability, either for increased size (> 100 TB) or for more throughput (> 5,000 operations per second).</span></span>
    
- <span data-ttu-id="cd1ab-182">구성 변경 사항으로, 코드 변경 사항으로 하지 추가 저장소 계정을 추가할 수 있는 기능을 디자인 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd1ab-182">Design the ability for adding additional storage accounts as a configuration change, not as a code change.</span></span>
    
- <span data-ttu-id="cd1ab-183">신중 하 게 삽입 및 쿼리 성능 면에서 원하는 확장을 사용 하도록 설정 하려면 테이블 저장소에 대 한 분할 기능을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd1ab-183">Carefully select partitioning functions for table storage to enable the desired scale in terms of insert and query performance.</span></span>
    
- <span data-ttu-id="cd1ab-184">메타 데이터 (속성 이름)으로 테이블 속성에 대 한 짧은 열 이름이 저장된 인밴드 (계산 최대 행 크기는 1MB 향해 열 이름)을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd1ab-184">Choose short column names for table properties as the metadata (property names) are stored in-band (the column names also count towards the maximum row size of 1 MB).</span></span>
    
- <span data-ttu-id="cd1ab-185">가능 하면 저장소에 대 한 작업을 일괄 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd1ab-185">When possible, batch operations into storage.</span></span>
    
- <span data-ttu-id="cd1ab-186">분산된 캐시를 구성 데이터베이스에 대 한 정보를 적극적으로 캐시 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd1ab-186">Aggressively cache information in the configuration database into a distributed cache.</span></span>
    
- <span data-ttu-id="cd1ab-187">응용 프로그램의 성능이 나 신뢰성 이면 캐시에서 사용할 수 있는 데이터의 특정 세그먼트를 필요에 따라 다릅니다 응용 프로그램 캐시 미리 채워진 될 때까지 들어오는 요청을 거부 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd1ab-187">If application performance or reliability is dependent on having a certain segment of data available in the cache, your application should refuse incoming requests until the cache has been pre-populated.</span></span>
    
- <span data-ttu-id="cd1ab-188">여러 데이터베이스에는 부하 분산을 데이터 또는 가로에서 세로로 (테이블에 의해) (여러 파편 간에 세그먼트 테이블)으로 분할 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd1ab-188">Partition the data in either vertically (by table) or horizontally (segment table across multiple shards) to spread the load across multiple databases.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="cd1ab-189">See Also</span><span class="sxs-lookup"><span data-stu-id="cd1ab-189">See Also</span></span>

[<span data-ttu-id="cd1ab-190">엔터프라이즈 설계자 용 Microsoft 클라우드 저장소</span><span class="sxs-lookup"><span data-stu-id="cd1ab-190">Microsoft Cloud Storage for Enterprise Architects</span></span>](microsoft-cloud-storage-for-enterprise-architects.md)
  
[<span data-ttu-id="cd1ab-191">Microsoft 클라우드 IT 아키텍처 리소스</span><span class="sxs-lookup"><span data-stu-id="cd1ab-191">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="cd1ab-192">Microsoft의 엔터프라이즈 클라우드 로드맵: IT 의사 결정권자를 위한 리소스</span><span class="sxs-lookup"><span data-stu-id="cd1ab-192">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



