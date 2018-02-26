---
title: "중요한 정보 유형 사용자 지정 또는 새로 만들기"
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
description: "GDPR에 대한 Office 365 중요한 정보 유형을 수정하거나 새로 만드는 방법을 알아봅니다."
ms.openlocfilehash: 58bfce19d75a66fe36d3e61ec0b05bcca6913b85
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2018
---
# <a name="customize-or-create-a-new-sensitive-information-type"></a><span data-ttu-id="42dad-103">중요한 정보 유형 사용자 지정 또는 새로 만들기</span><span class="sxs-lookup"><span data-stu-id="42dad-103">Customize or create a new sensitive information type</span></span>

<span data-ttu-id="42dad-104">이 문서에서는 GDPR에 대한 Office 365 중요한 정보 유형을 수정하거나 새로 만드는 방법을 보여 주는 3가지 예제를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="42dad-104">This article provides three examples to demonstrate how to modify or create new Office 365 sensitive information types for GDPR.</span></span>

-   <span data-ttu-id="42dad-105">기존 중요한 정보 유형 수정 — 유럽 직불 카드 번호</span><span class="sxs-lookup"><span data-stu-id="42dad-105">Modify an existing sensitive information type — EU Debit Card Number</span></span>

-   <span data-ttu-id="42dad-106">새 중요한 정보 유형 만들기 - 전자 메일 주소</span><span class="sxs-lookup"><span data-stu-id="42dad-106">Create a new sensitive information type — email address</span></span>

-   <span data-ttu-id="42dad-107">예제 XML 파일을 사용하여 새 중요한 정보 유형 만들기 — Contoso 고객 번호</span><span class="sxs-lookup"><span data-stu-id="42dad-107">Create a new sensitive information type with example XML file — Contoso customer number</span></span>

<span data-ttu-id="42dad-108">참고:</span><span class="sxs-lookup"><span data-stu-id="42dad-108">Also see:</span></span>

