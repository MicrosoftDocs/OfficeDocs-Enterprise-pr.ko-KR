---
title: "Microsoft Azure의 SharePoint Server 2013 재해 복구"
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Deployment
ms.assetid: e9d14cb2-ff28-4a18-a444-cebf891880ea
description: "요약: Azure를 사용 하 여 온-프레미스 SharePoint 팜에 대 한 재해 복구 환경을 만들 수 있습니다. 이 문서에서는 디자인 하 고이 솔루션을 구현 하는 방법에 설명 합니다."
ms.openlocfilehash: e949d2cc88e576993a357007c2a600b55c259009
ms.sourcegitcommit: b3d44b30b6e60df85ea9b404692db64ba54a16c7
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/29/2018
---
# <a name="sharepoint-server-2013-disaster-recovery-in-microsoft-azure"></a><span data-ttu-id="147ee-104">Microsoft Azure의 SharePoint Server 2013 재해 복구</span><span class="sxs-lookup"><span data-stu-id="147ee-104">SharePoint Server 2013 Disaster Recovery in Microsoft Azure</span></span>

 <span data-ttu-id="147ee-p102">**요약:** Azure를 사용 하 여 온-프레미스 SharePoint 팜에 대 한 재해 복구 환경을 만들 수 있습니다. 이 문서에서는 디자인 하 고이 솔루션을 구현 하는 방법에 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p102">**Summary:** Using Azure, you can create a disaster-recovery environment for your on-premises SharePoint farm. This article describes how to design and implement this solution.</span></span>
  
 <span data-ttu-id="147ee-p103">재난이 발생 한 SharePoint 온-프레미스 환경의 경우 시스템을 신속 하 게 다시 실행 하 여 가장 높은 우선순위가 됩니다. Microsoft Azure에서 이미 실행 되 고 백업 환경을 사용 하는 경우 SharePoint 사용 하 여 재해 복구는 빠르고 쉽게 수행할 수 있습니다. 이 비디오는 SharePoint 웜 장애 조치 환경의 주요 개념에 설명 하 고 전체 자세한 내용은이 문서에서 사용할 수 있는 기능을 보완 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p103">When disaster strikes your SharePoint on-premises environment, your top priority is to get the system running again quickly. Disaster recovery with SharePoint is quicker and easier when you have a backup environment already running in Microsoft Azure. This video explains the main concepts of a SharePoint warm failover environment and complements the full details available in this article.</span></span>
  
![동영상(재생 단추) 아이콘](images/mod_icon_video_M.png)
  
<span data-ttu-id="147ee-111">이 문서를 사용 하 여 다음과 같은 솔루션 모델: **Microsoft Azure의 SharePoint 재해 복구**합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-111">Use this article with the following solution model: **SharePoint Disaster Recovery in Microsoft Azure**.</span></span>
  
