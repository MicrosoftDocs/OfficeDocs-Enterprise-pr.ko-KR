---
title: Office 365 PowerShell를 사용 하 여 사용자 계정 속성 구성
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
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: '요약: Office 365 테 넌 트에 개인 또는 여러 사용자 계정 속성을 구성 하려면 Office 365 PowerShell를 사용 합니다.'
ms.openlocfilehash: 60b3c1d91df0cb28f19f60a285093de7337904a9
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2018
ms.locfileid: "17552691"
---
# <a name="configure-user-account-properties-with-office-365-powershell"></a>Office 365 PowerShell를 사용 하 여 사용자 계정 속성 구성

 **요약:** Office 365 PowerShell을 사용 하 여 Office 365 테 넌 트의 개인 또는 여러 사용자 계정 속성 구성.
  
Office 365 관리 센터를 사용 하 여 Office 365 테 넌 트의 사용자 계정에 대 한 속성을 구성할 수 있지만 Office 365 PowerShell을 사용 하 여 수 및 Office 365 관리 센터 수 없는 일부 작업을 수행 해야 합니다.
  
## <a name="before-you-begin"></a>시작하기 전에

이 항목의 절차를 수행하려면 Office 365 PowerShell에 연결되어 있어야 합니다. 지침을 보려면 [PowerShell Office 365에 연결](connect-to-office-365-powershell.md)을 참조하세요.
  
## <a name="change-properties-for-a-specific-user-account"></a>특정 사용자 계정에 대 한 속성을 변경 합니다.

