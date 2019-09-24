---
title: Office 365 PowerShell을 사용 하 여 사용자 계정에 라이선스를 할당 합니다.
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 08/05/2019
audience: Admin
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
search.appverid:
- MET150
description: Office 365 PowerShell을 사용 하 여 허가 되지 않은 사용자에 게 Office 365 라이선스를 할당 하는 방법
ms.openlocfilehash: 4351feaa1dbe9d657ed8df54a74410991834ea5d
ms.sourcegitcommit: c16ab90d0b9902228ce4337f1c64900592936cce
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/23/2019
ms.locfileid: "37108218"
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="1e233-103">Office 365 PowerShell을 사용 하 여 사용자 계정에 라이선스를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e233-103">Assign licenses to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="1e233-104">**요약:**  Office 365 PowerShell을 사용 하 여 허가 되지 않은 사용자에 게 Office 365 라이선스를 할당 하는 방법</span><span class="sxs-lookup"><span data-stu-id="1e233-104">**Summary:**  How to use Office 365 PowerShell to assign an Office 365 license to unlicensed users.</span></span>
  
<span data-ttu-id="1e233-105">사용자는 계정에 라이선스 요금제의 라이선스가 할당 되기 전 까지는 모든 Office 365 서비스를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1e233-105">Users can't use any Office 365 services until their account has been assigned a license from a licensing plan.</span></span> <span data-ttu-id="1e233-106">Office 365 PowerShell을 사용 하 여 라이선스가 없는 계정에 빠르게 라이선스를 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e233-106">You can use Office 365 PowerShell to quickly assign licenses to unlicensed accounts.</span></span> 

>[!Note]
><span data-ttu-id="1e233-107">사용자 계정에는 위치를 할당 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e233-107">User accounts must be assigned a location.</span></span> <span data-ttu-id="1e233-108">Microsoft 365 관리 센터 또는 PowerShell에서 사용자 계정의 속성을 사용 하 여이 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e233-108">You can do this from the properties of a user account in the Microsoft 365 admin center or from PowerShell.</span></span>
>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="1e233-109">Graph 모듈용 Azure Active Directory PowerShell 사용하기</span><span class="sxs-lookup"><span data-stu-id="1e233-109">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="1e233-110">먼저, [Office 365 테넌트에 연결](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)합니다.</span><span class="sxs-lookup"><span data-stu-id="1e233-110">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  

<span data-ttu-id="1e233-111">그런 다음이 명령을 사용 하 여 테 넌 트에 대 한 라이선스 계획을 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e233-111">Next, list the license plans for your tenant with this command.</span></span>

```
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="1e233-112">다음으로, UPN (사용자 계정 이름)이 라고도 하는 라이선스를 추가할 계정의 로그인 이름을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1e233-112">Next, get the sign-in name of the account to which you want add a license, also known as the user principal name (UPN).</span></span>

<span data-ttu-id="1e233-113">다음으로, 사용자 계정에 사용 위치를 할당 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e233-113">Next, ensure that the user account has a usage location assigned.</span></span>

```
Get-AzureADUser -ObjectID <user sign-in name (UPN)> | Select DisplayName, UsageLocation
```

<span data-ttu-id="1e233-114">사용 위치를 할당 하지 않은 경우 다음 명령을 사용 하 여 할당을 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e233-114">If there is no usage location assigned, you can assign one with these commands:</span></span>

```
$userUPN="<user sign-in name (UPN)>"
$userLoc="<ISO 3166-1 alpha-2 country code>"
Set-AzureADUser -ObjectID $userUPN -UsageLocation $userLoc
```

<span data-ttu-id="1e233-115">마지막으로 사용자 로그인 이름 및 라이선스 계획 이름을 지정 하 고 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e233-115">Finally, specify the user sign-in name and license plan name and run these commands.</span></span>

```
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="1e233-116">Windows PowerShell용 Microsoft Azure Active Directory 모듈 사용하기</span><span class="sxs-lookup"><span data-stu-id="1e233-116">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="1e233-117">먼저, [Office 365 테넌트에 연결](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)합니다.</span><span class="sxs-lookup"><span data-stu-id="1e233-117">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="1e233-118">**Get-get-msolaccountsku** 명령을 실행 하 여 조직의 각 계획에서 사용할 수 있는 라이선스 계획 및 사용 가능한 라이선스 수를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e233-118">Run the **Get-MsolAccountSku** command to view the available licensing plans and the number of available licenses in each plan in your organization.</span></span> <span data-ttu-id="1e233-119">각 계획에서 사용할 수 있는 라이선스의 수는 **activeunits** - **WarningUnits** - **ConsumedUnits**입니다.</span><span class="sxs-lookup"><span data-stu-id="1e233-119">The number of available licenses in each plan is **ActiveUnits** - **WarningUnits** - **ConsumedUnits**.</span></span> <span data-ttu-id="1e233-120">라이선스 계획, 라이선스 및 서비스에 대 한 자세한 내용은 [Office 365 PowerShell을 사용 하 여 라이선스 및 서비스 보기](view-licenses-and-services-with-office-365-powershell.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1e233-120">For more information about licensing plans, licenses, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="1e233-121">조직에서 라이선스가 없는 계정을 찾으려면이 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e233-121">To find the unlicensed accounts in your organization, run this command.</span></span>

