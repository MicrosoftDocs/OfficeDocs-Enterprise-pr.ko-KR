---
title: Office 365의 디렉터리 동기화 문제 해결
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MBS150
ms.assetid: 79c43023-5a47-45ae-8068-d8a26eee6bc2
description: Office 365에서 디렉터리 동기화 문제의 일반적인 원인에 설명 하 고 문제를 해결 하 고 해결 하는데 몇 메서드를 제공 합니다.
ms.openlocfilehash: a1ccf7aa8c6d450cdd3d658ef0bc8d9ed6d25753
ms.sourcegitcommit: 6a4611bb474c783efd361890fe6f41c26c5aeeb3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/04/2018
ms.locfileid: "25405131"
---
# <a name="fixing-problems-with-directory-synchronization-for-office-365"></a><span data-ttu-id="73b66-103">Office 365의 디렉터리 동기화 문제 해결</span><span class="sxs-lookup"><span data-stu-id="73b66-103">Fixing problems with directory synchronization for Office 365</span></span>

<span data-ttu-id="73b66-p101">디렉터리 동기화를 통해 온-프레미스 사용자 및 그룹을 관리 하 고 추가, 삭제 및 클라우드로 변경 내용을 동기화를 계속 수 있습니다. 하지만 설치 프로그램은 더 복잡 하 고 문제의 원인을 파악 하기 어려운 경우가 있습니다. 잠재적인 문제를 식별 하 고 해결 하는데 도움이 되는 리소스가 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="73b66-p101">With directory synchronization, you can continue to manage users and groups on-premises and synchronize additions, deletions, and changes to the cloud. But setup is a little complicated and it can sometimes be difficult to identify the source of problems. We have resources to help you identify potential issues and fix them.</span></span>
  
## <a name="how-do-i-know-if-something-is-wrong"></a><span data-ttu-id="73b66-107">잘못 된 경우 어떻게 알 수 있습니까?</span><span class="sxs-lookup"><span data-stu-id="73b66-107">How do I know if something is wrong?</span></span>

<span data-ttu-id="73b66-108">잘못 된 것은 첫번째 해당할 Office 365 관리 센터에서 디렉터리 동기화 상태 타일 없음을 문제가 발생 하는 경우 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="73b66-108">The first indication that something is wrong is when the DirSync Status tile in the Office 365 admin center indicates there is a problem:</span></span>
  
