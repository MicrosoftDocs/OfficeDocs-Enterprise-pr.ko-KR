---
title: PowerShell을 사용 하 여 Microsoft 365 사용자 계정 만들기
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
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
- PowerShell
- Ent_Office_Other
- O365ITProTrain
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: Microsoft 365 용 PowerShell을 사용 하 여 사용자 계정을 만드는 방법을 알아봅니다.
ms.openlocfilehash: 4057f4e1b29e8177bee32306c49f25f607ac5a0f
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230794"
---
# <a name="create-microsoft-365-user-accounts-with-powershell"></a><span data-ttu-id="9a2d5-103">PowerShell을 사용 하 여 Microsoft 365 사용자 계정 만들기</span><span class="sxs-lookup"><span data-stu-id="9a2d5-103">Create Microsoft 365 user accounts with PowerShell</span></span>

<span data-ttu-id="9a2d5-104">*이 문서는 Microsoft 365 Enterprise 및 Office 365 Enterprise에 모두 적용 됩니다.*</span><span class="sxs-lookup"><span data-stu-id="9a2d5-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="9a2d5-105">Microsoft 365 용 PowerShell을 사용 하 여 사용자 계정, 특히 여러 사용자 계정을 효율적으로 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a2d5-105">You can use PowerShell for Microsoft 365 to efficiently create user accounts, especially multiple user accounts.</span></span> <span data-ttu-id="9a2d5-106">PowerShell에서 사용자 계정을 만드는 경우에는 특정 계정 속성이 항상 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="9a2d5-106">When you create user accounts in PowerShell, certain account properties are always required.</span></span> <span data-ttu-id="9a2d5-107">다른 속성의 계정을 만들 필요는 없습니다 그렇지 않을 경우 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="9a2d5-107">Other properties aren't required to create the account, but are otherwise important.</span></span> <span data-ttu-id="9a2d5-108">다음 표에서는 이러한 속성에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="9a2d5-108">These properties are described in the following table:</span></span>
  
