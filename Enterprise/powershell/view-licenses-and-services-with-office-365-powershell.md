---
title: 라이선스 및 Office 365 PowerShell을 사용 하 여 서비스를 표시 합니다.
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- O365ITProTrain
- LIL_Placement
- PowerShell
ms.assetid: bb5260a9-a6a3-4f34-b19a-06c6699f6723
description: Office 365 PowerShell을 사용 하 여 Office 365 조직에서 사용할 수 있는 라이선스 계획, 서비스 및 라이선스에 대 한 정보를 확인 하는 방법에 대해 설명 합니다.
ms.openlocfilehash: 8ee2c834063ea80388662c1f36f4524715f98a58
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2019
ms.locfileid: "38747457"
---
# <a name="view-licenses-and-services-with-office-365-powershell"></a><span data-ttu-id="e0233-103">라이선스 및 Office 365 PowerShell을 사용 하 여 서비스를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0233-103">View licenses and services with Office 365 PowerShell</span></span>

<span data-ttu-id="e0233-104">모든 Office 365 구독은 다음과 같은 요소로 구성 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0233-104">Every Office 365 subscription consists of the following elements:</span></span>

- <span data-ttu-id="e0233-105">**라이선스 계획** 이러한 계획은 라이선스 요금제 또는 Office 365 요금제 라고도 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0233-105">**Licensing plans** These are also known as license plans or Office 365 plans.</span></span> <span data-ttu-id="e0233-106">라이선스 계획은 사용자에 게 제공 되는 Office 365 서비스를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0233-106">Licensing plans define the Office 365 services that are available to users.</span></span> <span data-ttu-id="e0233-107">Office 365 구독에는 여러 라이선싱 계획이 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0233-107">Your Office 365 subscription may contain multiple licensing plans.</span></span> <span data-ttu-id="e0233-108">라이선스 계획의 예로는 Office 365 Enterprise E3을 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0233-108">An example licensing plan would be Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="e0233-109">**서비스** 이러한 계획은 서비스 계획이 라고도 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0233-109">**Services** These are also known as service plans.</span></span> <span data-ttu-id="e0233-110">서비스는 각 라이선스 계획에서 사용할 수 있는 Office 365 제품, 기능 및 기능 (예: Exchange Online 및 Office Professional Plus)입니다.</span><span class="sxs-lookup"><span data-stu-id="e0233-110">Services are the Office 365 products, features, and capabilities that are available in each licensing plan, for example, Exchange Online and Office Professional Plus.</span></span> <span data-ttu-id="e0233-111">사용자는 다양 한 서비스에 대 한 액세스 권한을 부여 하는 다른 라이센스 계획에서 할당 된 여러 개의 라이센스를 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0233-111">Users can have multiple licenses assigned to them from different licensing plans that grant access to different services.</span></span>
    
- <span data-ttu-id="e0233-112">**라이선스** 각 라이선스 계획에는 구매한 라이선스 수가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0233-112">**Licenses** Each licensing plan contains the number of licenses that you purchased.</span></span> <span data-ttu-id="e0233-113">라이선스 계획에 정의 된 Office 365 서비스를 사용할 수 있도록 사용자에 게 라이선스를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0233-113">You assign licenses to users so they can use the Office 365 services that are defined by the licensing plan.</span></span> <span data-ttu-id="e0233-114">모든 사용자 계정에는 라이선스 요금제가 하나 이상 있어야 Office 365에 로그온 하 고 서비스를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0233-114">Every user account requires at least one license from one licensing plan so they can log on to Office 365 and use the services.</span></span>
    
