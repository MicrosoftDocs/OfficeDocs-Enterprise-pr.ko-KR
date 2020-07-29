---
title: PowerShell을 사용 하 여 비즈니스용 Skype Online 관리
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: 054c16e6-9fd1-4e85-a0e6-81788b8410ea
description: '요약: Microsoft 365 용 PowerShell을 사용 하 여 비즈니스용 Skype 온라인 정책, 사용자 단위 정책 및 모임 설정을 관리 합니다.'
ms.openlocfilehash: 0701fdb8a0a1f588e1c113ad7050ed516638aebc
ms.sourcegitcommit: d9abb99b336170f07b8f3f6d00fac19ad2159d3a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/28/2020
ms.locfileid: "46502613"
---
# <a name="manage-skype-for-business-online-with-powershell"></a>PowerShell을 사용 하 여 비즈니스용 Skype Online 관리

*이 문서는 Microsoft 365 Enterprise와 Office 365 Enterprise에 모두 적용됩니다.*

비즈니스용 Skype 온라인 관리자의 기본 작업 중 하나는 정책을 관리하는 것입니다. Microsoft 365 관리 센터에서 이러한 작업 중 일부를 수행할 수는 있지만, PowerShell에서 다른 작업은 훨씬 빠르고 간편 합니다. 

## <a name="before-you-start"></a>시작하기 전에

[비즈니스용 Skype Online 커넥터 모듈](https://www.microsoft.com/download/details.aspx?id=39366)을 다운로드 하 여 설치한 다음 컴퓨터를 다시 시작 합니다.


## <a name="connect-using-a-skype-for-business-online-administrator-account-name-and-password"></a>비즈니스용 Skype 온라인 관리자 계정 이름 및 암호를 사용 하 여 연결

1. Windows PowerShell 명령 프롬프트를 열고 다음 명령을 실행 합니다. 
    
   ```powershell
   Import-Module SkypeOnlineConnector
   $userCredential = Get-Credential
   $sfbSession = New-CsOnlineSession -Credential $userCredential
   Import-PSSession $sfbSession
   ```

2. **Windows PowerShell 자격 증명 요청** 대화 상자에서 비즈니스용 Skype Online 관리자 계정 이름 및 암호를 입력 하 고 **확인**을 클릭 합니다.


## <a name="connect-using-a-skype-for-business-online-administrator-account-with-multi-factor-authentication"></a>Multi-factor authentication을 사용 하 여 비즈니스용 Skype Online 관리자 계정을 사용 하 여 연결

1. Windows PowerShell 명령 프롬프트를 열고 다음 명령을 실행 합니다.

   ```powershell
   Import-Module SkypeOnlineConnector
   $sfbSession = New-CsOnlineSession
   Import-PSSession $sfbSession
   ```

2. **CsOnlineSession** 명령에서 메시지가 표시 되 면 비즈니스용 Skype Online 관리자 계정 이름을 입력 합니다.

3. **계정에 로그인** 대화 상자에서 비즈니스용 Skype Online 관리자 암호를 입력 하 고 **로그인**을 클릭 합니다.

4. **계정에 로그인** 대화 상자의 지침에 따라 확인 코드와 같은 추가 인증 정보를 제공 하 고 **확인**을 클릭 합니다.

자세한 내용은 다음 항목을 참조하세요.
  
- [PowerShell을 사용 하 여 비즈니스용 Skype Online 정책 관리](manage-skype-for-business-online-policies-with-office-365-powershell.md)
    
- [PowerShell을 사용 하 여 비즈니스용 Skype Online 정책 할당](assign-per-user-skype-for-business-online-policies-with-office-365-powershell.md)
    
## <a name="see-also"></a>참고 항목

[PowerShell로 Microsoft 365 관리](manage-office-365-with-office-365-powershell.md)
  
[Microsoft 365 용 PowerShell 시작](getting-started-with-office-365-powershell.md)

[비즈니스용 Skype PowerShell cmdlet 참조](https://docs.microsoft.com/powershell/module/skype/?view=skype-ps)

