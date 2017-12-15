---
title: "Office 365 PowerShell을 사용해야 하는 이유"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- DecEntMigration
ms.assetid: b3209b1a-40c7-4ede-8e78-8a88bb2adc8a
description: "요약: Office 365 PowerShell를 사용 하 여 Office 365를 관리, 일부 경우에 효율적이 고 또 어떤 경우에 필요에 의해 해야 이유를 이해 합니다."
ms.openlocfilehash: 46295ed851f24b16f775fd48dc8cdfbce39bf76c
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2017
---
# <a name="why-you-need-to-use-office-365-powershell"></a>Office 365 PowerShell을 사용해야 하는 이유

 **요약:** Office 365 PowerShell를 사용 하 여 Office 365를 관리, 일부 경우에 효율적이 고 또 어떤 경우에 필요에 의해 해야 이유를 이해 합니다.
  
Office 365 관리 센터와 하지만 관리할 수 Office 365 사용자 계정 및 라이선스 있지만 Office 365 서버 제품을 관리할 수 있습니다: Exchange, 비즈니스 온라인 상태이 고 SharePoint Online 용 Skype 합니다. 그러나 관리할 수도 있습니다 Office 365 PowerShell 명령으로 이러한 요소 속도, 자동화 및 추가 기능에 대 한 명령줄 및 스크립팅 언어 환경을 활용 합니다.
  
이 문서에서는 Office 365를 관리 하려면 Office 365 PowerShell를 사용할 수 있는 다음과 같은 방법이으로 살펴보겠습니다.
  
- Office 365 PowerShell Office 365 관리 센터를 볼 수 없습니다는 추가 정보를 표시할 수 있습니다.
    
- Office 365에는 Office 365 PowerShell로만 구성할 수 있는 기능이 있습니다.
    
- Office 365 PowerShell은 대량 작업 수행에 뛰어난
    
- Office 365 PowerShell은 데이터를 필터링하는 데 유용함
    
- Office 365 PowerShell을 사용하면 데이터 쉽게 인쇄 또는 저장할 수 있음
    
- Office 365 PowerShell을 사용하여 여러 서버 제품을 관리할 수 있음
    
시작 하기 전에 Office 365 PowerShell는 Windows PowerShell, Windows 기반 서비스 및 플랫폼에 대 한 명령줄 환경에 대 한 모듈의 집합을 이해 합니다. 이 환경 추가 모듈 확장할 수 있는 명령 셸 언어를 만들고 Office 365 PowerShell 모듈을 설치 하 고 Office 365에 연결 후 단순 또는 복잡 한 명령 또는 스크립트를 등 실행할 수 있는 방법을 제공합니다 구독, Microsoft Exchange Online에 대 한 모든 사용자 사서함을 목록을 표시 하려면이 명령을 실행할 수 있습니다.
  
```
Get-Mailbox
```

또한 모든 페이지의 모든 SharePoint Online에서 웹 응용 프로그램의 모든 사이트에 대 한 목록에서 항목의 수를 계산 하려면이 명령을 실행할 수 있습니다.
  
```
Get-SPOSite -Limit All | Get-SPWeb -Limit All | % {$_.Lists} | ? {$_ -is [Microsoft.SharePoint.SPDocumentLibrary]} | % {$total+= $_.ItemCount}; $total
```

사서함 수 있는 목록이도 사용 하 여 Office 365 관리 센터를 사용 하 여 쉽게 수행 되지만 모든 페이지의 모든 웹 응용 프로그램의 모든 사이트에 대 한 목록에서 항목의 수를 계산 될 수는 없습니다 쉽게 수행할 수 있습니다.
  
Office 365 PowerShell을 확대 하 고 Office 365 관리 센터 대신 Office 365를 관리 하 여 기능을 향상 하도록 설계 되는 note 하십시오. Office 365 관리자로 적어도 Office 365 PowerShell 명령으로만 수행할 수 있는 일부 구성 절차 있기 때문에 Office 365 PowerShell을 사용 하 여 능숙 하 게 될 해야 합니다. 이러한 경우 해야 합니다 이해 하는 방법:
  
- (각 관리자 컴퓨터에 대해 한번만 수행 됨) 하 여 Office 365 PowerShell 모듈을 설치 합니다.
    
- Office 365 구독 (각 PowerShell 세션에 대해 한번 수행 됨)에 연결 합니다.
    
- 필요한 Office 365 PowerShell 명령을 실행 하는 데 필요한 정보를 수집 합니다.
    
