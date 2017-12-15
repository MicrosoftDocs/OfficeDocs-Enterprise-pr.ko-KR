---
title: "Office 365 PowerShell을 사용 하 여 서비스에 대 한 액세스를 비활성화 합니다."
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
- Ent_Office_Other
- PowerShell
- LIL_Placement
- DecEntMigration
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: "Office 365 PowerShell을 사용 하 여 추가 하거나 조직에서 사용자를 위한 Office 365 서비스에 대 한 액세스를 제거 하는 방법에 설명 합니다."
ms.openlocfilehash: a371e6adc482a3f21ebfacac08aff02daf4fd5b2
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2017
---
# <a name="disable-access-to-services-with-office-365-powershell"></a><span data-ttu-id="1a8f7-103">Office 365 PowerShell을 사용 하 여 서비스에 대 한 액세스를 비활성화 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a8f7-103">Disable access to services with Office 365 PowerShell</span></span>

<span data-ttu-id="1a8f7-104">**요약:** Office 365 PowerShell을 사용 하 여 추가 하거나 조직에서 사용자를 위한 Office 365 서비스에 대 한 액세스를 제거 하는 방법에 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a8f7-104">**Summary:** Explains how to use Office 365 PowerShell to add or remove access to Office 365 services for users in your organization.</span></span>
  
<span data-ttu-id="1a8f7-p101">Office 365 계정을 라이선스 계획에서 라이선스를 할당 된, Office 365 서비스 사용할 수 있습니다는 사용자에 게 해당 라이선스에서 합니다. 그러나 사용자가 액세스할 수 있는 Office 365 서비스를 제어할 수 있습니다. 예, 라이선스에는 SharePoint Online에 액세스할 수 있도록, 경우에에 대 한 액세스를 비활성화할 수 있습니다. 실제로 임의 개수의 대 한 서비스에 대 한 액세스를 사용 하지 않도록 설정 하려면 Office 365 PowerShell를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a8f7-p101">When an Office 365 account is assigned a license from a licensing plan, Office 365 services are made available to the user from that license. However, you can control the Office 365 services that the user can access. For example, even though the license allows access to SharePoint Online, you can disable access to it. In fact, you can use Office 365 PowerShell to disable access to any number of services for:</span></span>
- <span data-ttu-id="1a8f7-109">개별 계정입니다.</span><span class="sxs-lookup"><span data-stu-id="1a8f7-109">An individual account.</span></span>
    
- <span data-ttu-id="1a8f7-110">그룹 계정입니다.</span><span class="sxs-lookup"><span data-stu-id="1a8f7-110">A group of accounts.</span></span>
    
