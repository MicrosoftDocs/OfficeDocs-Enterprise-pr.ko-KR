---
title: "Office 365 PowerShell을 사용 하 여 사용자 계정에서 라이센스를 제거 합니다."
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
- PowerShell
- Ent_Office_Other
- LIL_Placement
- O365ITProTrain
ms.assetid: e7e4dc5e-e299-482c-9414-c265e145134f
description: "Office 365 PowerShell을 사용 하 여 사용자에 게 이전에 할당 된 Office 365 라이선스를 제거 하는 방법에 설명 합니다."
ms.openlocfilehash: d419aab9b3287364567e03accdfb2e687eacb0de
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/11/2018
---
# <a name="remove-licenses-from-user-accounts-with-office-365-powershell"></a><span data-ttu-id="7a2c5-103">Office 365 PowerShell을 사용 하 여 사용자 계정에서 라이센스를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a2c5-103">Remove licenses from user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="7a2c5-104">**요약:** Office 365 PowerShell을 사용 하 여 사용자에 게 이전에 할당 된 Office 365 라이선스를 제거 하는 방법에 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a2c5-104">**Summary:** Explains how to use Office 365 PowerShell to remove Office 365 licenses that were previously assigned to users.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="7a2c5-105">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="7a2c5-105">Before you begin</span></span>

