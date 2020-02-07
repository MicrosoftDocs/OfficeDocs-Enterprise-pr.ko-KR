---
title: Office 365 DoS 방어 전략
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: None
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
f1.keywords:
- NOCSH
description: DoS (서비스 거부) 공격에 대 한 Microsoft 방어 전략 개요
ms.openlocfilehash: c30e8e5c91ead81ceda9cfaeb4ef6b17c9addc9f
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844389"
---
# <a name="office-365-denial-of-service-defense-strategy"></a>Office 365 서비스 거부 방어 전략

네트워크 기반 DoS (서비스 거부) 공격을 방어 하기 위한 Microsoft의 전략은 규모와 전역 공간으로 인해 고유 합니다. 이 확장을 통해 Microsoft는 조직, 공급자 또는 고객 조직이 일치 시킬 수 있는 전략 및 기법을 활용 합니다. DoS 전략의 세밀는 글로벌 현재 상태입니다. Microsoft는 전 세계에서 인터넷 공급자, 피어 링 공급자 (공개 및 개인) 및 사설 기업에 관여 합니다. 이를 통해 Microsoft는 인터넷에 심각한 정보를 제공 하 고 Microsoft에서 큰 영역을 통해 공격을 수행할 수 있습니다.

이러한 고유한 특성이 제공 되는 경우 Microsoft는 대규모 기업에서 사용 하는 것과는 다른 검색 및 완화 프로세스를 사용 합니다. 이 전략은 다양 한 네트워크에 지를 통한 검색 및 전역 분산 완화가 분리 된 방식을 기반으로 합니다. 대부분의 기업에서는 타사 솔루션을 사용 하 여 edge에서 공격을 감지 하 고 완화 합니다. Microsoft의 edge 용량이 증가 함에 따라 개별 또는 특정 모서리에 대 한 모든 공격의 중요성은 낮습니다. 이러한 고유한 구성 때문에 Microsoft는 검색 및 완화 구성 요소를 분리 했습니다. Microsoft는 전체 계층 검색 시스템을 배포 하 여 해당 하는 위치에 가까운 공격을 감지 하 고,에 지에 전역 완화를 유지 합니다. 이 전략을 사용 하면 여러 동시 공격을 처리할 수 있습니다.

DoS 공격에 대해 Microsoft가 사용 하는 가장 효율적인 저렴 한 방어 중 하나는 서비스 공격 표면을 줄이는 것입니다. 원치 않는 트래픽은 데이터를 분석, 처리 및 삭제 하는 대신 네트워크에 지에서 삭제 됩니다.

공용 네트워크와의 인터페이스에서 Microsoft는 방화벽, 네트워크 주소 변환 및 IP 필터링 기능에 특수 용도의 보안 장치를 사용 합니다. Microsoft는 또한 글로벌 동일한 ECMP (다중 경로) 라우팅을 사용 합니다. 전역 ECMP 라우팅은 서비스에 연결할 수 있는 여러 전역 경로가 있는지 확인 하기 위한 네트워크 프레임 워크입니다. 이러한 여러 경로를 사용 하 여 서비스에 대 한 공격은 공격이 시작 된 지역으로 제한 됩니다. 최종 사용자가 해당 지역의 서비스에 연결 하기 위해 다른 경로를 사용 하는 경우에는 다른 지역에서이 공격의 영향을 받지 않습니다. 또한 Microsoft는 흐름 데이터, 성능 메트릭 및 기타 정보를 사용 하는 내부 DoS 상관 관계 및 검색 시스템을 개발 했습니다. 이는 microsoft Azure의 스케일 클라우드 서비스 이며,이는 마이크로소프트 네트워크 및 서비스의 여러 지점에서 수집한 데이터를 분석 하는 데 사용할 수 있습니다. 작업 부하를 수행 하는 DoS 인시던트 대응 팀은 팀 전체의 역할과 책임, 에스컬레이션 기준 및 다양 한 팀을 사용 하 고 인시던트를 처리 하기 위한 프로토콜을 식별 합니다. 이러한 솔루션은 DoS 공격 으로부터 네트워크 기반 보호를 제공 합니다.

마지막으로 클라우드 기반 워크 로드는 해당 프로토콜에 따라 최적화 된 임계값을 사용 하 여 구성 되며 해당 작업을 고유 하 게 보호 하기 위해 대역폭 사용량이 필요 합니다.