- Office 365 PowerShell 명령을 성공적으로 실행 합니다.
    
이러한 기본 기술을 학습을 한 후 **Get-mailbox** 명령 사용 하 여 사서함 사용자를 나열 하려면 필요 하지는 또는 모두에 대 한 모든 사이트에 대 한 모든 목록에 있는 모든 항목을 개수를 이전 것과 같은 새 명령 만들기 하는 방법을 이해 하는데 필요한는  웹 응용 프로그램입니다. Microsoft 및 커뮤니티의 Office 365 관리자 도와주는 필요에 따라 합니다.
  
## <a name="office-365-powershell-can-reveal-additional-information-that-you-cannot-see-with-the-office-365-admin-center"></a>Office 365 PowerShell Office 365 관리 센터를 볼 수 없습니다는 추가 정보를 표시할 수 있습니다.
<a name="reveal"> </a>

많은 유용한 정보를 표시 하는 Office 365 관리 센터 하지만 Office 365 사용자, 라이선스, 사서함 및 사이트에 저장 하는 모든 정보를 표시 하는 것을 의미 하지는 않습니다. **사용자 및 그룹에서** Office 365 관리 센터에 대 한 예는 다음과 같습니다.
  
![Office 365 관리 센터의 사용자 및 그룹 표시 예제입니다.](images/o365_powershell_users_and_groups.png)
  
다양 한 용도로 알아두어야 할 정보가 표시 됩니다. 그러나 더 필요한 경우 경우가 있습니다. 예 (사용자에 게 제공 되는 Office 365 기능)와 Office 365 라이선스에 따라 달라 집니다 부분적으로 해당 사용자의 지리적 위치입니다. 정책 및 사용자에 게는 미국에 거주 하 고 확장할 수 기능 아닐 수 있습니다는 동일 정책 및 기능을 사용자에 게 벨기에 또는 인도에 거주 하 고 확장할 수 있습니다. 다음이 단계와 사용자의 지리적 위치를 확인 하는 Office 365 관리 센터를 사용할 수 있습니다.
  
1. 사용자의 **표시 이름**을 두번클릭 합니다.
    
2. 사용자 속성에서 창을 표시 하 고 **자세히**를 클릭 합니다.
    
3. 세부 정보 표시에서 **추가 정보**를 클릭 합니다.
    
4. **국가 또는 지역**제목이 나타날 때까지 아래로 스크롤하십시오.
    
     ![Office 365 관리 센터의 사용자에 대한 지역 정보 예제입니다.](images/o365_powershell_usage_location.png)
  
5. 사용자의 종이에서 이름 및 위치 표시 또는 복사 하 여 메모장에 붙여넣습니다를 작성 합니다. 
    
각 사용자에 대해이 절차를 반복 해야 합니다. 많은 사용자 들이 번거로운 작업 수 있습니다. Office 365 powershell 모든 다음 명령 사용 하 여 사용자에 대 한이 정보를 표시할 수 있습니다.
  
```
Get-MsolUser | Select DisplayName, UsageLocation
```