- <span data-ttu-id="7a2c5-p101">이 항목의 절차를 수행하려면 Office 365 PowerShell에 연결되어 있어야 합니다. 지침을 보려면 [PowerShell Office 365에 연결](connect-to-office-365-powershell.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7a2c5-p101">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="7a2c5-108">조직에서 라이선스 계획 ( **AccountSkuID** ) 정보를 보려면 다음 항목을 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a2c5-108">To view the licensing plan ( **AccountSkuID** ) information in your organization, see the following topics:</span></span>
    
  - [<span data-ttu-id="7a2c5-109">라이선스 및 Office 365 PowerShell을 사용 하 여 서비스를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a2c5-109">View licenses and services with Office 365 PowerShell</span></span>](view-licenses-and-services-with-office-365-powershell.md)
    
  - [<span data-ttu-id="7a2c5-110">Office 365 PowerShell을 사용 하 여 계정 라이센스와 서비스 정보 보기</span><span class="sxs-lookup"><span data-stu-id="7a2c5-110">View account license and service details with Office 365 PowerShell</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
    
- <span data-ttu-id="7a2c5-111">_-All_ 매개 변수를 사용하지 않고 **Get-MsolUser** cmdlet을 사용하는 경우 처음 500개의 계정만 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a2c5-111">If you use the **Get-MsolUser** cmdlet without using the _-All_ parameter, only the first 500 accounts are returned.</span></span>
    
## <a name="the-short-version-instructions-without-explanations"></a><span data-ttu-id="7a2c5-112">간략 한 (설명 없이 지침)</span><span class="sxs-lookup"><span data-stu-id="7a2c5-112">The short version (instructions without explanations)</span></span>
<span data-ttu-id="7a2c5-113"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="7a2c5-113"></span></span>

<span data-ttu-id="7a2c5-p102">이 여기서도 바라지 나 불필요 한 설명을 하지 않고 절차를 제공합니다. 질문이 있거나 자세한 내용을 확인 하려면 해당 항목의 나머지 부분을 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a2c5-p102">This section presents the procedures without fanfare or superfluous explanation. If you have questions or want more information, you can read rest of the topic.</span></span>
  
<span data-ttu-id="7a2c5-116">기존 사용자 계정에서 라이센스를 제거 하려면 다음 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a2c5-116">To remove licenses from an existing user account, use the following syntax:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

<span data-ttu-id="7a2c5-117">이 예제에서는 제거는 `litwareinc:ENTERPRISEPACK` BelindaN@litwareinc.com 사용자 계정에서 라이선스를 (Office 365 Enterprise E3).</span><span class="sxs-lookup"><span data-stu-id="7a2c5-117">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from the user account BelindaN@litwareinc.com.</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="7a2c5-118">기존 사용이 허가 된 사용자 그룹에서 라이센스를 제거 하려면 다음 방법 중 하나를 사용.</span><span class="sxs-lookup"><span data-stu-id="7a2c5-118">To remove licenses from a group of existing licensed users, use either of the following methods:</span></span>
  
- <span data-ttu-id="7a2c5-119">**기존 계정 특성을 기준으로 계정 필터링** 이 작업을 수행 하려면 다음 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a2c5-119">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
```
$x = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

<span data-ttu-id="7a2c5-120">제거 하는이 예제는 `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) 모든 accounts에서 사용자를 위한 라이선스 미국에서 Sales 부서에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a2c5-120">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licenses from all accounts for users in the Sales department in the United States.</span></span>
    
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
$USSales | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

- <span data-ttu-id="7a2c5-121">**특정 계정 목록 사용** 이 작업을 수행 하려면 다음 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a2c5-121">**Use a list of specific accounts** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="7a2c5-122">만들고 다음과 같이 각 줄에 한 계정에 포함 된 텍스트 파일을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a2c5-122">Create and save a text file that contains one account on each line like this:</span></span>
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

2. <span data-ttu-id="7a2c5-123">다음 구문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7a2c5-123">Use the following syntax:</span></span>
    
  ```
  Get-Content "<FileNameAndPath>" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
  ```

<span data-ttu-id="7a2c5-124">이 예제에서는 제거는 `litwareinc:ENTERPRISEPACK` C:\My Documents\Accounts.txt 텍스트 파일에 정의 된 사용자 계정에서 라이선스를 (Office 365 Enterprise E3).</span><span class="sxs-lookup"><span data-stu-id="7a2c5-124">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from the user accounts defined in the text file C:\My Documents\Accounts.txt.</span></span>
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"
  ```

<span data-ttu-id="7a2c5-125">모든 기존 사용자 계정에서 라이센스를 제거 하려면 다음 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a2c5-125">To remove licenses from all existing user accounts, use the following syntax:</span></span>
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

<span data-ttu-id="7a2c5-126">이 예제에서는 제거는 `litwareinc:ENTERPRISEPACK` 에서 모든 기존 (Office 365 Enterprise E3) 라이선스 사용이 허가 된 사용자 계정입니다.</span><span class="sxs-lookup"><span data-stu-id="7a2c5-126">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from all existing licensed user accounts.</span></span>
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a><span data-ttu-id="7a2c5-127">긴 버전 (명령에 대 한 세부 정보)</span><span class="sxs-lookup"><span data-stu-id="7a2c5-127">The long version (instructions with detailed explanations)</span></span>
<span data-ttu-id="7a2c5-128"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="7a2c5-128"></span></span>

<span data-ttu-id="7a2c5-p103">Nothing으로, 지속 되 고 Office 365 라이선스를 포함 하는: 일찍 또는 늦게 올 것 시간 사용자 계정에서 라이선스를 제거 해야 합니다. 엔터프라이즈 무선 전화 통신 사용자 나가기; 것 엔터프라이즈 무선 전화 통신 사용자가 더 이상는 운영 체제 버전; 위의-물론 있는데 분명 임의 개수의 사용자 라이선스를 제거 하는 이유는 이유</span><span class="sxs-lookup"><span data-stu-id="7a2c5-p103">Nothing lasts forever, and that includes Office 365 licenses: sooner or later, there will come a time when you need to remove a license from a user account. Maybe the user is going on leave; maybe the user no longer needs the license; maybe - well, there are obviously any number of reasons why you might want to remove a user license.</span></span>
  
<span data-ttu-id="7a2c5-p104">들어가기 전에 추가 된 잘 하는데 필요 라이선스를 제거 하는 것이 중요 것, 라이선스를 제거: 라이선스 제거와 동일한 작업 없는 라이선스에서 모든 서비스를 사용 하지 않도록 설정 합니다. 예에서는 모든 Office 365 라이선스;를 사용 한다고 가정 즉, 우리는 사용할 수 있는 한 어떠한 라이선스를 제공 합니다. 사용 하지 않으려면 모든 서비스 라고 표시, Belinda Newman의 계정에서 [Office 365 PowerShell을 사용 하 여 서비스에 대 한 액세스를 사용 하지 않도록 설정](disable-access-to-services-with-office-365-powershell.md) 의 절차를 수행 하기로 결정 합니다. 얼마나 많은 라이선스를 제공 하는 것이 할까요는 갖습니다를 보면 사용 가능한? 이와: 0입니다. 예, 해당 항목의 절차를 *사용 하지 않도록 설정* Belinda 라이선스에는 서비스는 모두 하지만 해제 하지 것입니다 (즉, 삭제) 자체 라이선스입니다. 라이선스 계속 유효 수 있으며 여전히 Belinda Newman에 게 할당 됩니다. 대화 상대가 방금 수 없습니다를 사용 하 여 해당 라이선스 모든 Office 365 서비스에 액세스 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a2c5-p104">Before we go any further it's important to note that removing a license requires you to, well, remove the license: disabling all the services on a license is not the same thing as removing a license. For example, suppose we've used up all our Office 365 licenses; in other words, we have no licenses available whatsoever. You decide to follow the procedure in [Disable access to services with Office 365 PowerShell](disable-access-to-services-with-office-365-powershell.md) to disable all the services, say, on Belinda Newman's account. After we do that, how many licenses will we have available to us? That's right: zero. Yes, the procedure from that topic will *disable*  all the services on Belinda's license, but it will not disable (i.e., delete) the license itself. The license will still be valid, and it will still be assigned to Belinda Newman. She just won't be able to use that license to access any Office 365 services.</span></span>
  
<span data-ttu-id="7a2c5-p105">중요 한 이며: 사용자에 게 서 라이선스를 제거 하려는 경우 실제로 *제거* 를 라이선스을 수행 해야 합니다. 모든 서비스 하지 않도록 설정 된 사용자 로그온 하는 Office 365에서에서 있지만 자신의 라이선스 확보 되지 않습니다. 현재이 1 이면 _RemoveLicenses_ 매개 변수를 사용 하 여 실제로 Belinda에 이전에 할당 된 라이선스를 제거 하는 명령은 다음과 비슷한 명령을 실행 해야 사용자에 게 할당 된 라이선스를 회수 하려면:</span><span class="sxs-lookup"><span data-stu-id="7a2c5-p105">And that's important: if you want to remove a license from a user you must actually  *remove*  the license. Disabling all the services will prevent the user from logging on to Office 365, but it won't free up his or her license. If you want to take back a license that's currently assigned to a user you need to run a command similar to this one, a command that uses the _RemoveLicenses_ parameter to actually remove the license previously assigned to Belinda:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="7a2c5-142">해당 명령을 실행 하 고 Belinda Newman Office 365를 사용 하 여 라이선스 더이상 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a2c5-142">Run that command, and Belinda Newman will no longer be licensed to use Office 365.</span></span>
  
> [!NOTE]
> <span data-ttu-id="7a2c5-p106">볼 수 있듯이, 제거할 라이선스의 이름을 지정 하면 _RemoveLicenses_ 매개 변수를 사용 합니다. 확실 하지 않은 경우 다음과 같은 명령을 실행 하는 사용자에 게 라이선스를 할당 하는 라이선스 계획 사용 되었습니다.`Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Format-List DisplayName,Licenses`</span><span class="sxs-lookup"><span data-stu-id="7a2c5-p106">As you can see, when you use the  _RemoveLicenses_ parameter you need to specify the name of the license to be removed. If you aren't sure which licensing plan was used to assign a license to the user just run a command like this:  `Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Format-List DisplayName,Licenses`</span></span>
  
<span data-ttu-id="7a2c5-145">라이선스가 실제로 제거되었는지 확인하려면 Get-MsolUser를 사용하여 문제의 사용자 계정을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="7a2c5-145">To verify that the license really was removed, use the Get-MsolUser to check the user account in question:</span></span>
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

<span data-ttu-id="7a2c5-146">모든 계획을 제공 하기 위해,으로 Belinda의 **isLicensed** 속성 설정 이제 됩니다 `False`:</span><span class="sxs-lookup"><span data-stu-id="7a2c5-146">If everything went according to plan, Belinda's **isLicensed** property will now be set to `False`:</span></span>
  
```
UserPrincipalName            DisplayName         isLicensed
-----------------            -----------         ----------
BelindaN@litwareinc.com      Newman, Belinda     False
```

<span data-ttu-id="7a2c5-p107">사용자 계정을 삭제 하 여 라이선스를 확보 하는 다른 방법은 됩니다. 자세한 내용은 [삭제 하 고 사용자 계정을 Office 365 powershell 복원](delete-and-restore-user-accounts-with-office-365-powershell.md)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="7a2c5-p107">Another way to free up a license is by deleting the user account. For more information, see [Delete and restore user accounts with Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="7a2c5-149">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7a2c5-149">See also</span></span>

<span data-ttu-id="7a2c5-150">Office 365 PowerShell을 사용 하여 사용자를 관리에 대하여 다음과 같은 추가 항목을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="7a2c5-150">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="7a2c5-151">Office 365 PowerShell을 사용 하 여 사용자 계정 만들기</span><span class="sxs-lookup"><span data-stu-id="7a2c5-151">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="7a2c5-152">삭제 한 사용자 계정 Office 365 PowerShell을 사용 하 여 복원 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a2c5-152">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="7a2c5-153">블록 사용자 계정 Office 365 PowerShell을 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="7a2c5-153">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="7a2c5-154">Office 365 PowerShell을 사용 하 여 사용자 계정에 라이선스를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a2c5-154">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="7a2c5-155">이 항목에서 사용된 cmdlet에 대한 자세한 내용은 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="7a2c5-155">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="7a2c5-156">Get-content</span><span class="sxs-lookup"><span data-stu-id="7a2c5-156">Get-Content</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [<span data-ttu-id="7a2c5-157">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="7a2c5-157">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="7a2c5-158">Set-msoluserlicense</span><span class="sxs-lookup"><span data-stu-id="7a2c5-158">Set-MsolUserLicense</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [<span data-ttu-id="7a2c5-159">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="7a2c5-159">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="7a2c5-160">Where-Object</span><span class="sxs-lookup"><span data-stu-id="7a2c5-160">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
## <a name="new-to-office-365"></a><span data-ttu-id="7a2c5-161">Office 365의 새로운 기능</span><span class="sxs-lookup"><span data-stu-id="7a2c5-161">New to Office 365?</span></span>

||
|:-----|
|<span data-ttu-id="7a2c5-p108">![LinkedIn 학습에 대 한 짧은 아이콘](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **새로 만들기를 Office 365?**         [Office 365 관리자 및 IT 전문가](https://support.office.com/article/Office-365-admin-and-IT-pro-courses-68cc9b95-0bdc-491e-a81f-ee70b3ec63c5), LinkedIn 학습에 의해 제공자에 대 한 무료 비디오 코스를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a2c5-p108">![The short icon for LinkedIn Learning](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **New to Office 365?**         Discover free video courses for [Office 365 admins and IT pros](https://support.office.com/article/Office-365-admin-and-IT-pro-courses-68cc9b95-0bdc-491e-a81f-ee70b3ec63c5), brought to you by LinkedIn Learning.</span></span> |
   

