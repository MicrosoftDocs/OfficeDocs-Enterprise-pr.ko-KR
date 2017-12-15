---
title: "DAP(위임된 액세스 권한) 파트너용 원격 Windows PowerShell을 사용하여 Exchange Online 테넌트에 연결"
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: DecEntMigration
ms.assetid: ae5f1a87-8b77-4f93-a1b8-56f800aeb283
description: "요약: 원격 Windows PowerShell을 사용 하 여 DelegatedOrg 매개 변수를 사용 하 여 Exchange Online에 연결 합니다."
ms.openlocfilehash: 9bb6a5a316f4bc23c6586da825b8755cf755f484
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2017
---
# <a name="connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated-access-permissions-dap-partners"></a>DAP(위임된 액세스 권한) 파트너용 원격 Windows PowerShell을 사용하여 Exchange Online 테넌트에 연결

 **요약:** 원격 Windows PowerShell을 사용 하 여 _DelegatedOrg_ 매개 변수를 사용 하 여 Exchange Online에 연결 합니다.
  
원격 Windows PowerShell를 사용 하면 명령줄에서 Exchange Online 설정을 관리할 수 있습니다. 로컬 컴퓨터에서 Windows PowerShell를 사용 하 여 Exchange Online에 대 한 원격 세션을 만들 수 있습니다. 해당 Exchange Online 자격 증명을 입력, 필요한 연결 설정을 제공 하 고 있는 다음 사용할 수 있도록 Exchange Online cmdlet은 로컬 Windows PowerShell 세션으로 가져올 3 단계 프로세스로 구성 됩니다.
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>시작하기 전에 알아야 할 내용

- 예상 완료 시간: 5분
    
