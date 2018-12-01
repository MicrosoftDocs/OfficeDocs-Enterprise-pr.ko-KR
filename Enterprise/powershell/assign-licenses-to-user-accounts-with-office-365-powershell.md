---
title: Office 365 PowerShell을 사용 하 여 사용자 계정에 라이선스를 할당 합니다.
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
- Ent_Office_Other
- LIL_Placement
- PowerShell
- O365ITProTrain
ms.assetid: ba235f4f-e640-4360-81ea-04507a3a70be
description: Office 365 PowerShell 할당 허가 되지 않은 사용자에 게 Office 365 라이선스를 사용 하는 방법에 설명 합니다.
ms.openlocfilehash: 4c91c9f2441d0e537f2fa23fd1f021fe0bfe03b6
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123295"
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="8e497-103">Office 365 PowerShell을 사용 하 여 사용자 계정에 라이선스를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e497-103">Assign licenses to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="8e497-104">**요약:**  Office 365 PowerShell 할당 허가 되지 않은 사용자에 게 Office 365 라이선스를 사용 하는 방법에 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e497-104">**Summary:**  Explains how to use Office 365 PowerShell assign an Office 365 license to unlicensed users.</span></span>
  
<span data-ttu-id="8e497-p101">사용자가 자신의 계정 사용이 허가 된 때까지 모든 Office 365 서비스를 사용할 수 없으므로 라이선스 Office 365에서 사용자 계정 하는 것이 중요 합니다. Office 365 PowerShell을 사용 하 여 효율적으로 허가 되지 않은 계정, 특히 여러 계정에 게 라이선스를 할당 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e497-p101">Licensing user accounts in Office 365 is important, because users can't use any Office 365 services until their account has been licensed. You can use Office 365 PowerShell to efficiently assign licenses to unlicensed accounts, especially multiple accounts.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="8e497-107">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="8e497-107">Before you begin</span></span>
<span data-ttu-id="8e497-108"><a name="RTT"> </a></span><span class="sxs-lookup"><span data-stu-id="8e497-108"></span></span>

