---
title: Microsoft 클라우드 서비스의 감사 및 보고
ms.author: robmazz
author: robmazz
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
- M365-analytics
- SPO_Content
description: Office 365, Microsoft 365 및 서비스 보증 내의 감사 및 보고 기능에 대 한 개요입니다.
ms.openlocfilehash: 991eb807ee297ea9dc912be53d99c80247220c1b
ms.sourcegitcommit: 5fe1c9be652222d6956c7dad5949ddcf0bd27041
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/08/2019
ms.locfileid: "38076232"
---
# <a name="auditing-and-reporting-in-microsoft-cloud-services"></a>Microsoft 클라우드 서비스의 감사 및 보고

## <a name="introduction"></a>소개

Microsoft 클라우드 서비스에는 테 넌 트 내에서 사용자 및 관리 활동을 추적 하는 데 사용할 수 있는 여러 감사 및 보고 기능, 예를 들어 Exchange Online 및 SharePoint Online 테 넌 트 구성 설정에 대 한 변경 내용 포함 사용자가 문서 및 기타 항목에 대해 변경한 내용 Microsoft 클라우드 서비스에서 사용할 수 있는 감사 정보 및 보고서를 사용 하 여 사용자 환경을 보다 효율적으로 관리 하 고 위험을 완화 하 고 규정 준수 의무를 충족할 수 있습니다.

## <a name="security--compliance-centers"></a>보안 & 준수 센터

