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
# <a name="use-powershell-to-perform-a-cutover-migration-to-office-365"></a><span data-ttu-id="00003-103">PowerShell을 사용하여 Office 365로 단독형 마이그레이션 수행</span><span class="sxs-lookup"><span data-stu-id="00003-103">Use PowerShell to perform a cutover migration to Office 365</span></span>

 <span data-ttu-id="00003-104">**요약:** Office 365에 단독형 마이그레이션을 수행 하기 위해 Windows PowerShell을 사용 하는 방법에 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="00003-104">**Summary:** Learn how to use Windows PowerShell to perform a cutover migration to Office 365.</span></span>
  
<span data-ttu-id="00003-p101">마이그레이션할 수 사용자 사서함의 내용을 원본 전자 메일 시스템에서 Office 365로 동시에 모두 단독형 마이그레이션을 사용 하 여 합니다. 이 문서에서는 Exchange Online PowerShell을 사용 하 여 전자 메일 단독형 마이그레이션에 대 한 작업을 통해 안내 합니다.</span><span class="sxs-lookup"><span data-stu-id="00003-p101">You can migrate the contents of user mailboxes from a source email system to Office 365 all at once by using a cutover migration. This article walks you through the tasks for an email cutover migration by using Exchange Online PowerShell.</span></span> 
  
