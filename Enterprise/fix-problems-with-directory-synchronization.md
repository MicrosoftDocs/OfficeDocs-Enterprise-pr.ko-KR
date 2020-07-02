---
title: Microsoft 365의 디렉터리 동기화 문제 해결
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MBS150
ms.assetid: 79c43023-5a47-45ae-8068-d8a26eee6bc2
description: Office 365에서 발생 하는 디렉터리 동기화 문제의 일반적인 원인에 대해 설명 하 고 이러한 문제를 해결 하는 데 도움이 되는 몇 가지 방법을 제공 합니다.
ms.openlocfilehash: d9e390a7230499f724ebbdae592264a850dd9418
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998036"
---
# <a name="fixing-problems-with-directory-synchronization-for-microsoft-365"></a><span data-ttu-id="6b140-103">Microsoft 365의 디렉터리 동기화 문제 해결</span><span class="sxs-lookup"><span data-stu-id="6b140-103">Fixing problems with directory synchronization for Microsoft 365</span></span>

<span data-ttu-id="6b140-104">디렉터리 동기화를 사용 하면 온-프레미스에서 사용자 및 그룹을 계속 관리 하 고 추가, 삭제 및 변경 내용을 클라우드로 동기화 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b140-104">With directory synchronization, you can continue to manage users and groups on-premises and synchronize additions, deletions, and changes to the cloud.</span></span> <span data-ttu-id="6b140-105">그러나 설치 프로그램은 다소 복잡 하며 때때로 문제의 원인을 파악 하기 어려울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b140-105">But setup is a little complicated and it can sometimes be difficult to identify the source of problems.</span></span> <span data-ttu-id="6b140-106">Microsoft는 잠재적인 문제를 파악 하 고 해결 하는 데 도움이 되는 리소스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b140-106">We have resources to help you identify potential issues and fix them.</span></span>
  
## <a name="how-do-i-know-if-something-is-wrong"></a><span data-ttu-id="6b140-107">무엇이 잘못 되었는지 어떻게 알 수 있나요?</span><span class="sxs-lookup"><span data-stu-id="6b140-107">How do I know if something is wrong?</span></span>

<span data-ttu-id="6b140-108">무언가가 잘못 되었음을 나타내는 첫 번째 방법은 Microsoft 365 관리 센터의 DirSync 상태 타일이 문제가 있음을 나타낼 때입니다.</span><span class="sxs-lookup"><span data-stu-id="6b140-108">The first indication that something is wrong is when the DirSync Status tile in the Microsoft 365 admin center indicates there is a problem.</span></span>
  
<span data-ttu-id="6b140-109">또한 테 넌 트에서 디렉터리 동기화 오류가 발생 했음을 나타내는 Microsoft 365에서 전자 메일 및 관리자 전자 메일에 대 한 메일을 받게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b140-109">You will also receive a mail (to the alternate email and to your admin email) from Microsoft 365 that indicates your tenant has encountered directory synchronization errors.</span></span> <span data-ttu-id="6b140-110">자세한 내용은 [Microsoft 365에서 디렉터리 동기화 오류 파악를](identify-directory-synchronization-errors.md)참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6b140-110">For details see [Identify directory synchronization errors in Microsoft 365](identify-directory-synchronization-errors.md).</span></span>
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a><span data-ttu-id="6b140-111">Azure Active Directory Connect 도구를 가져오려면 어떻게 해야 합니까?</span><span class="sxs-lookup"><span data-stu-id="6b140-111">How do I get Azure Active Directory Connect tool?</span></span>

