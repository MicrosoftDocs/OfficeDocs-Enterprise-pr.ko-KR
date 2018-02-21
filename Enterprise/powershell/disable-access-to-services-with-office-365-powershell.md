---
title: "Office 365 PowerShell을 사용 하 여 서비스에 대 한 액세스를 비활성화 합니다."
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/13/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- PowerShell
- LIL_Placement
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: "Office 365 PowerShell을 사용 하 여 조직에서 사용자를 위한 Office 365 서비스에 대 한 액세스를 사용 하지 않도록 설정 하는 방법에 설명 합니다."
ms.openlocfilehash: 61d92a1a0c55a381f10fedbb43403dd099fcb69b
ms.sourcegitcommit: 07416472be80566370c30631aff740177b37b24c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/19/2018
---
# <a name="disable-access-to-services-with-office-365-powershell"></a><span data-ttu-id="d0e51-103">Office 365 PowerShell을 사용 하 여 서비스에 대 한 액세스를 비활성화 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0e51-103">Disable access to services with Office 365 PowerShell</span></span>

<span data-ttu-id="d0e51-104">**요약:** Office 365 PowerShell을 사용 하 여 조직에서 사용자를 위한 Office 365 서비스에 대 한 액세스를 사용 하지 않도록 설정 하는 방법에 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0e51-104">**Summary:** Explains how to use Office 365 PowerShell to disable access to Office 365 services for users in your organization.</span></span>
  
<span data-ttu-id="d0e51-p101">Office 365 계정을 라이선스 계획에서 라이선스를 할당 된, Office 365 서비스 사용할 수 있습니다는 사용자에 게 해당 라이선스에서 합니다. 그러나 사용자가 액세스할 수 있는 Office 365 서비스를 제어할 수 있습니다. 예, 라이선스에는 SharePoint Online에 액세스할 수 있도록, 경우에에 대 한 액세스를 비활성화할 수 있습니다. 실제로 임의 개수의 대 한 서비스에 대 한 액세스를 사용 하지 않도록 설정 하려면 Office 365 PowerShell를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0e51-p101">When an Office 365 account is assigned a license from a licensing plan, Office 365 services are made available to the user from that license. However, you can control the Office 365 services that the user can access. For example, even though the license allows access to SharePoint Online, you can disable access to it. In fact, you can use Office 365 PowerShell to disable access to any number of services for:</span></span>

- <span data-ttu-id="d0e51-109">개별 계정입니다.</span><span class="sxs-lookup"><span data-stu-id="d0e51-109">An individual account.</span></span>
    
- <span data-ttu-id="d0e51-110">그룹 계정입니다.</span><span class="sxs-lookup"><span data-stu-id="d0e51-110">A group of accounts.</span></span>
    
- <span data-ttu-id="d0e51-111">조직의 모든 계정입니다.</span><span class="sxs-lookup"><span data-stu-id="d0e51-111">All accounts in your organization.</span></span>
    
## <a name="before-you-begin"></a><span data-ttu-id="d0e51-112">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="d0e51-112">Before you begin</span></span>
<span data-ttu-id="d0e51-113"><a name="RTT"> </a></span><span class="sxs-lookup"><span data-stu-id="d0e51-113"></span></span>

