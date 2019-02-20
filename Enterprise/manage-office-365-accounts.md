---
title: Office 365 계정 관리 도구
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 5/3/2018
ms.audience: Admin
ms.topic: overview
ms.prod: office-online-server
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-subscription-management
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: 98ca5b3f-f720-4d8e-91be-fe656548a25a
description: 'Office 365 사용자를 관리 하는 데 사용할 도구와 사용자 id를 관리 하는 방법에 따라 사용할 수 있는 작업에 대해 알아봅니다. '
ms.openlocfilehash: 0fa515d89afa3abe4b0fe936b297156b20890b0f
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085367"
---
# <a name="tools-to-manage-office-365-accounts"></a><span data-ttu-id="894f6-103">Office 365 계정 관리 도구</span><span class="sxs-lookup"><span data-stu-id="894f6-103">Tools to manage Office 365 accounts</span></span>

<span data-ttu-id="894f6-p101">구성에 따라 다양 한 방식으로 Office 365 사용자를 관리할 수 있습니다. Office 365 관리 센터, Windows PowerShell, 온-프레미스 디렉터리 또는 Azure Active directory 관리 포털에서 사용자를 관리할 수 있습니다. Office 365을 구입 하는 즉시 관리 센터 및 Windows PowerShell을 사용 하 여 계정을 관리할 수 있습니다. 조직의 모든 사용자가 클라우드 id를 관리할 때 Office 365에 대해 별도의 사용자 ID와 암호를 사용 합니다. 온-프레미스 인프라와 통합 하 고 사용자 계정이 Office 365와 동기화 되도록 하려면 Azure Active Directory Connect를 사용 하 여 id 동기화를 제공 하 고, 선택적으로 암호 동기화를 제공 하거나, 전체를 제공할 수 있습니다. single sign-on 기능</span><span class="sxs-lookup"><span data-stu-id="894f6-p101">You can manage Office 365 users in several different ways, depending on your configuration. You can manage users in the Office 365 admin center, Windows PowerShell, your on-premises directory, or in Azure Active Directory admin portal . As soon as you purchase Office 365, the admin center and Windows PowerShell can be used to manage accounts. When managing cloud identities every person in your organization has a separate user ID and password for Office 365. If you want to integrate with your on-premises infrastructure and have user accounts synchronized with Office 365, you can use Azure Active Directory Connect to provide synchronization of identities and optionally provide password synchronization, or full single sign-on functionality.</span></span>
  
## <a name="plan-for-where-and-how-you-will-manage-your-user-accounts"></a><span data-ttu-id="894f6-109">사용자 계정을 관리 하는 위치 및 방법 계획</span><span class="sxs-lookup"><span data-stu-id="894f6-109">Plan for where and how you will manage your user accounts</span></span>

<span data-ttu-id="894f6-p102">사용자 계정을 관리할 수 있는 위치와 방법은 Office 365에 사용할 id 모델에 따라 달라 집니다. 이 두 모델은 모두 클라우드 인증 및 페더레이션 인증입니다.</span><span class="sxs-lookup"><span data-stu-id="894f6-p102">Where and how you can manage your user accounts depends on the identity model you want to use for your Office 365. The two overall models are cloud authentication and federated authentication.</span></span>
  
### <a name="cloud-authentication"></a><span data-ttu-id="894f6-112">클라우드 인증</span><span class="sxs-lookup"><span data-stu-id="894f6-112">Cloud authentication</span></span>

