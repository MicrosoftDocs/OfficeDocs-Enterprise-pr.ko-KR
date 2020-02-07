---
title: 온-프레미스 환경과 Office 365 통합
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 10/08/2019
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
search.appverid:
- MET150
- LYN150
- SPS150
- MOE150
- MED150
ms.assetid: 263faf8d-aa21-428b-aed3-2021837a4b65
description: Office 365를 기존 디렉터리 서비스와 통합 하는 방법에 대해 알아봅니다.
ms.openlocfilehash: 61feabb4d62b4b67538f45a3f827c746197b55d3
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844499"
---
# <a name="office-365-integration-with-on-premises-environments"></a><span data-ttu-id="56bd1-103">온-프레미스 환경과 Office 365 통합</span><span class="sxs-lookup"><span data-stu-id="56bd1-103">Office 365 integration with on-premises environments</span></span>

<span data-ttu-id="56bd1-104">*이 문서는 Microsoft 365 Enterprise와 Office 365 Enterprise에 모두 적용됩니다.*</span><span class="sxs-lookup"><span data-stu-id="56bd1-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="56bd1-105">Office 365을 기존 디렉터리 서비스와 통합 하 고 Exchange Server의 온-프레미스 설치, 비즈니스용 Skype 서버 2015 또는 SharePoint Server와 통합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56bd1-105">You can integrate Office 365 with your existing directory services and with an on-premises installation of Exchange Server, Skype for Business Server 2015, or SharePoint Server.</span></span>
  
 - <span data-ttu-id="56bd1-106">디렉터리 서비스와 통합 하는 경우 두 환경의 사용자 계정을 동기화 하 고 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56bd1-106">When you integrate with directory services, you can synchronize and manage user accounts for both environments.</span></span> <span data-ttu-id="56bd1-107">또한 사용자가 온-프레미스 자격 증명을 사용 하 여 두 환경에 로그온 할 수 있도록 암호 해시 동기화 또는 SSO (single sign-on)를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56bd1-107">You can also add password hash synchronization or single sign-on (SSO) so users can log on to both environments with their on-premises credentials.</span></span>
 - <span data-ttu-id="56bd1-108">온-프레미스 서버 제품과 통합 하는 경우 하이브리드 환경을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="56bd1-108">When you integrate with on-premises server products, you create a hybrid environment.</span></span> <span data-ttu-id="56bd1-109">하이브리드 환경은 사용자 또는 정보를 Office 365로 마이그레이션하는 데 도움이 되거나, 일부 사용자 또는 일부 정보를 온-프레미스와 클라우드에서 계속 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56bd1-109">A hybrid environment can help as you migrate users or information to Office 365, or you can continue to have some users or some information on-premises and some in the cloud.</span></span> <span data-ttu-id="56bd1-110">하이브리드 환경에 대 한 자세한 내용은 [하이브리드 클라우드 개요](https://docs.microsoft.com/Office365/Enterprise/hybrid-cloud-overview)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="56bd1-110">For more information about hybrid environments, see [Hybrid cloud overview](https://docs.microsoft.com/Office365/Enterprise/hybrid-cloud-overview).</span></span>

<span data-ttu-id="56bd1-111">사용자 지정 된 설치 지침에 대 한 azure Active Directory (Azure AD) 관리자를 사용할 수도 있습니다 (Office 365에 로그인 해야 함).</span><span class="sxs-lookup"><span data-stu-id="56bd1-111">You can also use the Azure Active Directory (Azure AD) advisors for customized setup guidance (you must be signed in to Office 365):</span></span>

