---
title: Office 365의 테 넌 트 격리
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
description: Microsoft가 Office 365에 대해 테 넌 트 격리를 적용 하는 방법을 요약해 서 설명 합니다.
ms.openlocfilehash: a5b8a3e42aa7acc5cebe8ed21a8599fc03b5060f
ms.sourcegitcommit: 67dbbf1a5ec8cc4b10ca10f267f871f0bc045e63
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2019
ms.locfileid: "37375526"
---
# <a name="tenant-isolation-in-office-365"></a>Office 365의 테 넌 트 격리

클라우드 컴퓨팅의 주요 장점 중 하나는 다 수의 고객이 동시에 공유 공통 인프라를 확장 하는 개념입니다. 이 개념을 *다중 테 넌 시*라고 합니다. Microsoft는 클라우드 서비스의 다중 테 넌 트 아키텍처에서 엔터프라이즈 수준의 보안, 기밀성, 개인 정보, 무결성 및 가용성 표준을 지원 하는지 확인 하기 위해 지속적으로 작동 합니다.

신뢰할 수 있는 [컴퓨팅](https://www.microsoft.com/en-us/twc/default.aspx) 및 [보안 개발 수명 주기](http://www.microsoft.com/security/sdl/default.aspx)로부터 수집한 상당한 투자 및 경험을 기반으로 Microsoft 클라우드 서비스는 모든 테 넌 트가 모든 it에 취약 하다 고 가정 하는 것으로 디자인 되었습니다. 다른 테 넌 트는 한 테 넌 트에서 다른 테 넌 트의 보안 또는 서비스에 영향을 주지 않도록 하거나 다른 테 넌 트의 콘텐츠에 액세스 하지 못하도록 보안 조치를 구현 해야 합니다.

다중 테 넌 트 환경에서 테 넌 트 격리를 유지 관리 하는 두 가지 주요 목적은 다음과 같습니다.
1.  테 넌 트 간에 고객 콘텐츠 누출 또는 무단 액세스 차단 한
2.  한 테 넌 트의 작업이 다른 테 넌 트에 대 한 서비스에 악영향을 미치지 않도록 방지

고객이 Office 365 서비스 또는 응용 프로그램을 손상 시 키 지 못하도록 하거나, 다음을 비롯 하 여 다른 테 넌 트 또는 Office 365 시스템 자체의 정보에 무단으로 액세스 하는 것을 방지 하기 위해 Office 365에서 여러 보호 양식을 구현 했습니다.
- Office 365 서비스에 대 한 각 테 넌 트 내에서 고객 콘텐츠를 논리적으로 격리 하는 기능은 Azure Active Directory 권한 부여 및 역할 기반 액세스 제어를 통해 달성 됩니다.
- SharePoint Online은 저장소 수준에서 데이터 격리 메커니즘을 제공 합니다.
- Microsoft는 엄격한 물리적 보안, 배경 조사 및 다중 계층화 된 암호화 전략을 사용 하 여 고객 콘텐츠의 기밀성과 무결성을 보호 합니다. 모든 Office 365 데이터 센터에는 생체 인식 액세스 제어가 있으며, 팜 인쇄에 필요한 대부분의 경우 실제 액세스 권한을 얻게 됩니다. 또한 미국 기반 Microsoft 직원은 고용 프로세스의 일부로 표준 배경 확인을 성공적으로 완료 하는 데 필요 합니다. Office 365의 관리 액세스에 사용 되는 컨트롤에 대 한 자세한 내용은 [office 365 관리 액세스 제어](office-365-administrative-access-controls-overview.md)를 참조 하세요.
- Office 365에서는 BitLocker, 파일 단위 암호화, TLS (보안 계층 보안) 및 IPsec (인터넷 프로토콜 보안)을 포함 하 여 rest 및 전송 중에 고객 콘텐츠를 암호화 하는 서비스 쪽 기술을 사용 합니다. Office 365의 암호화에 대 한 자세한 내용은 [Data Encryption 기술을 office 365에서](https://docs.microsoft.com/microsoft-365/compliance/office-365-encryption-in-the-microsoft-cloud-overview)참조 하십시오.

위에 나열 된 보호를 함께 사용 하면 물리적 격리 만으로 제공 되는 것과 동등한 위협 방지 및 완화를 제공 하는 강력한 논리적 격리 컨트롤이 제공 됩니다.

## <a name="related-links"></a>관련 링크
- [Azure Active Directory에서 격리 및 액세스 제어](office-365-isolation-in-azure-active-directory.md)
- [Office Graph 및 Delve에서 테넌트 격리](office-365-isolation-in-graph-and-delve.md)
- [Office 365 검색에서 테넌트 격리](office-365-isolation-in-office-365-search.md)
- [Office 365 비디오에서 테넌트 격리](office-365-isolation-in-office-365-video.md)
- [리소스 제한 사항](office-365-resource-limits.md)
- [테넌트 경계 모니터링 및 테스트](office-365-monitoring-and-testing.md)
- [Office 365에서 격리 및 액세스 제어](office-365-isolation-in-office-365.md)
