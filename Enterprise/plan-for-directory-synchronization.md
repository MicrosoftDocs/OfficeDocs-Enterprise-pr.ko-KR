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
search.appverid:
- MOE150
- MET150
ms.assetid: d3577c90-dda5-45ca-afb0-370d2889b10f
description: Office 365, Active Directory 정리 및 Azure Active Directory 연결 도구를 사용 하 여 디렉터리 동기화에 설명 합니다.
ms.openlocfilehash: cc2a2ca050facaf53f0a235898c31ae7aaeff4ae
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542066"
---
# <a name="plan-for-directory-synchronization-for-office-365"></a><span data-ttu-id="c3c0b-103">Office 365의 디렉터리 동기화 계획</span><span class="sxs-lookup"><span data-stu-id="c3c0b-103">Plan for directory synchronization for Office 365</span></span>
<span data-ttu-id="c3c0b-p101">비즈니스 요구 및 기술 요구 사항에 따라 디렉터리 동기화는 엔터프라이즈 고객에 게 Office 365로 이동 하는 가장 일반적인 프로 비전 선택입니다. 해당 id에 대 한 모든 업데이트는 Office 365와 동기화 및 디렉터리 동기화에 id가 온-프레미스 Active Directory에서 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3c0b-p101">Depending on business need and technical requirements, directory synchronization is the most common provisioning choice for enterprise customers who are moving to Office 365. Directory synchronization allows identities to be managed in the on-premises Active Directory and all updates to that identity are synchronized to Office 365 .</span></span>
  
<span data-ttu-id="c3c0b-p102">디렉터리 동기화를 디렉터리 준비 및 요구 사항 및 Azure Active Directory의 기능 등의 구현을 계획 하는 경우 유의 해야할 사항 중 몇가지 있습니다. 디렉터리 준비는 몇 관련 된 내용을 다룹니다. 특성 업데이트, 감사, 및 도메인 컨트롤러 배치 계획 포함 됩니다. 계획 요구 사항 및 기능 포함 multiforest/디렉터리 시나리오, 용량 계획 및 양방향 동기화에 대 한 계획 필요한 사용 권한을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3c0b-p102">There are a couple of things to keep in mind when you plan an implementation of directory synchronization, including directory preparation, and the requirements and functionality of the Azure Active Directory. Directory preparation covers quite a few areas. They include attribute updates, auditing, and planning domain controller placement. Planning requirements and functionality includes determining the permissions that are required, planning for multiforest/directory scenarios, capacity planning, and two-way synchronization.</span></span>
  
## <a name="office-365-identity-models"></a><span data-ttu-id="c3c0b-110">Office 365 id 모델</span><span class="sxs-lookup"><span data-stu-id="c3c0b-110">Office 365 identity models</span></span>
<span data-ttu-id="c3c0b-111">두 기본 인증 및 id 모델을 사용 하 여 office 365: 클라우드 인증 및 연결 된 인증 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3c0b-111">Office 365 uses two main authentication and identity models: cloud authentication and federated authentication.</span></span>
  
### <a name="cloud-authentication"></a><span data-ttu-id="c3c0b-112">클라우드 인증</span><span class="sxs-lookup"><span data-stu-id="c3c0b-112">Cloud authentication</span></span>
<span data-ttu-id="c3c0b-113">[클라우드 id](about-office-365-identity.md) -만들기 및 Office 365 관리 센터에서 사용자 관리, 사용자를 관리 하려면 Windows PowerShell 또는 Azure Active Directory을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3c0b-113">[Cloud identity](about-office-365-identity.md) - create and manage users in the Office 365 admin center, you can also use Windows PowerShell, or Azure Active Directory to manage your users.</span></span> 
  
<span data-ttu-id="c3c0b-p103">[암호 해시를 원활 하 게 single sign-on 동기화](about-office-365-identity.md) -Azure AD에서 온-프레미스 디렉터리 개체에 대 한 인증을 사용 하는 가장 간단한 방법은 합니다. 암호 해시 동기화 (PHS)를 사용한 Office 365와 온-프레미스 Active Directory 사용자 계정 개체를 동기화 및 사용자가 온-프레미스를 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3c0b-p103">[Password hash sync with seamless single sign-on](about-office-365-identity.md) - The simplest way to enable authentication for on-premises directory objects in Azure AD. With password hash sync (PHS), you synchronize your on-premises Active Directory user account objects with Office 365 and manage your users on-premises.</span></span> 
  
