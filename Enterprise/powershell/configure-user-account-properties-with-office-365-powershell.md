---
title: PowerShell을 사용 하 여 Microsoft 365 사용자 계정 속성 구성
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/16/2020
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
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: '요약: Microsoft 365 용 PowerShell을 사용 하 여 Microsoft 365 테 넌 트에서 개별 또는 여러 사용자 계정의 속성을 구성 합니다.'
ms.openlocfilehash: ccf9bf9930551ab1ee26ef7a1f69427cdc4871f5
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230854"
---
# <a name="configure-microsoft-365-user-account-properties-with-powershell"></a>PowerShell을 사용 하 여 Microsoft 365 사용자 계정 속성 구성

*이 문서는 Microsoft 365 Enterprise 및 Office 365 Enterprise에 모두 적용 됩니다.*

Microsoft 365 관리 센터를 사용 하 여 Microsoft 365 테 넌 트의 사용자 계정에 대 한 속성을 구성할 수 있지만 PowerShell을 사용 하 여 Microsoft 365 관리 센터에서 수행할 수 없는 몇 가지 작업을 실행할 수도 있습니다.
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Graph 모듈용 Azure Active Directory PowerShell 사용하기

Graph 모듈에 대 한 Azure Active Directory PowerShell을 사용 하 여 사용자 계정 속성을 구성 하려면 [AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet을 사용 하 고 설정 하거나 변경할 속성을 지정 합니다. 

먼저 [Microsoft 365 테 넌 트에 연결](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)합니다.
   
### <a name="change-properties-for-a-specific-user-account"></a>특정 사용자 계정에 대 한 속성 변경

**-ObjectID** 매개 변수를 사용 하 여 계정을 식별 하 고 추가 매개 변수를 사용 하 여 특정 속성을 설정 하거나 변경 합니다. 가장 일반적인 매개 변수 목록은 다음과 같습니다.
  
- -부서 " \<department name> "
    
- -DisplayName " \<full user name> "
    
- -FacsimilieTelephoneNumber " \<fax number> "
    
- -GivenName " \<user first name> "
    
- -성 " \<user last name> "
    
- -Mobile " \<mobile phone number> "
    
- -JobTitle " \<job title> "
    
- -PreferredLanguage " \<language> "
    
- -StreetAddress " \<street address> "
    
- -구/군/시 " \<city name> "
    
- -State " \<state name> "
    
- -PostalCode " \<postal code> "
    
- -Country " \<country name> "
    
- -TelephoneNumber " \<office phone number> "
    
- -UsageLocation " \<2-character country or region code> "
    
    ISO 3166-1 alpha-2 (A2) 두 자리 국가 또는 지역 코드입니다.
    
추가 매개 변수에 대해서는 [AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) 을 참조 하십시오.


사용자 계정의 사용자 계정 이름을 표시 하려면 다음 명령을 실행 합니다.
  
```powershell
Get-AzureADUser | Sort UserPrincipalName | Select UserPrincipalName | More
```

이 명령은 PowerShell에 다음을 지시 합니다.
  
- 사용자 계정 (**AzureADUser**)에 대 한 모든 정보를 가져오고 다음 명령 ()으로 전송 **|** 합니다.
    
- 사용자 계정 이름 목록을 사전순 (**Sort UserPrincipalName**)으로 정렬 하 고 다음 명령 ()으로 보냅니다 **|** .
    
- 각 계정에 대해 사용자 계정 이름 속성을 표시 합니다 (**UserPrincipalName 선택**).

- 한**화면을 한**번에 한 화면씩 표시 합니다.
    
이 명령에는 모든 계정이 나열 됩니다. 표시 이름 (이름과 성)을 기준으로 계정의 사용자 계정 이름을 표시 하려면 아래에 **$userName** 변수를 입력 하 \< and > 고 (문자 제거) 다음 명령을 실행 합니다.
  
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

이 명령은 PowerShell에 다음을 지시 합니다.
  
- 사용자 계정 (**AzureADUser**)에 대 한 모든 정보를 가져오고 다음 명령 ()으로 전송 **|** 합니다.
    
- 사용자 위치를 프랑스 (**AzureADUser-UsageLocation "FR"**)로 설정 합니다.
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a>특정 사용자 계정 집합의 속성 변경

특정 사용자 계정 집합의 속성을 변경 하려면 **AzureADUser**, **Where**및 **AzureADUser** cmdlet을 조합 하 여 사용할 수 있습니다. 다음 예에서는 프랑스 회계 부서의 모든 사용자의 사용 위치를 변경합니다.
  
```powershell
Get-AzureADUser | Where {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

이 명령은 PowerShell에 다음을 지시 합니다.
  
- 사용자 계정 (**AzureADUser**)에 대 한 모든 정보를 가져오고 다음 명령 ()으로 전송 **|** 합니다.
    
- 부서 속성이 "회계"로 설정 된 모든 사용자 계정을 찾습니다 (**여기서 {$ _. 부서-eq "Accounting"}**)를 사용 하 고 결과 정보를 다음 명령 ( **|** )으로 보냅니다.
    
- 사용자 위치를 프랑스 (**AzureADUser-UsageLocation "FR"**)로 설정 합니다.
    
## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Windows PowerShell용 Microsoft Azure Active Directory 모듈 사용하기

Windows PowerShell 용 Microsoft Azure Active Directory 모듈을 사용 하 여 사용자 계정에 대 한 속성을 구성 하려면 **get-msoluser** cmdlet을 사용 하 고 설정 하거나 변경할 속성을 지정 합니다. 

먼저 [Microsoft 365 테 넌 트에 연결](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)합니다.
  
>[!Note]
>PowerShell Core는 Windows PowerShell용 Microsoft Azure Active Directory 모듈 및 이름에 **Msol**이 있는 cmdlet을 지원하지 않습니다. 이러한 cmdlet을 계속 사용하려면 Windows PowerShell에서 이를 실행해야 합니다.
>

### <a name="change-properties-for-a-specific-user-account"></a>특정 사용자 계정에 대 한 속성 변경

특정 사용자 계정에 대 한 속성을 구성 하려면 [get-msoluser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)) cmdlet을 사용 하 고 설정 하거나 변경할 속성을 지정 합니다. 

**-UserPrincipalName** 매개 변수를 사용 하 여 계정을 식별 하 고 추가 매개 변수를 사용 하 여 특정 속성을 설정 하거나 변경 합니다. 가장 일반적인 매개 변수 목록은 다음과 같습니다.
  
- -구/군/시 " \<city name> "
    
- -Country " \<country name> "
    
- -부서 " \<department name> "
    
- -DisplayName " \<full user name> "
    
- -Fax " \<fax number> "
    
- -FirstName " \<user first name> "
    
- -LastName " \<user last name> "
    
- -MobilePhone " \<mobile phone number> "
    
- -Office " \<office location> "
    
- -PhoneNumber " \<office phone number> "
    
- -PostalCode " \<postal code> "
    
- -PreferredLanguage " \<language> "
    
- -State " \<state name> "
    
- -StreetAddress " \<street address> "
    
- -Title " \<title name> "
    
- -UsageLocation " \<2-character country or region code> "
    
    ISO 3166-1 alpha-2 (A2) 두 자리 국가 또는 지역 코드입니다.
    
추가 매개 변수에 대해서는 [get-msoluser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)) 을 참조 하십시오.

모든 사용자의 사용자 계정 이름을 보려면 다음 명령을 실행 합니다.
  
```powershell
Get-MSolUser | Sort UserPrincipalName | Select UserPrincipalName | More
```

이 명령은 PowerShell에 다음을 지시 합니다.
  
- 사용자 계정 (**get-msoluser**)에 대 한 모든 정보를 가져오고 다음 명령 ()으로 전송 **|** 합니다.
    
- 사용자 계정 이름 목록을 사전순 (**Sort UserPrincipalName**)으로 정렬 하 고 다음 명령 ()으로 보냅니다 **|** .
    
- 각 계정에 대해 사용자 계정 이름 속성을 표시 합니다 (**UserPrincipalName 선택**).
    
- 한**화면을 한**번에 한 화면씩 표시 합니다.
    
이 명령에는 모든 계정이 나열 됩니다. 표시 이름 (이름과 성)을 기준으로 계정의 사용자 계정 이름을 표시 하려면 아래에 **$userName** 변수를 입력 하 \< and > 고 (문자 제거) 다음 명령을 실행 합니다.
  
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

이 명령은 PowerShell에 다음을 지시 합니다.
  
- 사용자 계정 (**get-msoluser**)에 대 한 모든 정보를 가져오고 다음 명령 ()으로 전송 **|** 합니다.
    
- 사용자 위치를 프랑스 (**get-msoluser-UsageLocation "FR"**)로 설정 합니다.
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a>특정 사용자 계정 집합의 속성 변경

특정 사용자 계정 집합의 속성을 변경 하려면 **get-msoluser**, **Where**및 **get-msoluser** cmdlet을 조합 하 여 사용할 수 있습니다. 다음 예에서는 프랑스 회계 부서의 모든 사용자의 사용 위치를 변경합니다.
  
```powershell
Get-MsolUser | Where {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

이 명령은 PowerShell에 다음을 지시 합니다.
  
- 사용자 계정 (**get-msoluser**)에 대 한 모든 정보를 가져오고 다음 명령 ()으로 전송 **|** 합니다.
    
- 부서 속성이 "회계"로 설정 된 모든 사용자 계정을 찾습니다 (**여기서 {$ _. 부서-eq "Accounting"}**)를 사용 하 고 결과 정보를 다음 명령 ( **|** )으로 보냅니다.
    
- 사용자 위치를 프랑스 (**get-msoluser-UsageLocation "FR"**)로 설정 합니다.
    

## <a name="see-also"></a>참고 항목

[PowerShell을 사용 하 여 Microsoft 365 사용자 계정, 라이선스 및 그룹 관리](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[PowerShell을 사용 하 여 Microsoft 365 관리](manage-office-365-with-office-365-powershell.md)
  
[Microsoft 365 용 PowerShell 시작](getting-started-with-office-365-powershell.md)
