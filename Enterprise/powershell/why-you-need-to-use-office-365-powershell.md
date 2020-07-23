---
title: Microsoft 365 용 PowerShell을 사용 해야 하는 이유
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: ITPro
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: ''
ms.assetid: b3209b1a-40c7-4ede-8e78-8a88bb2adc8a
description: '요약: 일부 경우에는 필요한 경우 PowerShell을 사용 하 여 Microsoft 365을 관리 해야 하는 이유를 파악 합니다.'
ms.openlocfilehash: ba786acd8b5ad08bad97b11812f0180004e55cb6
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/22/2020
ms.locfileid: "45229864"
---
# <a name="why-you-need-to-use-powershell-for-microsoft-365"></a>Microsoft 365 용 PowerShell을 사용 해야 하는 이유

*이 문서는 Microsoft 365 Enterprise 및 Office 365 Enterprise에 모두 적용 됩니다.*

Microsoft 365 관리 센터를 사용 하 여 Microsoft 365 사용자 계정 및 라이선스를 관리할 수 있을 뿐만 아니라 Exchange Online, 팀 및 SharePoint Online과 같은 Microsoft 365 서비스를 관리할 수도 있습니다. 그러나 PowerShell 명령을 사용 하 여 이러한 요소를 관리 하 고 속도, 자동화 및 추가 기능에 대 한 명령줄 및 스크립팅 언어 환경을 활용할 수도 있습니다.
  
이 문서에서는 PowerShell을 사용 하 여 Microsoft 365를 관리할 수 있는 다음과 같은 방법을 보여 줍니다.
  
- Microsoft 365 관리 센터에서 볼 수 없는 추가 정보 표시
    
- PowerShell로 가능한 기능 및 설정 구성
    
- 대량 작업 수행
    
- 데이터 필터링
    
- 데이터 인쇄 또는 저장
    
- 서비스 간 관리
    
시작 하기 전에 Microsoft 365 용 PowerShell이 windows 기반 서비스 및 플랫폼용 명령줄 환경인 Windows PowerShell 용 모듈 집합 인지 이해 합니다. 이 환경에서는 추가 모듈로 확장 될 수 있는 명령 셸 언어를 만들고 단순 또는 복잡 한 명령이 나 스크립트를 실행 하는 방법을 제공 합니다. 예를 들어 Microsoft 365 용 PowerShell 모듈을 설치 하 고 Microsoft 365 구독에 연결 하 고 나면이 명령을 실행 하 여 Microsoft Exchange Online에 대 한 모든 사용자 사서함을 나열할 수 있습니다.
  
```powershell
Get-Mailbox
```

Microsoft 365 관리 센터를 사용 하 여 사서함 목록을 쉽게 가져올 수 있지만 모든 웹 앱에 대 한 모든 사이트의 모든 목록에 있는 항목 수를 계산 하는 작업을 쉽게 수행할 수 없습니다.
  
Microsoft 365 용 PowerShell은 microsoft 365 관리 센터를 교체 하는 것이 아니라 Microsoft 365를 관리할 수 있는 기능을 강화 하 고 개선 하기 위한 것입니다. 관리자는 Microsoft 365 명령에 대해서만 PowerShell을 사용 하 여 수행할 수 있는 몇 가지 구성 프로시저가 있으므로 Microsoft 365의 PowerShell을 사용 하는 것이 좋습니다. 이러한 경우 다음 방법을 이해해야 합니다.
  
- Microsoft 365 용 PowerShell 모듈을 설치 합니다 (각 관리자 컴퓨터에 대해 한 번만 수행).
    
- Microsoft 365 구독에 연결 (각 PowerShell 세션에 대해 한 번 수행)
    
- Microsoft 365 명령에 필요한 PowerShell을 실행 하는 데 필요한 정보를 수집 합니다.
    
- Microsoft 365 명령에 대해 PowerShell을 성공적으로 실행 합니다.
    
이러한 기본 기술을 학습한 후에는 **Get-Mailbox** 명령을 사용하여 사서함 사용자를 나열할 필요도 없고, 앞에 나온 것처럼 모든 웹앱에 대한 모든 사이트의 전체 목록에 포함된 항목 수를 계산하기 위한 명령과 같은 새 명령을 만드는 방법을 알 필요도 없습니다. Microsoft 및 관리자 커뮤니티는 필요에 따라 도움을 받을 수 있습니다.
  
