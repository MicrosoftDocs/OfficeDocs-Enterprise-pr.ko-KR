---
title: Office 365 PowerShell을 사용 하 여 온라인 비즈니스 정책을 용 Skype 관리
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 06/26/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: ff93a341-6f0f-4f06-9690-726052e1be64
description: '요약: Office 365 PowerShell을 사용 하 여 정책으로 비즈니스용 Skype Online 사용자 계정 속성을 관리 합니다.'
ms.openlocfilehash: 1d4f6bc52932bb7315fdd769788b5b3108423424
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2019
ms.locfileid: "38748528"
---
# <a name="manage-skype-for-business-online-policies-with-office-365-powershell"></a><span data-ttu-id="98f5a-103">Office 365 PowerShell을 사용 하 여 온라인 비즈니스 정책을 용 Skype 관리</span><span class="sxs-lookup"><span data-stu-id="98f5a-103">Manage Skype for Business Online policies with Office 365 PowerShell</span></span>

<span data-ttu-id="98f5a-104">비즈니스용 Skype Online에 대 한 사용자 계정의 여러 속성을 관리 하려면 Office 365 PowerShell을 사용 하 여 정책 속성으로 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="98f5a-104">To manage many properties of user account for Skype for Business Online, you must specify them as properties of policies with Office 365 PowerShell.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="98f5a-105">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="98f5a-105">Before you begin</span></span>

<span data-ttu-id="98f5a-106">다음 절차에 따라 명령을 실행 하도록 설정 합니다 (이미 완료 한 단계 건너뛰기).</span><span class="sxs-lookup"><span data-stu-id="98f5a-106">Use these instructions to get set up to run the commands (skip the steps you have already completed):</span></span>
  
