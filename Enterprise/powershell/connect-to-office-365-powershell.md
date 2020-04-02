---
title: PowerShell Office 365에 연결
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/31/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- LIL_Placement
- O365ITProTrain
- Ent_Office_Other
ms.assetid: 5ebc0e21-b72d-46d8-96fa-00643b18eaec
description: Office 365 PowerShell을 통해 Office 365 조직에 연결하여 명령줄에서 관리 센터 작업을 수행합니다.
ms.openlocfilehash: 642016f734a2a9d7e490d5905a3ed93d7f330ca9
ms.sourcegitcommit: 7f025939c9dad676602bcd7693a8e356821fd456
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/31/2020
ms.locfileid: "43068760"
---
# <a name="connect-to-office-365-powershell"></a><span data-ttu-id="d76e7-103">PowerShell Office 365에 연결</span><span class="sxs-lookup"><span data-stu-id="d76e7-103">Connect to Office 365 PowerShell</span></span>

<span data-ttu-id="d76e7-104">Office 365 PowerShell을 사용하여 명령줄에서 Office 365 설정을 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d76e7-104">Office 365 PowerShell lets you manage your Office 365 settings from the command line.</span></span> <span data-ttu-id="d76e7-105">Office 365 PowerShell에 연결하려면 필요한 소프트웨어를 설치하고 Office 365 조직에 연결하는 간단한 과정을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="d76e7-105">Connecting to Office 365 PowerShell is a simple process where you install the required software and then connect to your Office 365 organization.</span></span> 

<span data-ttu-id="d76e7-106">Office 365 및 관리자 계정, 그룹 및 라이선스에 연결하는 데 사용하는 두 가지 버전의 PowerShell 모듈이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d76e7-106">There are two versions of the PowerShell module that you use to connect to Office 365 and administer user accounts, groups, and licenses:</span></span>

- <span data-ttu-id="d76e7-107">Azure Active Directory PowerShell for Graph(cmdlet의 이름에 **AzureAD** 포함)</span><span class="sxs-lookup"><span data-stu-id="d76e7-107">Azure Active Directory PowerShell for Graph (cmdlets include **AzureAD** in their name)</span></span>
- <span data-ttu-id="d76e7-108">Windows PowerShell용 Microsoft Azure Active Directory 모듈(cmdlet의 이름에 **MSol** 포함)</span><span class="sxs-lookup"><span data-stu-id="d76e7-108">Microsoft Azure Active Directory Module for Windows PowerShell (cmdlets include **MSol** in their name)</span></span> 

<span data-ttu-id="d76e7-109">이 문서의 날짜를 기준으로, Azure Active Directory PowerShell for Graph 모듈이 사용자, 그룹 및 라이선스 관리를 위해 Windows PowerShell용 Microsoft Azure Active Directory 모듈을 완전히 대체하는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="d76e7-109">As of the date of this article, the Azure Active Directory PowerShell for Graph module does not completely replace the functionality in the cmdlets of Microsoft Azure Active Directory Module for Windows PowerShell module for user, group, and license administration.</span></span> <span data-ttu-id="d76e7-110">대부분의 경우, 두 버전을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d76e7-110">In many cases, you need to use both versions.</span></span> <span data-ttu-id="d76e7-111">동일한 컴퓨터에 두 버전을 안전하게 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d76e7-111">You can safely install both versions on the same computer.</span></span>

## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="d76e7-112">시작하기 전에 알아야 할 사항은 무엇인가요?</span><span class="sxs-lookup"><span data-stu-id="d76e7-112">What do you need to know before you begin?</span></span>

