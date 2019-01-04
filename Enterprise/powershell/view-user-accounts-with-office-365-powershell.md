---
title: Office 365 PowerShell을 사용한 사용자 계정 보기
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
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
description: '요약: 보기, 목록, 또는 사용자 계정을 Office 365 powershell 다양 한 방식으로 표시 합니다.'
ms.openlocfilehash: dc33b64207341576968867fbeea6f211034eeca6
ms.sourcegitcommit: 15db0f1e5f8036e46063662d7df22387906f8ba7
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/04/2019
ms.locfileid: "27546529"
---
# <a name="view-user-accounts-with-office-365-powershell"></a>Office 365 PowerShell을 사용한 사용자 계정 보기

**요약:** Office 365 powershell 다양 한 방식으로 사용자 계정을 봅니다.
  
Office 365 관리 센터를 사용 하 여 Office 365 테 넌 트에 대 한 계정을 볼 수 있지만 Office 365 PowerShell을 사용 하 여 수 및 Office 365 관리 센터 수 없는 일부 작업을 수행 해야 합니다.
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Azure Active Directory PowerShell을 사용 하 여 그래프 모듈에 대 한

첫째, [Office 365 테 넌 트에 연결](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)합니다.
  
### <a name="view-all-accounts"></a>모든 계정 보기

사용자 계정의 전체 목록을 표시 하려면이 명령을 실행 합니다.
  
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

특정 사용자 계정으로 표시 하려면 사용자 계정의 사용자 계정 이름 (UPN)를 입력, 제거는 "<" 및 ">" 문자를 하 고이 명령을 실행 합니다.
  
```
Get-AzureADUser -ObjectID <UPN of user account>
```

### <a name="view-additional-property-values-for-a-specific-account"></a>특정 계정에 대 한 추가 속성 값을 보려면

기본적으로 **Get AzureADUser** cmdlet만 계정의 ObjectID, DisplayName 및 UserPrincipalName 속성을 표시 합니다.

더 많은 수를 표시 하려면 속성의 목록에 대 한 선택적 사용할 수 있습니다 **Select-object** cmdlet은 **Get AzureADUser** cmdlet과 함께. 두 cmdlet을 결합 하는, 사용 하 여 풀에 "파이프" 문자 "|", 그래프를 하나의 명령의 결과 가져간에 다음 명령을 보낼 용 Azure Active Directory PowerShell에 지시 하는 합니다. 모든 사용자 계정에 대해 DisplayName, 부서 및 usagelocation이 표시 하는 명령의 예가 나와 다음과 같습니다.
  
```
Get-AzureADUser | Select-Object DisplayName,Department,UsageLocation
```

이 명령은 지시 하는 Office 365 PowerShell:
  
- 사용자 계정 ( **Get AzureADUser** )에 대 한 정보를 모두 가져오고에 다음 명령을 보낼 ( **|** ).
    
- 사용자 계정 이름, 부서 및 사용 현황 위치에만 ( **Select-object DisplayName, 부서, UsageLocation** )를 표시 합니다.
  
모든 사용자 계정에 대 한 속성을 보려면 사용 **Select-object** cmdlet 및 와일드 카드 문자 (*)를 모두 표시 특정 사용자 계정에 대 한 합니다. 다음은 한 예가입니다.
  
```
Get-AzureADUser -ObjectID "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

다른 예로 다음 명령 사용 하 여 특정 사용자 계정의 사용 가능된 상태를 확인할 수 있습니다.
  
```
Get-AzureADUser -ObjectID <UPN of user account> | Select-Object DisplayName,UserPrincipalName,AccountEnabled
```

### <a name="view-some-accounts-based-on-a-common-property"></a>일반 속성을 기준으로 일부 계정 보기

더 많은 수를 표시 하기 위해 계정 목록에 대 한 선택적 사용할 수 있습니다 **Where-object** cmdlet은 **Get AzureADUser** cmdlet과 함께. 두 cmdlet을 결합 하는, 사용 하 여 풀에 "파이프" 문자 "|", 그래프를 하나의 명령의 결과 가져간에 다음 명령을 보낼 용 Azure Active Directory PowerShell에 지시 하는 합니다. 지정 되지 않은 사용 위치를 가진 사용자 계정을 표시 하는 명령의 예가 나와 다음과 같습니다.
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null}
```

이 명령은 PowerShell Azure Active Directory를 그래프에 대 한 지시 합니다.
  
- 사용자 계정 ( **Get AzureADUser** )에 대 한 정보를 모두 가져오고에 다음 명령을 보낼 ( **|** ).
    
- 지정 되지 않은 사용 위치를 가진 사용자 계정을 모두 찾기 ( **Where-object {$\_합니다. $Null usagelocation이-eq}** ). 중괄호 안에 명령은 지시만 usagelocation이 사용자 계정 속성에는 계정 집합을 확인 하는 Office 365 PowerShell ( ** $ \_합니다. Usagelocation이** ) 지정 된 ( **-eq $Null** ) 하지 않습니다.
    
