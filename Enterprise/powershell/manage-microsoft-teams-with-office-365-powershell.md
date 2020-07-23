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
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230614"
---
# <a name="manage-microsoft-teams-with-powershell"></a><span data-ttu-id="6a050-103">PowerShell을 사용 하 여 Microsoft 팀 관리</span><span class="sxs-lookup"><span data-stu-id="6a050-103">Manage Microsoft Teams with PowerShell</span></span>

<span data-ttu-id="6a050-104">*이 문서는 Microsoft 365 Enterprise 및 Office 365 Enterprise에 모두 적용 됩니다.*</span><span class="sxs-lookup"><span data-stu-id="6a050-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="6a050-105">PowerShell을 사용 하 여 Microsoft 팀을 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a050-105">You can manage Microsoft Teams with PowerShell.</span></span>
  
<span data-ttu-id="6a050-106">먼저 [Microsoft 팀 모듈](https://www.powershellgallery.com/packages/MicrosoftTeams/)을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a050-106">First, install the [Microsoft Teams module](https://www.powershellgallery.com/packages/MicrosoftTeams/).</span></span>
    
## <a name="sign-in-with-a-user-name-and-password"></a><span data-ttu-id="6a050-107">사용자 이름 및 암호를 사용 하 여 로그인</span><span class="sxs-lookup"><span data-stu-id="6a050-107">Sign in with a user name and password</span></span>

<span data-ttu-id="6a050-108">Office 365 전 세계 (+ GCC) 클라우드의 경우:</span><span class="sxs-lookup"><span data-stu-id="6a050-108">For the Office 365 Worldwide (+GCC) cloud:</span></span>

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred
```

<span data-ttu-id="6a050-109">Office 365 U.S. 정부 DoD 클라우드의 경우:</span><span class="sxs-lookup"><span data-stu-id="6a050-109">For the Office 365 U.S. Government DoD cloud:</span></span> 

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred -TeamsEnvironmentName TeamsDOD
```

<span data-ttu-id="6a050-110">Office 365 미국 정부 GCC High 클라우드의 경우:</span><span class="sxs-lookup"><span data-stu-id="6a050-110">For the Office 365 U.S. Government GCC High cloud:</span></span>

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred -TeamsEnvironmentName TeamsGCCH
```

## <a name="sign-in-with-multi-factor-authentication-mfa"></a><span data-ttu-id="6a050-111">MFA (다단계 인증)를 사용 하 여 로그인</span><span class="sxs-lookup"><span data-stu-id="6a050-111">Sign in with multi-factor authentication (MFA)</span></span>

<span data-ttu-id="6a050-112">Office 365 전 세계 (+ GCC) 클라우드의 경우:</span><span class="sxs-lookup"><span data-stu-id="6a050-112">For the Office 365 Worldwide (+GCC) cloud:</span></span>

```powershell
Connect-MicrosoftTeams
```

<span data-ttu-id="6a050-113">Office 365 U.S. 정부 DoD 클라우드의 경우:</span><span class="sxs-lookup"><span data-stu-id="6a050-113">For the Office 365 U.S. Government DoD cloud:</span></span> 

```powershell
Connect-MicrosoftTeams -TeamsEnvironmentName TeamsDOD
```

<span data-ttu-id="6a050-114">Office 365 미국 정부 GCC High 클라우드의 경우:</span><span class="sxs-lookup"><span data-stu-id="6a050-114">For the Office 365 U.S. Government GCC High cloud:</span></span>

```powershell
Connect-MicrosoftTeams -TeamsEnvironmentName TeamsGCCH
```

## <a name="disconnect-from-microsoft-teams"></a><span data-ttu-id="6a050-115">Microsoft 팀에서 연결 끊기</span><span class="sxs-lookup"><span data-stu-id="6a050-115">Disconnect from Microsoft Teams</span></span>

<span data-ttu-id="6a050-116">다음 명령을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="6a050-116">Use this command:</span></span>

```powershell
Disconnect-MicrosoftTeams
```


## <a name="see-also"></a><span data-ttu-id="6a050-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6a050-117">See also</span></span>

[<span data-ttu-id="6a050-118">팀 PowerShell 개요</span><span class="sxs-lookup"><span data-stu-id="6a050-118">Teams PowerShell Overview</span></span>](https://docs.microsoft.com/microsoftteams/teams-powershell-overview)
  
[<span data-ttu-id="6a050-119">PowerShell을 사용 하 여 Microsoft 365 관리</span><span class="sxs-lookup"><span data-stu-id="6a050-119">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="6a050-120">Microsoft 365 용 PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="6a050-120">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)