<span data-ttu-id="d76e7-113">다음 Windows 버전을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d76e7-113">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="d76e7-114">Windows 10, Windows 8.1, Windows 8 또는 Windows 7 서비스팩 1(SP1)</span><span class="sxs-lookup"><span data-stu-id="d76e7-114">Windows 10, Windows 8.1, Windows 8, or Windows 7 Service Pack 1 (SP1)</span></span> 
    
  - <span data-ttu-id="d76e7-115">Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 또는 Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="d76e7-115">Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2 SP1</span></span>

    > [!NOTE]
    > <span data-ttu-id="d76e7-116">Azure Active Directory PowerShell for Graph 모듈의 경우 PowerShell 버전 5.1 이상을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d76e7-116">For the Azure Active Directory PowerShell for Graph module, you must use PowerShell version 5.1 or later.</span></span> <span data-ttu-id="d76e7-117">Windows PowerShell용 Microsoft Azure Active Directory 모듈의 경우 PowerShell 버전 5.1 이상 PowerShell 버전 6 이하를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d76e7-117">For the Microsoft Azure Active Directory Module for Windows PowerShell module, you must use PowerShell version 5.1 or later up to PowerShell version 6.</span></span> <span data-ttu-id="d76e7-118">PowerShell 버전 7은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d76e7-118">You cannot use PowerShell version 7.</span></span> <span data-ttu-id="d76e7-119">Windows 8.1, Windows 8, Windows 7 Service Pack 1 (SP1), Windows Server 2012 R2, Windows Server 2012 및 Windows Server 2008 R2 SP1의 경우, [Windows Management Framework 5.1](https://www.microsoft.com/download/details.aspx?id=54616)을 다운로드하고 설치합니다. </span><span class="sxs-lookup"><span data-stu-id="d76e7-119">For Windows 8.1, Windows 8, Windows 7 Service Pack 1 (SP1), Windows Server 2012 R2, Windows Server 2012, and Windows Server 2008 R2 SP1, download and install the [Windows Management Framework 5.1](https://www.microsoft.com/download/details.aspx?id=54616).</span></span> 
    
    > [!NOTE]
    > <span data-ttu-id="d76e7-p104">Windows 64비트 버전을 사용하세요. 32비트 버전의 Microsoft PowerShell용 Windows Azure Active Directory 모듈은 2014년 10월에 중단되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d76e7-p104">Use a 64-bit version of Windows. Support for the 32-bit version the Microsoft Azure Active Directory Module for Windows PowerShell was discontinued in October of 2014.</span></span>
    
