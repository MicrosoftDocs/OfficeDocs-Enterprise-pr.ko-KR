---
title: Office 365의 개인 데이터에 레이블 적용
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
ms.custom: ''
ms.assetid: ''
description: GDPR 보호 계획의 일부로 Office 레이블을 사용하는 방법을 알아봅니다.
ms.openlocfilehash: 3ad329c061a1bd21002ca2f75c185d11d690e290
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
---
# <a name="apply-labels-to-personal-data-in-office-365"></a><span data-ttu-id="fe98d-103">Office 365의 개인 데이터에 레이블 적용</span><span class="sxs-lookup"><span data-stu-id="fe98d-103">Apply labels to personal data in Office 365</span></span>

 <span data-ttu-id="fe98d-p101">Office 레이블을 GDPR 보호 계획의 일부로 사용하는 경우 이 항목을 사용하세요. 지금 바로 Office 365 보안 및 규정 준수 센터 및 Azure Information Protection에서 레이블을 만들 수 있습니다. 시간에 따라 이러한 기술이 통합된 레이블 및 분류 환경으로 집약되며, 더 많은 성과를 거둘 수 있을 것입니다.</span><span class="sxs-lookup"><span data-stu-id="fe98d-p101">Use this topic if you are using Office labels as part of your GDPR protection plan. Today labels can be created in the Office 365 Security & Compliance Center and in Azure Information Protection. Over time these technologies will converge into a unified labeling and classification experience and you will be able to achieve even more.</span></span>

<span data-ttu-id="fe98d-p102">Office 365에서 개인 데이터의 보호를 위해 레이블을 사용하는 경우 Office 레이블로 시작하는 것이 좋습니다. 고급 데이터 거버넌스를 사용하여 중요한 정보 유형 또는 기타 기준에 따라 레이블을 자동으로 적용할 수 있습니다. 데이터 손실 방지와 함께 Office 레이블을 사용하여 보호를 적용할 수 있습니다. eDiscovery 및 콘텐츠 검색에서도 레이블을 사용할 수 있습니다. 머지 않아 Cloud App Security와 함께 레이블 및 중요한 정보 유형을 사용하여 다른 SaaS 앱에 있는 개인 데이터를 모니터링할 수 있게 될 것입니다.</span><span class="sxs-lookup"><span data-stu-id="fe98d-p102">If you are using labels for protection of personal data in Office 365, Microsoft recommends you start with Office labels. You can use Advanced Data Governance to automatically apply labels based on sensitive information types or other criteria. You can use Office labels with data loss prevention to apply protection. You can also use labels with eDiscovery and Content Search. You’ll soon be able to use both labels and sensitive information types with Cloud App Security to monitor personal data that resides in other SaaS apps.</span></span>

<span data-ttu-id="fe98d-p103">Azure Information Protection 레이블은 현재 온-프레미스 및 다른 클라우드 서비스와 공급자의 파일에 레이블을 적용하는 데 권장됩니다. 이러한 레이블은 데이터 보호를 위해 Azure RMS(Azure Rights Management) 암호화를 요구하는 Office 365의 파일(예: 영업 비밀 파일)에도 권장됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe98d-p103">Azure Information Protection labels are currently recommended for applying labels to files on premises and in other cloud services and providers. These are also recommended for files in Office 365 that require Azure Rights Management (Azure RMS) encryption for data protection, such as trade secret files.</span></span>

<span data-ttu-id="fe98d-p104">지금은 GDPR이 적용되는 데이터를 포함하는 Office 365의 파일에는 Azure Information Protection을 사용하여 Azure RMS 암호화를 적용하는 것이 권장되지 않습니다. Office 365 서비스는 현재 RMS로 암호화된 파일로 읽을 수 없습니다. 따라서 이 서비스는 이러한 파일에서 중요한 데이터를 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fe98d-p104">At this time, using Azure Information Protection to apply Azure RMS encryption is not recommended for files in Office 365 with data that is subject to the GDPR. Office 365 services currently cannot read into RMS-encrypted files. Therefore, the service can’t find sensitive data in these files.</span></span>

