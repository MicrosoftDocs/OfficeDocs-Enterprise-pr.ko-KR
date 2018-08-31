---
title: 개인 데이터 검색 및 찾기
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 2/7/2018
ms.audience: ITPro
ms.topic: overview
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- GDPR
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.custom: ''
ms.assetid: ''
description: Office 365에서 개인 데이터를 검색하고 찾는 방법을 알아봅니다.
ms.openlocfilehash: 8f1a293377570233e4d3ef01da9c56345768828c
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22914913"
---
# <a name="search-for-and-find-personal-data"></a>개인 데이터 검색 및 찾기

개인 데이터는 EU(유럽 연합)에 거주하는 식별되었거나 식별 가능한 자연인과 관련된 데이터로서 GDPR에서 매우 광범위하게 정의됩니다.

문서 4 - 정의

> '개인 데이터'는 식별되었거나 식별 가능한 자연인(‘데이터 주체’)과 관련된 정보를 의미합니다. 식별 가능한 자연인은 직간접적으로, 특히 이름, 식별 번호, 위치 데이터, 온라인 식별자 또는 해당 자연인의 신체적, 생리적, 유전적, 정신적, 경제적, 문화적 또는 사회적 ID와 같은 식별자를 참조하여 식별될 수 있는 사람입니다.

이 문서에서는 SharePoint Online 및 비즈니스용 OneDrive에 저장된 개인 데이터를 찾는 방법을 보여 줍니다(모든 Office 365 그룹 및 Microsoft Teams 사이트 포함) 

Office 365에서 GDPR이 적용되는 개인 데이터를 찾으려면 중요한 정보 유형을 사용해야 합니다. 이 과정에서 자동화된 서비스가 의료 서비스 번호 및 신용 카드 번호와 같은 특정 정보 유형을 인식하는 방식이 정의됩니다. 현재, 휴지 상태의 Exchange 사서함에서 데이터를 찾는 데는 이러한 정보를 사용할 수 없습니다. 그렇지만 중요한 정보 유형을 데이터 손실 방지 정책과 함께 사용하여 전송 중인 메일에서 개인 데이터를 찾을 수 있습니다.

따라서 현재는 콘텐츠 검색을 사용하여 Exchange Online 사서함의 휴지 상태의 개인 데이터를 찾을 수 없지만, GDPR에 맞게 조정한 중요한 정보 유형을 사용하여 전자 메일을 통해 전송되는 개인 정보를 찾아 보호할 수 있습니다.

## <a name="use-content-search-to-find-personal-data"></a>콘텐츠 검색을 사용하여 개인 데이터 찾기

Office 365에서 개인 데이터를 찾는 위한 3단계 접근 방식이 권장됩니다. 이 항목의 나머지 부분에서는 이러한 각 단계에 대한 지침을 제공합니다.

<table>
<thead>
<tr class="header">
<th align="left"><strong>단계</strong></th>
<th align="left"><strong>설명</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>1. 중요한 정보 유형 검색</p></td>
<td align="left"><p>먼저 중요한 정보 유형을 사용하여 개인 데이터를 찾습니다. 각각의 중요한 정보 유형에 대해 콘텐츠 검색 쿼리를 만듭니다. 쿼리를 실행한 후 결과를 분석합니다.</p>
필요에 따라 가양성을 줄이기 위해 쿼리에 매개 변수를 추가합니다. <li>개수 범위</li>
    <li>신뢰도 범위</li>
    <li>좀 더 복잡한 쿼리를 위한 기타 속성 또는 연산자</li>
<p>필요한 경우 조직에 맞게 정확도를 향상시키도록 중요한 정보 유형을 수정합니다.</p>
<p><li>XML에서 직접 신뢰 수준을 조정합니다.</li></p>
<p><li>키워드를 추가합니다.</li></p>
<p><li>키워드에 대한 근접 요구 사항을 조정합니다.</li></p></td>
</tr>
<tr class="even">
<td align="left"><p>2. KQL(키워드 쿼리 언어)을 사용하여 작업 환경에서 추가 개인 데이터 찾기</p></td>
<td align="left"><p>중요한 정보 유형에 포함되지 데이터를 찾으려면 KQL 쿼리 언어를 사용하여 사용자 지정 쿼리를 개발합니다.</p>
<p>이러한 검색의 결과를 테스트하고 예상된 결과를 얻을 때까지 KQL 쿼리 문자열을 조정합니다.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>3. KQL 쿼리를 사용하여 새 사용자 지정 중요한 정보 유형 만들기</p></td>
<td align="left">KQL 쿼리를 최적화하여 대상 데이터를 찾은 후 이러한 쿼리를 사용하여 새 사용자 지정 중요한 정보 유형을 만듭니다. 그런 후 DLP 정책 및 기타 도구와 다른 KQL 쿼리 내에서 콘텐츠 검색에 이러한 사용자 지정 중요한 정보 유형을 사용할 수 있습니다.</td>
</tr>
</tbody>
</table>

