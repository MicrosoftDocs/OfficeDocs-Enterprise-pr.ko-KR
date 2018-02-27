---
title: "Office 365 PowerShell을 사용 하 여 허가 된 / 허가 되지 않은 사용자 보기"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: O365ITProTrain, Ent_Office_Other, PowerShell
ms.assetid: e4ee53ed-ed36-4993-89f4-5bec11031435
description: "사용 하는 방법에 설명 Office 365 PowerShell 허가 된 / 허가 되지 않은 사용자 계정을 볼 수 있습니다."
ms.openlocfilehash: e691ba7db96b34166f03ccd90d87fee0d2ee09f8
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/13/2018
---
# <a name="view-licensed-and-unlicensed-users-with-office-365-powershell"></a><span data-ttu-id="08164-103">Office 365 PowerShell을 사용 하 여 허가 된 / 허가 되지 않은 사용자 보기</span><span class="sxs-lookup"><span data-stu-id="08164-103">View licensed and unlicensed users with Office 365 PowerShell</span></span>

<span data-ttu-id="08164-104">**요약:** Office 365 PowerShell을 사용하여 허가되거나 허가되지 않은 사용자 계정을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08164-104">**Summary:** Explains how to use Office 365 PowerShell to view licensed and unlicensed user accounts.</span></span>
  
<span data-ttu-id="08164-p101">Office 365 조직의 사용자 계정에 조직에서 사용할 수 있는 라이선싱 계획의 사용 가능한 라이선스가 일부 또는 모두 할당되어 있거나 하나도 할당되어 있지 않을 수 있습니다. Office 365 PowerShell을 사용하여 조직에서 사용이 허가되었거나 허가되지 않은 사용자를 빠르게 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08164-p101">User accounts in your Office 365 organization may have some, all, or none of the available licenses assigned to them from the licensing plans that are available in your organization. You can use Office 365 PowerShell to quickly find the licensed and unlicensed users in your organization.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="08164-107">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="08164-107">Before you begin</span></span>

