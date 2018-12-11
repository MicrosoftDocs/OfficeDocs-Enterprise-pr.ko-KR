---
title: Office 365 PowerShell을 사용 하 여 계정 라이센스와 서비스 정보 보기
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/10/2018
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
ms.openlocfilehash: 5d575ea9e0b45ddc453b3b1c73bd53bf73adab2e
ms.sourcegitcommit: 16806849f373196797d65e63ced825d547aef956
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2018
ms.locfileid: "27213955"
---
# <a name="view-account-license-and-service-details-with-office-365-powershell"></a><span data-ttu-id="c0630-103">Office 365 PowerShell을 사용 하 여 계정 라이센스와 서비스 정보 보기</span><span class="sxs-lookup"><span data-stu-id="c0630-103">View account license and service details with Office 365 PowerShell</span></span>

<span data-ttu-id="c0630-104">**요약:** Office 365 PowerShell을 사용 하 여 사용자에 게 할당 된 Office 365 서비스를 확인 하는 방법에 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0630-104">**Summary:** Explains how to use Office 365 PowerShell to determine the Office 365 services that have been assigned to users.</span></span>
  
<span data-ttu-id="c0630-p101">Office 365에서 라이선스를 제공 계획 라이선스를 (또한 호출된 Sku 또는 Office 365 계획) 사용자가 이러한 계획에 대해 정의 된 Office 365 서비스에 액세스 권한을 부여 합니다. 그러나 사용자 자신에 게 현재 할당 된 라이선스에서 사용할 수 있는 모든 서비스에 대 한 액세스를 권한이 없는 합니다. Office 365 PowerShell을 사용 하 여 사용자 계정에서 서비스의 상태를 보려면 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0630-p101">In Office 365, licenses from licensing plans (also called SKUs or Office 365 plans) give users access to the Office 365 services that are defined for those plans. However, a user might not have access to all the services that are available in a license that's currently assigned to them. You can use Office 365 PowerShell to view the status of services on user accounts.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="c0630-108">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="c0630-108">Before you begin</span></span>

- <span data-ttu-id="c0630-p102">이 항목의 절차를 수행하려면 Office 365 PowerShell에 연결되어 있어야 합니다. 지침을 보려면 [PowerShell Office 365에 연결](connect-to-office-365-powershell.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c0630-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="c0630-111">명령을 사용 하 여 `Get-MsolAccountSku` 및 `(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus` 다음 정보를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0630-111">Use the commands  `Get-MsolAccountSku` and `(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus` to find the following information:</span></span>
    
  - <span data-ttu-id="c0630-112">조직에서 사용할 수 있는 라이선스 계획.</span><span class="sxs-lookup"><span data-stu-id="c0630-112">The licensing plans that are available in your organization.</span></span>
    
  - <span data-ttu-id="c0630-113">각 라이선스 계획에서 사용할 수 있는 서비스 및 서비스 나열 순서(인덱스 번호).</span><span class="sxs-lookup"><span data-stu-id="c0630-113">The services that are available in each licensing plan, and the order in which they are listed (the index number).</span></span>
    
     <span data-ttu-id="c0630-114">계획, 라이선스 및 서비스 라이선스에 대 한 자세한 내용은 [보기 라이선스 및 Office 365 PowerShell을 사용 하 여 서비스를](view-licenses-and-services-with-office-365-powershell.md)참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="c0630-114">For more information about licensing plans, license, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="c0630-115">명령을 사용 하 여 `Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses` (인덱스 번호)를 나열 된 자신이 하는 사용자 및 순서에 할당 된 라이선스를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0630-115">Use the command  `Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses` to find the licenses that are assigned to a user, and the order in which they are listed (the index number).</span></span>
    
- <span data-ttu-id="c0630-116">사용 하는 경우는 **Get-MsolUser** cmdlet을 사용 하지 않고는 _All_ 매개 변수를 처음 500 개의 계정만 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0630-116">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 accounts are returned.</span></span>
    

## <a name="to-view-services-for-a-user-account"></a><span data-ttu-id="c0630-117">사용자 계정에 대 한 서비스를 보려면</span><span class="sxs-lookup"><span data-stu-id="c0630-117">To view services for a user account</span></span>

<span data-ttu-id="c0630-118">사용자에 액세스할 수 있는 모든 Office 365 서비스를 보려면 다음 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0630-118">To view all the Office 365 services that a user has access to, use the following syntax:</span></span>
  
```
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

<span data-ttu-id="c0630-p103">이 예제에서는 BelindaN@litwareinc.com 사용자가 액세스할 수 있는 서비스입니다. 이 사용자 계정에 할당 된 모든 라이선스와 연결 된 서비스를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="c0630-p103">This example shows the services to which the user BelindaN@litwareinc.com has access. This shows the services that are associated with all licenses that are assigned to her account.</span></span>
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

<span data-ttu-id="c0630-121">이 예제에서는 사용자 BelindaN@litwareinc.com이 계정에 할당된 첫 번째 라이선스(인덱스 번호: 0)에서 액세스할 수 있는 서비스를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="c0630-121">This example shows the services that user BelindaN@litwareinc.com has access to from the first license that's assigned to her account (the index number is 0).</span></span>
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

<span data-ttu-id="c0630-122">*여러 라이선스*할당 된 사용자에 대 한 모든 서비스를 보려면 다음 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0630-122">To view all the services for a user who has been assigned *multiple licenses*, use the following syntax:</span></span>

```
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

  
## <a name="see-also"></a><span data-ttu-id="c0630-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c0630-123">See also</span></span>

<span data-ttu-id="c0630-124">Office 365 PowerShell을 사용 하여 사용자를 관리에 대하여 다음과 같은 추가 항목을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="c0630-124">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="c0630-125">Office 365 PowerShell을 사용 하 여 사용자 계정 만들기</span><span class="sxs-lookup"><span data-stu-id="c0630-125">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="c0630-126">삭제 한 사용자 계정 Office 365 PowerShell을 사용 하 여 복원 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0630-126">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="c0630-127">블록 사용자 계정 Office 365 PowerShell을 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="c0630-127">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="c0630-128">Office 365 PowerShell을 사용 하 여 사용자 계정에 라이선스를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0630-128">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="c0630-129">Office 365 PowerShell을 사용 하 여 사용자 계정에서 라이센스를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0630-129">Remove licenses from user accounts with Office 365 PowerShell</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="c0630-130">이 항목에서 사용된 cmdlet에 대한 자세한 내용은 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="c0630-130">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="c0630-131">ConvertTo Html</span><span class="sxs-lookup"><span data-stu-id="c0630-131">ConvertTo-Html</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113290)
    
- [<span data-ttu-id="c0630-132">Format-List</span><span class="sxs-lookup"><span data-stu-id="c0630-132">Format-List</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113302)
    
- [<span data-ttu-id="c0630-133">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="c0630-133">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="c0630-134">선택 개체</span><span class="sxs-lookup"><span data-stu-id="c0630-134">Select-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [<span data-ttu-id="c0630-135">Where-Object</span><span class="sxs-lookup"><span data-stu-id="c0630-135">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

  
## <a name="new-to-office-365"></a><span data-ttu-id="c0630-136">Office 365의 새로운 기능</span><span class="sxs-lookup"><span data-stu-id="c0630-136">New to Office 365?</span></span>


[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]