<span data-ttu-id="e0233-115">Office 365 PowerShell을 사용 하 여 Office 365 조직의 사용 가능한 라이선스 계획, 라이선스 및 서비스에 대 한 세부 정보를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0233-115">You can use Office 365 PowerShell to view details about the available licensing plans, licenses, and services in your Office 365 organization.</span></span> <span data-ttu-id="e0233-116">서로 다른 Office 365 구독에서 사용할 수 있는 제품, 기능 및 서비스에 대 한 자세한 내용은 [office 365 계획 옵션](https://go.microsoft.com/fwlink/p/?LinkId=691147)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e0233-116">For more information about the products, features, and services that are available in different Office 365 subscriptions, see [Office 365 Plan Options](https://go.microsoft.com/fwlink/p/?LinkId=691147).</span></span>


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="e0233-117">Graph 모듈용 Azure Active Directory PowerShell 사용하기</span><span class="sxs-lookup"><span data-stu-id="e0233-117">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="e0233-118">먼저, [Office 365 테넌트에 연결](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)합니다.</span><span class="sxs-lookup"><span data-stu-id="e0233-118">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
<span data-ttu-id="e0233-119">현재 라이선스 계획 및 각 계획에 사용 가능한 라이선스에 대 한 요약 정보를 보려면 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0233-119">To view summary information about your current licensing plans and the available licenses for each plan, run the following command:</span></span>
  
```powershell
Get-AzureADSubscribedSku | Select -Property Sku*,ConsumedUnits -ExpandProperty PrepaidUnits
```

<span data-ttu-id="e0233-120">결과에는 다음 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0233-120">The results contain the following information:</span></span>
  
- <span data-ttu-id="e0233-121">**SkuPartNumber:** 조직에 사용할 수 있는 라이선스 계획을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0233-121">**SkuPartNumber:** Shows the available licensing plans for your organization.</span></span> <span data-ttu-id="e0233-122">예를 `ENTERPRISEPACK` 들어 Office 365 Enterprise e 3의 라이선스 계획 이름을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0233-122">For example, `ENTERPRISEPACK` is the license plan name for Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="e0233-123">**Enabled:** 특정 라이선스 계획을 위해 구매한 라이선스 수입니다.</span><span class="sxs-lookup"><span data-stu-id="e0233-123">**Enabled:** Number of licenses that you've purchased for a specific licensing plan.</span></span>
    
- <span data-ttu-id="e0233-124">**ConsumedUnits:** 특정 라이선스 계획에서 사용자에 게 할당 한 라이선스 수입니다.</span><span class="sxs-lookup"><span data-stu-id="e0233-124">**ConsumedUnits:** Number of licenses that you've assigned to users from a specific licensing plan.</span></span>
    
<span data-ttu-id="e0233-125">모든 라이선스 계획에서 사용할 수 있는 Office 365 서비스에 대 한 세부 정보를 보려면 먼저 라이선스 계획 목록을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0233-125">To view details about the Office 365 services that are available in all of your license plans, first display a list of your license plans.</span></span>

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="e0233-126">다음으로, 라이선스 계획 정보를 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0233-126">Next, store the license plans information in a variable.</span></span>

```powershell
$licenses = Get-AzureADSubscribedSku
```

<span data-ttu-id="e0233-127">다음으로, 특정 라이선스 계획에서 서비스를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0233-127">Next, display the services in a specific license plan.</span></span>

```powershell
$licenses[<index>].ServicePlans
```

<span data-ttu-id="e0233-128">\<index>는 `Get-AzureADSubscribedSku | Select SkuPartNumber` 명령 표시에서 1을 뺀 값으로 라이선스 계획의 행 번호를 지정 하는 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="e0233-128">\<index> is an integer that specifies the row number of the license plan from the display of the `Get-AzureADSubscribedSku | Select SkuPartNumber` command, minus 1.</span></span>

<span data-ttu-id="e0233-129">예를 들어 다음과 같이 `Get-AzureADSubscribedSku | Select SkuPartNumber` 명령을 표시 하는 경우를 예로 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0233-129">For example, if the display of the `Get-AzureADSubscribedSku | Select SkuPartNumber` command is this:</span></span>

```powershell
SkuPartNumber
-------------
WIN10_VDA_E5
EMSPREMIUM
ENTERPRISEPREMIUM
FLOW_FREE
```

<span data-ttu-id="e0233-130">그런 다음 ENTERPRISEPREMIUM 라이선스 계획에 대 한 서비스를 표시 하는 명령은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e0233-130">Then the command to display the services for the ENTERPRISEPREMIUM license plan is this:</span></span>

```powershell
$licenses[2].ServicePlans
```

<span data-ttu-id="e0233-131">ENTERPRISEPREMIUM은 세 번째 행입니다.</span><span class="sxs-lookup"><span data-stu-id="e0233-131">ENTERPRISEPREMIUM is the third row.</span></span> <span data-ttu-id="e0233-132">따라서 인덱스 값은 (3-1) 또는 2입니다.</span><span class="sxs-lookup"><span data-stu-id="e0233-132">Therefore, the index value is (3 - 1), or 2.</span></span>

<span data-ttu-id="e0233-133">라이선스 계획의 전체 목록 (제품 이름), 포함 된 서비스 계획 및 해당 하는 이름에 대 한 자세한 내용은 [product name and service plan identifier for license](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="e0233-133">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="e0233-134">Windows PowerShell용 Microsoft Azure Active Directory 모듈 사용하기</span><span class="sxs-lookup"><span data-stu-id="e0233-134">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="e0233-135">먼저, [Office 365 테넌트에 연결](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)합니다.</span><span class="sxs-lookup"><span data-stu-id="e0233-135">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

>[!Note]
><span data-ttu-id="e0233-136">이 항목에서 설명하는 절차를 자동화하는 PowerShell 스크립트를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0233-136">A PowerShell script is available that automates the procedures described in this topic.</span></span> <span data-ttu-id="e0233-137">특히이 스크립트를 사용 하면 Sway를 포함 하 여 Office 365 조직에서 서비스를 확인 하 고 사용 하지 않도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0233-137">Specifically, the script lets you view and disable services in your Office 365 organization, including Sway.</span></span> <span data-ttu-id="e0233-138">자세한 내용은 [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e0233-138">For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
>
    
<span data-ttu-id="e0233-139">현재 라이선스 계획 및 각 계획에 사용 가능한 라이선스에 대 한 요약 정보를 보려면 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0233-139">To view summary information about your current licensing plans and the available licenses for each plan, run the following command:</span></span>
  
```powershell
Get-MsolAccountSku
```

<span data-ttu-id="e0233-140">결과에는 다음 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0233-140">The results contain the following information:</span></span>
  
- <span data-ttu-id="e0233-141">**AccountSkuId:** 구문을 `<CompanyName>:<LicensingPlan>`사용 하 여 조직에 사용할 수 있는 라이선스 계획을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0233-141">**AccountSkuId:** Show the available licensing plans for your organization by using the syntax `<CompanyName>:<LicensingPlan>`.</span></span>  <span data-ttu-id="e0233-142">_<CompanyName>_ 은 Office 365에서 등록할 때 입력 한 값 이며 조직에서 고유 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0233-142">_<CompanyName>_ is the value that you provided when you enrolled in Office 365, and is unique for your organization.</span></span> <span data-ttu-id="e0233-143">_<LicensingPlan>_ 값은 모든 사용자에 대해 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0233-143">The _<LicensingPlan>_ value is the same for everyone.</span></span> <span data-ttu-id="e0233-144">예를 들어이 값 `litwareinc:ENTERPRISEPACK`에서 회사 이름은 `litwareinc`및 라이선스 계획 이름 `ENTERPRISEPACK`(Office 365 Enterprise e 3의 시스템 이름)입니다.</span><span class="sxs-lookup"><span data-stu-id="e0233-144">For example, in the value `litwareinc:ENTERPRISEPACK`, the company name is  `litwareinc`, and the licensing plan name  `ENTERPRISEPACK`, which is the system name for Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="e0233-145">**Activeunits:** 특정 라이선스 계획을 위해 구매한 라이선스 수입니다.</span><span class="sxs-lookup"><span data-stu-id="e0233-145">**ActiveUnits:** Number of licenses that you've purchased for a specific licensing plan.</span></span>
    
- <span data-ttu-id="e0233-146">**WarningUnits:** 갱신 하지 않고 30 일 유예 기간 이후에 만료 되는 라이선스 요금제의 라이선스 수입니다.</span><span class="sxs-lookup"><span data-stu-id="e0233-146">**WarningUnits:** Number of licenses in a licensing plan that you haven't renewed, and that will expire after the 30-day grace period.</span></span>
    
- <span data-ttu-id="e0233-147">**ConsumedUnits:** 특정 라이선스 계획에서 사용자에 게 할당 한 라이선스 수입니다.</span><span class="sxs-lookup"><span data-stu-id="e0233-147">**ConsumedUnits:** Number of licenses that you've assigned to users from a specific licensing plan.</span></span>
    
<span data-ttu-id="e0233-148">모든 라이선스 계획에서 사용할 수 있는 Office 365 서비스에 대 한 세부 정보를 보려면 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0233-148">To view details about the Office 365 services that are available in all of your license plans, run the following command:</span></span>
  
```powershell
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

<span data-ttu-id="e0233-149">다음 표에서는 가장 일반적인 서비스에 대 한 Office 365 서비스 계획 및 해당 이름을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e0233-149">The following table shows the Office 365 service plans and their friendly names for the most common services.</span></span> <span data-ttu-id="e0233-150">서비스 계획 목록이 다를 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0233-150">Your list of service plans might be different.</span></span> 
  
|<span data-ttu-id="e0233-151">**서비스 계획**</span><span class="sxs-lookup"><span data-stu-id="e0233-151">**Service plan**</span></span>|<span data-ttu-id="e0233-152">**설명**</span><span class="sxs-lookup"><span data-stu-id="e0233-152">**Description**</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="e0233-153">Sway</span><span class="sxs-lookup"><span data-stu-id="e0233-153">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="e0233-154">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="e0233-154">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="e0233-155">Yammer</span><span class="sxs-lookup"><span data-stu-id="e0233-155">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="e0233-156">RMS(Azure 권한 관리)</span><span class="sxs-lookup"><span data-stu-id="e0233-156">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="e0233-157">Office Professional Plus</span><span class="sxs-lookup"><span data-stu-id="e0233-157">Office Professional Plus</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="e0233-158">비즈니스용 Skype Online</span><span class="sxs-lookup"><span data-stu-id="e0233-158">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="e0233-159">사무실</span><span class="sxs-lookup"><span data-stu-id="e0233-159">Office</span></span>  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="e0233-160">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="e0233-160">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="e0233-161">Exchange Online 계획 2</span><span class="sxs-lookup"><span data-stu-id="e0233-161">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="e0233-162">라이선스 계획의 전체 목록 (제품 이름), 포함 된 서비스 계획 및 해당 하는 이름에 대 한 자세한 내용은 [product name and service plan identifier for license](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="e0233-162">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>

<span data-ttu-id="e0233-163">특정 라이선스 계획에서 사용할 수 있는 Office 365 서비스에 대 한 세부 정보를 보려면 다음 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0233-163">To view details about the Office 365 services that are available in a specific licensing plan, use the following syntax.</span></span>
  
```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```

<span data-ttu-id="e0233-164">이 예에서는 litwareinc: ENTERPRISEPACK (Office 365 Enterprise E3) 라이선스 계획에서 사용할 수 있는 Office 365 서비스를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0233-164">This example shows the Office 365 services that are available in the litwareinc:ENTERPRISEPACK (Office 365 Enterprise E3) licensing plan.</span></span>
  
```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "litwareinc:ENTERPRISEPACK"}).ServiceStatus
```


## <a name="new-to-office-365"></a><span data-ttu-id="e0233-165">Office 365의 새로운 기능</span><span class="sxs-lookup"><span data-stu-id="e0233-165">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a><span data-ttu-id="e0233-166">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e0233-166">See also</span></span>

[<span data-ttu-id="e0233-167">Office 365 PowerShell로 사용자 계정 및 라이선스 관리</span><span class="sxs-lookup"><span data-stu-id="e0233-167">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="e0233-168">Office 365 PowerShell 사용한 Office 365 관리</span><span class="sxs-lookup"><span data-stu-id="e0233-168">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="e0233-169">Office 365 PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="e0233-169">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
