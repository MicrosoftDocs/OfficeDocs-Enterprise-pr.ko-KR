---
title: PowerShell을 사용하여 Microsoft 365로 컷오버 마이그레이션 수행
ms.author: sirkkuw
author: sirkkuw
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.assetid: b468cb4b-a35c-43d3-85bf-65446998af40
description: Microsoft 365로 마이그레이션을 수행 하 여 PowerShell을 사용 하 여 원본 전자 메일 시스템에서 콘텐츠를 한 번에 이동 하는 방법에 대해 알아봅니다.
ms.openlocfilehash: fde0795b767f908fb0d1dcc5ce17a0bb50235d8e
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606224"
---
# <a name="use-powershell-to-perform-a-cutover-migration-to-microsoft-365"></a>PowerShell을 사용하여 Microsoft 365로 컷오버 마이그레이션 수행

*이 문서는 Microsoft 365 Enterprise와 Office 365 Enterprise에 모두 적용됩니다.*

단순 마이그레이션을 사용 하 여 원본 전자 메일 시스템의 사용자 사서함 내용을 한 번에 Microsoft 365로 마이그레이션할 수 있습니다. 이 문서에서는 Exchange Online PowerShell을 사용하는 전자 메일 단독형 마이그레이션 작업을 살펴봅니다. 
  
