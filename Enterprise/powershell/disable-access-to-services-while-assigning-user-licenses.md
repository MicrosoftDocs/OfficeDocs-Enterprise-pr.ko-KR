---
title: 사용자 라이선스를 할당하는 동안 서비스에 대한 액세스 사용 안 함
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 09/27/2019
audience: Admin
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-administration
localization_priority: Normal
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: bb003bdb-3c22-4141-ae3b-f0656fc23b9c
description: Office 365 PowerShell을 사용 하 여 사용자 계정에 라이선스를 할당 하 고 한 번에 특정 서비스 계획을 사용 하지 않도록 설정 하는 방법을 알아봅니다.
ms.openlocfilehash: 06b6de4ea6d96dd2c9510770042bd2a2f1260876
ms.sourcegitcommit: 4b057db053e93b0165f1ec6c4799cff4c2852566
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/25/2019
ms.locfileid: "39257397"
---
# <a name="disable-access-to-services-while-assigning-user-licenses"></a><span data-ttu-id="7cf69-103">사용자 라이선스를 할당하는 동안 서비스에 대한 액세스 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="7cf69-103">Disable access to services while assigning user licenses</span></span>

<span data-ttu-id="7cf69-104">Office 365 구독에는 개별 서비스에 대 한 서비스 계획이 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7cf69-104">Office 365 subscriptions come with service plans for individual services.</span></span> <span data-ttu-id="7cf69-105">Office 365 관리자가 사용자에 게 라이선스를 할당할 때 특정 요금제를 사용 하지 않도록 설정 해야 하는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7cf69-105">Office 365 administrators often need to disable certain plans when assigning licenses to users.</span></span> <span data-ttu-id="7cf69-106">이 문서의 지침을 사용 하 여 개별 사용자 계정 또는 여러 사용자 계정에 대해 PowerShell을 사용 하 여 특정 서비스 계획을 사용 하지 않도록 설정 하는 동안 Office 365 라이선스를 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7cf69-106">With the instructions in this article, you can assign an Office 365 license while disabling specific service plans using PowerShell for an individual user account or multiple user accounts.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="7cf69-107">Graph 모듈용 Azure Active Directory PowerShell 사용하기</span><span class="sxs-lookup"><span data-stu-id="7cf69-107">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="7cf69-108">먼저, [Office 365 테넌트에 연결](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf69-108">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  

<span data-ttu-id="7cf69-109">그런 다음이 명령을 사용 하 여 테 넌 트에 대 한 라이선스 계획을 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf69-109">Next, list the license plans for your tenant with this command.</span></span>

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="7cf69-110">다음으로, UPN (사용자 계정 이름)이 라고도 하는 라이선스를 추가할 계정의 로그인 이름을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="7cf69-110">Next, get the sign-in name of the account to which you want add a license, also known as the user principal name (UPN).</span></span>

<span data-ttu-id="7cf69-111">그런 다음 서비스 목록을 컴파일하여 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf69-111">Next, compile a list of services to enable.</span></span> <span data-ttu-id="7cf69-112">라이선스 계획의 전체 목록 (제품 이름), 포함 된 서비스 계획 및 해당 하는 이름에 대 한 자세한 내용은 [product name and service plan identifier for license](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="7cf69-112">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>

<span data-ttu-id="7cf69-113">아래 명령 블록에 대해 사용자 계정 이름, SKU 부품 번호 및 서비스 계획 목록을 입력 하 여 설명 텍스트와 > \< 및 문자를 사용 하도록 설정 하 고 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf69-113">For the command block below, fill in the user principal name of the user account, the SKU part number, and the list of service plans to enable and remove the explanatory text and the \< and > characters.</span></span> <span data-ttu-id="7cf69-114">그런 다음 PowerShell 명령 프롬프트에서 결과 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf69-114">Then, run the resulting commands at the PowerShell command prompt.</span></span>
  
