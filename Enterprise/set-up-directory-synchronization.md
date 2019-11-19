---
title: Office 365에서 디렉터리 동기화 설정
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED15
- MBS150
- BCS160
ms.assetid: 1b3b5318-6977-42ed-b5c7-96fa74b08846
description: Office 365와 온-프레미스 Active Directory 간에 디렉터리 동기화를 설정 하는 방법에 대해 알아봅니다.
ms.openlocfilehash: a51abf7dcca0a9edc4ecf233ea67fdeb80070a70
ms.sourcegitcommit: 23c8781d1a2b0472612c3a2cb6e5d13edb03e236
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/19/2019
ms.locfileid: "38702249"
---
# <a name="set-up-directory-synchronization-for-office-365"></a><span data-ttu-id="83546-103">Office 365에서 디렉터리 동기화 설정</span><span class="sxs-lookup"><span data-stu-id="83546-103">Set up directory synchronization for Office 365</span></span>

<span data-ttu-id="83546-104">Office 365에서는 azure Active Directory (Azure AD) 테 넌 트를 사용 하 여 인증 및 클라우드 기반 리소스에 액세스 하기 위한 사용 권한을 위한 id를 저장 하 고 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="83546-104">Office 365 uses an Azure Active Directory (Azure AD) tenant to store and manage identities for authentication and permissions to access cloud-based resources.</span></span> 

<span data-ttu-id="83546-105">온-프레미스 AD DS (Active Directory 도메인 서비스)를 사용 하는 경우 AD DS 사용자 계정, 그룹 및 연락처를 Office 365 구독의 Azure AD 테 넌 트와 동기화 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83546-105">If you have an on-premises Active Directory Domain Services (AD DS), you can synchronize your AD DS user accounts, groups, and contacts with the Azure AD tenant of your Office 365 subscription.</span></span> <span data-ttu-id="83546-106">Office 365의 하이브리드 id입니다.</span><span class="sxs-lookup"><span data-stu-id="83546-106">This is hybrid identity for Office 365.</span></span> <span data-ttu-id="83546-107">구성 요소는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="83546-107">Here are its components.</span></span>

![](./media/about-office-365-identity/hybrid-identity.png)

<span data-ttu-id="83546-108">Azure AD Connect는 온-프레미스 서버에서 실행 되며 AD DS를 Azure AD 테 넌 트와 동기화 합니다.</span><span class="sxs-lookup"><span data-stu-id="83546-108">Azure AD Connect runs on an on-premises server and synchronizes your AD DS with the Azure AD tenant.</span></span> <span data-ttu-id="83546-109">또한 디렉터리 동기화와 함께 다음과 같은 인증 옵션을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83546-109">Along with directory synchronization, you can also specify these authentication options:</span></span>

- <span data-ttu-id="83546-110">암호 해시 동기화 (PHS)</span><span class="sxs-lookup"><span data-stu-id="83546-110">Password hash synchronization (PHS)</span></span>

  <span data-ttu-id="83546-111">Azure AD는 인증 자체를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="83546-111">Azure AD performs the authentication itself.</span></span>

- <span data-ttu-id="83546-112">통과 인증(PTA)</span><span class="sxs-lookup"><span data-stu-id="83546-112">Pass-through authentication (PTA)</span></span>

  <span data-ttu-id="83546-113">Azure AD에 AD DS가 인증을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="83546-113">Azure AD has AD DS perform the authentication.</span></span>

- <span data-ttu-id="83546-114">페더레이션 인증</span><span class="sxs-lookup"><span data-stu-id="83546-114">Federated authentication</span></span>

  <span data-ttu-id="83546-115">Azure AD는 클라이언트 컴퓨터에서 인증 요청을 리디렉션하여 다른 id 공급자에 게 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="83546-115">Azure AD redirects the client computer requesting authentication to contact another identity provider.</span></span>

<span data-ttu-id="83546-116">자세한 내용은 [하이브리드 id](plan-for-directory-synchronization.md) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="83546-116">See [Hybrid identities](plan-for-directory-synchronization.md) for more information.</span></span>
  
## <a name="1-review-prerequisites-for-azure-ad-connect"></a><span data-ttu-id="83546-117">1. Azure AD Connect에 대 한 필수 구성 요소 검토</span><span class="sxs-lookup"><span data-stu-id="83546-117">1. Review prerequisites for Azure AD Connect</span></span>

