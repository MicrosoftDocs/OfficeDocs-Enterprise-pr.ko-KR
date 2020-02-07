---
title: SharePoint Online 용 페이지 진단 도구 사용
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 9/19/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
search.appverid:
- MET150
- SPO160
- MOE150
- BSA160
f1.keywords:
- NOCSH
description: SharePoint 도구에 페이지 진단을 사용 하 여 미리 정의 된 성능 기준 집합에 대해 SharePoint Online 최신 포털 및 클래식 게시 페이지를 분석할 수 있습니다.
ms.openlocfilehash: 57f8aa86b049701c152e8110f64b418d64250981
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841785"
---
# <a name="use-the-page-diagnostics-for-sharepoint-tool"></a>SharePoint 용 페이지 진단 도구 사용

이 문서에서는 **sharepoint 용 페이지 진단 도구** 를 사용 하 여 미리 정의 된 성능 기준 집합에 대해 sharepoint Online 현대 및 클래식 사이트 페이지를 분석 하는 방법에 대해 설명 합니다.  

>[!TIP]
>**도구의 버전 2.0.1이 릴리스 되었습니다**. 버전 **2.0.0** 이상에는 클래식 사이트 페이지 외에도 최신 페이지에 대 한 지원이 포함 됩니다. 사용 중인 도구의 버전을 잘 모를 경우 **정보** 링크 또는 줄임표 (...)를 선택 하 여 버전을 확인할 수 있습니다.

