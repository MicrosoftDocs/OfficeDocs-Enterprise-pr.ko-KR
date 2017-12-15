---
title: Some assembly required
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
ms.assetid: ccf1b8b3-0d50-4c66-b314-f480245fad5e
description: 'Summary: Get the details on the set of cloud storage options that you can use to create your custom storage solution.'
ms.openlocfilehash: bf6f7586b3a890cd25aba314e4892d5e2ac5bb34
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2017
---
# <a name="some-assembly-required"></a>Some assembly required

 **Summary:** Get the details on the set of cloud storage options that you can use to create your custom storage solution.
  
"Some assembly required " storage solutions:
  
- Use existing services as a starting point for your storage solution.
    
- Require some configuration or coding.
    
- Can be customized to fit your needs.
    
The following sections describe the details of each "Some assembly required" storage solution.
  
## <a name="azure-content-delivery-network"></a>Azure Content Delivery Network

### <a name="features"></a>기능

- Advanced and real time analytics
    
- Robust security against DDoS
    
- Gets content automatically from an Azure Website or Azure Cloud Service once you set up the integration
    
- New partnership with Akamai
    
- Can handle sudden traffic spikes and heavy loads
    
### <a name="common-uses"></a>Common uses

- Distribute audio, video, applications, images, and other files faster and more reliably to customers by using the servers that are closest to them
    
### <a name="key-storage-scenarios"></a>Key storage scenarios

- Manage data
    
- Manage videos
    
### <a name="resources"></a>리소스

