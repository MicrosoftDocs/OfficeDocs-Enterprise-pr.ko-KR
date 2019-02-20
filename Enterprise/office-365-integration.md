---
title: '도메인을 사용하여 온-프레미스 전자 메일과 통합(예: 디렉터리 서비스 사용)'
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
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
ms.openlocfilehash: 112f543a9c647ea850d5e43bc14483308da0b2c7
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085337"
---
# <a name="office-365-integration-with-on-premises-environments"></a><span data-ttu-id="6b62d-103">도메인을 사용하여 온-프레미스 전자 메일과 통합(예: 디렉터리 서비스 사용)</span><span class="sxs-lookup"><span data-stu-id="6b62d-103">Office 365 integration with on-premises environments</span></span>

<span data-ttu-id="6b62d-104">Office 365을 기존 디렉터리 서비스와 통합 하 고 Exchange server의 온-프레미스 설치, 비즈니스용 Skype 서버 2015 또는 SharePoint Server 2013와 통합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b62d-104">You can integrate Office 365 with your existing directory services and with an on-premises installation of Exchange Server, Skype for Business Server 2015, or SharePoint Server 2013.</span></span>
  
 - <span data-ttu-id="6b62d-p101">디렉터리 서비스와 통합 하는 경우 두 환경의 사용자 계정을 동기화 하 고 관리할 수 있습니다. 또한 사용자가 온-프레미스 자격 증명을 사용 하 여 두 환경에 로그온 할 수 있도록 암호 해시 동기화 또는 sso (single sign-on)를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b62d-p101">When you integrate with directory services, you can synchronize and manage user accounts for both environments. You can also add password hash synchronization or single sign-on (SSO) so users can log on to both environments with their on-premises credentials.</span></span>
 - <span data-ttu-id="6b62d-p102">온-프레미스 서버 제품과 통합 하는 경우 하이브리드 환경을 만듭니다. 하이브리드 환경은 사용자 또는 정보를 Office 365로 마이그레이션하는 데 도움이 되거나, 일부 사용자 또는 일부 정보를 온-프레미스와 클라우드에서 계속 사용할 수 있습니다. 하이브리드 환경에 대 한 자세한 내용은 [Office 365 하이브리드 클라우드 솔루션 개요](https://support.office.com/article/59616fab-acdb-40e9-b414-cf0c965c80b7)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6b62d-p102">When you integrate with on-premises server products, you create a hybrid environment. A hybrid environment can help as you migrate users or information to Office 365, or you can continue to have some users or some information on-premises and some in the cloud. For more information about hybrid environments, see [Office 365 hybrid cloud solutions overview](https://support.office.com/article/59616fab-acdb-40e9-b414-cf0c965c80b7).</span></span>

<span data-ttu-id="6b62d-110">또한 사용자 지정 된 설치 지침에 대해 Azure AD 관리자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b62d-110">You can also use the Azure AD advisors for customized setup guidance:</span></span>
- [<span data-ttu-id="6b62d-111">Azure AD Connect advisor</span><span class="sxs-lookup"><span data-stu-id="6b62d-111">Azure AD Connect advisor</span></span>](https://aka.ms/aadconnectpwsync)
- [<span data-ttu-id="6b62d-112">AD FS 배포 관리자</span><span class="sxs-lookup"><span data-stu-id="6b62d-112">AD FS deployment advisor</span></span>](https://aka.ms/adfsguidance)
- [<span data-ttu-id="6b62d-113">Azure RMS 배포 마법사</span><span class="sxs-lookup"><span data-stu-id="6b62d-113">Azure RMS Deployment Wizard</span></span>](https://aka.ms/azuremsguidance)
- [<span data-ttu-id="6b62d-114">Azure AD Premium 설치 지침</span><span class="sxs-lookup"><span data-stu-id="6b62d-114">Azure AD Premium setup guidance</span></span>](https://aka.ms/aadpguidance)
   
## <a name="before-you-begin"></a><span data-ttu-id="6b62d-115">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="6b62d-115">Before you begin</span></span>
<span data-ttu-id="6b62d-p103">office 365 및 온-프레미스 환경을 통합 하기 전에 [office 365의 네트워크 계획 및 성능 조정](network-planning-and-performance.md)에도 참석 해야 합니다. 또한 Office 365에서 사용 가능한 [id 모델](about-office-365-identity.md) 을 이해 하 고 싶을 것입니다.</span><span class="sxs-lookup"><span data-stu-id="6b62d-p103">Before you integrate Office 365 and an on-premises environment, you also need to attend to [network planning and performance tuning for Office 365](network-planning-and-performance.md). You will also want to understand the available [identity models](about-office-365-identity.md) in Office 365.</span></span> 

<span data-ttu-id="6b62d-118">office 365 사용자 및 계정을 관리 하는 데 사용할 수 있는 도구 목록은 [office 365 사용자 계정을 관리](manage-office-365-accounts.md) 하는 위치를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6b62d-118">See [where to manage Office 365 user accounts](manage-office-365-accounts.md) for a list of tools you can use to manage Office 365 users and accounts.</span></span> 
  
## <a name="integrate-office-365-with-directory-services"></a><span data-ttu-id="6b62d-119">디렉터리 서비스와 Office 365 통합</span><span class="sxs-lookup"><span data-stu-id="6b62d-119">Integrate Office 365 with directory services</span></span>
<span data-ttu-id="6b62d-p104">온-프레미스 디렉터리에 기존 사용자 계정이 있는 경우 Office 365에서 이러한 계정을 모두 다시 만들지 않고 환경 간에 차이점이 나 오류가 발생 하는 위험을 방지할 수 있습니다. 디렉터리 동기화를 사용 하면 온라인 및 온-프레미스 환경 간에 이러한 계정을 미러링할 수 있습니다. 디렉터리 동기화를 사용 하면 사용자가 각 환경에 대 한 새로운 정보를 저장할 필요가 없으며 계정을 두 번 만들거나 업데이트할 필요가 없습니다. 디렉터리 동기화를 위해 [온-프레미스 디렉터리를 준비](prepare-for-directory-synchronization.md) 해야 하며,이를 수동으로 수행 하거나 [idfix 도구](install-and-run-idfix.md) 를 사용할 수 있습니다 (idfix 도구는 Active directory 에서만 작동).</span><span class="sxs-lookup"><span data-stu-id="6b62d-p104">If you have existing user accounts in an on-premises directory, you don't want to re-create all of those accounts in Office 365 and risk introducing differences or errors between the environments. Directory synchronization helps you mirror those accounts between your online and on-premises environments. With directory synchronization, your users don't have to remember new information for each environment, and you don't have to create or update accounts twice. You will need to [prepare your on-premises directory](prepare-for-directory-synchronization.md) for directory synchronization, you can do this manually or use the [IdFix tool](install-and-run-idfix.md) (IdFix tool only works with Active Directory).</span></span> 
  
![디렉터리 동기화를 사용 하 여 온-프레미스 및 온라인 사용자 계정 정보 동기화 유지](media/a64af0d0-9be6-46b1-8727-277e683abf5e.png)
  
<span data-ttu-id="6b62d-p105">사용자가 온-프레미스 자격 증명을 사용 하 여 Office 365에 로그온 할 수 있게 하려면 SSO를 구성할 수도 있습니다. SSO를 사용 하는 경우 Office 365은 사용자 인증을 위해 온-프레미스 환경을 신뢰 하도록 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b62d-p105">If you want users to be able to log on to Office 365 with their on-premises credentials, you can also configure SSO. With SSO, Office 365 is configured to trust the on-premises environment for user authentication.</span></span>
  
![single sign-on을 사용 하는 경우 온-프레미스 및 온라인 환경 둘 다에서 동일한 계정을 사용할 수 있습니다.](media/d76235f2-8a53-405e-b8ef-dfa4cfc208b8.png)
  
<span data-ttu-id="6b62d-128">다음 표에 나와 있는 것 처럼 사용자 계정 관리 기법에 따라 사용자에 게 다음과 같은 다양 한 환경이 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b62d-128">Different user account management techniques provide different experiences for your users, as shown in the following table.</span></span>
 
### <a name="directory-synchronization-with-or-without-password-hash-synchronization-or-pass-through-authentication"></a><span data-ttu-id="6b62d-129">**암호 해시 동기화 또는 통과 인증을 포함 하거나 사용 하지 않고 디렉터리 동기화**</span><span class="sxs-lookup"><span data-stu-id="6b62d-129">**Directory synchronization with or without password hash synchronization or pass-through authentication**</span></span>
<span data-ttu-id="6b62d-p106">사용자가 자신의 사용자 계정 (domain\username)을 사용 하 여 온-프레미스 환경에 로그온 합니다. Office 365로 이동 하면 회사 또는 학교 계정 (user@domain.com)을 사용 하 여 다시 로그온 해야 합니다. 사용자 이름은 두 환경에서 동일 합니다. 암호 해시 동기화 또는 통과 인증을 추가 하는 경우 사용자는 두 환경 모두에 대해 동일한 암호를 사용 하지만 Office 365에 로그온 할 때 이러한 자격 증명을 다시 제공 해야 합니다. 암호 해시 동기화를 사용한 디렉터리 동기화는 가장 일반적으로 사용 되는 디렉터리 동기화 시나리오입니다.</span><span class="sxs-lookup"><span data-stu-id="6b62d-p106">A user logs on to their on-premises environment with their user account (domain\username). When they go to Office 365, they must log on again with their work or school account (user@domain.com). The user name is the same in both environments. When you add password hash sync or pass-through authentication, the user has the same password for both environments, but will have to provide those credentials again when logging on to Office 365. Directory synchronization with password hash sync is the most commonly used directory sync scenario.</span></span>

<span data-ttu-id="6b62d-p107">디렉터리 동기화를 설정 하려면 Azure Active directory Connect를 사용 합니다. 자세한 내용은 [Office 365에 대 한 디렉터리 동기화 설정](set-up-directory-synchronization.md)및 [빠른 설정을 사용 하 여 Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=698537)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6b62d-p107">To set up directory synchronization, use Azure Active Directory Connect. For instructions, read [Set up directory synchronization for Office 365](set-up-directory-synchronization.md), and [Use Azure AD Connect with express settings](https://go.microsoft.com/fwlink/p/?LinkId=698537).</span></span>

<span data-ttu-id="6b62d-137">[디렉터리 동기화를 통해 사용자를 Office 365에 프로 비전 하](prepare-for-directory-synchronization.md) 고 [온-프레미스 식별을 Azure Active directory에 통합](https://go.microsoft.com/fwlink/?LinkId=518101)하기 위한 준비에 대해 자세히 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="6b62d-137">Learn more about [preparing to provision users through directory synchronization to Office 365](prepare-for-directory-synchronization.md) and [integrating your on-premises identifies with Azure Active Directory](https://go.microsoft.com/fwlink/?LinkId=518101).</span></span>

### <a name="directory-synchronization-with-sso"></a><span data-ttu-id="6b62d-138">**SSO를 사용한 디렉터리 동기화**</span><span class="sxs-lookup"><span data-stu-id="6b62d-138">**Directory synchronization with SSO**</span></span>
<span data-ttu-id="6b62d-p108">사용자가 자신의 사용자 계정을 사용 하 여 온-프레미스 환경에 로그온 합니다. Office 365로 이동 하면 자동으로 로그온 되거나 온-프레미스 환경 (domain\username)에 사용 하는 것과 동일한 자격 증명을 사용 하 여 로그온 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b62d-p108">A user logs on to their on-premises environment with their user account. When they go to Office 365, they are either logged on automatically, or they log on using the same credentials they use for their on-premises environment (domain\username).</span></span>

<span data-ttu-id="6b62d-p109">SSO를 설정 하려면 Azure AD Connect도 사용 합니다. 자세한 내용은 [사용자 지정 설정을 사용 하 여 Azure AD Connect 사용](https://go.microsoft.com/fwlink/p/?LinkID=698430)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="6b62d-p109">To set up SSO you also use Azure AD Connect. For instructions, read [Use Azure AD Connect with custom settings](https://go.microsoft.com/fwlink/p/?LinkID=698430).</span></span>

<span data-ttu-id="6b62d-143">[Azure Active Directory를 사용 하 여 응용 프로그램 액세스 및 single sign-on](https://go.microsoft.com/fwlink/p/?LinkId=698604)에 대해 자세히 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="6b62d-143">Learn more about [application access and single sign-on with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=698604).</span></span>

## <a name="azure-ad-connect"></a><span data-ttu-id="6b62d-144">Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="6b62d-144">Azure AD Connect</span></span>
<span data-ttu-id="6b62d-p110">azure ad Connect는 DirSync 및 Azure ad Sync와 같은 이전 버전의 id 통합 도구를 대체 합니다. 자세한 내용은 [Azure Active Directory를 사용 하 여 온-프레미스 id 통합](https://go.microsoft.com/fwlink/p/?LinkId=527969)을 참조 하세요. azure Active Directory 동기화에서 azure AD Connect로의 업데이트를 하려면 [업그레이드 지침](https://go.microsoft.com/fwlink/p/?LinkId=733240)을 참조 하세요. [Microsoft Azure에서 Office 365 디렉터리 동기화 (DirSync)](https://go.microsoft.com/fwlink/?LinkId=517887)를 위해 빌드된 솔루션 아키텍처를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6b62d-p110">Azure AD Connect replaces older versions of identity integration tools such as DirSync and Azure AD Sync. For more information, see [Integrating your on-premises identities with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=527969). If you want to update from Azure Active Directory Sync to Azure AD Connect, see [the upgrade instructions](https://go.microsoft.com/fwlink/p/?LinkId=733240). See a solution architecture built for [Office 365 Directory Synchronization (DirSync) in Microsoft Azure](https://go.microsoft.com/fwlink/?LinkId=517887).</span></span>