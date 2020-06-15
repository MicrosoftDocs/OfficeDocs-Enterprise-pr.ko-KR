---
title: Microsoft 365에 대 한 하이브리드 id 및 디렉터리 동기화
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.date: 06/09/2020
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MOE150
- MET150
ms.assetid: d3577c90-dda5-45ca-afb0-370d2889b10f
description: Microsoft 365, Active Directory 도메인 서비스 정리 및 Azure Active Directory Connect 도구를 사용한 디렉터리 동기화에 대해 설명 합니다.
ms.openlocfilehash: b22533e66d18541b8eb72900514543367633e462
ms.sourcegitcommit: d2a3d6eeeaa07510ee94c2bc675284d893221a95
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2020
ms.locfileid: "44711871"
---
# <a name="hybrid-identity-and-directory-synchronization-for-microsoft-365"></a><span data-ttu-id="42481-103">Microsoft 365에 대 한 하이브리드 id 및 디렉터리 동기화</span><span class="sxs-lookup"><span data-stu-id="42481-103">Hybrid identity and directory synchronization for Microsoft 365</span></span>

<span data-ttu-id="42481-104">*이 문서는 Microsoft 365 Enterprise 및 Office 365 Enterprise에 모두 적용 됩니다.*</span><span class="sxs-lookup"><span data-stu-id="42481-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="42481-105">비즈니스 요구 사항과 기술 요구 사항에 따라 하이브리드 id 모델 및 디렉터리 동기화가 Microsoft 365를 채택 하는 엔터프라이즈 고객에 게 가장 일반적으로 선택 됩니다.</span><span class="sxs-lookup"><span data-stu-id="42481-105">Depending on your business needs and technical requirements, the hybrid identity model and directory synchronization is the most common choice for enterprise customers who are adopting Microsoft 365.</span></span> <span data-ttu-id="42481-106">디렉터리 동기화를 사용 하면 AD DS (Active Directory 도메인 서비스)에서 id를 관리할 수 있으며, 사용자 계정, 그룹 및 연락처에 대 한 모든 업데이트는 Microsoft 365 구독의 azure AD (azure Active Directory) 테 넌 트와 동기화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="42481-106">Directory synchronization allows you to manage identities in your Active Directory Domain Services (AD DS) and all updates to user accounts, groups, and contacts are synchronized to the Azure Active Directory (Azure AD) tenant of your Microsoft 365 subscription.</span></span>

>[!Note]
><span data-ttu-id="42481-107">AD DS 사용자 계정이 처음으로 동기화 되 면 Microsoft 365 라이선스가 자동으로 할당 되지 않으며 전자 메일과 같은 Microsoft 365 서비스에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="42481-107">When AD DS user accounts are synchronized for the first time, they are not automatically assigned a Microsoft 365 license and cannot access Microsoft 365 services, such as email.</span></span> <span data-ttu-id="42481-108">먼저 사용 위치를 할당 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="42481-108">You must first assign them a usage location.</span></span> <span data-ttu-id="42481-109">그런 다음 이러한 사용자 계정에 개별적으로 또는 동적으로 그룹 멤버 자격을 사용 하 여 라이선스를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="42481-109">Then, assign a license to these user accounts, either individually or dynamically through group membership.</span></span>
>

## <a name="authentication-for-hybrid-identity"></a><span data-ttu-id="42481-110">하이브리드 id에 대 한 인증</span><span class="sxs-lookup"><span data-stu-id="42481-110">Authentication for hybrid identity</span></span>

<span data-ttu-id="42481-111">하이브리드 id 모델을 사용 하는 경우 다음 두 가지 유형의 인증을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42481-111">There are two types of authentication when using the hybrid identity model:</span></span>

- <span data-ttu-id="42481-112">관리되는 인증</span><span class="sxs-lookup"><span data-stu-id="42481-112">Managed authentication</span></span>

  <span data-ttu-id="42481-113">Azure AD는 로컬로 저장 된 해시 버전의 암호를 사용 하 여 인증 프로세스를 처리 하거나 온-프레미스 AD DS에서 인증 하기 위해 온-프레미스 소프트웨어 에이전트로 자격 증명을 전송 합니다.</span><span class="sxs-lookup"><span data-stu-id="42481-113">Azure AD handles the authentication process by using a locally-stored hashed version of the password or sends the credentials to an on-premises software agent to be authenticated by the on-premises AD DS.</span></span>

