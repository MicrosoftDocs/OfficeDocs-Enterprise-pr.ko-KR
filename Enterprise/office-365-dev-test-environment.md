---
title: Office 365 개발/테스트 환경
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 08/09/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 4f6035b8-2da3-4cf9-9657-5284d6364f7a
description: '요약: 이 테스트 랩 가이드를 사용하여 평가 또는 개발/테스트를 위한 Office 365 평가판 구독을 만듭니다.'
ms.openlocfilehash: 7a7b12038acf914667655decee52993286faab1e
ms.sourcegitcommit: 4ef8e113fa20b539de1087422455fc26ff123d55
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/19/2019
ms.locfileid: "30574002"
---
# <a name="office-365-devtest-environment"></a><span data-ttu-id="65622-103">Office 365 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="65622-103">Office 365 dev/test environment</span></span>

 <span data-ttu-id="65622-104">**요약:** 이 테스트 랩 가이드를 사용하여 평가 또는 개발/테스트를 위한 Office 365 평가판 구독을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="65622-104">**Summary:** Use this Test Lab Guide to create an Office 365 trial subscription for evaluation or dev/test.</span></span>
  
<span data-ttu-id="65622-p101">Office 365 평가판 구독을 사용하여 응용 프로그램에 대한 Office 365 개발/테스트 환경을 만들거나 Office 365의 기능과 특성을 구현해볼 수 있습니다. 다음 두 버전을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65622-p101">You can use an Office 365 trial subscription and create an Office 365 dev/test environment for applications or to demonstrate features and capabilities of Office 365. There are two versions:</span></span>
  
- <span data-ttu-id="65622-107">경량 Office 365 개발/테스트 환경은 주 컴퓨터에서 액세스하는 Office 365 평가판 구독으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="65622-107">The lightweight Office 365 dev/test environment consists of an Office 365 trial subscription that you access from your main computer.</span></span>
    
    <span data-ttu-id="65622-p102">기능을 빠르게 구현해보려면 이 환경을 사용합니다. 경량 Office 365 개발/테스트 환경에서는 이 문서의 2, 3단계만 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="65622-p102">Use this environment when you want to quickly demonstrate a feature. For the lightweight Office 365 dev/test environment, complete only phases 2 and 3 of this article.</span></span>
    
- <span data-ttu-id="65622-p103">시뮬레이트된 엔터프라이즈 Office 365 개발/테스트 환경은 Office 365 평가판 구독과 인터넷에 연결되며 Microsoft Azure 인프라 서비스에 호스트된 간소화된 조직 인트라넷으로 구성됩니다. 이 구성은 Microsoft 클라우드에서 완전히 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65622-p103">The simulated enterprise Office 365 dev/test environment consists of an Office 365 trial subscription and a simplified organization intranet connected to the Internet, which is hosted in Microsoft Azure infrastructure services. You can build this configuration completely in the Microsoft cloud.</span></span>
    
    <span data-ttu-id="65622-p104">인터넷에 연결된 전형적인 조직 네트워크와 유사한 환경에서 기능이나 앱을 구현해보거나, 이러한 유형의 환경이 필요한 기능을 사용하려면 이 환경을 사용합니다. 시뮬레이트된 엔터프라이즈 Office 365 개발/테스트 환경에서는 이 문서의 1, 2 및 3단계를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="65622-p104">Use this environment when you want to demonstrate a feature or an app in an environment that resembles a typical organization network connected to the Internet, or for features that require this type of environment. For the simulated enterprise Office 365 dev/test environment, complete phases 1, 2, and 3 of this article.</span></span>
    
