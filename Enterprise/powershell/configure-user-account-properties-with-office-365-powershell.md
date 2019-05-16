---
title: Office 365 PowerShell를 사용 하 여 사용자 계정 속성 구성
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
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
ms.openlocfilehash: 3fdf5c4c5dbb4c44a3c91d343bd77810a1411a20
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069243"
---
# <a name="configure-user-account-properties-with-office-365-powershell"></a>Office 365 PowerShell를 사용 하 여 사용자 계정 속성 구성

 **요약:** Office 365 PowerShell을 사용 하 여 Office 365 테 넌 트에서 개별 또는 여러 사용자 계정에 대 한 속성을 구성 합니다.
  
Office 365 관리 센터를 사용 하 여 Office 365 테 넌 트의 사용자 계정에 대 한 속성을 구성할 수도 있지만 office 365 PowerShell을 사용 하 여 Office 365 관리 센터에서 수행할 수 없는 작업도 수행 하면 됩니다.
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Graph 모듈용 Azure Active Directory PowerShell 사용하기

Graph 모듈에 대 한 Azure Active Directory PowerShell을 사용 하 여 사용자 계정 속성을 구성 하려면 [AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet을 사용 하 고 설정 하거나 변경할 속성을 지정 합니다. 

먼저, [Office 365 테넌트에 연결](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)합니다.
   
### <a name="change-properties-for-a-specific-user-account"></a>특정 사용자 계정에 대 한 속성 변경

**-ObjectID** 매개 변수를 사용 하 여 계정을 식별 하 고 추가 매개 변수를 사용 하 여 특정 속성을 설정 하거나 변경 합니다. 가장 일반적인 매개 변수 목록은 다음과 같습니다.
  
- -부서 "\<부서 name>"
    
- -DisplayName "\<Full user name>"
    
- -FacsimilieTelephoneNumber "\<fax number>"
    
- -GivenName "\<User first name>"
    
- -성 "\<사용자 마지막 name>"
    
- -모바일 "\<휴대폰 전화 number>"
    
- -JobTitle "\<job title>"
    
- -PreferredLanguage "\<language>"
    
- -StreetAddress "\<번 지 address>"
    
- -구/\<군/시 "구 name>"
    
- -State "\<state name>"
    
- -PostalCode "\<우편 번호 code>"
    
- -Country "\<country name>"
    
- -TelephoneNumber "\<사무실 전화 number>"
    
- -UsageLocation "\<2 자 국가 또는 지역 code>"
    
    ISO 3166-1 alpha-2 (A2) 두 자리 국가 또는 지역 코드입니다.
    
추가 매개 변수에 대해서는 [AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) 을 참조 하십시오.
  
사용자 계정의 사용자 계정 이름을 표시 하려면 다음 명령을 실행 합니다.
  
```
Get-AzureADUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

이 명령은 Office 365 PowerShell에 다음과 같이 지시 합니다.
  
- 사용자 계정 ( **AzureADUser** )에 대 한 모든 정보를 가져오고 다음 명령 ( **|** )으로 전송 합니다.
    
- 사용자 계정 이름 목록을 사전순 ( **sort-Object UserPrincipalName** )으로 정렬 하 고 다음 명령 ( **|** )으로 보냅니다.
    
- 각 계정에 대 한 사용자 계정 이름 속성 ( **선택-개체 UserPrincipalName** )만 표시 합니다.
- 한 화면을 한 번에 한 화면씩 **** 표시 합니다.
    
이 명령에는 모든 계정이 나열 됩니다. 표시 이름 (이름 및 성)을 기준으로 계정의 사용자 계정 이름을 표시 하려면 다음 명령을 실행 하 여 **$userName** 변수를 아래에 입력 합니다 ( \< 및 > 문자 제거).
  
```
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

이 예에서는 Caleb 창턱의 표시 이름을 사용 하 여 사용자 계정에 대 한 사용자 보안 주체 이름을 표시 합니다.
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

**$Upn** 변수를 사용 하 여 개별 계정을 표시 이름에 따라 변경할 수 있습니다. 다음은 Belinda Newman의 사용 위치를 프랑스로 설정 하 고 사용자 계정 이름이 아닌 표시 이름을 지정 하는 예제입니다.
  
```
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a>모든 사용자 계정에 대 한 속성 변경

모든 사용자의 속성을 변경 하려면 **AzureADUser** 및 **AzureADUser** cmdlet을 조합 하 여 사용할 수 있습니다. 다음 예에서는 모든 사용자의 사용 위치를 프랑스로 변경합니다.
  
```
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

이 명령은 Office 365 PowerShell에 다음과 같이 지시 합니다.
  
- 사용자 계정 ( **AzureADUser** )에 대 한 모든 정보를 가져오고 다음 명령 ( **|** )으로 전송 합니다.
    
- 사용자 위치를 프랑스 ( **AzureADUser-UsageLocation "FR"** )로 설정 합니다.
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a>특정 사용자 계정 집합의 속성 변경

특정 사용자 계정 집합의 속성을 변경 하려면 **AzureADUser**, **Where**및 **AzureADUser** cmdlet을 조합 하 여 사용할 수 있습니다. 다음 예에서는 프랑스 회계 부서의 모든 사용자의 사용 위치를 변경합니다.
  
```
Get-AzureADUser | Where-Object {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

이 명령은 Office 365 PowerShell에 다음과 같이 지시 합니다.
  
- 사용자 계정 ( **AzureADUser** )에 대 한 모든 정보를 가져오고 다음 명령 ( **|** )으로 전송 합니다.
    
- 부서 속성이 "회계"로 설정 된 모든 사용자 계정을 찾습니다 ( **여기서 {$ _. 부서-eq "Accounting"}** )를 사용 하 고 결과 정보를 다음 명령 ( **|** )으로 보냅니다.
    
- 사용자 위치를 프랑스 ( **AzureADUser-UsageLocation "FR"** )로 설정 합니다.
    
## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Windows PowerShell용 Microsoft Azure Active Directory 모듈 사용하기

Windows PowerShell 용 Microsoft Azure Active Directory 모듈을 사용 하 여 사용자 계정에 대 한 속성을 구성 하려면 Get-msoluser cmdlet을 사용 하 고 설정 하거나 변경할 속성을 지정 합니다. 

먼저, [Office 365 테넌트에 연결](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)합니다.
  
### <a name="change-properties-for-a-specific-user-account"></a>특정 사용자 계정에 대 한 속성 변경

특정 사용자 계정에 대 한 속성을 구성 하려면 [get-msoluser](https://msdn.microsoft.com/library/azure/dn194136.aspx) cmdlet을 사용 하 고 설정 하거나 변경할 속성을 지정 합니다. 

**-UserPrincipalName** 매개 변수를 사용 하 여 계정을 식별 하 고 추가 매개 변수를 사용 하 여 특정 속성을 설정 하거나 변경 합니다. 가장 일반적인 매개 변수 목록은 다음과 같습니다.
  
- -구/\<군/시 "구 name>"
    
- -Country "\<country name>"
    
- -부서 "\<부서 name>"
    
- -DisplayName "\<Full user name>"
    
- -Fax "\<팩스 number>"
    
- -FirstName "\<User first name>"
    
- -LastName "\<사용자의 마지막 name>"
    
- -MobilePhone "\<휴대폰 number>"
    
- -Office "\<office location>"
    
- -PhoneNumber "\<사무실 전화 number>"
    
- -PostalCode "\<우편 번호 code>"
    
- -PreferredLanguage "\<language>"
    
- -State "\<state name>"
    
- -StreetAddress "\<번 지 address>"
    
- -Title "\<title name>"
    
- -UsageLocation "\<2 자 국가 또는 지역 code>"
    
    ISO 3166-1 alpha-2 (A2) 두 자리 국가 또는 지역 코드입니다.
    
추가 매개 변수에 대해서는 [get-msoluser](https://msdn.microsoft.com/library/azure/dn194136.aspx) 을 참조 하십시오.
  
모든 사용자의 사용자 계정 이름을 보려면 다음 명령을 실행 합니다.
  
```
Get-MSolUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

이 명령은 Office 365 PowerShell에 다음과 같이 지시 합니다.
  
- 사용자 계정 ( **get-msoluser** )에 대 한 모든 정보를 가져오고 다음 명령 ( **|** )으로 전송 합니다.
    
- 사용자 계정 이름 목록을 사전순 ( **sort-Object UserPrincipalName** )으로 정렬 하 고 다음 명령 ( **|** )으로 보냅니다.
    
- 각 계정에 대 한 사용자 계정 이름 속성 ( **선택-개체 UserPrincipalName** )만 표시 합니다.
    
- 한 화면을 한 번에 한 화면씩 **** 표시 합니다.
    
이 명령에는 모든 계정이 나열 됩니다. 표시 이름 (이름 및 성)을 기준으로 계정의 사용자 계정 이름을 표시 하려면 다음 명령을 실행 하 여 **$userName** 변수를 아래에 입력 합니다 ( \< 및 > 문자 제거).
  
```
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

이 예제에서는 Caleb 창턱 라는 사용자에 대 한 사용자 계정 이름을 표시 합니다.
  
```
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

**$Upn** 변수를 사용 하 여 개별 계정을 표시 이름에 따라 변경할 수 있습니다. 다음은 Belinda Newman의 사용 위치를 프랑스로 설정 하 고 사용자 계정 이름이 아닌 표시 이름을 지정 하는 예제입니다.
  
```
$userName="<display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a>모든 사용자 계정에 대 한 속성 변경

모든 사용자에 대한 속성을 변경하려면 **Get-msoluser** 및 **Set-msoluser** cmdlet의 조합을 사용합니다. 다음 예에서는 모든 사용자의 사용 위치를 프랑스로 변경합니다.
  
```
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

이 명령은 Office 365 PowerShell에 다음과 같이 지시 합니다.
  
- 사용자 계정 ( **get-msoluser** )에 대 한 모든 정보를 가져오고 다음 명령 ( **|** )으로 전송 합니다.
    
- 사용자 위치를 프랑스 ( **get-msoluser-UsageLocation "FR"** )로 설정 합니다.
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a>특정 사용자 계정 집합의 속성 변경

특정 사용자 계정 집합의 속성을 변경 하려면 **get-msoluser**, **Where 개체**및 **get-msoluser** cmdlet을 함께 사용 하면 됩니다. 다음 예에서는 프랑스 회계 부서의 모든 사용자의 사용 위치를 변경합니다.
  
```
Get-MsolUser | Where-Object {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

이 명령은 Office 365 PowerShell에 다음과 같이 지시 합니다.
  
- 사용자 계정 ( **get-msoluser** )에 대 한 모든 정보를 가져오고 다음 명령 ( **|** )으로 전송 합니다.
    
- 부서 속성이 "회계"로 설정 된 모든 사용자 계정을 찾습니다 ( **여기서-개체 {$ _. 부서-eq "Accounting"}** )를 사용 하 고 결과 정보를 다음 명령 ( **|** )으로 보냅니다.
    
- 사용자 위치를 프랑스 ( **get-msoluser-UsageLocation "FR"** )로 설정 합니다.
    

## <a name="see-also"></a>참고 항목

[Office 365 PowerShell로 사용자 계정 및 라이선스 관리](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Office 365 PowerShell을 사용하여 Office 365 관리](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell 시작](getting-started-with-office-365-powershell.md)
