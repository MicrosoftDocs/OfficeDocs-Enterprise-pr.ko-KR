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
ms.openlocfilehash: 0b95c993c3795bdbe9a68e23e107ea745c15f71b
ms.sourcegitcommit: 88ede20888e2db0bb904133c0bd97726d6d65ee2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2020
ms.locfileid: "44719969"
---
# <a name="assign-per-user-skype-for-business-online-policies-with-office-365-powershell"></a><span data-ttu-id="8e485-103">Office 365 powershell 비즈니스 온라인 정책에 대 한 사용자 당 Skype 할당</span><span class="sxs-lookup"><span data-stu-id="8e485-103">Assign per-user Skype for Business Online policies with Office 365 PowerShell</span></span>

<span data-ttu-id="8e485-104">Office 365 PowerShell을 사용 하는 것은 비즈니스용 Skype 온라인 정책에 따라 사용자별 통신 설정을 효율적으로 할당 하는 효율적인 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="8e485-104">Using Office 365 PowerShell is an efficient way to assign per-user communication settings with Skype for Business Online policies.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="8e485-105">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="8e485-105">Before you begin</span></span>

<span data-ttu-id="8e485-106">다음 절차에 따라 명령을 실행 하도록 설정 합니다 (이미 완료 한 단계 건너뛰기).</span><span class="sxs-lookup"><span data-stu-id="8e485-106">Use these instructions to get set up to run the commands (skip the steps you have already completed):</span></span>
  
