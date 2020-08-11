---
title: PowerShell을 사용 하 여 사용자 계정에 Microsoft 365 라이선스 할당
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/16/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Ent_Office_Other
- LIL_Placement
- PowerShell
- O365ITProTrain
- seo-marvel-apr2020
ms.assetid: ba235f4f-e640-4360-81ea-04507a3a70be
search.appverid:
- MET150
description: 이 문서에서는 PowerShell을 사용 하 여 라이선스가 없는 사용자에 게 Microsoft 365 라이선스를 할당 하는 방법을 알아봅니다.
ms.openlocfilehash: 824d6b786c3334ae36929e50298e6be0aafd9cb2
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606474"
---
# <a name="assign-microsoft-365-licenses-to-user-accounts-with-powershell"></a><span data-ttu-id="ef2b4-103">PowerShell을 사용 하 여 사용자 계정에 Microsoft 365 라이선스 할당</span><span class="sxs-lookup"><span data-stu-id="ef2b4-103">Assign Microsoft 365 licenses to user accounts with PowerShell</span></span>

<span data-ttu-id="ef2b4-104">*이 문서는 Microsoft 365 Enterprise와 Office 365 Enterprise에 모두 적용됩니다.*</span><span class="sxs-lookup"><span data-stu-id="ef2b4-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="ef2b4-105">사용자는 계정에 라이선스 요금제의 라이선스가 할당 되기 전 까지는 Microsoft 365 서비스를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ef2b4-105">Users can't use any Microsoft 365 services until their account has been assigned a license from a licensing plan.</span></span> <span data-ttu-id="ef2b4-106">PowerShell을 사용 하 여 라이선스가 없는 계정에 빠르게 라이선스를 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef2b4-106">You can use PowerShell to quickly assign licenses to unlicensed accounts.</span></span> 

>[!Note]
><span data-ttu-id="ef2b4-107">사용자 계정에는 위치를 할당 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef2b4-107">User accounts must be assigned a location.</span></span> <span data-ttu-id="ef2b4-108">Microsoft 365 관리 센터 또는 PowerShell에서 사용자 계정의 속성을 사용 하 여이 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef2b4-108">You can do this from the properties of a user account in the Microsoft 365 admin center or from PowerShell.</span></span>
>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="ef2b4-109">Graph 모듈용 Azure Active Directory PowerShell 사용하기</span><span class="sxs-lookup"><span data-stu-id="ef2b4-109">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="ef2b4-110">먼저 [Microsoft 365 테 넌 트에 연결](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)합니다.</span><span class="sxs-lookup"><span data-stu-id="ef2b4-110">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  

<span data-ttu-id="ef2b4-111">그런 다음이 명령을 사용 하 여 테 넌 트에 대 한 라이선스 계획을 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef2b4-111">Next, list the license plans for your tenant with this command.</span></span>

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="ef2b4-112">다음으로, UPN (사용자 계정 이름)이 라고도 하는 라이선스를 추가할 계정의 로그인 이름을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ef2b4-112">Next, get the sign-in name of the account to which you want add a license, also known as the user principal name (UPN).</span></span>

<span data-ttu-id="ef2b4-113">다음으로, 사용자 계정에 사용 위치를 할당 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef2b4-113">Next, ensure that the user account has a usage location assigned.</span></span>

```powershell
Get-AzureADUser -ObjectID <user sign-in name (UPN)> | Select DisplayName, UsageLocation
```

<span data-ttu-id="ef2b4-114">사용 위치를 할당 하지 않은 경우 다음 명령을 사용 하 여 할당을 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef2b4-114">If there is no usage location assigned, you can assign one with these commands:</span></span>

```powershell
$userUPN="<user sign-in name (UPN)>"
$userLoc="<ISO 3166-1 alpha-2 country code>"
Set-AzureADUser -ObjectID $userUPN -UsageLocation $userLoc
```

<span data-ttu-id="ef2b4-115">마지막으로 사용자 로그인 이름 및 라이선스 계획 이름을 지정 하 고 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef2b4-115">Finally, specify the user sign-in name and license plan name and run these commands.</span></span>

