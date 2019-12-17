---
title: Office 365 PowerShell을 사용 하 여 사용자 계정 만들기
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/16/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- O365ITProTrain
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: 사용 하는 방법은 Office 365 PowerShell 에 대 한 사용자 계정을 만드는 Office 365.
ms.openlocfilehash: b69e0afa6177f29ed2abe18be39f5db08c9f5e75
ms.sourcegitcommit: 3539ec707f984de6f3b874744ff8b6832fbd665e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/17/2019
ms.locfileid: "40072230"
---
# <a name="create-user-accounts-with-office-365-powershell"></a><span data-ttu-id="3a4aa-103">Office 365 PowerShell을 사용 하 여 사용자 계정 만들기</span><span class="sxs-lookup"><span data-stu-id="3a4aa-103">Create user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="3a4aa-p101">사용할 수 있습니다 Office 365 PowerShell 효과적으로 사용자 계정, 특히 여러 사용자 계정을 만들 수 있습니다. 사용자 계정을 만들 때 Office 365 PowerShell, 특정 계정 속성은 항상 필요 합니다. 다른 속성의 계정을 만들 필요는 없습니다 그렇지 않을 경우 중요 합니다. 다음 표에서 이러한 제한에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3a4aa-p101">You can use Office 365 PowerShell to efficiently create user accounts, especially multiple user accounts. When you create user accounts in Office 365 PowerShell, certain account properties are always required. Other properties aren't required to create the account, but are otherwise important. These properties are described in the following table:</span></span>
  
