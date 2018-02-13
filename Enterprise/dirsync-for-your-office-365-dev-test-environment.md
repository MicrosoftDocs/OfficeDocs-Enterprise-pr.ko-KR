---
title: "Office 365 개발/테스트 환경에 대 한 디렉터리 동기화"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365, Strat_O365_Enterprise
ms.custom: Strat_O365_Enterprise, TLG, Ent_TLGs
ms.assetid: e6b27e25-74ae-4b54-9421-c8e911aef543
description: "요약: Office 365 개발/테스트 환경에 대 한 디렉터리 동기화를 구성 합니다."
ms.openlocfilehash: fc3a28d52781ba5a541d223c9f8bc081251a2b07
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/13/2018
---
# <a name="dirsync-for-your-office-365-devtest-environment"></a><span data-ttu-id="4d007-103">Office 365 개발/테스트 환경에 대 한 디렉터리 동기화</span><span class="sxs-lookup"><span data-stu-id="4d007-103">DirSync for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="4d007-104">**요약:** Office 365 개발/테스트 환경에 대 한 디렉터리 동기화를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d007-104">**Summary:** Configure directory synchronization for your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="4d007-p101">많은 조직에서는 사용 Azure AD 연결 및 디렉터리 동기화 (DirSync)의 온-프레미스 Windows Server Active Directory (AD) 포리스트에 Office 365에서 계정 집합에 있는 계정의 집합 동기화 합니다. 이 문서에 추가 하는 방법을 DirSync Office 365 개발/테스트 환경에 대 한 암호 동기화와 다음 구성의 결과 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d007-p101">Many organizations use Azure AD Connect and directory synchronization (DirSync) to synchronize the set of accounts in their on-premises Windows Server Active Directory (AD) forest to the set of accounts in Office 365. This article describes how you can add DirSync with password synchronization to the Office 365 dev/test environment, resulting in the following configuration.</span></span>
  
![DirSync를 사용하는 Office 365 개발/테스트 환경](images/be5b37b0-f832-4878-b153-436c31546e21.png)
  
<span data-ttu-id="4d007-108">이 구성은 다음으로 이루어집니다.</span><span class="sxs-lookup"><span data-stu-id="4d007-108">This configuration consists of:</span></span> 
  
- <span data-ttu-id="4d007-109">Office 365 e 5 평가판 구독을 만들 때에서 30 일이 지나면 만료는 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d007-109">An Office 365 E5 Trial Subscription, which expires 30 days from when you create it.</span></span>
    
- <span data-ttu-id="4d007-p102">간소화 된 조직 인트라넷 (d c 1, a p p 1을 및 CLIENT1) Azure 가상 네트워크의 서브넷에 세 가상 컴퓨터의 구성 되는 인터넷에 연결 합니다. Azure AD 연결 Office 365에 Windows Server AD 도메인을 동기화 하는 a p p 1을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d007-p102">A simplified organization intranet connected to the Internet, consisting of three virtual machines on a subnet of an Azure virtual network (DC1, APP1, and CLIENT1). Azure AD Connect runs on APP1 to synchronize the Windows Server AD domain to Office 365.</span></span>
    
<span data-ttu-id="4d007-112">이 개발/테스트 환경 설정 하는 두 단계로 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d007-112">There are two phases to setting up this dev/test environment:</span></span>
  
1. <span data-ttu-id="4d007-113">Office 365 개발/테스트 환경 (d c 1, a p p 1을 및 CLIENT1 가상 컴퓨터에 Office 365 E5 평가판 구독을 Azure 가상 네트워크를)을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4d007-113">Create the Office 365 dev/test environment (the DC1, APP1, and CLIENT1 virtual machines in an Azure virtual network with an Office 365 E5 trial subscription).</span></span>
    
2. <span data-ttu-id="4d007-114">설치 하 고 a p p 1에서 Azure AD 연결을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d007-114">Install and configure Azure AD Connect on APP1.</span></span>
    