- <span data-ttu-id="8e497-p102">이 항목의 절차를 수행하려면 Office 365 PowerShell에 연결되어 있어야 합니다. 지침을 보려면 [PowerShell Office 365에 연결](connect-to-office-365-powershell.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8e497-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="8e497-p103">**Get-msolaccountsku** cmdlet을 사용 하 여 조직에서 각 계획에서 사용 가능한 라이선스 계획 및 사용 가능한 라이선스 수를 볼 수 있습니다. 각 계획에서 사용 가능한 라이선스 수가 **ActiveUnits** - **WarningUnits** - **ConsumedUnits**합니다. 계획, 라이선스 및 서비스 라이선스에 대 한 자세한 내용은 [보기 라이선스 및 Office 365 PowerShell을 사용 하 여 서비스를](view-licenses-and-services-with-office-365-powershell.md)참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="8e497-p103">Use the **Get-MsolAccountSku** cmdlet to view the available licensing plans and the number of available licenses in each plan in your organization. The number of available licenses in each plan is **ActiveUnits** - **WarningUnits** - **ConsumedUnits**. For more information about licensing plans, licenses, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="8e497-114">명령을 실행 하면 조직에서 허가 되지 않은 계정을 찾으려면`Get-MsolUser -All -UnlicensedUsersOnly`</span><span class="sxs-lookup"><span data-stu-id="8e497-114">To find the unlicensed accounts in your organization, run the command  `Get-MsolUser -All -UnlicensedUsersOnly`</span></span>
    
- <span data-ttu-id="8e497-p104">**Usagelocation이** 속성이 유효한 ISO 3166-1 alpha-2 국가 코드를로 설정 하는 사용자 계정에만 라이선스를 할당할 수 있습니다. 예: 대한민국, 미국, 대한민국 및 프랑스에 대 한 FR 합니다. 일부 Office 365 서비스 일부 국가에서는 사용할 수 없습니다. 자세한 내용은 [라이선스 제한에 대 한](https://go.microsoft.com/fwlink/p/?LinkId=691730)참조입니다.</span><span class="sxs-lookup"><span data-stu-id="8e497-p104">You can assign licenses only to user accounts that have the **UsageLocation** property set to a valid ISO 3166-1 alpha-2 country code. For example, US for the United States, and FR for France. Some Office 365 services aren't available in certain countries. For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span></span>
    
    <span data-ttu-id="8e497-p105">**Usagelocation이** 값을 갖지 않는 계정을 찾으려면 명령을 실행 `Get-MsolUser -All | where {$_.UsageLocation -eq $null}`합니다. 계정에 **usagelocation이** 값을 설정 하는 구문을 사용 하 여 `Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>`합니다. 예, `Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US`합니다.</span><span class="sxs-lookup"><span data-stu-id="8e497-p105">To find accounts that don't have a **UsageLocation** value, run the command `Get-MsolUser -All | where {$_.UsageLocation -eq $null}`. To set the **UsageLocation** value on an account, use the syntax `Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>`. For example,  `Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US`.</span></span>
    
- <span data-ttu-id="8e497-122">사용 하지 않고 **Get-msoluser** cmdlet을 사용 하는 경우는 `-All` 매개 변수를 처음 500 개 계정만 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e497-122">If you use the **Get-MsolUser** cmdlet without using the `-All` parameter, only the first 500 accounts are returned.</span></span>

## <a name="assigning-licenses-to-user-accounts"></a><span data-ttu-id="8e497-123">사용자 계정에 라이선스를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="8e497-123">Assigning licenses to user accounts</span></span>
    
<span data-ttu-id="8e497-124">사용자에 게 라이선스를 할당 하려면 Office 365 PowerShell에서 다음 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e497-124">To assign a license to a user, use the following syntax in Office 365 PowerShell:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

<span data-ttu-id="8e497-125">라이선스를 할당 하는이 예제는 `litwareinc:ENTERPRISEPACK` 허가 되지 않은 사용자에 게 라이선스 계획 (Office 365 Enterprise E3) `belindan@litwareinc.com`합니다.</span><span class="sxs-lookup"><span data-stu-id="8e497-125">This example assigns a license from the `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licensing plan to the unlicensed user `belindan@litwareinc.com`.</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="8e497-126">많은 허가 되지 않은 사용자에 게 라이선스를 할당 합니다를 다음 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e497-126">To assign a license to many unlicensed users, use the following syntax:</span></span>
  
```
$x = Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>]; $x | foreach {Set-MsolUserLicense -AddLicenses "<AccountSkuId>"}
```

 <span data-ttu-id="8e497-127">**참고**</span><span class="sxs-lookup"><span data-stu-id="8e497-127">**Notes**</span></span>
  
- <span data-ttu-id="8e497-128">동일한 라이센스 제도에서 여러 라이센스 사용자 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8e497-128">You can't assign multiple licenses to a user from the same licensing plan.</span></span>
    
- <span data-ttu-id="8e497-129">반환 하는 순서 대로 사용자에 게 라이선스 할당 된 충분 한 사용 가능한 라이센스를 설정 하지 않은 경우는 **Get-MsolUser** cmdlet 사용 가능한 라이센스가 실행 될 때까지.</span><span class="sxs-lookup"><span data-stu-id="8e497-129">If you don't have enough available licenses, the licenses are assigned to users in the order that they're returned by the **Get-MsolUser** cmdlet until the available licenses run out.</span></span>
    
<span data-ttu-id="8e497-130">라이선스를 할당 하는이 예제는 `litwareinc:ENTERPRISEPACK` 허가 되지 않은 모든 사용자에 게 라이선스 계획 (Office 365 Enterprise E3).</span><span class="sxs-lookup"><span data-stu-id="8e497-130">This example assigns licenses from the `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licensing plan to all unlicensed users.</span></span>
  
```
$AllUn = Get-MsolUser -All -UnlicensedUsersOnly; $AllUn | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

<span data-ttu-id="8e497-131">미국에서 영업 부서에서 허가 되지 않은 사용자에 게 동일한 라이센스를 지정 하는이 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="8e497-131">This example assigns those same licenses to unlicensed users in the Sales department in the United States.</span></span>
  
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly; $USSales | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```
  
## <a name="new-to-office-365"></a><span data-ttu-id="8e497-132">Office 365의 새로운 기능</span><span class="sxs-lookup"><span data-stu-id="8e497-132">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a><span data-ttu-id="8e497-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8e497-133">See also</span></span>
<span data-ttu-id="8e497-134"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="8e497-134"></span></span>

<span data-ttu-id="8e497-135">Office 365 PowerShell을 사용하여 사용자를 관리하는 방법에 대한 다음 추가 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8e497-135">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="8e497-136">사용자 계정 만들기</span><span class="sxs-lookup"><span data-stu-id="8e497-136">Create user accounts</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="8e497-137">삭제 하 고 사용자 계정 복원</span><span class="sxs-lookup"><span data-stu-id="8e497-137">Delete and restore user accounts</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="8e497-138">블록 사용자 계정</span><span class="sxs-lookup"><span data-stu-id="8e497-138">Block user accounts</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="8e497-139">사용자 계정에서 라이선스를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e497-139">Remove licenses from user accounts</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="8e497-140">이 항목에서 사용된 cmdlet에 대한 자세한 내용은 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="8e497-140">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="8e497-141">Get-msolaccountsku</span><span class="sxs-lookup"><span data-stu-id="8e497-141">Get-MsolAccountSku</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [<span data-ttu-id="8e497-142">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="8e497-142">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="8e497-143">Set-msoluserlicense</span><span class="sxs-lookup"><span data-stu-id="8e497-143">Set-MsolUserLicense</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [<span data-ttu-id="8e497-144">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="8e497-144">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="8e497-145">선택 개체</span><span class="sxs-lookup"><span data-stu-id="8e497-145">Select-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [<span data-ttu-id="8e497-146">Where-Object</span><span class="sxs-lookup"><span data-stu-id="8e497-146">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

