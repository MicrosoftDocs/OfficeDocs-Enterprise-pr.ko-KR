---
title: Office 365 eDiscovery 및 검색 기능 개요
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
- SPO_Content
f1.keywords:
- NOCSH
description: 감사 사용 및 투명성을 위한 eDiscovery 기능의 개요 및 Office 365 내의 기타 검색 기능
ms.openlocfilehash: 16cb8ac4703142b73d4f56bce9390743495d3fc2
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843650"
---
# <a name="ediscovery-and-search-features"></a>eDiscovery 및 검색 기능 

## <a name="ediscovery"></a>eDiscovery

EDiscovery 기능은 관리자, 준수 책임자 및 기타 권한 있는 사용자가 Office 365 사용자 활동에 대 한 포괄적인 조사를 수행할 수 있는 단일 위치를 제공 합니다. 적절 한 사용 권한이 있는 보안 관리자는 검색을 수행 하 고 콘텐츠를 보관 합니다. 검색 결과는 적용 된 보류에 대해 eDiscovery 사례가 만들어지는 것을 제외 하 고는 콘텐츠 검색에서 가져온 결과와 같습니다. EDiscovery 검색의 결과는 보안을 위해 암호화 되며, [고급 eDiscovery](https://support.office.com/article/office-365-advanced-ediscovery-fd53438a-a760-45f6-9df4-861b50161ae4)를 사용 하 여 내보낸 데이터를 분석할 수 있습니다.

## <a name="content-search"></a>콘텐츠 검색

[콘텐츠 검색](https://support.office.com/article/Run-a-Content-Search-in-the-Office-365-Security-Compliance-Center-61852fd9-fe8a-4880-a339-cb19ed3bff4a) 은 이전 ediscovery 검색 도구에 비해 향상 된 확장 및 성능 기능을 제공 하는 eDiscovery 검색 도구입니다. 콘텐츠 검색을 사용 하 여 사서함, 공용 폴더, SharePoint Online 사이트 및 비즈니스용 OneDrive 위치를 검색 합니다. 콘텐츠 검색에서는 큰 검색이 지원 됩니다. 검색할 수 있는 사서함 및 사이트의 수에는 제한이 없습니다. 또한 동시에 실행 되는 검색 수에는 제한이 없습니다. 검색을 실행 한 후에는 검색 페이지의 세부 정보 창에 콘텐츠 원본 수와 예상 검색 결과 수가 표시 됩니다. 결과를 미리 보거나 로컬 컴퓨터로 내보낼 수 있습니다. 조직에 Office 365 Enterprise E5 구독이 있는 경우 [office 365 Advanced eDiscovery](https://go.microsoft.com/fwlink/p/?LinkID=620116)의 강력한 분석 기능을 사용 하 여 분석 [결과를 준비할](https://support.office.com/article/Run-a-Content-Search-in-the-Office-365-Security-Compliance-Center-61852fd9-fe8a-4880-a339-cb19ed3bff4a#prepare) 수 있습니다.

## <a name="audit-log-search"></a>감사 로그 검색

Office 365 조직의 변경 내용을 추적 하는 것 외에도 감사 보고서를 확인 하 고 감사 로그를 내보낼 수 있습니다. Office 365 테 넌 트에서 감사를 사용 하도록 설정 하면 사용자 및 관리 활동이 이벤트 로그에 기록 되 고 검색이 가능 하 게 됩니다. 예를 들어 사서함 감사 로깅을 사용 하 여 사서함 소유자가 아닌 사용자가 사서함에서 수행 하는 작업을 추적할 수 있습니다. 규정 준수 관리자는 특정 사용자 작업에 대해 검색 및 필터 기능을 사용할 수 있습니다. 예를 들어 관리자가 사용자 관리 작업을 수행 하거나 최근 90 일 이내에 테 넌 트 구성의 변경 내용을 보려는 경우 특정 문서를 보거나 다운로드 한 사용자를 식별 합니다. 검색 결과에는 사용자 또는 관리자가 수행한 특정 작업에 대 한 중요 한 법적 정보가 포함 됩니다. Office 365에 로깅된 사용자 및 관리 활동에 대 한 설명은 [office 365의 감사 된 작업](https://support.office.com/article/Search-the-audit-log-in-the-Office-365-Security-Compliance-Center-0d4d0f35-390b-4518-800e-0c7ec95e946c#auditlogevents) 을 참조 하세요.

SharePoint Online 및 비즈니스용 OneDrive의 이벤트는 발생 한 30 분 내에 로그에 표시 됩니다. Exchange Online의 이벤트는 발생 한 24 시간 이내에 감사 로그에 표시 됩니다. Azure AD의 로그인 이벤트는 발생 시간 내에 사용할 수 있으며 Azure AD의 기타 디렉터리 이벤트는 발생 한 후에 사용할 수 있습니다. 추가 분석을 위해 감사 로그 검색 결과에서 통풍구를 내보낼 수 있습니다. 단일 감사 로그 검색에서 최대 5만 개의 항목을 내보냅니다. 이 제한에 해당 하는 추가 항목을 내보내려면 날짜 범위를 줄이거나 여러 감사 로그 검색을 실행 합니다.

다음 표에서는 활동 보고서에 표시 되는 일부 정보를 자세히 설명 합니다. 각 Office 365 작업을 통해 수집 되는 속성에 대 한 자세한 내용은 [office 365 감사 로그의 자세한 속성](https://support.office.com/article/detailed-properties-in-the-office-365-audit-log-ce004100-9e7f-443e-942b-9b04098fcfc3) 을 참조 하십시오.

| 속성 | 설명 |
|----------------|----------------------------------------------------------------------------------------------------------------------|
| 날짜 | 이벤트의 날짜 및 시간 |
| 사용자 | 작업을 수행한 사용자입니다. |
| ClientIP | 활동이 기록 될 때 사용 되는 장치의 IPv4 또는 IPv6 주소입니다. |
| CreationTime | 사용자가 활동을 수행 했을 때 UTC (협정 세계시)로 표시 된 날짜 및 시간입니다. |
| EventSource | 이벤트가 발생 한 것을 식별 합니다. 사용할 수 있는 값은 SharePoint 및 ObjectModel입니다. |
| ID | 보고서 항목의 ID입니다. ID는 보고서 항목을 고유 하 게 식별 합니다. |
| 작업 | 이 사용자의 결과 표시 작업에서 선택한 값에 해당 하는 사용자 또는 활동의 이름입니다. |
| 조직 id | 이벤트가 발생 한 조직의 Office 365 서비스에 대 한 GUID입니다. |
| UserAgent | 브라우저에서 제공 하는 사용자 브라우저에 대 한 정보입니다. |
| UserId | 작업 속성에 지정 된 작업을 실행 하 여 레코드가 기록 되는 사용자입니다. |
| UserType | 작업을 수행한 사용자의 유형입니다. 다음 값은 사용자 형식을 나타냅니다. |
|  | 0은 일반 사용자를 나타냅니다. |
|  | 2는 Office 365 조직의 관리자를 나타냅니다. |
|  | 3은 Microsoft 데이터 센터 관리자 또는 데이터 센터 시스템 계정을 나타냅니다. |
| 작업량 | 작업이 발생 한 Office 365 서비스입니다. 이 속성에 사용할 수 있는 값은 다음과 같습니다. |
|  | Exchange Online |
|  | SharePoint Online |
|  | 비즈니스용 OneDrive |
|  | Azure Active Directory 보고서 |

Office 365 감사 로그를 검색 하는 자세한 단계는 [office 365에서 감사 로그 검색](https://support.office.com/article/Search-the-audit-log-in-the-Office-365-Security-Compliance-Center-0d4d0f35-390b-4518-800e-0c7ec95e946c)을 참조 하십시오.

## <a name="search-unified-audit-log"></a>통합 감사 로그 검색

감사 로그 검색 기능을 사용 하 여 통합 된 감사 로그를 검색 합니다. 또한 Office 365는 원격 PowerShell을 사용 하 여이 로그를 검색할 수 있는 기능을 제공 합니다. Exchange Online PowerShell의 [search-unifiedauditlog cmdlet](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-audit/Search-UnifiedAuditLog?view=exchange-ps) 은 exchange Online, SharePoint Online, 비즈니스용 OneDrive 및 Azure AD에서의 사용자 작업과 관련 된 이벤트의 통합 감사 로그를 검색 하는 데 사용 됩니다. 

지정 된 날짜 범위의 모든 이벤트를 검색 하거나 특정 작업, 작업을 수행한 사용자, 대상 개체 등의 특정 조건에 따라 결과를 필터링 할 수 있습니다. 관리자는 대규모 날짜 범위 검색을 분할 하기 위해 동시에 최대 3 개의 Exchange Online PowerShell 세션을 사용할 수 있습니다.