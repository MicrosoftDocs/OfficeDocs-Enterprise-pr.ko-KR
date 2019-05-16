---
title: Office 365 개발/테스트 환경용 중요 파일 보호
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/01/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 27ecff45-06a6-4629-bc45-9dab4eef3a21
description: '요약: 잘못 된 SharePoint Online 사이트 모음에 게시 된 경우에도 Office 365 정보 권한 관리가 중요 한 파일을 보호 하는 방법을 구성 하 고 설명 합니다.'
ms.openlocfilehash: a845742f7ec874d63269f5f380568b7bb59cfe0d
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070894"
---
# <a name="sensitive-file-protection-in-the-office-365-devtest-environment"></a><span data-ttu-id="97586-103">Office 365 개발/테스트 환경용 중요 파일 보호</span><span class="sxs-lookup"><span data-stu-id="97586-103">Sensitive file protection in the Office 365 dev/test environment</span></span>

 <span data-ttu-id="97586-104">**요약:** Office 365 정보 권한 관리가 잘못 된 SharePoint Online 사이트 모음에 게시 된 경우에도 중요 한 파일을 보호 하는 방법을 구성 하 고 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="97586-104">**Summary:** Configure and demonstrate how Office 365 Information Rights Management protects your sensitive files, even when they are posted to the wrong SharePoint Online site collection.</span></span>
  
<span data-ttu-id="97586-105">Office 365의 IRM (정보 권한 관리)은 SharePoint Online 라이브러리 및 목록에서 다운로드 되는 문서를 보호 하는 기능 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="97586-105">Information Rights Management (IRM) in Office 365 is a set of capabilities to protect documents that are downloaded from SharePoint Online libraries and lists.</span></span> <span data-ttu-id="97586-106">다운로드 된 파일은 암호화 되며 저장 된 SharePoint Online 라이브러리를 반영 하는 열기, 복사, 저장 및 인쇄 권한을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-106">Downloaded files are encrypted and contain the open, copy, save, and print permissions that reflect the SharePoint Online library in which they were stored.</span></span>
  
<span data-ttu-id="97586-107">이 문서의 지침을 사용 하 여 Office 365 평가판 구독에서 가능한 중요 한 정보가 포함 된 파일에 대 한 IRM을 설정 하 고 Office 365에서 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-107">With the instructions in this article, you enable and test IRM in Office 365 for files containing possible sensitive information in your Office 365 trial subscription.</span></span>
  