> [!NOTE]
> <span data-ttu-id="65622-p105">30일 간의 Office 365 평가판 구독 기간이 끝난 후에도 이 환경에 필요할 수 있는 특정 값을 기록해 두려면 이 문서를 인쇄할 수 있습니다. 추가로 30일 동안 내역 구독을 연장할 수 있습니다. 영구 개발/테스트 환경의 경우 소수의 라이선스를 사용해서 유료 구독을 새로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="65622-p105">You might want to print this article to record the specific values that you will need for this environment over the 30 days of the Office 365 trial subscription. You can easily extend the trail subscription for another 30 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
![Microsoft 클라우드의 테스트 랩 가이드](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> <span data-ttu-id="65622-118">[여기](http://aka.ms/catlgstack)를 클릭하여 One Microsoft 클라우드 테스트 랩 가이드 스택의 모든 문서에 대한 가상 맵을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65622-118">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-the-base-configuration-in-azure"></a><span data-ttu-id="65622-119">1단계: Azure에서 기본 구성 만들기</span><span class="sxs-lookup"><span data-stu-id="65622-119">Phase 1: Create the base configuration in Azure</span></span>

<span data-ttu-id="65622-120">[기본 구성 개발/테스트 환경](base-configuration-dev-test-environment.md)의 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="65622-120">Follow the instructions in [Base Configuration dev/test environment](base-configuration-dev-test-environment.md).</span></span>
  
<span data-ttu-id="65622-p106">Azure 구독이 필요합니다. 이 구성을 위해 [Azure 무료 평가판](https://azure.microsoft.com/pricing/free-trial/)을 사용할 수 있습니다. MSDN 또는 Visual Studio 구독이 있는 경우 [Visual Studio 구독자를 위한 월별 Azure 크레딧](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="65622-p106">You will need an Azure subscription. You can use the [Azure Free Trial](https://azure.microsoft.com/pricing/free-trial/) for this configuration. If you have an MSDN or Visual Studio subscription, see [Monthly Azure credit for Visual Studio subscribers](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/).</span></span>
  
<span data-ttu-id="65622-124">구성 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="65622-124">Here is the resulting configuration.</span></span>
  
![Azure의 기본 구성 개발/테스트 환경](media/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)


  
<span data-ttu-id="65622-126">이 구성은 Azure Virtual Network의 서브넷에 있는 DC1, APP1 및 CLIENT1 가상 머신으로 이루어집니다.</span><span class="sxs-lookup"><span data-stu-id="65622-126">This configuration consists of the DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network.</span></span>
  
## <a name="phase-2-create-an-office-365-trial-subscription"></a><span data-ttu-id="65622-127">2단계: Office 365 평가판 구독 만들기</span><span class="sxs-lookup"><span data-stu-id="65622-127">Phase 2: Create an Office 365 trial subscription</span></span>

<span data-ttu-id="65622-128">Office 365 E5 평가판 구독을 시작하려면 먼저 가상의 회사 이름 및 새 Microsoft 계정이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="65622-128">To start your Office 365 E5 trial subscription, you first need a fictitious company name and a new Microsoft account.</span></span>
  
1. <span data-ttu-id="65622-p107">회사 이름으로 Microsoft 샘플 콘텐츠에 사용되는 가상의 회사인 Contoso의 변형을 사용하는 것이 좋지만 필수는 아닙니다. 여기에 가상의 회사 이름을 기록하세요. ![](./media/Common-Images/TableLine.png)</span><span class="sxs-lookup"><span data-stu-id="65622-p107">We recommend that you use a variant of the company name Contoso for your company name, which is a fictitious company used in Microsoft sample content, but it isn't required. Record your fictitious company name here: ![](./media/Common-Images/TableLine.png)</span></span>
    
2. <span data-ttu-id="65622-p108">새 Microsoft 계정을 등록하려면으로 [https://outlook.com](https://outlook.com)으로 이동한 후 새 전자 메일 계정 및 주소를 사용하여 계정을 만듭니다. 이 계정을 사용하여 Office 365에 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="65622-p108">To sign up for a new Microsoft account, go to [https://outlook.com](https://outlook.com) and create an account with a new email account and address. You will use this account to sign up for Office 365.</span></span>
    
  - <span data-ttu-id="65622-133">여기에 새 계정의 이름과 성을 기록합니다. ![](./media/Common-Images/TableLine.png)</span><span class="sxs-lookup"><span data-stu-id="65622-133">Record the first and last name of your new account here: ![](./media/Common-Images/TableLine.png)</span></span>
    
  - <span data-ttu-id="65622-134">여기서 새 전자 메일 계정 주소를 기록합니다. ![](./media/Common-Images/TableLine.png)@outlook.com</span><span class="sxs-lookup"><span data-stu-id="65622-134">Record the new email account address here: ![](./media/Common-Images/TableLine.png)@outlook.com</span></span>
    
### <a name="sign-up-for-an-office-365-e5-trial-subscription"></a><span data-ttu-id="65622-135">Office 365 E5 평가판 구독 등록</span><span class="sxs-lookup"><span data-stu-id="65622-135">Sign up for an Office 365 E5 trial subscription</span></span>

1. <span data-ttu-id="65622-136">경량 Office 365 개발/테스트 환경의 경우 컴퓨터에서 인터넷 브라우저를 열고 [https://aka.ms/e5trial](https://aka.ms/e5trial)로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="65622-136">For the lightweight Office 365 dev/test environment, open the Internet browser on your computer and go to [https://aka.ms/e5trial](https://aka.ms/e5trial).</span></span> 
    
    <span data-ttu-id="65622-137">시뮬레이트된 엔터프라이즈 Office 365 개발/테스트 환경의 경우 Azure Portal에서 CORP\User1 계정을 사용하여 CLIENT1에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="65622-137">For the simulated enterprise Office 365 dev/test environment, connect to CLIENT1 with the CORP\User1 account from the Azure portal.</span></span>

    <span data-ttu-id="65622-138">시작 화면에서 Microsoft Edge를 실행하고 [https://aka.ms/e5trial](https://aka.ms/e5trial)로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="65622-138">From the Start screen, run Microsoft Edge and go to [https://aka.ms/e5trial](https://aka.ms/e5trial).</span></span>
    
2. <span data-ttu-id="65622-139">**반갑습니다. 자기소개 정보를 제공해 주세요.** 페이지에서 다음을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="65622-139">On the **Welcome, let's get to know you** page, specify:</span></span>
    
  - <span data-ttu-id="65622-140">사용자의 실제 위치</span><span class="sxs-lookup"><span data-stu-id="65622-140">Your physical location</span></span>
    
  - <span data-ttu-id="65622-141">새 Microsoft 계정의 이름 및 성</span><span class="sxs-lookup"><span data-stu-id="65622-141">The first and last name of your new Microsoft account</span></span>
    
  - <span data-ttu-id="65622-142">새 전자 메일 계정 주소</span><span class="sxs-lookup"><span data-stu-id="65622-142">Your new email account address</span></span>
    
  - <span data-ttu-id="65622-143">회사 전화 번호</span><span class="sxs-lookup"><span data-stu-id="65622-143">A business phone number</span></span>
    
  - <span data-ttu-id="65622-144">가상의 회사 이름</span><span class="sxs-lookup"><span data-stu-id="65622-144">Your fictional company name</span></span>
    
  - <span data-ttu-id="65622-145">250-999명의 사용자로 구성된 조직 규모</span><span class="sxs-lookup"><span data-stu-id="65622-145">An organization size of 250-999 people</span></span>
    
3. <span data-ttu-id="65622-146">**마지막 단계만 남음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="65622-146">Click **Just one more step**.</span></span>
    
4. <span data-ttu-id="65622-147">**사용자 ID 만들기** 페이지에서 새 전자 메일 주소를 기준으로 하는 사용자 이름을 입력하고 @ 기호를 입력한 후 가상의 회사를 입력하고(이름에서 모든 공백 제거), 이 새 Office 365 계정에 대한 암호를 입력합니다(두 번).</span><span class="sxs-lookup"><span data-stu-id="65622-147">On the **Create your user ID** page, type a user name based on your new email address, your fictional company after the @ sign (remove all spaces in the name), then a password (twice) for this new Office 365 account.</span></span>
    
    <span data-ttu-id="65622-148">입력한 암호를 안전한 위치에 기록해둡니다.</span><span class="sxs-lookup"><span data-stu-id="65622-148">Record the password that you typed in a secure location.</span></span>
    
    <span data-ttu-id="65622-149">**조직 이름**으로 지칭될 가상의 회사 이름을 여기에 기록합니다. ![](./media/Common-Images/TableLine.png)</span><span class="sxs-lookup"><span data-stu-id="65622-149">Record your fictional company name, to be referred to as the **organization name**, here: ![](./media/Common-Images/TableLine.png)</span></span>
    
5. <span data-ttu-id="65622-150">**내 계정 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="65622-150">Click **Create my account**.</span></span>
    
6. <span data-ttu-id="65622-p109">**자동 가입 방지를 위한 절차입니다.** 페이지에서 문자 입력이 가능한 휴대폰의 전화 번호를 입력하고 **문자 메시지 받기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="65622-p109">On the **Prove. You're. Not. A. Robot.** page, type the phone number of your text-capable phone, and then click **Text me**.</span></span>
    
7. <span data-ttu-id="65622-153">받은 문자 메시지의 확인 코드를 입력하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="65622-153">Type the verification code from the received text message, and then click **Next**.</span></span>
    
8. <span data-ttu-id="65622-154">여기에 로그인 페이지 URL을 기록합니다(선택 후 복사). ![](./media/Common-Images/TableLine.png)</span><span class="sxs-lookup"><span data-stu-id="65622-154">Record the sign-in page URL here (select and copy): ![](./media/Common-Images/TableLine.png)</span></span>
    
9. <span data-ttu-id="65622-155">여기에 사용자 ID를 기록합니다(선택 후 복사). ![](./media/Common-Images/TableLine.png).onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="65622-155">Record the user ID here (select and copy): ![](./media/Common-Images/TableLine.png).onmicrosoft.com</span></span>
    
    <span data-ttu-id="65622-156">이 값은 **Office 365 전역 관리자 이름**으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="65622-156">This value will be referred to as the **Office 365 global administrator name**.</span></span>
    
10. <span data-ttu-id="65622-157">**준비가 되었습니다.** 가 표시되면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="65622-157">When you see **You're ready to go**, click it.</span></span>
    
11. <span data-ttu-id="65622-158">다음 페이지에서 Office 365 설정이 완료되고 모든 타일을 사용할 수 있게 될 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="65622-158">On the next page, wait until Office 365 completes setting up and all the tiles are available.</span></span>
    
<span data-ttu-id="65622-159">Office Online 서비스 및 Microsoft 365 관리 센터에 액세스할 수 있는 기본 Office 365 포털 페이지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="65622-159">You should see main Office 365 portal page from which you can access Office Online services and the Office 365 Admin center.</span></span>
  
<span data-ttu-id="65622-160">시뮬레이트된 엔터프라이즈 Office 365 개발/테스트 환경의 경우 결과 구성은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="65622-160">For the simulated enterprise Office 365 dev/test environment, here is your resulting configuration.</span></span>
  
![Office 365 개발/테스트 환경](media/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
<span data-ttu-id="65622-162">이 구성은 다음으로 이루어집니다.</span><span class="sxs-lookup"><span data-stu-id="65622-162">This configuration consists of:</span></span> 
  
- <span data-ttu-id="65622-163">Azure Virtual Network의 서브넷에 있는 DC1, APP1 및 CLIENT1 가상 머신</span><span class="sxs-lookup"><span data-stu-id="65622-163">The DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network.</span></span>
    
- <span data-ttu-id="65622-164">Office 365 E5 평가판 구독</span><span class="sxs-lookup"><span data-stu-id="65622-164">An Office 365 E5 Trial Subscription.</span></span>
    
## <a name="phase-3-configure-your-office-365-trial-subscription"></a><span data-ttu-id="65622-165">3단계: Office 365 평가판 구독 구성</span><span class="sxs-lookup"><span data-stu-id="65622-165">Phase 3: Configure your Office 365 trial subscription</span></span>

<span data-ttu-id="65622-166">이 단계에서는 추가된 사용자와 SharePoint Online 팀 사이트를 사용하여 Office 365 구독을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="65622-166">In this phase, you configure your Office 365 subscription with additional users and SharePoint Online team sites.</span></span>
  
<span data-ttu-id="65622-167">먼저, 4명의 새 사용자를 추가하고 E5 라이선스를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="65622-167">First, you add four new users and assign them E5 licenses.</span></span>
  
<span data-ttu-id="65622-168">[Office 365 PowerShell에 연결](https://technet.microsoft.com/library/dn975125.aspx)에 제공되는 지침을 사용하여 PowerShell 모듈을 설치하고 다음에서 새 Office 365 구독에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="65622-168">Use the instructions in [Connect to Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) to install the PowerShell modules and connect to your new Office 365 subscription from:</span></span>
  
- <span data-ttu-id="65622-169">사용하는 컴퓨터(경량 Office 365 개발/테스트 환경)</span><span class="sxs-lookup"><span data-stu-id="65622-169">Your computer (for the lightweight Office 365 dev/test environment).</span></span>
    
- <span data-ttu-id="65622-170">CLIENT1 가상 컴퓨터(시뮬레이트된 엔터프라이즈 Office 365 개발/테스트 환경)</span><span class="sxs-lookup"><span data-stu-id="65622-170">The CLIENT1 virtual machine (for the simulated enterprise Office 365 dev/test environment).</span></span>
    
 <span data-ttu-id="65622-171">Windows PowerShell 자격 증명 요청 대화 상자에서 Office 365 전역 관리자 이름(예: jdoe@contosotoycompany.onmicrosoft.com)과 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="65622-171">In the Windows PowerShell Credential Request dialog box, type the Office 365 global administrator name (example: jdoe@contosotoycompany.onmicrosoft.com) and password.</span></span>
  
<span data-ttu-id="65622-172">조직 이름(예: contosotoycompany), 위치에 대한 2자리 국가 코드를 입력한 후 Windows PowerShell 프롬프트에 대한 Microsoft Azure Active Directory 모듈에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="65622-172">Fill in your organization name (example: contosotoycompany), the two-character country code for your location, and then run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "user2@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 2" -FirstName User -LastName 2 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```
<!--
> [!TIP]
> Click [here](https://gallery.technet.microsoft.com/PowerShell-commands-for-fe3d7a34) to get a text file that has all the PowerShell commands in this article.
-->

<span data-ttu-id="65622-173">**New-MsolUser** 명령 표시에서 사용자 2 계정에 대해 생성된 암호를 적어둔 후 안전한 위치에 보관합니다.</span><span class="sxs-lookup"><span data-stu-id="65622-173">From the display of the **New-MsolUser** command, note the generated password for the User 2 account and record it in a safe location.</span></span>
  
<span data-ttu-id="65622-174">Windows PowerShell 프롬프트에 대한 Microsoft Azure Active Directory 모듈에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="65622-174">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "user3@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 3" -FirstName User -LastName 3 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

<span data-ttu-id="65622-175">**New-MsolUser** 명령 표시에서 사용자 3 계정에 대해 생성된 암호를 적어둔 후 안전한 위치에 보관합니다.</span><span class="sxs-lookup"><span data-stu-id="65622-175">From the display of the **New-MsolUser** command, note the generated password for the User 3 account and record it in a safe location.</span></span>
  
<span data-ttu-id="65622-176">Windows PowerShell 프롬프트에 대한 Microsoft Azure Active Directory 모듈에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="65622-176">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "user4@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 4" -FirstName User -LastName 4 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

<span data-ttu-id="65622-177">**New-MsolUser** 명령 표시에서 사용자 4 계정에 대해 생성된 암호를 적어둔 후 안전한 위치에 보관합니다.</span><span class="sxs-lookup"><span data-stu-id="65622-177">From the display of the **New-MsolUser** command, note the generated password for the User 4 account and record it in a safe location.</span></span>
  
<span data-ttu-id="65622-178">Windows PowerShell 프롬프트에 대한 Microsoft Azure Active Directory 모듈에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="65622-178">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "user5@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 5" -FirstName User -LastName 5 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

<span data-ttu-id="65622-179">**New-MsolUser** 명령 표시에서 사용자 5 계정에 대해 생성된 암호를 적어둔 후 안전한 위치에 보관합니다.</span><span class="sxs-lookup"><span data-stu-id="65622-179">From the display of the **New-MsolUser** command, note the generated password for the User 5 account and record it in a safe location.</span></span>
  
<span data-ttu-id="65622-180">다음으로, 판매, 프로덕션 및 지원 부서를 위해 3개의 SharePoint Online 팀 사이트를 새로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="65622-180">Next, you create three new SharePoint Online team sites for the Sales, Production, and Support departments.</span></span>
  
## <a name="phase-4-create-three-new-sharepoint-online-team-sites-optional"></a><span data-ttu-id="65622-181">4단계: 3개의 새로운 SharePoint Online 팀 사이트 만들기(선택 사항)</span><span class="sxs-lookup"><span data-stu-id="65622-181">Phase 4: Create three new SharePoint Online team sites (optional)</span></span>

<span data-ttu-id="65622-182">이 단계에서는 SharePoint Online 팀 사이트의 집합을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="65622-182">In this phase, you configure a set of SharePoint Online team sites.</span></span>
  
1. <span data-ttu-id="65622-183">[SharePoint Online 관리 셸](https://go.microsoft.com/fwlink/p/?LinkId=255251)(x64 버전)을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="65622-183">Install the [SharePoint Online Management Shell](https://go.microsoft.com/fwlink/p/?LinkId=255251) (the x64 version).</span></span>
    
2. <span data-ttu-id="65622-184">**시작**을 클릭하고 **sharepoint**를 입력한 후 **SharePoint Online 관리 셸**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="65622-184">Click **Start**, type **sharepoint**, and then click **SharePoint Online Management Shell**.</span></span>
    
3. <span data-ttu-id="65622-185">조직 이름(예: contosotoycompany)을 입력하고 SharePoint Online 관리 셸 프롬프트에서 다음 명령을 실행하여 SharePoint Online 서비스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="65622-185">Fill in your organization name (example: contosotoycompany), and then run the following commands from the SharePoint Online Management Shell prompt to connect to the SharePoint Online service</span></span>
```
$orgName="<organization name>"
$spURL="https://" + $orgName + "-admin.sharepoint.com"
Connect-SPOService -Url $spURL
```

4. <span data-ttu-id="65622-186">**Microsoft SharePoint Online 관리 셸** 대화 상자에서 Office 365 전역 관리자 이름(예: jdoe@contosotoycompany.onmicrosoft.com) 및 암호를 입력하고 **로그인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="65622-186">In the **Microsoft SharePoint Online Management Shell** dialog box, type the Office 365 global administrator name (example: jdoe@contosotoycompany.onmicrosoft.com) and password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="65622-187">3개의 새로운 팀 사이트(판매, 프로덕션 및 지원)를 만들려면 Office 365 전역 관리자 이름을 입력하고 SharePoint Online 관리 셸 프롬프트에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="65622-187">To create three new team sites (Sales, Production, and Support), fill in the Office 365 global administrator name, and then run the following commands from the SharePoint Online Management Shell prompt:</span></span>
    
  ```
  $owner = "<global administrator account name>"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/sales"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Sales site collection" -Template "STS#0"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/production"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Production site collection" -Template "STS#0"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/support"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Support site collection" -Template "STS#0"
  ```

6. <span data-ttu-id="65622-188">이러한 새 사이트의 URL을 나열하려면 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="65622-188">Run this command to list the URLs of these new sites:</span></span>
    
  ```
  Get-SPOSite | Where URL -like "*/sites/*" | Sort URL | Select URL
  ```

7. <span data-ttu-id="65622-189">Internet Explorer에서 프로덕션 사이트의 URL을 입력하여 프로덕션 부서에 대한 기본 SharePoint Online 팀 사이트를 표시합니다..</span><span class="sxs-lookup"><span data-stu-id="65622-189">In Internet Explorer, enter the URL of the Production site to see the default SharePoint Online team site for the Production department.</span></span>
    
## <a name="record-values-for-future-reference"></a><span data-ttu-id="65622-190">나중에 참조하기 위해 값 기록</span><span class="sxs-lookup"><span data-stu-id="65622-190">Record values for future reference</span></span>

<span data-ttu-id="65622-191">이 테스트 환경에서 추가 테스트 랩 가이드를 사용하거나 배포하려면 다음 값을 기록해둡니다.</span><span class="sxs-lookup"><span data-stu-id="65622-191">Record these values for working with or deploying additional Test Lab Guides in this test environment:</span></span>
  
- <span data-ttu-id="65622-192">Office 365 전역 관리자 이름: ![](./media/Common-Images/TableLine.png).onmicrosoft.com(2단계의 9번째 작업 단계)</span><span class="sxs-lookup"><span data-stu-id="65622-192">Office 365 global administrator name: ![](./media/Common-Images/TableLine.png).onmicrosoft.com (from step 9 of Phase 2)</span></span>
    
    <span data-ttu-id="65622-193">이 계정의 암호도 안전한 위치에 적어둡니다.</span><span class="sxs-lookup"><span data-stu-id="65622-193">Also record the password for this account in a secure location.</span></span>
    
- <span data-ttu-id="65622-194">평가판 구독 조 직 이름: ![](./media/Common-Images/TableLine.png)(4단계의 2번째 작업 단계)</span><span class="sxs-lookup"><span data-stu-id="65622-194">Your trial subscription organization name: ![](./media/Common-Images/TableLine.png) (from step 4 of Phase 2)</span></span>
    
- <span data-ttu-id="65622-195">사용자 2, 사용자 3, 사용자 4, 사용자 5에 대한 계정을 나열하려면 Windows PowerShell 프롬프트에 대한 Microsoft Azure Active Directory 모듈에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="65622-195">To list the accounts for User 2, User 3, User 4, and User 5, run the following command from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
    
  ```
  Get-MSolUser | Sort UserPrincipalName | Select UserPrincipalName
  ```

    <span data-ttu-id="65622-196">여기에 계정 이름을 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="65622-196">Record the account names here:</span></span>
    
  - <span data-ttu-id="65622-197">사용자 2 계정 이름: user2@![](./media/Common-Images/TableLine.png).onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="65622-197">User 2 account name: user2@![](./media/Common-Images/TableLine.png).onmicrosoft.com</span></span>
    
  - <span data-ttu-id="65622-198">사용자 3 계정 이름: user3@![](./media/Common-Images/TableLine.png).onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="65622-198">User 3 account name: user3@![](./media/Common-Images/TableLine.png).onmicrosoft.com</span></span>
    
  - <span data-ttu-id="65622-199">사용자 4 계정 이름: user4@![](./media/Common-Images/TableLine.png).onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="65622-199">User 4 account name: user4@![](./media/Common-Images/TableLine.png).onmicrosoft.com</span></span>
    
  - <span data-ttu-id="65622-200">사용자 5 계정 이름: user5@![](./media/Common-Images/TableLine.png).onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="65622-200">User 5 account name: user5@![](./media/Common-Images/TableLine.png).onmicrosoft.com</span></span>
    
    <span data-ttu-id="65622-201">해당 계정의 암호도 안전한 위치에 적어둡니다.</span><span class="sxs-lookup"><span data-stu-id="65622-201">Also record the passwords for these accounts in a secure location.</span></span>
    
- <span data-ttu-id="65622-202">(선택 사항) 판매, 프로덕션 및 지원 팀 사이트에 대한 URL을 나열하려면 SharePoint Online 관리 셸 프롬프트에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="65622-202">(optional) To list the URLs for the Sales, Production, and Support team sites, run the following command from the SharePoint Online Management Shell prompt:</span></span>
    
  ```
  Get-SPOSite | Where URL -like "*/sites/*" | Sort URL | Select URL
  ```

  - <span data-ttu-id="65622-203">프로덕션 사이트 URL: https://![](./media/Common-Images/TableLine.png).sharepoint.com/sites/production</span><span class="sxs-lookup"><span data-stu-id="65622-203">Production site URL: https://![](./media/Common-Images/TableLine.png).sharepoint.com/sites/production</span></span>
    
  - <span data-ttu-id="65622-204">판매 사이트 URL: https://![](./media/Common-Images/TableLine.png).sharepoint.com/sites/sales</span><span class="sxs-lookup"><span data-stu-id="65622-204">Sales site URL: https://![](./media/Common-Images/TableLine.png).sharepoint.com/sites/sales</span></span>
    
  - <span data-ttu-id="65622-205">지원 사이트 URL: https://![](./media/Common-Images/TableLine.png).sharepoint.com/sites/support</span><span class="sxs-lookup"><span data-stu-id="65622-205">Support site URL: https://![](./media/Common-Images/TableLine.png).sharepoint.com/sites/support</span></span>
    
## <a name="next-steps"></a><span data-ttu-id="65622-206">다음 단계</span><span class="sxs-lookup"><span data-stu-id="65622-206">Next steps</span></span>

<span data-ttu-id="65622-207">Office 365 개발/테스트 환경에서 다음 문서를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="65622-207">Use these additional articles in your Office 365 dev/test environment:</span></span>
  
- [<span data-ttu-id="65622-208">Office 365 개발/테스트 환경에 대한 디렉터리 동기화</span><span class="sxs-lookup"><span data-stu-id="65622-208">Directory Synchronization for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="65622-209">Office 365 개발/테스트 환경용 Multi-Factor Authentication</span><span class="sxs-lookup"><span data-stu-id="65622-209">Multi-factor authentication for your Office 365 dev/test environment</span></span>](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="65622-210">Office 365 개발/테스트 환경용 페더레이션된 ID</span><span class="sxs-lookup"><span data-stu-id="65622-210">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="65622-211">Office 365 개발/테스트 환경용 Cloud App Security</span><span class="sxs-lookup"><span data-stu-id="65622-211">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="65622-212">Office 365 개발/테스트 환경용 Advanced Threat Protection</span><span class="sxs-lookup"><span data-stu-id="65622-212">Advanced Threat Protection for your Office 365 dev/test environment</span></span>](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="65622-213">Office 365 개발/테스트 환경용 고급 eDiscovery</span><span class="sxs-lookup"><span data-stu-id="65622-213">Advanced eDiscovery for your Office 365 dev/test environment</span></span>](advanced-ediscovery-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="65622-214">Office 365 개발/테스트 환경용 중요 파일 보호</span><span class="sxs-lookup"><span data-stu-id="65622-214">Sensitive file protection in the Office 365 dev/test environment</span></span>](sensitive-file-protection-in-the-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="65622-215">개발/테스트 환경에서 격리된 SharePoint Online 팀 사이트</span><span class="sxs-lookup"><span data-stu-id="65622-215">Isolated SharePoint Online team site dev/test environment</span></span>](isolated-sharepoint-online-team-site-dev-test-environment.md)
    
- [<span data-ttu-id="65622-216">Office 365 개발/테스트 환경에서 데이터 분류 및 레이블 지정</span><span class="sxs-lookup"><span data-stu-id="65622-216">Data classification and labeling in the Office 365 dev/test environment</span></span>](data-classification-and-labeling-in-the-office-365-dev-test-environment.md)
    
<span data-ttu-id="65622-217">추가 Microsoft 클라우드 서비스를 포함하도록 Office 365 개발/테스트 환경을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="65622-217">Extend your Office 365 dev/test environment to include additional Microsoft cloud offerings:</span></span>
  
- [<span data-ttu-id="65622-218">Microsoft 365 Enterprise 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="65622-218">The Microsoft 365 Enterprise dev/test environment</span></span>](the-microsoft-365-enterprise-dev-test-environment.md)
    
- [<span data-ttu-id="65622-219">Office 365 및 Dynamics 365 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="65622-219">Office 365 and Dynamics 365 dev/test environment</span></span>](office-365-and-dynamics-365-dev-test-environment.md)
    
## <a name="see-also"></a><span data-ttu-id="65622-220">참고 항목</span><span class="sxs-lookup"><span data-stu-id="65622-220">See Also</span></span>

- [<span data-ttu-id="65622-221">클라우드 도입 TLG(테스트 랩 가이드)</span><span class="sxs-lookup"><span data-stu-id="65622-221">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
- [<span data-ttu-id="65622-222">Office 365 및 Dynamics 365 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="65622-222">Office 365 and Dynamics 365 dev/test environment</span></span>](office-365-and-dynamics-365-dev-test-environment.md)
  
- [<span data-ttu-id="65622-223">클라우드 도입 및 하이브리드 솔루션</span><span class="sxs-lookup"><span data-stu-id="65622-223">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)