<span data-ttu-id="fe98d-p105">Azure Information Protection 레이블은 Exchange Online의 메일에 적용할 수 있으며 Office 365 데이터 손실 방지에 작동합니다. 곧 통합된 분류 및 레이블링 엔진을 사용하여 전송 중인 전자 메일을 자동으로 레이블링하고 보호하는 것을 비롯하여 전자 메일 및 파일에 동일한 레이블을 사용할 수 있게 될 것입니다.</span><span class="sxs-lookup"><span data-stu-id="fe98d-p105">Azure Information Protection labels can be applied to mail in Exchange Online and these labels work with Office 365 data loss prevention. Coming soon with the unified classification and labeling engine you will be able to use the same labels for email and files, including automatically labeling and protecting email in transit.</span></span>

![Office 365 레이블 및 Azure Information Protection 레이블](Media/Apply-labels-to-personal-data-in-Office-365-image1.png)

<span data-ttu-id="fe98d-120">이 그림의 내용</span><span class="sxs-lookup"><span data-stu-id="fe98d-120">In the illustration:</span></span>

-   <span data-ttu-id="fe98d-121">SharePoint Online 및 비즈니스용 OneDrive의 개인 데이터와 규제 및 영업 비밀 파일에 Office 365 레이블을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="fe98d-121">Use Office 365 labels for personal data and for highly regulated & trade secret files in SharePoint Online and OneDrive for Business.</span></span>

-   <span data-ttu-id="fe98d-122">규제 및 영업 비밀 파일, Exchange Online 전자 메일, 다른 SaaS 서비스의 파일, 온-프레미스 데이터 센터의 파일 및 기타 클라우드 공급자의 파일에 AIP(Azure Information Protection) 레이블을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="fe98d-122">Use Azure Information Protection (AIP) labels for highly regulated & trade secret files, Exchange Online email, files in other SaaS services, files in on-premises datacenters, and files in other cloud providers.</span></span>

-   <span data-ttu-id="fe98d-123">출시 예정: 두 가지 유형의 레이블이 통합된 분류 및 레이블링 환경에 집약될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="fe98d-123">Coming soon: both types of labels will converge into a unified classification and labeling experience.</span></span>

## <a name="use-office-labels-and-sensitive-information-types-across-microsoft-365-for-information-protection"></a><span data-ttu-id="fe98d-124">정보 보호를 위해 Microsoft 365에서 Office 레이블 및 중요한 정보 유형 사용</span><span class="sxs-lookup"><span data-stu-id="fe98d-124">Use Office labels and sensitive information types across Microsoft 365 for information protection</span></span>

<span data-ttu-id="fe98d-125">다음 그림은 레이블 정책, 데이터 손실 방지 정책 및 Cloud App Security 정책에서 Office 레이블 및 중요한 정보 유형을 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="fe98d-125">The following illustration shows how Office labels and sensitive information types can be used in label policies, data loss prevention policies, and with Cloud App Security policies.</span></span>

![Office 레이블 및 중요한 정보 유형](Media/Apply-labels-to-personal-data-in-Office-365-image2.png)

