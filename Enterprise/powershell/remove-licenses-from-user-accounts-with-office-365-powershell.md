---
title: PowerShell을 사용 하 여 사용자 계정에서 Microsoft 365 라이선스 제거
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
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
description: PowerShell을 사용 하 여 이전에 사용자에 게 할당 된 Microsoft 365 라이선스를 제거 하는 방법에 대해 설명 합니다.
ms.openlocfilehash: 5f46cfeb075d83504e3562e60e3dfd70a53dd136
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230394"
---
# <a name="remove-microsoft-365-licenses-from-user-accounts-with-powershell"></a><span data-ttu-id="1eb99-103">PowerShell을 사용 하 여 사용자 계정에서 Microsoft 365 라이선스 제거</span><span class="sxs-lookup"><span data-stu-id="1eb99-103">Remove Microsoft 365 licenses from user accounts with PowerShell</span></span>

<span data-ttu-id="1eb99-104">*이 문서는 Microsoft 365 Enterprise 및 Office 365 Enterprise에 모두 적용 됩니다.*</span><span class="sxs-lookup"><span data-stu-id="1eb99-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="1eb99-105">Graph 모듈용 Azure Active Directory PowerShell 사용하기</span><span class="sxs-lookup"><span data-stu-id="1eb99-105">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="1eb99-106">먼저 [Microsoft 365 테 넌 트에 연결](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)합니다.</span><span class="sxs-lookup"><span data-stu-id="1eb99-106">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>

<span data-ttu-id="1eb99-107">그런 다음이 명령을 사용 하 여 테 넌 트에 대 한 라이선스 계획을 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="1eb99-107">Next, list the license plans for your tenant with this command.</span></span>

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="1eb99-108">다음으로, UPN (사용자 계정 이름)이 라고도 하는 라이선스를 제거할 계정의 로그인 이름을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1eb99-108">Next, get the sign-in name of the account for which you want remove a license, also known as the user principal name (UPN).</span></span>

<span data-ttu-id="1eb99-109">마지막으로 사용자 로그인 및 라이선스 계획 이름을 지정 하 고 "<" 및 ">" 문자를 제거한 후 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="1eb99-109">Finally, specify the user sign-in and license plan names, remove the "<" and ">" characters, and run these commands.</span></span>

```powershell
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$License.RemoveLicenses = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $license
```

<span data-ttu-id="1eb99-110">특정 사용자 계정에 대 한 라이선스를 모두 제거 하려면 사용자 로그인 이름을 지정 하 고 "<" 및 ">" 문자를 제거 하 고 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="1eb99-110">To remove all of the licenses for a specific user account, specify the user sign-in name, remove the "<" and ">" characters, and run these commands.</span></span>

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

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="1eb99-111">Windows PowerShell용 Microsoft Azure Active Directory 모듈 사용하기</span><span class="sxs-lookup"><span data-stu-id="1eb99-111">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="1eb99-112">먼저 [Microsoft 365 테 넌 트에 연결](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)합니다.</span><span class="sxs-lookup"><span data-stu-id="1eb99-112">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
   
