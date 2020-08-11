---
title: Microsoft 365 검색에서 테넌트 격리
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
f1.keywords:
- NOCSH
description: 이 문서에서는 테 넌 트 격리가 Microsoft 365 검색에서 테 넌 트 데이터를 분리 하는 방법에 대 한 설명을 찾습니다.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: b887088799c83422a6bc5797a76dde73a58e2f29
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605590"
---
# <a name="tenant-isolation-in-microsoft-365-search"></a><span data-ttu-id="57389-103">Microsoft 365 검색에서 테넌트 격리</span><span class="sxs-lookup"><span data-stu-id="57389-103">Tenant Isolation in Microsoft 365 Search</span></span>

<span data-ttu-id="57389-104">SharePoint Online 검색에서는 테 넌 트 간의 정보 누출을 방지 하는 보호 기능을 사용 하 여 공유 데이터 구조의 효율성을 균형 있게 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="57389-104">SharePoint Online search uses a tenant separation model that balances the efficiency of shared data structures with protection against information leaking between tenants.</span></span> <span data-ttu-id="57389-105">이 모델에서는 다음과 같은 검색 기능을 사용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="57389-105">With this model, we prevent the Search features from:</span></span>

- <span data-ttu-id="57389-106">다른 테 넌 트의 문서가 포함 된 쿼리 결과 반환</span><span class="sxs-lookup"><span data-stu-id="57389-106">Returning query results that contain documents from other tenants</span></span>
- <span data-ttu-id="57389-107">숙련 된 사용자가 다른 테 넌 트에 대 한 정보를 유추할 수 있도록 쿼리 결과에 충분 한 정보 노출</span><span class="sxs-lookup"><span data-stu-id="57389-107">Exposing sufficient information in query results that a skilled user could infer information about other tenants</span></span>
- <span data-ttu-id="57389-108">다른 테 넌 트의 스키마 또는 설정 표시</span><span class="sxs-lookup"><span data-stu-id="57389-108">Showing schema or settings from another tenant</span></span>
- <span data-ttu-id="57389-109">테 넌 트 또는 저장소 간의 분석 처리 정보가 잘못 된 테 넌 트에 섞여 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57389-109">Mixing analytics processing information between tenants or store results in the wrong tenant</span></span>
- <span data-ttu-id="57389-110">다른 테 넌 트에서 사전 항목 사용</span><span class="sxs-lookup"><span data-stu-id="57389-110">Using dictionary entries from another tenant</span></span>

<span data-ttu-id="57389-111">각 유형의 테 넌 트 데이터에 대해 실수로 인 한 정보 누출을 방지 하기 위해 코드에 보호 계층을 하나 이상 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="57389-111">For each type of tenant data, we use one or more layers of protection in the code to prevent accidental leaking of information.</span></span> <span data-ttu-id="57389-112">가장 중요 한 데이터는 대부분의 보호 계층을 통해 단일 오류로 인해 실제 또는 인식 된 정보 누출을 수행 하지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="57389-112">The most critical data has the most layers of protection to make sure that a single defect doesn't result in actual or perceived information leakage.</span></span>

## <a name="tenant-separation-for-the-search-index"></a><span data-ttu-id="57389-113">검색 인덱스에 대 한 테 넌 트 분리</span><span class="sxs-lookup"><span data-stu-id="57389-113">Tenant Separation for the Search Index</span></span>

<span data-ttu-id="57389-114">검색 인덱스는 인덱스 구성 요소를 호스팅하는 서버의 디스크에 저장 되며, 테 넌 트는 인덱스 파일을 공유 합니다.</span><span class="sxs-lookup"><span data-stu-id="57389-114">The search index is stored on disk in the servers hosting the index components and the tenants share the index files.</span></span> <span data-ttu-id="57389-115">테 넌 트의 인덱싱된 문서는 해당 테 넌 트에 대 한 쿼리에만 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="57389-115">A tenant's indexed documents are visible only for queries for that tenant.</span></span> <span data-ttu-id="57389-116">세 가지 독립 메커니즘은 정보 누출을 방지 합니다.</span><span class="sxs-lookup"><span data-stu-id="57389-116">Three independent mechanisms prevent information leakage:</span></span>

- <span data-ttu-id="57389-117">테 넌 트 ID 필터링</span><span class="sxs-lookup"><span data-stu-id="57389-117">Tenant ID filtering</span></span>
- <span data-ttu-id="57389-118">테 넌 트 ID 용어 접두사</span><span class="sxs-lookup"><span data-stu-id="57389-118">Tenant ID term prefixing</span></span>
- <span data-ttu-id="57389-119">ACL 검사</span><span class="sxs-lookup"><span data-stu-id="57389-119">ACL checks</span></span>

