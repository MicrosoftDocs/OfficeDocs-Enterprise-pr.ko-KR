---
title: Office 365 powershell 비즈니스 온라인 정책에 대 한 사용자 당 Skype 할당
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: 36743c86-46c2-46be-b9ed-ad9d4e85d186
description: '요약: Office 365 PowerShell을 사용 사용자별 비즈니스 온라인 정책에 대 한 Skype와 통신 설정을 할당 합니다.'
ms.openlocfilehash: 7f819b619c5b3607c98c10791fe30c3944e862a4
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/11/2018
ms.locfileid: "17114817"
---
# <a name="assign-per-user-skype-for-business-online-policies-with-office-365-powershell"></a>Office 365 powershell 비즈니스 온라인 정책에 대 한 사용자 당 Skype 할당

 **요약:** Office 365 PowerShell를 사용 하 여 사용자별 비즈니스 온라인 정책에 대 한 Skype와 통신 설정을 할당 합니다.
  
Office 365 PowerShell을 사용 하 여 하는 방법은 효율적인 사용자 당 비즈니스 온라인 정책에 대 한 Skype와 통신 설정을 할당 합니다.
  
## <a name="before-you-begin"></a>시작하기 전에

다음이 절차에 따라 사용 하도록 설정 가져오기 명령을 실행 (이미 완료 된 단계를 건너뛰고):
  
