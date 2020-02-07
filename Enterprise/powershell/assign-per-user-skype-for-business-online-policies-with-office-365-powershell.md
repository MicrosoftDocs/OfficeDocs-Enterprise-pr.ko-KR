---
title: Office 365 powershell 비즈니스 온라인 정책에 대 한 사용자 당 Skype 할당
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: 36743c86-46c2-46be-b9ed-ad9d4e85d186
description: '요약: Office 365 PowerShell을 사용 하 여 비즈니스용 Skype 온라인 정책에 대 한 사용자 단위 통신 설정을 할당 합니다.'
ms.openlocfilehash: b9bb38b4b93d9b18e46fc1891f52d89fd1ba9c9e
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844269"
---
# <a name="assign-per-user-skype-for-business-online-policies-with-office-365-powershell"></a><span data-ttu-id="30e67-103">Office 365 powershell 비즈니스 온라인 정책에 대 한 사용자 당 Skype 할당</span><span class="sxs-lookup"><span data-stu-id="30e67-103">Assign per-user Skype for Business Online policies with Office 365 PowerShell</span></span>

<span data-ttu-id="30e67-104">Office 365 PowerShell을 사용 하는 것은 비즈니스용 Skype 온라인 정책에 따라 사용자별 통신 설정을 효율적으로 할당 하는 효율적인 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="30e67-104">Using Office 365 PowerShell is an efficient way to assign per-user communication settings with Skype for Business Online policies.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="30e67-105">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="30e67-105">Before you begin</span></span>

<span data-ttu-id="30e67-106">다음 절차에 따라 명령을 실행 하도록 설정 합니다 (이미 완료 한 단계 건너뛰기).</span><span class="sxs-lookup"><span data-stu-id="30e67-106">Use these instructions to get set up to run the commands (skip the steps you have already completed):</span></span>
  
