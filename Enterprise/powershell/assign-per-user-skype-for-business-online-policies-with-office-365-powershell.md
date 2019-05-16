---
title: Office 365 powershell 비즈니스 온라인 정책에 대 한 사용자 당 Skype 할당
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: 36743c86-46c2-46be-b9ed-ad9d4e85d186
description: '요약: Office 365 PowerShell을 사용 하 여 비즈니스용 Skype 온라인 정책에 대 한 사용자 단위 통신 설정을 할당 합니다.'
ms.openlocfilehash: 3c6c869874329d7efb6d8c417c797c9f81df6bf8
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069294"
---
# <a name="assign-per-user-skype-for-business-online-policies-with-office-365-powershell"></a>Office 365 powershell 비즈니스 온라인 정책에 대 한 사용자 당 Skype 할당

 **요약:** Office 365 PowerShell을 사용 하 여 비즈니스용 Skype 온라인 정책에 대 한 사용자별 통신 설정을 할당 합니다.
  
Office 365 PowerShell을 사용 하는 것은 비즈니스용 Skype 온라인 정책에 따라 사용자별 통신 설정을 효율적으로 할당 하는 효율적인 방법입니다.
  
## <a name="before-you-begin"></a>시작하기 전에

다음 절차에 따라 명령을 실행 하도록 설정 합니다 (이미 완료 한 단계 건너뛰기).
  