1. 다운로드 하 고 [비즈니스 온라인 커넥터 모듈에 대 한 Skype](https://www.microsoft.com/en-us/download/details.aspx?id=39366)를 설치 합니다.
    
2. Windows PowerShell 명령 프롬프트를 열고 다음 명령을 실행 합니다. 
    
  ```
  Import-Module LyncOnlineConnector
$userCredential = Get-Credential
$sfbSession = New-CsOnlineSession -Credential $userCredential
Import-PSSession $sfbSession
  ```
대화 상자가 나타나면 비즈니스 온라인 관리자 계정 이름 및 암호에 대 한 사용자 Skype를 입력 합니다.
    
## <a name="updating-external-communication-settings-for-a-user-account"></a>사용자 계정에 대 한 외부 통신 설정 업데이트

사용자 계정에 대 한 외부 통신 설정을 변경 하려는 경우를 가정해 보겠습니다. 예, Alex (EnablePublicCloudAccess False를 같음) Windows Live 사용자 만한 없습니다 (EnableFederationAccess는 True와 같음) 페더레이션된 사용자와 통신할 수 있도록 하려는 경우 이렇게 하려면 두 작업을 수행 해야 합니다.
  
1. 기준을 충족하는 외부 액세스 정책을 찾습니다.
    
2. 해당 외부 액세스 정책을 Alex에게 할당합니다.
    
> [!NOTE]
>  모든 사용자 지정 정책을 만들 수 없습니다 자사 합니다. 하는 비즈니스 온라인 용 Skype 허용 하지 않으므로 사용자 지정 정책을 만들 수 있습니다. 대신 Office 365에 대해 구체적으로 작성 된 정책 중 하나를 할당 해야 합니다. 미리 만든 정책은 이러한 포함: 클라이언트 정책 4 개, 회의 정책 224 개, 다이얼 플랜 5 개, 다양 한 외부 액세스 정책 5, 1 호스팅된 음성 메일 정책 및 음성 정책 4 개 있습니다.
  
어떤 외부 액세스 정책을 Alex를 할당 하는 어떻게 알 수 있을까요? 다음 명령은 여기에서 EnableFederationAccess True로 설정 하 고 EnablePublicCloudAccess False로 설정 된 모든 외부 액세스 정책을 반환 합니다.
  
```
Get-CsExternalAccessPolicy | Where-Object {$_.EnableFederationAccess -eq $True -and $_.EnablePublicCloudAccess -eq $False}
```

두 조건을 충족 하는 모든 정책을 반환 되는 명령에서 수행 하는 작업: EnableFederationAccess 속성을 True로 설정 하 고 EnablePublicCloudAccess 정책이 False로 설정 됩니다. 차례로 명령은 (FederationOnly) 기준을 충족 하는 하나의 정책을 반환 합니다. 다음은 한 예가입니다.
  
```
Identity                          : Tag:FederationOnly
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : False
EnablePublicCloudAudioVideoAccess : False
EnableOutsideAccess               : True
```

> [!NOTE]
> 정책 Id 태그: FederationOnly를 표시 합니다. 이러한, Tag: 접두사는 Microsoft Lync 2013에서 수행 하는 초기 시험판 작업 으로부터 방법입니다. 태그를 삭제 해야와 관련해 서 사용자에 게 정책을 할당 하는 경우: 접두사 및 정책 이름만 사용: FederationOnly 합니다. 
  
Alex에 게 할당 하는 정책을 파악 했으면 이제는 [Grant-csexternalaccesspolicy](https://go.microsoft.com/fwlink/?LinkId=523974) cmdlet을 사용 하 여 해당 정책을 할당 수 있습니다. 다음은 한 예가입니다.
  
```
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName "FederationOnly"
```

정책 할당 하는 것은 매우 간단: 할당할 사용자의 Id 및 정책의 이름을 지정 하면 됩니다. 
  
한 사용자 계정 사용 (영문)으로 제한 자신이 관련해 서 정책 및 정책 할당 및 시간입니다. 등 Windows Live 사용자와 페더레이션된 파트너와 통신할 수 있는 모든 사용자의 목록이 필요한 경우를 가정해 보겠습니다. 해당 사용자가 외부 사용자 액세스 정책 FederationAndPICDefault 할당 된을 이미 알고 있습니다. 많음을 알고, 때문에 하나의 간단한 명령을 실행 하 여 이러한 모든 사용자의 목록을 표시할 수 있습니다. 명령은 다음과 같습니다.
  
```
Get-CsOnlineUser -Filter {ExternalAccessPolicy -eq "FederationAndPICDefault"} | Select-Object DisplayName
```

즉, 보여줍니다 모든 사용자에 게에서는 ExternalAccessPolicy 속성은 FederationAndPICDefault으로 설정 합니다. (고쳐지고, 화면 표시 되는 정보의 양을 제한 하기 위해 표시 하는 Select-object cmdlet을 사용 우리만 각 사용자의 표시 이름입니다.) 
  
모든 사용자 계정이 같은 정책을 사용 하도록를 구성 하려면이 명령을 사용 합니다.
  
```
Get-CsOnlineUser | Grant-CsExternalAccessPolicy "FederationAndPICDefault"
```

이 명령은 Get-csonlineuser를 사용 하 여 Lync를 사용할 수 있는 다음 FederationAndPICDefault 정책을 컬렉션의 각 사용자에 게 할당 하는 Grant-csexternalaccesspolicy에 해당 정보를 모두 전송 하는 모든 사용자의 컬렉션을 반환 합니다.
  
추가 예제를 이전에 할당 한 Alex FederationAndPICDefault 정책 및 사용자의 생각을 변경 했는지 및 전역 외부 액세스 정책에 의해 관리 되는 그 구매할 이제 한다고 가정 합니다. 명시적으로 모든 사용자에 게 전역 정책의 할당할 수 없습니다. 할당 된 사용자별 정책이 없는 경우에 사용 됩니다. 따라서 경우 글로벌 정책에 의해 관리 되는 Alex을 원합니다 해야 *할당 취소 하려면* 그에 이전에 할당 된 모든 사용자별 정책. 다음은 예제 명령이입니다.
  
```
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName $Null
```

이 명령은 null 값 ($Null) Alex에 게 할당 된 외부 액세스 정책의 이름을 설정 합니다. Null "nothing"을 의미합니다. 즉, 외부 액세스 정책이 없으면 Alex에 게 할당 됩니다. 외부 액세스 정책이 없으면 사용자에 게 할당 되 면 해당 사용자 다음 가져옵니다 관리 되는 전역 정책에 의해 합니다.
  
Windows PowerShell을 사용 하 여 사용자 계정을 사용 하지 않으려면, Alex의 Skype 비즈니스 온라인 라이선스를 제거 하려면 Azure Active Directory cmdlet을 사용 합니다. 자세한 내용은 [Office 365 PowerShell을 사용 하 여 서비스에 대 한 액세스를 사용 하지 않도록 설정](assign-licenses-to-user-accounts-with-office-365-powershell.md)을 참조 하십시오.
  
## <a name="see-also"></a>참고 항목

#### 

[Office 365 PowerShell을 사용하여 비즈니스용 Skype Online 관리](manage-skype-for-business-online-with-office-365-powershell.md)
  
[Office 365 PowerShell 사용한 Office 365 관리](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell 시작](getting-started-with-office-365-powershell.md)

