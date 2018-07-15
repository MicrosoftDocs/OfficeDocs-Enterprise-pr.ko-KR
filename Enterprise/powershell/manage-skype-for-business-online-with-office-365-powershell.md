---
title: Office 365 PowerShell을 사용하여 비즈니스용 Skype Online 관리
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/22/2018
ms.audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: 054c16e6-9fd1-4e85-a0e6-81788b8410ea
description: 요약:Office 365 PowerShell을 사용하여 비즈니스용 Skype 온라인 정책, 사용자 단위 정책 및 모임 설정을 관리합니다.
ms.openlocfilehash: f490131491a026961b0a5db312df5780483eadd9
ms.sourcegitcommit: b39b8ae3b4268d6475b54e2fdb62982b2c7d9943
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/12/2018
ms.locfileid: "20319239"
---
# <a name="manage-skype-for-business-online-with-office-365-powershell"></a>Office 365 PowerShell을 사용하여 비즈니스용 Skype Online 관리

 **요약:** Office 365 PowerShell을 사용하여 비즈니스용 Skype 온라인 정책, 사용자 단위 정책 및 모임 설정을 관리합니다.
  
정책 관리는 비즈니스 온라인 관리자에 대 한 모든 Skype의 기본 작업 중 하나입니다. Office 365 관리 센터에서 이러한 작업에 대해 작업을 수행할 수 있습니다, 있지만 훨씬 더 쉽고 빠르게 Office 365 PowerShell에서 다른 작업은 있습니다. 

## <a name="before-you-start"></a>시작하기 전에

다운로드 하 고 [비즈니스 온라인 커넥터 모듈에 대 한 Skype](https://www.microsoft.com/en-us/download/details.aspx?id=39366)설치 하 고 컴퓨터를 다시 시작 하 라는 메시지를 표시 하는 경우.


## <a name="connect-using-a-skype-for-business-online-administrator-account-name-and-password"></a>온라인 비즈니스 관리자의 계정 이름 및 암호를 Skype를 사용 하 여 연결

1. Windows PowerShell 명령 프롬프트를 열고 다음 명령을 실행 합니다. 
    
  ```
  Import-Module SkypeOnlineConnector
  $userCredential = Get-Credential
  $sfbSession = New-CsOnlineSession -Credential $userCredential
  Import-PSSession $sfbSession
  ```

2. **Windows PowerShell 자격 증명 요청** 대화 상자에서 사용자 Skype 비즈니스 온라인 관리자 계정 이름 및 암호를 입력 하 고 **확인**을 클릭 합니다.


## <a name="connect-using-a-skype-for-business-online-administrator-account-with-multifactor-authentication"></a>다단계 인증을 사용 하는 비즈니스 온라인 관리자 계정에 대 한 Skype를 사용 하 여 연결

1. Windows PowerShell 명령 프롬프트를 열고 다음 명령을 실행 합니다.

  ```
  Import-Module SkypeOnlineConnector
  $sfbSession = New-CsOnlineSession
  Import-PSSession $sfbSession
  ```

2. **새로 만들기 CsOnlineSession** 명령에 의해 대화 상자가 나타나면 비즈니스 온라인 관리자 계정 이름에 대 한 사용자 Skype를 입력 합니다.

3. **사용자의 계정에 로그인** 대화 상자에서 온라인 비즈니스 관리자 암호에 대 한 사용자 Skype를 입력 하 고 **로그인**을 클릭 합니다.

4. 지침에 따라 **사용자의 계정에 로그인** 대화 상자에서을 확인 코드와 같은 추가 인증 정보를 제공 하 고 **확인**을 클릭 합니다.

자세한 내용은 다음 항목을 참조하십시오.
  
- [Office 365 PowerShell을 사용 하 여 온라인 비즈니스 정책을 용 Skype 관리](manage-skype-for-business-online-policies-with-office-365-powershell.md)
    
- [Office 365 powershell 비즈니스 온라인 정책에 대 한 사용자 당 Skype 할당](assign-per-user-skype-for-business-online-policies-with-office-365-powershell.md)
    
## <a name="see-also"></a>참고 항목

[Office 365 PowerShell 사용한 Office 365 관리](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell 시작](getting-started-with-office-365-powershell.md)