|<span data-ttu-id="3a4aa-108">**속성 이름**</span><span class="sxs-lookup"><span data-stu-id="3a4aa-108">**Property name**</span></span>|<span data-ttu-id="3a4aa-109">**필수 여부**</span><span class="sxs-lookup"><span data-stu-id="3a4aa-109">**Required?**</span></span>|<span data-ttu-id="3a4aa-110">**설명**</span><span class="sxs-lookup"><span data-stu-id="3a4aa-110">**Description**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="3a4aa-111">**DisplayName**</span><span class="sxs-lookup"><span data-stu-id="3a4aa-111">**DisplayName**</span></span> <br/> |<span data-ttu-id="3a4aa-112">예</span><span class="sxs-lookup"><span data-stu-id="3a4aa-112">Yes</span></span>  <br/> |<span data-ttu-id="3a4aa-p102">표시 이름에 사용 되는 Office 365 서비스. 예를 들어, Caleb 창턱</span><span class="sxs-lookup"><span data-stu-id="3a4aa-p102">This is the display name that's used in Office 365 services. For example, Caleb Sills.</span></span>  <br/> |
|<span data-ttu-id="3a4aa-115">**UserPrincipalName**</span><span class="sxs-lookup"><span data-stu-id="3a4aa-115">**UserPrincipalName**</span></span> <br/> |<span data-ttu-id="3a4aa-116">예</span><span class="sxs-lookup"><span data-stu-id="3a4aa-116">Yes</span></span>  <br/> |<span data-ttu-id="3a4aa-p103">계정에 로그인 하는 데 사용 되는 이름 Office 365 서비스. For example, CalebS@contoso.onmicrosoft.com.</span><span class="sxs-lookup"><span data-stu-id="3a4aa-p103">This is the account name that's used to sign in to Office 365 services. For example, CalebS@contoso.onmicrosoft.com.</span></span>  <br/> |
|<span data-ttu-id="3a4aa-119">**FirstName**</span><span class="sxs-lookup"><span data-stu-id="3a4aa-119">**FirstName**</span></span> <br/> |<span data-ttu-id="3a4aa-120">아니요</span><span class="sxs-lookup"><span data-stu-id="3a4aa-120">No</span></span>  <br/> ||
|<span data-ttu-id="3a4aa-121">**LastName**</span><span class="sxs-lookup"><span data-stu-id="3a4aa-121">**LastName**</span></span> <br/> |<span data-ttu-id="3a4aa-122">아니요</span><span class="sxs-lookup"><span data-stu-id="3a4aa-122">No</span></span>  <br/> ||
|<span data-ttu-id="3a4aa-123">**LicenseAssignment**</span><span class="sxs-lookup"><span data-stu-id="3a4aa-123">**LicenseAssignment**</span></span> <br/> |<span data-ttu-id="3a4aa-124">아니요</span><span class="sxs-lookup"><span data-stu-id="3a4aa-124">No</span></span>  <br/> |<span data-ttu-id="3a4aa-p104">사용 가능한 라이선스가 사용자 계정에 할당되는 라이선싱 계획(라이선스 계획, Office 365 계획 또는 SKU라고도 함)입니다. 라이선스는 계정에서 사용할 수 있는 Office 365 서비스를 정의합니다. 계정을 만들 때 사용자에게 라이선스를 할당할 필요는 없지만 계정이 Office 365 서비스에 액세스하려면 라이선스가 필요합니다. 만든 후에 사용자 계정에 30일 간의 라이선스가 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a4aa-p104">This is the licensing plan (also known as the license plan, Office 365 plan, or SKU) from which an available license is assigned to the user account. The license defines the Office 365 services that are available to account. You don't have to assign a license to a user when you create the account, but the account requires a license to access Office 365 services. You have 30 days to license the user account after you create it.</span></span> |
|<span data-ttu-id="3a4aa-129">**Password**</span><span class="sxs-lookup"><span data-stu-id="3a4aa-129">**Password**</span></span> <br/> |<span data-ttu-id="3a4aa-130">아니요</span><span class="sxs-lookup"><span data-stu-id="3a4aa-130">No</span></span>  <br/> | <span data-ttu-id="3a4aa-p105">암호를 지정하지 않으면 사용자 계정에 임의의 암호가 할당되고, 명령 결과에 암호가 표시됩니다. 암호를 지정할 때에는 소문자, 대문자, 숫자, 기호 중 3가지가 포함된 길이 8 ~ 16의 ASCII 문자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3a4aa-p105">If you don't specify a password, a random password is assigned to the user account, and the password is visible in the results of the command. If you specify a password, it needs to be 8 to 16 ASCII text characters from any three of the following types: lowercase letters, uppercase letters, numbers, and symbols.</span></span> <br/> |
|<span data-ttu-id="3a4aa-133">**UsageLocation**</span><span class="sxs-lookup"><span data-stu-id="3a4aa-133">**UsageLocation**</span></span> <br/> |<span data-ttu-id="3a4aa-134">아니요</span><span class="sxs-lookup"><span data-stu-id="3a4aa-134">No</span></span>  <br/> |<span data-ttu-id="3a4aa-p106">유효한 ISO 3166-1 alpha-2 국가 코드입니다. 예를 들어 미국은 US, 프랑스는 FR입니다. 특정 국가에서는 일부 Office 365 서비스를 사용할 수 없으므로 이 값을 제공하는 것이 중요합니다. 따라서 계정에 이 값이 구성되어 있지 않으면 사용자 계정에 라이선스를 할당할 수 없습니다. 자세한 내용은 [라이센스 제한 정보](https://go.microsoft.com/fwlink/p/?LinkId=691730)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3a4aa-p106">This is a valid ISO 3166-1 alpha-2 country code. For example, US for the United States, and FR for France. It's important to provide this value, because some Office 365 services aren't available in certain countries, so you can't assign a license to a user account unless the account has this value configured. For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).  </span></span><br/> |
   

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="3a4aa-139">Graph 모듈용 Azure Active Directory PowerShell 사용하기</span><span class="sxs-lookup"><span data-stu-id="3a4aa-139">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="3a4aa-140">먼저, [Office 365 테넌트에 연결](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)합니다.</span><span class="sxs-lookup"><span data-stu-id="3a4aa-140">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>

<span data-ttu-id="3a4aa-141">연결한 후 다음 구문을 사용하여 개별 계정을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3a4aa-141">After you have connected, use the following syntax to create an individual account:</span></span>
  
```powershell
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="<user account password>"
New-AzureADUser -DisplayName "<display name>" -GivenName "<first name>" -SurName "<last name>" -UserPrincipalName <sign-in name> -UsageLocation <ISO 3166-1 alpha-2 country code> -MailNickName <mailbox name> -PasswordProfile $PasswordProfile -AccountEnabled $true
```

<span data-ttu-id="3a4aa-142">이 예제에서는 Caleb Sills라는 미국 사용자의 계정을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3a4aa-142">This example creates an account for the United States user named Caleb Sills:</span></span>
  
```powershell
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="3Rv0y1q39/chsy"
New-AzureADUser -DisplayName "Caleb Sills" -GivenName "Caleb" -SurName "Sills" -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -MailNickName calebs -PasswordProfile $PasswordProfile -AccountEnabled $true
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="3a4aa-143">Windows PowerShell용 Microsoft Azure Active Directory 모듈 사용하기</span><span class="sxs-lookup"><span data-stu-id="3a4aa-143">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="3a4aa-144">먼저, [Office 365 테넌트에 연결](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)합니다.</span><span class="sxs-lookup"><span data-stu-id="3a4aa-144">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

### <a name="create-an-individual-user-account"></a><span data-ttu-id="3a4aa-145">개별 사용자 계정 만들기</span><span class="sxs-lookup"><span data-stu-id="3a4aa-145">Create an individual user account</span></span>

<span data-ttu-id="3a4aa-146">개별 계정을 만들려면 다음 구문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3a4aa-146">To create an individual account, use the following syntax:</span></span>
  
```powershell
New-MsolUser -DisplayName <display name> -FirstName <first name> -LastName <last name> -UserPrincipalName <sign-in name> -UsageLocation <ISO 3166-1 alpha-2 country code> -LicenseAssignment <licensing plan name> [-Password <Password>]
```

>[!Note]
><span data-ttu-id="3a4aa-147">PowerShell Core는 Windows PowerShell용 Microsoft Azure Active Directory 모듈 및 이름에 **Msol**이 있는 cmdlet을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3a4aa-147">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="3a4aa-148">이러한 cmdlet을 계속 사용하려면 Windows PowerShell에서 이를 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a4aa-148">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="3a4aa-149">사용 가능한 라이선스 계획 이름을 열거하려면 이 명령을  사용합니다:</span><span class="sxs-lookup"><span data-stu-id="3a4aa-149">To list the available licensing plan names, use this command:</span></span>

````powershell
Get-MsolAccountSku
````

<span data-ttu-id="3a4aa-150">이 예제에서는 Caleb Sills라는 미국 사용자의 계정을 만들고, `contoso:ENTERPRISEPACK`(Office 365 Enterprise E3) 라이선스 계획에서 라이선스를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="3a4aa-150">This example creates an account for the United States user named Caleb Sills, and assigns a license from the `contoso:ENTERPRISEPACK` (Office 365 Enterprise E3) licensing plan.</span></span>
  
```powershell
New-MsolUser -DisplayName "Caleb Sills" -FirstName Caleb -LastName Sills -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -LicenseAssignment contoso:ENTERPRISEPACK
```

### <a name="create-multiple-user-accounts"></a><span data-ttu-id="3a4aa-151">다중 사용자 계정 만들기</span><span class="sxs-lookup"><span data-stu-id="3a4aa-151">Create multiple user accounts</span></span>

1. <span data-ttu-id="3a4aa-p108">필요한 사용자 계정 정보를 포함하는 쉼표로 구분 된 값(CSV) 파일을 만듭니다. 예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3a4aa-p108">Create a comma-separated value (CSV) file that contains the required user account information. For example:</span></span>
    
  ```powershell
  UserPrincipalName,FirstName,LastName,DisplayName,UsageLocation,AccountSkuId
  ClaudeL@contoso.onmicrosoft.com,Claude,Loiselle,Claude Loiselle,US,contoso:ENTERPRISEPACK
  LynneB@contoso.onmicrosoft.com,Lynne,Baxter,Lynne Baxter,US,contoso:ENTERPRISEPACK
  ShawnM@contoso.onmicrosoft.com,Shawn,Melendez,Shawn Melendez,US,contoso:ENTERPRISEPACK
  ```

 > [!NOTE]
><span data-ttu-id="3a4aa-154">CSV 파일의 첫 번째 행에서 열 이름 및 순서는 무작위지만 나머지 파일의 데이터는 열 이름의 순서와 일치하는지 확인하고 Office 365 PowerShell 명령에서 매개 변수 값의 열 이름을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3a4aa-154">The column names and their order in the first row of the CSV file are arbitrary, but make sure the data in the rest of the file matches the order of the column names, and use the column names for the parameter values in the Office 365 PowerShell command.</span></span>
    
2. <span data-ttu-id="3a4aa-155">다음 구문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3a4aa-155">Use the following syntax:</span></span>
    
  ```powershell
  Import-Csv -Path <Input CSV File Path and Name> | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId [-Password $_.Password]} | Export-Csv -Path <Output CSV File Path and Name>
  ```

<span data-ttu-id="3a4aa-156">이 예제는 C:\My Documents\NewAccounts.csv 라는 파일에서 사용자 계정을 만들고 C:\My Documents\NewAccountResults.csv 라는 파일에 결과를 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="3a4aa-156">This example creates the user accounts from the file named C:\My Documents\NewAccounts.csv, and logs the results in the file named C:\My Documents\NewAccountResults.csv</span></span>
    
  ```powershell
  Import-Csv -Path "C:\My Documents\NewAccounts.csv" | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId} | Export-Csv -Path "C:\My Documents\NewAccountResults.csv"
  ```

3. <span data-ttu-id="3a4aa-p109">결과를 보려면 출력 파일을 확인합니다. 암호를 지정하지 않았으므로 Office 365가 생성한 임의의 암호가 출력 파일에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a4aa-p109">Review the output file to see the results. We didn't specify passwords, so the random passwords that Office 365 generated are visible in the output file.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="3a4aa-159">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3a4aa-159">See also</span></span>

[<span data-ttu-id="3a4aa-160">Office 365 PowerShell을 사용 하 여 사용자 계정, 라이선스 및 그룹 관리</span><span class="sxs-lookup"><span data-stu-id="3a4aa-160">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="3a4aa-161">Office 365 PowerShell을 사용하여 Office 365 관리</span><span class="sxs-lookup"><span data-stu-id="3a4aa-161">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="3a4aa-162">Office 365 PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="3a4aa-162">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
