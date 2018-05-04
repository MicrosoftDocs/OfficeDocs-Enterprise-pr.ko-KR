---
title: Office 365 PowerShell을 사용하여 SharePoint Online 사용자 및 그룹 관리
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/01/2018
ms.audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: '요약: SharePoint Online 사용자, 그룹 및 사이트를 관리 하려면 Office 365 PowerShell를 사용 합니다.'
ms.openlocfilehash: 8ed40d2c736853145e21f0f9852bdb18c7842075
ms.sourcegitcommit: 74cdb2534bce376abc9cf4fef85ff039c46ee790
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="manage-sharepoint-online-users-and-groups-with-office-365-powershell"></a><span data-ttu-id="9b6ad-103">Office 365 PowerShell을 사용하여 SharePoint Online 사용자 및 그룹 관리</span><span class="sxs-lookup"><span data-stu-id="9b6ad-103">Manage SharePoint Online users and groups with Office 365 PowerShell</span></span>

 <span data-ttu-id="9b6ad-104">**요약:** Office 365 PowerShell을 사용 하 여 SharePoint Online 사용자, 그룹 및 사이트를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b6ad-104">**Summary:** Use Office 365 PowerShell to manage SharePoint Online users, groups, and sites.</span></span>

<span data-ttu-id="9b6ad-105">SharePoint Online 작동 하는 사용자 계정 또는 그룹의 큰 목록 및가 보다 쉽게 관리할 수 있는 경우에 Office 365 PowerShell을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b6ad-105">If you are a SharePoint Online who works with large lists of user accounts or groups and wants an easier way to manage them, you can use Office 365 PowerShell.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="9b6ad-106">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="9b6ad-106">Before you begin</span></span>

<span data-ttu-id="9b6ad-p101">이 항목의 절차에서는 SharePoint Online에 연결 해야 합니다. 자세한 내용은 [Connect to SharePoint Online PowerShell를](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps) 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="9b6ad-p101">The procedures in this topic require you to connect to SharePoint Online. For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span></span>

## <a name="get-a-list-of-sites-groups-and-users"></a><span data-ttu-id="9b6ad-109">사이트, 그룹, 사용자 목록 가져오기</span><span class="sxs-lookup"><span data-stu-id="9b6ad-109">Get a list of sites, groups, and users</span></span>

<span data-ttu-id="9b6ad-p102">사용자 및 그룹 관리를 시작하려면 먼저 사이트, 그룹 및 사용자 목록을 가져와야 합니다. 그리고 나면 해당 정보를 이 문서의 예제 전반에 걸쳐 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b6ad-p102">Before we start to manage users and groups, you need to get lists of your sites, groups, and users. You can then use this information to work through the example in this article.</span></span>

### <a name="get-a-list-of-sites"></a><span data-ttu-id="9b6ad-112">사이트 목록 가져오기</span><span class="sxs-lookup"><span data-stu-id="9b6ad-112">Get a list of sites</span></span>

<span data-ttu-id="9b6ad-113">이 명령을 사용하여 테넌트의 사이트 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9b6ad-113">Get a list of the sites in your tenant with this command:</span></span>

```
Get-SPOSite
```

### <a name="get-a-list-of-groups"></a><span data-ttu-id="9b6ad-114">그룹 목록 가져오기</span><span class="sxs-lookup"><span data-stu-id="9b6ad-114">Get a list of groups</span></span>

<span data-ttu-id="9b6ad-115">이 명령을 사용하여 테넌트의 그룹 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9b6ad-115">Get a list of the groups in your tenant with this command:</span></span>

```
Get-SPOSite | ForEach-Object {Get-SPOSiteGroup -Site $_.Url} |Format-Table
```

### <a name="get-a-list-of-users"></a><span data-ttu-id="9b6ad-116">사용자 목록 가져오기</span><span class="sxs-lookup"><span data-stu-id="9b6ad-116">Get a list of users</span></span>

<span data-ttu-id="9b6ad-117">이 명령을 사용하여 테넌트의 사용자 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9b6ad-117">Get a list of the users in your tenant with this command:</span></span>

