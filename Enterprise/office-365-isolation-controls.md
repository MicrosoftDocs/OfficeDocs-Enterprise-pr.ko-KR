---
title: Office 365 격리 컨트롤
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
description: '요약: Office 365 내의 격리 컨트롤에 대 한 설명입니다.'
ms.openlocfilehash: 87317d753198b50ce360640c94f042adf27ed06e
ms.sourcegitcommit: 55a046bdf49bf7c62ab74da73be1fd1cf6f0ad86
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/20/2019
ms.locfileid: "37067667"
---
# <a name="office-365-isolation-controls"></a>Office 365 격리 컨트롤 

Microsoft는 Office 365의 다중 테 넌 트 아키텍처에서 엔터프라이즈 수준의 보안, 기밀성, 개인 정보, 무결성, 로컬, 국제 및 가용성 [표준을](https://www.microsoft.com/TrustCenter/Compliance?service=Office#Icons)지원 하는지 확인 하기 위해 계속 작동 합니다. Microsoft에서 제공 하는 서비스의 확장 및 범위를 통해 상당한 사람의 상호 작용을 통해 Office 365을 관리 하기 어렵고 경제적으로 관리할 수 없습니다. Office 365 서비스는 여러 전역 분산 데이터 센터를 통해 제공 되며, 각 작업은 사용자의 터치 나 고객 콘텐츠에 대 한 액세스를 필요로 하는 소수의 작업과 함께 자동화 됩니다. 직원 들은 자동화 된 도구 및 높은 보안 원격 액세스를 사용 하 여 이러한 서비스와 데이터 센터를 지원 합니다. 대규모 서비스가 Office 365에서 운영 되는 방식에 대 한 자세한 내용은 [배후에서 IT 전문가를 위한 Office 365의 모습](https://channel9.msdn.com/Events/SharePoint-Conference/2014/SPC202)을 참조 하십시오.

Office 365은 중요 한 비즈니스 기능을 제공 하 고 전체 Office 365 환경에 기여 하는 여러 서비스로 구성 됩니다. 이러한 각 서비스는 독립적 이며 서로 통합 되도록 설계 되었습니다.

Office 365는 다음과 같은 원칙을 사용 하 여 디자인 되었습니다.

 - ** [서비스 지향 아키텍처](https://msdn.microsoft.com/library/aa480021.aspx):** 잘 정의 된 비즈니스 기능을 제공 하는 상호 운용 가능한 서비스 형태의 소프트웨어를 디자인 하 고 개발 합니다.
 - **[운영 보안 보증](http://www.microsoft.com/download/details.aspx?id=40872):** Microsoft 보안 [개발 수명 주기](https://www.microsoft.com/sdl/default.aspx)를 포함 하 여 microsoft에 고유 하 게 제공 되는 다양 한 기능을 통해 얻은 정보를 통합 하는 프레임 워크입니다. [ ](https://technet.microsoft.com/library/dn440717.aspx)Cybersecurity 위협 가로에 대 한 응답 센터 및 심층 인식

Office 365 서비스는 서로 간에 작동 하며, 서로 독립적으로 배포 되 고 운영 될 수 있도록 설계 및 구현 됩니다. Microsoft segregates 의무 및 책임 영역으로, 무단으로 수정 되거나 조직의 자산의 오용에 대 한 영업 기회를 줄이기 위한 Office 365 Office 365 팀은 포괄적인 역할 기반 액세스 제어 메커니즘의 일부로 역할을 정의 합니다.

## <a name="customer-content-isolation"></a>고객 콘텐츠 격리

테 넌 트의 모든 고객 콘텐츠는 다른 테 넌 트에서 격리 되며, Office 365의 관리에서 사용 되는 운영 및 시스템 데이터와는 다릅니다. Office 365 서비스 또는 응용 프로그램의 손상 위험을 최소화 하기 위해 여러 형태의 보호를 Office 365에서 구현 했습니다. 또한 여러 보호 양식을 사용 하면 테 넌 트 또는 Office 365 시스템 자체의 정보에 대 한 무단 액세스를 방지할 수 있습니다.

Microsoft가 Office 365 내의 테 넌 트 데이터의 논리적 격리를 구현 하는 방법에 대 한 자세한 내용은 [office 365에서 테 넌 트 격리](office-365-tenant-isolation-overview.md)를 참조 하세요
