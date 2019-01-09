---
title: Office 365의 디렉터리 동기화 설정
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED15
- MBS150
- BCS160
ms.assetid: 1b3b5318-6977-42ed-b5c7-96fa74b08846
description: Office 365 및 온-프레미스 Active Directory 간에 디렉터리 동기화를 설정 하는 방법에 알아봅니다.
ms.openlocfilehash: 95f138a0a11f14a1036d7d48983f4c88bc965fd0
ms.sourcegitcommit: 0fdb6e470342a98ba164db627fe3dd02cfe8aa0b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/08/2019
ms.locfileid: "27768827"
---
# <a name="set-up-directory-synchronization-for-office-365"></a><span data-ttu-id="59f12-103">Office 365의 디렉터리 동기화 설정</span><span class="sxs-lookup"><span data-stu-id="59f12-103">Set up directory synchronization for Office 365</span></span>
<span data-ttu-id="59f12-p101">Office 365 클라우드 기반 사용자 id 관리 서비스 Azure Active Directory를 사용 하 여 사용자를 관리 합니다. Office 365와 온-프레미스 환경을 동기화 하 여 Azure AD와 온-프레미스 Active Directory를 통합할 수 있습니다. 동기화를 설정한 후에 Azure AD 또는 온-프레미스 디렉터리 내에 수행 하는 사용자 인증을 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59f12-p101">Office 365 uses the cloud-based user identity management service Azure Active Directory to manage users. You can also integrate your on-premises Active Directory with Azure AD by synchronizing your on-premises environment with Office 365. Once you set up synchronization you can decide to have their user authentication take place within Azure AD or within your on-premises directory.</span></span>
  
## <a name="office-365-directory-synchronization"></a><span data-ttu-id="59f12-107">Office 365 디렉터리 동기화</span><span class="sxs-lookup"><span data-stu-id="59f12-107">Office 365 directory synchronization</span></span>
<span data-ttu-id="59f12-p102">동기화 된 id 또는 온-프레미스 조직과 Office 365 간의 페더레이션된 id를 사용할 수 있습니다. 동기화 된 id를 가진 사용자가 온-프레미스, 관리 하 고 Azure AD를 사용 하는 경우 동일한 암호 클라우드에서 온-프레미스로 하 여 인증 합니다. 가장 일반적인 디렉터리 동기화 시나리오입니다. 통과 인증 또는 페더레이션 id를 관리할 수 있도록 사용자가 온-프레미스 및 온-프레미스 디렉터리에서 인증 합니다. 페더레이션된 id 추가 구성이 필요 하 고 사용자만 한 번 로그인 할 수 있습니다. 자세한 내용은 [Office 365 Id 이해 및 Azure Active Directory를](about-office-365-identity.md)읽어보십시오.</span><span class="sxs-lookup"><span data-stu-id="59f12-p102">You can either use synchronized identity or federated identity between your on-premises organization and Office 365. With synchronized identity, you manage your users on-premises, and they are authenticated by Azure AD when they use the same password in the cloud as on-premises. This is the most common directory synchronization scenario. Pass-through authentication or Federated identity, allows you to manage your users on-premises and they are authenticated by your on-premises directory. Federated identity requires additional configuration and enables your users to only sign in once. For details, read [Understanding Office 365 Identity and Azure Active Directory](about-office-365-identity.md).</span></span>
  
