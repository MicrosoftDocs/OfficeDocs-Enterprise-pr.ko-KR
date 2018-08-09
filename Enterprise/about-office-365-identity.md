---
title: Office 365 id 및 Azure Active Directory 이해
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 5/1/2018
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MOE150
- BCS160
ms.assetid: 06a189e7-5ec6-4af2-94bf-a22ea225a7a9
description: Office 365에서 사용자 id를 관리 하는 방법에 대해 알아봅니다.
ms.openlocfilehash: cdd0ab2306e9a966f308006761a83cda8989b898
ms.sourcegitcommit: f42ca73d23beb5770981e7a93995ef3be5e341bb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/08/2018
ms.locfileid: "22213129"
---
# <a name="understanding-office-365-identity-and-azure-active-directory"></a><span data-ttu-id="5bd5f-103">Office 365 id 및 Azure Active Directory 이해</span><span class="sxs-lookup"><span data-stu-id="5bd5f-103">Understanding Office 365 identity and Azure Active Directory</span></span>

<span data-ttu-id="5bd5f-p101">Office 365 클라우드 기반 사용자 id 및 인증 서비스 Azure Active Directory (Azure AD)를 사용 하 여 사용자를 관리 합니다. 온-프레미스 조직과 Office 365 간의 id 관리 구성 된 경우 선택은 클라우드 인프라의 기초 중 하나가 있는 초기 결정 합니다. 나중에이 구성을 변경 하는 것은 어려울 수 있습니다, 때문에 조직의 필요에 따라 가장 적합 한 기능을 결정 하는 옵션을 신중 하 게 고려 합니다. Office 365를 설정 하 고 사용자 계정; 관리의 두 기본 인증 모델 중에서 선택할 수 있습니다. 클라우드 인증 및 연결 된 인증 합니다.</span><span class="sxs-lookup"><span data-stu-id="5bd5f-p101">Office 365 uses the cloud-based user identity and authentication service Azure Active Directory (Azure AD) to manage users. Choosing if identity management is configured between your on-premises organization and Office 365 is an early decision that is one of the foundations of your cloud infrastructure. Because changing this configuration later can be difficult, carefully consider the options to determine what works best for the needs of your organization. You can choose from two main authentication models in Office 365 to set up and manage user accounts; cloud authentication and federated authentication.</span></span>
  
<span data-ttu-id="5bd5f-p102">해당 되어 실행 되 고 신중 하 게 준비를 사용 하 여 어떤 인증 및 id 모델을 고려 하는 것이 중요 합니다. 시간, 기존 복잡성 및 비용을 구현 하 고 각각의 인증 및 id 옵션을 유지 관리를 고려해 야 합니다. 이러한 요소는 조직 마다;에 대 한 서로 다른 및 배포에 사용 하려는 인증 및 id 모델을 선택할 수 있도록 지원 id 옵션에 대 한 주요 개념을 이해 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5bd5f-p102">It's important to carefully consider which authentication and identity model to use to get up and running. Think about the time, existing complexity, and cost to implement and maintain each of the authentication and identity options. These factors are different for every organization; and you should understand the key concepts for the identity options to help you choose the authentication and identity model you want to use for your deployment.</span></span>
  
## <a name="cloud-authentication"></a><span data-ttu-id="5bd5f-111">클라우드 인증</span><span class="sxs-lookup"><span data-stu-id="5bd5f-111">Cloud authentication</span></span>

<span data-ttu-id="5bd5f-112">여부에 따라 Office 365 사용자에 대 한 인증 및 id 서비스를 관리 하는 여러 옵션 있거나 기존 Active Directory 환경 온-프레미스를 설치 하지 않은 경우 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5bd5f-112">Depending if you have or don't have an existing Active Directory environment on-premises, you have several options to manage authentication and identity services for your users with Office 365.</span></span>
  
### <a name="cloud-only"></a><span data-ttu-id="5bd5f-113">클라우드 전용</span><span class="sxs-lookup"><span data-stu-id="5bd5f-113">Cloud-only</span></span>