<span data-ttu-id="57389-120">검색 시 잘못 된 테 넌 트에 문서를 반환 하려면 세 가지 메커니즘을 모두 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="57389-120">All three mechanisms would have to fail for Search to return documents to the wrong tenant.</span></span>

## <a name="tenant-id-filtering-and-tenant-id-term-prefixing"></a><span data-ttu-id="57389-121">테 넌 트 ID 필터링 및 테 넌 트 ID 용어 접두사</span><span class="sxs-lookup"><span data-stu-id="57389-121">Tenant ID Filtering and Tenant ID Term Prefixing</span></span>

<span data-ttu-id="57389-122">검색 접두사는 전체 텍스트 인덱스에 있는 모든 용어를 테 넌 트 ID로 인덱싱합니다.</span><span class="sxs-lookup"><span data-stu-id="57389-122">Search prefixes every term that is indexed in the full-text index with the tenant ID.</span></span> <span data-ttu-id="57389-123">예를 들어 "*foo*" 라는 용어가 ID가 "*123*" 인 테 넌 트에 대해 인덱싱되는 경우 전체 텍스트 인덱스의 항목은 "*123foo*"가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="57389-123">For example, when the term "*foo*" is indexed for a tenant with an ID of "*123*", the entry in the full-text index is "*123foo.*"</span></span>

<span data-ttu-id="57389-124">모든 쿼리는 테 넌 트 ID 필터링 이라는 프로세스를 사용 하 여 테 넌 트 ID를 포함 하도록 변환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="57389-124">Every query is converted to include the tenant ID using a process called tenant ID filtering.</span></span> <span data-ttu-id="57389-125">예를 들어 쿼리 "*foo*"는 "<*guid*>로 변환 됩니다. *foo* 및 *tenantID*: <*guid*> "로, <*guid*> 쿼리를 수행 하는 테 넌 트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="57389-125">For example, the query "*foo*" is converted to "<*guid*>.*foo* AND *tenantID*:<*guid*>", where <*guid*> represents the tenant performing the query.</span></span> <span data-ttu-id="57389-126">이 쿼리 변환은 각 인덱스 노드 내에서 수행 되며, 쿼리 또는 콘텐츠 처리에서 모두 영향을 주지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="57389-126">This query conversion occurs within each index node and neither query nor content processing can influence it.</span></span> <span data-ttu-id="57389-127">테 넌 트 ID는 모든 쿼리에 추가 되므로 한 테 넌 트의 최상의 일치 순위를 확인 하 여 다른 테 넌 트의 용어 빈도를 유추할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="57389-127">Because the tenant ID is added to every query, the frequency of a term in other tenants can't be inferred by looking at best match ranking in one tenant.</span></span>

<span data-ttu-id="57389-128">테 넌 트 ID 용어 접두사는 전체 텍스트 인덱스에만 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="57389-128">Tenant ID term prefixing occurs only in the full-text index.</span></span> <span data-ttu-id="57389-129">"*Title: foo*"와 같은 Fielded 검색은 용어 앞에 테 넌 트 ID가 붙지 않은 종합 검색 인덱스로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="57389-129">Fielded searches, such as "*title:foo*", go to a synthetic search index where terms aren't prefixed by tenant ID.</span></span> <span data-ttu-id="57389-130">대신 fielded 검색 앞에 필드 이름을 접두사로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="57389-130">Instead, fielded searches are prefixed with the field name.</span></span> <span data-ttu-id="57389-131">예를 들어 "*title: foo*" 쿼리는 "*fields. TITLE: foo 및 fields*: <*guid*>"로 변환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="57389-131">For example, the query "*title:foo*" is converted to "*fields.title:foo AND fields.tenantID*:<*guid*>."</span></span> <span data-ttu-id="57389-132">용어의 빈도는 종합 검색 인덱스의 적중 순위에 영향을 주지 않으므로 용어 접두사를 사용한 테 넌 트를 분리할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="57389-132">Because the frequency of a term doesn't influence ranking of hits in the synthetic search index, there's no need for tenant separation by term prefixing.</span></span> <span data-ttu-id="57389-133">"*Title: foo*"와 같은 fielded 검색의 경우 테 넌 트 콘텐츠 구분은 쿼리 변환 별 테 넌 트 ID 필터링에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="57389-133">For a fielded search like "*title:foo*", tenant content separation depends on tenant ID filtering by query conversion.</span></span>

