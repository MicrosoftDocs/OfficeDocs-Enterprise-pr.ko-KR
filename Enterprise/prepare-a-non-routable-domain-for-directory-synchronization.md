---
title: 디렉터리 동기화를 위한 라우팅할 수 없는 도메인을 준비 합니다.
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: article
f1_keywords:
- O365E_SetupDirSyncLocalDir
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: e7968303-c234-46c4-b8b0-b5c93c6d57a7
description: Office 365와 동기화 하기 전에 온-프레미스 사용자와 연결 된 비 routale 도메인을 사용 하는 경우 취해야 할 조치에 대해 알아봅니다.
ms.openlocfilehash: 9ec96c34e1dc4a6c755ea97fce3f5f2a5ba21bb3
ms.sourcegitcommit: 9c493c4e18e83491d106c5e9bab55d1a89298879
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2018
ms.locfileid: "26674442"
---
# <a name="prepare-a-non-routable-domain-for-directory-synchronization"></a><span data-ttu-id="cc071-103">디렉터리 동기화를 위한 라우팅할 수 없는 도메인을 준비 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc071-103">Prepare a non-routable domain for directory synchronization</span></span>
<span data-ttu-id="cc071-p101">Office 365와 온-프레미스 디렉터리를 동기화 할 때 Azure Active Directory에서 확인 된 도메인을 포함 해야 합니다. 만 사용자 이름 (UPN) 온-프레미스 도메인 연관 된 동기화 됩니다. 에 있는 라우팅할 수 없는 도메인 (예: billa@contoso.local).local 같은 포함 된 모든 UPN를 동기화 하는 반면는. onmicrosoft.com 도메인 (예: billa@contoso.onmicrosoft.com).</span><span class="sxs-lookup"><span data-stu-id="cc071-p101">When you synchronize your on-premises directory with Office 365 you have to have a verified domain in Azure Active Directory. Only the User Principal Names (UPN) that are associated with the on-premises domain are synchronized. However, any UPN that contains an non-routable domain, for example .local (like billa@contoso.local), will be synchronized to an .onmicrosoft.com domain (like billa@contoso.onmicrosoft.com).</span></span> 

<span data-ttu-id="cc071-107">Active Directory에서 사용자 계정에 대 한 현재.local 도메인을 사용 하는 경우 Office 365 도메인 제대로 동기화 하기 위해 (예: billa@contoso.com) 확인 된 도메인을 사용 하도록 변경 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="cc071-107">If you currently use a .local domain for your user accounts in Active Directory it's recommended that you change them to use a verified domain (like billa@contoso.com) in order to properly sync with your Office 365 domain.</span></span>
  
## <a name="what-if-i-only-have-a-local-on-premises-domain"></a><span data-ttu-id="cc071-108">경우에 어떻게.local 온-프레미스 도메인만가?</span><span class="sxs-lookup"><span data-stu-id="cc071-108">What if I only have a .local on-premises domain?</span></span>