특정 사용자 계정에 대 한 속성을 구성 하려면 [이와](https://msdn.microsoft.com/library/azure/dn194136.aspx) cmdlet을 사용 하 고 속성을 설정 하거나 변경를 지정 합니다. 프랑스 Belinda Newman의 사용 현황 위치를 변경 하는이 예제에서는 명령 합니다.
  
```
Set-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" -UsageLocation "FR"
```

하면 **-UserPrincipalName** 매개 변수와 함께 계정을 식별 하 고 설정 또는 추가 매개 변수를 사용 하 여 특정 속성을 변경 합니다. 가장 일반적인 매개 변수 목록은 다음과 같습니다.
  
- -도시 "\<도시 이름 >"
    
- -국가 "\<국가 이름 >"
    
- -부서 "\<부서 이름 >"
    
- -DisplayName "\<완전 한 사용자 이름 >"
    
- -팩스 "\<팩스 번호 >"
    
- -FirstName "\<사용자 이름 >"
    
- -LastName "\<사용자 마지막 이름 >"
    
- -MobilePhone "\<휴대폰 번호 >"
    
- -Office "\<사무실 위치 >"
    
- -PhoneNumber "\<사무실 전화번호 >"
    
- -PostalCode "\<우편번호 >"
    
- -PreferredLanguage "\<언어 >"
    
- -상태 "\<상태 이름 >"
    
- -StreetAddress "\<주소 >"
    
- -Title "\<제목 이름 >"
    
- -Usagelocation이 "\<2 자리 국가 또는 지역 코드 >"
    
    ISO 3166-1 alpha-2 (A2) 두 문자로 된 국가 또는 지역 코드입니다.
    
추가 매개 변수에 대 한 [이와](https://msdn.microsoft.com/library/azure/dn194136.aspx) 참조 하십시오.
  
모든 사용자의 사용자 계정 이름을 보려면 다음 명령을 실행 합니다.
  
```
Get-MSolUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

이 명령은 지시 하는 Office 365 PowerShell:
  
- 사용자 계정 ( **Get-msoluser** )에 대 한 정보를 모두 가져오고에 다음 명령을 보낼 ( **|** ).
    
- 사용자 계정 이름 목록을 사전순으로 정렬 ( **Sort 개체 UserPrincipalName** )에 다음 명령을 보냅니다 ( **|** ).
    
- 각 계정 ( **Select-object UserPrincipalName** )에 대 한 사용자 계정 이름 속성만을 표시 합니다.
    
- 하 한 화면에 표시 ( **더 많은** ) 한번 합니다.
    
이 명령은 계정을 모두 나열 합니다. 기반으로 표시 하는 계정에 대 한 사용자 계정 이름 표시 하려는 경우 (이름 및 성) 이름, 아래 **$userName** 변수를 입력 (제거는 \< 및 > 문자), 그런 후 다음 명령을 실행 합니다.
  
```
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Caleb Sills 라는 사용자에 대 한 사용자 계정 이름을 표시 하는이 예제입니다.
  
```
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

**$Upn** 변수를 사용 하 여 표시 이름에 따라 개별 계정에 변경할 수 있습니다. 다음은 프랑스, Belinda Newman의 사용 현황 위치를 설정 하지만 그녀의 사용자 계정 이름 대신 그녀의 표시 이름을 지정 하는 예제가입니다.
  
```
$userName="<Display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

## <a name="change-properties-for-all-user-accounts"></a>모든 사용자 계정에 대 한 속성을 변경 합니다.

모든 사용자에 대 한 속성을 변경 하려면 **Get-msoluser** 및 **이와** cmdlet의 조합을 사용할 수 있습니다. 프랑스에 모든 사용자에 대 한 사용 현황 위치를 변경 하는 다음 예제에서는:
  
```
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

이 명령은 지시 하는 Office 365 PowerShell:
  
- 사용자 계정 ( **Get-msoluser** )에 대 한 정보를 모두 가져오고에 다음 명령을 보낼 ( **|** ).
    
- 프랑스 ( **이와-usagelocation이 "FR"** )로 사용자 위치를 설정 합니다.
    
## <a name="change-properties-for-a-specific-set-of-user-accounts"></a>사용자 계정의 특정 집합에 대 한 속성을 변경 합니다.

사용자 계정의 특정 집합에 대 한 속성을 변경 하려면 **Get-msoluser**, **Where-object**및 **이와** cmdlet의 조합을 사용할 수 있습니다. 프랑스 회계 부서의 모든 사용자에 대 한 사용 현황 위치를 변경 하는 다음 예제에서는:
  
```
Get-MsolUser | Where-Object {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

이 명령은 지시 하는 Office 365 PowerShell:
  
- 사용자 계정 ( **Get-msoluser** )에 대 한 정보를 모두 가져오고에 다음 명령을 보낼 ( **|** ).
    
- 해당 부서 속성이 "Accounting"로 설정 ( **Where-object {$_ 사용자 계정을 모두 찾기. 부서-eq "Accounting"}** )에 다음 명령을 결과 정보를 보내고 ( **|** ).
    
- 프랑스 ( **이와-usagelocation이 "FR"** )로 사용자 위치를 설정 합니다.
    
- 하 한 화면에 표시 ( **더 많은** ) 한번 합니다.
    
## <a name="use-the-azure-active-directory-v2-powershell-module-to-configure-user-account-properties"></a>Azure Active Directory V2 PowerShell 모듈을 사용 하 여 사용자 계정 속성을 구성 하려면

Azure Active Directory V2 PowerShell 모듈을 사용자 계정에 대 한 속성을 구성 하려면 [집합 AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet을 사용 하 고 속성을 설정 하거나 변경를 지정 합니다. 하지만 먼저, 구독에 연결 해야 합니다. 지침, [Azure Active Directory V2 PowerShell 모듈을 사용 하 여 연결](https://go.microsoft.com/fwlink/?linkid=842218)을 참조 하십시오.
  
### <a name="change-properties-for-a-specific-user-account"></a>특정 사용자 계정에 대 한 속성을 변경 합니다.

프랑스 Belinda Newman의 사용 현황 위치를 변경 하는이 예제에서는 명령 합니다.
  
```
Set-AzureADUser -ObjectID "BelindaN@litwareinc.onmicosoft.com" -UsageLocation "FR"
```

하면 **-ObjectID** 매개 변수와 함께 계정을 식별 하 고 설정 또는 추가 매개 변수를 사용 하 여 특정 속성을 변경 합니다. 가장 일반적인 매개 변수 목록은 다음과 같습니다.
  
- -부서 "\<부서 이름 >"
    
- -DisplayName "\<완전 한 사용자 이름 >"
    
- -FacsimilieTelephoneNumber "\<팩스 번호 >"
    
- -GivenName "\<사용자 이름 >"
    
- -성 "\<사용자 마지막 이름 >"
    
- -모바일 "\<휴대폰 번호 >"
    
- -JobTitle "\<직함 >"
    
- -PreferredLanguage "\<언어 >"
    
- -StreetAddress "\<주소 >"
    
- -도시 "\<도시 이름 >"
    
- -상태 "\<상태 이름 >"
    
- -PostalCode "\<우편번호 >"
    
- -국가 "\<국가 이름 >"
    
- -TelephoneNumber "\<사무실 전화번호 >"
    
- -Usagelocation이 "\<2 자리 국가 또는 지역 코드 >"
    
    ISO 3166-1 alpha-2 (A2) 두 문자로 된 국가 또는 지역 코드입니다.
    
추가 매개 변수 [집합 AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) 을 참조 하십시오.
  
사용자 계정에 대 한 사용자 계정 이름을 표시 하려면 다음 명령을 실행 합니다.
  
```
Get-AzureADUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

이 명령은 지시 하는 Office 365 PowerShell:
  
- 사용자 계정 ( **Get AzureADUser** )에 대 한 정보를 모두 가져오고에 다음 명령을 보낼 ( **|** ).
    
- 사용자 계정 이름 목록을 사전순으로 정렬 ( **Sort 개체 UserPrincipalName** )에 다음 명령을 보냅니다 ( **|** ).
    
- 각 계정 ( **Select-object UserPrincipalName** )에 대 한 사용자 계정 이름 속성만을 표시 합니다.
- 하 한 화면에 표시 ( **더 많은** ) 한번 합니다.
    
이 명령은 계정을 모두 나열 합니다. 기반으로 표시 하는 계정에 대 한 사용자 계정 이름 표시 하려는 경우 (이름 및 성) 이름, 아래 **$userName** 변수를 입력 (제거는 \< 및 > 문자), 그런 후 다음 명령을 실행 합니다.
  
```
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Caleb Sills 라는 사용자에 대 한 사용자 계정 이름을 표시 하는이 예제입니다.
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

**$Upn** 변수를 사용 하 여 표시 이름에 따라 개별 계정에 변경할 수 있습니다. 다음은 프랑스, Belinda Newman의 사용 현황 위치를 설정 하지만 그녀의 사용자 계정 이름 대신 그녀의 표시 이름을 지정 하는 예제가입니다.
  
```
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a>모든 사용자 계정에 대 한 속성을 변경 합니다.

모든 사용자에 대 한 속성을 변경 하려면 **Get AzureADUser** 및 **집합 AzureADUser** cmdlet의 조합을 사용할 수 있습니다. 프랑스에 모든 사용자에 대 한 사용 현황 위치를 변경 하는 다음 예제에서는:
  
```
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

이 명령은 지시 하는 Office 365 PowerShell:
  
- 사용자 계정 ( **Get AzureADUser** )에 대 한 정보를 모두 가져오고에 다음 명령을 보낼 ( **|** ).
    
- 프랑스 ( **집합 AzureADUser-usagelocation이 "FR"** )로 사용자 위치를 설정 합니다.
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a>사용자 계정의 특정 집합에 대 한 속성을 변경 합니다.

사용자 계정의 특정 집합에 대 한 속성을 변경 하려면 **Get AzureADUser**, **위치**및 **집합 AzureADUser** cmdlet의 조합을 사용할 수 있습니다. 프랑스 회계 부서의 모든 사용자에 대 한 사용 현황 위치를 변경 하는 다음 예제에서는:
  
```
Get-AzureADUser | Where-Object {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

이 명령은 지시 하는 Office 365 PowerShell:
  
- 사용자 계정 ( **Get AzureADUser** )에 대 한 정보를 모두 가져오고에 다음 명령을 보낼 ( **|** ).
    
- 해당 부서 속성이 "Accounting"로 설정 하는 사용자 계정을 모두 찾기 ( **여기에서 {$_ 합니다. 부서-eq "Accounting"}** )에 다음 명령을 결과 정보를 보내고 ( **|** ).
    
- 프랑스 ( **집합 AzureADUser-usagelocation이 "FR"** )로 사용자 위치를 설정 합니다.
    
## <a name="see-also"></a>참고 항목

#### 

[사용자 계정 및 Office 365 PowerShell을 사용 하 여 라이센스 관리](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Office 365 PowerShell 사용한 Office 365 관리](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell 시작](getting-started-with-office-365-powershell.md)

