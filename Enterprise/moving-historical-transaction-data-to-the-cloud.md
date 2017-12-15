---
title: "기록 트랜잭션 데이터를 클라우드로 이동"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 3e9c405a-415b-4584-aa7e-f2489299c457
description: "요약: Contoso 구현 하는 방법 SQL Server 데이터베이스의 온-프레미스 데이터 저장소 요구 사항 및 비용을 실행 하는 매일 감소를 확대 합니다."
ms.openlocfilehash: f1a44a14da49c394974755f7c557013717c4ccef
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2017
---
# <a name="moving-historical-transaction-data-to-the-cloud"></a><span data-ttu-id="ca633-103">기록 트랜잭션 데이터를 클라우드로 이동</span><span class="sxs-lookup"><span data-stu-id="ca633-103">Moving historical transaction data to the cloud</span></span>

 <span data-ttu-id="ca633-104">**요약:** Contoso는 SQL Server 늘이기 데이터베이스의 온-프레미스 데이터 저장소 요구 사항 및 비용을 실행 하는 매일 감소를 구현 하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="ca633-104">**Summary:** How Contoso implemented SQL Server stretch database to reduce its on-premises data storage needs and daily running costs.</span></span>
  
<span data-ttu-id="ca633-p101">Contoso의 엔터프라이즈 저장소 시스템 많은 양의 마케팅 연구 (영문)에 대 한 규정 요구 사항을 준수에 대 한 트랜잭션 기록 데이터 및 지출 추세의 BI 분석을 저장합니다. 또한 Contoso는 자기 테이프, 시간이 너무 많이 프로세스에서에서 보관 된 데이터를 복원 해야 합니다. Contoso의 엔터프라이즈 저장소 시스템의 하드웨어 수명 주기의 끝이 거의 하 고 비용이 비쌀 수 대체 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ca633-p101">Contoso's enterprise storage system stores a large amount of historical transaction data for adherence with regulatory requirements and for marketing research and BI analysis of spending trends. Contoso also needs to restore archived data from magnetic tape, a time-intensive process. The hardware in Contoso's enterprise storage system was nearing its end of life and replacing it would be very expensive.</span></span> 
  
<span data-ttu-id="ca633-p102">아래쪽의 온-프레미스 데이터 센터를 확장 하는 비즈니스 요구의 일부로, Contoso는 전체 확대/축소 데이터베이스 하이브리드 기능 및 Azure와 원활 하 게의 통합으로 인해 SQL Server 2016로 업그레이드 하도록 선택 했습니다. 로컬 디스크 공간을 확보 하 고 유지 관리를 줄이는 늘이기 데이터베이스에서 클라우드 저장소를 해당 테이블에서 온-프레미스에서 정지 데이터를 이동 하는 Contoso를 허용 합니다. 핫 및 정지 데이터 같은 테이블에 및는 항상 응용 프로그램 및 해당 사용자에 게 및 유지 관리 예: 백업 및 복원에 사용할 수 있습니다. 그림 1은 전체 확대/축소 데이터베이스를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="ca633-p102">As part of its business need to scale down its on-premises datacenters, Contoso chose to upgrade to SQL Server 2016 because of the Stretch Database hybrid feature and its seamless integration with Azure. Stretch Database allows Contoso to move the cold data in its tables from on-premises to cloud storage, freeing up local disk space and reducing maintenance. Both hot and cold data are in the same tables and are always available to applications and their users and for maintenance, such as backups and restores. Figure 1 shows Stretch Database.</span></span>
  
<span data-ttu-id="ca633-112">**그림 1: SQL Server 늘이기 데이터베이스**</span><span class="sxs-lookup"><span data-stu-id="ca633-112">**Figure 1: SQL Server Stretch Database**</span></span>

![하이브리드 데이터 솔루션으로 사용되는 SQL Server Stretch Database](images/Contoso_Poster/StretchDB01.png)
  
<span data-ttu-id="ca633-114">그림 1은 SQL 클라이언트 Azure PaaS에서 Azure SQL 전체 확대/축소 데이터베이스도 전달 하는 SQL Server 2016를 실행 하는 서버에 T-SQL 쿼리를 전송 하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="ca633-114">Figure 1 shows how a SQL client sends T-SQL queries to a server running SQL Server 2016, which forwards them to an Azure SQL Stretch Database in Azure PaaS.</span></span>
  
