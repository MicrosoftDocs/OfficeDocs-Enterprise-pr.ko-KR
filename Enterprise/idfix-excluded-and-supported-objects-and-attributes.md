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
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
ms.assetid: cc453ae5-fa9b-4836-b0ce-c7e824b1e36d
description: IdFix 도구에서 제외 및 지원 되는 특성을 나열 합니다.
ms.openlocfilehash: e57507688fe1efd21bb629b4fad297129eff55d6
ms.sourcegitcommit: a9804062071939b7b7e60da5b69f484ce1d34ff8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/04/2019
ms.locfileid: "39813928"
---
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a><span data-ttu-id="6c853-103">IdFix 제외 및 지원 개체/특성</span><span class="sxs-lookup"><span data-stu-id="6c853-103">IdFix excluded and supported objects and attributes</span></span>

<span data-ttu-id="6c853-104">*이 문서는 Microsoft 365 Enterprise와 Office 365 Enterprise에 모두 적용됩니다.*</span><span class="sxs-lookup"><span data-stu-id="6c853-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="6c853-105">IdFix에서 유지 관리 되는 두 가지 규칙 집합은 다음과 같습니다. 다중 테 넌 트 및 전용/ITAR</span><span class="sxs-lookup"><span data-stu-id="6c853-105">There are two sets of rules maintained by IdFix; Multi-tenant and Dedicated/ITAR.</span></span> <span data-ttu-id="6c853-106">이때 두 규칙 집합은 동일한 개체, 특성 및 특성 값을 해당 검색에서 제외 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c853-106">At this time, the two rule sets exclude the same objects, attributes, and attribute values from its search.</span></span> <span data-ttu-id="6c853-107">이는 이후 릴리스에서 변경 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c853-107">This may change in future releases.</span></span>
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a><span data-ttu-id="6c853-108">IdFix에서 사용 되는 다중 테 넌 트 및 전용 오류 제외</span><span class="sxs-lookup"><span data-stu-id="6c853-108">Multi-tenant and Dedicated error exclusions used by IdFix</span></span>
<span data-ttu-id="6c853-109">이 섹션에는 IdFix에서 디렉터리 검색에서 제외 되는 개체, 특성 및 값이 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c853-109">This section lists the objects, attributes, and values that IdFix excludes from its search of the directory.</span></span> <span data-ttu-id="6c853-110">별표 (\*)는 다른 문자를 대체할 수 있는 와일드 카드입니다.</span><span class="sxs-lookup"><span data-stu-id="6c853-110">The asterisk (\*) is a wildcard that can be substituted for other characters.</span></span>
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a><span data-ttu-id="6c853-111">IdFix 검색 중에 제외 되는 개체, 특성 및 값</span><span class="sxs-lookup"><span data-stu-id="6c853-111">Objects, attributes, and values excluded during an IdFix search</span></span>