<span data-ttu-id="fe98d-127">다음 표에서는 이해를 돕기 위해 그림과 동일한 예제를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="fe98d-127">For accessibility, the following table provides the same examples in the illustration.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="fe98d-128"><strong>분류 요소</strong></span><span class="sxs-lookup"><span data-stu-id="fe98d-128"><strong>Classification elements</strong></span></span></th>
<th align="left"><span data-ttu-id="fe98d-129"><strong>정책 레이블 지정 - 2개 예제</strong></span><span class="sxs-lookup"><span data-stu-id="fe98d-129"><strong>Label policies — 2 examples</strong></span></span></th>
<th align="left"><span data-ttu-id="fe98d-130"><strong>데이터 손실 방지 정책 — 2개 예제</strong></span><span class="sxs-lookup"><span data-stu-id="fe98d-130"><strong>Data loss prevention policies — 2 examples</strong></span></span></th>
<th align="left"><span data-ttu-id="fe98d-131"><strong>모든 SaaS 앱에 대한 Cloud App Security 정책 - 1개 예제</strong></span><span class="sxs-lookup"><span data-stu-id="fe98d-131"><strong>Cloud App Security policies for all SaaS apps — 1 example</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="fe98d-p106">Office 레이블 예제: 개인, 공용, 고객 데이터, HR 데이터, 기밀, 극비</span><span class="sxs-lookup"><span data-stu-id="fe98d-p106">Office labels. Examples: Personal, Public, Customer data, HR data, Confidential, Highly confidential</span></span></td>
<td align="left"><p><span data-ttu-id="fe98d-p107">다음 . . .</span><span class="sxs-lookup"><span data-stu-id="fe98d-p107">Auto apply this label . . .</span></span></p>
<p><span data-ttu-id="fe98d-137">고객 데이터</span><span class="sxs-lookup"><span data-stu-id="fe98d-137">Customer data</span></span></p>
<p><span data-ttu-id="fe98d-p108">. . . 레이블을 다음의 중요한 정보 유형과 일치하는 문서에 자동으로 적용 . . .</span><span class="sxs-lookup"><span data-stu-id="fe98d-p108">. . . to documents that match these sensitive information types . . .</span></span></p>
<p><span data-ttu-id="fe98d-144">&lt;중요한 정보 유형 예제 목록&gt;</span><span class="sxs-lookup"><span data-stu-id="fe98d-144">&lt;list of example sensitive information types&gt;</span></span></p></td>
<td align="left"><p><span data-ttu-id="fe98d-p109">다음 . . .</span><span class="sxs-lookup"><span data-stu-id="fe98d-p109">Apply this protection . . .</span></span></p>
<p><span data-ttu-id="fe98d-148">&lt;보호 정의&gt;</span><span class="sxs-lookup"><span data-stu-id="fe98d-148">&lt;define protection&gt;</span></span></p>
<p><span data-ttu-id="fe98d-p110">. . . 보호를 다음 레이블의 문서에 적용 . . .</span><span class="sxs-lookup"><span data-stu-id="fe98d-p110">. . . to documents with this label . . .</span></span></p>
<p><span data-ttu-id="fe98d-155">고객 데이터</span><span class="sxs-lookup"><span data-stu-id="fe98d-155">Customer data</span></span></p></td>
<td align="left"><p><span data-ttu-id="fe98d-p111">승인된 SaaS 앱에서 다음 . . .</span><span class="sxs-lookup"><span data-stu-id="fe98d-p111">Alert when files with these attributes . . .</span></span></p>
<p><span data-ttu-id="fe98d-159">&lt;미리 정의된 PII 특성 -또는- 사용자 지정 식&gt;</span><span class="sxs-lookup"><span data-stu-id="fe98d-159">&lt;predefined PII attribute -or- custom expression&gt;</span></span></p>
<p><span data-ttu-id="fe98d-p112">. . . 특성을 가진 파일이 조직 외부에서 공유될 때 경고 발생</span><span class="sxs-lookup"><span data-stu-id="fe98d-p112">. . . in any sanctioned SaaS app are shared outside the organization</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="fe98d-p113">중요한 정보 유형. 예: 벨기에 국가 번호, 신용 카드 번호, 크로아티아 ID 카트 번호, 핀란드 국가 ID</span><span class="sxs-lookup"><span data-stu-id="fe98d-p113">Sensitive information types. Examples: Belgium National Number, Credit Card Number, Croatia Identity Cart Number, Finland National ID</span></span></td>
<td align="left"><p><span data-ttu-id="fe98d-p114">사용자에 대해 다음 . . .</span><span class="sxs-lookup"><span data-stu-id="fe98d-p114">Publish these labels for users to manually apply . . .</span></span></p>
<p><span data-ttu-id="fe98d-169">&lt;레이블 선택&gt;</span><span class="sxs-lookup"><span data-stu-id="fe98d-169">&lt;select labels&gt;</span></span></p>
<p><span data-ttu-id="fe98d-p115">. . . 레이블을 다음 위치에 수동으로 적용 . . .</span><span class="sxs-lookup"><span data-stu-id="fe98d-p115">. . . to these locations . . .</span></span></p>
<p><span data-ttu-id="fe98d-176">&lt;모든 위치 또는 특정 위치 선택&gt;</span><span class="sxs-lookup"><span data-stu-id="fe98d-176">&lt;all locations or choose specific locations&gt;</span></span></p></td>
<td align="left"><p><span data-ttu-id="fe98d-p116">다음 . . .</span><span class="sxs-lookup"><span data-stu-id="fe98d-p116">Apply this protection . . .</span></span></p>
<p><span data-ttu-id="fe98d-180">&lt;보호 정의&gt;</span><span class="sxs-lookup"><span data-stu-id="fe98d-180">&lt;define protection&gt;</span></span></p>
<p><span data-ttu-id="fe98d-p117">. . . 레이블을 다음의 중요한 정보 유형과 일치하는 문서에 자동으로 적용&gt;</span><span class="sxs-lookup"><span data-stu-id="fe98d-p117">. . . to documents that match these sensitive information types&gt;</span></span></p></td>
<td align="left"><span data-ttu-id="fe98d-185">참고: Cloud App Security에 곧 제공될 특성에는 Office 365의 중요한 정보 유형과 Office 365 및 Azure Information Protection의 통합 레이블이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe98d-185">Note: Attributes coming soon to Cloud App Security include Office 365 sensitive information types and Unified labels across Office 365 and Azure Information Protection.</span></span></td>
</tr>
</tbody>
</table>

