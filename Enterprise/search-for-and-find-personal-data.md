---
title: "개인 데이터 검색 및 찾기"
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 2/7/2018
ms.audience: ITPro
ms.topic: overview
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.service: o365-solutions
localization_priority: Priority
ms.custom:
- Strat_O365_Enterprise
- GDPR
ms.assetid: 
description: "Office 365에서 개인 데이터를 검색하고 찾는 방법을 알아봅니다."
ms.openlocfilehash: f19aed534fe2bb4154edc31f0d1b0c82afcc1f04
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2018
---
# <a name="search-for-and-find-personal-data"></a><span data-ttu-id="dc77c-103">개인 데이터 검색 및 찾기</span><span class="sxs-lookup"><span data-stu-id="dc77c-103">Search for and find personal data</span></span>

<span data-ttu-id="dc77c-104">개인 데이터는 EU(유럽 연합)에 거주하는 식별되었거나 식별 가능한 자연인과 관련된 데이터로서 GDPR에서 매우 광범위하게 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc77c-104">Personal data is defined very broadly under the GDPR as any data that relates to an identified or identifiable natural person that is a resident of the European Union (EU).</span></span>

<span data-ttu-id="dc77c-105">문서 4 - 정의</span><span class="sxs-lookup"><span data-stu-id="dc77c-105">Article 4 – Definitions</span></span>

> <span data-ttu-id="dc77c-106">'개인 데이터'는 식별되었거나 식별 가능한 자연인(‘데이터 주체’)과 관련된 정보를 의미합니다. 식별 가능한 자연인은 직간접적으로, 특히 이름, 식별 번호, 위치 데이터, 온라인 식별자 또는 해당 자연인의 신체적, 생리적, 유전적, 정신적, 경제적, 문화적 또는 사회적 ID와 같은 식별자를 참조하여 식별될 수 있는 사람입니다.</span><span class="sxs-lookup"><span data-stu-id="dc77c-106">‘personal data’ means any information relating to an identified or identifiable natural person (‘data subject’); an identifiable natural person is one who can be identified, directly or indirectly, in particular by reference to an identifier such as a name, an identification number, location data, an online identifier or to one or more factors specific to the physical, physiological, genetic, mental, economic, cultural or social identity of that natural person;</span></span>

<span data-ttu-id="dc77c-107">이 문서에서는 SharePoint Online 및 비즈니스용 OneDrive에 저장된 개인 데이터를 찾는 방법을 보여 줍니다(모든 Office 365 그룹 및 Microsoft Teams 사이트 포함) </span><span class="sxs-lookup"><span data-stu-id="dc77c-107">This article demonstrates how to find personal data stored in SharePoint Online and OneDrive for Business (which includes the sites for all Office 365 groups and Microsoft Teams).</span></span>

<span data-ttu-id="dc77c-p101">Office 365에서 GDPR이 적용되는 개인 데이터를 찾으려면 중요한 정보 유형을 사용해야 합니다. 이 과정에서 자동화된 서비스가 의료 서비스 번호 및 신용 카드 번호와 같은 특정 정보 유형을 인식하는 방식이 정의됩니다. 현재, 휴지 상태의 Exchange 사서함에서 데이터를 찾는 데는 이러한 정보를 사용할 수 없습니다. 그렇지만 중요한 정보 유형을 데이터 손실 방지 정책과 함께 사용하여 전송 중인 메일에서 개인 데이터를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc77c-p101">Finding personal data subject to GDPR relies on using sensitive information types in Office 365. These define how the automated process recognizes specific information types such as health service numbers and credit card numbers. At this time these cannot be used to find data in Exchange mailboxes at rest. However, sensitive information types can be used with data loss prevention policies to find personal data in mail while in transit.</span></span>

<span data-ttu-id="dc77c-112">따라서 현재는 콘텐츠 검색을 사용하여 Exchange Online 사서함의 휴지 상태의 개인 데이터를 찾을 수 없지만, GDPR에 맞게 조정한 중요한 정보 유형을 사용하여 전자 메일을 통해 전송되는 개인 정보를 찾아 보호할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc77c-112">So, while you can’t currently use Content Search to find personal data at rest in Exchange Online mailboxes, you can use the sensitive information types you curate for GDPR to find and protect personal information as it is sent through email.</span></span>

