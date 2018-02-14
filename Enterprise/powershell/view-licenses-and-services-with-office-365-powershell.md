---
title: "라이선스 및 Office 365 PowerShell을 사용 하 여 서비스를 표시 합니다."
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
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
description: "라이선스 계획, 서비스 및 Office 365 조직에서 사용할 수 있는 라이선스에 대 한 정보를 보려면 Office 365 PowerShell을 사용 하는 방법에 설명 합니다."
ms.openlocfilehash: 718b26c7afb978384918b2de8ea37d01638d3e16
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2018
---
# <a name="view-licenses-and-services-with-office-365-powershell"></a><span data-ttu-id="f930f-103">라이선스 및 Office 365 PowerShell을 사용 하 여 서비스를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="f930f-103">View licenses and services with Office 365 PowerShell</span></span>

<span data-ttu-id="f930f-104">**요약:** 라이선스 계획, 서비스 및 Office 365 조직에서 사용할 수 있는 라이선스에 대 한 정보를 보려면 Office 365 PowerShell을 사용 하는 방법에 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="f930f-104">**Summary:** Explains how to use Office 365 PowerShell to view information about the licensing plans, services, and licenses that are available in your Office 365 organization.</span></span>
  
<span data-ttu-id="f930f-105">모든 Office 365 구독 다음과 같은 요소로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f930f-105">Every Office 365 subscription consists of the following elements:</span></span>
- <span data-ttu-id="f930f-p101">**라이선스 계획** 이러한 aslicense 계획 또는 Office 365 계획을도으로 알려져 있습니다. 라이선스 계획 사용자에 게 사용할 수 있는 Office 365 서비스를 정의 합니다. Office 365 구독에 여러 라이선스 계획을 포함할 수 있습니다. 예제 라이선스 계획에는 Office 365 Enterprise E3 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f930f-p101">**Licensing plans** These are also known aslicense plans or Office 365 plans. Licensing plans define the Office 365 services that are available to users. Your Office 365 subscription may contain multiple licensing plans. An example licensing plan would be Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="f930f-p102">**서비스** 드라이브 들도 알려진된 asservice 계획 합니다. 서비스에는 Office 365 제품, 기능 및 기능 라이선스 각 계획에서 사용할 수 있는 Exchange Online 및 Office Professional Plus 예는입니다. 사용자가 서로 다른 서비스에 대 한 액세스 권한을 부여 하는 다른 라이선스 계획에서 자신에 게 할당 하는 여러 라이선스를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f930f-p102">**Services** These are also known asservice plans. Services are the Office 365 products, features, and capabilities that are available in each licensing plan, for example, Exchange Online and Office Professional Plus. Users can have multiple licenses assigned to them from different licensing plans that grant access to different services.</span></span>
    
- <span data-ttu-id="f930f-p103">**라이선스** 각 라이선스 계획을 구입한 라이선스 수를 포함 합니다. 라이선스 계획에 의해 정의 되는 Office 365 서비스를 사용할 수 있도록 사용자에 게 라이선스를 할당 합니다. 모든 사용자 계정이 Office 365에 로그온 하 고 서비스를 사용할 수 있도록 하나의 라이선스 계획에서 하나 이상의 라이선스가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="f930f-p103">**Licenses** Each licensing plan contains the number of licenses that you purchased. You assign licenses to users so they can use the Office 365 services that are defined by the licensing plan. Every user account requires at least one license from one licensing plan so they can log on to Office 365 and use the services.</span></span>
    
