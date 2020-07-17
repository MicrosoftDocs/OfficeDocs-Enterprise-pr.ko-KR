---
title: Microsoft 365 액세스 제어 모니터링 및 감사
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
description: '요약: Microsoft 365 내에서 사용할 수 있는 다양 한 모니터링 및 감사 액세스 제어에 대 한 요약입니다.'
ms.openlocfilehash: aba1a9966cf50735ba3348fe126d7b4c9233b4b2
ms.sourcegitcommit: 4c519f054216c05c42acba5ac460fb9a821d6436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/17/2020
ms.locfileid: "44774873"
---
# <a name="monitoring-and-auditing-access-controls-in-microsoft-365"></a><span data-ttu-id="72e7b-103">Microsoft 365의 액세스 제어 모니터링 및 감사</span><span class="sxs-lookup"><span data-stu-id="72e7b-103">Monitoring and Auditing Access Controls in Microsoft 365</span></span>

<span data-ttu-id="72e7b-104">Microsoft는 Microsoft 365 내에서 발생 하는 모든 위임, 권한 및 작업에 대 한 광범위 한 모니터링 및 감사를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="72e7b-104">Microsoft performs extensive monitoring and auditing of all delegation, privileges, and operations that occur within Microsoft 365.</span></span> <span data-ttu-id="72e7b-105">Microsoft 365 액세스 제어는 최소 권한 원칙을 기반으로 하며 데이터 액세스 제어 및 감사를 통합 하는 자동화 된 프로세스입니다.</span><span class="sxs-lookup"><span data-stu-id="72e7b-105">Microsoft 365 access control is an automated process built on the principle of least privilege and incorporating data access controls and audits:</span></span>

- <span data-ttu-id="72e7b-106">허용 되는 모든 액세스를 고유 사용자가 추적할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72e7b-106">All permitted access is traceable to a unique user.</span></span> <span data-ttu-id="72e7b-107">관리자는 고객 콘텐츠를 처리 하는 데 책임이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72e7b-107">Administrators are accountable for their handling of customer content.</span></span>
- <span data-ttu-id="72e7b-108">액세스 제어 요청, 승인 및 관리 작업 로그는 보안 및 악의적인 이벤트를 분석 하기 위해 캡처됩니다.</span><span class="sxs-lookup"><span data-stu-id="72e7b-108">Access control requests, approvals, and administrative operations logs are captured for analysis of security and malicious events.</span></span>
- <span data-ttu-id="72e7b-109">액세스 수준은 보안 그룹 구성원을 기반으로 하 여 거의 실시간으로 검토 되며, 권한이 부여 된 비즈니스 근거 및 자격 요건을 충족 하는 사용자만 시스템에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72e7b-109">Access levels are reviewed in near real-time based on security group membership to ensure that only users who have authorized business justifications and meet the eligibility requirements have access to the systems.</span></span>
- <span data-ttu-id="72e7b-110">Microsoft 365, 해당 액세스 제어 및 지원 서비스 (Azure Active Directory 및 실제 데이터 센터 포함)는 독립 타사에서 [ISO/iec 27001](https://www.microsoft.com/TrustCenter/Compliance/iso-iec-27001), [iso/iec 27018](https://www.microsoft.com/TrustCenter/Compliance/iso-iec-27018), [SOC](https://www.microsoft.com/TrustCenter/Compliance/SOC), [FedRAMP](https://www.microsoft.com/TrustCenter/Compliance/FedRAMP)및 기타 [표준을](https://www.microsoft.com/TrustCenter/Compliance?service=Office#Icons)준수 하도록 정기적으로 감사 됩니다.</span><span class="sxs-lookup"><span data-stu-id="72e7b-110">Microsoft 365, its access controls, and supporting services, including Azure Active Directory and physical datacenters, are regularly audited by independent third-parties for compliance with [ISO/IEC 27001](https://www.microsoft.com/TrustCenter/Compliance/iso-iec-27001), [ISO/IEC 27018](https://www.microsoft.com/TrustCenter/Compliance/iso-iec-27018), [SOC](https://www.microsoft.com/TrustCenter/Compliance/SOC), [FedRAMP](https://www.microsoft.com/TrustCenter/Compliance/FedRAMP), and other [standards](https://www.microsoft.com/TrustCenter/Compliance?service=Office#Icons).</span></span>
- <span data-ttu-id="72e7b-111">Microsoft 365 엔지니어는 매년 보안 교육을 취하고, 높은 수준의 액세스 모범 사례를 검토 하 고, Microsoft의 보안 및 개인 정보 보호 정책을 승인 하 여 서비스에 대 한 권리를 유지 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="72e7b-111">Microsoft 365 engineers must take yearly security training, review elevated access best procedures, and acknowledge Microsoft's security and privacy policies to maintain entitlements to the service.</span></span>

<span data-ttu-id="72e7b-112">짧은 기간 내에 여러 번 실패 한 로그인과 같은 의심 스러운 작업이 감지 되 면 자동 경고가 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="72e7b-112">Automated alerts trigger when suspicious activity is detected, such as multiple failed logins within a short period.</span></span> <span data-ttu-id="72e7b-113">Microsoft 365 보안 응답 팀은 컴퓨터 학습 및 대규모 데이터 분석을 사용 하 여 작업을 검토 및 분석 하 고, 불규칙 한 액세스 패턴을 찾고, 비정상 및 불법 활동에 대 한 사전 대응 작업을 진행 합니다.</span><span class="sxs-lookup"><span data-stu-id="72e7b-113">The Microsoft 365 Security Response team uses machine learning and big data analysis to review and analyze activity, look for irregular access patterns, and proactively respond to anomalous and illicit activities.</span></span> <span data-ttu-id="72e7b-114">또한 Microsoft는 서비스에서 보안 및 액세스 제어 문제를 찾기 위해 주기적으로 위험 팀을 전담 하 고 팀이 정기적으로 팀을 관리 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72e7b-114">Microsoft also employs a dedicated team of penetration testers and engages in periodic Red Team and Blue Team exercises to find security and access control issues in the service.</span></span> <span data-ttu-id="72e7b-115">고객은 Microsoft 365에서 제공 하는 감사 보고서 및 관리 활동 API를 사용 하 여 액세스 제어 시스템의 효율성을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72e7b-115">Customers can verify the effectiveness of access control systems by using audit reports and the management activity API provided by Microsoft 365.</span></span>

<span data-ttu-id="72e7b-116">자세한 내용은 Microsoft 365의 [Office 365 관리 활동 API 참조](https://docs.microsoft.com/office/office-365-management-api/office-365-management-activity-api-reference) 및 [감사 및 보고](office-365-auditing-and-reporting-overview.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="72e7b-116">For more information, see [Office 365 Management Activity API reference](https://docs.microsoft.com/office/office-365-management-api/office-365-management-activity-api-reference) and [Auditing and reporting in Microsoft 365](office-365-auditing-and-reporting-overview.md).</span></span>
