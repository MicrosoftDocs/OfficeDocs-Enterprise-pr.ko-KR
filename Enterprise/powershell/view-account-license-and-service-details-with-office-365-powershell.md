---
title: PowerShell을 사용 하 여 Microsoft 365 계정 라이선스 및 서비스 세부 정보 보기
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
- PowerShell
- Ent_Office_Other
- LIL_Placement
ms.assetid: ace07d8a-15ca-4b89-87f0-abbce809b519
description: PowerShell을 사용 하 여 사용자에 게 할당 된 Microsoft 365 서비스를 확인 하는 방법에 대해 설명 합니다.
ms.openlocfilehash: 73af2fd40df8b36507250edcef48359e9d555a7f
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230244"
---
# <a name="view-microsoft-365-account-license-and-service-details-with-powershell"></a><span data-ttu-id="dbd17-103">PowerShell을 사용 하 여 Microsoft 365 계정 라이선스 및 서비스 세부 정보 보기</span><span class="sxs-lookup"><span data-stu-id="dbd17-103">View Microsoft 365 account license and service details with PowerShell</span></span>

<span data-ttu-id="dbd17-104">*이 문서는 Microsoft 365 Enterprise 및 Office 365 Enterprise에 모두 적용 됩니다.*</span><span class="sxs-lookup"><span data-stu-id="dbd17-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="dbd17-105">Microsoft 365에서는 라이선스 요금제 (Sku 또는 Microsoft 365 요금제 라고도 함)의 라이선스를 사용자에 게 해당 요금제에 대해 정의 된 Microsoft 365 서비스에 대 한 액세스 권한을 부여 합니다.</span><span class="sxs-lookup"><span data-stu-id="dbd17-105">In Microsoft 365, licenses from licensing plans (also called SKUs or Microsoft 365 plans) give users access to the Microsoft 365 services that are defined for those plans.</span></span> <span data-ttu-id="dbd17-106">그러나 사용자는 현재 할당된 라이선스에서 사용할 수 있는 모든 서비스에 액세스하지 못할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dbd17-106">However, a user might not have access to all the services that are available in a license that's currently assigned to them.</span></span> <span data-ttu-id="dbd17-107">Microsoft 365 용 PowerShell을 사용 하 여 사용자 계정에 대 한 서비스 상태를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dbd17-107">You can use PowerShell for Microsoft 365 to view the status of services on user accounts.</span></span> 

