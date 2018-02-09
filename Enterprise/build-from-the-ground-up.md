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
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 84348d0c-d9d1-4a98-9b99-8433f9b70e45
description: "요약: 클라우드 집합에 대 한 자세한 내용은 직접 저장소 서비스 또는 솔루션 만들기를 사용할 수 있는 저장소 구성 요소를 가져옵니다."
ms.openlocfilehash: be7ea3e7526115f1a983ec89f2afeb5d130daee1
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/09/2018
---
# <a name="build-from-the-ground-up"></a>처음부터 만들기

 **요약:** 클라우드 집합에 정보를 직접 저장소 서비스 또는 솔루션을 만드는데 사용할 수 있는 저장소 구성 요소를 가져옵니다.
  
"처음부터 구축" 저장소 솔루션:
  
- 이 기능을 사용 하면 처음부터 직접 저장소 솔루션을 만들 수 있습니다. 
    
- REST Api를 사용 하 여 프로그래밍이 필요 합니다.
    
- 최상의 사용자 지정 및 유연성을 제공 합니다.
    
다음 섹션에서는 각 "처음부터 구축" 저장소 옵션에 대 한 세부 정보에 설명 합니다.
  
## <a name="azure-storage-files"></a>Azure 저장소 (파일)

### <a name="features"></a>기능

- 쉽게 클라우드로 레거시 응용 프로그램을 이동 하려면
    
- 새 응용 프로그램에 대 한 기본적으로 사용 되는 blob 저장소
    
- Azure 가상 컴퓨터에서 탑재할 수 있습니다.
    
- 온-프레미스 SMB 3.0 탑재할 수 있습니다.
    
- Windows 및 Linux로 작업
    
- 지원 하지 않는 Azure AD 기반 인증 또는 Acl (Azure 저장소 계정 키 인증 및 파일 공유에 대 한 권한이 부여 된 액세스를 제공)
    
### <a name="common-uses"></a>일반적으로 사용

- 파일 공유를 사용 하는 클라우드로 레거시 응용 프로그램 마이그레이션
    
- 개발 및 테스트 도구를 공유 합니다.
    
- 분산된 응용 프로그램에서 로그, 진단 데이터를 저장 하 고 크래시 덤프 수 있습니다.
    
### <a name="key-storage-scenarios"></a>키 저장소 시나리오

- 백업 파일
    
### <a name="resources"></a>리소스

