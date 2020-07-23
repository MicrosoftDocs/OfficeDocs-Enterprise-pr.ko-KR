---
title: PowerShell을 사용 하 여 Microsoft 365 사용자 계정 속성 구성
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/16/2020
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
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: '요약: Microsoft 365 용 PowerShell을 사용 하 여 Microsoft 365 테 넌 트에서 개별 또는 여러 사용자 계정의 속성을 구성 합니다.'
ms.openlocfilehash: ccf9bf9930551ab1ee26ef7a1f69427cdc4871f5
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230854"
---
# <a name="configure-microsoft-365-user-account-properties-with-powershell"></a><span data-ttu-id="e9ed3-103">PowerShell을 사용 하 여 Microsoft 365 사용자 계정 속성 구성</span><span class="sxs-lookup"><span data-stu-id="e9ed3-103">Configure Microsoft 365 user account properties with PowerShell</span></span>

<span data-ttu-id="e9ed3-104">*이 문서는 Microsoft 365 Enterprise 및 Office 365 Enterprise에 모두 적용 됩니다.*</span><span class="sxs-lookup"><span data-stu-id="e9ed3-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="e9ed3-105">Microsoft 365 관리 센터를 사용 하 여 Microsoft 365 테 넌 트의 사용자 계정에 대 한 속성을 구성할 수 있지만 PowerShell을 사용 하 여 Microsoft 365 관리 센터에서 수행할 수 없는 몇 가지 작업을 실행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e9ed3-105">Although you can use the Microsoft 365 admin center to configure properties for the user accounts of your Microsoft 365 tenant, you can also use PowerShell and do some things that the Microsoft 365 admin center cannot.</span></span>
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="e9ed3-106">Graph 모듈용 Azure Active Directory PowerShell 사용하기</span><span class="sxs-lookup"><span data-stu-id="e9ed3-106">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="e9ed3-107">Graph 모듈에 대 한 Azure Active Directory PowerShell을 사용 하 여 사용자 계정 속성을 구성 하려면 [AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet을 사용 하 고 설정 하거나 변경할 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9ed3-107">To configure properties for user accounts with the Azure Active Directory PowerShell for Graph module, you use the [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="e9ed3-108">먼저 [Microsoft 365 테 넌 트에 연결](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)합니다.</span><span class="sxs-lookup"><span data-stu-id="e9ed3-108">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
   
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="e9ed3-109">특정 사용자 계정에 대 한 속성 변경</span><span class="sxs-lookup"><span data-stu-id="e9ed3-109">Change properties for a specific user account</span></span>

<span data-ttu-id="e9ed3-110">**-ObjectID** 매개 변수를 사용 하 여 계정을 식별 하 고 추가 매개 변수를 사용 하 여 특정 속성을 설정 하거나 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9ed3-110">You identify the account with the **-ObjectID** parameter and set or change specific properties with additional parameters.</span></span> <span data-ttu-id="e9ed3-111">가장 일반적인 매개 변수 목록은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e9ed3-111">Here's a list of the most common parameters.</span></span>
  
- <span data-ttu-id="e9ed3-112">-부서 " \<department name> "</span><span class="sxs-lookup"><span data-stu-id="e9ed3-112">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="e9ed3-113">-DisplayName " \<full user name> "</span><span class="sxs-lookup"><span data-stu-id="e9ed3-113">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="e9ed3-114">-FacsimilieTelephoneNumber " \<fax number> "</span><span class="sxs-lookup"><span data-stu-id="e9ed3-114">-FacsimilieTelephoneNumber "\<fax number>"</span></span>
    
- <span data-ttu-id="e9ed3-115">-GivenName " \<user first name> "</span><span class="sxs-lookup"><span data-stu-id="e9ed3-115">-GivenName "\<user first name>"</span></span>
    
- <span data-ttu-id="e9ed3-116">-성 " \<user last name> "</span><span class="sxs-lookup"><span data-stu-id="e9ed3-116">-Surname "\<user last name>"</span></span>
    
- <span data-ttu-id="e9ed3-117">-Mobile " \<mobile phone number> "</span><span class="sxs-lookup"><span data-stu-id="e9ed3-117">-Mobile "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="e9ed3-118">-JobTitle " \<job title> "</span><span class="sxs-lookup"><span data-stu-id="e9ed3-118">-JobTitle "\<job title>"</span></span>
    
- <span data-ttu-id="e9ed3-119">-PreferredLanguage " \<language> "</span><span class="sxs-lookup"><span data-stu-id="e9ed3-119">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="e9ed3-120">-StreetAddress " \<street address> "</span><span class="sxs-lookup"><span data-stu-id="e9ed3-120">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="e9ed3-121">-구/군/시 " \<city name> "</span><span class="sxs-lookup"><span data-stu-id="e9ed3-121">-City "\<city name>"</span></span>
    
- <span data-ttu-id="e9ed3-122">-State " \<state name> "</span><span class="sxs-lookup"><span data-stu-id="e9ed3-122">-State "\<state name>"</span></span>
    
- <span data-ttu-id="e9ed3-123">-PostalCode " \<postal code> "</span><span class="sxs-lookup"><span data-stu-id="e9ed3-123">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="e9ed3-124">-Country " \<country name> "</span><span class="sxs-lookup"><span data-stu-id="e9ed3-124">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="e9ed3-125">-TelephoneNumber " \<office phone number> "</span><span class="sxs-lookup"><span data-stu-id="e9ed3-125">-TelephoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="e9ed3-126">-UsageLocation " \<2-character country or region code> "</span><span class="sxs-lookup"><span data-stu-id="e9ed3-126">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="e9ed3-127">ISO 3166-1 alpha-2 (A2) 두 자리 국가 또는 지역 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="e9ed3-127">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="e9ed3-128">추가 매개 변수에 대해서는 [AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) 을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="e9ed3-128">See [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) for additional parameters.</span></span>


<span data-ttu-id="e9ed3-129">사용자 계정의 사용자 계정 이름을 표시 하려면 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9ed3-129">To display the User Principal Name for your user accounts, run the following command.</span></span>
  
```powershell
Get-AzureADUser | Sort UserPrincipalName | Select UserPrincipalName | More
```

<span data-ttu-id="e9ed3-130">이 명령은 PowerShell에 다음을 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9ed3-130">This command instructs PowerShell to:</span></span>
  
- <span data-ttu-id="e9ed3-131">사용자 계정 (**AzureADUser**)에 대 한 모든 정보를 가져오고 다음 명령 ()으로 전송 **|** 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9ed3-131">Get all of the information on the user accounts (**Get-AzureADUser**) and send it to the next command (**|**).</span></span>
    
- <span data-ttu-id="e9ed3-132">사용자 계정 이름 목록을 사전순 (**Sort UserPrincipalName**)으로 정렬 하 고 다음 명령 ()으로 보냅니다 **|** .</span><span class="sxs-lookup"><span data-stu-id="e9ed3-132">Sort the list of User Principal Names alphabetically (**Sort UserPrincipalName**) and send it to the next command (**|**).</span></span>
    
- <span data-ttu-id="e9ed3-133">각 계정에 대해 사용자 계정 이름 속성을 표시 합니다 (**UserPrincipalName 선택**).</span><span class="sxs-lookup"><span data-stu-id="e9ed3-133">Display just the User Principal Name property for each account (**Select UserPrincipalName**).</span></span>

- <span data-ttu-id="e9ed3-134">한**화면을 한**번에 한 화면씩 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9ed3-134">Display them one screen at a time (**More**).</span></span>
    
<span data-ttu-id="e9ed3-135">이 명령에는 모든 계정이 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e9ed3-135">This command will list all of your accounts.</span></span> <span data-ttu-id="e9ed3-136">표시 이름 (이름과 성)을 기준으로 계정의 사용자 계정 이름을 표시 하려면 아래에 **$userName** 변수를 입력 하 \< and > 고 (문자 제거) 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9ed3-136">If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```powershell
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="e9ed3-137">이 예에서는 Caleb 창턱의 표시 이름을 사용 하 여 사용자 계정에 대 한 사용자 보안 주체 이름을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9ed3-137">This example displays the User Principal Name for the user account with the display name of Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="e9ed3-138">**$Upn** 변수를 사용 하 여 개별 계정을 표시 이름에 따라 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e9ed3-138">By using a **$upn** variable, you can make changes to individual accounts based on their display name.</span></span> <span data-ttu-id="e9ed3-139">다음은 Belinda Newman의 사용 위치를 프랑스로 설정 하 고 사용자 계정 이름이 아닌 표시 이름을 지정 하는 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="e9ed3-139">Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```powershell
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="e9ed3-140">모든 사용자 계정에 대 한 속성 변경</span><span class="sxs-lookup"><span data-stu-id="e9ed3-140">Change properties for all user accounts</span></span>

<span data-ttu-id="e9ed3-141">모든 사용자의 속성을 변경 하려면 **AzureADUser** 및 **AzureADUser** cmdlet을 조합 하 여 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e9ed3-141">To change properties for all users, you can use the combination of the **Get-AzureADUser** and **Set-AzureADUser** cmdlets.</span></span> <span data-ttu-id="e9ed3-142">다음 예에서는 모든 사용자의 사용 위치를 프랑스로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="e9ed3-142">The following example changes the usage location for all users to France:</span></span>
  
```powershell
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="e9ed3-143">이 명령은 PowerShell에 다음을 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9ed3-143">This command instructs PowerShell to:</span></span>
  
- <span data-ttu-id="e9ed3-144">사용자 계정 (**AzureADUser**)에 대 한 모든 정보를 가져오고 다음 명령 ()으로 전송 **|** 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9ed3-144">Get all of the information on the user accounts (**Get-AzureADUser**) and send it to the next command (**|**).</span></span>
    
- <span data-ttu-id="e9ed3-145">사용자 위치를 프랑스 (**AzureADUser-UsageLocation "FR"**)로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9ed3-145">Set the user location to France (**Set-AzureADUser -UsageLocation "FR"**).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="e9ed3-146">특정 사용자 계정 집합의 속성 변경</span><span class="sxs-lookup"><span data-stu-id="e9ed3-146">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="e9ed3-147">특정 사용자 계정 집합의 속성을 변경 하려면 **AzureADUser**, **Where**및 **AzureADUser** cmdlet을 조합 하 여 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e9ed3-147">To change properties for a specific set of user account, you can use the combination of the **Get-AzureADUser**, **Where**, and **Set-AzureADUser** cmdlets.</span></span> <span data-ttu-id="e9ed3-148">다음 예에서는 프랑스 회계 부서의 모든 사용자의 사용 위치를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="e9ed3-148">The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```powershell
Get-AzureADUser | Where {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="e9ed3-149">이 명령은 PowerShell에 다음을 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9ed3-149">This command instructs PowerShell to:</span></span>
  
- <span data-ttu-id="e9ed3-150">사용자 계정 (**AzureADUser**)에 대 한 모든 정보를 가져오고 다음 명령 ()으로 전송 **|** 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9ed3-150">Get all of the information on the user accounts (**Get-AzureADUser**) and send it to the next command (**|**).</span></span>
    
- <span data-ttu-id="e9ed3-151">부서 속성이 "회계"로 설정 된 모든 사용자 계정을 찾습니다 (**여기서 {$ _. 부서-eq "Accounting"}**)를 사용 하 고 결과 정보를 다음 명령 ( **|** )으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="e9ed3-151">Find all of the user accounts that have their Department property set to "Accounting" (**Where {$_.Department -eq "Accounting"}**) and send the resulting information to the next command (**|**).</span></span>
    
- <span data-ttu-id="e9ed3-152">사용자 위치를 프랑스 (**AzureADUser-UsageLocation "FR"**)로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9ed3-152">Set the user location to France (**Set-AzureADUser -UsageLocation "FR"**).</span></span>
    
## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="e9ed3-153">Windows PowerShell용 Microsoft Azure Active Directory 모듈 사용하기</span><span class="sxs-lookup"><span data-stu-id="e9ed3-153">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="e9ed3-154">Windows PowerShell 용 Microsoft Azure Active Directory 모듈을 사용 하 여 사용자 계정에 대 한 속성을 구성 하려면 **get-msoluser** cmdlet을 사용 하 고 설정 하거나 변경할 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9ed3-154">To configure properties for user accounts with the Microsoft Azure Active Directory Module for Windows PowerShell, you use the **Set-MsolUser** cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="e9ed3-155">먼저 [Microsoft 365 테 넌 트에 연결](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)합니다.</span><span class="sxs-lookup"><span data-stu-id="e9ed3-155">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
  
>[!Note]
><span data-ttu-id="e9ed3-156">PowerShell Core는 Windows PowerShell용 Microsoft Azure Active Directory 모듈 및 이름에 **Msol**이 있는 cmdlet을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e9ed3-156">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="e9ed3-157">이러한 cmdlet을 계속 사용하려면 Windows PowerShell에서 이를 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9ed3-157">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="e9ed3-158">특정 사용자 계정에 대 한 속성 변경</span><span class="sxs-lookup"><span data-stu-id="e9ed3-158">Change properties for a specific user account</span></span>

<span data-ttu-id="e9ed3-159">특정 사용자 계정에 대 한 속성을 구성 하려면 [get-msoluser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)) cmdlet을 사용 하 고 설정 하거나 변경할 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9ed3-159">To configure properties for a specific user account, you use the [Set-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="e9ed3-160">**-UserPrincipalName** 매개 변수를 사용 하 여 계정을 식별 하 고 추가 매개 변수를 사용 하 여 특정 속성을 설정 하거나 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9ed3-160">You identify the account with the **-UserPrincipalName** parameter and set or change specific properties with additional parameters.</span></span> <span data-ttu-id="e9ed3-161">가장 일반적인 매개 변수 목록은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e9ed3-161">Here is a list of the most common parameters.</span></span>
  
- <span data-ttu-id="e9ed3-162">-구/군/시 " \<city name> "</span><span class="sxs-lookup"><span data-stu-id="e9ed3-162">-City "\<city name>"</span></span>
    
- <span data-ttu-id="e9ed3-163">-Country " \<country name> "</span><span class="sxs-lookup"><span data-stu-id="e9ed3-163">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="e9ed3-164">-부서 " \<department name> "</span><span class="sxs-lookup"><span data-stu-id="e9ed3-164">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="e9ed3-165">-DisplayName " \<full user name> "</span><span class="sxs-lookup"><span data-stu-id="e9ed3-165">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="e9ed3-166">-Fax " \<fax number> "</span><span class="sxs-lookup"><span data-stu-id="e9ed3-166">-Fax "\<fax number>"</span></span>
    
- <span data-ttu-id="e9ed3-167">-FirstName " \<user first name> "</span><span class="sxs-lookup"><span data-stu-id="e9ed3-167">-FirstName "\<user first name>"</span></span>
    
- <span data-ttu-id="e9ed3-168">-LastName " \<user last name> "</span><span class="sxs-lookup"><span data-stu-id="e9ed3-168">-LastName "\<user last name>"</span></span>
    
- <span data-ttu-id="e9ed3-169">-MobilePhone " \<mobile phone number> "</span><span class="sxs-lookup"><span data-stu-id="e9ed3-169">-MobilePhone "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="e9ed3-170">-Office " \<office location> "</span><span class="sxs-lookup"><span data-stu-id="e9ed3-170">-Office "\<office location>"</span></span>
    
- <span data-ttu-id="e9ed3-171">-PhoneNumber " \<office phone number> "</span><span class="sxs-lookup"><span data-stu-id="e9ed3-171">-PhoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="e9ed3-172">-PostalCode " \<postal code> "</span><span class="sxs-lookup"><span data-stu-id="e9ed3-172">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="e9ed3-173">-PreferredLanguage " \<language> "</span><span class="sxs-lookup"><span data-stu-id="e9ed3-173">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="e9ed3-174">-State " \<state name> "</span><span class="sxs-lookup"><span data-stu-id="e9ed3-174">-State "\<state name>"</span></span>
    
- <span data-ttu-id="e9ed3-175">-StreetAddress " \<street address> "</span><span class="sxs-lookup"><span data-stu-id="e9ed3-175">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="e9ed3-176">-Title " \<title name> "</span><span class="sxs-lookup"><span data-stu-id="e9ed3-176">-Title "\<title name>"</span></span>
    
- <span data-ttu-id="e9ed3-177">-UsageLocation " \<2-character country or region code> "</span><span class="sxs-lookup"><span data-stu-id="e9ed3-177">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="e9ed3-178">ISO 3166-1 alpha-2 (A2) 두 자리 국가 또는 지역 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="e9ed3-178">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="e9ed3-179">추가 매개 변수에 대해서는 [get-msoluser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)) 을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="e9ed3-179">See [Set-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)) for additional parameters.</span></span>

