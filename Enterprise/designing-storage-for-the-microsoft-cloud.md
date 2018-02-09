---
title: "Microsoft 클라우드를 위한 저장소 디자인 (영문)"
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
ms.assetid: 7e511118-1b75-413a-b959-ad0d3ffc9516
description: "요약:는 클라우드 저장소 필요한 이유를 이해 하 고 Microsoft의 클라우드 저장소 옵션 및 키 저장소 시나리오 목록을 검토 합니다."
ms.openlocfilehash: ed816743e2d85a622a3fbfbb129bf90a7db93881
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/09/2018
---
# <a name="designing-storage-for-the-microsoft-cloud"></a>Microsoft 클라우드를 위한 저장소 디자인 (영문)

 **요약:** 클라우드 저장소 필요한 이유를 이해 하 고 Microsoft의 클라우드 저장소 옵션 및 키 저장소 시나리오 목록을 검토 합니다.
  
Microsoft 클라우드 서비스와 함께 저장 장치를 통합 (영문) 광범위 한 서비스 및 클라우드 플랫폼 옵션에 액세스할을 수 있습니다.
  
## <a name="why-cloud-storage"></a>이유 클라우드 저장소?

클라우드 저장소를 사용 하 여 두 가지 주요 이유가 있습니다.
  
1. 에 대 한 시장 속도:
    
  - 고가용성 및 재해 복구에 대 한 빠른 구성
    
  - 없음 저장소 하드웨어를 구입
    
  - Microsoft의 클라우드 서비스에서 제공 하는 기본 제공 내부 작업
    
  - 전세계 각 지역에서에서 사용할 수 있는
    
2. 유지 관리 비용 절감:
    
  - 탄성 저장소 요구 사항에 맞는 위쪽 및 아래쪽 비율을 조정 하려면
    
  - 없음 저장소 하드웨어를 유지 하거나 마이그레이션
    
  - Microsoft는 유지 관리 하 고 인프라를 개선 하 여 기본 제공 배관공
    
  - 진행 중인 향상 된 시장에서 최상의 저장소 보안
    
## <a name="microsoft-cloud-storage-options"></a>Microsoft 클라우드 저장소 옵션

다양 한 클라우드 저장소 옵션을 쉽게 이해할 수 있도록, 건설 유추를 사용 합니다.
  
### <a name="move-in-ready"></a>이동-준비 완료

기존 서비스와 함께 제공 되는 이러한 미리 패키지 된 솔루션을 사용 합니다. 즉시 및 최소한의 구성으로 사용 합니다.
  
- Office 365
    
- Microsoft Intune
    
- 비즈니스용 OneDrive
    
- Dynamics 365
    
- Visual Studio Team Services
    
- Azure 사이트 복구
    
- Yammer 사이트 공유
    
- Azure 백업
    
이러한 각의 세부 정보에 대 한 저장소 옵션 클라우드 [이동-준비](move-in-ready.md)를 참조 하십시오.
  
### <a name="some-assembly-required"></a>필요한 일부 어셈블리

이러한 기존 서비스를 사용 하 여 추가 구성을 사용 하 여 저장소 솔루션에 대 한 시작점 또는 사용자 지정 맞춤에 대 한 구분 합니다.
  
- Azure 콘텐츠 배달 네트워크
    
- Azure 미디어 서비스
    
- HdInsight
    
- Azure 액세스 캐시
    
- Azure SQL 데이터베이스
    
- Azure VM에 SQL Server 설치
    
- Azure Cosmos DB
    
- StorSimple
    
- SQL azure 데이터 웨어하우스
    
- Azure 데이터 호수 저장소
    
이러한 각 클라우드 저장소 옵션의 세부 정보에 대 한 [일부 어셈블리 필요한](some-assembly-required.md)를 참조 합니다.
  
### <a name="build-from-the-ground-up"></a>처음부터 만들기

코딩와 함께 이러한 저장소 구성 요소를 사용 하 여 처음부터 직접 앱 또는 저장소 솔루션을 만듭니다.
  
- Azure 저장소 (파일)
    
- Azure 저장소 (blob)
    
- Azure 저장소 (큐의 경우)
    
- Azure 저장소 (표)
    
이러한 각 클라우드 저장소 옵션의 세부 정보를 [처음부터 작성](build-from-the-ground-up.md)을 참조 하십시오.
  
## <a name="key-storage-scenarios"></a>키 저장소 시나리오

클라우드 기반 저장소를 필요로 하는 주요 시나리오는 다음과 같습니다.
  
- 데이터 캐시
    
    고속 캐시에 저장 하 여 일반적으로 사용 되는 데이터에 대 한 액세스를 가속화 합니다.
    
- 팀 구성원과 공동으로 작업
    
    클라우드 저장소에서 데이터에 대 한 액세스를 허용 하려면 여러 사용자에 게 권한을 부여 합니다.
    
- 데이터 관리
    
    저장, 이동 또는 내부 또는 외부 대량 데이터를 삭제 합니다.
    
- 소스 코드 관리
    
    업로드 하 고 공동 작업, 클라우드에서 응용 프로그램 코드 파일을 실행 합니다.
    
- 백업 파일
    
    여러 클라우드 위치에서 내부 또는 외부 데이터 오프 사이트의 복사본을 저장 합니다.
    
- 회사 커뮤니케이션 게시
    
    내부 또는 외부 메시지에 대 한 발행물의 단일 지점을 만듭니다.
    
- 수백만 개의 이벤트를 배포 합니다.
    
    웹사이트, 앱 및 장치에서 원격 분석 수집에 대 한 저장소를 만듭니다.
    
- 비디오 관리 서비스
    
    저장 하 고 고객 또는 조직 사용자에 게 비디오 콘텐츠를 제공 합니다.
    
## <a name="next-step"></a>다음 단계

[이동-준비](move-in-ready.md) 클라우드 저장소 옵션을 검토 합니다.
  
## <a name="see-also"></a>참고 항목

[Microsoft Cloud Storage for Enterprise Architects](microsoft-cloud-storage-for-enterprise-architects.md)
  
[Microsoft 클라우드 IT 아키텍처 리소스](microsoft-cloud-it-architecture-resources.md)

[Microsoft의 엔터프라이즈 클라우드 로드맵: IT 의사 결정권자를 위한 리소스](https://sway.com/FJ2xsyWtkJc2taRD)


