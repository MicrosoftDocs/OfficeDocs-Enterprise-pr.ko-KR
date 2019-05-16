---
title: Office 365 PowerShell을 사용하여 SharePoint Online 사용자 및 그룹 관리
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/07/2018
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: '요약: Office 365 PowerShell을 사용 하 여 SharePoint Online 사용자, 그룹 및 사이트를 관리 합니다.'
ms.openlocfilehash: 194486f539593215b8f8a17c04e3d4f499077c65
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068824"
---
# <a name="manage-sharepoint-online-users-and-groups-with-office-365-powershell"></a><span data-ttu-id="b01dd-103">Office 365 PowerShell을 사용하여 SharePoint Online 사용자 및 그룹 관리</span><span class="sxs-lookup"><span data-stu-id="b01dd-103">Manage SharePoint Online users and groups with Office 365 PowerShell</span></span>

 <span data-ttu-id="b01dd-104">**요약:** Office 365 PowerShell을 사용 하 여 SharePoint Online 사용자, 그룹 및 사이트를 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="b01dd-104">**Summary:** Use Office 365 PowerShell to manage SharePoint Online users, groups, and sites.</span></span>

<span data-ttu-id="b01dd-105">많은 사용자 계정 또는 그룹 목록을 사용 하 고이를 보다 쉽게 관리 하기 원하는 SharePoint Online 관리자는 Office 365 PowerShell을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b01dd-105">If you are a SharePoint Online administrator who works with large lists of user accounts or groups and wants an easier way to manage them, you can use Office 365 PowerShell.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="b01dd-106">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="b01dd-106">Before you begin</span></span>

<span data-ttu-id="b01dd-107">이 항목의 절차를 수행 하려면 SharePoint Online에 연결 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b01dd-107">The procedures in this topic require you to connect to SharePoint Online.</span></span> <span data-ttu-id="b01dd-108">자세한 내용은 [SharePoint Online PowerShell에 연결을](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps) 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b01dd-108">For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span></span>

## <a name="get-a-list-of-sites-groups-and-users"></a><span data-ttu-id="b01dd-109">사이트, 그룹, 사용자 목록 가져오기</span><span class="sxs-lookup"><span data-stu-id="b01dd-109">Get a list of sites, groups, and users</span></span>

<span data-ttu-id="b01dd-p102">사용자 및 그룹 관리를 시작하려면 먼저 사이트, 그룹 및 사용자 목록을 가져와야 합니다. 그리고 나면 해당 정보를 이 문서의 예제 전반에 걸쳐 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b01dd-p102">Before we start to manage users and groups, you need to get lists of your sites, groups, and users. You can then use this information to work through the example in this article.</span></span>

### <a name="get-a-list-of-sites"></a><span data-ttu-id="b01dd-112">사이트 목록 가져오기</span><span class="sxs-lookup"><span data-stu-id="b01dd-112">Get a list of sites</span></span>

<span data-ttu-id="b01dd-113">이 명령을 사용하여 테넌트의 사이트 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b01dd-113">Get a list of the sites in your tenant with this command:</span></span>

```
Get-SPOSite
```

### <a name="get-a-list-of-groups"></a><span data-ttu-id="b01dd-114">그룹 목록 가져오기</span><span class="sxs-lookup"><span data-stu-id="b01dd-114">Get a list of groups</span></span>

<span data-ttu-id="b01dd-115">이 명령을 사용하여 테넌트의 그룹 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b01dd-115">Get a list of the groups in your tenant with this command:</span></span>

```
Get-SPOSite | ForEach {Get-SPOSiteGroup -Site $_.Url} | Format-Table
```

### <a name="get-a-list-of-users"></a><span data-ttu-id="b01dd-116">사용자 목록 가져오기</span><span class="sxs-lookup"><span data-stu-id="b01dd-116">Get a list of users</span></span>

<span data-ttu-id="b01dd-117">이 명령을 사용하여 테넌트의 사용자 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b01dd-117">Get a list of the users in your tenant with this command:</span></span>

