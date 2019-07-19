---
title: Office 365 PowerShell을 사용한 사용자 계정 보기
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/19/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- PowerShell
- Ent_Office_Other
ms.assetid: bb12f49d-a85d-4f3b-ada2-5c4e33977b10
description: '요약: Office 365 PowerShell을 사용 하 여 다양 한 방식으로 사용자 계정을 보거나, 나열 하거나, 표시 합니다.'
ms.openlocfilehash: c23e9106873aa32e8daccb1e35a16862e6f9bb7d
ms.sourcegitcommit: 1c97471f47e1869f6db684f280f9085b7c2ff59f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/18/2019
ms.locfileid: "35782068"
---
# <a name="view-user-accounts-with-office-365-powershell"></a>Office 365 PowerShell을 사용한 사용자 계정 보기

**요약:** Office 365 PowerShell을 사용 하 여 다양 한 방법으로 사용자 계정을 확인 합니다.
  
Microsoft 365 관리 센터를 사용 하 여 Office 365 테 넌 트에 대 한 계정을 볼 수도 있지만 Office 365 PowerShell을 사용 하 여 관리 센터에서 수행할 수 없는 몇 가지 작업을 수행 해도 됩니다.
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Graph 모듈용 Azure Active Directory PowerShell 사용하기

먼저, [Office 365 테넌트에 연결](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)합니다.
  
### <a name="view-all-accounts"></a>모든 계정 보기

사용자 계정의 전체 목록을 표시 하려면 다음 명령을 실행 합니다.
  
```
Get-AzureADUser
```

다음과 비슷한 정보가 표시됩니다.
  
```
ObjectId                             DisplayName                                           UserPrincipalName
--------                             -----------                                           -----------------
032fc1fc-b5a2-46f1-8635-3d7dcb52c48d Adele Vance                                           AdeleV@litwareinc.OnMicr...
bd1e6af1-41e7-4f77-a2ac-5b209950135c Global Administrator                                  admin@litwareinc.onmicro...
ec37a4d6-232e-4eb7-82a5-1613490642a5 Alex Wilber                                           AlexW@litwareinc.OnMicro...
be4bdddd-c790-424c-9f96-a0cf609b7815 Allan Deyoung                                         AllanD@litwareinc.OnMicr...
598ab87b-76f0-4bf9-9538-bd46b10f4438 Christie Cline                                        ChristieC@litwareinc.OnM...
40722671-e520-4a5f-97d4-0bc9e9b2dc0f Debra Berger                                          DebraB@litwareinc.OnMicr...
```

### <a name="view-a-specific-account"></a>특정 계정 보기

특정 사용자 계정을 표시 하려면 UPN (사용자 계정 이름)이 라고도 하는 사용자 계정의 로그인 계정 이름을 입력 하 고 "<" 및 ">" 문자를 제거한 다음이 명령을 실행 합니다.
  
```
Get-AzureADUser -ObjectID <sign-in name of the user account>
```

예를 들면 다음과 같습니다.
  
```
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com
```

### <a name="view-additional-property-values-for-a-specific-account"></a>특정 계정에 대 한 추가 속성 값 보기

기본적으로 **AzureADUser** cmdlet은 계정의 ObjectID, DisplayName 및 UserPrincipalName 속성만 표시 합니다.

표시할 속성 목록을 보다 신중 하 게 선택 하려면 **AzureADUser** cmdlet과 함께 **Select-Object** cmdlet을 사용할 수 있습니다. 두 cmdlet을 결합 하기 위해 Azure Active Directory PowerShell for Graph에 설명 된 "파이프" 문자를 사용 하 여 한 명령 결과를 가져와 다음 명령으로 보냅니다. 다음은 모든 사용자 계정에 대해 DisplayName, 학과 및 UsageLocation를 표시 하는 명령 예제입니다.
  
```
Get-AzureADUser | Select-Object DisplayName,Department,UsageLocation
```

이 명령은 Office 365 PowerShell에 다음과 같이 지시 합니다.
  
