---
title: 개인 데이터에 대한 분류 스키마 설계
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 2/7/2018
ms.audience: ITPro
ms.topic: overview
ms.collection:
- Strat_O365_Enterprise
- Ent_O365
- GDPR
ms.service: o365-solutions
localization_priority: Priority
ms.custom: ''
ms.assetid: ''
description: 조직이 GDPR 계획의 일부로 레이블을 구현하는지 여부를 확인합니다.
ms.openlocfilehash: 5a462c6e63c72d76fe11d1a41df02cc2bc6f249d
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
---
# <a name="architect-a-classification-schema-for-personal-data"></a><span data-ttu-id="e29dc-103">개인 데이터에 대한 분류 스키마 설계</span><span class="sxs-lookup"><span data-stu-id="e29dc-103">Architect a classification schema for personal data</span></span>

<span data-ttu-id="e29dc-p101">이 시리즈의 이전 문서는 중요한 정보 유형을 사용하여 GDPR이 적용되는 개인 데이터를 식별하는 내용을 집중적으로 소개했습니다. 중요한 정보 유형은 분류 형태를 갖습니다. 이 분류로도 충분합니다. 그러나 대부분의 조직에서는 레이블을 사용하여 보다 광범위한 데이터 거버넌스 전략을 구현합니다. 이 항목을 사용하여 레이블도 GDPR 계획의 일부로 구 현할 것인지를 결정합니다. 그렇다면 이 항목에서 몇 가지 지침과 예제를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="e29dc-p101">Previous articles in this series focus on using sensitive information types to identify personal data that is subject to GDPR. Sensitive information types are a form of classification. This might be all the classification you need. However, many organizations implement a broader data governance strategy using labels. Use this topic to decide if you also want to implement labels as part of your GDPR plan. If you do, this topic provides some guidance and examples.</span></span>

<span data-ttu-id="e29dc-p102">참고: 조직에 대한 분류 스키마를 정의하고 정책, 레이블 및 조건을 구성하려면 신중하게 계획하고 준비해야 합니다. 또한 이 과정이 IT 부서에서 추진하는 프로세스가 아니라는 점도 인식해야 합니다. 법률 및 규정 준수 팀과 합력하여 조직 데이터에 적절한 분류 및 레이블링 스키마를 개발하세요.</span><span class="sxs-lookup"><span data-stu-id="e29dc-p102">Note: Defining a classification schema for an organization and configuring policies, labels, and conditions requires careful planning and preparation. It is important to realize that this is not an IT driven process. Be sure to work with your legal and compliance team to develop an appropriate classification and labeling schema for your organization’s data.</span></span>

## <a name="decide-if-you-are-using-labels-in-addition-to-sensitive-data-types"></a><span data-ttu-id="e29dc-113">중요한 데이터 유형 외에 레이블도 사용할지 결정</span><span class="sxs-lookup"><span data-stu-id="e29dc-113">Decide if you are using labels in addition to sensitive data types</span></span>

<span data-ttu-id="e29dc-p103">개인 정보에 대한 Office 365의 분류법 2가지 중 하나를 사용할 수 있습니다. 이러한 두 방법은 GDPR 보호에 사용할 수 있습니다. 분류에 중요한 정보 유형 1가지만 사용하기로 결정한 경우 이 항목의 나머지 부분은 건너뛸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e29dc-p103">You can take one of two approaches for classification in Office 365 for personal information. Either of these can be used for GDPR protection. If decide to use only sensitive information types for classification, you can skip the rest of this topic.</span></span>

<span data-ttu-id="e29dc-117">다음 옵션 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e29dc-117">Choose one of the following options.</span></span>

### <a name="option-1-use-only-office-365-sensitive-information-types"></a><span data-ttu-id="e29dc-118">옵션 1: Office 365 중요한 정보 유형만 사용</span><span class="sxs-lookup"><span data-stu-id="e29dc-118">Option 1: Use only Office 365 sensitive information types</span></span>

