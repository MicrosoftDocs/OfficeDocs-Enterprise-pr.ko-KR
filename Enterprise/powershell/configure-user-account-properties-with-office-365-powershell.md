---
title: Office 365 PowerShell를 사용 하 여 사용자 계정 속성 구성
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/16/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: '요약: Office 365 PowerShell을 사용 하 여 Office 365 테 넌 트에서 개별 또는 여러 사용자 계정에 대 한 속성을 구성 합니다.'
ms.openlocfilehash: 211210dad54cb0af772af7dc611bc2c0fdf6035a
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841605"
---
# <a name="configure-user-account-properties-with-office-365-powershell"></a>Office 365 PowerShell를 사용 하 여 사용자 계정 속성 구성

Microsoft 365 관리 센터를 사용 하 여 Office 365 테 넌 트의 사용자 계정에 대 한 속성을 구성할 수 있지만 Office 365 PowerShell을 사용 하 고 관리 센터에서 수행할 수 없는 몇 가지 작업을 실행할 수도 있습니다.
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Graph 모듈용 Azure Active Directory PowerShell 사용하기

Graph 모듈에 대 한 Azure Active Directory PowerShell을 사용 하 여 사용자 계정 속성을 구성 하려면 [AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet을 사용 하 고 설정 하거나 변경할 속성을 지정 합니다. 

먼저, [Office 365 테넌트에 연결](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)합니다.
   
### <a name="change-properties-for-a-specific-user-account"></a>특정 사용자 계정에 대 한 속성 변경

**-ObjectID** 매개 변수를 사용 하 여 계정을 식별 하 고 추가 매개 변수를 사용 하 여 특정 속성을 설정 하거나 변경 합니다. 가장 일반적인 매개 변수 목록은 다음과 같습니다.
  
- -부서 "\<부서 이름>"
    
- -DisplayName "\<전체 사용자 이름>"
    
- -FacsimilieTelephoneNumber "\<팩스 번호>"
    
- -GivenName "\<사용자 이름>"
    
- -성 "\<사용자 성>"
    
- -Mobile "\<휴대폰 번호>"
    
- -JobTitle "\<직책>"
    
- -PreferredLanguage "\<language>"
    
- -StreetAddress "\<주소>"
    
- -도시명 "\<구/군/시 이름>"
    
- -State "\<상태 이름>"
    
- -PostalCode "\<우편 번호>"
    
- -Country "\<국가 이름>"
    
- -TelephoneNumber "\<사무실 전화 번호>"
    
- -UsageLocation "\<2 자리 국가 또는 지역 코드>"
    
    ISO 3166-1 alpha-2 (A2) 두 자리 국가 또는 지역 코드입니다.
    
추가 매개 변수에 대해서는 [AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) 을 참조 하십시오.


사용자 계정의 사용자 계정 이름을 표시 하려면 다음 명령을 실행 합니다.
  
```powershell
Get-AzureADUser | Sort UserPrincipalName | Select UserPrincipalName | More
```

이 명령은 Office 365 PowerShell에 다음과 같이 지시 합니다.
  
- 사용자 계정 ( **AzureADUser** )에 대 한 모든 정보를 가져오고 다음 명령 ( **|** )으로 전송 합니다.
    
- 사용자 계정 이름 목록을 사전순 ( **Sort UserPrincipalName** )으로 정렬 하 고 다음 명령 ( **|** )으로 보냅니다.
    
- 각 계정에 대해 사용자 계정 이름 속성을 표시 합니다 ( **UserPrincipalName 선택** ).

- 한 **화면을 한** 번에 한 화면씩 표시 합니다.
    
이 명령에는 모든 계정이 나열 됩니다. 표시 이름 (이름 및 성)을 기준으로 계정의 사용자 계정 이름을 표시 하려면 다음 명령을 실행 하 여 아래의 **$userName** 변수를 입력 합니다 ( \< 및 > 문자 제거).
  
```powershell
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

이 예에서는 Caleb 창턱의 표시 이름을 사용 하 여 사용자 계정에 대 한 사용자 보안 주체 이름을 표시 합니다.
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

**$Upn** 변수를 사용 하 여 개별 계정을 표시 이름에 따라 변경할 수 있습니다. 다음은 Belinda Newman의 사용 위치를 프랑스로 설정 하 고 사용자 계정 이름이 아닌 표시 이름을 지정 하는 예제입니다.
  
```powershell
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a>모든 사용자 계정에 대 한 속성 변경

모든 사용자의 속성을 변경 하려면 **AzureADUser** 및 **AzureADUser** cmdlet을 조합 하 여 사용할 수 있습니다. 다음 예에서는 모든 사용자의 사용 위치를 프랑스로 변경합니다.
  
```powershell
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

이 명령은 Office 365 PowerShell에 다음과 같이 지시 합니다.
  
- 사용자 계정 ( **AzureADUser** )에 대 한 모든 정보를 가져오고 다음 명령 ( **|** )으로 전송 합니다.
    
- 사용자 위치를 프랑스 ( **AzureADUser-UsageLocation "FR"** )로 설정 합니다.
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a>특정 사용자 계정 집합의 속성 변경

특정 사용자 계정 집합의 속성을 변경 하려면 **AzureADUser**, **Where**및 **AzureADUser** cmdlet을 조합 하 여 사용할 수 있습니다. 다음 예에서는 프랑스 회계 부서의 모든 사용자의 사용 위치를 변경합니다.
  
```powershell
Get-AzureADUser | Where {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

이 명령은 Office 365 PowerShell에 다음과 같이 지시 합니다.
  
- 사용자 계정 ( **AzureADUser** )에 대 한 모든 정보를 가져오고 다음 명령 ( **|** )으로 전송 합니다.
    
- 부서 속성이 "회계"로 설정 된 모든 사용자 계정을 찾습니다 ( **여기서 {$ _. 부서-eq "Accounting"}** )를 사용 하 고 결과 정보를 다음 명령 ( **|** )으로 보냅니다.
    
- 사용자 위치를 프랑스 ( **AzureADUser-UsageLocation "FR"** )로 설정 합니다.
    
## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Windows PowerShell용 Microsoft Azure Active Directory 모듈 사용하기

Windows PowerShell 용 Microsoft Azure Active Directory 모듈을 사용 하 여 사용자 계정에 대 한 속성을 구성 하려면 **get-msoluser** cmdlet을 사용 하 고 설정 하거나 변경할 속성을 지정 합니다. 

먼저, [Office 365 테넌트에 연결](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)합니다.
  
>[!Note]
>PowerShell Core는 Windows PowerShell용 Microsoft Azure Active Directory 모듈 및 이름에 **Msol**이 있는 cmdlet을 지원하지 않습니다. 이러한 cmdlet을 계속 사용하려면 Windows PowerShell에서 이를 실행해야 합니다.
>

### <a name="change-properties-for-a-specific-user-account"></a>특정 사용자 계정에 대 한 속성 변경

특정 사용자 계정에 대 한 속성을 구성 하려면 [get-msoluser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)) cmdlet을 사용 하 고 설정 하거나 변경할 속성을 지정 합니다. 

**-UserPrincipalName** 매개 변수를 사용 하 여 계정을 식별 하 고 추가 매개 변수를 사용 하 여 특정 속성을 설정 하거나 변경 합니다. 가장 일반적인 매개 변수 목록은 다음과 같습니다.
  
- -도시명 "\<구/군/시 이름>"
    
- -Country "\<국가 이름>"
    
- -부서 "\<부서 이름>"
    
- -DisplayName "\<전체 사용자 이름>"
    
- -Fax "\<팩스 번호>"
    
- -FirstName "\<사용자 이름>"
    
- -LastName "\<user last name>"
    
- -MobilePhone "\<휴대폰 번호>"
    
- -Office "\<사무실 위치>"
    
- -PhoneNumber "\<사무실 전화 번호>"
    
- -PostalCode "\<우편 번호>"
    
- -PreferredLanguage "\<language>"
    
- -State "\<상태 이름>"
    
- -StreetAddress "\<주소>"
    
- -Title "\<제목 이름>"
    
- -UsageLocation "\<2 자리 국가 또는 지역 코드>"
    
    ISO 3166-1 alpha-2 (A2) 두 자리 국가 또는 지역 코드입니다.
    
추가 매개 변수에 대해서는 [get-msoluser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)) 을 참조 하십시오.