- <span data-ttu-id="d0e51-p102">이 항목의 절차를 수행하려면 Office 365 PowerShell에 연결되어 있어야 합니다. 지침을 보려면 [PowerShell Office 365에 연결](connect-to-office-365-powershell.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d0e51-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="d0e51-p103">**Get-msolaccountsku** cmdlet를 사용 하 여 사용 가능한 라이선스 계획 및 해당 계획에서 사용할 수 있는 Office 365 서비스를 볼 수 있습니다. 자세한 내용은 [보기 라이선스 및 Office 365 PowerShell을 사용 하 여 서비스를](view-licenses-and-services-with-office-365-powershell.md)참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="d0e51-p103">You use the **Get-MsolAccountSku** cmdlet to view your available licensing plans, and the Office 365 services that are available in those plans. For more information, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="d0e51-118">참조 하는 하기 전과 후이 항목의 절차에서는의 결과 [Office 365 powershell 계정 라이선스 및 서비스 정보 보기](view-account-license-and-service-details-with-office-365-powershell.md)를 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0e51-118">To see the before and after results of the procedures in this topic, see [View account license and service details with Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="d0e51-p104">PowerShell 스크립트를 사용할 수 있는이 항목에서 설명 하는 절차를 자동화 합니다. 특히, 스크립트를 사용 하 보기 및 Office 365 조직 전체에서 영향을 포함 하 여 서비스를 사용 하지 않도록 설정할 수 있습니다. 자세한 내용은 [Office 365 powershell 영향에 대 한 액세스를 사용 하지 않도록 설정](disable-access-to-sway-with-office-365-powershell.md)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="d0e51-p104">A PowerShell script is available that automates the procedures described in this topic. Specifically, the script allows you to view and disable services in your Office 365 organization, including Sway. For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="d0e51-122">_모든_ 매개 변수를 사용 하지 않고 **Get-msoluser** cmdlet을 사용 하는 경우 첫번째 500 사용자 계정만 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0e51-122">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 user accounts are returned.</span></span>
    
## <a name="specific-office-365-services-for-specific-users-for-a-single-licensing-plan"></a><span data-ttu-id="d0e51-123">단일 라이선스에 대 한 특정 사용자에 대 한 특정 Office 365 서비스 계획</span><span class="sxs-lookup"><span data-stu-id="d0e51-123">Specific Office 365 services for specific users for a single licensing plan</span></span>
  
<span data-ttu-id="d0e51-124">단일 라이선스 계획에서 사용자를 위한 Office 365 서비스의 특정 집합을 사용 하지 않으려면 다음 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0e51-124">To disable a specific set of Office 365 services for users from a single licensing plan, perform the following steps:</span></span>
  
1. <span data-ttu-id="d0e51-125">다음 구문을 사용 하 여 라이선스 계획에서 원하지 않는 서비스를 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0e51-125">Identify the undesirable services in the licensing plan by using the following syntax:</span></span>
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
  ```

    <span data-ttu-id="d0e51-126">다음 예제에서는 이름이 지정 된 라이선스 계획에서 Office Online 및 SharePoint Online 서비스를 사용 하지 않도록 설정 하는 **LicenseOptions** 개체를 `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).</span><span class="sxs-lookup"><span data-stu-id="d0e51-126">The following example creates a **LicenseOptions** object that disables the Office Online and SharePoint Online services in the licensing plan named `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).</span></span>
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
  ```

