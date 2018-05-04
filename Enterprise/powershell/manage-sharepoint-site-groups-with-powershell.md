---
title: Office 365 PowerShell을 사용한 SharePoint Online 사이트 그룹 관리
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
description: '요약: SharePoint Online 사이트 그룹을 관리 하려면 Office 365 PowerShell를 사용 합니다.'
ms.openlocfilehash: 68be9ce3ef26cb46df6d43716c6719ffd9c172e2
ms.sourcegitcommit: 74cdb2534bce376abc9cf4fef85ff039c46ee790
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="manage-sharepoint-online-site-groups-with-office-365-powershell"></a><span data-ttu-id="da9a1-103">Office 365 PowerShell을 사용한 SharePoint Online 사이트 그룹 관리</span><span class="sxs-lookup"><span data-stu-id="da9a1-103">Manage SharePoint Online site groups with Office 365 PowerShell</span></span>

 <span data-ttu-id="da9a1-104">**요약:** SharePoint Online 사이트 그룹을 관리 하려면 Office 365 PowerShell을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="da9a1-104">**Summary:** Use Office 365 PowerShell to manage SharePoint Online site groups.</span></span>
  
<span data-ttu-id="da9a1-105">Office 365 관리 센터를 사용할 수 있지만 SharePoint Online 사이트 그룹을 관리 하려면 Office 365 PowerShell를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da9a1-105">Although you can use the Office 365 admin center, you can also use Office 365 PowerShell to manage your SharePoint Online site groups.</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="da9a1-106">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="da9a1-106">Before you begin</span></span>