- [<span data-ttu-id="56bd1-112">Azure AD Connect advisor</span><span class="sxs-lookup"><span data-stu-id="56bd1-112">Azure AD Connect advisor</span></span>](https://aka.ms/aadconnectpwsync)
- [<span data-ttu-id="56bd1-113">AD FS 배포 관리자</span><span class="sxs-lookup"><span data-stu-id="56bd1-113">AD FS deployment advisor</span></span>](https://aka.ms/adfsguidance)
- [<span data-ttu-id="56bd1-114">Azure AD Premium 설치 지침</span><span class="sxs-lookup"><span data-stu-id="56bd1-114">Azure AD Premium setup guidance</span></span>](https://aka.ms/aadpguidance)
   
## <a name="before-you-begin"></a><span data-ttu-id="56bd1-115">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="56bd1-115">Before you begin</span></span>

<span data-ttu-id="56bd1-116">Office 365 및 온-프레미스 환경을 통합 하기 전에 [네트워크 계획 및 성능 조정](network-planning-and-performance.md)에도 참석 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="56bd1-116">Before you integrate Office 365 and an on-premises environment, you also need to attend to [network planning and performance tuning](network-planning-and-performance.md).</span></span> <span data-ttu-id="56bd1-117">사용 가능한 [id 모델](about-office-365-identity.md)을 이해 하 고 싶을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56bd1-117">You will also want to understand the available [identity models](about-office-365-identity.md).</span></span> 

<span data-ttu-id="56bd1-118">Office 365 사용자 및 계정을 관리 하는 데 사용할 수 있는 도구 목록은 [office 365 계정을 관리](manage-office-365-accounts.md) 하는 위치를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="56bd1-118">See [where to manage Office 365 accounts](manage-office-365-accounts.md) for a list of tools you can use to manage Office 365 users and accounts.</span></span> 
  
## <a name="integrate-office-365-with-directory-services"></a><span data-ttu-id="56bd1-119">디렉터리 서비스와 Office 365 통합</span><span class="sxs-lookup"><span data-stu-id="56bd1-119">Integrate Office 365 with directory services</span></span>
<span data-ttu-id="56bd1-120">온-프레미스 디렉터리에 기존 사용자 계정이 있는 경우 Office 365에서 이러한 계정을 모두 다시 만들지 않고 환경 간에 차이점이 나 오류가 발생 하는 위험을 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56bd1-120">If you have existing user accounts in an on-premises directory, you don't want to re-create all of those accounts in Office 365 and risk introducing differences or errors between the environments.</span></span> <span data-ttu-id="56bd1-121">디렉터리 동기화를 사용 하면 온라인 및 온-프레미스 환경 간에 이러한 계정을 미러링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56bd1-121">Directory synchronization helps you mirror those accounts between your online and on-premises environments.</span></span> <span data-ttu-id="56bd1-122">디렉터리 동기화를 사용 하면 사용자가 각 환경에 대 한 새로운 정보를 저장할 필요가 없으며 계정을 두 번 만들거나 업데이트할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="56bd1-122">With directory synchronization, your users don't have to remember new information for each environment, and you don't have to create or update accounts twice.</span></span> <span data-ttu-id="56bd1-123">디렉터리 동기화를 위해 [온-프레미스 디렉터리를 준비](prepare-for-directory-synchronization.md) 해야 하는 경우이를 수동으로 수행 하거나 [idfix 도구](install-and-run-idfix.md) (Idfix 도구는 Active DIRECTORY 도메인 서비스 [AD DS] 에서만 작동)를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56bd1-123">You will need to [prepare your on-premises directory](prepare-for-directory-synchronization.md) for directory synchronization, you can do this manually or use the [IdFix tool](install-and-run-idfix.md) (IdFix tool only works with Active Directory Domain Services [AD DS]).</span></span> 
  
![디렉터리 동기화를 사용 하 여 온-프레미스 및 온라인 사용자 계정 정보 동기화 유지](media/a64af0d0-9be6-46b1-8727-277e683abf5e.png)
  
<span data-ttu-id="56bd1-125">사용자가 온-프레미스 자격 증명을 사용 하 여 Office 365에 로그온 할 수 있게 하려면 SSO를 구성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56bd1-125">If you want users to be able to log on to Office 365 with their on-premises credentials, you can also configure SSO.</span></span> <span data-ttu-id="56bd1-126">SSO를 사용 하는 경우 Office 365은 사용자 인증을 위해 온-프레미스 환경을 신뢰 하도록 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="56bd1-126">With SSO, Office 365 is configured to trust the on-premises environment for user authentication.</span></span>
  
![Single sign-on을 사용 하는 경우 온-프레미스 및 온라인 환경 둘 다에서 동일한 계정을 사용할 수 있습니다.](media/d76235f2-8a53-405e-b8ef-dfa4cfc208b8.png)
  
<span data-ttu-id="56bd1-128">다음 표에 나와 있는 것 처럼 사용자 계정 관리 기법에 따라 사용자에 게 다음과 같은 다양 한 환경이 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="56bd1-128">Different user account management techniques provide different experiences for your users, as shown in the following table.</span></span>
 
### <a name="directory-synchronization-with-or-without-password-hash-synchronization-or-pass-through-authentication"></a><span data-ttu-id="56bd1-129">암호 해시 동기화 또는 통과 인증을 포함 하거나 사용 하지 않고 디렉터리 동기화</span><span class="sxs-lookup"><span data-stu-id="56bd1-129">Directory synchronization with or without password hash synchronization or pass-through authentication</span></span>

<span data-ttu-id="56bd1-130">사용자가 자신의 사용자 계정 (domain\username)을 사용 하 여 온-프레미스 환경에 로그온 합니다.</span><span class="sxs-lookup"><span data-stu-id="56bd1-130">A user logs on to their on-premises environment with their user account (domain\username).</span></span> <span data-ttu-id="56bd1-131">Office 365로 이동 하면 회사 또는 학교 계정 (user@domain.com)을 사용 하 여 다시 로그온 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="56bd1-131">When they go to Office 365, they must log on again with their work or school account (user@domain.com).</span></span> <span data-ttu-id="56bd1-132">사용자 이름은 두 환경에서 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="56bd1-132">The user name is the same in both environments.</span></span> <span data-ttu-id="56bd1-133">암호 해시 동기화 또는 통과 인증을 추가 하는 경우 사용자는 두 환경 모두에 대해 동일한 암호를 사용 하지만 Office 365에 로그온 할 때 이러한 자격 증명을 다시 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="56bd1-133">When you add password hash sync or pass-through authentication, the user has the same password for both environments, but will have to provide those credentials again when logging on to Office 365.</span></span> <span data-ttu-id="56bd1-134">암호 해시 동기화를 사용한 디렉터리 동기화는 가장 일반적으로 사용 되는 디렉터리 동기화 시나리오입니다.</span><span class="sxs-lookup"><span data-stu-id="56bd1-134">Directory synchronization with password hash sync is the most commonly used directory sync scenario.</span></span>

<span data-ttu-id="56bd1-135">디렉터리 동기화를 설정 하려면 Azure Active Directory Connect를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="56bd1-135">To set up directory synchronization, use Azure Active Directory Connect.</span></span> <span data-ttu-id="56bd1-136">자세한 내용은 [Office 365에 대 한 디렉터리 동기화 설정](set-up-directory-synchronization.md)및 [express 설정을 사용 하 여 Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=698537)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="56bd1-136">For instructions, read [Set up directory synchronization for Office 365](set-up-directory-synchronization.md), and [Azure AD Connect with express settings](https://go.microsoft.com/fwlink/p/?LinkId=698537).</span></span>

<span data-ttu-id="56bd1-137">[Office 365에 대 한 디렉터리 동기화 준비](prepare-for-directory-synchronization.md) 및 [Azure Active directory에 온-프레미스 식별을 통합](https://go.microsoft.com/fwlink/?LinkId=518101)하는 방법에 대해 자세히 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="56bd1-137">Learn more about [preparing for directory synchronization to Office 365](prepare-for-directory-synchronization.md) and [integrating your on-premises identifies with Azure Active Directory](https://go.microsoft.com/fwlink/?LinkId=518101).</span></span>

### <a name="directory-synchronization-with-sso"></a><span data-ttu-id="56bd1-138">SSO를 사용한 디렉터리 동기화</span><span class="sxs-lookup"><span data-stu-id="56bd1-138">Directory synchronization with SSO</span></span>

<span data-ttu-id="56bd1-139">사용자가 자신의 사용자 계정을 사용 하 여 온-프레미스 환경에 로그온 합니다.</span><span class="sxs-lookup"><span data-stu-id="56bd1-139">A user logs on to their on-premises environment with their user account.</span></span> <span data-ttu-id="56bd1-140">Office 365로 이동 하면 자동으로 로그온 되거나 온-프레미스 환경 (domain\username)에 사용 하는 것과 동일한 자격 증명을 사용 하 여 로그온 됩니다.</span><span class="sxs-lookup"><span data-stu-id="56bd1-140">When they go to Office 365, they are either logged on automatically, or they log on using the same credentials they use for their on-premises environment (domain\username).</span></span>

<span data-ttu-id="56bd1-141">SSO를 설정 하려면 Azure AD Connect도 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="56bd1-141">To set up SSO you also use Azure AD Connect.</span></span> <span data-ttu-id="56bd1-142">자세한 내용은 [AZURE AD Connect의 사용자 지정 설치](https://go.microsoft.com/fwlink/p/?LinkID=698430)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="56bd1-142">For instructions, read [Custom installation of Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkID=698430).</span></span>

<span data-ttu-id="56bd1-143">[Azure Active Directory에서 응용 프로그램에 대 한 single sign-on](https://go.microsoft.com/fwlink/p/?LinkId=698604)에 대해 자세히 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="56bd1-143">Learn more about [single sign-on to applications in Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=698604).</span></span>

## <a name="azure-ad-connect"></a><span data-ttu-id="56bd1-144">Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="56bd1-144">Azure AD Connect</span></span>

<span data-ttu-id="56bd1-145">Azure AD Connect는 DirSync 및 Azure AD Sync와 같은 이전 버전의 id 통합 도구를 대체 합니다. 자세한 내용은 [Azure Active Directory를 사용한 하이브리드 id 란?](https://go.microsoft.com/fwlink/p/?LinkId=527969)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="56bd1-145">Azure AD Connect replaces older versions of identity integration tools such as DirSync and Azure AD Sync. For more information, see [What is hybrid identity with Azure Active Directory?](https://go.microsoft.com/fwlink/p/?LinkId=527969).</span></span> <span data-ttu-id="56bd1-146">Azure Active Directory 동기화에서 Azure AD Connect로의 업데이트를 하려면 [업그레이드 지침](https://go.microsoft.com/fwlink/p/?LinkId=733240)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="56bd1-146">If you want to update from Azure Active Directory Sync to Azure AD Connect, see [the upgrade instructions](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span></span> 

<span data-ttu-id="56bd1-147">또한 [Microsoft Azure에서 Office 365 디렉터리 동기화 배포를](https://go.microsoft.com/fwlink/?LinkId=517887)참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="56bd1-147">Also see [Deploy Office 365 Directory Synchronization in Microsoft Azure](https://go.microsoft.com/fwlink/?LinkId=517887).</span></span>

## <a name="see-also"></a><span data-ttu-id="56bd1-148">참고 항목</span><span class="sxs-lookup"><span data-stu-id="56bd1-148">See also</span></span>

[<span data-ttu-id="56bd1-149">Microsoft 365 Enterprise 개요</span><span class="sxs-lookup"><span data-stu-id="56bd1-149">Microsoft 365 Enterprise overview</span></span>](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
