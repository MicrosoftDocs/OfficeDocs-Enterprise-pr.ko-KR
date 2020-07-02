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
# <a name="use-powershell-to-perform-a-cutover-migration-to-office-365"></a><span data-ttu-id="3314c-103">PowerShell을 사용하여 Office 365로 단독형 마이그레이션 수행</span><span class="sxs-lookup"><span data-stu-id="3314c-103">Use PowerShell to perform a cutover migration to Office 365</span></span>

<span data-ttu-id="3314c-104">You can migrate the contents of user mailboxes from a source email system to Office 365 all at once by using a cutover migration.</span><span class="sxs-lookup"><span data-stu-id="3314c-104">You can migrate the contents of user mailboxes from a source email system to Office 365 all at once by using a cutover migration.</span></span> <span data-ttu-id="3314c-105">This article walks you through the tasks for an email cutover migration by using Exchange Online PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3314c-105">This article walks you through the tasks for an email cutover migration by using Exchange Online PowerShell.</span></span> 
  
<span data-ttu-id="3314c-106">By reviewing the topic, [What you need to know about a cutover email migration to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536688), you can get an overview of the migration process.</span><span class="sxs-lookup"><span data-stu-id="3314c-106">By reviewing the topic, [What you need to know about a cutover email migration to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536688), you can get an overview of the migration process.</span></span> <span data-ttu-id="3314c-107">When you're comfortable with the contents of that article, use this one to begin migrating mailboxes from one email system to another.</span><span class="sxs-lookup"><span data-stu-id="3314c-107">When you're comfortable with the contents of that article, use this one to begin migrating mailboxes from one email system to another.</span></span>
  
> [!NOTE]
> <span data-ttu-id="3314c-108">You can also use the Exchange admin center to perform a cutover migration.</span><span class="sxs-lookup"><span data-stu-id="3314c-108">You can also use the Exchange admin center to perform a cutover migration.</span></span> <span data-ttu-id="3314c-109">See [Perform a cutover migration of email to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536689).</span><span class="sxs-lookup"><span data-stu-id="3314c-109">See [Perform a cutover migration of email to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536689).</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="3314c-110">시작하기 전에 알아야 할 내용</span><span class="sxs-lookup"><span data-stu-id="3314c-110">What do you need to know before you begin?</span></span>