## <a name="powershell-for-microsoft-365-can-reveal-additional-information-that-you-cannot-see-with-the-microsoft-365-admin-center"></a>Microsoft 365 용 PowerShell을 사용 하 여 Microsoft 365 관리 센터에서는 볼 수 없는 추가 정보를 확인할 수 있습니다.

Microsoft 365 관리 센터에는 많은 유용한 정보가 표시 되지만,이는 Microsoft 365에서 사용자, 라이선스, 사서함 및 사이트에 저장 하는 모든 가능한 정보를 표시 하는 것을 의미 하지는 않습니다. 다음은 Microsoft 365 관리 센터의 **사용자 및 그룹** 에 대 한 예입니다.
  
![Microsoft 365 관리 센터의 사용자 및 그룹 표시 예제입니다.](media/o365-powershell-users-and-groups.png)
  
여기에는 다양한 용도로 사용자가 알아야 하는 정보가 표시됩니다. 그러나 더 많은 정보가 필요한 경우도 있습니다. 예를 들어 Microsoft 365 라이선스 (및 사용자가 사용할 수 있는 Microsoft 365 기능)는 부분적으로 해당 사용자의 지리적 위치에 따라 달라 집니다. 가령 미국 사용자에 대해 확장 가능한 정책과 기능은 인도나 벨기에 사용자에 대해 확장 가능한 정책과 기능은 서로 다를 수 있습니다. 다음 단계에 따라 Microsoft 365 관리 센터를 사용 하 여 사용자의 지리적 위치를 확인할 수 있습니다.
  
1. 사용자의 **표시 이름** 을 두 번 클릭합니다.
    
2. 사용자 속성 표시 창에서 **세부 정보** 를 클릭합니다.
    
3. 세부 정보 표시에서 **추가 정보**를 클릭합니다.
    
4. **국가 또는 지역** 제목이 표시될 때까지 아래쪽으로 스크롤합니다.
    
     ![Microsoft 365 관리 센터의 사용자에 대 한 지역 정보 예제입니다.](media/o365-powershell-usage-location.png)
  
5. 사용자의 표시 이름과 지역을 종이에 적어 두거나 복사한 다음 메모장에 붙여 넣습니다. 
    
각 사용자에 대해 이 절차를 반복해야 합니다. 많은 사용자에게 이 작업은 번거로울 수 있습니다. Microsoft 365 용 PowerShell을 사용 하 여 다음 명령을 사용 하 여 모든 사용자에 대해이 정보를 표시할 수 있습니다.
  
```powershell
Get-AzureADUser | Select DisplayName, UsageLocation
```


>[!Note]
>PowerShell Core는 Windows PowerShell용 Microsoft Azure Active Directory 모듈 및 이름에 **Msol**이 있는 cmdlet을 지원하지 않습니다. 이러한 cmdlet을 계속 사용하려면 Windows PowerShell에서 이를 실행해야 합니다.
>

다음과 같은 화면이 표시됩니다.
  
```powershell
DisplayName                               UsageLocation
-----------                               -------------
Bonnie Kearney                            GB
Fabrice Canel                             BR
Brian Johnson (TAILSPIN)                  US
Anne Wallace                              US
Alex Darrow                               US
David Longmuir                            BR
```

> [!TIP]
>  이 PowerShell 명령을 해석 하면 다음과 같습니다. 현재 Microsoft 365 구독 ( **AzureADUser** )의 모든 사용자를 가져오고 각 사용자의 이름과 위치만 표시 합니다 ( **DisplayName, UsageLocation 선택** ).
  
PowerShell for Microsoft 365는 명령 셸 언어를 지원 하므로 **AzureADUser** 명령에서 얻은 정보를 보다 세부적으로 조작할 수 있습니다. 예를 들어 이러한 사용자를 위치에 따라 정렬 하 고 모든 브라질 사용자와 모든 미국 사용자를 함께 그룹화 할 수 있습니다. 명령은 다음과 같습니다.
  
```powershell
Get-AzureADUser | Select DisplayName, UsageLocation | Sort UsageLocation, DisplayName
```

다음과 같은 화면이 표시됩니다.
  