<span data-ttu-id="dbd17-108">라이선스 계획, 라이선스 및 서비스에 대 한 자세한 내용은 PowerShell을 [사용 하 여 라이선스 및 서비스 보기](view-licenses-and-services-with-office-365-powershell.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="dbd17-108">For more information about licensing plans, license, and services, see [View licenses and services with PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="dbd17-109">Graph 모듈용 Azure Active Directory PowerShell 사용하기</span><span class="sxs-lookup"><span data-stu-id="dbd17-109">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="dbd17-110">먼저 [Microsoft 365 테 넌 트에 연결](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)합니다.</span><span class="sxs-lookup"><span data-stu-id="dbd17-110">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
<span data-ttu-id="dbd17-111">그런 다음이 명령을 사용 하 여 테 넌 트에 대 한 라이선스 계획을 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="dbd17-111">Next, list the license plans for your tenant with this command.</span></span>

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="dbd17-112">이러한 명령을 사용 하 여 각 라이선스 계획에서 사용할 수 있는 서비스를 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="dbd17-112">Use these commands to list the services that are available in each licensing plan.</span></span>

```powershell
$allSKUs=Get-AzureADSubscribedSku
$licArray = @()
for($i = 0; $i -lt $allSKUs.Count; $i++)
{
$licArray += "Service Plan: " + $allSKUs[$i].SkuPartNumber
$licArray +=  Get-AzureADSubscribedSku -ObjectID $allSKUs[$i].ObjectID | Select -ExpandProperty ServicePlans
$licArray +=  ""
}
$licArray
```

<span data-ttu-id="dbd17-113">이러한 명령을 사용 하 여 사용자 계정에 할당 된 라이선스를 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="dbd17-113">Use these commands to list the licenses that are assigned to a user account.</span></span>

```powershell
$userUPN="<user account UPN, such as belindan@contoso.com>"
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="dbd17-114">Windows PowerShell용 Microsoft Azure Active Directory 모듈 사용하기</span><span class="sxs-lookup"><span data-stu-id="dbd17-114">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="dbd17-115">먼저 [Microsoft 365 테 넌 트에 연결](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)합니다.</span><span class="sxs-lookup"><span data-stu-id="dbd17-115">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="dbd17-116">다음으로이 명령을 실행 하 여 조직에서 사용할 수 있는 라이선스 계획을 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="dbd17-116">Next, run this command to list the licensing plans that are available in your organization.</span></span> 

```powershell
Get-MsolAccountSku
```
>[!Note]
><span data-ttu-id="dbd17-117">PowerShell Core는 Windows PowerShell용 Microsoft Azure Active Directory 모듈 및 이름에 **Msol**이 있는 cmdlet을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dbd17-117">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="dbd17-118">이러한 cmdlet을 계속 사용하려면 Windows PowerShell에서 이를 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dbd17-118">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="dbd17-119">다음으로, 각 라이선스 계획에서 사용할 수 있는 서비스와 이러한 서비스가 나열 되는 순서 (인덱스 번호)를 나열 하려면이 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="dbd17-119">Next, run this command to list the services that are available in each licensing plan, and the order in which they are listed (the index number).</span></span>

```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```
  
<span data-ttu-id="dbd17-120">이 명령을 사용 하 여 사용자에 게 할당 된 라이선스와 해당 라이선스가 나열 되는 순서 (인덱스 번호)를 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="dbd17-120">Use this command to list the licenses that are assigned to a user, and the order in which they are listed (the index number).</span></span>

```powershell
Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses
```

### <a name="to-view-services-for-a-user-account"></a><span data-ttu-id="dbd17-121">사용자 계정에 대 한 서비스를 보려면</span><span class="sxs-lookup"><span data-stu-id="dbd17-121">To view services for a user account</span></span>

<span data-ttu-id="dbd17-122">사용자가 액세스할 수 있는 Microsoft 365 서비스를 모두 보려면 다음 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="dbd17-122">To view all the Microsoft 365 services that a user has access to, use the following syntax:</span></span>
  
```powershell
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

<span data-ttu-id="dbd17-123">이 예에서는 사용자 BelindaN@litwareinc.com에 게 액세스 권한이 있는 서비스를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="dbd17-123">This example shows the services to which the user BelindaN@litwareinc.com has access.</span></span> <span data-ttu-id="dbd17-124">사용자의 계정에 할당된 모든 라이선스와 관련된 서비스를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="dbd17-124">This shows the services that are associated with all licenses that are assigned to her account.</span></span>
  
```powershell
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

<span data-ttu-id="dbd17-125">이 예제에서는 사용자 BelindaN@litwareinc.com이 계정에 할당된 첫 번째 라이선스(인덱스 번호: 0)에서 액세스할 수 있는 서비스를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="dbd17-125">This example shows the services that user BelindaN@litwareinc.com has access to from the first license that's assigned to her account (the index number is 0).</span></span>
  
```powershell
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

<span data-ttu-id="dbd17-126">*여러 라이선스가*할당 된 사용자의 모든 서비스를 보려면 다음 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="dbd17-126">To view all the services for a user who has been assigned *multiple licenses*, use the following syntax:</span></span>

```powershell
$userUPN="<user account UPN>"
$AllLicenses=(Get-MsolUser -UserPrincipalName $userUPN).Licenses
$licArray = @()
for($i = 0; $i -lt $AllLicenses.Count; $i++)
{
$licArray += "License: " + $AllLicenses[$i].AccountSkuId
$licArray +=  $AllLicenses[$i].ServiceStatus
$licArray +=  ""
}
$licArray
```
 
## <a name="see-also"></a><span data-ttu-id="dbd17-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="dbd17-127">See also</span></span>

[<span data-ttu-id="dbd17-128">PowerShell을 사용 하 여 Microsoft 365 사용자 계정, 라이선스 및 그룹 관리</span><span class="sxs-lookup"><span data-stu-id="dbd17-128">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="dbd17-129">PowerShell을 사용 하 여 Microsoft 365 관리</span><span class="sxs-lookup"><span data-stu-id="dbd17-129">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="dbd17-130">Microsoft 365 용 PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="dbd17-130">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)