이 항목을 검토 하 여 [Microsoft 365로 전자 메일 마이그레이션에 대해 알아야 할 사항](https://go.microsoft.com/fwlink/p/?LinkId=536688)에 대해 설명 하 고 마이그레이션 프로세스에 대 한 개요를 볼 수 있습니다. 이 문서 내용을 충분히 이해할 수 있으면 다음을 사용하여 다른 전자 메일 시스템으로 사서함을 마이그레이션해 보세요.
  
> [!NOTE]
> Exchange 관리 센터를 사용하여 단독형 마이그레이션을 수행할 수도 있습니다. [Microsoft 365에 전자 메일 마이그레이션](https://go.microsoft.com/fwlink/p/?LinkId=536689)완료를 참조 하세요. 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>시작하기 전에 알아야 할 내용

이 작업의 예상 완료 시간: 2-5분(마이그레이션 일괄 처리 만들기에 소요되는 시간). 마이그레이션 일괄 처리가 시작되면 마이그레이션 기간은 일괄 처리의 사서함 수, 각 사서함의 크기 및 사용 가능한 네트워크 용량에 따라 달라집니다. 사서함을 Microsoft 365로 마이그레이션하는 데 걸리는 시간에 영향을 주는 다른 요인에 대 한 자세한 내용은 [마이그레이션 성능을](https://go.microsoft.com/fwlink/p/?LinkId=275079)참조 하십시오.
  
이 절차를 수행하려면 먼저 사용 권한을 할당받아야 합니다. 필요한 사용 권한을 확인하려면 [받는 사람 사용 권한](https://go.microsoft.com/fwlink/p/?LinkId=534105)의 표에 나오는 "마이그레이션" 항목을 참조하세요.
  
Exchange Online PowerShell cmdlet을 사용하려면 로그인한 후 cmdlet을 로컬 Windows PowerShell 세션으로 가져와야 합니다. 해당 지침은 [원격 PowerShell을 사용하여 Exchange Online에 연결](https://go.microsoft.com/fwlink/p/?LinkId=534121)을 참조하세요.
  
전체 마이그레이션 명령 목록을 보려면 [이동 및 마이그레이션 cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=534750)을 참조하세요.
  
## <a name="migration-steps"></a>마이그레이션 단계

### <a name="step-1-prepare-for-a-cutover-migration"></a>1단계: 단독형 마이그레이션 준비
<a name="BK_Step1"> </a>

- **온-프레미스 Exchange 조직을 Microsoft 365 조 직의 허용 도메인으로 추가 합니다.** 마이그레이션 서비스는 온-프레미스 사서함의 SMTP 주소를 사용 하 여 새 Microsoft 365 사서함에 대 한 Microsoft Online Services 사용자 ID 및 전자 메일 주소를 만듭니다. Exchange 도메인이 Microsoft 365 조직의 주 도메인 또는 허용 도메인이 아니면 마이그레이션이 실패 합니다. 자세한 내용은 [도메인 확인](https://go.microsoft.com/fwlink/p/?LinkId=534110)을 참조 하세요.
    
- **온-프레미스 Exchange 서버에서 "외부에서 Outlook 사용" 구성** 전자 메일 마이그레이션 서비스에서 RPC over HTTP나 "외부에서 Outlook 사용"을 사용하여 온-프레미스 Exchange 서버에 연결합니다. Exchange 2010, Exchange 2007 및 Exchange 2003용 "외부에서 Outlook 사용"을 설정하는 방법은 다음을 참조하십시오.
    
  - [Exchange 2010: "외부에서 Outlook 사용" 설정](https://go.microsoft.com/fwlink/?LinkID=187249)
    
  - [Exchange 2007: 외부에서 Outlook 사용 설정 방법](https://go.microsoft.com/fwlink/?LinkID=167210)
    
  - [Exchange 2003: RPC over HTTP에 대한 배포 시나리오](https://go.microsoft.com/fwlink/?LinkID=73657)
    
  - [Exchange 2003: "외부에서 Outlook 사용" 구성 방법](https://go.microsoft.com/fwlink/?LinkID=167209)
    
    > [!IMPORTANT]
    > "외부에서 Outlook 사용"은 신뢰할 수 있는 CA(인증 기관)에서 발급한 인증서를 통해 구성해야 합니다. 자체 서명된 인증서로는 구성할 수 없습니다. 자세한 내용은 ["외부에서 Outlook 사용"에 대한 SSL 구성 방법](https://go.microsoft.com/fwlink/?LinkID=80875)을 참조하세요. 
  
- **Outlook Anywhere를 사용하여 Exchange 조직에 연결할 수 있는지 확인** 다음 방법 중 하나를 사용하여 연결 설정을 테스트해 봅니다.
    
  - 회사 네트워크 외부에서 Microsoft Outlook을 사용하여 온-프레미스 Exchange 사서함에 연결합니다.
    
  - Microsoft [Exchange Remote Connectivity Analyzer](https://www.testexchangeconnectivity.com/)를 사용하여 연결 설정을 테스트합니다. 외부에서 Outlook 사용(RPC over HTTP)이나 Outlook 자동 검색 테스트를 사용합니다.
    
  - Exchange Online PowerShell에서 다음 명령을 실행합니다.
    
  ```
  $Credentials = Get-Credential
  ```

  ```
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

- **온-프레미스 사용자 계정에 Exchange 조직의 사서함에 액세스하는 데 필요한 사용 권한 할당** 온-프레미스 Exchange 조직 (마이그레이션 관리자 라고도 함)에 연결 하는 데 사용 하는 온-프레미스 사용자 계정에는 Microsoft 365로 마이그레이션할 온-프레미스 사서함에 액세스 하는 데 필요한 권한이 있어야 합니다. 이 사용자 계정은 온-프레미스 조직에 대한 마이그레이션 끝점을 만드는 데 사용됩니다.
    
    다음 목록에는 단독형 마이그레이션을 사용하여 사서함을 마이그레이션하는 데 필요한 관리 권한이 나와 있으며, 세 개의 옵션이 제공됩니다.
    
  - 마이그레이션 관리자는 온-프레미스 조직의 Active Directory에 있는 **Domain Admins** 그룹의 구성원이어야 합니다.
    
    또는
    
  - 마이그레이션 관리자에게 각 온-프레미스 사서함에 대한 **모든 권한** 권한이 할당되어야 합니다.
    
    또는
    
  - 마이그레이션 관리자에게 사용자 사서함을 저장하는 온-프레미스 사서함 데이터베이스에 대한 **다음으로 받기** 권한이 할당되어야 합니다.
    
- **통합 메시징을 사용하지 않도록 설정** 마이그레이션하려는 온-프레미스 사서함이 UM(통합 메시징)을 사용할 수 있도록 설정된 경우 마이그레이션 전에 사서함에서 UM을 사용하지 않도록 설정해야 합니다. 마이그레이션이 완료된 후 사서함에서 UM을 사용하도록 설정할 수 있습니다.
    
- **보안 그룹 및 대리인** 전자 메일 마이그레이션 서비스는 온-프레미스 Active Directory 그룹이 보안 그룹 인지 여부를 검색할 수 없으므로 마이그레이션된 그룹을 Microsoft 365의 보안 그룹으로 프로 비전 할 수 없습니다. Microsoft 365 테 넌 트에 보안 그룹을 포함 하려면 먼저 Microsoft 365 테 넌 트에서 빈 메일 사용 가능 보안 그룹을 프로 비전 한 후에 기본 마이그레이션을 시작 해야 합니다. 또한 이 마이그레이션 방법을 사용하는 경우에는 사서함, 메일 사용자, 메일 연락처 및 메일 사용 가능 그룹만 이동됩니다. 사용자가 Microsoft 365로 마이그레이션되지 않은 다른 Active Directory 개체 (예: 마이그레이션 대상 개체에 관리자 또는 위임)를 할당 한 경우에는 마이그레이션하기 전에 개체에서 제거 해야 합니다.
    
### <a name="step-2-create-a-migration-endpoint"></a>2단계: 마이그레이션 끝점 만들기
<a name="BK_Step2"> </a>

전자 메일을 성공적으로 마이그레이션하려면 Microsoft 365에서 원본 전자 메일 시스템과 연결 하 여 통신 해야 합니다. 이 작업을 수행 하기 위해 Microsoft 365는 마이그레이션 끝점을 사용 합니다. 단독형 마이그레이션을 위한 "외부에서 Outlook 사용" 마이그레이션 끝점을 만들려면 먼저 [Exchange Online에 연결](https://go.microsoft.com/fwlink/p/?LinkId=534121)합니다. 
  
전체 마이그레이션 명령 목록을 보려면 [이동 및 마이그레이션 cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=534750)을 참조하세요.
  
Exchange Online PowerShell에서 다음 명령을 실행합니다.
  
```
$Credentials = Get-Credential
```

이 예에서는 [Test-MigrationServerAvailability](https://go.microsoft.com/fwlink/p/?LinkId=534752) cmdlet을 사용하여 온-프레미스 Exchange 서버에 대한 연결 설정을 가져오고 테스트한 다음 해당 연결 설정을 사용하여 "CutoverEndpoint"라는 마이그레이션 끝점을 만듭니다.
  
```
$TSMA = Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress administrator@contoso.com -Credentials $credentials
```

```
New-MigrationEndpoint -ExchangeOutlookAnywhere -Name CutoverEndpoint -ConnectionSettings $TSMA.ConnectionSettings
```

> [!NOTE]
> **New-MigrationEndpoint** cmdlet을 사용하여 **-TargetDatabase** 옵션을 통해 서비스에서 사용할 데이터베이스를 지정할 수 있습니다. 그렇지 않으면 데이터베이스는 관리 사서함이 있는 AD FS(Active Directory Federation Services) 2.0 사이트에서 임의로 할당됩니다.
  
#### <a name="verify-it-worked"></a>작동하는지 확인

Exchange Online PowerShell에서 다음 명령을 실행하여 "CutoverEndpoint" 마이그레이션 끝점에 대한 정보를 표시합니다.
  
```
Get-MigrationEndpoint CutoverEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*

```

### <a name="step-3-create-the-cutover-migration-batch"></a>3단계: 단독형 마이그레이션 일괄 처리 만들기
<a name="BK_Step3"> </a>

Exchange Online PowerShell에서 **New-MigrationBatch** cmdlet을 사용하여 단독형 마이그레이션을 위한 마이그레이션 일괄 처리를 만들 수 있습니다. _AutoStart_ 매개 변수를 포함하면 마이그레이션 일괄 처리를 만들고 자동으로 시작할 수 있습니다. 또는 마이그레이션 일괄 처리를 만들고 **Start-MigrationBatch** cmdlet을 사용하여 나중에 마이그레이션을 수동으로 시작할 수 있습니다. 이 예에서는 "CutoverBatch"라는 마이그레이션 일괄 처리를 만든 다음 이전 예에서 만든 마이그레이션 끝점을 사용합니다.
  
```
New-MigrationBatch -Name CutoverBatch -SourceEndpoint CutoverEndpoint -AutoStart
```

또한 이 예에서는 "CutoverBatch"라는 마이그레이션 일괄 처리를 만든 다음 이전 예에서 만든 마이그레이션 끝점을 사용합니다.  _AutoStart_ 매개 변수가 포함되지 않으므로 마이그레이션 일괄 처리가 마이그레이션 대시보드나 **Start-MigrationBatch** cmdlet을 사용하여 수동으로 시작되어야 합니다. 앞서 설명했듯이 단독형 마이그레이션 일괄 처리는 한 번에 하나만 실행됩니다.
  
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

### <a name="step-5-route-your-email-to-microsoft-365"></a>5 단계: Microsoft 365로 전자 메일 라우팅
<a name="BK_Step5"> </a>

전자 메일 시스템은 MX 레코드라는 DNS 레코드를 사용하여 전자 메일을 배달할 위치를 확인합니다. 전자 메일 마이그레이션 프로세스 중에는 MX 레코드가 원본 전자 메일 시스템을 가리켰습니다. Microsoft 365로 전자 메일 마이그레이션이 완료 되었으므로 Microsoft 365에서 MX 레코드를 가리켜야 합니다. 이렇게 하면 전자 메일이 Microsoft 365 사서함으로 배달 됩니다. MX 레코드를 이동하여 준비가 되었을 때 이전 전자 메일 시스템을 해제할 수도 있습니다. 
  
DNS 공급자가 많이 있으므로 [MX 레코드를 변경](https://go.microsoft.com/fwlink/p/?LinkId=279163)하기 위한 특정 지침이 제공됩니다. 사용자의 DNS 공급자가 여기에 포함되지 않거나 일반적인 지침을 원하는 경우를 위해 [일반 MX 레코드 지침](https://go.microsoft.com/fwlink/?LinkId=397449)도 제공됩니다.
  
고객 및 파트너의 전자 메일 시스템에서 변경된 MX 레코드를 인식하는 데는 최대 72시간이 걸릴 수 있습니다. 다음 작업을 계속 진행하기 전에 적어도 72시간 동안 기다립니다. [6단계: 단독형 마이그레이션 일괄 처리 삭제](use-powershell-to-perform-a-cutover-migration-to-office-365.md#Bk_step6). 
  
### <a name="step-6-delete-the-cutover-migration-batch"></a>6단계: 단독형 마이그레이션 일괄 처리 삭제
<a name="Bk_step6"> </a>

MX 레코드를 변경 하 고 모든 전자 메일이 Microsoft 365 사서함으로 라우팅되는 것을 확인 한 후에는 메일이 Microsoft 365로 이동 중임을 사용자에 게 알립니다. 그런 후에는 단독형 마이그레이션 일괄 처리를 삭제해도 됩니다. 마이그레이션 일괄 처리를 삭제하기 전에 다음을 확인합니다.
  
- 모든 사용자가 Microsoft 365 사서함을 사용 하 고 있습니다. 일괄 처리가 삭제 된 후에는 온-프레미스 Exchange 서버의 사서함에 전송 된 메일이 해당 Microsoft 365 사서함에 복사 되지 않습니다.
    
- Microsoft 365 사서함은 메일이 직접 전송 되기 시작한 후에 한 번 이상 동기화 되었습니다. 이렇게 하려면 메일이 Microsoft 365 사서함으로 직접 라우팅되는 시기 보다 마이그레이션 일괄 처리에 대 한 마지막 동기화 시간 상자의 값이 최신 상태 인지 확인 합니다.
    
Exchange Online PowerShell에서 "CutoverBatch" 마이그레이션 일괄 처리를 삭제하려면 다음 명령을 실행합니다.
  
```
Remove-MigrationBatch -Identity CutoverBatch
```

### <a name="section-7-assign-user-licenses"></a>섹션 7: 사용자 라이선스 할당
<a name="BK_Step7"> </a>

 **라이선스를 할당 하 여 마이그레이션된 계정에 대해 Microsoft 365 사용자 계정을 정품 인증 합니다.** 라이선스를 할당하지 않은 경우 30일 유예 기간이 끝나면 사서함을 사용할 수 없습니다. Microsoft 365 관리 센터에서 라이선스를 할당 하려면 [라이선스 할당 또는](https://docs.microsoft.com/microsoft-365/admin/manage/assign-licenses-to-users)할당 해제를 참조 하세요.
  
### <a name="step-8-complete-post-migration-tasks"></a>8단계: 마이그레이션 후 작업 완료
<a name="BK_Step8"> </a>

- **사용자가 자신의 사서함으로 쉽게 이동할 수 있도록 자동 검색 DNS 레코드를 만듭니다.** 모든 온-프레미스 사서함이 Microsoft 365로 마이그레이션된 후에는 사용자가 Outlook 및 모바일 클라이언트를 사용 하 여 새 Microsoft 365 사서함에 쉽게 연결할 수 있도록 Microsoft 365 조 직에 대 한 자동 검색 DNS 레코드를 구성할 수도 있습니다. 이 새로운 자동 검색 DNS 레코드는 Microsoft 365 조직에 사용 중인 것과 동일한 네임 스페이스를 사용 해야 합니다. 예를 들어 클라우드 기반 네임스페이스가 cloud.contoso.com인 경우 만들어야 할 자동 검색 DNS 레코드는 autodiscover.cloud.contoso.com입니다.
    
    Exchange 서버를 유지 하는 경우 Outlook 클라이언트에서 올바른 사서함에 연결 하기 위해 마이그레이션 후 내부 및 외부 DNS에서 자동 검색 DNS CNAME 레코드가 Microsoft 365을 가리키는지 확인 해야 합니다.
    
    > [!NOTE]
    >  또한 Exchange 2007, Exchange 2010 및 Exchange 2013에서  `Set-ClientAccessServer AutodiscoverInternalConnectionURI`를  `Null`로 설정해야 합니다. 
  
    Microsoft 365는 CNAME 레코드를 사용 하 여 Outlook 및 모바일 클라이언트에 대 한 자동 검색 서비스를 구현 합니다. Autodiscover CNAME 레코드에는 다음과 같은 정보가 포함되어야 합니다.
    
  - **별칭:** autodiscover
    
  - **대상:** autodiscover.outlook.com
    
    자세한 내용은 [DNS 레코드를 추가 하 여 도메인 연결](https://go.microsoft.com/fwlink/p/?LinkId=535028)을 참조 하십시오.
    
- **온-프레미스 Exchange 서버를 해제합니다.** 모든 전자 메일이 Microsoft 365 사서함으로 바로 라우팅되고 있음을 확인 하 고 온-프레미스 전자 메일 조직을 더 이상 유지 관리할 필요가 없거나 SSO (single sign-on) 솔루션을 구현 하지 않아도 되는 경우 서버에서 Exchange를 제거 하 고 온-프레미스 Exchange 조직을 제거할 수 있습니다.
    
    자세한 내용은 다음 항목을 참조하십시오.
    
  - [Exchange 2010 수정 또는 제거](https://go.microsoft.com/fwlink/?LinkId=217936)
    
  - [Exchange 2007 조직 제거 방법](https://go.microsoft.com/fwlink/?LinkID=100485)
    
  - [Exchange Server 2003 제거 방법](https://go.microsoft.com/fwlink/?LinkID=56561)
    

