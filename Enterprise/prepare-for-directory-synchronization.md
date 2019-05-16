---
title: 디렉터리 동기화를 통해 사용자를 Office 365에 프로비전하기 위한 준비
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: 디렉터리 동기화 및이 방법을 사용할 경우의 장기적인 이점을 사용 하 여 사용자를 Office 365에 프로 비전 하도록 준비 하는 방법에 대해 설명 합니다.
ms.openlocfilehash: 0b2fe552911797337541bd25f0efcb81eab303bf
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34071034"
---
# <a name="prepare-to-provision-users-through-directory-synchronization-to-office-365"></a><span data-ttu-id="19f04-103">디렉터리 동기화를 통해 사용자를 Office 365에 프로비전하기 위한 준비</span><span class="sxs-lookup"><span data-stu-id="19f04-103">Prepare to provision users through directory synchronization to Office 365</span></span>

<span data-ttu-id="19f04-104">디렉터리 동기화를 사용 하 여 사용자를 프로 비전 하려면 Office 365에서 단순히 회사 또는 학교 계정을 관리 하는 것 보다 더 많은 계획 및 준비 작업이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-104">Provisioning users with directory synchronization requires more planning and preparation than simply managing your work or school account directly in Office 365.</span></span> <span data-ttu-id="19f04-105">추가 계획 및 준비 작업은 온-프레미스 Active Directory가 Azure Active Directory에 올바르게 동기화 되도록 하기 위해 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-105">The additional planning and preparation tasks are required to ensure that your on-premises Active Directory synchronizes properly to Azure Active Directory.</span></span> <span data-ttu-id="19f04-106">조직에 추가 된 이점은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-106">The added benefits to your organization include:</span></span>
  
- <span data-ttu-id="19f04-107">조직의 관리 프로그램 감소</span><span class="sxs-lookup"><span data-stu-id="19f04-107">Reducing the administrative programs in your organization</span></span>
- <span data-ttu-id="19f04-108">선택적으로 single sign-on 시나리오를 사용 하도록 설정</span><span class="sxs-lookup"><span data-stu-id="19f04-108">Optionally enabling single sign-on scenario</span></span>
- <span data-ttu-id="19f04-109">Office 365에서 계정 변경 자동화</span><span class="sxs-lookup"><span data-stu-id="19f04-109">Automating account changes in Office 365</span></span>
    
