---
title: Office 365의 디렉터리 동기화 계획
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MOE150
- MET150
ms.assetid: d3577c90-dda5-45ca-afb0-370d2889b10f
description: Office 365, Active directory 정리 및 Azure Active directory Connect 도구를 사용한 디렉터리 동기화에 대해 설명 합니다.
ms.openlocfilehash: 5f380efe3293d25e2e208c5fef836a89f6fa0cc8
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085287"
---
# <a name="plan-for-directory-synchronization-for-office-365"></a><span data-ttu-id="bc055-103">Office 365의 디렉터리 동기화 계획</span><span class="sxs-lookup"><span data-stu-id="bc055-103">Plan for directory synchronization for Office 365</span></span>
<span data-ttu-id="bc055-p101">비즈니스 요구 사항 및 기술 요건에 따라 디렉터리 동기화는 Office 365로 전환 하는 엔터프라이즈 고객에 게 가장 일반적인 프로 비전 선택입니다. 디렉터리 동기화를 통해 온-프레미스 Active Directory에서 id를 관리할 수 있으며 해당 id에 대 한 모든 업데이트가 Office 365에 동기화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bc055-p101">Depending on business need and technical requirements, directory synchronization is the most common provisioning choice for enterprise customers who are moving to Office 365. Directory synchronization allows identities to be managed in the on-premises Active Directory and all updates to that identity are synchronized to Office 365 .</span></span>
  
<span data-ttu-id="bc055-p102">디렉터리 준비, Azure Active directory의 요구 사항 및 기능을 비롯 하 여 디렉터리 동기화 구현을 계획할 때는 주의 해야 할 몇 가지 사항이 있습니다. 디렉터리 준비는 상당히 많은 영역을 포함 합니다. 여기에는 특성 업데이트, 감사 및 계획 도메인 컨트롤러 배치 등이 포함 됩니다. 계획 요구 사항 및 기능에는 필요한 사용 권한 결정, 다중 포리스트/디렉터리 시나리오, 용량 계획 및 양방향 동기화에 대 한 계획이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bc055-p102">There are a couple of things to keep in mind when you plan an implementation of directory synchronization, including directory preparation, and the requirements and functionality of the Azure Active Directory. Directory preparation covers quite a few areas. They include attribute updates, auditing, and planning domain controller placement. Planning requirements and functionality includes determining the permissions that are required, planning for multiforest/directory scenarios, capacity planning, and two-way synchronization.</span></span>
  
## <a name="office-365-identity-models"></a><span data-ttu-id="bc055-110">Office 365 id 모델</span><span class="sxs-lookup"><span data-stu-id="bc055-110">Office 365 identity models</span></span>
<span data-ttu-id="bc055-111">Office 365에서는 두 가지 주요 인증 및 id 모델, 즉 클라우드 인증과 페더레이션 인증을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc055-111">Office 365 uses two main authentication and identity models: cloud authentication and federated authentication.</span></span>
  
### <a name="cloud-authentication"></a><span data-ttu-id="bc055-112">클라우드 인증</span><span class="sxs-lookup"><span data-stu-id="bc055-112">Cloud authentication</span></span>
<span data-ttu-id="bc055-113">[클라우드 id](about-office-365-identity.md) -Office 365 관리 센터에서 사용자를 만들고 관리 하 고, Windows PowerShell 또는 Azure Active Directory를 사용 하 여 사용자를 관리할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc055-113">[Cloud identity](about-office-365-identity.md) - create and manage users in the Office 365 admin center, you can also use Windows PowerShell, or Azure Active Directory to manage your users.</span></span> 
  
<span data-ttu-id="bc055-p103">[원활한 single sign-on을 사용한 암호 해시 동기화](about-office-365-identity.md) -Azure AD의 온-프레미스 디렉터리 개체에 대 한 인증을 사용 하도록 설정 하는 가장 간단한 방법입니다. 암호 해시 동기화 (phs)를 사용 하 여 온-프레미스 Active Directory 사용자 계정 개체를 Office 365와 동기화 하 고 온-프레미스 사용자를 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc055-p103">[Password hash sync with seamless single sign-on](about-office-365-identity.md) - The simplest way to enable authentication for on-premises directory objects in Azure AD. With password hash sync (PHS), you synchronize your on-premises Active Directory user account objects with Office 365 and manage your users on-premises.</span></span> 
  
