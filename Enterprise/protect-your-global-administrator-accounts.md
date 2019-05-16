---
title: Office 365 전역 관리자 계정 보호
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 4/10/2018
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
description: 다음 세 가지 단계를 수행 하 여 Office 365 구독에 대 한 전역 관리자 액세스를 보호 합니다.
ms.openlocfilehash: bb1b19a7ac0ec8e32c23303e8acf2b7ee42f0532
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34071024"
---
# <a name="protect-your-office-365-global-administrator-accounts"></a><span data-ttu-id="b5abd-103">Office 365 전역 관리자 계정 보호</span><span class="sxs-lookup"><span data-stu-id="b5abd-103">Protect your Office 365 global administrator accounts</span></span>

 <span data-ttu-id="b5abd-104">**요약:** 전역 관리자 계정의 손상에 따라 공격 으로부터 Office 365 구독을 보호 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-104">**Summary:** Protect your Office 365 subscription from attacks based on the compromise of a global administrator account.</span></span> 
  
<span data-ttu-id="b5abd-105">정보 수집 및 피싱 공격을 비롯 한 Office 365 구독의 보안 침해는 일반적으로 Office 365 전역 관리자 계정의 자격 증명을 손상 시켜 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-105">Security breaches of an Office 365 subscription, including information harvesting and phishing attacks, are typically done by compromising the credentials of an Office 365 global administrator account.</span></span> <span data-ttu-id="b5abd-106">클라우드의 보안은 사용자와 Microsoft 간의 파트너 관계입니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-106">Security in the cloud is a partnership between you and Microsoft:</span></span>
  
- <span data-ttu-id="b5abd-107">Microsoft 클라우드 서비스는 신뢰 및 보안을 기반으로 구축 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-107">Microsoft cloud services are built on a foundation of trust and security.</span></span> <span data-ttu-id="b5abd-108">Microsoft는 데이터와 응용 프로그램을 보호 하는 데 도움이 되는 보안 제어 및 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-108">Microsoft provides you security controls and capabilities to help you protect your data and applications.</span></span>
    
- <span data-ttu-id="b5abd-109">사용자의 데이터 및 id를 보호 하 고, 온-프레미스 리소스의 보안을 관리 하 고, 사용자가 제어 하는 클라우드 구성 요소의 보안을 담당 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-109">You own your data and identities and the responsibility for protecting them, the security of your on-premises resources, and the security of cloud components you control.</span></span>
    
<span data-ttu-id="b5abd-110">Microsoft는 조직을 보호 하기 위한 기능을 제공 하지만, 이러한 기능은 사용 하는 경우에만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-110">Microsoft provides capabilities to help protect your organization, but they are effective only if you use them.</span></span> <span data-ttu-id="b5abd-111">사용 하지 않는 경우 공격에 취약할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-111">If you do not use them, you may be vulnerable to attack.</span></span> <span data-ttu-id="b5abd-112">전역 관리자 계정을 보호 하기 위해 Microsoft는 다음에 대 한 자세한 지침을 제공 하는 데 도움이 되는 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-112">To protect your global administrator accounts, Microsoft is here to help you with detailed instructions to:</span></span>
  
1. <span data-ttu-id="b5abd-113">전용 Office 365 전역 관리자 계정을 만들고 필요한 경우에만이를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-113">Create dedicated Office 365 global administrator accounts and use them only when necessary.</span></span>
    
2. <span data-ttu-id="b5abd-114">전용 Office 365 전역 관리자 계정에 대해 multi-factor authentication을 구성 하 고 가장 강력한 형태의 보조 인증을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-114">Configure multi-factor authentication for your dedicated Office 365 global administrator accounts and use the strongest form of secondary authentication.</span></span>
    
3. <span data-ttu-id="b5abd-115">의심 스러운 전역 관리자 계정 활동을 모니터링 하도록 Office 365 Cloud App Security를 사용 하도록 설정 하 고 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-115">Enable and configure Office 365 Cloud App Security to monitor for suspicious global administrator account activity.</span></span>
    
