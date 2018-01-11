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
ms.custom: 
ms.assetid: a20f9dbd-6102-4ffa-b72c-ff813e700930
description: "요약:Windows PowerShell을 사용하여 Office 365로 미리 구성된 마이그레이션을 수행하는 방법을 알아봅니다."
ms.openlocfilehash: 5143b039937389d965386de0e09f4f59db071c86
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/11/2018
---
# <a name="use-powershell-to-perform-a-staged-migration-to-office-365"></a><span data-ttu-id="aa8a0-103">PowerShell을 사용하여 Office 365로 미리 구성된 마이그레이션 수행</span><span class="sxs-lookup"><span data-stu-id="aa8a0-103">Use PowerShell to perform a staged migration to Office 365</span></span>

 <span data-ttu-id="aa8a0-104">**요약:** Windows PowerShell을 사용하여 Office 365로 미리 구성된 마이그레이션을 수행하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="aa8a0-104">**Summary:** Learn how to use Windows PowerShell to perform a staged migration to Office 365.</span></span>
  
<span data-ttu-id="aa8a0-105">미리 구성된 마이그레이션을 사용하여 시간에 따라 원본 전자 메일 시스템의 사용자 사서함 콘텐츠를 Office 365로 마이그레이션할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa8a0-105">You can migrate the contents of user mailboxes from a source email system to Office 365 over time using a staged migration.</span></span>
  