```
Get-SPOSite | ForEach {Get-SPOUser -Site $_.Url}
```

## <a name="add-a-user-to-the-site-collection-administrators-group"></a><span data-ttu-id="b01dd-118">사이트 모음 관리자 그룹에 사용자 추가</span><span class="sxs-lookup"><span data-stu-id="b01dd-118">Add a user to the Site Collection Administrators group</span></span>

<span data-ttu-id="b01dd-119">**Set-SPOUser** 명령을 사용하여 사이트 모음의 사이트 모음 관리자 목록에 사용자를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b01dd-119">You use the **Set-SPOUser** command to add a user to the list of Site Collection Administrators on a site collection.</span></span> <span data-ttu-id="b01dd-120">이 작업을 위한 구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b01dd-120">This is how the syntax looks:</span></span>

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.onmicrosoft.com -IsSiteCollectionAdmin $true
 ```

<span data-ttu-id="b01dd-121">이러한 명령을 사용 하려면 replace the < 및 > 문자를 포함 하 여 따옴표 안에 있는 모든 항목을 올바른 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="b01dd-121">To use these commands, replace replace everything within the quotes, including the < and > characters, with the correct names.</span></span>

<span data-ttu-id="b01dd-122">예를 들어 다음 명령 집합은 contoso1 테 넌 시에 있는 ContosoTest 사이트 모음의 사이트 모음 관리자 목록에 오 팔 Castillo (사용자 이름 opalc)을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b01dd-122">For example, this set of commands adds Opal Castillo (user name opalc) the list of Site Collection Administrators on the ContosoTest site collection in the contoso1 tenancy:</span></span>

```
$tenant = "contoso1"
$site = "contosotest"
$user = "opalc"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.onmicrosoft.com -IsSiteCollectionAdmin $true
```

<span data-ttu-id="b01dd-123">이러한 명령을 복사 하 여 메모장에 붙여 넣고 $tenant, $site 및 $user의 변수 값을 환경의 실제 값으로 변경한 다음이를 SharePoint Online 관리 셸 창에 붙여 넣어 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="b01dd-123">You can copy and paste these commands into Notepad, change the variable values for $tenant, $site, and $user to actual values from your environment, and then paste this into your SharePoint Online Management Shell window to run them.</span></span>

## <a name="add-a-user-to-other-site-collection-administrators-groups"></a><span data-ttu-id="b01dd-124">다른 사이트 모음 관리자 그룹에 사용자 추가</span><span class="sxs-lookup"><span data-stu-id="b01dd-124">Add a user to other Site Collection Administrators groups</span></span>

<span data-ttu-id="b01dd-125">이 작업에서는 **Add-SPOUser** 명령을 사용하여 사이트 모음의 SharePoint 그룹에 사용자를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="b01dd-125">In this task, we'll use the **Add-SPOUser** command to add a user to a SharePoint group on a site collection.</span></span>

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
$group = "<group name name, such as Auditors>"
Add-SPOUser -Group $group -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site

```

<span data-ttu-id="b01dd-126">예를 들어 Glen Rife(사용자 이름 glenr)를 contoso1 테넌시에 있는 ContosoTest 사이트 모음의 감사자 그룹에 추가해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="b01dd-126">For example, let’s add Glen Rife (user name glenr) to the Auditors group on the ContosoTest site collection in the contoso1 tenancy:</span></span>

```
$tenant = "contoso1"
$site = "contosotest"
$user = "glenr"
$group = "Auditors"
Add-SPOUser -Group $group -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="create-a-site-collection-group"></a><span data-ttu-id="b01dd-127">사이트 모음 그룹 만들기</span><span class="sxs-lookup"><span data-stu-id="b01dd-127">Create a site collection group</span></span>

<span data-ttu-id="b01dd-128">**Set-SPOSiteGroup** 명령을 사용하여 새 SharePoint 그룹을 만든 다음 ContosoTest 사이트 모음에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b01dd-128">You use the **Set-SPOSiteGroup** command to create a new SharePoint group and add it to the ContosoTest site collection.</span></span>

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$group = "<group name name, such as Auditors>"
$level = "<permission level, such as View Only>"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```
<span data-ttu-id="b01dd-129">사용 권한 수준과 같은 그룹 속성은 나중에 **Set-SPOSiteGroup** cmdlet을 사용하여 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b01dd-129">Group properties, such as permission levels, can be updated later by using the **Set-SPOSiteGroup** cmdlet.</span></span>

