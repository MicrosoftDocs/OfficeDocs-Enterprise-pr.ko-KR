---
title: Office 365 PowerShell을 사용 하 여 계정 라이센스와 서비스 정보 보기
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/19/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
ms.assetid: ace07d8a-15ca-4b89-87f0-abbce809b519
description: Office 365 PowerShell을 사용 하 여 사용자에 게 할당 된 Office 365 서비스를 확인 하는 방법에 설명 합니다.
ms.openlocfilehash: 5286a581a67b39d5d5ca921b998d6ea14b3ff50f
ms.sourcegitcommit: 8ff1cd7733dba438697b68f90189d4da72bbbefd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/20/2018
---
# <a name="view-account-license-and-service-details-with-office-365-powershell"></a><span data-ttu-id="3db54-103">Office 365 PowerShell을 사용 하 여 계정 라이센스와 서비스 정보 보기</span><span class="sxs-lookup"><span data-stu-id="3db54-103">View account license and service details with Office 365 PowerShell</span></span>

<span data-ttu-id="3db54-104">**요약:** Office 365 PowerShell을 사용 하 여 사용자에 게 할당 된 Office 365 서비스를 확인 하는 방법에 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="3db54-104">**Summary:** Explains how to use Office 365 PowerShell to determine the Office 365 services that have been assigned to users.</span></span>
  
<span data-ttu-id="3db54-p101">Office 365에서 라이선스를 제공 계획 라이선스를 (또한 호출된 Sku 또는 Office 365 계획) 사용자가 이러한 계획에 대해 정의 된 Office 365 서비스에 액세스 권한을 부여 합니다. 그러나 사용자 자신에 게 현재 할당 된 라이선스에서 사용할 수 있는 모든 서비스에 대 한 액세스를 권한이 없는 합니다. Office 365 PowerShell을 사용 하 여 사용자 계정에서 서비스의 상태를 보려면 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3db54-p101">In Office 365, licenses from licensing plans (also called SKUs or Office 365 plans) give users access to the Office 365 services that are defined for those plans. However, a user might not have access to all the services that are available in a license that's currently assigned to them. You can use Office 365 PowerShell to view the status of services on user accounts.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="3db54-108">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="3db54-108">Before you begin</span></span>
<span data-ttu-id="3db54-109"><a name="RTT"> </a></span><span class="sxs-lookup"><span data-stu-id="3db54-109"></span></span>

- <span data-ttu-id="3db54-p102">이 항목의 절차를 수행하려면 Office 365 PowerShell에 연결되어 있어야 합니다. 지침을 보려면 [PowerShell Office 365에 연결](connect-to-office-365-powershell.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3db54-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="3db54-112">명령을 사용 하 여 `Get-MsolAccountSku` 및 `(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus` 다음 정보를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3db54-112">Use the commands  `Get-MsolAccountSku` and `(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus` to find the following information:</span></span>
    
  - <span data-ttu-id="3db54-113">조직에서 사용할 수 있는 라이선스 계획.</span><span class="sxs-lookup"><span data-stu-id="3db54-113">The licensing plans that are available in your organization.</span></span>
    
  - <span data-ttu-id="3db54-114">각 라이선스 계획에서 사용할 수 있는 서비스 및 서비스 나열 순서(인덱스 번호).</span><span class="sxs-lookup"><span data-stu-id="3db54-114">The services that are available in each licensing plan, and the order in which they are listed (the index number).</span></span>
    
     <span data-ttu-id="3db54-115">계획, 라이선스 및 서비스 라이선스에 대 한 자세한 내용은 [보기 라이선스 및 Office 365 PowerShell을 사용 하 여 서비스를](view-licenses-and-services-with-office-365-powershell.md)참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="3db54-115">For more information about licensing plans, license, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="3db54-116">명령을 사용 하 여 `Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses` (인덱스 번호)를 나열 된 자신이 하는 사용자 및 순서에 할당 된 라이선스를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3db54-116">Use the command  `Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses` to find the licenses that are assigned to a user, and the order in which they are listed (the index number).</span></span>
    
- <span data-ttu-id="3db54-117">사용 하는 경우는 **Get-MsolUser** cmdlet을 사용 하지 않고는 _All_ 매개 변수를 처음 500 개의 계정만 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3db54-117">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 accounts are returned.</span></span>
    
<span data-ttu-id="3db54-118"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="3db54-118"></span></span>
## <a name="the-short-version-instructions-without-explanations"></a><span data-ttu-id="3db54-119">간략 한 (설명 없이 지침)</span><span class="sxs-lookup"><span data-stu-id="3db54-119">The short version (instructions without explanations)</span></span>

<span data-ttu-id="3db54-120">사용자에 액세스할 수 있는 모든 Office 365 PowerShell 서비스를 보려면 다음 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3db54-120">To view all the Office 365 PowerShell services that a user has access to, use the following syntax:</span></span>
  
```
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

<span data-ttu-id="3db54-p103">이 예제에서는 BelindaN@litwareinc.com 사용자가 액세스할 수 있는 서비스입니다. 이 사용자 계정에 할당 된 모든 라이선스와 연결 된 서비스를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="3db54-p103">This example shows the services to which the user BelindaN@litwareinc.com has access. This shows the services that are associated with all licenses that are assigned to her account.</span></span>
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

<span data-ttu-id="3db54-123">이 예제에서는 사용자 BelindaN@litwareinc.com이 계정에 할당된 첫 번째 라이선스(인덱스 번호: 0)에서 액세스할 수 있는 서비스를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="3db54-123">This example shows the services that user BelindaN@litwareinc.com has access to from the first license that's assigned to her account (the index number is 0).</span></span>
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

<span data-ttu-id="3db54-124">특정 서비스를 사용하거나 사용하지 않도록 허가된 모든 사용자를 찾으려면 다음 구문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3db54-124">To find all the licensed users who have been enabled or not enabled for specific services, use the following syntax:</span></span>
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[<LicenseIndexNumber> ].ServiceStatus[<ServiceIndexNumber> ].ProvisioningStatus <-eq | -ne> "Disabled" -and $_.Licenses[<LicenseIndexNumber> ].ServiceStatus[<ServiceIndexNumber> ].ProvisioningStatus <-eq | -ne> "Disabled"...}
```

<span data-ttu-id="3db54-125">이러한 예제는 다음 정보를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3db54-125">These examples use the following information:</span></span>
  
- <span data-ttu-id="3db54-126">관심 있는 우리가 하는 Office 365 서비스에 대 한 액세스를 제공 하는 라이선스는 (의 인덱스 번호는 0) 하는 모든 사용자에 게 할당 된 첫번째 라이선스입니다.</span><span class="sxs-lookup"><span data-stu-id="3db54-126">The license that gives access to the Office 365 services that we're interested in is the first license that's assigned to all users (the index number is 0).</span></span>
    
- <span data-ttu-id="3db54-p104">관심 있는 우리는 Office 365 서비스를 Skype 비즈니스 온라인 및 Exchange Online에 대 한 됩니다. 라이선스 계획 연관 된 라이선스에 대 한 온라인 비즈니스에 대 한 Skype는 나열 된 6 서비스 (인덱스 번호는 5), Exchange Online은 9 서비스 및 (인덱스 번호는 8) 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="3db54-p104">The Office 365 services that we're interested in are Skype for Business Online and Exchange Online. For the licenses that are associated with the licensing plan, Skype for Business Online is the 6th service listed (the index number is 5), and Exchange Online is the 9th service listed (the index number is 8).</span></span>
    
<span data-ttu-id="3db54-129">이 예제에서는 비즈니스 온라인 및 Exchange Online에 대 한 Skype에 대해 사용할 수 있는 모든 사용이 허가 된 사용자를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3db54-129">This example returns all licensed users who are enabled for Skype for Business Online and Exchange Online.</span></span>
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[5].ProvisioningStatus -ne "Disabled" -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -ne "Disabled"}
```

<span data-ttu-id="3db54-130">Skype 비즈니스 온라인 또는 Exchange Online에 대 한 사용 하도록 설정 되지 않은 모든 사용이 허가 된 사용자를 반환 하는이 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="3db54-130">This example returns all licensed users who aren't enabled for Skype for Business Online or Exchange Online.</span></span>
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[5].ProvisioningStatus -eq "Disabled" -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -eq "Disabled"}
```

