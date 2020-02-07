---
title: Office 365 리소스 제한
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
description: '요약: Office 365 내의 다양 한 응용 프로그램에 대 한 리소스 제한에 대해 설명 합니다.'
ms.openlocfilehash: 112d910ae724ad01629aaef5a8e2e1756ceb8ecf
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844319"
---
# <a name="resource-limits"></a>리소스 제한 사항

리소스 제한은 할당량 (제한) 및 제한을 사용 하 여 적용 됩니다. Azure Active Directory 및 개별 Office 365 서비스는 둘 다 사용 합니다. 제한은 새로운 기능이 추가 됨에 따라 서비스에 따라 달라 지 며 시간이 지나면서 변경 됩니다. 다양 한 서비스에 대 한 현재 제한 사항에 대 한 자세한 내용은 다음 항목을 참조 하십시오.

- [Azure Active Directory 서비스 제한 및 제한 사항](https://msdn.microsoft.com/library/azure/dn764971.aspx)
- [Exchange Online 제한](https://technet.microsoft.com/library/exchange-online-limits.aspx)
- [Exchange Online Protection 제한](https://technet.microsoft.com/library/exchange-online-protection-limits.aspx)
- [SharePoint Online 소프트웨어 경계 및 제한 사항](https://support.office.com/article/SharePoint-Online-software-boundaries-and-limits-8F34FF47-B749-408B-ABC0-B605E1F6D498)
- [비즈니스용 Skype 제한](https://technet.microsoft.com/library/skype-for-business-online-limits.aspx)
- [Yammer REST API 및 속도 제한](https://developer.yammer.com/docs/rest-api-rate-limits)
- [Sway의 파일 크기 제한](https://support.office.com/article/File-size-limits-in-Sway-4db21bc6-b42b-499f-9272-66e089db109f)

이러한 제한 외에도 다양 한 제한 메커니즘이 Azure Active Directory 및 Office 365에서 사용 됩니다. Microsoft 데이터 센터의 네트워크 리소스가 서비스를 사용 하는 광범위 한 고객 집합에 맞게 최적화 되어 있는 경우 서비스 내의 제한이 특히 중요 합니다. 제한 메커니즘은 다음과 같습니다.

- Azure Active Directory 및 Office 365 기능 사용자 수준 제한은 단일 사용자가 수행할 수 있는 트랜잭션 수 또는 동시 통화 (스크립트나 코드)를 제한 합니다.
- 기본 PowerShell 제한 정책이 테 넌 트를 만들 때 각 테 넌 트에 할당 됩니다. 이러한 설정은 단일 관리자가 열 수 있는 동시 PowerShell 세션의 최대 수와 같은 다른 항목에 영향을 줍니다.
- 각 Exchange Online 고객에 게 EWS 클라이언트 작업에 맞게 조정 된 기본 EWS (Exchange 웹 서비스) 정책 및 모든 Outlook 클라이언트에 적용 되는 제한 사항이 있습니다.