<span data-ttu-id="00003-p102">[Office 365에 단독 전자 메일 마이그레이션에 대해 알고 하는데 필요한](https://go.microsoft.com/fwlink/p/?LinkId=536688)항목을 검토 하 여 마이그레이션 프로세스의 개요를 얻을 수 있습니다. 해당 문서의 내용을 사용 하 여 능숙 하 게를 사용 하 여이 하나를 시작 하려면 다른 하나의 전자 메일 시스템에서 사서함 마이그레이션입니다.</span><span class="sxs-lookup"><span data-stu-id="00003-p102">By reviewing the topic, [What you need to know about a cutover email migration to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536688), you can get an overview of the migration process. When you're comfortable with the contents of that article, use this one to begin migrating mailboxes from one email system to another.</span></span>
  
> [!NOTE]
> <span data-ttu-id="00003-p103">단독형 마이그레이션을 수행 하기 위해 Exchange 관리 센터를 사용할 수도 있습니다. [전자 메일을 Office 365의 단독형 마이그레이션을 수행](https://go.microsoft.com/fwlink/p/?LinkId=536689)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="00003-p103">You can also use the Exchange admin center to perform a cutover migration. See [Perform a cutover migration of email to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536689).</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="00003-111">시작하기 전에 알아야 할 내용</span><span class="sxs-lookup"><span data-stu-id="00003-111">What do you need to know before you begin?</span></span>

<span data-ttu-id="00003-p104">예상이 작업을 완료 시간: 2 ~ 5 분 마이그레이션 일괄 처리를 만듭니다. 마이그레이션 일괄 처리 시작 되 면 마이그레이션 기간에 따라 달라 집니다 일괄 처리의 사서함 수, 사용 가능한 네트워크 용량 및 각 사서함의 크기입니다. Office 365로 사서함 마이그레이션에 걸리는 시간에 영향을 주는 다른 요인에 대 한 정보를 [마이그레이션 성능](https://go.microsoft.com/fwlink/p/?LinkId=275079)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="00003-p104">Estimated time to complete this task: 2-5 minutes to create a migration batch. After the migration batch is started, the duration of the migration will vary based on the number of mailboxes in the batch, the size of each mailbox, and your available network capacity. For information about other factors that affect how long it takes to migrate mailboxes to Office 365, see [Migration Performance](https://go.microsoft.com/fwlink/p/?LinkId=275079).</span></span>
  
<span data-ttu-id="00003-p105">이 절차를 수행 하기 전에 사용 권한을 할당 해야 합니다. 필요한 사용 권한을 [받는 사람에 게 사용 권한](https://go.microsoft.com/fwlink/p/?LinkId=534105) 항목의 테이블의 "마이그레이션" 항목을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="00003-p105">You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Migration" entry in a table in the [Recipients Permissions](https://go.microsoft.com/fwlink/p/?LinkId=534105) topic.</span></span>
  
<span data-ttu-id="00003-p106">Exchange Online PowerShell cmdlet을 사용 하려면 로그인 하 고 로컬 Windows PowerShell 세션으로 cmdlet을 가져올 해야 합니다. 지침에 대 한 [원격 PowerShell을 사용 하는 Exchange Online에 연결](https://go.microsoft.com/fwlink/p/?LinkId=534121) 을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="00003-p106">To use the Exchange Online PowerShell cmdlets, you need to sign in and import the cmdlets into your local Windows PowerShell session. See [Connect to Exchange Online using remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121) for instructions.</span></span>
  
<span data-ttu-id="00003-119">마이그레이션 명령 목록이 전체 [이동 및 마이그레이션 cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=534750)을 참고 하십시오.</span><span class="sxs-lookup"><span data-stu-id="00003-119">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
  
## <a name="migration-steps"></a><span data-ttu-id="00003-120">마이그레이션 단계</span><span class="sxs-lookup"><span data-stu-id="00003-120">Migration steps</span></span>

### <a name="step-1-prepare-for-a-cutover-migration"></a><span data-ttu-id="00003-121">1단계: 단독형 마이그레이션 준비</span><span class="sxs-lookup"><span data-stu-id="00003-121">Step 1: Prepare for a cutover migration</span></span>
<span data-ttu-id="00003-122"><a name="BK_Step1"> </a></span><span class="sxs-lookup"><span data-stu-id="00003-122"></span></span>

- <span data-ttu-id="00003-p107">**온-프레미스 Exchange 조직 하 여 Office 365 조직의 허용된 도메인으로 추가 합니다.** 마이그레이션 서비스 온-프레미스 사서함의 SMTP 주소를 사용 하 여 새 Office 365 사서함에 대 한 Microsoft 온라인 서비스 사용자 ID와 전자 메일 주소를 만듭니다. 허용된 도메인 또는 Office 365 조직의 주 도메인 Exchange 도메인 없으면 마이그레이션 실패 합니다. 자세한 내용은[Office 365에서 도메인을 확인 합니다.](https://go.microsoft.com/fwlink/p/?LinkId=534110)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="00003-p107">**Add your on-premises Exchange organization as an accepted domain of your Office 365 organization.** The migration service uses the SMTP address of your on-premises mailboxes to create the Microsoft Online Services user ID and email address for the new Office 365 mailboxes. Migration will fail if your Exchange domain isn't an accepted domain or the primary domain of your Office 365 organization. For more information, see[Verify your domain in Office 365](https://go.microsoft.com/fwlink/p/?LinkId=534110).</span></span>
    
- <span data-ttu-id="00003-p108">**외부에서 Outlook 구성 온-프레미스 Exchange 서버에서.** 전자 메일 마이그레이션 서비스를 사용 하 여 RPC over HTTP를 또는 외부에서 Outlook 사용, 온-프레미스 Exchange 서버에 연결 합니다. 다음 Exchange 2010, Exchange 2007 및 Exchange 2003, 참조에 대 한 외부에서 Outlook 사용을 설정 하는 방법에 대 한 내용은 합니다.</span><span class="sxs-lookup"><span data-stu-id="00003-p108">**Configure Outlook Anywhere on your on-premises Exchange server.** The email migration service uses RPC over HTTP, or Outlook Anywhere, to connect to your on-premises Exchange server. For information about how to set up Outlook Anywhere for Exchange 2010, Exchange 2007, and Exchange 2003, see the following:</span></span>
    
  - [<span data-ttu-id="00003-130">Exchange 2010: Outlook Anywhere 사용</span><span class="sxs-lookup"><span data-stu-id="00003-130">Exchange 2010: Enable Outlook Anywhere</span></span>](https://go.microsoft.com/fwlink/?LinkID=187249)
    
  - [<span data-ttu-id="00003-131">Exchange 2007: Outlook Anywhere 사용 하는 방법</span><span class="sxs-lookup"><span data-stu-id="00003-131">Exchange 2007: How to Enable Outlook Anywhere</span></span>](https://go.microsoft.com/fwlink/?LinkID=167210)
    
  - [<span data-ttu-id="00003-132">Exchange 2003: RPC over HTTP 배포 시나리오</span><span class="sxs-lookup"><span data-stu-id="00003-132">Exchange 2003: Deployment Scenarios for RPC over HTTP</span></span>](https://go.microsoft.com/fwlink/?LinkID=73657)
    
  - [<span data-ttu-id="00003-133">Exchange 2003과 함께 외부에서 Outlook을 구성 하는 방법</span><span class="sxs-lookup"><span data-stu-id="00003-133">How to Configure Outlook Anywhere with Exchange 2003</span></span>](https://go.microsoft.com/fwlink/?LinkID=167209)
    
    > [!IMPORTANT]
    > <span data-ttu-id="00003-p109">외부에서 Outlook 사용 구성에는 신뢰할 수 있는 CA (인증 기관)에서 발급 한 인증서로 구성 되어야 합니다. 자체 서명 된 인증서를 사용 하 여 구성할 수 없습니다. 자세한 내용은 [외부에서 Outlook 사용에 대 한 SSL을 구성 하는 방법](https://go.microsoft.com/fwlink/?LinkID=80875)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="00003-p109">Your Outlook Anywhere configuration must be configured with a certificate issued by a trusted certification authority (CA). It can't be configured with a self-signed certificate. For more information, see [How to Configure SSL for Outlook Anywhere](https://go.microsoft.com/fwlink/?LinkID=80875).</span></span> 
  
- <span data-ttu-id="00003-p110">**외부에서 Outlook 사용을 사용 하 여 Exchange 조직에 연결할 수 있는지 확인 합니다.** 연결 설정을 테스트 하려면 다음이 방법 중 하나를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="00003-p110">**Verify that you can connect to your Exchange organization using Outlook Anywhere.** Try one of these methods to test your connection settings:</span></span>
    
  - <span data-ttu-id="00003-139">회사 네트워크 외부에서 Microsoft Outlook을 사용하여 온-프레미스 Exchange 사서함에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="00003-139">Use Microsoft Outlook from outside your corporate network to connect to your on-premises Exchange mailbox.</span></span>
    
  - <span data-ttu-id="00003-p111">Microsoft [Exchange 원격 연결 분석기](https://www.testexchangeconnectivity.com/) 를 사용 하 여 연결 설정을 테스트해봅니다. 외부에서 Outlook 사용 (RPC over HTTP)를 사용 하 여 또는 Outlook 자동 검색을 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="00003-p111">Use the Microsoft [Exchange Remote Connectivity Analyzer](https://www.testexchangeconnectivity.com/) to test your connection settings. Use the Outlook Anywhere (RPC over HTTP) or Outlook Autodiscover tests.</span></span>
    
  - <span data-ttu-id="00003-142">Exchange Online PowerShell에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="00003-142">Run the following commands in Exchange Online PowerShell.</span></span>
    
  ```
  $Credentials = Get-Credential
  ```

  ```
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

- <span data-ttu-id="00003-p112">**온-프레미스 사용자 계정을 Exchange 조직에서 사서함에 액세스 하는 데 필요한 사용 권한을 할당 합니다.** (Themigration 관리자 라고도 함) 하 여 온-프레미스 Exchange 조직에 연결을 사용 하는 온-프레미스 사용자 계정에는 Office 365로 마이그레이션할 수 있는 온-프레미스 사서함에 액세스 하는 데 필요한 권한이 있어야 합니다. 이 사용자 계정은 온-프레미스 조직으로 마이그레이션 끝점을 만드는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="00003-p112">**Assign an on-premises user account the necessary permissions to access mailboxes in your Exchange organization.** The on-premises user account that you use to connect to your on-premises Exchange organization (also called themigration administrator) must have the necessary permissions to access the on-premises mailboxes that you want to migrate to Office 365. This user account is used to create a migration endpoint to your on-premises organization.</span></span>
    
    <span data-ttu-id="00003-p113">다음 목록에는 단독형 마이그레이션을 사용하여 사서함을 마이그레이션하는 데 필요한 관리 권한이 나와 있으며, 세 개의 옵션이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="00003-p113">The following list shows the administrative privileges required to migrate mailboxes using a cutover migration. There are three possible options.</span></span>
    
  - <span data-ttu-id="00003-148">마이그레이션 관리자에 게 온-프레미스 조직에서 Active Directory의 **Domain Admins** 그룹의 구성원 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="00003-148">The migration administrator must be a member of the **Domain Admins** group in Active Directory in the on-premises organization.</span></span>
    
    <span data-ttu-id="00003-149">또는</span><span class="sxs-lookup"><span data-stu-id="00003-149">Or</span></span>
    
  - <span data-ttu-id="00003-150">마이그레이션 관리자에 게 각 온-프레미스 사서함에 대 한 **FullAccess** 권한이 할당 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="00003-150">The migration administrator must be assigned the **FullAccess** permission for each on-premises mailbox.</span></span>
    
    <span data-ttu-id="00003-151">또는</span><span class="sxs-lookup"><span data-stu-id="00003-151">Or</span></span>
    
  - <span data-ttu-id="00003-152">마이그레이션 관리자에 게 사용자 사서함을 저장 하는 온-프레미스 사서함 데이터베이스에서 다음 **으로 받기** 권한이 할당 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="00003-152">The migration administrator must be assigned the **Receive As** permission on the on-premises mailbox database that stores the user mailboxes.</span></span>
    
- <span data-ttu-id="00003-p114">**통합 메시징 사용 안함.** 마이그레이션하는 온-프레미스 사서함에 대 한 UM (통합 메시징)을 사용 하는 경우 해당 마이그레이션하기 전에 UM 사서함에서 사용 하지 않도록 설정 해야 합니다. 마이그레이션이 완료 된 후에 다음 사서함에서 UM을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00003-p114">**Disable Unified Messaging.** If the on-premises mailboxes you're migrating are enabled for Unified Messaging (UM), you have to disable UM on the mailboxes before you migrate them. You can then enable UM on the mailboxes after the migration is complete.</span></span>
    
- <span data-ttu-id="00003-p115">**보안 그룹 및 대리인** 전자 메일 마이그레이션 서비스 Office 365의 보안 그룹으로 마이그레이션된 모든 그룹을 프로 비전 수 없는 것 되므로 여부, 온-프레미스 Active Directory 그룹은 보안 그룹 있는지 여부를 검색할 수 없습니다. Office 365 테 넌 트의 보안 그룹을 사용할 경우 단독형 마이그레이션을 시작 하기 전에 Office 365 테 넌 트에 빈 메일 사용이 가능한 보안 그룹을 먼저 구축 해야 있습니다. 또한이 마이그레이션 방법은 사서함, 메일 사용자, 메일 연락처 및 메일 사용이 가능한 그룹에만 이동합니다. Office 365로 마이그레이션되지 않는 사용자와 같은 다른 Active Directory 개체, 관리자 또는 마이그레이션되는 개체에 대 한 대리인으로 할당 되 면 제거 해야 개체에서 마이그레이션하기 전에 합니다.</span><span class="sxs-lookup"><span data-stu-id="00003-p115">**Security Groups and Delegates** The email migration service cannot detect whether on-premises Active Directory groups are security groups or not, so it cannot provision any migrated groups as security groups in Office 365. If you want to have security groups in your Office 365 tenant, you must first provision an empty mail-enabled security group in your Office 365 tenant before starting the cutover migration. Additionally, this migration method only moves mailboxes, mail users, mail contacts, and mail-enabled groups. If any other Active Directory object, such as user that is not migrated to Office 365, is assigned as a manager or delegate to an object being migrated, they must be removed from the object before you migrate.</span></span>
    
### <a name="step-2-create-a-migration-endpoint"></a><span data-ttu-id="00003-160">2단계: 마이그레이션 끝점 만들기</span><span class="sxs-lookup"><span data-stu-id="00003-160">Step 2: Create a migration endpoint</span></span>
<span data-ttu-id="00003-161"><a name="BK_Step2"> </a></span><span class="sxs-lookup"><span data-stu-id="00003-161"></span></span>

<span data-ttu-id="00003-p116">전자 메일을 성공적으로 마이그레이션 Office 365에 연결 하 고 원본 전자 메일 시스템과 통신할 해야 합니다. 이 위해 Office 365 마이그레이션 끝점을 사용 합니다. 외부에서 Outlook 사용 마이그레이션 끝점 첫번째 [Exchange Online에 연결](https://go.microsoft.com/fwlink/p/?LinkId=534121)하는 단독형 마이그레이션에 대 한를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="00003-p116">To migrate email successfully, Office 365 needs to connect and communicate with the source email system. To do this, Office 365 uses a migration endpoint. To create an Outlook Anywhere migration endpoint for cutover migration, first [connect to Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span></span> 
  
<span data-ttu-id="00003-165">마이그레이션 명령 목록이 전체 [이동 및 마이그레이션 cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=534750)을 참고 하십시오.</span><span class="sxs-lookup"><span data-stu-id="00003-165">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
  
<span data-ttu-id="00003-166">Exchange Online PowerShell에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="00003-166">Run the following commands in Exchange Online PowerShell:</span></span>
  
```
$Credentials = Get-Credential
```

<span data-ttu-id="00003-167">이 예제에서는 [테스트 MigrationServerAvailability](https://go.microsoft.com/fwlink/p/?LinkId=534752) cmdlet를 사용 하 여 받기 및 온-프레미스 Exchange 서버에 대 한 연결 설정을 테스트 한 다음 사용 하 여 이러한 연결 설정을 마이그레이션 끝점을 만드는 이라는 "CutoverEndpoint" 합니다.</span><span class="sxs-lookup"><span data-stu-id="00003-167">The example uses the [Test-MigrationServerAvailability](https://go.microsoft.com/fwlink/p/?LinkId=534752) cmdlet to obtain and test the connection settings to the on-premises Exchange server, and then uses those connection settings to create the migration endpoint called "CutoverEndpoint".</span></span>
  
```
$TSMA = Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress administrator@contoso.com -Credentials $credentials
```

```
New-MigrationEndpoint -ExchangeOutlookAnywhere -Name CutoverEndpoint -ConnectionSettings $TSMA.ConnectionSettings
```

> [!NOTE]
> <span data-ttu-id="00003-p117">**New-migrationendpoint** cmdlet은 **-TargetDatabase** 옵션을 사용 하 여 사용 하 여 서비스에 대 한 데이터베이스를 지정 하는데 사용할 수 있습니다. 그렇지 않은 경우 데이터베이스는 임의로 할당에서 Active Directory Federation Services (AD FS) 2.0 사이트는 관리 사서함이 있는 합니다.</span><span class="sxs-lookup"><span data-stu-id="00003-p117">The **New-MigrationEndpoint** cmdlet can be used to specify a database for the service to use by using the **-TargetDatabase** option. Otherwise a database is randomly assigned from the Active Directory Federation Services (AD FS) 2.0 site where the management mailbox is located.</span></span>
  
#### <a name="verify-it-worked"></a><span data-ttu-id="00003-170">작동하는지 확인</span><span class="sxs-lookup"><span data-stu-id="00003-170">Verify it worked</span></span>

<span data-ttu-id="00003-171">Exchange Online PowerShell에서 다음 명령을 실행하여 "CutoverEndpoint" 마이그레이션 끝점에 대한 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="00003-171">In Exchange Online PowerShell, run the following command to display information about the "CutoverEndpoint" migration endpoint:</span></span>
  
```
Get-MigrationEndpoint CutoverEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*

```

### <a name="step-3-create-the-cutover-migration-batch"></a><span data-ttu-id="00003-172">3단계: 단독형 마이그레이션 일괄 처리 만들기</span><span class="sxs-lookup"><span data-stu-id="00003-172">Step 3: Create the cutover migration batch</span></span>
<span data-ttu-id="00003-173"><a name="BK_Step3"> </a></span><span class="sxs-lookup"><span data-stu-id="00003-173"></span></span>

<span data-ttu-id="00003-p118">온라인으로 사용할 수 **New-migrationbatch** cmdlet은 Exchange PowerShell 단독형 마이그레이션 위한 마이그레이션 일괄 처리를 만들 수 있습니다. 마이그레이션 일괄 처리를 만들고 _자동 시작_ 매개 변수를 포함 하 여 자동으로 시작할 수 있습니다. 또는 마이그레이션 일괄 처리를 만들고 수동으로 시작 나중에 **Start-migrationbatch** cmdlet을 사용 하 여 수 있습니다. "CutoverBatch" 이라는 마이그레이션 일괄 처리를 만들고 이전 단계에서 만든 마이그레이션 끝점을 사용 하 여 하는이 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="00003-p118">You can use the **New-MigrationBatch** cmdlet in Exchange Online PowerShell to create a migration batch for a cutover migration. You can create a migration batch and start it automatically by including the _AutoStart_ parameter. Alternatively, you can create the migration batch and then manually start it afterwards by using the **Start-MigrationBatch** cmdlet. This example creates a migration batch called "CutoverBatch" and uses the migration endpoint that was created in the previous step.</span></span>
  
```
New-MigrationBatch -Name CutoverBatch -SourceEndpoint CutoverEndpoint -AutoStart
```

<span data-ttu-id="00003-p119">이 예제에서는 또한 "CutoverBatch" 이라는 마이그레이션 일괄 처리를 만들고 이전 단계에서 만든 마이그레이션 끝점을 사용 하 여 합니다. _자동 시작_ 매개 변수는 포함 되어있지, 마이그레이션 일괄 처리 하기 때문에 마이그레이션 대시보드 또는 **Start-migrationbatch** cmdlet을 사용 하 여 수동으로 시작 합니다. 듯이 하나만 단독형 마이그레이션 일괄 처리를 한번에 존재할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00003-p119">This example also creates a migration batch called "CutoverBatch" and uses the migration endpoint that was created in the previous step. Because the  _AutoStart_ parameter isn't included, the migration batch has to be manually started on the migration dashboard or by using **Start-MigrationBatch** cmdlet. As previously stated, only one cutover migration batch can exist at a time.</span></span>
  
```
New-MigrationBatch -Name CutoverBatch -SourceEndpoint CutoverEndpoint
```

#### <a name="verify-it-worked"></a><span data-ttu-id="00003-181">작동하는지 확인</span><span class="sxs-lookup"><span data-stu-id="00003-181">Verify it worked</span></span>

<span data-ttu-id="00003-182">단독형 마이그레이션을 위한 마이그레이션 일괄 처리를 성공적으로 만들었는지 확인하려면 Exchange Online PowerShell에서 다음 명령을 실행하여 새 마이그레이션 일괄 처리에 대한 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="00003-182">To verify that you've successfully created a migration batch for a cutover migration, run the following command in Exchange Online PowerShell to display information about the new migration batch:</span></span>
  
```
Get-MigrationBatch | Format-List
```

### <a name="step-4-start-the-cutover-migration-batch"></a><span data-ttu-id="00003-183">4단계: 단독형 마이그레이션 일괄 처리 시작</span><span class="sxs-lookup"><span data-stu-id="00003-183">Step 4: Start the cutover migration batch</span></span>
<span data-ttu-id="00003-184"><a name="BK_Step4"> </a></span><span class="sxs-lookup"><span data-stu-id="00003-184"></span></span>

<span data-ttu-id="00003-p120">Exchange Online PowerShell에서 마이그레이션 일괄 처리를 시작하려면 다음 명령을 실행합니다. 그러면 "CutoverBatch"라는 마이그레이션 일괄 처리가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="00003-p120">To start the migration batch in Exchange Online PowerShell, run the following command. This will create a migration batch called "CutoverBatch".</span></span>
  
```
Start-MigrationBatch -Identity CutoverBatch
```

#### <a name="verify-it-worked"></a><span data-ttu-id="00003-187">작동하는지 확인</span><span class="sxs-lookup"><span data-stu-id="00003-187">Verify it worked</span></span>

<span data-ttu-id="00003-p121">마이그레이션 일괄 처리가 정상적으로 시작된 경우 마이그레이션 대시보드에서 해당 상태가 동기화 중으로 지정됩니다. Exchange Online PowerShell을 사용하여 마이그레이션 일괄 처리를 성공적으로 시작했는지 확인하려면 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="00003-p121">If a migration batch is successfully started, its status on the migration dashboard is specified as Syncing. To verify that you've successfully started a migration batch using Exchange Online PowerShell, run the following command:</span></span>
  
```
Get-MigrationBatch -Identity CutoverBatch |  Format-List Status
```

### <a name="step-5-route-your-email-to-office-365"></a><span data-ttu-id="00003-190">5단계: Office 365로 전자 메일 라우팅</span><span class="sxs-lookup"><span data-stu-id="00003-190">Step 5: Route your email to Office 365</span></span>
<span data-ttu-id="00003-191"><a name="BK_Step5"> </a></span><span class="sxs-lookup"><span data-stu-id="00003-191"></span></span>

<span data-ttu-id="00003-p122">전자 메일 시스템 전자 메일을 제공 하기 위해 위치 결정 하는 MX 레코드를 호출 하는 DNS 레코드를 사용 합니다. 전자 메일 마이그레이션 프로세스 중 MX 레코드 원본 전자 메일 시스템을 가리키는 되었습니다. 이제 Office 365로 전자 메일 마이그레이션 완료 되 면 Office 365에서 MX 레코드를 가리키도록 시간입니다. 이렇게 하면 전자 메일이 Office 365 사서함으로 배달 되었는지 확인 합니다. MX 레코드를 이동 하 여 수도 준비 되 면 오래 된 전자 메일 시스템을 해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="00003-p122">Email systems use a DNS record called an MX record to figure out where to deliver emails. During the email migration process, your MX record was pointing to your source email system. Now that the email migration to Office 365 is complete, it's time to point your MX record at Office 365. This helps make sure that email is delivered to your Office 365 mailboxes. By moving the MX record, you can also you turn off your old email system when you're ready.</span></span> 
  
<span data-ttu-id="00003-p123">대부분의 DNS 공급자에 대 한 구체적인 지침은 [MX 레코드를 변경할](https://go.microsoft.com/fwlink/p/?LinkId=279163)수 있습니다. DNS 공급자 포함 되어있지는 또는 표시 되는 일반 지침의 알려면 하려는 경우 [MX 레코드는 일반적인 지침](https://go.microsoft.com/fwlink/?LinkId=397449) 도 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="00003-p123">For many DNS providers, there are specific instructions to [change your MX record](https://go.microsoft.com/fwlink/p/?LinkId=279163). If your DNS provider isn't included, or if you want to get a sense of the general directions, [general MX record instructions ](https://go.microsoft.com/fwlink/?LinkId=397449) are provided as well.</span></span>
  
<span data-ttu-id="00003-p124">변경 된 MX 레코드를 인식 하도록 고객 및 파트너의 전자 메일 시스템에 대 한 72 시간까지 걸릴 수 있습니다. 다음 작업을 계속 진행 하기 전에 72 시간 이상 대기: [6 단계: 단독형 마이그레이션 일괄 처리 삭제](use-powershell-to-perform-a-cutover-migration-to-office-365.md#Bk_step6)합니다.</span><span class="sxs-lookup"><span data-stu-id="00003-p124">It can take up to 72 hours for the email systems of your customers and partners to recognize the changed MX record. Wait at least 72 hours before you proceed to the next task: [Step 6: Delete the cutover migration batch](use-powershell-to-perform-a-cutover-migration-to-office-365.md#Bk_step6).</span></span> 
  
### <a name="step-6-delete-the-cutover-migration-batch"></a><span data-ttu-id="00003-201">6단계: 단독형 마이그레이션 일괄 처리 삭제</span><span class="sxs-lookup"><span data-stu-id="00003-201">Step 6: Delete the cutover migration batch</span></span>
<span data-ttu-id="00003-202"><a name="Bk_step6"> </a></span><span class="sxs-lookup"><span data-stu-id="00003-202"></span></span>

<span data-ttu-id="00003-p125">MX 레코드를 변경 하 고 모든 전자 메일이 Office 365 사서함으로 라우팅되는 확인 한 후 Office 365의 메일 될 사용자를 게 알립니다. 그런 다음, 단독형 마이그레이션 일괄 처리를 삭제할 수 있습니다. 마이그레이션 일괄 처리를 삭제 하기 전에 다음을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="00003-p125">After you change the MX record and verify that all email is being routed to Office 365 mailboxes, notify the users that their mail is going to Office 365. After this, you can delete the cutover migration batch. Verify the following before you delete the migration batch.</span></span>
  
- <span data-ttu-id="00003-p126">모든 사용자에 게 Office 365 사서함을 사용 중입니다. 일괄 처리 삭제 된 후 해당 하는 Office 365 사서함 온-프레미스 Exchange 서버에 있는 사서함으로 보낸 메일 복사 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="00003-p126">All users are using Office 365 mailboxes. After the batch is deleted, mail sent to mailboxes on the on-premises Exchange Server isn't copied to the corresponding Office 365 mailboxes.</span></span>
    
- <span data-ttu-id="00003-p127">Office 365 사서함 메일에 직접 전송 되 고 시작 된 후 최소한 한번 동기화 했습니다. 이 작업을 수행 하려면 마이그레이션 일괄 처리에 대 한 마지막 동기화 시간 상자에 값 Office 365 사서함으로 직접 라우팅되는 메일을 시작 하는 경우 보다 최신 인지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="00003-p127">Office 365 mailboxes were synchronized at least once after mail began being sent directly to them. To do this, make sure that the value in the Last Synced Time box for the migration batch is more recent than when mail started being routed directly to Office 365 mailboxes.</span></span>
    
<span data-ttu-id="00003-210">Exchange Online PowerShell에서 "CutoverBatch" 마이그레이션 일괄 처리를 삭제하려면 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="00003-210">To delete the "CutoverBatch" migration batch in Exchange Online PowerShell, run the following command:</span></span>
  
```
Remove-MigrationBatch -Identity CutoverBatch
```

### <a name="section-7-assign-user-licenses"></a><span data-ttu-id="00003-211">섹션 7: 사용자 라이선스 할당</span><span class="sxs-lookup"><span data-stu-id="00003-211">Section 7: Assign user licenses</span></span>
<span data-ttu-id="00003-212"><a name="BK_Step7"> </a></span><span class="sxs-lookup"><span data-stu-id="00003-212"></span></span>

 <span data-ttu-id="00003-p128">**활성화 Office 365 사용자 라이선스를 할당 하 여 마이그레이션된 계정에 대 한 계정.** 라이선스를 할당 하지 않은 경우 (30 일)이 유예 기간이 끝날 때 사서함 비활성화 됩니다. Office 365 관리 센터에서 라이선스를 할당 하려면[할당 또는 비즈니스를 위한 Office 365에 대 한 라이선스를 할당 취소 하려면](https://go.microsoft.com/fwlink/?LinkId=536681)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="00003-p128">**Activate Office 365 user accounts for the migrated accounts by assigning licenses.** If you don't assign a license, the mailbox is disabled when the grace period ends (30 days). To assign a license in the Office 365 admin center, see[Assign or unassign licenses for Office 365 for business](https://go.microsoft.com/fwlink/?LinkId=536681).</span></span>
  
### <a name="step-8-complete-post-migration-tasks"></a><span data-ttu-id="00003-216">8단계: 마이그레이션 후 작업 완료</span><span class="sxs-lookup"><span data-stu-id="00003-216">Step 8: Complete post-migration tasks</span></span>
<span data-ttu-id="00003-217"><a name="BK_Step8"> </a></span><span class="sxs-lookup"><span data-stu-id="00003-217"></span></span>

- <span data-ttu-id="00003-p129">**사용자가 자신의 사서함에 쉽게 액세스할 수 있도록 하는 자동 검색 DNS 레코드를 만듭니다.** 모든 온-프레미스 사서함을 Office 365로 마이그레이션된 후에 사용자가 쉽게 Outlook 및 모바일 클라이언트와 함께 새로운 Office 365 사서함에 연결할 수 있도록 하 여 Office 365 조직에 대 한 자동 검색 DNS 레코드를 구성할 수 있습니다. Office 365 조직에 대해 사용 중인 동일한 네임 스페이스를 사용 하 여이 새 자동 검색 DNS 레코드에 있습니다. 클라우드 기반 네임 스페이스 cloud.contoso.com 있으면 만들어야 하는 자동 검색 DNS 레코드는, autodiscover.cloud.contoso.com 합니다.</span><span class="sxs-lookup"><span data-stu-id="00003-p129">**Create an Autodiscover DNS record so users can easily get to their mailboxes.** After all on-premises mailboxes are migrated to Office 365, you can configure an Autodiscover DNS record for your Office 365 organization to enable users to easily connect to their new Office 365 mailboxes with Outlook and mobile clients. This new Autodiscover DNS record has to use the same namespace that you're using for your Office 365 organization. For example, if your cloud-based namespace is cloud.contoso.com, the Autodiscover DNS record you need to create is autodiscover.cloud.contoso.com.</span></span>
    
    <span data-ttu-id="00003-222">Exchange 서버를 유지 하는 경우 자동 검색 DNS CNAME 레코드를 가리키도록 내부 및 외부 DNS에서 Office 365는 마이그레이션 후 올바른 사서함에 연결 하 고 Outlook 클라이언트는 되도록에 있는지 확인도 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="00003-222">If you keep your Exchange Server, you should also make sure that Autodiscover DNS CNAME record has to point to Office 365 in both internal and external DNS after the migration so that the Outlook client will to connect to the correct mailbox.</span></span>
    
    > [!NOTE]
    >  <span data-ttu-id="00003-223">Exchange 2007, Exchange 2010 및 Exchange 2013의 설정도 해야 `Set-ClientAccessServer AutodiscoverInternalConnectionURI` 에 `Null`합니다.</span><span class="sxs-lookup"><span data-stu-id="00003-223">In Exchange 2007, Exchange 2010, and Exchange 2013 you should also set `Set-ClientAccessServer AutodiscoverInternalConnectionURI` to `Null`.</span></span> 
  
    <span data-ttu-id="00003-p130">Office 365 CNAME 레코드를 사용 하 여 Outlook과 모바일 클라이언트에 대 한 자동 검색 서비스를 구현 합니다. 자동 검색 CNAME 레코드는 다음 정보를 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="00003-p130">Office 365 uses a CNAME record to implement the Autodiscover service for Outlook and mobile clients. The Autodiscover CNAME record must contain the following information:</span></span>
    
  - <span data-ttu-id="00003-226">**별칭:** 자동 검색</span><span class="sxs-lookup"><span data-stu-id="00003-226">**Alias:** autodiscover</span></span>
    
  - <span data-ttu-id="00003-227">**대상:** autodiscover.outlook.com</span><span class="sxs-lookup"><span data-stu-id="00003-227">**Target:** autodiscover.outlook.com</span></span>
    
    <span data-ttu-id="00003-228">자세한 내용은 [DNS 레코드를 관리 하는 경우 Office 365 용 DNS 레코드 만들기](https://go.microsoft.com/fwlink/p/?LinkId=535028)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="00003-228">For more information, see [Create DNS records for Office 365 when you manage your DNS records](https://go.microsoft.com/fwlink/p/?LinkId=535028).</span></span>
    
- <span data-ttu-id="00003-p131">**온-프레미스 Exchange 서버를 해제 합니다.** 모든 전자 메일이 Office 365 사서함으로 직접 라우팅되는 하 고 더이상 온-프레미스 조직으로 전자 메일 또는 계획이 없는 single sign on (SSO) 솔루션을 구현에 유지 하기 위해 필요를 확인 한 후에 Exchange에서 제거할 수 없습니다 사용자 서버 및 온-프레미스 Exchange 조직 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="00003-p131">**Decommission on-premises Exchange servers.** After you've verified that all email is being routed directly to the Office 365 mailboxes, and you no longer need to maintain your on-premises email organization or don't plan on implementing a single sign-on (SSO) solution, you can uninstall Exchange from your servers and remove your on-premises Exchange organization.</span></span>
    
    <span data-ttu-id="00003-231">자세한 내용은 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="00003-231">For more information, see the following:</span></span>
    
  - [<span data-ttu-id="00003-232">Exchange 2010 수정 또는 제거</span><span class="sxs-lookup"><span data-stu-id="00003-232">Modify or Remove Exchange 2010</span></span>](https://go.microsoft.com/fwlink/?LinkId=217936)
    
  - [<span data-ttu-id="00003-233">Exchange 2007 조직을 제거 하는 방법</span><span class="sxs-lookup"><span data-stu-id="00003-233">How to Remove an Exchange 2007 Organization</span></span>](https://go.microsoft.com/fwlink/?LinkID=100485)
    
  - [<span data-ttu-id="00003-234">Exchange Server 2003을 제거 하는 방법</span><span class="sxs-lookup"><span data-stu-id="00003-234">How to Uninstall Exchange Server 2003</span></span>](https://go.microsoft.com/fwlink/?LinkID=56561)
    

