---
title: Office 365에서 서비스 거부 공격 으로부터 보호
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
description: DoS (서비스 거부) 공격의 개요
ms.openlocfilehash: 55fffccfc59f13d32cdd19930320c1df1cf58461
ms.sourcegitcommit: 55a046bdf49bf7c62ab74da73be1fd1cf6f0ad86
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/20/2019
ms.locfileid: "37067688"
---
# <a name="defend-against-denial-of-service-attacks-in-office-365"></a>Office 365에서 서비스 거부 공격 으로부터 보호

## <a name="introduction"></a>소개

Microsoft는 100 데이터 센터 보다 많은 글로벌 클라우드 인프라에 호스트 되는 200 개 이상의 클라우드 서비스에 대해 신뢰할 수 있는 인프라를 제공 합니다. 다음과 같은 다양한 알고리즘과 방법이 있습니다.

- Microsoft Azure
- Microsoft Bing
- Microsoft Dynamics 365
- Microsoft Office 365
- Microsoft OneDrive
- 시간이
- Xbox LIVE

인터넷 현재 상태와 클라우드 서비스를 제공 하는 다양 한 인터넷 속성을 가진 전역 조직으로, Microsoft는 해커 및 기타 악의적인 개인이 사용할 수 있는 광범위 한 일반 목표입니다. 클라이언트와 Microsoft 클라우드 간의 네트워크 통신 계층은 악의적인 공격의 가장 큰 목표 중 하나입니다. 실제로 Microsoft는 특정 형태의 네트워크 기반에서는 사이버 공격과 계속 해 서 지속적으로 영구적으로 사용 됩니다. 이 줄에서 Microsoft는 심층 방어 보안 원칙을 사용 하 여 클라우드 서비스 및 네트워크를 보호 합니다. 이러한 공격 으로부터 보호 하는 안정적이 고 지속적인 완화 시스템이 없는 경우 Microsoft의 클라우드 서비스는 오프 라인 상태 이며 고객이 사용할 수 없습니다.

## <a name="definition-and-symptoms-of-denial-of-service-attacks"></a>서비스 거부 공격의 정의 및 증상

네트워크 서비스를 공격할 수 있는 한 가지 방법은 네트워크 및 서버가 합법적인 사용자에 게 서비스를 거부할 수 있도록 서비스 호스트에 대 한 많은 요청을 만드는 것입니다. 이를 DoS (서비스 거부) 공격 이라고 합니다. 여러 행위자, 끝점 및/또는 벡터로 공격을 수행 하는 경우 분산 서비스 거부 (DDoS) 공격 이라고 합니다. 방법, 동기, 대상이 서로 다를 수 있지만 DoS 및 DDoS 공격은 일반적으로 인터넷 사이트 또는 서비스가 일시적으로 또는 무기한으로 정상적으로 작동 하는 것을 방지 하기 위한 노력으로 구성 됩니다.

[미국 컴퓨터 응급 준비 팀](https://www.us-cert.gov/) (미국-CERT)은 DoS 공격이 포함 될 증상을 정의 합니다.

- 네트워크 성능이 비정상적으로 느립니다 (파일을 열거나 인터넷 사이트에 액세스 하는 경우).
- 웹 사이트를 사용할 비 사용할 때
- 웹 사이트에 액세스할 수 없음
- 받은 스팸의 급격 한 증가
- 무선 또는 유선 인터넷 연결 끊기
- 웹 또는 인터넷 서비스에 대 한 장기간 액세스 권한 손실

## <a name="related-topics"></a>관련 주제

- [서비스 거부 공격에 대한 보안 핵심 원칙](office-365-core-principles-of-defense-against-dos-attacks.md)
- [Microsoft의 서비스 거부 방어 전략](office-365-microsoft-dos-defense-strategy.md)
- [서비스 거부 공격에 대해 Microsoft 클라우드 서비스 방어](office-365-defending-cloud-services-against-dos-attacks.md)
