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
ms.custom:
- O365ITProTrain
- Ent_Office_Other
- DecEntMigration
- PowerShell
ms.assetid: e4ee53ed-ed36-4993-89f4-5bec11031435
description: "사용이 허가 된 및 허가 되지 않은 사용자 계정을 보려면 Office 365 PowerShell을 사용 하는 방법에 설명 합니다."
ms.openlocfilehash: aa8c38864f3abf98f1aa5c8149db08506c6f7668
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2017
---
# <a name="view-licensed-and-unlicensed-users-with-office-365-powershell"></a>Office 365 PowerShell을 사용 하 여 허가 된 / 허가 되지 않은 사용자 보기

**요약:** 사용이 허가 된 및 허가 되지 않은 사용자 계정을 보려면 Office 365 PowerShell을 사용 하는 방법에 설명 합니다.
  
Office 365 조직에서 사용자 계정은 일부 또는 전체를, 조직에서 사용할 수 있는 라이선스 계획에서 자신에 게 할당 된 사용 가능한 라이선스의 none에 있을 수 있습니다. Office 365 PowerShell 신속 하 게 찾을 사용이 허가 된 및 허가 되지 않은 사용자가 조직에서 사용할 수 있습니다.
  
## <a name="before-you-begin"></a>시작하기 전에

- 이 항목의 절차에서는 Office 365 PowerShell에 연결 해야 합니다. 자세한 내용은 [Office 365 PowerShell 연결](connect-to-office-365-powershell.md)을 참조 하십시오.
    
- 사용 하지 않고 **Get-msoluser** cmdlet을 사용 하는 경우는 _-모든_ 매개 변수를 처음 500 개 계정만 반환 됩니다.
    
## <a name="the-short-version-instructions-without-explanations"></a>간략 한 (설명 없이 지침)

이 섹션에서는 선전과 또는 불필요 한 설명 없이 절차를 제공 합니다. 질문이 더 많은 정보를 원하는 경우에 항목의 나머지 부분을 읽을 수 있습니다.
  
조직에서 모든 사용자 계정 및 라이선스 상태의 목록을 보려면 Office 365 PowerShell에서 다음 명령을 실행 합니다.
  
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

