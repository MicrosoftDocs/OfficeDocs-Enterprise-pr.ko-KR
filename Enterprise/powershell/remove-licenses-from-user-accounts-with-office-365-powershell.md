---
title: Office 365 PowerShell을 사용 하 여 사용자 계정에서 라이센스를 제거 합니다.
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/26/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
- O365ITProTrain
ms.assetid: e7e4dc5e-e299-482c-9414-c265e145134f
description: Office 365 PowerShell을 사용 하 여 이전에 사용자에 게 할당 된 Office 365 라이선스를 제거 하는 방법에 대해 설명 합니다.
ms.openlocfilehash: f5b1dc18dfd53548d1e49a3193315acc0343f816
ms.sourcegitcommit: 0c2d4cfb4d1b21ea93bcc6eb52421548db34b1e6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/27/2020
ms.locfileid: "44374457"
---
# <a name="remove-licenses-from-user-accounts-with-office-365-powershell"></a><span data-ttu-id="0b736-103">Office 365 PowerShell을 사용 하 여 사용자 계정에서 라이센스를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b736-103">Remove licenses from user accounts with Office 365 PowerShell</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="0b736-104">Graph 모듈용 Azure Active Directory PowerShell 사용하기</span><span class="sxs-lookup"><span data-stu-id="0b736-104">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="0b736-105">먼저, [Office 365 테넌트에 연결](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)합니다.</span><span class="sxs-lookup"><span data-stu-id="0b736-105">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>

<span data-ttu-id="0b736-106">그런 다음이 명령을 사용 하 여 테 넌 트에 대 한 라이선스 계획을 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b736-106">Next, list the license plans for your tenant with this command.</span></span>

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="0b736-107">다음으로, UPN (사용자 계정 이름)이 라고도 하는 라이선스를 제거할 계정의 로그인 이름을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0b736-107">Next, get the sign-in name of the account for which you want remove a license, also known as the user principal name (UPN).</span></span>

<span data-ttu-id="0b736-108">마지막으로 사용자 로그인 및 라이선스 계획 이름을 지정 하 고 "<" 및 ">" 문자를 제거한 후 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b736-108">Finally, specify the user sign-in and license plan names, remove the "<" and ">" characters, and run these commands.</span></span>

```powershell
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$license.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
$licenses.AddLicenses = $license
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
$Licenses.AddLicenses = @()
$Licenses.RemoveLicenses =  (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
```

<span data-ttu-id="0b736-109">특정 사용자 계정에 대 한 라이선스를 모두 제거 하려면 사용자 로그인 이름을 지정 하 고 "<" 및 ">" 문자를 제거 하 고 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b736-109">To remove all of the licenses for a specific user account, specify the user sign-in name, remove the "<" and ">" characters, and run these commands.</span></span>

```powershell
$userUPN="<user sign-in name (UPN)>"
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID
if($userList.Count -ne 0) {
if($userList -is [array]) {
for ($i=0; $i -lt $userList.Count; $i++) {
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$license.SkuId = $userList[$i].SkuId
$licenses.AddLicenses = $license
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
$Licenses.AddLicenses = @()
$Licenses.RemoveLicenses =  (Get-AzureADSubscribedSku | Where-Object -Property SkuID -Value $userList[$i].SkuId -EQ).SkuID
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
}
} else {
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$license.SkuId = $userList.SkuId
$licenses.AddLicenses = $license
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
$Licenses.AddLicenses = @()
$Licenses.RemoveLicenses =  (Get-AzureADSubscribedSku | Where-Object -Property SkuID -Value $userList.SkuId -EQ).SkuID
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
}}
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="0b736-110">Windows PowerShell용 Microsoft Azure Active Directory 모듈 사용하기</span><span class="sxs-lookup"><span data-stu-id="0b736-110">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="0b736-111">먼저, [Office 365 테넌트에 연결](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)합니다.</span><span class="sxs-lookup"><span data-stu-id="0b736-111">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
   
<span data-ttu-id="0b736-112">라이센스 계획 (**AccountSkuID**) 조직에 대 한 정보는 다음 항목을 참조.</span><span class="sxs-lookup"><span data-stu-id="0b736-112">To view the licensing plan (**AccountSkuID**) information in your organization, see the following topics:</span></span>
    
  - [<span data-ttu-id="0b736-113">라이선스 및 Office 365 PowerShell을 사용 하 여 서비스를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b736-113">View licenses and services with Office 365 PowerShell</span></span>](view-licenses-and-services-with-office-365-powershell.md)
    
  - [<span data-ttu-id="0b736-114">Office 365 PowerShell을 사용 하 여 계정 라이센스와 서비스 정보 보기</span><span class="sxs-lookup"><span data-stu-id="0b736-114">View account license and service details with Office 365 PowerShell</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
    
<span data-ttu-id="0b736-115">_-All_ 매개 변수를 사용하지 않고 **Get-MsolUser** cmdlet을 사용하는 경우 처음 500개의 계정만 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b736-115">If you use the **Get-MsolUser** cmdlet without using the _-All_ parameter, only the first 500 accounts are returned.</span></span>
    
### <a name="removing-licenses-from-user-accounts"></a><span data-ttu-id="0b736-116">사용자 계정에서 라이선스 제거</span><span class="sxs-lookup"><span data-stu-id="0b736-116">Removing licenses from user accounts</span></span>

<span data-ttu-id="0b736-117">기존 사용자 계정에서 라이센스를 제거 하려면 다음 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b736-117">To remove licenses from an existing user account, use the following syntax:</span></span>
  
```powershell
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

