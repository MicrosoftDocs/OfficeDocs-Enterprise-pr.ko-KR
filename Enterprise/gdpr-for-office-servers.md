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
ms.openlocfilehash: dc1150361db6a28f011e4890a2770f4a6b607a91
ms.sourcegitcommit: aabd369fc8b397f9e738374d42d8afd18b96d469
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2018
---
# <a name="gdpr-for-office-on-premises-servers"></a><span data-ttu-id="3a15c-103">Office 온-프레미스 Server GDPR</span><span class="sxs-lookup"><span data-stu-id="3a15c-103">GDPR for Office on-premises Servers</span></span>

<span data-ttu-id="3a15c-p101">GDPR(일반 데이터 보호 규정)은 조직에 요구 사항을 소개하여 개인 데이터를 보호하고 데이터 주체 요청에 적절하게 응답합니다. 이 일련의 문서는 온-프레미스 작업에 권장되는 접근 방식을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3a15c-p101">The General Data Protection Regulation (GDPR) introduces requirements for organizations to protect personal data and respond appropriately to data subject requests. This series of articles provides recommended approaches for on-premises workloads:</span></span>

-   [<span data-ttu-id="3a15c-106">Exchange Server</span><span class="sxs-lookup"><span data-stu-id="3a15c-106">Exchange Server</span></span>](gdpr-for-exchange-server.md)

-   [<span data-ttu-id="3a15c-107">비즈니스용 Skype 서버</span><span class="sxs-lookup"><span data-stu-id="3a15c-107">Skype for Business Server</span></span>](gdpr-for-skype-for-business-server.md)

-   [<span data-ttu-id="3a15c-108">Project Server</span><span class="sxs-lookup"><span data-stu-id="3a15c-108">Project Server</span></span>](gdpr-for-project-server.md)

-   [<span data-ttu-id="3a15c-109">Office Web Apps Server 및 Office Online Server</span><span class="sxs-lookup"><span data-stu-id="3a15c-109">Office Web Apps Server and Office Online Server</span></span>](gdpr-for-office-online-server.md)

-   [<span data-ttu-id="3a15c-110">온-프레미스 파일 공유</span><span class="sxs-lookup"><span data-stu-id="3a15c-110">On-premises file shares</span></span>](gdpr-for-on-premises-file-shares.md)

