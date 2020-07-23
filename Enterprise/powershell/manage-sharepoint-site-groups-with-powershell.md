---
title: PowerShell을 사용 하 여 SharePoint Online 사이트 그룹 관리
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/17/2019
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
- SPO_Content
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: '요약: PowerShell을 사용 하 여 SharePoint Online 사이트 그룹을 관리 합니다.'
ms.openlocfilehash: bee1f01ae78ec35d34a6aba0119bba3fbf7eeada
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230494"
---
# <a name="manage-sharepoint-online-site-groups-with-powershell"></a><span data-ttu-id="66bc4-103">PowerShell을 사용 하 여 SharePoint Online 사이트 그룹 관리</span><span class="sxs-lookup"><span data-stu-id="66bc4-103">Manage SharePoint Online site groups with PowerShell</span></span>

<span data-ttu-id="66bc4-104">*이 문서는 Microsoft 365 Enterprise 및 Office 365 Enterprise에 모두 적용 됩니다.*</span><span class="sxs-lookup"><span data-stu-id="66bc4-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="66bc4-105">Microsoft 365 관리 센터를 사용할 수도 있지만 Microsoft 365 용 PowerShell을 사용 하 여 SharePoint Online 사이트 그룹을 관리할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66bc4-105">Although you can use the Microsoft 365 admin center, you can also use PowerShell for Microsoft 365 to manage your SharePoint Online site groups.</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="66bc4-106">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="66bc4-106">Before you begin</span></span>