```Get-SPOSite | ForEach-Object {Get-SPOUser -Site $_.Url}```

## <a name="add-a-user-to-the-site-collection-administrators-group"></a><span data-ttu-id="9b6ad-118">사이트 모음 관리자 그룹에 사용자 추가</span><span class="sxs-lookup"><span data-stu-id="9b6ad-118">Add a user to the Site Collection Administrators group</span></span>

<span data-ttu-id="9b6ad-p103">**Set-spouser** 명령을 사용 하 여 사이트 모음에서 사이트 모음 관리자의 목록에 사용자를 추가 합니다. 다음은 구문을 표시 하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="9b6ad-p103">You use the **Set-SPOUser** command to add a user to the list of Site Collection Administrators on a site collection. This is how the syntax looks:</span></span>

```
$tenant = "tenant"
<!--This is the Tenant Name. Value must be enclosed in double quotation marks. Example: "Contoso01"-->
$site = "site"
<!--# This is the Site name. Value must be enclosed in double quotation marks. Example: "contosotest"-->
$user = "loginname"
<!--This is the users login name. Value must be enclosed in double quotation marks. Example "opalc"-->
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.onmicrosoft.com -IsSiteCollectionAdmin $true
 ```

<span data-ttu-id="9b6ad-121">이 예제에서는 변수를 사용 하 여 값을 저장 하 고 스크립트에서 메모에 (예 "<!--This is the Tenant Name…-->") 해야 해당 값을 파악할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b6ad-121">This example uses variables to store values and has notes in the script (for example "<!--This is the Tenant Name…-->") to help you understand what those values should be.</span></span>

<span data-ttu-id="9b6ad-122">예,이 명령 집합에 추가 하는 Opal Castillo (사용자 이름 opalc) 사이트 모음 관리자의 목록 contoso1 테 넌 트의 ContosoTest 사이트 모음:</span><span class="sxs-lookup"><span data-stu-id="9b6ad-122">For example, this set of commands adds Opal Castillo (user name opalc) the list of Site Collection Administrators on the ContosoTest site collection in the contoso1 tenancy:</span></span>

```
$tenant = "contoso1"
$site = "contosotest"
$user = "opalc"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.onmicrosoft.com -IsSiteCollectionAdmin $true
```

<span data-ttu-id="9b6ad-123">실제로 이러한 명령을 잘라내 메모장에 붙여넣고 사용 중인 환경에서 $tenant, $site, $user 변수 값을 변경한 다음 SharePoint Online 관리 셸 창에 붙여넣을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b6ad-123">You can actually cut and paste these commands into Notepad, change the variable values for $tenant, $site, and $user to actual values from your environment, and then paste this into your SharePoint Online Management Shell window.</span></span>

## <a name="add-a-user-to-other-site-collection-administrators-groups"></a><span data-ttu-id="9b6ad-124">다른 사이트 모음 관리자 그룹에 사용자 추가</span><span class="sxs-lookup"><span data-stu-id="9b6ad-124">Add a user to other Site Collection Administrators groups</span></span>

<span data-ttu-id="9b6ad-p104">이 작업에서는 하겠습니다 사용 하 여 **Add-spouser** 명령을 사이트 모음에서 SharePoint 그룹에 사용자를 추가 합니다. 다음은 구문을 표시 하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="9b6ad-p104">In this task, we'll use the **Add-SPOUser** command to add a user to a SharePoint group on a site collection. This is how the syntax looks:</span></span>

```
$tenant = "tenant"
<!--This is the Tenant Name. Value must be enclosed in double quotation marks. Example: "Contoso01"-->
$site = "site"
<!--This is the Site name. Value must be enclosed in double quotation marks. Example: "contosotest"-->
$user = "loginname"
<!--This is the users login name. Value must be enclosed in double quotation marks. Example: "opalc"-->
$group = "group"
<!--This is the SharePoint security Group name. Value must be enclosed in double quotation marks. Example: "Auditors"-->
Add-SPOUser -Group $group -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site

```

