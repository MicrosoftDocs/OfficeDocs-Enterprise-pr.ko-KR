---
title: "PowerShell을 사용하여 Office 365로 미리 구성된 마이그레이션 수행"
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
ms.assetid: a20f9dbd-6102-4ffa-b72c-ff813e700930
description: "요약: Office 365에 미리 구성 된 마이그레이션을 수행 하기 위해 Windows PowerShell을 사용 하는 방법에 알아봅니다."
ms.openlocfilehash: 6c3ed6c0e37f7b99d3f26056dfe1b9d989388ff3
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2017
---
# <a name="use-powershell-to-perform-a-staged-migration-to-office-365"></a>PowerShell을 사용하여 Office 365로 미리 구성된 마이그레이션 수행

 **요약:** Office 365에 미리 구성 된 마이그레이션을 수행 하기 위해 Windows PowerShell을 사용 하는 방법에 알아봅니다.
  
미리 구성 된 마이그레이션을 사용 하 여 시간에 따른 원본 전자 메일 시스템에서 사용자 사서함의 내용을 Office 365에 마이그레이션할 수 있습니다.
  
이 문서에서는 Exchange Online PowerShell을 사용 하는 미리 구성 된 전자 메일 마이그레이션에 대 한와 관련 된 작업을 안내 합니다. [Office 365로 미리 구성 된 전자 메일 마이그레이션에 대해 알고 하는데 필요한](https://go.microsoft.com/fwlink/p/?LinkId=536487), 항목, 마이그레이션 프로세스의 개요를 제공 합니다. 해당 문서의 내용을 사용 하 여 능숙 하 게를 사용 하 여이 하나를 시작 하려면 다른 하나의 전자 메일 시스템에서 사서함 마이그레이션입니다.
  
> [!NOTE]
> 미리 구성 된 마이그레이션을 수행 하기 위해 Exchange 관리 센터를 사용할 수도 있습니다. [전자 메일을 Office 365의 미리 구성 된 마이그레이션을 수행](https://go.microsoft.com/fwlink/p/?LinkId=536687)을 참조 하십시오. 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>시작하기 전에 알아야 할 내용

예상이 작업을 완료 시간: 2 ~ 5 분 마이그레이션 일괄 처리를 만듭니다. 마이그레이션 일괄 처리 시작 되 면 마이그레이션 기간에 따라 달라 집니다 일괄 처리의 사서함 수, 사용 가능한 네트워크 용량 및 각 사서함의 크기입니다. Office 365로 사서함 마이그레이션에 걸리는 시간에 영향을 주는 다른 요인에 대 한 정보를 [마이그레이션 성능](https://go.microsoft.com/fwlink/p/?LinkId=275079)을 참조 하십시오.
  
이 절차를 수행 하기 전에 사용 권한을 할당 해야 합니다. 필요한 사용 권한을 [받는 사람에 게 사용 권한](https://go.microsoft.com/fwlink/p/?LinkId=534105) 항목의 "마이그레이션" 항목을 참조 하십시오.
  
Exchange Online PowerShell cmdlet을 사용 하려면 로그인 하 고 로컬 Windows PowerShell 세션으로 cmdlet을 가져올 해야 합니다. 지침에 대 한 [원격 PowerShell을 사용 하는 Exchange Online에 연결](https://go.microsoft.com/fwlink/p/?LinkId=534121) 을 참조 하십시오.
  
마이그레이션 명령 목록이 전체 [이동 및 마이그레이션 cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=534750)을 참고 하십시오.
  
## <a name="migration-steps"></a>마이그레이션 단계

### <a name="step-1-prepare-for-a-staged-migration"></a>1단계: 미리 구성된 마이그레이션 준비

미리 구성 된 마이그레이션을 사용 하 여 Office 365로 사서함을 마이그레이션하기 전에 몇가지 변경 해야 Exchange 환경에 있습니다.
  
 **온-프레미스 Exchange 서버에서 외부에서 Outlook 사용 구성** 전자 메일 마이그레이션 서비스 온-프레미스 Exchange 서버에 연결 외부에서 Outlook 사용 (로 알려져 RPC over HTTP)을 사용 하 여. Exchange Server 2007 및 Exchange 2003에 대 한 외부에서 Outlook 사용을 설정 하는 방법에 대 한 정보를 다음을 참조 하십시오.
  
- [Exchange 2007: Outlook Anywhere 사용 하는 방법](https://go.microsoft.com/fwlink/?LinkID=167210)
    
- [Exchange 2003과 함께 외부에서 Outlook 사용을 구성 하는 방법](https://go.microsoft.com/fwlink/?LinkID=167209)
    
> [!IMPORTANT]
> 외부에서 Outlook 사용 구성 된 신뢰할 수 있는 인증 기관 (CA)에서 발급 한 인증서를 사용 해야 합니다. 자체 서명 된 인증서를 사용 하 여 외부에서 outlook 사용을 구성할 수 없습니다. 자세한 내용은 [외부에서 Outlook 사용에 대 한 SSL을 구성 하는 방법](https://go.microsoft.com/fwlink/?LinkID=80875)을 참조 하십시오. 
  
 **선택 사항: 외부에서 Outlook 사용을 사용 하 여 Exchange 조직에 연결할 수 있는지 확인** 연결 설정을 테스트 하려면 다음 방법 중 하나를 수행 합니다.
  
- 회사 네트워크 외부에서 Outlook을 사용 하 여 온-프레미스 Exchange 사서함에 연결 합니다.
    
- [Microsoft Exchange 원격 연결 분석기](https://www.testexchangeconnectivity.com/) 를 사용 하 여 연결 설정을 테스트해봅니다. 외부에서 Outlook 사용 (RPC over HTTP)를 사용 하 여 또는 Outlook 자동 검색을 테스트 합니다.
    
- Exchange Online PowerShell에서 다음 명령을 실행합니다.
    
  ```
  $Credentials = Get-Credential
  ```

  ```
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

 **사용 권한 설정** (마이그레이션 관리자에 게가 라고도 함) 하 여 온-프레미스 Exchange 조직에 연결을 사용 하는 온-프레미스 사용자 계정에는 Office 365로 마이그레이션할 수 있는 온-프레미스 사서함에 액세스 하는 데 필요한 권한이 있어야 합니다. 이 절차의 뒷부분에서 마이그레이션 끝점 만들기 (영문) 하 여 전자 메일 시스템에 연결할 때 사용 되는이 사용자 계정 ([3 단계: 마이그레이션 끝점 만들기](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Endpoint) ).
  
사서함을 마이그레이션하려면 관리자는 다음 사용 권한 집합 중 하나가 있어야 합니다.
  
- 온-프레미스 조직에서 Active Directory의 **Domain Admins** 그룹의 구성원 이어야 합니다.
    
     또는 
    
- 각 온-프레미스 사서함에 대 한 **FullAccess** 권한이 및 온-프레미스 사용자 계정에 대해 **TargetAddress** 속성을 수정 하는 **WriteProperty** 권한을 할당할 수 있습니다.
    
     또는 
    
- 사용자 사서함을 저장 하는 온-프레미스 사서함 데이터베이스에서 다음 **으로 받기** 권한이 및 온-프레미스 사용자 계정에 대해 **TargetAddress** 속성을 수정 하는 **WriteProperty** 권한을 할당할 수 있습니다.
    
이러한 사용 권한을 설정 하는 방법에 대 한 자세한 내용은 [Office 365로 사서함 마이그레이션에 사용 권한을 할당](https://go.microsoft.com/fwlink/?LinkId=521656)합니다.
  
 **통합된 메시징 (UM)를 사용 하지 않도록 설정** 온-프레미스 사서함에 대 한 UM가 설정 된 경우 마이그레이션하는 경우, 마이그레이션 전에 UM을 해제 합니다. 마이그레이션이 완료 된 후에 UM 사서함에 대 한 설정 합니다. 방법 단계에 대 한[통합 메시징 사용 안함](https://go.microsoft.com/fwlink/?LinkId=521891)를 참조 합니다.
  
 **디렉터리 동기화를 사용 하 여 Office 365에서 새 사용자를 만드는.** 디렉터리 동기화를 사용 하 여 Office 365 조직에서 모든 온-프레미스 사용자를 만들 수 있습니다.
  
만들어지면 사용자 라이선스를 할당 해야 합니다. 30 일 사용자를 만든 후 라이선스를 추가 해야 합니다. 라이선스를 추가 하는 단계를 참조 하십시오. [8 단계: 마이그레이션 이후 작업 완료](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Postmigration)합니다.
  
 Office 365의 온-프레미스 사용자를 만들고 동기화 Microsoft Azure Active Directory 동기화 도구 또는 Microsoft Azure Active Directory 동기화 서비스 (AAD 동기화) 중 하나를 사용할 수 있습니다. 사서함을 Office 365로 마이그레이션된 후 온-프레미스 조직에서 사용자 계정을 관리 하 고 Office 365 조직와 동기화 하는 것입니다. 자세한 내용은[디렉터리 통합](https://go.microsoft.com/fwlink/?LinkId=521788) 을 참조 하십시오.
  
### <a name="step-2-create-a-csv-file-for-a-staged-migration-batch"></a>2단계: 미리 구성된 마이그레이션 일괄 처리에 대한 CSV 파일 만들기

Office 365로 마이그레이션하는 온-프레미스 사서함을 소유한 사용자를 확인 한 후 마이그레이션 일괄 처리 만들기를 쉼표로 구분 된 값 (CSV) 파일을 사용 합니다. CSV 파일의 각 행-Office 365에서 사용 하 여 마이그레이션을 실행 하려면-온-프레미스 사서함에 대 한 정보를 포함 합니다. 
  
> [!NOTE]
> 미리 구성 된 마이그레이션을 사용 하 여 Office 365로 마이그레이션할 수 있는 사서함의 수에 대 한 제한이 없습니다. 마이그레이션 일괄 처리에 대 한 CSV 파일에는 2, 000 행의 최대 포함 될 수 있습니다. 2, 000 개 이상의 사서함 마이그레이션, 추가 CSV 파일 만들기 및 각 파일을 사용 하 여 새 마이그레이션 일괄 처리를 만듭니다. 
  
 **지원 되는 특성**
  
미리 구성된 마이그레이션용 CSV 파일에는 다음과 같은 세 개의 특성이 지원됩니다. CSV 파일의 각 행은 하나의 사서함에 해당하며 이러한 각 특성에 대한 값을 포함해야 합니다.
  
|**특성**|**설명**|**필수?**|
|:-----|:-----|:-----|
|전자 메일 주소  <br/> |온-프레미스 사서함에 대한 기본 SMTP 전자 메일 주소(예: pilarp@contoso.com)를 지정합니다.  <br/> 온-프레미스 사서함과 사용자는 Office 365에서 Id가 아닌에 대 한 기본 SMTP 주소를 사용 합니다. 예 온-프레미스 도메인 contoso.com 라는 하 고 Office 365의 전자 메일 도메인에 service.contoso.com를 전자 메일 주소에 대 한 contoso.com 도메인 이름을 사용 하 여 CSV 파일에는 있습니다.  <br/> |필수  <br/> |
|Password  <br/> |새 Office 365 사서함에 대해 설정 될 암호입니다. Office 365 조직에 적용 되는 모든 암호 제한 CSV 파일에 포함 된 암호에도 적용 됩니다.  <br/> |옵션  <br/> |
|ForceChangePassword  <br/> |여부 사용자 암호를 변경 해야 새 Office 365 사서함에 로그인 할 처음으로 지정 합니다. 이 매개 변수의 값에 대 한 **True** 또는 **False** 를 사용 합니다.<br/> > [!NOTE]> Active Directory Federation Services (AD FS)를 배포 하 여 single sign on (SSO) 솔루션을 구현한 경우 이상에서 온-프레미스 조직에서 **ForceChangePassword** 특성의 값에 대 한 **False** 사용 해야 합니다.          |옵션  <br/> |
   
 **CSV 파일 형식**
  
CSV 파일에 대 한 서식의 예는 다음과 같습니다. 이 예제에서는 온-프레미스 사서함이 세 개인 Office 365로 마이그레이션됩니다.
  
CSV 파일의 머리글 행을 확인 하는 첫번째 행 다음에 있는 행에 지정 된 특성 또는 필드의 이름을 나열 합니다. 각 특성 이름은 쉼표로 구분 됩니다.
  
```
EmailAddress,Password,ForceChangePassword 
pilarp@contoso.com,Pa$$w0rd,False 
tobyn@contoso.com,Pa$$w0rd,False 
briant@contoso.com,Pa$$w0rd,False 
```

머리글 행 아래의 각 행은 한 명의 사용자를 나타내며 해당 사용자의 사서함을 마이그레이션하기 위해 사용되는 정보를 제공합니다. 각 행의 특성 값은 머리글 행의 특성 이름과 동일한 순서로 나열되어야 합니다. 
  
텍스트 편집기 또는 Excel 등의 응용 프로그램을 사용하여 CSV 파일을 만들 수 있습니다. 파일을 .csv 또는 .txt 파일로 저장합니다.
  
> [!NOTE]
> CSV 파일에 ASCII가 아닌 문자 또는 특수 문자가 포함되어 있는 경우에는 CSV 파일을 UTF-8 또는 다른 유니코드 인코딩으로 저장합니다. 응용 프로그램에 따라 컴퓨터의 시스템 로캘이 CSV 파일에 사용된 언어와 일치하는 경우 CSV 파일을 UTF-8 또는 다른 유니코드 인코딩으로 저장하는 것이 보다 간단할 수 있습니다. 
  
### <a name="step-3-create-a-migration-endpoint"></a>3단계: 마이그레이션 끝점 만들기
<a name="BK_Endpoint"> </a>

전자 메일을 성공적으로 마이그레이션 Office 365에 연결 하 고 원본 전자 메일 시스템과 통신할 해야 합니다. 이 위해 Office 365 마이그레이션 끝점을 사용 합니다. 첫번째 [Exchange Online에 연결](https://go.microsoft.com/fwlink/p/?LinkId=534121)하는 미리 구성 된 마이그레이션에 대 한 PowerShell을 사용 하 여 외부에서 Outlook 사용 마이그레이션 끝점 만들기 
  
마이그레이션 명령 목록이 전체 [이동 및 마이그레이션 cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=534750)을 참고 하십시오.
  
Exchange Online PowerShell에서 "StagedEndpoint"라는 Outlook Anywhere 마이그레이션 끝점을 만들려면 다음 명령을 실행합니다.
  
```
$Credentials = Get-Credential
```

```
New-MigrationEndpoint -ExchangeOutlookAnywhere -Name StagedEndpoint -Autodiscover -EmailAddress administrator@contoso.com -Credentials $Credentials
```

**New-migrationendpoint** cmdlet에 대 한 자세한 내용은[New-migrationendpoint](https://go.microsoft.com/fwlink/p/?LinkId=536437)를 참조 하십시오.
  
> [!NOTE]
> **New-migrationendpoint** cmdlet은 **-TargetDatabase** 옵션을 사용 하 여 사용 하 여 서비스에 대 한 데이터베이스를 지정 하는데 사용할 수 있습니다. 그렇지 않은 경우 데이터베이스는 임의로 할당에서 Active Directory Federation Services (AD FS) 2.0 사이트는 관리 사서함이 있는 합니다.
  
#### <a name="verify-it-worked"></a>작동하는지 확인

Exchange Online PowerShell에서 다음 명령을 실행하여 "StagedEndpoint" 마이그레이션 끝점에 대한 정보를 표시합니다.
  
```
Get-MigrationEndpoint StagedEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*
```

### <a name="step-4-create-and-start-a-stage-migration-batch"></a>4 단계:을 만들고 단계 마이그레이션 일괄 처리를 시작 합니다.
<a name="BK_Endpoint"> </a>

온라인으로 사용할 수 **New-migrationbatch** cmdlet은 Exchange PowerShell 단독형 마이그레이션 위한 마이그레이션 일괄 처리를 만들 수 있습니다. 마이그레이션 일괄 처리를 만들고 _자동 시작_ 매개 변수를 포함 하 여 자동으로 시작할 수 있습니다. 또는 마이그레이션 일괄 처리를 만들고 수동으로 시작 나중에 **Start-migrationbatch** cmdlet을 사용 하 여 수 있습니다. "StagedBatch1" 이라는 마이그레이션 일괄 처리를 만들고 이전 단계에서 만든 마이그레이션 끝점을 사용 하 여 하는이 예제입니다.
  
```
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint -AutoStart
```

이 예제에서는 또한 "StagedBatch1" 이라는 마이그레이션 일괄 처리를 만들고 이전 단계에서 만든 마이그레이션 끝점을 사용 하 여 합니다. _자동 시작_ 매개 변수는 포함 되어있지, 마이그레이션 일괄 처리 하기 때문에 마이그레이션 대시보드 또는 **Start-migrationbatch** cmdlet을 사용 하 여 수동으로 시작 합니다. 듯이 하나만 단독형 마이그레이션 일괄 처리를 한번에 존재할 수 있습니다.
  
```
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint
```

#### <a name="verify-it-worked"></a>작동하는지 확인

Exchange Online PowerShell에서 다음 명령을 실행하여 "StagedBatch1"에 대한 정보를 표시합니다.
  
```
Get-MigrationBatch -Identity StagedBatch1 | Format-List
```

다음 명령을 실행하여 일괄 처리가 시작되었는지 확인할 수도 있습니다.
  
```
Get-MigrationBatch -Identity StagedBatch1 | Format-List Status
```

**Get-migrationbatch** cmdlet에 대 한 자세한 내용은[Get-migrationbatch](https://go.microsoft.com/fwlink/p/?LinkId=536441)을 참조 하십시오.
  
### <a name="step-5-convert-on-premises-mailboxes-to-mail-enabled-users"></a>5단계: 온-프레미스 사서함을 메일 사용 가능 사용자로 변환
<a name="BK_Endpoint"> </a>

일괄 처리의 사서함을 성공적으로 마이그레이션 후 사용자가 자신의 메일을 가져올 수 있도록 수 있는 방법이 필요 합니다. 사용자 사서함 마이그레이션 되었고 이제 모두 사서함을 보유 한 온-프레미스 및 Office 365의 하나입니다. Office 365에서 사서함을 가진 사용자가 온-프레미스 사서함에 새 메일을 받는 중지 됩니다. 
  
마이그레이션을 수행 되지 않으며 때문에 준비가 되지 아직 전자 메일에 대 한 모든 사용자를 Office 365에 직접 보내도록 지정 합니다. 따라서 무엇을 할까요 모두 있는 해당 사용자에 대 한? 수행할 수 있는 작업은 온-프레미스 사서함을 메일 사용이 가능한 사용자에 게 이미 마이그레이션 했을 때 변경 합니다. 사서함에서 메일 사용이 가능한 사용자를 변경 하면가 온-프레미스 사서함을 이동 하는 대신 전자 메일에 대 한 Office 365로 사용자를 리디렉션할 수 있습니다. 
  
온-프레미스 사서함을 메일 사용이 가능한 사용자로 변환 하는 다른 중요 한 이유 메일 사용이 가능한 사용자에 게 프록시 주소를 복사 하 여 Office 365 사서함에서 프록시 주소를 유지할 수는 있습니다. 이렇게 하면 Active Directory를 사용 하 여 온-프레미스 조직에서 클라우드 기반 사용자를 관리할 수 있습니다. 또한 모든 사서함을 Office 365로 마이그레이션된 후 온-프레미스 Exchange Server 조직 해제 하려는 경우 메일 사용이 가능한 사용자에 게 복사 했을 때 프록시 주소는 온-프레미스 Active Directory에 유지 됩니다.
  
자세한 내용을 보고 사서함을 메일 사용이 가능한 사용자로 변환하기 위해 실행할 수 있는 스크립트를 다운로드하려면 다음을 참조하세요.
  
- [Exchange 2007 사서함을 메일 사용이 가능한 사용자로 변환](https://go.microsoft.com/fwlink/p/?LinkId=233648)
    
- [Exchange 2003 사서함을 메일 사용이 가능한 사용자로 변환](https://go.microsoft.com/fwlink/p/?LinkId=233647)
    
### <a name="step-6-delete-a-staged-migration-batch"></a>6단계: 미리 구성된 마이그레이션 일괄 처리 삭제
<a name="BK_Endpoint"> </a>

 모든 사서함 마이그레이션 일괄 처리에 성공적으로 마이그레이션한, 메일 사용이 가능한 사용자에 게 일괄 처리의 온-프레미스 사서함을 변환한 후 미리 구성 된 마이그레이션 일괄 처리를 삭제할 준비가 된 것입니다. 마이그레이션 일괄 처리에서 Office 365 사서함으로 메일을 전달 되었는지 확인 해야 합니다. 미리 구성 된 마이그레이션 일괄 처리를 삭제 하는 경우 마이그레이션 서비스는 마이그레이션 일괄 처리와 관련 된 모든 레코드를 정리 하 고 마이그레이션 일괄 처리를 삭제 합니다.
  
Exchange Online PowerShell에서 "StagedBatch1" 마이그레이션 일괄 처리를 삭제 하려면 다음 명령을 실행 합니다.
  
```
Remove-MigrationBatch -Identity StagedBatch1
```

**Remove-migrationbatch** cmdlet에 대 한 자세한 내용은[Remove-migrationbatch](https://go.microsoft.com/fwlink/p/?LinkId=536481)을 참조 하십시오.
  
#### <a name="verify-it-worked"></a>작동하는지 확인

Exchange Online PowerShell에서 다음 명령을 실행하여 "IMAPBatch1"에 대한 정보를 표시합니다.
  
```
Get-MigrationBatch StagedBatch1
```

이 명령은 **제거**상태와 마이그레이션 일괄 반환 됩니다 또는 해당 마이그레이션 일괄 처리를 찾을 수 없는 되었다는, 일괄 처리가 삭제 되었는지 확인 하면 오류가 반환 됩니다.
  
**Get-migrationbatch** cmdlet에 대 한 자세한 내용은[Get-migrationbatch](https://go.microsoft.com/fwlink/p/?LinkId=536441)을 참조 하십시오.
  
### <a name="step7-assign-licenses-to-office-365-users"></a>7단계: Office 365 사용자에게 라이선스 할당
<a name="BK_Endpoint"> </a>

라이선스를 할당 하 여 마이그레이션된 계정에 대 한 사용자 계정을 Office 365를 활성화 합니다. 라이선스를 할당 하지 않은 경우 (30 일) 유예 기간이 끝날 때 사서함 비활성화 됩니다. Office 365 관리 센터에서 라이선스를 할당 하려면 [할당 또는 비즈니스를 위한 Office 365에 대 한 라이선스를 할당 취소 하려면](https://go.microsoft.com/fwlink/?LinkId=536681)을 참조 하십시오.
  
### <a name="step-8-complete-post-migration-tasks"></a>8단계: 마이그레이션 후 작업 완료
<a name="BK_Postmigration"> </a>

- **사용자가 자신의 사서함에 쉽게 액세스할 수 있도록 하는 자동 검색 DNS 레코드를 만듭니다.** 모든 온-프레미스 사서함을 Office 365로 마이그레이션된 후에 사용자가 쉽게 Outlook 및 모바일 클라이언트와 함께 새로운 Office 365 사서함에 연결할 수 있도록 하 여 Office 365 조직에 대 한 자동 검색 DNS 레코드를 구성할 수 있습니다. Office 365 조직에 대해 사용 중인 동일한 네임 스페이스를 사용 하 여이 새 자동 검색 DNS 레코드에 있습니다. 클라우드 기반 네임 스페이스 cloud.contoso.com 있으면 만들어야 하는 자동 검색 DNS 레코드는, autodiscover.cloud.contoso.com 합니다.
    
    Office 365 CNAME 레코드를 사용 하 여 Outlook과 모바일 클라이언트에 대 한 자동 검색 서비스를 구현 합니다. 자동 검색 CNAME 레코드는 다음 정보를 포함 해야 합니다.
    
  - **별칭:** 자동 검색
    
  - **대상:** autodiscover.outlook.com
    
    자세한 내용은 [DNS 레코드를 관리 하는 경우 Office 365 용 DNS 레코드 만들기](https://go.microsoft.com/fwlink/p/?LinkId=535028)를 참조 하십시오.
    
- **온-프레미스 Exchange 서버를 해제 합니다.** 모든 전자 메일이 Office 365 사서함으로 직접 라우팅되는 하 고 더이상 온-프레미스 조직으로 전자 메일 또는 계획이 없는 SSO 솔루션을 구현에 유지 하기 위해 필요를 확인 한 후에 서버에서 Exchange를 제거 하거나 제거할 수 없습니다. 온-프레미스 Exchange 조직입니다.
    
    자세한 내용은 다음 항목을 참조하십시오.
    
  - [Exchange 2010 수정 또는 제거](https://go.microsoft.com/fwlink/?LinkId=217936)
    
  - [Exchange 2007 조직을 제거 하는 방법](https://go.microsoft.com/fwlink/?LinkID=100485)
    
  - [Exchange Server 2003을 제거 하는 방법](https://go.microsoft.com/fwlink/?LinkID=56561)
    

