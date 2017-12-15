---
title: "PowerShell Office 365에 연결"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- O365ITProTrain
- DecEntMigration
- apr17entnews
- Ent_Office_Other
ms.assetid: 5ebc0e21-b72d-46d8-96fa-00643b18eaec
description: "요약: Office 365 PowerShell을 사용 하 여 명령줄에서 Office 365 관리 센터 작업을 수행 하 여 Office 365 조직에 연결 합니다."
ms.openlocfilehash: 3ac368a3d3584c15e1d0c26104616e8258a78e7b
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2017
---
# <a name="connect-to-office-365-powershell"></a><span data-ttu-id="77c60-103">PowerShell Office 365에 연결</span><span class="sxs-lookup"><span data-stu-id="77c60-103">Connect to Office 365 PowerShell</span></span>

 <span data-ttu-id="77c60-104">**요약:** Office 365 PowerShell을 사용 하 여 명령줄에서 Office 365 관리 작업을 수행 하 여 Office 365 조직에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="77c60-104">**Summary:** Connect to your Office 365 organization using Office 365 PowerShell to perform Office 365 administration tasks from the command line.</span></span>
  
<span data-ttu-id="77c60-p101">Office 365 PowerShell을 사용 하면 명령줄에서 Office 365 설정을 관리할 수 있습니다. 3 단계 과정 필요한 소프트웨어를 설치, 필요한 소프트웨어를 실행 한 다음 Office 365 조직에 연결 위치를 Office 365 PowerShell에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="77c60-p101">Office 365 PowerShell lets you to manage your Office 365 settings from the command line. Connecting to Office 365 PowerShell is a simple three-step process where you install the required software, run the required software, and then connect to your Office 365 organization.</span></span> 

