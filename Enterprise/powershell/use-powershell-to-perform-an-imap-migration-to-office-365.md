---
title: "PowerShell을 사용하여 Office 365로 IMAP 마이그레이션 수행"
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
ms.assetid: c28de4a5-1e8e-4491-9421-af066cde7cdd
description: "요약: Office 365로 IMAP 마이그레이션을 수행 하려면 Windows PowerShell을 사용 하는 방법에 알아봅니다."
ms.openlocfilehash: 6187207d57723c9c69fa6fdc7885c91de6d5080f
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2017
---
# <a name="use-powershell-to-perform-an-imap-migration-to-office-365"></a>PowerShell을 사용하여 Office 365로 IMAP 마이그레이션 수행

 **요약:** Office 365로 IMAP 마이그레이션을 수행 하려면 Windows PowerShell을 사용 하는 방법에 알아봅니다.
  
Office 365를 배포 하는 프로세스의 일부로 Internet Mail Access Protocol (IMAP) 전자 메일 서비스에서 Office 365 사용자 사서함의 내용을 마이그레이션하려면 선택할 수 있습니다. 이 문서에서는 Exchange Online PowerShell을 사용 하 여 전자 메일 IMAP 마이그레이션에 대 한 작업을 통해 안내 합니다. 
  
> [!NOTE]
> IMAP 마이그레이션을 수행 하기 위해 Exchange 관리 센터를 사용할 수도 있습니다. [Office 365로 IMAP 사서함 마이그레이션](https://go.microsoft.com/fwlink/p/?LinkId=536685)참조 하십시오. 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>시작하기 전에 알아야 할 내용

예상이 작업을 완료 시간: 2 ~ 5 분 마이그레이션 일괄 처리를 만듭니다. 마이그레이션 일괄 처리 시작 되 면 마이그레이션 기간에 따라 달라 집니다 일괄 처리의 사서함 수, 사용 가능한 네트워크 용량 및 각 사서함의 크기입니다. Office 365로 사서함 마이그레이션에 걸리는 시간에 영향을 주는 다른 요인에 대 한 정보를 [마이그레이션 성능](https://go.microsoft.com/fwlink/p/?LinkId=275079)을 참조 하십시오.
  
이 절차를 수행 하기 전에 사용 권한을 할당 해야 합니다. 필요한 사용 권한을 [받는 사람에 게 사용 권한](https://go.microsoft.com/fwlink/p/?LinkId=534105) 항목의 테이블의 "마이그레이션" 항목을 참조 하십시오.
  
Exchange Online PowerShell cmdlet을 사용 하려면 로그인 하 고 로컬 Windows PowerShell 세션으로 cmdlet을 가져올 해야 합니다. 지침에 대 한 [원격 PowerShell을 사용 하는 Exchange Online에 연결](https://go.microsoft.com/fwlink/p/?LinkId=534121) 을 참조 하십시오.
  
마이그레이션 명령 목록이 전체 [이동 및 마이그레이션 cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=534750)을 참고 하십시오.
  
IMAP 마이그레이션에 적용되는 제한 사항은 다음과 같습니다.
  
- 사용자의 받은 편지함 또는 다른 메일 폴더에만 항목을 마이그레이션할 수 있습니다. 연락처, 일정 항목 또는 작업을 마이그레이션할 수 없습니다.
    
- 최대 500, 000 개의 항목이 사용자의 사서함에서 마이그레이션할 수 있습니다.
    
- 마이그레이션할 수 있는 최대 메시지 크기는 35MB입니다.
    
## <a name="migration-steps"></a>마이그레이션 단계

### <a name="step-1-prepare-for-an-imap-migration"></a>1단계: IMAP 마이그레이션 준비
<a name="BK_Step1"> </a>

- **도메인 수에 대 한 IMAP 조직이 있는 경우 Office 365 조직의 허용된 도메인으로 추가 합니다.** Office 365 사서함에 대 한 이미 소유 하는 동일한 도메인을 사용 하려는 경우에 먼저 Office 365에 허용된 도메인으로 추가 해야 합니다. 해당 작업을 추가한 후에 Office 365에서 사용자를 만들 수 있습니다. 자세한 내용은[Office 365에서 도메인을 확인 합니다.](https://go.microsoft.com/fwlink/p/?LinkId=534110)를 참조 하십시오.
    
- **Office 365 사서함 수 있도록 Office 365에 각 사용자를 추가 합니다.** 자세한 내용은[비즈니스를 위한 Office 365에 사용자 추가](https://go.microsoft.com/fwlink/p/?LinkId=535065)참조 하십시오.
    
- **접수 IMAP 서버의 FQDN**입니다. IMAP 마이그레이션 끝점을 만들 때에서 사서함 데이터 마이그레이션을 정규화 된 도메인 이름 (FQDN) (전체 컴퓨터 이름의 라고도 함) IMAP 서버의 제공 해야 합니다. 인터넷을 통해 IMAP 서버와 통신 하는 FQDN을 사용할 수 있는지 확인 하려면 IMAP 클라이언트나 PING 명령을 사용 합니다.
    
- **IMAP 연결을 허용 하도록 방화벽 구성**합니다. 마이그레이션하는 동안 Microsoft 데이터 센터에서 시작 되는 네트워크 트래픽을 IMAP 서버를 호스트 하는 조직의 입력할 수 있도록 IMAP 서버를 호스팅하는 조직의 방화벽에서 포트를 열기 해야할 수 있습니다. Microsoft 데이터 센터에서 사용 하는 IP 주소 목록이 [Exchange Online Url 및 IP 주소 범위](https://go.microsoft.com/fwlink/p/?LinkId=535066)를 참조 하십시오.
    
- **IMAP 조직 내의 사서함에에서 액세스 하려면 계정 사용 권한 관리자를 할당**합니다. CSV 파일의 관리자 자격 증명을 사용 하는 경우 사용 하는 계정에 온-프레미스 사서함에 액세스 하려면 필요한 권한이 있어야 합니다. 사용자 사서함에 액세스 하는 데 필요한 사용 권한은 특정 IMAP 서버에 의해 결정 됩니다. 
    
- **Exchange Online PowerShell cmdlet을 사용 하 여**, 해야에 로그인 하 고 cmdlet은 로컬 Windows PowerShell 세션으로 가져옵니다. 지침에 대 한 [원격 PowerShell을 사용 하는 Exchange Online에 연결](https://go.microsoft.com/fwlink/p/?LinkId=534121) 을 참조 하십시오.
    
    마이그레이션 명령 목록이 전체 [이동 및 마이그레이션 cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=534750)을 참고 하십시오.
    
- **IMAP 서버에 연결할 수 있는지 확인**합니다. 다음 명령을 실행 Exchange 온라인 PowerShell IMAP 서버에 대 한 연결 설정을 테스트 합니다.
    
  ```
  Test-MigrationServerAvailability -IMAP -RemoteServer <FQDN of IMAP server> -Port <143 or 993> -Security <None, Ssl, or Tls>
  ```

    **Port** 매개 변수 값에 대 한 암호화에 대 한 143을 사용 하 여 일반적인은 또는 전송 계층 보안 (TLS) 연결 및 SSL 연결에 대 한 993을 사용 하 여 합니다.
    
### <a name="step-2-create-a-csv-file-for-an-imap-migration-batch"></a>2단계: IMAP 마이그레이션 일괄 처리를 위한 CSV 파일 만들기
<a name="BK_Step2"> </a>

IMAP 마이그레이션 일괄 처리에서 해당 사서함을 마이그레이션할 사용자 그룹을 식별합니다. CSV 파일의 각 행에는 IMAP 메시징 시스템의 사서함에 연결하는 데 필요한 정보가 포함되어 있습니다.
  
각 사용자의 필수 특성은 다음과 같습니다. 
  
- **EmailAddress** 는 사용자의 Office 365 사서함에 대 한 사용자 ID를 지정합니다.
    
- **UserName** 은 IMAP 서버 사서함에 액세스를 사용 하 여 계정에 대 한 로그온 이름을 지정 합니다.
    
- **암호** **사용자 이름** 열에서 계정의 암호를 지정합니다.
    
다음은 CSV 파일 형식의 예입니다. 이 예에서는 다음 세 개의 사서함을 마이그레이션합니다.
  
```
EmailAddress,UserName,Password
terrya@contoso.edu,terry.adams,1091990
annb@contoso.edu,ann.beebe,2111991
paulc@contoso.edu,paul.cannon,3281986
```

사용자 이름 외에도 **사용자 이름** 특성에 대 한 IMAP 서버에서 사서함에 액세스 하는데 필요한 권한을 할당 된 계정의 자격 증명을 사용할 수 있습니다, IMAP 중 일부에 사용 되는 특정 형식 중 일부는 다음과 같습니다. 서버:
  
 **Microsoft Exchange:**
  
Microsoft Exchange에 대 한 IMAP 구현에서 전자 메일을 마이그레이션하는 경우 CSV 파일의 **사용자 이름** 특성에 대 한 **도메인/Admin_UserName/User_UserName** 형식을 사용 합니다. Terry Adams, Ann Beebe 및 Paul Cannon에 대 한 Exchange에서 전자 메일을 마이그레이션하는 경우를 가정해 보겠습니다. 메일 관리자 계정이 있는 사용자 이름은 **mailadmin** 이 고 암호는 **P@ssw0rd**해야 합니다. 다음과 같이 나타납니다 CSV 파일은 다음과 같습니다.
  
```
EmailAddress,UserName,Password
terrya@contoso.edu,contoso-students/mailadmin/terry.adams,P@ssw0rd
annb@contoso.edu,contoso-students/mailadmin/ann.beebe,P@ssw0rd
paulc@contoso.edu,contoso-students/mailadmin/paul.cannon,P@ssw0rd
```

 **Dovecot:**
  
Dovecot IMAP 서버와 같은 단순 인증 및 보안 레이어 (SASL)를 지 원하는 IMAP 서버 사용 * *User_UserName*Admin_UserName*형식에 대 한 *, 여기에서 별표 (*)는 구성 가능한 구분 기호입니다. 관리자 자격 증명 **mailadmin** 및 **P@ssw0rd**를 사용 하 여 Dovecot IMAP 서버에서 동일한 해당 사용자의 전자 메일을 마이그레이션하는 경우를 가정해 봅니다. 다음과 같이 나타납니다 CSV 파일은 다음과 같습니다.
  
```
EmailAddress,UserName,Password
terrya@contoso.edu,terry.adams*mailadmin,P@ssw0rd
annb@contoso.edu,ann.beebe*mailadmin,P@ssw0rd
paulc@contoso.edu,paul.cannon*mailadmin,P@ssw0rd
```

 **Mirapoint:**
  
전자 메일 Mirapoint 메시지 서버에서를 마이그레이션하는 경우 관리자 자격 증명에 대 한 형식 **#user@domain#Admin_UserName#** 를 사용 합니다. 관리자 자격 증명 **mailadmin** 및 **P@ssw0rd**를 사용 하 여 Mirapoint에서 전자 메일을 마이그레이션할 CSV 파일은 다음과 같습니다.
  
```
EmailAddress,UserName,Password
terrya@contoso.edu,#terry.adams@contoso-students.edu#mailadmin#,P@ssw0rd
annb@contoso.edu,#ann.beebe@contoso-students.edu#mailadmin#,P@ssw0rd
paulc@contoso.edu,#paul.cannon@contoso-students.edu#mailadmin#,P@ssw0rd
```

 **Courier IMAP:**
  
Courier IMAP와 같은 일부 원본 전자 메일 시스템 사서함 관리 자격 증명을 사용 하 여 Office 365로 사서함 마이그레이션 지원 하지 않습니다. 대신, 가상 공유 폴더를 사용 하 여 원본 전자 메일 시스템을 설정할 수 있습니다. 가상 공유 폴더를 사용 하 여 원본 전자 메일 시스템에서 사용자 사서함에 액세스 하는 사서함 관리 자격 증명을 사용할 수 있습니다. Courier IMAP에 대 한 가상 공유 폴더를 구성 하는 방법에 대 한 자세한 내용은 [공유 폴더](https://go.microsoft.com/fwlink/p/?LinkId=398870)를 참조 하십시오.
  
사서함을 마이그레이션하려면 원본 전자 메일 시스템에서 가상 공유 폴더를 설정한 후, 마이그레이션 파일의 선택적 특성 **UserRoot** 를 포함 해야 합니다. 이 특성 원본 전자 메일 시스템에 가상 공유 폴더 구조에서 각 사용자의 사서함의 위치를 지정합니다. 예, Terry의 사서함에 경로 /users/terry.adams 합니다.
  
**UserRoot** 특성이 포함 된 CSV 파일의 예는 다음과 같습니다.
  
```
EmailAddress,UserName,Password,UserRoot
terrya@contoso.edu,mailadmin,P@ssw0rd,/users/terry.adams
annb@contoso.edu,mailadmin,P@ssw0rd,/users/ann.beebe
paulc@contoso.edu,mailadmin,P@ssw0rd,/users/paul.cannon
```

### <a name="step-3-create-an-imap-migration-endpoint"></a>3단계: IMAP 마이그레이션 끝점 만들기
<a name="BK_Step3"> </a>

전자 메일을 성공적으로 마이그레이션 Office 365에 연결 하 고 원본 전자 메일 시스템과 통신할 해야 합니다. 이 위해 Office 365 마이그레이션 끝점을 사용 합니다. 또한 마이그레이션 끝점 동시에 마이그레이션할 사서함 수와 24 시간 마다 발생 하는 증분 동기화 하는 동안 동시에 동기화 하는 사서함의 수를 정의 합니다. [Exchange Online에 연결](https://go.microsoft.com/fwlink/p/?LinkId=534121)하는 첫번째 IMAP 마이그레이션에 대 한 마이그레이션 끝점을 생성 합니다. 
  
마이그레이션 명령 목록이 전체 [이동 및 마이그레이션 cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=534750)을 참고 하십시오.
  
Exchange Online PowerShell에서 "IMAPEndpoint"라는 IMAP 마이그레이션 끝점을 만들려면 다음 명령을 실행합니다.
  
```
New-MigrationEndpoint -IMAP -Name IMAPEndpoint -RemoteServer imap.contoso.com -Port 993 -Security Ssl

```

또한 동시 마이그레이션, 동시 증분 마이그레이션 및 사용할 포트를 지정 하려면 매개 변수를 추가할 수 있습니다. 다음 Exchange Online PowerShell 명령을 50 동시 마이그레이션을 지원 "IMAPEndpoint" 라는 IMAP 마이그레이션 끝점을 만듭니다 및 최대 25 동시 증분 동기화 합니다. 또한 TLS 암호화에 대 한 포트 143을 사용 하 여 끝점을 구성 합니다.
  
```
New-MigrationEndpoint -IMAP -Name IMAPEndpoint -RemoteServer imap.contoso.com -Port 143 -Security Tls -MaxConcurrentMigrations
50 -MaxConcurrentIncrementalSyncs 25
```

**New-migrationendpoint** cmdlet에 대 한 자세한 내용은[New-migrationendpoint](https://go.microsoft.com/fwlink/p/?LinkId=536437)를 참조 하십시오.
  
#### <a name="verify-it-worked"></a>작동하는지 확인

Exchange Online PowerShell에서 다음 명령을 실행하여 "IMAPEndpoint"에 대한 정보를 표시합니다.
  
```
Get-MigrationEndpoint IMAPEndpoint | Format-List EndpointType,RemoteServer,Port,Security,Max*
```

### <a name="step-4-create-and-start-an-imap-migration-batch"></a>4단계: IMAP 마이그레이션 일괄 처리 만들기 및 시작
<a name="BK_Step4"> </a>

IMAP 마이그레이션에 대 한 마이그레이션 일괄 처리를 만들려는 [New-migrationbatch](https://go.microsoft.com/fwlink/p/?LinkId=536439) cmdlet을 사용할 수 있습니다. 마이그레이션 일괄 처리를 만들고 _자동 시작_ 매개 변수를 포함 하 여 자동으로 시작할 수 있습니다. 또는 마이그레이션 일괄 처리를 만들고[Start-migrationbatch](https://go.microsoft.com/fwlink/p/?LinkId=536440) cmdlet을 사용 하 여 나중에 시작할 수 있습니다.
  
다음 Exchange Online PowerShell 명령은 "IMAPEndpoint"라는 IMAP 끝점을 사용하여 "IMAPBatch1"이라는 마이그레이션 일괄 처리를 자동으로 시작합니다.
  
```
New-MigrationBatch -Name IMAPBatch1 -SourceEndpoint IMAPEndpoint -CSVData ([System.IO.File]::ReadAllBytes("C:\\Users\\Administrator\\Desktop\\IMAPmigration_1.csv")) -AutoStart
```

#### <a name="verify-it-worked"></a>작동하는지 확인

"IMAPBatch1"에 대 한 정보를 표시 하도록 [Get-migrationbatch](https://go.microsoft.com/fwlink/p/?LinkId=536441) cmdlet을 실행 합니다.
  
```
Get-MigrationBatch -Identity IMAPBatch1 | Format-List
```

다음 명령을 실행하여 일괄 처리가 시작되었는지 확인할 수도 있습니다.
  
```
Get-MigrationBatch -Identity IMAPBatch1 | Format-List Status
```

### <a name="step-5-route-your-email-to-office-365"></a>5단계: Office 365로 전자 메일 라우팅
<a name="BK_Step5"> </a>

전자 메일 시스템 전자 메일을 제공 하기 위해 위치 결정 하는 MX 레코드를 호출 하는 DNS 레코드를 사용 합니다. 전자 메일 마이그레이션 프로세스 중 MX 레코드 원본 전자 메일 시스템을 가리키는 되었습니다. 이제 Office 365로 전자 메일 마이그레이션 완료 되 면 Office 365에서 MX 레코드를 가리키도록 시간입니다. 이렇게 하면 전자 메일이 Office 365 사서함으로 배달 되었는지 확인 합니다. MX 레코드를 이동 하 여 해제할 수 있습니다 또한 오래 된 전자 메일 시스템 준비 되 면 합니다. 
  
대부분의 DNS 공급자에 대 한 구체적인 지침은 [MX 레코드를 변경할](https://go.microsoft.com/fwlink/p/?LinkId=279163)수 있습니다. DNS 공급자 포함 되어있지는 또는 표시 되는 일반 지침의 알려면 하려는 경우 [MX 레코드는 일반적인 지침](https://go.microsoft.com/fwlink/?LinkId=397449) 도 제공 됩니다.
  
고객 및 파트너의 전자 메일 시스템에서 변경된 MX 레코드를 인식하는 데는 최대 72시간이 걸릴 수 있습니다. 다음 작업을 계속 진행하기 전에 적어도 72시간 동안 기다립니다. 6단계: IMAP 마이그레이션 일괄 처리 삭제 
  
### <a name="step-6-delete-imap-migration-batch"></a>6단계: IMAP 마이그레이션 일괄 처리 삭제
<a name="BK_Step6"> </a>

MX 레코드를 변경 하 고 모든 전자 메일이 Office 365 사서함으로 라우팅되는 확인 한 후 Office 365의 메일 될 사용자를 게 알립니다. 그런 다음, IMAP 마이그레이션 일괄 처리를 삭제할 수 있습니다. 마이그레이션 일괄 처리를 삭제 하기 전에 다음을 확인 합니다.
  
- 모든 사용자에 게 Office 365 사서함을 사용 중입니다. 일괄 처리 삭제 된 후 해당 하는 Office 365 사서함 온-프레미스 Exchange 서버에 있는 사서함으로 보낸 메일 복사 되지 않습니다.
    
- Office 365 사서함 메일에 직접 전송 되 고 시작 된 후 최소한 한번 동기화 했습니다. 이 작업을 수행 하려면 마이그레이션 일괄 처리에 대 한 마지막 동기화 시간 상자에 값 Office 365 사서함으로 직접 라우팅되는 메일을 시작 하는 경우 보다 최신 인지 확인 합니다.
    
Exchange Online PowerShell에서 "IMAPBatch1" 마이그레이션 일괄 처리를 삭제하려면 다음 명령을 실행합니다.
  
```
Remove-MigrationBatch -Identity IMAPBatch1
```

**Remove-migrationbatch** cmdlet에 대 한 자세한 내용은[Remove-migrationbatch](https://go.microsoft.com/fwlink/p/?LinkId=536481)을 참조 하십시오.
  
#### <a name="verify-it-worked"></a>작동하는지 확인

Exchange Online PowerShell에서 다음 명령을 실행하여 "IMAPBatch1"에 대한 정보를 표시합니다.
  
```
Get-MigrationBatch IMAPBatch1"
```

이 명령은 **제거**상태와 마이그레이션 일괄 반환 됩니다 또는 해당 마이그레이션 일괄 처리를 찾을 수 없는 되었다는, 일괄 처리가 삭제 되었는지 확인 하면 오류가 반환 됩니다.
  
**Get-migrationbatch** cmdlet에 대 한 자세한 내용은[Get-migrationbatch](https://go.microsoft.com/fwlink/p/?LinkId=536441)을 참조 하십시오.
  
## <a name="see-also"></a>See also

#### 

[IMAP 마이그레이션 문제 해결사](https://go.microsoft.com/fwlink/p/?LinkId=536482)