> [!TIP]
> <span data-ttu-id="4d007-115">클릭 [여기](http://aka.ms/catlgstack) 에 한 맵이 하나의 Microsoft 클라우드 테스트 랩 가이드 스택의 모든 문서를 시각적으로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d007-115">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-an-office-365-devtest-environment"></a><span data-ttu-id="4d007-116">1 단계: Office 365 개발/테스트 환경 만들기</span><span class="sxs-lookup"><span data-stu-id="4d007-116">Phase 1: Create an Office 365 dev/test environment</span></span>

<span data-ttu-id="4d007-p103">1, 2 및 [Office 365 개발/테스트 환경](office-365-dev-test-environment.md) 문서의 3 단계에서 지침을 따릅니다. 결과 구성은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4d007-p103">Follow the instructions in phases 1, 2, and 3 of the [Office 365 dev/test environment](office-365-dev-test-environment.md) article. Here is the resulting configuration.</span></span>
  
![Office 365 개발/테스트 환경](images/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
<span data-ttu-id="4d007-120">이 구성은 다음으로 이루어집니다.</span><span class="sxs-lookup"><span data-stu-id="4d007-120">This configuration consists of:</span></span> 
  
- <span data-ttu-id="4d007-121">Office 365 e 5 평가판 구독 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d007-121">An Office 365 E5 Trial Subscription.</span></span>
    
- <span data-ttu-id="4d007-122">간소화 된 조직 인트라넷 Azure 가상 네트워크의 서브넷에서 d c 1, a p p 1을 및 CLIENT1 가상 컴퓨터의 구성 되는 인터넷에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d007-122">A simplified organization intranet connected to the Internet, consisting of the DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network.</span></span>
    
## <a name="phase-2-install-azure-ad-connect-on-app1"></a><span data-ttu-id="4d007-123">2 단계: 설치 Azure AD a p p 1에 연결</span><span class="sxs-lookup"><span data-stu-id="4d007-123">Phase 2: Install Azure AD Connect on APP1</span></span>

<span data-ttu-id="4d007-p104">설치 및 구성한 후 Azure AD 연결 Office 365 평가판 구독에서 계정 집합으로 CORP Windows Server AD 도메인의 계정 집합을 동기화 합니다. 다음 절차를 안내 Azure AD Connect a p p 1을 설치 하 고 작동 하는지 확인 (영문)를 통해 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d007-p104">Once installed and configured, Azure AD Connect synchronizes the set of accounts in the CORP Windows Server AD domain with the set of accounts in your Office 365 trial subscription. The following procedure steps you through installing Azure AD Connect on APP1 and verifying that it works.</span></span>
  
### <a name="install-and-configure-azure-ad-connect-on-app1"></a><span data-ttu-id="4d007-126">설치 하 고 a p p 1에서 Azure AD 연결 구성</span><span class="sxs-lookup"><span data-stu-id="4d007-126">Install and configure Azure AD Connect on APP1</span></span>

1. <span data-ttu-id="4d007-127">[Azure 포털](https://portal.azure.com)는 회사와 a p p 1에 연결\\User1 계정을 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d007-127">From the [Azure portal](https://portal.azure.com), connect to APP1 with the CORP\\User1 account.</span></span>
    
2. <span data-ttu-id="4d007-128">A p p 1을에서 관리자 수준 Windows PowerShell 명령 프롬프트를 열고 하 고 이러한 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d007-128">From APP1, open an administrator-level Windows PowerShell command prompt, and then run these commands:</span></span>
    
  ```
  Set-ItemProperty -Path "HKLM:\\SOFTWARE\\Microsoft\\Active Setup\\Installed Components\\{A509B1A7-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Set-ItemProperty -Path "HKLM:\\SOFTWARE\\Microsoft\\Active Setup\\Installed Components\\{A509B1A8-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Stop-Process -Name Explorer -Force

  ```

3. <span data-ttu-id="4d007-129">작업 표시줄에서 **Internet Explorer** 를 클릭 하 고 [https://aka.ms/aadconnect](https://aka.ms/aadconnect)로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d007-129">From the task bar, click **Internet Explorer** and go to [https://aka.ms/aadconnect](https://aka.ms/aadconnect).</span></span>
    
4. <span data-ttu-id="4d007-130">Microsoft Azure Active Directory에 연결 페이지에서 **다운로드**를 클릭 한 다음 **실행**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d007-130">On the Microsoft Azure Active Directory Connect page, click **Download**, and then click **Run**.</span></span>
    
5. <span data-ttu-id="4d007-131">**Azure AD 연결을 시작** 페이지에서 **동의 함**를 클릭 한 다음 **계속**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d007-131">On the **Welcome to Azure AD Connect** page, click **I agree**, and then click **Continue**.</span></span>
    
6. <span data-ttu-id="4d007-132">**Express 설정** 페이지에서 **express 설정 사용을**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d007-132">On the **Express Settings** page, click **Use express settings**.</span></span>
    
7. <span data-ttu-id="4d007-133">**Azure AD에 연결** 페이지에서 **암호**해당 암호 **사용자 이름,** 형식에 전역 관리자 계정 이름을 입력 하 고 ****을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d007-133">On the **Connect to Azure AD** page, type your global administrator account name in **Username,** type its password in **Password**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="4d007-134">**AD DS에 연결** 페이지에서 입력 **CORP\\User1** **사용자 이름** 에서 **암호**를에서 계정의 암호를 입력 하 고 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d007-134">On the **Connect to AD DS** page, type **CORP\\User1** in **Username,** type its password in **Password**, and then click **Next**.</span></span>
    
9. <span data-ttu-id="4d007-135">**Azure AD 로그인 구성** 페이지에서 **확인 된 모든 도메인 키 지 않고 계속**클릭 하 고 ****을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d007-135">On the **Azure AD sign-in configuration** page, click **Continue without any verified domains**, and then click **Next**.</span></span>
    
10. <span data-ttu-id="4d007-136">**구성 준비 완료** 페이지에서 **설치**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d007-136">On the **Ready to configure** page, click **Install**.</span></span>
    
11. <span data-ttu-id="4d007-137">**구성 완료** 페이지에서 **끝내기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d007-137">On the **Configuration complete** page, click **Exit**.</span></span>
    
12. <span data-ttu-id="4d007-138">Internet Explorer에서 Office 365 포털 ([https://portal.office.com](https://portal.office.com))로 이동 하 고 전역 관리자 계정 사용 하 여 Office 365 평가판 구독에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d007-138">In Internet Explorer, go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
13. <span data-ttu-id="4d007-139">주 포털 페이지에서 **관리**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d007-139">From the main portal page, click **Admin**.</span></span>
    
14. <span data-ttu-id="4d007-140">왼쪽 탐색 영역에서 클릭 **사용자 > 활성 사용자**합니다.</span><span class="sxs-lookup"><span data-stu-id="4d007-140">In the left navigation, click **Users > Active users**.</span></span>
    
    <span data-ttu-id="4d007-p105">**사용자 1**이라는 새 계정을 note 합니다. 이 계정은 CORP Windows Server AD 도메인에서 형식이 며 교정본을 디렉터리 동기화 장치가 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d007-p105">Note the account named **User1**. This account is from the CORP Windows Server AD domain and is proof that DirSync has worked.</span></span>
    
15. <span data-ttu-id="4d007-p106">**User1** 계정을 클릭 합니다. 제품 라이선스에 대 한 **편집**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d007-p106">Click the **User1** account. For product licenses, click **Edit**.</span></span>
    
16. <span data-ttu-id="4d007-p107">**제품 라이선스**해당 국가 선택 하 고 **Office 365 Enterprise E5** ( **On**으로 전환)에 대 한 **오프** 컨트롤을 클릭 합니다. 페이지의 맨 아래에 **저장** 을 클릭 하 고 **닫기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d007-p107">In **Product licenses**, select your country, and then click the **Off** control for **Office 365 Enterprise E5** (switching it to **On**). Click **Save** at the bottom of the page, and then click **Close**.</span></span>
    
<span data-ttu-id="4d007-147">결과 구성입니다.</span><span class="sxs-lookup"><span data-stu-id="4d007-147">This is the resulting configuration.</span></span>
  
![DirSync를 사용하는 Office 365 개발/테스트 환경](images/be5b37b0-f832-4878-b153-436c31546e21.png)
  
<span data-ttu-id="4d007-149">이 구성은 다음으로 이루어집니다.</span><span class="sxs-lookup"><span data-stu-id="4d007-149">This configuration consists of:</span></span> 
  
- <span data-ttu-id="4d007-150">Office 365 e 5 평가판 구독 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d007-150">An Office 365 E5 Trial Subscription.</span></span>
    
- <span data-ttu-id="4d007-p108">간소화 된 조직 인트라넷 Azure 가상 네트워크의 서브넷에서 d c 1, a p p 1을 및 CLIENT1 가상 컴퓨터의 구성 되는 인터넷에 연결 합니다. Azure AD 연결 Office 365에 CORP Windows Server AD 도메인 30 분 마다 동기화 하는 a p p 1을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d007-p108">A simplified organization intranet connected to the Internet, consisting of the DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network. Azure AD Connect runs on APP1 to synchronize the CORP Windows Server AD domain to Office 365 every 30 minutes.</span></span>
    
## <a name="next-step"></a><span data-ttu-id="4d007-153">다음 단계</span><span class="sxs-lookup"><span data-stu-id="4d007-153">Next Step</span></span>

<span data-ttu-id="4d007-154">조직에 대 한 디렉터리 동기화를 배포할 준비가 되 면 [배포 Office 365에서에서 디렉터리 동기화 (DirSync) Microsoft Azure을](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md)참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="4d007-154">When you are ready to deploy DirSync for your organization, see [Deploy Office 365 Directory Synchronization (DirSync) in Microsoft Azure](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4d007-155">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4d007-155">See Also</span></span>

[<span data-ttu-id="4d007-156">클라우드 도입 TLG(테스트 랩 가이드)</span><span class="sxs-lookup"><span data-stu-id="4d007-156">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="4d007-157">기본 구성 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="4d007-157">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="4d007-158">Office 365 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="4d007-158">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="4d007-159">Office 365 개발/테스트 환경에 대 한 클라우드 응용 프로그램 보안</span><span class="sxs-lookup"><span data-stu-id="4d007-159">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="4d007-160">Office 365 개발/테스트 환경에 대 한 위협 보호 고급</span><span class="sxs-lookup"><span data-stu-id="4d007-160">Advanced Threat Protection for your Office 365 dev/test environment</span></span>](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="4d007-161">클라우드 채택 및 하이브리드 솔루션</span><span class="sxs-lookup"><span data-stu-id="4d007-161">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




