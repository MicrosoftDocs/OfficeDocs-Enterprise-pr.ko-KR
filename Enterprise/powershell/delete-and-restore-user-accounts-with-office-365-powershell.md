---
title: Office 365 PowerShell로 사용자 계정 삭제하기
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- O365ITProTrain
ms.assetid: 209c9868-448c-49bc-baae-11e28b923a39
description: Office 365 PowerShell을 사용하여 Office 365 사용자 계정을 삭제하는 방법에 대해 알아보세요.
ms.openlocfilehash: b7c30ec422475a4cf11b28249e8a20d64a3c90a4
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2019
ms.locfileid: "38746431"
---
# <a name="delete-user-accounts-with-office-365-powershell"></a><span data-ttu-id="1ea04-103">Office 365 PowerShell로 사용자 계정 삭제하기</span><span class="sxs-lookup"><span data-stu-id="1ea04-103">Delete user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="1ea04-104">사용자 계정을 삭제할 때 Office 365 PowerShell을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ea04-104">You can use Office 365 PowerShell to delete a user account.</span></span>
   
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="1ea04-105">Graph 모듈용 Azure Active Directory PowerShell 사용하기</span><span class="sxs-lookup"><span data-stu-id="1ea04-105">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="1ea04-106">먼저, [Office 365 테넌트에 연결](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)합니다.</span><span class="sxs-lookup"><span data-stu-id="1ea04-106">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>

<span data-ttu-id="1ea04-107">연결한 후 다음 구문을 사용하여 개별 사용자 계정을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="1ea04-107">After you have connected, use the following syntax to remove an individual user account:</span></span>
  
```powershell
Remove-AzureADUser -ObjectID <sign-in name>
```

<span data-ttu-id="1ea04-108">이 예제에서는 사용자 계정 fabricec@litwareinc.com을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="1ea04-108">This example removes the user account fabricec@litwareinc.com.</span></span>
  
```powershell
Remove-AzureADUser -ObjectID fabricec@litwareinc.com
```

> [!NOTE]
> <span data-ttu-id="1ea04-109">**Remove-AureAD** cmdlet의 **-ObjectID** 매개 변수는 사용자 계정 이름으로 알려진 계정 로그인 이름, 또는 계정의 개체 ID를 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="1ea04-109">The **-ObjectID** parameter in the **Remove-AzureAD** cmdlet accepts either the account's sign-in name, also known as the User Principal Name, or the account's object ID.</span></span>
  
<span data-ttu-id="1ea04-110">사용자 이름을 기준으로 계정 이름을 표시하려면 다음 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1ea04-110">To display the account name based on the user's name, use the following commands:</span></span>
  
```powershell
$userName="<User name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="1ea04-111">이 예제에서는 Caleb Sills라는 사용자의 계정 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="1ea04-111">This example displays the account name for the user named Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="1ea04-112">사용자 표시 이름을 기준으로 계정을 제거하려면 다음 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1ea04-112">To remove an account based on the user's display name, use the following commands:</span></span>
  
```powershell
$userName="<display name>"
Remove-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="1ea04-113">Windows PowerShell용 Microsoft Azure Active Directory 모듈 사용하기</span><span class="sxs-lookup"><span data-stu-id="1ea04-113">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="1ea04-p101">Windows PowerShell용 Microsoft Azure Active Directory 모듈을 사용하여 사용자 계정을 삭제할 경우에 계정은 영구 삭제되지 않습니다. 30일 이내에 삭제한 사용자 계정은 복원할 수 있습니다. </span><span class="sxs-lookup"><span data-stu-id="1ea04-p101">When you delete a user account with the Microsoft Azure Active Directory Module for Windows PowerShell, the account isn't permanently deleted. You can restore the deleted user account within 30 days.</span></span>

<span data-ttu-id="1ea04-116">먼저, [Office 365 테넌트에 연결](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)합니다.</span><span class="sxs-lookup"><span data-stu-id="1ea04-116">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>


<span data-ttu-id="1ea04-117">사용자 계정을 삭제하려면 다음 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ea04-117">To delete a user account, use the following syntax:</span></span>
  
```powershell
Remove-MsolUser -UserPrincipalName <sign-in name>
```

<span data-ttu-id="1ea04-118">BelindaN@litwareinc.com 사용자 계정을 삭제 하는이 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="1ea04-118">This example deletes the user account BelindaN@litwareinc.com.</span></span>
  
```powershell
Remove-MsolUser -UserPrincipalName belindan@litwareinc.com
```

<span data-ttu-id="1ea04-119">30 일 유예 기간 동안 삭제 된 사용자 계정을 복원 하려면 다음 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ea04-119">To restore a deleted user account within the 30-day grace period, use the following syntax:</span></span>
  
```powershell
Restore-MsolUser -UserPrincipalName <sign-in name>
```

<span data-ttu-id="1ea04-120">삭제 된 계정 BelindaN@litwareinc.com을 복원 하는이 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="1ea04-120">This example restores the deleted account BelindaN@litwareinc.com.</span></span>
  
```powershell
Restore-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

 <span data-ttu-id="1ea04-121">**참고:**</span><span class="sxs-lookup"><span data-stu-id="1ea04-121">**Notes:**</span></span>
  
- <span data-ttu-id="1ea04-122">복원할 수 있는 삭제된 사용자 목록을 보려면 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ea04-122">To see the list of deleted users that can be restored, run the following command:</span></span>
    
  ```powershell
  Get-MsolUser -All -ReturnDeletedUsers
  ```

- <span data-ttu-id="1ea04-123">사용자 계정의 원본 사용자 계정 이름이 다른 계정에서 사용된 경우에, 사용자 계정을 복원할 때 다른 사용자 계정 이름을 지정하려면 _UserPrincipalName_ 대신에 _NewUserPrincipalName_ 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1ea04-123">If the user account's original user principal name is used by another account, use the _NewUserPrincipalName_ parameter instead of _UserPrincipalName_ to specify a different user principal name when you restore the user account.</span></span>


## <a name="see-also"></a><span data-ttu-id="1ea04-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1ea04-124">See also</span></span>

[<span data-ttu-id="1ea04-125">Office 365 PowerShell로 사용자 계정 및 라이선스 관리</span><span class="sxs-lookup"><span data-stu-id="1ea04-125">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="1ea04-126">Office 365 PowerShell 사용한 Office 365 관리</span><span class="sxs-lookup"><span data-stu-id="1ea04-126">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="1ea04-127">Office 365 PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="1ea04-127">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

