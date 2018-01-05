---
title: "Office 365 PowerShell을 사용해야 하는 이유"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- DecEntMigration
ms.assetid: b3209b1a-40c7-4ede-8e78-8a88bb2adc8a
description: "요약: 경우에 따라 효율성을 높이기 위해 또는 필요에 의해 Office 365 PowerShell을 사용하여 Office 365를 관리해야 하는 이유를 파악합니다."
ms.openlocfilehash: 46295ed851f24b16f775fd48dc8cdfbce39bf76c
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2017
---
# <a name="why-you-need-to-use-office-365-powershell"></a><span data-ttu-id="ba446-103">Office 365 PowerShell을 사용해야 하는 이유</span><span class="sxs-lookup"><span data-stu-id="ba446-103">Why you need to use Office 365 PowerShell</span></span>

 <span data-ttu-id="ba446-104">**요약:** 경우에 따라 효율성을 높이기 위해 또는 필요에 의해 Office 365 PowerShell을 사용하여 Office 365를 관리해야 하는 이유를 파악합니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-104">Summary: Understand why you must use Office 365 PowerShell to manage Office 365, in some cases more efficiently and in other cases by necessity.</span></span>
  
<span data-ttu-id="ba446-p101">Office 365 관리 센터를 사용하면 Office 365 사용자 계정과 라이선스뿐 아니라 Office 365 서버 제품( Exchange, 비즈니스용 Skype 온라인, SharePoint Online)을 관리할 수 있습니다. 그러나 Office 365 PowerShell 명령을 사용하여 이러한 요소를 관리할 수도 있습니다, 이 경우 속도, 자동화 및 추가 기능을 위한 명령줄 및 스크립팅 언어 환경을 활용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-p101">With the Office 365 admin center, you can not only manage your Office 365 user accounts and licenses, but you can also manage your Office 365 server products: Exchange, Skype for Business Online, and SharePoint Online. However, you can also manage these elements with Office 365 PowerShell commands, taking advantage of a command-line and scripting language environment for speed, automation, and additional capability.</span></span>
  
<span data-ttu-id="ba446-107">이 문서에서는 Office 365 PowerShell을 사용하여 Office 365를 관리하는 다음과 같은 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-107">In this article, we'll show you these ways in which you can use Office 365 PowerShell to manage Office 365.</span></span>
  
- <span data-ttu-id="ba446-108">Office 365 PowerShell은 Office 365 관리 센터에서는 볼 수 없는 추가 정보를 제공할 수 있음</span><span class="sxs-lookup"><span data-stu-id="ba446-108">Office 365 PowerShell can reveal additional information that you cannot see with the Office 365 admin center</span></span>
    
- <span data-ttu-id="ba446-109">Office 365에는 Office 365 PowerShell로만 구성할 수 있는 기능이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-109">Office 365 has features that you can only configure by using Office 365 PowerShell</span></span>
    
- <span data-ttu-id="ba446-110">Office 365 PowerShell은 대량 작업을 수행하는 데 유용함</span><span class="sxs-lookup"><span data-stu-id="ba446-110">Office 365 PowerShell is great at performing bulk operations</span></span>
    
- <span data-ttu-id="ba446-111">Office 365 PowerShell은 데이터를 필터링하는 데 유용함</span><span class="sxs-lookup"><span data-stu-id="ba446-111">Office 365 PowerShell is great at filtering data</span></span>
    
- <span data-ttu-id="ba446-112">Office 365 PowerShell을 사용하면 데이터 쉽게 인쇄 또는 저장할 수 있음</span><span class="sxs-lookup"><span data-stu-id="ba446-112">Office 365 PowerShell makes it easy to print or save data</span></span>
    
- <span data-ttu-id="ba446-113">Office 365 PowerShell을 사용하여 여러 서버 제품을 관리할 수 있음</span><span class="sxs-lookup"><span data-stu-id="ba446-113">Office 365 PowerShell lets you manage across server products</span></span>
    
<span data-ttu-id="ba446-p102">시작하기 전에 Office 365 PowerShell이 Windows 기반 서비스 및 플랫폼에 대한 명령줄 환경인 Windows PowerShell용 모듈 집합이라는 점을 이해하면 도움이 됩니다. 이 환경은 추가 모듈로 확장할 수 있는 명령 셸 언어를 만들고 간단하거나 복잡한 명령을 실행하는 방법을 제공합니다. 예를 들어 Office 365 PowerShell 모듈을 설치하고 Office 365 구독에 연결한 후에는 이 명령을 사용하여 Microsoft Exchange Online에 대한 모든 사용자 사서함 목록을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-p102">Before you begin, understand that Office 365 PowerShell is a set of modules for Windows PowerShell, a command-line environment for Windows-based services and platforms. This environment creates a command shell language that can be extended with additional modules and provides a way to execute simple or complex commands or scripts For example, after you install the Office 365 PowerShell modules and connect to your Office 365 subscription, you can run this command to list all of the user mailboxes for Microsoft Exchange Online:</span></span>
  
```
Get-Mailbox
```

<span data-ttu-id="ba446-116">이 명령을 실행하여 SharePoint Online의 모든 웹앱에 대한 모든 사이트의 전체 목록에 포함된 항목 수를 계산할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-116">You can also run this command to calculate the number of items in all of the lists for all of the sites for all of your web apps in SharePoint Online:</span></span>
  
```
Get-SPOSite -Limit All | Get-SPWeb -Limit All | % {$_.Lists} | ? {$_ -is [Microsoft.SharePoint.SPDocumentLibrary]} | % {$total+= $_.ItemCount}; $total
```

<span data-ttu-id="ba446-117">Office 365 관리 센터를 사용하여 사서함 목록을 쉽게 가져올 수도 있지만 모든 웹앱에 대한 모든 사이트의 전체 목록에 포함된 항목 수를 계산하는 일은 쉽지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-117">Getting the list of mailboxes can also be easily done using the Office 365 admin center, but counting the number of items in all of the lists for all of the sites for all of your web apps cannot be easily done.</span></span>
  
<span data-ttu-id="ba446-p103">Office 365 PowerShell은 Office 365 관리 센터를 대신하는 것이 아니라 Office 365를 관리하는 능력을 강화하고 향상시키도록 고안되었습니다. Office 365 PowerShell 명령으로만 수행할 수 있는 일부 구성 절차가 있으므로 Office 365 관리자는 적어도 Office 365 PowerShell을 사용하는 데 익숙해야 합니다. 이러한 경우 다음 방법을 이해해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-p103">Please note that Office 365 PowerShell is designed to augment and enhance your ability to manage Office 365, not to replace the Office 365 admin center. As an Office 365 administrator, you must become at least comfortable with using Office 365 PowerShell because there are some configuration procedures that can only be done with Office 365 PowerShell commands. In these cases, you will be required to understand how to:</span></span>
  
- <span data-ttu-id="ba446-121">Office 365 PowerShell 모듈 설치(각 관리자 컴퓨터에 대해 한번만 수행)</span><span class="sxs-lookup"><span data-stu-id="ba446-121">Install the Office 365 PowerShell modules (done only once for each administrator computer).</span></span>
    
- <span data-ttu-id="ba446-122">Office 365 구독에 연결(각 PowerShell 세션에 대해 한번만 수행)</span><span class="sxs-lookup"><span data-stu-id="ba446-122">Connect to your Office 365 subscription (done once for each PowerShell session).</span></span>
    
- <span data-ttu-id="ba446-123">필수 Office 365 PowerShell 명령 실행에 필요한 정보 수집</span><span class="sxs-lookup"><span data-stu-id="ba446-123">Gather the information needed to run the required Office 365 PowerShell commands.</span></span>
    