**Usagelocation이** 속성은 사용자 계정과 관련 된 많은 속성 중 하나입니다. 모든 사용자 계정에 대 한 속성을 보려면 사용 **Select-object** cmdlet 및 와일드 카드 문자 (*)를 모두 표시 특정 사용자 계정에 대 한 합니다. 다음은 한 예가입니다.
  
```
Get-AzureADUser -ObjectID "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

예,이 목록에서 **도시** 는 사용자 계정 속성의 이름입니다. 즉, 런던에 거주 하는 사용자에 대 한 사용자 계정을 모두 나열 하려면 다음 명령을 사용할 수 있습니다.
  
```
Get-AzureADUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  이 예제에 표시 된 **Where-object** cmdlet에 대 한 구문은 **Where-object {$\_.** [사용자 계정 속성 이름] [비교 연산자] [값] **}**. > equals에 대 한 **-eq** , 같지에 대 한 **-ne** , 보다 작음, 보다 큼에 대 한 **-gt** 하 고 다른 사용자에 대 한 **-lt** [비교 연산자] 됩니다.  [값]은 일반적으로 문자열 (문자, 숫자, 및 기타 문자 시퀀스), 숫자 값 또는 **$Null** 지정 되지 않은 대 한 > 자세한 내용은 [Where-object](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where-Object?view=powershell-5.1) 를 참조 하십시오.
  

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Windows PowerShell 용 Microsoft Azure Active Directory 모듈을 사용 하 여

첫째, [Office 365 테 넌 트에 연결](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)합니다.

### <a name="view-all-accounts"></a>모든 계정 보기

사용자 계정의 전체 목록을 표시 하려면이 명령을 실행 합니다.
  
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

표시를 필터링 할 추가 매개 변수에 대 한 자세한 내용은 표시 하는 사용자 계정 집합 [Get-msoluser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100))를 참조 하십시오.
  

### <a name="view-a-specific-account"></a>특정 계정 보기

특정 사용자 계정으로 표시 하려면 사용자 계정의 사용자 계정 이름 (UPN)를 입력, 제거는 "<" 및 ">" 문자를 하 고이 명령을 실행 합니다.
  
```
Get-MsolUser -UserPrincipalName <UPN of user account>
```

### <a name="view-some-accounts-based-on-a-common-property"></a>일반 속성을 기준으로 일부 계정 보기

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
>  이 예제에 표시 된 **Where-object** cmdlet에 대 한 구문은 **Where-object {$\_.** [사용자 계정 속성 이름] [비교 연산자] [값] **}**.  [비교 연산자]은 equals에 대 한 **-eq** , 같지에 대 한 **-ne** , 보다 작음, 보다 큼에 대 한 **-gt** 하 고 다른 사용자에 대 한 **-lt** 입니다.  [값]는 일반적으로 문자열 (문자, 숫자, 및 기타 문자 시퀀스), 숫자 값 또는 **$Null** 지정 되지 않은 해야 합니다. 자세한 내용은 [Where-object](https://technet.microsoft.com/en-us/library/hh849715.aspx) 를 참조 하십시오.
  
다음 명령 사용 하 여 사용자 계정의 차단 된 상태를 확인할 수 있습니다.
  
```
Get-MolUser -UserPrincipalName <UPN of user account> | Select-Object DisplayName,BlockCredential
```

### <a name="view-additional-property-values-for-accounts"></a>계정에 대 한 추가 속성 값을 보려면

기본적으로 **Get-msoluser** cmdlet은 사용자 계정의 세 속성을 표시 합니다.
  
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
Scott Wallace           Operations
```

**Select-object** cmdlet를 사용 하면 원하는 속성을 표시 하는 명령을 선택할 수 있습니다. 모든 사용자 계정에 대 한 속성을 보려면 모두를 표시 하는 와일드 카드 문자 (*)를 사용 하 여 특정 사용자 계정에 대 한 합니다. 다음은 한 예가입니다.
  
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

디렉터리 동기화를 만들고 Office 365 사용자 관리를 사용 하는 경우에 Office 365 사용자에서 예상 된가 로컬 계정을 표시할 수 있습니다. 다음 Azure AD Connect가 ObjectGUID의 기본 소스 기준 위치를 사용 하도록 구성 된 것으로 가정 (원본 기준 위치를 구성 하는 방법에 자세한 내용은 참조 [Azure AD 연결: 개념 디자인](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/plan-connect-design-concepts)) powershell에 대 한 Active Directory 모듈에 있다고 가정 하 고 된 설치 ( [RSAT 도구](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)참조).

```
(Get-ADUser [guid][system.convert]::frombase64string((Get-MsolUser -UserPrincipalName <UPN of user account>).ImmutableID)).Guid
```

    
## <a name="see-also"></a>참고 항목

[Office 365 PowerShell을 사용하여 사용자 계정 및 라이선스 관리](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Office 365 PowerShell을 사용하여 Office 365 관리](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell 시작](getting-started-with-office-365-powershell.md)

