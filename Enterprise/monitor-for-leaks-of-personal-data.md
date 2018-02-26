---
title: "개인 데이터 누수 모니터링"
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 2/7/2018
ms.audience: ITPro
ms.topic: overview
ms.collection:
- Strat_O365_Enterprise
- Ent_O365
ms.service: o365-solutions
localization_priority: Priority
ms.custom:
- Strat_O365_Enterprise
- GDPR
ms.assetid: 
description: "개인 데이터의 누수를 모니터링하는 데 사용할 수 있는 세 가지 도구에 대해 알아봅니다."
ms.openlocfilehash: 04f5346a9c6554b75e9f360233c942907b826447
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2018
---
# <a name="monitor-for-leaks-of-personal-data"></a><span data-ttu-id="b5ddf-103">개인 데이터 누수 모니터링</span><span class="sxs-lookup"><span data-stu-id="b5ddf-103">Monitor for leaks of personal data</span></span>

<span data-ttu-id="b5ddf-p101">개인 데이터의 사용 및 전송을 모니터링하는 데 사용할 수 있는 많은 도구가 있습니다. 이 항목에서는 잘 작동하는 세 가지 도구에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b5ddf-p101">There are many tools that can be used to monitor the use and transport of personal data. This topic describes three tools that work well.</span></span>

![개인 데이터의 사용 및 전송을 모니터링하기 위한 도구](Media/Monitor-for-leaks-of-personal-data-image1.png)

<span data-ttu-id="b5ddf-107">이 그림의 내용</span><span class="sxs-lookup"><span data-stu-id="b5ddf-107">In the illustration:</span></span>

-   <span data-ttu-id="b5ddf-p102">SharePoint Online, 비즈니스용 OneDrive 및 전송 중인 전자 메일에서 개인 데이터를 모니터링하기 위해서는 Office 365 데이터 손실 방지 보고서로 시작합니다. 이러한 보고서는 개인 데이터 모니터링에 대한 가장 자세한 정보를 제공합니다. 그렇지만 이러한 보고서에 Office 365의 모든 서비스가 포함되어 있지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b5ddf-p102">Start with Office 365 data loss prevention reports for monitoring personal data in SharePoint Online, OneDrive for Business, and email in transit. These provide the greatest level of detail for monitoring personal data. However, these reports don’t include all services in Office 365.</span></span>

-   <span data-ttu-id="b5ddf-p103">다음으로, 경고 정책 및 Office 365 감사 로그를 사용하여 Office 365 서비스의 활동을 모니터링합니다. 지속적인 모니터링을 설정하거나 감사 로그를 검색하여 사고를 조사합니다. Office 365 감사 로그는 Sway, PowerBI, eDiscovery, Dynamics 365, Microsoft Flow, Microsoft Teams, 관리 활동, 비즈니스용 OneDrive, SharePoint Online, 전송 중인 메일 및 휴지 상태의 사서함을 비롯한 Office 365 서비스에서 작동합니다. 휴지 상태의 사서함에는 Skype 대화가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="b5ddf-p103">Next, use alert policies and the Office 365 audit log to monitor activity across Office 365 services. Setup ongoing monitoring or search the audit log to investigate an incident. The Office 365 audit log works across Office 365 services — Sway, PowerBI, eDiscovery, Dynamics 365, Microsoft Flow, Microsoft Teams, Admin activity, OneDrive for Business, SharePoint Online, mail in transit, and mailboxes at rest. Skype conversations are included in mailboxes at rest.</span></span>

-   <span data-ttu-id="b5ddf-p104">마지막으로 Microsoft Cloud App Security를 사용하여 다른 SaaS 공급자의 중요한 데이터가 포함된 파일을 모니터링합니다. 머지 않아 Azure Information Protection 및 Office(Cloud App Security 포함)에서 Office 365 중요한 정보 유형 및 통합된 레이블을 사용하는 기능이 제공될 예정입니다. 모든 SaaS 앱 또는 특정 앱(예: Box)에 적용되는 정책을 설정할 수 있습니다. Cloud App Security는 전자 메일에 첨부된 파일을 포함하는 Exchange Online의 파일을 검색하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b5ddf-p104">Finally, Use Microsoft Cloud App Security to monitor files with sensitive data in other SaaS providers. Coming soon is the ability to use Office 365 sensitive information types and unified labels across Azure Information Protection and Office with Cloud App Security. You can setup policies that apply to all of your SaaS apps or specific apps (like Box). Cloud App Security doesn’t discover files in Exchange Online, including files attached to email.</span></span>

## <a name="office-365-data-loss-prevention-reports"></a><span data-ttu-id="b5ddf-119">Office 365 데이터 손실 방지 보고서</span><span class="sxs-lookup"><span data-stu-id="b5ddf-119">Office 365 data loss prevention reports</span></span>

