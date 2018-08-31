---
title: Office 365의 디렉터리 동기화 설정
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: 1b3b5318-6977-42ed-b5c7-96fa74b08846
description: Office 365 및 온-프레미스 Active Directory 간에 디렉터리 동기화를 설정 하는 방법에 알아봅니다.
ms.openlocfilehash: e406eec08b34a694602c756235533f8b1ff6651e
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541941"
---
# <a name="set-up-directory-synchronization-for-office-365"></a><span data-ttu-id="b58b2-103">Office 365의 디렉터리 동기화 설정</span><span class="sxs-lookup"><span data-stu-id="b58b2-103">Set up directory synchronization for Office 365</span></span>
<span data-ttu-id="b58b2-p101">Office 365 클라우드 기반 사용자 id 관리 서비스 Azure Active Directory를 사용 하 여 사용자를 관리 합니다. Office 365와 온-프레미스 환경을 동기화 하 여 Azure AD와 온-프레미스 Active Directory를 통합할 수 있습니다. 동기화를 설정한 후에 Azure AD 또는 온-프레미스 디렉터리 내에 수행 하는 사용자 인증을 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b58b2-p101">Office 365 uses the cloud-based user identity management service Azure Active Directory to manage users. You can also integrate your on-premises Active Directory with Azure AD by synchronizing your on-premises environment with Office 365. Once you set up synchronization you can decide to have their user authentication take place within Azure AD or within your on-premises directory.</span></span>
  
## <a name="office-365-directory-synchronization"></a><span data-ttu-id="b58b2-107">Office 365 디렉터리 동기화</span><span class="sxs-lookup"><span data-stu-id="b58b2-107">Office 365 directory synchronization</span></span>
<span data-ttu-id="b58b2-p102">동기화 된 id 또는 온-프레미스 조직과 Office 365 간의 페더레이션된 id를 사용할 수 있습니다. 동기화 된 id를 가진 사용자가 온-프레미스, 관리 하 고 Azure AD를 사용 하는 경우 동일한 암호 클라우드에서 온-프레미스로 하 여 인증 합니다. 가장 일반적인 디렉터리 동기화 시나리오입니다. 통과 인증 또는 페더레이션 id를 관리할 수 있도록 사용자가 온-프레미스 및 온-프레미스 디렉터리에서 인증 합니다. 페더레이션된 id 추가 구성이 필요 하 고 사용자만 한 번 로그인 할 수 있습니다. 자세한 내용은 [Office 365 Id 이해 및 Azure Active Directory를](about-office-365-identity.md)읽어보십시오.</span><span class="sxs-lookup"><span data-stu-id="b58b2-p102">You can either use synchronized identity or federated identity between your on-premises organization and Office 365. With synchronized identity, you manage your users on-premises, and they are authenticated by Azure AD when they use the same password in the cloud as on-premises. This is the most common directory synchronization scenario. Pass-through authentication or Federated identity, allows you to manage your users on-premises and they are authenticated by your on-premises directory. Federated identity requires additional configuration and enables your users to only sign in once. For details, read [Understanding Office 365 Identity and Azure Active Directory](about-office-365-identity.md).</span></span>
  