<span data-ttu-id="da9a1-p101">이 문서의 절차에서는 SharePoint Online에 연결 해야 합니다. 자세한 내용은 [SharePoint Online PowerShell 연결](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="da9a1-p101">The procedures in this article require you to connect to SharePoint Online. For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span></span>

## <a name="view-sharepoint-online-with-office-365-powershell"></a><span data-ttu-id="da9a1-109">Office 365 PowerShell 사용 하 여 보기 SharePoint를 온라인</span><span class="sxs-lookup"><span data-stu-id="da9a1-109">View SharePoint Online with Office 365 PowerShell</span></span>

<span data-ttu-id="da9a1-p102">SharePoint Online 관리 센터에 사이트 그룹을 관리 하기 위한 일부 사용 하기 쉬운 메서드가 있습니다. 예, 그룹 및 그룹 구성원에 대 한 확인 하려는 경우를 가정해 보겠습니다는 https://litwareinc.sharepoint.com/sites/finance 사이트입니다. 다음을 수행 해야하는 작업은입니다.</span><span class="sxs-lookup"><span data-stu-id="da9a1-p102">The SharePoint Online admin center has some easy-to-use methods for managing site groups. For example, suppose you want to look at the groups, and the group members, for the https://litwareinc.sharepoint.com/sites/finance site. Here’s what you have to do to:</span></span>

1. <span data-ttu-id="da9a1-113">Office 365 관리 센터에서 **자원**을 클릭 > **사이트**를 한 다음 사이트의 URL을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="da9a1-113">From the Office 365 admin center, click **Resources** > **Sites**, and then click the URL of the site.</span></span>
2. <span data-ttu-id="da9a1-114">사이트 모음 대화 상자에서 **이 사이트로 이동**합니다.를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="da9a1-114">In the site collection dialog box, click **Go to this site**.</span></span>
3. <span data-ttu-id="da9a1-115">사이트 페이지에서 (페이지의 오른쪽 상단 모서리에 있음) **설정** 아이콘을 클릭 한 다음 **사이트 설정**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="da9a1-115">On the site page, click the **Settings** icon (located in the upper right-hand corner of the page) and then click **Site settings**:</span></span></br>
<span data-ttu-id="da9a1-116">![SharePoint Online 사이트 설정](images/spo-site-settings.png)</span><span class="sxs-lookup"><span data-stu-id="da9a1-116">![SharePoint Online site settings](images/spo-site-settings.png)</span></span></br>
4. <span data-ttu-id="da9a1-117">사이트 설정 페이지의 **사용자 및 사용 권한에서** **사이트 사용 권한** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="da9a1-117">On the Site Settings page, click **Sites permissions** under **Users and Permissions**.</span></span>

<span data-ttu-id="da9a1-118">확인하려는 다음 사이트에 대해 프로세스를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="da9a1-118">And then repeat the process for the next site you want to look at.</span></span>

<span data-ttu-id="da9a1-119">Office 365 powershell 그룹의 목록을 가져오려면, 하려면 다음 명령 집합을 사용 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da9a1-119">To get a list of the groups with Office 365 PowerShell, you would use the following command set:</span></span>

```
$siteURL = "https://litwareinc.sharepoint.com/sites/finance"
$x = Get-SPOSiteGroup -Site $siteURL
foreach ($y in $x)
    {
        Write-Host $y.Title -ForegroundColor "Yellow"
        Get-SPOSiteGroup -Site $siteURL -Group $y.Title | Select-Object -ExpandProperty Users
        Write-Host
    }
```

<span data-ttu-id="da9a1-120">두 가지 방법을 사용 하 여 SharePoint Online 관리 셸 명령 프롬프트에서 설정이 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da9a1-120">There are two ways to run this command set in the SharePoint Online Management Shell command prompt:</span></span>
- <span data-ttu-id="da9a1-p103">명령을 메모장 (또는 다른 텍스트 편집기)에 복사, **$siteURL** 변수의 값을 수정, 명령, 선택한 SharePoint Online 관리 셸 명령 프롬프트에 붙여넣습니다. PowerShell에서 중지를 수행 하면 한 >> 프롬프트 합니다. Enter 키를 눌러 실행 하 고 각 명령에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="da9a1-p103">Copy the commands into Notepad (or another text editor), modify the value of the **$siteURL** variable, select the commands, and then paste them into the SharePoint Online Management Shell command prompt. When you do, PowerShell will stop at a >> prompt. Press Enter to execute the for each command.</span></span></br>
- <span data-ttu-id="da9a1-p104">메모장 (또는 다른 텍스트 편집기)에 명령을 복사 하 고 **$siteURL** 변수의 값을 수정 이름과 적절 한 폴더에.ps1 확장명으로이 텍스트 파일을 저장 합니다. 다음으로, 해당 경로 파일 이름을 지정 하 여 SharePoint Online 관리 셸 명령 프롬프트에서 스크립트를 실행 합니다. 다음은 한 예가입니다.</span><span class="sxs-lookup"><span data-stu-id="da9a1-p104">Copy the commands into Notepad (or another text editor), modify the value of the **$siteURL** variable, and then save this text file with a name and the .ps1 extension in a suitable folder. Next, run the script from the SharePoint Online Management Shell command prompt by specifying its path and file name. Here is an example:</span></span></br>
```
C:\Scripts\SiteGroupsAndUsers.ps1
```</br>

In both cases, you should see something similar to this:

![SharePoint Online site groups](images/SPO-site-groups.png)

These are all the groups that have been created for the site https://litwareinc.sharepoint.com/sites/finance, as well as all the users assigned to those groups. The group names are in yellow to help you separate group names from their members.

As another example, here is a command set that lists the groups, and all the group memberships, for all of your SharePoint Online sites.

```
<span data-ttu-id="da9a1-127">$x Get-sposite foreach ($x에서 $y) = {쓰기 호스트 $y.Url-ForegroundColor "노란색" $z Get-spositegroup =-사이트 $y.Url foreach ($에서 $z) {$b Get-spositegroup =-$y.Url 사이트-그룹 $a.Title 쓰기 호스트 $b.Title-ForegroundColor "녹청" $b | 호스트-Select-object-ExpandProperty 사용자가 쓰기}을 (를)</span><span class="sxs-lookup"><span data-stu-id="da9a1-127">$x = Get-SPOSite foreach ($y in $x) { Write-Host $y.Url -ForegroundColor "Yellow" $z = Get-SPOSiteGroup -Site $y.Url foreach ($a in $z) { $b = Get-SPOSiteGroup -Site $y.Url -Group $a.Title Write-Host $b.Title -ForegroundColor "Cyan" $b | Select-Object -ExpandProperty Users Write-Host } }</span></span>
```
    
## See also

[Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[Create SharePoint Online sites and add users with Office 365 PowerShell](create-sharepoint-sites-and-add-users-with-powershell.md)

[Manage SharePoint Online users and groups with Office 365 PowerShell](manage-sharepoint-users-and-groups-with-powershell.md)

[Manage Office 365 with Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Getting started with Office 365 PowerShell](getting-started-with-office-365-powershell.md)