- <span data-ttu-id="894f6-113">[클라우드 인증](about-office-365-identity.md#cloud-authentication) -Office 365 관리 센터에서 사용자를 만들고 관리 하 고, Windows PowerShell 또는 Azure Active Directory를 사용 하 여 사용자를 관리할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="894f6-113">[Cloud authentication](about-office-365-identity.md#cloud-authentication) - create and manage users in the Office 365 admin center, you can also use Windows PowerShell, or Azure Active Directory to manage your users.</span></span> 
    
- <span data-ttu-id="894f6-p103">[원활한 single sign-on을 사용한 암호 해시 동기화](about-office-365-identity.md) -Azure AD의 온-프레미스 디렉터리 개체에 대 한 인증을 사용 하도록 설정 하는 가장 간단한 방법입니다. 암호 해시 동기화 (phs)를 사용 하 여 온-프레미스 Active Directory 사용자 계정 개체를 Office 365와 동기화 하 고 온-프레미스 사용자를 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="894f6-p103">[Password hash sync with seamless single sign-on](about-office-365-identity.md) - The simplest way to enable authentication for on-premises directory objects in Azure AD. With password hash sync (PHS), you synchronize your on-premises Active Directory user account objects with Office 365 and manage your users on-premises.</span></span> 
    
- <span data-ttu-id="894f6-116">[원활한 single sign-on을 통한 통과 인증](about-office-365-identity.md) -하나 이상의 온-프레미스 서버에서 실행 되는 소프트웨어 에이전트를 사용 하 여 Azure AD 인증 서비스에 대 한 간단한 암호 유효성 검사를 제공 하 여 사용자의 유효성을 직접 검사 합니다. 온-프레미스 Active Directory</span><span class="sxs-lookup"><span data-stu-id="894f6-116">[Pass-through authentication with seamless single sign-on](about-office-365-identity.md) - Provides a simple password validation for Azure AD authentication services using a software agent running on one or more on-premises servers to validate the users directly with your on-premises Active Directory.</span></span> 
    
### <a name="federated-authentication"></a><span data-ttu-id="894f6-117">페더레이션 인증</span><span class="sxs-lookup"><span data-stu-id="894f6-117">Federated authentication</span></span>

- <span data-ttu-id="894f6-118">[페더레이션 인증 옵션](about-office-365-identity.md#federated-authentication-options) -주로 인증 요구 사항이 더 복잡 한 대규모 엔터프라이즈 조직의 경우 온-프레미스 디렉터리 개체는 Office 365와 동기화 되 고 사용자 계정은 온-프레미스에서 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="894f6-118">[Federated authentication options](about-office-365-identity.md#federated-authentication-options) - Primarily for large enterprise organizations with more complex authentication requirements, on-premises directory objects are synchronized with Office 365 and users accounts are managed on-premises.</span></span> 
    
- <span data-ttu-id="894f6-119">타사 [인증 및 id 공급자](about-office-365-identity.md) -온-프레미스 디렉터리 개체는 Office 365와 동기화 될 수 있으며, 클라우드 리소스 액세스는 주로 타사 id 공급자 (IdP)를 통해 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="894f6-119">[Third-party authentication and identity providers](about-office-365-identity.md) - On-premises directory objects may be synchronized to Office 365 and cloud resource access is primarily managed by a third-party identity provider (IdP).</span></span> 
    
## <a name="managing-accounts"></a><span data-ttu-id="894f6-120">계정 관리</span><span class="sxs-lookup"><span data-stu-id="894f6-120">Managing Accounts</span></span>

<span data-ttu-id="894f6-121">조직에서 계정을 만들고 관리 하는 방법을 결정할 때는 다음 사항을 고려 하십시오.</span><span class="sxs-lookup"><span data-stu-id="894f6-121">When deciding which way your organization will create and manage accounts, consider the following:</span></span>
  
- <span data-ttu-id="894f6-122">Office 365와 온-프레미스 디렉터리 간에 id를 연결 하려면 온-프레미스 환경 내의 서버에 디렉터리 동기화 소프트웨어를 설치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="894f6-122">The directory synchronization software needs to be installed on servers within your on-premises environment to connect the identities between Office 365 and your on-premises directory.</span></span>
    
- <span data-ttu-id="894f6-p104">SSO 옵션을 비롯 한 디렉터리 동기화 옵션을 사용 하려면 온-프레미스 디렉터리 특성이 표준을 충족 해야 합니다. 디렉터리에서 사용 되는 특성에 대 한 구체적인 내용과 필요한 정리 (있는 경우)는 [Office 365에 대 한 디렉터리 동기화를 통한 사용자 프로 비전 준비](prepare-for-directory-synchronization.md)에서 설명 합니다. idfix를 사용 하 여 디렉터리 정리를 자동화 하는 방법에 대 한 지침은 [Office 365 idfix 도구 설치 및 실행](install-and-run-idfix.md) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="894f6-p104">Any directory synchronization option, including SSO options, requires your on-premises directory attributes meet standards. The specifics of what attributes are used in your directory and what cleanup (if any) is needed are described in [Prepare to provision users through directory synchronization to Office 365](prepare-for-directory-synchronization.md). See [Install and run the Office 365 IdFix tool](install-and-run-idfix.md) for instruction on how to use IdFix to automate directory cleanup.</span></span> 
    
- <span data-ttu-id="894f6-126">Office 365 계정을 만드는 방법을 계획 합니다.</span><span class="sxs-lookup"><span data-stu-id="894f6-126">Plan how you are going to create Office 365 accounts.</span></span>
    
    <span data-ttu-id="894f6-127">다음 표에서는 다양 한 계정 관리 도구를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="894f6-127">The following table lists the different account management tools.</span></span>
    
|<span data-ttu-id="894f6-128">**옵션**</span><span class="sxs-lookup"><span data-stu-id="894f6-128">**Option**</span></span>|<span data-ttu-id="894f6-129">**참고**</span><span class="sxs-lookup"><span data-stu-id="894f6-129">**Notes**</span></span>|
|:-----|:-----|
|<span data-ttu-id="894f6-130">Office 365 admin center</span><span class="sxs-lookup"><span data-stu-id="894f6-130">Office 365 admin center</span></span>  <br/> |[<span data-ttu-id="894f6-131">Office 365에 개별적으로 또는 대량으로 사용자 추가 - 관리자 도움말</span><span class="sxs-lookup"><span data-stu-id="894f6-131">Add users individually or in bulk to Office 365 - Admin Help</span></span>](https://support.office.com/article/1970f7d6-03b5-442f-b385-5880b9c256ec) <br/>  <span data-ttu-id="894f6-132">사용자 계정을 추가 및 변경할 수 있는 간단한 웹 인터페이스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="894f6-132">Provides a simple web interface to add and change user accounts.</span></span>  <br/>  <span data-ttu-id="894f6-133">디렉터리 동기화가 사용 하도록 설정 된 경우 (위치 및 라이선스 할당을 설정할 수 있음) 사용자를 변경 하는 데 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="894f6-133">Can't be used to change users if directory synchronization is enabled (location and license assignment can be set).</span></span>  <br/>  <span data-ttu-id="894f6-134">SSO 옵션과 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="894f6-134">Can't be used with SSO options.</span></span>  <br/> |
|<span data-ttu-id="894f6-135">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="894f6-135">Windows PowerShell</span></span>  <br/> |[<span data-ttu-id="894f6-136">Windows PowerShell로 Office 365 관리</span><span class="sxs-lookup"><span data-stu-id="894f6-136">Manage Office 365 with Windows PowerShell</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=698471) <br/>  <span data-ttu-id="894f6-137">Windows PowerShell 스크립트를 사용 하 여 사용자를 대량 사용자에 게 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="894f6-137">Allows you to add users in bulk users by using a Windows PowerShell script.</span></span>  <br/>  <span data-ttu-id="894f6-138">계정을 만드는 방법에 관계 없이 계정에 위치 및 라이선스를 할당 하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="894f6-138">Can be used to assign location and licenses to accounts, regardless of how the accounts are created.</span></span>  <br/> |
|<span data-ttu-id="894f6-139">대량 가져오기</span><span class="sxs-lookup"><span data-stu-id="894f6-139">Bulk import</span></span>  <br/> |[<span data-ttu-id="894f6-140">Office 365에 여러 사용자를 동시에 추가 - 관리자 도움말</span><span class="sxs-lookup"><span data-stu-id="894f6-140">Add several users at the same time to Office 365 - Admin Help</span></span>](add-several-users-at-the-same-time.md) <br/>  <span data-ttu-id="894f6-141">CSV 파일을 가져와서 Office 365에 사용자 그룹을 추가할 수 있도록 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="894f6-141">Allows you to import a CSV file to add a group of users to Office 365.</span></span>  <br/>  <span data-ttu-id="894f6-142">SSO 옵션과 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="894f6-142">Can't be used with SSO options.</span></span>  <br/> |
|<span data-ttu-id="894f6-143">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="894f6-143">Azure Active Directory</span></span>  <br/> |<span data-ttu-id="894f6-p105">Office 365 구독을 사용 하 여 무료 버전의 Azure Active Directory를 사용할 수 있습니다. 클라우드 사용자에 대해 셀프 서비스 암호 재설정 및 무료 버전을 사용 하 여 로그인 및 액세스 패널 페이지의 사용자 지정과 같은 기능을 수행할 수 있습니다. 향상 된 기능을 얻으려면 기본 버전 또는 premium edition으로 업그레이드 하면 됩니다. 지원 되는 기능 목록은 [Azure Active Directory edition](https://go.microsoft.com/fwlink/p/?LinkId=698465) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="894f6-p105">You get a free edition of Azure Active Directory with your Office 365 subscription. You can perform functions like self-service password reset for cloud users, and customization of the Sign-in and Access Panel pages by using the free edition. To get enhanced functionality, you can upgrade to either the basic edition, or the premium edition. See [Azure Active Directory editions](https://go.microsoft.com/fwlink/p/?LinkId=698465) for the list of supported features.  </span></span><br/> |
|<span data-ttu-id="894f6-148">디렉터리 동기화</span><span class="sxs-lookup"><span data-stu-id="894f6-148">Directory synchronization</span></span>  <br/> |[<span data-ttu-id="894f6-149">Azure Active Directory에 온-프레미스 id 통합</span><span class="sxs-lookup"><span data-stu-id="894f6-149">Integrating your on-premises identities with Azure Active Directory</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=624168) <br/>  <span data-ttu-id="894f6-150">암호 동기화 여부와 관계 없이 디렉터리 동기화의 경우 [빠른 설정으로 Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkID=698537)를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="894f6-150">For directory synchronization with or without password synchronization, use [Azure AD Connect with express settings](https://go.microsoft.com/fwlink/p/?LinkID=698537).</span></span>  <br/>  <span data-ttu-id="894f6-151">여러 포리스트와 SSO 옵션에 대해 [Azure AD Connect의 사용자 지정 설치](https://go.microsoft.com/fwlink/p/?LinkId=698430)를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="894f6-151">For multiple forests and SSO options, use [Custom Installation of Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430).</span></span>  <br/>  <span data-ttu-id="894f6-152">SSO를 사용 하도록 설정 하는 데 필요한 인프라를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="894f6-152">Provides the infrastructure that's necessary to enable SSO.</span></span>  <br/>  <span data-ttu-id="894f6-153">다양 한 하이브리드 시나리오에 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="894f6-153">Required for many hybrid scenarios:</span></span>  <br/>  <span data-ttu-id="894f6-154">미리 구성된 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="894f6-154">Staged migration</span></span>  <br/>  <span data-ttu-id="894f6-155">하이브리드 Exchange</span><span class="sxs-lookup"><span data-stu-id="894f6-155">Hybrid Exchange</span></span>  <br/>  <span data-ttu-id="894f6-156">온-프레미스 디렉터리의 보안 및 메일 사용 가능 그룹을 동기화합니다.</span><span class="sxs-lookup"><span data-stu-id="894f6-156">Synchronizes security and mail-enabled groups from your on-premises directory.</span></span>  <br/> |
   
- <span data-ttu-id="894f6-p106">사용자 계정을 Office 365에 추가 하려는 방법에 관계 없이 라이선스 할당, 위치 지정 등 여러 가지 계정 기능을 관리 해야 합니다. 이러한 기능은 office 365 관리 센터에서 장기간 관리할 수 있거나 [office 365 PowerShell을 사용 하 여 사용자 계정을 만들](https://go.microsoft.com/fwlink/p/?LinkId=717083)수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="894f6-p106">Regardless of how you intend to add the user accounts to Office 365, you need to manage several account features, such as assigning licenses, specifying location, and so on. These features can be managed long-term from the Office 365 admin center or you can also [create user accounts with Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=717083).</span></span>
    
    <span data-ttu-id="894f6-p107">office 365 관리 센터를 통해 모든 사용자를 추가 하 고 관리 하는 경우 office 365 계정을 만드는 것과 동일한 시간에 위치를 지정 하 고 라이선스를 할당 합니다. 따라서 계획은 그다지 많지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="894f6-p107">If you choose to add and manage all your users through the Office 365 admin center, you will specify the location and assign licenses at the same time as creating the Office 365 account. As a result, not much planning is required.</span></span>
    
    > [!IMPORTANT]
    > <span data-ttu-id="894f6-p108">라이선스 (예: SharePoint Online에)를 할당 하지 않고 office 365에서 계정을 만드는 것은 계정 소유자가 Office 365 포털을 볼 수 있지만 회사 구독 내의 어떤 서비스에도 액세스 하지 못하는 것을 의미 합니다. 위치 및 라이선스를 할당 한 후에는 할당 한 서비스에 계정이 복제 됩니다. 사용자는 자신의 계정에 로그인 하 고 할당 한 서비스를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="894f6-p108">Creating accounts in Office 365 without assigning a license (to SharePoint Online, for example) means that the account owner can view the Office 365 portal but can't access any of the services within your company's subscription. After you assign a location and the license, the account is replicated to the service or services that you assigned. The user can sign in to their account and use the services that you assigned to them.</span></span> 
  
## <a name="next-steps"></a><span data-ttu-id="894f6-164">다음 단계</span><span class="sxs-lookup"><span data-stu-id="894f6-164">Next steps</span></span>

[<span data-ttu-id="894f6-165">도메인을 사용하여 온-프레미스 전자 메일과 통합(예: 디렉터리 서비스 사용)</span><span class="sxs-lookup"><span data-stu-id="894f6-165">Office 365 integration with on-premises environments</span></span>](office-365-integration.md)
  
## <a name="see-also"></a><span data-ttu-id="894f6-166">참고 항목</span><span class="sxs-lookup"><span data-stu-id="894f6-166">See Also</span></span>

[<span data-ttu-id="894f6-167">Office 365에서 사용자 계정 관리</span><span class="sxs-lookup"><span data-stu-id="894f6-167">Manage user accounts in Office 365</span></span>](https://support.office.com/article/3204162b-0b6c-4838-8a11-394b9bfd31de.aspx)
  