- <span data-ttu-id="1a8f7-111">조직의 모든 계정입니다.</span><span class="sxs-lookup"><span data-stu-id="1a8f7-111">All accounts in your organization.</span></span>
    
 <span data-ttu-id="1a8f7-112">**내용을:** [짧은 버전 (설명 없이 지침)](disable-access-to-services-with-office-365-powershell.md#ShortVersion) [긴 버전 (대 한 자세한 설명을 제공 지침)](disable-access-to-services-with-office-365-powershell.md#LongVersion) [참조 하십시오](disable-access-to-services-with-office-365-powershell.md#SeeAlso)</span><span class="sxs-lookup"><span data-stu-id="1a8f7-112">**Contents:**[The short version (instructions without explanations)](disable-access-to-services-with-office-365-powershell.md#ShortVersion)[The long version (instructions with detailed explanations)](disable-access-to-services-with-office-365-powershell.md#LongVersion)[See also](disable-access-to-services-with-office-365-powershell.md#SeeAlso)</span></span>
## <a name="before-you-begin"></a><span data-ttu-id="1a8f7-113">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="1a8f7-113">Before you begin</span></span>
<span data-ttu-id="1a8f7-114"><a name="RTT"> </a></span><span class="sxs-lookup"><span data-stu-id="1a8f7-114"></span></span>

- <span data-ttu-id="1a8f7-p102">이 항목의 절차에서는 Office 365 PowerShell에 연결 해야 합니다. 자세한 내용은 [Office 365 PowerShell 연결](connect-to-office-365-powershell.md)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="1a8f7-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="1a8f7-p103">**Get-msolaccountsku** cmdlet를 사용 하 여 사용 가능한 라이선스 계획 및 해당 계획에서 사용할 수 있는 Office 365 서비스를 볼 수 있습니다. 자세한 내용은[보기 라이선스 및 Office 365 PowerShell을 사용 하 여 서비스를](view-licenses-and-services-with-office-365-powershell.md)참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="1a8f7-p103">You use the **Get-MsolAccountSku** cmdlet to view your available licensing plans, and the Office 365 services that are available in those plans. For more information, see[View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="1a8f7-119">참조 하는 하기 전과 후이 항목의 절차에서는의 결과 [Office 365 powershell 계정 라이선스 및 서비스 정보 보기](view-account-license-and-service-details-with-office-365-powershell.md)를 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a8f7-119">To see the before and after results of the procedures in this topic, see [View account license and service details with Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="1a8f7-p104">PowerShell 스크립트를 사용할 수 있는이 항목에서 설명 하는 절차를 자동화 합니다. 특히, 스크립트를 사용 하 보기 및 Office 365 조직 전체에서 영향을 포함 하 여 서비스를 사용 하지 않도록 설정할 수 있습니다. 자세한 내용은 [Office 365 powershell 영향에 대 한 액세스를 사용 하지 않도록 설정](disable-access-to-sway-with-office-365-powershell.md)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="1a8f7-p104">A PowerShell script is available that automates the procedures described in this topic. Specifically, the script allows you to view and disable services in your Office 365 organization, including Sway. For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="1a8f7-123">_모든_ 매개 변수를 사용 하지 않고 **Get-msoluser** cmdlet을 사용 하는 경우 처음 500 개 계정만 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a8f7-123">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 accounts are returned.</span></span>
    
## <a name="the-short-version-instructions-without-explanations"></a><span data-ttu-id="1a8f7-124">간략 한 (설명 없이 지침)</span><span class="sxs-lookup"><span data-stu-id="1a8f7-124">The short version (instructions without explanations)</span></span>
<span data-ttu-id="1a8f7-125"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="1a8f7-125"></span></span>

<span data-ttu-id="1a8f7-p105">이 섹션에서는 선전과 또는 불필요 한 설명 없이 절차를 제공 합니다. 질문이 더 많은 정보를 원하는 경우에 항목의 나머지 부분을 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a8f7-p105">This section presents the procedures without fanfare or superfluous explanation. If you have questions or want more information, you can read rest of the topic.</span></span>
  
<span data-ttu-id="1a8f7-128">단일 라이선스 계획에서 사용자를 위한 Office 365 서비스를 사용 하지 않으려면 다음 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a8f7-128">To disable Office 365 services for users from a single licensing plan, perform the following steps:</span></span>
  
1. <span data-ttu-id="1a8f7-129">다음 구문을 사용 하 여 라이선스 계획에서 원하지 않는 서비스를 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a8f7-129">Identify the undesirable services in the licensing plan by using the following syntax:</span></span>
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
  ```

    <span data-ttu-id="1a8f7-130">이 예제에서는 이름이 지정 된 라이선스 계획에서 Office Online 및 SharePoint Online 서비스를 사용 하지 않도록 설정 하는 **LicenseOptions** 개체를 만듭니다 `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).</span><span class="sxs-lookup"><span data-stu-id="1a8f7-130">This example creates a **LicenseOptions** object that disables the Office Online and SharePoint Online services in the licensing plan named `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).</span></span>
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
  ```

2. <span data-ttu-id="1a8f7-131">1 단계에서에서 **LicenseOptions** 개체를 사용 하 여 하나 이상의 사용자에 게 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a8f7-131">Use the **LicenseOptions** object from Step 1 on one or more users.</span></span>
    
  - <span data-ttu-id="1a8f7-132">서비스를 비활성화 하는 가진 새 계정을 만들려면 다음 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a8f7-132">To create a new account that has the services disabled, use the following syntax:</span></span>
    
  ```
  New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
  ```

    <span data-ttu-id="1a8f7-133">이 예제에서는 새 계정에 라이선스를 할당 하 고 1 단계에서에서 설명 하는 서비스를 사용할 수 없게 하는 Allie Bellew</span><span class="sxs-lookup"><span data-stu-id="1a8f7-133">This example creates a new account for Allie Bellew that assigns the license and disables the services described in Step 1.</span></span>
    
  ```
  New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
  ```

    <span data-ttu-id="1a8f7-134">Office 365 PowerShell의 사용자 계정 만들기 (영문) 하는 방법에 대 한 자세한 내용은 [Office 365 PowerShell을 사용한 사용자 계정 만들기를](create-user-accounts-with-office-365-powershell.md)참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="1a8f7-134">For more information about creating user accounts in Office 365 PowerShell, see [Create user accounts with Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span></span>
    
  - <span data-ttu-id="1a8f7-135">기존 사용이 허가 된 사용자에 대 한 서비스를 사용 하지 않으려면 다음 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a8f7-135">To disable the services for an existing licensed user, use the following syntax:</span></span>
    
  ```
  Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
  ```

    <span data-ttu-id="1a8f7-136">BelindaN@litwareinc.com 사용자에 대 한 서비스를 해제 하는이 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="1a8f7-136">This example disables the services for the user BelindaN@litwareinc.com.</span></span>
    
  ```
  Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
  ```

  - <span data-ttu-id="1a8f7-137">모든 기존 사용이 허가 된 사용자에 대해 1 단계에서에서 설명 하는 서비스를 사용 하지 않으려면 (예: **litwareinc:ENTERPRISEPACK** ) **Get-msolaccountsku** cmdlet의 표시에서 Office 365 계획의 이름을 지정 하 고 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a8f7-137">To disable the services described in Step 1 for all existing licensed users, specify the name of your Office 365 plan from the display of the **Get-MsolAccountSku** cmdlet (such as **litwareinc:ENTERPRISEPACK** ), and then run the following commands:</span></span>
    
  ```
  $acctSKU="<AccountSkuId>"
$AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
$AllLicensed | ForEach {Set-MsolUserLicense -LicenseOptions $LO}
  ```

  - <span data-ttu-id="1a8f7-138">기존 사용자 그룹에 대 한 서비스를 사용 하지 않으려면 다음 방법 중 하나를 사용자를 식별 하기 위해 사용.</span><span class="sxs-lookup"><span data-stu-id="1a8f7-138">To disable the services for a group of existing users, use either of the following methods to identify the users:</span></span>
    
  - <span data-ttu-id="1a8f7-139">**기존 계정 특성을 기준으로 계정 필터링** 이 작업을 수행 하려면 다음 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a8f7-139">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
  ```
  $x = Get-MsolUser -All <FilterableAttributes>
$x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

    <span data-ttu-id="1a8f7-140">미국에서 영업부의 사용자를 위한 서비스를 해제 하는이 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="1a8f7-140">This example disables the services for users in the Sales department in the United States.</span></span>
    
  ```
  $USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
$USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - <span data-ttu-id="1a8f7-141">**특정 계정 목록 사용** 이 작업을 수행 하려면 다음 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a8f7-141">**Use a list of specific accounts** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="1a8f7-142">다음과 같이 각 줄에 한 계정에 포함 된 텍스트 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1a8f7-142">Create a text file that contains one account on each line like this:</span></span>
    
  ```
  akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

    <span data-ttu-id="1a8f7-143">이 예제에서는 텍스트 파일은 c:\\My Documents\\Accounts.txt 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a8f7-143">In this example, the text file is C:\\My Documents\\Accounts.txt.</span></span>
    
2. <span data-ttu-id="1a8f7-144">다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="1a8f7-144">Run the following command:</span></span>
    
  ```
  Get-Content "C:\\My Documents\\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

<span data-ttu-id="1a8f7-145">라이선스 계획에 할당 되는 동안에 사용자를 위한 Office 365 서비스를 사용 하지 않도록 하십시오 [사용자 라이선스를 할당 하는 동안 서비스에 대 한 액세스를 사용 하지 않도록 설정](disable-access-to-services-while-assigning-user-licenses.md)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="1a8f7-145">To disable Office 365 services for users while you are assigning them to a licensing plan, see [Disable access to services while assigning user licenses](disable-access-to-services-while-assigning-user-licenses.md).</span></span>
  
<span data-ttu-id="1a8f7-146">모든 사용 가능한 라이선스 계획에 사용자를 위한 Office 365 서비스를 비활성화 하려면 다음 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a8f7-146">To disable Office 365 services for users in all available licensing plans, perform the following steps:</span></span>
  
1. <span data-ttu-id="1a8f7-147">아래 스크립트를 복사하여 메모장에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="1a8f7-147">Copy and paste this script into Notepad.</span></span>
    
  ```
  $AllLicensingPlans = Get-MsolAccountSku
for($i = 0; $i -lt $AllLicensingPlans.Count; $i++)
{
    $O365Licences = New-MsolLicenseOptions -AccountSkuId $AllLicensingPlans[$i].AccountSkuId -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
    Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $O365Licences
}
  ```

2. <span data-ttu-id="1a8f7-148">사용자 환경에 대 한 다음 값을 사용자 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a8f7-148">Customize the following values for your environment:</span></span>
    
  -  <span data-ttu-id="1a8f7-149">_<UndesirableService>_이 예제에서는 Office Online 및 SharePoint Online를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a8f7-149">_<UndesirableService>_ In this example, we'll use Office Online and SharePoint Online.</span></span>
    
  -  <span data-ttu-id="1a8f7-150">_<Account>_이 예제에서는 belindan@litwareinc.com를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a8f7-150">_<Account>_ In this example, we'll use belindan@litwareinc.com.</span></span>
    
    <span data-ttu-id="1a8f7-151">사용자 지정 된 스크립트는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1a8f7-151">The customized script looks like this:</span></span>
    
  ```
  $AllLicensingPlans = Get-MsolAccountSku
for($i = 0; $i -lt $AllLicensingPlans.Count; $i++)
{
    $O365Licences = New-MsolLicenseOptions -AccountSkuId $AllLicensingPlans[$i].AccountSkuId -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
    Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $O365Licences
}
  ```

3. <span data-ttu-id="1a8f7-p106">으로 스크립트를 저장 `RemoveO365Services.ps1` 를 쉽게 찾을 수 있는 위치에 있습니다. 이 예제에서는에서 파일을 저장 합니다 우리 " `C:\\O365 Scripts`"입니다.</span><span class="sxs-lookup"><span data-stu-id="1a8f7-p106">Save the script as  `RemoveO365Services.ps1` in a location that's easy for you to find. For this example, we'll save the file in " `C:\\O365 Scripts`".</span></span>
    
4. <span data-ttu-id="1a8f7-154">다음 명령을 사용 하 여 Office 365 PowerShell에서 스크립트를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a8f7-154">Run the script in Office 365 PowerShell by using the following command.</span></span>
    
  ```
  &amp; "C:\\O365 Scripts\\RemoveO365Services.ps1"
  ```

> [!NOTE]
> <span data-ttu-id="1a8f7-155">이러한 절차의 효과 반전 하려면 (즉, 다시 사용할 수 없는 서비스를 사용 하도록 설정)을 하는 절차를 다시 실행 되지만 값을 사용 하 여 `$null` _DisabledPlans_ 매개 변수에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a8f7-155">To reverse the effects of any of these procedures (that is, to re-enable the disabled services), run the procedure again, but use the value  `$null` for the _DisabledPlans_ parameter.</span></span>
  
[<span data-ttu-id="1a8f7-156">맨위로 돌아가기</span><span class="sxs-lookup"><span data-stu-id="1a8f7-156">Return to top</span></span>](disable-access-to-services-with-office-365-powershell.md#RTT)
  
## <a name="the-long-version-instructions-with-detailed-explanations"></a><span data-ttu-id="1a8f7-157">긴 버전 (명령에 대 한 세부 정보)</span><span class="sxs-lookup"><span data-stu-id="1a8f7-157">The long version (instructions with detailed explanations)</span></span>
<span data-ttu-id="1a8f7-158"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="1a8f7-158"></span></span>

<span data-ttu-id="1a8f7-p107">기본적으로 모든 서비스에는 Office 365 PowerShell을 사용 하 여 라이선스를 발급할 때 활성화 됩니다. 좋은 일이 자주 및: 쉽고 빠르게 할당할 수 라이선스 사용자에 게는 방식에 따라 각각의 모든 서비스를 설정 하는 것을 지정 하지 않고 것을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a8f7-p107">By default, all services are enabled when you issue a license by using Office 365 PowerShell. And often that's a good thing: that means that you can quickly and easily assign licenses to users without having to specify that each and every service be enabled along the way.</span></span>
  
<span data-ttu-id="1a8f7-p108">그러나 물론,는 어디에 일부 사용자에 게; 제공 되는 서비스를 제한 하려는 수 있습니다. 예, 일부 사용자에 게 Office Professional Plus를 Skype 비즈니스 온라인 및 Exchange Online에 액세스할 수 있는 엔터프라이즈 무선 전화 통신 되었지만 동일한 사용자 안됩니다 SharePoint online 또는 Office Online에 대 한 액세스. 해당 방식에서 계정을 제한할 수 있습니까? 이러한, 다음 작업을 수행할 수 있습니다. 이 작동 하는 방법에 대해 설명 하는데 알아보겠습니다 2 단계 접근 방식이이 문제를 다루는 하려면:</span><span class="sxs-lookup"><span data-stu-id="1a8f7-p108">Having said that, however, it's also true that you might want to restrict the services available some of your users; for example, maybe some users should have access to Office Professional Plus, Skype for Business Online, and Exchange Online, but those same users shouldn't have access to SharePoint Online or to Office Online. Can you restrict accounts in that fashion? As it turns out, you can. To help explain how this works, let's take a two-step approach to tackling this problem:</span></span>
  
1. <span data-ttu-id="1a8f7-165">사용자를 자동으로 모든 서비스를 사용 하도록 설정 하는 Office 365 라이선스를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a8f7-165">Assign the user an Office 365 license that automatically enables all the services.</span></span>
    
2. <span data-ttu-id="1a8f7-166">해당 사용자에 대 한 지정 된 서비스를 사용 하지 않도록 설정 하는 Office 365 PowerShell 명령 쌍을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a8f7-166">Run a pair of Office 365 PowerShell commands that disable specified services for that user.</span></span>
    
<span data-ttu-id="1a8f7-p109">우리 했을 때 이미에 주의 하지 않아도 1 단계: (Belinda Newman)에서는 사용자가 모든 Office 365 서비스에 액세스할 수 있는 그녀를 제공 하는 Office 365 라이선스를가지고 있습니다. 하지만 SharePoint Online에 액세스할 수 없는 대화 상대가 있도록 Belinda의 계정을 수정 하려고 ( `SHAREPOINTENTERPRISE`) 또는 Office Online ( `SHAREPOINTWAC`). 하지만 어떻게는 수행 하는 작업이 있는?</span><span class="sxs-lookup"><span data-stu-id="1a8f7-p109">We've already taken care of step 1: our user (Belinda Newman) has an Office 365 license that provides her with access to all the Office 365 services. However, we want to modify Belinda's account so that she doesn't have access to SharePoint Online ( `SHAREPOINTENTERPRISE`) or to Office Online ( `SHAREPOINTWAC`). But how are we supposed to do that?</span></span>
  
<span data-ttu-id="1a8f7-p110">다음은 방법입니다. 우선 비활성화 우리가 원하는 서비스를 포함 하는 **LicenseOption** 개체를 만들려면 **새로 만들기 MsolLicenseOptions** cmdlet을 사용 하는 것입니다. 사용 하지 않으려면 원합니다 Belinda의 경우 `SHAREPOINTENTERPRISE` 및 `SHAREPOINTWAC`이므로이 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a8f7-p110">Here's how. To begin with, we're going to use the **New-MsolLicenseOptions** cmdlet to create a **LicenseOption** object that contains the services that we want disabled. In Belinda's case, we want to disable `SHAREPOINTENTERPRISE` and `SHAREPOINTWAC`, so we use this command:</span></span>
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
```

<span data-ttu-id="1a8f7-p111">작동 하는 방법을 참조? 라이선스 계획을 지정 하면 ( `litwareinc:ENTERPRISEPACK`) 하 고 각 서비스를 사용 하지 않도록 설정, 쉼표를 사용 하 여 이러한 서비스를 분리 하를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1a8f7-p111">See how that works? You specify the licensing plan ( `litwareinc:ENTERPRISEPACK`) and then indicate each of the services that you want disabled, separating those services by using commas.</span></span>
  
> [!NOTE]
> <span data-ttu-id="1a8f7-p112">새 **LicenseOption** 개체 변수에 저장 해야 합니다. 위 예제에서 사용한 `$x`모든 유효한 Windows PowerShell 변수 이름을 사용할 수 있지만, 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a8f7-p112">Make sure you store your new **LicenseOption** object in a variable. In the preceding example, we used `$x`, although you can use any valid Windows PowerShell variable name.</span></span> 
  
<span data-ttu-id="1a8f7-177">이 시점에서 두 서비스에 대 한 Belinda의 액세스를 사용 하지 않도록 설정 하려면 다음 명령을 사용할 수는:</span><span class="sxs-lookup"><span data-stu-id="1a8f7-177">At this point we can use the following command to disable Belinda's access to the two services:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -LicenseOptions $x
```

<span data-ttu-id="1a8f7-p113">너무 팬시 nothing 여기에서 중 하나: 방금 **Set-msoluserlicense** cmdlet을 호출 하 고 _LicenseOptions_ 매개 변수를 함께 포함 ( `$x`) 사용 하지 않도록 설정 하려는 계획을 포함 합니다. 수행 보이는 지금 하는 경우 취할 살짝 Belinda의 (라이선스) 정보에서 명령을 실행 하 여 및: `(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus`? 이 참조:</span><span class="sxs-lookup"><span data-stu-id="1a8f7-p113">Nothing too fancy here, either: we just call the **Set-MsolUserLicense** cmdlet and include the _LicenseOptions_ parameter, along with the variable ( `$x`) containing the plans we want to disable. And what do we see now if we take a peek at Belinda's license information by running the command:  `(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus`? We see this:</span></span>
  
```
ServicePlan                              ProvisioningStatus
-----------                              ------------------
SWAY                                     Success
INTUNE_O365                              Success
YAMMER_ENTERPRISE                        PendingInput
RMS_S_ENTERPRISE                         Success
OFFICESUBSCRIPTION                       Success
MCOSTANDARD                              Success
SHAREPOINTWAC                            Disabled
SHAREPOINTENTERPRISE                     Disabled
EXCHANGE_S_ENTERPRISE                    Success
```

<span data-ttu-id="1a8f7-p114">멋진 스크립트 죠? 및 물론 우리가 할 수 있는 것이 다릅니다 여러 사용자에 게 있으니까요. 예, 이러한 명령을 사용해 사용이 허가 된 모든 사용자에 대해 동일한 두 서비스 사용 하지 않도록 설정 합니다. (예: **litwareinc:ENTERPRISEPACK** ) **Get-msolaccountsku** cmdlet의 표시에서 Office 365 계획의 이름을 지정 하 고을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a8f7-p114">Pretty cool, huh? And, of course, we could do this same thing to multiple users if we wanted to. For example, these commands disable the same two services for all our licensed users. Specify the name of your Office 365 plan from the display of the **Get-MsolAccountSku** cmdlet (such as **litwareinc:ENTERPRISEPACK** ), and then run them.</span></span>
  
```
$acctSKU="<AccountSKU ID>"
Get-MsolUser | Where {$_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1) -and $_.IsLicensed -eq $True} | Set-MsolUserLicense -LicenseOptions $x
```

<span data-ttu-id="1a8f7-p115">Belinda에 여전히 유효한 Office 365 라이선스;가 염두에 이제 그녀는 더 적은 서비스에 대 한 액세스 하는 것은 합니다. 두 서비스를 사용할 수 없을 것 전에 Belinda 걸어야 뉴스 피드, OneDrive, 및 SharePoint Online 사이트:</span><span class="sxs-lookup"><span data-stu-id="1a8f7-p115">Keep in mind that Belinda still has a valid Office 365 license; it's just that now she has access to fewer services. Before we disabled the two services, Belinda had access to newsfeeds, OneDrive, and SharePoint Online sites:</span></span>
  
![SharePoint 액세스 권한이 있는 사용자](images/o365_powershell_with_sharepoint.png)
  
<span data-ttu-id="1a8f7-188">이제 그녀는 더 이상 이러한 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1a8f7-188">Now those options are no longer available to her:</span></span>
  
![SharePoint 액세스 권한이 없는 사용자](images/o365_powershell_without_sharepoint.png)
  
<span data-ttu-id="1a8f7-190">정확히 원하던 결과를 얻었습니다.</span><span class="sxs-lookup"><span data-stu-id="1a8f7-190">Which is exactly what we hoped would happen.</span></span>
  
<span data-ttu-id="1a8f7-p116">경우에 어떻게 우리가 사용해 염두 나중에 변경 하 고: 이러한 서비스를 다시 활성화 수 있습니까? 물론입니다. 사용자에 대 한 모든 서비스를 다시 사용 하려면 다음 **LicenseOption** 개체를 만들이 명령을 사용:</span><span class="sxs-lookup"><span data-stu-id="1a8f7-p116">And what if we change our mind later on: is it possible to re-enable these services? You bet it is. To re-enable all the services for a user, just use this command to create the following **LicenseOption** object:</span></span>
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans $null
```

<span data-ttu-id="1a8f7-p117">이 명령을 기능은 무엇입니까? Windows PowerShell 상수와 함께 시작 하려면 `$null` "nothing."를 의미 합니다. (또는 "null 값입니다." 의미 약간 더 기술 언어) 으로 있습니다, 하는 경우 회수 disabled 원합니다 서비스를 나타내기 위해 있다고 **새로 MsolLicenseOptions** cmdlet을 사용 했습니다. 이 경우에서는 서비스를 사용 하지 않도록 설정할 필요 하지 않습니다. 않을 _DisabledPlans_ 매개 변수에 대 한 값을 지정 하지는 명령은 다음과 같은 명령을 사용할 수 있는 생각할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a8f7-p117">What does that command do? To begin with, the Windows PowerShell constant  `$null` means "nothing." (Or, in slightly-more technical language, it means a "null value.") As you recall, when we use the **New-MsolLicenseOptions** cmdlet we have to indicate the services that we want disabled. In this case, we don't want any of the services to be disabled. That might lead you to believe that we could use a command like the following, a command where we don't specify a value for the _DisabledPlans_ parameter:</span></span>
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans ""
```

<span data-ttu-id="1a8f7-p118">그러나 하는 작동 하지 않습니다. 대신, 오류 메시지를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="1a8f7-p118">However, that won't work. Instead, it generates an error message:</span></span>
  
 `Set-MsolUserLicense : Cannot bind parameter 'LicenseOptions'. Cannot convert the "" value of type "System.String" to type "Microsoft.Online.Administration.LicenseOption".`
  
<span data-ttu-id="1a8f7-201">놓기만 사람들에 대 한 매개 변수 값을 설정 하 `$null` 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a8f7-201">Fortunately for us, setting the parameter value to  `$null` does work:</span></span>
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans $null
```

<span data-ttu-id="1a8f7-202">단순히는 **Set-msoluserlicense** cmdlet을 실행할 때 한 이야기 **Set-msoluserlicense** Belinda가 서비스를 사용된 하지 않으려고 우리는 것을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a8f7-202">This simply means that, when we run the **Set-MsolUserLicense** cmdlet, we're telling **Set-MsolUserLicense** that we don't want Belinda to have any disabled services:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -LicenseOptions $x
```

<span data-ttu-id="1a8f7-203">또한 사용하지 않도록 설정된 서비스가 없는 경우 이는 논리적으로 모든 서비스를 사용할 수 있음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="1a8f7-203">And, logically enough, if none of the services are disabled that must mean that all of the services are enabled.</span></span>
  
<span data-ttu-id="1a8f7-p119">이 기능 들은 작동 방식을 이해 하면 했으므로 라이선스를 발급 및 지정 된 서비스와 같은 명령을 사용 하 여 모든 사용 하지 않도록 설정 하는 방법을 보여줍니다 보겠습니다. 매우 눈에 띄는 소리는 하지만 사실이 처럼 매우를: 방금를 같은 명령에 _AddLicenses_ 및 _LicenseOptions_ 매개 변수를 모두을 포함 합니다. 즉, **LicenseOption** 개체를 먼저 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1a8f7-p119">Now that you understand how this all works, let's show you how you can issue a license and disable specified services, and all with the same command. That sounds pretty impressive, but, to be honest, there's really nothing to it: you just include both the  _AddLicenses_ and the _LicenseOptions_ parameters in the same command. In other words, you first create your **LicenseOption** object:</span></span>
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
```

<span data-ttu-id="1a8f7-207">및 다음, 이전에 설명한 것 처럼 하면 사용 하 여 _AddLicenses_ 및 _LicenseOptions_ 매개 변수를 모두 명령:</span><span class="sxs-lookup"><span data-stu-id="1a8f7-207">And then, as noted previously, you use both the  _AddLicenses_ and the _LicenseOptions_ parameters in your command:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -AddLicenses "litwareinc:ENTERPRISEPACK" -LicenseOptions $x
```

<span data-ttu-id="1a8f7-208">명령 발급할 Belinda Newman 새 라이선스를 발급 하지만 라이선스는 Skype에서 온라인 비즈니스에 대 한 ( `SHAREPOINTWAC`) 및 SharePoint Online ( `SHAREPOINTENTERPRISE`) 모두 비활성화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a8f7-208">That command will issue Belinda Newman a new license, but a license in which Skype for Business Online ( `SHAREPOINTWAC`) and SharePoint Online ( `SHAREPOINTENTERPRISE`) are both disabled.</span></span>
  
[<span data-ttu-id="1a8f7-209">맨위로 돌아가기</span><span class="sxs-lookup"><span data-stu-id="1a8f7-209">Return to top</span></span>](disable-access-to-services-with-office-365-powershell.md#RTT)
  
## <a name="new-to-office-365"></a><span data-ttu-id="1a8f7-210">Office 365의 새로운 기능</span><span class="sxs-lookup"><span data-stu-id="1a8f7-210">New to Office 365?</span></span>
<span data-ttu-id="1a8f7-211"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="1a8f7-211"></span></span>

||
|:-----|
|<span data-ttu-id="1a8f7-p120">![LinkedIn 학습에 대 한 짧은 아이콘](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **새로 만들기를 Office 365?**         **Office 365 관리자 및 IT 전문가**, LinkedIn 학습에 의해 제공자에 대 한 무료 비디오 코스를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a8f7-p120">![The short icon for LinkedIn Learning](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **New to Office 365?**         Discover free video courses for **Office 365 admins and IT pros**, brought to you by LinkedIn Learning.</span></span> |
   
## <a name="see-also"></a><span data-ttu-id="1a8f7-214">See also</span><span class="sxs-lookup"><span data-stu-id="1a8f7-214">See also</span></span>
<span data-ttu-id="1a8f7-215"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="1a8f7-215"></span></span>

<span data-ttu-id="1a8f7-216">Office 365 PowerShell을 사용하여 사용자를 관리하는 방법에 대한 다음 추가 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1a8f7-216">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="1a8f7-217">삭제 하 고 사용자 계정을 Office 365 PowerShell로 복원</span><span class="sxs-lookup"><span data-stu-id="1a8f7-217">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="1a8f7-218">삭제 하 고 사용자 계정을 Office 365 PowerShell로 복원</span><span class="sxs-lookup"><span data-stu-id="1a8f7-218">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="1a8f7-219">Office 365 powershell 블록 사용자 계정</span><span class="sxs-lookup"><span data-stu-id="1a8f7-219">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="1a8f7-220">Office 365 PowerShell을 사용한 사용자 계정에 게 라이선스 할당</span><span class="sxs-lookup"><span data-stu-id="1a8f7-220">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="1a8f7-221">Office 365 PowerShell을 사용한 사용자 계정 만들기</span><span class="sxs-lookup"><span data-stu-id="1a8f7-221">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="1a8f7-222">이 항목에서 사용된 cmdlet에 대한 자세한 내용은 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="1a8f7-222">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="1a8f7-223">Get-content</span><span class="sxs-lookup"><span data-stu-id="1a8f7-223">Get-Content</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [<span data-ttu-id="1a8f7-224">Get-msolaccountsku</span><span class="sxs-lookup"><span data-stu-id="1a8f7-224">Get-MsolAccountSku</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [<span data-ttu-id="1a8f7-225">새 MsolLicenseOptions</span><span class="sxs-lookup"><span data-stu-id="1a8f7-225">New-MsolLicenseOptions</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691546)
    
- [<span data-ttu-id="1a8f7-226">Get-msoluser</span><span class="sxs-lookup"><span data-stu-id="1a8f7-226">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="1a8f7-227">New-msoluser</span><span class="sxs-lookup"><span data-stu-id="1a8f7-227">New-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [<span data-ttu-id="1a8f7-228">Set-msoluserlicense</span><span class="sxs-lookup"><span data-stu-id="1a8f7-228">Set-MsolUserLicense</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [<span data-ttu-id="1a8f7-229">ForEach 개체</span><span class="sxs-lookup"><span data-stu-id="1a8f7-229">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="1a8f7-230">Where-object</span><span class="sxs-lookup"><span data-stu-id="1a8f7-230">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
[<span data-ttu-id="1a8f7-231">맨위로 돌아가기</span><span class="sxs-lookup"><span data-stu-id="1a8f7-231">Return to top</span></span>](disable-access-to-services-with-office-365-powershell.md#RTT)
  

