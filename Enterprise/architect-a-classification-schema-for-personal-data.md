---
title: "개인 데이터에 대한 분류 스키마 설계"
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 2/7/2018
ms.audience: ITPro
ms.topic: overview
ms.collection:
- Strat_O365_Enterprise
- Ent_O365
ms.service: o365-solutions
localization_priority: Priority
ms.custom:
- GDPR
- Strat_O365_Enterprise
ms.assetid: 
description: "조직이 GDPR 계획의 일부로 레이블을 구현하는지 여부를 확인합니다."
ms.openlocfilehash: ee3c01cd4fd99fcc62bbde445eeb3018bb05f586
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2018
---
# <a name="architect-a-classification-schema-for-personal-data"></a>개인 데이터에 대한 분류 스키마 설계

이 시리즈의 이전 문서는 중요한 정보 유형을 사용하여 GDPR이 적용되는 개인 데이터를 식별하는 내용을 집중적으로 소개했습니다. 중요한 정보 유형은 분류 형태를 갖습니다. 이 분류로도 충분합니다. 그러나 대부분의 조직에서는 레이블을 사용하여 보다 광범위한 데이터 거버넌스 전략을 구현합니다. 이 항목을 사용하여 레이블도 GDPR 계획의 일부로 구 현할 것인지를 결정합니다. 그렇다면 이 항목에서 몇 가지 지침과 예제를 확인하세요.

참고: 조직에 대한 분류 스키마를 정의하고 정책, 레이블 및 조건을 구성하려면 신중하게 계획하고 준비해야 합니다. 또한 이 과정이 IT 부서에서 추진하는 프로세스가 아니라는 점도 인식해야 합니다. 법률 및 규정 준수 팀과 합력하여 조직 데이터에 적절한 분류 및 레이블링 스키마를 개발하세요.

## <a name="decide-if-you-are-using-labels-in-addition-to-sensitive-data-types"></a>중요한 데이터 유형 외에 레이블도 사용할지 결정

개인 정보에 대한 Office 365의 분류법 2가지 중 하나를 사용할 수 있습니다. 이러한 두 방법은 GDPR 보호에 사용할 수 있습니다. 분류에 중요한 정보 유형 1가지만 사용하기로 결정한 경우 이 항목의 나머지 부분은 건너뛸 수 있습니다.

다음 옵션 중 하나를 선택합니다.

### <a name="option-1-use-only-office-365-sensitive-information-types"></a>옵션 1: Office 365 중요한 정보 유형만 사용

-   중요한 정보 유형은 GDPR 및 기타 규제 유형에 따른 개인 데이터를 식별하고 보호하는 데 적합합니다.

-   다음은 조직이 아직 레이블을 사용하여 보다 광범위한 데이터 거버넌스 계획을 구현하지 않았거나 앞으로 구현할 계획인 경우 다음 방법을 사용하는 것이 더 간단합니다.

-   DLP 규칙에 잘 작동합니다(Office 레이블도 DLP 규칙에 잘 작동함).

-   나중에는 Cloud App Security와 함께 작동될 예정이므로 기타 SaaS 앱에서 중요한 정보를 검색할 수 있습니다.

### <a name="option-2-use-sensitive-information-types--office-labels"></a>옵션 2: 중요한 정보 유형 + Office 레이블 사용

-   GDPR이 적용되는 개인 데이터에 자동으로 레이블을 적용하려면 중요한 정보 유형이 필요하므로 필수 구성 요소가 됩니다.

-   Office 레이블을 사용하여 GDPR이 적용되는 개인 데이터를 조직의 보다 광범위한 데이터 거버넌스 계획에 포함할 수 있습니다.

-   나중에 Office 레이블은 Azure Information Protection 레이블을 통합된 분류 및 레이블링 엔진에 집약할 것입니다.

## <a name="develop-a-label-schema-that-includes-personal-data"></a>개인 데이터를 포함하는 레이블 스키마 개발

레이블 및 보호를 적용하는 기술을 사용하기 전에 먼저 조직 전반에서 분류 스키마를 정의합니다. 조직에 이미 분류 스키마가 있을 수도 있습니다. 이 경우 개인 데이터를 보다 쉽게 추가할 수 있습니다. 이 항목에는 예제 분류 스키마가 포함되어 있습니다. 필요한 경우 이 스키마를 시작점으로 사용할 수 있습니다.

### <a name="getting-started"></a>시작

