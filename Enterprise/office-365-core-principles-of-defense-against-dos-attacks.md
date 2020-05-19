---
title: 서비스 거부 공격에 대 한 방어의 Office 365 핵심 원리
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
description: Microsoft가 DoS (서비스 거부) 공격에 대 한 방어에서 absorption, 검색 및 완화의 핵심 원칙을 활용 하는 방법
ms.openlocfilehash: 78d1392adb35bead5d41f9655bea3c2680975561
ms.sourcegitcommit: 3cf463d28b7ba65957049dd3ed7cfbdf5f14fb82
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/18/2020
ms.locfileid: "44278081"
---
# <a name="core-principles-of-defense-against-denial-of-service-attacks"></a>서비스 거부 공격에 대한 보안 핵심 원칙

네트워크 기반 DoS 공격 으로부터 방어할 때의 세 가지 핵심 원리는 Absorption, 검색 및 완화입니다. Absorption가 검색 전에 수행 되 고 완화 되기 전에 검색이 수행 됩니다. DoS 공격에 대 한 최선의 방어는 Absorption입니다. 공격을 검색할 수 없는 경우에는이를 완화할 수 없습니다. 그러나 가장 작은 DoS 공격을 수용할 수 없는 경우에도 서비스는 공격을 감지할 수 있을 정도로 오래 지속 되지 않습니다.

대부분의 조직에서는 기술 및 기술 기술에 상당한 투자가 필요 하기 때문에 대부분의 조직은 DoS 공격을 위해 과다 한 용량을 구매 하는 것이 economically 불가능 합니다. 이를 통해 Microsoft 클라우드 서비스를 사용 하는 경우의 보안 혜택 중 하나가 강조 표시 됩니다. Microsoft 서비스의 엄청난 규모는 클라우드 고객에 게 비용 효율적인 방식으로 강력한 네트워크 보호 기능을 제공 합니다. 그러나 규모가 큰 경우에도 absorption, 검색 및 완화 간의 균형이 유지 되어야 합니다. 이러한 균형을 확인 하기 위해 Microsoft는 microsoft에서 충족 해야 하는 비용을 예측 하 여 공격을 평가 합니다.

검색은 cat and 마우스 게임입니다. 사용자가 공격 하는 새로운 방법을 끊임없이 확인 하 여 시스템을 처치 해야 합니다. 탐지 기능 > 완화-> 검색 > 완화 등은 무한정 지속 되는 정품 영구 상태입니다.

## <a name="defending-against-dos-attacks"></a>DoS 공격 으로부터 방어

DoS 공격을 성공적으로 방어 하려면 초기 검색이 필수적입니다. 시스템이 너무 defenders 전에 공격을 감지 하 여 응답 계획을 실행할 수 있습니다.

다음 수식을 사용 하면 DoS 공격의 영향을 보다 근접 하 게 할 수 있습니다.

   **최대 용량 (바이트/초)/증가율 (바이트/초) = 영향 (초)**

시간에 영향을 미치는 후에도 검색이 시간에 발생 하는 경우 DoS 공격이 성공할 가능성이 높습니다. 시간에 영향을 미치는 시간을 검색 하는 경우 공격에 대 한 서비스는 온라인 상태를 유지 하 고 완화 전략이 사용 되는 경우에도 액세스할 수 있어야 합니다. 따라서 DoS 공격 으로부터 보호 하기 위해 두 가지 작업을 수행할 수 있습니다.

- 용량을 늘려 최대 용량에 대 한 천장을 증대 시켜 공격을 감지 하는 데 더 많은 시간을 제공 합니다. 사용자나
- 검색 하는 데 걸리는 시간을 단축 합니다.

용량 증가는 회계에 직접적인 영향을 줍니다. 고객은 기본 absorption 용량을 개발 하 여 일부 DoS 공격 수준을 유지 하도록 하는 것이 좋습니다. 각 고객이 노출, 위험 및 재무 outlay에 대 한 자체 임계값을 가지 며 실제 absorption 용량은 고객 마다 다릅니다. 경제적 이유로 인해 검색 시간을 줄이는 방법에 대 한 연구 및 시간 투자는 대개 가장 비용 효율적인 방어 수단입니다.
