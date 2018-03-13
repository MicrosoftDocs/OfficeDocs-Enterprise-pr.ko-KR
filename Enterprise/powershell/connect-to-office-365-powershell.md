---
title: "PowerShell Office 365에 연결"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/02/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- O365ITProTrain
- Ent_Office_Other
ms.assetid: 5ebc0e21-b72d-46d8-96fa-00643b18eaec
description: "요약: Office 365 PowerShell을 통해 Office 365 조직에 연결하여 명령줄에서 Office 365 관리 센터 작업을 수행합니다."
ms.openlocfilehash: a13fcc401a4d00f49dcc4eec2a5acba36075233f
ms.sourcegitcommit: 2cfb30dd7c7a6bc9fa97a98f56ab8fe008504f41
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/09/2018
---
# <a name="connect-to-office-365-powershell"></a><span data-ttu-id="4760a-103">PowerShell Office 365에 연결</span><span class="sxs-lookup"><span data-stu-id="4760a-103">Connect to Office 365 PowerShell</span></span>

 <span data-ttu-id="4760a-104">**요약:**Office 365 PowerShell을 통해 Office 365 조직에 연결하여 명령줄에서 Office 365 관리 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="4760a-104">**Summary:** Connect to your Office 365 organization using Office 365 PowerShell to perform Office 365 administration tasks from the command line.</span></span>
  
<span data-ttu-id="4760a-p101">Office 365 PowerShell을 사용하면 명령줄에서 Office 365 설정을 관리할 수 있습니다. Office 365 PowerShell에 연결하려면 필요한 소프트웨어를 설치하고, 필요한 소프트웨어를 실행하고, Office 365 조직에 연결하는 간단한 세 단계 과정을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="4760a-p101">Office 365 PowerShell lets you to manage your Office 365 settings from the command line. Connecting to Office 365 PowerShell is a simple three-step process where you install the required software, run the required software, and then connect to your Office 365 organization.</span></span> 