- <span data-ttu-id="ba446-124">Office 365 PowerShell 명령을 성공적으로 실행</span><span class="sxs-lookup"><span data-stu-id="ba446-124">Run the Office 365 PowerShell commands successfully.</span></span>
    
<span data-ttu-id="ba446-p104">이러한 기본 기술을 학습한 후에는 **Get-Mailbox** 명령을 사용하여 사서함 사용자를 나열할 필요도 없고, 앞에 나온 것처럼 모든 웹앱에 대한 모든 사이트의 전체 목록에 포함된 항목 수를 계산하기 위한 명령과 같은 새 명령을 만드는 방법을 알 필요도 없습니다. Microsoft 및 Office 365 관리자 커뮤니티에서 필요할 때 도움을 드릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-p104">After learning these basic skills, you are not required to list your mailbox users with **Get-Mailbox** command, nor are you required to understand how to create a new command like the previous one to count all the items in all the lists for all of the sites for all of your web apps. Microsoft and the community of Office 365 administrators can help you with that as needed.</span></span>
  
## <a name="office-365-powershell-can-reveal-additional-information-that-you-cannot-see-with-the-office-365-admin-center"></a><span data-ttu-id="ba446-127">Office 365 PowerShell은 Office 365 관리 센터에서는 볼 수 없는 추가 정보를 제공할 수 있음</span><span class="sxs-lookup"><span data-stu-id="ba446-127">Office 365 PowerShell can reveal additional information that you cannot see with the Office 365 admin center</span></span>
<span data-ttu-id="ba446-128"><a name="reveal"> </a></span><span class="sxs-lookup"><span data-stu-id="ba446-128"></span></span>

<span data-ttu-id="ba446-p105">Office 365 관리 센터에는 많은 유용한 정보가 표시되지만 Office 365에서 사용자, 라이선스, 사서함 및 사이트에 대해 저장할 수 있는 모든 정보가 표시되지는 않습니다. 다음은 Office 365 관리 센터의 **사용자 및 그룹** 예입니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-p105">The Office 365 admin center displays a lot of useful information, but that doesn't mean that it displays all the possible information that Office 365 stores on users, licenses, mailboxes, and sites. Here is an example for **users and groups** in the Office 365 admin center:</span></span>
  
![Office 365 관리 센터의 사용자 및 그룹 표시 예제입니다.](images/o365_powershell_users_and_groups.png)
  
<span data-ttu-id="ba446-p106">여기에는 다양한 용도로 사용자가 알아야 하는 정보가 표시됩니다. 그러나 더 많은 정보가 필요한 경우도 있습니다. 예를 들어 Office 365 라이선스 및 사용자에게 제공되는 Office 365 기능은 해당 사용자의 지리적 위치에 따라 달라집니다. 가령 미국 사용자에 대해 확장 가능한 정책과 기능은 인도나 벨기에 사용자에 대해 확장 가능한 정책과 기능은 서로 다를 수 있습니다. Office 365 관리 센터를 사용하면 다음 단계에 따라 사용자가 있는 지리적 위치를 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-p106">For many purposes, this displays the information you need to know. However, there are times when you need more. For example, Office 365 licensing (as well as the Office 365 features available to a user) depend in part on that user's geographic location. The policies and features you can extend to a user who lives in the United States might not be the same as the policies and features you can extend to a user who lives in India or in Belgium. You can use the Office 365 admin center to determine a user's geographic location with these steps:</span></span>
  
1. <span data-ttu-id="ba446-137">사용자의 **표시 이름** 을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-137">Double-click the user's **Display Name**.</span></span>
    
2. <span data-ttu-id="ba446-138">사용자 속성 표시 창에서 **세부 정보** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-138">In the user properties display pane, click **details**.</span></span>
    
3. <span data-ttu-id="ba446-139">세부 정보 표시에서 **추가 정보** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-139">In the details display, click **additional details**.</span></span>
    
4. <span data-ttu-id="ba446-140">**국가 또는 지역** 제목이 표시될 때까지 아래쪽으로 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-140">Scroll down until you see the heading **Country or region**:</span></span>
    
     ![Office 365 관리 센터의 사용자에 대한 지역 정보 예제입니다.](images/o365_powershell_usage_location.png)
  
5. <span data-ttu-id="ba446-142">사용자의 표시 이름과 지역을 종이에 적어 두거나 복사한 다음 메모장에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-142">Write the user's display name and location on a piece of paper, or copy and paste it into Notepad.</span></span> 
    
<span data-ttu-id="ba446-p107">각 사용자에 대해 이 절차를 반복해야 합니다. 많은 사용자에게 이 작업은 번거로울 수 있습니다. Office 365 PowerShell을 사용하면 다음 명령을 사용하여 모든 사용자에 대해 이 정보를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-p107">You must repeat this procedure for each user. For many users, this can be a tedious task. With Office 365 PowerShell, you can display this information for all of your users with the following command:</span></span>
  
```
Get-MsolUser | Select DisplayName, UsageLocation
```