<span data-ttu-id="3db54-131"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="3db54-131"></span></span>
## <a name="the-long-version-instructions-with-detailed-explanations"></a><span data-ttu-id="3db54-132">긴 버전 (명령에 대 한 세부 정보)</span><span class="sxs-lookup"><span data-stu-id="3db54-132">The long version (instructions with detailed explanations)</span></span>

### <a name="find-the-office-365-powershell-services-that-a-user-has-access-to"></a><span data-ttu-id="3db54-133">사용자에 액세스할 수 있는 Office 365 PowerShell 서비스 찾기</span><span class="sxs-lookup"><span data-stu-id="3db54-133">Find the Office 365 PowerShell services that a user has access to</span></span>

<span data-ttu-id="3db54-p105">가 분명 어떤 사용자가 Office 365 라이선스 발급 하 고 있는 사용자 하지 않은 알 수 있습니다. (자세한 내용은 [Office 365 powershell 사용이 허가 된 및 허가 되지 않은 사용자를 보려면](view-licensed-and-unlicensed-users-with-office-365-powershell.md) 문서 참조). 그러나 단순히 Office 365 라이선스를 가진 알 수 없는 아무것도 해당 사용자 수행할 수 있는 실제로 Office 365를 사용 하는 방법에 대 한 합니다. 수가 자신이 사용 하 여 Exchange Online 또는 Skype 온라인 비즈니스에 대 한? 이 사용자 SharePoint Online 액세스할 수 있습니까? 가 자신이 않은 Office Professional Plus에 액세스할 수 있습니까? 사용자가 이러한 서비스에 액세스할 가능성이 의미 단순히는 라이선스가 필요 합니다. 그러나 사용자에 게 사용할 수 있는 기능이 자신의 라이선스에서 사용할 수 있는 서비스에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="3db54-p105">It's obviously important for you to know which users have been issued Office 365 licenses and which users haven't. (See the article [View licensed and unlicensed users with Office 365 PowerShell](view-licensed-and-unlicensed-users-with-office-365-powershell.md) for more information). However, simply having an Office 365 license doesn't tell you anything about what that user can actually do with Office 365. Can he or she use Exchange Online or Skype for Business Online? Can this user access SharePoint Online? Does he or she have access to Office Professional Plus? Having a license simply means that the user has the potential to access these services. However, the capabilities available to a user depend on the services that have been enabled on his or her license.</span></span>
  
