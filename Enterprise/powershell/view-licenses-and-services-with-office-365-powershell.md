---
title: 라이선스 및 Office 365 PowerShell을 사용 하 여 서비스를 표시 합니다.
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
ms.audience: Admin
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
description: 라이선스 계획, 서비스 및 Office 365 조직에서 사용할 수 있는 라이선스에 대 한 정보를 보려면 Office 365 PowerShell을 사용 하는 방법에 설명 합니다.
ms.openlocfilehash: e4c4a0570cafd3d9cb775dd99c5f75da613715e3
ms.sourcegitcommit: 15db0f1e5f8036e46063662d7df22387906f8ba7
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/04/2019
ms.locfileid: "27546539"
---
# <a name="view-licenses-and-services-with-office-365-powershell"></a><span data-ttu-id="a6d6f-103">라이선스 및 Office 365 PowerShell을 사용 하 여 서비스를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6d6f-103">View licenses and services with Office 365 PowerShell</span></span>

<span data-ttu-id="a6d6f-104">**요약:** 라이선스 계획, 서비스 및 Office 365 조직에서 사용할 수 있는 라이선스에 대 한 정보를 보려면 Office 365 PowerShell을 사용 하는 방법에 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6d6f-104">**Summary:** Explains how to use Office 365 PowerShell to view information about the licensing plans, services, and licenses that are available in your Office 365 organization.</span></span>
  
<span data-ttu-id="a6d6f-105">모든 Office 365 구독 다음과 같은 요소로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6d6f-105">Every Office 365 subscription consists of the following elements:</span></span>

- <span data-ttu-id="a6d6f-p101">**라이선스 계획** Office 365 계획 또는 라이선스 계획은 라고도 합니다. 라이선스 계획 사용자에 게 사용할 수 있는 Office 365 서비스를 정의 합니다. Office 365 구독에 여러 라이선스 계획을 포함할 수 있습니다. 예제 라이선스 계획에는 Office 365 Enterprise E3 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a6d6f-p101">**Licensing plans** These are also known as license plans or Office 365 plans. Licensing plans define the Office 365 services that are available to users. Your Office 365 subscription may contain multiple licensing plans. An example licensing plan would be Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="a6d6f-p102">**서비스** 이러한 서비스 계획 라고도 합니다. 서비스에는 Office 365 제품, 기능 및 기능 라이선스 각 계획에서 사용할 수 있는 Exchange Online 및 Office Professional Plus 예는입니다. 사용자가 서로 다른 서비스에 대 한 액세스 권한을 부여 하는 다른 라이선스 계획에서 자신에 게 할당 하는 여러 라이선스를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6d6f-p102">**Services** These are also known as service plans. Services are the Office 365 products, features, and capabilities that are available in each licensing plan, for example, Exchange Online and Office Professional Plus. Users can have multiple licenses assigned to them from different licensing plans that grant access to different services.</span></span>
    
- <span data-ttu-id="a6d6f-p103">**라이선스** 각 라이선스 계획을 구입한 라이선스 수를 포함 합니다. 라이선스 계획에 의해 정의 되는 Office 365 서비스를 사용할 수 있도록 사용자에 게 라이선스를 할당 합니다. 모든 사용자 계정이 Office 365에 로그온 하 고 서비스를 사용할 수 있도록 하나의 라이선스 계획에서 하나 이상의 라이선스가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6d6f-p103">**Licenses** Each licensing plan contains the number of licenses that you purchased. You assign licenses to users so they can use the Office 365 services that are defined by the licensing plan. Every user account requires at least one license from one licensing plan so they can log on to Office 365 and use the services.</span></span>
    