```powershell
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="ef2b4-116">Windows PowerShell용 Microsoft Azure Active Directory 모듈 사용하기</span><span class="sxs-lookup"><span data-stu-id="ef2b4-116">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="ef2b4-117">먼저 [Microsoft 365 테 넌 트에 연결](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)합니다.</span><span class="sxs-lookup"><span data-stu-id="ef2b4-117">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="ef2b4-118">`Get-MsolAccountSku`사용 가능한 라이선스 계획 및 조직의 각 계획에서 사용 가능한 라이선스 수를 확인 하려면 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef2b4-118">Run the `Get-MsolAccountSku` command to view the available licensing plans and the number of available licenses in each plan in your organization.</span></span> <span data-ttu-id="ef2b4-119">각 계획에서 사용할 수 있는 라이선스의 수는 **activeunits**  -  **WarningUnits**  -  **ConsumedUnits**입니다.</span><span class="sxs-lookup"><span data-stu-id="ef2b4-119">The number of available licenses in each plan is **ActiveUnits** - **WarningUnits** - **ConsumedUnits**.</span></span> <span data-ttu-id="ef2b4-120">라이선스 계획, 라이선스 및 서비스에 대 한 자세한 내용은 PowerShell을 [사용 하 여 라이선스 및 서비스 보기](view-licenses-and-services-with-office-365-powershell.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ef2b4-120">For more information about licensing plans, licenses, and services, see [View licenses and services with PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>

>[!Note]
><span data-ttu-id="ef2b4-121">PowerShell Core는 Windows PowerShell용 Microsoft Azure Active Directory 모듈 및 이름에 **Msol**이 있는 cmdlet을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ef2b4-121">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="ef2b4-122">이러한 cmdlet을 계속 사용하려면 Windows PowerShell에서 이를 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef2b4-122">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="ef2b4-123">조직에서 라이선스가 없는 계정을 찾으려면이 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef2b4-123">To find the unlicensed accounts in your organization, run this command.</span></span>

```powershell
Get-MsolUser -All -UnlicensedUsersOnly
```

<span data-ttu-id="ef2b4-124">**UsageLocation** 속성이 유효한 ISO 3166-1 국가 코드로 설정 된 사용자 계정에만 라이선스를 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef2b4-124">You can only assign licenses to user accounts that have the **UsageLocation** property set to a valid ISO 3166-1 alpha-2 country code.</span></span> <span data-ttu-id="ef2b4-125">예를 들어 미국, 프랑스의 경우 FR을 들을 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef2b4-125">For example, US for the United States, and FR for France.</span></span> <span data-ttu-id="ef2b4-126">일부 Microsoft 365 서비스는 특정 국가에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ef2b4-126">Some Microsoft 365 services aren't available in certain countries.</span></span> <span data-ttu-id="ef2b4-127">자세한 내용은 [사용권 제한 정보](https://go.microsoft.com/fwlink/p/?LinkId=691730)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ef2b4-127">For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span></span>
    
<span data-ttu-id="ef2b4-128">**UsageLocation** 값이 없는 계정을 찾으려면이 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef2b4-128">To find accounts that don't have a **UsageLocation** value, run this command.</span></span>

```powershell
Get-MsolUser -All | where {$_.UsageLocation -eq $null}
```

<span data-ttu-id="ef2b4-129">계정에 **UsageLocation** 값을 설정 하려면 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef2b4-129">To set the **UsageLocation** value on an account, run this command.</span></span>

```powershell
Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>
```

<span data-ttu-id="ef2b4-130">예제:</span><span class="sxs-lookup"><span data-stu-id="ef2b4-130">For example:</span></span>

```powershell
Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US
```
    
<span data-ttu-id="ef2b4-131">**-All** 매개 변수를 사용하지 않고 **Get-MsolUser** cmdlet을 사용하는 경우 처음 500개의 계정만 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef2b4-131">If you use the **Get-MsolUser** cmdlet without using the **-All** parameter, only the first 500 accounts are returned.</span></span>

### <a name="assigning-licenses-to-user-accounts"></a><span data-ttu-id="ef2b4-132">사용자 계정에 라이선스 할당</span><span class="sxs-lookup"><span data-stu-id="ef2b4-132">Assigning licenses to user accounts</span></span>
    
<span data-ttu-id="ef2b4-133">사용자에 게 라이선스를 할당 하려면 PowerShell에서 다음 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef2b4-133">To assign a license to a user, use the following command in PowerShell.</span></span>
  
```powershell
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

<span data-ttu-id="ef2b4-134">이 예에서는 **litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3) 라이선스 계획에서 라이선스가 없는 사용자 **belindan \@ litwareinc.com**에 라이선스를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef2b4-134">This example assigns a license from the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) licensing plan to the unlicensed user **belindan\@litwareinc.com**:</span></span>
  
```powershell
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="ef2b4-135">라이선스가 없는 모든 사용자에 게 라이선스를 할당 하려면이 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef2b4-135">To assign a license to all unlicensed users, run this command.</span></span>
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>] | Set-MsolUserLicense -AddLicenses "<AccountSkuId>"
```
  
