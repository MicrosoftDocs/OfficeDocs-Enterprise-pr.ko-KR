---
title: SharePoint Online에 대한 탐색 옵션
ms.author: krowley
author: kccross
manager: laurawi
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: adb92b80-b342-4ecb-99a1-da2a2b4782eb
description: 이 문서에서는 SharePoint 게시 SharePoint Online에서 사용할 수 있는 탐색 옵션 사이트를 설명 합니다. 선택 및 구성 탐색의 성능 및 SharePoint Online에서 사이트의 확장성에 영향을 현저 하 게 됩니다.
ms.openlocfilehash: 5a190ca643c20b6644ca1eecdac2a4a2e281a09e
ms.sourcegitcommit: 45633b7034ee98d0cd833db9743f283b638237f4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/16/2018
ms.locfileid: "26547180"
---
# <a name="navigation-options-for-sharepoint-online"></a>SharePoint Online에 대한 탐색 옵션

이 문서에서는 SharePoint 게시 SharePoint Online에서 사용할 수 있는 탐색 옵션 사이트를 설명 합니다. 선택 및 구성 탐색의 성능 및 SharePoint Online에서 사이트의 확장성에 영향을 현저 하 게 됩니다.

## <a name="overview"></a>개요

탐색 공급자 구성 전체 사이트에 대 한 성능에 영향을 줄 크게 수 및 탐색 공급자 및 SharePoint 사이트의 요구 사항에 대 한 효과적으로 확장할 수 있는 구성 선택 하려면 신중 하 게 고려를 수행 해야 합니다. 사용자 지정 탐색 구현을 뿐아니라 두의 기본 탐색 공급자 있습니다.