<span data-ttu-id="9b6ad-127">예, 보겠습니다 협곡 투성이 (사용자 이름 glenr) 그룹에 추가 감사자 contoso1 테 넌 트의 ContosoTest 사이트 모음에서:</span><span class="sxs-lookup"><span data-stu-id="9b6ad-127">For example, let’s add Glen Rife (user name glenr) to the Auditors group on the ContosoTest site collection in the contoso1 tenancy:</span></span>

```
$tenant = "contoso1"
$site = "contosotest"
$user = "glenr"
$group = "Auditors"
Add-SPOUser -Group $group -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="create-a-site-collection-group"></a><span data-ttu-id="9b6ad-128">사이트 모음 그룹 만들기</span><span class="sxs-lookup"><span data-stu-id="9b6ad-128">Create a site collection group</span></span>

<span data-ttu-id="9b6ad-p105">**Set-spositegroup** 명령을 사용 하 여 새 SharePoint 그룹 만들기 및 ContosoTest 사이트 모음에 추가 합니다. 다음은 구문을 표시 하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="9b6ad-p105">You use the **Set-SPOSiteGroup** command to create a new SharePoint group and add it to the ContosoTest site collection. This is how the syntax looks:</span></span>

```
$tenant = "tenant"
<!--This is the Tenant Name. Value must be enclosed in double quotation marks, Example: "Contoso01"-->
$site = "site"
<!--This is the Site name. Value must be enclosed in double quotation marks, Example: "contosotest"-->
$group = "group"
<!--This is the SharePoint security Group name. Value must be enclosed in double quotation marks, Example: "Auditors"-->
$level = "permission level"
<!--This is the level of permissions to assign to the group. Value must be enclosed in double quotation marks, Example: "View Only"-->
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```

> [!IMPORTANT]
> <span data-ttu-id="9b6ad-p106">따옴표로 공백이 포함 된 모든 문자열을 묶어야 합니다. **Set-spositegroup** cmdlet을 사용 하 여 사용 권한 수준 등의 그룹 속성을 나중에 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b6ad-p106">You must enclose any string with spaces in quotation marks. Group properties, such as permission levels, can be updated later by using the **Set-SPOSiteGroup** cmdlet.</span></span>

<span data-ttu-id="9b6ad-133">예, contoso1 테 넌 시에서 Contoso 테스트 사이트 모음에 추가 보기 전용 권한이 있는 감사자 그룹 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="9b6ad-133">For example, let’s add the Auditors group with View Only permissions to the Contoso Test site collection in the contoso1 tenancy:</span></span>

```
$tenant = "contoso1"
$site = "Contoso Test"
$level = "View Only"
$group = "Auditors"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="remove-users-from-a-group"></a><span data-ttu-id="9b6ad-134">그룹에서 사용자 제거</span><span class="sxs-lookup"><span data-stu-id="9b6ad-134">Remove users from a group</span></span>

<span data-ttu-id="9b6ad-p107">사이트 하나 또는 모든 사이트에서 사용자를 제거해야 하는 경우가 있습니다. 직원이 사업부를 이동하거나 퇴사하는 경우를 예로 들 수 있습니다. 직원이 한 명이라면 UI에서 이 작업을 쉽게 수행할 수 있습니다. 그러나 전체 사업부를 사이트 간에 이동해야 하는 경우에는 쉽지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9b6ad-p107">Sometimes you have to remove a user from a site or even all sites. Perhaps the employee moves from one division to another or leaves the company. You can do this for one employee easily in the UI, but this is not easily done when you have to move a complete division from one site to another.</span></span>

<span data-ttu-id="9b6ad-p108">그러나 SharePoint Online 관리 셸 및 CSV 파일을 사용 하 여이 빠르고 쉽게 합니다. 이 작업에서 사이트 모음 보안 그룹에서 사용자를 제거 하려면 Windows PowerShell을 사용 합니다. 그런 다음 CSV 파일을 사용 하 고 다른 사이트에서 많은 사용자를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b6ad-p108">However by using the SharePoint Online Management Shell and CSV files, this is fast and easy. In this task, you'll use Windows PowerShell to remove a user from a site collection security group. Then you'll use a CSV file and remove lots of users from different sites.</span></span> 

