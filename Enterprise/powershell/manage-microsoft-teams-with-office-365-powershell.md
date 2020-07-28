---
title: PowerShell을 사용 하 여 Microsoft 팀 관리
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: ff93a341-6f0f-4f06-9690-726052e1be64
description: '요약: PowerShell을 사용 하 여 Microsoft 팀을 관리 합니다.'
ms.openlocfilehash: 8958c6ec6f0c17c21461cbee4cb1a6441ceed8d6
ms.sourcegitcommit: 132c97bd5e0dbe469da64356ace5084b71419cea
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/28/2020
ms.locfileid: "45429201"
---
# <a name="manage-microsoft-teams-with-powershell"></a>PowerShell을 사용 하 여 Microsoft 팀 관리

*이 문서는 Microsoft 365 Enterprise와 Office 365 Enterprise에 모두 적용됩니다.*

PowerShell을 사용 하 여 Microsoft 팀을 관리할 수 있습니다.
  
먼저 [Microsoft 팀 모듈](https://www.powershellgallery.com/packages/MicrosoftTeams/)을 설치 합니다.
    
## <a name="sign-in-with-a-user-name-and-password"></a>사용자 이름 및 암호를 사용 하 여 로그인

Office 365 전 세계 (+ GCC) 클라우드의 경우:

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred
```

Office 365 U.S. 정부 DoD 클라우드의 경우: 

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred -TeamsEnvironmentName TeamsDOD
```

Office 365 미국 정부 GCC High 클라우드의 경우:

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred -TeamsEnvironmentName TeamsGCCH
```

## <a name="sign-in-with-multi-factor-authentication-mfa"></a>MFA (다단계 인증)를 사용 하 여 로그인

Office 365 전 세계 (+ GCC) 클라우드의 경우:

```powershell
Connect-MicrosoftTeams
```

Office 365 U.S. 정부 DoD 클라우드의 경우: 

```powershell
Connect-MicrosoftTeams -TeamsEnvironmentName TeamsDOD
```

Office 365 미국 정부 GCC High 클라우드의 경우:

```powershell
Connect-MicrosoftTeams -TeamsEnvironmentName TeamsGCCH
```

## <a name="disconnect-from-microsoft-teams"></a>Microsoft 팀에서 연결 끊기

다음 명령을 사용하세요.

```powershell
Disconnect-MicrosoftTeams
```


## <a name="see-also"></a>참고 항목

[팀 PowerShell 개요](https://docs.microsoft.com/microsoftteams/teams-powershell-overview)
  
[PowerShell로 Microsoft 365 관리](manage-office-365-with-office-365-powershell.md)
  
[Microsoft 365 용 PowerShell 시작](getting-started-with-office-365-powershell.md)