```powershell
$userUPN="<user account UPN>"
$skuPart="<SKU part number>"
$serviceList=<double-quoted enclosed, comma-separated list of enabled services>
$user = Get-AzureADUser -ObjectID $userUPN
$skuID= (Get-AzureADSubscribedSku  | Where {$_.SkuPartNumber -eq $skuPart}).SkuID
$SkuFeaturesToEnable = @($serviceList)
$StandardLicense = Get-AzureADSubscribedSku | Where {$_.SkuId -eq $skuID}
$SkuFeaturesToDisable = $StandardLicense.ServicePlans | ForEach-Object { $_ | Where {$_.ServicePlanName -notin $SkuFeaturesToEnable }}
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = $StandardLicense.SkuId
$License.DisabledPlans = $SkuFeaturesToDisable.ServicePlanId
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $user.ObjectId -AssignedLicenses $LicensesToAssign
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="7cf69-115">Windows PowerShell용 Microsoft Azure Active Directory 모듈 사용하기</span><span class="sxs-lookup"><span data-stu-id="7cf69-115">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="7cf69-116">먼저, [Office 365 테넌트에 연결](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf69-116">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="7cf69-117">다음으로, 다음 명령을 실행 하 여 현재 구독을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf69-117">Next, run this command to see your current subscriptions:</span></span>
  
```powershell
Get-MsolAccountSku
```

>[!Note]
><span data-ttu-id="7cf69-118">PowerShell Core에서는 이름에 **Msol** 이 포함 된 Windows powershell 모듈 및 cmdlet에 대 한 Microsoft Azure Active Directory 모듈을 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7cf69-118">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="7cf69-119">이러한 cmdlet을 계속 사용 하려면 Windows PowerShell에서 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf69-119">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="7cf69-120">`Get-MsolAccountSku` 명령 표시에서 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf69-120">In the display of the  `Get-MsolAccountSku` command:</span></span>
  
- <span data-ttu-id="7cf69-121">**AccountSkuId** 은 OrganizationName>에서 \<\<구독> 형식으로 조직에 대 한 구독입니다.</span><span class="sxs-lookup"><span data-stu-id="7cf69-121">**AccountSkuId** is a subscription for your organization in \<OrganizationName>:\<Subscription> format.</span></span> <span data-ttu-id="7cf69-122">\<OrganizationName>는 Office 365에서 등록할 때 입력 한 값으로, 조직에서 고유 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf69-122">The \<OrganizationName> is the value that you provided when you enrolled in Office 365, and is unique for your organization.</span></span> <span data-ttu-id="7cf69-123">\<구독> 값은 특정 구독의 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7cf69-123">The \<Subscription> value is for a specific subscription.</span></span> <span data-ttu-id="7cf69-124">예를 들어 litwareinc: ENTERPRISEPACK의 경우 조직 이름은 litwareinc이 고 구독 이름은 ENTERPRISEPACK (Office 365 Enterprise E3)입니다.</span><span class="sxs-lookup"><span data-stu-id="7cf69-124">For example, for litwareinc:ENTERPRISEPACK, the organization name is litwareinc, and the subscription name is ENTERPRISEPACK (Office 365 Enterprise E3).</span></span>
    
- <span data-ttu-id="7cf69-125">**Activeunits** 는 구독을 위해 구매한 라이선스 수입니다.</span><span class="sxs-lookup"><span data-stu-id="7cf69-125">**ActiveUnits** is the number of licenses that you've purchased for the subscription.</span></span>
    
- <span data-ttu-id="7cf69-126">**WarningUnits** 은 갱신 되지 않고 30 일 유예 기간 후에 만료 되는 구독의 라이선스 수입니다.</span><span class="sxs-lookup"><span data-stu-id="7cf69-126">**WarningUnits** is the number of licenses in a subscription that you haven't renewed, and that will expire after the 30-day grace period.</span></span>
    
- <span data-ttu-id="7cf69-127">**ConsumedUnits** 은 구독에 대해 사용자에 게 할당 한 라이선스 수입니다.</span><span class="sxs-lookup"><span data-stu-id="7cf69-127">**ConsumedUnits** is the number of licenses that you've assigned to users for the subscription.</span></span>
    
<span data-ttu-id="7cf69-128">라이선스를 부여할 사용자가 포함 된 Office 365 구독에 대 한 AccountSkuId를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf69-128">Note the AccountSkuId for your Office 365 subscription that contains the users you want to license.</span></span> <span data-ttu-id="7cf69-129">또한 할당 하기에 충분 한 라이선스가 있는지 확인 하세요 ( **Activeunits** 에서 **ConsumedUnits** 빼기).</span><span class="sxs-lookup"><span data-stu-id="7cf69-129">Also, ensure that there are enough licenses to assign (subtract **ConsumedUnits** from **ActiveUnits** ).</span></span>
  
<span data-ttu-id="7cf69-130">다음으로, 다음 명령을 실행 하 여 모든 구독에서 사용할 수 있는 Office 365 서비스 계획에 대 한 세부 정보를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf69-130">Next, run this command to see the details about the Office 365 service plans that are available in all your subscriptions:</span></span>
  
```powershell
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

