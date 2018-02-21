---
title: "Contoso의 IT 인프라 및 요구 사항"
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
ms.assetid: 5d6a58b8-bec3-4629-9737-8733c7b7ec92
description: "요약: Contoso의 기본 구조는 온-프레미스 IT 인프라 및 방법의 비즈니스 요구 하 여 충족할 수 Microsoft의 클라우드 서비스를 이해 합니다."
ms.openlocfilehash: b8282c4bd04448266bc68e65f95aaaff0a7a5db8
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/09/2018
---
# <a name="contosos-it-infrastructure-and-needs"></a>Contoso의 IT 인프라 및 요구 사항

 **요약:** Contoso의 기본 구조는 온-프레미스 IT 인프라 및 방법의 비즈니스 요구 하 여 충족할 수 Microsoft의 클라우드 서비스를 이해 합니다.
  
Contoso가 온-프레미스에서 전환, 개인의 생산성 클라우드 기반 작업, 응용 프로그램 및 하이브리드 시나리오를 지 원하는 클라우드 (포함) 하나를 중앙 집중화 된 IT 인프라 관리 하는 중입니다.
  
## <a name="contosos-existing-it-infrastructure"></a>Contoso의 기존 IT 인프라

Contoso는 대부분의 중앙 사용 하 여 온-프레미스 파리 본사에서 응용 프로그램 데이터 센터와 IT 인프라 관리 합니다.
  
**그림 1: Contoso의 기존 IT 인프라 관리**

![Contoso의 기존 IT 인프라](images/Contoso_Poster/Existing_IT.png)
  
그림 1은 응용 프로그램 데이터 센터, DMZ, 및 인터넷 사용 하 여 중앙 사무소를 보여줍니다.
  
Contoso의 DMZ에서 서로 다른 서버 집합을 제공합니다.
  
- 파리 본사에서 작업자에 대 한 Contoso 인트라넷 및 웹 프록시에 원격 액세스 합니다.
    
- Contoso 공용 웹사이트에 대 한 호스팅, 어떤 고객 으로부터 주문할 수 제품, 부품 또는 공급 합니다.
    
- 파트너 통신 및 공동 작업에 대 한 엑스트라넷 Contoso 파트너에 대 한 호스팅.
    
## <a name="contosos-business-needs"></a>Contoso의 비즈니스 요구 사항

우선순위에 따라 Contoso의 비즈니스 요구 사항은 다음과 같습니다.
  
1. 국가별 규정 요구 사항 준수
    
    벌금을 방지 하 고 로컬 정부와 좋은 관계를 유지 관리, 하려면 Contoso 데이터 저장소 및 암호화 규정 준수를 확인 해야 합니다.
    
2. 공급 업체와 파트너 관리 개선
    
    익스트라넷 파트너 연결 하 고 유지 관리 비용이 매우 많이 됩니다. Contoso는 연결 된 인증을 사용 하는 클라우드 기반 솔루션으로 대체 하려고 합니다.
    
3. 모바일 직원 생산성, 장치 관리 및 액세스 향상
    
    Contoso의 모바일 전용 리소스는 확장 하 고 장치 관리 지적 재산 보호 및 리소스에 보다 효율적으로 액세스할 수 있도록 합니다.
    
4. 원격 액세스 인프라 감소
    
    클라우드로 원격 작업 자가 일반적으로 액세스 되는 리소스를 이동 하 여 Contoso의 원격 액세스 솔루션에 대 한 유지 관리 및 지원 비용을 줄여 비용을 절약할 것입니다.
    
5. 온-프레미스 데이터 센터 아래로 확장
    
    Contoso 데이터 센터 수백 대의 서버, IT 담당자가 높은 비즈니스 값 작업 부하를 유지 관리에서 혼동는 레거시 또는 보관 함수를 실행 하는 중 일부를 포함 합니다.
    
6. 분기의 최종 처리를 위해 수직 확장 컴퓨팅 및 저장소 리소스
    
    분기의 최종 재무 회계 및 재고 관리와 함께 처리 프로젝션 단기 증가 하면 서버 및 저장소에 필요 합니다.
    
## <a name="mapping-contosos-business-needs-to-microsofts-cloud-offerings"></a>Microsoft의 클라우드 서비스에 필요한 Contoso의 비즈니스 매핑 (영문)

Microsoft의 클라우드 서비스, Contoso의 분석을 바탕의 IT 부서는 다음과 같은 매핑을 결정 합니다.
  
|**Software as a Service (SaaS)**|**(Azure PaaS) 서비스로 플랫폼**|**As a Service (Azure IaaS) 인프라**|
|:-----|:-----|:-----|
|**Office 365:** 클라우드에서 기본 그룹 및 개인 생산성 응용 프로그램입니다. <br/> 비즈니스 요구 사항: 1 3 5  <br/> |판매를 호스트 하 고 문서 및 클라우드 기반 앱을 사용 하 여 정보 시스템을 지원 합니다.  <br/> 비즈니스 요구: 3  <br/> |클라우드 기반 서버에 보관 하 고 레거시 시스템을 이동 합니다.  <br/> 비즈니스 요구: 5  <br/> |
|**Dynamics 365:** 클라우드 기반 고객 및 공급 업체 관리를 사용 합니다. DMZ에 익스트라넷 파트너를 제거 합니다.<br/> 비즈니스 요구: 2  <br/> |모바일 응용 프로그램은 클라우드 기반 데이터 센터 기반 파리가 아닌 합니다.  <br/> 비즈니스 요구 사항: 3 4  <br/> |자주 사용 앱 및 온-프레미스 데이터 센터에서 데이터를 마이그레이션하십시오.  <br/> 비즈니스 요구: 5  <br/> |
|**Intune/EMS:** IOS 및 Android 장치를 관리 합니다. <br/> 비즈니스 요구: 3  <br/> ||임시 서버 및 분기의 끝 처리 요구 사항에 대 한 저장소를 추가 합니다.  <br/> 비즈니스 요구: 6  <br/> |
   
## <a name="see-also"></a>참고 항목

[Microsoft 클라우드의 Contoso](contoso-in-the-microsoft-cloud.md)
  
[Microsoft 클라우드 IT 아키텍처 리소스](microsoft-cloud-it-architecture-resources.md)

[Microsoft의 엔터프라이즈 클라우드 로드맵: IT 의사 결정권자를 위한 리소스](https://sway.com/FJ2xsyWtkJc2taRD)


