---
title: SharePoint Online 사이트를 만들고 Office 365 PowerShell을 사용하여 사용자 추가
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: '요약: Office 365 PowerShell을 사용 하 여 새 SharePoint Online 사이트를 만든 다음 해당 사이트에 사용자 및 그룹을 추가 합니다.'
ms.openlocfilehash: 2262c69af7dce7472257512d215c1f0425f875f0
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2019
ms.locfileid: "38031033"
---
# <a name="create-sharepoint-online-sites-and-add-users-with-office-365-powershell"></a><span data-ttu-id="fc3cc-103">SharePoint Online 사이트를 만들고 Office 365 PowerShell을 사용하여 사용자 추가</span><span class="sxs-lookup"><span data-stu-id="fc3cc-103">Create SharePoint Online sites and add users with Office 365 PowerShell</span></span>

 <span data-ttu-id="fc3cc-104">**요약:** Office 365 PowerShell을 사용 하 여 새 SharePoint Online 사이트를 만든 다음 해당 사이트에 사용자 및 그룹을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc3cc-104">**Summary:** Use Office 365 PowerShell to create new SharePoint Online sites, and then add users and groups to those sites.</span></span>

<span data-ttu-id="fc3cc-105">Office 365 PowerShell을 사용 하 여 SharePoint Online 사이트를 만들고 사용자를 추가할 때 Office 356 관리 센터에서 보다 훨씬 빠르게 작업을 빠르게 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc3cc-105">When you use Office 365 PowerShell to create SharePoint Online sites and add users, you can quickly and repeatedly perform tasks much faster than you can in the Office 356 admin center.</span></span> <span data-ttu-id="fc3cc-106">Office 356 관리 센터에서 수행할 수 없는 작업을 수행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc3cc-106">You can also perform tasks that are not possible to perform in the Office 356 admin center.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="fc3cc-107">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="fc3cc-107">Before you begin</span></span>

<span data-ttu-id="fc3cc-108">이 항목의 절차를 수행 하려면 SharePoint Online에 연결 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc3cc-108">The procedures in this topic require you to connect to SharePoint Online.</span></span> <span data-ttu-id="fc3cc-109">자세한 내용은 [SharePoint Online PowerShell에 연결을](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps) 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="fc3cc-109">For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span></span>

## <a name="step-1-create-new-site-collections-using-office-365-powershell"></a><span data-ttu-id="fc3cc-110">1 단계: Office 365 PowerShell을 사용 하 여 새 사이트 모음 만들기</span><span class="sxs-lookup"><span data-stu-id="fc3cc-110">Step 1: Create new site collections using Office 365 PowerShell</span></span>

<span data-ttu-id="fc3cc-111">제공 된 예제 코드와 메모장을 사용 하 여 만든 Office 365 PowerShell 및 .csv 파일을 사용 하 여 여러 사이트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="fc3cc-111">Create multiple sites using Office 365 PowerShell and a .csv file that you create using the example code provided and Notepad.</span></span> <span data-ttu-id="fc3cc-112">이 절차에서는 괄호로 표시 된 자리 표시자 정보를 자체 사이트 및 테 넌 트 관련 정보와 함께 대체 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc3cc-112">For this procedure, you’ll be replacing the placeholder information shown in brackets with your own site- and tenant-specific information.</span></span> <span data-ttu-id="fc3cc-113">이 프로세스를 통해 단일 파일을 만들고 해당 파일을 사용 하는 단일 Office 365 PowerShell 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc3cc-113">This process lets you create a single file and run a single Office 365 PowerShell command that uses that file.</span></span> <span data-ttu-id="fc3cc-114">이렇게 하면 반복 및 이식 가능 하 게 작업을 수행 하 고 SharePoint Online 관리 셸에 긴 명령을 입력 하는 것과 같은 여러 가지 오류를 모두 없앨 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc3cc-114">This makes the actions taken both repeatable and portable and eliminates many, if not all, errors that can come from typing long commands into the SharePoint Online Management Shell.</span></span> <span data-ttu-id="fc3cc-115">이 절차는 두 부분으로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fc3cc-115">There are two parts to this procedure.</span></span> <span data-ttu-id="fc3cc-116">먼저 .csv 파일을 만든 다음 Office 365 PowerShell을 사용 하 여 해당 .csv 파일을 참조 하 여 해당 콘텐츠를 사용 하 여 사이트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="fc3cc-116">First you’ll create a .csv file, and then you’ll reference that .csv file using Office 365 PowerShell, which will use its contents to create the sites.</span></span>