```powershell
DisplayName                                 UsageLocation
-----------                                 -------------
David Longmuir                              BR
Fabrice Canel                               BR
Bonnie Kearney                              GB
Alex Darrow                                 US
Anne Wallace                                US
Brian Johnson (TAILSPIN)                    US
```

> [!TIP]
>  이 PowerShell 명령을 사용 하는 경우에는 현재 Microsoft 365 구독의 모든 사용자를 가져오고, 각 사용자의 이름과 위치만 표시 하 고, 위치에 따라 먼저 정렬 한 다음 이름 ( **Sort UsageLocation, DisplayName** )을 설정 합니다.
  
추가 필터링을 사용할 수도 있습니다. 예를 들어 브라질 사용자에 대한 정보만 표시하려면 다음 명령을 사용합니다.
  
```powershell
Get-AzureADUser | Where {$_.UsageLocation -eq "BR"} | Select DisplayName, UsageLocation 
```

다음과 같은 화면이 표시됩니다.
  
```powershell
DisplayName                                           UsageLocation
-----------                                           -------------
David Longmuir                                        BR
Fabrice Canel                                         BR
```

> [!TIP]
>  이 PowerShell 명령의 해석은 다음과 같습니다. 현재 Microsoft 365 구독에서 위치가 브라질 인 모든 사용자 가져오기 ( **여기서 {$) \_ UsageLocation-eq "BR"}** )를 선택한 다음 각 사용자의 이름과 위치를 표시 합니다.
  
 **대규모 도메인 관련 참고 사항**
  
사용자가 수만 명인 매우 큰 도메인의 경우 이 문서에서 제시하는 몇 가지 예를 사용하면 "제한" 현상이 발생할 수 있습니다. 즉, 컴퓨팅 기능, 사용 가능한 네트워크 대역폭 등을 기준으로 보았을 때 사용자가 한 번에 너무 많은 작업을 수행할 수 있습니다. 따라서 대규모 조직에서는 이러한 PowerShell 중 일부를 Microsoft 365 명령에 대 한 두 개의 명령으로 분할할 수 있습니다. 예를 들어 이 명령 하나를 실행하면 모든 사용자 계정이 반환되고 각 사용자의 이름과 위치가 표시됩니다.
  
```powershell
Get-AzureADUser | Select DisplayName, UsageLocation
```

소규모 도메인에서는 이 명령을 사용해도 아무런 문제가 없습니다. 그러나 대규모 조직에서는 위의 명령을 두 개의 명령, 즉 변수에 사용자 계정 정보를 저장하기 위한 명령과 필요한 정보를 표시하기 위한 명령으로 분할해야 할 수 있습니다. 예제는 다음과 같습니다.
  
```powershell
$x = Get-AzureADUser
$x | Select DisplayName, UsageLocation
```

이 PowerShell 명령 집합을 해석 하면 다음과 같습니다.
- 현재 Microsoft 365 구독의 모든 사용자를 가져온 다음 해당 정보를 $x ( **$x = AzureADUser** ) 라는 변수에 저장 합니다.
- $x 변수의 내용을 표시하지만 각 사용자의 이름과 위치만 포함합니다(**$x | Select DisplayName, UsageLocation**).
  
## <a name="microsoft-365-has-features-that-you-can-only-configure-with-powershell-for-microsoft-365"></a>Microsoft 365에는 Microsoft 365 용 PowerShell을 사용 하 여 구성할 수 있는 기능이 있습니다.

Microsoft 365 관리 센터는 대부분의 사용자에 게 적용 되는 가장 일반적인 또는 의미 있는 관리 작업에 대 한 액세스를 제공 하기 위한 것입니다. 즉, Microsoft 365 관리 센터는 일반적인 관리자가 도구를 사용 하 여 가장 일반적인 관리 작업을 수행할 수 있도록 설계 되었습니다. 이 정의에서는 Microsoft 365 관리 센터를 사용 하 여 완료할 수 없는 몇 가지 작업이 있음을 의미 합니다.
  
예를 들어 비즈니스용 Skype 온라인 관리 센터에서는 사용자 지정 모임 초대를 만들기 위한 몇 가지 옵션을 제공합니다.
  
![비즈니스용 Skype Online 관리 센터에 표시된 사용자 지정 모임 초대 예제입니다.](media/o365-powershell-meeting-invitation.png)
  
