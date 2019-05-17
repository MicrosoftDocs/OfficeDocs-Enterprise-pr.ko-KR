---
title: Office 365 id 모델 및 Azure Active Directory
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
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
ms.openlocfilehash: cd7fb1db2d5372097f3da0e6a2521335d7933015
ms.sourcegitcommit: 47c6156c0038745103b71f44b2a3b103c62e5d6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/16/2019
ms.locfileid: "34102471"
---
# <a name="office-365-identity-models-and-azure-active-directory"></a><span data-ttu-id="8bc8d-103">Office 365 id 모델 및 Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="8bc8d-103">Office 365 identity models and Azure Active Directory</span></span>

<span data-ttu-id="8bc8d-104">Office 365에서는 office 365 구독에 포함 되어 있는 Azure Active Directory (Azure AD), 클라우드 기반 사용자 id 및 인증 서비스를 사용 하 여 office 365에 대 한 id 및 인증을 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bc8d-104">Office 365 uses Azure Active Directory (Azure AD), a cloud-based user identity and authentication service that is included with your Office 365 subscription, to manage identities and authentication for Office 365.</span></span> <span data-ttu-id="8bc8d-105">조직에 대 한 Office 365 사용자 액세스 및 사용 권한을 관리 하려면 id 인프라를 올바르게 구성 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bc8d-105">Getting your identity infrastructure configured correctly is vital to managing Office 365 user access and permissions for your organization.</span></span>

<span data-ttu-id="8bc8d-106">시작 하기 전에이 비디오에서 Office 365 및 Microsoft 365에 대 한 id 모델 및 인증에 대 한 개요를 시청 하세요.</span><span class="sxs-lookup"><span data-stu-id="8bc8d-106">Before you begin, watch this video for an overview of identity models and authentication for both Office 365 and Microsoft 365.</span></span>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE2Pjwu]

<span data-ttu-id="8bc8d-107">첫 번째 계획 선택은 Office 365 id 모델입니다.</span><span class="sxs-lookup"><span data-stu-id="8bc8d-107">Your first planning choice is the Office 365 identity model.</span></span>

## <a name="office-365-identity-models"></a><span data-ttu-id="8bc8d-108">Office 365 id 모델</span><span class="sxs-lookup"><span data-stu-id="8bc8d-108">Office 365 identity models</span></span>

<span data-ttu-id="8bc8d-109">사용자 계정을 계획 하려면 먼저 Microsoft 365에서 두 가지 id 모델을 이해 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bc8d-109">To plan for user accounts, you first need to understand the two identity models in Microsoft 365.</span></span> <span data-ttu-id="8bc8d-110">조직의 id는 클라우드에서만 유지 관리할 수 있으며, 사용자가 Microsoft 365 클라우드 서비스에 액세스할 때 온-프레미스 AD DS (Active Directory 도메인 서비스) id를 유지 관리 하 고 인증에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8bc8d-110">You can maintain your organization's identities only in the cloud, or you can maintain your on-premises Active Directory Domain Services (AD DS) identities and use them for authentication when users access Microsoft 365 cloud services.</span></span>  

<span data-ttu-id="8bc8d-111">다음은 두 가지 유형의 id와 가장 적합 한 일치 및 장점입니다.</span><span class="sxs-lookup"><span data-stu-id="8bc8d-111">Here are the two types of identity and their best fit and benefits.</span></span>