<span data-ttu-id="bc055-116">[원활한 single sign-on을 통한 통과 인증](about-office-365-identity.md) -하나 이상의 온-프레미스 서버에서 실행 되는 소프트웨어 에이전트를 사용 하 여 Azure AD 인증 서비스에 대 한 간단한 암호 유효성 검사를 제공 하 여 사용자의 유효성을 직접 검사 합니다. 온-프레미스 Active Directory</span><span class="sxs-lookup"><span data-stu-id="bc055-116">[Pass-through authentication with seamless single sign-on](about-office-365-identity.md) - Provides a simple password validation for Azure AD authentication services using a software agent running on one or more on-premises servers to validate the users directly with your on-premises Active Directory.</span></span> 
  
### <a name="federated-authentication"></a><span data-ttu-id="bc055-117">페더레이션 인증</span><span class="sxs-lookup"><span data-stu-id="bc055-117">Federated authentication</span></span>
<span data-ttu-id="bc055-118">[페더레이션 id Active Directory Federation Services AD FS](about-office-365-identity.md) -주로 인증 요구 사항이 더 많은 대규모 엔터프라이즈 조직에서 온-프레미스 디렉터리 개체는 Office 365와 사용자 계정으로 동기화 됩니다. 온-프레미스에서 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bc055-118">[Federated identity with Active Directory Federation Services AD FS](about-office-365-identity.md) - Primarily for large enterprise organizations with more complex authentication requirements, on-premises directory objects are synchronized with Office 365 and users accounts are managed on-premises.</span></span> 
  
<span data-ttu-id="bc055-119">타사 [인증 및 id 공급자](about-office-365-identity.md) -온-프레미스 디렉터리 개체는 Office 365와 동기화 될 수 있으며, 클라우드 리소스 액세스는 주로 타사 id 공급자 (IdP)를 통해 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bc055-119">[Third-party authentication and identity providers](about-office-365-identity.md) - On-premises directory objects may be synchronized to Office 365 and cloud resource access is primarily managed by a third-party identity provider (IdP).</span></span> 
  
## <a name="active-directory-cleanup"></a><span data-ttu-id="bc055-120">Active Directory 정리</span><span class="sxs-lookup"><span data-stu-id="bc055-120">Active Directory Cleanup</span></span>
<span data-ttu-id="bc055-121">동기화를 사용 하 여 office 365로 원활 하 게 전환할 수 있도록 office 365 디렉터리 동기화 배포를 시작 하기 전에 Active Directory 포리스트를 준비 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="bc055-121">To help ensure a seamless transition to Office 365 by using synchronization, we highly recommend that you prepare your Active Directory forest before you begin your Office 365 directory synchronization deployment.</span></span>
  
<span data-ttu-id="bc055-p104">[Office 365에서 디렉터리 동기화를 설정](set-up-directory-synchronization.md)하면 [idfix 도구를 다운로드 하 여 실행](install-and-run-idfix.md)하는 단계 중 하나입니다. idfix 도구를 사용 하 여 [디렉터리 정리](prepare-directory-attributes-for-synch-with-idfix.md)를 지원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc055-p104">When you [set up directory synchronization in Office 365](set-up-directory-synchronization.md), one of the steps is to [download and run the IdFix tool](install-and-run-idfix.md). You can use the IdFix tool to help with the [directory cleanup](prepare-directory-attributes-for-synch-with-idfix.md).</span></span>
  
<span data-ttu-id="bc055-124">디렉터리 정리는 다음 작업에 중점을 두어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc055-124">Your directory cleanup should focus on the following tasks:</span></span>