## <a name="want-to-upgrade-from-windows-azure-active-directory-sync-dirsync-to-azure-active-directory-connect"></a><span data-ttu-id="b58b2-114">Azure Active Directory 연결 하려면 Windows Azure Active Directory 동기화 (DirSync)에서 업그레이드 하려는 경우?</span><span class="sxs-lookup"><span data-stu-id="b58b2-114">Want to upgrade from Windows Azure Active Directory sync (DirSync) to Azure Active Directory Connect?</span></span>
<span data-ttu-id="b58b2-115">현재 디렉터리 동기화를 사용 하 고 업그레이드 하려는 경우을 향해 위에 [azure.com](https://azure.com) 에 [업그레이드 지침](https://go.microsoft.com/fwlink/p/?LinkId=733240)입니다.</span><span class="sxs-lookup"><span data-stu-id="b58b2-115">If you are currently using DirSync and want to upgrade, head over to [azure.com](https://azure.com) for [upgrade instructions](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span></span>
  
## <a name="prerequisites-for-azure-ad-connect"></a><span data-ttu-id="b58b2-116">Azure AD에 대 한 필수 구성 요소에 연결</span><span class="sxs-lookup"><span data-stu-id="b58b2-116">Prerequisites for Azure AD Connect</span></span>
<span data-ttu-id="b58b2-p103">Office 365 구독을 Azure AD에 대 한 무료 구독을 얻을 수 있습니다. 디렉터리 동기화를 설정 하는 경우는 Azure Active Directory 연결에 설치한 온-프레미스 서버 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="b58b2-p103">You get a free subscription to Azure AD with your Office 365 subscription. When you set up directory synchronization, you will install Azure Active Directory Connect on one of your on-premises servers.</span></span>
  
<span data-ttu-id="b58b2-119">Office 365에 대 한 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b58b2-119">For Office 365 you will need to:</span></span>
  
- <span data-ttu-id="b58b2-120">온-프레미스 도메인 (절차를 안내이 통해)을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b58b2-120">Verify your on-premises domain (the procedure will guide you through this).</span></span>
- <span data-ttu-id="b58b2-121">Office 365 테 넌 트에 대 한 권한이 파일 [비즈니스를 위한 Office 365의 관리 역할을 할당](https://support.office.com/article/EAC4D046-1AFD-4F1A-85FC-8219C79E1504) 하 고 온-프레미스 Active Directory 합니다.</span><span class="sxs-lookup"><span data-stu-id="b58b2-121">Have [Assign admin roles in Office 365 for business](https://support.office.com/article/EAC4D046-1AFD-4F1A-85FC-8219C79E1504) permissions for your Office 365 tenant and on-premises Active Directory.</span></span> 
    
<span data-ttu-id="b58b2-122">Azure AD 연결을 설치 하는 온-프레미스 서버에 대 한 다음과 같은 소프트웨어가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="b58b2-122">For your on-premises server on which you install Azure AD Connect you will need the following software:</span></span>
  
|<span data-ttu-id="b58b2-123">**서버 운영 체제**</span><span class="sxs-lookup"><span data-stu-id="b58b2-123">**Server OS**</span></span>|<span data-ttu-id="b58b2-124">**기타 소프트웨어**</span><span class="sxs-lookup"><span data-stu-id="b58b2-124">**Other software**</span></span>|
|:-----|:-----|
|<span data-ttu-id="b58b2-125">**Windows Server 2012 R2**</span><span class="sxs-lookup"><span data-stu-id="b58b2-125">**Windows Server 2012 R2**</span></span> | <span data-ttu-id="b58b2-126">-PowerShell는 기본적으로 설치, 작업이 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b58b2-126">- PowerShell is installed by default, no action is required.</span></span>  <br/> <span data-ttu-id="b58b2-p104">-Net 4.5.1 이후 릴리스에서 Windows Update를 통해 제공 되는 하 고 있습니다. 제어판에서 Windows 서버에 최신 업데이트를 설치한 후 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b58b2-p104">- Net 4.5.1 and later releases are offered through Windows Update. Make sure you have installed the latest updates to Windows Server in the Control Panel.</span></span> |
|<span data-ttu-id="b58b2-129">**Windows Server 2008 R2 서비스 팩 1 (SP1)** 또는 **Windows Server 2012**</span><span class="sxs-lookup"><span data-stu-id="b58b2-129">**Windows Server 2008 R2 with Service Pack 1 (SP1)** or **Windows Server 2012**</span></span> | <span data-ttu-id="b58b2-p105">-최신 버전의 PowerShell Windows Management Framework 4.0에서 제공 됩니다. [Microsoft 다운로드 센터](https://go.microsoft.com/fwlink/p/?LinkId=717996)에서 검색.</span><span class="sxs-lookup"><span data-stu-id="b58b2-p105">- The latest version of PowerShell is available in Windows Management Framework 4.0. Search for it on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).  </span></span><br/> <span data-ttu-id="b58b2-132">-.Net 4.5.1 및 이후 릴리스에서 [Microsoft 다운로드 센터](https://go.microsoft.com/fwlink/p/?LinkId=717996)에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b58b2-132">- .Net 4.5.1 and later releases are available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span> |
|<span data-ttu-id="b58b2-133">**Windows Server 2008**</span><span class="sxs-lookup"><span data-stu-id="b58b2-133">**Windows Server 2008**</span></span> | <span data-ttu-id="b58b2-134">-최신 지원 되는 버전의 PowerShell Windows Management Framework 3.0을 [Microsoft 다운로드 센터](https://go.microsoft.com/fwlink/p/?LinkId=717996)에서 사용할 수 있는에서 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b58b2-134">- The latest supported version of PowerShell is available in Windows Management Framework 3.0, available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span>  <br/> <span data-ttu-id="b58b2-135">-.Net 4.5.1 및 이후 릴리스에서 [Microsoft 다운로드 센터](https://go.microsoft.com/fwlink/p/?LinkId=717996)에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b58b2-135">- .Net 4.5.1 and later releases are available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span> |
   
> [!NOTE]
> <span data-ttu-id="b58b2-p106">Azure Active Directory 디렉터리 동기화를 사용 하는 경우 온-프레미스 Active Directory에서 Azure Active Directory에는 동기화 할 수 있는 메일 그룹 구성원의 최대 수는 15, 000입니다. Azure AD 연결에 대 한 해당 번호가 50, 000입니다.</span><span class="sxs-lookup"><span data-stu-id="b58b2-p106">If you're using Azure Active Directory DirSync, the maximum number of distribution group members that you can synchronize from your on-premises Active Directory to Azure Active Directory is 15,000. For Azure AD Connect, that number is 50,000.</span></span> 
  
<span data-ttu-id="b58b2-138">Azure AD 연결에 대 한 하드웨어, 소프트웨어, 계정 및 권한 요구 사항, SSL 인증서 요구 사항 및 제한 개체를 더 신중 하 게 검토 하려면 [Azure Active Directory 연결에 대 한 필수 구성 요소](https://go.microsoft.com/fwlink/p/?LinkId=716896)를 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="b58b2-138">To more carefully review hardware, software, account and permissions requirements, SSL certificate requirements, and object limits for Azure AD Connect, read [Prerequisites for Azure Active Directory Connect](https://go.microsoft.com/fwlink/p/?LinkId=716896).</span></span>
  
<span data-ttu-id="b58b2-139">Azure AD 연결 [버전 릴리스 정보](https://go.microsoft.com/fwlink/p/?LinkId=733238) 포함 되며 각 버전에서 수정 된 기능을 검토할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b58b2-139">You can also review the Azure AD Connect [version release history](https://go.microsoft.com/fwlink/p/?LinkId=733238) to see what is included and fixed in each release.</span></span> 

## <a name="to-set-up-directory-synchronization"></a><span data-ttu-id="b58b2-140">디렉터리 동기화를 설정 하려면</span><span class="sxs-lookup"><span data-stu-id="b58b2-140">To set up directory synchronization</span></span>
1. <span data-ttu-id="b58b2-141">Office 365 관리 센터에 로그인 하 고 **사용자가** 선택 \> 왼쪽된 탐색 모음에 **현재 사용자** 입니다.</span><span class="sxs-lookup"><span data-stu-id="b58b2-141">Sign in to the Office 365 admin center and choose **Users** \> **Active Users** on the left navigation.</span></span> 
2. <span data-ttu-id="b58b2-142">Office 365 관리 센터의 **현재 사용자** 페이지에서 선택 * * 더 * * \> **디렉터리 동기화**합니다.</span><span class="sxs-lookup"><span data-stu-id="b58b2-142">In the Office 365 admin center, on the **Active users** page, choose ** More ** \> **Directory synchronization**.</span></span>
    
    ![더 많은 메뉴에서 디렉터리 동기화를 선택 합니다.](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
3. <span data-ttu-id="b58b2-p107">에 * * 적합 디렉터리 동기화가? * * 페이지, **1 ~ 10**및 "조직의 크기에 따라, 것이 좋습니다 만들기 및 클라우드에서 사용자를 관리 하는에서 **11 ~ 50** 결과의 두 첫번째 선택. 디렉터리 동기화를 사용 하 여 하면 설치가 복잡 하 게 됩니다. 이동 하면 사용자를 추가 하려면 현재 사용자에 게. "</span><span class="sxs-lookup"><span data-stu-id="b58b2-p107">On the ** Is directory sync right for you? ** page, the two first choices of **1-10**, and **11-50** result in "Based on the size of your organization, we recommend that you create and manage users in the cloud. Using directory synchronization will make your setup more complex. Go to Active users to add your users."</span></span> 
    
    - <span data-ttu-id="b58b2-148">그러나 여전히, 디렉터리 동기화 설정 페이지의 아래쪽에 **여기에서 계속** 선택 하 여 계속할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b58b2-148">You can still, however, continue setting up directory synchronization by choosing **Continue here** on the bottom of the page.</span></span> 
    
    - <span data-ttu-id="b58b2-p108">두 후자의 선택 **51-250** 또는 **251 이상에서 작동할**을 선택 하는 경우 사용 하 여 동기화 설치 디렉터리 동기화를 권장 합니다. **다음** 계속을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b58b2-p108">If you select the two latter choices, **51-250** or **251 or greater**, the synchronization setup will recommend directory synchronization. Choose **Next** to continue.</span></span> 
    
    ![디렉터리 동기화 설정을 계속 하려면 다음을 선택합니다](media/359a1eb9-99ae-4b5b-a413-4de53037cceb.png)
  
4. <span data-ttu-id="b58b2-152">**동기화 클라우드와 로컬 디렉터리**정보를 확인 하 고 자세한 정보를 원하는 경우 알아보기로 이동 하는 자세한 내용 링크를 선택: [Office 365에 대 한 디렉터리 동기화를 통해 프로 비전 사용자에 게 준비](prepare-for-directory-synchronization.md)하 고 다음 **를 선택 합니다 **.</span><span class="sxs-lookup"><span data-stu-id="b58b2-152">On the **Sync your local directory with the cloud**, read the information, and if you want more information, choose the learn more link that goes to: [Prepare to provision users through directory synchronization to Office 365](prepare-for-directory-synchronization.md), and then choose **Next**.</span></span> 
    
5. <span data-ttu-id="b58b2-p109">**디렉터리를 확인해 보겠습니다** 페이지에서 자동으로 디렉터리를 검사 하는 것에 대 한 요구 사항을 검토 합니다. 요구를 충족 하는 경우 **다음** 을 선택 \> **검사를 시작**합니다. 요구 사항을 충족 수 없는 경우 **수동으로 계속**을 선택 하 여 계속할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b58b2-p109">On the **Let's check your directory** page, review the requirements for automatically checking your directory. If you meet the requirements, choose **Next** \> **Start scan**. If you can't meet the requirements you can still continue by choosing **continue manually**.</span></span>
    
    ![다음을 선택 또는 수동으로 계속는 보겠습니다 디렉터리 페이지에서 제품 키를 확인 합니다.](media/af4a6bd5-13aa-4bfa-9751-4464a32ca8db.png)
  
6. <span data-ttu-id="b58b2-157">디렉터리를 검사 하려면 선택 하는 경우 **디렉터리 동기화 설치 확인** 페이지에서 **검사 시작** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b58b2-157">If you select to scan your directories, choose **Start scan** on the **Evaluating directory synchronization setup** page.</span></span> 
    
    <span data-ttu-id="b58b2-158">다운로드 하 여 검사를 실행 하는 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="b58b2-158">Follow the instructions to download and run the scan.</span></span>
    
7. <span data-ttu-id="b58b2-159">검사가 완료 되 면 설치 마법사를 반환 하 고 **다음** 검색 결과 표시 하려면 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b58b2-159">Once the scan is complete, return to the setup wizard, and choose **Next** to see your scan results.</span></span> 
    
8. <span data-ttu-id="b58b2-p110">**도메인 소유권 확인** 페이지에서 설명 하는 대로 도메인을 확인 합니다. 자세한 지침은 [DNS 레코드를 관리 하는 경우 Office 365 용 DNS 레코드 만들기](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="b58b2-p110">Verify your domains as instructed on the **Verify Ownership of your domains** page. For detailed instructions, see [Create DNS records for Office 365 when you manage your DNS records](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23).</span></span>
    
    > [!IMPORTANT]
    > <span data-ttu-id="b58b2-p111">소유 하 고 도메인을 확인 하려면 TXT 레코드를 추가한 후 도메인 마법사에서 사용자 추가 (영문)의 다음 단계로 이동 하지 마십시오. 디렉터리 동기화 하기에 대 한 사용자를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b58b2-p111">After you have added a TXT record to verify you own your domain, do not go to the next step of adding users in the domains wizard. The directory synchronization will add users for you.</span></span> 
  
    <span data-ttu-id="b58b2-164">**Office 365 설치** 페이지로 돌아갑니다 하 고 **새로 고칠** 선택</span><span class="sxs-lookup"><span data-stu-id="b58b2-164">Return to the **Office 365 Setup** page and choose **Refresh**</span></span>
    
    ![도메인을 확인 한 후 새로 고침을 선택 합니다.](media/9b5fb593-5ff7-49f0-80d0-18e36d39d669.png)
  
9. <span data-ttu-id="b58b2-166">**도메인 준비가 완료** 페이지에서 **다음**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b58b2-166">On the **Your domains are ready** page, choose **Next**.</span></span>
    
10. <span data-ttu-id="b58b2-p112">**환경을 정리** 페이지에서 필요에 따라 Active Directory를 확인 하는 IDFix를 다운로드 하려면 지침을 따릅니다. **다음** 계속을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b58b2-p112">On the **Clean up your environment** page, optionally follow the instructions to download IDFix to check your Active Directory. Choose **Next** to continue.</span></span> 
    
11. <span data-ttu-id="b58b2-169">에 * * 실행 Azure Active Directory 연결 * * 페이지에서 Azure AD 연결 마법사를 설치 하려면 **다운로드** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b58b2-169">On the ** Run Azure Active Directory Connect ** page, choose **Download** to install Azure AD Connect wizard.</span></span> 
    
    > [!NOTE]
    > <span data-ttu-id="b58b2-p113">이 시점에서 Azure AD 연결 마법사에서 수 있습니다. 한다고 가정해봅니다. 마지막 열 브라우저에서 Azure AD 연결 단계 완료 한 후 돌아갈 수 있도록 하는 디렉터리 동기화 마법사 페이지를 두면 있는지 확인 하십시오.</span><span class="sxs-lookup"><span data-stu-id="b58b2-p113">At this point you will be in the Azure AD Connect wizard. Make sure you leave the directory synchronization wizard page you were last on open in your browser, so you can return to it after the Azure AD Connect steps are done.</span></span> 
  
    <span data-ttu-id="b58b2-p114">Azure AD 연결 마법사가 설치 후 자동으로 열립니다. 기본 설치 사이트 바탕 화면에서 열 수 있습니다. 자신의 시나리오에 따라 마법사 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="b58b2-p114">After Azure AD Connect wizard has installed it will automatically open. You can also open it from your desktop, the default install site. Follow the wizard instructions depending on your scenario:</span></span>
    
  - <span data-ttu-id="b58b2-175">암호 해시 동기화와 디렉터리 동기화를 위해 [express 설정 사용 하 여 Azure AD 연결](https://go.microsoft.com/fwlink/p/?LinkID=698537)을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b58b2-175">For directory synchronization with password hash synchronization, use [Azure AD Connect with express settings](https://go.microsoft.com/fwlink/p/?LinkID=698537).</span></span>
    
  - <span data-ttu-id="b58b2-176">다중 포리스트, 통과 인증, 페더레이션된 id 및 SSO 옵션을 [사용자 지정 설치의 Azure AD 연결](https://go.microsoft.com/fwlink/p/?LinkId=698430)을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b58b2-176">For multiple forests, pass-through authentication, federated identity and SSO options, use [Custom Installation of Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430).</span></span>
    
    <span data-ttu-id="b58b2-177">이러한 옵션을 사용 하 여 **Express 설정** 페이지에서 **사용자 지정** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b58b2-177">Select **Customize** on the **Express Settings** page to use these options.</span></span> 
    
12. <span data-ttu-id="b58b2-p115">Azure AD 연결 마법사가 완료 되 면 **Office 365 설치** 마법사를 반환 하 고 **페이지 예상된 대로 작동 하는지 동기화 확인**에 지침을 따릅니다. **다음** 계속을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b58b2-p115">After the Azure AD Connect wizard is done, return to the **Office 365 Setup** wizard, and follow the instructions on the **Make sure sync worked as expected page**. Choose **Next** to continue.</span></span> 
    
13. <span data-ttu-id="b58b2-180">지침에 읽기는 * * 사용자 활성화를 * * 페이지 하 고 **다음**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b58b2-180">Read the instructions on the ** Activate users ** page and then choose **Next**.</span></span>
    
14. <span data-ttu-id="b58b2-181">**모든 설치 하 고 있는** 페이지에서 **완료** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b58b2-181">Choose **Finish** on the **You're all setup** page.</span></span> 
    
## <a name="assign-licences-to-synchronized-users"></a><span data-ttu-id="b58b2-182">동기화 된 사용자에 게 라이센스 할당</span><span class="sxs-lookup"><span data-stu-id="b58b2-182">Assign licences to synchronized users</span></span>
<span data-ttu-id="b58b2-p116">Office 365로 사용자 동기화 한 후 만들어질 때 하지만 메일 등의 Office 365 기능을 사용 하 여 수 자신에 게 라이선스를 할당 해야 합니다. 자세한 내용은 [비즈니스를 위한 Office 365에서 사용자에 게 라이선스 할당](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="b58b2-p116">After you have synchronized your users to Office 365, they are created but you need to assign licenses to them so they can use Office 365 features, such as mail. For instructions, see [Assign licenses to users in Office 365 for business](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc).</span></span>
    
## <a name="finish-setting-up-domains"></a><span data-ttu-id="b58b2-185">도메인 설정이 완료</span><span class="sxs-lookup"><span data-stu-id="b58b2-185">Finish setting up domains</span></span>
<span data-ttu-id="b58b2-186">도메인 설정이 완료 [DNS 레코드를 관리 하는 경우 Office 365 용 DNS 레코드 만들기](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23) 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="b58b2-186">Follow the steps in [Create DNS records for Office 365 when you manage your DNS records](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23) to finish setting up your domains.</span></span>