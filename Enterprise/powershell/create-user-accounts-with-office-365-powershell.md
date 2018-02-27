---
title: "Office 365 PowerShell을 사용 하 여 사용자 계정 만들기"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: PowerShell, Ent_Office_Other, O365ITProTrain
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: "사용 하는 방법은 Office 365 PowerShell 에 대 한 사용자 계정을 만드는 Office 365."
ms.openlocfilehash: 58c4f6b1d75bb8b77cbf6616b8036dd753ddc3f3
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/13/2018
---
# <a name="create-user-accounts-with-office-365-powershell"></a><span data-ttu-id="234aa-103">Office 365 PowerShell을 사용 하 여 사용자 계정 만들기</span><span class="sxs-lookup"><span data-stu-id="234aa-103">Create user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="234aa-104">**요약:** Office 365에서 Office 365 PowerShell을 사용하여 사용자 계정을 만드는 방법을 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="234aa-104">**Summary:** Learn how to use Office 365 PowerShell to create user accounts in Office 365.</span></span>
  
<span data-ttu-id="234aa-p101">사용할 수 있습니다 Office 365 PowerShell 효과적으로 사용자 계정, 특히 여러 사용자 계정을 만들 수 있습니다. 사용자 계정을 만들 때 Office 365 PowerShell, 특정 계정 속성은 항상 필요 합니다. 다른 속성의 계정을 만들 필요는 없습니다 그렇지 않을 경우 중요 합니다. 다음 표에서 이러한 제한에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="234aa-p101">You can use Office 365 PowerShell to efficiently create user accounts, especially multiple user accounts. When you create user accounts in Office 365 PowerShell, certain account properties are always required. Other properties aren't required to create the account, but are otherwise important. These properties are described in the following table:</span></span>
  
****

