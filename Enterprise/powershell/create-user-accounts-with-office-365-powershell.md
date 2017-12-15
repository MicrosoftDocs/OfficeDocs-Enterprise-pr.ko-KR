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
ms.custom:
- PowerShell
- apr17entnews
- Ent_Office_Other
- DecEntMigration
- O365ITProTrain
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: "Office 365에서 사용자 계정을 만들려면 Office 365 PowerShell을 사용 하는 방법에 알아봅니다."
ms.openlocfilehash: 9f6eb4cafa82ae511e806b7e32f2ed98a065d52e
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2017
---
# <a name="create-user-accounts-with-office-365-powershell"></a><span data-ttu-id="c4b8d-103">Office 365 PowerShell을 사용 하 여 사용자 계정 만들기</span><span class="sxs-lookup"><span data-stu-id="c4b8d-103">Create user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="c4b8d-104">**요약:** Office 365에서 사용자 계정을 만들려면 Office 365 PowerShell을 사용 하는 방법에 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="c4b8d-104">**Summary:** Learn how to use Office 365 PowerShell to create user accounts in Office 365.</span></span>
  
<span data-ttu-id="c4b8d-p101">Office 365 PowerShell 효율적으로 사용자 계정을 만들려면, 특히 여러 사용자 계정을 사용할 수 있습니다. Office 365 PowerShell에서 사용자 계정을 만들면 특정 계정 속성이 항상 필수인 합니다. 다른 속성은 계정을 만들 필요가 없다고 이지만 중요 한 그렇지 않은 경우. 다음 표에에서는 이러한 속성에 대 한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="c4b8d-p101">You can use Office 365 PowerShell to efficiently create user accounts, especially multiple user accounts. When you create user accounts in Office 365 PowerShell, certain account properties are always required. Other properties aren't required to create the account, but are otherwise important. These properties are described in the following table:</span></span>
  
****

