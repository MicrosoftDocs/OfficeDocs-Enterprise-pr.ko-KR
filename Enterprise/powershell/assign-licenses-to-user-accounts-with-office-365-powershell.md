---
title: "Office 365 PowerShell을 사용 하 여 사용자 계정에 라이선스를 할당 합니다."
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
- Ent_Office_Other
- LIL_Placement
- PowerShell
- O365ITProTrain
ms.assetid: ba235f4f-e640-4360-81ea-04507a3a70be
description: "Office 365 PowerShell 할당 허가 되지 않은 사용자에 게 Office 365 라이선스를 사용 하는 방법에 설명 합니다."
ms.openlocfilehash: 688e2775e7a028cd9dbe0c8ea27a7f3a453b5279
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2018
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a>Office 365 PowerShell을 사용 하 여 사용자 계정에 라이선스를 할당 합니다.

**요약:**  Office 365 PowerShell 할당 허가 되지 않은 사용자에 게 Office 365 라이선스를 사용 하는 방법에 설명 합니다.
  
사용자가 자신의 계정 사용이 허가 된 때까지 모든 Office 365 서비스를 사용할 수 없으므로 라이선스 Office 365에서 사용자 계정 하는 것이 중요 합니다. Office 365 PowerShell을 사용 하 여 효율적으로 허가 되지 않은 계정, 특히 여러 계정에 게 라이선스를 할당 수 있습니다. 

## <a name="before-you-begin"></a>시작하기 전에
<a name="RTT"> </a>

- 이 항목의 절차를 수행하려면 Office 365 PowerShell에 연결되어 있어야 합니다. 지침을 보려면 [PowerShell Office 365에 연결](connect-to-office-365-powershell.md)을 참조하세요.
    
- **Get-msolaccountsku** cmdlet을 사용 하 여 조직에서 각 계획에서 사용 가능한 라이선스 계획 및 사용 가능한 라이선스 수를 볼 수 있습니다. 각 계획에서 사용 가능한 라이선스 수가 **ActiveUnits** - **WarningUnits** - **ConsumedUnits**합니다. 계획, 라이선스 및 서비스 라이선스에 대 한 자세한 내용은 [보기 라이선스 및 Office 365 PowerShell을 사용 하 여 서비스를](view-licenses-and-services-with-office-365-powershell.md)참조 하십시오.
    
- 명령을 실행 하면 조직에서 허가 되지 않은 계정을 찾으려면`Get-MsolUser -All -UnlicensedUsersOnly`
    