<span data-ttu-id="b5ddf-p105">DLP(데이터 손실 방지) 정책을 만든 후에는 의도한 대로 작동하는지와 규정 준수 상태를 유지하는 데 도움이 되는지 확인할 수 있습니다. Office 365에서 DLP 보고서를 사용하면 DLP 정책 일치, 재정의 또는 가양성 수를 빠르게 확인하고, 시간에 따라 증가 추세인지 또는 감소 추세인지를 확인하고, 다양한 방식으로 보고서를 필터링하고, 그래프의 선 위에 있는 점을 선택하여 추가 세부 사항을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5ddf-p105">After you create your data loss prevention (DLP) policies, you’ll want to verify that they’re working as you intended and helping you to stay compliant. With the DLP reports in O365_W14_2nd, you can quickly view the number of DLP policy matches, overrides, or false positives; see whether they’re trending up or down over time; filter the report in different ways; and view additional details by selecting a point on a line on the graph.</span></span>

<span data-ttu-id="b5ddf-122">DLP 보고서를 사용하여 다음을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5ddf-122">You can use the DLP reports to:</span></span>

-   <span data-ttu-id="b5ddf-123">특정 기간에 초점을 맞추고 스파이크 및 추세의 이유를 이해합니다.</span><span class="sxs-lookup"><span data-stu-id="b5ddf-123">Focus on specific time periods and understand the reasons for spikes and trends.</span></span>

-   <span data-ttu-id="b5ddf-124">조직의 DLP 정책을 위반하는 비즈니스 프로세스를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="b5ddf-124">Discover business processes that violate your organization’s DLP policies.</span></span>

-   <span data-ttu-id="b5ddf-125">DLP 정책이 비즈니스에 미치는 영향을 이해합니다.</span><span class="sxs-lookup"><span data-stu-id="b5ddf-125">Understand any business impact of the DLP policies.</span></span>

-   <span data-ttu-id="b5ddf-126">사용자가 정책을 재정의하거나 가양성을 보고하여 정책 팁을 확인할 때 제출한 근거를 봅니다.</span><span class="sxs-lookup"><span data-stu-id="b5ddf-126">View the justifications submitted by users when they resolve a policy tip by overriding the policy or reporting a false positive.</span></span>

-   <span data-ttu-id="b5ddf-127">해당 정책에 대한 일치 항목을 표시하여 특정 DLP 정책에 대한 준수를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b5ddf-127">Verify compliance with a specific DLP policy by showing any matches for that policy.</span></span>

-   <span data-ttu-id="b5ddf-128">세부 정보 창에서 DLP 정책과 일치하는 중요한 데이터가 포함된 파일의 목록을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="b5ddf-128">View a list of files with sensitive data that matches your DLP policies in the details pane.</span></span>

<span data-ttu-id="b5ddf-129">또한 DLP 보고서를 사용하여 테스트 모드에서 실행하면서 DLP 정책을 미세 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5ddf-129">In addition, you can use the DLP reports to fine tune your DLP policies as you run them in test mode.</span></span>

<span data-ttu-id="b5ddf-p106">DLP 보고서는 보안 및 준수 센터에 있습니다. 보고서 \> 보고서 보기로 이동합니다. DLP(데이터 손실 방지) 아래에서 DLP 정책 및 규칙 일치 또는 DLP 가양성 및 재정의로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="b5ddf-p106">DLP reports are in Security and Compliance center. Navigate to Reports \> View reports. Under Data loss prevention (DLP), go to either DLP policy and rule matches or DLP false positives and overrides.</span></span>

