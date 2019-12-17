---
title: Office 365 id 모델 및 Azure Active Directory
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.date: 05/20/2019
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-identity-device-management
- M365-security-compliance
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 06a189e7-5ec6-4af2-94bf-a22ea225a7a9
description: Office 365에서 사용자 id가 관리 되는 방식을 알아봅니다.
ms.openlocfilehash: 0cc40323d978fe9ab13e3326dac183143a014406
ms.sourcegitcommit: 3539ec707f984de6f3b874744ff8b6832fbd665e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/17/2019
ms.locfileid: "40071880"
---
# <a name="office-365-identity-models-and-azure-active-directory"></a><span data-ttu-id="3cace-103">Office 365 id 모델 및 Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="3cace-103">Office 365 identity models and Azure Active Directory</span></span>

<span data-ttu-id="3cace-104">*이 문서는 Microsoft 365 Enterprise와 Office 365 Enterprise에 모두 적용됩니다.*</span><span class="sxs-lookup"><span data-stu-id="3cace-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="3cace-105">Office 365에서는 office 365 구독에 포함 되어 있는 Azure Active Directory (Azure AD), 클라우드 기반 사용자 id 및 인증 서비스를 사용 하 여 office 365에 대 한 id 및 인증을 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cace-105">Office 365 uses Azure Active Directory (Azure AD), a cloud-based user identity and authentication service that is included with your Office 365 subscription, to manage identities and authentication for Office 365.</span></span> <span data-ttu-id="3cace-106">조직에 대 한 Office 365 사용자 액세스 및 사용 권한을 관리 하려면 id 인프라를 올바르게 구성 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cace-106">Getting your identity infrastructure configured correctly is vital to managing Office 365 user access and permissions for your organization.</span></span>

<span data-ttu-id="3cace-107">시작 하기 전에이 비디오에서 Office 365 및 Microsoft 365에 대 한 id 모델 및 인증에 대 한 개요를 시청 하세요.</span><span class="sxs-lookup"><span data-stu-id="3cace-107">Before you begin, watch this video for an overview of identity models and authentication for both Office 365 and Microsoft 365.</span></span>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE2Pjwu]

<span data-ttu-id="3cace-108">첫 번째 계획 선택은 Office 365 id 모델입니다.</span><span class="sxs-lookup"><span data-stu-id="3cace-108">Your first planning choice is the Office 365 identity model.</span></span>

## <a name="office-365-identity-models"></a><span data-ttu-id="3cace-109">Office 365 id 모델</span><span class="sxs-lookup"><span data-stu-id="3cace-109">Office 365 identity models</span></span>

<span data-ttu-id="3cace-110">사용자 계정을 계획 하려면 먼저 Microsoft 365에서 두 가지 id 모델을 이해 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cace-110">To plan for user accounts, you first need to understand the two identity models in Microsoft 365.</span></span> <span data-ttu-id="3cace-111">조직의 id는 클라우드에서만 유지 관리할 수 있으며, 사용자가 Microsoft 365 클라우드 서비스에 액세스할 때 온-프레미스 AD DS (Active Directory 도메인 서비스) id를 유지 관리 하 고 인증에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3cace-111">You can maintain your organization's identities only in the cloud, or you can maintain your on-premises Active Directory Domain Services (AD DS) identities and use them for authentication when users access Microsoft 365 cloud services.</span></span>  

<span data-ttu-id="3cace-112">다음은 두 가지 유형의 id와 가장 적합 한 일치 및 장점입니다.</span><span class="sxs-lookup"><span data-stu-id="3cace-112">Here are the two types of identity and their best fit and benefits.</span></span>