-   <span data-ttu-id="e29dc-119">중요한 정보 유형은 GDPR 및 기타 규제 유형에 따른 개인 데이터를 식별하고 보호하는 데 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="e29dc-119">Sensitive information types work well to identify and protect personal data subject to GDPR and other types of regulations.</span></span>

-   <span data-ttu-id="e29dc-120">다음은 조직이 아직 레이블을 사용하여 보다 광범위한 데이터 거버넌스 계획을 구현하지 않았거나 앞으로 구현할 계획인 경우 다음 방법을 사용하는 것이 더 간단합니다.</span><span class="sxs-lookup"><span data-stu-id="e29dc-120">These are simpler to use if your organization doesn’t already have or plan to implement a broader data governance plan using labels.</span></span>

-   <span data-ttu-id="e29dc-121">DLP 규칙에 잘 작동합니다(Office 레이블도 DLP 규칙에 잘 작동함).</span><span class="sxs-lookup"><span data-stu-id="e29dc-121">These work with DLP rules (so do Office labels).</span></span>

-   <span data-ttu-id="e29dc-122">나중에는 Cloud App Security와 함께 작동될 예정이므로 기타 SaaS 앱에서 중요한 정보를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e29dc-122">In the future these will work with Cloud App Security so you can detect sensitive information in other SaaS apps.</span></span>

### <a name="option-2-use-sensitive-information-types--office-labels"></a><span data-ttu-id="e29dc-123">옵션 2: 중요한 정보 유형 + Office 레이블 사용</span><span class="sxs-lookup"><span data-stu-id="e29dc-123">Option 2: Use sensitive information types + Office labels</span></span>

-   <span data-ttu-id="e29dc-124">GDPR이 적용되는 개인 데이터에 자동으로 레이블을 적용하려면 중요한 정보 유형이 필요하므로 필수 구성 요소가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e29dc-124">You’ll need sensitive information types to automatically apply labels to personal data that is subject to GDPR, so these are a prerequisite.</span></span>

-   <span data-ttu-id="e29dc-125">Office 레이블을 사용하여 GDPR이 적용되는 개인 데이터를 조직의 보다 광범위한 데이터 거버넌스 계획에 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e29dc-125">Using Office labels allows you to include personal data that is subject to GDPR into a broader data governance plan for your organization.</span></span>

-   <span data-ttu-id="e29dc-126">나중에 Office 레이블은 Azure Information Protection 레이블을 통합된 분류 및 레이블링 엔진에 집약할 것입니다.</span><span class="sxs-lookup"><span data-stu-id="e29dc-126">Later, Office labels will converge with Azure Information Protection labels into a unified classification and labeling engine.</span></span>

## <a name="develop-a-label-schema-that-includes-personal-data"></a><span data-ttu-id="e29dc-127">개인 데이터를 포함하는 레이블 스키마 개발</span><span class="sxs-lookup"><span data-stu-id="e29dc-127">Develop a label schema that includes personal data</span></span>

<span data-ttu-id="e29dc-p104">레이블 및 보호를 적용하는 기술을 사용하기 전에 먼저 조직 전반에서 분류 스키마를 정의합니다. 조직에 이미 분류 스키마가 있을 수도 있습니다. 이 경우 개인 데이터를 보다 쉽게 추가할 수 있습니다. 이 항목에는 예제 분류 스키마가 포함되어 있습니다. 필요한 경우 이 스키마를 시작점으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e29dc-p104">Before using technical capabilities to apply labels and protection, first work across your organization to define a classification schema. Your organization might already have a classification schema, which makes it easier to add personal data. This topic includes an example classification schema. You can use this as a starting point, if needed.</span></span>

### <a name="getting-started"></a><span data-ttu-id="e29dc-132">시작</span><span class="sxs-lookup"><span data-stu-id="e29dc-132">Getting started</span></span>

<span data-ttu-id="e29dc-p105">먼저 구현할 레이블의 수와 이름을 결정합니다. 사용할 기술과 레이블 적용 방식을 걱정할 필요 없이 이 작업을 수행할 수 있습니다. 온-프레미스 및 기타 클라우드 서비스에 있는 데이터를 포함하여 조직 전체에 범용으로 이 스키마를 적용하세요.</span><span class="sxs-lookup"><span data-stu-id="e29dc-p105">Begin by deciding on the number and names of labels to implement. Do this activity without worrying about which technology to use and how labels will be applied. Apply this schema universally throughout your organization, including data that resides on premises and in other cloud services.</span></span>

