---
title: Microsoft 365 엔지니어링을 위한 microsoft 365 내부 로깅
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
description: 이 문서에서는 Microsoft 365 엔지니어링 팀의 내부 로깅이 작동 하는 방식에 대 한 설명을 찾습니다.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: e7c5c32d1ea0704f8f56a4af6e6dd85f73f9c2df
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606554"
---
# <a name="internal-logging-for-microsoft-365-engineering"></a>Microsoft 365 엔지니어링에 대 한 내부 로깅

고객에 게 제공 되는 이벤트 및 로그 데이터 뿐 아니라 Microsoft 365 엔지니어가 제공 하는 내부 로그 데이터 수집 시스템도 있습니다. 다양 한 유형의 로그 데이터가 Microsoft 365 서버에서 Cosmos 라는 내부 대규모 데이터 컴퓨팅 서비스로 업로드 됩니다. 각 서비스 팀은 집계 및 분석을 위해 각 서버의 감사 로그를 Cosmos 데이터베이스에 업로드 합니다. 이 데이터 전송은 ODL (Office Data Loader) 라는 전용 자동화 도구를 사용 하 여 특별히 승인 된 포트 및 프로토콜에 대해 FIPS 140-2 유효성 검사 TLS 연결을 통해 수행 됩니다. Microsoft 365에서 감사 레코드를 수집 하 고 처리 하는 데 사용 되는 도구는 원본 감사 레코드 콘텐츠 또는 시간 순서에 영구 또는 되돌릴 수 없는 변경을 허용 하지 않습니다.

서비스 팀에서는 Cosmos을 중앙 리포지토리로 사용 하 여 응용 프로그램 사용 현황 분석을 수행 하 고, 시스템 및 운영 성과를 측정 하며, 문제 또는 보안 문제를 나타내는 abnormalities 및 패턴을 찾습니다. 각 서비스 팀은 분석 하려는 대상에 따라 다음을 포함 하는 Cosmos에 로그 초기 계획을 업로드 합니다.

- 이벤트 로그
- AppLocker 로그
- 성능 데이터
- System Center data
- 통화 정보 기록
- 경력 데이터 품질
- IIS 웹 서버 로그
- SQL Server 로그
- Syslog 데이터
- 보안 감사 로그

Cosmos에 데이터를 업로드 하기 전에 ODL 응용 프로그램은 스크러빙 서비스를 사용 하 여 테 넌 트 정보, 최종 사용자 식별 정보 등의 고객 데이터가 포함 된 모든 필드를 해시 값으로 바꿉니다. 익명 및 해시 된 로그가 다시 작성 된 다음 Cosmos에 업로드 됩니다. 서비스 팀은 상관 관계, 경고 및 보고를 위해 Cosmos에서 데이터에 대해 범위 지정 쿼리를 실행 합니다. Cosmos의 감사 로그 데이터 보존 기간은 서비스 팀에 따라 결정 됩니다. 대부분의 감사 로그 데이터는 보안 인시던트 조사를 지원 하 고 규정 보존 요구 사항을 충족 하기 위해 90 일 이상 보존 됩니다.

Cosmos에 저장 된 Microsoft 365 데이터에 대 한 액세스 권한이 권한 있는 담당자 에게만 제한 됩니다. Microsoft는 감사 기능을 담당 하는 서비스 팀 구성원의 제한 된 하위 집합으로 감사 기능을 관리할 수 있도록 제한 합니다. 이러한 팀 구성원은 Cosmos에서 데이터를 수정 하거나 삭제할 수 없으며 Cosmos에 대 한 로깅 메커니즘에 대 한 모든 변경 내용이 기록 및 감사 됩니다.

각 서비스 팀은 특정 분석을 수행 하도록 특정 응용 프로그램에 부여 하 여 분석을 위해 로그 데이터에 액세스 합니다. 예를 들어 Microsoft 365 보안 팀은 Cosmos의 데이터를 사용 하 여 Microsoft 365 프로덕션 환경에 있는 의심 스러운 작업을 수행할 수 있는 문제를 해결 하 고 문제를 해결 하 고 해당 보고서를 생성 합니다. 이 데이터의 보고서는 취약성을 수정 하 고 서비스의 전반적인 성능을 향상 시키는 데 사용 됩니다. 특정 경고나 보고서에 대해 자세히 조사 해야 하는 경우 서비스 담당자는 해당 데이터를 Microsoft 365 서비스로 다시 가져오도록 요청할 수 있습니다. Cosmos에서 가져오는 특정 로그는 암호화 되 고 서비스 직원에 게 암호 해독 키에 대 한 액세스 권한이 없기 때문에, 대상 로그는 인증 된 서비스 담당자에 게 범위가 지정 된 결과를 반환 하는 암호 해독 서비스를 통해 프로그래밍 방식으로 전달 됩니다. 이 연습에서 발견 된 모든 취약성은 Microsoft의 표준 보안 인시던트 관리 채널을 사용 하 여 보고 되 고 제기 됩니다.