1. [비즈니스용 Skype Online 커넥터 모듈](https://www.microsoft.com/en-us/download/details.aspx?id=39366)을 다운로드 하 고 설치 합니다.
    
2. Windows PowerShell 명령 프롬프트를 열고 다음 명령을 실행 합니다. 
    
  ```
  Import-Module LyncOnlineConnector
$userCredential = Get-Credential
$sfbSession = New-CsOnlineSession -Credential $userCredential
Import-PSSession $sfbSession
  ```
메시지가 나타나면 비즈니스용 Skype Online 관리자 계정 이름 및 암호를 입력 합니다.
    
## <a name="updating-external-communication-settings-for-a-user-account"></a>사용자 계정에 대 한 외부 통신 설정 업데이트

사용자 계정에 대 한 외부 통신 설정을 변경 하려는 경우를 예로 들 수 있습니다. 예를 들어 Alex가 페더레이션 사용자와 통신할 수 있도록 허용 하려는 경우 (EnableFederationAccess이 True 인 경우) Windows Live users (EnablePublicCloudAccess와 False)는 사용 하지 않는 것이 좋습니다. 이렇게 하려면 다음과 같은 두 가지 작업을 수행 해야 합니다.
  
1. 기준을 충족하는 외부 액세스 정책을 찾습니다.
    
2. 해당 외부 액세스 정책을 Alex에게 할당합니다.
    
> [!NOTE]
>  사용자 지정 정책을 직접 만들 수는 없습니다. 비즈니스용 Skype Online에서는 사용자 지정 정책을 만들 수 없기 때문입니다. 대신 특별히 Office 365에 대해 만들어진 정책 중 하나를 할당 해야 합니다. 미리 만든 정책에는 4 가지 다른 클라이언트 정책, 224 다른 회의 정책, 5 가지 다이얼 플랜, 5 다른 외부 액세스 정책, 호스트 된 음성 메일 정책 1 개 및 4 가지 음성 정책이 포함 됩니다.
  
그렇다면 Alex을 할당할 외부 액세스 정책을 어떻게 결정 합니까? 다음 명령은 EnableFederationAccess가 True로 설정되고 EnablePublicCloudAccess가 False로 설정된 모든 외부 액세스 정책을 반환합니다.
  
```
Get-CsExternalAccessPolicy | Where-Object {$_.EnableFederationAccess -eq $True -and $_.EnablePublicCloudAccess -eq $False}
```

명령이 수행 하는 작업은 EnableFederationAccess 속성을 True로 설정 하 고 EnablePublicCloudAccess 정책이 False로 설정 되어 있는 두 가지 조건을 충족 하는 모든 정책을 반환 합니다. 그런 다음이 명령은 조건을 충족 하는 하나의 정책을 반환 합니다 (FederationOnly). 예를 들면 다음과 같습니다.
  
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
> 정책 Id는 Tag: FederationOnly로 표시 됩니다. 아시다시피 Tag: 접두사는 Microsoft Lync 2013에서 진행된 초기 사전 릴리스 작업에서 이어진 것입니다. 사용자에게 정책을 할당하려는 경우에는 Tag: 접두사를 제거하고 정책 이름인 FederationOnly를 사용해야 합니다. 
  
이제 Alex에 할당할 정책을 알고 있으므로 [get-csexternalaccesspolicy](https://go.microsoft.com/fwlink/?LinkId=523974) cmdlet을 사용 하 여 해당 정책을 할당할 수 있습니다. 예를 들면 다음과 같습니다.
  
```
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName "FederationOnly"
```

정책을 할당 하는 작업은 매우 간단 하며, 사용자의 Id와 할당할 정책의 이름을 지정 하기만 하면 됩니다. 
  
정책 및 정책 할당에 대 한 작업을 수행 하는 경우에는 한 번에 한 사용자 계정을 사용 하는 것으로 제한 되지 않습니다. 페더레이션 파트너 및 Windows Live 사용자와 통신할 수 있는 모든 사용자의 목록이 필요한 경우를 예로 들어 보겠습니다. 여기서 해당 사용자에게는 외부 사용자 액세스 정책 FederationAndPICDefault가 이미 할당되어 있습니다. 이를 알고 있으므로 간단한 명령을 하나씩 실행 하 여 모든 사용자의 목록을 표시할 수 있습니다. 해당 명령은 다음과 같습니다.
  
```
Get-CsOnlineUser -Filter {ExternalAccessPolicy -eq "FederationAndPICDefault"} | Select-Object DisplayName
```

이처럼 ExternalAccessPolicy 속성이 FederationAndPICDefault로 설정된 모든 사용자가 표시됩니다. 화면에 표시 되는 정보의 양을 제한 하기 위해 Select-Object cmdlet을 사용 하 여 각 사용자의 표시 이름만 표시 합니다. 
  
모든 사용자 계정이 같은 정책을 사용 하도록 구성 하려면 다음 명령을 사용 합니다.
  
```
Get-CsOnlineUser | Grant-CsExternalAccessPolicy "FederationAndPICDefault"
```

이 명령은 Get-csonlineuser를 사용 하 여 Lync에 대해 사용 하도록 설정 된 모든 사용자의 컬렉션을 반환한 다음, 모든 해당 정보를 부여-Get-csexternalaccesspolicy로 보내 컬렉션에 있는 각 사용자에 게 FederationAndPICDefault 정책을 할당 합니다.
  
또 다른 예로, 이전에 FederationAndPICDefault 정책을 할당 했 고, 이제 생각이 변경 되었으며 전역 외부 액세스 정책에 의해 관리 되는 것을 Alex 가정해 보겠습니다. 전역 정책은 모든 사용자에 게 명시적으로 할당할 수 없습니다. 다른 사용자별 정책이 할당 되지 않은 경우에만 사용 됩니다. 따라서 전역 정책에 따라 Alex를 관리 하려면 이전에 자신에 게 할당 된 사용자별 정책을 *할당* 해제 해야 합니다. 예제 명령은 다음과 같습니다.
  
```
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName $Null
```

이 명령은 Alex에 할당 된 외부 액세스 정책의 이름을 null 값 ($Null)으로 설정 합니다. Null은 "nothing"을 의미 합니다. 즉, Alex에 외부 액세스 정책이 할당 되지 않습니다. 사용자에 게 할당 된 외부 액세스 정책이 없으면 해당 사용자는 전역 정책에 의해 관리 됩니다.
  
Windows PowerShell을 사용 하 여 사용자 계정을 사용 하지 않도록 설정 하려면 Azure Active Directory cmdlet을 사용 하 여 Alex의 비즈니스용 Skype Online 라이선스를 제거 합니다. 자세한 내용은 [Office 365 PowerShell을 사용 하 여 서비스에 대 한 액세스 비활성화](assign-licenses-to-user-accounts-with-office-365-powershell.md)를 참조 하세요.
  
## <a name="see-also"></a>참고 항목

#### 

[Office 365 PowerShell을 사용하여 비즈니스용 Skype Online 관리](manage-skype-for-business-online-with-office-365-powershell.md)
  
[Office 365 PowerShell을 사용하여 Office 365 관리](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell 시작](getting-started-with-office-365-powershell.md)

