---
title: "사용자 라이선스를 할당 하는 동안 서비스에 대 한 액세스를 사용 하지 않도록 설정"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom:
- PowerShell
- Ent_Office_Other
- DecEntMigration
ms.assetid: bb003bdb-3c22-4141-ae3b-f0656fc23b9c
description: "사용자 계정에 라이선스를 할당 하 고 Office 365 PowerShell을 사용 하 여 동시에 특정 서비스 계획을 사용 하지 않도록 설정 하는 방법에 알아봅니다."
ms.openlocfilehash: 907314e13b353e5d5ddbcd8fe467db568473d0b3
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2017
---
# <a name="disable-access-to-services-while-assigning-user-licenses"></a><span data-ttu-id="5d28c-103">사용자 라이선스를 할당 하는 동안 서비스에 대 한 액세스를 사용 하지 않도록 설정</span><span class="sxs-lookup"><span data-stu-id="5d28c-103">Disable access to services while assigning user licenses</span></span>

<span data-ttu-id="5d28c-104">**요약:**  사용자 계정에 라이선스를 할당 하 고 Office 365 PowerShell을 사용 하 여 동시에 특정 서비스 계획을 사용 하지 않도록 설정 하는 방법에 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="5d28c-104">**Summary:**  Learn how to assign licenses to user accounts and disable specific service plans at the same time using Office 365 PowerShell.</span></span>
  
<span data-ttu-id="5d28c-p101">Office 365 구독 개별 서비스에 대 한 서비스 계획 함께 제공 됩니다. Office 365 관리자는 종종 사용자에 게 라이선스를 할당 하는 경우 특정 계획을 사용 하지 않도록 설정 해야 합니다. 이 문서의 지침을 개별 사용자 계정 또는 여러 사용자 계정에 대 한 PowerShell을 사용 하 여 특정 서비스 계획을 사용 하지 않도록 설정 하는 동안 Office 365 라이선스를 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d28c-p101">Office 365 subscriptions come with service plans for individual services. Office 365 administrators often need to disable certain plans when assigning licenses to users. With the instructions in this article, you can assign an Office 365 license while disabling specific service plans using PowerShell for an individual user account or multiple user accounts.</span></span>
  
> [!NOTE]
> <span data-ttu-id="5d28c-108">이 문서는 감사 Parmar, Microsoft 지원 에스컬레이션 엔지니어의 작업을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="5d28c-108">This article is based on the work of Siddhartha Parmar, a Microsoft Support Escalation Engineer.</span></span> 
  
## <a name="before-you-begin"></a><span data-ttu-id="5d28c-109">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="5d28c-109">Before you begin</span></span>

<span data-ttu-id="5d28c-p102">이 항목의 절차에서는 Office 365 PowerShell에 연결 해야 합니다. 자세한 내용은 [Office 365 PowerShell 연결](connect-to-office-365-powershell.md)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="5d28c-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
## <a name="collect-information-about-subscriptions-and-service-plans"></a><span data-ttu-id="5d28c-112">구독 및 서비스 계획 하는 방법에 대 한 정보 수집</span><span class="sxs-lookup"><span data-stu-id="5d28c-112">Collect information about subscriptions and service plans</span></span>

<span data-ttu-id="5d28c-113">현재 구독을 참조 하려면이 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="5d28c-113">Run this command to see your current subscriptions:</span></span>
  
```
Get-MsolAccountSku
```

<span data-ttu-id="5d28c-114">표시에서 된 `Get-MsolAccountSku` 명령 합니다.</span><span class="sxs-lookup"><span data-stu-id="5d28c-114">In the display of the  `Get-MsolAccountSku` command:</span></span>
  
- <span data-ttu-id="5d28c-p103">**AccountSkuId** 은에서 조직에 대 한 구독 \<OrganizationName >:\<구독 > 형식입니다. \<OrganizationName > Office 365에 등록 하 고 조직에 대 한 고유함 때 제공한 값입니다. \<구독 > 값은 특정 구독에 사용 됩니다. 예, litwareinc:ENTERPRISEPACK에 대 한 조직 이름은 litwareinc, 하 고 구독 이름은 ENTERPRISEPACK (Office 365 Enterprise E3)입니다.</span><span class="sxs-lookup"><span data-stu-id="5d28c-p103">**AccountSkuId** is a subscription for your organization in \<OrganizationName>:\<Subscription> format. The \<OrganizationName> is the value that you provided when you enrolled in Office 365, and is unique for your organization. The \<Subscription> value is for a specific subscription. For example, for litwareinc:ENTERPRISEPACK, the organization name is litwareinc, and the subscription name is ENTERPRISEPACK (Office 365 Enterprise E3).</span></span>
    
