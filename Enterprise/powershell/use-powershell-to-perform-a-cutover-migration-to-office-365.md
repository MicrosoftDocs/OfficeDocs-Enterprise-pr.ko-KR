---
title: PowerShell을 사용 하 여 Microsoft 365로의 마이그레이션 수행
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
description: '요약: Windows PowerShell을 사용 하 여 Microsoft 365로의 마이그레이션을 수행 하는 방법을 알아봅니다.'
ms.openlocfilehash: 203c041e0bd5fe58d697d074e94b749726bb22bf
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/22/2020
ms.locfileid: "45229854"
---
# <a name="use-powershell-to-perform-a-cutover-migration-to-microsoft-365"></a><span data-ttu-id="1333b-103">PowerShell을 사용 하 여 Microsoft 365로의 마이그레이션 수행</span><span class="sxs-lookup"><span data-stu-id="1333b-103">Use PowerShell to perform a cutover migration to Microsoft 365</span></span>

<span data-ttu-id="1333b-104">*이 문서는 Microsoft 365 Enterprise 및 Office 365 Enterprise에 모두 적용 됩니다.*</span><span class="sxs-lookup"><span data-stu-id="1333b-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="1333b-105">단순 마이그레이션을 사용 하 여 원본 전자 메일 시스템의 사용자 사서함 내용을 한 번에 Microsoft 365로 마이그레이션할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1333b-105">You can migrate the contents of user mailboxes from a source email system to Microsoft 365 all at once by using a cutover migration.</span></span> <span data-ttu-id="1333b-106">이 문서에서는 Exchange Online PowerShell을 사용하는 전자 메일 단독형 마이그레이션 작업을 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="1333b-106">This article walks you through the tasks for an email cutover migration by using Exchange Online PowerShell.</span></span> 
  
