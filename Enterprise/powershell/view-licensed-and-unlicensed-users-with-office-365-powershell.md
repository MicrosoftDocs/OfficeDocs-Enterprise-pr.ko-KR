---
title: Office 365 PowerShell을 사용 하 여 허가 된 / 허가 되지 않은 사용자 보기
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/29/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: e4ee53ed-ed36-4993-89f4-5bec11031435
description: 사용 하는 방법에 설명 Office 365 PowerShell 허가 된 / 허가 되지 않은 사용자 계정을 볼 수 있습니다.
ms.openlocfilehash: 61f94664a62b6a5cb178579c1a5777b208d0b2ec
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123365"
---
# <a name="view-licensed-and-unlicensed-users-with-office-365-powershell"></a><span data-ttu-id="15739-103">Office 365 PowerShell을 사용 하 여 허가 된 / 허가 되지 않은 사용자 보기</span><span class="sxs-lookup"><span data-stu-id="15739-103">View licensed and unlicensed users with Office 365 PowerShell</span></span>

<span data-ttu-id="15739-104">**요약:** Office 365 PowerShell을 사용하여 허가되거나 허가되지 않은 사용자 계정을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15739-104">**Summary:** Explains how to use Office 365 PowerShell to view licensed and unlicensed user accounts.</span></span>
  
<span data-ttu-id="15739-p101">사용자 계정에 사용자 Office 365 조직 일부, 또는 전체 조직에서 사용할 수 있는 라이센스 계획에서 할당 된 사용 가능한 라이선스 중 있을 수 있습니다. 사용할 수 있습니다 Office 365 PowerShell 조직에서 허가 된 / 허가 되지 않은 사용자를 빠르게 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15739-p101">User accounts in your Office 365 organization may have some, all, or none of the available licenses assigned to them from the licensing plans that are available in your organization. You can use Office 365 PowerShell to quickly find the licensed and unlicensed users in your organization.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="15739-107">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="15739-107">Before you begin</span></span>

- <span data-ttu-id="15739-p102">이 항목의 절차를 수행하려면 Office 365 PowerShell에 연결되어 있어야 합니다. 지침을 보려면 [PowerShell Office 365에 연결](connect-to-office-365-powershell.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="15739-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="15739-110">_-All_ 매개 변수를 사용하지 않고 **Get-MsolUser** cmdlet을 사용하는 경우 처음 500개의 계정만 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="15739-110">If you use the **Get-MsolUser** cmdlet without using the _-All_ parameter, only the first 500 accounts are returned.</span></span>
    
## <a name="viewing-licensed-and-unlicensed-users"></a><span data-ttu-id="15739-111">사용이 허가 된 사용자와 허가 되지 않은 사용자 보기</span><span class="sxs-lookup"><span data-stu-id="15739-111">Viewing licensed and unlicensed users</span></span>

<span data-ttu-id="15739-112">조직에서 모든 사용자 계정 및 라이선스 상태 목록을 보려는 다음 명령에서 실행 Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="15739-112">To view the list of all user accounts and their licensing status in your organization, run the following command in Office 365 PowerShell:</span></span>
  
```
Get-MsolUser -All
```

<span data-ttu-id="15739-113">조직의 모든 허가 되지 않은 사용자 계정 목록을 보려면 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="15739-113">To view the list of all unlicensed user accounts in your organization, run the following command:</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly
```

<span data-ttu-id="15739-114">전체 목록을 보려면 다음 명령을 실행 하 여 조직에 있는 사용자 계정의 라이센스:</span><span class="sxs-lookup"><span data-stu-id="15739-114">To view the list of all licensed user accounts in your organization, run the following command:</span></span>
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true}
```

## <a name="see-also"></a><span data-ttu-id="15739-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="15739-115">See also</span></span>

<span data-ttu-id="15739-116">이 항목에서 사용된 cmdlet에 대한 자세한 내용은 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="15739-116">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="15739-117">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="15739-117">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [<span data-ttu-id="15739-118">Where-Object</span><span class="sxs-lookup"><span data-stu-id="15739-118">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