<span data-ttu-id="b01dd-130">예를 들어 보기 전용 권한이 있는 감사자 그룹을 contoso1 테 넌 시에 있는 Contoso 테스트 사이트 모음에 추가 해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="b01dd-130">For example, let’s add the Auditors group with View Only permissions to the Contoso Test site collection in the contoso1 tenancy:</span></span>

```
$tenant = "contoso1"
$site = "Contoso Test"
$group = "Auditors"
$level = "View Only"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="remove-users-from-a-group"></a><span data-ttu-id="b01dd-131">그룹에서 사용자 제거</span><span class="sxs-lookup"><span data-stu-id="b01dd-131">Remove users from a group</span></span>

<span data-ttu-id="b01dd-p104">사이트 하나 또는 모든 사이트에서 사용자를 제거해야 하는 경우가 있습니다. 직원이 사업부를 이동하거나 퇴사하는 경우를 예로 들 수 있습니다. 직원이 한 명이라면 UI에서 이 작업을 쉽게 수행할 수 있습니다. 그러나 전체 사업부를 사이트 간에 이동해야 하는 경우에는 쉽지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b01dd-p104">Sometimes you have to remove a user from a site or even all sites. Perhaps the employee moves from one division to another or leaves the company. You can do this for one employee easily in the UI, but this is not easily done when you have to move a complete division from one site to another.</span></span>

<span data-ttu-id="b01dd-135">그러나 SharePoint Online 관리 셸 및 CSV 파일을 사용 하는 것이 빠르고 쉬운 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="b01dd-135">However by using the SharePoint Online Management Shell and CSV files, this is fast and easy.</span></span> <span data-ttu-id="b01dd-136">이 작업에서는 Windows PowerShell을 사용하여 사이트 모음 보안 그룹에서 사용자를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="b01dd-136">In this task, you'll use Windows PowerShell to remove a user from a site collection security group.</span></span> <span data-ttu-id="b01dd-137">그런 다음 CSV 파일을 사용해 여러 사이트에서 다수의 사용자를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="b01dd-137">Then you'll use a CSV file and remove lots of users from different sites.</span></span> 

<span data-ttu-id="b01dd-138">명령 구문이 표시 되도록 하기 위해 Office 365 사용자 하나만 사이트 모음 그룹에서 제거 하는 **SPOUser** 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b01dd-138">We'll be using the **Remove-SPOUser** command to remove a single Office 365 user from a site collection group just so we can see the command syntax.</span></span> <span data-ttu-id="b01dd-139">이 작업을 위한 구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b01dd-139">Here is how the syntax looks:</span></span>

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
$group = "<group name name, such as Auditors>"
Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```
<span data-ttu-id="b01dd-140">예를 들어 contoso1 테 넌 시에 있는 Contoso 테스트 사이트 모음의 사이트 모음 감사자 그룹에서 강현수를 제거 하는 경우를 가정해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="b01dd-140">For example, let’s remove Bobby Overby from the site collection Auditors group in the Contoso Test site collection in the contoso1 tenancy:</span></span>

```
$tenant = "contoso1"
$site = "contosotest"
$user = "bobbyo"
$group = "Auditors"
Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```

<span data-ttu-id="b01dd-141">현재는 모든 그룹에서 강현수를 제거 하려고 한다고 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b01dd-141">Suppose we wanted to remove Bobby from all the groups he is currently in.</span></span> <span data-ttu-id="b01dd-142">이 작업을 수행 하는 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b01dd-142">Here is how we would do that:</span></span>