<span data-ttu-id="3db54-p106">어떻게 확인할 수 있는 Office 365 기능을 사용자가 액세스할 수 있습니까? 이 하나에 다음과 비슷한 명령을 실행 해야할 사항은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3db54-p106">So how can we determine which Office 365 features a user has access to? To do that we need to run a command similar to this one:</span></span>
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Select-Object -ExpandProperty Licenses | Select-Object -ExpandProperty ServiceStatus
```

<span data-ttu-id="3db54-144">이 명령은 BelindaN@litwareinc.com 계정에 대 한 정보를 반환 하려면 **Get-msoluser** cmdlet를 사용 합니다. 해당 정보를 반환한 후에, 되 면 다음 계정 데이터를 **Select-object** cmdlet에 파이프 하 고는 **Select-object** **라이선스** 속성의 값을 "확장" 하 게 합니다.</span><span class="sxs-lookup"><span data-stu-id="3db54-144">In this command, we're using the **Get-MsolUser** cmdlet to return information about the account BelindaN@litwareinc.com. Once we've returned that information, we then pipe the account data to the **Select-Object** cmdlet and ask **Select-Object** to "expand" the value of the **Licenses** property:</span></span>
  
 `Select-Object -ExpandProperty Licenses`
  
<span data-ttu-id="3db54-p107">왜 이렇게 할까요? 물론 **라이선스** 기본적으로 속성은 알려줍니다에서 Belinda 라이선스를 획득 한 라이선스 팩의 이름:</span><span class="sxs-lookup"><span data-stu-id="3db54-p107">Why do we do that? Well, by default the **Licenses** property only tells us the name of the licensing pack where Belinda's license came from:</span></span>
  
```
Licenses
--------
{litwareinc:ENTERPRISEPACK}
```

<span data-ttu-id="3db54-147">**라이선스** 속성을 "확장" 하면 더 많은 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="3db54-147">"Expanding" the **Licenses** property gives us a little more information:</span></span>
  
```
ExtensionData     AccountSku       AccountSkuId ServiceStatus
-------------     ----------       ------------ -------------
System.Runtime... Microsoft.On...  litwarein... {Microsoft.Online.A...
```

<span data-ttu-id="3db54-148">및 다음 **ServiceStatus** 속성을 확장 하 여을 얻을 수 더 많은 정보:</span><span class="sxs-lookup"><span data-stu-id="3db54-148">And then by expanding the **ServiceStatus** property we can get back even more information:</span></span>
  
|<span data-ttu-id="3db54-149">서비스 계획 \* \* \*</span><span class="sxs-lookup"><span data-stu-id="3db54-149">****Service plan****</span></span>|<span data-ttu-id="3db54-150">****Description****</span><span class="sxs-lookup"><span data-stu-id="3db54-150">****Description****</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="3db54-151">Sway</span><span class="sxs-lookup"><span data-stu-id="3db54-151">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="3db54-152">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="3db54-152">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="3db54-153">Yammer</span><span class="sxs-lookup"><span data-stu-id="3db54-153">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="3db54-154">RMS(Azure 권한 관리)</span><span class="sxs-lookup"><span data-stu-id="3db54-154">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="3db54-155">Office Professional Plus</span><span class="sxs-lookup"><span data-stu-id="3db54-155">Office Professional Plus</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="3db54-156">비즈니스용 Skype 온라인</span><span class="sxs-lookup"><span data-stu-id="3db54-156">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="3db54-157">Office Online</span><span class="sxs-lookup"><span data-stu-id="3db54-157">Office Online</span></span>  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="3db54-158">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="3db54-158">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="3db54-159">Exchange Online 계획 2</span><span class="sxs-lookup"><span data-stu-id="3db54-159">Exchange Online Plan 2</span></span>  <br/> |
   
> [!NOTE]
> <span data-ttu-id="3db54-p108">너무 많은 입력 하는 것이를 알고 계십니까? 물론을 이해할 수 애매 한 Windows PowerShell을 하는 경우 대신 실행할 수 있습니다는 명령의 압축 된 버전: >`(Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com).Licenses[0].ServiceStatus`</span><span class="sxs-lookup"><span data-stu-id="3db54-p108">You say that's too much typing? Well, if you can put up with a little Windows PowerShell obtuseness, you can run this condensed version of the command instead: >  `(Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com).Licenses[0].ServiceStatus`</span></span>
  
<span data-ttu-id="3db54-p109">궁금할 경우에 수 "확장" **라이선스** 속성은 **라이선스** 는 다중값된 속성 때문에:은 여러 값을 저장할 수 있는 단일 속성입니다. 단순히 드릴 다운 하 여 속성 값을 확장 하 고는 결과가에서 이러한 추가 되는 값을 기본적으로 표시 되지 않습니다 화면에 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="3db54-p109">In case you're wondering, we can "expand" the **Licenses** property because **Licenses** is a multivalued property: it's a single property that can store multiple values. When we expand a property value we simply drill down to get at these additional values that, by default, are not displayed onscreen.</span></span>
  
> [!NOTE]
> <span data-ttu-id="3db54-p110">값이 다중값된 속성 인지를 알고 있는 어떻게 가정해는? 물론 사실을 확인 하려면 다음과 같은 명령을 실행 하를 시도: > `Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Get-Member`> **get-member** cmdlet은 자체; 개체에 대 한 정보를 반환 합니다. 이 경우에 속성에 대 한 정보는 사용자 계정 개체를 구성 하는 값입니다. **라이선스** 속성에 대 한 말을 **Get-member** 다음과 같습니다: > `Licenses Property System.Collections.Generic.List[Microsoft.On...`> 속성 정의 컬렉션에 대 한 자료 된다고 표시 되 면 (이 경우 `System.Collections.Generic.List`) 다중값된 속성을 사용 해야하는 경우 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3db54-p110">So how are you supposed to know that a value is a multivalued property? Well, to find that out, try running a command similar to this: >  `Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Get-Member`> The **Get-member** cmdlet returns information about the object itself; in this case, information about the property values that make up a user account object. Here's what **Get-Member** has to say about the **Licenses** property:>  `Licenses Property System.Collections.Generic.List[Microsoft.On...`> If the property definition says something about collections (in this case,  `System.Collections.Generic.List`) then you know you're dealing with a multivalued property.</span></span> 
  
<span data-ttu-id="3db54-p111">따라서이 모든 의미 합니까? 답변을 먼저 살펴보겠습니다 다른 **Get-msoluser** cmdlet에 의해 반환 되는 정보:</span><span class="sxs-lookup"><span data-stu-id="3db54-p111">So what does all this mean? To answer that, let's first take another look at the information returned by the **Get-MsolUser** cmdlet:</span></span>
  
```
ServicePlan                       ProvisioningStatus
-----------                       ------------------
SWAY                              Success
INTUNE_O365                       Success
YAMMER_ENTERPRISE                 PendingInput
RMS_S_ENTERPRISE                  Success
OFFICESUBSCRIPTION                Success
MCOSTANDARD                       Success
SHAREPOINTWAC                     Success
SHAREPOINTENTERPRISE              Success
EXCHANGE_S_ENTERPRISE             Success
```

<span data-ttu-id="3db54-169">한 보겠습니다 또한 이러한 이상한 이름의 서비스 계획이 실제로 나타내는 설명 하는 테이블에 대 한 정보를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="3db54-169">And let's also take a look at a table that explains what these oddly-named service plans really represent:</span></span>
  
|<span data-ttu-id="3db54-170">서비스 계획 \* \* \*</span><span class="sxs-lookup"><span data-stu-id="3db54-170">****Service plan****</span></span>|<span data-ttu-id="3db54-171">****Description****</span><span class="sxs-lookup"><span data-stu-id="3db54-171">****Description****</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="3db54-172">Sway</span><span class="sxs-lookup"><span data-stu-id="3db54-172">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="3db54-173">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="3db54-173">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="3db54-174">Yammer</span><span class="sxs-lookup"><span data-stu-id="3db54-174">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="3db54-175">RMS(Azure 권한 관리)</span><span class="sxs-lookup"><span data-stu-id="3db54-175">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="3db54-176">Office Professional Plus</span><span class="sxs-lookup"><span data-stu-id="3db54-176">Office Professional Plus</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="3db54-177">비즈니스용 Skype 온라인</span><span class="sxs-lookup"><span data-stu-id="3db54-177">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="3db54-178">Office Online</span><span class="sxs-lookup"><span data-stu-id="3db54-178">Office Online</span></span>  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="3db54-179">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="3db54-179">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="3db54-180">Exchange Online 계획 2</span><span class="sxs-lookup"><span data-stu-id="3db54-180">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="3db54-p112">모든 확실히 이해 하셨나요?  `MCOSTANDARD` 은 Skype에 대 한 내부 프로그래밍 이름을 방금 온라인 비즈니스에 대 한 동안 `OFFICESUSBCRIPTION` Office Professional Plus에 대 한 내부 프로그래밍 이름 뿐입니다. 분야에서 가장 직관적인 것 없는 하지만이 표 간편 하 게 유지으로 필요가 많은 문제를 사용할 때 Office 365 서비스 사용 (영문).</span><span class="sxs-lookup"><span data-stu-id="3db54-p112">Got all that?  `MCOSTANDARD` is just an internal programming name for Skype for Business Online, while `OFFICESUSBCRIPTION` is just the internal programming name for Office Professional Plus. It's not the most intuitive thing in the world, but as long as you keep this table handy you won't have many problems when it comes to working with Office 365 services.</span></span>
  
<span data-ttu-id="3db54-p113">리더에 게: 아니 군요. **ProvisioningStatus** 로 설정 된 경우에 문서를 [보기 라이선스 및 Office 365 PowerShell을 사용 하 여 서비스를](view-licenses-and-services-with-office-365-powershell.md)갸우뚱 처럼 `Success` 는 서비스 완벽 하 게 활성화 되었는지, 즉 예 하는 경우 `MCOSTANDARD` 로 설정 된 `Success` 즉, 사용자가 온라인 비즈니스에 대 한 Skype를 액세스할 수 있습니다. **ProvisioningStatus** 로 설정 된 경우 `PendingInput` 즉, Office 365 서비스 요청을 처리 하 고 계속 그러나 사용자 수 일반적으로 로그온 하 고 요청 처리를 완료 하는 동안 서비스에 액세스 합니다. ( `YAMMER_ENTERPRISE` 항상 같이 표시 됩니다. `PendingInput`, 상관 없습니다: 하는 Yammer에 로그온 한 사용자 중지 되지 않음).</span><span class="sxs-lookup"><span data-stu-id="3db54-p113">But wait: there's more. As we learned in the article [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md), if the **ProvisioningStatus** is set to `Success` that means that the service has been fully enabled; for example if `MCOSTANDARD` is set to `Success` that means that the user can access Skype for Business Online. If the **ProvisioningStatus** is set to `PendingInput` that means that Office 365 is still processing the service request; however, the user can typically log on and access the service while the request finishes processing. ( `YAMMER_ENTERPRISE` will always be shown as `PendingInput`, but that's OK: that won't stop a user from logging on to Yammer).</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="3db54-188">사용자가 설치 및 활성화 하는 동안 사용 되는 새로운 Office Professional Plus 설치 수 `OFFICESUBSCRIPTION` 에 `PendingInput` 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="3db54-188">Users can install and activate a new Office Professional Plus installation while  `OFFICESUBSCRIPTION` is in the `PendingInput` state.</span></span>
  
<span data-ttu-id="3db54-189">이며, 관리할 수 있어야 하는 서비스로 설정 되어 `Disabled` 는 해당 서비스에는 사용자에 게 사용할 수 없다는 것을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="3db54-189">And, needless to say, is a service is set to  `Disabled` that means that the service in question is not available to the user.</span></span>
  

### <a name="find-users-that-have-access-to-specific-office-365-powershell-services"></a><span data-ttu-id="3db54-190">특정 Office 365 PowerShell 서비스에 액세스할 수 있는 사용자 찾기</span><span class="sxs-lookup"><span data-stu-id="3db54-190">Find users that have access to specific Office 365 PowerShell services</span></span>

<span data-ttu-id="3db54-p114">별도 문서에서는 Office 365 PowerShell을 사용 하 여 서비스에 대 한 사용자 액세스를 사용 하지 않도록 설정 하는 방법을 살펴보았습니다. (해당 문서, 누락 된 경우 참조 [Office 365 PowerShell을 사용 하 여 서비스에 대 한 액세스를 사용 하지 않도록 설정](disable-access-to-services-with-office-365-powershell.md)) 합니다. 그렇다면 대체 발생 하는: 인스턴스가 있는 *사용자* 를 결정 하는 방법이 있습니다 (즉, 둘 이상의 사용자)가 사용 하거나 사용 하지 않도록 설정 하는 서비스?</span><span class="sxs-lookup"><span data-stu-id="3db54-p114">In a separate article, we saw how you can use Office 365 PowerShell to disable user access to services. (If you missed that article, see [Disable access to services with Office 365 PowerShell](disable-access-to-services-with-office-365-powershell.md)). That leads to an obvious question: is there any way to determine which  *users*  (that is, more than one user) have which services enabled or disabled?</span></span>
  
<span data-ttu-id="3db54-p115">요청은 다른 사용자 굴뚝 된 것입니다. 그 대답 하기 위해 먼저 살펴보았습니다 문서 [보기 라이선스 및 Office 365 PowerShell을 사용 하 여 서비스에](view-licenses-and-services-with-office-365-powershell.md) 에서만 사용할 수 있는 현재 라이선스 계획에 대 한 서비스의 표를 검토 보겠습니다 `litwareinc:ENTERPRISEPACK`:</span><span class="sxs-lookup"><span data-stu-id="3db54-p115">We were hoping that someone would ask that. In order to answer that question, let's review the table of services that we first looked at in the article [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md) for our only available licensing plan `litwareinc:ENTERPRISEPACK`:</span></span>
  
|<span data-ttu-id="3db54-196">서비스 계획 \* \* \*</span><span class="sxs-lookup"><span data-stu-id="3db54-196">****Service plan****</span></span>|<span data-ttu-id="3db54-197">****Description****</span><span class="sxs-lookup"><span data-stu-id="3db54-197">****Description****</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="3db54-198">Sway</span><span class="sxs-lookup"><span data-stu-id="3db54-198">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="3db54-199">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="3db54-199">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="3db54-200">Yammer</span><span class="sxs-lookup"><span data-stu-id="3db54-200">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="3db54-201">RMS(Azure 권한 관리)</span><span class="sxs-lookup"><span data-stu-id="3db54-201">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="3db54-202">Office Professional Plus</span><span class="sxs-lookup"><span data-stu-id="3db54-202">Office Professional Plus</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="3db54-203">비즈니스용 Skype 온라인</span><span class="sxs-lookup"><span data-stu-id="3db54-203">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="3db54-204">Office Online</span><span class="sxs-lookup"><span data-stu-id="3db54-204">Office Online</span></span>  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="3db54-205">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="3db54-205">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="3db54-206">Exchange Online 계획 2</span><span class="sxs-lookup"><span data-stu-id="3db54-206">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="3db54-p116">서비스 계획은 제품;에 대 한 내부 프로그래밍 이름에 마찬가지 기억할 것 처럼 예, `OFFICESUBSCRIPTION`, 하나의 이름을,은 Office Professional Plus에 대 한 내부 프로그래밍 이름입니다. 하는 경우 `OFFICESUBSCRIPTION` 변수로 나타나는데 `SUCCESS` 사용자의 서비스 계획에 다음 즉, 사용자가 Office Professional Plus에 액세스할 수 있습니다. 하는 경우 `EXCHANGE_S_ENTERPRISE` 으로 나열 되어있는지 `DISABLED` 즉, 사용자를 Exchange Online 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3db54-p116">As you might recall, the service plan is nothing more than the internal programming name for a product; for example,  `OFFICESUBSCRIPTION`, to name one, is the internal programming name for Office Professional Plus. If  `OFFICESUBSCRIPTION` shows up as `SUCCESS` on a user's service plan, then that means that the user is allowed to access Office Professional Plus. If `EXCHANGE_S_ENTERPRISE` is listed as `DISABLED` that means the user can't use Exchange Online.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="3db54-210">사용자가 설치 및 활성화 하는 동안 사용 되는 새로운 Office Professional Plus 설치 수 `OFFICESUBSCRIPTION` 에 `PendingInput` 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="3db54-210">Users can install and activate a new Office Professional Plus installation while  `OFFICESUBSCRIPTION` is in the `PendingInput` state.</span></span>
  
<span data-ttu-id="3db54-p117">이제는 서비스에 표시 하는 순서는 매우 중요 시간입니다. Windows PowerShell 목록에서 각 항목에는 인덱스 번호를 할당합니다. 첫번째 항목은 0으로, 다음 항목은 1 등입니다. 결과 다음 표에서 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="3db54-p117">Now is the time where the order in which the services appear is extremely important. Windows PowerShell assigns an index number to each entry in the list. The first entry is 0, the next entry is 1, and so on. The results are explained in the following table:</span></span>
  
|<span data-ttu-id="3db54-215">인덱스 번호 \* \* \*</span><span class="sxs-lookup"><span data-stu-id="3db54-215">****Index number****</span></span>|<span data-ttu-id="3db54-216">서비스 계획 \* \* \*</span><span class="sxs-lookup"><span data-stu-id="3db54-216">****Service plan****</span></span>|
|:-----|:-----|
|<span data-ttu-id="3db54-217">0</span><span class="sxs-lookup"><span data-stu-id="3db54-217">0</span></span>  <br/> | `SWAY` <br/> |
|<span data-ttu-id="3db54-218">1</span><span class="sxs-lookup"><span data-stu-id="3db54-218">1</span></span>  <br/> | `INTUNE_O365` <br/> |
|<span data-ttu-id="3db54-219">2</span><span class="sxs-lookup"><span data-stu-id="3db54-219">2</span></span>  <br/> | `YAMMER_ENTERPRISE` <br/> |
|<span data-ttu-id="3db54-220">3</span><span class="sxs-lookup"><span data-stu-id="3db54-220">3</span></span>  <br/> | `RMS_S_ENTERPRISE` <br/> |
|<span data-ttu-id="3db54-221">4</span><span class="sxs-lookup"><span data-stu-id="3db54-221">4</span></span>  <br/> | `OFFICESUBSCRIPTION` <br/> |
|<span data-ttu-id="3db54-222">5</span><span class="sxs-lookup"><span data-stu-id="3db54-222">5</span></span>  <br/> | `MCOSTANDARD` <br/> |
|<span data-ttu-id="3db54-223">6</span><span class="sxs-lookup"><span data-stu-id="3db54-223">6</span></span>  <br/> | `SHAREPOINTWAC` <br/> |
|<span data-ttu-id="3db54-224">7</span><span class="sxs-lookup"><span data-stu-id="3db54-224">7</span></span>  <br/> | `SHAREPOINTENTERPRISE` <br/> |
|<span data-ttu-id="3db54-225">8</span><span class="sxs-lookup"><span data-stu-id="3db54-225">8</span></span>  <br/> | `EXCHANGE_S_ENTERPRISE` <br/> |
   
<span data-ttu-id="3db54-226">볼 수 있듯이 `SWAY` 는 첫번째 서비스 나열 된 인덱스 번호 0을 할당을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3db54-226">As you can see,  `SWAY` is the first service listed, so it gets assigned index number 0.</span></span>
  
> [!CAUTION]
> <span data-ttu-id="3db54-p118">이유 0과 1 하지? 이것은 프로그래밍 것입니다. 프로그래밍 언어에서 인덱스가 안내 얼마나 항목은 ""에서 오프셋 배열의 시작 합니다. 첫번째 항목은 *은* 해당 offset이 0 되므로 배열의 시작 부분입니다. 두번째 항목은 배열의 시작 부분에서 1 개 항목 이므로 해당 오프셋은 1.</span><span class="sxs-lookup"><span data-stu-id="3db54-p118">Why 0 and not 1? That's a programming thing. In programming languages indices tell you how far an item is "offset" from the beginning of the array. The first item  *is*  the beginning of the array, so its offset is 0. The second item is 1 item from the beginning of the array, so its offset is 1.</span></span>
  
<span data-ttu-id="3db54-p119">예를 보겠습니다. Exchange Online에 대해 활성화 되지 않은 모든 사용이 허가 된 사용자의 목록 같은 경우를 가정해 보겠습니다. 다음 명령을 사용할 수 있는, 사항은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3db54-p119">Let's try an example. Suppose we'd like a list of all the licensed users who have not been enabled for Exchange Online. To do that, we can use the following command:</span></span>
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -eq "Disabled"}
```

<span data-ttu-id="3db54-p120">그러나 이것은 필요에 따라 복잡을 찾고 거의 명령 보겠습니다 작동 하는 방법에 대해 설명 하는 분 걸릴입니다. 이것은 실제로 두 부분으로 구성 명령 및 앞부분은 매우 간단: 모든 Office 365 사용자의 컬렉션을 반환 하려면 **Get-msoluser** cmdlet을 사용 하면 했습니다 (사용이 허가 된 및 허가 되지 않은):</span><span class="sxs-lookup"><span data-stu-id="3db54-p120">Admittedly, that's a cryptic-looking little command, so let's take a minute to explain how it works. This is actually a two-part command, and the first part is very simple: we use the **Get-MsolUser** cmdlet to return a collection of all our Office 365 users (both licensed and unlicensed):</span></span>
  
```
Get-MsolUser
```

<span data-ttu-id="3db54-p121">해당 정보는 **Where-object** cmdlet에 파이프 됩니다. **Where-object** 모든 사용자 계정을 통해 이동 하 고 다음 조건이 모두 충족 하는 이러한 계정을:</span><span class="sxs-lookup"><span data-stu-id="3db54-p121">That information is then piped to the **Where-Object** cmdlet. **Where-Object** goes through all the user accounts and looks for those accounts that meet both of the following criteria:</span></span>
  
- <span data-ttu-id="3db54-p122">**IsLicensed** 속성이 같음 ( `-eq`) `True` ( `$true`). 이렇게 하면 허가 되지 않은 사용자가 걸러내기 하 게 합니다.</span><span class="sxs-lookup"><span data-stu-id="3db54-p122">The **isLicensed** property is equal to ( `-eq`)  `True` ( `$true`). That enables us to weed out the unlicensed users.</span></span>
    
- <span data-ttu-id="3db54-p123">**라이선스 [0]의 값입니다. ServiceStatus [8]입니다. ProvisioningStatus** 속성이 같음 ( `-eq`) `Disabled`합니다. 즉시이 목적을 위해이 다루기가 속성 이름의 중요 한 부분 입니까:</span><span class="sxs-lookup"><span data-stu-id="3db54-p123">The value of the **Licenses[0].ServiceStatus[8].ProvisioningStatus** property is equal to ( `-eq`)  `Disabled`. For our immediate purposes, the important part of this unwieldy property name is this:</span></span>
    
     `ServiceStatus[8]`
    
    <span data-ttu-id="3db54-p124">`[8]` Exchange Online에 대 한 인덱스 번호를 나타냅니다. (많음을 알고 에서만 몇분 이내 테이블을 보면). 비즈니스 Online 용 Skype에 대해 활성화 된 모든 사용자를 찾으려면 어떻게 해야 할까요? 물론 비즈니스 온라인 용 Skype에 대 한 인덱스 번호 이므로 5,이 구문을 사용 하면:</span><span class="sxs-lookup"><span data-stu-id="3db54-p124">The  `[8]` represents the index number for Exchange Online. (We know that from looking at the table a few minutes ago). What if we wanted to find all the users enabled for Skype for Business Online? Well, the index number for Skype for Business Online is 5, so we'd use this syntax:</span></span>
    
     `ServiceStatus[5]`
    
    <span data-ttu-id="3db54-247">이러한 식으로 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3db54-247">Etc., etc.</span></span>
    
    <span data-ttu-id="3db54-p125">참고로, `Licenses[0]` 살펴보는 원합니다 라이선스 계획을 나타냅니다. 이 테스트 도메인만 하나의 라이선스 계획을 갖기 때문이 훨씬 문제가 되지 않습니다. 하지만 사용자가 서로 다른 두 라이선스 계획에서 라이선스를 할당 된가 였습니다 경우를 가정해 보겠습니다. 이 경우 `Licenses[0]` 첫번째 라이선스 계획은 나타냅니다 및 `Licenses[1]` 두번째 라이선스 계획을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="3db54-p125">Incidentally,  `Licenses[0]` indicates the licensing plan that we want to look at. Since our test domain only has one licensing plan this doesn't matter much. But suppose we had a user who has been assigned licenses from two different licensing plans. In that case, `Licenses[0]` would represent the first licensing plan, and `Licenses[1]` would represent the second licensing plan.</span></span>
    
    <span data-ttu-id="3db54-252">다음 명령을 실행하여 사용자에게 할당된 라이선스 및 나열 순서를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3db54-252">To find the licenses that are assigned to a user, and the order in which they are listed, run the following command:</span></span>
    
  ```
  Get-MsolUser -UserPrincipalName <Account>  | Format-List DisplayName,Licenses
  ```

<span data-ttu-id="3db54-p126">이 모든 것이 작동 하는 방법이 된 것을 볼 수 있습니다. Office Professional Plus의 인덱스 번호는 4; 따라서이 명령은 Office Professional Plus에 대해 활성화 되지 않은 모든 사용자의 목록을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3db54-p126">Do you see how this all works? The index number for Office Professional Plus is 4; therefore, this command returns a list of all the users who have not been enabled for Office Professional Plus:</span></span>
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses.ServiceStatus[4].ProvisioningStatus -eq "Disabled"}
```

<span data-ttu-id="3db54-p127">및 Office Professional Plus에 대해 *활성화* 를 받은 사용자가 목록이 경우에 어떻게 할까요? 음, 프로그램 **ServiceStatus** 갖게 됩니다 다음 활성화 된 했을 때 경우 `PendingInput` 또는 `Success`; 즉, **servicestatus에 포함 된** 사용자 *같지* ( `-ne`) `Disabled`합니다. 즉, 이전 명령에서는 걸리고 아웃 스왑가 하기만 하면 모든는 `-eq` 에 대 한 연산자는 `-ne` 연산자:</span><span class="sxs-lookup"><span data-stu-id="3db54-p127">And what if we wanted a list of users who have been  *enabled*  for Office Professional Plus? Well, if you've been enabled then your **ServiceStatus** will either be `PendingInput` or `Success`; in other words, your **ServiceStatus** will *not*  equal ( `-ne`)  `Disabled`. That means all we have to do is take our previous command and swap out the  `-eq` operator for the `-ne` operator:</span></span>
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses.ServiceStatus[4].ProvisioningStatus -ne "Disabled"}
```

<span data-ttu-id="3db54-p128">되었다는로 전환 되 면는 코드 싶은 않습니다 win 많은 장점은 컨 합니다. 및 사실 필요 하다는 메시지가, 코드를 더 많은 얻을 수 혼란 합니다. 예, 비즈니스 온라인 및 Exchange Online에 대 한 두 Skype에 대해 활성화 된 사용자를 확인 하려고 있다고 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3db54-p128">As the saying goes, that code probably won't win many beauty contests. And, truth be told, the code can get even more tangled. For example, suppose we want to look for users who have been enabled for both Skype for Business Online and Exchange Online:</span></span>
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses.ServiceStatus[5].ProvisioningStatus -ne "Disabled" -and $_.Licenses.ServiceStatus[8].ProvisioningStatus -ne "Disabled"}
```

<span data-ttu-id="3db54-p129">하지 않는다면 하지만 어떻게 gnarly 있는 형태에 대해 알아봅니다 하는 방법에 대 한 너무 많은: 중요 한 점은, 비교적 적은 노력이이 정보 검색할 수 있습니다. Office 365 관리 센터를 사용 하 여이 같은 정보를 가져올 수 없습니다. Yes 하지만,에서 이론적에서 실질적, no입니다. Office 365 관리 센터를 사용 하 여이 동일한 정보에서를 각 사용자에 대 한 라이선스 정보에서 한번에 한 명의 사용자를 확인 하 고 다음 수동으로 추적할 *X* 에 대해 활성화 되어 있던 사용자 및 사용자가 않았다면 필요가 것입니다. 작동을 제외 하면 솔직히: 10 또는 11 개 이상의 사용자가이 작업을 수행 하려는 하지 않습니다. 이것이 너무 방대 하 고 시간이 많이 걸리는입니다.</span><span class="sxs-lookup"><span data-stu-id="3db54-p129">But don't worry too much about how gnarly that might look: the important thing is that, with relatively little effort, you can retrieve this information. Can't you get at this same information using the Office 365 admin center? In theory, yes but, in practical terms, no. To get at this same information using the Office 365 admin center you'd need to look at the licensing information for each user, one user at a time, and then manually keep track of who'd been enabled for  *X*  and who hadn't. That would work, but let's be honest: if you have more than 10 or 11 users, you're not going to do this. It's way too tedious and time-consuming.</span></span>
  
<span data-ttu-id="3db54-267">물론는 Windows PowerShell가 제공 하는 이유: 하는 등의 방대 하 고 시간이 많이 걸리는 작업에서 Windows PowerShell 하면 저장 하는데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3db54-267">Which, of course, is why we have Windows PowerShell: Windows PowerShell helps save you from tedious and time-consuming tasks such as that.</span></span>
  
<span data-ttu-id="3db54-268">Office 365 E5 구독에 대 한 해당 라이선스 및 servicestatus에 포함 된 색인으로 식별 되는 지정 된 서비스 집합에 대 한 서비스 정보를 보기 위한 명령의 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3db54-268">Here's an example of a command for viewing service information for a specified set of services as identified by their Licenses and ServiceStatus indexes for an Office 365 E5 subscription:</span></span>
  
```
Get-MsolUser | Select-Object DisplayName, @{Name="Sway";Expression={$_.Licenses[0].ServiceStatus[12].ProvisioningStatus}}, @{Name="Teams";Expression={$_.Licenses[0].ServiceStatus[7].ProvisioningStatus}}, @{Name="Yammer";Expression={$_.Licenses[0].ServiceStatus[20].ProvisioningStatus}}, @{Name="AD RMS";Expression={$_.Licenses[0].ServiceStatus[19].ProvisioningStatus}}, @{Name="OfficePro";Expression={$_.Licenses[0].ServiceStatus[21].ProvisioningStatus}}, @{Name="Skype";Expression={$_.Licenses[0].ServiceStatus[22].ProvisioningStatus}}, @{Name="SharePoint";Expression={$_.Licenses[0].ServiceStatus[24].ProvisioningStatus}}, @{Name="Exchange";Expression={$_.Licenses[0].ServiceStatus[23].ProvisioningStatus}} | ConvertTo-CSV > "C:\Service Info.csv"
```

<span data-ttu-id="3db54-269">이 명령은 모든 사용자 및 서비스 (팀, Yammer, AD RMS, OfficePro, Skype, SharePoint, 및 Exchange)의 지정된 된 집합에 대 한 해당 서비스 상태를 보여주는 CSV 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3db54-269">This command creates a CSV file showing all of your users and their service statuses for a specified set of services (Teams, Yammer, AD RMS, OfficePro, Skype, SharePoint, and Exchange).</span></span>

>[!Note]
><span data-ttu-id="3db54-p130">서비스 목록에서 구독에서 얻을 수 있습니다는 `(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus` 명령 합니다. 출력을 0이 들어 있는 서비스 인덱스 번호 매기기 시작 합니다. 위 명령은 단지 예를 합니다. 시간에 따른 서비스에 대 한 인덱스 번호를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3db54-p130">You can get the list of services in a subscription from the `(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus` command. In the output, you start numbering the service indexes with 0. The preceding command is just an example. Index numbers for services can change over time.</span></span>
>

  
<span data-ttu-id="3db54-274"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="3db54-274"></span></span>
## <a name="see-also"></a><span data-ttu-id="3db54-275">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3db54-275">See also</span></span>

<span data-ttu-id="3db54-276">Office 365 PowerShell을 사용 하여 사용자를 관리에 대하여 다음과 같은 추가 항목을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="3db54-276">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="3db54-277">Office 365 PowerShell을 사용 하 여 사용자 계정 만들기</span><span class="sxs-lookup"><span data-stu-id="3db54-277">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="3db54-278">삭제 한 사용자 계정 Office 365 PowerShell을 사용 하 여 복원 합니다.</span><span class="sxs-lookup"><span data-stu-id="3db54-278">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="3db54-279">블록 사용자 계정 Office 365 PowerShell을 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="3db54-279">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="3db54-280">Office 365 PowerShell을 사용 하 여 사용자 계정에 라이선스를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="3db54-280">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="3db54-281">Office 365 PowerShell을 사용 하 여 사용자 계정에서 라이센스를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="3db54-281">Remove licenses from user accounts with Office 365 PowerShell</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="3db54-282">이 항목에서 사용된 cmdlet에 대한 자세한 내용은 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="3db54-282">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="3db54-283">ConvertTo Html</span><span class="sxs-lookup"><span data-stu-id="3db54-283">ConvertTo-Html</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113290)
    
- [<span data-ttu-id="3db54-284">형식 목록</span><span class="sxs-lookup"><span data-stu-id="3db54-284">Format-List</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113302)
    
- [<span data-ttu-id="3db54-285">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="3db54-285">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="3db54-286">선택 개체</span><span class="sxs-lookup"><span data-stu-id="3db54-286">Select-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [<span data-ttu-id="3db54-287">Where-Object</span><span class="sxs-lookup"><span data-stu-id="3db54-287">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

  
## <a name="new-to-office-365"></a><span data-ttu-id="3db54-288">Office 365의 새로운 기능</span><span class="sxs-lookup"><span data-stu-id="3db54-288">New to Office 365?</span></span>


[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]