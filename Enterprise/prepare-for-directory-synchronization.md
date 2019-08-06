---
title: Office 365에 대 한 디렉터리 동기화 준비
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
ms.openlocfilehash: 67d22f9087aabd431f61e01f6669ef147db98516
ms.sourcegitcommit: 3dc4cb3ed48429fcb84f8adeba3d9ba2fb38edf7
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/26/2019
ms.locfileid: "35249199"
---
# <a name="prepare-for-directory-synchronization-to-office-365"></a><span data-ttu-id="d3adc-103">Office 365에 대 한 디렉터리 동기화 준비</span><span class="sxs-lookup"><span data-stu-id="d3adc-103">Prepare for directory synchronization to Office 365</span></span>

<span data-ttu-id="d3adc-104">조직에 대 한 하이브리드 id 및 디렉터리 동기화의 이점은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-104">The benefits to hybrid identity and directory synchronization your organization include:</span></span>
  
- <span data-ttu-id="d3adc-105">조직의 관리 프로그램 감소</span><span class="sxs-lookup"><span data-stu-id="d3adc-105">Reducing the administrative programs in your organization</span></span>
- <span data-ttu-id="d3adc-106">선택적으로 single sign-on 시나리오를 사용 하도록 설정</span><span class="sxs-lookup"><span data-stu-id="d3adc-106">Optionally enabling single sign-on scenario</span></span>
- <span data-ttu-id="d3adc-107">Office 365에서 계정 변경 자동화</span><span class="sxs-lookup"><span data-stu-id="d3adc-107">Automating account changes in Office 365</span></span>
    
