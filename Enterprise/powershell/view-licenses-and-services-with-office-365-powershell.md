---
title: PowerShell을 사용 하 여 Microsoft 365 라이선스 및 서비스 보기
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Ent_Office_Other
- O365ITProTrain
- LIL_Placement
- PowerShell
ms.assetid: bb5260a9-a6a3-4f34-b19a-06c6699f6723
description: PowerShell을 사용 하 여 Microsoft 365 조직에서 사용할 수 있는 라이선스 계획, 서비스 및 라이선스에 대 한 정보를 보는 방법에 대해 설명 합니다.
ms.openlocfilehash: f0b7d6cd5981bec09e7773d10d82ff81c0f34d4e
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230214"
---
# <a name="view-microsoft-365-licenses-and-services-with-powershell"></a><span data-ttu-id="a8f17-103">PowerShell을 사용 하 여 Microsoft 365 라이선스 및 서비스 보기</span><span class="sxs-lookup"><span data-stu-id="a8f17-103">View Microsoft 365 licenses and services with PowerShell</span></span>

<span data-ttu-id="a8f17-104">*이 문서는 Microsoft 365 Enterprise 및 Office 365 Enterprise에 모두 적용 됩니다.*</span><span class="sxs-lookup"><span data-stu-id="a8f17-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="a8f17-105">모든 Microsoft 365 구독은 다음과 같은 요소로 구성 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8f17-105">Every Microsoft 365 subscription consists of the following elements:</span></span>

- <span data-ttu-id="a8f17-106">**라이선스 계획** 이러한 계획은 라이선스 요금제 또는 Microsoft 365 요금제 라고도 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8f17-106">**Licensing plans** These are also known as license plans or Microsoft 365 plans.</span></span> <span data-ttu-id="a8f17-107">라이선스 계획은 사용자에 게 제공 되는 Microsoft 365 서비스를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8f17-107">Licensing plans define the Microsoft 365 services that are available to users.</span></span> <span data-ttu-id="a8f17-108">Microsoft 365 구독에는 여러 라이선싱 계획이 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8f17-108">Your Microsoft 365 subscription may contain multiple licensing plans.</span></span> <span data-ttu-id="a8f17-109">라이선스 계획의 예로는 Microsoft 365 E3을 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8f17-109">An example licensing plan would be Microsoft 365 E3.</span></span>
    
- <span data-ttu-id="a8f17-110">**서비스** 이러한 계획은 서비스 계획이 라고도 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8f17-110">**Services** These are also known as service plans.</span></span> <span data-ttu-id="a8f17-111">서비스는 각 라이선스 계획에서 사용할 수 있는 Microsoft 365 제품, 기능, 기능 (예: Exchange Online 및 Microsoft 365 Apps for enterprise for Office 365 ProPlus)입니다.</span><span class="sxs-lookup"><span data-stu-id="a8f17-111">Services are the Microsoft 365 products, features, and capabilities that are available in each licensing plan, for example, Exchange Online and Microsoft 365 Apps for enterprise (previously named Office 365 ProPlus).</span></span> <span data-ttu-id="a8f17-112">사용자는 다양 한 서비스에 대 한 액세스 권한을 부여 하는 다른 라이센스 계획에서 할당 된 여러 개의 라이센스를 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8f17-112">Users can have multiple licenses assigned to them from different licensing plans that grant access to different services.</span></span>
    
- <span data-ttu-id="a8f17-113">**라이선스** 각 라이선스 계획에는 구매한 라이선스 수가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8f17-113">**Licenses** Each licensing plan contains the number of licenses that you purchased.</span></span> <span data-ttu-id="a8f17-114">라이선스 계획에 정의 된 Microsoft 365 서비스를 사용할 수 있도록 사용자에 게 라이선스를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8f17-114">You assign licenses to users so they can use the Microsoft 365 services that are defined by the licensing plan.</span></span> <span data-ttu-id="a8f17-115">모든 사용자 계정에는 라이선스 요금제가 하나 이상 있어야 Microsoft 365에 로그온 하 고 서비스를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8f17-115">Every user account requires at least one license from one licensing plan so they can log on to Microsoft 365 and use the services.</span></span>
    