<span data-ttu-id="cc071-p102">Azure Active Directory에 Active Directory 동기화 (영문)에 대해 사용할 수 있는 가장 최근의 도구에는 Azure AD 연결 이라고 합니다. 자세한 내용은 [Azure Active Directory를 사용 하 여 온-프레미스 id가 통합 (영문)을](https://docs.microsoft.com/azure/architecture/reference-architectures/identity/azure-ad)참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="cc071-p102">The most recent tool you can use for synchronizing your Active Directory to Azure Active Directory is named Azure AD Connect. For more information, see [Integrating your on-premises identities with Azure Active Directory](https://docs.microsoft.com/azure/architecture/reference-architectures/identity/azure-ad).</span></span>
  
<span data-ttu-id="cc071-p103">사용자가 로그인 할 수 있도록 사용자의 UPN과 암호 동기화를 azure AD 연결 온-프레미스를 사용 하는 동일한 자격 증명으로 로그인 합니다. 그러나 Azure AD 연결 사용자가 Office 365에 의해 검증 된 도메인에만 동기화 합니다. 이 도메인도 확인 Azure Active Directory를 통해 Office 365 id가 Azure Active Directory에서 관리 되므로 것을 의미 합니다. 즉, 도메인은 유효한 인터넷 도메인 (예.com,.org,.net,.us 등) 이어야 합니다. 내부 Active Directory를 라우팅할 수 없는 도메인 (예:.local)에 사용 하 여,이 Office 365에 있는 확인 된 도메인과 일치 가능 수는 없습니다. 두 프로그램 온-프레미스 Active Directory에서에서 기본 도메인을 변경 하 여 또는 하나 이상의 UPN 접미사를 추가 하 여이 문제를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc071-p103">Azure AD Connect synchronizes your users' UPN and password so that users can sign in with the same credentials they use on-premises. However, Azure AD Connect only synchronizes users to domains that are verified by Office 365. This means that the domain also is verified by Azure Active Directory because Office 365 identities are managed by Azure Active Directory. In other words, the domain has to be a valid Internet domain (for example, .com, .org, .net, .us, etc.). If your internal Active Directory only uses a non-routable domain (for example, .local), this can't possibly match the verified domain you have on Office 365. You can fix this issue by either changing your primary domain in your on premises Active Directory, or by adding one or more UPN suffixes.</span></span>
  
### <a name="change-your-primary-domain"></a><span data-ttu-id="cc071-117">**기본 도메인을 변경 합니다.**</span><span class="sxs-lookup"><span data-stu-id="cc071-117">**Change your primary domain**</span></span>

<span data-ttu-id="cc071-p104">Office 365, 예: contoso.com에서에서 확인 한 도메인을 기본 도메인을 변경 합니다. 도메인 contoso.local 포함 된 모든 사용자가이 contoso.com으로 업데이트 됩니다. 자세한 내용은 [이름바꾸기 작동 방법 도메인을](https://go.microsoft.com/fwlink/p/?LinkId=624174)참조 하십시오. 그러나 이것은 매우 관련 된 프로세스 및를 보다 쉽게 솔루션 것 [추가 UPN 접미사 및 자신에 게 사용자를 업데이트](prepare-a-non-routable-domain-for-directory-synchronization.md#bk_register), 다음 섹션에 나와있는 것 처럼입니다.</span><span class="sxs-lookup"><span data-stu-id="cc071-p104">Change your primary domain to a domain you have verified in Office 365, for example, contoso.com. Every user that has the domain contoso.local is then updated to contoso.com. For instructions, see [How Domain Rename Works](https://go.microsoft.com/fwlink/p/?LinkId=624174). This is a very involved process, however, and an easier solution is to [Add UPN suffixes and update your users to them](prepare-a-non-routable-domain-for-directory-synchronization.md#bk_register), as shown in the following section.</span></span>
  
### <a name="add-upn-suffixes-and-update-your-users-to-them"></a><span data-ttu-id="cc071-122">**UPN 접미사를 추가 하 고 사용자에 게 자신에 게 업데이트**</span><span class="sxs-lookup"><span data-stu-id="cc071-122">**Add UPN suffixes and update your users to them**</span></span>

<span data-ttu-id="cc071-p105">.Local 문제를 해결할 수 도메인 (또는 도메인)와 일치 하도록 Active Directory에 새 UPN 접미사 또는 접미사를 등록 하 여 Office 365에서 확인 합니다. 새 접미사를 등록 한 후 사용자는 사용자 계정이 billa@contoso.com 처럼 표시 되도록는.local 예제에 대 한 새 도메인 이름으로 바꿉니다 Upn 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc071-p105">You can solve the .local problem by registering new UPN suffix or suffixes in Active Directory to match the domain (or domains) you verified in Office 365. After you register the new suffix, you update the user UPNs to replace the .local with the new domain name for example so that a user account looks like billa@contoso.com.</span></span>
  
<span data-ttu-id="cc071-125">확인 된 도메인을 사용 하 여 Upn을 업데이트 한 후 Office 365와 온-프레미스 Active Directory 동기화 준비가 된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="cc071-125">After you have updated the UPNs to use the verified domain,you are ready to synchronize your on-premises Active Directory with Office 365.</span></span>
  
 <span data-ttu-id="cc071-126">**1 단계: 새 UPN 접미사를 추가 합니다.**</span><span class="sxs-lookup"><span data-stu-id="cc071-126">**Step 1: Add the new UPN suffix**</span></span>
  
1. <span data-ttu-id="cc071-127">Active Directory 도메인 서비스 (AD DS)에서 실행 되는 서버의 서버 관리자에서 **도구** 를 선택 \> **Active Directory 도메인 및 트러스트**합니다.</span><span class="sxs-lookup"><span data-stu-id="cc071-127">On the server that Active Directory Domain Services (AD DS) runs on, in the Server Manager choose **Tools** \> **Active Directory Domains and Trusts**.</span></span>
    
    <span data-ttu-id="cc071-128">**또는 Windows Server 2012를 설치 하지 않은 경우**</span><span class="sxs-lookup"><span data-stu-id="cc071-128">**Or, if you don't have Windows Server 2012**</span></span>
    
    <span data-ttu-id="cc071-129">**실행** 대화 상자를 열고 Domain.msc에서 입력 한 다음 **Windows 키 + R을** 누릅니다. 하 고 **확인**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc071-129">Press **Windows key + R** to open the **Run** dialog, and then type in Domain.msc, and then choose **OK**.</span></span>
    
    ![Active Directory 도메인 및 트러스트를 선택 합니다.](media/46b6e007-9741-44af-8517-6f682e0ac974.png)
  
2. <span data-ttu-id="cc071-131">**Active Directory 도메인 및 트러스트** 창에서 **Active Directory 도메인 및 트러스트를**마우스 오른쪽 단추로 클릭 한 다음 **속성**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc071-131">On the **Active Directory Domains and Trusts** window, right-click **Active Directory Domains and Trusts**, and then choose **Properties**.</span></span>
    
    ![ActiveDirectory 도메인 및 트러스트를 단추로 클릭 하 고 속성을 선택 합니다.](media/39d20812-ffb5-4ba9-8d7b-477377ac360d.png)
  
3. <span data-ttu-id="cc071-133">**UPN 접미사** 탭에서 **대체 UPN 접미사** 상자에 입력 새 UPN 접미사 또는 접미사를 한 다음 **추가** 선택 \> **적용**합니다.</span><span class="sxs-lookup"><span data-stu-id="cc071-133">On the **UPN Suffixes** tab, in the **Alternative UPN Suffixes** box, type your new UPN suffix or suffixes, and then choose **Add** \> **Apply**.</span></span>
    
    ![새 UPN 접미사를 추가 합니다.](media/a4aaf919-7adf-469a-b93f-83ef284c0915.PNG)
  
    <span data-ttu-id="cc071-135">추가 접미사를 완료 했으면 **확인** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc071-135">Choose **OK** when you're done adding suffixes.</span></span> 
    
 <span data-ttu-id="cc071-136">**2 단계: 기존 사용자에 대 한 UPN 접미사를 변경 합니다.**</span><span class="sxs-lookup"><span data-stu-id="cc071-136">**Step 2: Change the UPN suffix for existing users**</span></span>
  
1. <span data-ttu-id="cc071-137">Active Directory 도메인 서비스 (AD DS)에서 실행 되는 서버의 서버 관리자에서 **도구** 를 선택 \> **Active Directory Active Directory 사용자 및 컴퓨터**입니다.</span><span class="sxs-lookup"><span data-stu-id="cc071-137">On the server that Active Directory Domain Services (AD DS) runs on, in the Server Manager choose **Tools** \> **Active Directory Active Directory Users and Computers**.</span></span>
    
    <span data-ttu-id="cc071-138">**또는 Windows Server 2012를 설치 하지 않은 경우**</span><span class="sxs-lookup"><span data-stu-id="cc071-138">**Or, if you don't have Windows Server 2012**</span></span>
    
    <span data-ttu-id="cc071-139">다음 **확인** 을 클릭 하 고 **실행** 대화 상자를 열고에 Dsa.msc를 입력 한 다음 **Windows 키 + R을** 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="cc071-139">Press **Windows key + R** to open the **Run** dialog, and then type in Dsa.msc, and then click **OK**</span></span>
    
2. <span data-ttu-id="cc071-140">사용자를 선택 마우스 오른쪽 단추로 클릭 한 다음 **속성**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc071-140">Select a user, right-click, and then choose **Properties**.</span></span>
    
3. <span data-ttu-id="cc071-141">UPN 접미사 드롭다운 목록에서 **계정** 탭에서 새 UPN 접미사를 선택 하 고 **확인**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc071-141">On the **Account** tab, in the UPN suffix drop-down list, choose the new UPN suffix, and then choose **OK**.</span></span>
    
    ![사용자에 대 한 새 UPN 접미사를 추가 합니다.](media/54876751-49f0-48cc-b864-2623c4835563.png)
  
4. <span data-ttu-id="cc071-143">모든 사용자에 대해 다음이 단계를 완료 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc071-143">Complete these steps for every user.</span></span>
    
    <span data-ttu-id="cc071-144">업데이트를 대량 수 또는 UPN 접미사 [를 모든 사용자에 대 한 UPN 접미사를 변경 하려면 Windows PowerShell을 사용할 수 있습니다](prepare-a-non-routable-domain-for-directory-synchronization.md#BK_Posh).</span><span class="sxs-lookup"><span data-stu-id="cc071-144">Alternately you can bulk update the UPN suffixes [You can also use Windows PowerShell to change the UPN suffix for all users](prepare-a-non-routable-domain-for-directory-synchronization.md#BK_Posh).</span></span>
    
### <a name="you-can-also-use-windows-powershell-to-change-the-upn-suffix-for-all-users"></a><span data-ttu-id="cc071-145">**Windows PowerShell을 사용 하 여 모든 사용자에 대 한 UPN 접미사를 변경할 수도 있습니다.**</span><span class="sxs-lookup"><span data-stu-id="cc071-145">**You can also use Windows PowerShell to change the UPN suffix for all users**</span></span>

<span data-ttu-id="cc071-p106">업데이트 하는 사용자 수가 많은 경우에 Windows PowerShell을 사용 하 여 더 쉽습니다. 다음 예제에서는 contoso.com으로 모든 contoso.local 접미사를 변경 하려면 [Get ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624312) 및 [집합 ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624313) cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc071-p106">If you have a lot of users to update, it is easier to use Windows PowerShell. The following example uses the cmdlets [Get-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624312) and [Set-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624313) to change all contoso.local suffixes to contoso.com.</span></span> 

<span data-ttu-id="cc071-148">Contoso.com를 모든 contoso.local 접미사를 업데이트 하려면 다음 Windows PowerShell 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc071-148">Run the following Windows PowerShell commands to update all contoso.local suffixes to contoso.com:</span></span>
    
  ```
  $LocalUsers = Get-ADUser -Filter {UserPrincipalName -like '*contoso.local'} -Properties userPrincipalName -ResultSetSize $null
  ```

  ```
  $LocalUsers | foreach {$newUpn = $_.UserPrincipalName.Replace("contoso.local","contoso.com"); $_ | Set-ADUser -UserPrincipalName $newUpn}
  ```
<span data-ttu-id="cc071-149">Active Directory에서 Windows PowerShell을 사용 하는 방법에 대 한 자세한 내용은 [Windows PowerShell의 Active Directory 모듈](https://go.microsoft.com/fwlink/p/?LinkId=624314) 을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="cc071-149">See [Active Directory Windows PowerShell module](https://go.microsoft.com/fwlink/p/?LinkId=624314) to learn more about using Windows PowerShell in Active Directory.</span></span> 

