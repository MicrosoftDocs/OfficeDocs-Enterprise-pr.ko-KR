---
title: "Office 365 개발/테스트 환경에서 중요 한 파일 보호"
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
- TLG
- Ent_TLGs
ms.assetid: 27ecff45-06a6-4629-bc45-9dab4eef3a21
description: "요약: 구성 및 잘못 된 SharePoint Online 사이트 모음에 게시 된 경우에 Office 365 정보 권한 관리에 중요 한 파일을 보호 하는 방법을 시연 합니다."
ms.openlocfilehash: 388eb2a6288fc72771b6a554d1c9de78febe8a4e
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/09/2018
---
# <a name="sensitive-file-protection-in-the-office-365-devtest-environment"></a><span data-ttu-id="12407-103">Office 365 개발/테스트 환경에서 중요 한 파일 보호</span><span class="sxs-lookup"><span data-stu-id="12407-103">Sensitive file protection in the Office 365 dev/test environment</span></span>

 <span data-ttu-id="12407-104">**요약:** 구성 하 고 잘못 된 SharePoint Online 사이트 모음에 게시 된 경우에 Office 365 정보 권한 관리에 중요 한 파일을 보호 하는 방법을 시연 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-104">**Summary:** Configure and demonstrate how Office 365 Information Rights Management protects your sensitive files, even when they are posted to the wrong SharePoint Online site collection.</span></span>
  
<span data-ttu-id="12407-p101">Office 365의 정보 권한 관리 (IRM)는 SharePoint Online 라이브러리 및 목록에서 다운로드 하는 문서를 보호 하기 위해 기능 집합입니다. 다운로드 한 파일 저장, 열기, 복사본을 포함 및 저장 된 SharePoint Online 라이브러리를 반영 하는 권한이 인쇄 암호화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="12407-p101">Information Rights Management (IRM) in Office 365 is a set of capabilities to protect documents that are downloaded from SharePoint Online libraries and lists. Downloaded files are encrypted and contain the open, copy, save, and print permissions that reflect the SharePoint Online library in which they were stored.</span></span>
  
<span data-ttu-id="12407-107">이 문서의 지침을 함께 사용 하도록 설정 및 Office 365 평가판 구독에서 사용할 수 있는 중요 한 정보를 포함 하는 파일에 대 한 Office 365에서 IRM을 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-107">With the instructions in this article, you enable and test IRM in Office 365 for files containing possible sensitive information in your Office 365 trial subscription.</span></span>
  