<span data-ttu-id="3314c-111">Estimated time to complete this task: 2-5 minutes to create a migration batch.</span><span class="sxs-lookup"><span data-stu-id="3314c-111">Estimated time to complete this task: 2-5 minutes to create a migration batch.</span></span> <span data-ttu-id="3314c-112">After the migration batch is started, the duration of the migration will vary based on the number of mailboxes in the batch, the size of each mailbox, and your available network capacity.</span><span class="sxs-lookup"><span data-stu-id="3314c-112">After the migration batch is started, the duration of the migration will vary based on the number of mailboxes in the batch, the size of each mailbox, and your available network capacity.</span></span> <span data-ttu-id="3314c-113">For information about other factors that affect how long it takes to migrate mailboxes to Office 365, see [Migration Performance](https://go.microsoft.com/fwlink/p/?LinkId=275079).</span><span class="sxs-lookup"><span data-stu-id="3314c-113">For information about other factors that affect how long it takes to migrate mailboxes to Office 365, see [Migration Performance](https://go.microsoft.com/fwlink/p/?LinkId=275079).</span></span>
  
<span data-ttu-id="3314c-114">You need to be assigned permissions before you can perform this procedure or procedures.</span><span class="sxs-lookup"><span data-stu-id="3314c-114">You need to be assigned permissions before you can perform this procedure or procedures.</span></span> <span data-ttu-id="3314c-115">To see what permissions you need, see the "Migration" entry in a table in the [Recipients Permissions](https://go.microsoft.com/fwlink/p/?LinkId=534105) topic.</span><span class="sxs-lookup"><span data-stu-id="3314c-115">To see what permissions you need, see the "Migration" entry in a table in the [Recipients Permissions](https://go.microsoft.com/fwlink/p/?LinkId=534105) topic.</span></span>
  
<span data-ttu-id="3314c-116">To use the Exchange Online PowerShell cmdlets, you need to sign in and import the cmdlets into your local Windows PowerShell session.</span><span class="sxs-lookup"><span data-stu-id="3314c-116">To use the Exchange Online PowerShell cmdlets, you need to sign in and import the cmdlets into your local Windows PowerShell session.</span></span> <span data-ttu-id="3314c-117">See [Connect to Exchange Online using remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121) for instructions.</span><span class="sxs-lookup"><span data-stu-id="3314c-117">See [Connect to Exchange Online using remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121) for instructions.</span></span>
  
<span data-ttu-id="3314c-118">전체 마이그레이션 명령 목록을 보려면 [이동 및 마이그레이션 cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=534750)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3314c-118">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
  
## <a name="migration-steps"></a><span data-ttu-id="3314c-119">마이그레이션 단계</span><span class="sxs-lookup"><span data-stu-id="3314c-119">Migration steps</span></span>

### <a name="step-1-prepare-for-a-cutover-migration"></a><span data-ttu-id="3314c-120">1단계: 단독형 마이그레이션 준비</span><span class="sxs-lookup"><span data-stu-id="3314c-120">Step 1: Prepare for a cutover migration</span></span>
<span data-ttu-id="3314c-121"><a name="BK_Step1"> </a></span><span class="sxs-lookup"><span data-stu-id="3314c-121"><a name="BK_Step1"> </a></span></span>

- <span data-ttu-id="3314c-122">**Add your on-premises Exchange organization as an accepted domain of your Office 365 organization.**</span><span class="sxs-lookup"><span data-stu-id="3314c-122">**Add your on-premises Exchange organization as an accepted domain of your Office 365 organization.**</span></span> <span data-ttu-id="3314c-123">The migration service uses the SMTP address of your on-premises mailboxes to create the Microsoft Online Services user ID and email address for the new Office 365 mailboxes.</span><span class="sxs-lookup"><span data-stu-id="3314c-123">The migration service uses the SMTP address of your on-premises mailboxes to create the Microsoft Online Services user ID and email address for the new Office 365 mailboxes.</span></span> <span data-ttu-id="3314c-124">Migration will fail if your Exchange domain isn't an accepted domain or the primary domain of your Office 365 organization.</span><span class="sxs-lookup"><span data-stu-id="3314c-124">Migration will fail if your Exchange domain isn't an accepted domain or the primary domain of your Office 365 organization.</span></span> <span data-ttu-id="3314c-125">For more information, see[Verify your domain in Office 365](https://go.microsoft.com/fwlink/p/?LinkId=534110).</span><span class="sxs-lookup"><span data-stu-id="3314c-125">For more information, see[Verify your domain in Office 365](https://go.microsoft.com/fwlink/p/?LinkId=534110).</span></span>
    
- <span data-ttu-id="3314c-126">**Configure Outlook Anywhere on your on-premises Exchange server.**</span><span class="sxs-lookup"><span data-stu-id="3314c-126">**Configure Outlook Anywhere on your on-premises Exchange server.**</span></span> <span data-ttu-id="3314c-127">The email migration service uses RPC over HTTP, or Outlook Anywhere, to connect to your on-premises Exchange server.</span><span class="sxs-lookup"><span data-stu-id="3314c-127">The email migration service uses RPC over HTTP, or Outlook Anywhere, to connect to your on-premises Exchange server.</span></span> <span data-ttu-id="3314c-128">For information about how to set up Outlook Anywhere for Exchange 2010, Exchange 2007, and Exchange 2003, see the following:</span><span class="sxs-lookup"><span data-stu-id="3314c-128">For information about how to set up Outlook Anywhere for Exchange 2010, Exchange 2007, and Exchange 2003, see the following:</span></span>
    
  - [<span data-ttu-id="3314c-129">Exchange 2010: "외부에서 Outlook 사용" 설정</span><span class="sxs-lookup"><span data-stu-id="3314c-129">Exchange 2010: Enable Outlook Anywhere</span></span>](https://go.microsoft.com/fwlink/?LinkID=187249)
    
  - [<span data-ttu-id="3314c-130">Exchange 2007: 외부에서 Outlook 사용 설정 방법</span><span class="sxs-lookup"><span data-stu-id="3314c-130">Exchange 2007: How to Enable Outlook Anywhere</span></span>](https://go.microsoft.com/fwlink/?LinkID=167210)
    
  - [<span data-ttu-id="3314c-131">Exchange 2003: RPC over HTTP에 대한 배포 시나리오</span><span class="sxs-lookup"><span data-stu-id="3314c-131">Exchange 2003: Deployment Scenarios for RPC over HTTP</span></span>](https://go.microsoft.com/fwlink/?LinkID=73657)
    
  - [<span data-ttu-id="3314c-132">Exchange 2003: "외부에서 Outlook 사용" 구성 방법</span><span class="sxs-lookup"><span data-stu-id="3314c-132">How to Configure Outlook Anywhere with Exchange 2003</span></span>](https://go.microsoft.com/fwlink/?LinkID=167209)
    
    > [!IMPORTANT]
    > <span data-ttu-id="3314c-133">Your Outlook Anywhere configuration must be configured with a certificate issued by a trusted certification authority (CA).</span><span class="sxs-lookup"><span data-stu-id="3314c-133">Your Outlook Anywhere configuration must be configured with a certificate issued by a trusted certification authority (CA).</span></span> <span data-ttu-id="3314c-134">It can't be configured with a self-signed certificate.</span><span class="sxs-lookup"><span data-stu-id="3314c-134">It can't be configured with a self-signed certificate.</span></span> <span data-ttu-id="3314c-135">For more information, see [How to Configure SSL for Outlook Anywhere](https://go.microsoft.com/fwlink/?LinkID=80875).</span><span class="sxs-lookup"><span data-stu-id="3314c-135">For more information, see [How to Configure SSL for Outlook Anywhere](https://go.microsoft.com/fwlink/?LinkID=80875).</span></span> 
  
- <span data-ttu-id="3314c-136">**Verify that you can connect to your Exchange organization using Outlook Anywhere.**</span><span class="sxs-lookup"><span data-stu-id="3314c-136">**Verify that you can connect to your Exchange organization using Outlook Anywhere.**</span></span> <span data-ttu-id="3314c-137">Try one of these methods to test your connection settings:</span><span class="sxs-lookup"><span data-stu-id="3314c-137">Try one of these methods to test your connection settings:</span></span>
    
  - <span data-ttu-id="3314c-138">회사 네트워크 외부에서 Microsoft Outlook을 사용하여 온-프레미스 Exchange 사서함에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="3314c-138">Use Microsoft Outlook from outside your corporate network to connect to your on-premises Exchange mailbox.</span></span>
    
  - <span data-ttu-id="3314c-139">Use the Microsoft [Exchange Remote Connectivity Analyzer](https://www.testexchangeconnectivity.com/) to test your connection settings.</span><span class="sxs-lookup"><span data-stu-id="3314c-139">Use the Microsoft [Exchange Remote Connectivity Analyzer](https://www.testexchangeconnectivity.com/) to test your connection settings.</span></span> <span data-ttu-id="3314c-140">Use the Outlook Anywhere (RPC over HTTP) or Outlook Autodiscover tests.</span><span class="sxs-lookup"><span data-stu-id="3314c-140">Use the Outlook Anywhere (RPC over HTTP) or Outlook Autodiscover tests.</span></span>
    
  - <span data-ttu-id="3314c-141">Exchange Online PowerShell에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="3314c-141">Run the following commands in Exchange Online PowerShell.</span></span>
    
  ```
  $Credentials = Get-Credential
  ```

  ```
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

- <span data-ttu-id="3314c-142">**온-프레미스 사용자 계정에 Exchange 조직의 사서함에 액세스하는 데 필요한 사용 권한 할당**</span><span class="sxs-lookup"><span data-stu-id="3314c-142">**Assign an on-premises user account the necessary permissions to access mailboxes in your Exchange organization.**</span></span> <span data-ttu-id="3314c-143">온-프레미스 Exchange 조직에 연결 하는 데 사용 하는 온-프레미스 사용자 계정 (마이그레이션 관리자 라고도 함)에는 Office 365로 마이그레이션할 온-프레미스 사서함에 액세스 하는 데 필요한 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3314c-143">The on-premises user account that you use to connect to your on-premises Exchange organization (also called the migration administrator) must have the necessary permissions to access the on-premises mailboxes that you want to migrate to Office 365.</span></span> <span data-ttu-id="3314c-144">이 사용자 계정은 온-프레미스 조직에 대한 마이그레이션 끝점을 만드는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3314c-144">This user account is used to create a migration endpoint to your on-premises organization.</span></span>
    
    <span data-ttu-id="3314c-145">The following list shows the administrative privileges required to migrate mailboxes using a cutover migration.</span><span class="sxs-lookup"><span data-stu-id="3314c-145">The following list shows the administrative privileges required to migrate mailboxes using a cutover migration.</span></span> <span data-ttu-id="3314c-146">There are three possible options.</span><span class="sxs-lookup"><span data-stu-id="3314c-146">There are three possible options.</span></span>
    
  - <span data-ttu-id="3314c-147">마이그레이션 관리자는 온-프레미스 조직의 Active Directory에 있는 **Domain Admins** 그룹의 구성원이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3314c-147">The migration administrator must be a member of the **Domain Admins** group in Active Directory in the on-premises organization.</span></span>
    
    <span data-ttu-id="3314c-148">또는</span><span class="sxs-lookup"><span data-stu-id="3314c-148">Or</span></span>
    
  - <span data-ttu-id="3314c-149">마이그레이션 관리자에게 각 온-프레미스 사서함에 대한 **모든 권한** 권한이 할당되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3314c-149">The migration administrator must be assigned the **FullAccess** permission for each on-premises mailbox.</span></span>
    
    <span data-ttu-id="3314c-150">또는</span><span class="sxs-lookup"><span data-stu-id="3314c-150">Or</span></span>
    
  - <span data-ttu-id="3314c-151">마이그레이션 관리자에게 사용자 사서함을 저장하는 온-프레미스 사서함 데이터베이스에 대한 **다음으로 받기** 권한이 할당되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3314c-151">The migration administrator must be assigned the **Receive As** permission on the on-premises mailbox database that stores the user mailboxes.</span></span>
    
- <span data-ttu-id="3314c-152">**Disable Unified Messaging.**</span><span class="sxs-lookup"><span data-stu-id="3314c-152">**Disable Unified Messaging.**</span></span> <span data-ttu-id="3314c-153">If the on-premises mailboxes you're migrating are enabled for Unified Messaging (UM), you have to disable UM on the mailboxes before you migrate them.</span><span class="sxs-lookup"><span data-stu-id="3314c-153">If the on-premises mailboxes you're migrating are enabled for Unified Messaging (UM), you have to disable UM on the mailboxes before you migrate them.</span></span> <span data-ttu-id="3314c-154">You can then enable UM on the mailboxes after the migration is complete.</span><span class="sxs-lookup"><span data-stu-id="3314c-154">You can then enable UM on the mailboxes after the migration is complete.</span></span>
    
- <span data-ttu-id="3314c-155">**Security Groups and Delegates** The email migration service cannot detect whether on-premises Active Directory groups are security groups or not, so it cannot provision any migrated groups as security groups in Office 365.</span><span class="sxs-lookup"><span data-stu-id="3314c-155">**Security Groups and Delegates** The email migration service cannot detect whether on-premises Active Directory groups are security groups or not, so it cannot provision any migrated groups as security groups in Office 365.</span></span> <span data-ttu-id="3314c-156">If you want to have security groups in your Office 365 tenant, you must first provision an empty mail-enabled security group in your Office 365 tenant before starting the cutover migration.</span><span class="sxs-lookup"><span data-stu-id="3314c-156">If you want to have security groups in your Office 365 tenant, you must first provision an empty mail-enabled security group in your Office 365 tenant before starting the cutover migration.</span></span> <span data-ttu-id="3314c-157">Additionally, this migration method only moves mailboxes, mail users, mail contacts, and mail-enabled groups.</span><span class="sxs-lookup"><span data-stu-id="3314c-157">Additionally, this migration method only moves mailboxes, mail users, mail contacts, and mail-enabled groups.</span></span> <span data-ttu-id="3314c-158">If any other Active Directory object, such as user that is not migrated to Office 365, is assigned as a manager or delegate to an object being migrated, they must be removed from the object before you migrate.</span><span class="sxs-lookup"><span data-stu-id="3314c-158">If any other Active Directory object, such as user that is not migrated to Office 365, is assigned as a manager or delegate to an object being migrated, they must be removed from the object before you migrate.</span></span>
    
### <a name="step-2-create-a-migration-endpoint"></a><span data-ttu-id="3314c-159">2단계: 마이그레이션 끝점 만들기</span><span class="sxs-lookup"><span data-stu-id="3314c-159">Step 2: Create a migration endpoint</span></span>
<span data-ttu-id="3314c-160"><a name="BK_Step2"> </a></span><span class="sxs-lookup"><span data-stu-id="3314c-160"><a name="BK_Step2"> </a></span></span>

<span data-ttu-id="3314c-161">To migrate email successfully, Office 365 needs to connect and communicate with the source email system.</span><span class="sxs-lookup"><span data-stu-id="3314c-161">To migrate email successfully, Office 365 needs to connect and communicate with the source email system.</span></span> <span data-ttu-id="3314c-162">To do this, Office 365 uses a migration endpoint.</span><span class="sxs-lookup"><span data-stu-id="3314c-162">To do this, Office 365 uses a migration endpoint.</span></span> <span data-ttu-id="3314c-163">To create an Outlook Anywhere migration endpoint for cutover migration, first [connect to Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span><span class="sxs-lookup"><span data-stu-id="3314c-163">To create an Outlook Anywhere migration endpoint for cutover migration, first [connect to Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span></span> 
  
<span data-ttu-id="3314c-164">전체 마이그레이션 명령 목록을 보려면 [이동 및 마이그레이션 cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=534750)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3314c-164">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
  
<span data-ttu-id="3314c-165">Exchange Online PowerShell에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="3314c-165">Run the following commands in Exchange Online PowerShell:</span></span>
  
```
$Credentials = Get-Credential
```

<span data-ttu-id="3314c-166">이 예에서는 [Test-MigrationServerAvailability](https://go.microsoft.com/fwlink/p/?LinkId=534752) cmdlet을 사용하여 온-프레미스 Exchange 서버에 대한 연결 설정을 가져오고 테스트한 다음 해당 연결 설정을 사용하여 "CutoverEndpoint"라는 마이그레이션 끝점을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3314c-166">The example uses the [Test-MigrationServerAvailability](https://go.microsoft.com/fwlink/p/?LinkId=534752) cmdlet to obtain and test the connection settings to the on-premises Exchange server, and then uses those connection settings to create the migration endpoint called "CutoverEndpoint".</span></span>
  
```
$TSMA = Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress administrator@contoso.com -Credentials $credentials
```

```
New-MigrationEndpoint -ExchangeOutlookAnywhere -Name CutoverEndpoint -ConnectionSettings $TSMA.ConnectionSettings
```

> [!NOTE]
> <span data-ttu-id="3314c-167">The **New-MigrationEndpoint** cmdlet can be used to specify a database for the service to use by using the **-TargetDatabase** option.</span><span class="sxs-lookup"><span data-stu-id="3314c-167">The **New-MigrationEndpoint** cmdlet can be used to specify a database for the service to use by using the **-TargetDatabase** option.</span></span> <span data-ttu-id="3314c-168">Otherwise a database is randomly assigned from the Active Directory Federation Services (AD FS) 2.0 site where the management mailbox is located.</span><span class="sxs-lookup"><span data-stu-id="3314c-168">Otherwise a database is randomly assigned from the Active Directory Federation Services (AD FS) 2.0 site where the management mailbox is located.</span></span>
  
#### <a name="verify-it-worked"></a><span data-ttu-id="3314c-169">작동하는지 확인</span><span class="sxs-lookup"><span data-stu-id="3314c-169">Verify it worked</span></span>

<span data-ttu-id="3314c-170">Exchange Online PowerShell에서 다음 명령을 실행하여 "CutoverEndpoint" 마이그레이션 끝점에 대한 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="3314c-170">In Exchange Online PowerShell, run the following command to display information about the "CutoverEndpoint" migration endpoint:</span></span>
  
```
Get-MigrationEndpoint CutoverEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*

```

### <a name="step-3-create-the-cutover-migration-batch"></a><span data-ttu-id="3314c-171">3단계: 단독형 마이그레이션 일괄 처리 만들기</span><span class="sxs-lookup"><span data-stu-id="3314c-171">Step 3: Create the cutover migration batch</span></span>
<span data-ttu-id="3314c-172"><a name="BK_Step3"> </a></span><span class="sxs-lookup"><span data-stu-id="3314c-172"><a name="BK_Step3"> </a></span></span>

<span data-ttu-id="3314c-173">You can use the **New-MigrationBatch** cmdlet in Exchange Online PowerShell to create a migration batch for a cutover migration.</span><span class="sxs-lookup"><span data-stu-id="3314c-173">You can use the **New-MigrationBatch** cmdlet in Exchange Online PowerShell to create a migration batch for a cutover migration.</span></span> <span data-ttu-id="3314c-174">You can create a migration batch and start it automatically by including the _AutoStart_ parameter.</span><span class="sxs-lookup"><span data-stu-id="3314c-174">You can create a migration batch and start it automatically by including the _AutoStart_ parameter.</span></span> <span data-ttu-id="3314c-175">Alternatively, you can create the migration batch and then manually start it afterwards by using the **Start-MigrationBatch** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3314c-175">Alternatively, you can create the migration batch and then manually start it afterwards by using the **Start-MigrationBatch** cmdlet.</span></span> <span data-ttu-id="3314c-176">This example creates a migration batch called "CutoverBatch" and uses the migration endpoint that was created in the previous step.</span><span class="sxs-lookup"><span data-stu-id="3314c-176">This example creates a migration batch called "CutoverBatch" and uses the migration endpoint that was created in the previous step.</span></span>
  
```
New-MigrationBatch -Name CutoverBatch -SourceEndpoint CutoverEndpoint -AutoStart
```

<span data-ttu-id="3314c-177">This example also creates a migration batch called "CutoverBatch" and uses the migration endpoint that was created in the previous step.</span><span class="sxs-lookup"><span data-stu-id="3314c-177">This example also creates a migration batch called "CutoverBatch" and uses the migration endpoint that was created in the previous step.</span></span> <span data-ttu-id="3314c-178">Because the  _AutoStart_ parameter isn't included, the migration batch has to be manually started on the migration dashboard or by using **Start-MigrationBatch** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3314c-178">Because the  _AutoStart_ parameter isn't included, the migration batch has to be manually started on the migration dashboard or by using **Start-MigrationBatch** cmdlet.</span></span> <span data-ttu-id="3314c-179">As previously stated, only one cutover migration batch can exist at a time.</span><span class="sxs-lookup"><span data-stu-id="3314c-179">As previously stated, only one cutover migration batch can exist at a time.</span></span>
  
```
New-MigrationBatch -Name CutoverBatch -SourceEndpoint CutoverEndpoint
```

#### <a name="verify-it-worked"></a><span data-ttu-id="3314c-180">작동하는지 확인</span><span class="sxs-lookup"><span data-stu-id="3314c-180">Verify it worked</span></span>

<span data-ttu-id="3314c-181">단독형 마이그레이션을 위한 마이그레이션 일괄 처리를 성공적으로 만들었는지 확인하려면 Exchange Online PowerShell에서 다음 명령을 실행하여 새 마이그레이션 일괄 처리에 대한 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="3314c-181">To verify that you've successfully created a migration batch for a cutover migration, run the following command in Exchange Online PowerShell to display information about the new migration batch:</span></span>
  
```
Get-MigrationBatch | Format-List
```

### <a name="step-4-start-the-cutover-migration-batch"></a><span data-ttu-id="3314c-182">4단계: 단독형 마이그레이션 일괄 처리 시작</span><span class="sxs-lookup"><span data-stu-id="3314c-182">Step 4: Start the cutover migration batch</span></span>
<span data-ttu-id="3314c-183"><a name="BK_Step4"> </a></span><span class="sxs-lookup"><span data-stu-id="3314c-183"><a name="BK_Step4"> </a></span></span>

<span data-ttu-id="3314c-184">To start the migration batch in Exchange Online PowerShell, run the following command.</span><span class="sxs-lookup"><span data-stu-id="3314c-184">To start the migration batch in Exchange Online PowerShell, run the following command.</span></span> <span data-ttu-id="3314c-185">This will create a migration batch called "CutoverBatch".</span><span class="sxs-lookup"><span data-stu-id="3314c-185">This will create a migration batch called "CutoverBatch".</span></span>
  
```
Start-MigrationBatch -Identity CutoverBatch
```

#### <a name="verify-it-worked"></a><span data-ttu-id="3314c-186">작동하는지 확인</span><span class="sxs-lookup"><span data-stu-id="3314c-186">Verify it worked</span></span>

<span data-ttu-id="3314c-187">If a migration batch is successfully started, its status on the migration dashboard is specified as Syncing.</span><span class="sxs-lookup"><span data-stu-id="3314c-187">If a migration batch is successfully started, its status on the migration dashboard is specified as Syncing.</span></span> <span data-ttu-id="3314c-188">To verify that you've successfully started a migration batch using Exchange Online PowerShell, run the following command:</span><span class="sxs-lookup"><span data-stu-id="3314c-188">To verify that you've successfully started a migration batch using Exchange Online PowerShell, run the following command:</span></span>
  
```
Get-MigrationBatch -Identity CutoverBatch |  Format-List Status
```

### <a name="step-5-route-your-email-to-office-365"></a><span data-ttu-id="3314c-189">5단계: Office 365로 전자 메일 라우팅</span><span class="sxs-lookup"><span data-stu-id="3314c-189">Step 5: Route your email to Office 365</span></span>
<span data-ttu-id="3314c-190"><a name="BK_Step5"> </a></span><span class="sxs-lookup"><span data-stu-id="3314c-190"><a name="BK_Step5"> </a></span></span>

<span data-ttu-id="3314c-191">Email systems use a DNS record called an MX record to figure out where to deliver emails.</span><span class="sxs-lookup"><span data-stu-id="3314c-191">Email systems use a DNS record called an MX record to figure out where to deliver emails.</span></span> <span data-ttu-id="3314c-192">During the email migration process, your MX record was pointing to your source email system.</span><span class="sxs-lookup"><span data-stu-id="3314c-192">During the email migration process, your MX record was pointing to your source email system.</span></span> <span data-ttu-id="3314c-193">Now that the email migration to Office 365 is complete, it's time to point your MX record at Office 365.</span><span class="sxs-lookup"><span data-stu-id="3314c-193">Now that the email migration to Office 365 is complete, it's time to point your MX record at Office 365.</span></span> <span data-ttu-id="3314c-194">This helps make sure that email is delivered to your Office 365 mailboxes.</span><span class="sxs-lookup"><span data-stu-id="3314c-194">This helps make sure that email is delivered to your Office 365 mailboxes.</span></span> <span data-ttu-id="3314c-195">By moving the MX record, you can also you turn off your old email system when you're ready.</span><span class="sxs-lookup"><span data-stu-id="3314c-195">By moving the MX record, you can also you turn off your old email system when you're ready.</span></span> 
  
<span data-ttu-id="3314c-196">For many DNS providers, there are specific instructions to [change your MX record](https://go.microsoft.com/fwlink/p/?LinkId=279163).</span><span class="sxs-lookup"><span data-stu-id="3314c-196">For many DNS providers, there are specific instructions to [change your MX record](https://go.microsoft.com/fwlink/p/?LinkId=279163).</span></span> <span data-ttu-id="3314c-197">If your DNS provider isn't included, or if you want to get a sense of the general directions, [general MX record instructions ](https://go.microsoft.com/fwlink/?LinkId=397449) are provided as well.</span><span class="sxs-lookup"><span data-stu-id="3314c-197">If your DNS provider isn't included, or if you want to get a sense of the general directions, [general MX record instructions ](https://go.microsoft.com/fwlink/?LinkId=397449) are provided as well.</span></span>
  
<span data-ttu-id="3314c-198">It can take up to 72 hours for the email systems of your customers and partners to recognize the changed MX record.</span><span class="sxs-lookup"><span data-stu-id="3314c-198">It can take up to 72 hours for the email systems of your customers and partners to recognize the changed MX record.</span></span> <span data-ttu-id="3314c-199">Wait at least 72 hours before you proceed to the next task: [Step 6: Delete the cutover migration batch](use-powershell-to-perform-a-cutover-migration-to-office-365.md#Bk_step6).</span><span class="sxs-lookup"><span data-stu-id="3314c-199">Wait at least 72 hours before you proceed to the next task: [Step 6: Delete the cutover migration batch](use-powershell-to-perform-a-cutover-migration-to-office-365.md#Bk_step6).</span></span> 
  
### <a name="step-6-delete-the-cutover-migration-batch"></a><span data-ttu-id="3314c-200">6단계: 단독형 마이그레이션 일괄 처리 삭제</span><span class="sxs-lookup"><span data-stu-id="3314c-200">Step 6: Delete the cutover migration batch</span></span>
<span data-ttu-id="3314c-201"><a name="Bk_step6"> </a></span><span class="sxs-lookup"><span data-stu-id="3314c-201"><a name="Bk_step6"> </a></span></span>

<span data-ttu-id="3314c-202">After you change the MX record and verify that all email is being routed to Office 365 mailboxes, notify the users that their mail is going to Office 365.</span><span class="sxs-lookup"><span data-stu-id="3314c-202">After you change the MX record and verify that all email is being routed to Office 365 mailboxes, notify the users that their mail is going to Office 365.</span></span> <span data-ttu-id="3314c-203">After this, you can delete the cutover migration batch.</span><span class="sxs-lookup"><span data-stu-id="3314c-203">After this, you can delete the cutover migration batch.</span></span> <span data-ttu-id="3314c-204">Verify the following before you delete the migration batch.</span><span class="sxs-lookup"><span data-stu-id="3314c-204">Verify the following before you delete the migration batch.</span></span>
  
- <span data-ttu-id="3314c-205">All users are using Office 365 mailboxes.</span><span class="sxs-lookup"><span data-stu-id="3314c-205">All users are using Office 365 mailboxes.</span></span> <span data-ttu-id="3314c-206">After the batch is deleted, mail sent to mailboxes on the on-premises Exchange Server isn't copied to the corresponding Office 365 mailboxes.</span><span class="sxs-lookup"><span data-stu-id="3314c-206">After the batch is deleted, mail sent to mailboxes on the on-premises Exchange Server isn't copied to the corresponding Office 365 mailboxes.</span></span>
    
- <span data-ttu-id="3314c-207">Office 365 mailboxes were synchronized at least once after mail began being sent directly to them.</span><span class="sxs-lookup"><span data-stu-id="3314c-207">Office 365 mailboxes were synchronized at least once after mail began being sent directly to them.</span></span> <span data-ttu-id="3314c-208">To do this, make sure that the value in the Last Synced Time box for the migration batch is more recent than when mail started being routed directly to Office 365 mailboxes.</span><span class="sxs-lookup"><span data-stu-id="3314c-208">To do this, make sure that the value in the Last Synced Time box for the migration batch is more recent than when mail started being routed directly to Office 365 mailboxes.</span></span>
    
<span data-ttu-id="3314c-209">Exchange Online PowerShell에서 "CutoverBatch" 마이그레이션 일괄 처리를 삭제하려면 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="3314c-209">To delete the "CutoverBatch" migration batch in Exchange Online PowerShell, run the following command:</span></span>
  
```
Remove-MigrationBatch -Identity CutoverBatch
```

### <a name="section-7-assign-user-licenses"></a><span data-ttu-id="3314c-210">섹션 7: 사용자 라이선스 할당</span><span class="sxs-lookup"><span data-stu-id="3314c-210">Section 7: Assign user licenses</span></span>
<span data-ttu-id="3314c-211"><a name="BK_Step7"> </a></span><span class="sxs-lookup"><span data-stu-id="3314c-211"><a name="BK_Step7"> </a></span></span>

 <span data-ttu-id="3314c-212">**라이선스를 할당하여 마이그레이션된 계정에 대한 Office 365 사용자 계정을 활성화합니다.**</span><span class="sxs-lookup"><span data-stu-id="3314c-212">**Activate Office 365 user accounts for the migrated accounts by assigning licenses.**</span></span> <span data-ttu-id="3314c-213">라이선스를 할당하지 않은 경우 30일 유예 기간이 끝나면 사서함을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3314c-213">If you don't assign a license, the mailbox is disabled when the grace period ends (30 days).</span></span> <span data-ttu-id="3314c-214">Microsoft 365 관리 센터에서 라이선스를 할당 하려면[비즈니스용 Office 365에 대 한 라이선스 할당 또는](https://go.microsoft.com/fwlink/?LinkId=536681)할당 해제를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3314c-214">To assign a license in the Microsoft 365 admin center, see[Assign or unassign licenses for Office 365 for business](https://go.microsoft.com/fwlink/?LinkId=536681).</span></span>
  
### <a name="step-8-complete-post-migration-tasks"></a><span data-ttu-id="3314c-215">8단계: 마이그레이션 후 작업 완료</span><span class="sxs-lookup"><span data-stu-id="3314c-215">Step 8: Complete post-migration tasks</span></span>
<span data-ttu-id="3314c-216"><a name="BK_Step8"> </a></span><span class="sxs-lookup"><span data-stu-id="3314c-216"><a name="BK_Step8"> </a></span></span>

- <span data-ttu-id="3314c-217">**Create an Autodiscover DNS record so users can easily get to their mailboxes.**</span><span class="sxs-lookup"><span data-stu-id="3314c-217">**Create an Autodiscover DNS record so users can easily get to their mailboxes.**</span></span> <span data-ttu-id="3314c-218">After all on-premises mailboxes are migrated to Office 365, you can configure an Autodiscover DNS record for your Office 365 organization to enable users to easily connect to their new Office 365 mailboxes with Outlook and mobile clients.</span><span class="sxs-lookup"><span data-stu-id="3314c-218">After all on-premises mailboxes are migrated to Office 365, you can configure an Autodiscover DNS record for your Office 365 organization to enable users to easily connect to their new Office 365 mailboxes with Outlook and mobile clients.</span></span> <span data-ttu-id="3314c-219">This new Autodiscover DNS record has to use the same namespace that you're using for your Office 365 organization.</span><span class="sxs-lookup"><span data-stu-id="3314c-219">This new Autodiscover DNS record has to use the same namespace that you're using for your Office 365 organization.</span></span> <span data-ttu-id="3314c-220">For example, if your cloud-based namespace is cloud.contoso.com, the Autodiscover DNS record you need to create is autodiscover.cloud.contoso.com.</span><span class="sxs-lookup"><span data-stu-id="3314c-220">For example, if your cloud-based namespace is cloud.contoso.com, the Autodiscover DNS record you need to create is autodiscover.cloud.contoso.com.</span></span>
    
    <span data-ttu-id="3314c-221">Exchange Server를 유지하는 경우 Outlook 클라이언트가 올바른 사서함에 연결되도록 자동 검색 DNS CNAME 레코드는 마이그레이션 후에 내부 및 외부 DNS 둘 다에서 Office 365를 가리켜야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3314c-221">If you keep your Exchange Server, you should also make sure that Autodiscover DNS CNAME record has to point to Office 365 in both internal and external DNS after the migration so that the Outlook client will to connect to the correct mailbox.</span></span>
    
    > [!NOTE]
    >  <span data-ttu-id="3314c-222">또한 Exchange 2007, Exchange 2010 및 Exchange 2013에서  `Set-ClientAccessServer AutodiscoverInternalConnectionURI`를  `Null`로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3314c-222">In Exchange 2007, Exchange 2010, and Exchange 2013 you should also set `Set-ClientAccessServer AutodiscoverInternalConnectionURI` to `Null`.</span></span> 
  
    <span data-ttu-id="3314c-223">Office 365 uses a CNAME record to implement the Autodiscover service for Outlook and mobile clients.</span><span class="sxs-lookup"><span data-stu-id="3314c-223">Office 365 uses a CNAME record to implement the Autodiscover service for Outlook and mobile clients.</span></span> <span data-ttu-id="3314c-224">The Autodiscover CNAME record must contain the following information:</span><span class="sxs-lookup"><span data-stu-id="3314c-224">The Autodiscover CNAME record must contain the following information:</span></span>
    
  - <span data-ttu-id="3314c-225">**별칭:** autodiscover</span><span class="sxs-lookup"><span data-stu-id="3314c-225">**Alias:** autodiscover</span></span>
    
  - <span data-ttu-id="3314c-226">**대상:** autodiscover.outlook.com</span><span class="sxs-lookup"><span data-stu-id="3314c-226">**Target:** autodiscover.outlook.com</span></span>
    
    <span data-ttu-id="3314c-227">자세한 내용은 [DNS 레코드를 관리하는 경우 Office 365용 DNS 레코드 만들기](https://go.microsoft.com/fwlink/p/?LinkId=535028)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3314c-227">For more information, see [Create DNS records for Office 365 when you manage your DNS records](https://go.microsoft.com/fwlink/p/?LinkId=535028).</span></span>
    
- <span data-ttu-id="3314c-228">**Decommission on-premises Exchange servers.**</span><span class="sxs-lookup"><span data-stu-id="3314c-228">**Decommission on-premises Exchange servers.**</span></span> <span data-ttu-id="3314c-229">After you've verified that all email is being routed directly to the Office 365 mailboxes, and you no longer need to maintain your on-premises email organization or don't plan on implementing a single sign-on (SSO) solution, you can uninstall Exchange from your servers and remove your on-premises Exchange organization.</span><span class="sxs-lookup"><span data-stu-id="3314c-229">After you've verified that all email is being routed directly to the Office 365 mailboxes, and you no longer need to maintain your on-premises email organization or don't plan on implementing a single sign-on (SSO) solution, you can uninstall Exchange from your servers and remove your on-premises Exchange organization.</span></span>
    
    <span data-ttu-id="3314c-230">자세한 내용은 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="3314c-230">For more information, see the following:</span></span>
    
  - [<span data-ttu-id="3314c-231">Exchange 2010 수정 또는 제거</span><span class="sxs-lookup"><span data-stu-id="3314c-231">Modify or Remove Exchange 2010</span></span>](https://go.microsoft.com/fwlink/?LinkId=217936)
    
  - [<span data-ttu-id="3314c-232">Exchange 2007 조직 제거 방법</span><span class="sxs-lookup"><span data-stu-id="3314c-232">How to Remove an Exchange 2007 Organization</span></span>](https://go.microsoft.com/fwlink/?LinkID=100485)
    
  - [<span data-ttu-id="3314c-233">Exchange Server 2003 제거 방법</span><span class="sxs-lookup"><span data-stu-id="3314c-233">How to Uninstall Exchange Server 2003</span></span>](https://go.microsoft.com/fwlink/?LinkID=56561)
    