첫번째 옵션 [**(메타 데이터) 관리 되는 탐색**](#using-managed-navigation-and-metadata-in-sharepoint-online)것이 좋으며, SharePoint Online에서 기본 옵션 중 하나입니다. 그러나 보안 조정 필요 하지 않은 경우 사용할 수 없도록 하는 것이 좋습니다. 이 탐색 공급자 간의 보안 기본 설정으로 상태가 보안 조정 그러나 대부분의 사이트 탐색 요소를 자주 사이트의 모든 사용자에 대해 일관성는 이후 보안 조정의 오버 헤드를 필요 하지 않습니다. 보안 조정을 사용 하지 않으려면 권장 구성과이 탐색 공급자 사이트 구조를 열거 하는 것 필요 하지 않은 이며 적절 한 성능 영향을 주는 뛰어납니다.

두번째 옵션, [**구조적 탐색**](#using-structural-navigation-in-sharepoint-online) **하지 SharePoint Online에서 권장된 탐색 옵션입니다**. 이 탐색 공급자는 온-프레미스 토폴로지를 제한적으로 SharePoint Online에서 지원에 대 한 설계 되었습니다. 일부 추가 집합의 다른 탐색 옵션 비교 기능을 제공 하는 동시에 보안 조정 및 사이트 구조 열거형을 포함 하 여 이러한 기능을 사용 하는 경우 과도 한 서버 통화 및 영향 확장성 및 성능 비용에 가져옵니다. 과도 한 리소스를 사용 하는 사이트 structed 탐색을 사용 하 여 제한에 따라 달라 집니다 수 있습니다.

다 수의 고객의 기본 탐색 공급자 외에도 대체 사용자 지정 탐색 구현을 성공적으로 구현 했습니다. 탐색 노드의 로컬 캐시를 저장 하는 클라이언트 렌더링 된 디자인 패턴 채택 하는 사용자 지정 탐색 구현의 일반적인 클래스 중 하나입니다. ( **[검색 기반 클라이언트쪽 스크립팅](#using-search-driven-client-side-scripting)** 이 문서에서 참조 합니다.)

이러한 탐색 공급자가 메시지를 몇 주요 장점: 
- 일반적으로 응답 페이지 디자인을 제대로 작동 합니다.
- 매우 확장성 및 성능이 자신이 못할 수 있기 때문에 자원 비용 (없고 시간이 초과 후 백그라운드에서 새로고침). 
- 이러한 탐색 공급자는 단순한 정적 구성에서 다양 한 동적 데이터 공급자에 이르기까지 다양 한 전략을 사용 하 여 탐색 데이터를 검색할 수 있습니다. 

데이터 공급자의 예로는 **검색 기반 탐색**, 탐색 노드를 열거 하 고 효율적으로 조정 하는 보안 처리에 대 한 유연성을 허용 하는 사용 하는 것입니다. 

**사용자 정의 탐색 공급자**작성 인기 있는 다른 옵션이 있습니다. 사용자 정의 탐색 공급자 만들기 (영문)에 대 한 추가 지침에 대 한 [SharePoint 온라인 포털에 대 한 탐색 솔루션](https://docs.microsoft.com/sharepoint/dev/solution-guidance/portal-navigation) 을 검토 하십시오.
  
## <a name="pros-and-cons-of-sharepoint-online-navigation-options"></a>전문가 및 SharePoint Online의 단점 탐색 옵션

다음 표에 각 옵션의 장단점이 있습니다. 


|관리 탐색  |구조적 탐색  |검색 기반 탐색  |사용자 정의 탐색 공급자  |
|---------|---------|---------|---------|
|장점:<br/><br/>쉬운 유지 관리<br/>권장 되는 옵션<br/>     |장점:<br/><br/>쉬운 구성<br/>보안 조정이 적용<br/>콘텐츠 추가 됨에 따라 자동으로 업데이트<br/>|장점:<br/><br/>보안 조정이 적용<br/>사이트를 추가할 때 자동으로 업데이트<br/>빠른 로드 시간 및 로컬로 캐시된 탐색 구조<br/>|장점:<br/><br/>사용 가능한 옵션에 더 넓은 선택<br/>Fast 캐싱 때 로드 되는 올바르게<br/>다양 한 옵션 응답 페이지 디자인 잘 작동<br/>|
|단점:<br/><br/>사이트 구조를 반영하도록 자동으로 업데이트되지 않음<br/>보안 조정을 사용 하도록 설정 하는 경우 성능에 미치는<br/>|단점:<br/><br/>**권장하지 않음**<br/>**영향을 미치는 성능 및 확장성**<br/>**제한 적용**<br/>|단점:<br/><br/>사이트를 쉽게 정렬하는 기능이 없음<br/>마스터 페이지의 사용자 지정 필요(기술 필요)<br/>|단점:<br/><br/>사용자 지정 개발이 필요<br/>외부 데이터 원본을 저장 캐시 필요한 / 예: Azure<br/>|

사이트에 대 한 가장 적절 한 옵션에는 사이트 요구 사항 및 기술 사용자 기능에 따라 달라 집니다. 확장 가능한의 기본 탐색 공급자를 사용할 경우 사용 하지 않도록 설정 하는 보안 조정을 사용 하 여 관리 되는 탐색 매우 유용한 옵션입니다. 

관리 되는 탐색 옵션을 통해 유지할 수 구성, 코드 사용자 지정 파일을 포함 하지 않는 한 구조적 탐색 보다 훨씬 빠릅니다. 보안 조정 필요 및 사용자 지정 마스터 페이지를 사용 하 여 능숙 하 게은 SharePoint Online에 대 한 기본 마스터 페이지에서 발생할 수 있는 변경 내용을 유지 관리 하기 위해 조직에서 일부 기능이 있어야 하는 경우 다음 검색을 통해 구동 옵션 생성 될 수 있습니다를 좋음 사용자 경험 합니다. 보다 복잡 한 요구 사항에 있는 사용자 지정 탐색 공급자에서 올바른 선택을 수 있습니다. 구조적 탐색 권장 되지 않습니다.

마지막으로 추가 탐색 공급자 및 기능 보다 플랫된 사이트 계층 구조 및 SharePoint 허브 사이트를 사용 하 여 허브 및 스포크 모델을 활용 하는 현대 SharePoint 사이트 아키텍처에 대 한 SharePoint를 추가 하는 것이 중요 합니다. 이 통해 다양 한 시나리오를 구현할 수 필요가 없는 경우 SharePoint 게시 기능을 사용 하 고 이러한 탐색 구성은 확장성과 SharePoint Online 내 대기 시간에 대해 최적화 된 키를 누릅니다. 볼록한 구조를 SharePoint 게시 사이트의 전체 구조를 단순화 하는 동일한 원칙-적용 자주 전반적인 쿼리 성능을 높일 기록한도 확장 합니다. 이 것을 의미는 수백 개의 사이트 (하위 웹)와 단일 사이트 모음을 대신 더 나은 방법은 거의 하위 사이트 (하위 웹) 포함 하는 여러 사이트 모음을 합니다.


## <a name="using-managed-navigation-and-metadata-in-sharepoint-online"></a>SharePoint Online에서 관리 되는 탐색 및 메타 데이터를 사용 하 여

관리 되는 탐색은 대부분의 구조적 탐색와 동일한 기능을 다시 사용할 수 있는 다른의 기본 옵션입니다. 보안 조정 사용 하거나 사용 하지 않도록 설정 하려면 관리 되는 메타 데이터를 구성할 수 있습니다. 사용 하지 않도록 설정 하는 보안 조정을 구성 하는 경우 서버 통화 상수 번호와 함께 모든 탐색 링크를 로드 하는 것 처럼 관리 되는 탐색이 매우 효율적입니다. 그러나 관리 되는 탐색의 장점 중 일부를 부정 보안 조정 사용 하도록 설정 하 고 고객 최적의 성능 및 확장성에 대 한 사용자 지정 탐색 솔루션 중 하나를 탐색 하도록 선택할 수 있습니다.

대부분의 사이트의 탐색 구조는 사이트의 모든 사용자에 대해 일관성 종종으로 보안 조정을 필요 하지 않습니다. 보안 조정을 사용 하지 않으면 모든 사용자가 액세스할 수 있는 탐색 링크가 추가 하는 경우 링크에는 여전히 표시 되지만 액세스 거부 메시지가 하 게 될 합니다. 콘텐츠를 실수로 액세스의 위험은 없습니다.

### <a name="how-to-implement-managed-navigation-and-the-results"></a>관리 탐색 및 결과의 구현 방법

여러 문서에는 Docs.Microsoft.com 관리 되는 탐색의 세부 정보에 대 한 예 [SharePoint Server의 관리 탐색 개요 (영문)를](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation)참조 하십시오.

관리 되는 탐색을 구현 하기 위해 설정한 용어 Url이 포함 된 사이트의 탐색 구조에 해당 합니다. 관리 되는 탐색 대부분의 경우에서 구조적 탐색을 바꾸려면 수동으로 curated도 수 있습니다. 예를 들어:

![SharePoint Online 사이트 구조](media/SPONavOptionsListOfSites.png)

아래 예에서는 관리 탐색을 사용한 경우의 복잡한 탐색의 성능을 보여 줍니다.

![관리 되는 탐색을 사용 하 여 복잡 한 탐색의 성능](media/SPONavOptionsComplexNavPerf.png)

지속적으로 관리 되는 탐색을 사용 하 여 구조적 탐색 접근 방식에 비해 성능이 향상 됩니다.
  
## <a name="using-structural-navigation-in-sharepoint-online"></a>SharePoint Online에서 구조적 탐색 사용

이것은 기본적으로 사용의 기본 탐색 하 고는 가장 간단한 솔루션 했으나 이와 같이 비용이 많이 드는 성능이 떨어질 있습니다. 모든 사용자 지정이 필요 하지 않습니다 및 비 기술적인 사용자 수도 쉽게 항목을 추가, 항목을 숨기려면 설정 페이지에서 탐색을 관리 합니다. 그러나도 쉽게 관리 하 고 수와 제어 하는 true 되므로으로 관리 되는 탐색을 사용 하는 것이 좋습니다. 관리 되는 탐색에 대 한 향상 된 성능입니다.

![선택한 표시 하위 사이트를 사용 하 여 구조적 탐색](media/SPONavOptionsStructuredShowSubsites.png)
  
### <a name="turning-on-structural-navigation-in-sharepoint-online"></a>SharePoint Online에서 구조적 탐색 설정

구조적 탐색 하 고 표시 된 표준 SharePoint Online 솔루션에서 성능 옵션을 하위 하는 방법을 설명 하기 위해 설정 합니다. 다음은 **사이트 설정** 페이지에서 찾은 설정 스크린샷 \> **탐색**합니다.
  
![하위 사이트를 보여 주는 스크린샷](media/5b6a8841-34ed-4f61-b6d3-9d3e78d393e7.png)
  
### <a name="analyzing-structural-navigation-performance-in-sharepoint-online"></a>SharePoint Online의 구조적 탐색 성능 분석

SharePoint 페이지의 성능 분석, Internet Explorer에서 F12 개발자 도구에 있는 **네트워크** 탭을 사용 합니다. 
  
![F12 개발자 도구 네트워크 탭을 보여 주는 스크린샷](media/SPONavOptionsNetworks.png)
  
1. **네트워크** 탭에서 로드할 .aspx 페이지와 **세부 정보** 탭을 차례로 클릭합니다.<br/> ![세부 정보 탭을 보여 주는 스크린샷](media/ad85cefb-7bc5-4932-b29c-25f61b4ceeb2.png)<br/>
2. **응답 헤더**를 클릭합니다. <br/>![세부 정보 탭의 스크린샷](media/c47770ac-5b2b-4941-9830-c57565dec4cc.png)<br/>SharePoint 응답 헤더에 유용한 진단 정보를 반환합니다. 
3. **SPRequestDuration** 요청 되는데 걸린 시간 서버에서 프로세스의 밀리초에서 값은 정보의 가장 유용한 항목 중 하나입니다. 다음 스크린샷에 **표시 하위** 선택 되지 않습니다 구조적 탐색에 대 한. 전역 탐색에서 사이트 모음 링크는 것을 의미 합니다.<br/>![부하 시간을 요청 기간으로 나타내는 스크린샷](media/3422b2e8-15ec-4bb9-ba86-0965b6b49b01.png)<br/>
4. **SPRequestDuration** 키 245 시간 (밀리초)의 값을 갖습니다. 요청을 반환 하는데 걸린 시간을 나타냅니다. 사이트 탐색 항목을 하나만 이므로 SharePoint Online 수행 되는 방법을 굵은 탐색 하지 않고에 대 한 좋은 벤치 마크입니다. 다음 스크린샷은 추가 (영문)의 하위 사이트에서이 키에 주는 영향을 보여줍니다.<br/>![2502ms의 요청 기간을 나타내는 스크린샷](media/618ee4e9-2ffa-4a22-b638-fa77b72292b8.png)<br/>
  
하위 사이트 추가 (영문)이 비교적 간단 샘플 사이트에 대 한 페이지 요청을 반환 하는데 걸리는 시간을 크게 증가 했습니다. 복잡 한 사이트 계층 구조, 탐색 영역에서 페이지 및 기타 구성 및 토폴로지 옵션을 포함 하 여에이 영향을 더욱 크게 향상 시킬 수 있습니다.

## <a name="using-search-driven-client-side-scripting"></a>검색 기반 클라이언트 쪽 스크립팅 사용

검색을 사용 하는 연속 크롤링을 사용 하 여 백그라운드에서 제작 하는 인덱스를 활용할 수 있습니다. 검색 인덱스에서 검색 결과 가져오는 및 결과 보안 조정이 적용 됩니다. 보안 조정 필요할 때 일반적으로의 기본 탐색 공급자 보다 더 빠릅니다입니다. 구조적 탐색에 대 한 검색을 사용 하는 복잡 한 사이트 구조를 포함 하는 경우에 특히 더 빠르게 처리할 페이지 로드 시간이 훨씬 합니다. 관리 되는 탐색을 통해이의 주요 이점은 보안 조정에서 이점이 있습니다.

이 방법은 사용자 지정 마스터 페이지를 만들고 사용자 지정 HTML의 기본 탐색 코드 바꿉니다 수 있습니다. 파일에서 탐색 코드를 교체 하려면 다음 예제에 설명 된이 절차에 따라 `seattle.html`합니다. 하면이 예제에서는 열립니다는 `seattle.html` 파일 및 전체 요소 `id=”DeltaTopNavigation”` 사용자 지정 HTML 코드를 사용 합니다.

### <a name="example-replace-the-out-of-the-box-navigation-code-in-a-master-page"></a>예: 마스터 페이지에서의 기본 탐색 코드를 대체 합니다.

1.  사이트 설정 페이지로 이동합니다.
2.  **마스터 페이지**를 클릭하여 마스터 페이지 갤러리를 엽니다.
3.  여기에서 라이브러리를 통해 이동 및 파일을 다운로드할 수 있는 `seattle.master`합니다.
4.  텍스트 편집기를 사용하여 코드를 편집하고 아래의 스크린샷과 같이 코드 블록을 삭제합니다.<br/>![표시 된 코드 블록을 삭제 합니다.](media/SPONavOptionsDeleteCodeBlock.png)<br/>
5. 사이 코드를 제거는 `<SharePoint:AjaxDelta id=”DeltaTopNavigation”>` 및 `<\SharePoint:AjaxDelta>` 태그를 지정 하 고 다음 코드 조각으로 대체 합니다.<br/>

```
<div id="loading">
  <!--Replace with path to loading image.-->
  <div style="background-image: url(''); height: 22px; width: 22px; ">
  </div>
</div>
<!-- Main Content-->
<div id="navContainer" style="display:none">
    <div data-bind="foreach: hierarchy" class="noindex ms-core-listMenu-horizontalBox">
        <a class="dynamic menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">
            <span class="menu-item-text" data-bind="text: item.Title">
            </span>
        </a>
        <ul id="menu" data-bind="foreach: $data.children" style="padding-left:20px">
            <li class="static dynamic-children level1">
                <a class="static dynamic-children menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">
               
                 <!-- ko if: children.length > 0-->
                    <span aria-haspopup="true" class="additional-background ms-navedit-flyoutArrow dynamic-children">
                        <span class="menu-item-text" data-bind="text: item.Title">
                        </span>
                    </span>
                <!-- /ko -->
                <!-- ko if: children.length == 0-->   
                    <span aria-haspopup="true" class="ms-navedit-flyoutArrow dynamic-children">
                        <span class="menu-item-text" data-bind="text: item.Title">
                        </span>
                    </span>
                <!-- /ko -->   
                </a>
               
                <!-- ko if: children.length > 0-->                                                       
                <ul id="menu"  data-bind="foreach: children;" class="dynamic  level2" >
                    <li class="dynamic level2">
                        <a class="dynamic menu-item ms-core-listMenu-item ms-displayInline  ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">
         
          <!-- ko if: children.length > 0-->
          <span aria-haspopup="true" class="additional-background ms-navedit-flyoutArrow dynamic-children">
           <span class="menu-item-text" data-bind="text: item.Title">
           </span>
          </span>
           <!-- /ko -->
          <!-- ko if: children.length == 0-->
          <span aria-haspopup="true" class="ms-navedit-flyoutArrow dynamic-children">
           <span class="menu-item-text" data-bind="text: item.Title">
           </span>
          </span>                 
          <!-- /ko -->   
                        </a>
          <!-- ko if: children.length > 0-->
         <ul id="menu" data-bind="foreach: children;" class="dynamic level3" >
          <li class="dynamic level3">
           <a class="dynamic menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">
            <span class="menu-item-text" data-bind="text: item.Title">
            </span>
           </a>
          </li>
         </ul>
           <!-- /ko -->
                    </li>
                </ul>
                <!-- /ko -->
            </li>
        </ul>
    </div>
</div>
```
<br/>
6. 대체 URL을 로드 하는 사이트 모음에 로드 이미지에 대 한 링크와 시작 부분에 앵커 태그 이미지입니다. 변경 된 내용을 변경한 파일 이름을 바꾼 다음 마스터 페이지 갤러리에 업로드 합니다. 새.master 파일을 생성 합니다.<br/>
7. 이 HTML은 JavaScript 코드에서 반환 하는 검색 결과에서 채울 하는 기본 태그입니다. Var 루트에 대 한 값을 변경 하는 코드 편집 해야하는 다음 코드 조각에서 볼 수 있듯이 "사이트 모음 URL" =:<br/>

```
var root = “https://spperformance.sharepoint.com/sites/NavigationBySearch”;
```
<br/>
8. 결과 self.nodes 배열에 할당 된 및 배열 self.hierarchy에 출력을 할당 하는 linq.js를 사용 하 여 개체에서 계층 구조를 작성 합니다. 이 배열에는 HTML에 바인딩된 개체입니다. 이 작업은 toggleView() 함수에서 ko.applyBinding() 함수에는 자체 개체를 전달 하 여 수행 됩니다.<br/>그런 다음이 위치를 선택 하면 계층 구조 배열의 다음 HTML에 바인딩할 수 있습니다:<br/>

```
<div data-bind=”foreach: hierarchy” class=”noindex ms-core-listMenu-horizontalBox”>
```

에 대 한 이벤트 처리기 `mouseenter` 및 `mouseexit` 에서 작업을 수행 하는 하위 사이트 드롭다운 메뉴를 처리할 수 있는 최상위 탐색 모음에 추가 되는 `addEventsToElements()` 함수입니다.

복잡 한 탐색이 예제에서는 새 페이지는 관리 되는 탐색 방식으로 비슷한 결과 얻을 수 벤치 마크 구조적 탐색에서 서버에 소요 된 시간 줄이기 된 로컬 캐싱 표시 하지 않고 로드 합니다.

### <a name="about-the-javascript-file"></a>JavaScript 파일에 대 한...

전체 JavaScript 파일은 다음과 같습니다.

```
//Models and Namespaces
var SPOCustom = SPOCustom || {};
SPOCustom.Models = SPOCustom.Models || {}
SPOCustom.Models.NavigationNode = function () {

    this.Url = ko.observable("");
    this.Title = ko.observable("");
    this.Parent = ko.observable("");

};

var root = "https://spperformance.sharepoint.com/sites/NavigationBySearch";
var baseUrl = root + "/_api/search/query?querytext=";
var query = baseUrl + "'contentClass=\"STS_Web\"+path:" + root + "'&trimduplicates=false&rowlimit=300";

var baseRequest = {
    url: "",
    type: ""
};


//Parses a local object from JSON search result.
function getNavigationFromDto(dto) {
    var item = new SPOCustom.Models.NavigationNode();
    if (dto != undefined) {

        var webTemplate = getSearchResultsValue(dto.Cells.results, 'WebTemplate');

        if (webTemplate != "APP") {
            item.Title(getSearchResultsValue(dto.Cells.results, 'Title')); //Key = Title
            item.Url(getSearchResultsValue(dto.Cells.results, 'Path')); //Key = Path
            item.Parent(getSearchResultsValue(dto.Cells.results, 'ParentLink')); //Key = ParentLink
        }

    }
    return item;
}

function getSearchResultsValue(results, key) {

    for (i = 0; i < results.length; i++) {
        if (results[i].Key == key) {
            return results[i].Value;
        }
    }
    return null;
}

//Parse a local object from the serialized cache.
function getNavigationFromCache(dto) {
    var item = new SPOCustom.Models.NavigationNode();

    if (dto != undefined) {

        item.Title(dto.Title);
        item.Url(dto.Url);
        item.Parent(dto.Parent);
    }

    return item;
}

/* create a new OData request for JSON response */
function getRequest(endpoint) {
    var request = baseRequest;
    request.type = "GET";
    request.url = endpoint;
    request.headers = { ACCEPT: "application/json;odata=verbose" };
    return request;
};

/* Navigation Module*/
function NavigationViewModel() {
    "use strict";
    var self = this;
    self.nodes = ko.observableArray([]);
    self.hierarchy = ko.observableArray([]);;
    self.loadNavigatioNodes = function () {
        //Check local storage for cached navigation datasource.
        var fromStorage = localStorage["nodesCache"];
        if (false) {
            var cachedNodes = JSON.parse(localStorage["nodesCache"]);

            if (cachedNodes && timeStamp) {
                //Check for cache expiration. Currently set to 3 hrs.
                var now = new Date();
                var diff = now.getTime() - timeStamp;
                if (Math.round(diff / (1000 * 60 * 60)) < 3) {

                    //return from cache.
                    var cacheResults = [];
                    $.each(cachedNodes, function (i, item) {
                        var nodeitem = getNavigationFromCache(item, true);
                        cacheResults.push(nodeitem);
                    });

                    self.buildHierarchy(cacheResults);
                    self.toggleView();
                    addEventsToElements();
                    return;
                }
            }
        }
        //No cache hit, REST call required.
        self.queryRemoteInterface();
    };

    //Executes a REST call and builds the navigation hierarchy.
    self.queryRemoteInterface = function () {
        var oDataRequest = getRequest(query);
        $.ajax(oDataRequest).done(function (data) {
            var results = [];
            $.each(data.d.query.PrimaryQueryResult.RelevantResults.Table.Rows.results, function (i, item) {

                if (i == 0) {
                    //Add root element.
                    var rootItem = new SPOCustom.Models.NavigationNode();
                    rootItem.Title("Root");
                    rootItem.Url(root);
                    rootItem.Parent(null);
                    results.push(rootItem);
                }
                var navItem = getNavigationFromDto(item);
                results.push(navItem);
            });
            //Add to local cache
            localStorage["nodesCache"] = ko.toJSON(results);

            localStorage["nodesCachedAt"] = new Date().getTime();
            self.nodes(results);
            if (self.nodes().length > 0) {
                var unsortedArray = self.nodes();
                var sortedArray = unsortedArray.sort(self.sortObjectsInArray);

                self.buildHierarchy(sortedArray);
                self.toggleView();
                addEventsToElements();
            }
        }).fail(function () {
            //Handle error here!!
            $("#loading").hide();
            $("#error").show();
        });
    };
    self.toggleView = function () {
        var navContainer = document.getElementById("navContainer");
        ko.applyBindings(self, navContainer);
        $("#loading").hide();
        $("#navContainer").show();

    };
    //Uses linq.js to build the navigation tree.
    self.buildHierarchy = function (enumerable) {
        self.hierarchy(Enumerable.From(enumerable).ByHierarchy(function (d) {
            return d.Parent() == null;
        }, function (parent, child) {
            if (parent.Url() == null || child.Parent() == null)
                return false;
            return parent.Url().toUpperCase() == child.Parent().toUpperCase();
        }).ToArray());

        self.sortChildren(self.hierarchy()[0]);
    };


    self.sortChildren = function (parent) {

        // sjip processing if no children
        if (!parent || !parent.children || parent.children.length === 0) {
            return;
        }

        parent.children = parent.children.sort(self.sortObjectsInArray2);

        for (var i = 0; i < parent.children.length; i++) {
            var elem = parent.children[i];

            if (elem.children && elem.children.length > 0) {
                self.sortChildren(elem);
            }
        }
    };

    // ByHierarchy method breaks the sorting in chrome and firefix 
    // we need to resort  as ascending
    self.sortObjectsInArray2 = function (a, b) {
        if (a.item.Title() > b.item.Title())
            return 1;
        if (a.item.Title() < b.item.Title())
            return -1;
        return 0;
    };


    self.sortObjectsInArray = function (a, b) {
        if (a.Title() > b.Title())
            return -1;
        if (a.Title() < b.Title())
            return 1;
        return 0;
    }
}

//Loads the navigation on load and binds the event handlers for mouse interaction.
function InitCustomNav() {
    var viewModel = new NavigationViewModel();
    viewModel.loadNavigatioNodes();
}

function addEventsToElements() {
    //events.
      $("li.level1").mouseover(function () {
          var position = $(this).position();
          $(this).find("ul.level2").css({ width: 100, left: position.left + 10, top: 50 });
      })
   .mouseout(function () {
     $(this).find("ul.level2").css({  left: -99999, top: 0 });
   
    });
   
     $("li.level2").mouseover(function () {
          var position = $(this).position();
          console.log(JSON.stringify(position));
          $(this).find("ul.level3").css({ width: 100, left: position.left + 95, top:  position.top});
      })
   .mouseout(function () {
     $(this).find("ul.level3").css({  left: -99999, top: 0 });
    });
} _spBodyOnLoadFunctionNames.push("InitCustomNav");

``` 

위에 표시 된 코드를 요약 하는 `jQuery $(document).ready` 방법이 함수는 `viewModel object` 만든 다음는 `loadNavigationNodes()` 해당 개체에 대해 함수를 호출 합니다. 이 함수는 클라이언트 브라우저의 HTML5 로컬 저장소에 저장 된 이전에 작성된 된 탐색 계층 구조를 로드 하는 중 하나 또는 함수를 호출 하 `queryRemoteInterface()`합니다.

`QueryRemoteInterface()`사용 하 여 요청을 작성은 `getRequest()` 함수는 쿼리 매개 변수와 함께 스크립트 앞부분에서 정의한 하 고 다음 서버에서 데이터를 반환 합니다. 이 데이터는 기본적으로 다양 한 속성으로 표시 되는 데이터 전송 개체로 표현 하는 사이트 모음에 있는 모든 사이트의 배열입니다. 

이 데이터는 다음 구문 분석 되는 이전에 정의 된으로 `SPO.Models.NavigationNode` 개체를 사용 하는 `Knockout.js` 데이터 이전에 정의한 하는 HTML로 값 바인딩 (영문)에서 사용 하기 위해 눈에 띄는 속성을 만들 수 있습니다. 

그런 다음 개체는 결과 배열에 배치 됩니다. 이 배열은 녹아웃을 사용 하 여 JSON으로 구문 분석 되 고 이후 페이지 로드에서 성능 향상된을 위해 로컬 브라우저 저장소에 저장 합니다.

### <a name="benefits-of-this-approach"></a>이 방법을 사용의 이점

[이 방법](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page) 의 주요 이점 중 하나는 HTML5 로컬 저장소를 사용 하 여 탐색 저장 되어 로컬로 사용자에 대 한 다음에 페이지를 로드 합니다. 검색 API를 사용 하 여 구조적 탐색;에 대 한 주요 성능 향상을 얻게 그러나 일부 기술 기능을 실행 하 고이 기능을 사용자 지정을 걸립니다. 

[구현 하는 예제](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page)사이트의 기본 구조적 탐색;와 동일한 방식으로 정렬 됩니다. 사전순으로 보여줍니다. 이 순서에서 파생 하는 하고자 하는 경우는 것이 더 복잡 하 고 유지 관리, 개발 합니다. 또한이 방법을 사용을 사용 하면 지원 되는 마스터 페이지에서 파생 하는으로 해야 합니다. 사용자 지정 마스터 페이지, 유지 하지 않는 경우 사이트를에 업데이트 및 마스터 페이지를 Microsoft에 게 하는 향상 된 기능입니다.

[위의 코드는](#about-the-javascript-file) 다음과 같은 종속성에 있습니다.

- jQuery-http://jquery.com/
- KnockoutJS-http://knockoutjs.com/
- Linq.js- http://linqjs.codeplex.com/, 또는 github.com/neuecc/linq.js

LinqJS의 현재 버전 위의 코드에 사용 되는 ByHierarchy 메서드를 포함 하지 않는 및 탐색 코드의 연결이 끊어집니다. 이 문제를 해결 하려면 다음 메서드를 줄 앞 Linq.js 파일에 추가 `Flatten: function ()`합니다.

```
ByHierarchy: function(firstLevel, connectBy, orderBy, ascending, parent) {
     ascending = ascending == undefined ? true : ascending;
     var orderMethod = ascending == true ? 'OrderBy' : 'OrderByDescending';
     var source = this;
     firstLevel = Utils.CreateLambda(firstLevel);
     connectBy = Utils.CreateLambda(connectBy);
     orderBy = Utils.CreateLambda(orderBy);
    
     //Initiate or increase level
     var level = parent === undefined ? 1 : parent.level + 1;

    return new Enumerable(function() {
         var enumerator;
         var index = 0;

        var createLevel = function() {
                 var obj = {
                     item: enumerator.Current(),
                     level : level
                 };
                 obj.children = Enumerable.From(source).ByHierarchy(firstLevel, connectBy, orderBy, ascending, obj);
                 if (orderBy !== undefined) {
                     obj.children = obj.children[orderMethod](function(d) {
                         return orderBy(d.item); //unwrap the actual item for sort to work
                     });
                 }
                 obj.children = obj.children.ToArray();
                 Enumerable.From(obj.children).ForEach(function(child) {
                     child.getParent = function() {
                         return obj;
                     };
                 });
                 return obj;
             };

        return new IEnumerator(

        function() {
             enumerator = source.GetEnumerator();
         }, function() {
             while (enumerator.MoveNext()) {
                 var returnArr;
                 if (!parent) {
                     if (firstLevel(enumerator.Current(), index++)) {
                         return this.Yield(createLevel());
                     }

                } else {
                     if (connectBy(parent.item, enumerator.Current(), index++)) {
                         return this.Yield(createLevel());
                     }
                 }
             }
             return false;
         }, function() {
             Utils.Dispose(enumerator);
         })
     });
 },

```
  
## <a name="related-topics"></a>관련 항목

[SharePoint Server의 관리 탐색 개요](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation)