<span data-ttu-id="3a15c-111">GDPR 및 Microsoft가 지원하는 방법에 대한 자세한 내용은 [Microsoft 보안 센터](https://www.microsoft.com/ko-KR/TrustCenter/Privacy/gdpr/default.aspx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3a15c-111">For more information about the GDPR and how Microsoft can help you, see the [Microsoft Trust Center](https://www.microsoft.com/ko-KR/TrustCenter/Privacy/gdpr/default.aspx).</span></span>

<span data-ttu-id="3a15c-p102">온-프레미스 데이터로 작업을 수행하기 전에 먼저 법률 및 규정 준수 팀에 문의하여 안내를 받고 개인 데이터를 사용하여 작업하는 접근 방식 및 기존 분류 스키마에 대해 알아보세요. 수 및 기존 분류에 대한 자세한 내용은  스키마 및 개인 데이터 작업을 위한 접근 방식을합니다. Microsoft는 [http://aka.ms/gdprpartners](<http://aka.ms/gdprpartners>)에서 Microsoft GDPR 데이터 검색 도구 키트의 분류 스키마를 개발하고 확장하는 권장 사항을 제공합니다. 또한, 이 도구 키트는 원하는 경우 더 정교한 데이터 거버넌스 기능을 사용할 수 있는 클라우드로 온-프레미스 데이터를 이동하는 접근 방식을 설명합니다. 이 섹션에 나와 있는 문서는 온-프레미스로 유지하기 위한 데이터 권장 사항을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3a15c-p102">Before doing any work with on-premises data, consult with your legal and compliance teams to seek guidance and to learn about existing classification schemas and approaches to working with personal data. Microsoft provides recommendations for developing and extending classifications schemas in the Microsoft GDPR Data Discovery Toolkit at [http://aka.ms/gdprpartners](<http://aka.ms/gdprpartners>). This toolkit also describes approaches for moving on-premises data to the cloud where you can use more sophisticated data governance capabilities, if this is desired. The articles in this section provide recommendations for data that is intended to remain on premises.</span></span>

<span data-ttu-id="3a15c-p103">다음 그림은 이러한 각 작업에 사용하여 개인 데이터를 검색, 분류, 보호, 모니터링할 수 있는 권장 기능을 나열합니다. 자세한 내용은 이 섹션의 문서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3a15c-p103">The following illustration lists recommended capabilities to use across each of these workloads to discover, classify, protect, and monitor personal data. See the articles in this section for more information.</span></span>

![](media/gdpr-for-office-servers_image1.png)

## <a name="illustration-description"></a><span data-ttu-id="3a15c-118">그림 설명</span><span class="sxs-lookup"><span data-stu-id="3a15c-118">Illustration description</span></span>

<span data-ttu-id="3a15c-119">다음 표에서는 이해를 돕기 위해 그림과 동일한 예제를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3a15c-119">For accessibility, the following table provides the same examples in the illustration.</span></span>

|             |<span data-ttu-id="3a15c-120">Windows Server 파일 공유</span><span class="sxs-lookup"><span data-stu-id="3a15c-120">Windows Server file shares</span></span>|<span data-ttu-id="3a15c-121">SharePoint Server</span><span class="sxs-lookup"><span data-stu-id="3a15c-121">SharePoint Server</span></span>|<span data-ttu-id="3a15c-122">Exchange Server</span><span class="sxs-lookup"><span data-stu-id="3a15c-122">Exchange Server</span></span>|<span data-ttu-id="3a15c-123">비즈니스용 Skype</span><span class="sxs-lookup"><span data-stu-id="3a15c-123">Skype for Business</span></span>|<span data-ttu-id="3a15c-124">Project Server</span><span class="sxs-lookup"><span data-stu-id="3a15c-124">Project Server</span></span>|
|:------------|:-------------------------|:----------------|:--------------|:-----------------|:-------------|
|<span data-ttu-id="3a15c-125">검색</span><span class="sxs-lookup"><span data-stu-id="3a15c-125">discover
</span></span>|<span data-ttu-id="3a15c-126">Azure Information Protection 스캐너\*</span><span class="sxs-lookup"><span data-stu-id="3a15c-126">Azure Information Protection</span></span>|<span data-ttu-id="3a15c-127">검색 센터 또는 eDiscovery(데이터 분류 후), Azure Information Protection 스캐너\*</span><span class="sxs-lookup"><span data-stu-id="3a15c-127">Search Center or eDiscovery (after data is classified); Azure Information Protection scanner\*</span></span>|<span data-ttu-id="3a15c-128">Exchange eDiscovery 포털</span><span class="sxs-lookup"><span data-stu-id="3a15c-128">Exchange eDiscovery Portal</span></span>|<span data-ttu-id="3a15c-129">Exchange eDiscovery 포털</span><span class="sxs-lookup"><span data-stu-id="3a15c-129">Exchange eDiscovery portal</span></span>|<span data-ttu-id="3a15c-130">검색 및 내보내기용 SQL 스크립트</span><span class="sxs-lookup"><span data-stu-id="3a15c-130">SQL scripts for discovery and exporting</span></span>|
|<span data-ttu-id="3a15c-131">분류</span><span class="sxs-lookup"><span data-stu-id="3a15c-131">Classify</span></span>|<span data-ttu-id="3a15c-132">Azure Information Protection 스캐너\*, Office 365 중요한 정보 유형</span><span class="sxs-lookup"><span data-stu-id="3a15c-132">Azure Information Protection scanner\*; Office 365 sensitive information types</span></span>|<span data-ttu-id="3a15c-133">Azure Information Protection 스캐너\*, Office 365 중요한 정보 유형</span><span class="sxs-lookup"><span data-stu-id="3a15c-133">Azure Information Protection scanner\*; Office 365 sensitive information types</span></span>|<span data-ttu-id="3a15c-134">Exchange 보존 태그 및 보존 정책</span><span class="sxs-lookup"><span data-stu-id="3a15c-134">Exchange retention tags and retention policies</span></span>|<span data-ttu-id="3a15c-135">Exchange 보존 태그 및 보존 정책</span><span class="sxs-lookup"><span data-stu-id="3a15c-135">Exchange retention tags and retention policies</span></span>||
|<span data-ttu-id="3a15c-136">보호</span><span class="sxs-lookup"><span data-stu-id="3a15c-136">protect</span></span>||<span data-ttu-id="3a15c-137">Exchange Server 데이터 손실 방지 규칙, 권한, 라이브러리의 IRM 보호</span><span class="sxs-lookup"><span data-stu-id="3a15c-137">Exchange Server data loss prevention rules; Permissions, IRM-protection for libraries</span></span>|<span data-ttu-id="3a15c-138">Exchange Server 데이터 손실 방지 규칙, Exchange Server와 IRM 통합</span><span class="sxs-lookup"><span data-stu-id="3a15c-138">Exchange Server data loss prevention rules; IRM integration with Exchange Server</span></span>|||
|<span data-ttu-id="3a15c-139">모니터링</span><span class="sxs-lookup"><span data-stu-id="3a15c-139">Monitor</span></span>|<span data-ttu-id="3a15c-140">SIEM 도구와 로그 통합</span><span class="sxs-lookup"><span data-stu-id="3a15c-140">Integrate logs with SIEM tools</span></span>|<span data-ttu-id="3a15c-141">SIEM 도구와 로그 통합</span><span class="sxs-lookup"><span data-stu-id="3a15c-141">Integrate logs with SIEM tools</span></span>|<span data-ttu-id="3a15c-142">SIEM 도구와 로그 통합</span><span class="sxs-lookup"><span data-stu-id="3a15c-142">Integrate logs with SIEM tools</span></span>|<span data-ttu-id="3a15c-143">SIEM 도구와 로그 통합</span><span class="sxs-lookup"><span data-stu-id="3a15c-143">Integrate logs with SIEM tools</span></span>|<span data-ttu-id="3a15c-144">SIEM 도구와 로그 통합</span><span class="sxs-lookup"><span data-stu-id="3a15c-144">Integrate logs with SIEM tools</span></span>|

<span data-ttu-id="3a15c-p104">\*GDPR의 경우 보호가 포함되지 않은 레이블을 적용합니다. 보호는 파일을 암호화합니다. 따라서 SharePoint Server가 이러한 파일에서 중요한 정보 유형을 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3a15c-p104">\*For GDPR, apply labels that do not include protection. Protection encrypts the file. Consequently, SharePoint Server can't find the sensitive information types in these files.</span></span>
