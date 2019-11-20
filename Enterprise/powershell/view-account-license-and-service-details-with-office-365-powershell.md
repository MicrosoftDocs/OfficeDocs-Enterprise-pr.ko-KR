---
title: Office 365 PowerShell을 사용 하 여 계정 라이센스와 서비스 정보 보기
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/13/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
ms.assetid: ace07d8a-15ca-4b89-87f0-abbce809b519
description: Office 365 PowerShell을 사용 하 여 사용자에 게 할당 된 Office 365 서비스를 확인 하는 방법에 대해 설명 합니다.
ms.openlocfilehash: 53668a69d72cdcbe912d550be2b9e571b7f6c0e0
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2019
ms.locfileid: "38747477"
---
# <a name="view-account-license-and-service-details-with-office-365-powershell"></a><span data-ttu-id="2c84f-103">Office 365 PowerShell을 사용 하 여 계정 라이센스와 서비스 정보 보기</span><span class="sxs-lookup"><span data-stu-id="2c84f-103">View account license and service details with Office 365 PowerShell</span></span>

<span data-ttu-id="2c84f-104">Office 365에서는 라이선스 요금제 (Sku 또는 Office 365 요금제 라고도 함)의 라이선스를 사용자에 게 해당 요금제에 대해 정의 된 Office 365 서비스에 대 한 액세스 권한을 부여 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c84f-104">In Office 365, licenses from licensing plans (also called SKUs or Office 365 plans) give users access to the Office 365 services that are defined for those plans.</span></span> <span data-ttu-id="2c84f-105">그러나 사용자는 현재 할당된 라이선스에서 사용할 수 있는 모든 서비스에 액세스하지 못할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c84f-105">However, a user might not have access to all the services that are available in a license that's currently assigned to them.</span></span> <span data-ttu-id="2c84f-106">Office 365 PowerShell을 사용 하 여 사용자 계정에 대 한 서비스 상태를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c84f-106">You can use Office 365 PowerShell to view the status of services on user accounts.</span></span> 

<span data-ttu-id="2c84f-107">라이선스 계획, 라이선스 및 서비스에 대 한 자세한 내용은 [Office 365 PowerShell을 사용 하 여 라이선스 및 서비스 보기](view-licenses-and-services-with-office-365-powershell.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2c84f-107">For more information about licensing plans, license, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="2c84f-108">Graph 모듈용 Azure Active Directory PowerShell 사용하기</span><span class="sxs-lookup"><span data-stu-id="2c84f-108">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="2c84f-109">먼저, [Office 365 테넌트에 연결](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)합니다.</span><span class="sxs-lookup"><span data-stu-id="2c84f-109">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
<span data-ttu-id="2c84f-110">그런 다음이 명령을 사용 하 여 테 넌 트에 대 한 라이선스 계획을 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c84f-110">Next, list the license plans for your tenant with this command.</span></span>

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="2c84f-111">이러한 명령을 사용 하 여 각 라이선스 계획에서 사용할 수 있는 서비스를 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c84f-111">Use these commands to list the services that are available in each licensing plan.</span></span>

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

<span data-ttu-id="2c84f-112">이러한 명령을 사용 하 여 사용자 계정에 할당 된 라이선스를 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c84f-112">Use these commands to list the licenses that are assigned to a user account.</span></span>

```powershell
$userUPN="<user account UPN, such as belindan@contoso.com>"
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="2c84f-113">Windows PowerShell용 Microsoft Azure Active Directory 모듈 사용하기</span><span class="sxs-lookup"><span data-stu-id="2c84f-113">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="2c84f-114">먼저, [Office 365 테넌트에 연결](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)합니다.</span><span class="sxs-lookup"><span data-stu-id="2c84f-114">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="2c84f-115">다음으로이 명령을 실행 하 여 조직에서 사용할 수 있는 라이선스 계획을 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c84f-115">Next, run this command to list the licensing plans that are available in your organization.</span></span> 

```powershell
Get-MsolAccountSku
```

<span data-ttu-id="2c84f-116">다음으로, 각 라이선스 계획에서 사용할 수 있는 서비스와 이러한 서비스가 나열 되는 순서 (인덱스 번호)를 나열 하려면이 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c84f-116">Next, run this command to list the services that are available in each licensing plan, and the order in which they are listed (the index number).</span></span>

```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus
```
  
<span data-ttu-id="2c84f-117">이 명령을 사용 하 여 사용자에 게 할당 된 라이선스와 해당 라이선스가 나열 되는 순서 (인덱스 번호)를 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c84f-117">Use this command to list the licenses that are assigned to a user, and the order in which they are listed (the index number).</span></span>

```powershell
Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses
```

>[!Note]
><span data-ttu-id="2c84f-118">사용 하는 경우는 **Get-MsolUser** cmdlet을 사용 하지 않고는 _All_ 매개 변수를 처음 500 개의 계정만 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c84f-118">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 accounts are returned.</span></span>
>
   

### <a name="to-view-services-for-a-user-account"></a><span data-ttu-id="2c84f-119">사용자 계정에 대 한 서비스를 보려면</span><span class="sxs-lookup"><span data-stu-id="2c84f-119">To view services for a user account</span></span>

<span data-ttu-id="2c84f-120">사용자가 액세스할 수 있는 모든 Office 365 서비스를 보려면 다음 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c84f-120">To view all the Office 365 services that a user has access to, use the following syntax:</span></span>
  
```powershell
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

<span data-ttu-id="2c84f-121">이 예에서는 사용자 BelindaN@litwareinc.com에 게 액세스 권한이 있는 서비스를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c84f-121">This example shows the services to which the user BelindaN@litwareinc.com has access.</span></span> <span data-ttu-id="2c84f-122">사용자의 계정에 할당된 모든 라이선스와 관련된 서비스를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="2c84f-122">This shows the services that are associated with all licenses that are assigned to her account.</span></span>
  
```powershell
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

<span data-ttu-id="2c84f-123">이 예제에서는 사용자 BelindaN@litwareinc.com이 계정에 할당된 첫 번째 라이선스(인덱스 번호: 0)에서 액세스할 수 있는 서비스를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="2c84f-123">This example shows the services that user BelindaN@litwareinc.com has access to from the first license that's assigned to her account (the index number is 0).</span></span>
  
```powershell
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

<span data-ttu-id="2c84f-124">*여러 라이선스가*할당 된 사용자의 모든 서비스를 보려면 다음 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c84f-124">To view all the services for a user who has been assigned *multiple licenses*, use the following syntax:</span></span>

```powershell
$userAccountUPN="<user account UPN>"
$AllLicenses=(Get-MsolUser -UserPrincipalName $userAccountUPN).Licenses
$licArray = @()
for($i = 0; $i -lt $AllLicenses.Count; $i++)
{
$licArray += "License: " + $AllLicenses[$i].AccountSkuId
$licArray +=  $AllLicenses[$i].ServiceStatus
$licArray +=  ""
}
$licArray
```

  
## <a name="new-to-office-365"></a><span data-ttu-id="2c84f-125">Office 365의 새로운 기능</span><span class="sxs-lookup"><span data-stu-id="2c84f-125">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a><span data-ttu-id="2c84f-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2c84f-126">See also</span></span>

[<span data-ttu-id="2c84f-127">Office 365 PowerShell로 사용자 계정 및 라이선스 관리</span><span class="sxs-lookup"><span data-stu-id="2c84f-127">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="2c84f-128">Office 365 PowerShell 사용한 Office 365 관리</span><span class="sxs-lookup"><span data-stu-id="2c84f-128">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="2c84f-129">Office 365 PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="2c84f-129">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