<span data-ttu-id="d76e7-122">이러한 절차는 Office 365 관리자 역할의 구성원인 사용자를 대상으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="d76e7-122">These procedures are intended for users who are members of an Office 365 admin role.</span></span> <span data-ttu-id="d76e7-123">자세한 내용은 [Office 365 관리자 역할 정보](https://go.microsoft.com/fwlink/p/?LinkId=532367)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d76e7-123">For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span></span>


## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="d76e7-124">그런 다음, Azure Active Directory PowerShell for Graph 모듈에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="d76e7-124">Connect with the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="d76e7-125">Azure Active Directory PowerShell for Graph 모듈의 명령에는 cmdlet 이름에 **AzureAD**가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d76e7-125">Commands in the Azure Active Directory PowerShell for Graph module have **AzureAD** in their cmdlet name.</span></span> <span data-ttu-id="d76e7-126">[Azure Active Directory PowerShell for Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) 모듈 또는 [Azure PowerShell](https://docs.microsoft.com/powershell/azure/install-az-ps?view=azps-3.6.1)을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d76e7-126">You can install the [Azure Active Directory PowerShell for Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) module or [Azure PowerShell](https://docs.microsoft.com/powershell/azure/install-az-ps?view=azps-3.6.1).</span></span>

<span data-ttu-id="d76e7-127">Azure Active Directory PowerShell for Graph 모듈에서 새 cmdlet을 필요로 하는 프로시저의 경우, 이러한 단계를 사용해서 모듈을 설치하고 Office 365 구독에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d76e7-127">For procedures that require the new cmdlets in the Azure Active Directory PowerShell for Graph module, use these steps to install the module and connect to your Office 365 subscription.</span></span>

>[!Note]
><span data-ttu-id="d76e7-128">Microsoft Windows의 여러 버전에 대한 지원 정보는 [Azure Active Directory PowerShell for Graph 모듈](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d76e7-128">See [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) for information about the support for different versions of Microsoft Windows.</span></span>
>

### <a name="step-1-install-required-software"></a><span data-ttu-id="d76e7-129">1단계: 필수 소프트웨어 설치</span><span class="sxs-lookup"><span data-stu-id="d76e7-129">Step 1: Install required software</span></span>

<span data-ttu-id="d76e7-p107">다음이 단계 연결할 때마다 하지 컴퓨터에 한 번만 필요 합니다. 주기적으로 최신 버전의 소프트웨어를 설치 하려면 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d76e7-p107">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1. <span data-ttu-id="d76e7-132">관리자 권한의 Windows PowerShell 명령 프롬프트를 엽니다(관리자 권한으로 Windows PowerShell 실행).</span><span class="sxs-lookup"><span data-stu-id="d76e7-132">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
    
2. <span data-ttu-id="d76e7-133">\*\* 관리자에서 Windows PowerShell\*\* 명령 창에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d76e7-133">In the **Administrator: Windows PowerShell** command window, run this command:</span></span>
    
  ```powershell
  Install-Module -Name AzureAD
  ```

<span data-ttu-id="d76e7-134">신뢰할 수 없는 리포지토리에서 모듈을 설치할지 묻는 메시지가 표시되면 **Y**를 입력하고 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="d76e7-134">If prompted about installing a module from an untrusted repository, type **Y** and press ENTER.</span></span>

### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a><span data-ttu-id="d76e7-135">2단계: Office 365 구독을 위해 Azure AD에 연결</span><span class="sxs-lookup"><span data-stu-id="d76e7-135">Step 2: Connect to Azure AD for your Office 365 subscription</span></span>

<span data-ttu-id="d76e7-136">계정 이름 및 암호를 사용하여 또는 MFA(다중 요소 인증)을 사용하여 Office 365 구독을 위해 Azure AD에 연결하려면, Windows PowerShell 명령 프롬프트(관리자 권한이 아니어도 됨)에서 이 명령 중 하나를 실행하세요.</span><span class="sxs-lookup"><span data-stu-id="d76e7-136">To connect to Azure AD for your Office 365 subscription with an account name and password or with multi-factor authentication (MFA), run one of these commands from a Windows PowerShell command prompt (it does not have to be elevated).</span></span>

|||
|:-------|:-----|
| <span data-ttu-id="d76e7-137">**Office 365 클라우드**</span><span class="sxs-lookup"><span data-stu-id="d76e7-137">**Office 365 cloud**</span></span> | <span data-ttu-id="d76e7-138">**명령**</span><span class="sxs-lookup"><span data-stu-id="d76e7-138">**Command**</span></span> |
| <span data-ttu-id="d76e7-139">Office 365 Worldwide(+GCC)</span><span class="sxs-lookup"><span data-stu-id="d76e7-139">Office 365 Worldwide (+GCC)</span></span> | `Connect-AzureAD` |
| <span data-ttu-id="d76e7-140">21 Vianet이 운영하는 Office 365</span><span class="sxs-lookup"><span data-stu-id="d76e7-140">Office 365 operated by 21 Vianet</span></span> | `Connect-AzureAD -AzureEnvironmentName AzureChinaCloud` |
| <span data-ttu-id="d76e7-141">Office 365 Germany</span><span class="sxs-lookup"><span data-stu-id="d76e7-141">Office 365 Germany</span></span> | `Connect-AzureAD -AzureEnvironmentName AzureGermanyCloud` |
| <span data-ttu-id="d76e7-142">Office 365 미국 국방부(DoD) 및 Office 365 미국 정부 GCC High</span><span class="sxs-lookup"><span data-stu-id="d76e7-142">Office 365 U.S. Government DoD and Office 365 U.S. Government GCC High</span></span> | `Connect-AzureAD -AzureEnvironmentName AzureUSGovernment` |
|||

<span data-ttu-id="d76e7-143">**계정에 로그인하세요** 대화 상자에서, Office 365 회사 또는 학교 계정 사용자 이름 및 암호를 입력한 다음, **확인**을 클릭하세요.</span><span class="sxs-lookup"><span data-stu-id="d76e7-143">In the **Sign into your account** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>

<span data-ttu-id="d76e7-144">MFA를 사용하는 경우, 추가 대화 상자에 있는 지침을 따라서 추가 인증 정보(예: 확인 코드)를 제공하세요.</span><span class="sxs-lookup"><span data-stu-id="d76e7-144">If you are using MFA, follow the instructions in the additional dialog boxes to provide more authentication information, such as a verification code.</span></span>

<span data-ttu-id="d76e7-145">연결 후 [그래프 모듈용 Azure Active Directory PowerShell](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)의 cmdlet을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d76e7-145">After connecting, you can use the cmdlets for the [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span></span>
  

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="d76e7-146">Windows PowerShell용 Microsoft Azure Active Directory 모듈에 연결</span><span class="sxs-lookup"><span data-stu-id="d76e7-146">Connect with the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="d76e7-147">Windows PowerShell용 Microsoft Azure Active Directory 모듈의 명령에는 cmdlet 이름에 **Msol**이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d76e7-147">Commands in the Microsoft Azure Active Directory Module for Windows PowerShell have **Msol** in their cmdlet name.</span></span>

<span data-ttu-id="d76e7-148">PowerShell 버전 7 이상은 Windows PowerShell용 Microsoft Azure Active Directory 모듈 및 이름에 **Msol**이 있는 cmdlet을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d76e7-148">PowerShell version 7 and later do not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="d76e7-149">PowerShell 버전 7 이상의 경우 Azure Active Directory PowerShell for Graph 모듈 또는 Azure PowerShell을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d76e7-149">For PowerShell version 7 and later, you must use the Azure Active Directory PowerShell for Graph module or Azure PowerShell.</span></span>

<span data-ttu-id="d76e7-150">PowerShell Core는 Windows PowerShell용 Microsoft Azure Active Directory 모듈 및 이름에 **Msol**이 있는 cmdlet을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d76e7-150">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="d76e7-151">이러한 cmdlet을 계속 사용하려면 Windows PowerShell에서 이를 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d76e7-151">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span> 
    
### <a name="step-1-install-required-software"></a><span data-ttu-id="d76e7-152">1단계: 필수 소프트웨어 설치</span><span class="sxs-lookup"><span data-stu-id="d76e7-152">Step 1: Install required software</span></span>

<span data-ttu-id="d76e7-p110">다음이 단계 연결할 때마다 하지 컴퓨터에 한 번만 필요 합니다. 주기적으로 최신 버전의 소프트웨어를 설치 하려면 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d76e7-p110">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1.  <span data-ttu-id="d76e7-155">64비트 버전의 Microsoft Online Services 로그인 도우미를 설치합니다.[IT 전문가용 Microsoft Online Services 로그인 도우미 RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152)를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="d76e7-155">Install the 64-bit version of the Microsoft Online Services Sign-in Assistant: [Microsoft Online Services Sign-in Assistant for IT Professionals RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span></span>
    
2. <span data-ttu-id="d76e7-156">다음 단계에 따라 Windows PowerShell용 Microsoft Azure Active Directory 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="d76e7-156">Install the Microsoft Azure Active Directory Module for Windows PowerShell with these steps:</span></span>
    
  - <span data-ttu-id="d76e7-157">관리자 권한의 Windows PowerShell 명령 프롬프트를 엽니다(관리자 권한으로 Windows PowerShell 실행).</span><span class="sxs-lookup"><span data-stu-id="d76e7-157">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
  - <span data-ttu-id="d76e7-158">**Install-Module MSOnline** 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d76e7-158">Run the **Install-Module MSOnline** command.</span></span>
  - <span data-ttu-id="d76e7-159">NuGet 공급자를 설치할지 묻는 메시지가 표시되면 **Y**를 입력하고 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="d76e7-159">If prompted to install the NuGet provider, type **Y** and press ENTER.</span></span>
  - <span data-ttu-id="d76e7-160">PSGallery에서 모듈을 설치할지 묻는 메시지가 표시되면 **Y**를 입력하고 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="d76e7-160">If prompted to install the module from PSGallery, type **Y** and press ENTER.</span></span>
    
### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a><span data-ttu-id="d76e7-161">2단계: Office 365 구독을 위해 Azure AD에 연결</span><span class="sxs-lookup"><span data-stu-id="d76e7-161">Step 2: Connect to Azure AD for your Office 365 subscription</span></span>

<span data-ttu-id="d76e7-162">계정 이름 및 암호를 사용하여 또는 MFA(다중 요소 인증)을 사용하여 Office 365 구독을 위해 Azure AD에 연결하려면, Windows PowerShell 명령 프롬프트(관리자 권한이 아니어도 됨)에서 이 명령 중 하나를 실행하세요.</span><span class="sxs-lookup"><span data-stu-id="d76e7-162">To connect to Azure AD for your Office 365 subscription with an account name and password or with multi-factor authentication (MFA), run one of these commands from a Windows PowerShell command prompt (it does not have to be elevated).</span></span>

|||
|:-------|:-----|
| <span data-ttu-id="d76e7-163">**Office 365 클라우드**</span><span class="sxs-lookup"><span data-stu-id="d76e7-163">**Office 365 cloud**</span></span> | <span data-ttu-id="d76e7-164">**명령**</span><span class="sxs-lookup"><span data-stu-id="d76e7-164">**Command**</span></span> |
| <span data-ttu-id="d76e7-165">Office 365 Worldwide(+GCC)</span><span class="sxs-lookup"><span data-stu-id="d76e7-165">Office 365 Worldwide (+GCC)</span></span> | `Connect-MsolService` |
| <span data-ttu-id="d76e7-166">21 Vianet이 운영하는 Office 365</span><span class="sxs-lookup"><span data-stu-id="d76e7-166">Office 365 operated by 21 Vianet</span></span> | `Connect-MsolService -AzureEnvironment AzureChinaCloud` |
| <span data-ttu-id="d76e7-167">Office 365 Germany</span><span class="sxs-lookup"><span data-stu-id="d76e7-167">Office 365 Germany</span></span> | `Connect-MsolService -AzureEnvironment AzureGermanyCloud` |
| <span data-ttu-id="d76e7-168">Office 365 미국 국방부(DoD) 및 Office 365 미국 정부 GCC High</span><span class="sxs-lookup"><span data-stu-id="d76e7-168">Office 365 U.S. Government DoD and Office 365 U.S. Government GCC High</span></span> | `Connect-MsolService -AzureEnvironment USGovernment` |
|||

<span data-ttu-id="d76e7-169">**계정에 로그인하세요** 대화 상자에서, Office 365 회사 또는 학교 계정 사용자 이름 및 암호를 입력한 다음, **확인**을 클릭하세요.</span><span class="sxs-lookup"><span data-stu-id="d76e7-169">In the **Sign into your account** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>

<span data-ttu-id="d76e7-170">MFA를 사용하는 경우, 추가 대화 상자에 있는 지침을 따라서 추가 인증 정보(예: 확인 코드)를 제공하세요.</span><span class="sxs-lookup"><span data-stu-id="d76e7-170">If you are using MFA, follow the instructions in the additional dialog boxes to provide more authentication information, such as a verification code.</span></span>

### <a name="how-do-you-know-this-worked"></a><span data-ttu-id="d76e7-171">작동 여부는 어떻게 확인하나요?</span><span class="sxs-lookup"><span data-stu-id="d76e7-171">How do you know this worked?</span></span>

<span data-ttu-id="d76e7-p111">어떠한 오류도 전송되지 않으면 성공적으로 연결되었음을 의미합니다. 빠른 테스트는 Office 365 cmdlet(예: **Get-MsolUser** )을 실행하여 결과를 확인하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="d76e7-p111">If you don't receive any errors, you connected successfully. A quick test is to run an Office 365 cmdlet—for example, **Get-MsolUser** —and see the results.</span></span>
  
<span data-ttu-id="d76e7-174">오류가 발생하면 다음 요구 사항을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d76e7-174">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="d76e7-175">**가장 흔한 문제는 암호를 잘못 입력한 경우입니다**.</span><span class="sxs-lookup"><span data-stu-id="d76e7-175">**A common problem is an incorrect password**.</span></span> <span data-ttu-id="d76e7-176">2단계를 다시 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d76e7-176">Run Step 2 again.</span></span> <span data-ttu-id="d76e7-177">사용자 이름과 암호를 입력할 때 신중하게 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d76e7-177">and pay close attention to the user name and password you enter.</span></span>
    
- <span data-ttu-id="d76e7-p113">**Windows PowerShell용 Microsoft Azure Active Directory 모듈을 사용하려면 컴퓨터에서 Microsoft .NET Framework 3.5.* x* 기능이 사용되도록 설정되어야 합니다.\*\* 컴퓨터 최신 버전(예: 4 또는 4.5.\* x\*)이 설치되어 있을 수 있지만 이전 버전의 .NET Framework와의 호환성이 사용되거나 사용되지 않도록 설정되어 있을 수 있습니다. 자세한 내용은 다음 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d76e7-p113">**The Microsoft Azure Active Directory Module for Windows PowerShell requires that the Microsoft .NET Framework 3.5.* x* feature is enabled on your computer**. It's likely that your computer has a newer version installed (for example, 4 or 4.5.* x*), but backwards compatibility with older versions of the .NET Framework can be enabled or disabled. For more information, see the following topics:</span></span>
    
  - <span data-ttu-id="d76e7-180">Windows Server 2012 또는 Windows Server 2012 R2의 경우 [역할 및 기능 추가 마법사를 사용하여 .NET Framework 3.5를 사용 가능하도록 설정](https://go.microsoft.com/fwlink/p/?LinkId=532368)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d76e7-180">For Windows Server 2012 or Windows Server 2012 R2, see [Enable .NET Framework 3.5 by using the Add Roles and Features Wizard](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span></span>
    
  - <span data-ttu-id="d76e7-181">Windows 7 또는 Windows Server 2008 R2의 경우 [Windows PowerShell용 Azure Active Directory 모듈을 열 수 없음](https://go.microsoft.com/fwlink/p/?LinkId=532370)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d76e7-181">For Windows 7 or Windows Server 2008 R2, see [You can't open the Azure Active Directory Module for Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span></span>

  - <span data-ttu-id="d76e7-182">Windows 10, Windows 8.1 및 Windows 8의 경우, [Windows 10, Windows 8.1 및 Windows 8에 .NET Framework 3.5 설치](https://docs.microsoft.com/dotnet/framework/install/dotnet-35-windows-10)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d76e7-182">For Windows 10, Windows 8.1, and Windows 8, see [Install the .NET Framework 3.5 on Windows 10, Windows 8.1, and Windows 8](https://docs.microsoft.com/dotnet/framework/install/dotnet-35-windows-10)</span></span>

  
- <span data-ttu-id="d76e7-p114">**사용자의 Microsoft PowerShell용 Windows Azure Active Directory 모듈 버전이 오래되었을 수 있습니다.** 확인하려면 Microsoft PowerShell용 Windows Azure Active Directory 모듈 또는 Office 365 PowerShell에서 다음 명령을 실행하세요.</span><span class="sxs-lookup"><span data-stu-id="d76e7-p114">**Your version of the Microsoft Azure Active Directory Module for Windows PowerShell might be out of date.** To check, run the following command in Office 365 PowerShell or the Microsoft Azure Active Directory Module for Windows PowerShell:</span></span>
    
  ```powershell
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    <span data-ttu-id="d76e7-185">반환된 버전 번호가 1.0.8070.2 값보다 낮은 경우 Microsoft PowerShell용 Windows Azure Active Directory 모듈을 제거한 후 1단계의 링크에서 최신 버전을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="d76e7-185">If the version number returned is lower than the value 1.0.8070.2, uninstall the Microsoft Azure Active Directory Module for Windows PowerShell and install the latest version from the link in Step 1.</span></span>

- <span data-ttu-id="d76e7-186">**연결 오류가 발생하면** ["Connect-MsolService: 형식의 예외가 발생했습니다." 오류](https://go.microsoft.com/fwlink/p/?LinkId=532377) 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d76e7-186">**If you receive a connection error, see this topic:** ["Connect-MsolService: Exception of type was thrown" error](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span></span>
    
- <span data-ttu-id="d76e7-187">**"Get-Item: path를 찾을 수 없습니다" 라는 오류가 표시 되는 경우 다음 명령을 사용 합니다.**</span><span class="sxs-lookup"><span data-stu-id="d76e7-187">**If you receive a "Get-Item : Cannot find path" error, use this command:**</span></span> 

  ```powershell
  (dir "C:\Program Files\WindowsPowerShell\Modules\MSOnline").Name
 
```

## <a name="see-also"></a><span data-ttu-id="d76e7-188">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d76e7-188">See also</span></span>

- [<span data-ttu-id="d76e7-189">Office 365 PowerShell 사용한 Office 365 관리</span><span class="sxs-lookup"><span data-stu-id="d76e7-189">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="d76e7-190">Office 365 PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="d76e7-190">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
- [<span data-ttu-id="d76e7-191">단일 Windows PowerShell 창에서 모든 Office 365 서비스에 연결</span><span class="sxs-lookup"><span data-stu-id="d76e7-191">Connect to all Office 365 services in a single Windows PowerShell window</span></span>](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