|||
|:-------|:-----|:-----|
|  | <span data-ttu-id="8bc8d-112">클라우드 전용 id</span><span class="sxs-lookup"><span data-stu-id="8bc8d-112">Cloud-only identity</span></span> | <span data-ttu-id="8bc8d-113">하이브리드 id</span><span class="sxs-lookup"><span data-stu-id="8bc8d-113">Hybrid identity</span></span> |
| <span data-ttu-id="8bc8d-114">정의</span><span class="sxs-lookup"><span data-stu-id="8bc8d-114">Definition</span></span> | <span data-ttu-id="8bc8d-115">사용자 계정이 Microsoft 365 구독의 azure AD (Active Directory) 테 넌 트에만 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8bc8d-115">User account only exists in the Azure Active Directory (Azure AD) tenant for your Microsoft 365 subscription.</span></span> | <span data-ttu-id="8bc8d-116">사용자 계정이 AD DS에 있고 복사본은 Microsoft 365 구독의 Azure AD 테 넌 트에도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8bc8d-116">User account exists in AD DS and a copy is also in the Azure AD tenant for your Microsoft 365 subscription.</span></span> <span data-ttu-id="8bc8d-117">또한 Azure AD의 사용자 계정에는 사용자 계정 암호의 해시 된 버전을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8bc8d-117">The user account in Azure AD might also include a hashed version of the user account password.</span></span> |
| <span data-ttu-id="8bc8d-118">Microsoft 365에서 사용자 자격 증명을 인증 하는 방법</span><span class="sxs-lookup"><span data-stu-id="8bc8d-118">How Microsoft 365 authenticates user credentials</span></span> | <span data-ttu-id="8bc8d-119">Microsoft 365 구독의 Azure AD 테 넌 트는 클라우드 id 계정을 사용 하 여 인증을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bc8d-119">The Azure AD tenant for your Microsoft 365 subscription performs the authentication with the cloud identity account.</span></span> | <span data-ttu-id="8bc8d-120">Microsoft 365 구독에 대 한 Azure AD 테 넌 트가 인증 프로세스를 처리 하거나 사용자를 다른 id 공급자로 리디렉션합니다.</span><span class="sxs-lookup"><span data-stu-id="8bc8d-120">The Azure AD tenant for your Microsoft 365 subscription either handles the authentication process or redirects the user to another identity provider.</span></span> |
| <span data-ttu-id="8bc8d-121">최적 ...</span><span class="sxs-lookup"><span data-stu-id="8bc8d-121">Best for…</span></span> | <span data-ttu-id="8bc8d-122">온-프레미스 AD DS가 없거나 필요 하지 않은 조직</span><span class="sxs-lookup"><span data-stu-id="8bc8d-122">Organizations that do not have or need an on-premises AD DS.</span></span> | <span data-ttu-id="8bc8d-123">AD DS 또는 다른 id 공급자를 사용 하는 조직</span><span class="sxs-lookup"><span data-stu-id="8bc8d-123">Organizations using AD DS or another identity provider.</span></span> |
| <span data-ttu-id="8bc8d-124">가장 큰 혜택</span><span class="sxs-lookup"><span data-stu-id="8bc8d-124">Greatest benefit</span></span> | <span data-ttu-id="8bc8d-125">간편 하 게 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8bc8d-125">Simple to use.</span></span> <span data-ttu-id="8bc8d-126">추가 디렉터리 도구 또는 서버가 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8bc8d-126">No extra directory tools or servers required.</span></span> | <span data-ttu-id="8bc8d-127">사용자는 온-프레미스 또는 클라우드 기반 리소스에 액세스할 때 동일한 자격 증명을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8bc8d-127">Users can use the same credentials when accessing on-premises or cloud-based resources.</span></span> |
||||

### <a name="cloud-only-identity"></a><span data-ttu-id="8bc8d-128">클라우드 전용 id</span><span class="sxs-lookup"><span data-stu-id="8bc8d-128">Cloud-only identity</span></span>

<span data-ttu-id="8bc8d-129">클라우드 전용 id는 Azure AD에만 있는 사용자 계정을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bc8d-129">A cloud-only identity uses user accounts that exist only in Azure AD.</span></span> <span data-ttu-id="8bc8d-130">클라우드 id는 일반적으로 온-프레미스 서버가 없거나 AD DS를 사용 하 여 로컬 id를 관리 하지 않는 소규모 조직에서 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8bc8d-130">Cloud identity is typically used by small organizations that do not have on-premises servers or do not use AD DS to manage local identities.</span></span> 

<span data-ttu-id="8bc8d-131">다음은 클라우드 전용 id의 기본 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="8bc8d-131">Here are the basic components of cloud-only identity.</span></span>
 
![](./media/about-office-365-identity/cloud-only-identity.png)