1. <span data-ttu-id="98f5a-107">[비즈니스용 Skype Online 커넥터 모듈](https://www.microsoft.com/download/details.aspx?id=39366)을 다운로드 하 고 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="98f5a-107">Download and install the [Skype for Business Online Connector module](https://www.microsoft.com/download/details.aspx?id=39366).</span></span>
    
2. <span data-ttu-id="98f5a-108">Windows PowerShell 명령 프롬프트를 열고 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="98f5a-108">Open a Windows PowerShell command prompt and run the following commands:</span></span> 
    
```powershell
Import-Module SkypeOnlineConnector
$userCredential = Get-Credential
$sfbSession = New-CsOnlineSession -Credential $userCredential
Import-PSSession $sfbSession
  ```

<span data-ttu-id="98f5a-109">메시지가 나타나면 비즈니스용 Skype Online 관리자 계정 이름 및 암호를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="98f5a-109">When prompted, enter your Skype for Business Online administrator account name and password.</span></span>
    
## <a name="manage-user-account-policies"></a><span data-ttu-id="98f5a-110">사용자 계정 정책 관리</span><span class="sxs-lookup"><span data-stu-id="98f5a-110">Manage user account policies</span></span>

<span data-ttu-id="98f5a-111">많은 비즈니스용 Skype Online 사용자 계정 속성은 정책을 사용 하 여 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="98f5a-111">Many Skype for Business Online user account properties are configured by using policies.</span></span> <span data-ttu-id="98f5a-112">정책은 하나 이상의 사용자에 게 적용할 수 있는 설정의 모음 뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="98f5a-112">Policies are simply collections of settings that can be applied to one or more users.</span></span> <span data-ttu-id="98f5a-113">정책 구성에 대 한 자세한 내용을 보려면 FederationAndPICDefault 정책에 대해이 명령 예를 실행 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="98f5a-113">To take a look at how the a policy has been configured, you can run this example command for the FederationAndPICDefault policy:</span></span>
  
```powershell
Get-CsExternalAccessPolicy -Identity "FederationAndPICDefault"
```

<span data-ttu-id="98f5a-114">그러면 다음과 비슷한 결과가 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="98f5a-114">In turn, you should get back something similar to this:</span></span>
  
```powershell
Identity                          : Tag:FederationAndPICDefault
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : True
EnablePublicCloudAudioVideoAccess : True
EnableOutsideAccess               : True
```

<span data-ttu-id="98f5a-115">이 예에서이 정책 내의 값은 페더레이션 사용자와의 통신에 사용 될 수 있는 작업을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="98f5a-115">In this example, the values within this policy determine what a use can or cannot do when it comes to communicating with federated users.</span></span> <span data-ttu-id="98f5a-116">예를 들어 사용자가 조직 외부의 사용자와 통신할 수 있도록 Enableout간 액세스 속성을 True로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="98f5a-116">For example, the EnableOutsideAccess property must be set to True for a user to be able to communicate with people outside the organization.</span></span> <span data-ttu-id="98f5a-117">이 속성은 Microsoft 365 관리 센터에 나타나지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="98f5a-117">Note that this property does not appear in the Microsoft 365 admin center.</span></span> <span data-ttu-id="98f5a-118">대신 사용자가 선택한 다른 항목에 따라 속성이 자동으로 True 또는 False로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="98f5a-118">Instead, the property is automatically set to True or False based on the other selections that you make.</span></span> <span data-ttu-id="98f5a-119">다른 두 가지 주요 속성은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="98f5a-119">The other two properties of interest are:</span></span>
  
- <span data-ttu-id="98f5a-120">**EnableFederationAccess** 는 사용자가 페더레이션 도메인의 사용자와 통신할 수 있는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="98f5a-120">**EnableFederationAccess** indicates whether the user can communicate with people from federated domains.</span></span>
    
- <span data-ttu-id="98f5a-121">**Enablepubliccloudaccess** 는 사용자가 Windows Live 사용자와 통신할 수 있는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="98f5a-121">**EnablePublicCloudAccess** indicates whether the user can communicate with Windows Live users.</span></span>
    
<span data-ttu-id="98f5a-122">따라서 사용자 계정 (예: **EnableFederationAccess $True**)에서 페더레이션 관련 속성을 직접 변경 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="98f5a-122">Therefore, you don't directly change federation-related properties on user accounts (for example, **Set-CsUser -EnableFederationAccess $True**).</span></span> <span data-ttu-id="98f5a-123">대신 미리 구성 된 원하는 속성 값을 가진 외부 액세스 정책에 계정을 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="98f5a-123">Instead, you assign an account an external access policy that has the desired property values preconfigured.</span></span> <span data-ttu-id="98f5a-124">사용자가 페더레이션 사용자와 Windows Live 사용자와 통신할 수 있게 하려면 해당 사용자 계정에 이러한 유형의 통신을 허용 하는 정책이 할당 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="98f5a-124">If we want a user to be able to communicate with federated users and with Windows Live users, that user account must be assigned a policy that allows those types of communication.</span></span>
  
<span data-ttu-id="98f5a-125">누군가가 조직 외부의 사용자와 통신할 수 있는지 여부를 확인 하려면 다음을 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="98f5a-125">If you want to know whether or not someone can communicate with users from outside the organization, you have to:</span></span>
  
- <span data-ttu-id="98f5a-126">해당 사용자에 게 할당 된 외부 액세스 정책을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="98f5a-126">Determine which external access policy has been assigned to that user.</span></span>
    
- <span data-ttu-id="98f5a-127">해당 정책에서 허용 되는 기능을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="98f5a-127">Determine which capabilities are or are not allowed by that policy.</span></span>
    
<span data-ttu-id="98f5a-128">예를 들어 다음 명령을 사용 하 여이 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98f5a-128">For example, you can do that by using this command:</span></span>
  
```powershell
Get-CsOnlineUser -Identity "Alex Darrow" | ForEach {Get-CsExternalAccessPolicy -Identity $_.ExternalAccessPolicy}
```

<span data-ttu-id="98f5a-129">이 명령은 사용자에 게 할당 된 정책을 찾은 다음 해당 정책 내에서 사용 하거나 사용 하지 않도록 설정 된 기능을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="98f5a-129">This command finds the policy assigned to the user, then finds the capabilities enabled or disabled within that policy.</span></span>
  
<span data-ttu-id="98f5a-130">PowerShell을 사용 하 여 비즈니스용 Skype Online 정책을 관리 하려면 다음에 대 한 cmdlet을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="98f5a-130">To manage Skype for Business Online policies with PowerShell, see the cmdlets for:</span></span>

- <span data-ttu-id="98f5a-131">[클라이언트 정책](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#client-policy-cmdlets)</span><span class="sxs-lookup"><span data-stu-id="98f5a-131">[Client policy](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#client-policy-cmdlets)</span></span>
- <span data-ttu-id="98f5a-132">[회의 정책](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#conferencing-policy-cmdlets)</span><span class="sxs-lookup"><span data-stu-id="98f5a-132">[Conferencing policy](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#conferencing-policy-cmdlets)</span></span>
- <span data-ttu-id="98f5a-133">[모바일 정책](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#mobile-policy-cmdlets)</span><span class="sxs-lookup"><span data-stu-id="98f5a-133">[Mobile policy](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#mobile-policy-cmdlets)</span></span>
- <span data-ttu-id="98f5a-134">[온라인 음성 메일 정책](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#online-voicemail-policy-cmdlets)</span><span class="sxs-lookup"><span data-stu-id="98f5a-134">[Online Voicemail policy](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#online-voicemail-policy-cmdlets)</span></span>
- <span data-ttu-id="98f5a-135">[음성 라우팅 정책](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#voice-routing-policy-cmdlets)</span><span class="sxs-lookup"><span data-stu-id="98f5a-135">[Voice Routing policy](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#voice-routing-policy-cmdlets)</span></span>


> [!NOTE]
> <span data-ttu-id="98f5a-136">비즈니스용 Skype Online 다이얼 플랜은 이름을 제외한 모든 관점에서 정책입니다.</span><span class="sxs-lookup"><span data-stu-id="98f5a-136">A Skype for Business Online dial plan is a policy in every respect except the name.</span></span> <span data-ttu-id="98f5a-137">Office Communications Server 및 Exchange와의 이전 버전과의 호환성을 제공 하기 위해 "전화 걸기 정책" 대신 "다이얼 플랜" 이라는 이름이 선택 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="98f5a-137">The name "dial plan" was chosen instead of, say, "dialing policy" in order to provide backward compatibility with Office Communications Server and with Exchange.</span></span> 
  
<span data-ttu-id="98f5a-138">예를 들어 사용 가능한 모든 음성 정책을 확인 하려면 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="98f5a-138">For example, to look at all the voice policies available for your use, run this command:</span></span>
  
```powershell
Get-CsVoicePolicy
```

> [!NOTE]
> <span data-ttu-id="98f5a-139">그러면 사용할 수 있는 모든 음성 정책의 목록이 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="98f5a-139">That returns a list of all the voice policies available to you.</span></span> <span data-ttu-id="98f5a-140">그러나 모든 정책을 모든 사용자에 게 할당할 수 있는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="98f5a-140">Keep in mind, however, that not all policies can be assigned to all users.</span></span> <span data-ttu-id="98f5a-141">이는 라이선스 및 지리적 위치를 포함 하는 다양 한 제한으로 인해 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="98f5a-141">This is due to various restrictions involving licensing and geographic location.</span></span> <span data-ttu-id="98f5a-142">("[사용 위치](https://msdn.microsoft.com/library/azure/dn194136.aspx)" 라고 부르는 ") 특정 사용자에 게 할당할 수 있는 외부 액세스 정책 및 회의 정책을 확인 하려면 다음과 같은 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="98f5a-142">(The so-called "[usage location](https://msdn.microsoft.com/library/azure/dn194136.aspx).") If you want to know the external access policies and the conferencing policies that can be assigned to a particular user, use commands similar to these:</span></span> 

```powershell
Get-CsConferencingPolicy -ApplicableTo "Alex Darrow"
Get-CsExternalAccessPolicy -ApplicableTo "Alex Darrow"
```

<span data-ttu-id="98f5a-143">적용 범위 Ableto 매개 변수는 반환 된 데이터를 지정 된 사용자에 게 할당할 수 있는 정책 (예: Alex Darrow)으로 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="98f5a-143">The ApplicableTo parameter limits the returned data to policies that can be assigned to the specified user (for example, Alex Darrow).</span></span> <span data-ttu-id="98f5a-144">라이선스 및 사용 위치 제한에 따라 사용 가능한 모든 정책의 하위 집합을 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98f5a-144">Depending on licensing and usage location restrictions, that might represent a subset of all the available policies.</span></span> 
  
<span data-ttu-id="98f5a-145">정책 속성이 Office 365에서 사용 되지 않는 경우도 있고, 일부 경우에는 Microsoft 지원 담당자만 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98f5a-145">In some cases, properties of policies are not used with Office 365, while others can only be managed by Microsoft support personnel.</span></span> 
  
<span data-ttu-id="98f5a-146">비즈니스용 Skype를 사용 하는 경우 사용자는 일종의 정책에 따라 관리 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="98f5a-146">With Skype for Business Online, users must be managed by a policy of some kind.</span></span> <span data-ttu-id="98f5a-147">유효한 정책 관련 속성이 비어 있는 경우에는 해당 사용자가 사용자 단위 정책을 특별히 할당 하지 않으면 사용자에 게 자동으로 적용 되는 정책 인 전역 정책에 의해 관리 되 고 있음을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="98f5a-147">If a valid policy-related property is blank, that means that the user in question is being managed by a global policy, which is a policy that is automatically applied to a user unless he or she is specifically assigned a per-user policy.</span></span> <span data-ttu-id="98f5a-148">사용자 계정에 대해 나열 된 클라이언트 정책이 표시 되지 않으므로 글로벌 정책에 의해 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="98f5a-148">Because we don't see a client policy listed for a user account, it is managed by the global policy.</span></span> <span data-ttu-id="98f5a-149">다음 명령을 사용 하 여 전역 클라이언트 정책을 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98f5a-149">You can determine the global client policy with this command:</span></span>
  
```powershell
Get-CsClientPolicy -Identity "Global"
```

## <a name="see-also"></a><span data-ttu-id="98f5a-150">참고 항목</span><span class="sxs-lookup"><span data-stu-id="98f5a-150">See also</span></span>

[<span data-ttu-id="98f5a-151">Office 365 PowerShell을 사용하여 비즈니스용 Skype Online 관리</span><span class="sxs-lookup"><span data-stu-id="98f5a-151">Manage Skype for Business Online with Office 365 PowerShell</span></span>](manage-skype-for-business-online-with-office-365-powershell.md)
  
[<span data-ttu-id="98f5a-152">Office 365 PowerShell 사용한 Office 365 관리</span><span class="sxs-lookup"><span data-stu-id="98f5a-152">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="98f5a-153">Office 365 PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="98f5a-153">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

