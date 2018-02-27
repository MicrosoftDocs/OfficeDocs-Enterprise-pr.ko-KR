---
title: "Office 365 PowerShell을 사용 하 여 허가 된 / 허가 되지 않은 사용자 보기"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: O365ITProTrain, Ent_Office_Other, PowerShell
ms.assetid: e4ee53ed-ed36-4993-89f4-5bec11031435
description: "사용 하는 방법에 설명 Office 365 PowerShell 허가 된 / 허가 되지 않은 사용자 계정을 볼 수 있습니다."
ms.openlocfilehash: e691ba7db96b34166f03ccd90d87fee0d2ee09f8
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/13/2018
---
# <a name="view-licensed-and-unlicensed-users-with-office-365-powershell"></a>Office 365 PowerShell을 사용 하 여 허가 된 / 허가 되지 않은 사용자 보기

**요약:** Office 365 PowerShell을 사용하여 허가되거나 허가되지 않은 사용자 계정을 확인할 수 있습니다.
  
Office 365 조직의 사용자 계정에 조직에서 사용할 수 있는 라이선싱 계획의 사용 가능한 라이선스가 일부 또는 모두 할당되어 있거나 하나도 할당되어 있지 않을 수 있습니다. Office 365 PowerShell을 사용하여 조직에서 사용이 허가되었거나 허가되지 않은 사용자를 빠르게 찾을 수 있습니다.
  
## <a name="before-you-begin"></a>시작하기 전에

- 이 항목의 절차를 수행하려면 Office 365 PowerShell에 연결되어 있어야 합니다. 지침을 보려면 [PowerShell Office 365에 연결](connect-to-office-365-powershell.md)을 참조하세요.
    
- _-All_ 매개 변수를 사용하지 않고 **Get-MsolUser** cmdlet을 사용하는 경우 처음 500개의 계정만 반환됩니다.
    
## <a name="the-short-version-instructions-without-explanations"></a>간략 한 (설명 없이 지침)

이 섹션에서는 부풀려졌거나 불필요한 설명 없이 절차를 제공합니다. 질문이 있거나 자세한 내용을 원할 경우 항목의 나머지 부분을 읽을 수 있습니다.
  
조직의 모든 사용자 계정 및 라이선스 상태 목록을 보려면 Office 365 PowerShell에서 다음 명령을 실행하세요.
  
```
Get-MsolUser -All
```

조직의 모든 허가 되지 않은 사용자 계정 목록을 보려면 다음 명령을 실행 합니다.
  
```
Get-MsolUser -All -UnlicensedUsersOnly
```

전체 목록을 보려면 다음 명령을 실행 하 여 조직에 있는 사용자 계정의 라이센스:
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true}
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a>긴 버전 (명령에 대 한 세부 정보)