SharePoint 용 페이지 진단 도구는 Chrome 및 [Microsoft Edge 버전 77 이상](https://www.microsoftedgeinsider.com/download?form=MI13E8&OCID=MI13E8) 에서 sharepoint Online 최신 포털 및 클래식 게시 사이트 페이지를 모두 분석 하는 데 사용할 수 있는 브라우저 확장입니다. 이 도구는 SharePoint Online 에서만 작동 하며 SharePoint Server 사이트 페이지에서 사용 하면 오류가 발생 합니다.

이 도구는 분석 된 각 페이지에 대 한 보고서를 생성 하 고, 테스트 결과가 기준 값 외부에 있을 때 해당 페이지에 대 한 자세한 정보를 표시 합니다. SharePoint Online 관리자 및 디자이너는이 도구를 사용 하 여 성능 문제를 해결 하 고, 게시 하기 전에 새 페이지가 최적화 되도록 할 수 있습니다.

페이지 진단 도구는 *allitems.aspx* 또는 *sharepoint .aspx*와 같은 시스템 페이지가 아니라 sharepoint 사이트 페이지만 분석 하도록 디자인 되었습니다. 시스템 페이지 또는 다른 사이트 이외의 페이지에서 도구를 실행 하려고 하면 해당 페이지 유형에 대해 도구를 실행할 수 없다는 오류 메시지가 표시 됩니다.

![SharePoint 페이지에서 실행 해야 합니다.](media/page-diagnostics-for-spo/pagediag-Error-StartPage.png)

라이브러리 또는 시스템 페이지를 평가 하는 데 값이 없으므로 도구에서 오류가 발생 하지 않습니다. 도구를 사용 하려면 SharePoint 사이트 페이지로 이동 하세요. SharePoint 페이지에서이 오류가 발생 하는 경우 마스터 페이지를 확인 하 여 SharePoint metatags 제거 되지 않았는지 확인 하십시오.

도구에 대 한 의견을 제공 하려면 도구의 오른쪽 위 모서리에 있는 줄임표를 선택 하 고 [의견 제공](https://go.microsoft.com/fwlink/?linkid=874109)을 선택 합니다.

![의견 제공](media/page-diagnostics-for-spo/pagediag-feedback.png)
  
## <a name="install-the-page-diagnostics-for-sharepoint-tool"></a>SharePoint 용 페이지 진단 도구 설치

이 섹션의 설치 절차는 Chrome 및 Microsoft Edge 브라우저에서 모두 작동 합니다.

> [!IMPORTANT]
> Microsoft는 SharePoint 용 페이지 진단 도구를 통해 분석 되는 데이터 나 페이지 콘텐츠를 읽지 않으며, 개인 정보, 웹 사이트 또는 다운로드 정보를 캡처하지 않습니다. 도구를 통해 기록 되는 유일한 정보는 테 넌 트 이름, 규칙 수 및 도구를 실행할 때 지원 로깅 옵션을 사용 하도록 설정 했는지 여부입니다. 이 정보는 Microsoft에서 최신 포털 및 게시 사이트 사용 추세 및 일반적인 성능 문제를 이해 하 여 제품 개선을 알리는 데 사용 됩니다.

1. _Chrome_ 또는 _Microsoft Edge 버전 77 이상_ 브라우저를 사용 하 여 도구에 [대 한 링크](https://chrome.google.com/webstore/detail/inahogkhlkbkjkkaleonemeijihmfagi) 를 직접 열거나 [Chrome browser WebStore](https://chrome.google.com/webstore/search/page%20diagnostics%20for%20sharepoint) 에서 검색을 열고 브라우저 확장을 설치 합니다. 스토어의 설명 페이지에서 제공 되는 사용자 개인 정보 보호 정책을 확인 하세요. 브라우저에 도구를 추가할 때 다음과 같은 사용 권한 표시가 나타납니다.

    ![확장 사용 권한](media/page-diagnostics-for-spo/pagediag-add-to-edge.png)

    페이지의 웹 파트 및 사용자 지정 내용에 따라 페이지에 SharePoint 외부 위치의 콘텐츠가 포함 될 수 있기 때문에이 알림 메시지가 표시 됩니다. 즉, 도구는 시작 단추를 클릭 하 고 도구를 실행 하는 활성 SharePoint 탭에 대해서만 요청 및 응답을 읽습니다. 이 **정보는 웹** 브라우저에 의해 로컬로 캡처되고, 도구의 _네트워크 추적_ 탭에 있는 **JSON으로 내보내기** 또는 **HAR로 내보내기** 단추를 통해 사용할 수 있습니다. (이 도구는 [여기](https://go.microsoft.com/fwlink/p/?linkid=857875)에서 액세스할 수 있는 Microsoft 개인 정보 취급 방침을 고려 합니다.)

    _다운로드 관리_ 사용 권한은 도구에서 **JSON으로의 내보내기를** 사용 하는 기능을 포함 합니다. 결과에 Url이 포함 되 고 PII (개인 식별이 가능한 정보)로 분류 될 수 있으므로 조직 외부의 JSON 파일을 공유 하기 전에 회사에서 제공 하는 개인 정보 보호 지침을 따르세요.
1. Incognito 또는 InPrivate 모드에서이 도구를 사용 하려면 브라우저에 대 한 절차를 따르세요.
    1. Microsoft Edge에서 **확장** 으로 이동 하거나 URL 표시줄에 _edge://extensions_ 을 입력 하 고 내선 번호에 대 한 **세부 정보** 를 선택 합니다. 확장 설정에서 **InPrivate에 허용**에 대 한 확인란을 선택 합니다.
    1. Chrome의 경우 **내선** 번호로 이동 하거나 URL 표시줄에 _chrome://extensions_ 을 입력 하 고 내선 번호에 대 한 **세부 정보** 를 선택 합니다. 확장 설정에서 **Incognito에 허용**에 대 한 슬라이더를 선택 합니다.
1. 검토할 SharePoint Online의 SharePoint 사이트 페이지로 이동 합니다. 페이지에 있는 항목의 "지연 로드"가 허용 됩니다. 따라서이 도구는 자동으로 중지 되지 않습니다 (이는 모든 페이지 로드 시나리오에 맞게 디자인 됨). 수집을 중지 하려면 **중지**를 선택 합니다. 데이터 수집을 중지 하기 전에 페이지 로드가 완료 되었는지 확인 하거나 부분 추적만 캡처합니다.
1. 확장 도구 모음 단추를 클릭 합니다. ![SharePoint 로고에 대 한 페이지 진단](media/page-diagnostics-for-spo/pagediag-icon32.png) 도구를 로드 하려면 다음과 같은 확장 팝업 창이 표시 됩니다.

    ![페이지 진단 도구 팝업](media/page-diagnostics-for-spo/pagediag-Landing.png)

**시작** 을 선택 하 여 분석할 데이터 수집을 시작 합니다.

## <a name="what-youll-see-in-the-page-diagnostics-for-sharepoint-tool"></a>SharePoint 용 페이지 진단 도구에 표시 되는 항목

1. 오른쪽 위 모서리에 있는 줄임표 (...)와 같은 **정보** 링크는이 문서에 대 한 링크를 포함 하 여 도구에 대 한 일반적인 지침과 세부 정보를 제공 합니다. 또한 SharePoint 성능 권장 사항에 대 한 직접 링크, 타사 공지 및 도구에 대 한 의견을 제공 하는 옵션이 포함 되어 있습니다.  
1. **상관 관계 ID, SPRequestDuration, SPIISLatency**, **페이지 로드 시간**및 **URL** 세부 정보는 정보 제공 용으로, 몇 가지 용도로 사용할 수 있습니다.

    ![페이지 진단 세부 정보](media/page-diagnostics-for-spo/pagediag-details.PNG)

   - **CorrelationID** 는 Microsoft 지원으로 작업할 때 특정 페이지에 대 한 추가 진단 데이터를 수집할 수 있도록 하는 중요 한 요소입니다.
   - **Sprequestduration** 은 SharePoint에서 페이지를 처리 하는 데 소요 되는 시간입니다. 구조적 탐색, 대규모 이미지, 수많은 API 호출이 더 긴 기간에 기여할 수 있습니다.
   - **SPIISLatency** 는 SharePoint Online에 페이지 로드를 시작 하는 데 걸리는 시간 (밀리초)입니다. 이 값에는 웹 응용 프로그램에서 응답 하는 데 소요 되는 시간이 포함 되지 않습니다.
   - **페이지 로드 시간은** 요청이 요청을 받은 시간부터 브라우저에서 응답을 받아서 렌더링할 때까지 페이지에서 기록한 총 시간입니다. 이 값은 네트워크 대기 시간, 컴퓨터의 성능 및 브라우저가 페이지를 로드 하는 데 걸리는 시간을 비롯 한 다양 한 요인의 영향을 받습니다.
   - **페이지 URL** (Uniform resource Locator)은 현재 페이지의 웹 주소입니다.

1. [**진단 테스트**](#how-to-use-the-diagnostic-tests-tab) 탭에는 세 가지 범주의 분석 결과가 표시 됩니다. **필요한 작업**, **개선 기회** 및 **주의가 필요**하지 않습니다. 각 테스트 결과는 다음 표에 설명 된 대로 이러한 범주 중 하나의 항목으로 표시 됩니다.

    |범주  |색  |설명  |
    |---------|---------|---------|
    |**주의 필요** |빨강 |테스트 결과가 초기 계획 값을 벗어나므로 페이지 성능에 영향을 줍니다. 수정 지침을 따릅니다.|
    |**개선 기회** |노랑 |테스트 결과가 초기 계획 값을 벗어나므로 성능 문제에 영향을 받을 수 있습니다. 테스트 관련 조건이 적용 될 수 있습니다.|
    |**필요한 작업 없음** |친환경 |테스트 결과가 테스트의 초기 계획 값에 포함 됩니다.|

    ![페이지 진단](media/page-diagnostics-for-spo/pagediag-results-general.PNG)

1. [**네트워크 추적**](#how-to-use-the-network-trace-tab) 탭에는 페이지 빌드 요청 및 응답에 대 한 세부 정보가 제공 됩니다.

## <a name="how-to-use-the-diagnostic-tests-tab"></a>진단 테스트 탭을 사용 하는 방법

Sharepoint 용 페이지 진단 도구를 사용 하 여 SharePoint 최신 포털 페이지 또는 클래식 게시 사이트 페이지를 분석할 때 결과는 기준 값에 대 한 결과를 비교 하 여 **진단 테스트** 탭에 표시 되는 미리 정의 된 규칙을 사용 하 여 분석 됩니다.

**개선 영업 기회** 또는 **주의 필수** 범주에 표시 되는 테스트 결과는 권장 되는 방법에 따라 검토 해야 하는 영역을 나타내고 결과에 대 한 추가 정보를 표시 하도록 선택할 수 있습니다. 각 항목에 대 한 자세한 내용은 테스트와 관련 된 지침으로 바로 이동 하는 _자세한_ 정보 링크를 포함 합니다. **없음 작업 필수** 범주에 표시 되는 테스트 결과는 관련 규칙을 준수 하며,이 항목을 선택 하면 추가 세부 정보를 표시 하지 않습니다.

진단 테스트 탭의 정보는 페이지를 디자인 하는 방법을 알려주지 않으며 페이지 성능에 영향을 줄 수 있는 요인을 강조 표시 합니다. 일부 페이지 기능 및 사용자 지정은 페이지 성능에 피할 수 없는 영향을 주므로, 해당 영향이 큰 경우에는 페이지에서의 잠재적 수정 또는 누락을 검토 해야 합니다.

빨간색 또는 노란색 결과를 통해 데이터를 너무 자주 새로 고치는 웹 파트가 표시 될 수도 있습니다. 예를 들어 회사 뉴스는 매 초 마다 업데이트 되지 않지만, 사용자 지정 웹 파트는 전체 사용자 환경을 향상 시킬 수 있는 캐싱 요소를 구현 하는 대신 항상 최신 뉴스를 페치 (fetch) 하기 위해 작성 됩니다. 페이지에 웹 파트를 포함 하는 경우 사용 가능한 각 매개 변수의 값을 평가 하 여 해당 목적에 맞게 적절 하 게 설정 되었는지 확인 하 여 성능 영향을 줄이는 간단한 방법이 있는 경우가 있습니다.

>[!NOTE]
>게시 기능이 사용 되지 않는 클래식 팀 사이트는 CDNs를 사용할 수 없습니다. 이러한 사이트에서 도구를 실행 하면 CDN 테스트가 실패 하 고 무시 될 수 있지만 나머지 테스트는 모두 해당 됩니다. SharePoint 게시 기능의 추가 기능은 페이지 로드 시간을 늘릴 수 있으므로 CDN 기능을 허용 하기 위해 사용 하도록 설정 해서는 안 됩니다.

>[!IMPORTANT]
>테스트 규칙은 정기적으로 추가 및 업데이트 되므로 최신 버전의 도구를 참조 하 여 테스트 결과에 포함 된 특정 정보 및 현재 규칙에 대 한 자세한 내용을 확인 하세요. 확장을 관리 하 여 버전을 확인할 수 있으며, 확장은 업데이트를 사용할 수 있는지 여부를 알려 주어 야 합니다.

## <a name="how-to-use-the-network-trace-tab"></a>네트워크 추적 탭을 사용 하는 방법

**Network Trace (네트워크 추적** ) 탭에는 페이지를 작성 하기 위한 요청과 SharePoint에서 받은 응답에 대 한 자세한 정보가 제공 됩니다.

1. **빨간색으로 플래그가 지정 된 항목 로드 시간을 찾습니다**. 각 요청 및 응답의 성능은 다음과 같이 전체 페이지 성능에 미치는 영향을 기반으로 하 여 색으로 구분 됩니다.
    - 녹색: \< 500ms
    - 노랑: 500-1000ms
    - 빨강: \> 1000ms

    ![네트워크 추적](media/page-diagnostics-for-spo/pagediag-networktrace.png)

    위에 표시 된 이미지에서 빨간색 항목은 기본 페이지와 관련이 있습니다. 페이지가 1000ms (1 초 미만)로 로드 \< 되지 않으면 항상 빨간색으로 표시 됩니다.

2. **항목 로드 시간을 테스트**합니다. 일부 경우에는 항목이 이미 브라우저에 의해 캐시 되었기 때문에 시간 또는 색 지표가 나타나지 않을 수 있습니다. 이를 올바르게 테스트 하려면 페이지를 열고 브라우저 캐시를 지운 다음 **시작** 을 클릭 하 여 "콜드" 페이지를 로드 하 고 초기 페이지 로드를 true로 반사 해야 합니다. 이 경우 페이지에 캐시 되는 항목을 확인 하는 데 도움이 되는 것 처럼 "웜" 페이지 로드와 비교 해야 합니다.

3. **문제를 조사 하는 데 도움이 되는 다른 사용자와 관련 세부 정보를 공유**합니다. 도구에서 제공 하는 세부 정보 또는 정보를 개발자나 기술 지원 담당자와 공유 하려면 위의 이미지에 표시 된 **JSON으로 내보내기를** 클릭 합니다. 이를 통해 결과를 다운로드할 수 있으며,이를 통해 JSON 파일 뷰어가 표시 됩니다.

    미리 보기 기능을 사용 하 여 *HAR로 내보내기를* 사용 하도록 설정한 경우 내보내기 유형이 **HAR에 내보내기**로 표시 됩니다.

    ![네트워크 추적](media/page-diagnostics-for-spo/pagediag-NetworkTraceHAR.PNG)

> [!IMPORTANT]
> 이러한 결과에는 Url이 포함 되며 PII (개인 식별이 가능한 정보)로 분류 될 수 있습니다. 해당 정보를 배포 하기 전에 조직의 지침을 따라야 합니다.

## <a name="engaging-with-microsoft-support"></a>Microsoft 지원 제공

지원 사례를 직접 사용 하는 경우에만 사용할 수 있는 **Microsoft 지원 수준 기능이** 포함 되어 있습니다. 이 기능을 사용 하면 팀 참여를 지원 하지 않고을 사용할 때 도움이 되지 않으며 페이지 속도를 크게 높일 수 있습니다. 추가 정보가 서비스의 로깅에 추가 될 때 도구에서이 기능을 사용 하는 경우 추가 정보가 제공 되지 않습니다.

변경 내용이 표시 되지 않으며, 사용 하도록 설정 하 고 페이지 성능이 사용 하도록 설정 된 경우에는 2-3 배 더 느린 성능 보다 성능이 크게 저하 된다는 점을 제외 하 고는 아무런 변화가 없습니다. 특정 페이지와 해당 활성 세션에만 해당 됩니다. 따라서이는 실제로 지원 서비스를 받을 때에만 사용 해야 합니다.

### <a name="to-enable-the-microsoft-support-level-feature"></a>Microsoft 지원 수준 기능을 사용 하도록 설정 하려면

1. SharePoint 용 페이지 진단 도구를 엽니다.
2. 키보드에서 ALT + e- **L**을 누릅니다. 그러면 **지원 로깅 사용** 확인란이 표시 됩니다.
3. 확인란을 선택한 다음 **시작** 을 클릭 하 여 페이지를 다시 로드 하 고 자세한 정보 표시 로깅을 생성 합니다.

    ![지원 옵션 사용](media/page-diagnostics-for-spo/pagediag-support.png)
  
    상관 관계 (도구 맨 위에 표시 됨)를 확인 하 고 지원 담당자에 게 진단 세션에 대 한 추가 정보를 수집할 수 있도록 제공 합니다.

## <a name="related-topics"></a>관련 항목

[SharePoint Online 성능 조정](tune-sharepoint-online-performance.md)

[Office 365 성능 조정](tune-office-365-performance.md)

[콘텐츠 배달 네트워크](content-delivery-networks.md)
