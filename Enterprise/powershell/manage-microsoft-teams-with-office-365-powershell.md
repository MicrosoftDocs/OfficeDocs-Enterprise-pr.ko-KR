---
title: Office 365 PowerShell을 사용 하 여 Microsoft 팀 관리
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/12/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: ff93a341-6f0f-4f06-9690-726052e1be64
description: '요약: Office 365 PowerShell을 사용 하 여 Microsoft 팀을 관리 합니다.'
ms.openlocfilehash: 0f15d71558ddb5166090b067da06e0a6321a2b99
ms.sourcegitcommit: dce58576a61f2c8efba98657b3f6e277a12a3a7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/12/2020
ms.locfileid: "44209128"
---
# <a name="manage-microsoft-teams-with-office-365-powershell"></a><span data-ttu-id="ae464-103">Office 365 PowerShell을 사용 하 여 Microsoft 팀 관리</span><span class="sxs-lookup"><span data-stu-id="ae464-103">Manage Microsoft Teams with Office 365 PowerShell</span></span>

<span data-ttu-id="ae464-104">Office 365 PowerShell을 사용 하 여 Microsoft 팀을 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae464-104">You can manage Microsoft Teams with Office 365 PowerShell.</span></span>
  
<span data-ttu-id="ae464-105">먼저 [Microsoft 팀 모듈](https://www.powershellgallery.com/packages/MicrosoftTeams/)을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae464-105">First, install the [Microsoft Teams module](https://www.powershellgallery.com/packages/MicrosoftTeams/).</span></span>
    
## <a name="sign-in-with-a-user-name-and-password"></a><span data-ttu-id="ae464-106">사용자 이름 및 암호를 사용 하 여 로그인</span><span class="sxs-lookup"><span data-stu-id="ae464-106">Sign in with a user name and password</span></span>

<span data-ttu-id="ae464-107">Office 365 전 세계 (+ GCC) 클라우드의 경우:</span><span class="sxs-lookup"><span data-stu-id="ae464-107">For the Office 365 Worldwide (+GCC) cloud:</span></span>

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred
```

<span data-ttu-id="ae464-108">Office 365 U.S. 정부 DoD 클라우드의 경우:</span><span class="sxs-lookup"><span data-stu-id="ae464-108">For the Office 365 U.S. Government DoD cloud:</span></span> 

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred -TeamsEnvironmentName TeamsDOD
```

<span data-ttu-id="ae464-109">Office 365 미국 정부 GCC High 클라우드의 경우:</span><span class="sxs-lookup"><span data-stu-id="ae464-109">For the Office 365 U.S. Government GCC High cloud:</span></span>

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred -TeamsEnvironmentName TeamsGCCH
```

## <a name="sign-in-with-multi-factor-authentication-mfa"></a><span data-ttu-id="ae464-110">MFA (다단계 인증)를 사용 하 여 로그인</span><span class="sxs-lookup"><span data-stu-id="ae464-110">Sign in with multi-factor authentication (MFA)</span></span>

<span data-ttu-id="ae464-111">Office 365 전 세계 (+ GCC) 클라우드의 경우:</span><span class="sxs-lookup"><span data-stu-id="ae464-111">For the Office 365 Worldwide (+GCC) cloud:</span></span>

```powershell
Connect-MicrosoftTeams
```

<span data-ttu-id="ae464-112">Office 365 U.S. 정부 DoD 클라우드의 경우:</span><span class="sxs-lookup"><span data-stu-id="ae464-112">For the Office 365 U.S. Government DoD cloud:</span></span> 

```powershell
Connect-MicrosoftTeams -TeamsEnvironmentName TeamsDOD
```

<span data-ttu-id="ae464-113">Office 365 미국 정부 GCC High 클라우드의 경우:</span><span class="sxs-lookup"><span data-stu-id="ae464-113">For the Office 365 U.S. Government GCC High cloud:</span></span>

```powershell
Connect-MicrosoftTeams -TeamsEnvironmentName TeamsGCCH
```

## <a name="disconnect-from-microsoft-teams"></a><span data-ttu-id="ae464-114">Microsoft 팀에서 연결 끊기</span><span class="sxs-lookup"><span data-stu-id="ae464-114">Disconnect from Microsoft Teams</span></span>

<span data-ttu-id="ae464-115">다음 명령을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="ae464-115">Use this command:</span></span>

```powershell
Disconnect-MicrosoftTeams
```


## <a name="see-also"></a><span data-ttu-id="ae464-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ae464-116">See also</span></span>

[<span data-ttu-id="ae464-117">팀 PowerShell 개요</span><span class="sxs-lookup"><span data-stu-id="ae464-117">Teams PowerShell Overview</span></span>](https://docs.microsoft.com/microsoftteams/teams-powershell-overview)
  
[<span data-ttu-id="ae464-118">Office 365 PowerShell 사용한 Office 365 관리</span><span class="sxs-lookup"><span data-stu-id="ae464-118">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="ae464-119">Office 365 PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="ae464-119">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