<span data-ttu-id="9b6ad-p109">**Remove-spouser** 명령을 명령 구문을 볼 수 있도록 사이트 모음 그룹에서 단일 Office 365 사용자를 제거 하려면 사용할 것 것입니다. 구문을 표시 되는 모양을 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9b6ad-p109">We'll be using the **Remove-SPOUser** command to remove a single Office 365 user from a site collection group just so we can see the command syntax. Here is how the syntax looks:</span></span>

```
$tenant = "tenant"
<!--This is the Tenant Name. Value must be enclosed in double quotation marks, Example: "Contoso01"-->
$site = "site"
<!--This is the Site name. Value must be enclosed in double quotation marks, Example: "contosotest"-->
$group = "group"
<!--This is the SharePoint security Group name. Value must be enclosed in double quotation marks, Example: "Auditors"-->
$user = "loginname"
<!--This is the user’s login name. Value must be enclosed in double quotation marks, Example: "opalc"-->
Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site
```

<span data-ttu-id="9b6ad-143">예, contoso1 테 넌 시에서 Contoso 테스트 사이트 모음에서 사이트 모음 감사자 그룹에서 제거 Bobby Overby 보겠습니다 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b6ad-143">For example, let’s remove Bobby Overby from the site collection Auditors group in the Contoso Test site collection in the contoso1 tenancy:</span></span>

```
$tenant = "contoso1"
$site = "contosotest"
$user = "bobbyo"
$group = "Auditors"
Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```

<span data-ttu-id="9b6ad-p110">다음으로는 Bobby를 현재 포함되어 있는 모든 그룹에서 제거해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="9b6ad-p110">Suppose we wanted to remove Bobby from all the groups he is currently in. Here is how we would do that:</span></span>

```
$tenant = "contoso1"
$user = "bobbyo"
Get-SPOSite | ForEach-Object {Get-SPOSiteGroup –Site $_.Url} | ForEach-Object {Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site &_.Url}
```

> [!WARNING]
> <span data-ttu-id="9b6ad-p111">이 스크립트는 작업 방법을 설명하기 위한 용도로만 제공됩니다. 실제로 사용자가 퇴사하는 경우 등 모든 그룹에서 사용자를 제거해야 하는 경우가 아니면 이 명령을 실행해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b6ad-p111">This is just to show how to do this. You should not run this command unless you really have to remove a user from every group, for example if the user leaves the company.</span></span>

## <a name="automate-management-of-large-lists-of-users-and-groups"></a><span data-ttu-id="9b6ad-148">대형 사용자 및 그룹 목록의 관리 자동화</span><span class="sxs-lookup"><span data-stu-id="9b6ad-148">Automate management of large lists of users and groups</span></span>

<span data-ttu-id="9b6ad-p112">SharePoint 사이트에 많은 수의 계정 추가 및 사용 권한을 부여할 Office 365 관리 센터, 개별 PowerShell 명령 또는 PowerShell를 사용할 수 있는 CSV 파일입니다. 이러한 선택 항목 중 CSV 파일이이 작업을 자동화 하는 가장 빠른 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="9b6ad-p112">To add a large number of accounts to SharePoint sites and give them permissions, you can use the Office 365 admin center, individual PowerShell commands, or PowerShell an a CSV file. Of these choices, the CSV file is the fastest way to automate this task.</span></span>

<span data-ttu-id="9b6ad-p113">기본 프로세스에 해당 하는 Windows PowerShell 스크립트 필요한 매개 변수는 헤더 (열)를 가진 CSV 파일을 만드는 것입니다. Excel에서 이러한 목록의 쉽게 만들 수 있으며 다음 CSV 파일로 내보낼 수 있습니다. Windows PowerShell 스크립트를 사용 하 여 그룹 및 사이트에 그룹에 사용자 추가 (영문) CSV 파일의 레코드 (행)를 통해 반복 하는 다음 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b6ad-p113">The basic process is to create a CSV file that has headers (columns) that correspond to the parameters that the Windows PowerShell script needs. You can easily create such a list in Excel and then export it as a CSV file. Then, you use a Windows PowerShell script to iterate through records (rows) in the CSV file, adding the users to groups and the groups to sites.</span></span> 

