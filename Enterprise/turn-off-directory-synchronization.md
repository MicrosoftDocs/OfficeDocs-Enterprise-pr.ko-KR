---
title: Office 365의 디렉터리 동기화 끄기
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
description: PowerShell을 사용 하 여 Office 365에 대 한 디렉터리 동기화를 해제 하는 방법을 알아봅니다.
ms.openlocfilehash: eab736241372b2d1b6023dc803dff540dded64ae
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841015"
---
# <a name="turn-off-directory-synchronization-for-office-365"></a><span data-ttu-id="3dc40-103">Office 365의 디렉터리 동기화 끄기</span><span class="sxs-lookup"><span data-stu-id="3dc40-103">Turn off directory synchronization for Office 365</span></span>
<span data-ttu-id="3dc40-104">PowerShell을 사용 하 여 디렉터리 동기화를 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3dc40-104">You can use PowerShell to turn off directory synchronization.</span></span> <span data-ttu-id="3dc40-105">그러나 디렉터리 동기화를 문제 해결 단계로 해제 하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="3dc40-105">However, it is not recommended that you turn off directory synchronization as a troubleshooting step.</span></span> <span data-ttu-id="3dc40-106">디렉터리 동기화 문제를 해결 하는 데 도움이 필요한 경우 [Office 365의 디렉터리 동기화 문제 해결](fix-problems-with-directory-synchronization.md) 문서를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="3dc40-106">If you need assistance with troubleshooting directory synchronization, see the [Fixing problems with directory synchronization for Office 365](fix-problems-with-directory-synchronization.md) article.</span></span> 
  
<span data-ttu-id="3dc40-107">필요한 경우 비즈니스 제품에 대해 [고객 지원에 문의 하세요](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) .</span><span class="sxs-lookup"><span data-stu-id="3dc40-107">[Contact support](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) for business products if needed.</span></span>
  
## <a name="turn-off-directory-synchronization"></a><span data-ttu-id="3dc40-108">디렉터리 동기화 끄기</span><span class="sxs-lookup"><span data-stu-id="3dc40-108">Turn off directory synchronization</span></span>  
<span data-ttu-id="3dc40-109">디렉터리 동기화를 해제 하려면</span><span class="sxs-lookup"><span data-stu-id="3dc40-109">To turn off Directory synchronization:</span></span>
  
1. <span data-ttu-id="3dc40-110">먼저 필요한 소프트웨어를 설치 하 고 Office 365 구독에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="3dc40-110">First, install the required software and connect to your Office 365 subscription.</span></span> <span data-ttu-id="3dc40-111">자세한 내용은 [Windows PowerShell 용 Microsoft Azure Active Directory 모듈을 사용 하 여 연결](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="3dc40-111">For instructions, see [Connect with the Microsoft Azure Active Directory Module for Windows PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
    
2. <span data-ttu-id="3dc40-112">MsolDirSyncEnabled을 사용 하 여 디렉터리 동기화를 사용 하지 않도록 [설정](https://go.microsoft.com/fwlink/p/?LinkId=821939) 합니다.</span><span class="sxs-lookup"><span data-stu-id="3dc40-112">Use [Set-MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939) to disable directory synchronization:</span></span> 
    
  ```powershell
  Set-MsolDirSyncEnabled -EnableDirSync $false
  ```