|<span data-ttu-id="234aa-109">**속성 이름**</span><span class="sxs-lookup"><span data-stu-id="234aa-109">**Property name**</span></span>|<span data-ttu-id="234aa-110">**필수 여부**</span><span class="sxs-lookup"><span data-stu-id="234aa-110">**Required?**</span></span>|<span data-ttu-id="234aa-111">**설명**</span><span class="sxs-lookup"><span data-stu-id="234aa-111">**Description**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="234aa-112">**DisplayName**</span><span class="sxs-lookup"><span data-stu-id="234aa-112">**DisplayName**</span></span> <br/> |<span data-ttu-id="234aa-113">예</span><span class="sxs-lookup"><span data-stu-id="234aa-113">Yes</span></span>  <br/> |<span data-ttu-id="234aa-p102">Office 365 서비스에서 사용되는 표시 이름입니다. 예: Caleb Sills</span><span class="sxs-lookup"><span data-stu-id="234aa-p102">This is the display name that's used in Office 365 services. For example, Caleb Sills.</span></span>  <br/> |
|<span data-ttu-id="234aa-116">**UserPrincipalName**</span><span class="sxs-lookup"><span data-stu-id="234aa-116">**UserPrincipalName**</span></span> <br/> |<span data-ttu-id="234aa-117">예</span><span class="sxs-lookup"><span data-stu-id="234aa-117">Yes</span></span>  <br/> |<span data-ttu-id="234aa-p103">Office 365 서비스에 로그인하는 데 사용되는 계정 이름입니다. 예: CalebS@contoso.onmicrosoft.com.</span><span class="sxs-lookup"><span data-stu-id="234aa-p103">This is the account name that's used to sign in to Office 365 services. For example, CalebS@contoso.onmicrosoft.com.</span></span>  <br/> |
|<span data-ttu-id="234aa-120">**FirstName**</span><span class="sxs-lookup"><span data-stu-id="234aa-120">**FirstName**</span></span> <br/> |<span data-ttu-id="234aa-121">아니요</span><span class="sxs-lookup"><span data-stu-id="234aa-121">No</span></span>  <br/> ||
|<span data-ttu-id="234aa-122">**LastName**</span><span class="sxs-lookup"><span data-stu-id="234aa-122">**LastName**</span></span> <br/> |<span data-ttu-id="234aa-123">아니요</span><span class="sxs-lookup"><span data-stu-id="234aa-123">No</span></span>  <br/> ||
|<span data-ttu-id="234aa-124">**LicenseAssignment**</span><span class="sxs-lookup"><span data-stu-id="234aa-124">**LicenseAssignment**</span></span> <br/> |<span data-ttu-id="234aa-125">아니요</span><span class="sxs-lookup"><span data-stu-id="234aa-125">No</span></span>  <br/> |<span data-ttu-id="234aa-p104">사용 가능한 라이선스가 사용자 계정에 할당되는 라이선싱 계획(라이선스 계획, Office 365 계획 또는 SKU라고도 함)입니다. 라이선스는 계정에서 사용할 수 있는 Office 365 서비스를 정의합니다. 계정을 만들 때 사용자에게 라이선스를 할당할 필요는 없지만 계정이 Office 365 서비스에 액세스하려면 라이선스가 필요합니다. 만든 후에 사용자 계정에 30일 간의 라이선스가 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="234aa-p104">This is the licensing plan (also known as the license plan, Office 365 plan, or SKU) from which an available license is assigned to the user account. The license defines the Office 365 services that are available to account. You don't have to assign a license to a user when you create the account, but the account requires a license to access Office 365 services. You have 30 days to license the user account after you create it.  </span></span><br/> <span data-ttu-id="234aa-p105">**Get-MsolAccountSku** cmdlet을 사용하여 조직의 라이선싱 계획(**AccountSkuId**) 및 사용할 수 있는 라이선스를 확인할 수 있습니다. 자세한 내용은 [Office 365 PowerShell을 통해 라이선스 및 서비스 확인](view-licenses-and-services-with-office-365-powershell.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="234aa-p105">Use the **Get-MsolAccountSku** cmdlet to view the licensing plans ( **AccountSkuId** ) and available licenses in your organization. For more information, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).  </span></span><br/> |
|<span data-ttu-id="234aa-132">**Password**</span><span class="sxs-lookup"><span data-stu-id="234aa-132">**Password**</span></span> <br/> |<span data-ttu-id="234aa-133">아니요</span><span class="sxs-lookup"><span data-stu-id="234aa-133">No</span></span>  <br/> | <span data-ttu-id="234aa-p106">암호를 지정하지 않으면 사용자 계정에 임의 암호가 할당되고 명령 결과에 암호가 표시됩니다. 암호를 지정하는 경우 다음과 같은 복잡성 요구 사항을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="234aa-p106">If you don't specify a password, a random password is assigned to the user account, and the password is visible in the results of the command. If you specify a password, it needs to meet the following complexity requirements:</span></span> <br/>  <span data-ttu-id="234aa-136">8에서 16 ASCII 텍스트 문자입니다.</span><span class="sxs-lookup"><span data-stu-id="234aa-136">8 to 16 ASCII text characters.</span></span> <br/>  <span data-ttu-id="234aa-137">다음과 같은 종류의 모든 3 문자: 소문자, 대문자, 숫자 및 기호입니다.</span><span class="sxs-lookup"><span data-stu-id="234aa-137">Characters from any three of the following types: lowercase letters, uppercase letters, numbers, and symbols.</span></span> <br/> |
|<span data-ttu-id="234aa-138">**UsageLocation**</span><span class="sxs-lookup"><span data-stu-id="234aa-138">**UsageLocation**</span></span> <br/> |<span data-ttu-id="234aa-139">아니요</span><span class="sxs-lookup"><span data-stu-id="234aa-139">No</span></span>  <br/> |<span data-ttu-id="234aa-p107">유효한 ISO 3166-1 alpha-2 국가 코드입니다. 예를 들어 미국은 US, 프랑스는 FR입니다. 특정 국가에서는 일부 Office 365 서비스를 사용할 수 없으므로 이 값을 제공하는 것이 중요합니다. 따라서 계정에 이 값이 구성되어 있지 않으면 사용자 계정에 라이선스를 할당할 수 없습니다. 자세한 내용은 [라이센스 제한 정보](https://go.microsoft.com/fwlink/p/?LinkId=691730)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="234aa-p107">This is a valid ISO 3166-1 alpha-2 country code. For example, US for the United States, and FR for France. It's important to provide this value, because some Office 365 services aren't available in certain countries, so you can't assign a license to a user account unless the account has this value configured. For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).  </span></span><br/> |
   
## <a name="before-you-begin"></a><span data-ttu-id="234aa-144">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="234aa-144">Before you begin</span></span>

<span data-ttu-id="234aa-p108">이 항목의 절차를 수행하려면 Office 365 PowerShell에 연결되어 있어야 합니다. 지침을 보려면 [PowerShell Office 365에 연결](connect-to-office-365-powershell.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="234aa-p108">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
## <a name="use-office-365-powershell-to-create-individual-user-accounts"></a><span data-ttu-id="234aa-147">Office 365 PowerShell을 사용하여 개별 사용자 계정 만들기</span><span class="sxs-lookup"><span data-stu-id="234aa-147">Use Office 365 PowerShell to create individual user accounts</span></span>

<span data-ttu-id="234aa-148">개별 계정을 만들려면 다음 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="234aa-148">To create an individual account, use the following syntax:</span></span>
  
```
New-MsolUser -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -UserPrincipalName <Account> -UsageLocation <CountryCode> -LicenseAssignment <AccountSkuID> [-Password <Password>]
```

<span data-ttu-id="234aa-149">로부터 라이센스를 할당 하는이 예제 Caleb 창턱 이라는 미국 사용자에 대 한 계정을 만들고는  `contoso:ENTERPRISEPACK` (Office 365 Enterprise E3) 라이센스 제도.</span><span class="sxs-lookup"><span data-stu-id="234aa-149">This example creates an account for the United States user named Caleb Sills, and assigns a license from the  `contoso:ENTERPRISEPACK` (Office 365 Enterprise E3) licensing plan.</span></span>
  
```
New-MsolUser -DisplayName "Caleb Sills" -FirstName Caleb -LastName Sills -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -LicenseAssignment contoso:ENTERPRISEPACK
```

## <a name="use-office-365-powershell-to-create-multiple-user-accounts"></a><span data-ttu-id="234aa-150">사용 하 여 Office 365 PowerShell 여러 사용자 계정을 만들려면</span><span class="sxs-lookup"><span data-stu-id="234aa-150">Use Office 365 PowerShell to create multiple user accounts</span></span>

1. <span data-ttu-id="234aa-p109">필요한 사용자 계정 정보를 포함 하는 쉼표로 구분 된 값 (CSV) 파일을 만듭니다. 예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="234aa-p109">Create a comma-separated value (CSV) file that contains the required user account information. For example:</span></span>
    
  ```
  UserPrincipalName,FirstName,LastName,DisplayName,UsageLocation,AccountSkuId
ClaudeL@contoso.onmicrosoft.com,Claude,Loiselle,Claude Loiselle,US,contoso:ENTERPRISEPACK
LynneB@contoso.onmicrosoft.com,Lynne,Baxter,Lynne Baxter,US,contoso:ENTERPRISEPACK
ShawnM@contoso.onmicrosoft.com,Shawn,Melendez,Shawn Melendez,US,contoso:ENTERPRISEPACK
  ```

 > [!NOTE]
><span data-ttu-id="234aa-153">CSV 파일의 첫 번째 행에서 열 이름 및 순서는 무작위지만 나머지 파일의 데이터는 열 이름의 순서와 일치하는지 확인하고 Office 365 PowerShell 명령에서 매개 변수 값의 열 이름을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="234aa-153">The column names and their order in the first row of the CSV file are arbitrary, but make sure the data in the rest of the file matches the order of the column names, and use the column names for the parameter values in the Office 365 PowerShell command.</span></span>
    
2. <span data-ttu-id="234aa-154">다음 구문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="234aa-154">Use the following syntax:</span></span>
    
  ```
  Import-Csv -Path <Input CSV File Path and Name> | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId [-Password $_.Password]} | Export-Csv -Path <Output CSV File Path and Name>
  ```

<span data-ttu-id="234aa-155">이 이때는 C:\My Documents\NewAccounts.csv 라는 파일에서 사용자 계정을 만들고 C:\My Documents\NewAccountResults.csv 라는 파일에 결과 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="234aa-155">This example creates the user accounts from the file named C:\My Documents\NewAccounts.csv, and logs the results in the file named C:\My Documents\NewAccountResults.csv</span></span>
    
  ```
  Import-Csv -Path "C:\My Documents\NewAccounts.csv" | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId} | Export-Csv -Path "C:\My Documents\NewAccountResults.csv"
  ```

3. <span data-ttu-id="234aa-p110">출력 파일을 검토하여 결과를 확인합니다. 암호를 지정하지 않았으므로 생성된 임의 암호가 출력 파일에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="234aa-p110">Review the output file to see the results. We didn't specify passwords, so the random passwords that were generated are visible in the output file.</span></span>
    
## <a name="use-the-azure-active-directory-v2-powershell-module-to-create-individual-user-accounts"></a><span data-ttu-id="234aa-158">Azure Active Directory V2 PowerShell 모듈을 사용하여 개별 사용자 계정 만들기</span><span class="sxs-lookup"><span data-stu-id="234aa-158">Use the Azure Active Directory V2 PowerShell module to create individual user accounts</span></span>

<span data-ttu-id="234aa-p111">Azure Active Directory V2 PowerShell 모듈에서 **New-AzureADUser** cmdlet을 사용하려면 먼저 구독에 연결해야 합니다. 지침은[Azure Active Directory V2 PowerShell 모듈을 사용하여 연결](https://go.microsoft.com/fwlink/?linkid=842218)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="234aa-p111">To use the **New-AzureADUser** cmdlet from the Azure Active Directory V2 PowerShell module, you must first connect to your subscription. For the instructions, see [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
<span data-ttu-id="234aa-161">연결한 후 다음 구문을 사용하여 개별 계정을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="234aa-161">After you have connected, use the following syntax to create an individual account:</span></span>
  
```
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="<user account password>"
New-AzureADUser -DisplayName <DisplayName> -GivenName <FirstName> -SurName <LastName> -UserPrincipalName <Account> -UsageLocation <CountryCode> -MailNickName <mailbox name> -PasswordProfile $PasswordProfile -AccountEnabled $true
```

<span data-ttu-id="234aa-162">이 예제에서는 Caleb Sills라는 미국 사용자의 계정을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="234aa-162">This example creates an account for the United States user named Caleb Sills:</span></span>
  
```
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="3Rv0y1q39/chsy"
New-AzureADUser -DisplayName "Caleb Sills" -GivenName "Caleb" -SurName "Sills" -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -MailNickName calebs -PasswordProfile $PasswordProfile -AccountEnabled $true
```
  
## <a name="see-also"></a><span data-ttu-id="234aa-163">참고 항목</span><span class="sxs-lookup"><span data-stu-id="234aa-163">See also</span></span>

<span data-ttu-id="234aa-164">Office 365 PowerShell을 사용하여 사용자를 관리하는 방법에 대한 다음 추가 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="234aa-164">See these additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="234aa-165">Office 365 PowerShell을 사용하여 사용자 계정 삭제 및 복원</span><span class="sxs-lookup"><span data-stu-id="234aa-165">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="234aa-166">블록 사용자 계정 Office 365 PowerShell을 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="234aa-166">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="234aa-167">Office 365 PowerShell을 사용 하 여 사용자 계정에 라이선스를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="234aa-167">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="234aa-168">Office 365 PowerShell을 사용 하 여 사용자 계정에서 라이센스를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="234aa-168">Remove licenses from user accounts with Office 365 PowerShell</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="234aa-169">이 항목에서 사용된 cmdlet에 대한 자세한 내용은 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="234aa-169">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="234aa-170">Csv 내보내기</span><span class="sxs-lookup"><span data-stu-id="234aa-170">Export-Csv</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113299)
    
- [<span data-ttu-id="234aa-171">Import-Csv</span><span class="sxs-lookup"><span data-stu-id="234aa-171">Import-Csv</span></span>](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/import-csv)
    
- [<span data-ttu-id="234aa-172">New-MsolUser</span><span class="sxs-lookup"><span data-stu-id="234aa-172">New-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [<span data-ttu-id="234aa-173">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="234aa-173">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="234aa-174">New-AzureADUser</span><span class="sxs-lookup"><span data-stu-id="234aa-174">New-AzureADUser</span></span>](https://docs.microsoft.com/powershell/module/azuread/new-azureaduser?view=azureadps-2.0)
    

