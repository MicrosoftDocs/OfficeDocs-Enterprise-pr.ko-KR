---
title: PowerShell을 사용 하 여 Microsoft 365로 미리 구성 된 마이그레이션 수행
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
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
description: '요약: Windows PowerShell을 사용 하 여 Microsoft 365로 미리 구성 된 마이그레이션을 수행 하는 방법을 알아봅니다.'
ms.openlocfilehash: bc21ec403b0c6daa3fe2411f8f4fea790dd5e71c
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/22/2020
ms.locfileid: "45229794"
---
# <a name="use-powershell-to-perform-a-staged-migration-to-microsoft-365"></a><span data-ttu-id="4ae1c-103">PowerShell을 사용 하 여 Microsoft 365로 미리 구성 된 마이그레이션 수행</span><span class="sxs-lookup"><span data-stu-id="4ae1c-103">Use PowerShell to perform a staged migration to Microsoft 365</span></span>

<span data-ttu-id="4ae1c-104">*이 문서는 Microsoft 365 Enterprise 및 Office 365 Enterprise에 모두 적용 됩니다.*</span><span class="sxs-lookup"><span data-stu-id="4ae1c-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="4ae1c-105">미리 구성 된 마이그레이션을 사용 하 여 시간에 따라 원본 전자 메일 시스템에서 Microsoft 365으로 사용자 사서함의 내용을 마이그레이션할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-105">You can migrate the contents of user mailboxes from a source email system to Microsoft 365 over time using a staged migration.</span></span>
  
