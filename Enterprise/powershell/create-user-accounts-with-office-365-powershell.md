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
# <a name="create-user-accounts-with-office-365-powershell"></a>Office 365 PowerShell을 사용 하 여 사용자 계정 만들기

**요약:** Office 365에서 사용자 계정을 만들려면 Office 365 PowerShell을 사용 하는 방법에 알아봅니다.
  
Office 365 PowerShell 효율적으로 사용자 계정을 만들려면, 특히 여러 사용자 계정을 사용할 수 있습니다. Office 365 PowerShell에서 사용자 계정을 만들면 특정 계정 속성이 항상 필수인 합니다. 다른 속성은 계정을 만들 필요가 없다고 이지만 중요 한 그렇지 않은 경우. 다음 표에에서는 이러한 속성에 대 한 설명입니다.
  
****

|**속성 이름**|**필수?**|**설명**|
|:-----|:-----|:-----|
|**DisplayName** <br/> |예  <br/> |Office 365 서비스에서 사용 되는 표시 이름입니다. 예를들어 Caleb Sills 합니다.  <br/> |
|**UserPrincipalName** <br/> |예  <br/> |Office 365 서비스에 로그인 하는데 사용 되는 계정 이름입니다. 예: CalebS@contoso.onmicrosoft.com 합니다.  <br/> |
|**FirstName** <br/> |아니요  <br/> ||
|**LastName** <br/> |아니요  <br/> ||
|**LicenseAssignment** <br/> |아니요  <br/> |사용자 계정에 할당 된 라이선스를 사용할 수 있는 라이선스 계획 (로 알려져: 라이선스 계획, Office 365 계획 또는 SKU)입니다. 이 라이선스 계정에 사용할 수 있는 Office 365 서비스를 정의 합니다. 계정에는 Office 365 서비스에 액세스 하는 라이선스가 필요 하지만 계정을 만들 경우 사용자에 게 라이선스를 할당할 필요가 없습니다. 사용자 계정을 만든 후에 30 일 해야 합니다.<br/> **Get-msolaccountsku** cmdlet을 사용 하 여 조직에서 라이선스 계획 ( **AccountSkuId** ) 및 사용 가능한 라이선스를 볼 수 있습니다. 자세한 내용은 [보기 라이선스 및 Office 365 PowerShell을 사용 하 여 서비스를](view-licenses-and-services-with-office-365-powershell.md)참조 하십시오.<br/> |
|**암호** <br/> |아니요  <br/> | 암호를 지정 하지 않으면 사용자 계정에 임의의 암호를 할당 하 고 암호는 명령의 결과에 표시 됩니다. 암호를 지정 하면 다음과 같은 복잡성을 만족 해야 합니다. <br/>  8에서 16 ASCII 텍스트 문자입니다. <br/>  다음과 같은 종류의 모든 3 문자: 소문자, 대문자, 숫자 및 기호입니다. <br/> |
|**Usagelocation이** <br/> |아니요  <br/> |유효한 ISO 3166-1 alpha-2 국가 코드입니다. 예: 대한민국, 미국, 대한민국 및 프랑스에 대 한 FR 합니다. 되므로이 값을 제공 하는 것이 중요 하므로 해당 계정에이 값을 구성 하지 않으면 사용자 계정에 라이선스를 할당할 수는 없습니다 일부 Office 365 서비스를 특정 국가에서 사용할 수 없습니다. 자세한 내용은 [라이선스 제한에 대 한](https://go.microsoft.com/fwlink/p/?LinkId=691730)참조입니다.<br/> |
   
## <a name="before-you-begin"></a>시작하기 전에

이 항목의 절차에서는 Office 365 PowerShell에 연결 해야 합니다. 자세한 내용은 [Office 365 PowerShell 연결](connect-to-office-365-powershell.md)을 참조 하십시오.
  
## <a name="use-office-365-powershell-to-create-individual-user-accounts"></a>Office 365 PowerShell을 사용 하 여 개별 사용자 계정을 만들려면

개별 계정을 만들려면 다음 구문을 사용 합니다.
  
```
New-MsolUser -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -UserPrincipalName <Account> -UsageLocation <CountryCode> -LicenseAssignment <AccountSkuID> [-Password <Password>]
```

이 예제에서는 Caleb Sills 라는 미국 사용자에 대 한 계정을 만들고에서 라이선스를 할당은 `contoso:ENTERPRISEPACK` (Office 365 Enterprise E3) 라이선스 계획 합니다.
  
```
New-MsolUser -DisplayName "Caleb Sills" -FirstName Caleb -LastName Sills -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -LicenseAssignment contoso:ENTERPRISEPACK
```

## <a name="use-office-365-powershell-to-create-multiple-user-accounts"></a>Office 365 PowerShell을 사용 하 여 여러 사용자 계정을 만들려면

1. 필요한 사용자 계정 정보를 포함 하는 쉼표로 구분 된 값 (CSV) 파일을 만듭니다. 예를 들면 다음과 같습니다.
    
  ```
  UserPrincipalName,FirstName,LastName,DisplayName,UsageLocation,AccountSkuId
ClaudeL@contoso.onmicrosoft.com,Claude,Loiselle,Claude Loiselle,US,contoso:ENTERPRISEPACK
LynneB@contoso.onmicrosoft.com,Lynne,Baxter,Lynne Baxter,US,contoso:ENTERPRISEPACK
ShawnM@contoso.onmicrosoft.com,Shawn,Melendez,Shawn Melendez,US,contoso:ENTERPRISEPACK
  ```

 > [!NOTE]
>열 이름 및 CSV 파일의 행 1에 있는 순서는 임의의 하지만 파일의 나머지 부분에서 데이터 열 이름의 순서 일치 하는지 확인 하 고 Office 365 PowerShell 명령에서 매개 변수 값에 대 한 열 이름을 사용 합니다.
    
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

Azure Active Directory V2 PowerShell 모듈에서 **새로 만들기 AzureADUser** cmdlet을 사용 하려면 먼저 구독에 연결 해야 합니다. 지침, [Azure Active Directory V2 PowerShell 모듈을 사용 하 여 연결](https://go.microsoft.com/fwlink/?linkid=842218)을 참조 하십시오.
  
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
  
## <a name="see-also"></a>See also

Office 365 powershell 사용자를 관리 하는 방법에 대 한 다음 추가 항목을 참조 합니다.
  
- [삭제 하 고 사용자 계정을 Office 365 PowerShell로 복원](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Office 365 powershell 블록 사용자 계정](block-user-accounts-with-office-365-powershell.md)
    
- [Office 365 PowerShell을 사용한 사용자 계정에 게 라이선스 할당](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [Office 365 PowerShell을 사용한 사용자 계정에서 라이선스를 제거 합니다.](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
이 항목에서 사용된 cmdlet에 대한 자세한 내용은 다음 항목을 참조하십시오.
  
- [Csv 내보내기](https://go.microsoft.com/fwlink/p/?LinkId=113299)
    
- [Csv 가져오기](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/import-csv)
    
- [New-msoluser](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [ForEach 개체](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [새 AzureADUser](https://docs.microsoft.com/powershell/module/azuread/new-azureaduser?view=azureadps-2.0)
    

