---
title: "Office 365 PowerShell을 사용한 사용자 계정 보기"
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
- LIL_Placement
- PowerShell
- Ent_Office_Other
ms.assetid: bb12f49d-a85d-4f3b-ada2-5c4e33977b10
description: "요약: 보기, 목록, 또는 사용자 계정을 Office 365 powershell 다양 한 방식으로 표시 합니다."
ms.openlocfilehash: e9ffa439c1840cbbbd8a47c2835d9427330804be
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2018
---
# <a name="view-user-accounts-with-office-365-powershell"></a>Office 365 PowerShell을 사용한 사용자 계정 보기

 **요약:** 보기, 목록, 또는 사용자 계정을 Office 365 powershell 다양 한 방식으로 표시 합니다.
  
Office 365 관리 센터를 사용 하 여 Office 365 테 넌 트에 대 한 계정을 볼 수 있지만 Office 365 PowerShell을 사용 하 여 수 및 Office 365 관리 센터 수 없는 일부 작업을 수행 해야 합니다.
  
## <a name="before-you-begin"></a>시작하기 전에

이 항목의 절차를 수행하려면 Office 365 PowerShell에 연결되어 있어야 합니다. 지침을 보려면 [PowerShell Office 365에 연결](connect-to-office-365-powershell.md)을 참조하세요.
  
## <a name="display-office-365-user-account-information"></a>Office 365 사용자 계정 정보 표시

사용자 계정의 전체 목록을 표시 하려면 Office 365 PowerShell 명령 프롬프트 또는 PowerShell 스크립트 ISE (통합 환경)에서이 명령을 실행 합니다.
  
```
Get-MsolUser
```

다음과 비슷한 정보가 표시됩니다.
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
ZrinkaM@litwareinc.onmicrosoft.com    Zrinka Makovac        True
BonnieK@litwareinc.onmicrosoft.com    Bonnie Kearney        True
FabriceC@litwareinc.onmicrosoft.com   Fabrice Canel         True
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
AnneWlitwareinc.onmicrosoft.com       Anne Wallace          True
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

**Get-msoluser** cmdlet를 표시 하는 사용자 계정 집합을 필터링 매개 변수 집합을가지고 있습니다. 예, 허가 되지 않은 사용자 (Office 365에 추가 되었는지 하지만 서비스 중 하나를 사용 하 여 라이선스 아직 하지 않은 사용자)의 목록에 대 한이 명령을 실행 합니다.
  
```
Get-MsolUser -UnlicensedUsersOnly
```

다음과 비슷한 정보가 표시됩니다.
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

