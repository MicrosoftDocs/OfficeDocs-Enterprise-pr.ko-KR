---
title: Microsoft 365 Yammer enterprise access 컨트롤
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
description: 이 문서에는 프로덕션 환경의 Yammer Enterprise Access 컨트롤에 대 한 간략 한 요약이 포함 되어 있습니다.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: a6157715836b046fa98fbdaf8427f7708b771081
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606494"
---
# <a name="yammer-enterprise-access-controls"></a>Yammer enterprise 액세스 제어 

Yammer 프로덕션 환경에 대 한 물리적 및 논리적 액세스는 소수의 사용자 (인프라 및 작업)로 제한 됩니다. 다른 Microsoft 365 엔지니어와 마찬가지로 Yammer 엔지니어는 고객 데이터에 대 한 액세스 권한이 없습니다. 승인자 수가 제한 된 Lockbox와 유사한 승인 기반 just-in-time 액세스 제어 시스템을 사용 하 여 액세스를 요청 해야 합니다. 승인자는 요청 (예: 요구 사항에 따라 요청이 합법적인 지, 비즈니스 사례, 시간 등)을 확인 한 다음 요청을 승인 하거나 거부 합니다. 요청이 승인 되 면 정의 되 고 제한 된 시간에 JIT 액세스가 부여 됩니다. 액세스 시간이 초과 되 면 액세스가 자동으로 만료 됩니다.

다른 Microsoft 365 서비스와 마찬가지로 Yammer 프로덕션 환경에 대 한 모든 액세스에서 다단계 인증을 사용 합니다. 모든 액세스 및 명령 기록은 사용자에 게 특성을 사용 하며 Yammer 보안 팀에서 정기적으로 기록 및 검토 합니다.

Yammer 관리 및 관리에 대 한 자세한 내용은 [yammer admin help](https://docs.microsoft.com/yammer/yammer-landing-page)를 참조 하십시오.