|<span data-ttu-id="6c853-112">**배타적**</span><span class="sxs-lookup"><span data-stu-id="6c853-112">**Exclusion**</span></span>|<span data-ttu-id="6c853-113">**예**</span><span class="sxs-lookup"><span data-stu-id="6c853-113">**Example**</span></span>|
|:-----|:-----|
|<span data-ttu-id="6c853-114">Admini\*</span><span class="sxs-lookup"><span data-stu-id="6c853-114">Admini\*</span></span> |<span data-ttu-id="6c853-115">관리자</span><span class="sxs-lookup"><span data-stu-id="6c853-115">Administrator</span></span> |
|<span data-ttu-id="6c853-116">CAS_ {\*</span><span class="sxs-lookup"><span data-stu-id="6c853-116">CAS_{\*</span></span>  |<span data-ttu-id="6c853-117">CAS_ {fe35fc98e69e4d08}</span><span class="sxs-lookup"><span data-stu-id="6c853-117">CAS_{fe35fc98e69e4d08}</span></span> |
|<span data-ttu-id="6c853-118">DiscoverySearchMailbox\*</span><span class="sxs-lookup"><span data-stu-id="6c853-118">DiscoverySearchMailbox\*</span></span>  |<span data-ttu-id="6c853-119">DiscoverySearchMailbox</span><span class="sxs-lookup"><span data-stu-id="6c853-119">DiscoverySearchMailbox</span></span>  |
|<span data-ttu-id="6c853-120">FederatedEmail\*</span><span class="sxs-lookup"><span data-stu-id="6c853-120">FederatedEmail\*</span></span> |<span data-ttu-id="6c853-121">FederatedEmail.</span><span class="sxs-lookup"><span data-stu-id="6c853-121">FederatedEmail.</span></span> <span data-ttu-id="6c853-122">*GUID*</span><span class="sxs-lookup"><span data-stu-id="6c853-122">*GUID*</span></span> |
|<span data-ttu-id="6c853-123">체제\*</span><span class="sxs-lookup"><span data-stu-id="6c853-123">Guest\*</span></span> ||
|<span data-ttu-id="6c853-124">HTTPConnector\*</span><span class="sxs-lookup"><span data-stu-id="6c853-124">HTTPConnector\*</span></span>  |<span data-ttu-id="6c853-125">HTTPConnector</span><span class="sxs-lookup"><span data-stu-id="6c853-125">HTTPConnector</span></span> |
|<span data-ttu-id="6c853-126">krbtgt\*</span><span class="sxs-lookup"><span data-stu-id="6c853-126">krbtgt\*</span></span> |<span data-ttu-id="6c853-127">ms-DS-KrbTgt-링크</span><span class="sxs-lookup"><span data-stu-id="6c853-127">ms-DS-KrbTgt-Link</span></span> |
|<span data-ttu-id="6c853-128">iusr_\*</span><span class="sxs-lookup"><span data-stu-id="6c853-128">iusr_\*</span></span> |<span data-ttu-id="6c853-129">iusr_ *machinename*</span><span class="sxs-lookup"><span data-stu-id="6c853-129">iusr_ *machinename*</span></span> |
|<span data-ttu-id="6c853-130">iwam\*</span><span class="sxs-lookup"><span data-stu-id="6c853-130">iwam\*</span></span>  |<span data-ttu-id="6c853-131">IWAM_ *machinename*</span><span class="sxs-lookup"><span data-stu-id="6c853-131">IWAM_ *machinename*</span></span> |
|<span data-ttu-id="6c853-132">msol\*</span><span class="sxs-lookup"><span data-stu-id="6c853-132">msol\*</span></span> |<span data-ttu-id="6c853-133">MSOL_AD_SYNC</span><span class="sxs-lookup"><span data-stu-id="6c853-133">MSOL_AD_SYNC</span></span> |
|<span data-ttu-id="6c853-134">support_\*</span><span class="sxs-lookup"><span data-stu-id="6c853-134">support_\*</span></span> ||
|<span data-ttu-id="6c853-135">SystemMailbox\*</span><span class="sxs-lookup"><span data-stu-id="6c853-135">SystemMailbox\*</span></span> |<span data-ttu-id="6c853-136">Systemmailbox { *GUID* }</span><span class="sxs-lookup"><span data-stu-id="6c853-136">Systemmailbox{ *GUID*  }</span></span>|
|<span data-ttu-id="6c853-137">WWIOadmini\*</span><span class="sxs-lookup"><span data-stu-id="6c853-137">WWIOadmini\*</span></span>  ||
|\*$ ||
|<span data-ttu-id="6c853-138">distinguishedName에는 "\0ACNF:"가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c853-138">distinguishedName contains "\0ACNF:"</span></span>|<span data-ttu-id="6c853-139">"\0ACNF: *GUID* "</span><span class="sxs-lookup"><span data-stu-id="6c853-139">"\0ACNF: *GUID*  "</span></span> |
|<span data-ttu-id="6c853-140">IsCriticalSystemObject 특성을 포함 하는 개체</span><span class="sxs-lookup"><span data-stu-id="6c853-140">Object contains the IsCriticalSystemObject attribute</span></span> |<span data-ttu-id="6c853-141">[특성 isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6c853-141">See [Attribute isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169).</span></span> |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a><span data-ttu-id="6c853-142">IdFix에서 확인 하는 다중 테 넌 트 및 전용 개체 및 특성</span><span class="sxs-lookup"><span data-stu-id="6c853-142">Multi-Tenant and Dedicated objects and attributes checked by IdFix</span></span>
<span data-ttu-id="6c853-143">IdFix에서 오류를 확인 하는 특성은 [idfix 도구를 사용 하 여 Office 365 동기화를 위한 디렉터리 특성 준비](prepare-directory-attributes-for-synch-with-idfix.md)의 "디렉터리 개체 및 특성 준비" 섹션에 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c853-143">The attributes that are checked for errors by IdFix are described in the section "Directory object and attribute preparation" in [Prepare directory attributes for synchronization with Office 365 by using the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md).</span></span>
  