이러한 설정을 사용하여 모임 초대를 전문적으로 개인 설정할 수 있습니다. 그러나 모임 구성 설정에는 사용자 지정 모임 초대 만들기 외에도 다양한 기능이 있습니다. 예를 들어 모임에서는 기본적으로 다음과 같은 설정이 가능합니다.
  
- 익명 사용자가 각 모임에 자동으로 입장할 수 있도록 설정
    
- 참석자가 모임을 기록하도록 설정
    
- 조직의 모든 사용자가 모임 참가 시 발표자로 지정되도록 설정
    
이러한 설정을 비즈니스용 Skype 온라인 관리 센터에서는 사용할 수 없습니다. 그러나 Microsoft 365 용 PowerShell에서이를 제어할 수 있습니다. 이러한 세 가지 설정을 사용하지 않도록 하는 명령은 다음과 같습니다.
  
```powershell
Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $False -AllowConferenceRecording $False -DesignateAsPresenter "None"
```

> [!NOTE]
> 이 명령을 사용하려면 [비즈니스용 Skype Online PowerShell 모듈](https://www.microsoft.com/download/details.aspx?id=39366)을 설치해야 합니다. 
  
> [!TIP]
>  이 PowerShell 명령을 사용 하는 경우: **get-csmeetingconfiguration** (새 비즈니스용 Skype Online 모임에 대 한 설정), 익명 사용자가 모임에 자동으로 입장할 수 있도록 허용 (- **AdmitAnonymousUsersByDefault $False** ), 참석자가 모임을 녹음 하는 기능을 사용 하지 않도록 설정 (- **AllowConferenceRecording $False** ), 조직의 모든 사용자를 발표자 (- **designateaspresenter "없음"** )로 지정 하지 않도록 설정할 수 있습니다.
  
생각이 바뀌어 이러한 기본 설정을 복원하려면(모두 사용하도록 설정) 다음 명령을 실행합니다.
  
```powershell
Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $True -AllowConferenceRecording $True -DesignateAsPresenter "Company"
```

이것은 예에 불과합니다. 관리자가 Microsoft 365 명령에 대해 PowerShell을 실행 하는 데 어려움을 갖고 있어야 하는 다른 방법이 있습니다.
  
## <a name="powershell-for-microsoft-365-is-great-at-carrying-out-bulk-operations"></a>Microsoft 365 용 PowerShell은 대량 작업을 수행 하는 데 유용 합니다.

이전에는 Microsoft 365 관리 센터와 같은 시각적 인터페이스는 단일 작업을 수행 해야 하는 경우에 가장 유용 합니다. 예를 들어 하나의 사용자 계정을 사용 하지 않도록 설정 해야 하는 경우 Microsoft 365 관리 센터를 사용 하 여 확인란을 빠르게 찾아서 지울 수 있습니다. 이는 PowerShell에서 비슷한 작업을 수행 하는 것 보다 간단 합니다.
  
그러나 많은 항목을 변경 해야 하는 경우 또는 여러 항목 중에서 선택한 일부 항목은 Microsoft 365 관리 센터를 사용 하는 데 가장 적합 하지 않을 수 있습니다. 예를 들어 수천 개의 전화 번호에 대 한 접두사를 변경 해야 하거나 모든 SharePoint Online 사이트에서 특정 사용자 Ken Myer을 제거 해야 하는 경우 Microsoft 365 관리 센터에서이 작업을 수행 하려면 어떻게 해야 합니까?
  
후자의 경우 SharePoint Online 사이트는 수백 개이고 그 중에서 Ken이 구성원으로 속해 있는 사이트가 어느 것인지도 모르는 상황입니다. 즉, Microsoft 365 관리 센터에서 시작한 다음 각 사이트에 대해이 절차를 수행 해야 합니다.
  
1. 사이트의 **URL** 을 클릭합니다.
    
2. **사이트 모음 속성** 상자에서 **웹 사이트 주소** 링크를 클릭하여 사이트를 엽니다.
    
3. 사이트에서 **공유** 를 클릭합니다.
    
4. **공유** 대화 상자에서 사이트에 대한 사용 권한이 있는 모든 사용자를 표시하는 링크를 클릭합니다.
    
     ![SharePoint Online 관리 센터에서 SharePoint Online 사이트의 구성원을 보는 예제입니다.](media/o365-powershell-view-permissions.png)
  
5. **다음 사용자와 공유** 대화 상자에서 **고급** 을 클릭합니다.
    
6. 사용자 목록 아래쪽으로 스크롤하여 Ken Myer(사이트에 대한 사용 권한이 있는 사용자라고 가정함)를 찾아 선택한 다음 **사용자의 사용 권한 제거** 를 클릭합니다.
    
수백 개의 사이트의 경우 시간이 오래 걸릴 수 있습니다.
  
다른 방법은 Microsoft 365 용 PowerShell을 사용 하 여 모든 사이트에서 Ken Myer를 제거 하는 것입니다.
  
```powershell
Get-SPOSite | ForEach {Remove-SPOUser -Site $_.Url -LoginName "kenmyer@litwareinc.com"}
```

> [!NOTE]
> 이 명령을 사용 하려면 [SharePoint Online PowerShell 모듈](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)을 설치 해야 합니다. 
  
> [!TIP]
>  이 PowerShell 명령을 해석 하면 다음과 같습니다. 현재 Microsoft 365 구독 ( **get-sposite** ) 및 각 사이트에 대해 모든 SharePoint 사이트 가져오기 ( **ForEach {Remove-spouser-site $)를 사용 하 여 액세스할 수 있는 사용자 목록에서 Ken 구 지 후을 제거 \_ 합니다. Url-LoginName "kenmyer@litwareinc.com"}** )
  
