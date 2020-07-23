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
# <a name="create-microsoft-365-user-accounts-with-powershell"></a>PowerShell을 사용 하 여 Microsoft 365 사용자 계정 만들기

*이 문서는 Microsoft 365 Enterprise 및 Office 365 Enterprise에 모두 적용 됩니다.*

Microsoft 365 용 PowerShell을 사용 하 여 사용자 계정, 특히 여러 사용자 계정을 효율적으로 만들 수 있습니다. PowerShell에서 사용자 계정을 만드는 경우에는 특정 계정 속성이 항상 필요 합니다. 다른 속성의 계정을 만들 필요는 없습니다 그렇지 않을 경우 중요 합니다. 다음 표에서는 이러한 속성에 대해 설명 합니다.
  
|**속성 이름**|**필수 여부**|**설명**|
|:-----|:-----|:-----|
|**DisplayName** <br/> |예  <br/> |Microsoft 365 서비스에서 사용 되는 표시 이름입니다. 예를 들어, Caleb 창턱  <br/> |
|**UserPrincipalName** <br/> |예  <br/> |Microsoft 365 서비스에 로그인 하는 데 사용 되는 계정 이름입니다. For example, CalebS@contoso.onmicrosoft.com.  <br/> |
|**FirstName** <br/> |아니요  <br/> ||
|**LastName** <br/> |아니요  <br/> ||
|**LicenseAssignment** <br/> |아니요  <br/> |사용 가능한 라이선스가 사용자 계정에 할당 되는 라이선스 계획 (라이선스 요금제 또는 SKU 라고도 함)입니다. 라이선스는 계정에 사용할 수 있는 Microsoft 365 서비스를 정의 합니다. 계정을 만들 때 사용자에 게 라이선스를 할당할 필요가 없지만 계정에 Microsoft 365 서비스에 액세스 하기 위한 라이선스가 필요 합니다. 30 일 내에 사용자 계정을 만든 후 라이선스를 허가 해야 합니다. |
|**Password** <br/> |아니요  <br/> | 암호를 지정하지 않으면 사용자 계정에 임의의 암호가 할당되고, 명령 결과에 암호가 표시됩니다. 암호를 지정할 때에는 소문자, 대문자, 숫자, 기호 중 3가지가 포함된 길이 8 ~ 16의 ASCII 문자를 사용합니다. <br/> |
|**UsageLocation** <br/> |아니요  <br/> |유효한 ISO 3166-1 alpha-2 국가 코드입니다. 예를 들어 미국, 프랑스의 경우 FR을 들을 있습니다. 일부 Microsoft 365 서비스는 특정 국가에서 사용할 수 없기 때문에이 값을 제공 하는 것이 중요 하므로, 계정에이 값이 구성 되어 있지 않으면 사용자 계정에 라이선스를 할당할 수 없습니다. 자세한 내용은 [사용권 제한 정보](https://go.microsoft.com/fwlink/p/?LinkId=691730)를 참조 하세요.  <br/> |
   

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Graph 모듈용 Azure Active Directory PowerShell 사용하기

먼저 [Microsoft 365 테 넌 트에 연결](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)합니다.

연결한 후 다음 구문을 사용하여 개별 계정을 만듭니다.
  
```powershell
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="<user account password>"
New-AzureADUser -DisplayName "<display name>" -GivenName "<first name>" -SurName "<last name>" -UserPrincipalName <sign-in name> -UsageLocation <ISO 3166-1 alpha-2 country code> -MailNickName <mailbox name> -PasswordProfile $PasswordProfile -AccountEnabled $true
```

이 예제에서는 Caleb Sills라는 미국 사용자의 계정을 만듭니다.
  
```powershell
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="3Rv0y1q39/chsy"
New-AzureADUser -DisplayName "Caleb Sills" -GivenName "Caleb" -SurName "Sills" -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -MailNickName calebs -PasswordProfile $PasswordProfile -AccountEnabled $true
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Windows PowerShell용 Microsoft Azure Active Directory 모듈 사용하기

먼저 [Microsoft 365 테 넌 트에 연결](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)합니다.

### <a name="create-an-individual-user-account"></a>개별 사용자 계정 만들기

개별 계정을 만들려면 다음 구문을 사용합니다.
  
```powershell
New-MsolUser -DisplayName <display name> -FirstName <first name> -LastName <last name> -UserPrincipalName <sign-in name> -UsageLocation <ISO 3166-1 alpha-2 country code> -LicenseAssignment <licensing plan name> [-Password <Password>]
```

>[!Note]
>PowerShell Core는 Windows PowerShell용 Microsoft Azure Active Directory 모듈 및 이름에 **Msol**이 있는 cmdlet을 지원하지 않습니다. 이러한 cmdlet을 계속 사용하려면 Windows PowerShell에서 이를 실행해야 합니다.
>

사용 가능한 라이선스 계획 이름을 열거하려면 이 명령을  사용합니다:

````powershell
Get-MsolAccountSku
````

이 예제에서는 Caleb Sills라는 미국 사용자의 계정을 만들고, `contoso:ENTERPRISEPACK`(Office 365 Enterprise E3) 라이선스 계획에서 라이선스를 할당합니다.
  
```powershell
New-MsolUser -DisplayName "Caleb Sills" -FirstName Caleb -LastName Sills -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -LicenseAssignment contoso:ENTERPRISEPACK
```

### <a name="create-multiple-user-accounts"></a>다중 사용자 계정 만들기

1. 필요한 사용자 계정 정보를 포함하는 쉼표로 구분 된 값(CSV) 파일을 만듭니다. 예를 들면 다음과 같습니다.
    
  ```powershell
  UserPrincipalName,FirstName,LastName,DisplayName,UsageLocation,AccountSkuId
  ClaudeL@contoso.onmicrosoft.com,Claude,Loiselle,Claude Loiselle,US,contoso:ENTERPRISEPACK
  LynneB@contoso.onmicrosoft.com,Lynne,Baxter,Lynne Baxter,US,contoso:ENTERPRISEPACK
  ShawnM@contoso.onmicrosoft.com,Shawn,Melendez,Shawn Melendez,US,contoso:ENTERPRISEPACK
  ```

 > [!NOTE]
>CSV 파일의 첫 번째 행에 있는 열 이름과 해당 순서는 임의적 이지만 파일의 나머지 부분에 있는 데이터가 열 이름의 순서와 일치 하는지 확인 하 고 365 Microsoft for a PowerShell 명령에서 매개 변수 값에 대 한 열 이름을 사용 합니다.
    
2. 다음 구문을 사용합니다.
    
  ```powershell
  Import-Csv -Path <Input CSV File Path and Name> | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId [-Password $_.Password]} | Export-Csv -Path <Output CSV File Path and Name>
  ```

이 예제는 C:\My Documents\NewAccounts.csv 라는 파일에서 사용자 계정을 만들고 C:\My Documents\NewAccountResults.csv 라는 파일에 결과를 기록합니다.
    
  ```powershell
  Import-Csv -Path "C:\My Documents\NewAccounts.csv" | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId} | Export-Csv -Path "C:\My Documents\NewAccountResults.csv"
  ```

3. 결과 볼 수 있는 출력 파일을 검토 합니다. 암호를 지정 하지 않았으므로 Microsoft 365이 생성 하는 임의의 암호가 출력 파일에 표시 됩니다.
    
## <a name="see-also"></a>참고 항목

[PowerShell을 사용 하 여 Microsoft 365 사용자 계정, 라이선스 및 그룹 관리](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[PowerShell을 사용 하 여 Microsoft 365 관리](manage-office-365-with-office-365-powershell.md)
  
[Microsoft 365 용 PowerShell 시작](getting-started-with-office-365-powershell.md)
