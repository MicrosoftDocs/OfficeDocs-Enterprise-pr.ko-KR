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
# <a name="turn-off-directory-synchronization-for-microsoft-365"></a><span data-ttu-id="fc28b-103">Microsoft 365에 대 한 디렉터리 동기화 해제</span><span class="sxs-lookup"><span data-stu-id="fc28b-103">Turn off directory synchronization for Microsoft 365</span></span>
<span data-ttu-id="fc28b-104">PowerShell을 사용 하 여 디렉터리 동기화를 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc28b-104">You can use PowerShell to turn off directory synchronization.</span></span> <span data-ttu-id="fc28b-105">그러나 디렉터리 동기화를 문제 해결 단계로 해제 하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="fc28b-105">However, it is not recommended that you turn off directory synchronization as a troubleshooting step.</span></span> <span data-ttu-id="fc28b-106">디렉터리 동기화 문제를 해결 하는 데 도움이 필요한 경우 [Microsoft 365의 디렉터리 동기화 문제 해결](fix-problems-with-directory-synchronization.md) 문서를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="fc28b-106">If you need assistance with troubleshooting directory synchronization, see the [Fixing problems with directory synchronization for Microsoft 365](fix-problems-with-directory-synchronization.md) article.</span></span> 
  
<span data-ttu-id="fc28b-107">필요한 경우 비즈니스 제품에 대해 [고객 지원에 문의 하세요](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) .</span><span class="sxs-lookup"><span data-stu-id="fc28b-107">[Contact support](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) for business products if needed.</span></span>
  
## <a name="turn-off-directory-synchronization"></a><span data-ttu-id="fc28b-108">디렉터리 동기화 끄기</span><span class="sxs-lookup"><span data-stu-id="fc28b-108">Turn off directory synchronization</span></span>  
<span data-ttu-id="fc28b-109">디렉터리 동기화를 해제 하려면</span><span class="sxs-lookup"><span data-stu-id="fc28b-109">To turn off Directory synchronization:</span></span>
  
1. <span data-ttu-id="fc28b-110">먼저 필요한 소프트웨어를 설치 하 고 Microsoft 365 구독에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc28b-110">First, install the required software and connect to your Microsoft 365 subscription.</span></span> <span data-ttu-id="fc28b-111">자세한 내용은 [Windows PowerShell 용 Microsoft Azure Active Directory 모듈을 사용 하 여 연결](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="fc28b-111">For instructions, see [Connect with the Microsoft Azure Active Directory Module for Windows PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
    
2. <span data-ttu-id="fc28b-112">MsolDirSyncEnabled을 사용 하 여 디렉터리 동기화를 사용 하지 않도록 [설정](https://go.microsoft.com/fwlink/p/?LinkId=821939) 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc28b-112">Use [Set-MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939) to disable directory synchronization:</span></span> 
    
  ```powershell
  Set-MsolDirSyncEnabled -EnableDirSync $false
  ```

>[!Note]
><span data-ttu-id="fc28b-113">이 명령을 사용 하는 경우에는 72 시간을 기다린 후 디렉터리 동기화를 다시 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc28b-113">If you use this command, you must wait 72 hours before you can turn directory synchronization back on.</span></span>
>
 