### <a name="recommendations"></a><span data-ttu-id="e29dc-136">추천</span><span class="sxs-lookup"><span data-stu-id="e29dc-136">Recommendations</span></span> 

<span data-ttu-id="e29dc-137">정책, 레이블 및 조건을 디자인하고 구현할 때는 다음 권장 사항을 고려하세요.</span><span class="sxs-lookup"><span data-stu-id="e29dc-137">When designing and implementing policies, labels and conditions, consider following these recommendations:</span></span>

-   <span data-ttu-id="e29dc-p106">기존 분류 스키마 사용(있는 경우) - 많은 조직에서는 이미 특정 형태의 데이터 분류를 사용하고 있습니다. 기존 레이블 스키마를 주의 깊게 평가하고, 가능한 경우 있는 그대로 사용합니다. 최종 사용자가 인식할 수 있는 익숙한 레이블을 사용하면 채택에 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e29dc-p106">Use existing classification schema (if any) — Many organizations already are using data classification in some form. Carefully evaluate the existing label schema and if possible use it as is. Using familiar labels that are recognizable to the end-user will drive adoption.</span></span>

-   <span data-ttu-id="e29dc-p107">기본 정책 및 레이블로 시작 - 모든 솔루션은 미리 정의된 정책 및 레이블 집합과 함께 제공됩니다. 조직의 법률 및 비즈니스 요구 사항에 따라 이러한 항목을 주의 깊게 평가하고, 새 항목을 사용하는 대신 기존 항목을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="e29dc-p107">Start with default policies and labels — All solutions come with a set of predefined policies and labels. Carefully evaluate these against the organizations legal and business requirements and consider using them instead of creating new ones.</span></span>

-   <span data-ttu-id="e29dc-p108">소규모 사용 — 만들 수 있는 레이블 수에는 거의 제한이 없습니다. 그러나 많은 수의 레이블 및 하위 레이블은 채택에 부정적인 영향을 줍니다. 선택 항목이 너무 많으면 없는 것과 같은 효과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e29dc-p108">Start small — There is virtually no limit to the number of labels that can be created. However, large numbers of labels and sub-labels will negatively impact the adoption. Too many choices often means no choice at all.</span></span>

-   <span data-ttu-id="e29dc-146">시나리오 및 사용 사례 사용 - 조직 내에서 일반적인 사용 사례를 식별하고 GDPR에서 파생된 시나리오를 사용하여 구상 중인 레이블 및 분류 구성이 실제로 작동할지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e29dc-146">Use scenarios and use cases — Identify common use cases within the organization and use scenarios derived from the GDPR to verify if the envisioned label and classification configuration will work in practice.</span></span>

-   <span data-ttu-id="e29dc-p109">새 레이블의 모든 요청에 대해 모든 시나리오나 사용 사례에 정말로 새 레이블이 필요한지 또는 기존 레이블을 사용할 수 있는지 질문합니다. 레이블 수를 최소로 유지하면 채택 가능성이 높아집니다.</span><span class="sxs-lookup"><span data-stu-id="e29dc-p109">Question every request for a new label, does every scenario or use case really need a new label or can we use what we already have? Keeping the number of labels to a minimum improves adoption.</span></span>

-   <span data-ttu-id="e29dc-p110">핵심 부서에 대해 하위 레이블 사용 - 일부 부서에서는 특정 레이블이 필요한 고유한 요구가 있습니다. 이러한 레이블을 기존 레이블에 대한 하위 레이블로 정의하고, 전역적이 아닌 사용자 그룹에 할당된 범위 지정 정책을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="e29dc-p110">Use sub-labels for key departments, some departments will have specific needs that require specific labels. Define these labels as sub-labels to an existing label and consider using scoped policies that are assigned to user groups instead of globally.</span></span>

