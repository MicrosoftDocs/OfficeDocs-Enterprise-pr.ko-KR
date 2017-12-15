---
title: "Office 365 PowerShell를 사용 하 여 사용자 계정 속성 구성"
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
- DecEntMigration
- O365ITProTrain
- Ent_Office_Other
- PowerShell
- apr17entnews
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: "요약: Office 365 테 넌 트에 개인 또는 여러 사용자 계정 속성을 구성 하려면 Office 365 PowerShell를 사용 합니다."
ms.openlocfilehash: d9e817530f3b1554cb757720f01afec5ed3b63ef
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2017
---
# <a name="configure-user-account-properties-with-office-365-powershell"></a><span data-ttu-id="fb2e7-103">Office 365 PowerShell를 사용 하 여 사용자 계정 속성 구성</span><span class="sxs-lookup"><span data-stu-id="fb2e7-103">Configure user account properties with Office 365 PowerShell</span></span>

 <span data-ttu-id="fb2e7-104">**요약:** Office 365 PowerShell을 사용 하 여 Office 365 테 넌 트의 개인 또는 여러 사용자 계정 속성 구성.</span><span class="sxs-lookup"><span data-stu-id="fb2e7-104">**Summary:** Use Office 365 PowerShell to configure properties of individual or multiple user accounts in your Office 365 tenant.</span></span>
  
<span data-ttu-id="fb2e7-105">Office 365 관리 센터를 사용 하 여 Office 365 테 넌 트의 사용자 계정에 대 한 속성을 구성할 수 있지만 Office 365 PowerShell을 사용 하 여 수 및 Office 365 관리 센터 수 없는 일부 작업을 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb2e7-105">Although you can use the Office 365 Admin center to configure properties for the user accounts of your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the Office 365 Admin center cannot.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="fb2e7-106">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="fb2e7-106">Before you begin</span></span>

<span data-ttu-id="fb2e7-p101">이 항목의 절차에서는 Office 365 PowerShell에 연결 해야 합니다. 자세한 내용은 [Office 365 PowerShell 연결](connect-to-office-365-powershell.md)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="fb2e7-p101">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
## <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="fb2e7-109">특정 사용자 계정에 대 한 속성을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb2e7-109">Change properties for a specific user account</span></span>

