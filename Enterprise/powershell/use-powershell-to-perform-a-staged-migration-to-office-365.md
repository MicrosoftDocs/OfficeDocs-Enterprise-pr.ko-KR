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
# <a name="use-powershell-to-perform-a-staged-migration-to-office-365"></a><span data-ttu-id="d2da2-103">PowerShell을 사용하여 Office 365로 미리 구성된 마이그레이션 수행</span><span class="sxs-lookup"><span data-stu-id="d2da2-103">Use PowerShell to perform a staged migration to Office 365</span></span>

<span data-ttu-id="d2da2-104">미리 구성된 마이그레이션을 사용하여 시간에 따라 원본 전자 메일 시스템의 사용자 사서함 콘텐츠를 Office 365로 마이그레이션할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2da2-104">You can migrate the contents of user mailboxes from a source email system to Office 365 over time using a staged migration.</span></span>
  
<span data-ttu-id="d2da2-105">This article walks you through the tasks involved with for a staged email migration using Exchange Online PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d2da2-105">This article walks you through the tasks involved with for a staged email migration using Exchange Online PowerShell.</span></span> <span data-ttu-id="d2da2-106">The topic, [What you need to know about a staged email migration to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536487), gives you an overview of the migration process.</span><span class="sxs-lookup"><span data-stu-id="d2da2-106">The topic, [What you need to know about a staged email migration to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536487), gives you an overview of the migration process.</span></span> <span data-ttu-id="d2da2-107">When you're comfortable with the contents of that article, use this one to begin migrating mailboxes from one email system to another.</span><span class="sxs-lookup"><span data-stu-id="d2da2-107">When you're comfortable with the contents of that article, use this one to begin migrating mailboxes from one email system to another.</span></span>
  
> [!NOTE]
> <span data-ttu-id="d2da2-108">You can also use the Exchange admin center to perform staged migration.</span><span class="sxs-lookup"><span data-stu-id="d2da2-108">You can also use the Exchange admin center to perform staged migration.</span></span> <span data-ttu-id="d2da2-109">See [Perform a staged migration of email to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536687).</span><span class="sxs-lookup"><span data-stu-id="d2da2-109">See [Perform a staged migration of email to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536687).</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="d2da2-110">시작하기 전에 알아야 할 내용</span><span class="sxs-lookup"><span data-stu-id="d2da2-110">What do you need to know before you begin?</span></span>