> [!NOTE]
> <span data-ttu-id="ba446-146">이 명령을 사용하려면 [Windows Azure Active Directory 모듈]((https://technet.microsoft.com/ko-KR/library/jj151815.aspx))을 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-146">This command requires you to install the [Windows Azure Active Directory module]((https://technet.microsoft.com/ko-KR/library/jj151815.aspx)).</span></span> 
  
<span data-ttu-id="ba446-147">다음과 같은 화면이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-147">Here is an example of the display:</span></span>
  
```
DisplayName                               UsageLocation
-----------                               -------------
Zrinka Makovac                            US
Bonnie Kearney                            GB
Fabrice Canel                             BR
Brian Johnson (TAILSPIN)                  US
Anne Wallace                              US
Alex Darrow                               US
David Longmuir                            BR
```

> [!TIP]
>  <span data-ttu-id="ba446-148">이 Office 365 PowerShell 명령을 해석하면 다음과 같습니다. 현재 Office 365 구독의 모든 사용자를 가져오지만(**Get-MsolUser**), 각 사용자의 이름과 위치만 표시합니다(**Select DisplayName, UsageLocation**).</span><span class="sxs-lookup"><span data-stu-id="ba446-148">The interpretation of this Office 365 PowerShell command is:>  Get all of the users in the current Office 365 subscription ( **Get-MsolUser** ), but only display the name and location for each user ( **Select DisplayName, UsageLocation** ).</span></span>
  
<span data-ttu-id="ba446-p108">Office 365 PowerShell은 명령 셸 언어를 지원하므로 **Get-MSolUser** 명령에서 획득한 정보를 추가로 조작할 수 있습니다. 예를 들어 이러한 사용자를 위치별로 정렬하여 모든 브라질 사용자, 모든 미국 사용자 등으로 그룹화할 수 있습니다. 해당 명령은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-p108">Because Office 365 PowerShell supports a command shell language, you can further manipulate the information obtained from the **Get-MSolUser** command. For example, maybe you'd like to sort these users by their location, grouping all the Brazilian users together, all the United States users together, etc. Here is the command:</span></span>
  
```
Get-MsolUser | Select DisplayName, UsageLocation | Sort UsageLocation, DisplayName
```

<span data-ttu-id="ba446-151">다음과 같은 화면이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-151">Here is an example of the display:</span></span>
  
```
DisplayName                                 UsageLocation
-----------                                 -------------
David Longmuir                              BR
Fabrice Canel                               BR
Bonnie Kearney                              GB
Alex Darrow                                 US
Anne Wallace                                US
Brian Johnson (TAILSPIN)                    US
Zrinka Makovac                              US
```

> [!TIP]
>  <span data-ttu-id="ba446-152">이 Office 365 PowerShell 명령을 해석하면 다음과 같습니다. 현재 Office 365 구독의 모든 사용자를 가져오지만 각 사용자의 이름과 위치만 표시하고 먼저 위치별로 정렬한 후 이름별로 정렬합니다(**Sort UsageLocation, DisplayName**).</span><span class="sxs-lookup"><span data-stu-id="ba446-152">The interpretation of this Office 365 PowerShell command is:>  Get all of the users in the current Office 365 subscription, but only display the name and location for each user and sort them first by their location, and then their names ( **Sort UsageLocation, DisplayName** ).</span></span>
  
<span data-ttu-id="ba446-p109">추가 필터링을 사용할 수도 있습니다. 예를 들어 브라질 사용자에 대한 정보만 표시하려면 다음 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-p109">You can also employ additional filtering. For example, if you only want to see information about users based in Brazil, use this command:</span></span>
  
```
Get-MsolUser | Where {$_.UsageLocation -eq "BR"} | Select DisplayName, UsageLocation 
```

<span data-ttu-id="ba446-155">다음과 같은 화면이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-155">Here is an example of the display:</span></span>
  
```
DisplayName                                           UsageLocation
-----------                                           -------------
David Longmuir                                        BR
Fabrice Canel                                         BR
```

> [!TIP]
>  <span data-ttu-id="ba446-156">이 Office 365 PowerShell 명령을 해석하면 다음과 같습니다. 현재 Office 365 구독에서 해당 위치가 브라질인 모든 사용자를 가져온 다음(**Where {$\__.UsageLocation -eq "BR"}**), 각 사용자의 이름과 위치를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-156">The interpretation of this Office 365 PowerShell command is:>  Get all of the users in the current Office 365 subscription whose location is Brazil ( **Where {$_.UsageLocation -eq "BR"}** ), then display the name and location for each user.</span></span>
  
 <span data-ttu-id="ba446-157">**대규모 도메인 관련 참고 사항**</span><span class="sxs-lookup"><span data-stu-id="ba446-157">**A Quick Note Regarding Larger Domains**</span></span>
  
<span data-ttu-id="ba446-p110">사용자가 수만 명인 매우 큰 도메인의 경우 이 문서에서 제시하는 몇 가지 예를 사용하면 "제한" 현상이 발생할 수 있습니다. 즉, 컴퓨팅 기능, 사용 가능한 네트워크 대역폭 등을 기준으로 보았을 때 사용자가 한 번에 너무 많은 작업을 수행할 수 있습니다. 이러한 이유 때문에 대규모 조직은 이러한 Office 365 PowerShell 명령을 두 개의 명령으로 분할하고 싶을 수도 있습니다. 예를 들어 이 명령 하나를 실행하면 모든 사용자 계정이 반환되고 각 사용자의 이름과 위치가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-p110">If you have a very large domain with tens of thousands of users, trying some of the examples we show in this article could lead to "throttling." That means that, based on things like computing power and available network bandwidth, you're trying to do a little too much at one time. Because of that, larger organizations might want to split some of these Office 365 PowerShell commands into two commands. For example, this one command returns all the user accounts and shows the name and location for each:</span></span>
  
```
Get-MsolUser | Select DisplayName, UsageLocation
```

<span data-ttu-id="ba446-p111">소규모 도메인에서는 이 명령을 사용해도 아무런 문제가 없습니다. 그러나 대규모 조직에서는 위의 명령을 두 개의 명령, 즉 변수에 사용자 계정 정보를 저장하기 위한 명령과 필요한 정보를 표시하기 위한 명령으로 분할해야 할 수 있습니다. 예제는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-p111">That works great for smaller domains. In a large organization, however, you might need to split that into two commands: one command to store the user account information in a variable and another command to display the needed information. Here is an example:</span></span>
  
```
$x = Get-MsolUser
$x | Select DisplayName, UsageLocation
```


<span data-ttu-id="ba446-165">이 Office 365 PowerShell 명령을 해석하면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-165">The interpretation of this set of O365_W14_2nd PowerShell commands is:</span></span>
- <span data-ttu-id="ba446-166">현재 Office 365 구독의 모든 사용자를 가져오고 $x 변수에 정보를 저장합니다(**$x = Get-MsolUser**).</span><span class="sxs-lookup"><span data-stu-id="ba446-166">Get all of the users in the current  O365_W14_2nd subscription and store the information in a variable named $x ($x = Get-MsolUser).</span></span>
- <span data-ttu-id="ba446-167">$x 변수의 내용을 표시하지만 각 사용자의 이름과 위치만 포함합니다(**$x | Select DisplayName, UsageLocation**).</span><span class="sxs-lookup"><span data-stu-id="ba446-167">Display the contents of the variable $x, but only include the name and location for each user (**$x | Select DisplayName, UsageLocation**).</span></span>
  
## <a name="office-365-has-features-that-you-can-only-configure-with-office-365-powershell"></a><span data-ttu-id="ba446-168">Office 365에는 Office 365 PowerShell로만 구성할 수 있는 기능이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-168">Office 365 has features that you can only configure with Office 365 PowerShell</span></span>
<span data-ttu-id="ba446-169"><a name="only"> </a></span><span class="sxs-lookup"><span data-stu-id="ba446-169"></span></span>

<span data-ttu-id="ba446-p112">Office 365 관리 센터는 대부분의 사용자에 적용 되는 가장 일반적이거나 의미있는 관리 작업에 액세스할 수 있도록 하기 위해 고안되었습니다. 다시 말해서 Office 365 관리 센터는 일반적인 관리자가 가장 일반적인 관리 작업을 수행하는 데 사용할 수 있는 도구로 설계되었습니다. 따라서 기본적으로는 Office 365 관리 센터를 통해 완료할 수 없는 작업도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-p112">The Office 365 admin center is intended to provide access to the most common or meaningful administrative tasks that apply to most people. In other words, the Office 365 admin center was designed so that the typical administrator could use the tool to carry out the most common management tasks. By this definition, that means that there are some tasks that can't be completed by using the Office 365 admin center.</span></span>
  
<span data-ttu-id="ba446-173">예를 들어 비즈니스용 Skype 온라인 관리 센터에서는 사용자 지정 모임 초대를 만들기 위한 몇 가지 옵션을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-173">For example, the Skype for Business Online Admin center provides a few options for creating custom meeting invitations:</span></span>
  
![비즈니스용 Skype Online 관리 센터에 표시된 사용자 지정 모임 초대 예제입니다.](images/o365_powershell_meeting_invitation.png)
  
<span data-ttu-id="ba446-p113">이러한 설정을 사용하여 모임 초대를 전문적으로 개인 설정할 수 있습니다. 그러나 모임 구성 설정에는 사용자 지정 모임 초대 만들기 외에도 다양한 기능이 있습니다. 예를 들어 모임에서는 기본적으로 다음과 같은 설정이 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-p113">With these settings, you can add a touch of personalization and professionalism to meeting invitations. However, there's more to meeting configuration settings than simply creating custom meeting invitations. For example, by default, meetings allow:</span></span>
  
- <span data-ttu-id="ba446-178">익명 사용자가 각 모임에 자동으로 입장할 수 있도록 설정</span><span class="sxs-lookup"><span data-stu-id="ba446-178">Anonymous users to gain automatic entrance to each meeting.</span></span>
    
- <span data-ttu-id="ba446-179">참석자가 모임을 기록하도록 설정</span><span class="sxs-lookup"><span data-stu-id="ba446-179">Attendees to record the meeting.</span></span>
    
- <span data-ttu-id="ba446-180">조직의 모든 사용자가 모임 참가 시 발표자로 지정되도록 설정</span><span class="sxs-lookup"><span data-stu-id="ba446-180">All users from your organization to be designated as presenters when they join the meeting.</span></span>
    
<span data-ttu-id="ba446-p114">이러한 설정을 비즈니스용 Skype 온라인 관리 센터에서는 사용할 수 없습니다. 그러나 Office 365 PowerShell에서는 제어할 수 있습니다. 이러한 세 가지 설정을 사용하지 않도록 하는 명령은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-p114">These settings are not available from the Skype for Business Online Admin center. However, you can control them from Office 365 PowerShell. Here is a command that disables these three settings:</span></span>
  
```
Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $False -AllowConferenceRecording $False -DesignateAsPresenter "None"
```

> [!NOTE]
> <span data-ttu-id="ba446-184">이 명령을 사용하려면 [비즈니스용 Skype Online PowerShell 모듈](https://www.microsoft.com/download/details.aspx?id=39366)을 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-184">This command requires that you install the [Skype for Business Online PowerShell Module ](https://www.microsoft.com/download/details.aspx?id=39366).</span></span> 
  
> [!TIP]
>  <span data-ttu-id="ba446-185">이 Office 365 PowerShell 명령을 해석하면 다음과 같습니다.>  새 비즈니스용 Skype 온라인 모임 설정을 위해(**Set-CsMeetingConfiguration**) 익명 사용자가 모임에 자동으로 입장할 수 있도록 허용하는 기능을 사용하지 않도록 설정하고(**-AdmitAnonymousUsersByDefault $False**), 참석자가 모임을 기록하는 기능을 사용하지 않도록 설정하고(**-AllowConferenceRecording $False**), 조직의 모든 사용자를 발표자로 지정하지는 않도록 합니다(**-DesignateAsPresenter "None"**).</span><span class="sxs-lookup"><span data-stu-id="ba446-185">The interpretation of this Office 365 PowerShell command is:>  For the settings for new Skype for Business Online meetings ( **Set-CsMeetingConfiguration** ), disable allowing anonymous users to gain automatic entrance to meetings ( **-AdmitAnonymousUsersByDefault $False** ), disable the ability for attendees to record meetings ( **-AllowConferenceRecording $False** ), and do not designate all users from your organization as presenters ( **-DesignateAsPresenter "None"** ).</span></span>
  
<span data-ttu-id="ba446-186">생각이 바뀌어 이러한 기본 설정을 복원하려면(모두 사용하도록 설정) 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-186">If you change your mind and want to restore these default settings (all of them enabled), run this command:</span></span>
  
```
Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $True -AllowConferenceRecording $True -DesignateAsPresenter "Company"
```

<span data-ttu-id="ba446-p115">이것은 예에 불과합니다. Office 365 관리자가 Office 365 PowerShell 명령에 익숙해져야 하는 다른 이유도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-p115">This is just one example. There are others, which is why you, as an Office 365 administrator, need to be comfortable with running Office 365 PowerShell commands.</span></span>
  
## <a name="office-365-powershell-is-great-at-carrying-out-bulk-operations"></a><span data-ttu-id="ba446-189">Office 365 PowerShell은 대량 작업을 수행하는 데 유용함</span><span class="sxs-lookup"><span data-stu-id="ba446-189">Office 365 PowerShell is great at carrying out bulk operations</span></span>
<span data-ttu-id="ba446-190"><a name="bulk"> </a></span><span class="sxs-lookup"><span data-stu-id="ba446-190"></span></span>

<span data-ttu-id="ba446-p116">지금까지 Office 365 관리 센터와 같은 시각적 인터페이스는 단일 작업만 수행하면 될 경우에 가장 유용합니다. 예를 들어 사용자 계정 하나를 사용하지 않도록 설정해야 하는 경우 Office 365 관리 센터를 사용하여 확인란을 빠르게 찾은 후 선택을 취소할 수 있습니다. 이 작업은 Office 365 PowerShell에서 유사한 작업을 수행하는 것보다 더 간단할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-p116">Historically, visual interfaces like the Office 365 admin center are most valuable when you have a single operation to perform. For example, if you need to disable one user account, you can use the Office 365 admin center to quickly locate and clear a checkbox. This can be simpler than performing a similar operation in Office 365 PowerShell.</span></span>
  
<span data-ttu-id="ba446-p117">그렇지만 대규모 작업 내에서 많은 부분이나 선택한 일부 항목을 변경해야 할 경우 Office 365 관리 센터를 사용하는 것이 시간을 효과적으로 사용하는 데 적합하지 않을 수 있습니다. 예를 들어 수천 개의 전화 번호에 있는 내선 번호를 변경해야 하거나 모든 SharePoint Online 사이트에서 특정 사용자, Ken Myer를 제거해야 할 경우 Office 365 관리 센터에서 어떻게 이 작업을 수행할 수 있을까요?</span><span class="sxs-lookup"><span data-stu-id="ba446-p117">But if you have to change many things or some selected things within a large set of other things, the Office 365 admin center might not be the best use of your time. For example, if you had to change the prefix on thousands of phone numbers or you needed to remove a specific user, Ken Myer, from all of your SharePoint Online sites, how would you do that in the Office 365 admin center?</span></span>
  
<span data-ttu-id="ba446-p118">후자의 경우 SharePoint Online 사이트는 수백 개이고 그 중에서 Ken이 구성원으로 속해 있는 사이트가 어느 것인지도 모르는 상황입니다. 따라서 Office 365 관리 센터에서 시작한 후 각 사이트에 대해 다음 절차를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-p118">For the latter example, you have several hundred SharePoint Online sites and you don't know even know which ones of which Ken Meyer is a member. That means you'll have to start at the Office 365 admin center and then perform this procedure for each site:</span></span>
  
1. <span data-ttu-id="ba446-198">사이트의 **URL** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-198">Click the **URL** of the site.</span></span>
    
2. <span data-ttu-id="ba446-199">**사이트 모음 속성** 상자에서 **웹 사이트 주소** 링크를 클릭하여 사이트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-199">In the **site collection properties** box, click the **Web Site Address** link to open the site.</span></span>
    
3. <span data-ttu-id="ba446-200">사이트에서 **공유** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-200">On the site, click **Share**.</span></span>
    
4. <span data-ttu-id="ba446-201">**공유** 대화 상자에서 사이트에 대한 사용 권한이 있는 모든 사용자를 표시하는 링크를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-201">In the **Share** dialog box click the link that shows you all the users who have permissions to the site:</span></span>
    
     ![SharePoint Online 관리 센터에서 SharePoint Online 사이트의 구성원을 보는 예제입니다.](images/o365_powershell_view_permissions.png)
  
5. <span data-ttu-id="ba446-203">**다음 사용자와 공유** 대화 상자에서 **고급** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-203">In the **Shared With** dialog box, click **Advanced**.</span></span>
    
6. <span data-ttu-id="ba446-204">사용자 목록 아래쪽으로 스크롤하여 Ken Myer(사이트에 대한 사용 권한이 있는 사용자라고 가정함)를 찾아 선택한 다음 **사용자의 사용 권한 제거** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-204">Scroll down the list of users, find and select Ken Myer (assuming he has permissions to the site), and then click **Remove User Permissions**.</span></span>
    
<span data-ttu-id="ba446-205">수백 개의 사이트의 경우 시간이 오래 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-205">This can take a long time for several hundred sites.</span></span>
  
<span data-ttu-id="ba446-206">또 다른 방법은 Office 365 PowerShell과 다음 명령을 사용하여 모든 사이트에서 Ken Myer를 제거하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-206">The alternative is to use Office 365 PowerShell and the following command to remove Ken Myer from all of your sites:</span></span>
  
```
Get-SPOSite | ForEach {Remove-SPOUser -Site $_.Url -LoginName "kenmyer@litwareinc.com"}
```

> [!NOTE]
> <span data-ttu-id="ba446-207">이 명령을 사용하려면 [SharePoint Online PowerShell에 연결]((https://technet.microsoft.com/library/fp161372.aspx))을 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-207">This command requires that you install the [Connect to SharePoint Online PowerShell]((https://technet.microsoft.com/library/fp161372.aspx)).</span></span> 
  
> [!TIP]
>  <span data-ttu-id="ba446-208">이 Office 365 PowerShell 명령을 해석하면 다음과 같습니다. 현재 Office 365 구독에서 모든 SharePoint 사이트를 가져오고(**Get-SPOSite**) 각 사이트에 액세스할 수 있는 사용자 목록에서 Ken Meyer를 제거합니다(**ForEach {Remove-SPOUser -Site $\__.Url -LoginName "kenmyer@litwareinc.com"}**).</span><span class="sxs-lookup"><span data-stu-id="ba446-208">The interpretation of this Office 365 PowerShell command is:>  Get all of the SharePoint sites in the current Office 365 subscription ( **Get-SPOSite** ) and for each site, remove Ken Meyer from the list of users who can access it ( **ForEach {Remove-SPOUser -Site $_.Url -LoginName "kenmyer@litwareinc.com"}** ).</span></span>
  
<span data-ttu-id="ba446-p119">Office 365에 Key Meyer가 액세스할 수 없는 사이트를 비롯한 모든 사이트에서 Ken Meyer를 제거하도록 지정하고 있으므로 현재 액세스 권한이 없는 사이트에 대한 오류가 표시됩니다. 이 명령에 추가 조건을 사용하여 로그인 목록에 Ken Meyer가 있는 사이트에서만 Ken Meyer를 제거할 수 있지만 나열되는 오류가 사이트 자체에는 문제가 되지 않습니다. 수백 개의 사이트에 대해 이 명령을 실행하는 데 몇 분 정도 소요될 수 있지만 Office 365 관리 센터로 작업하면 몇 시간이 걸리게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-p119">Because we are telling Office 365 to remove Ken Meyer from every site, including those in which he does not have access, the display of this command will show errors for those sites in which he does not currently have access. We can use an additional condition on this command to remove Key Meyer only from the sites that have him in their login list, but the listed errors cause no harm to the sites themselves. This command might take a few minutes to run against hundreds of sites, rather than hours of working through the Office 365 admin center.</span></span>
  
<span data-ttu-id="ba446-p120">다른 대량 작업의 예제는 다음과 같습니다. 이 명령을 사용하여 새 SharePoint 관리자인 Bonnie Kearney를 조직의 모든 사이트에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-p120">Here is another bulk operation example. Use this command to add Bonnie Kearney, a new SharePoint administrator, to all of the sites in the organization:</span></span>
  
```
Get-SPOSite | ForEach {Add-SPOUser -Site $_.Url -LoginName "bkearney@litwareinc.com" -Group "Members"}
```

> [!TIP]
>  <span data-ttu-id="ba446-214">이 Office 365 PowerShell 명령을 해석하면 다음과 같습니다. 현재 Office 365 구독의 모든 SharePoint 사이트를 가져오고 각 사이트의 구성원 그룹에 해당 로그인 이름을 추가하여 Bonnie Kearney의 액세스를 허용합니다(**ForEach {Add-SPOUser -Site $\__.Url -LoginName "bkearney@litwareinc.com" -Group "Members"}**).</span><span class="sxs-lookup"><span data-stu-id="ba446-214">The interpretation of this Office 365 PowerShell command is:>  Get all of the SharePoint sites in the current Office 365 subscription and for each site, allow Bonnie Kearney access by adding her login name to the Members group of the site ( **ForEach {Add-SPOUser -Site $_.Url -LoginName "bkearney@litwareinc.com" -Group "Members"}** ).</span></span>
  
## <a name="office-365-powershell-is-great-at-filtering-data"></a><span data-ttu-id="ba446-215">Office 365 PowerShell은 데이터를 필터링하는 데 유용함</span><span class="sxs-lookup"><span data-stu-id="ba446-215">Office 365 PowerShell is great at filtering data</span></span>
<span data-ttu-id="ba446-216"><a name="filter"> </a></span><span class="sxs-lookup"><span data-stu-id="ba446-216"></span></span>

<span data-ttu-id="ba446-p121">Office 365 관리 센터에서는 데이터를 필터링하여 대상 정보 하위 집합을 쉽고 빠르게 찾을 수 있는 여러 가지 방법을 제공합니다. 예를 들어 Exchange에서는 사용자 사서함의 사실상 모든 속성을 기준으로 쉽게 필터링을 할 수 있습니다. 예를 들어 다음은 Bloomington에 거주하는 모든 사용자의 사서함 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-p121">The Office 365 admin center provides several different ways to filter your data to quickly and easily locate a targeted subset of information. For example, Exchange makes it easy to filter on practically any property of a user mailbox. For example, here is the list of mailboxes for all the users who live in the city of Bloomington:</span></span>
  
![Bloomington 시에 거주하는 모든 사용자의 사서함 목록에 대해 Office 365 관리 센터에서 고급 검색을 수행하는 예제입니다.](images/o365_powershell_advanced_search.png)
  
<span data-ttu-id="ba446-p122">Exchange 관리 센터에서도 필터 기준을 조합할 수 있습니다. 예를 들어 Bloomington에 거주하고 재무 부서에서 일하는 모든 사용자에 대한 사서함을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-p122">The Exchange Admin center also lets you combine filter criteria. For example, you can find the mailboxes for all the people who live in Bloomington and who work in the Finance department.</span></span> 
  
<span data-ttu-id="ba446-p123">그러나 Exchange 관리 센터에서는 수행할 수 있는 작업에 제한이 있습니다. 예를 들어 Bloomington이나 San Diego에 거주하는 사용자의 사서함을 찾거나 Bloomington에 거주하지 않는 모든 사용자에 대한 사서함을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-p123">However, there are limitations to what you can do in the Exchange Admin center. For example, maybe you'd like to find the mailboxes of people who live in Bloomington or San Diego, or the mailboxes for all the people who don't live in Bloomington.</span></span> 
  
<span data-ttu-id="ba446-225">Office 365 PowerShell에서 다음 명령을 사용하여 Bloomington 또는 San Diego에 거주하는 모든 사람에 대한 사서함 목록을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-225">With Office 365 PowerShell, you can get a list of mailboxes for all the people who live in the cities of Bloomington or San Diego with this command:</span></span>
  
```
Get-User | Where {$_.RecipientTypeDetails -eq "UserMailbox" -and ($_.City -eq "San Diego" -or $_.City -eq "Bloomington")} | Select DisplayName, City
```

<span data-ttu-id="ba446-226">다음과 같은 화면이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-226">Here is an example of the display:</span></span>
  
```
DisplayName                              City
-----------                              ----
Alex Darrow                              San Diego
Bonnie Kearney                           San Diego
Julian Isla                              Bloomington
Rob Young                                Bloomington
Zrinka Makovac                           San Diego
```

> [!TIP]
>  <span data-ttu-id="ba446-227">이 Office 365 PowerShell 명령을 해석하면 다음과 같습니다. 현재 Office 365 구독에서 San Diego 또는 Bloomington에 사서함을 보유하고 있는 모든 사용자를 가져온 다음(**Where {$\_.RecipientTypeDetails -eq "UserMailbox" -and ($\_.City -eq "San Diego" -or $\__.City -eq "Bloomington")}**) 각 사용자의 이름과 도시를 표시합니다(**Select DisplayName, City**).</span><span class="sxs-lookup"><span data-stu-id="ba446-227">The interpretation of this Office 365 PowerShell command is:>  Get all of the users in the current Office 365 subscription who have a mailbox in the cities of either San Diego or Bloomington ( **Where {$\_.RecipientTypeDetails -eq "UserMailbox" -and ($\_.City -eq "San Diego" -or $_.City -eq "Bloomington")}** ), then display the name and city for each ( **Select DisplayName, City** ).</span></span>
  
<span data-ttu-id="ba446-228">Bloomington을 제외한 모든 위치에 거주하는 사용자의 모든 사서함을 나열하려면 다음 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-228">To list all the mailboxes for people who live anywhere except Bloomington, here is the command:</span></span>
  
```
Get-User | Where {$_.RecipientTypeDetails -eq "UserMailbox" -and $_.City -ne "Bloomington"} | Select DisplayName, City
```

<span data-ttu-id="ba446-229">다음과 같은 화면이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-229">Here is an example of the display:</span></span>
  
```
DisplayName                               City
-----------                               ----
MOD Administrator                         Redmond
Alex Darrow                               San Diego
Allie Bellew                              Bellevue
Anne Wallace                              Louisville
Aziz Hassouneh                            Cairo
Belinda Newman                            Charlotte
Bonnie Kearney                            San Diego
David Longmuir                            Waukesha
Denis Dehenne                             Birmingham
Garret Vargas                             Seattle
Garth Fort                                Tulsa
Janet Schorr                              Bellevue
```

> [!TIP]
>  <span data-ttu-id="ba446-230">이 Office 365 PowerShell 명령을 해석하면 다음과 같습니다. Bloomington에 사서함이 없는 현재 Office 365 구독의 모든 사용자를 가져오고(**Where {$\_.RecipientTypeDetails -eq "UserMailbox" -and $\_.City -ne "Bloomington"}**) 각 사용자의 이름과 도시를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-230">The interpretation of this Office 365 PowerShell command is:>  Get all of the users in the current Office 365 subscription who have a mailbox not located in the city of Bloomington ( **Where {$\_.RecipientTypeDetails -eq "UserMailbox" -and $\_.City -ne "Bloomington"}** ), then display the name and city for each.</span></span>
  
<span data-ttu-id="ba446-p124">Office 365 PowerShell 필터에 와일드카드 문자를 사용하여 이름 일부와 일치하는 항목을 찾을 수도 있습니다. 예를 들어 특정 사용자 계정을 찾아야 하는데 성이 Anderson, Henderson 또는 Jorgenson이라는 점만 기억하고 있다고 가정할 경우</span><span class="sxs-lookup"><span data-stu-id="ba446-p124">You can also use wildcard characters in your Office 365 PowerShell filters to match part of a name. For example, suppose you're looking for a user account, and all you can remember is that their last name was Anderson, or maybe Henderson, or maybe it was Jorgenson.</span></span>
  
<span data-ttu-id="ba446-233">검색 도구를 사용하고 다음 세 가지 다른 검색을 수행하여 Office 365 관리 센터에서 해당 사용자에 추적할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-233">You could track down that user in the Office 365 admin center by using the search tool and carrying out three different searches:</span></span>
  
- <span data-ttu-id="ba446-234">*Anderson*  에 대해,</span><span class="sxs-lookup"><span data-stu-id="ba446-234">One for  *Anderson*</span></span> 
    
- <span data-ttu-id="ba446-235">*Henderson*  에 대해,</span><span class="sxs-lookup"><span data-stu-id="ba446-235">One for  *Henderson*</span></span> 
    
- <span data-ttu-id="ba446-236">*Jorgenson*  에 대해</span><span class="sxs-lookup"><span data-stu-id="ba446-236">One for  *Jorgenson*</span></span> 
    
<span data-ttu-id="ba446-p125">이렇나 모든 이름은 "son"으로 끝나므로 Office 365 PowerShell에 이름이 "son"으로 끝나는 모든 사용자를 표시하도록 지정할 수 있습니다. 해당 명령은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-p125">Because all three of these names end in "son", you can tell Office 365 PowerShell to display all the users whose name ends in "son". Here is the command:</span></span>
  
```
Get-User -Filter '{LastName -like "*son"}'
```

> [!TIP]
>  <span data-ttu-id="ba446-p126">이 Office 365 PowerShell 명령을 해석하면 다음과 같습니다. 현재 Office 365 구독의 모든 사용자를 가져오지만 성이 "son"으로 끝나는 사용자만 나열하는 필터를 사용합니다(**-Filter '{LastName -like "**son"}'\**). \*는 임의의 문자 집합을 나타내며, 사용자의 성인 경우에는 글자에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-p126">The interpretation of this Office 365 PowerShell command is:>  Get all of the users in the current Office 365 subscription, but use a filter that only lists the users whose last names end in "son" ( **-Filter '{LastName -like "\*son"}'*** ). The ***** stands for any set of characters, which are letters in the case of the user's last name.</span></span>
  
## <a name="office-365-powershell-makes-it-easy-to-print-or-save-data"></a><span data-ttu-id="ba446-241">Office 365 PowerShell을 사용하면 데이터 쉽게 인쇄 또는 저장할 수 있음</span><span class="sxs-lookup"><span data-stu-id="ba446-241">Office 365 PowerShell makes it easy to print or save data</span></span>
<span data-ttu-id="ba446-242"><a name="printsave"> </a></span><span class="sxs-lookup"><span data-stu-id="ba446-242"></span></span>

<span data-ttu-id="ba446-p127">Office 365 관리 센터에서 데이터 목록을 볼 수 있습니다. 다음은 비즈니스용 Skype 온라인에 대해 사용되도록 설정된 사용자 목록을 표시하는 비즈니스용 Skype 온라인 관리 센터의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-p127">The Office 365 admin center allows you to view lists of data. Here is an example of the Skype for Business Online Admin center displaying a list of users who have been enabled for Skype for Business Online:</span></span>
  
![비즈니스용 Skype Online을 사용하도록 설정된 사용자 목록을 표시하는 비즈니스용 Skype Online 관리 센터 예제입니다.](images/o365_powershell_lync_users.png)
  
<span data-ttu-id="ba446-p128">해당 정보를 파일에 저장하려면 복사한 후 문서 또는 Excel에 붙여 넣어야 합니다. 두 경우 모두 복사를 위해 추가 서식이 필요할 수 있습니다. 또한 Office 365 관리 센터에서는 표시된 목록을 바로 인쇄하는 방법을 제공하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-p128">To save that information to a file, you must copy and paste it into a document or Excel. In either case, the copy might require additional formatting. Additionally, the Office 365 admin center does not provide a way to directly print the displayed list.</span></span>
  
<span data-ttu-id="ba446-p129">다행히 Office 365 PowerShell을 사용하여 목록을 표시할 수 있을뿐 아니라 Excel로 쉽게 가져올 수 있는 파일에 저장할 수도 있습니다. 다음은 비즈니스용 Skype 온라인 사용자 데이터를 Excel 워크시트의 표로 쉽게 가져올 수 있는 CSV(쉼표로 구분된 값) 파일에 저장하는 예제 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-p129">Fortunately, you can use Office 365 PowerShell to not only display the list, but save it to a file that can be easily imported into Excel. Here is an example command to save Skype for Business Online user data to a comma-separated values (CSV) file, a file that can be easily imported as a table in an Excel worksheet:</span></span>
  
```
Get-CsOnlineUser | Select DisplayName, UserPrincipalName, UsageLocation | Export-Csv -Path "C:\\Logs\\SfBUsers.csv" -NoTypeInformation
```

<span data-ttu-id="ba446-251">다음과 같은 화면이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-251">Here is an example of the display:</span></span>
  
![쉼표로 구분된 값(CSV) 파일로 저장된 Skype용 비즈니스 Online 사용자 데이터를 Excel 워크시트로 가져온 테이블 예제입니다.](images/o365_powershell_data_in_excel.png)
  
> [!TIP]
>  <span data-ttu-id="ba446-253">이 Office 365 PowerShell 명령을 해석하면 다음과 같습니다. 현재 Office 365 구독의 모든 비즈니스용 Skype 온라인 사용자를 가져오고(**Get-CsOnlineUser**), 사용자 이름, UPN 및 위치만 가져오고(**Select DisplayName, UserPrincipalName, UsageLocation**), C:\\Logs\\SfBUsers.csv라는 CSV 파일에 해당 정보를 저장합니다(**Export-Csv -Path "C:\\Logs\\SfBUsers.csv" -NoTypeInformation**).</span><span class="sxs-lookup"><span data-stu-id="ba446-253">The interpretation of this Office 365 PowerShell command is:>  Get all of the Skype for Business Online users in the current Office 365 subscription ( **Get-CsOnlineUser** ), obtain only the user name, UPN, and location ( **Select DisplayName, UserPrincipalName, UsageLocation** ), and then save that information in CSV file named C:\\Logs\\SfBUsers.csv ( **Export-Csv -Path "C:\\Logs\\SfBUsers.csv" -NoTypeInformation** ).</span></span>
  
<span data-ttu-id="ba446-p130">또한 옵션을 사용하여 이 목록을 XML 파일 또는 HTML 페이지로 저장할 수도 있습니다. 실제로 추가 PowerShell 명령과 원하는 사용자 지정 서식을 사용하여 Excel 파일로 직접 저장할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-p130">You can also use options to save this list as an XML file or as an HTML page. In fact, with additional PowerShell commands, you could save it directly as an Excel file, with any custom formatting you desire.</span></span> 
  
<span data-ttu-id="ba446-p131">Windows에서 기본 프린터에 직접 목록을 표시하는 Office 365 PowerShell 명령의 출력을 보낼 수도 있습니다. 예제 명령은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-p131">You can also send the output of an Office 365 PowerShell command that displays a list directly to the default printer in Windows. Here is an example command:</span></span>
  
```
Get-CsOnlineUser | Select DisplayName, UserPrincipalName, UsageLocation | Out-Printer
```

<span data-ttu-id="ba446-258">인쇄된 문서의 모양은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-258">Here's what your printed document will look like:</span></span>
  
![Windows의 기본 프린터에 직접 나열된 Office 365 PowerShell 명령 출력의 인쇄된 문서 예제입니다.](images/o365_powershell_printed_data.png)
  
> [!TIP]
>  <span data-ttu-id="ba446-260">이 Office 365 PowerShell 명령을 해석하면 다음과 같습니다. 현재 Office 365 구독의 모두 비즈니스용 Skype 온라인 사용자를 가져오고, 사용자 이름, UPN 및 위치만 가져온 다음 기본 Windows 프린터에 해당 정보를 보냅니다(**Out-Printer**).</span><span class="sxs-lookup"><span data-stu-id="ba446-260">The interpretation of this Office 365 PowerShell command is:>  Get all of the Skype for Business Online users in the current Office 365 subscription, obtain only the user name, UPN, and location, and then send that information to the default Windows printer ( **Out-Printer** ).</span></span>
  
<span data-ttu-id="ba446-261">인쇄된 문서는 Office 365 PowerShell 명령 창 내에 표시되는 것과 동일한 간단한 서식을 가지지만 필요한 항목만 나열하는 Office 365 PowerShell 명령을 만든 경우 명령 끝에 **| Out-Printer**만 추가하여 작업할 하드 카피를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-261">The printed document has the same simple formatting as the display within the Office 365 PowerShell command window, but once you have created an Office 365 PowerShell command to list what you need, you just add ** | Out-Printer** to the end of the command to get a hard copy to work from.</span></span>
  
## <a name="office-365-powershell-lets-you-manage-across-server-products"></a><span data-ttu-id="ba446-262">Office 365 PowerShell을 사용하여 여러 서버 제품을 관리할 수 있음</span><span class="sxs-lookup"><span data-stu-id="ba446-262">Office 365 PowerShell lets you manage across server products</span></span>
<span data-ttu-id="ba446-263"><a name="printsave"> </a></span><span class="sxs-lookup"><span data-stu-id="ba446-263"></span></span>

<span data-ttu-id="ba446-p132">Office 365를 구성하는 여러 다양한 구성 요소는 함께 작동되도록 설계되어 있습니다. 예를 들어 Office 365에 새 사용자를 추가할 때는 사용자의 부서, 전화 번호 등의 정보를 지정합니다. 이러한 정보는 Office 365 서버 제품인 비즈니스용 Skype 온라인, Exchange 또는 SharePoint Online 중 하나를 사용하여 사용자 정보에 액세스하는 경우에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-p132">The different components that make up Office 365 are designed to work together. For example, suppose you add a new user to Office 365 and, when you do, you specify such information as the user's department and phone number. That information will then be available if you access the user's information using any of the Office 365 server products: Skype for Business Online, Exchange, or SharePoint Online.</span></span>
  
<span data-ttu-id="ba446-p133">그러나 이러한 방식은 제품군 전체에 적용되는 일반적인 정보에만 해당됩니다. 사용자의 Exchange 사서함에 대한 정보와 같은 제품 관련 정보는 일반적으로 전체 제품군 내에서 사용할 수 없스니다. 예를 들어 사용자의 사서함이 사용되도록 설정되어 있는지를 알려면 해당 정보가 Exchange 관리 센터에서만 사용할 수 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-p133">But that's for common information that spans the suite of products. Product-specific information-for example, information about a user's Exchange mailbox-is typically not available across the suite. For example, if you want to know if a user's mailbox is enabled or not, that information is available only in the Exchange Admin center.</span></span> 
  
<span data-ttu-id="ba446-270">모든 사용자에 대해 다음 정보를 표시하는 보고서를 만들려는 경우를 가정해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-270">Suppose you'd like to make a report that shows the following information for all your users:</span></span>
  
- <span data-ttu-id="ba446-271">사용자의 표시 이름</span><span class="sxs-lookup"><span data-stu-id="ba446-271">The user's display name</span></span>
    
- <span data-ttu-id="ba446-272">사용자에게 Office 365 사용이 허가되었는지 여부</span><span class="sxs-lookup"><span data-stu-id="ba446-272">Whether the user is licensed for Office 365</span></span>
    
- <span data-ttu-id="ba446-273">사용자의 Exchange 사서함이 사용하도록 설정되었는지 여부</span><span class="sxs-lookup"><span data-stu-id="ba446-273">Whether the user's Exchange mailbox has been enabled</span></span>
    
- <span data-ttu-id="ba446-274">사용자가 비즈니스용 Skype 온라인을 사용할 수 있도록 설정되었는지 여부</span><span class="sxs-lookup"><span data-stu-id="ba446-274">Whether the user is enabled for Skype for Business Online</span></span>
    
<span data-ttu-id="ba446-p134">현재 Office 365 관리 센터에서는 이러한 보고서를 쉽게 생성할 수 없습니다. 대신 정보를 저장하는 별도의 문서(예: Excel 워크시트)를 만들고, Office 365 관리 센터 관리 센터에서 와 모든 사용자 이름 및 라이선스 정보를 가져오고, Exchange에서 사서함 정보를 가져오고, 비즈니스용 Skype 온라인 관리 센터에서 비즈니스용 Skype 온라인 정보를 가져온 다음 해당 정보를 수집한 후 조합해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-p134">You currently cannot use the Office 365 admin center to easily produce such a report. Instead, you'll have to create a separate document to store the information, like an Excel worksheet, and get all the user names and licensing information from the Office 365 admin center, get mailbox information from the Exchange Admin center, get Skype for Business Online information from the Skype for Business Online Admin center, and then collate and combine that information.</span></span>
  
<span data-ttu-id="ba446-277">이 방법 대신 Office 365 PowerShell 스크립트를 사용하여 해당 보고서를 컴파일할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-277">The alternative is to use an Office 365 PowerShell script to compile that report for you.</span></span>
  
<span data-ttu-id="ba446-p135">다음 예제 스크립트는 지금까지 이 문서에서 살펴본 명령보다 좀 더 복잡합니다. 그렇지만 Office 365 PowerShell을 사용하여 훨씬 더 어려울 수 있는 정보 보기를 만들 수 있다는 사실을 보여 줍니다. 다음은 필요한 목록을 정리해서 표시할 수 있는 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-p135">The following example script is more complicated than the commands you have seen so far in this article. But, it shows the potential of using Office 365 PowerShell to create views of information that are very difficult to do otherwise. Here is the script that can compile and display the needed list:</span></span>
  
```
$x = Get-MsolUser

foreach ($i in $x)
    {
      $y = Get-Mailbox -Identity $i.UserPrincipalName
      $i | Add-Member -MemberType NoteProperty -Name IsMailboxEnabled -Value $y.IsMailboxEnabled

      $y = Get-CsOnlineUser -Identity $i.UserPrincipalName
      $i | Add-Member -MemberType NoteProperty -Name EnabledForSfB -Value $y.Enabled
    }

$x | Select DisplayName, IsLicensed, IsMailboxEnabled, EnabledforSfB
```

<span data-ttu-id="ba446-281">다음과 같은 화면이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-281">Here is an example of the display:</span></span>
  
```
DisplayName             IsLicensed   IsMailboxEnabled   EnabledForSfB
-----------             ----------   ----------------   --------------
Zrinka Makovac          True         True               True
Bonnie Kearney          True         True               True
Fabrice Canel           True         True               True
Brian Johnson           False        True               False
Anne Wallace            True         True               True
Alex Darrow             True         True               True
David Longmuir          True         True               True
Katy Jordan             False        True               False
Molly Dempsey           False        True               False
```

<span data-ttu-id="ba446-282">이 Office 365 PowerShell 스크립트를 해석하면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ba446-282">The interpretation of this Office 365 PowerShell script is:</span></span>  
- <span data-ttu-id="ba446-283">현재 Office 365 구독의 모든 사용자를 가져오고 $x 변수에 정보를 저장합니다(**$x = Get-MsolUser**).</span><span class="sxs-lookup"><span data-stu-id="ba446-283">Get all of the users in the current  O365_W14_2nd subscription and store the information in a variable named $x ($x = Get-MsolUser).</span></span>
- <span data-ttu-id="ba446-284">변수 $x에서 모든 사용자에 대해 실행되는 루프를 시작합니다(**foreach ($i in $x)**).</span><span class="sxs-lookup"><span data-stu-id="ba446-284">Start a loop that runs over all the users in the variable named $x (**foreach ($i in $x)**).</span></span>  
- <span data-ttu-id="ba446-285">$y라는 변수를 정의하고 이 변수에 사용자의 사서함 정보를 저장합니다(**$y = Get-Mailbox -Identity $i.UserPrincipalName**).</span><span class="sxs-lookup"><span data-stu-id="ba446-285">Define a variable named $y and store the user's mailbox information in it (**$y = Get-Mailbox -Identity $i.UserPrincipalName**).</span></span>
- <span data-ttu-id="ba446-286">IsMailBoxEnabled라는 사용자 정보에 새 속성을 추가하고 사용자 사서함의 IsMailBoxEnabled 속성 값으로 설정합니다(**$i | Add-Member -MemberType NoteProperty -Name IsMailboxEnabled -Value $y.IsMailboxEnabled**).</span><span class="sxs-lookup"><span data-stu-id="ba446-286">Add a new property to the user information named IsMailBoxEnabled and set it to the value of the IsMailBoxEnabled property of the user's mailbox  (**$i | Add-Member -MemberType NoteProperty -Name IsMailboxEnabled -Value $y.IsMailboxEnabled**).</span></span>
- <span data-ttu-id="ba446-287">$y라는 변수를 정의하고 이 변수에 사용자의 비즈니스용 Skype Online 정보를 저장합니다(**$y = Get-CsOnlineUser -Identity $i.UserPrincipalName**).</span><span class="sxs-lookup"><span data-stu-id="ba446-287">Define a variable named $y and store the user's Skype for Business Online information in it ( **$y = Get-CsOnlineUser -Identity $i.UserPrincipalName** ).</span></span>
- <span data-ttu-id="ba446-288">EnabledForSfB라는 사용자 정보에 새 속성을 추가하고 사용자 비즈니스용 Skype Online 정보의 Enabled 속성 값으로 설정합니다(**$i | Add-Member -MemberType NoteProperty -Name EnabledForSfB -Value $y.Enabled**).</span><span class="sxs-lookup"><span data-stu-id="ba446-288">Add a new property to the user information named EnabledForSfB and set it to the value of the Enabled property of the user's Skype_for_Business_Online information ($i | Add-Member -MemberType NoteProperty -Name EnabledForSfB -Value $y.Enabled).</span></span>
- <span data-ttu-id="ba446-289">사용자의 목록을 표시하지만 이름, 사용 허가 여부, 사서함 사용 가능 여부와 비즈니스용 Skype Online에 대해 사용되도록 설정되었는지 여부를 나타내는 두 개의 새 속성만 포함합니다(**$x | Select DisplayName, IsLicensed, IsMailboxEnabled, EnabledforSfB**).</span><span class="sxs-lookup"><span data-stu-id="ba446-289">Display the list of users, but include only their name, whether they are licensed, and the two new properties that indicate whether their mailbox is enabled and whether they are enabled for Skype_for_Business_Online  ($x | Select DisplayName, IsLicensed, IsMailboxEnabled, EnabledforSfB).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="ba446-290">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ba446-290">See also</span></span>


#### 

[<span data-ttu-id="ba446-291">Office 365 PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="ba446-291">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
  
[<span data-ttu-id="ba446-292">사용자 계정 및 Office 365 PowerShell을 사용 하 여 라이센스 관리</span><span class="sxs-lookup"><span data-stu-id="ba446-292">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="ba446-293">Office 365에서 Windows PowerShell을 사용하여 보고서 만들기</span><span class="sxs-lookup"><span data-stu-id="ba446-293">Use Windows PowerShell to create reports in Office 365</span></span>](use-windows-powershell-to-create-reports-in-office-365.md)