출시 예정 - 보안 및 규정 준수 센터의 새 사용자 인터페이스에서 중요한 정보 유형을 만들고 수정할 수 있습니다. 일치하는 결과를 동적으로 확인하고 사용자 요구에 맞게 중요한 정보 유형을 조정할 수 있습니다.

## <a name="search-for-sensitive-information-types-using-content-search"></a>콘텐츠 검색을 사용하여 중요한 정보 유형 검색

먼저 Office 365에 포함된 중요한 정보 유형을 사용하여 개인 데이터를 검색합니다. 이러한 데이터는 보안 및 규정 준수 센터의 분류 아래에 표시됩니다.

이 항목에는 유럽 연합 거주민에게 적용되는 최신 중요한 정보 유형 목록이 포함됩니다. 이러한 중요한 정보 유형을 시작점으로 사용합니다. 보안 및 규정 준수 센터에서 GDPR 규정 준수에 도움이 될 수 있는 새로운 추가 항목이 있는지 자주 확인합니다.

또한 [중요한 정보 유형 및 각 유형이 확인하는 내용 목록](https://support.office.com/ko-KR/article/What-the-sensitive-information-types-look-for-fd505979-76be-4d9f-b459-abef3fc9e86b)을 참조하세요.

중요한 정보 유형은 정규식이나 함수로 식별될 수 있는 패턴으로 정의됩니다. 또한 키워드 및 체크섬과 같은 확증적인 증거를 사용하여 중요한 정보 유형을 식별할 수 있습니다. 이러한 평가 프로세스에서 신뢰 수준 및 근접성도 사용됩니다. 중요한 정보 유형은 정규식이나 함수로 식별될 수 있는 패턴으로 정의됩니다. 또한 키워드 및 체크섬과 같은 보완적 증거를 사용하여 중요한 정보 유형을 식별할 수 있습니다. 신뢰도 및 근접성도 평가 프로세스에서 활용됩니다.

현재, 사서함에서 휴지 상태의 데이터를 찾는 데는 중요한 정보 유형을 사용할 수 없습니다.

### <a name="using-content-search-with-sensitive-information-types"></a>중요한 정보 유형에 콘텐츠 검색 사용

<table>
<thead>
<tr class="header">
<th align="left"><strong>단계</strong></th>
<th align="left"><strong>추가 정보</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd"><td align="left"><p>보안 및 준수 센터에서 콘텐츠 검색으로 이동</p></td>
<td align="left"><p>보안 및 준수 센터의 왼쪽 창에서 **검색 및 조사** &gt; **콘텐츠 검색**을 클릭합니다.</p>
<p>
  <a href="https://support.office.com/en-us/article/Run-a-Content-Search-in-the-Office-365-Security-Compliance-Center-61852fd9-fe8a-4880-a339-cb19ed3bff4a">Office 365 보안 및 준수 센터에서 콘텐츠 검색 실행</a>을 참조하세요.</p></td>
</tr>
<tr class="even">
<td align="left"><p>각 중요한 정보 유형에 대해 새 검색 항목 만들기</p></td>
<td align="left"><p>다음 구문을 사용합니다.</p>
<blockquote>
<p>SensitiveType:”&lt;type&gt;”</p>
</blockquote>
<p>예를 들면 다음과 같습니다.</p>
<blockquote>
<p>SensitiveType:&quot;France Passport Number&quot;</p>
</blockquote>
<p>검색 범위를 SharePoint(비즈니스용 OneDrive 포함)으로 지정합니다. 구문이 정확한지와 불필요한 공백이나 입력 오류가 없는지 확인합니다.</p>
<p><a href="https://support.office.com/ko-KR/article/Form-a-query-to-find-sensitive-data-stored-on-sites-3019fbc5-7f15-4972-8d0e-dc182dc7f836">사이트에 저장된 중요한 데이터를 찾기 위한 쿼리 작성</a>을 참조하세요.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>각 검색에 대한 결과 검토</p></td>
<td align="left"><p>다음 유형의 문제를 찾아 쿼리 정확도가 원하는 수준인지 확인합니다.</p>
<p><li>많은 가양성</li></p>
<p><li>누락된 데이터의 알려진 인스턴스</li></p>
<p>
  <a href="https://support.office.com/en-us/article/Export-Content-Search-results-from-the-Office-365-Security-Compliance-Center-ed48d448-3714-4c42-85f5-10f75f6a4278">Office 365 보안 및 준수 센터에서 콘텐츠 검색 결과 내보내기</a>를 참조하세요.</p>
<p>참고: Mozilla Firefox 또는 Chrome을 사용하는 경우 필요한 추가 기능을 설치하기 위해 먼저 Internet Explorer 또는 Edge를 사용하여 보고서를 다운로드해야 할 수 있습니다.</p></td>
</tr>
</tbody>
</table>

## <a name="sensitive-information-types-for-eu-citizen-data"></a>EU 거주민 데이터에 대한 중요한 정보 유형

이러한 중요한 정보 유형으로 시작합니다. EU 국가의 개인 데이터에 대한 더 많은 중요한 정보 유형이 곧 제공될 예정입니다.

> 벨기에 국가 번호
>
> 신용 카드 번호
>
> 크로아티아 ID 카드 번호
>
> 크로아티아 개인 식별(OIB) 번호
>
> 체코 국가 ID 카드 번호
>
> 덴마크 개인 식별 번호
>
> 유럽 직불 카드 번호
>
> 핀란드 국가 ID
>
> 핀란드 여권 번호
>
> 프랑스 운전 면허 번호
>
> 프랑스 국가 ID 카드(CNI)
>
> 프랑스 여권 번호
>
> 프랑스 사회 보장 번호(INSEE)
>
> 독일 운전 면허 번호
>
> 독일 ID 카드 번호
>
> 독일 여권 번호
>
> 그리스 국가 ID 카드
>
> IBAN(국제 은행 계좌 번호)
>
> IP 주소
>
> 아일랜드 PPS(개인 공공 서비스) 번호
>
> 이탈리아 운전 면허 번호
>
> 네덜란드 시민 서비스(BSN) 번호
>
> 노르웨이 ID 번호
>
> 폴란드 ID 카드
>
> 폴란드 국가 ID(PESEL)
>
> 폴란드 여권
>
> 포르투갈 시민 카드 번호
>
> 스페인 SSN(사회 보장 번호)
>
> 스웨덴 국가 ID
>
> 스웨덴 여권 번호
>
> 영국 운전 면허 번호
>
> 영국 선거 롤 번호
>
> 영국 국립 보건 서비스 번호
>
> 영국 NINO(국민 보험 번호)
>
> 미국/영국 여권 번호

## <a name="add-parameters-to-a-sensitive-information-type-query-to-hone-the-results"></a>중요한 정보 유형 쿼리에 매개 변수를 추가하여 결과 조정

중요한 정보 유형 쿼리에 다음 매개 변수를 추가할 수 있습니다.

-   개수 범위 - 문서가 쿼리 결과에 포함되기 위해 포함해야 하는 중요한 정보가 나오는 횟수를 정의합니다.

-   신뢰도 범위 - 검색된 중요한 유형이 실제로 일치하는 신뢰도 수준[예: 85(85%)]을 나타냅니다.

구문:

-   SensitiveType:”\<type\>|\<count range\>|\<confidence range\>”

예제:

-   SensitiveType:“Credit Card Number|5” (정확히 5개의 카드 번호와 일치하는 문서만 반환)

-   SensitiveType:“Credit Card Number|\*|85..” (신뢰도 범위는 85% 이상임)

참고: "SensitiveType"은 대/소문자를 구분하지만 쿼리의 나머지 부분은 그렇지 않습니다.

또한 속성 및 연산자를 사용하여 쿼리를 구체화하는 방법을 보여줄 수도 있습니다. 자세한 내용 및 예제에 대해서는 [사이트에 저장된 중요한 데이터를 찾기 위한 쿼리 작성](https://support.office.com/ko-KR/article/Form-a-query-to-find-sensitive-data-stored-on-sites-3019fbc5-7f15-4972-8d0e-dc182dc7f836)을 참조하세요.
