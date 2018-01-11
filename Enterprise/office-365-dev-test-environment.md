---
title: "Office 365 개발/테스트 환경"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Strat_O365_Enterprise
- Ent_TLGs
ms.assetid: 4f6035b8-2da3-4cf9-9657-5284d6364f7a
description: "요약:이 테스트 랩 가이드를 사용 하 여 평가 또는 개발/테스트는 Office 365 평가판 구독을 만듭니다."
ms.openlocfilehash: 60ac59f8b6af81ff18a4c41c0ce5d2376bc161e7
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/11/2018
---
# <a name="office-365-devtest-environment"></a><span data-ttu-id="882a1-103">Office 365 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="882a1-103">Office 365 dev/test environment</span></span>

 <span data-ttu-id="882a1-104">**요약:** 이 테스트 랩 가이드를 사용 하 여 평가 또는 개발/테스트는 Office 365 평가판 구독을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="882a1-104">**Summary:** Use this Test Lab Guide to create an Office 365 trial subscription for evaluation or dev/test.</span></span>
  
<span data-ttu-id="882a1-p101">Office 365 평가판 구독을 사용할 수 있으며 응용 프로그램 또는 Office 365의 기능 및 특징을 설명 하기 위해 Office 365 개발/테스트 환경을 만들 수 있습니다. 두 버전 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="882a1-p101">You can use an Office 365 trial subscription and create an Office 365 dev/test environment for applications or to demonstrate features and capabilities of Office 365. There are two versions:</span></span>
  
- <span data-ttu-id="882a1-107">Office 365 개발/테스트 환경 lightweight 주 컴퓨터에서 액세스 하는 Office 365 평가판 구독으로 이루어져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="882a1-107">The lightweight Office 365 dev/test environment consists of an Office 365 trial subscription that you access from your main computer.</span></span>
    
    <span data-ttu-id="882a1-p102">이 환경을 사용 하 여 신속 하 게 하는 기능을 시연 하려는 경우. 간편한 Office 365 개발/테스트 환경에 대 한 2 및 3이 문서의 단계를 완료 합니다.</span><span class="sxs-lookup"><span data-stu-id="882a1-p102">Use this environment when you want to quickly demonstrate a feature. For the lightweight Office 365 dev/test environment, complete phases 2 and 3 of this article.</span></span>
    
- <span data-ttu-id="882a1-p103">Office 365 평가판 구독 및 Microsoft Azure 인프라 서비스에서 호스팅되는 인터넷에 연결 하는 간소화 된 조직 인트라넷의 시뮬레이션 된 엔터프라이즈 Office 365 개발/테스트 환경 구성 됩니다. Microsoft 클라우드에서 완전히이 구성을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="882a1-p103">The simulated enterprise Office 365 dev/test environment consists of an Office 365 trial subscription and a simplified organization intranet connected to the Internet, which is hosted in Microsoft Azure infrastructure services. You can build this configuration completely in the Microsoft cloud.</span></span>
    
    <span data-ttu-id="882a1-p104">기능 또는 유사한 일반적인 조직 네트워크에서 인터넷 또는이 유형의 환경을 필요로 하는 기능에 대 한 연결 하는 환경에서 앱을 설명 하기 위해이 환경을 사용 합니다. 시뮬레이션 된 엔터프라이즈 Office 365 개발/테스트 환경에 대 한 1, 2 및 3이 문서의 단계를 완료 합니다.</span><span class="sxs-lookup"><span data-stu-id="882a1-p104">Use this environment when you want to demonstrate a feature or an app in an environment that resembles a typical organization network connected to the Internet, or for features that require this type of environment. For the simulated enterprise Office 365 dev/test environment, complete phases 1, 2, and 3 of this article.</span></span>
    