<span data-ttu-id="a8f17-116">Microsoft 365 용 PowerShell을 사용 하 여 Microsoft 365 조직의 사용 가능한 라이선스 계획, 라이선스 및 서비스에 대 한 세부 정보를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8f17-116">You can use PowerShell for Microsoft 365 to view details about the available licensing plans, licenses, and services in your Microsoft 365 organization.</span></span> <span data-ttu-id="a8f17-117">서로 다른 Office 365 구독에서 사용할 수 있는 제품, 기능 및 서비스에 대 한 자세한 내용은 [office 365 계획 옵션](https://go.microsoft.com/fwlink/p/?LinkId=691147)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a8f17-117">For more information about the products, features, and services that are available in different Office 365 subscriptions, see [Office 365 Plan Options](https://go.microsoft.com/fwlink/p/?LinkId=691147).</span></span>


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="a8f17-118">Graph 모듈용 Azure Active Directory PowerShell 사용하기</span><span class="sxs-lookup"><span data-stu-id="a8f17-118">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="a8f17-119">먼저 [Microsoft 365 테 넌 트에 연결](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)합니다.</span><span class="sxs-lookup"><span data-stu-id="a8f17-119">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
<span data-ttu-id="a8f17-120">현재 라이선스 계획 및 각 계획에 사용 가능한 라이선스에 대 한 요약 정보를 보려면 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8f17-120">To view summary information about your current licensing plans and the available licenses for each plan, run this command:</span></span>
  
```powershell
Get-AzureADSubscribedSku | Select -Property Sku*,ConsumedUnits -ExpandProperty PrepaidUnits
```

<span data-ttu-id="a8f17-121">결과에 다음이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8f17-121">The results contain:</span></span>
  
- <span data-ttu-id="a8f17-122">**SkuPartNumber:** 조직에 사용할 수 있는 라이선스 계획을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8f17-122">**SkuPartNumber:** Shows the available licensing plans for your organization.</span></span> <span data-ttu-id="a8f17-123">예를 들어 `ENTERPRISEPACK` Office 365 Enterprise e 3의 라이선스 계획 이름을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8f17-123">For example, `ENTERPRISEPACK` is the license plan name for Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="a8f17-124">**Enabled:** 특정 라이선스 계획을 위해 구매한 라이선스 수입니다.</span><span class="sxs-lookup"><span data-stu-id="a8f17-124">**Enabled:** Number of licenses that you've purchased for a specific licensing plan.</span></span>
    
- <span data-ttu-id="a8f17-125">**ConsumedUnits:** 특정 라이선스 계획에서 사용자에 게 할당 한 라이선스 수입니다.</span><span class="sxs-lookup"><span data-stu-id="a8f17-125">**ConsumedUnits:** Number of licenses that you've assigned to users from a specific licensing plan.</span></span>
    
<span data-ttu-id="a8f17-126">모든 라이선스 계획에서 사용할 수 있는 Microsoft 365 서비스에 대 한 세부 정보를 보려면 먼저 라이선스 계획 목록을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8f17-126">To view details about the Microsoft 365 services that are available in all of your license plans, first display a list of your license plans.</span></span>

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="a8f17-127">다음으로, 라이선스 계획 정보를 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8f17-127">Next, store the license plans information in a variable.</span></span>

```powershell
$licenses = Get-AzureADSubscribedSku
```

<span data-ttu-id="a8f17-128">다음으로, 특정 라이선스 계획에서 서비스를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8f17-128">Next, display the services in a specific license plan.</span></span>

```powershell
$licenses[<index>].ServicePlans
```

<span data-ttu-id="a8f17-129">\<index>는 명령 표시에서 `Get-AzureADSubscribedSku | Select SkuPartNumber` 1을 뺀 값으로 라이선스 계획의 행 번호를 지정 하는 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="a8f17-129">\<index> is an integer that specifies the row number of the license plan from the display of the `Get-AzureADSubscribedSku | Select SkuPartNumber` command, minus 1.</span></span>

<span data-ttu-id="a8f17-130">예를 들어 다음과 같이 명령을 표시 하는 경우를 예로 들 `Get-AzureADSubscribedSku | Select SkuPartNumber` 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8f17-130">For example, if the display of the `Get-AzureADSubscribedSku | Select SkuPartNumber` command is this:</span></span>

```powershell
SkuPartNumber
-------------
WIN10_VDA_E5
EMSPREMIUM
ENTERPRISEPREMIUM
FLOW_FREE
```

<span data-ttu-id="a8f17-131">그런 다음 ENTERPRISEPREMIUM 라이선스 계획에 대 한 서비스를 표시 하는 명령은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a8f17-131">Then the command to display the services for the ENTERPRISEPREMIUM license plan is this:</span></span>

```powershell
$licenses[2].ServicePlans
```

<span data-ttu-id="a8f17-132">ENTERPRISEPREMIUM은 세 번째 행입니다.</span><span class="sxs-lookup"><span data-stu-id="a8f17-132">ENTERPRISEPREMIUM is the third row.</span></span> <span data-ttu-id="a8f17-133">따라서 인덱스 값은 (3-1) 또는 2입니다.</span><span class="sxs-lookup"><span data-stu-id="a8f17-133">Therefore, the index value is (3 - 1), or 2.</span></span>

<span data-ttu-id="a8f17-134">라이선스 계획의 전체 목록 (제품 이름), 포함 된 서비스 계획 및 해당 하는 이름에 대 한 자세한 내용은 [product name and service plan identifier for license](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="a8f17-134">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="a8f17-135">Windows PowerShell용 Microsoft Azure Active Directory 모듈 사용하기</span><span class="sxs-lookup"><span data-stu-id="a8f17-135">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="a8f17-136">먼저 [Microsoft 365 테 넌 트에 연결](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)합니다.</span><span class="sxs-lookup"><span data-stu-id="a8f17-136">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

>[!Note]
><span data-ttu-id="a8f17-137">이 항목에서 설명하는 절차를 자동화하는 PowerShell 스크립트를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8f17-137">A PowerShell script is available that automates the procedures described in this topic.</span></span> <span data-ttu-id="a8f17-138">특히이 스크립트를 사용 하면 Sway를 포함 하 여 Microsoft 365 조직에서 서비스를 확인 하 고 사용 하지 않도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8f17-138">Specifically, the script lets you view and disable services in your Microsoft 365 organization, including Sway.</span></span> <span data-ttu-id="a8f17-139">자세한 내용은 [PowerShell을 사용 하 여 Sway에 액세스 사용 안 함을](disable-access-to-sway-with-office-365-powershell.md)참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a8f17-139">For more information, see [Disable access to Sway with PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
>
    
<span data-ttu-id="a8f17-140">현재 라이선스 계획 및 각 계획에 사용 가능한 라이선스에 대 한 요약 정보를 보려면 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8f17-140">To view summary information about your current licensing plans and the available licenses for each plan, run the following command:</span></span>
  
```powershell
Get-MsolAccountSku
```

>[!Note]
><span data-ttu-id="a8f17-141">PowerShell Core는 Windows PowerShell용 Microsoft Azure Active Directory 모듈 및 이름에 **Msol**이 있는 cmdlet을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a8f17-141">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="a8f17-142">이러한 cmdlet을 계속 사용하려면 Windows PowerShell에서 이를 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8f17-142">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="a8f17-143">결과에는 다음 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8f17-143">The results contain the following information:</span></span>
  
- <span data-ttu-id="a8f17-144">**AccountSkuId:** 구문을 사용 하 여 조직에 사용할 수 있는 라이선스 계획을 표시 합니다 `<CompanyName>:<LicensingPlan>` .</span><span class="sxs-lookup"><span data-stu-id="a8f17-144">**AccountSkuId:** Show the available licensing plans for your organization by using the syntax `<CompanyName>:<LicensingPlan>`.</span></span>  <span data-ttu-id="a8f17-145">_\<CompanyName>_ 은 Microsoft 365에 등록할 때 입력 한 값 이며 조직에서 고유 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8f17-145">_\<CompanyName>_ is the value that you provided when you enrolled in Microsoft 365, and is unique for your organization.</span></span> <span data-ttu-id="a8f17-146">_\<LicensingPlan>_ 값은 모든 사용자에 대해 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8f17-146">The _\<LicensingPlan>_ value is the same for everyone.</span></span> <span data-ttu-id="a8f17-147">예를 들어이 값에서 `litwareinc:ENTERPRISEPACK` 회사 이름은 `litwareinc` 및 라이선스 계획 이름 `ENTERPRISEPACK` (Office 365 Enterprise e 3의 시스템 이름)입니다.</span><span class="sxs-lookup"><span data-stu-id="a8f17-147">For example, in the value `litwareinc:ENTERPRISEPACK`, the company name is  `litwareinc`, and the licensing plan name  `ENTERPRISEPACK`, which is the system name for Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="a8f17-148">**Activeunits:** 특정 라이선스 계획을 위해 구매한 라이선스 수입니다.</span><span class="sxs-lookup"><span data-stu-id="a8f17-148">**ActiveUnits:** Number of licenses that you've purchased for a specific licensing plan.</span></span>
    
- <span data-ttu-id="a8f17-149">**WarningUnits:** 갱신 하지 않고 30 일 유예 기간 이후에 만료 되는 라이선스 요금제의 라이선스 수입니다.</span><span class="sxs-lookup"><span data-stu-id="a8f17-149">**WarningUnits:** Number of licenses in a licensing plan that you haven't renewed, and that will expire after the 30-day grace period.</span></span>
    
- <span data-ttu-id="a8f17-150">**ConsumedUnits:** 특정 라이선스 계획에서 사용자에 게 할당 한 라이선스 수입니다.</span><span class="sxs-lookup"><span data-stu-id="a8f17-150">**ConsumedUnits:** Number of licenses that you've assigned to users from a specific licensing plan.</span></span>
    
<span data-ttu-id="a8f17-151">모든 라이선스 계획에서 사용할 수 있는 Microsoft 365 서비스에 대 한 세부 정보를 보려면 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8f17-151">To view details about the Microsoft 365 services that are available in all of your license plans, run the following command:</span></span>
  
```powershell
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

<span data-ttu-id="a8f17-152">다음 표에서는 Microsoft 365 서비스 계획 및 가장 일반적인 서비스에 대 한 친숙 한 이름을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a8f17-152">The following table shows the Microsoft 365 service plans and their friendly names for the most common services.</span></span> <span data-ttu-id="a8f17-153">서비스 계획 목록이 다를 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8f17-153">Your list of service plans might be different.</span></span> 
  
|<span data-ttu-id="a8f17-154">**서비스 계획**</span><span class="sxs-lookup"><span data-stu-id="a8f17-154">**Service plan**</span></span>|<span data-ttu-id="a8f17-155">**설명**</span><span class="sxs-lookup"><span data-stu-id="a8f17-155">**Description**</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="a8f17-156">Sway</span><span class="sxs-lookup"><span data-stu-id="a8f17-156">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="a8f17-157">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="a8f17-157">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="a8f17-158">Yammer</span><span class="sxs-lookup"><span data-stu-id="a8f17-158">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="a8f17-159">RMS(Azure 권한 관리)</span><span class="sxs-lookup"><span data-stu-id="a8f17-159">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="a8f17-160">Microsoft 365 Apps for enterprise *(이전 이름 Office 365 ProPlus)*</span><span class="sxs-lookup"><span data-stu-id="a8f17-160">Microsoft 365 Apps for enterprise *(previously named Office 365 ProPlus)*</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="a8f17-161">비즈니스용 Skype Online</span><span class="sxs-lookup"><span data-stu-id="a8f17-161">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="a8f17-162">사무실</span><span class="sxs-lookup"><span data-stu-id="a8f17-162">Office</span></span>  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="a8f17-163">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="a8f17-163">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="a8f17-164">Exchange Online 계획 2</span><span class="sxs-lookup"><span data-stu-id="a8f17-164">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="a8f17-165">라이선스 계획의 전체 목록 (제품 이름), 포함 된 서비스 계획 및 해당 하는 이름에 대 한 자세한 내용은 [product name and service plan identifier for license](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="a8f17-165">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>

<span data-ttu-id="a8f17-166">특정 라이선스 계획에서 사용할 수 있는 Microsoft 365 서비스에 대 한 세부 정보를 보려면 다음 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8f17-166">To view details about the Microsoft 365 services that are available in a specific licensing plan, use the following syntax.</span></span>
  
```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```

<span data-ttu-id="a8f17-167">이 예에서는 litwareinc: ENTERPRISEPACK (Office 365 Enterprise E3) 라이선스 요금제에서 사용할 수 있는 서비스를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8f17-167">This example shows the services that are available in the litwareinc:ENTERPRISEPACK (Office 365 Enterprise E3) licensing plan.</span></span>
  
```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "litwareinc:ENTERPRISEPACK"}).ServiceStatus
```

## <a name="see-also"></a><span data-ttu-id="a8f17-168">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a8f17-168">See also</span></span>

[<span data-ttu-id="a8f17-169">PowerShell을 사용 하 여 Microsoft 365 사용자 계정, 라이선스 및 그룹 관리</span><span class="sxs-lookup"><span data-stu-id="a8f17-169">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="a8f17-170">PowerShell을 사용 하 여 Microsoft 365 관리</span><span class="sxs-lookup"><span data-stu-id="a8f17-170">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="a8f17-171">Microsoft 365 용 PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="a8f17-171">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)
