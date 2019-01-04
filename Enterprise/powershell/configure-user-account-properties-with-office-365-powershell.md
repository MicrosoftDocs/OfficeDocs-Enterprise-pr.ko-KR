---
title: Office 365 PowerShell을 사용하여 사용자 계정 속성 구성
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: '요약: Office 365 테 넌 트에 개인 또는 여러 사용자 계정 속성을 구성 하려면 Office 365 PowerShell를 사용 합니다.'
ms.openlocfilehash: 4db63482fdcc1d6cb186e663fd55c13186b33813
ms.sourcegitcommit: 15db0f1e5f8036e46063662d7df22387906f8ba7
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/04/2019
ms.locfileid: "27546489"
---
# <a name="configure-user-account-properties-with-office-365-powershell"></a><span data-ttu-id="5e07e-103">Office 365 PowerShell을 사용하여 사용자 계정 속성 구성</span><span class="sxs-lookup"><span data-stu-id="5e07e-103">Configure user account properties with Office 365 PowerShell</span></span>

 <span data-ttu-id="5e07e-104">**요약:** Office 365 PowerShell을 사용 하 여 Office 365 테 넌 트의 개인 또는 여러 사용자 계정 속성 구성.</span><span class="sxs-lookup"><span data-stu-id="5e07e-104">**Summary:** Use Office 365 PowerShell to configure properties of individual or multiple user accounts in your Office 365 tenant.</span></span>
  
