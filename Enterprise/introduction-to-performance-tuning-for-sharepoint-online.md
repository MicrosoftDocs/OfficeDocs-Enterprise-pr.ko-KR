---
title: SharePoint Online의 성능 조정 소개
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/22/2018
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 81c4be5f-327e-435d-a568-526d68cffef0
description: 이 문서에서는 SharePoint Online에서 최상의 성능을 위해 페이지를 디자인할 때 고려 해야할 어떤 특정 측면에 설명 합니다.
ms.openlocfilehash: 07938770d711477126f78fc583e8d2533ba5c1d1
ms.sourcegitcommit: ba91a1d2d785c1df425617b309fec2edc093793a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/09/2018
ms.locfileid: "26219878"
---
# <a name="introduction-to-performance-tuning-for-sharepoint-online"></a>SharePoint Online의 성능 조정 소개

이 문서에서는 SharePoint Online에서 최상의 성능을 위해 페이지를 디자인할 때 고려 해야할 어떤 특정 측면에 설명 합니다.
     
## <a name="sharepoint-online-metrics"></a>SharePoint Online 메트릭

SharePoint Online에 대한 다음의 광범위한 메트릭은 성능의 실제 데이터를 제공합니다.
  
- 페이지 로드 속도
    
- 페이지당 필요한 왕복 횟수
    
- 서비스 관련 문제
    
- 성능 저하를 유발하는 기타 사항
    
### <a name="conclusions-reached-because-of-the-data"></a>데이터로 인해 도달한 결론

데이터를 통해 알 수 있는 사항은 다음과 같습니다.
  
- 대부분의 페이지가 SharePoint Online에서 제대로 작동합니다.
    
- 사용자 지정되지 않은 페이지가 매우 빠르게 로드됩니다.
    
- 비즈니스용 OneDrive, 팀 사이트 및 시스템 페이지(_layouts 등)가 모두 신속하게 로드됩니다.
    
- SharePoint Online 페이지 중 가장 느린 1%를 로드하는 데 5,000밀리초가 넘게 걸립니다.
    
사용할 수 있는 한 가지 간단한 벤치마크 테스트는 사용자 지정된 일부 기능을 사용하면서 자체 포털의 로드 시간을 비즈니스용 OneDrive 홈 페이지의 로드 시간과 비교하여 성능을 측정하는 것입니다. 지원 서비스에서 사용자가 네트워크 성능 문제를 해결할 때 필요한 첫 번째 단계가 바로 여기에 해당합니다.
  
## <a name="use-a-standard-user-account-when-checking-performance"></a>성능 확인할 때 표준 사용자 계정을 사용 하 여

사이트 모음 관리자, 사이트 소유자, 편집기 또는 참가자 추가 보안 그룹에 속해, 추가 권한이 되어 있으므로 SharePoint 페이지에 로드 되는 추가 요소 합니다.
  
SharePoint 온-프레미스 및 SharePoint Online에 적용할 수 있는 반드시 온-프레미스 시나리오에서 차이 그만큼 쉽게 발견 되지 SharePoint Online에서 같이 합니다.
  
올바르게 페이지는 사용자에 대해 수행 하는 방식 평가 하기 위해 제작 컨트롤 및 보안 그룹에 관련 된 추가 트래픽 로드를 방지 하기 위해 표준 사용자 계정을 사용 해야 합니다.
  
## <a name="connection-categories-for-performance-tuning"></a>성능 조정에 대한 연결 범주

서버와 사용자 간의 연결을 세 가지 주요 구성 요소로 분류할 수 있습니다. 로드 시간을 고려하여 SharePoint Online 페이지를 설계할 때는 다음 사항에 유의하세요.
  
- **서버** Microsoft 데이터 센터에서 호스팅하는 서버입니다.
    
- **네트워크** Microsoft 네트워크, 인터넷 및 온-프레미스 네트워크 간에 데이터 센터 및 사용자에 게 합니다.
    
- **브라우저** 여기서는 페이지가 로드 됩니다.
    
이러한 세 가지 연결에서 느린 페이지의 95%를 차지하는 5가지 일반적인 원인이 있습니다. 다음과 같은 각 원인이 이 문서에 설명되어 있습니다.
  
- 탐색 문제
    
- 콘텐츠 롤업
    
- 대용량 파일
    
- 서버에 대한 많은 요청
    
- 웹 파트 처리
    
### <a name="server-connection"></a>서버 연결

SharePoint 온-프레미스의 성능에 영향을 주는 많은 문제가 SharePoint Online에도 적용됩니다.
  
예상할 수 있듯이 온-프레미스 SharePoint를 사용하면 서버의 성능을 훨씬 더 강력하게 제어할 수 있습니다. SharePoint Online을 사용하는 경우 상황이 약간 달라집니다. 서버가 수행하는 작업이 많을수록 페이지를 렌더링하는 데 더 오래 걸립니다. SharePoint를 사용하는 경우 이러한 측면에서 가장 큰 원인은 여러 웹 파트가 있는 복잡한 페이지입니다.
  
SharePoint Server 온-프레미스
  
![온-프레미스 서버의 스크린샷](media/a8e9b646-cdff-4131-976a-b5f891da44ac.png)
  
SharePoint Online
  
![온라인 서버의 스크린샷](media/46b27ded-d8a4-4287-b3e0-2603a764b8f8.png)
  
