---
title: Office 365의 디렉터리 동기화 끄기
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: ee5f861e-bd48-4267-83d1-a4ead4b4a00d
description: PowerShell을 사용 하 여 Office 365에 대 한 디렉터리 동기화를 해제 하는 방법을 알아봅니다.
ms.openlocfilehash: 83a01d827217db141016f622a2cb417f93f88e76
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070364"
---
# <a name="turn-off-directory-synchronization-for-office-365"></a>Office 365의 디렉터리 동기화 끄기
PowerShell을 사용 하 여 디렉터리 동기화를 해제할 수 있습니다. 그러나 디렉터리 동기화를 문제 해결 단계로 해제 하지 않는 것이 좋습니다. 디렉터리 동기화 문제를 해결 하는 데 도움이 필요한 경우 [Office 365의 디렉터리 동기화 문제 해결](fix-problems-with-directory-synchronization.md) 문서를 참조 하십시오. 
  
필요한 경우 비즈니스 제품에 대해 [고객 지원에 문의 하세요](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) .
  
## <a name="turn-off-directory-synchronization"></a>디렉터리 동기화 해제  
디렉터리 동기화를 해제 하려면
  
1. 먼저 필요한 소프트웨어를 설치 하 고 Office 365 구독에 연결 합니다. 둘 다에 대 한 지침은 [Office 365 PowerShell에 연결을](https://go.microsoft.com/fwlink/p/?LinkId=821938)참조 하세요.
    
2. MsolDirSyncEnabled을 사용 하 여 디렉터리 동기화를 사용 하지 않도록 [설정](https://go.microsoft.com/fwlink/p/?LinkId=821939) 합니다. 
    
  ```
  Set-MsolDirSyncEnabled -EnableDirSync $false
  ```