<span data-ttu-id="1333b-107">이 항목을 검토 하 여 [Microsoft 365로 전자 메일 마이그레이션에 대해 알아야 할 사항](https://go.microsoft.com/fwlink/p/?LinkId=536688)에 대해 설명 하 고 마이그레이션 프로세스에 대 한 개요를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1333b-107">By reviewing the topic, [What you need to know about a cutover email migration to Microsoft 365](https://go.microsoft.com/fwlink/p/?LinkId=536688), you can get an overview of the migration process.</span></span> <span data-ttu-id="1333b-108">이 문서 내용을 충분히 이해할 수 있으면 다음을 사용하여 다른 전자 메일 시스템으로 사서함을 마이그레이션해 보세요.</span><span class="sxs-lookup"><span data-stu-id="1333b-108">When you're comfortable with the contents of that article, use this one to begin migrating mailboxes from one email system to another.</span></span>
  
> [!NOTE]
> <span data-ttu-id="1333b-109">Exchange 관리 센터를 사용하여 단독형 마이그레이션을 수행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1333b-109">You can also use the Exchange admin center to perform a cutover migration.</span></span> <span data-ttu-id="1333b-110">[Microsoft 365에 전자 메일 마이그레이션](https://go.microsoft.com/fwlink/p/?LinkId=536689)완료를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1333b-110">See [Perform a cutover migration of email to Microsoft 365](https://go.microsoft.com/fwlink/p/?LinkId=536689).</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="1333b-111">시작하기 전에 알아야 할 내용</span><span class="sxs-lookup"><span data-stu-id="1333b-111">What do you need to know before you begin?</span></span>

<span data-ttu-id="1333b-112">이 작업의 예상 완료 시간: 2-5분(마이그레이션 일괄 처리 만들기에 소요되는 시간).</span><span class="sxs-lookup"><span data-stu-id="1333b-112">Estimated time to complete this task: 2-5 minutes to create a migration batch.</span></span> <span data-ttu-id="1333b-113">마이그레이션 일괄 처리가 시작되면 마이그레이션 기간은 일괄 처리의 사서함 수, 각 사서함의 크기 및 사용 가능한 네트워크 용량에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="1333b-113">After the migration batch is started, the duration of the migration will vary based on the number of mailboxes in the batch, the size of each mailbox, and your available network capacity.</span></span> <span data-ttu-id="1333b-114">사서함을 Microsoft 365로 마이그레이션하는 데 걸리는 시간에 영향을 주는 다른 요인에 대 한 자세한 내용은 [마이그레이션 성능을](https://go.microsoft.com/fwlink/p/?LinkId=275079)참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="1333b-114">For information about other factors that affect how long it takes to migrate mailboxes to Microsoft 365, see [Migration Performance](https://go.microsoft.com/fwlink/p/?LinkId=275079).</span></span>
  
<span data-ttu-id="1333b-p105">이 절차를 수행하려면 먼저 사용 권한을 할당받아야 합니다. 필요한 사용 권한을 확인하려면 [받는 사람 사용 권한](https://go.microsoft.com/fwlink/p/?LinkId=534105)의 표에 나오는 "마이그레이션" 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1333b-p105">You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Migration" entry in a table in the [Recipients Permissions](https://go.microsoft.com/fwlink/p/?LinkId=534105) topic.</span></span>
  
<span data-ttu-id="1333b-p106">Exchange Online PowerShell cmdlet을 사용하려면 로그인한 후 cmdlet을 로컬 Windows PowerShell 세션으로 가져와야 합니다. 해당 지침은 [원격 PowerShell을 사용하여 Exchange Online에 연결](https://go.microsoft.com/fwlink/p/?LinkId=534121)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1333b-p106">To use the Exchange Online PowerShell cmdlets, you need to sign in and import the cmdlets into your local Windows PowerShell session. See [Connect to Exchange Online using remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121) for instructions.</span></span>
  
<span data-ttu-id="1333b-119">전체 마이그레이션 명령 목록을 보려면 [이동 및 마이그레이션 cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=534750)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1333b-119">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
  
## <a name="migration-steps"></a><span data-ttu-id="1333b-120">마이그레이션 단계</span><span class="sxs-lookup"><span data-stu-id="1333b-120">Migration steps</span></span>

### <a name="step-1-prepare-for-a-cutover-migration"></a><span data-ttu-id="1333b-121">1단계: 단독형 마이그레이션 준비</span><span class="sxs-lookup"><span data-stu-id="1333b-121">Step 1: Prepare for a cutover migration</span></span>
<span data-ttu-id="1333b-122"><a name="BK_Step1"> </a></span><span class="sxs-lookup"><span data-stu-id="1333b-122"><a name="BK_Step1"> </a></span></span>

- <span data-ttu-id="1333b-123">**온-프레미스 Exchange 조직을 Microsoft 365 조 직의 허용 도메인으로 추가 합니다.**</span><span class="sxs-lookup"><span data-stu-id="1333b-123">**Add your on-premises Exchange organization as an accepted domain of your Microsoft 365 organization.**</span></span> <span data-ttu-id="1333b-124">마이그레이션 서비스는 온-프레미스 사서함의 SMTP 주소를 사용 하 여 새 Microsoft 365 사서함에 대 한 Microsoft Online Services 사용자 ID 및 전자 메일 주소를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1333b-124">The migration service uses the SMTP address of your on-premises mailboxes to create the Microsoft Online Services user ID and email address for the new Microsoft 365 mailboxes.</span></span> <span data-ttu-id="1333b-125">Exchange 도메인이 Microsoft 365 조직의 주 도메인 또는 허용 도메인이 아니면 마이그레이션이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="1333b-125">Migration will fail if your Exchange domain isn't an accepted domain or the primary domain of your Microsoft 365 organization.</span></span> <span data-ttu-id="1333b-126">자세한 내용은 [도메인 확인](https://go.microsoft.com/fwlink/p/?LinkId=534110)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1333b-126">For more information, see [Verify your domain](https://go.microsoft.com/fwlink/p/?LinkId=534110).</span></span>
    
- <span data-ttu-id="1333b-p108">**온-프레미스 Exchange 서버에서 "외부에서 Outlook 사용" 구성** 전자 메일 마이그레이션 서비스에서 RPC over HTTP나 "외부에서 Outlook 사용"을 사용하여 온-프레미스 Exchange 서버에 연결합니다. Exchange 2010, Exchange 2007 및 Exchange 2003용 "외부에서 Outlook 사용"을 설정하는 방법은 다음을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="1333b-p108">**Configure Outlook Anywhere on your on-premises Exchange server.** The email migration service uses RPC over HTTP, or Outlook Anywhere, to connect to your on-premises Exchange server. For information about how to set up Outlook Anywhere for Exchange 2010, Exchange 2007, and Exchange 2003, see the following:</span></span>
    
  - [<span data-ttu-id="1333b-130">Exchange 2010: "외부에서 Outlook 사용" 설정</span><span class="sxs-lookup"><span data-stu-id="1333b-130">Exchange 2010: Enable Outlook Anywhere</span></span>](https://go.microsoft.com/fwlink/?LinkID=187249)
    
  - [<span data-ttu-id="1333b-131">Exchange 2007: 외부에서 Outlook 사용 설정 방법</span><span class="sxs-lookup"><span data-stu-id="1333b-131">Exchange 2007: How to Enable Outlook Anywhere</span></span>](https://go.microsoft.com/fwlink/?LinkID=167210)
    
  - [<span data-ttu-id="1333b-132">Exchange 2003: RPC over HTTP에 대한 배포 시나리오</span><span class="sxs-lookup"><span data-stu-id="1333b-132">Exchange 2003: Deployment Scenarios for RPC over HTTP</span></span>](https://go.microsoft.com/fwlink/?LinkID=73657)
    
  - [<span data-ttu-id="1333b-133">Exchange 2003: "외부에서 Outlook 사용" 구성 방법</span><span class="sxs-lookup"><span data-stu-id="1333b-133">How to Configure Outlook Anywhere with Exchange 2003</span></span>](https://go.microsoft.com/fwlink/?LinkID=167209)
    
    > [!IMPORTANT]
    > <span data-ttu-id="1333b-p109">"외부에서 Outlook 사용"은 신뢰할 수 있는 CA(인증 기관)에서 발급한 인증서를 통해 구성해야 합니다. 자체 서명된 인증서로는 구성할 수 없습니다. 자세한 내용은 ["외부에서 Outlook 사용"에 대한 SSL 구성 방법](https://go.microsoft.com/fwlink/?LinkID=80875)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1333b-p109">Your Outlook Anywhere configuration must be configured with a certificate issued by a trusted certification authority (CA). It can't be configured with a self-signed certificate. For more information, see [How to Configure SSL for Outlook Anywhere](https://go.microsoft.com/fwlink/?LinkID=80875).</span></span> 
  
- <span data-ttu-id="1333b-p110">**Outlook Anywhere를 사용하여 Exchange 조직에 연결할 수 있는지 확인** 다음 방법 중 하나를 사용하여 연결 설정을 테스트해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="1333b-p110">**Verify that you can connect to your Exchange organization using Outlook Anywhere.** Try one of these methods to test your connection settings:</span></span>
    
  - <span data-ttu-id="1333b-139">회사 네트워크 외부에서 Microsoft Outlook을 사용하여 온-프레미스 Exchange 사서함에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="1333b-139">Use Microsoft Outlook from outside your corporate network to connect to your on-premises Exchange mailbox.</span></span>
    
  - <span data-ttu-id="1333b-p111">Microsoft [Exchange Remote Connectivity Analyzer](https://www.testexchangeconnectivity.com/)를 사용하여 연결 설정을 테스트합니다. 외부에서 Outlook 사용(RPC over HTTP)이나 Outlook 자동 검색 테스트를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1333b-p111">Use the Microsoft [Exchange Remote Connectivity Analyzer](https://www.testexchangeconnectivity.com/) to test your connection settings. Use the Outlook Anywhere (RPC over HTTP) or Outlook Autodiscover tests.</span></span>
    
  - <span data-ttu-id="1333b-142">Exchange Online PowerShell에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="1333b-142">Run the following commands in Exchange Online PowerShell.</span></span>
    
  ```
  $Credentials = Get-Credential
  ```

  ```
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

- <span data-ttu-id="1333b-143">**온-프레미스 사용자 계정에 Exchange 조직의 사서함에 액세스하는 데 필요한 사용 권한 할당**</span><span class="sxs-lookup"><span data-stu-id="1333b-143">**Assign an on-premises user account the necessary permissions to access mailboxes in your Exchange organization.**</span></span> <span data-ttu-id="1333b-144">온-프레미스 Exchange 조직 (마이그레이션 관리자 라고도 함)에 연결 하는 데 사용 하는 온-프레미스 사용자 계정에는 Microsoft 365로 마이그레이션할 온-프레미스 사서함에 액세스 하는 데 필요한 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1333b-144">The on-premises user account that you use to connect to your on-premises Exchange organization (also called the migration administrator) must have the necessary permissions to access the on-premises mailboxes that you want to migrate to Microsoft 365.</span></span> <span data-ttu-id="1333b-145">이 사용자 계정은 온-프레미스 조직에 대한 마이그레이션 끝점을 만드는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1333b-145">This user account is used to create a migration endpoint to your on-premises organization.</span></span>
    
    <span data-ttu-id="1333b-p113">다음 목록에는 단독형 마이그레이션을 사용하여 사서함을 마이그레이션하는 데 필요한 관리 권한이 나와 있으며, 세 개의 옵션이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="1333b-p113">The following list shows the administrative privileges required to migrate mailboxes using a cutover migration. There are three possible options.</span></span>
    
  - <span data-ttu-id="1333b-148">마이그레이션 관리자는 온-프레미스 조직의 Active Directory에 있는 **Domain Admins** 그룹의 구성원이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1333b-148">The migration administrator must be a member of the **Domain Admins** group in Active Directory in the on-premises organization.</span></span>
    
    <span data-ttu-id="1333b-149">또는</span><span class="sxs-lookup"><span data-stu-id="1333b-149">Or</span></span>
    
  - <span data-ttu-id="1333b-150">마이그레이션 관리자에게 각 온-프레미스 사서함에 대한 **모든 권한** 권한이 할당되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1333b-150">The migration administrator must be assigned the **FullAccess** permission for each on-premises mailbox.</span></span>
    
    <span data-ttu-id="1333b-151">또는</span><span class="sxs-lookup"><span data-stu-id="1333b-151">Or</span></span>
    
  - <span data-ttu-id="1333b-152">마이그레이션 관리자에게 사용자 사서함을 저장하는 온-프레미스 사서함 데이터베이스에 대한 **다음으로 받기** 권한이 할당되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1333b-152">The migration administrator must be assigned the **Receive As** permission on the on-premises mailbox database that stores the user mailboxes.</span></span>
    
- <span data-ttu-id="1333b-p114">**통합 메시징을 사용하지 않도록 설정** 마이그레이션하려는 온-프레미스 사서함이 UM(통합 메시징)을 사용할 수 있도록 설정된 경우 마이그레이션 전에 사서함에서 UM을 사용하지 않도록 설정해야 합니다. 마이그레이션이 완료된 후 사서함에서 UM을 사용하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1333b-p114">**Disable Unified Messaging.** If the on-premises mailboxes you're migrating are enabled for Unified Messaging (UM), you have to disable UM on the mailboxes before you migrate them. You can then enable UM on the mailboxes after the migration is complete.</span></span>
    
- <span data-ttu-id="1333b-156">**보안 그룹 및 대리인** 전자 메일 마이그레이션 서비스는 온-프레미스 Active Directory 그룹이 보안 그룹 인지 여부를 검색할 수 없으므로 마이그레이션된 그룹을 Microsoft 365의 보안 그룹으로 프로 비전 할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1333b-156">**Security Groups and Delegates** The email migration service cannot detect whether on-premises Active Directory groups are security groups or not, so it cannot provision any migrated groups as security groups in Microsoft 365.</span></span> <span data-ttu-id="1333b-157">Microsoft 365 테 넌 트에 보안 그룹을 포함 하려면 먼저 Microsoft 365 테 넌 트에서 빈 메일 사용 가능 보안 그룹을 프로 비전 한 후에 기본 마이그레이션을 시작 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1333b-157">If you want to have security groups in your Microsoft 365 tenant, you must first provision an empty mail-enabled security group in your Microsoft 365 tenant before starting the cutover migration.</span></span> <span data-ttu-id="1333b-158">또한 이 마이그레이션 방법을 사용하는 경우에는 사서함, 메일 사용자, 메일 연락처 및 메일 사용 가능 그룹만 이동됩니다.</span><span class="sxs-lookup"><span data-stu-id="1333b-158">Additionally, this migration method only moves mailboxes, mail users, mail contacts, and mail-enabled groups.</span></span> <span data-ttu-id="1333b-159">사용자가 Microsoft 365로 마이그레이션되지 않은 다른 Active Directory 개체 (예: 마이그레이션 대상 개체에 관리자 또는 위임)를 할당 한 경우에는 마이그레이션하기 전에 개체에서 제거 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1333b-159">If any other Active Directory object, such as user that is not migrated to Microsoft 365, is assigned as a manager or delegate to an object being migrated, they must be removed from the object before you migrate.</span></span>
    
### <a name="step-2-create-a-migration-endpoint"></a><span data-ttu-id="1333b-160">2단계: 마이그레이션 끝점 만들기</span><span class="sxs-lookup"><span data-stu-id="1333b-160">Step 2: Create a migration endpoint</span></span>
<span data-ttu-id="1333b-161"><a name="BK_Step2"> </a></span><span class="sxs-lookup"><span data-stu-id="1333b-161"><a name="BK_Step2"> </a></span></span>

<span data-ttu-id="1333b-162">전자 메일을 성공적으로 마이그레이션하려면 Microsoft 365에서 원본 전자 메일 시스템과 연결 하 여 통신 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1333b-162">To migrate email successfully, Microsoft 365 needs to connect and communicate with the source email system.</span></span> <span data-ttu-id="1333b-163">이 작업을 수행 하기 위해 Microsoft 365는 마이그레이션 끝점을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1333b-163">To do this, Microsoft 365 uses a migration endpoint.</span></span> <span data-ttu-id="1333b-164">단독형 마이그레이션을 위한 "외부에서 Outlook 사용" 마이그레이션 끝점을 만들려면 먼저 [Exchange Online에 연결](https://go.microsoft.com/fwlink/p/?LinkId=534121)합니다.</span><span class="sxs-lookup"><span data-stu-id="1333b-164">To create an Outlook Anywhere migration endpoint for cutover migration, first [connect to Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span></span> 
  
<span data-ttu-id="1333b-165">전체 마이그레이션 명령 목록을 보려면 [이동 및 마이그레이션 cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=534750)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1333b-165">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
  
<span data-ttu-id="1333b-166">Exchange Online PowerShell에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="1333b-166">Run the following commands in Exchange Online PowerShell:</span></span>
  
```
$Credentials = Get-Credential
```

<span data-ttu-id="1333b-167">이 예에서는 [Test-MigrationServerAvailability](https://go.microsoft.com/fwlink/p/?LinkId=534752) cmdlet을 사용하여 온-프레미스 Exchange 서버에 대한 연결 설정을 가져오고 테스트한 다음 해당 연결 설정을 사용하여 "CutoverEndpoint"라는 마이그레이션 끝점을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1333b-167">The example uses the [Test-MigrationServerAvailability](https://go.microsoft.com/fwlink/p/?LinkId=534752) cmdlet to obtain and test the connection settings to the on-premises Exchange server, and then uses those connection settings to create the migration endpoint called "CutoverEndpoint".</span></span>
  
```
$TSMA = Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress administrator@contoso.com -Credentials $credentials
```

```
New-MigrationEndpoint -ExchangeOutlookAnywhere -Name CutoverEndpoint -ConnectionSettings $TSMA.ConnectionSettings
```

> [!NOTE]
> <span data-ttu-id="1333b-p117">**New-MigrationEndpoint** cmdlet을 사용하여 **-TargetDatabase** 옵션을 통해 서비스에서 사용할 데이터베이스를 지정할 수 있습니다. 그렇지 않으면 데이터베이스는 관리 사서함이 있는 AD FS(Active Directory Federation Services) 2.0 사이트에서 임의로 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="1333b-p117">The **New-MigrationEndpoint** cmdlet can be used to specify a database for the service to use by using the **-TargetDatabase** option. Otherwise a database is randomly assigned from the Active Directory Federation Services (AD FS) 2.0 site where the management mailbox is located.</span></span>
  
#### <a name="verify-it-worked"></a><span data-ttu-id="1333b-170">작동하는지 확인</span><span class="sxs-lookup"><span data-stu-id="1333b-170">Verify it worked</span></span>

<span data-ttu-id="1333b-171">Exchange Online PowerShell에서 다음 명령을 실행하여 "CutoverEndpoint" 마이그레이션 끝점에 대한 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="1333b-171">In Exchange Online PowerShell, run the following command to display information about the "CutoverEndpoint" migration endpoint:</span></span>
  
```
Get-MigrationEndpoint CutoverEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*

```

### <a name="step-3-create-the-cutover-migration-batch"></a><span data-ttu-id="1333b-172">3단계: 단독형 마이그레이션 일괄 처리 만들기</span><span class="sxs-lookup"><span data-stu-id="1333b-172">Step 3: Create the cutover migration batch</span></span>
<span data-ttu-id="1333b-173"><a name="BK_Step3"> </a></span><span class="sxs-lookup"><span data-stu-id="1333b-173"><a name="BK_Step3"> </a></span></span>

<span data-ttu-id="1333b-p118">Exchange Online PowerShell에서 **New-MigrationBatch** cmdlet을 사용하여 단독형 마이그레이션을 위한 마이그레이션 일괄 처리를 만들 수 있습니다. _AutoStart_ 매개 변수를 포함하면 마이그레이션 일괄 처리를 만들고 자동으로 시작할 수 있습니다. 또는 마이그레이션 일괄 처리를 만들고 **Start-MigrationBatch** cmdlet을 사용하여 나중에 마이그레이션을 수동으로 시작할 수 있습니다. 이 예에서는 "CutoverBatch"라는 마이그레이션 일괄 처리를 만든 다음 이전 예에서 만든 마이그레이션 끝점을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1333b-p118">You can use the **New-MigrationBatch** cmdlet in Exchange Online PowerShell to create a migration batch for a cutover migration. You can create a migration batch and start it automatically by including the _AutoStart_ parameter. Alternatively, you can create the migration batch and then manually start it afterwards by using the **Start-MigrationBatch** cmdlet. This example creates a migration batch called "CutoverBatch" and uses the migration endpoint that was created in the previous step.</span></span>
  
```
New-MigrationBatch -Name CutoverBatch -SourceEndpoint CutoverEndpoint -AutoStart
```

<span data-ttu-id="1333b-p119">또한 이 예에서는 "CutoverBatch"라는 마이그레이션 일괄 처리를 만든 다음 이전 예에서 만든 마이그레이션 끝점을 사용합니다.  _AutoStart_ 매개 변수가 포함되지 않으므로 마이그레이션 일괄 처리가 마이그레이션 대시보드나 **Start-MigrationBatch** cmdlet을 사용하여 수동으로 시작되어야 합니다. 앞서 설명했듯이 단독형 마이그레이션 일괄 처리는 한 번에 하나만 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="1333b-p119">This example also creates a migration batch called "CutoverBatch" and uses the migration endpoint that was created in the previous step. Because the  _AutoStart_ parameter isn't included, the migration batch has to be manually started on the migration dashboard or by using **Start-MigrationBatch** cmdlet. As previously stated, only one cutover migration batch can exist at a time.</span></span>
  
```
New-MigrationBatch -Name CutoverBatch -SourceEndpoint CutoverEndpoint
```

#### <a name="verify-it-worked"></a><span data-ttu-id="1333b-181">작동하는지 확인</span><span class="sxs-lookup"><span data-stu-id="1333b-181">Verify it worked</span></span>

<span data-ttu-id="1333b-182">단독형 마이그레이션을 위한 마이그레이션 일괄 처리를 성공적으로 만들었는지 확인하려면 Exchange Online PowerShell에서 다음 명령을 실행하여 새 마이그레이션 일괄 처리에 대한 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="1333b-182">To verify that you've successfully created a migration batch for a cutover migration, run the following command in Exchange Online PowerShell to display information about the new migration batch:</span></span>
  
```
Get-MigrationBatch | Format-List
```

### <a name="step-4-start-the-cutover-migration-batch"></a><span data-ttu-id="1333b-183">4단계: 단독형 마이그레이션 일괄 처리 시작</span><span class="sxs-lookup"><span data-stu-id="1333b-183">Step 4: Start the cutover migration batch</span></span>
<span data-ttu-id="1333b-184"><a name="BK_Step4"> </a></span><span class="sxs-lookup"><span data-stu-id="1333b-184"><a name="BK_Step4"> </a></span></span>

<span data-ttu-id="1333b-p120">Exchange Online PowerShell에서 마이그레이션 일괄 처리를 시작하려면 다음 명령을 실행합니다. 그러면 "CutoverBatch"라는 마이그레이션 일괄 처리가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="1333b-p120">To start the migration batch in Exchange Online PowerShell, run the following command. This will create a migration batch called "CutoverBatch".</span></span>
  
```
Start-MigrationBatch -Identity CutoverBatch
```

#### <a name="verify-it-worked"></a><span data-ttu-id="1333b-187">작동하는지 확인</span><span class="sxs-lookup"><span data-stu-id="1333b-187">Verify it worked</span></span>

<span data-ttu-id="1333b-p121">마이그레이션 일괄 처리가 정상적으로 시작된 경우 마이그레이션 대시보드에서 해당 상태가 동기화 중으로 지정됩니다. Exchange Online PowerShell을 사용하여 마이그레이션 일괄 처리를 성공적으로 시작했는지 확인하려면 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="1333b-p121">If a migration batch is successfully started, its status on the migration dashboard is specified as Syncing. To verify that you've successfully started a migration batch using Exchange Online PowerShell, run the following command:</span></span>
  
```
Get-MigrationBatch -Identity CutoverBatch |  Format-List Status
```

### <a name="step-5-route-your-email-to-microsoft-365"></a><span data-ttu-id="1333b-190">5 단계: Microsoft 365로 전자 메일 라우팅</span><span class="sxs-lookup"><span data-stu-id="1333b-190">Step 5: Route your email to Microsoft 365</span></span>
<span data-ttu-id="1333b-191"><a name="BK_Step5"> </a></span><span class="sxs-lookup"><span data-stu-id="1333b-191"><a name="BK_Step5"> </a></span></span>

<span data-ttu-id="1333b-192">전자 메일 시스템은 MX 레코드라는 DNS 레코드를 사용하여 전자 메일을 배달할 위치를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="1333b-192">Email systems use a DNS record called an MX record to figure out where to deliver emails.</span></span> <span data-ttu-id="1333b-193">전자 메일 마이그레이션 프로세스 중에는 MX 레코드가 원본 전자 메일 시스템을 가리켰습니다.</span><span class="sxs-lookup"><span data-stu-id="1333b-193">During the email migration process, your MX record was pointing to your source email system.</span></span> <span data-ttu-id="1333b-194">Microsoft 365로 전자 메일 마이그레이션이 완료 되었으므로 Microsoft 365에서 MX 레코드를 가리켜야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1333b-194">Now that the email migration to Microsoft 365 is complete, it's time to point your MX record at Microsoft 365.</span></span> <span data-ttu-id="1333b-195">이렇게 하면 전자 메일이 Microsoft 365 사서함으로 배달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1333b-195">This helps make sure that email is delivered to your Microsoft 365 mailboxes.</span></span> <span data-ttu-id="1333b-196">MX 레코드를 이동하여 준비가 되었을 때 이전 전자 메일 시스템을 해제할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1333b-196">By moving the MX record, you can also you turn off your old email system when you're ready.</span></span> 
  
<span data-ttu-id="1333b-p123">DNS 공급자가 많이 있으므로 [MX 레코드를 변경](https://go.microsoft.com/fwlink/p/?LinkId=279163)하기 위한 특정 지침이 제공됩니다. 사용자의 DNS 공급자가 여기에 포함되지 않거나 일반적인 지침을 원하는 경우를 위해 [일반 MX 레코드 지침](https://go.microsoft.com/fwlink/?LinkId=397449)도 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="1333b-p123">For many DNS providers, there are specific instructions to [change your MX record](https://go.microsoft.com/fwlink/p/?LinkId=279163). If your DNS provider isn't included, or if you want to get a sense of the general directions, [general MX record instructions ](https://go.microsoft.com/fwlink/?LinkId=397449) are provided as well.</span></span>
  
<span data-ttu-id="1333b-p124">고객 및 파트너의 전자 메일 시스템에서 변경된 MX 레코드를 인식하는 데는 최대 72시간이 걸릴 수 있습니다. 다음 작업을 계속 진행하기 전에 적어도 72시간 동안 기다립니다. [6단계: 단독형 마이그레이션 일괄 처리 삭제](use-powershell-to-perform-a-cutover-migration-to-office-365.md#Bk_step6).</span><span class="sxs-lookup"><span data-stu-id="1333b-p124">It can take up to 72 hours for the email systems of your customers and partners to recognize the changed MX record. Wait at least 72 hours before you proceed to the next task: [Step 6: Delete the cutover migration batch](use-powershell-to-perform-a-cutover-migration-to-office-365.md#Bk_step6).</span></span> 
  
### <a name="step-6-delete-the-cutover-migration-batch"></a><span data-ttu-id="1333b-201">6단계: 단독형 마이그레이션 일괄 처리 삭제</span><span class="sxs-lookup"><span data-stu-id="1333b-201">Step 6: Delete the cutover migration batch</span></span>
<span data-ttu-id="1333b-202"><a name="Bk_step6"> </a></span><span class="sxs-lookup"><span data-stu-id="1333b-202"><a name="Bk_step6"> </a></span></span>

<span data-ttu-id="1333b-203">MX 레코드를 변경 하 고 모든 전자 메일이 Microsoft 365 사서함으로 라우팅되는 것을 확인 한 후에는 메일이 Microsoft 365로 이동 중임을 사용자에 게 알립니다.</span><span class="sxs-lookup"><span data-stu-id="1333b-203">After you change the MX record and verify that all email is being routed to Microsoft 365 mailboxes, notify the users that their mail is going to Microsoft 365.</span></span> <span data-ttu-id="1333b-204">그런 후에는 단독형 마이그레이션 일괄 처리를 삭제해도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1333b-204">After this, you can delete the cutover migration batch.</span></span> <span data-ttu-id="1333b-205">마이그레이션 일괄 처리를 삭제하기 전에 다음을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="1333b-205">Verify the following before you delete the migration batch.</span></span>
  
- <span data-ttu-id="1333b-206">모든 사용자가 Microsoft 365 사서함을 사용 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1333b-206">All users are using Microsoft 365 mailboxes.</span></span> <span data-ttu-id="1333b-207">일괄 처리가 삭제 된 후에는 온-프레미스 Exchange 서버의 사서함에 전송 된 메일이 해당 Microsoft 365 사서함에 복사 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1333b-207">After the batch is deleted, mail sent to mailboxes on the on-premises Exchange Server isn't copied to the corresponding Microsoft 365 mailboxes.</span></span>
    
- <span data-ttu-id="1333b-208">Microsoft 365 사서함은 메일이 직접 전송 되기 시작한 후에 한 번 이상 동기화 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1333b-208">Microsoft 365 mailboxes were synchronized at least once after mail began being sent directly to them.</span></span> <span data-ttu-id="1333b-209">이렇게 하려면 메일이 Microsoft 365 사서함으로 직접 라우팅되는 시기 보다 마이그레이션 일괄 처리에 대 한 마지막 동기화 시간 상자의 값이 최신 상태 인지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="1333b-209">To do this, make sure that the value in the Last Synced Time box for the migration batch is more recent than when mail started being routed directly to Microsoft 365 mailboxes.</span></span>
    
<span data-ttu-id="1333b-210">Exchange Online PowerShell에서 "CutoverBatch" 마이그레이션 일괄 처리를 삭제하려면 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="1333b-210">To delete the "CutoverBatch" migration batch in Exchange Online PowerShell, run the following command:</span></span>
  
```
Remove-MigrationBatch -Identity CutoverBatch
```

### <a name="section-7-assign-user-licenses"></a><span data-ttu-id="1333b-211">섹션 7: 사용자 라이선스 할당</span><span class="sxs-lookup"><span data-stu-id="1333b-211">Section 7: Assign user licenses</span></span>
<span data-ttu-id="1333b-212"><a name="BK_Step7"> </a></span><span class="sxs-lookup"><span data-stu-id="1333b-212"><a name="BK_Step7"> </a></span></span>

 <span data-ttu-id="1333b-213">**라이선스를 할당 하 여 마이그레이션된 계정에 대해 Microsoft 365 사용자 계정을 정품 인증 합니다.**</span><span class="sxs-lookup"><span data-stu-id="1333b-213">**Activate Microsoft 365 user accounts for the migrated accounts by assigning licenses.**</span></span> <span data-ttu-id="1333b-214">라이선스를 할당하지 않은 경우 30일 유예 기간이 끝나면 사서함을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1333b-214">If you don't assign a license, the mailbox is disabled when the grace period ends (30 days).</span></span> <span data-ttu-id="1333b-215">Microsoft 365 관리 센터에서 라이선스를 할당 하려면 [라이선스 할당 또는](https://docs.microsoft.com/microsoft-365/admin/manage/assign-licenses-to-users)할당 해제를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1333b-215">To assign a license in the Microsoft 365 admin center, see [Assign or unassign licenses](https://docs.microsoft.com/microsoft-365/admin/manage/assign-licenses-to-users).</span></span>
  
### <a name="step-8-complete-post-migration-tasks"></a><span data-ttu-id="1333b-216">8단계: 마이그레이션 후 작업 완료</span><span class="sxs-lookup"><span data-stu-id="1333b-216">Step 8: Complete post-migration tasks</span></span>
<span data-ttu-id="1333b-217"><a name="BK_Step8"> </a></span><span class="sxs-lookup"><span data-stu-id="1333b-217"><a name="BK_Step8"> </a></span></span>

- <span data-ttu-id="1333b-218">**사용자가 자신의 사서함으로 쉽게 이동할 수 있도록 자동 검색 DNS 레코드를 만듭니다.**</span><span class="sxs-lookup"><span data-stu-id="1333b-218">**Create an Autodiscover DNS record so users can easily get to their mailboxes.**</span></span> <span data-ttu-id="1333b-219">모든 온-프레미스 사서함이 Microsoft 365로 마이그레이션된 후에는 사용자가 Outlook 및 모바일 클라이언트를 사용 하 여 새 Microsoft 365 사서함에 쉽게 연결할 수 있도록 Microsoft 365 조 직에 대 한 자동 검색 DNS 레코드를 구성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1333b-219">After all on-premises mailboxes are migrated to Microsoft 365, you can configure an Autodiscover DNS record for your Microsoft 365 organization to enable users to easily connect to their new Microsoft 365 mailboxes with Outlook and mobile clients.</span></span> <span data-ttu-id="1333b-220">이 새로운 자동 검색 DNS 레코드는 Microsoft 365 조직에 사용 중인 것과 동일한 네임 스페이스를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1333b-220">This new Autodiscover DNS record has to use the same namespace that you're using for your Microsoft 365 organization.</span></span> <span data-ttu-id="1333b-221">예를 들어 클라우드 기반 네임스페이스가 cloud.contoso.com인 경우 만들어야 할 자동 검색 DNS 레코드는 autodiscover.cloud.contoso.com입니다.</span><span class="sxs-lookup"><span data-stu-id="1333b-221">For example, if your cloud-based namespace is cloud.contoso.com, the Autodiscover DNS record you need to create is autodiscover.cloud.contoso.com.</span></span>
    
    <span data-ttu-id="1333b-222">Exchange 서버를 유지 하는 경우 Outlook 클라이언트에서 올바른 사서함에 연결 하기 위해 마이그레이션 후 내부 및 외부 DNS에서 자동 검색 DNS CNAME 레코드가 Microsoft 365을 가리키는지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1333b-222">If you keep your Exchange Server, you should also make sure that Autodiscover DNS CNAME record has to point to Microsoft 365 in both internal and external DNS after the migration so that the Outlook client will to connect to the correct mailbox.</span></span>
    
    > [!NOTE]
    >  <span data-ttu-id="1333b-223">또한 Exchange 2007, Exchange 2010 및 Exchange 2013에서  `Set-ClientAccessServer AutodiscoverInternalConnectionURI`를  `Null`로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1333b-223">In Exchange 2007, Exchange 2010, and Exchange 2013 you should also set `Set-ClientAccessServer AutodiscoverInternalConnectionURI` to `Null`.</span></span> 
  
    <span data-ttu-id="1333b-224">Microsoft 365는 CNAME 레코드를 사용 하 여 Outlook 및 모바일 클라이언트에 대 한 자동 검색 서비스를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="1333b-224">Microsoft 365 uses a CNAME record to implement the Autodiscover service for Outlook and mobile clients.</span></span> <span data-ttu-id="1333b-225">Autodiscover CNAME 레코드에는 다음과 같은 정보가 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1333b-225">The Autodiscover CNAME record must contain the following information:</span></span>
    
  - <span data-ttu-id="1333b-226">**별칭:** autodiscover</span><span class="sxs-lookup"><span data-stu-id="1333b-226">**Alias:** autodiscover</span></span>
    
  - <span data-ttu-id="1333b-227">**대상:** autodiscover.outlook.com</span><span class="sxs-lookup"><span data-stu-id="1333b-227">**Target:** autodiscover.outlook.com</span></span>
    
    <span data-ttu-id="1333b-228">자세한 내용은 [DNS 레코드를 추가 하 여 도메인 연결](https://go.microsoft.com/fwlink/p/?LinkId=535028)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="1333b-228">For more information, see [Add DNS records to connect your domain](https://go.microsoft.com/fwlink/p/?LinkId=535028).</span></span>
    
- <span data-ttu-id="1333b-229">**온-프레미스 Exchange 서버를 해제합니다.**</span><span class="sxs-lookup"><span data-stu-id="1333b-229">**Decommission on-premises Exchange servers.**</span></span> <span data-ttu-id="1333b-230">모든 전자 메일이 Microsoft 365 사서함으로 바로 라우팅되고 있음을 확인 하 고 온-프레미스 전자 메일 조직을 더 이상 유지 관리할 필요가 없거나 SSO (single sign-on) 솔루션을 구현 하지 않아도 되는 경우 서버에서 Exchange를 제거 하 고 온-프레미스 Exchange 조직을 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1333b-230">After you've verified that all email is being routed directly to the Microsoft 365 mailboxes, and you no longer need to maintain your on-premises email organization or don't plan on implementing a single sign-on (SSO) solution, you can uninstall Exchange from your servers and remove your on-premises Exchange organization.</span></span>
    
    <span data-ttu-id="1333b-231">자세한 내용은 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="1333b-231">For more information, see the following:</span></span>
    
  - [<span data-ttu-id="1333b-232">Exchange 2010 수정 또는 제거</span><span class="sxs-lookup"><span data-stu-id="1333b-232">Modify or Remove Exchange 2010</span></span>](https://go.microsoft.com/fwlink/?LinkId=217936)
    
  - [<span data-ttu-id="1333b-233">Exchange 2007 조직 제거 방법</span><span class="sxs-lookup"><span data-stu-id="1333b-233">How to Remove an Exchange 2007 Organization</span></span>](https://go.microsoft.com/fwlink/?LinkID=100485)
    
  - [<span data-ttu-id="1333b-234">Exchange Server 2003 제거 방법</span><span class="sxs-lookup"><span data-stu-id="1333b-234">How to Uninstall Exchange Server 2003</span></span>](https://go.microsoft.com/fwlink/?LinkID=56561)
    