## <a name="use-content-search-to-find-personal-data"></a><span data-ttu-id="dc77c-113">콘텐츠 검색을 사용하여 개인 데이터 찾기</span><span class="sxs-lookup"><span data-stu-id="dc77c-113">Use Content Search to find personal data</span></span>

<span data-ttu-id="dc77c-p102">Office 365에서 개인 데이터를 찾는 위한 3단계 접근 방식이 권장됩니다. 이 항목의 나머지 부분에서는 이러한 각 단계에 대한 지침을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="dc77c-p102">Microsoft recommends a three-stage approach to finding personal data in Office 365. The rest of this topic provides guidance for each of these stages.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="dc77c-116"><strong>단계</strong></span><span class="sxs-lookup"><span data-stu-id="dc77c-116"><strong>Step</strong></span></span></th>
<th align="left"><span data-ttu-id="dc77c-117"><strong>설명</strong></span><span class="sxs-lookup"><span data-stu-id="dc77c-117"><strong>Description</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><span data-ttu-id="dc77c-118">1. 중요한 정보 유형 검색</span><span class="sxs-lookup"><span data-stu-id="dc77c-118">1. Search for sensitive information types</span></span></p></td>
<td align="left"><p><span data-ttu-id="dc77c-p103">먼저 중요한 정보 유형을 사용하여 개인 데이터를 찾습니다. 각각의 중요한 정보 유형에 대해 콘텐츠 검색 쿼리를 만듭니다. 쿼리를 실행한 후 결과를 분석합니다.</span><span class="sxs-lookup"><span data-stu-id="dc77c-p103">Start by using sensitive information types to find personal data. Create a Content Search query for each sensitive information type. Run the query and analyze the results.</span></span></p>
<span data-ttu-id="dc77c-122">필요에 따라 가양성을 줄이기 위해 쿼리에 매개 변수를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="dc77c-122">If needed, add parameters to the query to reduce false positives:</span></span> <li><span data-ttu-id="dc77c-123">개수 범위</span><span class="sxs-lookup"><span data-stu-id="dc77c-123">Count range</span></span></li>
    <li><span data-ttu-id="dc77c-124">신뢰도 범위</span><span class="sxs-lookup"><span data-stu-id="dc77c-124">Confidence range</span></span></li>
    <li><span data-ttu-id="dc77c-125">좀 더 복잡한 쿼리를 위한 기타 속성 또는 연산자</span><span class="sxs-lookup"><span data-stu-id="dc77c-125">Other properties or operators for more complex queries</span></span></li>
<p><span data-ttu-id="dc77c-126">필요한 경우 조직에 맞게 정확도를 향상시키도록 중요한 정보 유형을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="dc77c-126">If necessary, modify a sensitive information type to improve accuracy for your organization:</span></span></p>
<p><li><span data-ttu-id="dc77c-127">XML에서 직접 신뢰 수준을 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="dc77c-127">Adjust the confidence level directly in the XML.</span></span></li></p>
<p><li><span data-ttu-id="dc77c-128">키워드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="dc77c-128">Add key words.</span></span></li></p>
<p><li><span data-ttu-id="dc77c-129">키워드에 대한 근접 요구 사항을 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="dc77c-129">Adjust the proximity requirements for keywords.</span></span></li></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="dc77c-130">2. KQL(키워드 쿼리 언어)을 사용하여 작업 환경에서 추가 개인 데이터 찾기</span><span class="sxs-lookup"><span data-stu-id="dc77c-130">2. Use Keyword Query Language (KQL) to find additional personal data in your environment</span></span></p></td>
<td align="left"><p><span data-ttu-id="dc77c-131">중요한 정보 유형에 포함되지 데이터를 찾으려면 KQL 쿼리 언어를 사용하여 사용자 지정 쿼리를 개발합니다.</span><span class="sxs-lookup"><span data-stu-id="dc77c-131">To find data not included in sensitive information types, use the KQL query language to develop custom queries.</span></span></p>
<p><span data-ttu-id="dc77c-132">이러한 검색의 결과를 테스트하고 예상된 결과를 얻을 때까지 KQL 쿼리 문자열을 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="dc77c-132">Test the results of these searches and adjust the KQL query string until you achieve the expected result.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="dc77c-133">3. KQL 쿼리를 사용하여 새 사용자 지정 중요한 정보 유형 만들기</span><span class="sxs-lookup"><span data-stu-id="dc77c-133">3. Create new custom sensitive information types using the KQL queries</span></span></p></td>
<td align="left"><span data-ttu-id="dc77c-p104">KQL 쿼리를 최적화하여 대상 데이터를 찾은 후 이러한 쿼리를 사용하여 새 사용자 지정 중요한 정보 유형을 만듭니다. 그런 후 DLP 정책 및 기타 도구와 다른 KQL 쿼리 내에서 콘텐츠 검색에 이러한 사용자 지정 중요한 정보 유형을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc77c-p104">After optimizing KQL queries to find target data, create new custom sensitive information types using these queries. You can then use these custom sensitive information types with Content Search, in DLP policies and other tools, and within other KQL queries.</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="dc77c-p105">출시 예정 - 보안 및 규정 준수 센터의 새 사용자 인터페이스에서 중요한 정보 유형을 만들고 수정할 수 있습니다. 일치하는 결과를 동적으로 확인하고 사용자 요구에 맞게 중요한 정보 유형을 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc77c-p105">Coming soon — You'll be able to create and modify sensitive information types in a new user interface in the Security and Compliance Center. You can dynamically see matching results and tune sensitive information types to meet your needs.</span></span>

