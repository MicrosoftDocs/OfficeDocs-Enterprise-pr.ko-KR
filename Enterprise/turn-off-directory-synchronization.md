---
title: Microsoft 365에 대 한 디렉터리 동기화 해제
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: ee5f861e-bd48-4267-83d1-a4ead4b4a00d
description: PowerShell을 사용 하 여 Microsoft 365에 대 한 디렉터리 동기화를 해제 하는 방법을 알아봅니다.
ms.openlocfilehash: 1e3e26a262c112c05fe22cda2dbe3f14efb61f87
ms.sourcegitcommit: c1a1b028195342affe0f3367db4e79c42429582a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/23/2020
ms.locfileid: "45387711"
---
# <a name="turn-off-directory-synchronization-for-microsoft-365"></a>Microsoft 365에 대 한 디렉터리 동기화 해제
PowerShell을 사용 하 여 디렉터리 동기화를 해제할 수 있습니다. 그러나 디렉터리 동기화를 문제 해결 단계로 해제 하지 않는 것이 좋습니다. 디렉터리 동기화 문제를 해결 하는 데 도움이 필요한 경우 [Microsoft 365의 디렉터리 동기화 문제 해결](fix-problems-with-directory-synchronization.md) 문서를 참조 하십시오. 
  
필요한 경우 비즈니스 제품에 대해 [고객 지원에 문의 하세요](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) .
  
## <a name="turn-off-directory-synchronization"></a>디렉터리 동기화 끄기  
디렉터리 동기화를 해제 하려면
  
1. 먼저 필요한 소프트웨어를 설치 하 고 Microsoft 365 구독에 연결 합니다. 자세한 내용은 [Windows PowerShell 용 Microsoft Azure Active Directory 모듈을 사용 하 여 연결](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)을 참조 하십시오.
    
2. MsolDirSyncEnabled을 사용 하 여 디렉터리 동기화를 사용 하지 않도록 [설정](https://go.microsoft.com/fwlink/p/?LinkId=821939) 합니다. 
    
  ```powershell
  Set-MsolDirSyncEnabled -EnableDirSync $false
  ```

>[!Note]
>이 명령을 사용 하는 경우에는 72 시간을 기다린 후 디렉터리 동기화를 다시 설정 해야 합니다.
>
 
