---
title: Microsoft 클라우드에 대한 저장소 디자인
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 7e511118-1b75-413a-b959-ad0d3ffc9516
description: 요약:는 클라우드 저장소 필요한 이유를 이해 하 고 Microsoft의 클라우드 저장소 옵션 및 키 저장소 시나리오 목록을 검토 합니다.
ms.openlocfilehash: d96992d63115095dd6a1b7277886d0a4bb2bc02f
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915233"
---
# <a name="designing-storage-for-the-microsoft-cloud"></a><span data-ttu-id="54996-103">Microsoft 클라우드에 대한 저장소 디자인</span><span class="sxs-lookup"><span data-stu-id="54996-103">Designing storage for the Microsoft cloud</span></span>

 <span data-ttu-id="54996-104">**요약:** 클라우드 저장소 필요한 이유를 이해 하 고 Microsoft의 클라우드 저장소 옵션 및 키 저장소 시나리오 목록을 검토 합니다.</span><span class="sxs-lookup"><span data-stu-id="54996-104">**Summary:** Understand why you need cloud storage and review the list of Microsoft's cloud storage options and the key storage scenarios.</span></span>
  
<span data-ttu-id="54996-105">Microsoft 클라우드 서비스와 함께 저장 장치를 통합 (영문) 광범위 한 서비스 및 클라우드 플랫폼 옵션에 액세스할을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54996-105">Integrating your storage with Microsoft cloud services gives you access to a broad range of services and cloud platform options.</span></span>
  
## <a name="why-cloud-storage"></a><span data-ttu-id="54996-106">이유 클라우드 저장소?</span><span class="sxs-lookup"><span data-stu-id="54996-106">Why cloud storage?</span></span>

<span data-ttu-id="54996-107">클라우드 저장소를 사용 하 여 두 가지 주요 이유가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54996-107">There are two key reasons to use cloud storage.</span></span>
  
1. <span data-ttu-id="54996-108">에 대 한 시장 속도:</span><span class="sxs-lookup"><span data-stu-id="54996-108">Speed to market:</span></span>
    
  - <span data-ttu-id="54996-109">고가용성 및 재해 복구에 대 한 빠른 구성</span><span class="sxs-lookup"><span data-stu-id="54996-109">Faster configuration for high availability and disaster recovery</span></span>
    
  - <span data-ttu-id="54996-110">없음 저장소 하드웨어를 구입</span><span class="sxs-lookup"><span data-stu-id="54996-110">No storage hardware to purchase</span></span>
    
  - <span data-ttu-id="54996-111">Microsoft의 클라우드 서비스에서 제공 하는 기본 제공 내부 작업</span><span class="sxs-lookup"><span data-stu-id="54996-111">Built-in plumbing provided by Microsoft's cloud offerings</span></span>
    
  - <span data-ttu-id="54996-112">전세계 각 지역에서에서 사용할 수 있는</span><span class="sxs-lookup"><span data-stu-id="54996-112">Available from anywhere in the world</span></span>
    
2. <span data-ttu-id="54996-113">유지 관리 비용 절감:</span><span class="sxs-lookup"><span data-stu-id="54996-113">Lower costs to maintain:</span></span>
    
  - <span data-ttu-id="54996-114">탄성 저장소 요구 사항에 맞는 위쪽 및 아래쪽 비율을 조정 하려면</span><span class="sxs-lookup"><span data-stu-id="54996-114">Elasticity to scale up and down your storage demands</span></span>
    
  - <span data-ttu-id="54996-115">없음 저장소 하드웨어를 유지 하거나 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="54996-115">No storage hardware to maintain or migrate</span></span>
    
  - <span data-ttu-id="54996-116">Microsoft는 유지 관리 하 고 인프라를 개선 하 여 기본 제공 배관공</span><span class="sxs-lookup"><span data-stu-id="54996-116">Microsoft is your built-in plumber to maintain and improve infrastructure</span></span>
    
  - <span data-ttu-id="54996-117">진행 중인 향상 된 시장에서 최상의 저장소 보안</span><span class="sxs-lookup"><span data-stu-id="54996-117">Best storage security in the marketplace with ongoing improvements</span></span>
    