<span data-ttu-id="5e07e-105">Office 365 관리 센터를 사용 하 여 Office 365 테 넌 트의 사용자 계정에 대 한 속성을 구성할 수 있지만 Office 365 PowerShell을 사용 하 여 수 및 Office 365 관리 센터 수 없는 일부 작업을 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e07e-105">Although you can use the Office 365 Admin center to configure properties for the user accounts of your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the Office 365 Admin center cannot.</span></span>
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="5e07e-106">Azure Active Directory PowerShell을 사용 하 여 그래프 모듈에 대 한</span><span class="sxs-lookup"><span data-stu-id="5e07e-106">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="5e07e-107">Azure Active Directory powershell 그래프 모듈에 대 한 사용자 계정에 대 한 속성을 구성 하려면 [집합 AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet을 사용 하 고 속성을 설정 하거나 변경를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e07e-107">To configure properties for user accounts with the Azure Active Directory PowerShell for Graph module, you use the [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="5e07e-108">첫째, [Office 365 테 넌 트에 연결](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)합니다.</span><span class="sxs-lookup"><span data-stu-id="5e07e-108">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
   
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="5e07e-109">특정 사용자 계정에 대 한 속성을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e07e-109">Change properties for a specific user account</span></span>

<span data-ttu-id="5e07e-p101">하면 **-ObjectID** 매개 변수와 함께 계정을 식별 하 고 설정 또는 추가 매개 변수를 사용 하 여 특정 속성을 변경 합니다. 가장 일반적인 매개 변수 목록은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="5e07e-p101">You identify the account with the **-ObjectID** parameter and set or change specific properties with additional parameters. Here's a list of the most common parameters.</span></span>
  
- <span data-ttu-id="5e07e-112">-부서 "\<부서 이름 >"</span><span class="sxs-lookup"><span data-stu-id="5e07e-112">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="5e07e-113">-DisplayName "\<완전 한 사용자 이름 >"</span><span class="sxs-lookup"><span data-stu-id="5e07e-113">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="5e07e-114">-FacsimilieTelephoneNumber "\<팩스 번호 >"</span><span class="sxs-lookup"><span data-stu-id="5e07e-114">-FacsimilieTelephoneNumber "\<fax number>"</span></span>
    
- <span data-ttu-id="5e07e-115">-GivenName "\<사용자 이름 >"</span><span class="sxs-lookup"><span data-stu-id="5e07e-115">-GivenName "\<user first name>"</span></span>
    
- <span data-ttu-id="5e07e-116">-성 "\<사용자 마지막 이름 >"</span><span class="sxs-lookup"><span data-stu-id="5e07e-116">-Surname "\<user last name>"</span></span>
    
- <span data-ttu-id="5e07e-117">-모바일 "\<휴대폰 번호 >"</span><span class="sxs-lookup"><span data-stu-id="5e07e-117">-Mobile "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="5e07e-118">-JobTitle "\<직함 >"</span><span class="sxs-lookup"><span data-stu-id="5e07e-118">-JobTitle "\<job title>"</span></span>
    
- <span data-ttu-id="5e07e-119">-PreferredLanguage "\<언어 >"</span><span class="sxs-lookup"><span data-stu-id="5e07e-119">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="5e07e-120">-StreetAddress "\<주소 >"</span><span class="sxs-lookup"><span data-stu-id="5e07e-120">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="5e07e-121">-도시 "\<도시 이름 >"</span><span class="sxs-lookup"><span data-stu-id="5e07e-121">-City "\<city name>"</span></span>
    
- <span data-ttu-id="5e07e-122">-상태 "\<상태 이름 >"</span><span class="sxs-lookup"><span data-stu-id="5e07e-122">-State "\<state name>"</span></span>
    
- <span data-ttu-id="5e07e-123">-PostalCode "\<우편번호 >"</span><span class="sxs-lookup"><span data-stu-id="5e07e-123">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="5e07e-124">-국가 "\<국가 이름 >"</span><span class="sxs-lookup"><span data-stu-id="5e07e-124">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="5e07e-125">-TelephoneNumber "\<사무실 전화번호 >"</span><span class="sxs-lookup"><span data-stu-id="5e07e-125">-TelephoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="5e07e-126">-Usagelocation이 "\<2 자리 국가 또는 지역 코드 >"</span><span class="sxs-lookup"><span data-stu-id="5e07e-126">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="5e07e-127">ISO 3166-1 alpha-2 (A2) 두 문자로 된 국가 또는 지역 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="5e07e-127">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="5e07e-128">추가 매개 변수 [집합 AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) 을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="5e07e-128">See [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) for additional parameters.</span></span>
  
<span data-ttu-id="5e07e-129">사용자 계정에 대 한 사용자 계정 이름을 표시 하려면 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e07e-129">To display the User Principal Name for your user accounts, run the following command.</span></span>
  
```
Get-AzureADUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="5e07e-130">이 명령은 지시 하는 Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="5e07e-130">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="5e07e-131">사용자 계정 ( **Get AzureADUser** )에 대 한 정보를 모두 가져오고에 다음 명령을 보낼 ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="5e07e-131">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="5e07e-132">사용자 계정 이름 목록을 사전순으로 정렬 ( **Sort 개체 UserPrincipalName** )에 다음 명령을 보냅니다 ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="5e07e-132">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="5e07e-133">각 계정 ( **Select-object UserPrincipalName** )에 대 한 사용자 계정 이름 속성만을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e07e-133">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
- <span data-ttu-id="5e07e-134">하 한 화면에 표시 ( **더 많은** ) 한번 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e07e-134">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="5e07e-p102">이 명령은 계정을 모두 나열 합니다. 기반으로 표시 하는 계정에 대 한 사용자 계정 이름 표시 하려는 경우 (이름 및 성) 이름, 아래 **$userName** 변수를 입력 (제거는 \< 및 > 문자), 그런 후 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e07e-p102">This command will list all of your accounts. If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="5e07e-137">Caleb Sills의 표시 이름 가진 사용자 계정에 대 한 사용자 계정 이름을 표시 하는이 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="5e07e-137">This example displays the User Principal Name for the user account with the display name of Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="5e07e-p103">**$Upn** 변수를 사용 하 여 표시 이름에 따라 개별 계정에 변경할 수 있습니다. 다음은 프랑스, Belinda Newman의 사용 현황 위치를 설정 하지만 그녀의 사용자 계정 이름 대신 그녀의 표시 이름을 지정 하는 예제가입니다.</span><span class="sxs-lookup"><span data-stu-id="5e07e-p103">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="5e07e-140">모든 사용자 계정에 대 한 속성을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e07e-140">Change properties for all user accounts</span></span>

<span data-ttu-id="5e07e-p104">모든 사용자에 대 한 속성을 변경 하려면 **Get AzureADUser** 및 **집합 AzureADUser** cmdlet의 조합을 사용할 수 있습니다. 프랑스에 모든 사용자에 대 한 사용 현황 위치를 변경 하는 다음 예제에서는:</span><span class="sxs-lookup"><span data-stu-id="5e07e-p104">To change properties for all users, you can use the combination of the **Get-AzureADUser** and **Set-AzureADUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="5e07e-143">이 명령은 지시 하는 Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="5e07e-143">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="5e07e-144">사용자 계정 ( **Get AzureADUser** )에 대 한 정보를 모두 가져오고에 다음 명령을 보낼 ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="5e07e-144">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="5e07e-145">프랑스 ( **집합 AzureADUser-usagelocation이 "FR"** )로 사용자 위치를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e07e-145">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="5e07e-146">사용자 계정의 특정 집합에 대 한 속성을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e07e-146">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="5e07e-p105">사용자 계정의 특정 집합에 대 한 속성을 변경 하려면 **Get AzureADUser**, **위치**및 **집합 AzureADUser** cmdlet의 조합을 사용할 수 있습니다. 프랑스 회계 부서의 모든 사용자에 대 한 사용 현황 위치를 변경 하는 다음 예제에서는:</span><span class="sxs-lookup"><span data-stu-id="5e07e-p105">To change properties for a specific set of user account, you can use the combination of the **Get-AzureADUser**, **Where**, and **Set-AzureADUser** cmdlets. The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="5e07e-149">이 명령은 지시 하는 Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="5e07e-149">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="5e07e-150">사용자 계정 ( **Get AzureADUser** )에 대 한 정보를 모두 가져오고에 다음 명령을 보낼 ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="5e07e-150">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="5e07e-151">해당 부서 속성이 "Accounting"로 설정 하는 사용자 계정을 모두 찾기 ( **여기에서 {$_ 합니다. 부서-eq "Accounting"}** )에 다음 명령을 결과 정보를 보내고 ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="5e07e-151">Find all of the user accounts that have their Department property set to "Accounting" ( **Where {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="5e07e-152">프랑스 ( **집합 AzureADUser-usagelocation이 "FR"** )로 사용자 위치를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e07e-152">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="5e07e-153">Windows PowerShell 용 Microsoft Azure Active Directory 모듈을 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="5e07e-153">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="5e07e-154">Azure Active Directory 모듈에 대 한 Windows PowerShell Microsoft와 사용자 계정에 대 한 속성을 구성 하려면 이와 cmdlet을 사용 하 고 속성을 설정 하거나 변경를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e07e-154">To configure properties for user accounts with the Microsoft Azure Active Directory Module for Windows PowerShell, you use the Set-MsolUser cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="5e07e-155">첫째, [Office 365 테 넌 트에 연결](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)합니다.</span><span class="sxs-lookup"><span data-stu-id="5e07e-155">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
  
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="5e07e-156">특정 사용자 계정에 대 한 속성을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e07e-156">Change properties for a specific user account</span></span>

<span data-ttu-id="5e07e-157">특정 사용자 계정에 대 한 속성을 구성 하려면 [이와](https://msdn.microsoft.com/library/azure/dn194136.aspx) cmdlet을 사용 하 고 속성을 설정 하거나 변경를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e07e-157">To configure properties for a specific user account, you use the [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="5e07e-p106">하면 **-UserPrincipalName** 매개 변수와 함께 계정을 식별 하 고 설정 또는 추가 매개 변수를 사용 하 여 특정 속성을 변경 합니다. 가장 일반적인 매개 변수 목록은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="5e07e-p106">You identify the account with the **-UserPrincipalName** parameter and set or change specific properties with additional parameters. Here is a list of the most common parameters.</span></span>
  
- <span data-ttu-id="5e07e-160">-도시 "\<도시 이름 >"</span><span class="sxs-lookup"><span data-stu-id="5e07e-160">-City "\<city name>"</span></span>
    
- <span data-ttu-id="5e07e-161">-국가 "\<국가 이름 >"</span><span class="sxs-lookup"><span data-stu-id="5e07e-161">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="5e07e-162">-부서 "\<부서 이름 >"</span><span class="sxs-lookup"><span data-stu-id="5e07e-162">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="5e07e-163">-DisplayName "\<완전 한 사용자 이름 >"</span><span class="sxs-lookup"><span data-stu-id="5e07e-163">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="5e07e-164">-팩스 "\<팩스 번호 >"</span><span class="sxs-lookup"><span data-stu-id="5e07e-164">-Fax "\<fax number>"</span></span>
    
- <span data-ttu-id="5e07e-165">-FirstName "\<사용자 이름 >"</span><span class="sxs-lookup"><span data-stu-id="5e07e-165">-FirstName "\<user first name>"</span></span>
    
- <span data-ttu-id="5e07e-166">-LastName "\<사용자 마지막 이름 >"</span><span class="sxs-lookup"><span data-stu-id="5e07e-166">-LastName "\<user last name>"</span></span>
    
- <span data-ttu-id="5e07e-167">-MobilePhone "\<휴대폰 번호 >"</span><span class="sxs-lookup"><span data-stu-id="5e07e-167">-MobilePhone "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="5e07e-168">-Office "\<사무실 위치 >"</span><span class="sxs-lookup"><span data-stu-id="5e07e-168">-Office "\<office location>"</span></span>
    
- <span data-ttu-id="5e07e-169">-PhoneNumber "\<사무실 전화번호 >"</span><span class="sxs-lookup"><span data-stu-id="5e07e-169">-PhoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="5e07e-170">-PostalCode "\<우편번호 >"</span><span class="sxs-lookup"><span data-stu-id="5e07e-170">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="5e07e-171">-PreferredLanguage "\<언어 >"</span><span class="sxs-lookup"><span data-stu-id="5e07e-171">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="5e07e-172">-상태 "\<상태 이름 >"</span><span class="sxs-lookup"><span data-stu-id="5e07e-172">-State "\<state name>"</span></span>
    
- <span data-ttu-id="5e07e-173">-StreetAddress "\<주소 >"</span><span class="sxs-lookup"><span data-stu-id="5e07e-173">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="5e07e-174">-Title "\<제목 이름 >"</span><span class="sxs-lookup"><span data-stu-id="5e07e-174">-Title "\<title name>"</span></span>
    
- <span data-ttu-id="5e07e-175">-Usagelocation이 "\<2 자리 국가 또는 지역 코드 >"</span><span class="sxs-lookup"><span data-stu-id="5e07e-175">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="5e07e-176">ISO 3166-1 alpha-2 (A2) 두 문자로 된 국가 또는 지역 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="5e07e-176">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="5e07e-177">추가 매개 변수에 대 한 [이와](https://msdn.microsoft.com/library/azure/dn194136.aspx) 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="5e07e-177">See [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) for additional parameters.</span></span>
  
<span data-ttu-id="5e07e-178">모든 사용자의 사용자 계정 이름을 보려면 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e07e-178">To see the User Principal Names of all your users, run the following command.</span></span>
  
```
Get-MSolUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="5e07e-179">이 명령은 지시 하는 Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="5e07e-179">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="5e07e-180">사용자 계정 ( **Get-msoluser** )에 대 한 정보를 모두 가져오고에 다음 명령을 보낼 ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="5e07e-180">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="5e07e-181">사용자 계정 이름 목록을 사전순으로 정렬 ( **Sort 개체 UserPrincipalName** )에 다음 명령을 보냅니다 ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="5e07e-181">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="5e07e-182">각 계정 ( **Select-object UserPrincipalName** )에 대 한 사용자 계정 이름 속성만을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e07e-182">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
    
- <span data-ttu-id="5e07e-183">하 한 화면에 표시 ( **더 많은** ) 한번 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e07e-183">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="5e07e-p107">이 명령은 계정을 모두 나열 합니다. 기반으로 표시 하는 계정에 대 한 사용자 계정 이름 표시 하려는 경우 (이름 및 성) 이름, 아래 **$userName** 변수를 입력 (제거는 \< 및 > 문자), 그런 후 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e07e-p107">This command will list all of your accounts. If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="5e07e-186">Caleb Sills 라는 사용자에 대 한 사용자 계정 이름을 표시 하는이 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="5e07e-186">This example displays the User Principal Name for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="5e07e-p108">**$Upn** 변수를 사용 하 여 표시 이름에 따라 개별 계정에 변경할 수 있습니다. 다음은 프랑스, Belinda Newman의 사용 현황 위치를 설정 하지만 그녀의 사용자 계정 이름 대신 그녀의 표시 이름을 지정 하는 예제가입니다.</span><span class="sxs-lookup"><span data-stu-id="5e07e-p108">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```
$userName="<display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="5e07e-189">모든 사용자 계정에 대 한 속성을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e07e-189">Change properties for all user accounts</span></span>

<span data-ttu-id="5e07e-p109">모든 사용자에 대한 속성을 변경하려면 **Get-msoluser** 및 **Set-msoluser** cmdlet의 조합을 사용합니다. 다음 예에서는 모든 사용자의 사용 위치를 프랑스로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="5e07e-p109">To change properties for all users, you can use the combination of the **Get-MsolUser** and **Set-MsolUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="5e07e-192">이 명령은 지시 하는 Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="5e07e-192">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="5e07e-193">사용자 계정 ( **Get-msoluser** )에 대 한 정보를 모두 가져오고에 다음 명령을 보낼 ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="5e07e-193">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="5e07e-194">프랑스 ( **이와-usagelocation이 "FR"** )로 사용자 위치를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e07e-194">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="5e07e-195">사용자 계정의 특정 집합에 대 한 속성을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e07e-195">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="5e07e-p110">사용자 계정의 특정 집합에 대 한 속성을 변경 하려면 **Get-msoluser**, **Where-object**및 **이와** cmdlet의 조합을 사용할 수 있습니다. 프랑스 회계 부서의 모든 사용자에 대 한 사용 현황 위치를 변경 하는 다음 예제에서는:</span><span class="sxs-lookup"><span data-stu-id="5e07e-p110">To change properties for a specific set of user account, you can use the combination of the **Get-MsolUser**, **Where-Object**, and **Set-MsolUser** cmdlets. The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```
Get-MsolUser | Where-Object {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="5e07e-198">이 명령은 지시 하는 Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="5e07e-198">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="5e07e-199">사용자 계정 ( **Get-msoluser** )에 대 한 정보를 모두 가져오고에 다음 명령을 보낼 ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="5e07e-199">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="5e07e-200">해당 부서 속성이 "Accounting"로 설정 ( **Where-object {$_ 사용자 계정을 모두 찾기. 부서-eq "Accounting"}** )에 다음 명령을 결과 정보를 보내고 ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="5e07e-200">Find all of the user accounts that have their Department property set to "Accounting" ( **Where-Object {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="5e07e-201">프랑스 ( **이와-usagelocation이 "FR"** )로 사용자 위치를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e07e-201">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    

## <a name="see-also"></a><span data-ttu-id="5e07e-202">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5e07e-202">See also</span></span>

[<span data-ttu-id="5e07e-203">Office 365 PowerShell을 사용하여 사용자 계정 및 라이선스 관리</span><span class="sxs-lookup"><span data-stu-id="5e07e-203">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="5e07e-204">Office 365 PowerShell을 사용하여 Office 365 관리</span><span class="sxs-lookup"><span data-stu-id="5e07e-204">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="5e07e-205">Office 365 PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="5e07e-205">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