<span data-ttu-id="6b140-112">[Microsoft 365 관리 센터](https://admin.microsoft.com)에서 **사용자** \> **활성 사용자**로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b140-112">In the [Microsoft 365 admin center](https://admin.microsoft.com), navigate to **Users** \> **Active users**.</span></span> <span data-ttu-id="6b140-113">**기타** 메뉴 (세 개의 점선)를 클릭 하 고 **디렉터리 동기화**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b140-113">Click the **More** menu (three dots) and select **Directory synchronization**.</span></span> 
  
<span data-ttu-id="6b140-114">[마법사의 지침](set-up-directory-synchronization.md) 에 따라 Azure AD Connect를 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b140-114">Follow the [instructions in the wizard](set-up-directory-synchronization.md) to download Azure AD Connect.</span></span> 
  
<span data-ttu-id="6b140-115">여전히 Azure AD (Active Directory) 동기화 (DirSync)를 사용 하는 경우 dirsync 설치를 위한 시스템 요구 사항, 필요한 권한 및 일반적인 오류를 해결 하는 방법에 대 한 자세한 내용은 [Microsoft 365의 Azure Active Directory 동기화 도구 설치 및 구성 마법사 오류 메시지 문제 해결 방법을](https://go.microsoft.com/fwlink/p/?LinkId=396717) 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="6b140-115">If you are still using Azure Active Directory (Azure AD) Sync (DirSync), take a look at [How to troubleshoot Azure Active Directory Sync Tool installation and Configuration Wizard error messages in Microsoft 365](https://go.microsoft.com/fwlink/p/?LinkId=396717) for information about the system requirements to install dirsync, the permissions you need, and how to troubleshoot common errors.</span></span> 
  
<span data-ttu-id="6b140-116">Azure ad Sync에서 Azure AD Connect로 업데이트 하려면 [업그레이드 지침](https://go.microsoft.com/fwlink/p/?LinkId=733240)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6b140-116">To update from Azure AD Sync to Azure AD Connect, see [the upgrade instructions](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span></span>
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-microsoft-365"></a><span data-ttu-id="6b140-117">Microsoft 365에서 디렉터리 동기화 문제의 일반적인 원인 해결</span><span class="sxs-lookup"><span data-stu-id="6b140-117">Resolving common causes of problems with directory synchronization in Microsoft 365</span></span>

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a><span data-ttu-id="6b140-118">**동기화 된 개체가 표시 되지 않거나 온라인으로 업데이트 되지 않거나, 서비스에서 동기화 오류 보고서를 가져옵니다.**</span><span class="sxs-lookup"><span data-stu-id="6b140-118">**Synchronized objects aren't appearing or updating online, or I'm getting synchronization error reports from the Service.**</span></span>

- [<span data-ttu-id="6b140-119">ID 동기화 및 중복 특성 복원력</span><span class="sxs-lookup"><span data-stu-id="6b140-119">Identity synchronization and duplicate attribute resiliency</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)

### <a name="i-have-an-alert-in-the-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a><span data-ttu-id="6b140-120">**관리 센터에 경고가 있거나 최근 동기화 이벤트가 없는 자동 전자 메일을 받는 경우**</span><span class="sxs-lookup"><span data-stu-id="6b140-120">**I have an alert in the admin center, or am receiving automated emails that there hasn't been a recent synchronization event**</span></span>
- [<span data-ttu-id="6b140-121">Azure AD Connect 연결 문제 해결</span><span class="sxs-lookup"><span data-stu-id="6b140-121">Troubleshoot connectivity issues with Azure AD Connect</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/tshoot-connect-connectivity)
- [<span data-ttu-id="6b140-122">Azure AD Connect 계정 및 사용 권한</span><span class="sxs-lookup"><span data-stu-id="6b140-122">Azure AD Connect Accounts and permissions</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=820598)
- [<span data-ttu-id="6b140-123">Azure AD Connect 동기화: Azure AD 서비스 계정을 관리하는 방법</span><span class="sxs-lookup"><span data-stu-id="6b140-123">Azure AD Connect sync: How to manage the Azure AD service account</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-azureadaccount)
- [<span data-ttu-id="6b140-124">Azure Active Directory에 대한 디렉터리 동기화가 중지되거나 동기화가 하루 이상 등록되지 않았다는 경고가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b140-124">Directory synchronization to Azure Active Directory stops or you're warned that sync hasn't registered in more than a day</span></span>](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a><span data-ttu-id="6b140-125">**암호 해시가 동기화 되지 않거나 최근 암호 해시 동기화가 아직 없는 경우 관리 센터에서 경고가 표시 됨**</span><span class="sxs-lookup"><span data-stu-id="6b140-125">**Password hashes aren't synchronizing, or I'm seeing an alert in the admin center that there hasn't been a recent password hash synchronization**</span></span>
- [<span data-ttu-id="6b140-126">Azure AD Connect 동기화로 암호 동기화 구현</span><span class="sxs-lookup"><span data-stu-id="6b140-126">Implementing password hash synchronization with Azure AD Connect sync</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization)

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a><span data-ttu-id="6b140-127">**개체 할당량이 초과 되었음을 알리는 경고가 표시 됨**</span><span class="sxs-lookup"><span data-stu-id="6b140-127">**I'm seeing an alert that Object quota exceeded**</span></span>
- <span data-ttu-id="6b140-128">서비스를 보호 하는 데 도움이 되는 기본 제공 개체 할당량이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b140-128">We have a built-in object quota to help protect the service.</span></span> <span data-ttu-id="6b140-129">디렉터리에 Microsoft 365와 동기화 해야 하는 개체가 너무 많은 경우에는 [비즈니스 제품 지원에 문의](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) 하 여 할당량을 늘려야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b140-129">If you have too many objects in your directory that need to sync to Microsoft 365, you'll have to [Contact support for business products](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) to increase your quota.</span></span>

### <a name="i-need-to-know-which-attributes-are-synchronized"></a><span data-ttu-id="6b140-130">**동기화 되는 특성을 확인 해야 합니다.**</span><span class="sxs-lookup"><span data-stu-id="6b140-130">**I need to know which attributes are synchronized**</span></span>
- <span data-ttu-id="6b140-131">온-프레미스와 클라우드 간에 동기화 되는 모든 특성의 목록을 [여기](https://go.microsoft.com/fwlink/p/?LinkId=396719)에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b140-131">You can find a list of all the attributes that are synced between on-premises and the cloud [right here](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span></span>

### <a name="i-cant-manage-or-remove-objects-that-were-synchronized-to-the-cloud"></a><span data-ttu-id="6b140-132">**클라우드와 동기화 된 개체를 관리 하거나 제거할 수 없습니다.**</span><span class="sxs-lookup"><span data-stu-id="6b140-132">**I can't manage or remove objects that were synchronized to the cloud**</span></span>
- <span data-ttu-id="6b140-133">클라우드에서만 개체를 관리할 준비가 되셨습니까?</span><span class="sxs-lookup"><span data-stu-id="6b140-133">Are you ready to manage objects in the cloud only?</span></span> <span data-ttu-id="6b140-134">또는 온-프레미스에서 삭제 되었지만 클라우드에서는 개체가 없습니까?</span><span class="sxs-lookup"><span data-stu-id="6b140-134">Or is there an object that was deleted on-premises, but is stuck in the cloud?</span></span> <span data-ttu-id="6b140-135">이러한 문제를 해결 하는 방법에 대 한 지침은 동기화 및 [지원 문서](https://go.microsoft.com/fwlink/p/?LinkId=396720) 에서이 [문제 해결 오류](https://go.microsoft.com/fwlink/p/?linkid=842044) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6b140-135">Take a look at this [Troubleshooting Errors during synchronization](https://go.microsoft.com/fwlink/p/?linkid=842044) and [support article](https://go.microsoft.com/fwlink/p/?LinkId=396720) for guidance on how to resolve these issues.</span></span>

### <a name="i-got-an-error-message-that-my-company-has-exceeded-the-number-of-objects-that-can-be-synchronized"></a><span data-ttu-id="6b140-136">**회사에서 동기화 할 수 있는 개체 수가 초과 되었다는 오류 메시지가 표시 됨**</span><span class="sxs-lookup"><span data-stu-id="6b140-136">**I got an error message that my company has exceeded the number of objects that can be synchronized**</span></span>
- <span data-ttu-id="6b140-137">[여기](https://go.microsoft.com/fwlink/p/?LinkId=396721)에서이 문제에 대 한 자세한 내용을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b140-137">You can read more about this issue [here](https://go.microsoft.com/fwlink/p/?LinkId=396721).</span></span>
   
## <a name="other-resources"></a><span data-ttu-id="6b140-138">기타 리소스</span><span class="sxs-lookup"><span data-stu-id="6b140-138">Other resources</span></span>

- <span data-ttu-id="6b140-139">[Script to fix duplicate user principal names](https://go.microsoft.com/fwlink/p/?LinkId=396725)(중복된 사용자 계정 이름을 수정하기 위한 스크립트)</span><span class="sxs-lookup"><span data-stu-id="6b140-139">[Script to fix duplicate user principal names](https://go.microsoft.com/fwlink/p/?LinkId=396725)</span></span>
    
- [<span data-ttu-id="6b140-140">디렉터리 동기화를 위해 라우팅할 수 없는 도메인 (예: 로컬 도메인)을 준비 하는 방법</span><span class="sxs-lookup"><span data-stu-id="6b140-140">How to prepare a non-routable domain (such as .local domain) for directory synchronization</span></span>](prepare-a-non-routable-domain-for-directory-synchronization.md)
    
- [<span data-ttu-id="6b140-141">동기화 된 총 개체 수를 계산할 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="6b140-141">Script to count total synchronized objects</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396726)
    
- [<span data-ttu-id="6b140-142">AD FS 2.0 문제 해결</span><span class="sxs-lookup"><span data-stu-id="6b140-142">Troubleshoot AD FS 2.0</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396727)
    
- [<span data-ttu-id="6b140-143">PowerShell을 사용 하 여 메일 사용이 가능한 그룹에 대 한 빈 DisplayName 특성 수정</span><span class="sxs-lookup"><span data-stu-id="6b140-143">Use PowerShell to fix empty DisplayName attributes for mail-enabled groups</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396728)
    
- [<span data-ttu-id="6b140-144">PowerShell을 사용 하 여 중복 UPN 수정</span><span class="sxs-lookup"><span data-stu-id="6b140-144">Use PowerShell to fix duplicate UPN</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396730)
    
- [<span data-ttu-id="6b140-145">PowerShell을 사용 하 여 중복 전자 메일 주소 수정</span><span class="sxs-lookup"><span data-stu-id="6b140-145">Use PowerShell to fix duplicate email addresses</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396731)
    
## <a name="diagnostic-tools"></a><span data-ttu-id="6b140-146">진단 도구</span><span class="sxs-lookup"><span data-stu-id="6b140-146">Diagnostic tools</span></span>

<span data-ttu-id="6b140-147">[Idfix 도구](prepare-directory-attributes-for-synch-with-idfix.md) 는 Microsoft 365로의 마이그레이션을 준비 하기 위해 온-프레미스 Active Directory 환경에서 id 개체 및 해당 특성의 검색 및 관리를 수행 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b140-147">[IDFix tool](prepare-directory-attributes-for-synch-with-idfix.md) is used to perform discovery and remediation of identity objects and their attributes in an on-premises Active Directory environment in preparation for migration to Microsoft 365.</span></span> <span data-ttu-id="6b140-148">IDFix는 Microsoft 365 서비스와의 디렉터리 동기화를 담당 하는 Active Directory 관리자를 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="6b140-148">IDFix is intended for the Active Directory administrators responsible for directory synchronization with the Microsoft 365 service.</span></span> 

<span data-ttu-id="6b140-149">Microsoft 다운로드 센터에서 [IDFix 도구를 다운로드](https://go.microsoft.com/fwlink/p/?LinkId=396718) 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b140-149">[Download the IDFix tool](https://go.microsoft.com/fwlink/p/?LinkId=396718) from the Microsoft download center.</span></span>