<span data-ttu-id="19f04-110">디렉터리 동기화를 사용할 때의 이점에 대 한 자세한 내용은 [디렉터리 동기화 로드맵]( https://go.microsoft.com/fwlink/p/?LinkId=525398) 및 [Office 365 Id 및 Azure Active directory 이해](about-office-365-identity.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="19f04-110">For more information about the advantages of using directory synchronization, see [Directory synchronization roadmap]( https://go.microsoft.com/fwlink/p/?LinkId=525398) and [Understanding Office 365 Identity and Azure Active Directory](about-office-365-identity.md).</span></span>
  
<span data-ttu-id="19f04-111">조직에 가장 적합 한 시나리오를 확인 하려면 [디렉터리 통합 도구 비교](https://go.microsoft.com/fwlink/p/?LinkId=525320)를 검토 합니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-111">To determine which scenario is the best for your organization, review the [directory integration tools comparison](https://go.microsoft.com/fwlink/p/?LinkId=525320).</span></span>
  
## <a name="directory-cleanup-tasks"></a><span data-ttu-id="19f04-112">디렉터리 정리 작업</span><span class="sxs-lookup"><span data-stu-id="19f04-112">Directory cleanup tasks</span></span>

<span data-ttu-id="19f04-113">디렉터리 동기화를 시작 하기 전에 디렉터리를 정리 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-113">Before you begin synchronizing your directory, you need to clean up your directory.</span></span>
  
<span data-ttu-id="19f04-114">[AZURE AD Connect에 의해 Azure Active Directory와 동기화 되는 특성도](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-sync-attributes-synchronized)검토 합니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-114">Review also the [attributes synchronized to Azure Active Directory by Azure AD Connect](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-sync-attributes-synchronized).</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="19f04-115">동기화 하기 전에 디렉터리 정리를 수행 하지 않으면 배포 프로세스에 큰 부정적인 영향을 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-115">If you don't perform directory cleanup before you synchronize, there can be a significant negative effect on the deployment process.</span></span> <span data-ttu-id="19f04-116">디렉터리 동기화 주기, 오류 식별 및 다시 동기화를 진행 하는 데 며칠 또는 몇 주가 소요 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-116">It might take days, or even weeks, to go through the cycle of directory synchronization, identifying errors, and re-synchronization.</span></span> 
  
<span data-ttu-id="19f04-117">온-프레미스 디렉터리에서 다음과 같은 정리 작업을 완료 합니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-117">In your on-premises directory, complete the following clean-up tasks:</span></span>
  
1. <span data-ttu-id="19f04-118">Office 365 서비스 제품을 할당할 각 사용자에 게 **proxyAddresses** 특성의 유효한 전자 메일 주소와 고유한 주소가 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-118">Ensure that each user who will be assigned Office 365 service offerings has a valid and unique email address in the **proxyAddresses** attribute.</span></span> 
    
2. <span data-ttu-id="19f04-119">**ProxyAddresses** 특성에서 중복 된 값을 모두 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-119">Remove any duplicate values in the **proxyAddresses** attribute.</span></span> 
    
3.  <span data-ttu-id="19f04-120">가능한 경우 Office 365 서비스 제품을 할당할 각 사용자에 게 사용자의 **user** 개체에 있는 **userPrincipalName** 특성에 대 한 유효한 값과 고유 설정값이 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-120">If possible, ensure that each user who will be assigned Office 365 service offerings has a valid and unique value for the **userPrincipalName** attribute in the user's **user** object.</span></span> <span data-ttu-id="19f04-121">최상의 동기화 환경을 위해 온-프레미스 Active Directory UPN이 클라우드 UPN과 일치 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-121">For best synchronization experience, ensure that the on-premises Active Directory UPN matches the cloud UPN.</span></span> <span data-ttu-id="19f04-122">사용자에 게 **userPrincipalName** 특성에 대 한 값이 없는 경우에는 **사용자** 개체에 **sAMAccountName** 특성에 대 한 유효한 값과 고유 정보가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-122">If a user does not have a value for the **userPrincipalName** attribute, then the **user** object must contain a valid and unique value for the **sAMAccountName** attribute.</span></span> <span data-ttu-id="19f04-123">**UserPrincipalName** 특성에서 중복 된 값을 모두 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-123">Remove any duplicate values in the **userPrincipalName** attribute.</span></span> 
    
4. <span data-ttu-id="19f04-124">전체 주소 목록 (GAL)을 최적의 상태로 사용 하려면 다음 특성의 정보가 올바른지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-124">For optimal use of the global address list (GAL), be sure the information in the following attributes is correct:</span></span>
    
  - <span data-ttu-id="19f04-125">givenName</span><span class="sxs-lookup"><span data-stu-id="19f04-125">givenName</span></span>
  - <span data-ttu-id="19f04-126">성</span><span class="sxs-lookup"><span data-stu-id="19f04-126">surname</span></span>
  - <span data-ttu-id="19f04-127">n</span><span class="sxs-lookup"><span data-stu-id="19f04-127">displayName</span></span>
  - <span data-ttu-id="19f04-128">직함</span><span class="sxs-lookup"><span data-stu-id="19f04-128">Job Title</span></span>
  - <span data-ttu-id="19f04-129">부서</span><span class="sxs-lookup"><span data-stu-id="19f04-129">Department</span></span>
  - <span data-ttu-id="19f04-130">사무실</span><span class="sxs-lookup"><span data-stu-id="19f04-130">Office</span></span>
  - <span data-ttu-id="19f04-131">사무실 전화</span><span class="sxs-lookup"><span data-stu-id="19f04-131">Office Phone</span></span>
  - <span data-ttu-id="19f04-132">휴대폰 번호</span><span class="sxs-lookup"><span data-stu-id="19f04-132">Mobile Phone</span></span>
  - <span data-ttu-id="19f04-133">팩스 번호</span><span class="sxs-lookup"><span data-stu-id="19f04-133">Fax Number</span></span>
  - <span data-ttu-id="19f04-134">주소</span><span class="sxs-lookup"><span data-stu-id="19f04-134">Street Address</span></span>
  - <span data-ttu-id="19f04-135">구/군/시</span><span class="sxs-lookup"><span data-stu-id="19f04-135">City</span></span>
  - <span data-ttu-id="19f04-136">시/도</span><span class="sxs-lookup"><span data-stu-id="19f04-136">State or Province</span></span>
  - <span data-ttu-id="19f04-137">우편 번호</span><span class="sxs-lookup"><span data-stu-id="19f04-137">Zip or Postal Code</span></span>
  - <span data-ttu-id="19f04-138">국가</span><span class="sxs-lookup"><span data-stu-id="19f04-138">Country or Region</span></span>
    
## <a name="directory-object-and-attribute-preparation"></a><span data-ttu-id="19f04-139">디렉터리 개체 및 특성 준비</span><span class="sxs-lookup"><span data-stu-id="19f04-139">Directory object and attribute preparation</span></span>

<span data-ttu-id="19f04-140">온-프레미스 디렉터리와 Office 365 간의 디렉터리 동기화를 성공적으로 수행 하려면 온-프레미스 디렉터리 특성이 적절 하 게 준비 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-140">Successful directory synchronization between your on-premises directory and Office 365 requires that your on-premises directory attributes are properly prepared.</span></span> <span data-ttu-id="19f04-141">예를 들어 Office 365 환경과 동기화 되는 특정 특성에 특정 문자가 사용 되지 않는지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-141">For example, you need to ensure that specific characters aren't used in certain attributes that are synchronized with the Office 365 environment.</span></span> <span data-ttu-id="19f04-142">예기치 않은 문자로 인해 디렉터리 동기화가 실패 하는 것은 아니지만 경고를 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-142">Unexpected characters do not cause directory synchronization to fail but might return a warning.</span></span> <span data-ttu-id="19f04-143">잘못 된 문자가 있으면 디렉터리 동기화가 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-143">Invalid characters will cause directory synchronization to fail.</span></span>
  
<span data-ttu-id="19f04-144">Active Directory 사용자 중 일부에 중복 된 특성이 하나 이상 있으면 디렉터리 동기화도 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-144">Directory synchronization will also fail if some of your Active Directory users have one or more duplicate attributes.</span></span> <span data-ttu-id="19f04-145">각 사용자에 게는 고유한 특성이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-145">Each user must have unique attributes.</span></span>
  
<span data-ttu-id="19f04-146">준비 해야 하는 특성은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-146">The attributes that you need to prepare are listed here:</span></span>
  
 <span data-ttu-id="19f04-147">**참고:** 또한 [Idfix 도구](install-and-run-idfix.md) 를 사용 하 여이 프로세스를 훨씬 더 쉽게 진행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-147">**NOTE:** You can also use the [IdFix tool](install-and-run-idfix.md) to make this process a lot easier.</span></span> 
  
- <span data-ttu-id="19f04-148">**n**</span><span class="sxs-lookup"><span data-stu-id="19f04-148">**displayName**</span></span>
    
  - <span data-ttu-id="19f04-149">사용자 개체에 특성이 있으면 Office 365와 동기화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-149">If the attribute exists in the user object, it will be synchronized with Office 365.</span></span>
  - <span data-ttu-id="19f04-150">이 특성이 사용자 개체에 있는 경우에는 해당 특성에 대 한 값이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-150">If this attribute exists in the user object, there must be a value for it.</span></span> <span data-ttu-id="19f04-151">즉, 특성을 비워 두면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-151">That is, the attribute must not be blank.</span></span>
  - <span data-ttu-id="19f04-152">최대 문자 수: 256</span><span class="sxs-lookup"><span data-stu-id="19f04-152">Maximum number of characters: 256</span></span>
    
- <span data-ttu-id="19f04-153">**givenName**</span><span class="sxs-lookup"><span data-stu-id="19f04-153">**givenName**</span></span>
    
  - <span data-ttu-id="19f04-154">사용자 개체에 특성이 있으면 Office 365와 동기화 되지만 Office 365에서는이 특성을 사용할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-154">If the attribute exists in the user object, it will be synchronized with Office 365, but Office 365 does not require or use it.</span></span>
  - <span data-ttu-id="19f04-155">최대 문자 수: 64</span><span class="sxs-lookup"><span data-stu-id="19f04-155">Maximum number of characters: 64</span></span>
    
- <span data-ttu-id="19f04-156">**메일**</span><span class="sxs-lookup"><span data-stu-id="19f04-156">**mail**</span></span>
    
  - <span data-ttu-id="19f04-157">특성 값은 디렉터리 내에서 고유 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-157">The attribute value must be unique within the directory.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="19f04-158">중복 된 값이 있는 경우 값이 있는 첫 번째 사용자가 동기화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-158">If there are duplicate values, the first user with the value is synchronized.</span></span> <span data-ttu-id="19f04-159">이후 사용자는 Office 365에 나타나지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-159">Subsequent users will not appear in Office 365.</span></span> <span data-ttu-id="19f04-160">두 사용자가 Office 365에 표시 되도록 하려면 Office 365의 값을 수정 하거나 온-프레미스 디렉터리의 두 값을 모두 수정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-160">You must modify either the value in Office 365, or modify both of the values in the on-premises directory in order for both users to appear in Office 365.</span></span> 
  
- <span data-ttu-id="19f04-161">**mailNickname** (Exchange 별칭)</span><span class="sxs-lookup"><span data-stu-id="19f04-161">**mailNickname** (Exchange alias)</span></span> 
    
  - <span data-ttu-id="19f04-162">특성 값은 마침표 (.)로 시작할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-162">The attribute value cannot begin with a period (.).</span></span>
  - <span data-ttu-id="19f04-163">특성 값은 디렉터리 내에서 고유 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-163">The attribute value must be unique within the directory.</span></span>
    
- <span data-ttu-id="19f04-164">**proxyAddresses**</span><span class="sxs-lookup"><span data-stu-id="19f04-164">**proxyAddresses**</span></span>
    
  - <span data-ttu-id="19f04-165">여러 값 특성</span><span class="sxs-lookup"><span data-stu-id="19f04-165">Multiple-value attribute</span></span>
  - <span data-ttu-id="19f04-166">값 당 최대 문자 수: 256</span><span class="sxs-lookup"><span data-stu-id="19f04-166">Maximum number of characters per value: 256</span></span>
  - <span data-ttu-id="19f04-167">특성 값에는 공백이 없어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-167">The attribute value must not contain a space.</span></span>
  - <span data-ttu-id="19f04-168">특성 값은 디렉터리 내에서 고유 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-168">The attribute value must be unique within the directory.</span></span>
  - <span data-ttu-id="19f04-169">유효 하지 않은 \< \> 문자: (); , [ ] "</span><span class="sxs-lookup"><span data-stu-id="19f04-169">Invalid characters: \< \> ( ) ; , [ ] "</span></span>
    
    <span data-ttu-id="19f04-170">잘못 된 문자는 형식 구분 기호 뒤에 있는 문자에 적용 되 고, SMTP:User@contso.com는 허용 되지만 SMTP:user:M@contoso.com는 그렇지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-170">Note that the invalid characters apply to the characters following the type delimiter and ":", such that SMTP:User@contso.com is allowed, but SMTP:user:M@contoso.com is not.</span></span>
    
    > [!IMPORTANT]
    > <span data-ttu-id="19f04-171">모든 SMTP (Simple Mail Transport Protocol) 주소는 전자 메일 메시징 표준을 준수 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-171">All Simple Mail Transport Protocol (SMTP) addresses should comply with email messaging standards.</span></span> <span data-ttu-id="19f04-172">중복 또는 원치 않는 주소가 있으면 [Exchange에서 중복 및 원하지 않는 프록시 주소 제거](https://go.microsoft.com/fwlink/?LinkId=293860)도움말 항목을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="19f04-172">If duplicate or unwanted addresses exist, see the Help topic [Removing duplicate and unwanted proxy addresses in Exchange](https://go.microsoft.com/fwlink/?LinkId=293860).</span></span> 
  
- <span data-ttu-id="19f04-173">**sAMAccountName**</span><span class="sxs-lookup"><span data-stu-id="19f04-173">**sAMAccountName**</span></span>
    
  - <span data-ttu-id="19f04-174">최대 문자 수: 20</span><span class="sxs-lookup"><span data-stu-id="19f04-174">Maximum number of characters: 20</span></span>
  - <span data-ttu-id="19f04-175">특성 값은 디렉터리 내에서 고유 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-175">The attribute value must be unique within the directory.</span></span>
  - <span data-ttu-id="19f04-176">유효 하지 않은 문자: [\ "|, \< \> /: + =;?</span><span class="sxs-lookup"><span data-stu-id="19f04-176">Invalid characters: [ \ " | , / : \< \> + = ; ?</span></span> <span data-ttu-id="19f04-177">\* ]</span><span class="sxs-lookup"><span data-stu-id="19f04-177"></span></span>
  - <span data-ttu-id="19f04-178">사용자의 **sAMAccountName** 특성이 유효 하지 않지만 **UserPrincipalName** 특성이 유효한 경우 사용자 계정이 Office 365에서 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-178">If a user has an invalid **sAMAccountName** attribute but has a valid **userPrincipalName** attribute, the user account is created in Office 365.</span></span> 
  - <span data-ttu-id="19f04-179">**SAMAccountName** 및 **userPrincipalName** 이 둘 다 유효 하지 않은 경우 온-프레미스 Active Directory **userPrincipalName** 특성을 업데이트 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-179">If both **sAMAccountName** and **userPrincipalName** are invalid, the on-premises Active Directory **userPrincipalName** attribute must be updated.</span></span> 
    
- <span data-ttu-id="19f04-180">**sn** 성</span><span class="sxs-lookup"><span data-stu-id="19f04-180">**sn** (surname)</span></span> 
    
  - <span data-ttu-id="19f04-181">사용자 개체에 특성이 있으면 Office 365와 동기화 되지만 Office 365에서는이 특성을 사용할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-181">If the attribute exists in the user object, it will be synchronized with Office 365, but Office 365 does not require or use it.</span></span>
    
- <span data-ttu-id="19f04-182">**targetAddress**</span><span class="sxs-lookup"><span data-stu-id="19f04-182">**targetAddress**</span></span>
    
    <span data-ttu-id="19f04-183">사용자에 대해 채워지는 **targetAddress** 특성 (예: SMTP:tom@contoso.com)이 OFFICE 365 GAL에 나타나야 합니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-183">It's required that the **targetAddress** attribute (for example, SMTP:tom@contoso.com) that's populated for the user must appear in the Office 365 GAL.</span></span> <span data-ttu-id="19f04-184">타사 메시징 마이그레이션 시나리오에서이를 위해서는 온-프레미스 디렉터리에 대 한 Office 365 스키마 확장이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-184">In third-party messaging migration scenarios, this would require the Office 365 schema extension for the on-premises directory.</span></span> <span data-ttu-id="19f04-185">또한 Office 365 스키마 확장은 온-프레미스 디렉터리에서 디렉터리 동기화 도구를 사용 하 여 채워지는 Office 365 개체를 관리 하는 데 유용한 다른 특성도 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-185">The Office 365 schema extension would also add other useful attributes to manage Office 365 objects that are populated by using a directory synchronization tool from on-premises directory.</span></span> <span data-ttu-id="19f04-186">예를 들어, 숨겨진 사서함 또는 메일 그룹을 관리 하기 위한 **msExchHideFromAddressLists** 특성이 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-186">For example, the **msExchHideFromAddressLists** attribute to manage hidden mailboxes or distribution groups would be added.</span></span> 
   
  - <span data-ttu-id="19f04-187">최대 문자 수: 256</span><span class="sxs-lookup"><span data-stu-id="19f04-187">Maximum number of characters: 256</span></span>
  - <span data-ttu-id="19f04-188">특성 값에는 공백이 없어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-188">The attribute value must not contain a space.</span></span>
  - <span data-ttu-id="19f04-189">특성 값은 디렉터리 내에서 고유 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-189">The attribute value must be unique within the directory.</span></span>
  - <span data-ttu-id="19f04-190">유효 하지 않은 문자 \< \> : \ (); , [ ] "</span><span class="sxs-lookup"><span data-stu-id="19f04-190">Invalid characters: \ \< \> ( ) ; , [ ] "</span></span>
  - <span data-ttu-id="19f04-191">모든 SMTP (Simple Mail Transport Protocol) 주소는 전자 메일 메시징 표준을 준수 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-191">All Simple Mail Transport Protocol (SMTP) addresses should comply with email messaging standards.</span></span>
    
- <span data-ttu-id="19f04-192">**userPrincipalName**</span><span class="sxs-lookup"><span data-stu-id="19f04-192">**userPrincipalName**</span></span>
    
  - <span data-ttu-id="19f04-193">**UserPrincipalName** 특성은 사용자 이름 뒤에 @ 기호와 도메인 이름 (예: user@contoso.com)이 오는 인터넷 스타일 로그인 형식 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-193">The **userPrincipalName** attribute must be in the Internet-style sign-in format where the user name is followed by the at sign (@) and a domain name: for example, user@contoso.com.</span></span> <span data-ttu-id="19f04-194">모든 SMTP (Simple Mail Transport Protocol) 주소는 전자 메일 메시징 표준을 준수 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-194">All Simple Mail Transport Protocol (SMTP) addresses should comply with email messaging standards.</span></span>
  - <span data-ttu-id="19f04-195">**UserPrincipalName** 특성의 최대 문자 수는 113입니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-195">The maximum number of characters for the **userPrincipalName** attribute is 113.</span></span> <span data-ttu-id="19f04-196">다음과 같이 @ 기호 앞 이나 뒤에 특정 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-196">A specific number of characters are permitted before and after the at sign (@), as follows:</span></span> 
  - <span data-ttu-id="19f04-197">@ 기호 앞에 있는 사용자 이름의 최대 문자 수: 64</span><span class="sxs-lookup"><span data-stu-id="19f04-197">Maximum number of characters for the user name that is in front of the at sign (@): 64</span></span>
  - <span data-ttu-id="19f04-198">@ 기호 뒤에 있는 도메인 이름의 최대 문자 수: 48</span><span class="sxs-lookup"><span data-stu-id="19f04-198">Maximum number of characters for the domain name following the at sign (@): 48</span></span>
  - <span data-ttu-id="19f04-199">유효 하지 않은 문자: &amp; \* \% +/=?</span><span class="sxs-lookup"><span data-stu-id="19f04-199">Invalid characters: \ % &amp; \* + / = ?</span></span> <span data-ttu-id="19f04-200">{ } | \< \> ( ) ; : , [ ] "</span><span class="sxs-lookup"><span data-stu-id="19f04-200"></span></span>
  - <span data-ttu-id="19f04-201">움라우트도 잘못 된 문자입니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-201">An umlaut is also an invalid character.</span></span>
  - <span data-ttu-id="19f04-202">@ 문자는 각 **userPrincipalName** 값에 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-202">The @ character is required in each **userPrincipalName** value.</span></span> 
  - <span data-ttu-id="19f04-203">@ 문자는 각 **userPrincipalName** 값의 첫 번째 문자일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-203">The @ character cannot be the first character in each **userPrincipalName** value.</span></span> 
  - <span data-ttu-id="19f04-204">사용자 이름은 마침표 (.), 앰퍼샌드 (&amp;), 공백 또는 @ 기호로 끝날 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-204">The user name cannot end with a period (.), an ampersand (&amp;), a space, or an at sign (@).</span></span>
  - <span data-ttu-id="19f04-205">사용자 이름에는 공백을 포함할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-205">The user name cannot contain any spaces.</span></span>
  - <span data-ttu-id="19f04-206">라우팅 가능한 도메인을 사용 해야 합니다. 예를 들어 로컬 또는 내부 도메인은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-206">Routable domains must be used; for example, local or internal domains cannot be used.</span></span>
  - <span data-ttu-id="19f04-207">유니코드는 밑줄 문자로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-207">Unicode is converted to underscore characters.</span></span>
  - <span data-ttu-id="19f04-208">**userPrincipalName** 는 디렉터리에 중복 된 값을 포함할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-208">**userPrincipalName** cannot contain any duplicate values in the directory.</span></span> 
    
## <a name="prepare-the-userprincipalname-attribute"></a><span data-ttu-id="19f04-209">UserPrincipalName 특성 준비</span><span class="sxs-lookup"><span data-stu-id="19f04-209">Prepare the userPrincipalName attribute</span></span>

<span data-ttu-id="19f04-210">Active Directory는 조직의 최종 사용자가 **sAMAccountName** 또는 **userPrincipalName**를 사용 하 여 디렉터리에 로그인 할 수 있도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-210">Active Directory is designed to allow the end users in your organization to sign in to your directory by using either **sAMAccountName** or **userPrincipalName**.</span></span> <span data-ttu-id="19f04-211">마찬가지로 최종 사용자는 회사 또는 학교 계정의 UPN (사용자 계정 이름)을 사용 하 여 Office 365에 로그인 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-211">Similarly, end users can sign in to Office 365 by using the user principal name (UPN) of their work or school account.</span></span> <span data-ttu-id="19f04-212">디렉터리 동기화에서는 온-프레미스 디렉터리에 있는 것과 동일한 UPN을 사용 하 여 Azure Active Directory에 새 사용자를 만들려고 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-212">Directory synchronization attempts to create new users in Azure Active Directory by using the same UPN that's in your on-premises directory.</span></span> <span data-ttu-id="19f04-213">UPN은 전자 메일 주소와 같은 형식으로 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-213">The UPN is formatted like an email address.</span></span> 

<span data-ttu-id="19f04-214">Office 365에서 UPN은 전자 메일 주소를 생성 하는 데 사용 되는 기본 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-214">In Office 365, the UPN is the default attribute that's used to generate the email address.</span></span> <span data-ttu-id="19f04-215">**UserPrincipalName** (온-프레미스 및 Azure Active Directory) 및 **proxyAddresses** 의 기본 전자 메일 주소를 다른 값으로 설정 하는 것이 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-215">It's easy to get **userPrincipalName** (on-premises and in Azure Active Directory) and the primary email address in **proxyAddresses** set to different values.</span></span> <span data-ttu-id="19f04-216">서로 다른 값으로 설정 하면 관리자와 최종 사용자에 게 혼동이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-216">When they are set to different values, there can be confusion for administrators and end users.</span></span> 
  
<span data-ttu-id="19f04-217">혼동을 줄이려면 이러한 특성을 맞추는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-217">It's best to align these attributes to reduce confusion.</span></span> <span data-ttu-id="19f04-218">AD FS (Active Directory Federation Services) 2.0에서 single sign-on 요구 사항을 충족 하려면 Azure Active Directory 및 온-프레미스 Active Directory의 Upn이 일치 하며 유효한 도메인 네임 스페이스를 사용 하 고 있는지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-218">To meet the requirements of single sign-on with Active Directory Federation Services (AD FS) 2.0, you need to ensure that the UPNs in Azure Active Directory and your on-premises Active Directory match and are using a valid domain namespace.</span></span>
  
## <a name="add-an-alternative-upn-suffix-to-ad-ds"></a><span data-ttu-id="19f04-219">AD DS에 대체 UPN 접미사 추가</span><span class="sxs-lookup"><span data-stu-id="19f04-219">Add an alternative UPN suffix to AD DS</span></span>

<span data-ttu-id="19f04-220">사용자의 회사 자격 증명을 Office 365 환경에 연결 하기 위해 대체 UPN 접미사를 추가 해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-220">You may need to add an alternative UPN suffix to associate the user's corporate credentials with the Office 365 environment.</span></span> <span data-ttu-id="19f04-221">UPN 접미사는 UPN에서 @ 문자 오른쪽에 있는 부분입니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-221">A UPN suffix is the part of a UPN to the right of the @ character.</span></span> <span data-ttu-id="19f04-222">Single Sign-On에 사용되는 UPN에는 문자, 숫자, 마침표, 대시 및 밑줄을 포함할 수 있으며 다른 유형의 문자는 포함할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-222">UPNs that are used for single sign-on can contain letters, numbers, periods, dashes, and underscores, but no other types of characters.</span></span>
  
<span data-ttu-id="19f04-223">Active Directory에 대체 UPN 접미사를 추가 하는 방법에 대 한 자세한 내용은 [디렉터리 동기화 준비]( https://go.microsoft.com/fwlink/p/?LinkId=525430)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="19f04-223">For more information on how to add an alternative UPN suffix to Active Directory, see [Prepare for directory synchronization]( https://go.microsoft.com/fwlink/p/?LinkId=525430).</span></span>
  
## <a name="match-the-on-premises-upn-with-the-office-365-upn"></a><span data-ttu-id="19f04-224">온-프레미스 UPN과 Office 365 UPN 일치</span><span class="sxs-lookup"><span data-stu-id="19f04-224">Match the on-premises UPN with the Office 365 UPN</span></span>

<span data-ttu-id="19f04-225">디렉터리 동기화를 이미 설정한 경우 Office 365에 대 한 사용자의 UPN이 온-프레미스 디렉터리 서비스에 정의 된 사용자의 온-프레미스 UPN과 일치 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-225">If you've already set up directory synchronization, the user's UPN for Office 365 may not match the user's on-premises UPN that's defined in your on-premises directory service.</span></span> <span data-ttu-id="19f04-226">도메인이 확인되기 전에 사용자에게 라이선스가 할당된 경우 이와 같은 문제가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-226">This can occur when a user was assigned a license before the domain was verified.</span></span> <span data-ttu-id="19f04-227">이 문제를 해결 하려면 [PowerShell을](https://go.microsoft.com/fwlink/p/?LinkId=396730) 사용 하 여 중복 UPN을 수정 하 여 OFFICE 365 UPN이 회사 사용자 이름 및 도메인과 일치 하도록 사용자의 upn을 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-227">To fix this, use [PowerShell to fix duplicate UPN](https://go.microsoft.com/fwlink/p/?LinkId=396730) to update the user's UPN to ensure that the Office 365 UPN matches the corporate user name and domain.</span></span> <span data-ttu-id="19f04-228">온-프레미스 디렉터리 서비스에서 UPN을 업데이트 하 고 Azure Active Directory id와 동기화 하는 것을 원하는 경우에는 온-프레미스를 변경 하기 전에 Office 365에서 사용자의 라이선스를 제거 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-228">If you are updating the UPN in the on-premises directory service and would like it to synchronize with the Azure Active Directory identity, you need to remove the user's license in Office 365 prior to making the changes on-premises.</span></span> 
  
<span data-ttu-id="19f04-229">[디렉터리 동기화를 위해 라우팅할 수 없는 도메인 (예: 로컬 도메인)을 준비 하는 방법을](prepare-a-non-routable-domain-for-directory-synchronization.md)참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="19f04-229">See also [How to prepare a non-routable domain (such as .local domain) for directory synchronization](prepare-a-non-routable-domain-for-directory-synchronization.md).</span></span>
  
## <a name="directory-integration-tools"></a><span data-ttu-id="19f04-230">디렉터리 통합 도구</span><span class="sxs-lookup"><span data-stu-id="19f04-230">Directory integration tools</span></span>

<span data-ttu-id="19f04-231">디렉터리 동기화는 온-프레미스 Active Directory 환경에서 Office 365 디렉터리 인프라, Azure Active Directory에 대 한 디렉터리 개체 (사용자, 그룹 및 연락처)를 동기화 하는 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-231">Directory synchronization is the synchronization of directory objects (users, groups, and contacts) from your on-premises Active Directory environment to the Office 365 directory infrastructure, Azure Active Directory.</span></span> <span data-ttu-id="19f04-232">사용할 수 있는 도구 및 해당 기능 목록은 [디렉터리 통합 도구](https://go.microsoft.com/fwlink/p/?LinkID=510956) 를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="19f04-232">See [Directory Integration Tools](https://go.microsoft.com/fwlink/p/?LinkID=510956) for a list of the available tools and their functionality.</span></span> <span data-ttu-id="19f04-233">권장 되는 도구는 [Microsoft Azure Active Directory Connect](https://go.microsoft.com/fwlink/p/?LinkID=510956)입니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-233">The recommended tool is [Microsoft Azure Active Directory Connect](https://go.microsoft.com/fwlink/p/?LinkID=510956).</span></span> <span data-ttu-id="19f04-234">Azure Active Directory Connect에 대 한 자세한 내용은 [Azure Active directory를 사용 하 여 온-프레미스 Id 통합](https://go.microsoft.com/fwlink/p/?LinkId=527969)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="19f04-234">For more information about Azure Active Directory Connect, see [Integrating your on-premises identities with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=527969).</span></span>
  
<span data-ttu-id="19f04-235">사용자 계정이 처음에 Office 365 디렉터리와 동기화 되 면 활성화 되지 않은 것으로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-235">When user accounts are synchronized with the Office 365 directory for the first time, they are marked as not activated.</span></span> <span data-ttu-id="19f04-236">전자 메일을 보내거나 받을 수 없으며 구독 라이선스를 사용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-236">They cannot send or receive email, and they don't consume subscription licenses.</span></span> <span data-ttu-id="19f04-237">특정 사용자에 게 Office 365 구독을 할당할 준비가 되 면 [비즈니스용 office 365에서 사용자에 게 라이선스를 할당](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc)하 여 해당 등록을 선택 하 고 활성화 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-237">When you're ready to assign Office 365 subscriptions to specific users, you must select and activate them by [Assign licenses to users in Office 365 for business](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc).</span></span>
  
<span data-ttu-id="19f04-238">또한 [PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=613097) 을 사용 하 여 라이선스를 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19f04-238">You can also use [PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=613097) to assign licenses.</span></span> <span data-ttu-id="19f04-239">PowerShell을 사용 하 여 자동화 된 솔루션의 [Office 365 사용자에 게 라이선스를 자동으로 할당 하는 방법을](https://go.microsoft.com/fwlink/p?LinkID=329805) 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="19f04-239">See [How to Use PowerShell to Automatically Assign Licenses to Your Office 365 Users](https://go.microsoft.com/fwlink/p?LinkID=329805) for an automated solution.</span></span>