<span data-ttu-id="77c60-107">Note는 이러한 연결 지침은 [Azure ActiveDirectory (MSOnline)](https://go.microsoft.com/fwlink/p/?LinkId=528113)항목의 것과 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="77c60-107">Note that these connection instructions are the same as those in the topic [Azure ActiveDirectory (MSOnline)](https://go.microsoft.com/fwlink/p/?LinkId=528113).</span></span>
  
> [!TIP]
> <span data-ttu-id="77c60-p102">**PowerShell의 새로운 기능?** [PowerShell 비디오 개요 (영문)](http://technet.microsoft.com/library/https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx), LinkedIn 학습에 의해 제공자를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="77c60-p102">**New to PowerShell?** See a [video Overview of PowerShell](http://technet.microsoft.com/library/https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx), brought to you by LinkedIn Learning.</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="77c60-110">시작하기 전에 알아야 할 내용</span><span class="sxs-lookup"><span data-stu-id="77c60-110">What do you need to know before you begin?</span></span>

- <span data-ttu-id="77c60-111">예상 완료 시간: 5분</span><span class="sxs-lookup"><span data-stu-id="77c60-111">Estimated time to complete: 5 minutes</span></span>
    
- <span data-ttu-id="77c60-112">다음 Windows 버전을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77c60-112">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="77c60-113">10 Windows, Windows 8.1, Windows 8 또는 Windows 7 서비스 팩 1 (SP1)</span><span class="sxs-lookup"><span data-stu-id="77c60-113">Windows 10, Windows 8.1, Windows 8 or Windows 7 Service Pack 1 (SP1)</span></span> 
    
  - <span data-ttu-id="77c60-114">Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 또는 Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="77c60-114">Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2 SP1</span></span>
    
    > [!NOTE]
    ><span data-ttu-id="77c60-p103">64 비트 버전의 Windows 사용 합니다. 32 비트 버전의 Microsoft Azure Active Directory 모듈에 대 한 Windows PowerShell에 대 한 지원 2014 년 10 월에에서 중단 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="77c60-p103">Use a 64-bit version of Windows. Support for the 32-bit version the Microsoft Azure Active Directory Module for Windows PowerShell was discontinued in October of 2014.</span></span>
    
-  <span data-ttu-id="77c60-p104">Office 365 작동 또는 학교 계정을 사용 하는 이러한 절차에 대 한 요구를 Office 365 관리자 역할의 구성원 이어야 합니다. 자세한 내용은 [Office 365에 대 한 관리자 역할](https://go.microsoft.com/fwlink/p/?LinkId=532367)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="77c60-p104">The Office 365 work or school account that you use for these procedures needs to be a member of an Office 365 admin role. For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span></span>
    
## <a name="step-1-install-required-software"></a><span data-ttu-id="77c60-119">1단계: 필수 소프트웨어 설치</span><span class="sxs-lookup"><span data-stu-id="77c60-119">Step 1: Install required software</span></span>

<span data-ttu-id="77c60-p105">다음이 단계 연결할 때마다 하지 컴퓨터에 한 번만 필요 합니다. 주기적으로 최신 버전의 소프트웨어를 설치 하려면 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77c60-p105">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1.  <span data-ttu-id="77c60-122">64 비트 버전의 Microsoft Online Services 로그인 도우미 설치: [IT 전문가 RTW에 대 한 Microsoft Online Services 로그인 도우미](https://go.microsoft.com/fwlink/p/?LinkId=286152)합니다.</span><span class="sxs-lookup"><span data-stu-id="77c60-122">Install the 64-bit version of the Microsoft Online Services Sign-in Assistant: [Microsoft Online Services Sign-in Assistant for IT Professionals RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span></span>
    
2. <span data-ttu-id="77c60-123">이러한 단계는 Microsoft Azure Active Directory 모듈에 대 한 Windows PowerShell의 64 비트 버전을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="77c60-123">Install the 64-bit version of the Microsoft Azure Active Directory Module for Windows PowerShell with these steps:</span></span>
    
  - <span data-ttu-id="77c60-124">[Azure Active Directory 연결](http://connect.microsoft.com/site1164/Downloads/DownloadDetails.aspx?DownloadID=59185) 웹 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="77c60-124">Open the [Azure Active Directory Connection](http://connect.microsoft.com/site1164/Downloads/DownloadDetails.aspx?DownloadID=59185) web page.</span></span>
    
  - <span data-ttu-id="77c60-125">페이지의 맨 아래에 **다운로드에서 파일** 을에서 **AdministrationConfig-V1.1.166.0-GA.msi** 파일에 대 한 **다운로드** 를 클릭 하 고 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="77c60-125">In **Files in Download** at the bottom of the page, click **Download** for the **AdministrationConfig-V1.1.166.0-GA.msi** file, and then install it.</span></span>
    
## <a name="step-2-open-the-windows-azure-active-directory-module"></a><span data-ttu-id="77c60-126">2단계: Windows Azure Active Directory 모듈 열기</span><span class="sxs-lookup"><span data-stu-id="77c60-126">Step 2: Open the Windows Azure Active Directory Module</span></span>

1. <span data-ttu-id="77c60-127">찾기 및 Windows의 버전에 따라 다음 방법 중 하나를 사용 하 여 Microsoft Azure Active Directory 모듈에 대 한 Windows PowerShell을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="77c60-127">Find and open the Microsoft Azure Active Directory Module for Windows PowerShell by using one of the following methods based on your version of Windows:</span></span>
    
  - <span data-ttu-id="77c60-128">**시작 메뉴** 바탕 화면에서 **시작**을 클릭 하 고 Azure를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="77c60-128">**Start menu** From the desktop, click **Start**, and then type Azure.</span></span>
    
  - <span data-ttu-id="77c60-129">**No 시작 메뉴** 이러한 방법 중 하나를 사용 하 여 검색 forAzure 합니다.</span><span class="sxs-lookup"><span data-stu-id="77c60-129">**No Start menu** Search forAzure using any of these methods:</span></span>
    
  - <span data-ttu-id="77c60-130">시작 화면에서 빈 영역을 클릭 하 고 Azure를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="77c60-130">On the Start screen, click an empty area, and type Azure.</span></span>
    
  - <span data-ttu-id="77c60-p106">바탕 화면 또는 시작 화면에서 Windows 키 + Q를 누릅니다. 검색 참을 Azure를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="77c60-p106">On the desktop or the Start screen, press the Windows key+Q. In the Search charm, type Azure.</span></span>
    
  - <span data-ttu-id="77c60-p107">바탕 화면 또는 시작 화면에서 커서를 오른쪽 위 모서리 또는 살짝 참을 표시 하려면 화면 오른쪽 가장자리에서 왼쪽으로 이동 합니다. 검색 참을 선택 하 고 **Azure**를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="77c60-p107">On the desktop or the Start screen, move your cursor to the upper-right corner, or swipe left from the right edge of the screen to show the charms. Select the Search charm, and type **Azure**.</span></span>
    
2. <span data-ttu-id="77c60-135">결과에서 **Microsoft Azure Active Directory 모듈에 대 한 Windows PowerShell**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="77c60-135">In the results, click **Microsoft Azure Active Directory Module for Windows PowerShell**.</span></span>
    
## <a name="step-3-connect-to-your-office-365-subscription"></a><span data-ttu-id="77c60-136">3 단계: Office 365 구독에 연결</span><span class="sxs-lookup"><span data-stu-id="77c60-136">Step 3: Connect to your Office 365 subscription</span></span>
<span data-ttu-id="77c60-137"><a name="step3"> </a></span><span class="sxs-lookup"><span data-stu-id="77c60-137"></span></span>

<span data-ttu-id="77c60-138">연결 하는 *계정 이름 및 암호* :</span><span class="sxs-lookup"><span data-stu-id="77c60-138">To connect with just an  *account name and password*  :</span></span>
  
1. <span data-ttu-id="77c60-139">**Microsoft Azure Active Directory 모듈에 대 한 Windows PowerShell** 명령 창에 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="77c60-139">In the **Microsoft Azure Active Directory Module for Windows PowerShell** command window, run the following commands.</span></span>
    
  ```
  $UserCredential = Get-Credential
Connect-MsolService -Credential $UserCredential
  ```

2. <span data-ttu-id="77c60-140">**Windows PowerShell 자격 증명 요청** 대화 상자에서 Office 365 작업 또는 학교 계정 사용자 이름 및 암호를 입력 한 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="77c60-140">In the **Windows PowerShell Credential Request** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>
    
<span data-ttu-id="77c60-141">*다단계 인증 (MFA)* 와 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="77c60-141">To connect with  *multi-factor authentication (MFA)*  :</span></span>
  
1. <span data-ttu-id="77c60-142">**Microsoft Azure Active Directory 모듈에 대 한 Windows PowerShell** 명령 창에 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="77c60-142">In the **Microsoft Azure Active Directory Module for Windows PowerShell** command window, run the following command.</span></span>
    
  ```
  Connect-MsolService
  ```

2. <span data-ttu-id="77c60-143">**PowerShell Azure Active Directory** 대화 상자에서 Office 365 작업 또는 학교 계정 사용자 이름 및 암호를 입력 한 다음 **로그인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="77c60-143">In the **Azure Active Directory PowerShell** dialog box, type your Office 365 work or school account user name and password, and then click **Sign in**.</span></span>
    
3. <span data-ttu-id="77c60-144">확인 코드와 같은 추가 인증 정보를 제공 하려면 **PowerShell Azure Active Directory** 대화 상자의 지침에 따라 하 고 **로그인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="77c60-144">Follow the instructions in the **Azure Active Directory PowerShell** dialog box to provide additional authentication information, such as a verification code, and then click **Sign in**.</span></span>
    
## <a name="how-do-you-know-this-worked"></a><span data-ttu-id="77c60-145">작동 여부는 어떻게 확인합니까?</span><span class="sxs-lookup"><span data-stu-id="77c60-145">How do you know this worked?</span></span>
<span data-ttu-id="77c60-146"><a name="step3"> </a></span><span class="sxs-lookup"><span data-stu-id="77c60-146"></span></span>

<span data-ttu-id="77c60-p108">모든 오류가 하지 않으면 하는 경우 성공적으로 연결한 합니다. Office 365 cmdlet을 실행 하는 빠른 테스트는- **Get-msoluser** 예-하 고 결과 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="77c60-p108">If you don't receive any errors, you connected successfully. A quick test is to run an Office 365 cmdlet—for example, **Get-MsolUser** —and see the results.</span></span>
  
<span data-ttu-id="77c60-149">오류가 발생하면 다음 요구 사항을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="77c60-149">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="77c60-p109">**일반적인 문제는 잘못 된 암호는**입니다. 3 단계를 다시 실행 합니다. 및 입력 하면 사용자 이름 및 암호를 살펴보아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="77c60-p109">**A common problem is an incorrect password**. Run Step 3 again. and pay close attention to the user name and password you enter.</span></span>
    
- <span data-ttu-id="77c60-p110">**Azure Active Directory 모듈 PowerShell 용 Microsoft Windows를 실행 하려면 Microsoft.NET Framework 3.5 합니다. 사용자의 컴퓨터에서 _x_ 기능이 활성화 되어**합니다. 사용자의 컴퓨터에 최신 버전이 설치 (예: 4 또는 4.5 것 같습니다. _x_),.NET Framework의 이전 버전과 호환성 수 사용 하거나 사용 하지 않도록 이전 버전과 하지만 합니다. 자세한 내용은 다음 항목을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="77c60-p110">**The Microsoft Azure Active Directory Module for Windows PowerShell requires that the Microsoft .NET Framework 3.5. _x_ feature is enabled on your computer**. It's likely that your computer has a newer version installed (for example, 4 or 4.5. _x_), but backwards compatibility with older versions of the .NET Framework can be enabled or disabled. For more information, see the following topics:</span></span>
    
  - <span data-ttu-id="77c60-157">Windows Server 2012 또는 Windows Server 2012 r 2에 대 한 [역할 및 추가 기능 마법사를 사용 하 여.NET Framework 3.5 활성화](https://go.microsoft.com/fwlink/p/?LinkId=532368) 를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="77c60-157">For Windows Server 2012 or Windows Server 2012 R2, see [Enable .NET Framework 3.5 by using the Add Roles and Features Wizard](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span></span>
    
  - <span data-ttu-id="77c60-158">Windows 8 또는 Windows 8.1 [Windows 8 또는 8.1에서.NET Framework 3.5를 설치](https://go.microsoft.com/fwlink/p/?LinkId=532369) 를 참조합니다</span><span class="sxs-lookup"><span data-stu-id="77c60-158">For Windows 8 or Windows 8.1, see [Installing the .NET Framework 3.5 on Windows 8 or 8.1](https://go.microsoft.com/fwlink/p/?LinkId=532369)</span></span>
    
  - <span data-ttu-id="77c60-159">Windows 7 또는 Windows Server 2008 r 2에 대 한 참조 [는 Azure Active Directory에 대 한 Windows PowerShell 모듈을 열 수 없습니다](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span><span class="sxs-lookup"><span data-stu-id="77c60-159">For Windows 7 or Windows Server 2008 R2, see [You can't open the Azure Active Directory Module for Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span></span>
    
- <span data-ttu-id="77c60-p111">**버전의 Microsoft Azure Active Directory 모듈에 대 한 Windows PowerShell에 최신이 아닐 수 있습니다.** 을 확인 하려면 Office 365 PowerShell 또는 Microsoft Azure Active Directory 모듈에 대 한 Windows PowerShell에서 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="77c60-p111">**Your version of the Microsoft Azure Active Directory Module for Windows PowerShell might be out of date.** To check, run the following command in Office 365 PowerShell or the Microsoft Azure Active Directory Module for Windows PowerShell:</span></span>
    
  ```
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    <span data-ttu-id="77c60-162">반환 되는 버전 번호를 1.0.8070.2 값 보다 작은 경우 Microsoft Azure Active Directory 모듈에 대 한 Windows PowerShell을 제거 하 고 1 단계에서에서 링크에서 최신 버전을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="77c60-162">If the version number returned is lower than the value 1.0.8070.2, uninstall the Microsoft Azure Active Directory Module for Windows PowerShell and install the latest version from the link in Step 1.</span></span>
    
- <span data-ttu-id="77c60-163">**연결 오류 메시지가 표시 되는 경우이 항목을 참조:** ["Connect-msolservice: 유형의 예외가 발생 했습니다" 오류](https://go.microsoft.com/fwlink/p/?LinkId=532377)합니다.</span><span class="sxs-lookup"><span data-stu-id="77c60-163">**If you receive a connection error, see this topic:** ["Connect-MsolService: Exception of type was thrown" error](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span></span>
    
## <a name="connect-with-the-azure-active-directory-v2-powershell-module"></a><span data-ttu-id="77c60-164">Azure Active Directory V2 PowerShell 모듈을 사용하 여 연결</span><span class="sxs-lookup"><span data-stu-id="77c60-164">Connect with the Azure Active Directory V2 PowerShell module</span></span>
<span data-ttu-id="77c60-165"><a name="ConnectV2"> </a></span><span class="sxs-lookup"><span data-stu-id="77c60-165"></span></span>

<span data-ttu-id="77c60-166">[Azure Active Directory V2 PowerShell 모듈](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)의 새 cmdlet를 필요로 하는 절차에 대해 다음이 단계를 사용 하 여 모듈을 설치 하 고 Office 365 구독에 연결 하려면:</span><span class="sxs-lookup"><span data-stu-id="77c60-166">For procedures that require the new cmdlets in the [Azure Active Directory V2 PowerShell module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory), use these steps to install the module and connect to your Office 365 subscription:</span></span>
  
1. <span data-ttu-id="77c60-167">관리자 권한의 Windows PowerShell 명령 프롬프트를 엽니다(관리자 권한으로 Windows PowerShell 실행).</span><span class="sxs-lookup"><span data-stu-id="77c60-167">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
    
2. <span data-ttu-id="77c60-168">**관리자: Windows PowerShell** 명령 창에서는이 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="77c60-168">In the **Administrator: Windows PowerShell** command window, run this command:</span></span>
    
  ```
  Install-Module -Name AzureAD 
  ```

<span data-ttu-id="77c60-169">신뢰할 수 있는 저장소에서 모듈을 설치 하는 방법에 대 한 메시지가 표시 되 면 **Y** 를 입력 하 고 ENTER 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="77c60-169">If prompted about installing a module from an untrusted repository, type **Y** and press ENTER.</span></span>
    
3. <span data-ttu-id="77c60-170">새로운 모듈 설치가 완료되면 이러한 명령을 사용하여 Office 365 구독에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="77c60-170">When the installation of the new module is complete, use these commands to connect to your Office 365 subscription:</span></span>
    
  -  <span data-ttu-id="77c60-171">수 있는 *계정 이름 및 암호* :</span><span class="sxs-lookup"><span data-stu-id="77c60-171">With an *account name and password*  :</span></span>
    
  ```
  $UserCredential = Get-Credential
Connect-AzureAD -Credential $UserCredential
  ```

 <span data-ttu-id="77c60-172">**Windows PowerShell 자격 증명 요청** 대화 상자에서 Office 365 작업 또는 학교 계정 사용자 이름 및 암호를 입력 한 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="77c60-172">In the **Windows PowerShell Credential Request** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>
    
  - <span data-ttu-id="77c60-173">*다단계 인증 (MFA)* :</span><span class="sxs-lookup"><span data-stu-id="77c60-173">With  *multi-factor authentication (MFA)*  :</span></span>
    
  ```
  Connect-AzureAD
  ```

<span data-ttu-id="77c60-174">**PowerShell Azure Active Directory** 대화 상자에서 Office 365 작업 또는 학교 계정 사용자 이름 및 암호를 입력 한 다음 **로그인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="77c60-174">In the **Azure Active Directory PowerShell** dialog box, type your Office 365 work or school account user name and password, and then click **Sign in**.</span></span>
    
<span data-ttu-id="77c60-175">확인 코드와 같은 추가 인증 정보를 제공 하려면 **PowerShell Azure Active Directory** 대화 상자의 지침에 따라 하 고 **로그인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="77c60-175">Follow the instructions in the **Azure Active Directory PowerShell** dialog box to provide additional authentication information, such as a verification code, and then click **Sign in**.</span></span>
    
<span data-ttu-id="77c60-176">를 연결한 후 [Azure Active Directory V2 PowerShell 모듈](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)에 대 한 새 cmdlet을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77c60-176">After connecting, you can use the new cmdlets for the [Azure Active Directory V2 PowerShell module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="77c60-177">See also</span><span class="sxs-lookup"><span data-stu-id="77c60-177">See also</span></span>

#### 

[<span data-ttu-id="77c60-178">Office 365 PowerShell로 Office 365 관리</span><span class="sxs-lookup"><span data-stu-id="77c60-178">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="77c60-179">Office 365 PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="77c60-179">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
  
[<span data-ttu-id="77c60-180">단일 Windows PowerShell 창에서 모든 Office 365 서비스에 연결</span><span class="sxs-lookup"><span data-stu-id="77c60-180">Connect to all Office 365 services in a single Windows PowerShell window</span></span>](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
#### 

[<span data-ttu-id="77c60-181">Get-자격 증명</span><span class="sxs-lookup"><span data-stu-id="77c60-181">Get-Credential</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389618)
  
[<span data-ttu-id="77c60-182">연결 MsolService</span><span class="sxs-lookup"><span data-stu-id="77c60-182">Connect-MsolService</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532375)

