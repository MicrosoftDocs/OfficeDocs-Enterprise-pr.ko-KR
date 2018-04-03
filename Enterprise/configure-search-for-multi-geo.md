---
title: 다중-지리적으로 분산 환경 관리
ms.author: tlarsen
author: tklarsen
manager: arnek
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: 다중-지리적으로 분산 환경에서 검색을 구성 하는 방법에 알아봅니다.
ms.openlocfilehash: 0c5c8eaa981c31151c70507da54587a7269f98f5
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/03/2018
---
# <a name="configure-search-for-onedrive-for-business-multi-geo"></a>비즈니스 다중-지리적으로 분산에 대 한 OneDrive에 대 한 검색 구성

다중-지리적으로 분산 SharePoint Online (SPO) 환경에서 조직 수 있는 하나의 Office 365 테 넌 트, 되었지만 여러 지리적 위치-에서 자신의 SharePoint 콘텐츠를 저장 한 중앙 위치와 하나 이상의 지리적 위치를 위성 합니다.

각 지리적 위치에는 자체 검색 인덱스와 검색 센터에 있습니다. 사용자를 검색 하는 경우 쿼리는 모든 인덱스를 정렬 하 고 반환 된 결과 병합 됩니다.

예 한 지리적 위치에 있는 사용자는 다른 지리적 위치에 저장 된 콘텐츠 또는 다른 지리적 위치로 제한 되는 SharePoint 사이트에서 콘텐츠를 검색할 수 있습니다. 사용자가이 콘텐츠에 대 한 액세스를 하는 경우 검색 결과 표시 됩니다.

## <a name="which-search-clients-work-in-a-multi-geo-environment"></a>다중-지리적으로 분산 환경에서 클라이언트 작업을 검색 하는?

이러한 클라이언트는 모든 지리적 위치에서 결과 반환할 수 있습니다.

-   비즈니스용 OneDrive

-   Delve

-   SharePoint 홈 페이지

-   검색 센터

-   SharePoint 검색 API를 사용 하는 사용자 지정 검색 응용 프로그램

### <a name="onedrive-for-business"></a>비즈니스용 OneDrive

다중-지리적으로 분산 환경 설정, OneDrive를 검색 하는 사용자는 즉시 모든 지리적 위치에서 결과를 가져옵니다.

### <a name="delve"></a>Delve

다중-지리적으로 분산 환경을 Delve에서 검색 하는 사용자를 설정 했으면 하는 즉시 모든 지리적 위치에서 결과를 가져옵니다.

Delve 피드와 프로필 카드만 **중앙** 위치에 저장 된 파일의 미리 보기를 표시 합니다. 위성 지리적 위치에 저장 된 파일에 대 한 파일 형식에 대 한 아이콘 대신 표시 됩니다.

### <a name="the-sharepoint-home-page"></a>SharePoint 홈 페이지

다중-지리적으로 분산 환경 설정 된, 하는 즉시 사용자 나타납니다 뉴스, 해당 SharePoint 홈 페이지에 여러 지리적 위치에서 최근 및 열어본 사이트입니다. SharePoint 홈 페이지에서 검색 상자를 사용 하는 경우 이러한만에서 결과 가져올 검색 인덱스에 있는 지리적으로 분산 위치 SPHome 합니다.

### <a name="the-search-center"></a>검색 센터

