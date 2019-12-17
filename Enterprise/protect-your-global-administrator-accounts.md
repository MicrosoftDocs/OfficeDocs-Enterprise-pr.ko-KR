---
title: Office 365 전역 관리자 계정 보호
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/03/2019
audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Strat_O365_IP
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: 6b4ded77-ac8d-42ed-8606-c014fd947560
description: Office 365 구독에 대 한 전역 관리자 액세스를 보호 합니다.
ms.openlocfilehash: 293044fc508c89b5e08234aa62633c6c4490ba6d
ms.sourcegitcommit: 3539ec707f984de6f3b874744ff8b6832fbd665e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/17/2019
ms.locfileid: "40072210"
---
# <a name="protect-your-office-365-global-administrator-accounts"></a><span data-ttu-id="2c284-103">Office 365 전역 관리자 계정 보호</span><span class="sxs-lookup"><span data-stu-id="2c284-103">Protect your Office 365 global administrator accounts</span></span>

<span data-ttu-id="2c284-104">*이 문서는 Microsoft 365 Enterprise와 Office 365 Enterprise에 모두 적용됩니다.*</span><span class="sxs-lookup"><span data-stu-id="2c284-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="2c284-105">정보 수집 및 피싱 공격을 비롯 한 Office 365 구독의 보안 침해는 일반적으로 Office 365 전역 관리자 계정의 자격 증명을 손상 시켜 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c284-105">Security breaches of an Office 365 subscription, including information harvesting and phishing attacks, are typically done by compromising the credentials of an Office 365 global administrator account.</span></span> <span data-ttu-id="2c284-106">클라우드의 보안은 사용자와 Microsoft 간의 파트너 관계입니다.</span><span class="sxs-lookup"><span data-stu-id="2c284-106">Security in the cloud is a partnership between you and Microsoft:</span></span>
  
- <span data-ttu-id="2c284-107">Microsoft 클라우드 서비스는 신뢰 및 보안을 기반으로 구축 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c284-107">Microsoft cloud services are built on a foundation of trust and security.</span></span> <span data-ttu-id="2c284-108">Microsoft는 데이터와 응용 프로그램을 보호 하는 데 도움이 되는 보안 제어 및 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c284-108">Microsoft provides you security controls and capabilities to help you protect your data and applications.</span></span>
    
- <span data-ttu-id="2c284-109">사용자의 데이터 및 id를 보호 하 고, 온-프레미스 리소스의 보안을 관리 하 고, 사용자가 제어 하는 클라우드 구성 요소의 보안을 담당 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c284-109">You own your data and identities and the responsibility for protecting them, the security of your on-premises resources, and the security of cloud components you control.</span></span>
    
<span data-ttu-id="2c284-110">Microsoft는 조직을 보호 하기 위한 기능을 제공 하지만, 이러한 기능은 사용 하는 경우에만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c284-110">Microsoft provides capabilities to help protect your organization, but they are effective only if you use them.</span></span> <span data-ttu-id="2c284-111">사용 하지 않는 경우 공격에 취약할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c284-111">If you do not use them, you may be vulnerable to attack.</span></span> <span data-ttu-id="2c284-112">전역 관리자 계정을 보호 하기 위해 Microsoft는 다음에 대 한 자세한 지침을 제공 하는 데 도움이 되는 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c284-112">To protect your global administrator accounts, Microsoft is here to help you with detailed instructions to:</span></span>
  
1. <span data-ttu-id="2c284-113">전용 Office 365 전역 관리자 계정을 만들고 필요한 경우에만이를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c284-113">Create dedicated Office 365 global administrator accounts and use them only when necessary.</span></span>
    
2. <span data-ttu-id="2c284-114">전용 Office 365 전역 관리자 계정에 대해 multi-factor authentication을 구성 하 고 가장 강력한 형태의 보조 인증을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c284-114">Configure multi-factor authentication for your dedicated Office 365 global administrator accounts and use the strongest form of secondary authentication.</span></span>
    
> [!NOTE]
> <span data-ttu-id="2c284-115">이 문서에서는 전역 관리자 계정에 초점을 맞추었습니다 하지만 구독에 포함 된 데이터에 액세스 하기 위한 광범위 한 사용 권한이 있는 추가 계정 (예: eDiscovery 관리자 또는 보안 또는 준수 관리자)이 있는지 고려해 야 합니다. 동일한 방식으로 계정을 보호 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c284-115">Although this article is focused on global administrator accounts, you should consider whether additional accounts with wide-ranging permissions to access the data in your subscription, such as eDiscovery administrator or security or compliance administrator accounts, should be protected in the same way.</span></span> 
  