- <span data-ttu-id="42481-114">페더레이션 인증</span><span class="sxs-lookup"><span data-stu-id="42481-114">Federated authentication</span></span>

  <span data-ttu-id="42481-115">Azure AD에서는 인증을 요청 하는 클라이언트 컴퓨터를 다른 id 공급자로 리디렉션합니다.</span><span class="sxs-lookup"><span data-stu-id="42481-115">Azure AD redirects the client computer requesting authentication to another identity provider.</span></span>

### <a name="managed-authentication"></a><span data-ttu-id="42481-116">관리되는 인증</span><span class="sxs-lookup"><span data-stu-id="42481-116">Managed authentication</span></span>

<span data-ttu-id="42481-117">관리 되는 인증에는 다음과 같은 두 가지 유형이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42481-117">There are two types of managed authentication:</span></span>

- <span data-ttu-id="42481-118">암호 해시 동기화 (PHS)</span><span class="sxs-lookup"><span data-stu-id="42481-118">Password hash synchronization (PHS)</span></span>

  <span data-ttu-id="42481-119">Azure AD는 인증 자체를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="42481-119">Azure AD performs the authentication itself.</span></span>

- <span data-ttu-id="42481-120">통과 인증(PTA)</span><span class="sxs-lookup"><span data-stu-id="42481-120">Pass-through authentication (PTA)</span></span>

  <span data-ttu-id="42481-121">Azure AD에 AD DS가 인증을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="42481-121">Azure AD has AD DS perform the authentication.</span></span>


#### <a name="password-hash-synchronization-phs"></a><span data-ttu-id="42481-122">암호 해시 동기화 (PHS)</span><span class="sxs-lookup"><span data-stu-id="42481-122">Password hash synchronization (PHS)</span></span>

<span data-ttu-id="42481-123">PHS를 사용 하면 AD DS 사용자 계정을 Microsoft 365와 동기화 하 고 온-프레미스 사용자를 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="42481-123">With PHS, you synchronize your AD DS user accounts with Microsoft 365 and manage your users on-premises.</span></span> <span data-ttu-id="42481-124">사용자 암호는 온-프레미스와 클라우드에서 동일한 암호를 사용 하도록 AD DS에서 Azure AD로 동기화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="42481-124">Hashes of user passwords are synchronized from your AD DS to Azure AD so that the users have the same password on-premises and in the cloud.</span></span> <span data-ttu-id="42481-125">Azure AD에서 AD DS id에 대 한 인증을 사용 하는 가장 간단한 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="42481-125">This is the simplest way to enable authentication for AD DS identities in Azure AD.</span></span> 

![암호 해시 동기화 (PHS)](./media/plan-for-directory-synchronization/phs-authentication.png)

<span data-ttu-id="42481-127">암호가 변경 되거나 온-프레미스에서 다시 설정 되 면 새 암호 해시가 Azure AD와 동기화 되어 사용자가 항상 클라우드 리소스 및 온-프레미스 리소스에 대해 동일한 암호를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42481-127">When passwords are changed or reset on-premises, the new password hashes are synchronized to Azure AD so that your users can always use the same password for cloud resources and on-premises resources.</span></span> <span data-ttu-id="42481-128">사용자 암호가 Azure ad로 전송 되지 않거나 Azure AD의 일반 텍스트로 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="42481-128">The user passwords are never sent to Azure AD or stored in Azure AD in clear text.</span></span> <span data-ttu-id="42481-129">Id 보호와 같은 Azure AD의 일부 프리미엄 기능은 선택한 인증 방법에 관계 없이 PHS를 요구 합니다.</span><span class="sxs-lookup"><span data-stu-id="42481-129">Some premium features of Azure AD, such as Identity Protection, require PHS regardless of which authentication method is selected.</span></span>
  
