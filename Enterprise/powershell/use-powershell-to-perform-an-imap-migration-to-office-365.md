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
# <a name="use-powershell-to-perform-an-imap-migration-to-office-365"></a><span data-ttu-id="48e4a-103">PowerShell을 사용하여 Office 365로 IMAP 마이그레이션 수행</span><span class="sxs-lookup"><span data-stu-id="48e4a-103">Use PowerShell to perform an IMAP migration to Office 365</span></span>

 <span data-ttu-id="48e4a-104">**요약:** Office 365로 IMAP 마이그레이션을 수행 하려면 Windows PowerShell을 사용 하는 방법에 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="48e4a-104">**Summary:** Learn how to use Windows PowerShell to perform an IMAP migration to Office 365.</span></span>
  
<span data-ttu-id="48e4a-p101">Office 365를 배포 하는 프로세스의 일부로 Internet Mail Access Protocol (IMAP) 전자 메일 서비스에서 Office 365 사용자 사서함의 내용을 마이그레이션하려면 선택할 수 있습니다. 이 문서에서는 Exchange Online PowerShell을 사용 하 여 전자 메일 IMAP 마이그레이션에 대 한 작업을 통해 안내 합니다.</span><span class="sxs-lookup"><span data-stu-id="48e4a-p101">As part of the process of deploying Office 365, you can choose to migrate the contents of user mailboxes from an Internet Mail Access Protocol (IMAP) email service to Office 365. This article walks you through the tasks for an email IMAP migration by using Exchange Online PowerShell.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="48e4a-p102">IMAP 마이그레이션을 수행 하기 위해 Exchange 관리 센터를 사용할 수도 있습니다. [Office 365로 IMAP 사서함 마이그레이션](https://go.microsoft.com/fwlink/p/?LinkId=536685)참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="48e4a-p102">You can also use the Exchange admin center to perform an IMAP migration. See [Migrate your IMAP mailboxes to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536685).</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="48e4a-109">시작하기 전에 알아야 할 내용</span><span class="sxs-lookup"><span data-stu-id="48e4a-109">What do you need to know before you begin?</span></span>

<span data-ttu-id="48e4a-p103">예상이 작업을 완료 시간: 2 ~ 5 분 마이그레이션 일괄 처리를 만듭니다. 마이그레이션 일괄 처리 시작 되 면 마이그레이션 기간에 따라 달라 집니다 일괄 처리의 사서함 수, 사용 가능한 네트워크 용량 및 각 사서함의 크기입니다. Office 365로 사서함 마이그레이션에 걸리는 시간에 영향을 주는 다른 요인에 대 한 정보를 [마이그레이션 성능](https://go.microsoft.com/fwlink/p/?LinkId=275079)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="48e4a-p103">Estimated time to complete this task: 2-5 minutes to create a migration batch. After the migration batch is started, the duration of the migration will vary based on the number of mailboxes in the batch, the size of each mailbox, and your available network capacity. For information about other factors that affect how long it takes to migrate mailboxes to Office 365, see [Migration Performance](https://go.microsoft.com/fwlink/p/?LinkId=275079).</span></span>
  
<span data-ttu-id="48e4a-p104">이 절차를 수행 하기 전에 사용 권한을 할당 해야 합니다. 필요한 사용 권한을 [받는 사람에 게 사용 권한](https://go.microsoft.com/fwlink/p/?LinkId=534105) 항목의 테이블의 "마이그레이션" 항목을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="48e4a-p104">You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Migration" entry in a table in the [Recipients Permissions](https://go.microsoft.com/fwlink/p/?LinkId=534105) topic.</span></span>
  
<span data-ttu-id="48e4a-p105">Exchange Online PowerShell cmdlet을 사용 하려면 로그인 하 고 로컬 Windows PowerShell 세션으로 cmdlet을 가져올 해야 합니다. 지침에 대 한 [원격 PowerShell을 사용 하는 Exchange Online에 연결](https://go.microsoft.com/fwlink/p/?LinkId=534121) 을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="48e4a-p105">To use the Exchange Online PowerShell cmdlets, you need to sign in and import the cmdlets into your local Windows PowerShell session. See [Connect to Exchange Online using remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121) for instructions.</span></span>
  
<span data-ttu-id="48e4a-117">마이그레이션 명령 목록이 전체 [이동 및 마이그레이션 cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=534750)을 참고 하십시오.</span><span class="sxs-lookup"><span data-stu-id="48e4a-117">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
  
<span data-ttu-id="48e4a-118">IMAP 마이그레이션에 적용되는 제한 사항은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="48e4a-118">The following restrictions apply to IMAP migrations:</span></span>
  
- <span data-ttu-id="48e4a-p106">사용자의 받은 편지함 또는 다른 메일 폴더에만 항목을 마이그레이션할 수 있습니다. 연락처, 일정 항목 또는 작업을 마이그레이션할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="48e4a-p106">Only items in a user's inbox or other mail folders can be migrated. You can't migrate contacts, calendar items, or tasks.</span></span>
    
- <span data-ttu-id="48e4a-121">최대 500, 000 개의 항목이 사용자의 사서함에서 마이그레이션할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48e4a-121">A maximum of 500,000 items can be migrated from a user's mailbox.</span></span>
    
- <span data-ttu-id="48e4a-122">마이그레이션할 수 있는 최대 메시지 크기는 35MB입니다.</span><span class="sxs-lookup"><span data-stu-id="48e4a-122">The maximum message size that can be migrated is 35 MB.</span></span>
    
## <a name="migration-steps"></a><span data-ttu-id="48e4a-123">마이그레이션 단계</span><span class="sxs-lookup"><span data-stu-id="48e4a-123">Migration steps</span></span>

### <a name="step-1-prepare-for-an-imap-migration"></a><span data-ttu-id="48e4a-124">1단계: IMAP 마이그레이션 준비</span><span class="sxs-lookup"><span data-stu-id="48e4a-124">Step 1: Prepare for an IMAP migration</span></span>
<span data-ttu-id="48e4a-125"><a name="BK_Step1"> </a></span><span class="sxs-lookup"><span data-stu-id="48e4a-125"></span></span>

- <span data-ttu-id="48e4a-p107">**도메인 수에 대 한 IMAP 조직이 있는 경우 Office 365 조직의 허용된 도메인으로 추가 합니다.** Office 365 사서함에 대 한 이미 소유 하는 동일한 도메인을 사용 하려는 경우에 먼저 Office 365에 허용된 도메인으로 추가 해야 합니다. 해당 작업을 추가한 후에 Office 365에서 사용자를 만들 수 있습니다. 자세한 내용은[Office 365에서 도메인을 확인 합니다.](https://go.microsoft.com/fwlink/p/?LinkId=534110)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="48e4a-p107">**If you have a domain for you IMAP organization, add it as an accepted domain of your Office 365 organization.** If you want to use the same domain you already own for your Office 365 mailboxes, you first have to add it as an accepted domain to Office 365. After you have added it, you can create your users in Office 365. For more information, see[Verify your domain in Office 365](https://go.microsoft.com/fwlink/p/?LinkId=534110).</span></span>
    
- <span data-ttu-id="48e4a-p108">**Office 365 사서함 수 있도록 Office 365에 각 사용자를 추가 합니다.** 자세한 내용은[비즈니스를 위한 Office 365에 사용자 추가](https://go.microsoft.com/fwlink/p/?LinkId=535065)참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="48e4a-p108">**Add each user to Office 365 so that they have an Office 365 mailbox.** For instructions, see[Add users to Office 365 for business](https://go.microsoft.com/fwlink/p/?LinkId=535065).</span></span>
    
- <span data-ttu-id="48e4a-p109">**접수 IMAP 서버의 FQDN**입니다. IMAP 마이그레이션 끝점을 만들 때에서 사서함 데이터 마이그레이션을 정규화 된 도메인 이름 (FQDN) (전체 컴퓨터 이름의 라고도 함) IMAP 서버의 제공 해야 합니다. 인터넷을 통해 IMAP 서버와 통신 하는 FQDN을 사용할 수 있는지 확인 하려면 IMAP 클라이언트나 PING 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="48e4a-p109">**Obtain the FQDN of the IMAP server**. You need to provide the fully qualified domain name (FQDN) (also called the full computer name) of the IMAP server that you will migrate mailbox data from when you create an IMAP migration endpoint. Use an IMAP client or the PING command to verify that you can use the FQDN to communicate with the IMAP server over the Internet.</span></span>
    
- <span data-ttu-id="48e4a-p110">**IMAP 연결을 허용 하도록 방화벽 구성**합니다. 마이그레이션하는 동안 Microsoft 데이터 센터에서 시작 되는 네트워크 트래픽을 IMAP 서버를 호스트 하는 조직의 입력할 수 있도록 IMAP 서버를 호스팅하는 조직의 방화벽에서 포트를 열기 해야할 수 있습니다. Microsoft 데이터 센터에서 사용 하는 IP 주소 목록이 [Exchange Online Url 및 IP 주소 범위](https://go.microsoft.com/fwlink/p/?LinkId=535066)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="48e4a-p110">**Configure the firewall to allow IMAP connections**. You might have to open ports in the firewall of the organization that hosts the IMAP server so network traffic originating from the Microsoft datacenter during the migration is allowed to enter the organization that hosts the IMAP server. For a list of IP addresses used by Microsoft datacenters, see [Exchange Online URLs and IP Address Ranges](https://go.microsoft.com/fwlink/p/?LinkId=535066).</span></span>
    
- <span data-ttu-id="48e4a-p111">**IMAP 조직 내의 사서함에에서 액세스 하려면 계정 사용 권한 관리자를 할당**합니다. CSV 파일의 관리자 자격 증명을 사용 하는 경우 사용 하는 계정에 온-프레미스 사서함에 액세스 하려면 필요한 권한이 있어야 합니다. 사용자 사서함에 액세스 하는 데 필요한 사용 권한은 특정 IMAP 서버에 의해 결정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="48e4a-p111">**Assign the administrator account permissions to access mailboxes in your IMAP organization**. If you use administrator credentials in the CSV file, the account that you use must have the necessary permissions to access the on-premises mailboxes. The permissions required to access user mailboxes is determined by the particular IMAP server.</span></span> 
    
- <span data-ttu-id="48e4a-p112">**Exchange Online PowerShell cmdlet을 사용 하 여**, 해야에 로그인 하 고 cmdlet은 로컬 Windows PowerShell 세션으로 가져옵니다. 지침에 대 한 [원격 PowerShell을 사용 하는 Exchange Online에 연결](https://go.microsoft.com/fwlink/p/?LinkId=534121) 을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="48e4a-p112">**To use the Exchange Online PowerShell cmdlets**, you need to sign in and import the cmdlets into your local Windows PowerShell session. See [Connect to Exchange Online using remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121) for instructions.</span></span>
    
    <span data-ttu-id="48e4a-143">마이그레이션 명령 목록이 전체 [이동 및 마이그레이션 cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=534750)을 참고 하십시오.</span><span class="sxs-lookup"><span data-stu-id="48e4a-143">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
    
- <span data-ttu-id="48e4a-p113">**IMAP 서버에 연결할 수 있는지 확인**합니다. 다음 명령을 실행 Exchange 온라인 PowerShell IMAP 서버에 대 한 연결 설정을 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="48e4a-p113">**Verify that you can connect to your IMAP server**. Run the following command in Exchange Online PowerShell to test the connection settings to your IMAP server.</span></span>
    
  ```
  Test-MigrationServerAvailability -IMAP -RemoteServer <FQDN of IMAP server> -Port <143 or 993> -Security <None, Ssl, or Tls>
  ```

    <span data-ttu-id="48e4a-146">**Port** 매개 변수 값에 대 한 암호화에 대 한 143을 사용 하 여 일반적인은 또는 전송 계층 보안 (TLS) 연결 및 SSL 연결에 대 한 993을 사용 하 여 합니다.</span><span class="sxs-lookup"><span data-stu-id="48e4a-146">For the value of the **Port** parameter, it's typical to use 143 for unencrypted or Transport Layer Security (TLS) connections and to use 993 for SSL connections.</span></span>
    
### <a name="step-2-create-a-csv-file-for-an-imap-migration-batch"></a><span data-ttu-id="48e4a-147">2단계: IMAP 마이그레이션 일괄 처리를 위한 CSV 파일 만들기</span><span class="sxs-lookup"><span data-stu-id="48e4a-147">Step 2: Create a CSV file for an IMAP migration batch</span></span>
<span data-ttu-id="48e4a-148"><a name="BK_Step2"> </a></span><span class="sxs-lookup"><span data-stu-id="48e4a-148"></span></span>

<span data-ttu-id="48e4a-p114">IMAP 마이그레이션 일괄 처리에서 해당 사서함을 마이그레이션할 사용자 그룹을 식별합니다. CSV 파일의 각 행에는 IMAP 메시징 시스템의 사서함에 연결하는 데 필요한 정보가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48e4a-p114">Identify the group of users whose mailboxes you want to migrate in an IMAP migration batch. Each row in the CSV file contains information necessary to connect to a mailbox in the IMAP messaging system.</span></span>
  
<span data-ttu-id="48e4a-151">각 사용자의 필수 특성은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="48e4a-151">Here are the required attributes for each user:</span></span> 
  
- <span data-ttu-id="48e4a-152">**EmailAddress** 는 사용자의 Office 365 사서함에 대 한 사용자 ID를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="48e4a-152">**EmailAddress** specifies the user ID for the user's Office 365 mailbox.</span></span>
    
- <span data-ttu-id="48e4a-153">**UserName** 은 IMAP 서버 사서함에 액세스를 사용 하 여 계정에 대 한 로그온 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="48e4a-153">**UserName** specifies the logon name for the account to use to access the mailbox on the IMAP server.</span></span>
    
- <span data-ttu-id="48e4a-154">**암호** **사용자 이름** 열에서 계정의 암호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="48e4a-154">**Password** specifies the password for the account in the **UserName** column.</span></span>
    
<span data-ttu-id="48e4a-p115">다음은 CSV 파일 형식의 예입니다. 이 예에서는 다음 세 개의 사서함을 마이그레이션합니다.</span><span class="sxs-lookup"><span data-stu-id="48e4a-p115">Here's an example of the format for the CSV file. In this example, three mailboxes are migrated:</span></span>
  
```
EmailAddress,UserName,Password
terrya@contoso.edu,terry.adams,1091990
annb@contoso.edu,ann.beebe,2111991
paulc@contoso.edu,paul.cannon,3281986
```

<span data-ttu-id="48e4a-157">사용자 이름 외에도 **사용자 이름** 특성에 대 한 IMAP 서버에서 사서함에 액세스 하는데 필요한 권한을 할당 된 계정의 자격 증명을 사용할 수 있습니다, IMAP 중 일부에 사용 되는 특정 형식 중 일부는 다음과 같습니다. 서버:</span><span class="sxs-lookup"><span data-stu-id="48e4a-157">For the **UserName** attribute, in addition to the user name, you can use the credentials of an account that has been assigned the necessary permissions to access mailboxes on the IMAP server, the following are some of the specific formats used for some of the IMAP servers:</span></span>
  
 <span data-ttu-id="48e4a-158">**Microsoft Exchange:**</span><span class="sxs-lookup"><span data-stu-id="48e4a-158">**Microsoft Exchange:**</span></span>
  
<span data-ttu-id="48e4a-p116">Microsoft Exchange에 대 한 IMAP 구현에서 전자 메일을 마이그레이션하는 경우 CSV 파일의 **사용자 이름** 특성에 대 한 **도메인/Admin_UserName/User_UserName** 형식을 사용 합니다. Terry Adams, Ann Beebe 및 Paul Cannon에 대 한 Exchange에서 전자 메일을 마이그레이션하는 경우를 가정해 보겠습니다. 메일 관리자 계정이 있는 사용자 이름은 **mailadmin** 이 고 암호는 **P@ssw0rd**해야 합니다. 다음과 같이 나타납니다 CSV 파일은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="48e4a-p116">If you're migrating email from the IMAP implementation for Microsoft Exchange, use the format **Domain/Admin_UserName/User_UserName** for the **UserName** attribute in the CSV file. Let's say you're migrating email from Exchange for Terry Adams, Ann Beebe, and Paul Cannon. You have a mail administrator account, where the user name is **mailadmin** and the password is **P@ssw0rd**. Here's what your CSV file would look like:</span></span>
  
```
EmailAddress,UserName,Password
terrya@contoso.edu,contoso-students/mailadmin/terry.adams,P@ssw0rd
annb@contoso.edu,contoso-students/mailadmin/ann.beebe,P@ssw0rd
paulc@contoso.edu,contoso-students/mailadmin/paul.cannon,P@ssw0rd
```

 <span data-ttu-id="48e4a-163">**Dovecot:**</span><span class="sxs-lookup"><span data-stu-id="48e4a-163">**Dovecot:**</span></span>
  
<span data-ttu-id="48e4a-p117">Dovecot IMAP 서버와 같은 단순 인증 및 보안 레이어 (SASL)를 지 원하는 IMAP 서버 사용 * *User_UserName*Admin_UserName*형식에 대 한 *, 여기에서 별표 (*)는 구성 가능한 구분 기호입니다. 관리자 자격 증명 **mailadmin** 및 **P@ssw0rd**를 사용 하 여 Dovecot IMAP 서버에서 동일한 해당 사용자의 전자 메일을 마이그레이션하는 경우를 가정해 봅니다. 다음과 같이 나타납니다 CSV 파일은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="48e4a-p117">For IMAP servers that support Simple Authentication and Security Layer (SASL), such as a Dovecot IMAP server, use the format **User_UserName*Admin_UserName**, where the asterisk ( * ) is a configurable separator character. Let's say you're migrating those same users' email from a Dovecot IMAP server using the administrator credentials **mailadmin** and **P@ssw0rd**. Here's what your CSV file would look like:</span></span>
  
```
EmailAddress,UserName,Password
terrya@contoso.edu,terry.adams*mailadmin,P@ssw0rd
annb@contoso.edu,ann.beebe*mailadmin,P@ssw0rd
paulc@contoso.edu,paul.cannon*mailadmin,P@ssw0rd
```

 <span data-ttu-id="48e4a-167">**Mirapoint:**</span><span class="sxs-lookup"><span data-stu-id="48e4a-167">**Mirapoint:**</span></span>
  
<span data-ttu-id="48e4a-p118">전자 메일 Mirapoint 메시지 서버에서를 마이그레이션하는 경우 관리자 자격 증명에 대 한 형식 **#user@domain#Admin_UserName#** 를 사용 합니다. 관리자 자격 증명 **mailadmin** 및 **P@ssw0rd**를 사용 하 여 Mirapoint에서 전자 메일을 마이그레이션할 CSV 파일은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="48e4a-p118">If you're migrating email from Mirapoint Message Server, use the format **#user@domain#Admin_UserName#** for the administrator credentials. To migrate email from Mirapoint using the administrator credentials **mailadmin** and **P@ssw0rd**, your CSV file would look like this:</span></span>
  
```
EmailAddress,UserName,Password
terrya@contoso.edu,#terry.adams@contoso-students.edu#mailadmin#,P@ssw0rd
annb@contoso.edu,#ann.beebe@contoso-students.edu#mailadmin#,P@ssw0rd
paulc@contoso.edu,#paul.cannon@contoso-students.edu#mailadmin#,P@ssw0rd
```

 <span data-ttu-id="48e4a-170">**Courier IMAP:**</span><span class="sxs-lookup"><span data-stu-id="48e4a-170">**Courier IMAP:**</span></span>
  
<span data-ttu-id="48e4a-p119">Courier IMAP와 같은 일부 원본 전자 메일 시스템 사서함 관리 자격 증명을 사용 하 여 Office 365로 사서함 마이그레이션 지원 하지 않습니다. 대신, 가상 공유 폴더를 사용 하 여 원본 전자 메일 시스템을 설정할 수 있습니다. 가상 공유 폴더를 사용 하 여 원본 전자 메일 시스템에서 사용자 사서함에 액세스 하는 사서함 관리 자격 증명을 사용할 수 있습니다. Courier IMAP에 대 한 가상 공유 폴더를 구성 하는 방법에 대 한 자세한 내용은 [공유 폴더](https://go.microsoft.com/fwlink/p/?LinkId=398870)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="48e4a-p119">Some source email systems, such as Courier IMAP, don't support using mailbox admin credentials to migrate mailboxes to Office 365. Instead, you can set up your source email system to use virtual shared folders. By using virtual shared folders, you can use the mailbox admin credentials to access user mailboxes on the source email system. For more information about how to configure virtual shared folders for Courier IMAP, see [Shared Folders](https://go.microsoft.com/fwlink/p/?LinkId=398870).</span></span>
  
<span data-ttu-id="48e4a-p120">사서함을 마이그레이션하려면 원본 전자 메일 시스템에서 가상 공유 폴더를 설정한 후, 마이그레이션 파일의 선택적 특성 **UserRoot** 를 포함 해야 합니다. 이 특성 원본 전자 메일 시스템에 가상 공유 폴더 구조에서 각 사용자의 사서함의 위치를 지정합니다. 예, Terry의 사서함에 경로 /users/terry.adams 합니다.</span><span class="sxs-lookup"><span data-stu-id="48e4a-p120">To migrate mailboxes after you set up virtual shared folders on your source email system, you have to include the optional attribute **UserRoot** in the migration file. This attribute specifies the location of each user's mailbox in the virtual shared folder structure on the source email system. For example, the path to Terry's mailbox is /users/terry.adams.</span></span>
  
<span data-ttu-id="48e4a-178">**UserRoot** 특성이 포함 된 CSV 파일의 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="48e4a-178">Here's an example of a CSV file that contains the **UserRoot** attribute:</span></span>
  
```
EmailAddress,UserName,Password,UserRoot
terrya@contoso.edu,mailadmin,P@ssw0rd,/users/terry.adams
annb@contoso.edu,mailadmin,P@ssw0rd,/users/ann.beebe
paulc@contoso.edu,mailadmin,P@ssw0rd,/users/paul.cannon
```

### <a name="step-3-create-an-imap-migration-endpoint"></a><span data-ttu-id="48e4a-179">3단계: IMAP 마이그레이션 끝점 만들기</span><span class="sxs-lookup"><span data-stu-id="48e4a-179">Step 3: Create an IMAP migration endpoint</span></span>
<span data-ttu-id="48e4a-180"><a name="BK_Step3"> </a></span><span class="sxs-lookup"><span data-stu-id="48e4a-180"></span></span>

<span data-ttu-id="48e4a-p121">전자 메일을 성공적으로 마이그레이션 Office 365에 연결 하 고 원본 전자 메일 시스템과 통신할 해야 합니다. 이 위해 Office 365 마이그레이션 끝점을 사용 합니다. 또한 마이그레이션 끝점 동시에 마이그레이션할 사서함 수와 24 시간 마다 발생 하는 증분 동기화 하는 동안 동시에 동기화 하는 사서함의 수를 정의 합니다. [Exchange Online에 연결](https://go.microsoft.com/fwlink/p/?LinkId=534121)하는 첫번째 IMAP 마이그레이션에 대 한 마이그레이션 끝점을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="48e4a-p121">To migrate email successfully, Office 365 needs to connect to and communicate with the source email system. To do this, Office 365 uses a migration endpoint. The migration endpoint also defines the number of mailboxes to migrate simultaneously and the number of mailboxes to synchronize simultaneously during incremental synchronization, which occurs once every 24 hours. To create a migration end point for IMAP migration, first [connect to Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span></span> 
  
<span data-ttu-id="48e4a-185">마이그레이션 명령 목록이 전체 [이동 및 마이그레이션 cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=534750)을 참고 하십시오.</span><span class="sxs-lookup"><span data-stu-id="48e4a-185">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
  
<span data-ttu-id="48e4a-186">Exchange Online PowerShell에서 "IMAPEndpoint"라는 IMAP 마이그레이션 끝점을 만들려면 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="48e4a-186">To create the IMAP migration endpoint called "IMAPEndpoint" in Exchange Online PowerShell, run the following command:</span></span>
  
```
New-MigrationEndpoint -IMAP -Name IMAPEndpoint -RemoteServer imap.contoso.com -Port 993 -Security Ssl

```

<span data-ttu-id="48e4a-p122">또한 동시 마이그레이션, 동시 증분 마이그레이션 및 사용할 포트를 지정 하려면 매개 변수를 추가할 수 있습니다. 다음 Exchange Online PowerShell 명령을 50 동시 마이그레이션을 지원 "IMAPEndpoint" 라는 IMAP 마이그레이션 끝점을 만듭니다 및 최대 25 동시 증분 동기화 합니다. 또한 TLS 암호화에 대 한 포트 143을 사용 하 여 끝점을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="48e4a-p122">You can also add parameters to specify concurrent migrations, concurrent incremental migrations, and the port to use. The following Exchange Online PowerShell command creates an IMAP migration endpoint called "IMAPEndpoint" that supports 50 concurrent migrations and up to 25 concurrent incremental synchronizations. It also configures the endpoint to use port 143 for TLS encryption.</span></span>
  
```
New-MigrationEndpoint -IMAP -Name IMAPEndpoint -RemoteServer imap.contoso.com -Port 143 -Security Tls -MaxConcurrentMigrations
50 -MaxConcurrentIncrementalSyncs 25
```

<span data-ttu-id="48e4a-190">**New-migrationendpoint** cmdlet에 대 한 자세한 내용은[New-migrationendpoint](https://go.microsoft.com/fwlink/p/?LinkId=536437)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="48e4a-190">For more information about the **New-MigrationEndpoint** cmdlet, see[New-MigrationEndpoint](https://go.microsoft.com/fwlink/p/?LinkId=536437).</span></span>
  
#### <a name="verify-it-worked"></a><span data-ttu-id="48e4a-191">작동하는지 확인</span><span class="sxs-lookup"><span data-stu-id="48e4a-191">Verify it worked</span></span>

<span data-ttu-id="48e4a-192">Exchange Online PowerShell에서 다음 명령을 실행하여 "IMAPEndpoint"에 대한 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="48e4a-192">Run the following command in Exchange Online PowerShell to display information about the "IMAPEndpoint":</span></span>
  
```
Get-MigrationEndpoint IMAPEndpoint | Format-List EndpointType,RemoteServer,Port,Security,Max*
```

### <a name="step-4-create-and-start-an-imap-migration-batch"></a><span data-ttu-id="48e4a-193">4단계: IMAP 마이그레이션 일괄 처리 만들기 및 시작</span><span class="sxs-lookup"><span data-stu-id="48e4a-193">Step 4: Create and start an IMAP migration batch</span></span>
<span data-ttu-id="48e4a-194"><a name="BK_Step4"> </a></span><span class="sxs-lookup"><span data-stu-id="48e4a-194"></span></span>

<span data-ttu-id="48e4a-p123">IMAP 마이그레이션에 대 한 마이그레이션 일괄 처리를 만들려는 [New-migrationbatch](https://go.microsoft.com/fwlink/p/?LinkId=536439) cmdlet을 사용할 수 있습니다. 마이그레이션 일괄 처리를 만들고 _자동 시작_ 매개 변수를 포함 하 여 자동으로 시작할 수 있습니다. 또는 마이그레이션 일괄 처리를 만들고[Start-migrationbatch](https://go.microsoft.com/fwlink/p/?LinkId=536440) cmdlet을 사용 하 여 나중에 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48e4a-p123">You can use the [New-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536439) cmdlet to create a migration batch for an IMAP migration. You can create a migration batch and start it automatically by including the _AutoStart_ parameter. Alternatively, you can create the migration batch and then start it afterwards by using the[Start-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536440) cmdlet.</span></span>
  
<span data-ttu-id="48e4a-198">다음 Exchange Online PowerShell 명령은 "IMAPEndpoint"라는 IMAP 끝점을 사용하여 "IMAPBatch1"이라는 마이그레이션 일괄 처리를 자동으로 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="48e4a-198">The following Exchange Online PowerShell command will automatically start the migration batch called "IMAPBatch1" using the IMAP endpoint called "IMAPEndpoint":</span></span>
  
```
New-MigrationBatch -Name IMAPBatch1 -SourceEndpoint IMAPEndpoint -CSVData ([System.IO.File]::ReadAllBytes("C:\\Users\\Administrator\\Desktop\\IMAPmigration_1.csv")) -AutoStart
```

#### <a name="verify-it-worked"></a><span data-ttu-id="48e4a-199">작동하는지 확인</span><span class="sxs-lookup"><span data-stu-id="48e4a-199">Verify it worked</span></span>

<span data-ttu-id="48e4a-200">"IMAPBatch1"에 대 한 정보를 표시 하도록 [Get-migrationbatch](https://go.microsoft.com/fwlink/p/?LinkId=536441) cmdlet을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="48e4a-200">Run the [Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441) cmdlet to display information about the "IMAPBatch1":</span></span>
  
```
Get-MigrationBatch -Identity IMAPBatch1 | Format-List
```

<span data-ttu-id="48e4a-201">다음 명령을 실행하여 일괄 처리가 시작되었는지 확인할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48e4a-201">You can also verify that the batch has started by running the following command:</span></span>
  
```
Get-MigrationBatch -Identity IMAPBatch1 | Format-List Status
```

### <a name="step-5-route-your-email-to-office-365"></a><span data-ttu-id="48e4a-202">5단계: Office 365로 전자 메일 라우팅</span><span class="sxs-lookup"><span data-stu-id="48e4a-202">Step 5: Route your email to Office 365</span></span>
<span data-ttu-id="48e4a-203"><a name="BK_Step5"> </a></span><span class="sxs-lookup"><span data-stu-id="48e4a-203"></span></span>

<span data-ttu-id="48e4a-p124">전자 메일 시스템 전자 메일을 제공 하기 위해 위치 결정 하는 MX 레코드를 호출 하는 DNS 레코드를 사용 합니다. 전자 메일 마이그레이션 프로세스 중 MX 레코드 원본 전자 메일 시스템을 가리키는 되었습니다. 이제 Office 365로 전자 메일 마이그레이션 완료 되 면 Office 365에서 MX 레코드를 가리키도록 시간입니다. 이렇게 하면 전자 메일이 Office 365 사서함으로 배달 되었는지 확인 합니다. MX 레코드를 이동 하 여 해제할 수 있습니다 또한 오래 된 전자 메일 시스템 준비 되 면 합니다.</span><span class="sxs-lookup"><span data-stu-id="48e4a-p124">Email systems use a DNS record called an MX record to figure out where to deliver emails. During the email migration process, your MX record was pointing to your source email system. Now that the email migration to Office 365 is complete, it's time to point your MX record at Office 365. This helps make sure that email is delivered to your Office 365 mailboxes. By moving the MX record, you can also turn off your old email system when you're ready.</span></span> 
  
<span data-ttu-id="48e4a-p125">대부분의 DNS 공급자에 대 한 구체적인 지침은 [MX 레코드를 변경할](https://go.microsoft.com/fwlink/p/?LinkId=279163)수 있습니다. DNS 공급자 포함 되어있지는 또는 표시 되는 일반 지침의 알려면 하려는 경우 [MX 레코드는 일반적인 지침](https://go.microsoft.com/fwlink/?LinkId=397449) 도 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="48e4a-p125">For many DNS providers, there are specific instructions to [change your MX record](https://go.microsoft.com/fwlink/p/?LinkId=279163). If your DNS provider isn't included, or if you want to get a sense of the general directions, [general MX record instructions ](https://go.microsoft.com/fwlink/?LinkId=397449) are provided as well.</span></span>
  
<span data-ttu-id="48e4a-p126">고객 및 파트너의 전자 메일 시스템에서 변경된 MX 레코드를 인식하는 데는 최대 72시간이 걸릴 수 있습니다. 다음 작업을 계속 진행하기 전에 적어도 72시간 동안 기다립니다. 6단계: IMAP 마이그레이션 일괄 처리 삭제</span><span class="sxs-lookup"><span data-stu-id="48e4a-p126">It can take up to 72 hours for the email systems of your customers and partners to recognize the changed MX record. Wait at least 72 hours before you proceed to the next task: Step 6: Delete IMAP migration batch.</span></span> 
  
### <a name="step-6-delete-imap-migration-batch"></a><span data-ttu-id="48e4a-213">6단계: IMAP 마이그레이션 일괄 처리 삭제</span><span class="sxs-lookup"><span data-stu-id="48e4a-213">Step 6: Delete IMAP migration batch</span></span>
<span data-ttu-id="48e4a-214"><a name="BK_Step6"> </a></span><span class="sxs-lookup"><span data-stu-id="48e4a-214"></span></span>

<span data-ttu-id="48e4a-p127">MX 레코드를 변경 하 고 모든 전자 메일이 Office 365 사서함으로 라우팅되는 확인 한 후 Office 365의 메일 될 사용자를 게 알립니다. 그런 다음, IMAP 마이그레이션 일괄 처리를 삭제할 수 있습니다. 마이그레이션 일괄 처리를 삭제 하기 전에 다음을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="48e4a-p127">After you change the MX record and verify that all email is being routed to Office 365 mailboxes, notify the users that their mail is going to Office 365. After this, you can delete the IMAP migration batch. Verify the following before you delete the migration batch.</span></span>
  
- <span data-ttu-id="48e4a-p128">모든 사용자에 게 Office 365 사서함을 사용 중입니다. 일괄 처리 삭제 된 후 해당 하는 Office 365 사서함 온-프레미스 Exchange 서버에 있는 사서함으로 보낸 메일 복사 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="48e4a-p128">All users are using Office 365 mailboxes. After the batch is deleted, mail sent to mailboxes on the on-premises Exchange Server isn't copied to the corresponding Office 365 mailboxes.</span></span>
    
- <span data-ttu-id="48e4a-p129">Office 365 사서함 메일에 직접 전송 되 고 시작 된 후 최소한 한번 동기화 했습니다. 이 작업을 수행 하려면 마이그레이션 일괄 처리에 대 한 마지막 동기화 시간 상자에 값 Office 365 사서함으로 직접 라우팅되는 메일을 시작 하는 경우 보다 최신 인지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="48e4a-p129">Office 365 mailboxes were synchronized at least once after mail began being sent directly to them. To do this, make sure that the value in the Last Synced Time box for the migration batch is more recent than when mail started being routed directly to Office 365 mailboxes.</span></span>
    
<span data-ttu-id="48e4a-222">Exchange Online PowerShell에서 "IMAPBatch1" 마이그레이션 일괄 처리를 삭제하려면 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="48e4a-222">To delete the "IMAPBatch1" migration batch from Exchange Online PowerShell, run the following command:</span></span>
  
```
Remove-MigrationBatch -Identity IMAPBatch1
```

<span data-ttu-id="48e4a-223">**Remove-migrationbatch** cmdlet에 대 한 자세한 내용은[Remove-migrationbatch](https://go.microsoft.com/fwlink/p/?LinkId=536481)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="48e4a-223">For more information about the **Remove-MigrationBatch** cmdlet, see[Remove-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536481).</span></span>
  
#### <a name="verify-it-worked"></a><span data-ttu-id="48e4a-224">작동하는지 확인</span><span class="sxs-lookup"><span data-stu-id="48e4a-224">Verify it worked</span></span>

<span data-ttu-id="48e4a-225">Exchange Online PowerShell에서 다음 명령을 실행하여 "IMAPBatch1"에 대한 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="48e4a-225">Run the following command in Exchange Online PowerShell to display information about the "IMAPBatch1":</span></span>
  
```
Get-MigrationBatch IMAPBatch1"
```

<span data-ttu-id="48e4a-226">이 명령은 **제거**상태와 마이그레이션 일괄 반환 됩니다 또는 해당 마이그레이션 일괄 처리를 찾을 수 없는 되었다는, 일괄 처리가 삭제 되었는지 확인 하면 오류가 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="48e4a-226">The command will return either the migration batch with a status of **Removing**, or it will return an error stating that migration batch couldn't be found, verifying that the batch was deleted.</span></span>
  
<span data-ttu-id="48e4a-227">**Get-migrationbatch** cmdlet에 대 한 자세한 내용은[Get-migrationbatch](https://go.microsoft.com/fwlink/p/?LinkId=536441)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="48e4a-227">For more information about the **Get-MigrationBatch** cmdlet, see[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="48e4a-228">See also</span><span class="sxs-lookup"><span data-stu-id="48e4a-228">See also</span></span>

#### 

[<span data-ttu-id="48e4a-229">IMAP 마이그레이션 문제 해결사</span><span class="sxs-lookup"><span data-stu-id="48e4a-229">IMAP Migration Troubleshooter</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536482)

