---
title: Office 365 PowerShell을 사용 하 여 사용자 계정에서 라이센스를 제거 합니다.
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
- PowerShell
- Ent_Office_Other
- LIL_Placement
- O365ITProTrain
ms.assetid: e7e4dc5e-e299-482c-9414-c265e145134f
description: Office 365 PowerShell을 사용 하 여 사용자에 게 이전에 할당 된 Office 365 라이선스를 제거 하는 방법에 설명 합니다.
ms.openlocfilehash: a993737f4bd1186a7fb5beb7fa0f6a2ae6782618
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123305"
---
# <a name="remove-licenses-from-user-accounts-with-office-365-powershell"></a><span data-ttu-id="a2eac-103">Office 365 PowerShell을 사용 하 여 사용자 계정에서 라이센스를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2eac-103">Remove licenses from user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="a2eac-104">**요약:** Office 365 PowerShell을 사용 하 여 사용자에 게 이전에 할당 된 Office 365 라이선스를 제거 하는 방법에 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2eac-104">**Summary:** Explains how to use Office 365 PowerShell to remove Office 365 licenses that were previously assigned to users.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="a2eac-105">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="a2eac-105">Before you begin</span></span>

- <span data-ttu-id="a2eac-p101">이 항목의 절차를 수행하려면 Office 365 PowerShell에 연결되어 있어야 합니다. 지침을 보려면 [PowerShell Office 365에 연결](connect-to-office-365-powershell.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a2eac-p101">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="a2eac-108">조직에서 라이선스 계획 (**AccountSkuID** ) 정보를 보려면 다음 항목을 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2eac-108">To view the licensing plan (**AccountSkuID** ) information in your organization, see the following topics:</span></span>
    
  - [<span data-ttu-id="a2eac-109">Office 365 PowerShell을 사용하여 라이선스 및 서비스 보기</span><span class="sxs-lookup"><span data-stu-id="a2eac-109">View licenses and services with Office 365 PowerShell</span></span>](view-licenses-and-services-with-office-365-powershell.md)
    
  - [<span data-ttu-id="a2eac-110">Office 365 PowerShell을 사용 하 여 계정 라이센스와 서비스 정보 보기</span><span class="sxs-lookup"><span data-stu-id="a2eac-110">View account license and service details with Office 365 PowerShell</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
    
- <span data-ttu-id="a2eac-111">_-All_ 매개 변수를 사용하지 않고 **Get-MsolUser** cmdlet을 사용하는 경우 처음 500개의 계정만 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="a2eac-111">If you use the **Get-MsolUser** cmdlet without using the _-All_ parameter, only the first 500 accounts are returned.</span></span>
    
## <a name="removing-licenses-from-user-accounts"></a><span data-ttu-id="a2eac-112">사용자 계정에서 라이선스를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="a2eac-112">Removing licenses from user accounts</span></span>

<span data-ttu-id="a2eac-113">기존 사용자 계정에서 라이센스를 제거 하려면 다음 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2eac-113">To remove licenses from an existing user account, use the following syntax:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

<span data-ttu-id="a2eac-114">이 예제에서는 제거는 `litwareinc:ENTERPRISEPACK` BelindaN@litwareinc.com 사용자 계정에서 라이선스를 (Office 365 Enterprise E3).</span><span class="sxs-lookup"><span data-stu-id="a2eac-114">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from the user account BelindaN@litwareinc.com.</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="a2eac-115">기존 사용이 허가 된 사용자 그룹에서 라이센스를 제거 하려면 다음 방법 중 하나를 사용.</span><span class="sxs-lookup"><span data-stu-id="a2eac-115">To remove licenses from a group of existing licensed users, use either of the following methods:</span></span>
  
- <span data-ttu-id="a2eac-116">**기존 계정 특성을 기준으로 계정 필터링** 이 작업을 수행 하려면 다음 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2eac-116">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
```
$x = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

<span data-ttu-id="a2eac-117">제거 하는이 예제는 `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) 모든 accounts에서 사용자를 위한 라이선스 미국에서 Sales 부서에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2eac-117">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licenses from all accounts for users in the Sales department in the United States.</span></span>
    
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
$USSales | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

- <span data-ttu-id="a2eac-118">**특정 계정 목록 사용** 이 작업을 수행 하려면 다음 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2eac-118">**Use a list of specific accounts** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="a2eac-119">만들고 다음과 같이 각 줄에 한 계정에 포함 된 텍스트 파일을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2eac-119">Create and save a text file that contains one account on each line like this:</span></span>
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

2. <span data-ttu-id="a2eac-120">다음 구문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a2eac-120">Use the following syntax:</span></span>
    
  ```
  Get-Content "<FileNameAndPath>" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
  ```

<span data-ttu-id="a2eac-121">이 예제에서는 제거는 `litwareinc:ENTERPRISEPACK` C:\My Documents\Accounts.txt 텍스트 파일에 정의 된 사용자 계정에서 라이선스를 (Office 365 Enterprise E3).</span><span class="sxs-lookup"><span data-stu-id="a2eac-121">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from the user accounts defined in the text file C:\My Documents\Accounts.txt.</span></span>
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"
  ```

<span data-ttu-id="a2eac-122">모든 기존 사용자 계정에서 라이센스를 제거 하려면 다음 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2eac-122">To remove licenses from all existing user accounts, use the following syntax:</span></span>
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

<span data-ttu-id="a2eac-123">이 예제에서는 제거는 `litwareinc:ENTERPRISEPACK` 에서 모든 기존 (Office 365 Enterprise E3) 라이선스 사용이 허가 된 사용자 계정입니다.</span><span class="sxs-lookup"><span data-stu-id="a2eac-123">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from all existing licensed user accounts.</span></span>
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

<span data-ttu-id="a2eac-p102">사용자 계정을 삭제 하 여 라이선스를 확보 하는 다른 방법은 됩니다. 자세한 내용은 [삭제 하 고 사용자 계정을 Office 365 powershell 복원](delete-and-restore-user-accounts-with-office-365-powershell.md)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="a2eac-p102">Another way to free up a license is by deleting the user account. For more information, see [Delete and restore user accounts with Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a2eac-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a2eac-126">See also</span></span>

<span data-ttu-id="a2eac-127">Office 365 PowerShell을 사용 하여 사용자를 관리에 대하여 다음과 같은 추가 항목을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="a2eac-127">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="a2eac-128">Office 365 PowerShell을 사용 하 여 사용자 계정 만들기</span><span class="sxs-lookup"><span data-stu-id="a2eac-128">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="a2eac-129">삭제 한 사용자 계정 Office 365 PowerShell을 사용 하 여 복원 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2eac-129">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="a2eac-130">블록 사용자 계정 Office 365 PowerShell을 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="a2eac-130">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="a2eac-131">Office 365 PowerShell을 사용 하 여 사용자 계정에 라이선스를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2eac-131">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="a2eac-132">이 항목에서 사용된 cmdlet에 대한 자세한 내용은 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="a2eac-132">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="a2eac-133">Get-content</span><span class="sxs-lookup"><span data-stu-id="a2eac-133">Get-Content</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [<span data-ttu-id="a2eac-134">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="a2eac-134">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="a2eac-135">Set-msoluserlicense</span><span class="sxs-lookup"><span data-stu-id="a2eac-135">Set-MsolUserLicense</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [<span data-ttu-id="a2eac-136">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="a2eac-136">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="a2eac-137">Where-Object</span><span class="sxs-lookup"><span data-stu-id="a2eac-137">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
## <a name="new-to-office-365"></a><span data-ttu-id="a2eac-138">Office 365의 새로운 기능</span><span class="sxs-lookup"><span data-stu-id="a2eac-138">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   