<span data-ttu-id="e9ed3-180">모든 사용자의 사용자 계정 이름을 보려면 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9ed3-180">To see the User Principal Names of all your users, run the following command.</span></span>
  
```powershell
Get-MSolUser | Sort UserPrincipalName | Select UserPrincipalName | More
```

<span data-ttu-id="e9ed3-181">이 명령은 PowerShell에 다음을 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9ed3-181">This command instructs PowerShell to:</span></span>
  
- <span data-ttu-id="e9ed3-182">사용자 계정 (**get-msoluser**)에 대 한 모든 정보를 가져오고 다음 명령 ()으로 전송 **|** 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9ed3-182">Get all of the information on the user accounts (**Get-MsolUser**) and send it to the next command (**|**).</span></span>
    
- <span data-ttu-id="e9ed3-183">사용자 계정 이름 목록을 사전순 (**Sort UserPrincipalName**)으로 정렬 하 고 다음 명령 ()으로 보냅니다 **|** .</span><span class="sxs-lookup"><span data-stu-id="e9ed3-183">Sort the list of User Principal Names alphabetically (**Sort UserPrincipalName**) and send it to the next command (**|**).</span></span>
    
- <span data-ttu-id="e9ed3-184">각 계정에 대해 사용자 계정 이름 속성을 표시 합니다 (**UserPrincipalName 선택**).</span><span class="sxs-lookup"><span data-stu-id="e9ed3-184">Display just the User Principal Name property for each account (**Select UserPrincipalName**).</span></span>
    
