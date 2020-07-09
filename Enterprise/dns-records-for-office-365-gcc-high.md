---
title: Office 365 GCC High용 DNS 레코드
ms.author: dzazzo
author: dzazzo
manager: dzazzo
ms.date: 05/19/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- OGA150
- OGC150
- OGD150
- MOE150
ms.assetid: ''
description: '요약: Office 365 GCC High에 대 한 DNS 레코드'
hideEdit: true
ms.openlocfilehash: 9bcaa71ab965f01481887d50a3e6ddbbbe3fadee
ms.sourcegitcommit: 576c3dbdef535f952a861197dea5348908da9504
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/09/2020
ms.locfileid: "44339805"
---
# <a name="dns-records-for-office-365-gcc-high"></a>Office 365 GCC High용 DNS 레코드

*이 문서는 Office 365 GCC High 및 Microsoft 365 GCC High에 적용 됩니다.*

Office 365 GCC High 온 보 딩의 일부로, SMTP 및 SIP 도메인을 온라인 서비스 테 넌 트에 추가 해야 합니다.  Azure AD PowerShell에서 New-msoldomain cmdlet을 사용 하 여이 작업을 수행 하거나 [Azure 정부 포털](https://portal.azure.us) 을 사용 하 여 도메인을 추가 하 고 소유권을 증명 하는 프로세스를 시작 합니다.

테 넌 트에 도메인을 추가 하 고 유효성을 검사 한 후에는 다음 지침을 사용 하 여 서비스에 대 한 적절 한 DNS 레코드를 추가 합니다.  조직에서 인바운드 MX 레코드 및 모든 기존 Exchange 자동 검색 레코드와 관련 하 여 조직의 요구 사항에 맞게 아래 표를 수정 해야 할 수 있습니다.  이러한 DNS 레코드를 메시징 팀에 조정 하 여 전자 메일이 중단 되거나 잘못 배달 되지 않도록 하는 것이 좋습니다.

## <a name="exchange-online"></a>Exchange Online

| 종류 | 우선 순위 | 호스트 이름 | 주소 또는 값을 가리킵니다. | TTL |
| --- | --- | --- | --- | --- |
| MX | 개 | @ | *tenant*mail.protection.office365.us (자세한 내용은 아래 참조) | 1 Hour |
| TXT | - | @ | v = spf1에는 office365-all을 포함 합니다. | 1 Hour |
| CNAME | - | autodiscover | autodiscover.office365.us | 1 Hour |

### <a name="exchange-autodiscover-record"></a>Exchange 자동 검색 레코드

Exchange Server 온-프레미스를 사용 하는 경우 Exchange Online으로 마이그레이션하는 동안 기존 레코드를 그대로 두고 마이그레이션을 완료 한 후에 해당 레코드를 업데이트 하는 것이 좋습니다. 

### <a name="exchange-online-mx-record"></a>Exchange Online MX 레코드

허용 도메인에 대 한 MX 레코드 값은 위에서 설명한 표준 *형식: mail.protection.office365.us*, *테 넌* 트를 기본 테 넌 트 이름의 첫 부분으로 교체 합니다.

예를 들어 테 넌 트 이름이 contoso.onmicrosoft.us 인 경우 MX 레코드의 값으로 **contoso.mail.protection.office365.us** 을 사용 합니다.

## <a name="skype-for-business-online"></a>비즈니스용 Skype Online

### <a name="cname-records"></a>CNAME 레코드

| 유형 | 호스트 이름 | 주소 또는 값을 가리킵니다. | TTL |
| --- | --- | --- | --- |
| CNAME | sip | sipdir.online.gov.skypeforbusiness.us | 1 Hour |
| CNAME | lyncdiscover | webdir.online.gov.skypeforbusiness.us | 1 Hour |

### <a name="srv-records"></a>SRV 레코드

| 유형 | 서비스 | Protocol(프로토콜) | 포트 | 가중치 | 우선 순위 | 이름 | Target(대상) | TTL |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| SRV | \_sip | \_ls | 443 | 1  | 100 | @ | sipdir.online.gov.skypeforbusiness.us | 1시간 |
| SRV | \_sipfederationtls | \_rdp-tcp | 5061 | 1  | 100 | @ | sipfed.online.gov.skypeforbusiness.us | 1 Hour |

## <a name="additional-dns-records"></a>추가 DNS 레코드

> [!IMPORTANT]
> DNS 영역에 기존 *msoid* CNAME 레코드가 있으면 지금 dns에서 레코드를 **제거** 해야 합니다.  Msoid 레코드는 Microsoft 365 엔터프라이즈 앱 *(이전의 Office 365 ProPlus)* 과 호환 되지 않으며, 정품 인증에 성공 하지 못합니다.
