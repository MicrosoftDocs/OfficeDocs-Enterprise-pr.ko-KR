---
title: PowerShell Office 365에 연결
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/16/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- O365ITProTrain
- Ent_Office_Other
ms.assetid: 5ebc0e21-b72d-46d8-96fa-00643b18eaec
description: '요약: Office 365 PowerShell을 사용 하 여 명령줄에서 관리 센터 작업을 수행 하 여 Office 365 조직에 연결 합니다.'
ms.openlocfilehash: d9bee7060f599120d2d6036c45b44e485ea9a0bd
ms.sourcegitcommit: a3e2b2e58c328238c15d3f9daf042ea3de9d66be
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/30/2018
ms.locfileid: "25849894"
---
# <a name="connect-to-office-365-powershell"></a><span data-ttu-id="01196-103">PowerShell Office 365에 연결</span><span class="sxs-lookup"><span data-stu-id="01196-103">Connect to Office 365 PowerShell</span></span>

 <span data-ttu-id="01196-104">**요약:** Office 365 PowerShell을 사용 하 여 명령줄에서 관리 작업을 수행 하 여 Office 365 조직에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="01196-104">**Summary:** Connect to your Office 365 organization using Office 365 PowerShell to perform administration tasks from the command line.</span></span>
  
<span data-ttu-id="01196-p101">Office 365 PowerShell을 사용 하면 명령줄에서 Office 365 설정을 관리할 수 있습니다. 필요한 소프트웨어를 설치 하 고 다음 Office 365 조직에 연결 과정은 Office 365 PowerShell에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="01196-p101">Office 365 PowerShell lets you to manage your Office 365 settings from the command line. Connecting to Office 365 PowerShell is a simple process where you install the required software and then connect to your Office 365 organization.</span></span> 

<span data-ttu-id="01196-107">Office 365에 연결 하 고 사용자 계정, 그룹 및 라이선스 관리를 사용 하는 PowerShell 모듈의 두 버전 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01196-107">There are two versions of the PowerShell module that you use to connect to Office 365 and administer user accounts, groups, and licenses:</span></span>

- <span data-ttu-id="01196-108">Azure PowerShell Active Directory 그래프 (cmdlet 이름에 **AzureAD** 포함)에 대 한</span><span class="sxs-lookup"><span data-stu-id="01196-108">Azure Active Directory PowerShell for Graph (cmdlets include **AzureAD** in their name)</span></span> 
- <span data-ttu-id="01196-109">Microsoft Azure Active Directory 모듈에 대 한 Windows PowerShell (cmdlet 이름에 **MSol** 포함)</span><span class="sxs-lookup"><span data-stu-id="01196-109">Microsoft Azure Active Directory Module for Windows PowerShell (cmdlets include **MSol** in their name)</span></span> 

<span data-ttu-id="01196-p102">이 문서의 날짜 그래프 모듈에 대 한 Active Directory Azure PowerShell 완전히 해도 사용자, 그룹 및 라이선스 관리에 대 한 Microsoft Azure Active Directory 모듈에 대 한 Windows PowerShell 모듈의 cmdlet의 기능 . 대부분의 경우에서 두 버전을 사용 하 여 지정 해야 합니다. 안전 하 게 동일한 컴퓨터에 두 버전을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01196-p102">As of the date of this article, the Azure Active Directory PowerShell for Graph module does not completely replace the functionality in the cmdlets of Microsoft Azure Active Directory Module for Windows PowerShell module for user, group, and license administration. In many cases, you need to use both versions. You can safely install both versions on the same computer.</span></span>

> [!TIP]
> <span data-ttu-id="01196-p103">**PowerShell을 처음 사용하시나요?** [PowerShell의 비디오 개요](https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx)를 보고 LinkedIn Learning을 통해 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01196-p103">**New to PowerShell?** See a [video Overview of PowerShell](https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx), brought to you by LinkedIn Learning.</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="01196-115">시작하기 전에 알아야 할 내용</span><span class="sxs-lookup"><span data-stu-id="01196-115">What do you need to know before you begin?</span></span>

- <span data-ttu-id="01196-116">예상 완료 시간: 5분</span><span class="sxs-lookup"><span data-stu-id="01196-116">Estimated time to complete: 5 minutes</span></span>
    