## <a name="want-to-upgrade-from-windows-azure-active-directory-sync-dirsync-to-azure-active-directory-connect"></a><span data-ttu-id="59f12-114">Azure Active Directory 연결 하려면 Windows Azure Active Directory 동기화 (DirSync)에서 업그레이드 하려는 경우?</span><span class="sxs-lookup"><span data-stu-id="59f12-114">Want to upgrade from Windows Azure Active Directory sync (DirSync) to Azure Active Directory Connect?</span></span>
<span data-ttu-id="59f12-115">현재 디렉터리 동기화를 사용 하 고 업그레이드 하려는 경우을 향해 위에 [azure.com](https://azure.com) 에 [업그레이드 지침](https://go.microsoft.com/fwlink/p/?LinkId=733240)입니다.</span><span class="sxs-lookup"><span data-stu-id="59f12-115">If you are currently using DirSync and want to upgrade, head over to [azure.com](https://azure.com) for [upgrade instructions](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span></span>
  
## <a name="prerequisites-for-azure-ad-connect"></a><span data-ttu-id="59f12-116">Azure AD에 대 한 필수 구성 요소에 연결</span><span class="sxs-lookup"><span data-stu-id="59f12-116">Prerequisites for Azure AD Connect</span></span>
<span data-ttu-id="59f12-p103">Office 365 구독을 Azure AD에 대 한 무료 구독을 얻을 수 있습니다. 디렉터리 동기화를 설정 하는 경우는 Azure Active Directory 연결에 설치한 온-프레미스 서버 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="59f12-p103">You get a free subscription to Azure AD with your Office 365 subscription. When you set up directory synchronization, you will install Azure Active Directory Connect on one of your on-premises servers.</span></span>
  
<span data-ttu-id="59f12-119">Office 365에 대 한 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="59f12-119">For Office 365 you will need to:</span></span>
  
- <span data-ttu-id="59f12-120">온-프레미스 도메인 (절차를 안내이 통해)을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="59f12-120">Verify your on-premises domain (the procedure will guide you through this).</span></span>
- <span data-ttu-id="59f12-121">Office 365 테 넌 트에 대 한 권한이 파일 [비즈니스를 위한 Office 365의 관리 역할을 할당](https://support.office.com/article/EAC4D046-1AFD-4F1A-85FC-8219C79E1504) 하 고 온-프레미스 Active Directory 합니다.</span><span class="sxs-lookup"><span data-stu-id="59f12-121">Have [Assign admin roles in Office 365 for business](https://support.office.com/article/EAC4D046-1AFD-4F1A-85FC-8219C79E1504) permissions for your Office 365 tenant and on-premises Active Directory.</span></span> 
    
<span data-ttu-id="59f12-122">Azure AD 연결을 설치 하는 온-프레미스 서버에 대 한 다음과 같은 소프트웨어가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="59f12-122">For your on-premises server on which you install Azure AD Connect you will need the following software:</span></span>
  
|<span data-ttu-id="59f12-123">**서버 운영 체제**</span><span class="sxs-lookup"><span data-stu-id="59f12-123">**Server OS**</span></span>|<span data-ttu-id="59f12-124">**기타 소프트웨어**</span><span class="sxs-lookup"><span data-stu-id="59f12-124">**Other software**</span></span>|
|:-----|:-----|
|<span data-ttu-id="59f12-125">**Windows Server 2012 R2**</span><span class="sxs-lookup"><span data-stu-id="59f12-125">**Windows Server 2012 R2**</span></span> | <span data-ttu-id="59f12-126">-PowerShell는 기본적으로 설치, 작업이 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="59f12-126">- PowerShell is installed by default, no action is required.</span></span>  <br/> <span data-ttu-id="59f12-p104">-Net 4.5.1 이후 릴리스에서 Windows Update를 통해 제공 되는 하 고 있습니다. 제어판에서 Windows 서버에 최신 업데이트를 설치한 후 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="59f12-p104">- Net 4.5.1 and later releases are offered through Windows Update. Make sure you have installed the latest updates to Windows Server in the Control Panel.</span></span> |
|<span data-ttu-id="59f12-129">**Windows Server 2008 R2 서비스 팩 1 (SP1)** 또는 **Windows Server 2012**</span><span class="sxs-lookup"><span data-stu-id="59f12-129">**Windows Server 2008 R2 with Service Pack 1 (SP1)** or **Windows Server 2012**</span></span> | <span data-ttu-id="59f12-p105">-최신 버전의 PowerShell Windows Management Framework 4.0에서 제공 됩니다. [Microsoft 다운로드 센터](https://go.microsoft.com/fwlink/p/?LinkId=717996)에서 검색.</span><span class="sxs-lookup"><span data-stu-id="59f12-p105">- The latest version of PowerShell is available in Windows Management Framework 4.0. Search for it on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).  </span></span><br/> <span data-ttu-id="59f12-132">-.Net 4.5.1 및 이후 릴리스에서 [Microsoft 다운로드 센터](https://go.microsoft.com/fwlink/p/?LinkId=717996)에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59f12-132">- .Net 4.5.1 and later releases are available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span> |
|<span data-ttu-id="59f12-133">**Windows Server 2008**</span><span class="sxs-lookup"><span data-stu-id="59f12-133">**Windows Server 2008**</span></span> | <span data-ttu-id="59f12-134">-최신 지원 되는 버전의 PowerShell Windows Management Framework 3.0을 [Microsoft 다운로드 센터](https://go.microsoft.com/fwlink/p/?LinkId=717996)에서 사용할 수 있는에서 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="59f12-134">- The latest supported version of PowerShell is available in Windows Management Framework 3.0, available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span>  <br/> <span data-ttu-id="59f12-135">-.Net 4.5.1 및 이후 릴리스에서 [Microsoft 다운로드 센터](https://go.microsoft.com/fwlink/p/?LinkId=717996)에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59f12-135">- .Net 4.5.1 and later releases are available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span> |
   
> [!NOTE]
> <span data-ttu-id="59f12-p106">Azure Active Directory 디렉터리 동기화를 사용 하는 경우 온-프레미스 Active Directory에서 Azure Active Directory에는 동기화 할 수 있는 메일 그룹 구성원의 최대 수는 15, 000입니다. Azure AD 연결에 대 한 해당 번호가 50, 000입니다.</span><span class="sxs-lookup"><span data-stu-id="59f12-p106">If you're using Azure Active Directory DirSync, the maximum number of distribution group members that you can synchronize from your on-premises Active Directory to Azure Active Directory is 15,000. For Azure AD Connect, that number is 50,000.</span></span> 
  
<span data-ttu-id="59f12-138">Azure AD 연결에 대 한 하드웨어, 소프트웨어, 계정 및 권한 요구 사항, SSL 인증서 요구 사항 및 제한 개체를 더 신중 하 게 검토 하려면 [Azure Active Directory 연결에 대 한 필수 구성 요소](https://go.microsoft.com/fwlink/p/?LinkId=716896)를 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="59f12-138">To more carefully review hardware, software, account and permissions requirements, SSL certificate requirements, and object limits for Azure AD Connect, read [Prerequisites for Azure Active Directory Connect](https://go.microsoft.com/fwlink/p/?LinkId=716896).</span></span>
  
<span data-ttu-id="59f12-139">Azure AD 연결 [버전 릴리스 정보](https://go.microsoft.com/fwlink/p/?LinkId=733238) 포함 되며 각 버전에서 수정 된 기능을 검토할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59f12-139">You can also review the Azure AD Connect [version release history](https://go.microsoft.com/fwlink/p/?LinkId=733238) to see what is included and fixed in each release.</span></span> 

## <a name="to-set-up-directory-synchronization"></a><span data-ttu-id="59f12-140">디렉터리 동기화를 설정 하려면</span><span class="sxs-lookup"><span data-stu-id="59f12-140">To set up directory synchronization</span></span>
1. <span data-ttu-id="59f12-141">Office 365 관리 센터에 로그인 하 고 **사용자가** 선택 \> 왼쪽된 탐색 모음에 **현재 사용자** 입니다.</span><span class="sxs-lookup"><span data-stu-id="59f12-141">Sign in to the Office 365 admin center and choose **Users** \> **Active Users** on the left navigation.</span></span> 
2. <span data-ttu-id="59f12-142">Office 365 관리 센터의 **현재 사용자** 페이지에서 선택 \* \* 더 \* \* \> **디렉터리 동기화**합니다.</span><span class="sxs-lookup"><span data-stu-id="59f12-142">In the Office 365 admin center, on the **Active users** page, choose \*\* More \*\* \> **Directory synchronization**.</span></span>
    
    ![더 많은 메뉴에서 디렉터리 동기화를 선택 합니다.](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
3. <span data-ttu-id="59f12-p107">**Active Directory 준비** 페이지에서 시작 **도구 다운로드 Microsoft Azure Active Directory 연결** 링크를 선택 합니다. Azure Active Directory 연결 설치 프로세스에 대 한 자세한 내용은 [Azure AD 연결 및 Azure AD 연결 상태 설치 안내서](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap)를 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="59f12-p107">On the **Active Directory preparation** page, select the **Download Microsoft Azure Active Directory Connect tool** link to get started. For more information about the Azure Active Directory Connect installation process, see [Azure AD Connect and Azure AD Connect Health installation roadmap](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap).</span></span>
    
## <a name="assign-licences-to-synchronized-users"></a><span data-ttu-id="59f12-146">동기화 된 사용자에 게 라이센스 할당</span><span class="sxs-lookup"><span data-stu-id="59f12-146">Assign licences to synchronized users</span></span>
<span data-ttu-id="59f12-p108">Office 365로 사용자 동기화 한 후 만들어질 때 하지만 메일 등의 Office 365 기능을 사용 하 여 수 자신에 게 라이선스를 할당 해야 합니다. 자세한 내용은 [비즈니스를 위한 Office 365에서 사용자에 게 라이선스 할당](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="59f12-p108">After you have synchronized your users to Office 365, they are created but you need to assign licenses to them so they can use Office 365 features, such as mail. For instructions, see [Assign licenses to users in Office 365 for business](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc).</span></span>
    
## <a name="finish-setting-up-domains"></a><span data-ttu-id="59f12-149">도메인 설정이 완료</span><span class="sxs-lookup"><span data-stu-id="59f12-149">Finish setting up domains</span></span>
<span data-ttu-id="59f12-150">도메인 설정이 완료 [DNS 레코드를 관리 하는 경우 Office 365 용 DNS 레코드 만들기](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23) 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="59f12-150">Follow the steps in [Create DNS records for Office 365 when you manage your DNS records](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23) to finish setting up your domains.</span></span>