표시를 필터링 할 추가 매개 변수에 대 한 자세한 내용은 표시 하는 사용자 계정 집합 [Get-msoluser](https://msdn.microsoft.com/library/azure/dn194133.aspx) 를 참조 하십시오.
  
더 많은 수를 표시 하기 위해 계정 목록에 대 한 선택적 사용할 수 있습니다 **Where-object** cmdlet은 **Get-msoluser** cmdlet과 함께. 두 cmdlet을 결합 하는, 사용 하 여 풀에 "파이프" 문자 "|", 하나의 명령의 결과 가져와서에 다음 명령을 보낼를 Office 365 PowerShell에 지시 하는 합니다. 지정 되지 않은 사용 위치를 가진 사용자 계정을 표시 하는 명령의 예가 나와 다음과 같습니다.
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null}
```

이 명령은 지시 하는 Office 365 PowerShell:
  
- 사용자 계정 ( **Get-msoluser** )에 대 한 정보를 모두 가져오고에 다음 명령을 보낼 ( **|** ).
    
- 지정 되지 않은 사용 위치를 가진 사용자 계정을 모두 찾기 ( **Where-object {$\_합니다. $Null usagelocation이-eq}** ). 중괄호 안에 명령은 지시만 usagelocation이 사용자 계정 속성에는 계정 집합을 확인 하는 Office 365 PowerShell ( ** $ \_합니다. Usagelocation이** ) 지정 된 ( **-eq $Null** ) 하지 않습니다.
    
다음과 비슷한 정보가 표시됩니다.
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

**Usagelocation이** 속성은 사용자 계정과 관련 된 많은 속성 중 하나입니다. 모든 사용자 계정에 대 한 속성을 보려면 사용 **Select-object** cmdlet 및 와일드 카드 문자 (*)를 모두 표시 특정 사용자 계정에 대 한 합니다. 다음은 한 예가입니다.
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

예,이 목록에서 **도시** 는 사용자 계정 속성의 이름입니다. 즉, 런던에 거주 하는 사용자에 대 한 사용자 계정을 모두 나열 하려면 다음 명령을 사용할 수 있습니다.
  
```
Get-MsolUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  이 예제에 표시 된 **Where-object** cmdlet에 대 한 구문은 **Where-object {$\_.** [사용자 계정 속성 이름] [비교 연산자] [값] **}**. > [비교 연산자]는 equals에 대 한 **-eq** , 같지에 대 한 **-ne** , 보다 작음, 보다 큼에 대 한 **-gt** 하 고 다른 사용자에 대 한 **-lt** > [값]는 문자열 (문자, 숫자, 및 기타 문자 시퀀스), 일반적으로 숫자 값 또는 **$Null** 에 대 한 지정 되지 않은 > 자세한 내용은 [Where-object](https://technet.microsoft.com/en-us/library/hh849715.aspx) 를 참조 하십시오.
  
다음 명령 사용 하 여 사용자 계정의 차단 된 상태를 확인할 수 있습니다.
  
```
Get-MolUser -UserPrincipalName <UPN of user account> | Select DisplayName,BlockCredential
```

## <a name="select-the-user-account-properties-to-display"></a>사용자 계정 속성을 선택하여 표시

기본적으로 [Get-msoluser](https://msdn.microsoft.com/library/azure/dn194133.aspx) cmdlet은 사용자 계정의 세 속성을 표시 합니다.
  
- UserPrincipalName
    
- DisplayName
    
- isLicensed
    
사용자에 대 한 작동 하는 부서 및 사용자 Office 365 서비스를 사용 하 여 있는 국가/지역 등의 추가 속성을 필요한 경우 사용자 계정 목록을 지정 하는 **Select-object** cmdlet과 함께에서 **Get-msoluser** 를 실행할 수 있습니다. 속성 수 있습니다. 다음은 한 예가입니다.
  
```
Get-MsolUser | Select-Object DisplayName, Department, UsageLocation
```

이 명령은 지시 하는 Office 365 PowerShell:
  
- 사용자 계정 ( **Get-msoluser** )에 대 한 정보를 모두 가져오고에 다음 명령을 보낼 ( **|** ).
    
- 사용자 계정 이름, 부서 및 사용 현황 위치에만 ( **Select-object DisplayName, 부서, UsageLocation** )를 표시 합니다.
    
다음과 비슷한 정보가 표시됩니다.
  
```
DisplayName             Department                       UsageLocation
-----------             ----------                       -------------
Zrinka Makovac          Sales & Marketing                    US
Bonnie Kearney          Sales & Marketing                    US
Fabrice Canel           Legal                                US
Brian Johnson
Anne Wallace            Executive Management                 US
Alex Darrow             Sales & Marketing                    US
David Longmuir      Operations                               US
Scott Wallace            Operations
```

**Select-object** cmdlet을 사용 하는 속성을 표시 하는 명령을 선택할 수 있습니다. 모든 사용자 계정에 대 한 속성을 보려면 모두를 표시 하는 와일드 카드 문자 (*)를 사용 하 여 특정 사용자 계정에 대 한 합니다. 다음은 한 예가입니다.
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

더 많은 수를 표시 하기 위해 계정 목록에 대 한 선택적 사용할 수도 있습니다 **Where-object** cmdlet입니다. 지정 되지 않은 사용 위치를 가진 사용자 계정을 표시 하는 명령의 예가 나와 다음과 같습니다.
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

이 명령은 지시 하는 Office 365 PowerShell:
  
- 사용자 계정 ( **Get-msoluser** )에 대 한 정보를 모두 가져오고에 다음 명령을 보낼 ( **|** ).
    
- 지정 되지 않은 사용 위치를 가진 사용자 계정을 모두 찾기 ( **Where-object {$\_합니다. $Null usagelocation이-eq}** )에 다음 명령을 결과 정보를 보내고 ( **|** ). 중괄호 안에 명령은 usagelocation이 사용자 계정 속성에는 계정 집합을 확인 하는 Office 365 PowerShell 지시 됩니다 ( ** $ \_합니다. Usagelocation이** ) 지정 된 ( **-eq $Null** ) 하지 않습니다.
    
- 사용자 계정 이름, 부서 및 사용 현황 위치에만 ( **Select-object DisplayName, 부서, UsageLocation** )를 표시 합니다.
    
다음과 비슷한 정보가 표시됩니다.
  
```
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

## <a name="use-the-azure-active-directory-v2-powershell-module-to-display-user-accounts"></a>Azure Active Directory V2 PowerShell 모듈을 사용 하 여 사용자 계정을 표시 하려면

Azure Active Directory V2 PowerShell 모듈을 사용자 계정에 대 한 속성을 표시 하려면 [Get AzureADUser](https://docs.microsoft.com/powershell/module/azuread/get-azureaduser?view=azureadps-2.0) cmdlet을 사용 합니다. 하지만 먼저, 구독에 연결 해야 합니다. 지침,[Azure Active Directory V2 PowerShell 모듈을 사용 하 여 연결](https://go.microsoft.com/fwlink/?linkid=842218)을 참조 하십시오.
  
### <a name="display-office-365-user-account-information"></a>Office 365 사용자 계정 정보 표시

사용자 계정의 전체 목록을 표시 하려면 Office 365 PowerShell 명령 프롬프트 또는 PowerShell 스크립트 ISE (통합 환경)에서이 명령을 실행 합니다.
  
```
Get-AzureADUser
```

기본적으로 **Get AzureADUser** cmdlet은 사용자 계정의 세 속성을 표시 합니다.
  
- ObjectID
    
- DisplayName
    
- UserPrincipalName
    
더 많은 수를 표시 하기 위해 계정 목록에 대 한 선택적 사용할 수 있습니다 **Where-object** cmdlet은 **Get AzureADUser** cmdlet과 함께. 두 cmdlet을 결합 하는, 사용 하 여 풀에 "파이프" 문자 "|", 하나의 명령의 결과 가져와서에 다음 명령을 보낼를 Office 365 PowerShell에 지시 하는 합니다. 지정 되지 않은 사용 위치를 가진 사용자 계정을 표시 하는 명령의 예가 나와 다음과 같습니다.
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null}
```

이 명령은 지시 하는 Office 365 PowerShell:
  
- 사용자 계정 ( **Get AzureADUser** )에 대 한 정보를 모두 가져오고에 다음 명령을 보낼 ( **|** ).
    
- 지정 되지 않은 사용 위치를 가진 사용자 계정을 모두 찾기 ( **Where-object {$\_합니다. $Null usagelocation이-eq}** ). 중괄호 안에 명령은 지시만 usagelocation이 사용자 계정 속성에는 계정 집합을 확인 하는 Office 365 PowerShell ( ** $ \_합니다. Usagelocation이** ) 지정 된 ( **-eq $Null** ) 하지 않습니다.
    
**Usagelocation이** 속성은 사용자 계정과 관련 된 많은 속성 중 하나입니다. 모든 사용자 계정에 대 한 속성을 보려면 사용 **Select-object** cmdlet 및 와일드 카드 문자 (*)를 모두 표시 특정 사용자 계정 ( **더 많은** ) 한번에 한 페이지에 대 한 합니다. 다음은 한 예가입니다.
  
```
Get-AzureADUser -ObjectID "BelindaN@litwareinc.onmicosoft.com" | Select-Object * | More
```

예, **도시** 는 사용자 계정 속성의 이름입니다. 즉, 런던에 거주 하는 사용자에 대 한 사용자 계정을 모두 나열 하려면 다음 명령을 사용할 수 있습니다.
  
```
Get-AzureADUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  이 예제에 표시 된 **Where-object** cmdlet에 대 한 구문은 **Where-object {$\_.** [사용자 계정 속성 이름] [비교 연산자] [값] **}**. > [비교 연산자]는 equals에 대 한 **-eq** , 같지에 대 한 **-ne** , 보다 작음, 보다 큼에 대 한 **-gt** 하 고 다른 사용자에 대 한 **-lt** > [값]는 문자열 (문자, 숫자, 및 기타 문자 시퀀스), 일반적으로 숫자 값 또는 **$Null** 에 대 한 지정 되지 않은 > 자세한 내용은[Where-object](https://technet.microsoft.com/en-us/library/hh849715.aspx) 를 참조 하십시오.
  
### <a name="select-the-user-account-properties-to-display"></a>사용자 계정 속성을 선택하여 표시

기본적으로 **Get AzureADUser** cmdlet은 사용자 계정의 ObjectID, DisplayName 및 UserPrincipalName 속성을 표시 합니다. 사용자에 대 한 작동 하는 부서 및 사용자 Office 365 서비스를 사용 하 여 있는 국가/지역 등의 추가 속성을 필요한 경우 사용자의 목록을 지정 하는 **Select-object** cmdlet과 함께에서 **Get AzureADUser** 를 실행할 수 있습니다. 계정 속성입니다. 다음은 한 예가입니다.
  
```
Get-AzureADUser | Select-Object DisplayName,Department,UsageLocation
```

이 명령은 지시 하는 Office 365 PowerShell:
  
- 사용자 계정 ( **Get AzureADUser** )에 대 한 정보를 모두 가져오고에 다음 명령을 보낼 ( **|** ).
    
- 사용자 계정 이름, 부서 및 사용 현황 위치에만 ( **Select-object DisplayName, 부서, UsageLocation** )를 표시 합니다.
    
더 많은 수를 표시 하기 위해 계정 목록에 대 한 선택적 사용할 수도 있습니다 **Where-object** cmdlet입니다. 지정 되지 않은 사용 위치를 가진 사용자 계정을 표시 하는 명령의 예가 나와 다음과 같습니다.
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

이 명령은 지시 하는 Office 365 PowerShell:
  
- 사용자 계정 ( **Get AzureADUser** )에 대 한 정보를 모두 가져오고에 다음 명령을 보낼 ( **|** ).
    
- 지정 되지 않은 사용 위치를 가진 사용자 계정을 모두 찾기 ( **Where-object {$\_합니다. $Null usagelocation이-eq}** )에 다음 명령을 결과 정보를 보내고 ( **|** ). 중괄호 안에 명령은 usagelocation이 사용자 계정 속성에는 계정 집합을 확인 하는 Office 365 PowerShell 지시 됩니다 ( ** $ \_합니다. Usagelocation이** ) 지정 된 ( **-eq $Null** ) 하지 않습니다.
    
- 사용자 계정 이름, 부서 및 사용 현황 위치에만 ( **Select-object DisplayName, 부서, UsageLocation** )를 표시 합니다.
    
## <a name="new-to-office-365"></a>Office 365의 새로운 기능

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
  
## <a name="see-also"></a>참고 항목

#### 

[사용자 계정 및 Office 365 PowerShell을 사용 하 여 라이센스 관리](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Office 365 PowerShell 사용한 Office 365 관리](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell 시작](getting-started-with-office-365-powershell.md)

