---
title: "격리 된 SharePoint Online 팀 사이트 개발/테스트 환경"
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
ms.assetid: d1795031-beef-49ea-a6fc-5da5450d320d
description: "요약: Office 365 개발/테스트 환경에서 조직의 나머지 부분에서 격리 된 SharePoint Online 팀 사이트를 구성 합니다."
ms.openlocfilehash: 997c5cf236a795f4846718cc8864997799a1d966
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/09/2018
---
# <a name="isolated-sharepoint-online-team-site-devtest-environment"></a><span data-ttu-id="7ad09-103">격리 된 SharePoint Online 팀 사이트 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="7ad09-103">Isolated SharePoint Online team site dev/test environment</span></span>

 <span data-ttu-id="7ad09-104">**요약:** Office 365 개발/테스트 환경에서 조직의 나머지 부분에서 분리 되는 SharePoint Online 팀 사이트를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-104">**Summary:** Configure a SharePoint Online team site that is isolated from the rest of the organization in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="7ad09-p101">Office 365의 SharePoint Online 팀 사이트는 일반적인 문서 라이브러리, OneNote 전자 필기장 및 기타 서비스를 사용 하 여 공동 작업에 대 한 위치입니다. 대부분의 경우에서 원하는 전체 액세스 및 공동 작업 부서 또는 조직 전체에서 합니다. 그러나 일부 경우에 조밀 하 게 제어 하려는 액세스 및 공동 작업이 용이해 집니다 소규모 사용자에 대 한 사용 권한입니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-p101">SharePoint Online team sites in Office 365 are locations for collaboration using a common document library, a OneNote notebook, and other services. In many cases, you want wide access and collaboration across departments or organizations. However, in some cases, you want to tightly control the access and permissions for collaboration among a small group of people.</span></span>
  
<span data-ttu-id="7ad09-p102">SharePoint Online 팀 사이트 및 사용자가 수행할 수 있는 작업에 대 한 액세스는 SharePoint 그룹 및 권한 수준을 통해 제어 됩니다. 기본적으로 SharePoint Online 사이트에 있는 세가지 수준의 액세스:</span><span class="sxs-lookup"><span data-stu-id="7ad09-p102">Access to SharePoint Online team sites and what users can do is controlled by SharePoint groups and permission levels. By default, SharePoint Online sites have three levels of access:</span></span>
  
- <span data-ttu-id="7ad09-110">**구성원**보기, 작성 및 사이트에 있는 리소스를 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-110">**Members**, who can view, create, and modify resources on the site.</span></span>
    
- <span data-ttu-id="7ad09-111">**소유자**는 사이트의 완벽 한 제어를 가진 사용 권한을 변경 하는 기능을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-111">**Owners**, who have complete control of the site, including the ability to change permissions.</span></span>
    
- <span data-ttu-id="7ad09-112">**방문자**만 사이트에서 리소스를 볼 수 있는 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-112">**Visitors**, who only can view resources on the site.</span></span>
    
<span data-ttu-id="7ad09-p103">이 문서의 단계 ProjectX 라는 비밀 리서치 프로젝트에 대해 격리 된 SharePoint Online 팀 사이트의 구성을 안내 합니다. 액세스 요구 사항을합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-p103">This article steps you through the configuration of an isolated SharePoint Online team site for a secret research project named ProjectX. The access requirements are:</span></span>
  
- <span data-ttu-id="7ad09-115">프로젝트의 구성원만 사이트 및 해당 콘텐츠(문서, OneNote 전자 필기장, 페이지)에 액세스할 수 있고, SharePoint 편집 및 보기 권한 수준은 그룹 구성원 자격을 통해 제어됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-115">Only members of the project can access the site and its contents (documents, OneNote Notebook, Pages), with edit and view SharePoint permission levels controlled through group membership.</span></span>
    
- <span data-ttu-id="7ad09-116">사이트의 사이트 작성자 및 관리자 그룹의 구성원만 사이트 수준 권한 수정을 비롯한 사이트 관리 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-116">Only the site creator and members of an Admins group for the site can perform site administration, which includes modifying site-level permissions.</span></span>
    
<span data-ttu-id="7ad09-117">Office 365 개발/테스트 환경에서 격리 된 SharePoint Online 팀 사이트를 설정 하는 세 단계로 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-117">There are three phases to setting up an isolated SharePoint Online team site in your Office 365 dev/test environment:</span></span>
  
