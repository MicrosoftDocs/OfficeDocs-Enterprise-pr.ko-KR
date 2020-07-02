---
title: DAP (위임 된 액세스 권한) 파트너에 대해 Windows PowerShell을 사용 하 여 Microsoft 365 테 넌 트 관리
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- M365-subscription-management
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: f92d5116-5b66-4150-ad20-1452fc3dd712
description: '요약: Microsoft 365 용 Windows PowerShell을 사용 하 여 고객 테 넌 트를 관리 합니다.'
ms.openlocfilehash: a57f66ec02f5ba69006c17a9cf734e622017b8fb
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998234"
---
# <a name="manage-microsoft-365-tenants-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="80a05-103">DAP (위임 된 액세스 권한) 파트너에 대해 Windows PowerShell을 사용 하 여 Microsoft 365 테 넌 트 관리</span><span class="sxs-lookup"><span data-stu-id="80a05-103">Manage Microsoft 365 tenants with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

<span data-ttu-id="80a05-104">Windows PowerShell을 사용 하면 배포 및 CSP (클라우드 솔루션 공급자) 파트너가 Microsoft 365 관리 센터에서 사용할 수 없는 고객 테 넌 트 설정을 쉽게 관리 하 고 보고할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80a05-104">Windows PowerShell allows Syndication and Cloud Solution Provider (CSP) partners to easily administer and report on customer tenancy settings that are not available in the Microsoft 365 admin center.</span></span> <span data-ttu-id="80a05-105">AOBO(관리 위임자) 권한은 파트너 관리자 계정에서 고객 테넌트에 연결하는 데 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="80a05-105">Note that Administer on Behalf Of (AOBO) permissions are required for the partner administrator account to connect to its customer tenancies.</span></span>
  
<span data-ttu-id="80a05-106">DAP(위임된 액세스 권한) 파트너는 Syndication 및 CSP(클라우드 솔루션 공급자) 파트너입니다.</span><span class="sxs-lookup"><span data-stu-id="80a05-106">Delegated Access Permission (DAP) partners are Syndication and Cloud Solution Providers (CSP) Partners.</span></span> <span data-ttu-id="80a05-107">이러한 공급자는 다른 회사의 네트워크 또는 전자 통신 공급자인 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="80a05-107">They are frequently network or telecom providers to other companies.</span></span> <span data-ttu-id="80a05-108">Microsoft 365 구독을 고객에 게 서비스 제공으로 번들 합니다.</span><span class="sxs-lookup"><span data-stu-id="80a05-108">They bundle Microsoft 365 subscriptions into their service offerings to their customers.</span></span> <span data-ttu-id="80a05-109">Microsoft 365 구독을 판매할 때 고객 테 넌 트에 대 한 관리 및 보고를 수행할 수 있도록 사용자에 게 테 넌 트에 대 한 "대신 (AOBO) 사용 권한을 자동으로 부여 합니다.</span><span class="sxs-lookup"><span data-stu-id="80a05-109">When they sell a Microsoft 365 subscription, they are automatically granted Administer On Behalf Of (AOBO) permissions to the customer tenancies so they can administer and report on the customer tenancies.</span></span>
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="80a05-110">시작하기 전에 알아야 할 내용</span><span class="sxs-lookup"><span data-stu-id="80a05-110">What do you need to know before you begin?</span></span>

<span data-ttu-id="80a05-111">The procedures in this topic require you to connect to Windows PowerShell for Office 365.</span><span class="sxs-lookup"><span data-stu-id="80a05-111">The procedures in this topic require you to connect to Windows PowerShell for Office 365.</span></span> <span data-ttu-id="80a05-112">For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="80a05-112">For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
<span data-ttu-id="80a05-113">파트너 테넌트 관리자 자격 증명도 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="80a05-113">You also need your partner tenant administrator credentials.</span></span>
  
## <a name="what-do-you-want-to-do"></a><span data-ttu-id="80a05-114">무슨 작업을 하고 싶으십니까?</span><span class="sxs-lookup"><span data-stu-id="80a05-114">What do you want to do?</span></span>