> [!NOTE]
> <span data-ttu-id="b5abd-116">이 문서에서는 전역 관리자 계정에 초점을 맞추었습니다 하지만 구독에 포함 된 데이터에 액세스 하는 데 필요한 추가 계정 (예: eDiscovery 관리자 또는 보안 또는 규정 준수)이 있는지도 고려해 야 합니다. 관리자 계정을 동일한 방식으로 보호 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-116">Although this article is focused on global administrator accounts, you should also consider whether additional accounts with wide-ranging permissions to access the data in your subscription, such as eDiscovery administrator or security or compliance administrator accounts, should be protected in the same way.</span></span> 
  
## <a name="step-1-create-dedicated-office-365-global-administrator-accounts-and-use-them-only-when-necessary"></a><span data-ttu-id="b5abd-117">1단계.</span><span class="sxs-lookup"><span data-stu-id="b5abd-117">Step 1.</span></span> <span data-ttu-id="b5abd-118">전용 Office 365 전역 관리자 계정을 만들고 필요한 경우에만이를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-118">Create dedicated Office 365 global administrator accounts and use them only when necessary</span></span>

<span data-ttu-id="b5abd-119">전역 관리자 권한이 필요한 관리 작업 (예: 사용자 계정에 역할 할당)은 비교적 적습니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-119">There are relatively few administrative tasks, such as assigning roles to user accounts, that require global administrator privileges.</span></span> <span data-ttu-id="b5abd-120">따라서 전역 관리자 역할이 할당 된 일상적인 사용자 계정을 사용 하는 대신, 다음 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-120">Therefore, instead of using everyday user accounts that have been assigned the global admin role, do these steps:</span></span>
  
1. <span data-ttu-id="b5abd-121">전역 관리자 역할이 할당 된 사용자 계정 집합을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-121">Determine the set of user accounts that have been assigned the global admin role.</span></span> <span data-ttu-id="b5abd-122">Windows PowerShell 용 Microsoft Azure Active Directory 모듈 명령 프롬프트에서 다음 명령을 사용 하 여이 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-122">You can do this with this command at the Microsoft Azure Active Directory Module for Windows PowerShell command prompt:</span></span>
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

2. <span data-ttu-id="b5abd-123">전역 관리자 역할이 할당 된 사용자 계정으로 Office 365 구독에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-123">Sign into your Office 365 subscription with a user account that has been assigned the global admin role.</span></span>
    
3. <span data-ttu-id="b5abd-124">최대 5 개의 전용 전역 관리자 사용자 계정을 하나 이상 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-124">Create at least one and up to a maximum of five dedicated global administrator user accounts.</span></span> <span data-ttu-id="b5abd-125">**최소 12 자 이상의 강력한 암호를 사용 합니다.**</span><span class="sxs-lookup"><span data-stu-id="b5abd-125">**Use strong passwords at least 12 characters long.**</span></span> <span data-ttu-id="b5abd-126">자세한 내용은 [강력한 암호 만들기를](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password) 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b5abd-126">See [Create a strong password](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password) for more information.</span></span> <span data-ttu-id="b5abd-127">새 계정에 대 한 암호를 안전한 위치에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-127">Store the passwords for the new accounts in a secure location.</span></span> 
    
4. <span data-ttu-id="b5abd-128">전역 관리자 역할을 각각의 새 전용 전역 관리자 사용자 계정에 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-128">Assign the global admin role to each of the new dedicated global administrator user accounts.</span></span>
    
5. <span data-ttu-id="b5abd-129">Office 365에서 로그 아웃 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-129">Sign out of Office 365.</span></span>
    
6. <span data-ttu-id="b5abd-130">새로운 전용 전역 관리자 사용자 계정 중 하나를 사용 하 여 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-130">Sign in with one of the new dedicated global administrator user accounts.</span></span>
    