## <a name="document-access-control-list-checks"></a><span data-ttu-id="57389-134">문서 액세스 제어 목록 검사</span><span class="sxs-lookup"><span data-stu-id="57389-134">Document Access Control List Checks</span></span>

<span data-ttu-id="57389-135">검색에서는 검색 인덱스에 저장 된 Acl을 통해 문서에 대 한 액세스를 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="57389-135">Search controls access to documents through ACLs that are saved in the search index.</span></span> <span data-ttu-id="57389-136">모든 항목은 특별 한 ACL 필드의 용어 집합으로 인덱싱됩니다.</span><span class="sxs-lookup"><span data-stu-id="57389-136">Every item is indexed with a set of terms in a special ACL field.</span></span> <span data-ttu-id="57389-137">ACL 필드에는 문서를 볼 수 있는 그룹 또는 사용자 당 하나의 용어가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57389-137">The ACL field contains one term per group or user that can view the document.</span></span> <span data-ttu-id="57389-138">모든 쿼리는 인증 된 사용자가 속한 각 그룹에 대해 하나씩 ACE (액세스 제어 항목) 용어 목록을 사용 하 여 확장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="57389-138">Every query is augmented with a list of access control entry (ACE) terms, one for each group to which the authenticated user belongs.</span></span>

<span data-ttu-id="57389-139">예를 들어 "<*guid*>와 같은 쿼리를 예로 들 있습니다. *FOO 및 tenantID*: <*guid*> "이 (가) <*guid*>입니다. *foo 및 tenantID*: <*guid* >  *및* (*docacl:* < *ace1* >  *또는 docacl*: <*ace2* >  *또는 docacl*: <*ace3* >  *...*) "</span><span class="sxs-lookup"><span data-stu-id="57389-139">For example, a query like "<*guid*>.*foo AND tenantID*:<*guid*>" becomes: "<*guid*>.*foo AND tenantID*:<*guid*> *AND* (*docACL:*<*ace1*> *OR docACL*:<*ace2*> *OR docACL*:<*ace3*> *...*)"</span></span>

<span data-ttu-id="57389-140">사용자와 그룹 식별자 및 Ace가 고유 하므로 일부 사용자 에게만 표시 되는 문서에 대 한 테 넌 트 간의 추가 보안 수준이 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="57389-140">Because user and group identifiers and hence ACEs are unique, this provides an extra level of security between tenants for documents that are only visible to some users.</span></span> <span data-ttu-id="57389-141">테 넌 트의 일반 사용자에 게 액세스 권한을 부여 하는 특수 "외부 사용자를 제외한 모든 사람" ACE의 경우에도 마찬가지입니다.</span><span class="sxs-lookup"><span data-stu-id="57389-141">The same is the case for the special "Everyone except external users" ACE that grants access to regular users in the tenant.</span></span> <span data-ttu-id="57389-142">그러나 "모든 사용자"에 대 한 Ace는 모든 테 넌 트에서 동일 하므로 공용 문서에 대 한 테 넌 트 분리는 테 넌 트 ID 필터링에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="57389-142">But since ACEs for "Everyone" are the same for all tenants, tenant separation for public documents depends on tenant ID filtering.</span></span> <span data-ttu-id="57389-143">Deny Ace도 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="57389-143">Deny ACEs are also supported.</span></span> <span data-ttu-id="57389-144">쿼리 확대는 deny ACE와 일치 하는 경우 결과에서 문서를 제거 하는 절을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="57389-144">The query augmentation adds a clause that removes a document from the result when there is a match with a deny ACE.</span></span>

<span data-ttu-id="57389-145">Exchange Online 검색에서 SharePoint Online과 같이 테 넌 트 ID (구독 ID)가 아닌 개별 사용자의 사서함에 대 한 사서함 ID로 인덱스가 분할 됩니다.</span><span class="sxs-lookup"><span data-stu-id="57389-145">In Exchange Online search, the index is partitioned on mailbox ID for individual user's mailboxes instead of tenant ID (subscription ID) as in SharePoint Online.</span></span> <span data-ttu-id="57389-146">분할 메커니즘은 SharePoint Online과 동일 하지만 ACL 필터링은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="57389-146">The partitioning mechanism is the same as SharePoint Online, but there is no ACL filtering.</span></span>