-   <span data-ttu-id="e29dc-p111">범위가 지정된 정책 고려 - 사용자 일부를 대상으로 하는 정책을 사용하면 "레이블 오버로드”가 방지됩니다. 범위가 지정된 정책을 사용하면 해당 특정 부서에 작동하는 직원에게만 역할 또는 부서별 (하위) 레이블을 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e29dc-p111">Consider scoped policies, polices targeted at subsets of users will prevent "label overload". A scoped policy enables assigning role or department specific (sub-)labels to just employees that work for that specific department.</span></span>

-   <span data-ttu-id="e29dc-p112">의미 있는 레이블 이름 사용 - 전문 용어, 표준 또는 약어를 레이블 이름으로 사용하지 않는 것이 좋습니다. 최종 사용자에게 잘 기억나는 이름을 사용하면 채택이 높아집니다., PII, PCI, HIPAA, LBI, MBI 및 HBI와 같은 레이블을 사용하지 말고, 업무 외, 공개, 일반, 기밀 및 극비와 같은 이름을 고려하세요.</span><span class="sxs-lookup"><span data-stu-id="e29dc-p112">Use meaningful label names, it is recommended not to use jargon, standards or acronyms as label names. Try to use names that resonate with the end user to improve adoption. Instead of using labels like PII, PCI, HIPAA, LBI, MBI and HBI consider names like Non-Business, Public, General, Confidential and Highly Confidential.</span></span>

### <a name="example-classification-schema"></a><span data-ttu-id="e29dc-156">분류 스키마 예제</span><span class="sxs-lookup"><span data-stu-id="e29dc-156">Example classification schema</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="e29dc-157"><strong>레이블 이름</strong></span><span class="sxs-lookup"><span data-stu-id="e29dc-157"><strong>Label name</strong></span></span></th>
<th align="left"><span data-ttu-id="e29dc-158"><strong>설명</strong></span><span class="sxs-lookup"><span data-stu-id="e29dc-158"><strong>Description</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="e29dc-159">개인</span><span class="sxs-lookup"><span data-stu-id="e29dc-159">Personal</span></span></td>
<td align="left"><span data-ttu-id="e29dc-160">개인 용도 전용인 업무 외 데이터입니다.</span><span class="sxs-lookup"><span data-stu-id="e29dc-160">Non-business data, for personal use only.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="e29dc-161">공용</span><span class="sxs-lookup"><span data-stu-id="e29dc-161">Public</span></span></td>
<td align="left"><span data-ttu-id="e29dc-162">공용 사용을 위해 특수하게 준비되고 승인된 비즈니스 데이터입니다.</span><span class="sxs-lookup"><span data-stu-id="e29dc-162">Business data that is specifically prepared and approved for public consumption.</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="e29dc-163">고객 데이터</span><span class="sxs-lookup"><span data-stu-id="e29dc-163">Customer data</span></span></td>
<td align="left"><span data-ttu-id="e29dc-p113">개인 식별이 가능한 정보를 포함하는 비즈니스 데이터입니다. 신용 카드 번호, 은행 계좌 번호, 주민 등록 번호를 예로 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e29dc-p113">Business data that contains personal identifiable information. Examples are credit card numbers, bank account numbers, and social security numbers.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="e29dc-166">HR 데이터</span><span class="sxs-lookup"><span data-stu-id="e29dc-166">HR data</span></span></td>
<td align="left"><span data-ttu-id="e29dc-167">직원 번호 및 급여 데이터와 같은 Contoso 직원에 대한 인사 데이터입니다.</span><span class="sxs-lookup"><span data-stu-id="e29dc-167">Human Resource data about Contoso employees, such as employee number and salary data.</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="e29dc-168">기밀</span><span class="sxs-lookup"><span data-stu-id="e29dc-168">Confidential</span></span></td>
<td align="left"><span data-ttu-id="e29dc-p114">권한 없는 사용자와 공유될 경우 비즈니스를 손상시킬 수 있는 중요한 비즈니스 데이터입니다. 계약, 보안 보고서, 예측된 요약 및 영업 계정 데이터를 예로 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e29dc-p114">Sensitive business data that could cause damage to the business if shared with unauthorized people. Examples include contracts, security reports, forecast summaries, and sales account data.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="e29dc-171">극비</span><span class="sxs-lookup"><span data-stu-id="e29dc-171">Highly confidential</span></span></td>
<td align="left"><span data-ttu-id="e29dc-p115">권한 없는 사용자와 공유될 경우 비즈니스를 손상시킬 수 있는 매우 중요한 비즈니스 데이터입니다. 고객 정보, 암호, 소스 코드 및 미리 발표된 재무 보고서를 예로 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e29dc-p115">Very sensitive business data that would cause damage to the business if it was shared with unauthorized people. Examples include employee and customer information, passwords, source code, and pre-announced financial reports.</span></span></td>
</tr>
</tbody>
</table>