- <span data-ttu-id="e9ed3-185">한**화면을 한**번에 한 화면씩 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9ed3-185">Display them one screen at a time (**More**).</span></span>
    
<span data-ttu-id="e9ed3-186">이 명령에는 모든 계정이 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e9ed3-186">This command will list all of your accounts.</span></span> <span data-ttu-id="e9ed3-187">표시 이름 (이름과 성)을 기준으로 계정의 사용자 계정 이름을 표시 하려면 아래에 **$userName** 변수를 입력 하 \< and > 고 (문자 제거) 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9ed3-187">If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```powershell
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="e9ed3-188">이 예제에서는 Caleb 창턱 라는 사용자에 대 한 사용자 계정 이름을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9ed3-188">This example displays the User Principal Name for the user named Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="e9ed3-189">**$Upn** 변수를 사용 하 여 개별 계정을 표시 이름에 따라 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e9ed3-189">By using a **$upn** variable, you can make changes to individual accounts based on their display name.</span></span> <span data-ttu-id="e9ed3-190">다음은 Belinda Newman의 사용 위치를 프랑스로 설정 하 고 사용자 계정 이름이 아닌 표시 이름을 지정 하는 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="e9ed3-190">Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```powershell
$userName="<display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="e9ed3-191">모든 사용자 계정에 대 한 속성 변경</span><span class="sxs-lookup"><span data-stu-id="e9ed3-191">Change properties for all user accounts</span></span>

