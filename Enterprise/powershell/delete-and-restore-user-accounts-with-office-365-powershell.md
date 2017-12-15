---
title: "삭제 한 사용자 계정 Office 365 PowerShell을 사용 하 여 복원 합니다."
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- DecEntMigration
- PowerShell
- Ent_Office_Other
- O365ITProTrain
ms.assetid: 209c9868-448c-49bc-baae-11e28b923a39
description: "Office 365 PowerShell을 사용 하 여 삭제 하 고 Office 365 사용자 계정 복원 하는 방법에 알아봅니다."
ms.openlocfilehash: 8404395ea9594cea1a2e772cecbeb011756b7754
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2017
---
# <a name="delete-and-restore-user-accounts-with-office-365-powershell"></a><span data-ttu-id="8620d-103">삭제 한 사용자 계정 Office 365 PowerShell을 사용 하 여 복원 합니다.</span><span class="sxs-lookup"><span data-stu-id="8620d-103">Delete and restore user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="8620d-104">**요약:**  Office 365 PowerShell을 사용 하 여 삭제 하 고 Office 365 사용자 계정 복원 하는 방법에 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="8620d-104">**Summary:**  Learn how to use Office 365 PowerShell to delete and restore Office 365 user accounts.</span></span>
  
<span data-ttu-id="8620d-p101">Office 365 PowerShell을 사용 하 여 사용자 계정을 삭제 하려면 계정 영구적으로 삭제 되지 않습니다. 30 일 이내에 삭제 된 사용자 계정에 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8620d-p101">When you use Office 365 PowerShell to delete a user account, the account isn't permanently deleted. You can restore the deleted user account within 30 days.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="8620d-107">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="8620d-107">Before you begin</span></span>

- <span data-ttu-id="8620d-p102">이 항목의 절차에서는 Office 365 PowerShell에 연결 해야 합니다. 자세한 내용은 [Office 365 PowerShell 연결](connect-to-office-365-powershell.md)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="8620d-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="8620d-110">사용 하지 않고 **Get-msoluser** cmdlet을 사용 하는 경우는 _-모든_ 매개 변수를 처음 500 개 계정만 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8620d-110">If you use the **Get-MsolUser** cmdlet without using the _-All_ parameter, only the first 500 accounts are returned.</span></span>
    
## <a name="use-office-365-powershell-to-block-access-to-individual-user-accounts"></a><span data-ttu-id="8620d-111">Office 365 PowerShell을 사용 하 여 개별 사용자 계정에 대 한 액세스를 차단 하려면</span><span class="sxs-lookup"><span data-stu-id="8620d-111">Use Office 365 PowerShell to block access to individual user accounts</span></span>
<span data-ttu-id="8620d-112"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="8620d-112"></span></span>

<span data-ttu-id="8620d-113">사용자 계정을 삭제 하려면 다음 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8620d-113">To delete a user account, use the following syntax:</span></span>
  
```
Remove-MsolUser -UserPrincipalName <Account>
```

<span data-ttu-id="8620d-114">BelindaN@litwareinc.com 사용자 계정을 삭제 하는이 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="8620d-114">This example deletes the user account BelindaN@litwareinc.com.</span></span>
  
```
Remove-MsolUser -UserPrincipalName belindan@litwareinc.com
```

<span data-ttu-id="8620d-115">30 일 유예 기간 동안 삭제 된 사용자 계정을 복원 하려면 다음 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8620d-115">To restore a deleted user account within the 30-day grace period, use the following syntax:</span></span>
  
```
Restore-MsolUser -UserPrincipalName <Account>
```

<span data-ttu-id="8620d-116">삭제 된 계정 BelindaN@litwareinc.com을 복원 하는이 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="8620d-116">This example restores the deleted account BelindaN@litwareinc.com.</span></span>
  