-   [<span data-ttu-id="42dad-109">사용자 지정 중요한 정보 유형 만들기</span><span class="sxs-lookup"><span data-stu-id="42dad-109">Create a custom sensitive information type</span></span>](https://support.office.com/ko-KR/article/Create-a-custom-sensitive-information-type-82c382a5-b6db-44fd-995d-b333b3c7fc30)

-   [<span data-ttu-id="42dad-110">기본 제공 중요한 정보 유형 사용자 지정 </span><span class="sxs-lookup"><span data-stu-id="42dad-110">Customize a built-in sensitive information type </span></span>](https://support.office.com/ko-KR/article/Customize-a-built-in-sensitive-information-type-2164ce3d-4d64-4283-b6b1-b81fbe835e8e)

## <a name="modify-a-sensitive-information-type-to-improve-accuracy"></a><span data-ttu-id="42dad-111">정확도를 향상시키도록 중요한 정보 유형 수정</span><span class="sxs-lookup"><span data-stu-id="42dad-111">Modify a sensitive information type to improve accuracy</span></span>

<span data-ttu-id="42dad-112">콘텐츠 검색을 사용하여 중요한 정보 유형을 통해 개인 데이터를 검색하려고 하는데 예상된 결과가 반환되지 않거나, 너무 많은 가양성이 반환된 경우 작업 환경에 더 잘 맞게 중요한 정보 유형을 수정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="42dad-112">If you’re using Content Search to search for personal data using sensitive information types and you’re not returning the expected results, or the query returns too many false positives, consider modifying the sensitive information type to work better with your environment.</span></span>

<span data-ttu-id="42dad-p101">중요한 정보 유형을 만들거나 사용자 지정할 때의 모범 사례는 기존의 중요한 정보 유형에 따라 새로운 정보 유형을 만들고 고유한 이름 및 식별자를 지정하는 것입니다. 예를 들어 "유럽 직불 카드 번호" 중요한 정보 유형 매개 변수를 조정하려는 경우 해당 규칙 사본에 "유럽 직불 카드 강화"로 이름을 지정하여 원본과 구분할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42dad-p101">The best practice when creating or customizing a sensitive information type is to create a new sensitive information type based on an existing one, giving it a unique name and identifiers. For example, if you wish to adjust the parameters of the “EU Debit Card Number” sensitive information type, you could name your copy of that rule “EU Debit Card Enhanced” to distinguish it from the original.</span></span>

<span data-ttu-id="42dad-p102">새 중요한 정보 유형에서 정확도 향상을 위해 변경하려는 값을 수정하기만 하면 됩니다. 일단 완료되면, 새 중요한 정보 유형을 업로드하고, 방금 추가한 새 중요한 정보 유형을 사용하기 위한 새 DLP 규칙을 새로 만듭니다(또는 기존 계정 수정). 중요한 정보 유형의 정확도를 수정하려면 약간의 시행 착오가 필요할 수 있으므로 원본 유형의 복사본을 유지하여 나중에 필요할 때 원본 사본으로 대체할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42dad-p102">In your new sensitive information type, simply modify the values you wish to change to improve its accuracy. Once complete, upload your new sensitive information type and create a new DLP rule (or modify an existing one) to use the new sensitive information type you just added. Modifying the accuracy of sensitive information types might require some trial and error, so maintaining a copy of the original type allows you to fall back to it if required in the future.</span></span>

<span data-ttu-id="42dad-118">중요한 정보 유형을 사용자 지정하려면</span><span class="sxs-lookup"><span data-stu-id="42dad-118">To customize a sensitive information type:</span></span>

1.  <span data-ttu-id="42dad-119">Office 365에서 기본 제공 중요한 정보 유형의 기존 Microsoft 규칙 패키지를 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="42dad-119">Export the existing Microsoft Rule Package of built in sensitive information types in Office 365.</span></span>

2.  <span data-ttu-id="42dad-120">이 XML 파일의 이름을 바꾸고 원하는 XML 편집기에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="42dad-120">Rename this XML file and open it in your favorite XML editor.</span></span>

3.  <span data-ttu-id="42dad-121">중요한 정보 유형을 격리하고 다른 모든 정보 유형을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="42dad-121">Isolate the sensitive information type and remove all others.</span></span>

4.  <span data-ttu-id="42dad-122">PowerShell을 사용하여 수정하려는 중요한 정보 유형에 대해 2개의 새 GUID를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="42dad-122">Use PowerShell to generate two new GUIDs for the sensitive information type you are modifying.</span></span>

5.  <span data-ttu-id="42dad-123">중요한 정보 유형이 고유하도록 ID 및 기타 기본 요소를 수정합니다(2개의 GUID를 생성한 새 GUID로 대체).</span><span class="sxs-lookup"><span data-stu-id="42dad-123">Modify the ID and other basic elements so the sensitive information type is unique (this includes replacing two GUIDs with the new ones you generated).</span></span>

6.  <span data-ttu-id="42dad-124">일치 요구 사항을 조정하여 정확도를 높입니다.</span><span class="sxs-lookup"><span data-stu-id="42dad-124">Tune the match requirements to improve accuracy.</span></span>

    1.  <span data-ttu-id="42dad-125">근접성 수정 - 문자 패턴 근접성을 수정하여 중요한 정보 유형에 대해 키워드를 찾아야 하는 창을 확장하거나 축소합니다.</span><span class="sxs-lookup"><span data-stu-id="42dad-125">Proximity modifications — Modify the character pattern proximity to expand or shrink the window in which keywords must be found around the sensitive information type.</span></span>

    2.  <span data-ttu-id="42dad-p103">키워드 수정 — 이 규칙에 대해 일치 사실을 알리기 위해 중요한 정보 유형이 보다 구체적인 추측 증거를 제공하도록 \<Keywords\> 요소 중 하나에 키워드를 추가합니다. 또는 가양성을 유발하는 키워드를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="42dad-p103">Keyword modifications — Add keywords to one of the \<Keywords\> element in order to provide our sensitive information type more specific corroborative evidence to search for in order to signal a match on this rule. Or remove keywords that are causing false positives.</span></span>

    3.  <span data-ttu-id="42dad-128">신뢰도 수정 - 일치에 대해 알림 및 보고가 제공되기 전에 중요한 정보 유형이 해당 정의에 지정된 조건과 일치해야 하는 신뢰도를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="42dad-128">Confidence modifications — Modify the confidence with which the sensitive information type must match the criteria specified in its definition before a match is signaled and reported.</span></span>

7.  <span data-ttu-id="42dad-129">새 중요한 정보 유형을 업로드합니다.</span><span class="sxs-lookup"><span data-stu-id="42dad-129">Upload the new sensitive information type.</span></span>

8.  <span data-ttu-id="42dad-p104">중요한 정보를 식별하도록 콘텐츠를 다시 크롤링합니다. [사이트 크롤링 및 재인덱싱 수동 요청](https://support.office.com/ko-KR/article/Manually-request-crawling-and-re-indexing-of-a-site-a-library-or-a-list-9AFA977D-39DE-4321-B4CA-8C7C7E6D264E)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="42dad-p104">Recrawl your content to identify the sensitive information. See [Manually request crawling and re-indexing of a site](https://support.office.com/ko-KR/article/Manually-request-crawling-and-re-indexing-of-a-site-a-library-or-a-list-9AFA977D-39DE-4321-B4CA-8C7C7E6D264E).</span></span>

## <a name="example-modify-the-eu-debit-card-number-sensitive-information-type"></a><span data-ttu-id="42dad-132">예제: '유럽 직불 카드 번호' 중요한 정보 유형 수정</span><span class="sxs-lookup"><span data-stu-id="42dad-132">Example: modify the ‘EU Debit Card Number’ sensitive information type</span></span>

<span data-ttu-id="42dad-p105">모든 시스템에서 DLP 규칙의 정확도를 향상시키려면 샘플 데이터 집합에 대한 테스트가 필요하며, 반복적인 수정 및 테스트를 통해 미세 조정해야 할 수 있습니다. 이 예제에서는 정확도 개선을 위해 '유럽 직불 카드 번호' 중요한 정보 유형에 대한 수정 작업을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="42dad-p105">Improving the accuracy of DLP rules in any system requires testing against a sample data set, and may require fine tuning through repetitive modifications and tests. This example demonstrates modifications to the ‘EU Debit Card Number’ sensitive information type to improve its accuracy.</span></span>

<span data-ttu-id="42dad-p106">이 예제에서 유럽 직불 카드 번호를 검색할 때 해당 번호의 정의는 복잡한 패턴을 사용하여 16자리 숫자로 엄격히 정의되며 체크섬의 유효성 검사를 따라야 합닏. 이 중요한 정보 유형의 문자열 정의로 인해 이 패턴을 변경할 수 없습니다. 그러나 Office 365 DLP가 Office 365 내에서 이 중요한 정보 유형을 찾는 방식의 정확도를 높이기 위해 다음과 같이 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42dad-p106">When searching for an EU Debit Card Number in our example, the definition of that number is strictly defined as 16 digits using a complex pattern, and being subject to the validation of a checksum. We cannot alter this pattern due to the string definition of this sensitive information type. However, we can make the following adjustments to improve the accuracy of how Office 365 DLP finds this sensitive information type within Office 365.</span></span>

### <a name="proximity-modification"></a><span data-ttu-id="42dad-138">근접성 수정</span><span class="sxs-lookup"><span data-stu-id="42dad-138">Proximity modification</span></span>

<span data-ttu-id="42dad-p107">\<Entity\> 요소의 patternProximity 값을 300에서 150자로 수정하여 창을 축소합니다. 이것은 이 규칙에 대한 일치를 알리려면 추측 증거 또는 키워드가 중요한 정보 유형과 좀 더 근접해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="42dad-p107">We'll shrink the window by modifying the patternProximity value in our \<Entity\> element from 300 to 150 characters. This means that our corroborative evidence, or our keywords, must be closer to our sensitive information type in order to signal a match on this rule.</span></span>

<span data-ttu-id="42dad-141">\<Entity id="48da7072-821e-4804-9fab-72ffb48f6f78" patternsProximity="150" recommendedConfidence="85"\></span><span class="sxs-lookup"><span data-stu-id="42dad-141">\<Entity id="48da7072-821e-4804-9fab-72ffb48f6f78" patternsProximity="150" recommendedConfidence="85"\></span></span>

### <a name="keyword-modifications"></a><span data-ttu-id="42dad-142">키워드 수정</span><span class="sxs-lookup"><span data-stu-id="42dad-142">Keyword modifications</span></span>

<span data-ttu-id="42dad-p108">일부 키워드는 가양성의 원인이 될 수 있습니다. 따라서 키워드를 제거할 수 있습니다. 이러한 예에 해당하는 키워드는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="42dad-p108">Some keywords might cause false positives to occur. As a result you might want to remove keywords. Here are the keywords for this example::</span></span>

<span data-ttu-id="42dad-146">\<Keyword id="Keyword\_card\_terms\_dict"\></span><span class="sxs-lookup"><span data-stu-id="42dad-146">\<Keyword id="Keyword\_card\_terms\_dict"\></span></span>

<span data-ttu-id="42dad-147">\<Group\></span><span class="sxs-lookup"><span data-stu-id="42dad-147">group</span></span>

<span data-ttu-id="42dad-148">\<Term\>corporate card\</Term\></span><span class="sxs-lookup"><span data-stu-id="42dad-148">\<Term\>corporate card\</Term\></span></span>

<span data-ttu-id="42dad-149">\<Term\>organization card\</Term\></span><span class="sxs-lookup"><span data-stu-id="42dad-149">\<Term\>organization card\</Term\></span></span>

<span data-ttu-id="42dad-150">\<Term\>acct nbr\</Term\></span><span class="sxs-lookup"><span data-stu-id="42dad-150">\<Term\>acct nbr\</Term\></span></span>

<span data-ttu-id="42dad-151">\<Term\>acct num\</Term\></span><span class="sxs-lookup"><span data-stu-id="42dad-151">\<Term\>acct num\</Term\></span></span>

<span data-ttu-id="42dad-152">\<Term\>acct no\</Term\></span><span class="sxs-lookup"><span data-stu-id="42dad-152">\<Term\>acct no\</Term\></span></span>

<span data-ttu-id="42dad-153">…</span><span class="sxs-lookup"><span data-stu-id="42dad-153"></span></span>

<span data-ttu-id="42dad-154">\</Group\></span><span class="sxs-lookup"><span data-stu-id="42dad-154">group</span></span>

<span data-ttu-id="42dad-155">\</Keyword\></span><span class="sxs-lookup"><span data-stu-id="42dad-155">\</Keyword\></span></span>

### <a name="confidence-modifications"></a><span data-ttu-id="42dad-156">신뢰도 수정</span><span class="sxs-lookup"><span data-stu-id="42dad-156">Confidence modifications</span></span>

<span data-ttu-id="42dad-p109">정의에서 키워드를 제거하는 경우 일반적으로 이 값이 줄여서 이 중요한 정보 유형을 찾을 수 있는 신뢰도를 조정할 수 있습니다. 유럽 직불 카드 번호 유형의 기본 수준은 85입니다.</span><span class="sxs-lookup"><span data-stu-id="42dad-p109">If you remove keywords from the definition, you would typically want to adjust how confident you are that this sensitive information type was found by lowering this value. The default level for EU Debit Card Number type is 85.</span></span>

<span data-ttu-id="42dad-159">\<Entity id="48da7072-821e-4804-9fab-72ffb48f6f78" patternsProximity="150" recommendedConfidence="85"\></span><span class="sxs-lookup"><span data-stu-id="42dad-159">\<Entity id="48da7072-821e-4804-9fab-72ffb48f6f78" patternsProximity="150" recommendedConfidence="85"\></span></span>

<span data-ttu-id="42dad-160">\<Pattern confidenceLevel="85"\></span><span class="sxs-lookup"><span data-stu-id="42dad-160">\<Pattern confidenceLevel="85"\></span></span>

<span data-ttu-id="42dad-161">…</span><span class="sxs-lookup"><span data-stu-id="42dad-161"></span></span>

<span data-ttu-id="42dad-162">\</Pattern\></span><span class="sxs-lookup"><span data-stu-id="42dad-162">pattern</span></span>

<span data-ttu-id="42dad-163">\</Entity\></span><span class="sxs-lookup"><span data-stu-id="42dad-163">entity</span></span>

## <a name="create-a-new-custom-sensitive-information-type"></a><span data-ttu-id="42dad-164">새 사용자 지정 중요한 정보 유형 만들기</span><span class="sxs-lookup"><span data-stu-id="42dad-164">Create a new custom sensitive information type</span></span>

<span data-ttu-id="42dad-165">새 사용자 지정 중요한 정보 유형을 만들려면 먼저 콘텐츠 검색을 사용하여 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="42dad-165">To create a new custom sensitive information type, start by using Content Search to:</span></span>

-   <span data-ttu-id="42dad-166">KQL 쿼리 최적화</span><span class="sxs-lookup"><span data-stu-id="42dad-166">Optimize a KQL query</span></span>

-   <span data-ttu-id="42dad-167">가장 유용한 키워드 찾기</span><span class="sxs-lookup"><span data-stu-id="42dad-167">See which keywords are most useful</span></span>

<span data-ttu-id="42dad-p110">이러한 결과를 사용하여 새 중요한 정보 유형을 만듭니다. 그런 후 작업 환경에 대한 새 중요한 정보 유형을 최적화합니다.</span><span class="sxs-lookup"><span data-stu-id="42dad-p110">Use these results to create a new sensitive information type. Then optimize the new sensitive information type for your environment.</span></span>

<span data-ttu-id="42dad-p111">참고: 유럽 연합 국가의 개인 데이터에 대해 많은 새 중요한 정보 유형이 제공될 예정입니다. 새 중요한 정보 유형을 만들어야 할 경우 먼저 작업 환경에 맞게 조정된 데이터를 대상으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="42dad-p111">Note: Many new sensitive information types are coming soon for personal data in EU countries. If you need to create new sensitive information types, begin by targeting data that is custom to your environment.</span></span>

### <a name="step-1--use-kql-queries-and-key-words-to-find-additional-data-in-your-environment"></a><span data-ttu-id="42dad-172">1단계 - KQL 쿼리 및 키워드를 사용하여 사용 환경에서 추가 데이터 찾기</span><span class="sxs-lookup"><span data-stu-id="42dad-172">Step 1 — Use KQL queries and key words to find additional data in your environment</span></span>

<span data-ttu-id="42dad-p112">GDPR이 적용되는 개인 데이터를 찾기 위한 추가 쿼리를 만들어야 할 수 있습니다. 콘텐츠 검색은 KQL(키워드 쿼리 언어)을 사용하여 데이터를 찾습니다. 대부분의 중요한 정보 유형은 중요한 정보 유형 없이 KQL만 사용하여 정확히 검색할 수 없습니다. 따라서 콘텐츠 검색을 사용하여 KQL 문자열을 테스트 및 최적화하고 이를 사용하여 보다 정확한 새 중요한 정보 유형을 만들고 조정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="42dad-p112">You might need to create additional queries to find personal data that is subject to GDPR. Content Search uses Keyword Query Language (KQL) to find data. Most sensitive data can’t be accurately detected using just KQL without sensitive information types. So the goal is to test and optimize KQL strings using Content Search and then use these to create and tune new sensitive information types where you can achieve even greater accuracy.</span></span>

<span data-ttu-id="42dad-177">KQL을 사용하여 쿼리를 작성하고 최적화하려면 다음 리소스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="42dad-177">Use these resources to formulate and optimize queries using KQL:</span></span>

-   [<span data-ttu-id="42dad-178">KQL(키워드 쿼리 언어) 구문 참조(DMC)</span><span class="sxs-lookup"><span data-stu-id="42dad-178">Keyword Query Language (KQL) syntax reference (DMC)</span></span>](https://docs.microsoft.com/ko-KR/sharepoint/dev/general-development/keyword-query-language-kql-syntax-reference)

-   [<span data-ttu-id="42dad-179">Office 365 보안 및 준수 센터에서 콘텐츠 검색 실행</span><span class="sxs-lookup"><span data-stu-id="42dad-179">Run a Content Search in the Office 365 Security &amp; Compliance Center</span></span>](https://support.office.com/ko-KR/article/Run-a-Content-Search-in-the-Office-365-Security-Compliance-Center-61852fd9-fe8a-4880-a339-cb19ed3bff4a) 

<span data-ttu-id="42dad-p113">콘텐츠 검색은 KQL 쿼리 및 중요한 정보 유형을 개발하는 데 도움이 되는 또 다른 리소스인 키워드를 제공합니다. 키워드 목록은 왜 사용할까요? 많은 항목이 각 키워드와 일치하는 방식을 보여 주는 통계를 얻을 수 있습니다. 이러한 통계는 가장 많이(덜) 효과적인 키워드를 빠르게 식별하는 데 도움이 됩니다. 검색 통계에 대한 자세한 내용은 [콘텐츠 검색 결과에 대한 키워드 통계 보기](https://support.office.com/ko-KR/article/View-keyword-statistics-for-Content-Search-results-9701a024-c52e-43f0-b545-9a53478aec04)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="42dad-p113">Content Search provides another resource to help you develop KQL queries and sensitive information types — keywords. Why use the keyword list? You can get statistics that show how many items match each keyword. This can help you quickly identify which keywords are the most (and least) effective. For more information about search statistics, see [View keyword statistics for Content Search results](https://support.office.com/ko-KR/article/View-keyword-statistics-for-Content-Search-results-9701a024-c52e-43f0-b545-9a53478aec04).</span></span>

<span data-ttu-id="42dad-p114">각 행의 키워드는 만들어지는 검색 쿼리에서 OR 연산자로 연결됩니다. 행에 키워드 구(괄호 사용)를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42dad-p114">Keywords on each row are connected by the OR operator in the search query that's created. You can also use a keyword phrase (surrounded by parentheses) in a row.</span></span>

<span data-ttu-id="42dad-187">자세한 내용은 [콘텐츠 검색에 대한 키워드 쿼리 및 검색 조건](https://support.office.com/ko-KR/article/Keyword-queries-and-search-conditions-for-Content-Search-c4639c2e-7223-4302-8e0d-b6e10f1c3be3)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="42dad-187">For more information about creating a search query and using conditions, see [Keyword queries for Content Search](https://support.office.com/ko-KR/article/Keyword-queries-and-search-conditions-for-Content-Search-c4639c2e-7223-4302-8e0d-b6e10f1c3be3).</span></span>

### <a name="exampleusing-content-search-to-identify-email-addresses"></a><span data-ttu-id="42dad-188">예제 - 콘텐츠 검색을 사용하여 전자 메일 주소 식별</span><span class="sxs-lookup"><span data-stu-id="42dad-188">Example—Using Content Search to identify email addresses</span></span>

<span data-ttu-id="42dad-p115">전자 메일 주소는 데이터 주체와 관련된 중요한 정보로 간주됩니다. 다음은 콘텐츠 검색이 어떻게 유용할 수 있는지를 보여 주는 간단한 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="42dad-p115">Email addresses are considered sensitive information related to data subjects. This is a simple example to demonstrate how Content Search can help.</span></span>

<span data-ttu-id="42dad-p116">KQL 및 키워드를 함께 사용할 수는 없습니다. 이러한 도구를 개별적으로 사용하여 쿼리를 조정하고, 중요한 정보 유형에서 유용할 수 있는 키워드를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="42dad-p116">KQL and keywords can’t be used together. Use these tools separately to hone your query and determine keywords that might be useful in sensitive information types.</span></span>

### <a name="kql-query"></a><span data-ttu-id="42dad-193">KQL 쿼리</span><span class="sxs-lookup"><span data-stu-id="42dad-193">KQL query</span></span>

<span data-ttu-id="42dad-194">(^|\\b)([a-zA-Z0-9\_\\-\\.]+)@([a-zA-Z0-9\_\\-\\.]+)\\.([a-zA-Z]{2,5})($|\\b)</span><span class="sxs-lookup"><span data-stu-id="42dad-194">(^|\\b)([a-zA-Z0-9\_\\-\\.]+)@([a-zA-Z0-9\_\\-\\.]+)\\.([a-zA-Z]{2,5})($|\\b)</span></span>

<span data-ttu-id="42dad-195">참고:</span><span class="sxs-lookup"><span data-stu-id="42dad-195">Notes:</span></span>

-   <span data-ttu-id="42dad-196">근접 검색에는 NEAR 및 ONEAR을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42dad-196">You can use NEAR and ONEAR for proximity searches.</span></span>

-   <span data-ttu-id="42dad-197">그렇지만 KQL은 Regex 클래스가 있는 쿼리(예: IdRef="Regex\_email\_address")를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="42dad-197">Unfortunately, KQL doesn’t support queries with the Regex Class (ex: IdRef="Regex\_email\_address")</span></span>

### <a name="keywords"></a><span data-ttu-id="42dad-198">키워드</span><span class="sxs-lookup"><span data-stu-id="42dad-198">Keywords</span></span>

<span data-ttu-id="42dad-p117">각 키워드를 별도 줄에 입력합니다. 예제 키워드:</span><span class="sxs-lookup"><span data-stu-id="42dad-p117">Enter each keyword on a separate line. Example keywords:</span></span>

-   <span data-ttu-id="42dad-201">전자 메일 주소</span><span class="sxs-lookup"><span data-stu-id="42dad-201">Email address</span></span>

-   <span data-ttu-id="42dad-202">메일</span><span class="sxs-lookup"><span data-stu-id="42dad-202">mail</span></span>

-   <span data-ttu-id="42dad-203">연락처</span><span class="sxs-lookup"><span data-stu-id="42dad-203">contact</span></span>

-   <span data-ttu-id="42dad-204">보낸 사람</span><span class="sxs-lookup"><span data-stu-id="42dad-204">Sender</span></span>

-   <span data-ttu-id="42dad-205">받는 사람</span><span class="sxs-lookup"><span data-stu-id="42dad-205">Recipient</span></span>

-   <span data-ttu-id="42dad-206">참조</span><span class="sxs-lookup"><span data-stu-id="42dad-206">Cc</span></span>

-   <span data-ttu-id="42dad-207">숨은 참조</span><span class="sxs-lookup"><span data-stu-id="42dad-207">Bcc</span></span>

<span data-ttu-id="42dad-208">이 예제에서는 키워드가 필요하지 않으며 잘못된 가양성 결과를 많이 생성한다는 것을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42dad-208">In this example, you might learn the keywords are not necessary and produce a lot of false positive results.</span></span>

### <a name="step-2--create-a-new-custom-sensitive-information-type"></a><span data-ttu-id="42dad-209">2단계 - 새 사용자 지정 중요한 정보 유형 만들기</span><span class="sxs-lookup"><span data-stu-id="42dad-209">Step 2 — Create a new custom sensitive information type</span></span>

<span data-ttu-id="42dad-p118">KQL 쿼리 및 키워드를 사용하여 중요한 정보를 식별한 후에 이러한 정보를 사용하여 새 사용자 지정 중요한 정보 유형을 만듭니다. 많은 경우에 적절한 수준의 정확도를 얻기 위해 정교한 중요한 정보 유형이 필요합니다. 그런 후 콘텐츠 검색, DLP 정책 및 기타 도구, 다른 KQL 쿼리 내에서 이러한 사용자 지정 중요한 정보 유형을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42dad-p118">After using KQL queries and keywords to identify sensitive information, use these to create new custom sensitive information types. In many cases, you’ll require the sophistication of sensitive information types to achieve the right level of accuracy. You can then use these custom sensitive information types with Content Search, in DLP policies and other tools, and within other KQL queries.</span></span>

<span data-ttu-id="42dad-p119">모범 사례는 기존의 중요한 정보 유형을 기준으로 새 중요한 정보 유형을 만드는 것입니다. 이 문서 앞부분에 설명된 것과 동일한 프로세스를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="42dad-p119">The best practice is to create a new sensitive information type based on an existing one. Use the same process described earlier in this article.</span></span>

### <a name="example--create-a-new-sensitive-information-for-email-addresses"></a><span data-ttu-id="42dad-215">예제 - 전자 메일 주소에 대한 새 중요한 정보 만들기</span><span class="sxs-lookup"><span data-stu-id="42dad-215">Example — Create a new sensitive information for email addresses</span></span> 

<span data-ttu-id="42dad-p120">전자 메일 주소가 간단하기 때문에 계속 예제로 사용하겠습니다. 다음 표에서는 새 전자 메일 중요한 정보 유형에 대해 권장되는 수정 내용을 자세히 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="42dad-p120">We’ll continue with the email address as an example because it’s simple. The following table details the modifications recommended for a new email sensitive information type.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="42dad-218"><strong>단계</strong></span><span class="sxs-lookup"><span data-stu-id="42dad-218"><strong>Step</strong></span></span></th>
<th align="left"><span data-ttu-id="42dad-219"><strong>수정 </strong></span><span class="sxs-lookup"><span data-stu-id="42dad-219"><strong>Modification</strong></span></span></th>
<th align="left"><span data-ttu-id="42dad-220"><strong>예제 XML 구문</strong></span><span class="sxs-lookup"><span data-stu-id="42dad-220"><strong>Example XML syntax</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="42dad-221">1</span><span class="sxs-lookup"><span data-stu-id="42dad-221">1.</span></span></td>
<td align="left"><span data-ttu-id="42dad-222">IdRef 속성 설정</span><span class="sxs-lookup"><span data-stu-id="42dad-222">Set the IdRef property</span></span>
<p><span data-ttu-id="42dad-p121">&lt;Entity&gt; 요소 내에서 idRef 속성이 고유한 값이 되도록 &lt;IdMatch&gt; 요소를 수정합니다. 이 값은 전자 메일 주소를 찾는 정규식을 정의하는 요소를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="42dad-p121">Within the &lt;Entity&gt; element, modify the &lt;IdMatch&gt; element so that its idRef property is = to a unique value. This value will point to an element that defines our regular expression to find email addresses.</span></span></p></td>
<td align="left"><span data-ttu-id="42dad-225">IdRef=&quot;Regex_email_address&quot;</span><span class="sxs-lookup"><span data-stu-id="42dad-225">IdRef=&quot;Regex_email_address&quot;</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="42dad-226">2</span><span class="sxs-lookup"><span data-stu-id="42dad-226">2.</span></span></td>
<td align="left"><p><span data-ttu-id="42dad-227">근접 특성</span><span class="sxs-lookup"><span data-stu-id="42dad-227">Proximity attribute</span></span></p>
<p><span data-ttu-id="42dad-228">&lt;Entity&gt; 요소의 patternProximity 값을 300으로 지정해서 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="42dad-228">We'll start with a patternProximity value in our &lt;Entity&gt; element of 300.</span></span></p></td>
<td align="left"><span data-ttu-id="42dad-229">patternsProximity=&quot;300&quot;</span><span class="sxs-lookup"><span data-stu-id="42dad-229">patternsProximity=&quot;300&quot;</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="42dad-230">3</span><span class="sxs-lookup"><span data-stu-id="42dad-230">3.</span></span></td>
<td align="left"><p><span data-ttu-id="42dad-231">신뢰 수준</span><span class="sxs-lookup"><span data-stu-id="42dad-231">Confidence Level</span></span></p>
<p><span data-ttu-id="42dad-p122">recommendedConfidence 속성을 정확한 일치 항목을 찾을 수 있다고 생각되는 신뢰도로 설정합니다. 보다 정확한 결과를 가져오기 위해서는 대표적인 데이터 집합을 사용해서 테스트해야 할 수 있습니다. 초기 설정으로 이 값을 75로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="42dad-p122">Set the recommendedConfidence property to a value you feel will represent the confidence of finding an accurate match. This will likely require testing with a representative data set to get an accurate result. As an initial setting, set this value to 75.</span></span></p></td>
<td align="left"><p><span data-ttu-id="42dad-235">recommendedConfidence=&quot;75&quot;&gt;</span><span class="sxs-lookup"><span data-stu-id="42dad-235">recommendedConfidence=&quot;75&quot;&gt;</span></span></p>
<p><span data-ttu-id="42dad-236">이러한 결합된 처음 세 가지 요소에 대한 결과 XML은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="42dad-236">The resulting XML for these first three elements combined looks like this:</span></span></p>
<p><span data-ttu-id="42dad-237">&lt;Entity id=&quot;42e6348e-27f0-4774-9604-d470cb3e219a&quot; patternsProximity=&quot;300&quot; recommendedConfidence=&quot;75&quot;&gt;</span><span class="sxs-lookup"><span data-stu-id="42dad-237">&lt;Entity id=&quot;42e6348e-27f0-4774-9604-d470cb3e219a&quot; patternsProximity=&quot;300&quot; recommendedConfidence=&quot;75&quot;&gt;</span></span></p>
<p><span data-ttu-id="42dad-238">&lt;Pattern confidenceLevel=&quot;75&quot;&gt;</span><span class="sxs-lookup"><span data-stu-id="42dad-238">&lt;Pattern confidenceLevel=&quot;75&quot;&gt;</span></span></p>
<p><span data-ttu-id="42dad-239">&lt;IdMatch idRef=&quot;Regex_email_address&quot; /&gt;</span><span class="sxs-lookup"><span data-stu-id="42dad-239">&lt;IdMatch idRef=&quot;Regex_email_address&quot; /&gt;</span></span></p>
<p><span data-ttu-id="42dad-240">&lt;Any minMatches=&quot;1&quot;&gt;</span><span class="sxs-lookup"><span data-stu-id="42dad-240">&lt;Any minMatches=&quot;1&quot;&gt;</span></span></p>
<p><span data-ttu-id="42dad-241">&lt;Match idRef=&quot;Keyword_email_terms&quot; /&gt;</span><span class="sxs-lookup"><span data-stu-id="42dad-241">&lt;Match idRef=&quot;Keyword_email_terms&quot; /&gt;</span></span></p>
<p><span data-ttu-id="42dad-242">&lt;/Any&gt;</span><span class="sxs-lookup"><span data-stu-id="42dad-242">Any</span></span></p>
<p><span data-ttu-id="42dad-243">&lt;/Pattern&gt;</span><span class="sxs-lookup"><span data-stu-id="42dad-243">pattern</span></span></p>
<p><span data-ttu-id="42dad-244">&lt;/Entity&gt;</span><span class="sxs-lookup"><span data-stu-id="42dad-244">entity</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="42dad-245">4</span><span class="sxs-lookup"><span data-stu-id="42dad-245">4.</span></span></td>
<td align="left"><p><span data-ttu-id="42dad-246">Regex 요소</span><span class="sxs-lookup"><span data-stu-id="42dad-246">Regex element</span></span></p>
<p><span data-ttu-id="42dad-247">새 &lt;Regex&gt; 요소를 전자 메일 주소를 식별하는 데 사용되는 정규식을 정의하는 &lt;Entity&gt; 요소 바로 아래에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="42dad-247">Add a new &lt;Regex&gt; element immediately be below the &lt;Entity&gt; elements that defines the regular expression used to identify email addresses.</span></span></p></td>
<td align="left"><span data-ttu-id="42dad-248">&lt;Regex id=&quot;Regex_email_address&quot;&gt;(^|\b)([a-zA-Z0-9_\-\.]+)@([a-zA-Z0-9_\-\.]+)\.([a-zA-Z]{2,5})($|\b)&lt;/Regex&gt;</span><span class="sxs-lookup"><span data-stu-id="42dad-248">&lt;Regex id=&quot;Regex_email_address&quot;&gt;(^|\b)([a-zA-Z0-9_\-\.]+)@([a-zA-Z0-9_\-\.]+)\.([a-zA-Z]{2,5})($|\b)&lt;/Regex&gt;</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="42dad-249">5</span><span class="sxs-lookup"><span data-stu-id="42dad-249">5.</span></span></td>
<td align="left"><p><span data-ttu-id="42dad-250">키워드</span><span class="sxs-lookup"><span data-stu-id="42dad-250">Keywords</span></span></p>
<p><span data-ttu-id="42dad-p123">새 &lt;Keyword&gt; 요소를 전자 메일 주소 관련 키워드의 목록을 정의하는 &lt;Regex&gt; 요소 아래에 추가합니다. &lt;Keyword&gt; 요소의 ID 값이 &lt;Entity&gt;&lt;Pattern&gt; 요소의 &lt;Match idRef&gt; 값과 일치하는지 확인합니다. 필요한 경우 사용자 고유의 키워드를 계속 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42dad-p123">Add a new &lt;Keyword&gt; element below the &lt;Regex&gt; element that defines list of email address related keywords. Ensure that the id value for the &lt;Keyword&gt; element matches the &lt;Match idRef&gt; value in the &lt;Entity&gt;&lt;Pattern&gt; element. You may continue to add your own keywords if needed.</span></span></p>
<p><span data-ttu-id="42dad-p124">키워드를 전자 메일 중요한 정보 유형에 포함할 필요는 없습니다. 예제로 제공되기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="42dad-p124">Keywords are likely not necessary to include in an email sensitive information type. These are provided as an example.</span></span></p></td>
<td align="left"><p><span data-ttu-id="42dad-256">&lt;Keyword id=&quot;Keyword_email_terms&quot;&gt;</span><span class="sxs-lookup"><span data-stu-id="42dad-256">&lt;Keyword id=&quot;Keyword_email_terms&quot;&gt;</span></span></p>
<p><span data-ttu-id="42dad-257">&lt;Group&gt;</span><span class="sxs-lookup"><span data-stu-id="42dad-257">group</span></span></p>
<p><span data-ttu-id="42dad-258">&lt;Term&gt;email&lt;/Term&gt;</span><span class="sxs-lookup"><span data-stu-id="42dad-258">&lt;Term&gt;email&lt;/Term&gt;</span></span></p>
<p><span data-ttu-id="42dad-259">&lt;Term&gt;email address&lt;/Term&gt;</span><span class="sxs-lookup"><span data-stu-id="42dad-259">&lt;Term&gt;email address&lt;/Term&gt;</span></span></p>
<p><span data-ttu-id="42dad-260">&lt;Term&gt;contact&lt;/Term&gt;</span><span class="sxs-lookup"><span data-stu-id="42dad-260">&lt;Term&gt;contact&lt;/Term&gt;</span></span></p>
<p><span data-ttu-id="42dad-261">&lt;/Group&gt;</span><span class="sxs-lookup"><span data-stu-id="42dad-261">group</span></span></p>
<p><span data-ttu-id="42dad-262">&lt;/Keyword&gt;</span><span class="sxs-lookup"><span data-stu-id="42dad-262">&lt;/Keyword&gt;</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="42dad-263">6</span><span class="sxs-lookup"><span data-stu-id="42dad-263">6.</span></span></td>
<td align="left"><p><span data-ttu-id="42dad-264">LocalizedStrings 요소</span><span class="sxs-lookup"><span data-stu-id="42dad-264">LocalizedStrings element</span></span></p>
<p><span data-ttu-id="42dad-265">&lt;LocalizedStrings&gt;&lt;Resource&gt; 요소에서 중요한 정보 유형을 식별하는 고유한 이름이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="42dad-265">In the &lt;LocalizedStrings&gt;&lt;Resource&gt; element ensure that you have a unique name that identifies your sensitive information type.</span></span></p></td>
<td align="left"><p><span data-ttu-id="42dad-266">&lt;LocalizedStrings&gt;</span><span class="sxs-lookup"><span data-stu-id="42dad-266">&lt;LocalizedStrings&gt;</span></span></p>
<p><span data-ttu-id="42dad-267">&lt;Resource idRef=&quot;42e6348e-27f0-4774-9604-d470cb3e219a&quot;&gt;</span><span class="sxs-lookup"><span data-stu-id="42dad-267">&lt;Resource idRef=&quot;42e6348e-27f0-4774-9604-d470cb3e219a&quot;&gt;</span></span></p>
<p><span data-ttu-id="42dad-268">&lt;Name default=&quot;true&quot; langcode=&quot;en-us&quot;&gt;Email Address&lt;/Name&gt;</span><span class="sxs-lookup"><span data-stu-id="42dad-268">&lt;Name default=&quot;true&quot; langcode=&quot;en-us&quot;&gt;Email Address&lt;/Name&gt;</span></span></p>
<p><span data-ttu-id="42dad-269">&lt;Description default=&quot;true&quot; langcode=&quot;en-us&quot;&gt;Detects email addresses.&lt;/Description&gt;</span><span class="sxs-lookup"><span data-stu-id="42dad-269">&lt;Description default=&quot;true&quot; langcode=&quot;en-us&quot;&gt;Detects email addresses.&lt;/Description&gt;</span></span></p>
<p><span data-ttu-id="42dad-270">&lt;/Resource&gt;</span><span class="sxs-lookup"><span data-stu-id="42dad-270">resource</span></span></p>
<p><span data-ttu-id="42dad-271">&lt;/LocalizedStrings&gt;</span><span class="sxs-lookup"><span data-stu-id="42dad-271">&lt;/LocalizedStrings&gt;</span></span></p></td>
</tr>
</tbody>
</table>

## <a name="create-a-new-sensitive-information-type-with-example-powershell-and-xml-file--contoso-customer-number"></a><span data-ttu-id="42dad-272">예제 PowerShell 및 XML 파일을 사용하여 새 중요한 정보 유형 만들기 — Contoso 고객 번호</span><span class="sxs-lookup"><span data-stu-id="42dad-272">Create a new sensitive information type with example PowerShell and XML file — Contoso customer number</span></span>

<span data-ttu-id="42dad-p125">Contoso는 CCN(Contoso 고객 번호)을 사용하여 고객 데이터베이스에 있는 각 고객을 식별합니다. CCN은 다음 분류법으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="42dad-p125">Contoso uses a Contoso Customer Number (CCN) to identify each customer in their customer database. A CCN consists of the following taxonomy:</span></span>

-   <span data-ttu-id="42dad-p126">레코드가 생성된 연도를 나타내는 두 자리 숫자. Contoso는 2002년에 설립되었으므로 가장 앞에 나올 수 있는 값은 02입니다.</span><span class="sxs-lookup"><span data-stu-id="42dad-p126">Two digits to represent the year that the record was created. Contoso was founded in 2002; therefore, the earliest possible value would be 02.</span></span>

-   <span data-ttu-id="42dad-p127">레코드를 만든 파트너 에이전시를 나타내는 세 자리 숫자. 가능한 에이전시 값의 범위는 000에서 999까지입니다.</span><span class="sxs-lookup"><span data-stu-id="42dad-p127">Three digits to represent the partner agency that created the record. Possible agency values range from 000 to 999.</span></span>

-   <span data-ttu-id="42dad-p128">사업 부문을 나타내는 영문자. 가능한 값은 a-z이며 대/소문자를 구분하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="42dad-p128">An alpha character to represent the line of business. Possible values are a-z and should be case insensitive.</span></span>

-   <span data-ttu-id="42dad-p129">네 자리 일련 번호. 가능한 일련 번호 값의 범위는 0000에서 9999까지입니다.</span><span class="sxs-lookup"><span data-stu-id="42dad-p129">A four-digit serial number. Possible serial number values range from 0000 to 9999.</span></span>

<span data-ttu-id="42dad-283">예제 CCN:</span><span class="sxs-lookup"><span data-stu-id="42dad-283">Example CCNs:</span></span>

> <span data-ttu-id="42dad-284">15080P9562</span><span class="sxs-lookup"><span data-stu-id="42dad-284">15080P9562</span></span>
>
> <span data-ttu-id="42dad-285">14040O1119</span><span class="sxs-lookup"><span data-stu-id="42dad-285">14040O1119</span></span>
>
> <span data-ttu-id="42dad-286">15020J8317</span><span class="sxs-lookup"><span data-stu-id="42dad-286">15020J8317</span></span>
>
> <span data-ttu-id="42dad-287">14050E2330</span><span class="sxs-lookup"><span data-stu-id="42dad-287">14050E2330</span></span>
>
> <span data-ttu-id="42dad-288">16050E2166</span><span class="sxs-lookup"><span data-stu-id="42dad-288">16050E2166</span></span>
>
> <span data-ttu-id="42dad-289">17040O1118</span><span class="sxs-lookup"><span data-stu-id="42dad-289">17040O1118</span></span>

<span data-ttu-id="42dad-290">Contoso는 내부 서신, 외부 서신, 문서 등에서 항상 CCN을 사용하여 고객을 참조합니다. Office 365에서는 사용자 지정 중요한 정보 유형을 만들어 CCN의 사용을 감지할 수 있으므로 이러한 형식의 개인 데이터를 사용할 때 보호 기능을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42dad-290">Contoso always refers to customers by using a CCN in internal correspondence, external correspondence, documents, etc. They would like to create a custom sensitive information type to detect the use of CCN in Office 365 so that they may apply protection to the use of this form of personal data.</span></span>

### <a name="create-a-new-sensitive-information-type-for-contoso-customer-number"></a><span data-ttu-id="42dad-291">Contoso 고객 번호에 대한 새 중요한 정보 유형 만들기</span><span class="sxs-lookup"><span data-stu-id="42dad-291">Create a new sensitive information type for Contoso customer number</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="42dad-292"><strong>단계</strong></span><span class="sxs-lookup"><span data-stu-id="42dad-292"><strong>Step</strong></span></span></th>
<th align="left"><span data-ttu-id="42dad-293"><strong>작업</strong></span><span class="sxs-lookup"><span data-stu-id="42dad-293"><strong>action</strong></span></span></th>
<th align="left"><span data-ttu-id="42dad-294"><strong>결과</strong></span><span class="sxs-lookup"><span data-stu-id="42dad-294"><strong>Result</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="42dad-295">1</span><span class="sxs-lookup"><span data-stu-id="42dad-295">1.</span></span></td>
<td align="left"><span data-ttu-id="42dad-296">Contoso에서는 PowerShell 및 콘텐츠 검색을 사용하여 CCN 예제 집합과 일치하는 문서를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="42dad-296">Contoso uses PowerShell and Content Search to find documents that match an example set of CCNs.</span></span></td>
<td align="left">

<p><span data-ttu-id="42dad-297">#Office 365 보안 및 준수 센터에 연결</span><span class="sxs-lookup"><span data-stu-id="42dad-297">#Connect to Office 365 Security &amp; Compliance Center</span></span></p>
<p><span data-ttu-id="42dad-298">$adminUser = &quot;alland@contoso.com&quot;</span><span class="sxs-lookup"><span data-stu-id="42dad-298">$adminUser = &quot;alland@contoso.com&quot;</span></span></p>
<p><span data-ttu-id="42dad-299">Connect-IPPSSession -UserPrincipalName $adminUser</span><span class="sxs-lookup"><span data-stu-id="42dad-299">Connect-IPPSSession -UserPrincipalName $adminUser</span></span></p>
<p><span data-ttu-id="42dad-300">#만들기 및 샘플 데이터 검색 시작</span><span class="sxs-lookup"><span data-stu-id="42dad-300">#Create &amp; start search for sample data</span></span></p>
<p><span data-ttu-id="42dad-301">$searchName = &quot;Sample Customer Information Search&quot;</span><span class="sxs-lookup"><span data-stu-id="42dad-301">$searchName = &quot;Sample Customer Information Search&quot;</span></span></p>
<p><span data-ttu-id="42dad-302">$searchQuery = &quot;15080P9562 OR 14040O1119 OR 15020J8317 OR 14050E2330 OR 16050E2166 OR 17040O1118&quot;</span><span class="sxs-lookup"><span data-stu-id="42dad-302">$searchQuery = &quot;15080P9562 OR 14040O1119 OR 15020J8317 OR 14050E2330 OR 16050E2166 OR 17040O1118&quot;</span></span></p>
<p><span data-ttu-id="42dad-303">New-ComplianceSearch -Name $searchName -SharePointLocation All -ExchangeLocation All -ContentMatchQuery $searchQuery</span><span class="sxs-lookup"><span data-stu-id="42dad-303">New-ComplianceSearch -Name $searchName -SharePointLocation All -ExchangeLocation All -ContentMatchQuery $searchQuery</span></span></p>
<p><span data-ttu-id="42dad-304">Start-ComplianceSearch -Identity $searchName</span><span class="sxs-lookup"><span data-stu-id="42dad-304">Start-ComplianceSearch -Identity $searchName</span></span></p>
</td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="42dad-305">2</span><span class="sxs-lookup"><span data-stu-id="42dad-305">2.</span></span></td>
<td align="left"><span data-ttu-id="42dad-p130">Contoso에서는 결과를 분석합니다. CCN이 사용될 때마다 EU 형식이 지정된 날짜가 사용되고 이러한 키워드 중 하나가 300 문자의 근접성 내에서도 사용되었습니다.</span><span class="sxs-lookup"><span data-stu-id="42dad-p130">Contoso analyzes the results. Every time the CCN was used, an EU formatted date was used and one of these keywords were also used within a proximity of 300 characters.</span></span></td>
<td align="left"><span data-ttu-id="42dad-308">customer number, customer no, customer #, customer#, Contoso customer</span><span class="sxs-lookup"><span data-stu-id="42dad-308">customer number, customer no, customer #, customer#, Contoso customer</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="42dad-309">3</span><span class="sxs-lookup"><span data-stu-id="42dad-309">3.</span></span></td>
<td align="left"><span data-ttu-id="42dad-310">Contoso는 CCN를 식별하기 위해 다음과 같은 정규식(RegEx) 패턴을 개발했습니다.</span><span class="sxs-lookup"><span data-stu-id="42dad-310">Contoso developed the following Regular Expression (RegEx) pattern to identify their CCN.</span></span></td>
<td align="left"><span data-ttu-id="42dad-311">[0-1][0-9][0-9]{3}[A-Za-z][0-9]{4}</span><span class="sxs-lookup"><span data-stu-id="42dad-311">[0-1][0-9][0-9]{3}[A-Za-z][0-9]{4}</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="42dad-312">4</span><span class="sxs-lookup"><span data-stu-id="42dad-312">4.</span></span></td>
<td align="left"><span data-ttu-id="42dad-313">Contoso는 다양한 자회사에서 사용되는 형식에서 EU 날짜를 식별하기 위해 다음과 같은 정규식(RegEx) 패턴을 개발했습니다.</span><span class="sxs-lookup"><span data-stu-id="42dad-313">Contoso developed the following Regular Expression (RegEx) pattern to identify EU dates in the formats used by their various subsidiaries.</span></span></td>
<td align="left">
````xml
(0?[1-9]|[12][0-9]|3[0-1])[\/-](0?[1-9]|1[0-2]|j\x00e4n(uar)?|jan(uary|uari|uar|eiro|vier|v)?|ene(ro)?|genn(aio)?|‌ feb(ruary|ruari|rero|braio|ruar|br)?|f\x00e9vr(ier)?|fev(ereiro)?|mar(zo|o|ch|s)?|m\x00e4rz|maart|‌ apr(ile|il)?|abr(il)?|avril|may(o)?|magg(io)?|mai|mei|mai(o)?|jun(io|i|e|ho)?|giugno|juin|jul(y|io|i|ho)?|lu(glio)?|juil(let)?|ag(o|osto)?|aug(ustus|ust)?|ao\x00fbt|sep|sept(ember|iembre|embre)?|sett(embre)?|set(embro)?|‌ oct(ober|ubre|obre)?|ott(obre)?|okt(ober)?|out(ubro)?|nov(ember|iembre|embre|embro)?|dec(ember)?|‌ dic(iembre|embre)?|dez(ember|embro)?|d\x00e9c(embre)?)[ \/-](19|20)?[0-9]{2}
````
</td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="42dad-314">5</span><span class="sxs-lookup"><span data-stu-id="42dad-314">5.</span></span></td>
<td align="left"><span data-ttu-id="42dad-315">Contoso는 PowerShell을 사용하여 3개의 고유한 GUID를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="42dad-315">Contoso uses PowerShell to generate three unique GUIDs.</span></span></td>
<td align="left"><p><span data-ttu-id="42dad-316">#Generate a unique GUID for RulePack Id, Publisher Id, and Entity Id</span><span class="sxs-lookup"><span data-stu-id="42dad-316">#Generate a unique GUID for RulePack Id, Publisher Id, and Entity Id</span></span></p>
<p>[guid]::NewGuid().Guid</p>
<p>[guid]::NewGuid().Guid</p>
<p>[guid]::NewGuid().Guid</p></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="42dad-317">6</span><span class="sxs-lookup"><span data-stu-id="42dad-317">6.</span></span></td>
<td align="left"><span data-ttu-id="42dad-318">Contoso는 중요한 항목 유형 규칙에 대해 다음과 같은 매개 변수를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="42dad-318">Contoso defines the following parameters for their sensitive item type rule.</span></span></td>
<td align="left"><p><span data-ttu-id="42dad-319">Name: Contoso Customer Number (CCN)</span><span class="sxs-lookup"><span data-stu-id="42dad-319">Name: Contoso Customer Number (CCN)</span></span></p>
<p><span data-ttu-id="42dad-320">Description: Contoso Customer Number (CCN) that looks for additional keywords and EU formatted date</span><span class="sxs-lookup"><span data-stu-id="42dad-320">Description: Contoso Customer Number (CCN) that looks for additional keywords and EU formatted date</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="42dad-321">7</span><span class="sxs-lookup"><span data-stu-id="42dad-321">7.</span></span></td>
<td align="left"><span data-ttu-id="42dad-322">Contoso는 CCN(Contoso 고객 번호)을 검색하기 위한 새 중요한 정보 유형에 대해 XML 파일을 만들고 UTF-8 인코딩을 사용하는 C:\Scripts\ContosoCCN.xml으로 로컬 파일 시스템에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="42dad-322">Contoso creates an XML file for a new sensitive information type to detect a Contoso Customer Number (CCN) and saves this to a local file system as C:\Scripts\ContosoCCN.xml in with UTF-8 encoding.</span></span></td>
<td align="left"><span data-ttu-id="42dad-323">이 표 아래의 XML 파일을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="42dad-323">See the XML file below this table.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="42dad-324">8</span><span class="sxs-lookup"><span data-stu-id="42dad-324">8%</span></span></td>
<td align="left"><span data-ttu-id="42dad-325">Contoso는 다음 PowerShell을 사용하여 사용자 지정 중요한 정보 유형을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="42dad-325">Contoso creates the custom sensitive information type with the following PowerShell.</span></span></td>
<td align="left"><p><span data-ttu-id="42dad-326">#Office 365 보안 및 준수 센터에 연결</span><span class="sxs-lookup"><span data-stu-id="42dad-326">#Connect to Office 365 Security &amp; Compliance Center</span></span></p>
<p><span data-ttu-id="42dad-327">$adminUser = &quot;alland@contoso.com&quot;</span><span class="sxs-lookup"><span data-stu-id="42dad-327">$adminUser = &quot;alland@contoso.com&quot;</span></span></p>
<p><span data-ttu-id="42dad-328">Connect-IPPSSession -UserPrincipalName $adminUser</span><span class="sxs-lookup"><span data-stu-id="42dad-328">Connect-IPPSSession -UserPrincipalName $adminUser</span></span></p>
<p><span data-ttu-id="42dad-329">#새 중요한 정보 유형 만들기</span><span class="sxs-lookup"><span data-stu-id="42dad-329">#Create new Sensitive Information Type</span></span></p>
<p><span data-ttu-id="42dad-330">New-DlpSensitiveInformationTypeRulePackage -FileData (Get-Content -Path &quot;C:\Scripts\ContosoCCN.xml&quot; -Encoding Byte -ReadCount 0)</span><span class="sxs-lookup"><span data-stu-id="42dad-330">New-DlpSensitiveInformationTypeRulePackage -FileData (Get-Content -Path &quot;C:\Scripts\ContosoCCN.xml&quot; -Encoding Byte -ReadCount 0)</span></span></p></td>
</tr>
</tbody>
</table>

### <a name="example-xml-file-for-the-new-sensitive-information-type-step-7"></a><span data-ttu-id="42dad-331">새 중요 한 정보 유형에 대한 예제 XML 파일(7단계)</span><span class="sxs-lookup"><span data-stu-id="42dad-331">Example XML file for the new sensitive information type (step 7)</span></span>
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
