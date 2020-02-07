---
title: 디렉터리 동기화를 위해 라우팅할 수 없는 도메인 준비
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365E_SetupDirSyncLocalDir
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: e7968303-c234-46c4-b8b0-b5c93c6d57a7
description: Office 365와 동기화 하기 전에 온-프레미스 사용자와 연결 된 routale 도메인이 있는 경우 수행 해야 하는 작업에 대해 알아봅니다.
ms.openlocfilehash: 10ec92ff19bd5e74363bced9a2f29c356c7fa4e8
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841225"
---
# <a name="prepare-a-non-routable-domain-for-directory-synchronization"></a><span data-ttu-id="78d9f-103">디렉터리 동기화를 위해 라우팅할 수 없는 도메인 준비</span><span class="sxs-lookup"><span data-stu-id="78d9f-103">Prepare a non-routable domain for directory synchronization</span></span>
<span data-ttu-id="78d9f-104">온-프레미스 디렉터리를 Office 365와 동기화 하는 경우 Azure Active Directory에 확인 된 도메인이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="78d9f-104">When you synchronize your on-premises directory with Office 365 you have to have a verified domain in Azure Active Directory.</span></span> <span data-ttu-id="78d9f-105">온-프레미스 도메인과 연결 된 UPN (사용자 계정 이름)만 동기화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="78d9f-105">Only the User Principal Names (UPN) that are associated with the on-premises domain are synchronized.</span></span> <span data-ttu-id="78d9f-106">하지만 예를 들어 라우팅할 수 없는 도메인을 포함 하는 UPN은 billa@contoso와 마찬가지로 billa@contoso.onmicrosoft.com와 같은 onmicrosoft.com 도메인에 동기화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="78d9f-106">However, any UPN that contains an non-routable domain, for example .local (like billa@contoso.local), will be synchronized to an .onmicrosoft.com domain (like billa@contoso.onmicrosoft.com).</span></span> 

<span data-ttu-id="78d9f-107">현재 Active Directory의 사용자 계정에 대해 로컬 도메인을 사용 하는 경우 Office 365 도메인과 올바르게 동기화 하기 위해 확인 된 도메인 (예 billa@contoso.com)을 사용 하도록 변경 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="78d9f-107">If you currently use a .local domain for your user accounts in Active Directory it's recommended that you change them to use a verified domain (like billa@contoso.com) in order to properly sync with your Office 365 domain.</span></span>
  
## <a name="what-if-i-only-have-a-local-on-premises-domain"></a><span data-ttu-id="78d9f-108">로컬 온-프레미스 도메인만 있는 경우에는 어떻게 하나요?</span><span class="sxs-lookup"><span data-stu-id="78d9f-108">What if I only have a .local on-premises domain?</span></span>