```
$tenant = "contoso1"
$user = "bobbyo"
Get-SPOSite | ForEach {Get-SPOSiteGroup –Site $_.Url} | ForEach {Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site &_.Url}
```

> [!WARNING]
> <span data-ttu-id="b01dd-143">이는 단지 예 일 뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="b01dd-143">This is just an example.</span></span> <span data-ttu-id="b01dd-144">실제로 사용자가 퇴사하는 경우 등 모든 그룹에서 사용자를 제거해야 하는 경우가 아니면 이 명령을 실행해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b01dd-144">You should not run this command unless you really have to remove a user from every group, for example if the user leaves the company.</span></span>

## <a name="automate-management-of-large-lists-of-users-and-groups"></a><span data-ttu-id="b01dd-145">대형 사용자 및 그룹 목록의 관리 자동화</span><span class="sxs-lookup"><span data-stu-id="b01dd-145">Automate management of large lists of users and groups</span></span>

<span data-ttu-id="b01dd-146">SharePoint 사이트에 다 수의 계정을 추가 하 고 사용 권한을 부여 하려면 CSV 파일을 Microsoft 365 관리 센터, 개별 PowerShell 명령 또는 PowerShell을 사용 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b01dd-146">To add a large number of accounts to SharePoint sites and give them permissions, you can use the Microsoft 365 admin center, individual PowerShell commands, or PowerShell an a CSV file.</span></span> <span data-ttu-id="b01dd-147">이중에서 CSV 파일이 작업을 자동화하는 가장 빠른 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="b01dd-147">Of these choices, the CSV file is the fastest way to automate this task.</span></span>

<span data-ttu-id="b01dd-148">기본적인 프로세스는 Windows PowerShell 스크립트에 필요한 매개 변수에 해당하는 헤더(열)가 포함된 CSV 파일을 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b01dd-148">The basic process is to create a CSV file that has headers (columns) that correspond to the parameters that the Windows PowerShell script needs.</span></span> <span data-ttu-id="b01dd-149">Excel에서 이러한 목록을 쉽게 만든 다음 CSV 파일로 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b01dd-149">You can easily create such a list in Excel and then export it as a CSV file.</span></span> <span data-ttu-id="b01dd-150">그런 다음 Windows PowerShell 스크립트를 사용하여 CSV 파일에서 레코드(행)를 반복해 사용자를 그룹에, 그룹을 사이트에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="b01dd-150">Then, you use a Windows PowerShell script to iterate through records (rows) in the CSV file, adding the users to groups and the groups to sites.</span></span> 

<span data-ttu-id="b01dd-p111">예를 들어 사이트 모음, 그룹 및 사용 권한 그룹을 정의하는 CSV 파일을 만들어 보겠습니다. 다음으로는 CSV 파일을 만들어 그룹에 사용자를 채웁니다. 마지막으로 그룹을 만들고 채우는 간단한 Windows PowerShell 스크립트를 만들어 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="b01dd-p111">For example, let’s create a CSV file to define a group of site collections, groups, and permissions. Next, we will create a CSV file to populate the groups with users. Finally, we will create and run a simple Windows PowerShell script that creates and populates the groups.</span></span>

<span data-ttu-id="b01dd-154">다음과 같은 구조의 첫 번째 CSV 파일은 하나 이상의 그룹을 하나 이상의 사이트 모음에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="b01dd-154">The first CSV file will add one or more groups to one or more site collections and will have this structure:</span></span>

### <a name="header"></a><span data-ttu-id="b01dd-155">머리글이</span><span class="sxs-lookup"><span data-stu-id="b01dd-155">Header:</span></span>

```
Site,Group,PermissionLevels
```

### <a name="item"></a><span data-ttu-id="b01dd-156">품목이</span><span class="sxs-lookup"><span data-stu-id="b01dd-156">Item:</span></span>

```
https://tenant.sharepoint.com/sites/site,group,level
```

