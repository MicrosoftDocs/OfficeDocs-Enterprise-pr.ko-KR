---
title: Microsoft 365 데이터 손상 처리
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
ms.custom: seo-marvel-apr2020
description: 이 문서에서는 Microsoft 365의 데이터 손상 및 데이터를 방지 하 고 복구 하기 위해 Microsoft에서 수행 하는 작업에 대해 설명 합니다.
ms.openlocfilehash: dc8e865a69e110fa0a68e6cd9d9f4d6b45d43d71
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606634"
---
# <a name="dealing-with-data-corruption-in-microsoft-365"></a>Microsoft 365의 데이터 손상 처리

대규모 클라우드 서비스를 실행할 때의 까다로운 측면 중 하나는 대규모 데이터 및 독립 시스템에 따라 데이터 손상을 처리 하는 방법입니다. 데이터 손상은 다음과 같은 이유로 인해 발생할 수 있습니다.

- 응용 프로그램 또는 인프라 버그 (일부 또는 모든 응용 프로그램 상태 손상)
- 데이터가 손실 되거나 데이터를 읽을 수 없게 되는 하드웨어 문제
- 사용자 운영 오류
- 악의적인 해커 및 불만을 품은 직원
- 데이터 손실을 발생 시키는 외부 서비스의 사건

데이터 무결성이 높을수록 데이터 손상 사고가 더 적기 때문에 Microsoft는 손상 발생을 방지 하기 위해 Microsoft 365 보호 메커니즘을 기본적으로 제공 하 고 시스템 및 프로세스를 통해 데이터를 복구할 수 있습니다. 다음을 포함 하 여 데이터 손상에 대 한 복구 력을 늘리기 위해 엔지니어링 릴리스 프로세스의 다양 한 단계 내에 검사 및 프로세스가 존재 합니다.

- 시스템 디자인
- 코드 구성 및 구조
- 코드 검토
- 단위 테스트, 통합 테스트 및 시스템 테스트
- 여행 와이어 테스트/게이트

Microsoft 365 프로덕션 환경에서 데이터 센터 간의 피어 복제를 사용 하면 항상 모든 데이터가 포함 된 라이브 복사본을 여러 개 유지할 수 있습니다. 표준 이미지 및 스크립트는 손실 된 서버를 복구 하는 데 사용 되 고, 복제 된 데이터는 고객 데이터를 복원 하는 데 사용 됩니다. 기본 제공 되는 데이터 복구 력 검사 및 프로세스로 인해 Microsoft는 SharePoint Online의 기본 제공 복제 및 내부 코드 리포지토리 도구인 원본 서비스 센터를 사용 하 여 Microsoft 365 information system 설명서 (보안 관련 문서 포함)의 백업만 유지 합니다. 시스템 설명서는 SharePoint Online에 저장 되며, 원본 서비스 센터에는 시스템 및 응용 프로그램 이미지가 포함 됩니다. SharePoint Online 및 원본 서비스는 모두 버전 관리를 사용 하며 거의 실시간으로 복제 됩니다.