> [!TIP]
> <span data-ttu-id="12407-108">클릭 [여기](http://aka.ms/catlgstack) 에 한 맵이 하나의 Microsoft 클라우드 테스트 랩 가이드 스택의 모든 문서를 시각적으로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-108">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a><span data-ttu-id="12407-109">1 단계: Office 365 개발/테스트 환경을 구축합니다</span><span class="sxs-lookup"><span data-stu-id="12407-109">Phase 1: Build out your Office 365 dev/test environment</span></span>

<span data-ttu-id="12407-110">최소 요구 사항을 경량 방식으로 중요 한 파일 보호 기능을 테스트 하려면 2와 [Office 365 개발/테스트 환경](office-365-dev-test-environment.md)의 3 단계에서 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="12407-110">If you just want to test sensitive file protection in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="12407-111">시뮬레이션 된 엔터프라이즈에서 중요 한 파일 보호 기능을 테스트 하려는 경우 [Office 365 개발/테스트 환경에 대 한 디렉터리 동기화](dirsync-for-your-office-365-dev-test-environment.md)의 지시를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="12407-111">If you want to test sensitive file protection in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="12407-p102">중요 한 파일 보호를 테스트 하지 않아도 인터넷에 연결 하는 시뮬레이션 된 인트라넷을 포함 하는 시뮬레이션 된 엔터프라이즈 개발/테스트 환경 및 Windows Server AD 포리스트에 대 한 디렉터리 동기화 합니다. 제공은 중요 한 파일 보호 기능을 테스트 하 고 일반적인 조직을 대표 하는 환경에서 사용해 수 있도록 하는 옵션으로 여기 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-p102">Testing sensitive file protection does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can test sensitive file protection and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-demonstrate-how-documents-from-permissions-protected-sites-can-be-leaked"></a><span data-ttu-id="12407-114">2 단계: 사용 권한으로 보호 된 사이트에서 문서 수 유출 하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="12407-114">Phase 2: Demonstrate how documents from permissions-protected sites can be leaked</span></span>

<span data-ttu-id="12407-115">이 단계는 다른 사용자 수는 사용 권한으로 보호 된 사이트에서 문서를 다운로드 하 고 다음 널리 개방 된 사용 권한이 있는 사이트에 업로드를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="12407-115">In this phase, you demonstrate that someone can download a document from a permissions-protected site and then upload it to a site that has wide-open permissions.</span></span>
  
<span data-ttu-id="12407-116">먼저, 임원 진술 하 고 Office 365 E5 라이선스를 할당 하는 3 개의 새 사용자 계정을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-116">First, you add three new user accounts that represent executives and assign them Office 365 E5 licenses.</span></span>
  
<span data-ttu-id="12407-117">[Office 365 PowerShell 연결](https://technet.microsoft.com/library/dn975125.aspx) 에 지침을 사용 하 여 PowerShell 모듈 (필요한 경우)를 설치 하 고에서 새로운 Office 365 구독에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-117">Use the instructions in [Connect to Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) to install the PowerShell modules (if needed) and connect to your new Office 365 subscription from:</span></span>
  
- <span data-ttu-id="12407-118">사용하는 컴퓨터(경량 Office 365 개발/테스트 환경)</span><span class="sxs-lookup"><span data-stu-id="12407-118">Your computer (for the lightweight Office 365 dev/test environment).</span></span>
    
- <span data-ttu-id="12407-119">(시뮬레이션 된 엔터프라이즈 Office 365 개발/테스트 환경)에 대 한 CLIENT1 가상 컴퓨터로 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-119">The CLIENT1 virtual machine (for the simulated enterprise Office 365 dev/test environment).</span></span>
    
<span data-ttu-id="12407-120">**Windows PowerShell 자격 증명 요청** 대화 상자에서 Office 365 전역 관리자 이름을 입력 합니다 (예: jdoe@contosotoycompany.onmicrosoft.com) 및 Office 365 평가판 구독의 암호입니다.</span><span class="sxs-lookup"><span data-stu-id="12407-120">In the **Windows PowerShell Credential Request** dialog box, type the Office 365 global administrator name (example: jdoe@contosotoycompany.onmicrosoft.com) and password of your Office 365 trial subscription.</span></span>
  
<span data-ttu-id="12407-121">조직 이름을 입력 (예: contosotoycompany) 및 사용자 위치에 대 한 코드 및 Windows Azure Active Directory 모듈에 대 한 Windows PowerShell 프롬프트에서 다음 명령을 실행 하는 다음 두 자리 국가:</span><span class="sxs-lookup"><span data-stu-id="12407-121">Fill in your organization name (example: contosotoycompany) and the two-character country code for your location, and then run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "ceo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CEO" -FirstName "Chief" -LastName "Executive Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

<span data-ttu-id="12407-122">**New-msoluser** 명령의 디스플레이에서 CEO 계정에 대해 생성 된 암호를 확인 하 고 안전한 위치에 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-122">From the display of the **New-MsolUser** command, note the generated password for the CEO account and record it in a safe location.</span></span>
  
<span data-ttu-id="12407-123">Windows PowerShell 프롬프트에 대한 Microsoft Azure Active Directory 모듈에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-123">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "cfo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CFO" -FirstName "Chief" -LastName "Financial Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

<span data-ttu-id="12407-124">**New-msoluser** 명령의 디스플레이에서 CFO 계정에 대해 생성 된 암호를 확인 하 고 안전한 위치에 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-124">From the display of the **New-MsolUser** command, note the generated password for the CFO account and record it in a safe location.</span></span>
  
<span data-ttu-id="12407-125">Windows PowerShell 프롬프트에 대한 Microsoft Azure Active Directory 모듈에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-125">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "coo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "COO" -FirstName "Chief" -LastName "Operations Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

<span data-ttu-id="12407-126">**New-msoluser** 명령의 디스플레이에서 COO 계정에 대해 생성 된 암호를 확인 하 고 안전한 위치에 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-126">From the display of the **New-MsolUser** command, note the generated password for the COO account and record it in a safe location.</span></span>
  
<span data-ttu-id="12407-127">다음으로, 개인 임원 그룹을 만들고 새 임원 계정을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-127">Next, you create a private Executives group and add the new executive accounts to it.</span></span>
  
1. <span data-ttu-id="12407-128">브라우저에서 [http://portal.office.com](http://portal.office.com) 에서 Office 포털로 이동 하 고 전역 관리자 계정 사용 하 여 Office 365 평가판 구독에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-128">In your browser, go to the Office portal at [http://portal.office.com](http://portal.office.com) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
  - <span data-ttu-id="12407-129">Office 365 개발/테스트 환경 lightweight를 사용 하는 경우 Internet Explorer 또는 브라우저의 개인 세션을 열고 로컬 컴퓨터에서 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-129">If you are using the lightweight Office 365 dev/test environment, open a private session of Internet Explorer or your browser and sign in from your local computer.</span></span>
    
  - <span data-ttu-id="12407-130">시뮬레이션 된 엔터프라이즈 Office 365 개발/테스트 환경을 사용 하는 경우 Azure 포털을 사용 하 여 CLIENT1 가상 컴퓨터에 연결한 다음 CLIENT1에서 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-130">If you are using the simulated enterprise Office 365 dev/test environment, use the Azure portal to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="12407-131">**Microsoft Office 홈** 탭에서 클릭 **관리 > 그룹 > 그룹**, **그룹 추가**클릭 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12407-131">On the **Microsoft Office Home** tab, click **Admin > Groups > Groups**, and then click **Add a group**.</span></span>
    
3. <span data-ttu-id="12407-132">**추가 그룹**에서 그룹 종류에 대 한 **Office 365 그룹** 을 선택, **임원** **이름과 **그룹 Id**를** 입력 **개인** **개인정보 보호**대 한 선택한 다음 클릭 **소유자를 선택**합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-132">In **Add a group**, select **Office 365 group** for the group type, type **Executives** in **Name** and **Group Id**, select **Private** for **Privacy**, and then click **Select Owner**.</span></span>
    
4. <span data-ttu-id="12407-133">목록에서 전역 관리자 계정 이름을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-133">In the list, click your global administrator account name.</span></span>
    
5. <span data-ttu-id="12407-134">**추가**클릭 한 다음 **닫기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-134">Click **Add**, and then click **Close**.</span></span>
    
6. <span data-ttu-id="12407-135">그룹 목록에서 **중역**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-135">In the groups list, click **Executives**.</span></span>
    
7. <span data-ttu-id="12407-136">**구성원에 대 한 편집**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-136">Click **Edit for Members**.</span></span>
    
8. <span data-ttu-id="12407-p103">**구성원 추가**클릭 합니다. 구성원 목록에서 다음 사용자 계정을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-p103">Click **Add members**. In the member list, select the following user accounts:</span></span>
    
  - <span data-ttu-id="12407-139">중역이 책임자</span><span class="sxs-lookup"><span data-stu-id="12407-139">Chief Executive Officer</span></span>
    
  - <span data-ttu-id="12407-140">회계 부 책임자</span><span class="sxs-lookup"><span data-stu-id="12407-140">Chief Financial Officer</span></span>
    
  - <span data-ttu-id="12407-141">작업 책임자</span><span class="sxs-lookup"><span data-stu-id="12407-141">Chief Operations Officer</span></span>
    
9. <span data-ttu-id="12407-142">**저장**을 클릭 한 다음 **닫기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-142">Click **Save**, and then click **Close**.</span></span>
    
10. <span data-ttu-id="12407-143">**Office 관리 센터** 탭을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="12407-143">Close the **Office Admin center** tab.</span></span>
    
<span data-ttu-id="12407-144">다음으로 임원 사이트 모음을 만들고에 대 한 액세스는 임원 그룹의 구성원만 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-144">Next, you create an Executives site collection and allow just the members of the Executives group to access it.</span></span>
  
1. <span data-ttu-id="12407-145">**Microsoft Office 홈** 탭에서 **관리** 타일을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-145">On the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
2. <span data-ttu-id="12407-146">**Office 관리 센터** 탭을 클릭 **관리 센터 > SharePoint**합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-146">On the **Office Admin center** tab, click **Admin centers > SharePoint**.</span></span>
    
3. <span data-ttu-id="12407-147">**SharePoint 관리 센터** 탭을 클릭 **새로 만들기 > 개인 사이트 모음**합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-147">On the **SharePoint admin center** tab, click **New > Private site collection**.</span></span>
    
4. <span data-ttu-id="12407-148">새 사이트 모음 창에서 **임원** **제목**, 경영진의 URL 상자에서에 입력 하 고 **관리자**, 전역 관리자 계정의 이름을 지정 한 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-148">In the new site collection pane, type **Executives** in **Title**, executives in the URL box, specify the name of your global administrator account in **Administrator**, and then click **OK**.</span></span>
    
5. <span data-ttu-id="12407-p104">새 사이트 모음도 만들지 않은 때까지 기다립니다. 완료 되 면 새 임원 사이트 모음의 URL을 복사 하 고 브라우저의 새 탭에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="12407-p104">Wait until the new site collection has been created. When complete, copy the URL of the new Executives site collection and paste it into a new tab of your browser.</span></span>
    
6. <span data-ttu-id="12407-151">**임원** 사이트 모음의 오른쪽 위에 있는 설정 아이콘을 클릭 하 고 **공유 대상을**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-151">In the upper right of the **Executives** site collection, click the settings icon, and then click **Shared with**.</span></span>
    
7. <span data-ttu-id="12407-152">**공유 '임원'** **고급**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-152">In **Share 'Executives'**, click **Advanced**.</span></span>
    
8. <span data-ttu-id="12407-153">SharePoint 그룹의 목록에서 **임원 구성원**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-153">In the list of SharePoint groups, click **Executives Members**.</span></span>
    
9. <span data-ttu-id="12407-154">**사용자 및 그룹** 페이지에서 **새로 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-154">On the **People and Groups** page, click **New**.</span></span>
    
10. <span data-ttu-id="12407-155">**공유 '임원'** **임원**를 입력 하 고 **임원** 그룹을 클릭 한 다음 **공유**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-155">In **Share 'Executives'**, type **Executives**, click the **Executives** group, and then click **Share**.</span></span>
    
11. <span data-ttu-id="12407-156">**사용자 및 그룹** 탭을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="12407-156">Close the **People and groups** tab.</span></span>
    
<span data-ttu-id="12407-157">다음으로 모든 사용자가 판매 사이트 모음에 액세스 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-157">Next, you allow everyone to access the Sales site collection.</span></span>
  
1. <span data-ttu-id="12407-158">**SharePoint 관리 센터** 탭에서 Sales 사이트 모음의 URL을 복사 하 고 브라우저의 새 탭에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="12407-158">From the **SharePoint admin center** tab, copy the URL of the Sales site collection and paste it into a new tab of your browser..</span></span>
    
2. <span data-ttu-id="12407-159">오른쪽 위에 있는 설정 아이콘을 클릭 하 고 **공유 대상을**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-159">In the upper right, click the settings icon, and then click **Shared with**.</span></span>
    
3. <span data-ttu-id="12407-160">**공유 '영업 사이트 모음의'** **고급**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-160">In **Share 'Sales site collection'**, click **Advanced**.</span></span>
    
4. <span data-ttu-id="12407-161">SharePoint 그룹의 목록에서 **판매 사이트 모음 구성원을**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-161">In the list of SharePoint groups, click **Sales site collection Members**.</span></span>
    
5. <span data-ttu-id="12407-162">**사용자 및 그룹** 페이지에서 **새로 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-162">On the **People and Groups** page, click **New**.</span></span>
    
6. <span data-ttu-id="12407-163">**'영업 사이트 모음의' 공유** **모든 사용자**를 입력 하 고 **외부 사용자를 제외한 모든**를 클릭 한 다음 **공유**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-163">In **Share 'Sales site collection'**, type **Everyone**, click **Everyone except external users**, and then click **Share**.</span></span>
    
7. <span data-ttu-id="12407-164">다음은 **Sales 사이트 모음** 및 **SharePoint** 탭을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="12407-164">Close the **Sales site collection** and **SharePoint** tabs.</span></span>
    
<span data-ttu-id="12407-165">다음으로, 임원 계정을 사용 하 여 로그인 및 임원 사이트 모음에서 문서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="12407-165">Next, you sign in with an executive account and create a document in the Executives site collection.</span></span>
  
1. <span data-ttu-id="12407-166">**Microsoft Office 홈** 탭에서 위 오른쪽에 있는 사용자 아이콘을 클릭 한 다음 **로그 아웃**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-166">On the **Microsoft Office Home** tab, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="12407-167">[Http://portal.office.com](http://portal.office.com)로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-167">Go to [http://portal.office.com](http://portal.office.com).</span></span>
    
3. <span data-ttu-id="12407-168">**Office 365 로그인** 페이지에서 **다른 계정 사용**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-168">On the **Office 365 sign in** page, click **Use another account**.</span></span>
    
4. <span data-ttu-id="12407-169">**CEO** 계정 이름 및 해당 암호를 입력 하 고 **로그인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-169">Type the **CEO** account name and its password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="12407-170">브라우저의 새 탭에서 임원 사이트 모음에 URL을 입력 합니다 ( **https://**\<조직 이름 >**.sharepoint.com/sites/executives**).</span><span class="sxs-lookup"><span data-stu-id="12407-170">On a new tab of your browser, type the URL to the Executives site collection ( **https://**\<organization name>**.sharepoint.com/sites/executives**).</span></span>
    
6. <span data-ttu-id="12407-171">**문서**를 클릭 하 고 **새로 만들기** 를 클릭 한 다음 **Word 문서**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-171">Click **Documents**, click **New,** and then click **Word Document**.</span></span>
    
7. <span data-ttu-id="12407-172">제목 표시줄에서 클릭 하 고 **SensitiveData BeforeIRM**를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-172">Click in the title bar and type **SensitiveData-BeforeIRM**.</span></span>
    
8. <span data-ttu-id="12407-173">문서 본문에 클릭 하 고 **최신 보드 모임에서 시간 (분)을**입력 한 다음 **경영진**을 클릭 하 고 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-173">Click in the document body and type **Minutes from the latest board meeting**, and then click **Executives**.</span></span>
    
     <span data-ttu-id="12407-174">**문서** 폴더에 **SensitiveData BeforeIRM.docx** 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="12407-174">You should see **SensitiveData-BeforeIRM.docx** in the **Documents** folder.</span></span>
    
<span data-ttu-id="12407-175">다음으로 SensitiveData BeforeIRM.docx 문서의 로컬 복사본을 다운로드 하 고 Sales 사이트 모음을 실수로 게시 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-175">Next, you download a local copy of the SensitiveData-BeforeIRM.docx document and then accidentally post it to the Sales site collection.</span></span>
  
1. <span data-ttu-id="12407-176">로컬 컴퓨터에서 새 폴더를 만듭니다 (예: c:\\Tlg\\SensitiveDataTestFiles).</span><span class="sxs-lookup"><span data-stu-id="12407-176">On your local computer, create a new folder (for example, C:\\TLGs\\SensitiveDataTestFiles).</span></span>
    
2. <span data-ttu-id="12407-177">브라우저에서 **문서** 탭에서 **SensitiveData BeforeIRM.docx** 문서를 선택, 있는 줄임표를 클릭 하 고 **다운로드**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-177">On the **Documents** tab of your browser, select the **SensitiveData-BeforeIRM.docx** document, click the ellipses, and then click **Download**.</span></span>
    
3. <span data-ttu-id="12407-178">1 단계에서 만든 폴더에 **SensitiveData BeforeIRM.docx** 문서를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-178">Store the **SensitiveData-BeforeIRM.docx** document in the folder created in step 1.</span></span>
    
4. <span data-ttu-id="12407-179">브라우저의 새 탭에서 Sales 사이트 모음에 URL을 입력 합니다 ( **https://**\<조직 이름 >**.sharepoint.com/sites/sales**).</span><span class="sxs-lookup"><span data-stu-id="12407-179">On a new tab of your browser, type the URL to the Sales site collection ( **https://**\<organization name>**.sharepoint.com/sites/sales**).</span></span>
    
5. <span data-ttu-id="12407-180">**판매 사이트 모음을 사이트**의 **문서** 폴더를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-180">Click the **Documents** folder of the **Sales site collection**.</span></span>
    
6. <span data-ttu-id="12407-181">**업로드**를 클릭 하 고 1 단계에서 만든 폴더에 **SensitiveData BeforeIRM.docx** 문서를 지정 하 고 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-181">Click **Upload**, and then specify **SensitiveData-BeforeIRM.docx** document in the folder created in step 1, and then click **OK**.</span></span>
    
7. <span data-ttu-id="12407-182">**문서** 폴더에 **SensitiveData BeforeIRM.docx** 문서 인지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-182">Verify that the **SensitiveData-BeforeIRM.docx** document is in the **Documents** folder.</span></span>
    
8. <span data-ttu-id="12407-183">**판매** 및 **SharePoint** 탭을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="12407-183">Close the **Sales** and **SharePoint** tabs.</span></span>
    
<span data-ttu-id="12407-184">다음으로 User5로 로그인 한 Sales 사이트 모음에서 SensitiveData BeforeIRM.docx 문서를 열려고 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-184">Next, you sign in as User5 and try to open the SensitiveData-BeforeIRM.docx document in the Sales site collection.</span></span>
  
1. <span data-ttu-id="12407-185">**Microsoft Office 홈** 탭에서 위 오른쪽에 있는 사용자 아이콘을 클릭 한 다음 **로그 아웃**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-185">On the **Microsoft Office Home** tab, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="12407-186">[Http://portal.office.com](http://portal.office.com)로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-186">Go to [http://portal.office.com](http://portal.office.com).</span></span>
    
3. <span data-ttu-id="12407-187">**Office 365 로그인** 페이지에서 **다른 계정 사용**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-187">On the **Office 365 sign in** page, click **Use another account**.</span></span>
    
4. <span data-ttu-id="12407-188">User5 계정 이름 및 해당 암호를 입력 하 고 **로그인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-188">Type the User5 account name and its password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="12407-189">브라우저의 새 탭에서 Sales 사이트 모음에 URL을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-189">On a new tab of your browser, type the URL to the Sales site collection.</span></span>
    
6. <span data-ttu-id="12407-190">**판매 사이트 모음을 사이트**의 **문서** 폴더를 **SensitiveData BeforeIRM.docx** 문서를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-190">In the **Documents** folder of the **Sales site collection**, click the **SensitiveData-BeforeIRM.docx** document.</span></span>
    
    <span data-ttu-id="12407-191">해당 내용을 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="12407-191">You should see its contents.</span></span>
    
7. <span data-ttu-id="12407-192">다음은 **문서** 및 **판매 사이트 모음** 탭을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="12407-192">Close the **Documents** and **Sales site collection** tabs.</span></span>
    
<span data-ttu-id="12407-193">영업 사이트 모음의 SensitiveData BeforeIRM.docx 문서를 실수로 게시, 하 여 CEO 임원 사이트 모음의 사용 권한 보안을 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="12407-193">By accidentally posting the SensitiveData-BeforeIRM.docx document on the Sales site collection, the CEO bypassed the permissions security of the Executives site collection.</span></span>
  
<span data-ttu-id="12407-194">단계 3과 4에 대 한 Office 365를 준비 하려면 SharePoint Online에 대 한 IRM을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-194">To prepare Office 365 for Phases 3 and 4, enable IRM for SharePoint Online.</span></span>
  
1. <span data-ttu-id="12407-195">**Microsoft Office 홈** 탭에서 위 오른쪽에 있는 사용자 아이콘을 클릭 한 다음 **로그 아웃**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-195">On the **Microsoft Office Home** tab, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="12407-196">[Http://portal.office.com](http://portal.office.com)로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-196">Go to [http://portal.office.com](http://portal.office.com).</span></span>
    
3. <span data-ttu-id="12407-197">**Office 365 로그인** 페이지에서 전역 관리자 계정 이름을 클릭 하 고 해당 암호를 입력 한 다음 **로그인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-197">On the **Office 365 sign in** page, click the global administrator account name, type its password, and then click **Sign in**.</span></span>
    
4. <span data-ttu-id="12407-198">**Microsoft Office 홈** 탭에서 클릭 **관리 > 관리 센터 > SharePoint**합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-198">On the **Microsoft Office Home** tab, click **Admin > Admin centers > SharePoint**.</span></span>
    
5. <span data-ttu-id="12407-199">**SharePoint 관리 센터** 탭에서 **설정**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-199">On the **SharePoint admin center** tab, click **Settings**.</span></span>
    
6. <span data-ttu-id="12407-200">**설정** 페이지의 **정보 권한 관리 (IRM)** 섹션에서 **구성에 지정 된 IRM 서비스를 사용 하 여**를 선택한 다음 **새로고침 IRM 설정**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-200">On the **Settings** page, in the **Information Rights Management (IRM)** section, select **Use the IRM service specified in your configuration**, and then select **Refresh IRM Settings**.</span></span>
    
7. <span data-ttu-id="12407-201">**SharePoint 관리 센터** 탭을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="12407-201">Close the **SharePoint admin center** tab.</span></span>
    
## <a name="phase-3-use-sharepoint-information-rights-management-with-an-office-365-private-group"></a><span data-ttu-id="12407-202">Office 365 개인 그룹과 3 단계: 사용 하 여 SharePoint 정보 권한 관리</span><span class="sxs-lookup"><span data-stu-id="12407-202">Phase 3: Use SharePoint Information Rights Management with an Office 365 private group</span></span>

<span data-ttu-id="12407-203">이 단계에서 열기 권한으로 사이트에 게시 하는 경우에 중요 한 정보를 사용 하 여 문서에 대 한 액세스를 보호 하기 위해 Office 365 개인 그룹과 SharePoint 정보 권한 관리를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-203">In this phase, you use SharePoint Information Rights Management with an Office 365 private group to protect access to a document with sensitive information, even when it is posted on a site with open permissions.</span></span>
  
<span data-ttu-id="12407-204">첫째, 사용 하도록 설정 및 임원 사이트 모음의 문서 라이브러리에 대 한 IRM을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-204">First, you enable and configure IRM for the documents library of the Executives site collection.</span></span> 
  
1. <span data-ttu-id="12407-205">브라우저의 새 탭에서 임원 사이트 모음에 URL을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-205">On a new tab of your browser, type the URL to the Executives site collection.</span></span>
    
2. <span data-ttu-id="12407-206">**문서**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-206">Click **Documents**.</span></span>
    
3. <span data-ttu-id="12407-207">위 오른쪽에서 설정 아이콘을 클릭 하 고 **라이브러리 설정**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-207">In the upper-right, click the settings icon, and then click **Library settings**.</span></span>
    
4. <span data-ttu-id="12407-208">**설정** 페이지의 **사용 권한 및 관리**에서 **정보 권한 관리**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-208">On the **Settings** page, under **Permissions and Management**, click **Information Rights Management**.</span></span>
    
5. <span data-ttu-id="12407-209">**정보 권한 관리 설정** 페이지 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-209">On the **Information Rights Management Settings** page:</span></span>
    
  - <span data-ttu-id="12407-210">**다운로드 시이 라이브러리에서 문서에 대 한 사용 권한을 제한**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-210">Select **Restrict permission to documents in this library on download**.</span></span>
    
  - <span data-ttu-id="12407-211">**권한 정책 제목 만들기**대 한 **경영진**을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-211">For **Create a permission policy title**, type **Executives**.</span></span>
    
  - <span data-ttu-id="12407-212">**추가 권한 정책 설명**대 한 **중역에 대 한 IRM**을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-212">For **Add a permission policy description**, type **IRM for executives**.</span></span>
    
6. <span data-ttu-id="12407-213">**옵션 표시**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-213">Click **Show Options**.</span></span>
    
7. <span data-ttu-id="12407-214">**추가 IRM 라이브러리 설정을**에서 **IRM을 지원 하지 않는 문서를 업로드할 수 없도록 함**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-214">Under **Set additional IRM library settings**, select **Do not allow users to upload documents that do not support IRM**.</span></span>
    
8. <span data-ttu-id="12407-215">**구성 문서 액세스 권한** **허용 뷰어 인쇄** 하 고 **허용 뷰어 다운로드 한 문서의 복사본에 쓸 수**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-215">Under **Configure document access rights**, select **Allow viewers to print** and **Allow viewers to write on a copy of the downloaded document**.</span></span>
    
9. <span data-ttu-id="12407-216">**그룹 보호 및 자격 증명 간격 설정**에서 **허용 그룹 보호** 를 선택 하 고 **기본 그룹**에 대 한 **경영진**을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-216">Under **Set group protection and credentials interval**, select **Allow group protection** and for **Default group**, type **Executives**.</span></span>
    
10. <span data-ttu-id="12407-217">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-217">Click **OK**.</span></span>
    
<span data-ttu-id="12407-218">다음으로, CEO 역할을 있습니다 임원 문서 폴더에 새 문서를 업로드, 다운로드, 다음 실수로 Sales 문서 폴더에 업로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-218">Next, acting as the CEO, you upload a new document to the Executives document folder, download it, then accidentally upload it to the Sales document folder.</span></span>
  
1. <span data-ttu-id="12407-219">**SensitiveData BeforeIRM.docx** 문서를 저장 하는 로컬 폴더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="12407-219">Open the local folder where you stored the **SensitiveData-BeforeIRM.docx** document.</span></span>
    
2. <span data-ttu-id="12407-220">**SensitiveData BeforeIRM.docx**마우스 오른쪽 단추로 클릭 한 다음 **복사**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-220">Right-click **SensitiveData-BeforeIRM.docx**, and then click **Copy**.</span></span>
    
3. <span data-ttu-id="12407-221">폴더를 마우스 오른쪽 **붙여넣기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-221">Right-click within the folder, and then click **Paste**.</span></span>
    
4. <span data-ttu-id="12407-222">새 **SensitiveData-BeforeIRM-Copy.docx** 파일을 **SensitiveData AfterIRM.docx**을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="12407-222">Rename the new **SensitiveData-BeforeIRM - Copy.docx** file to **SensitiveData-AfterIRM.docx**.</span></span>
    
5. <span data-ttu-id="12407-223">브라우저에서 **Microsoft Office 홈** 탭에서 위 오른쪽에 있는 사용자 아이콘을 클릭 한 다음 **로그 아웃**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-223">From the **Microsoft Office Home** tab in your browser, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
6. <span data-ttu-id="12407-224">[Http://portal.office.com](http://portal.office.com)로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-224">Go to [http://portal.office.com](http://portal.office.com).</span></span>
    
7. <span data-ttu-id="12407-225">**Office 365 로그인** 페이지에서 CEO 계정 이름을 클릭 하 고 해당 암호를 입력 한 다음 **로그인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-225">On the **Office 365 sign in** page, click the CEO account name, type its password, and then click **Sign in**.</span></span>
    
8. <span data-ttu-id="12407-226">브라우저의 새 탭에서 임원 사이트 모음에 URL을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-226">On a new tab of your browser, type the URL to the Executives site collection.</span></span>
    
9. <span data-ttu-id="12407-227">**문서** 페이지에서 **업로드**를 클릭, 로컬 폴더, **SensitiveData AfterIRM.docx** 문서를 지정 하 고 **열기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-227">On the **Documents** page, click **Upload**, specify the **SensitiveData-AfterIRM.docx** document in your local folder, and then click **Open**.</span></span>
    
10. <span data-ttu-id="12407-228">**문서** 페이지에서 새 **SensitiveData AfterIRM.docx** 문서를 선택 하 고 메뉴 모음에서 줄임표 (...)를 클릭 한 다음 **다운로드**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-228">Select the new **SensitiveData-AfterIRM.docx** document in the **Documents** page, click the ellipsis (…) in the menu bar, and then click **Download**.</span></span>
    
11. <span data-ttu-id="12407-229">대화 상자가 나타나면 원래 버전을 덮어쓰지 로컬 폴더, **SensitiveData AfterIRM.docx** 문서를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-229">When prompted, save the **SensitiveData-AfterIRM.docx** document in your local folder, overwriting the original version.</span></span>
    
12. <span data-ttu-id="12407-230">**문서** 페이지에 대 한 탭을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="12407-230">Close the tab for the **Documents** page.</span></span>
    
13. <span data-ttu-id="12407-231">브라우저의 새 탭에서 Sales 사이트 모음에 URL을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-231">On a new tab of your browser, type the URL to the Sales site collection.</span></span>
    
14. <span data-ttu-id="12407-232">**문서**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-232">Click **Documents**.</span></span>
    
15. <span data-ttu-id="12407-233">**문서** 페이지에서 **업로드**를 클릭, 로컬 폴더, **SensitiveData AfterIRM.docx** 문서를 지정 하 고 **열기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-233">On the **Documents** page, click **Upload**, specify the **SensitiveData-AfterIRM.docx** document in your local folder, and then click **Open**.</span></span>
    
16. <span data-ttu-id="12407-234">다음은 **Sales 사이트 모음** 및 **SharePoint** 탭을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="12407-234">Close the **Sales site collection** and **SharePoint** tabs.</span></span>
    
<span data-ttu-id="12407-235">다음으로 일반 사용자 역할을 하려고 하면 Sales 문서 폴더에 **SensitiveData AfterIRM.docx** 문서에 액세스 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-235">Next, acting as a normal user, you try to access the **SensitiveData-AfterIRM.docx** document in the Sales document folder.</span></span>
  
1. <span data-ttu-id="12407-236">브라우저에서 **Microsoft Office 홈** 탭에서 위 오른쪽에 있는 사용자 아이콘을 클릭 한 다음 **로그 아웃**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-236">From the **Microsoft Office Home** tab in your browser, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="12407-237">[Http://portal.office.com](http://portal.office.com)로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-237">Go to [http://portal.office.com](http://portal.office.com).</span></span>
    
3. <span data-ttu-id="12407-238">**Office 365 로그인** 페이지에서 User5 계정 이름을 클릭 하 고 해당 암호를 입력 한 다음 **로그인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-238">On the **Office 365 sign in** page, click the User5 account name, type its password, and then click **Sign in**.</span></span>
    
4. <span data-ttu-id="12407-239">브라우저의 새 탭에서 Sales 사이트 모음에 URL을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-239">On a new tab of your browser, type the URL to the Sales site collection.</span></span>
    
5. <span data-ttu-id="12407-240">**문서**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-240">Click **Documents**.</span></span>
    
6. <span data-ttu-id="12407-241">**문서** 페이지에서 **SensitiveData AfterIRM.docx** 문서를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="12407-241">On the **Documents** page, open the **SensitiveData-AfterIRM.docx** document.</span></span>
    
    <span data-ttu-id="12407-242">"사과, Word 온라인 정보 권한 관리 (IRM)를 통해 보호 되어 있으므로이 문서를 열 수 없습니다." 되었다는 메시지가 나타나야 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-242">You should see a message that states "Sorry, Word Online can't open this document because it's protected by Information Rights Management (IRM)."</span></span> 
    
7. <span data-ttu-id="12407-p105">**Word에서 편집**을 클릭 합니다. 메시지가 표시 되는 파일을 열 하려는 경우. **예**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-p105">Click **Edit in Word**. You are prompted if you want to open the file. Click **Yes**.</span></span>
    
8. <span data-ttu-id="12407-p106">로그인 하는 메시지가 User5 계정의 계정 이름을 입력 하 고 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-p106">You are prompted to sign-in. Type the account name of the User5 account, and then click **Next**.</span></span>
    
9. <span data-ttu-id="12407-p107">암호를 제공 하 라는 메시지가 표시 됩니다. User5 계정에 대 한 암호를 입력 한 다음 **로그인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-p107">You are prompted to provide the password. Type the password for the User5 account and then click **Sign in**.</span></span> 
    
    <span data-ttu-id="12407-250">확인할 수는 없다는 메시지: "없는이 문서를 열 수 있도록 하는 자격 증명입니다."</span><span class="sxs-lookup"><span data-stu-id="12407-250">You should see the a message that states: "You do not have the credentials that allow you to open this document."</span></span>
    
10. <span data-ttu-id="12407-251">**아니요**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-251">Click **No**.</span></span>
    
<span data-ttu-id="12407-p108">IRM 보호를 참조 하는 다른 방법은 로컬 폴더에 파일에서 확인 하는 것입니다. **SensitiveData AfterIRM.docx** **SensitiveData BeforeIRM.docx** 파일 보다 훨씬 더 큰 있어야 합니다. **SensitiveData AfterIRM.docx** 파일은 암호화 및 IRM 보호 정보를 사용 하 여 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="12407-p108">Another way to see the IRM protection is to look at the files in your local folder. The **SensitiveData-AfterIRM.docx** should be much larger than the **SensitiveData-BeforeIRM.docx** file. The **SensitiveData-AfterIRM.docx** file is encrypted and has the IRM protection information added to it.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="12407-255">참고 항목</span><span class="sxs-lookup"><span data-stu-id="12407-255">See Also</span></span>

[<span data-ttu-id="12407-256">클라우드 도입 TLG(테스트 랩 가이드)</span><span class="sxs-lookup"><span data-stu-id="12407-256">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="12407-257">기본 구성 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="12407-257">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="12407-258">Office 365 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="12407-258">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="12407-259">클라우드 채택 및 하이브리드 솔루션</span><span class="sxs-lookup"><span data-stu-id="12407-259">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)


