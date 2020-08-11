---
title: Microsoft 365 데이터 불변성
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
description: Microsoft 365에서 규정 준수, 내부 거 버 넌 스 요구 사항 및 소송 위험을 해결 하기 위해 검색 가능한 형태의 데이터를 보존 하는 방법을 알아봅니다.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: dcc997cf157df08441bf1f6e825d0a5a468edbd1
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605640"
---
# <a name="immutability-in-microsoft-365"></a>Microsoft 365의 불변성

규정 준수, 내부 거 버 넌 스 또는 소송 위험을 충족 하려면 조직이 전자 메일 및 관련 데이터를 검색 가능한 형태로 유지 해야 합니다. 시스템에 있는 모든 데이터를 검색 가능 하 게 하 고 소멸 하거나 변경할 수 없어야 합니다. 이에 대 한 업계 표준 용어는 "불변성"입니다.

일반적으로 불변성에 대 한 일반적인 방법은 전자 메일 메시지를 별도의 읽기 전용 저장소 위치로 이동 하는 방식으로 작동 합니다. 이러한 시스템은 검색에 대 한 사서함 항목을 보존 하기 위한 목적을 제공 하지만 일반적인 일별 워크플로에서 보존 된 항목을 제거 하 여 사용자 환경에 영향을 줍니다. IT 전문가를 위해이 불변성 접근법을 사용 하려면 별도의 서버 및 저장소 인프라를 배포 하 고 지속적으로 유지 관리 해야 합니다. 검색은 메일 시스템 외부의 도구를 통해 수행 되며 관련 배포 및 유지 관리 비용을 포함 합니다.

Microsoft 365 및 해당 서비스의 보관에 대 한 보존 정책 기능을 통해 들어오는, 내부 및 나가는 데이터의 여러 클래스를 보존 하 고 보존할 수 있습니다. 해당 활동은 다음과 같습니다.

- 인바운드 및 아웃 바운드 전자 메일 통신
- 전자 메일 양식 또는 공유 온라인 문서에 포함 된 서적 및 레코드
- 모임 요청
- 못한
- 인스턴트 메시지
- 온라인 모임 중 공유 되는 문서
- 음성 사서함

또한 Microsoft는 타사 데이터 캡처 및 관리 솔루션과의 통합을 통해 다른 원본의 [데이터 보관](https://support.office.com/article/Archiving-third-party-data-in-Office-365-0ce338d5-3666-4a18-86ab-c6910ff408cc) 을 허용 하는 추가 기능을 개발 했습니다. 타사 데이터를 가져온 후에는 다음을 포함 하 여 데이터에 Microsoft 365 준수 기능을 적용할 수 있습니다.

- [소송 대기](https://docs.microsoft.com/microsoft-365/compliance/create-a-litigation-hold)
- [원본 위치 eDiscovery 및 유지](https://docs.microsoft.com/microsoft-365/compliance/manage-legal-investigations)
- [규격 검색](https://docs.microsoft.com/microsoft-365/compliance/search-for-content)
- [원본 위치 보관](https://docs.microsoft.com/microsoft-365/compliance/enable-archive-mailboxes)
- [사서함 감사](https://docs.microsoft.com/microsoft-365/compliance/enable-mailbox-auditing)
- [보존 정책](https://docs.microsoft.com/microsoft-365/compliance/retention-policies)

예를 들어 사서함이 소송 보존 상태에 있는 경우 타사 데이터는 보존 됩니다. 원본 위치 eDiscovery 또는 준수 검색을 사용 하 여 타사 데이터를 검색할 수 있습니다. 또는 Microsoft 데이터에 대해 사용할 수 있는 것과 마찬가지로 보관 및 보존 정책을 타사 데이터에 적용할 수도 있습니다. Microsoft 365에서 타사 데이터를 보관 하면 조직이 정부 및 규정 정책을 준수 하는 데 도움이 됩니다.

Microsoft 365의 보관은 증권 및 Exchange 위원회 (초) 규칙 17a-4 호환 저장소를 제공 합니다. Microsoft 365는 보존 잠금을 포함 하 여 원본 위치 보존 정책 및 보존 정책을 사용 하 여 쓰기 불가능 한 erasable 형식으로 수집 된 모든 데이터의 영구 파일을 보존 합니다.

특히 다음 사항에 유의합니다.

- 위에 설명한 보존 정책을 사용 하 여 저장 된 모든 레코드는 일반 사용자의 purview에서 전용 저장소 영역에 보존 됩니다. 권한이 부여 된 사용자만이 레코드에 액세스 하 고 검색할 수 있지만이를 변경 하거나 지울 수는 없습니다.
- 각 항목에 대 한 메타 데이터에는 보존 기간 계산에 사용 되는 타임 스탬프가 포함 됩니다. 타임 스탬프는 새 항목을 수신 하거나 만들 때 적용 되며 메타 데이터에서 수정 하거나 제거할 수 없습니다.
- Microsoft 365에서 보관을 사용 하면 사용자가 다른 보존 정책을 결합 하 여 세분화 된 보존 정책을 만들 수 있습니다. 이러한 정책은 보존 되는 항목의 유형 또는 위치와 보존 기간을 정의 합니다.
- 보존 잠금 기능을 사용 하면 사용자가 정책을 제한 된 정책으로 만들지 여부를 선택할 수 있습니다. 제한적인 정책은 보존 정책을 제거, 사용 하지 않도록 설정 또는 변경 하는 기능을 가진 사용자를 금지 합니다. 즉, 보존 잠금을 사용 하도록 설정 하 고, 사용 하지 않도록 설정할 수 없으며, 보존 기간 동안 보관 정책에 의해 수집 된 기존 custodians의 데이터를 덮어쓰기, 수정, 삭제 또는 삭제할 수 있습니다. 또한 보존 잠금에 설정 된 보존 기간은 단축 되거나 감소할 수 없습니다. 그러나 위의 설명에 따라 저장 된 데이터의 보존을 계속 하기 위해 법적 요구 사항을 충족 하는 경우에는이 방법을 사용할 수 있습니다. 보존 잠금 기능을 사용 하면 관리자 또는 특정 제어 액세스 권한이 있는 경우에도 설정을 변경 하거나 저장 된 데이터를 덮어쓰거나 지울 수 있으며, Microsoft 365의 2003 릴리스에 설명 된 지침을 사용 하 여 온라인으로 보관 합니다.

Microsoft 365이 규칙 17a-4 요구 사항에 따라 특히 규정 의무를 충족 하는 방법을 이해 하려면 Exchange Online 보관, SharePoint Online, 비즈니스용 OneDrive 및 비즈니스용 Skype에 대해 설명 하는 [백서](https://www.microsoft.com/microsoft-365/blog/wp-content/uploads/2015/11/Microsoft-EOA-White-Paper.pdf) 를 참조 하세요. 또한이 백서에서는 Microsoft 365 보관 기능에 대 한 심도 깊은 분석을 제공 하 고 SEC 규칙 17a-4의 각 요구 사항에 대해 자세히 설명 하 고, Microsoft 365 보관을 통해 이러한 요구 사항을 충족 하도록 하는 고객을 규제 하는 방법을 보여 줍니다.