## <a name="microsoft-cloud-storage-options"></a><span data-ttu-id="54996-118">Microsoft 클라우드 저장소 옵션</span><span class="sxs-lookup"><span data-stu-id="54996-118">Microsoft cloud storage options</span></span>

<span data-ttu-id="54996-119">다양 한 클라우드 저장소 옵션을 쉽게 이해할 수 있도록, 건설 유추를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="54996-119">To help you understand the wide variety of cloud storage options, we use a construction analogy.</span></span>
  
### <a name="move-in-ready"></a><span data-ttu-id="54996-120">이동 준비 완료</span><span class="sxs-lookup"><span data-stu-id="54996-120">Move-in ready</span></span>

<span data-ttu-id="54996-p101">기존 서비스와 함께 제공 되는 이러한 미리 패키지 된 솔루션을 사용 합니다. 즉시 및 최소한의 구성으로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="54996-p101">Use these prepackaged solutions that are bundled with existing services. Use immediately and with minimal configuration.</span></span>
  
- <span data-ttu-id="54996-123">Office 365</span><span class="sxs-lookup"><span data-stu-id="54996-123">Office 365</span></span>
    
- <span data-ttu-id="54996-124">Microsoft Intune</span><span class="sxs-lookup"><span data-stu-id="54996-124">Microsoft Intune</span></span>
    
- <span data-ttu-id="54996-125">비즈니스용 OneDrive</span><span class="sxs-lookup"><span data-stu-id="54996-125">OneDrive for Business</span></span>
    
- <span data-ttu-id="54996-126">Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="54996-126">Dynamics 365</span></span>
    
- <span data-ttu-id="54996-127">Visual Studio Team Services</span><span class="sxs-lookup"><span data-stu-id="54996-127">Visual Studio Team Services</span></span>
    
- <span data-ttu-id="54996-128">Azure Site Recovery</span><span class="sxs-lookup"><span data-stu-id="54996-128">Azure Site Recovery</span></span>
    
- <span data-ttu-id="54996-129">Yammer 사이트 공유</span><span class="sxs-lookup"><span data-stu-id="54996-129">Yammer Site Sharing</span></span>
    
- <span data-ttu-id="54996-130">Azure 백업</span><span class="sxs-lookup"><span data-stu-id="54996-130">Azure Backup</span></span>
    
<span data-ttu-id="54996-131">이러한 각의 세부 정보에 대 한 저장소 옵션 클라우드 [이동-준비](move-in-ready.md)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="54996-131">For the details of each of these cloud storage options, see [Move-in ready](move-in-ready.md).</span></span>
  
### <a name="some-assembly-required"></a><span data-ttu-id="54996-132">일부 필수 어셈블리</span><span class="sxs-lookup"><span data-stu-id="54996-132">Some assembly required</span></span>

<span data-ttu-id="54996-133">이러한 기존 서비스를 사용 하 여 추가 구성을 사용 하 여 저장소 솔루션에 대 한 시작점 또는 사용자 지정 맞춤에 대 한 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="54996-133">Use these existing services as a starting point for your storage solution with additional configuration or coding for a custom fit.</span></span>
  
- <span data-ttu-id="54996-134">Azure 콘텐츠 배달 네트워크</span><span class="sxs-lookup"><span data-stu-id="54996-134">Azure Content Delivery Network</span></span>
    
- <span data-ttu-id="54996-135">Azure 미디어 서비스</span><span class="sxs-lookup"><span data-stu-id="54996-135">Azure Media Services</span></span>
    
- <span data-ttu-id="54996-136">HdInsight</span><span class="sxs-lookup"><span data-stu-id="54996-136">HdInsight</span></span>
    