<span data-ttu-id="ca633-115">자세한 내용은 [전체 확대/축소 데이터베이스](https://msdn.microsoft.com/library/dn935011.aspx)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="ca633-115">For more information, see [Stretch Database](https://msdn.microsoft.com/library/dn935011.aspx).</span></span>
  
<span data-ttu-id="ca633-116">Contoso는 클라우드를 자신의 기록 데이터를 이동 하려면 다음이 단계를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca633-116">Contoso used these steps to move their historical data to the cloud:</span></span>
  
1. <span data-ttu-id="ca633-117">데이터베이스를 분석 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca633-117">Analyze databases</span></span>
    
    <span data-ttu-id="ca633-p103">클라우드로 이동 하기 위한 하 고 문제를 해결 하는 데이터베이스의 테이블에 대 한 분석을 수행 합니다. 새 전체 확대/축소 데이터베이스 관리자는 테이블에는 확장 될 수 있는 정지 데이터를 포함 하 여 SQL Server 2016의 모든 기능에서 기대할 수 있는 기능에 대 한 전체 개요를 제공 했습니다.</span><span class="sxs-lookup"><span data-stu-id="ca633-p103">Performed an analysis of the tables in the databases that they intended to move to the cloud and fixed any issues. The new Stretch Database Advisor gave them a full overview of what they can expect from all features in SQL Server 2016, including which tables have cold data that could be stretched.</span></span>
    
2. <span data-ttu-id="ca633-120">업그레이드</span><span class="sxs-lookup"><span data-stu-id="ca633-120">Upgrade</span></span>
    
    <span data-ttu-id="ca633-121">SQL Server 2016에 파리 본사 데이터 센터에서 업데이트 된 기존 SQL 서버를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca633-121">Updated existing SQL servers in the Paris headquarters datacenter to SQL Server 2016.</span></span>
    
3. <span data-ttu-id="ca633-122">콜드 데이터를 클라우드로 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="ca633-122">Migrate cold data to the cloud</span></span>
    
    <span data-ttu-id="ca633-p104">늘이기 데이터베이스와 Azure에서 늘이기 데이터베이스의 인스턴스를 마이그레이션하려면 테이블 파악 SQL Management Studio를 사용 합니다. 시간에 따른 및 백그라운드에서 SQL Server 2016 Azure에서 데이터베이스를 확장 하는 기록 데이터를 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca633-p104">Using SQL Management Studio, they identified the databases to stretch and the tables to migrate to instances of Stretch Database in Azure. Over time and in the background, SQL Server 2016 moved the historical data to stretch databases in Azure.</span></span>
    
<span data-ttu-id="ca633-125">SQL Server 2016 파리 본사에서 실행 하는 하나의 서버에 대 한 결과 구성은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ca633-125">Here is the resulting configuration for one server running SQL Server 2016 in the Paris headquarters.</span></span>
  
<span data-ttu-id="ca633-126">**그림 2: 전체 확대/축소 데이터베이스를 사용 하 여 Contoso의 데이터 센터의 서버에 대 한**</span><span class="sxs-lookup"><span data-stu-id="ca633-126">**Figure 2: Using Stretch Database for a server in Contoso's datacenter**</span></span>

![SQL Server가 실행되는 단일 컴퓨터에 대한 Contoso의 구성 SQL Server Stretch Database](images/Contoso_Poster/StretchDB02.png)

  
<span data-ttu-id="ca633-128">그림 2 Contoso의 데이터 센터에서 응용 프로그램 서버에 대 한 사용자 쿼리를 Azure PaaS에서 Azure SQL 전체 확대/축소 데이터베이스에 전달 되는 SQL 쿼리를 만드는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="ca633-128">Figure 2 shows how user queries to an application server in Contoso's datacenter become SQL queries that are passed to an Azure SQL Stretch Database in Azure PaaS.</span></span>
  
<span data-ttu-id="ca633-p105">사용자가 기존 응용 프로그램 및 쿼리를 통해 데이터에 액세스 합니다. 액세스 정책 동일 하 게 유지 합니다. 앞으로 이동, 테이프 백업에 대 한 않아도가 됩니다. 백업 및 복원 핫 데이터의 유지 관리 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca633-p105">Users access the data through existing apps and queries. Access policies remain the same. Moving forward, there is no need for tape backups. Maintenance consists of backing up and restoring hot data.</span></span>
  
<span data-ttu-id="ca633-133">후 전체 확대/축소 데이터베이스, Contoso를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca633-133">After implementing Stretch Database, Contoso:</span></span>
  
- <span data-ttu-id="ca633-134">온-프레미스 데이터 저장소 요구 사항 85% 감소 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca633-134">Reduced its on-premises data storage needs by 85%.</span></span>
    
- <span data-ttu-id="ca633-135">엔터프라이즈 저장소 시스템 및 자기 테이프 보관 파일에 대 한 의존성의 업데이트를 불필요 하 게 걸.</span><span class="sxs-lookup"><span data-stu-id="ca633-135">Made the update of the enterprise storage system and reliance on magnetic tape archives unnecessary.</span></span>
    
- <span data-ttu-id="ca633-136">일별 실행 비용을 크게 절감 하였습니다.</span><span class="sxs-lookup"><span data-stu-id="ca633-136">Reduced its daily running costs significantly.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="ca633-137">See Also</span><span class="sxs-lookup"><span data-stu-id="ca633-137">See Also</span></span>

[<span data-ttu-id="ca633-138">Contoso Corporation에 대 한 엔터프라이즈 시나리오</span><span class="sxs-lookup"><span data-stu-id="ca633-138">Enterprise scenarios for the Contoso Corporation</span></span>](enterprise-scenarios-for-the-contoso-corporation.md)
  
[<span data-ttu-id="ca633-139">Microsoft 클라우드 Contoso</span><span class="sxs-lookup"><span data-stu-id="ca633-139">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="ca633-140">Microsoft 클라우드 IT 아키텍처 리소스</span><span class="sxs-lookup"><span data-stu-id="ca633-140">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="ca633-141">데이터베이스를 늘이기</span><span class="sxs-lookup"><span data-stu-id="ca633-141">Stretch Database</span></span>](https://msdn.microsoft.com/library/dn935011.aspx)
  
[<span data-ttu-id="ca633-142">Microsoft의 엔터프라이즈 클라우드 로드맵: IT 의사 결정권자를 위한 리소스</span><span class="sxs-lookup"><span data-stu-id="ca633-142">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)