<span data-ttu-id="147ee-112">[</span><span class="sxs-lookup"><span data-stu-id="147ee-112"></span></span>![Azure에 대한 SharePoint 재해 복구 프로세스](images/SP_DR_Azure.png)
  
<span data-ttu-id="147ee-114">] (https://go.microsoft.com/fwlink/p/?LinkId=392555)</span><span class="sxs-lookup"><span data-stu-id="147ee-114">](https://go.microsoft.com/fwlink/p/?LinkId=392555)</span></span>
  
<span data-ttu-id="147ee-115">![PDF 파일](images/ITPro_Other_PDFicon.png)[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392555) |![Visio 파일](images/ITPro_Other_VisioIcon.jpg)[Visio](https://go.microsoft.com/fwlink/p/?LinkId=392554)</span><span class="sxs-lookup"><span data-stu-id="147ee-115">![PDF file](images/ITPro_Other_PDFicon.png)[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392555) |![Visio file](images/ITPro_Other_VisioIcon.jpg)[Visio](https://go.microsoft.com/fwlink/p/?LinkId=392554)</span></span>
  
<span data-ttu-id="147ee-116">이 문서의 내용</span><span class="sxs-lookup"><span data-stu-id="147ee-116">In this article:</span></span>
  
- [<span data-ttu-id="147ee-117">재해 복구를 위한 Azure 인프라 서비스를 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="147ee-117">Use Azure Infrastructure Services for disaster recovery</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#AZ)
    
- [<span data-ttu-id="147ee-118">솔루션 설명</span><span class="sxs-lookup"><span data-stu-id="147ee-118">Solution description</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#SOL)
    
- [<span data-ttu-id="147ee-119">상세 아키텍처</span><span class="sxs-lookup"><span data-stu-id="147ee-119">Detailed architecture</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#arch)
    
- [<span data-ttu-id="147ee-120">재해 복구 로드맵</span><span class="sxs-lookup"><span data-stu-id="147ee-120">Disaster recovery roadmap</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#RDmap)
    
- [<span data-ttu-id="147ee-121">1 단계: 디자인 재해 복구 환경</span><span class="sxs-lookup"><span data-stu-id="147ee-121">Phase 1: Design the disaster recovery environment</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#Phase1)
    
- [<span data-ttu-id="147ee-122">단계 2: Azure 가상 네트워크 및 VPN 연결 만들기</span><span class="sxs-lookup"><span data-stu-id="147ee-122">Phase 2: Create the Azure virtual network and VPN connection</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#Phase2)
    
- [<span data-ttu-id="147ee-123">Azure 가상 네트워크를 Active Directory 및 도메인 이름 서비스를 배포 하는 3 단계:</span><span class="sxs-lookup"><span data-stu-id="147ee-123">Phase 3: Deploy Active Directory and Domain Name Services to the Azure virtual network</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#Phase3)
    
- [<span data-ttu-id="147ee-124">4 단계: Azure의 SharePoint 복구 팜 배포</span><span class="sxs-lookup"><span data-stu-id="147ee-124">Phase 4: Deploy the SharePoint recovery farm in Azure</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#Phase4)
    
- [<span data-ttu-id="147ee-125">5 단계: 팜 간에 DFSR를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-125">Phase 5: Set up DFSR between the farms</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#Phase5)
    
- [<span data-ttu-id="147ee-126">단계 6: 로그 복구 팜으로 전달 설정</span><span class="sxs-lookup"><span data-stu-id="147ee-126">Phase 6: Set up log shipping to the recovery farm</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#Phase6)
    
- [<span data-ttu-id="147ee-127">단계 7: 장애 조치 및 복구의 유효성을 검사합니다</span><span class="sxs-lookup"><span data-stu-id="147ee-127">Phase 7: Validate failover and recovery</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#Phase7)
    
- [<span data-ttu-id="147ee-128">Microsoft 개념 증명 환경</span><span class="sxs-lookup"><span data-stu-id="147ee-128">Microsoft proof-of-concept environment</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#POC)
    
- [<span data-ttu-id="147ee-129">문제해결 팁</span><span class="sxs-lookup"><span data-stu-id="147ee-129">Troubleshooting tips</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#Troubleshooting)
    
## <a name="use-azure-infrastructure-services-for-disaster-recovery"></a><span data-ttu-id="147ee-130">재해 복구를 위한 Azure 인프라 서비스를 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="147ee-130">Use Azure Infrastructure Services for disaster recovery</span></span>
<span data-ttu-id="147ee-131"><a name="AZ"> </a></span><span class="sxs-lookup"><span data-stu-id="147ee-131"></span></span>

<span data-ttu-id="147ee-p104">대부분의 조직에서는 하지 않은 재해 복구 환경 sharepoint, 구축 및 온-프레미스를 유지 관리 비용이 매우 많이 값일 수 있습니다. Azure 인프라 서비스 주목할 옵션에 대 한 재해 복구 환경에 더욱 유연 하 고 온-프레미스 대안 보다 저렴을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p104">Many organizations do not have a disaster recovery environment for SharePoint, which can be expensive to build and maintain on-premises. Azure Infrastructure Services provides compelling options for disaster recovery environments that are more flexible and less expensive than the on-premises alternatives.</span></span>
  
<span data-ttu-id="147ee-134">Azure 인프라 서비스를 사용 하는 경우의 이점은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-134">The advantages for using Azure Infrastructure Services include:</span></span>
  
- <span data-ttu-id="147ee-p105">**더 적은 비용이 많이 드는 리소스** 유지 관리 하 고 온-프레미스 재해 복구 환경에 비해 더 적은 리소스에 대 한 지불 합니다. 자원 수 선택 어떤 재해 복구 환경에 따라 달라 집니다: 정지 대기, 웜 대기 또는 핫 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p105">**Fewer costly resources** Maintain and pay for fewer resources than on-premises disaster recovery environments. The number of resources depends on which disaster-recovery environment you choose: cold standby, warm standby, or hot standby.</span></span>
    
- <span data-ttu-id="147ee-p106">**더 나은 리소스 유연성** 재해 발생 시 쉽게 팜을 수평 확장할 복구 SharePoint 부하 요구 사항을 충족 합니다. 리소스에는 필요 없는 경우의 수직 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p106">**Better resource flexibility** In the event of a disaster, easily scale out your recovery SharePoint farm to meet load requirements. Scale in when you no longer need the resources.</span></span>
    
- <span data-ttu-id="147ee-139">**낮은 데이터 센터의 참여** Azure 인프라 서비스를 사용 하 여 서로 다른 영역에 보조 데이터 센터에 투자 하는 대신 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-139">**Lower datacenter commitment** Use Azure Infrastructure Services instead of investing in a secondary datacenter in a different region.</span></span>
    
<span data-ttu-id="147ee-p107">시작 재해 복구와 조직에 대 한 덜 복잡 한 옵션 및 고급 높은 복구 요구 사항이 조직에 대 한 옵션입니다. 정지, 웜, 및 핫 대기 환경에 대 한 정의 클라우드 플랫폼에서 호스팅되는 환경 때 약간 달라 집니다. 다음 표에서에 Azure의 SharePoint 복구 팜 만들기 (영문)에 대 한 이러한 환경에 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p107">There are less-complex options for organizations just getting started with disaster recovery and advanced options for organizations with high-resilience requirements. The definitions for cold, warm, and hot standby environments are a little different when the environment is hosted on a cloud platform. The following table describes these environments for building a SharePoint recovery farm in Azure.</span></span>
  
<span data-ttu-id="147ee-143">**표: 복구 환경**</span><span class="sxs-lookup"><span data-stu-id="147ee-143">**Table: Recovery environments**</span></span>

|<span data-ttu-id="147ee-144">**복구 환경 유형**</span><span class="sxs-lookup"><span data-stu-id="147ee-144">**Type of recovery environment**</span></span>|<span data-ttu-id="147ee-145">**설명**</span><span class="sxs-lookup"><span data-stu-id="147ee-145">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="147ee-146">핫</span><span class="sxs-lookup"><span data-stu-id="147ee-146">Hot</span></span>  <br/> |<span data-ttu-id="147ee-147">완벽 하 게 한 크기의 팜을 프로 비전 된, 대기 모드에서 실행 되 고, 업데이트 된 됩니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-147">A fully sized farm is provisioned, updated, and running on standby.</span></span>  <br/> |
|<span data-ttu-id="147ee-148">웜</span><span class="sxs-lookup"><span data-stu-id="147ee-148">Warm</span></span>  <br/> |<span data-ttu-id="147ee-149">팜을 작성 하 고 가상 컴퓨터가 실행 중 이며 업데이트 된 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-149">The farm is built and virtual machines are running and updated.</span></span>  <br/> <span data-ttu-id="147ee-150">콘텐츠 데이터베이스를 연결, 서비스 응용 프로그램을 구축 하 고 콘텐츠를 크롤링할 복구를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-150">Recovery includes attaching content databases, provisioning service applications, and crawling content.</span></span>  <br/> <span data-ttu-id="147ee-151">팜에는 프로덕션 팜에 보다 작은 버전일 수 및 사용자층에 전체 수평 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-151">The farm can be a smaller version of the production farm and then scaled out to serve the full user base.</span></span>  <br/> |
|<span data-ttu-id="147ee-152">콜드</span><span class="sxs-lookup"><span data-stu-id="147ee-152">Cold</span></span>  <br/> |<span data-ttu-id="147ee-153">팜의 완벽 하 게, 작성 되었지만 가상 컴퓨터를 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-153">The farm is fully built, but the virtual machines are stopped.</span></span>  <br/> <span data-ttu-id="147ee-154">유지 관리 하는 환경 때때로 가상 컴퓨터를 시작, 패치, 업데이트 및 환경 확인 (영문)를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-154">Maintaining the environment includes starting the virtual machines from time to time, patching, updating, and verifying the environment.</span></span>  <br/> <span data-ttu-id="147ee-155">재해 발생 시 전체 환경을 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-155">Start the full environment in the event of a disaster.</span></span>  <br/> |
   
<span data-ttu-id="147ee-p108">것은 조직의 복구 시간 목표 (RTOs) 및 복구 지점 목표 (RPOs)를 평가 하는 것이 중요 합니다. 이러한 요구 사항이 있는 환경 조직에 가장 적합 한 투자를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p108">It's important to evaluate your organization's Recovery Time Objectives (RTOs) and Recovery Point Objectives (RPOs). These requirements determine which environment is the most appropriate investment for your organization.</span></span>
  
<span data-ttu-id="147ee-p109">이 문서의 지침에서는 웜 대기 환경 구현 하는 방법에 설명 합니다. 또한 해당를 직접 적용할 수 콜드 대기 환경 환경의이 종류를 지원 하기 위해 추가 절차에 따라 필요는 없지만 합니다. 이 문서는 상시 대기 환경 구현 하는 방법을 설명 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p109">The guidance in this article describes how to implement a warm standby environment. You can also adapt it to a cold standby environment, although you need to follow additional procedures to support this kind of environment. This article does not describe how to implement a hot standby environment.</span></span>
  
<span data-ttu-id="147ee-161">재해 복구 솔루션에 대 한 자세한 내용은 [고가용성 및 재해 복구 개념에 SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkID=393114) 및[SharePoint 2013에 대 한 재해 복구 전략 선택](https://go.microsoft.com/fwlink/p/?linkid=203228)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="147ee-161">For more information about disaster recovery solutions, see [High availability and disaster recovery concepts in SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkID=393114) and[Choose a disaster recovery strategy for SharePoint 2013](https://go.microsoft.com/fwlink/p/?linkid=203228).</span></span>
  
## <a name="solution-description"></a><span data-ttu-id="147ee-162">솔루션 설명</span><span class="sxs-lookup"><span data-stu-id="147ee-162">Solution description</span></span>
<span data-ttu-id="147ee-163"><a name="SOL"> </a></span><span class="sxs-lookup"><span data-stu-id="147ee-163"></span></span>

<span data-ttu-id="147ee-164">웜 대기 재해 복구 솔루션에는 다음과 같은 환경을 해야합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-164">The warm standby disaster-recovery solution requires the following environment:</span></span>
  
- <span data-ttu-id="147ee-165">온-프레미스 SharePoint 프로덕션 팜</span><span class="sxs-lookup"><span data-stu-id="147ee-165">An on-premises SharePoint production farm</span></span>
    
- <span data-ttu-id="147ee-166">Azure의 복구 SharePoint 팜</span><span class="sxs-lookup"><span data-stu-id="147ee-166">A recovery SharePoint farm in Azure</span></span>
    
- <span data-ttu-id="147ee-167">두 환경 간에 사이트 마다 VPN 연결</span><span class="sxs-lookup"><span data-stu-id="147ee-167">A site-to-site VPN connection between the two environments</span></span>
    
<span data-ttu-id="147ee-168">다음 그림에서는 이러한 세 요소를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-168">The following figure illustrates these three elements.</span></span>
  
<span data-ttu-id="147ee-169">**그림: Azure의 웜 대기 솔루션 요소**</span><span class="sxs-lookup"><span data-stu-id="147ee-169">**Figure: Elements of a warm standby solution in Azure**</span></span>

![Azure의 SharePoint 웜 대기 솔루션 요소](images/AZarch_AZWarmStndby.gif)
  
<span data-ttu-id="147ee-171">SQL Server 로그 전달 분산 파일 시스템 복제 (DFSR)와 Azure에서 복구 팜에 데이터베이스 백업과 트랜잭션 로그를 복사를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-171">SQL Server log shipping with Distributed File System Replication (DFSR) is used to copy database backups and transaction logs to the recovery farm in Azure:</span></span> 
  
- <span data-ttu-id="147ee-p110">DFSR 복구 환경에 프로덕션 환경에서 로그를 전송합니다. WAN 시나리오에서는 DFSR Azure에서 직접 보조 서버로 로그를 전달 하는 보다 더 효율적입니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p110">DFSR transfers logs from the production environment to the recovery environment. In a WAN scenario, DFSR is more efficient than shipping the logs directly to the secondary server in Azure.</span></span>
    
- <span data-ttu-id="147ee-174">Azure에서 복구 환경에서 SQL Server에 로그 재생 됩니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-174">Logs are replayed to the SQL Server in the recovery environment in Azure.</span></span>
    
- <span data-ttu-id="147ee-175">복구 작업이 수행 될 때까지 로그 전달 SharePoint 콘텐츠 데이터베이스 복구 환경에서를 연결 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-175">You don't attach log-shipped SharePoint content databases in the recovery environment until a recovery exercise is performed.</span></span>
    
<span data-ttu-id="147ee-176">팜 복구 하려면 다음 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-176">Perform the following steps to recover the farm:</span></span>
  
1. <span data-ttu-id="147ee-177">로그 전달을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-177">Stop log shipping.</span></span>
    
2. <span data-ttu-id="147ee-178">기본 팜에 대 한 트래픽이 수락을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-178">Stop accepting traffic to the primary farm.</span></span>
    
3. <span data-ttu-id="147ee-179">마지막 트랜잭션 로그를 재생 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-179">Replay the final transaction logs.</span></span>
    
4. <span data-ttu-id="147ee-180">콘텐츠 데이터베이스를 팜에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-180">Attach the content databases to the farm.</span></span>
    
5. <span data-ttu-id="147ee-181">복제 된 서비스 데이터베이스에서 서비스 응용 프로그램을 복원 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-181">Restore service applications from the replicated services databases.</span></span>
    
6. <span data-ttu-id="147ee-182">복구 팜을 가리키도록 시스템 DNS (Domain Name) 레코드를 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-182">Update Domain Name System (DNS) records to point to the recovery farm.</span></span>
    
7. <span data-ttu-id="147ee-183">전체 크롤링을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-183">Start a full crawl.</span></span>
    
<span data-ttu-id="147ee-p111">다음이 단계를 정기적으로 예행 연습 하 고 라이브 복구에 원활 하 게 실행 되는지 확인 하는 데 도움이 되도록 문서화 하는 것이 좋습니다. 콘텐츠 데이터베이스를 연결 하 고 서비스 응용 프로그램을 복원 다소 시간이 걸릴 수 및 일반적으로 일부 수동 구성을 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p111">We recommend that you rehearse these steps regularly and document them to help ensure that your live recovery runs smoothly. Attaching content databases and restoring service applications can take some time and typically involves some manual configuration.</span></span>
  
<span data-ttu-id="147ee-186">복구를 수행한 후이 솔루션은 다음 표에 나열 된 항목을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-186">After a recovery is performed, this solution provides the items listed in the following table.</span></span>
  
<span data-ttu-id="147ee-187">**표: 솔루션 복구 목표**</span><span class="sxs-lookup"><span data-stu-id="147ee-187">**Table: Solution recovery objectives**</span></span>

|<span data-ttu-id="147ee-188">**항목**</span><span class="sxs-lookup"><span data-stu-id="147ee-188">**Item**</span></span>|<span data-ttu-id="147ee-189">**설명**</span><span class="sxs-lookup"><span data-stu-id="147ee-189">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="147ee-190">사이트 및 콘텐츠</span><span class="sxs-lookup"><span data-stu-id="147ee-190">Sites and content</span></span>  <br/> |<span data-ttu-id="147ee-191">사이트 및 콘텐츠 복구 환경에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-191">Sites and content are available in the recovery environment.</span></span>  <br/> |
|<span data-ttu-id="147ee-192">검색의 새 인스턴스를</span><span class="sxs-lookup"><span data-stu-id="147ee-192">A new instance of search</span></span>  <br/> |<span data-ttu-id="147ee-p112">이 웜 대기 솔루션에서 검색 검색 데이터베이스에서 복원 되지 않습니다. 복구 팜의 검색 구성 요소는 프로덕션 팜으로 최대한 비슷하게으로 구성 됩니다. 사이트 및 콘텐츠를 복원 후 검색 인덱스를 다시 작성 하려면 전체 크롤링 시작 됩니다. 사이트 및 콘텐츠를 사용할 수 있도록 설정 하기 위해 완료 하 고 탐색에 대 한 기다릴 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p112">In this warm standby solution, search is not restored from search databases. Search components in the recovery farm are configured as similarly as possible to the production farm. After the sites and content are restored, a full crawl is started to rebuild the search index. You do not need to wait for the crawl to complete to make the sites and content available.</span></span>  <br/> |
|<span data-ttu-id="147ee-197">서비스</span><span class="sxs-lookup"><span data-stu-id="147ee-197">Services</span></span>  <br/> | <span data-ttu-id="147ee-p113">서비스 데이터베이스에 데이터를 저장 하는 로그 전달 데이터베이스에서 복원 됩니다. 데이터베이스에 데이터를 저장 하지 않도록 하는 서비스가 시작 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p113">Services that store data in databases are restored from the log-shipped databases. Services that do not store data in databases are simply started.</span></span> <br/>  <span data-ttu-id="147ee-p114">일부 서비스 데이터베이스를 복원 해야 합니다. 다음 서비스 데이터베이스에서 복원할 필요 하지 않으며 장애 조치 후 단순히 시작 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p114">Not all services with databases need to be restored. The following services do not need to be restored from databases and can simply be started after failover:</span></span> <br/>  <span data-ttu-id="147ee-202">Usage and Health Data Collection</span><span class="sxs-lookup"><span data-stu-id="147ee-202">Usage and Health Data Collection</span></span> <br/>  <span data-ttu-id="147ee-203">State Service</span><span class="sxs-lookup"><span data-stu-id="147ee-203">State service</span></span> <br/>  <span data-ttu-id="147ee-204">Word 자동화</span><span class="sxs-lookup"><span data-stu-id="147ee-204">Word automation</span></span> <br/>  <span data-ttu-id="147ee-205">데이터베이스를 사용 하지 않는 다른 서비스</span><span class="sxs-lookup"><span data-stu-id="147ee-205">Any other service that doesn't use a database</span></span> <br/> |
   
<span data-ttu-id="147ee-p115">더 복잡 한 복구 목표를 해결 하는 Microsoft Consulting Services (MCS) 또는 파트너를 사용 하 여 작업할 수 있습니다. 이 다음 표에 요약 되어있습니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p115">You can work with Microsoft Consulting Services (MCS) or a partner to address more-complex recovery objectives. These are summarized in the following table.</span></span>
  
<span data-ttu-id="147ee-208">**표: 기타 항목 MCS 또는 파트너 하 여 해결할 수 있는**</span><span class="sxs-lookup"><span data-stu-id="147ee-208">**Table: Other items that can be addressed by MCS or a partner**</span></span>

|<span data-ttu-id="147ee-209">**항목**</span><span class="sxs-lookup"><span data-stu-id="147ee-209">**Item**</span></span>|<span data-ttu-id="147ee-210">**설명**</span><span class="sxs-lookup"><span data-stu-id="147ee-210">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="147ee-211">사용자 지정 팜 솔루션 동기화 (영문)</span><span class="sxs-lookup"><span data-stu-id="147ee-211">Synchronizing custom farm solutions</span></span>  <br/> |<span data-ttu-id="147ee-p116">원칙적으로 복구 팜 구성은 프로덕션 팜으로 동일 합니다. 사용자 지정 팜 솔루션은 복제 되므로 여부와 동기화 하는 두 환경 유지 하는 것에 대 한 전체 프로세스 인지 여부를 평가 하는 컨설턴트 또는 파트너와 작업할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p116">Ideally, the recovery farm configuration is identical to the production farm. You can work with a consultant or partner to evaluate whether custom farm solutions are replicated and whether the process is in place for keeping the two environments synchronized.</span></span>  <br/> |
|<span data-ttu-id="147ee-214">데이터 원본 온-프레미스에 대 한 연결</span><span class="sxs-lookup"><span data-stu-id="147ee-214">Connections to data sources on-premises</span></span>  <br/> |<span data-ttu-id="147ee-215">예: 백업 도메인 컨트롤러 (BDC) 연결 및 콘텐츠 원본을 검색 백엔드 데이터 시스템에 연결을 복제를 수행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-215">It might not be practical to replicate connections to back-end data systems, such as backup domain controller (BDC) connections and search content sources.</span></span>  <br/> |
|<span data-ttu-id="147ee-216">검색 복원 시나리오</span><span class="sxs-lookup"><span data-stu-id="147ee-216">Search restore scenarios</span></span>  <br/> |<span data-ttu-id="147ee-p117">엔터프라이즈 검색 배포 되는 매우 고유 하 고 복잡 한 경향이, 때문에 더 많은 투자를 필요 데이터베이스에서 검색을 복원 합니다. 컨설턴트 또는 파트너를 식별 하 고 조직 필요할 수 있는 검색 복원 시나리오를 구현를 사용 하 여 작업할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p117">Because enterprise search deployments tend to be fairly unique and complex, restoring search from databases requires a greater investment. You can work with a consultant or partner to identify and implement search restore scenarios that your organization might require.</span></span>  <br/> |
   
<span data-ttu-id="147ee-219">이 문서에서 제공 하는 지침에는 온-프레미스 팜에 이미 디자인 및 배포 된 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-219">The guidance provided in this article assumes that the on-premises farm is already designed and deployed.</span></span>
  
## <a name="detailed-architecture"></a><span data-ttu-id="147ee-220">자세한 아키텍처</span><span class="sxs-lookup"><span data-stu-id="147ee-220">Detailed architecture</span></span>
<span data-ttu-id="147ee-221"><a name="arch"> </a></span><span class="sxs-lookup"><span data-stu-id="147ee-221"></span></span>

<span data-ttu-id="147ee-222">원칙적으로 Azure에서 복구 팜 구성은 프로덕션 팜 온-프레미스, 다음을 비롯 한 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-222">Ideally, the recovery farm configuration in Azure is identical to the production farm on-premises, including the following:</span></span>
  
- <span data-ttu-id="147ee-223">서버 역할의 동일한 표현</span><span class="sxs-lookup"><span data-stu-id="147ee-223">The same representation of server roles</span></span>
    
- <span data-ttu-id="147ee-224">동일한 구성의 사용자 지정</span><span class="sxs-lookup"><span data-stu-id="147ee-224">The same configuration of customizations</span></span>
    
- <span data-ttu-id="147ee-225">검색 구성 요소는 동일한 구성</span><span class="sxs-lookup"><span data-stu-id="147ee-225">The same configuration of search components</span></span>
    
<span data-ttu-id="147ee-p118">Azure의 환경에는 프로덕션 팜 중 더 작은 버전 수 있습니다. 장애 조치 후 복구 팜 확장 하려는 경우에 각 종류의 서버 역할 처음 표현 되는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p118">The environment in Azure can be a smaller version of the production farm. If you plan to scale out the recovery farm after failover, it's important that each type of server role be initially represented.</span></span>
  
<span data-ttu-id="147ee-p119">일부 구성 장애 조치 환경에서 복제를 수행할 수 없습니다. 장애 조치 절차 및 장애 조치 팜 예상된 서비스 수준에서 제공 하을 보장 하는 환경 테스트 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p119">Some configurations might not be practical to replicate in the failover environment. Be sure to test the failover procedures and environment to help ensure that the failover farm provides the expected service level.</span></span>
  
<span data-ttu-id="147ee-p120">이 솔루션에는 SharePoint 팜에 대 한 특정 토폴로지를 규정 하지 않습니다. 이 솔루션의 포커스가 있는 장애 조치 팜에 대해 Azure를 사용 하 고 두 환경 간에 로그 전달 및 DFSR를 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p120">This solution doesn't prescribe a specific topology for a SharePoint farm. The focus of this solution is to use Azure for the failover farm and to implement log shipping and DFSR between the two environments.</span></span>
  
### <a name="warm-standby-environments"></a><span data-ttu-id="147ee-232">웜 대기 환경</span><span class="sxs-lookup"><span data-stu-id="147ee-232">Warm standby environments</span></span>

<span data-ttu-id="147ee-p121">웜 대기 환경에서 모든 가상 컴퓨터 Azure 환경에서 실행 됩니다. 환경이 장애 조치 연습 또는 이벤트를 수행할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p121">In a warm standby environment, all virtual machines in the Azure environment are running. The environment is ready for a failover exercise or event.</span></span>
  
<span data-ttu-id="147ee-235">다음 그림에서는 웜 대기 환경으로 구성 된 Azure 기반 SharePoint 팜에 온-프레미스 SharePoint 팜에서 재해 복구 솔루션을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-235">The following figure illustrates a disaster recovery solution from an on-premises SharePoint farm to an Azure-based SharePoint farm that is configured as a warm standby environment.</span></span>
  
<span data-ttu-id="147ee-236">**그림: 토폴로지 및 프로덕션 팜과 웜 대기 복구 팜의 핵심 요소**</span><span class="sxs-lookup"><span data-stu-id="147ee-236">**Figure: Topology and key elements of a production farm and a warm standby recovery farm**</span></span>

![SharePoint 프로덕션 팜 및 웜 대기 복구 팜의 토폴로지 및 핵심 요소를 보여줍니다.](images/AZarchWarmStndby.gif)
  
<span data-ttu-id="147ee-238">다음은 이 다이어그램에 대한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-238">In this diagram:</span></span>
  
- <span data-ttu-id="147ee-239">두 환경이 나란히 표시 된: 온-프레미스 SharePoint 팜과 Azure의 웜 대기 팜 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-239">Two environments are illustrated side by side: the on-premises SharePoint farm and the warm standby farm in Azure.</span></span>
    
- <span data-ttu-id="147ee-240">각 환경에는 파일 공유가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-240">Each environment includes a file share.</span></span>
    
- <span data-ttu-id="147ee-p122">각 팜 а를 포함합니다. 고가용성을 달성 하기 위해 각 계층에는 두 서버 또는 프런트엔드 서비스, 분산된 캐시, 백엔드 서비스 데이터베이스 등의 특정 역할에 대 한 동일 하 게 구성 된 가상 컴퓨터 포함 됩니다. 이 그림 특정 구성 요소를 호출 하는 것이 중요 하지 않습니다. 두 팜은 동일 하 게 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p122">Each farm includes four tiers. To achieve high availability, each tier includes two servers or virtual machines that are configured identically for a specific role, such as front-end services, distributed cache, back-end services, and databases. It isn't important in this illustration to call out specific components. The two farms are configured identically.</span></span>
    
- <span data-ttu-id="147ee-p123">4 번째 계층은 데이터베이스 계층입니다. 로그 전달 보조 데이터베이스 서버는 온-프레미스 환경에서 동일한 환경에서 파일 공유에 로그를 복사 하는 하는데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p123">The fourth tier is the database tier. Log shipping is used to copy logs from the secondary database server in the on-premises environment to the file share in the same environment.</span></span>
    
- <span data-ttu-id="147ee-247">DFSR Azure 환경에서 파일 공유에 온-프레미스 환경에서 파일 공유에서 파일을 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-247">DFSR copies files from the file share in the on-premises environment to the file share in the Azure environment.</span></span>
    
- <span data-ttu-id="147ee-248">로그 전달은 복구 환경에서 SQL Server AlwaysOn 가용성 그룹의 기본 복제본으로 Azure 환경에서 공유 되는 파일에서 로그를 재생 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-248">Log shipping replays the logs from the file share in the Azure environment to the primary replica in the SQL Server AlwaysOn availability group in the recovery environment.</span></span>
    
### <a name="cold-standby-environments"></a><span data-ttu-id="147ee-249">콜드 대기 환경</span><span class="sxs-lookup"><span data-stu-id="147ee-249">Cold standby environments</span></span>

<span data-ttu-id="147ee-p124">콜드 대기 환경에서 SharePoint 팜 가상 컴퓨터의 대부분 종료할 수 있습니다. (권장 가상 컴퓨터 마다 2 주 또는 한 달, 번 등을 시작 하는 경우에 따라 각 가상 컴퓨터의 도메인과 동기화 할 수 있도록 합니다.) Azure 복구 환경에서 다음 가상 컴퓨터 로그 전달 및 DFSR 연속 작업을 보장 하는 실행 중인 상태를 유지 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p124">In a cold standby environment, most of the SharePoint farm virtual machines can be shut down. (We recommend occasionally starting the virtual machines, such as every two weeks or once a month, so that each virtual machine can sync with the domain.) The following virtual machines in the Azure recovery environment must remain running to help ensure continuous operations of log shipping and DFSR:</span></span>
  
- <span data-ttu-id="147ee-252">파일 공유</span><span class="sxs-lookup"><span data-stu-id="147ee-252">The file share</span></span>
    
- <span data-ttu-id="147ee-253">기본 데이터베이스 서버입니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-253">The primary database server</span></span>
    
- <span data-ttu-id="147ee-254">Windows Server Active Directory 도메인 서비스 및 DNS를 실행 하는 하나 이상의 가상 컴퓨터</span><span class="sxs-lookup"><span data-stu-id="147ee-254">At least one virtual machine running Windows Server Active Directory Domain Services and DNS</span></span>
    
<span data-ttu-id="147ee-p125">다음 그림은 파일 공유 가상 컴퓨터 및 기본 SharePoint 데이터베이스 가상 컴퓨터 실행 중인 Azure 장애 조치 환경입니다. 다른 모든 SharePoint 가상 컴퓨터는 중지 됩니다. Windows Server Active Directory 및 DNS를 실행 하는 가상 컴퓨터 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p125">The following figure shows an Azure failover environment in which the file share virtual machine and the primary SharePoint database virtual machine are running. All other SharePoint virtual machines are stopped. The virtual machine that is running Windows Server Active Directory and DNS is not shown.</span></span>
  
<span data-ttu-id="147ee-258">**가상 컴퓨터를 실행 하는 포함 된 그림: 콜드 대기 복구 팜**</span><span class="sxs-lookup"><span data-stu-id="147ee-258">**Figure: Cold standby recovery farm with running virtual machines**</span></span>

![Azure의 SharePoint 콜드 대기 솔루션 요소](images/AZarch_AZColdStndby.png)
  
<span data-ttu-id="147ee-260">콜드 대기 환경에 장애 조치 후 모든 가상 컴퓨터를 시작 하 고 메서드를 호출 하는 데이터베이스 서버의 고가용성을 얻을 수를 구성 해야, SQL Server AlwaysOn 가용성 그룹 등입니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-260">After failover to a cold standby environment, all virtual machines are started, and the method to achieve high availability of the database servers must be configured, such as SQL Server AlwaysOn availability groups.</span></span>
  
<span data-ttu-id="147ee-261">여러 저장소 그룹 구현 된 경우 (데이터베이스 분산 된 하나 이상의 SQL Server 고가용성 집합)을 해당 저장소 그룹에 연결 된 로그를 수락 하려면 각 저장소 그룹에 대 한 기본 데이터베이스를 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-261">If multiple storage groups are implemented (databases are spread across more than one SQL Server high availability set), the primary database for each storage group must be running to accept the logs associated with its storage group.</span></span>
  
### <a name="skills-and-experience"></a><span data-ttu-id="147ee-262">기술 및 경험</span><span class="sxs-lookup"><span data-stu-id="147ee-262">Skills and experience</span></span>

<span data-ttu-id="147ee-p126">여러 기술은이 재해 복구 솔루션에 사용 됩니다. 이러한 기술을 예상 대로 작용 하는 확인 하는데에 온-프레미스 및 Azure 환경에서 각 구성 요소를 설치 하 고 올바르게 구성 수 해야 합니다. 하는 개인 또는 팀이이 솔루션을 설정 하는 사용자가 대 한 강력한 작업 지식이 및 실습 기술을 다음 문서에 설명 된 기술을 사용 하 여는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p126">Multiple technologies are used in this disaster recovery solution. To help ensure that these technologies interact as expected, each component in the on-premises and Azure environment must be installed and configured correctly. We recommend that the person or team who sets up this solution have a strong working knowledge of and hands-on skills with the technologies described in the following articles:</span></span>
  
- [<span data-ttu-id="147ee-266">분산된 파일 시스템 (DFS) 복제 서비스</span><span class="sxs-lookup"><span data-stu-id="147ee-266">Distributed File System (DFS) Replication Services</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=392698)
    
- [<span data-ttu-id="147ee-267">Windows Server 장애 조치 (WSFC) SQL server 클러스터링</span><span class="sxs-lookup"><span data-stu-id="147ee-267">Windows Server Failover Clustering (WSFC) with SQL Server</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=392701)
    
- [<span data-ttu-id="147ee-268">AlwaysOn 가용성 그룹 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="147ee-268">AlwaysOn Availability Groups (SQL Server)</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=392725)
    
- [<span data-ttu-id="147ee-269">백업 및 SQL Server 데이터베이스 복원</span><span class="sxs-lookup"><span data-stu-id="147ee-269">Back Up and Restore of SQL Server Databases</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=392728)
    
- [<span data-ttu-id="147ee-270">SharePoint Server 2013 설치 및 팜 배포</span><span class="sxs-lookup"><span data-stu-id="147ee-270">SharePoint Server 2013 installation and farm deployment</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=393119)
    
- [<span data-ttu-id="147ee-271">Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="147ee-271">Microsoft Azure</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=392729)
    
<span data-ttu-id="147ee-p127">마지막으로, 이러한 기술에 관련 된 작업을 자동화 하는 데 사용할 수 있는 기술 스크립팅 하는 것이 좋습니다. 이 솔루션에 설명 된 모든 작업을 완료 하는 사용할 수 있는 사용자 인터페이스를 사용 하는 것이 불가능 합니다. 그러나 수동 접근 시간 사용 (영문) 및 오류가 유발 될 수 있습니다와 일치 하지 않는 결과 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p127">Finally, we recommend scripting skills that you can use to automate tasks associated with these technologies. It's possible to use the available user interfaces to complete all the tasks described in this solution. However, a manual approach can be time consuming and error prone and delivers inconsistent results.</span></span>
  
<span data-ttu-id="147ee-p128">Windows PowerShell 외에도 SQL Server, SharePoint Server 및 Azure 용 Windows PowerShell 라이브러리도 있습니다. T SQL에도 도움이 구성 및 재해 복구 환경을 유지 관리 시간을 단축 하는 것을 잊지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="147ee-p128">In addition to Windows PowerShell, there are also Windows PowerShell libraries for SQL Server, SharePoint Server, and Azure. Don't forget T-SQL, which can also help reduce the time to configure and maintain your disaster-recovery environment.</span></span>
  
## <a name="disaster-recovery-roadmap"></a><span data-ttu-id="147ee-277">재해 복구 로드맵</span><span class="sxs-lookup"><span data-stu-id="147ee-277">Disaster recovery roadmap</span></span>
<span data-ttu-id="147ee-278"><a name="RDmap"> </a></span><span class="sxs-lookup"><span data-stu-id="147ee-278"></span></span>

![SharePoint 재해 복구 로드맵을 시각적으로 보여줍니다.](images/Azure_DRroadmap.png)
  
<span data-ttu-id="147ee-280">이 로드맵 프로덕션 환경에 배포 된 SharePoint Server 2013 팜 이미 있다고 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-280">This roadmap assumes that you already have a SharePoint Server 2013 farm deployed in production.</span></span>
  
<span data-ttu-id="147ee-281">**재해 복구를 위한 테이블: 로드맵**</span><span class="sxs-lookup"><span data-stu-id="147ee-281">**Table: Roadmap for disaster recovery**</span></span>

|<span data-ttu-id="147ee-282">**단계**</span><span class="sxs-lookup"><span data-stu-id="147ee-282">**Phase**</span></span>|<span data-ttu-id="147ee-283">**설명**</span><span class="sxs-lookup"><span data-stu-id="147ee-283">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="147ee-284">1 단계</span><span class="sxs-lookup"><span data-stu-id="147ee-284">Phase 1</span></span>  <br/> |<span data-ttu-id="147ee-285">재해 복구 환경을 디자인 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-285">Design the disaster recovery environment.</span></span>  <br/> |
|<span data-ttu-id="147ee-286">2 단계</span><span class="sxs-lookup"><span data-stu-id="147ee-286">Phase 2</span></span>  <br/> |<span data-ttu-id="147ee-287">Azure 가상 네트워크와 VPN 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-287">Create the Azure virtual network and VPN connection.</span></span>  <br/> |
|<span data-ttu-id="147ee-288">3 단계</span><span class="sxs-lookup"><span data-stu-id="147ee-288">Phase 3</span></span>  <br/> |<span data-ttu-id="147ee-289">Azure 가상 네트워크를 Windows Active Directory 및 도메인 이름 서비스를 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-289">Deploy Windows Active Directory and Domain Name Services to the Azure virtual network.</span></span>  <br/> |
|<span data-ttu-id="147ee-290">4 단계</span><span class="sxs-lookup"><span data-stu-id="147ee-290">Phase 4</span></span>  <br/> |<span data-ttu-id="147ee-291">Azure의 SharePoint 복구 팜에 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-291">Deploy the SharePoint recovery farm in Azure.</span></span>  <br/> |
|<span data-ttu-id="147ee-292">단계 5</span><span class="sxs-lookup"><span data-stu-id="147ee-292">Phase 5</span></span>  <br/> |<span data-ttu-id="147ee-293">팜 간에 DFSR를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-293">Set up DFSR between the farms.</span></span>  <br/> |
|<span data-ttu-id="147ee-294">단계 6</span><span class="sxs-lookup"><span data-stu-id="147ee-294">Phase 6</span></span>  <br/> |<span data-ttu-id="147ee-295">복구 팜으로 전달 하는 로그를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-295">Set up log shipping to the recovery farm.</span></span>  <br/> |
|<span data-ttu-id="147ee-296">단계 7</span><span class="sxs-lookup"><span data-stu-id="147ee-296">Phase 7</span></span>  <br/> | <span data-ttu-id="147ee-p129">장애 조치 및 복구 솔루션의 유효성을 검사 합니다. 다음 절차 및 기술 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p129">Validate failover and recovery solutions. This includes the following procedures and technologies:</span></span> <br/>  <span data-ttu-id="147ee-299">로그 전달을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-299">Stop log shipping.</span></span> <br/>  <span data-ttu-id="147ee-300">백업을 복원 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-300">Restore the backups.</span></span> <br/>  <span data-ttu-id="147ee-301">콘텐츠를 크롤링합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-301">Crawl content.</span></span> <br/>  <span data-ttu-id="147ee-302">서비스를 복구 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-302">Recover services.</span></span> <br/>  <span data-ttu-id="147ee-303">DNS 레코드를 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-303">Manage DNS records.</span></span> <br/> |
   
## <a name="phase-1-design-the-disaster-recovery-environment"></a><span data-ttu-id="147ee-304">1 단계: 디자인 재해 복구 환경</span><span class="sxs-lookup"><span data-stu-id="147ee-304">Phase 1: Design the disaster recovery environment</span></span>
<span data-ttu-id="147ee-305"><a name="Phase1"> </a></span><span class="sxs-lookup"><span data-stu-id="147ee-305"></span></span>

<span data-ttu-id="147ee-p130">SharePoint 복구 팜에 포함 하 여 재해 복구 환경을 디자인 하는 [SharePoint 2013에 대 한 Microsoft Azure 아키텍처](microsoft-azure-architectures-for-sharepoint-2013.md) 의 지침을 사용 합니다. 디자인 프로세스를 시작 하는 그래픽[Azure의 재해 복구 솔루션을 SharePoint](https://go.microsoft.com/fwlink/p/?LinkId=392554) Visio 파일에 사용할 수 있습니다. Azure 환경에 있는 모든 작업을 시작 하기 전에 전체 환경을 디자인 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p130">Use the guidance in [Microsoft Azure Architectures for SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md) to design the disaster-recovery environment, including the SharePoint recovery farm. You can use the graphics in the[SharePoint Disaster Recovery Solution in Azure](https://go.microsoft.com/fwlink/p/?LinkId=392554) Visio file to start the design process. We recommend that you design the entire environment before beginning any work in the Azure environment.</span></span>
  
<span data-ttu-id="147ee-309">가상 네트워크, VPN 연결, Active Directory 및 SharePoint 팜 디자인을 위한 [SharePoint 2013에 대 한 Microsoft Azure 아키텍처](microsoft-azure-architectures-for-sharepoint-2013.md) 에서 제공 하는 지침을 외에도 Azure 환경에는 파일 공유 역할을 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-309">In addition to the guidance provided in [Microsoft Azure Architectures for SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md) for designing the virtual network, VPN connection, Active Directory, and SharePoint farm, be sure to add a file share role to the Azure environment.</span></span>
  
<span data-ttu-id="147ee-p131">로그 전달을 재해 복구 솔루션에서을 지원 하려면 파일 공유 가상 컴퓨터는 데이터베이스 역할이 있는 서브넷에 추가 됩니다. 파일 공유를 사용 하는 SQL Server AlwaysOn 가용성 그룹에 대 한 노드 과반수의 세번째 노드로 사용 됩니다. SQL Server AlwaysOn 가용성 그룹을 사용 하는 표준 SharePoint 팜에 대 한 권장 되는 구성입니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p131">To support log shipping in a disaster-recovery solution, a file share virtual machine is added to the subnet where the database roles reside. The file share also serves as the third node of a Node Majority for the SQL Server AlwaysOn availability group. This is the recommended configuration for a standard SharePoint farm that uses SQL Server AlwaysOn availability groups.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="147ee-p132">SQL Server AlwaysOn 가용성 그룹에 참가할 수 있는 데이터베이스에 대 한 필수 구성 요소를 검토 하는 것이 반드시 합니다. 자세한 내용은 [필수 구성 요소, 제한 사항 및 AlwaysOn 가용성 그룹에 대 한 권장 사항을](https://go.microsoft.com/fwlink/p/?LinkId=510870)참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="147ee-p132">It is important to review the prerequisites for a database to participate in a SQL Server AlwaysOn availability group. For more information, see [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups](https://go.microsoft.com/fwlink/p/?LinkId=510870).</span></span> 
  
<span data-ttu-id="147ee-315">**그림: 재해 복구 솔루션에 사용 되는 파일 서버 배치**</span><span class="sxs-lookup"><span data-stu-id="147ee-315">**Figure: Placement of a file server used for a disaster recovery solution**</span></span>

![SharePoint 데이터베이스 서버 역할을 포함하는 동일한 클라우드 서비스에 추가된 파일 공유 VM을 보여줍니다.](images/AZenv_FSforDFSRandWSFC.png)
  
<span data-ttu-id="147ee-p133">이 다이어그램에서 파일 공유 가상 컴퓨터는 데이터베이스 서버 역할을 포함 하는 Azure의 동일한 서브넷에 추가 됩니다. SQL Server 역할 등의 다른 서버 역할을 사용 하 여 설정 하는 가용성 파일 공유 가상 컴퓨터를 추가 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="147ee-p133">In this diagram, a file share virtual machine is added to the same subnet in Azure that contains the database server roles. Do not add the file share virtual machine to an availability set with other server roles, such as the SQL Server roles.</span></span>
  
<span data-ttu-id="147ee-p134">로그의 고가용성에 대 한 고려 해야하는 경우에 [SQL Server 백업 및 복원 Azure Blob 저장소 서비스](https://go.microsoft.com/fwlink/p/?LinkId=393113)를 사용 하 여 다른 접근 방식을 취하고 하는 것이 좋습니다. 이것은 blob 저장소 URL에 직접 로그를 저장 하는 Azure의 새로운 기능입니다. 이 솔루션에서이 기능을 사용 하는 방법에 대 한 지침을 포함 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p134">If you are concerned about the high availability of the logs, consider taking a different approach by using [SQL Server backup and restore with Azure Blob Storage Service](https://go.microsoft.com/fwlink/p/?LinkId=393113). This is a new feature in Azure that saves logs directly to a blob storage URL. This solution does not include guidance about using this feature.</span></span>
  
<span data-ttu-id="147ee-p135">복구 팜을 디자인할 때 염두에 성공적인 재해 복구 환경 복구 하려는 프로덕션 팜을 정확 하 게 반영 하는 합니다. 복구 팜 크기 복구 팜의 디자인, 배포 및 테스트에서 가장 중요 한 사항은 않습니다. 비즈니스 요구 사항에 따라 조직에 조직에서 팜 수평 달라 집니다. 짧은 중단 또는 성능 및 용량 요구 사항에 맞출 필요 하면 팜의 확장할 수 있을 때까지 규모가 축소 된 팜을 사용 하 여 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p135">When you design the recovery farm, keep in mind that a successful disaster recovery environment accurately reflects the production farm that you want to recover. The size of the recovery farm is not the most important thing in the recovery farm's design, deployment, and testing. Farm scale varies from organization to organization based on business requirements. It might be possible to use a scaled-down farm for a short outage or until performance and capacity demands require you to scale the farm.</span></span>
  
<span data-ttu-id="147ee-p136">구성 복구 팜에 프로덕션 팜으로 최대한 동일 하 게 서비스 수준 계약 (SLA) 요구 사항을 충족 하 고 비즈니스를 지원 하기 위해 필요한 기능을 제공 합니다. 재해 복구 환경을 디자인할 때도 프로덕션 환경에 대 한 변경 관리 프로세스를 살펴봅니다. 프로덕션 환경으로 복구 환경 동일한 간격으로 업데이트 하 여 복구 환경에 변경 관리 프로세스를 확장 하는 것이 좋습니다. 변경 관리 프로세스의 일부로 팜 구성, 응용 프로그램 및 사용자의 상세 인벤토리를 유지 관리 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p136">Configure the recovery farm as identically as possible to the production farm so that it meets your service level agreement (SLA) requirements and provides the functionality that you need to support your business. When you design the disaster recovery environment, also look at your change management process for your production environment. We recommend that you extend the change management process to the recovery environment by updating the recovery environment at the same interval as the production environment. As part of the change management process, we recommend maintaining a detailed inventory of your farm configuration, applications, and users.</span></span> 
  
## <a name="phase-2-create-the-azure-virtual-network-and-vpn-connection"></a><span data-ttu-id="147ee-330">단계 2: Azure 가상 네트워크 및 VPN 연결 만들기</span><span class="sxs-lookup"><span data-stu-id="147ee-330">Phase 2: Create the Azure virtual network and VPN connection</span></span>
<span data-ttu-id="147ee-331"><a name="Phase2"> </a></span><span class="sxs-lookup"><span data-stu-id="147ee-331"></span></span>

<span data-ttu-id="147ee-p137">[Microsoft Azure 가상 네트워크에 연결 온-프레미스 네트워크](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md) 계획 하 고 Azure에 가상 네트워크를 배포 하는 방법 및 VPN 연결을 만드는 방법을 표시 합니다. 다음 절차를 완료 하려면 항목의 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p137">[Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md) shows you how to plan and deploy the virtual network in Azure and how to create the VPN connection. Follow the guidance in the topic to complete the following procedures:</span></span>
  
- <span data-ttu-id="147ee-334">가상 네트워크의 개인 IP 주소 공간을 계획 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-334">Plan the private IP address space of the Virtual Network.</span></span>
    
- <span data-ttu-id="147ee-335">가상 네트워크에 대 한 라우팅 인프라 변경 작업을 계획 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-335">Plan the routing infrastructure changes for the Virtual Network.</span></span>
    
- <span data-ttu-id="147ee-336">트래픽과 온-프레미스 VPN 장치에 대 한 방화벽 규칙을 계획 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-336">Plan firewall rules for traffic to and from the on-premises VPN device.</span></span>
    
- <span data-ttu-id="147ee-337">Azure에서 크로스-프레미스 가상 네트워크를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-337">Create the cross-premises virtual network in Azure.</span></span>
    
- <span data-ttu-id="147ee-338">온-프레미스 네트워크와 가상 네트워크 간의 라우팅을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-338">Configure routing between your on-premises network and the Virtual Network.</span></span>
    
## <a name="phase-3-deploy-active-directory-and-domain-name-services-to-the-azure-virtual-network"></a><span data-ttu-id="147ee-339">Azure 가상 네트워크를 Active Directory 및 도메인 이름 서비스를 배포 하는 3 단계:</span><span class="sxs-lookup"><span data-stu-id="147ee-339">Phase 3: Deploy Active Directory and Domain Name Services to the Azure virtual network</span></span>
<span data-ttu-id="147ee-340"><a name="Phase3"> </a></span><span class="sxs-lookup"><span data-stu-id="147ee-340"></span></span>

<span data-ttu-id="147ee-341">이 단계는 다음 그림에 나와있는 것 처럼 및 [SharePoint 2013에 대 한 Microsoft Azure 아키텍처](microsoft-azure-architectures-for-sharepoint-2013.md) 의 설명에 따라 Windows Server Active Directory와 DNS 하이브리드 시나리오에서 가상 네트워크에 배포를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-341">This phase includes deploying both Windows Server Active Directory and DNS to the Virtual Network in a hybrid scenario as described in [Microsoft Azure Architectures for SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md) and as illustrated in the following figure.</span></span>
  
<span data-ttu-id="147ee-342">**그림: 하이브리드 Active Directory 도메인 구성**</span><span class="sxs-lookup"><span data-stu-id="147ee-342">**Figure: Hybrid Active Directory domain configuration**</span></span>

![Azure Virtual Network와 SharePoint 팜 서브넷에 배포된 두 가상 컴퓨터: 복제 도메인 컨트롤러 및 DNS 서버](images/AZarch_HyADdomainConfig.png)
  
<span data-ttu-id="147ee-p138">그림에서는 두 가상 컴퓨터는 동일한 서브넷에 배포 됩니다. 이러한 가상 컴퓨터에는 각 호스팅 두 역할은: Active Directory 및 DNS 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p138">In the illustration, two virtual machines are deployed to the same subnet. These virtual machines are each hosting two roles: Active Directory and DNS.</span></span>
  
<span data-ttu-id="147ee-p139">Azure의 Active Directory를 배포 하기 전에 [Windows Server Active Directory를 배포에 Azure 가상 컴퓨터에 대 한 지침](https://go.microsoft.com/fwlink/p/?linkid=392681)을 제공 합니다. 이러한 지침 솔루션에 대 한 서로 다른 아키텍처 또는 다른 구성 설정의 필요 여부를 결정 하는데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p139">Before deploying Active Directory in Azure, read [Guidelines for Deploying Windows Server Active Directory on Azure Virtual Machines](https://go.microsoft.com/fwlink/p/?linkid=392681). These guidelines help you determine whether you need a different architecture or different configuration settings for your solution.</span></span>
  
<span data-ttu-id="147ee-348">Azure의 도메인 컨트롤러를 설정에 대 한 자세한 지침을 [Azure 가상 네트워크에서 복제 Active Directory 도메인 컨트롤러 설치](https://go.microsoft.com/fwlink/p/?LinkId=392687)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="147ee-348">For detailed guidance on setting up a domain controller in Azure, see [Install a Replica Active Directory Domain Controller in Azure Virtual Networks](https://go.microsoft.com/fwlink/p/?LinkId=392687).</span></span>
  
<span data-ttu-id="147ee-p140">이 단계 전에 가상 네트워크를 가상 컴퓨터를 배포 하지 않았으므로 있습니다. Active Directory 및 DNS를 호스팅하기 위한 가상 컴퓨터는 가능성이 솔루션에 필요한 가장 큰 가상 컴퓨터 없습니다. 이러한 가상 컴퓨터를 배포 하기 전에 먼저 가상 네트워크에서 사용 하 여 계획 하는 가장 큰 가상 컴퓨터를 만듭니다. 이렇게 하면 솔루션에 필요한 가장 큰 크기를 허용 하는 Azure의 태그에 도착 있는지 확인 합니다. 이 시간에이 가상 컴퓨터를 구성할 필요가 없습니다. 만들고 별도로 설정 하기만 합니다. 이렇게 하지 않으면 하는 경우 충돌할 수 있습니다 나중에 더 큰 가상 컴퓨터를 만들려는 경우 제한 하는 시점의 문제는이 문서 작성 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p140">Before this phase, you didn't deploy virtual machines to the Virtual Network. The virtual machines for hosting Active Directory and DNS are likely not the largest virtual machines you need for the solution. Before you deploy these virtual machines, first create the largest virtual machine that you plan to use in your Virtual Network. This helps ensure that your solution lands on a tag in Azure that allows the largest size you need. You do not need to configure this virtual machine at this time. Simply create it, and set it aside. If you do not do this, you might run into a limitation when you try to create larger virtual machines later, which was an issue at the time this article was written.</span></span> 
  
## <a name="phase-4-deploy-the-sharepoint-recovery-farm-in-azure"></a><span data-ttu-id="147ee-356">4 단계: Azure의 SharePoint 복구 팜 배포</span><span class="sxs-lookup"><span data-stu-id="147ee-356">Phase 4: Deploy the SharePoint recovery farm in Azure</span></span>
<span data-ttu-id="147ee-357"><a name="Phase4"> </a></span><span class="sxs-lookup"><span data-stu-id="147ee-357"></span></span>

<span data-ttu-id="147ee-p141">디자인 계획에 따라 가상 네트워크에서 SharePoint 팜에 배포 합니다. Azure의 SharePoint 역할을 배포 하기 전에 [Azure 인프라 서비스에 SharePoint 2013에 대 한 계획](https://go.microsoft.com/fwlink/p/?LinkId=400984) 을 검토할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p141">Deploy the SharePoint farm in your Virtual Network according to your design plans. It might be helpful to review [Planning for SharePoint 2013 on Azure Infrastructure Services](https://go.microsoft.com/fwlink/p/?LinkId=400984) before you deploy SharePoint roles in Azure.</span></span>
  
<span data-ttu-id="147ee-360">이 개념 검토 환경 구축 하 여 알게 된 다음의 사례를 고려 하십시오.</span><span class="sxs-lookup"><span data-stu-id="147ee-360">Consider the following practices that we learned by building our proof of concept environment:</span></span>
  
- <span data-ttu-id="147ee-361">Azure 포털 또는 PowerShell을 사용 하 여 가상 컴퓨터를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-361">Create virtual machines by using the Azure portal or PowerShell.</span></span>
    
- <span data-ttu-id="147ee-p142">Azure 및 Hyper-v에는 동적 메모리를 지원 하지 않습니다. 이 성능 및 용량 계획에 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p142">Azure and Hyper-V do not support dynamic memory. Be sure this is factored into your performance and capacity plans.</span></span>
    
- <span data-ttu-id="147ee-p143">자체 가상 컴퓨터 로그온에서가 아니라 Azure 인터페이스를 통해 가상 컴퓨터를 다시 시작 합니다. Azure 인터페이스를 사용 하 여 더 잘 작동 하 고는 예측 하기가 더 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p143">Restart virtual machines through the Azure interface, not from the virtual machine logon itself. Using the Azure interface works better and is more predictable.</span></span>
    
- <span data-ttu-id="147ee-p144">비용 절감을 위해 가상 컴퓨터를 종료 하려면 Azure 인터페이스를 사용 합니다. 로그온 하 고는 가상 컴퓨터를 종료 하는 경우 요금 계속 계산 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p144">If you want to shut down a virtual machine to save costs, use the Azure interface. If you shut down from the virtual machine logon, charges continue to accrue.</span></span>
    
- <span data-ttu-id="147ee-368">가상 컴퓨터에 대 한 명명 규칙을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-368">Use a naming convention for the virtual machines.</span></span>
    
- <span data-ttu-id="147ee-369">가상 컴퓨터는 배포 되는 데이터 센터 위치에 주의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-369">Pay attention to which datacenter location the virtual machines are being deployed.</span></span>
    
- <span data-ttu-id="147ee-370">Azure의 자동 확장 기능 SharePoint 역할에 대 한 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-370">The automatic scaling feature in Azure is not supported for SharePoint roles.</span></span>
    
- <span data-ttu-id="147ee-371">팜에서 같은 사이트 모음 복원 됩니다 하는 항목을 구성 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="147ee-371">Do not configure items in the farm that will be restored, such as site collections.</span></span> 
    
## <a name="phase-5-set-up-dfsr-between-the-farms"></a><span data-ttu-id="147ee-372">5 단계: 팜 간에 DFSR를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-372">Phase 5: Set up DFSR between the farms</span></span>
<span data-ttu-id="147ee-373"><a name="Phase5"> </a></span><span class="sxs-lookup"><span data-stu-id="147ee-373"></span></span>

<span data-ttu-id="147ee-p145">DFSR를 사용 하 여 파일 복제를 설정 하려면 DNS 관리 스냅인을 사용 합니다. 그러나 DFSR 설치 하기 전에 온-프레미스 파일 서버 및 Azure 파일 서버에 로그온 하 고 Windows에서 서비스를 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p145">To set up file replication by using DFSR, use the DNS Management snap-in. However, before the DFSR setup, log on to your on-premises file server and Azure file server and enable the service in Windows.</span></span>
  
<span data-ttu-id="147ee-376">서버 관리자 대시보드에서 다음 단계를 완료 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-376">From the Server Manager Dashboard, complete the following steps:</span></span>
  
- <span data-ttu-id="147ee-377">로컬 서버를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-377">Configure the local server.</span></span>
    
- <span data-ttu-id="147ee-378">**추가 역할 및 기능 마법사**시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-378">Start the **Add Roles and Features Wizard**.</span></span>
    
- <span data-ttu-id="147ee-379">**파일 및 저장소 서비스** 노드를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-379">Open the **File and Storage Services** node.</span></span>
    
- <span data-ttu-id="147ee-380">**DFS 네임 스페이스** 와 **DFS 복제**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-380">Select **DFS Namespaces** and **DFS replication**.</span></span>
    
- <span data-ttu-id="147ee-381">**다음** 마법사의 단계를 완료 하려면 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-381">Click **Next** to finish the wizard steps.</span></span>
    
<span data-ttu-id="147ee-382">다음 표에서 DFSR 참조 문서 및 블로그 게시물에 대 한 링크를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-382">The following table provides links to DFSR reference articles and blog posts.</span></span>
  
<span data-ttu-id="147ee-383">**표: DFSR에 대 한 문서를 참조**</span><span class="sxs-lookup"><span data-stu-id="147ee-383">**Table: Reference articles for DFSR**</span></span>

|<span data-ttu-id="147ee-384">**Title**</span><span class="sxs-lookup"><span data-stu-id="147ee-384">**Title**</span></span>|<span data-ttu-id="147ee-385">**설명**</span><span class="sxs-lookup"><span data-stu-id="147ee-385">**Description**</span></span>|
|:-----|:-----|
|[<span data-ttu-id="147ee-386">복제</span><span class="sxs-lookup"><span data-stu-id="147ee-386">Replication</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=392732) <br/> |<span data-ttu-id="147ee-387">복제에 대 한 링크와 함께 DFS 관리 TechNet 항목</span><span class="sxs-lookup"><span data-stu-id="147ee-387">DFS Management TechNet topic with links for replication</span></span>  <br/> |
|[<span data-ttu-id="147ee-388">DFS 복제: 상태 가이드</span><span class="sxs-lookup"><span data-stu-id="147ee-388">DFS Replication: Survival Guide</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=392737) <br/> |<span data-ttu-id="147ee-389">DFS 정보에 대 한 링크와 위 키</span><span class="sxs-lookup"><span data-stu-id="147ee-389">Wiki with links to DFS information</span></span>  <br/> |
|[<span data-ttu-id="147ee-390">DFS 복제: 질문과 대답 (영문)</span><span class="sxs-lookup"><span data-stu-id="147ee-390">DFS Replication: Frequently Asked Questions</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=392738) <br/> |<span data-ttu-id="147ee-391">DFS 복제 TechNet 항목</span><span class="sxs-lookup"><span data-stu-id="147ee-391">DFS Replication TechNet topic</span></span>  <br/> |
|[<span data-ttu-id="147ee-392">합니다. Barreto 블로그 (영문)</span><span class="sxs-lookup"><span data-stu-id="147ee-392">Jose Barreto's Blog</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=392739) <br/> |<span data-ttu-id="147ee-393">보안 주체 프로그램 관리자가 Microsoft에서 파일 서버 팀에서 작성 된 블로그 (영문)</span><span class="sxs-lookup"><span data-stu-id="147ee-393">Blog written by a Principal Program Manager on the File Server team at Microsoft</span></span>  <br/> |
|[<span data-ttu-id="147ee-394">Microsoft-파일 캐비닛 블로그 (영문)에서 저장소 팀</span><span class="sxs-lookup"><span data-stu-id="147ee-394">The Storage Team at Microsoft - File Cabinet Blog</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=392740) <br/> |<span data-ttu-id="147ee-395">파일 서비스 및 Windows Server의 저장소 기능에 대 한 블로그 (영문)</span><span class="sxs-lookup"><span data-stu-id="147ee-395">Blog about file services and storage features in Windows Server</span></span>  <br/> |
   
## <a name="phase-6-set-up-log-shipping-to-the-recovery-farm"></a><span data-ttu-id="147ee-396">단계 6: 로그 복구 팜으로 전달 설정</span><span class="sxs-lookup"><span data-stu-id="147ee-396">Phase 6: Set up log shipping to the recovery farm</span></span>
<span data-ttu-id="147ee-397"><a name="Phase6"> </a></span><span class="sxs-lookup"><span data-stu-id="147ee-397"></span></span>

<span data-ttu-id="147ee-p146">로그 전달이이 환경에서 재해 복구를 설정 하기 위한 중요 한 요소가 있습니다. 로그 전달 보조 데이터베이스 서버 인스턴스를 기본 데이터베이스 서버 인스턴스에서 데이터베이스에 대 한 트랜잭션 로그 파일을 보낼 자동으로 사용할 수 있습니다. 로그 전달을 설정 하려면 [구성에서에서 로그 전달을 SharePoint 2013을](http://technet.microsoft.com/library/482aeb81-e2aa-419f-a269-5b349a6c4721.aspx)참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="147ee-p146">Log shipping is the critical component for setting up disaster recovery in this environment. You can use log shipping to automatically send transaction log files for databases from a primary database server instance to a secondary database server instance. To set up log shipping, see [Configure log shipping in SharePoint 2013](http://technet.microsoft.com/library/482aeb81-e2aa-419f-a269-5b349a6c4721.aspx).</span></span> 
  
> [!IMPORTANT]
> <span data-ttu-id="147ee-p147">에서 로그 전달을 지원 SharePoint 서버는 특정 데이터베이스에 제한 됩니다. 자세한 내용은 [지원 되는 고가용성 및 재해 복구 옵션에 SharePoint 데이터베이스 (SharePoint 2013)을](https://go.microsoft.com/fwlink/p/?LinkId=393121)참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="147ee-p147">Log shipping support in SharePoint Server is limited to certain databases. For more information, see [Supported high availability and disaster recovery options for SharePoint databases (SharePoint 2013)](https://go.microsoft.com/fwlink/p/?LinkId=393121).</span></span> 
  
## <a name="phase-7-validate-failover-and-recovery"></a><span data-ttu-id="147ee-403">단계 7: 장애 조치 및 복구의 유효성을 검사합니다</span><span class="sxs-lookup"><span data-stu-id="147ee-403">Phase 7: Validate failover and recovery</span></span>
<span data-ttu-id="147ee-404"><a name="Phase7"> </a></span><span class="sxs-lookup"><span data-stu-id="147ee-404"></span></span>

<span data-ttu-id="147ee-p148">이 최종 단계의 목표 재해 복구 솔루션 계획 한 대로 작동 하는지 확인 하는 것입니다. 이 작업을 수행 하려면 프로덕션 팜 종료 되 고 대체할 수 있는으로 복구 팜 시작 되는 장애 조치 이벤트를 만듭니다. 수동으로 또는 스크립트를 사용 하 여 장애 조치 시나리오를 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p148">The goal of this final phase is to verify that the disaster recovery solution works as planned. To do this, create a failover event that shuts down the production farm and starts up the recovery farm as a replacement. You can start a failover scenario manually or by using scripts.</span></span>
  
<span data-ttu-id="147ee-p149">첫번째 단계 팜 서비스 또는 콘텐츠 받는 사용자 요청을 중지 하는 것입니다. DNS 항목을 사용 하지 않도록 설정 하 여 또는 프런트엔드 웹 서버를 종료 하 여 수행할 수 있습니다. 팜의 작동이 중지 "", 후 있습니다 수 장애 조치 복구 팜으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p149">The first step is to stop incoming user requests for farm services or content. You can do this by disabling DNS entries or by shutting down the front-end web servers. After the farm is "down," you can fail over to the recovery farm.</span></span>
  
### <a name="stop-log-shipping"></a><span data-ttu-id="147ee-411">로그 전달을 중지합니다</span><span class="sxs-lookup"><span data-stu-id="147ee-411">Stop log shipping</span></span>

<span data-ttu-id="147ee-p150">팜 복구 하기 전에 로그 전달을 중지 해야 합니다. 로그 전달 보조 서버 Azure에서 첫째, 중지 하 고 기본 서버 온-프레미스에 중지 합니다. 다음 스크립트를 사용 하 여 첫번째 보조 서버에서 한 주 서버에서 다음 로그 전달을 중지 합니다. 스크립트에서 데이터베이스 이름을 사용자 환경에 따라 달라질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p150">You must stop log shipping before farm recovery. Stop log shipping on the secondary server in Azure first, and then stop it on the primary server on-premises. Use the following script to stop log shipping on the secondary server first and then on the primary server. The database names in the script might be different, depending on your environment.</span></span>
  
```
-- This script removes log shipping from the server.
-- Commands must be executed on the secondary server first and then on the primary server.

SET NOCOUNT ON
DECLARE  @PriDB nvarchar(max)
,@SecDB nvarchar(250)
,@PriSrv nvarchar(250)
,@SecSrv nvarchar(250)

Set @PriDB= ''
SET @PriDB = UPPER(@PriDB)
SET @PriDB = REPLACE(@PriDB, ' ', '')
SET @PriDB = '''' + REPLACE(@PriDB, ',', ''', ''') + ''''

Set @SecDB = @PriDB

Exec ( 'Select  ''exec master..sp_delete_log_shipping_secondary_database '' + '''''''' + prm.primary_database +  ''''''''   
from msdb.dbo.log_shipping_monitor_primary prm INNER JOIN msdb.dbo.log_shipping_primary_secondaries sec  ON  prm.primary_database=sec.secondary_database
where prm.primary_database in ( ' + @PriDB + ' )')

Exec ( 'Select  ''exec master..sp_delete_log_shipping_primary_secondary '' + '''''''' + prm.Primary_Database + '''''', '''''' + sec.Secondary_Server + '''''', '''''' + sec.Secondary_database + ''''''''   
from msdb.dbo.log_shipping_monitor_primary prm INNER JOIN msdb.dbo.log_shipping_primary_secondaries sec  ON  prm.primary_database=sec.secondary_database
where prm.primary_database in ( ' + @PriDB + ' )')

Exec ( 'Select  ''exec master..sp_delete_log_shipping_primary_database '' + '''''''' + prm.primary_database +  ''''''''   
from msdb.dbo.log_shipping_monitor_primary prm INNER JOIN msdb.dbo.log_shipping_primary_secondaries sec  ON  prm.primary_database=sec.secondary_database
where prm.primary_database in ( ' + @PriDB + ' )')

Exec ( 'Select  ''exec master..sp_delete_log_shipping_secondary_primary '' + '''''''' + prm.primary_server + '''''', '''''' + prm.primary_database +  ''''''''   
from msdb.dbo.log_shipping_monitor_primary prm INNER JOIN msdb.dbo.log_shipping_primary_secondaries sec  ON  prm.primary_database=sec.secondary_database
where prm.primary_database in ( ' + @PriDB + ' )')

```

### <a name="restore-the-backups"></a><span data-ttu-id="147ee-416">백업 복원</span><span class="sxs-lookup"><span data-stu-id="147ee-416">Restore the backups</span></span>

<span data-ttu-id="147ee-p151">생성 된 순서에 백업은 복원 해야 합니다. 커밋되지 않은 트랜잭션이 롤백 하지 않고 다음 이전 백업을 복원 해야 특정 트랜잭션 로그 백업, 복원 하기 전에 (즉,을 사용 하 여 `WITH NORECOVERY`):</span><span class="sxs-lookup"><span data-stu-id="147ee-p151">Backups must be restored in the order in which they were created. Before you can restore a particular transaction log backup, you must first restore the following previous backups without rolling back uncommitted transactions (that is, by using  `WITH NORECOVERY`):</span></span>
  
- <span data-ttu-id="147ee-p152">전체 데이터베이스 백업 및 마지막 차등 백업-있을 경우, 특정 트랜잭션 로그 백업을 수행 하기 전에 만든 이러한 백업을 복원 합니다. 가장 최근의 전체 또는 차등 데이터베이스 백업을 만든, 전에 데이터베이스 전체 복구 모델 또는 대량 로그 된 복구 모델 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p152">The full database backup and the last differential backup - Restore these backups, if any exist, taken before the particular transaction log backup. Before the most recent full or differential database backup was created, the database was using the full recovery model or bulk-logged recovery model.</span></span>
    
- <span data-ttu-id="147ee-p153">모든 트랜잭션 로그 백업-전체 데이터베이스 백업 또는 (하나 복원) 하는 경우 차등 백업 후 및 전에 특정 트랜잭션 로그 백업 수행 모든 트랜잭션 로그 백업을 복원 합니다. 로그 백업은 생성 된 로그 체인에 있는 모든 간격 없이 시퀀스에 적용 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p153">All transaction log backups - Restore any transaction log backups taken after the full database backup or the differential backup (if you restore one) and before the particular transaction log backup. Log backups must be applied in the sequence in which they were created, without any gaps in the log chain.</span></span>
    
<span data-ttu-id="147ee-p154">사이트 렌더링 되도록 보조 서버에서 콘텐츠 데이터베이스를 복구 하려면 복구 하기 전에 모든 데이터베이스 연결을 제거 합니다. 데이터베이스를 복원 하려면 다음 SQL 문을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p154">To recover the content database on the secondary server so that the sites render, remove all database connections before recovery. To restore the database, run the following SQL statement.</span></span>
  
```
restore database WSS_Content with recovery

```

> [!IMPORTANT]
> <span data-ttu-id="147ee-p155">명시적으로 T-SQL을 사용 하는 경우 모호성을 제거 하려면 모든 복원 문에서 **WITH NORECOVERY** 또는 **WITH RECOVERY** 지정 — 스크립트를 작성 하는 경우이 매우 중요 합니다. 전체 및 차등 백업을 복원 되 면 SQL Server Management Studio에서 트랜잭션 로그를 복원할 수 있습니다. 또한 로그 전달을 이미 중지 되 면 때문에 콘텐츠 데이터베이스 이므로 대기 상태에서에 대 한 전체 액세스 상태를 변경 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p155">When you use T-SQL explicitly, specify either **WITH NORECOVERY** or **WITH RECOVERY** in every RESTORE statement to eliminate ambiguity—this is very important when writing scripts. After the full and differential backups are restored, the transaction logs can be restored in SQL Server Management Studio. Also, because log shipping is already stopped, the content database is in a standby state, so you must change the state to full access.</span></span>
  
<span data-ttu-id="147ee-p156">SQL Server Management Studio에서 **WSS_Content** 데이터베이스를 마우스 오른쪽 단추로, **작업**을 가리킨 > **복원**, 다음 **트랜잭션 로그** 를 클릭 하 고 (전체 백업, 복원 되지 않은 경우이 사용할 수 없는). 자세한 내용은[복원 트랜잭션 로그 백업 (SQL Server)을](https://go.microsoft.com/fwlink/p/?LinkId=392778)참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="147ee-p156">In SQL Server Management Studio, right-click the **WSS_Content** database, point to **Tasks** > **Restore**, and then click **Transaction Log** (if you have not restored the full backup, this is not available). For more information, see[Restore a Transaction Log Backup (SQL Server)](https://go.microsoft.com/fwlink/p/?LinkId=392778).</span></span>
  
### <a name="crawl-the-content-source"></a><span data-ttu-id="147ee-430">콘텐츠 원본 크롤링</span><span class="sxs-lookup"><span data-stu-id="147ee-430">Crawl the content source</span></span>

<span data-ttu-id="147ee-p157">검색 서비스를 복원 하려면 각 콘텐츠 원본의 전체 크롤링을 시작 해야 합니다. 참고 온-프레미스 팜에서 검색 추천와 같은 일부 분석 정보를 잃을 있습니다. 전체 크롤링 시작, **Restore-spenterprisesearchserviceapplication** Windows PowerShell cmdlet을 사용 하 고 로그를 전달 하 고 복제 된 검색 관리 데이터베이스를 지정 하기 전에 **Search_Service__DB_<GUID>**합니다. 이 cmdlet는 검색 구성, 스키마, 관리 속성, 규칙 및 원본에 게 제공 하 고 다른 구성 요소의 기본 집합을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p157">You must start a full crawl for each content source to restore the Search Service. Note that you lose some analytics information from the on-premises farm, such as search recommendations. Before you start the full crawls, use the Windows PowerShell cmdlet **Restore-SPEnterpriseSearchServiceApplication** and specify the log-shipped and replicated Search Administration database, **Search_Service__DB_<GUID>**. This cmdlet gives the search configuration, schema, managed properties, rules, and sources and creates a default set of the other components.</span></span>
  
<span data-ttu-id="147ee-435">전체 크롤링을 시작 하려면 다음 단계를 완료 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-435">To start a full crawl, complete the following steps:</span></span>
  
1. <span data-ttu-id="147ee-436">SharePoint 2013 중앙 관리에서 **응용 프로그램 관리**로 이동 > **서비스 응용 프로그램** > **서비스 응용 프로그램 관리**, 다음 크롤링할 지는 검색 서비스 응용 프로그램을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-436">In the SharePoint 2013 Central Administration, go to **Application Management** > **Service Applications** > **Manage service applications**, and then click the Search Service application that you want to crawl.</span></span>
    
2. <span data-ttu-id="147ee-437">**검색 관리** 페이지에서 **콘텐츠 원본**을 클릭, 화살표를 클릭 하 고 **전체 크롤링 시작**을 클릭 한 다음 사용할 콘텐츠 원본을 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-437">On the **Search Administration** page, click **Content Sources**, point to the content source that you want, click the arrow, and then click **Start Full Crawl**.</span></span>
    
### <a name="recover-farm-services"></a><span data-ttu-id="147ee-438">팜 서비스 복구</span><span class="sxs-lookup"><span data-stu-id="147ee-438">Recover farm services</span></span>
<span data-ttu-id="147ee-439"><a name="Reco"> </a></span><span class="sxs-lookup"><span data-stu-id="147ee-439"></span></span>

<span data-ttu-id="147ee-440">다음 표에서 로그 전달 데이터베이스, 서비스를 데이터베이스가 되어 있지만 로그 전달 데이터베이스 되지 않은 서비스와 복원 하는 것을 권장 하지 않은 서비스를 복구 하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-440">The following table shows how to recover services that have log-shipped databases, the services that have databases but are not recommended to restore with log shipping, and the services that do not have databases.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="147ee-441">Azure 환경에는 온-프레미스 SharePoint 데이터베이스를 복원 하 이미를 설치 하지 않은 Azure에서 수동으로 하는 모든 SharePoint 서비스 복구 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-441">Restoring an on-premises SharePoint database into the Azure environment will not recover any SharePoint services that you did not already install in Azure manually.</span></span> 
  
<span data-ttu-id="147ee-442">**표: 서비스 응용 프로그램 데이터베이스 참조 (영문)**</span><span class="sxs-lookup"><span data-stu-id="147ee-442">**Table: Service application database reference**</span></span>

|<span data-ttu-id="147ee-443">**로그 전달 데이터베이스에서 이러한 서비스를 복원 합니다.**</span><span class="sxs-lookup"><span data-stu-id="147ee-443">**Restore these services from log-shipped databases**</span></span>|<span data-ttu-id="147ee-444">**이러한 서비스 데이터베이스를 되었지만 해당 데이터베이스를 복원 하지 않고 이러한 서비스를 시작 하는 것이 좋습니다.**</span><span class="sxs-lookup"><span data-stu-id="147ee-444">**These services have databases, but we recommend that you start these services without restoring their databases**</span></span>|<span data-ttu-id="147ee-445">**이러한 서비스, 데이터베이스에서 데이터를 저장 하지 않습니다. 장애 조치 후 이러한 서비스를 시작 합니다.**</span><span class="sxs-lookup"><span data-stu-id="147ee-445">**These services do not store data in databases; start these services after failover**</span></span>|
|:-----|:-----|:-----|
| <span data-ttu-id="147ee-446">기계 번역 서비스</span><span class="sxs-lookup"><span data-stu-id="147ee-446">Machine Translation Service</span></span> <br/>  <span data-ttu-id="147ee-447">Managed Metadata Service</span><span class="sxs-lookup"><span data-stu-id="147ee-447">Managed Metadata Service</span></span> <br/>  <span data-ttu-id="147ee-448">Secure Store Service</span><span class="sxs-lookup"><span data-stu-id="147ee-448">Secure Store Service</span></span> <br/>  <span data-ttu-id="147ee-p158">사용자 프로필입니다. (프로필 및 공유 태그 데이터베이스 에서만 지원 됩니다. 동기화 데이터베이스 지원 되지 않습니다.)</span><span class="sxs-lookup"><span data-stu-id="147ee-p158">User Profile. (Only the Profile and Social Tagging databases are supported. The Synchronization database is not supported.)</span></span> <br/>  <span data-ttu-id="147ee-452">Microsoft SharePoint Foundation 가입 설정 서비스</span><span class="sxs-lookup"><span data-stu-id="147ee-452">Microsoft SharePoint Foundation Subscription Settings Service</span></span> <br/> | <span data-ttu-id="147ee-453">Usage and Health Data Collection</span><span class="sxs-lookup"><span data-stu-id="147ee-453">Usage and Health Data Collection</span></span> <br/>  <span data-ttu-id="147ee-454">State Service</span><span class="sxs-lookup"><span data-stu-id="147ee-454">State service</span></span> <br/>  <span data-ttu-id="147ee-455">Word 자동화</span><span class="sxs-lookup"><span data-stu-id="147ee-455">Word automation</span></span> <br/> | <span data-ttu-id="147ee-456">Excel Services</span><span class="sxs-lookup"><span data-stu-id="147ee-456">Excel Services</span></span> <br/>  <span data-ttu-id="147ee-457">PerformancePoint Services</span><span class="sxs-lookup"><span data-stu-id="147ee-457">PerformancePoint Services</span></span> <br/>  <span data-ttu-id="147ee-458">PowerPoint Conversion</span><span class="sxs-lookup"><span data-stu-id="147ee-458">PowerPoint Conversion</span></span> <br/>  <span data-ttu-id="147ee-459">Visio Graphics Service</span><span class="sxs-lookup"><span data-stu-id="147ee-459">Visio Graphics Service</span></span> <br/>  <span data-ttu-id="147ee-460">Work Management</span><span class="sxs-lookup"><span data-stu-id="147ee-460">Work Management</span></span> <br/> |
   
<span data-ttu-id="147ee-461">다음 예제에서는 데이터베이스에서 관리 되는 메타 데이터 서비스를 복원 하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-461">The following example shows how to restore the Managed Metadata service from a database.</span></span>
  
<span data-ttu-id="147ee-p159">이 기존 Managed_Metadata_DB 데이터베이스를 사용합니다. 이 데이터베이스에서는 로그 전달 되거나, 수 있지만를 설정 했으면 서비스 응용 프로그램에 연결할 수 있어야 하므로 활성 서비스 응용 프로그램을 보조 팜에서 않습니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p159">This uses the existing Managed_Metadata_DB database. This database is log shipped, but there is no active service application on the secondary farm, so it needs to be connected after the service application is in place.</span></span>
  
<span data-ttu-id="147ee-464">먼저를 사용 하 여 `New-SPMetadataServiceApplication`를 지정 하 고는 `DatabaseName` 복원된 된 데이터베이스의 이름으로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-464">First, use  `New-SPMetadataServiceApplication`, and specify the  `DatabaseName` switch with the name of the restored database.</span></span>
  
<span data-ttu-id="147ee-465">다음으로 구성 새 관리 되는 메타 데이터 서비스 응용 프로그램 보조 서버에서 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-465">Next, configure the new Managed Metadata Service Application on the secondary server, as follows:</span></span>
  
- <span data-ttu-id="147ee-466">이름: 관리 되는 메타 데이터 서비스</span><span class="sxs-lookup"><span data-stu-id="147ee-466">Name: Managed Metadata Service</span></span>
    
- <span data-ttu-id="147ee-467">데이터베이스 서버: 선적된 트랜잭션 로그에서 데이터베이스 이름</span><span class="sxs-lookup"><span data-stu-id="147ee-467">Database server: The database name from the shipped transaction log</span></span>
    
- <span data-ttu-id="147ee-468">데이터베이스 이름: Managed_Metadata_DB</span><span class="sxs-lookup"><span data-stu-id="147ee-468">Database name: Managed_Metadata_DB</span></span>
    
- <span data-ttu-id="147ee-469">응용 프로그램 풀: SharePoint 서비스 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="147ee-469">Application pool: SharePoint Service Applications</span></span> 
    
### <a name="manage-dns-records"></a><span data-ttu-id="147ee-470">DNS 레코드 관리</span><span class="sxs-lookup"><span data-stu-id="147ee-470">Manage DNS records</span></span>
<span data-ttu-id="147ee-471"><a name="DNS"> </a></span><span class="sxs-lookup"><span data-stu-id="147ee-471"></span></span>

<span data-ttu-id="147ee-472">SharePoint 팜의를 가리키도록 DNS 레코드를 수동으로 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-472">You must manually create DNS records to point to your SharePoint farm.</span></span>
  
<span data-ttu-id="147ee-p160">여러 프런트엔드 웹 서버가 있는 대부분의 경우에는 팜의 프런트엔드 웹 서버 요청을 배포 하는 Windows Server 2012 또는 하드웨어 부하 분산 장치에서 네트워크 부하 분산 기능을 활용 하 것이 좋습니다. 네트워크 부하 분산 프런트엔드 웹 서버 중 하나에 실패 하는 경우 다른 서버에 대 한 요청을 분산 하 여 위험을 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p160">In most cases where you have multiple front-end web servers, it makes sense to take advantage of the Network Load Balancing feature in Windows Server 2012 or a hardware load balancer to distribute requests among the web-front-end servers in your farm. Network load balancing can also help reduce risk by distributing requests to the other servers if one of your web-front-end servers fails.</span></span> 
  
<span data-ttu-id="147ee-p161">일반적으로 네트워크 부하 분산 설정 하는 경우 클러스터는 단일 IP 주소를 할당 됩니다. 그런 다음 만들면 DNS 호스트 레코드를 DNS 공급자에서 클러스터를 가리키는 네트워크에 대 한 합니다. (이 프로젝트에 대 한는 DNS 서버에에서 배치 Azure에서 온-프레미스 데이터 센터 오류가 발생 하는 경우 복구를 위한.) DNS 레코드를 DNS 관리자에서 Active Directory에서 예, 호출을 만들 수 예를 들어, `http://sharepoint.contoso.com`, 부하 분산 된 클러스터에 대 한 IP 주소를 가리키는 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p161">Typically, when you set up network load balancing, your cluster is assigned a single IP address. You then create a DNS host record in the DNS provider for your network that points to the cluster. (For this project, we put a DNS server in Azure for resiliency in case of an on-premises datacenter failure.) For instance, you can create a DNS record, in DNS Manager in Active Directory, for example, called  `http://sharepoint.contoso.com`, that points to the IP address for your load-balanced cluster.</span></span>
  
<span data-ttu-id="147ee-p162">SharePoint 팜에 대 한 외부 액세스를 위한 방화벽의 외부 IP 주소를 가리키는 인트라넷 (예: http://sharepoint.contoso.com)에서 클라이언트를 사용 하는 동일한 URL에는 외부 DNS 서버에 호스트 레코드를 만들 수 있습니다. (이 예제를 사용 하 여 최상의 결과은 외부 DNS 서버 라우팅 DNS 요청 하지 않고 내부 DNS 서버에서 SharePoint 팜 클러스터에 직접 contoso.com 및 경로 요청에 대 한 신뢰할 수 있도록 분할 DNS 설정 합니다.) 그런 다음 클라이언트에 대 한 필요 리소스를 찾을 수 있도록 외부 IP 주소 온-프레미스 클러스터의 내부 IP 주소를 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p162">For external access to your SharePoint farm, you can create a host record on an external DNS server with the same URL that clients use on your intranet (for example, http://sharepoint.contoso.com) that points to an external IP address in your firewall. (A best practice, using this example, is to set up split DNS so that the internal DNS server is authoritative for contoso.com and routes requests directly to the SharePoint farm cluster, rather than routing DNS requests to your external DNS server.) You can then map the external IP address to the internal IP address of your on-premises cluster so that clients find the resources they are looking for.</span></span>
  
<span data-ttu-id="147ee-480">여기에서 서로 다른 재해 복구 시나리오의 메시지를 몇 충돌할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-480">From here, you might run into a couple of different disaster-recovery scenarios:</span></span>
  
 <span data-ttu-id="147ee-p163">**예제 시나리오: 온-프레미스 SharePoint 팜의 하드웨어 오류로 인해 온-프레미스 SharePoint 팜의 사용할 수 없습니다.** 이 경우 Azure SharePoint 팜에 장애 조치에 대 한 단계를 완료 한 후에 네트워크에서 부하 분산 복구 SharePoint 팜의 프런트엔드 웹 서버는 온-프레미스 팜 것과 마찬가지로 동일한 방식으로 구성할 수 있습니다. 그런 다음 복구 팜의 클러스터 IP 주소를 가리키도록 내부 DNS 공급자에서 호스트 레코드를 리디렉션할 수 있습니다. 클라이언트에서 캐시 된 DNS 레코드 하기 전에 다소 시간이 걸릴 수 있는 메모를 새로 고칠 하 고 복구 팜에를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p163">**Example scenario: The on-premises SharePoint farm is unavailable because of hardware failure in the on-premises SharePoint farm.** In this case, after you have completed the steps for failover to the Azure SharePoint farm, you can configure network load balancing on the recovery SharePoint farm's web-front-end servers, the same way you did with the on-premises farm. You can then redirect the host record in your internal DNS provider to point to the recovery farm's cluster IP address. Note that it can take some time before cached DNS records on clients are refreshed and point to the recovery farm.</span></span>
  
 <span data-ttu-id="147ee-p164">**예제 시나리오: 온-프레미스 데이터 센터를 완전히 손실 됩니다.** 이 시나리오는 자연 재해, 화재 또는 배 등으로 인해 발생할 수 있습니다. 이 경우에 엔터프라이즈에 대 한 가능성이 해야 Azure 서브넷 자체 디렉터리 서비스와 DNS를 비롯 하 여 다른 지역에 호스팅되는 보조 데이터 센터입니다. 이전 재해 시나리오와 같이 Azure SharePoint 팜을 가리키도록 내부 및 외부 DNS 레코드를 리디렉션할 수 있습니다. 다시는 점에 주의 DNS 레코드가 전파 다소 시간이 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p164">**Example scenario: The on-premises datacenter is lost completely.** This scenario might occur due to a natural disaster, such as a fire or flood. In this case, for an enterprise, you would likely have a secondary datacenter hosted in another region as well as your Azure subnet that has its own directory services and DNS. As in the previous disaster scenario, you can redirect your internal and external DNS records to point to the Azure SharePoint farm. Again, take note that DNS-record propagation can take some time.</span></span>
  
<span data-ttu-id="147ee-p165">[호스트 이름이 지정 된 사이트 모음 아키텍처 및 배포 (SharePoint 2013)](https://go.microsoft.com/fwlink/p/?LinkId=393120)에서 권장 하는 대로 호스트 이름이 지정 된 사이트 모음을 사용 하는 경우에 SharePoint 팜의 고유와 동일한 웹 응용 프로그램에서 호스트 하는 여러 사이트 모음을 할 수 있습니다. DNS 이름 (예: http://sales.contoso.com 및 http://marketing.contoso.com). 이 경우 사용자 클러스터의 IP 주소를 가리키는 각 사이트 모음에 대 한 DNS 레코드를 만들 수 있습니다. 요청을 SharePoint 웹 프런트엔드 서버에 도달 하면 후 적절 한 사이트 모음에 각 요청을 라우팅 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p165">If you are using host-named site collections, as recommended in [Host-named site collection architecture and deployment (SharePoint 2013)](https://go.microsoft.com/fwlink/p/?LinkId=393120), you might have several site collections hosted by the same web application in your SharePoint farm, with unique DNS names (for example, http://sales.contoso.com and http://marketing.contoso.com). In this case, you can create DNS records for each site collection that point to your cluster IP address. After a request reaches your SharePoint web-front-end servers, they handle routing each request to the appropriate site collection.</span></span>
  
## <a name="microsoft-proof-of-concept-environment"></a><span data-ttu-id="147ee-493">Microsoft 개념 증명 환경</span><span class="sxs-lookup"><span data-stu-id="147ee-493">Microsoft proof-of-concept environment</span></span>
<span data-ttu-id="147ee-494"><a name="POC"> </a></span><span class="sxs-lookup"><span data-stu-id="147ee-494"></span></span>

<span data-ttu-id="147ee-p166">설계 하 고이 솔루션에 대 한 개념 증명 환경을 테스트 합니다. 이 테스트 환경에 대 한 디자인 목표를 배포 하 고 고객 환경에서 찾을 수도 하는 SharePoint 팜을 복구 하는 것 이었습니다. 여러 가정 걸었지만 팜의 모든 사용자 지정 내용을 없이 기본 기능을 제공 하는 데 필요한 있는지 알고 있습니다. 토폴로지 필드 및 제품 그룹에서 모범 사례 지침을 사용 하 여 고가용성을 위해 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p166">We designed and tested a proof-of-concept environment for this solution. The design goal for our test environment was to deploy and recover a SharePoint farm that we might find in a customer environment. We made several assumptions, but we knew that the farm needed to provide all of the out-of-the-box functionality without any customizations. The topology was designed for high availability by using best practice guidance from the field and product group.</span></span>
  
<span data-ttu-id="147ee-499">다음 표에서 작성 하 고 온-프레미스 테스트 환경에 대해 구성 하는 Hyper-v 가상 컴퓨터를 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-499">The following table describes the Hyper-V virtual machines that we created and configured for the on-premises test environment.</span></span>
  
<span data-ttu-id="147ee-500">**표: 온-프레미스에 대 한 가상 컴퓨터 테스트**</span><span class="sxs-lookup"><span data-stu-id="147ee-500">**Table: Virtual machines for on-premises test**</span></span>

|<span data-ttu-id="147ee-501">**서버 이름**</span><span class="sxs-lookup"><span data-stu-id="147ee-501">**Server name**</span></span>|<span data-ttu-id="147ee-502">**Role**</span><span class="sxs-lookup"><span data-stu-id="147ee-502">**Role**</span></span>|<span data-ttu-id="147ee-503">**구성**</span><span class="sxs-lookup"><span data-stu-id="147ee-503">**Configuration**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="147ee-504">DC1</span><span class="sxs-lookup"><span data-stu-id="147ee-504">DC1</span></span>  <br/> |<span data-ttu-id="147ee-505">Active Directory와 도메인 컨트롤러입니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-505">Domain controller with Active Directory.</span></span>  <br/> |<span data-ttu-id="147ee-506">2 개의 프로세서</span><span class="sxs-lookup"><span data-stu-id="147ee-506">Two processors</span></span>  <br/> <span data-ttu-id="147ee-507">Ram 4GB를 통해 512MB에서</span><span class="sxs-lookup"><span data-stu-id="147ee-507">From 512 MB through 4 GB of RAM</span></span>  <br/> <span data-ttu-id="147ee-508">1 x 127 GB 하드 디스크</span><span class="sxs-lookup"><span data-stu-id="147ee-508">1 x 127-GB hard disk</span></span>  <br/> |
|<span data-ttu-id="147ee-509">RRAS</span><span class="sxs-lookup"><span data-stu-id="147ee-509">RRAS</span></span>  <br/> |<span data-ttu-id="147ee-510">라우팅 및 원격 액세스 서비스 (RRAS) 역할을 사용 하 여 구성 하는 서버입니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-510">Server configured with the Routing and Remote Access Service (RRAS) role.</span></span>  <br/> |<span data-ttu-id="147ee-511">2 개의 프로세서</span><span class="sxs-lookup"><span data-stu-id="147ee-511">Two processors</span></span>  <br/> <span data-ttu-id="147ee-512">2-8 개의 2GB의 RAM</span><span class="sxs-lookup"><span data-stu-id="147ee-512">2-8 GB of RAM</span></span>  <br/> <span data-ttu-id="147ee-513">1 x 127 GB 하드 디스크</span><span class="sxs-lookup"><span data-stu-id="147ee-513">1 x 127-GB hard disk</span></span>  <br/> |
|<span data-ttu-id="147ee-514">F S 1</span><span class="sxs-lookup"><span data-stu-id="147ee-514">FS1</span></span>  <br/> |<span data-ttu-id="147ee-515">파일 서버 백업에 대 한 공유 및 DFSR의 시작점과 끝점입니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-515">File server with shares for backups and an end point for DFSR.</span></span>  <br/> |<span data-ttu-id="147ee-516">4 개의 프로세서</span><span class="sxs-lookup"><span data-stu-id="147ee-516">Four processors</span></span>  <br/> <span data-ttu-id="147ee-517">2-12GB ram</span><span class="sxs-lookup"><span data-stu-id="147ee-517">2-12 GB of RAM</span></span>  <br/> <span data-ttu-id="147ee-518">1 x 127 GB 하드 디스크</span><span class="sxs-lookup"><span data-stu-id="147ee-518">1 x 127-GB hard disk</span></span>  <br/> <span data-ttu-id="147ee-519">1 x 1 TB 하드 디스크 (SAN)</span><span class="sxs-lookup"><span data-stu-id="147ee-519">1 x 1-TB hard disk (SAN)</span></span>  <br/> <span data-ttu-id="147ee-520">1 x 750 GB 하드 디스크</span><span class="sxs-lookup"><span data-stu-id="147ee-520">1 x 750-GB hard disk</span></span>  <br/> |
|<span data-ttu-id="147ee-521">SP-WFE1, SP-WFE2</span><span class="sxs-lookup"><span data-stu-id="147ee-521">SP-WFE1, SP-WFE2</span></span>  <br/> |<span data-ttu-id="147ee-522">프런트엔드 웹 서버입니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-522">Front-end web servers.</span></span>  <br/> |<span data-ttu-id="147ee-523">4 개의 프로세서</span><span class="sxs-lookup"><span data-stu-id="147ee-523">Four processors</span></span>  <br/> <span data-ttu-id="147ee-524">16GB RAM</span><span class="sxs-lookup"><span data-stu-id="147ee-524">16 GB of RAM</span></span>  <br/> |
|<span data-ttu-id="147ee-525">S P-A P P 1을 S P-APP2 S P-APP3</span><span class="sxs-lookup"><span data-stu-id="147ee-525">SP-APP1, SP-APP2, SP-APP3</span></span>  <br/> |<span data-ttu-id="147ee-526">응용 프로그램 서버입니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-526">Application servers.</span></span>  <br/> |<span data-ttu-id="147ee-527">4 개의 프로세서</span><span class="sxs-lookup"><span data-stu-id="147ee-527">Four processors</span></span>  <br/> <span data-ttu-id="147ee-528">2-16 2GB의 RAM</span><span class="sxs-lookup"><span data-stu-id="147ee-528">2-16 GB of RAM</span></span>  <br/> |
|<span data-ttu-id="147ee-529">SP-SQL-HA1, SP-SQL-HA2</span><span class="sxs-lookup"><span data-stu-id="147ee-529">SP-SQL-HA1, SP-SQL-HA2</span></span>  <br/> |<span data-ttu-id="147ee-p167">높은 가용성을 제공 하도록 SQL Server 2012 AlwaysOn 가용성 그룹을 사용 하 여 구성 데이터베이스 서버입니다. 이 구성은 기본 및 보조 복제본으로 SP-sql-ha1 및 HA2-s P-SQL을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p167">Database servers, configured with SQL Server 2012 AlwaysOn availability groups to provide high availability. This configuration uses SP-SQL-HA1 and SP-SQL-HA2 as the primary and secondary replicas.</span></span>  <br/> |<span data-ttu-id="147ee-532">4 개의 프로세서</span><span class="sxs-lookup"><span data-stu-id="147ee-532">Four processors</span></span>  <br/> <span data-ttu-id="147ee-533">2-16 2GB의 RAM</span><span class="sxs-lookup"><span data-stu-id="147ee-533">2-16 GB of RAM</span></span>  <br/> |
   
<span data-ttu-id="147ee-534">다음 표에서 작성 하 고 프런트엔드 웹 및 온-프레미스 테스트 환경에 대 한 응용 프로그램 서버에 대해 구성 하는 Hyper-v 가상 컴퓨터에 대 한 드라이브 구성을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-534">The following table describes drive configurations for the Hyper-V virtual machines that we created and configured for the front-end web and application servers for the on-premises test environment.</span></span>
  
<span data-ttu-id="147ee-535">**표: 프런트엔드 최종 웹에 대 한 가상 컴퓨터 드라이브 요구 사항 및 온-프레미스에 대 한 응용 프로그램 서버 테스트**</span><span class="sxs-lookup"><span data-stu-id="147ee-535">**Table: Virtual machine drive requirements for the Front End Web and Application servers for the on-premises test**</span></span>

|<span data-ttu-id="147ee-536">**드라이브 문자**</span><span class="sxs-lookup"><span data-stu-id="147ee-536">**Drive letter**</span></span>|<span data-ttu-id="147ee-537">**크기**</span><span class="sxs-lookup"><span data-stu-id="147ee-537">**Size**</span></span>|<span data-ttu-id="147ee-538">**디렉터리 이름**</span><span class="sxs-lookup"><span data-stu-id="147ee-538">**Directory name**</span></span>|<span data-ttu-id="147ee-539">**Path**</span><span class="sxs-lookup"><span data-stu-id="147ee-539">**Path**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="147ee-540">C</span><span class="sxs-lookup"><span data-stu-id="147ee-540">C</span></span>  <br/> |<span data-ttu-id="147ee-541">80</span><span class="sxs-lookup"><span data-stu-id="147ee-541">80</span></span>  <br/> |<span data-ttu-id="147ee-542">시스템 드라이브</span><span class="sxs-lookup"><span data-stu-id="147ee-542">System drive</span></span>  <br/> |<span data-ttu-id="147ee-543"><DriveLetter>:\\프로그램 파일\\Microsoft SQL Server\\</span><span class="sxs-lookup"><span data-stu-id="147ee-543"><DriveLetter>:\\Program Files\\Microsoft SQL Server\\</span></span>  <br/> |
|<span data-ttu-id="147ee-544">E</span><span class="sxs-lookup"><span data-stu-id="147ee-544">E</span></span>  <br/> |<span data-ttu-id="147ee-545">80</span><span class="sxs-lookup"><span data-stu-id="147ee-545">80</span></span>  <br/> |<span data-ttu-id="147ee-546">로그 드라이브 (40GB)</span><span class="sxs-lookup"><span data-stu-id="147ee-546">Log drive (40 GB)</span></span>  <br/> |<span data-ttu-id="147ee-547"><DriveLetter>:\\프로그램 파일\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\데이터</span><span class="sxs-lookup"><span data-stu-id="147ee-547"><DriveLetter>:\\Program Files\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\DATA</span></span>  <br/> |
|<span data-ttu-id="147ee-548">F</span><span class="sxs-lookup"><span data-stu-id="147ee-548">F</span></span>  <br/> |<span data-ttu-id="147ee-549">80</span><span class="sxs-lookup"><span data-stu-id="147ee-549">80</span></span>  <br/> |<span data-ttu-id="147ee-550">페이지 (36GB)</span><span class="sxs-lookup"><span data-stu-id="147ee-550">Page (36 GB)</span></span>  <br/> |<span data-ttu-id="147ee-551"><DriveLetter>:\\프로그램 파일\\Microsoft SQL Server\\MSSQL\\데이터</span><span class="sxs-lookup"><span data-stu-id="147ee-551"><DriveLetter>:\\Program Files\\Microsoft SQL Server\\MSSQL\\DATA</span></span>  <br/> |
   
<span data-ttu-id="147ee-p168">다음 표에서 만들고 온-프레미스 데이터베이스 서버 처럼 작동 하도록 구성 된 Hyper-v 가상 컴퓨터에 대 한 드라이브 구성을 설명 합니다. **데이터베이스 엔진 구성** 페이지에서 설정 하 고 다음 표에 나와있는 설정을 확인 하 고 **데이터 디렉터리** 탭에 액세스 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p168">The following table describes drive configurations for the Hyper-V virtual machines created and configured to serve as the on-premises database servers. On the **Database Engine Configuration** page, access the **Data Directories** tab to set and confirm the settings shown in the following table.</span></span>
  
<span data-ttu-id="147ee-554">**표: 온-프레미스에 대 한 데이터베이스 서버에 대 한 가상 컴퓨터 드라이브 요구 사항 테스트**</span><span class="sxs-lookup"><span data-stu-id="147ee-554">**Table: Virtual machine drive requirements for the database server for the on-premises test**</span></span>

|<span data-ttu-id="147ee-555">**드라이브 문자**</span><span class="sxs-lookup"><span data-stu-id="147ee-555">**Drive letter**</span></span>|<span data-ttu-id="147ee-556">**크기**</span><span class="sxs-lookup"><span data-stu-id="147ee-556">**Size**</span></span>|<span data-ttu-id="147ee-557">**디렉터리 이름**</span><span class="sxs-lookup"><span data-stu-id="147ee-557">**Directory name**</span></span>|<span data-ttu-id="147ee-558">**Path**</span><span class="sxs-lookup"><span data-stu-id="147ee-558">**Path**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="147ee-559">C</span><span class="sxs-lookup"><span data-stu-id="147ee-559">C</span></span>  <br/> |<span data-ttu-id="147ee-560">80</span><span class="sxs-lookup"><span data-stu-id="147ee-560">80</span></span>  <br/> |<span data-ttu-id="147ee-561">데이터 루트 디렉터리</span><span class="sxs-lookup"><span data-stu-id="147ee-561">Data root directory</span></span>  <br/> |<span data-ttu-id="147ee-562"><DriveLetter>:\\프로그램 파일\\Microsoft SQL Server\\</span><span class="sxs-lookup"><span data-stu-id="147ee-562"><DriveLetter>:\\Program Files\\Microsoft SQL Server\\</span></span>  <br/> |
|<span data-ttu-id="147ee-563">E</span><span class="sxs-lookup"><span data-stu-id="147ee-563">E</span></span>  <br/> |<span data-ttu-id="147ee-564">500 개</span><span class="sxs-lookup"><span data-stu-id="147ee-564">500</span></span>  <br/> |<span data-ttu-id="147ee-565">사용자 데이터베이스 디렉터리</span><span class="sxs-lookup"><span data-stu-id="147ee-565">User database directory</span></span>  <br/> |<span data-ttu-id="147ee-566"><DriveLetter>:\\프로그램 파일\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\데이터</span><span class="sxs-lookup"><span data-stu-id="147ee-566"><DriveLetter>:\\Program Files\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\DATA</span></span>  <br/> |
|<span data-ttu-id="147ee-567">F</span><span class="sxs-lookup"><span data-stu-id="147ee-567">F</span></span>  <br/> |<span data-ttu-id="147ee-568">500 개</span><span class="sxs-lookup"><span data-stu-id="147ee-568">500</span></span>  <br/> |<span data-ttu-id="147ee-569">사용자 데이터베이스 로그 디렉터리</span><span class="sxs-lookup"><span data-stu-id="147ee-569">User database log directory</span></span>  <br/> |<span data-ttu-id="147ee-570"><DriveLetter>:\\프로그램 파일\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\데이터</span><span class="sxs-lookup"><span data-stu-id="147ee-570"><DriveLetter>:\\Program Files\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\DATA</span></span>  <br/> |
|<span data-ttu-id="147ee-571">G</span><span class="sxs-lookup"><span data-stu-id="147ee-571">G</span></span>  <br/> |<span data-ttu-id="147ee-572">500 개</span><span class="sxs-lookup"><span data-stu-id="147ee-572">500</span></span>  <br/> |<span data-ttu-id="147ee-573">Temp DB 디렉터리</span><span class="sxs-lookup"><span data-stu-id="147ee-573">Temp DB directory</span></span>  <br/> |<span data-ttu-id="147ee-574"><DriveLetter>:\\프로그램 파일\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\데이터</span><span class="sxs-lookup"><span data-stu-id="147ee-574"><DriveLetter>:\\Program Files\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\DATA</span></span>  <br/> |
|<span data-ttu-id="147ee-575">H</span><span class="sxs-lookup"><span data-stu-id="147ee-575">H</span></span>  <br/> |<span data-ttu-id="147ee-576">500 개</span><span class="sxs-lookup"><span data-stu-id="147ee-576">500</span></span>  <br/> |<span data-ttu-id="147ee-577">Temp DB 로그 디렉터리</span><span class="sxs-lookup"><span data-stu-id="147ee-577">Temp DB log directory</span></span>  <br/> |<span data-ttu-id="147ee-578"><DriveLetter>:\\프로그램 파일\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\데이터</span><span class="sxs-lookup"><span data-stu-id="147ee-578"><DriveLetter>:\\Program Files\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\DATA</span></span>  <br/> |
   
### <a name="setting-up-the-test-environment"></a><span data-ttu-id="147ee-579">테스트 환경 설정</span><span class="sxs-lookup"><span data-stu-id="147ee-579">Setting up the test environment</span></span>

<span data-ttu-id="147ee-p169">테스트 팀에서 다양 한 배포 단계 중 첫번째 온-프레미스 아키텍처에 대 한 다음 해당 Azure 환경에서 일반적으로 작동 합니다. 이 사내 프로덕션 팜에 이미 실행 중인 일반 실제 사례를 반영 합니다. 훨씬 더 중요 한 점은 현재 프로덕션 작업량, 용량 및 일반적인 성능을 알고 있어야입니다. 비즈니스 요구 사항을 충족할 수 있는 재해 복구 모델을 구축 하는 것 외에도 최소 수준의 서비스를 제공 하기 위해 복구 팜 서버를 크기를 결정 해야 합니다. 정지 또는 웜 대기 환경에서 복구 팜 일반적으로 보다 작으면 프로덕션 팜 합니다. 복구 후 팜의 안정적이 고, 프로덕션 환경에서 팜의 확장할 수 있습니다를 시작 및 종료 작업 요구 사항을 충족 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p169">During the different deployment phases, the test team typically worked on the on-premises architecture first and then on the corresponding Azure environment. This reflects the general real-world cases where in-house production farms are already running. What is even more important is that you should know the current production workload, capacity, and typical performance. In addition to building a disaster recovery model that can meet business requirements, you should size the recovery farm servers to deliver a minimum level of service. In a cold or warm standby environment, a recovery farm is typically smaller than a production farm. After the recovery farm is stable and in production, the farm can be scaled up and out to meet workload requirements.</span></span>
  
<span data-ttu-id="147ee-586">세 단계로 다음에 테스트 환경의 배포 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-586">We deployed our test environment in the following three phases:</span></span>
  
- <span data-ttu-id="147ee-587">하이브리드 인프라 설정</span><span class="sxs-lookup"><span data-stu-id="147ee-587">Set up the hybrid infrastructure</span></span>
    
- <span data-ttu-id="147ee-588">서버를 구축 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-588">Provision the servers</span></span>
    
- <span data-ttu-id="147ee-589">SharePoint 팜 배포</span><span class="sxs-lookup"><span data-stu-id="147ee-589">Deploy the SharePoint farms</span></span>
    
#### <a name="set-up-the-hybrid-infrastructure"></a><span data-ttu-id="147ee-590">하이브리드 인프라 설정</span><span class="sxs-lookup"><span data-stu-id="147ee-590">Set up the hybrid infrastructure</span></span>

<span data-ttu-id="147ee-p170">이 단계는 온-프레미스 팜에 대 한 및 Azure에서 복구 팜에 대 한 도메인 환경 설정을 관여합니다. Active Directory를 구성 하는와 관련 된 일반적인 작업을 외에도 테스트 팀 라우팅 솔루션 및 두 환경 간에 VPN 연결을 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p170">This phase involved setting up a domain environment for the on-premises farm and for the recovery farm in Azure. In addition to the normal tasks associated with configuring Active Directory, the test team implemented a routing solution and a VPN connection between the two environments.</span></span>
  
#### <a name="provision-the-servers"></a><span data-ttu-id="147ee-593">서버를 구축 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-593">Provision the servers</span></span>

<span data-ttu-id="147ee-p171">팜 서버 외에도 클래스는 도메인 컨트롤러에 대 한 프로 비전 서버에 필요한 된 및 RRAS 사이트 마다 VPN를 처리할 수 있는 서버를 구성 합니다. 두 파일 서버 DFSR 서비스에 대 한 프로 비전 된 및 테스터에 게 여러 클라이언트 컴퓨터를 공급 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p171">In addition to the farm servers, it was necessary to provision servers for the domain controllers and configure a server to handle RRAS as well as the site-to-site VPN. Two file servers were provisioned for the DFSR service, and several client computers were provisioned for testers.</span></span>
  
#### <a name="deploy-the-sharepoint-farms"></a><span data-ttu-id="147ee-596">SharePoint 팜 배포</span><span class="sxs-lookup"><span data-stu-id="147ee-596">Deploy the SharePoint farms</span></span>

<span data-ttu-id="147ee-p172">SharePoint 팜 필요한 경우 환경 안정화 하 고 문제를 해결을 단순화 하기 위해 두 단계로에 구축 되었습니다. 첫 단계 동안 각 팜 서버는 필요한 기능을 지원 하기 위해 토폴로지의 각 계층에 대 한 최소 수에 배포 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p172">The SharePoint farms were deployed in two stages in order to simplify environment stabilization and troubleshooting, if required. During the first stage, each farm was deployed on the minimum number of servers for each tier of the topology to support the required functionality.</span></span>
  
<span data-ttu-id="147ee-p173">SQL server가 SharePoint 2013 서버를 만들기 전에 설치 된 데이터베이스 서버를 만들었습니다. 새 배포 되었으므로 SharePoint를 배포 하기 전에 사용 가능 그룹을 작성 되었습니다. MCS 모범 사례 지침에 따라 세 그룹 작성 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p173">We created the database servers with SQL Server installed before creating the SharePoint 2013 servers. Because this was a new deployment, we created the availability groups before deploying SharePoint. We created three groups based on MCS best practice guidance.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="147ee-p174">SharePoint 설치 하기 전에 사용 가능 그룹을 만들 수 있도록 자리 표시자 데이터베이스를 만듭니다. 자세한 내용은 [구성 SQL Server 2012 AlwaysOn 가용성 그룹에 대 한 SharePoint 2013을](https://go.microsoft.com/fwlink/p/?LinkId=517626) 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="147ee-p174">Create placeholder databases so that you can create availability groups before the SharePoint installation. For more information, see [Configure SQL Server 2012 AlwaysOn Availability Groups for SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=517626)</span></span>
  
<span data-ttu-id="147ee-604">팜의 만든 하 고 다음과 같은 순서로 추가 서버에 참가 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-604">We created the farm and joined additional servers in the following order:</span></span>
  
- <span data-ttu-id="147ee-605">S P-sql-ha1 및 s P-SQL-HA2 프로 비전 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-605">Provision SP-SQL-HA1 and SP-SQL-HA2.</span></span>
    
- <span data-ttu-id="147ee-606">AlwaysOn을 구성 하 고 팜에 대 한 세 가용성 그룹을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-606">Configure AlwaysOn and create the three availability groups for the farm.</span></span> 
    
- <span data-ttu-id="147ee-607">프로 비전 s P-a p p 1에 중앙 관리를 호스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-607">Provision SP-APP1 to host Central Administration.</span></span>
    
- <span data-ttu-id="147ee-608">S P-w f e 1 및 SP WFE2 분산된 캐시 호스트를 프로 비전 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-608">Provision SP-WFE1 and SP-WFE2 to host the distributed cache.</span></span> 
    
<span data-ttu-id="147ee-p175">**Psconfig.exe** 명령줄에서 실행 하는 경우 _skipRegisterAsDistributedCachehost_ 매개 변수를 사용 했습니다. 자세한 내용은[피드 및 SharePoint Server 2013의 분산 캐시 서비스에 대 한 계획](https://go.microsoft.com/fwlink/p/?linkid=270985)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="147ee-p175">We used the  _skipRegisterAsDistributedCachehost_ parameter when we ran **psconfig.exe** at the command line. For more information, see[Plan for feeds and the Distributed Cache service in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?linkid=270985).</span></span> 
  
<span data-ttu-id="147ee-611">복구 환경에서 다음 단계를 반복 하는:</span><span class="sxs-lookup"><span data-stu-id="147ee-611">We repeated the following steps in the recovery environment:</span></span>
  
- <span data-ttu-id="147ee-612">AZ-sql-ha1 및 AZ-SQL-HA2 프로 비전 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-612">Provision AZ-SQL-HA1 and AZ-SQL-HA2.</span></span>
    
- <span data-ttu-id="147ee-613">AlwaysOn을 구성 하 고 팜에 대 한 세 가용성 그룹을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-613">Configure AlwaysOn and create the three availability groups for the farm.</span></span>
    
- <span data-ttu-id="147ee-614">프로 비전 AZ-a p p 1에 중앙 관리를 호스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-614">Provision AZ-APP1 to host Central Administration.</span></span>
    
- <span data-ttu-id="147ee-615">AZ-w f e 1 및 AZ WFE2 분산된 캐시 호스트를 프로 비전 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-615">Provision AZ-WFE1 and AZ-WFE2 to host the distributed cache.</span></span>
    
<span data-ttu-id="147ee-p176">분산된 캐시, 추가 된 테스트 사용자 및 테스트 콘텐츠를 구성 했습니다 후에 배포의 두 단계를 시작 했습니다. 이 필수 계층을 확장 하 고 팜 아키텍처에 설명 된 고가용성 토폴로지를 지원 하기 위해 팜 서버를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p176">After we configured the distributed cache and added test users and test content, we started stage two of the deployment. This required scaling out the tiers and configuring the farm servers to support the high-availability topology described in the farm architecture.</span></span>
  
<span data-ttu-id="147ee-618">다음 표에서 가상 컴퓨터, 서브넷 및 가용성 집합 사용해 복구 팜에 대 한 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-618">The following table describes the virtual machines, subnets, and availability sets we set up for our recovery farm.</span></span>
  
<span data-ttu-id="147ee-619">**표: 복구 팜 인프라**</span><span class="sxs-lookup"><span data-stu-id="147ee-619">**Table: Recovery farm infrastructure**</span></span>

|<span data-ttu-id="147ee-620">**서버 이름**</span><span class="sxs-lookup"><span data-stu-id="147ee-620">**Server name**</span></span>|<span data-ttu-id="147ee-621">**Role**</span><span class="sxs-lookup"><span data-stu-id="147ee-621">**Role**</span></span>|<span data-ttu-id="147ee-622">**구성**</span><span class="sxs-lookup"><span data-stu-id="147ee-622">**Configuration**</span></span>|<span data-ttu-id="147ee-623">**서브넷**</span><span class="sxs-lookup"><span data-stu-id="147ee-623">**Subnet**</span></span>|<span data-ttu-id="147ee-624">**가용성 집합**</span><span class="sxs-lookup"><span data-stu-id="147ee-624">**Availability set**</span></span>|
|:-----|:-----|:-----|:-----|:-----|
|<span data-ttu-id="147ee-625">spDRAD</span><span class="sxs-lookup"><span data-stu-id="147ee-625">spDRAD</span></span>  <br/> |<span data-ttu-id="147ee-626">Active Directory와 도메인 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="147ee-626">Domain controller with Active Directory</span></span>  <br/> |<span data-ttu-id="147ee-627">2 개의 프로세서</span><span class="sxs-lookup"><span data-stu-id="147ee-627">Two processors</span></span>  <br/> <span data-ttu-id="147ee-628">Ram 4GB를 통해 512MB에서</span><span class="sxs-lookup"><span data-stu-id="147ee-628">From 512 MB through 4 GB of RAM</span></span>  <br/> <span data-ttu-id="147ee-629">1 x 127 GB 하드 디스크</span><span class="sxs-lookup"><span data-stu-id="147ee-629">1 x 127-GB hard disk</span></span>  <br/> |<span data-ttu-id="147ee-630">sp ADservers</span><span class="sxs-lookup"><span data-stu-id="147ee-630">sp-ADservers</span></span>  <br/> ||
|<span data-ttu-id="147ee-631">AZ-S P-FS</span><span class="sxs-lookup"><span data-stu-id="147ee-631">AZ-SP-FS</span></span>  <br/> |<span data-ttu-id="147ee-632">파일 서버 백업 위한 공유 및 DFSR에 대 한 끝점</span><span class="sxs-lookup"><span data-stu-id="147ee-632">File server with shares for backups and an endpoint for DFSR</span></span>  <br/> | <span data-ttu-id="147ee-633">A5 구성:</span><span class="sxs-lookup"><span data-stu-id="147ee-633">A5 configuration:</span></span> <br/>  <span data-ttu-id="147ee-634">2 개의 프로세서</span><span class="sxs-lookup"><span data-stu-id="147ee-634">Two processors</span></span> <br/>  <span data-ttu-id="147ee-635">14 2GB의 RAM</span><span class="sxs-lookup"><span data-stu-id="147ee-635">14 GB of RAM</span></span> <br/>  <span data-ttu-id="147ee-636">1 x 127 GB 하드 디스크</span><span class="sxs-lookup"><span data-stu-id="147ee-636">1 x 127-GB hard disk</span></span> <br/>  <span data-ttu-id="147ee-637">1 x 135 GB 하드 디스크</span><span class="sxs-lookup"><span data-stu-id="147ee-637">1 x 135-GB hard disk</span></span> <br/>  <span data-ttu-id="147ee-638">1 x 127 GB 하드 디스크</span><span class="sxs-lookup"><span data-stu-id="147ee-638">1 x 127-GB hard disk</span></span> <br/>  <span data-ttu-id="147ee-639">1 x 150 GB 하드 디스크</span><span class="sxs-lookup"><span data-stu-id="147ee-639">1 x 150-GB hard disk</span></span> <br/> |<span data-ttu-id="147ee-640">sp databaseservers</span><span class="sxs-lookup"><span data-stu-id="147ee-640">sp-databaseservers</span></span>  <br/> |<span data-ttu-id="147ee-641">DATA_SET</span><span class="sxs-lookup"><span data-stu-id="147ee-641">DATA_SET</span></span>  <br/> |
|<span data-ttu-id="147ee-642">AZ-W F E 1, AZ-WFE2</span><span class="sxs-lookup"><span data-stu-id="147ee-642">AZ-WFE1, AZ -WFE2</span></span>  <br/> |<span data-ttu-id="147ee-643">프런트엔드 최종 웹 서버</span><span class="sxs-lookup"><span data-stu-id="147ee-643">Front End Web servers</span></span>  <br/> | <span data-ttu-id="147ee-644">A5 구성:</span><span class="sxs-lookup"><span data-stu-id="147ee-644">A5 configuration:</span></span> <br/>  <span data-ttu-id="147ee-645">2 개의 프로세서</span><span class="sxs-lookup"><span data-stu-id="147ee-645">Two processors</span></span> <br/>  <span data-ttu-id="147ee-646">14 2GB의 RAM</span><span class="sxs-lookup"><span data-stu-id="147ee-646">14 GB of RAM</span></span> <br/>  <span data-ttu-id="147ee-647">1 x 127 GB 하드 디스크</span><span class="sxs-lookup"><span data-stu-id="147ee-647">1 x 127-GB hard disk</span></span> <br/> |<span data-ttu-id="147ee-648">sp webservers</span><span class="sxs-lookup"><span data-stu-id="147ee-648">sp-webservers</span></span>  <br/> |<span data-ttu-id="147ee-649">WFE_SET</span><span class="sxs-lookup"><span data-stu-id="147ee-649">WFE_SET</span></span>  <br/> |
|<span data-ttu-id="147ee-650">AZ-A P P 1, AZ-APP2, AZ-APP3</span><span class="sxs-lookup"><span data-stu-id="147ee-650">AZ -APP1, AZ -APP2, AZ -APP3</span></span>  <br/> |<span data-ttu-id="147ee-651">응용 프로그램 서버</span><span class="sxs-lookup"><span data-stu-id="147ee-651">Application servers</span></span>  <br/> | <span data-ttu-id="147ee-652">A5 구성:</span><span class="sxs-lookup"><span data-stu-id="147ee-652">A5 configuration:</span></span> <br/>  <span data-ttu-id="147ee-653">2 개의 프로세서</span><span class="sxs-lookup"><span data-stu-id="147ee-653">Two processors</span></span> <br/>  <span data-ttu-id="147ee-654">14 2GB의 RAM</span><span class="sxs-lookup"><span data-stu-id="147ee-654">14 GB of RAM</span></span> <br/>  <span data-ttu-id="147ee-655">1 x 127 GB 하드 디스크</span><span class="sxs-lookup"><span data-stu-id="147ee-655">1 x 127-GB hard disk</span></span> <br/> |<span data-ttu-id="147ee-656">sp applicationservers</span><span class="sxs-lookup"><span data-stu-id="147ee-656">sp-applicationservers</span></span>  <br/> |<span data-ttu-id="147ee-657">APP_SET</span><span class="sxs-lookup"><span data-stu-id="147ee-657">APP_SET</span></span>  <br/> |
|<span data-ttu-id="147ee-658">AZ-SQL-HA1, AZ-SQL-HA2</span><span class="sxs-lookup"><span data-stu-id="147ee-658">AZ -SQL-HA1, AZ -SQL-HA2</span></span>  <br/> |<span data-ttu-id="147ee-659">데이터베이스 서버 및 AlwaysOn 가용성 그룹에 대 한 기본 및 보조 복제본</span><span class="sxs-lookup"><span data-stu-id="147ee-659">Database servers and primary and secondary replicas for AlwaysOn availability groups</span></span>  <br/> | <span data-ttu-id="147ee-660">A5 구성:</span><span class="sxs-lookup"><span data-stu-id="147ee-660">A5 configuration:</span></span> <br/>  <span data-ttu-id="147ee-661">2 개의 프로세서</span><span class="sxs-lookup"><span data-stu-id="147ee-661">Two processors</span></span> <br/>  <span data-ttu-id="147ee-662">14 2GB의 RAM</span><span class="sxs-lookup"><span data-stu-id="147ee-662">14 GB of RAM</span></span> <br/> |<span data-ttu-id="147ee-663">sp databaseservers</span><span class="sxs-lookup"><span data-stu-id="147ee-663">sp-databaseservers</span></span>  <br/> |<span data-ttu-id="147ee-664">DATA_SET</span><span class="sxs-lookup"><span data-stu-id="147ee-664">DATA_SET</span></span>  <br/> |
   
### <a name="operations"></a><span data-ttu-id="147ee-665">작업</span><span class="sxs-lookup"><span data-stu-id="147ee-665">Operations</span></span>

<span data-ttu-id="147ee-666">다음 작업을 시작은 테스트 팀 팜 환경을 안정 기능 테스트 완료 된 후 온-프레미스 복구 환경을 구성 하는 데 필요한 작업:</span><span class="sxs-lookup"><span data-stu-id="147ee-666">After the test team stabilized the farm environments and completed functional testing, they started the following operations tasks required to configure the on-premises recovery environment:</span></span>
  
- <span data-ttu-id="147ee-667">전체 및 차등 백업을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-667">Configure full and differential backups.</span></span>
    
- <span data-ttu-id="147ee-668">온-프레미스 환경 및 Azure 환경 간에 트랜잭션 로그를 전송 하는 파일 서버에서 DFSR를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-668">Configure DFSR on the file servers that transfer transaction logs between the on-premises environment and the Azure environment.</span></span>
    
- <span data-ttu-id="147ee-669">기본 데이터베이스 서버에서 로그 전달 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-669">Configure log shipping on the primary database server.</span></span>
    
- <span data-ttu-id="147ee-p177">안정을,의 유효성을 검사 하 고 필요에 따라 로그 전달의 문제를 해결 합니다. 이 식별 하 고 로그 전달 또는 DFSR 파일 동기화가 실패 하면 네트워크 대기 시간 등의 문제를 발생 시킬 수 있는 모든 동작을 문서화 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p177">Stabilize, validate, and troubleshoot log shipping, as required. This included identifying and documenting any behavior that might cause issues, such as network latency, which would cause log shipping or DFSR file synchronization failures.</span></span>
    
### <a name="databases"></a><span data-ttu-id="147ee-672">데이터베이스</span><span class="sxs-lookup"><span data-stu-id="147ee-672">Databases</span></span>

<span data-ttu-id="147ee-673">장애 조치 테스트 다음 데이터베이스를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-673">Our failover tests involved the following databases:</span></span> 
  
- <span data-ttu-id="147ee-674">WSS_Content</span><span class="sxs-lookup"><span data-stu-id="147ee-674">WSS_Content</span></span>
    
- <span data-ttu-id="147ee-675">ManagedMetadata</span><span class="sxs-lookup"><span data-stu-id="147ee-675">ManagedMetadata</span></span>
    
- <span data-ttu-id="147ee-676">프로필 DB</span><span class="sxs-lookup"><span data-stu-id="147ee-676">Profile DB</span></span>
    
- <span data-ttu-id="147ee-677">DB 동기화</span><span class="sxs-lookup"><span data-stu-id="147ee-677">Sync DB</span></span>
    
- <span data-ttu-id="147ee-678">공유 DB</span><span class="sxs-lookup"><span data-stu-id="147ee-678">Social DB</span></span>
    
- <span data-ttu-id="147ee-679">콘텐츠 형식 허브 (전용된 콘텐츠 형식 신디케이션 허브에 대 한 데이터베이스)</span><span class="sxs-lookup"><span data-stu-id="147ee-679">Content Type Hub (a database for a dedicated Content Type Syndication Hub)</span></span>
    
## <a name="troubleshooting-tips"></a><span data-ttu-id="147ee-680">문제 해결 팁</span><span class="sxs-lookup"><span data-stu-id="147ee-680">Troubleshooting tips</span></span>
<span data-ttu-id="147ee-681"><a name="Troubleshooting"> </a></span><span class="sxs-lookup"><span data-stu-id="147ee-681"></span></span>

<span data-ttu-id="147ee-682">섹션에서는 우리가 테스트 하 고 그 솔루션 하는 동안 발생 하는 문제에 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-682">The section explains the problems we encountered during our testing and their solutions.</span></span> 
  
### <a name="using-the-term-store-management-tool-caused-the-error-the-managed-metadata-store-or-connection-is-currently-not-available"></a><span data-ttu-id="147ee-683">용어 저장소 관리 도구를 사용 하 여 오류를 발생 시킨, "관리 되는 메타 데이터 저장소 또는 연결 현재 사용할 수 없습니다."</span><span class="sxs-lookup"><span data-stu-id="147ee-683">Using the Term Store Management Tool caused the error, "The Managed Metadata Store or Connection is currently not available."</span></span>

<span data-ttu-id="147ee-684">웹 응용 프로그램에서 사용 하는 응용 프로그램 풀 계정에 용어 저장소 사용 권한 읽기 액세스 권한이 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-684">Ensure that the application pool account used by the web application has the Read Access to Term Store permission.</span></span>
  
### <a name="custom-term-sets-are-not-available-in-the-site-collection"></a><span data-ttu-id="147ee-685">사용자 지정 용어 집합 사이트 모음에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-685">Custom term sets are not available in the site collection</span></span>

<span data-ttu-id="147ee-p178">콘텐츠 사이트 모음 및 콘텐츠 형식 허브 사이 누락 된 서비스 응용 프로그램 연결을 확인 합니다. 또한 아래는 **관리 되는 메타 데이터- <site collection name> 연결** 속성 화면에서이 옵션을 사용 하도록 설정: **이 서비스 응용 프로그램은 열 관련 용어 집합에 대 한 기본 저장소 위치.**</span><span class="sxs-lookup"><span data-stu-id="147ee-p178">Check for a missing service application association between your content site collection and your content type hub. In addition, under the **Managed Metadata - <site collection name> Connection** properties screen, make sure this option is enabled: **This service application is the default storage location for column specific term sets.**</span></span>
  
### <a name="the-get-adforest-windows-powershell-command-generates-the-error-the-term-get-adforest-is-not-recognized-as-the-name-of-a-cmdlet-function-script-file-or-operable-program"></a><span data-ttu-id="147ee-688">이 오류를 생성 하는 Get ADForest Windows PowerShell 명령, "' Get-ADForest' 용어 cmdlet, 함수, 스크립트 파일, 또는 실행할 수 있는 프로그램의 이름으로 인식 되지 않습니다."</span><span class="sxs-lookup"><span data-stu-id="147ee-688">The Get-ADForest Windows PowerShell command generates the error, "The term 'Get-ADForest' is not recognized as the name of a cmdlet, function, script file, or operable program."</span></span>

<span data-ttu-id="147ee-p179">사용자 프로필을 설정할 때 Active Directory 포리스트 이름을 해야 합니다. 추가 역할 및 기능 마법사는 Active Directory 모듈에 대 한 Windows PowerShell을 설정 했는지 확인 (아래는 **원격 서버 관리 도구 > 역할 관리 도구 > AD DS 및 AD LDS 도구** 섹션). 또한 **Get ADForest** 을 보장 하는 종속성을 로드 하는지 소프트웨어를 사용 하기 전에 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p179">When setting up user profiles, you need the Active Directory forest name. In the Add Roles and Features Wizard, ensure that you have enabled the Active Directory Module for Windows PowerShell (under the **Remote Server Administration Tools>Role Administration Tools>AD DS and AD LDS Tools** section). In addition, run the following commands before using **Get-ADForest** to help ensure that your software dependencies are loaded.</span></span>
  
```
Import-module servermanager
Import-module activedirectory

```

### <a name="availability-group-creation-fails-at-starting-the-alwaysonhealth-xevent-session-on-server-name"></a><span data-ttu-id="147ee-692">가용성 그룹 만들기 'AlwaysOn_health' XEvent 세션에서 시작 해 서에 실패 하면 '<server name>'</span><span class="sxs-lookup"><span data-stu-id="147ee-692">Availability group creation fails at Starting the 'AlwaysOn_health' XEvent session on '<server name>'</span></span>

<span data-ttu-id="147ee-693">장애 조치 클러스터의 두 노드 상태에 있는지 확인 "최대" 및 하지 "일시 중지 됨" 또는 "중지 됨"입니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-693">Ensure that both nodes of your failover cluster are in the Status "Up" and not "Paused" or "Stopped".</span></span> 
  
### <a name="sql-server-log-shipping-job-fails-with-access-denied-error-trying-to-connect-to-the-file-share"></a><span data-ttu-id="147ee-694">SQL Server 로그 전달 작업이 실패 하 고 액세스 거부 오류 파일 공유에 연결 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-694">SQL Server log shipping job fails with access denied error trying to connect to the file share</span></span>

<span data-ttu-id="147ee-695">SQL Server 에이전트의 기본 자격 증명 하는 대신 네트워크 자격 증명에서 실행 되 고 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-695">Ensure that your SQL Server Agent is running under network credentials, instead of the default credentials.</span></span>
  
### <a name="sql-server-log-shipping-job-indicates-success-but-no-files-are-copied"></a><span data-ttu-id="147ee-696">SQL Server 로그 전달 작업 성공, 나타내지만 없는 파일 복사</span><span class="sxs-lookup"><span data-stu-id="147ee-696">SQL Server log shipping job indicates success, but no files are copied</span></span>

<span data-ttu-id="147ee-p180">이러한 **보조 선호**은 가용성 그룹에 대 한 기본 백업 기본 설정 하기 때문에 발생 합니다. 기본 형식은 하는 대신 사용 가능 그룹에 대 한 보조 서버에서 로그 전달 작업을 실행 하는 확인 그렇지 않은 경우 작업이 자동으로 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p180">This happens because the default backup preference for an availability group is **Prefer Secondary**. Ensure that you run the log shipping job from the secondary server for the availability group instead of the primary; otherwise, the job will fail silently.</span></span> 
  
### <a name="managed-metadata-service-or-other-sharepoint-service-fails-to-start-automatically-after-installation"></a><span data-ttu-id="147ee-699">설치 후 자동으로 시작 하도록 실패 하는 관리 되는 메타 데이터 서비스 (또는 기타 SharePoint 서비스)</span><span class="sxs-lookup"><span data-stu-id="147ee-699">Managed Metadata service (or other SharePoint service) fails to start automatically after installation</span></span>

<span data-ttu-id="147ee-p181">서비스를 시작, 성능 및 SharePoint Server의 현재 부하에 따라 몇 분정도 걸릴 수 있습니다. 수동으로 서비스에 대 한 **시작** 을 클릭 하 고 필요에 따라 해당 상태를 모니터링할 서버 화면에서 서비스를 새로 고치는 동안 시작에 대 한 적절 한 시간을 제공 합니다. 서비스가 중지 된 설정을 변경 하거나 하는 경우에 SharePoint 진단 로깅을 사용 하도록 설정, 서비스를 다시 시작 하 고 오류에 대 한 로그를 확인 하려고 합니다. 자세한 내용은[SharePoint 2013에서 진단 로깅을 구성](https://go.microsoft.com/fwlink/p/?LinkId=510884) 을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="147ee-p181">Services might take several minutes to start, depending on the performance and current load of your SharePoint Server. Manually click **Start** for the service and provide adequate time for startup while occasionally refreshing the Services on Server screen to monitor its status. In case the service remains stopped, enable SharePoint diagnostic logging, attempt to start the service again, and then check the log for errors. For more information, see[Configure diagnostic logging in SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=510884)</span></span>
  
### <a name="after-changing-dns-to-the-azure-failover-environment-client-browsers-continue-to-use-the-old-ip-address-for-the-sharepoint-site"></a><span data-ttu-id="147ee-704">SharePoint 사이트에 대 한 이전 IP 주소를 사용 하 여 클라이언트 브라우저 계속 Azure 장애 조치 환경으로 DNS를 변경한 후</span><span class="sxs-lookup"><span data-stu-id="147ee-704">After changing DNS to the Azure failover environment, client browsers continue to use the old IP address for the SharePoint site</span></span>

<span data-ttu-id="147ee-p182">DNS 변경 내용을 표시 되지 않을 수도 모든 클라이언트에 게 즉시 합니다. 테스트 클라이언트에서 관리자 권한 명령 프롬프트에서 다음 명령을 수행 하 고 사이트에 액세스 하 고 다시 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="147ee-p182">Your DNS change might not be visible to all clients immediately. On a test client, perform the following command from an elevated command prompt and attempt to access the site again.</span></span>
  
```
Ipconfig /flushdns
```

## <a name="additional-resources"></a><span data-ttu-id="147ee-707">추가 리소스</span><span class="sxs-lookup"><span data-stu-id="147ee-707">Additional resources</span></span>
<span data-ttu-id="147ee-708"><a name="Troubleshooting"> </a></span><span class="sxs-lookup"><span data-stu-id="147ee-708"></span></span>

[<span data-ttu-id="147ee-709">(SharePoint 2013) SharePoint 데이터베이스에 대 한 지원 되는 고가용성 및 재해 복구 옵션</span><span class="sxs-lookup"><span data-stu-id="147ee-709">Supported high availability and disaster recovery options for SharePoint databases (SharePoint 2013)</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=393121)
  
[<span data-ttu-id="147ee-710">SharePoint 2013에 대 한 SQL Server 2012 AlwaysOn 가용성 그룹 구성</span><span class="sxs-lookup"><span data-stu-id="147ee-710">Configure SQL Server 2012 AlwaysOn Availability Groups for SharePoint 2013</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=393122)
  
## <a name="see-also"></a><span data-ttu-id="147ee-711">참고 항목</span><span class="sxs-lookup"><span data-stu-id="147ee-711">See Also</span></span>

<span data-ttu-id="147ee-712"><a name="Troubleshooting"> </a></span><span class="sxs-lookup"><span data-stu-id="147ee-712"></span></span>

[<span data-ttu-id="147ee-713">클라우드 채택 및 하이브리드 솔루션</span><span class="sxs-lookup"><span data-stu-id="147ee-713">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)