## <a name="define-a-taxonomy-and-search-criteria-for-each-label"></a><span data-ttu-id="e29dc-174">각 레이블에 대해 분류 및 검색 조건 정의</span><span class="sxs-lookup"><span data-stu-id="e29dc-174">Define a taxonomy and search criteria for each label</span></span>

<span data-ttu-id="e29dc-p116">조직에 대한 분류 스키마를 개발한 후에는 분류법을 개발하고 이 데이터를 찾기 위한 검색 조건을 개발해야 합니다. 개인 데이터에 대해 중요한 정보 유형을 식별하고, 작업 환경에 맞게 중요한 정보 유형을 사용자 지정하거나 새로 만들어 이 작업을 이미 완료했을 것입니다.</span><span class="sxs-lookup"><span data-stu-id="e29dc-p116">After developing a classification schema for your organization, the next step is to develop the taxonomy and search criteria for finding this data. For personal data, you’ve already completed this work by identifying sensitive information types and also by customizing or creating new sensitive information types for your environment.</span></span>

<span data-ttu-id="e29dc-p117">다음 표에서는 조직에 대한 예제 스키마, 분류법 및 검색 조건을 제공합니다. 가장 덜 민감한 레이블부터 가장 민감한 레이블까지 민감도 수준에 따라 정렬하여 여러 레이블 조건과 일치하는 데이터에 적절한 레이블이 할당되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="e29dc-p117">The following table provides an example schema, taxonomy, and search criteria for an organization. The labels are ordered by sensitivity level from least sensitive to most sensitive to ensure that data that matches multiple label conditions is assigned the appropriate label.</span></span>

<span data-ttu-id="e29dc-179">참고: 구성 예제는 그림 설명을 위한 예로 제공될 뿐이며 배포 지침 또는 참조로 제공된 것이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="e29dc-179">Note: The configuration example is provided for illustration only and is not intended as deployment guidance or reference.</span></span>

<span data-ttu-id="e29dc-180">중요한 지침은 GDPR 규정에 따라 개인 데이터를 분류하기 위해 수행한 작업이 전체 조직의 목표에 부합되도록 해야 한다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="e29dc-180">The important takeaway is to ensure that the work you invest to classify personal data for GDPR compliance fits together with the objectives for your entire organization.</span></span>