모든 사용자의 사용자 계정 이름을 보려면 다음 명령을 실행 합니다.
  
```powershell
Get-MSolUser | Sort UserPrincipalName | Select UserPrincipalName | More
```

이 명령은 Office 365 PowerShell에 다음과 같이 지시 합니다.
  
- 사용자 계정 ( **get-msoluser** )에 대 한 모든 정보를 가져오고 다음 명령 ( **|** )으로 전송 합니다.
    
- 사용자 계정 이름 목록을 사전순 ( **Sort UserPrincipalName** )으로 정렬 하 고 다음 명령 ( **|** )으로 보냅니다.
    
- 각 계정에 대해 사용자 계정 이름 속성을 표시 합니다 ( **UserPrincipalName 선택** ).
    
- 한 **화면을 한** 번에 한 화면씩 표시 합니다.
    
이 명령에는 모든 계정이 나열 됩니다. 표시 이름 (이름 및 성)을 기준으로 계정의 사용자 계정 이름을 표시 하려면 다음 명령을 실행 하 여 아래의 **$userName** 변수를 입력 합니다 ( \< 및 > 문자 제거).
  
```powershell
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

이 예제에서는 Caleb 창턱 라는 사용자에 대 한 사용자 계정 이름을 표시 합니다.
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

**$Upn** 변수를 사용 하 여 개별 계정을 표시 이름에 따라 변경할 수 있습니다. 다음은 Belinda Newman의 사용 위치를 프랑스로 설정 하 고 사용자 계정 이름이 아닌 표시 이름을 지정 하는 예제입니다.
  
```powershell
$userName="<display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a>모든 사용자 계정에 대 한 속성 변경