<span data-ttu-id="9b6ad-p114">예를 들어 사이트 모음, 그룹 및 사용 권한 그룹을 정의하는 CSV 파일을 만들어 보겠습니다. 다음으로는 CSV 파일을 만들어 그룹에 사용자를 채웁니다. 마지막으로 그룹을 만들고 채우는 간단한 Windows PowerShell 스크립트를 만들어 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="9b6ad-p114">For example, let’s create a CSV file to define a group of site collections, groups, and permissions. Next, we will create a CSV file to populate the groups with users. Finally, we will create and run a simple Windows PowerShell script that creates and populates the groups.</span></span>

<span data-ttu-id="9b6ad-157">다음과 같은 구조의 첫 번째 CSV 파일은 하나 이상의 그룹을 하나 이상의 사이트 모음에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="9b6ad-157">The first CSV file will add one or more groups to one or more site collections and will have this structure:</span></span>

### <a name="header"></a><span data-ttu-id="9b6ad-158">머리글:</span><span class="sxs-lookup"><span data-stu-id="9b6ad-158">Header:</span></span>

```
Site,Group,PermissionLevels
```

### <a name="item"></a><span data-ttu-id="9b6ad-159">항목:</span><span class="sxs-lookup"><span data-stu-id="9b6ad-159">Item:</span></span>

```
https://tenant.sharepoint.com/sites/site,site collection,group,level
```

<span data-ttu-id="9b6ad-160">예제 파일은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9b6ad-160">Here is an example file:</span></span>

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

<span data-ttu-id="9b6ad-161">다음과 같은 구조의 두 번째 CSV 파일은 한 명 이상의 사용자를 하나 이상의 그룹에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="9b6ad-161">The second CSV file will add one or more users to one or more groups and will have this structure:</span></span>

### <a name="header"></a><span data-ttu-id="9b6ad-162">머리글:</span><span class="sxs-lookup"><span data-stu-id="9b6ad-162">Header:</span></span>

```
Group,LoginName,Site
```

### <a name="item"></a><span data-ttu-id="9b6ad-163">항목:</span><span class="sxs-lookup"><span data-stu-id="9b6ad-163">Item:</span></span>

```
group,login,https://tenant.sharepoint.com/sites/site
```

<span data-ttu-id="9b6ad-164">예제 파일은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9b6ad-164">Here is an example file:</span></span>

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

<span data-ttu-id="9b6ad-p115">그런 다음 해당 드라이브에 CSV 파일 두 개가 저장되어 있어야 합니다. 다음 명령은 두 CSV 파일을 모두 사용하여 권한 및 그룹 멤버십을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="9b6ad-p115">For the next step, you must have the two CSV files saved to your drive. Here are the commands that use both CSV files and to add permissions and group membership:</span></span>

```
Import-Csv C:\O365Admin\GroupsAndPermissions.csv | ForEach-Object {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\O365Admin\Users.csv | ForEach-Object {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```

<span data-ttu-id="9b6ad-p116">스크립트는 CSV 파일 내용을 가져오고 (굵게)에서 열에 값을 사용 하 여 **새로 SPOSiteGroup** 및 **Add-spouser** 명령의 매개 변수를 채웁니다. 이 예제에서는 C 드라이브에 저장 되는 있지만 원하는 위치에 관계 없이 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b6ad-p116">The script imports the CSV file contents and uses the values in the columns (in bold) to populate the parameters of the **New-SPOSiteGroup** and **Add-SPOUser** commands. In our example, we are saving this to the drive C, but you can save it wherever you want.</span></span>

<span data-ttu-id="9b6ad-p117">다음으로 동일한 CSV 파일을 사용해 서로 다른 사이트의 여러 그룹에서 사용자 여러 명을 제거해 보겠습니다. 명령은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9b6ad-p117">Now, let’s remove a bunch of people for several groups in different sites using the same CSV file. Here is the command:</span></span>

```
Import-Csv C:\O365Admin\Users.csv | ForEach-Object {Remove-SPOUser -LoginName $_.LoginName -Site $_.Site -Group $_.Group}
```