<span data-ttu-id="a6d6f-p104">Office 365 조직에서 사용 가능한 라이선스 계획, 라이선스 및 서비스에 대 한 세부 정보를 보려면 Office 365 PowerShell를 사용할 수 있습니다. 제품, 기능 및 다른 Office 365 구독에서 사용할 수 있는 서비스에 대 한 자세한 내용은 [Office 365 계획 옵션](https://go.microsoft.com/fwlink/p/?LinkId=691147)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="a6d6f-p104">You can use Office 365 PowerShell to view details about the available licensing plans, licenses, and services in your Office 365 organization. For more information about the products, features, and services that are available in different Office 365 subscriptions, see [Office 365 Plan Options](https://go.microsoft.com/fwlink/p/?LinkId=691147).</span></span>


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="a6d6f-118">Azure Active Directory PowerShell을 사용 하 여 그래프 모듈에 대 한</span><span class="sxs-lookup"><span data-stu-id="a6d6f-118">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="a6d6f-119">첫째, [Office 365 테 넌 트에 연결](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)합니다.</span><span class="sxs-lookup"><span data-stu-id="a6d6f-119">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
<span data-ttu-id="a6d6f-120">각 계획에 대 한 사용 가능한 라이선스 및 현재 라이선스 계획 하는 방법에 대 한 요약 정보를 보려면 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6d6f-120">To view summary information about your current licensing plans and the available licenses for each plan, run the following command:</span></span>
  
```
Get-AzureADSubscribedSku | Select -Property Sku*,ConsumedUnits -ExpandProperty PrepaidUnits
```

<span data-ttu-id="a6d6f-121">결과에는 다음 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6d6f-121">The results contain the following information:</span></span>
  
- <span data-ttu-id="a6d6f-122">**SkuPartNumber:** 조직에 대 한 사용 가능한 라이선스 계획 표시 > 등 `ENTERPRISEPACK` Office 365 Enterprise E3에 대 한 시스템 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="a6d6f-122">**SkuPartNumber:** Show the available licensing plans for your organization> For example, `ENTERPRISEPACK` is the system name for Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="a6d6f-123">**사용:** 특정 라이선스 계획에 대 한 구입한 라이선스 개수입니다.</span><span class="sxs-lookup"><span data-stu-id="a6d6f-123">**Enabled:** Number of licenses that you've purchased for a specific licensing plan.</span></span>
    
- <span data-ttu-id="a6d6f-124">**ConsumedUnits:** 특정 라이선스 계획에서 사용자에 게 할당 했을 때 라이선스의 수입니다.</span><span class="sxs-lookup"><span data-stu-id="a6d6f-124">**ConsumedUnits:** Number of licenses that you've assigned to users from a specific licensing plan.</span></span>
    
<span data-ttu-id="a6d6f-125">모든 사용자의 라이선스 계획에서 사용할 수 있는 Office 365 서비스에 대 한 세부 정보를 보려면 먼저 라이선스 계획의 목록을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6d6f-125">To view details about the Office 365 services that are available in all of your license plans, first display a list of your license plans.</span></span>

````
Get-AzureADSubscribedSku | Select SkuPartNumber
````

<span data-ttu-id="a6d6f-126">다음으로, 라이선스 계획 정보를 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6d6f-126">Next, store the license plans information in a variable.</span></span>

````
$licenses = Get-AzureADSubscribedSku
````

<span data-ttu-id="a6d6f-127">다음으로, 특정 라이선스 계획에서 서비스를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6d6f-127">Next, display the services in a specific license plan.</span></span>

````
$licenses[<index>].ServicePlan
````

<span data-ttu-id="a6d6f-128">\<인덱스 >은 표시에서 라이선스 계획의 행 번호를 지정 하는 정수는 `Get-AzureADSubscribedSku | Select SkuPartNumber` 명령 1을 뺀 값입니다.</span><span class="sxs-lookup"><span data-stu-id="a6d6f-128">\<index> is an integer that specifies the row number of the license plan from the display of the `Get-AzureADSubscribedSku | Select SkuPartNumber` command, minus 1.</span></span>

<span data-ttu-id="a6d6f-129">예, 하는 경우의 표시는 `Get-AzureADSubscribedSku | Select SkuPartNumber` 명령은이:</span><span class="sxs-lookup"><span data-stu-id="a6d6f-129">For example, if the display of the `Get-AzureADSubscribedSku | Select SkuPartNumber` command is this:</span></span>

````
SkuPartNumber
-------------
WIN10_VDA_E5
EMSPREMIUM
ENTERPRISEPREMIUM
FLOW_FREE
````

<span data-ttu-id="a6d6f-130">그런 다음 ENTERPRISEPREMIUM 라이선스 계획에 대 한 서비스를 표시 하는 명령은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a6d6f-130">Then the command to display the services for the ENTERPRISEPREMIUM license plan is this:</span></span>

````
$licenses[2].ServicePlan
````

<span data-ttu-id="a6d6f-p105">ENTERPRISEPREMIUM은 세번째 행입니다. 따라서 인덱스 값은 (3-1) 또는 2입니다.</span><span class="sxs-lookup"><span data-stu-id="a6d6f-p105">ENTERPRISEPREMIUM is the third row. Therefore, the index value is (3 - 1), or 2.</span></span>

<span data-ttu-id="a6d6f-133">전체 목록은 라이선스 계획 (제품 이름 라고도 함)가 포함 된 서비스 계획 및 해당 친숙 한 이름, [제품 이름 및 라이선스에 대 한 서비스 계획 식별자를](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="a6d6f-133">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="a6d6f-134">Windows PowerShell 용 Microsoft Azure Active Directory 모듈을 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="a6d6f-134">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="a6d6f-135">첫째, [Office 365 테 넌 트에 연결](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)합니다.</span><span class="sxs-lookup"><span data-stu-id="a6d6f-135">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

>[!Note]
><span data-ttu-id="a6d6f-p106">PowerShell 스크립트를 사용할 수 있는이 항목에서 설명 하는 절차를 자동화 합니다. 특히, 스크립트 통해 보기 및 Office 365 조직 전체에서 영향을 포함 하 여 서비스를 사용 하지 않도록 설정할 수 있습니다. 자세한 내용은 [Office 365 powershell 영향에 대 한 액세스를 사용 하지 않도록 설정](disable-access-to-sway-with-office-365-powershell.md)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="a6d6f-p106">A PowerShell script is available that automates the procedures described in this topic. Specifically, the script lets you view and disable services in your Office 365 organization, including Sway. For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
>
    
<span data-ttu-id="a6d6f-139">각 계획에 대 한 사용 가능한 라이선스 및 현재 라이선스 계획 하는 방법에 대 한 요약 정보를 보려면 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6d6f-139">To view summary information about your current licensing plans and the available licenses for each plan, run the following command:</span></span>
  
```
Get-MsolAccountSku
```

<span data-ttu-id="a6d6f-140">결과에는 다음 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6d6f-140">The results contain the following information:</span></span>
  
- <span data-ttu-id="a6d6f-p107">**AccountSkuId:** 구문을 사용 하 여 조직에 대 한 사용 가능한 라이선스 계획 표시 `<CompanyName>:<LicensingPlan>`합니다.  _<CompanyName>_ 는 Office 365에 등록 하 고 조직에 대 한 고유함 때 제공한 값입니다. _<LicensingPlan>_ 값은 모든 사용자에 대해 동일 합니다. 값에서 예, `litwareinc:ENTERPRISEPACK`, 회사 이름이 `litwareinc`, 및 라이선스 계획 이름 `ENTERPRISEPACK`, Office 365 Enterprise E3에 대 한 시스템 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="a6d6f-p107">**AccountSkuId:** Show the available licensing plans for your organization by using the syntax `<CompanyName>:<LicensingPlan>`.  _<CompanyName>_ is the value that you provided when you enrolled in Office 365, and is unique for your organization. The _<LicensingPlan>_ value is the same for everyone. For example, in the value `litwareinc:ENTERPRISEPACK`, the company name is  `litwareinc`, and the licensing plan name  `ENTERPRISEPACK`, which is the system name for Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="a6d6f-145">**ActiveUnits:** 특정 라이선스 계획에 대 한 구입한 라이선스 개수입니다.</span><span class="sxs-lookup"><span data-stu-id="a6d6f-145">**ActiveUnits:** Number of licenses that you've purchased for a specific licensing plan.</span></span>
    
- <span data-ttu-id="a6d6f-146">**WarningUnits:** 하면 하지 않은 갱신 되 고 30 일의 유예 기간 후 만료 되는 라이선스 계획에서 라이선스의 수입니다.</span><span class="sxs-lookup"><span data-stu-id="a6d6f-146">**WarningUnits:** Number of licenses in a licensing plan that you haven't renewed, and that will expire after the 30-day grace period.</span></span>
    
- <span data-ttu-id="a6d6f-147">**ConsumedUnits:** 특정 라이선스 계획에서 사용자에 게 할당 했을 때 라이선스의 수입니다.</span><span class="sxs-lookup"><span data-stu-id="a6d6f-147">**ConsumedUnits:** Number of licenses that you've assigned to users from a specific licensing plan.</span></span>
    
<span data-ttu-id="a6d6f-148">모든 사용자의 라이선스 계획에서 사용할 수 있는 Office 365 서비스에 대 한 세부 정보를 보려면 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6d6f-148">To view details about the Office 365 services that are available in all of your license plans, run the following command:</span></span>
  
```
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

<span data-ttu-id="a6d6f-p108">다음 표에서 Office 365 서비스 계획 및 가장 일반적인 서비스에 대 한 친숙 한 이름을 보여줍니다. 서비스 계획의 대화 목록 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6d6f-p108">The following table shows the Office 365 service plans and their friendly names for the most common services. Your list of service plans might be different.</span></span> 
  
|<span data-ttu-id="a6d6f-151">**서비스 계획**</span><span class="sxs-lookup"><span data-stu-id="a6d6f-151">**Service plan**</span></span>|<span data-ttu-id="a6d6f-152">**설명**</span><span class="sxs-lookup"><span data-stu-id="a6d6f-152">**Description**</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="a6d6f-153">Sway</span><span class="sxs-lookup"><span data-stu-id="a6d6f-153">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="a6d6f-154">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="a6d6f-154">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="a6d6f-155">Yammer</span><span class="sxs-lookup"><span data-stu-id="a6d6f-155">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="a6d6f-156">RMS(Azure 권한 관리)</span><span class="sxs-lookup"><span data-stu-id="a6d6f-156">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="a6d6f-157">Office Professional Plus</span><span class="sxs-lookup"><span data-stu-id="a6d6f-157">Office Professional Plus</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="a6d6f-158">비즈니스용 Skype Online</span><span class="sxs-lookup"><span data-stu-id="a6d6f-158">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="a6d6f-159">Office Online</span><span class="sxs-lookup"><span data-stu-id="a6d6f-159">Office Online</span></span>  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="a6d6f-160">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="a6d6f-160">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="a6d6f-161">Exchange Online 계획 2</span><span class="sxs-lookup"><span data-stu-id="a6d6f-161">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="a6d6f-162">전체 목록은 라이선스 계획 (제품 이름 라고도 함)가 포함 된 서비스 계획 및 해당 친숙 한 이름, [제품 이름 및 라이선스에 대 한 서비스 계획 식별자를](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="a6d6f-162">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>

<span data-ttu-id="a6d6f-163">특정 라이선스 계획에서 사용할 수 있는 Office 365 서비스에 대 한 세부 정보를 보려면 다음 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6d6f-163">To view details about the Office 365 services that are available in a specific licensing plan, use the following syntax.</span></span>
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```

<span data-ttu-id="a6d6f-164">이 예제에서는 litwareinc:ENTERPRISEPACK (Office 365 Enterprise E3) 라이선스 계획에서 사용할 수 있는 Office 365 서비스를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="a6d6f-164">This example shows the Office 365 services that are available in the litwareinc:ENTERPRISEPACK (Office 365 Enterprise E3) licensing plan.</span></span>
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "litwareinc:ENTERPRISEPACK"}).ServiceStatus
```


## <a name="new-to-office-365"></a><span data-ttu-id="a6d6f-165">Office 365의 새로운 기능</span><span class="sxs-lookup"><span data-stu-id="a6d6f-165">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a><span data-ttu-id="a6d6f-166">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a6d6f-166">See also</span></span>


[<span data-ttu-id="a6d6f-167">Office 365 PowerShell을 사용하여 사용자 계정 및 라이선스 관리</span><span class="sxs-lookup"><span data-stu-id="a6d6f-167">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="a6d6f-168">Office 365 PowerShell을 사용하여 Office 365 관리</span><span class="sxs-lookup"><span data-stu-id="a6d6f-168">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="a6d6f-169">Office 365 PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="a6d6f-169">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