|<span data-ttu-id="9a2d5-109">**속성 이름**</span><span class="sxs-lookup"><span data-stu-id="9a2d5-109">**Property name**</span></span>|<span data-ttu-id="9a2d5-110">**필수 여부**</span><span class="sxs-lookup"><span data-stu-id="9a2d5-110">**Required?**</span></span>|<span data-ttu-id="9a2d5-111">**설명**</span><span class="sxs-lookup"><span data-stu-id="9a2d5-111">**Description**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="9a2d5-112">**DisplayName**</span><span class="sxs-lookup"><span data-stu-id="9a2d5-112">**DisplayName**</span></span> <br/> |<span data-ttu-id="9a2d5-113">예</span><span class="sxs-lookup"><span data-stu-id="9a2d5-113">Yes</span></span>  <br/> |<span data-ttu-id="9a2d5-114">Microsoft 365 서비스에서 사용 되는 표시 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="9a2d5-114">This is the display name that's used in Microsoft 365 services.</span></span> <span data-ttu-id="9a2d5-115">예를 들어, Caleb 창턱</span><span class="sxs-lookup"><span data-stu-id="9a2d5-115">For example, Caleb Sills.</span></span>  <br/> |
|<span data-ttu-id="9a2d5-116">**UserPrincipalName**</span><span class="sxs-lookup"><span data-stu-id="9a2d5-116">**UserPrincipalName**</span></span> <br/> |<span data-ttu-id="9a2d5-117">예</span><span class="sxs-lookup"><span data-stu-id="9a2d5-117">Yes</span></span>  <br/> |<span data-ttu-id="9a2d5-118">Microsoft 365 서비스에 로그인 하는 데 사용 되는 계정 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="9a2d5-118">This is the account name that's used to sign in to Microsoft 365 services.</span></span> <span data-ttu-id="9a2d5-119">For example, CalebS@contoso.onmicrosoft.com.</span><span class="sxs-lookup"><span data-stu-id="9a2d5-119">For example, CalebS@contoso.onmicrosoft.com.</span></span>  <br/> |
|<span data-ttu-id="9a2d5-120">**FirstName**</span><span class="sxs-lookup"><span data-stu-id="9a2d5-120">**FirstName**</span></span> <br/> |<span data-ttu-id="9a2d5-121">아니요</span><span class="sxs-lookup"><span data-stu-id="9a2d5-121">No</span></span>  <br/> ||
|<span data-ttu-id="9a2d5-122">**LastName**</span><span class="sxs-lookup"><span data-stu-id="9a2d5-122">**LastName**</span></span> <br/> |<span data-ttu-id="9a2d5-123">아니요</span><span class="sxs-lookup"><span data-stu-id="9a2d5-123">No</span></span>  <br/> ||
|<span data-ttu-id="9a2d5-124">**LicenseAssignment**</span><span class="sxs-lookup"><span data-stu-id="9a2d5-124">**LicenseAssignment**</span></span> <br/> |<span data-ttu-id="9a2d5-125">아니요</span><span class="sxs-lookup"><span data-stu-id="9a2d5-125">No</span></span>  <br/> |<span data-ttu-id="9a2d5-126">사용 가능한 라이선스가 사용자 계정에 할당 되는 라이선스 계획 (라이선스 요금제 또는 SKU 라고도 함)입니다.</span><span class="sxs-lookup"><span data-stu-id="9a2d5-126">This is the licensing plan (also known as the license plan or SKU) from which an available license is assigned to the user account.</span></span> <span data-ttu-id="9a2d5-127">라이선스는 계정에 사용할 수 있는 Microsoft 365 서비스를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="9a2d5-127">The license defines the Microsoft 365 services that are available to account.</span></span> <span data-ttu-id="9a2d5-128">계정을 만들 때 사용자에 게 라이선스를 할당할 필요가 없지만 계정에 Microsoft 365 서비스에 액세스 하기 위한 라이선스가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="9a2d5-128">You don't have to assign a license to a user when you create the account, but the account requires a license to access Microsoft 365 services.</span></span> <span data-ttu-id="9a2d5-129">30 일 내에 사용자 계정을 만든 후 라이선스를 허가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9a2d5-129">You have 30 days to license the user account after you create it.</span></span> |
|<span data-ttu-id="9a2d5-130">**Password**</span><span class="sxs-lookup"><span data-stu-id="9a2d5-130">**Password**</span></span> <br/> |<span data-ttu-id="9a2d5-131">아니요</span><span class="sxs-lookup"><span data-stu-id="9a2d5-131">No</span></span>  <br/> | <span data-ttu-id="9a2d5-p105">암호를 지정하지 않으면 사용자 계정에 임의의 암호가 할당되고, 명령 결과에 암호가 표시됩니다. 암호를 지정할 때에는 소문자, 대문자, 숫자, 기호 중 3가지가 포함된 길이 8 ~ 16의 ASCII 문자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9a2d5-p105">If you don't specify a password, a random password is assigned to the user account, and the password is visible in the results of the command. If you specify a password, it needs to be 8 to 16 ASCII text characters from any three of the following types: lowercase letters, uppercase letters, numbers, and symbols.</span></span> <br/> |
|<span data-ttu-id="9a2d5-134">**UsageLocation**</span><span class="sxs-lookup"><span data-stu-id="9a2d5-134">**UsageLocation**</span></span> <br/> |<span data-ttu-id="9a2d5-135">아니요</span><span class="sxs-lookup"><span data-stu-id="9a2d5-135">No</span></span>  <br/> |<span data-ttu-id="9a2d5-136">유효한 ISO 3166-1 alpha-2 국가 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="9a2d5-136">This is a valid ISO 3166-1 alpha-2 country code.</span></span> <span data-ttu-id="9a2d5-137">예를 들어 미국, 프랑스의 경우 FR을 들을 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a2d5-137">For example, US for the United States, and FR for France.</span></span> <span data-ttu-id="9a2d5-138">일부 Microsoft 365 서비스는 특정 국가에서 사용할 수 없기 때문에이 값을 제공 하는 것이 중요 하므로, 계정에이 값이 구성 되어 있지 않으면 사용자 계정에 라이선스를 할당할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9a2d5-138">It's important to provide this value, because some Microsoft 365 services aren't available in certain countries, so you can't assign a license to a user account unless the account has this value configured.</span></span> <span data-ttu-id="9a2d5-139">자세한 내용은 [사용권 제한 정보](https://go.microsoft.com/fwlink/p/?LinkId=691730)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9a2d5-139">For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span></span>  <br/> |
   

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="9a2d5-140">Graph 모듈용 Azure Active Directory PowerShell 사용하기</span><span class="sxs-lookup"><span data-stu-id="9a2d5-140">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="9a2d5-141">먼저 [Microsoft 365 테 넌 트에 연결](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)합니다.</span><span class="sxs-lookup"><span data-stu-id="9a2d5-141">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>

