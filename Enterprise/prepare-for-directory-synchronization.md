---
title: 디렉터리 동기화를 통해 사용자를 Office 365에 프로비전하기 위한 준비
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
f1_keywords:
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: 이 메서드를 사용 하 여의 장기 이점과 디렉터리 동기화를 사용 하 여 사용자를 Office 365에 프로 비전을 준비 하는 방법에 설명 합니다.
ms.openlocfilehash: 8e84f4602b79ce321cd9a71e6c35331baf40f7f0
ms.sourcegitcommit: c5761d3c41aa2d26815f0d24c73dbcd53ab37957
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/19/2018
ms.locfileid: "27371122"
---
# <a name="prepare-to-provision-users-through-directory-synchronization-to-office-365"></a><span data-ttu-id="dd30b-103">디렉터리 동기화를 통해 사용자를 Office 365에 프로비전하기 위한 준비</span><span class="sxs-lookup"><span data-stu-id="dd30b-103">Prepare to provision users through directory synchronization to Office 365</span></span>

<span data-ttu-id="dd30b-p101">디렉터리 동기화를 통해 사용자를 프로 비전 더 많은 계획 및 준비 단순히 Office 365에서 직접 작업이 나 교육용 계정 관리 보다 필요 합니다. 추가 계획 및 준비 작업은 온-프레미스 Active Directory Azure Active Directory에 올바르게 동기화 보장 하기 위해 필요 합니다. 조직에 추가 된 이점은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="dd30b-p101">Provisioning users with directory synchronization requires more planning and preparation than simply managing your work or school account directly in Office 365. The additional planning and preparation tasks are required to ensure that your on-premises Active Directory synchronizes properly to Azure Active Directory. The added benefits to your organization include:</span></span>
  
- <span data-ttu-id="dd30b-107">조직의 관리 프로그램 감소</span><span class="sxs-lookup"><span data-stu-id="dd30b-107">Reducing the administrative programs in your organization</span></span>
- <span data-ttu-id="dd30b-108">필요에 따라 single sign-on 및 시나리오를 사용 하도록 설정</span><span class="sxs-lookup"><span data-stu-id="dd30b-108">Optionally enabling single sign-on scenario</span></span>
- <span data-ttu-id="dd30b-109">Office 365에서 계정 변경 자동화</span><span class="sxs-lookup"><span data-stu-id="dd30b-109">Automating account changes in Office 365</span></span>
    
