---
title: Office 365 Yammer Enterprise 액세스 제어
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
f1.keywords:
- NOCSH
description: '요약: 프로덕션 환경의 Yammer Enterprise 액세스 제어에 대 한 간략 한 요약입니다.'
ms.openlocfilehash: 9b88ff0f8c480dd3726246e47714d9468509ef08
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841795"
---
# <a name="yammer-enterprise-access-controls"></a>Yammer Enterprise 액세스 제어 

Yammer 프로덕션 환경에 대 한 물리적 및 논리적 액세스는 소수의 사용자 (인프라 및 작업)로 제한 됩니다. 다른 Office 365 엔지니어와 마찬가지로 Yammer 엔지니어는 고객 데이터에 대 한 액세스를 영 없이 사용할 수 있습니다. 승인자 수가 제한 된 Lockbox와 유사한 승인 기반 just-in-time 액세스 제어 시스템을 사용 하 여 액세스를 요청 해야 합니다. 승인자는 요청 (예: 요구 사항에 따라 요청이 합법적인 지, 비즈니스 사례, 시간 등)을 확인 한 다음 요청을 승인 하거나 거부 합니다. 요청이 승인 되 면 정의 되 고 제한 된 시간에 JIT 액세스가 부여 됩니다. 액세스 시간이 초과 되 면 액세스가 자동으로 만료 됩니다.

다른 Office 365 서비스와 마찬가지로 Yammer 프로덕션 환경에 대 한 모든 액세스에서 다단계 인증을 사용 합니다. 모든 액세스 및 명령 기록은 사용자에 게 특성을 사용 하며 Yammer 보안 팀에서 정기적으로 기록 및 검토 합니다.

Yammer 관리 및 관리에 대 한 자세한 내용은 [Yammer Admin Help](https://support.office.com/article/yammer-–-admin-help-e1464355-1f97-49ac-b2aa-dd320b179dbe?ui=en-US&rs=en-US&ad=US)를 참조 하십시오.