- <span data-ttu-id="54996-137">Azure 액세스 캐시</span><span class="sxs-lookup"><span data-stu-id="54996-137">Azure Redis Cache</span></span>
    
- <span data-ttu-id="54996-138">Azure SQL 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="54996-138">Azure SQL Database</span></span>
    
- <span data-ttu-id="54996-139">Azure VM에 SQL Server 설치</span><span class="sxs-lookup"><span data-stu-id="54996-139">SQL Server on an Azure VM</span></span>
    
- <span data-ttu-id="54996-140">Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="54996-140">Azure Cosmos DB</span></span>
    
- <span data-ttu-id="54996-141">StorSimple</span><span class="sxs-lookup"><span data-stu-id="54996-141">StorSimple</span></span>
    
- <span data-ttu-id="54996-142">SQL azure 데이터 웨어하우스</span><span class="sxs-lookup"><span data-stu-id="54996-142">Azure SQL Data Warehouse</span></span>
    
- <span data-ttu-id="54996-143">Azure 데이터 호수 저장소</span><span class="sxs-lookup"><span data-stu-id="54996-143">Azure Data Lake Store</span></span>
    
<span data-ttu-id="54996-144">이러한 각 클라우드 저장소 옵션의 세부 정보에 대 한 [일부 어셈블리 필요한](some-assembly-required.md)를 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="54996-144">For the details of each of these cloud storage options, see [Some assembly required](some-assembly-required.md).</span></span>
  
### <a name="build-from-the-ground-up"></a><span data-ttu-id="54996-145">처음부터 새로 구축</span><span class="sxs-lookup"><span data-stu-id="54996-145">Build from the ground up</span></span>

<span data-ttu-id="54996-146">코딩와 함께 이러한 저장소 구성 요소를 사용 하 여 처음부터 직접 앱 또는 저장소 솔루션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="54996-146">Use these storage building blocks, along with coding, to create your own storage solution or apps from scratch.</span></span>
  
- <span data-ttu-id="54996-147">Azure 저장소 (파일)</span><span class="sxs-lookup"><span data-stu-id="54996-147">Azure Storage (files)</span></span>
    
- <span data-ttu-id="54996-148">Azure 저장소 (blob)</span><span class="sxs-lookup"><span data-stu-id="54996-148">Azure Storage (blobs)</span></span>
    
- <span data-ttu-id="54996-149">Azure 저장소 (큐의 경우)</span><span class="sxs-lookup"><span data-stu-id="54996-149">Azure Storage (queues)</span></span>
    
- <span data-ttu-id="54996-150">Azure 저장소 (표)</span><span class="sxs-lookup"><span data-stu-id="54996-150">Azure Storage (tables)</span></span>
    
<span data-ttu-id="54996-151">이러한 각 클라우드 저장소 옵션의 세부 정보를 [처음부터 작성](build-from-the-ground-up.md)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="54996-151">For the details of each of these cloud storage options, see [Build from the ground up](build-from-the-ground-up.md).</span></span>
  
## <a name="key-storage-scenarios"></a><span data-ttu-id="54996-152">키 저장소 시나리오</span><span class="sxs-lookup"><span data-stu-id="54996-152">Key storage scenarios</span></span>

<span data-ttu-id="54996-153">클라우드 기반 저장소를 필요로 하는 주요 시나리오는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="54996-153">Here are the key scenarios that require cloud-based storage:</span></span>
  
- <span data-ttu-id="54996-154">데이터 캐시</span><span class="sxs-lookup"><span data-stu-id="54996-154">Cache data</span></span>
    
    <span data-ttu-id="54996-155">고속 캐시에 저장 하 여 일반적으로 사용 되는 데이터에 대 한 액세스를 가속화 합니다.</span><span class="sxs-lookup"><span data-stu-id="54996-155">Accelerate access to commonly used data by storing it in a high-speed cache.</span></span>
    