<span data-ttu-id="4ae1c-p101">이 문서에서는 Exchange Online PowerShell을 사용 하 여 미리 구성 된 전자 메일 마이그레이션과 관련 된 작업을 안내 합니다. 미리 구성 [된 전자 메일 마이그레이션에 대해 알아야](https://go.microsoft.com/fwlink/p/?LinkId=536487)할 항목은 마이그레이션 프로세스에 대 한 개요를 제공 합니다. 해당 문서의 내용에 익숙해지면이 문서를 사용 하 여 전자 메일 시스템 간에 사서함 마이그레이션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-p101">This article walks you through the tasks involved with for a staged email migration using Exchange Online PowerShell. The topic, [What you need to know about a staged email migration](https://go.microsoft.com/fwlink/p/?LinkId=536487), gives you an overview of the migration process. When you're comfortable with the contents of that article, use this one to begin migrating mailboxes from one email system to another.</span></span>
  
> [!NOTE]
> <span data-ttu-id="4ae1c-p102">Exchange 관리 센터를 사용 하 여 미리 구성 된 마이그레이션을 수행할 수도 있습니다. 미리 구성 [된 전자 메일 마이그레이션 수행을 Microsoft 365에](https://go.microsoft.com/fwlink/p/?LinkId=536687)참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-p102">You can also use the Exchange admin center to perform staged migration. See [Perform a staged migration of email to Microsoft 365](https://go.microsoft.com/fwlink/p/?LinkId=536687).</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="4ae1c-111">시작하기 전에 알아야 할 내용</span><span class="sxs-lookup"><span data-stu-id="4ae1c-111">What do you need to know before you begin?</span></span>

<span data-ttu-id="4ae1c-p103">이 작업의 예상 완료 시간: 2-5 분 동안 마이그레이션 일괄 처리를 만듭니다. 마이그레이션 일괄 처리를 시작한 후에는 일괄 처리의 사서함 수, 각 사서함의 크기 및 사용 가능한 네트워크 용량에 따라 마이그레이션 시간이 달라 집니다. 사서함을 Microsoft 365로 마이그레이션하는 데 걸리는 시간에 영향을 주는 다른 요인에 대 한 자세한 내용은 [마이그레이션 성능을](https://go.microsoft.com/fwlink/p/?LinkId=275079)참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-p103">Estimated time to complete this task: 2-5 minutes to create a migration batch. After the migration batch is started, the duration of the migration will vary based on the number of mailboxes in the batch, the size of each mailbox, and your available network capacity. For information about other factors that affect how long it takes to migrate mailboxes to Microsoft 365, see [Migration Performance](https://go.microsoft.com/fwlink/p/?LinkId=275079).</span></span>
  
<span data-ttu-id="4ae1c-p104">이 절차를 수행하려면 먼저 사용 권한을 할당받아야 합니다. 필요한 사용 권한을 확인하려면 [받는 사람 사용 권한](https://go.microsoft.com/fwlink/p/?LinkId=534105)의 "마이그레이션" 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-p104">You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Migration" entry in the [Recipients Permissions](https://go.microsoft.com/fwlink/p/?LinkId=534105) topic.</span></span>
  
<span data-ttu-id="4ae1c-p105">Exchange Online PowerShell cmdlet을 사용하려면 로그인한 후 cmdlet을 로컬 Windows PowerShell 세션으로 가져와야 합니다. 해당 지침은 [원격 PowerShell을 사용하여 Exchange Online에 연결](https://go.microsoft.com/fwlink/p/?LinkId=534121)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-p105">To use the Exchange Online PowerShell cmdlets, you need to sign in and import the cmdlets into your local Windows PowerShell session. See [Connect to Exchange Online using remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121) for instructions.</span></span>
  
<span data-ttu-id="4ae1c-119">전체 마이그레이션 명령 목록을 보려면 [이동 및 마이그레이션 cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=534750)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-119">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
  
## <a name="migration-steps"></a><span data-ttu-id="4ae1c-120">마이그레이션 단계</span><span class="sxs-lookup"><span data-stu-id="4ae1c-120">Migration steps</span></span>

### <a name="step-1-prepare-for-a-staged-migration"></a><span data-ttu-id="4ae1c-121">1단계: 미리 구성된 마이그레이션 준비</span><span class="sxs-lookup"><span data-stu-id="4ae1c-121">Step 1: Prepare for a staged migration</span></span>

<span data-ttu-id="4ae1c-122">미리 구성 된 마이그레이션을 사용 하 여 사서함을 Microsoft 365로 마이그레이션하기 전에 Exchange 환경에 대 한 몇 가지 변경 사항을 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-122">Before you migrate mailboxes to Microsoft 365 by using a staged migration, there are a few changes you must make to your Exchange environment.</span></span>
  
 <span data-ttu-id="4ae1c-p106">**온-프레미스에서 Exchange Server에서 Outlook Anywhere 구성** 전자 메일 마이그레이션 서비스는 Outlook Anywhere(RPC over HTTP라고도 함)를 사용하여 온-프레미스 Exchange Server에 연결합니다. Exchange Server 2007 및 Exchange 2003에 맞게 Outlook Anywhere를 설정하는 방법에 대한 자세한 내용은 다음 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-p106">**Configure Outlook Anywhere on your on-premises Exchange Server** The email migration service uses Outlook Anywhere (also known as RPC over HTTP), to connect to your on-premises Exchange Server. For information about how to set up Outlook Anywhere for Exchange Server 2007, and Exchange 2003, see the following:</span></span>
  
- [<span data-ttu-id="4ae1c-125">Exchange 2007: "외부에서 Outlook 사용" 설정 방법</span><span class="sxs-lookup"><span data-stu-id="4ae1c-125">Exchange 2007: How to Enable Outlook Anywhere</span></span>](https://go.microsoft.com/fwlink/?LinkID=167210)
    
- [<span data-ttu-id="4ae1c-126">Exchange 2003: "외부에서 Outlook 사용" 구성 방법</span><span class="sxs-lookup"><span data-stu-id="4ae1c-126">How to configure Outlook Anywhere with Exchange 2003</span></span>](https://go.microsoft.com/fwlink/?LinkID=167209)
    
> [!IMPORTANT]
> <span data-ttu-id="4ae1c-p107">Outlook Anywhere 구성에서는 신뢰할 수 있는 CA(인증 기관)에서 발급한 인증서를 사용해야 합니다. Outlook Anywhere은 자체 서명된 인증서로 구성할 수 없습니다. 자세한 내용은 ["외부에서 Outlook 사용"에 대한 SSL 구성 방법](https://go.microsoft.com/fwlink/?LinkID=80875)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-p107">You must use a certificate issued by a trusted certification authority (CA) with your Outlook Anywhere configuration. Outlook Anywhere can't be configured with a self-signed certificate. For more information, see [How to configure SSL for Outlook Anywhere](https://go.microsoft.com/fwlink/?LinkID=80875).</span></span> 
  
 <span data-ttu-id="4ae1c-130">**선택 사항: Outlook Anywhere을 사용하여 Exchange 조직에 연결할 수 있는지 확인** 다음 방법 중 하나를 사용하여 연결 설정을 테스트해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-130">**Optional: Verify that you can connect to your Exchange organization using Outlook Anywhere** Try one of the following methods to test your connection settings.</span></span>
  
- <span data-ttu-id="4ae1c-131">회사 네트워크 외부에서 Outlook을 사용하여 온-프레미스 Exchange 사서함에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-131">Use Outlook from outside your corporate network to connect to your on-premises Exchange mailbox.</span></span>
    
- <span data-ttu-id="4ae1c-p108">[Microsoft 원격 연결 분석기](https://https://testconnectivity.microsoft.com/) 를 사용 하 여 연결 설정을 테스트 합니다. Outlook Anywhere (RPC over HTTP) 또는 Outlook 자동 검색 테스트를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-p108">Use the [Microsoft Remote Connectivity Analyzer](https://https://testconnectivity.microsoft.com/) to test your connection settings. Use the Outlook Anywhere (RPC over HTTP) or Outlook Autodiscover tests.</span></span>
    
- <span data-ttu-id="4ae1c-134">Exchange Online PowerShell에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-134">Run the following commands in Exchange Online PowerShell:</span></span>
    
  ```powershell
  $Credentials = Get-Credential
  ```

  ```powershell
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

 <span data-ttu-id="4ae1c-p109">**사용 권한 설정** 온-프레미스 Exchange 조직 (마이그레이션 관리자 라고도 함)에 연결 하는 데 사용 하는 온-프레미스 사용자 계정에는 Microsoft 365로 마이그레이션할 온-프레미스 사서함에 액세스 하는 데 필요한 권한이 있어야 합니다. 이 사용자 계정은이 절차의 뒷부분에 나오는 마이그레이션 끝점을 만들어 전자 메일 시스템에 연결할 때 사용 됩니다 ([3 단계: 마이그레이션 끝점 만들기](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Endpoint) ).</span><span class="sxs-lookup"><span data-stu-id="4ae1c-p109">**Set permissions** The on-premises user account that you use to connect to your on-premises Exchange organization (also called the migration administrator) must have the necessary permissions to access the on-premises mailboxes that you want to migrate to Microsoft 365. This user account is used when you connect to your email system by creating a migration endpoint later in this procedure ([Step 3: Create a migration endpoint](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Endpoint) ).</span></span>
  
<span data-ttu-id="4ae1c-137">사서함을 마이그레이션하려면 관리자는 다음 사용 권한 집합 중 하나가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-137">To migrate the mailboxes, the admin must have one of the following permission sets:</span></span>
  
- <span data-ttu-id="4ae1c-138">온-프레미스 조직의 Active Directory에 있는 **Domain Admins** 그룹의 구성원이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-138">Be a member of the **Domain Admins** group in Active Directory in the on-premises organization.</span></span>
    
    <span data-ttu-id="4ae1c-139"> 선택하거나 </span><span class="sxs-lookup"><span data-stu-id="4ae1c-139">or</span></span>
    
- <span data-ttu-id="4ae1c-140">각 온-프레미스 사서함에 대해 **FullAccess** 권한이 할당되고 온-프레미스 사용자 계정에 대해 **TargetAddress** 속성을 수정할 수 있는 **WriteProperty** 권한이 할당되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-140">Be assigned the **FullAccess** permission for each on-premises mailbox and the **WriteProperty** permission to modify the **TargetAddress** property on the on-premises user accounts.</span></span>
    
    <span data-ttu-id="4ae1c-141"> 선택하거나 </span><span class="sxs-lookup"><span data-stu-id="4ae1c-141">or</span></span>
    
- <span data-ttu-id="4ae1c-142">사용자 사서함을 저장하는 온-프레미스 사서함 데이터베이스에 대해 **다음으로 받기** 권한이 할당되고 온-프레미스 사용자 계정에 대해 **TargetAddress** 속성을 수정할 수 있는 **WriteProperty** 권한이 할당되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-142">Be assigned the **Receive As** permission on the on-premises mailbox database that stores user mailboxes and the **WriteProperty** permission to modify the **TargetAddress** property on the on-premises user accounts.</span></span>
    
<span data-ttu-id="4ae1c-143">이러한 사용 권한을 설정 하는 방법에 대 한 자세한 내용은 [Assign permissions To Microsoft 365로 사서함 마이그레이션을](https://go.microsoft.com/fwlink/?LinkId=521656)참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-143">For instructions about how to set these permissions, see [Assign permissions to migrate mailboxes to Microsoft 365](https://go.microsoft.com/fwlink/?LinkId=521656).</span></span>
  
 <span data-ttu-id="4ae1c-p110">**UM(통합 메시징)을 사용하지 않도록 설정** 마이그레이션하려는 온-프레미스 사서함에 대해 UM이 켜져 있는 경우 마이그레이션 전에 UM을 사용하지 않도록 설정합니다. 마이그레이션이 완료된 후 사서함에 대해 UM을 켭니다. 방법 단계에 대해서는[통합 메시징을 사용하지 않도록 설정](https://go.microsoft.com/fwlink/?LinkId=521891)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-p110">**Disable Unified Messaging (UM)** If UM is turned on for the on-premises mailboxes you're migrating, turn off UM before migration. Turn on UM for the mailboxes after migration is complete. For how-to steps, see[disable unified messaging](https://go.microsoft.com/fwlink/?LinkId=521891).</span></span>
  
 <span data-ttu-id="4ae1c-p111">**디렉터리 동기화를 사용 하 여 Microsoft 365에서 새 사용자를 만듭니다.** 디렉터리 동기화를 사용 하 여 Microsoft 365 조직의 모든 온-프레미스 사용자를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-p111">**Use directory synchronization to create new users in Microsoft 365.** You use directory synchronization to create all the on-premises users in your Microsoft 365 organization.</span></span>
  
<span data-ttu-id="4ae1c-p112">만든 사용자에게는 라이선스를 부여해야 합니다. 사용자를 만들고 30일 내에 라이선스를 추가해야 합니다. 라이선스를 추가하는 단계에 대해서는 [8단계: 마이그레이션 후 작업 완료](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Postmigration)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-p112">You need to license the users after they're created. You have 30 days to add licenses after the users are created. For steps to add licenses, see [Step 8: Complete post-migration tasks](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Postmigration).</span></span>
  
 <span data-ttu-id="4ae1c-p113">Microsoft azure Active Directory (Azure AD) 동기화 도구 또는 microsoft Azure AD Sync Services를 사용 하 여 Microsoft 365에서 온-프레미스 사용자를 동기화 하 고 만들 수 있습니다. 사서함이 Microsoft 365로 마이그레이션된 후에는 온-프레미스 조직에서 사용자 계정을 관리 하 고 Microsoft 365 조직과 동기화 합니다. 자세한 내용은[디렉터리 통합](https://go.microsoft.com/fwlink/?LinkId=521788) 을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-p113">You can use either the Microsoft Azure Active Directory (Azure AD) Synchronization Tool or the Microsoft Azure AD Sync Services  to synchronize and create your on-premises users in Microsoft 365. After mailboxes are migrated to Microsoft 365, you manage user accounts in your on-premises organization, and they're synchronized with your Microsoft 365 organization. For more information, see[Directory Integration](https://go.microsoft.com/fwlink/?LinkId=521788) .</span></span>
  
### <a name="step-2-create-a-csv-file-for-a-staged-migration-batch"></a><span data-ttu-id="4ae1c-155">2단계: 미리 구성된 마이그레이션 일괄 처리에 대한 CSV 파일 만들기</span><span class="sxs-lookup"><span data-stu-id="4ae1c-155">Step 2: Create a CSV file for a staged migration batch</span></span>

<span data-ttu-id="4ae1c-p114">온-프레미스 사서함이 Microsoft 365로 마이그레이션될 사용자를 확인 한 후 CSV (쉼표로 구분 된 값) 파일을 사용 하 여 마이그레이션 일괄 처리를 만듭니다. Microsoft 365에서 마이그레이션을 실행 하는 데 사용 하는 CSV 파일의 각 행에는 온-프레미스 사서함에 대 한 정보가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-p114">After you identify the users whose on-premises mailboxes you want to migrate to Microsoft 365, you use a comma separated value (CSV ) file to create a migration batch. Each row in the CSV file—used by Microsoft 365 to run the migration—contains information about an on-premises mailbox.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="4ae1c-p115">미리 구성 된 마이그레이션을 사용 하 여 Microsoft 365로 마이그레이션할 수 있는 사서함 수에는 제한이 없습니다. 마이그레이션 일괄 처리를 위한 CSV 파일에는 최대 2000 행이 포함 될 수 있습니다. 2000 개 보다 많은 사서함을 마이그레이션하려면 추가 CSV 파일을 만들고 각 파일을 사용 하 여 새 마이그레이션 일괄 처리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-p115">There isn't a limit for the number of mailboxes that you can migrate to Microsoft 365 using a staged migration. The CSV file for a migration batch can contain a maximum of 2,000 rows. To migrate more than 2,000 mailboxes, create additional CSV files and use each file to create a new migration batch.</span></span> 
  
 <span data-ttu-id="4ae1c-161">**지원되는 특성**</span><span class="sxs-lookup"><span data-stu-id="4ae1c-161">**Supported attributes**</span></span>
  
<span data-ttu-id="4ae1c-p116">미리 구성된 마이그레이션용 CSV 파일에는 다음과 같은 세 개의 특성이 지원됩니다. CSV 파일의 각 행은 하나의 사서함에 해당하며 이러한 각 특성에 대한 값을 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-p116">The CSV file for a staged migration supports the following three attributes. Each row in the CSV file corresponds to a mailbox and must contain a value for each of these attributes.</span></span>
  
|<span data-ttu-id="4ae1c-164">**특성**</span><span class="sxs-lookup"><span data-stu-id="4ae1c-164">**Attribute**</span></span>|<span data-ttu-id="4ae1c-165">**설명**</span><span class="sxs-lookup"><span data-stu-id="4ae1c-165">**Description**</span></span>|<span data-ttu-id="4ae1c-166">**필수 여부**</span><span class="sxs-lookup"><span data-stu-id="4ae1c-166">**Required?**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="4ae1c-167">EmailAddress</span><span class="sxs-lookup"><span data-stu-id="4ae1c-167">EmailAddress</span></span>  <br/> |<span data-ttu-id="4ae1c-168">온-프레미스 사서함에 대한 기본 SMTP 전자 메일 주소(예: pilarp@contoso.com)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-168">Specifies the primary SMTP email address, for example, pilarp@contoso.com, for on-premises mailboxes.</span></span>  <br/> <span data-ttu-id="4ae1c-p117">Microsoft 365의 사용자 Id가 아니라 온-프레미스 사서함에 대 한 기본 SMTP 주소를 사용 합니다. 예를 들어 온-프레미스 도메인의 이름이 contoso.com 이지만 Microsoft 365 전자 메일 도메인의 이름이 service.contoso.com 인 경우 CSV 파일의 전자 메일 주소에 contoso.com 도메인 이름을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-p117">Use the primary SMTP address for on-premises mailboxes and not user IDs from the Microsoft 365. For example, if the on-premises domain is named contoso.com but the Microsoft 365 email domain is named service.contoso.com, you would use the contoso.com domain name for email addresses in the CSV file.</span></span>  <br/> |<span data-ttu-id="4ae1c-171">필수</span><span class="sxs-lookup"><span data-stu-id="4ae1c-171">Required</span></span>  <br/> |
|<span data-ttu-id="4ae1c-172">암호</span><span class="sxs-lookup"><span data-stu-id="4ae1c-172">Password</span></span>  <br/> |<span data-ttu-id="4ae1c-p118">새 Microsoft 365 사서함에 대해 설정할 암호입니다. Microsoft 365 조직에 적용 되는 암호 제한은 CSV 파일에 포함 된 암호에도 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-p118">The password to be set for the new Microsoft 365 mailbox. Any password restrictions that are applied to your Microsoft 365 organization also apply to the passwords included in the CSV file.</span></span>  <br/> |<span data-ttu-id="4ae1c-175">옵션</span><span class="sxs-lookup"><span data-stu-id="4ae1c-175">Optional</span></span>  <br/> |
|<span data-ttu-id="4ae1c-176">ForceChangePassword</span><span class="sxs-lookup"><span data-stu-id="4ae1c-176">ForceChangePassword</span></span>  <br/> |<span data-ttu-id="4ae1c-p119">사용자가 새 Microsoft 365 사서함에 처음 로그인 할 때 암호를 변경 해야 하는지 여부를 지정 합니다. 이 매개 변수의 값으로는 **True** 또는 **False** 를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-p119">Specifies whether a user must change the password the first time they sign in to their new Microsoft 365 mailbox. Use **True** or **False** for the value of this parameter. </span></span><br/> <span data-ttu-id="4ae1c-179">> [!NOTE]> 온-프레미스 조직에서 AD FS(Active Directory Federation Services)를 배포하여 SSO(Single Sign-On) 솔루션을 구현한 경우 **ForceChangePassword** 특성 값으로 **False** 를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-179">> [!NOTE]> If you've implemented a single sign-on (SSO) solution by deploying Active Directory Federation Services (AD FS) or greater in your on-premises organization, you must use **False** for the value of the **ForceChangePassword** attribute.</span></span>          |<span data-ttu-id="4ae1c-180">옵션</span><span class="sxs-lookup"><span data-stu-id="4ae1c-180">Optional</span></span>  <br/> |
   
 <span data-ttu-id="4ae1c-181">**CSV 파일 형식**</span><span class="sxs-lookup"><span data-stu-id="4ae1c-181">**CSV file format**</span></span>
  
<span data-ttu-id="4ae1c-p120">다음은 CSV 파일 형식의 예입니다. 이 예에서는 세 개의 온-프레미스 사서함이 Microsoft 365로 마이그레이션됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-p120">Here's an example of the format for the CSV file. In this example, three on-premises mailboxes are migrated to Microsoft 365.</span></span>
  
<span data-ttu-id="4ae1c-p121">CSV 파일의 첫 번째 행(머리글 행)에는 그 다음 행들에 지정된 특성 또는 필드의 이름이 나열됩니다. 각 특성 이름은 쉼표로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-p121">The first row, or header row, of the CSV file lists the names of the attributes, or fields, specified in the rows that follow. Each attribute name is separated by a comma.</span></span>
  
```powershell
EmailAddress,Password,ForceChangePassword 
pilarp@contoso.com,Pa$$w0rd,False 
tobyn@contoso.com,Pa$$w0rd,False 
briant@contoso.com,Pa$$w0rd,False 
```

<span data-ttu-id="4ae1c-p122">머리글 행 아래의 각 행은 한 명의 사용자를 나타내며 해당 사용자의 사서함을 마이그레이션하기 위해 사용되는 정보를 제공합니다. 각 행의 특성 값은 머리글 행의 특성 이름과 동일한 순서로 나열되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-p122">Each row under the header row represents one user and supplies the information that will be used to migrate the user's mailbox. The attribute values in each row must be in the same order as the attribute names in the header row.</span></span> 
  
<span data-ttu-id="4ae1c-p123">텍스트 편집기 또는 Excel 등의 응용 프로그램을 사용하여 CSV 파일을 만들 수 있습니다. 파일을 .csv 또는 .txt 파일로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-p123">Use any text editor, or an application like Excel , to create the CSV file. Save the file as a .csv or .txt file.</span></span>
  
> [!NOTE]
> <span data-ttu-id="4ae1c-p124">CSV 파일에 ASCII가 아닌 문자 또는 특수 문자가 포함되어 있는 경우에는 CSV 파일을 UTF-8 또는 다른 유니코드 인코딩으로 저장합니다. 응용 프로그램에 따라 컴퓨터의 시스템 로캘이 CSV 파일에 사용된 언어와 일치하는 경우 CSV 파일을 UTF-8 또는 다른 유니코드 인코딩으로 저장하는 것이 보다 간단할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-p124">If the CSV file contains non-ASCII or special characters, save the CSV file with UTF-8 or other Unicode encoding. Depending on the application, saving the CSV file with UTF-8 or other Unicode encoding can be easier when the system locale of the computer matches the language used in the CSV file.</span></span> 
  
### <a name="step-3-create-a-migration-endpoint"></a><span data-ttu-id="4ae1c-192">3단계: 마이그레이션 끝점 만들기</span><span class="sxs-lookup"><span data-stu-id="4ae1c-192">Step 3: Create a migration endpoint</span></span>
<span data-ttu-id="4ae1c-193"><a name="BK_Endpoint"> </a></span><span class="sxs-lookup"><span data-stu-id="4ae1c-193"><a name="BK_Endpoint"> </a></span></span>

<span data-ttu-id="4ae1c-p125">전자 메일을 성공적으로 마이그레이션하려면 Microsoft 365에서 원본 전자 메일 시스템과 연결 하 여 통신 해야 합니다. 이 작업을 수행 하기 위해 Microsoft 365는 마이그레이션 끝점을 사용 합니다. PowerShell을 사용 하 여 Outlook Anywhere 마이그레이션 끝점을 만들려면 먼저 미리 구성 된 마이그레이션에 대해 [Exchange Online에 연결](https://go.microsoft.com/fwlink/p/?LinkId=534121)합니다.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-p125">To migrate email successfully, Microsoft 365 needs to connect and communicate with the source email system. To do this, Microsoft 365 uses a migration endpoint. To create an Outlook Anywhere migration endpoint by using PowerShell, for staged migration, first [connect to Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span></span> 
  
<span data-ttu-id="4ae1c-197">전체 마이그레이션 명령 목록을 보려면 [이동 및 마이그레이션 cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=534750)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-197">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
  
<span data-ttu-id="4ae1c-198">Exchange Online PowerShell에서 "StagedEndpoint"라는 Outlook Anywhere 마이그레이션 끝점을 만들려면 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-198">To create an Outlook Anywhere migration endpoint called "StagedEndpoint" in Exchange Online PowerShell, run the following commands:</span></span>
  
```powershell
$Credentials = Get-Credential
```

```powershell
New-MigrationEndpoint -ExchangeOutlookAnywhere -Name StagedEndpoint -Autodiscover -EmailAddress administrator@contoso.com -Credentials $Credentials
```

<span data-ttu-id="4ae1c-199">**New-MigrationEndpoint** cmdlet에 대한 자세한 내용은[New-MigrationEndpoint](https://go.microsoft.com/fwlink/p/?LinkId=536437)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-199">For more information about the **New-MigrationEndpoint** cmdlet, see[New-MigrationEndpoint](https://go.microsoft.com/fwlink/p/?LinkId=536437).</span></span>
  
> [!NOTE]
> <span data-ttu-id="4ae1c-p126">**New-MigrationEndpoint** cmdlet을 사용하여 **-TargetDatabase** 옵션을 통해 서비스에서 사용할 데이터베이스를 지정할 수 있습니다. 그렇지 않으면 데이터베이스는 관리 사서함이 있는 AD FS(Active Directory Federation Services) 2.0 사이트에서 임의로 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-p126">The **New-MigrationEndpoint** cmdlet can be used to specify a database for the service to use by using the **-TargetDatabase** option. Otherwise a database is randomly assigned from the Active Directory Federation Services (AD FS) 2.0 site where the management mailbox is located.</span></span>
  
#### <a name="verify-it-worked"></a><span data-ttu-id="4ae1c-202">작동하는지 확인</span><span class="sxs-lookup"><span data-stu-id="4ae1c-202">Verify it worked</span></span>

<span data-ttu-id="4ae1c-203">Exchange Online PowerShell에서 다음 명령을 실행하여 "StagedEndpoint" 마이그레이션 끝점에 대한 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-203">In Exchange Online PowerShell, run the following command to display information about the "StagedEndpoint" migration endpoint:</span></span>
  
```powershell
Get-MigrationEndpoint StagedEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*
```

### <a name="step-4-create-and-start-a-stage-migration-batch"></a><span data-ttu-id="4ae1c-204">4단계: 미리 구성된 마이그레이션 일괄 처리 만들기 및 시작</span><span class="sxs-lookup"><span data-stu-id="4ae1c-204">Step 4: Create and start a stage migration batch</span></span>
<span data-ttu-id="4ae1c-205"><a name="BK_Endpoint"> </a></span><span class="sxs-lookup"><span data-stu-id="4ae1c-205"><a name="BK_Endpoint"> </a></span></span>

<span data-ttu-id="4ae1c-p127">Exchange Online PowerShell에서 **New-MigrationBatch** cmdlet을 사용하여 단독형 마이그레이션을 위한 마이그레이션 일괄 처리를 만들 수 있습니다. _AutoStart_ 매개 변수를 포함하면 마이그레이션 일괄 처리를 만들고 자동으로 시작할 수 있습니다. 또는 마이그레이션 일괄 처리를 만들고 **Start-MigrationBatch** cmdlet을 사용하여 나중에 마이그레이션을 수동으로 시작할 수 있습니다. 이 예에서는 "StagedBatch1"이라는 마이그레이션 일괄 처리를 만든 다음 이전 예에서 만든 마이그레이션 끝점을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-p127">You can use the **New-MigrationBatch** cmdlet in Exchange Online PowerShell to create a migration batch for a cutover migration. You can create a migration batch and start it automatically by including the _AutoStart_ parameter. Alternatively, you can create the migration batch and then manually start it afterwards by using the **Start-MigrationBatch** cmdlet. This example creates a migration batch called "StagedBatch1" and uses the migration endpoint that was created in the previous step.</span></span>
  
```powershell
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint -AutoStart
```

<span data-ttu-id="4ae1c-p128">또한 이 예에서는 "StagedBatch1"이라는 마이그레이션 일괄 처리를 만든 다음 이전 예에서 만든 마이그레이션 끝점을 사용합니다.  _AutoStart_ 매개 변수가 포함되지 않으므로 마이그레이션 일괄 처리가 마이그레이션 대시보드나 **Start-MigrationBatch** cmdlet을 사용하여 수동으로 시작되어야 합니다. 앞서 설명했듯이 단독형 마이그레이션 일괄 처리는 한 번에 하나만 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-p128">This example also creates a migration batch called "StagedBatch1" and uses the migration endpoint that was created in the previous step. Because the  _AutoStart_ parameter isn't included, the migration batch has to be manually started on the migration dashboard or by using **Start-MigrationBatch** cmdlet. As previously stated, only one cutover migration batch can exist at a time.</span></span>
  
```powershell
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint
```

#### <a name="verify-it-worked"></a><span data-ttu-id="4ae1c-213">작동하는지 확인</span><span class="sxs-lookup"><span data-stu-id="4ae1c-213">Verify it worked</span></span>

<span data-ttu-id="4ae1c-214">Exchange Online PowerShell에서 다음 명령을 실행하여 "StagedBatch1"에 대한 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-214">Run the following command in Exchange Online PowerShell to display information about the "StagedBatch1":</span></span>
  
```powershell
Get-MigrationBatch -Identity StagedBatch1 | Format-List
```

<span data-ttu-id="4ae1c-215">다음 명령을 실행하여 일괄 처리가 시작되었는지 확인할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-215">You can also verify that the batch has started by running the following command:</span></span>
  
```powershell
Get-MigrationBatch -Identity StagedBatch1 | Format-List Status
```

<span data-ttu-id="4ae1c-216">**Get-MigrationBatch** cmdlet에 대한 자세한 내용은[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-216">For more information about the **Get-MigrationBatch** cmdlet, see[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441).</span></span>
  
### <a name="step-5-convert-on-premises-mailboxes-to-mail-enabled-users"></a><span data-ttu-id="4ae1c-217">5단계: 온-프레미스 사서함을 메일 사용 가능 사용자로 변환</span><span class="sxs-lookup"><span data-stu-id="4ae1c-217">Step 5: Convert on-premises mailboxes to mail-enabled users</span></span>
<span data-ttu-id="4ae1c-218"><a name="BK_Endpoint"> </a></span><span class="sxs-lookup"><span data-stu-id="4ae1c-218"><a name="BK_Endpoint"> </a></span></span>

<span data-ttu-id="4ae1c-p129">사서함 일괄 처리를 성공적으로 마이그레이션한 후에는 사용자가 자신의 메일에 액세스할 수 있도록 하는 방법이 필요 합니다. 이제 사서함이 마이그레이션된 사용자에 게는 온-프레미스와 Microsoft 365의 사서함이 모두 포함 됩니다. Microsoft 365에 사서함이 있는 사용자는 온-프레미스 사서함에서 새 메일 수신을 중지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-p129">After you have successfully migrated a batch of mailboxes, you need some way to let users get to their mail. A user whose mailbox has been migrated now has both a mailbox on-premises and one in Microsoft 365. Users who have a mailbox in Microsoft 365 will stop receiving new mail in their on-premises mailbox.</span></span> 
  
<span data-ttu-id="4ae1c-p130">마이그레이션이 완료 되지 않았으므로 모든 사용자에 게 전자 메일을 보낼 수 있는 Microsoft 365를 추가할 준비가 되지 않았습니다. 그렇다면 두 사용자에 대해 수행 하는 작업은 무엇 인가요? 사용자가 이미 마이그레이션한 온-프레미스 사서함을 메일 사용이 가능한 사람으로 변경 하는 것은 수행할 수 있는 작업입니다. 사서함에서 메일 사용이 가능한 사용자로 변경 하는 경우 해당 사용자를 온-프레미스 사서함으로 이동 하는 대신 전자 메일을 통해 Microsoft 365에 지시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-p130">Because you are not done with your migrations, you are not yet ready to direct all users to Microsoft 365 for their email. So what do you do for those people who have both? What you can do is change the on-premises mailboxes that you've already migrated to mail-enabled users. When you change from a mailbox to a mail-enabled user, you can direct the user to Microsoft 365 for their email instead of going to their on-premises mailbox.</span></span> 
  
<span data-ttu-id="4ae1c-p131">온-프레미스 사서함을 메일 사용이 가능한 사용자로 변환 하는 또 다른 중요 한 이유는 메일 사용이 가능한 사용자에 게 프록시 주소를 복사 하 여 Microsoft 365 사서함의 프록시 주소를 유지 하는 것입니다. 이렇게 하면 Active Directory를 사용 하 여 온-프레미스 조직에서 클라우드 기반 사용자를 관리할 수 있습니다. 또한 모든 사서함이 Microsoft 365로 마이그레이션된 후 온-프레미스 Exchange Server 조 직을 제거 하기로 결정 하면 메일 사용이 가능한 사용자에 게 복사한 프록시 주소가 온-프레미스 Active Directory에 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-p131">Another important reason to convert on-premises mailboxes to mail-enabled users is to retain proxy addresses from the Microsoft 365 mailboxes by copying proxy addresses to the mail-enabled users. This lets you manage cloud-based users from your on-premises organization by using Active Directory. Also, if you decide to decommission your on-premises Exchange Server organization after all mailboxes are migrated to Microsoft 365, the proxy addresses you've copied to the mail-enabled users will remain in your on-premises Active Directory.</span></span>
    
### <a name="step-6-delete-a-staged-migration-batch"></a><span data-ttu-id="4ae1c-229">6단계: 미리 구성된 마이그레이션 일괄 처리 삭제</span><span class="sxs-lookup"><span data-stu-id="4ae1c-229">Step 6: Delete a staged migration batch</span></span>
<span data-ttu-id="4ae1c-230"><a name="BK_Endpoint"> </a></span><span class="sxs-lookup"><span data-stu-id="4ae1c-230"><a name="BK_Endpoint"> </a></span></span>

 <span data-ttu-id="4ae1c-231">마이그레이션 일괄 처리에 포함된 모든 사서함이 마이그레이션되었고 일괄 처리에 있는 온-프레미스 사서함이 메일 사용 가능 사용자로 변환되면 미리 구성된 마이그레이션 일괄 처리를 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-231">After all mailboxes in a migration batch have been successfully migrated, and you've converted the on-premises mailboxes in the batch to mail-enabled users, you're ready to delete a staged migration batch.</span></span> <span data-ttu-id="4ae1c-232">메일이 마이그레이션 일괄 처리의 Microsoft 365 사서함으로 전달 되 고 있는지 확인 하십시오.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-232">Be sure to verify that mail is being forwarded to the Microsoft 365 mailboxes in the migration batch.</span></span> <span data-ttu-id="4ae1c-233">미리 구성된 마이그레이션 일괄 처리를 삭제하면 마이그레이션 서비스에서 마이그레이션 일괄 처리와 관련된 모든 레코드를 정리하고 마이그레이션 일괄 처리를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-233">When you delete a staged migration batch, the migration service cleans up any records related to the migration batch and deletes the migration batch.</span></span>
  
<span data-ttu-id="4ae1c-234">Exchange Online PowerShell에서 "StagedBatch1" 마이그레이션 일괄 처리를 삭제하려면 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-234">To delete the "StagedBatch1" migration batch in Exchange Online PowerShell, run the following command.</span></span>
  
```powershell
Remove-MigrationBatch -Identity StagedBatch1
```

<span data-ttu-id="4ae1c-235">**Remove-MigrationBatch** cmdlet에 대한 자세한 내용은[Remove-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536481)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-235">For more information about the **Remove-MigrationBatch** cmdlet, see[Remove-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536481).</span></span>
  
#### <a name="verify-it-worked"></a><span data-ttu-id="4ae1c-236">작동하는지 확인</span><span class="sxs-lookup"><span data-stu-id="4ae1c-236">Verify it worked</span></span>

<span data-ttu-id="4ae1c-237">Exchange Online PowerShell에서 다음 명령을 실행하여 "IMAPBatch1"에 대한 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-237">Run the following command in Exchange Online PowerShell to display information about the "IMAPBatch1":</span></span>
  
```powershell
Get-MigrationBatch StagedBatch1
```

<span data-ttu-id="4ae1c-238">이 명령을 실행하면 상태가 **제거 중** 인 마이그레이션 일괄 처리가 반환되거나, 마이그레이션 일괄 처리를 찾을 수 없다는 오류가 반환됩니다. 이 경우 해당 일괄 처리가 삭제되었음을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-238">The command will return either the migration batch with a status of **Removing**, or it will return an error stating that migration batch couldn't be found, verifying that the batch was deleted.</span></span>
  
<span data-ttu-id="4ae1c-239">**Get-MigrationBatch** cmdlet에 대한 자세한 내용은[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-239">For more information about the **Get-MigrationBatch** cmdlet, see[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441).</span></span>
  
### <a name="step7-assign-licenses-to-microsoft-365-users"></a><span data-ttu-id="4ae1c-240">7 단계: Microsoft 365 사용자에 게 라이선스 할당</span><span class="sxs-lookup"><span data-stu-id="4ae1c-240">Step7: Assign licenses to Microsoft 365 users</span></span>
<span data-ttu-id="4ae1c-241"><a name="BK_Endpoint"> </a></span><span class="sxs-lookup"><span data-stu-id="4ae1c-241"><a name="BK_Endpoint"> </a></span></span>

<span data-ttu-id="4ae1c-242">라이선스를 할당 하 여 마이그레이션된 계정에 대해 Microsoft 365 사용자 계정을 정품 인증 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-242">Activate Microsoft 365 user accounts for the migrated accounts by assigning licenses.</span></span> <span data-ttu-id="4ae1c-243">라이선스를 할당하지 않은 경우 30일의 유예 기간이 끝나면 사서함을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-243">If you don't assign a license, the mailbox is disabled when the grace period (30 days) ends.</span></span> <span data-ttu-id="4ae1c-244">Microsoft 365 관리 센터에서 라이선스를 할당 하려면 [라이선스 할당 또는](https://docs.microsoft.com/microsoft-365/admin/manage/assign-licenses-to-users)할당 해제를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-244">To assign a license in the Microsoft 365 admin center, see [Assign or unassign licenses](https://docs.microsoft.com/microsoft-365/admin/manage/assign-licenses-to-users).</span></span>
  
### <a name="step-8-complete-post-migration-tasks"></a><span data-ttu-id="4ae1c-245">8단계: 마이그레이션 후 작업 완료</span><span class="sxs-lookup"><span data-stu-id="4ae1c-245">Step 8: Complete post-migration tasks</span></span>
<span data-ttu-id="4ae1c-246"><a name="BK_Postmigration"> </a></span><span class="sxs-lookup"><span data-stu-id="4ae1c-246"><a name="BK_Postmigration"> </a></span></span>

- <span data-ttu-id="4ae1c-247">**사용자가 자신의 사서함으로 쉽게 이동할 수 있도록 자동 검색 DNS 레코드를 만듭니다.**</span><span class="sxs-lookup"><span data-stu-id="4ae1c-247">**Create an Autodiscover DNS record so users can easily get to their mailboxes.**</span></span> <span data-ttu-id="4ae1c-248">모든 온-프레미스 사서함이 Microsoft 365로 마이그레이션된 후에는 사용자가 Outlook 및 모바일 클라이언트를 사용 하 여 새 Microsoft 365 사서함에 쉽게 연결할 수 있도록 Microsoft 365 조 직에 대 한 자동 검색 DNS 레코드를 구성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-248">After all on-premises mailboxes are migrated to Microsoft 365, you can configure an Autodiscover DNS record for your Microsoft 365 organization to enable users to easily connect to their new Microsoft 365 mailboxes with Outlook and mobile clients.</span></span> <span data-ttu-id="4ae1c-249">이 새로운 자동 검색 DNS 레코드는 Microsoft 365 조직에 사용 중인 것과 동일한 네임 스페이스를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-249">This new Autodiscover DNS record has to use the same namespace that you're using for your Microsoft 365 organization.</span></span> <span data-ttu-id="4ae1c-250">예를 들어 클라우드 기반 네임스페이스가 cloud.contoso.com인 경우 만들어야 할 자동 검색 DNS 레코드는 autodiscover.cloud.contoso.com입니다.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-250">For example, if your cloud-based namespace is cloud.contoso.com, the Autodiscover DNS record you need to create is autodiscover.cloud.contoso.com.</span></span>
    
    <span data-ttu-id="4ae1c-251">Microsoft 365는 CNAME 레코드를 사용 하 여 Outlook 및 모바일 클라이언트에 대 한 자동 검색 서비스를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-251">Microsoft 365 uses a CNAME record to implement the Autodiscover service for Outlook and mobile clients.</span></span> <span data-ttu-id="4ae1c-252">Autodiscover CNAME 레코드에는 다음과 같은 정보가 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-252">The Autodiscover CNAME record must contain the following information:</span></span>
    
  - <span data-ttu-id="4ae1c-253">**별칭:** autodiscover</span><span class="sxs-lookup"><span data-stu-id="4ae1c-253">**Alias:** autodiscover</span></span>
    
  - <span data-ttu-id="4ae1c-254">**대상:** autodiscover.outlook.com</span><span class="sxs-lookup"><span data-stu-id="4ae1c-254">**Target:** autodiscover.outlook.com</span></span>
    
    <span data-ttu-id="4ae1c-255">자세한 내용은 [DNS 레코드를 추가 하 여 도메인 연결](https://go.microsoft.com/fwlink/p/?LinkId=535028)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-255">For more information, see [Add DNS records to connect your domain](https://go.microsoft.com/fwlink/p/?LinkId=535028).</span></span>
    
- <span data-ttu-id="4ae1c-256">**온-프레미스 Exchange 서버를 해제합니다.**</span><span class="sxs-lookup"><span data-stu-id="4ae1c-256">**Decommission on-premises Exchange servers.**</span></span> <span data-ttu-id="4ae1c-257">모든 전자 메일이 Microsoft 365 사서함으로 바로 라우팅되고 있음을 확인 하 고 온-프레미스 전자 메일 조직을 더 이상 유지 관리할 필요가 없거나 SSO 솔루션을 구현 하지 않으려는 경우 서버에서 Exchange를 제거 하 고 온-프레미스 Exchange 조직을 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-257">After you've verified that all email is being routed directly to the Microsoft 365 mailboxes, and you no longer need to maintain your on-premises email organization or don't plan on implementing an SSO solution, you can uninstall Exchange from your servers and remove your on-premises Exchange organization.</span></span>
    
    <span data-ttu-id="4ae1c-258">자세한 내용은 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="4ae1c-258">For more information, see the following:</span></span>
    
  - [<span data-ttu-id="4ae1c-259">Exchange 2010 수정 또는 제거</span><span class="sxs-lookup"><span data-stu-id="4ae1c-259">Modify or Remove Exchange 2010</span></span>](https://go.microsoft.com/fwlink/?LinkId=217936)
    
  - [<span data-ttu-id="4ae1c-260">Exchange 2007 조직 제거 방법</span><span class="sxs-lookup"><span data-stu-id="4ae1c-260">How to Remove an Exchange 2007 Organization</span></span>](https://go.microsoft.com/fwlink/?LinkID=100485)
    
  - [<span data-ttu-id="4ae1c-261">Exchange Server 2003 제거 방법</span><span class="sxs-lookup"><span data-stu-id="4ae1c-261">How to Uninstall Exchange Server 2003</span></span>](https://go.microsoft.com/fwlink/?LinkID=56561)
    