<span data-ttu-id="fb2e7-p102">특정 사용자 계정에 대 한 속성을 구성 하려면 [이와](https://msdn.microsoft.com/library/azure/dn194136.aspx) cmdlet을 사용 하 고 속성을 설정 하거나 변경를 지정 합니다. 프랑스 Belinda Newman의 사용 현황 위치를 변경 하는이 예제에서는 명령 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb2e7-p102">To configure properties for a specific user account, you use the [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) cmdlet and specify the properties to set or change. This example command changes Belinda Newman's usage location to France:</span></span>
  
```
Set-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" -UsageLocation "FR"
```

<span data-ttu-id="fb2e7-p103">하면 **-UserPrincipalName** 매개 변수와 함께 계정을 식별 하 고 설정 또는 추가 매개 변수를 사용 하 여 특정 속성을 변경 합니다. 가장 일반적인 매개 변수 목록은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="fb2e7-p103">You identify the account with the **-UserPrincipalName** parameter and set or change specific properties with additional parameters. Here is a list of the most common parameters.</span></span>
  
- <span data-ttu-id="fb2e7-114">-도시 "\<도시 이름 >"</span><span class="sxs-lookup"><span data-stu-id="fb2e7-114">-City "\<city name>"</span></span>
    
- <span data-ttu-id="fb2e7-115">-국가 "\<국가 이름 >"</span><span class="sxs-lookup"><span data-stu-id="fb2e7-115">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="fb2e7-116">-부서 "\<부서 이름 >"</span><span class="sxs-lookup"><span data-stu-id="fb2e7-116">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="fb2e7-117">-DisplayName "\<완전 한 사용자 이름 >"</span><span class="sxs-lookup"><span data-stu-id="fb2e7-117">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="fb2e7-118">-팩스 "\<팩스 번호 >"</span><span class="sxs-lookup"><span data-stu-id="fb2e7-118">-Fax "\<fax number>"</span></span>
    
- <span data-ttu-id="fb2e7-119">-FirstName "\<사용자 이름 >"</span><span class="sxs-lookup"><span data-stu-id="fb2e7-119">-FirstName "\<user first name>"</span></span>
    
- <span data-ttu-id="fb2e7-120">-LastName "\<사용자 마지막 이름 >"</span><span class="sxs-lookup"><span data-stu-id="fb2e7-120">-LastName "\<user last name>"</span></span>
    
- <span data-ttu-id="fb2e7-121">-MobilePhone "\<휴대폰 번호 >"</span><span class="sxs-lookup"><span data-stu-id="fb2e7-121">-MobilePhone "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="fb2e7-122">-Office "\<사무실 위치 >"</span><span class="sxs-lookup"><span data-stu-id="fb2e7-122">-Office "\<office location>"</span></span>
    
- <span data-ttu-id="fb2e7-123">-PhoneNumber "\<사무실 전화번호 >"</span><span class="sxs-lookup"><span data-stu-id="fb2e7-123">-PhoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="fb2e7-124">-PostalCode "\<우편번호 >"</span><span class="sxs-lookup"><span data-stu-id="fb2e7-124">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="fb2e7-125">-PreferredLanguage "\<언어 >"</span><span class="sxs-lookup"><span data-stu-id="fb2e7-125">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="fb2e7-126">-상태 "\<상태 이름 >"</span><span class="sxs-lookup"><span data-stu-id="fb2e7-126">-State "\<state name>"</span></span>
    
- <span data-ttu-id="fb2e7-127">-StreetAddress "\<주소 >"</span><span class="sxs-lookup"><span data-stu-id="fb2e7-127">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="fb2e7-128">-Title "\<제목 이름 >"</span><span class="sxs-lookup"><span data-stu-id="fb2e7-128">-Title "\<title name>"</span></span>
    
- <span data-ttu-id="fb2e7-129">-Usagelocation이 "\<2 자리 국가 또는 지역 코드 >"</span><span class="sxs-lookup"><span data-stu-id="fb2e7-129">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="fb2e7-130">ISO 3166-1 alpha-2 (A2) 두 문자로 된 국가 또는 지역 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="fb2e7-130">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="fb2e7-131">추가 매개 변수에 대 한 [이와](https://msdn.microsoft.com/library/azure/dn194136.aspx) 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="fb2e7-131">See [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) for additional parameters.</span></span>
  
<span data-ttu-id="fb2e7-132">모든 사용자의 사용자 계정 이름을 보려면 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb2e7-132">To see the User Principal Names of all your users, run the following command.</span></span>
  
```
Get-MSolUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="fb2e7-133">이 명령은 지시 하는 Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="fb2e7-133">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="fb2e7-134">사용자 계정 ( **Get-msoluser** )에 대 한 정보를 모두 가져오고에 다음 명령을 보낼 ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="fb2e7-134">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="fb2e7-135">사용자 계정 이름 목록을 사전순으로 정렬 ( **Sort 개체 UserPrincipalName** )에 다음 명령을 보냅니다 ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="fb2e7-135">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="fb2e7-136">각 계정 ( **Select-object UserPrincipalName** )에 대 한 사용자 계정 이름 속성만을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb2e7-136">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
    
- <span data-ttu-id="fb2e7-137">하 한 화면에 표시 ( **더 많은** ) 한번 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb2e7-137">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="fb2e7-p104">이 명령은 계정을 모두 나열 합니다. 기반으로 표시 하는 계정에 대 한 사용자 계정 이름 표시 하려는 경우 (이름 및 성) 이름, 아래 **$userName** 변수를 입력 (제거는 \< 및 > 문자), 그런 후 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb2e7-p104">This command will list all of your accounts. If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="fb2e7-140">Caleb Sills 라는 사용자에 대 한 사용자 계정 이름을 표시 하는이 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="fb2e7-140">This example displays the User Principal Name for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="fb2e7-p105">**$Upn** 변수를 사용 하 여 표시 이름에 따라 개별 계정에 변경할 수 있습니다. 다음은 프랑스, Belinda Newman의 사용 현황 위치를 설정 하지만 그녀의 사용자 계정 이름 대신 그녀의 표시 이름을 지정 하는 예제가입니다.</span><span class="sxs-lookup"><span data-stu-id="fb2e7-p105">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```
$userName="<Display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

## <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="fb2e7-143">모든 사용자 계정에 대 한 속성을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb2e7-143">Change properties for all user accounts</span></span>

<span data-ttu-id="fb2e7-p106">모든 사용자에 대 한 속성을 변경 하려면 **Get-msoluser** 및 **이와** cmdlet의 조합을 사용할 수 있습니다. 프랑스에 모든 사용자에 대 한 사용 현황 위치를 변경 하는 다음 예제에서는:</span><span class="sxs-lookup"><span data-stu-id="fb2e7-p106">To change properties for all users, you can use the combination of the **Get-MsolUser** and **Set-MsolUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="fb2e7-146">이 명령은 지시 하는 Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="fb2e7-146">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="fb2e7-147">사용자 계정 ( **Get-msoluser** )에 대 한 정보를 모두 가져오고에 다음 명령을 보낼 ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="fb2e7-147">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="fb2e7-148">프랑스 ( **이와-usagelocation이 "FR"** )로 사용자 위치를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb2e7-148">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    
## <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="fb2e7-149">사용자 계정의 특정 집합에 대 한 속성을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb2e7-149">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="fb2e7-p107">사용자 계정의 특정 집합에 대 한 속성을 변경 하려면 **Get-msoluser**, **Where-object**및 **이와** cmdlet의 조합을 사용할 수 있습니다. 프랑스 회계 부서의 모든 사용자에 대 한 사용 현황 위치를 변경 하는 다음 예제에서는:</span><span class="sxs-lookup"><span data-stu-id="fb2e7-p107">To change properties for a specific set of user account, you can use the combination of the **Get-MsolUser**, **Where-Object**, and **Set-MsolUser** cmdlets. The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```
Get-MsolUser | Where-Object {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="fb2e7-152">이 명령은 지시 하는 Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="fb2e7-152">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="fb2e7-153">사용자 계정 ( **Get-msoluser** )에 대 한 정보를 모두 가져오고에 다음 명령을 보낼 ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="fb2e7-153">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="fb2e7-154">해당 부서 속성이 "Accounting"로 설정 ( **Where-object {$_ 사용자 계정을 모두 찾기. 부서-eq "Accounting"}** )에 다음 명령을 결과 정보를 보내고 ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="fb2e7-154">Find all of the user accounts that have their Department property set to "Accounting" ( **Where-Object {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="fb2e7-155">프랑스 ( **이와-usagelocation이 "FR"** )로 사용자 위치를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb2e7-155">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    
- <span data-ttu-id="fb2e7-156">하 한 화면에 표시 ( **더 많은** ) 한번 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb2e7-156">Display them one screen at a time ( **More** ).</span></span>
    
## <a name="use-the-azure-active-directory-v2-powershell-module-to-configure-user-account-properties"></a><span data-ttu-id="fb2e7-157">Azure Active Directory V2 PowerShell 모듈을 사용 하 여 사용자 계정 속성을 구성 하려면</span><span class="sxs-lookup"><span data-stu-id="fb2e7-157">Use the Azure Active Directory V2 PowerShell module to configure user account properties</span></span>

<span data-ttu-id="fb2e7-p108">Azure Active Directory V2 PowerShell 모듈을 사용자 계정에 대 한 속성을 구성 하려면 [집합 AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet을 사용 하 고 속성을 설정 하거나 변경를 지정 합니다. 하지만 먼저, 구독에 연결 해야 합니다. 지침, [Azure Active Directory V2 PowerShell 모듈을 사용 하 여 연결](https://go.microsoft.com/fwlink/?linkid=842218)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="fb2e7-p108">To configure properties for user accounts with the Azure Active Directory V2 PowerShell module, you use the [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet and specify the properties to set or change. But first, you must connect to your subscription. For the instructions, see [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="fb2e7-161">특정 사용자 계정에 대 한 속성을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb2e7-161">Change properties for a specific user account</span></span>

<span data-ttu-id="fb2e7-162">프랑스 Belinda Newman의 사용 현황 위치를 변경 하는이 예제에서는 명령 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb2e7-162">This example command changes Belinda Newman's usage location to France:</span></span>
  
```
Set-AzureADUser -ObjectID "BelindaN@litwareinc.onmicosoft.com" -UsageLocation "FR"
```

<span data-ttu-id="fb2e7-p109">하면 **-ObjectID** 매개 변수와 함께 계정을 식별 하 고 설정 또는 추가 매개 변수를 사용 하 여 특정 속성을 변경 합니다. 가장 일반적인 매개 변수 목록은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="fb2e7-p109">You identify the account with the **-ObjectID** parameter and set or change specific properties with additional parameters. Here is a list of the most common parameters.</span></span>
  
- <span data-ttu-id="fb2e7-165">-부서 "\<부서 이름 >"</span><span class="sxs-lookup"><span data-stu-id="fb2e7-165">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="fb2e7-166">-DisplayName "\<완전 한 사용자 이름 >"</span><span class="sxs-lookup"><span data-stu-id="fb2e7-166">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="fb2e7-167">-FacsimilieTelephoneNumber "\<팩스 번호 >"</span><span class="sxs-lookup"><span data-stu-id="fb2e7-167">-FacsimilieTelephoneNumber "\<fax number>"</span></span>
    
- <span data-ttu-id="fb2e7-168">-GivenName "\<사용자 이름 >"</span><span class="sxs-lookup"><span data-stu-id="fb2e7-168">-GivenName "\<user first name>"</span></span>
    
- <span data-ttu-id="fb2e7-169">-성 "\<사용자 마지막 이름 >"</span><span class="sxs-lookup"><span data-stu-id="fb2e7-169">-Surname "\<user last name>"</span></span>
    
- <span data-ttu-id="fb2e7-170">-모바일 "\<휴대폰 번호 >"</span><span class="sxs-lookup"><span data-stu-id="fb2e7-170">-Mobile "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="fb2e7-171">-JobTitle "\<직함 >"</span><span class="sxs-lookup"><span data-stu-id="fb2e7-171">-JobTitle "\<job title>"</span></span>
    
- <span data-ttu-id="fb2e7-172">-PreferredLanguage "\<언어 >"</span><span class="sxs-lookup"><span data-stu-id="fb2e7-172">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="fb2e7-173">-StreetAddress "\<주소 >"</span><span class="sxs-lookup"><span data-stu-id="fb2e7-173">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="fb2e7-174">-도시 "\<도시 이름 >"</span><span class="sxs-lookup"><span data-stu-id="fb2e7-174">-City "\<city name>"</span></span>
    
- <span data-ttu-id="fb2e7-175">-상태 "\<상태 이름 >"</span><span class="sxs-lookup"><span data-stu-id="fb2e7-175">-State "\<state name>"</span></span>
    
- <span data-ttu-id="fb2e7-176">-PostalCode "\<우편번호 >"</span><span class="sxs-lookup"><span data-stu-id="fb2e7-176">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="fb2e7-177">-국가 "\<국가 이름 >"</span><span class="sxs-lookup"><span data-stu-id="fb2e7-177">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="fb2e7-178">-TelephoneNumber "\<사무실 전화번호 >"</span><span class="sxs-lookup"><span data-stu-id="fb2e7-178">-TelephoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="fb2e7-179">-Usagelocation이 "\<2 자리 국가 또는 지역 코드 >"</span><span class="sxs-lookup"><span data-stu-id="fb2e7-179">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="fb2e7-180">ISO 3166-1 alpha-2 (A2) 두 문자로 된 국가 또는 지역 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="fb2e7-180">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="fb2e7-181">추가 매개 변수 [집합 AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) 을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="fb2e7-181">See [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) for additional parameters.</span></span>
  
<span data-ttu-id="fb2e7-182">사용자 계정에 대 한 사용자 계정 이름을 표시 하려면 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb2e7-182">To display the User Principal Name for your user accounts, run the following command.</span></span>
  
```
Get-AzureADUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="fb2e7-183">이 명령은 지시 하는 Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="fb2e7-183">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="fb2e7-184">사용자 계정 ( **Get AzureADUser** )에 대 한 정보를 모두 가져오고에 다음 명령을 보낼 ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="fb2e7-184">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="fb2e7-185">사용자 계정 이름 목록을 사전순으로 정렬 ( **Sort 개체 UserPrincipalName** )에 다음 명령을 보냅니다 ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="fb2e7-185">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="fb2e7-186">각 계정 ( **Select-object UserPrincipalName** )에 대 한 사용자 계정 이름 속성만을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb2e7-186">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
- <span data-ttu-id="fb2e7-187">하 한 화면에 표시 ( **더 많은** ) 한번 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb2e7-187">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="fb2e7-p110">이 명령은 계정을 모두 나열 합니다. 기반으로 표시 하는 계정에 대 한 사용자 계정 이름 표시 하려는 경우 (이름 및 성) 이름, 아래 **$userName** 변수를 입력 (제거는 \< 및 > 문자), 그런 후 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb2e7-p110">This command will list all of your accounts. If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="fb2e7-190">Caleb Sills 라는 사용자에 대 한 사용자 계정 이름을 표시 하는이 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="fb2e7-190">This example displays the User Principal Name for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="fb2e7-p111">**$Upn** 변수를 사용 하 여 표시 이름에 따라 개별 계정에 변경할 수 있습니다. 다음은 프랑스, Belinda Newman의 사용 현황 위치를 설정 하지만 그녀의 사용자 계정 이름 대신 그녀의 표시 이름을 지정 하는 예제가입니다.</span><span class="sxs-lookup"><span data-stu-id="fb2e7-p111">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="fb2e7-193">모든 사용자 계정에 대 한 속성을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb2e7-193">Change properties for all user accounts</span></span>

<span data-ttu-id="fb2e7-p112">모든 사용자에 대 한 속성을 변경 하려면 **Get AzureADUser** 및 **집합 AzureADUser** cmdlet의 조합을 사용할 수 있습니다. 프랑스에 모든 사용자에 대 한 사용 현황 위치를 변경 하는 다음 예제에서는:</span><span class="sxs-lookup"><span data-stu-id="fb2e7-p112">To change properties for all users, you can use the combination of the **Get-AzureADUser** and **Set-AzureADUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="fb2e7-196">이 명령은 지시 하는 Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="fb2e7-196">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="fb2e7-197">사용자 계정 ( **Get AzureADUser** )에 대 한 정보를 모두 가져오고에 다음 명령을 보낼 ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="fb2e7-197">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="fb2e7-198">프랑스 ( **집합 AzureADUser-usagelocation이 "FR"** )로 사용자 위치를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb2e7-198">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="fb2e7-199">사용자 계정의 특정 집합에 대 한 속성을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb2e7-199">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="fb2e7-p113">사용자 계정의 특정 집합에 대 한 속성을 변경 하려면 **Get AzureADUser**, **위치**및 **집합 AzureADUser** cmdlet의 조합을 사용할 수 있습니다. 프랑스 회계 부서의 모든 사용자에 대 한 사용 현황 위치를 변경 하는 다음 예제에서는:</span><span class="sxs-lookup"><span data-stu-id="fb2e7-p113">To change properties for a specific set of user account, you can use the combination of the **Get-AzureADUser**, **Where**, and **Set-AzureADUser** cmdlets. The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="fb2e7-202">이 명령은 지시 하는 Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="fb2e7-202">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="fb2e7-203">사용자 계정 ( **Get AzureADUser** )에 대 한 정보를 모두 가져오고에 다음 명령을 보낼 ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="fb2e7-203">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="fb2e7-204">해당 부서 속성이 "Accounting"로 설정 하는 사용자 계정을 모두 찾기 ( **여기에서 {$_ 합니다. 부서-eq "Accounting"}** )에 다음 명령을 결과 정보를 보내고 ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="fb2e7-204">Find all of the user accounts that have their Department property set to "Accounting" ( **Where {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="fb2e7-205">프랑스 ( **집합 AzureADUser-usagelocation이 "FR"** )로 사용자 위치를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb2e7-205">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
## <a name="see-also"></a><span data-ttu-id="fb2e7-206">See also</span><span class="sxs-lookup"><span data-stu-id="fb2e7-206">See also</span></span>

#### 

[<span data-ttu-id="fb2e7-207">사용자 계정 및 Office 365 powershell 라이선스 관리</span><span class="sxs-lookup"><span data-stu-id="fb2e7-207">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="fb2e7-208">Office 365 PowerShell로 Office 365 관리</span><span class="sxs-lookup"><span data-stu-id="fb2e7-208">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="fb2e7-209">Office 365 PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="fb2e7-209">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