|<span data-ttu-id="c4b8d-109">**속성 이름**</span><span class="sxs-lookup"><span data-stu-id="c4b8d-109">**Property name**</span></span>|<span data-ttu-id="c4b8d-110">**필수?**</span><span class="sxs-lookup"><span data-stu-id="c4b8d-110">**Required?**</span></span>|<span data-ttu-id="c4b8d-111">**설명**</span><span class="sxs-lookup"><span data-stu-id="c4b8d-111">**Description**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="c4b8d-112">**DisplayName**</span><span class="sxs-lookup"><span data-stu-id="c4b8d-112">**DisplayName**</span></span> <br/> |<span data-ttu-id="c4b8d-113">예</span><span class="sxs-lookup"><span data-stu-id="c4b8d-113">Yes</span></span>  <br/> |<span data-ttu-id="c4b8d-p102">Office 365 서비스에서 사용 되는 표시 이름입니다. 예를들어 Caleb Sills 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4b8d-p102">This is the display name that's used in Office 365 services. For example, Caleb Sills.</span></span>  <br/> |
|<span data-ttu-id="c4b8d-116">**UserPrincipalName**</span><span class="sxs-lookup"><span data-stu-id="c4b8d-116">**UserPrincipalName**</span></span> <br/> |<span data-ttu-id="c4b8d-117">예</span><span class="sxs-lookup"><span data-stu-id="c4b8d-117">Yes</span></span>  <br/> |<span data-ttu-id="c4b8d-p103">Office 365 서비스에 로그인 하는데 사용 되는 계정 이름입니다. 예: CalebS@contoso.onmicrosoft.com 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4b8d-p103">This is the account name that's used to sign in to Office 365 services. For example, CalebS@contoso.onmicrosoft.com.</span></span>  <br/> |
|<span data-ttu-id="c4b8d-120">**FirstName**</span><span class="sxs-lookup"><span data-stu-id="c4b8d-120">**FirstName**</span></span> <br/> |<span data-ttu-id="c4b8d-121">아니요</span><span class="sxs-lookup"><span data-stu-id="c4b8d-121">No</span></span>  <br/> ||
|<span data-ttu-id="c4b8d-122">**LastName**</span><span class="sxs-lookup"><span data-stu-id="c4b8d-122">**LastName**</span></span> <br/> |<span data-ttu-id="c4b8d-123">아니요</span><span class="sxs-lookup"><span data-stu-id="c4b8d-123">No</span></span>  <br/> ||
|<span data-ttu-id="c4b8d-124">**LicenseAssignment**</span><span class="sxs-lookup"><span data-stu-id="c4b8d-124">**LicenseAssignment**</span></span> <br/> |<span data-ttu-id="c4b8d-125">아니요</span><span class="sxs-lookup"><span data-stu-id="c4b8d-125">No</span></span>  <br/> |<span data-ttu-id="c4b8d-p104">사용자 계정에 할당 된 라이선스를 사용할 수 있는 라이선스 계획 (로 알려져: 라이선스 계획, Office 365 계획 또는 SKU)입니다. 이 라이선스 계정에 사용할 수 있는 Office 365 서비스를 정의 합니다. 계정에는 Office 365 서비스에 액세스 하는 라이선스가 필요 하지만 계정을 만들 경우 사용자에 게 라이선스를 할당할 필요가 없습니다. 사용자 계정을 만든 후에 30 일 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4b8d-p104">This is the licensing plan (also known as the license plan, Office 365 plan, or SKU) from which an available license is assigned to the user account. The license defines the Office 365 services that are available to account. You don't have to assign a license to a user when you create the account, but the account requires a license to access Office 365 services. You have 30 days to license the user account after you create it.  </span></span><br/> <span data-ttu-id="c4b8d-p105">**Get-msolaccountsku** cmdlet을 사용 하 여 조직에서 라이선스 계획 ( **AccountSkuId** ) 및 사용 가능한 라이선스를 볼 수 있습니다. 자세한 내용은 [보기 라이선스 및 Office 365 PowerShell을 사용 하 여 서비스를](view-licenses-and-services-with-office-365-powershell.md)참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="c4b8d-p105">Use the **Get-MsolAccountSku** cmdlet to view the licensing plans ( **AccountSkuId** ) and available licenses in your organization. For more information, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).  </span></span><br/> |
|<span data-ttu-id="c4b8d-132">**암호**</span><span class="sxs-lookup"><span data-stu-id="c4b8d-132">**Password**</span></span> <br/> |<span data-ttu-id="c4b8d-133">아니요</span><span class="sxs-lookup"><span data-stu-id="c4b8d-133">No</span></span>  <br/> | <span data-ttu-id="c4b8d-p106">암호를 지정 하지 않으면 사용자 계정에 임의의 암호를 할당 하 고 암호는 명령의 결과에 표시 됩니다. 암호를 지정 하면 다음과 같은 복잡성을 만족 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4b8d-p106">If you don't specify a password, a random password is assigned to the user account, and the password is visible in the results of the command. If you specify a password, it needs to meet the following complexity requirements:</span></span> <br/>  <span data-ttu-id="c4b8d-136">8에서 16 ASCII 텍스트 문자입니다.</span><span class="sxs-lookup"><span data-stu-id="c4b8d-136">8 to 16 ASCII text characters.</span></span> <br/>  <span data-ttu-id="c4b8d-137">다음과 같은 종류의 모든 3 문자: 소문자, 대문자, 숫자 및 기호입니다.</span><span class="sxs-lookup"><span data-stu-id="c4b8d-137">Characters from any three of the following types: lowercase letters, uppercase letters, numbers, and symbols.</span></span> <br/> |
|<span data-ttu-id="c4b8d-138">**Usagelocation이**</span><span class="sxs-lookup"><span data-stu-id="c4b8d-138">**UsageLocation**</span></span> <br/> |<span data-ttu-id="c4b8d-139">아니요</span><span class="sxs-lookup"><span data-stu-id="c4b8d-139">No</span></span>  <br/> |<span data-ttu-id="c4b8d-p107">유효한 ISO 3166-1 alpha-2 국가 코드입니다. 예: 대한민국, 미국, 대한민국 및 프랑스에 대 한 FR 합니다. 되므로이 값을 제공 하는 것이 중요 하므로 해당 계정에이 값을 구성 하지 않으면 사용자 계정에 라이선스를 할당할 수는 없습니다 일부 Office 365 서비스를 특정 국가에서 사용할 수 없습니다. 자세한 내용은 [라이선스 제한에 대 한](https://go.microsoft.com/fwlink/p/?LinkId=691730)참조입니다.</span><span class="sxs-lookup"><span data-stu-id="c4b8d-p107">This is a valid ISO 3166-1 alpha-2 country code. For example, US for the United States, and FR for France. It's important to provide this value, because some Office 365 services aren't available in certain countries, so you can't assign a license to a user account unless the account has this value configured. For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).  </span></span><br/> |
   
## <a name="before-you-begin"></a><span data-ttu-id="c4b8d-144">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="c4b8d-144">Before you begin</span></span>

<span data-ttu-id="c4b8d-p108">이 항목의 절차에서는 Office 365 PowerShell에 연결 해야 합니다. 자세한 내용은 [Office 365 PowerShell 연결](connect-to-office-365-powershell.md)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="c4b8d-p108">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
## <a name="use-office-365-powershell-to-create-individual-user-accounts"></a><span data-ttu-id="c4b8d-147">Office 365 PowerShell을 사용 하 여 개별 사용자 계정을 만들려면</span><span class="sxs-lookup"><span data-stu-id="c4b8d-147">Use Office 365 PowerShell to create individual user accounts</span></span>

<span data-ttu-id="c4b8d-148">개별 계정을 만들려면 다음 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4b8d-148">To create an individual account, use the following syntax:</span></span>
  
```
New-MsolUser -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -UserPrincipalName <Account> -UsageLocation <CountryCode> -LicenseAssignment <AccountSkuID> [-Password <Password>]
```

<span data-ttu-id="c4b8d-149">이 예제에서는 Caleb Sills 라는 미국 사용자에 대 한 계정을 만들고에서 라이선스를 할당은 `contoso:ENTERPRISEPACK` (Office 365 Enterprise E3) 라이선스 계획 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4b8d-149">This example creates an account for the United States user named Caleb Sills, and assigns a license from the  `contoso:ENTERPRISEPACK` (Office 365 Enterprise E3) licensing plan.</span></span>
  
```
New-MsolUser -DisplayName "Caleb Sills" -FirstName Caleb -LastName Sills -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -LicenseAssignment contoso:ENTERPRISEPACK
```

## <a name="use-office-365-powershell-to-create-multiple-user-accounts"></a><span data-ttu-id="c4b8d-150">Office 365 PowerShell을 사용 하 여 여러 사용자 계정을 만들려면</span><span class="sxs-lookup"><span data-stu-id="c4b8d-150">Use Office 365 PowerShell to create multiple user accounts</span></span>

1. <span data-ttu-id="c4b8d-p109">필요한 사용자 계정 정보를 포함 하는 쉼표로 구분 된 값 (CSV) 파일을 만듭니다. 예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c4b8d-p109">Create a comma-separated value (CSV) file that contains the required user account information. For example:</span></span>
    
  ```
  UserPrincipalName,FirstName,LastName,DisplayName,UsageLocation,AccountSkuId
ClaudeL@contoso.onmicrosoft.com,Claude,Loiselle,Claude Loiselle,US,contoso:ENTERPRISEPACK
LynneB@contoso.onmicrosoft.com,Lynne,Baxter,Lynne Baxter,US,contoso:ENTERPRISEPACK
ShawnM@contoso.onmicrosoft.com,Shawn,Melendez,Shawn Melendez,US,contoso:ENTERPRISEPACK
  ```

 > [!NOTE]
><span data-ttu-id="c4b8d-153">열 이름 및 CSV 파일의 행 1에 있는 순서는 임의의 하지만 파일의 나머지 부분에서 데이터 열 이름의 순서 일치 하는지 확인 하 고 Office 365 PowerShell 명령에서 매개 변수 값에 대 한 열 이름을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4b8d-153">The column names and their order in the first row of the CSV file are arbitrary, but make sure the data in the rest of the file matches the order of the column names, and use the column names for the parameter values in the Office 365 PowerShell command.</span></span>
    
2. <span data-ttu-id="c4b8d-154">다음 구문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c4b8d-154">Use the following syntax:</span></span>
    
  ```
  Import-Csv -Path <Input CSV File Path and Name> | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId [-Password $_.Password]} | Export-Csv -Path <Output CSV File Path and Name>
  ```

<span data-ttu-id="c4b8d-155">이 이때는 C:\My Documents\NewAccounts.csv 라는 파일에서 사용자 계정을 만들고 C:\My Documents\NewAccountResults.csv 라는 파일에 결과 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4b8d-155">This example creates the user accounts from the file named C:\My Documents\NewAccounts.csv, and logs the results in the file named C:\My Documents\NewAccountResults.csv</span></span>
    
  ```
  Import-Csv -Path "C:\My Documents\NewAccounts.csv" | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId} | Export-Csv -Path "C:\My Documents\NewAccountResults.csv"
  ```

3. <span data-ttu-id="c4b8d-p110">결과 볼 수 있는 출력 파일을 검토 합니다. 임의의 암호 생성 된 출력 파일에 표시 되므로 암호를 지정 하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="c4b8d-p110">Review the output file to see the results. We didn't specify passwords, so the random passwords that were generated are visible in the output file.</span></span>
    
## <a name="use-the-azure-active-directory-v2-powershell-module-to-create-individual-user-accounts"></a><span data-ttu-id="c4b8d-158">Azure Active Directory V2 PowerShell 모듈을 사용하여 개별 사용자 계정 만들기</span><span class="sxs-lookup"><span data-stu-id="c4b8d-158">Use the Azure Active Directory V2 PowerShell module to create individual user accounts</span></span>

<span data-ttu-id="c4b8d-p111">Azure Active Directory V2 PowerShell 모듈에서 **새로 만들기 AzureADUser** cmdlet을 사용 하려면 먼저 구독에 연결 해야 합니다. 지침, [Azure Active Directory V2 PowerShell 모듈을 사용 하 여 연결](https://go.microsoft.com/fwlink/?linkid=842218)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="c4b8d-p111">To use the **New-AzureADUser** cmdlet from the Azure Active Directory V2 PowerShell module, you must first connect to your subscription. For the instructions, see [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
<span data-ttu-id="c4b8d-161">연결한 후 다음 구문을 사용하여 개별 계정을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c4b8d-161">After you have connected, use the following syntax to create an individual account:</span></span>
  
```
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="<user account password>"
New-AzureADUser -DisplayName <DisplayName> -GivenName <FirstName> -SurName <LastName> -UserPrincipalName <Account> -UsageLocation <CountryCode> -MailNickName <mailbox name> -PasswordProfile $PasswordProfile -AccountEnabled $true
```

<span data-ttu-id="c4b8d-162">이 예제에서는 Caleb Sills라는 미국 사용자의 계정을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c4b8d-162">This example creates an account for the United States user named Caleb Sills:</span></span>
  
```
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="3Rv0y1q39/chsy"
New-AzureADUser -DisplayName "Caleb Sills" -GivenName "Caleb" -SurName "Sills" -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -MailNickName calebs -PasswordProfile $PasswordProfile -AccountEnabled $true
```
  
## <a name="see-also"></a><span data-ttu-id="c4b8d-163">See also</span><span class="sxs-lookup"><span data-stu-id="c4b8d-163">See also</span></span>

<span data-ttu-id="c4b8d-164">Office 365 powershell 사용자를 관리 하는 방법에 대 한 다음 추가 항목을 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4b8d-164">See these additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="c4b8d-165">삭제 하 고 사용자 계정을 Office 365 PowerShell로 복원</span><span class="sxs-lookup"><span data-stu-id="c4b8d-165">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="c4b8d-166">Office 365 powershell 블록 사용자 계정</span><span class="sxs-lookup"><span data-stu-id="c4b8d-166">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="c4b8d-167">Office 365 PowerShell을 사용한 사용자 계정에 게 라이선스 할당</span><span class="sxs-lookup"><span data-stu-id="c4b8d-167">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="c4b8d-168">Office 365 PowerShell을 사용한 사용자 계정에서 라이선스를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4b8d-168">Remove licenses from user accounts with Office 365 PowerShell</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="c4b8d-169">이 항목에서 사용된 cmdlet에 대한 자세한 내용은 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="c4b8d-169">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="c4b8d-170">Csv 내보내기</span><span class="sxs-lookup"><span data-stu-id="c4b8d-170">Export-Csv</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113299)
    
- [<span data-ttu-id="c4b8d-171">Csv 가져오기</span><span class="sxs-lookup"><span data-stu-id="c4b8d-171">Import-Csv</span></span>](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/import-csv)
    
- [<span data-ttu-id="c4b8d-172">New-msoluser</span><span class="sxs-lookup"><span data-stu-id="c4b8d-172">New-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [<span data-ttu-id="c4b8d-173">ForEach 개체</span><span class="sxs-lookup"><span data-stu-id="c4b8d-173">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="c4b8d-174">새 AzureADUser</span><span class="sxs-lookup"><span data-stu-id="c4b8d-174">New-AzureADUser</span></span>](https://docs.microsoft.com/powershell/module/azuread/new-azureaduser?view=azureadps-2.0)
    