<span data-ttu-id="8bc8d-132">온-프레미스 및 원격 (온라인)은 모두 Azure AD 사용자 계정 및 암호를 사용 하 여 Office 365 클라우드 서비스에 액세스 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bc8d-132">Both on-premises and remote (online) users use their Azure AD user accounts and passwords to access Office 365 cloud services.</span></span> <span data-ttu-id="8bc8d-133">Azure AD는 저장 된 사용자 계정 및 암호를 기반으로 사용자 자격 증명을 인증 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bc8d-133">Azure AD authenticates user credentials based on its stored user accounts and passwords.</span></span>

#### <a name="administration"></a><span data-ttu-id="8bc8d-134">관리</span><span class="sxs-lookup"><span data-stu-id="8bc8d-134">Administration</span></span>
<span data-ttu-id="8bc8d-135">사용자 계정은 Azure AD에만 저장 되므로 Graph 모듈에 대 한 Azure Active Directory PowerShell을 사용 하 여 [Microsoft 365 관리 센터](https://admin.microsoft.com) 및 Windows PowerShell과 같은 도구를 사용 하 여 클라우드 id를 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bc8d-135">Because user accounts are only stored in Azure AD, you manage cloud identities with tools such as the [Microsoft 365 admin center](https://admin.microsoft.com) and Windows PowerShell with the Azure Active Directory PowerShell for Graph module.</span></span> 

## <a name="hybrid-identity"></a><span data-ttu-id="8bc8d-136">하이브리드 id</span><span class="sxs-lookup"><span data-stu-id="8bc8d-136">Hybrid identity</span></span>

<span data-ttu-id="8bc8d-137">하이브리드 id는 온-프레미스 AD DS에서 시작 되 고 Microsoft 365 구독의 Azure AD 테 넌 트에 복사본을 포함 하는 계정을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bc8d-137">Hybrid identity uses accounts that originate in an on-premises AD DS and have a copy in the Azure AD tenant of a Microsoft 365 subscription.</span></span> <span data-ttu-id="8bc8d-138">그러나 대부분의 변경 내용은 단방향 으로만 흐릅니다.</span><span class="sxs-lookup"><span data-stu-id="8bc8d-138">However, most changes only flow one way.</span></span> <span data-ttu-id="8bc8d-139">AD DS 사용자 계정에 대해 수행한 변경 내용이 Azure AD에서 해당 복사본에 동기화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8bc8d-139">Changes that you make to AD DS user accounts are synchronized to their copy in Azure AD.</span></span> <span data-ttu-id="8bc8d-140">그러나 새 사용자 계정과 같은 Azure AD의 클라우드 기반 계정에 대 한 변경 내용은 AD DS와 동기화 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8bc8d-140">But changes made to cloud-based accounts in Azure AD, such as new user accounts, are not synchronized with AD DS.</span></span>

<span data-ttu-id="8bc8d-141">Azure AD Connect는 진행 중인 계정 동기화를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bc8d-141">Azure AD Connect provides the ongoing account synchronization.</span></span> <span data-ttu-id="8bc8d-142">이 도구는 온-프레미스 서버에서 실행 되 고, AD DS의 변경 내용을 확인 하 고, 해당 변경 내용을 Azure AD로 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bc8d-142">It runs on an on-premises server, checks for changes in the AD DS, and forwards those changes to Azure AD.</span></span> <span data-ttu-id="8bc8d-143">Azure AD Connect는 동기화 되는 계정 및 해시 된 버전의 사용자 암호를 동기화 (암호 해시 동기화 (PHS)) 할지 여부를 필터링 하는 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bc8d-143">Azure AD Connect provides the ability to filter which accounts are synchronized and whether to synchronize a hashed version of user passwords, known as password hash synchronization (PHS).</span></span>

<span data-ttu-id="8bc8d-144">하이브리드 id를 구현 하는 경우 온-프레미스 AD DS가 계정 정보에 대 한 신뢰할 수 있는 원본입니다.</span><span class="sxs-lookup"><span data-stu-id="8bc8d-144">When you implement hybrid identity, your on-premises AD DS is the authoritative source for account information.</span></span> <span data-ttu-id="8bc8d-145">즉, 관리 작업을 주로 온-프레미스로 수행한 다음 Azure AD와 동기화 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bc8d-145">This means that you perform administration tasks mostly on-premises, which are then synchronized to Azure AD.</span></span> 

<span data-ttu-id="8bc8d-146">하이브리드 id의 구성 요소는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8bc8d-146">Here are the components of hybrid identity.</span></span>

![](./media/about-office-365-identity/hybrid-identity.png)

<span data-ttu-id="8bc8d-147">Azure AD 테 넌 트에는 AD DS 계정의 복사본이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8bc8d-147">The Azure AD tenant has a copy of the AD DS accounts.</span></span> <span data-ttu-id="8bc8d-148">이 구성에서 Microsoft 365 클라우드 서비스에 액세스 하는 온-프레미스 및 원격 사용자 둘 다 Azure AD에 대해 인증을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bc8d-148">In this configuration, both on-premises and remote users accessing Microsoft 365 cloud services authenticate against Azure AD.</span></span>

>[!Note]
><span data-ttu-id="8bc8d-149">하이브리드 id에 대해 사용자 계정을 동기화 하려면 항상 Azure AD Connect를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bc8d-149">You always need to use Azure AD Connect to synchronize user accounts for hybrid identity.</span></span> <span data-ttu-id="8bc8d-150">라이선스 할당 및 그룹 관리, 사용 권한 구성 및 사용자 계정을 포함 하는 기타 관리 작업을 수행 하려면 Azure AD에서 동기화 된 사용자 계정이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bc8d-150">You need the synchronized user accounts in Azure AD to perform license assignment and group management, configure permissions, and other administrative tasks that involve user accounts.</span></span>
>

#### <a name="administration"></a><span data-ttu-id="8bc8d-151">관리</span><span class="sxs-lookup"><span data-stu-id="8bc8d-151">Administration</span></span>

<span data-ttu-id="8bc8d-152">원본 및 신뢰할 수 있는 사용자 계정이 온-프레미스 AD DS에 저장 되기 때문에 Active Directory 사용자 및 컴퓨터 도구와 같은 도구를 사용 하 여 AD DS와 동일한 도구로 id를 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bc8d-152">Because the original and authoritative user accounts are stored in the on-premises AD DS, you manage your identities with the same tools as AD DS, such as the Active Directory Users and Computers tool.</span></span> 

<span data-ttu-id="8bc8d-153">Microsoft 365 관리 센터 또는 Windows PowerShell을 사용 하 여 Azure AD에서 동기화 된 사용자 계정을 관리 하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8bc8d-153">You don’t use the Microsoft 365 admin center or Windows PowerShell to manage synchronized user accounts in Azure AD.</span></span>


## <a name="next-step"></a><span data-ttu-id="8bc8d-154">다음 단계</span><span class="sxs-lookup"><span data-stu-id="8bc8d-154">Next step</span></span>

<span data-ttu-id="8bc8d-155">하이브리드 id 모델이 필요한 경우 [에는 동기화 된 id 및 인증 방법에 대 한 계획](plan-for-directory-synchronization.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8bc8d-155">If you need the hybrid identity model, see [planning for your synchronized identities and authentication methods](plan-for-directory-synchronization.md).</span></span>
  

## <a name="video-training"></a><span data-ttu-id="8bc8d-156">동영상 교육</span><span class="sxs-lookup"><span data-stu-id="8bc8d-156">Video training</span></span>

<span data-ttu-id="8bc8d-157">LinkedIn 학습을 통해 가져온 [Office 365: AZURE AD Connect를 사용 하 여 Id 관리](https://support.office.com/article/90991a1d-c0ab-479a-b413-35c9706f6fed.aspx)코스를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8bc8d-157">See the video course [Office 365: Manage Identities Using Azure AD Connect](https://support.office.com/article/90991a1d-c0ab-479a-b413-35c9706f6fed.aspx), brought to you by LinkedIn Learning.</span></span>