SharePoint Online을 사용하는 경우에는 특정 페이지 요청이 실제로 여러 서버 호출을 발생할 수 있습니다. 개별 요청에 대해 서버 간에 단계별 요청 구조가 발생할 수 있습니다. 이러한 상호 작용은 페이지 부하 측면에서는 많은 비용을 초래하며 속도를 저하시킵니다.
  
이러한 서버 간 상호 작용의 예는 다음과 같습니다.
  
- 웹 - SQL 서버
    
- 웹 - 응용 프로그램 서버
    
서버 상호 작용을 저하시킬 수 있는 기타 요인으로는 캐시 누락이 있습니다. 온-프레미스 SharePoint와 달리, 이전에 방문한 페이지에 동일한 서버가 사용될 가능성이 아주 적으므로 개체 캐싱이 더 이상 사용되지 않습니다.
  
### <a name="network-connection"></a>네트워크 연결

사용할 수 있도록 하지 WAN의 온-프레미스 sharepoint를 데이터 센터와 최종 사용자에 게 간의 고속 연결을 사용할 수 있습니다. 일반적으로 작업에는 네트워크의 관점에서 관리 하기 어렵습니다.
  
SharePoint Online을 사용하는 경우 다음과 같은 몇 가지 요인을 더 고려해야 합니다.
  
- Microsoft 네트워크
    
- 인터넷
    
- ISP
    
사용 중인 SharePoint 버전(및 네트워크)와 관계없이, 일반적으로 네트워크의 사용량을 높이는 항목은 다음과 같습니다.
  
- 대형 페이로드
    
- 많은 수의 파일
    
- 서버와의 큰 실제 거리
    
SharePoint Online에서 활용할 수 있는 기능 중 하나는 Microsoft CDN (콘텐츠 배달 네트워크)입니다. CDN는 기본적으로 여러 데이터 센터에 배포 된 서버의 분산된 컬렉션입니다. CDN와 경우에 클라이언트 멀리 떨어져 원래 SharePoint 서버에서 클라이언트에 근접 한 서버에서 페이지에 콘텐츠를 호스팅할 수 있습니다. Microsoft 됩니다 수를 사용 하 여이 더 나중에 SharePoint Online 관리자 홈 페이지 같은 수 없는 사용자 지정할 수 있는 페이지의 로컬 인스턴스를 저장 합니다. Cdn 하는 방법에 대 한 자세한 내용은 [콘텐츠 배달 네트워크](https://docs.microsoft.com/en-us/office365/enterprise/content-delivery-networks)를 참조 하십시오.
  
고려해야 하지만 많은 작업을 수행할 수는 없는 측면이 바로 ISP의 연결 속도입니다. 간단한 속도 테스트 도구로 연결 속도를 알 수 있습니다.
  
### <a name="browser-connection"></a>브라우저 연결

성능 측면에서 웹 브라우저에 대해 고려해야 할 몇 가지 요소가 있습니다.
  
복잡 한 페이지를 방문 하는 것 성능에 영향을 줍니다. 대부분의 브라우저에 하나만 평균 하는 동안 작은 캐시 (약 90 MB), 웹 페이지는 일반적으로 약 1.6 MB입니다. 이 사용 하는 데 긴 필요 하지 않습니다.
  
대역폭이 문제가 될 수도 있습니다. 예, 사용자가 다른 세션에 비디오를 보고,이 SharePoint 페이지의 성능을 적용 됩니다. 스트리밍 미디어에서 사용자를 방지 수 없는 사용자에 대 한 페이지를 로드 하는 방식을 제어할 수 있습니다.
  
다른 SharePoint Online 페이지 사용자 지정 방법에 대 한 다음 문서 및 기타 모범 사례 최적의 성능을 얻을 수 있도록 체크아웃 합니다.
  
- [SharePoint Online에 대한 탐색 옵션](navigation-options-for-sharepoint-online.md)
    
- [SharePoint Online에 대 한 페이지 진단 도구를 사용 하 여](page-diagnostics-for-spo.md)
    
- [SharePoint Online에 대한 이미지 최적화](image-optimization-for-sharepoint-online.md)
    
- [SharePoint Online에서 이미지 및 JavaScript 로드 지연](delay-loading-images-and-javascript-in-sharepoint-online.md)
    
- [SharePoint Online의 축소 및 묶음](minification-and-bundling-in-sharepoint-online.md)
    
- [콘텐츠 배달 네트워크 사용](using-content-delivery-networks-with-sharepoint-online.md)
    
- [콘텐츠 쿼리 웹 파트는 대신 콘텐츠 검색 웹 파트를 사용 하 여 SharePoint Online에서 성능을 개선합니다](using-content-search-web-part-instead-of-content-query-web-part-to-improve-perfo.md)
    
- [용량 계획 및 부하 테스트를 SharePoint Online](capacity-planning-and-load-testing-sharepoint-online.md)
    
- [SharePoint Online의 성능 문제 진단](diagnosing-performance-issues-with-sharepoint-online.md)
    
- [SharePoint online에서 개체 캐시 사용](using-the-object-cache-with-sharepoint-online.md)
    
- [방법: SharePoint Online에서 제한 또는 차단되지 않도록 방지](https://msdn.microsoft.com/en-us/library/office/dn889829.aspx)
    