## <a name="prioritize-auto-apply-label-policies"></a><span data-ttu-id="fe98d-186">자동 적용 레이블 정책의 우선 순위 지정</span><span class="sxs-lookup"><span data-stu-id="fe98d-186">Prioritize auto-apply label policies</span></span>

<span data-ttu-id="fe98d-p118">GDPR이 적용되는 개인 데이터의 경우, 사용자 환경을 위해 조정한 중요한 정보 유형을 사용하여 레이블을 자동 적용하는 것이 좋습니다. 자동 적용 레이블 정책을 잘 디자인하고 테스트하여 의도한 대로 작동하는지 확인하는 것이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="fe98d-p118">For personal data that is subject to GDPR, Microsoft recommends auto-applying labels by using the sensitive information types you curated for your environment. It is important that auto-apply label policies are well designed and tested to ensure the intended behavior occurs.</span></span>

<span data-ttu-id="fe98d-p119">자동 적용 정책이 만들어지는 순서와 사용자가 이러한 레이블을 적용하는지 여부도 결과에 영향을 미칩니다. 따라서 롤아웃을 신중하게 계획하는 것이 중요합니다. 알아야 할 사항은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="fe98d-p119">The order that auto-apply policies are created and whether users are also applying these labels affect the result. So, it is important to carefully plan the roll-out. Here’s what you need to know.</span></span>

### <a name="one-label-at-a-time"></a><span data-ttu-id="fe98d-191">한 번에 하나의 레이블 할당</span><span class="sxs-lookup"><span data-stu-id="fe98d-191">One label at a time</span></span>

<span data-ttu-id="fe98d-192">문서에 하나의 레이블만 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe98d-192">You can only assign one label to a document.</span></span>

### <a name="older-auto-apply-policies-win"></a><span data-ttu-id="fe98d-193">오래된 정책이 먼저 자동으로 적용</span><span class="sxs-lookup"><span data-stu-id="fe98d-193">Older auto-apply policies win</span></span>

<span data-ttu-id="fe98d-p120">자동 적용 레이블을 할당하는 규칙이 여러 개 있고 콘텐츠가 여러 규칙의 조건을 충족하는 경우, 가장 오래된 규칙에 대한 레이블이 할당됩니다. 이러한 이유로, 레이블 정책을 구성하기 전에 신중하게 계획하는 것이 중요합니다. 조직은 레이블 정책의 우선 순위를 변경해야 하는 경우 삭제한 후 다시 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe98d-p120">If there are multiple rules that assign an auto-apply label and content meets the conditions of multiple rules, the label for the oldest rule is assigned. For this reason, it is important to plan the label policies carefully before configuring them. If an organization requires a change to the priority of the label policies, they will need to delete and recreate them.</span></span>

### <a name="manual-user-applied-labels-trump-auto-applied-labels"></a><span data-ttu-id="fe98d-197">수동 사용자 적용 레이블이 자동 적용 레이블보다 우선함</span><span class="sxs-lookup"><span data-stu-id="fe98d-197">Manual user-applied labels trump auto-applied labels</span></span>

<span data-ttu-id="fe98d-p121">수동 사용자 적용 레이블은 자동 적용 레이블보다 우선합니다. 자동 적용 정책은 사용자가 이미 적용한 레이블을 대체할 수 없습니다. 사용자는 자동 적용된 레이블을 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe98d-p121">Manual user applied labels trump auto-applied labels. Auto-apply policies cannot replace a label that is already applied by a user. Users can replace labels that are auto-applied.</span></span>