먼저 구현할 레이블의 수와 이름을 결정합니다. 사용할 기술과 레이블 적용 방식을 걱정할 필요 없이 이 작업을 수행할 수 있습니다. 온-프레미스 및 기타 클라우드 서비스에 있는 데이터를 포함하여 조직 전체에 범용으로 이 스키마를 적용하세요.

### <a name="recommendations"></a>추천 

정책, 레이블 및 조건을 디자인하고 구현할 때는 다음 권장 사항을 고려하세요.

-   기존 분류 스키마 사용(있는 경우) - 많은 조직에서는 이미 특정 형태의 데이터 분류를 사용하고 있습니다. 기존 레이블 스키마를 주의 깊게 평가하고, 가능한 경우 있는 그대로 사용합니다. 최종 사용자가 인식할 수 있는 익숙한 레이블을 사용하면 채택에 도움이 됩니다.

-   기본 정책 및 레이블로 시작 - 모든 솔루션은 미리 정의된 정책 및 레이블 집합과 함께 제공됩니다. 조직의 법률 및 비즈니스 요구 사항에 따라 이러한 항목을 주의 깊게 평가하고, 새 항목을 사용하는 대신 기존 항목을 사용하는 것이 좋습니다.

-   소규모 사용 — 만들 수 있는 레이블 수에는 거의 제한이 없습니다. 그러나 많은 수의 레이블 및 하위 레이블은 채택에 부정적인 영향을 줍니다. 선택 항목이 너무 많으면 없는 것과 같은 효과를 가져옵니다.

-   시나리오 및 사용 사례 사용 - 조직 내에서 일반적인 사용 사례를 식별하고 GDPR에서 파생된 시나리오를 사용하여 구상 중인 레이블 및 분류 구성이 실제로 작동할지 확인합니다.

-   새 레이블의 모든 요청에 대해 모든 시나리오나 사용 사례에 정말로 새 레이블이 필요한지 또는 기존 레이블을 사용할 수 있는지 질문합니다. 레이블 수를 최소로 유지하면 채택 가능성이 높아집니다.

-   핵심 부서에 대해 하위 레이블 사용 - 일부 부서에서는 특정 레이블이 필요한 고유한 요구가 있습니다. 이러한 레이블을 기존 레이블에 대한 하위 레이블로 정의하고, 전역적이 아닌 사용자 그룹에 할당된 범위 지정 정책을 사용하는 것이 좋습니다.

-   범위가 지정된 정책 고려 - 사용자 일부를 대상으로 하는 정책을 사용하면 "레이블 오버로드”가 방지됩니다. 범위가 지정된 정책을 사용하면 해당 특정 부서에 작동하는 직원에게만 역할 또는 부서별 (하위) 레이블을 할당할 수 있습니다.

-   의미 있는 레이블 이름 사용 - 전문 용어, 표준 또는 약어를 레이블 이름으로 사용하지 않는 것이 좋습니다. 최종 사용자에게 잘 기억나는 이름을 사용하면 채택이 높아집니다., PII, PCI, HIPAA, LBI, MBI 및 HBI와 같은 레이블을 사용하지 말고, 업무 외, 공개, 일반, 기밀 및 극비와 같은 이름을 고려하세요.

### <a name="example-classification-schema"></a>분류 스키마 예제

<table>
<thead>
<tr class="header">
<th align="left"><strong>레이블 이름</strong></th>
<th align="left"><strong>설명</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">개인</td>
<td align="left">개인 용도 전용인 업무 외 데이터입니다.</td>
</tr>
<tr class="even">
<td align="left">공용</td>
<td align="left">공용 사용을 위해 특수하게 준비되고 승인된 비즈니스 데이터입니다.</td>
</tr>
<tr class="odd">
<td align="left">고객 데이터</td>
<td align="left">개인 식별이 가능한 정보를 포함하는 비즈니스 데이터입니다. 신용 카드 번호, 은행 계좌 번호, 주민 등록 번호를 예로 들 수 있습니다.</td>
</tr>
<tr class="even">
<td align="left">HR 데이터</td>
<td align="left">직원 번호 및 급여 데이터와 같은 Contoso 직원에 대한 인사 데이터입니다.</td>
</tr>
<tr class="odd">
<td align="left">기밀</td>
<td align="left">권한 없는 사용자와 공유될 경우 비즈니스를 손상시킬 수 있는 중요한 비즈니스 데이터입니다. 계약, 보안 보고서, 예측된 요약 및 영업 계정 데이터를 예로 들 수 있습니다.</td>
</tr>
<tr class="even">
<td align="left">극비</td>
<td align="left">권한 없는 사용자와 공유될 경우 비즈니스를 손상시킬 수 있는 매우 중요한 비즈니스 데이터입니다. 고객 정보, 암호, 소스 코드 및 미리 발표된 재무 보고서를 예로 들 수 있습니다.</td>
</tr>
</tbody>
</table>