For additional information, click [here](https://azure.microsoft.com/services/cdn/).
  
For cost information, click [here](https://azure.microsoft.com/pricing/details/cdn/).
  
## <a name="hdinsight"></a>HdInsight

### <a name="features"></a>기능

- Apache Hadoop distribution powered by the cloud A Data Lake service
    
- Scale to petabytes on demand
    
- Process unstructured and semi-structured data Develop in Java, .NET, and more
    
- Skip buying and maintaining hardware
    
- Connect on-premises Hadoop clusters with the cloud
    
- Flexibility to deploy arbitrary Hadoop projects through custom scripts (e.g. R, Giraph, Solr)
    
### <a name="common-uses"></a>Common uses

- Data analytics workloads
    
- In-memory data processing framework for big data (Spark)
    
- Real-time stream processing (Storm)
    
- Large transactional processing (OLTP) of non-relational data (HBase)
    
### <a name="key-storage-scenarios"></a>Key storage scenarios

- Manage data
    
### <a name="resources"></a>리소스

For additional information, click [here](https://azure.microsoft.com/services/hdinsight/).
  
For cost information, click [here](https://azure.microsoft.com/pricing/details/hdinsight/).
  
## <a name="azure-sql-database"></a>Azure SQL 데이터베이스

### <a name="features"></a>기능

- Optimized to reduce management and costs
    
- Automatic high availability, disaster recovery, and upgrade
    
- Recommended for organizations managing hundreds or thousands of databases of up to 1 TB in size
    
- Sharding techniques can split data across databases for increased storage
    
- Stretch database with SQL Server 2016
    
### <a name="common-uses"></a>Common uses

- New cloud-designed applications with relational data
    
- Data processing over schematic, highly structured data sets with relationships
    
- Spatial data or rich data types
    
### <a name="key-storage-scenarios"></a>Key storage scenarios

- Manage data
    
### <a name="elastic-database"></a>Elastic database

Use the virtually unlimited resources of Azure SQL Database when:
  
- The total amount of data is too large to fit within the constraints of a single database.
    
- The transaction throughput of the overall workload exceeds the capabilities of a single database.
    
- Tenants require physical isolation from each other, so separate databases are needed for each tenant.
    
- Different sections of a database need to reside in different geographies for compliance, performance, or geopolitical reasons.
    
With vertical scaling, you can change Azure database performance level/edition or by using elastic database pools.
  
![Azure SQL Database에서 제공한 세로 배율입니다.](images/Storage_Poster/CloudStor-VertScale.png)
  
With horizontal scaling, you can add new databases as needed.
  
![Azure SQL Database에서 제공한 가로 배율입니다.](images/Storage_Poster/CloudStor-HorizScale.png)
  
Click [here](https://docs.microsoft.com/azure/sql-database/sql-database-elastic-scale-introduction) for more information.
  
### <a name="stretch-database-with-sql-server-2016"></a>SQL Server 2016에 적용된 스트레치 데이터베이스

Stretch database is a feature of SQL Server 2016 that allows you to transparently and securely move cold data, such as closed business data in a large table that contains customer order information, to a SQL Stretch database in Azure. When stretched, the contents of a SQL Server instance, a database, or even a single table is the combination of local data in SQL Server 2016 server and remote data in Azure. Data that becomes eligible for stretch is automatically moved to Azure by SQL Server 2016.
  
![SQL Server 2016을 사용하는 Stretch Database입니다.](images/Storage_Poster/CloudStor-Stretch.png)
  
User queries that include the historical data are transparently forwarded to Azure SQL Stretch database. The queries do not need to be re-written, even though the table is stretched.
  
Stretch database provides a cost-effective option for long-term storage and transparent access to historical data. It also solves performance and availability problems that arise when tables become very large.
  
Click [here](https://msdn.microsoft.com/library/dn935011.aspx) for more information.
  
### <a name="resources"></a>리소스

For additional information, click [here](http://azure.microsoft.com/services/sql-database/).
  
For cost information, click [here](http://azure.microsoft.com/pricing/details/sql-database/).
  
## <a name="azure-cosmos-db"></a>Azure Cosmos DB

### <a name="features"></a>기능

- Guaranteed low latency, 99.99% availability SLA with limitless, elastic scale of storage and throughput
    
- All data is globally replicated across any number of regions with transparent failover and four well-defined consistency levels
    
- Automatically indexes all your data without requiring schemas or secondary indices
    
- Rich SQL and JavaScript queries and multi-item transactions
    
### <a name="common-uses"></a>Common uses

- IoT, Mobile and Social
    
- 게임
    
- 정품
    
- Content management
    
### <a name="key-storage-scenarios"></a>Key storage scenarios

- Manage data
    
### <a name="cosmos-db-vs-azure-tables-vs-azure-sql-database"></a>Cosmos DB vs. Azure Tables vs. Azure SQL Database

Common attributes of Cosmos DB, Azure Table Storage, and Azure SQL Database:
  
- 99.99 availability SLA
    
- Fully managed database services
    
- ISO 27001, HIPAA and EU Model Clauses Compliant
    
The following table shows the uncommon attributes of Azure Cosmos DB, Azure Table Storage, and Azure SQL Database.
  
![Cosmos DB의 일반적이지 않은 특성 대 Azure Tables 대 Azure SQL Database](images/Storage_Poster/CloudStor-Table.png)
  
### <a name="resources"></a>리소스

자세한 내용은 [여기](http://azure.microsoft.com/services/documentdb/)합니다.
  
For cost information, click [here](http://azure.microsoft.com/pricing/details/documentdb/).
  
## <a name="azure-media-services"></a>Azure Media Services

### <a name="features"></a>기능

- 라이브 및 배율로 VOD (주문형) 배달에 비디오
    
- Highly available encoding and streaming
    
- Supports Flash, iOS, Android, HTML5, and Xbox
    
- Studio-certified DRM support
    
- Rich content monetization
    
- Broad ecosystem of pre-integrated partners
    
### <a name="common-uses"></a>Common uses

- Encode, store, and stream audio and video at scale
    
- Real time streaming and VOD
    
- Streamlined video content management
    
### <a name="key-storage-scenarios"></a>Key storage scenarios

- Manage videos
    
### <a name="resources"></a>리소스

For additional information, click [here](https://azure.microsoft.com/services/media-services/).
  
For cost information, click [here](http://azure.microsoft.com/pricing/details/media-services/).
  
## <a name="azure-redis-cache"></a>Azure 액세스 캐시

### <a name="features"></a>기능

- Secure, dedicated Redis server with high-availability with data replication and failover managed by Microsoft
    
- Recommended for any app needing high-throughput
    
- Available in sizes up to 530 GB and beyond (with Premium and automatic sharding)
    
- 지 속성 액세스 지속 되는 메모리에 캐시 된 데이터를 Azure 저장소
    
- 액세스 클러스터링 최대 눈금 및 처리량을 달성할 수 있습니다.
    
- Azure 가상 네트워크를 지 원하는 향상 된 보안 및 네트워크 격리
    
### <a name="common-uses"></a>일반적으로 사용

- Azure Cosmos DB Azure SQL 데이터베이스 등의 모든 저장소 서비스의 데이터에 대 한 역방향 조회
    
- Synchronized content from other data stores
    
### <a name="key-storage-scenarios"></a>키 저장소 시나리오

- 데이터 캐시
    
- 처리량이 많은 응용 프로그램에 대 한 메시지 브로커
    
### <a name="resources"></a>리소스

자세한 내용은 [여기](http://azure.microsoft.com/services/cache/)합니다.
  
비용 정보에 대 한 클릭 [여기](http://azure.microsoft.com/pricing/details/cache/)합니다.
  
## <a name="sql-server-on-an-azure-vm"></a>Azure VM에 SQL Server 설치

### <a name="features"></a>기능

- SQL Server는 Azure 가상 컴퓨터에 설치 된 응용 프로그램으로 실행
    
- SQL Server를 사용한 갤러리 이미지를 설치 하거나 직접 SQL 서버 라이선스를 가져올 사용
    
### <a name="common-uses"></a>일반적으로 사용

- 응용 프로그램에 대 한 데이터를 관리 합니다.
    
### <a name="key-storage-scenarios"></a>키 저장소 시나리오

- 데이터 관리
    
### <a name="resources"></a>리소스

자세한 내용은 [여기](http://azure.microsoft.com/services/virtual-machines/)합니다.
  
비용 정보에 대 한 클릭 [여기](http://azure.microsoft.com/pricing/details/virtual-machines/)합니다.
  
## <a name="storsimple"></a>StorSimple

### <a name="features"></a>기능

- 확장성, 엔터프라이즈 하이브리드 SAN 저장소 SSD HDD와 온-프레미스 하이브리드 저장소 배열에 클라우드 저장소 솔루션의 통합 된 확장으로
    
- 인라인 중복 제거, 압축, 자동 계층으로 구성 하 고 구조화 되지 않은 암호화 및 반 구조화 된 데이터
    
- 클라우드 스냅숏을 사용 하 여 자동화 된 오프 사이트 데이터 보호
    
- 매우 효율적이 고 위치에 관계 없이 재해 복구
    
- Azure의 StorSimple 가상 기기를 사용 하 여 엔터프라이즈 데이터에 대 한 데이터 모바일 기능
    
### <a name="common-uses"></a>일반적으로 사용

- 파일 공유, 보관 및 기타 데이터 저장소와 관련 된 데이터 증가세를 관리 합니다.
    
- 파일 공유, 가상 컴퓨터, SQL, 및 SharePoint (원격 Blob 저장소를 사용 하 여)에 대 한 오프 사이트 데이터 보호 및 재해 복구
    
- Azure의 데이터를 복제 하 고 비즈니스 민첩성 향상을 클라우드 스냅숏을 활용합니다
    
### <a name="key-storage-scenarios"></a>키 저장소 시나리오

- 데이터 관리
    
- 공동 작업
    
### <a name="resources"></a>리소스

자세한 내용은 [여기](http://azure.microsoft.com/services/storsimple/)합니다.
  
비용 정보에 대 한 클릭 [여기](http://azure.microsoft.com/pricing/details/storsimple/)합니다.
  
## <a name="azure-sql-data-warehouse"></a>SQL azure 데이터 웨어하우스

### <a name="features"></a>기능

- 최대 동시 쿼리 32 페타바이트를 조정 하는 탄력적 데이터웨어하우스
    
- 많은 양의 fast 사용 하 여 구조화 된 데이터 관리 분석에서 동적으로 증가 하 고 축소 compute (초)
    
- 투명 한 데이터 암호화를 지원합니다.
    
- 7 일 동안 8 시간 마다 백업
    
### <a name="common-uses"></a>일반적으로 사용

- 판매 보고서
    
- 사용 현황 보고서
    
- 많은 양의 데이터
    
### <a name="key-storage-scenarios"></a>키 저장소 시나리오

- 데이터 관리
    
### <a name="resources"></a>리소스

자세한 내용은 [여기](https://azure.microsoft.com/services/sql-data-warehouse/)합니다.
  
비용 정보에 대 한 클릭 [여기](https://azure.microsoft.com/pricing/details/sql-data-warehouse/)합니다.
  
## <a name="azure-data-lake-store"></a>Azure 데이터 호수 저장소

### <a name="features"></a>기능

- 큰 데이터 분석 작업에 대 한 하이퍼 규모 리포지토리
    
- 클라우드를 위한 Hadoop 분산 파일 시스템
    
- 파일 크기에 고정된 제한 없음
    
- 계정 크기에 고정된 제한 없음
    
- 원시 형식으로 구조화 되지 않은 및 구조화 된 데이터
    
- 분석 성능을 향상 시키기 위해 대규모 처리량
    
- 높은 내구성, 가용성 및 안정성 (99.9% 엔터프라이즈급 SLA 및 24/7 지원)
    
- Azure Active Directory 액세스 제어
    
### <a name="common-uses"></a>일반적으로 사용

- 모든 유형의 한곳에서 수집한 데이터를 저장 하려면 엔터프라이즈 수준 리포지토리
    
### <a name="key-storage-scenarios"></a>키 저장소 시나리오

- 데이터 관리
    
### <a name="resources"></a>리소스

자세한 내용은 [여기](https://azure.microsoft.com/services/data-lake-store/)합니다.
  
비용 정보에 대 한 클릭 [여기](https://azure.microsoft.com/pricing/details/data-lake-store/)합니다.
  
## <a name="next-step"></a>다음 단계

클라우드 저장소를 [처음부터 작성](build-from-the-ground-up.md) 옵션을 검토 합니다.
  
## <a name="see-also"></a>See Also

[엔터프라이즈 설계자 용 Microsoft 클라우드 저장소](microsoft-cloud-storage-for-enterprise-architects.md)
  
[Microsoft 클라우드 IT 아키텍처 리소스](microsoft-cloud-it-architecture-resources.md)

[Microsoft의 엔터프라이즈 클라우드 로드맵: IT 의사 결정권자를 위한 리소스](https://sway.com/FJ2xsyWtkJc2taRD)



