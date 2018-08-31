---
title: Office 365의 디렉터리 동기화 해제
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: ee5f861e-bd48-4267-83d1-a4ead4b4a00d
description: Office 365에 대 한 디렉터리 동기화를 해제 하려면 PowerShell을 사용 하는 방법에 알아봅니다.
ms.openlocfilehash: f47209dd8b6be47b7ae7a4b63a9fae38c5cb498f
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542143"
---
# <a name="turn-off-directory-synchronization-for-office-365"></a>Office 365의 디렉터리 동기화 해제
디렉터리 동기화를 해제 하려면 PowerShell을 사용할 수 있습니다. 그러나으로 문제해결 단계에 따라 디렉터리 동기화를 해제 하는 것은 좋지 않습니다. 디렉터리 동기화 문제를 해결 하는 도움이 필요 하면, [Office 365에 대 한 디렉터리 동기화를 통해 수정 문제](fix-problems-with-directory-synchronization.md) 문서를 참조 합니다. 
  
필요한 경우 비즈니스 제품에 대 한 [대화 상대를 지원](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) 합니다.
  
## <a name="turn-off-directory-synchronization"></a>디렉터리 동기화를 해제  
디렉터리 동기화 해제 하려면:
  
1. 먼저, 필요한 소프트웨어를 설치 하 고 Office 365 구독에 연결 합니다. 모두에 대 한 지침을 [Office 365 powershell 연결](https://go.microsoft.com/fwlink/p/?LinkId=821938)을 참조 하십시오.
    
2. [Set-msoldirsyncenabled](https://go.microsoft.com/fwlink/p/?LinkId=821939) 를 사용 하 여 디렉터리 동기화를 사용 하지 않도록 설정 합니다. 
    
  ```
  Set-MsolDirSyncEnabled -EnableDirSync $false
  ```