---
title: IdFix 제외 및 지원 개체/특성
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
- MOE150
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
ms.assetid: cc453ae5-fa9b-4836-b0ce-c7e824b1e36d
description: IdFix 도구에서 제외 및 지원 되는 특성을 나열 합니다.
ms.openlocfilehash: 0203f47864dc4222cd2f95a4e67b2f10bec44f71
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41840145"
---
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a><span data-ttu-id="7afe7-103">IdFix 제외 및 지원 개체/특성</span><span class="sxs-lookup"><span data-stu-id="7afe7-103">IdFix excluded and supported objects and attributes</span></span>

<span data-ttu-id="7afe7-104">*이 문서는 Microsoft 365 Enterprise와 Office 365 Enterprise에 모두 적용됩니다.*</span><span class="sxs-lookup"><span data-stu-id="7afe7-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="7afe7-105">IdFix에서 유지 관리 되는 두 가지 규칙 집합은 다음과 같습니다. 다중 테 넌 트 및 전용/ITAR</span><span class="sxs-lookup"><span data-stu-id="7afe7-105">There are two sets of rules maintained by IdFix; Multi-tenant and Dedicated/ITAR.</span></span> <span data-ttu-id="7afe7-106">이때 두 규칙 집합은 동일한 개체, 특성 및 특성 값을 해당 검색에서 제외 합니다.</span><span class="sxs-lookup"><span data-stu-id="7afe7-106">At this time, the two rule sets exclude the same objects, attributes, and attribute values from its search.</span></span> <span data-ttu-id="7afe7-107">이는 이후 릴리스에서 변경 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7afe7-107">This may change in future releases.</span></span>
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a><span data-ttu-id="7afe7-108">IdFix에서 사용 되는 다중 테 넌 트 및 전용 오류 제외</span><span class="sxs-lookup"><span data-stu-id="7afe7-108">Multi-tenant and Dedicated error exclusions used by IdFix</span></span>
<span data-ttu-id="7afe7-109">이 섹션에는 IdFix에서 디렉터리 검색에서 제외 되는 개체, 특성 및 값이 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7afe7-109">This section lists the objects, attributes, and values that IdFix excludes from its search of the directory.</span></span> <span data-ttu-id="7afe7-110">별표 (\*)는 다른 문자를 대체할 수 있는 와일드 카드입니다.</span><span class="sxs-lookup"><span data-stu-id="7afe7-110">The asterisk (\*) is a wildcard that can be substituted for other characters.</span></span>
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a><span data-ttu-id="7afe7-111">IdFix 검색 중에 제외 되는 개체, 특성 및 값</span><span class="sxs-lookup"><span data-stu-id="7afe7-111">Objects, attributes, and values excluded during an IdFix search</span></span>