> [!NOTE]
> 이 명령을 사용 하면 [Windows Azure Active Directory 모듈](https://technet.microsoft.com/en-us/library/jj151815.aspx)을 설치 해야 합니다. 
  
다음과 같은 화면이 표시됩니다.
  
```
DisplayName                               UsageLocation
-----------                               -------------
Zrinka Makovac                            US
Bonnie Kearney                            GB
Fabrice Canel                             BR
Brian Johnson (TAILSPIN)                  US
Anne Wallace                              US
Alex Darrow                               US
David Longmuir                            BR
```

> [!TIP]
>  이 Office 365 PowerShell 명령의 해석: 현재 Office 365 구독 ( **Get-msoluser** )를에서 확인할 수 있는 모든 사용자 하지만 이름 및 ( **선택 DisplayName, UsageLocation** )의 각 사용자에 대 한 위치를 표시 합니다.
  
Office 365 PowerShell 명령 셸 언어를 지원 하므로 **Get-msoluser** 명령에서 얻은 정보를 추가로 조작할 수 있습니다. 예, 해야하는 경우도 있습니다 자신의 등 위치와 함께 모든 브라질 사용자, 모든 미국, 대한민국 사용자를 함께 그룹화 하 여 이러한 사용자를 정렬 합니다. 명령은 다음과 같습니다.
  
```
Get-MsolUser | Select DisplayName, UsageLocation | Sort UsageLocation, DisplayName
```

다음과 같은 화면이 표시됩니다.
  
```
DisplayName                                 UsageLocation
-----------                                 -------------
David Longmuir                              BR
Fabrice Canel                               BR
Bonnie Kearney                              GB
Alex Darrow                                 US
Anne Wallace                                US
Brian Johnson (TAILSPIN)                    US
Zrinka Makovac                              US
```

> [!TIP]
>  이 Office 365 PowerShell 명령의 해석: 현재 Office 365 구독을 확인할 수 있는 모든 사용자가 있지만 이름 및 각 사용자에 대 한 위치를 표시 하 고 해당 위치 및 이름 ( **정렬 usagelocation이 하 여 먼저 정렬 DisplayName** ).
  
추가 필터링을 사용할 수도 있습니다. 예를 들어 브라질 사용자에 대한 정보만 표시하려면 다음 명령을 사용합니다.
  
```
Get-MsolUser | Where {$_.UsageLocation -eq "BR"} | Select DisplayName, UsageLocation 
```

다음과 같은 화면이 표시됩니다.
  
```
DisplayName                                           UsageLocation
-----------                                           -------------
David Longmuir                                        BR
Fabrice Canel                                         BR
```

> [!TIP]
>  이 Office 365 PowerShell 명령의 해석: 브라질 위치가 현재 Office 365 구독을 확인할 수 있는 모든 사용자 ( **여기에서 {$\_합니다. UsageLocation-eq "b R"}** ), 이름 및 각 사용자에 대 한 위치를 표시 합니다.
  
 **대규모 도메인 관련 참고 사항**
  
매우 많은 수의 사용자와 매우 큰 도메인을 사용 하는 경우이 문서의 내용을 다룹니다 예 중 일부는 동안 발생할 수 있습니다 "제한 합니다." 약간 수행 하려는 컴퓨팅 성능 및 사용 가능한 네트워크 대역폭 등의 작업을 기초로 하는 의미를 너무 많이 한번에 있습니다. 따라서 대규모 조직에서는 두 명령으로이 Office 365 PowerShell 명령 중 일부를 분할 하려고 수 있습니다. 예, 하나의 명령 모든 사용자 계정 하 고 각각에 대 한 위치와 이름을 표시를 반환 합니다.
  
```
Get-MsolUser | Select DisplayName, UsageLocation
```

더 작은 도메인에 대 한 간단 하 게 합니다. 그러나 대규모 조직에서는 해야할 수 있습니다 두 명령으로 분할 하는: 변수 및 다른 사용자 계정 정보를 저장 하는 하나의 명령 필요한 정보를 표시 하는 명령입니다. 다음은 한 예가입니다.
  
```
$x = Get-MsolUser
$x | Select DisplayName, UsageLocation
```


이 Office 365 PowerShell 명령이 집합의 해석이 됩니다.
- 변수 $ $x에서에서 정보를 저장 하 고 현재 Office 365 구독을 확인할 수 있는 모든 사용자 ( **$x Get-msoluser =** ).
- 변수 $x의 콘텐츠를 표시 하지만 각 사용자에 대 한 위치와 이름을 포함 ( **$x | DisplayName, usagelocation이 선택** ).
  
## <a name="office-365-has-features-that-you-can-only-configure-with-office-365-powershell"></a>Office 365는 Office 365 powershell을 통해서만 구성할 수 있는 기능
<a name="only"> </a>

Office 365 관리 센터는 대부분의 사용자에 적용 되는 가장 일반적인 또는 의미 있는 관리 작업에 대 한 액세스를 제공 하기 위한 것입니다. 즉, Office 365 관리 센터 일반적인 관리자는 가장 일반적인 관리 작업을 수행 하기 위해이 도구를 사용할 수 있도록 디자인 되었습니다. 이 정의 하 여 Office 365 관리 센터를 사용 하 여 완료할 수 없는 일부 작업은 의미 합니다.
  
예, Skype 비즈니스 온라인 관리 센터에 대 한 사용자 지정 모임 초대를 만들기 위한 몇가지 옵션을 제공 합니다.
  
![비즈니스용 Skype Online 관리 센터에 표시된 사용자 지정 모임 초대 예제입니다.](images/o365_powershell_meeting_invitation.png)
  
이러한 설정을 사용 하 여 모임 초대를 전문적으로 개인 터치를 추가할 수 있습니다. 그러나 방법이에 모임 구성 설정 단순히 사용자 지정 모임 초대를 만들 때 보다 더 많은입니다. 예, 기본적으로 모임 허용 합니다.
  
- 익명 사용자가 각 모임에 자동으로 입장할 수 있도록 설정
    
- 참석자가 모임을 기록하도록 설정
    
- 조직의 모든 사용자가 모임 참가 시 발표자로 지정되도록 설정
    
이러한 설정은 Skype 비즈니스 온라인 관리 센터에서 사용할 수 없습니다. 그러나 Office 365 PowerShell에서 해당을 제어할 수 있습니다. 이러한 세 설정을 사용 하지 않도록 설정 하는 명령은 다음과 같습니다.
  
```
Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $False -AllowConferenceRecording $False -DesignateAsPresenter "None"
```

> [!NOTE]
> 이 명령은 [비즈니스 온라인 PowerShell 모듈에 대 한 Skype ](https://www.microsoft.com/download/details.aspx?id=39366)를 설치 해야 합니다. 
  
> [!TIP]
>  이 Office 365 PowerShell 명령의 해석: 비즈니스 온라인 모임 ( **Set-csmeetingconfiguration** )에 대 한 새 Skype에 대 한 설정에 대해 사용 하지 않도록 설정 익명 사용자를 모임에 자동 입장할 수 있도록 허용 ( **- AdmitAnonymousUsersByDefault $False** ), 모임 기록을 ( **-AllowConferenceRecording $False** ) 참석자에 대 한 기능을 사용 하지 않도록 설정 하 고 조직에서 모든 사용자를 발표자로 지정 하지 않으면 ( **-DesignateAsPresenter "None"** ).
  
생각이 바뀌어 이러한 기본 설정을 복원하려면(모두 사용하도록 설정) 다음 명령을 실행합니다.
  
```
Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $True -AllowConferenceRecording $True -DesignateAsPresenter "Company"
```

이것은 한 예입니다. 경우 다른 사용자를 Office 365 관리자로 해야하는와 Office 365 PowerShell 명령을 실행 하 여 능숙 하 게 하는 이유는
  
## <a name="office-365-powershell-is-great-at-carrying-out-bulk-operations"></a>Office 365 PowerShell은 대량 작업을 수행하는 데 유용함
<a name="bulk"> </a>

과거에 대 한 단일 작업 수행에 있는 경우 Office 365 관리 센터와 같은 시각적 인터페이스는 가장 중요 한입니다. 등 사용자 계정 하나를 사용 하지 않도록 설정 해야하는 경우 신속 하 게 찾아 확인란의 선택을 취소 하는 Office 365 관리 센터를 사용할 수 있습니다. 이 경우 Office 365 PowerShell에서 유사한 작업을 실행 하는 보다 간단한 수 있습니다.
  
하지만 시간의 효과적인 사용을 많은 작업 또는 문서에서 다른 대형 집합 내에서 선택 된 일부 작업을 변경 하는 경우 Office 365 관리 센터 수 없습니다. 예, 다양 한 전화번호에 접두사를 변경 해야 했습니다 표현 하자면 모든 SharePoint Online 사이트에서 Ken Myer 특정 사용자를 제거 하는 데 필요한 경우 어떻게 해야 할까요 하는 Office 365 관리 센터에서?
  
후자의 예제에 대 한 여러 백 SharePoint Online 사이트 있고 모르는 선택할 것을 알지 Ken: Meyer은 구성원의 합니다. 즉, Office 365 관리 센터에서 시작 하 고 다음 각 사이트에 대해이 절차를 수행 해야 합니다.
  
1. 사이트의 **URL** 을 클릭 합니다.
    
2. **사이트 모음 속성** 상자에서 사이트 열 **웹사이트 주소** 링크를 클릭 합니다.
    
3. 해당 사이트에서 **공유**를 클릭 합니다.
    
4. **공유** 대화 상자에서 사이트에 대 한 사용 권한이 있는 모든 사용자를 표시 하는 링크를 클릭 합니다.
    
     ![SharePoint Online 관리 센터에서 SharePoint Online 사이트의 구성원을 보는 예제입니다.](images/o365_powershell_view_permissions.png)
  
5. **사용자와 공유** 대화 상자에서 **고급**을 클릭 합니다.
    
6. 사용자의 목록을 아래로 스크롤합니다 하 Ken Myer (사이트에 권한이 있다고 가정함)를 찾아 선택한 다음 **사용자의 사용 권한 제거**를 클릭 합니다.
    
수백 개의 사이트의 경우 시간이 오래 걸릴 수 있습니다.
  
모든 사이트에서 Ken Myer를 제거 하려면 Office 365 PowerShell 하 고 다음 명령을 사용 하 여 것입니다.
  
```
Get-SPOSite | ForEach {Remove-SPOUser -Site $_.Url -LoginName "kenmyer@litwareinc.com"}
```

> [!NOTE]
> 이 명령은 [SharePoint Online PowerShell 연결](https://technet.microsoft.com/library/fp161372.aspx)를 설치 해야 합니다. 
  
> [!TIP]
>  이 Office 365 PowerShell 명령의 해석: 현재 Office 365 구독 ( **Get-sposite** )에서 SharePoint 사이트의 모든 가져오고 각 사이트에 대 한 Ken: Meyer 것 ( **ForEach {Remove-spouser-액세스할 수 있는 사용자의 목록에서 제거 $ 사이트\_합니다. Url-LoginName "kenmyer@litwareinc.com"}** ).
  
Ken: Meyer는가 액세스 권한이 없는 포함 하 여 모든 사이트에서 제거 하려면 Office 365를 알려주는 우리 때문에이 명령이 표시는가 현재 대 한 액세스 권한이 해당 사이트에 대 한 오류가 표시 됩니다. 그에 게 자신의 로그인 목록에 있는 사이트 에서만에서 키: Meyer를 제거 하려면 조건을 추가로이 명령에서 사용할 수 있지만 나열된 된 오류 사이트 자체에 나쁜 영향을 미치지 않습니다. Office 365 관리자를 통해 작업의 시간 센터 보다는이 명령에는 수백 개의 사이트에 대해 실행할 몇 분정도 걸릴 수 있습니다.
  
다른 대량 작업의 예제는 다음과 같습니다. 이 명령을 사용하여 새 SharePoint 관리자인 Bonnie Kearney를 조직의 모든 사이트에 추가합니다.
  
```
Get-SPOSite | ForEach {Add-SPOUser -Site $_.Url -LoginName "bkearney@litwareinc.com" -Group "Members"}
```

> [!TIP]
>  이 Office 365 PowerShell 명령의 해석:을 모두 활용할 수 있는 SharePoint 사이트의 현재 Office 365 구독에서 하 고 각 사이트에 대 한, 사용자 로그인 이름 사이트의 Members 그룹에 추가 하 여 Bonnie Kearney 대 한 액세스를 허용 ( **ForEach {Add-spouser-사이트 $\_. Url-LoginName "bkearney@litwareinc.com"-그룹 "구성원"}** ).
  
## <a name="office-365-powershell-is-great-at-filtering-data"></a>Office 365 PowerShell은 데이터를 필터링하는 데 유용함
<a name="filter"> </a>

Office 365 관리 센터를 신속 하 게 데이터를 필터링 하 고 정보를 대상으로 지정 된 하위 집합을 손쉽게 찾을 다양 한 방법을 제공 합니다. 등 Exchange 쉽게 필터를 사용자 사서함의 모든 속성에 것이 더 실용적입니다. 예, 도시의 Bloomington에 거주 하는 모든 사용자에 대 한 사서함 목록이 같습니다.
  
![Bloomington 시에 거주하는 모든 사용자의 사서함 목록에 대해 Office 365 관리 센터에서 고급 검색을 수행하는 예제입니다.](images/o365_powershell_advanced_search.png)
  
Exchange 관리 센터 필터 조건을 결합할 수 있습니다. 예, Bloomington에 거주 하 고 Finance 부서에서 근무 하는 모든 사용자에 대 한 사서함을 찾을 수 있습니다. 
  
그러나 Exchange 관리 센터에서 수행할 수 있는 작업에 제한이 있습니다. 예, 해야하는 경우도 있습니다 Bloomington에 거주 하지 않는 모든 사용자에 대 한 Bloomington 또는 San 디에고에 거주 하는 사용자의 사서함 또는 사서함을 찾을 수 있습니다. 
  
Office 365 powershell이 명령 사용 하 여 Bloomington 또는 김해시 도시에 거주 하는 모든 사용자에 대 한 사서함 목록을 인증할 수 있습니다.
  
```
Get-User | Where {$_.RecipientTypeDetails -eq "UserMailbox" -and ($_.City -eq "San Diego" -or $_.City -eq "Bloomington")} | Select DisplayName, City
```

다음과 같은 화면이 표시됩니다.
  
```
DisplayName                              City
-----------                              ----
Alex Darrow                              San Diego
Bonnie Kearney                           San Diego
Julian Isla                              Bloomington
Rob Young                                Bloomington
Zrinka Makovac                           San Diego
```

> [!TIP]
>  이 Office 365 PowerShell 명령의 해석: 샌디에이고 또는 Bloomington의 도시에서 사서함을 가진 사용자에 현재 Office 365 구독을 모두 활용할 수 ( **여기에서 {$\_합니다. RecipientTypeDetails-eq "UserMailbox"-및 ($\_합니다. 도시-eq "샌디에이고"-또는 $\_합니다. 도시-eq "Bloomington")을 (를)** ), 각 ( **DisplayName 선택, 도시** )에 대 한 이름 및 도시를 표시 합니다.
  
Bloomington을 제외한 모든 위치에 거주하는 사용자의 모든 사서함을 나열하려면 다음 명령을 사용합니다.
  
```
Get-User | Where {$_.RecipientTypeDetails -eq "UserMailbox" -and $_.City -ne "Bloomington"} | Select DisplayName, City
```

다음과 같은 화면이 표시됩니다.
  
```
DisplayName                               City
-----------                               ----
MOD Administrator                         Redmond
Alex Darrow                               San Diego
Allie Bellew                              Bellevue
Anne Wallace                              Louisville
Aziz Hassouneh                            Cairo
Belinda Newman                            Charlotte
Bonnie Kearney                            San Diego
David Longmuir                            Waukesha
Denis Dehenne                             Birmingham
Garret Vargas                             Seattle
Garth Fort                                Tulsa
Janet Schorr                              Bellevue
```

> [!TIP]
>  이 Office 365 PowerShell 명령의 해석: 하지 Bloomington 도시에에서 있는 사서함을 가진 현재 Office 365 구독에서 사용자의을 모두 활용할 수 ( **여기에서 {$\_합니다. RecipientTypeDetails-eq "UserMailbox"-및 $\_합니다. 도시-ne "Bloomington"}** )을 각각에 대 한 이름 및 도시를 표시 합니다.
  
이름의 일부를 일치 하도록 Office 365 PowerShell 필터에 와일드 카드 문자를 사용할 수 있습니다. 예는 사용자 계정에 대 한 찾는 고 기억할 수 있는 모든는 Anderson, 또는 henderson, 엔터프라이즈 무선 전화 통신, 마지막 이름 인지 또는 Jorgenson 되었던 엔터프라이즈 무선 전화 통신 경우를 가정해 보겠습니다.
  
검색 도구를 사용 하 고 개별 검색 3을 수행 하 여 Office 365 관리 센터에서 해당 사용자를 추적할 수 있습니다.:
  
- *Anderson* 
    
- *Henderson* 
    
- *Jorgenson* 에 대해 
    
이러한 이름의 세를 모두 "son"을 종료 하기 때문에 이름이 "son"으로 끝나는 모든 사용자를 표시 하는 Office 365 PowerShell 알 수 있습니다. 명령은 다음과 같습니다.
  
```
Get-User -Filter '{LastName -like "*son"}'
```

> [!TIP]
>  이 Office 365 PowerShell 명령의 해석: 현재 Office 365 구독을 확인할 수 있는 모든 사용자가 있지만 성이 "son"으로 끝나는 사용자를 나열 하는 필터를 사용 하 여 ( **-필터 ' {LastName-같은 "\*아들"을 (를) '** ). \* 임의의 사용자의 성의 경우 문자는 문자 집합에 대 한 의미 합니다.
  
## <a name="office-365-powershell-makes-it-easy-to-print-or-save-data"></a>Office 365 PowerShell을 사용하면 데이터 쉽게 인쇄 또는 저장할 수 있음
<a name="printsave"> </a>

Office 365 관리 센터를 사용 하면 데이터의 목록을 볼 수 있습니다. 비즈니스 Online 용 Skype를 사용할 수 있는 사용자 목록을 표시 하는 비즈니스 온라인 관리 센터에 대 한 Skype의 예는 다음과 같습니다.
  
![비즈니스용 Skype Online을 사용하도록 설정된 사용자 목록을 표시하는 비즈니스용 Skype Online 관리 센터 예제입니다.](images/o365_powershell_lync_users.png)
  
파일에 해당 정보를 저장 하려면 복사 하 고 문서 또는 Excel에 붙여넣어야 합니다. 두 경우 모두 추가 서식을 복사본 필요할 수 있습니다. 또한 Office 365 관리 센터에 표시 된 목록 직접 인쇄 하는 방법을 제공 하지 않습니다.
  
놓기만 Office 365 PowerShell의 목록을 표시 뿐아니라 Excel에 쉽게 가져올 수 있는 파일에 저장을 사용할 수 있습니다. 비즈니스 온라인 사용자 데이터를 쉼표로 구분 된 값 (CSV) 파일을 Excel 워크시트의 테이블로 쉽게 가져올 수 있는 파일에 대 한 Skype를 저장 하는 명령의 예가 나와 다음과 같습니다.
  
```
Get-CsOnlineUser | Select DisplayName, UserPrincipalName, UsageLocation | Export-Csv -Path "C:\\Logs\\SfBUsers.csv" -NoTypeInformation
```

다음과 같은 화면이 표시됩니다.
  
![쉼표로 구분된 값(CSV) 파일로 저장된 Skype용 비즈니스 Online 사용자 데이터를 Excel 워크시트로 가져온 테이블 예제입니다.](images/o365_powershell_data_in_excel.png)
  
> [!TIP]
>  이 Office 365 PowerShell 명령의 해석: 현재 Office 365 구독 ( **Get-csonlineuser** )에서 온라인 비즈니스 사용자를 위한는 Skype을 모두 활용할 수, 사용자 이름, UPN, 및 위치 ( **DisplayName 선택 UserPrincipalName, usagelocation이** ), 다음 정보가 CSV 파일에 c:를 명명 된를 저장 하 고\\로그\\SfBUsers.csv ( **내보내기 Csv-경로 "c:\\로그\\SfBUsers.csv"-NoTypeInformation** ).
  
또한 옵션을 사용하여 이 목록을 XML 파일 또는 HTML 페이지로 저장할 수도 있습니다. 실제로 추가 PowerShell 명령과 원하는 사용자 지정 서식을 사용하여 Excel 파일로 직접 저장할 수도 있습니다.  
  
또한 Windows에서 기본 프린터로 직접 목록을 표시 하는 Office 365 PowerShell 명령의 출력을 보낼 수 있습니다. 다음은 예제 명령이입니다.
  
```
Get-CsOnlineUser | Select DisplayName, UserPrincipalName, UsageLocation | Out-Printer
```

인쇄 된 문서의 모양은 다음과 같습니다.
  
![Windows의 기본 프린터에 직접 나열된 Office 365 PowerShell 명령 출력의 인쇄된 문서 예제입니다.](images/o365_powershell_printed_data.png)
  
> [!TIP]
>  이 Office 365 PowerShell 명령의 해석: 온라인 비즈니스 사용자가 현재 Office 365 구독에 사용자 이름, UPN, 및 위치를 얻고 기본 Windows 프린터로 ( **해당 정보를 보내려면 다음에 대 한 모든는 Skype 가져오기 Out-Printer** ).
  
다음은 인쇄 된 문서에는 동일한 간단한 서식으로 Office 365 PowerShell 명령 창 내에서 표시 되지만 필요한 정보를 나열 하는 Office 365 PowerShell 명령의 만들면 방금 추가한 **| 정찰기 프린터** 에서 작동 하도록 하드 카피를 가져오려면 명령의 끝에 있습니다.
  
## <a name="office-365-powershell-lets-you-manage-across-server-products"></a>Office 365 PowerShell을 사용하여 여러 서버 제품을 관리할 수 있음
<a name="printsave"> </a>

Office 365를 구성 하는 다양 한 구성 요소는 함께 작동 하도록 설계 되었습니다. 예, Office 365에 새 사용자를 추가 하 고 사용자의 부서 및 전화 번호 등의 정보를 지정 하는 이렇게 전환 하면 경우를 가정해 보겠습니다. 정보를 Office 365 서버 제품 중 하나를 사용 하 여 사용자의 정보를 액세스 하는 경우에 사용할 수 다음: 비즈니스 Online, Exchange, 또는 SharePoint Online 용 Skype 합니다.
  
하지만 제품의 제품군에 걸쳐 있는 일반적인 정보에 대 한이. 제품별 정보-사용자의 Exchange 사서함에 대 한 정보 등-일반적으로 사용할 수 없으면 해당 도구 모음 전체에서 합니다. 예 하는 경우 사용자의 사서함 설정 되었는지 여부를 확인 하려는 경우 해당 정보는 사용할 수 있는 Exchange 관리 센터에만. 
  
모든 사용자에 대 한 다음 정보를 표시 하는 보고서를 확인 하려는 경우를 가정해 보겠습니다.
  
- 사용자의 표시 이름
    
- Office 365에 대 한 사용자가 사용이 허가 되었는지 여부
    
- 사용자의 Exchange 사서함 활성화 되었는지 여부
    
- 사용자가 사용할 수 있는지 여부 Skype에 대 한 비즈니스 온라인
    
현재 Office 365 관리 센터를 사용 하 여 쉽게 이러한 보고서를 생성 하려면 수는 없습니다. 대신, 해야 하는 Excel 워크시트와 같은 정보를 저장 하 고 모든 사용자 이름을 라이선스 정보는 Office 365 관리 센터에서 Exchange 관리 센터에서 사서함 정보를 얻을 가져오고, Skype 비즈니스를 위한 별도 문서 만들기 비즈니스 온라인 관리 센터에 대 한 Skype에서 온라인 정보 다음 한 부씩 인쇄 하 고 해당 정보를 결합 합니다.
  
대신 사용 하는 하면 해당 보고서를 컴파일할 Office 365 PowerShell 스크립트를 사용 하는 것입니다.
  
다음 예제 스크립트는이 문서에서 지금까지 설명한 것 명령 보다 더 복잡 합니다. 하지만 그렇지 않은 경우 수행 하기가 매우 어려울 수 있는 정보의 보기를 만들어 Office 365 PowerShell을 사용 하 여 잠재적인을 보여줍니다. 컴파일 하 고 필요한 목록을 표시할 수 있는 스크립트는 다음과 같습니다.
  
```
$x = Get-MsolUser

foreach ($i in $x)
    {
      $y = Get-Mailbox -Identity $i.UserPrincipalName
      $i | Add-Member -MemberType NoteProperty -Name IsMailboxEnabled -Value $y.IsMailboxEnabled

      $y = Get-CsOnlineUser -Identity $i.UserPrincipalName
      $i | Add-Member -MemberType NoteProperty -Name EnabledForSfB -Value $y.Enabled
    }

$x | Select DisplayName, IsLicensed, IsMailboxEnabled, EnabledforSfB
```

다음과 같은 화면이 표시됩니다.
  
```
DisplayName             IsLicensed   IsMailboxEnabled   EnabledForSfB
-----------             ----------   ----------------   --------------
Zrinka Makovac          True         True               True
Bonnie Kearney          True         True               True
Fabrice Canel           True         True               True
Brian Johnson           False        True               False
Anne Wallace            True         True               True
Alex Darrow             True         True               True
David Longmuir          True         True               True
Katy Jordan             False        True               False
Molly Dempsey           False        True               False
```

이 Office 365 PowerShell 스크립트의 해석이 됩니다.  
- 변수 $ $x에서에서 정보를 저장 하 고 현재 Office 365 구독을 확인할 수 있는 모든 사용자 ( **$x Get-msoluser =** ).
- 변수 $ $x ( **foreach ($x에서 $i)** )에 있는 모든 사용자를 통해 실행 되는 루프를 시작 합니다.  
- $Y 라는 변수를 정의 하 고 여기에 사용자의 사서함 정보를 저장 ( **$y Get-mailbox =-Identity $i.UserPrincipalName** ).
- IsMailBoxEnabled 라는 사용자 정보에 새 속성을 추가 하 고 사용자의 사서함의 IsMailBoxEnabled 속성의 값으로 설정 ( **$i | Add-Member-MemberType NoteProperty-IsMailboxEnabled 이름-값이 $y.IsMailboxEnabled** ).
- $Y 라는 변수를 정의 하 고 그 안에 온라인 비즈니스 정보에 대 한 사용자의 Skype 저장 ( **$y Get-csonlineuser =-Identity $i.UserPrincipalName** ).
- EnabledForSfB 라는 사용자 정보를 새 속성을 추가 하 고 온라인 비즈니스 정보에 대 한 사용자의 Skype의 Enabled 속성의 값으로 설정 ( **$i | Add-Member-MemberType NoteProperty-EnabledForSfB 이름-값이 $y.Enabled** ).
- 사용자의 목록을 표시 하지만 자신의 이름만, 라이선스 여부 및 해당 사서함의 사용 가능 여부 및 온라인 비즈니스에 대 한 Skype에 대해 활성화 되었는지 여부를 나타내는 두 새 속성을 포함 ( **$x | DisplayName, IsLicensed, IsMailboxEnabled, EnabledforSfB 선택** ).
  
## <a name="see-also"></a>See also


#### 

[Office 365 PowerShell 시작](getting-started-with-office-365-powershell.md)
  
[사용자 계정 및 Office 365 powershell 라이선스 관리](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Windows PowerShell을 사용 하 여 Office 365에서 보고서를 만들려면](use-windows-powershell-to-create-reports-in-office-365.md)