Office 365 사용자 계정 및 Office 365 라이선스는 일대일로 맞출 필요가 없습니다. Office 365 사용자에게 Office 365 라이선스가 없을 수도 있고 사용자에게 할당되지 않은 Office 365 라이선스가 있을 수도 있습니다. 실제로 단일 사용자 계정에서 *여러* Office 365 라이선스를 보유할 수도 있습니다. 새 Office 365 사용자 계정을 만들 경우(자세한 내용은[ Windows PowerShell을 통해 Office 365 사용자에게 라이선스 할당](http://technet.microsoft.com/library/0ab9fcac-e5ea-4b5b-b72c-8c92c55565ac.aspx) 문서 참조) 해당 사용자에게 라이선스를 할당할 필요가 없습니다. 이 경우 새 사용자는 유효한 계정이 있지만 Office 365에 로그인할 수 없습니다. 로그인을 시도하면 다음과 유사한 메시지가 나타납니다.
  
![유효한 Office 365 라이선스가 없는 사용자](images/o365_powershell_no_license.png)
  
마찬가지로 유급 휴가나 출산 휴가 등 일정 기간 휴직할 사용자가 있을 수 있습니다. 이 경우 해당 사용자의 사용자 계정을 그대로 유지한 채(즉, 주소, 휴대폰 번호 등의 모든 속성 값을 그대로 유지) 라이선스를 제거할 수 있습니다. 그런 다음 해당 라이선스를 다른 사용자(즉, 해당 사용자 대신 업무에 투입된 임시 작업자)에게 할당할 수 있습니다. 사용자가 복귀하면 새 라이선스를 발급하여 이전처럼 작업을 재개할 수 있습니다.
  
이는 계정이 있지만 라이선스가 없는 사용자를 유지할 수 있으며 그 반대의 경우도 가능함을 의미합니다.
  
[Office 365 PowerShell을 사용하여 라이선스 및 서비스 보기](view-licenses-and-services-with-office-365-powershell.md) 문서에서는 조직이 구매한 Office 365 라이선스 수와 사용자에게 할당된 라이선스 수를 를 확인하는 방법과 사용자에게 할당된 해당 라이선스의 수를 확인하는 방법을 설명합니다. 이것은 중요한 정보입니다. 이러한 라이선스가 할당된 사용자와 할당되지 않은 사용자를 파악하는 것도 마찬가지로 중요합니다. 또한 이 문서에서는 이러한 정보를 확인하는 방법도 알려줍니다.
  
아시다시피 **Get-MsolUser** cmdlet은 모든 Office 365 사용자 계정에 대한 정보를 반환합니다. 모든 Office 365 사용자에 대한 정보를 빠르게 확인하고 싶나요? 그렇다면 Office 365 PowerShell에서 다음 명령을 실행하세요.
  
```
Get-MsolUser
```

그러면 Get-MsolUser에서 다음과 유사한 데이터를 반환합니다.
  
```
UserPrincipalName           DisplayName                     isLicensed
-----------------           -----------                     ----------
ZrinkaM@litwareinc.com      Zrinka Makovac                  True
BelindaN@litwareinc.com     Belinda Newman                  False
BonnieK@litwareinc.com      Bonnie Kearney                  True
FabriceC@litwareinc.com     Fabrice Canel                   True
AnneW@litwareinc.com        Anne Wallace                    True
AlexD@litwareinc.com        Alex Darrow                     True
```

위 예에서 볼 수 있듯이 반환된 속성 값 중 하나에 **isLicensed** 속성 값이 있습니다. **isLicensed**가 `False`와 같은 경우 이는 사용자에게 Office 365에 대한 라이선스가 없음을 의미합니다. 따라서 필요한 경우 사용자 목록을 스크롤하여 **isLicensed** 속성이 `False`로 설정된 사용자를 선택할 수 있습니다.
  
사용자 목록을 스크롤하여 라이선스가 없는 사용자를 선택하는 작업은 사용자 수가 비교적 적은 경우에 효과적입니다. 그러나 사용자 수가 많은 경우에는 목록을 스크롤하는 것이 매우 지루한 작업이 될 것입니다. 또한 Windows PowerShell이 구성된 방식에 따라 스크롤이 불가능할 수도 있습니다. Windows PowerShell 콘솔에 한 번에 표시할 수 있는 출력 줄 수에는 제한이 있기 때문입니다.
  
이 점을 염두에 둔다면 라이선스가 없는 사용자를 나열하는 방법은 스크롤 대신 다음 명령을 실행하는 것이 훨씬 효과적입니다.
  
```
Get-MsolUser -UnlicensedUsersOnly
```

이 명령은 Office 365에 대한 라이선스가 없는 사용자만 반환합니다. 위의 명령이 반환하는 결과는 다음과 같습니다.
  
```
UserPrincipalName           DisplayName                     isLicensed
-----------------           -----------                     ----------
BelindaN@litwareinc.com     Belinda Newman                  False
```

라이선스가 없는 사용자가 한 명임을 알 수 있습니다. 그렇다면 우리에게 *라이선스가 있는* 사용자의 목록만 필요하다면 어떻게 될까요? 이러한 경우라고 해도 아주 약간 더 복잡해질 뿐입니다.
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true}
```

이 명령은 **isLicensed** 속성이 `True`인 모든 사용자 계정을 찾으며 다음과 비슷한 정보를 반환합니다.
  
```
UserPrincipalName           DisplayName                     isLicensed
-----------------           -----------                     ----------
ZrinkaM@litwareinc.com      Zrinka Makovac                  True
BonnieK@litwareinc.com      Bonnie Kearney                  True
FabriceC@litwareinc.com     Fabrice Canel                   True
AnneW@litwareinc.com        Anne Wallace                    True
AlexD@litwareinc.com        Alex Darrow                     True
```

확인할 수 있는 것처럼 Belinda Newman의 정보는 반환되지 않습니다. 그 이유는 해결하려면 Belinda 계정의 **isLicensed** 속성이 `True`로 설정되어 있지 않기 때문입니다.
  
## <a name="see-also"></a>참고 항목
<a name="SeeAlso"> </a>

이 항목에서 사용된 cmdlet에 대한 자세한 내용은 다음 항목을 참조하십시오.
  
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

