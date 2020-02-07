---
title: Exchange Multi-Geo
ms.author: chrisda
author: chrisda
manager: serdars
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: ''
localization_priority: Priority
description: Exchange Onlinedl 다중 위치 기능에 대해 알아봅니다.
ms.openlocfilehash: 07a231a78d52ced4102e26c070eee40b9846c12f
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844779"
---
# <a name="multi-geo-capabilities-in-exchange-online"></a>Exchange Online의 다중 위치 기능

다중 위치 환경에서, 사용자별 기준으로 Exchange Online 사서함 콘텐츠(보관 중인 데이터)의 위치를 선택할 수 있습니다.

다음과 같은 방법으로 위성의 지리적 위치에서 사서함을 배치할 수 있습니다.

- 위성의 지리적 위치에서 새 Exchange Online 사서함을 바로 만듭니다.

- 사용자의 기본 설정된 데이터 위치를 변경하 여 기존 Exchange Online 사서함을 위성의 지리적 위치로 이동합니다.

- 온-프레미스 Exchange 조직의 사서함을 위성의 지리적 위치로 바로 온보딩합니다.

## <a name="mailbox-placement-and-moves"></a>사서함 배치 및 이동

Microsoft에서 필수 다중 위치 구성 단계를 완료한 후, Exchange Online에서 Azure AD의 사용자 개체에 있는 **PreferredDataLocation** 특성을 따릅니다.

Exchange Online에서 Azure AD의 **PreferredDataLocation** 속성을 Exchange Online 디렉터리 서비스의 **MailboxRegion** 속성으로 동기화합니다. **MailboxRegion**의 값이 사용자 사서함 및 관련된 보관 사서함이 위치하는 지리적 위치를 결정합니다. 사용자의 기본 사서함과 보관 사서함이 여러 지리적 위치에 있도록 구성할 수 없습니다. 사용자 개체당 하나의 지리적 위치만 구성할 수 있습니다.

- **PreferredDataLocation**이 기존 사서함을 사용하는 사용자에게 구성된 경우, 사서함이 재배치 큐에 저장되고 특정 지리적 위치로 자동으로 이동합니다.

- **PreferredDataLocation**이 기존 사서함이 없는 사용자에게 구성된 경우, 사서함을 프로비저닝하면 사서함이 지정된 지리적 위치로 프로비저닝됩니다.

- **PreferredDataLocation**이 사용자에게 지정되지 않은 경우, 사서함을 프로비저닝하면 사서함이 중앙 지리적 위치로 프로비저닝됩니다.

- **PreferredDataLocation** 코드가 틀린 경우(예: NAM 대신 NAN 입력), 사서함이 중앙 지리적 위치에서 프로비저닝됩니다.

**참고**: 다중 위치 기능 및 비즈니스용 Skype에서 지리적으로 호스팅된 모임은 사용자 개체에서 **PreferredDataLocation** 속성을 사용하여 서비스를 찾습니다. 지리적으로 호스팅된 모임에 대해 사용자 개체에서 **PreferredDataLocation** 값을 구성하는 경우, Office 365 테넌트에서 다중 지역이 활성화된 후 해당 사용자의 사서함이 지정된 지리적 위치로 자동으로 이동합니다. 

## <a name="feature-limitations-for-multi-geo-in-exchange-online"></a>Exchange Online의 다중 지역에 대한 기능 제한 사항

- EAC(Exchange 관리 센터)에서 사용할 수 있는 보안 및 준수 기능(예: 감사 및 eDiscovery)을 다중 지역 조직에서는 사용할 수 없습니다. 대신, [Office 365 보안 및 준수 센터](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8)를 사용하여 보안 및 준수 기능을 구성할 수 있습니다.

- Mac용 Outlook 사용자는 사서함을 새 지리적 위치로 이동하는 동안 온라인 보관함 폴더에 대한 액세스가 일시적으로 중단될 수 있습니다. 교차 지역 사서함 이동이 다른 시간에 완료될 수 있으므로, 이 조건은 사용자의 기본 및 보관 사서함이 다른 지리적 위치에 있을 때 발생합니다.

- 웹용 Outlook(이전의 Outlook Web App 또는 OWA)에서 지리적 위치를 넘어서 *사서함 폴더*를 공유할 수 없습니다. 예를 들어, 유럽 연합에 있는 사용자는 웹용 Outlook을 사용하여 미국에 있는 사서함에서 공유 폴더를 열 수 없습니다. 그러나 웹용 Outlook 사용자는 [Outlook Web App의 개별 브라우저 창에서 다른 사용자의 사서함 열기](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362)에 설명된 대로 개별 브라우저 창을 사용하여 다른 지리적 위치에서 *다른 사서함*을 열 수 있습니다.

  **참고**: 교차 지역 사서함 폴더 공유가 Windows의 Outlook에서 지원됩니다.

- 공용 폴더는 다중 지역 조직에서 지원됩니다. 그러나 공용 폴더가 중앙 지리적 위치에 있어야 합니다. 공용 폴더를 위성의 지리적 위치로 이동할 수 없습니다.