<span data-ttu-id="d3adc-108">디렉터리 동기화를 사용할 때의 이점에 대 한 자세한 내용은 [디렉터리 동기화 로드맵]( https://go.microsoft.com/fwlink/p/?LinkId=525398) 및 [Office 365의 하이브리드 id](plan-for-directory-synchronization.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d3adc-108">For more information about the advantages of using directory synchronization, see [Directory synchronization roadmap]( https://go.microsoft.com/fwlink/p/?LinkId=525398) and [Hybrid identity for Office 365](plan-for-directory-synchronization.md).</span></span>

<span data-ttu-id="d3adc-109">그러나 디렉터리 동기화의 경우에는 계획 및 준비를 수행 하 여 AD DS (Active Directory 도메인 서비스)가 Office 365 구독에 대 한 azure Active Directory (Azure AD) 테 넌 트와 동기화 하 여 오류가 최소화 되도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-109">However, directory synchronization requires planning and preparation to ensure that your Active Directory Domain Services (AD DS) synchronizes to the Azure Active Directory (Azure AD) tenant of your Office 365 subscription with a minimum of errors.</span></span> 

<span data-ttu-id="d3adc-110">최상의 결과를 위해 다음 단계를 순서 대로 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-110">Follow these steps in order for the best results.</span></span>
  
## <a name="1-directory-cleanup-tasks"></a><span data-ttu-id="d3adc-111">1. 디렉터리 정리 작업</span><span class="sxs-lookup"><span data-stu-id="d3adc-111">1. Directory cleanup tasks</span></span>

<span data-ttu-id="d3adc-112">Azure AD 테 넌 트에 AD DS를 동기화 하기 전에 AD DS를 정리 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-112">Before you synchronize your AD DS to your Azure AD tenant, you need to clean up your AD DS.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d3adc-113">동기화 하기 전에 AD DS 정리를 수행 하지 않으면 배포 프로세스에 큰 부정적인 영향을 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-113">If you don't perform AD DS cleanup before you synchronize, there can be a significant negative effect on the deployment process.</span></span> <span data-ttu-id="d3adc-114">디렉터리 동기화 주기, 오류 식별 및 다시 동기화를 진행 하는 데 며칠 또는 몇 주가 소요 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-114">It might take days, or even weeks, to go through the cycle of directory synchronization, identifying errors, and re-synchronization.</span></span> 
  
<span data-ttu-id="d3adc-115">AD DS에서 Office 365 라이선스가 할당 될 각 사용자 계정에 대해 다음과 같은 정리 작업을 완료 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-115">In your AD DS, complete the following clean-up tasks for each user account that will be assigned an Office 365 license:</span></span>
  
1. <span data-ttu-id="d3adc-116">**ProxyAddresses** 특성에 유효한 전자 메일 주소와 고유한 주소가 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-116">Ensure a valid and unique email address in the **proxyAddresses** attribute.</span></span> 
    
2. <span data-ttu-id="d3adc-117">**ProxyAddresses** 특성에서 중복 된 값을 모두 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-117">Remove any duplicate values in the **proxyAddresses** attribute.</span></span> 
    
3.  <span data-ttu-id="d3adc-118">가능한 경우 사용자의 **user** 개체에 있는 **userPrincipalName** 특성에 대 한 유효한 값 및 고유함을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-118">If possible, ensure a valid and unique value for the **userPrincipalName** attribute in the user's **user** object.</span></span> <span data-ttu-id="d3adc-119">최상의 동기화 환경을 위해 AD DS UPN이 Azure AD UPN과 일치 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-119">For the best synchronization experience, ensure that the AD DS UPN matches the Azure AD UPN.</span></span> <span data-ttu-id="d3adc-120">사용자에 게 **userPrincipalName** 특성에 대 한 값이 없는 경우에는 **사용자** 개체에 **sAMAccountName** 특성에 대 한 유효한 값과 고유 정보가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-120">If a user does not have a value for the **userPrincipalName** attribute, then the **user** object must contain a valid and unique value for the **sAMAccountName** attribute.</span></span> <span data-ttu-id="d3adc-121">**UserPrincipalName** 특성에서 중복 된 값을 모두 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-121">Remove any duplicate values in the **userPrincipalName** attribute.</span></span> 
    
4. <span data-ttu-id="d3adc-122">전체 주소 목록 (GAL)을 최적의 상태로 사용 하려면 AD DS 사용자 계정의 다음 특성에 있는 정보가 올바른지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-122">For optimal use of the global address list (GAL), ensure the information in the following attributes of the AD DS user account is correct:</span></span>
    
  - <span data-ttu-id="d3adc-123">givenName</span><span class="sxs-lookup"><span data-stu-id="d3adc-123">givenName</span></span>
  - <span data-ttu-id="d3adc-124">성</span><span class="sxs-lookup"><span data-stu-id="d3adc-124">surname</span></span>
  - <span data-ttu-id="d3adc-125">n</span><span class="sxs-lookup"><span data-stu-id="d3adc-125">displayName</span></span>
  - <span data-ttu-id="d3adc-126">직함</span><span class="sxs-lookup"><span data-stu-id="d3adc-126">Job Title</span></span>
  - <span data-ttu-id="d3adc-127">부서</span><span class="sxs-lookup"><span data-stu-id="d3adc-127">Department</span></span>
  - <span data-ttu-id="d3adc-128">사무실</span><span class="sxs-lookup"><span data-stu-id="d3adc-128">Office</span></span>
  - <span data-ttu-id="d3adc-129">사무실 전화</span><span class="sxs-lookup"><span data-stu-id="d3adc-129">Office Phone</span></span>
  - <span data-ttu-id="d3adc-130">휴대폰 번호</span><span class="sxs-lookup"><span data-stu-id="d3adc-130">Mobile Phone</span></span>
  - <span data-ttu-id="d3adc-131">팩스 번호</span><span class="sxs-lookup"><span data-stu-id="d3adc-131">Fax Number</span></span>
  - <span data-ttu-id="d3adc-132">주소</span><span class="sxs-lookup"><span data-stu-id="d3adc-132">Street Address</span></span>
  - <span data-ttu-id="d3adc-133">구/군/시</span><span class="sxs-lookup"><span data-stu-id="d3adc-133">City</span></span>
  - <span data-ttu-id="d3adc-134">시/도</span><span class="sxs-lookup"><span data-stu-id="d3adc-134">State or Province</span></span>
  - <span data-ttu-id="d3adc-135">우편 번호</span><span class="sxs-lookup"><span data-stu-id="d3adc-135">Zip or Postal Code</span></span>
  - <span data-ttu-id="d3adc-136">국가</span><span class="sxs-lookup"><span data-stu-id="d3adc-136">Country or Region</span></span>
    
## <a name="2-directory-object-and-attribute-preparation"></a><span data-ttu-id="d3adc-137">2. 디렉터리 개체 및 특성 준비</span><span class="sxs-lookup"><span data-stu-id="d3adc-137">2. Directory object and attribute preparation</span></span>

<span data-ttu-id="d3adc-138">AD DS와 Office 365 간의 디렉터리 동기화가 정상적으로 수행 되려면 AD DS 특성이 적절 하 게 준비 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-138">Successful directory synchronization between your AD DS and Office 365 requires that your AD DS attributes are properly prepared.</span></span> <span data-ttu-id="d3adc-139">예를 들어 Office 365 환경과 동기화 되는 특정 특성에 특정 문자가 사용 되지 않는지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-139">For example, you need to ensure that specific characters aren't used in certain attributes that are synchronized with the Office 365 environment.</span></span> <span data-ttu-id="d3adc-140">예기치 않은 문자로 인해 디렉터리 동기화가 실패 하는 것은 아니지만 경고를 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-140">Unexpected characters do not cause directory synchronization to fail but might return a warning.</span></span> <span data-ttu-id="d3adc-141">잘못 된 문자가 있으면 디렉터리 동기화가 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-141">Invalid characters will cause directory synchronization to fail.</span></span>
  
<span data-ttu-id="d3adc-142">AD DS 사용자 중 일부에 중복 된 특성이 하나 이상 있는 경우에도 디렉터리 동기화가 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-142">Directory synchronization will also fail if some of your AD DS users have one or more duplicate attributes.</span></span> <span data-ttu-id="d3adc-143">각 사용자에 게는 고유한 특성이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-143">Each user must have unique attributes.</span></span>
  
<span data-ttu-id="d3adc-144">준비 해야 하는 특성은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-144">The attributes that you need to prepare are listed here:</span></span>
  
- <span data-ttu-id="d3adc-145">**n**</span><span class="sxs-lookup"><span data-stu-id="d3adc-145">**displayName**</span></span>
    
  - <span data-ttu-id="d3adc-146">사용자 개체에 특성이 있으면 Office 365와 동기화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-146">If the attribute exists in the user object, it will be synchronized with Office 365.</span></span>
  - <span data-ttu-id="d3adc-147">이 특성이 사용자 개체에 있는 경우에는 해당 특성에 대 한 값이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-147">If this attribute exists in the user object, there must be a value for it.</span></span> <span data-ttu-id="d3adc-148">즉, 특성을 비워 두면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-148">That is, the attribute must not be blank.</span></span>
  - <span data-ttu-id="d3adc-149">최대 문자 수: 256</span><span class="sxs-lookup"><span data-stu-id="d3adc-149">Maximum number of characters: 256</span></span>
    
- <span data-ttu-id="d3adc-150">**givenName**</span><span class="sxs-lookup"><span data-stu-id="d3adc-150">**givenName**</span></span>
    
  - <span data-ttu-id="d3adc-151">사용자 개체에 특성이 있으면 Office 365와 동기화 되지만 Office 365에서는이 특성을 사용할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-151">If the attribute exists in the user object, it will be synchronized with Office 365, but Office 365 does not require or use it.</span></span>
  - <span data-ttu-id="d3adc-152">최대 문자 수: 64</span><span class="sxs-lookup"><span data-stu-id="d3adc-152">Maximum number of characters: 64</span></span>
    
- <span data-ttu-id="d3adc-153">**메일**</span><span class="sxs-lookup"><span data-stu-id="d3adc-153">**mail**</span></span>
    
  - <span data-ttu-id="d3adc-154">특성 값은 디렉터리 내에서 고유 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-154">The attribute value must be unique within the directory.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="d3adc-155">중복 된 값이 있는 경우 값이 있는 첫 번째 사용자가 동기화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-155">If there are duplicate values, the first user with the value is synchronized.</span></span> <span data-ttu-id="d3adc-156">이후 사용자는 Office 365에 나타나지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-156">Subsequent users will not appear in Office 365.</span></span> <span data-ttu-id="d3adc-157">두 사용자가 Office 365에 나타나려면 Office 365의 값을 수정 하거나 AD DS의 값을 모두 수정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-157">You must modify either the value in Office 365 or modify both of the values in AD DS in order for both users to appear in Office 365.</span></span> 
  
- <span data-ttu-id="d3adc-158">**mailNickname** (Exchange 별칭)</span><span class="sxs-lookup"><span data-stu-id="d3adc-158">**mailNickname** (Exchange alias)</span></span> 
    
  - <span data-ttu-id="d3adc-159">특성 값은 마침표 (.)로 시작할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-159">The attribute value cannot begin with a period (.).</span></span>
  - <span data-ttu-id="d3adc-160">특성 값은 디렉터리 내에서 고유 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-160">The attribute value must be unique within the directory.</span></span>
    
- <span data-ttu-id="d3adc-161">**proxyAddresses**</span><span class="sxs-lookup"><span data-stu-id="d3adc-161">**proxyAddresses**</span></span>
    
  - <span data-ttu-id="d3adc-162">여러 값 특성</span><span class="sxs-lookup"><span data-stu-id="d3adc-162">Multiple-value attribute</span></span>
  - <span data-ttu-id="d3adc-163">값 당 최대 문자 수: 256</span><span class="sxs-lookup"><span data-stu-id="d3adc-163">Maximum number of characters per value: 256</span></span>
  - <span data-ttu-id="d3adc-164">특성 값에는 공백이 없어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-164">The attribute value must not contain a space.</span></span>
  - <span data-ttu-id="d3adc-165">특성 값은 디렉터리 내에서 고유 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-165">The attribute value must be unique within the directory.</span></span>
  - <span data-ttu-id="d3adc-166">유효 하지 않은 \< \> 문자: (); , [ ] " '</span><span class="sxs-lookup"><span data-stu-id="d3adc-166">Invalid characters: \< \> ( ) ; , [ ] " '</span></span>
    
    <span data-ttu-id="d3adc-167">잘못 된 문자는 형식 구분 기호 뒤에 있는 문자에 적용 되 고, SMTP:User@contso.com는 허용 되지만 SMTP:user:M@contoso.com는 그렇지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-167">Note that the invalid characters apply to the characters following the type delimiter and ":", such that SMTP:User@contso.com is allowed, but SMTP:user:M@contoso.com is not.</span></span>
    
    > [!IMPORTANT]
    > <span data-ttu-id="d3adc-168">모든 SMTP (Simple Mail Transport Protocol) 주소는 전자 메일 메시징 표준을 준수 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-168">All Simple Mail Transport Protocol (SMTP) addresses should comply with email messaging standards.</span></span> <span data-ttu-id="d3adc-169">중복 또는 원치 않는 주소가 있으면 [Exchange에서 중복 및 원하지 않는 프록시 주소 제거](https://go.microsoft.com/fwlink/?LinkId=293860)도움말 항목을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="d3adc-169">If duplicate or unwanted addresses exist, see the Help topic [Removing duplicate and unwanted proxy addresses in Exchange](https://go.microsoft.com/fwlink/?LinkId=293860).</span></span> 
  
- <span data-ttu-id="d3adc-170">**sAMAccountName**</span><span class="sxs-lookup"><span data-stu-id="d3adc-170">**sAMAccountName**</span></span>
    
  - <span data-ttu-id="d3adc-171">최대 문자 수: 20</span><span class="sxs-lookup"><span data-stu-id="d3adc-171">Maximum number of characters: 20</span></span>
  - <span data-ttu-id="d3adc-172">특성 값은 디렉터리 내에서 고유 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-172">The attribute value must be unique within the directory.</span></span>
  - <span data-ttu-id="d3adc-173">유효 하지 않은 문자: [\ "|, \< \> /: + =;?</span><span class="sxs-lookup"><span data-stu-id="d3adc-173">Invalid characters: [ \ " | , / : \< \> + = ; ?</span></span> <span data-ttu-id="d3adc-174">\* ']</span><span class="sxs-lookup"><span data-stu-id="d3adc-174"></span></span>
  - <span data-ttu-id="d3adc-175">사용자의 **sAMAccountName** 특성이 유효 하지 않지만 **userPrincipalName** 특성이 유효한 경우 사용자 계정이 Office 365에서 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-175">If a user has an invalid **sAMAccountName** attribute but has a valid **userPrincipalName** attribute, the user account is created in Office 365.</span></span> 
  - <span data-ttu-id="d3adc-176">**SAMAccountName** 및 **userPrincipalName** 이 둘 다 유효 하지 않은 경우 AD DS **userPrincipalName** 특성을 업데이트 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-176">If both **sAMAccountName** and **userPrincipalName** are invalid, the AD DS **userPrincipalName** attribute must be updated.</span></span> 
    
- <span data-ttu-id="d3adc-177">**sn** 성</span><span class="sxs-lookup"><span data-stu-id="d3adc-177">**sn** (surname)</span></span> 
    
  - <span data-ttu-id="d3adc-178">사용자 개체에 특성이 있으면 Office 365와 동기화 되지만 Office 365에서는이 특성을 사용할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-178">If the attribute exists in the user object, it will be synchronized with Office 365, but Office 365 does not require or use it.</span></span>
    
- <span data-ttu-id="d3adc-179">**targetAddress**</span><span class="sxs-lookup"><span data-stu-id="d3adc-179">**targetAddress**</span></span>
    
    <span data-ttu-id="d3adc-180">사용자에 대해 채워지는 **targetAddress** 특성 (예: SMTP:tom@contoso.com)이 OFFICE 365 GAL에 나타나야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-180">It's required that the **targetAddress** attribute (for example, SMTP:tom@contoso.com) that's populated for the user must appear in the Office 365 GAL.</span></span> <span data-ttu-id="d3adc-181">타사 메시징 마이그레이션 시나리오에서이를 위해서는 AD DS에 대 한 Office 365 스키마 확장이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-181">In third-party messaging migration scenarios, this would require the Office 365 schema extension for the AD DS.</span></span> <span data-ttu-id="d3adc-182">또한 Office 365 스키마 확장은 AD DS에서 디렉터리 동기화 도구를 사용 하 여 채워지는 Office 365 개체를 관리 하는 데 유용한 다른 특성도 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-182">The Office 365 schema extension would also add other useful attributes to manage Office 365 objects that are populated by using a directory synchronization tool from AD DS.</span></span> <span data-ttu-id="d3adc-183">예를 들어, 숨겨진 사서함 또는 메일 그룹을 관리 하기 위한 **msExchHideFromAddressLists** 특성이 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-183">For example, the **msExchHideFromAddressLists** attribute to manage hidden mailboxes or distribution groups would be added.</span></span> 
   
  - <span data-ttu-id="d3adc-184">최대 문자 수: 256</span><span class="sxs-lookup"><span data-stu-id="d3adc-184">Maximum number of characters: 256</span></span>
  - <span data-ttu-id="d3adc-185">특성 값에는 공백이 없어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-185">The attribute value must not contain a space.</span></span>
  - <span data-ttu-id="d3adc-186">특성 값은 디렉터리 내에서 고유 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-186">The attribute value must be unique within the directory.</span></span>
  - <span data-ttu-id="d3adc-187">유효 하지 않은 문자 \< \> : \ (); , [ ] "</span><span class="sxs-lookup"><span data-stu-id="d3adc-187">Invalid characters: \ \< \> ( ) ; , [ ] "</span></span>
  - <span data-ttu-id="d3adc-188">모든 SMTP (Simple Mail Transport Protocol) 주소는 전자 메일 메시징 표준을 준수 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-188">All Simple Mail Transport Protocol (SMTP) addresses should comply with email messaging standards.</span></span>
    
- <span data-ttu-id="d3adc-189">**userPrincipalName**</span><span class="sxs-lookup"><span data-stu-id="d3adc-189">**userPrincipalName**</span></span>
    
  - <span data-ttu-id="d3adc-190">**UserPrincipalName** 특성은 사용자 이름 뒤에 @ 기호와 도메인 이름 (예: user@contoso.com)이 오는 인터넷 스타일 로그인 형식 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-190">The **userPrincipalName** attribute must be in the Internet-style sign-in format where the user name is followed by the at sign (@) and a domain name: for example, user@contoso.com.</span></span> <span data-ttu-id="d3adc-191">모든 SMTP (Simple Mail Transport Protocol) 주소는 전자 메일 메시징 표준을 준수 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-191">All Simple Mail Transport Protocol (SMTP) addresses should comply with email messaging standards.</span></span>
  - <span data-ttu-id="d3adc-192">**UserPrincipalName** 특성의 최대 문자 수는 113입니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-192">The maximum number of characters for the **userPrincipalName** attribute is 113.</span></span> <span data-ttu-id="d3adc-193">다음과 같이 @ 기호 앞 이나 뒤에 특정 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-193">A specific number of characters are permitted before and after the at sign (@), as follows:</span></span> 
  - <span data-ttu-id="d3adc-194">@ 기호 앞에 있는 사용자 이름의 최대 문자 수: 64</span><span class="sxs-lookup"><span data-stu-id="d3adc-194">Maximum number of characters for the username that is in front of the at sign (@): 64</span></span>
  - <span data-ttu-id="d3adc-195">@ 기호 뒤에 있는 도메인 이름의 최대 문자 수: 48</span><span class="sxs-lookup"><span data-stu-id="d3adc-195">Maximum number of characters for the domain name following the at sign (@): 48</span></span>
  - <span data-ttu-id="d3adc-196">유효 하지 않은 문자: &amp; \* \% +/=?</span><span class="sxs-lookup"><span data-stu-id="d3adc-196">Invalid characters: \ % &amp; \* + / = ?</span></span> <span data-ttu-id="d3adc-197">{ } | \< \> ( ) ; : , [ ] " '</span><span class="sxs-lookup"><span data-stu-id="d3adc-197"></span></span>
  - <span data-ttu-id="d3adc-198">움라우트도 잘못 된 문자입니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-198">An umlaut is also an invalid character.</span></span>
  - <span data-ttu-id="d3adc-199">@ 문자는 각 **userPrincipalName** 값에 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-199">The @ character is required in each **userPrincipalName** value.</span></span> 
  - <span data-ttu-id="d3adc-200">@ 문자는 각 **userPrincipalName** 값의 첫 번째 문자일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-200">The @ character cannot be the first character in each **userPrincipalName** value.</span></span> 
  - <span data-ttu-id="d3adc-201">사용자 이름은 마침표 (.), 앰퍼샌드 (&amp;), 공백 또는 @ 기호로 끝날 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-201">The username cannot end with a period (.), an ampersand (&amp;), a space, or an at sign (@).</span></span>
  - <span data-ttu-id="d3adc-202">사용자 이름에는 공백을 포함할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-202">The username cannot contain any spaces.</span></span>
  - <span data-ttu-id="d3adc-203">라우팅 가능한 도메인을 사용 해야 합니다. 예를 들어 로컬 또는 내부 도메인은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-203">Routable domains must be used; for example, local or internal domains cannot be used.</span></span>
  - <span data-ttu-id="d3adc-204">유니코드는 밑줄 문자로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-204">Unicode is converted to underscore characters.</span></span>
  - <span data-ttu-id="d3adc-205">**userPrincipalName** 는 디렉터리에 중복 된 값을 포함할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-205">**userPrincipalName** cannot contain any duplicate values in the directory.</span></span> 

<span data-ttu-id="d3adc-206">Idfix 도구를 사용 하 여 [디렉터리 특성 준비](prepare-directory-attributes-for-synch-with-idfix.md) 를 참조 하 여 AD DS의 특성에서 오류를 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-206">See [Prepare directory attributes with the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md) to use the IdFIx tool to identify errors in the attributes of your AD DS.</span></span>
    
## <a name="3-prepare-the-userprincipalname-attribute"></a><span data-ttu-id="d3adc-207">3. userPrincipalName 특성을 준비 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-207">3. Prepare the userPrincipalName attribute</span></span>

<span data-ttu-id="d3adc-208">Active Directory는 조직의 최종 사용자가 **sAMAccountName** 또는 **userPrincipalName**를 사용 하 여 디렉터리에 로그인 할 수 있도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-208">Active Directory is designed to allow the end users in your organization to sign in to your directory by using either **sAMAccountName** or **userPrincipalName**.</span></span> <span data-ttu-id="d3adc-209">마찬가지로 최종 사용자는 회사 또는 학교 계정의 UPN (사용자 계정 이름)을 사용 하 여 Office 365에 로그인 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-209">Similarly, end users can sign in to Office 365 by using the user principal name (UPN) of their work or school account.</span></span> <span data-ttu-id="d3adc-210">디렉터리 동기화는 AD DS에 있는 것과 동일한 UPN을 사용 하 여 Azure Active Directory에 새 사용자를 만들려고 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-210">Directory synchronization attempts to create new users in Azure Active Directory by using the same UPN that's in your AD DS.</span></span> <span data-ttu-id="d3adc-211">UPN은 전자 메일 주소와 같은 형식으로 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-211">The UPN is formatted like an email address.</span></span> 

<span data-ttu-id="d3adc-212">Office 365에서 UPN은 전자 메일 주소를 생성 하는 데 사용 되는 기본 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-212">In Office 365, the UPN is the default attribute that's used to generate the email address.</span></span> <span data-ttu-id="d3adc-213">**UserPrincipalName** (AD DS 및 Azure ad) 및 **proxyAddresses** 의 기본 전자 메일 주소를 다른 값으로 설정 하는 것이 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-213">It's easy to get **userPrincipalName** (in AD DS and in Azure AD) and the primary email address in **proxyAddresses** set to different values.</span></span> <span data-ttu-id="d3adc-214">서로 다른 값으로 설정 하면 관리자와 최종 사용자에 게 혼동이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-214">When they are set to different values, there can be confusion for administrators and end users.</span></span> 
  
<span data-ttu-id="d3adc-215">혼동을 줄이려면 이러한 특성을 맞추는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-215">It's best to align these attributes to reduce confusion.</span></span> <span data-ttu-id="d3adc-216">AD FS (Active Directory Federation Services) 2.0에서 single sign-on 요구 사항을 충족 하려면 Azure Active Directory 및 AD DS의 Upn이 일치 하며 유효한 도메인 네임 스페이스를 사용 하 고 있는지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-216">To meet the requirements of single sign-on with Active Directory Federation Services (AD FS) 2.0, you need to ensure that the UPNs in Azure Active Directory and your AD DS match and are using a valid domain namespace.</span></span>
  
## <a name="4-add-an-alternative-upn-suffix-to-ad-ds"></a><span data-ttu-id="d3adc-217">4. AD DS에 대체 UPN 접미사 추가</span><span class="sxs-lookup"><span data-stu-id="d3adc-217">4. Add an alternative UPN suffix to AD DS</span></span>

<span data-ttu-id="d3adc-218">사용자의 회사 자격 증명을 Office 365 환경에 연결 하기 위해 대체 UPN 접미사를 추가 해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-218">You may need to add an alternative UPN suffix to associate the user's corporate credentials with the Office 365 environment.</span></span> <span data-ttu-id="d3adc-219">UPN 접미사는 UPN에서 @ 문자 오른쪽에 있는 부분입니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-219">A UPN suffix is the part of a UPN to the right of the @ character.</span></span> <span data-ttu-id="d3adc-220">Single Sign-On에 사용되는 UPN에는 문자, 숫자, 마침표, 대시 및 밑줄을 포함할 수 있으며 다른 유형의 문자는 포함할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-220">UPNs that are used for single sign-on can contain letters, numbers, periods, dashes, and underscores, but no other types of characters.</span></span>
  
<span data-ttu-id="d3adc-221">Active Directory에 대체 UPN 접미사를 추가 하는 방법에 대 한 자세한 내용은 [디렉터리 동기화 준비]( https://go.microsoft.com/fwlink/p/?LinkId=525430)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d3adc-221">For more information on how to add an alternative UPN suffix to Active Directory, see [Prepare for directory synchronization]( https://go.microsoft.com/fwlink/p/?LinkId=525430).</span></span>
  
## <a name="5-match-the-ad-ds-upn-with-the-office-365-upn"></a><span data-ttu-id="d3adc-222">5. AD DS UPN과 Office 365 UPN 일치</span><span class="sxs-lookup"><span data-stu-id="d3adc-222">5. Match the AD DS UPN with the Office 365 UPN</span></span>

<span data-ttu-id="d3adc-223">디렉터리 동기화를 이미 설정한 경우 Office 365에 대 한 사용자의 UPN이 AD DS에 정의 된 사용자의 AD DS UPN과 일치 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-223">If you've already set up directory synchronization, the user's UPN for Office 365 may not match the user's AD DS UPN that's defined in your AD DS.</span></span> <span data-ttu-id="d3adc-224">도메인이 확인되기 전에 사용자에게 라이선스가 할당된 경우 이와 같은 문제가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-224">This can occur when a user was assigned a license before the domain was verified.</span></span> <span data-ttu-id="d3adc-225">이 문제를 해결 하려면 [PowerShell을](https://go.microsoft.com/fwlink/p/?LinkId=396730) 사용 하 여 중복 UPN을 수정 하 여 OFFICE 365 UPN이 회사 사용자 이름 및 도메인과 일치 하도록 사용자의 upn을 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-225">To fix this, use [PowerShell to fix duplicate UPN](https://go.microsoft.com/fwlink/p/?LinkId=396730) to update the user's UPN to ensure that the Office 365 UPN matches the corporate user name and domain.</span></span> <span data-ttu-id="d3adc-226">AD DS에서 UPN을 업데이트 하 고 Azure Active Directory id와 동기화 하 고 싶은 경우 AD DS에서 변경 작업을 수행 하기 전에 Office 365에서 사용자의 라이선스를 제거 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3adc-226">If you are updating the UPN in the AD DS and would like it to synchronize with the Azure Active Directory identity, you need to remove the user's license in Office 365 prior to making the changes in AD DS.</span></span> 
  
<span data-ttu-id="d3adc-227">또한 [디렉터리 동기화를 위해 라우팅할 수 없는 도메인 (예: 로컬 도메인)을 준비 하는 방법을](prepare-a-non-routable-domain-for-directory-synchronization.md)참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d3adc-227">Also see [How to prepare a non-routable domain (such as .local domain) for directory synchronization](prepare-a-non-routable-domain-for-directory-synchronization.md).</span></span>


## <a name="next-steps"></a><span data-ttu-id="d3adc-228">다음 단계</span><span class="sxs-lookup"><span data-stu-id="d3adc-228">Next steps</span></span>

<span data-ttu-id="d3adc-229">디렉터리 동기화 전에 AD DS 특성의 오류를 수정 하는 데 도움이 되도록 [IdFix 도구를 사용 하 여 디렉터리 특성 준비](prepare-directory-attributes-for-synch-with-idfix.md) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d3adc-229">See [Prepare directory attributes with the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md) to help you correct errors in the attributes of your AD DS prior to directory synchronization.</span></span>

<span data-ttu-id="d3adc-230">IdFix 도구로 식별 된 모든 특성 오류를 수정 하 고 위의 1 ~ 5 단계를 수행한 경우 [디렉터리 동기화 설정을](set-up-directory-synchronization.md)참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="d3adc-230">If you have corrected all the attribute errors identified with the IdFix tool and have done steps 1 through 5 above, see [Set up directory synchronization](set-up-directory-synchronization.md).</span></span>