### <a name="list-all-tenant-ids"></a><span data-ttu-id="80a05-115">모든 테넌트 ID 나열</span><span class="sxs-lookup"><span data-stu-id="80a05-115">List all tenant IDs</span></span>

> [!NOTE]
> <span data-ttu-id="80a05-116">If you have more than 500 tenants, scope the cmdlet syntax with either  _-All_ or _-MaxResultsParameter_.</span><span class="sxs-lookup"><span data-stu-id="80a05-116">If you have more than 500 tenants, scope the cmdlet syntax with either  _-All_ or _-MaxResultsParameter_.</span></span> <span data-ttu-id="80a05-117">This applies to other cmdlets that can give a large output, such as **Get-MsolUser**.</span><span class="sxs-lookup"><span data-stu-id="80a05-117">This applies to other cmdlets that can give a large output, such as **Get-MsolUser**.</span></span>
  
<span data-ttu-id="80a05-118">액세스 권한이 있는 모든 고객의 테넌트 ID를 나열하려면 이 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="80a05-118">To list all customer tenant Ids that you have access to, run this command.</span></span>
  
```
Get-MsolPartnerContract -All | Select-Object TenantId
```

<span data-ttu-id="80a05-119">그러면 **TenantId** 별로 모든 고객 테넌트 목록이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="80a05-119">This will display a listing of all your customer tenants by **TenantId**.</span></span>

>[!Note]
><span data-ttu-id="80a05-120">PowerShell Core는 Windows PowerShell용 Microsoft Azure Active Directory 모듈 및 이름에 **Msol**이 있는 cmdlet을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="80a05-120">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="80a05-121">이러한 cmdlet을 계속 사용하려면 Windows PowerShell에서 이를 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="80a05-121">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>
  
### <a name="get-a-tenant-id-by-using-the-domain-name"></a><span data-ttu-id="80a05-122">도메인 이름을 사용하여 테넌트 ID 받기</span><span class="sxs-lookup"><span data-stu-id="80a05-122">Get a tenant ID by using the domain name</span></span>

<span data-ttu-id="80a05-123">To get the **TenantId** for a specific customer tenant by domain name, run this command.</span><span class="sxs-lookup"><span data-stu-id="80a05-123">To get the **TenantId** for a specific customer tenant by domain name, run this command.</span></span> <span data-ttu-id="80a05-124">Replace _<domainname.onmicrosoft.com>_ with the actual domain name of the customer tenant that you want.</span><span class="sxs-lookup"><span data-stu-id="80a05-124">Replace _<domainname.onmicrosoft.com>_ with the actual domain name of the customer tenant that you want.</span></span>
  
```
Get-MsolPartnerContract -DomainName <domainname.onmicrosoft.com> | Select-Object TenantId
```

### <a name="list-all-domains-for-a-tenant"></a><span data-ttu-id="80a05-125">테넌트에 대한 모든 도메인 나열</span><span class="sxs-lookup"><span data-stu-id="80a05-125">List all domains for a tenant</span></span>

<span data-ttu-id="80a05-126">To get all domains for any one customer tenant, run this command.</span><span class="sxs-lookup"><span data-stu-id="80a05-126">To get all domains for any one customer tenant, run this command.</span></span> <span data-ttu-id="80a05-127">Replace  _<customer TenantId value>_ with the actual value.</span><span class="sxs-lookup"><span data-stu-id="80a05-127">Replace  _<customer TenantId value>_ with the actual value.</span></span>
  
```
Get-MsolDomain -TenantId <customer TenantId value>
```

<span data-ttu-id="80a05-128">추가 도메인을 등록한 경우 고객 **TenantId** 와 관련된 모든 도메인이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="80a05-128">If you have registered additional domains, this will return all domains associated with the customer **TenantId**.</span></span>
  
### <a name="get-a-mapping-of-all-tenants-and-registered-domains"></a><span data-ttu-id="80a05-129">모든 테넌트 및 등록된 도메인의 매핑 가져오기</span><span class="sxs-lookup"><span data-stu-id="80a05-129">Get a mapping of all tenants and registered domains</span></span>