Microsoft 365에는 모든 사이트에서 Ken 구 지 후를 제거 하는 것이 포함 되어 있으므로 (액세스 권한이 없는 경우)이 명령은 현재 액세스 권한이 없는 사이트의 오류를 표시 합니다. 이 명령에 추가 조건을 사용하여 로그인 목록에 Ken Meyer가 있는 사이트에서만 Ken Meyer를 제거할 수 있지만 나열되는 오류가 사이트 자체에는 문제가 되지 않습니다. 이 명령을 실행 하는 데 몇 분 정도 걸릴 수 있습니다 (Microsoft 365 관리 센터를 사용 하는 시간이 아님).
  
다른 대량 작업의 예제는 다음과 같습니다. 이 명령을 사용하여 새 SharePoint 관리자인 Bonnie Kearney를 조직의 모든 사이트에 추가합니다.
  
```powershell
Get-SPOSite | ForEach {Add-SPOUser -Site $_.Url -LoginName "bkearney@litwareinc.com" -Group "Members"}
```

> [!TIP]
>  이 PowerShell 명령을 사용 하는 경우의 해석은 현재 Microsoft 365 구독에 있는 모든 SharePoint 사이트를 가져오고 각 사이트에 대해 Bonnie Kearney access를 사용 하도록 허용 합니다 ( **ForEach {Add-SPOUser-site $ \_ ). Url-LoginName "bkearney@litwareinc.com"-Group "Members"}** )
  
## <a name="powershell-for-microsoft-365-is-great-at-filtering-data"></a>Microsoft 365 용 PowerShell은 데이터를 필터링 하는 데 유용 합니다.

Microsoft 365 관리 센터에서는 데이터를 필터링 하 여 대상 정보 하위 집합을 빠르고 쉽게 찾을 수 있는 다양 한 방법을 제공 합니다. 예를 들어 Exchange에서는 사용자 사서함의 사실상 모든 속성을 기준으로 쉽게 필터링을 할 수 있습니다. 예를 들어 다음은 Bloomington에 거주하는 모든 사용자의 사서함 목록입니다.
  
![Bloomington의 구/군/시에 거주 하는 모든 사용자의 사서함 목록에 대해 Microsoft 365 관리 센터에서 고급 검색을 수행 하는 방법의 예입니다.](media/o365-powershell-advanced-search.png)
  
Exchange 관리 센터에서도 필터 기준을 조합할 수 있습니다. 예를 들어 Bloomington에 거주하고 재무 부서에서 일하는 모든 사용자에 대한 사서함을 찾을 수 있습니다. 
  
그러나 Exchange 관리 센터에서는 수행할 수 있는 작업에 제한이 있습니다. 예를 들어 Bloomington이나 San Diego에 거주하는 사용자의 사서함을 찾거나 Bloomington에 거주하지 않는 모든 사용자에 대한 사서함을 찾을 수 있습니다. 
  
