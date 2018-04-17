---
title: GDPR에 대한 Office 365 정보 보호 개요
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
description: GDPR에 대한 Office 365 정보 보호 개요를 확인합니다. 개인 데이터를 검색, 분류, 보호 및 모니터링하는 방법을 알아봅니다.
ms.openlocfilehash: 0b5021fbe90c894e72f252494c07c5a4e3dbdad8
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
---
# <a name="overview-of-office-365-information-protection-for-gdpr"></a><span data-ttu-id="71c1f-104">GDPR에 대한 Office 365 정보 보호 개요</span><span class="sxs-lookup"><span data-stu-id="71c1f-104">Overview of Office 365 Information Protection for GDPR</span></span>

<span data-ttu-id="71c1f-p102">이 솔루션은 Office 365 서비스에 저장되어 있는 중요한 데이터를 보호하는 방법을 설명하며 개인 데이터를 검색, 분류, 보호 및 모니터링하기 위한 규정된 권장 사항을 포함합니다. 이 솔루션에서는 GDPR(일반 데이터 보호 규정)을 예제로 사용하지만, 동일한 프로세스를 적용하여 여러 다른 규정을 준수할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71c1f-p102">This solution demonstrates how to protect sensitive data that is stored in Office 365 services. It includes prescriptive recommendations for discovering, classifying, protecting, and monitoring personal data. This solution uses General Data Protection Regulation (GDPR) as an example, but you can apply the same process to achieve compliance with many other regulations.</span></span>

<span data-ttu-id="71c1f-p103">GDPR은 개인 데이터의 수집, 저장, 처리 및 공유를 규제합니다. 개인 데이터는 EU(유럽 연합)에 거주하는 식별되었거나 식별 가능한 자연인과 관련된 데이터로서 GDPR에서 매우 광범위하게 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="71c1f-p103">GDPR regulates the collection, storage, processing, and sharing of personal data. Personal data is defined very broadly under the GDPR as any data that relates to an identified or identifiable natural person that is a resident of the European Union (EU).</span></span>

<span data-ttu-id="71c1f-110">문서 4 - 정의</span><span class="sxs-lookup"><span data-stu-id="71c1f-110">Article 4 – Definitions</span></span>

> <span data-ttu-id="71c1f-111">'개인 데이터'는 식별되었거나 식별 가능한 자연인(‘데이터 주체’)과 관련된 정보를 의미합니다. 식별 가능한 자연인은 직간접적으로, 특히 이름, 식별 번호, 위치 데이터, 온라인 식별자 또는 해당 자연인의 신체적, 생리적, 유전적, 정신적, 경제적, 문화적 또는 사회적 ID와 같은 식별자를 참조하여 식별될 수 있는 사람입니다.</span><span class="sxs-lookup"><span data-stu-id="71c1f-111">‘personal data’ means any information relating to an identified or identifiable natural person (‘data subject’); an identifiable natural person is one who can be identified, directly or indirectly, in particular by reference to an identifier such as a name, an identification number, location data, an online identifier or to one or more factors specific to the physical, physiological, genetic, mental, economic, cultural or social identity of that natural person;</span></span>

<span data-ttu-id="71c1f-p104">이 솔루션은 조직에서 GDPR이 적용될 수 있는 Office 365dml 개인 데이터를 검색하고 보호하는 데 도움을 주기 위해 작성되었습니다. 이 솔루션은 GDPR 규정 준수에 대한 증거로 제공되지 않습니다. 조직에서는 자체 GDPR 규정 준수를 보장하고, 법률 및 규정 준수 팀의 자문을 구하거나 규정 준수에 특하된 제3자의 자문을 구하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="71c1f-p104">This solution is intended to help organizations discover and protect personal data in Office 365 that might be subject to the GDPR. It is not offered as a GDPR compliance attestation. Organizations are responsible for ensuring their own GDPR compliance and are advised to consult their legal and compliance teams or to seek guidance and advice from third parties that specialize in compliance.</span></span>

