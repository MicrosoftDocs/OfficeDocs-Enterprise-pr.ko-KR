---
title: "Office 365 PowerShell을 사용 하 여 온라인 비즈니스 정책을 용 Skype 관리"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: DecEntMigration
ms.assetid: ff93a341-6f0f-4f06-9690-726052e1be64
description: "요약:는 Office 365 PowerShell을 사용 하 여 Skype 정책 사용 하 여 비즈니스 온라인 사용자 계정 속성을 관리할 수 있습니다."
ms.openlocfilehash: 9b3877d2680b2b36d155cb5dd2a69fa21c972fe3
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2017
---
# <a name="manage-skype-for-business-online-policies-with-office-365-powershell"></a><span data-ttu-id="2d6bd-103">Office 365 PowerShell을 사용 하 여 온라인 비즈니스 정책을 용 Skype 관리</span><span class="sxs-lookup"><span data-stu-id="2d6bd-103">Manage Skype for Business Online policies with Office 365 PowerShell</span></span>

 <span data-ttu-id="2d6bd-104">**요약:** Office 365 PowerShell을 사용 하 여 정책 사용 하 여 비즈니스 온라인 사용자 계정 속성에 대 한 사용자 Skype 관리.</span><span class="sxs-lookup"><span data-stu-id="2d6bd-104">**Summary:** Use Office 365 PowerShell to manage your Skype for Business Online user account properties with policies.</span></span>
  
<span data-ttu-id="2d6bd-105">사용자 계정에 대 한 여러 속성이 Skype에 대 한 비즈니스 online을 관리 하려면 Office 365 powershell 정책의 속성으로 지정 해야 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d6bd-105">To manage many properties of user account for Skype for Business Online, you must specify them as properties of policies with Office 365 PowerShell.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="2d6bd-106">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="2d6bd-106">Before you begin</span></span>

<span data-ttu-id="2d6bd-107">다음이 절차에 따라 사용 하도록 설정 가져오기 명령을 실행 (이미 완료 된 단계를 건너뛰고):</span><span class="sxs-lookup"><span data-stu-id="2d6bd-107">Use these instructions to get set up to run the commands (skip the steps you have already completed):</span></span>
  
