---
title: Office 365 PowerShell을 사용 하 여 사용자 계정에 라이선스를 할당 합니다.
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/29/2019
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
ms.openlocfilehash: ab9b66065e20d0c2d6cfb673dac24ee2ab79e831
ms.sourcegitcommit: 6826e0ea4a777f7d98500209a9d3bc75e89f8d15
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/30/2019
ms.locfileid: "29651185"
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="14a74-103">Office 365 PowerShell을 사용 하 여 사용자 계정에 라이선스를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="14a74-103">Assign licenses to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="14a74-104">**요약:**  Office 365 PowerShell 할당 허가 되지 않은 사용자에 게 Office 365 라이선스를 사용 하는 방법에 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="14a74-104">**Summary:**  Explains how to use Office 365 PowerShell assign an Office 365 license to unlicensed users.</span></span>
  
<span data-ttu-id="14a74-p101">사용자가 자신의 계정이 할당 된 라이선스 라이선스 계획에서 때까지 모든 Office 365 서비스를 사용할 수 없습니다. Office 365 PowerShell을 사용 하 여 신속 하 게 사용 허가 되지 않은 계정에 라이선스를 할당 하 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14a74-p101">Users can't use any Office 365 services until their account has been assigned a license from a licensing plan. You can use Office 365 PowerShell to quickly assign licenses to unlicensed accounts.</span></span> 


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="14a74-107">Graph 모듈용 Azure Active Directory PowerShell 사용하기</span><span class="sxs-lookup"><span data-stu-id="14a74-107">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="14a74-108">먼저, [Office 365 테넌트에 연결](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)합니다.</span><span class="sxs-lookup"><span data-stu-id="14a74-108">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  

<span data-ttu-id="14a74-109">다음으로,이 명령 사용 하 여 테 넌 트에 대 한 라이선스 계획을 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="14a74-109">Next, list the license plans for your tenant with this command.</span></span>

```
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="14a74-110">다음으로도 알려져 사용자 계정 이름 (UPN) 라이선스, 추가 추가할 계정의 로그인 이름을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="14a74-110">Next, get the sign-in name of the account to which you want add a license, also known as the user principal name (UPN).</span></span>

<span data-ttu-id="14a74-111">마지막으로, 사용자 로그인 이름 및 라이선스 계획 이름을 지정 하 고 이러한 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="14a74-111">Finally, specify the user sign-in name and license plan name and run these commands.</span></span>

```
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="14a74-112">Windows PowerShell용 Microsoft Azure Active Directory 모듈 사용하기</span><span class="sxs-lookup"><span data-stu-id="14a74-112">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="14a74-113">먼저, [Office 365 테넌트에 연결](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)합니다.</span><span class="sxs-lookup"><span data-stu-id="14a74-113">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="14a74-p102">조직에서 각 계획에서 사용 가능한 라이선스 계획 및 사용 가능한 라이선스 수를 보려면 **Get-msolaccountsku** 명령을 실행 합니다. 각 계획에서 사용 가능한 라이선스 수가 **ActiveUnits** - **WarningUnits** - **ConsumedUnits**합니다. 계획, 라이선스 및 서비스 라이선스에 대 한 자세한 내용은 [보기 라이선스 및 Office 365 PowerShell을 사용 하 여 서비스를](view-licenses-and-services-with-office-365-powershell.md)참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="14a74-p102">Run the **Get-MsolAccountSku** command to view the available licensing plans and the number of available licenses in each plan in your organization. The number of available licenses in each plan is **ActiveUnits** - **WarningUnits** - **ConsumedUnits**. For more information about licensing plans, licenses, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="14a74-117">조직에서 허가 되지 않은 계정을 찾으려고이 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="14a74-117">To find the unlicensed accounts in your organization, run this command.</span></span>

```
Get-MsolUser -All -UnlicensedUsersOnly
```
    