## <a name="search-for-sensitive-information-types-using-content-search"></a><span data-ttu-id="dc77c-138">콘텐츠 검색을 사용하여 중요한 정보 유형 검색</span><span class="sxs-lookup"><span data-stu-id="dc77c-138">Search for sensitive information types using Content Search</span></span>

<span data-ttu-id="dc77c-p106">먼저 Office 365에 포함된 중요한 정보 유형을 사용하여 개인 데이터를 검색합니다. 이러한 데이터는 보안 및 규정 준수 센터의 분류 아래에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc77c-p106">Begin searching for personal data by using the sensitive information types that are included with Office 365. These are listed in the Security and Compliance Center under Classification.</span></span>

<span data-ttu-id="dc77c-p107">이 항목에는 유럽 연합 거주민에게 적용되는 최신 중요한 정보 유형 목록이 포함됩니다. 이러한 중요한 정보 유형을 시작점으로 사용합니다. 보안 및 규정 준수 센터에서 GDPR 규정 준수에 도움이 될 수 있는 새로운 추가 항목이 있는지 자주 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="dc77c-p107">This topic includes a list of current sensitive information types that apply to citizens in the European Union. Use these as a starting point. Check Security and Compliance Center frequently for new additions that can help with GDPR compliance.</span></span>

<span data-ttu-id="dc77c-144">또한 [중요한 정보 유형 및 각 유형이 확인하는 내용 목록](https://support.office.com/ko-KR/article/What-the-sensitive-information-types-look-for-fd505979-76be-4d9f-b459-abef3fc9e86b)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dc77c-144">Also see this article: [List of sensitive information types and what each one looks for](https://support.office.com/ko-KR/article/What-the-sensitive-information-types-look-for-fd505979-76be-4d9f-b459-abef3fc9e86b).</span></span>

<span data-ttu-id="dc77c-p108">중요한 정보 유형은 정규식이나 함수로 식별될 수 있는 패턴으로 정의됩니다. 또한 키워드 및 체크섬과 같은 확증적인 증거를 사용하여 중요한 정보 유형을 식별할 수 있습니다. 이러한 평가 프로세스에서 신뢰 수준 및 근접성도 사용됩니다. 중요한 정보 유형은 정규식이나 함수로 식별될 수 있는 패턴으로 정의됩니다. 또한 키워드 및 체크섬과 같은 보완적 증거를 사용하여 중요한 정보 유형을 식별할 수 있습니다. 신뢰도 및 근접성도 평가 프로세스에서 활용됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc77c-p108">Sensitive information types define how the automated process recognizes specific information types such as bank account numbers, health service numbers, and credit card numbers. Sensitive information types are also referred to as conditions. A sensitive information type is defined by a pattern that can be identified by a regular expression or a function. In addition, corroborative evidence such as keywords and checksums can be used to identify a sensitive information type. Confidence level and proximity are also used in the evaluation process.</span></span>

<span data-ttu-id="dc77c-150">현재, 사서함에서 휴지 상태의 데이터를 찾는 데는 중요한 정보 유형을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="dc77c-150">At this time sensitive information types cannot be used to find data at rest in mailboxes.</span></span>

### <a name="using-content-search-with-sensitive-information-types"></a><span data-ttu-id="dc77c-151">중요한 정보 유형에 콘텐츠 검색 사용</span><span class="sxs-lookup"><span data-stu-id="dc77c-151">Using Content Search with sensitive information types</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="dc77c-152"><strong>단계</strong></span><span class="sxs-lookup"><span data-stu-id="dc77c-152"><strong>Step</strong></span></span></th>
<th align="left"><span data-ttu-id="dc77c-153"><strong>추가 정보</strong></span><span class="sxs-lookup"><span data-stu-id="dc77c-153"><strong>More Information</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd"><td align="left"><p><span data-ttu-id="dc77c-154">보안 및 준수 센터에서 콘텐츠 검색으로 이동</span><span class="sxs-lookup"><span data-stu-id="dc77c-154">Go to Content Search in the Security and Compliance Center</span></span></p></td>
<td align="left"><p><span data-ttu-id="dc77c-155">보안 및 준수 센터의 왼쪽 창에서 **검색 및 조사** &gt; **콘텐츠 검색**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="dc77c-155">In the left pane of the Security &amp; Compliance Center, click **Search &amp; investigation** &gt; **Content search**.</span></span></p>
<p><span data-ttu-id="dc77c-156"><a href="https://support.office.com/en-us/article/Run-a-Content-Search-in-the-Office-365-Security-Compliance-Center-61852fd9-fe8a-4880-a339-cb19ed3bff4a">Office 365 보안 및 준수 센터에서 콘텐츠 검색 실행</a>을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dc77c-156">Run a Content Search in the Office 365 Security & Compliance Center</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="dc77c-157">각 중요한 정보 유형에 대해 새 검색 항목 만들기</span><span class="sxs-lookup"><span data-stu-id="dc77c-157">Create a new search item for each sensitive information type</span></span></p></td>
<td align="left"><p><span data-ttu-id="dc77c-158">다음 구문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="dc77c-158">Use the following syntax:</span></span></p>
<blockquote>
<p><span data-ttu-id="dc77c-159">SensitiveType:”&lt;type&gt;”</span><span class="sxs-lookup"><span data-stu-id="dc77c-159">SensitiveType:”&lt;type&gt;”</span></span></p>
</blockquote>
<p><span data-ttu-id="dc77c-160">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="dc77c-160">For example:</span></span></p>
<blockquote>
<p><span data-ttu-id="dc77c-161">SensitiveType:&quot;France Passport Number&quot;</span><span class="sxs-lookup"><span data-stu-id="dc77c-161">France Passport Number</span></span></p>
</blockquote>
<p><span data-ttu-id="dc77c-p109">검색 범위를 SharePoint(비즈니스용 OneDrive 포함)으로 지정합니다. 구문이 정확한지와 불필요한 공백이나 입력 오류가 없는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="dc77c-p109">Scope the search to SharePoint (includes OneDrive for Business). Make sure the syntax is exact and there are no extra spaces or typos.</span></span></p>
<p><span data-ttu-id="dc77c-164"><a href="https://support.office.com/ko-KR/article/Form-a-query-to-find-sensitive-data-stored-on-sites-3019fbc5-7f15-4972-8d0e-dc182dc7f836">사이트에 저장된 중요한 데이터를 찾기 위한 쿼리 작성</a>을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dc77c-164">Form a query to find sensitive data stored on sites</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="dc77c-165">각 검색에 대한 결과 검토</span><span class="sxs-lookup"><span data-stu-id="dc77c-165">Review the results for each search</span></span></p></td>
<td align="left"><p><span data-ttu-id="dc77c-166">다음 유형의 문제를 찾아 쿼리 정확도가 원하는 수준인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="dc77c-166">Look for these types of issues to determine if the query accuracy is on target:</span></span></p>
<p><li><span data-ttu-id="dc77c-167">많은 가양성</span><span class="sxs-lookup"><span data-stu-id="dc77c-167">Many false positives</span></span></li></p>
<p><li><span data-ttu-id="dc77c-168">누락된 데이터의 알려진 인스턴스</span><span class="sxs-lookup"><span data-stu-id="dc77c-168">Missing known instances of data</span></span></li></p>
<p><span data-ttu-id="dc77c-169"><a href="https://support.office.com/en-us/article/Export-Content-Search-results-from-the-Office-365-Security-Compliance-Center-ed48d448-3714-4c42-85f5-10f75f6a4278">Office 365 보안 및 준수 센터에서 콘텐츠 검색 결과 내보내기</a>를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dc77c-169">Export search results from the Office 365 Security & Compliance Center</span></span></p>
<p><span data-ttu-id="dc77c-170">참고: Mozilla Firefox 또는 Chrome을 사용하는 경우 필요한 추가 기능을 설치하기 위해 먼저 Internet Explorer 또는 Edge를 사용하여 보고서를 다운로드해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc77c-170">Note: if you’re using Mozilla Firefox or Chrome, you might need to first download reports using Internet Explorer or Edge in order to install the required add-in.</span></span></p></td>
</tr>
</tbody>
</table>

## <a name="sensitive-information-types-for-eu-citizen-data"></a><span data-ttu-id="dc77c-171">EU 거주민 데이터에 대한 중요한 정보 유형</span><span class="sxs-lookup"><span data-stu-id="dc77c-171">Sensitive information types for EU citizen data</span></span>

<span data-ttu-id="dc77c-p110">이러한 중요한 정보 유형으로 시작합니다. EU 국가의 개인 데이터에 대한 더 많은 중요한 정보 유형이 곧 제공될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="dc77c-p110">Start with these sensitive information types. Many more sensitive information types are coming soon for personal data in EU countries.</span></span>

> <span data-ttu-id="dc77c-174">벨기에 국가 번호</span><span class="sxs-lookup"><span data-stu-id="dc77c-174">Belgium National Number</span></span>
>
> <span data-ttu-id="dc77c-175">신용 카드 번호</span><span class="sxs-lookup"><span data-stu-id="dc77c-175">Credit Card Number</span></span>
>
> <span data-ttu-id="dc77c-176">크로아티아 ID 카드 번호</span><span class="sxs-lookup"><span data-stu-id="dc77c-176">Croatia Identity Card Number</span></span>
>
> <span data-ttu-id="dc77c-177">크로아티아 개인 식별(OIB) 번호</span><span class="sxs-lookup"><span data-stu-id="dc77c-177">Croatia Personal Identification (OIB) Number</span></span>
>
> <span data-ttu-id="dc77c-178">체코 국가 ID 카드 번호</span><span class="sxs-lookup"><span data-stu-id="dc77c-178">Czech National Identity Card Number</span></span>
>
> <span data-ttu-id="dc77c-179">덴마크 개인 식별 번호</span><span class="sxs-lookup"><span data-stu-id="dc77c-179">Denmark Personal Identification Number</span></span>
>
> <span data-ttu-id="dc77c-180">유럽 직불 카드 번호</span><span class="sxs-lookup"><span data-stu-id="dc77c-180">EU Debit Card Number</span></span>
>
> <span data-ttu-id="dc77c-181">핀란드 국가 ID</span><span class="sxs-lookup"><span data-stu-id="dc77c-181">Finland National ID</span></span>
>
> <span data-ttu-id="dc77c-182">핀란드 여권 번호</span><span class="sxs-lookup"><span data-stu-id="dc77c-182">Finland Passport Number</span></span>
>
> <span data-ttu-id="dc77c-183">프랑스 운전 면허 번호</span><span class="sxs-lookup"><span data-stu-id="dc77c-183">France Driver's License Number</span></span>
>
> <span data-ttu-id="dc77c-184">프랑스 국가 ID 카드(CNI)</span><span class="sxs-lookup"><span data-stu-id="dc77c-184">France National ID Card (CNI)</span></span>
>
> <span data-ttu-id="dc77c-185">프랑스 여권 번호</span><span class="sxs-lookup"><span data-stu-id="dc77c-185">France Passport Number</span></span>
>
> <span data-ttu-id="dc77c-186">프랑스 사회 보장 번호(INSEE)</span><span class="sxs-lookup"><span data-stu-id="dc77c-186">France Social Security Number (INSEE)</span></span>
>
> <span data-ttu-id="dc77c-187">독일 운전 면허 번호</span><span class="sxs-lookup"><span data-stu-id="dc77c-187">German Driver's License Number</span></span>
>
> <span data-ttu-id="dc77c-188">독일 ID 카드 번호</span><span class="sxs-lookup"><span data-stu-id="dc77c-188">Identity Card Number
</span></span>
>
> <span data-ttu-id="dc77c-189">독일 여권 번호</span><span class="sxs-lookup"><span data-stu-id="dc77c-189">German Passport Number</span></span>
>
> <span data-ttu-id="dc77c-190">그리스 국가 ID 카드</span><span class="sxs-lookup"><span data-stu-id="dc77c-190">Greece National ID Card</span></span>
>
> <span data-ttu-id="dc77c-191">IBAN(국제 은행 계좌 번호)</span><span class="sxs-lookup"><span data-stu-id="dc77c-191">International Banking Account Number (IBAN)</span></span>
>
> <span data-ttu-id="dc77c-192">IP 주소</span><span class="sxs-lookup"><span data-stu-id="dc77c-192">IP Address</span></span>
>
> <span data-ttu-id="dc77c-193">아일랜드 PPS(개인 공공 서비스) 번호</span><span class="sxs-lookup"><span data-stu-id="dc77c-193">Ireland Personal Public Service (PPS) Number</span></span>
>
> <span data-ttu-id="dc77c-194">이탈리아 운전 면허 번호</span><span class="sxs-lookup"><span data-stu-id="dc77c-194">Italy’s Driver’s License Number</span></span>
>
> <span data-ttu-id="dc77c-195">네덜란드 시민 서비스(BSN) 번호</span><span class="sxs-lookup"><span data-stu-id="dc77c-195">Netherlands Citizen's Service (BSN) Number</span></span>
>
> <span data-ttu-id="dc77c-196">노르웨이 ID 번호</span><span class="sxs-lookup"><span data-stu-id="dc77c-196">Norway Identity Number</span></span>
>
> <span data-ttu-id="dc77c-197">폴란드 ID 카드</span><span class="sxs-lookup"><span data-stu-id="dc77c-197">Poland Identity Card</span></span>
>
> <span data-ttu-id="dc77c-198">폴란드 국가 ID(PESEL)</span><span class="sxs-lookup"><span data-stu-id="dc77c-198">Poland National ID (PESEL)</span></span>
>
> <span data-ttu-id="dc77c-199">폴란드 여권</span><span class="sxs-lookup"><span data-stu-id="dc77c-199">Poland Passport</span></span>
>
> <span data-ttu-id="dc77c-200">포르투갈 시민 카드 번호</span><span class="sxs-lookup"><span data-stu-id="dc77c-200">Portugal Citizen Card Number</span></span>
>
> <span data-ttu-id="dc77c-201">스페인 SSN(사회 보장 번호)</span><span class="sxs-lookup"><span data-stu-id="dc77c-201">Spain Social Security Number (SSN)</span></span>
>
> <span data-ttu-id="dc77c-202">스웨덴 국가 ID</span><span class="sxs-lookup"><span data-stu-id="dc77c-202">Sweden National ID</span></span>
>
> <span data-ttu-id="dc77c-203">스웨덴 여권 번호</span><span class="sxs-lookup"><span data-stu-id="dc77c-203">Sweden Passport Number</span></span>
>
> <span data-ttu-id="dc77c-p111">영국 운전 면허 번호</span><span class="sxs-lookup"><span data-stu-id="dc77c-p111">U.K. Driver's License Number</span></span>
>
> <span data-ttu-id="dc77c-p112">영국 선거 롤 번호</span><span class="sxs-lookup"><span data-stu-id="dc77c-p112">U.K. Electoral Roll Number</span></span>
>
> <span data-ttu-id="dc77c-p113">영국 국립 보건 서비스 번호</span><span class="sxs-lookup"><span data-stu-id="dc77c-p113">U.K. National Health Service Number</span></span>
>
> <span data-ttu-id="dc77c-p114">영국 NINO(국민 보험 번호)</span><span class="sxs-lookup"><span data-stu-id="dc77c-p114">U.K. National Insurance Number (NINO)</span></span>
>
> <span data-ttu-id="dc77c-p115">미국/영국 여권 번호</span><span class="sxs-lookup"><span data-stu-id="dc77c-p115">U.S. / U.K. Passport Number</span></span>

## <a name="add-parameters-to-a-sensitive-information-type-query-to-hone-the-results"></a><span data-ttu-id="dc77c-214">중요한 정보 유형 쿼리에 매개 변수를 추가하여 결과 조정</span><span class="sxs-lookup"><span data-stu-id="dc77c-214">Add parameters to a sensitive information type query to hone the results</span></span>

<span data-ttu-id="dc77c-215">중요한 정보 유형 쿼리에 다음 매개 변수를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc77c-215">You can add these parameters to a sensitive information type query:</span></span>

-   <span data-ttu-id="dc77c-216">개수 범위 - 문서가 쿼리 결과에 포함되기 위해 포함해야 하는 중요한 정보가 나오는 횟수를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="dc77c-216">Count range — define the number of occurrences of sensitive information a document needs to contain before it’s included in the query results.</span></span>

-   <span data-ttu-id="dc77c-217">신뢰도 범위 - 검색된 중요한 유형이 실제로 일치하는 신뢰도 수준[예: 85(85%)]을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="dc77c-217">Confidence range — the level of confidence that the detected sensitive type is actually a match, such as 85 (85%).</span></span>

<span data-ttu-id="dc77c-218">구문:</span><span class="sxs-lookup"><span data-stu-id="dc77c-218">Syntax</span></span>

-   <span data-ttu-id="dc77c-219">SensitiveType:”\<type\>|\<count range\>|\<confidence range\>”</span><span class="sxs-lookup"><span data-stu-id="dc77c-219">SensitiveType:”\<type\>|\<count range\>|\<confidence range\>”</span></span>

<span data-ttu-id="dc77c-220">예제:</span><span class="sxs-lookup"><span data-stu-id="dc77c-220">Examples:</span></span>

-   <span data-ttu-id="dc77c-221">SensitiveType:“Credit Card Number|5” (정확히 5개의 카드 번호와 일치하는 문서만 반환)</span><span class="sxs-lookup"><span data-stu-id="dc77c-221">SensitiveType:“Credit Card Number|5” (return only documents that contain exactly five credit card numbers)</span></span>

-   <span data-ttu-id="dc77c-p116">SensitiveType:“Credit Card Number|\*|85..” (신뢰도 범위는 85% 이상임)</span><span class="sxs-lookup"><span data-stu-id="dc77c-p116">SensitiveType:“Credit Card Number|\*|85..” (confidence range is 85 percent or higher)</span></span>

<span data-ttu-id="dc77c-224">참고: "SensitiveType"은 대/소문자를 구분하지만 쿼리의 나머지 부분은 그렇지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dc77c-224">Note: “SensitiveType” is case sensitive, but the rest of the query is not.</span></span>

<span data-ttu-id="dc77c-p117">또한 속성 및 연산자를 사용하여 쿼리를 구체화하는 방법을 보여줄 수도 있습니다. 자세한 내용 및 예제에 대해서는 [사이트에 저장된 중요한 데이터를 찾기 위한 쿼리 작성](https://support.office.com/ko-KR/article/Form-a-query-to-find-sensitive-data-stored-on-sites-3019fbc5-7f15-4972-8d0e-dc182dc7f836)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dc77c-p117">You can also use properties, and operators to illustrate how you can refine your queries. For more information and examples, see [Form a query to find sensitive data stored on sites](https://support.office.com/ko-KR/article/Form-a-query-to-find-sensitive-data-stored-on-sites-3019fbc5-7f15-4972-8d0e-dc182dc7f836).</span></span>