<span data-ttu-id="fc3cc-117">Office 365 PowerShell cmdlet은 .csv 파일을 가져온 후 파일의 첫 번째 줄을 열 머리글로 읽는 중괄호 내부의 루프에 파이프 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc3cc-117">The Office 365 PowerShell cmdlet imports the .csv file and pipes it to a loop inside the curly brackets that reads the first line of the file as column headers.</span></span> <span data-ttu-id="fc3cc-118">그런 다음 Office 365 PowerShell cmdlet은 나머지 레코드를 반복 하 고 각 레코드에 대 한 새 사이트 모음을 만들고, 열 머리글에 따라 사이트 모음의 속성을 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc3cc-118">The Office 365 PowerShell cmdlet then iterates through the remaining records, creates a new site collection for each record, and assigns properties of the site collection according to the column headers.</span></span>

### <a name="create-a-csv-file"></a><span data-ttu-id="fc3cc-119">.csv 파일 만들기</span><span class="sxs-lookup"><span data-stu-id="fc3cc-119">Create a .csv file</span></span>

1. <span data-ttu-id="fc3cc-120">메모장을 열고 다음 텍스트 블록을 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="fc3cc-120">Open Notepad, and paste the following text block into it:</span></span><br/>

```
Owner,StorageQuota,Url,ResourceQuota,Template,TimeZoneID,Name
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/TeamSite01,25,EHS#1,10,Contoso Team Site
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/Blog01,25,BLOG#0,10,Contoso Blog
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Project01,25,PROJECTSITE#0,10,Project Alpha
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Community01,25,COMMUNITY#0,10,Community Site
```
<br/><span data-ttu-id="fc3cc-121">여기서 *테* 넌 트에서은 테 넌 트의 이름이 고 *소유자* 는 기본 사이트 모음 관리자 역할을 부여 하려는 테 넌 트에 있는 사용자의 사용자 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="fc3cc-121">Where *tenant* is the name of your tenant, and *owner* is the user name of the user on your tenant to whom you want to grant the role of primary site collection administrator.</span></span><br/><span data-ttu-id="fc3cc-122">(메모장을 사용 하 여 빠르게 대량으로 바꿀 때 Ctrl + H를 누를 수 있습니다.)</span><span class="sxs-lookup"><span data-stu-id="fc3cc-122">(You can press Ctrl+H when you use Notepad to bulk replace faster.)</span></span><br/>

2. <span data-ttu-id="fc3cc-123">파일을 바탕 화면에 **sitecollections.csv**로 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc3cc-123">Save the file on your desktop as **SiteCollections.csv**.</span></span><br/>

> [!TIP]
> <span data-ttu-id="fc3cc-124">이 또는 다른 .csv 또는 Windows PowerShell 스크립트 파일을 사용 하기 전에 불필요 하거나 인쇄 되지 않는 문자가 없는지 확인 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="fc3cc-124">Before you use this or any other .csv or Windows PowerShell script file, it is good practice to make sure that there are no extraneous or nonprinting characters.</span></span> <span data-ttu-id="fc3cc-125">이렇게 하려면 Word에서 파일을 열고 리본 메뉴에서 단락 아이콘을 클릭하여 인쇄할 수 없는 문자를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="fc3cc-125">Open the file in Word, and in the ribbon, click the paragraph icon to show nonprinting characters.</span></span> <span data-ttu-id="fc3cc-126">불필요한 인쇄할 수 없는 문자가 없어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc3cc-126">There should be no extraneous nonprinting characters.</span></span> <span data-ttu-id="fc3cc-127">예를 들어 파일 끝의 마지막 단락 표시 뒤에는 단락 표시가 없어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc3cc-127">For example, there should be no paragraph marks beyond the final one at the end of the file.</span></span>

### <a name="run-the-windows-powershell-command"></a><span data-ttu-id="fc3cc-128">Windows PowerShell 명령 실행</span><span class="sxs-lookup"><span data-stu-id="fc3cc-128">Run the Windows PowerShell command</span></span>

1. <span data-ttu-id="fc3cc-129">Windows PowerShell 프롬프트에서 다음 cmdlet을 입력 하거나 복사 하 여 붙여 넣은 다음 enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="fc3cc-129">At the Windows PowerShell prompt, type or copy and paste the following cmdlet, and press Enter:</span></span><br/>
```
Import-Csv C:\users\MyAlias\desktop\SiteCollections.csv | ForEach-Object {New-SPOSite -Owner $_.Owner -StorageQuota $_.StorageQuota -Url $_.Url -NoWait -ResourceQuota $_.ResourceQuota -Template $_.Template -TimeZoneID $_.TimeZoneID -Title $_.Name}
```
<br/><span data-ttu-id="fc3cc-130">여기서 *Myalias* 는 사용자 별칭과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="fc3cc-130">Where *MyAlias* equals your user alias.</span></span><br/>