- **Usagelocation이** 속성이 유효한 ISO 3166-1 alpha-2 국가 코드를로 설정 하는 사용자 계정에만 라이선스를 할당할 수 있습니다. 예: 대한민국, 미국, 대한민국 및 프랑스에 대 한 FR 합니다. 일부 Office 365 서비스 일부 국가에서는 사용할 수 없습니다. 자세한 내용은 [라이선스 제한에 대 한](https://go.microsoft.com/fwlink/p/?LinkId=691730)참조입니다.
    
    **Usagelocation이** 값을 갖지 않는 계정을 찾으려면 명령을 실행 `Get-MsolUser -All | where {$_.UsageLocation -eq $null}`합니다. 계정에 **usagelocation이** 값을 설정 하는 구문을 사용 하 여 `Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>`합니다. 예, `Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US`합니다.
    
- 사용 하지 않고 **Get-msoluser** cmdlet을 사용 하는 경우는 `-All` 매개 변수를 처음 500 개 계정만 반환 됩니다.
    
## <a name="the-short-version-instructions-without-explanations"></a>간략 한 (설명 없이 지침)
<a name="ShortVersion"> </a>

이 섹션에서는 자세한 설명 하지 않고 절차를 제공 합니다. 질문이 더 많은 정보를 원하는 경우에 항목의 나머지 부분을 읽을 수 있습니다.
  
사용자에 게 라이선스를 할당 하려면 Office 365 PowerShell에서 다음 구문을 사용 합니다.
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

라이선스를 할당 하는이 예제는 `litwareinc:ENTERPRISEPACK` 허가 되지 않은 사용자에 게 라이선스 계획 (Office 365 Enterprise E3) `belindan@litwareinc.com`합니다.
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

많은 허가 되지 않은 사용자에 게 라이선스를 할당 합니다를 다음 구문을 사용 합니다.
  
```
$x = Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>]; $x | foreach {Set-MsolUserLicense -AddLicenses "<AccountSkuId>"}
```

 **슬라이드 노트**
  
- 동일한 라이센스 제도에서 여러 라이센스 사용자 지정할 수 없습니다.
    
- 충분 한 사용 가능한 라이선스를 설치 하지 않은 경우 사용 가능한 라이선스 실행 될 때까지 **Get-msoluser** cmdlet에 의해 반환 하는 순서는 사용자에 게 라이선스 할당 됩니다.
    
라이선스를 할당 하는이 예제는 `litwareinc:ENTERPRISEPACK` 허가 되지 않은 모든 사용자에 게 라이선스 계획 (Office 365 Enterprise E3).
  
```
$AllUn = Get-MsolUser -All -UnlicensedUsersOnly; $AllUn | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

미국에서 영업 부서에서 허가 되지 않은 사용자에 게 동일한 라이센스를 지정 하는이 예제입니다.
  
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly; $USSales | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a>긴 버전 (명령에 대 한 세부 정보)
<a name="LongVersion"> </a>

[Office 365 powershell 사용이 허가 된 및 허가 되지 않은 사용자를 보려면](view-licensed-and-unlicensed-users-with-office-365-powershell.md)문서에서 설명 했 듯이 있지만 사용자는 유효한 Office 365 사용자 계정에 게 발급 되지 않은 Office 365 라이선스를 보유할 수는 있습니다. 즉,는 유효한 계정이 나 유효한 계정이 없는 사용자 됩니다 Office 365에 로그온 할 수입니다. 및 로그온 할 수 없는, 하는 경우 모든 Office 365 서비스의 활용할 수 없습니다.
  
앞에 언급된 문서에 설명된 것처럼 다음 명령을 실행하면 라이선스가 없는 사용자 계정 목록을 반환할 수 있습니다.
  
```
Get-MsolUser -All -UnlicensedUsersOnly
```

해당 명령은 현재 Office 365에 대 한 라이선스가 없는 사용자에 대 한 정보를 반환 합니다.
  
```
UserPrincipalName           DisplayName                     isLicensed
-----------------           -----------                     ----------
BelindaN@litwareinc.com     Belinda Newman                  False
```

허가 되지 않은 사용자가 한 명 있다고 볼 수 있듯이: Belinda Newman 합니다. 수행 어떻게 Belinda Office 365 라이선스를 할당 하는 방법에 대 한 죠?
  
먼저 [보기 라이선스 및 Office 365 powershell 서비스](view-licenses-and-services-with-office-365-powershell.md)문서에서 설명한 **Get-msolaccountsku** cmdlet을 실행 하려고 합니다.
  
```
Get-MsolAccountSku
```

이 명령은 다음과 비슷한 데이터를 반환합니다.
  
```
AccountSkuId               ActiveUnits    WarningUnits   ConsumedUnits
------------               -----------    ------------   -------------
litwareinc:ENTERPRISEPACK  25             0              24
```

**Get-msolaccountsku** 를 실행할 않은 이유는? ("Sku,"를 사용 하면 심지어 하는 경우는 약어로 "재고 단위입니다." 이 목적을 위해 하는 비즈니스-음성을 입력 "제품.") **Get-msolaccountsku**실행 이유는 두 가지 이유가 있습니다. 첫째,는 실제로 라이선스가 Belinda를 할당 하 고 있는지 확인 해야 합니다. 그녀를 할당할 수는 모든 라이선스는 있습니까? 확인 하려면, **ActiveUnits** 속성 (25)의 값을 사용 하 고는 (0) **WarningUnits** 및 **ConsumedUnits** (24) 속성의 값을 뺍니다.
  
 `25 - 0 - 24 = 1`
  
**ActiveUnits** 속성은 알려줍니다는 구입한 라이선스 및 **WarningUnits** 및 **ConsumedUnits** 의 값을 조합된 알려줍니다 얼마나 많은 라이선스에서에서 현재 사용 중인 합니다. 이미 구입한는 라이선스 수에서 음성에 대 한 라이선스의 수를 뺍니다. 우리가 하는 경우 사실을 알 수가 얼마나 많은 라이선스는 계속 사용할 수 있습니다. 없다면,에서는 배포에 사용할 수 있는 하나의 라이선스를 한 합니다.
  
 `25 - 0 - 24 = 1`
  
둘째, Belinda를 사용해 라이선스 계획의 이름을 알고 있어야 하는 새 라이선스를 할당 하기 위해 (즉, 알아야 **AccountSkuId** ). 이 경우 임을: 단일 라이선스 계획을가지고 ( `litwareinc:ENTERPRISEPACK`). 단, 여러 라이선스 계획을 조직에 대 한 수 있다는 것입니다. 이 경우 **Get-msolaccountsku** 두 다른 **AccountSkuIds**를 반환 하 고 라이선스를 할당 하는 경우 적절 한 라이선스 계획을 선택 해야 합니다. 지금은, 그러나 해요 가장 간단한 경우 그대로 유지 하 고 하나의 라이선스 계획 있다고 가정 합니다.
  
그러면 어떻게 라이선스를 할당 *하려면 Belinda Newman를 새* ? 이런 식으로:
  
```
Set-MsolUserLicense -UserPrincipalName "BelindaN@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

이기도 하면 작업을 수행 해야: 사용자와 적절 한 라이선스 계획에 대 한 _UserPrincipalName_ 매개 변수를 지정 하는 확인 **Set-msoluserlicense** cmdlet을 호출 하는 것입니다.
  
때 **Set-msoluserlicense** 실행이 완료 되이 다음과 유사한 화면:
  
 `PS C:\\windows\\system32>`
  
즉, 이러한 상황이 발생 아무것도 동일 하 게 모양과지 않습니다 동일 합니다. 사용자는 라이선스가 할당 된을 확인 하려면 다음과 같은 명령을 실행 합니다.
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.com"
```

모든 작업이 예상 대로 수행, Belinda의 isLicensed 속성이 True로 설정 되 나타납니다.
  
```
UserPrincipalName           DisplayName                     isLicensed
-----------------           -----------                     ----------
BelindaN@litwareinc.com     Belinda Newman                  True
```

> [! 보안 참고 사항] 좋은 질문: 실수 하 고 라이선스에 이미 있는 사용자에 게 라이선스를 할당 하려고 하는 경우에 어떻게 합니까? 단일 사용자에 게 두 라이선스 부여 결국 것? > 빠른 대답? 아니요, Office 365를 사용 하면 동일한 사용자에 게 둘 이상의 라이선스를 할당할 수 없습니다. (동일한 라이선스 계획에서 둘 이상의 라이선스입니다.) 다음과 같은 오류 메시지와 함께 명령이 실패 합니다 작업을 수행 하려고 하는 경우: > `Set-MsolUserLicense : Unable to assign this license because it is invalid. Use the Get-MsolAccountSku cmdlet to retrieve a list of valid licenses.`> 있겠지만, 해당 오류 메시지는 조금 잘못 된: 라이선스 되지 실제로 잘못 된, 방금 사용자에 게 할당 되 고가 이미 *가* 라이선스입니다. 이지만, 오류 메시지에 제외 하 고, 사용는 것이 중요 한 명의 사용자를 여러 라이선스 결국 되지 않습니다.
  
방금 살펴본 것 처럼 단일 사용자에 게 단일 라이선스를 할당 하려면 Office 365 PowerShell를 매우 쉽게 사용할 수 있습니다. 그렇다면 대체 하는 잠재 고객: 않을까요로, 단일 사용자에 게 단일 라이선스를 할당 하는 Office 365 관리 센터를 사용 하 여 엔터프라이즈 무선 전화 통신도 쉽게? 음, 엔터프라이즈 무선 전화 통신; , 정도 따라 결정, Windows PowerShell을 사용 하 여 하는데 더 익숙할 또는 Office 365 관리 센터를 사용 하 여 하는데 더 익숙할는 여부. 그러나 Windows PowerShell 특히 유용 여기서 때에 여러 사용자에 게 여러 라이선스를 할당 해야 합니다. 예,이 명령은 이미 라이선스가 없는 사용자를 Office 365 라이선스를 할당 합니다.
  
```
Get-MsolUser -All -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

위 명령에서는 사용 하 여 **Get-msoluser** 및 _UnlicensedUsersOnly_ 매개 변수는 모든 허가 되지 않은 사용자 계정의 컬렉션을 반환 합니다. 그런 다음이 컬렉션은 **Set-msoluserlicense** cmdlet을 전달 **특정** 라이선스를 할당 하는 차례로 (에서 가져온 연락처는 `litwareinc:ENTERPRISEPACK` 라이선스 계획) 컬렉션의 각 사용자에 게 있습니다.
  
아, 하지만 경우에 어떻게 라이센스는 하나만 사용할 수 있지만 5 허가 되지 않은 사용자가 있습니까? 이 경우 **Set-msoluserlicense** 에서 **Get-msoluser**에서 반환 된 첫번째 사용자에 게 사용 가능한 라이선스를 제공 합니다. **Set-msoluserlicense** 은 다음 이후 하려고 다른 네가지 사용자에 게 라이선스를 할당 합니다. 하지만 다음과 같은 오류 메시지와 함께 이러한 시도의 네 실패 합니다.
  
 `Set-MsolUserLicense : Unable to assign this license because the number of allowed licenses have been assigned.`
  
즉, 특정 실패 방금 되지 않습니다. 대신 다음과 같은 이점이 있습니다 라이선스 할당 됩니다. 그런 다음만 실패 합니다.
  
다른 예를 보겠습니다. 엔터프라이즈 무선 전화 통신 판매 부서의 모든 사용자에 게 라이선스를 할당 하려고 합니다. 문제 없어요:
  
```
Get-MsolUser -All -Department "Sales" | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

또는 오류 메시지와 컴퓨팅 처리를 최소로 유지하고 판매 부서의 라이선스가 없는 사용자에게만 라이선스를 할당할 수 있습니다.
  
```
Get-MsolUser -All -Department "Sales" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

따라서, 포인터가 없는 사용자에 게 라이선스를 라이선스를 이미 있는 하려고 합니다. 앞서 설명한 것 처럼 이미, 하는 작동 하지 않습니다.
  
다른 예는 다음과 같습니다. Office 365 라이선스 현재 없는 모든 미국 사용자 라이선스 경우도 것입니다. 이 경우:
  
```
Get-MsolUser -All -UsageLocation "US" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

이외에도 많은 예가 있습니다.
  
> [!NOTE]
> 걸리는 라고 표시, 라이선스 허가 되지 않은 모든 사용자에 게 문제를 해결 하는 명령을 실행할 수 있습니까? 나타내도록 어렵습니다: 사용자의 네트워크 연결 속도 해야할 수에서 모든 항목에 따라 달라 집니다. 적절 하 게 신속 하 게 전환이 라이선스에는 두 백 사용자를 포함 하는 경우 (즉, 안됩니다 걸릴 1 분 이상 또는 2). 있는 경우 해당 라이선스를 사용자 1 만명 분명 약간 더 오래 걸립니다. 하지만 않다는으로 Office 365 관리 센터를 사용 하 여 10, 000 사용자에 게 라이선스를 할당 하는 것이 걸립니다. 
  
제목에 우리가으로 방법은 라이선스를 할당 하는 경우 시청 해야하는 것: 사용자 **usagelocation이** 속성에 대해 구성 된 값이 없는 경우 해당 사용자는 Office 365 라이선스 할당 할 수 없습니다. 대신, 메시지가 나타납니다 오류 메시지가이 비슷합니다.
  
 `Set-MsolUserLicense : You must provide a required property: Parameter name: UsageLocation`
  
오프 라인 상태가 원형 교차로 방식 이며,이 오류 메시지를 알려줍니다. 해당 사용자에 **usagelocation이**할당 되지 않은 합니다. 짐작할 수 있습니다 (나타내는 지역 또는 국가 여기서 사용자 일반적으로 사용 하 여 Office 365) **usagelocation이** 속성은 매우 중요 합니다. 이유는 무엇입니까? 이것은 사용자가 거주 하는 위치에 구매한 라이선스 팩에만 아니라 사용자에 게 제공 되는 서비스에 따라 달라 집니다 때문: 로컬 규칙 및 규정으로 인해 일부 서비스 하지 못할 수 일부 사용자에 게 있습니다. 사용자 **usagelocation이**없으면 Office 365에 있는 서비스는 해당 사용자에 게 법적으로 노출 될 수 있습니다를 알 수 없습니다. 따라서 Office 365 수 없는 서비스를 제공 모든 해당 사용자에 게 최소한 하지 **usagelocation이** 지정 되었습니다.
  
> [!NOTE]
> 사용자 계정을 구성 하는 경우 사실이 알게됩니다 즉시 전세계의 지정한 부분에 관련 된 모든 사용권 제한이 없습니다. 예: 이란을 허가 된 사용자에 대 한 **usagelocation이** 변경 하는 경우 ( `IR`),이 오류 메시지와 함께 명령이 실패 합니다: `Set-MsolUser : Unable to update license for this user. One or more of the assigned service plans is not available in this user's country. Prohibited Service Plans: EXCHANGE_S_ENTERPRISE, SHAREPOINTENTERPRISE, SHAREPOINTWAC, MCOSTANDARD, OFFICESUBSCRIPTION, RMS_S_ENTERPRISE. Specific service plans can be disabled for a user by using the licenseoptions parameter.`> Office 365 이란의 사용자에 게 현재 사용할 수 없는 때문입니다. 자세한 내용은 [라이선스 제한에 대 한](https://go.microsoft.com/fwlink/p/?LinkId=691730)참조입니다. 참고로, Office 365 표준화 (ISO)에 대 한 국제 조직에서 생성 된 두 문자로 된 국가 코드를 사용 합니다. [ISO 웹사이트](https://go.microsoft.com/fwlink/p/?LinkId=84073)에 해당 코드를 찾을 수 있습니다. 
  
확인 하려는 경우 특정된 사용자에 게 **UsageLocation** 이 예와 비슷한 명령을 사용할 수 있습니다.
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.com" | Select-Object UsageLocation
```

또는이 명령을 사용 하 여 **usagelocation이** 없는 모든 사용자 목록을 반환할 수 있습니다.
  
```
Get-MsolUser -All | Where-Object {$_.UsageLocation -eq $null}
```

> [!NOTE]
> 라이선스를 사용자에 게 할당할 때 해당 사용자가, 기본적으로 액세스 권한이 부여 조직에 대 한 액세스를 하는 모든 Office 365 서비스에 있습니다. 예, Office 365 Enterprise E3에 대 한 라이선스를 구입 하는 경우 새로 사용 허가 된 사용자 자동으로 부여할 Exchange Online, Skype와 같은 서비스에 대 한 액세스 비즈니스 온라인 상태이 고 SharePoint Online에 대 한 합니다. 이러한 서비스에 대 한 사용자의 액세스를 제한 하려는 ( *하지* 있지만 SharePoint Online에 액세스할 수 있도록 사용자를 사용할 수 등 Exchange Online 및 비즈니스 온라인 용 Skype) 한 다음 Office 365 서비스에 대 한 액세스 불가 [문서를 참조 PowerShell](disable-access-to-services-with-office-365-powershell.md)합니다. 
  
## <a name="new-to-office-365"></a>Office 365의 새로운 기능

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a>참고 항목
<a name="SeeAlso"> </a>

Office 365 PowerShell을 사용하여 사용자를 관리하는 방법에 대한 다음 추가 항목을 참조하세요.
  
- [Office 365 PowerShell을 사용 하 여 사용자 계정 만들기](create-user-accounts-with-office-365-powershell.md)
    
- [삭제 한 사용자 계정 Office 365 PowerShell을 사용 하 여 복원 합니다.](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [블록 사용자 계정 Office 365 PowerShell을 사용 하 여](block-user-accounts-with-office-365-powershell.md)
    
- [Office 365 PowerShell을 사용 하 여 사용자 계정에서 라이센스를 제거 합니다.](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
이 항목에서 사용된 cmdlet에 대한 자세한 내용은 다음 항목을 참조하십시오.
  
- [Get-msolaccountsku](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [Set-msoluserlicense](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [ForEach-Object](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [선택 개체](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