- 다음 Windows 버전을 사용할 수 있습니다.
    
  - Windows 10
    
  - Windows 8.1 또는 Windows 8
    
  - Windows Server 2012 R2 또는 Windows Server 2012
    
  - Windows 7 SP1(서비스 팩 1)*
    
  - Windows Server 2008 R2 SP1*
    
    * 4.0 또는 Windows Management Framework 3.0 설치는.NET Framework 4.5.1 또는.NET Framework 4.5 하 고 다음 중 하나는 Windows 관리 프레임 워크에 필요 합니다. 자세한 내용은 다음 리소스를 참조 합니다.
    
  - [.NET Framework를 설치합니다.](https://go.microsoft.com/fwlink/p/?LinkId=257868)
    
  - [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) 또는[Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344)
    
- 이 항목의 절차에 적용 될 수 있는 바로 가기 키에 대 한 정보를 [Exchange 관리 센터에서 바로 가기 키](https://go.microsoft.com/fwlink/p/?LinkId=534017)를 참조 하십시오.
    
## 

> [!IMPORTANT]
> 위임 액세스 권한 (DAP) 파트너에 대해서만이 절차는 합니다. DAP 파트너 모를 경우에이 절차를 사용 하지 마십시오. 
  
DAP 파트너 신디케이션 및 클라우드 솔루션 공급자 (CSP) 파트너 됩니다. 다른 회사 네트워크 또는 전화 통신 공급자 자주 됩니다. 이러한 번들를 고객에 게 자신의 서비스 제품에 구독 합니다. 자신이 소유한 모든 자신의 고객 테에서 자동으로 자신이 관리할 수 있도록 자신의 Office 365customer 테 및 보고서에 대 한 관리 대리 (AOBO) 권한이 부여 되는 파트너 테 넌 트입니다.
  
## <a name="connect-to-exchange-online"></a>Exchange Online에 연결

1. 로컬 컴퓨터에서 Windows PowerShell을 열고 다음 명령을 실행합니다.
    
  ```
  $UserCredential = Get-Credential
  ```

    **Windows PowerShell 자격 증명 요청** 대화 상자에서 DAP 관리자의 사용자 이름 및 암호를 입력 한 다음 **확인**을 클릭 합니다.
    
2. 다음 명령을 실행 바꾸기 _<customer tenant domain name>_ 에 연결 하려는 테 넌 트 도메인의 이름으로 바꿉니다.
    
  ```
  $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell-liveid?DelegatedOrg=<customer tenant domain name>-Credential $UserCredential -Authentication Basic -AllowRedirection
  ```

    이 명령에서 중요 한 단계는 보고 정보에 액세스 하는 고객을 지정 합니다. _DelegatedOrg_ 매개 변수를 값으로 초기 도메인 이름의 FQDN을 제공한 _ConnectionURI_ 매개 변수에서이 수행 합니다. 이렇게 하면 원격 Windows PowerShell Exchange Online PowerShell 원격 Windows PowerShell에 대 한 연결할 끝점입니다. 원격 Windows PowerShell 보고서를 실행할 때마다 특정 고객의 컨텍스트에서 Office 365 보고에 연결 해야 합니다. 이 고객을 지정한 후 다음 명령 중 모든 해당 고객의 컨텍스트에서 실행 됩니다. 이렇게 하면 파트너를이 고객에 대 한 모든 사용 가능한 보고서에 액세스할 수 있습니다.
    
3. 다음 명령을 실행합니다.
    
  ```
  Import-PSSession $Session
  ```

> [!NOTE]
> 계정 아래에서 하나를 실행할 수 있는 3 개의 동시 세션의 제한이 됩니다. 작업이 완료 되는 원격 Windows PowerShell 세션의 연결을 해제 해야 합니다. 세션을 분리 하지 않고 Windows PowerShell 창을 닫으면 모든 원격 Windows PowerShell 세션을 사용할 수 있습니다를 사용할 수 및 만료 되도록 하는 세션에 대 한 대기 해야 합니다. 원격 Windows PowerShell 세션을 끊으려면 다음 명령을 실행 합니다. >`Remove-PSSession $Session`
  
## <a name="how-do-you-know-this-worked"></a>작동 여부는 어떻게 확인합니까?

3 단계 후 Exchange Online cmdlet 진행률 표시줄에서 추적 로컬 Windows PowerShell 세션으로 가져옵니다. 모든 오류가 하지 않으면 하는 경우 성공적으로 연결한 합니다. 빠른 테스트는 Exchange Online cmdlet을 실행 하는-예: **Get-mailbox** -하 고 결과 참조 하십시오.
  
오류가 발생하면 다음 요구 사항을 확인합니다.
  
- 가장 흔한 문제는 암호를 잘못 입력한 경우입니다. 세 단계를 다시 실행하고 1단계에서 사용자 이름과 암호를 입력할 때 신중하게 확인하세요.
    
- 서비스 거부 (DoS) 공격을 방지 하려면 자신이 세개의 개방형 원격 Windows PowerShell 연결만 Exchange Online 조직에 있습니다.
    
- Windows PowerShell 스크립트를 실행 하도록 구성 해야 합니다. 이 설정은 한번만 사용자 컴퓨터에 연결할 때마다 하지 구성 해야 합니다. 서명 된 스크립트를 실행 하는 Windows PowerShell을 사용 하도록 설정 하려면 관리자 권한으로 Windows PowerShell 창 ( **관리자 권한으로 실행**을 선택 하 여 연 Windows PowerShell 창)에서 다음 명령을 실행 합니다.
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

- Exchange Online에 연결을 사용 하는 계정이 원격 Windows PowerShell에 대해 활성화 되어야 합니다. 자세한 내용은 [Manage 원격 PowerShell 액세스 Exchange Online을](https://go.microsoft.com/fwlink/p/?LinkId=534018)참조 하십시오.
    
- TCP 포트 80 트래픽에 로컬 컴퓨터와 Exchange Online 사이 열려 있어야 합니다. 아마도 열려 있지만 조직에는 제한적인 인터넷 액세스 정책이 하는 경우를 고려 하는 것이.
    
## <a name="call-the-cmdlet-directly-with-invoke-command"></a>Invoke-Command를 사용하여 cmdlet 직접 호출

원격 Windows PowerShell 세션을 가져오기 (영문) 하는 모든 Exchange Online cmdlet에서 가져오는 시간이 오래 걸리는 프로세스 수 있습니다. 이 일괄 처리에서 문제가 될 수-등 때는 보고서를 실행 하거나 다른 테 넌 트에 대 한 대량 변경 작업을 수행 합니다. **Import-pssession**를 사용 하는 대신, **Invoke 명령을**사용 하 여 직접 사용 하 여 원하는 cmdlet을 호출할 수 있습니다. 예, **get 사서함** cmdlet을 호출 하려면이 구문에 대 한으로 대체 `Import-PSSession $Session`합니다.
  
```
Invoke-Command -Session $Session -ScriptBlock {Get-Mailbox}
```

## <a name="more-reporting-cmdlets"></a>자세한 보고 cmdlet 내용

이 항목에서 사용 되는 cmdlet에는 Windows PowerShell cmdlet은입니다. 이러한 cmdlet에 대 한 자세한 내용은 다음 항목을 참조 하십시오.
  
- [Get-자격 증명](https://go.microsoft.com/fwlink/p/?LinkId=389618)
    
- [새 PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389621)
    
- [Import-pssession](https://go.microsoft.com/fwlink/p/?LinkId=389619)
    
- [Remove-pssession](https://go.microsoft.com/fwlink/p/?LinkId=389620)
    
- [Set-executionpolicy](https://go.microsoft.com/fwlink/p/?LinkId=389623)
    

