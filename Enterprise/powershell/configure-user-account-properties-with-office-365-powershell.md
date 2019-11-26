---
title: Office 365 PowerShell를 사용 하 여 사용자 계정 속성 구성
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/07/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: '요약: Office 365 PowerShell을 사용 하 여 Office 365 테 넌 트에서 개별 또는 여러 사용자 계정에 대 한 속성을 구성 합니다.'
ms.openlocfilehash: 67ce7d3c57f286f0b2365aa2503fdf1c8bc13429
ms.sourcegitcommit: 4b057db053e93b0165f1ec6c4799cff4c2852566
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/25/2019
ms.locfileid: "39257659"
---
# <a name="configure-user-account-properties-with-office-365-powershell"></a><span data-ttu-id="e8700-103">Office 365 PowerShell를 사용 하 여 사용자 계정 속성 구성</span><span class="sxs-lookup"><span data-stu-id="e8700-103">Configure user account properties with Office 365 PowerShell</span></span>

 <span data-ttu-id="e8700-104">**요약:** Office 365 PowerShell을 사용 하 여 Office 365 테 넌 트에서 개별 또는 여러 사용자 계정에 대 한 속성을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8700-104">**Summary:** Use Office 365 PowerShell to configure properties of individual or multiple user accounts in your Office 365 tenant.</span></span>
  
