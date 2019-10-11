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
ms.openlocfilehash: 40d7e78b3fd6c011f6c53b2af433f258b888d5bb
ms.sourcegitcommit: ecfa362182f906befa885bf5f0094528ff570779
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/09/2019
ms.locfileid: "37435352"
---
# <a name="configure-user-account-properties-with-office-365-powershell"></a><span data-ttu-id="36068-103">Office 365 PowerShell를 사용 하 여 사용자 계정 속성 구성</span><span class="sxs-lookup"><span data-stu-id="36068-103">Configure user account properties with Office 365 PowerShell</span></span>

 <span data-ttu-id="36068-104">**요약:** Office 365 PowerShell을 사용 하 여 Office 365 테 넌 트에서 개별 또는 여러 사용자 계정에 대 한 속성을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="36068-104">**Summary:** Use Office 365 PowerShell to configure properties of individual or multiple user accounts in your Office 365 tenant.</span></span>
  
<span data-ttu-id="36068-105">Microsoft 365 관리 센터를 사용 하 여 Office 365 테 넌 트의 사용자 계정에 대 한 속성을 구성할 수 있지만 Office 365 PowerShell을 사용 하 고 관리 센터에서 수행할 수 없는 몇 가지 작업을 실행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36068-105">Although you can use the Microsoft 365 admin center to configure properties for the user accounts of your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the admin center cannot.</span></span>
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="36068-106">Graph 모듈용 Azure Active Directory PowerShell 사용하기</span><span class="sxs-lookup"><span data-stu-id="36068-106">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="36068-107">Graph 모듈에 대 한 Azure Active Directory PowerShell을 사용 하 여 사용자 계정 속성을 구성 하려면 [AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet을 사용 하 고 설정 하거나 변경할 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36068-107">To configure properties for user accounts with the Azure Active Directory PowerShell for Graph module, you use the [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="36068-108">먼저, [Office 365 테넌트에 연결](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)합니다.</span><span class="sxs-lookup"><span data-stu-id="36068-108">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
   
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="36068-109">특정 사용자 계정에 대 한 속성 변경</span><span class="sxs-lookup"><span data-stu-id="36068-109">Change properties for a specific user account</span></span>

<span data-ttu-id="36068-110">**-ObjectID** 매개 변수를 사용 하 여 계정을 식별 하 고 추가 매개 변수를 사용 하 여 특정 속성을 설정 하거나 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="36068-110">You identify the account with the **-ObjectID** parameter and set or change specific properties with additional parameters.</span></span> <span data-ttu-id="36068-111">가장 일반적인 매개 변수 목록은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="36068-111">Here's a list of the most common parameters.</span></span>
  
- <span data-ttu-id="36068-112">-부서 "\<부서 이름>"</span><span class="sxs-lookup"><span data-stu-id="36068-112">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="36068-113">-DisplayName "\<전체 사용자 이름>"</span><span class="sxs-lookup"><span data-stu-id="36068-113">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="36068-114">-FacsimilieTelephoneNumber "\<팩스 번호>"</span><span class="sxs-lookup"><span data-stu-id="36068-114">-FacsimilieTelephoneNumber "\<fax number>"</span></span>
    
- <span data-ttu-id="36068-115">-GivenName "\<사용자 이름>"</span><span class="sxs-lookup"><span data-stu-id="36068-115">-GivenName "\<user first name>"</span></span>
    
- <span data-ttu-id="36068-116">-성 "\<사용자 성>"</span><span class="sxs-lookup"><span data-stu-id="36068-116">-Surname "\<user last name>"</span></span>
    
- <span data-ttu-id="36068-117">-Mobile "\<휴대폰 번호>"</span><span class="sxs-lookup"><span data-stu-id="36068-117">-Mobile "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="36068-118">-JobTitle "\<직책>"</span><span class="sxs-lookup"><span data-stu-id="36068-118">-JobTitle "\<job title>"</span></span>
    
- <span data-ttu-id="36068-119">-PreferredLanguage "\<language>"</span><span class="sxs-lookup"><span data-stu-id="36068-119">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="36068-120">-StreetAddress "\<주소>"</span><span class="sxs-lookup"><span data-stu-id="36068-120">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="36068-121">-도시명 "\<구/군/시 이름>"</span><span class="sxs-lookup"><span data-stu-id="36068-121">-City "\<city name>"</span></span>
    
- <span data-ttu-id="36068-122">-State "\<상태 이름>"</span><span class="sxs-lookup"><span data-stu-id="36068-122">-State "\<state name>"</span></span>
    
- <span data-ttu-id="36068-123">-PostalCode "\<우편 번호>"</span><span class="sxs-lookup"><span data-stu-id="36068-123">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="36068-124">-Country "\<국가 이름>"</span><span class="sxs-lookup"><span data-stu-id="36068-124">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="36068-125">-TelephoneNumber "\<사무실 전화 번호>"</span><span class="sxs-lookup"><span data-stu-id="36068-125">-TelephoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="36068-126">-UsageLocation "\<2 자리 국가 또는 지역 코드>"</span><span class="sxs-lookup"><span data-stu-id="36068-126">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="36068-127">ISO 3166-1 alpha-2 (A2) 두 자리 국가 또는 지역 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="36068-127">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="36068-128">추가 매개 변수에 대해서는 [AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) 을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="36068-128">See [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) for additional parameters.</span></span>


<span data-ttu-id="36068-129">사용자 계정의 사용자 계정 이름을 표시 하려면 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="36068-129">To display the User Principal Name for your user accounts, run the following command.</span></span>
  
```
Get-AzureADUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="36068-130">이 명령은 Office 365 PowerShell에 다음과 같이 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="36068-130">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="36068-131">사용자 계정 ( **AzureADUser** )에 대 한 모든 정보를 가져오고 다음 명령 ( **|** )으로 전송 합니다.</span><span class="sxs-lookup"><span data-stu-id="36068-131">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="36068-132">사용자 계정 이름 목록을 사전순 ( **sort-Object UserPrincipalName** )으로 정렬 하 고 다음 명령 ( **|** )으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="36068-132">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="36068-133">각 계정에 대 한 사용자 계정 이름 속성 ( **선택-개체 UserPrincipalName** )만 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="36068-133">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
- <span data-ttu-id="36068-134">한 **화면을 한** 번에 한 화면씩 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="36068-134">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="36068-135">이 명령에는 모든 계정이 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="36068-135">This command will list all of your accounts.</span></span> <span data-ttu-id="36068-136">표시 이름 (이름 및 성)을 기준으로 계정의 사용자 계정 이름을 표시 하려면 다음 명령을 실행 하 여 아래의 **$userName** 변수를 입력 합니다 ( \< 및 > 문자 제거).</span><span class="sxs-lookup"><span data-stu-id="36068-136">If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="36068-137">이 예에서는 Caleb 창턱의 표시 이름을 사용 하 여 사용자 계정에 대 한 사용자 보안 주체 이름을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="36068-137">This example displays the User Principal Name for the user account with the display name of Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="36068-138">**$Upn** 변수를 사용 하 여 개별 계정을 표시 이름에 따라 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36068-138">By using a **$upn** variable, you can make changes to individual accounts based on their display name.</span></span> <span data-ttu-id="36068-139">다음은 Belinda Newman의 사용 위치를 프랑스로 설정 하 고 사용자 계정 이름이 아닌 표시 이름을 지정 하는 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="36068-139">Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="36068-140">모든 사용자 계정에 대 한 속성 변경</span><span class="sxs-lookup"><span data-stu-id="36068-140">Change properties for all user accounts</span></span>

<span data-ttu-id="36068-141">모든 사용자의 속성을 변경 하려면 **AzureADUser** 및 **AzureADUser** cmdlet을 조합 하 여 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36068-141">To change properties for all users, you can use the combination of the **Get-AzureADUser** and **Set-AzureADUser** cmdlets.</span></span> <span data-ttu-id="36068-142">다음 예에서는 모든 사용자의 사용 위치를 프랑스로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="36068-142">The following example changes the usage location for all users to France:</span></span>
  
```
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="36068-143">이 명령은 Office 365 PowerShell에 다음과 같이 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="36068-143">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="36068-144">사용자 계정 ( **AzureADUser** )에 대 한 모든 정보를 가져오고 다음 명령 ( **|** )으로 전송 합니다.</span><span class="sxs-lookup"><span data-stu-id="36068-144">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="36068-145">사용자 위치를 프랑스 ( **AzureADUser-UsageLocation "FR"** )로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36068-145">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="36068-146">특정 사용자 계정 집합의 속성 변경</span><span class="sxs-lookup"><span data-stu-id="36068-146">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="36068-147">특정 사용자 계정 집합의 속성을 변경 하려면 **AzureADUser**, **Where**및 **AzureADUser** cmdlet을 조합 하 여 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36068-147">To change properties for a specific set of user account, you can use the combination of the **Get-AzureADUser**, **Where**, and **Set-AzureADUser** cmdlets.</span></span> <span data-ttu-id="36068-148">다음 예에서는 프랑스 회계 부서의 모든 사용자의 사용 위치를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="36068-148">The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="36068-149">이 명령은 Office 365 PowerShell에 다음과 같이 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="36068-149">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="36068-150">사용자 계정 ( **AzureADUser** )에 대 한 모든 정보를 가져오고 다음 명령 ( **|** )으로 전송 합니다.</span><span class="sxs-lookup"><span data-stu-id="36068-150">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="36068-151">부서 속성이 "회계"로 설정 된 모든 사용자 계정을 찾습니다 ( **여기서 {$ _. 부서-eq "Accounting"}** )를 사용 하 고 결과 정보를 다음 명령 ( **|** )으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="36068-151">Find all of the user accounts that have their Department property set to "Accounting" ( **Where {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="36068-152">사용자 위치를 프랑스 ( **AzureADUser-UsageLocation "FR"** )로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36068-152">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="36068-153">Windows PowerShell용 Microsoft Azure Active Directory 모듈 사용하기</span><span class="sxs-lookup"><span data-stu-id="36068-153">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="36068-154">Windows PowerShell 용 Microsoft Azure Active Directory 모듈을 사용 하 여 사용자 계정에 대 한 속성을 구성 하려면 Get-msoluser cmdlet을 사용 하 고 설정 하거나 변경할 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36068-154">To configure properties for user accounts with the Microsoft Azure Active Directory Module for Windows PowerShell, you use the Set-MsolUser cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="36068-155">먼저, [Office 365 테넌트에 연결](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)합니다.</span><span class="sxs-lookup"><span data-stu-id="36068-155">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
  
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="36068-156">특정 사용자 계정에 대 한 속성 변경</span><span class="sxs-lookup"><span data-stu-id="36068-156">Change properties for a specific user account</span></span>

<span data-ttu-id="36068-157">특정 사용자 계정에 대 한 속성을 구성 하려면 [get-msoluser](https://msdn.microsoft.com/library/azure/dn194136.aspx) cmdlet을 사용 하 고 설정 하거나 변경할 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36068-157">To configure properties for a specific user account, you use the [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="36068-158">**-UserPrincipalName** 매개 변수를 사용 하 여 계정을 식별 하 고 추가 매개 변수를 사용 하 여 특정 속성을 설정 하거나 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="36068-158">You identify the account with the **-UserPrincipalName** parameter and set or change specific properties with additional parameters.</span></span> <span data-ttu-id="36068-159">가장 일반적인 매개 변수 목록은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="36068-159">Here is a list of the most common parameters.</span></span>
  
- <span data-ttu-id="36068-160">-도시명 "\<구/군/시 이름>"</span><span class="sxs-lookup"><span data-stu-id="36068-160">-City "\<city name>"</span></span>
    
- <span data-ttu-id="36068-161">-Country "\<국가 이름>"</span><span class="sxs-lookup"><span data-stu-id="36068-161">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="36068-162">-부서 "\<부서 이름>"</span><span class="sxs-lookup"><span data-stu-id="36068-162">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="36068-163">-DisplayName "\<전체 사용자 이름>"</span><span class="sxs-lookup"><span data-stu-id="36068-163">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="36068-164">-Fax "\<팩스 번호>"</span><span class="sxs-lookup"><span data-stu-id="36068-164">-Fax "\<fax number>"</span></span>
    
- <span data-ttu-id="36068-165">-FirstName "\<사용자 이름>"</span><span class="sxs-lookup"><span data-stu-id="36068-165">-FirstName "\<user first name>"</span></span>
    
- <span data-ttu-id="36068-166">-LastName "\<user last name>"</span><span class="sxs-lookup"><span data-stu-id="36068-166">-LastName "\<user last name>"</span></span>
    
- <span data-ttu-id="36068-167">-MobilePhone "\<휴대폰 번호>"</span><span class="sxs-lookup"><span data-stu-id="36068-167">-MobilePhone "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="36068-168">-Office "\<사무실 위치>"</span><span class="sxs-lookup"><span data-stu-id="36068-168">-Office "\<office location>"</span></span>
    
- <span data-ttu-id="36068-169">-PhoneNumber "\<사무실 전화 번호>"</span><span class="sxs-lookup"><span data-stu-id="36068-169">-PhoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="36068-170">-PostalCode "\<우편 번호>"</span><span class="sxs-lookup"><span data-stu-id="36068-170">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="36068-171">-PreferredLanguage "\<language>"</span><span class="sxs-lookup"><span data-stu-id="36068-171">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="36068-172">-State "\<상태 이름>"</span><span class="sxs-lookup"><span data-stu-id="36068-172">-State "\<state name>"</span></span>
    
- <span data-ttu-id="36068-173">-StreetAddress "\<주소>"</span><span class="sxs-lookup"><span data-stu-id="36068-173">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="36068-174">-Title "\<제목 이름>"</span><span class="sxs-lookup"><span data-stu-id="36068-174">-Title "\<title name>"</span></span>
    
- <span data-ttu-id="36068-175">-UsageLocation "\<2 자리 국가 또는 지역 코드>"</span><span class="sxs-lookup"><span data-stu-id="36068-175">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="36068-176">ISO 3166-1 alpha-2 (A2) 두 자리 국가 또는 지역 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="36068-176">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="36068-177">추가 매개 변수에 대해서는 [get-msoluser](https://msdn.microsoft.com/library/azure/dn194136.aspx) 을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="36068-177">See [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) for additional parameters.</span></span>

<span data-ttu-id="36068-178">모든 사용자의 사용자 계정 이름을 보려면 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="36068-178">To see the User Principal Names of all your users, run the following command.</span></span>
  
```
Get-MSolUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="36068-179">이 명령은 Office 365 PowerShell에 다음과 같이 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="36068-179">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="36068-180">사용자 계정 ( **get-msoluser** )에 대 한 모든 정보를 가져오고 다음 명령 ( **|** )으로 전송 합니다.</span><span class="sxs-lookup"><span data-stu-id="36068-180">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="36068-181">사용자 계정 이름 목록을 사전순 ( **sort-Object UserPrincipalName** )으로 정렬 하 고 다음 명령 ( **|** )으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="36068-181">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="36068-182">각 계정에 대 한 사용자 계정 이름 속성 ( **선택-개체 UserPrincipalName** )만 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="36068-182">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
    
- <span data-ttu-id="36068-183">한 **화면을 한** 번에 한 화면씩 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="36068-183">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="36068-184">이 명령에는 모든 계정이 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="36068-184">This command will list all of your accounts.</span></span> <span data-ttu-id="36068-185">표시 이름 (이름 및 성)을 기준으로 계정의 사용자 계정 이름을 표시 하려면 다음 명령을 실행 하 여 아래의 **$userName** 변수를 입력 합니다 ( \< 및 > 문자 제거).</span><span class="sxs-lookup"><span data-stu-id="36068-185">If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="36068-186">이 예제에서는 Caleb 창턱 라는 사용자에 대 한 사용자 계정 이름을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="36068-186">This example displays the User Principal Name for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="36068-187">**$Upn** 변수를 사용 하 여 개별 계정을 표시 이름에 따라 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36068-187">By using a **$upn** variable, you can make changes to individual accounts based on their display name.</span></span> <span data-ttu-id="36068-188">다음은 Belinda Newman의 사용 위치를 프랑스로 설정 하 고 사용자 계정 이름이 아닌 표시 이름을 지정 하는 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="36068-188">Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```
$userName="<display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="36068-189">모든 사용자 계정에 대 한 속성 변경</span><span class="sxs-lookup"><span data-stu-id="36068-189">Change properties for all user accounts</span></span>

<span data-ttu-id="36068-p109">모든 사용자에 대한 속성을 변경하려면 **Get-msoluser** 및 **Set-msoluser** cmdlet의 조합을 사용합니다. 다음 예에서는 모든 사용자의 사용 위치를 프랑스로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="36068-p109">To change properties for all users, you can use the combination of the **Get-MsolUser** and **Set-MsolUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="36068-192">이 명령은 Office 365 PowerShell에 다음과 같이 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="36068-192">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="36068-193">사용자 계정 ( **get-msoluser** )에 대 한 모든 정보를 가져오고 다음 명령 ( **|** )으로 전송 합니다.</span><span class="sxs-lookup"><span data-stu-id="36068-193">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="36068-194">사용자 위치를 프랑스 ( **get-msoluser-UsageLocation "FR"** )로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36068-194">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="36068-195">특정 사용자 계정 집합의 속성 변경</span><span class="sxs-lookup"><span data-stu-id="36068-195">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="36068-196">특정 사용자 계정 집합의 속성을 변경 하려면 **get-msoluser**, **Where 개체**및 **get-msoluser** cmdlet을 함께 사용 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="36068-196">To change properties for a specific set of user account, you can use the combination of the **Get-MsolUser**, **Where-Object**, and **Set-MsolUser** cmdlets.</span></span> <span data-ttu-id="36068-197">다음 예에서는 프랑스 회계 부서의 모든 사용자의 사용 위치를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="36068-197">The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```
Get-MsolUser | Where-Object {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="36068-198">이 명령은 Office 365 PowerShell에 다음과 같이 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="36068-198">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="36068-199">사용자 계정 ( **get-msoluser** )에 대 한 모든 정보를 가져오고 다음 명령 ( **|** )으로 전송 합니다.</span><span class="sxs-lookup"><span data-stu-id="36068-199">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="36068-200">부서 속성이 "회계"로 설정 된 모든 사용자 계정을 찾습니다 ( **여기서-개체 {$ _. 부서-eq "Accounting"}** )를 사용 하 고 결과 정보를 다음 명령 ( **|** )으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="36068-200">Find all of the user accounts that have their Department property set to "Accounting" ( **Where-Object {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="36068-201">사용자 위치를 프랑스 ( **get-msoluser-UsageLocation "FR"** )로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36068-201">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    

## <a name="see-also"></a><span data-ttu-id="36068-202">참고 항목</span><span class="sxs-lookup"><span data-stu-id="36068-202">See also</span></span>

[<span data-ttu-id="36068-203">Office 365 PowerShell로 사용자 계정 및 라이선스 관리</span><span class="sxs-lookup"><span data-stu-id="36068-203">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="36068-204">Office 365 PowerShell 사용한 Office 365 관리</span><span class="sxs-lookup"><span data-stu-id="36068-204">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="36068-205">Office 365 PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="36068-205">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
