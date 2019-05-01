---
title: IdFix 제외 및 지원 개체/특성
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2016
ms.audience: Admin
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
description: idfix 도구에서 제외 및 지원 되는 특성을 나열 합니다.
ms.openlocfilehash: d6b7aac023e9fe96b8308483322e718937ab1355
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487184"
---
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a><span data-ttu-id="a1d20-103">IdFix 제외 및 지원 개체/특성</span><span class="sxs-lookup"><span data-stu-id="a1d20-103">IdFix excluded and supported objects and attributes</span></span>
<span data-ttu-id="a1d20-104">idfix에서 유지 관리 되는 두 가지 규칙 집합은 다음과 같습니다. 다중 테 넌 트 및 전용/itar</span><span class="sxs-lookup"><span data-stu-id="a1d20-104">There are two sets of rules maintained by IdFix; Multi-tenant and Dedicated/ITAR.</span></span> <span data-ttu-id="a1d20-105">이때 두 규칙 집합은 동일한 개체, 특성 및 특성 값을 해당 검색에서 제외 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1d20-105">At this time, the two rule sets exclude the same objects, attributes, and attribute values from its search.</span></span> <span data-ttu-id="a1d20-106">이는 이후 릴리스에서 변경 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1d20-106">This may change in future releases.</span></span>
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a><span data-ttu-id="a1d20-107">idfix에서 사용 되는 다중 테 넌 트 및 전용 오류 제외</span><span class="sxs-lookup"><span data-stu-id="a1d20-107">Multi-tenant and Dedicated error exclusions used by IdFix</span></span>
<span data-ttu-id="a1d20-108">이 섹션에는 idfix에서 디렉터리 검색에서 제외 되는 개체, 특성 및 값이 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1d20-108">This section lists the objects, attributes, and values that IdFix excludes from its search of the directory.</span></span> <span data-ttu-id="a1d20-109">별표 (\*)는 다른 문자를 대체할 수 있는 와일드 카드입니다.</span><span class="sxs-lookup"><span data-stu-id="a1d20-109">The asterisk (\*) is a wildcard that can be substituted for other characters.</span></span>
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a><span data-ttu-id="a1d20-110">idfix 검색 중에 제외 되는 개체, 특성 및 값</span><span class="sxs-lookup"><span data-stu-id="a1d20-110">Objects, attributes, and values excluded during an IdFix search</span></span>

