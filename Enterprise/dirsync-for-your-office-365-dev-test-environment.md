---
title: Office 365 개발/테스트 환경에 대한 디렉터리 동기화
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/18/2018
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: e6b27e25-74ae-4b54-9421-c8e911aef543
description: '요약: Office 365 개발/테스트 환경에 대한 디렉터리 동기화를 구성합니다.'
ms.openlocfilehash: 795bd871be7937933ce61801d616c900dab7601a
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2019
ms.locfileid: "38030792"
---
# <a name="directory-synchronization-for-your-office-365-devtest-environment"></a><span data-ttu-id="e5a34-103">Office 365 개발/테스트 환경에 대한 디렉터리 동기화</span><span class="sxs-lookup"><span data-stu-id="e5a34-103">Directory synchronization for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="e5a34-104">**요약:** Office 365 개발/테스트 환경에 대한 디렉터리 동기화를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="e5a34-104">**Summary:** Configure directory synchronization for your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="e5a34-p101">많은 조직에서는 Azure AD Connect 및 디렉터리 동기화를 사용하여 온-프레미스 Active Directory Domain Services(AD DS) 포리스트의 계정 집합을 Office 365의 계정 집합과 동기화합니다. 이 문서에서는 암호 해시 동기화를 사용한 디렉터리 동기화를 Office 365 개발/테스트 환경에 추가하여 다음과 같이 구성하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e5a34-p101">Many organizations use Azure AD Connect and directory synchronization to synchronize the set of accounts in their on-premises Active Directory Domain Services (AD DS) forest to the set of accounts in Office 365. This article describes how you can add directory synchronization with password hash synchronization to the Office 365 dev/test environment, resulting in the following configuration.</span></span>
  
![디렉터리 동기화를 사용하는 Office 365 개발/테스트 환경](media/be5b37b0-f832-4878-b153-436c31546e21.png)
  
<span data-ttu-id="e5a34-108">이 구성은 다음으로 이루어집니다.</span><span class="sxs-lookup"><span data-stu-id="e5a34-108">This configuration consists of:</span></span> 
  
- <span data-ttu-id="e5a34-109">Office 365 E5 평가판 구독: 만들고 30일 후에 만료됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5a34-109">An Office 365 E5 Trial Subscription, which expires 30 days from when you create it.</span></span>
- <span data-ttu-id="e5a34-p102">인터넷에 연결된 간소화된 조직 인트라넷: Azure Virtual Network 서브넷에 있는 3개의 가상 머신(DC1, APP1 및 CLIENT1)으로 구성됩니다. Azure AD Connect는 APP1에서 실행되며 AD DS 도메인을 Office 365와 동기화합니다.</span><span class="sxs-lookup"><span data-stu-id="e5a34-p102">A simplified organization intranet connected to the Internet, consisting of three virtual machines on a subnet of an Azure virtual network (DC1, APP1, and CLIENT1). Azure AD Connect runs on APP1 to synchronize the AD DS domain to Office 365.</span></span>
    
<span data-ttu-id="e5a34-112">이 개발/테스트 환경의 2가지 주요 설정 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e5a34-112">There are two phases to setting up this dev/test environment:</span></span>
  
1. <span data-ttu-id="e5a34-113">Office 365 개발/테스트 환경을 만듭니다(Office 365 E5 평가판 구독, Azure Virtual Network의 DC1, APP1, and CLIENT1 가상 머신).</span><span class="sxs-lookup"><span data-stu-id="e5a34-113">Create the Office 365 dev/test environment (the DC1, APP1, and CLIENT1 virtual machines in an Azure virtual network with an Office 365 E5 trial subscription).</span></span>
2. <span data-ttu-id="e5a34-114">APP1에 Azure AD Connect를 설치 및 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="e5a34-114">Install and configure Azure AD Connect on APP1.</span></span>
    