1. <span data-ttu-id="8e485-107">[비즈니스용 Skype Online 커넥터 모듈](https://www.microsoft.com/download/details.aspx?id=39366)을 다운로드 하 고 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e485-107">Download and install the [Skype for Business Online Connector module](https://www.microsoft.com/download/details.aspx?id=39366).</span></span>
    
2. <span data-ttu-id="8e485-108">Windows PowerShell 명령 프롬프트를 열고 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e485-108">Open a Windows PowerShell command prompt and run the following commands:</span></span> 
    
```powershell
Import-Module LyncOnlineConnector
$userCredential = Get-Credential
$sfbSession = New-CsOnlineSession -Credential $userCredential
Import-PSSession $sfbSession
```

<span data-ttu-id="8e485-109">메시지가 나타나면 비즈니스용 Skype Online 관리자 계정 이름 및 암호를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e485-109">When prompted, enter your Skype for Business Online administrator account name and password.</span></span>
    
## <a name="updating-external-communication-settings-for-a-user-account"></a><span data-ttu-id="8e485-110">사용자 계정에 대 한 외부 통신 설정 업데이트</span><span class="sxs-lookup"><span data-stu-id="8e485-110">Updating external communication settings for a user account</span></span>

<span data-ttu-id="8e485-111">사용자 계정에 대 한 외부 통신 설정을 변경 하려는 경우를 예로 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e485-111">Suppose you want to change external communication settings on a user account.</span></span> <span data-ttu-id="8e485-112">예를 들어 Alex가 페더레이션 사용자와 통신할 수 있도록 허용 하려는 경우 (EnableFederationAccess이 True 인 경우) Windows Live users (EnablePublicCloudAccess와 False)는 사용 하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8e485-112">For example, you want to allow Alex to communicate with federated users (EnableFederationAccess is equal to True) but not with Windows Live users (EnablePublicCloudAccess equals False).</span></span> <span data-ttu-id="8e485-113">이렇게 하려면 다음과 같은 두 가지 작업을 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e485-113">To do that, you need to do two things:</span></span>
  
1. <span data-ttu-id="8e485-114">기준을 충족하는 외부 액세스 정책을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="8e485-114">Find an external access policy that meets our criteria.</span></span>
    
2. <span data-ttu-id="8e485-115">해당 외부 액세스 정책을 Alex에게 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="8e485-115">Assign that external access policy to Alex.</span></span>
    
<span data-ttu-id="8e485-116">Alex을 할당할 외부 액세스 정책을 결정 하는 방법은 무엇 인가요?</span><span class="sxs-lookup"><span data-stu-id="8e485-116">How do you determine which external access policy to assign Alex?</span></span> <span data-ttu-id="8e485-117">다음 명령은 EnableFederationAccess가 True로 설정되고 EnablePublicCloudAccess가 False로 설정된 모든 외부 액세스 정책을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8e485-117">The following command returns all the external access policies where EnableFederationAccess is set to True and EnablePublicCloudAccess is set to False:</span></span>
  
```powershell
Get-CsExternalAccessPolicy -Include All| Where-Object {$_.EnableFederationAccess -eq $True -and $_.EnablePublicCloudAccess -eq $False}
```

<span data-ttu-id="8e485-118">ExternalAccessPolicy의 사용자 지정 인스턴스를 만든 경우가 아니면 해당 명령은 조건을 충족 하는 정책 하나 (FederationOnly)를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e485-118">Unless you have created any custom instances of ExternalAccessPolicy, that command returns one policy that meets our criteria (FederationOnly).</span></span> <span data-ttu-id="8e485-119">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8e485-119">Here is an example:</span></span>
  
```powershell
Identity                          : Tag:FederationOnly
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : False
EnablePublicCloudAudioVideoAccess : False
EnableOutsideAccess               : True
```

<span data-ttu-id="8e485-120">이제 Alex에 할당할 정책을 알고 있으므로 [get-csexternalaccesspolicy](https://go.microsoft.com/fwlink/?LinkId=523974) cmdlet을 사용 하 여 해당 정책을 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e485-120">Now that you know which policy to assign to Alex, we can assign that policy by using the [Grant-CsExternalAccessPolicy](https://go.microsoft.com/fwlink/?LinkId=523974) cmdlet.</span></span> <span data-ttu-id="8e485-121">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8e485-121">Here is an example:</span></span>
  
```powershell
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName "FederationOnly"
```

<span data-ttu-id="8e485-122">정책을 할당 하는 작업은 매우 간단 하며, 사용자의 Id와 할당할 정책의 이름을 지정 하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e485-122">Assigning a policy is pretty simple: you simply specify the Identity of the user and the name of the policy to be assigned.</span></span> 
  
<span data-ttu-id="8e485-123">정책 및 정책 할당에 대 한 작업을 수행 하는 경우에는 한 번에 한 사용자 계정을 사용 하는 것으로 제한 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8e485-123">And when it comes to policies and policy assignments, you're not limited to working with user accounts one a time.</span></span> <span data-ttu-id="8e485-124">페더레이션 파트너 및 Windows Live 사용자와 통신할 수 있는 모든 사용자의 목록이 필요한 경우를 예로 들어 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="8e485-124">For example, suppose you need a list of all the users who are allowed to communicate with federated partners and with Windows Live users.</span></span> <span data-ttu-id="8e485-125">여기서 해당 사용자에게는 외부 사용자 액세스 정책 FederationAndPICDefault가 이미 할당되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e485-125">We already know that those users have been assigned the external user access policy FederationAndPICDefault.</span></span> <span data-ttu-id="8e485-126">이를 알고 있으므로 간단한 명령을 하나씩 실행 하 여 모든 사용자의 목록을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e485-126">Because we know that, you can display a list of all those users by running one simple command.</span></span> <span data-ttu-id="8e485-127">해당 명령은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8e485-127">Here is the command:</span></span>
  
```powershell
Get-CsOnlineUser -Filter {ExternalAccessPolicy -eq "FederationAndPICDefault"} | Select-Object DisplayName
```

<span data-ttu-id="8e485-128">이처럼 ExternalAccessPolicy 속성이 FederationAndPICDefault로 설정된 모든 사용자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e485-128">In other words, show us all the users where the ExternalAccessPolicy property is set to FederationAndPICDefault.</span></span> <span data-ttu-id="8e485-129">화면에 표시 되는 정보의 양을 제한 하기 위해 Select-Object cmdlet을 사용 하 여 각 사용자의 표시 이름만 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e485-129">(And, in order to limit the amount of information that appears onscreen, use the Select-Object cmdlet to display show us only each user's display name.)</span></span> 
  
<span data-ttu-id="8e485-130">모든 사용자 계정이 같은 정책을 사용 하도록 구성 하려면 다음 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e485-130">To configure all our user accounts to use that same policy, use this command:</span></span>
  
```powershell
Get-CsOnlineUser | Grant-CsExternalAccessPolicy "FederationAndPICDefault"
```

<span data-ttu-id="8e485-131">이 명령은 Get-csonlineuser를 사용 하 여 Lync에 대해 사용 하도록 설정 된 모든 사용자의 컬렉션을 반환한 다음, 모든 해당 정보를 부여-Get-csexternalaccesspolicy로 보내 컬렉션에 있는 각 사용자에 게 FederationAndPICDefault 정책을 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e485-131">This command uses Get-CsOnlineUser to return a collection of all the users who have been enabled for Lync, then sends all that information to Grant-CsExternalAccessPolicy, which assigns the FederationAndPICDefault policy to each and every user in the collection.</span></span>
  
<span data-ttu-id="8e485-132">또 다른 예로, 이전에 FederationAndPICDefault 정책을 할당 했 고, 이제 생각이 변경 되었으며 전역 외부 액세스 정책에 의해 관리 되는 것을 Alex 가정해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="8e485-132">As an additional example, suppose you've previously assigned Alex the FederationAndPICDefault policy and now you've changed your mind and would like him to be managed by the global external access policy.</span></span> <span data-ttu-id="8e485-133">전역 정책은 모든 사용자에 게 명시적으로 할당할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8e485-133">You can't explicitly assign the global policy to anyone.</span></span> <span data-ttu-id="8e485-134">대신 해당 사용자에 게 할당 된 사용자별 정책이 없는 경우 지정 된 사용자에 게 글로벌 정책이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e485-134">Instead, the global policy is used for a given user if no per-user policy is assigned to that user.</span></span> <span data-ttu-id="8e485-135">따라서 전역 정책에 따라 Alex를 관리 하려면 이전에 자신에 게 할당 된 사용자별 정책을 *할당* 해제 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e485-135">Therefore, if we want Alex to be managed by the global policy, you need to  *unassign*  any per-user policy previously assigned to him.</span></span> <span data-ttu-id="8e485-136">예제 명령은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8e485-136">Here is an example command:</span></span>
  
```powershell
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName $Null
```

<span data-ttu-id="8e485-137">이 명령은 Alex에 할당 된 외부 액세스 정책의 이름을 null 값 ($Null)으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e485-137">This command sets the name of the external access policy assigned to Alex to a null value ($Null).</span></span> <span data-ttu-id="8e485-138">Null은 "nothing"을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e485-138">Null means "nothing".</span></span> <span data-ttu-id="8e485-139">즉, Alex에 외부 액세스 정책이 할당 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8e485-139">In other words, no external access policy is assigned to Alex.</span></span> <span data-ttu-id="8e485-140">사용자에 게 할당 된 외부 액세스 정책이 없으면 해당 사용자는 전역 정책에 의해 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e485-140">When no external access policy is assigned to a user, that user then gets managed by the global policy.</span></span>
  

## <a name="managing-large-numbers-of-users"></a><span data-ttu-id="8e485-141">다 수의 사용자 관리</span><span class="sxs-lookup"><span data-stu-id="8e485-141">Managing large numbers of users</span></span>

<span data-ttu-id="8e485-142">많은 수의 사용자 (1000 이상)를 관리 하려면 [Invoke](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/invoke-command?view=powershell-7) cmdlet을 사용 하 여 스크립트 블록을 통해 명령을 일괄 처리 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e485-142">To manage large numbers of users (1000 or more), you need to batch the commands via a script block using the [Invoke-Command](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/invoke-command?view=powershell-7) cmdlet.</span></span>  <span data-ttu-id="8e485-143">이전 예제에서는 cmdlet을 실행할 때마다 통화를 설정 하 고 결과를 기다린 후에 다시 전송 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e485-143">In previous examples, each time a cmdlet is executed, it must set up the call and then wait for the result before sending it back.</span></span>  <span data-ttu-id="8e485-144">스크립트 블록을 사용 하는 경우이를 통해 cmdlet이 원격으로 실행 되 고 완료 된 후에는 데이터를 다시 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e485-144">When using a script block, this allows the cmdlets to be executed remotely, and once completed, send the data back.</span></span> 

```powershell
Import-Module LyncOnlineConnector
$sfbSession = New-CsOnlineSession
$users = Get-CsOnlineUser -Filter { ClientPolicy -eq $null } -ResultSize 500

$batch = 50
$filter = ''
$total = $users.Count
$count = 0
    $users | ForEach-Object {
    $upn = $_.UserPrincipalName
    $filter += "(UserPrincipalName -eq '$upn')"
    $batch--
    $count++
    if (($batch -eq 0) -or ($count -eq $total)) {
        $filterSB=[ScriptBlock]::Create($filter)
        Invoke-Command -Session $s -ScriptBlock {param($f) Get-CsOnlineUser -filter $f | Grant-CsClientPolicy -PolicyName "ClientPolicyNoIMURL" -Passthru | Grant-CsExternalAccessPolicy -PolicyName "FederationAndPICDefault"} -ArgumentList $filterSB

        # Reset
        $batch = 50
        $filter = ''
    } else {
        $filter += " -or "
    }
}
```

<span data-ttu-id="8e485-145">이렇게 하면 클라이언트 정책이 없는 경우 500 사용자가 한 번에 검색 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e485-145">This will find 500 users at a time who do not have a client policy.</span></span> <span data-ttu-id="8e485-146">여기에는 클라이언트 정책 "ClientPolicyNoIMURL"과 외부 액세스 정책 "FederationAndPicDefault"가 부여 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e485-146">It will grant them the client policy "ClientPolicyNoIMURL" and the external access policy "FederationAndPicDefault".</span></span> <span data-ttu-id="8e485-147">결과가 50 그룹으로 일괄 처리 되 고 각 50의 각 배치가 원격 컴퓨터로 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e485-147">The results are batched into groups of 50 and each batch of 50 is then sent to the remote machine.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="8e485-148">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8e485-148">See also</span></span>

[<span data-ttu-id="8e485-149">Office 365 PowerShell을 통해 비즈니스용 Skype Oline 관리</span><span class="sxs-lookup"><span data-stu-id="8e485-149">Manage Skype for Business Online with Office 365 PowerShell</span></span>](manage-skype-for-business-online-with-office-365-powershell.md)
  
[<span data-ttu-id="8e485-150">Office 365 PowerShell을 사용하여 Office 365 관리</span><span class="sxs-lookup"><span data-stu-id="8e485-150">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="8e485-151">Office 365 PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="8e485-151">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