- <span data-ttu-id="5d28c-119">**ActiveUnits** 는 구독에 대 한 구입한 라이선스의 수입니다.</span><span class="sxs-lookup"><span data-stu-id="5d28c-119">**ActiveUnits** is the number of licenses that you've purchased for the subscription.</span></span>
    
- <span data-ttu-id="5d28c-120">**WarningUnits** 는 하면 하지 않은 갱신 되 고 30 일의 유예 기간 후 만료 되는 구독에서 라이선스의 수입니다.</span><span class="sxs-lookup"><span data-stu-id="5d28c-120">**WarningUnits** is the number of licenses in a subscription that you haven't renewed, and that will expire after the 30-day grace period.</span></span>
    
- <span data-ttu-id="5d28c-121">**ConsumedUnits** 는 구독에 대 한 사용자에 게 할당 했을 때 라이선스의 수입니다.</span><span class="sxs-lookup"><span data-stu-id="5d28c-121">**ConsumedUnits** is the number of licenses that you've assigned to users for the subscription.</span></span>
    
<span data-ttu-id="5d28c-p104">라이선스 할당 하려는 사용자를 포함 하는 Office 365 구독에 대 한 AccountSkuId note 합니다. 또한 충분 한 라이선스를 할당 되었는지 확인 ( **ActiveUnits** 에서 **ConsumedUnits** 빼기).</span><span class="sxs-lookup"><span data-stu-id="5d28c-p104">Note the AccountSkuId for your Office 365 subscription that contains the users you want to license. Also, ensure that there are enough licenses to assign (subtract **ConsumedUnits** from **ActiveUnits** ).</span></span>
  
<span data-ttu-id="5d28c-124">이 명령은 모든 구독에서 사용할 수 있는 Office 365 서비스 계획에 대 한 자세한 내용을 보려면 다음을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="5d28c-124">Next, run this command to see the details about the Office 365 service plans that are available in all your subscriptions:</span></span>
  