<span data-ttu-id="5bd5f-p103">클라우드 전용 모델을 사용 하면 사용자 계정을 Office 365에만 관리할 수 있습니다. 온-프레미스 서버 없음 요소가 필요 합니다. 모든 클라우드에서 의해 처리 될 Azure AD 합니다. 컨트롤을 만들고 Office 365 관리 센터에서 사용자 관리 또는 Windows PowerShell을 사용 하 여 [PowerShell cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=698471) 및 id 및 인증에서에서 처리 되는 완전히 클라우드 Azure AD 하 여 합니다. 클라우드 전용 모델은 일반적으로 좋은 선택 경우:</span><span class="sxs-lookup"><span data-stu-id="5bd5f-p103">With the cloud-only model, you manage your user accounts in Office 365 only. No on-premises servers are required; it's all handled in the cloud by Azure AD. You create and manage users in the Office 365 admin center or by using Windows PowerShell [PowerShell cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=698471) and identity and authentication are handled completely in the cloud by Azure AD. The cloud-only model is typically a good choice if:</span></span> 
  
- <span data-ttu-id="5bd5f-118">다른 온-프레미스 사용자 디렉터리에 없는 해야합니다.</span><span class="sxs-lookup"><span data-stu-id="5bd5f-118">You have no other on-premises user directory.</span></span>
    
- <span data-ttu-id="5bd5f-119">매우 복잡 한 온-프레미스 디렉터리 있고와 통합 하는 작업을 방지 하기 위해를 세려면 합니다.</span><span class="sxs-lookup"><span data-stu-id="5bd5f-119">You have a very complex on-premises directory and simply want to avoid the work to integrate with it.</span></span>
    
- <span data-ttu-id="5bd5f-p104">기존 온-프레미스 디렉터리를 되었지만 평가판 또는 Office 365의 파일럿을 실행 하려는 합니다. 나중에 온-프레미스 디렉터리에 연결할 준비가 되 면 온-프레미스 사용자에 게 클라우드 사용자를 일치 시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5bd5f-p104">You have an existing on-premises directory, but you want to run a trial or pilot of Office 365. Later, you can match the cloud users to on-premises users when you are ready to connect to your on-premises directory.</span></span>
    