<span data-ttu-id="d2da2-111">Estimated time to complete this task: 2-5 minutes to create a migration batch.</span><span class="sxs-lookup"><span data-stu-id="d2da2-111">Estimated time to complete this task: 2-5 minutes to create a migration batch.</span></span> <span data-ttu-id="d2da2-112">After the migration batch is started, the duration of the migration will vary based on the number of mailboxes in the batch, the size of each mailbox, and your available network capacity.</span><span class="sxs-lookup"><span data-stu-id="d2da2-112">After the migration batch is started, the duration of the migration will vary based on the number of mailboxes in the batch, the size of each mailbox, and your available network capacity.</span></span> <span data-ttu-id="d2da2-113">For information about other factors that affect how long it takes to migrate mailboxes to Office 365, see [Migration Performance](https://go.microsoft.com/fwlink/p/?LinkId=275079).</span><span class="sxs-lookup"><span data-stu-id="d2da2-113">For information about other factors that affect how long it takes to migrate mailboxes to Office 365, see [Migration Performance](https://go.microsoft.com/fwlink/p/?LinkId=275079).</span></span>
  
<span data-ttu-id="d2da2-114">You need to be assigned permissions before you can perform this procedure or procedures.</span><span class="sxs-lookup"><span data-stu-id="d2da2-114">You need to be assigned permissions before you can perform this procedure or procedures.</span></span> <span data-ttu-id="d2da2-115">To see what permissions you need, see the "Migration" entry in the [Recipients Permissions](https://go.microsoft.com/fwlink/p/?LinkId=534105) topic.</span><span class="sxs-lookup"><span data-stu-id="d2da2-115">To see what permissions you need, see the "Migration" entry in the [Recipients Permissions](https://go.microsoft.com/fwlink/p/?LinkId=534105) topic.</span></span>
  
<span data-ttu-id="d2da2-116">To use the Exchange Online PowerShell cmdlets, you need to sign in and import the cmdlets into your local Windows PowerShell session.</span><span class="sxs-lookup"><span data-stu-id="d2da2-116">To use the Exchange Online PowerShell cmdlets, you need to sign in and import the cmdlets into your local Windows PowerShell session.</span></span> <span data-ttu-id="d2da2-117">See [Connect to Exchange Online using remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121) for instructions.</span><span class="sxs-lookup"><span data-stu-id="d2da2-117">See [Connect to Exchange Online using remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121) for instructions.</span></span>
  
<span data-ttu-id="d2da2-118">전체 마이그레이션 명령 목록을 보려면 [이동 및 마이그레이션 cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=534750)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d2da2-118">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
  
## <a name="migration-steps"></a><span data-ttu-id="d2da2-119">마이그레이션 단계</span><span class="sxs-lookup"><span data-stu-id="d2da2-119">Migration steps</span></span>

### <a name="step-1-prepare-for-a-staged-migration"></a><span data-ttu-id="d2da2-120">1단계: 미리 구성된 마이그레이션 준비</span><span class="sxs-lookup"><span data-stu-id="d2da2-120">Step 1: Prepare for a staged migration</span></span>

<span data-ttu-id="d2da2-121">미리 구성된 마이그레이션을 사용하여 사서함을 Office 365로 마이그레이션하기 전에 Exchange 환경을 일부 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2da2-121">Before you migrate mailboxes to Office 365 by using a staged migration, there are a few changes you must make to your Exchange environment.</span></span>
  
 <span data-ttu-id="d2da2-122">**Configure Outlook Anywhere on your on-premises Exchange Server** The email migration service uses Outlook Anywhere (also known as RPC over HTTP), to connect to your on-premises Exchange Server.</span><span class="sxs-lookup"><span data-stu-id="d2da2-122">**Configure Outlook Anywhere on your on-premises Exchange Server** The email migration service uses Outlook Anywhere (also known as RPC over HTTP), to connect to your on-premises Exchange Server.</span></span> <span data-ttu-id="d2da2-123">For information about how to set up Outlook Anywhere for Exchange Server 2007, and Exchange 2003, see the following:</span><span class="sxs-lookup"><span data-stu-id="d2da2-123">For information about how to set up Outlook Anywhere for Exchange Server 2007, and Exchange 2003, see the following:</span></span>
  
- [<span data-ttu-id="d2da2-124">Exchange 2007: "외부에서 Outlook 사용" 설정 방법</span><span class="sxs-lookup"><span data-stu-id="d2da2-124">Exchange 2007: How to Enable Outlook Anywhere</span></span>](https://go.microsoft.com/fwlink/?LinkID=167210)
    
- [<span data-ttu-id="d2da2-125">Exchange 2003: "외부에서 Outlook 사용" 구성 방법</span><span class="sxs-lookup"><span data-stu-id="d2da2-125">How to configure Outlook Anywhere with Exchange 2003</span></span>](https://go.microsoft.com/fwlink/?LinkID=167209)
    
> [!IMPORTANT]
> <span data-ttu-id="d2da2-126">You must use a certificate issued by a trusted certification authority (CA) with your Outlook Anywhere configuration.</span><span class="sxs-lookup"><span data-stu-id="d2da2-126">You must use a certificate issued by a trusted certification authority (CA) with your Outlook Anywhere configuration.</span></span> <span data-ttu-id="d2da2-127">Outlook Anywhere can't be configured with a self-signed certificate.</span><span class="sxs-lookup"><span data-stu-id="d2da2-127">Outlook Anywhere can't be configured with a self-signed certificate.</span></span> <span data-ttu-id="d2da2-128">For more information, see [How to configure SSL for Outlook Anywhere](https://go.microsoft.com/fwlink/?LinkID=80875).</span><span class="sxs-lookup"><span data-stu-id="d2da2-128">For more information, see [How to configure SSL for Outlook Anywhere](https://go.microsoft.com/fwlink/?LinkID=80875).</span></span> 
  
 <span data-ttu-id="d2da2-129">**선택 사항: Outlook Anywhere을 사용하여 Exchange 조직에 연결할 수 있는지 확인** 다음 방법 중 하나를 사용하여 연결 설정을 테스트해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="d2da2-129">**Optional: Verify that you can connect to your Exchange organization using Outlook Anywhere** Try one of the following methods to test your connection settings.</span></span>
  
- <span data-ttu-id="d2da2-130">회사 네트워크 외부에서 Outlook을 사용하여 온-프레미스 Exchange 사서함에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="d2da2-130">Use Outlook from outside your corporate network to connect to your on-premises Exchange mailbox.</span></span>
    
- <span data-ttu-id="d2da2-131">[Microsoft 원격 연결 분석기](https://https://testconnectivity.microsoft.com/) 를 사용 하 여 연결 설정을 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2da2-131">Use the [Microsoft Remote Connectivity Analyzer](https://https://testconnectivity.microsoft.com/) to test your connection settings.</span></span> <span data-ttu-id="d2da2-132">Outlook Anywhere(RPC over HTTP) 또는 Outlook 자동 검색 테스트를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d2da2-132">Use the Outlook Anywhere (RPC over HTTP) or Outlook Autodiscover tests.</span></span>
    
- <span data-ttu-id="d2da2-133">Exchange Online PowerShell에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d2da2-133">Run the following commands in Exchange Online PowerShell:</span></span>
    
  ```powershell
  $Credentials = Get-Credential
  ```

  ```powershell
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

 <span data-ttu-id="d2da2-134">**Set permissions** The on-premises user account that you use to connect to your on-premises Exchange organization (also called the migration administrator) must have the necessary permissions to access the on-premises mailboxes that you want to migrate to Office 365.</span><span class="sxs-lookup"><span data-stu-id="d2da2-134">**Set permissions** The on-premises user account that you use to connect to your on-premises Exchange organization (also called the migration administrator) must have the necessary permissions to access the on-premises mailboxes that you want to migrate to Office 365.</span></span> <span data-ttu-id="d2da2-135">This user account is used when you connect to your email system by creating a migration endpoint later in this procedure ([Step 3: Create a migration endpoint](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Endpoint) ).</span><span class="sxs-lookup"><span data-stu-id="d2da2-135">This user account is used when you connect to your email system by creating a migration endpoint later in this procedure ([Step 3: Create a migration endpoint](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Endpoint) ).</span></span>
  
<span data-ttu-id="d2da2-136">사서함을 마이그레이션하려면 관리자는 다음 사용 권한 집합 중 하나가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2da2-136">To migrate the mailboxes, the admin must have one of the following permission sets:</span></span>
  
- <span data-ttu-id="d2da2-137">온-프레미스 조직의 Active Directory에 있는 **Domain Admins** 그룹의 구성원이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2da2-137">Be a member of the **Domain Admins** group in Active Directory in the on-premises organization.</span></span>
    
    <span data-ttu-id="d2da2-138">또는</span><span class="sxs-lookup"><span data-stu-id="d2da2-138">or</span></span>
    
- <span data-ttu-id="d2da2-139">각 온-프레미스 사서함에 대해 **FullAccess** 권한이 할당되고 온-프레미스 사용자 계정에 대해 **TargetAddress** 속성을 수정할 수 있는 **WriteProperty** 권한이 할당되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2da2-139">Be assigned the **FullAccess** permission for each on-premises mailbox and the **WriteProperty** permission to modify the **TargetAddress** property on the on-premises user accounts.</span></span>
    
    <span data-ttu-id="d2da2-140"> 선택하거나 </span><span class="sxs-lookup"><span data-stu-id="d2da2-140">or</span></span>
    
- <span data-ttu-id="d2da2-141">사용자 사서함을 저장하는 온-프레미스 사서함 데이터베이스에 대해 **다음으로 받기** 권한이 할당되고 온-프레미스 사용자 계정에 대해 **TargetAddress** 속성을 수정할 수 있는 **WriteProperty** 권한이 할당되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2da2-141">Be assigned the **Receive As** permission on the on-premises mailbox database that stores user mailboxes and the **WriteProperty** permission to modify the **TargetAddress** property on the on-premises user accounts.</span></span>
    
<span data-ttu-id="d2da2-142">이러한 사용 권한을 설정하는 방법에 대한 지침은 [Office 365로 사서함을 마이그레이션할 수 있는 권한 할당](https://go.microsoft.com/fwlink/?LinkId=521656)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d2da2-142">For instructions about how to set these permissions, see [Assign permissions to migrate mailboxes to Office 365](https://go.microsoft.com/fwlink/?LinkId=521656).</span></span>
  
 <span data-ttu-id="d2da2-143">**Disable Unified Messaging (UM)** If UM is turned on for the on-premises mailboxes you're migrating, turn off UM before migration.</span><span class="sxs-lookup"><span data-stu-id="d2da2-143">**Disable Unified Messaging (UM)** If UM is turned on for the on-premises mailboxes you're migrating, turn off UM before migration.</span></span> <span data-ttu-id="d2da2-144">Turn on UM for the mailboxes after migration is complete.</span><span class="sxs-lookup"><span data-stu-id="d2da2-144">Turn on UM for the mailboxes after migration is complete.</span></span> <span data-ttu-id="d2da2-145">For how-to steps, see[disable unified messaging](https://go.microsoft.com/fwlink/?LinkId=521891).</span><span class="sxs-lookup"><span data-stu-id="d2da2-145">For how-to steps, see[disable unified messaging](https://go.microsoft.com/fwlink/?LinkId=521891).</span></span>
  
 <span data-ttu-id="d2da2-146">**Use directory synchronization to create new users in Office 365.**</span><span class="sxs-lookup"><span data-stu-id="d2da2-146">**Use directory synchronization to create new users in Office 365.**</span></span> <span data-ttu-id="d2da2-147">You use directory synchronization to create all the on-premises users in your Office 365 organization.</span><span class="sxs-lookup"><span data-stu-id="d2da2-147">You use directory synchronization to create all the on-premises users in your Office 365 organization.</span></span>
  
<span data-ttu-id="d2da2-148">You need to license the users after they're created.</span><span class="sxs-lookup"><span data-stu-id="d2da2-148">You need to license the users after they're created.</span></span> <span data-ttu-id="d2da2-149">You have 30 days to add licenses after the users are created.</span><span class="sxs-lookup"><span data-stu-id="d2da2-149">You have 30 days to add licenses after the users are created.</span></span> <span data-ttu-id="d2da2-150">For steps to add licenses, see [Step 8: Complete post-migration tasks](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Postmigration).</span><span class="sxs-lookup"><span data-stu-id="d2da2-150">For steps to add licenses, see [Step 8: Complete post-migration tasks](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Postmigration).</span></span>
  
 <span data-ttu-id="d2da2-151">Microsoft azure Active Directory (Azure AD) 동기화 도구 또는 Microsoft Azure AD Sync Services를 사용 하 여 Office 365에서 온-프레미스 사용자를 동기화 하 고 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2da2-151">You can use either the Microsoft Azure Active Directory (Azure AD) Synchronization Tool or the Microsoft Azure AD Sync Services  to synchronize and create your on-premises users in Office 365.</span></span> <span data-ttu-id="d2da2-152">사서함이 Office 365로 마이그레이션되면 온-프레미스 조직에서 사용자 계정을 관리하고 Office 365 조직과 동기화되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2da2-152">After mailboxes are migrated to Office 365, you manage user accounts in your on-premises organization, and they're synchronized with your Office 365 organization.</span></span> <span data-ttu-id="d2da2-153">자세한 내용은 [디렉터리 통합](https://go.microsoft.com/fwlink/?LinkId=521788)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d2da2-153">For more information, see[Directory Integration](https://go.microsoft.com/fwlink/?LinkId=521788) .</span></span>
  
### <a name="step-2-create-a-csv-file-for-a-staged-migration-batch"></a><span data-ttu-id="d2da2-154">2단계: 미리 구성된 마이그레이션 일괄 처리에 대한 CSV 파일 만들기</span><span class="sxs-lookup"><span data-stu-id="d2da2-154">Step 2: Create a CSV file for a staged migration batch</span></span>

<span data-ttu-id="d2da2-155">After you identify the users whose on-premises mailboxes you want to migrate to Office 365, you use a comma separated value (CSV ) file to create a migration batch.</span><span class="sxs-lookup"><span data-stu-id="d2da2-155">After you identify the users whose on-premises mailboxes you want to migrate to Office 365, you use a comma separated value (CSV ) file to create a migration batch.</span></span> <span data-ttu-id="d2da2-156">Each row in the CSV file—used by Office 365 to run the migration—contains information about an on-premises mailbox.</span><span class="sxs-lookup"><span data-stu-id="d2da2-156">Each row in the CSV file—used by Office 365 to run the migration—contains information about an on-premises mailbox.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="d2da2-157">There isn't a limit for the number of mailboxes that you can migrate to Office 365 using a staged migration.</span><span class="sxs-lookup"><span data-stu-id="d2da2-157">There isn't a limit for the number of mailboxes that you can migrate to Office 365 using a staged migration.</span></span> <span data-ttu-id="d2da2-158">The CSV file for a migration batch can contain a maximum of 2,000 rows.</span><span class="sxs-lookup"><span data-stu-id="d2da2-158">The CSV file for a migration batch can contain a maximum of 2,000 rows.</span></span> <span data-ttu-id="d2da2-159">To migrate more than 2,000 mailboxes, create additional CSV files and use each file to create a new migration batch.</span><span class="sxs-lookup"><span data-stu-id="d2da2-159">To migrate more than 2,000 mailboxes, create additional CSV files and use each file to create a new migration batch.</span></span> 
  
 <span data-ttu-id="d2da2-160">**지원되는 특성**</span><span class="sxs-lookup"><span data-stu-id="d2da2-160">**Supported attributes**</span></span>
  
<span data-ttu-id="d2da2-161">The CSV file for a staged migration supports the following three attributes.</span><span class="sxs-lookup"><span data-stu-id="d2da2-161">The CSV file for a staged migration supports the following three attributes.</span></span> <span data-ttu-id="d2da2-162">Each row in the CSV file corresponds to a mailbox and must contain a value for each of these attributes.</span><span class="sxs-lookup"><span data-stu-id="d2da2-162">Each row in the CSV file corresponds to a mailbox and must contain a value for each of these attributes.</span></span>
  
|<span data-ttu-id="d2da2-163">**특성**</span><span class="sxs-lookup"><span data-stu-id="d2da2-163">**Attribute**</span></span>|<span data-ttu-id="d2da2-164">**설명**</span><span class="sxs-lookup"><span data-stu-id="d2da2-164">**Description**</span></span>|<span data-ttu-id="d2da2-165">**필수 여부**</span><span class="sxs-lookup"><span data-stu-id="d2da2-165">**Required?**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="d2da2-166">EmailAddress</span><span class="sxs-lookup"><span data-stu-id="d2da2-166">EmailAddress</span></span>  <br/> |<span data-ttu-id="d2da2-167">온-프레미스 사서함에 대한 기본 SMTP 전자 메일 주소(예: pilarp@contoso.com)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d2da2-167">Specifies the primary SMTP email address, for example, pilarp@contoso.com, for on-premises mailboxes.</span></span>  <br/> <span data-ttu-id="d2da2-168">Use the primary SMTP address for on-premises mailboxes and not user IDs from the Office 365.</span><span class="sxs-lookup"><span data-stu-id="d2da2-168">Use the primary SMTP address for on-premises mailboxes and not user IDs from the Office 365.</span></span> <span data-ttu-id="d2da2-169">For example, if the on-premises domain is named contoso.com but the Office 365 email domain is named service.contoso.com, you would use the contoso.com domain name for email addresses in the CSV file.</span><span class="sxs-lookup"><span data-stu-id="d2da2-169">For example, if the on-premises domain is named contoso.com but the Office 365 email domain is named service.contoso.com, you would use the contoso.com domain name for email addresses in the CSV file.</span></span>  <br/> |<span data-ttu-id="d2da2-170">필수</span><span class="sxs-lookup"><span data-stu-id="d2da2-170">Required</span></span>  <br/> |
|<span data-ttu-id="d2da2-171">암호</span><span class="sxs-lookup"><span data-stu-id="d2da2-171">Password</span></span>  <br/> |<span data-ttu-id="d2da2-172">The password to be set for the new Office 365 mailbox.</span><span class="sxs-lookup"><span data-stu-id="d2da2-172">The password to be set for the new Office 365 mailbox.</span></span> <span data-ttu-id="d2da2-173">Any password restrictions that are applied to your Office 365 organization also apply to the passwords included in the CSV file.</span><span class="sxs-lookup"><span data-stu-id="d2da2-173">Any password restrictions that are applied to your Office 365 organization also apply to the passwords included in the CSV file.</span></span>  <br/> |<span data-ttu-id="d2da2-174">옵션</span><span class="sxs-lookup"><span data-stu-id="d2da2-174">Optional</span></span>  <br/> |
|<span data-ttu-id="d2da2-175">ForceChangePassword</span><span class="sxs-lookup"><span data-stu-id="d2da2-175">ForceChangePassword</span></span>  <br/> |<span data-ttu-id="d2da2-176">Specifies whether a user must change the password the first time they sign in to their new Office 365 mailbox.</span><span class="sxs-lookup"><span data-stu-id="d2da2-176">Specifies whether a user must change the password the first time they sign in to their new Office 365 mailbox.</span></span> <span data-ttu-id="d2da2-177">Use **True** or **False** for the value of this parameter.</span><span class="sxs-lookup"><span data-stu-id="d2da2-177">Use **True** or **False** for the value of this parameter.</span></span> <br/> <span data-ttu-id="d2da2-178">> [!NOTE]> 온-프레미스 조직에서 AD FS(Active Directory Federation Services)를 배포하여 SSO(Single Sign-On) 솔루션을 구현한 경우 **ForceChangePassword** 특성 값으로 **False** 를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2da2-178">> [!NOTE]> If you've implemented a single sign-on (SSO) solution by deploying Active Directory Federation Services (AD FS) or greater in your on-premises organization, you must use **False** for the value of the **ForceChangePassword** attribute.</span></span>          |<span data-ttu-id="d2da2-179">옵션</span><span class="sxs-lookup"><span data-stu-id="d2da2-179">Optional</span></span>  <br/> |
   
 <span data-ttu-id="d2da2-180">**CSV 파일 형식**</span><span class="sxs-lookup"><span data-stu-id="d2da2-180">**CSV file format**</span></span>
  
<span data-ttu-id="d2da2-181">Here's an example of the format for the CSV file.</span><span class="sxs-lookup"><span data-stu-id="d2da2-181">Here's an example of the format for the CSV file.</span></span> <span data-ttu-id="d2da2-182">In this example, three on-premises mailboxes are migrated to Office 365.</span><span class="sxs-lookup"><span data-stu-id="d2da2-182">In this example, three on-premises mailboxes are migrated to Office 365.</span></span>
  
<span data-ttu-id="d2da2-183">The first row, or header row, of the CSV file lists the names of the attributes, or fields, specified in the rows that follow.</span><span class="sxs-lookup"><span data-stu-id="d2da2-183">The first row, or header row, of the CSV file lists the names of the attributes, or fields, specified in the rows that follow.</span></span> <span data-ttu-id="d2da2-184">Each attribute name is separated by a comma.</span><span class="sxs-lookup"><span data-stu-id="d2da2-184">Each attribute name is separated by a comma.</span></span>
  
```powershell
EmailAddress,Password,ForceChangePassword 
pilarp@contoso.com,Pa$$w0rd,False 
tobyn@contoso.com,Pa$$w0rd,False 
briant@contoso.com,Pa$$w0rd,False 
```

<span data-ttu-id="d2da2-185">Each row under the header row represents one user and supplies the information that will be used to migrate the user's mailbox.</span><span class="sxs-lookup"><span data-stu-id="d2da2-185">Each row under the header row represents one user and supplies the information that will be used to migrate the user's mailbox.</span></span> <span data-ttu-id="d2da2-186">The attribute values in each row must be in the same order as the attribute names in the header row.</span><span class="sxs-lookup"><span data-stu-id="d2da2-186">The attribute values in each row must be in the same order as the attribute names in the header row.</span></span> 
  
<span data-ttu-id="d2da2-187">Use any text editor, or an application like Excel , to create the CSV file.</span><span class="sxs-lookup"><span data-stu-id="d2da2-187">Use any text editor, or an application like Excel , to create the CSV file.</span></span> <span data-ttu-id="d2da2-188">Save the file as a .csv or .txt file.</span><span class="sxs-lookup"><span data-stu-id="d2da2-188">Save the file as a .csv or .txt file.</span></span>
  
> [!NOTE]
> <span data-ttu-id="d2da2-189">If the CSV file contains non-ASCII or special characters, save the CSV file with UTF-8 or other Unicode encoding.</span><span class="sxs-lookup"><span data-stu-id="d2da2-189">If the CSV file contains non-ASCII or special characters, save the CSV file with UTF-8 or other Unicode encoding.</span></span> <span data-ttu-id="d2da2-190">Depending on the application, saving the CSV file with UTF-8 or other Unicode encoding can be easier when the system locale of the computer matches the language used in the CSV file.</span><span class="sxs-lookup"><span data-stu-id="d2da2-190">Depending on the application, saving the CSV file with UTF-8 or other Unicode encoding can be easier when the system locale of the computer matches the language used in the CSV file.</span></span> 
  
### <a name="step-3-create-a-migration-endpoint"></a><span data-ttu-id="d2da2-191">3단계: 마이그레이션 끝점 만들기</span><span class="sxs-lookup"><span data-stu-id="d2da2-191">Step 3: Create a migration endpoint</span></span>
<span data-ttu-id="d2da2-192"><a name="BK_Endpoint"> </a></span><span class="sxs-lookup"><span data-stu-id="d2da2-192"><a name="BK_Endpoint"> </a></span></span>

<span data-ttu-id="d2da2-193">To migrate email successfully, Office 365 needs to connect and communicate with the source email system.</span><span class="sxs-lookup"><span data-stu-id="d2da2-193">To migrate email successfully, Office 365 needs to connect and communicate with the source email system.</span></span> <span data-ttu-id="d2da2-194">To do this, Office 365 uses a migration endpoint.</span><span class="sxs-lookup"><span data-stu-id="d2da2-194">To do this, Office 365 uses a migration endpoint.</span></span> <span data-ttu-id="d2da2-195">To create an Outlook Anywhere migration endpoint by using PowerShell, for staged migration, first [connect to Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span><span class="sxs-lookup"><span data-stu-id="d2da2-195">To create an Outlook Anywhere migration endpoint by using PowerShell, for staged migration, first [connect to Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span></span> 
  
<span data-ttu-id="d2da2-196">전체 마이그레이션 명령 목록을 보려면 [이동 및 마이그레이션 cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=534750)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d2da2-196">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
  
<span data-ttu-id="d2da2-197">Exchange Online PowerShell에서 "StagedEndpoint"라는 Outlook Anywhere 마이그레이션 끝점을 만들려면 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d2da2-197">To create an Outlook Anywhere migration endpoint called "StagedEndpoint" in Exchange Online PowerShell, run the following commands:</span></span>
  
```powershell
$Credentials = Get-Credential
```

```powershell
New-MigrationEndpoint -ExchangeOutlookAnywhere -Name StagedEndpoint -Autodiscover -EmailAddress administrator@contoso.com -Credentials $Credentials
```

<span data-ttu-id="d2da2-198">**New-MigrationEndpoint** cmdlet에 대한 자세한 내용은[New-MigrationEndpoint](https://go.microsoft.com/fwlink/p/?LinkId=536437)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d2da2-198">For more information about the **New-MigrationEndpoint** cmdlet, see[New-MigrationEndpoint](https://go.microsoft.com/fwlink/p/?LinkId=536437).</span></span>
  
> [!NOTE]
> <span data-ttu-id="d2da2-199">The **New-MigrationEndpoint** cmdlet can be used to specify a database for the service to use by using the **-TargetDatabase** option.</span><span class="sxs-lookup"><span data-stu-id="d2da2-199">The **New-MigrationEndpoint** cmdlet can be used to specify a database for the service to use by using the **-TargetDatabase** option.</span></span> <span data-ttu-id="d2da2-200">Otherwise a database is randomly assigned from the Active Directory Federation Services (AD FS) 2.0 site where the management mailbox is located.</span><span class="sxs-lookup"><span data-stu-id="d2da2-200">Otherwise a database is randomly assigned from the Active Directory Federation Services (AD FS) 2.0 site where the management mailbox is located.</span></span>
  
#### <a name="verify-it-worked"></a><span data-ttu-id="d2da2-201">작동하는지 확인</span><span class="sxs-lookup"><span data-stu-id="d2da2-201">Verify it worked</span></span>

<span data-ttu-id="d2da2-202">Exchange Online PowerShell에서 다음 명령을 실행하여 "StagedEndpoint" 마이그레이션 끝점에 대한 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d2da2-202">In Exchange Online PowerShell, run the following command to display information about the "StagedEndpoint" migration endpoint:</span></span>
  
```powershell
Get-MigrationEndpoint StagedEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*
```

### <a name="step-4-create-and-start-a-stage-migration-batch"></a><span data-ttu-id="d2da2-203">4단계: 미리 구성된 마이그레이션 일괄 처리 만들기 및 시작</span><span class="sxs-lookup"><span data-stu-id="d2da2-203">Step 4: Create and start a stage migration batch</span></span>
<span data-ttu-id="d2da2-204"><a name="BK_Endpoint"> </a></span><span class="sxs-lookup"><span data-stu-id="d2da2-204"><a name="BK_Endpoint"> </a></span></span>

<span data-ttu-id="d2da2-205">You can use the **New-MigrationBatch** cmdlet in Exchange Online PowerShell to create a migration batch for a cutover migration.</span><span class="sxs-lookup"><span data-stu-id="d2da2-205">You can use the **New-MigrationBatch** cmdlet in Exchange Online PowerShell to create a migration batch for a cutover migration.</span></span> <span data-ttu-id="d2da2-206">You can create a migration batch and start it automatically by including the _AutoStart_ parameter.</span><span class="sxs-lookup"><span data-stu-id="d2da2-206">You can create a migration batch and start it automatically by including the _AutoStart_ parameter.</span></span> <span data-ttu-id="d2da2-207">Alternatively, you can create the migration batch and then manually start it afterwards by using the **Start-MigrationBatch** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d2da2-207">Alternatively, you can create the migration batch and then manually start it afterwards by using the **Start-MigrationBatch** cmdlet.</span></span> <span data-ttu-id="d2da2-208">This example creates a migration batch called "StagedBatch1" and uses the migration endpoint that was created in the previous step.</span><span class="sxs-lookup"><span data-stu-id="d2da2-208">This example creates a migration batch called "StagedBatch1" and uses the migration endpoint that was created in the previous step.</span></span>
  
```powershell
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint -AutoStart
```

<span data-ttu-id="d2da2-209">This example also creates a migration batch called "StagedBatch1" and uses the migration endpoint that was created in the previous step.</span><span class="sxs-lookup"><span data-stu-id="d2da2-209">This example also creates a migration batch called "StagedBatch1" and uses the migration endpoint that was created in the previous step.</span></span> <span data-ttu-id="d2da2-210">Because the  _AutoStart_ parameter isn't included, the migration batch has to be manually started on the migration dashboard or by using **Start-MigrationBatch** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d2da2-210">Because the  _AutoStart_ parameter isn't included, the migration batch has to be manually started on the migration dashboard or by using **Start-MigrationBatch** cmdlet.</span></span> <span data-ttu-id="d2da2-211">As previously stated, only one cutover migration batch can exist at a time.</span><span class="sxs-lookup"><span data-stu-id="d2da2-211">As previously stated, only one cutover migration batch can exist at a time.</span></span>
  
```powershell
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint
```

#### <a name="verify-it-worked"></a><span data-ttu-id="d2da2-212">작동하는지 확인</span><span class="sxs-lookup"><span data-stu-id="d2da2-212">Verify it worked</span></span>

<span data-ttu-id="d2da2-213">Exchange Online PowerShell에서 다음 명령을 실행하여 "StagedBatch1"에 대한 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d2da2-213">Run the following command in Exchange Online PowerShell to display information about the "StagedBatch1":</span></span>
  
```powershell
Get-MigrationBatch -Identity StagedBatch1 | Format-List
```

<span data-ttu-id="d2da2-214">다음 명령을 실행하여 일괄 처리가 시작되었는지 확인할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2da2-214">You can also verify that the batch has started by running the following command:</span></span>
  
```powershell
Get-MigrationBatch -Identity StagedBatch1 | Format-List Status
```

<span data-ttu-id="d2da2-215">**Get-MigrationBatch** cmdlet에 대한 자세한 내용은[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d2da2-215">For more information about the **Get-MigrationBatch** cmdlet, see[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441).</span></span>
  
### <a name="step-5-convert-on-premises-mailboxes-to-mail-enabled-users"></a><span data-ttu-id="d2da2-216">5단계: 온-프레미스 사서함을 메일 사용 가능 사용자로 변환</span><span class="sxs-lookup"><span data-stu-id="d2da2-216">Step 5: Convert on-premises mailboxes to mail-enabled users</span></span>
<span data-ttu-id="d2da2-217"><a name="BK_Endpoint"> </a></span><span class="sxs-lookup"><span data-stu-id="d2da2-217"><a name="BK_Endpoint"> </a></span></span>

<span data-ttu-id="d2da2-218">After you have successfully migrated a batch of mailboxes, you need some way to let users get to their mail.</span><span class="sxs-lookup"><span data-stu-id="d2da2-218">After you have successfully migrated a batch of mailboxes, you need some way to let users get to their mail.</span></span> <span data-ttu-id="d2da2-219">A user whose mailbox has been migrated now has both a mailbox on-premises and one in Office 365.</span><span class="sxs-lookup"><span data-stu-id="d2da2-219">A user whose mailbox has been migrated now has both a mailbox on-premises and one in Office 365.</span></span> <span data-ttu-id="d2da2-220">Users who have a mailbox in Office 365 will stop receiving new mail in their on-premises mailbox.</span><span class="sxs-lookup"><span data-stu-id="d2da2-220">Users who have a mailbox in Office 365 will stop receiving new mail in their on-premises mailbox.</span></span> 
  
<span data-ttu-id="d2da2-221">Because you are not done with your migrations, you are not yet ready to direct all users to Office 365 for their email.</span><span class="sxs-lookup"><span data-stu-id="d2da2-221">Because you are not done with your migrations, you are not yet ready to direct all users to Office 365 for their email.</span></span> <span data-ttu-id="d2da2-222">So what do you do for those people who have both?</span><span class="sxs-lookup"><span data-stu-id="d2da2-222">So what do you do for those people who have both?</span></span> <span data-ttu-id="d2da2-223">What you can do is change the on-premises mailboxes that you've already migrated to mail-enabled users.</span><span class="sxs-lookup"><span data-stu-id="d2da2-223">What you can do is change the on-premises mailboxes that you've already migrated to mail-enabled users.</span></span> <span data-ttu-id="d2da2-224">When you change from a mailbox to a mail-enabled user, you can direct the user to Office 365 for their email instead of going to their on-premises mailbox.</span><span class="sxs-lookup"><span data-stu-id="d2da2-224">When you change from a mailbox to a mail-enabled user, you can direct the user to Office 365 for their email instead of going to their on-premises mailbox.</span></span> 
  
<span data-ttu-id="d2da2-225">Another important reason to convert on-premises mailboxes to mail-enabled users is to retain proxy addresses from the Office 365 mailboxes by copying proxy addresses to the mail-enabled users.</span><span class="sxs-lookup"><span data-stu-id="d2da2-225">Another important reason to convert on-premises mailboxes to mail-enabled users is to retain proxy addresses from the Office 365 mailboxes by copying proxy addresses to the mail-enabled users.</span></span> <span data-ttu-id="d2da2-226">This lets you manage cloud-based users from your on-premises organization by using Active Directory.</span><span class="sxs-lookup"><span data-stu-id="d2da2-226">This lets you manage cloud-based users from your on-premises organization by using Active Directory.</span></span> <span data-ttu-id="d2da2-227">Also, if you decide to decommission your on-premises Exchange Server organization after all mailboxes are migrated to Office 365, the proxy addresses you've copied to the mail-enabled users will remain in your on-premises Active Directory.</span><span class="sxs-lookup"><span data-stu-id="d2da2-227">Also, if you decide to decommission your on-premises Exchange Server organization after all mailboxes are migrated to Office 365, the proxy addresses you've copied to the mail-enabled users will remain in your on-premises Active Directory.</span></span>
    
### <a name="step-6-delete-a-staged-migration-batch"></a><span data-ttu-id="d2da2-228">6단계: 미리 구성된 마이그레이션 일괄 처리 삭제</span><span class="sxs-lookup"><span data-stu-id="d2da2-228">Step 6: Delete a staged migration batch</span></span>
<span data-ttu-id="d2da2-229"><a name="BK_Endpoint"> </a></span><span class="sxs-lookup"><span data-stu-id="d2da2-229"><a name="BK_Endpoint"> </a></span></span>

 <span data-ttu-id="d2da2-230">After all mailboxes in a migration batch have been successfully migrated, and you've converted the on-premises mailboxes in the batch to mail-enabled users, you're ready to delete a staged migration batch.</span><span class="sxs-lookup"><span data-stu-id="d2da2-230">After all mailboxes in a migration batch have been successfully migrated, and you've converted the on-premises mailboxes in the batch to mail-enabled users, you're ready to delete a staged migration batch.</span></span> <span data-ttu-id="d2da2-231">Be sure to verify that mail is being forwarded to the Office 365 mailboxes in the migration batch.</span><span class="sxs-lookup"><span data-stu-id="d2da2-231">Be sure to verify that mail is being forwarded to the Office 365 mailboxes in the migration batch.</span></span> <span data-ttu-id="d2da2-232">When you delete a staged migration batch, the migration service cleans up any records related to the migration batch and deletes the migration batch.</span><span class="sxs-lookup"><span data-stu-id="d2da2-232">When you delete a staged migration batch, the migration service cleans up any records related to the migration batch and deletes the migration batch.</span></span>
  
<span data-ttu-id="d2da2-233">Exchange Online PowerShell에서 "StagedBatch1" 마이그레이션 일괄 처리를 삭제하려면 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d2da2-233">To delete the "StagedBatch1" migration batch in Exchange Online PowerShell, run the following command.</span></span>
  
```powershell
Remove-MigrationBatch -Identity StagedBatch1
```

<span data-ttu-id="d2da2-234">**Remove-MigrationBatch** cmdlet에 대한 자세한 내용은[Remove-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536481)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d2da2-234">For more information about the **Remove-MigrationBatch** cmdlet, see[Remove-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536481).</span></span>
  
#### <a name="verify-it-worked"></a><span data-ttu-id="d2da2-235">작동하는지 확인</span><span class="sxs-lookup"><span data-stu-id="d2da2-235">Verify it worked</span></span>

<span data-ttu-id="d2da2-236">Exchange Online PowerShell에서 다음 명령을 실행하여 "IMAPBatch1"에 대한 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d2da2-236">Run the following command in Exchange Online PowerShell to display information about the "IMAPBatch1":</span></span>
  
```powershell
Get-MigrationBatch StagedBatch1
```

<span data-ttu-id="d2da2-237">이 명령을 실행하면 상태가 **제거 중** 인 마이그레이션 일괄 처리가 반환되거나, 마이그레이션 일괄 처리를 찾을 수 없다는 오류가 반환됩니다. 이 경우 해당 일괄 처리가 삭제되었음을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2da2-237">The command will return either the migration batch with a status of **Removing**, or it will return an error stating that migration batch couldn't be found, verifying that the batch was deleted.</span></span>
  
<span data-ttu-id="d2da2-238">**Get-MigrationBatch** cmdlet에 대한 자세한 내용은[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d2da2-238">For more information about the **Get-MigrationBatch** cmdlet, see[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441).</span></span>
  
### <a name="step7-assign-licenses-to-office-365-users"></a><span data-ttu-id="d2da2-239">7단계: Office 365 사용자에게 라이선스 할당</span><span class="sxs-lookup"><span data-stu-id="d2da2-239">Step7: Assign licenses to Office 365 users</span></span>
<span data-ttu-id="d2da2-240"><a name="BK_Endpoint"> </a></span><span class="sxs-lookup"><span data-stu-id="d2da2-240"><a name="BK_Endpoint"> </a></span></span>

<span data-ttu-id="d2da2-241">라이선스를 할당하여 마이그레이션된 계정에 대한 Office 365 사용자 계정을 활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="d2da2-241">Activate Office 365 user accounts for the migrated accounts by assigning licenses.</span></span> <span data-ttu-id="d2da2-242">라이선스를 할당하지 않은 경우 30일의 유예 기간이 끝나면 사서함을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d2da2-242">If you don't assign a license, the mailbox is disabled when the grace period (30 days) ends.</span></span> <span data-ttu-id="d2da2-243">Microsoft 365 관리 센터에서 라이선스를 할당하려면 [비즈니스용 Office 365 라이선스 할당 또는 할당 취소](https://go.microsoft.com/fwlink/?LinkId=536681)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d2da2-243">To assign a license in the Microsoft 365 admin center, see [Assign or unassign licenses for Office 365 for business](https://go.microsoft.com/fwlink/?LinkId=536681).</span></span>
  
### <a name="step-8-complete-post-migration-tasks"></a><span data-ttu-id="d2da2-244">8단계: 마이그레이션 후 작업 완료</span><span class="sxs-lookup"><span data-stu-id="d2da2-244">Step 8: Complete post-migration tasks</span></span>
<span data-ttu-id="d2da2-245"><a name="BK_Postmigration"> </a></span><span class="sxs-lookup"><span data-stu-id="d2da2-245"><a name="BK_Postmigration"> </a></span></span>

- <span data-ttu-id="d2da2-246">**Create an Autodiscover DNS record so users can easily get to their mailboxes.**</span><span class="sxs-lookup"><span data-stu-id="d2da2-246">**Create an Autodiscover DNS record so users can easily get to their mailboxes.**</span></span> <span data-ttu-id="d2da2-247">After all on-premises mailboxes are migrated to Office 365, you can configure an Autodiscover DNS record for your Office 365 organization to enable users to easily connect to their new Office 365 mailboxes with Outlook and mobile clients.</span><span class="sxs-lookup"><span data-stu-id="d2da2-247">After all on-premises mailboxes are migrated to Office 365, you can configure an Autodiscover DNS record for your Office 365 organization to enable users to easily connect to their new Office 365 mailboxes with Outlook and mobile clients.</span></span> <span data-ttu-id="d2da2-248">This new Autodiscover DNS record has to use the same namespace that you're using for your Office 365 organization.</span><span class="sxs-lookup"><span data-stu-id="d2da2-248">This new Autodiscover DNS record has to use the same namespace that you're using for your Office 365 organization.</span></span> <span data-ttu-id="d2da2-249">For example, if your cloud-based namespace is cloud.contoso.com, the Autodiscover DNS record you need to create is autodiscover.cloud.contoso.com.</span><span class="sxs-lookup"><span data-stu-id="d2da2-249">For example, if your cloud-based namespace is cloud.contoso.com, the Autodiscover DNS record you need to create is autodiscover.cloud.contoso.com.</span></span>
    
    <span data-ttu-id="d2da2-250">Office 365 uses a CNAME record to implement the Autodiscover service for Outlook and mobile clients.</span><span class="sxs-lookup"><span data-stu-id="d2da2-250">Office 365 uses a CNAME record to implement the Autodiscover service for Outlook and mobile clients.</span></span> <span data-ttu-id="d2da2-251">The Autodiscover CNAME record must contain the following information:</span><span class="sxs-lookup"><span data-stu-id="d2da2-251">The Autodiscover CNAME record must contain the following information:</span></span>
    
  - <span data-ttu-id="d2da2-252">**별칭:** autodiscover</span><span class="sxs-lookup"><span data-stu-id="d2da2-252">**Alias:** autodiscover</span></span>
    
  - <span data-ttu-id="d2da2-253">**대상:** autodiscover.outlook.com</span><span class="sxs-lookup"><span data-stu-id="d2da2-253">**Target:** autodiscover.outlook.com</span></span>
    
    <span data-ttu-id="d2da2-254">자세한 내용은 [DNS 레코드를 관리하는 경우 Office 365용 DNS 레코드 만들기](https://go.microsoft.com/fwlink/p/?LinkId=535028)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d2da2-254">For more information, see [Create DNS records for Office 365 when you manage your DNS records](https://go.microsoft.com/fwlink/p/?LinkId=535028).</span></span>
    
- <span data-ttu-id="d2da2-255">**Decommission on-premises Exchange servers.**</span><span class="sxs-lookup"><span data-stu-id="d2da2-255">**Decommission on-premises Exchange servers.**</span></span> <span data-ttu-id="d2da2-256">After you've verified that all email is being routed directly to the Office 365 mailboxes, and you no longer need to maintain your on-premises email organization or don't plan on implementing an SSO solution, you can uninstall Exchange from your servers and remove your on-premises Exchange organization.</span><span class="sxs-lookup"><span data-stu-id="d2da2-256">After you've verified that all email is being routed directly to the Office 365 mailboxes, and you no longer need to maintain your on-premises email organization or don't plan on implementing an SSO solution, you can uninstall Exchange from your servers and remove your on-premises Exchange organization.</span></span>
    
    <span data-ttu-id="d2da2-257">자세한 내용은 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="d2da2-257">For more information, see the following:</span></span>
    
  - [<span data-ttu-id="d2da2-258">Exchange 2010 수정 또는 제거</span><span class="sxs-lookup"><span data-stu-id="d2da2-258">Modify or Remove Exchange 2010</span></span>](https://go.microsoft.com/fwlink/?LinkId=217936)
    
  - [<span data-ttu-id="d2da2-259">Exchange 2007 조직 제거 방법</span><span class="sxs-lookup"><span data-stu-id="d2da2-259">How to Remove an Exchange 2007 Organization</span></span>](https://go.microsoft.com/fwlink/?LinkID=100485)
    
  - [<span data-ttu-id="d2da2-260">Exchange Server 2003 제거 방법</span><span class="sxs-lookup"><span data-stu-id="d2da2-260">How to Uninstall Exchange Server 2003</span></span>](https://go.microsoft.com/fwlink/?LinkID=56561)
    