## <a name="step-1-create-dedicated-office-365-global-administrator-accounts-and-use-them-only-when-necessary"></a><span data-ttu-id="2c284-116">1단계.</span><span class="sxs-lookup"><span data-stu-id="2c284-116">Step 1.</span></span> <span data-ttu-id="2c284-117">전용 Office 365 전역 관리자 계정을 만들고 필요한 경우에만이를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c284-117">Create dedicated Office 365 global administrator accounts and use them only when necessary</span></span>

<span data-ttu-id="2c284-118">전역 관리자 권한이 필요한 관리 작업 (예: 사용자 계정에 역할 할당)은 비교적 적습니다.</span><span class="sxs-lookup"><span data-stu-id="2c284-118">There are relatively few administrative tasks, such as assigning roles to user accounts, that require global administrator privileges.</span></span> <span data-ttu-id="2c284-119">따라서 전역 관리자 역할이 할당 된 일상적인 사용자 계정을 사용 하는 대신, 다음 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c284-119">Therefore, instead of using everyday user accounts that have been assigned the global admin role, do these steps:</span></span>
  
1. <span data-ttu-id="2c284-120">전역 관리자 역할이 할당 된 사용자 계정 집합을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c284-120">Determine the set of user accounts that have been assigned the global admin role.</span></span> <span data-ttu-id="2c284-121">이 작업은 Graph 용 Azure 활성 (Azure AD) 디렉터리 PowerShell 명령에 대해 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c284-121">You can do this with Azure Active (Azure AD) Directory PowerShell for Graph  command:</span></span>
  
  ```powershell
  Get-AzureADDirectoryRole | where { $_.DisplayName -eq "Company Administrator" } | Get-AzureADDirectoryRoleMember | Ft DisplayName
  ```

2. <span data-ttu-id="2c284-122">전역 관리자 역할이 할당 된 사용자 계정으로 Office 365 구독에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c284-122">Sign into your Office 365 subscription with a user account that has been assigned the global admin role.</span></span>
    
3. <span data-ttu-id="2c284-123">최대 5 개의 전용 전역 관리자 사용자 계정을 하나 이상 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2c284-123">Create at least one and up to a maximum of five dedicated global administrator user accounts.</span></span> <span data-ttu-id="2c284-124">**최소 12 자 이상의 강력한 암호를 사용 합니다.**</span><span class="sxs-lookup"><span data-stu-id="2c284-124">**Use strong passwords at least 12 characters long.**</span></span> <span data-ttu-id="2c284-125">자세한 내용은 [강력한 암호 만들기를](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password) 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2c284-125">See [Create a strong password](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password) for more information.</span></span> <span data-ttu-id="2c284-126">새 계정에 대 한 암호를 안전한 위치에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c284-126">Store the passwords for the new accounts in a secure location.</span></span> 
    
4. <span data-ttu-id="2c284-127">전역 관리자 역할을 각각의 새 전용 전역 관리자 사용자 계정에 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c284-127">Assign the global admin role to each of the new dedicated global administrator user accounts.</span></span>
    
5. <span data-ttu-id="2c284-128">Office 365에서 로그 아웃 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c284-128">Sign out of Office 365.</span></span>
    
6. <span data-ttu-id="2c284-129">새로운 전용 전역 관리자 사용자 계정 중 하나를 사용 하 여 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c284-129">Sign in with one of the new dedicated global administrator user accounts.</span></span>
    
7. <span data-ttu-id="2c284-130">1 단계에서 전역 관리자 역할이 할당 된 각 기존 사용자 계정에 대해 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c284-130">For each existing user account that had been assigned the global admin role from step 1:</span></span>
    
  - <span data-ttu-id="2c284-131">전역 관리자 역할을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c284-131">Remove the global admin role.</span></span>
    
  - <span data-ttu-id="2c284-132">해당 사용자의 작업 기능 및 책임에 해당 하는 관리자 역할을 계정에 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c284-132">Assign admin roles to the account that are appropriate to that user's job function and responsibility.</span></span> <span data-ttu-id="2c284-133">Office 365의 다양 한 관리자 역할에 대 한 자세한 내용은 [관리 역할 정보](https://docs.microsoft.com/office365/admin/add-users/about-admin-roles)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="2c284-133">For more information about various admin roles in Office 365, see [About admin roles](https://docs.microsoft.com/office365/admin/add-users/about-admin-roles).</span></span>
    
