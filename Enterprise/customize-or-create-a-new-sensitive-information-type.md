---
title: 중요한 정보 유형 사용자 지정 또는 새로 만들기
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
description: GDPR에 대한 Office 365 중요한 정보 유형을 수정하거나 새로 만드는 방법을 알아봅니다.
ms.openlocfilehash: 70c79bd08a9e9e94155f4a8de76f627afc91bddf
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915563"
---
# <a name="customize-or-create-a-new-sensitive-information-type"></a>중요한 정보 유형 사용자 지정 또는 새로 만들기

이 문서에서는 GDPR에 대한 Office 365 중요한 정보 유형을 수정하거나 새로 만드는 방법을 보여 주는 3가지 예제를 제공합니다.

-   기존 중요한 정보 유형 수정 — 유럽 직불 카드 번호

-   새 중요한 정보 유형 만들기 - 전자 메일 주소

-   예제 XML 파일을 사용하여 새 중요한 정보 유형 만들기 — Contoso 고객 번호

참고:

-   [사용자 지정 중요한 정보 유형 만들기](https://support.office.com/ko-KR/article/Create-a-custom-sensitive-information-type-82c382a5-b6db-44fd-995d-b333b3c7fc30)

-   [기본 제공 중요한 정보 유형 사용자 지정 ](https://support.office.com/ko-KR/article/Customize-a-built-in-sensitive-information-type-2164ce3d-4d64-4283-b6b1-b81fbe835e8e)

## <a name="modify-a-sensitive-information-type-to-improve-accuracy"></a>정확도를 향상시키도록 중요한 정보 유형 수정

콘텐츠 검색을 사용하여 중요한 정보 유형을 통해 개인 데이터를 검색하려고 하는데 예상된 결과가 반환되지 않거나, 너무 많은 가양성이 반환된 경우 작업 환경에 더 잘 맞게 중요한 정보 유형을 수정하는 것이 좋습니다.

중요한 정보 유형을 만들거나 사용자 지정할 때의 모범 사례는 기존의 중요한 정보 유형에 따라 새로운 정보 유형을 만들고 고유한 이름 및 식별자를 지정하는 것입니다. 예를 들어 "유럽 직불 카드 번호" 중요한 정보 유형 매개 변수를 조정하려는 경우 해당 규칙 사본에 "유럽 직불 카드 강화"로 이름을 지정하여 원본과 구분할 수 있습니다.

새 중요한 정보 유형에서 정확도 향상을 위해 변경하려는 값을 수정하기만 하면 됩니다. 일단 완료되면, 새 중요한 정보 유형을 업로드하고, 방금 추가한 새 중요한 정보 유형을 사용하기 위한 새 DLP 규칙을 새로 만듭니다(또는 기존 계정 수정). 중요한 정보 유형의 정확도를 수정하려면 약간의 시행 착오가 필요할 수 있으므로 원본 유형의 복사본을 유지하여 나중에 필요할 때 원본 사본으로 대체할 수 있습니다.

중요한 정보 유형을 사용자 지정하려면

1.  Office 365에서 기본 제공 중요한 정보 유형의 기존 Microsoft 규칙 패키지를 내보냅니다.

2.  이 XML 파일의 이름을 바꾸고 원하는 XML 편집기에서 엽니다.

3.  중요한 정보 유형을 격리하고 다른 모든 정보 유형을 제거합니다.

4.  PowerShell을 사용하여 수정하려는 중요한 정보 유형에 대해 2개의 새 GUID를 생성합니다.

5.  중요한 정보 유형이 고유하도록 ID 및 기타 기본 요소를 수정합니다(2개의 GUID를 생성한 새 GUID로 대체).

6.  일치 요구 사항을 조정하여 정확도를 높입니다.

    1.  근접성 수정 - 문자 패턴 근접성을 수정하여 중요한 정보 유형에 대해 키워드를 찾아야 하는 창을 확장하거나 축소합니다.

    2.  키워드 수정 — 이 규칙에 대해 일치 사실을 알리기 위해 중요한 정보 유형이 보다 구체적인 추측 증거를 제공하도록 \<Keywords\> 요소 중 하나에 키워드를 추가합니다. 또는 가양성을 유발하는 키워드를 제거합니다.

    3.  신뢰도 수정 - 일치에 대해 알림 및 보고가 제공되기 전에 중요한 정보 유형이 해당 정의에 지정된 조건과 일치해야 하는 신뢰도를 수정합니다.

7.  새 중요한 정보 유형을 업로드합니다.

8.  중요한 정보를 식별하도록 콘텐츠를 다시 크롤링합니다. [사이트 크롤링 및 재인덱싱 수동 요청](https://support.office.com/ko-KR/article/Manually-request-crawling-and-re-indexing-of-a-site-a-library-or-a-list-9AFA977D-39DE-4321-B4CA-8C7C7E6D264E)을 참조하세요.

## <a name="example-modify-the-eu-debit-card-number-sensitive-information-type"></a>예제: '유럽 직불 카드 번호' 중요한 정보 유형 수정

모든 시스템에서 DLP 규칙의 정확도를 향상시키려면 샘플 데이터 집합에 대한 테스트가 필요하며, 반복적인 수정 및 테스트를 통해 미세 조정해야 할 수 있습니다. 이 예제에서는 정확도 개선을 위해 '유럽 직불 카드 번호' 중요한 정보 유형에 대한 수정 작업을 보여 줍니다.

이 예제에서 유럽 직불 카드 번호를 검색할 때 해당 번호의 정의는 복잡한 패턴을 사용하여 16자리 숫자로 엄격히 정의되며 체크섬의 유효성 검사를 따라야 합닏. 이 중요한 정보 유형의 문자열 정의로 인해 이 패턴을 변경할 수 없습니다. 그러나 Office 365 DLP가 Office 365 내에서 이 중요한 정보 유형을 찾는 방식의 정확도를 높이기 위해 다음과 같이 수정할 수 있습니다.

### <a name="proximity-modification"></a>근접성 수정

\<Entity\> 요소의 patternProximity 값을 300에서 150자로 수정하여 창을 축소합니다. 이것은 이 규칙에 대한 일치를 알리려면 추측 증거 또는 키워드가 중요한 정보 유형과 좀 더 근접해야 함을 나타냅니다.

\<Entity id="48da7072-821e-4804-9fab-72ffb48f6f78" patternsProximity="150" recommendedConfidence="85"\>

### <a name="keyword-modifications"></a>키워드 수정

일부 키워드는 가양성의 원인이 될 수 있습니다. 따라서 키워드를 제거할 수 있습니다. 이러한 예에 해당하는 키워드는 다음과 같습니다.

\<Keyword id="Keyword\_card\_terms\_dict"\>

\<Group\>

\<Term\>corporate card\</Term\>

\<Term\>organization card\</Term\>

\<Term\>acct nbr\</Term\>

\<Term\>acct num\</Term\>

\<Term\>acct no\</Term\>

…

\</Group\>

\</Keyword\>

### <a name="confidence-modifications"></a>신뢰도 수정

정의에서 키워드를 제거하는 경우 일반적으로 이 값이 줄여서 이 중요한 정보 유형을 찾을 수 있는 신뢰도를 조정할 수 있습니다. 유럽 직불 카드 번호 유형의 기본 수준은 85입니다.

\<Entity id="48da7072-821e-4804-9fab-72ffb48f6f78" patternsProximity="150" recommendedConfidence="85"\>

\<Pattern confidenceLevel="85"\>

…

\</Pattern\>

\</Entity\>

## <a name="create-a-new-custom-sensitive-information-type"></a>새 사용자 지정 중요한 정보 유형 만들기

새 사용자 지정 중요한 정보 유형을 만들려면 먼저 콘텐츠 검색을 사용하여 다음을 수행합니다.

-   KQL 쿼리 최적화

-   가장 유용한 키워드 찾기

이러한 결과를 사용하여 새 중요한 정보 유형을 만듭니다. 그런 후 작업 환경에 대한 새 중요한 정보 유형을 최적화합니다.

참고: 유럽 연합 국가의 개인 데이터에 대해 많은 새 중요한 정보 유형이 제공될 예정입니다. 새 중요한 정보 유형을 만들어야 할 경우 먼저 작업 환경에 맞게 조정된 데이터를 대상으로 지정합니다.

### <a name="step-1--use-kql-queries-and-key-words-to-find-additional-data-in-your-environment"></a>1단계 - KQL 쿼리 및 키워드를 사용하여 사용 환경에서 추가 데이터 찾기

GDPR이 적용되는 개인 데이터를 찾기 위한 추가 쿼리를 만들어야 할 수 있습니다. 콘텐츠 검색은 KQL(키워드 쿼리 언어)을 사용하여 데이터를 찾습니다. 대부분의 중요한 정보 유형은 중요한 정보 유형 없이 KQL만 사용하여 정확히 검색할 수 없습니다. 따라서 콘텐츠 검색을 사용하여 KQL 문자열을 테스트 및 최적화하고 이를 사용하여 보다 정확한 새 중요한 정보 유형을 만들고 조정해야 합니다.

KQL을 사용하여 쿼리를 작성하고 최적화하려면 다음 리소스를 사용합니다.

-   [KQL(키워드 쿼리 언어) 구문 참조(DMC)](https://docs.microsoft.com/ko-KR/sharepoint/dev/general-development/keyword-query-language-kql-syntax-reference)

-   [Office 365 보안 및 준수 센터에서 콘텐츠 검색 실행](https://support.office.com/ko-KR/article/Run-a-Content-Search-in-the-Office-365-Security-Compliance-Center-61852fd9-fe8a-4880-a339-cb19ed3bff4a) 

콘텐츠 검색은 KQL 쿼리 및 중요한 정보 유형을 개발하는 데 도움이 되는 또 다른 리소스인 키워드를 제공합니다. 키워드 목록은 왜 사용할까요? 많은 항목이 각 키워드와 일치하는 방식을 보여 주는 통계를 얻을 수 있습니다. 이러한 통계는 가장 많이(덜) 효과적인 키워드를 빠르게 식별하는 데 도움이 됩니다. 검색 통계에 대한 자세한 내용은 [콘텐츠 검색 결과에 대한 키워드 통계 보기](https://support.office.com/ko-KR/article/View-keyword-statistics-for-Content-Search-results-9701a024-c52e-43f0-b545-9a53478aec04)를 참조하세요.

각 행의 키워드는 만들어지는 검색 쿼리에서 OR 연산자로 연결됩니다. 행에 키워드 구(괄호 사용)를 사용할 수도 있습니다.

자세한 내용은 [콘텐츠 검색에 대한 키워드 쿼리 및 검색 조건](https://support.office.com/ko-KR/article/Keyword-queries-and-search-conditions-for-Content-Search-c4639c2e-7223-4302-8e0d-b6e10f1c3be3)을 참조하세요.

### <a name="exampleusing-content-search-to-identify-email-addresses"></a>예제 - 콘텐츠 검색을 사용하여 전자 메일 주소 식별

전자 메일 주소는 데이터 주체와 관련된 중요한 정보로 간주됩니다. 다음은 콘텐츠 검색이 어떻게 유용할 수 있는지를 보여 주는 간단한 예제입니다.

KQL 및 키워드를 함께 사용할 수는 없습니다. 이러한 도구를 개별적으로 사용하여 쿼리를 조정하고, 중요한 정보 유형에서 유용할 수 있는 키워드를 확인합니다.

### <a name="kql-query"></a>KQL 쿼리

(^|\\b)([a-zA-Z0-9\_\\-\\.]+)@([a-zA-Z0-9\_\\-\\.]+)\\.([a-zA-Z]{2,5})($|\\b)

참고:

-   근접 검색에는 NEAR 및 ONEAR을 사용할 수 있습니다.

-   그렇지만 KQL은 Regex 클래스가 있는 쿼리(예: IdRef="Regex\_email\_address")를 지원하지 않습니다.

### <a name="keywords"></a>키워드

각 키워드를 별도 줄에 입력합니다. 예제 키워드:

-   전자 메일 주소

-   메일

-   연락처

-   보낸 사람

-   받는 사람

-   참조

-   숨은 참조

이 예제에서는 키워드가 필요하지 않으며 잘못된 가양성 결과를 많이 생성한다는 것을 알 수 있습니다.

### <a name="step-2--create-a-new-custom-sensitive-information-type"></a>2단계 - 새 사용자 지정 중요한 정보 유형 만들기

KQL 쿼리 및 키워드를 사용하여 중요한 정보를 식별한 후에 이러한 정보를 사용하여 새 사용자 지정 중요한 정보 유형을 만듭니다. 많은 경우에 적절한 수준의 정확도를 얻기 위해 정교한 중요한 정보 유형이 필요합니다. 그런 후 콘텐츠 검색, DLP 정책 및 기타 도구, 다른 KQL 쿼리 내에서 이러한 사용자 지정 중요한 정보 유형을 사용할 수 있습니다.

모범 사례는 기존의 중요한 정보 유형을 기준으로 새 중요한 정보 유형을 만드는 것입니다. 이 문서 앞부분에 설명된 것과 동일한 프로세스를 사용하세요.

### <a name="example--create-a-new-sensitive-information-for-email-addresses"></a>예제 - 전자 메일 주소에 대한 새 중요한 정보 만들기 

전자 메일 주소가 간단하기 때문에 계속 예제로 사용하겠습니다. 다음 표에서는 새 전자 메일 중요한 정보 유형에 대해 권장되는 수정 내용을 자세히 보여 줍니다.

<table>
<thead>
<tr class="header">
<th align="left"><strong>단계</strong></th>
<th align="left"><strong>수정 </strong></th>
<th align="left"><strong>예제 XML 구문</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">1</td>
<td align="left">IdRef 속성 설정
<p>&lt;Entity&gt; 요소 내에서 idRef 속성이 고유한 값이 되도록 &lt;IdMatch&gt; 요소를 수정합니다. 이 값은 전자 메일 주소를 찾는 정규식을 정의하는 요소를 가리킵니다.</p></td>
<td align="left">IdRef=&quot;Regex_email_address&quot;</td>
</tr>
<tr class="even">
<td align="left">2</td>
<td align="left"><p>근접 특성</p>
<p>&lt;Entity&gt; 요소의 patternProximity 값을 300으로 지정해서 시작합니다.</p></td>
<td align="left">patternsProximity=&quot;300&quot;</td>
</tr>
<tr class="odd">
<td align="left">3</td>
<td align="left"><p>신뢰 수준</p>
<p>recommendedConfidence 속성을 정확한 일치 항목을 찾을 수 있다고 생각되는 신뢰도로 설정합니다. 보다 정확한 결과를 가져오기 위해서는 대표적인 데이터 집합을 사용해서 테스트해야 할 수 있습니다. 초기 설정으로 이 값을 75로 설정합니다.</p></td>
<td align="left"><p>recommendedConfidence=&quot;75&quot;&gt;</p>
<p>이러한 결합된 처음 세 가지 요소에 대한 결과 XML은 다음과 같습니다.</p>
<p>&lt;Entity id=&quot;42e6348e-27f0-4774-9604-d470cb3e219a&quot; patternsProximity=&quot;300&quot; recommendedConfidence=&quot;75&quot;&gt;</p>
<p>&lt;Pattern confidenceLevel=&quot;75&quot;&gt;</p>
<p>&lt;IdMatch idRef=&quot;Regex_email_address&quot; /&gt;</p>
<p>&lt;Any minMatches=&quot;1&quot;&gt;</p>
<p>&lt;Match idRef=&quot;Keyword_email_terms&quot; /&gt;</p>
<p>&lt;/Any&gt;</p>
<p>&lt;/Pattern&gt;</p>
<p>&lt;/Entity&gt;</p></td>
</tr>
<tr class="even">
<td align="left">4</td>
<td align="left"><p>Regex 요소</p>
<p>새 &lt;Regex&gt; 요소를 전자 메일 주소를 식별하는 데 사용되는 정규식을 정의하는 &lt;Entity&gt; 요소 바로 아래에 추가합니다.</p></td>
<td align="left">&lt;Regex id=&quot;Regex_email_address&quot;&gt;(^|\b)([a-zA-Z0-9_\-\.]+)@([a-zA-Z0-9_\-\.]+)\.([a-zA-Z]{2,5})($|\b)&lt;/Regex&gt;</td>
</tr>
<tr class="odd">
<td align="left">5</td>
<td align="left"><p>키워드</p>
<p>새 &lt;Keyword&gt; 요소를 전자 메일 주소 관련 키워드의 목록을 정의하는 &lt;Regex&gt; 요소 아래에 추가합니다. &lt;Keyword&gt; 요소의 ID 값이 &lt;Entity&gt;&lt;Pattern&gt; 요소의 &lt;Match idRef&gt; 값과 일치하는지 확인합니다. 필요한 경우 사용자 고유의 키워드를 계속 추가할 수 있습니다.</p>
<p>키워드를 전자 메일 중요한 정보 유형에 포함할 필요는 없습니다. 예제로 제공되기 때문입니다.</p></td>
<td align="left"><p>&lt;Keyword id=&quot;Keyword_email_terms&quot;&gt;</p>
<p>&lt;Group&gt;</p>
<p>&lt;Term&gt;email&lt;/Term&gt;</p>
<p>&lt;Term&gt;email address&lt;/Term&gt;</p>
<p>&lt;Term&gt;contact&lt;/Term&gt;</p>
<p>&lt;/Group&gt;</p>
<p>&lt;/Keyword&gt;</p></td>
</tr>
<tr class="even">
<td align="left">6</td>
<td align="left"><p>LocalizedStrings 요소</p>
<p>&lt;LocalizedStrings&gt;&lt;Resource&gt; 요소에서 중요한 정보 유형을 식별하는 고유한 이름이 있는지 확인합니다.</p></td>
<td align="left"><p>&lt;LocalizedStrings&gt;</p>
<p>&lt;Resource idRef=&quot;42e6348e-27f0-4774-9604-d470cb3e219a&quot;&gt;</p>
<p>&lt;Name default=&quot;true&quot; langcode=&quot;en-us&quot;&gt;Email Address&lt;/Name&gt;</p>
<p>&lt;Description default=&quot;true&quot; langcode=&quot;en-us&quot;&gt;Detects email addresses.&lt;/Description&gt;</p>
<p>&lt;/Resource&gt;</p>
<p>&lt;/LocalizedStrings&gt;</p></td>
</tr>
</tbody>
</table>

## <a name="create-a-new-sensitive-information-type-with-example-powershell-and-xml-file--contoso-customer-number"></a>예제 PowerShell 및 XML 파일을 사용하여 새 중요한 정보 유형 만들기 — Contoso 고객 번호

Contoso는 CCN(Contoso 고객 번호)을 사용하여 고객 데이터베이스에 있는 각 고객을 식별합니다. CCN은 다음 분류법으로 구성됩니다.

-   레코드가 생성된 연도를 나타내는 두 자리 숫자. Contoso는 2002년에 설립되었으므로 가장 앞에 나올 수 있는 값은 02입니다.

-   레코드를 만든 파트너 에이전시를 나타내는 세 자리 숫자. 가능한 에이전시 값의 범위는 000에서 999까지입니다.

-   사업 부문을 나타내는 영문자. 가능한 값은 a-z이며 대/소문자를 구분하지 않습니다.

-   네 자리 일련 번호. 가능한 일련 번호 값의 범위는 0000에서 9999까지입니다.

예제 CCN:

> 15080P9562
>
> 14040O1119
>
> 15020J8317
>
> 14050E2330
>
> 16050E2166
>
> 17040O1118

Contoso는 내부 서신, 외부 서신, 문서 등에서 항상 CCN을 사용하여 고객을 참조합니다. Office 365에서는 사용자 지정 중요한 정보 유형을 만들어 CCN의 사용을 감지할 수 있으므로 이러한 형식의 개인 데이터를 사용할 때 보호 기능을 적용할 수 있습니다.

### <a name="create-a-new-sensitive-information-type-for-contoso-customer-number"></a>Contoso 고객 번호에 대한 새 중요한 정보 유형 만들기

<table>
<thead>
<tr class="header">
<th align="left"><strong>단계</strong></th>
<th align="left"><strong>작업</strong></th>
<th align="left"><strong>결과</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">1</td>
<td align="left">Contoso에서는 PowerShell 및 콘텐츠 검색을 사용하여 CCN 예제 집합과 일치하는 문서를 찾습니다.</td>
<td align="left">

<p>#Office 365 보안 및 준수 센터에 연결</p>
<p>$adminUser = &quot;alland@contoso.com&quot;</p>
<p>Connect-IPPSSession -UserPrincipalName $adminUser</p>
<p>#만들기 및 샘플 데이터 검색 시작</p>
<p>$searchName = &quot;Sample Customer Information Search&quot;</p>
<p>$searchQuery = &quot;15080P9562 OR 14040O1119 OR 15020J8317 OR 14050E2330 OR 16050E2166 OR 17040O1118&quot;</p>
<p>New-ComplianceSearch -Name $searchName -SharePointLocation All -ExchangeLocation All -ContentMatchQuery $searchQuery</p>
<p>Start-ComplianceSearch -Identity $searchName</p>
</td>
</tr>
<tr class="even">
<td align="left">2</td>
<td align="left">Contoso에서는 결과를 분석합니다. CCN이 사용될 때마다 EU 형식이 지정된 날짜가 사용되고 이러한 키워드 중 하나가 300 문자의 근접성 내에서도 사용되었습니다.</td>
<td align="left">customer number, customer no, customer #, customer#, Contoso customer</td>
</tr>
<tr class="odd">
<td align="left">3</td>
<td align="left">Contoso는 CCN를 식별하기 위해 다음과 같은 정규식(RegEx) 패턴을 개발했습니다.</td>
<td align="left">[0-1][0-9][0-9]{3}[A-Za-z][0-9]{4}</td>
</tr>
<tr class="even">
<td align="left">4</td>
<td align="left">Contoso는 다양한 자회사에서 사용되는 형식에서 EU 날짜를 식별하기 위해 다음과 같은 정규식(RegEx) 패턴을 개발했습니다.</td>
<td align="left">
````xml
(0?[1-9]|[12][0-9]|3[0-1])[\/-](0?[1-9]|1[0-2]|j\x00e4n(uar)?|jan(uary|uari|uar|eiro|vier|v)?|ene(ro)?|genn(aio)?|‌ feb(ruary|ruari|rero|braio|ruar|br)?|f\x00e9vr(ier)?|fev(ereiro)?|mar(zo|o|ch|s)?|m\x00e4rz|maart|‌ apr(ile|il)?|abr(il)?|avril|may(o)?|magg(io)?|mai|mei|mai(o)?|jun(io|i|e|ho)?|giugno|juin|jul(y|io|i|ho)?|lu(glio)?|juil(let)?|ag(o|osto)?|aug(ustus|ust)?|ao\x00fbt|sep|sept(ember|iembre|embre)?|sett(embre)?|set(embro)?|‌ oct(ober|ubre|obre)?|ott(obre)?|okt(ober)?|out(ubro)?|nov(ember|iembre|embre|embro)?|dec(ember)?|‌ dic(iembre|embre)?|dez(ember|embro)?|d\x00e9c(embre)?)[ \/-](19|20)?[0-9]{2}
````
</td>
</tr>
<tr class="odd">
<td align="left">5</td>
<td align="left">Contoso는 PowerShell을 사용하여 3개의 고유한 GUID를 생성합니다.</td>
<td align="left"><p>#Generate a unique GUID for RulePack Id, Publisher Id, and Entity Id</p>
<p>[guid]::NewGuid().Guid</p>
<p>[guid]::NewGuid().Guid</p>
<p>[guid]::NewGuid().Guid</p></td>
</tr>
<tr class="even">
<td align="left">6</td>
<td align="left">Contoso는 중요한 항목 유형 규칙에 대해 다음과 같은 매개 변수를 정의합니다.</td>
<td align="left"><p>Name: Contoso Customer Number (CCN)</p>
<p>Description: Contoso Customer Number (CCN) that looks for additional keywords and EU formatted date</p></td>
</tr>
<tr class="odd">
<td align="left">7</td>
<td align="left">Contoso는 CCN(Contoso 고객 번호)을 검색하기 위한 새 중요한 정보 유형에 대해 XML 파일을 만들고 UTF-8 인코딩을 사용하는 C:\Scripts\ContosoCCN.xml으로 로컬 파일 시스템에 저장합니다.</td>
<td align="left">이 표 아래의 XML 파일을 참조하세요.</td>
</tr>
<tr class="even">
<td align="left">8</td>
<td align="left">Contoso는 다음 PowerShell을 사용하여 사용자 지정 중요한 정보 유형을 만듭니다.</td>
<td align="left"><p>#Office 365 보안 및 준수 센터에 연결</p>
<p>$adminUser = &quot;alland@contoso.com&quot;</p>
<p>Connect-IPPSSession -UserPrincipalName $adminUser</p>
<p>#새 중요한 정보 유형 만들기</p>
<p>New-DlpSensitiveInformationTypeRulePackage -FileData (Get-Content -Path &quot;C:\Scripts\ContosoCCN.xml&quot; -Encoding Byte -ReadCount 0)</p></td>
</tr>
</tbody>
</table>

### <a name="example-xml-file-for-the-new-sensitive-information-type-step-7"></a>새 중요 한 정보 유형에 대한 예제 XML 파일(7단계)
```xml
\<?xml version="1.0" encoding="utf-8"?\>

\<RulePackage xmlns="http://schemas.microsoft.com/office/2011/mce"\>

\<RulePack id="130ae63b-a91e-4a12-9e02-a90e36a83d7f"\>

\<Version major="1" minor="0" build="0" revision="0" /\>

\<Publisher id="47148982-defd-42a1-890a-7b9472099f1f" /\>

\<Details defaultLangCode="en"\>

\<LocalizedDetails langcode="en"\>

\<PublisherName\>Contoso Ltd.\</PublisherName\>

\<Name\>Contoso Rule Package\</Name\>

\<Description\>Defines Contoso's custom set of classification rules\</Description\>

\</LocalizedDetails\>

\</Details\>

\</RulePack\>

\<Rules\>

\<!-- Contoso Customer Number (CCN) --\>

\<Entity id="a91f9a2e-6cfc-4622-8c5d-954875aa5b2b" patternsProximity="300" recommendedConfidence="85"\>

\<Pattern confidenceLevel="85"\>

\<IdMatch idRef="Regex\_contoso\_ccn" /\>

\<Match idRef="Keyword\_contoso\_ccn" /\>

\<Match idRef="Regex\_eu\_date" /\>

\</Pattern\>

\</Entity\>

\<Regex id="Regex\_contoso\_ccn"\>[0-1][0-9][0-9]{3}[A-Za-z][0-9]{4}\</Regex\>

\<Keyword id="Keyword\_contoso\_ccn"\>

\<Group matchStyle="word"\>

\<Term caseSensitive="false"\>customer number\</Term\>

\<Term caseSensitive="false"\>customer no\</Term\>

\<Term caseSensitive="false"\>customer \#\</Term\>

\<Term caseSensitive="false"\>customer\#\</Term\>

\<Term caseSensitive="false"\>Contoso customer\</Term\>

\</Group\>

\</Keyword\>

\<Regex id="Regex\_eu\_date"\> (0?[1-9]|[12][0-9]|3[0-1])[\\/-](0?[1-9]|1[0-2]|j\\x00e4n(uar)?|jan(uary|uari|uar|eiro|vier|v)?|ene(ro)?|genn(aio)?‌ |feb(ruary|ruari|rero|braio|ruar|br)?|f\\x00e9vr(ier)?|fev(ereiro)?|mar(zo|o|ch|s)?|m\\x00e4rz|maart‌|apr(ile|il)?|abr(il)?|avril‌ |may(o)?|magg(io)?|mai|mei|mai(o)?|jun(io|i|e|ho)?|giugno|juin|jul(y|io|i|ho)?|lu(glio)?|juil(let)?|ag(o|osto)?|aug(ustus|ust)?|ao\\x00fbt|sep|sept(ember|iembre|embre)?|sett(embre)?|set(embro)?|oct(ober|ubre|obre)?|ott(obre)?|okt(ober)?|out(ubro)?‌ |nov(ember|iembre|embre|embro)?|dec(ember)?|dic(iembre|embre)?|dez(ember|embro)?|d\\x00e9c(embre)?)[ \\/-](19|20)?[0-9]{2}\</Regex\>

\<LocalizedStrings\>

\<Resource idRef="a91f9a2e-6cfc-4622-8c5d-954875aa5b2b"\>

\<Name default="true" langcode="en-us"\>Contoso Customer Number (CCN)\</Name\>

\<Description default="true" langcode="en-us"\>Contoso Customer Number (CCN) that looks for additional keywords and EU formatted date\</Description\>

\</Resource\>

\</LocalizedStrings\>

\</Rules\>

\</RulePackage\>
```