### <a name="auto-assigned-labels-can-be-updated"></a><span data-ttu-id="fe98d-201">자동 할당 레이블을 업데이트할 수 있음</span><span class="sxs-lookup"><span data-stu-id="fe98d-201">Auto-assigned labels can be updated</span></span>

<span data-ttu-id="fe98d-202">자동 할당 레이블은 최신 레이블 정책 또는 기존 정책의 업데이트로 업데이트될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe98d-202">Auto-assigned labels can be updated by either newer label policies or by updates to existing policies.</span></span>

<span data-ttu-id="fe98d-203">레이블 구현 계획에 다음이 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe98d-203">Be sure your plan for implementing labels includes:</span></span>

-   <span data-ttu-id="fe98d-204">자동 적용 정책이 만들어지는 순서에 우선 순위 지정</span><span class="sxs-lookup"><span data-stu-id="fe98d-204">Prioritizing the order that auto-apply policies are created.</span></span>

-   <span data-ttu-id="fe98d-p122">사용자가 수동으로 적용하기 위해 레이블을 롤아웃하기 전에 레이블이 자동으로 적용될 수 있는 충분한 시간 허용. 레이블이 조건과 일치하는 모든 콘텐츠에 적용되는 데는 최대 7일이 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe98d-p122">Allowing enough time for labels to be automatically applied before rolling these out for users to manually apply. It can take up to seven days for the labels to be applied to all content that matches the conditions.</span></span>

### <a name="example-priority-for-creating-the-auto-apply-policies"></a><span data-ttu-id="fe98d-207">자동 적용 정책 만들기 우선 순위 예제</span><span class="sxs-lookup"><span data-stu-id="fe98d-207">Example priority for creating the auto-apply policies</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="fe98d-208"><strong>레이블</strong></span><span class="sxs-lookup"><span data-stu-id="fe98d-208"><strong>Labels</strong></span></span></th>
<th align="left"><span data-ttu-id="fe98d-209"><strong>자동 적용 정책을 만드는 우선 순위</strong></span><span class="sxs-lookup"><span data-stu-id="fe98d-209"><strong>Priority order to create auto-apply policies</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="fe98d-210">인사 - 직원 데이터</span><span class="sxs-lookup"><span data-stu-id="fe98d-210">Human Resources — Employee Data</span></span></td>
<td align="left"><span data-ttu-id="fe98d-211">1</span><span class="sxs-lookup"><span data-stu-id="fe98d-211">1</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="fe98d-212">고객 데이터</span><span class="sxs-lookup"><span data-stu-id="fe98d-212">Customer Data</span></span></td>
<td align="left"><span data-ttu-id="fe98d-213">2</span><span class="sxs-lookup"><span data-stu-id="fe98d-213">2</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="fe98d-214">극비</span><span class="sxs-lookup"><span data-stu-id="fe98d-214">Highly Confidential</span></span></td>
<td align="left"><span data-ttu-id="fe98d-215">3</span><span class="sxs-lookup"><span data-stu-id="fe98d-215">3</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="fe98d-216">인사 - 급여 데이터</span><span class="sxs-lookup"><span data-stu-id="fe98d-216">Human Resources — Salary Data</span></span></td>
<td align="left"><span data-ttu-id="fe98d-217">4</span><span class="sxs-lookup"><span data-stu-id="fe98d-217">4</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="fe98d-218">기밀</span><span class="sxs-lookup"><span data-stu-id="fe98d-218">Confidential</span></span></td>
<td align="left"><span data-ttu-id="fe98d-219">5</span><span class="sxs-lookup"><span data-stu-id="fe98d-219">5</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="fe98d-220">공용</span><span class="sxs-lookup"><span data-stu-id="fe98d-220">Public</span></span></td>
<td align="left"><span data-ttu-id="fe98d-221">6</span><span class="sxs-lookup"><span data-stu-id="fe98d-221">6</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="fe98d-222">개인</span><span class="sxs-lookup"><span data-stu-id="fe98d-222">Personal</span></span></td>
<td align="left"><span data-ttu-id="fe98d-223">자동 적용 정책 없음</span><span class="sxs-lookup"><span data-stu-id="fe98d-223">No auto-apply policy</span></span></td>
</tr>
</tbody>
</table>

## <a name="create-labels-and-auto-apply-label-policies"></a><span data-ttu-id="fe98d-224">레이블 만들기 및 레이블 정책 자동 적용</span><span class="sxs-lookup"><span data-stu-id="fe98d-224">Create labels and auto-apply label policies</span></span>