<span data-ttu-id="4760a-107">이러한 연결 지침은 [Azure ActiveDirectory(MSOnline)](https://go.microsoft.com/fwlink/p/?LinkId=528113) 항목의 연결 지침과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="4760a-107">Note that these connection instructions are the same as those in the topic [Azure ActiveDirectory (MSOnline)](https://go.microsoft.com/fwlink/p/?LinkId=528113).</span></span>
  
> [!TIP]
> <span data-ttu-id="4760a-p102">**PowerShell을 처음 사용하시나요?** [PowerShell의 비디오 개요](http://technet.microsoft.com/library/https://support.office.com/ko-KR/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx)를 보고 LinkedIn Learning을 통해 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4760a-p102">**New to PowerShell?** See a [video Overview of PowerShell](http://technet.microsoft.com/library/https://support.office.com/ko-KR/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx), brought to you by LinkedIn Learning.</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="4760a-110">시작하기 전에 알아야 할 내용</span><span class="sxs-lookup"><span data-stu-id="4760a-110">What do you need to know before you begin?</span></span>

- <span data-ttu-id="4760a-111">예상 완료 시간: 5분</span><span class="sxs-lookup"><span data-stu-id="4760a-111">Estimated time to complete: 5 minutes</span></span>
    
- <span data-ttu-id="4760a-112">다음 Windows 버전을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4760a-112">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="4760a-113">Windows 10, Windows 8.1, Windows 8 또는 Windows 7 서비스팩 1(SP1)</span><span class="sxs-lookup"><span data-stu-id="4760a-113">Windows 10, Windows 8.1, Windows 8 or Windows 7 Service Pack 1 (SP1)</span></span> 
    
  - <span data-ttu-id="4760a-114">Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 또는 Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="4760a-114">Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2 SP1</span></span>
    
    > [!NOTE]
    ><span data-ttu-id="4760a-p103">Windows 64비트 버전을 사용하세요. 32비트 버전의 Microsoft PowerShell용 Windows Azure Active Directory 모듈은 2014년 10월에 중단되었습니다.</span><span class="sxs-lookup"><span data-stu-id="4760a-p103">Use a 64-bit version of Windows. Support for the 32-bit version the Microsoft Azure Active Directory Module for Windows PowerShell was discontinued in October of 2014.</span></span>
    
-  <span data-ttu-id="4760a-p104">이러한 절차에 사용하는 Office 365회사 또는 학교 계정은 Office 365 관리자 역할의 구성원이어야 합니다. 자세한 내용은 [Office 365 관리자 역할 정보](https://go.microsoft.com/fwlink/p/?LinkId=532367)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4760a-p104">The Office 365 work or school account that you use for these procedures needs to be a member of an Office 365 admin role. For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span></span>

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="4760a-119">Windows PowerShell용 Microsoft Azure Active Directory 모듈에 연결</span><span class="sxs-lookup"><span data-stu-id="4760a-119">Connect with the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="4760a-120">Windows PowerShell용 Microsoft Azure Active Directory 모듈의 명령에는 cmdlet 이름에 **Msol**이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4760a-120">Commands in the Microsoft Azure Active Directory Module for Windows PowerShell have **Msol** in their cmdlet name.</span></span>
    
### <a name="step-1-install-required-software"></a><span data-ttu-id="4760a-121">1단계: 필수 소프트웨어 설치</span><span class="sxs-lookup"><span data-stu-id="4760a-121">Step 1: Install required software</span></span>

<span data-ttu-id="4760a-p105">다음이 단계 연결할 때마다 하지 컴퓨터에 한 번만 필요 합니다. 주기적으로 최신 버전의 소프트웨어를 설치 하려면 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4760a-p105">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1.  <span data-ttu-id="4760a-124">64비트 버전의 Microsoft Online Services 로그인 도우미를 설치합니다.[IT 전문가용 Microsoft Online Services 로그인 도우미 RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152)를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="4760a-124">Install the 64-bit version of the Microsoft Online Services Sign-in Assistant: [Microsoft Online Services Sign-in Assistant for IT Professionals RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span></span>
    
2. <span data-ttu-id="4760a-125">다음 단계에 따라 Windows PowerShell용 Microsoft Azure Active Directory 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="4760a-125">Install the the Microsoft Azure Active Directory Module for Windows PowerShell with these steps:</span></span>
    
  - <span data-ttu-id="4760a-126">관리자 수준 PowerShell 명령 프롬프트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="4760a-126">Open an administrator-level PowerShell command prompt.</span></span>
  - <span data-ttu-id="4760a-127">**Install-Module MSOnline** 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="4760a-127">Run the **Install-Module MSOnline** command.</span></span>
  - <span data-ttu-id="4760a-128">NuGet 공급자를 설치할지 묻는 메시지가 표시되면 **Y**를 입력하고 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="4760a-128">If prompted to install the NuGet provider, type **Y** and press ENTER.</span></span>
  - <span data-ttu-id="4760a-129">PSGallery에서 모듈을 설치할지 묻는 메시지가 표시되면 **Y**를 입력하고 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="4760a-129">If prompted to install the module from PSGallery, type **Y** and press ENTER.</span></span>
  - <span data-ttu-id="4760a-130">설치 후 PowerShell 명령 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="4760a-130">After installation, close the PowerShell command window.</span></span>
    
### <a name="step-2-connect-to-your-office-365-subscription"></a><span data-ttu-id="4760a-131">2단계: Office 365 구독에 연결</span><span class="sxs-lookup"><span data-stu-id="4760a-131">Step 2: Connect to your Office 365 subscription</span></span>
<span data-ttu-id="4760a-132"><a name="step3"> </a></span><span class="sxs-lookup"><span data-stu-id="4760a-132"><a name="step3"> </a></span></span>

<span data-ttu-id="4760a-133">*계정 이름 및 암호*만으로 연결하려면</span><span class="sxs-lookup"><span data-stu-id="4760a-133">To connect with just an *account name and password*:</span></span>
  
1. <span data-ttu-id="4760a-134">Windows PowerShell 명령 프롬프트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="4760a-134">Run a Windows PowerShell command prompt.</span></span>
2. <span data-ttu-id="4760a-135">**Windows PowerShell** 명령 창에 다음 명령을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="4760a-135">In the **Windows PowerShell** command window, run the following commands:</span></span>
    
```
$UserCredential = Get-Credential
Connect-MsolService -Credential $UserCredential
```

3. <span data-ttu-id="4760a-136">**Windows PowerShell 자격 증명 요청** 대화 상자에서 Office 365Office 365회사 또는 학교 계정 사용자 이름과 암호를 입력한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4760a-136">In the **Windows PowerShell Credential Request** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>
    
<span data-ttu-id="4760a-137">*MFA(다단계 인증)*를 사용해서 연결하려면</span><span class="sxs-lookup"><span data-stu-id="4760a-137">To connect with *multi-factor authentication (MFA)*:</span></span>
  
1. <span data-ttu-id="4760a-138">Windows PowerShell 명령 프롬프트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="4760a-138">Run a Windows PowerShell command prompt.</span></span>
2. <span data-ttu-id="4760a-139">**Windows PowerShell용 Microsoft Azure Active Directory 모듈  ** 명령 창에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="4760a-139">In the **Microsoft Azure Active Directory Module for Windows PowerShell** command window, run the following command.</span></span>
    
```
Connect-MsolService
```

3. <span data-ttu-id="4760a-140">**Azure Active Directory PowerShell** 대화 상자에서 Office 365회사 또는 학교 계정 사용자 이름과 암호를 입력한 다음 **로그인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4760a-140">In the **Azure Active Directory PowerShell** dialog box, type your Office 365 work or school account user name and password, and then click **Sign in**.</span></span>
    
4. <span data-ttu-id="4760a-141">** Azure Active Directory PowerShell** 대화 상자의 지침에 따라 인증 코드와 같은 추가 인증 정보를 제공한 다음 **로그인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4760a-141">Follow the instructions in the **Azure Active Directory PowerShell** dialog box to provide additional authentication information, such as a verification code, and then click **Sign in**.</span></span>
    
### <a name="how-do-you-know-this-worked"></a><span data-ttu-id="4760a-142">작동 여부는 어떻게 확인합니까?</span><span class="sxs-lookup"><span data-stu-id="4760a-142">How do you know this worked?</span></span>
<span data-ttu-id="4760a-143"><a name="step3"> </a></span><span class="sxs-lookup"><span data-stu-id="4760a-143"><a name="step3"> </a></span></span>

<span data-ttu-id="4760a-p106">어떠한 오류도 전송되지 않으면 성공적으로 연결되었음을 의미합니다. 빠른 테스트는 Office 365 cmdlet(예: **Get-MsolUser** )을 실행하여 결과를 확인하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="4760a-p106">If you don't receive any errors, you connected successfully. A quick test is to run an Office 365 cmdlet—for example, **Get-MsolUser** —and see the results.</span></span>
  
<span data-ttu-id="4760a-146">오류가 발생하면 다음 요구 사항을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="4760a-146">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="4760a-p107">가장 흔한 문제는 암호를 잘못 입력한 경우입니다. 두 가지 단계를 다시 실행하고 1단계에서 사용자 이름과 암호를 입력할 때 신중하게 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="4760a-p107">**A common problem is an incorrect password**. Run Step 3 again. and pay close attention to the user name and password you enter.</span></span>
    
- <span data-ttu-id="4760a-p108">**Microsoft PowerShell용 Windows Azure Active Directory 모듈 하 고 Microsoft .NET Framework 3.5. _x_ 기능을 컴퓨터에서 사용할 수**. 컴퓨터에 새 버전이 설치 될 (4 또는 4.5 등. _x_), 있지만 이전 버전과 이전 버전과의 호환성을 .NET Framework 사용 또는 사용할 수. 자세한 내용은 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="4760a-p108">**The Microsoft Azure Active Directory Module for Windows PowerShell requires that the Microsoft .NET Framework 3.5. _x_ feature is enabled on your computer**. It's likely that your computer has a newer version installed (for example, 4 or 4.5. _x_), but backwards compatibility with older versions of the .NET Framework can be enabled or disabled. For more information, see the following topics:</span></span>
    
  - <span data-ttu-id="4760a-154">Windows Server 2012 또는 Windows Server 2012 R2의 경우 [역할 및 기능 추가 마법사를 사용하여 .NET Framework 3.5를 사용 가능하도록 설정](https://go.microsoft.com/fwlink/p/?LinkId=532368)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4760a-154">For Windows Server 2012 or Windows Server 2012 R2, see [Enable .NET Framework 3.5 by using the Add Roles and Features Wizard](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span></span>
    
  - <span data-ttu-id="4760a-155">Windows 8 또는 Windows 8.1의 경우 [Windows 8 또는 8.1에.NET Framework 3.5 설치](https://go.microsoft.com/fwlink/p/?LinkId=532369)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4760a-155">For Windows 8 or Windows 8.1, see [Installing the .NET Framework 3.5 on Windows 8 or 8.1](https://go.microsoft.com/fwlink/p/?LinkId=532369)</span></span>
    
  - <span data-ttu-id="4760a-156">Windows 7 또는 Windows Server 2008 R2의 경우 [Windows PowerShell용 Azure Active Directory 모듈을 열 수 없음](https://go.microsoft.com/fwlink/p/?LinkId=532370)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4760a-156">For Windows 7 or Windows Server 2008 R2, see [You can't open the Azure Active Directory Module for Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span></span>
    
- <span data-ttu-id="4760a-p109">**사용자의 Microsoft PowerShell용 Windows Azure Active Directory 모듈 버전이 오래되었을 수 있습니다.** 확인하려면 Microsoft PowerShell용 Windows Azure Active Directory 모듈 또는 Office 365 PowerShell에서 다음 명령을 실행하세요.</span><span class="sxs-lookup"><span data-stu-id="4760a-p109">**Your version of the Microsoft Azure Active Directory Module for Windows PowerShell might be out of date.** To check, run the following command in Office 365 PowerShell or the Microsoft Azure Active Directory Module for Windows PowerShell:</span></span>
    
  ```
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    <span data-ttu-id="4760a-159">반환된 버전 번호가 1.0.8070.2 값보다 낮은 경우 Microsoft PowerShell용 Windows Azure Active Directory 모듈을 제거한 후 1단계의 링크에서 최신 버전을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="4760a-159">If the version number returned is lower than the value 1.0.8070.2, uninstall the Microsoft Azure Active Directory Module for Windows PowerShell and install the latest version from the link in Step 1.</span></span>
    
- <span data-ttu-id="4760a-160">**연결 오류가 발생하면** ["Connect-MsolService: 형식의 예외가 발생했습니다." 오류](https://go.microsoft.com/fwlink/p/?LinkId=532377) 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4760a-160">**If you receive a connection error, see this topic:** ["Connect-MsolService: Exception of type was thrown" error](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span></span>
    
## <a name="connect-with-the-azure-active-directory-v2-powershell-module"></a><span data-ttu-id="4760a-161">Azure Active Directory V2 PowerShell 모듈을 사용하 여 연결</span><span class="sxs-lookup"><span data-stu-id="4760a-161">Connect with the Azure Active Directory V2 PowerShell module</span></span>
<span data-ttu-id="4760a-162"><a name="ConnectV2"> </a></span><span class="sxs-lookup"><span data-stu-id="4760a-162"><a name="ConnectV2"> </a></span></span>

<span data-ttu-id="4760a-163">Azure Active Directory V2 PowerShell 모듈의 명령에는 cmdlet 이름에 “AzureAD”가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4760a-163">Commands in the Azure Active Directory V2 PowerShell module have "AzureAD" in their cmdlet name.</span></span>

<span data-ttu-id="4760a-164">[Azure Active Directory V2 PowerShell 모듈](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)에서 새 cmdlet을 필요로 하는 프로시저의 경우, 이러한 단계를 사용해서 모듈을 설치하고 Office 365 구독에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4760a-164">For procedures that require the new cmdlets in the [Azure Active Directory V2 PowerShell module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory), use these steps to install the module and connect to your Office 365 subscription.</span></span>

### <a name="step-1-install-required-software"></a><span data-ttu-id="4760a-165">1단계: 필수 소프트웨어 설치</span><span class="sxs-lookup"><span data-stu-id="4760a-165">Step 1: Install required software</span></span>

<span data-ttu-id="4760a-p110">다음이 단계 연결할 때마다 하지 컴퓨터에 한 번만 필요 합니다. 주기적으로 최신 버전의 소프트웨어를 설치 하려면 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4760a-p110">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>

  
1. <span data-ttu-id="4760a-168">관리자 권한의 Windows PowerShell 명령 프롬프트를 엽니다(관리자 권한으로 Windows PowerShell 실행).</span><span class="sxs-lookup"><span data-stu-id="4760a-168">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
    
2. <span data-ttu-id="4760a-169">** 관리자에서 Windows PowerShell** 명령 창에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="4760a-169">In the **Administrator: Windows PowerShell** command window, run this command:</span></span>
    
  ```
  Install-Module -Name AzureAD 
  ```

<span data-ttu-id="4760a-170">신뢰할 수 없는 리포지토리에서 모듈을 설치할지 묻는 메시지가 표시되면 **Y**를 입력하고 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="4760a-170">If prompted about installing a module from an untrusted repository, type **Y** and press ENTER.</span></span>


### <a name="step-2-connect-to-office-365"></a><span data-ttu-id="4760a-171">2단계: Office 365에 연결</span><span class="sxs-lookup"><span data-stu-id="4760a-171">Step 2: Connect to Office 365</span></span>

<span data-ttu-id="4760a-172">*계정 이름 및 암호*를 사용하여 Office 365 구독에 연결하려면</span><span class="sxs-lookup"><span data-stu-id="4760a-172">To connect to your Office 365 subscription with an *account name and password*:</span></span>
    
```
$UserCredential = Get-Credential
Connect-AzureAD -Credential $UserCredential
```

<span data-ttu-id="4760a-173">**Windows PowerShell 자격 증명 요청** 대화 상자에서 Office 365Office 365회사 또는 학교 계정 사용자 이름과 암호를 입력한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4760a-173">In the **Windows PowerShell Credential Request** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>
    
<span data-ttu-id="4760a-174">*MFA(다단계 인증)*를 사용하여 Office 365 구독에 연결하려면</span><span class="sxs-lookup"><span data-stu-id="4760a-174">To connect to your Office 365 subscription with *multi-factor authentication (MFA)*:</span></span>

```
Connect-AzureAD
```

<span data-ttu-id="4760a-175">**Azure Active Directory PowerShell** 대화 상자에서 Office 365회사 또는 학교 계정 사용자 이름과 암호를 입력한 다음 **로그인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4760a-175">In the **Azure Active Directory PowerShell** dialog box, type your Office 365 work or school account user name and password, and then click **Sign in**.</span></span>
    
<span data-ttu-id="4760a-176">** Azure Active Directory PowerShell** 대화 상자의 지침에 따라 인증 코드와 같은 추가 인증 정보를 제공한 다음 **로그인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4760a-176">Follow the instructions in the **Azure Active Directory PowerShell** dialog box to provide additional authentication information, such as a verification code, and then click **Sign in**.</span></span>
    
<span data-ttu-id="4760a-177">연결이 되면 [Azure Active Directory V2 PowerShell 모듈](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)의 새 cmdlet을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4760a-177">After connecting, you can use the new cmdlets for the [Azure Active Directory V2 PowerShell module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="4760a-178">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4760a-178">See also</span></span>

[<span data-ttu-id="4760a-179">Office 365 PowerShell 사용한 Office 365 관리</span><span class="sxs-lookup"><span data-stu-id="4760a-179">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="4760a-180">Office 365 PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="4760a-180">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
  
[<span data-ttu-id="4760a-181">단일 Windows PowerShell 창에서 모든 Office 365 서비스에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="4760a-181">Connect to all Office 365 services in a single Windows PowerShell window</span></span>](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)

[<span data-ttu-id="4760a-182">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="4760a-182">Get-Credential</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389618)
  
[<span data-ttu-id="4760a-183">Connect-MsolService</span><span class="sxs-lookup"><span data-stu-id="4760a-183">Connect-MsolService</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532375)