|<span data-ttu-id="a1d20-111">**배타적**</span><span class="sxs-lookup"><span data-stu-id="a1d20-111">**Exclusion**</span></span>|<span data-ttu-id="a1d20-112">**예제**</span><span class="sxs-lookup"><span data-stu-id="a1d20-112">**Example**</span></span>|
|:-----|:-----|
|<span data-ttu-id="a1d20-113">Admini\*</span><span class="sxs-lookup"><span data-stu-id="a1d20-113">Admini\*</span></span> |<span data-ttu-id="a1d20-114">관리자</span><span class="sxs-lookup"><span data-stu-id="a1d20-114">Administrator</span></span> |
|<span data-ttu-id="a1d20-115">CAS_ {\*</span><span class="sxs-lookup"><span data-stu-id="a1d20-115">CAS_{\*</span></span>  |<span data-ttu-id="a1d20-116">CAS_ {fe35fc98e69e4d08}</span><span class="sxs-lookup"><span data-stu-id="a1d20-116">CAS_{fe35fc98e69e4d08}</span></span> |
|<span data-ttu-id="a1d20-117">discoverysearchmailbox\*</span><span class="sxs-lookup"><span data-stu-id="a1d20-117">DiscoverySearchMailbox\*</span></span>  |<span data-ttu-id="a1d20-118">discoverysearchmailbox</span><span class="sxs-lookup"><span data-stu-id="a1d20-118">DiscoverySearchMailbox</span></span>  |
|<span data-ttu-id="a1d20-119">FederatedEmail\*</span><span class="sxs-lookup"><span data-stu-id="a1d20-119">FederatedEmail\*</span></span> |<span data-ttu-id="a1d20-120">FederatedEmail</span><span class="sxs-lookup"><span data-stu-id="a1d20-120">FederatedEmail.</span></span> <span data-ttu-id="a1d20-121">*GUID*</span><span class="sxs-lookup"><span data-stu-id="a1d20-121">*GUID*</span></span> |
|<span data-ttu-id="a1d20-122">체제\*</span><span class="sxs-lookup"><span data-stu-id="a1d20-122">Guest\*</span></span> ||
|<span data-ttu-id="a1d20-123">httpconnector\*</span><span class="sxs-lookup"><span data-stu-id="a1d20-123">HTTPConnector\*</span></span>  |<span data-ttu-id="a1d20-124">httpconnector</span><span class="sxs-lookup"><span data-stu-id="a1d20-124">HTTPConnector</span></span> |
|<span data-ttu-id="a1d20-125">krbtgt\*</span><span class="sxs-lookup"><span data-stu-id="a1d20-125">krbtgt\*</span></span> |<span data-ttu-id="a1d20-126">ms-DS-KrbTgt-링크</span><span class="sxs-lookup"><span data-stu-id="a1d20-126">ms-DS-KrbTgt-Link</span></span> |
|<span data-ttu-id="a1d20-127">iusr\*</span><span class="sxs-lookup"><span data-stu-id="a1d20-127">iusr_\*</span></span> |<span data-ttu-id="a1d20-128">iusr_ *machinename*</span><span class="sxs-lookup"><span data-stu-id="a1d20-128">iusr_ *machinename*</span></span> |
|<span data-ttu-id="a1d20-129">iwam\*</span><span class="sxs-lookup"><span data-stu-id="a1d20-129">iwam\*</span></span>  |<span data-ttu-id="a1d20-130">IWAM_ *machinename*</span><span class="sxs-lookup"><span data-stu-id="a1d20-130">IWAM_ *machinename*</span></span> |
|<span data-ttu-id="a1d20-131">msol\*</span><span class="sxs-lookup"><span data-stu-id="a1d20-131">msol\*</span></span> |<span data-ttu-id="a1d20-132">MSOL_AD_SYNC</span><span class="sxs-lookup"><span data-stu-id="a1d20-132">MSOL_AD_SYNC</span></span> |
|<span data-ttu-id="a1d20-133">지원\*</span><span class="sxs-lookup"><span data-stu-id="a1d20-133">support_\*</span></span> ||
|<span data-ttu-id="a1d20-134">SystemMailbox\*</span><span class="sxs-lookup"><span data-stu-id="a1d20-134">SystemMailbox\*</span></span> |<span data-ttu-id="a1d20-135">systemmailbox { *GUID* }</span><span class="sxs-lookup"><span data-stu-id="a1d20-135">Systemmailbox{ *GUID*  }</span></span>|
|<span data-ttu-id="a1d20-136">wwioadmini\*</span><span class="sxs-lookup"><span data-stu-id="a1d20-136">WWIOadmini\*</span></span>  ||
|\*$ ||
|<span data-ttu-id="a1d20-137">distinguishedName에는 "\0ACNF:"가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1d20-137">distinguishedName contains "\0ACNF:"</span></span>|<span data-ttu-id="a1d20-138">"\0ACNF: *GUID* "</span><span class="sxs-lookup"><span data-stu-id="a1d20-138">"\0ACNF: *GUID*  "</span></span> |
|<span data-ttu-id="a1d20-139">IsCriticalSystemObject 특성을 포함 하는 개체</span><span class="sxs-lookup"><span data-stu-id="a1d20-139">Object contains the IsCriticalSystemObject attribute</span></span> |<span data-ttu-id="a1d20-140">[특성 isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a1d20-140">See [Attribute isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169).</span></span> |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a><span data-ttu-id="a1d20-141">idfix에서 확인 하는 다중 테 넌 트 및 전용 개체 및 특성</span><span class="sxs-lookup"><span data-stu-id="a1d20-141">Multi-Tenant and Dedicated objects and attributes checked by IdFix</span></span>
<span data-ttu-id="a1d20-142">idfix에서 오류를 확인 하는 특성은 [idfix 도구를 사용 하 여 Office 365 동기화를 위한 디렉터리 특성 준비](prepare-directory-attributes-for-synch-with-idfix.md)의 "디렉터리 개체 및 특성 준비" 섹션에 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1d20-142">The attributes that are checked for errors by IdFix are described in the section "Directory object and attribute preparation" in [Prepare directory attributes for synchronization with Office 365 by using the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md).</span></span>
  