1. <span data-ttu-id="2d6bd-108">다운로드 하 고 [비즈니스 온라인 커넥터 모듈에 대 한 Skype](https://www.microsoft.com/en-us/download/details.aspx?id=39366)를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d6bd-108">Download and install the [Skype for Business Online Connector module](https://www.microsoft.com/en-us/download/details.aspx?id=39366).</span></span>
    
2. <span data-ttu-id="2d6bd-109">Windows PowerShell 명령 프롬프트를 열고 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d6bd-109">Open a Windows PowerShell command prompt and run the following commands:</span></span> 
    
```
Import-Module LyncOnlineConnector
$userCredential = Get-Credential
$sfbSession = New-CsOnlineSession -Credential $userCredential
Import-PSSession $sfbSession
  ```

<span data-ttu-id="2d6bd-110">대화 상자가 나타나면 비즈니스 온라인 관리자 계정 이름 및 암호에 대 한 사용자 Skype를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d6bd-110">When prompted, enter your Skype for Business Online administrator account name and password.</span></span>
    
## <a name="manage-user-account-policies"></a><span data-ttu-id="2d6bd-111">사용자 계정 정책 관리</span><span class="sxs-lookup"><span data-stu-id="2d6bd-111">Manage user account policies</span></span>

<span data-ttu-id="2d6bd-p101">비즈니스 온라인 사용자 계정 속성에 대 한 많은 Skype 정책을 사용 하 여 구성 됩니다. 정책은 단순히 설정 컬렉션을 하나 이상의 사용자에 게 적용할 수 있는 됩니다. 방법에 대 한 정보를 사용 하는 정책이 구성 되었는지, FederationAndPICDefault 정책에 대 한이 예에서는 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d6bd-p101">Many Skype for Business Online user account properties are configured by using policies. Policies are simply collections of settings that can be applied to one or more users. To take a look at how the a policy has been configured, you can run this example command for the FederationAndPICDefault policy:</span></span>
  
```
Get-CsExternalAccessPolicy -Identity "FederationAndPICDefault"
```

<span data-ttu-id="2d6bd-115">차례로 않았다고 다시 다음과 비슷한 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2d6bd-115">In turn, you should get back something similar to this:</span></span>
  
```
Identity                          : Tag:FederationAndPICDefault
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : True
EnablePublicCloudAudioVideoAccess : True
EnableOutsideAccess               : True
```

<span data-ttu-id="2d6bd-p102">이 예제에서는이 정책에 포함 된 값을 사용할 수 있는 확인 또는 페더레이션된 사용자와의 통신에 있어 할 수 없는 합니다. 예, EnableOutsideAccess 속성은 사용자 조직 외부의 사용자와 통신할 수 있도록 하려면 True로 설정 해야 합니다. 이 속성은 Office 365 관리 센터에 나타나지 않는 메모 합니다. 대신 속성은 True로 자동 설정 또는 false를 반환 하는 다른 선택 영역에 기반 합니다. 관심 다른 두 속성은:</span><span class="sxs-lookup"><span data-stu-id="2d6bd-p102">In this example, the values within this policy determine what a use can or cannot do when it comes to communicating with federated users. For example, the EnableOutsideAccess property must be set to True for a user to be able to communicate with people outside the organization. Note that this property does not appear in the Office 365 Admin center. Instead, the property is automatically set to True or False based on the other selections that you make. The other two properties of interest are:</span></span>
  
- <span data-ttu-id="2d6bd-121">**EnableFederationAccess** 는 사용자가 페더레이션된 도메인의에서 사용자와 통신할 수 있는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2d6bd-121">**EnableFederationAccess** indicates whether the user can communicate with people from federated domains.</span></span>
    
- <span data-ttu-id="2d6bd-122">**EnablePublicCloudAccess** 는 사용자 Windows Live 사용자와 통신할 수 있는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2d6bd-122">**EnablePublicCloudAccess** indicates whether the user can communicate with Windows Live users.</span></span>
    
<span data-ttu-id="2d6bd-p103">따라서 사용자 계정 (예: **Set-csuser-EnableFederationAccess $True**)에서 페더레이션과 관련 된 속성을 직접 변경 하지 않습니다. 대신이 계정을 미리 구성 된 원하는 속성 값을 갖는 외부 액세스 정책을 할당 합니다. Windows Live 사용자와 페더레이션된 사용자와 통신할 수 있도록 사용자를 원합니다 하는 경우 해당 사용자 계정은 이러한 유형의 통신을 허용 하는 정책을 할당 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d6bd-p103">Therefore, you don't directly change federation-related properties on user accounts (for example, **Set-CsUser -EnableFederationAccess $True**). Instead, you assign an account an external access policy that has the desired property values preconfigured. If we want a user to be able to communicate with federated users and with Windows Live users, that user account must be assigned a policy that allows those types of communication.</span></span>
  
<span data-ttu-id="2d6bd-126">다른 사용자 조직 외부의 사용자와 통신할 수 있는지 여부를 확인 하려는 경우 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d6bd-126">If you want to know whether or not someone can communicate with users from outside the organization, you have to:</span></span>
  
- <span data-ttu-id="2d6bd-127">해당 사용자에게 할당된 외부 액세스 정책 확인</span><span class="sxs-lookup"><span data-stu-id="2d6bd-127">Determine which external access policy has been assigned to that user.</span></span>
    
- <span data-ttu-id="2d6bd-128">해당 정책에서 허용되거나 허용되지 않는 기능 확인</span><span class="sxs-lookup"><span data-stu-id="2d6bd-128">Determine which capabilities are or are not allowed by that policy.</span></span>
    
<span data-ttu-id="2d6bd-129">예,이 명령을 사용 하 여를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d6bd-129">For example, you can do that by using this command:</span></span>
  
```
Get-CsOnlineUser -Identity "Alex Darrow" | ForEach {Get-CsExternalAccessPolicy -Identity $_.ExternalAccessPolicy}
```

<span data-ttu-id="2d6bd-130">이 명령은 사용자, 다음 기능 사용 하거나 사용 하지 않도록를 설정 하 여 해당 정책 내에서 검색에 할당 된 정책을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="2d6bd-130">This command finds the policy assigned to the user, then finds the capabilities enabled or disabled within that policy.</span></span>
  
<span data-ttu-id="2d6bd-p104">정책 수정 또는 만들기 (영문)에 대 한 없는 cmdlet은 메모 합니다. Office 365에서 제공한 미리 정책을 사용 해야 합니다. 사용할 수 있는 다른 정책에 대 한 정보를 사용 하려는 경우에 이러한 명령을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d6bd-p104">Note that there are no cmdlets for creating or for modifying policies. You must use the policies pre-supplied by Office 365. If you want to take a look at the different policies available, you can use these commands:</span></span>
  
- <span data-ttu-id="2d6bd-134">Get-csclientpolicy</span><span class="sxs-lookup"><span data-stu-id="2d6bd-134">Get-CsClientPolicy</span></span>       
- <span data-ttu-id="2d6bd-135">Get-csconferencingpolicy</span><span class="sxs-lookup"><span data-stu-id="2d6bd-135">Get-CsConferencingPolicy</span></span>        
- <span data-ttu-id="2d6bd-136">Get-csdialplan</span><span class="sxs-lookup"><span data-stu-id="2d6bd-136">Get-CsDialPlan</span></span>            
- <span data-ttu-id="2d6bd-137">Get-csexternalaccesspolicy</span><span class="sxs-lookup"><span data-stu-id="2d6bd-137">Get-CsExternalAccessPolicy</span></span>                         
- <span data-ttu-id="2d6bd-138">Get-cshostedvoicemailpolicy</span><span class="sxs-lookup"><span data-stu-id="2d6bd-138">Get-CsHostedVoicemailPolicy</span></span>                        
- <span data-ttu-id="2d6bd-139">Get-cspresencepolicy</span><span class="sxs-lookup"><span data-stu-id="2d6bd-139">Get-CsPresencePolicy</span></span>                               
- <span data-ttu-id="2d6bd-140">Get-csvoicepolicy</span><span class="sxs-lookup"><span data-stu-id="2d6bd-140">Get-CsVoicePolicy</span></span>                                  

> [!NOTE]
> <span data-ttu-id="2d6bd-p105">비즈니스 온라인 다이얼 플랜에 대 한 Skype에 이름 제외한 모든 측면에서 정책입니다. 예: "전화를 걸 정책" 대신 "다이얼 플랜" 이름 선택 되었습니다 Office Communications Server와 Exchange 이전 버전과 호환성을 제공할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d6bd-p105">A Skype for Business Online dial plan is a policy in every respect except the name. The name "dial plan" was chosen instead of, say, "dialing policy" in order to provide backward compatibility with Office Communications Server and with Exchange.</span></span> 
  
<span data-ttu-id="2d6bd-143">등 전혀 확인에 사용 하기 위해 사용할 수 있는 음성 정책이이 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d6bd-143">For example, to look at all the voice policies available for your use, run this command:</span></span>
  
```
Get-CsVoicePolicy
```

> [!NOTE]
> <span data-ttu-id="2d6bd-p106">사용자의 사용 가능한 모든 음성 정책 목록을 반환합니다. 그러나 일부 정책을 모든 사용자에 게 할당할 수 있는 염두에 두어야 합니다. 라이선스 및 지리적 위치와 관련 된 다양 한 제한으로 인해입니다. (즉, "[사용 현황 위치](https://msdn.microsoft.com/en-us/library/azure/dn194136.aspx)입니다.") 외부 액세스 정책 및 특정 사용자에 게 할당할 수 있는 회의 정책 확인 하려는 경우에 다음과 유사한 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d6bd-p106">That returns a list of all the voice policies available to you. Keep in mind, however, that not all policies can be assigned to all users. This is due to various restrictions involving licensing and geographic location. (The so-called "[usage location](https://msdn.microsoft.com/en-us/library/azure/dn194136.aspx).") If you want to know the external access policies and the conferencing policies that can be assigned to a particular user, use commands similar to these:</span></span> 

```
Get-CsConferencingPolicy -ApplicableTo "Alex Darrow"
Get-CsExternalAccessPolicy -ApplicableTo "Alex Darrow"
```

<span data-ttu-id="2d6bd-p107">ApplicableTo 매개 변수는 반환되는 데이터를 지정된 사용자(여기서는 Alex Darrow)에게 할당 가능한 정책으로 제한합니다. 라이선스 및 사용 위치 제한에 따라 사용 가능한 모든 정책 중 일부분이 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d6bd-p107">The ApplicableTo parameter limits the returned data to policies that can be assigned to the specified user (for example, Alex Darrow). Depending on licensing and usage location restrictions, that might represent a subset of all the available policies.</span></span> 
  
<span data-ttu-id="2d6bd-150">경우에 따라 정책의 속성은 Microsoft 지원 담당자 여만 관리할 수 있는 다른 사용자에 게 하는 동안 Office 365와 함께 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2d6bd-150">In some cases, properties of policies are not used with Office 365, while others can only be managed by Microsoft support personnel.</span></span> 
  
<span data-ttu-id="2d6bd-p108">온라인 비즈니스에 대 한 Skype와는 일종의 정책에 의해 사용자를 관리 해야 합니다. 유효한 정책 관련 속성이 비어 있으면 해당 사용자에는 자신이 사용자별 정책이 특별히 할당 하지 않은 경우 사용자에 게 자동으로 적용 되는 정책 인 전역 정책에 의해 관리 되는 것입니다. 사용자 계정에 대해 나열 된 클라이언트 정책 보이지을 하기 때문에 전역 정책에 의해 관리 됩니다. 이 명령 사용 하 여 전역 클라이언트 정책을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d6bd-p108">With Skype for Business Online, users must be managed by a policy of some kind. If a valid policy-related property is blank, that means that the user in question is being managed by a global policy, which is a policy that is automatically applied to a user unless he or she is specifically assigned a per-user policy. Because we don't see a client policy listed for a user account, it is managed by the global policy. You can determine the global client policy with this command:</span></span>
  
```
Get-CsClientPolicy -Identity "Global"
```

## <a name="see-also"></a><span data-ttu-id="2d6bd-155">See also</span><span class="sxs-lookup"><span data-stu-id="2d6bd-155">See also</span></span>

#### 

[<span data-ttu-id="2d6bd-156">Office 365 powershell 온라인 비즈니스에 대 한 Skype 관리</span><span class="sxs-lookup"><span data-stu-id="2d6bd-156">Manage Skype for Business Online with Office 365 PowerShell</span></span>](manage-skype-for-business-online-with-office-365-powershell.md)
  
[<span data-ttu-id="2d6bd-157">Office 365 PowerShell로 Office 365 관리</span><span class="sxs-lookup"><span data-stu-id="2d6bd-157">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="2d6bd-158">Office 365 PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="2d6bd-158">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

