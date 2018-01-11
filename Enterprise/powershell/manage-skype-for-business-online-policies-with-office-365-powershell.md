---
title: "Office 365 PowerShell을 사용 하 여 온라인 비즈니스 정책을 용 Skype 관리"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: 
ms.assetid: ff93a341-6f0f-4f06-9690-726052e1be64
description: "요약:는 Office 365 PowerShell을 사용 하 여 Skype 정책 사용 하 여 비즈니스 온라인 사용자 계정 속성을 관리할 수 있습니다."
ms.openlocfilehash: 6698bd43b2a55e1c98fbe8e536a46e2de604b4d2
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/11/2018
---
# <a name="manage-skype-for-business-online-policies-with-office-365-powershell"></a>Office 365 PowerShell을 사용 하 여 온라인 비즈니스 정책을 용 Skype 관리

 **요약:** Office 365 PowerShell을 사용 하 여 정책 사용 하 여 비즈니스 온라인 사용자 계정 속성에 대 한 사용자 Skype 관리.
  
사용자 계정에 대 한 여러 속성이 Skype에 대 한 비즈니스 online을 관리 하려면 Office 365 powershell 정책의 속성으로 지정 해야 있습니다.
  
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
    
## <a name="manage-user-account-policies"></a>사용자 계정 정책 관리

비즈니스 온라인 사용자 계정 속성에 대 한 많은 Skype 정책을 사용 하 여 구성 됩니다. 정책은 단순히 설정 컬렉션을 하나 이상의 사용자에 게 적용할 수 있는 됩니다. 방법에 대 한 정보를 사용 하는 정책이 구성 되었는지, FederationAndPICDefault 정책에 대 한이 예에서는 명령을 실행할 수 있습니다.
  
```
Get-CsExternalAccessPolicy -Identity "FederationAndPICDefault"
```

차례로 않았다고 다시 다음과 비슷한 됩니다.
  
```
Identity                          : Tag:FederationAndPICDefault
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : True
EnablePublicCloudAudioVideoAccess : True
EnableOutsideAccess               : True
```

이 예제에서는이 정책에 포함 된 값을 사용할 수 있는 확인 또는 페더레이션된 사용자와의 통신에 있어 할 수 없는 합니다. 예, EnableOutsideAccess 속성은 사용자 조직 외부의 사용자와 통신할 수 있도록 하려면 True로 설정 해야 합니다. 이 속성은 Office 365 관리 센터에 나타나지 않는 메모 합니다. 대신 속성은 True로 자동 설정 또는 false를 반환 하는 다른 선택 영역에 기반 합니다. 관심 다른 두 속성은:
  
- **EnableFederationAccess** 는 사용자가 페더레이션된 도메인의에서 사용자와 통신할 수 있는지 여부를 나타냅니다.
    
- **EnablePublicCloudAccess** 는 사용자 Windows Live 사용자와 통신할 수 있는지 여부를 나타냅니다.
    
따라서 사용자 계정 (예: **Set-csuser-EnableFederationAccess $True**)에서 페더레이션과 관련 된 속성을 직접 변경 하지 않습니다. 대신이 계정을 미리 구성 된 원하는 속성 값을 갖는 외부 액세스 정책을 할당 합니다. Windows Live 사용자와 페더레이션된 사용자와 통신할 수 있도록 사용자를 원합니다 하는 경우 해당 사용자 계정은 이러한 유형의 통신을 허용 하는 정책을 할당 되어야 합니다.
  
다른 사용자 조직 외부의 사용자와 통신할 수 있는지 여부를 확인 하려는 경우 해야 합니다.
  
- 해당 사용자에게 할당된 외부 액세스 정책 확인
    
- 해당 정책에서 허용되거나 허용되지 않는 기능 확인
    
예,이 명령을 사용 하 여를 수행할 수 있습니다.
  
```
Get-CsOnlineUser -Identity "Alex Darrow" | ForEach {Get-CsExternalAccessPolicy -Identity $_.ExternalAccessPolicy}
```

이 명령은 사용자, 다음 기능 사용 하거나 사용 하지 않도록를 설정 하 여 해당 정책 내에서 검색에 할당 된 정책을 찾습니다.
  
정책 수정 또는 만들기 (영문)에 대 한 없는 cmdlet은 메모 합니다. Office 365에서 제공한 미리 정책을 사용 해야 합니다. 사용할 수 있는 다른 정책에 대 한 정보를 사용 하려는 경우에 이러한 명령을 사용할 수 있습니다.
  
- Get-csclientpolicy       
- Get-csconferencingpolicy        
- Get-csdialplan            
- Get-csexternalaccesspolicy                         
- Get-cshostedvoicemailpolicy                        
- Get-cspresencepolicy                               
- Get-csvoicepolicy                                  

> [!NOTE]
> 비즈니스 온라인 다이얼 플랜에 대 한 Skype에 이름 제외한 모든 측면에서 정책입니다. 예: "전화를 걸 정책" 대신 "다이얼 플랜" 이름 선택 되었습니다 Office Communications Server와 Exchange 이전 버전과 호환성을 제공할 수 있도록 합니다. 
  
등 전혀 확인에 사용 하기 위해 사용할 수 있는 음성 정책이이 명령을 실행 합니다.
  
```
Get-CsVoicePolicy
```

> [!NOTE]
> 사용자의 사용 가능한 모든 음성 정책 목록을 반환합니다. 그러나 일부 정책을 모든 사용자에 게 할당할 수 있는 염두에 두어야 합니다. 라이선스 및 지리적 위치와 관련 된 다양 한 제한으로 인해입니다. (즉, "[사용 현황 위치](https://msdn.microsoft.com/en-us/library/azure/dn194136.aspx)입니다.") 외부 액세스 정책 및 특정 사용자에 게 할당할 수 있는 회의 정책 확인 하려는 경우에 다음과 유사한 명령을 사용 합니다. 

```
Get-CsConferencingPolicy -ApplicableTo "Alex Darrow"
Get-CsExternalAccessPolicy -ApplicableTo "Alex Darrow"
```

ApplicableTo 매개 변수는 반환되는 데이터를 지정된 사용자(여기서는 Alex Darrow)에게 할당 가능한 정책으로 제한합니다. 라이선스 및 사용 위치 제한에 따라 사용 가능한 모든 정책 중 일부분이 표시될 수 있습니다. 
  
경우에 따라 정책의 속성은 Microsoft 지원 담당자 여만 관리할 수 있는 다른 사용자에 게 하는 동안 Office 365와 함께 사용 되지 않습니다. 
  
온라인 비즈니스에 대 한 Skype와는 일종의 정책에 의해 사용자를 관리 해야 합니다. 유효한 정책 관련 속성이 비어 있으면 해당 사용자에는 자신이 사용자별 정책이 특별히 할당 하지 않은 경우 사용자에 게 자동으로 적용 되는 정책 인 전역 정책에 의해 관리 되는 것입니다. 사용자 계정에 대해 나열 된 클라이언트 정책 보이지을 하기 때문에 전역 정책에 의해 관리 됩니다. 이 명령 사용 하 여 전역 클라이언트 정책을 확인할 수 있습니다.
  
```
Get-CsClientPolicy -Identity "Global"
```

## <a name="see-also"></a>참고 항목

#### 

[Office 365 PowerShell을 사용하여 비즈니스용 Skype Online 관리](manage-skype-for-business-online-with-office-365-powershell.md)
  
[Office 365 PowerShell 사용한 Office 365 관리](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell 시작](getting-started-with-office-365-powershell.md)