<span data-ttu-id="b5ddf-133">자세한 내용은 [데이터 손실 방지에 대한 보고서 보기](https://support.office.com/ko-KR/article/View-the-reports-for-data-loss-prevention-41eb4324-c513-4fa5-91c8-8fbd8aaba83b)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b5ddf-133">For more information, see [View the reports for data loss prevention](https://support.office.com/ko-KR/article/View-the-reports-for-data-loss-prevention-41eb4324-c513-4fa5-91c8-8fbd8aaba83b).</span></span>

![DLP 정책 일치를 표시하는 보고서](Media/Monitor-for-leaks-of-personal-data-image2.png)

## <a name="office-365-audit-log-and-alert-policies"></a><span data-ttu-id="b5ddf-135">Office 365 감사 로그 및 경고 정책</span><span class="sxs-lookup"><span data-stu-id="b5ddf-135">Office 365 audit log and alert policies</span></span>

<span data-ttu-id="b5ddf-136">Office 365 감사 로그에는 Exchange Online, SharePoint Online, 비즈니스용 OneDrive, Azure Active Directory, Microsoft Teams, Power BI, Sway 및 기타 Office 365 서비스의 이벤트가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5ddf-136">The Office 365 audit log contains events from Exchange Online, SharePoint Online, OneDrive for Business, Azure Active Directory, Microsoft Teams, Power BI, Sway, and other Office 365 services.</span></span>

<span data-ttu-id="b5ddf-137">Office 365 보안 및 준수 센터에서는 Office 365 감사 로그에 대한 보고서를 모니터링하고 보고하는 두 가지 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b5ddf-137">The Office 365 Security and Compliance Center provides two ways to monitor and report against the Office 365 audit log:</span></span>

-   <span data-ttu-id="b5ddf-138">경고 정책 설정, 경고 보기 및 추세 모니터링 — Office 365 보안 및 준수 센터에서 새 경고 정책 및 알림 대시보드 도구를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b5ddf-138">Setup alert policies, view alerts, and monitor trends — Use the new alert policy and alert dashboard tools in the Office 365 Security & Compliance Center.</span></span>

-   <span data-ttu-id="b5ddf-p107">감사 정책 직접 검색 - 지정한 날짜 범위의 모든 이벤트를 검색하거나, 작업을 수행한 사용자 작업 또는 대상 개체와 같은 특정 기준에 따라 결과를 필터링합니다.</span><span class="sxs-lookup"><span data-stu-id="b5ddf-p107">Use the Search-UnifiedAuditLog cmdlet to search the unified audit log. This log contains events from exExchangeOnline, exSharePointOnline2ndMen, exOneDriveForBusiness, and WindowsAzureActiveDirectory. You can search for all events in a specified date rage, or you can filter the results based on specific criteria, such as the user who performed the action, the action, or the target object.</span></span>

<span data-ttu-id="b5ddf-p108">정보 보안 및 준수 팀은 이러한 도구를 사용하여 Office 365 서비스에서 최종 사용자 및 관리자가 수행한 활동을 사전에 검토할 수 있습니다. 특정 사이트 모음에 대해 특정 활동이 수행될 때, 특히 GDPR 관련 정보를 포함하는 것으로 알려진 사이트에서 콘텐츠가 공유될 때 전자 메일 알림을 전송하도록 자동 경고를 구성할 수 있습니다. 이를 통해 해당 팀은 사용자에 대해 후속 조치를 취하여 회사 보안 정책이 준수되도록 하거나 추가 교육을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5ddf-p108">Information security and compliance teams can use these tools to proactively review activities performed by both end users and administrators across Office 365 services. Automatic alerts can be configured to send email notifications when certain activities occur on specific site collections - for example when content is shared from sites known to contain GDPR related information. This allows those teams to follow up with users to ensure that corporate security policies are followed, or to provide additional training.</span></span>

<span data-ttu-id="b5ddf-p109">또한 정보 보안 팀은 감사 로그를 검색하여 의심되는 데이터 침해를 조사하고, 침해의 근본 원인과 범위를 확인할 수 있습니다. 이러한 기본 제공 기능은 GDPR 감독 기관 및 데이터 주체 자체에 특정 기간 동안 데이터 침해가 발생했음을 알리는 알림을 제공하도록 요구하는 GDPR 33 및 34절을 통해 규정이 준수되도록 합니다. 감사 로그 항목은 권장 지침대로 서비스 내에서 90일 동안만 유지되며, 많은 조직은 이러한 로그를 더 오랫 동안 보관해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5ddf-p109">Information security teams can also search the audit log to investigate suspected data breaches and determine both root cause and the extent of the breach. This built in capability facilitates compliance with article 33 and 34 of the GDPR, which require notifications be provided to the GDPR supervisory authority and to the data subjects themselves of a data breach within a specific time period. Audit log entries are only retained for 90 days within the service - it is often recommended and many organizations required that these logs be retained for longer periods of time.</span></span>

<span data-ttu-id="b5ddf-p110">Microsoft Management Activity API를 통해 통합 감사 로그에 구독된 솔루션을 사용할 수 있으며, 필요에 따라 로그 항목을 저장할 수 있고 고급 대시보드 및 경고를 제공할 수 있습니다. 한 가지 예제는 [Microsoft OMS(Operations Management Suite)](https://docs.microsoft.com/ko-KR/azure/operations-management-suite/oms-solution-office-365)입니다.</span><span class="sxs-lookup"><span data-stu-id="b5ddf-p110">Solutions are available which subscribe to the Unified Audit Logs through the Microsoft Management Activity API and can both store log entries as needed, and provide advanced dashboards and alerts. One example is [Microsoft Operations Management Suite (OMS)](https://docs.microsoft.com/ko-KR/azure/operations-management-suite/oms-solution-office-365).</span></span>

<span data-ttu-id="b5ddf-149">경고 정책 및 감사 로그 검색에 대한 자세한 정보:</span><span class="sxs-lookup"><span data-stu-id="b5ddf-149">More information about alert policies and searching the audit log:</span></span>

-   [<span data-ttu-id="b5ddf-150">Office 365 보안 및 준수 센터의 경고 정책</span><span class="sxs-lookup"><span data-stu-id="b5ddf-150">Reports in the Office 365 Security &amp; Compliance Center</span></span>](https://support.office.com/ko-KR/article/Alert-policies-in-the-Office-365-Security-Compliance-Center-8927B8B9-C5BC-45A8-A9F9-96C732E58264)

-   <span data-ttu-id="b5ddf-151">[Office 365의 감사 로그에서 사용자 및 관리자 활동 검색](https://support.office.com/ko-KR/article/Search-the-audit-log-for-user-and-admin-activity-in-Office-365-57CA5138-0AE0-4D34-BD40-240441EF2FB6)(소개)</span><span class="sxs-lookup"><span data-stu-id="b5ddf-151">[Search the audit log for user and admin activity in Office 365](https://support.office.com/ko-KR/article/Search-the-audit-log-for-user-and-admin-activity-in-Office-365-57CA5138-0AE0-4D34-BD40-240441EF2FB6) (introduction)</span></span>

-   [<span data-ttu-id="b5ddf-152">Office 365 감사 로그 검색 켜기 또는 끄기</span><span class="sxs-lookup"><span data-stu-id="b5ddf-152">Turn Office 365 audit log search on or off</span></span>](https://support.office.com/ko-KR/article/Turn-Office-365-audit-log-search-on-or-off-e893b19a-660c-41f2-9074-d3631c95a014)

-   [<span data-ttu-id="b5ddf-153">Office 365 보안 및 준수 센터에서 감사 로그 검색</span><span class="sxs-lookup"><span data-stu-id="b5ddf-153">Search the audit log in the Office 365 Security & Compliance Centerhttp://go.microsoft.com/fwlink/p/?LinkId=708432</span></span>](https://support.office.com/en-us/article/Search-the-audit-log-in-the-Office-365-Security-Compliance-Center-0d4d0f35-390b-4518-800e-0c7ec95e946c?ui=en-US&rs=en-US&ad=US)

-   <span data-ttu-id="b5ddf-154">
  [Search-UnifiedAuditLog](https://technet.microsoft.com/en-us/library/mt238501(v=exchg.160).aspx)(cmdlet)</span><span class="sxs-lookup"><span data-stu-id="b5ddf-154">[Search-UnifiedAuditLog](https://technet.microsoft.com/en-us/library/mt238501(v=exchg.160).aspx) (cmdlet)</span></span> 

-   [<span data-ttu-id="b5ddf-155">Office 365 감사 로그의 자세한 속성</span><span class="sxs-lookup"><span data-stu-id="b5ddf-155">Detailed properties in the Office 365 audit log</span></span>](https://support.office.com/ko-KR/article/Detailed-properties-in-the-Office-365-audit-log-ce004100-9e7f-443e-942b-9b04098fcfc3)

## <a name="microsoft-cloud-app-security"></a><span data-ttu-id="b5ddf-156">Microsoft Cloud App Security</span><span class="sxs-lookup"><span data-stu-id="b5ddf-156">Microsoft Cloud App Security</span></span>

<span data-ttu-id="b5ddf-157">Microsoft Cloud App Security는 네트워크에서 사용 중인 다른 SaaS 앱을 검색하고, 이러한 앱과 주고받는 중요한 데이터를 검색하는 데 도움을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b5ddf-157">Microsoft Cloud App Security helps you discover other SaaS apps in use across your networks and sensitive data that is sent to and from these apps.</span></span>

<span data-ttu-id="b5ddf-p111">Microsoft Cloud App Security는 클라우드 앱에 대해 보다 자세한 가시성, 제어 기능 및 향상된 위협 보호를 제공하는 포괄적인 서비스입니다. 이 서비스는 모든 장치에서 네트워크에 연결된 15,000가지 이상의 클라우드 응용 프로그램을 식별하고, 위험 점수와 지속적인 위험 평가 및 분석을 제공합니다. 필요한 에이전트는 없습니다. 방화벽 및 프록시에서 정보가 수집된후 클라우드 사용 및 섀도우 ID에 대한 완전한 가시성 및 컨텍스트가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="b5ddf-p111">Microsoft Cloud App Security is a comprehensive service providing deep visibility, granular controls and enhanced threat protection for your cloud apps. It identifies more than 15,000 cloud applications in your network-from all devices-and provides risk scoring and ongoing risk assessment and analytics. No agents required: information is collected from your firewalls and proxies to give you complete visibility and context for cloud usage and shadow IT.</span></span>

<span data-ttu-id="b5ddf-p112">클라우드 환경을 보다 잘 이해하기 위해 Cloud App Security 조사 기능은 승인되고 관리되는 앱에 대한 모든 활동, 파일 및 계정을 자세히 확인할 수 있도록 합니다. 파일 수준에서 자세한 정보를 얻고 클라우드 앱에서 데이터가 이동하는 위치를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5ddf-p112">To better understand your cloud environment, Cloud App Security investigate feature provides deep visibility into all activities, files and accounts for sanctioned and managed apps. You can gain detailed information on a file level and discover where data travels in the cloud apps.</span></span>

<span data-ttu-id="b5ddf-163">예를 들어, 다음 그림에서는 GDPR 준수에 도움이 되는 두 가지 Cloud App Security 정책을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b5ddf-163">For examples, the following illustration demonstrates two Cloud App Security policies that can help with GDPR.</span></span>

![예제 Cloud App Security 정책](Media/Monitor-for-leaks-of-personal-data-image3.png)

<span data-ttu-id="b5ddf-165">첫 번째 정책은 선택한 미리 정의된 PII 특성 또는 사용자 지정 식을 포함하는 파일이 선택한 SaaS 앱을 통해 조직 외부에서 공유되면 경고합니다.</span><span class="sxs-lookup"><span data-stu-id="b5ddf-165">The first policy alerts when files with a predefined PII attribute or custom expression that you choose is shared outside the organization from the SaaS apps that you choose.</span></span>

<span data-ttu-id="b5ddf-p113">두 번째 정책은 관리되지 않는 모든 장치로의 파일 다운로드를 차단합니다. 찾으려는 파일 내 특성과 정책을 적용할 SaaS 앱을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b5ddf-p113">The second policy blocks downloads of files to any unmanaged device. You choose the attributes within the files to look for and the SaaS apps you want the policy to apply to.</span></span>

<span data-ttu-id="b5ddf-168">Cloud App Security에 다음 특성 형식의 곧 제공될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="b5ddf-168">These attribute types are coming soon to Cloud App Security:</span></span>

-   <span data-ttu-id="b5ddf-169">Office 365 중요한 정보 유형</span><span class="sxs-lookup"><span data-stu-id="b5ddf-169">Office 365 sensitive information types</span></span>

-   <span data-ttu-id="b5ddf-170">Office 365 및 Azure Information Protection의 통합된 레이블</span><span class="sxs-lookup"><span data-stu-id="b5ddf-170">Unified labels across Office 365 and Azure Information Protection</span></span>

### <a name="cloud-app-security-dashboard"></a><span data-ttu-id="b5ddf-171">Cloud App Security 대시보드</span><span class="sxs-lookup"><span data-stu-id="b5ddf-171">Microsoft Cloud App Security</span></span>

<span data-ttu-id="b5ddf-p114">아직 Cloud App Security를 사용하지 않고 이는 경우 먼저 시작하세요. Cloud App Security에 액세스하려면 <https://portal.cloudappsecurity.com>으로 이동하세요.</span><span class="sxs-lookup"><span data-stu-id="b5ddf-p114">If you haven’t yet started to use Cloud App Security, begin by starting it up. To access Cloud App Security: <https://portal.cloudappsecurity.com>.</span></span>

<span data-ttu-id="b5ddf-p115">참고: Cloud App Security를 시작할 때 또는 레이블을 할당하기 전에 '파일에서 Azure Information Protection 분류 레이블 자동 검색’(일반 설정)을 사용하도록 설정해야 합니다. 설정 후에는 Cloud App Security가 기존 파일이 수정될 때까지 다시 검색하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b5ddf-p115">Note: Be sure to enable ‘Automatically scan files for Azure Information Protection classification labels’ (in General settings) when getting started with Cloud App Security or before you assign labels. After setup, Cloud App Security does not scan existing files again until they are modified.</span></span>

![경고에 대한 정보를 표시하는 대시보드](Media/Monitor-for-leaks-of-personal-data-image4.png)

<span data-ttu-id="b5ddf-177">추가 정보:</span><span class="sxs-lookup"><span data-stu-id="b5ddf-177">More Information</span></span>

-   [<span data-ttu-id="b5ddf-178">Cloud App Security 배포</span><span class="sxs-lookup"><span data-stu-id="b5ddf-178">Deploy Cloud App Security</span></span>](https://docs.microsoft.com/ko-KR/cloud-app-security/getting-started-with-cloud-app-security)

-   [<span data-ttu-id="b5ddf-179">Microsoft Cloud App Security에 대한 자세한 정보</span><span class="sxs-lookup"><span data-stu-id="b5ddf-179">More information about Microsoft Cloud App Security</span></span>](https://www.microsoft.com/ko-KR/cloud-platform/cloud-app-security)

-   [<span data-ttu-id="b5ddf-180">Microsoft Cloud App Security 프록시를 사용하여 중요한 정보 다운로드 차단</span><span class="sxs-lookup"><span data-stu-id="b5ddf-180">Block downloads of sensitive information using the Microsoft Cloud App Security proxy</span></span>](https://docs.microsoft.com/ko-KR/cloud-app-security/use-case-proxy-block-session-aad)

## <a name="example-file-and-activity-policies-to-detect-sharing-of-personal-data"></a><span data-ttu-id="b5ddf-181">개인 데이터의 공유를 감지하는 예제 파일 및 활동 정책</span><span class="sxs-lookup"><span data-stu-id="b5ddf-181">Example file and activity policies to detect sharing of personal data</span></span>

### <a name="detect-sharing-of-files-containing-pii--credit-card-number"></a><span data-ttu-id="b5ddf-182">PII를 포함하는 파일 공유 감지 - 신용 카드 번호</span><span class="sxs-lookup"><span data-stu-id="b5ddf-182">Detect sharing of files containing PII — Credit card number</span></span>

<span data-ttu-id="b5ddf-183">신용 카드 번호를 포함하는 파일이 승인된 클라우드 앱에서 공유될 때 경고합니다.</span><span class="sxs-lookup"><span data-stu-id="b5ddf-183">Alert when a file containing a credit card number is shared from an approved cloud app.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="b5ddf-184"><strong>제어</strong></span><span class="sxs-lookup"><span data-stu-id="b5ddf-184"><strong>control</strong></span></span></th>
<th align="left"><span data-ttu-id="b5ddf-185"><strong>설정</strong></span><span class="sxs-lookup"><span data-stu-id="b5ddf-185"><strong>Settings</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="b5ddf-186">정책 유형</span><span class="sxs-lookup"><span data-stu-id="b5ddf-186">Policy type</span></span></td>
<td align="left"><span data-ttu-id="b5ddf-187">파일 정책</span><span class="sxs-lookup"><span data-stu-id="b5ddf-187">File policy</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="b5ddf-188">정책 템플릿</span><span class="sxs-lookup"><span data-stu-id="b5ddf-188">Policy template format definition</span></span></td>
<td align="left"><span data-ttu-id="b5ddf-189">템플릿 없음</span><span class="sxs-lookup"><span data-stu-id="b5ddf-189">No template</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="b5ddf-190">정책 심각도</span><span class="sxs-lookup"><span data-stu-id="b5ddf-190">Policy severity</span></span></td>
<td align="left"><span data-ttu-id="b5ddf-191">높음</span><span class="sxs-lookup"><span data-stu-id="b5ddf-191">High</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="b5ddf-192">범주</span><span class="sxs-lookup"><span data-stu-id="b5ddf-192">Category</span></span></td>
<td align="left"><span data-ttu-id="b5ddf-193">DLP</span><span class="sxs-lookup"><span data-stu-id="b5ddf-193">DLP policies</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="b5ddf-194">필터 설정</span><span class="sxs-lookup"><span data-stu-id="b5ddf-194">Filter settings</span></span></td>
<td align="left"><p><span data-ttu-id="b5ddf-195">액세스 수준 = 공용(인터넷), 공용, 외부</span><span class="sxs-lookup"><span data-stu-id="b5ddf-195">Access level = Public (Internet), Public, External</span></span></p>
<p><span data-ttu-id="b5ddf-196">앱 = &lt;앱 선택&gt;(특정 SaaS 앱으로 모니터링을 제한하려는 경우 이 설정 사용)</span><span class="sxs-lookup"><span data-stu-id="b5ddf-196">App = &lt;select apps&gt; (use this setting if you want to limit monitoring to specific SaaS apps)</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="b5ddf-197">적용 대상</span><span class="sxs-lookup"><span data-stu-id="b5ddf-197">Apply to</span></span></td>
<td align="left"><span data-ttu-id="b5ddf-198">모든 파일, 모든 소유자</span><span class="sxs-lookup"><span data-stu-id="b5ddf-198">All files, all owners</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="b5ddf-199">콘텐츠 검사</span><span class="sxs-lookup"><span data-stu-id="b5ddf-199">Content inspection</span></span></td>
<td align="left"><p><span data-ttu-id="b5ddf-200">현재 식과 일치하는 파일 포함: 모든 국가: 재무: 신용 카드 번호</span><span class="sxs-lookup"><span data-stu-id="b5ddf-200">Includes files that match a present expression: All countries: Finance: Credit card number</span></span></p>
<p><span data-ttu-id="b5ddf-201">관련 컨텍스트는 필요하지 않음: (regex 뿐만 아니라 키워드도 검색 대상임)</span><span class="sxs-lookup"><span data-stu-id="b5ddf-201">Don’t require relevant context: unchecked (this will match keywords as well as regex)</span></span></p>
<p><span data-ttu-id="b5ddf-202">일치하는 항목이 1개 이상인 파일 포함</span><span class="sxs-lookup"><span data-stu-id="b5ddf-202">Includes files with at least 1 match</span></span></p>
<p><span data-ttu-id="b5ddf-203">위반의 마지막 4자 마스크 해제: 선택 취소됨</span><span class="sxs-lookup"><span data-stu-id="b5ddf-203">Unmask the last 4 characters of the violation: checked</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="b5ddf-204">경고</span><span class="sxs-lookup"><span data-stu-id="b5ddf-204">Alerts</span></span></td>
<td align="left"><p><span data-ttu-id="b5ddf-205">각각의 일치 파일에 대한 경고 만들기: 선택됨</span><span class="sxs-lookup"><span data-stu-id="b5ddf-205">Create an alert for each matching file: checked</span></span></p>
<p><span data-ttu-id="b5ddf-206">일별 경고 제한: 1000</span><span class="sxs-lookup"><span data-stu-id="b5ddf-206">Daily alert limit: 1000</span></span></p>
<p><span data-ttu-id="b5ddf-207">전자 메일 알림 선택: 선택됨</span><span class="sxs-lookup"><span data-stu-id="b5ddf-207">Select an alert as email: checked</span></span></p>
<p><span data-ttu-id="b5ddf-208">받는 사람: infosec@contoso.com</span><span class="sxs-lookup"><span data-stu-id="b5ddf-208">To: infosec@contoso.com</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="b5ddf-209">거버넌스</span><span class="sxs-lookup"><span data-stu-id="b5ddf-209">Governance</span></span></td>
<td align="left"><p><span data-ttu-id="b5ddf-210">Microsoft 비즈니스용 OneDrive</span><span class="sxs-lookup"><span data-stu-id="b5ddf-210">OneDrive for Business Hybrid</span></span></p>
<p><span data-ttu-id="b5ddf-211">비공개로 지정: 외부 사용자 제거 선택</span><span class="sxs-lookup"><span data-stu-id="b5ddf-211">Make private: check Remove External Users</span></span></p>
<p><span data-ttu-id="b5ddf-212">다른 모든 설정: 선택되지 않음</span><span class="sxs-lookup"><span data-stu-id="b5ddf-212">All other settings: unchecked</span></span></p>
<p><span data-ttu-id="b5ddf-213">Microsoft SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="b5ddf-213">Microsoft SharePoint Online</span></span></p>
<p><span data-ttu-id="b5ddf-214">비공개로 지정: 외부 사용자 제거 선택</span><span class="sxs-lookup"><span data-stu-id="b5ddf-214">Make private: check Remove External Users</span></span></p>
<p><span data-ttu-id="b5ddf-215">다른 모든 설정: 선택되지 않음</span><span class="sxs-lookup"><span data-stu-id="b5ddf-215">All other settings: unchecked</span></span></p></td>
</tr>
</tbody>
</table>

<span data-ttu-id="b5ddf-216">비슷한 정책:</span><span class="sxs-lookup"><span data-stu-id="b5ddf-216">Similar policies:</span></span>

-   <span data-ttu-id="b5ddf-217">PII를 포함하는 파일 공유 감지 - 전자 메일 주소</span><span class="sxs-lookup"><span data-stu-id="b5ddf-217">Detect sharing of Files containing PII - Email Address</span></span>

-   <span data-ttu-id="b5ddf-218">PII를 포함하는 파일 공유 감지 - 여권 번호</span><span class="sxs-lookup"><span data-stu-id="b5ddf-218">Detect sharing of Files containing PII - Passport Number</span></span>

### <a name="detect-customer-or-hr-data-in-box-or-onedrive-for-business"></a><span data-ttu-id="b5ddf-219">Box 또는 비즈니스용 OneDrive에서 고객 또는 HR 데이터 감지</span><span class="sxs-lookup"><span data-stu-id="b5ddf-219">Detect Customer or HR Data in Box or OneDrive for Business</span></span>

<span data-ttu-id="b5ddf-220">고객 데이터 또는 HR 데이터로 레이블이 표시된 파일은 비즈니스용 OneDrive 또는 Box로 업로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="b5ddf-220">Alert when a file labeled as Customer Data or HR Data is uploaded to OneDrive for Business or Box.</span></span>

<span data-ttu-id="b5ddf-221">참고:</span><span class="sxs-lookup"><span data-stu-id="b5ddf-221">Notes:</span></span>

-   <span data-ttu-id="b5ddf-222">Box 모니터링을 사용하려면 API Connector SDK를 사용하여 커넥터를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5ddf-222">Box monitoring requires a connector be configured using the API Connector SDK.</span></span>

-   <span data-ttu-id="b5ddf-223">이 정책에는 현재 비공개 미리 보기 상태인 기능이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="b5ddf-223">This policy requires capabilities that are currently in private preview.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="b5ddf-224"><strong>제어</strong></span><span class="sxs-lookup"><span data-stu-id="b5ddf-224"><strong>control</strong></span></span></th>
<th align="left"><span data-ttu-id="b5ddf-225"><strong>설정</strong></span><span class="sxs-lookup"><span data-stu-id="b5ddf-225"><strong>Settings</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="b5ddf-226">정책 유형</span><span class="sxs-lookup"><span data-stu-id="b5ddf-226">Policy type</span></span></td>
<td align="left"><span data-ttu-id="b5ddf-227">활동 정책</span><span class="sxs-lookup"><span data-stu-id="b5ddf-227">Activity policy</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="b5ddf-228">정책 템플릿</span><span class="sxs-lookup"><span data-stu-id="b5ddf-228">Policy template format definition</span></span></td>
<td align="left"><span data-ttu-id="b5ddf-229">템플릿 없음</span><span class="sxs-lookup"><span data-stu-id="b5ddf-229">No template</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="b5ddf-230">정책 심각도</span><span class="sxs-lookup"><span data-stu-id="b5ddf-230">Policy severity</span></span></td>
<td align="left"><span data-ttu-id="b5ddf-231">높음</span><span class="sxs-lookup"><span data-stu-id="b5ddf-231">High</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="b5ddf-232">범주</span><span class="sxs-lookup"><span data-stu-id="b5ddf-232">Category</span></span></td>
<td align="left"><span data-ttu-id="b5ddf-233">제어 공유</span><span class="sxs-lookup"><span data-stu-id="b5ddf-233">Sharing Control</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="b5ddf-234">작업</span><span class="sxs-lookup"><span data-stu-id="b5ddf-234">Act on data.</span></span></td>
<td align="left"><span data-ttu-id="b5ddf-235">단일 활동</span><span class="sxs-lookup"><span data-stu-id="b5ddf-235">Single activity</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="b5ddf-236">필터 설정</span><span class="sxs-lookup"><span data-stu-id="b5ddf-236">Filter settings</span></span></td>
<td align="left"><p><span data-ttu-id="b5ddf-237">활동 유형 = 파일 업로드</span><span class="sxs-lookup"><span data-stu-id="b5ddf-237">Activity type = Upload File</span></span></p>
<p><span data-ttu-id="b5ddf-238">앱 = Microsoft 비즈니스용 OneDrive 및 Box</span><span class="sxs-lookup"><span data-stu-id="b5ddf-238">App = Microsoft OneDrive for Business and Box</span></span></p>
<p><span data-ttu-id="b5ddf-239">분류 레이블(현재 비공개 미리 보기로 제공): Azure Information Protection = 고객 데이터, 인사 — 급여 데이터, 인사 - 직원 데이터</span><span class="sxs-lookup"><span data-stu-id="b5ddf-239">Classification Label (currently in private preview): Azure Information Protection = Customer Data, Human Resources—Salary Data, Human Resources—Employee Data</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="b5ddf-240">경고</span><span class="sxs-lookup"><span data-stu-id="b5ddf-240">Alerts</span></span></td>
<td align="left"><p><span data-ttu-id="b5ddf-241">경고 만들기: 선택됨</span><span class="sxs-lookup"><span data-stu-id="b5ddf-241">Create an alert: checked</span></span></p>
<p><span data-ttu-id="b5ddf-242">일별 경고 제한: 1000</span><span class="sxs-lookup"><span data-stu-id="b5ddf-242">Daily alert limit: 1000</span></span></p>
<p><span data-ttu-id="b5ddf-243">전자 메일 알림 선택: 선택됨</span><span class="sxs-lookup"><span data-stu-id="b5ddf-243">Select an alert as email: checked</span></span></p>
<p><span data-ttu-id="b5ddf-244">받는 사람: infosec@contoso.com</span><span class="sxs-lookup"><span data-stu-id="b5ddf-244">To: infosec@contoso.com</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="b5ddf-245">거버넌스</span><span class="sxs-lookup"><span data-stu-id="b5ddf-245">Governance</span></span></td>
<td align="left"><p><span data-ttu-id="b5ddf-246">모든 앱</span><span class="sxs-lookup"><span data-stu-id="b5ddf-246">All apps</span></span></p>
<p><span data-ttu-id="b5ddf-247">사용자 격리: 선택</span><span class="sxs-lookup"><span data-stu-id="b5ddf-247">Put user in quarantine: check</span></span></p>
<p><span data-ttu-id="b5ddf-248">다른 모든 설정: 선택되지 않음</span><span class="sxs-lookup"><span data-stu-id="b5ddf-248">All other settings: unchecked</span></span></p>
<p><span data-ttu-id="b5ddf-249">Office 365</span><span class="sxs-lookup"><span data-stu-id="b5ddf-249">Office 365</span></span></p>
<p><span data-ttu-id="b5ddf-250">사용자 격리: 선택</span><span class="sxs-lookup"><span data-stu-id="b5ddf-250">Put user in quarantine: check</span></span></p>
<p><span data-ttu-id="b5ddf-251">다른 모든 설정: 선택되지 않음</span><span class="sxs-lookup"><span data-stu-id="b5ddf-251">All other settings: unchecked</span></span></p></td>
</tr>
</tbody>
</table>

<span data-ttu-id="b5ddf-252">비슷한 정책:</span><span class="sxs-lookup"><span data-stu-id="b5ddf-252">Similar policies:</span></span>

-   <span data-ttu-id="b5ddf-253">고객 데이터나 HR 데이터의 대량 다운로드 감지 - 고객 데이터 또는 HR 데이터를 포함하는 많은 수의 파일을 짧은 기간 내에 단일 사용자가 다운로드한 것이 감지되면 경고합니다.</span><span class="sxs-lookup"><span data-stu-id="b5ddf-253">Detect large downloads of Customer data or HR Data — Alert when a large number of files containing customer data or HR data have been detected being downloaded by a single user within a short period of time.</span></span>

-   <span data-ttu-id="b5ddf-254">고객 및 HR 데이터 공유 감지 — 고객 또는 HR 데이터를 포함하는 파일이 공유될 때 경고합니다.</span><span class="sxs-lookup"><span data-stu-id="b5ddf-254">Detect Sharing of Customer and HR Data — Alert when files containing Customer or HR Data are shared.</span></span>
