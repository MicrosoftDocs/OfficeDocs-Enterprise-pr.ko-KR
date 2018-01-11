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
- Ent_Office_Other
- O365ITProTrain
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: "사용 하는 방법은 Office 365 PowerShell 에 대 한 사용자 계정을 만드는 Office 365."
ms.openlocfilehash: 97830f8158f84e6978cf3f2d168aa83d9fc551e6
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/11/2018
---
# <a name="create-user-accounts-with-office-365-powershell"></a>Office 365 PowerShell을 사용 하 여 사용자 계정 만들기

**요약:** Office 365에서 Office 365 PowerShell을 사용하여 사용자 계정을 만드는 방법을 알아보세요.
  
사용할 수 있습니다 Office 365 PowerShell 효과적으로 사용자 계정, 특히 여러 사용자 계정을 만들 수 있습니다. 사용자 계정을 만들 때 Office 365 PowerShell, 특정 계정 속성은 항상 필요 합니다. 다른 속성의 계정을 만들 필요는 없습니다 그렇지 않을 경우 중요 합니다. 다음 표에서 이러한 제한에 대해 설명합니다.
  
****

|**속성 이름**|**필수 여부**|**설명**|
|:-----|:-----|:-----|
|**DisplayName** <br/> |예  <br/> |표시 이름에 사용 되는 Office 365 서비스. 예를 들어, Caleb 창턱  <br/> |
|**UserPrincipalName** <br/> |예  <br/> |계정에 로그인 하는 데 사용 되는 이름 Office 365 서비스. For example, CalebS@contoso.onmicrosoft.com.  <br/> |
|**FirstName** <br/> |아니요  <br/> ||
|**LastName** <br/> |아니요  <br/> ||
|**LicenseAssignment** <br/> |아니요  <br/> |이것은 라이센스 제도 (라이센스 계획으로 Office 365 계획 또는 SKU)에서 사용 가능한 라이선스는 사용자 계정에 할당 되. 라이선스 정의 Office 365 계정에 사용할 수 있는 서비스입니다. 계정을 만들면 계정에 액세스 하려면 라이센스가 필요 하지만 사용자에 게 라이선스를 할당 하지 않아도 됩니다. Office 365 서비스. 30 일을 만든 후 사용자 계정 허가 해야 합니다.<br/> **Get-MsolAccountSku** cmdlet을 사용하여 조직의 라이선싱 계획(**AccountSkuId**) 및 사용할 수 있는 라이선스를 확인할 수 있습니다. 자세한 내용은 [Office 365 PowerShell을 통해 라이선스 및 서비스 확인](view-licenses-and-services-with-office-365-powershell.md)을 참조하세요.<br/> |
|**Password** <br/> |아니요  <br/> | 암호를 지정 하지 않으면 사용자 계정에 임의의 암호를 할당 하 고 암호는 명령의 결과에 표시 됩니다. 암호를 지정 하면 다음과 같은 복잡성을 만족 해야 합니다. <br/>  8에서 16 ASCII 텍스트 문자입니다. <br/>  다음과 같은 종류의 모든 3 문자: 소문자, 대문자, 숫자 및 기호입니다. <br/> |
|**UsageLocation** <br/> |아니요  <br/> |유효한 ISO 3166-1 alpha-2 국가 코드입니다. 예를 들어 미국은 US, 프랑스는 FR입니다. 특정 국가에서는 일부 Office 365 서비스를 사용할 수 없으므로 이 값을 제공하는 것이 중요합니다. 따라서 계정에 이 값이 구성되어 있지 않으면 사용자 계정에 라이선스를 할당할 수 없습니다. 자세한 내용은 [라이센스 제한 정보](https://go.microsoft.com/fwlink/p/?LinkId=691730)를 참조하세요.<br/> |
   
## <a name="before-you-begin"></a>시작하기 전에

이 항목의 절차를 수행하려면 Office 365 PowerShell에 연결되어 있어야 합니다. 지침을 보려면 [PowerShell Office 365에 연결](connect-to-office-365-powershell.md)을 참조하세요.
  
## <a name="use-office-365-powershell-to-create-individual-user-accounts"></a>사용 하 여 Office 365 PowerShell 개별 사용자 계정을 만들려면

개별 계정을 만들려면 다음 구문을 사용 합니다.
  
```
New-MsolUser -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -UserPrincipalName <Account> -UsageLocation <CountryCode> -LicenseAssignment <AccountSkuID> [-Password <Password>]
```

로부터 라이센스를 할당 하는이 예제 Caleb 창턱 이라는 미국 사용자에 대 한 계정을 만들고는  `contoso:ENTERPRISEPACK` (Office 365 Enterprise E3) 라이센스 제도.
  
```
New-MsolUser -DisplayName "Caleb Sills" -FirstName Caleb -LastName Sills -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -LicenseAssignment contoso:ENTERPRISEPACK
```

## <a name="use-office-365-powershell-to-create-multiple-user-accounts"></a>사용 하 여 Office 365 PowerShell 여러 사용자 계정을 만들려면

1. 필요한 사용자 계정 정보를 포함 하는 쉼표로 구분 된 값 (CSV) 파일을 만듭니다. 예를 들면 다음과 같습니다.
    
  ```
  UserPrincipalName,FirstName,LastName,DisplayName,UsageLocation,AccountSkuId
ClaudeL@contoso.onmicrosoft.com,Claude,Loiselle,Claude Loiselle,US,contoso:ENTERPRISEPACK
LynneB@contoso.onmicrosoft.com,Lynne,Baxter,Lynne Baxter,US,contoso:ENTERPRISEPACK
ShawnM@contoso.onmicrosoft.com,Shawn,Melendez,Shawn Melendez,US,contoso:ENTERPRISEPACK
  ```

 > [!NOTE]
>CSV 파일의 첫 번째 행에서 열 이름 및 순서는 무작위지만 나머지 파일의 데이터는 열 이름의 순서와 일치하는지 확인하고 Office 365 PowerShell 명령에서 매개 변수 값의 열 이름을 사용합니다.
    
2. 다음 구문을 사용합니다.
    
  ```
  Import-Csv -Path <Input CSV File Path and Name> | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId [-Password $_.Password]} | Export-Csv -Path <Output CSV File Path and Name>
  ```

이 이때는 C:\My Documents\NewAccounts.csv 라는 파일에서 사용자 계정을 만들고 C:\My Documents\NewAccountResults.csv 라는 파일에 결과 기록 합니다.
    
  ```
  Import-Csv -Path "C:\My Documents\NewAccounts.csv" | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId} | Export-Csv -Path "C:\My Documents\NewAccountResults.csv"
  ```

3. 결과 볼 수 있는 출력 파일을 검토 합니다. 임의의 암호 생성 된 출력 파일에 표시 되므로 암호를 지정 하지 않았습니다.
    
## <a name="use-the-azure-active-directory-v2-powershell-module-to-create-individual-user-accounts"></a>Azure Active Directory V2 PowerShell 모듈을 사용하여 개별 사용자 계정 만들기

Azure Active Directory V2 PowerShell 모듈에서 **New-AzureADUser** cmdlet을 사용하려면 먼저 구독에 연결해야 합니다. 지침은[Azure Active Directory V2 PowerShell 모듈을 사용하여 연결](https://go.microsoft.com/fwlink/?linkid=842218)을 참조하세요.
  
연결한 후 다음 구문을 사용하여 개별 계정을 만듭니다.
  
```
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="<user account password>"
New-AzureADUser -DisplayName <DisplayName> -GivenName <FirstName> -SurName <LastName> -UserPrincipalName <Account> -UsageLocation <CountryCode> -MailNickName <mailbox name> -PasswordProfile $PasswordProfile -AccountEnabled $true
```

이 예제에서는 Caleb Sills라는 미국 사용자의 계정을 만듭니다.
  
```
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="3Rv0y1q39/chsy"
New-AzureADUser -DisplayName "Caleb Sills" -GivenName "Caleb" -SurName "Sills" -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -MailNickName calebs -PasswordProfile $PasswordProfile -AccountEnabled $true
```
  
## <a name="see-also"></a>참고 항목

Office 365 PowerShell을 사용하여 사용자를 관리하는 방법에 대한 다음 추가 항목을 참조하세요.
  
- [Office 365 PowerShell을 사용하여 사용자 계정 삭제 및 복원](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [블록 사용자 계정 Office 365 PowerShell을 사용 하 여](block-user-accounts-with-office-365-powershell.md)
    
- [Office 365 PowerShell을 사용 하 여 사용자 계정에 라이선스를 할당 합니다.](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [Office 365 PowerShell을 사용 하 여 사용자 계정에서 라이센스를 제거 합니다.](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
이 항목에서 사용된 cmdlet에 대한 자세한 내용은 다음 항목을 참조하십시오.
  
- [Csv 내보내기](https://go.microsoft.com/fwlink/p/?LinkId=113299)
    
- [Import-Csv]((https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/import-csv))
    
- [New-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [ForEach-Object](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [New-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/new-azureaduser?view=azureadps-2.0)
    