자세한 내용은 [여기](https://msdn.microsoft.com/library/azure/dn166972.aspx)합니다.
  
비용 정보에 대 한 클릭 [여기](http://azure.microsoft.com/pricing/details/storage/)합니다.
  
## <a name="azure-storage-blobs"></a>Azure 저장소 (blob)

### <a name="features"></a>기능

- 각 저장소 계정에는 최대 500 TB 보유할 수 있습니다 (하나의 구독 수 계정이 여러 개인 저장소)
    
- 저장소 계정은 자신에 게 적용 되는 보안 하 고 blob가 포함 될 수 있는 컨테이너 구조로 구성 됩니다.
    
- 블록 blob가 스트리밍에 최적화 된 및 최대 200GB 크기의 개체, 클라우드를 저장 합니다.
    
- 페이지 blob가 나타내는 PaaS 디스크에 최적화 된 및 기록 임의 지 원하는 최대 1TB 크기
    
- Append blob에 최적화 된 작업을 추가할 최대 195 g B
    
- 프리미엄 저장소 SSD 저장소를 통해 더 빠른 IOPS를 제공합니다.
    
### <a name="common-uses"></a>일반적으로 사용

- 파일, 컴퓨터, 데이터베이스 및 장치 이미지 및 웹 응용 프로그램에 대 한 텍스트의 백업
    
- 클라우드 응용 프로그램에 대 한 구성 데이터
    
- 예: 로그 및 기타 큰 데이터 집합의 큰 데이터
    
- Azure 사용 하 여 blob HDInsight 및 가상 컴퓨터 디스크 등의 자체 서비스에 대 한 저장소
    
### <a name="key-storage-scenarios"></a>키 저장소 시나리오

- 데이터 관리
    
### <a name="resources"></a>리소스

자세한 내용은 [여기](https://msdn.microsoft.com/library/azure/dd179376.aspx)합니다.
  
비용 정보에 대 한 클릭 [여기](http://azure.microsoft.com/pricing/details/storage/)합니다.
  
## <a name="azure-storage-queues"></a>Azure 저장소 (큐의 경우)

### <a name="features"></a>기능

- 저장소 계정에는 큐의 숫자 포함 될 수 있습니다.
    
- (있을 때까지 저장소 계정의 전체) 큐에서 메시지의 숫자를 포함할 수 있습니다.
    
- 메시지 큐는 자동으로 7 일이 지난 후에 삭제 된 값이 없는 경우 검색 및 삭제 된 응용 프로그램에 의해
    
- 메시지 크기에서 64KB 최대 수 있습니다.
    
- 저장소 계정 수준 보안
    
- 큐는 제어 메시지를 하지 원시 데이터를 전달 하기 위한 것
    
### <a name="common-uses"></a>일반적으로 사용

- 비동기적으로 처리 된 작업의 백로그 만들기
    
- 로그 메시지 처리
    
- 응용 프로그램을 분리
    
### <a name="key-storage-scenarios"></a>키 저장소 시나리오

- 이벤트를 배포 합니다.
    
### <a name="resources"></a>리소스

자세한 내용은 [여기](https://msdn.microsoft.com/library/azure/dd179353.aspx)합니다.
  
비용 정보에 대 한 클릭 [여기](http://azure.microsoft.com/pricing/details/storage/)합니다.
  
## <a name="azure-storage-tables"></a>Azure 저장소 (표)

### <a name="features"></a>기능

- 반구조적된 데이터 집합에 가장 적합 한
    
- 기존 SQL 보다 일반적으로 더 낮은 비용
    
- 초고속 값에 대 한 쿼리 하는 경우 느린 키로 이동한 다음에 대 한 쿼리 하는 경우
    
- 확장성이 매우 높은; 저장소 계정의 제한 최대 테이블의 모든 크기
    
- REST API,.NET, 제한 된 oData 프로토콜을 통해 액세스할 수 있음
    
- 값을 직렬화 해야 합니다.
    
### <a name="common-uses"></a>일반적으로 사용

- 웹 응용 프로그램에 대 한 사용자 데이터
    
- 주소록
    
- 장치 정보
    
### <a name="key-storage-scenarios"></a>키 저장소 시나리오

- 데이터 관리
    
### <a name="resources"></a>리소스

자세한 내용은 [여기](https://msdn.microsoft.com/library/azure/dd179463.aspx)합니다.
  
비용 정보에 대 한 클릭 [여기](http://azure.microsoft.com/pricing/details/storage/)합니다.
  
## <a name="microsoft-azure-storage-recommendations"></a>Microsoft Azure 저장소 권장 사항

Azure 저장소와 사용자 지정 저장소 솔루션을 디자인할 때 다음 사항에 유의 해야 합니다.
  
- 여러 저장소 계정을 증가 크기 (> 100 테라바이트)에 대 한 또는 더 많은 처리량 (초당 5, 000 개 > 작업)에 대 한 확장성이 높아집니다을 활용 합니다.
    
- 구성 변경 사항으로, 코드 변경 사항으로 하지 추가 저장소 계정을 추가할 수 있는 기능을 디자인 합니다.
    
- 신중 하 게 삽입 및 쿼리 성능 면에서 원하는 확장을 사용 하도록 설정 하려면 테이블 저장소에 대 한 분할 기능을 선택 합니다.
    
- 메타 데이터 (속성 이름)으로 테이블 속성에 대 한 짧은 열 이름이 저장된 인밴드 (계산 최대 행 크기는 1MB 향해 열 이름)을 선택 합니다.
    
- 가능 하면 저장소에 대 한 작업을 일괄 처리 합니다.
    
- 분산된 캐시를 구성 데이터베이스에 대 한 정보를 적극적으로 캐시 합니다.
    
- 응용 프로그램의 성능이 나 신뢰성 이면 캐시에서 사용할 수 있는 데이터의 특정 세그먼트를 필요에 따라 다릅니다 응용 프로그램 캐시 미리 채워진 될 때까지 들어오는 요청을 거부 해야 합니다.
    
- 여러 데이터베이스에는 부하 분산을 데이터 또는 가로에서 세로로 (테이블에 의해) (여러 파편 간에 세그먼트 테이블)으로 분할 합니다.
    
## <a name="see-also"></a>참고 항목

[Microsoft Cloud Storage for Enterprise Architects](microsoft-cloud-storage-for-enterprise-architects.md)
  
[Microsoft 클라우드 IT 아키텍처 리소스](microsoft-cloud-it-architecture-resources.md)

[Microsoft의 엔터프라이즈 클라우드 로드맵: IT 의사 결정권자를 위한 리소스](https://sway.com/FJ2xsyWtkJc2taRD)