<span data-ttu-id="14a74-p103">만 **usagelocation이** 속성이 유효한 ISO 3166-1 alpha-2 국가 코드를로 설정 하는 사용자 계정에 라이선스를 할당할 수 있습니다. 예: 대한민국, 미국, 대한민국 및 프랑스에 대 한 FR 합니다. 일부 Office 365 서비스 일부 국가에서는 사용할 수 없습니다. 자세한 내용은 [라이선스 제한에 대 한](https://go.microsoft.com/fwlink/p/?LinkId=691730)참조입니다.</span><span class="sxs-lookup"><span data-stu-id="14a74-p103">You can only assign licenses to user accounts that have the **UsageLocation** property set to a valid ISO 3166-1 alpha-2 country code. For example, US for the United States, and FR for France. Some Office 365 services aren't available in certain countries. For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span></span>
    
<span data-ttu-id="14a74-122">**Usagelocation이** 값을 갖지 않는 계정을이 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="14a74-122">To find accounts that don't have a **UsageLocation** value, run this command.</span></span>

```
Get-MsolUser -All | where {$_.UsageLocation -eq $null}
```

<span data-ttu-id="14a74-123">계정에 **usagelocation이** 값을 설정 하려면이 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="14a74-123">To set the **UsageLocation** value on an account, run this command.</span></span>

```
Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>
```

<span data-ttu-id="14a74-124">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="14a74-124">For example:</span></span>

```
Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US
```
    
<span data-ttu-id="14a74-125">**-All** 매개 변수를 사용하지 않고 **Get-MsolUser** cmdlet을 사용하는 경우 처음 500개의 계정만 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="14a74-125">If you use the **Get-MsolUser** cmdlet without using the **-All** parameter, only the first 500 accounts are returned.</span></span>

### <a name="assigning-licenses-to-user-accounts"></a><span data-ttu-id="14a74-126">사용자 계정에 라이선스를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="14a74-126">Assigning licenses to user accounts</span></span>
    
<span data-ttu-id="14a74-127">사용자에 게 라이선스를 할당 하려면 Office 365 PowerShell에서 다음 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="14a74-127">To assign a license to a user, use the following command in Office 365 PowerShell.</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

<span data-ttu-id="14a74-128">이 예제에서는는 **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) 적절 한 계획을 허가 되지 않은 사용자 **belindan@litwareinc.com**라이선스에서 라이선스를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="14a74-128">This example assigns a license from the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) licensing plan to the unlicensed user **belindan@litwareinc.com**:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="14a74-129">많은 허가 되지 않은 사용자에 게 라이선스를 할당할이 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="14a74-129">To assign a license to many unlicensed users, run this command.</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>] | ForEach {Set-MsolUserLicense -AddLicenses "<AccountSkuId>"}
```
  
>[!Note]
><span data-ttu-id="14a74-p104">동일한 라이선스 계획에서 사용자에 게 여러 라이선스를 할당할 수 없습니다. 충분 한 사용 가능한 라이선스를 설치 하지 않은 경우 사용 가능한 라이선스 실행 될 때까지 **Get-msoluser** cmdlet에 의해 반환 하는 순서는 사용자에 게 라이선스 할당 됩니다.</span><span class="sxs-lookup"><span data-stu-id="14a74-p104">You can't assign multiple licenses to a user from the same licensing plan. If you don't have enough available licenses, the licenses are assigned to users in the order that they're returned by the **Get-MsolUser** cmdlet until the available licenses run out.</span></span>
>

<span data-ttu-id="14a74-132">이 예제에서는 모든 허가 되지 않은 사용자에 게 **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) 라이선스 계획에서 라이선스를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="14a74-132">This example assigns licenses from the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) licensing plan to all unlicensed users:</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly | ForEach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

<span data-ttu-id="14a74-133">이 예제에서는 미국에서 Sales 부서에 허가 되지 않은 사용자에 게 이러한 동일한 라이선스를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="14a74-133">This example assigns those same licenses to unlicensed users in the Sales department in the United States:</span></span>
  
```
Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly | ForEach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```
  
## <a name="new-to-office-365"></a><span data-ttu-id="14a74-134">Office 365의 새로운 기능</span><span class="sxs-lookup"><span data-stu-id="14a74-134">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a><span data-ttu-id="14a74-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="14a74-135">See also</span></span>

[<span data-ttu-id="14a74-136">Office 365 PowerShell로 사용자 계정 및 라이선스 관리</span><span class="sxs-lookup"><span data-stu-id="14a74-136">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="14a74-137">Office 365 PowerShell로 Office 365 관리</span><span class="sxs-lookup"><span data-stu-id="14a74-137">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="14a74-138">Office 365 PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="14a74-138">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