|<span data-ttu-id="7afe7-112">**배타적**</span><span class="sxs-lookup"><span data-stu-id="7afe7-112">**Exclusion**</span></span>|<span data-ttu-id="7afe7-113">**예**</span><span class="sxs-lookup"><span data-stu-id="7afe7-113">**Example**</span></span>|
|:-----|:-----|
|<span data-ttu-id="7afe7-114">Admini\*</span><span class="sxs-lookup"><span data-stu-id="7afe7-114">Admini\*</span></span> |<span data-ttu-id="7afe7-115">관리자</span><span class="sxs-lookup"><span data-stu-id="7afe7-115">Administrator</span></span> |
|<span data-ttu-id="7afe7-116">CAS_ {\*</span><span class="sxs-lookup"><span data-stu-id="7afe7-116">CAS_{\*</span></span>  |<span data-ttu-id="7afe7-117">CAS_ {fe35fc98e69e4d08}</span><span class="sxs-lookup"><span data-stu-id="7afe7-117">CAS_{fe35fc98e69e4d08}</span></span> |
|<span data-ttu-id="7afe7-118">DiscoverySearchMailbox\*</span><span class="sxs-lookup"><span data-stu-id="7afe7-118">DiscoverySearchMailbox\*</span></span>  |<span data-ttu-id="7afe7-119">DiscoverySearchMailbox</span><span class="sxs-lookup"><span data-stu-id="7afe7-119">DiscoverySearchMailbox</span></span>  |
|<span data-ttu-id="7afe7-120">FederatedEmail\*</span><span class="sxs-lookup"><span data-stu-id="7afe7-120">FederatedEmail\*</span></span> |<span data-ttu-id="7afe7-121">FederatedEmail.</span><span class="sxs-lookup"><span data-stu-id="7afe7-121">FederatedEmail.</span></span> <span data-ttu-id="7afe7-122">*GUID*</span><span class="sxs-lookup"><span data-stu-id="7afe7-122">*GUID*</span></span> |
|<span data-ttu-id="7afe7-123">체제\*</span><span class="sxs-lookup"><span data-stu-id="7afe7-123">Guest\*</span></span> ||
|<span data-ttu-id="7afe7-124">HTTPConnector\*</span><span class="sxs-lookup"><span data-stu-id="7afe7-124">HTTPConnector\*</span></span>  |<span data-ttu-id="7afe7-125">HTTPConnector</span><span class="sxs-lookup"><span data-stu-id="7afe7-125">HTTPConnector</span></span> |
|<span data-ttu-id="7afe7-126">krbtgt\*</span><span class="sxs-lookup"><span data-stu-id="7afe7-126">krbtgt\*</span></span> |<span data-ttu-id="7afe7-127">ms-DS-KrbTgt-링크</span><span class="sxs-lookup"><span data-stu-id="7afe7-127">ms-DS-KrbTgt-Link</span></span> |
|<span data-ttu-id="7afe7-128">iusr_\*</span><span class="sxs-lookup"><span data-stu-id="7afe7-128">iusr_\*</span></span> |<span data-ttu-id="7afe7-129">iusr_ *machinename*</span><span class="sxs-lookup"><span data-stu-id="7afe7-129">iusr_ *machinename*</span></span> |
|<span data-ttu-id="7afe7-130">iwam\*</span><span class="sxs-lookup"><span data-stu-id="7afe7-130">iwam\*</span></span>  |<span data-ttu-id="7afe7-131">IWAM_ *machinename*</span><span class="sxs-lookup"><span data-stu-id="7afe7-131">IWAM_ *machinename*</span></span> |
|<span data-ttu-id="7afe7-132">msol\*</span><span class="sxs-lookup"><span data-stu-id="7afe7-132">msol\*</span></span> |<span data-ttu-id="7afe7-133">MSOL_AD_SYNC</span><span class="sxs-lookup"><span data-stu-id="7afe7-133">MSOL_AD_SYNC</span></span> |
|<span data-ttu-id="7afe7-134">support_\*</span><span class="sxs-lookup"><span data-stu-id="7afe7-134">support_\*</span></span> ||
|<span data-ttu-id="7afe7-135">SystemMailbox\*</span><span class="sxs-lookup"><span data-stu-id="7afe7-135">SystemMailbox\*</span></span> |<span data-ttu-id="7afe7-136">Systemmailbox { *GUID* }</span><span class="sxs-lookup"><span data-stu-id="7afe7-136">Systemmailbox{ *GUID*  }</span></span>|
|<span data-ttu-id="7afe7-137">WWIOadmini\*</span><span class="sxs-lookup"><span data-stu-id="7afe7-137">WWIOadmini\*</span></span>  ||
|\*$ ||
|<span data-ttu-id="7afe7-138">distinguishedName에는 "\0ACNF:"가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7afe7-138">distinguishedName contains "\0ACNF:"</span></span>|<span data-ttu-id="7afe7-139">"\0ACNF: *GUID* "</span><span class="sxs-lookup"><span data-stu-id="7afe7-139">"\0ACNF: *GUID*  "</span></span> |
|<span data-ttu-id="7afe7-140">IsCriticalSystemObject 특성을 포함 하는 개체</span><span class="sxs-lookup"><span data-stu-id="7afe7-140">Object contains the IsCriticalSystemObject attribute</span></span> |<span data-ttu-id="7afe7-141">[특성 isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7afe7-141">See [Attribute isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169).</span></span> |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a><span data-ttu-id="7afe7-142">IdFix에서 확인 하는 다중 테 넌 트 및 전용 개체 및 특성</span><span class="sxs-lookup"><span data-stu-id="7afe7-142">Multi-Tenant and Dedicated objects and attributes checked by IdFix</span></span>
<span data-ttu-id="7afe7-143">IdFix에서 오류를 확인 하는 특성은 [idfix 도구를 사용 하 여 Office 365 동기화를 위한 디렉터리 특성 준비](prepare-directory-attributes-for-synch-with-idfix.md)의 "디렉터리 개체 및 특성 준비" 섹션에 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7afe7-143">The attributes that are checked for errors by IdFix are described in the section "Directory object and attribute preparation" in [Prepare directory attributes for synchronization with Office 365 by using the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md).</span></span>
  