## <a name="define-a-taxonomy-and-search-criteria-for-each-label"></a>각 레이블에 대해 분류 및 검색 조건 정의

조직에 대한 분류 스키마를 개발한 후에는 분류법을 개발하고 이 데이터를 찾기 위한 검색 조건을 개발해야 합니다. 개인 데이터에 대해 중요한 정보 유형을 식별하고, 작업 환경에 맞게 중요한 정보 유형을 사용자 지정하거나 새로 만들어 이 작업을 이미 완료했을 것입니다.

다음 표에서는 조직에 대한 예제 스키마, 분류법 및 검색 조건을 제공합니다. 가장 덜 민감한 레이블부터 가장 민감한 레이블까지 민감도 수준에 따라 정렬하여 여러 레이블 조건과 일치하는 데이터에 적절한 레이블이 할당되도록 합니다.

참고: 구성 예제는 그림 설명을 위한 예로 제공될 뿐이며 배포 지침 또는 참조로 제공된 것이 아닙니다.

중요한 지침은 GDPR 규정에 따라 개인 데이터를 분류하기 위해 수행한 작업이 전체 조직의 목표에 부합되도록 해야 한다는 것입니다.

### <a name="example-schema-taxonomy-and-search-criteria"></a>예제 스키마, 분류법 및 검색 조건

<table>
<thead>
<tr class="header">
<th align="left"><strong>레이블</strong></th>
<th align="left"><strong>분류</strong></th>
<th align="left"><strong>방법</strong></th>
<th align="left"><strong>검색 구문</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">개인</td>
<td align="left">최종 사용자가 수동으로 개인 레이블을 지정한 문서입니다.</td>
<td align="left">수동</td>
<td align="left">Documents manually labelled personal by the end user.</td>
</tr>
<tr class="even">
<td align="left">공용</td>
<td align="left">대/소문자를 구분하지 않는 Approved for Public Release ##/####를 포함하는 문서입니다. 여기서 #은 임의 숫자를 나타냅니다.</td>
<td align="left"><p>KQL</p>
<p>정규식</p></td>
<td align="left"><p>KQL — Approved for Public Release*</p>
<p>RegEx — (?i)(\bApproved for Public Release \d{2}\/\d{4}\b)</p></td>
</tr>
<tr class="odd">
<td align="left">고객 데이터</td>
<td align="left">EU 거주민 데이터에 대한 중요한 정보 유형</td>
<td align="left">중요한 정보 유형</td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left">인사 - 직원 데이터</td>
<td align="left">CONTOSO-9##### 형식의 대/소문자 구분 직원 ID를 포함하는 문서입니다.여기서 #은 임의 숫자를 나타냅니다.</td>
<td align="left"><p>KQL</p>
<p>정규식</p></td>
<td align="left"><p>KQL — CONTOSO-9*</p>
<p>RegEx — (\bCONTOSO-9\d{5}\b)</p></td>
</tr>
<tr class="odd">
<td align="left">인사 - 급여 데이터</td>
<td align="left">키워드(대/소문자 구분 안 함) Contoso AND 키워드(대/소문자 구분 안 함) Salary OR Compensation을 포함하는 문서입니다.</td>
<td align="left"><p>KQL</p>
<p>정규식</p></td>
<td align="left"><p>KQL — Contoso AND (Salary OR Compensation)</p>
<p>RegEx — (\bCONTOSO-9\d{5}\b)</p></td>
</tr>
<tr class="even">
<td align="left">기밀</td>
<td align="left">구(대/소문자 구문 안 함) Contoso Confidential을 포함하는 문서입니다.</td>
<td align="left"><p>KQL</p>
<p>정규식</p></td>
<td align="left"><p>KQL — Contoso Confidential</p>
<p>RegEx — (?i)(\bContoso Confidential\b)</p></td>
</tr>
<tr class="odd">
<td align="left">극비</td>
<td align="left">구(대/소문자 구분) Contoso Secret 또는 Secret-C####을 포함하는 문서입니다. 여기서 #은 임의 숫자를 나타냅니다.</td>
<td align="left"><p>KQL</p>
<p>정규식</p></td>
<td align="left"><p>KQL — Contoso Secret OR Secret-C*</p>
<p>RegEx — (?i)(\bContoso Secret\b)|(\bSecret-C\d{4}\b)</p></td>
</tr>
</tbody>
</table>