![디렉터리 동기화 상태 관리 센터 미리 보기에서 바둑판식으로 배열](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
<span data-ttu-id="73b66-p102">또한 Office 365 테 넌 트에 디렉터리 동기화 오류가 발생 했는지 여부를 나타내는 (대체 전자 메일 및 관리 전자 메일을) 메일을 받습니다. 자세한 내용은 [Office 365에서 식별 디렉터리 동기화 오류](identify-directory-synchronization-errors.md)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="73b66-p102">You will also receive a mail (to the alternate email and to your admin email) from Office 365 that indicates your tenant has encountered directory synchronization errors. For details see [Identify directory synchronization errors in Office 365](identify-directory-synchronization-errors.md).</span></span>
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a><span data-ttu-id="73b66-112">Azure Active Directory 연결 도구를 가져오는 방법</span><span class="sxs-lookup"><span data-stu-id="73b66-112">How do I get Azure Active Directory Connect tool?</span></span>

<span data-ttu-id="73b66-p103">Office 365 관리 센터에서 이동 \* \* 사용자 \* \* \> **활성 사용자**입니다. **더 많은** 메뉴를 클릭 하 고 **디렉터리 동기화**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="73b66-p103">In the Office 365 admin center, navigate to \*\* Users \*\* \> **Active users**. Click the **More** menu and select **Directory synchronization**.</span></span> 
  
![더 많은 메뉴에서 디렉터리 동기화를 선택 합니다.](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
<span data-ttu-id="73b66-116">이전 Office 365 관리 센터에서 **사용자** 에 게 이동 \> **활성 사용자**및 **Active Directory 동기화**옆에 있는 선택 **를 설정** 합니다.</span><span class="sxs-lookup"><span data-stu-id="73b66-116">In the old Office 365 admin center, navigate to **USERS** \> **Active Users**, and select **Set up** next to **Active Directory synchronization**.</span></span> 
  
![Active Directory 동기화 옆에 있는 설정을 선택합니다](media/bd95492b-d65e-4072-a6ee-e562f5f566c3.png)
  
<span data-ttu-id="73b66-118">Azure AD 연결을 다운로드 하려면 [마법사의 지시](set-up-directory-synchronization.md) 를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="73b66-118">Follow the [instructions in the wizard](set-up-directory-synchronization.md) to download Azure AD Connect.</span></span> 
  
<span data-ttu-id="73b66-119">여전히 Azure Active Directory 동기화 (DirSync)를 사용 하는 경우 수행을 설치 하려면 시스템 요구 사항에 대 한 내용은 [Azure Active Directory 동기화 도구 설치 및 Office 365에서 구성 마법사 오류 메시지 문제를 해결 하는 방법](https://go.microsoft.com/fwlink/p/?LinkId=396717) 에 대 한 정보 디렉터리 동기화, 필요한 권한 및 일반적인 오류를 해결 하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="73b66-119">If you are still using Azure Active Directory Sync (DirSync), take a look at [How to troubleshoot Azure Active Directory Sync Tool installation and Configuration Wizard error messages in Office 365](https://go.microsoft.com/fwlink/p/?LinkId=396717) for information about the system requirements to install dirsync, the permissions you need, and how to troubleshoot common errors.</span></span> 
  
<span data-ttu-id="73b66-120">Azure Active Directory 동기화에서 Azure AD 연결을 업데이트 하려면 [대 한 업그레이드 지침](https://go.microsoft.com/fwlink/p/?LinkId=733240)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="73b66-120">To update from Azure Active Directory Sync to Azure AD Connect, see [the upgrade instructions](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span></span>
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-office-365"></a><span data-ttu-id="73b66-121">문제가 발생 하는 Office 365에서 디렉터리 동기화 설정 하는 일반적인 해결</span><span class="sxs-lookup"><span data-stu-id="73b66-121">Resolving common causes of problems with directory synchronization in Office 365</span></span>

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a><span data-ttu-id="73b66-122">**동기화 된 개체에 표시 되지 않거나 온라인으로 업데이트 또는 서비스에서 동기화 오류 보고서 나타남 합니다.**</span><span class="sxs-lookup"><span data-stu-id="73b66-122">**Synchronized objects aren't appearing or updating online, or I'm getting synchronization error reports from the Service.**</span></span>

- [<span data-ttu-id="73b66-123">Identity 동기화 및 복제 특성 복구</span><span class="sxs-lookup"><span data-stu-id="73b66-123">Identity synchronization and duplicate attribute resiliency</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=798300)

### <a name="i-have-an-alert-in-the-office-365-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a><span data-ttu-id="73b66-124">**Office 365 관리 센터에서 알림을 I 또는 최근 동기화 이벤트 된 하지 않은 자동된 전자 메일이 받고**</span><span class="sxs-lookup"><span data-stu-id="73b66-124">**I have an alert in the Office 365 admin center, or am receiving automated emails that there hasn't been a recent synchronization event**</span></span>
- [<span data-ttu-id="73b66-125">Azure AD 연결 연결 문제를 해결 합니다.</span><span class="sxs-lookup"><span data-stu-id="73b66-125">Troubleshoot connectivity issues with Azure AD Connect</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=820597)
- [<span data-ttu-id="73b66-126">Azure AD 연결 계정 및 사용 권한</span><span class="sxs-lookup"><span data-stu-id="73b66-126">Azure AD Connect Accounts and permissions</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=820598)
- [<span data-ttu-id="73b66-127">Azure AD 연결 동기화: Azure AD 서비스 계정을 관리 하는 방법</span><span class="sxs-lookup"><span data-stu-id="73b66-127">Azure AD Connect sync: How to manage the Azure AD service account</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=820599)
- [<span data-ttu-id="73b66-128">Azure Active Directory 중지 되거나 사용자에 대 한 디렉터리 동기화는 사용자에 게 경고 메시지 동기화 하지 않은 하루 이상에 등록 하는</span><span class="sxs-lookup"><span data-stu-id="73b66-128">Directory synchronization to Azure Active Directory stops or you're warned that sync hasn't registered in more than a day</span></span>](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-office-365-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a><span data-ttu-id="73b66-129">**암호 해시 동기화 되지 않은 또는 최근 암호 해시 동기화 된 하지 않은 Office 365 관리 센터에서 알림을 표시**</span><span class="sxs-lookup"><span data-stu-id="73b66-129">**Password hashes aren't synchronizing, or I'm seeing an alert in the Office 365 admin center that there hasn't been a recent password hash synchronization**</span></span>
- [<span data-ttu-id="73b66-130">Azure AD 연결 동기화를 사용 하 여 암호 해시 동기화를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="73b66-130">Implementing password hash synchronization with Azure AD Connect sync</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization)

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a><span data-ttu-id="73b66-131">**개체 할당량을 초과 하는 알림이 표시**</span><span class="sxs-lookup"><span data-stu-id="73b66-131">**I'm seeing an alert that Object quota exceeded**</span></span>
- <span data-ttu-id="73b66-p104">서비스를 보호 하는 기본 제공 개체 할당량을 제공 됩니다. Office 365와 동기화 하는 디렉터리에 너무 많은 개체를 사용 하는 경우 프로그램 할당량을 늘릴 수를 [비즈니스 제품에 대 한 지원 되는 대화 상대](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) 게 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="73b66-p104">We have a built-in object quota to help protect the service. If you have too many objects in your directory that need to sync to Office 365, you'll have to [Contact support for business products](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) to increase your quota.</span></span>

### <a name="i-need-to-know-which-attributes-are-synchronized"></a><span data-ttu-id="73b66-134">**동기화되는 특성을 확인해야 함**</span><span class="sxs-lookup"><span data-stu-id="73b66-134">**I need to know which attributes are synchronized**</span></span>
- <span data-ttu-id="73b66-135">온-프레미스 및 클라우드 [오른쪽 여기](https://go.microsoft.com/fwlink/p/?LinkId=396719)간에 동기화 되는 모든 특성의 목록을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73b66-135">You can find a list of all the attributes that are synced between on-premises and the cloud [right here](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span></span>

### <a name="i-cant-manage-or-remove-objects-that-were-synchronized-to-the-cloud"></a><span data-ttu-id="73b66-136">**관리 하거나 클라우드로 동기화 된 개체를 제거할 수 없음**</span><span class="sxs-lookup"><span data-stu-id="73b66-136">**I can't manage or remove objects that were synchronized to the cloud**</span></span>
- <span data-ttu-id="73b66-p105">클라우드에서 개체를 관리 준비가 되셨습니까? 또는 삭제 된 온-프레미스, 되었지만 클라우드에서 걸려 않은 개체는 다음과 같은? 이러한 문제를 해결 하는 방법에 대 한 정보를 [동기화 하는 동안 오류 문제를 해결](https://go.microsoft.com/fwlink/p/?linkid=842044) 와 지침에 대 한 [문서를 지원](https://go.microsoft.com/fwlink/p/?LinkId=396720) 하기에 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="73b66-p105">Are you ready to manage objects in the cloud only? Or is there an object that was deleted on-premises, but is stuck in the cloud? Take a look at this [Troubleshooting Errors during synchronization](https://go.microsoft.com/fwlink/p/?linkid=842044) and [support article](https://go.microsoft.com/fwlink/p/?LinkId=396720) for guidance on how to resolve these issues.</span></span>

### <a name="i-got-an-error-message-that-my-company-has-exceeded-the-number-of-objects-that-can-be-synchronized"></a><span data-ttu-id="73b66-140">**회사에서 동기화할 수 있는 개체 수가 초과되었다는 오류 메시지가 표시됨**</span><span class="sxs-lookup"><span data-stu-id="73b66-140">**I got an error message that my company has exceeded the number of objects that can be synchronized**</span></span>
- <span data-ttu-id="73b66-141">자세한 내용은이 문제에 대 한 [여기](https://go.microsoft.com/fwlink/p/?LinkId=396721)합니다.</span><span class="sxs-lookup"><span data-stu-id="73b66-141">You can read more about this issue [here](https://go.microsoft.com/fwlink/p/?LinkId=396721).</span></span>
   
## <a name="other-resources"></a><span data-ttu-id="73b66-142">기타 리소스</span><span class="sxs-lookup"><span data-stu-id="73b66-142">Other resources</span></span>

- [<span data-ttu-id="73b66-143">중복 된 사용자 계정 이름을 수정 하는 스크립트</span><span class="sxs-lookup"><span data-stu-id="73b66-143">Script to fix duplicate user principal names</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396725)
    
- [<span data-ttu-id="73b66-144">디렉터리 동기화를 위한 라우팅할 수 없는 도메인 (예:.local 도메인)를 준비 하는 방법</span><span class="sxs-lookup"><span data-stu-id="73b66-144">How to prepare a non-routable domain (such as .local domain) for directory synchronization</span></span>](prepare-a-non-routable-domain-for-directory-synchronization.md)
    
- [<span data-ttu-id="73b66-145">총 동기화 된 개체 수를 계산 하는 스크립트</span><span class="sxs-lookup"><span data-stu-id="73b66-145">Script to count total synchronized objects</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396726)
    
- [<span data-ttu-id="73b66-146">AD FS 2.0 문제해결</span><span class="sxs-lookup"><span data-stu-id="73b66-146">Troubleshoot AD FS 2.0</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396727)
    
- [<span data-ttu-id="73b66-147">PowerShell을 사용 하 여 메일 사용이 가능한 그룹에 대 한 빈 DisplayName 특성을 수정 하려면</span><span class="sxs-lookup"><span data-stu-id="73b66-147">Use PowerShell to fix empty DisplayName attributes for mail-enabled groups</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396728)
    
- [<span data-ttu-id="73b66-148">PowerShell을 사용 하 여 중복 된 UPN을 수정 하려면</span><span class="sxs-lookup"><span data-stu-id="73b66-148">Use PowerShell to fix duplicate UPN</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396730)
    
- [<span data-ttu-id="73b66-149">PowerShell을 사용 하 여 중복 된 전자 메일 주소를 수정 하려면</span><span class="sxs-lookup"><span data-stu-id="73b66-149">Use PowerShell to fix duplicate email addresses</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396731)
    
## <a name="diagnostic-tools"></a><span data-ttu-id="73b66-150">진단 도구</span><span class="sxs-lookup"><span data-stu-id="73b66-150">Diagnostic tools</span></span>

<span data-ttu-id="73b66-p106">[IDFix 도구](prepare-directory-attributes-for-synch-with-idfix.md) 는 Office 365로 마이그레이션 준비 하는 과정에서 온-프레미스 Active Directory 환경에서 검색 및 identity 개체 및 특성의 업데이트 관리를 수행 하는데 사용 됩니다. IDFix는 Office 365 서비스와 디렉터리 동기화에 대 한 담당 하는 Active Directory 관리자를 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="73b66-p106">[IDFix tool](prepare-directory-attributes-for-synch-with-idfix.md) is used to perform discovery and remediation of identity objects and their attributes in an on-premises Active Directory environment in preparation for migration to Office 365. IDFix is intended for the Active Directory administrators responsible for DirSync with the Office 365 service.</span></span> 

<span data-ttu-id="73b66-153">Microsoft 다운로드 센터에서 [IDFix 도구를 다운로드](https://go.microsoft.com/fwlink/p/?LinkId=396718) 합니다.</span><span class="sxs-lookup"><span data-stu-id="73b66-153">[Download the IDFix tool](https://go.microsoft.com/fwlink/p/?LinkId=396718) from the Microsoft download center.</span></span>