- <span data-ttu-id="08164-p102">이 항목의 절차를 수행하려면 Office 365 PowerShell에 연결되어 있어야 합니다. 지침을 보려면 [PowerShell Office 365에 연결](connect-to-office-365-powershell.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="08164-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="08164-110">_-All_ 매개 변수를 사용하지 않고 **Get-MsolUser** cmdlet을 사용하는 경우 처음 500개의 계정만 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="08164-110">If you use the **Get-MsolUser** cmdlet without using the _-All_ parameter, only the first 500 accounts are returned.</span></span>
    
## <a name="the-short-version-instructions-without-explanations"></a><span data-ttu-id="08164-111">간략 한 (설명 없이 지침)</span><span class="sxs-lookup"><span data-stu-id="08164-111">The short version (instructions without explanations)</span></span>

<span data-ttu-id="08164-p103">이 섹션에서는 부풀려졌거나 불필요한 설명 없이 절차를 제공합니다. 질문이 있거나 자세한 내용을 원할 경우 항목의 나머지 부분을 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08164-p103">This section presents the procedures without fanfare or superfluous explanation. If you have questions or want more information, you can read rest of the topic.</span></span>
  
<span data-ttu-id="08164-114">조직의 모든 사용자 계정 및 라이선스 상태 목록을 보려면 Office 365 PowerShell에서 다음 명령을 실행하세요.</span><span class="sxs-lookup"><span data-stu-id="08164-114">To view the list of all user accounts and their licensing status in your organization, run the following command in Office 365 PowerShell:</span></span>
  
```
Get-MsolUser -All
```

<span data-ttu-id="08164-115">조직의 모든 허가 되지 않은 사용자 계정 목록을 보려면 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="08164-115">To view the list of all unlicensed user accounts in your organization, run the following command:</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly
```

<span data-ttu-id="08164-116">전체 목록을 보려면 다음 명령을 실행 하 여 조직에 있는 사용자 계정의 라이센스:</span><span class="sxs-lookup"><span data-stu-id="08164-116">To view the list of all licensed user accounts in your organization, run the following command:</span></span>
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true}
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a><span data-ttu-id="08164-117">긴 버전 (명령에 대 한 세부 정보)</span><span class="sxs-lookup"><span data-stu-id="08164-117">The long version (instructions with detailed explanations)</span></span>

<span data-ttu-id="08164-p104">Office 365 사용자 계정 및 Office 365 라이선스는 일대일로 맞출 필요가 없습니다. Office 365 사용자에게 Office 365 라이선스가 없을 수도 있고 사용자에게 할당되지 않은 Office 365 라이선스가 있을 수도 있습니다. 실제로 단일 사용자 계정에서 *여러* Office 365 라이선스를 보유할 수도 있습니다. 새 Office 365 사용자 계정을 만들 경우(자세한 내용은[ Windows PowerShell을 통해 Office 365 사용자에게 라이선스 할당](http://technet.microsoft.com/library/0ab9fcac-e5ea-4b5b-b72c-8c92c55565ac.aspx) 문서 참조) 해당 사용자에게 라이선스를 할당할 필요가 없습니다. 이 경우 새 사용자는 유효한 계정이 있지만 Office 365에 로그인할 수 없습니다. 로그인을 시도하면 다음과 유사한 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="08164-p104">Office 365 user accounts and Office 365 licenses don't need to have a one-to-one correspondence: it's possible to have Office 365 users who do not have an Office 365 license, and it's possible to have Office 365 licenses that haven't been assigned to a user. (In fact, a single user account can even have  *multiple*  Office 365 licenses.) When you create a new Office 365 user account (see the article [License Office 365 users with Windows PowerShell](http://technet.microsoft.com/library/0ab9fcac-e5ea-4b5b-b72c-8c92c55565ac.aspx) for more information) you don't have to assign that user a license: the new user will have a valid account, but he or she won't be able to sign in to Office 365. If they try to sign in, they'll see something similar to this:</span></span>
  
![유효한 Office 365 라이선스가 없는 사용자](images/o365_powershell_no_license.png)
  
<span data-ttu-id="08164-p105">마찬가지로 유급 휴가나 출산 휴가 등 일정 기간 휴직할 사용자가 있을 수 있습니다. 이 경우 해당 사용자의 사용자 계정을 그대로 유지한 채(즉, 주소, 휴대폰 번호 등의 모든 속성 값을 그대로 유지) 라이선스를 제거할 수 있습니다. 그런 다음 해당 라이선스를 다른 사용자(즉, 해당 사용자 대신 업무에 투입된 임시 작업자)에게 할당할 수 있습니다. 사용자가 복귀하면 새 라이선스를 발급하여 이전처럼 작업을 재개할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08164-p105">Likewise, you might have a user who will be taking some extended time off, perhaps for a sabbatical or for maternity/paternity leave. In a case like that, you could remove the user's license but leave the user account intact (that is, leave all its property values, such as address and phone number, as-is). By doing that, you can assign their license to someone else (like, say, a temporary worker filling in for the person on leave). When the user returns to work you can issue them a new license and they'll be able to resume working as if they'd never been gone.</span></span>
  
<span data-ttu-id="08164-p106">이는 계정이 있지만 라이선스가 없는 사용자를 유지할 수 있으며 그 반대의 경우도 가능함을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="08164-p106">Which simply means that, yes, you can have users who have accounts but who don't have licenses. Or vice-versa.</span></span>
  
<span data-ttu-id="08164-p107">[Office 365 PowerShell을 사용하여 라이선스 및 서비스 보기](view-licenses-and-services-with-office-365-powershell.md) 문서에서는 조직이 구매한 Office 365 라이선스 수와 사용자에게 할당된 라이선스 수를 를 확인하는 방법과 사용자에게 할당된 해당 라이선스의 수를 확인하는 방법을 설명합니다. 이것은 중요한 정보입니다. 이러한 라이선스가 할당된 사용자와 할당되지 않은 사용자를 파악하는 것도 마찬가지로 중요합니다. 또한 이 문서에서는 이러한 정보를 확인하는 방법도 알려줍니다.</span><span class="sxs-lookup"><span data-stu-id="08164-p107">The article [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md) explains how you can determine the number of Office 365 licenses your organization has purchased as well as how many of those licenses have been assigned to users. That's important information. Equally important, however is knowing which of your users have been assigned these licenses and which ones haven't. And this article will tell you how to do just that.</span></span>
  
<span data-ttu-id="08164-p108">아시다시피 **Get-MsolUser** cmdlet은 모든 Office 365 사용자 계정에 대한 정보를 반환합니다. 모든 Office 365 사용자에 대한 정보를 빠르게 확인하고 싶나요? 그렇다면 Office 365 PowerShell에서 다음 명령을 실행하세요.</span><span class="sxs-lookup"><span data-stu-id="08164-p108">As you probably know, the **Get-MsolUser** cmdlet returns information about all your Office 365 user accounts. Need some quick info about all your Office 365 users? Then run this command in Office 365 PowerShell:</span></span>
  
```
Get-MsolUser
```

<span data-ttu-id="08164-135">그러면 Get-MsolUser에서 다음과 유사한 데이터를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="08164-135">In turn, Get-MsolUser returns data similar to this:</span></span>
  
```
UserPrincipalName           DisplayName                     isLicensed
-----------------           -----------                     ----------
ZrinkaM@litwareinc.com      Zrinka Makovac                  True
BelindaN@litwareinc.com     Belinda Newman                  False
BonnieK@litwareinc.com      Bonnie Kearney                  True
FabriceC@litwareinc.com     Fabrice Canel                   True
AnneW@litwareinc.com        Anne Wallace                    True
AlexD@litwareinc.com        Alex Darrow                     True
```

<span data-ttu-id="08164-p109">위 예에서 볼 수 있듯이 반환된 속성 값 중 하나에 **isLicensed** 속성 값이 있습니다. **isLicensed**가 `False`와 같은 경우 이는 사용자에게 Office 365에 대한 라이선스가 없음을 의미합니다. 따라서 필요한 경우 사용자 목록을 스크롤하여 **isLicensed** 속성이 `False`로 설정된 사용자를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08164-p109">As you can see, one of the property values returned is for the **isLicensed** property. If **isLicensed** is equal to `False` that means that the user doesn't have a license for Office 365. In other words, and if you wanted to, you could simply scroll through your list of users and pick out the ones where the **isLicensed** property is set to `False`.</span></span>
  
<span data-ttu-id="08164-p110">사용자 목록을 스크롤하여 라이선스가 없는 사용자를 선택하는 작업은 사용자 수가 비교적 적은 경우에 효과적입니다. 그러나 사용자 수가 많은 경우에는 목록을 스크롤하는 것이 매우 지루한 작업이 될 것입니다. 또한 Windows PowerShell이 구성된 방식에 따라 스크롤이 불가능할 수도 있습니다. Windows PowerShell 콘솔에 한 번에 표시할 수 있는 출력 줄 수에는 제한이 있기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="08164-p110">At any rate, scrolling through a list of users trying to pick out the unlicensed users works as long as you have a relatively small number of users. If you have a large number of users, however, scrolling through that list will be, at best, extremely tedious. (And, depending on how Windows PowerShell has been configured, perhaps downright impossible. That's because there's a limit to the number of lines of output that can be displayed in the Windows PowerShell console at any one time.)</span></span>
  
<span data-ttu-id="08164-143">이 점을 염두에 둔다면 라이선스가 없는 사용자를 나열하는 방법은 스크롤 대신 다음 명령을 실행하는 것이 훨씬 효과적입니다.</span><span class="sxs-lookup"><span data-stu-id="08164-143">With that in mind, a much better way to list your unlicensed users is to run this command instead:</span></span>
  
```
Get-MsolUser -UnlicensedUsersOnly
```

<span data-ttu-id="08164-p111">이 명령은 Office 365에 대한 라이선스가 없는 사용자만 반환합니다. 위의 명령이 반환하는 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="08164-p111">That command returns only those users who don't have a license for Office 365. In other words:</span></span>
  
```
UserPrincipalName           DisplayName                     isLicensed
-----------------           -----------                     ----------
BelindaN@litwareinc.com     Belinda Newman                  False
```

<span data-ttu-id="08164-p112">라이선스가 없는 사용자가 한 명임을 알 수 있습니다. 그렇다면 우리에게 *라이선스가 있는* 사용자의 목록만 필요하다면 어떻게 될까요? 이러한 경우라고 해도 아주 약간 더 복잡해질 뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="08164-p112">As you can see we have one unlicensed user. And what is we only wanted a list of the  *licensed*  users? That's a tiny bit more complicated, but only the tiniest bit:</span></span>
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true}
```

<span data-ttu-id="08164-149">이 명령은 **isLicensed** 속성이 `True`인 모든 사용자 계정을 찾으며 다음과 비슷한 정보를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="08164-149">That command, which looks for all the user accounts where the **isLicensed** property is equal to `True`, returns information similar to this:</span></span>
  
```
UserPrincipalName           DisplayName                     isLicensed
-----------------           -----------                     ----------
ZrinkaM@litwareinc.com      Zrinka Makovac                  True
BonnieK@litwareinc.com      Bonnie Kearney                  True
FabriceC@litwareinc.com     Fabrice Canel                   True
AnneW@litwareinc.com        Anne Wallace                    True
AlexD@litwareinc.com        Alex Darrow                     True
```

<span data-ttu-id="08164-p113">확인할 수 있는 것처럼 Belinda Newman의 정보는 반환되지 않습니다. 그 이유는 해결하려면 Belinda 계정의 **isLicensed** 속성이 `True`로 설정되어 있지 않기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="08164-p113">As you can see, information is not returned for Belinda Newman. Why not? You got it: because the **isLicensed** property for Belinda's account is not set to `True`.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="08164-153">참고 항목</span><span class="sxs-lookup"><span data-stu-id="08164-153">See also</span></span>
<span data-ttu-id="08164-154"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="08164-154"><a name="SeeAlso"> </a></span></span>

<span data-ttu-id="08164-155">이 항목에서 사용된 cmdlet에 대한 자세한 내용은 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="08164-155">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="08164-156">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="08164-156">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [<span data-ttu-id="08164-157">Where-Object</span><span class="sxs-lookup"><span data-stu-id="08164-157">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