<span data-ttu-id="e8700-105">Microsoft 365 관리 센터를 사용 하 여 Office 365 테 넌 트의 사용자 계정에 대 한 속성을 구성할 수 있지만 Office 365 PowerShell을 사용 하 고 관리 센터에서 수행할 수 없는 몇 가지 작업을 실행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8700-105">Although you can use the Microsoft 365 admin center to configure properties for the user accounts of your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the admin center cannot.</span></span>
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="e8700-106">Graph 모듈용 Azure Active Directory PowerShell 사용하기</span><span class="sxs-lookup"><span data-stu-id="e8700-106">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="e8700-107">Graph 모듈에 대 한 Azure Active Directory PowerShell을 사용 하 여 사용자 계정 속성을 구성 하려면 [AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet을 사용 하 고 설정 하거나 변경할 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8700-107">To configure properties for user accounts with the Azure Active Directory PowerShell for Graph module, you use the [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="e8700-108">먼저, [Office 365 테넌트에 연결](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)합니다.</span><span class="sxs-lookup"><span data-stu-id="e8700-108">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
   
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="e8700-109">특정 사용자 계정에 대 한 속성 변경</span><span class="sxs-lookup"><span data-stu-id="e8700-109">Change properties for a specific user account</span></span>

<span data-ttu-id="e8700-110">**-ObjectID** 매개 변수를 사용 하 여 계정을 식별 하 고 추가 매개 변수를 사용 하 여 특정 속성을 설정 하거나 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8700-110">You identify the account with the **-ObjectID** parameter and set or change specific properties with additional parameters.</span></span> <span data-ttu-id="e8700-111">가장 일반적인 매개 변수 목록은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e8700-111">Here's a list of the most common parameters.</span></span>
  
- <span data-ttu-id="e8700-112">-부서 "\<부서 이름>"</span><span class="sxs-lookup"><span data-stu-id="e8700-112">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="e8700-113">-DisplayName "\<전체 사용자 이름>"</span><span class="sxs-lookup"><span data-stu-id="e8700-113">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="e8700-114">-FacsimilieTelephoneNumber "\<팩스 번호>"</span><span class="sxs-lookup"><span data-stu-id="e8700-114">-FacsimilieTelephoneNumber "\<fax number>"</span></span>
    
- <span data-ttu-id="e8700-115">-GivenName "\<사용자 이름>"</span><span class="sxs-lookup"><span data-stu-id="e8700-115">-GivenName "\<user first name>"</span></span>
    
- <span data-ttu-id="e8700-116">-성 "\<사용자 성>"</span><span class="sxs-lookup"><span data-stu-id="e8700-116">-Surname "\<user last name>"</span></span>
    
- <span data-ttu-id="e8700-117">-Mobile "\<휴대폰 번호>"</span><span class="sxs-lookup"><span data-stu-id="e8700-117">-Mobile "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="e8700-118">-JobTitle "\<직책>"</span><span class="sxs-lookup"><span data-stu-id="e8700-118">-JobTitle "\<job title>"</span></span>
    
- <span data-ttu-id="e8700-119">-PreferredLanguage "\<language>"</span><span class="sxs-lookup"><span data-stu-id="e8700-119">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="e8700-120">-StreetAddress "\<주소>"</span><span class="sxs-lookup"><span data-stu-id="e8700-120">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="e8700-121">-도시명 "\<구/군/시 이름>"</span><span class="sxs-lookup"><span data-stu-id="e8700-121">-City "\<city name>"</span></span>
    
- <span data-ttu-id="e8700-122">-State "\<상태 이름>"</span><span class="sxs-lookup"><span data-stu-id="e8700-122">-State "\<state name>"</span></span>
    
- <span data-ttu-id="e8700-123">-PostalCode "\<우편 번호>"</span><span class="sxs-lookup"><span data-stu-id="e8700-123">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="e8700-124">-Country "\<국가 이름>"</span><span class="sxs-lookup"><span data-stu-id="e8700-124">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="e8700-125">-TelephoneNumber "\<사무실 전화 번호>"</span><span class="sxs-lookup"><span data-stu-id="e8700-125">-TelephoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="e8700-126">-UsageLocation "\<2 자리 국가 또는 지역 코드>"</span><span class="sxs-lookup"><span data-stu-id="e8700-126">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="e8700-127">ISO 3166-1 alpha-2 (A2) 두 자리 국가 또는 지역 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="e8700-127">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="e8700-128">추가 매개 변수에 대해서는 [AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) 을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="e8700-128">See [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) for additional parameters.</span></span>


<span data-ttu-id="e8700-129">사용자 계정의 사용자 계정 이름을 표시 하려면 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8700-129">To display the User Principal Name for your user accounts, run the following command.</span></span>
  
```powershell
Get-AzureADUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="e8700-130">이 명령은 Office 365 PowerShell에 다음과 같이 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8700-130">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="e8700-131">사용자 계정 ( **AzureADUser** )에 대 한 모든 정보를 가져오고 다음 명령 ( **|** )으로 전송 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8700-131">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="e8700-132">사용자 계정 이름 목록을 사전순 ( **sort-Object UserPrincipalName** )으로 정렬 하 고 다음 명령 ( **|** )으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="e8700-132">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="e8700-133">각 계정에 대 한 사용자 계정 이름 속성 ( **선택-개체 UserPrincipalName** )만 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8700-133">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
- <span data-ttu-id="e8700-134">한 **화면을 한** 번에 한 화면씩 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8700-134">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="e8700-135">이 명령에는 모든 계정이 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8700-135">This command will list all of your accounts.</span></span> <span data-ttu-id="e8700-136">표시 이름 (이름 및 성)을 기준으로 계정의 사용자 계정 이름을 표시 하려면 다음 명령을 실행 하 여 아래의 **$userName** 변수를 입력 합니다 ( \< 및 > 문자 제거).</span><span class="sxs-lookup"><span data-stu-id="e8700-136">If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```powershell
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="e8700-137">이 예에서는 Caleb 창턱의 표시 이름을 사용 하 여 사용자 계정에 대 한 사용자 보안 주체 이름을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8700-137">This example displays the User Principal Name for the user account with the display name of Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="e8700-138">**$Upn** 변수를 사용 하 여 개별 계정을 표시 이름에 따라 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8700-138">By using a **$upn** variable, you can make changes to individual accounts based on their display name.</span></span> <span data-ttu-id="e8700-139">다음은 Belinda Newman의 사용 위치를 프랑스로 설정 하 고 사용자 계정 이름이 아닌 표시 이름을 지정 하는 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="e8700-139">Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```powershell
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="e8700-140">모든 사용자 계정에 대 한 속성 변경</span><span class="sxs-lookup"><span data-stu-id="e8700-140">Change properties for all user accounts</span></span>

<span data-ttu-id="e8700-141">모든 사용자의 속성을 변경 하려면 **AzureADUser** 및 **AzureADUser** cmdlet을 조합 하 여 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8700-141">To change properties for all users, you can use the combination of the **Get-AzureADUser** and **Set-AzureADUser** cmdlets.</span></span> <span data-ttu-id="e8700-142">다음 예에서는 모든 사용자의 사용 위치를 프랑스로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="e8700-142">The following example changes the usage location for all users to France:</span></span>
  
```powershell
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="e8700-143">이 명령은 Office 365 PowerShell에 다음과 같이 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8700-143">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="e8700-144">사용자 계정 ( **AzureADUser** )에 대 한 모든 정보를 가져오고 다음 명령 ( **|** )으로 전송 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8700-144">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="e8700-145">사용자 위치를 프랑스 ( **AzureADUser-UsageLocation "FR"** )로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8700-145">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="e8700-146">특정 사용자 계정 집합의 속성 변경</span><span class="sxs-lookup"><span data-stu-id="e8700-146">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="e8700-147">특정 사용자 계정 집합의 속성을 변경 하려면 **AzureADUser**, **Where**및 **AzureADUser** cmdlet을 조합 하 여 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8700-147">To change properties for a specific set of user account, you can use the combination of the **Get-AzureADUser**, **Where**, and **Set-AzureADUser** cmdlets.</span></span> <span data-ttu-id="e8700-148">다음 예에서는 프랑스 회계 부서의 모든 사용자의 사용 위치를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="e8700-148">The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```powershell
Get-AzureADUser | Where-Object {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="e8700-149">이 명령은 Office 365 PowerShell에 다음과 같이 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8700-149">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="e8700-150">사용자 계정 ( **AzureADUser** )에 대 한 모든 정보를 가져오고 다음 명령 ( **|** )으로 전송 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8700-150">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="e8700-151">부서 속성이 "회계"로 설정 된 모든 사용자 계정을 찾습니다 ( **여기서 {$ _. 부서-eq "Accounting"}** )를 사용 하 고 결과 정보를 다음 명령 ( **|** )으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="e8700-151">Find all of the user accounts that have their Department property set to "Accounting" ( **Where {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="e8700-152">사용자 위치를 프랑스 ( **AzureADUser-UsageLocation "FR"** )로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8700-152">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="e8700-153">Windows PowerShell용 Microsoft Azure Active Directory 모듈 사용하기</span><span class="sxs-lookup"><span data-stu-id="e8700-153">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="e8700-154">Windows PowerShell 용 Microsoft Azure Active Directory 모듈을 사용 하 여 사용자 계정에 대 한 속성을 구성 하려면 Get-msoluser cmdlet을 사용 하 고 설정 하거나 변경할 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8700-154">To configure properties for user accounts with the Microsoft Azure Active Directory Module for Windows PowerShell, you use the Set-MsolUser cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="e8700-155">먼저, [Office 365 테넌트에 연결](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)합니다.</span><span class="sxs-lookup"><span data-stu-id="e8700-155">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
  
>[!Note]
><span data-ttu-id="e8700-156">PowerShell Core에서는 이름에 **Msol** 이 포함 된 Windows powershell 모듈 및 cmdlet에 대 한 Microsoft Azure Active Directory 모듈을 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e8700-156">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="e8700-157">이러한 cmdlet을 계속 사용 하려면 Windows PowerShell에서 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8700-157">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="e8700-158">특정 사용자 계정에 대 한 속성 변경</span><span class="sxs-lookup"><span data-stu-id="e8700-158">Change properties for a specific user account</span></span>

<span data-ttu-id="e8700-159">특정 사용자 계정에 대 한 속성을 구성 하려면 [get-msoluser](https://msdn.microsoft.com/library/azure/dn194136.aspx) cmdlet을 사용 하 고 설정 하거나 변경할 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8700-159">To configure properties for a specific user account, you use the [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="e8700-160">**-UserPrincipalName** 매개 변수를 사용 하 여 계정을 식별 하 고 추가 매개 변수를 사용 하 여 특정 속성을 설정 하거나 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8700-160">You identify the account with the **-UserPrincipalName** parameter and set or change specific properties with additional parameters.</span></span> <span data-ttu-id="e8700-161">가장 일반적인 매개 변수 목록은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e8700-161">Here is a list of the most common parameters.</span></span>
  
- <span data-ttu-id="e8700-162">-도시명 "\<구/군/시 이름>"</span><span class="sxs-lookup"><span data-stu-id="e8700-162">-City "\<city name>"</span></span>
    
- <span data-ttu-id="e8700-163">-Country "\<국가 이름>"</span><span class="sxs-lookup"><span data-stu-id="e8700-163">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="e8700-164">-부서 "\<부서 이름>"</span><span class="sxs-lookup"><span data-stu-id="e8700-164">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="e8700-165">-DisplayName "\<전체 사용자 이름>"</span><span class="sxs-lookup"><span data-stu-id="e8700-165">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="e8700-166">-Fax "\<팩스 번호>"</span><span class="sxs-lookup"><span data-stu-id="e8700-166">-Fax "\<fax number>"</span></span>
    
- <span data-ttu-id="e8700-167">-FirstName "\<사용자 이름>"</span><span class="sxs-lookup"><span data-stu-id="e8700-167">-FirstName "\<user first name>"</span></span>
    
- <span data-ttu-id="e8700-168">-LastName "\<user last name>"</span><span class="sxs-lookup"><span data-stu-id="e8700-168">-LastName "\<user last name>"</span></span>
    
- <span data-ttu-id="e8700-169">-MobilePhone "\<휴대폰 번호>"</span><span class="sxs-lookup"><span data-stu-id="e8700-169">-MobilePhone "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="e8700-170">-Office "\<사무실 위치>"</span><span class="sxs-lookup"><span data-stu-id="e8700-170">-Office "\<office location>"</span></span>
    
- <span data-ttu-id="e8700-171">-PhoneNumber "\<사무실 전화 번호>"</span><span class="sxs-lookup"><span data-stu-id="e8700-171">-PhoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="e8700-172">-PostalCode "\<우편 번호>"</span><span class="sxs-lookup"><span data-stu-id="e8700-172">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="e8700-173">-PreferredLanguage "\<language>"</span><span class="sxs-lookup"><span data-stu-id="e8700-173">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="e8700-174">-State "\<상태 이름>"</span><span class="sxs-lookup"><span data-stu-id="e8700-174">-State "\<state name>"</span></span>
    
- <span data-ttu-id="e8700-175">-StreetAddress "\<주소>"</span><span class="sxs-lookup"><span data-stu-id="e8700-175">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="e8700-176">-Title "\<제목 이름>"</span><span class="sxs-lookup"><span data-stu-id="e8700-176">-Title "\<title name>"</span></span>
    
- <span data-ttu-id="e8700-177">-UsageLocation "\<2 자리 국가 또는 지역 코드>"</span><span class="sxs-lookup"><span data-stu-id="e8700-177">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="e8700-178">ISO 3166-1 alpha-2 (A2) 두 자리 국가 또는 지역 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="e8700-178">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="e8700-179">추가 매개 변수에 대해서는 [get-msoluser](https://msdn.microsoft.com/library/azure/dn194136.aspx) 을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="e8700-179">See [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) for additional parameters.</span></span>

<span data-ttu-id="e8700-180">모든 사용자의 사용자 계정 이름을 보려면 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8700-180">To see the User Principal Names of all your users, run the following command.</span></span>
  
```powershell
Get-MSolUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="e8700-181">이 명령은 Office 365 PowerShell에 다음과 같이 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8700-181">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="e8700-182">사용자 계정 ( **get-msoluser** )에 대 한 모든 정보를 가져오고 다음 명령 ( **|** )으로 전송 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8700-182">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="e8700-183">사용자 계정 이름 목록을 사전순 ( **sort-Object UserPrincipalName** )으로 정렬 하 고 다음 명령 ( **|** )으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="e8700-183">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="e8700-184">각 계정에 대 한 사용자 계정 이름 속성 ( **선택-개체 UserPrincipalName** )만 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8700-184">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
    
- <span data-ttu-id="e8700-185">한 **화면을 한** 번에 한 화면씩 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8700-185">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="e8700-186">이 명령에는 모든 계정이 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8700-186">This command will list all of your accounts.</span></span> <span data-ttu-id="e8700-187">표시 이름 (이름 및 성)을 기준으로 계정의 사용자 계정 이름을 표시 하려면 다음 명령을 실행 하 여 아래의 **$userName** 변수를 입력 합니다 ( \< 및 > 문자 제거).</span><span class="sxs-lookup"><span data-stu-id="e8700-187">If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```powershell
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="e8700-188">이 예제에서는 Caleb 창턱 라는 사용자에 대 한 사용자 계정 이름을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8700-188">This example displays the User Principal Name for the user named Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="e8700-189">**$Upn** 변수를 사용 하 여 개별 계정을 표시 이름에 따라 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8700-189">By using a **$upn** variable, you can make changes to individual accounts based on their display name.</span></span> <span data-ttu-id="e8700-190">다음은 Belinda Newman의 사용 위치를 프랑스로 설정 하 고 사용자 계정 이름이 아닌 표시 이름을 지정 하는 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="e8700-190">Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```powershell
$userName="<display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="e8700-191">모든 사용자 계정에 대 한 속성 변경</span><span class="sxs-lookup"><span data-stu-id="e8700-191">Change properties for all user accounts</span></span>

<span data-ttu-id="e8700-p110">모든 사용자에 대한 속성을 변경하려면 **Get-msoluser** 및 **Set-msoluser** cmdlet의 조합을 사용합니다. 다음 예에서는 모든 사용자의 사용 위치를 프랑스로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="e8700-p110">To change properties for all users, you can use the combination of the **Get-MsolUser** and **Set-MsolUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```powershell
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="e8700-194">이 명령은 Office 365 PowerShell에 다음과 같이 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8700-194">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="e8700-195">사용자 계정 ( **get-msoluser** )에 대 한 모든 정보를 가져오고 다음 명령 ( **|** )으로 전송 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8700-195">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="e8700-196">사용자 위치를 프랑스 ( **get-msoluser-UsageLocation "FR"** )로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8700-196">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="e8700-197">특정 사용자 계정 집합의 속성 변경</span><span class="sxs-lookup"><span data-stu-id="e8700-197">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="e8700-198">특정 사용자 계정 집합의 속성을 변경 하려면 **get-msoluser**, **Where 개체**및 **get-msoluser** cmdlet을 함께 사용 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8700-198">To change properties for a specific set of user account, you can use the combination of the **Get-MsolUser**, **Where-Object**, and **Set-MsolUser** cmdlets.</span></span> <span data-ttu-id="e8700-199">다음 예에서는 프랑스 회계 부서의 모든 사용자의 사용 위치를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="e8700-199">The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```powershell
Get-MsolUser | Where-Object {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="e8700-200">이 명령은 Office 365 PowerShell에 다음과 같이 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8700-200">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="e8700-201">사용자 계정 ( **get-msoluser** )에 대 한 모든 정보를 가져오고 다음 명령 ( **|** )으로 전송 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8700-201">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="e8700-202">부서 속성이 "회계"로 설정 된 모든 사용자 계정을 찾습니다 ( **여기서-개체 {$ _. 부서-eq "Accounting"}** )를 사용 하 고 결과 정보를 다음 명령 ( **|** )으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="e8700-202">Find all of the user accounts that have their Department property set to "Accounting" ( **Where-Object {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="e8700-203">사용자 위치를 프랑스 ( **get-msoluser-UsageLocation "FR"** )로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8700-203">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    

## <a name="see-also"></a><span data-ttu-id="e8700-204">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e8700-204">See also</span></span>

[<span data-ttu-id="e8700-205">Office 365 PowerShell로 사용자 계정 및 라이선스 관리</span><span class="sxs-lookup"><span data-stu-id="e8700-205">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="e8700-206">Office 365 PowerShell 사용한 Office 365 관리</span><span class="sxs-lookup"><span data-stu-id="e8700-206">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="e8700-207">Office 365 PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="e8700-207">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