>[!Note]
><span data-ttu-id="ef2b4-136">동일한 라이센스 제도에서 여러 라이센스 사용자 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ef2b4-136">You can't assign multiple licenses to a user from the same licensing plan.</span></span> <span data-ttu-id="ef2b4-137">반환 하는 순서 대로 사용자에 게 라이선스 할당 된 충분 한 사용 가능한 라이센스를 설정 하지 않은 경우는 **Get-MsolUser** cmdlet 사용 가능한 라이센스가 실행 될 때까지.</span><span class="sxs-lookup"><span data-stu-id="ef2b4-137">If you don't have enough available licenses, the licenses are assigned to users in the order that they're returned by the **Get-MsolUser** cmdlet until the available licenses run out.</span></span>
>

<span data-ttu-id="ef2b4-138">이 예에서는 **litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3) 라이선스 계획에서 라이선스가 없는 모든 사용자에 게 라이선스를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef2b4-138">This example assigns licenses from the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) licensing plan to all unlicensed users:</span></span>
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="ef2b4-139">이 예에서는 미국의 영업 부서에 있는 라이선스가 없는 사용자에 게 동일한 라이선스를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef2b4-139">This example assigns those same licenses to unlicensed users in the Sales department in the United States:</span></span>
  
```powershell
Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```
  
## <a name="move-a-user-to-a-different-subscription-license-plan-with-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="ef2b4-140">Graph 모듈에 대 한 Azure Active Directory PowerShell을 사용 하 여 다른 구독으로 사용자 이동 (라이선스 계획)</span><span class="sxs-lookup"><span data-stu-id="ef2b4-140">Move a user to a different subscription (license plan) with the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="ef2b4-141">먼저 [Microsoft 365 테 넌 트에 연결](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)합니다.</span><span class="sxs-lookup"><span data-stu-id="ef2b4-141">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
<span data-ttu-id="ef2b4-142">다음으로, UPN (사용자 계정 이름)이 라고도 하는 스위치 구독을 사용할 사용자 계정의 로그인 이름을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ef2b4-142">Next, get the sign-in name of the user account for which you want switch subscriptions, also known as the user principal name (UPN).</span></span>

<span data-ttu-id="ef2b4-143">그런 다음이 명령을 사용 하 여 테 넌 트에 대 한 구독 (라이선스 계획)을 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef2b4-143">Next, list the subscriptions (license plans) for your tenant with this command.</span></span>

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="ef2b4-144">다음으로는 사용자 계정에 현재 이러한 명령이 포함 된 구독을 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef2b4-144">Next, list the subscriptions that the user account currently has with these commands.</span></span>

```powershell
$userUPN="<user account UPN>"
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

<span data-ttu-id="ef2b4-145">현재 사용자가 있는 구독 (보낸 사람 구독)과 사용자가 이동 하는 구독 (TO subscription)을 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef2b4-145">Identify the subscription the user currently has (the FROM subscription) and the subscription to which the user is moving (the TO subscription).</span></span>

<span data-ttu-id="ef2b4-146">마지막으로 TO 및 FROM 구독 이름 (SKU 부분 번호)을 지정 하 고 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef2b4-146">Finally, specify the TO and FROM subscription names (SKU part numbers) and run these commands.</span></span>

```powershell
$subscriptionFrom="<SKU part number of the current subscription>"
$subscriptionTo="<SKU part number of the new subscription>"
# Unassign
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$license.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $subscriptionFrom -EQ).SkuID
$licenses.AddLicenses = $license
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
$licenses.AddLicenses = @()
$licenses.RemoveLicenses =  (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $subscriptionFrom -EQ).SkuID
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
# Assign
$license.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $subscriptionTo -EQ).SkuID
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$licenses.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
```

<span data-ttu-id="ef2b4-147">이러한 명령을 사용 하 여 사용자 계정에 대 한 구독의 변경 내용을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef2b4-147">You can verify the change in subscription for the user account with these commands.</span></span>

```powershell
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

## <a name="see-also"></a><span data-ttu-id="ef2b4-148">기타 참고 항목</span><span class="sxs-lookup"><span data-stu-id="ef2b4-148">See also</span></span>

[<span data-ttu-id="ef2b4-149">PowerShell을 사용 하 여 사용자 계정, 라이선스 및 그룹 관리</span><span class="sxs-lookup"><span data-stu-id="ef2b4-149">Manage user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="ef2b4-150">PowerShell로 Microsoft 365 관리</span><span class="sxs-lookup"><span data-stu-id="ef2b4-150">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="ef2b4-151">Microsoft 365 용 PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="ef2b4-151">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)
