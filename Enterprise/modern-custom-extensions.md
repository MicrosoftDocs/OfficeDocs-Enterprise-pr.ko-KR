---
title: SharePoint Online 최신 사이트 페이지에서 사용자 지정 확장 최적화
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 03/11/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.reviewer: sstewart
search.appverid:
- MET150
description: SharePoint Online 최신 사이트 페이지에서 사용자 지정 확장 성능을 최적화하는 방법에 대해 알아봅니다.
ms.openlocfilehash: d4e5e492e0573c54f40b1f9e040859037a97965c
ms.sourcegitcommit: a9021ba0800ffc0da21cf2c4da67ab1da2d97099
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "46571171"
---
# <a name="optimize-custom-extension-performance-in-sharepoint-online-modern-site-pages"></a>SharePoint Online 최신 사이트 페이지에서 사용자 지정 확장 성능 최적화

이 문서는 사용자 지정 확장이 사용자가 인식하는 대기 시간에 미치는 영향을 확인하는 방법 및 일반적인 문제를 해결하는 방법을 이해하는데 도움을 줄 것입니다.

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-custom-extensions"></a>SharePoint용 페이지 진단 도구를 사용하여 사용자 지정 확장 분석

SharePoint용 페이지 진단 도구는 새 Microsoft Edge에 대한 브라우저 확장입니다. (SharePoint Online 최신 포털 및 클래식 게시 사이트 페이지를 분석하는 https://www.microsoft.com/edge) 및 Chrome 브라우저) 이 도구는 정의된 성능 기준의 집합 대비 페이지 수행 방식을 보여주는 분석된 각 페이지에 대한 보고서를 제공합니다. Sharepoint용 페이지 진단 도구에 대해 배우고 설치하려면[Sharepoint Online에 페이지 진단 도구 사용](page-diagnostics-for-spo.md)을 참조하세요.

>[!NOTE]
>페이지 진단 도구는 SharePoint Online에서만 사용할 수 있으며 SharePoint 시스템 페이지에서는 사용할 수 없습니다.

Sharepoint용 페이지 진단 도구를 사용하여 Sharepoint 사이트 페이지를 분석하는 경우 **확장이 로드 시간에 영향을 미칩니다** 및/또는 _진단 테스트_ 창의 **너무 많은 확장 ** 결과에서 기준치를 초과하는 사용자 지정 확장에 대한 정보를 확인할 수 있습니다. 

잠정 결과는 다음과 같습니다:

- **주의 필요** (빨간색): 로드하는데 **1**초 보다 긴 시간이 걸리는 모든 _사용자 지정_ 확장 테스트 결과에 표시되는 총 로드 시간은 모듈 로드 및 초기화로 나누어집니다. 또한 페이지에 너무 많은 확장이 있는 경우 페이지 로드 시간에 영향을 줄 수 있으며, **7개** 이상의 확장이 페이지에서 사용되는 경우에는 강조 표시됩니다.
- **개선 기회** (노란색) **5개** 이상의 확장이 사용되는 경우 이 섹션에서 경고로 표시되며 7개가 이상이 사용되면 주의가 필요하다고 ㅍ시됩니다.
- **필요한 작업 없음** (녹색): 로드하는데 1초가 넘게 걸리는 확장이 없습니다.

확장이 페이지 로드 시간에 영향을 미치는 경우 결과는 결과의 **주의 필요** 섹션에 나타납니다. 결과를 클릭하여 느리게 로드되는 확장 또는 너무 많은 확장이 표시된 것에 대한 세부 정보를 확인합니다. 차후 SharePoint 용 페이지 진단 도구를 업데이트는 분석 규칙에 대한 업데이트를 포함할 수 있으므로 항상 최신 버전의 도구를 보유하고 있는지 확인하세요.

![페이지 로드 시간 결과](media/page-diagnostics-for-spo/pagediag-extensions-load-time.png)

결과로 제공되는 정보는 다음을 포함합니다:

- **이름 및 ID**는 페이지에서 확장을 찾는데 도움이 될 수 있는 식별정보를 표시합니다.
- **전체 결과**는 확장이 초기화하고 로드하는 데 걸리는 총 시간을 표시합니다.
- **모듈 로드**는 확장을 가지고 와서 로드하는데 걸리는 시간을 표시합니다.
- **초기화**는 확장이 초기화하는 데 걸리는 시간을 표시합니다.

이 정보는 디자이너 및 개발자가 문제를 해결하는데 도움을 주기 위해 제공됩니다. 이 정보는 디자인 및 개발 팀에 제공해야 합니다.

## <a name="overview-of-extensions"></a>확장 개요

SharePoint Framework (SPFx) 확장은 SharePoint 사용자 환경을 확장하는 데 사용될 수 있습니다. SharePoint Framework 확장을 사용하여 알림 영역, 도구 모음 및 목록 데이터 보기를 포함하여 SharePoint 환경의 여러 패싯을 사용자 지정할 수 있습니다.

확장은 필요한 작업을 수행하기 위해 CPU 및 네트워크 리소스를 사용하기 때문에 SharePoint 페이지의 성능에 좋지 않은 영향을 미칠 수 있습니다.

확장에는 다음과 같은 네 가지 유형이 있습니다.

- **응용 프로그램 사용자 지정자**는 페이지에 스크립트를 추가하고 잘 알려진 HTML 요소 자리 표시자에 액세스하여 사용자 지정 렌더링으로 확장합니다.
- **필드 사용자 지정자**는 목록 내에서 필드에 대한 데이터에 수정된 보기를 제공합니다.
- **명령 집합**은 새 작업을 추가하기 위해 SharePoint 명령 표면을 확장하고 동작을 구현하는 데 사용할 수 있는 클라이언트 쪽 코드를 제공합니다.
- **검색 쿼리 한정자 (미리 보기만)** 는 검색 쿼리를 실행하기 직전에만 호출됩니다.

## <a name="remediate-extension-performance-issues"></a>확장 성능 문제 해결

**확장이 페이지 로드 시간 결과에 영향을 미칩니다**에 나열된 확장의 성능 문제를 식별하고 해결하려면 이 섹션의 지침을 따릅니다.

>[!NOTE]
>응용 프로그램 사용자 지정자는 페이지 수명 주기 동안 초기 단계에서 실행될 수 있으며 페이지의 다른 확장 성능에 영향을 미칠 수 있습니다.

페이지 진단 도구의 감사 결과는 잠재적인 성능 영향을 식별하는 데 도움이 될 수 있도록 확장을 실행하는 두 단계를 표시합니다.

- **모듈 로드**는 확장을 로드하는 데 걸리는 시간으로, 확장 크기에 영향을 받으므로 확장에 필요한 라이브러리를 번들하고 더 밝은 라이브러리를 선택하는 것이 좋습니다.
- **초기화**는 확장의 초기화 시간이며 확장 개발자는 확장이 불필요한 작업을 수행하고 있거나 초기화 단계에서 너무 많은 명령을 실행하고 있지 않는지 고려해야 합니다.

페이지 작성자는 또한 너무 많은 확장은 페이지 성능에 부정적인 영향을 미치기 때문에 감사 결과를 사용하여 페이지가 너무 많은 확장을 가지고 있지 않는지 확인할 수 있습니다.

- **확장 크기 및 종속성**
  - 최적의 정적 리소스 다운로드를 위해서는 Office 365 CDN을 사용해야 합니다. _Js/css_ 파일에는 공개 CDN 출처의 사용을 선호합니다. Office 365 CDN을 사용하는 방법에 대한 자세한 내용은 [SharePoint Online를 활용해 Office 365 Content Delivery Network(CDN) 사용하기](use-office-365-cdn-with-spo.md)를 참조하십시오.
  - SharePoint 프레임워크 (SPFx)의 일부로 제공되는_반응_ 및 _패브릭 가져오기_와 같은 프레임워크를 재사용합니다. 자세한 내용은 [SharePoint 프레임워크 개요](https://docs.microsoft.com/sharepoint/dev/spfx/sharepoint-framework-overview)를 참조하세요.
  - 최신 버전의 SharePoint 프레임워크를 사용하고 있는지 확인하고 새 버전이 가용하게 되면 업그레이드합니다.
- **데이터 페칭/캐싱**
  - 확장에서 표시할 데이터를 가져오기 위해 추가 서버 호출을 사용하는 경우에는 해당 서버 API가 빠르고 클라이언트 쪽 캐싱을 구현하는지 확인합니다. (규모가 큰 집합에는 _localStorage_ 혹은 _IndexDB_의 사용 등)
  - 중요한 데이터를 제공하는데 여러 번의 호출이 필요한 경우 서버에서 일괄 처리를 하거나 요청을 단일 호출로 통합하는 다른 방법을 고려합니다.
  - 또는 일부 데이터 요소에 더 느린 API가 필요하지만 초기 렌더링이 중요하지 않은 경우에는 이를 중요한 데이터가 제공된 후 실행되는 별도의 호출로 분리합니다.
  - 여러 파트에서 같은 데이터를 사용하는 경우에는 공통 데이터 레이어를 활용하여 중복되는 호출을 방지합니다.
- **렌더링 시간**
  - 이미지 및 비디오와 같은 모든 미디어 소스는 컨테이너, 장치 및/또는 네트워크의 제한사항에 맞게 크기가 조정되어 불필요한 대규모 자산이 다운로드되지 않도록 합니다. 콘텐츠 종속성에 대한 자세한 내용은 [SharePoint Online을 활용해 Office 365 Content Delivery Network(CDN) 사용하기](use-office-365-cdn-with-spo.md)를 참조하십시오.
  - 리플로우, 복잡한 CSS 규칙이나 복잡한 애니메이션을 발생시키는 API 호출을 하지 않습니다. 자세한 내용은 [브라우저 리플로우 최소화](https://developers.google.com/speed/docs/insights/browser-reflow)를 참조하세요.
  - 일련의 장기 실행 작업을 사용하지 않습니다. 대신 장기 실행 작업은 개별적 큐로 분리합니다. 자세한 내용은 [JavaScript 실행 최적화](https://developers.google.com/web/fundamentals/performance/rendering/optimize-javascript-execution)를 참조하세요.
  - 프레임의 생략이나 끊김현상을 방지하기 위해 비동기식 렌더링 미디어나 시각적 요소에는 해당 공간을 비축해둡니다. (_jank_로도 알려짐)
  - 특정 브라우저가 렌더링에 사용되는 기능을 지원 하지 않는 경우 polyfill을 로드하거나 종속 코드의 실행을 제외합니다. 기능이 중요하지 않은 경우 메모리 유출을 방지하기 위해 이벤트 핸들러 등의 리소스를 삭제합니다.

성능 문제를 개선하기 위해 페이지를 수정하기 전에 분석 결과에 페이지 로드 시간을 기록해 둡니다. 수정 후에 다시 도구를 실행하여 새 결과가 기준선 표준에 포함되는지 확인하고 새 페이지 로드 시간을 확인하여 개선이 되었는지 확인합니다.

![페이지 로드 시간 결과](media/modern-portal-optimization/pagediag-page-load-time.png)

>[!NOTE]
>페이지 로드 시간은 네트워크 부하, 하루 중 시간 및 기타 일시적인 조건과 같은 다양한 요인에 따라 다를 수 있습니다. 결과의 평균을 내는데 도움이 되도록 수정을 하기 전과 후에 페이지 로드 시간을 몇 번 정도 테스트해야 합니다.

## <a name="related-topics"></a>관련 항목

[SharePoint Online 성능 조정](tune-sharepoint-online-performance.md)

[Office 365 성능 조정](tune-office-365-performance.md)

[최신 SharePoint 환경의 성능](https://docs.microsoft.com/sharepoint/modern-experience-performance)

[콘텐츠 배달 네트워크](content-delivery-networks.md)

[sharepoint Online을 활용해 Office 365 콘텐츠 배달 네트워크(CDN) 사용하기](use-office-365-cdn-with-spo.md)
