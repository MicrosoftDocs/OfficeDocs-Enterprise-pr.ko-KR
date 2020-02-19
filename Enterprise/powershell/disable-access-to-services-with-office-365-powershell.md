---
title: Office 365 PowerShell을 사용 하 여 서비스에 대 한 액세스를 비활성화 합니다.
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/17/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Ent_Office_Other
- PowerShell
- LIL_Placement
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: Office 365 PowerShell을 사용 하 여 사용자의 Office 365 서비스에 대 한 액세스를 사용 하지 않도록 설정 합니다.
ms.openlocfilehash: 17927b6d7e402aff66c059e159ae81a950667ad1
ms.sourcegitcommit: e2f7bb4ccd4c74902235f680104ca6b56c051587
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/19/2020
ms.locfileid: "42106219"
---
# <a name="disable-access-to-services-with-office-365-powershell"></a><span data-ttu-id="22d04-103">Office 365 PowerShell을 사용 하 여 서비스에 대 한 액세스를 비활성화 합니다.</span><span class="sxs-lookup"><span data-stu-id="22d04-103">Disable access to services with Office 365 PowerShell</span></span>

<span data-ttu-id="22d04-104">Office 365 계정에 라이선스 계획의 라이선스가 할당 되 면 해당 라이선스의 사용자가 Office 365 서비스를 사용할 수 있게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="22d04-104">When an Office 365 account is assigned a license from a licensing plan, Office 365 services are made available to the user from that license.</span></span> <span data-ttu-id="22d04-105">그러나 사용자가 액세스할 수 있는 Office 365 서비스는 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22d04-105">However, you can control the Office 365 services that the user can access.</span></span> <span data-ttu-id="22d04-106">예를 들어 라이선스를 사용 하 여 SharePoint Online 서비스에 액세스할 수 있는 경우에도 액세스를 사용 하지 않도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22d04-106">For example, even though the license allows access to the SharePoint Online service, you can disable access to it.</span></span> <span data-ttu-id="22d04-107">PowerShell을 사용 하 여 특정 라이선스 계획에 대 한 모든 서비스에 대 한 액세스를 사용 하지 않도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22d04-107">You can use PowerShell to disable access to any number of services for a specific licensing plan for:</span></span>

- <span data-ttu-id="22d04-108">개별 계정</span><span class="sxs-lookup"><span data-stu-id="22d04-108">An individual account.</span></span>
- <span data-ttu-id="22d04-109">계정 그룹</span><span class="sxs-lookup"><span data-stu-id="22d04-109">A group of accounts.</span></span>
- <span data-ttu-id="22d04-110">조직의 모든 계정입니다.</span><span class="sxs-lookup"><span data-stu-id="22d04-110">All accounts in your organization.</span></span>

>[!Note]
><span data-ttu-id="22d04-111">다른 서비스가 종속 되어 있을 때 지정 된 서비스를 사용 하지 않도록 설정할 수 있는 Office 365 서비스 종속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22d04-111">There are Office 365 service dependencies that can prevent you from disabling a specified service when other services depend on it.</span></span>
>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="22d04-112">Windows PowerShell용 Microsoft Azure Active Directory 모듈 사용하기</span><span class="sxs-lookup"><span data-stu-id="22d04-112">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="22d04-113">먼저, [Office 365 테넌트에 연결](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)합니다.</span><span class="sxs-lookup"><span data-stu-id="22d04-113">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="22d04-114">다음으로, 다음 명령을 사용 하 여 Account과 Uid 라고도 하는 사용 가능한 라이선스 계획을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="22d04-114">Next, use this command to view your available licensing plans, also known as AccountSkuIds:</span></span>

```powershell
Get-MsolAccountSku | Select AccountSkuId | Sort AccountSkuId
```