Microsoft 365 용 PowerShell을 사용 하 여 다음 명령을 사용 하 여 Bloomington 또는 San Diego에 거주 하는 모든 사람에 대 한 사서함 목록을 가져올 수 있습니다.
  
```powershell
Get-User | Where {$_.RecipientTypeDetails -eq "UserMailbox" -and ($_.City -eq "San Diego" -or $_.City -eq "Bloomington")} | Select DisplayName, City
```

다음과 같은 화면이 표시됩니다.
  
```powershell
DisplayName                              City
-----------                              ----
Alex Darrow                              San Diego
Bonnie Kearney                           San Diego
Julian Isla                              Bloomington
Rob Young                                Bloomington
```

> [!TIP]
>  이 PowerShell 명령을 해석 하면 다음과 같습니다. San Diego 또는 Bloomington ( **여기서 {$)의 도시에 사서함이 있는 현재 Microsoft 365 구독의 모든 사용자를 가져옵니다. \_ RecipientTypeDetails-eq "UserMailbox" and ($ \_ . 도시-eq "San Diego"- \_ 또는 $ City-eq "Bloomington")}** )를 선택한 다음 각각의 이름과 구/군/시 ( **DisplayName, city** )을 표시 합니다.
  
Bloomington을 제외한 모든 위치에 거주하는 사용자의 모든 사서함을 나열하려면 다음 명령을 사용합니다.
  
```powershell
Get-User | Where {$_.RecipientTypeDetails -eq "UserMailbox" -and $_.City -ne "Bloomington"} | Select DisplayName, City
```

다음과 같은 화면이 표시됩니다.
  