다중-지리적으로 분산 후 환경에 설정 된, 각 검색 센터는 자신의 지리적 위치에서 결과 표시만 계속입니다. 관리자가 모든 지리적 위치에서 결과를 가져오는 [각 검색 센터의 설정을 변경](#_Set_up_a_1) 해야 합니다. 이후에, 검색 센터에서 검색 하는 사용자가 모든 지리적 위치에서 결과를 가져옵니다.

### <a name="custom-search-applications"></a>사용자 지정 검색 응용 프로그램

평소와 같이 사용자 지정 검색 응용 프로그램을 기존 SharePoint 검색 REST Api를 사용 하 여 검색 인덱스와 상호작용 합니다. 일부 또는 전체, 지리적 위치에서 결과 얻으려면, 응용 프로그램 [API를 호출 하 고 새 다중-지리적으로 분산 쿼리 매개 변수를 포함할](#_Get_custom_search) 요청에 있어야 합니다. 모든 지리적 위치를 쿼리 로그 아웃 팬을 트리거합니다.

### <a name="whats-different-about-search-in-a-multi-geo-environment"></a>다중-지리적으로 분산 환경에서 검색 하는 방법에 대 한 서로 다른 이란?

일부 검색 기능을 잘 알고 있어야 수 있습니다는 다중-지리적으로 분산 환경에서 다르게 작동 합니다.

<table>
<thead>
<tr class="header">
<th align="left"><strong>기능</strong></th>
<th align="left"><strong>어떻게 작동 합니까</strong></th>
<th align="left"><strong>해결 방법</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">승격 된 결과</td>
<td align="left">여러 수준에서 승격 된 결과 함께 쿼리 규칙을 만들 수: 전체 테 넌 트, 사이트 모음 또는 사이트에 대 한 합니다. 다중-지리적으로 분산 환경에서 <strong>모든</strong> 지리적 위치에서 검색 센터에 결과 낼 하려는 경우 <strong>테 넌 트</strong> 수준에서 승격 된 결과 정의 합니다. 원할 경우 <strong></strong> 을 사이트 모음 또는 사이트의 지리적 위치에 있는 검색 센터에서 결과 개선 하기 위한 <strong>사이트 모음</strong> 또는 <strong>사이트</strong> 수준에서 결과 정의 합니다.</td>
<td align="left">지리적으로 분산 위치를 이동 하 고, 같은 다른 규칙 마다 서로 다른 승격 된 결과 필요 하지 않으면 승격 된 테 넌 트 수준에서 결과 정의 하는 것이 좋습니다.</td>
</tr>
<tr class="even">
<td align="left">검색 구체화</td>
<td align="left">테 넌 트의 지리적 위치를 모두에서 구체화를 반환 하 고 집계 하 게 하는 검색 합니다. 집계는 최선을 다, 구체화 개수 100% 정확 하지 못할 수도 있습니다. 대부분의 검색 기반 시나리오가 정확 하이 게도 충분 합니다.</td>
<td align="left">검색 기반 응용 프로그램의 구체화 완전성을 활용 하는 경우 쿼리 하지 각 지리적 위치 독립적으로 다중-지리적으로 분산 된 팬아웃을 사용 하지 않고 합니다.</td>
</tr>
<tr class="odd">
<td align="left"></td>
<td align="left">다중-지리적으로 분산 검색 숫자 구체화에 대 한 동적 버킷팅은 지원 하지 않습니다.</td>
<td align="left">숫자 구체화에 대 한 <a href="https://docs.microsoft.com/en-us/sharepoint/dev/general-development/query-refinement-in-sharepoint">"Discretize" 매개 변수</a> 를 사용 합니다.</td>
</tr>
<tr class="even">
<td align="left">문서 Id</td>
<td align="left">문서 Id에 의존 하는 검색 기반 응용 프로그램을 개발 하는 경우에 여러 지리적 위치에 걸친 다중-지리적으로 분산 환경에서 문서 Id 고유 하지, 지리적 위치 마다 고유 하다는 note 합니다.</td>
<td align="left">지리적 위치를 식별 하는 열을 추가 했습니다. 고유성을 달성 하기 위해이 열을 사용 합니다. 이 열에는 "GeoLocationSource" 라고 합니다.</td>
</tr>
<tr class="odd">
<td align="left">결과의 수</td>
<td align="left">지리적으로 분산 위치의 결합 된 결과 표시 하는 검색 결과 페이지 하지만 500 결과 이외 페이지 불가능 합니다.</td>
<td align="left"></td>
</tr>
</tbody>
</table>

### <a name="whats-not-supported-for-search-in-a-multi-geo-environment"></a>항목 수는 없습니다 다중-지리적으로 분산 환경에서 검색을 위한?

친숙 한 수도 있습니다 검색 기능 중 일부는 다중-지리적으로 분산 환경에서 지원 되지 않습니다.

<table>
<thead>
<tr class="header">
<th align="left"><strong>검색 기능</strong></th>
<th align="left"><strong>참고</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">응용 프로그램 전용 인증</td>
<td align="left">응용 프로그램 전용 인증 (서비스에서 액세스 권한을된) 다중-지리적으로 분산 검색에서 지원 되지 않습니다.</td>
</tr>
<tr class="even">
<td align="left">게스트 사용자</td>
<td align="left">게스트 사용자는만에서 찾고 지리적 위치에서 결과를 가져옵니다.</td>
</tr>
</tbody>
</table>

### <a name="how-does-search-work-in-a-multi-geo-environment"></a>어떻게 역할 검색 다중-지리적으로 분산 환경에서 작동 합니까?

**모든** 검색 클라이언트 기존 SharePoint 검색 REST Api와 상호작용 하는데 사용할 검색 인덱스입니다.

<table>
<thead>
<tr class="header">
<th align="left"><p><img src="media/configure-search-for-multi-geo_image1.png" /></p>
<p>그림 1: 세 지리적 위치를 가진 테 넌 트 간에 검색</p></th>
<th align="left"><p>쿼리 속성 EnableMultiGeoSearch와 검색 REST 끝점을 호출 하는 검색 클라이언트 = true입니다.</p>
<p>쿼리는 테 넌 트의 모든 지리적 위치에 전송 됩니다.</p>
<p>각 지리적 위치에서 검색 결과 병합 하 고 순위가 지정 됩니다.</p>
<p>클라이언트 통합된 검색 결과를 가져옵니다.</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

<span id="_Set_up_a" class="anchor"><span id="_Ref501388384" class="anchor"></span></span>다중-지리적으로 분산 검색 각 geos에서 각 검색 끝점을 호출 하 여 작동 합니다. 병합 작업을 수행할 수는 전에 회신 가장 느린 레그에 대 한 리더 우리는 병합 (영문) 될 수행,에 게 원격 이동에 대 한 요청을 동시에 수행 됩니다. 다중-지리적으로 분산을 알 수 있듯이이 검색 환경에 추가 대기 시간을 추가 합니다.  <span id="_Set_up_a_1" class="anchor"><span id="_Ref505252370" class="anchor"></span></span> 
### 모든 지리적 위치에서 결과 표시 하도록 검색 센터를 가져오려면

각 검색 센터는 여러 분야별 하 고 각 범주를 개별적으로 설정 해야 합니다.

1.  검색 결과 페이지 및 검색 결과 웹 파트를 편집할 수 있는 권한이 있는 계정으로 다음이 단계를 수행 하는 것을 확인 합니다.

2.  검색 결과 페이지로 이동 ( [목록](https://support.office.com/article/174d36e0-2f85-461a-ad9a-8b3f434a4213) 검색 결과 페이지 참조)

3.  설정, 오른쪽, 위쪽 모서리에서 **설정** 기어 아이콘을 클릭 한 다음 **페이지 편집**을 클릭 하 여 세로 선택 합니다.

> ![](media/configure-search-for-multi-geo_image2.png)
>
> 검색 결과 페이지가 편집 모드로 열립니다.

1.  검색 결과 웹 파트에 포인터를 위, 웹 파트의 오른쪽 모서리는 화살표를 클릭 한 다음 메뉴에서 **웹 파트 편집** 을 클릭 합니다. ![](media/configure-search-for-multi-geo_image3.png)

> 위쪽에서 리본 메뉴에서 검색 결과 웹 파트 도구 창이 열립니다 페이지의 오른쪽입니다.

1.  웹 파트 도구 창의 **결과 설정을 제어**, 아래에서 **설정** 섹션에서 모든 지리적 위치에서 결과 표시 하도록 검색 결과 웹 파트를 가져올 **결과 표시 다중-지리적으로 분산** 선택 합니다.

2.  하 여 변경 내용을 저장 하 고 웹 파트 도구 창을 닫습니다 **확인** 클릭 합니다.

3.  주 메뉴의 페이지 탭에서 **체크인** 을 클릭 하 여 검색 결과 웹 파트에 변경 내용을 확인 합니다.

4.  페이지 맨 마지막에 나오는 참고에서 제공 하는 링크를 사용 하 여 변경 내용을 게시 합니다.

<span id="_Get_custom_search" class="anchor"><span id="_Ref501388387" class="anchor"></span></span>
### <a name="get-custom-search-applications-to-show-results-from-all-or-some-geo-locations"></a>일부 또는 전체 지리적 위치에서 결과 표시 하도록 사용자 지정 검색 응용 프로그램 가져오기

사용자 지정 검색 응용 프로그램 모두 또는 일부를 지리적으로 분산 위치에서 SharePoint 검색 REST API에 요청 된 쿼리 매개 변수를 지정 하 여 결과 가져올 합니다. 쿼리 매개 변수를에 따라 쿼리 모든 지리적 위치에 나 일부 지리적 위치에 정렬 됩니다. 예, 지리적 위치 관련 정보를 찾을 수의 하위 집합을 쿼리할 해야하는 경우에 이러한 아웃 팬을 제어할 수 있습니다. 요청이 성공 하는 경우 SharePoint 검색 REST API 응답 데이터를 반환 합니다.

### <a name="query-parameters"></a>쿼리 매개 변수

**EnableMultiGeoSearch** -쿼리를 Geo 다중 테 넌 트의 다른 지리적 위치를 인덱스에 정렬 항목과 여부를 지정 하는 부울 값입니다. **True** 를 쿼리; 아웃 펼쳐서로 설정 **false** 를 쿼리 아웃 펼쳐서 하지 않습니다. 기본값은 **false**입니다. 쿼리는이 매개 변수를 포함 하지 않으면 다른 지리적 위치에 정렬 **되지 않습니다** . 다중-지리적으로 분산 없는 환경에서 매개 변수를 사용 하는 경우에 매개 변수는 무시 됩니다.

**ClientType** -문자열입니다. 각 검색 응용 프로그램에 대 한 고유 클라이언트 이름을 입력 합니다. 쿼리는이 매개 변수를 포함 하지 않으면 다른 지리적 위치에 정렬 **되지 않습니다** .

**MultiGeoSearchConfiguration** -는 지리적으로 분산의 다중 지리적 위치 테 넌 트를 ** **EnableMultiGeoSearch** 참인 경우**에 쿼리 펼쳐서 선택 목록입니다. 이 매개 변수를 포함 하지 않거나는 비워둡니다 하지 않는 경우 쿼리 모든 지리적 위치에 정렬 됩니다. 각 지리적 위치에 대 한 JSON 형식에는 다음 항목을 입력 합니다.

<table>
<thead>
<tr class="header">
<th align="left">항목</th>
<th align="left">설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">DataLocation</td>
<td align="left">지리적으로 분산 위치 이름 예입니다.</td>
</tr>
<tr class="even">
<td align="left">끝점</td>
<td align="left">예, 연결할 끝점https://contoso.sharepoint.com</td>
</tr>
<tr class="odd">
<td align="left">SourceId</td>
<td align="left">결과 원본에 같은 B81EAB55-3140-4312-B0F4-9459D1B4FFEE의 GUID입니다.</td>
</tr>
</tbody>
</table>

DataLocation 또는 끝점을 생략 하면 또는 DataLocation 중복 될 경우에 요청이 실패 합니다. [다음은 Microsoft Graph를 사용 하 여 테 넌 트의 지리적 위치 끝점에 대 한 정보를 얻을 수 있습니다](https://docs.microsoft.com/en-us/sharepoint/dev/solution-guidance/multigeo-discovery).

### <a name="response-data"></a>응답 데이터

**MultiGeoSearchStatus** – SharePoint 검색 API는 요청에 대 한 응답으로 반환 하는 속성입니다. 속성의 값은 문자열 및 SharePoint 검색 API를 반환 하는 결과 대 한 다음 정보를 제공 합니다.

<table>
<thead>
<tr class="header">
<th align="left">값</th>
<th align="left">설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">전체</td>
<td align="left">모든 결과를 <strong>모든</strong> 지리적 위치 수 있습니다.</td>
</tr>
<tr class="even">
<td align="left">부분</td>
<td align="left">하나 이상의 지리적 위치에서 일부 결과입니다. 결과 일시적인 오류로 인해 완전 하지 않습니다.</td>
</tr>
<tr class="odd">
<td align="left">없음</td>
<td align="left">쿼리 다중-지리적으로 분산 쿼리 없으며 다른 지리적 위치를 정렬 하지 되었습니다.</td>
</tr>
</tbody>
</table>

### <a name="query-using-the-rest-service"></a>REST 서비스를 사용 하 여 쿼리

GET 요청을 하는 URL에 쿼리 매개 변수를 지정 합니다. POST 요청으로 표기법 JSON (JavaScript Object) 형식에서 본문에 쿼리 매개 변수를 전달 합니다.

#### <a name="request-headers"></a>요청 헤더

<table>
<thead>
<tr class="header">
<th align="left">이름</th>
<th align="left">값</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Content-Type</td>
<td align="left">응용 프로그램/json; odata = 자세한 정보 표시</td>
</tr>
</tbody>
</table>

#### <a name="sample-get-request-thats-fanned-out-to-all-geo-locations"></a>**모든** 지리적 위치에 정렬 되는 샘플 GET 요청

https:// \<테 넌 트\>/\_api/검색/query?querytext ''.value = 속성 'EnableMultiGeoSearch:true' & ClientType = =' 내\_클라이언트\_id'

#### <a name="sample-get-request-to-fan-out-to-some-geo-locations"></a>샘플 GET 요청을 **일부** 지리적 위치를 팬 하

https:// <tenant>/_api/search/query?querytext '사이트' & ClientType = 'my_client_id' & 속성 = ='EnableMultiGeoSearch:true, MultiGeoSearchConfiguration: [{DataLocation\:"이름"\,끝점\:"https\: contosoNAM.sharepoint.com"\,SourceId\:"B81EAB55-3140-4312-B0F4-9459D1B4FFEE"}\,{DataLocation\:"수"\,끝점\:" https\://contosoCAN.sharepoint-df.com "}]'

#### <a name="sample-post-request-thats-fanned-out-to-all-geo-locations"></a>**모든** 지리적 위치에 정렬 되는 샘플 POST 요청

    {
        "request": {
            "__metadata": {
            "type": "Microsoft.Office.Server.Search.REST.SearchRequest"
        },
        "Querytext": "sharepoint",
        "Properties": {
            "results": [
                {
                    "Name": "EnableMultiGeoSearch",
                    "Value": {
                        "QueryPropertyValueTypeIndex": 3,
                        "BoolVal": true
                    }
                }
            ]
        },
        "ClientType": "my_client_id"
        }
    }


#### <a name="sample-post-request-thats-fanned-out-to-some-geo-locations"></a>**일부** 지리적 위치에 정렬 되는 샘플 POST 요청


    {
        "request": {
            "Querytext": "SharePoint",
            "ClientType": "my_client_id",
            "Properties": {
                "results": [
                    {
                        "Name": "EnableMultiGeoSearch",
                        "Value": {
                            "QueryPropertyValueTypeIndex": 3,
                            "BoolVal": true
                        }
                    },
                    {
                        "Name": "MultiGeoSearchConfiguration",
                        "Value": {
                        "StrVal": "[{\"DataLocation\":\"NAM\",\"Endpoint\":\"https://contoso.sharepoint.com\",\"SourceId\":\"B81EAB55-3140-4312-B0F4-9459D1B4FFEE\"},{\"DataLocation\":\"CAN\",\"Endpoint\":\"https://contosoCAN.sharepoint.com\"}]",
                            "QueryPropertyValueTypeIndex": 1
                        }
                    }
                ]
            }
        }
    }

### <a name="query-using-csom"></a>CSOM을 사용 하 여 쿼리

**모든** 지리적 위치에 정렬 되는 샘플 CSOM 쿼리는 다음과 같습니다.

    var keywordQuery = new KeywordQuery(ctx);
    keywordQuery.QueryText = query.SearchQueryText;
    keywordQuery.ClientType = <enter a string here>;
    keywordQuery["EnableMultiGeoSearch"] = true;