```
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

<span data-ttu-id="5d28c-125">이 명령의 디스플레이에서 사용자에 게 라이선스를 할당 하는 경우 사용 하지 않도록 설정 하려면 어떤 서비스 계획을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5d28c-125">From the display of this command, determine which service plans you would like to disable when you assign licenses to users.</span></span>
  
<span data-ttu-id="5d28c-126">다음은 서비스 계획 및 해당가 Office 365 서비스의 일부 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="5d28c-126">Here is a partial list of service plans and their corresponding Office 365 services.</span></span>
  
|<span data-ttu-id="5d28c-127">**서비스 계획**</span><span class="sxs-lookup"><span data-stu-id="5d28c-127">**Service plan**</span></span>|<span data-ttu-id="5d28c-128">**설명**</span><span class="sxs-lookup"><span data-stu-id="5d28c-128">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="5d28c-129">영향</span><span class="sxs-lookup"><span data-stu-id="5d28c-129">SWAY</span></span>  <br/> |<span data-ttu-id="5d28c-130">Sway</span><span class="sxs-lookup"><span data-stu-id="5d28c-130">Sway</span></span>  <br/> |
|<span data-ttu-id="5d28c-131">INTUNE_O365</span><span class="sxs-lookup"><span data-stu-id="5d28c-131">INTUNE_O365</span></span>  <br/> |<span data-ttu-id="5d28c-132">Office 365의 모바일 장치 관리</span><span class="sxs-lookup"><span data-stu-id="5d28c-132">Mobile Device Management for Office 365</span></span>  <br/> |
|<span data-ttu-id="5d28c-133">YAMMER_ENTERPRISE</span><span class="sxs-lookup"><span data-stu-id="5d28c-133">YAMMER_ENTERPRISE</span></span>  <br/> |<span data-ttu-id="5d28c-134">Yammer</span><span class="sxs-lookup"><span data-stu-id="5d28c-134">Yammer</span></span>  <br/> |
|<span data-ttu-id="5d28c-135">RMS_S_ENTERPRISE</span><span class="sxs-lookup"><span data-stu-id="5d28c-135">RMS_S_ENTERPRISE</span></span>  <br/> |<span data-ttu-id="5d28c-136">RMS(Azure 권한 관리)</span><span class="sxs-lookup"><span data-stu-id="5d28c-136">Azure Rights Management (RMS)</span></span>  <br/> |
|<span data-ttu-id="5d28c-137">OFFICESUBSCRIPTION</span><span class="sxs-lookup"><span data-stu-id="5d28c-137">OFFICESUBSCRIPTION</span></span>  <br/> |<span data-ttu-id="5d28c-138">Office Professional Plus</span><span class="sxs-lookup"><span data-stu-id="5d28c-138">Office Professional Plus</span></span>  <br/> |
|<span data-ttu-id="5d28c-139">MCOSTANDARD</span><span class="sxs-lookup"><span data-stu-id="5d28c-139">MCOSTANDARD</span></span>  <br/> |<span data-ttu-id="5d28c-140">비즈니스용 Skype 온라인</span><span class="sxs-lookup"><span data-stu-id="5d28c-140">Skype for Business Online</span></span>  <br/> |
|<span data-ttu-id="5d28c-141">SHAREPOINTWAC</span><span class="sxs-lookup"><span data-stu-id="5d28c-141">SHAREPOINTWAC</span></span>  <br/> |<span data-ttu-id="5d28c-142">Office Online</span><span class="sxs-lookup"><span data-stu-id="5d28c-142">Office Online</span></span>  <br/> |
|<span data-ttu-id="5d28c-143">SHAREPOINTENTERPRISE</span><span class="sxs-lookup"><span data-stu-id="5d28c-143">SHAREPOINTENTERPRISE</span></span>  <br/> |<span data-ttu-id="5d28c-144">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="5d28c-144">SharePoint Online</span></span>  <br/> |
|<span data-ttu-id="5d28c-145">EXCHANGE_S_ENTERPRISE</span><span class="sxs-lookup"><span data-stu-id="5d28c-145">EXCHANGE_S_ENTERPRISE</span></span>  <br/> |<span data-ttu-id="5d28c-146">Exchange Online 계획 2</span><span class="sxs-lookup"><span data-stu-id="5d28c-146">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="5d28c-147">만들었으므로 이제는 AccountSkuId 및 사용 하지 않으려면 서비스 계획, 라이선스에 대 한 개별 사용자 또는 여러 사용자에 게 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d28c-147">Now that you have the AccountSkuId and the service plans to disable, you can assign licenses for an individual user or for multiple users.</span></span>
  
## <a name="for-a-single-user"></a><span data-ttu-id="5d28c-148">단일 사용자에 대 한</span><span class="sxs-lookup"><span data-stu-id="5d28c-148">For a single user</span></span>

<span data-ttu-id="5d28c-p105">단일 사용자에 대 한 사용자 계정, AccountSkuId, 및 서비스 계획의 목록을 사용 하지 않도록 설정 하 고 설명 텍스트를 제거 하려면 사용자 계정 이름에 입력 및 \< 및 > 문자입니다. 다음, PowerShell 명령 프롬프트에서 결과 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="5d28c-p105">For a single user, fill in the user principal name of the user account, the AccountSkuId, and the list of service plans to disable and remove the explanatory text and the \< and > characters. Then, run the resulting commands at the PowerShell command prompt.</span></span>
  
```
$userUPN="<the user's account name in email format>"
$accountSkuId="<the AccountSkuId from the Get-MsolAccountSku command>"
$planList=@( <comma-separated, double-quote enclosed list of the service plans to disable> )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
$user=Get-MsolUser -UserPrincipalName $userUPN
$usageLocation=$user.Usagelocation
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
Set-MsolUser -UserPrincipalName $userUpn -UsageLocation $usageLocation
```

<span data-ttu-id="5d28c-151">Belindan@contoso.com, contoso:ENTERPRISEPACK 라이선스에 대 한 명명 된 계정에 대 한 예제 명령 블록 되며 서비스 계획 사용 하지 않도록 설정 하는 RMS_S_ENTERPRISE, 영향, INTUNE_O365, 및 YAMMER_ENTERPRISE 여기:</span><span class="sxs-lookup"><span data-stu-id="5d28c-151">Here is an example command block for the account named belindan@contoso.com, for the contoso:ENTERPRISEPACK license, and the service plans to disable are RMS_S_ENTERPRISE, SWAY, INTUNE_O365, and YAMMER_ENTERPRISE:</span></span>
  
```
$userUPN="belindan@contoso.com"
$accountSkuId="contoso:ENTERPRISEPACK"
$planList=@( "RMS_S_ENTERPRISE","SWAY","INTUNE_O365","YAMMER_ENTERPRISE" )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
$user=Get-MsolUser -UserPrincipalName $userUPN
$usageLocation=$user.Usagelocation
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
Set-MsolUser -UserPrincipalName $userUpn -UsageLocation $UsageLocation
```

## <a name="for-multiple-users"></a><span data-ttu-id="5d28c-152">여러 사용자에 대 한</span><span class="sxs-lookup"><span data-stu-id="5d28c-152">For multiple users</span></span>

<span data-ttu-id="5d28c-p106">여러 사용자에 대 한이 관리 작업을 수행 하려면 UserPrincipalName 및 usagelocation이 필드를 포함 하는 쉼표로 구분 된 값 (CSV) 텍스트 파일을 만듭니다. 다음은 한 예가입니다.</span><span class="sxs-lookup"><span data-stu-id="5d28c-p106">To perform this administration task for multiple users, create a comma-separated value (CSV) text file that contains the UserPrincipalName and UsageLocation fields. Here is an example:</span></span>
  
```
UserPrincipalName,UsageLocation
ClaudeL@contoso.onmicrosoft.com,FR
LynneB@contoso.onmicrosoft.com,US
ShawnM@contoso.onmicrosoft.com,US
```

<span data-ttu-id="5d28c-155">다음으로 입력 및 출력 CSV 파일, SKU ID 계정 및 서비스 계획을 사용 하지 않으려면 목록이의 위치를 입력 하 고 명령을 입력 하 고 결과 PowerShell 명령 프롬프트에서.</span><span class="sxs-lookup"><span data-stu-id="5d28c-155">Next, fill in the location of the input and output CSV files, the account SKU ID, and the list of service plans to disable, and then run the resulting commands at the PowerShell command prompt.</span></span>
  
```
$inFileName="<path and file name of the input CSV file that contains the users, example: C:\admin\Users2License.CSV>"
$outFileName="<path and file name of the output CSV file that records the results, example: C:\admin\Users2License-Done.CSV>"
$accountSkuId="<the AccountSkuId from the Get-MsolAccountSku command>"
$planList=@( <comma-separated, double-quote enclosed list of the plans to disable> )
$users=Import-Csv $inFileName
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
ForEach ($user in $users)
{
$user.Userprincipalname
$upn=$user.UserPrincipalName
$usageLocation=$user.UsageLocation
Set-MsolUserLicense -UserPrincipalName $upn -AddLicenses $AccountSkuId -ErrorAction SilentlyContinue
sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $upn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
Set-MsolUser -UserPrincipalName $upn -UsageLocation $usageLocation
$users | Get-MsolUser | Select UserPrincipalName, Islicensed,Usagelocation | Export-Csv $outFileName
}
```

<span data-ttu-id="5d28c-156">이 PowerShell 명령 차단 합니다.</span><span class="sxs-lookup"><span data-stu-id="5d28c-156">This PowerShell command block:</span></span>
  
- <span data-ttu-id="5d28c-157">각 사용자의 사용자 계정 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5d28c-157">Displays the user principal name of each user.</span></span>
    
- <span data-ttu-id="5d28c-158">각 사용자에 게 라이선스를 사용자 지정 하는 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="5d28c-158">Assigns customized licenses to each user.</span></span>
    
- <span data-ttu-id="5d28c-159">처리 된 모든 사용자와 CSV 파일을 만들고의 라이선스 상태를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="5d28c-159">Creates a CSV file with all the users that were processed and shows their license status.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="5d28c-160">See also</span><span class="sxs-lookup"><span data-stu-id="5d28c-160">See also</span></span>

#### 

[<span data-ttu-id="5d28c-161">Office 365 PowerShell을 사용 하 여 서비스에 대 한 액세스를 사용 하지 않도록 설정</span><span class="sxs-lookup"><span data-stu-id="5d28c-161">Disable access to services with Office 365 PowerShell</span></span>](disable-access-to-services-with-office-365-powershell.md)
  
[<span data-ttu-id="5d28c-162">Office 365 powershell 영향에 대 한 액세스를 사용 하지 않도록 설정</span><span class="sxs-lookup"><span data-stu-id="5d28c-162">Disable access to Sway with Office 365 PowerShell</span></span>](disable-access-to-sway-with-office-365-powershell.md)
  
[<span data-ttu-id="5d28c-163">사용자 계정 및 Office 365 powershell 라이선스 관리</span><span class="sxs-lookup"><span data-stu-id="5d28c-163">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="5d28c-164">Office 365 PowerShell로 Office 365 관리</span><span class="sxs-lookup"><span data-stu-id="5d28c-164">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)