### <a name="example-schema-taxonomy-and-search-criteria"></a><span data-ttu-id="e29dc-181">예제 스키마, 분류법 및 검색 조건</span><span class="sxs-lookup"><span data-stu-id="e29dc-181">Example schema, taxonomy, and search criteria</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="e29dc-182"><strong>레이블</strong></span><span class="sxs-lookup"><span data-stu-id="e29dc-182"><strong>Label</strong></span></span></th>
<th align="left"><span data-ttu-id="e29dc-183"><strong>분류</strong></span><span class="sxs-lookup"><span data-stu-id="e29dc-183"><strong>Taxonomy</strong></span></span></th>
<th align="left"><span data-ttu-id="e29dc-184"><strong>방법</strong></span><span class="sxs-lookup"><span data-stu-id="e29dc-184"><strong>Method</strong></span></span></th>
<th align="left"><span data-ttu-id="e29dc-185"><strong>검색 구문</strong></span><span class="sxs-lookup"><span data-stu-id="e29dc-185"><strong>Search syntax</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="e29dc-186">개인</span><span class="sxs-lookup"><span data-stu-id="e29dc-186">Personal</span></span></td>
<td align="left"><span data-ttu-id="e29dc-187">최종 사용자가 수동으로 개인 레이블을 지정한 문서입니다.</span><span class="sxs-lookup"><span data-stu-id="e29dc-187">Documents manually labelled personal by the end user.</span></span></td>
<td align="left"><span data-ttu-id="e29dc-188">수동</span><span class="sxs-lookup"><span data-stu-id="e29dc-188">Manual</span></span></td>
<td align="left"><span data-ttu-id="e29dc-189">Documents manually labelled personal by the end user.</span><span class="sxs-lookup"><span data-stu-id="e29dc-189">Documents manually labelled personal by the end user.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="e29dc-190">공용</span><span class="sxs-lookup"><span data-stu-id="e29dc-190">Public</span></span></td>
<td align="left"><span data-ttu-id="e29dc-191">대/소문자를 구분하지 않는 Approved for Public Release ##/####를 포함하는 문서입니다. 여기서 #은 임의 숫자를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e29dc-191">Documents containing the case insensitive phrase Approved for Public Release ##/#### where # represents any digit.</span></span></td>
<td align="left"><p><span data-ttu-id="e29dc-192">KQL</span><span class="sxs-lookup"><span data-stu-id="e29dc-192">KQL</span></span></p>
<p><span data-ttu-id="e29dc-193">정규식</span><span class="sxs-lookup"><span data-stu-id="e29dc-193">RegEx</span></span></p></td>
<td align="left"><p><span data-ttu-id="e29dc-194">KQL — Approved for Public Release\*</span><span class="sxs-lookup"><span data-stu-id="e29dc-194">KQL — Approved for Public Release\*</span></span></p>
<p><span data-ttu-id="e29dc-195">RegEx — (?i)(\bApproved for Public Release \d{2}\/\d{4}\b)</span><span class="sxs-lookup"><span data-stu-id="e29dc-195">RegEx — (?i)(\bApproved for Public Release \d{2}\/\d{4}\b)</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="e29dc-196">고객 데이터</span><span class="sxs-lookup"><span data-stu-id="e29dc-196">Customer data</span></span></td>
<td align="left"><span data-ttu-id="e29dc-197">EU 거주민 데이터에 대한 중요한 정보 유형</span><span class="sxs-lookup"><span data-stu-id="e29dc-197">Sensitive information types for EU citizen data.</span></span></td>
<td align="left"><span data-ttu-id="e29dc-198">중요한 정보 유형</span><span class="sxs-lookup"><span data-stu-id="e29dc-198">Sensitive information types</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="e29dc-199">인사 - 직원 데이터</span><span class="sxs-lookup"><span data-stu-id="e29dc-199">Human Resources — Employee Data</span></span></td>
<td align="left"><span data-ttu-id="e29dc-200">CONTOSO-9##### 형식의 대/소문자 구분 직원 ID를 포함하는 문서입니다.여기서 #은 임의 숫자를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e29dc-200">Documents that include the case sensitive employee id in the format CONTOSO-9##### where # represents any digit.</span></span></td>
<td align="left"><p><span data-ttu-id="e29dc-201">KQL</span><span class="sxs-lookup"><span data-stu-id="e29dc-201">KQL</span></span></p>
<p><span data-ttu-id="e29dc-202">정규식</span><span class="sxs-lookup"><span data-stu-id="e29dc-202">RegEx</span></span></p></td>
<td align="left"><p><span data-ttu-id="e29dc-203">KQL — CONTOSO-9\*</span><span class="sxs-lookup"><span data-stu-id="e29dc-203">KQL — CONTOSO-9\*</span></span></p>
<p><span data-ttu-id="e29dc-204">RegEx — (\bCONTOSO-9\d{5}\b)</span><span class="sxs-lookup"><span data-stu-id="e29dc-204">RegEx — (\bCONTOSO-9\d{5}\b)</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="e29dc-205">인사 - 급여 데이터</span><span class="sxs-lookup"><span data-stu-id="e29dc-205">Human Resources — Salary Data</span></span></td>
<td align="left"><span data-ttu-id="e29dc-206">키워드(대/소문자 구분 안 함) Contoso AND 키워드(대/소문자 구분 안 함) Salary OR Compensation을 포함하는 문서입니다.</span><span class="sxs-lookup"><span data-stu-id="e29dc-206">Documents that include the keyword (not case sensitive) Contoso AND either keyword (not case sensitive) Salary OR Compensation</span></span></td>
<td align="left"><p><span data-ttu-id="e29dc-207">KQL</span><span class="sxs-lookup"><span data-stu-id="e29dc-207">KQL</span></span></p>
<p><span data-ttu-id="e29dc-208">정규식</span><span class="sxs-lookup"><span data-stu-id="e29dc-208">RegEx</span></span></p></td>
<td align="left"><p><span data-ttu-id="e29dc-209">KQL — Contoso AND (Salary OR Compensation)</span><span class="sxs-lookup"><span data-stu-id="e29dc-209">KQL — Contoso AND (Salary OR Compensation)</span></span></p>
<p><span data-ttu-id="e29dc-210">RegEx — (\bCONTOSO-9\d{5}\b)</span><span class="sxs-lookup"><span data-stu-id="e29dc-210">RegEx — (\bCONTOSO-9\d{5}\b)</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="e29dc-211">기밀</span><span class="sxs-lookup"><span data-stu-id="e29dc-211">Confidential</span></span></td>
<td align="left"><span data-ttu-id="e29dc-212">구(대/소문자 구문 안 함) Contoso Confidential을 포함하는 문서입니다.</span><span class="sxs-lookup"><span data-stu-id="e29dc-212">Documents containing the phrase (not case sensitive) Contoso Confidential.</span></span></td>
<td align="left"><p><span data-ttu-id="e29dc-213">KQL</span><span class="sxs-lookup"><span data-stu-id="e29dc-213">KQL</span></span></p>
<p><span data-ttu-id="e29dc-214">정규식</span><span class="sxs-lookup"><span data-stu-id="e29dc-214">RegEx</span></span></p></td>
<td align="left"><p><span data-ttu-id="e29dc-215">KQL — Contoso Confidential</span><span class="sxs-lookup"><span data-stu-id="e29dc-215">KQL — Contoso Confidential</span></span></p>
<p><span data-ttu-id="e29dc-216">RegEx — (?i)(\bContoso Confidential\b)</span><span class="sxs-lookup"><span data-stu-id="e29dc-216">RegEx — (?i)(\bContoso Confidential\b)</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="e29dc-217">극비</span><span class="sxs-lookup"><span data-stu-id="e29dc-217">Highly confidential</span></span></td>
<td align="left"><span data-ttu-id="e29dc-218">구(대/소문자 구분) Contoso Secret 또는 Secret-C####을 포함하는 문서입니다. 여기서 #은 임의 숫자를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e29dc-218">Documents that include either pharase (case sensitive) Contoso Secret or Secret-C#### where # represents any digit.</span></span></td>
<td align="left"><p><span data-ttu-id="e29dc-219">KQL</span><span class="sxs-lookup"><span data-stu-id="e29dc-219">KQL</span></span></p>
<p><span data-ttu-id="e29dc-220">정규식</span><span class="sxs-lookup"><span data-stu-id="e29dc-220">RegEx</span></span></p></td>
<td align="left"><p><span data-ttu-id="e29dc-221">KQL — Contoso Secret OR Secret-C\*</span><span class="sxs-lookup"><span data-stu-id="e29dc-221">KQL — Contoso Secret OR Secret-C\*</span></span></p>
<p><span data-ttu-id="e29dc-222">RegEx — (?i)(\bContoso Secret\b)|(\bSecret-C\d{4}\b)</span><span class="sxs-lookup"><span data-stu-id="e29dc-222">RegEx — (?i)(\bContoso Secret\b)|(\bSecret-C\d{4}\b)</span></span></p></td>
</tr>
</tbody>
</table>