<span data-ttu-id="1eb99-113">라이센스 계획 (**AccountSkuID**) 조직에 대 한 정보는 다음 항목을 참조.</span><span class="sxs-lookup"><span data-stu-id="1eb99-113">To view the licensing plan (**AccountSkuID**) information in your organization, see the following topics:</span></span>
    
  - [<span data-ttu-id="1eb99-114">PowerShell을 사용 하 여 라이선스 및 서비스 보기</span><span class="sxs-lookup"><span data-stu-id="1eb99-114">View licenses and services with PowerShell</span></span>](view-licenses-and-services-with-office-365-powershell.md)
    
  - [<span data-ttu-id="1eb99-115">PowerShell을 사용 하 여 계정 라이선스 및 서비스 세부 정보 보기</span><span class="sxs-lookup"><span data-stu-id="1eb99-115">View account license and service details with PowerShell</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
    
<span data-ttu-id="1eb99-116">_-All_ 매개 변수를 사용하지 않고 **Get-MsolUser** cmdlet을 사용하는 경우 처음 500개의 계정만 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="1eb99-116">If you use the **Get-MsolUser** cmdlet without using the _-All_ parameter, only the first 500 accounts are returned.</span></span>
    
### <a name="removing-licenses-from-user-accounts"></a><span data-ttu-id="1eb99-117">사용자 계정에서 라이선스 제거</span><span class="sxs-lookup"><span data-stu-id="1eb99-117">Removing licenses from user accounts</span></span>

<span data-ttu-id="1eb99-118">기존 사용자 계정에서 라이센스를 제거 하려면 다음 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1eb99-118">To remove licenses from an existing user account, use the following syntax:</span></span>
  
```powershell
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

>[!Note]
><span data-ttu-id="1eb99-119">PowerShell Core는 Windows PowerShell용 Microsoft Azure Active Directory 모듈 및 이름에 **Msol**이 있는 cmdlet을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1eb99-119">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="1eb99-120">이러한 cmdlet을 계속 사용하려면 Windows PowerShell에서 이를 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1eb99-120">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="1eb99-121">이 예에서는 사용자 계정 BelindaN@litwareinc.com에서 **litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3) 라이선스를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="1eb99-121">This example removes the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) license from the user account BelindaN@litwareinc.com.</span></span>
  
```powershell
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

>[!Note]
><span data-ttu-id="1eb99-122">`Set-MsolUserLicense`Cmdlet을 사용 하 여 취소 된 라이선스의 사용자 할당을 *취소할* 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1eb99-122">You cannot use the `Set-MsolUserLicense` cmdlet to unassign users from *canceled* licenses.</span></span> <span data-ttu-id="1eb99-123">Microsoft 365 관리 센터에서 각 사용자 계정에 대해 개별적으로이 작업을 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1eb99-123">You must do this individually for each user account in the Microsoft 365 admin center.</span></span>
>

<span data-ttu-id="1eb99-124">기존의 사용이 허가 된 사용자 그룹에서 모든 라이선스를 제거 하려면 다음 방법 중 하나를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1eb99-124">To remove all licenses from a group of existing licensed users, use either of the following methods:</span></span>
  
- <span data-ttu-id="1eb99-125">**기존 계정 특성을 기반으로 계정 필터링** 이 작업을 수행 하려면 다음 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1eb99-125">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
```powershell
$userArray = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
for ($i=0; $i -lt $userArray.Count; $i++)
{
Set-MsolUserLicense -UserPrincipalName $userArray[$i].UserPrincipalName -RemoveLicenses $userArray[$i].licenses.accountskuid
}
```

<span data-ttu-id="1eb99-126">이 예에서는 미국의 영업 부서에 있는 모든 사용자 계정에서 모든 라이선스를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="1eb99-126">This example removes all licenses from all user accounts in the Sales department in the United States.</span></span>
    
```powershell
$userArray = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
for ($i=0; $i -lt $userArray.Count; $i++)
{
Set-MsolUserLicense -UserPrincipalName $userArray[$i].UserPrincipalName -RemoveLicenses $userArray[$i].licenses.accountskuid
}
```

- <span data-ttu-id="1eb99-127">**특정 라이선스에 대 한 특정 계정 목록 사용** 이렇게 하려면 다음 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="1eb99-127">**Use a list of specific accounts for a specific license** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="1eb99-128">만들고 다음과 같이 각 줄에 한 계정에 포함 된 텍스트 파일을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="1eb99-128">Create and save a text file that contains one account on each line like this:</span></span>
    
  ```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

2. <span data-ttu-id="1eb99-129">다음 구문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1eb99-129">Use the following syntax:</span></span>
    
  ```powershell
  $x=Get-Content "<FileNameAndPath>"
  for ($i=0; $i -lt $x.Count; $i++)
  {
  Set-MsolUserLicense -UserPrincipalName $x[$i] -RemoveLicenses "<AccountSkuId1>","<AccountSkuId2>"...
  }
  ```
<span data-ttu-id="1eb99-130">이 예에서는 텍스트 파일 C:\My Documents\Accounts.txt에 정의 된 사용자 계정에서 **litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3) 라이선스를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="1eb99-130">This example removes the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) license from the user accounts defined in the text file C:\My Documents\Accounts.txt.</span></span>
    
  ```powershell
  $x=Get-Content "C:\My Documents\Accounts.txt"
  for ($i=0; $i -lt $x.Count; $i++)
  {
  Set-MsolUserLicense -UserPrincipalName $x[$i] -RemoveLicenses "litwareinc:ENTERPRISEPACK"
  }
  ```

<span data-ttu-id="1eb99-131">모든 기존 사용자 계정에서 모든 라이선스를 제거 하려면 다음 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1eb99-131">To remove all licenses from all existing user accounts, use the following syntax:</span></span>
  
```powershell
$userArray = Get-MsolUser -All | where {$_.isLicensed -eq $true}
for ($i=0; $i -lt $userArray.Count; $i++)
{
Set-MsolUserLicense -UserPrincipalName $userArray[$i].UserPrincipalName -RemoveLicenses $userArray[$i].licenses.accountskuid
}
```

<span data-ttu-id="1eb99-132">라이선스를 회수하는 또 다른 방법은 사용자 계정을 삭제하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="1eb99-132">Another way to free up a license is by deleting the user account.</span></span> <span data-ttu-id="1eb99-133">자세한 내용은 [With PowerShell을 사용 하 여 사용자 계정 삭제 및 복원을](delete-and-restore-user-accounts-with-office-365-powershell.md)참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1eb99-133">For more information, see [Delete and restore user accounts with PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="1eb99-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1eb99-134">See also</span></span>

[<span data-ttu-id="1eb99-135">PowerShell을 사용 하 여 Microsoft 365 사용자 계정, 라이선스 및 그룹 관리</span><span class="sxs-lookup"><span data-stu-id="1eb99-135">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="1eb99-136">PowerShell을 사용 하 여 Microsoft 365 관리</span><span class="sxs-lookup"><span data-stu-id="1eb99-136">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="1eb99-137">Microsoft 365 용 PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="1eb99-137">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)

