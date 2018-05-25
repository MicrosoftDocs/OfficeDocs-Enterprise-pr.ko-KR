---
title: Office Server GDPR
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
description: Office 온-프레미스 Server에서 GDPR 요구 사항을 해결하는 방법을 알아보세요.
ms.openlocfilehash: 598d4b0c3f4b7d4281383111f0891759f81d483f
ms.sourcegitcommit: 53a57b0617b5bb22beea766e515873d14b3a4783
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2018
---
# <a name="gdpr-for-office-on-premises-servers"></a><span data-ttu-id="e8a81-103">Office 온-프레미스 Server GDPR</span><span class="sxs-lookup"><span data-stu-id="e8a81-103">GDPR for Office on-premises Servers</span></span>

<span data-ttu-id="e8a81-p101">GDPR(일반 데이터 보호 규정)은 조직에 요구 사항을 소개하여 개인 데이터를 보호하고 데이터 주체 요청에 적절하게 응답합니다. 이 일련의 문서는 온-프레미스 작업에 권장되는 접근 방식을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e8a81-p101">The General Data Protection Regulation (GDPR) introduces requirements for organizations to protect personal data and respond appropriately to data subject requests. This series of articles provides recommended approaches for on-premises workloads:</span></span>

-   [<span data-ttu-id="e8a81-106">SharePoint Server</span><span class="sxs-lookup"><span data-stu-id="e8a81-106">SharePoint Server</span></span>](gdpr-for-sharepoint-server.md)

-   [<span data-ttu-id="e8a81-107">Exchange Server</span><span class="sxs-lookup"><span data-stu-id="e8a81-107">Exchange Server</span></span>](gdpr-for-exchange-server.md)

-   [<span data-ttu-id="e8a81-108">비즈니스용 Skype 서버</span><span class="sxs-lookup"><span data-stu-id="e8a81-108">Skype for Business Server</span></span>](gdpr-for-skype-for-business-server.md)

-   [<span data-ttu-id="e8a81-109">Project Server</span><span class="sxs-lookup"><span data-stu-id="e8a81-109">Project Server</span></span>](gdpr-for-project-server.md)

-   [<span data-ttu-id="e8a81-110">Office Web Apps Server 및 Office Online Server</span><span class="sxs-lookup"><span data-stu-id="e8a81-110">Office Web Apps Server and Office Online Server</span></span>](gdpr-for-office-online-server.md)

-   [<span data-ttu-id="e8a81-111">온-프레미스 파일 공유</span><span class="sxs-lookup"><span data-stu-id="e8a81-111">On-premises file shares</span></span>](gdpr-for-on-premises-file-shares.md)