- <span data-ttu-id="bc055-125">중복 **proxyaddress** 및 **userPrincipalName** 특성을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc055-125">Remove duplicate **proxyAddress** and **userPrincipalName** attributes.</span></span>
- <span data-ttu-id="bc055-126">비어 있거나 잘못된 **userPrincipalName** 특성을 올바른 **userPrincipalName** 특성으로 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="bc055-126">Update blank and invalid **userPrincipalName** attributes with valid **userPrincipalName** attributes.</span></span>
- <span data-ttu-id="bc055-p105">**givenName**, 성 ( **sn** ), **sAMAccountName**, **displayName**, **mail**, **proxyAddresses**, **mailNickname**및 **userPrincipalName** 에서 잘못 되었거나 불확실 한 문자 제거 특성만. 특성을 준비 하는 방법에 대 한 자세한 내용은 [Azure Active Directory 동기화 도구를 통해 동기화 되는 특성 목록을](https://go.microsoft.com/fwlink/p/?LinkId=396719)참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="bc055-p105">Remove invalid and questionable characters in the **givenName**, surname ( **sn** ), **sAMAccountName**, **displayName**, **mail**, **proxyAddresses**, **mailNickname**, and **userPrincipalName** attributes. For details about preparing attributes, see [List of attributes that are synced by the Azure Active Directory Sync Tool](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="bc055-129">Azure AD Connect가 동기화 하는 것과 동일한 특성이 여기에 해당 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bc055-129">These are the same attributes that Azure AD Connect syncs.</span></span> 
  
## <a name="multiforest-deployment-considerations"></a><span data-ttu-id="bc055-130">다중 포리스트 배포 시 고려 사항</span><span class="sxs-lookup"><span data-stu-id="bc055-130">Multiforest Deployment Considerations</span></span>
<span data-ttu-id="bc055-131">여러 포리스트와 SSO 옵션에 대해 [Azure AD Connect의 사용자 지정 설치](https://go.microsoft.com/fwlink/p/?LinkId=698430)를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc055-131">For multiple forests and SSO options, use [Custom Installation of Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430).</span></span>
  
<span data-ttu-id="bc055-132">조직에 인증 (로그온 포리스트)을 위한 포리스트가 여러 개 있는 경우에는 다음을 수행 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="bc055-132">If your organization has multiple forests for authentication (logon forests), we highly recommend the following:</span></span>
  
- <span data-ttu-id="bc055-p106">**포리스트 통합 평가** 일반적으로 여러 포리스트를 유지 관리 하려면 오버 헤드가 더 많이 필요 합니다. 조직에 별도의 포리스트에 대 한 요구를 규정 하는 보안 제약 조건이 없는 경우에는 온-프레미스 환경을 단순화 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="bc055-p106">**Evaluate consolidating your forests.** In general, there's more overhead required to maintain multiple forests. Unless your organization has security constraints that dictate the need for separate forests, consider simplifying your on-premises environment.</span></span>
- <span data-ttu-id="bc055-p107">**기본 로그온 포리스트에서만 사용 합니다.** office 365의 초기 롤아웃을 위해 기본 로그온 포리스트에만 office 365을 배포 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="bc055-p107">**Use only in your primary logon forest.** Consider deploying Office 365 only in your primary logon forest for your initial rollout of Office 365.</span></span> 
    
<span data-ttu-id="bc055-138">다중 포리스트 Active Directory 배포를 통합할 수 없거나 다른 디렉터리 서비스를 사용 하 여 id를 관리 하는 경우에는 이러한 정보를 Microsoft 또는 파트너의 도움과 동기화 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc055-138">If you can't consolidate your multiforest Active Directory deployment or are using other directory services to manage identities, you may be able to synchronize these with the help of Microsoft or a partner.</span></span>
  
<span data-ttu-id="bc055-139">자세한 내용은 [Single sign-on 시나리오를 사용 하 여 다중 포리스트 디렉터리 동기화](https://go.microsoft.com/fwlink/p/?LinkId=525321)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bc055-139">For more information, see [Multi-forest Directory Sync with Single Sign-On Scenario](https://go.microsoft.com/fwlink/p/?LinkId=525321).</span></span>
  
## <a name="directory-integration-tools"></a><span data-ttu-id="bc055-140">디렉터리 통합 도구</span><span class="sxs-lookup"><span data-stu-id="bc055-140">Directory integration tools</span></span>
<span data-ttu-id="bc055-p108">디렉터리 동기화는 온-프레미스 Active directory 환경의 디렉터리 개체 (사용자, 그룹 및 연락처)를 Office 365 디렉터리 인프라와 동기화 하는 것입니다. 사용할 수 있는 도구 및 해당 기능 목록은 [디렉터리 통합 도구](https://go.microsoft.com/fwlink/p/?LinkID=510956) 를 참조 하십시오. 사용이 권장 되는 도구는 [Azure Active Directory Connect](https://go.microsoft.com/fwlink/?LinkId=525323)입니다.</span><span class="sxs-lookup"><span data-stu-id="bc055-p108">Directory synchronization is the synchronization of directory objects (users, groups, and contacts) from your on-premises Active Directory environment to the Office 365 directory infrastructure. See [directory integration tools](https://go.microsoft.com/fwlink/p/?LinkID=510956) for a list of the available tools and their functionality. The recommended tool to use is [Azure Active Directory Connect](https://go.microsoft.com/fwlink/?LinkId=525323).</span></span>
  
<span data-ttu-id="bc055-p109">사용자 계정이 처음에 Office 365 디렉터리와 동기화 되 면 활성화 되지 않은 것으로 표시 됩니다. 전자 메일을 보내거나 받을 수 없으며 구독 라이선스를 사용 하지 않습니다. 특정 사용자에 게 Office 365 구독을 할당할 준비가 되 면 유효한 라이선스를 할당 하 여 선택 하 고 활성화 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc055-p109">When user accounts are synchronized with the Office 365 directory for the first time, they are marked as non-activated. They cannot send or receive email, and they don't consume subscription licenses. When you're ready to assign Office 365 subscriptions to specific users, you must select and activate them by assigning a valid license.</span></span>
  
<span data-ttu-id="bc055-147">디렉터리 동기화는 다음과 같은 기능을 수행 하는 데 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc055-147">Directory synchronization is required for the following features and functionality:</span></span>
  
- <span data-ttu-id="bc055-148">SSO</span><span class="sxs-lookup"><span data-stu-id="bc055-148">SSO</span></span>
    
- <span data-ttu-id="bc055-149">Lync 동시 사용</span><span class="sxs-lookup"><span data-stu-id="bc055-149">Lync coexistence</span></span>
    
- <span data-ttu-id="bc055-150">다음을 포함 한 Exchange 하이브리드 배포</span><span class="sxs-lookup"><span data-stu-id="bc055-150">Exchange hybrid deployment, including:</span></span>
    
  - <span data-ttu-id="bc055-151">온-프레미스 Exchange 환경과 Office 365 간에 완전히 공유 되는 GAL (전체 주소 목록)입니다.</span><span class="sxs-lookup"><span data-stu-id="bc055-151">Fully shared global address list (GAL) between your on-premises Exchange environment and Office 365.</span></span>
  - <span data-ttu-id="bc055-152">다양한 메일 시스템의 GAL 정보 동기화</span><span class="sxs-lookup"><span data-stu-id="bc055-152">Synchronizing GAL information from different mail systems.</span></span>
  - <span data-ttu-id="bc055-p110">Office 365 서비스 제품에서 사용자를 추가 및 제거 하는 기능 이를 위해서는 다음이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc055-p110">The ability to add users to and remove users from Office 365 service offerings. This requires the following:</span></span>
  - <span data-ttu-id="bc055-p111">양방향 동기화는 디렉터리 동기화 설정 중에 구성 해야 합니다. 기본적으로 디렉터리 동기화 도구는 디렉터리 정보를 클라우드에만 기록 합니다. 양방향 동기화를 구성 하는 경우에는 다시 쓰기 기능을 사용 하도록 설정 하 여 제한 된 수의 개체 특성을 클라우드에서 복사한 다음 로컬 Active Directory에 다시 씁니다. 쓰기 저장은 Exchange 하이브리드 모드 라고도 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc055-p111">Two-way synchronization must be configured during directory synchronization setup. By default, directory synchronization tools write directory information only to the cloud. When you configure two-way synchronization, you enable write-back functionality so that a limited number of object attributes are copied from the cloud, and then written them back to your local Active Directory. Write-back is also referred to as Exchange hybrid mode.</span></span> 
  - <span data-ttu-id="bc055-159">온-프레미스 Exchange 하이브리드 배포</span><span class="sxs-lookup"><span data-stu-id="bc055-159">An on-premises Exchange hybrid deployment</span></span>
  - <span data-ttu-id="bc055-160">다른 사용자 사서함을 온-프레미스에 유지 하면서 일부 사용자 사서함을 Office 365로 이동 하는 기능</span><span class="sxs-lookup"><span data-stu-id="bc055-160">The ability to move some user mailboxes to Office 365 while keeping other user mailboxes on-premises.</span></span>
  - <span data-ttu-id="bc055-161">온-프레미스의 수신 허용 및 수신 거부는 Office 365에 복제 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bc055-161">Safe senders and blocked senders on-premises are replicated to Office 365.</span></span>
  - <span data-ttu-id="bc055-162">기본 위임 및 대신 보내기 전자 메일 기능</span><span class="sxs-lookup"><span data-stu-id="bc055-162">Basic delegation and send-on-behalf-of email functionality.</span></span>
  - <span data-ttu-id="bc055-163">통합 된 온-프레미스 스마트 카드 또는 다단계 인증 솔루션을 사용 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc055-163">You have an integrated on-premises smart card or multi-factor authentication solution.</span></span>
    
- <span data-ttu-id="bc055-164">사진, 축소판 그림, 회의실 및 보안 그룹 동기화</span><span class="sxs-lookup"><span data-stu-id="bc055-164">Synchronization of photos, thumbnails, conference rooms, and security groups</span></span>