> [!TIP]
> <span data-ttu-id="e5a34-115">[여기](https://aka.ms/catlgstack)를 클릭하여 Office 365 테스트 랩 가이드 스택의 모든 문서에 대한 가상 맵을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5a34-115">Click [here](https://aka.ms/catlgstack) for a visual map to all the articles in the Office 365 Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-an-office-365-devtest-environment"></a><span data-ttu-id="e5a34-116">1단계: Office 365 개발/테스트 환경 만들기</span><span class="sxs-lookup"><span data-stu-id="e5a34-116">Phase 1: Create an Office 365 dev/test environment</span></span>

<span data-ttu-id="e5a34-p103">[Office 365 개발/테스트 환경](office-365-dev-test-environment.md) 문서의 1, 2 및 3단계 지침을 따릅니다. 구성 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e5a34-p103">Follow the instructions in phases 1, 2, and 3 of the [Office 365 dev/test environment](office-365-dev-test-environment.md) article. Here is the resulting configuration.</span></span>
  
![Office 365 개발/테스트 환경](media/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
<span data-ttu-id="e5a34-120">이 구성은 다음으로 이루어집니다.</span><span class="sxs-lookup"><span data-stu-id="e5a34-120">This configuration consists of:</span></span> 
  
- <span data-ttu-id="e5a34-121">Office 365 E5 평가판 구독</span><span class="sxs-lookup"><span data-stu-id="e5a34-121">An Office 365 E5 Trial Subscription.</span></span>
- <span data-ttu-id="e5a34-122">인터넷에 연결된 간소화된 조직 인트라넷: Azure Virtual Network 서브넷에 있는 DC1, APP1 및 CLIENT1 가상 머신으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5a34-122">A simplified organization intranet connected to the Internet, consisting of the DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network.</span></span>
    
## <a name="phase-2-install-azure-ad-connect-on-app1"></a><span data-ttu-id="e5a34-123">2단계: APP1에 Azure AD Connect 설치</span><span class="sxs-lookup"><span data-stu-id="e5a34-123">Phase 2: Install Azure AD Connect on APP1</span></span>

<span data-ttu-id="e5a34-p104">일단 설치 및 구성되면, Azure AD Connect는 CORP AD DS 도메인의 계정 집합을 Office 365 평가판 구독의 계정 집합과 동기화합니다. 다음 절차에서는 APP1에 Azure AD Connect를 설치하고 작동하는지 확인하는 과정을 안내합니다.</span><span class="sxs-lookup"><span data-stu-id="e5a34-p104">Once installed and configured, Azure AD Connect synchronizes the set of accounts in the CORP AD DS domain with the set of accounts in your Office 365 trial subscription. The following procedure steps you through installing Azure AD Connect on APP1 and checking that it works.</span></span>
  
### <a name="install-and-configure-azure-ad-connect-on-app1"></a><span data-ttu-id="e5a34-126">APP1에 Azure AD Connect 설치 및 구성</span><span class="sxs-lookup"><span data-stu-id="e5a34-126">Install and configure Azure AD Connect on APP1</span></span>

1. <span data-ttu-id="e5a34-127">[Azure Portal](https://portal.azure.com)에서 CORP\\User1 계정을 사용하여 APP1에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="e5a34-127">From the [Azure portal](https://portal.azure.com), connect to APP1 with the CORP\\User1 account.</span></span>
    
2. <span data-ttu-id="e5a34-128">APP1에서 관리자 수준 Windows PowerShell 명령 프롬프트를 열고 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e5a34-128">From APP1, open an administrator-level Windows PowerShell command prompt, and then run these commands:</span></span>
    
  ```
  Set-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Active Setup\Installed Components\{A509B1A7-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Set-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Active Setup\Installed Components\{A509B1A8-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Stop-Process -Name Explorer -Force

  ```

3. <span data-ttu-id="e5a34-129">작업 표시줄에서 **Internet Explorer**를 클릭하고 [https://aka.ms/aadconnect](https://aka.ms/aadconnect)로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="e5a34-129">From the task bar, click **Internet Explorer** and go to [https://aka.ms/aadconnect](https://aka.ms/aadconnect).</span></span>
    
4. <span data-ttu-id="e5a34-130">Microsoft Azure Active Directory Connect 페이지에서 **다운로드**를 클릭하고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e5a34-130">On the Microsoft Azure Active Directory Connect page, click **Download**, and then click **Run**.</span></span>
    
5. <span data-ttu-id="e5a34-131">**Azure AD Connect 시작** 페이지에서 **동의**를 클릭하고 **계속**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e5a34-131">On the **Welcome to Azure AD Connect** page, click **I agree**, and then click **Continue**.</span></span>
    
6. <span data-ttu-id="e5a34-132">**기본 설정** 페이지에서 **기본 설정 사용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e5a34-132">On the **Express Settings** page, click **Use express settings**.</span></span>
    
7. <span data-ttu-id="e5a34-133">**Azure AD에 연결** 페이지에서 **사용자 이름**에 전역 관리자 계정 이름을 입력하고 **암호**에 해당 암호를 입력한 후 \*\*다음 \*\*을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e5a34-133">On the **Connect to Azure AD** page, type your global administrator account name in **Username,** type its password in **Password**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="e5a34-134">**AD DS에 연결** 페이지에서 **사용자 이름**에 **CORP\\User1**을 입력하고 **암호**에 암호를 입력한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e5a34-134">On the **Connect to AD DS** page, type **CORP\\User1** in **Username,** type its password in **Password**, and then click **Next**.</span></span>
    
9. <span data-ttu-id="e5a34-135">**Azure AD 로그인 구성** 페이지에서 **확인된 도메인 없이 계속**을 클릭한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e5a34-135">On the **Azure AD sign-in configuration** page, click **Continue without any verified domains**, and then click **Next**.</span></span>
    
10. <span data-ttu-id="e5a34-136">**구성 준비 완료** 페이지에서 **설치**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e5a34-136">On the **Ready to configure** page, click **Install**.</span></span>
    
11. <span data-ttu-id="e5a34-137">**구성 완료** 페이지에서 **끝내기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e5a34-137">On the **Configuration complete** page, click **Exit**.</span></span>
    
12. <span data-ttu-id="e5a34-138">Internet Explorer에서 Microsoft 365 관리 센터([https://admin.microsoft.com](https://admin.microsoft.com))로 이동한 후 전역 관리자 계정으로 Office 365 평가판 구독에 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="e5a34-138">In Internet Explorer, go to the Microsoft 365 admin center ([https://admin.microsoft.com](https://admin.microsoft.com)) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
13. <span data-ttu-id="e5a34-139">기본 포털 페이지에서 **관리자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e5a34-139">From the main portal page, click **Admin**.</span></span>
    
14. <span data-ttu-id="e5a34-140">왼쪽 탐색에서 **사용자 > 활성화된 사용자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e5a34-140">In the left navigation, click **Users > Active users**.</span></span>
    
    <span data-ttu-id="e5a34-p105">**User1** 계정을 확인합니다. 이 계정은 CORP AD DS 도메인에서 가져온 것이며 디렉터리 동기화가 진행되었다는 증거입니다.</span><span class="sxs-lookup"><span data-stu-id="e5a34-p105">Note the account named **User1**. This account is from the CORP AD DS domain and is proof that directory synchronization has worked.</span></span>
    
15. <span data-ttu-id="e5a34-p106">**User1** 계정을 클릭합니다. 제품 라이선스에 대해 **편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e5a34-p106">Click the **User1** account. For product licenses, click **Edit**.</span></span>
    
16. <span data-ttu-id="e5a34-p107">**제품 라이선스**에서 국가를 선택하고 **Office 365 Enterprise E5**에 대해 **해제**를 클릭합니다(**설정**으로 전환됨). 페이지 아래쪽의 **저장**을 클릭하고 **닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e5a34-p107">In **Product licenses**, select your country, and then click the **Off** control for **Office 365 Enterprise E5** (switching it to **On**). Click **Save** at the bottom of the page, and then click **Close**.</span></span>
    
<span data-ttu-id="e5a34-147">구성 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e5a34-147">This is the resulting configuration.</span></span>
  
![디렉터리 동기화를 사용하는 Office 365 개발/테스트 환경](media/be5b37b0-f832-4878-b153-436c31546e21.png)
  
<span data-ttu-id="e5a34-149">이 구성은 다음으로 이루어집니다.</span><span class="sxs-lookup"><span data-stu-id="e5a34-149">This configuration consists of:</span></span> 
  
- <span data-ttu-id="e5a34-150">Office 365 E5 평가판 구독</span><span class="sxs-lookup"><span data-stu-id="e5a34-150">An Office 365 E5 Trial Subscription.</span></span>
- <span data-ttu-id="e5a34-p108">인터넷에 연결된 간소화된 조직 인트라넷: Azure Virtual Network 서브넷에 있는 DC1, APP1 및 CLIENT1 가상 머신으로 구성됩니다. Azure AD Connect는 APP1에서 실행되며 30분 간격으로 CORP AD DS 도메인을 Office 365와 동기화합니다.</span><span class="sxs-lookup"><span data-stu-id="e5a34-p108">A simplified organization intranet connected to the Internet, consisting of the DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network. Azure AD Connect runs on APP1 to synchronize the CORP AD DS domain to Office 365 every 30 minutes.</span></span>
    
## <a name="next-step"></a><span data-ttu-id="e5a34-153">다음 단계</span><span class="sxs-lookup"><span data-stu-id="e5a34-153">Next Step</span></span>

<span data-ttu-id="e5a34-154">조직에 대한 디렉터리 동기화 배포 준비가 완료되면 [Microsoft Azure에서 Office 365 디렉터리 동기화 배포](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e5a34-154">When you are ready to deploy directory synchronization for your organization, see [Deploy Office 365 Directory Synchronization in Microsoft Azure](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e5a34-155">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e5a34-155">See Also</span></span>

[<span data-ttu-id="e5a34-156">클라우드 도입 TLG(테스트 랩 가이드)</span><span class="sxs-lookup"><span data-stu-id="e5a34-156">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="e5a34-157">기본 구성 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="e5a34-157">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)

[<span data-ttu-id="e5a34-158">Office 365 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="e5a34-158">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)

[<span data-ttu-id="e5a34-159">Office 365 개발/테스트 환경용 Advanced Threat Protection</span><span class="sxs-lookup"><span data-stu-id="e5a34-159">Advanced Threat Protection for your Office 365 dev/test environment</span></span>](advanced-threat-protection-for-your-office-365-dev-test-environment.md)

[<span data-ttu-id="e5a34-160">클라우드 도입 및 하이브리드 솔루션</span><span class="sxs-lookup"><span data-stu-id="e5a34-160">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