2. <span data-ttu-id="d0e51-127">1 단계에서에서 **LicenseOptions** 개체를 사용 하 여 하나 이상의 사용자에 게 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0e51-127">Use the **LicenseOptions** object from Step 1 on one or more users.</span></span>
    
  - <span data-ttu-id="d0e51-128">서비스를 비활성화 하는 가진 새 계정을 만들려면 다음 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0e51-128">To create a new account that has the services disabled, use the following syntax:</span></span>
    
  ```
  New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
  ```

    <span data-ttu-id="d0e51-129">다음 예제에서는 라이선스를 할당 하 고 1 단계에서에서 설명 하는 서비스를 사용 하지 않도록 설정 하는 Allie Bellew에 대 한 새 계정을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d0e51-129">The following example creates a new account for Allie Bellew that assigns the license and disables the services described in Step 1.</span></span>
    
  ```
  New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
  ```

    <span data-ttu-id="d0e51-130">Office 365 PowerShell의 사용자 계정 만들기 (영문) 하는 방법에 대 한 자세한 내용은 [Office 365 PowerShell을 사용한 사용자 계정 만들기를](create-user-accounts-with-office-365-powershell.md)참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="d0e51-130">For more information about creating user accounts in Office 365 PowerShell, see [Create user accounts with Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span></span>
    
  - <span data-ttu-id="d0e51-131">기존 사용이 허가 된 사용자에 대 한 서비스를 사용 하지 않으려면 다음 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0e51-131">To disable the services for an existing licensed user, use the following syntax:</span></span>
    
  ```
  Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
  ```

    <span data-ttu-id="d0e51-132">BelindaN@litwareinc.com 사용자에 대 한 서비스를 해제 하는이 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="d0e51-132">This example disables the services for the user BelindaN@litwareinc.com.</span></span>
    
  ```
  Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
  ```

  - <span data-ttu-id="d0e51-133">모든 기존 사용이 허가 된 사용자에 대해 1 단계에서에서 설명 하는 서비스를 사용 하지 않으려면 (예: **litwareinc:ENTERPRISEPACK**) **Get-msolaccountsku** cmdlet의 표시에서 Office 365 계획의 이름을 지정 하 고 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0e51-133">To disable the services described in Step 1 for all existing licensed users, specify the name of your Office 365 plan from the display of the **Get-MsolAccountSku** cmdlet (such as **litwareinc:ENTERPRISEPACK**), and then run the following commands:</span></span>
    
  ```
  $acctSKU="<AccountSkuId>"
  $AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
  $AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - <span data-ttu-id="d0e51-134">기존 사용자 그룹에 대 한 서비스를 사용 하지 않으려면 다음 방법 중 하나를 사용자를 식별 하기 위해 사용.</span><span class="sxs-lookup"><span data-stu-id="d0e51-134">To disable the services for a group of existing users, use either of the following methods to identify the users:</span></span>
    
  - <span data-ttu-id="d0e51-135">**기존 계정 특성을 기준으로 계정 필터링** 이 작업을 수행 하려면 다음 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0e51-135">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
  ```
  $x = Get-MsolUser -All <FilterableAttributes>
  $x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

    <span data-ttu-id="d0e51-136">다음 예제에서는 미국에서 Sales 부서에 있는 사용자에 대 한 서비스를 비활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="d0e51-136">The following example disables the services for users in the Sales department in the United States.</span></span>
    
  ```
  $USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
  $USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - <span data-ttu-id="d0e51-137">**특정 계정 목록 사용** 이 작업을 수행 하려면 다음 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0e51-137">**Use a list of specific accounts** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="d0e51-138">다음과 같이 각 줄에 한 계정에 포함 된 텍스트 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d0e51-138">Create a text file that contains one account on each line like this:</span></span>
    
  ```
  akol@contoso.com
  tjohnston@contoso.com
  kakers@contoso.com
  ```

    <span data-ttu-id="d0e51-139">이 예제에서는 텍스트 파일은 c:\\My Documents\\Accounts.txt 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0e51-139">In this example, the text file is C:\\My Documents\\Accounts.txt.</span></span>
    
2. <span data-ttu-id="d0e51-140">다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d0e51-140">Run the following command:</span></span>
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

<span data-ttu-id="d0e51-141">라이선스 계획에 할당 되는 동안에 사용자를 위한 Office 365 서비스를 사용 하지 않도록 하십시오 [사용자 라이선스를 할당 하는 동안 서비스에 대 한 액세스를 사용 하지 않도록 설정](disable-access-to-services-while-assigning-user-licenses.md)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="d0e51-141">To disable Office 365 services for users while you are assigning them to a licensing plan, see [Disable access to services while assigning user licenses](disable-access-to-services-while-assigning-user-licenses.md).</span></span>
  
## <a name="specific-office-365-services-for-users-from-all-licensing-plans"></a><span data-ttu-id="d0e51-142">모든 라이선스 계획에서 사용자에 대 한 특정 Office 365 서비스</span><span class="sxs-lookup"><span data-stu-id="d0e51-142">Specific Office 365 services for users from all licensing plans</span></span>
  
<span data-ttu-id="d0e51-143">모든 사용 가능한 라이선스 계획에 사용자를 위한 Office 365 서비스를 비활성화 하려면 다음 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0e51-143">To disable Office 365 services for users in all available licensing plans, perform the following steps:</span></span>
  
1. <span data-ttu-id="d0e51-144">아래 스크립트를 복사하여 메모장에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="d0e51-144">Copy and paste this script into Notepad.</span></span>
    
  ```
  $AllLicensingPlans = Get-MsolAccountSku
for($i = 0; $i -lt $AllLicensingPlans.Count; $i++)
{
    $O365Licences = New-MsolLicenseOptions -AccountSkuId $AllLicensingPlans[$i].AccountSkuId -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
    Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $O365Licences
}
  ```

2. <span data-ttu-id="d0e51-145">사용자 환경에 대 한 다음 값을 사용자 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0e51-145">Customize the following values for your environment:</span></span>
    
  -  <span data-ttu-id="d0e51-146">_<UndesirableService>_이 예제에서는 Office Online 및 SharePoint Online를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0e51-146">_<UndesirableService>_ In this example, we'll use Office Online and SharePoint Online.</span></span>
    
  -  <span data-ttu-id="d0e51-147">_<Account>_이 예제에서는 belindan@litwareinc.com를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0e51-147">_<Account>_ In this example, we'll use belindan@litwareinc.com.</span></span>
    
    <span data-ttu-id="d0e51-148">사용자 지정 된 스크립트는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d0e51-148">The customized script looks like this:</span></span>
    
  ```
  $AllLicensingPlans = Get-MsolAccountSku
for($i = 0; $i -lt $AllLicensingPlans.Count; $i++)
{
    $O365Licences = New-MsolLicenseOptions -AccountSkuId $AllLicensingPlans[$i].AccountSkuId -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
    Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $O365Licences
}
  ```

3. <span data-ttu-id="d0e51-p105">으로 스크립트를 저장 `RemoveO365Services.ps1` 를 쉽게 찾을 수 있는 위치에 있습니다. 이 예제에서는에서 파일을 저장 합니다는 `C:\\O365 Scripts`합니다.</span><span class="sxs-lookup"><span data-stu-id="d0e51-p105">Save the script as  `RemoveO365Services.ps1` in a location that's easy for you to find. For this example, we'll save the file in `C:\\O365 Scripts`.</span></span>
    
4. <span data-ttu-id="d0e51-151">다음 명령을 사용 하 여 Office 365 PowerShell에서 스크립트를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0e51-151">Run the script in Office 365 PowerShell by using the following command.</span></span>
    
  ```
  & "C:\O365 Scripts\RemoveO365Services.ps1"
  ```

> [!NOTE]
> <span data-ttu-id="d0e51-152">이러한 절차의 효과 반전 하려면 (즉, 다시 사용할 수 없는 서비스를 사용 하도록 설정)을 하는 절차를 다시 실행 되지만 값을 사용 하 여 `$null` _DisabledPlans_ 매개 변수에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0e51-152">To reverse the effects of any of these procedures (that is, to re-enable the disabled services), run the procedure again, but use the value `$null` for the _DisabledPlans_ parameter.</span></span>
  
[<span data-ttu-id="d0e51-153">맨위로 돌아가기</span><span class="sxs-lookup"><span data-stu-id="d0e51-153">Return to top</span></span>](disable-access-to-services-with-office-365-powershell.md#RTT)


## <a name="all-office-365-services-for-all-users-for-a-single-licensing-plan"></a><span data-ttu-id="d0e51-154">단일 라이선스에 대 한 모든 사용자에 대 한 모든 Office 365 서비스 계획</span><span class="sxs-lookup"><span data-stu-id="d0e51-154">All Office 365 services for all users for a single licensing plan</span></span>
 
<span data-ttu-id="d0e51-155">특정 라이선스 계획에서 모든 사용자에 대 한 모든 Office 365 서비스를 사용 하지 않도록 설정 합니다 (예: **litwareinc:ENTERPRISEPACK**) $acctSKU에 대 한 라이선스 계획 이름을 지정 하 고 PowerShell 명령 창에 다음이 명령을 실행:</span><span class="sxs-lookup"><span data-stu-id="d0e51-155">To disable all Office 365 services for all users in a specific licensing plan, specify the licensing plan name for $acctSKU (such as **litwareinc:ENTERPRISEPACK**), and then run these commands in the PowerShell command window:</span></span>

```
$acctSKU="<AccountSkuId>"
$servicesList=(Get-MsolAccountSku | Select -ExpandProperty ServiceStatus).ServicePlan.ServiceName
$lo = New-MsolLicenseOptions -AccountSkuId $acctSKU -DisabledPlans $servicesList
$AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
$AllLicensed | ForEach {Set-MsolUserLicense -ObjectID $_.ObjectID -LicenseOptions $lo}
```

## <a name="new-to-office-365"></a><span data-ttu-id="d0e51-156">Office 365의 새로운 기능</span><span class="sxs-lookup"><span data-stu-id="d0e51-156">New to Office 365?</span></span>
<span data-ttu-id="d0e51-157"><a name="LinkedIn"> </a></span><span class="sxs-lookup"><span data-stu-id="d0e51-157"></span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a><span data-ttu-id="d0e51-158">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d0e51-158">See also</span></span>
<span data-ttu-id="d0e51-159"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="d0e51-159"></span></span>

<span data-ttu-id="d0e51-160">Office 365 PowerShell을 사용 하여 사용자를 관리에 대하여 다음과 같은 추가 항목을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="d0e51-160">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="d0e51-161">삭제 한 사용자 계정 Office 365 PowerShell을 사용 하 여 복원 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0e51-161">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="d0e51-162">삭제 한 사용자 계정 Office 365 PowerShell을 사용 하 여 복원 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0e51-162">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="d0e51-163">블록 사용자 계정 Office 365 PowerShell을 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="d0e51-163">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="d0e51-164">Office 365 PowerShell을 사용 하 여 사용자 계정에 라이선스를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0e51-164">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="d0e51-165">Office 365 PowerShell을 사용 하 여 사용자 계정 만들기</span><span class="sxs-lookup"><span data-stu-id="d0e51-165">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="d0e51-166">이 항목에서 사용된 cmdlet에 대한 자세한 내용은 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="d0e51-166">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="d0e51-167">Get-content</span><span class="sxs-lookup"><span data-stu-id="d0e51-167">Get-Content</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [<span data-ttu-id="d0e51-168">Get-msolaccountsku</span><span class="sxs-lookup"><span data-stu-id="d0e51-168">Get-MsolAccountSku</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [<span data-ttu-id="d0e51-169">새 MsolLicenseOptions</span><span class="sxs-lookup"><span data-stu-id="d0e51-169">New-MsolLicenseOptions</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691546)
    
- [<span data-ttu-id="d0e51-170">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="d0e51-170">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="d0e51-171">New-MsolUser</span><span class="sxs-lookup"><span data-stu-id="d0e51-171">New-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [<span data-ttu-id="d0e51-172">Set-msoluserlicense</span><span class="sxs-lookup"><span data-stu-id="d0e51-172">Set-MsolUserLicense</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [<span data-ttu-id="d0e51-173">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="d0e51-173">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="d0e51-174">Where-Object</span><span class="sxs-lookup"><span data-stu-id="d0e51-174">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
  