2. <span data-ttu-id="fc3cc-131">Windows PowerShell 프롬프트가 다시 나타날 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="fc3cc-131">Wait for the Windows PowerShell prompt to reappear.</span></span> <span data-ttu-id="fc3cc-132">1~2분 정도 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc3cc-132">It might take a minute or two.</span></span><br/>

3. <span data-ttu-id="fc3cc-133">Windows PowerShell 프롬프트에서 다음 cmdlet을 입력 하거나 복사 하 여 붙여 넣은 다음 enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="fc3cc-133">At the Windows PowerShell prompt, type or copy and paste the following cmdlet, and press Enter:</span></span><br/>

```
Get-SPOSite -Detailed | Format-Table -AutoSize
```
<br/>

4. <span data-ttu-id="fc3cc-134">목록의 새 사이트 모음을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="fc3cc-134">Note the new site collections in the list.</span></span> <span data-ttu-id="fc3cc-135">**Contosotest**, **TeamSite01**, **Blog01**및 **Project01** 의 사이트 모음이 표시 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc3cc-135">You should see the following site collections: **contosotest**, **TeamSite01**, **Blog01**, and **Project01**</span></span>

<span data-ttu-id="fc3cc-136">그거에요.</span><span class="sxs-lookup"><span data-stu-id="fc3cc-136">That’s it.</span></span> <span data-ttu-id="fc3cc-137">만든 .csv 파일 및 단일 Windows PowerShell cmdlet을 사용 하 여 여러 사이트 모음을 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="fc3cc-137">You’ve created multiple site collections using the .csv file you created and a single Windows PowerShell cmdlet.</span></span> <span data-ttu-id="fc3cc-138">이제이 사이트에 사용자를 만들고 할당할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="fc3cc-138">You’re now ready to create and assign users to these sites.</span></span>

## <a name="step-2-add-users-and-groups"></a><span data-ttu-id="fc3cc-139">2단계: 사용자 및 그룹 추가</span><span class="sxs-lookup"><span data-stu-id="fc3cc-139">Step 2: Add users and groups</span></span>

<span data-ttu-id="fc3cc-p109">이제 사용자를 만들어 사이트 모음 그룹에 추가할 수 있습니다. 그런 다음 .csv 파일을 사용하여 새 그룹 및 사용자를 대량 업로드합니다.</span><span class="sxs-lookup"><span data-stu-id="fc3cc-p109">Now you’re going to create users and add them to a site collection group. You will then use a .csv file to bulk upload new groups and users.</span></span>

<span data-ttu-id="fc3cc-142">다음 절차에서는 contosotest, TeamSite01, Blog01, Project01 사이트 모음을 정상적으로 만들었다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="fc3cc-142">The following procedures assume that you successfully created the site collections contosotest, TeamSite01, Blog01, and Project01.</span></span>

### <a name="create-csv-and-ps1-files"></a><span data-ttu-id="fc3cc-143">.csv 및 .ps1 파일 만들기</span><span class="sxs-lookup"><span data-stu-id="fc3cc-143">Create .csv and .ps1 files</span></span>

1. <span data-ttu-id="fc3cc-144">메모장을 열고 다음 텍스트 블록을 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="fc3cc-144">Open Notepad, and paste the following text block into it:</span></span><br/>
```
Site,Group,PermissionLevels
https://tenant.sharepoint.com/sites/contosotest,Contoso Project Leads,Full Control
https://tenant.sharepoint.com/sites/contosotest,Contoso Auditors,View Only
https://tenant.sharepoint.com/sites/contosotest,Contoso Designers,Design
https://tenant.sharepoint.com/sites/TeamSite01,XT1000 Team Leads,Full Control
https://tenant.sharepoint.com/sites/TeamSite01,XT1000 Advisors,Edit
https://tenant.sharepoint.com/sites/Blog01,Contoso Blog Designers,Design
https://tenant.sharepoint.com/sites/Blog01,Contoso Blog Editors,Edit
https://tenant.sharepoint.com/sites/Project01,Project Alpha Approvers,Full Control
```
<br/><span data-ttu-id="fc3cc-145">여기서 *테 넌* 트에서 테 넌 트 이름과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="fc3cc-145">Where *tenant* equals your tenant name.</span></span><br/>

2. <span data-ttu-id="fc3cc-146">파일을 바탕 화면에 **groupsandpermissions.csv**로 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc3cc-146">Save the file to your desktop as **GroupsAndPermissions.csv**.</span></span><br/>

3. <span data-ttu-id="fc3cc-147">새 메모장 인스턴스를 열고 다음 텍스트 블록을 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="fc3cc-147">Open a new instance of Notepad, and paste the following text block into it:</span></span><br/>