8. <span data-ttu-id="2c284-134">Office 365에서 로그 아웃 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c284-134">Sign out of Office 365.</span></span>
    
<span data-ttu-id="2c284-135">결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2c284-135">The result should be:</span></span>
  
- <span data-ttu-id="2c284-136">구독에서 전역 관리자 역할이 할당된 사용자 계정은 새로운 전용 전역 관리자 계정 집합뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="2c284-136">The only user accounts in your subscription that have the global admin role are the new set of dedicated global administrator accounts.</span></span> <span data-ttu-id="2c284-137">다음 PowerShell 명령을 사용 하 여이를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c284-137">Verify this with the following PowerShell command:</span></span>
    
  ```powershell
  Get-AzureADDirectoryRole | where { $_.DisplayName -eq "Company Administrator" } | Get-AzureADDirectoryRoleMember | Ft DisplayName
  ```

- <span data-ttu-id="2c284-138">구독을 관리하는 다른 모든 일상적인 사용자 계정에는 업무 책임과 연관된 관리자 역할이 할당되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c284-138">All other everyday user accounts that manage your subscription have admin roles assigned that are associated with their job responsibilities.</span></span>
    
<span data-ttu-id="2c284-139">이 순간 부터는 전역 관리자 권한이 필요한 작업에 대해서만 전용 전역 관리자 계정으로 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c284-139">From this moment onward, you sign in with the dedicated global administrator accounts only for tasks that require global administrator privileges.</span></span> <span data-ttu-id="2c284-140">다른 모든 Office 365 관리는 사용자 계정에 다른 관리 역할을 할당 하 여 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c284-140">All other Office 365 administration must be done by assigning other administration roles to user accounts.</span></span>
  
> [!NOTE]
> <span data-ttu-id="2c284-141">이렇게 하려면 일상적인 사용자 계정으로 로그 아웃 하 고 전용 전역 관리자 계정으로 로그인 하기 위한 추가 단계가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c284-141">This does require additional steps to sign out as your everyday user account and sign in with a dedicated global administrator account.</span></span> <span data-ttu-id="2c284-142">하지만이 작업을 가끔씩만 수행 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c284-142">But this only needs to be done occasionally for global administrator operations.</span></span> <span data-ttu-id="2c284-143">전역 관리자 계정 위반 후에 Office 365 구독을 복구 하려면 많은 단계가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c284-143">Consider that recovering your Office 365 subscription after a global administrator account breach requires a lot more steps.</span></span>
  
## <a name="step-2-configure-multi-factor-authentication-for-your-dedicated-office-365-global-administrator-accounts-and-use-the-strongest-form-of-secondary-authentication"></a><span data-ttu-id="2c284-144">2단계.</span><span class="sxs-lookup"><span data-stu-id="2c284-144">Step 2.</span></span> <span data-ttu-id="2c284-145">전용 Office 365 전역 관리자 계정에 대해 multi-factor authentication을 구성 하 고 가장 강력한 형태의 보조 인증 사용</span><span class="sxs-lookup"><span data-stu-id="2c284-145">Configure multi-factor authentication for your dedicated Office 365 global administrator accounts and use the strongest form of secondary authentication</span></span>

<span data-ttu-id="2c284-146">MFA (multi-factor authentication)에는 계정 이름 및 암호 외에 추가 정보가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c284-146">Multi-factor authentication (MFA) requires additional information beyond the account name and password.</span></span> <span data-ttu-id="2c284-147">Office 365에서는 다음과 같은 확인 방법을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c284-147">Office 365 supports these verification methods:</span></span>
  
- <span data-ttu-id="2c284-148">전화 통화</span><span class="sxs-lookup"><span data-stu-id="2c284-148">A phone call</span></span>
    
- <span data-ttu-id="2c284-149">임의로 생성된 암호</span><span class="sxs-lookup"><span data-stu-id="2c284-149">A randomly generated pass code</span></span>
    
- <span data-ttu-id="2c284-150">스마트 카드(가상 또는 실제)</span><span class="sxs-lookup"><span data-stu-id="2c284-150">A smart card (virtual or physical)</span></span>
    