<span data-ttu-id="e8a81-112">GDPR 및 Microsoft가 지원하는 방법에 대한 자세한 내용은 [Microsoft 보안 센터](https://www.microsoft.com/ko-KR/TrustCenter/Privacy/gdpr/default.aspx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e8a81-112">For more information about the GDPR and how Microsoft can help you, see the [Microsoft Trust Center](https://www.microsoft.com/ko-KR/TrustCenter/Privacy/gdpr/default.aspx).</span></span>

<span data-ttu-id="e8a81-p102">온-프레미스 데이터로 작업을 수행하기 전에 먼저 법률 및 규정 준수 팀에 문의하여 안내를 받고 개인 데이터를 사용하여 작업하는 접근 방식 및 기존 분류 스키마에 대해 알아보세요. 수 및 기존 분류에 대한 자세한 내용은  스키마 및 개인 데이터 작업을 위한 접근 방식을합니다. Microsoft는 [http://aka.ms/gdprpartners](<http://aka.ms/gdprpartners>)에서 Microsoft GDPR 데이터 검색 도구 키트의 분류 스키마를 개발하고 확장하는 권장 사항을 제공합니다. 또한, 이 도구 키트는 원하는 경우 더 정교한 데이터 거버넌스 기능을 사용할 수 있는 클라우드로 온-프레미스 데이터를 이동하는 접근 방식을 설명합니다. 이 섹션에 나와 있는 문서는 온-프레미스로 유지하기 위한 데이터 권장 사항을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e8a81-p102">Before doing any work with on-premises data, consult with your legal and compliance teams to seek guidance and to learn about existing classification schemas and approaches to working with personal data. Microsoft provides recommendations for developing and extending classifications schemas in the Microsoft GDPR Data Discovery Toolkit at [http://aka.ms/gdprpartners](<http://aka.ms/gdprpartners>). This toolkit also describes approaches for moving on-premises data to the cloud where you can use more sophisticated data governance capabilities, if this is desired. The articles in this section provide recommendations for data that is intended to remain on premises.</span></span>

<span data-ttu-id="e8a81-p103">다음 그림은 이러한 각 작업에 사용하여 개인 데이터를 검색, 분류, 보호, 모니터링할 수 있는 권장 기능을 나열합니다. 자세한 내용은 이 섹션의 문서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e8a81-p103">The following illustration lists recommended capabilities to use across each of these workloads to discover, classify, protect, and monitor personal data. See the articles in this section for more information.</span></span>

![](media/gdpr-for-office-servers_image1.png)

## <a name="illustration-description"></a><span data-ttu-id="e8a81-119">그림 설명</span><span class="sxs-lookup"><span data-stu-id="e8a81-119">Illustration description</span></span>

<span data-ttu-id="e8a81-120">다음 표에서는 이해를 돕기 위해 그림과 동일한 예제를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e8a81-120">For accessibility, the following table provides the same examples in the illustration.</span></span>

|             |<span data-ttu-id="e8a81-121">Windows Server 파일 공유</span><span class="sxs-lookup"><span data-stu-id="e8a81-121">Windows Server file shares</span></span>|<span data-ttu-id="e8a81-122">SharePoint Server</span><span class="sxs-lookup"><span data-stu-id="e8a81-122">SharePoint Server</span></span>|<span data-ttu-id="e8a81-123">Exchange Server</span><span class="sxs-lookup"><span data-stu-id="e8a81-123">Exchange Server</span></span>|<span data-ttu-id="e8a81-124">비즈니스용 Skype</span><span class="sxs-lookup"><span data-stu-id="e8a81-124">Skype for Business</span></span>|<span data-ttu-id="e8a81-125">Project Server</span><span class="sxs-lookup"><span data-stu-id="e8a81-125">Project Server</span></span>|
|:------------|:-------------------------|:----------------|:--------------|:-----------------|:-------------|
|<span data-ttu-id="e8a81-126">검색</span><span class="sxs-lookup"><span data-stu-id="e8a81-126">discover
</span></span>|<span data-ttu-id="e8a81-127">Azure Information Protection 스캐너\*</span><span class="sxs-lookup"><span data-stu-id="e8a81-127">Azure Information Protection</span></span>|<span data-ttu-id="e8a81-128">검색 센터 또는 eDiscovery(데이터 분류 후), Azure Information Protection 스캐너\*</span><span class="sxs-lookup"><span data-stu-id="e8a81-128">Search Center or eDiscovery (after data is classified); Azure Information Protection scanner\*</span></span>|<span data-ttu-id="e8a81-129">Exchange eDiscovery 포털</span><span class="sxs-lookup"><span data-stu-id="e8a81-129">Exchange eDiscovery Portal</span></span>|<span data-ttu-id="e8a81-130">Exchange eDiscovery 포털</span><span class="sxs-lookup"><span data-stu-id="e8a81-130">Exchange eDiscovery portal</span></span>|<span data-ttu-id="e8a81-131">검색 및 내보내기용 SQL 스크립트</span><span class="sxs-lookup"><span data-stu-id="e8a81-131">SQL scripts for discovery and exporting</span></span>|
|<span data-ttu-id="e8a81-132">분류</span><span class="sxs-lookup"><span data-stu-id="e8a81-132">Classify</span></span>|<span data-ttu-id="e8a81-133">Azure Information Protection 스캐너\*, Office 365 중요한 정보 유형</span><span class="sxs-lookup"><span data-stu-id="e8a81-133">Azure Information Protection scanner\*; Office 365 sensitive information types</span></span>|<span data-ttu-id="e8a81-134">Azure Information Protection 스캐너\*, Office 365 중요한 정보 유형</span><span class="sxs-lookup"><span data-stu-id="e8a81-134">Azure Information Protection scanner\*; Office 365 sensitive information types</span></span>|<span data-ttu-id="e8a81-135">Exchange 보존 태그 및 보존 정책</span><span class="sxs-lookup"><span data-stu-id="e8a81-135">Exchange retention tags and retention policies</span></span>|<span data-ttu-id="e8a81-136">Exchange 보존 태그 및 보존 정책</span><span class="sxs-lookup"><span data-stu-id="e8a81-136">Exchange retention tags and retention policies</span></span>||
|<span data-ttu-id="e8a81-137">보호</span><span class="sxs-lookup"><span data-stu-id="e8a81-137">protect</span></span>||<span data-ttu-id="e8a81-138">Exchange Server 데이터 손실 방지 규칙, 권한, 라이브러리의 IRM 보호</span><span class="sxs-lookup"><span data-stu-id="e8a81-138">Exchange Server data loss prevention rules; Permissions, IRM-protection for libraries</span></span>|<span data-ttu-id="e8a81-139">Exchange Server 데이터 손실 방지 규칙, Exchange Server와 IRM 통합</span><span class="sxs-lookup"><span data-stu-id="e8a81-139">Exchange Server data loss prevention rules; IRM integration with Exchange Server</span></span>|||
|<span data-ttu-id="e8a81-140">모니터링</span><span class="sxs-lookup"><span data-stu-id="e8a81-140">Monitor</span></span>|<span data-ttu-id="e8a81-141">SIEM 도구와 로그 통합</span><span class="sxs-lookup"><span data-stu-id="e8a81-141">Integrate logs with SIEM tools</span></span>|<span data-ttu-id="e8a81-142">SIEM 도구와 로그 통합</span><span class="sxs-lookup"><span data-stu-id="e8a81-142">Integrate logs with SIEM tools</span></span>|<span data-ttu-id="e8a81-143">SIEM 도구와 로그 통합</span><span class="sxs-lookup"><span data-stu-id="e8a81-143">Integrate logs with SIEM tools</span></span>|<span data-ttu-id="e8a81-144">SIEM 도구와 로그 통합</span><span class="sxs-lookup"><span data-stu-id="e8a81-144">Integrate logs with SIEM tools</span></span>|<span data-ttu-id="e8a81-145">SIEM 도구와 로그 통합</span><span class="sxs-lookup"><span data-stu-id="e8a81-145">Integrate logs with SIEM tools</span></span>|

<span data-ttu-id="e8a81-p104">\*보호는 파일을 암호화합니다. 따라서 SharePoint Server가 보호된 파일에서 중요한 정보 유형을 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e8a81-p104">\*Note that protection encrypts the file. Consequently, SharePoint Server can’t find the sensitive information types in protected files.</span></span>