<span data-ttu-id="42481-130">자세한 정보 [는 올바른 인증 방법 선택을](https://docs.microsoft.com/azure/active-directory/hybrid/choose-ad-authn) 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="42481-130">See [choosing the right authentication method](https://docs.microsoft.com/azure/active-directory/hybrid/choose-ad-authn) to learn more.</span></span>
  
#### <a name="pass-through-authentication-pta"></a><span data-ttu-id="42481-131">통과 인증(PTA)</span><span class="sxs-lookup"><span data-stu-id="42481-131">Pass-through authentication (PTA)</span></span>

<span data-ttu-id="42481-132">PTA는 AD DS와 직접 유효성을 검사 하기 위해 하나 이상의 온-프레미스 서버에서 실행 되는 소프트웨어 에이전트를 사용 하는 Azure AD 인증 서비스에 대 한 간단한 암호 유효성 검사를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="42481-132">PTA provides a simple password validation for Azure AD authentication services using a software agent running on one or more on-premises servers to validate the users directly with your AD DS.</span></span> <span data-ttu-id="42481-133">PTA를 사용 하 여 AD DS 사용자 계정을 Microsoft 365와 동기화 하 고 온-프레미스 사용자를 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="42481-133">With PTA, you synchronize AD DS user accounts with Microsoft 365 and manage your users on-premises.</span></span> 

![통과 인증(PTA)](./media/plan-for-directory-synchronization/pta-authentication.png)

<span data-ttu-id="42481-135">PTA 사용자는 온-프레미스 계정 및 암호를 사용 하 여 온-프레미스 및 Microsoft 365 리소스와 응용 프로그램 모두에 로그인 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42481-135">PTA allows your users to sign in to both on-premises and Microsoft 365 resources and applications using their on-premises account and password.</span></span> <span data-ttu-id="42481-136">이 구성은 Azure AD에 암호 해시를 저장 하지 않고 온-프레미스 AD DS에 대해 직접 사용자 암호의 유효성을 검사 합니다.</span><span class="sxs-lookup"><span data-stu-id="42481-136">This configuration validates users passwords directly against your on-premises AD DS without storing password hashes in Azure AD.</span></span> 

<span data-ttu-id="42481-137">또한 PTA는 온-프레미스 사용자 계정 상태, 암호 정책 및 로그온 시간을 즉시 적용 하기 위한 보안 요구 사항이 있는 조직에도 적합 합니다.</span><span class="sxs-lookup"><span data-stu-id="42481-137">PTA is also for organizations with a security requirement to immediately enforce on-premises user account states, password policies, and logon hours.</span></span> 
  
<span data-ttu-id="42481-138">자세한 정보 [는 올바른 인증 방법 선택을](https://docs.microsoft.com/azure/active-directory/hybrid/choose-ad-authn) 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="42481-138">See [choosing the right authentication method](https://docs.microsoft.com/azure/active-directory/hybrid/choose-ad-authn) to learn more.</span></span>
  
### <a name="federated-authentication"></a><span data-ttu-id="42481-139">페더레이션 인증</span><span class="sxs-lookup"><span data-stu-id="42481-139">Federated authentication</span></span>

<span data-ttu-id="42481-140">페더레이션 인증은 인증 요구 사항이 더 복잡 한 대규모 엔터프라이즈 조직에 주로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="42481-140">Federated authentication is primarily for large enterprise organizations with more complex authentication requirements.</span></span> <span data-ttu-id="42481-141">AD DS id는 Microsoft 365와 동기화 되며 사용자 계정은 온-프레미스에서 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="42481-141">AD DS identities are synchronized with Microsoft 365 and users accounts are managed on-premises.</span></span> <span data-ttu-id="42481-142">페더레이션 인증을 사용 하는 경우 사용자는 온-프레미스와 클라우드에서 동일한 암호를 사용 하며, Microsoft 365을 사용할 때 다시 로그인 할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="42481-142">With federated authentication, users have the same password on-premises and in the cloud and they do not have to sign in again to use Microsoft 365.</span></span> 

<span data-ttu-id="42481-143">페더레이션 인증은 스마트 카드 기반 인증 또는 타사 다단계 인증과 같은 추가 인증 요구 사항을 지원할 수 있으며, 일반적으로 조직이 Azure AD에서 기본적으로 지원 하지 않는 인증 요구 사항을 충족 하는 경우에 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="42481-143">Federated authentication can support additional authentication requirements, such as smartcard-based authentication or a third-party multi-factor authentication and is typically required when organizations have an authentication requirement not natively supported by Azure AD.</span></span>
 
<span data-ttu-id="42481-144">자세한 정보 [는 올바른 인증 방법 선택을](https://docs.microsoft.com/azure/active-directory/hybrid/choose-ad-authn) 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="42481-144">See [choosing the right authentication method](https://docs.microsoft.com/azure/active-directory/hybrid/choose-ad-authn) to learn more.</span></span>
  
#### <a name="third-party-authentication-and-identity-providers"></a><span data-ttu-id="42481-145">타사 인증 및 id 공급자</span><span class="sxs-lookup"><span data-stu-id="42481-145">Third-party authentication and identity providers</span></span>

<span data-ttu-id="42481-146">온-프레미스 디렉터리 개체는 Microsoft 365와 동기화 될 수 있으며, 클라우드 리소스 액세스는 주로 타사 id 공급자 (IdP)를 통해 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="42481-146">On-premises directory objects may be synchronized to Microsoft 365 and cloud resource access is primarily managed by a third-party identity provider (IdP).</span></span> <span data-ttu-id="42481-147">조직에서 타사 페더레이션 솔루션을 사용 하는 경우 타사 페더레이션 솔루션을 Azure AD와 호환 되는 Microsoft 365 솔루션을 사용 하 여 로그온을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42481-147">If your organization uses a third-party federation solution, you can configure sign-on with that solution for Microsoft 365 provided that the third-party federation solution is compatible with Azure AD.</span></span>
  
<span data-ttu-id="42481-148">자세한 내용은 [AZURE AD 페더레이션 호환성 목록을](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility) 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="42481-148">See the [Azure AD federation compatibility list](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility) to learn more.</span></span>
  
## <a name="ad-ds-cleanup"></a><span data-ttu-id="42481-149">AD DS 정리</span><span class="sxs-lookup"><span data-stu-id="42481-149">AD DS Cleanup</span></span>

<span data-ttu-id="42481-150">동기화를 사용 하 여 Microsoft 365로 원활 하 게 전환할 수 있도록 하려면 Microsoft 365 디렉터리 동기화 배포를 시작 하기 전에 AD DS 포리스트를 준비 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="42481-150">To help ensure a seamless transition to Microsoft 365 by using synchronization, you must prepare your AD DS forest before you begin your Microsoft 365 directory synchronization deployment.</span></span>
  
<span data-ttu-id="42481-151">[디렉터리 동기화를 설정](set-up-directory-synchronization.md)하는 경우에는 [idfix 도구를 다운로드 하 고 실행](install-and-run-idfix.md)하는 단계 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="42481-151">When you [set up directory synchronization](set-up-directory-synchronization.md), one of the steps is to [download and run the IdFix tool](install-and-run-idfix.md).</span></span> <span data-ttu-id="42481-152">IdFix 도구를 사용 하 여 [디렉터리 정리](prepare-directory-attributes-for-synch-with-idfix.md)를 지원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42481-152">You can use the IdFix tool to help with [directory cleanup](prepare-directory-attributes-for-synch-with-idfix.md).</span></span>
  
<span data-ttu-id="42481-153">디렉터리 정리는 다음 작업에 중점을 두어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="42481-153">Your directory cleanup should focus on the following tasks:</span></span>

- <span data-ttu-id="42481-154">중복 **Proxyaddress** 및 **userPrincipalName** 특성을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="42481-154">Remove duplicate **proxyAddress** and **userPrincipalName** attributes.</span></span>
- <span data-ttu-id="42481-155">비어 있거나 잘못 된 **userPrincipalName** 특성을 올바른 **userPrincipalName** 특성으로 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="42481-155">Update blank and invalid **userPrincipalName** attributes with valid **userPrincipalName** attributes.</span></span>
- <span data-ttu-id="42481-156">**GivenName**, 성 ( **Sn** ), **sAMAccountName**, **displayName**, **mail**, **proxyAddresses**, **mailNickname**및 **userPrincipalName** 특성에서 잘못 되었거나 불확실 한 문자를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="42481-156">Remove invalid and questionable characters in the **givenName**, surname ( **sn** ), **sAMAccountName**, **displayName**, **mail**, **proxyAddresses**, **mailNickname**, and **userPrincipalName** attributes.</span></span> <span data-ttu-id="42481-157">특성을 준비 하는 방법에 대 한 자세한 내용은 [Azure Active Directory 동기화 도구를 통해 동기화 되는 특성 목록을](https://go.microsoft.com/fwlink/p/?LinkId=396719)참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="42481-157">For details about preparing attributes, see [List of attributes that are synced by the Azure Active Directory Sync Tool](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span></span>

    > [!NOTE]
    > <span data-ttu-id="42481-158">Azure AD Connect에서 동기화 하는 것과 동일한 특성이 여기에 해당 됩니다.</span><span class="sxs-lookup"><span data-stu-id="42481-158">These are the same attributes that Azure AD Connect synchronizes.</span></span> 
  
## <a name="multi-forest-deployment-considerations"></a><span data-ttu-id="42481-159">다중 포리스트 배포 시 고려 사항</span><span class="sxs-lookup"><span data-stu-id="42481-159">Multi-forest deployment considerations</span></span>

<span data-ttu-id="42481-160">여러 포리스트와 SSO 옵션에 대해 [AZURE AD Connect의 사용자 지정 설치](https://go.microsoft.com/fwlink/p/?LinkId=698430)를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="42481-160">For multiple forests and SSO options, use a [Custom Installation of Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430).</span></span>
  
<span data-ttu-id="42481-161">조직에 인증 (로그온 포리스트)을 위한 포리스트가 여러 개 있는 경우에는 다음을 수행 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="42481-161">If your organization has multiple forests for authentication (logon forests), we highly recommend the following:</span></span>
  
- <span data-ttu-id="42481-162">**포리스트를 통합 하는 것이 좋습니다.**</span><span class="sxs-lookup"><span data-stu-id="42481-162">**Consider consolidating your forests.**</span></span> <span data-ttu-id="42481-163">일반적으로 여러 포리스트를 유지 관리 하려면 오버 헤드가 더 많이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="42481-163">In general, there's more overhead required to maintain multiple forests.</span></span> <span data-ttu-id="42481-164">조직에 별도의 포리스트에 대 한 요구를 규정 하는 보안 제약 조건이 없는 경우에는 온-프레미스 환경을 단순화 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="42481-164">Unless your organization has security constraints that dictate the need for separate forests, consider simplifying your on-premises environment.</span></span>
- <span data-ttu-id="42481-165">**기본 로그온 포리스트에서만 사용 합니다.**</span><span class="sxs-lookup"><span data-stu-id="42481-165">**Use only in your primary logon forest.**</span></span> <span data-ttu-id="42481-166">Microsoft 365의 초기 롤아웃을 위한 Microsoft 365만 기본 로그온 포리스트에 배포 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="42481-166">Consider deploying Microsoft 365 only in your primary logon forest for your initial rollout of Microsoft 365.</span></span> 

<span data-ttu-id="42481-167">다중 포리스트 AD DS 배포를 통합할 수 없거나 다른 디렉터리 서비스를 사용 하 여 id를 관리 하는 경우에는 이러한 정보를 Microsoft 또는 파트너의 도움말과 동기화 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42481-167">If you can't consolidate your multi-forest AD DS deployment or are using other directory services to manage identities, you may be able to synchronize these with the help of Microsoft or a partner.</span></span>
  
<span data-ttu-id="42481-168">자세한 내용은 [AZURE AD Connect에 대 한 토폴로지](https://docs.microsoft.com/azure/active-directory/hybrid/plan-connect-topologies) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="42481-168">See [Topologies for Azure AD Connect](https://docs.microsoft.com/azure/active-directory/hybrid/plan-connect-topologies) for more information.</span></span>
  
## <a name="features-that-are-dependent-on-directory-synchronization"></a><span data-ttu-id="42481-169">디렉터리 동기화에 따라 달라 지는 기능</span><span class="sxs-lookup"><span data-stu-id="42481-169">Features that are dependent on directory synchronization</span></span>
  
<span data-ttu-id="42481-170">디렉터리 동기화는 다음과 같은 기능을 수행 하는 데 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="42481-170">Directory synchronization is required for the following features and functionality:</span></span>
  
- <span data-ttu-id="42481-171">Azure AD에 원활한 SSO (Single Sign-on)</span><span class="sxs-lookup"><span data-stu-id="42481-171">Azure AD Seamless Single Sign-On (SSO)</span></span>
- <span data-ttu-id="42481-172">Skype 동시 사용</span><span class="sxs-lookup"><span data-stu-id="42481-172">Skype coexistence</span></span>
- <span data-ttu-id="42481-173">다음을 포함 한 Exchange 하이브리드 배포</span><span class="sxs-lookup"><span data-stu-id="42481-173">Exchange hybrid deployment, including:</span></span>
  - <span data-ttu-id="42481-174">온-프레미스 Exchange 환경과 Microsoft 365 간에 완전히 공유 되는 GAL (전체 주소 목록)입니다.</span><span class="sxs-lookup"><span data-stu-id="42481-174">Fully shared global address list (GAL) between your on-premises Exchange environment and Microsoft 365.</span></span>
  - <span data-ttu-id="42481-175">다양 한 메일 시스템에서 GAL 정보 동기화</span><span class="sxs-lookup"><span data-stu-id="42481-175">Synchronizing GAL information from different mail systems.</span></span>
  - <span data-ttu-id="42481-176">Microsoft 365 서비스 제품에서 사용자를 추가 및 제거 하는 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="42481-176">The ability to add users to and remove users from Microsoft 365 service offerings.</span></span> <span data-ttu-id="42481-177">이를 위해서는 다음이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="42481-177">This requires the following:</span></span>
  - <span data-ttu-id="42481-178">양방향 동기화는 디렉터리 동기화 설정 중에 구성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="42481-178">Two-way synchronization must be configured during directory synchronization setup.</span></span> <span data-ttu-id="42481-179">기본적으로 디렉터리 동기화 도구는 디렉터리 정보를 클라우드에만 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="42481-179">By default, directory synchronization tools write directory information only to the cloud.</span></span> <span data-ttu-id="42481-180">양방향 동기화를 구성 하는 경우 제한 된 수의 개체 특성이 클라우드에서 복사 되 고 로컬 AD DS에 다시 기록 되도록 쓰기 기능을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="42481-180">When you configure two-way synchronization, you enable write-back functionality so that a limited number of object attributes are copied from the cloud, and then written them back to your local AD DS.</span></span> <span data-ttu-id="42481-181">쓰기 저장은 Exchange 하이브리드 모드 라고도 합니다.</span><span class="sxs-lookup"><span data-stu-id="42481-181">Write-back is also referred to as Exchange hybrid mode.</span></span> 
  - <span data-ttu-id="42481-182">온-프레미스 Exchange 하이브리드 배포</span><span class="sxs-lookup"><span data-stu-id="42481-182">An on-premises Exchange hybrid deployment</span></span>
  - <span data-ttu-id="42481-183">다른 사용자 사서함을 온-프레미스에 유지 하면서 일부 사용자 사서함을 Microsoft 365로 이동 하는 기능</span><span class="sxs-lookup"><span data-stu-id="42481-183">The ability to move some user mailboxes to Microsoft 365 while keeping other user mailboxes on-premises.</span></span>
  - <span data-ttu-id="42481-184">온-프레미스의 수신 허용 및 수신 거부는 Microsoft 365에 복제 됩니다.</span><span class="sxs-lookup"><span data-stu-id="42481-184">Safe senders and blocked senders on-premises are replicated to Microsoft 365.</span></span>
  - <span data-ttu-id="42481-185">기본 위임 및 대신 보내기 전자 메일 기능</span><span class="sxs-lookup"><span data-stu-id="42481-185">Basic delegation and send-on-behalf-of email functionality.</span></span>
  - <span data-ttu-id="42481-186">통합 된 온-프레미스 스마트 카드 또는 다단계 인증 솔루션을 사용 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42481-186">You have an integrated on-premises smart card or multi-factor authentication solution.</span></span>
- <span data-ttu-id="42481-187">사진, 축소판 그림, 회의실 및 보안 그룹 동기화</span><span class="sxs-lookup"><span data-stu-id="42481-187">Synchronization of photos, thumbnails, conference rooms, and security groups</span></span>

## <a name="next-step"></a><span data-ttu-id="42481-188">다음 단계</span><span class="sxs-lookup"><span data-stu-id="42481-188">Next step</span></span>

<span data-ttu-id="42481-189">하이브리드 id를 배포할 준비가 되 면 [사용자 프로 비전 준비를](prepare-for-directory-synchronization.md)참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="42481-189">When you are ready to deploy hybrid identity, see [prepare to provision users](prepare-for-directory-synchronization.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="42481-190">참고 항목</span><span class="sxs-lookup"><span data-stu-id="42481-190">See also</span></span>

[<span data-ttu-id="42481-191">Microsoft 365 Enterprise 개요</span><span class="sxs-lookup"><span data-stu-id="42481-191">Microsoft 365 Enterprise overview</span></span>](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)

