---
title: "PowerShell을 사용하여 Office 365로 단독형 마이그레이션 수행"
ms.author: sirkkuw
author: sirkkuw
manager: scotv
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: DecEntMigration
ms.assetid: b468cb4b-a35c-43d3-85bf-65446998af40
description: "요약: Office 365에 단독형 마이그레이션을 수행 하기 위해 Windows PowerShell을 사용 하는 방법에 알아봅니다."
ms.openlocfilehash: be5a3587538c32589c20fe6d27d69a84e0b8e7db
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2017
---
# <a name="use-powershell-to-perform-a-cutover-migration-to-office-365"></a>PowerShell을 사용하여 Office 365로 단독형 마이그레이션 수행

 **요약:** Office 365에 단독형 마이그레이션을 수행 하기 위해 Windows PowerShell을 사용 하는 방법에 알아봅니다.
  
마이그레이션할 수 사용자 사서함의 내용을 원본 전자 메일 시스템에서 Office 365로 동시에 모두 단독형 마이그레이션을 사용 하 여 합니다. 이 문서에서는 Exchange Online PowerShell을 사용 하 여 전자 메일 단독형 마이그레이션에 대 한 작업을 통해 안내 합니다. 
  
[Office 365에 단독 전자 메일 마이그레이션에 대해 알고 하는데 필요한](https://go.microsoft.com/fwlink/p/?LinkId=536688)항목을 검토 하 여 마이그레이션 프로세스의 개요를 얻을 수 있습니다. 해당 문서의 내용을 사용 하 여 능숙 하 게를 사용 하 여이 하나를 시작 하려면 다른 하나의 전자 메일 시스템에서 사서함 마이그레이션입니다.
  
> [!NOTE]
> 단독형 마이그레이션을 수행 하기 위해 Exchange 관리 센터를 사용할 수도 있습니다. [전자 메일을 Office 365의 단독형 마이그레이션을 수행](https://go.microsoft.com/fwlink/p/?LinkId=536689)을 참조 하십시오. 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>시작하기 전에 알아야 할 내용

예상이 작업을 완료 시간: 2 ~ 5 분 마이그레이션 일괄 처리를 만듭니다. 마이그레이션 일괄 처리 시작 되 면 마이그레이션 기간에 따라 달라 집니다 일괄 처리의 사서함 수, 사용 가능한 네트워크 용량 및 각 사서함의 크기입니다. Office 365로 사서함 마이그레이션에 걸리는 시간에 영향을 주는 다른 요인에 대 한 정보를 [마이그레이션 성능](https://go.microsoft.com/fwlink/p/?LinkId=275079)을 참조 하십시오.
  
이 절차를 수행 하기 전에 사용 권한을 할당 해야 합니다. 필요한 사용 권한을 [받는 사람에 게 사용 권한](https://go.microsoft.com/fwlink/p/?LinkId=534105) 항목의 테이블의 "마이그레이션" 항목을 참조 하십시오.
  
Exchange Online PowerShell cmdlet을 사용 하려면 로그인 하 고 로컬 Windows PowerShell 세션으로 cmdlet을 가져올 해야 합니다. 지침에 대 한 [원격 PowerShell을 사용 하는 Exchange Online에 연결](https://go.microsoft.com/fwlink/p/?LinkId=534121) 을 참조 하십시오.
  
마이그레이션 명령 목록이 전체 [이동 및 마이그레이션 cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=534750)을 참고 하십시오.
  
## <a name="migration-steps"></a>마이그레이션 단계

### <a name="step-1-prepare-for-a-cutover-migration"></a>1단계: 단독형 마이그레이션 준비
<a name="BK_Step1"> </a>

- **온-프레미스 Exchange 조직 하 여 Office 365 조직의 허용된 도메인으로 추가 합니다.** 마이그레이션 서비스 온-프레미스 사서함의 SMTP 주소를 사용 하 여 새 Office 365 사서함에 대 한 Microsoft 온라인 서비스 사용자 ID와 전자 메일 주소를 만듭니다. 허용된 도메인 또는 Office 365 조직의 주 도메인 Exchange 도메인 없으면 마이그레이션 실패 합니다. 자세한 내용은[Office 365에서 도메인을 확인 합니다.](https://go.microsoft.com/fwlink/p/?LinkId=534110)를 참조 하십시오.
    
- **외부에서 Outlook 구성 온-프레미스 Exchange 서버에서.** 전자 메일 마이그레이션 서비스를 사용 하 여 RPC over HTTP를 또는 외부에서 Outlook 사용, 온-프레미스 Exchange 서버에 연결 합니다. 다음 Exchange 2010, Exchange 2007 및 Exchange 2003, 참조에 대 한 외부에서 Outlook 사용을 설정 하는 방법에 대 한 내용은 합니다.
    
  - [Exchange 2010: Outlook Anywhere 사용](https://go.microsoft.com/fwlink/?LinkID=187249)
    
  - [Exchange 2007: Outlook Anywhere 사용 하는 방법](https://go.microsoft.com/fwlink/?LinkID=167210)
    
  - [Exchange 2003: RPC over HTTP 배포 시나리오](https://go.microsoft.com/fwlink/?LinkID=73657)
    
  - [Exchange 2003과 함께 외부에서 Outlook을 구성 하는 방법](https://go.microsoft.com/fwlink/?LinkID=167209)
    
    > [!IMPORTANT]
    > 외부에서 Outlook 사용 구성에는 신뢰할 수 있는 CA (인증 기관)에서 발급 한 인증서로 구성 되어야 합니다. 자체 서명 된 인증서를 사용 하 여 구성할 수 없습니다. 자세한 내용은 [외부에서 Outlook 사용에 대 한 SSL을 구성 하는 방법](https://go.microsoft.com/fwlink/?LinkID=80875)을 참조 하십시오. 
  
- **외부에서 Outlook 사용을 사용 하 여 Exchange 조직에 연결할 수 있는지 확인 합니다.** 연결 설정을 테스트 하려면 다음이 방법 중 하나를 수행 합니다.
    
  - 회사 네트워크 외부에서 Microsoft Outlook을 사용하여 온-프레미스 Exchange 사서함에 연결합니다.
    
  - Microsoft [Exchange 원격 연결 분석기](https://www.testexchangeconnectivity.com/) 를 사용 하 여 연결 설정을 테스트해봅니다. 외부에서 Outlook 사용 (RPC over HTTP)를 사용 하 여 또는 Outlook 자동 검색을 테스트 합니다.
    
  - Exchange Online PowerShell에서 다음 명령을 실행합니다.
    
  ```
  $Credentials = Get-Credential
  ```

  ```
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

- **온-프레미스 사용자 계정을 Exchange 조직에서 사서함에 액세스 하는 데 필요한 사용 권한을 할당 합니다.** (Themigration 관리자 라고도 함) 하 여 온-프레미스 Exchange 조직에 연결을 사용 하는 온-프레미스 사용자 계정에는 Office 365로 마이그레이션할 수 있는 온-프레미스 사서함에 액세스 하는 데 필요한 권한이 있어야 합니다. 이 사용자 계정은 온-프레미스 조직으로 마이그레이션 끝점을 만드는 데 사용 됩니다.
    
    다음 목록에는 단독형 마이그레이션을 사용하여 사서함을 마이그레이션하는 데 필요한 관리 권한이 나와 있으며, 세 개의 옵션이 제공됩니다.
    
  - 마이그레이션 관리자에 게 온-프레미스 조직에서 Active Directory의 **Domain Admins** 그룹의 구성원 이어야 합니다.
    
    또는
    
  - 마이그레이션 관리자에 게 각 온-프레미스 사서함에 대 한 **FullAccess** 권한이 할당 되어야 합니다.
    
    또는
    
  - 마이그레이션 관리자에 게 사용자 사서함을 저장 하는 온-프레미스 사서함 데이터베이스에서 다음 **으로 받기** 권한이 할당 되어야 합니다.
    
- **통합 메시징 사용 안함.** 마이그레이션하는 온-프레미스 사서함에 대 한 UM (통합 메시징)을 사용 하는 경우 해당 마이그레이션하기 전에 UM 사서함에서 사용 하지 않도록 설정 해야 합니다. 마이그레이션이 완료 된 후에 다음 사서함에서 UM을 사용할 수 있습니다.
    
- **보안 그룹 및 대리인** 전자 메일 마이그레이션 서비스 Office 365의 보안 그룹으로 마이그레이션된 모든 그룹을 프로 비전 수 없는 것 되므로 여부, 온-프레미스 Active Directory 그룹은 보안 그룹 있는지 여부를 검색할 수 없습니다. Office 365 테 넌 트의 보안 그룹을 사용할 경우 단독형 마이그레이션을 시작 하기 전에 Office 365 테 넌 트에 빈 메일 사용이 가능한 보안 그룹을 먼저 구축 해야 있습니다. 또한이 마이그레이션 방법은 사서함, 메일 사용자, 메일 연락처 및 메일 사용이 가능한 그룹에만 이동합니다. Office 365로 마이그레이션되지 않는 사용자와 같은 다른 Active Directory 개체, 관리자 또는 마이그레이션되는 개체에 대 한 대리인으로 할당 되 면 제거 해야 개체에서 마이그레이션하기 전에 합니다.
    
### <a name="step-2-create-a-migration-endpoint"></a>2단계: 마이그레이션 끝점 만들기
<a name="BK_Step2"> </a>

전자 메일을 성공적으로 마이그레이션 Office 365에 연결 하 고 원본 전자 메일 시스템과 통신할 해야 합니다. 이 위해 Office 365 마이그레이션 끝점을 사용 합니다. 외부에서 Outlook 사용 마이그레이션 끝점 첫번째 [Exchange Online에 연결](https://go.microsoft.com/fwlink/p/?LinkId=534121)하는 단독형 마이그레이션에 대 한를 생성 합니다. 
  
마이그레이션 명령 목록이 전체 [이동 및 마이그레이션 cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=534750)을 참고 하십시오.
  
Exchange Online PowerShell에서 다음 명령을 실행합니다.
  
```
$Credentials = Get-Credential
```

이 예제에서는 [테스트 MigrationServerAvailability](https://go.microsoft.com/fwlink/p/?LinkId=534752) cmdlet를 사용 하 여 받기 및 온-프레미스 Exchange 서버에 대 한 연결 설정을 테스트 한 다음 사용 하 여 이러한 연결 설정을 마이그레이션 끝점을 만드는 이라는 "CutoverEndpoint" 합니다.
  
```
$TSMA = Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress administrator@contoso.com -Credentials $credentials
```

```
New-MigrationEndpoint -ExchangeOutlookAnywhere -Name CutoverEndpoint -ConnectionSettings $TSMA.ConnectionSettings
```

> [!NOTE]
> **New-migrationendpoint** cmdlet은 **-TargetDatabase** 옵션을 사용 하 여 사용 하 여 서비스에 대 한 데이터베이스를 지정 하는데 사용할 수 있습니다. 그렇지 않은 경우 데이터베이스는 임의로 할당에서 Active Directory Federation Services (AD FS) 2.0 사이트는 관리 사서함이 있는 합니다.
  
#### <a name="verify-it-worked"></a>작동하는지 확인

Exchange Online PowerShell에서 다음 명령을 실행하여 "CutoverEndpoint" 마이그레이션 끝점에 대한 정보를 표시합니다.
  
```
Get-MigrationEndpoint CutoverEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*

```

### <a name="step-3-create-the-cutover-migration-batch"></a>3단계: 단독형 마이그레이션 일괄 처리 만들기
<a name="BK_Step3"> </a>

온라인으로 사용할 수 **New-migrationbatch** cmdlet은 Exchange PowerShell 단독형 마이그레이션 위한 마이그레이션 일괄 처리를 만들 수 있습니다. 마이그레이션 일괄 처리를 만들고 _자동 시작_ 매개 변수를 포함 하 여 자동으로 시작할 수 있습니다. 또는 마이그레이션 일괄 처리를 만들고 수동으로 시작 나중에 **Start-migrationbatch** cmdlet을 사용 하 여 수 있습니다. "CutoverBatch" 이라는 마이그레이션 일괄 처리를 만들고 이전 단계에서 만든 마이그레이션 끝점을 사용 하 여 하는이 예제입니다.
  
```
New-MigrationBatch -Name CutoverBatch -SourceEndpoint CutoverEndpoint -AutoStart
```

이 예제에서는 또한 "CutoverBatch" 이라는 마이그레이션 일괄 처리를 만들고 이전 단계에서 만든 마이그레이션 끝점을 사용 하 여 합니다. _자동 시작_ 매개 변수는 포함 되어있지, 마이그레이션 일괄 처리 하기 때문에 마이그레이션 대시보드 또는 **Start-migrationbatch** cmdlet을 사용 하 여 수동으로 시작 합니다. 듯이 하나만 단독형 마이그레이션 일괄 처리를 한번에 존재할 수 있습니다.
  
```
New-MigrationBatch -Name CutoverBatch -SourceEndpoint CutoverEndpoint
```

#### <a name="verify-it-worked"></a>작동하는지 확인

단독형 마이그레이션을 위한 마이그레이션 일괄 처리를 성공적으로 만들었는지 확인하려면 Exchange Online PowerShell에서 다음 명령을 실행하여 새 마이그레이션 일괄 처리에 대한 정보를 표시합니다.
  
```
Get-MigrationBatch | Format-List
```

### <a name="step-4-start-the-cutover-migration-batch"></a>4단계: 단독형 마이그레이션 일괄 처리 시작
<a name="BK_Step4"> </a>

Exchange Online PowerShell에서 마이그레이션 일괄 처리를 시작하려면 다음 명령을 실행합니다. 그러면 "CutoverBatch"라는 마이그레이션 일괄 처리가 만들어집니다.
  
```
Start-MigrationBatch -Identity CutoverBatch
```

#### <a name="verify-it-worked"></a>작동하는지 확인

마이그레이션 일괄 처리가 정상적으로 시작된 경우 마이그레이션 대시보드에서 해당 상태가 동기화 중으로 지정됩니다. Exchange Online PowerShell을 사용하여 마이그레이션 일괄 처리를 성공적으로 시작했는지 확인하려면 다음 명령을 실행합니다.
  
```
Get-MigrationBatch -Identity CutoverBatch |  Format-List Status
```

### <a name="step-5-route-your-email-to-office-365"></a>5단계: Office 365로 전자 메일 라우팅
<a name="BK_Step5"> </a>

전자 메일 시스템 전자 메일을 제공 하기 위해 위치 결정 하는 MX 레코드를 호출 하는 DNS 레코드를 사용 합니다. 전자 메일 마이그레이션 프로세스 중 MX 레코드 원본 전자 메일 시스템을 가리키는 되었습니다. 이제 Office 365로 전자 메일 마이그레이션 완료 되 면 Office 365에서 MX 레코드를 가리키도록 시간입니다. 이렇게 하면 전자 메일이 Office 365 사서함으로 배달 되었는지 확인 합니다. MX 레코드를 이동 하 여 수도 준비 되 면 오래 된 전자 메일 시스템을 해제 합니다. 
  
대부분의 DNS 공급자에 대 한 구체적인 지침은 [MX 레코드를 변경할](https://go.microsoft.com/fwlink/p/?LinkId=279163)수 있습니다. DNS 공급자 포함 되어있지는 또는 표시 되는 일반 지침의 알려면 하려는 경우 [MX 레코드는 일반적인 지침](https://go.microsoft.com/fwlink/?LinkId=397449) 도 제공 됩니다.
  
변경 된 MX 레코드를 인식 하도록 고객 및 파트너의 전자 메일 시스템에 대 한 72 시간까지 걸릴 수 있습니다. 다음 작업을 계속 진행 하기 전에 72 시간 이상 대기: [6 단계: 단독형 마이그레이션 일괄 처리 삭제](use-powershell-to-perform-a-cutover-migration-to-office-365.md#Bk_step6)합니다. 
  
### <a name="step-6-delete-the-cutover-migration-batch"></a>6단계: 단독형 마이그레이션 일괄 처리 삭제
<a name="Bk_step6"> </a>

MX 레코드를 변경 하 고 모든 전자 메일이 Office 365 사서함으로 라우팅되는 확인 한 후 Office 365의 메일 될 사용자를 게 알립니다. 그런 다음, 단독형 마이그레이션 일괄 처리를 삭제할 수 있습니다. 마이그레이션 일괄 처리를 삭제 하기 전에 다음을 확인 합니다.
  
- 모든 사용자에 게 Office 365 사서함을 사용 중입니다. 일괄 처리 삭제 된 후 해당 하는 Office 365 사서함 온-프레미스 Exchange 서버에 있는 사서함으로 보낸 메일 복사 되지 않습니다.
    
- Office 365 사서함 메일에 직접 전송 되 고 시작 된 후 최소한 한번 동기화 했습니다. 이 작업을 수행 하려면 마이그레이션 일괄 처리에 대 한 마지막 동기화 시간 상자에 값 Office 365 사서함으로 직접 라우팅되는 메일을 시작 하는 경우 보다 최신 인지 확인 합니다.
    
Exchange Online PowerShell에서 "CutoverBatch" 마이그레이션 일괄 처리를 삭제하려면 다음 명령을 실행합니다.
  
```
Remove-MigrationBatch -Identity CutoverBatch
```

### <a name="section-7-assign-user-licenses"></a>섹션 7: 사용자 라이선스 할당
<a name="BK_Step7"> </a>

 **활성화 Office 365 사용자 라이선스를 할당 하 여 마이그레이션된 계정에 대 한 계정.** 라이선스를 할당 하지 않은 경우 (30 일)이 유예 기간이 끝날 때 사서함 비활성화 됩니다. Office 365 관리 센터에서 라이선스를 할당 하려면[할당 또는 비즈니스를 위한 Office 365에 대 한 라이선스를 할당 취소 하려면](https://go.microsoft.com/fwlink/?LinkId=536681)을 참조 하십시오.
  
### <a name="step-8-complete-post-migration-tasks"></a>8단계: 마이그레이션 후 작업 완료
<a name="BK_Step8"> </a>

- **사용자가 자신의 사서함에 쉽게 액세스할 수 있도록 하는 자동 검색 DNS 레코드를 만듭니다.** 모든 온-프레미스 사서함을 Office 365로 마이그레이션된 후에 사용자가 쉽게 Outlook 및 모바일 클라이언트와 함께 새로운 Office 365 사서함에 연결할 수 있도록 하 여 Office 365 조직에 대 한 자동 검색 DNS 레코드를 구성할 수 있습니다. Office 365 조직에 대해 사용 중인 동일한 네임 스페이스를 사용 하 여이 새 자동 검색 DNS 레코드에 있습니다. 클라우드 기반 네임 스페이스 cloud.contoso.com 있으면 만들어야 하는 자동 검색 DNS 레코드는, autodiscover.cloud.contoso.com 합니다.
    
    Exchange 서버를 유지 하는 경우 자동 검색 DNS CNAME 레코드를 가리키도록 내부 및 외부 DNS에서 Office 365는 마이그레이션 후 올바른 사서함에 연결 하 고 Outlook 클라이언트는 되도록에 있는지 확인도 해야 합니다.
    
    > [!NOTE]
    >  Exchange 2007, Exchange 2010 및 Exchange 2013의 설정도 해야 `Set-ClientAccessServer AutodiscoverInternalConnectionURI` 에 `Null`합니다. 
  
    Office 365 CNAME 레코드를 사용 하 여 Outlook과 모바일 클라이언트에 대 한 자동 검색 서비스를 구현 합니다. 자동 검색 CNAME 레코드는 다음 정보를 포함 해야 합니다.
    
  - **별칭:** 자동 검색
    
  - **대상:** autodiscover.outlook.com
    
    자세한 내용은 [DNS 레코드를 관리 하는 경우 Office 365 용 DNS 레코드 만들기](https://go.microsoft.com/fwlink/p/?LinkId=535028)를 참조 하십시오.
    
- **온-프레미스 Exchange 서버를 해제 합니다.** 모든 전자 메일이 Office 365 사서함으로 직접 라우팅되는 하 고 더이상 온-프레미스 조직으로 전자 메일 또는 계획이 없는 single sign on (SSO) 솔루션을 구현에 유지 하기 위해 필요를 확인 한 후에 Exchange에서 제거할 수 없습니다 사용자 서버 및 온-프레미스 Exchange 조직 제거 합니다.
    
    자세한 내용은 다음 항목을 참조하십시오.
    
  - [Exchange 2010 수정 또는 제거](https://go.microsoft.com/fwlink/?LinkId=217936)
    
  - [Exchange 2007 조직을 제거 하는 방법](https://go.microsoft.com/fwlink/?LinkID=100485)
    
  - [Exchange Server 2003을 제거 하는 방법](https://go.microsoft.com/fwlink/?LinkID=56561)
    

