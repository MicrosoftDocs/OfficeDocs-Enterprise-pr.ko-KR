---
title: Office 365 PowerShell를 사용 하 여 사용자 계정 속성 구성
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/16/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: '요약: Office 365 PowerShell을 사용 하 여 Office 365 테 넌 트에서 개별 또는 여러 사용자 계정에 대 한 속성을 구성 합니다.'
ms.openlocfilehash: 211210dad54cb0af772af7dc611bc2c0fdf6035a
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841605"
---
# <a name="configure-user-account-properties-with-office-365-powershell"></a><span data-ttu-id="f8fdb-103">Office 365 PowerShell를 사용 하 여 사용자 계정 속성 구성</span><span class="sxs-lookup"><span data-stu-id="f8fdb-103">Configure user account properties with Office 365 PowerShell</span></span>

<span data-ttu-id="f8fdb-104">Microsoft 365 관리 센터를 사용 하 여 Office 365 테 넌 트의 사용자 계정에 대 한 속성을 구성할 수 있지만 Office 365 PowerShell을 사용 하 고 관리 센터에서 수행할 수 없는 몇 가지 작업을 실행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8fdb-104">Although you can use the Microsoft 365 admin center to configure properties for the user accounts of your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the admin center cannot.</span></span>
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="f8fdb-105">Graph 모듈용 Azure Active Directory PowerShell 사용하기</span><span class="sxs-lookup"><span data-stu-id="f8fdb-105">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="f8fdb-106">Graph 모듈에 대 한 Azure Active Directory PowerShell을 사용 하 여 사용자 계정 속성을 구성 하려면 [AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet을 사용 하 고 설정 하거나 변경할 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8fdb-106">To configure properties for user accounts with the Azure Active Directory PowerShell for Graph module, you use the [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="f8fdb-107">먼저, [Office 365 테넌트에 연결](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)합니다.</span><span class="sxs-lookup"><span data-stu-id="f8fdb-107">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
   
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="f8fdb-108">특정 사용자 계정에 대 한 속성 변경</span><span class="sxs-lookup"><span data-stu-id="f8fdb-108">Change properties for a specific user account</span></span>

<span data-ttu-id="f8fdb-109">**-ObjectID** 매개 변수를 사용 하 여 계정을 식별 하 고 추가 매개 변수를 사용 하 여 특정 속성을 설정 하거나 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8fdb-109">You identify the account with the **-ObjectID** parameter and set or change specific properties with additional parameters.</span></span> <span data-ttu-id="f8fdb-110">가장 일반적인 매개 변수 목록은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f8fdb-110">Here's a list of the most common parameters.</span></span>
  
- <span data-ttu-id="f8fdb-111">-부서 "\<부서 이름>"</span><span class="sxs-lookup"><span data-stu-id="f8fdb-111">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="f8fdb-112">-DisplayName "\<전체 사용자 이름>"</span><span class="sxs-lookup"><span data-stu-id="f8fdb-112">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="f8fdb-113">-FacsimilieTelephoneNumber "\<팩스 번호>"</span><span class="sxs-lookup"><span data-stu-id="f8fdb-113">-FacsimilieTelephoneNumber "\<fax number>"</span></span>
    
- <span data-ttu-id="f8fdb-114">-GivenName "\<사용자 이름>"</span><span class="sxs-lookup"><span data-stu-id="f8fdb-114">-GivenName "\<user first name>"</span></span>
    
- <span data-ttu-id="f8fdb-115">-성 "\<사용자 성>"</span><span class="sxs-lookup"><span data-stu-id="f8fdb-115">-Surname "\<user last name>"</span></span>
    
- <span data-ttu-id="f8fdb-116">-Mobile "\<휴대폰 번호>"</span><span class="sxs-lookup"><span data-stu-id="f8fdb-116">-Mobile "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="f8fdb-117">-JobTitle "\<직책>"</span><span class="sxs-lookup"><span data-stu-id="f8fdb-117">-JobTitle "\<job title>"</span></span>
    
- <span data-ttu-id="f8fdb-118">-PreferredLanguage "\<language>"</span><span class="sxs-lookup"><span data-stu-id="f8fdb-118">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="f8fdb-119">-StreetAddress "\<주소>"</span><span class="sxs-lookup"><span data-stu-id="f8fdb-119">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="f8fdb-120">-도시명 "\<구/군/시 이름>"</span><span class="sxs-lookup"><span data-stu-id="f8fdb-120">-City "\<city name>"</span></span>
    
- <span data-ttu-id="f8fdb-121">-State "\<상태 이름>"</span><span class="sxs-lookup"><span data-stu-id="f8fdb-121">-State "\<state name>"</span></span>
    
- <span data-ttu-id="f8fdb-122">-PostalCode "\<우편 번호>"</span><span class="sxs-lookup"><span data-stu-id="f8fdb-122">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="f8fdb-123">-Country "\<국가 이름>"</span><span class="sxs-lookup"><span data-stu-id="f8fdb-123">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="f8fdb-124">-TelephoneNumber "\<사무실 전화 번호>"</span><span class="sxs-lookup"><span data-stu-id="f8fdb-124">-TelephoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="f8fdb-125">-UsageLocation "\<2 자리 국가 또는 지역 코드>"</span><span class="sxs-lookup"><span data-stu-id="f8fdb-125">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="f8fdb-126">ISO 3166-1 alpha-2 (A2) 두 자리 국가 또는 지역 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="f8fdb-126">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="f8fdb-127">추가 매개 변수에 대해서는 [AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) 을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="f8fdb-127">See [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) for additional parameters.</span></span>


<span data-ttu-id="f8fdb-128">사용자 계정의 사용자 계정 이름을 표시 하려면 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8fdb-128">To display the User Principal Name for your user accounts, run the following command.</span></span>
  
```powershell
Get-AzureADUser | Sort UserPrincipalName | Select UserPrincipalName | More
```

<span data-ttu-id="f8fdb-129">이 명령은 Office 365 PowerShell에 다음과 같이 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8fdb-129">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="f8fdb-130">사용자 계정 ( **AzureADUser** )에 대 한 모든 정보를 가져오고 다음 명령 ( **|** )으로 전송 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8fdb-130">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="f8fdb-131">사용자 계정 이름 목록을 사전순 ( **Sort UserPrincipalName** )으로 정렬 하 고 다음 명령 ( **|** )으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="f8fdb-131">Sort the list of User Principal Names alphabetically ( **Sort UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="f8fdb-132">각 계정에 대해 사용자 계정 이름 속성을 표시 합니다 ( **UserPrincipalName 선택** ).</span><span class="sxs-lookup"><span data-stu-id="f8fdb-132">Display just the User Principal Name property for each account ( **Select UserPrincipalName** ).</span></span>

- <span data-ttu-id="f8fdb-133">한 **화면을 한** 번에 한 화면씩 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8fdb-133">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="f8fdb-134">이 명령에는 모든 계정이 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f8fdb-134">This command will list all of your accounts.</span></span> <span data-ttu-id="f8fdb-135">표시 이름 (이름 및 성)을 기준으로 계정의 사용자 계정 이름을 표시 하려면 다음 명령을 실행 하 여 아래의 **$userName** 변수를 입력 합니다 ( \< 및 > 문자 제거).</span><span class="sxs-lookup"><span data-stu-id="f8fdb-135">If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```powershell
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="f8fdb-136">이 예에서는 Caleb 창턱의 표시 이름을 사용 하 여 사용자 계정에 대 한 사용자 보안 주체 이름을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8fdb-136">This example displays the User Principal Name for the user account with the display name of Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="f8fdb-137">**$Upn** 변수를 사용 하 여 개별 계정을 표시 이름에 따라 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8fdb-137">By using a **$upn** variable, you can make changes to individual accounts based on their display name.</span></span> <span data-ttu-id="f8fdb-138">다음은 Belinda Newman의 사용 위치를 프랑스로 설정 하 고 사용자 계정 이름이 아닌 표시 이름을 지정 하는 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="f8fdb-138">Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```powershell
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="f8fdb-139">모든 사용자 계정에 대 한 속성 변경</span><span class="sxs-lookup"><span data-stu-id="f8fdb-139">Change properties for all user accounts</span></span>

<span data-ttu-id="f8fdb-140">모든 사용자의 속성을 변경 하려면 **AzureADUser** 및 **AzureADUser** cmdlet을 조합 하 여 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8fdb-140">To change properties for all users, you can use the combination of the **Get-AzureADUser** and **Set-AzureADUser** cmdlets.</span></span> <span data-ttu-id="f8fdb-141">다음 예에서는 모든 사용자의 사용 위치를 프랑스로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="f8fdb-141">The following example changes the usage location for all users to France:</span></span>
  
```powershell
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="f8fdb-142">이 명령은 Office 365 PowerShell에 다음과 같이 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8fdb-142">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="f8fdb-143">사용자 계정 ( **AzureADUser** )에 대 한 모든 정보를 가져오고 다음 명령 ( **|** )으로 전송 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8fdb-143">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="f8fdb-144">사용자 위치를 프랑스 ( **AzureADUser-UsageLocation "FR"** )로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8fdb-144">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="f8fdb-145">특정 사용자 계정 집합의 속성 변경</span><span class="sxs-lookup"><span data-stu-id="f8fdb-145">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="f8fdb-146">특정 사용자 계정 집합의 속성을 변경 하려면 **AzureADUser**, **Where**및 **AzureADUser** cmdlet을 조합 하 여 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8fdb-146">To change properties for a specific set of user account, you can use the combination of the **Get-AzureADUser**, **Where**, and **Set-AzureADUser** cmdlets.</span></span> <span data-ttu-id="f8fdb-147">다음 예에서는 프랑스 회계 부서의 모든 사용자의 사용 위치를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="f8fdb-147">The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```powershell
Get-AzureADUser | Where {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="f8fdb-148">이 명령은 Office 365 PowerShell에 다음과 같이 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8fdb-148">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="f8fdb-149">사용자 계정 ( **AzureADUser** )에 대 한 모든 정보를 가져오고 다음 명령 ( **|** )으로 전송 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8fdb-149">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="f8fdb-150">부서 속성이 "회계"로 설정 된 모든 사용자 계정을 찾습니다 ( **여기서 {$ _. 부서-eq "Accounting"}** )를 사용 하 고 결과 정보를 다음 명령 ( **|** )으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="f8fdb-150">Find all of the user accounts that have their Department property set to "Accounting" ( **Where {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="f8fdb-151">사용자 위치를 프랑스 ( **AzureADUser-UsageLocation "FR"** )로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8fdb-151">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="f8fdb-152">Windows PowerShell용 Microsoft Azure Active Directory 모듈 사용하기</span><span class="sxs-lookup"><span data-stu-id="f8fdb-152">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="f8fdb-153">Windows PowerShell 용 Microsoft Azure Active Directory 모듈을 사용 하 여 사용자 계정에 대 한 속성을 구성 하려면 **get-msoluser** cmdlet을 사용 하 고 설정 하거나 변경할 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8fdb-153">To configure properties for user accounts with the Microsoft Azure Active Directory Module for Windows PowerShell, you use the **Set-MsolUser** cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="f8fdb-154">먼저, [Office 365 테넌트에 연결](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)합니다.</span><span class="sxs-lookup"><span data-stu-id="f8fdb-154">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
  
>[!Note]
><span data-ttu-id="f8fdb-155">PowerShell Core는 Windows PowerShell용 Microsoft Azure Active Directory 모듈 및 이름에 **Msol**이 있는 cmdlet을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f8fdb-155">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="f8fdb-156">이러한 cmdlet을 계속 사용하려면 Windows PowerShell에서 이를 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8fdb-156">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="f8fdb-157">특정 사용자 계정에 대 한 속성 변경</span><span class="sxs-lookup"><span data-stu-id="f8fdb-157">Change properties for a specific user account</span></span>

<span data-ttu-id="f8fdb-158">특정 사용자 계정에 대 한 속성을 구성 하려면 [get-msoluser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)) cmdlet을 사용 하 고 설정 하거나 변경할 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8fdb-158">To configure properties for a specific user account, you use the [Set-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="f8fdb-159">**-UserPrincipalName** 매개 변수를 사용 하 여 계정을 식별 하 고 추가 매개 변수를 사용 하 여 특정 속성을 설정 하거나 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8fdb-159">You identify the account with the **-UserPrincipalName** parameter and set or change specific properties with additional parameters.</span></span> <span data-ttu-id="f8fdb-160">가장 일반적인 매개 변수 목록은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f8fdb-160">Here is a list of the most common parameters.</span></span>
  
- <span data-ttu-id="f8fdb-161">-도시명 "\<구/군/시 이름>"</span><span class="sxs-lookup"><span data-stu-id="f8fdb-161">-City "\<city name>"</span></span>
    
- <span data-ttu-id="f8fdb-162">-Country "\<국가 이름>"</span><span class="sxs-lookup"><span data-stu-id="f8fdb-162">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="f8fdb-163">-부서 "\<부서 이름>"</span><span class="sxs-lookup"><span data-stu-id="f8fdb-163">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="f8fdb-164">-DisplayName "\<전체 사용자 이름>"</span><span class="sxs-lookup"><span data-stu-id="f8fdb-164">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="f8fdb-165">-Fax "\<팩스 번호>"</span><span class="sxs-lookup"><span data-stu-id="f8fdb-165">-Fax "\<fax number>"</span></span>
    
- <span data-ttu-id="f8fdb-166">-FirstName "\<사용자 이름>"</span><span class="sxs-lookup"><span data-stu-id="f8fdb-166">-FirstName "\<user first name>"</span></span>
    
- <span data-ttu-id="f8fdb-167">-LastName "\<user last name>"</span><span class="sxs-lookup"><span data-stu-id="f8fdb-167">-LastName "\<user last name>"</span></span>
    
- <span data-ttu-id="f8fdb-168">-MobilePhone "\<휴대폰 번호>"</span><span class="sxs-lookup"><span data-stu-id="f8fdb-168">-MobilePhone "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="f8fdb-169">-Office "\<사무실 위치>"</span><span class="sxs-lookup"><span data-stu-id="f8fdb-169">-Office "\<office location>"</span></span>
    
- <span data-ttu-id="f8fdb-170">-PhoneNumber "\<사무실 전화 번호>"</span><span class="sxs-lookup"><span data-stu-id="f8fdb-170">-PhoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="f8fdb-171">-PostalCode "\<우편 번호>"</span><span class="sxs-lookup"><span data-stu-id="f8fdb-171">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="f8fdb-172">-PreferredLanguage "\<language>"</span><span class="sxs-lookup"><span data-stu-id="f8fdb-172">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="f8fdb-173">-State "\<상태 이름>"</span><span class="sxs-lookup"><span data-stu-id="f8fdb-173">-State "\<state name>"</span></span>
    
- <span data-ttu-id="f8fdb-174">-StreetAddress "\<주소>"</span><span class="sxs-lookup"><span data-stu-id="f8fdb-174">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="f8fdb-175">-Title "\<제목 이름>"</span><span class="sxs-lookup"><span data-stu-id="f8fdb-175">-Title "\<title name>"</span></span>
    
- <span data-ttu-id="f8fdb-176">-UsageLocation "\<2 자리 국가 또는 지역 코드>"</span><span class="sxs-lookup"><span data-stu-id="f8fdb-176">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="f8fdb-177">ISO 3166-1 alpha-2 (A2) 두 자리 국가 또는 지역 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="f8fdb-177">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="f8fdb-178">추가 매개 변수에 대해서는 [get-msoluser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)) 을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="f8fdb-178">See [Set-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)) for additional parameters.</span></span>

<span data-ttu-id="f8fdb-179">모든 사용자의 사용자 계정 이름을 보려면 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8fdb-179">To see the User Principal Names of all your users, run the following command.</span></span>
  
```powershell
Get-MSolUser | Sort UserPrincipalName | Select UserPrincipalName | More
```

<span data-ttu-id="f8fdb-180">이 명령은 Office 365 PowerShell에 다음과 같이 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8fdb-180">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="f8fdb-181">사용자 계정 ( **get-msoluser** )에 대 한 모든 정보를 가져오고 다음 명령 ( **|** )으로 전송 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8fdb-181">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="f8fdb-182">사용자 계정 이름 목록을 사전순 ( **Sort UserPrincipalName** )으로 정렬 하 고 다음 명령 ( **|** )으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="f8fdb-182">Sort the list of User Principal Names alphabetically ( **Sort UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="f8fdb-183">각 계정에 대해 사용자 계정 이름 속성을 표시 합니다 ( **UserPrincipalName 선택** ).</span><span class="sxs-lookup"><span data-stu-id="f8fdb-183">Display just the User Principal Name property for each account ( **Select UserPrincipalName** ).</span></span>
    
- <span data-ttu-id="f8fdb-184">한 **화면을 한** 번에 한 화면씩 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8fdb-184">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="f8fdb-185">이 명령에는 모든 계정이 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f8fdb-185">This command will list all of your accounts.</span></span> <span data-ttu-id="f8fdb-186">표시 이름 (이름 및 성)을 기준으로 계정의 사용자 계정 이름을 표시 하려면 다음 명령을 실행 하 여 아래의 **$userName** 변수를 입력 합니다 ( \< 및 > 문자 제거).</span><span class="sxs-lookup"><span data-stu-id="f8fdb-186">If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```powershell
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="f8fdb-187">이 예제에서는 Caleb 창턱 라는 사용자에 대 한 사용자 계정 이름을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8fdb-187">This example displays the User Principal Name for the user named Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="f8fdb-188">**$Upn** 변수를 사용 하 여 개별 계정을 표시 이름에 따라 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8fdb-188">By using a **$upn** variable, you can make changes to individual accounts based on their display name.</span></span> <span data-ttu-id="f8fdb-189">다음은 Belinda Newman의 사용 위치를 프랑스로 설정 하 고 사용자 계정 이름이 아닌 표시 이름을 지정 하는 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="f8fdb-189">Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```powershell
$userName="<display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="f8fdb-190">모든 사용자 계정에 대 한 속성 변경</span><span class="sxs-lookup"><span data-stu-id="f8fdb-190">Change properties for all user accounts</span></span>

<span data-ttu-id="f8fdb-p110">모든 사용자에 대한 속성을 변경하려면 **Get-msoluser** 및 **Set-msoluser** cmdlet의 조합을 사용합니다. 다음 예에서는 모든 사용자의 사용 위치를 프랑스로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="f8fdb-p110">To change properties for all users, you can use the combination of the **Get-MsolUser** and **Set-MsolUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```powershell
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="f8fdb-193">이 명령은 Office 365 PowerShell에 다음과 같이 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8fdb-193">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="f8fdb-194">사용자 계정 ( **get-msoluser** )에 대 한 모든 정보를 가져오고 다음 명령 ( **|** )으로 전송 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8fdb-194">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="f8fdb-195">사용자 위치를 프랑스 ( **get-msoluser-UsageLocation "FR"** )로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8fdb-195">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="f8fdb-196">특정 사용자 계정 집합의 속성 변경</span><span class="sxs-lookup"><span data-stu-id="f8fdb-196">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="f8fdb-197">특정 사용자 계정 집합의 속성을 변경 하려면 **get-msoluser**, **Where**및 **get-msoluser** cmdlet을 조합 하 여 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8fdb-197">To change properties for a specific set of user account, you can use the combination of the **Get-MsolUser**, **Where**, and **Set-MsolUser** cmdlets.</span></span> <span data-ttu-id="f8fdb-198">다음 예에서는 프랑스 회계 부서의 모든 사용자의 사용 위치를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="f8fdb-198">The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```powershell
Get-MsolUser | Where {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="f8fdb-199">이 명령은 Office 365 PowerShell에 다음과 같이 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8fdb-199">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="f8fdb-200">사용자 계정 ( **get-msoluser** )에 대 한 모든 정보를 가져오고 다음 명령 ( **|** )으로 전송 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8fdb-200">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="f8fdb-201">부서 속성이 "회계"로 설정 된 모든 사용자 계정을 찾습니다 ( **여기서 {$ _. 부서-eq "Accounting"}** )를 사용 하 고 결과 정보를 다음 명령 ( **|** )으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="f8fdb-201">Find all of the user accounts that have their Department property set to "Accounting" ( **Where {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="f8fdb-202">사용자 위치를 프랑스 ( **get-msoluser-UsageLocation "FR"** )로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8fdb-202">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    

## <a name="see-also"></a><span data-ttu-id="f8fdb-203">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f8fdb-203">See also</span></span>

[<span data-ttu-id="f8fdb-204">Office 365 PowerShell을 사용 하 여 사용자 계정, 라이선스 및 그룹 관리</span><span class="sxs-lookup"><span data-stu-id="f8fdb-204">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="f8fdb-205">Office 365 PowerShell 사용한 Office 365 관리</span><span class="sxs-lookup"><span data-stu-id="f8fdb-205">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="f8fdb-206">Office 365 PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="f8fdb-206">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
