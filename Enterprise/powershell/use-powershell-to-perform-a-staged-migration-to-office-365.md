---
title: PowerShell을 사용하여 Office 365로 미리 구성된 마이그레이션 수행
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: a20f9dbd-6102-4ffa-b72c-ff813e700930
description: 요약:Windows PowerShell을 사용하여 Office 365로 미리 구성된 마이그레이션을 수행하는 방법을 알아봅니다.
ms.openlocfilehash: 846704ff32a8f6e4012e93b67ec2a921d4c9ac51
ms.sourcegitcommit: d1022143bdefdd5583d8eff08046808657b49c94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/02/2020
ms.locfileid: "44004521"
---
# <a name="use-powershell-to-perform-a-staged-migration-to-office-365"></a>PowerShell을 사용하여 Office 365로 미리 구성된 마이그레이션 수행

미리 구성된 마이그레이션을 사용하여 시간에 따라 원본 전자 메일 시스템의 사용자 사서함 콘텐츠를 Office 365로 마이그레이션할 수 있습니다.
  
이 문서에서는 Exchange Online PowerShell을 사용하여 미리 구성된 전자 메일 마이그레이션과 관련된 작업을 안내합니다. [Office 365로의 미리 구성된 전자 메일 마이그레이션에 대해 알아야 할 사항](https://go.microsoft.com/fwlink/p/?LinkId=536487) 항목에서는 마이그레이션 프로세스를 대략적으로 소개합니다. 이 문서 내용을 충분히 이해할 수 있으면 다음을 사용하여 다른 전자 메일 시스템으로 사서함을 마이그레이션해 보세요.
  
> [!NOTE]
> Exchange 관리 센터를 사용하여 미리 구성된 마이그레이션을 수행할 수도 있습니다. [Office 365로 미리 구성된 전자 메일 마이그레이션 수행](https://go.microsoft.com/fwlink/p/?LinkId=536687)을 참조하세요. 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>시작하기 전에 알아야 할 내용

이 작업의 예상 완료 시간: 2-5분(마이그레이션 일괄 처리 만들기에 소요되는 시간). 마이그레이션 일괄 처리가 시작되면 마이그레이션 기간은 일괄 처리의 사서함 수, 각 사서함의 크기 및 사용 가능한 네트워크 용량에 따라 달라집니다. 사서함을 Office 365로 마이그레이션하는 데 소요되는 시간에 영향을 주는 기타 요인에 대한 자세한 내용은 [마이그레이션 성능](https://go.microsoft.com/fwlink/p/?LinkId=275079)을 참조하세요.
  
이 절차를 수행하려면 먼저 사용 권한을 할당받아야 합니다. 필요한 사용 권한을 확인하려면 [받는 사람 사용 권한](https://go.microsoft.com/fwlink/p/?LinkId=534105)의 "마이그레이션" 항목을 참조하세요.
  
Exchange Online PowerShell cmdlet을 사용하려면 로그인한 후 cmdlet을 로컬 Windows PowerShell 세션으로 가져와야 합니다. 해당 지침은 [원격 PowerShell을 사용하여 Exchange Online에 연결](https://go.microsoft.com/fwlink/p/?LinkId=534121)을 참조하세요.
  
전체 마이그레이션 명령 목록을 보려면 [이동 및 마이그레이션 cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=534750)을 참조하세요.
  
## <a name="migration-steps"></a>마이그레이션 단계

### <a name="step-1-prepare-for-a-staged-migration"></a>1단계: 미리 구성된 마이그레이션 준비

미리 구성된 마이그레이션을 사용하여 사서함을 Office 365로 마이그레이션하기 전에 Exchange 환경을 일부 변경해야 합니다.
  
 **온-프레미스에서 Exchange Server에서 Outlook Anywhere 구성** 전자 메일 마이그레이션 서비스는 Outlook Anywhere(RPC over HTTP라고도 함)를 사용하여 온-프레미스 Exchange Server에 연결합니다. Exchange Server 2007 및 Exchange 2003에 맞게 Outlook Anywhere를 설정하는 방법에 대한 자세한 내용은 다음 항목을 참조하세요.
  
- [Exchange 2007: "외부에서 Outlook 사용" 설정 방법](https://go.microsoft.com/fwlink/?LinkID=167210)
    
- [Exchange 2003: "외부에서 Outlook 사용" 구성 방법](https://go.microsoft.com/fwlink/?LinkID=167209)
    
> [!IMPORTANT]
> Outlook Anywhere 구성에서는 신뢰할 수 있는 CA(인증 기관)에서 발급한 인증서를 사용해야 합니다. Outlook Anywhere은 자체 서명된 인증서로 구성할 수 없습니다. 자세한 내용은 ["외부에서 Outlook 사용"에 대한 SSL 구성 방법](https://go.microsoft.com/fwlink/?LinkID=80875)을 참조하세요. 
  
 **선택 사항: Outlook Anywhere을 사용하여 Exchange 조직에 연결할 수 있는지 확인** 다음 방법 중 하나를 사용하여 연결 설정을 테스트해 봅니다.
  
- 회사 네트워크 외부에서 Outlook을 사용하여 온-프레미스 Exchange 사서함에 연결합니다.
    
- [Microsoft 원격 연결 분석기](https://https://testconnectivity.microsoft.com/) 를 사용 하 여 연결 설정을 테스트 합니다. Outlook Anywhere(RPC over HTTP) 또는 Outlook 자동 검색 테스트를 사용합니다.
    
- Exchange Online PowerShell에서 다음 명령을 실행합니다.
    
  ```powershell
  $Credentials = Get-Credential
  ```

  ```powershell
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

 **사용 권한 설정** 온-프레미스 Exchange 조직에 연결하는 데 사용하는 온-프레미스 계정(마이그레이션 관리자라고도 함)에는 Office 365로 마이그레이션할 온-프레미스 사서함에 액세스하는 데 필요한 권한이 있어야 합니다. 이 사용자 계정은 이 절차의 뒷부분에서 마이그레이션 끝점을 만들어 전자 메일 시스템에 연결할 때 사용됩니다([3단계: 마이그레이션 끝점 만들기](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Endpoint)).
  
사서함을 마이그레이션하려면 관리자는 다음 사용 권한 집합 중 하나가 있어야 합니다.
  
- 온-프레미스 조직의 Active Directory에 있는 **Domain Admins** 그룹의 구성원이어야 합니다.
    
    또는
    
- 각 온-프레미스 사서함에 대해 **FullAccess** 권한이 할당되고 온-프레미스 사용자 계정에 대해 **TargetAddress** 속성을 수정할 수 있는 **WriteProperty** 권한이 할당되어야 합니다.
    
     선택하거나 
    
- 사용자 사서함을 저장하는 온-프레미스 사서함 데이터베이스에 대해 **다음으로 받기** 권한이 할당되고 온-프레미스 사용자 계정에 대해 **TargetAddress** 속성을 수정할 수 있는 **WriteProperty** 권한이 할당되어야 합니다.
    
이러한 사용 권한을 설정하는 방법에 대한 지침은 [Office 365로 사서함을 마이그레이션할 수 있는 권한 할당](https://go.microsoft.com/fwlink/?LinkId=521656)을 참조하세요.
  
 **UM(통합 메시징)을 사용하지 않도록 설정** 마이그레이션하려는 온-프레미스 사서함에 대해 UM이 켜져 있는 경우 마이그레이션 전에 UM을 사용하지 않도록 설정합니다. 마이그레이션이 완료된 후 사서함에 대해 UM을 켭니다. 방법 단계에 대해서는[통합 메시징을 사용하지 않도록 설정](https://go.microsoft.com/fwlink/?LinkId=521891)을 참조하세요.
  
 **디렉터리 동기화를 사용하여 Office 365에서 새 사용자를 만듭니다.** 디렉터리 동기화를 사용하여 Office 365 조직의 모든 온-프레미스 사용자를 만들 수 있습니다.
  
만든 사용자에게는 라이선스를 부여해야 합니다. 사용자를 만들고 30일 내에 라이선스를 추가해야 합니다. 라이선스를 추가하는 단계에 대해서는 [8단계: 마이그레이션 후 작업 완료](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Postmigration)를 참조하세요.
  
 Microsoft Azure Active Directory 동기화 도구 또는 Microsoft AAD Sync(Azure Active Directory 동기화 서비스)를 사용하여 Office 365에서 온-프레미스 사용자를 만들고 동기화할 수 있습니다. 사서함이 Office 365로 마이그레이션되면 온-프레미스 조직에서 사용자 계정을 관리하고 Office 365 조직과 동기화되도록 합니다. 자세한 내용은 [디렉터리 통합](https://go.microsoft.com/fwlink/?LinkId=521788)을 참조하세요.
  
### <a name="step-2-create-a-csv-file-for-a-staged-migration-batch"></a>2단계: 미리 구성된 마이그레이션 일괄 처리에 대한 CSV 파일 만들기

Office 365로 온-프레미스 사서함을 마이그레이션할 사용자를 확인한 후 CSV(쉼표로 구분된 값) 파일을 사용하여 마이그레이션 일괄 처리를 만듭니다. Office 365에서 마이그레이션을 실행하는 데 사용하는 CSV 파일의 각 행에는 온-프레미스 사서함에 대한 정보가 포함되어 있습니다. 
  
> [!NOTE]
> 미리 구성된 마이그레이션을 사용하여 Office 365으로 마이그레이션할 수 있는 사서함의 수에는 제한이 없습니다. 마이그레이션 일괄 처리용 CSV 파일에는 최대 2,000개 행을 포함할 수 있습니다. 2,000개가 넘는 사서함을 마이그레이션하려면 CSV 파일을 추가로 만든 다음 각 파일을 사용하여 새 마이그레이션 일괄 처리를 만들어야 합니다. 
  
 **지원되는 특성**
  
미리 구성된 마이그레이션용 CSV 파일에는 다음과 같은 세 개의 특성이 지원됩니다. CSV 파일의 각 행은 하나의 사서함에 해당하며 이러한 각 특성에 대한 값을 포함해야 합니다.
  
|**특성**|**설명**|**필수 여부**|
|:-----|:-----|:-----|
|EmailAddress  <br/> |온-프레미스 사서함에 대한 기본 SMTP 전자 메일 주소(예: pilarp@contoso.com)를 지정합니다.  <br/> 온-프레미스 사서함에 대해서는 Office 365의 사용자 ID가 아닌 기본 SMTP 주소를 사용합니다. 예를 들어 온-프레미스 도메인의 이름이 contoso.com이고 Office 365 전자 메일 도메인의 이름이 service.contoso.com인 경우 CSV 파일의 전자 메일 주소에 contoso.com 도메인 이름을 사용해야 합니다.  <br/> |필수  <br/> |
|암호  <br/> |새 Office 365 사서함에 대해 설정할 암호입니다. Office 365 조직에 적용되는 암호 제한은 CSV 파일에 포함된 암호에도 적용됩니다.  <br/> |옵션  <br/> |
|ForceChangePassword  <br/> |사용자가 새 Office 365 사서함에 처음 로그인할 때 암호를 변경해야 하는지 여부를 지정합니다. 이 매개 변수 값으로는 **True** 또는 **False** 를 사용합니다. <br/> > [!NOTE]> 온-프레미스 조직에서 AD FS(Active Directory Federation Services)를 배포하여 SSO(Single Sign-On) 솔루션을 구현한 경우 **ForceChangePassword** 특성 값으로 **False** 를 사용해야 합니다.          |옵션  <br/> |
   
 **CSV 파일 형식**
  
다음은 CSV 파일 형식의 예입니다. 이 예에서는 온-프레미스 사서함 세 개를 Office 365으로 마이그레이션합니다.
  
CSV 파일의 첫 번째 행(머리글 행)에는 그 다음 행들에 지정된 특성 또는 필드의 이름이 나열됩니다. 각 특성 이름은 쉼표로 구분됩니다.
  
```powershell
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

전자 메일을 마이그레이션하기 위해 Office 365는 원본 전자 메일 시스템에 연결하고 통신해야 합니다. 이를 위해 Office 365에서는 마이그레이션 끝점을 사용합니다. PowerShell을 사용하여 "외부에서 Outlook 사용" 마이그레이션 끝점을 만들려면 미리 구성된 마이그레이션에 대해 먼저 [Exchange Online에 연결](https://go.microsoft.com/fwlink/p/?LinkId=534121)합니다. 
  
전체 마이그레이션 명령 목록을 보려면 [이동 및 마이그레이션 cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=534750)을 참조하세요.
  
Exchange Online PowerShell에서 "StagedEndpoint"라는 Outlook Anywhere 마이그레이션 끝점을 만들려면 다음 명령을 실행합니다.
  
```powershell
$Credentials = Get-Credential
```

```powershell
New-MigrationEndpoint -ExchangeOutlookAnywhere -Name StagedEndpoint -Autodiscover -EmailAddress administrator@contoso.com -Credentials $Credentials
```

**New-MigrationEndpoint** cmdlet에 대한 자세한 내용은[New-MigrationEndpoint](https://go.microsoft.com/fwlink/p/?LinkId=536437)를 참조하세요.
  
> [!NOTE]
> **New-MigrationEndpoint** cmdlet을 사용하여 **-TargetDatabase** 옵션을 통해 서비스에서 사용할 데이터베이스를 지정할 수 있습니다. 그렇지 않으면 데이터베이스는 관리 사서함이 있는 AD FS(Active Directory Federation Services) 2.0 사이트에서 임의로 할당됩니다.
  
#### <a name="verify-it-worked"></a>작동하는지 확인

Exchange Online PowerShell에서 다음 명령을 실행하여 "StagedEndpoint" 마이그레이션 끝점에 대한 정보를 표시합니다.
  
```powershell
Get-MigrationEndpoint StagedEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*
```

### <a name="step-4-create-and-start-a-stage-migration-batch"></a>4단계: 미리 구성된 마이그레이션 일괄 처리 만들기 및 시작
<a name="BK_Endpoint"> </a>

Exchange Online PowerShell에서 **New-MigrationBatch** cmdlet을 사용하여 단독형 마이그레이션을 위한 마이그레이션 일괄 처리를 만들 수 있습니다. _AutoStart_ 매개 변수를 포함하면 마이그레이션 일괄 처리를 만들고 자동으로 시작할 수 있습니다. 또는 마이그레이션 일괄 처리를 만들고 **Start-MigrationBatch** cmdlet을 사용하여 나중에 마이그레이션을 수동으로 시작할 수 있습니다. 이 예에서는 "StagedBatch1"이라는 마이그레이션 일괄 처리를 만든 다음 이전 예에서 만든 마이그레이션 끝점을 사용합니다.
  
```powershell
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint -AutoStart
```

또한 이 예에서는 "StagedBatch1"이라는 마이그레이션 일괄 처리를 만든 다음 이전 예에서 만든 마이그레이션 끝점을 사용합니다.  _AutoStart_ 매개 변수가 포함되지 않으므로 마이그레이션 일괄 처리가 마이그레이션 대시보드나 **Start-MigrationBatch** cmdlet을 사용하여 수동으로 시작되어야 합니다. 앞서 설명했듯이 단독형 마이그레이션 일괄 처리는 한 번에 하나만 실행됩니다.
  
```powershell
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint
```

#### <a name="verify-it-worked"></a>작동하는지 확인

Exchange Online PowerShell에서 다음 명령을 실행하여 "StagedBatch1"에 대한 정보를 표시합니다.
  
```powershell
Get-MigrationBatch -Identity StagedBatch1 | Format-List
```

다음 명령을 실행하여 일괄 처리가 시작되었는지 확인할 수도 있습니다.
  
```powershell
Get-MigrationBatch -Identity StagedBatch1 | Format-List Status
```

**Get-MigrationBatch** cmdlet에 대한 자세한 내용은[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441)를 참조하세요.
  
### <a name="step-5-convert-on-premises-mailboxes-to-mail-enabled-users"></a>5단계: 온-프레미스 사서함을 메일 사용 가능 사용자로 변환
<a name="BK_Endpoint"> </a>

사서함 일괄 처리를 마이그레이션한 후에는 다른 사용자가 해당 메일에 액세스할 수 있도록 해야 합니다. 사서함이 마이그레이션된 사용자는 온-프레미스 및 Office 365 둘 다에 사서함이 존재하게 됩니다. Office 365에 사서함이 있는 사용자는 더 이상 온-프레미스 사서함에 새 메일이 수신되지 않습니다. 
  
마이그레이션을 완료하지 않았으므로 아직 모든 사용자가 본인의 전자 메일을 받기 위해 Office 365으로 이동되도록 하면 안 됩니다. 그렇다면 두 위치에 사서함을 모두 보유하는 사용자의 경우는 어떻게 해야 할까요? 메일 사용 가능 사용자로 이미 마이그레이션한 온-프레미스 사서함을 변경할 수 있습니다. 사서함에서 메일 사용 가능 사용자로 변경할 경우 사용자가 본인의 전자 메일을 받기 위해 해당 온-프레미스 사서함이 아닌 Office 365로 이동되도록 할 수 있습니다. 
  
온-프레미스 사서함을 메일 사용 가능 사용자로 변환하는 다른 중요한 이유는 프록시 주소를 메일 사용 가능 사용자로 복사하여 Office 365 사서함의 프록시 주소를 보존하는 것입니다. 이렇게 하면 Active Directory를 사용하여 온-프레미스 조직의 클라우드(Cloud) 기반 사용자를 관리할 수 있습니다. 또한 모든 사서함이 Office 365으로 마이그레이션된 후 온-프레미스 Exchange Server 조직을 제거하면 메일 사용 가능한 사용자로 복사한 프록시 주소가 온-프레미스 Active Directory에 남아 있습니다.
    
### <a name="step-6-delete-a-staged-migration-batch"></a>6단계: 미리 구성된 마이그레이션 일괄 처리 삭제
<a name="BK_Endpoint"> </a>

 마이그레이션 일괄 처리에 포함된 모든 사서함이 마이그레이션되었고 일괄 처리에 있는 온-프레미스 사서함이 메일 사용 가능 사용자로 변환되면 미리 구성된 마이그레이션 일괄 처리를 삭제할 수 있습니다. 메일이 마이그레이션 일괄 처리의 Office 365 사서함으로 전달 중인지 확인하세요. 미리 구성된 마이그레이션 일괄 처리를 삭제하면 마이그레이션 서비스에서 마이그레이션 일괄 처리와 관련된 모든 레코드를 정리하고 마이그레이션 일괄 처리를 삭제합니다.
  
Exchange Online PowerShell에서 "StagedBatch1" 마이그레이션 일괄 처리를 삭제하려면 다음 명령을 실행합니다.
  
```powershell
Remove-MigrationBatch -Identity StagedBatch1
```

**Remove-MigrationBatch** cmdlet에 대한 자세한 내용은[Remove-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536481)를 참조하세요.
  
#### <a name="verify-it-worked"></a>작동하는지 확인

Exchange Online PowerShell에서 다음 명령을 실행하여 "IMAPBatch1"에 대한 정보를 표시합니다.
  
```powershell
Get-MigrationBatch StagedBatch1
```

이 명령을 실행하면 상태가 **제거 중** 인 마이그레이션 일괄 처리가 반환되거나, 마이그레이션 일괄 처리를 찾을 수 없다는 오류가 반환됩니다. 이 경우 해당 일괄 처리가 삭제되었음을 확인할 수 있습니다.
  
**Get-MigrationBatch** cmdlet에 대한 자세한 내용은[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441)를 참조하세요.
  
### <a name="step7-assign-licenses-to-office-365-users"></a>7단계: Office 365 사용자에게 라이선스 할당
<a name="BK_Endpoint"> </a>

라이선스를 할당하여 마이그레이션된 계정에 대한 Office 365 사용자 계정을 활성화합니다. 라이선스를 할당하지 않은 경우 30일의 유예 기간이 끝나면 사서함을 사용할 수 없습니다. Microsoft 365 관리 센터에서 라이선스를 할당하려면 [비즈니스용 Office 365 라이선스 할당 또는 할당 취소](https://go.microsoft.com/fwlink/?LinkId=536681)를 참조하세요.
  
### <a name="step-8-complete-post-migration-tasks"></a>8단계: 마이그레이션 후 작업 완료
<a name="BK_Postmigration"> </a>

- **사용자가 자신의 사서함으로 쉽게 이동할 수 있도록 자동 검색 DNS 레코드를 만듭니다.** 모든 온-프레미스 사서함이 Office 365로 마이그레이션된 후에는 사용자가 Outlook 및 모바일 클라이언트를 사용하여 새 Office 365 사서함에 쉽게 연결할 수 있도록 Office 365 조직에 대한 자동 검색 DNS 레코드를 구성할 수 있습니다. 이 새로운 자동 검색 DNS 레코드에서는 Office 365 조직에 사용 중인 동일한 네임스페이스를 사용해야 합니다. 예를 들어 클라우드(Cloud) 기반 네임스페이스가 cloud.contoso.com인 경우 만들어야 할 자동 검색 DNS 레코드는 autodiscover.cloud.contoso.com입니다.
    
    Office 365는 CNAME 레코드를 사용하여 Outlook 및 모바일 클라이언트에 대한 자동 검색 서비스를 구현합니다. Autodiscover CNAME 레코드에는 다음과 같은 정보가 포함되어야 합니다.
    
  - **별칭:** autodiscover
    
  - **대상:** autodiscover.outlook.com
    
    자세한 내용은 [DNS 레코드를 관리하는 경우 Office 365용 DNS 레코드 만들기](https://go.microsoft.com/fwlink/p/?LinkId=535028)를 참조하세요.
    
- **온-프레미스 Exchange 서버를 해제합니다.** 모든 전자 메일이 Office 365 사서함으로 직접 라우팅됨을 확인하고 온-프레미스 전자 메일 조직을 더 이상 유지 관리할 필요가 없거나 SSO 솔루션을 구현하지 않으려는 경우에는 서버에서 Exchange를 제거하고 온-프레미스 Exchange 조직을 제거할 수 있습니다.
    
    자세한 내용은 다음 항목을 참조하십시오.
    
  - [Exchange 2010 수정 또는 제거](https://go.microsoft.com/fwlink/?LinkId=217936)
    
  - [Exchange 2007 조직 제거 방법](https://go.microsoft.com/fwlink/?LinkID=100485)
    
  - [Exchange Server 2003 제거 방법](https://go.microsoft.com/fwlink/?LinkID=56561)
    

