---
title: PowerShell을 사용하여 Office 365로 단독형 마이그레이션 수행
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
ms.custom: ''
ms.assetid: b468cb4b-a35c-43d3-85bf-65446998af40
description: 요약:Windows PowerShell을 사용하여 Office 365로 단독형 마이그레이션을 수행하는 방법을 알아봅니다.
ms.openlocfilehash: b40c6ac53a173f700c6b931781d98d7965a2be7c
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998573"
---
# <a name="use-powershell-to-perform-a-cutover-migration-to-office-365"></a>PowerShell을 사용하여 Office 365로 단독형 마이그레이션 수행

You can migrate the contents of user mailboxes from a source email system to Office 365 all at once by using a cutover migration. This article walks you through the tasks for an email cutover migration by using Exchange Online PowerShell. 
  
By reviewing the topic, [What you need to know about a cutover email migration to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536688), you can get an overview of the migration process. When you're comfortable with the contents of that article, use this one to begin migrating mailboxes from one email system to another.
  
> [!NOTE]
> You can also use the Exchange admin center to perform a cutover migration. See [Perform a cutover migration of email to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536689). 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>시작하기 전에 알아야 할 내용

Estimated time to complete this task: 2-5 minutes to create a migration batch. After the migration batch is started, the duration of the migration will vary based on the number of mailboxes in the batch, the size of each mailbox, and your available network capacity. For information about other factors that affect how long it takes to migrate mailboxes to Office 365, see [Migration Performance](https://go.microsoft.com/fwlink/p/?LinkId=275079).
  
You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Migration" entry in a table in the [Recipients Permissions](https://go.microsoft.com/fwlink/p/?LinkId=534105) topic.
  
To use the Exchange Online PowerShell cmdlets, you need to sign in and import the cmdlets into your local Windows PowerShell session. See [Connect to Exchange Online using remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121) for instructions.
  
전체 마이그레이션 명령 목록을 보려면 [이동 및 마이그레이션 cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=534750)을 참조하세요.
  
## <a name="migration-steps"></a>마이그레이션 단계

### <a name="step-1-prepare-for-a-cutover-migration"></a>1단계: 단독형 마이그레이션 준비
<a name="BK_Step1"> </a>

- **Add your on-premises Exchange organization as an accepted domain of your Office 365 organization.** The migration service uses the SMTP address of your on-premises mailboxes to create the Microsoft Online Services user ID and email address for the new Office 365 mailboxes. Migration will fail if your Exchange domain isn't an accepted domain or the primary domain of your Office 365 organization. For more information, see[Verify your domain in Office 365](https://go.microsoft.com/fwlink/p/?LinkId=534110).
    
- **Configure Outlook Anywhere on your on-premises Exchange server.** The email migration service uses RPC over HTTP, or Outlook Anywhere, to connect to your on-premises Exchange server. For information about how to set up Outlook Anywhere for Exchange 2010, Exchange 2007, and Exchange 2003, see the following:
    
  - [Exchange 2010: "외부에서 Outlook 사용" 설정](https://go.microsoft.com/fwlink/?LinkID=187249)
    
  - [Exchange 2007: 외부에서 Outlook 사용 설정 방법](https://go.microsoft.com/fwlink/?LinkID=167210)
    
  - [Exchange 2003: RPC over HTTP에 대한 배포 시나리오](https://go.microsoft.com/fwlink/?LinkID=73657)
    
  - [Exchange 2003: "외부에서 Outlook 사용" 구성 방법](https://go.microsoft.com/fwlink/?LinkID=167209)
    
    > [!IMPORTANT]
    > Your Outlook Anywhere configuration must be configured with a certificate issued by a trusted certification authority (CA). It can't be configured with a self-signed certificate. For more information, see [How to Configure SSL for Outlook Anywhere](https://go.microsoft.com/fwlink/?LinkID=80875). 
  
- **Verify that you can connect to your Exchange organization using Outlook Anywhere.** Try one of these methods to test your connection settings:
    
  - 회사 네트워크 외부에서 Microsoft Outlook을 사용하여 온-프레미스 Exchange 사서함에 연결합니다.
    
  - Use the Microsoft [Exchange Remote Connectivity Analyzer](https://www.testexchangeconnectivity.com/) to test your connection settings. Use the Outlook Anywhere (RPC over HTTP) or Outlook Autodiscover tests.
    
  - Exchange Online PowerShell에서 다음 명령을 실행합니다.
    
  ```
  $Credentials = Get-Credential
  ```

  ```
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

- **온-프레미스 사용자 계정에 Exchange 조직의 사서함에 액세스하는 데 필요한 사용 권한 할당** 온-프레미스 Exchange 조직에 연결 하는 데 사용 하는 온-프레미스 사용자 계정 (마이그레이션 관리자 라고도 함)에는 Office 365로 마이그레이션할 온-프레미스 사서함에 액세스 하는 데 필요한 권한이 있어야 합니다. 이 사용자 계정은 온-프레미스 조직에 대한 마이그레이션 끝점을 만드는 데 사용됩니다.
    
    The following list shows the administrative privileges required to migrate mailboxes using a cutover migration. There are three possible options.
    
  - 마이그레이션 관리자는 온-프레미스 조직의 Active Directory에 있는 **Domain Admins** 그룹의 구성원이어야 합니다.
    
    또는
    
  - 마이그레이션 관리자에게 각 온-프레미스 사서함에 대한 **모든 권한** 권한이 할당되어야 합니다.
    
    또는
    
  - 마이그레이션 관리자에게 사용자 사서함을 저장하는 온-프레미스 사서함 데이터베이스에 대한 **다음으로 받기** 권한이 할당되어야 합니다.
    
- **Disable Unified Messaging.** If the on-premises mailboxes you're migrating are enabled for Unified Messaging (UM), you have to disable UM on the mailboxes before you migrate them. You can then enable UM on the mailboxes after the migration is complete.
    
- **Security Groups and Delegates** The email migration service cannot detect whether on-premises Active Directory groups are security groups or not, so it cannot provision any migrated groups as security groups in Office 365. If you want to have security groups in your Office 365 tenant, you must first provision an empty mail-enabled security group in your Office 365 tenant before starting the cutover migration. Additionally, this migration method only moves mailboxes, mail users, mail contacts, and mail-enabled groups. If any other Active Directory object, such as user that is not migrated to Office 365, is assigned as a manager or delegate to an object being migrated, they must be removed from the object before you migrate.
    
### <a name="step-2-create-a-migration-endpoint"></a>2단계: 마이그레이션 끝점 만들기
<a name="BK_Step2"> </a>

To migrate email successfully, Office 365 needs to connect and communicate with the source email system. To do this, Office 365 uses a migration endpoint. To create an Outlook Anywhere migration endpoint for cutover migration, first [connect to Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121). 
  
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
> The **New-MigrationEndpoint** cmdlet can be used to specify a database for the service to use by using the **-TargetDatabase** option. Otherwise a database is randomly assigned from the Active Directory Federation Services (AD FS) 2.0 site where the management mailbox is located.
  
#### <a name="verify-it-worked"></a>작동하는지 확인

Exchange Online PowerShell에서 다음 명령을 실행하여 "CutoverEndpoint" 마이그레이션 끝점에 대한 정보를 표시합니다.
  
```
Get-MigrationEndpoint CutoverEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*

```

### <a name="step-3-create-the-cutover-migration-batch"></a>3단계: 단독형 마이그레이션 일괄 처리 만들기
<a name="BK_Step3"> </a>

You can use the **New-MigrationBatch** cmdlet in Exchange Online PowerShell to create a migration batch for a cutover migration. You can create a migration batch and start it automatically by including the _AutoStart_ parameter. Alternatively, you can create the migration batch and then manually start it afterwards by using the **Start-MigrationBatch** cmdlet. This example creates a migration batch called "CutoverBatch" and uses the migration endpoint that was created in the previous step.
  
```
New-MigrationBatch -Name CutoverBatch -SourceEndpoint CutoverEndpoint -AutoStart
```

This example also creates a migration batch called "CutoverBatch" and uses the migration endpoint that was created in the previous step. Because the  _AutoStart_ parameter isn't included, the migration batch has to be manually started on the migration dashboard or by using **Start-MigrationBatch** cmdlet. As previously stated, only one cutover migration batch can exist at a time.
  
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

To start the migration batch in Exchange Online PowerShell, run the following command. This will create a migration batch called "CutoverBatch".
  
```
Start-MigrationBatch -Identity CutoverBatch
```

#### <a name="verify-it-worked"></a>작동하는지 확인

If a migration batch is successfully started, its status on the migration dashboard is specified as Syncing. To verify that you've successfully started a migration batch using Exchange Online PowerShell, run the following command:
  
```
Get-MigrationBatch -Identity CutoverBatch |  Format-List Status
```

### <a name="step-5-route-your-email-to-office-365"></a>5단계: Office 365로 전자 메일 라우팅
<a name="BK_Step5"> </a>

Email systems use a DNS record called an MX record to figure out where to deliver emails. During the email migration process, your MX record was pointing to your source email system. Now that the email migration to Office 365 is complete, it's time to point your MX record at Office 365. This helps make sure that email is delivered to your Office 365 mailboxes. By moving the MX record, you can also you turn off your old email system when you're ready. 
  
For many DNS providers, there are specific instructions to [change your MX record](https://go.microsoft.com/fwlink/p/?LinkId=279163). If your DNS provider isn't included, or if you want to get a sense of the general directions, [general MX record instructions ](https://go.microsoft.com/fwlink/?LinkId=397449) are provided as well.
  
It can take up to 72 hours for the email systems of your customers and partners to recognize the changed MX record. Wait at least 72 hours before you proceed to the next task: [Step 6: Delete the cutover migration batch](use-powershell-to-perform-a-cutover-migration-to-office-365.md#Bk_step6). 
  
### <a name="step-6-delete-the-cutover-migration-batch"></a>6단계: 단독형 마이그레이션 일괄 처리 삭제
<a name="Bk_step6"> </a>

After you change the MX record and verify that all email is being routed to Office 365 mailboxes, notify the users that their mail is going to Office 365. After this, you can delete the cutover migration batch. Verify the following before you delete the migration batch.
  
- All users are using Office 365 mailboxes. After the batch is deleted, mail sent to mailboxes on the on-premises Exchange Server isn't copied to the corresponding Office 365 mailboxes.
    
- Office 365 mailboxes were synchronized at least once after mail began being sent directly to them. To do this, make sure that the value in the Last Synced Time box for the migration batch is more recent than when mail started being routed directly to Office 365 mailboxes.
    
Exchange Online PowerShell에서 "CutoverBatch" 마이그레이션 일괄 처리를 삭제하려면 다음 명령을 실행합니다.
  
```
Remove-MigrationBatch -Identity CutoverBatch
```

### <a name="section-7-assign-user-licenses"></a>섹션 7: 사용자 라이선스 할당
<a name="BK_Step7"> </a>

 **라이선스를 할당하여 마이그레이션된 계정에 대한 Office 365 사용자 계정을 활성화합니다.** 라이선스를 할당하지 않은 경우 30일 유예 기간이 끝나면 사서함을 사용할 수 없습니다. Microsoft 365 관리 센터에서 라이선스를 할당 하려면[비즈니스용 Office 365에 대 한 라이선스 할당 또는](https://go.microsoft.com/fwlink/?LinkId=536681)할당 해제를 참조 하세요.
  
### <a name="step-8-complete-post-migration-tasks"></a>8단계: 마이그레이션 후 작업 완료
<a name="BK_Step8"> </a>

- **Create an Autodiscover DNS record so users can easily get to their mailboxes.** After all on-premises mailboxes are migrated to Office 365, you can configure an Autodiscover DNS record for your Office 365 organization to enable users to easily connect to their new Office 365 mailboxes with Outlook and mobile clients. This new Autodiscover DNS record has to use the same namespace that you're using for your Office 365 organization. For example, if your cloud-based namespace is cloud.contoso.com, the Autodiscover DNS record you need to create is autodiscover.cloud.contoso.com.
    
    Exchange Server를 유지하는 경우 Outlook 클라이언트가 올바른 사서함에 연결되도록 자동 검색 DNS CNAME 레코드는 마이그레이션 후에 내부 및 외부 DNS 둘 다에서 Office 365를 가리켜야 합니다.
    
    > [!NOTE]
    >  또한 Exchange 2007, Exchange 2010 및 Exchange 2013에서  `Set-ClientAccessServer AutodiscoverInternalConnectionURI`를  `Null`로 설정해야 합니다. 
  
    Office 365 uses a CNAME record to implement the Autodiscover service for Outlook and mobile clients. The Autodiscover CNAME record must contain the following information:
    
  - **별칭:** autodiscover
    
  - **대상:** autodiscover.outlook.com
    
    자세한 내용은 [DNS 레코드를 관리하는 경우 Office 365용 DNS 레코드 만들기](https://go.microsoft.com/fwlink/p/?LinkId=535028)를 참조하세요.
    
- **Decommission on-premises Exchange servers.** After you've verified that all email is being routed directly to the Office 365 mailboxes, and you no longer need to maintain your on-premises email organization or don't plan on implementing a single sign-on (SSO) solution, you can uninstall Exchange from your servers and remove your on-premises Exchange organization.
    
    자세한 내용은 다음 항목을 참조하십시오.
    
  - [Exchange 2010 수정 또는 제거](https://go.microsoft.com/fwlink/?LinkId=217936)
    
  - [Exchange 2007 조직 제거 방법](https://go.microsoft.com/fwlink/?LinkID=100485)
    
  - [Exchange Server 2003 제거 방법](https://go.microsoft.com/fwlink/?LinkID=56561)
    