|||
|:-------|:-----|:-----|
|  | <span data-ttu-id="3cace-113">**클라우드 전용 id**</span><span class="sxs-lookup"><span data-stu-id="3cace-113">**Cloud-only identity**</span></span> | <span data-ttu-id="3cace-114">**하이브리드 ID**</span><span class="sxs-lookup"><span data-stu-id="3cace-114">**Hybrid identity**</span></span> |
| <span data-ttu-id="3cace-115">**정의**</span><span class="sxs-lookup"><span data-stu-id="3cace-115">**Definition**</span></span> | <span data-ttu-id="3cace-116">사용자 계정이 Microsoft 365 구독의 azure AD (Active Directory) 테 넌 트에만 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3cace-116">User account only exists in the Azure Active Directory (Azure AD) tenant for your Microsoft 365 subscription.</span></span> | <span data-ttu-id="3cace-117">사용자 계정이 AD DS에 있고 복사본은 Microsoft 365 구독의 Azure AD 테 넌 트에도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3cace-117">User account exists in AD DS and a copy is also in the Azure AD tenant for your Microsoft 365 subscription.</span></span> <span data-ttu-id="3cace-118">또한 Azure AD의 사용자 계정에는 사용자 계정 암호의 해시 된 버전을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3cace-118">The user account in Azure AD might also include a hashed version of the user account password.</span></span> |
| <span data-ttu-id="3cace-119">**Microsoft 365에서 사용자 자격 증명을 인증 하는 방법**</span><span class="sxs-lookup"><span data-stu-id="3cace-119">**How Microsoft 365 authenticates user credentials**</span></span> | <span data-ttu-id="3cace-120">Microsoft 365 구독의 Azure AD 테 넌 트는 클라우드 id 계정을 사용 하 여 인증을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cace-120">The Azure AD tenant for your Microsoft 365 subscription performs the authentication with the cloud identity account.</span></span> | <span data-ttu-id="3cace-121">Microsoft 365 구독에 대 한 Azure AD 테 넌 트가 인증 프로세스를 처리 하거나 사용자를 다른 id 공급자로 리디렉션합니다.</span><span class="sxs-lookup"><span data-stu-id="3cace-121">The Azure AD tenant for your Microsoft 365 subscription either handles the authentication process or redirects the user to another identity provider.</span></span> |
| <span data-ttu-id="3cace-122">**최적 시나리오**</span><span class="sxs-lookup"><span data-stu-id="3cace-122">**Best for**</span></span> | <span data-ttu-id="3cace-123">온-프레미스 AD DS가 없거나 필요 하지 않은 조직</span><span class="sxs-lookup"><span data-stu-id="3cace-123">Organizations that do not have or need an on-premises AD DS.</span></span> | <span data-ttu-id="3cace-124">AD DS 또는 다른 id 공급자를 사용 하는 조직</span><span class="sxs-lookup"><span data-stu-id="3cace-124">Organizations using AD DS or another identity provider.</span></span> |
| <span data-ttu-id="3cace-125">**가장 큰 혜택**</span><span class="sxs-lookup"><span data-stu-id="3cace-125">**Greatest benefit**</span></span> | <span data-ttu-id="3cace-126">간편 하 게 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3cace-126">Simple to use.</span></span> <span data-ttu-id="3cace-127">추가 디렉터리 도구 또는 서버가 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3cace-127">No extra directory tools or servers required.</span></span> | <span data-ttu-id="3cace-128">사용자는 온-프레미스 또는 클라우드 기반 리소스에 액세스할 때 동일한 자격 증명을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3cace-128">Users can use the same credentials when accessing on-premises or cloud-based resources.</span></span> |
||||

## <a name="cloud-only-identity"></a><span data-ttu-id="3cace-129">클라우드 전용 id</span><span class="sxs-lookup"><span data-stu-id="3cace-129">Cloud-only identity</span></span>

<span data-ttu-id="3cace-130">클라우드 전용 id는 Azure AD에만 있는 사용자 계정을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cace-130">A cloud-only identity uses user accounts that exist only in Azure AD.</span></span> <span data-ttu-id="3cace-131">클라우드 id는 일반적으로 온-프레미스 서버가 없거나 AD DS를 사용 하 여 로컬 id를 관리 하지 않는 소규모 조직에서 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3cace-131">Cloud identity is typically used by small organizations that do not have on-premises servers or do not use AD DS to manage local identities.</span></span> 

<span data-ttu-id="3cace-132">다음은 클라우드 전용 id의 기본 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="3cace-132">Here are the basic components of cloud-only identity.</span></span>
 
![클라우드 전용 id의 기본 구성 요소](./media/about-office-365-identity/cloud-only-identity.png)