```
Restore-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

 <span data-ttu-id="8620d-117">**참고 사항:**</span><span class="sxs-lookup"><span data-stu-id="8620d-117">**Notes:**</span></span>
  
- <span data-ttu-id="8620d-118">복원할 수 있는 삭제 된 사용자의 목록을 보려면 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="8620d-118">To see the list of deleted users that can be restored, run the following command:</span></span>
    
  ```
  Get-MsolUser -All -ReturnDeletedUsers
  ```

- <span data-ttu-id="8620d-119">사용자 계정의 원래 사용자 계정 이름 다른 계정에서 사용 하는 경우는 사용자 계정이 복원 하는 경우 다른 사용자 계정 이름을 지정 하려면 _UserPrincipalName_ 대신 _NewUserPrincipalName_ 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8620d-119">If the user account's original user principal name is used by another account, use the  _NewUserPrincipalName_ parameter instead of _UserPrincipalName_ to specify a different user principal name when you restore the user account.</span></span>
    
## <a name="use-the-azure-active-directory-v2-powershell-module-to-remove-a-user-account"></a><span data-ttu-id="8620d-120">Azure Active Directory V2 PowerShell 모듈을 사용하여 사용자 계정 제거</span><span class="sxs-lookup"><span data-stu-id="8620d-120">Use the Azure Active Directory V2 PowerShell module to remove a user account</span></span>
<span data-ttu-id="8620d-121"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="8620d-121"></span></span>

<span data-ttu-id="8620d-p103">Azure Active Directory V2 PowerShell 모듈에서 **제거 AzureADUser** cmdlet을 사용 하려면 먼저 구독에 연결 해야 합니다. 지침, [Azure Active Directory V2 PowerShell 모듈을 사용 하 여 연결](https://go.microsoft.com/fwlink/?linkid=842218)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="8620d-p103">To use the **Remove-AzureADUser** cmdlet from the Azure Active Directory V2 PowerShell module, you must first connect to your subscription. For the instructions, see [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
<span data-ttu-id="8620d-124">연결한 후 다음 구문을 사용하여 개별 사용자 계정을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="8620d-124">After you have connected, use the following syntax to remove an individual user account:</span></span>
  
```
Remove-AzureADUser -ObjectID <Account>
```

<span data-ttu-id="8620d-125">이 예제에서는 사용자 계정 fabricec@litwareinc.com을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="8620d-125">This example removes the user account fabricec@litwareinc.com.</span></span>
  
```
Remove-AzureADUser -ObjectID fabricec@litwareinc.com
```

> [!NOTE]
> <span data-ttu-id="8620d-126">**제거 AzureAD** cmdlet의 **-ObjectID** 매개 변수는 허용 중 하나는 계정 이름로 알려져 사용자 계정 이름 또는 계정 개체 id입니다.</span><span class="sxs-lookup"><span data-stu-id="8620d-126">The **-ObjectID** parameter in the **Remove-AzureAD** cmdlet accepts either the account name, also known as the User Principal Name, or the account's object ID.</span></span>
  
<span data-ttu-id="8620d-127">사용자 이름을 기준으로 계정 이름을 표시하려면 다음 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8620d-127">To display the account name based on the user's name, use the following commands:</span></span>
  
```
$userName="<User name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="8620d-128">이 예제에서는 Caleb Sills라는 사용자의 계정 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8620d-128">This example displays the account name for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="8620d-129">사용자 이름을 기준으로 계정을 제거하려면 다음 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8620d-129">To remove an account based on the user's name, use the following commands:</span></span>
  
```
$userName="<User name>"
Remove-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

## <a name="see-also"></a><span data-ttu-id="8620d-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8620d-130">See also</span></span>
<span data-ttu-id="8620d-131"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="8620d-131"></span></span>

<span data-ttu-id="8620d-132">Office 365 powershell 사용자를 관리 하는 방법에 대 한 다음 추가 항목을 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="8620d-132">See these additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="8620d-133">Office 365 PowerShell을 사용한 사용자 계정 만들기</span><span class="sxs-lookup"><span data-stu-id="8620d-133">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="8620d-134">Office 365 powershell 블록 사용자 계정</span><span class="sxs-lookup"><span data-stu-id="8620d-134">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="8620d-135">Office 365 PowerShell을 사용한 사용자 계정에 게 라이선스 할당</span><span class="sxs-lookup"><span data-stu-id="8620d-135">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="8620d-136">Office 365 PowerShell을 사용한 사용자 계정에서 라이선스를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="8620d-136">Remove licenses from user accounts with Office 365 PowerShell</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="8620d-137">이 항목에서 사용된 cmdlet에 대한 자세한 내용은 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="8620d-137">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="8620d-138">Get-msoluser</span><span class="sxs-lookup"><span data-stu-id="8620d-138">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="8620d-139">이와 제거</span><span class="sxs-lookup"><span data-stu-id="8620d-139">Remove-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691636)
    
- [<span data-ttu-id="8620d-140">이와 복원</span><span class="sxs-lookup"><span data-stu-id="8620d-140">Restore-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691637)
    
- [<span data-ttu-id="8620d-141">새 AzureADUser</span><span class="sxs-lookup"><span data-stu-id="8620d-141">New-AzureADUser</span></span>](https://docs.microsoft.com/powershell/module/azuread/new-azureaduser?view=azureadps-2.0)
    