```powershell
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
>  이 PowerShell 명령을 해석 하면 다음과 같습니다. Bloomington ( **여기서 {$)가 없는 사서함이 있는 현재 Microsoft 365 구독의 모든 사용자를 가져옵니다. \_ RecipientTypeDetails-eq "UserMailbox"- \_ 및 $ City-ne "Bloomington"}** )를 선택한 다음 각각에 대해 이름과 구/군/시를 표시 합니다.
  
또한 PowerShell 필터에서 와일드 카드 문자를 사용 하 여 이름의 일부를 일치 시킬 수도 있습니다. 예를 들어 특정 사용자 계정을 찾아야 하는데 성이 Anderson, Henderson 또는 Jorgenson이라는 점만 기억하고 있다고 가정할 경우
  
검색 도구를 사용 하 고 다음과 같은 세 가지 다른 검색을 수행 하 여 Microsoft 365 관리 센터에서 해당 사용자에 추적할 수 있습니다.
  
- *Anderson*  에 대해, 
    
- *Henderson*  에 대해, 
    
- *Jorgenson*  에 대해 
    
이 세 가지 이름이 모두 "son"으로 끝나는 것 이므로 PowerShell을 통해 이름이 "son"으로 끝나는 모든 사용자를 표시할 수 있습니다. 해당 명령은 다음과 같습니다.
  
```powershell
Get-User -Filter '{LastName -like "*son"}'
```

> [!TIP]
>  이 PowerShell 명령을 사용 하는 경우에는 현재 Microsoft 365 구독의 모든 사용자를 가져오고, 성이 "son" ( **-filter ' {LastName-like " \* son"} '** 으로 끝나는 사용자만 나열 하는 필터를 사용할 수 있습니다. 는 \* 문자 집합 (사용자의 성에 대 한 문자)을 나타냅니다.
  
## <a name="powershell-for-microsoft-365-makes-it-easy-to-print-or-save-data"></a>Microsoft 365 용 PowerShell을 사용 하면 데이터를 쉽게 인쇄 하거나 저장할 수 있습니다.

Microsoft 365 관리 센터를 사용 하 여 데이터 목록을 볼 수 있습니다. 다음은 비즈니스용 Skype 온라인에 대해 사용되도록 설정된 사용자 목록을 표시하는 비즈니스용 Skype 온라인 관리 센터의 예입니다.
  
![비즈니스용 Skype Online을 사용하도록 설정된 사용자 목록을 표시하는 비즈니스용 Skype Online 관리 센터 예제입니다.](media/o365-powershell-lync-users.png)
  
해당 정보를 파일에 저장하려면 복사한 후 문서 또는 Excel에 붙여 넣어야 합니다. 두 경우 모두 복사를 위해 추가 서식이 필요할 수 있습니다. 또한 Microsoft 365 관리 센터에서는 표시 된 목록을 직접 인쇄 하는 방법을 제공 하지 않습니다.
  
다행히 PowerShell을 사용 하 여 목록을 표시할 뿐만 아니라 쉽게 Excel로 가져올 수 있는 파일에 저장할 수 있습니다. 다음은 비즈니스용 Skype 온라인 사용자 데이터를 Excel 워크시트의 표로 쉽게 가져올 수 있는 CSV(쉼표로 구분된 값) 파일에 저장하는 예제 명령입니다.
  
```powershell
Get-CsOnlineUser | Select DisplayName, UserPrincipalName, UsageLocation | Export-Csv -Path "C:\Logs\SfBUsers.csv" -NoTypeInformation
```

다음과 같은 화면이 표시됩니다.
  
![쉼표로 구분된 값(CSV) 파일로 저장된 Skype용 비즈니스 Online 사용자 데이터를 Excel 워크시트로 가져온 테이블 예제입니다.](media/o365-powershell-data-in-excel.png)
  
> [!TIP]
>  이 PowerShell 명령을 해석 하면 다음과 같습니다. 현재 Microsoft 365 구독 ( **get-csonlineuser** )의 모든 비즈니스용 Skype Online 사용자를 가져오고, 사용자 이름, UPN 및 위치 ( **DisplayName, UserPrincipalName, UsageLocation** )를 가져온 다음 이라는 csv 파일 ()에 해당SfBUsers.csv 정보를 저장 합니다 \\ \\ ( **내보내기-csv-Path "c: \\ logs \\SfBUsers.csv"-notypeinformation** ).
  
또한 옵션을 사용하여 이 목록을 XML 파일 또는 HTML 페이지로 저장할 수도 있습니다. 실제로 추가 PowerShell 명령과 원하는 사용자 지정 서식을 사용하여 Excel 파일로 직접 저장할 수도 있습니다. 
  
목록을 표시 하는 PowerShell 명령의 출력을 Windows의 기본 프린터로 직접 보낼 수도 있습니다. 예제 명령은 다음과 같습니다.
  
```powershell
Get-CsOnlineUser | Select DisplayName, UserPrincipalName, UsageLocation | Out-Printer
```

인쇄된 문서의 모양은 다음과 같습니다.
  
![Windows의 기본 프린터에 직접 나열 된 PowerShell 명령 출력의 예입니다.](media/o365-powershell-printed-data.png)
  
> [!TIP]
>  이 PowerShell 명령을 해석 하면 다음과 같습니다. 현재 Microsoft 365 구독의 모든 비즈니스용 Skype Online 사용자를 가져오고, 사용자 이름, UPN 및 위치만 얻은 다음 해당 정보를 기본 Windows 프린터 (전자 **프린터** )로 보냅니다.
  
인쇄 된 문서는 PowerShell 명령 창 내에 표시 되는 것과 동일한 서식이 동일 하지만 필요한 것을 나열 하는 PowerShell 명령을 만든 후에는 |을 추가 하기만 하면 됩니다. ** Out-프린터** 에서 작동 하도록 하드 복사본을 가져오기 위한 명령 끝까지 인쇄 합니다.
  
## <a name="powershell-for-microsoft-365-lets-you-manage-across-server-products"></a>Microsoft 365 용 PowerShell을 사용 하면 서버 제품에서 관리할 수 있습니다.

Microsoft 365을 구성 하는 다양 한 요소가 함께 작동 하도록 설계 되었습니다. 예를 들어 Microsoft 365에 새 사용자를 추가 하는 경우 사용자의 부서 및 전화 번호로 이러한 정보를 지정 하는 경우를 예로 들 수 있습니다. Microsoft 365 서비스 (비즈니스용 Skype Online, Exchange 또는 SharePoint Online)를 사용 하 여 사용자 정보에 액세스 하면 해당 정보를 사용할 수 있게 됩니다.
  
그러나 이러한 방식은 제품군 전체에 적용되는 일반적인 정보에만 해당됩니다. 사용자의 Exchange 사서함에 대한 정보와 같은 제품 관련 정보는 일반적으로 전체 제품군 내에서 사용할 수 없스니다. 예를 들어 사용자의 사서함이 사용되도록 설정되어 있는지를 알려면 해당 정보가 Exchange 관리 센터에서만 사용할 수 있는지 확인합니다. 
  
모든 사용자에 대해 다음 정보를 표시하는 보고서를 만들려는 경우를 가정해 보겠습니다.
  
- 사용자의 표시 이름
    
- 사용자에 게 Microsoft 365에 대 한 라이선스가 있는지 여부
    
- 사용자의 Exchange 사서함이 사용하도록 설정되었는지 여부
    
- 사용자가 비즈니스용 Skype 온라인을 사용할 수 있도록 설정되었는지 여부
    
현재 Microsoft 365 관리 센터를 사용 하 여 이러한 보고서를 쉽게 만들 수는 없습니다. 대신 Excel 워크시트와 같은 정보를 저장 하는 별도의 문서를 만들고, Microsoft 365 관리 센터에서 사서함 정보를 가져오고, Exchange 관리 센터에서 비즈니스용 Skype Online 정보를 가져온 다음, 해당 정보를 한 부씩 인쇄 하 고 결합 해야 합니다.
  
다른 방법은 PowerShell 스크립트를 사용 하 여 해당 보고서를 컴파일하는 것입니다.
  
다음 예제 스크립트는 지금까지 이 문서에서 살펴본 명령보다 좀 더 복잡합니다. 그러나 PowerShell을 사용 하 여 특별히 수행 하기 어려운 정보 보기를 만들 수 있는 가능성을 보여 줍니다. 다음은 필요한 목록을 정리해서 표시할 수 있는 스크립트입니다.
  
```powershell
$x = Get-AzureADUser

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
  