<span data-ttu-id="c3c0b-116">하나 이상의 온-프레미스 서버에서 실행 되는 소프트웨어 에이전트를 사용 하 여 직접 사용 하는 사용자의 유효성을 검사 하려면 Azure AD 인증 서비스에 대 한 간단한 암호 유효성을 제공 하는 [원활 하 게 single sign-on 통과 인증](about-office-365-identity.md) -사용자 온-프레미스 Active Directory 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3c0b-116">[Pass-through authentication with seamless single sign-on](about-office-365-identity.md) - Provides a simple password validation for Azure AD authentication services using a software agent running on one or more on-premises servers to validate the users directly with your on-premises Active Directory.</span></span> 
  
### <a name="federated-authentication"></a><span data-ttu-id="c3c0b-117">연결 된 인증</span><span class="sxs-lookup"><span data-stu-id="c3c0b-117">Federated authentication</span></span>
<span data-ttu-id="c3c0b-118">[Active Directory Federation Services AD FS 갖는 페더레이션 id](about-office-365-identity.md) -대기업 조직 보다 복잡 한 인증 요구 사항에 대 한 주로 온-프레미스 디렉터리 개체는 Office 365와 동기화 되며 사용자 계정 관리 되는 온-프레미스 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3c0b-118">[Federated identity with Active Directory Federation Services AD FS](about-office-365-identity.md) - Primarily for large enterprise organizations with more complex authentication requirements, on-premises directory objects are synchronized with Office 365 and users accounts are managed on-premises.</span></span> 
  
<span data-ttu-id="c3c0b-119">[타사 인증 및 id 공급자](about-office-365-identity.md) -온-프레미스 디렉터리 개체를 Office 365로 동기화 될 수 및 리소스 액세스를 클라우드는 주로 타사 id 공급자 (IdP)에 의해 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3c0b-119">[Third-party authentication and identity providers](about-office-365-identity.md) - On-premises directory objects may be synchronized to Office 365 and cloud resource access is primarily managed by a third-party identity provider (IdP).</span></span> 
  
## <a name="active-directory-cleanup"></a><span data-ttu-id="c3c0b-120">Active Directory 정리</span><span class="sxs-lookup"><span data-stu-id="c3c0b-120">Active Directory Cleanup</span></span>
<span data-ttu-id="c3c0b-121">을 동기화를 사용 하 여 Office 365로 원활 하 게 전환을 보장 하기 위해 Office 365 디렉터리 동기화 배포를 시작 하기 전에 Active Directory 포리스트를 준비 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c3c0b-121">To help ensure a seamless transition to Office 365 by using synchronization, we highly recommend that you prepare your Active Directory forest before you begin your Office 365 directory synchronization deployment.</span></span>
  
<span data-ttu-id="c3c0b-p104">[다운로드 하 고 IdFix 도구를 실행](install-and-run-idfix.md)하려면이 [Office 365에서 디렉터리 동기화를 설정](set-up-directory-synchronization.md)하는 경우는 단계 중 하나입니다. [디렉터리 정리](prepare-directory-attributes-for-synch-with-idfix.md)를 위해 IdFix 도구를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3c0b-p104">When you [set up directory synchronization in Office 365](set-up-directory-synchronization.md), one of the steps is to [download and run the IdFix tool](install-and-run-idfix.md). You can use the IdFix tool to help with the [directory cleanup](prepare-directory-attributes-for-synch-with-idfix.md).</span></span>
  
<span data-ttu-id="c3c0b-124">디렉터리 정리 다음과 같은 작업에 초점 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3c0b-124">Your directory cleanup should focus on the following tasks:</span></span>