<span data-ttu-id="66bc4-107">이 문서의 절차를 수행 하려면 SharePoint Online에 연결 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="66bc4-107">The procedures in this article require you to connect to SharePoint Online.</span></span> <span data-ttu-id="66bc4-108">자세한 내용은 [SharePoint Online PowerShell에 연결을](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="66bc4-108">For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span></span>

## <a name="view-sharepoint-online-with-powershell-for-microsoft-365"></a><span data-ttu-id="66bc4-109">Microsoft 365 용 PowerShell을 사용 하 여 SharePoint Online 보기</span><span class="sxs-lookup"><span data-stu-id="66bc4-109">View SharePoint Online with PowerShell for Microsoft 365</span></span>

<span data-ttu-id="66bc4-110">SharePoint Online 관리 센터에는 사이트 그룹을 관리 하기 위한 사용 하기 쉬운 몇 가지 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66bc4-110">The SharePoint Online admin center has some easy-to-use methods for managing site groups.</span></span> <span data-ttu-id="66bc4-111">예를 들어 사이트의 그룹 및 그룹 구성원을 확인 하려는 경우를 가정해 보겠습니다 `https://litwareinc.sharepoint.com/sites/finance` .</span><span class="sxs-lookup"><span data-stu-id="66bc4-111">For example, suppose you want to look at the groups, and the group members, for the `https://litwareinc.sharepoint.com/sites/finance` site.</span></span> <span data-ttu-id="66bc4-112">수행 해야 하는 작업은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="66bc4-112">Here’s what you have to do to:</span></span>

1. <span data-ttu-id="66bc4-113">SharePoint 관리 센터에서 **활성 사이트**를 클릭 한 다음 사이트의 URL을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="66bc4-113">From the SharePoint admin center, click **Active sites**, and then click the URL of the site.</span></span>
2. <span data-ttu-id="66bc4-114">사이트 페이지에서 페이지 오른쪽 위 모서리에 있는 **설정** 아이콘을 클릭 한 다음 **사이트 사용 권한을**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="66bc4-114">On the site page, click the **Settings** icon (located in the upper right-hand corner of the page), and then click **Site permissions**.</span></span>

<span data-ttu-id="66bc4-115">확인하려는 다음 사이트에 대해 프로세스를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="66bc4-115">And then repeat the process for the next site you want to look at.</span></span>

<span data-ttu-id="66bc4-116">Microsoft 365 용 PowerShell을 사용 하 여 그룹 목록을 가져오려면 다음 명령을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66bc4-116">To get a list of the groups with PowerShell for Microsoft 365, you can use the following commands:</span></span>

```powershell
$siteURL = "https://litwareinc.sharepoint.com/sites/finance"
$x = Get-SPOSiteGroup -Site $siteURL
foreach ($y in $x)
    {
        Write-Host $y.Title -ForegroundColor "Yellow"
        Get-SPOSiteGroup -Site $siteURL -Group $y.Title | Select-Object -ExpandProperty Users
        Write-Host
    }
```

<span data-ttu-id="66bc4-117">SharePoint Online 관리 셸 명령 프롬프트에서이 명령 집합을 실행 하는 방법에는 두 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66bc4-117">There are two ways to run this command set in the SharePoint Online Management Shell command prompt:</span></span>

- <span data-ttu-id="66bc4-118">메모장 (또는 다른 텍스트 편집기)에 명령을 복사 하 고 **$siteURL** 변수의 값을 수정한 다음 명령을 선택 하 여 SharePoint Online 관리 셸 명령 프롬프트에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="66bc4-118">Copy the commands into Notepad (or another text editor), modify the value of the **$siteURL** variable, select the commands, and then paste them into the SharePoint Online Management Shell command prompt.</span></span> <span data-ttu-id="66bc4-119">이렇게 하면 PowerShell이 프롬프트에서 중지 됩니다 **>>** .</span><span class="sxs-lookup"><span data-stu-id="66bc4-119">When you do, PowerShell will stop at a **>>** prompt.</span></span> <span data-ttu-id="66bc4-120">Enter 키를 눌러 `foreach` 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="66bc4-120">Press Enter to execute the `foreach` command.</span></span><br/>
- <span data-ttu-id="66bc4-121">메모장 (또는 다른 텍스트 편집기)에 명령을 복사 하 고 **$siteURL** 변수의 값을 수정한 다음이 텍스트 파일을 적절 한 폴더에 이름을 지정 하 고 ps1 확장명을 사용 하 여 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="66bc4-121">Copy the commands into Notepad (or another text editor), modify the value of the **$siteURL** variable, and then save this text file with a name and the .ps1 extension in a suitable folder.</span></span> <span data-ttu-id="66bc4-122">다음으로, 경로와 파일 이름을 지정 하 여 SharePoint Online 관리 셸 명령 프롬프트에서 스크립트를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="66bc4-122">Next, run the script from the SharePoint Online Management Shell command prompt by specifying its path and file name.</span></span> <span data-ttu-id="66bc4-123">예제 명령은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="66bc4-123">Here is an example command:</span></span>

```powershell
C:\Scripts\SiteGroupsAndUsers.ps1
```

<span data-ttu-id="66bc4-124">두 경우 모두에 다음과 같은 내용이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="66bc4-124">In both cases, you should see something similar to this:</span></span>

![SharePoint Online 사이트 그룹](media/SPO-site-groups.png)

<span data-ttu-id="66bc4-126">사이트에 대해 만들어진 모든 그룹 `https://litwareinc.sharepoint.com/sites/finance` 및 해당 그룹에 할당 된 모든 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="66bc4-126">These are all the groups that have been created for the site `https://litwareinc.sharepoint.com/sites/finance`, and all the users assigned to those groups.</span></span> <span data-ttu-id="66bc4-127">그룹 이름은 노란색으로 되어 그룹 이름을 해당 구성원 으로부터 구분 하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="66bc4-127">The group names are in yellow to help you separate group names from their members.</span></span>

<span data-ttu-id="66bc4-128">또 다른 예로, 모든 SharePoint Online 사이트에 대 한 그룹 및 모든 그룹 구성원 자격이 나열 된 명령 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="66bc4-128">As another example, here is a command set that lists the groups, and all the group memberships, for all of your SharePoint Online sites.</span></span>

```powershell
$x = Get-SPOSite
foreach ($y in $x)
    {
        Write-Host $y.Url -ForegroundColor "Yellow"
        $z = Get-SPOSiteGroup -Site $y.Url
        foreach ($a in $z)
            {
                 $b = Get-SPOSiteGroup -Site $y.Url -Group $a.Title 
                 Write-Host $b.Title -ForegroundColor "Cyan"
                 $b | Select-Object -ExpandProperty Users
                 Write-Host
            }
    }
```
    
## <a name="see-also"></a><span data-ttu-id="66bc4-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="66bc4-129">See also</span></span>

[<span data-ttu-id="66bc4-130">SharePoint Online PowerShell에 연결</span><span class="sxs-lookup"><span data-stu-id="66bc4-130">Connect to SharePoint Online PowerShell</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[<span data-ttu-id="66bc4-131">SharePoint Online 사이트 만들기 및 PowerShell을 사용 하 여 사용자 추가</span><span class="sxs-lookup"><span data-stu-id="66bc4-131">Create SharePoint Online sites and add users with PowerShell</span></span>](create-sharepoint-sites-and-add-users-with-powershell.md)

[<span data-ttu-id="66bc4-132">PowerShell을 사용 하 여 SharePoint Online 사용자 및 그룹 관리</span><span class="sxs-lookup"><span data-stu-id="66bc4-132">Manage SharePoint Online users and groups with PowerShell</span></span>](manage-sharepoint-users-and-groups-with-powershell.md)

[<span data-ttu-id="66bc4-133">PowerShell을 사용 하 여 Microsoft 365 관리</span><span class="sxs-lookup"><span data-stu-id="66bc4-133">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="66bc4-134">Microsoft 365 용 PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="66bc4-134">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)