1. <span data-ttu-id="30e67-107">[비즈니스용 Skype Online 커넥터 모듈](https://www.microsoft.com/download/details.aspx?id=39366)을 다운로드 하 고 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="30e67-107">Download and install the [Skype for Business Online Connector module](https://www.microsoft.com/download/details.aspx?id=39366).</span></span>
    
2. <span data-ttu-id="30e67-108">Windows PowerShell 명령 프롬프트를 열고 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="30e67-108">Open a Windows PowerShell command prompt and run the following commands:</span></span> 
    
```powershell
Import-Module LyncOnlineConnector
$userCredential = Get-Credential
$sfbSession = New-CsOnlineSession -Credential $userCredential
Import-PSSession $sfbSession
```

<span data-ttu-id="30e67-109">메시지가 나타나면 비즈니스용 Skype Online 관리자 계정 이름 및 암호를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="30e67-109">When prompted, enter your Skype for Business Online administrator account name and password.</span></span>
    
## <a name="updating-external-communication-settings-for-a-user-account"></a><span data-ttu-id="30e67-110">사용자 계정에 대 한 외부 통신 설정 업데이트</span><span class="sxs-lookup"><span data-stu-id="30e67-110">Updating external communication settings for a user account</span></span>

<span data-ttu-id="30e67-111">사용자 계정에 대 한 외부 통신 설정을 변경 하려는 경우를 예로 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30e67-111">Suppose you want to change external communication settings on a user account.</span></span> <span data-ttu-id="30e67-112">예를 들어 Alex가 페더레이션 사용자와 통신할 수 있도록 허용 하려는 경우 (EnableFederationAccess이 True 인 경우) Windows Live users (EnablePublicCloudAccess와 False)는 사용 하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="30e67-112">For example, you want to allow Alex to communicate with federated users (EnableFederationAccess is equal to True) but not with Windows Live users (EnablePublicCloudAccess equals False).</span></span> <span data-ttu-id="30e67-113">이렇게 하려면 다음과 같은 두 가지 작업을 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="30e67-113">To do that, you need to do two things:</span></span>
  
1. <span data-ttu-id="30e67-114">기준을 충족하는 외부 액세스 정책을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="30e67-114">Find an external access policy that meets our criteria.</span></span>
    
2. <span data-ttu-id="30e67-115">해당 외부 액세스 정책을 Alex에게 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="30e67-115">Assign that external access policy to Alex.</span></span>
    
> [!NOTE]
>  <span data-ttu-id="30e67-116">사용자 지정 정책을 직접 만들 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="30e67-116">You can't create a custom policy all our own.</span></span> <span data-ttu-id="30e67-117">비즈니스용 Skype Online에서는 사용자 지정 정책을 만들 수 없기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="30e67-117">That's because Skype for Business Online does not allow you to create custom policies.</span></span> <span data-ttu-id="30e67-118">대신 특별히 Office 365에 대해 만들어진 정책 중 하나를 할당 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="30e67-118">Instead, you must assign one of the policies that were created specifically for Office 365.</span></span> <span data-ttu-id="30e67-119">미리 만든 정책에는 4 가지 다른 클라이언트 정책, 224 다른 회의 정책, 5 가지 다이얼 플랜, 5 다른 외부 액세스 정책, 호스트 된 음성 메일 정책 1 개 및 4 가지 음성 정책이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="30e67-119">Those pre-created policies include: 4 different client policies, 224 different conferencing policies, 5 different dial plans, 5 different external access policies, 1 hosted voicemail policy, and 4 different voice policies.</span></span>
  
<span data-ttu-id="30e67-120">그렇다면 Alex을 할당할 외부 액세스 정책을 어떻게 결정 합니까?</span><span class="sxs-lookup"><span data-stu-id="30e67-120">So how do you determine which external access policy to assign Alex?</span></span> <span data-ttu-id="30e67-121">다음 명령은 EnableFederationAccess가 True로 설정되고 EnablePublicCloudAccess가 False로 설정된 모든 외부 액세스 정책을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="30e67-121">The following command returns all the external access policies where EnableFederationAccess is set to True and EnablePublicCloudAccess is set to False:</span></span>
  
```powershell
Get-CsExternalAccessPolicy | Where-Object {$_.EnableFederationAccess -eq $True -and $_.EnablePublicCloudAccess -eq $False}
```

<span data-ttu-id="30e67-122">명령이 수행 하는 작업은 EnableFederationAccess 속성을 True로 설정 하 고 EnablePublicCloudAccess 정책이 False로 설정 되어 있는 두 가지 조건을 충족 하는 모든 정책을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="30e67-122">What the command does is return all the policies that meet two criteria: the EnableFederationAccess property is set to True, and the EnablePublicCloudAccess policy is set to False.</span></span> <span data-ttu-id="30e67-123">그런 다음이 명령은 조건을 충족 하는 하나의 정책을 반환 합니다 (FederationOnly).</span><span class="sxs-lookup"><span data-stu-id="30e67-123">In turn, that command returns one policy that meets our criteria (FederationOnly).</span></span> <span data-ttu-id="30e67-124">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="30e67-124">Here is an example:</span></span>
  
```powershell
Identity                          : Tag:FederationOnly
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : False
EnablePublicCloudAudioVideoAccess : False
EnableOutsideAccess               : True
```

> [!NOTE]
> <span data-ttu-id="30e67-125">정책 Id는 Tag: FederationOnly로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="30e67-125">The policy Identity says Tag:FederationOnly.</span></span> <span data-ttu-id="30e67-126">아시다시피 Tag: 접두사는 Microsoft Lync 2013에서 진행된 초기 사전 릴리스 작업에서 이어진 것입니다.</span><span class="sxs-lookup"><span data-stu-id="30e67-126">As it turns out, the Tag: prefix is a carryover from the early pre-release work done on Microsoft Lync 2013.</span></span> <span data-ttu-id="30e67-127">사용자에게 정책을 할당하려는 경우에는 Tag: 접두사를 제거하고 정책 이름인 FederationOnly를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="30e67-127">When it comes to assigning policies to users, you should delete the Tag: prefix and use just the policy name: FederationOnly.</span></span> 
  
<span data-ttu-id="30e67-128">이제 Alex에 할당할 정책을 알고 있으므로 [get-csexternalaccesspolicy](https://go.microsoft.com/fwlink/?LinkId=523974) cmdlet을 사용 하 여 해당 정책을 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30e67-128">Now that you know which policy to assign to Alex, we can assign that policy by using the [Grant-CsExternalAccessPolicy](https://go.microsoft.com/fwlink/?LinkId=523974) cmdlet.</span></span> <span data-ttu-id="30e67-129">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="30e67-129">Here is an example:</span></span>
  
```powershell
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName "FederationOnly"
```

<span data-ttu-id="30e67-130">정책을 할당 하는 작업은 매우 간단 하며, 사용자의 Id와 할당할 정책의 이름을 지정 하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="30e67-130">Assigning a policy is pretty simple: you simply specify the Identity of the user and the name of the policy to be assigned.</span></span> 
  
<span data-ttu-id="30e67-131">정책 및 정책 할당에 대 한 작업을 수행 하는 경우에는 한 번에 한 사용자 계정을 사용 하는 것으로 제한 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="30e67-131">And when it comes to policies and policy assignments, you're not limited to working with user accounts one a time.</span></span> <span data-ttu-id="30e67-132">페더레이션 파트너 및 Windows Live 사용자와 통신할 수 있는 모든 사용자의 목록이 필요한 경우를 예로 들어 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="30e67-132">For example, suppose you need a list of all the users who are allowed to communicate with federated partners and with Windows Live users.</span></span> <span data-ttu-id="30e67-133">여기서 해당 사용자에게는 외부 사용자 액세스 정책 FederationAndPICDefault가 이미 할당되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30e67-133">We already know that those users have been assigned the external user access policy FederationAndPICDefault.</span></span> <span data-ttu-id="30e67-134">이를 알고 있으므로 간단한 명령을 하나씩 실행 하 여 모든 사용자의 목록을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30e67-134">Because we know that, you can display a list of all those users by running one simple command.</span></span> <span data-ttu-id="30e67-135">해당 명령은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="30e67-135">Here is the command:</span></span>
  
```powershell
Get-CsOnlineUser -Filter {ExternalAccessPolicy -eq "FederationAndPICDefault"} | Select-Object DisplayName
```

<span data-ttu-id="30e67-136">이처럼 ExternalAccessPolicy 속성이 FederationAndPICDefault로 설정된 모든 사용자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="30e67-136">In other words, show us all the users where the ExternalAccessPolicy property is set to FederationAndPICDefault.</span></span> <span data-ttu-id="30e67-137">화면에 표시 되는 정보의 양을 제한 하기 위해 Select-Object cmdlet을 사용 하 여 각 사용자의 표시 이름만 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="30e67-137">(And, in order to limit the amount of information that appears onscreen, use the Select-Object cmdlet to display show us only each user's display name.)</span></span> 
  
<span data-ttu-id="30e67-138">모든 사용자 계정이 같은 정책을 사용 하도록 구성 하려면 다음 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="30e67-138">To configure all our user accounts to use that same policy, use this command:</span></span>
  
```powershell
Get-CsOnlineUser | Grant-CsExternalAccessPolicy "FederationAndPICDefault"
```

<span data-ttu-id="30e67-139">이 명령은 Get-csonlineuser를 사용 하 여 Lync에 대해 사용 하도록 설정 된 모든 사용자의 컬렉션을 반환한 다음, 모든 해당 정보를 부여-Get-csexternalaccesspolicy로 보내 컬렉션에 있는 각 사용자에 게 FederationAndPICDefault 정책을 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="30e67-139">This command uses Get-CsOnlineUser to return a collection of all the users who have been enabled for Lync, then sends all that information to Grant-CsExternalAccessPolicy, which assigns the FederationAndPICDefault policy to each and every user in the collection.</span></span>
  
<span data-ttu-id="30e67-140">또 다른 예로, 이전에 FederationAndPICDefault 정책을 할당 했 고, 이제 생각이 변경 되었으며 전역 외부 액세스 정책에 의해 관리 되는 것을 Alex 가정해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="30e67-140">As an additional example, suppose you've previously assigned Alex the FederationAndPICDefault policy and now you've changed your mind and would like him to be managed by the global external access policy.</span></span> <span data-ttu-id="30e67-141">전역 정책은 모든 사용자에 게 명시적으로 할당할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="30e67-141">You can't explicitly assign the global policy to anyone.</span></span> <span data-ttu-id="30e67-142">다른 사용자별 정책이 할당 되지 않은 경우에만 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="30e67-142">It is only used if no other per-user policy is assigned.</span></span> <span data-ttu-id="30e67-143">따라서 전역 정책에 따라 Alex를 관리 하려면 이전에 자신에 게 할당 된 사용자별 정책을 *할당* 해제 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="30e67-143">Therefore, if we want Alex to be managed by the global policy, you need to  *unassign*  any per-user policy previously assigned to him.</span></span> <span data-ttu-id="30e67-144">예제 명령은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="30e67-144">Here is an example command:</span></span>
  
```powershell
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName $Null
```

<span data-ttu-id="30e67-145">이 명령은 Alex에 할당 된 외부 액세스 정책의 이름을 null 값 ($Null)으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="30e67-145">This command sets the name of the external access policy assigned to Alex to a null value ($Null).</span></span> <span data-ttu-id="30e67-146">Null은 "nothing"을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="30e67-146">Null means "nothing".</span></span> <span data-ttu-id="30e67-147">즉, Alex에 외부 액세스 정책이 할당 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="30e67-147">In other words, no external access policy is assigned to Alex.</span></span> <span data-ttu-id="30e67-148">사용자에 게 할당 된 외부 액세스 정책이 없으면 해당 사용자는 전역 정책에 의해 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="30e67-148">When no external access policy is assigned to a user, that user then gets managed by the global policy.</span></span>
  
<span data-ttu-id="30e67-149">Windows PowerShell을 사용 하 여 사용자 계정을 사용 하지 않도록 설정 하려면 Azure Active Directory cmdlet을 사용 하 여 Alex의 비즈니스용 Skype Online 라이선스를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="30e67-149">To disable a user account using Windows PowerShell, use the Azure Active Directory cmdlets to remove Alex's Skype for Business Online license.</span></span> <span data-ttu-id="30e67-150">자세한 내용은 [Office 365 PowerShell을 사용 하 여 서비스에 대 한 액세스 비활성화](assign-licenses-to-user-accounts-with-office-365-powershell.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="30e67-150">For more information, see [Disable access to services with Office 365 PowerShell](assign-licenses-to-user-accounts-with-office-365-powershell.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="30e67-151">참고 항목</span><span class="sxs-lookup"><span data-stu-id="30e67-151">See also</span></span>

[<span data-ttu-id="30e67-152">Office 365 PowerShell을 사용하여 비즈니스용 Skype Online 관리</span><span class="sxs-lookup"><span data-stu-id="30e67-152">Manage Skype for Business Online with Office 365 PowerShell</span></span>](manage-skype-for-business-online-with-office-365-powershell.md)
  
[<span data-ttu-id="30e67-153">Office 365 PowerShell 사용한 Office 365 관리</span><span class="sxs-lookup"><span data-stu-id="30e67-153">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="30e67-154">Office 365 PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="30e67-154">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