- 사용자 계정 ( **AzureADUser** )에 대 한 모든 정보를 가져오고 다음 명령 ( **|** )으로 전송 합니다.
    
- 사용자 계정 이름, 부서 및 사용 위치만 표시 합니다 ( **선택-개체 DisplayName, 학과, UsageLocation** ).
  
사용자 계정에 대 한 모든 속성을 보려면 **Select-Object** cmdlet 및 와일드 카드 문자 (*)를 사용 하 여 특정 사용자 계정에 대해 모두 표시 합니다. 예를 들면 다음과 같습니다.
  
```
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

또 다른 예로, 다음 명령을 사용 하 여 특정 사용자 계정의 사용 상태를 확인할 수 있습니다.
  
```
Get-AzureADUser -ObjectID <sign-in name of the user account> | Select-Object DisplayName,UserPrincipalName,AccountEnabled
```

### <a name="view-some-accounts-based-on-a-common-property"></a>공통 속성을 기준으로 일부 계정 보기

표시할 계정 목록에 대해 좀 더 선택 하려면 **AzureADUser** cmdlet과 함께 **Where** cmdlet을 사용 하면 됩니다. 두 cmdlet을 결합 하기 위해 Azure Active Directory PowerShell for Graph에 설명 된 "파이프" 문자를 사용 하 여 한 명령 결과를 가져와 다음 명령으로 보냅니다. 다음은 지정되지 않은 사용 위치가 있는 사용자 계정만 표시하는 예제 명령입니다.
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null}
```

이 명령은 다음과 같은 그래프에 Azure Active Directory PowerShell을 지시 합니다.
  
- 사용자 계정 ( **AzureADUser** )에 대 한 모든 정보를 가져오고 다음 명령 ( **|** )으로 전송 합니다.
    
- 사용 위치 ( **여기서-개체 {$\_)가 지정 되지 않은 모든 사용자 계정을 찾습니다. UsageLocation-eq $Null}** ). 중괄호 내에서이 명령은 Office 365 PowerShell에 UsageLocation 사용자 계정 속성 ( ** $ \_을 사용 하는 경우에만 계정 집합을 찾습니다. UsageLocation** )이 지정 되지 않았습니다 ( **-eq $Null** ).
    
**UsageLocation** 속성은 사용자 계정에 연결 된 여러 속성 중 하나에 불과합니다. 사용자 계정에 대 한 모든 속성을 보려면 **Select-Object** cmdlet 및 와일드 카드 문자 (*)를 사용 하 여 특정 사용자 계정에 대해 모두 표시 합니다. 예를 들면 다음과 같습니다.
  
```
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

예를 들어이 목록에서 **도시명** 은 사용자 계정 속성의 이름입니다. 즉, 다음 명령을 사용 하 여 London에 살아있는 사용자에 대 한 모든 사용자 계정을 나열할 수 있습니다.
  
```
Get-AzureADUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  이러한 예에 표시 되는 **Where 개체** cmdlet의 구문은 **-object {$\_** 를 사용 합니다. [사용자 계정 속성 이름] [비교 연산자] 가치 **}**. > [비교 연산자]는 equals의 경우- **eq** , **-ne** = 같지 않음,-a = 부등호, **-lt** for a,- **gt** = 보다 작음, 기타 보다 작거나 같습니다.  [값]은 일반적으로 문자열 (문자, 숫자 및 기타 문자 시퀀스), 숫자 값 또는 지정 되지 않은 **$Null**> 자세한 내용을 보려면 [-Object](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where-Object?view=powershell-5.1) 를 참고 하십시오.
  

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Windows PowerShell용 Microsoft Azure Active Directory 모듈 사용하기

먼저, [Office 365 테넌트에 연결](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)합니다.

### <a name="view-all-accounts"></a>모든 계정 보기

사용자 계정의 전체 목록을 표시 하려면 다음 명령을 실행 합니다.
  
```
Get-MsolUser
```

다음과 비슷한 정보가 표시됩니다.
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BonnieK@litwareinc.onmicrosoft.com    Bonnie Kearney        True
FabriceC@litwareinc.onmicrosoft.com   Fabrice Canel         True
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
AnneWlitwareinc.onmicrosoft.com       Anne Wallace          True
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

