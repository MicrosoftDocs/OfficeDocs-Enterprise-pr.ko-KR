---
title: Exchange Multi-Geo
ms.author: chrisda
author: chrisda
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
description: Exchange Online의 다중 지리적 기능에 대해 알아봅니다.
ms.openlocfilehash: 60d25cab08ada195d1b189b30bdce8ea505f1d19
ms.sourcegitcommit: 8ba20f1b1839630a199585da0c83aaebd1ceb9fc
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/27/2019
ms.locfileid: "30931777"
---
# <a name="multi-geo-capabilities-in-exchange-online"></a>Exchange Online의 Multi-Geo 기능

다중 위치 환경에서는 사용자 단위로 Exchange Online 사서함 콘텐츠 (휴지 상태의 데이터) 위치를 선택할 수 있습니다.

다음과 같은 방법으로 위성 위치에 사서함을 배치할 수 있습니다.

- 새 Exchange Online 사서함을 위성 위치에 직접 만들기

- 사용자의 기본 설정 데이터 위치를 변경 하 여 기존 Exchange Online 사서함을 위성 위치로 이동

- 온-프레미스 Exchange 조직의 사서함을 위성 위치로 직접 온 보 딩

## <a name="mailbox-placement-and-moves"></a>사서함 배치 및 이동
Microsoft에서 필수 구성 요소 다중 지역 구성을 완료 한 후에는 Exchange Online에서 Azure AD의 사용자 개체에 대 한 **PreferredDataLocation** 특성을 사용 합니다.

exchange online은 Azure AD의 **PreferredDataLocation** 속성을 exchange Online 디렉터리 서비스의 **MailboxRegion** 속성에 동기화 합니다. **MailboxRegion** 의 값은 사용자 사서함과 연결 된 모든 보관 사서함이 위치할 지리적 위치를 결정 합니다. 사용자의 기본 사서함과 보관 사서함이 서로 다른 지리적 위치에 있도록 구성할 수는 없습니다. 사용자 개체만 하나의 지리적 위치를 구성할 수 있습니다.

- **PreferredDataLocation** 가 기존 사서함을 사용 하는 사용자에 대해 구성 된 경우 사서함이 재배치 큐에 저장 되 고 지정 된 지리적 위치로 자동으로 이동 됩니다. 

- **PreferredDataLocation** 가 기존 사서함이 없는 사용자에 대해 구성 된 경우 사서함을 프로 비전 하면 지정 된 지리적 위치로 프로 비전 됩니다. 

- 사용자에 대해 **PreferredDataLocation** 를 지정 하지 않으면 사서함을 프로 비전 할 때 중앙 위치에 프로 비전 됩니다.

- **PreferredDataLocation** 코드가 잘못 된 경우 (예: 베트남 대신 NAN 유형) 사서함이 중앙 위치에서 프로 비전 됩니다.

**참고**: 다중 위치 기능 및 비즈니스용 Skype 온라인 지역적으로 호스팅 모임에서는 사용자 개체에 대해 **PreferredDataLocation** 속성을 사용 하 여 서비스를 찾습니다. 지역적으로 호스트 된 모임에 대해 사용자 개체에 대해 **PreferredDataLocation** 값을 구성 하는 경우 Office 365 테 넌 트에서 다중 위치를 사용 하도록 설정한 후 해당 사용자의 사서함이 지정 된 지리적 위치로 자동으로 이동 됩니다.

## <a name="feature-limitations-for-multi-geo-in-exchange-online"></a>Exchange Online의 다중 지역에 대 한 기능 제한 사항

1. EAC (Exchange 관리 센터)에서 사용할 수 있는 보안 및 규정 준수 기능 (예: 감사 및 eDiscovery)은 다중 지역 조직에서 사용할 수 없습니다. 대신 [Office 365 security & 준수 센터](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8) 를 사용 하 여 보안 및 규정 준수 기능을 구성 해야 합니다.

2. Outlook for Mac 사용자는 자신의 사서함을 새 지리적 위치로 이동 하는 동안 해당 온라인 보관 폴더에 일시적으로 액세스 하지 못할 수 있습니다. 이 조건은 지리적 사서함 이동이 서로 다른 시간대에서 완료 될 수 있기 때문에 사용자의 기본 및 보관 사서함이 서로 다른 지리적 위치에 있을 때 발생 합니다.

3. 사용자가 웹에서 outlook의 지리적 위치 (이전의 outlook web App 또는 OWA)에서 *사서함 폴더* 를 공유할 수 없습니다. 예를 들어 유럽 연합의 사용자가 웹에서 Outlook을 사용 하 여 미국에 있는 사서함의 공유 폴더를 열 수 없습니다. 그러나 웹 사용자의 outlook에서는 다른 [사용자의 사서함을 Outlook Web App의 별도의 브라우저 창에 열기](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362)에 설명 된 대로 별도의 브라우저 창을 사용 하 여 다른 달의 *기타 사서함* 을 열 수 있습니다.

    **참고**: 다중 지역 사서함 폴더 공유는 Windows의 Outlook에서 지원 됩니다.