> [!TIP]
> <span data-ttu-id="97586-108">[여기](http://aka.ms/catlgstack)를 클릭하여 Office 365 테스트 랩 가이드 스택의 모든 문서에 대한 가상 맵을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97586-108">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the Office 365 Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a><span data-ttu-id="97586-109">1 단계: Office 365 개발/테스트 환경 구축</span><span class="sxs-lookup"><span data-stu-id="97586-109">Phase 1: Build out your Office 365 dev/test environment</span></span>

<span data-ttu-id="97586-110">최소 요구 사항에 따라 간단한 방법으로 중요 한 파일 보호를 테스트 하려는 경우에는 [Office 365 개발/테스트 환경의](office-365-dev-test-environment.md)2, 3 단계의 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="97586-110">If you just want to test sensitive file protection in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="97586-111">시뮬레이트된 엔터프라이즈에서 중요 한 파일 보호를 테스트 하려면 [Office 365 개발/테스트 환경용 DirSync](dirsync-for-your-office-365-dev-test-environment.md)의 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="97586-111">If you want to test sensitive file protection in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="97586-112">중요 한 파일 보호를 테스트 하려면 AD DS (Active Directory 도메인 서비스) 포리스트의 인터넷 및 디렉터리 동기화에 연결 된 시뮬레이트된 인트라넷을 포함 하는 시뮬레이트된 엔터프라이즈 개발/테스트 환경이 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="97586-112">Testing sensitive file protection does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Active Directory Domain Services (AD DS) forest.</span></span> <span data-ttu-id="97586-113">중요 한 파일 보호 기능을 테스트 하 고 일반적인 조직을 나타내는 환경에서 테스트해 볼 수 있도록 여기에 제공 되는 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="97586-113">It is provided here as an option so that you can test sensitive file protection and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-demonstrate-how-documents-from-permissions-protected-sites-can-be-leaked"></a><span data-ttu-id="97586-114">2 단계: 사용 권한으로 보호 되는 사이트의 문서가 누수 될 수 있는 방식 설명</span><span class="sxs-lookup"><span data-stu-id="97586-114">Phase 2: Demonstrate how documents from permissions-protected sites can be leaked</span></span>

<span data-ttu-id="97586-115">이 단계에서는 누군가가 사용 권한으로 보호 된 사이트에서 문서를 다운로드 한 다음, 사용자를 사이트에 업로드 하 여 파일을 광범위 하 게 사용할 수 있도록 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="97586-115">In this phase, you demonstrate that someone can download a document from a permissions-protected site and then upload it to a site that has wide-open permissions.</span></span>
  
<span data-ttu-id="97586-116">먼저 임원을 나타내는 새 사용자 계정을 세 개 추가 하 고 Office 365 E5 라이선스를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-116">First, you add three new user accounts that represent executives and assign them Office 365 E5 licenses.</span></span>
  
<span data-ttu-id="97586-117">[Office 365 powershell에 연결](https://technet.microsoft.com/library/dn975125.aspx) 의 지침을 사용 하 여 powershell 모듈 (필요한 경우)을 설치 하 고 다음에서 새 Office 365 구독에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-117">Use the instructions in [Connect to Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) to install the PowerShell modules (if needed) and connect to your new Office 365 subscription from:</span></span>
  
- <span data-ttu-id="97586-118">사용하는 컴퓨터(경량 Office 365 개발/테스트 환경)</span><span class="sxs-lookup"><span data-stu-id="97586-118">Your computer (for the lightweight Office 365 dev/test environment).</span></span>
    
- <span data-ttu-id="97586-119">CLIENT1 가상 컴퓨터(시뮬레이트된 엔터프라이즈 Office 365 개발/테스트 환경)</span><span class="sxs-lookup"><span data-stu-id="97586-119">The CLIENT1 virtual machine (for the simulated enterprise Office 365 dev/test environment).</span></span>
    
<span data-ttu-id="97586-120">**Windows PowerShell 자격 증명 요청** 대화 상자에서 office 365 전역 관리자 이름 (예: jdoe@contosotoycompany.onmicrosoft.com)과 office 365 평가판 구독의 암호를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-120">In the **Windows PowerShell Credential Request** dialog box, type the Office 365 global administrator name (example: jdoe@contosotoycompany.onmicrosoft.com) and password of your Office 365 trial subscription.</span></span>
  
<span data-ttu-id="97586-121">조직 이름 (예: contosotoycompany)과 해당 위치에 대 한 두 문자로 된 국가 코드를 입력 한 다음 windows PowerShell 프롬프트 용 Windows Azure Active Directory 모듈에서 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-121">Fill in your organization name (example: contosotoycompany) and the two-character country code for your location, and then run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "ceo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CEO" -FirstName "Chief" -LastName "Executive Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

<span data-ttu-id="97586-122">**Get-msoluser** 명령을 표시할 때 CEO 계정에 대해 생성 된 암호를 확인 하 고 안전한 위치에 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-122">From the display of the **New-MsolUser** command, note the generated password for the CEO account and record it in a safe location.</span></span>
  
<span data-ttu-id="97586-123">Windows PowerShell 프롬프트에 대한 Microsoft Azure Active Directory 모듈에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-123">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "cfo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CFO" -FirstName "Chief" -LastName "Financial Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

<span data-ttu-id="97586-124">**Get-msoluser** 명령을 표시 하 고 CFO 계정에 대해 생성 된 암호를 확인 하 여 안전한 위치에 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-124">From the display of the **New-MsolUser** command, note the generated password for the CFO account and record it in a safe location.</span></span>
  
<span data-ttu-id="97586-125">Windows PowerShell 프롬프트에 대한 Microsoft Azure Active Directory 모듈에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-125">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "coo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "COO" -FirstName "Chief" -LastName "Operations Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

<span data-ttu-id="97586-126">**Get-msoluser** 명령을 표시할 때 coo 계정에 대해 생성 된 암호를 확인 하 고 안전한 위치에 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-126">From the display of the **New-MsolUser** command, note the generated password for the COO account and record it in a safe location.</span></span>
  
<span data-ttu-id="97586-127">다음으로, 비공개 임원 그룹을 만들고 새 executive 계정을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-127">Next, you create a private Executives group and add the new executive accounts to it.</span></span>
  
1. <span data-ttu-id="97586-128">브라우저에서 Office 포털로 이동 [http://admin.microsoft.com](http://admin.microsoft.com) 하 여 전역 관리자 계정을 사용 하 여 office 365 평가판 구독에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-128">In your browser, go to the Office portal at [http://admin.microsoft.com](http://admin.microsoft.com) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
  - <span data-ttu-id="97586-129">경량 Office 365 개발/테스트 환경을 사용 하는 경우 Internet Explorer 또는 브라우저의 개인 세션을 열고 로컬 컴퓨터에서 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-129">If you are using the lightweight Office 365 dev/test environment, open a private session of Internet Explorer or your browser and sign in from your local computer.</span></span>
    
  - <span data-ttu-id="97586-130">시뮬레이트된 enterprise Office 365 개발/테스트 환경을 사용 하는 경우 Azure portal을 사용 하 여 CLIENT1 가상 컴퓨터에 연결한 다음, CLIENT1에서 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-130">If you are using the simulated enterprise Office 365 dev/test environment, use the Azure portal to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="97586-131">**Microsoft Office 홈** 탭에서 **Admin _GT_ groups > groups**를 클릭 한 다음 **그룹 추가**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-131">On the **Microsoft Office Home** tab, click **Admin > Groups > Groups**, and then click **Add a group**.</span></span>
    
3. <span data-ttu-id="97586-132">**그룹 추가**에서 그룹 유형에 대해 **Office 365 그룹** 을 선택 하 고 **이름** 및 **그룹 Id**에 **임원** 을 입력 한 다음 \*\*\*\* 개인 **정보 보호**를 선택 하 고 **소유자 선택을**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-132">In **Add a group**, select **Office 365 group** for the group type, type **Executives** in **Name** and **Group Id**, select **Private** for **Privacy**, and then click **Select Owner**.</span></span>
    
4. <span data-ttu-id="97586-133">목록에서 전역 관리자 계정 이름을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-133">In the list, click your global administrator account name.</span></span>
    
5. <span data-ttu-id="97586-134">**추가**를 클릭한 다음 **닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-134">Click **Add**, and then click **Close**.</span></span>
    
6. <span data-ttu-id="97586-135">그룹 목록에서 **임원**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-135">In the groups list, click **Executives**.</span></span>
    
7. <span data-ttu-id="97586-136">**구성원에 대해 편집을**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-136">Click **Edit for Members**.</span></span>
    
8. <span data-ttu-id="97586-137">**구성원 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-137">Click **Add members**.</span></span> <span data-ttu-id="97586-138">구성원 목록에서 다음 사용자 계정을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-138">In the member list, select the following user accounts:</span></span>
    
  - <span data-ttu-id="97586-139">경영 최고 책임자</span><span class="sxs-lookup"><span data-stu-id="97586-139">Chief Executive Officer</span></span>
    
  - <span data-ttu-id="97586-140">최고 회계 담당자</span><span class="sxs-lookup"><span data-stu-id="97586-140">Chief Financial Officer</span></span>
    
  - <span data-ttu-id="97586-141">운영 책임자 최고</span><span class="sxs-lookup"><span data-stu-id="97586-141">Chief Operations Officer</span></span>
    
9. <span data-ttu-id="97586-142">**저장**을 클릭 하 고 **닫기를**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-142">Click **Save**, and then click **Close**.</span></span>
    
10. <span data-ttu-id="97586-143">**Office 관리 센터** 탭을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="97586-143">Close the **Office Admin center** tab.</span></span>
    
<span data-ttu-id="97586-144">다음에는 임원 사이트 모음을 만들고 중역 그룹의 구성원만 액세스할 수 있도록 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-144">Next, you create an Executives site collection and allow just the members of the Executives group to access it.</span></span>
  
1. <span data-ttu-id="97586-145">**Microsoft Office 홈** 탭에서 **관리** 타일을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-145">On the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
2. <span data-ttu-id="97586-146">**Office 관리 센터** 탭에서 **관리 센터 > SharePoint**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-146">On the **Office Admin center** tab, click **Admin centers > SharePoint**.</span></span>
    
3. <span data-ttu-id="97586-147">**SharePoint 관리 센터** 탭에서 **새 > 개인 사이트 모음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-147">On the **SharePoint admin center** tab, click **New > Private site collection**.</span></span>
    
4. <span data-ttu-id="97586-148">새 사이트 모음 창에서 **제목**에 **임원** , URL 상자에 임원을 차례로 입력 하 고 **관리자**에 게 전역 관리자 계정의 이름을 지정한 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-148">In the new site collection pane, type **Executives** in **Title**, executives in the URL box, specify the name of your global administrator account in **Administrator**, and then click **OK**.</span></span>
    
5. <span data-ttu-id="97586-149">새 사이트 모음을 만들 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="97586-149">Wait until the new site collection has been created.</span></span> <span data-ttu-id="97586-150">완료 되 면 새 임원 사이트 모음의 URL을 복사 하 여 브라우저의 새 탭에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="97586-150">When complete, copy the URL of the new Executives site collection and paste it into a new tab of your browser.</span></span>
    
6. <span data-ttu-id="97586-151">**임원** 사이트 모음의 오른쪽 위에 있는 설정 아이콘을 클릭 한 다음 **공유를**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-151">In the upper right of the **Executives** site collection, click the settings icon, and then click **Shared with**.</span></span>
    
7. <span data-ttu-id="97586-152">**' 임원 ' 공유**에서 **고급**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-152">In **Share 'Executives'**, click **Advanced**.</span></span>
    
8. <span data-ttu-id="97586-153">SharePoint 그룹 목록에서 **임원 구성원**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-153">In the list of SharePoint groups, click **Executives Members**.</span></span>
    
9. <span data-ttu-id="97586-154">**사용자 및 그룹** 페이지에서 **새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-154">On the **People and Groups** page, click **New**.</span></span>
    
10. <span data-ttu-id="97586-155">**' 임원 ' 공유**에 **임원**을 입력 하 고 **임원** 그룹을 클릭 한 다음 **공유**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-155">In **Share 'Executives'**, type **Executives**, click the **Executives** group, and then click **Share**.</span></span>
    
11. <span data-ttu-id="97586-156">**사용자 및 그룹** 탭을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="97586-156">Close the **People and groups** tab.</span></span>
    
<span data-ttu-id="97586-157">다음으로, 모든 사용자가 Sales 사이트 모음에 액세스할 수 있도록 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-157">Next, you allow everyone to access the Sales site collection.</span></span>
  
1. <span data-ttu-id="97586-158">**SharePoint 관리 센터** 탭에서 Sales 사이트 모음의 URL을 복사 하 여 브라우저의 새 탭에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="97586-158">From the **SharePoint admin center** tab, copy the URL of the Sales site collection and paste it into a new tab of your browser..</span></span>
    
2. <span data-ttu-id="97586-159">오른쪽 위에 있는 설정 아이콘을 클릭 한 다음 **공유를**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-159">In the upper right, click the settings icon, and then click **Shared with**.</span></span>
    
3. <span data-ttu-id="97586-160">**공유 ' 판매 사이트 모음 '** 에서 **고급**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-160">In **Share 'Sales site collection'**, click **Advanced**.</span></span>
    
4. <span data-ttu-id="97586-161">SharePoint 그룹 목록에서 **판매 사이트 모음 구성원**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-161">In the list of SharePoint groups, click **Sales site collection Members**.</span></span>
    
5. <span data-ttu-id="97586-162">**사용자 및 그룹** 페이지에서 **새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-162">On the **People and Groups** page, click **New**.</span></span>
    
6. <span data-ttu-id="97586-163">**' 판매 사이트 모음 ' 공유**에 **모든 사람**을 입력 하 고 **외부 사용자를 제외한 모든 사람**을 클릭 한 다음 **공유**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-163">In **Share 'Sales site collection'**, type **Everyone**, click **Everyone except external users**, and then click **Share**.</span></span>
    
7. <span data-ttu-id="97586-164">**Sales 사이트 모음** 및 **SharePoint** 탭을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="97586-164">Close the **Sales site collection** and **SharePoint** tabs.</span></span>
    
<span data-ttu-id="97586-165">다음으로 중역 계정으로 로그인 하 고 임원 사이트 모음에 문서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="97586-165">Next, you sign in with an executive account and create a document in the Executives site collection.</span></span>
  
1. <span data-ttu-id="97586-166">**Microsoft Office 홈** 탭의 오른쪽 위에 있는 사용자 아이콘을 클릭 한 다음 **로그 아웃**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-166">On the **Microsoft Office Home** tab, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="97586-167">[http://admin.microsoft.com](http://admin.microsoft.com)으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-167">Go to [http://admin.microsoft.com](http://admin.microsoft.com).</span></span>
    
3. <span data-ttu-id="97586-168">**Office 365 로그인** 페이지에서 **다른 계정 사용**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-168">On the **Office 365 sign in** page, click **Use another account**.</span></span>
    
4. <span data-ttu-id="97586-169">**CEO** 계정 이름 및 암호를 입력 하 고 **로그인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-169">Type the **CEO** account name and its password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="97586-170">브라우저의 새 탭에서 임원 사이트 모음 ( **https://**\<조직 name>**. sharepoint.com/sites/executives**)에 대 한 URL을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-170">On a new tab of your browser, type the URL to the Executives site collection ( **https://**\<organization name>**.sharepoint.com/sites/executives**).</span></span>
    
6. <span data-ttu-id="97586-171">**문서**를 클릭 하 고 **새로 만들기를** 클릭 한 다음 **Word 문서**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-171">Click **Documents**, click **New,** and then click **Word Document**.</span></span>
    
7. <span data-ttu-id="97586-172">제목 표시줄을 클릭 하 고 **SensitiveData-BeforeIRM**를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-172">Click in the title bar and type **SensitiveData-BeforeIRM**.</span></span>
    
8. <span data-ttu-id="97586-173">문서 본문을 클릭 하 고 **최신 보드 회의에서 의사록**을 입력 한 다음 **중역**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-173">Click in the document body and type **Minutes from the latest board meeting**, and then click **Executives**.</span></span>
    
     <span data-ttu-id="97586-174">**문서** 폴더에 **SensitiveData-BeforeIRM** 가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="97586-174">You should see **SensitiveData-BeforeIRM.docx** in the **Documents** folder.</span></span>
    
<span data-ttu-id="97586-175">다음으로, SensitiveData-BeforeIRM의 로컬 복사본을 다운로드 한 후 실수로 판매 사이트 모음에 게시 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-175">Next, you download a local copy of the SensitiveData-BeforeIRM.docx document and then accidentally post it to the Sales site collection.</span></span>
  
1. <span data-ttu-id="97586-176">로컬 컴퓨터에서 새 폴더를 만듭니다 (예를 들어, C:\\tlgs\\SensitiveDataTestFiles).</span><span class="sxs-lookup"><span data-stu-id="97586-176">On your local computer, create a new folder (for example, C:\\TLGs\\SensitiveDataTestFiles).</span></span>
    
2. <span data-ttu-id="97586-177">브라우저의 **문서** 탭에서 **SensitiveData-BeforeIRM** 문서를 선택 하 고 줄임표를 클릭 한 다음 **다운로드**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-177">On the **Documents** tab of your browser, select the **SensitiveData-BeforeIRM.docx** document, click the ellipses, and then click **Download**.</span></span>
    
3. <span data-ttu-id="97586-178">1 단계에서 만든 폴더에 **SensitiveData-BeforeIRM** 문서를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-178">Store the **SensitiveData-BeforeIRM.docx** document in the folder created in step 1.</span></span>
    
4. <span data-ttu-id="97586-179">브라우저의 새 탭에서 Sales site collection ( **https://**\<조직 name>**. sharepoint.com/sites/sales**)의 URL을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-179">On a new tab of your browser, type the URL to the Sales site collection ( **https://**\<organization name>**.sharepoint.com/sites/sales**).</span></span>
    
5. <span data-ttu-id="97586-180">**Sales 사이트 모음의** **문서** 폴더를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-180">Click the **Documents** folder of the **Sales site collection**.</span></span>
    
6. <span data-ttu-id="97586-181">**업로드**를 클릭 하 고 1 단계에서 만든 폴더에 **SensitiveData-BeforeIRM** 문서를 지정한 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-181">Click **Upload**, and then specify **SensitiveData-BeforeIRM.docx** document in the folder created in step 1, and then click **OK**.</span></span>
    
7. <span data-ttu-id="97586-182">**SensitiveData-BeforeIRM** 문서가 **문서** 폴더에 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-182">Verify that the **SensitiveData-BeforeIRM.docx** document is in the **Documents** folder.</span></span>
    
8. <span data-ttu-id="97586-183">**영업** 및 **SharePoint** 탭을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="97586-183">Close the **Sales** and **SharePoint** tabs.</span></span>
    
<span data-ttu-id="97586-184">다음에는 User5으로 로그인 하 고 Sales site collection에서 SensitiveData-BeforeIRM 문서를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="97586-184">Next, you sign in as User5 and try to open the SensitiveData-BeforeIRM.docx document in the Sales site collection.</span></span>
  
1. <span data-ttu-id="97586-185">**Microsoft Office 홈** 탭의 오른쪽 위에 있는 사용자 아이콘을 클릭 한 다음 **로그 아웃**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-185">On the **Microsoft Office Home** tab, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="97586-186">[http://admin.microsoft.com](http://admin.microsoft.com)으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-186">Go to [http://admin.microsoft.com](http://admin.microsoft.com).</span></span>
    
3. <span data-ttu-id="97586-187">**Office 365 로그인** 페이지에서 **다른 계정 사용**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-187">On the **Office 365 sign in** page, click **Use another account**.</span></span>
    
4. <span data-ttu-id="97586-188">User5 계정 이름 및 암호를 입력 한 다음 **로그인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-188">Type the User5 account name and its password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="97586-189">브라우저의 새 탭에서 판매 사이트 모음의 URL을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-189">On a new tab of your browser, type the URL to the Sales site collection.</span></span>
    
6. <span data-ttu-id="97586-190">**영업 사이트 모음의** **문서** 폴더에서 **SensitiveData-BeforeIRM** 문서를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-190">In the **Documents** folder of the **Sales site collection**, click the **SensitiveData-BeforeIRM.docx** document.</span></span>
    
    <span data-ttu-id="97586-191">해당 콘텐츠가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="97586-191">You should see its contents.</span></span>
    
7. <span data-ttu-id="97586-192">**문서** 및 **판매 사이트 모음** 탭을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="97586-192">Close the **Documents** and **Sales site collection** tabs.</span></span>
    
<span data-ttu-id="97586-193">실수로 영업 사이트 모음에 SensitiveData-BeforeIRM 문서를 게시 하면 CEO가 임원 사이트 모음의 사용 권한 보안을 무시 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-193">By accidentally posting the SensitiveData-BeforeIRM.docx document on the Sales site collection, the CEO bypassed the permissions security of the Executives site collection.</span></span>
  
<span data-ttu-id="97586-194">3 ~ 4 단계에 대해 Office 365을 준비 하려면 SharePoint Online에 대해 IRM을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-194">To prepare Office 365 for Phases 3 and 4, enable IRM for SharePoint Online.</span></span>
  
1. <span data-ttu-id="97586-195">**Microsoft Office 홈** 탭의 오른쪽 위에 있는 사용자 아이콘을 클릭 한 다음 **로그 아웃**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-195">On the **Microsoft Office Home** tab, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="97586-196">[http://admin.microsoft.com](http://admin.microsoft.com)으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-196">Go to [http://admin.microsoft.com](http://admin.microsoft.com).</span></span>
    
3. <span data-ttu-id="97586-197">**Office 365 로그인** 페이지에서 전역 관리자 계정 이름을 클릭 하 고 암호를 입력 한 다음 **로그인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-197">On the **Office 365 sign in** page, click the global administrator account name, type its password, and then click **Sign in**.</span></span>
    
4. <span data-ttu-id="97586-198">**Microsoft Office 홈** 탭에서 **admin > 관리 센터 > SharePoint**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-198">On the **Microsoft Office Home** tab, click **Admin > Admin centers > SharePoint**.</span></span>
    
5. <span data-ttu-id="97586-199">**SharePoint 관리 센터** 탭에서 **설정을**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-199">On the **SharePoint admin center** tab, click **Settings**.</span></span>
    
6. <span data-ttu-id="97586-200">페이지의 **IRM (정보 권한 관리** ) 섹션에서 **구성에 지정 된 IRM 서비스 사용**을 선택 하 고 **IRM 설정 새로 고침**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-200">On the page, in the **Information Rights Management (IRM)** section, select **Use the IRM service specified in your configuration**, and then select **Refresh IRM Settings**.</span></span>
    
7. <span data-ttu-id="97586-201">**SharePoint 관리 센터** 탭을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="97586-201">Close the **SharePoint admin center** tab.</span></span>
    
## <a name="phase-3-use-sharepoint-information-rights-management-with-an-office-365-private-group"></a><span data-ttu-id="97586-202">3 단계: Office 365 전용 그룹에서 SharePoint 정보 권한 관리 사용</span><span class="sxs-lookup"><span data-stu-id="97586-202">Phase 3: Use SharePoint Information Rights Management with an Office 365 private group</span></span>

<span data-ttu-id="97586-203">이 단계에서는 Office 365 전용 그룹의 SharePoint 정보 권한 관리를 사용 하 여 문서에 대 한 액세스 권한이 열려 있는 사이트에 게시 된 경우에도 해당 정보를 보호 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-203">In this phase, you use SharePoint Information Rights Management with an Office 365 private group to protect access to a document with sensitive information, even when it is posted on a site with open permissions.</span></span>
  
<span data-ttu-id="97586-204">먼저, 임원 사이트 모음의 문서 라이브러리에 대해 IRM을 사용 하도록 설정 하 고 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-204">First, you enable and configure IRM for the documents library of the Executives site collection.</span></span> 
  
1. <span data-ttu-id="97586-205">브라우저의 새 탭에서 임원 사이트 모음의 URL을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-205">On a new tab of your browser, type the URL to the Executives site collection.</span></span>
    
2. <span data-ttu-id="97586-206">**문서**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-206">Click **Documents**.</span></span>
    
3. <span data-ttu-id="97586-207">오른쪽 위에서 설정 아이콘을 클릭 한 다음 **라이브러리 설정을**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-207">In the upper-right, click the settings icon, and then click **Library settings**.</span></span>
    
4. <span data-ttu-id="97586-208">**설정** 페이지의 **사용 권한 및 관리**에서 **정보 권한 관리**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-208">On the **Settings** page, under **Permissions and Management**, click **Information Rights Management**.</span></span>
    
5. <span data-ttu-id="97586-209">**정보 권한 관리 설정** 페이지에서 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-209">On the **Information Rights Management Settings** page:</span></span>
    
  - <span data-ttu-id="97586-210">**다운로드 시이 라이브러리의 문서에 대 한 사용 권한 제한을**선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-210">Select **Restrict permission to documents in this library on download**.</span></span>
    
  - <span data-ttu-id="97586-211">**권한 정책 제목 만들기**에 대해 **임원**을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-211">For **Create a permission policy title**, type **Executives**.</span></span>
    
  - <span data-ttu-id="97586-212">**권한 정책 설명 추가**에 대해 **임원에 IRM**을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-212">For **Add a permission policy description**, type **IRM for executives**.</span></span>
    
6. <span data-ttu-id="97586-213">**옵션 표시**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-213">Click **Show Options**.</span></span>
    
7. <span data-ttu-id="97586-214">**추가 irm 라이브러리 설정 설정**에서 irm을 **지원 하지 않는 문서를 사용자가 업로드 하도록 허용**안 함을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-214">Under **Set additional IRM library settings**, select **Do not allow users to upload documents that do not support IRM**.</span></span>
    
8. <span data-ttu-id="97586-215">**문서 액세스 권한 구성**에서 보기 **허용** 을 선택 하 고 **다운로드 한 문서 복사본에 보는 사람이 쓰기**저장을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-215">Under **Configure document access rights**, select **Allow viewers to print** and **Allow viewers to write on a copy of the downloaded document**.</span></span>
    
9. <span data-ttu-id="97586-216">**그룹 보호 및 자격 증명 간격 설정**에서 **그룹 보호 허용을 선택 합니다. 기본 그룹**을 선택한 다음 **임원**을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-216">Under **Set group protection and credentials interval**, select **Allow group protection. Default group**, and then type **Executives**.</span></span>
    
10. <span data-ttu-id="97586-217">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-217">Click **OK**.</span></span>
    
<span data-ttu-id="97586-218">다음으로, CEO 역할을 하 여 임원 문서 폴더에 새 문서를 업로드 하 고 다운로드 한 다음 판매 문서 폴더에 실수로 업로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-218">Next, acting as the CEO, you upload a new document to the Executives document folder, download it, then accidentally upload it to the Sales document folder.</span></span>
  
1. <span data-ttu-id="97586-219">**SensitiveData-BeforeIRM** 문서를 저장 한 로컬 폴더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="97586-219">Open the local folder where you stored the **SensitiveData-BeforeIRM.docx** document.</span></span>
    
2. <span data-ttu-id="97586-220">**SensitiveData-BeforeIRM**를 마우스 오른쪽 단추로 클릭 한 다음 **복사**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-220">Right-click **SensitiveData-BeforeIRM.docx**, and then click **Copy**.</span></span>
    
3. <span data-ttu-id="97586-221">폴더 내에서 마우스 오른쪽 단추를 클릭 하 고 **붙여넣기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-221">Right-click within the folder, and then click **Paste**.</span></span>
    
4. <span data-ttu-id="97586-222">새 **SensitiveData** 파일의 이름을 **SensitiveData-AfterIRM**로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="97586-222">Rename the new **SensitiveData-BeforeIRM - Copy.docx** file to **SensitiveData-AfterIRM.docx**.</span></span>
    
5. <span data-ttu-id="97586-223">브라우저의 **Microsoft Office 홈** 탭에서 오른쪽 위에 있는 사용자 아이콘을 클릭 한 다음 **로그 아웃**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-223">From the **Microsoft Office Home** tab in your browser, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
6. <span data-ttu-id="97586-224">[http://admin.microsoft.com](http://admin.microsoft.com)으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-224">Go to [http://admin.microsoft.com](http://admin.microsoft.com).</span></span>
    
7. <span data-ttu-id="97586-225">**Office 365 로그인** 페이지에서 CEO 계정 이름을 클릭 하 고 암호를 입력 한 다음 **로그인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-225">On the **Office 365 sign in** page, click the CEO account name, type its password, and then click **Sign in**.</span></span>
    
8. <span data-ttu-id="97586-226">브라우저의 새 탭에서 임원 사이트 모음의 URL을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-226">On a new tab of your browser, type the URL to the Executives site collection.</span></span>
    
9. <span data-ttu-id="97586-227">**문서** 페이지에서 **업로드**를 클릭 하 고 로컬 폴더에 **SensitiveData-AfterIRM** 문서를 지정한 다음 **열기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-227">On the **Documents** page, click **Upload**, specify the **SensitiveData-AfterIRM.docx** document in your local folder, and then click **Open**.</span></span>
    
10. <span data-ttu-id="97586-228">**문서** 페이지에서 새 **SensitiveData-AfterIRM** 문서를 선택 하 고 메뉴 모음에서 줄임표 (...)를 클릭 한 다음 **다운로드**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-228">Select the new **SensitiveData-AfterIRM.docx** document in the **Documents** page, click the ellipsis (…) in the menu bar, and then click **Download**.</span></span>
    
11. <span data-ttu-id="97586-229">메시지가 표시 되 면 로컬 폴더에 **SensitiveData-AfterIRM** 문서를 저장 하 고 원본 버전을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="97586-229">When prompted, save the **SensitiveData-AfterIRM.docx** document in your local folder, overwriting the original version.</span></span>
    
12. <span data-ttu-id="97586-230">**문서** 페이지에 대 한 탭을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="97586-230">Close the tab for the **Documents** page.</span></span>
    
13. <span data-ttu-id="97586-231">브라우저의 새 탭에서 판매 사이트 모음의 URL을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-231">On a new tab of your browser, type the URL to the Sales site collection.</span></span>
    
14. <span data-ttu-id="97586-232">**문서**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-232">Click **Documents**.</span></span>
    
15. <span data-ttu-id="97586-233">**문서** 페이지에서 **업로드**를 클릭 하 고 로컬 폴더에 **SensitiveData-AfterIRM** 문서를 지정한 다음 **열기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-233">On the **Documents** page, click **Upload**, specify the **SensitiveData-AfterIRM.docx** document in your local folder, and then click **Open**.</span></span>
    
16. <span data-ttu-id="97586-234">**Sales 사이트 모음** 및 **SharePoint** 탭을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="97586-234">Close the **Sales site collection** and **SharePoint** tabs.</span></span>
    
<span data-ttu-id="97586-235">다음으로, 일반 사용자 역할을 하 고 영업 문서 폴더의 **SensitiveData-AfterIRM** 문서에 액세스 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-235">Next, acting as a normal user, you try to access the **SensitiveData-AfterIRM.docx** document in the Sales document folder.</span></span>
  
1. <span data-ttu-id="97586-236">브라우저의 **Microsoft Office 홈** 탭에서 오른쪽 위에 있는 사용자 아이콘을 클릭 한 다음 **로그 아웃**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-236">From the **Microsoft Office Home** tab in your browser, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="97586-237">[http://admin.microsoft.com](http://admin.microsoft.com)으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-237">Go to [http://admin.microsoft.com](http://admin.microsoft.com).</span></span>
    
3. <span data-ttu-id="97586-238">**Office 365 로그인** 페이지에서 User5 계정 이름을 클릭 하 고 암호를 입력 한 다음 **로그인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-238">On the **Office 365 sign in** page, click the User5 account name, type its password, and then click **Sign in**.</span></span>
    
4. <span data-ttu-id="97586-239">브라우저의 새 탭에서 판매 사이트 모음의 URL을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-239">On a new tab of your browser, type the URL to the Sales site collection.</span></span>
    
5. <span data-ttu-id="97586-240">**문서**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-240">Click **Documents**.</span></span>
    
6. <span data-ttu-id="97586-241">**문서** 페이지에서 **SensitiveData-AfterIRM** 문서를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="97586-241">On the **Documents** page, open the **SensitiveData-AfterIRM.docx** document.</span></span>
    
    <span data-ttu-id="97586-242">"죄송 하지만이 문서는 IRM (정보 권한 관리)으로 보호 되어 있어 Word Online에서 열 수 없습니다." 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="97586-242">You should see a message that states "Sorry, Word Online can't open this document because it's protected by Information Rights Management (IRM)."</span></span> 
    
7. <span data-ttu-id="97586-243">**Word에서 편집을**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-243">Click **Edit in Word**.</span></span> <span data-ttu-id="97586-244">파일을 열 것인지 묻는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="97586-244">You are prompted if you want to open the file.</span></span> <span data-ttu-id="97586-245">**예**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-245">Click **Yes**.</span></span>
    
8. <span data-ttu-id="97586-246">로그인 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="97586-246">You are prompted to sign-in.</span></span> <span data-ttu-id="97586-247">User5 계정의 계정 이름을 입력 하 고 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-247">Type the account name of the User5 account, and then click **Next**.</span></span>
    
9. <span data-ttu-id="97586-248">암호를 입력 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="97586-248">You are prompted to provide the password.</span></span> <span data-ttu-id="97586-249">User5 계정의 암호를 입력 하 고 **로그인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-249">Type the password for the User5 account and then click **Sign in**.</span></span> 
    
    <span data-ttu-id="97586-250">"이 문서를 열 수 있는 자격 증명을가지고 있지 않습니다." 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="97586-250">You should see the a message that states: "You do not have the credentials that allow you to open this document."</span></span>
    
10. <span data-ttu-id="97586-251">**아니요**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-251">Click **No**.</span></span>
    
<span data-ttu-id="97586-252">IRM 보호를 확인 하는 또 다른 방법은 로컬 폴더의 파일을 확인 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="97586-252">Another way to see the IRM protection is to look at the files in your local folder.</span></span> <span data-ttu-id="97586-253">**SensitiveData-AfterIRM** 는 **SensitiveData-BeforeIRM** 파일 보다 훨씬 커야 합니다.</span><span class="sxs-lookup"><span data-stu-id="97586-253">The **SensitiveData-AfterIRM.docx** should be much larger than the **SensitiveData-BeforeIRM.docx** file.</span></span> <span data-ttu-id="97586-254">**SensitiveData-AfterIRM** 파일은 암호화 되며 IRM 보호 정보가 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="97586-254">The **SensitiveData-AfterIRM.docx** file is encrypted and has the IRM protection information added to it.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="97586-255">참고 항목</span><span class="sxs-lookup"><span data-stu-id="97586-255">See Also</span></span>

[<span data-ttu-id="97586-256">클라우드 도입 TLG(테스트 랩 가이드)</span><span class="sxs-lookup"><span data-stu-id="97586-256">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="97586-257">기본 구성 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="97586-257">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="97586-258">Office 365 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="97586-258">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="97586-259">클라우드 도입 및 하이브리드 솔루션</span><span class="sxs-lookup"><span data-stu-id="97586-259">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)