**Get-msoluser** cmdlet에도 매개 변수 집합이 있어 표시된 사용자 계정 집합을 필터링할 수 있습니다. 예를 들어 Office 365에 추가 되었지만 아직 어떤 서비스를 사용 하도록 허가 되지 않은 사용자의 목록을 보려면이 명령을 실행 합니다.
  
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

표시 되는 사용자 계정 집합을 필터링 하기 위한 추가 매개 변수에 대 한 자세한 내용은 [get-msoluser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100))를 참조 하십시오.
  

### <a name="view-a-specific-account"></a>특정 계정 보기

특정 사용자 계정을 표시 하려면 UPN (사용자 계정 이름)이 라고도 하는 사용자 계정의 사용자 계정에 대 한 로그인 이름을 입력 하 고 "<" 및 ">" 문자를 제거한 다음이 명령을 실행 합니다.
  
```
Get-MsolUser -UserPrincipalName <sign-in name of the user account>
```

### <a name="view-some-accounts-based-on-a-common-property"></a>공통 속성을 기준으로 일부 계정 보기

표시할 계정 목록에 대해 좀 더 선택 하려면 **get-msoluser** cmdlet과 함께 **Where** cmdlet을 사용 하면 됩니다. 두 cmdlet을 결합 하려면 Office 365 PowerShell에 명령 결과를 가져와서 다음 명령으로 보내는 "파이프" 문자 "|"을 사용 합니다. 다음은 지정되지 않은 사용 위치가 있는 사용자 계정만 표시하는 예제 명령입니다.
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null}
```

이 명령은 Office 365 PowerShell에 다음과 같이 지시 합니다.
  
- 사용자 계정 ( **get-msoluser** )에 대 한 모든 정보를 가져오고 다음 명령 ( **|** )으로 전송 합니다.
    
- 사용 위치 ( **여기서-개체 {$\_)가 지정 되지 않은 모든 사용자 계정을 찾습니다. UsageLocation-eq $Null}** ). 중괄호 내에서이 명령은 Office 365 PowerShell에 UsageLocation 사용자 계정 속성 ( ** $ \_을 사용 하는 경우에만 계정 집합을 찾습니다. UsageLocation** )이 지정 되지 않았습니다 ( **-eq $Null** ).
    
다음과 비슷한 정보가 표시됩니다.
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

**UsageLocation** 속성은 사용자 계정에 연결 된 여러 속성 중 하나에 불과합니다. 사용자 계정에 대 한 모든 속성을 보려면 **Select-Object** cmdlet 및 와일드 카드 문자 (*)를 사용 하 여 특정 사용자 계정에 대해 모두 표시 합니다. 예를 들면 다음과 같습니다.
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

예를 들어이 목록에서 **도시명** 은 사용자 계정 속성의 이름입니다. 즉, 다음 명령을 사용 하 여 London에 살아있는 사용자에 대 한 모든 사용자 계정을 나열할 수 있습니다.
  
```
Get-MsolUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  이러한 예에 표시 되는 **Where 개체** cmdlet의 구문은 **-object {$\_** 를 사용 합니다. [사용자 계정 속성 이름] [비교 연산자] 가치 **}**.  [비교 연산자]는 equals의 경우- **eq** , **-ne** : 같지 않음,-a = 부등호, **-** a = 보다 작음,- **gt** for = 및 기타입니다.  [값]은 일반적으로 문자열 (문자, 숫자 및 기타 문자의 시퀀스), 숫자 값 또는 **$Null** 지정 되지 않음에 해당 합니다. 자세한 내용은 [-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) 를 참조 하세요.
  
다음 명령을 사용 하 여 사용자 계정의 차단 상태를 확인할 수 있습니다.
  
```
Get-MsolUser -UserPrincipalName <UPN of user account> | Select-Object DisplayName,BlockCredential
```

### <a name="view-additional-property-values-for-accounts"></a>계정의 추가 속성 값 보기