<span data-ttu-id="80a05-130">The previous Windows PowerShell for Office 365 commands showed you how to retrieve either tenant IDs or domains but not both at the same time, and with no clear mapping between them all.</span><span class="sxs-lookup"><span data-stu-id="80a05-130">The previous Windows PowerShell for Office 365 commands showed you how to retrieve either tenant IDs or domains but not both at the same time, and with no clear mapping between them all.</span></span> <span data-ttu-id="80a05-131">This command generates a listing of all your customer tenant IDs and their domains.</span><span class="sxs-lookup"><span data-stu-id="80a05-131">This command generates a listing of all your customer tenant IDs and their domains.</span></span>
  
```
$Tenants = Get-MsolPartnerContract -All; $Tenants | foreach {$Domains = $_.TenantId; Get-MsolDomain -TenantId $Domains | fl @{Label="TenantId";Expression={$Domains}},name}
```

### <a name="get-all-users-for-a-tenant"></a><span data-ttu-id="80a05-132">테넌트에 대한 모든 사용자 가져오기</span><span class="sxs-lookup"><span data-stu-id="80a05-132">Get all users for a tenant</span></span>

<span data-ttu-id="80a05-133">This will display the **UserPrincipalName**, the **DisplayName**, and the **isLicensed** status for all users for a particular tenant.</span><span class="sxs-lookup"><span data-stu-id="80a05-133">This will display the **UserPrincipalName**, the **DisplayName**, and the **isLicensed** status for all users for a particular tenant.</span></span> <span data-ttu-id="80a05-134">Replace _<customer TenantId value>_ with the actual value.</span><span class="sxs-lookup"><span data-stu-id="80a05-134">Replace _<customer TenantId value>_ with the actual value.</span></span>
  
```
Get-MsolUser -TenantID <customer TenantId value>
```

### <a name="get-all-details-about-a-user"></a><span data-ttu-id="80a05-135">사용자에 대한 모든 세부 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="80a05-135">Get all details about a user</span></span>

<span data-ttu-id="80a05-136">If you want to see all the properties of a particular user, run this command.</span><span class="sxs-lookup"><span data-stu-id="80a05-136">If you want to see all the properties of a particular user, run this command.</span></span> <span data-ttu-id="80a05-137">Replace  _<customer TenantId value>_ and _<user principal name value>_ with the actual values.</span><span class="sxs-lookup"><span data-stu-id="80a05-137">Replace  _<customer TenantId value>_ and _<user principal name value>_ with the actual values.</span></span>
  
```
Get-MsolUser -TenantId <customer TenantId value> -UserPrincipalName <user principal name value>
```

### <a name="add-users-set-options-and-assign-licenses"></a><span data-ttu-id="80a05-138">사용자 추가, 옵션 설정 및 라이선스 할당</span><span class="sxs-lookup"><span data-stu-id="80a05-138">Add users, set options, and assign licenses</span></span>

<span data-ttu-id="80a05-139">Microsoft 365 사용자의 대량 생성, 구성 및 라이선스는 특히 Office 365 용 Windows PowerShell을 사용 하 여 효율적으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80a05-139">The bulk creation, configuration, and licensing of Microsoft 365 users is particularly efficient by using Windows PowerShell for Office 365.</span></span> <span data-ttu-id="80a05-140">이 2단계 프로세스에서 먼저 쉼표로 구분된 값(CSV) 파일에 추가하려는 모든 사용자에 대한 항목을 만든 다음 Office 365용 Windows PowerShell을 사용하여 해당 파일을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="80a05-140">In this two-step process, you first create entries for all the users you want to add in a comma-separated value (CSV) file and then import that file by using Windows PowerShell for Office 365.</span></span> 
  
#### <a name="create-a-csv-file"></a><span data-ttu-id="80a05-141">CSV 파일 만들기</span><span class="sxs-lookup"><span data-stu-id="80a05-141">Create a CSV file</span></span>