<span data-ttu-id="3cace-134">온-프레미스 및 원격 (온라인)은 모두 Azure AD 사용자 계정 및 암호를 사용 하 여 Office 365 클라우드 서비스에 액세스 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cace-134">Both on-premises and remote (online) users use their Azure AD user accounts and passwords to access Office 365 cloud services.</span></span> <span data-ttu-id="3cace-135">Azure AD는 저장 된 사용자 계정 및 암호를 기반으로 사용자 자격 증명을 인증 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cace-135">Azure AD authenticates user credentials based on its stored user accounts and passwords.</span></span>

### <a name="administration"></a><span data-ttu-id="3cace-136">관리</span><span class="sxs-lookup"><span data-stu-id="3cace-136">Administration</span></span>
<span data-ttu-id="3cace-137">사용자 계정은 Azure AD에만 저장 되므로 Graph 모듈에 대 한 Azure Active Directory PowerShell을 사용 하 여 [Microsoft 365 관리 센터](https://admin.microsoft.com) 및 Windows PowerShell과 같은 도구를 사용 하 여 클라우드 id를 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cace-137">Because user accounts are only stored in Azure AD, you manage cloud identities with tools such as the [Microsoft 365 admin center](https://admin.microsoft.com) and Windows PowerShell with the Azure Active Directory PowerShell for Graph module.</span></span> 

## <a name="hybrid-identity"></a><span data-ttu-id="3cace-138">하이브리드 ID</span><span class="sxs-lookup"><span data-stu-id="3cace-138">Hybrid identity</span></span>

<span data-ttu-id="3cace-139">하이브리드 id는 온-프레미스 AD DS에서 시작 되 고 Microsoft 365 구독의 Azure AD 테 넌 트에 복사본을 포함 하는 계정을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cace-139">Hybrid identity uses accounts that originate in an on-premises AD DS and have a copy in the Azure AD tenant of a Microsoft 365 subscription.</span></span> <span data-ttu-id="3cace-140">그러나 대부분의 변경 내용은 단방향 으로만 흐릅니다.</span><span class="sxs-lookup"><span data-stu-id="3cace-140">However, most changes only flow one way.</span></span> <span data-ttu-id="3cace-141">AD DS 사용자 계정에 대해 수행한 변경 내용이 Azure AD에서 해당 복사본에 동기화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3cace-141">Changes that you make to AD DS user accounts are synchronized to their copy in Azure AD.</span></span> <span data-ttu-id="3cace-142">그러나 새 사용자 계정과 같은 Azure AD의 클라우드 기반 계정에 대 한 변경 내용은 AD DS와 동기화 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3cace-142">But changes made to cloud-based accounts in Azure AD, such as new user accounts, are not synchronized with AD DS.</span></span>

<span data-ttu-id="3cace-143">Azure AD Connect는 진행 중인 계정 동기화를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cace-143">Azure AD Connect provides the ongoing account synchronization.</span></span> <span data-ttu-id="3cace-144">이 도구는 온-프레미스 서버에서 실행 되 고, AD DS의 변경 내용을 확인 하 고, 해당 변경 내용을 Azure AD로 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cace-144">It runs on an on-premises server, checks for changes in the AD DS, and forwards those changes to Azure AD.</span></span> <span data-ttu-id="3cace-145">Azure AD Connect는 동기화 되는 계정 및 해시 된 버전의 사용자 암호를 동기화 (암호 해시 동기화 (PHS)) 할지 여부를 필터링 하는 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cace-145">Azure AD Connect provides the ability to filter which accounts are synchronized and whether to synchronize a hashed version of user passwords, known as password hash synchronization (PHS).</span></span>

<span data-ttu-id="3cace-146">하이브리드 id를 구현 하는 경우 온-프레미스 AD DS가 계정 정보에 대 한 신뢰할 수 있는 원본입니다.</span><span class="sxs-lookup"><span data-stu-id="3cace-146">When you implement hybrid identity, your on-premises AD DS is the authoritative source for account information.</span></span> <span data-ttu-id="3cace-147">즉, 관리 작업을 주로 온-프레미스로 수행한 다음 Azure AD와 동기화 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cace-147">This means that you perform administration tasks mostly on-premises, which are then synchronized to Azure AD.</span></span> 

<span data-ttu-id="3cace-148">하이브리드 id의 구성 요소는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3cace-148">Here are the components of hybrid identity.</span></span>

![하이브리드 id의 구성 요소](./media/about-office-365-identity/hybrid-identity.png)

<span data-ttu-id="3cace-150">Azure AD 테 넌 트에는 AD DS 계정의 복사본이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3cace-150">The Azure AD tenant has a copy of the AD DS accounts.</span></span> <span data-ttu-id="3cace-151">이 구성에서 Microsoft 365 클라우드 서비스에 액세스 하는 온-프레미스 및 원격 사용자 둘 다 Azure AD에 대해 인증을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cace-151">In this configuration, both on-premises and remote users accessing Microsoft 365 cloud services authenticate against Azure AD.</span></span>

>[!Note]
><span data-ttu-id="3cace-152">하이브리드 id에 대해 사용자 계정을 동기화 하려면 항상 Azure AD Connect를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cace-152">You always need to use Azure AD Connect to synchronize user accounts for hybrid identity.</span></span> <span data-ttu-id="3cace-153">라이선스 할당 및 그룹 관리, 사용 권한 구성 및 사용자 계정을 포함 하는 기타 관리 작업을 수행 하려면 Azure AD에서 동기화 된 사용자 계정이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cace-153">You need the synchronized user accounts in Azure AD to perform license assignment and group management, configure permissions, and other administrative tasks that involve user accounts.</span></span>
>

### <a name="administration"></a><span data-ttu-id="3cace-154">관리</span><span class="sxs-lookup"><span data-stu-id="3cace-154">Administration</span></span>

<span data-ttu-id="3cace-155">원본 및 신뢰할 수 있는 사용자 계정이 온-프레미스 AD DS에 저장 되기 때문에 Active Directory 사용자 및 컴퓨터 도구와 같은 도구를 사용 하 여 AD DS와 동일한 도구로 id를 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cace-155">Because the original and authoritative user accounts are stored in the on-premises AD DS, you manage your identities with the same tools as AD DS, such as the Active Directory Users and Computers tool.</span></span> 

<span data-ttu-id="3cace-156">Microsoft 365 관리 센터 또는 Windows PowerShell을 사용 하 여 Azure AD에서 동기화 된 사용자 계정을 관리 하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3cace-156">You don’t use the Microsoft 365 admin center or Windows PowerShell to manage synchronized user accounts in Azure AD.</span></span>

## <a name="next-step"></a><span data-ttu-id="3cace-157">다음 단계</span><span class="sxs-lookup"><span data-stu-id="3cace-157">Next step</span></span>

<span data-ttu-id="3cace-158">클라우드 전용 id 모델이 필요한 경우 [클라우드 전용](cloud-only-identities.md)id를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3cace-158">If you need the cloud-only identity model, see [Cloud-only identities](cloud-only-identities.md).</span></span>

<span data-ttu-id="3cace-159">하이브리드 id 모델이 필요한 경우 [디렉터리 동기화](plan-for-directory-synchronization.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3cace-159">If you need the hybrid identity model, see [directory synchronization](plan-for-directory-synchronization.md).</span></span>
  

## <a name="video-training"></a><span data-ttu-id="3cace-160">동영상 교육</span><span class="sxs-lookup"><span data-stu-id="3cace-160">Video training</span></span>

<span data-ttu-id="3cace-161">LinkedIn 학습을 통해 가져온 [Office 365: AZURE AD Connect를 사용 하 여 Id 관리](https://support.office.com/article/90991a1d-c0ab-479a-b413-35c9706f6fed.aspx)코스를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3cace-161">See the video course [Office 365: Manage Identities Using Azure AD Connect](https://support.office.com/article/90991a1d-c0ab-479a-b413-35c9706f6fed.aspx), brought to you by LinkedIn Learning.</span></span>

## <a name="see-also"></a><span data-ttu-id="3cace-162">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3cace-162">See also</span></span>

[<span data-ttu-id="3cace-163">Microsoft 365 Enterprise 개요</span><span class="sxs-lookup"><span data-stu-id="3cace-163">Microsoft 365 Enterprise overview</span></span>](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