**Get-msoluser** cmdlet은 기본적으로 사용자 계정의 세 가지 속성을 표시 합니다.
  
- UserPrincipalName
    
- DisplayName
    
- isLicensed
    
사용자가 근무 하는 부서 및 Office 365 서비스를 사용 하는 국가/지역 같은 추가 속성이 필요한 경우 Get-msoluser cmdlet과 함께 **get-help** 를 실행 하 여 사용자 계정 목록을 지정할 수 있습니다 **** . 물성. 예를 들면 다음과 같습니다.
  
```
Get-MsolUser | Select-Object DisplayName, Department, UsageLocation
```

이 명령은 Office 365 PowerShell에 다음과 같이 지시 합니다.
  
- 사용자 계정 ( **get-msoluser** )에 대 한 모든 정보를 가져오고 다음 명령 ( **|** )으로 전송 합니다.
    
- 사용자 계정 이름, 부서 및 사용 위치만 표시 합니다 ( **선택-개체 DisplayName, 학과, UsageLocation** ).
    
다음과 비슷한 정보가 표시됩니다.
  
```
DisplayName             Department                       UsageLocation
-----------             ----------                       -------------
Bonnie Kearney          Sales & Marketing                    US
Fabrice Canel           Legal                                US
Brian Johnson
Anne Wallace            Executive Management                 US
Alex Darrow             Sales & Marketing                    US
Scott Wallace           Operations
```

**Select-Object** cmdlet을 사용 하면 명령으로 표시할 속성을 선택 하 고 선택할 수 있습니다. 사용자 계정의 모든 속성을 보려면 와일드 카드 문자 (*)를 사용 하 여 특정 사용자 계정에 대해 모두 표시 합니다. 예를 들면 다음과 같습니다.
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

표시할 계정 목록을 보다 신중 하 게 선택 하기 위해, **여기서-Object** cmdlet을 사용할 수도 있습니다. 다음은 지정되지 않은 사용 위치가 있는 사용자 계정만 표시하는 예제 명령입니다.
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

이 명령은 Office 365 PowerShell에 다음과 같이 지시 합니다.
  
- 사용자 계정 ( **get-msoluser** )에 대 한 모든 정보를 가져오고 다음 명령 ( **|** )으로 전송 합니다.
    
- 사용 위치 ( **여기서-개체 {$\_)가 지정 되지 않은 모든 사용자 계정을 찾습니다. UsageLocation-eq $Null}** )을 사용 하 고 결과 정보를 다음 명령 ( **|** )로 보냅니다. 중괄호 내에서 명령은 Office 365 PowerShell에 게 UsageLocation 사용자 계정 속성 ( ** $ \_을 갖는 계정 집합만 찾도록 지시 합니다. UsageLocation** )이 지정 되지 않았습니다 ( **-eq $Null** ).
    
- 사용자 계정 이름, 부서 및 사용 위치만 표시 합니다 ( **선택-개체 DisplayName, 학과, UsageLocation** ).
    
다음과 비슷한 정보가 표시됩니다.
  
```
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

디렉터리 동기화를 사용 하 여 Office 365 사용자를 만들고 관리 하는 경우 Office 365 사용자가 프로젝션 한 로컬 계정을 표시할 수 있습니다. 다음은 Azure AD Connect가 ObjectGUID의 기본 원본 앵커를 사용 하도록 구성 된 것으로 가정 합니다 (원본 앵커 구성에 대 한 자세한 내용은 [AZURE Ad connect: Design 개념](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/plan-connect-design-concepts)참조) 및 Powershell 용 Active Directory 모듈에 대 한 것으로 가정 설치 된 경우 ( [RSAT tools](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)참조):

```
Get-ADUser ([guid][System.Convert]::FromBase64String((Get-MsolUser -UserPrincipalName <UPN of user account>).ImmutableID)).guid
```

    
## <a name="see-also"></a>참고 항목

[Office 365 PowerShell로 사용자 계정 및 라이선스 관리](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Office 365 PowerShell을 사용하여 Office 365 관리](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell 시작](getting-started-with-office-365-powershell.md)