Office 365 사용자 계정 및 Office 365 라이선스의 일대일 해야: Office 365 사용자는 Office 365 라이선스 없는 하는 것이 불가능 하 고 사용자에 게 할당 하지 않은 Office 365 라이선스를 보유 하는 것이 불가능 합니다. (실제로 단일 사용자 계정도 수도 *여러* Office 365 라이선스.) 만들 때 새 Office 365 사용자 계정 (자세한 내용은 [Windows PowerShell을 사용한 Office 365 라이선스 사용자가](http://technet.microsoft.com/library/0ab9fcac-e5ea-4b5b-b72c-8c92c55565ac.aspx) 문서를 참조) 하면 해당 사용자에 게 라이선스 할당 하지 않아도: 새 사용자에 게 사용자는 유효한 계정이 되지만 없게가 자신이 및에 로그인 할 수 없습니다 ce 365 합니다. 로그인 하려고 할 경우 다음과 비슷한를 볼 수 있습니다.
  
![유효한 Office 365 라이선스가 없는 사용자](images/o365_powershell_no_license.png)
  
마찬가지로, 사용자, 해달라는 sabbatical에 대 한 설정 하거나 해제 maternity/paternity 휴가 대 한 확장 된 시간이 라인는 있을 수 있습니다. 다음과 같은 경우에 사용자의 라이선스를 제거 하지만 사용자 계정을 그대로 두려면 수 있습니다 (즉, 해당 속성 값이 모두, 주소 및 전화 번호 등으로 나가기-은). 수행 하 여 해당 라이선스 (예:, 예: 임시 직원 나가기에 해당 사용자에 대 한 채우기) 다른 사람에 게 할당할 수 있습니다. 작동 하는 사용자를 반환 하는 경우 새 라이선스 발급할 수 하 고 명의 하지 사라졌는지 확인 된 하는 경우에 따라 작업을 다시 시작할 수는 표시 됩니다.
  
있음을 의미 합니다 예, 수 있는 사용자 계정을 갖고 있지만 라이선스가 합니다. 또는 그 반대로 합니다.
  
문서 [보기 라이선스 및 Office 365 PowerShell을 사용 하 여 서비스](view-licenses-and-services-with-office-365-powershell.md) 사용자에 게 할당 된 다양 한 이러한 라이선스 하는 방법에 따라 사용자의 조직도 구입가 Office 365 라이선스의 수를 결정 하는 방법을 설명 합니다. 중요 한 정보입니다. 하지만 중요도, 이러한 라이선스는 할당 된 사용자에 게는 및을 선택할 하지 않은 알고 있으면 됩니다. 이 문서가를 수행 하는 방법을 안내 하 고 있습니다.
  
아시다시피, **Get-msoluser** cmdlet은 모든 Office 365 사용자 계정에 대 한 정보를 반환 합니다. 모든 Office 365 사용자에 대 한 요약 정보 일부 필요 합니까? Office 365 PowerShell에서 다음이 명령을 실행 한 다음.
  
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

볼 수 있듯이 **isLicensed** 속성에 대 한 반환 되는 속성 값 중 하나입니다. **IsLicensed** 같으면 `False` 즉, 사용자가 Office 365에 대 한 라이선스를가 하지 않습니다. 즉, 사용자의 대화 목록 스크롤해야 하 고 선택과 아웃에서는 **isLicensed** 속성으로 설정 하는 경우에 이와 더불어, 있습니다 단순히 및 `False`합니다.
  
비교적 적은 수의 사용자가 서 모든 속도로 작동 하면 라이선스가 없는 사용자를 선택 하는 동안 사용자 목록을 통해 스크롤 합니다. 그러나 많은 수의 사용자가 해당 목록을 스크롤할 수, 최고, 매우 번거로운 일입니다. (하 고, Windows PowerShell에 구성 된 방법부터 완전히 아마도 불가능에 따라 합니다. 없기 때문입니다 한번에 Windows PowerShell 콘솔에 표시 될 수 있는 출력의 줄 수에 제한이.)
  
이 점을 염두에 둔다면 라이선스가 없는 사용자를 나열하는 방법은 스크롤 대신 다음 명령을 실행하는 것이 훨씬 효과적입니다.
  
```
Get-MsolUser -UnlicensedUsersOnly
```

해당 명령에는 Office 365에 대 한 라이선스가 없는 사용자만 반환 합니다. 즉:
  
```
UserPrincipalName           DisplayName                     isLicensed
-----------------           -----------                     ----------
BelindaN@litwareinc.com     Belinda Newman                  False
```

볼 수 있듯이 허가 되지 않은 사용자가 한 명 했습니다. 이며는 *사용이 허가 된* 사용자의 목록을 표시 하는 전용? 작은 약간 더 복잡 하지만 아무리 비트만 없습니다.
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true}
```

해당 명령 하는 모든 사용자 계정에 대 한 **isLicensed** 속성이 같은 `True`,이 비슷한 정보를 반환 합니다.
  
```
UserPrincipalName           DisplayName                     isLicensed
-----------------           -----------                     ----------
ZrinkaM@litwareinc.com      Zrinka Makovac                  True
BonnieK@litwareinc.com      Bonnie Kearney                  True
FabriceC@litwareinc.com     Fabrice Canel                   True
AnneW@litwareinc.com        Anne Wallace                    True
AlexD@litwareinc.com        Alex Darrow                     True
```

볼 수 있듯이 Belinda Newman에 대 한 정보가 반환 되지 않습니다. 왜 안 돼요? 맞습니다: Belinda의 계정에 대 한 **isLicensed** 속성은로 설정 하지 않으므로 `True`합니다.
  
## <a name="see-also"></a>See also
<a name="SeeAlso"> </a>

이 항목에서 사용된 cmdlet에 대한 자세한 내용은 다음 항목을 참조하십시오.
  
- [Get-msoluser](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [Where-object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