<span data-ttu-id="dd30b-110">디렉터리 동기화를 사용 하 여의 장점에 대 한 자세한 내용은 [디렉터리 동기화 로드맵]( https://go.microsoft.com/fwlink/p/?LinkId=525398) 및 [Office 365 Id 이해 및 Azure Active Directory를](about-office-365-identity.md)참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="dd30b-110">For more information about the advantages of using directory synchronization, see [Directory synchronization roadmap]( https://go.microsoft.com/fwlink/p/?LinkId=525398) and [Understanding Office 365 Identity and Azure Active Directory](about-office-365-identity.md).</span></span>
  
<span data-ttu-id="dd30b-111">시나리오를 조직에 대 한 최고를 확인 하려면 [디렉터리 통합 도구 비교](https://go.microsoft.com/fwlink/p/?LinkId=525320)를 검토 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd30b-111">To determine which scenario is the best for your organization, review the [directory integration tools comparison](https://go.microsoft.com/fwlink/p/?LinkId=525320).</span></span>
  
## <a name="directory-cleanup-tasks"></a><span data-ttu-id="dd30b-112">디렉터리 정리 작업</span><span class="sxs-lookup"><span data-stu-id="dd30b-112">Directory cleanup tasks</span></span>

<span data-ttu-id="dd30b-113">디렉터리 동기화를 시작 하기 전에 디렉터리를 정리 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd30b-113">Before you begin synchronizing your directory, you need to clean up your directory.</span></span>
  
<span data-ttu-id="dd30b-114">[Azure AD 연결 하 여 Azure Active Directory 특성 동기화](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-sync-attributes-synchronized)한도 검토 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd30b-114">Review also the [attributes synchronized to Azure Active Directory by Azure AD Connect](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-sync-attributes-synchronized).</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="dd30b-p102">동기화 하기 전에 디렉터리 정리를 수행 하지는 배포 프로세스에 중요 한 부정적인 영향을 있을 수 있습니다. 일, 수행 또는 디렉터리 동기화를 다시 동기화 및 오류를 식별 하는 주기를 통과 하도록 주에도 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd30b-p102">If you don't perform directory cleanup before you synchronize, there can be a significant negative effect on the deployment process. It might take days, or even weeks, to go through the cycle of directory synchronization, identifying errors, and re-synchronization.</span></span> 
  
<span data-ttu-id="dd30b-117">프로그램 온-프레미스 디렉터리에서 다음과 같은 정리 작업을 완료 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd30b-117">In your on-premises directory, complete the following clean-up tasks:</span></span>
  
1. <span data-ttu-id="dd30b-118">Office 365 서비스 제품을 할당받을 각 사용자의 올바르고 고유한 전자 메일 주소가 **proxyAddresses** 특성에 포함되는 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="dd30b-118">Ensure that each user who will be assigned Office 365 service offerings has a valid and unique email address in the **proxyAddresses** attribute.</span></span> 
    
2. <span data-ttu-id="dd30b-119">**proxyAddresses** 속성에서 중복되는 값을 모두 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="dd30b-119">Remove any duplicate values in the **proxyAddresses** attribute.</span></span> 
    
3.  <span data-ttu-id="dd30b-p103">가능한 경우 Office 365 서비스 제품 할당 받을 각 사용자가 사용자의 **사용자** 개체의 **userPrincipalName** 특성에 대 한 유효 하 고 고유한 값을 확인 합니다. 최상의 동기화 경험에 대 한 온-프레미스 Active Directory UPN 클라우드 UPN과 일치 하는지 확인 합니다. 사용자의 **userPrincipalName** 특성에 대 한 값이 없는 경우 **사용자** 개체의 **sAMAccountName** 특성에 대 한 유효 하 고 고유한 값을 포함 해야 합니다. **UserPrincipalName** 특성에 중복 된 값을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd30b-p103">If possible, ensure that each user who will be assigned Office 365 service offerings has a valid and unique value for the **userPrincipalName** attribute in the user's **user** object. For best synchronization experience, ensure that the on-premises Active Directory UPN matches the cloud UPN. If a user does not have a value for the **userPrincipalName** attribute, then the **user** object must contain a valid and unique value for the **sAMAccountName** attribute. Remove any duplicate values in the **userPrincipalName** attribute.</span></span> 
    
4. <span data-ttu-id="dd30b-124">GAL(전체 주소 목록)을 가장 효과적으로 사용하려면 다음 특성의 정보가 올바른지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="dd30b-124">For optimal use of the global address list (GAL), be sure the information in the following attributes is correct:</span></span>
    
  - <span data-ttu-id="dd30b-125">givenName </span><span class="sxs-lookup"><span data-stu-id="dd30b-125">givenName</span></span>
  - <span data-ttu-id="dd30b-126">성</span><span class="sxs-lookup"><span data-stu-id="dd30b-126">surname</span></span>
  - <span data-ttu-id="dd30b-127">displayName</span><span class="sxs-lookup"><span data-stu-id="dd30b-127">displayName</span></span>
  - <span data-ttu-id="dd30b-128">직함</span><span class="sxs-lookup"><span data-stu-id="dd30b-128">Job Title</span></span>
  - <span data-ttu-id="dd30b-129">부서</span><span class="sxs-lookup"><span data-stu-id="dd30b-129">Department</span></span>
  - <span data-ttu-id="dd30b-130">사무실</span><span class="sxs-lookup"><span data-stu-id="dd30b-130">Office</span></span>
  - <span data-ttu-id="dd30b-131">사무실 전화</span><span class="sxs-lookup"><span data-stu-id="dd30b-131">Office Phone</span></span>
  - <span data-ttu-id="dd30b-132">휴대폰 번호</span><span class="sxs-lookup"><span data-stu-id="dd30b-132">Mobile Phone</span></span>
  - <span data-ttu-id="dd30b-133">팩스 번호</span><span class="sxs-lookup"><span data-stu-id="dd30b-133">Fax Number</span></span>
  - <span data-ttu-id="dd30b-134">주소</span><span class="sxs-lookup"><span data-stu-id="dd30b-134">Street Address</span></span>
  - <span data-ttu-id="dd30b-135">구/군/시</span><span class="sxs-lookup"><span data-stu-id="dd30b-135">City</span></span>
  - <span data-ttu-id="dd30b-136">시/도</span><span class="sxs-lookup"><span data-stu-id="dd30b-136">State or Province</span></span>
  - <span data-ttu-id="dd30b-137">우편 번호</span><span class="sxs-lookup"><span data-stu-id="dd30b-137">Zip or Postal Code</span></span>
  - <span data-ttu-id="dd30b-138">국가 또는 지역</span><span class="sxs-lookup"><span data-stu-id="dd30b-138">Country or Region</span></span>
    
## <a name="directory-object-and-attribute-preparation"></a><span data-ttu-id="dd30b-139">디렉터리 개체 및 특성 준비</span><span class="sxs-lookup"><span data-stu-id="dd30b-139">Directory object and attribute preparation</span></span>

<span data-ttu-id="dd30b-p104">온-프레미스 디렉터리 및 Office 365 간의 성공적인 디렉터리 동기화 온-프레미스 디렉터리 특성 적절히 준비는 필요 합니다. 예, Office 365 환경과 동기화 되는 특정 특성에 사용 되지 않은 특정 문자를 확인 해야 합니다. 예기치 않은 문자 실패에 대 한 디렉터리 동기화를 일으키지 않습니다 하지만 알리는 경고 메시지를 반환할 수 있습니다. 잘못 된 문자가 디렉터리 동기화 실패 하면 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd30b-p104">Successful directory synchronization between your on-premises directory and Office 365 requires that your on-premises directory attributes are properly prepared. For example, you need to ensure that specific characters aren't used in certain attributes that are synchronized with the Office 365 environment. Unexpected characters do not cause directory synchronization to fail but might return a warning. Invalid characters will cause directory synchronization to fail.</span></span>
  
<span data-ttu-id="dd30b-p105">디렉터리 동기화는 Active Directory 사용자의 일부는 중복 된 특성을 하나 이상 하는 경우에 실패 합니다. 각 사용자에는 고유한 특성이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd30b-p105">Directory synchronization will also fail if some of your Active Directory users have one or more duplicate attributes. Each user must have unique attributes.</span></span>
  
<span data-ttu-id="dd30b-146">준비 하는 특성은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="dd30b-146">The attributes that you need to prepare are listed here:</span></span>
  
 <span data-ttu-id="dd30b-147">**참고:** 또한이 프로세스를 훨씬 쉽게 [IdFix 도구](install-and-run-idfix.md) 를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd30b-147">**NOTE:** You can also use the [IdFix tool](install-and-run-idfix.md) to make this process a lot easier.</span></span> 
  
- <span data-ttu-id="dd30b-148">**displayName**</span><span class="sxs-lookup"><span data-stu-id="dd30b-148">**displayName**</span></span>
    
  - <span data-ttu-id="dd30b-149">이 특성이 사용자 개체에 있으면 Office 365와 동기화됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd30b-149">If the attribute exists in the user object, it will be synchronized with Office 365.</span></span>
  - <span data-ttu-id="dd30b-p106">사용자 개체에 이 특성이 있으면 해당하는 값이 있어야 합니다. 즉 특성은 비워 두면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd30b-p106">If this attribute exists in the user object, there must be a value for it. That is, the attribute must not be blank.</span></span>
  - <span data-ttu-id="dd30b-152">최대 문자 수: 256</span><span class="sxs-lookup"><span data-stu-id="dd30b-152">Maximum number of characters: 256</span></span>
    
- <span data-ttu-id="dd30b-153">\*\*givenName \*\*</span><span class="sxs-lookup"><span data-stu-id="dd30b-153">**givenName**</span></span>
    
  - <span data-ttu-id="dd30b-154">사용자 개체에 특성이 있으면 Office 365와 동기화되지만, Office 365에서 해당 특성이 필요하거나 이를 사용하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dd30b-154">If the attribute exists in the user object, it will be synchronized with Office 365, but Office 365 does not require or use it.</span></span>
  - <span data-ttu-id="dd30b-155">최대 문자 수: 64</span><span class="sxs-lookup"><span data-stu-id="dd30b-155">Maximum number of characters: 64</span></span>
    
- <span data-ttu-id="dd30b-156">**메일**</span><span class="sxs-lookup"><span data-stu-id="dd30b-156">**mail**</span></span>
    
  - <span data-ttu-id="dd30b-157">특성 값은 디렉터리 내에서 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd30b-157">The attribute value must be unique within the directory.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="dd30b-p107">중복 값이 없으면 값을 가진 첫번째 사용자 동기화 됩니다. 이후 사용자가 Office 365에 나타나지 않습니다. Office 365의 값을 수정 하거나 두 사용자가 Office 365에 표시 하는 순서는 온-프레미스 디렉터리의 값을 모두 수정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd30b-p107">If there are duplicate values, the first user with the value is synchronized. Subsequent users will not appear in Office 365. You must modify either the value in Office 365, or modify both of the values in the on-premises directory in order for both users to appear in Office 365.</span></span> 
  
- <span data-ttu-id="dd30b-161">**mailNickname**(Exchange 별칭)</span><span class="sxs-lookup"><span data-stu-id="dd30b-161">**mailNickname** (Exchange alias)</span></span> 
    
  - <span data-ttu-id="dd30b-162">특성 값에 마침표 (.)로 시작할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="dd30b-162">The attribute value cannot begin with a period (.).</span></span>
  - <span data-ttu-id="dd30b-163">특성 값은 디렉터리 내에서 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd30b-163">The attribute value must be unique within the directory.</span></span>
    
- <span data-ttu-id="dd30b-164">\*\*proxyAddresses \*\*</span><span class="sxs-lookup"><span data-stu-id="dd30b-164">**proxyAddresses**</span></span>
    
  - <span data-ttu-id="dd30b-165">다중값 특성</span><span class="sxs-lookup"><span data-stu-id="dd30b-165">Multiple-value attribute</span></span>
  - <span data-ttu-id="dd30b-166">값당 최대 문자 수: 256</span><span class="sxs-lookup"><span data-stu-id="dd30b-166">Maximum number of characters per value: 256</span></span>
  - <span data-ttu-id="dd30b-167">특성 값에 공백이 포함 해서는 안됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd30b-167">The attribute value must not contain a space.</span></span>
  - <span data-ttu-id="dd30b-168">특성 값은 디렉터리 내에서 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd30b-168">The attribute value must be unique within the directory.</span></span>
  - <span data-ttu-id="dd30b-169">유효 하지 않은 문자: \< \> (); , [ ] "</span><span class="sxs-lookup"><span data-stu-id="dd30b-169">Invalid characters: \< \> ( ) ; , [ ] "</span></span>
    
    <span data-ttu-id="dd30b-170">잘못 된 문자는 문자에 유형을 구분 기호 뒤에 적용 하 고 ":" SMTP:User@contso.com를 사용할 수 있지만 SMTP:user:M@contoso.com 하지는 않도록, 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd30b-170">Note that the invalid characters apply to the characters following the type delimiter and ":", such that SMTP:User@contso.com is allowed, but SMTP:user:M@contoso.com is not.</span></span>
    
    > [!IMPORTANT]
    > <span data-ttu-id="dd30b-p108">모든 메일 전송 SMTP (Simple Protocol) 주소는 전자 메일 메시징 표준을 준수 해야 합니다. 중복 되거나 불필요 한 주소 존재 하는 경우 [Exchange에서 주소를 복제 하 고 불필요 한 프록시를 제거](https://go.microsoft.com/fwlink/?LinkId=293860)하는 도움말 항목을 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd30b-p108">All Simple Mail Transport Protocol (SMTP) addresses should comply with email messaging standards. If duplicate or unwanted addresses exist, see the Help topic [Removing duplicate and unwanted proxy addresses in Exchange](https://go.microsoft.com/fwlink/?LinkId=293860).</span></span> 
  
- <span data-ttu-id="dd30b-173">**sAMAccountName**</span><span class="sxs-lookup"><span data-stu-id="dd30b-173">**sAMAccountName**</span></span>
    
  - <span data-ttu-id="dd30b-174">최대 문자 수: 20</span><span class="sxs-lookup"><span data-stu-id="dd30b-174">Maximum number of characters: 20</span></span>
  - <span data-ttu-id="dd30b-175">특성 값은 디렉터리 내에서 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd30b-175">The attribute value must be unique within the directory.</span></span>
  - <span data-ttu-id="dd30b-p109">유효 하지 않은 문자: [\ "|, /: \< \> + =;? \* ]</span><span class="sxs-lookup"><span data-stu-id="dd30b-p109">Invalid characters: [ \ " | , / : \< \> + = ; ? \* ]</span></span>
  - <span data-ttu-id="dd30b-178">사용자의 **sAMAccountName** 특성이 유효하지 않지만 **userPrincipalName** 특성이 유효한 경우 사용자 계정이 Office 365에서 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="dd30b-178">If a user has an invalid **sAMAccountName** attribute but has a valid **userPrincipalName** attribute, the user account is created in Office 365.</span></span> 
  - <span data-ttu-id="dd30b-179">**SAMAccountName** 및 **userPrincipalName** 이 둘다 유효 하지 않은 경우에 온-프레미스 Active Directory **userPrincipalName** 특성을 업데이트 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd30b-179">If both **sAMAccountName** and **userPrincipalName** are invalid, the on-premises Active Directory **userPrincipalName** attribute must be updated.</span></span> 
    
- <span data-ttu-id="dd30b-180">**sn**(성)</span><span class="sxs-lookup"><span data-stu-id="dd30b-180">**sn** (surname)</span></span> 
    
  - <span data-ttu-id="dd30b-181">사용자 개체에 특성이 있으면 Office 365와 동기화되지만, Office 365에서 해당 특성이 필요하거나 이를 사용하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dd30b-181">If the attribute exists in the user object, it will be synchronized with Office 365, but Office 365 does not require or use it.</span></span>
    
- <span data-ttu-id="dd30b-182">**targetAddress**</span><span class="sxs-lookup"><span data-stu-id="dd30b-182">**targetAddress**</span></span>
    
    <span data-ttu-id="dd30b-p110">Office 365 GAL에에서는 사용자에 대 한 채워지는 **targetAddress** 특성 (예: SMTP:tom@contoso.com) 해야 나타나는지 필요한 합니다. 타사 메시징 마이그레이션 시나리오에서 온-프레미스 디렉터리에 대 한 Office 365 스키마를 확장을 해야 합니다. Office 365 스키마 확장은 온-프레미스 디렉터리에서 디렉터리 동기화 도구를 사용 하 여 채워져 있는 Office 365 개체를 관리 하는데 유용한 다른 특성 추가적으로 합니다. 예, 숨겨진된 사서함 또는 메일 그룹을 관리할 **msExchHideFromAddressLists** 특성 추가지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dd30b-p110">It's required that the **targetAddress** attribute (for example, SMTP:tom@contoso.com) that's populated for the user must appear in the Office 365 GAL. In third-party messaging migration scenarios, this would require the Office 365 schema extension for the on-premises directory. The Office 365 schema extension would also add other useful attributes to manage Office 365 objects that are populated by using a directory synchronization tool from on-premises directory. For example, the **msExchHideFromAddressLists** attribute to manage hidden mailboxes or distribution groups would be added.</span></span> 
   
  - <span data-ttu-id="dd30b-187">최대 문자 수: 256</span><span class="sxs-lookup"><span data-stu-id="dd30b-187">Maximum number of characters: 256</span></span>
  - <span data-ttu-id="dd30b-188">특성 값에 공백이 포함 해서는 안됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd30b-188">The attribute value must not contain a space.</span></span>
  - <span data-ttu-id="dd30b-189">특성 값은 디렉터리 내에서 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd30b-189">The attribute value must be unique within the directory.</span></span>
  - <span data-ttu-id="dd30b-190">유효 하지 않은 문자: \ \< \> (); , [ ] "</span><span class="sxs-lookup"><span data-stu-id="dd30b-190">Invalid characters: \ \< \> ( ) ; , [ ] "</span></span>
  - <span data-ttu-id="dd30b-191">모든 SMTP(Simple Mail Transport Protocol) 주소는 전자 메일 메시징 표준을 준수해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd30b-191">All Simple Mail Transport Protocol (SMTP) addresses should comply with email messaging standards.</span></span>
    
- <span data-ttu-id="dd30b-192">**userPrincipalName**</span><span class="sxs-lookup"><span data-stu-id="dd30b-192">**userPrincipalName**</span></span>
    
  - <span data-ttu-id="dd30b-p111">**UserPrincipalName** 특성 하 여 사용자 이름 뒤에 있는 로그인 형식 인터넷 스타일에에서 있어야는 at 기호 (@) 및 도메인 이름: 예: user@contoso.com 합니다. 모든 메일 전송 SMTP (Simple Protocol) 주소는 전자 메일 메시징 표준을 준수 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd30b-p111">The **userPrincipalName** attribute must be in the Internet-style sign-in format where the user name is followed by the at sign (@) and a domain name: for example, user@contoso.com. All Simple Mail Transport Protocol (SMTP) addresses should comply with email messaging standards.</span></span>
  - <span data-ttu-id="dd30b-p112">**userPrincipalName** 특성의 최대 문자 수는 113자입니다. 다음과 같이 @ 기호 앞뒤에는 특정 개수의 문자가 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd30b-p112">The maximum number of characters for the **userPrincipalName** attribute is 113. A specific number of characters are permitted before and after the at sign (@), as follows:</span></span> 
  - <span data-ttu-id="dd30b-197">@ 기호 앞에 있는 사용자 이름의 최대 문자 수: 64</span><span class="sxs-lookup"><span data-stu-id="dd30b-197">Maximum number of characters for the user name that is in front of the at sign (@): 64</span></span>
  - <span data-ttu-id="dd30b-198">@ 기호 뒤에 있는 도메인 이름의 최대 문자 수: 48</span><span class="sxs-lookup"><span data-stu-id="dd30b-198">Maximum number of characters for the domain name following the at sign (@): 48</span></span>
  - <span data-ttu-id="dd30b-p113">유효 하지 않은 문자: \ % &amp; \* + / =? { } | \< \> ( ) ; : , [ ] "</span><span class="sxs-lookup"><span data-stu-id="dd30b-p113">Invalid characters: \ % &amp; \* + / = ? { } | \< \> ( ) ; : , [ ] "</span></span>
  - <span data-ttu-id="dd30b-201">움라우트 잘못 된 문자가 이기도합니다.</span><span class="sxs-lookup"><span data-stu-id="dd30b-201">An umlaut is also an invalid character.</span></span>
  - <span data-ttu-id="dd30b-202">@ 문자가 각 **userPrincipalName** 값에 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd30b-202">The @ character is required in each **userPrincipalName** value.</span></span> 
  - <span data-ttu-id="dd30b-203">@ 문자는 각 **userPrincipalName** 값의 첫 번째 문자일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="dd30b-203">The @ character cannot be the first character in each **userPrincipalName** value.</span></span> 
  - <span data-ttu-id="dd30b-204">사용자 이름은 마침표 (.), 앰퍼샌드 끝날 수 없습니다 (&amp;), 공백, a 또는 한 at 기호 (@).</span><span class="sxs-lookup"><span data-stu-id="dd30b-204">The user name cannot end with a period (.), an ampersand (&amp;), a space, or an at sign (@).</span></span>
  - <span data-ttu-id="dd30b-205">사용자 이름에는 공백을 포함할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="dd30b-205">The user name cannot contain any spaces.</span></span>
  - <span data-ttu-id="dd30b-206">라우팅할 수 있는 도메인을 사용 해야 합니다. 예, 로컬 또는 내부 도메인을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="dd30b-206">Routable domains must be used; for example, local or internal domains cannot be used.</span></span>
  - <span data-ttu-id="dd30b-207">유니코드는 밑줄 문자로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd30b-207">Unicode is converted to underscore characters.</span></span>
  - <span data-ttu-id="dd30b-208">**userPrincipalName**에는 디렉터리에서 중복된 값을 포함할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="dd30b-208">**userPrincipalName** cannot contain any duplicate values in the directory.</span></span> 
    
## <a name="prepare-the-userprincipalname-attribute"></a><span data-ttu-id="dd30b-209">userPrincipalName 특성 준비</span><span class="sxs-lookup"><span data-stu-id="dd30b-209">Prepare the userPrincipalName attribute</span></span>

<span data-ttu-id="dd30b-p114">Active Directory는 **sAMAccountName** 또는 **userPrincipalName**중 하나를 사용 하 여 디렉터리에 로그인 하 여 조직에서 최종 사용자를 허용 하도록 설계 되었습니다. 마찬가지로, 최종 사용자가 자신의 작업의 사용자 계정 이름 (UPN)를 사용 하 여 Office 365에 로그인 하거나 계정 학교 수 있습니다. 디렉터리 동기화 온-프레미스 디렉터리에 있는 동일한 UPN을 사용 하 여 Azure Active Directory에 새 사용자를 만들려고 시도 합니다. UPN 전자 메일 주소 형식으로 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd30b-p114">Active Directory is designed to allow the end users in your organization to sign in to your directory by using either **sAMAccountName** or **userPrincipalName**. Similarly, end users can sign in to Office 365 by using the user principal name (UPN) of their work or school account. Directory synchronization attempts to create new users in Azure Active Directory by using the same UPN that's in your on-premises directory. The UPN is formatted like an email address.</span></span> 

<span data-ttu-id="dd30b-p115">Office 365 UPN 전자 메일 주소를 생성 하는데 사용 되는 기본 특성을입니다. **UserPrincipalName** 가져올 쉽습니다 (온-프레미스 및 Azure Active Directory에서) 및 **proxyAddresses** 서로 다른 값으로 설정의 기본 전자 메일 주소입니다. 서로 다른 값으로 설정 하는 경우 관리자와 최종 사용자에 대 한 혼란 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd30b-p115">In Office 365, the UPN is the default attribute that's used to generate the email address. It's easy to get **userPrincipalName** (on-premises and in Azure Active Directory) and the primary email address in **proxyAddresses** set to different values. When they are set to different values, there can be confusion for administrators and end users.</span></span> 
  
<span data-ttu-id="dd30b-p116">이러한 특성 혼동을 줄이기 위한을 정렬 하는 것이 좋습니다. Active Directory Federation services (AD FS)에서 single sign-on의 요구 사항에 맞게 2.0, 해야 Azure Active Directory 및 온-프레미스 Active Directory에서 Upn을 확인 하는 유효한 도메인 네임 스페이스를 사용 하 여 일치 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd30b-p116">It's best to align these attributes to reduce confusion. To meet the requirements of single sign-on with Active Directory Federation Services (AD FS) 2.0, you need to ensure that the UPNs in Azure Active Directory and your on-premises Active Directory match and are using a valid domain namespace.</span></span>
  
## <a name="add-an-alternative-upn-suffix-to-ad-ds"></a><span data-ttu-id="dd30b-219">AD DS에 대체 UPN 접미사를 추가</span><span class="sxs-lookup"><span data-stu-id="dd30b-219">Add an alternative UPN suffix to AD DS</span></span>

<span data-ttu-id="dd30b-p117">Office 365 환경과 사용자의 회사 자격 증명을 연결 하려면 대체 UPN 접미사를 추가 해야 합니다. UPN 접미사는 오른쪽에 UPN의 일부는 @ 문자입니다. Single sign-on에 사용 되는 Upn 문자, 숫자, 기간, 대시 및 밑줄을 사용할 수 있지만 다른 종류의 문자를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd30b-p117">You may need to add an alternative UPN suffix to associate the user's corporate credentials with the Office 365 environment. A UPN suffix is the part of a UPN to the right of the @ character. UPNs that are used for single sign-on can contain letters, numbers, periods, dashes, and underscores, but no other types of characters.</span></span>
  
<span data-ttu-id="dd30b-223">Active Directory에 대체 UPN 접미사를 추가 하는 방법에 대 한 자세한 내용은 [디렉터리 동기화 준비]( https://go.microsoft.com/fwlink/p/?LinkId=525430)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="dd30b-223">For more information on how to add an alternative UPN suffix to Active Directory, see [Prepare for directory synchronization]( https://go.microsoft.com/fwlink/p/?LinkId=525430).</span></span>
  
## <a name="match-the-on-premises-upn-with-the-office-365-upn"></a><span data-ttu-id="dd30b-224">Office 365와 함께 온-프레미스 UPN과 일치 UPN</span><span class="sxs-lookup"><span data-stu-id="dd30b-224">Match the on-premises UPN with the Office 365 UPN</span></span>

<span data-ttu-id="dd30b-p118">디렉터리 동기화를 이미 설정한 경우 Office 365에 대 한 사용자의 UPN 온-프레미스 디렉터리 서비스에 정의 된 사용자의 온-프레미스 UPN와 일치 하지 않을 수 있습니다. 이 사용자의 도메인 확인 되었음을 전에 라이선스를 할당 된 경우 발생할 수 있습니다. 이 문제를 해결 하려면 회사 사용자 이름과 도메인 Office 365 UPN과 일치 하는지 확인 하는 사용자의 UPN을 업데이트 하려면 [중복 된 UPN을 수정 하는 PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=396730) 을 사용 합니다. 온-프레미스 디렉터리 서비스에서 UPN을 업데이트 하는 id가 Azure Active Directory와 동기화 되도록 구매할 하는 경우 변경 내용을 온-프레미스를 만들기 전에 Office 365에서 사용자의 라이선스를 제거 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd30b-p118">If you've already set up directory synchronization, the user's UPN for Office 365 may not match the user's on-premises UPN that's defined in your on-premises directory service. This can occur when a user was assigned a license before the domain was verified. To fix this, use [PowerShell to fix duplicate UPN](https://go.microsoft.com/fwlink/p/?LinkId=396730) to update the user's UPN to ensure that the Office 365 UPN matches the corporate user name and domain. If you are updating the UPN in the on-premises directory service and would like it to synchronize with the Azure Active Directory identity, you need to remove the user's license in Office 365 prior to making the changes on-premises.</span></span> 
  
<span data-ttu-id="dd30b-229">[디렉터리 동기화를 위한 라우팅할 수 없는 도메인 (예:.local 도메인)를 준비 하는 방법](prepare-a-non-routable-domain-for-directory-synchronization.md)을 참고 하십시오.</span><span class="sxs-lookup"><span data-stu-id="dd30b-229">See also [How to prepare a non-routable domain (such as .local domain) for directory synchronization](prepare-a-non-routable-domain-for-directory-synchronization.md).</span></span>
  
## <a name="directory-integration-tools"></a><span data-ttu-id="dd30b-230">디렉터리 통합 도구</span><span class="sxs-lookup"><span data-stu-id="dd30b-230">Directory integration tools</span></span>

<span data-ttu-id="dd30b-p119">디렉터리 동기화가 디렉터리 개체의 (사용자, 그룹 및 연락처)를 온-프레미스 Active Directory 환경에서에서 Office 365 디렉터리 인프라 Azure Active Directory 동기화 합니다. 사용 가능한 도구 및 해당 기능 목록에 대 한 [디렉터리 통합 도구](https://go.microsoft.com/fwlink/p/?LinkID=510956) 를 참조 하십시오. 권장 되는 도구는 [Microsoft Azure Active Directory에 연결](https://go.microsoft.com/fwlink/p/?LinkID=510956)합니다. Azure Active Directory에 연결 하는 방법에 대 한 자세한 내용은 [Azure Active Directory를 사용 하 여 온-프레미스 id가 통합 (영문)을](https://go.microsoft.com/fwlink/p/?LinkId=527969)참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="dd30b-p119">Directory synchronization is the synchronization of directory objects (users, groups, and contacts) from your on-premises Active Directory environment to the Office 365 directory infrastructure, Azure Active Directory. See [Directory Integration Tools](https://go.microsoft.com/fwlink/p/?LinkID=510956) for a list of the available tools and their functionality. The recommended tool is [Microsoft Azure Active Directory Connect](https://go.microsoft.com/fwlink/p/?LinkID=510956). For more information about Azure Active Directory Connect, see [Integrating your on-premises identities with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=527969).</span></span>
  
<span data-ttu-id="dd30b-p120">표시 된 사용자 계정을 처음에 대 한 Office 365 디렉터리와 동기화 된 경우 활성화 되지 않은 것으로 합니다. 전자 메일을 수신 하거나 보낼 수는 없습니다 및 구독 라이선스를 사용 하지 않습니다. 특정 사용자에 게 Office 365 구독을 할당 하려면 준비 되 면를 선택 하 고 [비즈니스를 위한 Office 365에서 사용자에 게 라이선스를 할당](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc)하 여이 활성화 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd30b-p120">When user accounts are synchronized with the Office 365 directory for the first time, they are marked as not activated. They cannot send or receive email, and they don't consume subscription licenses. When you're ready to assign Office 365 subscriptions to specific users, you must select and activate them by [Assign licenses to users in Office 365 for business](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc).</span></span>
  
<span data-ttu-id="dd30b-p121">[PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=613097) 을 사용 하 여 라이선스를 할당 하려면 수도 있습니다. 자동화 된 솔루션에 대 한 [PowerShell Office 365 사용자에 게 자동으로 할당 라이선스를 사용 하는 방법](https://go.microsoft.com/fwlink/p?LinkID=329805) 을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="dd30b-p121">You can also use [PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=613097) to assign licenses. See [How to Use PowerShell to Automatically Assign Licenses to Your Office 365 Users](https://go.microsoft.com/fwlink/p?LinkID=329805) for an automated solution.</span></span>