<span data-ttu-id="b01dd-157">예제 파일은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b01dd-157">Here is an example file:</span></span>

```
Site,Group,PermissionLevels
https://contoso1.sharepoint.com/sites/contosotest,Contoso Project Leads,Full Control
https://contoso1.sharepoint.com/sites/contosotest,Contoso Auditors,View Only
https://contoso1.sharepoint.com/sites/contosotest,Contoso Designers,Design
https://contoso1.sharepoint.com/sites/TeamSite01,XT1000 Team Leads,Full Control
https://contoso1.sharepoint.com/sites/TeamSite01,XT1000 Advisors,Edit
https://contoso1.sharepoint.com/sites/Blog01,Contoso Blog Designers,Design
https://contoso1.sharepoint.com/sites/Blog01,Contoso Blog Editors,Edit
https://contoso1.sharepoint.com/sites/Project01,Project Alpha Approvers,Full Control
```

<span data-ttu-id="b01dd-158">다음과 같은 구조의 두 번째 CSV 파일은 한 명 이상의 사용자를 하나 이상의 그룹에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="b01dd-158">The second CSV file will add one or more users to one or more groups and will have this structure:</span></span>

### <a name="header"></a><span data-ttu-id="b01dd-159">머리글이</span><span class="sxs-lookup"><span data-stu-id="b01dd-159">Header:</span></span>

```
Group,LoginName,Site
```

### <a name="item"></a><span data-ttu-id="b01dd-160">품목이</span><span class="sxs-lookup"><span data-stu-id="b01dd-160">Item:</span></span>

```
group,login,https://tenant.sharepoint.com/sites/site
```

<span data-ttu-id="b01dd-161">예제 파일은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b01dd-161">Here is an example file:</span></span>

```
Group,LoginName,Site
Contoso Project Leads,bobbyo@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/contosotest
Contoso Auditors,allieb@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/contosotest
Contoso Designers,bonniek@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/contosotest
XT1000 Team Leads,dorenap@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/TeamSite01
XT1000 Advisors,garthf@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/TeamSite01
Contoso Blog Designers,janets@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/Blog01
Contoso Blog Editors,opalc@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/Blog01
Project Alpha Approvers,robinc@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/Project01
```

<span data-ttu-id="b01dd-162">그런 다음 해당 드라이브에 CSV 파일 두 개가 저장되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b01dd-162">For the next step, you must have the two CSV files saved to your drive.</span></span> <span data-ttu-id="b01dd-163">다음은 두 CSV 파일을 모두 사용 하 고 사용 권한 및 그룹 구성원을 추가 하는 명령 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="b01dd-163">Here are example commands that use both CSV files and to add permissions and group membership:</span></span>

```
Import-Csv C:\O365Admin\GroupsAndPermissions.csv | ForEach {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\O365Admin\Users.csv | ForEach {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```

<span data-ttu-id="b01dd-164">이 스크립트는 CSV 파일 내용을 가져오고 열의 값을 사용 하 여 **remove-spositegroup** 및 **Add-spouser** 명령에 대 한 매개 변수를 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="b01dd-164">The script imports the CSV file contents and uses the values in the columns to populate the parameters of the **New-SPOSiteGroup** and **Add-SPOUser** commands.</span></span> <span data-ttu-id="b01dd-165">이 예제에서는이를 C 드라이브의 theO365Admin 폴더에 저장 하지만 원하는 위치에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b01dd-165">In our example, we are saving this to theO365Admin folder on drive C, but you can save it wherever you want.</span></span>

<span data-ttu-id="b01dd-166">다음으로 동일한 CSV 파일을 사용해 서로 다른 사이트의 여러 그룹에서 사용자 여러 명을 제거해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="b01dd-166">Now, let’s remove a bunch of people for several groups in different sites using the same CSV file.</span></span> <span data-ttu-id="b01dd-167">예제 명령은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b01dd-167">Here is an example command:</span></span>

```
Import-Csv C:\O365Admin\Users.csv | ForEach {Remove-SPOUser -LoginName $_.LoginName -Site $_.Site -Group $_.Group}
```