- <span data-ttu-id="01196-117">다음 Windows 버전을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01196-117">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="01196-118">10 Windows, Windows 8.1, Windows 8 또는 Windows 7 서비스 팩 1 (SP1)</span><span class="sxs-lookup"><span data-stu-id="01196-118">Windows 10, Windows 8.1, Windows 8, or Windows 7 Service Pack 1 (SP1)</span></span> 
    
  - <span data-ttu-id="01196-119">Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 또는 Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="01196-119">Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2 SP1</span></span>
    
    > [!NOTE]
    ><span data-ttu-id="01196-p104">Windows 64비트 버전을 사용하세요. 32비트 버전의 Microsoft PowerShell용 Windows Azure Active Directory 모듈은 2014년 10월에 중단되었습니다.</span><span class="sxs-lookup"><span data-stu-id="01196-p104">Use a 64-bit version of Windows. Support for the 32-bit version the Microsoft Azure Active Directory Module for Windows PowerShell was discontinued in October of 2014.</span></span>
    
-  <span data-ttu-id="01196-p105">이 절차는 Office 365 관리자 역할의 구성원 인 사용자를 위한것입니다. 자세한 내용은 [Office 365에 대 한 관리자 역할](https://go.microsoft.com/fwlink/p/?LinkId=532367)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="01196-p105">These procedures are intended for users who are members of an Office 365 admin role. For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span></span>


## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="01196-124">그래프 모듈에 대 한 Active Directory Azure PowerShell을 사용 하 여 연결</span><span class="sxs-lookup"><span data-stu-id="01196-124">Connect with the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="01196-125">Cmdlet 이름에 **AzureAD** 를 포함 하는 [그래프에 대 한 Azure Active Directory PowerShell](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) 모듈에 명령 합니다.</span><span class="sxs-lookup"><span data-stu-id="01196-125">Commands in the [Azure Active Directory PowerShell for Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) module have **AzureAD** in their cmdlet name.</span></span>

<span data-ttu-id="01196-126">그래프 모듈에 대 한 Azure Active Directory PowerShell에서 새 cmdlet을 필요로 하는 절차에 대 한 모듈을 설치 하 고 Office 365 구독에 연결 하려면 다음이 단계를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="01196-126">For procedures that require the new cmdlets in the Azure Active Directory PowerShell for Graph module, use these steps to install the module and connect to your Office 365 subscription.</span></span>

>[!Note]
><span data-ttu-id="01196-127">다른 버전의 Microsoft Windows에 대 한 지원에 대 한 정보에 대 한 [그래프 모듈에 대 한 Azure Active Directory PowerShell](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) 를 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="01196-127">See [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) for information about the support for different versions of Microsoft Windows.</span></span>
>

### <a name="step-1-install-required-software"></a><span data-ttu-id="01196-128">1단계: 필수 소프트웨어 설치</span><span class="sxs-lookup"><span data-stu-id="01196-128">Step 1: Install required software</span></span>

<span data-ttu-id="01196-p106">다음이 단계 연결할 때마다 하지 컴퓨터에 한 번만 필요 합니다. 주기적으로 최신 버전의 소프트웨어를 설치 하려면 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01196-p106">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1. <span data-ttu-id="01196-131">관리자 권한의 Windows PowerShell 명령 프롬프트를 엽니다(관리자 권한으로 Windows PowerShell 실행).</span><span class="sxs-lookup"><span data-stu-id="01196-131">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
    
2. <span data-ttu-id="01196-132">\*\* 관리자에서 Windows PowerShell\*\* 명령 창에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="01196-132">In the **Administrator: Windows PowerShell** command window, run this command:</span></span>
    
  ```
  Install-Module -Name AzureAD
  ```

<span data-ttu-id="01196-133">신뢰할 수 없는 리포지토리에서 모듈을 설치할지 묻는 메시지가 표시되면 **Y**를 입력하고 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="01196-133">If prompted about installing a module from an untrusted repository, type **Y** and press ENTER.</span></span>

### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a><span data-ttu-id="01196-134">2 단계: Office 365 구독에 대 한 Azure AD에 연결</span><span class="sxs-lookup"><span data-stu-id="01196-134">Step 2: Connect to Azure AD for your Office 365 subscription</span></span>

<span data-ttu-id="01196-135">*다단계 인증 (MFA)* 또는 계정 이름 및 암호를 사용한 Office 365 구독에 대 한 Azure AD에 연결할 (없는 상승 된 되도록) Windows PowerShell 명령 프롬프트에서 다음이 명령 중 하나를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="01196-135">To connect to Azure AD for your Office 365 subscription with an account name and password or with *multi-factor authentication (MFA)*, run one of these commands from a Windows PowerShell command prompt (it does not have to be elevated).</span></span>

|||
|:-------|:-----|
| <span data-ttu-id="01196-136">**Office 365 클라우드**</span><span class="sxs-lookup"><span data-stu-id="01196-136">**Office 365 cloud**</span></span> | <span data-ttu-id="01196-137">**명령**</span><span class="sxs-lookup"><span data-stu-id="01196-137">**Command**</span></span> |
| <span data-ttu-id="01196-138">Office 365 전세계 (+ GCC)</span><span class="sxs-lookup"><span data-stu-id="01196-138">Office 365 Worldwide (+GCC)</span></span> | `Connect-AzureAD` |
| <span data-ttu-id="01196-139">Office 365에서 21 Vianet 운영</span><span class="sxs-lookup"><span data-stu-id="01196-139">Office 365 operated by 21 Vianet</span></span> | `Connect-AzureAD -AzureEnvironmentName AzureChinaCloud` |
| <span data-ttu-id="01196-140">Office 365 Germany</span><span class="sxs-lookup"><span data-stu-id="01196-140">Office 365 Germany</span></span> | `Connect-AzureAD -AzureEnvironmentName AzureGermanyCloud` |
| <span data-ttu-id="01196-141">Office 365 미국 정부 DoD 및 Office 365 미국 정부 GCC 높음</span><span class="sxs-lookup"><span data-stu-id="01196-141">Office 365 U.S. Government DoD and Office 365 U.S. Government GCC High</span></span> | `Connect-AzureAD -AzureEnvironmentName AzureUSGovernment` |
|||

<span data-ttu-id="01196-142">**계정에 로그인** 대화 상자에서 Office 365 작업 또는 학교 계정 사용자 이름 및 암호를 입력 한 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="01196-142">In the **Sign into your account** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>

<span data-ttu-id="01196-143">MFA를 사용 하는 경우 지침에 따라 추가 대화 상자에서을 확인 코드 등의 더 많은 인증 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="01196-143">If you are using MFA, follow the instructions in the additional dialog boxes to provide more authentication information, such as a verification code.</span></span>


<span data-ttu-id="01196-144">를 연결한 후 [그래프 모듈에 대 한 Azure Active Directory PowerShell](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)에 대 한 새 cmdlet을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01196-144">After connecting, you can use the new cmdlets for the [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span></span>
  

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="01196-145">Windows PowerShell용 Microsoft Azure Active Directory 모듈에 연결</span><span class="sxs-lookup"><span data-stu-id="01196-145">Connect with the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="01196-146">Windows PowerShell용 Microsoft Azure Active Directory 모듈의 명령에는 cmdlet 이름에 **Msol**이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01196-146">Commands in the Microsoft Azure Active Directory Module for Windows PowerShell have **Msol** in their cmdlet name.</span></span>
    
### <a name="step-1-install-required-software"></a><span data-ttu-id="01196-147">1단계: 필수 소프트웨어 설치</span><span class="sxs-lookup"><span data-stu-id="01196-147">Step 1: Install required software</span></span>

<span data-ttu-id="01196-p107">다음이 단계 연결할 때마다 하지 컴퓨터에 한 번만 필요 합니다. 주기적으로 최신 버전의 소프트웨어를 설치 하려면 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01196-p107">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1.  <span data-ttu-id="01196-150">64비트 버전의 Microsoft Online Services 로그인 도우미를 설치합니다.[IT 전문가용 Microsoft Online Services 로그인 도우미 RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152)를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="01196-150">Install the 64-bit version of the Microsoft Online Services Sign-in Assistant: [Microsoft Online Services Sign-in Assistant for IT Professionals RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span></span>
    
2. <span data-ttu-id="01196-151">다음 단계에 따라 Windows PowerShell용 Microsoft Azure Active Directory 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="01196-151">Install the Microsoft Azure Active Directory Module for Windows PowerShell with these steps:</span></span>
    
  - <span data-ttu-id="01196-152">관리자 권한의 Windows PowerShell 명령 프롬프트를 엽니다(관리자 권한으로 Windows PowerShell 실행).</span><span class="sxs-lookup"><span data-stu-id="01196-152">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
  - <span data-ttu-id="01196-153">**Install-Module MSOnline** 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="01196-153">Run the **Install-Module MSOnline** command.</span></span>
  - <span data-ttu-id="01196-154">NuGet 공급자를 설치할지 묻는 메시지가 표시되면 **Y**를 입력하고 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="01196-154">If prompted to install the NuGet provider, type **Y** and press ENTER.</span></span>
  - <span data-ttu-id="01196-155">PSGallery에서 모듈을 설치할지 묻는 메시지가 표시되면 **Y**를 입력하고 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="01196-155">If prompted to install the module from PSGallery, type **Y** and press ENTER.</span></span>
    
### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a><span data-ttu-id="01196-156">2 단계: Office 365 구독에 대 한 Azure AD에 연결</span><span class="sxs-lookup"><span data-stu-id="01196-156">Step 2: Connect to Azure AD for your Office 365 subscription</span></span>

<span data-ttu-id="01196-157">*다단계 인증 (MFA)* 또는 계정 이름 및 암호를 사용한 Office 365 구독에 대 한 Azure AD에 연결할 (없는 상승 된 되도록) Windows PowerShell 명령 프롬프트에서 다음이 명령 중 하나를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="01196-157">To connect to Azure AD for your Office 365 subscription with an account name and password or with *multi-factor authentication (MFA)*, run one of these commands from a Windows PowerShell command prompt (it does not have to be elevated).</span></span>

|||
|:-------|:-----|
| <span data-ttu-id="01196-158">**Office 365 클라우드**</span><span class="sxs-lookup"><span data-stu-id="01196-158">**Office 365 cloud**</span></span> | <span data-ttu-id="01196-159">**명령**</span><span class="sxs-lookup"><span data-stu-id="01196-159">**Command**</span></span> |
| <span data-ttu-id="01196-160">Office 365 전세계 (+ GCC)</span><span class="sxs-lookup"><span data-stu-id="01196-160">Office 365 Worldwide (+GCC)</span></span> | `Connect-MsolService` |
| <span data-ttu-id="01196-161">Office 365에서 21 Vianet 운영</span><span class="sxs-lookup"><span data-stu-id="01196-161">Office 365 operated by 21 Vianet</span></span> | `Connect-MsolService -AzureEnvironmentName AzureChinaCloud` |
| <span data-ttu-id="01196-162">Office 365 Germany</span><span class="sxs-lookup"><span data-stu-id="01196-162">Office 365 Germany</span></span> | `Connect-MsolService -AzureEnvironmentName AzureGermanyCloud` |
| <span data-ttu-id="01196-163">Office 365 미국 정부 DoD 및 Office 365 미국 정부 GCC 높음</span><span class="sxs-lookup"><span data-stu-id="01196-163">Office 365 U.S. Government DoD and Office 365 U.S. Government GCC High</span></span> | `Connect-MsolService -AzureEnvironmentName USGovernment` |
|||

<span data-ttu-id="01196-164">**계정에 로그인** 대화 상자에서 Office 365 작업 또는 학교 계정 사용자 이름 및 암호를 입력 한 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="01196-164">In the **Sign into your account** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>

<span data-ttu-id="01196-165">MFA를 사용 하는 경우 지침에 따라 추가 대화 상자에서을 확인 코드 등의 더 많은 인증 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="01196-165">If you are using MFA, follow the instructions in the additional dialog boxes to provide more authentication information, such as a verification code.</span></span>

### <a name="how-do-you-know-this-worked"></a><span data-ttu-id="01196-166">작동 여부는 어떻게 확인하나요?</span><span class="sxs-lookup"><span data-stu-id="01196-166">How do you know this worked?</span></span>

<span data-ttu-id="01196-p108">어떠한 오류도 전송되지 않으면 성공적으로 연결되었음을 의미합니다. 빠른 테스트는 Office 365 cmdlet(예: **Get-MsolUser** )을 실행하여 결과를 확인하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="01196-p108">If you don't receive any errors, you connected successfully. A quick test is to run an Office 365 cmdlet—for example, **Get-MsolUser** —and see the results.</span></span>
  
<span data-ttu-id="01196-169">오류가 발생하면 다음 요구 사항을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="01196-169">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="01196-p109">**일반적인 문제는 잘못 된 암호는**입니다. 2 단계를 다시 실행 합니다. 및 입력 하면 사용자 이름 및 암호를 살펴보아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="01196-p109">**A common problem is an incorrect password**. Run Step 2 again. and pay close attention to the user name and password you enter.</span></span>
    
- <span data-ttu-id="01196-p110">**Windows PowerShell용 Microsoft Azure Active Directory 모듈을 사용하려면 컴퓨터에서 Microsoft .NET Framework 3.5.* x* 기능이 사용되도록 설정되어야 합니다.\*\* 컴퓨터 최신 버전(예: 4 또는 4.5.\* x\*)이 설치되어 있을 수 있지만 이전 버전의 .NET Framework와의 호환성이 사용되거나 사용되지 않도록 설정되어 있을 수 있습니다. 자세한 내용은 다음 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="01196-p110">**The Microsoft Azure Active Directory Module for Windows PowerShell requires that the Microsoft .NET Framework 3.5.* x* feature is enabled on your computer**. It's likely that your computer has a newer version installed (for example, 4 or 4.5.* x*), but backwards compatibility with older versions of the .NET Framework can be enabled or disabled. For more information, see the following topics:</span></span>
    
  - <span data-ttu-id="01196-175">Windows Server 2012 또는 Windows Server 2012 R2의 경우 [역할 및 기능 추가 마법사를 사용하여 .NET Framework 3.5를 사용 가능하도록 설정](https://go.microsoft.com/fwlink/p/?LinkId=532368)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="01196-175">For Windows Server 2012 or Windows Server 2012 R2, see [Enable .NET Framework 3.5 by using the Add Roles and Features Wizard](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span></span>
    
  - <span data-ttu-id="01196-176">Windows 7 또는 Windows Server 2008 R2의 경우 [Windows PowerShell용 Azure Active Directory 모듈을 열 수 없음](https://go.microsoft.com/fwlink/p/?LinkId=532370)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="01196-176">For Windows 7 or Windows Server 2008 R2, see [You can't open the Azure Active Directory Module for Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span></span>

  - <span data-ttu-id="01196-177">Windows 10, Windows 8.1 및 Windows 8의 경우 [Windows 10, Windows 8.1 및 Windows 8에서.NET Framework 3.5를 설치](https://docs.microsoft.com/en-us/dotnet/framework/install/dotnet-35-windows-10) 를 참조합니다</span><span class="sxs-lookup"><span data-stu-id="01196-177">For Windows 10, Windows 8.1, and Windows 8, see [Install the .NET Framework 3.5 on Windows 10, Windows 8.1, and Windows 8](https://docs.microsoft.com/en-us/dotnet/framework/install/dotnet-35-windows-10)</span></span>

  
- <span data-ttu-id="01196-p111">**사용자의 Microsoft PowerShell용 Windows Azure Active Directory 모듈 버전이 오래되었을 수 있습니다.** 확인하려면 Microsoft PowerShell용 Windows Azure Active Directory 모듈 또는 Office 365 PowerShell에서 다음 명령을 실행하세요.</span><span class="sxs-lookup"><span data-stu-id="01196-p111">**Your version of the Microsoft Azure Active Directory Module for Windows PowerShell might be out of date.** To check, run the following command in Office 365 PowerShell or the Microsoft Azure Active Directory Module for Windows PowerShell:</span></span>
    
  ```
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    <span data-ttu-id="01196-180">반환된 버전 번호가 1.0.8070.2 값보다 낮은 경우 Microsoft PowerShell용 Windows Azure Active Directory 모듈을 제거한 후 1단계의 링크에서 최신 버전을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="01196-180">If the version number returned is lower than the value 1.0.8070.2, uninstall the Microsoft Azure Active Directory Module for Windows PowerShell and install the latest version from the link in Step 1.</span></span>
    
- <span data-ttu-id="01196-181">**연결 오류가 발생하면** ["Connect-MsolService: 형식의 예외가 발생했습니다." 오류](https://go.microsoft.com/fwlink/p/?LinkId=532377) 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="01196-181">**If you receive a connection error, see this topic:** ["Connect-MsolService: Exception of type was thrown" error](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span></span>
    

## <a name="see-also"></a><span data-ttu-id="01196-182">참고 항목</span><span class="sxs-lookup"><span data-stu-id="01196-182">See also</span></span>

- [<span data-ttu-id="01196-183">Office 365 PowerShell 사용한 Office 365 관리</span><span class="sxs-lookup"><span data-stu-id="01196-183">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="01196-184">Office 365 PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="01196-184">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
- [<span data-ttu-id="01196-185">단일 Windows PowerShell 창에서 모든 Office 365 서비스에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="01196-185">Connect to all Office 365 services in a single Windows PowerShell window</span></span>](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
- [<span data-ttu-id="01196-186">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="01196-186">Get-Credential</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389618)
- [<span data-ttu-id="01196-187">Connect-MsolService</span><span class="sxs-lookup"><span data-stu-id="01196-187">Connect-MsolService</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532375)