<span data-ttu-id="7cf69-131">이 명령을 표시할 때 사용자에 게 라이선스를 할당할 때 사용 하지 않도록 설정할 서비스 계획을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf69-131">From the display of this command, determine which service plans you would like to disable when you assign licenses to users.</span></span>
  
<span data-ttu-id="7cf69-132">다음은 서비스 계획 및 해당 Office 365 서비스의 일부 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="7cf69-132">Here is a partial list of service plans and their corresponding Office 365 services.</span></span>

<span data-ttu-id="7cf69-133">다음 표에서는 가장 일반적인 서비스에 대 한 Office 365 서비스 계획 및 해당 이름을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7cf69-133">The following table shows the Office 365 service plans and their friendly names for the most common services.</span></span> <span data-ttu-id="7cf69-134">서비스 계획 목록이 다를 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7cf69-134">Your list of service plans might be different.</span></span> 
  
|<span data-ttu-id="7cf69-135">**서비스 계획**</span><span class="sxs-lookup"><span data-stu-id="7cf69-135">**Service plan**</span></span>|<span data-ttu-id="7cf69-136">**설명**</span><span class="sxs-lookup"><span data-stu-id="7cf69-136">**Description**</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="7cf69-137">Sway</span><span class="sxs-lookup"><span data-stu-id="7cf69-137">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="7cf69-138">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="7cf69-138">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="7cf69-139">Yammer</span><span class="sxs-lookup"><span data-stu-id="7cf69-139">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="7cf69-140">RMS(Azure 권한 관리)</span><span class="sxs-lookup"><span data-stu-id="7cf69-140">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="7cf69-141">Office Professional Plus</span><span class="sxs-lookup"><span data-stu-id="7cf69-141">Office Professional Plus</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="7cf69-142">비즈니스용 Skype Online</span><span class="sxs-lookup"><span data-stu-id="7cf69-142">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="7cf69-143">사무실</span><span class="sxs-lookup"><span data-stu-id="7cf69-143">Office</span></span>   <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="7cf69-144">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="7cf69-144">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="7cf69-145">Exchange Online 계획 2</span><span class="sxs-lookup"><span data-stu-id="7cf69-145">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="7cf69-146">라이선스 계획의 전체 목록 (제품 이름), 포함 된 서비스 계획 및 해당 하는 이름에 대 한 자세한 내용은 [product name and service plan identifier for license](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="7cf69-146">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>
   
<span data-ttu-id="7cf69-147">AccountSkuId 및 서비스 계획을 사용 하지 않도록 설정 했으므로 개별 사용자 또는 여러 사용자에 대해 라이선스를 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7cf69-147">Now that you have the AccountSkuId and the service plans to disable, you can assign licenses for an individual user or for multiple users.</span></span>
  
### <a name="for-a-single-user"></a><span data-ttu-id="7cf69-148">단일 사용자의 경우</span><span class="sxs-lookup"><span data-stu-id="7cf69-148">For a single user</span></span>

<span data-ttu-id="7cf69-149">단일 사용자에 대해 사용자 계정 이름, AccountSkuId 및 서비스 계획 목록을 입력 하 여 설명 텍스트 및 \< 및 > 문자를 사용 하지 않도록 설정 하 고 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf69-149">For a single user, fill in the user principal name of the user account, the AccountSkuId, and the list of service plans to disable and remove the explanatory text and the \< and > characters.</span></span> <span data-ttu-id="7cf69-150">그런 다음 PowerShell 명령 프롬프트에서 결과 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf69-150">Then, run the resulting commands at the PowerShell command prompt.</span></span>
  
```powershell
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

<span data-ttu-id="7cf69-151">다음은 contoso: ENTERPRISEPACK 라이선스에 대해 belindan@contoso.com 이라는 계정에 대 한 명령 블록이 며 사용 하지 않도록 설정할 서비스 계획은 RMS_S_ENTERPRISE, SWAY, INTUNE_O365 및 YAMMER_ENTERPRISE입니다.</span><span class="sxs-lookup"><span data-stu-id="7cf69-151">Here is an example command block for the account named belindan@contoso.com, for the contoso:ENTERPRISEPACK license, and the service plans to disable are RMS_S_ENTERPRISE, SWAY, INTUNE_O365, and YAMMER_ENTERPRISE:</span></span>
  
```powershell
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

### <a name="for-multiple-users"></a><span data-ttu-id="7cf69-152">여러 사용자의 경우</span><span class="sxs-lookup"><span data-stu-id="7cf69-152">For multiple users</span></span>

<span data-ttu-id="7cf69-153">여러 사용자에 대해이 관리 작업을 수행 하려면 UserPrincipalName 및 UsageLocation 필드를 포함 하는 쉼표로 구분 된 값 (CSV) 텍스트 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7cf69-153">To perform this administration task for multiple users, create a comma-separated value (CSV) text file that contains the UserPrincipalName and UsageLocation fields.</span></span> <span data-ttu-id="7cf69-154">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7cf69-154">Here is an example:</span></span>
  
```powershell
UserPrincipalName,UsageLocation
ClaudeL@contoso.onmicrosoft.com,FR
LynneB@contoso.onmicrosoft.com,US
ShawnM@contoso.onmicrosoft.com,US
```

<span data-ttu-id="7cf69-155">그런 다음 입력 및 출력 CSV 파일의 위치, 계정 SKU ID 및 서비스 계획 목록을 사용 하지 않도록 설정 하 고 PowerShell 명령 프롬프트에서 결과 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf69-155">Next, fill in the location of the input and output CSV files, the account SKU ID, and the list of service plans to disable, and then run the resulting commands at the PowerShell command prompt.</span></span>
  
```powershell
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
Set-MsolUserLicense -UserPrincipalName $upn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $upn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
Set-MsolUser -UserPrincipalName $upn -UsageLocation $usageLocation
$users | Get-MsolUser | Select UserPrincipalName, Islicensed,Usagelocation | Export-Csv $outFileName
}
```

<span data-ttu-id="7cf69-156">다음 PowerShell 명령 블록:</span><span class="sxs-lookup"><span data-stu-id="7cf69-156">This PowerShell command block:</span></span>
  
- <span data-ttu-id="7cf69-157">각 사용자의 사용자 이름을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf69-157">Displays the user principal name of each user.</span></span>
    
- <span data-ttu-id="7cf69-158">각 사용자에 대해 사용자 지정 된 라이선스를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf69-158">Assigns customized licenses to each user.</span></span>
    
- <span data-ttu-id="7cf69-159">처리 된 모든 사용자와 함께 CSV 파일을 만들고 해당 라이선스 상태를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf69-159">Creates a CSV file with all the users that were processed and shows their license status.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="7cf69-160">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7cf69-160">See also</span></span>

[<span data-ttu-id="7cf69-161">Office 365 PowerShell을 사용 하 여 서비스에 대 한 액세스를 비활성화 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf69-161">Disable access to services with Office 365 PowerShell</span></span>](disable-access-to-services-with-office-365-powershell.md)
  
[<span data-ttu-id="7cf69-162">Office 365 PowerShell을 사용하여 Sway에 대한 액세스 비활성화</span><span class="sxs-lookup"><span data-stu-id="7cf69-162">Disable access to Sway with Office 365 PowerShell</span></span>](disable-access-to-sway-with-office-365-powershell.md)
  
[<span data-ttu-id="7cf69-163">Office 365 PowerShell로 사용자 계정 및 라이선스 관리</span><span class="sxs-lookup"><span data-stu-id="7cf69-163">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="7cf69-164">Office 365 PowerShell로 Office 365 관리</span><span class="sxs-lookup"><span data-stu-id="7cf69-164">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)