- <span data-ttu-id="2c284-151">생체 인식 장치</span><span class="sxs-lookup"><span data-stu-id="2c284-151">A biometric device</span></span>
    
<span data-ttu-id="2c284-152">클라우드에만 저장 된 사용자 계정을 사용 하는 소규모 회사 인 경우 (클라우드 전용 id 모델) 이러한 단계를 사용 하 여 전화 통화 또는 스마트 전화로 전송 되는 텍스트 메시지 확인 코드를 사용 하 여 MFA를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c284-152">If you are a small business that is using user accounts stored only in the cloud (the cloud-only identity model), use these steps to configure MFA using a phone call or a text message verification code sent to a smart phone:</span></span>
  
1. <span data-ttu-id="2c284-153">[MFA를 설정](https://docs.microsoft.com/office365/admin/security-and-compliance/set-up-multi-factor-authentication)합니다.</span><span class="sxs-lookup"><span data-stu-id="2c284-153">[Set up MFA](https://docs.microsoft.com/office365/admin/security-and-compliance/set-up-multi-factor-authentication).</span></span>
    
2. <span data-ttu-id="2c284-154">[Office 365에 대 한 2 단계 인증을 설정](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) 하 여 전화 통화 또는 문자 메시지에 대 한 각 전용 전역 관리자 계정을 확인 방법으로 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c284-154">[Set up 2-step verification for Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) to configure each dedicated global administrator account for phone call or text message as the verification method.</span></span> 
    
<span data-ttu-id="2c284-155">Office 365 하이브리드 id 모델을 사용 하는 조직 규모가 큰 경우에는 더 많은 확인 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c284-155">If you are a larger organization that is using an Office 365 hybrid identity model, you have more verification options.</span></span> <span data-ttu-id="2c284-156">더 강력한 보조 인증 방법으로 보안 인프라가 이미 마련 되어 있는 경우 다음 단계를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c284-156">If you have the security infrastructure already in place for a stronger secondary authentication method, use these steps:</span></span>
  
1. <span data-ttu-id="2c284-157">[MFA를 설정](https://docs.microsoft.com/office365/admin/security-and-compliance/set-up-multi-factor-authentication)합니다.</span><span class="sxs-lookup"><span data-stu-id="2c284-157">[Set up MFA](https://docs.microsoft.com/office365/admin/security-and-compliance/set-up-multi-factor-authentication).</span></span>
    
2. <span data-ttu-id="2c284-158">[Office 365에 대 한 2 단계 인증을 설정](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) 하 여 적절 한 확인 방법에 대해 각 전용 전역 관리자 계정을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c284-158">[Set up 2-step verification for Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) to configure each dedicated global administrator account for the appropriate verification method.</span></span> 
    
<span data-ttu-id="2c284-159">원하는 보다 강력한 확인 방법의 보안 인프라가 제대로 작동 하지 않고 Office 365 MFA에 적합 하지 않은 경우 전화 통화 또는 문자 메시지를 사용 하 여 MFA로 전용 전역 관리자 계정을 구성 하는 것이 좋습니다. 중간 보안 조치로 전역 관리자 계정의 스마트 전화로 전송 되는 확인 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="2c284-159">If the security infrastructure for the desired stronger verification method is not in place and functioning for Office 365 MFA, we strongly recommend that you configure dedicated global administrator accounts with MFA using a phone call or a text message verification code sent to a smart phone for your global administrator accounts as an interim security measure.</span></span> <span data-ttu-id="2c284-160">MFA에서 제공 하는 추가 보호를 사용 하지 않고 전용 전역 관리자 계정을 그대로 사용 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="2c284-160">Do not leave your dedicated global administrator accounts without the additional protection provided by MFA.</span></span>
  
<span data-ttu-id="2c284-161">자세한 내용은 [Office 365 배포에 대한 다단계 인증 계획](https://docs.microsoft.com/office365/admin/security-and-compliance/multi-factor-authentication-plan)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2c284-161">For more information, see [Plan for multi-factor authentication for Office 365 Deployments](https://docs.microsoft.com/office365/admin/security-and-compliance/multi-factor-authentication-plan).</span></span>
  
<span data-ttu-id="2c284-162">MFA 및 PowerShell을 사용 하 여 Office 365 서비스에 연결 하려면 다음 문서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2c284-162">To connect to Office 365 services with MFA and PowerShell, see these articles:</span></span>

- [<span data-ttu-id="2c284-163">사용자 계정, 그룹 및 라이선스에 대 한 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="2c284-163">Office 365 PowerShell for user accounts, groups, and licenses</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell)
- [<span data-ttu-id="2c284-164">Exchange Online</span><span class="sxs-lookup"><span data-stu-id="2c284-164">Exchange Online</span></span>](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell#connect-to-exchange-online-powershell-by-using-mfa)
- [<span data-ttu-id="2c284-165">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="2c284-165">SharePoint Online</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online#to-connect-with-multifactor-authentication-mfa)
- [<span data-ttu-id="2c284-166">비즈니스용 Skype Online</span><span class="sxs-lookup"><span data-stu-id="2c284-166">Skype for Business Online</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell#connect-using-a-skype-for-business-online-administrator-account-with-multifactor-authentication)

## <a name="additional-protections-for-enterprise-organizations"></a><span data-ttu-id="2c284-167">엔터프라이즈 조직에 대 한 추가 보호</span><span class="sxs-lookup"><span data-stu-id="2c284-167">Additional protections for enterprise organizations</span></span>

<span data-ttu-id="2c284-168">1 ~ 2 단계를 수행한 후에는 이러한 추가 방법을 사용 하 여 전역 관리자 계정 및이 계정을 사용 하 여 수행 하는 구성이 최대한 안전한 지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c284-168">After steps 1 and 2, use these additional methods to ensure that your global administrator account, and the configuration that you perform using it, are as secure as possible.</span></span>
  
### <a name="privileged-access-workstation"></a><span data-ttu-id="2c284-169">권한이 부여 된 액세스 워크스테이션</span><span class="sxs-lookup"><span data-stu-id="2c284-169">Privileged access workstation</span></span>

<span data-ttu-id="2c284-170">높은 권한 작업의 실행을 최대한 안전한 상태로 유지 하려면 권한이 부여 된 액세스 워크스테이션 (발 없는)을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c284-170">To ensure that the execution of highly privileged tasks is as secure as possible, use a privileged access workstation (PAW).</span></span> <span data-ttu-id="2c284-171">발 없는는 전역 관리자 계정이 필요한 Office 365 구성 같은 중요 한 구성 작업에만 사용 되는 전용 컴퓨터입니다.</span><span class="sxs-lookup"><span data-stu-id="2c284-171">A PAW is a dedicated computer that is only used for sensitive configuration tasks, such as Office 365 configuration that requires a global administrator account.</span></span> <span data-ttu-id="2c284-172">이 컴퓨터는 인터넷 브라우징이 나 전자 메일에 대해 매일 사용 되지 않으므로 인터넷 공격 및 위협 으로부터 보호 되는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="2c284-172">Because this computer is not used daily for Internet browsing or email, it is better protected from Internet attacks and threats.</span></span>
  
<span data-ttu-id="2c284-173">발 없는를 설정 하는 방법에 대 한 자세한 내용은 [https://aka.ms/cyberpaw](https://aka.ms/cyberpaw)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2c284-173">For instructions on how to set up a PAW, see [https://aka.ms/cyberpaw](https://aka.ms/cyberpaw).</span></span>
  
### <a name="azure-ad-privileged-identity-management"></a><span data-ttu-id="2c284-174">Azure AD Privileged Identity Management</span><span class="sxs-lookup"><span data-stu-id="2c284-174">Azure AD Privileged Identity Management</span></span>

<span data-ttu-id="2c284-175">전역 관리자 계정을 전역 관리자 역할에 영구적으로 할당 하는 대신, Azure AD PIM (권한 부여 Id 관리)을 사용 하 여 필요에 따라 글로벌 관리자 역할에 대 한 주문형 (온-just-in-time) 할당을 사용 하도록 설정할 수 있습니다. 불필요.</span><span class="sxs-lookup"><span data-stu-id="2c284-175">Rather than having your global administrator accounts be permanently assigned the global administrator role, you can use Azure AD Privileged Identity Management (PIM) to enable on-demand, just-in-time assignment of the global administrator role when it is needed.</span></span>
  
<span data-ttu-id="2c284-176">전역 관리자 계정 대신 영구 관리자가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c284-176">Instead of your global administrator accounts being a permanent admin, they become eligible administrators.</span></span> <span data-ttu-id="2c284-177">전역 관리자 역할은 사용자가 필요한 경우에만 비활성화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c284-177">The global administrator role is inactive until someone needs it.</span></span> <span data-ttu-id="2c284-178">그런 다음 정품 인증 프로세스를 완료 하 여 전역 관리자 계정에 미리 정의 된 시간에 대 한 역할을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c284-178">You then complete an activation process to add the global administrator role to the global administrator account for a predetermined amount of time.</span></span> <span data-ttu-id="2c284-179">시간이 만료 되 면 PIM은 전역 관리자 계정에서 전역 관리자 역할을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c284-179">When the time expires, PIM removes the global administrator role from the global administrator account.</span></span>
  
<span data-ttu-id="2c284-180">PIM 및이 프로세스를 사용 하면 악의적인 사용자가 공격 하 고 사용할 수 있는 전역 관리자 계정의 시간이 크게 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="2c284-180">Using PIM and this process significantly reduces the amount of time that your global administrator accounts are vulnerable to attack and use by malicious users.</span></span>
  
<span data-ttu-id="2c284-181">자세한 내용은 [AZURE AD 권한 Id 관리](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2c284-181">For more information, see [Azure AD Privileged Identity Management](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure).</span></span>
  
> [!NOTE]
> <span data-ttu-id="2c284-182">PIM은 Microsoft 365 Enterprise E5 또는 EMS (Enterprise Mobility + Security) e 5에 포함 된 Azure AD Premium P2에 제공 되거나, 전역 관리자 계정에 대 한 개별 라이선스를 구입할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c284-182">PIM is available with Azure AD Premium P2, which is included with Microsoft 365 Enterprise E5 or Enterprise Mobility + Security (EMS) E5, or you can purchase individual licenses for your global administrator accounts.</span></span> 
  
### <a name="security-information-and-event-management-siem-software-for-office-365-logging"></a><span data-ttu-id="2c284-183">Office 365 용 SIEM (보안 정보 및 이벤트 관리) 소프트웨어</span><span class="sxs-lookup"><span data-stu-id="2c284-183">Security information and event management (SIEM) software for Office 365 logging</span></span>

<span data-ttu-id="2c284-184">SIEM 소프트웨어 서버에서 실행 되는 응용 프로그램 및 네트워크 하드웨어에 의해 생성 되는 이벤트에 대 한 실시간 분석을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c284-184">SIEM software run on a server performs real-time analysis of security alerts and events created by applications and network hardware.</span></span> <span data-ttu-id="2c284-185">SIEM 서버에서 분석 및 보고 기능에 Office 365 보안 경고 및 이벤트를 포함 하도록 허용 하려면 Azure AD를 사용자에 게 통합 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c284-185">To allow your SIEM server to include Office 365 security alerts and events in its analysis and reporting functions, integrate Azure AD into you SEIM.</span></span> <span data-ttu-id="2c284-186">[Azure 로그 통합 소개를](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview)참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2c284-186">See [Introduction to Azure Log Integration](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview).</span></span>

## <a name="next-step"></a><span data-ttu-id="2c284-187">다음 단계</span><span class="sxs-lookup"><span data-stu-id="2c284-187">Next step</span></span>

<span data-ttu-id="2c284-188">Office 365 구독에 대 한 id를 설정 하는 경우 다음을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="2c284-188">If you're setting up identity for your Office 365 subscription, see:</span></span>

- <span data-ttu-id="2c284-189">클라우드 전용 id를 사용 하는 경우 [클라우드 전용 id](cloud-only-identities.md)</span><span class="sxs-lookup"><span data-stu-id="2c284-189">[Cloud-only identities](cloud-only-identities.md) if you're using cloud-only identity</span></span>
- <span data-ttu-id="2c284-190">하이브리드 id를 사용 하 [는 경우 디렉터리 동기화 준비](prepare-for-directory-synchronization.md)</span><span class="sxs-lookup"><span data-stu-id="2c284-190">[Prepare for directory synchronization](prepare-for-directory-synchronization.md) if you're using hybrid identity</span></span>

  
## <a name="see-also"></a><span data-ttu-id="2c284-191">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2c284-191">See also</span></span>

<span data-ttu-id="2c284-192">[Office 365 보안 로드맵](https://docs.microsoft.com/office365/securitycompliance/security-roadmap)</span><span class="sxs-lookup"><span data-stu-id="2c284-192">[Office 365 security roadmap](https://docs.microsoft.com/office365/securitycompliance/security-roadmap).</span></span>