>[!Note]
><span data-ttu-id="22d04-115">PowerShell Core는 Windows PowerShell용 Microsoft Azure Active Directory 모듈 및 이름에 **Msol**이 있는 cmdlet을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="22d04-115">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="22d04-116">이러한 cmdlet을 계속 사용하려면 Windows PowerShell에서 이를 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="22d04-116">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="22d04-117">자세한 내용은 [Office 365 PowerShell을 사용 하 여 라이선스 및 서비스 보기](view-licenses-and-services-with-office-365-powershell.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="22d04-117">For more information, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="22d04-118">이 항목에서 설명 하는 절차의 이전 및 후 결과를 보려면 [Office 365 PowerShell을 사용 하 여 계정 라이선스 및 서비스 세부 정보 보기](view-account-license-and-service-details-with-office-365-powershell.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="22d04-118">To see the before and after results of the procedures in this topic, see [View account license and service details with Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="22d04-119">이 항목에서 설명하는 절차를 자동화하는 PowerShell 스크립트를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22d04-119">A PowerShell script is available that automates the procedures described in this topic.</span></span> <span data-ttu-id="22d04-120">특히이 스크립트를 사용 하면 Sway를 포함 하 여 Office 365 조직에서 서비스를 확인 하 고 사용 하지 않도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22d04-120">Specifically, the script lets you view and disable services in your Office 365 organization, including Sway.</span></span> <span data-ttu-id="22d04-121">자세한 내용은 [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="22d04-121">For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
    
    
### <a name="disable-specific-office-365-services-for-specific-users-for-a-specific-licensing-plan"></a><span data-ttu-id="22d04-122">특정 라이선스 계획에 대해 특정 사용자에 대해 특정 Office 365 서비스를 사용 하지 않도록 설정</span><span class="sxs-lookup"><span data-stu-id="22d04-122">Disable specific Office 365 services for specific users for a specific licensing plan</span></span>
  
<span data-ttu-id="22d04-123">특정 라이선스 계획에 대해 사용자에 대해 특정 Office 365 서비스 집합을 사용 하지 않도록 설정 하려면 다음 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="22d04-123">To disable a specific set of Office 365 services for users for a specific licensing plan, perform the following steps:</span></span>
  
#### <a name="step-1-identify-the-undesirable-services-in-the-licensing-plan-by-using-the-following-syntax"></a><span data-ttu-id="22d04-124">1 단계: 다음 구문을 사용 하 여 라이선스 계획에서 원하지 않는 서비스를 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="22d04-124">Step 1: Identify the undesirable services in the licensing plan by using the following syntax:</span></span>
    
```powershell
$LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
```

<span data-ttu-id="22d04-125">다음 예제에서는 라는 `litwareinc:ENTERPRISEPACK` 라이선스 계획에서 Office 및 SharePoint Online 서비스를 사용 하지 않도록 설정 하는 **LicenseOptions** 개체 (office 365 Enterprise E3)를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="22d04-125">The following example creates a **LicenseOptions** object that disables the Office and SharePoint Online services in the licensing plan named `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).</span></span>
    
```powershell
$LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
```

#### <a name="step-2-use-the-licenseoptions-object-from-step-1-on-one-or-more-users"></a><span data-ttu-id="22d04-126">2 단계: 한 명 이상의 사용자에 대해 1 단계의 **LicenseOptions** 개체를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="22d04-126">Step 2: Use the **LicenseOptions** object from Step 1 on one or more users.</span></span>
    
<span data-ttu-id="22d04-127">서비스를 사용 하지 않도록 설정 된 새 계정을 만들려면 다음 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="22d04-127">To create a new account that has the services disabled, use the following syntax:</span></span>
    
```powershell
New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
```

<span data-ttu-id="22d04-128">다음 예에서는 라이선스를 할당 하 고 1 단계에서 설명 하는 서비스를 사용 하지 않도록 설정 하는 Allie에 대 한 새 계정을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="22d04-128">The following example creates a new account for Allie Bellew that assigns the license and disables the services described in Step 1.</span></span>
    
```powershell
New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
```

<span data-ttu-id="22d04-129">Office 365 PowerShell에서 사용자 계정을 만드는 방법에 대 한 자세한 내용은 [Create user accounts With office 365 powershell](create-user-accounts-with-office-365-powershell.md)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="22d04-129">For more information about creating user accounts in Office 365 PowerShell, see [Create user accounts with Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="22d04-130">사용이 허가 된 기존 사용자에 대 한 서비스를 사용 하지 않도록 설정 하려면 다음 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="22d04-130">To disable the services for an existing licensed user, use the following syntax:</span></span>
    
```powershell
Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
```

<span data-ttu-id="22d04-131">이 예에서는 사용자 BelindaN@litwareinc.com에 대 한 서비스를 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="22d04-131">This example disables the services for the user BelindaN@litwareinc.com.</span></span>
    
```powershell
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
```

<span data-ttu-id="22d04-132">사용이 허가 된 모든 사용자에 대해 1 단계에서 설명 하는 서비스를 사용 하지 않도록 설정 하려면 **get-msolaccountsku** cmdlet (예: **litwareinc**)의 표시에서 Office 365 계획의 이름을 지정 하 고 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="22d04-132">To disable the services described in Step 1 for all existing licensed users, specify the name of your Office 365 plan from the display of the **Get-MsolAccountSku** cmdlet (such as **litwareinc:ENTERPRISEPACK**), and then run the following commands:</span></span>
    
```powershell
$acctSKU="<AccountSkuId>"
$AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses.AccountSku.SkuPartNumber -contains ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
$AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

 <span data-ttu-id="22d04-133">_All_ 매개 변수를 사용 하지 않고 **get-msoluser** cmdlet을 사용 하는 경우에는 첫 번째 500 사용자 계정만 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="22d04-133">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 user accounts are returned.</span></span>

<span data-ttu-id="22d04-134">기존 사용자 그룹에 대 한 서비스를 사용 하지 않도록 설정 하려면 다음 방법 중 하나를 사용 하 여 사용자를 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="22d04-134">To disable the services for a group of existing users, use either of the following methods to identify the users:</span></span>
    
<span data-ttu-id="22d04-135">**방법 1 기존 계정 특성을 기반으로 계정 필터링**</span><span class="sxs-lookup"><span data-stu-id="22d04-135">**Method 1. Filter the accounts based on an existing account attribute**</span></span> 

<span data-ttu-id="22d04-136">그렇게 하려면 다음 구문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="22d04-136">To do this, use the following syntax:</span></span>
    
```powershell
$x = Get-MsolUser -All <FilterableAttributes>
$x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

<span data-ttu-id="22d04-137">다음 예에서는 미국 영업부에 있는 사용자에 대 한 서비스를 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="22d04-137">The following example disables the services for users in the Sales department in the United States.</span></span>
    
```powershell
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
$USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

<span data-ttu-id="22d04-138">**방법 2: 특정 계정 목록 사용**</span><span class="sxs-lookup"><span data-stu-id="22d04-138">**Method 2: Use a list of specific accounts**</span></span> 

<span data-ttu-id="22d04-139">이 작업을 수행 하려면 다음 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="22d04-139">To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="22d04-140">다음과 같이 각 줄에 한 계정에 포함 된 텍스트 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="22d04-140">Create a text file that contains one account on each line like this:</span></span>
    
  ```powershell
  akol@contoso.com
  tjohnston@contoso.com
  kakers@contoso.com
  ```

  <span data-ttu-id="22d04-141">이 예제에서 텍스트 파일은 C:\\내 문서\\. t s s 3입니다.</span><span class="sxs-lookup"><span data-stu-id="22d04-141">In this example, the text file is C:\\My Documents\\Accounts.txt.</span></span>
    
2. <span data-ttu-id="22d04-142">다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="22d04-142">Run the following command:</span></span>
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

<span data-ttu-id="22d04-143">여러 라이선싱 계획에 대 한 서비스에 대 한 액세스를 사용 하지 않도록 설정 하려면 각 라이선스 계획에 대해 위의 지침을 반복 하 고 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="22d04-143">If you want to disable access to services for multiple licensing plans, repeat the above instructions for each licensing plan, ensuring that:</span></span>

- <span data-ttu-id="22d04-144">사용자 계정에 라이선스 계획이 할당 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="22d04-144">The user accounts have been assigned the licensing plan.</span></span>
- <span data-ttu-id="22d04-145">사용 하지 않도록 설정할 서비스는 라이선스 계획에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22d04-145">The services to disable are available in the licensing plan.</span></span>

<span data-ttu-id="22d04-146">사용자가 라이선스를 계획에 할당 하는 동안 Office 365 서비스를 사용 하지 않도록 설정 하려면 [사용자 라이선스를 할당 하는 동안 서비스에 대 한 액세스 사용 안 함을](disable-access-to-services-while-assigning-user-licenses.md)참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="22d04-146">To disable Office 365 services for users while you are assigning them to a licensing plan, see [Disable access to services while assigning user licenses](disable-access-to-services-while-assigning-user-licenses.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="22d04-147">참고 항목</span><span class="sxs-lookup"><span data-stu-id="22d04-147">See also</span></span>

[<span data-ttu-id="22d04-148">Office 365 PowerShell을 사용 하 여 사용자 계정, 라이선스 및 그룹 관리</span><span class="sxs-lookup"><span data-stu-id="22d04-148">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="22d04-149">Office 365 PowerShell 사용한 Office 365 관리</span><span class="sxs-lookup"><span data-stu-id="22d04-149">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="22d04-150">Office 365 PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="22d04-150">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