```powershell
DisplayName             IsLicensed   IsMailboxEnabled   EnabledForSfB
-----------             ----------   ----------------   --------------
Bonnie Kearney          True         True               True
Fabrice Canel           True         True               True
Brian Johnson           False        True               False
Anne Wallace            True         True               True
Alex Darrow             True         True               True
David Longmuir          True         True               True
Katy Jordan             False        True               False
Molly Dempsey           False        True               False
```

이 PowerShell 스크립트를 해석 하면 다음과 같습니다.  

- 현재 Microsoft 365 구독의 모든 사용자를 가져온 다음 해당 정보를 $x ( **$x = AzureADUser** ) 라는 변수에 저장 합니다.
- 변수 $x에서 모든 사용자에 대해 실행되는 루프를 시작합니다(**foreach ($i in $x)**).  
- $y라는 변수를 정의하고 이 변수에 사용자의 사서함 정보를 저장합니다(**$y = Get-Mailbox -Identity $i.UserPrincipalName**).
- IsMailBoxEnabled라는 사용자 정보에 새 속성을 추가하고 사용자 사서함의 IsMailBoxEnabled 속성 값으로 설정합니다(**$i | Add-Member -MemberType NoteProperty -Name IsMailboxEnabled -Value $y.IsMailboxEnabled**).
- $y라는 변수를 정의하고 이 변수에 사용자의 비즈니스용 Skype Online 정보를 저장합니다(**$y = Get-CsOnlineUser -Identity $i.UserPrincipalName**).
- EnabledForSfB라는 사용자 정보에 새 속성을 추가하고 사용자 비즈니스용 Skype Online 정보의 Enabled 속성 값으로 설정합니다(**$i | Add-Member -MemberType NoteProperty -Name EnabledForSfB -Value $y.Enabled**).
- 사용자의 목록을 표시하지만 이름, 사용 허가 여부, 사서함 사용 가능 여부와 비즈니스용 Skype Online에 대해 사용되도록 설정되었는지 여부를 나타내는 두 개의 새 속성만 포함합니다(**$x | Select DisplayName, IsLicensed, IsMailboxEnabled, EnabledforSfB**).
  
## <a name="see-also"></a>참고 항목

[Microsoft 365 용 PowerShell 시작](getting-started-with-office-365-powershell.md)
  
[PowerShell을 사용 하 여 Microsoft 365 사용자 계정, 라이선스 및 그룹 관리](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Windows PowerShell을 사용 하 여 Microsoft 365에서 보고서 만들기](use-windows-powershell-to-create-reports-in-office-365.md)