7. <span data-ttu-id="b5abd-131">1 단계에서 전역 관리자 역할이 할당 된 각 기존 사용자 계정에 대해 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-131">For each existing user account that had been assigned the global admin role from step 1:</span></span>
    
  - <span data-ttu-id="b5abd-132">전역 관리자 역할을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-132">Remove the global admin role.</span></span>
    
  - <span data-ttu-id="b5abd-133">해당 사용자의 작업 기능 및 책임에 해당 하는 관리자 역할을 계정에 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-133">Assign admin roles to the account that are appropriate to that user's job function and responsibility.</span></span> <span data-ttu-id="b5abd-134">Office 365의 다양 한 관리자 역할에 대 한 자세한 내용은 [office 365 관리자 역할 정보](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b5abd-134">For more information about various admin roles in Office 365, see [About Office 365 admin roles](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d).</span></span>
    
8. <span data-ttu-id="b5abd-135">Office 365에서 로그 아웃 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-135">Sign out of Office 365.</span></span>
    
<span data-ttu-id="b5abd-136">결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-136">The result should be:</span></span>
  
- <span data-ttu-id="b5abd-137">구독에서 전역 관리자 역할이 할당된 사용자 계정은 새로운 전용 전역 관리자 계정 집합뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-137">The only user accounts in your subscription that have the global admin role are the new set of dedicated global administrator accounts.</span></span> <span data-ttu-id="b5abd-138">다음 PowerShell 명령을 사용 하 여이를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-138">Verify this with the following PowerShell command:</span></span>
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

- <span data-ttu-id="b5abd-139">구독을 관리하는 다른 모든 일상적인 사용자 계정에는 업무 책임과 연관된 관리자 역할이 할당되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-139">All other everyday user accounts that manage your subscription have admin roles assigned that are associated with their job responsibilities.</span></span>
    
<span data-ttu-id="b5abd-140">이 순간 부터는 전역 관리자 권한이 필요한 작업에 대해서만 전용 전역 관리자 계정으로 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-140">From this moment onward, you sign in with the dedicated global administrator accounts only for tasks that require global administrator privileges.</span></span> <span data-ttu-id="b5abd-141">다른 모든 Office 365 관리는 사용자 계정에 다른 관리 역할을 할당 하 여 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-141">All other Office 365 administration must be done by assigning other administration roles to user accounts.</span></span>
  
> [!NOTE]
> <span data-ttu-id="b5abd-142">예, 일상적인 사용자 계정으로 로그 아웃 하 고 전용 전역 관리자 계정을 사용 하 여 로그인 하려면 추가 단계가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-142">Yes, this requires additional steps to sign out as your everyday user account and sign in with a dedicated global administrator account.</span></span> <span data-ttu-id="b5abd-143">하지만이 작업을 가끔씩만 수행 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-143">But this only needs to be done occasionally for global administrator operations.</span></span> <span data-ttu-id="b5abd-144">전역 관리자 계정 위반 후에 Office 365 구독을 복구 하려면 많은 단계가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-144">Consider that recovering your Office 365 subscription after a global administrator account breach requires a lot more steps.</span></span> 
  
## <a name="step-2-configure-multi-factor-authentication-for-your-dedicated-office-365-global-administrator-accounts-and-use-the-strongest-form-of-secondary-authentication"></a><span data-ttu-id="b5abd-145">2단계.</span><span class="sxs-lookup"><span data-stu-id="b5abd-145">Step 2.</span></span> <span data-ttu-id="b5abd-146">전용 Office 365 전역 관리자 계정에 대해 multi-factor authentication을 구성 하 고 가장 강력한 형태의 보조 인증 사용</span><span class="sxs-lookup"><span data-stu-id="b5abd-146">Configure multi-factor authentication for your dedicated Office 365 global administrator accounts and use the strongest form of secondary authentication</span></span>

<span data-ttu-id="b5abd-147">전역 관리자 계정에 대 한 MFA (Multi-factor authentication)에는 계정 이름 및 암호 외에 추가 정보가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-147">Multi-factor authentication (MFA) for your global administrator accounts requires additional information beyond the account name and password.</span></span> <span data-ttu-id="b5abd-148">Office 365에서는 다음과 같은 확인 방법을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-148">Office 365 supports these verification methods:</span></span>
  