<span data-ttu-id="aa8a0-p101">이 문서에서는 Exchange Online PowerShell을 사용하여 미리 구성된 전자 메일 마이그레이션과 관련된 작업을 안내합니다. [Office 365로의 미리 구성된 전자 메일 마이그레이션에 대해 알아야 할 사항](https://go.microsoft.com/fwlink/p/?LinkId=536487) 항목에서는 마이그레이션 프로세스를 대략적으로 소개합니다. 이 문서 내용을 충분히 이해할 수 있으면 다음을 사용하여 다른 전자 메일 시스템으로 사서함을 마이그레이션해 보세요.</span><span class="sxs-lookup"><span data-stu-id="aa8a0-p101">This article walks you through the tasks involved with for a staged email migration using Exchange Online PowerShell. The topic, [What you need to know about a staged email migration to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536487), gives you an overview of the migration process. When you're comfortable with the contents of that article, use this one to begin migrating mailboxes from one email system to another.</span></span>
  
> [!NOTE]
> <span data-ttu-id="aa8a0-p102">Exchange 관리 센터를 사용하여 미리 구성된 마이그레이션을 수행할 수도 있습니다. [Office 365로 미리 구성된 전자 메일 마이그레이션 수행](https://go.microsoft.com/fwlink/p/?LinkId=536687)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aa8a0-p102">You can also use the Exchange admin center to perform staged migration. See [Perform a staged migration of email to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536687).</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="aa8a0-111">시작하기 전에 알아야 할 내용</span><span class="sxs-lookup"><span data-stu-id="aa8a0-111">What do you need to know before you begin?</span></span>

<span data-ttu-id="aa8a0-p103">이 작업의 예상 완료 시간: 2-5분(마이그레이션 일괄 처리 만들기에 소요되는 시간). 마이그레이션 일괄 처리가 시작되면 마이그레이션 기간은 일괄 처리의 사서함 수, 각 사서함의 크기 및 사용 가능한 네트워크 용량에 따라 달라집니다. 사서함을 Office 365로 마이그레이션하는 데 소요되는 시간에 영향을 주는 기타 요인에 대한 자세한 내용은 [마이그레이션 성능](https://go.microsoft.com/fwlink/p/?LinkId=275079)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aa8a0-p103">Estimated time to complete this task: 2-5 minutes to create a migration batch. After the migration batch is started, the duration of the migration will vary based on the number of mailboxes in the batch, the size of each mailbox, and your available network capacity. For information about other factors that affect how long it takes to migrate mailboxes to Office 365, see [Migration Performance](https://go.microsoft.com/fwlink/p/?LinkId=275079).</span></span>
  
<span data-ttu-id="aa8a0-p104">이 절차를 수행하려면 먼저 사용 권한을 할당받아야 합니다. 필요한 사용 권한을 확인하려면 [받는 사람 사용 권한](https://go.microsoft.com/fwlink/p/?LinkId=534105)의 "마이그레이션" 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aa8a0-p104">You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Migration" entry in the [Recipients Permissions](https://go.microsoft.com/fwlink/p/?LinkId=534105) topic.</span></span>
  
<span data-ttu-id="aa8a0-p105">Exchange Online PowerShell cmdlet을 사용하려면 로그인한 후 cmdlet을 로컬 Windows PowerShell 세션으로 가져와야 합니다. 해당 지침은 [원격 PowerShell을 사용하여 Exchange Online에 연결](https://go.microsoft.com/fwlink/p/?LinkId=534121)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aa8a0-p105">To use the Exchange Online PowerShell cmdlets, you need to sign in and import the cmdlets into your local Windows PowerShell session. See [Connect to Exchange Online using remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121) for instructions.</span></span>
  
<span data-ttu-id="aa8a0-119">전체 마이그레이션 명령 목록을 보려면 [이동 및 마이그레이션 cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=534750)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aa8a0-119">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
  
## <a name="migration-steps"></a><span data-ttu-id="aa8a0-120">마이그레이션 단계</span><span class="sxs-lookup"><span data-stu-id="aa8a0-120">Migration steps</span></span>

### <a name="step-1-prepare-for-a-staged-migration"></a><span data-ttu-id="aa8a0-121">1단계: 미리 구성된 마이그레이션 준비</span><span class="sxs-lookup"><span data-stu-id="aa8a0-121">Step 1: Prepare for a staged migration</span></span>

<span data-ttu-id="aa8a0-122">미리 구성된 마이그레이션을 사용하여 사서함을 Office 365로 마이그레이션하기 전에 Exchange 환경을 일부 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa8a0-122">Before you migrate mailboxes to Office 365 by using a staged migration, there are a few changes you must make to your Exchange environment.</span></span>
  
 <span data-ttu-id="aa8a0-p106">**온-프레미스에서 Exchange Server에서 Outlook Anywhere 구성** 전자 메일 마이그레이션 서비스는 Outlook Anywhere(RPC over HTTP라고도 함)를 사용하여 온-프레미스 Exchange Server에 연결합니다. Exchange Server 2007 및 Exchange 2003에 맞게 Outlook Anywhere를 설정하는 방법에 대한 자세한 내용은 다음 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aa8a0-p106">**Configure Outlook Anywhere on your on-premises Exchange Server** The email migration service uses Outlook Anywhere (also known as RPC over HTTP), to connect to your on-premises Exchange Server. For information about how to set up Outlook Anywhere for Exchange Server 2007, and Exchange 2003, see the following:</span></span>
  
- [<span data-ttu-id="aa8a0-125">Exchange 2007: "외부에서 Outlook 사용" 설정 방법</span><span class="sxs-lookup"><span data-stu-id="aa8a0-125">Exchange 2007: How to Enable Outlook Anywhere</span></span>](https://go.microsoft.com/fwlink/?LinkID=167210)
    
- [<span data-ttu-id="aa8a0-126">Exchange 2003: "외부에서 Outlook 사용" 구성 방법</span><span class="sxs-lookup"><span data-stu-id="aa8a0-126">How to configure Outlook Anywhere with Exchange 2003</span></span>](https://go.microsoft.com/fwlink/?LinkID=167209)
    
> [!IMPORTANT]
> <span data-ttu-id="aa8a0-p107">Outlook Anywhere 구성에서는 신뢰할 수 있는 CA(인증 기관)에서 발급한 인증서를 사용해야 합니다. Outlook Anywhere은 자체 서명된 인증서로 구성할 수 없습니다. 자세한 내용은 ["외부에서 Outlook 사용"에 대한 SSL 구성 방법](https://go.microsoft.com/fwlink/?LinkID=80875)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aa8a0-p107">You must use a certificate issued by a trusted certification authority (CA) with your Outlook Anywhere configuration. Outlook Anywhere can't be configured with a self-signed certificate. For more information, see [How to configure SSL for Outlook Anywhere](https://go.microsoft.com/fwlink/?LinkID=80875).</span></span> 
  
 <span data-ttu-id="aa8a0-130">**선택 사항: Outlook Anywhere을 사용하여 Exchange 조직에 연결할 수 있는지 확인** 다음 방법 중 하나를 사용하여 연결 설정을 테스트해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="aa8a0-130">**Optional: Verify that you can connect to your Exchange organization using Outlook Anywhere** Try one of the following methods to test your connection settings.</span></span>
  
- <span data-ttu-id="aa8a0-131">회사 네트워크 외부에서 Outlook을 사용하여 온-프레미스 Exchange 사서함에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="aa8a0-131">Use Outlook from outside your corporate network to connect to your on-premises Exchange mailbox.</span></span>
    
- <span data-ttu-id="aa8a0-p108">[Microsoft Exchange Remote Connectivity Analyzer](https://www.testexchangeconnectivity.com/)를 사용하여 연결 설정을 테스트합니다. Outlook Anywhere(RPC over HTTP) 또는 Outlook 자동 검색 테스트를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="aa8a0-p108">Use the [Microsoft Exchange Remote Connectivity Analyzer](https://www.testexchangeconnectivity.com/) to test your connection settings. Use the Outlook Anywhere (RPC over HTTP) or Outlook Autodiscover tests.</span></span>
    
- <span data-ttu-id="aa8a0-134">Exchange Online PowerShell에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="aa8a0-134">Run the following commands in Exchange Online PowerShell:</span></span>
    
  ```
  $Credentials = Get-Credential
  ```

  ```
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

 <span data-ttu-id="aa8a0-p109">**사용 권한 설정** 온-프레미스 Exchange 조직에 연결하는 데 사용하는 온-프레미스 계정(마이그레이션 관리자라고도 함)에는 Office 365로 마이그레이션할 온-프레미스 사서함에 액세스하는 데 필요한 권한이 있어야 합니다. 이 사용자 계정은 이 절차의 뒷부분에서 마이그레이션 끝점을 만들어 전자 메일 시스템에 연결할 때 사용됩니다([3단계: 마이그레이션 끝점 만들기](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Endpoint)).</span><span class="sxs-lookup"><span data-stu-id="aa8a0-p109">**Set permissions** The on-premises user account that you use to connect to your on-premises Exchange organization (also called the migration administrator) must have the necessary permissions to access the on-premises mailboxes that you want to migrate to Office 365. This user account is used when you connect to your email system by creating a migration endpoint later in this procedure ([Step 3: Create a migration endpoint](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Endpoint) ).</span></span>
  
<span data-ttu-id="aa8a0-137">사서함을 마이그레이션하려면 관리자는 다음 사용 권한 집합 중 하나가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa8a0-137">To migrate the mailboxes, the admin must have one of the following permission sets:</span></span>
  
- <span data-ttu-id="aa8a0-138">온-프레미스 조직의 Active Directory에 있는 **Domain Admins** 그룹의 구성원이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa8a0-138">Be a member of the **Domain Admins** group in Active Directory in the on-premises organization.</span></span>
    
    <span data-ttu-id="aa8a0-139"> 선택하거나 </span><span class="sxs-lookup"><span data-stu-id="aa8a0-139">or</span></span>
    
- <span data-ttu-id="aa8a0-140">각 온-프레미스 사서함에 대해 **FullAccess** 권한이 할당되고 온-프레미스 사용자 계정에 대해 **TargetAddress** 속성을 수정할 수 있는 **WriteProperty** 권한이 할당되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa8a0-140">Be assigned the **FullAccess** permission for each on-premises mailbox and the **WriteProperty** permission to modify the **TargetAddress** property on the on-premises user accounts.</span></span>
    
    <span data-ttu-id="aa8a0-141"> 선택하거나 </span><span class="sxs-lookup"><span data-stu-id="aa8a0-141">or</span></span>
    
- <span data-ttu-id="aa8a0-142">사용자 사서함을 저장하는 온-프레미스 사서함 데이터베이스에 대해 **다음으로 받기** 권한이 할당되고 온-프레미스 사용자 계정에 대해 **TargetAddress** 속성을 수정할 수 있는 **WriteProperty** 권한이 할당되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa8a0-142">Be assigned the **Receive As** permission on the on-premises mailbox database that stores user mailboxes and the **WriteProperty** permission to modify the **TargetAddress** property on the on-premises user accounts.</span></span>
    
<span data-ttu-id="aa8a0-143">이러한 사용 권한을 설정하는 방법에 대한 지침은 [Office 365로 사서함을 마이그레이션할 수 있는 권한 할당](https://go.microsoft.com/fwlink/?LinkId=521656)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aa8a0-143">For instructions about how to set these permissions, see [Assign permissions to migrate mailboxes to Office 365](https://go.microsoft.com/fwlink/?LinkId=521656).</span></span>
  
 <span data-ttu-id="aa8a0-p110">**UM(통합 메시징)을 사용하지 않도록 설정** 마이그레이션하려는 온-프레미스 사서함에 대해 UM이 켜져 있는 경우 마이그레이션 전에 UM을 사용하지 않도록 설정합니다. 마이그레이션이 완료된 후 사서함에 대해 UM을 켭니다. 방법 단계에 대해서는[통합 메시징을 사용하지 않도록 설정](https://go.microsoft.com/fwlink/?LinkId=521891)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aa8a0-p110">**Disable Unified Messaging (UM)** If UM is turned on for the on-premises mailboxes you're migrating, turn off UM before migration. Turn on UM for the mailboxes after migration is complete. For how-to steps, see[disable unified messaging](https://go.microsoft.com/fwlink/?LinkId=521891).</span></span>
  
 <span data-ttu-id="aa8a0-p111">**디렉터리 동기화를 사용하여 Office 365에서 새 사용자를 만듭니다.** 디렉터리 동기화를 사용하여 Office 365 조직의 모든 온-프레미스 사용자를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa8a0-p111">**Use directory synchronization to create new users in Office 365.** You use directory synchronization to create all the on-premises users in your Office 365 organization.</span></span>
  
<span data-ttu-id="aa8a0-p112">만든 사용자에게는 라이선스를 부여해야 합니다. 사용자를 만들고 30일 내에 라이선스를 추가해야 합니다. 라이선스를 추가하는 단계에 대해서는 [8단계: 마이그레이션 후 작업 완료](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Postmigration)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aa8a0-p112">You need to license the users after they're created. You have 30 days to add licenses after the users are created. For steps to add licenses, see [Step 8: Complete post-migration tasks](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Postmigration).</span></span>
  
 <span data-ttu-id="aa8a0-p113">Microsoft Azure Active Directory 동기화 도구 또는 Microsoft AAD Sync(Azure Active Directory 동기화 서비스)를 사용하여 Office 365에서 온-프레미스 사용자를 만들고 동기화할 수 있습니다. 사서함이 Office 365로 마이그레이션되면 온-프레미스 조직에서 사용자 계정을 관리하고 Office 365 조직과 동기화되도록 합니다. 자세한 내용은 [디렉터리 통합](https://go.microsoft.com/fwlink/?LinkId=521788)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aa8a0-p113">You can use either the Microsoft Azure Active Directory Synchronization Tool or the Microsoft Azure Active Directory Sync Services (AAD Sync) to synchronize and create your on-premises users in Office 365. After mailboxes are migrated to Office 365, you manage user accounts in your on-premises organization, and they're synchronized with your Office 365 organization. For more information, see[Directory Integration](https://go.microsoft.com/fwlink/?LinkId=521788) .</span></span>
  
### <a name="step-2-create-a-csv-file-for-a-staged-migration-batch"></a><span data-ttu-id="aa8a0-155">2단계: 미리 구성된 마이그레이션 일괄 처리에 대한 CSV 파일 만들기</span><span class="sxs-lookup"><span data-stu-id="aa8a0-155">Step 2: Create a CSV file for a staged migration batch</span></span>

<span data-ttu-id="aa8a0-p114">Office 365로 온-프레미스 사서함을 마이그레이션할 사용자를 확인한 후 CSV(쉼표로 구분된 값) 파일을 사용하여 마이그레이션 일괄 처리를 만듭니다. Office 365에서 마이그레이션을 실행하는 데 사용하는 CSV 파일의 각 행에는 온-프레미스 사서함에 대한 정보가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa8a0-p114">After you identify the users whose on-premises mailboxes you want to migrate to Office 365, you use a comma separated value (CSV ) file to create a migration batch. Each row in the CSV file—used by Office 365 to run the migration—contains information about an on-premises mailbox.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="aa8a0-p115">미리 구성된 마이그레이션을 사용하여 Office 365으로 마이그레이션할 수 있는 사서함의 수에는 제한이 없습니다. 마이그레이션 일괄 처리용 CSV 파일에는 최대 2,000개 행을 포함할 수 있습니다. 2,000개가 넘는 사서함을 마이그레이션하려면 CSV 파일을 추가로 만든 다음 각 파일을 사용하여 새 마이그레이션 일괄 처리를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa8a0-p115">There isn't a limit for the number of mailboxes that you can migrate to Office 365 using a staged migration. The CSV file for a migration batch can contain a maximum of 2,000 rows. To migrate more than 2,000 mailboxes, create additional CSV files and use each file to create a new migration batch.</span></span> 
  
 <span data-ttu-id="aa8a0-161">**지원되는 특성**</span><span class="sxs-lookup"><span data-stu-id="aa8a0-161">**Supported attributes**</span></span>
  
<span data-ttu-id="aa8a0-p116">미리 구성된 마이그레이션용 CSV 파일에는 다음과 같은 세 개의 특성이 지원됩니다. CSV 파일의 각 행은 하나의 사서함에 해당하며 이러한 각 특성에 대한 값을 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa8a0-p116">The CSV file for a staged migration supports the following three attributes. Each row in the CSV file corresponds to a mailbox and must contain a value for each of these attributes.</span></span>
  
|<span data-ttu-id="aa8a0-164">**특성**</span><span class="sxs-lookup"><span data-stu-id="aa8a0-164">**Attribute**</span></span>|<span data-ttu-id="aa8a0-165">**설명**</span><span class="sxs-lookup"><span data-stu-id="aa8a0-165">**Description**</span></span>|<span data-ttu-id="aa8a0-166">**필수 여부**</span><span class="sxs-lookup"><span data-stu-id="aa8a0-166">**Required?**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="aa8a0-167">EmailAddress</span><span class="sxs-lookup"><span data-stu-id="aa8a0-167">EmailAddress</span></span>  <br/> |<span data-ttu-id="aa8a0-168">온-프레미스 사서함에 대한 기본 SMTP 전자 메일 주소(예: pilarp@contoso.com)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="aa8a0-168">Specifies the primary SMTP email address, for example, pilarp@contoso.com, for on-premises mailboxes.</span></span>  <br/> <span data-ttu-id="aa8a0-p117">온-프레미스 사서함에 대해서는 Office 365의 사용자 ID가 아닌 기본 SMTP 주소를 사용합니다. 예를 들어 온-프레미스 도메인의 이름이 contoso.com이고 Office 365 전자 메일 도메인의 이름이 service.contoso.com인 경우 CSV 파일의 전자 메일 주소에 contoso.com 도메인 이름을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa8a0-p117">Use the primary SMTP address for on-premises mailboxes and not user IDs from the Office 365. For example, if the on-premises domain is named contoso.com but the Office 365 email domain is named service.contoso.com, you would use the contoso.com domain name for email addresses in the CSV file.</span></span>  <br/> |<span data-ttu-id="aa8a0-171">필수</span><span class="sxs-lookup"><span data-stu-id="aa8a0-171">Required</span></span>  <br/> |
|<span data-ttu-id="aa8a0-172">암호</span><span class="sxs-lookup"><span data-stu-id="aa8a0-172">Password</span></span>  <br/> |<span data-ttu-id="aa8a0-p118">새 Office 365 사서함에 대해 설정할 암호입니다. Office 365 조직에 적용되는 암호 제한은 CSV 파일에 포함된 암호에도 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa8a0-p118">The password to be set for the new Office 365 mailbox. Any password restrictions that are applied to your Office 365 organization also apply to the passwords included in the CSV file.</span></span>  <br/> |<span data-ttu-id="aa8a0-175">옵션</span><span class="sxs-lookup"><span data-stu-id="aa8a0-175">Optional</span></span>  <br/> |
|<span data-ttu-id="aa8a0-176">ForceChangePassword</span><span class="sxs-lookup"><span data-stu-id="aa8a0-176">ForceChangePassword</span></span>  <br/> |<span data-ttu-id="aa8a0-p119">사용자가 새 Office 365 사서함에 처음 로그인할 때 암호를 변경해야 하는지 여부를 지정합니다. 이 매개 변수 값으로는 **True** 또는 **False** 를 사용합니다. </span><span class="sxs-lookup"><span data-stu-id="aa8a0-p119">Specifies whether a user must change the password the first time they sign in to their new Office 365 mailbox. Use **True** or **False** for the value of this parameter. </span></span><br/> <span data-ttu-id="aa8a0-179">> [!NOTE]> 온-프레미스 조직에서 AD FS(Active Directory Federation Services)를 배포하여 SSO(Single Sign-On) 솔루션을 구현한 경우 **ForceChangePassword** 특성 값으로 **False** 를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa8a0-179">> [!NOTE]> If you've implemented a single sign-on (SSO) solution by deploying Active Directory Federation Services (AD FS) or greater in your on-premises organization, you must use **False** for the value of the **ForceChangePassword** attribute.</span></span>          |<span data-ttu-id="aa8a0-180">옵션</span><span class="sxs-lookup"><span data-stu-id="aa8a0-180">Optional</span></span>  <br/> |
   
 <span data-ttu-id="aa8a0-181">**CSV 파일 형식**</span><span class="sxs-lookup"><span data-stu-id="aa8a0-181">**CSV file format**</span></span>
  
<span data-ttu-id="aa8a0-p120">다음은 CSV 파일 형식의 예입니다. 이 예에서는 온-프레미스 사서함 세 개를 Office 365으로 마이그레이션합니다.</span><span class="sxs-lookup"><span data-stu-id="aa8a0-p120">Here's an example of the format for the CSV file. In this example, three on-premises mailboxes are migrated to Office 365.</span></span>
  
<span data-ttu-id="aa8a0-p121">CSV 파일의 첫 번째 행(머리글 행)에는 그 다음 행들에 지정된 특성 또는 필드의 이름이 나열됩니다. 각 특성 이름은 쉼표로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa8a0-p121">The first row, or header row, of the CSV file lists the names of the attributes, or fields, specified in the rows that follow. Each attribute name is separated by a comma.</span></span>
  
```
EmailAddress,Password,ForceChangePassword 
pilarp@contoso.com,Pa$$w0rd,False 
tobyn@contoso.com,Pa$$w0rd,False 
briant@contoso.com,Pa$$w0rd,False 
```

<span data-ttu-id="aa8a0-p122">머리글 행 아래의 각 행은 한 명의 사용자를 나타내며 해당 사용자의 사서함을 마이그레이션하기 위해 사용되는 정보를 제공합니다. 각 행의 특성 값은 머리글 행의 특성 이름과 동일한 순서로 나열되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa8a0-p122">Each row under the header row represents one user and supplies the information that will be used to migrate the user's mailbox. The attribute values in each row must be in the same order as the attribute names in the header row.</span></span> 
  
<span data-ttu-id="aa8a0-p123">텍스트 편집기 또는 Excel 등의 응용 프로그램을 사용하여 CSV 파일을 만들 수 있습니다. 파일을 .csv 또는 .txt 파일로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="aa8a0-p123">Use any text editor, or an application like Excel , to create the CSV file. Save the file as a .csv or .txt file.</span></span>
  
> [!NOTE]
> <span data-ttu-id="aa8a0-p124">CSV 파일에 ASCII가 아닌 문자 또는 특수 문자가 포함되어 있는 경우에는 CSV 파일을 UTF-8 또는 다른 유니코드 인코딩으로 저장합니다. 응용 프로그램에 따라 컴퓨터의 시스템 로캘이 CSV 파일에 사용된 언어와 일치하는 경우 CSV 파일을 UTF-8 또는 다른 유니코드 인코딩으로 저장하는 것이 보다 간단할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa8a0-p124">If the CSV file contains non-ASCII or special characters, save the CSV file with UTF-8 or other Unicode encoding. Depending on the application, saving the CSV file with UTF-8 or other Unicode encoding can be easier when the system locale of the computer matches the language used in the CSV file.</span></span> 
  
### <a name="step-3-create-a-migration-endpoint"></a><span data-ttu-id="aa8a0-192">3단계: 마이그레이션 끝점 만들기</span><span class="sxs-lookup"><span data-stu-id="aa8a0-192">Step 3: Create a migration endpoint</span></span>
<span data-ttu-id="aa8a0-193"><a name="BK_Endpoint"> </a></span><span class="sxs-lookup"><span data-stu-id="aa8a0-193"><a name="BK_Endpoint"> </a></span></span>

<span data-ttu-id="aa8a0-p125">전자 메일을 마이그레이션하기 위해 Office 365는 원본 전자 메일 시스템에 연결하고 통신해야 합니다. 이를 위해 Office 365에서는 마이그레이션 끝점을 사용합니다. PowerShell을 사용하여 "외부에서 Outlook 사용" 마이그레이션 끝점을 만들려면 미리 구성된 마이그레이션에 대해 먼저 [Exchange Online에 연결](https://go.microsoft.com/fwlink/p/?LinkId=534121)합니다.</span><span class="sxs-lookup"><span data-stu-id="aa8a0-p125">To migrate email successfully, Office 365 needs to connect and communicate with the source email system. To do this, Office 365 uses a migration endpoint. To create an Outlook Anywhere migration endpoint by using PowerShell, for staged migration, first [connect to Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span></span> 
  
<span data-ttu-id="aa8a0-197">전체 마이그레이션 명령 목록을 보려면 [이동 및 마이그레이션 cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=534750)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aa8a0-197">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
  
<span data-ttu-id="aa8a0-198">Exchange Online PowerShell에서 "StagedEndpoint"라는 Outlook Anywhere 마이그레이션 끝점을 만들려면 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="aa8a0-198">To create an Outlook Anywhere migration endpoint called "StagedEndpoint" in Exchange Online PowerShell, run the following commands:</span></span>
  
```
$Credentials = Get-Credential
```

```
New-MigrationEndpoint -ExchangeOutlookAnywhere -Name StagedEndpoint -Autodiscover -EmailAddress administrator@contoso.com -Credentials $Credentials
```

<span data-ttu-id="aa8a0-199">**New-MigrationEndpoint** cmdlet에 대한 자세한 내용은[New-MigrationEndpoint](https://go.microsoft.com/fwlink/p/?LinkId=536437)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aa8a0-199">For more information about the **New-MigrationEndpoint** cmdlet, see[New-MigrationEndpoint](https://go.microsoft.com/fwlink/p/?LinkId=536437).</span></span>
  
> [!NOTE]
> <span data-ttu-id="aa8a0-p126">**New-MigrationEndpoint** cmdlet을 사용하여 **-TargetDatabase** 옵션을 통해 서비스에서 사용할 데이터베이스를 지정할 수 있습니다. 그렇지 않으면 데이터베이스는 관리 사서함이 있는 AD FS(Active Directory Federation Services) 2.0 사이트에서 임의로 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa8a0-p126">The **New-MigrationEndpoint** cmdlet can be used to specify a database for the service to use by using the **-TargetDatabase** option. Otherwise a database is randomly assigned from the Active Directory Federation Services (AD FS) 2.0 site where the management mailbox is located.</span></span>
  
#### <a name="verify-it-worked"></a><span data-ttu-id="aa8a0-202">작동하는지 확인</span><span class="sxs-lookup"><span data-stu-id="aa8a0-202">Verify it worked</span></span>

<span data-ttu-id="aa8a0-203">Exchange Online PowerShell에서 다음 명령을 실행하여 "StagedEndpoint" 마이그레이션 끝점에 대한 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="aa8a0-203">In Exchange Online PowerShell, run the following command to display information about the "StagedEndpoint" migration endpoint:</span></span>
  
```
Get-MigrationEndpoint StagedEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*
```

### <a name="step-4-create-and-start-a-stage-migration-batch"></a><span data-ttu-id="aa8a0-204">4단계: 미리 구성된 마이그레이션 일괄 처리 만들기 및 시작</span><span class="sxs-lookup"><span data-stu-id="aa8a0-204">Step 4: Create and start a stage migration batch</span></span>
<span data-ttu-id="aa8a0-205"><a name="BK_Endpoint"> </a></span><span class="sxs-lookup"><span data-stu-id="aa8a0-205"><a name="BK_Endpoint"> </a></span></span>

<span data-ttu-id="aa8a0-p127">Exchange Online PowerShell에서 **New-MigrationBatch** cmdlet을 사용하여 단독형 마이그레이션을 위한 마이그레이션 일괄 처리를 만들 수 있습니다. _AutoStart_ 매개 변수를 포함하면 마이그레이션 일괄 처리를 만들고 자동으로 시작할 수 있습니다. 또는 마이그레이션 일괄 처리를 만들고 **Start-MigrationBatch** cmdlet을 사용하여 나중에 마이그레이션을 수동으로 시작할 수 있습니다. 이 예에서는 "StagedBatch1"이라는 마이그레이션 일괄 처리를 만든 다음 이전 예에서 만든 마이그레이션 끝점을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="aa8a0-p127">You can use the **New-MigrationBatch** cmdlet in Exchange Online PowerShell to create a migration batch for a cutover migration. You can create a migration batch and start it automatically by including the _AutoStart_ parameter. Alternatively, you can create the migration batch and then manually start it afterwards by using the **Start-MigrationBatch** cmdlet. This example creates a migration batch called "StagedBatch1" and uses the migration endpoint that was created in the previous step.</span></span>
  
```
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint -AutoStart
```

<span data-ttu-id="aa8a0-p128">또한 이 예에서는 "StagedBatch1"이라는 마이그레이션 일괄 처리를 만든 다음 이전 예에서 만든 마이그레이션 끝점을 사용합니다.  _AutoStart_ 매개 변수가 포함되지 않으므로 마이그레이션 일괄 처리가 마이그레이션 대시보드나 **Start-MigrationBatch** cmdlet을 사용하여 수동으로 시작되어야 합니다. 앞서 설명했듯이 단독형 마이그레이션 일괄 처리는 한 번에 하나만 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa8a0-p128">This example also creates a migration batch called "StagedBatch1" and uses the migration endpoint that was created in the previous step. Because the  _AutoStart_ parameter isn't included, the migration batch has to be manually started on the migration dashboard or by using **Start-MigrationBatch** cmdlet. As previously stated, only one cutover migration batch can exist at a time.</span></span>
  
```
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint
```

#### <a name="verify-it-worked"></a><span data-ttu-id="aa8a0-213">작동하는지 확인</span><span class="sxs-lookup"><span data-stu-id="aa8a0-213">Verify it worked</span></span>

<span data-ttu-id="aa8a0-214">Exchange Online PowerShell에서 다음 명령을 실행하여 "StagedBatch1"에 대한 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="aa8a0-214">Run the following command in Exchange Online PowerShell to display information about the "StagedBatch1":</span></span>
  
```
Get-MigrationBatch -Identity StagedBatch1 | Format-List
```

<span data-ttu-id="aa8a0-215">다음 명령을 실행하여 일괄 처리가 시작되었는지 확인할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa8a0-215">You can also verify that the batch has started by running the following command:</span></span>
  
```
Get-MigrationBatch -Identity StagedBatch1 | Format-List Status
```

<span data-ttu-id="aa8a0-216">**Get-MigrationBatch** cmdlet에 대한 자세한 내용은[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aa8a0-216">For more information about the **Get-MigrationBatch** cmdlet, see[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441).</span></span>
  
### <a name="step-5-convert-on-premises-mailboxes-to-mail-enabled-users"></a><span data-ttu-id="aa8a0-217">5단계: 온-프레미스 사서함을 메일 사용 가능 사용자로 변환</span><span class="sxs-lookup"><span data-stu-id="aa8a0-217">Step 5: Convert on-premises mailboxes to mail-enabled users</span></span>
<span data-ttu-id="aa8a0-218"><a name="BK_Endpoint"> </a></span><span class="sxs-lookup"><span data-stu-id="aa8a0-218"><a name="BK_Endpoint"> </a></span></span>

<span data-ttu-id="aa8a0-p129">사서함 일괄 처리를 마이그레이션한 후에는 다른 사용자가 해당 메일에 액세스할 수 있도록 해야 합니다. 사서함이 마이그레이션된 사용자는 온-프레미스 및 Office 365 둘 다에 사서함이 존재하게 됩니다. Office 365에 사서함이 있는 사용자는 더 이상 온-프레미스 사서함에 새 메일이 수신되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="aa8a0-p129">After you have successfully migrated a batch of mailboxes, you need some way to let users get to their mail. A user whose mailbox has been migrated now has both a mailbox on-premises and one in Office 365. Users who have a mailbox in Office 365 will stop receiving new mail in their on-premises mailbox.</span></span> 
  
<span data-ttu-id="aa8a0-p130">마이그레이션을 완료하지 않았으므로 아직 모든 사용자가 본인의 전자 메일을 받기 위해 Office 365으로 이동되도록 하면 안 됩니다. 그렇다면 두 위치에 사서함을 모두 보유하는 사용자의 경우는 어떻게 해야 할까요? 메일 사용 가능 사용자로 이미 마이그레이션한 온-프레미스 사서함을 변경할 수 있습니다. 사서함에서 메일 사용 가능 사용자로 변경할 경우 사용자가 본인의 전자 메일을 받기 위해 해당 온-프레미스 사서함이 아닌 Office 365로 이동되도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa8a0-p130">Because you are not done with your migrations, you are not yet ready to direct all users to Office 365 for their email. So what do you do for those people who have both? What you can do is change the on-premises mailboxes that you've already migrated to mail-enabled users. When you change from a mailbox to a mail-enabled user, you can direct the user to Office 365 for their email instead of going to their on-premises mailbox.</span></span> 
  
<span data-ttu-id="aa8a0-p131">온-프레미스 사서함을 메일 사용 가능 사용자로 변환하는 다른 중요한 이유는 프록시 주소를 메일 사용 가능 사용자로 복사하여 Office 365 사서함의 프록시 주소를 보존하는 것입니다. 이렇게 하면 Active Directory를 사용하여 온-프레미스 조직의 클라우드(Cloud) 기반 사용자를 관리할 수 있습니다. 또한 모든 사서함이 Office 365으로 마이그레이션된 후 온-프레미스 Exchange Server 조직을 제거하면 메일 사용 가능한 사용자로 복사한 프록시 주소가 온-프레미스 Active Directory에 남아 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa8a0-p131">Another important reason to convert on-premises mailboxes to mail-enabled users is to retain proxy addresses from the Office 365 mailboxes by copying proxy addresses to the mail-enabled users. This lets you manage cloud-based users from your on-premises organization by using Active Directory. Also, if you decide to decommission your on-premises Exchange Server organization after all mailboxes are migrated to Office 365, the proxy addresses you've copied to the mail-enabled users will remain in your on-premises Active Directory.</span></span>
  
<span data-ttu-id="aa8a0-229">자세한 내용을 보고 사서함을 메일 사용이 가능한 사용자로 변환하기 위해 실행할 수 있는 스크립트를 다운로드하려면 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aa8a0-229">For more information, and to download scripts that you can run to convert mailboxes to mail-enabled users, see the following:</span></span>
  
- [<span data-ttu-id="aa8a0-230">Exchange 2007 사서함을 메일 사용이 가능한 사용자로 변환</span><span class="sxs-lookup"><span data-stu-id="aa8a0-230">Convert Exchange 2007 mailboxes to mail-enabled users</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=233648)
    
- [<span data-ttu-id="aa8a0-231">Exchange 2003 사서함을 메일 사용이 가능한 사용자로 변환</span><span class="sxs-lookup"><span data-stu-id="aa8a0-231">Convert Exchange 2003 mailboxes to mail-enabled users</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=233647)
    
### <a name="step-6-delete-a-staged-migration-batch"></a><span data-ttu-id="aa8a0-232">6단계: 미리 구성된 마이그레이션 일괄 처리 삭제</span><span class="sxs-lookup"><span data-stu-id="aa8a0-232">Step 6: Delete a staged migration batch</span></span>
<span data-ttu-id="aa8a0-233"><a name="BK_Endpoint"> </a></span><span class="sxs-lookup"><span data-stu-id="aa8a0-233"><a name="BK_Endpoint"> </a></span></span>

 <span data-ttu-id="aa8a0-p132">마이그레이션 일괄 처리에 포함된 모든 사서함이 마이그레이션되었고 일괄 처리에 있는 온-프레미스 사서함이 메일 사용 가능 사용자로 변환되면 미리 구성된 마이그레이션 일괄 처리를 삭제할 수 있습니다. 메일이 마이그레이션 일괄 처리의 Office 365 사서함으로 전달 중인지 확인하세요. 미리 구성된 마이그레이션 일괄 처리를 삭제하면 마이그레이션 서비스에서 마이그레이션 일괄 처리와 관련된 모든 레코드를 정리하고 마이그레이션 일괄 처리를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="aa8a0-p132">After all mailboxes in a migration batch have been successfully migrated, and you've converted the on-premises mailboxes in the batch to mail-enabled users, you're ready to delete a staged migration batch. Be sure to verify that mail is being forwarded to the Office 365 mailboxes in the migration batch. When you delete a staged migration batch, the migration service cleans up any records related to the migration batch and deletes the migration batch.</span></span>
  
<span data-ttu-id="aa8a0-237">Exchange Online PowerShell에서 "StagedBatch1" 마이그레이션 일괄 처리를 삭제하려면 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="aa8a0-237">To delete the "StagedBatch1" migration batch in Exchange Online PowerShell, run the following command.</span></span>
  
```
Remove-MigrationBatch -Identity StagedBatch1
```

<span data-ttu-id="aa8a0-238">**Remove-MigrationBatch** cmdlet에 대한 자세한 내용은[Remove-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536481)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aa8a0-238">For more information about the **Remove-MigrationBatch** cmdlet, see[Remove-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536481).</span></span>
  
#### <a name="verify-it-worked"></a><span data-ttu-id="aa8a0-239">작동하는지 확인</span><span class="sxs-lookup"><span data-stu-id="aa8a0-239">Verify it worked</span></span>

<span data-ttu-id="aa8a0-240">Exchange Online PowerShell에서 다음 명령을 실행하여 "IMAPBatch1"에 대한 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="aa8a0-240">Run the following command in Exchange Online PowerShell to display information about the "IMAPBatch1":</span></span>
  
```
Get-MigrationBatch StagedBatch1
```

<span data-ttu-id="aa8a0-241">이 명령을 실행하면 상태가 **제거 중** 인 마이그레이션 일괄 처리가 반환되거나, 마이그레이션 일괄 처리를 찾을 수 없다는 오류가 반환됩니다. 이 경우 해당 일괄 처리가 삭제되었음을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa8a0-241">The command will return either the migration batch with a status of **Removing**, or it will return an error stating that migration batch couldn't be found, verifying that the batch was deleted.</span></span>
  
<span data-ttu-id="aa8a0-242">**Get-MigrationBatch** cmdlet에 대한 자세한 내용은[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aa8a0-242">For more information about the **Get-MigrationBatch** cmdlet, see[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441).</span></span>
  
### <a name="step7-assign-licenses-to-office-365-users"></a><span data-ttu-id="aa8a0-243">7단계: Office 365 사용자에게 라이선스 할당</span><span class="sxs-lookup"><span data-stu-id="aa8a0-243">Step7: Assign licenses to Office 365 users</span></span>
<span data-ttu-id="aa8a0-244"><a name="BK_Endpoint"> </a></span><span class="sxs-lookup"><span data-stu-id="aa8a0-244"><a name="BK_Endpoint"> </a></span></span>

<span data-ttu-id="aa8a0-p133">라이선스를 할당하여 마이그레이션된 계정에 대한 Office 365 사용자 계정을 활성화합니다. 라이선스를 할당하지 않은 경우 30일의 유예 기간이 끝나면 사서함을 사용할 수 없습니다. Office 365 관리 센터에서 라이선스를 할당하려면 [비즈니스용 Office 365 라이선스 할당 또는 할당 취소](https://go.microsoft.com/fwlink/?LinkId=536681)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aa8a0-p133">Activate Office 365 user accounts for the migrated accounts by assigning licenses. If you don't assign a license, the mailbox is disabled when the grace period (30 days) ends. To assign a license in the Office 365 admin center, see [Assign or unassign licenses for Office 365 for business](https://go.microsoft.com/fwlink/?LinkId=536681).</span></span>
  
### <a name="step-8-complete-post-migration-tasks"></a><span data-ttu-id="aa8a0-248">8단계: 마이그레이션 후 작업 완료</span><span class="sxs-lookup"><span data-stu-id="aa8a0-248">Step 8: Complete post-migration tasks</span></span>
<span data-ttu-id="aa8a0-249"><a name="BK_Postmigration"> </a></span><span class="sxs-lookup"><span data-stu-id="aa8a0-249"><a name="BK_Postmigration"> </a></span></span>

- <span data-ttu-id="aa8a0-p134">**사용자가 자신의 사서함으로 쉽게 이동할 수 있도록 자동 검색 DNS 레코드를 만듭니다.** 모든 온-프레미스 사서함이 Office 365로 마이그레이션된 후에는 사용자가 Outlook 및 모바일 클라이언트를 사용하여 새 Office 365 사서함에 쉽게 연결할 수 있도록 Office 365 조직에 대한 자동 검색 DNS 레코드를 구성할 수 있습니다. 이 새로운 자동 검색 DNS 레코드에서는 Office 365 조직에 사용 중인 동일한 네임스페이스를 사용해야 합니다. 예를 들어 클라우드(Cloud) 기반 네임스페이스가 cloud.contoso.com인 경우 만들어야 할 자동 검색 DNS 레코드는 autodiscover.cloud.contoso.com입니다.</span><span class="sxs-lookup"><span data-stu-id="aa8a0-p134">**Create an Autodiscover DNS record so users can easily get to their mailboxes.** After all on-premises mailboxes are migrated to Office 365, you can configure an Autodiscover DNS record for your Office 365 organization to enable users to easily connect to their new Office 365 mailboxes with Outlook and mobile clients. This new Autodiscover DNS record has to use the same namespace that you're using for your Office 365 organization. For example, if your cloud-based namespace is cloud.contoso.com, the Autodiscover DNS record you need to create is autodiscover.cloud.contoso.com.</span></span>
    
    <span data-ttu-id="aa8a0-p135">Office 365는 CNAME 레코드를 사용하여 Outlook 및 모바일 클라이언트에 대한 자동 검색 서비스를 구현합니다. Autodiscover CNAME 레코드에는 다음과 같은 정보가 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa8a0-p135">Office 365 uses a CNAME record to implement the Autodiscover service for Outlook and mobile clients. The Autodiscover CNAME record must contain the following information:</span></span>
    
  - <span data-ttu-id="aa8a0-256">**별칭:** autodiscover</span><span class="sxs-lookup"><span data-stu-id="aa8a0-256">**Alias:** autodiscover</span></span>
    
  - <span data-ttu-id="aa8a0-257">**대상:** autodiscover.outlook.com</span><span class="sxs-lookup"><span data-stu-id="aa8a0-257">**Target:** autodiscover.outlook.com</span></span>
    
    <span data-ttu-id="aa8a0-258">자세한 내용은 [DNS 레코드를 관리하는 경우 Office 365용 DNS 레코드 만들기](https://go.microsoft.com/fwlink/p/?LinkId=535028)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aa8a0-258">For more information, see [Create DNS records for Office 365 when you manage your DNS records](https://go.microsoft.com/fwlink/p/?LinkId=535028).</span></span>
    
- <span data-ttu-id="aa8a0-p136">**온-프레미스 Exchange 서버를 해제합니다.** 모든 전자 메일이 Office 365 사서함으로 직접 라우팅됨을 확인하고 온-프레미스 전자 메일 조직을 더 이상 유지 관리할 필요가 없거나 SSO 솔루션을 구현하지 않으려는 경우에는 서버에서 Exchange를 제거하고 온-프레미스 Exchange 조직을 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa8a0-p136">**Decommission on-premises Exchange servers.** After you've verified that all email is being routed directly to the Office 365 mailboxes, and you no longer need to maintain your on-premises email organization or don't plan on implementing an SSO solution, you can uninstall Exchange from your servers and remove your on-premises Exchange organization.</span></span>
    
    <span data-ttu-id="aa8a0-261">자세한 내용은 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="aa8a0-261">For more information, see the following:</span></span>
    
  - [<span data-ttu-id="aa8a0-262">Exchange 2010 수정 또는 제거</span><span class="sxs-lookup"><span data-stu-id="aa8a0-262">Modify or Remove Exchange 2010</span></span>](https://go.microsoft.com/fwlink/?LinkId=217936)
    
  - [<span data-ttu-id="aa8a0-263">Exchange 2007 조직 제거 방법</span><span class="sxs-lookup"><span data-stu-id="aa8a0-263">How to Remove an Exchange 2007 Organization</span></span>](https://go.microsoft.com/fwlink/?LinkID=100485)
    
  - [<span data-ttu-id="aa8a0-264">Exchange Server 2003 제거 방법</span><span class="sxs-lookup"><span data-stu-id="aa8a0-264">How to Uninstall Exchange Server 2003</span></span>](https://go.microsoft.com/fwlink/?LinkID=56561)
    