- <span data-ttu-id="54996-156">팀 구성원과 공동으로 작업</span><span class="sxs-lookup"><span data-stu-id="54996-156">Collaborate with team members</span></span>
    
    <span data-ttu-id="54996-157">클라우드 저장소에서 데이터에 대 한 액세스를 허용 하려면 여러 사용자에 게 권한을 부여 합니다.</span><span class="sxs-lookup"><span data-stu-id="54996-157">Grant permission to multiple users to allow access to data in cloud storage.</span></span>
    
- <span data-ttu-id="54996-158">데이터 관리</span><span class="sxs-lookup"><span data-stu-id="54996-158">Manage data</span></span>
    
    <span data-ttu-id="54996-159">저장, 이동 또는 내부 또는 외부 대량 데이터를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="54996-159">Store, move, or delete internal or external bulk data.</span></span>
    
- <span data-ttu-id="54996-160">소스 코드 관리</span><span class="sxs-lookup"><span data-stu-id="54996-160">Manage source code</span></span>
    
    <span data-ttu-id="54996-161">업로드 하 고 공동 작업, 클라우드에서 응용 프로그램 코드 파일을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="54996-161">Upload, collaborate, and run application code files in the cloud.</span></span>
    
- <span data-ttu-id="54996-162">백업 파일</span><span class="sxs-lookup"><span data-stu-id="54996-162">Backup files</span></span>
    
    <span data-ttu-id="54996-163">여러 클라우드 위치에서 내부 또는 외부 데이터 오프 사이트의 복사본을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="54996-163">Store copies of internal or external data offsite in multiple cloud locations.</span></span>
    
- <span data-ttu-id="54996-164">회사 커뮤니케이션 게시</span><span class="sxs-lookup"><span data-stu-id="54996-164">Publish company communications</span></span>
    
    <span data-ttu-id="54996-165">내부 또는 외부 메시지에 대 한 발행물의 단일 지점을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="54996-165">Create a single point of publication for internal or external messages.</span></span>
    
- <span data-ttu-id="54996-166">수백만 개의 이벤트를 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="54996-166">Distribute millions of events</span></span>
    
    <span data-ttu-id="54996-167">웹사이트, 앱 및 장치에서 원격 분석 수집에 대 한 저장소를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="54996-167">Create storage for telemetry ingestion from websites, apps, and devices.</span></span>
    
- <span data-ttu-id="54996-168">비디오 관리 서비스</span><span class="sxs-lookup"><span data-stu-id="54996-168">Manage/serve videos</span></span>
    
    <span data-ttu-id="54996-169">저장 하 고 고객 또는 조직 사용자에 게 비디오 콘텐츠를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="54996-169">Store and serve video content to customers or organization users.</span></span>
    
## <a name="next-step"></a><span data-ttu-id="54996-170">다음 단계</span><span class="sxs-lookup"><span data-stu-id="54996-170">Next step</span></span>

<span data-ttu-id="54996-171">[이동-준비](move-in-ready.md) 클라우드 저장소 옵션을 검토 합니다.</span><span class="sxs-lookup"><span data-stu-id="54996-171">Review the [Move-in ready](move-in-ready.md) cloud storage options.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="54996-172">참고 항목</span><span class="sxs-lookup"><span data-stu-id="54996-172">See Also</span></span>

[<span data-ttu-id="54996-173">Microsoft Cloud Storage for Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="54996-173">Microsoft Cloud Storage for Enterprise Architects</span></span>](microsoft-cloud-storage-for-enterprise-architects.md)
  
[<span data-ttu-id="54996-174">Microsoft 클라우드 IT 아키텍처 리소스</span><span class="sxs-lookup"><span data-stu-id="54996-174">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="54996-175">Microsoft의 엔터프라이즈 클라우드 로드맵: IT 의사 결정권자를 위한 리소스</span><span class="sxs-lookup"><span data-stu-id="54996-175">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)