>[!Note]
><span data-ttu-id="0b736-118">PowerShell Core는 Windows PowerShell용 Microsoft Azure Active Directory 모듈 및 이름에 **Msol**이 있는 cmdlet을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0b736-118">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="0b736-119">이러한 cmdlet을 계속 사용하려면 Windows PowerShell에서 이를 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b736-119">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="0b736-120">이 예에서는 사용자 계정 BelindaN@litwareinc.com에서 **litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3) 라이선스를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b736-120">This example removes the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) license from the user account BelindaN@litwareinc.com.</span></span>
  
```powershell
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

>[!Note]
><span data-ttu-id="0b736-121">`Set-MsolUserLicense`Cmdlet을 사용 하 여 취소 된 라이선스의 사용자 할당을 *취소할* 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0b736-121">You cannot use the `Set-MsolUserLicense` cmdlet to unassign users from *canceled* licenses.</span></span> <span data-ttu-id="0b736-122">Microsoft 365 관리 센터에서 각 사용자 계정에 대해 개별적으로이 작업을 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b736-122">You must do this individually for each user account in the Microsoft 365 admin center.</span></span>
>

<span data-ttu-id="0b736-123">기존의 사용이 허가 된 사용자 그룹에서 모든 라이선스를 제거 하려면 다음 방법 중 하나를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b736-123">To remove all licenses from a group of existing licensed users, use either of the following methods:</span></span>
  
- <span data-ttu-id="0b736-124">**기존 계정 특성을 기반으로 계정 필터링** 이 작업을 수행 하려면 다음 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b736-124">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
```powershell
$userArray = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
for ($i=0; $i -lt $userArray.Count; $i++)
{
Set-MsolUserLicense -UserPrincipalName $userArray[$i].UserPrincipalName -RemoveLicenses $userArray[$i].licenses.accountskuid
}
```

<span data-ttu-id="0b736-125">이 예에서는 미국의 영업 부서에 있는 모든 사용자 계정에서 모든 라이선스를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b736-125">This example removes all licenses from all user accounts in the Sales department in the United States.</span></span>
    
```powershell
$userArray = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
for ($i=0; $i -lt $userArray.Count; $i++)
{
Set-MsolUserLicense -UserPrincipalName $userArray[$i].UserPrincipalName -RemoveLicenses $userArray[$i].licenses.accountskuid
}
```

- <span data-ttu-id="0b736-126">**특정 라이선스에 대 한 특정 계정 목록 사용** 이렇게 하려면 다음 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b736-126">**Use a list of specific accounts for a specific license** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="0b736-127">만들고 다음과 같이 각 줄에 한 계정에 포함 된 텍스트 파일을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b736-127">Create and save a text file that contains one account on each line like this:</span></span>
    
  ```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

2. <span data-ttu-id="0b736-128">다음 구문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0b736-128">Use the following syntax:</span></span>
    
  ```powershell
  $x=Get-Content "<FileNameAndPath>"
  for ($i=0; $i -lt $x.Count; $i++)
  {
  Set-MsolUserLicense -UserPrincipalName $x[$i] -RemoveLicenses "<AccountSkuId1>","<AccountSkuId2>"...
  }
  ```
<span data-ttu-id="0b736-129">이 예에서는 텍스트 파일 C:\My Documents\accounts.txt입니다 .에 정의 된 사용자 계정에서 **litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3) 라이선스를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b736-129">This example removes the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) license from the user accounts defined in the text file C:\My Documents\Accounts.txt.</span></span>
    
  ```powershell
  $x=Get-Content "C:\My Documents\Accounts.txt"
  for ($i=0; $i -lt $x.Count; $i++)
  {
  Set-MsolUserLicense -UserPrincipalName $x[$i] -RemoveLicenses "litwareinc:ENTERPRISEPACK"
  }
  ```

<span data-ttu-id="0b736-130">모든 기존 사용자 계정에서 모든 라이선스를 제거 하려면 다음 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b736-130">To remove all licenses from all existing user accounts, use the following syntax:</span></span>
  
```powershell
$userArray = Get-MsolUser -All | where {$_.isLicensed -eq $true}
for ($i=0; $i -lt $userArray.Count; $i++)
{
Set-MsolUserLicense -UserPrincipalName $userArray[$i].UserPrincipalName -RemoveLicenses $userArray[$i].licenses.accountskuid
}
```

<span data-ttu-id="0b736-131">라이선스를 회수하는 또 다른 방법은 사용자 계정을 삭제하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0b736-131">Another way to free up a license is by deleting the user account.</span></span> <span data-ttu-id="0b736-132">자세한 내용은 [Office 365 PowerShell을 사용 하 여 사용자 계정 삭제 및 복원을](delete-and-restore-user-accounts-with-office-365-powershell.md)참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0b736-132">For more information, see [Delete and restore user accounts with Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="0b736-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0b736-133">See also</span></span>

[<span data-ttu-id="0b736-134">Office 365 PowerShell을 사용 하 여 사용자 계정, 라이선스 및 그룹 관리</span><span class="sxs-lookup"><span data-stu-id="0b736-134">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="0b736-135">Office 365 PowerShell을 사용하여 Office 365 관리</span><span class="sxs-lookup"><span data-stu-id="0b736-135">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="0b736-136">Office 365 PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="0b736-136">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

