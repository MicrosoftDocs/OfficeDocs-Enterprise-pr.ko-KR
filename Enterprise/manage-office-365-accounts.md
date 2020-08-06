---
title: Microsoft 365 계정 관리 도구
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: overview
ms.prod: office-online-server
localization_priority: Normal
f1.keywords:
- CSH
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
description: 'Microsoft 365 사용자를 관리 하는 데 사용할 도구에 대해 알아봅니다. '
ms.openlocfilehash: ba73d899dee002fa08f373faaed4d772da546b13
ms.sourcegitcommit: a9021ba0800ffc0da21cf2c4da67ab1da2d97099
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "46571031"
---
# <a name="tools-to-manage-microsoft-365-accounts"></a><span data-ttu-id="76245-103">Microsoft 365 계정 관리 도구</span><span class="sxs-lookup"><span data-stu-id="76245-103">Tools to manage Microsoft 365 accounts</span></span>

<span data-ttu-id="76245-104">구성에 따라 다양 한 방식으로 Microsoft 365 사용자를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76245-104">You can manage Microsoft 365 users in several different ways, depending on your configuration.</span></span> <span data-ttu-id="76245-105">[Microsoft 365 관리 센터](https://admin.microsoft.com), Windows POWERSHELL, AD DS (Active Directory 도메인 서비스) 또는 azure Ad (active directory) 관리 포털에서 사용자를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76245-105">You can manage users in the [Microsoft 365 admin center](https://admin.microsoft.com), Windows PowerShell, in Active Directory Domain Services (AD DS), or in the Azure Active Directory (Azure AD) admin portal.</span></span> 

<span data-ttu-id="76245-106">Microsoft 365을 구입 하는 즉시 관리 센터 및 Windows PowerShell을 사용 하 여 계정을 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76245-106">As soon as you purchase Microsoft 365, the admin center and Windows PowerShell can be used to manage accounts.</span></span> <span data-ttu-id="76245-107">클라우드 id를 관리할 때 조직의 모든 사용자에 게는 Microsoft 365에 대 한 별도의 사용자 ID와 암호가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76245-107">When managing cloud identities, every person in your organization has a separate user ID and password for Microsoft 365.</span></span> <span data-ttu-id="76245-108">온-프레미스 인프라와 통합 하 고 사용자 계정을 Microsoft 365와 동기화 하려면 Azure AD Connect를 사용 하 여 single sign-on 기능에 대 한 id와 암호를 동기화 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76245-108">If you want to integrate with your on-premises infrastructure and have user accounts synchronized with Microsoft 365, you can use Azure AD Connect to provide synchronization of identities and passwords for single sign-on functionality.</span></span>
  
## <a name="plan-for-where-and-how-you-will-manage-your-user-accounts"></a><span data-ttu-id="76245-109">사용자 계정을 관리 하는 위치 및 방법 계획</span><span class="sxs-lookup"><span data-stu-id="76245-109">Plan for where and how you will manage your user accounts</span></span>

<span data-ttu-id="76245-110">사용자 계정을 관리할 수 있는 위치와 방법은 Microsoft 365에 사용할 id 모델에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="76245-110">Where and how you can manage your user accounts depends on the identity model you want to use for your Microsoft 365.</span></span> <span data-ttu-id="76245-111">이 두 모델은 모두 클라우드 인증 및 페더레이션 인증입니다.</span><span class="sxs-lookup"><span data-stu-id="76245-111">The two overall models are cloud authentication and federated authentication.</span></span>
  
### <a name="cloud-authentication"></a><span data-ttu-id="76245-112">클라우드 인증</span><span class="sxs-lookup"><span data-stu-id="76245-112">Cloud authentication</span></span>

- <span data-ttu-id="76245-113">클라우드 인증-Microsoft 365 관리 센터에서 사용자를 만들고 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="76245-113">Cloud authentication - Create and manage users in the Microsoft 365 admin center.</span></span> <span data-ttu-id="76245-114">Windows PowerShell 또는 Azure AD를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76245-114">You can also use Windows PowerShell or Azure AD .</span></span> 
    
- <span data-ttu-id="76245-115">원활한 single sign-on을 사용 하는 암호 해시 동기화 (PHS)-Azure AD에서 AD DS 개체에 대 한 인증을 사용 하도록 설정 하는 가장 간단한 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="76245-115">Password hash sync (PHS) with seamless single sign-on - The simplest way to enable authentication for AD DS objects in Azure AD.</span></span> <span data-ttu-id="76245-116">PHS를 사용 하면 AD DS 사용자 계정 개체를 Microsoft 365와 동기화 하 고 온-프레미스 사용자를 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="76245-116">With PHS, you synchronize your AD DS user account objects with Microsoft 365 and manage your users on-premises.</span></span> 
    
- <span data-ttu-id="76245-117">원활한 single sign-on을 사용 하는 PTA (통과 인증)는 하나 이상의 온-프레미스 서버에서 실행 되는 소프트웨어 에이전트를 사용 하는 Azure AD 인증 서비스에 대 한 간단한 암호 유효성 검사를 제공 하 여 사용자를 AD DS와 직접 유효화 합니다.</span><span class="sxs-lookup"><span data-stu-id="76245-117">Pass-through authentication (PTA) with seamless single sign-on - Provides a simple password validation for Azure AD authentication services using a software agent running on one or more on-premises servers to validate the users directly with your AD DS.</span></span> 
    
### <a name="federated-authentication"></a><span data-ttu-id="76245-118">페더레이션 인증</span><span class="sxs-lookup"><span data-stu-id="76245-118">Federated authentication</span></span>

- <span data-ttu-id="76245-119">페더레이션 인증 옵션-주로 인증 요구 사항이 더 복잡 한 대규모 엔터프라이즈 조직의 경우 AD DS 개체는 Microsoft 365와 동기화 되 고 사용자 계정은 온-프레미스에서 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="76245-119">Federated authentication options - Primarily for large enterprise organizations with more complex authentication requirements, AD DS objects are synchronized with Microsoft 365 and users accounts are managed on-premises.</span></span> 
    
- <span data-ttu-id="76245-120">타사 [인증 및 id 공급자](about-office-365-identity.md) -AD DS 개체는 Microsoft 365와 동기화 될 수 있으며, 클라우드 리소스 액세스는 주로 타사 id 공급자 (IDP)를 통해 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="76245-120">[Third-party authentication and identity providers](about-office-365-identity.md) - AD DS objects may be synchronized to Microsoft 365 and cloud resource access is primarily managed by a third-party identity provider (IDP).</span></span> 
    
## <a name="managing-accounts"></a><span data-ttu-id="76245-121">계정 관리</span><span class="sxs-lookup"><span data-stu-id="76245-121">Managing Accounts</span></span>

<span data-ttu-id="76245-122">조직에서 계정을 만들고 관리 하는 방법을 결정할 때는 다음 요구 사항을 고려 하세요.</span><span class="sxs-lookup"><span data-stu-id="76245-122">When deciding which way your organization will create and manage accounts, consider the following requirements:</span></span>
  
- <span data-ttu-id="76245-123">Microsoft 365와 AD DS 간에 id를 연결 하려면 온-프레미스 환경 내의 서버에 디렉터리 동기화 소프트웨어를 설치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="76245-123">The directory synchronization software needs to be installed on servers within your on-premises environment to connect the identities between Microsoft 365 and your AD DS.</span></span>
    
- <span data-ttu-id="76245-124">SSO 옵션을 비롯 한 디렉터리 동기화 옵션을 사용 하려면 AD DS 특성이 표준을 충족 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="76245-124">Any directory synchronization option, including SSO options, requires your AD DS attributes meet standards.</span></span> <span data-ttu-id="76245-125">디렉터리에서 사용 되는 특성 및 필요한 정리 (있는 경우)에 대 한 자세한 내용은 [Prepare to the users to a directory synchronization to The Microsoft 365를](prepare-for-directory-synchronization.md)참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="76245-125">The specifics of what attributes are used in your directory and what cleanup (if any) is needed are described in [Prepare to provision users through directory synchronization to Microsoft 365](prepare-for-directory-synchronization.md).</span></span> 
    
- <span data-ttu-id="76245-126">Microsoft 365 계정을 만드는 방법을 계획 합니다.</span><span class="sxs-lookup"><span data-stu-id="76245-126">Plan how you are going to create Microsoft 365 accounts.</span></span>
    
    <span data-ttu-id="76245-127">다음 표에서는 다양 한 계정 관리 도구를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="76245-127">The following table lists the different account management tools.</span></span>
    
|<span data-ttu-id="76245-128">**옵션**</span><span class="sxs-lookup"><span data-stu-id="76245-128">**Option**</span></span>|<span data-ttu-id="76245-129">**참고**</span><span class="sxs-lookup"><span data-stu-id="76245-129">**Notes**</span></span>|
|:-----|:-----|
|<span data-ttu-id="76245-130">관리 센터</span><span class="sxs-lookup"><span data-stu-id="76245-130">Admin center</span></span>  <br/> |[<span data-ttu-id="76245-131">개별적으로 또는 대량으로 사용자 추가</span><span class="sxs-lookup"><span data-stu-id="76245-131">Add users individually or in bulk</span></span>](https://docs.microsoft.com/microsoft-365/admin/add-users/add-users) <br/>  <span data-ttu-id="76245-132">사용자 계정을 추가 및 변경할 수 있는 간단한 웹 인터페이스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="76245-132">Provides a simple web interface to add and change user accounts.</span></span>  <br/>  <span data-ttu-id="76245-133">디렉터리 동기화가 사용 하도록 설정 된 경우 (위치 및 라이선스 할당을 설정할 수 있음) 사용자를 변경 하는 데 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="76245-133">Can't be used to change users if directory synchronization is enabled (location and license assignment can be set).</span></span>  <br/>  <span data-ttu-id="76245-134">SSO 옵션과 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="76245-134">Can't be used with SSO options.</span></span>  <br/> |
|<span data-ttu-id="76245-135">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="76245-135">Windows PowerShell</span></span>  <br/> |[<span data-ttu-id="76245-136">Windows PowerShell을 사용 하 여 Microsoft 365 관리</span><span class="sxs-lookup"><span data-stu-id="76245-136">Manage Microsoft 365 with Windows PowerShell</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=698471) <br/>  <span data-ttu-id="76245-137">Windows PowerShell 스크립트를 사용 하 여 사용자를 대량 사용자에 게 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76245-137">Allows you to add users in bulk users by using a Windows PowerShell script.</span></span>  <br/>  <span data-ttu-id="76245-138">계정을 만드는 방법에 관계 없이 계정에 위치 및 라이선스를 할당 하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76245-138">Can be used to assign location and licenses to accounts, regardless of how the accounts are created.</span></span>  <br/> |
|<span data-ttu-id="76245-139">대량 가져오기</span><span class="sxs-lookup"><span data-stu-id="76245-139">Bulk import</span></span>  <br/> |[<span data-ttu-id="76245-140">동시에 여러 사용자 추가</span><span class="sxs-lookup"><span data-stu-id="76245-140">Add several users at the same time</span></span>](add-several-users-at-the-same-time.md) <br/>  <span data-ttu-id="76245-141">CSV 파일을 가져와서 Microsoft 365에 사용자 그룹을 추가할 수 있도록 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="76245-141">Allows you to import a CSV file to add a group of users to Microsoft 365.</span></span>  <br/>  <span data-ttu-id="76245-142">SSO 옵션과 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="76245-142">Can't be used with SSO options.</span></span>  <br/> |
|<span data-ttu-id="76245-143">Azure AD</span><span class="sxs-lookup"><span data-stu-id="76245-143">Azure AD</span></span>  <br/> |<span data-ttu-id="76245-144">Microsoft 365 구독을 사용 하 여 무료 버전의 Azure AD를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76245-144">You get a free edition of Azure AD with your Microsoft 365 subscription.</span></span> <span data-ttu-id="76245-145">클라우드 사용자에 대해 셀프 서비스 암호 재설정 및 무료 버전을 사용 하 여 로그인 및 액세스 패널 페이지의 사용자 지정과 같은 기능을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76245-145">You can perform functions like self-service password reset for cloud users, and customization of the Sign-in and Access Panel pages by using the free edition.</span></span> <span data-ttu-id="76245-146">향상 된 기능을 얻으려면 기본 에디션, Azure AD Premium P1 또는 Azure AD Premium P2로 업그레이드 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="76245-146">To get enhanced functionality, you can upgrade to the basic edition, Azure AD Premium P1, or Azure AD Premium P2.</span></span> <span data-ttu-id="76245-147">지원 되는 기능 목록은 [AZURE AD edition](https://go.microsoft.com/fwlink/p/?LinkId=698465) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="76245-147">See [Azure AD editions](https://go.microsoft.com/fwlink/p/?LinkId=698465) for the list of supported features.</span></span>  <br/> |
|<span data-ttu-id="76245-148">디렉터리 동기화</span><span class="sxs-lookup"><span data-stu-id="76245-148">Directory synchronization</span></span>  <br/> |[<span data-ttu-id="76245-149">Azure AD와 온-프레미스 id 통합</span><span class="sxs-lookup"><span data-stu-id="76245-149">Integrating your on-premises identities with Azure AD</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=624168) <br/>  <span data-ttu-id="76245-150">암호 동기화 여부와 관계 없이 디렉터리 동기화의 경우 [빠른 설정으로 AZURE AD Connect](https://go.microsoft.com/fwlink/p/?LinkID=698537)를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="76245-150">For directory synchronization with or without password synchronization, use [Azure AD Connect with express settings](https://go.microsoft.com/fwlink/p/?LinkID=698537).</span></span>  <br/>  <span data-ttu-id="76245-151">여러 포리스트와 SSO 옵션에 대해 [AZURE AD Connect의 사용자 지정 설치](https://go.microsoft.com/fwlink/p/?LinkId=698430)를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="76245-151">For multiple forests and SSO options, use [Custom Installation of Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430).</span></span>  <br/>  <span data-ttu-id="76245-152">SSO를 사용 하도록 설정 하는 데 필요한 인프라를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="76245-152">Provides the infrastructure that's necessary to enable SSO.</span></span>  <br/>  <span data-ttu-id="76245-153">다양 한 하이브리드 시나리오에 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="76245-153">Required for many hybrid scenarios:</span></span>  <br/>  <span data-ttu-id="76245-154">미리 구성된 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="76245-154">Staged migration</span></span>  <br/>  <span data-ttu-id="76245-155">하이브리드 Exchange</span><span class="sxs-lookup"><span data-stu-id="76245-155">Hybrid Exchange</span></span>  <br/>  <span data-ttu-id="76245-156">AD DS에서 보안 및 메일 사용이 가능한 그룹을 동기화 합니다.</span><span class="sxs-lookup"><span data-stu-id="76245-156">Synchronizes security and mail-enabled groups from your AD DS.</span></span>  <br/> |
   
- <span data-ttu-id="76245-157">사용자 계정을 Microsoft 365에 추가 하려는 방법에 관계 없이 라이선스 할당, 위치 지정 등 여러 가지 계정 기능을 관리 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="76245-157">Regardless of how you intend to add the user accounts to Microsoft 365, you need to manage several account features, such as assigning licenses, specifying location, and so on.</span></span> <span data-ttu-id="76245-158">이러한 기능은 관리 센터에서 장기간 관리할 수 있거나 [PowerShell을 사용 하 여 사용자 계정을 만들](https://go.microsoft.com/fwlink/p/?LinkId=717083)수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76245-158">These features can be managed long-term from the admin center or you can also [create user accounts with PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=717083).</span></span>
    
    <span data-ttu-id="76245-159">관리 센터를 통해 모든 사용자를 추가 하 고 관리 하는 경우 Microsoft 365 계정을 만드는 것과 동시에 위치를 지정 하 고 라이선스를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="76245-159">If you choose to add and manage all your users through the admin center, you will specify the location and assign licenses at the same time as creating the Microsoft 365 account.</span></span> <span data-ttu-id="76245-160">따라서 계획은 그다지 많지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="76245-160">As a result, not much planning is required.</span></span>
    
    > [!IMPORTANT]
    > <span data-ttu-id="76245-161">라이선스 (예: SharePoint Online에)를 할당 하지 않고 Microsoft 365에서 계정을 만드는 것은 계정 소유자가 Microsoft 365 center를 볼 수 있지만 회사 구독 내의 어떤 서비스에도 액세스 하지 못하는 것을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="76245-161">Creating accounts in Microsoft 365 without assigning a license (to SharePoint Online, for example) means that the account owner can view the Microsoft 365 center but can't access any of the services within your company's subscription.</span></span> <span data-ttu-id="76245-162">위치 및 라이선스를 할당 한 후에는 할당 한 서비스에 계정이 복제 됩니다.</span><span class="sxs-lookup"><span data-stu-id="76245-162">After you assign a location and the license, the account is replicated to the service or services that you assigned.</span></span> <span data-ttu-id="76245-163">사용자는 자신의 계정에 로그인 하 고 할당 한 서비스를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76245-163">The user can sign in to their account and use the services that you assigned to them.</span></span> 
  
## <a name="next-steps"></a><span data-ttu-id="76245-164">다음 단계</span><span class="sxs-lookup"><span data-stu-id="76245-164">Next steps</span></span>

[<span data-ttu-id="76245-165">Microsoft 365 통합 온-프레미스 환경</span><span class="sxs-lookup"><span data-stu-id="76245-165">Microsoft 365 integration with on-premises environments</span></span>](office-365-integration.md)
  
## <a name="see-also"></a><span data-ttu-id="76245-166">참고 항목</span><span class="sxs-lookup"><span data-stu-id="76245-166">See Also</span></span>

[<span data-ttu-id="76245-167">Microsoft 365에서 사용자 및 그룹 관리</span><span class="sxs-lookup"><span data-stu-id="76245-167">Manage users and groups in Microsoft 365</span></span>](https://docs.microsoft.com/microsoft-365/admin/add-users)
  

