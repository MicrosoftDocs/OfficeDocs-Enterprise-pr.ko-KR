---
title: 온-프레미스 환경와 office 365의 통합
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- LYN150
- SPS150
- MOE150
- MED150
ms.assetid: 263faf8d-aa21-428b-aed3-2021837a4b65
description: Office 365에서 기존 디렉터리 서비스와 통합 하는 방법에 알아봅니다.
ms.openlocfilehash: b660dda74303a3bf0fa92bc8e3146cd2c9add662
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542070"
---
# <a name="office-365-integration-with-on-premises-environments"></a><span data-ttu-id="4f473-103">온-프레미스 환경와 office 365의 통합</span><span class="sxs-lookup"><span data-stu-id="4f473-103">Office 365 integration with on-premises environments</span></span>

<span data-ttu-id="4f473-104">비즈니스 서버 2015 또는 SharePoint Server 2013에 대 한 Office 365의 Exchange Server, Skype 온-프레미스 설치와 함께 기존 디렉터리 서비스와 통합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f473-104">You can integrate Office 365 with your existing directory services and with an on-premises installation of Exchange Server, Skype for Business Server 2015, or SharePoint Server 2013.</span></span>
  
 - <span data-ttu-id="4f473-p101">디렉터리 서비스와 통합 하는 경우 동기화 할 수 있으며 두 환경에 대 한 사용자 계정을 관리할 수 있습니다. 추가할 수도 있습니다 암호 해시 동기화 또는 single sign on (SSO) 사용자가 로그온 수 있도록 두 환경에서 온-프레미스 자격 증명 사용에 로그온 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f473-p101">When you integrate with directory services, you can synchronize and manage user accounts for both environments. You can also add password hash synchronization or single sign-on (SSO) so users can log on to both environments with their on-premises credentials.</span></span>
 - <span data-ttu-id="4f473-p102">온-프레미스 서버 제품을 통합 하는 경우에 하이브리드 환경을 만듭니다. 하이브리드 환경에는 Office 365에 사용자 또는 정보를 마이그레이션 또는 일부 사용자 또는 일부 정보 온-프레미스 및 클라우드의 일부를 계속할 수 대로 데 도움이 됩니다. 하이브리드 환경에 대 한 자세한 내용은 [Office 365 하이브리드 클라우드 솔루션 개요](https://support.office.com/article/59616fab-acdb-40e9-b414-cf0c965c80b7)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="4f473-p102">When you integrate with on-premises server products, you create a hybrid environment. A hybrid environment can help as you migrate users or information to Office 365, or you can continue to have some users or some information on-premises and some in the cloud. For more information about hybrid environments, see [Office 365 hybrid cloud solutions overview](https://support.office.com/article/59616fab-acdb-40e9-b414-cf0c965c80b7).</span></span>

<span data-ttu-id="4f473-110">사용자 지정 된 설치 지침에 대 한 Azure AD 문에 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f473-110">You can also use the Azure AD advisors for customized setup guidance:</span></span>
- [<span data-ttu-id="4f473-111">Azure AD 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="4f473-111">Azure AD Connect advisor</span></span>](https://aka.ms/aadconnectpwsync)
- [<span data-ttu-id="4f473-112">AD FS 배포 관리자</span><span class="sxs-lookup"><span data-stu-id="4f473-112">AD FS deployment advisor</span></span>](https://aka.ms/adfsguidance)
- [<span data-ttu-id="4f473-113">Azure RMS 배포 마법사</span><span class="sxs-lookup"><span data-stu-id="4f473-113">Azure RMS Deployment Wizard</span></span>](https://aka.ms/azuremsguidance)
- [<span data-ttu-id="4f473-114">Azure AD 프리미엄 설치 지침</span><span class="sxs-lookup"><span data-stu-id="4f473-114">Azure AD Premium setup guidance</span></span>](https://aka.ms/aadpguidance)
   
## <a name="before-you-begin"></a><span data-ttu-id="4f473-115">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="4f473-115">Before you begin</span></span>
<span data-ttu-id="4f473-p103">Office 365 및 온-프레미스 환경 통합 하기 전에 네트워크를 계획 하 [고 Office 365에 대 한 성능 조정](network-planning-and-performance.md)참석 해야할 수도 있습니다. Office 365에서 사용 가능한 [id 모델](about-office-365-identity.md) 을 이해 하려면 원하는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f473-p103">Before you integrate Office 365 and an on-premises environment, you also need to attend to [network planning and performance tuning for Office 365](network-planning-and-performance.md). You will also want to understand the available [identity models](about-office-365-identity.md) in Office 365.</span></span> 

<span data-ttu-id="4f473-118">[계정을 Office 365 사용자를 관리 하려면 여기서](manage-office-365-accounts.md) 목록은 Office 365의 사용자 및 계정 관리 하기 위해 사용할 수 있는 도구를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="4f473-118">See [where to manage Office 365 user accounts](manage-office-365-accounts.md) for a list of tools you can use to manage Office 365 users and accounts.</span></span> 
  
## <a name="integrate-office-365-with-directory-services"></a><span data-ttu-id="4f473-119">Office 365의 디렉터리 서비스와 통합</span><span class="sxs-lookup"><span data-stu-id="4f473-119">Integrate Office 365 with directory services</span></span>
<span data-ttu-id="4f473-p104">온-프레미스 디렉터리에 있는 기존 사용자 계정을 Office 365와 환경 간의 오류나 차이점을 소개 하는 위험에서 이러한 계정을 모두를 다시 만듭니다 하려는 하지 않습니다. 디렉터리 동기화를 사용 하면 온라인 사용자 간의 이러한 계정이 미러와 온-프레미스 환경입니다. 디렉터리 동기화를 통해 사용자가 각 환경에 대 한 새로운 정보를 기억할 필요가 없습니다 하 고 만들거나 두번 계정을 업데이트할 필요가 없습니다. 디렉터리 동기화를 위한 [온-프레미스 디렉터리 준비](prepare-for-directory-synchronization.md) 를 해야 합니다, 그리고이 작업을 수동으로 수행 하거나 [IdFix 도구](install-and-run-idfix.md) (IdFix 도구에만 작동 하며 Active Directory)를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f473-p104">If you have existing user accounts in an on-premises directory, you don't want to re-create all of those accounts in Office 365 and risk introducing differences or errors between the environments. Directory synchronization helps you mirror those accounts between your online and on-premises environments. With directory synchronization, your users don't have to remember new information for each environment, and you don't have to create or update accounts twice. You will need to [prepare your on-premises directory](prepare-for-directory-synchronization.md) for directory synchronization, you can do this manually or use the [IdFix tool](install-and-run-idfix.md) (IdFix tool only works with Active Directory).</span></span> 
  
![디렉터리 동기화를 사용 하 여 온-프레미스 및 온라인 사용자 계정 정보 동기화 유지](media/a64af0d0-9be6-46b1-8727-277e683abf5e.png)
  
<span data-ttu-id="4f473-p105">사용자가 온-프레미스 자격 증명을 사용 하 여 Office 365에 로그온 할 수 있도록, 하려는 경우에 SSO를 구성할 수 있습니다. SSO를와 Office 365 사용자 인증에 대 한 온-프레미스 환경을 신뢰 하도록 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f473-p105">If you want users to be able to log on to Office 365 with their on-premises credentials, you can also configure SSO. With SSO, Office 365 is configured to trust the on-premises environment for user authentication.</span></span>
  
![Single sign-on과 동일한 계정을 온-프레미스 및 온라인 환경 모두에서 사용할 수 있는](media/d76235f2-8a53-405e-b8ef-dfa4cfc208b8.png)
  
<span data-ttu-id="4f473-128">다른 사용자 계정 관리 기술 다음 표와 같이 사용자에 게 다른 경험을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f473-128">Different user account management techniques provide different experiences for your users, as shown in the following table.</span></span>
 
### <a name="directory-synchronization-with-or-without-password-hash-synchronization-or-pass-through-authentication"></a><span data-ttu-id="4f473-129">**디렉터리 동기화와 관계 없이 암호 해시 동기화 또는 통과 인증**</span><span class="sxs-lookup"><span data-stu-id="4f473-129">**Directory synchronization with or without password hash synchronization or pass-through authentication**</span></span>
<span data-ttu-id="4f473-p106">사용자가 자신의 사용자 계정 (도메인 \ 사용자 이름)가 온-프레미스 환경에 로그온 합니다. Office 365로 전달 될 때 이러한 해야 다시 계정으로 로그온 자신의 작업이 나 교육용 (user@domain.com). 사용자 이름은 환경 모두에서 동일 합니다. 암호 해시 동기화 또는 통과 인증을 추가 하면 사용자는 두 환경에 대 한 동일한 암호를 다르지만 Office 365에 로그온 할 때 이러한 자격 증명을 다시 제공 해야 합니다. 암호 해시 동기화를 사용 하 여 디렉터리 동기화에 가장 일반적으로 사용 되는 디렉터리 동기화 시나리오입니다.</span><span class="sxs-lookup"><span data-stu-id="4f473-p106">A user logs on to their on-premises environment with their user account (domain\username). When they go to Office 365, they must log on again with their work or school account (user@domain.com). The user name is the same in both environments. When you add password hash sync or pass-through authentication, the user has the same password for both environments, but will have to provide those credentials again when logging on to Office 365. Directory synchronization with password hash sync is the most commonly used directory sync scenario.</span></span>

<span data-ttu-id="4f473-p107">디렉터리 동기화를 설정 하려면 Azure Active Directory 연결을 사용 합니다. 자세한 내용은 [Office 365에 대 한 디렉터리 동기화를 설정](set-up-directory-synchronization.md)하 고 [express 설정 사용 하 여 사용 하 여 Azure AD 연결](https://go.microsoft.com/fwlink/p/?LinkId=698537)을 읽어보십시오.</span><span class="sxs-lookup"><span data-stu-id="4f473-p107">To set up directory synchronization, use Azure Active Directory Connect. For instructions, read [Set up directory synchronization for Office 365](set-up-directory-synchronization.md), and [Use Azure AD Connect with express settings](https://go.microsoft.com/fwlink/p/?LinkId=698537).</span></span>

<span data-ttu-id="4f473-137">[Office 365에 대 한 디렉터리 동기화를 통해 사용자를 프로 비전을 준비 하](prepare-for-directory-synchronization.md) 고 [통합 (영문) Azure Active Directory와 온-프레미스를 식별](https://go.microsoft.com/fwlink/?LinkId=518101)하는 방법에 대 한 자세한 내용은.</span><span class="sxs-lookup"><span data-stu-id="4f473-137">Learn more about [preparing to provision users through directory synchronization to Office 365](prepare-for-directory-synchronization.md) and [integrating your on-premises identifies with Azure Active Directory](https://go.microsoft.com/fwlink/?LinkId=518101).</span></span>

### <a name="directory-synchronization-with-sso"></a><span data-ttu-id="4f473-138">**SSO 사용 하 여 디렉터리 동기화**</span><span class="sxs-lookup"><span data-stu-id="4f473-138">**Directory synchronization with SSO**</span></span>
<span data-ttu-id="4f473-p108">사용자가 자신의 사용자 계정 사용 하 여 온-프레미스 환경에 로그온 합니다. Office 365로 전달 될 때 하거나 로그온 되어 자동으로 또는 온-프레미스 환경 (도메인 \ 사용자 이름)을 사용 하는지에 동일한 자격 증명을 사용 하 여 로그온 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f473-p108">A user logs on to their on-premises environment with their user account. When they go to Office 365, they are either logged on automatically, or they log on using the same credentials they use for their on-premises environment (domain\username).</span></span>

<span data-ttu-id="4f473-p109">SSO를 설정 하려면 Azure AD 연결 사용 합니다. 자세한 내용은 [사용자 지정 설정 사용 하 여 사용 하 여 Azure AD 연결](https://go.microsoft.com/fwlink/p/?LinkID=698430)을 읽어보십시오.</span><span class="sxs-lookup"><span data-stu-id="4f473-p109">To set up SSO you also use Azure AD Connect. For instructions, read [Use Azure AD Connect with custom settings](https://go.microsoft.com/fwlink/p/?LinkID=698430).</span></span>

<span data-ttu-id="4f473-143">[응용 프로그램 액세스 및 single sign-on 및 Azure Active Directory를 사용](https://go.microsoft.com/fwlink/p/?LinkId=698604)하는 방법에 대 한 자세한 내용은 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f473-143">Learn more about [application access and single sign-on with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=698604).</span></span>

## <a name="azure-ad-connect"></a><span data-ttu-id="4f473-144">Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="4f473-144">Azure AD Connect</span></span>
<span data-ttu-id="4f473-p110">Azure AD 연결 이전 버전의 디렉터리 동기화 및 Azure AD 동기화와 같은 identity 통합 도구를 대체합니다. 자세한 내용은 [Azure Active Directory를 사용 하 여 온-프레미스 id가 통합 (영문)을](https://go.microsoft.com/fwlink/p/?LinkId=527969)참조 하십시오. Azure Active Directory 동기화에서 Azure AD 연결을 업데이트 하려는 경우 [업그레이드 지침](https://go.microsoft.com/fwlink/p/?LinkId=733240)을 참조 하십시오. [Microsoft Azure에서 Office 365 디렉터리 동기화 (DirSync)](https://go.microsoft.com/fwlink/?LinkId=517887)용으로 작성 된 솔루션 아키텍처를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="4f473-p110">Azure AD Connect replaces older versions of identity integration tools such as DirSync and Azure AD Sync. For more information, see [Integrating your on-premises identities with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=527969). If you want to update from Azure Active Directory Sync to Azure AD Connect, see [the upgrade instructions](https://go.microsoft.com/fwlink/p/?LinkId=733240). See a solution architecture built for [Office 365 Directory Synchronization (DirSync) in Microsoft Azure](https://go.microsoft.com/fwlink/?LinkId=517887).</span></span>