<span data-ttu-id="83546-118">Office 365 구독을 사용 하 여 무료 Azure AD 구독을 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83546-118">You get a free Azure AD subscription with your Office 365 subscription.</span></span> <span data-ttu-id="83546-119">디렉터리 동기화를 설정할 때 온-프레미스 서버 중 하나에 Azure AD Connect를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="83546-119">When you set up directory synchronization, you will install Azure AD Connect on one of your on-premises servers.</span></span>
  
<span data-ttu-id="83546-120">Office 365의 경우 다음 작업을 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="83546-120">For Office 365 you'll need to:</span></span>
  
- <span data-ttu-id="83546-121">온-프레미스 도메인을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="83546-121">Verify your on-premises domain.</span></span> <span data-ttu-id="83546-122">Azure AD Connect 마법사는이 과정을 안내 합니다.</span><span class="sxs-lookup"><span data-stu-id="83546-122">The Azure AD Connect wizard guides you through this.</span></span>
- <span data-ttu-id="83546-123">Office 365 테 넌 트 및 AD DS의 관리자 계정에 대 한 사용자 이름 및 암호를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="83546-123">Obtain the user names and passwords for the admin accounts of your Office 365 tenant and AD DS.</span></span>

<span data-ttu-id="83546-124">Azure AD Connect를 설치 하는 온-프레미스 서버의 경우 다음이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="83546-124">For your on-premises server on which you install Azure AD Connect, you'll need:</span></span>
  