<span data-ttu-id="80a05-142">다음 형식을 사용하여 CSV 파일 만들기</span><span class="sxs-lookup"><span data-stu-id="80a05-142">Create a CSV file by using this format:</span></span>
  
-  `UserPrincipalName,FirstName,LastName,DisplayName,Password,TenantId,UsageLocation,LicenseAssignment`
    
<span data-ttu-id="80a05-143">여기서 각 부분이 나타내는 의미는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="80a05-143">where:</span></span>
  
- <span data-ttu-id="80a05-144">**UsageLocation**: The value for this is the two-letter ISO country/region code of the user.</span><span class="sxs-lookup"><span data-stu-id="80a05-144">**UsageLocation**: The value for this is the two-letter ISO country/region code of the user.</span></span> <span data-ttu-id="80a05-145">The country/region codes can be looked up at the[ISO Online Browsing Platform](https://go.microsoft.com/fwlink/p/?LinkId=532703).</span><span class="sxs-lookup"><span data-stu-id="80a05-145">The country/region codes can be looked up at the[ISO Online Browsing Platform](https://go.microsoft.com/fwlink/p/?LinkId=532703).</span></span> <span data-ttu-id="80a05-146">For example, the code for the United States is US, and the code for Brazil is BR.</span><span class="sxs-lookup"><span data-stu-id="80a05-146">For example, the code for the United States is US, and the code for Brazil is BR.</span></span> 
    
- <span data-ttu-id="80a05-147">**LicenseAssignment**: The value for this uses this format: `syndication-account:<PROVISIONING_ID>`.</span><span class="sxs-lookup"><span data-stu-id="80a05-147">**LicenseAssignment**: The value for this uses this format: `syndication-account:<PROVISIONING_ID>`.</span></span> <span data-ttu-id="80a05-148">For example, if you are assigning customer tenant users O365_Business_Premium licenses, the **LicenseAssignment** value looks like this: **syndication-account:O365_Business_Premium**.</span><span class="sxs-lookup"><span data-stu-id="80a05-148">For example, if you are assigning customer tenant users O365_Business_Premium licenses, the **LicenseAssignment** value looks like this: **syndication-account:O365_Business_Premium**.</span></span> <span data-ttu-id="80a05-149">You will find the PROVISIONING_IDs in the Syndication Partner Portal that you have access to as a Syndication or CSP partner.</span><span class="sxs-lookup"><span data-stu-id="80a05-149">You will find the PROVISIONING_IDs in the Syndication Partner Portal that you have access to as a Syndication or CSP partner.</span></span>
    
#### <a name="import-the-csv-file-and-create-the-users"></a><span data-ttu-id="80a05-150">CSV 파일 가져오기 및 사용자 만들기</span><span class="sxs-lookup"><span data-stu-id="80a05-150">Import the CSV file and create the users</span></span>

<span data-ttu-id="80a05-151">After you have your CSV file created, run this command to create user accounts with non-expiring passwords that the user must change at first sign-in and that assigns the license you specify.</span><span class="sxs-lookup"><span data-stu-id="80a05-151">After you have your CSV file created, run this command to create user accounts with non-expiring passwords that the user must change at first sign-in and that assigns the license you specify.</span></span> <span data-ttu-id="80a05-152">Be sure to substitute the correct CSV file name.</span><span class="sxs-lookup"><span data-stu-id="80a05-152">Be sure to substitute the correct CSV file name.</span></span>
  
```
Import-Csv .\FILENAME.CSV | foreach {New-MsolUser -UserPrincipalName $_.UserPrincipalName -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -Password $_.Password -UsageLocation $_.UsageLocation -LicenseAssignment $_.LicenseAssignment -ForceChangePassword:$true -PasswordNeverExpires:$true -TenantId $_.TenantId}
```

## <a name="see-also"></a><span data-ttu-id="80a05-153">참고 항목</span><span class="sxs-lookup"><span data-stu-id="80a05-153">See also</span></span>

#### 

[<span data-ttu-id="80a05-154">파트너를 위한 도움말</span><span class="sxs-lookup"><span data-stu-id="80a05-154">Help for partners</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=533477)