```
Get-MsolUser -All -UnlicensedUsersOnly
```

<span data-ttu-id="1e233-122">**UsageLocation** 속성이 유효한 ISO 3166-1 국가 코드로 설정 된 사용자 계정에만 라이선스를 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e233-122">You can only assign licenses to user accounts that have the **UsageLocation** property set to a valid ISO 3166-1 alpha-2 country code.</span></span> <span data-ttu-id="1e233-123">예를 들어 미국, 프랑스의 경우 FR을 들을 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e233-123">For example, US for the United States, and FR for France.</span></span> <span data-ttu-id="1e233-124">일부 Office 365 서비스는 특정 국가에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1e233-124">Some Office 365 services aren't available in certain countries.</span></span> <span data-ttu-id="1e233-125">자세한 내용은 [사용권 제한 정보](https://go.microsoft.com/fwlink/p/?LinkId=691730)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1e233-125">For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span></span>
    
<span data-ttu-id="1e233-126">**UsageLocation** 값이 없는 계정을 찾으려면이 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e233-126">To find accounts that don't have a **UsageLocation** value, run this command.</span></span>

```
Get-MsolUser -All | where {$_.UsageLocation -eq $null}
```

<span data-ttu-id="1e233-127">계정에 **UsageLocation** 값을 설정 하려면 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e233-127">To set the **UsageLocation** value on an account, run this command.</span></span>

```
Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>
```

<span data-ttu-id="1e233-128">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1e233-128">For example:</span></span>

```
Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US
```
    
<span data-ttu-id="1e233-129">**-All** 매개 변수를 사용하지 않고 **Get-MsolUser** cmdlet을 사용하는 경우 처음 500개의 계정만 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e233-129">If you use the **Get-MsolUser** cmdlet without using the **-All** parameter, only the first 500 accounts are returned.</span></span>

### <a name="assigning-licenses-to-user-accounts"></a><span data-ttu-id="1e233-130">사용자 계정에 라이선스 할당</span><span class="sxs-lookup"><span data-stu-id="1e233-130">Assigning licenses to user accounts</span></span>
    
<span data-ttu-id="1e233-131">사용자에 게 라이선스를 할당 하려면 Office 365 PowerShell에서 다음 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e233-131">To assign a license to a user, use the following command in Office 365 PowerShell.</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

<span data-ttu-id="1e233-132">이 예에서는 **litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3) 라이선스 계획에서 라이선스가 없는 사용자 **\@belindan litwareinc.com**에 라이선스를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e233-132">This example assigns a license from the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) licensing plan to the unlicensed user **belindan\@litwareinc.com**:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="1e233-133">라이선스가 너무 많은 사용자에 게 라이선스를 할당 하려면이 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e233-133">To assign a license to many unlicensed users, run this command.</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>] | Set-MsolUserLicense -AddLicenses "<AccountSkuId>"
```
  
>[!Note]
><span data-ttu-id="1e233-134">동일한 라이센스 제도에서 여러 라이센스 사용자 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1e233-134">You can't assign multiple licenses to a user from the same licensing plan.</span></span> <span data-ttu-id="1e233-135">반환 하는 순서 대로 사용자에 게 라이선스 할당 된 충분 한 사용 가능한 라이센스를 설정 하지 않은 경우는 **Get-MsolUser** cmdlet 사용 가능한 라이센스가 실행 될 때까지.</span><span class="sxs-lookup"><span data-stu-id="1e233-135">If you don't have enough available licenses, the licenses are assigned to users in the order that they're returned by the **Get-MsolUser** cmdlet until the available licenses run out.</span></span>
>

<span data-ttu-id="1e233-136">이 예에서는 **litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3) 라이선스 계획에서 라이선스가 없는 모든 사용자에 게 라이선스를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e233-136">This example assigns licenses from the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) licensing plan to all unlicensed users:</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="1e233-137">이 예에서는 미국의 영업 부서에 있는 라이선스가 없는 사용자에 게 동일한 라이선스를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e233-137">This example assigns those same licenses to unlicensed users in the Sales department in the United States:</span></span>
  
```
Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```
  
## <a name="new-to-office-365"></a><span data-ttu-id="1e233-138">Office 365의 새로운 기능</span><span class="sxs-lookup"><span data-stu-id="1e233-138">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a><span data-ttu-id="1e233-139">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1e233-139">See also</span></span>

[<span data-ttu-id="1e233-140">Office 365 PowerShell로 사용자 계정 및 라이선스 관리</span><span class="sxs-lookup"><span data-stu-id="1e233-140">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="1e233-141">Office 365 PowerShell을 사용하여 Office 365 관리</span><span class="sxs-lookup"><span data-stu-id="1e233-141">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="1e233-142">Office 365 PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="1e233-142">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