<span data-ttu-id="fe98d-225">보안 및 규정 준수 센터에서 레이블 및 정책을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="fe98d-225">Create labels and policies in the Security & Compliance Center.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="fe98d-226"><strong>단계</strong></span><span class="sxs-lookup"><span data-stu-id="fe98d-226"><strong>Step</strong></span></span></th>
<th align="left"><span data-ttu-id="fe98d-227"><strong>설명</strong></span><span class="sxs-lookup"><span data-stu-id="fe98d-227"><strong>Description</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><span data-ttu-id="fe98d-228">규정 준수 팀의 구성원에게 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="fe98d-228">Give permissions to members of your compliance team.</span></span></p></td>
<td align="left"><p><span data-ttu-id="fe98d-p123">레이블을 만드는 규정 준수 팀의 구성원에게는 의 보안 &amp; 규정 준수 센터를 사용할 수 있는 권한이 있어야 합니다. 보안 및 규정 준수 센터의 사용 권한으로 이동한 후, 규정 준수 관리자 그룹의 구성원을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="fe98d-p123">Members of your compliance team who will create labels need permissions to use the Security &amp; Compliance Center. Go to Permissions in Security and Compliance Center and modify the members of the Compliance Administrator group.</span></span></p>
<p><span data-ttu-id="fe98d-231"><a href="https://support.office.com/en-ie/article/Give-users-access-to-the-Office-365-Security-Compliance-Center-2cfce2c8-20c5-47f9-afc4-24b059c1bd76">사용자에게 Office 365 보안 &amp; 준수 센터에 대한 액세스 권한 부여</a>를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fe98d-231">See <a href="https://support.office.com/en-ie/article/Give-users-access-to-the-Office-365-Security-Compliance-Center-2cfce2c8-20c5-47f9-afc4-24b059c1bd76">Give users access to the Office 365 Security &amp; Compliance Center</a>.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="fe98d-232">Office 레이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="fe98d-232">Create Office labels.</span></span></p></td>
<td align="left"><span data-ttu-id="fe98d-233">보안 및 규정 준수 센터의 분류로 이동한 후 레이블을 선택하고 해당 환경에 대한 레이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="fe98d-233">Go to Classifications in Security and Compliance Center, choose Labels, and create the labels for your environment.</span></span></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="fe98d-234">레이블에 대한 자동 적용 정책을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="fe98d-234">Create auto-apply policies for labels.</span></span></p></td>
<td align="left"><span data-ttu-id="fe98d-p124">보안 및 규정 준수 센터에서 분류를 선택하고, 레이블 정책을 선택한 후 레이블을 자동 적용하기 위한 정책을 만듭니다. 이러한 정책을 우선 순위대로 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe98d-p124">Go to Classification in Security and Compliance Center, choose Label policies, and create the policies for auto-applying labels. Be sure to create these policies in the prioritized order.</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="fe98d-237">다음 그림에서는 고객 데이터 레이블에 대한 자동 적용 레이블을 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="fe98d-237">The following illustration shows how to create an auto-apply label for the Customer data label.</span></span>

![고객 데이터에 대한 레이블 만들기 및 적용](Media/Apply-labels-to-personal-data-in-Office-365-image3.png)

<span data-ttu-id="fe98d-239">이 그림의 내용</span><span class="sxs-lookup"><span data-stu-id="fe98d-239">In the illustration:</span></span>

-   <span data-ttu-id="fe98d-240">"고객 데이터" 레이블이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="fe98d-240">The “Customer data” label is created.</span></span>

-   <span data-ttu-id="fe98d-241">GDPR에 대해 원하는 중요한 정보 유형인 벨기에 국가 번호, 신용 카드 번호, 크로아티아 ID 카트 번호, 핀란드 국가 ID가 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe98d-241">The desired sensitive information types for GDPR are listed: Belgium National Number, Credit Card Number, Croatia Identity Card Number, Finland National ID.</span></span>

-   <span data-ttu-id="fe98d-242">자동 적용 정책을 만들고 정책에 추가하는 중요한 정보 유형 중 하나를 포함하는 모든 파일에 "고객 데이터" 레이블을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="fe98d-242">Create an auto-apply policy assigns the label “Customer data” to any file that includes one of the sensitive information types that you add to the policy.</span></span>