## <a name="generate-user-reports"></a><span data-ttu-id="b01dd-168">사용자 보고서 생성</span><span class="sxs-lookup"><span data-stu-id="b01dd-168">Generate user reports</span></span>

<span data-ttu-id="b01dd-p115">사이트 몇 개에 대해 간단한 보고서를 가져와 해당 사이트의 사용자, 사용자의 사용 권한 수준 및 기타 속성을 표시할 수 있습니다. 이 작업을 위한 구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b01dd-p115">You might want to get a simple report for a few sites and display the users for those sites, their permission level, and other properties. This is how the syntax looks:</span></span>

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | select * | Format-table -Wrap -AutoSize | Out-File c\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="b01dd-171">이 구문은 3개 사이트의 데이터를 가져와 로컬 드라이브의 텍스트 파일에 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="b01dd-171">This will grab the data for these three sites and write them to a text file on your local drive.</span></span> <span data-ttu-id="b01dd-172">–Append 매개 변수는 기존 파일에 새 콘텐츠를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="b01dd-172">Note that the parameter –Append will add new content to an existing file.</span></span>

<span data-ttu-id="b01dd-173">예를 들어 Contoso1 테넌트의 ContosoTest, TeamSite01 및 Project01 사이트에 대한 보고서를 실행해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="b01dd-173">For example, let's run a report on the ContosoTest, TeamSite01, and Project01 sites for the Contoso1 tenant:</span></span>

```
$tenant = "contoso1"
$site = "contosotest"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "TeamSite01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site |Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "Project01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="b01dd-174">**$Site** 변수만 변경 해야 했습니다.</span><span class="sxs-lookup"><span data-stu-id="b01dd-174">Note that we had to change only the **$site** variable.</span></span> <span data-ttu-id="b01dd-175">**$Tenant** 변수는 명령에 대 한 세 가지 실행을 모두 통해 해당 값을 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="b01dd-175">The **$tenant** variable keeps its value through all three runs of the command.</span></span>

<span data-ttu-id="b01dd-p118">모든 사이트에 대해 이 작업을 수행하려는 경우 다음 명령을 사용하면 모든 웹 사이트를 입력하지 않고도 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b01dd-p118">However, what if you wanted to do this for every site? You can do this without having to type all those websites by using this command:</span></span>

```
Get-SPOSite | ForEach {Get-SPOUser –Site $_.Url} | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="b01dd-178">이 보고서는 매우 단순하므로 코드를 더 추가하여 더 자세한 정보를 포함하는 보고서나 보다 구체적인 보고서를 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b01dd-178">This report is fairly simple, and you can add more code to create more specific reports or reports that include more detailed information.</span></span> <span data-ttu-id="b01dd-179">그러나 sharepoint online 관리 셸을 사용 하 여 SharePoint Online 환경에서 사용자를 관리 하는 방법에 대 한 아이디어를 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b01dd-179">But this should give you an idea of how to use the SharePoint Online Management Shell to manage users in the SharePoint Online environment.</span></span>
   
## <a name="see-also"></a><span data-ttu-id="b01dd-180">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b01dd-180">See also</span></span>

[<span data-ttu-id="b01dd-181">SharePoint Online PowerShell에 연결</span><span class="sxs-lookup"><span data-stu-id="b01dd-181">Connect to SharePoint Online PowerShell</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[<span data-ttu-id="b01dd-182">Office 365 PowerShell을 사용하여 SharePoint Online 관리</span><span class="sxs-lookup"><span data-stu-id="b01dd-182">Manage SharePoint Online with Office 365 PowerShell</span></span>](create-sharepoint-sites-and-add-users-with-powershell.md)

[<span data-ttu-id="b01dd-183">Office 365 PowerShell을 사용하여 Office 365 관리</span><span class="sxs-lookup"><span data-stu-id="b01dd-183">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="b01dd-184">Office 365 PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="b01dd-184">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