<span data-ttu-id="9a2d5-142">연결한 후 다음 구문을 사용하여 개별 계정을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9a2d5-142">After you have connected, use the following syntax to create an individual account:</span></span>
  
```powershell
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="<user account password>"
New-AzureADUser -DisplayName "<display name>" -GivenName "<first name>" -SurName "<last name>" -UserPrincipalName <sign-in name> -UsageLocation <ISO 3166-1 alpha-2 country code> -MailNickName <mailbox name> -PasswordProfile $PasswordProfile -AccountEnabled $true
```

<span data-ttu-id="9a2d5-143">이 예제에서는 Caleb Sills라는 미국 사용자의 계정을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9a2d5-143">This example creates an account for the United States user named Caleb Sills:</span></span>
  
```powershell
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="3Rv0y1q39/chsy"
New-AzureADUser -DisplayName "Caleb Sills" -GivenName "Caleb" -SurName "Sills" -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -MailNickName calebs -PasswordProfile $PasswordProfile -AccountEnabled $true
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="9a2d5-144">Windows PowerShell용 Microsoft Azure Active Directory 모듈 사용하기</span><span class="sxs-lookup"><span data-stu-id="9a2d5-144">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="9a2d5-145">먼저 [Microsoft 365 테 넌 트에 연결](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)합니다.</span><span class="sxs-lookup"><span data-stu-id="9a2d5-145">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

### <a name="create-an-individual-user-account"></a><span data-ttu-id="9a2d5-146">개별 사용자 계정 만들기</span><span class="sxs-lookup"><span data-stu-id="9a2d5-146">Create an individual user account</span></span>

<span data-ttu-id="9a2d5-147">개별 계정을 만들려면 다음 구문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9a2d5-147">To create an individual account, use the following syntax:</span></span>
  
```powershell
New-MsolUser -DisplayName <display name> -FirstName <first name> -LastName <last name> -UserPrincipalName <sign-in name> -UsageLocation <ISO 3166-1 alpha-2 country code> -LicenseAssignment <licensing plan name> [-Password <Password>]
```

>[!Note]
><span data-ttu-id="9a2d5-148">PowerShell Core는 Windows PowerShell용 Microsoft Azure Active Directory 모듈 및 이름에 **Msol**이 있는 cmdlet을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9a2d5-148">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="9a2d5-149">이러한 cmdlet을 계속 사용하려면 Windows PowerShell에서 이를 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9a2d5-149">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="9a2d5-150">사용 가능한 라이선스 계획 이름을 열거하려면 이 명령을  사용합니다:</span><span class="sxs-lookup"><span data-stu-id="9a2d5-150">To list the available licensing plan names, use this command:</span></span>

````powershell
Get-MsolAccountSku
````

<span data-ttu-id="9a2d5-151">이 예제에서는 Caleb Sills라는 미국 사용자의 계정을 만들고, `contoso:ENTERPRISEPACK`(Office 365 Enterprise E3) 라이선스 계획에서 라이선스를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="9a2d5-151">This example creates an account for the United States user named Caleb Sills, and assigns a license from the `contoso:ENTERPRISEPACK` (Office 365 Enterprise E3) licensing plan.</span></span>
  
```powershell
New-MsolUser -DisplayName "Caleb Sills" -FirstName Caleb -LastName Sills -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -LicenseAssignment contoso:ENTERPRISEPACK
```

### <a name="create-multiple-user-accounts"></a><span data-ttu-id="9a2d5-152">다중 사용자 계정 만들기</span><span class="sxs-lookup"><span data-stu-id="9a2d5-152">Create multiple user accounts</span></span>

1. <span data-ttu-id="9a2d5-p108">필요한 사용자 계정 정보를 포함하는 쉼표로 구분 된 값(CSV) 파일을 만듭니다. 예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9a2d5-p108">Create a comma-separated value (CSV) file that contains the required user account information. For example:</span></span>
    
  ```powershell
  UserPrincipalName,FirstName,LastName,DisplayName,UsageLocation,AccountSkuId
  ClaudeL@contoso.onmicrosoft.com,Claude,Loiselle,Claude Loiselle,US,contoso:ENTERPRISEPACK
  LynneB@contoso.onmicrosoft.com,Lynne,Baxter,Lynne Baxter,US,contoso:ENTERPRISEPACK
  ShawnM@contoso.onmicrosoft.com,Shawn,Melendez,Shawn Melendez,US,contoso:ENTERPRISEPACK
  ```

 > [!NOTE]
><span data-ttu-id="9a2d5-155">CSV 파일의 첫 번째 행에 있는 열 이름과 해당 순서는 임의적 이지만 파일의 나머지 부분에 있는 데이터가 열 이름의 순서와 일치 하는지 확인 하 고 365 Microsoft for a PowerShell 명령에서 매개 변수 값에 대 한 열 이름을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9a2d5-155">The column names and their order in the first row of the CSV file are arbitrary, but make sure the data in the rest of the file matches the order of the column names, and use the column names for the parameter values in the PowerShell for Microsoft 365 command.</span></span>
    
2. <span data-ttu-id="9a2d5-156">다음 구문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9a2d5-156">Use the following syntax:</span></span>
    
  ```powershell
  Import-Csv -Path <Input CSV File Path and Name> | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId [-Password $_.Password]} | Export-Csv -Path <Output CSV File Path and Name>
  ```

<span data-ttu-id="9a2d5-157">이 예제는 C:\My Documents\NewAccounts.csv 라는 파일에서 사용자 계정을 만들고 C:\My Documents\NewAccountResults.csv 라는 파일에 결과를 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="9a2d5-157">This example creates the user accounts from the file named C:\My Documents\NewAccounts.csv, and logs the results in the file named C:\My Documents\NewAccountResults.csv</span></span>
    
  ```powershell
  Import-Csv -Path "C:\My Documents\NewAccounts.csv" | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId} | Export-Csv -Path "C:\My Documents\NewAccountResults.csv"
  ```

3. <span data-ttu-id="9a2d5-158">결과 볼 수 있는 출력 파일을 검토 합니다.</span><span class="sxs-lookup"><span data-stu-id="9a2d5-158">Review the output file to see the results.</span></span> <span data-ttu-id="9a2d5-159">암호를 지정 하지 않았으므로 Microsoft 365이 생성 하는 임의의 암호가 출력 파일에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9a2d5-159">We didn't specify passwords, so the random passwords that Microsoft 365 generated are visible in the output file.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="9a2d5-160">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9a2d5-160">See also</span></span>

[<span data-ttu-id="9a2d5-161">PowerShell을 사용 하 여 Microsoft 365 사용자 계정, 라이선스 및 그룹 관리</span><span class="sxs-lookup"><span data-stu-id="9a2d5-161">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="9a2d5-162">PowerShell을 사용 하 여 Microsoft 365 관리</span><span class="sxs-lookup"><span data-stu-id="9a2d5-162">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="9a2d5-163">Microsoft 365 용 PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="9a2d5-163">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)