<span data-ttu-id="e9ed3-p110">모든 사용자에 대한 속성을 변경하려면 **Get-msoluser** 및 **Set-msoluser** cmdlet의 조합을 사용합니다. 다음 예에서는 모든 사용자의 사용 위치를 프랑스로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="e9ed3-p110">To change properties for all users, you can use the combination of the **Get-MsolUser** and **Set-MsolUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```powershell
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="e9ed3-194">이 명령은 PowerShell에 다음을 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9ed3-194">This command instructs PowerShell to:</span></span>
  
- <span data-ttu-id="e9ed3-195">사용자 계정 (**get-msoluser**)에 대 한 모든 정보를 가져오고 다음 명령 ()으로 전송 **|** 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9ed3-195">Get all of the information on the user accounts (**Get-MsolUser**) and send it to the next command (**|**).</span></span>
    
- <span data-ttu-id="e9ed3-196">사용자 위치를 프랑스 (**get-msoluser-UsageLocation "FR"**)로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9ed3-196">Set the user location to France (**Set-MsolUser -UsageLocation "FR"**).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="e9ed3-197">특정 사용자 계정 집합의 속성 변경</span><span class="sxs-lookup"><span data-stu-id="e9ed3-197">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="e9ed3-198">특정 사용자 계정 집합의 속성을 변경 하려면 **get-msoluser**, **Where**및 **get-msoluser** cmdlet을 조합 하 여 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e9ed3-198">To change properties for a specific set of user account, you can use the combination of the **Get-MsolUser**, **Where**, and **Set-MsolUser** cmdlets.</span></span> <span data-ttu-id="e9ed3-199">다음 예에서는 프랑스 회계 부서의 모든 사용자의 사용 위치를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="e9ed3-199">The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```powershell
Get-MsolUser | Where {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="e9ed3-200">이 명령은 PowerShell에 다음을 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9ed3-200">This command instructs PowerShell to:</span></span>
  
- <span data-ttu-id="e9ed3-201">사용자 계정 (**get-msoluser**)에 대 한 모든 정보를 가져오고 다음 명령 ()으로 전송 **|** 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9ed3-201">Get all of the information on the user accounts (**Get-MsolUser**) and send it to the next command (**|**).</span></span>
    
- <span data-ttu-id="e9ed3-202">부서 속성이 "회계"로 설정 된 모든 사용자 계정을 찾습니다 (**여기서 {$ _. 부서-eq "Accounting"}**)를 사용 하 고 결과 정보를 다음 명령 ( **|** )으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="e9ed3-202">Find all of the user accounts that have their Department property set to "Accounting" (**Where {$_.Department -eq "Accounting"}**) and send the resulting information to the next command (**|**).</span></span>
    
- <span data-ttu-id="e9ed3-203">사용자 위치를 프랑스 (**get-msoluser-UsageLocation "FR"**)로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9ed3-203">Set the user location to France (**Set-MsolUser -UsageLocation "FR"**).</span></span>
    

## <a name="see-also"></a><span data-ttu-id="e9ed3-204">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e9ed3-204">See also</span></span>

[<span data-ttu-id="e9ed3-205">PowerShell을 사용 하 여 Microsoft 365 사용자 계정, 라이선스 및 그룹 관리</span><span class="sxs-lookup"><span data-stu-id="e9ed3-205">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="e9ed3-206">PowerShell을 사용 하 여 Microsoft 365 관리</span><span class="sxs-lookup"><span data-stu-id="e9ed3-206">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="e9ed3-207">Microsoft 365 용 PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="e9ed3-207">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)
