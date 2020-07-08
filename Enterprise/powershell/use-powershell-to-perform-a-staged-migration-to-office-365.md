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
ms.openlocfilehash: ca50edd079e17808c46ff5a956ed2efad34eb322
ms.sourcegitcommit: c6a2256f746f55d1cfb739649ffeee1f2f2152aa
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "45052561"
---
# <a name="use-powershell-to-perform-a-staged-migration-to-office-365"></a>PowerShell을 사용하여 Office 365로 미리 구성된 마이그레이션 수행

미리 구성된 마이그레이션을 사용하여 시간에 따라 원본 전자 메일 시스템의 사용자 사서함 콘텐츠를 Office 365로 마이그레이션할 수 있습니다.
  
This article walks you through the tasks involved with for a staged email migration using Exchange Online PowerShell. The topic, [What you need to know about a staged email migration to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536487), gives you an overview of the migration process. When you're comfortable with the contents of that article, use this one to begin migrating mailboxes from one email system to another.
  
> [!NOTE]
> You can also use the Exchange admin center to perform staged migration. See [Perform a staged migration of email to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536687). 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>시작하기 전에 알아야 할 내용

Estimated time to complete this task: 2-5 minutes to create a migration batch. After the migration batch is started, the duration of the migration will vary based on the number of mailboxes in the batch, the size of each mailbox, and your available network capacity. For information about other factors that affect how long it takes to migrate mailboxes to Office 365, see [Migration Performance](https://go.microsoft.com/fwlink/p/?LinkId=275079).
  
You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Migration" entry in the [Recipients Permissions](https://go.microsoft.com/fwlink/p/?LinkId=534105) topic.
  
To use the Exchange Online PowerShell cmdlets, you need to sign in and import the cmdlets into your local Windows PowerShell session. See [Connect to Exchange Online using remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121) for instructions.
  
전체 마이그레이션 명령 목록을 보려면 [이동 및 마이그레이션 cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=534750)을 참조하세요.
  
## <a name="migration-steps"></a>마이그레이션 단계

### <a name="step-1-prepare-for-a-staged-migration"></a>1단계: 미리 구성된 마이그레이션 준비

미리 구성된 마이그레이션을 사용하여 사서함을 Office 365로 마이그레이션하기 전에 Exchange 환경을 일부 변경해야 합니다.
  
 **Configure Outlook Anywhere on your on-premises Exchange Server** The email migration service uses Outlook Anywhere (also known as RPC over HTTP), to connect to your on-premises Exchange Server. For information about how to set up Outlook Anywhere for Exchange Server 2007, and Exchange 2003, see the following:
  
- [Exchange 2007: "외부에서 Outlook 사용" 설정 방법](https://go.microsoft.com/fwlink/?LinkID=167210)
    
- [Exchange 2003: "외부에서 Outlook 사용" 구성 방법](https://go.microsoft.com/fwlink/?LinkID=167209)
    
> [!IMPORTANT]
> You must use a certificate issued by a trusted certification authority (CA) with your Outlook Anywhere configuration. Outlook Anywhere can't be configured with a self-signed certificate. For more information, see [How to configure SSL for Outlook Anywhere](https://go.microsoft.com/fwlink/?LinkID=80875). 
  
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

 **Set permissions** The on-premises user account that you use to connect to your on-premises Exchange organization (also called the migration administrator) must have the necessary permissions to access the on-premises mailboxes that you want to migrate to Office 365. This user account is used when you connect to your email system by creating a migration endpoint later in this procedure ([Step 3: Create a migration endpoint](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Endpoint) ).
  
사서함을 마이그레이션하려면 관리자는 다음 사용 권한 집합 중 하나가 있어야 합니다.
  
- 온-프레미스 조직의 Active Directory에 있는 **Domain Admins** 그룹의 구성원이어야 합니다.
    
    또는
    
- 각 온-프레미스 사서함에 대해 **FullAccess** 권한이 할당되고 온-프레미스 사용자 계정에 대해 **TargetAddress** 속성을 수정할 수 있는 **WriteProperty** 권한이 할당되어야 합니다.
    
     선택하거나 
    
- 사용자 사서함을 저장하는 온-프레미스 사서함 데이터베이스에 대해 **다음으로 받기** 권한이 할당되고 온-프레미스 사용자 계정에 대해 **TargetAddress** 속성을 수정할 수 있는 **WriteProperty** 권한이 할당되어야 합니다.
    
이러한 사용 권한을 설정하는 방법에 대한 지침은 [Office 365로 사서함을 마이그레이션할 수 있는 권한 할당](https://go.microsoft.com/fwlink/?LinkId=521656)을 참조하세요.
  
 **Disable Unified Messaging (UM)** If UM is turned on for the on-premises mailboxes you're migrating, turn off UM before migration. Turn on UM for the mailboxes after migration is complete. For how-to steps, see[disable unified messaging](https://go.microsoft.com/fwlink/?LinkId=521891).
  
 **Use directory synchronization to create new users in Office 365.** You use directory synchronization to create all the on-premises users in your Office 365 organization.
  
You need to license the users after they're created. You have 30 days to add licenses after the users are created. For steps to add licenses, see [Step 8: Complete post-migration tasks](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Postmigration).
  
 Microsoft azure Active Directory (Azure AD) 동기화 도구 또는 Microsoft Azure AD Sync Services를 사용 하 여 Office 365에서 온-프레미스 사용자를 동기화 하 고 만들 수 있습니다. 사서함이 Office 365로 마이그레이션되면 온-프레미스 조직에서 사용자 계정을 관리하고 Office 365 조직과 동기화되도록 합니다. 자세한 내용은 [디렉터리 통합](https://go.microsoft.com/fwlink/?LinkId=521788)을 참조하세요.
  
### <a name="step-2-create-a-csv-file-for-a-staged-migration-batch"></a>2단계: 미리 구성된 마이그레이션 일괄 처리에 대한 CSV 파일 만들기

After you identify the users whose on-premises mailboxes you want to migrate to Office 365, you use a comma separated value (CSV ) file to create a migration batch. Each row in the CSV file—used by Office 365 to run the migration—contains information about an on-premises mailbox. 
  
> [!NOTE]
> There isn't a limit for the number of mailboxes that you can migrate to Office 365 using a staged migration. The CSV file for a migration batch can contain a maximum of 2,000 rows. To migrate more than 2,000 mailboxes, create additional CSV files and use each file to create a new migration batch. 
  
 **지원되는 특성**
  
The CSV file for a staged migration supports the following three attributes. Each row in the CSV file corresponds to a mailbox and must contain a value for each of these attributes.
  
|**특성**|**설명**|**필수 여부**|
|:-----|:-----|:-----|
|EmailAddress  <br/> |온-프레미스 사서함에 대한 기본 SMTP 전자 메일 주소(예: pilarp@contoso.com)를 지정합니다.  <br/> Use the primary SMTP address for on-premises mailboxes and not user IDs from the Office 365. For example, if the on-premises domain is named contoso.com but the Office 365 email domain is named service.contoso.com, you would use the contoso.com domain name for email addresses in the CSV file.  <br/> |필수  <br/> |
|암호  <br/> |The password to be set for the new Office 365 mailbox. Any password restrictions that are applied to your Office 365 organization also apply to the passwords included in the CSV file.  <br/> |옵션  <br/> |
|ForceChangePassword  <br/> |Specifies whether a user must change the password the first time they sign in to their new Office 365 mailbox. Use **True** or **False** for the value of this parameter. <br/> > [!NOTE]> 온-프레미스 조직에서 AD FS(Active Directory Federation Services)를 배포하여 SSO(Single Sign-On) 솔루션을 구현한 경우 **ForceChangePassword** 특성 값으로 **False** 를 사용해야 합니다.          |옵션  <br/> |
   
 **CSV 파일 형식**
  
Here's an example of the format for the CSV file. In this example, three on-premises mailboxes are migrated to Office 365.
  
The first row, or header row, of the CSV file lists the names of the attributes, or fields, specified in the rows that follow. Each attribute name is separated by a comma.
  
```powershell
EmailAddress,Password,ForceChangePassword 
pilarp@contoso.com,Pa$$w0rd,False 
tobyn@contoso.com,Pa$$w0rd,False 
briant@contoso.com,Pa$$w0rd,False 
```

Each row under the header row represents one user and supplies the information that will be used to migrate the user's mailbox. The attribute values in each row must be in the same order as the attribute names in the header row. 
  
Use any text editor, or an application like Excel , to create the CSV file. Save the file as a .csv or .txt file.
  
> [!NOTE]
> If the CSV file contains non-ASCII or special characters, save the CSV file with UTF-8 or other Unicode encoding. Depending on the application, saving the CSV file with UTF-8 or other Unicode encoding can be easier when the system locale of the computer matches the language used in the CSV file. 
  
### <a name="step-3-create-a-migration-endpoint"></a>3단계: 마이그레이션 끝점 만들기
<a name="BK_Endpoint"> </a>

To migrate email successfully, Office 365 needs to connect and communicate with the source email system. To do this, Office 365 uses a migration endpoint. To create an Outlook Anywhere migration endpoint by using PowerShell, for staged migration, first [connect to Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121). 
  
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
> The **New-MigrationEndpoint** cmdlet can be used to specify a database for the service to use by using the **-TargetDatabase** option. Otherwise a database is randomly assigned from the Active Directory Federation Services (AD FS) 2.0 site where the management mailbox is located.
  
#### <a name="verify-it-worked"></a>작동하는지 확인

Exchange Online PowerShell에서 다음 명령을 실행하여 "StagedEndpoint" 마이그레이션 끝점에 대한 정보를 표시합니다.
  
```powershell
Get-MigrationEndpoint StagedEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*
```

### <a name="step-4-create-and-start-a-stage-migration-batch"></a>4단계: 미리 구성된 마이그레이션 일괄 처리 만들기 및 시작
<a name="BK_Endpoint"> </a>

You can use the **New-MigrationBatch** cmdlet in Exchange Online PowerShell to create a migration batch for a cutover migration. You can create a migration batch and start it automatically by including the _AutoStart_ parameter. Alternatively, you can create the migration batch and then manually start it afterwards by using the **Start-MigrationBatch** cmdlet. This example creates a migration batch called "StagedBatch1" and uses the migration endpoint that was created in the previous step.
  
```powershell
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint -AutoStart
```

This example also creates a migration batch called "StagedBatch1" and uses the migration endpoint that was created in the previous step. Because the  _AutoStart_ parameter isn't included, the migration batch has to be manually started on the migration dashboard or by using **Start-MigrationBatch** cmdlet. As previously stated, only one cutover migration batch can exist at a time.
  
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

After you have successfully migrated a batch of mailboxes, you need some way to let users get to their mail. A user whose mailbox has been migrated now has both a mailbox on-premises and one in Office 365. Users who have a mailbox in Office 365 will stop receiving new mail in their on-premises mailbox. 
  
Because you are not done with your migrations, you are not yet ready to direct all users to Office 365 for their email. So what do you do for those people who have both? What you can do is change the on-premises mailboxes that you've already migrated to mail-enabled users. When you change from a mailbox to a mail-enabled user, you can direct the user to Office 365 for their email instead of going to their on-premises mailbox. 
  
Another important reason to convert on-premises mailboxes to mail-enabled users is to retain proxy addresses from the Office 365 mailboxes by copying proxy addresses to the mail-enabled users. This lets you manage cloud-based users from your on-premises organization by using Active Directory. Also, if you decide to decommission your on-premises Exchange Server organization after all mailboxes are migrated to Office 365, the proxy addresses you've copied to the mail-enabled users will remain in your on-premises Active Directory.
    
### <a name="step-6-delete-a-staged-migration-batch"></a>6단계: 미리 구성된 마이그레이션 일괄 처리 삭제
<a name="BK_Endpoint"> </a>

 After all mailboxes in a migration batch have been successfully migrated, and you've converted the on-premises mailboxes in the batch to mail-enabled users, you're ready to delete a staged migration batch. Be sure to verify that mail is being forwarded to the Office 365 mailboxes in the migration batch. When you delete a staged migration batch, the migration service cleans up any records related to the migration batch and deletes the migration batch.
  
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

- **Create an Autodiscover DNS record so users can easily get to their mailboxes.** After all on-premises mailboxes are migrated to Office 365, you can configure an Autodiscover DNS record for your Office 365 organization to enable users to easily connect to their new Office 365 mailboxes with Outlook and mobile clients. This new Autodiscover DNS record has to use the same namespace that you're using for your Office 365 organization. For example, if your cloud-based namespace is cloud.contoso.com, the Autodiscover DNS record you need to create is autodiscover.cloud.contoso.com.
    
    Office 365 uses a CNAME record to implement the Autodiscover service for Outlook and mobile clients. The Autodiscover CNAME record must contain the following information:
    
  - **별칭:** autodiscover
    
  - **대상:** autodiscover.outlook.com
    
    자세한 내용은 [DNS 레코드를 관리하는 경우 Office 365용 DNS 레코드 만들기](https://go.microsoft.com/fwlink/p/?LinkId=535028)를 참조하세요.
    
- **Decommission on-premises Exchange servers.** After you've verified that all email is being routed directly to the Office 365 mailboxes, and you no longer need to maintain your on-premises email organization or don't plan on implementing an SSO solution, you can uninstall Exchange from your servers and remove your on-premises Exchange organization.
    
    자세한 내용은 다음 항목을 참조하십시오.
    
  - [Exchange 2010 수정 또는 제거](https://go.microsoft.com/fwlink/?LinkId=217936)
    
  - [Exchange 2007 조직 제거 방법](https://go.microsoft.com/fwlink/?LinkID=100485)
    
  - [Exchange Server 2003 제거 방법](https://go.microsoft.com/fwlink/?LinkID=56561)
    