1. <span data-ttu-id="7ad09-118">Office 365 개발/테스트 환경을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-118">Create the Office 365 dev/test environment.</span></span>
    
2. <span data-ttu-id="7ad09-119">ProjectX에 대한 사용자 및 그룹을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-119">Create the users and groups for ProjectX.</span></span>
    
3. <span data-ttu-id="7ad09-120">새 ProjectX SharePoint Online 팀 사이트를 만들고 발견 하면 격리 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-120">Create a new ProjectX SharePoint Online team site and isolate it.</span></span>
    
> [!TIP]
> <span data-ttu-id="7ad09-121">클릭 [여기](http://aka.ms/catlgstack) 에 한 맵이 하나의 Microsoft 클라우드 테스트 랩 가이드 스택의 모든 문서를 시각적으로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-121">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="7ad09-122">1단계: 경량 또는 시뮬레이트된 엔터프라이즈 Office 365 개발/테스트 환경을 구축합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-122">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="7ad09-123">최소 요구 사항을 경량 방식으로 격리 된 SharePoint Online 팀 사이트를 만들 하려면 2와 [Office 365 개발/테스트 환경](office-365-dev-test-environment.md)의 3 단계에서 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-123">If you just want to create an isolated SharePoint Online team site in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="7ad09-124">시뮬레이션 된 엔터프라이즈 구성에서 격리 된 SharePoint Online 팀 사이트를 만들려는 경우 [Office 365 개발/테스트 환경에 대 한 디렉터리 동기화](dirsync-for-your-office-365-dev-test-environment.md)의 지시를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-124">If you want to create an isolated SharePoint Online team site in a simulated enterprise configuration, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="7ad09-p104">격리된 SharePoint Online 사이트를 만들기 위해 시뮬레이트된 엔터프라이즈 개발/테스트 환경이 필요하지 않습니다. 해당 환경에는 Windows Server AD 포리스트의 디렉터리 동기화 및 인터넷에 연결된 시뮬레이트된 인트라넷이 포함되어 있습니다. 여기서는 옵션으로 제공되므로 격리된 SharePoint Online 사이트를 테스트하고 일반적인 조직을 나타내는 환경에서 실험할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-p104">Creating an isolated SharePoint Online site does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can test an isolated SharePoint Online site and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-create-user-accounts-and-access-groups"></a><span data-ttu-id="7ad09-127">2 단계: 사용자 계정 만들기 및 그룹에 액세스</span><span class="sxs-lookup"><span data-stu-id="7ad09-127">Phase 2: Create user accounts and access groups</span></span>

<span data-ttu-id="7ad09-128">[Office 365 PowerShell 연결](https://technet.microsoft.com/library/dn975125.aspx) 지침을 사용 하 여 Office 365 내역 구독에서 전역 관리자 계정으로 연결할 수 있습니다:</span><span class="sxs-lookup"><span data-stu-id="7ad09-128">Use the instructions in [Connect to Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) to connect to your Office 365 trail subscription with your global administrator account from:</span></span>
  
- <span data-ttu-id="7ad09-129">사용하는 컴퓨터(경량 Office 365 개발/테스트 환경)</span><span class="sxs-lookup"><span data-stu-id="7ad09-129">Your computer (for the lightweight Office 365 dev/test environment).</span></span>
    
- <span data-ttu-id="7ad09-130">(시뮬레이션 된 엔터프라이즈 Office 365 개발/테스트 환경)에 대 한 CLIENT1 가상 컴퓨터로 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-130">The CLIENT1 virtual machine (for the simulated enterprise Office 365 dev/test environment).</span></span>
    
<span data-ttu-id="7ad09-131">ProjectX SharePoint Online 팀 사이트에 대 한 새 액세스 그룹을 만들려면 Windows Azure Active Directory 모듈에 대 한 Windows PowerShell 프롬프트에서 다음이 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-131">To create the new access groups for the ProjectX SharePoint Online team site, run these commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$groupName="ProjectX-Members"
$groupDesc="People allowed to collaborate for ProjectX."
New-MsolGroup -DisplayName $groupName -Description $groupDesc
$groupName="ProjectX-Admins"
$groupDesc="People allowed to administer SharePoint for ProjectX."
New-MsolGroup -DisplayName $groupName -Description $groupDesc
$groupName="ProjectX-Viewers"
$groupDesc="People allowed to view the SharePoint resources for ProjectX."
New-MsolGroup -DisplayName $groupName -Description $groupDesc
```

> [!TIP]
> <span data-ttu-id="7ad09-132">클릭 [여기](https://gallery.technet.microsoft.com/PowerShell-commands-for-an-b2608df1) 모든이 문서의 PowerShell 명령을 포함 하는 텍스트 파일에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-132">Click [here](https://gallery.technet.microsoft.com/PowerShell-commands-for-an-b2608df1) for a text file that contains all of the PowerShell commands in this article.</span></span>
  
<span data-ttu-id="7ad09-133">조직 이름(예: contosotoycompany), 위치에 대한 2자리 국가 코드를 입력한 후 Windows PowerShell 프롬프트에 대한 Microsoft Azure Active Directory 모듈에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-133">Fill in your organization name (example: contosotoycompany), the two-character country code for your location, and then run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "designer@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "Lead Designer" -FirstName Lead -LastName Designer -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment -ForceChangePassword $false
```

<span data-ttu-id="7ad09-134">**New-msoluser** 명령의 디스플레이에서 디자이너 잠재 고객 계정에 대해 생성 된 암호를 확인 하 고 안전한 위치에 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-134">From the display of the **New-MsolUser** command, note the generated password for the Lead Designer account and record it in a safe location.</span></span>
  
<span data-ttu-id="7ad09-135">Windows PowerShell 프롬프트에 대한 Microsoft Azure Active Directory 모듈에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-135">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "researcher@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "Lead Researcher" -FirstName Lead -LastName Researcher -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment -ForceChangePassword $false
```

<span data-ttu-id="7ad09-136">**New-msoluser** 명령의 디스플레이에서 잠재 고객 연구원 계정에 대해 생성 된 암호를 확인 하 고 안전한 위치에 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-136">From the display of the **New-MsolUser** command, note the generated password for the Lead Researcher account and record it in a safe location.</span></span>
  
<span data-ttu-id="7ad09-137">Windows PowerShell 프롬프트에 대한 Microsoft Azure Active Directory 모듈에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-137">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "devvp@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "Development VP" -FirstName Development -LastName VP -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment -ForceChangePassword $false
```

<span data-ttu-id="7ad09-138">**New-msoluser** 명령의 디스플레이에서 개발 VP 계정에 대해 생성 된 암호를 확인 하 고 안전한 위치에 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-138">From the display of the **New-MsolUser** command, note the generated password for the Development VP account and record it in a safe location.</span></span>
  
<span data-ttu-id="7ad09-139">다음으로 새 액세스 그룹에 새 계정을 추가 하려면 Windows Azure Active Directory 모듈에 대 한 Windows PowerShell 프롬프트에서 다음 PowerShell 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-139">Next, to add the new accounts to the new access groups, run these PowerShell commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$grpName="ProjectX-Members"
$userUPN="designer@" + $orgName + ".onmicrosoft.com"
Add-MsolGroupMember -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $grpName }).ObjectID -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupMemberType "User"
$userUPN="researcher@" + $orgName + ".onmicrosoft.com"
Add-MsolGroupMember -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $grpName }).ObjectID -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupMemberType "User"
$grpName="ProjectX-Admins"
Add-MsolGroupMember -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $grpName }).ObjectID -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userCredential.UserName }).ObjectID -GroupMemberType "User"
$grpName="ProjectX-Viewers"
$userUPN="devvp@" + $orgName + ".onmicrosoft.com"
Add-MsolGroupMember -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $grpName }).ObjectID -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupMemberType "User"
```

<span data-ttu-id="7ad09-140">결과:</span><span class="sxs-lookup"><span data-stu-id="7ad09-140">Results:</span></span>
  
- <span data-ttu-id="7ad09-141">ProjectX 멤버 액세스 그룹에는 포함 디자이너 잠재 고객 및 잠재 고객 연구원 사용자 계정</span><span class="sxs-lookup"><span data-stu-id="7ad09-141">The ProjectX-Members access group contains the Lead Designer and Lead Researcher user accounts</span></span>
    
- <span data-ttu-id="7ad09-142">ProjectX 관리자 액세스 그룹 평가판 구독에 대 한 전역 관리자 계정이 포함</span><span class="sxs-lookup"><span data-stu-id="7ad09-142">The ProjectX-Admins access group contains the global administrator account for your trial subscription</span></span>
    
- <span data-ttu-id="7ad09-143">ProjectX 뷰어 액세스 그룹에는 포함 개발 VP 사용자 계정</span><span class="sxs-lookup"><span data-stu-id="7ad09-143">The ProjectX-Viewers access group contains the Development VP user account</span></span>
    
<span data-ttu-id="7ad09-144">그림 1 액세스 그룹 및 그룹 구성원을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-144">Figure 1 shows the access groups and their membership.</span></span>
  
<span data-ttu-id="7ad09-145">**그림 1**</span><span class="sxs-lookup"><span data-stu-id="7ad09-145">**Figure 1**</span></span>

![Office 365 그룹 및 격리된 SharePoint Online 그룹 사이트에 대한 멤버 자격](images/5b7373b9-2a80-4880-afe5-63ffb17237e6.png)
  
## <a name="phase-3-create-a-new-projectx-sharepoint-online-team-site-and-isolate-it"></a><span data-ttu-id="7ad09-147">3 단계: 새 ProjectX SharePoint Online 팀 사이트를 만들고 발견 하면 격리</span><span class="sxs-lookup"><span data-stu-id="7ad09-147">Phase 3: Create a new ProjectX SharePoint Online team site and isolate it</span></span>

<span data-ttu-id="7ad09-148">ProjectX에 대 한 SharePoint Online 팀 사이트를 만들려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-148">To create a SharePoint Online team site for ProjectX, do the following:</span></span>
  
1. <span data-ttu-id="7ad09-149">브라우저를 사용 하는 중 하나에서 로컬 컴퓨터 (경량 구성) 또는 CLIENT1 (시뮬레이션 된 엔터프라이즈 구성) 전역 관리자 계정을 사용 하 여 Office 365 포털 ([https://portal.office.com](https://portal.office.com))에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-149">Using a browser on either your local computer (lightweight configuration) or on CLIENT1 (simulated enterprise configuration), sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using your global administrator account.</span></span>
    
2. <span data-ttu-id="7ad09-150">타일의 목록에서 **SharePoint**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-150">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="7ad09-151">브라우저에서 새 SharePoint 탭에서 **+ 사이트 만들기를**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-151">On the new SharePoint tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="7ad09-p105">**팀 사이트 이름** **ProjectX**를 입력 합니다. **개인 설정**선택 **개인-이 사이트에 액세스할 수 있는 구성원만**합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-p105">In **Team site name**, type **ProjectX**. In **Privacy settings**, select **Private - only members can access this site**.</span></span>
    
5. <span data-ttu-id="7ad09-154">**팀 사이트 설명** **ProjectX에 대 한 SharePoint 사이트**입력 하 고 ****을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-154">In **Team site description**, type **SharePoint site for ProjectX**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="7ad09-155">**가 수행 하려는 추가**에서? 창 **마침**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-155">On the **Who do you want to add**? pane, click **Finish**.</span></span>
    
7. <span data-ttu-id="7ad09-156">도구 모음에서 브라우저에서 새 **ProjectX 홈** 탭에서 설정 아이콘을 클릭 한 다음 **사이트 사용 권한**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-156">On the new **ProjectX-Home** tab in your browser, in the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
8. <span data-ttu-id="7ad09-157">**사이트 사용 권한** 창에서 **고급 사용 권한 설정**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-157">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
9. <span data-ttu-id="7ad09-158">새 **사용 권한: 프로젝트 X** 브라우저에서 탭, **액세스 요청 설정**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-158">In the new **Permissions: Project X** tab in your browser, click **Access Request Settings**.</span></span>
    
10. <span data-ttu-id="7ad09-159">**액세스 요청 설정** 대화 상자에서의 선택을 취소 **허용 구성원 사이트 및 개별 파일 및 폴더 공유** 및 **액세스 요청 허용** (되도록 세 확인란을 모두 선택 취소)를 한 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-159">In the **Access Requests Settings** dialog box, clear **Allow members to share the site and individual files and folders** and **Allow access requests** (so that all three check boxes are cleared), and then click **OK**.</span></span>
    
11. <span data-ttu-id="7ad09-160">목록에서 **ProjectX 구성원** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-160">Click **ProjectX Members** in the list.</span></span>
    
12. <span data-ttu-id="7ad09-161">**사용자 및 그룹** 페이지에서 **새로 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-161">On the **People and Groups** page, click **New**.</span></span>
    
13. <span data-ttu-id="7ad09-162">**공유** 대화 상자에서 입력 **ProjectX 구성원**을 선택한 다음 **공유**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-162">In the **Share** dialog box, type **ProjectX-Members**, select it, and then click **Share**.</span></span>
    
14. <span data-ttu-id="7ad09-163">브라우저에서 뒤로 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-163">Click the back button on your browser.</span></span>
    
15. <span data-ttu-id="7ad09-164">목록에서 **ProjectX 소유자** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-164">Click **ProjectX Owners** in the list.</span></span>
    
16. <span data-ttu-id="7ad09-165">**사용자 및 그룹** 페이지에서 **새로 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-165">On the **People and Groups** page, click **New**.</span></span>
    
17. <span data-ttu-id="7ad09-166">**공유** 대화 상자에서 입력 **ProjectX Admins**를 선택한 다음 **공유**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-166">In the **Share** dialog box, type **ProjectX-Admins**, select it, and then click **Share**.</span></span>
    
18. <span data-ttu-id="7ad09-167">브라우저에서 뒤로 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-167">Click the back button on your browser.</span></span>
    
19. <span data-ttu-id="7ad09-168">목록에서 **ProjectX 방문자** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-168">Click **ProjectX Visitors** in the list.</span></span>
    
20. <span data-ttu-id="7ad09-169">**사용자 및 그룹** 페이지에서 **새로 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-169">On the **People and Groups** page, click **New**.</span></span>
    
21. <span data-ttu-id="7ad09-170">**공유** 대화 상자에서 입력 **ProjectX 뷰어**를 선택한 다음 **공유**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-170">In the **Share** dialog box, type **ProjectX-Viewers**, select it, and then click **Share**.</span></span>
    
22. <span data-ttu-id="7ad09-171">브라우저에서 **사용자 및 그룹** 탭을 닫은 브라우저에서 **ProjectX 홈** 탭을 클릭 한 다음 **사이트 사용 권한** 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-171">Close the **People and Groups** tab in your browser, click the **ProjectX-Home** tab in your browser, and then close the **Site permissions** pane.</span></span>
    
<span data-ttu-id="7ad09-172">사용 권한 구성 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-172">Here are the results of configuring permissions:</span></span>
  
- <span data-ttu-id="7ad09-173">ProjectX Members SharePoint 그룹 (포함 하는 디자이너 잠재 고객 및 잠재 고객 연구원 사용자 계정만) ProjectX 구성원 액세스 그룹만 및 (포함 하는 전역 관리자 사용자 계정이) ProjectX 그룹을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-173">The ProjectX Members SharePoint group contains only the ProjectX-Members access group (which contains only the Lead Designer and Lead Researcher user accounts) and the ProjectX group (which contains only the global administrator user account).</span></span>
    
- <span data-ttu-id="7ad09-174">ProjectX Owners SharePoint 그룹 (포함 하는 전역 관리자 사용자 계정이) ProjectX 관리자 액세스 그룹만 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-174">The ProjectX Owners SharePoint group contains only the ProjectX-Admins access group (which contains only the global administrator user account).</span></span>
    
- <span data-ttu-id="7ad09-175">ProjectX 방문자 SharePoint 그룹 (포함 하는 개발 VP 사용자 계정만) ProjectX 뷰어 액세스 그룹만 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-175">The ProjectX Visitors SharePoint group contains only the ProjectX-Viewers access group (which contains only the Development VP user account).</span></span>
    
- <span data-ttu-id="7ad09-176">구성원은 사이트 수준 권한을 수정할 수 없습니다(이 작업은 ProjectX-Admins 그룹의 구성원만 수행할 수 있음).</span><span class="sxs-lookup"><span data-stu-id="7ad09-176">Members cannot modify site-level permissions (this can only be done by members of the ProjectX-Admins group).</span></span>
    
- <span data-ttu-id="7ad09-177">다른 사용자 계정은 사이트나 해당 리소스에 액세스할 수 없고 사이트에 대한 액세스를 요청할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-177">Other user accounts cannot access the site or its resources or request access to the site.</span></span>
    
<span data-ttu-id="7ad09-178">그림 2는 SharePoint 그룹 및 해당 그룹 구성원을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-178">Figure 2 shows the SharePoint groups and their membership.</span></span>
  
<span data-ttu-id="7ad09-179">**그림 2**</span><span class="sxs-lookup"><span data-stu-id="7ad09-179">**Figure 2**</span></span>

![SharePoint Online 그룹 및 격리된 SharePoint Online 그룹 사이트에 대한 멤버 자격](images/595abff4-64f9-49de-a37a-c70c6856936b.png)
  
<span data-ttu-id="7ad09-181">이제 잠재 고객 디자이너 사용자 계정을 사용 하 여 액세스를 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-181">Now let's demonstrate access using the Lead Designer user account:</span></span>
  
1. <span data-ttu-id="7ad09-182">**ProjectX 홈** 탭에서 브라우저를 닫은 다음 브라우저에서 **Microsoft Office Home** 탭을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-182">Close the **ProjectX-Home** tab in your browser, and then click the **Microsoft Office Home** tab in your browser.</span></span>
    
2. <span data-ttu-id="7ad09-183">전역 관리자의 이름을 클릭 한 다음 **로그 아웃**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-183">Click the name of your global administrator, and then click **Sign out**.</span></span>
    
3. <span data-ttu-id="7ad09-184">잠재 고객 디자이너 계정 이름과 암호를 사용 하 여 Office 365 포털 ([https://portal.office.com](https://portal.office.com))에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-184">Sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using the Lead Designer account name and its password.</span></span>
    
4. <span data-ttu-id="7ad09-185">타일의 목록에서 **SharePoint**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-185">In the list of tiles, click **SharePoint**.</span></span>
    
5. <span data-ttu-id="7ad09-p106">브라우저에서 새 **SharePoint** 탭에서 검색 상자에 **ProjectX** 를 입력 하 고 검색을 활성화 한 다음 **ProjectX** 팀 사이트를 클릭 합니다. ProjectX 팀 사이트에 대 한 브라우저에서 새 탭이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-p106">On the new **SharePoint** tab in your browser, type **ProjectX** in the search box, activate the search, and then click the **ProjectX** team site. You should see a new tab in your browser for the ProjectX team site.</span></span>
    
6. <span data-ttu-id="7ad09-p107">설정 아이콘을 클릭 합니다. **사이트**사용 권한 없음 옵션 인지 확인 합니다. ProjectX Admins 그룹의 구성원만 사이트에 대 한 권한을 수정할 수 있기 때문에 올바른지</span><span class="sxs-lookup"><span data-stu-id="7ad09-p107">Click the settings icon. Notice that there is no option for **Site Permissions**. This is correct because only the members of the ProjectX-Admins group can modify permissions on the site</span></span>
    
7. <span data-ttu-id="7ad09-191">메모장 또는 원하는 텍스트 편집기를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-191">Open Notepad or a text editor of your choice.</span></span>
    
8. <span data-ttu-id="7ad09-192">ProjectX 팀 사이트의 URL을 복사 하 고 메모장 이나 텍스트 편집기에서 새 줄에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-192">Copy the URL of the ProjectX team site and paste it on a new line in Notepad or your text editor.</span></span>
    
9. <span data-ttu-id="7ad09-193">브라우저에서 새 **ProjectX 홈** 탭에서 **문서**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-193">On the new **ProjectX-Home** tab in your browser, click **Documents**.</span></span>
    
10. <span data-ttu-id="7ad09-194">ProjectX 문서 폴더 URL을 복사한 후 메모장이나 텍스트 편집기에서 새 줄에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-194">Copy the URL of the ProjectX documents folder and paste it on a new line in Notepad or your text editor.</span></span>
    
11. <span data-ttu-id="7ad09-195">브라우저에서 새 **ProjectX 문서** 탭을 클릭 **새로 만들기 > Word 문서**합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-195">On the new **ProjectX-Documents** tab in your browser, click **New > Word document**.</span></span>
    
12. <span data-ttu-id="7ad09-p108">**Word 온라인** 페이지에 일부 텍스트를 입력, 상태를 **저장**, 브라우저에서 뒤로 단추를 클릭 하 고 페이지를 새로 고칠 때까지 대기 합니다. **문서** 폴더에 새 **Document.docx** 이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-p108">Type some text in the **Word Online** page, wait for the status to indicate **Saved**, click the back button on your browser, and then refresh the page. You should see a new **Document.docx** in the **Documents** folder.</span></span>
    
13. <span data-ttu-id="7ad09-198">**Document.docx** 문서에 대 한 줄임표 (...)를 클릭 하 고 **가져오기 링크를**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-198">Click the ellipsis for the **Document.docx** document, and then click **Get a link**.</span></span>
    
14. <span data-ttu-id="7ad09-199">**'Document.docx' 공유** 대화 상자에서 URL을 복사 하 고 메모장 이나 다른 텍스트 편집기에서 새 줄에 붙여 **'Document.docx' 공유** 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-199">Copy the URL in the **Share 'Document.docx'** dialog box and paste it on a new line in Notepad or your text editor, and then close the **Share 'Document.docx'** dialog box.</span></span>
    
15. <span data-ttu-id="7ad09-200">브라우저에서 **ProjectX 문서** 및 **SharePoint** 탭 닫은 다음 **Microsoft Office Home** 탭을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-200">Close the **ProjectX-Documents** and **SharePoint** tabs in your browser, and then click the **Microsoft Office Home** tab.</span></span>
    
16. <span data-ttu-id="7ad09-201">**잠재 고객 디자이너** 이름을 클릭 한 다음 **로그 아웃**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-201">Click the **Lead Designer** name, and then click **Sign out**.</span></span>
    
<span data-ttu-id="7ad09-202">이제 개발 VP 사용자 계정을 사용 하 여 액세스를 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-202">Now let's demonstrate access using the Development VP user account:</span></span>
  
1. <span data-ttu-id="7ad09-203">개발 VP 계정 이름과 암호를 사용 하 여 Office 365 포털 ([https://portal.office.com](https://portal.office.com))에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-203">Sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using the Development VP account name and its password.</span></span>
    
2. <span data-ttu-id="7ad09-204">타일의 목록에서 **SharePoint**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-204">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="7ad09-p109">브라우저에서 새 **SharePoint** 탭에서 검색 상자에 **ProjectX** 를 입력 하 고 검색을 활성화 한 다음 **ProjectX** 팀 사이트를 클릭 합니다. ProjectX 팀 사이트에 대 한 브라우저에서 새 탭이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-p109">On the new **SharePoint** tab in your browser, type **ProjectX** in the search box, activate the search, and then click the **ProjectX** team site. You should see a new tab in your browser for the ProjectX team site.</span></span>
    
4. <span data-ttu-id="7ad09-207">**문서**클릭 하 고 **Document.docx** 파일을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-207">Click **Documents**, and then click the **Document.docx** file.</span></span>
    
5. <span data-ttu-id="7ad09-p110">브라우저에서 **Document.docx** 탭에서 텍스트를 수정 하려고 합니다. 확인할 수 없다는 메시지가 **이 문서는 읽기 전용으로 설정 합니다.** 이 개발 VP 사용자 계정에 게는 사이트에 대 한 보기 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-p110">In the **Document.docx** tab in your browser, try to modify the text. You should see a message stating **This document is read-only.** This is expected because the Development VP user account only has view permissions for the site.</span></span>
    
6. <span data-ttu-id="7ad09-211">브라우저에서 **Document.docx**, **ProjectX 문서**및 **SharePoint** 탭을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-211">Close the **Document.docx**, **ProjectX-Documents**, and **SharePoint** tabs in your browser.</span></span>
    
7. <span data-ttu-id="7ad09-212">**Microsoft Office Home** 탭을 클릭 하 고 **개발 VP** 이름을 클릭 한 다음 **로그 아웃**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-212">Click the **Microsoft Office Home** tab, click the **Development VP** name, and then click **Sign out**.</span></span>
    
<span data-ttu-id="7ad09-213">이제 없는 사용 권한이 있는 사용자 계정 사용 하 여 액세스를 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-213">Now let's demonstrate access with a user account that has no permissions:</span></span>
  
1. <span data-ttu-id="7ad09-214">사용자 3 계정 이름과 암호를 사용 하 여 Office 365 포털 ([https://portal.office.com](https://portal.office.com))에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-214">Sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using the User 3 account name and its password.</span></span>
    
2. <span data-ttu-id="7ad09-215">타일의 목록에서 **SharePoint**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-215">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="7ad09-p111">브라우저에서 새 **SharePoint** 탭에서 검색 상자에 **ProjectX** 를 입력 한 다음 검색을 활성화 합니다. 메시지를 참조 해야 **검색 일치 Nothing 여기.**</span><span class="sxs-lookup"><span data-stu-id="7ad09-p111">On the new **SharePoint** tab in your browser, type **ProjectX** in the search box and then activate the search. You should see the message **Nothing here matches your search.**</span></span>
    
4. <span data-ttu-id="7ad09-p112">메모장 이나 텍스트 편집기의 열린 인스턴스를에서 브라우저의 주소 표시줄에 ProjectX 사이트에 대 한 URL을 복사 하 고 **Enter**키를 누릅니다. **액세스 거부** 페이지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-p112">From the open instance of Notepad or your text editor, copy the URL for the ProjectX site into the address bar of your browser and press **Enter**. You should see an **Access Denied** page.</span></span>
    
5. <span data-ttu-id="7ad09-p113">메모장 이나 텍스트 편집기에서 사용자의 브라우저 주소 표시줄에 ProjectX 문서 폴더에 대 한 URL을 복사 하 고 **Enter**키를 누릅니다. **액세스 거부** 페이지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-p113">From Notepad or your text editor, copy the URL for the ProjectX Documents folder into the address bar of your browser and press **Enter**. You should see an **Access Denied** page.</span></span>
    
6. <span data-ttu-id="7ad09-p114">메모장 이나 텍스트 편집기에서 사용자의 브라우저 주소 표시줄에 Documents.docx 파일에 대 한 URL을 복사 하 고 **Enter**키를 누릅니다. **액세스 거부** 페이지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-p114">From Notepad or your text editor, copy the URL for the Documents.docx file into the address bar of your browser and press **Enter**. You should see an **Access Denied** page.</span></span>
    
7. <span data-ttu-id="7ad09-224">브라우저에서 **SharePoint** 탭을 닫습니다 **Microsoft Office Home** 탭을 클릭 **사용자 3** 이름을 클릭 한 다음 **로그 아웃**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-224">Close the **SharePoint** tab in your browser, click the **Microsoft Office Home** tab, click the **User 3** name, and then click **Sign out**.</span></span>
    
<span data-ttu-id="7ad09-225">격리 된 SharePoint Online 사이트 추가 테스트를 수행할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7ad09-225">Your isolated SharePoint Online site is now ready for your additional experimentation.</span></span>
  
## <a name="next-step"></a><span data-ttu-id="7ad09-226">다음 단계</span><span class="sxs-lookup"><span data-stu-id="7ad09-226">Next Step</span></span>

<span data-ttu-id="7ad09-227">프로덕션 환경에서 격리 된 SharePoint Online 팀 사이트를 배포할 준비가 되 면 [디자인 한 격리 된 SharePoint Online 팀 사이트에](design-an-isolated-sharepoint-online-team-site.md)대 한 단계별 디자인 고려 사항을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="7ad09-227">When you are ready to deploy an isolated SharePoint Online team site in production, see the step-by-step design considerations in [Design an isolated SharePoint Online team site](design-an-isolated-sharepoint-online-team-site.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="7ad09-228">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7ad09-228">See Also</span></span>

[<span data-ttu-id="7ad09-229">격리 된 SharePoint Online 팀 사이트</span><span class="sxs-lookup"><span data-stu-id="7ad09-229">Isolated SharePoint Online team sites</span></span>](isolated-sharepoint-online-team-sites.md)
  
[<span data-ttu-id="7ad09-230">클라우드 도입 TLG(테스트 랩 가이드)</span><span class="sxs-lookup"><span data-stu-id="7ad09-230">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="7ad09-231">기본 구성 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="7ad09-231">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="7ad09-232">Office 365 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="7ad09-232">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="7ad09-233">클라우드 채택 및 하이브리드 솔루션</span><span class="sxs-lookup"><span data-stu-id="7ad09-233">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