## <a name="generate-user-reports"></a><span data-ttu-id="9b6ad-171">사용자 보고서 생성</span><span class="sxs-lookup"><span data-stu-id="9b6ad-171">Generate user reports</span></span>

<span data-ttu-id="9b6ad-p118">사이트 몇 개에 대해 간단한 보고서를 가져와 해당 사이트의 사용자, 사용자의 사용 권한 수준 및 기타 속성을 표시할 수 있습니다. 이 작업을 위한 구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9b6ad-p118">You might want to get a simple report for a few sites and display the users for those sites, their permission level, and other properties. This is how the syntax looks:</span></span>

```
$tenant = "tenant"
<!--This is the Tenant Name. Value must be enclosed in double quotes, Example: "Contoso01"-->
$site = "site"
<!--This is the Site name. Value must be enclosed in double quotes, Example: "contosotest"-->
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | select * | Format-table -Wrap -AutoSize | Out-File c\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="9b6ad-p119">이러한 세 사이트에 대 한 데이터를 가져오려면 그러면 되 고 해당 사용자의 로컬 드라이브에 텍스트 파일에 쓰기. 이때 매개 변수는-Append 기존 파일에 새 콘텐츠를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b6ad-p119">This will grab the data for these three sites and write them to a text file on your local drive. Note that the parameter –Append will add new content to an existing file.</span></span>

<span data-ttu-id="9b6ad-176">예를 들어 Contoso1 테넌트의 ContosoTest, TeamSite01 및 Project01 사이트에 대한 보고서를 실행해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="9b6ad-176">For example, let's run a report on the ContosoTest, TeamSite01, and Project01 sites for the Contoso1 tenant:</span></span>

```
$tenant = "contoso1"
$site = "contosotest"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "TeamSite01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site |Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "Project01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="9b6ad-p120">참고만 **$site** 변수를 변경 해야 합니다. 명령의 세 연속 영역이 모두을 통해 해당 값을 유지 하는 **$tenant** 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="9b6ad-p120">Note that we had to change only the **$site** variable. The **$tenant** variable keeps its value through all three runs of the command.</span></span>

<span data-ttu-id="9b6ad-p121">모든 사이트에 대해 이 작업을 수행하려는 경우 다음 명령을 사용하면 모든 웹 사이트를 입력하지 않고도 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b6ad-p121">However, what if you wanted to do this for every site? You can do this without having to type all those websites by using this command:</span></span>

```
Get-SPOSite | ForEach-Object {Get-SPOUser –Site $_.Url} | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="9b6ad-p122">이 보고서는 매우 간단 하 고 더 많은 보다 구체적인 보고서 또는 보다 자세한 정보를 포함 하는 보고서를 만드는 코드를 추가할 수 있습니다. 하지만이 방법을 사용 해야 SharePoint 온라인 환경에서 사용자를 관리 하려면 SharePoint Online 관리 셸을 사용 하는 방법의 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b6ad-p122">This report is fairly simple, and you can add more code to create more specific reports or reports that include more detailed information. But this should give you an idea of how to use the SharePoint Online Management Shell to manage users in the SharePoint Online environment.</span></span>
   
## <a name="see-also"></a><span data-ttu-id="9b6ad-183">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9b6ad-183">See also</span></span>

[<span data-ttu-id="9b6ad-184">SharePoint Online PowerShell에 연결</span><span class="sxs-lookup"><span data-stu-id="9b6ad-184">Connect to SharePoint Online PowerShell</span></span>](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[<span data-ttu-id="9b6ad-185">Office 365 PowerShell을 사용하여 SharePoint Online 관리</span><span class="sxs-lookup"><span data-stu-id="9b6ad-185">Manage SharePoint Online with Office 365 PowerShell</span></span>](create-sharepoint-sites-and-add-users-with-powershell.md)

[<span data-ttu-id="9b6ad-186">Office 365 PowerShell 사용한 Office 365 관리</span><span class="sxs-lookup"><span data-stu-id="9b6ad-186">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="9b6ad-187">Office 365 PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="9b6ad-187">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