- <span data-ttu-id="b5abd-149">전화 통화</span><span class="sxs-lookup"><span data-stu-id="b5abd-149">A phone call</span></span>
    
- <span data-ttu-id="b5abd-150">임의로 생성된 암호</span><span class="sxs-lookup"><span data-stu-id="b5abd-150">A randomly generated pass code</span></span>
    
- <span data-ttu-id="b5abd-151">스마트 카드(가상 또는 실제)</span><span class="sxs-lookup"><span data-stu-id="b5abd-151">A smart card (virtual or physical)</span></span>
    
- <span data-ttu-id="b5abd-152">생체 인식 장치</span><span class="sxs-lookup"><span data-stu-id="b5abd-152">A biometric device</span></span>
    
<span data-ttu-id="b5abd-153">클라우드에만 저장 된 사용자 계정을 사용 하는 소규모 회사 인 경우 (클라우드 id 모델) 이러한 단계를 사용 하 여 전화 통화 또는 스마트 전화로 전송 된 텍스트 메시지 확인 코드를 사용 하 여 MFA를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-153">If you are a small business that is using user accounts stored only in the cloud (the cloud identity model), use these steps to configure MFA using a phone call or a text message verification code sent to a smart phone:</span></span>
  
1. <span data-ttu-id="b5abd-154">[MFA를 사용 하도록 설정](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6)합니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-154">[Enable MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).</span></span>
    
2. <span data-ttu-id="b5abd-155">[Office 365에 대 한 2 단계 인증을 설정](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) 하 여 전화 통화 또는 문자 메시지에 대 한 각 전용 전역 관리자 계정을 확인 방법으로 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-155">[Set up 2-step verification for Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) to configure each dedicated global administrator account for phone call or text message as the verification method.</span></span> 
    
<span data-ttu-id="b5abd-156">Office 365 하이브리드 id 모델을 사용 하는 조직 규모가 큰 경우에는 더 많은 확인 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-156">If you are a larger organization that is using an Office 365 hybrid identity model, you have more verification options.</span></span> <span data-ttu-id="b5abd-157">더 강력한 보조 인증 방법으로 보안 인프라가 이미 마련 되어 있는 경우 다음 단계를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-157">If you have the security infrastructure already in place for a stronger secondary authentication method, use these steps:</span></span>
  
1. <span data-ttu-id="b5abd-158">[MFA를 사용 하도록 설정](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6)합니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-158">[Enable MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).</span></span>
    
2. <span data-ttu-id="b5abd-159">[Office 365에 대 한 2 단계 인증을 설정](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) 하 여 적절 한 확인 방법에 대해 각 전용 전역 관리자 계정을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-159">[Set up 2-step verification for Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) to configure each dedicated global administrator account for the appropriate verification method.</span></span> 
    
<span data-ttu-id="b5abd-160">원하는 보다 강력한 확인 방법의 보안 인프라가 제대로 작동 하지 않고 Office 365 MFA에 적합 하지 않은 경우 전화 통화 또는 문자 메시지를 사용 하 여 MFA로 전용 전역 관리자 계정을 구성 하는 것이 좋습니다. 중간 보안 조치로 전역 관리자 계정의 스마트 전화로 전송 되는 확인 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-160">If the security infrastructure for the desired stronger verification method is not in place and functioning for Office 365 MFA, we strongly recommend that you configure dedicated global administrator accounts with MFA using a phone call or a text message verification code sent to a smart phone for your global administrator accounts as an interim security measure.</span></span> <span data-ttu-id="b5abd-161">MFA에서 제공 하는 추가 보호를 사용 하지 않고 전용 전역 관리자 계정을 그대로 사용 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="b5abd-161">Do not leave your dedicated global administrator accounts without the additional protection provided by MFA.</span></span>
  
