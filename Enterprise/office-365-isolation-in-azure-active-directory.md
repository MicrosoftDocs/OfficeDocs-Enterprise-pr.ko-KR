---
title: Azure Active Directory의 Office 365 격리 및 액세스 제어
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
description: '요약: Azure Active Directory 내에서 격리 및 액세스 제어 작업을 수행 하는 방법을 설명 합니다.'
ms.openlocfilehash: ac8ea9cf0550517f4d4d8c6eac10812700bb668b
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844469"
---
# <a name="isolation-and-access-control-in-azure-active-directory"></a>Azure Active Directory에서 격리 및 액세스 제어

Azure Active Directory는 논리적 데이터 격리를 통해 고도로 안전한 방식으로 여러 테 넌 트를 호스트 하도록 디자인 되었습니다. Azure Active Directory에 대 한 액세스는 인증 계층에 의해 제어 됩니다. Azure Active Directory는 사용자의 콘텐츠를 보호 하기 위해 테 넌 트 컨테이너를 보안 경계로 사용 하는 고객을 격리 하 여 동료의 콘텐츠 액세스 또는 손상을 차단 합니다. Azure Active Directory의 인증 계층에서 다음 세 가지 검사를 수행 합니다.

- 사용자가 Azure Active Directory 테 넌 트에 액세스할 수 있는지 여부
- 이 테 넌 트에서 데이터 액세스에 대 한 보안 주체를 사용할 수 있나요?
- 이 테 넌 트의 사용자 역할이 요청 된 데이터 액세스 유형에 대해 승인 되었습니까?

적절 한 인증 및 토큰 또는 인증서 없이는 응용 프로그램, 사용자, 서버 또는 서비스가 Azure Active Directory에 액세스할 수 없습니다. 적절 한 자격 증명이 없으면 요청이 거부 됩니다.

실제로 Azure Active Directory는 자체 보호 된 컨테이너의 각 테 넌 트를 호스트 하며, 해당 컨테이너에 대 한 정책 및 사용 권한을 테 넌 트에서 단독으로 소유 하 고 관리 합니다.
 
![Azure 컨테이너](media/office-365-isolation-azure-container.png)

테 넌 트 컨테이너의 개념은 모든 계층의 디렉터리 서비스에서 포털부터 영구 저장소까지 깊이 있는 방식으로 세분화 됩니다. 여러 Azure Active Directory 테 넌 트 메타 데이터가 동일한 실제 디스크에 저장 된 경우에도 디렉터리 서비스에서 정의 하는 것 외의 컨테이너 사이에는 아무런 관계도 없으며이는 차례로 테 넌 트 관리자에 게 지시 됩니다. 먼저 인증 계층을 거치지 않고는 요청 하는 응용 프로그램 또는 서비스에서 Azure Active Directory 저장소에 직접 연결할 수 없습니다.

아래 예에서, Contoso와 Fabrikam은 모두 별도의 전용 컨테이너를 가지 지만, 이러한 컨테이너는 서버 및 저장소와 같은 동일한 기본 인프라를 공유할 수 있더라도 서로 분리 되 고 서로 격리 되며,이에 따라 제어 됩니다. 권한 부여 및 액세스 제어 계층
 
![Azure 전용 컨테이너](media/office-365-isolation-azure-dedicated-containers.png)

또한 Azure Active Directory 내에서 실행할 수 있는 응용 프로그램 구성 요소는 없으며, 한 테 넌 트에서 다른 테 넌 트의 무결성을 강제로 침해 하거나, 다른 테 넌 트의 암호화 키에 액세스 하거나, 서버에서 원시 데이터를 읽을 수 없습니다.

기본적으로 Azure Active Directory에서는 다른 테 넌 트의 id에서 실행 되는 모든 작업을 허용 하지 않습니다. 각 테 넌 트는 클레임 기반 액세스 제어를 통해 Azure Active Directory 내에서 논리적으로 격리 됩니다. 디렉터리 데이터의 읽기 및 쓰기는 테 넌 트 컨테이너로 범위가 지정 되 고, 내부 추상화 계층 및 RBAC (역할 기반 액세스 제어) 계층으로 제어 되며,이를 통해 테 넌 트가 보안 경계로 적용 됩니다. 이러한 계층은 모든 디렉터리 데이터 액세스 요청을 처리 하며, Office 365의 모든 액세스 요청은 위의 논리에 의해 policed입니다.

Azure Active Directory에 북미, 미국 정부, 유럽 연합, 독일 및 World Wide partitions가 포함 되어 있습니다. 테 넌 트가 단일 파티션에 있고, 파티션에 여러 테 넌 트가 포함 될 수 있습니다. 파티션 정보가 사용자 로부터 벗어나게 됩니다. 지정 된 파티션 (it 내의 모든 테 넌 트 포함)은 여러 데이터 센터로 복제 됩니다. 테 넌 트의 파티션은 테 넌 트의 속성 (예: 국가 코드)을 기준으로 선택 됩니다. 각 파티션의 비밀 및 기타 중요 한 정보는 전용 키로 암호화 됩니다. 새 파티션을 만들 때 키가 자동으로 생성 됩니다.

Azure Active Directory 시스템 기능은 각 사용자 세션에 대 한 고유한 인스턴스입니다. 또한 Azure Active Directory는 암호화 기술을 사용 하 여 무단 및 원치 않는 정보 전송을 방지 하기 위해 네트워크 수준에서 공유 시스템 리소스의 격리를 제공 합니다.