모든 사용자에 대한 속성을 변경하려면 **Get-msoluser** 및 **Set-msoluser** cmdlet의 조합을 사용합니다. 다음 예에서는 모든 사용자의 사용 위치를 프랑스로 변경합니다.
  
```powershell
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

이 명령은 Office 365 PowerShell에 다음과 같이 지시 합니다.
  
- 사용자 계정 ( **get-msoluser** )에 대 한 모든 정보를 가져오고 다음 명령 ( **|** )으로 전송 합니다.
    
- 사용자 위치를 프랑스 ( **get-msoluser-UsageLocation "FR"** )로 설정 합니다.
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a>특정 사용자 계정 집합의 속성 변경

특정 사용자 계정 집합의 속성을 변경 하려면 **get-msoluser**, **Where**및 **get-msoluser** cmdlet을 조합 하 여 사용할 수 있습니다. 다음 예에서는 프랑스 회계 부서의 모든 사용자의 사용 위치를 변경합니다.
  
```powershell
Get-MsolUser | Where {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

이 명령은 Office 365 PowerShell에 다음과 같이 지시 합니다.
  
- 사용자 계정 ( **get-msoluser** )에 대 한 모든 정보를 가져오고 다음 명령 ( **|** )으로 전송 합니다.
    
- 부서 속성이 "회계"로 설정 된 모든 사용자 계정을 찾습니다 ( **여기서 {$ _. 부서-eq "Accounting"}** )를 사용 하 고 결과 정보를 다음 명령 ( **|** )으로 보냅니다.
    
- 사용자 위치를 프랑스 ( **get-msoluser-UsageLocation "FR"** )로 설정 합니다.
    

## <a name="see-also"></a>참고 항목

[Office 365 PowerShell을 사용 하 여 사용자 계정, 라이선스 및 그룹 관리](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Office 365 PowerShell 사용한 Office 365 관리](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell 시작](getting-started-with-office-365-powershell.md)