<span data-ttu-id="b5abd-162">자세한 내용은 [Office 365 배포에 대한 다단계 인증 계획](https://support.office.com/article/043807b2-21db-4d5c-b430-c8a6dee0e6ba)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b5abd-162">For more information, see [Plan for multi-factor authentication for Office 365 Deployments](https://support.office.com/article/043807b2-21db-4d5c-b430-c8a6dee0e6ba).</span></span>
  
<span data-ttu-id="b5abd-163">MFA 및 PowerShell을 사용 하 여 Office 365 서비스에 연결 하려면 [이 문서](https://blogs.technet.microsoft.com/solutions_advisory_board/2017/04/27/connect-to-office-365-services-with-multifactor-authentication-mfa-and-powershell/)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b5abd-163">To connect to Office 365 services with MFA and PowerShell, see [this article](https://blogs.technet.microsoft.com/solutions_advisory_board/2017/04/27/connect-to-office-365-services-with-multifactor-authentication-mfa-and-powershell/).</span></span>
  
## <a name="step-3-monitor-for-suspicious-global-administrator-account-activity"></a><span data-ttu-id="b5abd-164">3단계.</span><span class="sxs-lookup"><span data-stu-id="b5abd-164">Step 3.</span></span> <span data-ttu-id="b5abd-165">의심 스러운 전역 관리자 계정 활동에 대 한 모니터링</span><span class="sxs-lookup"><span data-stu-id="b5abd-165">Monitor for suspicious global administrator account activity</span></span>

<span data-ttu-id="b5abd-166">Office 365 Cloud App Security를 사용 하 여 구독에서 의심 스러운 동작을 알리는 정책을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-166">Office 365 Cloud App Security lets you create policies to notify you of suspicious behavior in your subscription.</span></span> <span data-ttu-id="b5abd-167">Cloud App Security는 Office 365 E5에 기본 제공 되지만 별도의 서비스로도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-167">Cloud App Security is built into Office 365 E5, but is also available as a separate service.</span></span> <span data-ttu-id="b5abd-168">예를 들어, Office 365 E5가 없는 경우 전역 관리자, 보안 관리자 및 준수 관리자 역할이 할당 된 사용자 계정에 대해 개별 Cloud App Security 라이선스를 구입할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-168">For example, if you do not have Office 365 E5, you can purchase individual Cloud App Security licenses for the user accounts that are assigned the global administrator, security administrator, and compliance administrator roles.</span></span>
  
<span data-ttu-id="b5abd-169">Office 365 구독에 Cloud App Security가 있는 경우 다음 단계를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-169">If you have Cloud App Security in your Office 365 subscription, use these steps:</span></span>
  
1. <span data-ttu-id="b5abd-170">보안 관리자 또는 준수 관리자 역할이 할당 된 계정으로 Microsoft 365 관리 센터에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-170">Sign into the Microsoft 365 admin center with an account that is assigned the Security Administrator or Compliance Administrator role.</span></span>
    
2. <span data-ttu-id="b5abd-171">[Office 365 Cloud App Security를 설정](https://support.office.com/article/ba919c73-d021-404d-9850-eec57e78678c)합니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-171">[Turn on Office 365 Cloud App Security](https://support.office.com/article/ba919c73-d021-404d-9850-eec57e78678c).</span></span>
    
3. <span data-ttu-id="b5abd-172">[Office 365 Cloud App Security에서 변칙 검색 정책을](https://support.office.com/article/88935b4e-dcb1-47f1-8aca-1bf8fb069db6) 검토 하 여 권한이 있는 관리 활동의 비정상 패턴을 전자 메일로 알려 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-172">Review your [Anomaly detection policies in Office 365 Cloud App Security](https://support.office.com/article/88935b4e-dcb1-47f1-8aca-1bf8fb069db6) to notify you by email of anomalous patterns of privileged administrative activity.</span></span> 
    
<span data-ttu-id="b5abd-173">사용자 계정을 보안 관리자 역할에 추가 하려면 전용 전역 관리자 계정 및 MFA를 사용 하 여 [Office 365 PowerShell에 연결](https://technet.microsoft.com/library/dn975125.aspx#step3) 하 고 사용자 계정의 사용자 계정 이름을 입력 한 후 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-173">To add a user account to the Security Administrator role, [connect to Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx#step3) with a dedicated global administrator account and MFA, fill in the user principal name of the user account, and then run these commands:</span></span> 
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upn -RoleName "Security Administrator"
```

<span data-ttu-id="b5abd-174">준수 관리자 역할에 사용자 계정을 추가 하려면 사용자 계정의 사용자 계정 이름을 입력 하 고 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-174">To add a user account to the Compliance Administrator role, fill in the user principal name of the user account, and then run these commands:</span></span>
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress  $upn -RoleName "Compliance Administrator"
```

## <a name="additional-protections-for-enterprise-organizations"></a><span data-ttu-id="b5abd-175">엔터프라이즈 조직에 대 한 추가 보호</span><span class="sxs-lookup"><span data-stu-id="b5abd-175">Additional protections for enterprise organizations</span></span>

<span data-ttu-id="b5abd-176">1-3 단계를 수행한 후에는 이러한 추가 방법을 사용 하 여 전역 관리자 계정 및이 계정을 사용 하 여 수행 하는 구성이 최대한 안전한 지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-176">After steps 1-3, use these additional methods to ensure that your global administrator account, and the configuration that you perform using it, are as secure as possible.</span></span>
  
### <a name="privileged-access-workstation-paw"></a><span data-ttu-id="b5abd-177">발 없는 (권한이 부여 된 액세스 워크스테이션)</span><span class="sxs-lookup"><span data-stu-id="b5abd-177">Privileged Access Workstation (PAW)</span></span>

<span data-ttu-id="b5abd-178">높은 권한의 작업 실행이 최대한 안전한 지 확인 하려면 발 없는를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-178">To ensure that the execution of highly privileged tasks is as secure as possible, use a PAW.</span></span> <span data-ttu-id="b5abd-179">발 없는는 전역 관리자 계정이 필요한 Office 365 구성 같은 중요 한 구성 작업에만 사용 되는 전용 컴퓨터입니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-179">A PAW is a dedicated computer that is only used for sensitive configuration tasks, such as Office 365 configuration that requires a global administrator account.</span></span> <span data-ttu-id="b5abd-180">이 컴퓨터는 인터넷 브라우징이 나 전자 메일에 대해 매일 사용 되지 않으므로 인터넷 공격 및 위협 으로부터 보호 되는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-180">Because this computer is not used daily for Internet browsing or email, it is better protected from Internet attacks and threats.</span></span>
  
<span data-ttu-id="b5abd-181">발 없는를 설정 하는 방법에 대 한 자세한 내용은 [http://aka.ms/cyberpaw](http://aka.ms/cyberpaw)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b5abd-181">For instructions on how to set up a PAW, see [http://aka.ms/cyberpaw](http://aka.ms/cyberpaw).</span></span>
  
### <a name="azure-ad-privileged-identity-management-pim"></a><span data-ttu-id="b5abd-182">Azure AD PIM (권한 부여 Id 관리)</span><span class="sxs-lookup"><span data-stu-id="b5abd-182">Azure AD Privileged Identity Management (PIM)</span></span>

<span data-ttu-id="b5abd-183">전역 관리자 계정을 전역 관리자 역할에 영구적으로 할당 하는 대신 Azure AD PIM을 사용 하 여 필요에 따라 전역 관리자 역할을 주문형으로 할당 하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-183">Rather than having your global administrator accounts be permanently assigned the global administrator role, you can use Azure AD PIM to enable on-demand, just-in-time assignment of the global administrator role when it is needed.</span></span>
  
<span data-ttu-id="b5abd-184">전역 관리자 계정 대신 영구 관리자가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-184">Instead of your global administrator accounts being a permanent admin, they become eligible administrators.</span></span> <span data-ttu-id="b5abd-185">전역 관리자 역할은 사용자가 필요한 경우에만 비활성화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-185">The global administrator role is inactive until someone needs it.</span></span> <span data-ttu-id="b5abd-186">그런 다음 정품 인증 프로세스를 완료 하 여 전역 관리자 계정에 미리 정의 된 시간에 대 한 역할을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-186">You then complete an activation process to add the global administrator role to the global administrator account for a predetermined amount of time.</span></span> <span data-ttu-id="b5abd-187">시간이 만료 되 면 PIM은 전역 관리자 계정에서 전역 관리자 역할을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-187">When the time expires, PIM removes the global administrator role from the global administrator account.</span></span>
  
<span data-ttu-id="b5abd-188">PIM 및이 프로세스를 사용 하면 악의적인 사용자가 공격 하 고 사용할 수 있는 전역 관리자 계정의 시간이 크게 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-188">Using PIM and this process significantly reduces the amount of time that your global administrator accounts are vulnerable to attack and use by malicious users.</span></span>
  
<span data-ttu-id="b5abd-189">자세한 내용은 [Configure AZURE AD 권한이 있는 Id 관리](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b5abd-189">For more information, see [Configure Azure AD Privileged Identity Management](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure).</span></span>
  
> [!NOTE]
> <span data-ttu-id="b5abd-190">PIM은 EMS (Enterprise Mobility + Security) E5에 포함 되어 있는 Azure Active Directory Premium P2와 함께 사용할 수 있거나, 전역 관리자 계정에 대 한 개별 라이선스를 구입할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-190">PIM is available with Azure Active Directory Premium P2, which is included with Enterprise Mobility + Security (EMS) E5, or you can purchase individual licenses for your global administrator accounts.</span></span> 
  
### <a name="security-information-and-event-management-siem-software-for-office-365-logging"></a><span data-ttu-id="b5abd-191">Office 365 용 SIEM (보안 정보 및 이벤트 관리) 소프트웨어</span><span class="sxs-lookup"><span data-stu-id="b5abd-191">Security information and event management (SIEM) software for Office 365 logging</span></span>

<span data-ttu-id="b5abd-192">SIEM 소프트웨어 서버에서 실행 되는 응용 프로그램 및 네트워크 하드웨어에 의해 생성 되는 이벤트에 대 한 실시간 분석을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-192">SIEM software run on a server performs real-time analysis of security alerts and events created by applications and network hardware.</span></span> <span data-ttu-id="b5abd-193">SIEM 서버에서 분석 및 보고 기능에 Office 365 보안 경고 및 이벤트를 포함 하도록 허용 하려면 SIEM 시스템에서이를 통합 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5abd-193">To allow your SIEM server to include Office 365 security alerts and events in its analysis and reporting functions, integrate these in your SIEM system:</span></span>
  
- <span data-ttu-id="b5abd-194">Azure AD</span><span class="sxs-lookup"><span data-stu-id="b5abd-194">Azure AD</span></span>
    
    <span data-ttu-id="b5abd-195">자세한 내용은 [Azure 리소스의 로그를 SIEM 시스템에 통합](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b5abd-195">For more information, see [Integrate logs from Azure resources into your SIEM systems](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview).</span></span>
    
- <span data-ttu-id="b5abd-196">Office 365 Cloud App Security</span><span class="sxs-lookup"><span data-stu-id="b5abd-196">Office 365 Cloud App Security</span></span>
    
    <span data-ttu-id="b5abd-197">자세한 내용은 [SIEM server를 Office 365 Cloud App Security와 통합](https://support.office.com/article/dd6d2417-49c4-4de6-9294-67fdabbf8532)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b5abd-197">For more information, see [Integrate your SIEM server with Office 365 Cloud App Security](https://support.office.com/article/dd6d2417-49c4-4de6-9294-67fdabbf8532).</span></span>
    
## <a name="next-step"></a><span data-ttu-id="b5abd-198">다음 단계</span><span class="sxs-lookup"><span data-stu-id="b5abd-198">Next step</span></span>

<span data-ttu-id="b5abd-199">[Office 365에 대 한 보안 모범 사례를](https://support.office.com/article/9295e396-e53d-49b9-ae9b-0b5828cdedc3)참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b5abd-199">See [Security best practices for Office 365](https://support.office.com/article/9295e396-e53d-49b9-ae9b-0b5828cdedc3).</span></span>
  