> [!NOTE]
> <span data-ttu-id="882a1-p105">Office 365 평가판 구독 30 일 동안의이 환경에 대 한 해야 하는 특정 값을 기록 하려면이 문서를 인쇄 하려면 될 수 있습니다. 다른 30 일에 대 한 내역 구독을 쉽게 확장할 수 있습니다. 영구 개발/테스트 환경에 대 한 만들기 새 적은 수의 라이선스를 사용 하 여 구독을 지불 합니다.</span><span class="sxs-lookup"><span data-stu-id="882a1-p105">You might want to print this article to record the specific values that you will need for this environment over the 30 days of the Office 365 trial subscription. You can easily extend the trail subscription for another 30 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
![Microsoft 클라우드의 테스트 랩 가이드](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> <span data-ttu-id="882a1-118">클릭 [여기](http://aka.ms/catlgstack) 에 한 맵이 하나의 Microsoft 클라우드 테스트 랩 가이드 스택의 모든 문서를 시각적으로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="882a1-118">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-the-base-configuration-in-azure"></a><span data-ttu-id="882a1-119">1 단계: Azure의 기본 구성 만들기</span><span class="sxs-lookup"><span data-stu-id="882a1-119">Phase 1: Create the base configuration in Azure</span></span>

<span data-ttu-id="882a1-120">[기본 구성 개발/테스트 환경](base-configuration-dev-test-environment.md)에 대 한 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="882a1-120">Follow the instructions in [Base Configuration dev/test environment](base-configuration-dev-test-environment.md).</span></span>
  
<span data-ttu-id="882a1-p106">Azure에 구독을 해야 합니다. 이 구성에 대 한 [Azure 무료 평가판](https://azure.microsoft.com/pricing/free-trial/) 을 사용할 수 있습니다. MSDN 또는 Visual Studio 구독이 있는 경우 [Visual Studio 구독자에 대 한 월별 Azure 신용](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="882a1-p106">You will need an Azure subscription. You can use the [Azure Free Trial](https://azure.microsoft.com/pricing/free-trial/) for this configuration. If you have an MSDN or Visual Studio subscription, see [Monthly Azure credit for Visual Studio subscribers](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/).</span></span>
  
<span data-ttu-id="882a1-124">결과 구성은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="882a1-124">Here is the resulting configuration.</span></span>
  
![Azure의 기본 구성 개발/테스트 환경](images/63108214-f716-46ae-9974-072ff15b44a2.png)
  
<span data-ttu-id="882a1-126">이 구성은 Azure 가상 네트워크의 서브넷에서 d c 1, a p p 1을 및 CLIENT1 가상 컴퓨터의 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="882a1-126">This configuration consists of the DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network.</span></span>
  
## <a name="phase-2-create-an-office-365-trial-subscription"></a><span data-ttu-id="882a1-127">2 단계: Office 365 평가판 구독 만들기</span><span class="sxs-lookup"><span data-stu-id="882a1-127">Phase 2: Create an Office 365 trial subscription</span></span>

<span data-ttu-id="882a1-128">Office 365 E5 평가판 구독을 시작 하려면 먼저 가상의 회사 이름 및 새 Microsoft 계정을 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="882a1-128">To start your Office 365 E5 trial subscription, you first need a fictitious company name and a new Microsoft account.</span></span>
  
1. <span data-ttu-id="882a1-p107">하는 Microsoft 샘플 콘텐츠에서 사용 되는 가상의 회사, 회사 이름에 대 한 회사 이름 Contoso의 variant를 사용 하지만 필요 하지 않습니다 하는 것이 좋습니다. 여기에 가상의 회사 이름을 기록: ___</span><span class="sxs-lookup"><span data-stu-id="882a1-p107">We recommend that you use a variant of the company name Contoso for your company name, which is a fictitious company used in Microsoft sample content, but it isn't required. Record your fictitious company name here: _____________________________________</span></span>
    
2. <span data-ttu-id="882a1-p108">새 Microsoft 계정을 등록 하려면 [https://outlook.com](https://outlook.com) 로 이동 하 고 새 전자 메일 계정 및 주소와 계정을 만듭니다. 이 계정을 사용 하 여 Office 365에 등록 됩니다.</span><span class="sxs-lookup"><span data-stu-id="882a1-p108">To sign up for a new Microsoft account, go to [https://outlook.com](https://outlook.com) and create an account with a new email account and address. You will use this account to sign up for Office 365.</span></span>
    
  - <span data-ttu-id="882a1-133">여기에 새 계정의 성과 이름을 기록: ___</span><span class="sxs-lookup"><span data-stu-id="882a1-133">Record the first and last name of your new account here: _______________________________</span></span>
    
  - <span data-ttu-id="882a1-134">여기서 새 전자 메일 계정 주소를 기록: ___@outlook.com</span><span class="sxs-lookup"><span data-stu-id="882a1-134">Record the new email account address here: _____________________________@outlook.com</span></span>
    
### <a name="sign-up-for-an-office-365-e5-trial-subscription"></a><span data-ttu-id="882a1-135">Office 365 E5 평가판 구독에 등록</span><span class="sxs-lookup"><span data-stu-id="882a1-135">Sign up for an Office 365 E5 trial subscription</span></span>

1. <span data-ttu-id="882a1-136">간편한 Office 365 개발/테스트 환경에 대 한 사용자의 컴퓨터에서 인터넷 브라우저를 열고 및 [https://aka.ms/e5trial](https://aka.ms/e5trial)로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="882a1-136">For the lightweight Office 365 dev/test environment, open the Internet browser on your computer and go to [https://aka.ms/e5trial](https://aka.ms/e5trial).</span></span> 
    
    <span data-ttu-id="882a1-137">시뮬레이션 된 엔터프라이즈 Office 365 개발/테스트 환경용:</span><span class="sxs-lookup"><span data-stu-id="882a1-137">For the simulated enterprise Office 365 dev/test environment:</span></span>
    
  - <span data-ttu-id="882a1-138">[Azure 포털](https://portal.azure.com)연결 하는 회사와 CLIENT1\\User1 계정을 합니다.</span><span class="sxs-lookup"><span data-stu-id="882a1-138">From the [Azure portal](https://portal.azure.com), connect to CLIENT1 with the CORP\\User1 account.</span></span>
    
  - <span data-ttu-id="882a1-139">관리자 수준 Windows PowerShell 명령 프롬프트를 열고 하 고 이러한 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="882a1-139">Open an administrator-level Windows PowerShell command prompt, and then run these commands:</span></span>
    
  ```
  Set-ItemProperty -Path "HKLM:\\SOFTWARE\\Microsoft\\Active Setup\\Installed Components\\{A509B1A7-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Set-ItemProperty -Path "HKLM:\\SOFTWARE\\Microsoft\\Active Setup\\Installed Components\\{A509B1A8-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Stop-Process -Name Explorer -Force
  ```

    > [!TIP]
    > <span data-ttu-id="882a1-140">클릭 [여기](https://gallery.technet.microsoft.com/PowerShell-commands-for-fe3d7a34) 이 문서의 모든 PowerShell 명령을 포함 된 텍스트 파일을 가져오도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="882a1-140">Click [here](https://gallery.technet.microsoft.com/PowerShell-commands-for-fe3d7a34) to get a text file that contains all the PowerShell commands in this article.</span></span>
  
  - <span data-ttu-id="882a1-141">시작 화면에서 **Internet Explorer** 를 클릭 하 고 [https://aka.ms/e5trial](https://aka.ms/e5trial)로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="882a1-141">From the Start screen, click **Internet Explorer** and go to [https://aka.ms/e5trial](https://aka.ms/e5trial).</span></span>
    
2. <span data-ttu-id="882a1-142">**알고 있습니다 하기 시작** 페이지에서 다음을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="882a1-142">On the **Welcome, let's get to know you** page, specify:</span></span>
    
  - <span data-ttu-id="882a1-143">실제 위치</span><span class="sxs-lookup"><span data-stu-id="882a1-143">Your physical location</span></span>
    
  - <span data-ttu-id="882a1-144">새 Microsoft 계정의 성과 이름</span><span class="sxs-lookup"><span data-stu-id="882a1-144">The first and last name of your new Microsoft account</span></span>
    
  - <span data-ttu-id="882a1-145">새 전자 메일 계정 주소</span><span class="sxs-lookup"><span data-stu-id="882a1-145">Your new email account address</span></span>
    
  - <span data-ttu-id="882a1-146">회사 전화 번호</span><span class="sxs-lookup"><span data-stu-id="882a1-146">A business phone number</span></span>
    
  - <span data-ttu-id="882a1-147">가상의 회사 이름</span><span class="sxs-lookup"><span data-stu-id="882a1-147">Your fictional company name</span></span>
    
  - <span data-ttu-id="882a1-148">250-999 사용자의 조직 크기는</span><span class="sxs-lookup"><span data-stu-id="882a1-148">An organization size of 250-999 people</span></span>
    
3. <span data-ttu-id="882a1-149">**방금 하나 더 큰 단계**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="882a1-149">Click **Just one more step**.</span></span>
    
4. <span data-ttu-id="882a1-150">**사용자 ID 만들기** 페이지에서 새 전자 메일 주소 후 가상의 회사를 기반으로 사용자 이름을 입력은 @ 기호 (이름 간격을 모두 제거), 다음 암호 (두번클릭)이 새로운 Office 365에 대 한 계정입니다.</span><span class="sxs-lookup"><span data-stu-id="882a1-150">On the **Create your user ID** page, type a user name based on your new email address, your fictional company after the @ sign (remove all spaces in the name), then a password (twice) for this new Office 365 account.</span></span>
    
    <span data-ttu-id="882a1-151">안전한 위치에 입력 한 암호를 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="882a1-151">Record the password that you typed in a secure location.</span></span>
    
    <span data-ttu-id="882a1-152">여기에서 **조직 이름**, 라고 하 여 가상의 회사 이름을 기록: ___</span><span class="sxs-lookup"><span data-stu-id="882a1-152">Record your fictional company name, to be referred to as the **organization name**, here: ________________________________________</span></span>
    
5. <span data-ttu-id="882a1-153">**내 계정 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="882a1-153">Click **Create my account**.</span></span>
    
6. <span data-ttu-id="882a1-p109">**에서 다음을 확인 합니다. 것입니다. 하지 않습니다. A. 로봇.** 페이지, 텍스트 지원 전화기의 전화번호를 입력 하 고 **텍스트 하기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="882a1-p109">On the **Prove. You're. Not. A. Robot.** page, type the phone number of your text-capable phone, and then click **Text me**.</span></span>
    
7. <span data-ttu-id="882a1-156">수신 된 텍스트 메시지에서 확인 코드를 입력 하 고 ****을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="882a1-156">Type the verification code from the received text message, and then click **Next**.</span></span>
    
8. <span data-ttu-id="882a1-157">URL을 기록 로그인 페이지 여기 (선택한 복사본): ___</span><span class="sxs-lookup"><span data-stu-id="882a1-157">Record the sign-in page URL here (select and copy): ___________________________________________</span></span>
    
9. <span data-ttu-id="882a1-158">ID를 기록 사용자 여기 (선택한 복사본): ___.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="882a1-158">Record the user ID here (select and copy): __________________________________.onmicrosoft.com</span></span>
    
    <span data-ttu-id="882a1-159">이 값은 **Office 365 전역 관리자의 이름**으로 참조할 수 됩니다.</span><span class="sxs-lookup"><span data-stu-id="882a1-159">This value will be referred to as the **Office 365 global administrator name**.</span></span>
    
10. <span data-ttu-id="882a1-160">**이동 준비가 되었습니다.**표시 되 면이 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="882a1-160">When you see **You're ready to go**, click it.</span></span>
    
11. <span data-ttu-id="882a1-161">다음 페이지에서 Office 365를 설정을 완료 하 고 모든 타일을 사용할 수 있을 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="882a1-161">On the next page, wait until Office 365 completes setting up and all the tiles are available.</span></span>
    
<span data-ttu-id="882a1-162">Office Online 서비스 및 Office 365 관리 센터를 액세스할 수 있는 주요 Office 365 포털 페이지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="882a1-162">You should see main Office 365 portal page from which you can access Office Online services and the Office 365 Admin center.</span></span>
  
<span data-ttu-id="882a1-163">시뮬레이션 된 엔터프라이즈 Office 365 개발/테스트 환경에 대 한 결과 구성을 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="882a1-163">For the simulated enterprise Office 365 dev/test environment, here is your resulting configuration.</span></span>
  
![Office 365 개발/테스트 환경](images/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
<span data-ttu-id="882a1-165">이 구성은 다음으로 이루어집니다.</span><span class="sxs-lookup"><span data-stu-id="882a1-165">This configuration consists of:</span></span> 
  
- <span data-ttu-id="882a1-166">D c 1, a p p 1을 및 CLIENT1 가상 컴퓨터는 Azure 가상 네트워크의 서브넷에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="882a1-166">The DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network.</span></span>
    
- <span data-ttu-id="882a1-167">Office 365 e 5 평가판 구독 합니다.</span><span class="sxs-lookup"><span data-stu-id="882a1-167">An Office 365 E5 Trial Subscription.</span></span>
    
## <a name="phase-3-configure-your-office-365-trial-subscription"></a><span data-ttu-id="882a1-168">3 단계: Office 365 평가판 구독 구성</span><span class="sxs-lookup"><span data-stu-id="882a1-168">Phase 3: Configure your Office 365 trial subscription</span></span>

<span data-ttu-id="882a1-169">이 단계에서 추가 사용자 및 SharePoint Online 팀 사이트와 함께 Office 365 구독을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="882a1-169">In this phase, you configure your Office 365 subscription with additional users and SharePoint Online team sites.</span></span>
  
<span data-ttu-id="882a1-170">첫째, 4 개의 새로운 사용자 추가 및 e 5 라이선스를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="882a1-170">First, you add four new users and assign them E5 licenses.</span></span>
  
<span data-ttu-id="882a1-171">[Office 365 PowerShell 연결](https://technet.microsoft.com/library/dn975125.aspx) 에 지침을 사용 하 여 PowerShell 모듈을 설치 하 고에서 새로운 Office 365 구독에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="882a1-171">Use the instructions in [Connect to Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) to install the PowerShell modules and connect to your new Office 365 subscription from:</span></span>
  
- <span data-ttu-id="882a1-172">사용하는 컴퓨터(경량 Office 365 개발/테스트 환경)</span><span class="sxs-lookup"><span data-stu-id="882a1-172">Your computer (for the lightweight Office 365 dev/test environment).</span></span>
    
- <span data-ttu-id="882a1-173">(시뮬레이션 된 엔터프라이즈 Office 365 개발/테스트 환경)에 대 한 CLIENT1 가상 컴퓨터로 합니다.</span><span class="sxs-lookup"><span data-stu-id="882a1-173">The CLIENT1 virtual machine (for the simulated enterprise Office 365 dev/test environment).</span></span>
    
 <span data-ttu-id="882a1-174">Windows PowerShell 자격 증명 요청 대화 상자에서 Office 365 전역 관리자 이름을 입력 합니다 (예: jdoe@contosotoycompany.onmicrosoft.com) 및 암호입니다.</span><span class="sxs-lookup"><span data-stu-id="882a1-174">In the Windows PowerShell Credential Request dialog box, type the Office 365 global administrator name (example: jdoe@contosotoycompany.onmicrosoft.com) and password.</span></span>
  
<span data-ttu-id="882a1-175">조직 이름(예: contosotoycompany), 위치에 대한 2자리 국가 코드를 입력한 후 Windows PowerShell 프롬프트에 대한 Microsoft Azure Active Directory 모듈에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="882a1-175">Fill in your organization name (example: contosotoycompany), the two-character country code for your location, and then run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "user2@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 2" -FirstName User -LastName 2 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

<span data-ttu-id="882a1-176">**New-msoluser** 명령의 디스플레이에서 사용자 2 계정에 대해 생성 된 암호를 확인 하 고 안전한 위치에 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="882a1-176">From the display of the **New-MsolUser** command, note the generated password for the User 2 account and record it in a safe location.</span></span>
  
<span data-ttu-id="882a1-177">Windows PowerShell 프롬프트에 대한 Microsoft Azure Active Directory 모듈에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="882a1-177">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "user3@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 3" -FirstName User -LastName 3 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

<span data-ttu-id="882a1-178">**New-msoluser** 명령의 디스플레이에서 사용자 3 계정에 대해 생성 된 암호를 확인 하 고 안전한 위치에 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="882a1-178">From the display of the **New-MsolUser** command, note the generated password for the User 3 account and record it in a safe location.</span></span>
  
<span data-ttu-id="882a1-179">Windows PowerShell 프롬프트에 대한 Microsoft Azure Active Directory 모듈에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="882a1-179">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "user4@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 4" -FirstName User -LastName 4 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

<span data-ttu-id="882a1-180">**New-msoluser** 명령의 디스플레이에서 사용자 4 계정에 대해 생성 된 암호를 확인 하 고 안전한 위치에 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="882a1-180">From the display of the **New-MsolUser** command, note the generated password for the User 4 account and record it in a safe location.</span></span>
  
<span data-ttu-id="882a1-181">Windows PowerShell 프롬프트에 대한 Microsoft Azure Active Directory 모듈에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="882a1-181">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "user5@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 5" -FirstName User -LastName 5 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

<span data-ttu-id="882a1-182">**New-msoluser** 명령의 디스플레이에서 사용자 5 계정에 대해 생성 된 암호를 확인 하 고 안전한 위치에 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="882a1-182">From the display of the **New-MsolUser** command, note the generated password for the User 5 account and record it in a safe location.</span></span>
  
<span data-ttu-id="882a1-183">다음으로 판매를 프로덕션에 대 한 3 개의 새 SharePoint Online 팀 사이트 만들기 및 부서를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="882a1-183">Next, you create three new SharePoint Online team sites for the Sales, Production, and Support departments.</span></span>
  
### <a name="create-three-new-sharepoint-online-team-sites"></a><span data-ttu-id="882a1-184">3 개의 새 SharePoint Online 팀 사이트 만들기</span><span class="sxs-lookup"><span data-stu-id="882a1-184">Create three new SharePoint Online team sites</span></span>

1. <span data-ttu-id="882a1-185">[SharePoint Online 관리 셸](https://go.microsoft.com/fwlink/p/?LinkId=255251) 설치 (은 x64 버전).</span><span class="sxs-lookup"><span data-stu-id="882a1-185">Install the [SharePoint Online Management Shell](https://go.microsoft.com/fwlink/p/?LinkId=255251) (the x64 version).</span></span>
    
2. <span data-ttu-id="882a1-186">**시작**을 클릭 하 고 **sharepoint**입력 **SharePoint Online 관리 셸**을 차례로 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="882a1-186">Click **Start**, type **sharepoint**, and then click **SharePoint Online Management Shell**.</span></span>
    
3. <span data-ttu-id="882a1-187">조직 이름을 입력 (예: contosotoycompany), 다음 SharePoint Online 서비스에 연결 하는 SharePoint Online 관리 셸 프롬프트에서 다음 명령을 실행 하 고</span><span class="sxs-lookup"><span data-stu-id="882a1-187">Fill in your organization name (example: contosotoycompany), and then run the following commands from the SharePoint Online Management Shell prompt to connect to the SharePoint Online service</span></span>
```
$orgName="<organization name>"
$spURL="https://" + $orgName + "-admin.sharepoint.com"
Connect-SPOService -Url $spURL
```

4. <span data-ttu-id="882a1-188">**Microsoft SharePoint Online 관리 셸** 대화 상자에서 Office 365 전역 관리자 이름을 입력 합니다 (예: jdoe@contosotoycompany.onmicrosoft.com) 및 암호를 한 다음 **로그인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="882a1-188">In the **Microsoft SharePoint Online Management Shell** dialog box, type the Office 365 global administrator name (example: jdoe@contosotoycompany.onmicrosoft.com) and password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="882a1-189">세 새 팀 사이트를 만드는 (판매, 프로덕션 및 지원)는 Office 365 전역 관리자 이름을 입력 하 고 SharePoint Online 관리 셸 프롬프트에서 다음 명령을 실행 하는 다음:</span><span class="sxs-lookup"><span data-stu-id="882a1-189">To create three new team sites (Sales, Production, and Support), fill in the Office 365 global administrator name, and then run the following commands from the SharePoint Online Management Shell prompt:</span></span>
    
  ```
  $owner = "<global administrator account name>"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/sales"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Sales site collection" -Template "STS#0"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/production"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Production site collection" -Template "STS#0"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/support"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Support site collection" -Template "STS#0"
  ```

6. <span data-ttu-id="882a1-190">이러한 새 사이트의 Url을 나열 하려면이 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="882a1-190">Run this command to list the URLs of these new sites:</span></span>
    
  ```
  Get-SPOSite | Where URL -like "*/sites/*" | Sort URL | Select URL
  ```

7. <span data-ttu-id="882a1-191">Internet Explorer에서 프로덕션 부서에 대 한 기본 SharePoint Online 팀 사이트를 참조 하는 프로덕션 사이트의 URL을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="882a1-191">In Internet Explorer, enter the URL of the Production site to see the default SharePoint Online team site for the Production department.</span></span>
    
## <a name="record-values-for-future-reference"></a><span data-ttu-id="882a1-192">나중에 참조할 수에 대 한 레코드 값</span><span class="sxs-lookup"><span data-stu-id="882a1-192">Record values for future reference</span></span>

<span data-ttu-id="882a1-193">(영문) 또는이 테스트 환경에 있는 추가 테스트 랩 가이드를 배포에 대 한 이러한 값을 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="882a1-193">Record these values for working with or deploying additional Test Lab Guides in this test environment:</span></span>
  
- <span data-ttu-id="882a1-194">Office 365 전역 관리자 이름: ___.onmicrosoft.com (에서 9 단계 중 2 단계)</span><span class="sxs-lookup"><span data-stu-id="882a1-194">Office 365 global administrator name: ____________________________________.onmicrosoft.com (from step 9 of Phase 2)</span></span>
    
    <span data-ttu-id="882a1-195">또한 안전한 위치에이 계정에 대 한 암호를 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="882a1-195">Also record the password for this account in a secure location.</span></span>
    
- <span data-ttu-id="882a1-196">평가판 구독 조직 이름: ___ (에서 4 단계 중 2 단계)</span><span class="sxs-lookup"><span data-stu-id="882a1-196">Your trial subscription organization name: _______________________________________________ (from step 4 of Phase 2)</span></span>
    
- <span data-ttu-id="882a1-197">사용자 2에 대 한 계정을 나열 하려면 사용자 3, 4 사용자 및 사용자 5 Windows Azure Active Directory 모듈에 대 한 Windows PowerShell 프롬프트에서 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="882a1-197">To list the accounts for User 2, User 3, User 4, and User 5, run the following command from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
    
  ```
  Get-MSolUser | Sort UserPrincipalName | Select UserPrincipalName
  ```

    <span data-ttu-id="882a1-198">여기에 계정 이름을 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="882a1-198">Record the account names here:</span></span>
    
  - <span data-ttu-id="882a1-199">2 사용자 계정 이름: user2@___.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="882a1-199">User 2 account name: user2@_______________________________________________.onmicrosoft.com</span></span>
    
  - <span data-ttu-id="882a1-200">3 사용자 계정 이름: user3@___.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="882a1-200">User 3 account name: user3@_______________________________________________.onmicrosoft.com</span></span>
    
  - <span data-ttu-id="882a1-201">4 사용자 계정 이름: user4@___.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="882a1-201">User 4 account name: user4@_______________________________________________.onmicrosoft.com</span></span>
    
  - <span data-ttu-id="882a1-202">5 사용자 계정 이름: user5@___.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="882a1-202">User 5 account name: user5@_______________________________________________.onmicrosoft.com</span></span>
    
    <span data-ttu-id="882a1-203">또한 안전한 위치에 이러한 계정에 대 한 암호를 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="882a1-203">Also record the passwords for these accounts in a secure location.</span></span>
    
- <span data-ttu-id="882a1-204">판매를 프로덕션에 대 한 Url을 나열 하 고 팀 사이트를 지원 하려면 SharePoint Online 관리 셸 프롬프트에서 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="882a1-204">To list the URLs for the Sales, Production, and Support team sites, run the following command from the SharePoint Online Management Shell prompt:</span></span>
    
  ```
  Get-SPOSite | Where URL -like "*/sites/*" | Sort URL | Select URL
  ```

  - <span data-ttu-id="882a1-205">프로덕션 사이트 URL: https://___.sharepoint.com/sites/production</span><span class="sxs-lookup"><span data-stu-id="882a1-205">Production site URL: https://______________________________________________.sharepoint.com/sites/production</span></span>
    
  - <span data-ttu-id="882a1-206">판매 사이트 URL: https://___.sharepoint.com/sites/sales</span><span class="sxs-lookup"><span data-stu-id="882a1-206">Sales site URL: https://______________________________________________.sharepoint.com/sites/sales</span></span>
    
  - <span data-ttu-id="882a1-207">사이트 URL을 지원: https://___.sharepoint.com/sites/support</span><span class="sxs-lookup"><span data-stu-id="882a1-207">Support site URL: https://______________________________________________.sharepoint.com/sites/support</span></span>
    
## <a name="next-steps"></a><span data-ttu-id="882a1-208">다음 단계</span><span class="sxs-lookup"><span data-stu-id="882a1-208">Next steps</span></span>

<span data-ttu-id="882a1-209">이러한 추가 문서를 사용 하 여 Office 365 개발/테스트 환경에서:</span><span class="sxs-lookup"><span data-stu-id="882a1-209">Use these additional articles in your Office 365 dev/test environment:</span></span>
  
- [<span data-ttu-id="882a1-210">Office 365 개발/테스트 환경용 DirSync</span><span class="sxs-lookup"><span data-stu-id="882a1-210">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="882a1-211">Office 365 개발/테스트 환경에 대해 다단계 인증</span><span class="sxs-lookup"><span data-stu-id="882a1-211">Multi-factor authentication for your Office 365 dev/test environment</span></span>](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="882a1-212">Office 365 개발/테스트 환경에 대 한 페더레이션된 id</span><span class="sxs-lookup"><span data-stu-id="882a1-212">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="882a1-213">Office 365 개발/테스트 환경에 대 한 클라우드 응용 프로그램 보안</span><span class="sxs-lookup"><span data-stu-id="882a1-213">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="882a1-214">Office 365 개발/테스트 환경에 대 한 위협 보호 고급</span><span class="sxs-lookup"><span data-stu-id="882a1-214">Advanced Threat Protection for your Office 365 dev/test environment</span></span>](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="882a1-215">Office 365 개발/테스트 환경에 대 한 고급 eDiscovery</span><span class="sxs-lookup"><span data-stu-id="882a1-215">Advanced eDiscovery for your Office 365 dev/test environment</span></span>](advanced-ediscovery-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="882a1-216">Office 365 개발/테스트 환경에서 중요 한 파일 보호</span><span class="sxs-lookup"><span data-stu-id="882a1-216">Sensitive file protection in the Office 365 dev/test environment</span></span>](sensitive-file-protection-in-the-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="882a1-217">격리 된 SharePoint Online 팀 사이트 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="882a1-217">Isolated SharePoint Online team site dev/test environment</span></span>](isolated-sharepoint-online-team-site-dev-test-environment.md)
    
- [<span data-ttu-id="882a1-218">데이터 분류 및 Office 365 개발/테스트 환경에서 레이블 지정</span><span class="sxs-lookup"><span data-stu-id="882a1-218">Data classification and labeling in the Office 365 dev/test environment</span></span>](data-classification-and-labeling-in-the-office-365-dev-test-environment.md)
    
<span data-ttu-id="882a1-219">Office 365 개발/테스트 환경을 추가로 Microsoft 클라우드 서비스를 포함 하도록 확장:</span><span class="sxs-lookup"><span data-stu-id="882a1-219">Extend your Office 365 dev/test environment to include additional Microsoft cloud offerings:</span></span>
  
- [<span data-ttu-id="882a1-220">Microsoft 365 엔터프라이즈 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="882a1-220">The Microsoft 365 Enterprise dev/test environment</span></span>](the-microsoft-365-enterprise-dev-test-environment.md)
    
- [<span data-ttu-id="882a1-221">Office 365 및 Dynamics 365 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="882a1-221">Office 365 and Dynamics 365 dev/test environment</span></span>](office-365-and-dynamics-365-dev-test-environment.md)
    
## <a name="see-also"></a><span data-ttu-id="882a1-222">참고 항목</span><span class="sxs-lookup"><span data-stu-id="882a1-222">See Also</span></span>

[<span data-ttu-id="882a1-223">클라우드 도입 TLG(테스트 랩 가이드)</span><span class="sxs-lookup"><span data-stu-id="882a1-223">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="882a1-224">Office 365 및 Dynamics 365 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="882a1-224">Office 365 and Dynamics 365 dev/test environment</span></span>](office-365-and-dynamics-365-dev-test-environment.md)
  
[<span data-ttu-id="882a1-225">클라우드 채택 및 하이브리드 솔루션</span><span class="sxs-lookup"><span data-stu-id="882a1-225">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)