<span data-ttu-id="5bd5f-122">클라우드 id를 가진 시작 [비즈니스를 위한 Office 365 설정](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="5bd5f-122">To get started with cloud identity, see [Set up Office 365 for business](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa).</span></span>
  
### <a name="password-hash-sync-with-seamless-single-sign-on"></a><span data-ttu-id="5bd5f-123">원활 하 게 single sign-on 암호 해시 동기화</span><span class="sxs-lookup"><span data-stu-id="5bd5f-123">Password hash sync with seamless single sign-on</span></span>

<span data-ttu-id="5bd5f-p105">Azure AD에서 온-프레미스 디렉터리 개체에 대 한 인증을 사용 하는 가장 간단한 방법은 합니다. 암호 해시 동기화 (PHS)를 사용한 Office 365와 온-프레미스 Active Directory 사용자 계정 개체를 동기화 및 사용자가 온-프레미스를 관리 합니다. 사용자 암호 해시를 사용자가 동일한 암호 온-프레미스 및 클라우드에서 Azure AD를 온-프레미스 Active Directory에서 동기화 됩니다. 암호 변경 또는 온-프레미스를 다시 설정 하는 경우 사용자에 게 클라우드 리소스 및 온-프레미스 리소스에 대 한 동일한 암호를 항상 사용할 수 있도록 새 암호 해시 Azure AD에 동기화 됩니다. 암호는 되지 Azure AD 보내거나 일반 텍스트로 Azure AD에 저장 합니다. 일부 프리미엄 기능 Id 보호와 같은 Azure ad 인증 방법을 선택 하는 관계 없이 PHS 필요 합니다. 원활 하 게 single sign-on, 사용자는 자동으로 로그인을 통해 회사 장치에는 및 회사 네트워크에 연결 된 경우 Azure AD 합니다.</span><span class="sxs-lookup"><span data-stu-id="5bd5f-p105">The simplest way to enable authentication for on-premises directory objects in Azure AD. With password hash sync (PHS), you synchronize your on-premises Active Directory user account objects with Office 365 and manage your users on-premises. Hashes of user passwords are synchronized from your on-premises Active Directory to Azure AD so that the users have the same password on-premises and in the cloud. When passwords are changed or reset on-premises, the new password hashes are synchronized to Azure AD so that your users can always use the same password for cloud resources and on-premises resources. The passwords are never sent to Azure AD or stored in Azure AD in clear text. Some premium features of Azure AD, such as Identity Protection, require PHS regardless of which authentication method is selected. With seamless single sign-on, users are automatically signed in to Azure AD when they are on their corporate devices and connected to your corporate network.</span></span>
  
<span data-ttu-id="5bd5f-131">[암호 해시 동기화를 선택](https://docs.microsoft.com/en-us/azure/security/azure-ad-choose-authn) 하 고 [원활 하 게 single sign on](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnect-sso)하는 방법에 대 한 자세한 내용은.</span><span class="sxs-lookup"><span data-stu-id="5bd5f-131">Learn more about [choosing password hash sync](https://docs.microsoft.com/en-us/azure/security/azure-ad-choose-authn) and [seamless single sign-on](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnect-sso).</span></span>
  
### <a name="pass-through-authentication-with-seamless-single-sign-on"></a><span data-ttu-id="5bd5f-132">원활 하 게 single sign-on 통과 인증</span><span class="sxs-lookup"><span data-stu-id="5bd5f-132">Pass-through authentication with seamless single sign-on</span></span>

<span data-ttu-id="5bd5f-p106">하나 이상의 온-프레미스 서버에서 실행 되는 소프트웨어 에이전트를 사용 하 여 온-프레미스 Active Directory를 사용 하 여 직접 사용자의 유효성을 검사 하려면 Azure AD 인증 서비스에 대 한 간단한 암호 유효성 검사를 제공 합니다. 통과 인증 (설명)을 사용 하면 Office 365와 온-프레미스 Active Directory 사용자 계정 개체 동기화 및 사용자가 온-프레미스를 관리 합니다. 사용자가 온-프레미스 및 Office 365 리소스 및 온-프레미스 계정 및 암호를 사용 하는 응용 프로그램에 로그인 하도록 허용 합니다. 이 구성은 Office 365에 암호 해시를 보내지 않고 온-프레미스 Active Directory에 대해 직접 사용자의 암호의 유효성을 검사 합니다. 온-프레미스 사용자 계정을 즉시 적용 하려면 보안 요구 사항이 있는 회사 상태, 암호 정책 및 로그온 시간에이 인증 방법을 사용 합니다. 원활 하 게 single sign-on, 사용자는 자동으로 로그인을 통해 회사 장치에는 및 회사 네트워크에 연결 된 경우 Azure AD 합니다.</span><span class="sxs-lookup"><span data-stu-id="5bd5f-p106">Provides a simple password validation for Azure AD authentication services using a software agent running on one or more on-premises servers to validate the users directly with your on-premises Active Directory. With pass-through authentication (PTA), you synchronize on-premises Active Directory user account objects with Office 365 and manage your users on-premises. Allows your users to sign in to both on-premises and Office 365 resources and applications using their on-premises account and password. This configuration validates users' passwords directly against your on-premises Active Directory without sending password hashes to Office 365. Companies with a security requirement to immediately enforce on-premises user account states, password policies, and logon hours would use this authentication method. With seamless single sign-on, users are automatically signed in to Azure AD when they are on their corporate devices and connected to your corporate network.</span></span>
  
<span data-ttu-id="5bd5f-139">[통과 인증을 선택](https://docs.microsoft.com/en-us/azure/security/azure-ad-choose-authn) 하 고 [원활 하 게 single sign on](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnect-sso)하는 방법에 대 한 자세한 내용은.</span><span class="sxs-lookup"><span data-stu-id="5bd5f-139">Learn more about [choosing pass-through authentication](https://docs.microsoft.com/en-us/azure/security/azure-ad-choose-authn) and [seamless single sign-on](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnect-sso).</span></span>
  
## <a name="federated-authentication-options"></a><span data-ttu-id="5bd5f-140">연결 된 인증 옵션</span><span class="sxs-lookup"><span data-stu-id="5bd5f-140">Federated authentication options</span></span>

<span data-ttu-id="5bd5f-141">기존 Active Directory 환경 온-프레미스가 Office 365에서 사용자에 대 한 인증 및 id 서비스를 관리 하려면 연결 된 인증을 사용 하 여 Office 365 디렉터리와 통합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5bd5f-141">If you have an existing Active Directory environment on-premises, you can integrate Office 365 with your directory by using federated authentication to manage authentication and identity services for your users in Office 365.</span></span>
  
### <a name="federated-identity-with-active-directory-federation-services-ad-fs"></a><span data-ttu-id="5bd5f-142">Active Directory Federation Services (AD FS)와 페더레이션된 id</span><span class="sxs-lookup"><span data-stu-id="5bd5f-142">Federated identity with Active Directory Federation Services (AD FS)</span></span>

<span data-ttu-id="5bd5f-p107">주로 보다 복잡 한 인증 요구 사항이 조직 대기업, 온-프레미스 디렉터리 개체는 Office 365와 동기화 되며 사용자 계정을 관리 되는 온-프레미스 합니다. AD FS, 사용자가 동일한 암호 온-프레미스 및 클라우드에서 Office 365를 사용 하 여 다시 로그인 갖지 않습니다. 이 연결 된 인증 모델 추가 인증 요구 사항, 예: 제 3 자 다단계 인증 또는 스마트 카드 기반 인증을 제공할 수 및는 조직에는 인증 요구 사항이 있는 경우 일반적으로 필요 Azure AD에서 지원 되지 않음.</span><span class="sxs-lookup"><span data-stu-id="5bd5f-p107">Primarily for large enterprise organizations with more complex authentication requirements, on-premises directory objects are synchronized with Office 365 and users accounts are managed on-premises. With AD FS, users have the same password on-premises and in the cloud and they do not have to sign in again to use Office 365. This federated authentication model can provide additional authentication requirements, such as smartcard-based authentication or a third-party multi-factor authentication and is typically required when organizations have an authentication requirement not natively supported by Azure AD.</span></span>
  
<span data-ttu-id="5bd5f-146">[AD FS 사용한 페더레이션된 id를 선택](https://docs.microsoft.com/en-us/azure/security/azure-ad-choose-authn)하는 방법에 대 한 자세한 내용은.</span><span class="sxs-lookup"><span data-stu-id="5bd5f-146">Learn more about [choosing federated identity with AD FS](https://docs.microsoft.com/en-us/azure/security/azure-ad-choose-authn).</span></span>
  
### <a name="third-party-authentication-and-identity-providers"></a><span data-ttu-id="5bd5f-147">타사 인증 및 id 공급자</span><span class="sxs-lookup"><span data-stu-id="5bd5f-147">Third-party authentication and identity providers</span></span>

<span data-ttu-id="5bd5f-p108">온-프레미스 디렉터리 개체를 Office 365로 동기화 될 수 및 클라우드 리소스 액세스는 주로 타사 id 공급자 (IdP)에 의해 관리 됩니다. 조직에서 타사 페더레이션 솔루션을 사용 하는 경우 구성할 수 있습니다 로그온 해당 솔루션 Office 365에 대 한 타사 페더레이션 솔루션 Azure AD와 호환 되는 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="5bd5f-p108">On-premises directory objects may be synchronized to Office 365 and cloud resource access is primarily managed by a third-party identity provider (IdP). If your organization uses a third-party federation solution, you can configure sign-on with that solution for Office 365 provided that the third-party federation solution is compatible with Azure AD.</span></span>
  
<span data-ttu-id="5bd5f-150">[Azure AD 페더레이션 호환성](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility)에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="5bd5f-150">Learn more about [Azure AD federation compatibility](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility).</span></span>
  
## <a name="configuring-identity-and-authentication-with-office-365"></a><span data-ttu-id="5bd5f-151">Office 365를 사용 하 여 id 및 인증 구성</span><span class="sxs-lookup"><span data-stu-id="5bd5f-151">Configuring identity and authentication with Office 365</span></span>

<span data-ttu-id="5bd5f-p109">Office 365 및 Azure AD와 온-프레미스 디렉터리 통합 (영문) [Azure AD 연결](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnect)된 간소화 되었습니다. Azure AD 연결 디렉터리에 연결 하는 가장 좋은 방법은 및 클라우드로 사용자를 동기화 할 조직에 대 한 Microsoft의 권장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5bd5f-p109">Integrating your on-premises directories with Office 365 and Azure AD has been simplified with [Azure AD Connect](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnect). Azure AD Connect is the best way to connect your directories and is Microsoft's recommendation for organizations to sync their users to the cloud.</span></span>
  
<span data-ttu-id="5bd5f-154">Azure AD 문에 사용할 수도 있습니다: [Azure AD 연결 관리자](https://aka.ms/aadconnectpwsync), [AD FS 배포 관리자](https://aka.ms/adfsguidance), 및 [Azure AD 프리미엄 설치 가이드](https://aka.ms/aadpguidance)입니다.</span><span class="sxs-lookup"><span data-stu-id="5bd5f-154">You can also use the Azure AD advisors: the [Azure AD Connect advisor](https://aka.ms/aadconnectpwsync), the [AD FS deployment advisor](https://aka.ms/adfsguidance), and the [Azure AD Premium setup guide](https://aka.ms/aadpguidance).</span></span>
  
## <a name="video-training"></a><span data-ttu-id="5bd5f-155">비디오 교육</span><span class="sxs-lookup"><span data-stu-id="5bd5f-155">Video training</span></span>

<span data-ttu-id="5bd5f-156">자세한 내용은 비디오 과정을 참조 하십시오. [Office 365: 관리 id가 사용 하 여 Azure AD 연결](https://support.office.com/article/90991a1d-c0ab-479a-b413-35c9706f6fed.aspx), LinkedIn 학습에 의해 제공자 합니다.</span><span class="sxs-lookup"><span data-stu-id="5bd5f-156">For more information, see the video course [Office 365: Manage Identities Using Azure AD Connect](https://support.office.com/article/90991a1d-c0ab-479a-b413-35c9706f6fed.aspx), brought to you by LinkedIn Learning.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="5bd5f-157">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5bd5f-157">See Also</span></span>

[<span data-ttu-id="5bd5f-158">디렉터리 동기화를 통해 사용자를 Office 365에 프로비전하기 위한 준비</span><span class="sxs-lookup"><span data-stu-id="5bd5f-158">Prepare to provision users through directory synchronization to Office 365</span></span>](https://support.office.com/article/prepare-to-provision-users-through-directory-synchronization-to-office-365-01920974-9e6f-4331-a370-13aea4e82b3e)
  
[<span data-ttu-id="5bd5f-159">PowerShell Office 365 서비스에 연결</span><span class="sxs-lookup"><span data-stu-id="5bd5f-159">Connect PowerShell to Office 365 services</span></span>](https://support.office.com/article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6)
  
[<span data-ttu-id="5bd5f-160">Office 365에 대 한 디렉터리 동기화를 통해 문제를 해결</span><span class="sxs-lookup"><span data-stu-id="5bd5f-160">Fixing problems with directory synchronization for Office 365</span></span>](https://support.office.com/article/fixing-problems-with-directory-synchronization-for-office-365-79c43023-5a47-45ae-8068-d8a26eee6bc2d)
  