<span data-ttu-id="78d9f-109">Active Directory를 Azure Active Directory와 동기화 하는 데 사용할 수 있는 가장 최근 도구를 Azure AD Connect 라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="78d9f-109">The most recent tool you can use for synchronizing your Active Directory to Azure Active Directory is named Azure AD Connect.</span></span> <span data-ttu-id="78d9f-110">자세한 내용은 [Azure Active Directory에 온-프레미스 ID 통합](https://docs.microsoft.com/azure/architecture/reference-architectures/identity/azure-ad).</span><span class="sxs-lookup"><span data-stu-id="78d9f-110">For more information, see [Integrating your on-premises identities with Azure Active Directory](https://docs.microsoft.com/azure/architecture/reference-architectures/identity/azure-ad).</span></span>
  
<span data-ttu-id="78d9f-111">Azure AD Connect 사용자가 온-프레미스에서 사용 하는 것과 동일한 자격 증명으로 로그인 할 수 있도록 사용자의 UPN과 암호를 동기화 합니다.</span><span class="sxs-lookup"><span data-stu-id="78d9f-111">Azure AD Connect synchronizes your users' UPN and password so that users can sign in with the same credentials they use on-premises.</span></span> <span data-ttu-id="78d9f-112">그러나 Azure AD Connect는 사용자를 Office 365에서 확인 된 도메인으로 동기화 합니다.</span><span class="sxs-lookup"><span data-stu-id="78d9f-112">However, Azure AD Connect only synchronizes users to domains that are verified by Office 365.</span></span> <span data-ttu-id="78d9f-113">이는 Office 365 id가 Azure Active Directory에서 관리 되므로 Azure Active Directory에서 도메인을 확인 한다는 것을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="78d9f-113">This means that the domain also is verified by Azure Active Directory because Office 365 identities are managed by Azure Active Directory.</span></span> <span data-ttu-id="78d9f-114">즉, 도메인은 유효한 인터넷 도메인 (예: .com, org, .net, 미국 등) 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="78d9f-114">In other words, the domain has to be a valid Internet domain (for example, .com, .org, .net, .us, etc.).</span></span> <span data-ttu-id="78d9f-115">내부 Active Directory에서 라우팅할 수 없는 도메인 (예: .local)을 사용 하는 경우이는 Office 365에 있는 확인 된 도메인과 일치할 수도 없습니다.</span><span class="sxs-lookup"><span data-stu-id="78d9f-115">If your internal Active Directory only uses a non-routable domain (for example, .local), this can't possibly match the verified domain you have on Office 365.</span></span> <span data-ttu-id="78d9f-116">온-프레미스 Active Directory에서 주 도메인을 변경 하거나 하나 이상의 UPN 접미사를 추가 하 여이 문제를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78d9f-116">You can fix this issue by either changing your primary domain in your on premises Active Directory, or by adding one or more UPN suffixes.</span></span>
  
### <a name="change-your-primary-domain"></a><span data-ttu-id="78d9f-117">**주 도메인 변경**</span><span class="sxs-lookup"><span data-stu-id="78d9f-117">**Change your primary domain**</span></span>

<span data-ttu-id="78d9f-118">기본 도메인을 Office 365에서 확인 한 도메인 (예: contoso.com)으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="78d9f-118">Change your primary domain to a domain you have verified in Office 365, for example, contoso.com.</span></span> <span data-ttu-id="78d9f-119">그런 다음 contoso.com으로 업데이트 되는 contoso 라는 도메인이 있는 모든 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="78d9f-119">Every user that has the domain contoso.local is then updated to contoso.com.</span></span> <span data-ttu-id="78d9f-120">자세한 내용은 [도메인 이름 바꾸기 작동 방법을](https://go.microsoft.com/fwlink/p/?LinkId=624174)참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="78d9f-120">For instructions, see [How Domain Rename Works](https://go.microsoft.com/fwlink/p/?LinkId=624174).</span></span> <span data-ttu-id="78d9f-121">이는 매우 관련이 있는 프로세스 이며, 다음 섹션에서 보다 쉬운 솔루션을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="78d9f-121">This is a very involved process, however, and an easier solution is described in the following section.</span></span>
  
### <a name="add-upn-suffixes-and-update-your-users-to-them"></a><span data-ttu-id="78d9f-122">**UPN 접미사를 추가 하 고 사용자를 업데이트 합니다.**</span><span class="sxs-lookup"><span data-stu-id="78d9f-122">**Add UPN suffixes and update your users to them**</span></span>

<span data-ttu-id="78d9f-123">Active Directory의 새 UPN 접미사 또는 접미사를 Office 365에서 확인 한 도메인 (또는 도메인)과 일치 시켜이 문제를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78d9f-123">You can solve the .local problem by registering new UPN suffix or suffixes in Active Directory to match the domain (or domains) you verified in Office 365.</span></span> <span data-ttu-id="78d9f-124">새 접미사를 등록 한 후에는 사용자 Upn을 새 도메인 이름 (예: billa@contoso.com으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="78d9f-124">After you register the new suffix, you update the user UPNs to replace the .local with the new domain name for example so that a user account looks like billa@contoso.com.</span></span>
  
<span data-ttu-id="78d9f-125">확인 된 도메인을 사용 하도록 Upn을 업데이트 한 후에는 온-프레미스 Active Directory를 Office 365과 동기화 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78d9f-125">After you have updated the UPNs to use the verified domain,you are ready to synchronize your on-premises Active Directory with Office 365.</span></span>
  
 <span data-ttu-id="78d9f-126">**1 단계: 새 UPN 접미사 추가**</span><span class="sxs-lookup"><span data-stu-id="78d9f-126">**Step 1: Add the new UPN suffix**</span></span>
  
1. <span data-ttu-id="78d9f-127">AD DS (Active directory 도메인 서비스)가 실행 되는 서버의 서버 관리자에서 **도구** \> **Active Directory 도메인 및 트러스트**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="78d9f-127">On the server that Active Directory Domain Services (AD DS) runs on, in the Server Manager choose **Tools** \> **Active Directory Domains and Trusts**.</span></span>
    
    <span data-ttu-id="78d9f-128">**또는 Windows Server 2012이 없는 경우**</span><span class="sxs-lookup"><span data-stu-id="78d9f-128">**Or, if you don't have Windows Server 2012**</span></span>
    
    <span data-ttu-id="78d9f-129">**Windows 키 + R** 을 눌러 **실행** 대화 상자를 열고 도메인 .msc를 입력 한 다음 **확인**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="78d9f-129">Press **Windows key + R** to open the **Run** dialog, and then type in Domain.msc, and then choose **OK**.</span></span>
    
    ![Active Directory 도메인 및 트러스트를 선택 합니다.](media/46b6e007-9741-44af-8517-6f682e0ac974.png)
  
2. <span data-ttu-id="78d9f-131">**Active Directory 도메인 및 트러스트** 창에서 **active Directory 도메인 및 트러스트**를 마우스 오른쪽 단추로 클릭 한 다음 **속성**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="78d9f-131">On the **Active Directory Domains and Trusts** window, right-click **Active Directory Domains and Trusts**, and then choose **Properties**.</span></span>
    
    ![ActiveDirectory 도메인 및 트러스트를 마우스 오른쪽 단추로 클릭 하 고 속성을 선택 합니다.](media/39d20812-ffb5-4ba9-8d7b-477377ac360d.png)
  
3. <span data-ttu-id="78d9f-133">**Upn 접미사** 탭의 **대체 UPN 접미사** 상자에 새 upn 접미사 또는 접미사를 입력 한 다음 **적용** **추가** \> 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="78d9f-133">On the **UPN Suffixes** tab, in the **Alternative UPN Suffixes** box, type your new UPN suffix or suffixes, and then choose **Add** \> **Apply**.</span></span>
    
    ![새 UPN 접미사 추가](media/a4aaf919-7adf-469a-b93f-83ef284c0915.PNG)
  
    <span data-ttu-id="78d9f-135">접미사 추가가 완료 되 면 **확인을** 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="78d9f-135">Choose **OK** when you're done adding suffixes.</span></span> 
    
 <span data-ttu-id="78d9f-136">**2 단계: 기존 사용자에 대 한 UPN 접미사 변경**</span><span class="sxs-lookup"><span data-stu-id="78d9f-136">**Step 2: Change the UPN suffix for existing users**</span></span>
  
1. <span data-ttu-id="78d9f-137">AD DS (Active Directory 도메인 서비스)가 실행 되는 서버의 서버 관리자에서 **도구** \> **active directory active directory 사용자 및 컴퓨터**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="78d9f-137">On the server that Active Directory Domain Services (AD DS) runs on, in the Server Manager choose **Tools** \> **Active Directory Active Directory Users and Computers**.</span></span>
    
    <span data-ttu-id="78d9f-138">**또는 Windows Server 2012이 없는 경우**</span><span class="sxs-lookup"><span data-stu-id="78d9f-138">**Or, if you don't have Windows Server 2012**</span></span>
    
    <span data-ttu-id="78d9f-139">**Windows 키 + R** 을 눌러 **실행** 대화 상자를 연 다음 dsa.msc를 입력 하 고 **확인** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="78d9f-139">Press **Windows key + R** to open the **Run** dialog, and then type in Dsa.msc, and then click **OK**</span></span>
    
2. <span data-ttu-id="78d9f-140">사용자를 선택 하 고 마우스 오른쪽 단추를 클릭 한 다음 **속성**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="78d9f-140">Select a user, right-click, and then choose **Properties**.</span></span>
    
3. <span data-ttu-id="78d9f-141">**계정** 탭의 UPN 접미사 드롭다운 목록에서 새 UPN 접미사를 선택한 다음 **확인**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="78d9f-141">On the **Account** tab, in the UPN suffix drop-down list, choose the new UPN suffix, and then choose **OK**.</span></span>
    
    ![사용자에 대해 새 UPN 접미사 추가](media/54876751-49f0-48cc-b864-2623c4835563.png)
  
4. <span data-ttu-id="78d9f-143">모든 사용자에 대해이 단계를 완료 합니다.</span><span class="sxs-lookup"><span data-stu-id="78d9f-143">Complete these steps for every user.</span></span>
    
   
### <a name="you-can-also-use-windows-powershell-to-change-the-upn-suffix-for-all-users"></a><span data-ttu-id="78d9f-144">**Windows PowerShell을 사용 하 여 모든 사용자에 대 한 UPN 접미사를 변경할 수도 있습니다.**</span><span class="sxs-lookup"><span data-stu-id="78d9f-144">**You can also use Windows PowerShell to change the UPN suffix for all users**</span></span>

<span data-ttu-id="78d9f-145">업데이트 해야 하는 사용자가 많은 경우에는 Windows PowerShell을 사용 하는 것이 더 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="78d9f-145">If you have a lot of users to update, it is easier to use Windows PowerShell.</span></span> <span data-ttu-id="78d9f-146">다음 예에서는 [contoso.com cmdlet을](https://go.microsoft.com/fwlink/p/?LinkId=624312) [사용 하 여](https://go.microsoft.com/fwlink/p/?LinkId=624313) 모든 contoso 접미사를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="78d9f-146">The following example uses the cmdlets [Get-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624312) and [Set-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624313) to change all contoso.local suffixes to contoso.com.</span></span> 

<span data-ttu-id="78d9f-147">다음 Windows PowerShell 명령을 실행 하 여 모든 contoso 접미사를 contoso.com로 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="78d9f-147">Run the following Windows PowerShell commands to update all contoso.local suffixes to contoso.com:</span></span>
    
  ```powershell
  $LocalUsers = Get-ADUser -Filter {UserPrincipalName -like '*contoso.local'} -Properties userPrincipalName -ResultSetSize $null
  $LocalUsers | foreach {$newUpn = $_.UserPrincipalName.Replace("contoso.local","contoso.com"); $_ | Set-ADUser -UserPrincipalName $newUpn}
  ```

<span data-ttu-id="78d9f-148">Active directory에서 Windows PowerShell을 사용 하는 방법에 대해 자세히 알아보려면 [Active Directory Windows powershell 모듈](https://go.microsoft.com/fwlink/p/?LinkId=624314) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="78d9f-148">See [Active Directory Windows PowerShell module](https://go.microsoft.com/fwlink/p/?LinkId=624314) to learn more about using Windows PowerShell in Active Directory.</span></span> 