|<span data-ttu-id="83546-125">**서버 OS**</span><span class="sxs-lookup"><span data-stu-id="83546-125">**Server OS**</span></span>|<span data-ttu-id="83546-126">**기타 소프트웨어**</span><span class="sxs-lookup"><span data-stu-id="83546-126">**Other software**</span></span>|
|:-----|:-----|
|<span data-ttu-id="83546-127">Windows Server 2012 R2 이상</span><span class="sxs-lookup"><span data-stu-id="83546-127">Windows Server 2012 R2 and later</span></span> | <span data-ttu-id="83546-128">-PowerShell은 기본적으로 설치 되며 아무 작업도 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="83546-128">- PowerShell is installed by default, no action is required.</span></span>  <br> <span data-ttu-id="83546-129">-Net 4.5.1 이상 버전은 Windows Update를 통해 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="83546-129">- Net 4.5.1 and later releases are offered through Windows Update.</span></span> <span data-ttu-id="83546-130">제어판에 Windows Server에 대 한 최신 업데이트를 설치 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="83546-130">Make sure you have installed the latest updates to Windows Server in the Control Panel.</span></span> |
|<span data-ttu-id="83546-131">Windows Server 2008 R2 서비스 팩 1 (SP1) \* \* 또는 Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="83546-131">Windows Server 2008 R2 with Service Pack 1 (SP1)\*\* or Windows Server 2012</span></span> | <span data-ttu-id="83546-132">-PowerShell의 최신 버전은 Windows Management Framework 4.0에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83546-132">- The latest version of PowerShell is available in Windows Management Framework 4.0.</span></span> <span data-ttu-id="83546-133">[Microsoft 다운로드 센터](https://go.microsoft.com/fwlink/p/?LinkId=717996)에서 해당 파일을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="83546-133">Search for it on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span>  <br> <span data-ttu-id="83546-134">- [Microsoft 다운로드 센터](https://go.microsoft.com/fwlink/p/?LinkId=717996)에서 .net 4.5.1 이상 버전을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83546-134">- .Net 4.5.1 and later releases are available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span> |
|<span data-ttu-id="83546-135">Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="83546-135">Windows Server 2008</span></span> | <span data-ttu-id="83546-136">- [Microsoft 다운로드 센터](https://go.microsoft.com/fwlink/p/?LinkId=717996)에서 제공 하는 Windows Management Framework 3.0에서 지원 되는 최신 버전의 PowerShell을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83546-136">- The latest supported version of PowerShell is available in Windows Management Framework 3.0, available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span>  <br> <span data-ttu-id="83546-137">- [Microsoft 다운로드 센터](https://go.microsoft.com/fwlink/p/?LinkId=717996)에서 .net 4.5.1 이상 버전을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83546-137">- .Net 4.5.1 and later releases are available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span> |

<span data-ttu-id="83546-138">Azure AD Connect에 대 한 하드웨어, 소프트웨어, 계정 및 사용 권한 요구 사항, SSL 인증서 요구 사항 및 개체 제한에 대 한 자세한 내용은 [Azure Active Directory Connect의 필수 구성 요소](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-prerequisites) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="83546-138">See [Prerequisites for Azure Active Directory Connect](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-prerequisites) for the details of hardware, software, account and permissions requirements, SSL certificate requirements, and object limits for Azure AD Connect.</span></span>
  
<span data-ttu-id="83546-139">또한 Azure AD Connect [버전 릴리스 기록을](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history) 검토 하 여 각 릴리스에서 포함 및 수정 된 항목을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83546-139">You can also review the Azure AD Connect [version release history](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history) to see what is included and fixed in each release.</span></span>

## <a name="2-install-azure-ad-connect-and-configure-directory-synchronization"></a><span data-ttu-id="83546-140">2. Azure AD Connect를 설치 하 고 디렉터리 동기화를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="83546-140">2. Install Azure AD Connect and configure directory synchronization</span></span>

<span data-ttu-id="83546-141">시작 하기 전에 다음을 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="83546-141">Before you begin, make sure you have:</span></span>

- <span data-ttu-id="83546-142">Office 365 전역 관리자의 사용자 이름 및 암호</span><span class="sxs-lookup"><span data-stu-id="83546-142">The user name and password of an Office 365 global admin</span></span>
- <span data-ttu-id="83546-143">AD DS 도메인 관리자의 사용자 이름 및 암호</span><span class="sxs-lookup"><span data-stu-id="83546-143">The user name and password of an AD DS domain administrator</span></span>
- <span data-ttu-id="83546-144">어떤 인증 방법 (PHS, PTA, 페더레이션된)</span><span class="sxs-lookup"><span data-stu-id="83546-144">Which authentication method (PHS, PTA, federated)</span></span>
- <span data-ttu-id="83546-145">[AZURE AD 원활한 sso (Single sign-on)](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-sso) 를 사용 하 고 있는지 여부</span><span class="sxs-lookup"><span data-stu-id="83546-145">Whether you want to use [Azure AD Seamless Single Sign-on (SSO)](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-sso)</span></span>

<span data-ttu-id="83546-146">다음 단계를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="83546-146">Follow these steps:</span></span>

1. <span data-ttu-id="83546-147">[Microsoft 365 관리 센터](https://admin.microsoft.com) 에 로그인https://admin.microsoft.com) 하 고 왼쪽 탐색 창에서 **사용자** \> **활성 사용자** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="83546-147">Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com) (https://admin.microsoft.com) and choose **Users** \> **Active Users** on the left navigation.</span></span>
2. <span data-ttu-id="83546-148">**활성 사용자** 페이지에서 **더** (3 개의 점) \> **디렉터리 동기화**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="83546-148">On the **Active users** page, choose **More** (three dots) \> **Directory synchronization**.</span></span>
  
3. <span data-ttu-id="83546-149">**Azure Active Directory 준비** 페이지에서 **다운로드 센터로 이동을 선택 하 여 Azure AD Connect 도구** 링크를 시작 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="83546-149">On the **Azure Active Directory preparation** page, select the **Go to the Download center to get the Azure AD Connect tool** link to get started.</span></span> 
4. <span data-ttu-id="83546-150">[AZURE Ad connect 및 AZURE Ad Connect Health 설치 로드맵](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap)의 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="83546-150">Follow the steps in [Azure AD Connect and Azure AD Connect Health installation roadmap](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap).</span></span>

## <a name="3-finish-setting-up-domains"></a><span data-ttu-id="83546-151">3. 도메인 설정 마침</span><span class="sxs-lookup"><span data-stu-id="83546-151">3. Finish setting up domains</span></span>

<span data-ttu-id="83546-152">DNS 레코드를 관리 하 여 도메인 설정을 완료 하려면 [Office 365에 대 한 dns 레코드 만들기](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23) 의 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="83546-152">Follow the steps in [Create DNS records for Office 365 when you manage your DNS records](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23) to finish setting up your domains.</span></span>

## <a name="next-step"></a><span data-ttu-id="83546-153">다음 단계</span><span class="sxs-lookup"><span data-stu-id="83546-153">Next step</span></span>

<span data-ttu-id="83546-154">[사용자 계정에 라이선스를 할당](assign-licenses-to-user-accounts.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="83546-154">[Assign licenses to user accounts](assign-licenses-to-user-accounts.md).</span></span>