```
Group,LoginName,Site
Contoso Project Leads,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/contosotest
Contoso Auditors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/contosotest
Contoso Designers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/contosotest
XT1000 Team Leads,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/TeamSite01
XT1000 Advisors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/TeamSite01
Contoso Blog Designers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Blog01
Contoso Blog Editors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Blog01
Project Alpha Approvers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Project01
```
<br/><span data-ttu-id="fc3cc-148">여기서 *테 넌 트는* 테 넌 트 이름과 같고 *username* 은 기존 사용자의 사용자 이름과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="fc3cc-148">Where *tenant* equals your tenant name, and *username* equals the user name of an existing user.</span></span><br/>

4. <span data-ttu-id="fc3cc-149">파일을 데스크톱에 **사용자 .csv**로 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc3cc-149">Save the file to your desktop as **Users.csv**.</span></span><br/>

5. <span data-ttu-id="fc3cc-150">새 메모장 인스턴스를 열고 다음 텍스트 블록을 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="fc3cc-150">Open a new instance of Notepad, and paste the following text block into it:</span></span><br/>

```
Import-Csv C:\users\MyAlias\desktop\GroupsAndPermissions.csv | ForEach-Object {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\users\MyAlias\desktop\Users.csv | where {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```
<br/><span data-ttu-id="fc3cc-151">여기서 MyAlias는 현재 로그온 되어 있는 사용자의 사용자 이름과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="fc3cc-151">Where MyAlias equals the user name of the user that is currently logged on.</span></span><br/>

6. <span data-ttu-id="fc3cc-152">파일을 바탕 화면에 Usersandgroups.ps1로 저장 **합니다.**</span><span class="sxs-lookup"><span data-stu-id="fc3cc-152">Save the file to your desktop as **UsersAndGroups.ps1**.</span></span> <span data-ttu-id="fc3cc-153">간단한 Windows PowerShell 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="fc3cc-153">This is a simple Windows PowerShell script.</span></span>

<span data-ttu-id="fc3cc-154">이제 UsersAndGroup.ps1 스크립트를 실행하여 사용자와 그룹을 여러 사이트 모음에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc3cc-154">You’re now ready to run the UsersAndGroup.ps1 script to add users and groups to multiple site collections.</span></span>

### <a name="run-usersandgroupsps1-script"></a><span data-ttu-id="fc3cc-155">UsersAndGroups.ps1 스크립트 실행</span><span class="sxs-lookup"><span data-stu-id="fc3cc-155">Run UsersAndGroups.ps1 script</span></span>

1. <span data-ttu-id="fc3cc-156">SharePoint Online 관리 셸로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="fc3cc-156">Return to the SharePoint Online Management Shell.</span></span><br/>
2. <span data-ttu-id="fc3cc-157">Windows PowerShell 프롬프트에서 다음 줄을 입력 하거나 복사 하 여 붙여 넣은 다음 enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="fc3cc-157">At the Windows PowerShell prompt, type or copy and paste the following line, and press Enter:</span></span><br/>
```
Set-ExecutionPolicy Bypass
```
<br/>

3. <span data-ttu-id="fc3cc-158">확인 메시지가 나타나면 **Y**키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="fc3cc-158">At the confirmation prompt, press **Y**.</span></span><br/>

4. <span data-ttu-id="fc3cc-159">Windows PowerShell 프롬프트에서 다음을 입력 하거나 복사 하 여 붙여 넣은 다음 enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="fc3cc-159">At the Windows PowerShell prompt, type or copy and paste the following, and press Enter:</span></span><br/>

```
c:\users\MyAlias\desktop\UsersAndGroups.ps1
```
<br/><span data-ttu-id="fc3cc-160">여기서 *Myalias* 는 사용자 이름과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="fc3cc-160">Where *MyAlias* equals your user name.</span></span><br/>

5. <span data-ttu-id="fc3cc-p111">프롬프트가 반환될 때까지 기다렸다가 계속 진행합니다. 먼저 작성된 그룹이 표시되고, 사용자를 추가하면 그룹 목록이 반복적으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="fc3cc-p111">Wait for the prompt to return before moving on. You will first see the groups appear as they are created. Then you will see the group list repeated as users are added.</span></span>

## <a name="see-also"></a><span data-ttu-id="fc3cc-164">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fc3cc-164">See also</span></span>

[<span data-ttu-id="fc3cc-165">SharePoint Online PowerShell에 연결</span><span class="sxs-lookup"><span data-stu-id="fc3cc-165">Connect to SharePoint Online PowerShell</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[<span data-ttu-id="fc3cc-166">SharePoint Online 사이트 그룹 관리 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="fc3cc-166">Manage SharePoint Online site groups Office 365 PowerShell</span></span>](manage-sharepoint-site-groups-with-powershell.md)

[<span data-ttu-id="fc3cc-167">Office 365 PowerShell 사용한 Office 365 관리</span><span class="sxs-lookup"><span data-stu-id="fc3cc-167">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="fc3cc-168">Office 365 PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="fc3cc-168">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