<span data-ttu-id="71c1f-115">[GDPR 평가](https://www.gdprbenchmark.com)는 조직이 전반적인 준비 수준이 GDPR에 부합되는지 검토하는 데 도움을 주기 위해 무료로 사용할 수 있는 빠른 온라인 자체 평가 도구입니다(<http://aka.ms/gdprassessment>).</span><span class="sxs-lookup"><span data-stu-id="71c1f-115">[GDPR Assessment](https://www.gdprbenchmark.com) is a quick, online self-evaluation tool available at no cost to help your organization review its overall level of readiness to comply with the GDPR (<http://aka.ms/gdprassessment>).</span></span>

## <a name="assess-and-manage-your-compliance-risk"></a><span data-ttu-id="71c1f-116">규정 준수 위험 평가 및 관리</span><span class="sxs-lookup"><span data-stu-id="71c1f-116">Assess and manage your compliance risk</span></span>

<span data-ttu-id="71c1f-p105">GDPR 규정을 준수하는 첫 번째 단계는 GDPR이 조직에 적용되는지, 적용된다면 적용 수준은 어떤지 평가하는 것입니다. 이러한 분석에는 조직이 처리하는 데이터와 데이터의 위치를 이해하는 작업이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="71c1f-p105">The first step towards GDPR compliance is to assess whether the GDPR applies to your organization, and, if so, to what extent. This analysis includes understanding the data your organization processes and where it resides.</span></span>

### <a name="step-1--use-compliance-manager-to-view-the-regulation-requirements-and-track-your-progress"></a><span data-ttu-id="71c1f-119">1단계 - 규정 준수 관리자를 사용하여 규정 요구 사항을 확인하고 진행 상황 추적</span><span class="sxs-lookup"><span data-stu-id="71c1f-119">Step 1 — Use Compliance Manager to view the regulation requirements and track your progress</span></span>

<span data-ttu-id="71c1f-120">규정 준수 관리자는 조직이 GDPR을 비롯한 다양한 표준 규정을 준수하도록 하기 위해 감사 컨트롤을 추적, 구현 및 관리하기 위한 도구를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="71c1f-120">Compliance Manager provides tools to track, implement, and manage the auditing controls to help your organization reach compliance against various standards, including GDPR.</span></span>

![규정 준수 관리자를 사용하여 요구 사항 확인 및 진행 상황 추적](Media/Overview-image1.png)

<span data-ttu-id="71c1f-122">자세한 내용은 [서비스 보안 포털에서 규정 준수 관리자 사용](https://support.office.com/ko-KR/article/Use-Compliance-Manager-in-the-Service-Trust-Portal-Preview-5756d342-5af9-4496-82e8-4dd50fa39942)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="71c1f-122">For more information, see [Use Compliance Manager in the Service Trust Portal](https://support.office.com/ko-KR/article/Use-Compliance-Manager-in-the-Service-Trust-Portal-Preview-5756d342-5af9-4496-82e8-4dd50fa39942).</span></span> 

### <a name="step-2--use-content-search-and-sensitive-information-types-to-find-personal-data"></a><span data-ttu-id="71c1f-123">2단계 - 콘텐츠 검색 및 중요한 정보 유형을 사용하여 및 개인 데이터 찾기</span><span class="sxs-lookup"><span data-stu-id="71c1f-123">Step 2 — Use Content Search and sensitive information types to find personal data</span></span> 

<span data-ttu-id="71c1f-p106">작업 환경에서 GDPR이 적용되는 개인 데이터를 검색합니다. 중요한 정보 유형과 콘텐츠 검색을 사용하여 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="71c1f-p106">Discover personal data in your environment that is subject to the GDPR. Use Content Search together with sensitive information types to:</span></span>

-   <span data-ttu-id="71c1f-126">개인 데이터가 있는 위치를 찾아 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="71c1f-126">Find and report on where personal data resides.</span></span>

-   <span data-ttu-id="71c1f-127">중요한 데이터 유형 및 기타 쿼리를 최적화하여 사용자 환경의 모든 개인 데이터를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="71c1f-127">Optimize sensitive data types and other queries to find all personal data in your environment.</span></span>

![콘텐츠 검색 및 중요한 정보 유형을 사용하여 개인 데이터 찾기](Media/Overview-image2.png)

<span data-ttu-id="71c1f-p107">중요한 정보 유형은 자동화된 프로세스가 상태 서비스 번호 및 신용 카드 번호와 같은 특정 정보 유형을 인식하는 방법을 정의합니다. 이 문서에는 시작점으로 사용할 수 있는 정보 집합이 포함되어 있습니다. EU 국가의 개인 데이터의 경우 앞으로 좀 더 많은 중요한 정보 유형이 제공될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="71c1f-p107">Sensitive information types define how the automated process recognizes specific information types such as health service numbers and credit card numbers. This article includes a set you can use as a starting point. Many more sensitive information types are coming soon for personal data in EU countries.</span></span>

<span data-ttu-id="71c1f-132">자세한 내용은 [개인 데이터 검색 및 찾기](search-for-and-find-personal-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="71c1f-132">For more information, see [Search for and find personal data](search-for-and-find-personal-data.md).</span></span> 

## <a name="classify-protect-and-monitor-personal-data-in-office-365-and-other-saas-apps"></a><span data-ttu-id="71c1f-133">Office 365 및 기타 SaaS 앱에서 개인 데이터 분류, 보호 및 모니터링</span><span class="sxs-lookup"><span data-stu-id="71c1f-133">Classify, protect, and monitor personal data in Office 365 and other SaaS apps</span></span>

<span data-ttu-id="71c1f-134">Office 365에서 정보 보호에 사용되는 기능 중 일부를 다른 SaaS 응용 프로그램에서 중요한 데이터를 보호하는 데도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71c1f-134">Some of the capabilities used for information protection in Office 365 can also be used to protect sensitive data in other SaaS applications.</span></span>

![개인 데이터 분류, 보호 및 모니터링](Media/Overview-image3.png)

<span data-ttu-id="71c1f-136">이 그림은 이 섹션의 나머지 부분을 나타냅니다(3-5단계).</span><span class="sxs-lookup"><span data-stu-id="71c1f-136">This illustration is described by the rest this section (steps 3-5).</span></span>

### <a name="step-3--decide-if-you-want-to-use-labels-in-addition-to-sensitive-information-types"></a><span data-ttu-id="71c1f-137">3단계 - 중요한 정보 유형 외에도 레이블을 사용할지 여부 결정</span><span class="sxs-lookup"><span data-stu-id="71c1f-137">Step 3 — Decide if you want to use labels in addition to sensitive information types</span></span>

<span data-ttu-id="71c1f-p108">중요한 정보 유형은 분류의 한 형태입니다. 레이블도 구현하려는 경우에는 [개인 데이터에 대한 분류 스키마 설계](architect-a-classification-schema-for-personal-data.md)를 참조하세요. 레이블을 적용하려면 [Office 365의 개인 데이터에 레이블 적용](apply-labels-to-personal-data-in-office-365.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="71c1f-p108">Sensitive information types are a form of classification. See [Architect a classification schema for personal data](architect-a-classification-schema-for-personal-data.md), to decide if you also want to implement labels. To apply labels, see [Apply labels to personal data in Office 365](apply-labels-to-personal-data-in-office-365.md).</span></span>

<span data-ttu-id="71c1f-p109">이 그림에서 보면 중요한 정보 유형 및 레이블이 Office 365 전반에서 작동합니다. 머지 않아 Cloud App Security에서 이러한 항목을 사용하여 Box 및 Salesforce 등의 기타 SaaS 앱에서 중요한 데이터를 찾을 수 있을 것입니다.</span><span class="sxs-lookup"><span data-stu-id="71c1f-p109">In the illustration, sensitive information types and labels work across Office 365. Coming soon, you can use these with Cloud App Security to find sensitive data in other SaaS apps, such as Box and Salesforce.</span></span>

### <a name="step-4--protect-personal-data-in-office-365"></a><span data-ttu-id="71c1f-143">4단계 - Office 365에서 개인 데이터 보호</span><span class="sxs-lookup"><span data-stu-id="71c1f-143">Step 4 — Protect personal data in Office 365</span></span> 

<span data-ttu-id="71c1f-p110">개인 데이터의 보호는 Office 365 데이터 손실 방지 기능을 통해 시작됩니다. 전자 메일을 위한 Office 365 메시지 암호화를 포함하여 개인 데이터에 대한 액세스를 보호하는 데 권장되는 다른 몇 가지 기능도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71c1f-p110">Protection for personal data starts with Office 365 data loss prevention. There are several other capabilities recommended for protecting access to personal data, including Office 365 Message Encryption for email.</span></span>

<span data-ttu-id="71c1f-146">이러한 보호 기능의 대상을 다음과 같은 특정 데이터 집합으로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71c1f-146">These protections can be targeted to specific data sets:</span></span>

-   <span data-ttu-id="71c1f-147">사이트 및 라이브러리 수준 사용 권한</span><span class="sxs-lookup"><span data-stu-id="71c1f-147">Site and library-level permissions</span></span>

-   <span data-ttu-id="71c1f-148">사이트 수준 외부 공유 정책</span><span class="sxs-lookup"><span data-stu-id="71c1f-148">Site-level external sharing policies</span></span>

-   <span data-ttu-id="71c1f-149">사이트 수준 장치 액세스 제어</span><span class="sxs-lookup"><span data-stu-id="71c1f-149">Site-level device access policies</span></span>

<span data-ttu-id="71c1f-150">Office 365 및 기타 클라우드 서비스에 대한 액세스 보호에는 다음이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="71c1f-150">Protection for access to Office 365 and other cloud services include:</span></span>

-   <span data-ttu-id="71c1f-151">EMS(Enterprise Mobility + Security)의 ID 및 장치 액세스 보호</span><span class="sxs-lookup"><span data-stu-id="71c1f-151">Identity and device access protection in Enterprise Mobility + Security (EMS)</span></span>

-   <span data-ttu-id="71c1f-152">권한이 부여된 액세스 관리</span><span class="sxs-lookup"><span data-stu-id="71c1f-152">Privileged access management</span></span>

-   <span data-ttu-id="71c1f-153">Windows 10 보안 기능</span><span class="sxs-lookup"><span data-stu-id="71c1f-153">Windows 10 security capabilities</span></span>

<span data-ttu-id="71c1f-154">보호 적용에 대한 자세한 내용은 [Office 365에서 개인 데이터에 보호 적용](apply-protection-to-personal-data-in-office-365.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="71c1f-154">For more information about applying proteciton, see [Apply protection to personal data in Office 365](apply-protection-to-personal-data-in-office-365.md).</span></span>

### <a name="step-5--monitor-for-leaks-of-personal-data"></a><span data-ttu-id="71c1f-155">5단계 - 개인 데이터 누수 모니터링</span><span class="sxs-lookup"><span data-stu-id="71c1f-155">Step 5 — Monitor for leaks of personal data</span></span>

<span data-ttu-id="71c1f-p111">Office 365 데이터 손실 방지 보고서는 중요한 데이터의 모니터링 결과를 가장 자세히 제공합니다. Office 365 감사 로그를 사용하여 자동화된 경고를 설정하고 위반을 조사할 수 있습니다. Cloud App Security는 확인하여 모니터링하는 중요한 데이터 범위를 다른 SaaS 공급자로 확장합니다. 이러한 도구에 대한 자세한 내용은 [개인 데이터 침해 모니터링](monitor-for-leaks-of-personal-data.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="71c1f-p111">Office 365 data loss prevention reports provide the greatest level of detail for monitoring sensitive data. You can setup automated alerts and investigate breaches by using the Office 365 audit log. Cloud App Security extends the ability to find and monitor sensitive data to other SaaS providers. For more information on these tools, see [Monitor for breaches of personal data](monitor-for-leaks-of-personal-data.md).</span></span>