- <span data-ttu-id="c3c0b-125">중복 **되는 proxyAddress** 및 **userPrincipalName** 특성을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3c0b-125">Remove duplicate **proxyAddress** and **userPrincipalName** attributes.</span></span>
- <span data-ttu-id="c3c0b-126">비어 있거나 잘못된 **userPrincipalName** 특성을 올바른 **userPrincipalName** 특성으로 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="c3c0b-126">Update blank and invalid **userPrincipalName** attributes with valid **userPrincipalName** attributes.</span></span>
- <span data-ttu-id="c3c0b-p105">**GivenName**, 성 ( **sn** ), **sAMAccountName**, **displayName**, **메일**, **proxyAddresses**, **mailNickname**및 **userPrincipalName** 문제가 되 고 잘못 된 문자를 제거 합니다. 특성입니다. 특성을 준비 하는 방법에 대 한 자세한 내용은, [Azure Active Directory 동기화 도구에 의해 동기화 하는 특성의 목록은](https://go.microsoft.com/fwlink/p/?LinkId=396719)참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="c3c0b-p105">Remove invalid and questionable characters in the **givenName**, surname ( **sn** ), **sAMAccountName**, **displayName**, **mail**, **proxyAddresses**, **mailNickname**, and **userPrincipalName** attributes. For details about preparing attributes, see [List of attributes that are synced by the Azure Active Directory Sync Tool](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="c3c0b-129">다음은 Azure AD 연결 동기화 되는 동일한 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="c3c0b-129">These are the same attributes that Azure AD Connect syncs.</span></span> 
  
## <a name="multiforest-deployment-considerations"></a><span data-ttu-id="c3c0b-130">다중 포리스트 배포 시 고려 사항</span><span class="sxs-lookup"><span data-stu-id="c3c0b-130">Multiforest Deployment Considerations</span></span>
<span data-ttu-id="c3c0b-131">여러 포리스트 및 SSO 옵션에 대 한 [사용자 정의 설치의 Azure AD 연결](https://go.microsoft.com/fwlink/p/?LinkId=698430)을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3c0b-131">For multiple forests and SSO options, use [Custom Installation of Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430).</span></span>
  
<span data-ttu-id="c3c0b-132">조직에 인증 (로그온 포리스트)에 대 한 다중 포리스트, 하는 경우 좋습니다 다음 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3c0b-132">If your organization has multiple forests for authentication (logon forests), we highly recommend the following:</span></span>
  
- <span data-ttu-id="c3c0b-p106">**포리스트 통합 (영문) 평가.** 일반적으로 다중 포리스트를 유지 관리 하는 데 필요한 더 많은 오버 헤드가 합니다. 조직에 별도 포리스트에 대 한 필요성을 지정 하는 보안 제약 조건, 하지 않은 경우에 온-프레미스 환경의 간소화 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c3c0b-p106">**Evaluate consolidating your forests.** In general, there's more overhead required to maintain multiple forests. Unless your organization has security constraints that dictate the need for separate forests, consider simplifying your on-premises environment.</span></span>
- <span data-ttu-id="c3c0b-p107">**기본 로그온 포리스트에만 사용 합니다.** Office 365의 초기 롤아웃에 대 한 기본 로그온 포리스트에만 Office 365를 배포 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c3c0b-p107">**Use only in your primary logon forest.** Consider deploying Office 365 only in your primary logon forest for your initial rollout of Office 365.</span></span> 
    
<span data-ttu-id="c3c0b-138">다중 포리스트 Active Directory 배포에 통합할 수 없을 또는 다른 디렉터리 서비스를 사용 하 여 id가 관리 하는 경우에 Microsoft 또는 파트너를 활용 하 여 이러한 동기화 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3c0b-138">If you can't consolidate your multiforest Active Directory deployment or are using other directory services to manage identities, you may be able to synchronize these with the help of Microsoft or a partner.</span></span>
  
<span data-ttu-id="c3c0b-139">자세한 내용은 [Single Sign-on 시나리오를 사용 하는 다중 포리스트 디렉터리 동기화](https://go.microsoft.com/fwlink/p/?LinkId=525321)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="c3c0b-139">For more information, see [Multi-forest Directory Sync with Single Sign-On Scenario](https://go.microsoft.com/fwlink/p/?LinkId=525321).</span></span>
  
## <a name="directory-integration-tools"></a><span data-ttu-id="c3c0b-140">디렉터리 통합 도구</span><span class="sxs-lookup"><span data-stu-id="c3c0b-140">Directory integration tools</span></span>
<span data-ttu-id="c3c0b-p108">디렉터리 동기화 온-프레미스 Active Directory 환경에서 Office 365 디렉터리 인프라 (사용자, 그룹 및 연락처) 디렉터리 개체 동기화 시작 됩니다. 사용 가능한 도구 및 해당 기능 목록에 대 한 [디렉터리 통합 도구](https://go.microsoft.com/fwlink/p/?LinkID=510956) 참조 하십시오. 사용 하 여 권장 되는 도구 [Azure Active Directory 연결](https://go.microsoft.com/fwlink/?LinkId=525323)됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3c0b-p108">Directory synchronization is the synchronization of directory objects (users, groups, and contacts) from your on-premises Active Directory environment to the Office 365 directory infrastructure. See [directory integration tools](https://go.microsoft.com/fwlink/p/?LinkID=510956) for a list of the available tools and their functionality. The recommended tool to use is [Azure Active Directory Connect](https://go.microsoft.com/fwlink/?LinkId=525323).</span></span>
  
<span data-ttu-id="c3c0b-p109">사용자 계정의 처음으로 Office 365 디렉터리와 동기화 됩니다 활성화 되지 않은으로 표시 됩니다. 전자 메일을 수신 하거나 보낼 수는 없습니다 및 구독 라이선스를 사용 하지 않습니다. 특정 사용자에 게 Office 365 구독을 할당 하려면 준비 되 면를 선택 하 고 유효한 라이선스를 할당 하 여이 활성화 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3c0b-p109">When user accounts are synchronized with the Office 365 directory for the first time, they are marked as non-activated. They cannot send or receive email, and they don't consume subscription licenses. When you're ready to assign Office 365 subscriptions to specific users, you must select and activate them by assigning a valid license.</span></span>
  
<span data-ttu-id="c3c0b-147">디렉터리 동기화가 다음과 같은 특징 및 기능 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3c0b-147">Directory synchronization is required for the following features and functionality:</span></span>
  
- <span data-ttu-id="c3c0b-148">SSO</span><span class="sxs-lookup"><span data-stu-id="c3c0b-148">SSO</span></span>
    
- <span data-ttu-id="c3c0b-149">Lync 공존 성</span><span class="sxs-lookup"><span data-stu-id="c3c0b-149">Lync coexistence</span></span>
    
- <span data-ttu-id="c3c0b-150">Exchange 하이브리드 배포를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3c0b-150">Exchange hybrid deployment, including:</span></span>
    
  - <span data-ttu-id="c3c0b-151">온-프레미스 Exchange 환경과 Office 365 간에 공유 전체 주소 목록 (gal 전체) 완벽 하 게 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3c0b-151">Fully shared global address list (GAL) between your on-premises Exchange environment and Office 365.</span></span>
  - <span data-ttu-id="c3c0b-152">다양한 메일 시스템의 GAL 정보 동기화</span><span class="sxs-lookup"><span data-stu-id="c3c0b-152">Synchronizing GAL information from different mail systems.</span></span>
  - <span data-ttu-id="c3c0b-p110">사용자를 추가 하 고 Office 365 서비스 제품에서 사용자를 제거할 수 있습니다. 이렇게 하려면 다음이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3c0b-p110">The ability to add users to and remove users from Office 365 service offerings. This requires the following:</span></span>
  - <span data-ttu-id="c3c0b-p111">디렉터리 동기화 설치 하는 동안 양방향 동기화를 구성 해야 합니다. 기본적으로 디렉터리 동기화 도구는 클라우드로만 디렉터리 정보를 작성합니다. 양방향 동기화를 구성할 때 개체 특성의 제한 된 수의 클라우드에서 복사 되며 하 여 로컬 Active Directory에 다시 작성 있도록 쓰기 저장 기능이 활성화 합니다. 쓰기 저장 Exchange 하이브리드 모드 라고도 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3c0b-p111">Two-way synchronization must be configured during directory synchronization setup. By default, directory synchronization tools write directory information only to the cloud. When you configure two-way synchronization, you enable write-back functionality so that a limited number of object attributes are copied from the cloud, and then written them back to your local Active Directory. Write-back is also referred to as Exchange hybrid mode.</span></span> 
  - <span data-ttu-id="c3c0b-159">온-프레미스 Exchange 하이브리드 배포</span><span class="sxs-lookup"><span data-stu-id="c3c0b-159">An on-premises Exchange hybrid deployment</span></span>
  - <span data-ttu-id="c3c0b-160">Office 365에 다른 사용자 온-프레미스 사서함을 유지 하면서 일부 사용자 사서함을 이동 하는 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="c3c0b-160">The ability to move some user mailboxes to Office 365 while keeping other user mailboxes on-premises.</span></span>
  - <span data-ttu-id="c3c0b-161">수신 허용-보낸사람 및 수신된 거부 온-프레미스 Office 365로 복제 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3c0b-161">Safe senders and blocked senders on-premises are replicated to Office 365.</span></span>
  - <span data-ttu-id="c3c0b-162">기본 위임 및 대신 보내기 전자 메일 기능</span><span class="sxs-lookup"><span data-stu-id="c3c0b-162">Basic delegation and send-on-behalf-of email functionality.</span></span>
  - <span data-ttu-id="c3c0b-163">통합 된 온-프레미스 스마트 카드 또는 다단계 인증 솔루션은 해야합니다.</span><span class="sxs-lookup"><span data-stu-id="c3c0b-163">You have an integrated on-premises smart card or multi-factor authentication solution.</span></span>
    
- <span data-ttu-id="c3c0b-164">사진, 축소판 그림, 회의실 및 보안 그룹의 동기화</span><span class="sxs-lookup"><span data-stu-id="c3c0b-164">Synchronization of photos, thumbnails, conference rooms, and security groups</span></span>