<span data-ttu-id="f930f-p104">Office 365 조직에서 사용 가능한 라이선스 계획, 라이선스 및 서비스에 대 한 세부 정보를 보려면 Office 365 PowerShell를 사용할 수 있습니다. 제품, 기능 및 다른 Office 365 구독에서 사용할 수 있는 서비스에 대 한 자세한 내용은 [Office 365 계획 옵션](https://go.microsoft.com/fwlink/p/?LinkId=691147)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="f930f-p104">You can use Office 365 PowerShell to view details about the available licensing plans, licenses, and services in your Office 365 organization. For more information about the products, features, and services that are available in different Office 365 subscriptions, see [Office 365 Plan Options](https://go.microsoft.com/fwlink/p/?LinkId=691147).</span></span>
## <a name="before-you-begin"></a><span data-ttu-id="f930f-118">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="f930f-118">Before you begin</span></span>
<span data-ttu-id="f930f-119"><a name="RTT"> </a></span><span class="sxs-lookup"><span data-stu-id="f930f-119"></span></span>

- <span data-ttu-id="f930f-p105">이 항목의 절차를 수행하려면 Office 365 PowerShell에 연결되어 있어야 합니다. 지침을 보려면 [PowerShell Office 365에 연결](connect-to-office-365-powershell.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f930f-p105">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="f930f-p106">PowerShell 스크립트를 사용할 수 있는이 항목에서 설명 하는 절차를 자동화 합니다. 특히, 스크립트를 사용 하 보기 및 Office 365 조직 전체에서 영향을 포함 하 여 서비스를 사용 하지 않도록 설정할 수 있습니다. 자세한 내용은 [Office 365 powershell 영향에 대 한 액세스를 사용 하지 않도록 설정](disable-access-to-sway-with-office-365-powershell.md)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="f930f-p106">A PowerShell script is available that automates the procedures described in this topic. Specifically, the script allows you to view and disable services in your Office 365 organization, including Sway. For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
    
## <a name="view-information-about-licensing-plans-and-the-available-licenses"></a><span data-ttu-id="f930f-125">라이선스 계획 및 사용 가능한 라이선스에 대한 정보 보기</span><span class="sxs-lookup"><span data-stu-id="f930f-125">View information about licensing plans and the available licenses</span></span>
<span data-ttu-id="f930f-126"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="f930f-126"></span></span>

<span data-ttu-id="f930f-127">각 계획에 대 한 사용 가능한 라이선스 및 현재 라이선스 계획 하는 방법에 대 한 요약 정보를 보려면 Office 365 PowerShell에서 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="f930f-127">To view summary information about your current licensing plans and the available licenses for each plan, run the following command in Office 365 PowerShell:</span></span>
  
```
Get-MsolAccountSku
```

<span data-ttu-id="f930f-128">결과에는 다음 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="f930f-128">The results contain the following information:</span></span>
  
- <span data-ttu-id="f930f-p107">**AccountSkuId:** 구문을 사용 하 여 조직에 대 한 사용 가능한 라이선스 계획 표시 `<CompanyName>:<LicensingPlan>`합니다.  _<CompanyName>_ 는 Office 365에 등록 하 고 조직에 대 한 고유함 때 제공한 값입니다. _<LicensingPlan>_ 값은 모든 사용자에 대해 동일 합니다. 값에서 예, `litwareinc:ENTERPRISEPACK`, 회사 이름이 `litwareinc`, 및 라이선스 계획 이름 `ENTERPRISEPACK`, Office 365 Enterprise E3에 대 한 시스템 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="f930f-p107">**AccountSkuId:** Show the available licensing plans for your organization by using the syntax `<CompanyName>:<LicensingPlan>`.  _<CompanyName>_ is the value that you provided when you enrolled in Office 365, and is unique for your organization. The _<LicensingPlan>_ value is the same for everyone. For example, in the value `litwareinc:ENTERPRISEPACK`, the company name is  `litwareinc`, and the licensing plan name  `ENTERPRISEPACK`, which is the system name for Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="f930f-133">**ActiveUnits:** 특정 라이선스 계획에 대 한 구매 했을 때 라이선스의 수입니다.</span><span class="sxs-lookup"><span data-stu-id="f930f-133">**ActiveUnits:** Number of licenses that you've purchases for a specific licensing plan.</span></span>
    
- <span data-ttu-id="f930f-134">**WarningUnits:** 하면 하지 않은 갱신 되 고 30 일의 유예 기간 후 만료 되는 라이선스 계획에서 라이선스의 수입니다.</span><span class="sxs-lookup"><span data-stu-id="f930f-134">**WarningUnits:** Number of licenses in a licensing plan that you haven't renewed, and that will expire after the 30-day grace period.</span></span>
    
- <span data-ttu-id="f930f-135">**ConsumedUnits:** 특정 라이선스 계획에서 사용자에 게 할당 했을 때 라이선스의 수입니다.</span><span class="sxs-lookup"><span data-stu-id="f930f-135">**ConsumedUnits:** Number of licenses that you've assigned to users from a specific licensing plan.</span></span>
    
<span data-ttu-id="f930f-136">모든 사용자의 라이선스 계획에서 사용할 수 있는 Office 365 서비스에 대 한 세부 정보를 보려면 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="f930f-136">To view details about the Office 365 services that are available in all of your license plans, run the following command:</span></span>
  
```
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

<span data-ttu-id="f930f-p108">다음 표에서 Office 365 서비스 계획 및 가장 일반적인 서비스에 대 한 친숙 한 이름을 보여줍니다. 서비스 계획의 대화 목록 다를 수 있습니다. 서비스 계획 및 친숙 한 이름을 전체 목록은 [Office 지원](https://support.office.com/home/contact)서비스에 문의 합니다.</span><span class="sxs-lookup"><span data-stu-id="f930f-p108">The following table shows the Office 365 service plans and their friendly names for the most common services. Your list of service plans might be different. For a complete list of service plans and their friendly names, contact [Office Support](https://support.office.com/home/contact).</span></span>
  
|<span data-ttu-id="f930f-140">서비스 계획 \* \* \*</span><span class="sxs-lookup"><span data-stu-id="f930f-140">****Service plan****</span></span>|<span data-ttu-id="f930f-141">설명 \* \* \*</span><span class="sxs-lookup"><span data-stu-id="f930f-141">****Description****</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="f930f-142">Sway</span><span class="sxs-lookup"><span data-stu-id="f930f-142">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="f930f-143">Microsoft 팀</span><span class="sxs-lookup"><span data-stu-id="f930f-143">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="f930f-144">Yammer</span><span class="sxs-lookup"><span data-stu-id="f930f-144">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="f930f-145">RMS(Azure 권한 관리)</span><span class="sxs-lookup"><span data-stu-id="f930f-145">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="f930f-146">Office Professional Plus</span><span class="sxs-lookup"><span data-stu-id="f930f-146">Office Professional Plus</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="f930f-147">비즈니스용 Skype 온라인</span><span class="sxs-lookup"><span data-stu-id="f930f-147">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="f930f-148">Office Online</span><span class="sxs-lookup"><span data-stu-id="f930f-148">Office Online</span></span>  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="f930f-149">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="f930f-149">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="f930f-150">Exchange Online 계획 2</span><span class="sxs-lookup"><span data-stu-id="f930f-150">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="f930f-151">특정 라이선스 계획에서 사용할 수 있는 Office 365 서비스에 대 한 세부 정보를 보려면 다음 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f930f-151">To view details about the Office 365 services that are available in a specific licensing plan, use the following syntax.</span></span>
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq " <AccountSkuId>"}).ServiceStatus
```

<span data-ttu-id="f930f-152">이 예제에서는 litwareinc:ENTERPRISEPACK (Office 365 Enterprise E3) 라이선스 계획에서 사용할 수 있는 Office 365 서비스를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="f930f-152">This example shows the Office 365 services that are available in the  litwareinc:ENTERPRISEPACK (Office 365 Enterprise E3) licensing plan.</span></span>
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "litwareinc:ENTERPRISEPACK"}).ServiceStatus
```

## <a name="new-to-office-365"></a><span data-ttu-id="f930f-153">Office 365의 새로운 기능</span><span class="sxs-lookup"><span data-stu-id="f930f-153">New to Office 365?</span></span>
<span data-ttu-id="f930f-154"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="f930f-154"></span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a><span data-ttu-id="f930f-155">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f930f-155">See also</span></span>
<span data-ttu-id="f930f-156"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="f930f-156"></span></span>

#### 

[<span data-ttu-id="f930f-157">Office 365 PowerShell을 사용 하 여 허가 된 / 허가 되지 않은 사용자 보기</span><span class="sxs-lookup"><span data-stu-id="f930f-157">View licensed and unlicensed users with Office 365 PowerShell</span></span>](view-licensed-and-unlicensed-users-with-office-365-powershell.md)
  
[<span data-ttu-id="f930f-158">Office 365 PowerShell을 사용 하 여 계정 라이센스와 서비스 정보 보기</span><span class="sxs-lookup"><span data-stu-id="f930f-158">View account license and service details with Office 365 PowerShell</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
#### 

[<span data-ttu-id="f930f-159">Get-msolaccountsku</span><span class="sxs-lookup"><span data-stu-id="f930f-159">Get-MsolAccountSku</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691549)