[Office 365 보안 & 준수 센터](https://protection.office.com), [Microsoft 365 보안 센터](https://security.microsoft.com)및 [microsoft 365 준수 센터](https://compliance.microsoft.com) 는 조직의 데이터를 보호 하는 하나의 중지 포털이 며 다양 한 감사 및 보고 기능을 포함 합니다. 이러한 센터를 통해 데이터 보호 또는 규정 준수 요구를 해결 하 고 사용자 및 관리자 작업을 감사할 수 있습니다. 구독 관리자 계정을 사용 하 여 이러한 센터에 액세스할 수 있습니다.

이러한 센터에는 여러 기능에 액세스할 수 있는 탐색 창이 포함 되어 있습니다.

- **알림:** [Office 365 Cloud App security](https://docs.microsoft.com/cloud-app-security/what-is-cloud-app-security)를 사용 하 여 알림을 관리 하 고, 보안 관련 알림을 보고, 고급 알림을 관리할 수 있습니다.
- **사용 권한:** 준수 관리자, eDiscovery 관리자 및 기타 권한을 조직의 사용자에 게 [할당](https://support.office.com/article/Give-users-access-to-the-Office-365-Security-Compliance-Center-2cfce2c8-20c5-47f9-afc4-24b059c1bd76) 하 여 이러한 센터에서 작업을 수행할 수 있도록 합니다. 각 센터에서 대부분의 기능에 대 한 사용 권한을 할당 하지만 다른 사용 권한은 Exchange 관리 센터 및 SharePoint 관리 센터를 사용 하 여 구성 해야 합니다.
- **위협 관리:** [Office 365 모바일 장치 관리](https://support.office.com/article/Overview-of-Mobile-Device-Management-for-Office-365-faa7d8e5-645d-4d59-839c-c8d4c1869e4a)를 사용 하 여 장치 관리 정책을 만들고 적용할 수 있으며,이를 통해 조직의 DLP ( [데이터 손실 방지](https://support.office.com/article/Overview-of-data-loss-prevention-policies-1966b2a7-d1e2-4d92-ab61-42efbb137f5e) ) 정책을 설정 하 고, 전자 메일 필터링, 맬웨어 방지, Domainkeys 식별 된 메일 (dkim), 안전한 첨부 파일, 안전한 링크 및 OAuth 앱을 구성 합니다.
- **데이터 거 버 넌 스:** [다른 시스템에서 전자 메일 또는 SharePoint 데이터를 Office 365로 가져오고](https://support.office.com/article/Import-PST-files-or-SharePoint-data-to-Office-365-ba688e0a-0fcb-4bd7-8e57-2b669564ea84), [보관 사서함을 구성](https://support.office.com/article/Enable-archive-mailboxes-in-the-Office-365-Security-Compliance-Center-268a109e-7843-405b-bb3d-b9393b2342ce)하 고, 전자 메일 및 조직 내의 기타 콘텐츠에 대 한 [보존 정책을](https://docs.microsoft.com/microsoft-365/compliance/retention-policies) 설정할 수 있습니다.
- **검색 & 조사:** [콘텐츠 검색](https://support.office.com/article/Run-a-Content-Search-in-the-Office-365-Security-Compliance-Center-61852fd9-fe8a-4880-a339-cb19ed3bff4a), [감사 로그](https://support.office.com/article/Search-the-audit-log-in-the-Office-365-Security-Compliance-Center-0d4d0f35-390b-4518-800e-0c7ec95e946c), 격리 및 [eDiscovery 사례 관리](https://support.office.com/article/Manage-eDiscovery-cases-in-the-Office-365-Security-Compliance-Center-edea80d6-20a7-40fb-b8c4-5e8c8395f6da) 도구를 제공 하 여 Exchange Online 사서함, 그룹 및 공용 폴더, SharePoint Online 및 비즈니스용 OneDrive에서 활동을 빠르게 확인할 수 있습니다.
- **보고서:** SharePoint Online, 비즈니스용 OneDrive, Exchange Online 및 Azure AD에 대 한 [보고서](https://support.office.com/article/Reports-in-the-Office-365-Security-Compliance-Center-7acd33ce-1ec8-49fb-b625-43bac7b58c5a) 에 빠르게 액세스할 수 있습니다.
- **서비스 보증:** Microsoft가 Office 365, Azure, Microsoft Dynamics CRM Online, Microsoft Intune 및 기타 클라우드 서비스에 대 한 글로벌 표준의 보안, 개인 정보 보호 및 준수를 유지 관리 하는 방법에 대해 설명 합니다. 또한 타사 ISO, SOC 및 기타 감사 보고서에 대 한 액세스 뿐만 아니라 Office 365의 타사 감사자에 의해 테스트 및 확인 된 다양 한 컨트롤에 대 한 세부 정보를 제공 하는 감사 되는 컨트롤에 대 한 정보도 포함 합니다.

## <a name="service-assurance"></a>서비스 보증

규정 된 업계의 많은 조직에는 광범위 한 준수 요구 사항이 적용 됩니다. 사용자는 위험 평가를 수행 하기 위해 Office 365에서 데이터의 보안 및 개인 정보 보호를 유지 하는 방법에 대 한 자세한 정보가 필요한 경우가 많습니다. Microsoft는 클라우드 서비스에서 고객 데이터의 보안 및 개인 정보를 수용 하 고, 작업을 투명 하 게 확인 하 고 독립적인 준수 보고서 및 평가에 쉽게 액세스할 수 있도록 하 여 고객의 신뢰를 획득 합니다.

서비스 보증은 Microsoft가 Office 365에서 고객 데이터의 보안, 개인 정보 보호 및 규정 준수를 유지 관리 하는 방법에 대 한 작업 및 정보를 제공 합니다. 이 문서에는 데이터 암호화, 데이터 복구, 보안 문제 관리 등의 Office 365 항목에 대 한 백서, Faq 및 기타 자료 라이브러리와 함께 타사 감사 보고서가 포함 되어 있습니다. 고객은이 정보를 사용 하 여 자체 규정 위험 평가를 수행할 수 있습니다. 규정 준수 관리자는 "서비스 보증 사용자" 역할을 할당 하 여 사용자에 게 서비스 보증에 대 한 액세스 권한을 부여할 수 있습니다. 테 넌 트 관리자는 또한 독립 감사자와 같은 외부 사용자를 제공 하 여 [Microsoft 클라우드 서비스 트러스트 포털](https://aka.ms/STP) (STP)을 통해 서비스 보증 대시보드의 정보에 액세스할 수 있습니다. STP에 액세스 하는 방법에 대 한 자세한 내용을 보려면 [Office 365 for business, Azure 및 DYNAMICS CRM Online 구독에 대 한 서비스 신뢰 포털로 시작](https://aka.ms/STPHelp)을 참조 하세요.

## <a name="onedrive-for-business-admin-center"></a>비즈니스용 OneDrive 관리 센터

Microsoft OneDrive 관리 센터에서는 조직의 비즈니스용 OneDrive 설정을 빠르고 쉽게 관리 하는 데 도움이 됩니다. OneDrive 관리 센터를 사용 하려면 onedrive.com에 대 한 액세스가 필요 합니다. 또한 조직의 전역 관리자 이거나 SharePoint 관리자 역할을 가진 사용자 지정 관리자 여야 합니다. 에서 [https://admin.onedrive.com](https://admin.onedrive.com/)비즈니스용 OneDrive 관리 센터에 액세스 합니다.

주요 기능에는 감사 로그 검색, DLP, 보존, eDiscovery 및 경고와 같은 주요 시나리오에 대 한 적절 한 관리 센터에 대 한 링크를 관리자에 게 제공 하는 규정 준수 영역이 포함 되어 있습니다.

## <a name="related-links"></a>관련 링크

- [eDiscovery 및 검색 기능](office-365-ediscovery-and-search-features.md)
- [Office 365 보고 기능](office-365-reporting-features.md)
- [Office 365 관리 작업 API](office-365-management-activity-api.md)
- [Office 365 사서함 마이그레이션](office-365-mailbox-migrations.md)
- [Office 365 엔지니어링에 대한 내부 로깅](office-365-internal-logging.md)