---
title: DAP(위임된 액세스 권한) 파트너용 Windows PowerShell을 사용하여 Office 365 테넌트 관리
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-subscription-management
ms.custom: ''
ms.assetid: f92d5116-5b66-4150-ad20-1452fc3dd712
description: 요약:Office 365에 대해 Windows PowerShell을 사용하여 고객 테넌트를 관리합니다.
ms.openlocfilehash: b38c1862a0cf2db4a751d1690686baeead8ae9ea
ms.sourcegitcommit: 1c97471f47e1869f6db684f280f9085b7c2ff59f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/18/2019
ms.locfileid: "35781858"
---
# <a name="manage-office-365-tenants-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="a519b-103">DAP(위임된 액세스 권한) 파트너용 Windows PowerShell을 사용하여 Office 365 테넌트 관리</span><span class="sxs-lookup"><span data-stu-id="a519b-103">Manage Office 365 tenants with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

 <span data-ttu-id="a519b-104">**요약:** Office 365에 대해 Windows PowerShell을 사용하여 고객 테넌트를 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="a519b-104">**Summary:** Use Windows PowerShell for Office 365 to manage your customer tenancies.</span></span>
  
<span data-ttu-id="a519b-105">Windows PowerShell을 사용 하면 배포 및 CSP (클라우드 솔루션 공급자) 파트너가 Microsoft 365 관리 센터에서 사용할 수 없는 고객 테 넌 트 설정을 쉽게 관리 하 고 보고할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a519b-105">Windows PowerShell allows Syndication and Cloud Solution Provider (CSP) partners to easily administer and report on customer tenancy settings that are not available in the Microsoft 365 admin center.</span></span> <span data-ttu-id="a519b-106">AOBO(관리 위임자) 권한은 파트너 관리자 계정에서 고객 테넌트에 연결하는 데 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="a519b-106">Note that Administer on Behalf Of (AOBO) permissions are required for the partner administrator account to connect to its customer tenancies.</span></span>
  
<span data-ttu-id="a519b-107">DAP(위임된 액세스 권한) 파트너는 Syndication 및 CSP(클라우드 솔루션 공급자) 파트너입니다.</span><span class="sxs-lookup"><span data-stu-id="a519b-107">Delegated Access Permission (DAP) partners are Syndication and Cloud Solution Providers (CSP) Partners.</span></span> <span data-ttu-id="a519b-108">이러한 공급자는 다른 회사의 네트워크 또는 전자 통신 공급자인 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="a519b-108">They are frequently network or telecom providers to other companies.</span></span> <span data-ttu-id="a519b-109">이러한 공급자는 서비스와 Office 365 구독을 통합해서 고객에게 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a519b-109">They bundle Office 365 subscriptions into their service offerings to their customers.</span></span> <span data-ttu-id="a519b-110">Office 365 구독을 판매하는 경우 고객 테넌트에 대한 AOBO(관리 위임자) 권한이 자동으로 부여되므로 고객 테넌트를 관리하고 보고할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a519b-110">When they sell an Office 365 subscription, they are automatically granted Administer On Behalf Of (AOBO) permissions to the customer tenancies so they can administer and report on the customer tenancies.</span></span>
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="a519b-111">시작하기 전에 알아야 할 내용</span><span class="sxs-lookup"><span data-stu-id="a519b-111">What do you need to know before you begin?</span></span>

<span data-ttu-id="a519b-p103">이 항목의 절차를 수행하려면 Windows PowerShell용 Office 365에 연결되어 있어야 합니다.지침을 보려면 [PowerShell Office 365에 연결](connect-to-office-365-powershell.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a519b-p103">The procedures in this topic require you to connect to Windows PowerShell for Office 365. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
<span data-ttu-id="a519b-114">파트너 테넌트 관리자 자격 증명도 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="a519b-114">You also need your partner tenant administrator credentials.</span></span>
  
## <a name="what-do-you-want-to-do"></a><span data-ttu-id="a519b-115">무슨 작업을 하고 싶으십니까?</span><span class="sxs-lookup"><span data-stu-id="a519b-115">What do you want to do?</span></span>

### <a name="list-all-tenant-ids"></a><span data-ttu-id="a519b-116">모든 테넌트 ID 나열</span><span class="sxs-lookup"><span data-stu-id="a519b-116">List all tenant IDs</span></span>

> [!NOTE]
> <span data-ttu-id="a519b-p104">테넌트가 500개 넘는 경우  _-All_ 또는 _-MaxResultsParameter_를 사용하여 cmdlet 구문의 범위를 지정합니다. 이는 **Get-MsolUser** 등의 대규모 출력을 제공할 수 있는 다른 cmdlet에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a519b-p104">If you have more than 500 tenants, scope the cmdlet syntax with either  _-All_ or _-MaxResultsParameter_. This applies to other cmdlets that can give a large output, such as **Get-MsolUser**.</span></span>
  
<span data-ttu-id="a519b-119">액세스 권한이 있는 모든 고객의 테넌트 ID를 나열하려면 이 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="a519b-119">To list all customer tenant Ids that you have access to, run this command.</span></span>
  
```
Get-MsolPartnerContract -All | Select-Object TenantId
```

<span data-ttu-id="a519b-120">그러면 **TenantId** 별로 모든 고객 테넌트 목록이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a519b-120">This will display a listing of all your customer tenants by **TenantId**.</span></span>
  
### <a name="get-a-tenant-id-by-using-the-domain-name"></a><span data-ttu-id="a519b-121">도메인 이름을 사용하여 테넌트 ID 받기</span><span class="sxs-lookup"><span data-stu-id="a519b-121">Get a tenant ID by using the domain name</span></span>

<span data-ttu-id="a519b-p105">도메인 이름별로 특정 고객 테넌트에 대한 **TenantId** 를 받으려면 이 명령을 실행합니다. _<domainname.onmicrosoft.com>_ 을 원하는 고객 테넌트의 실제 도메인 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="a519b-p105">To get the **TenantId** for a specific customer tenant by domain name, run this command. Replace _<domainname.onmicrosoft.com>_ with the actual domain name of the customer tenant that you want.</span></span>
  
```
Get-MsolPartnerContract -DomainName <domainname.onmicrosoft.com> | Select-Object TenantId
```

### <a name="list-all-domains-for-a-tenant"></a><span data-ttu-id="a519b-124">테넌트에 대한 모든 도메인 나열</span><span class="sxs-lookup"><span data-stu-id="a519b-124">List all domains for a tenant</span></span>

<span data-ttu-id="a519b-p106">고객 테넌트에 대한 모든 도메인을 받으려면 이 명령을 실행합니다. _<customer TenantId value>_ 을 실제 값으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="a519b-p106">To get all domains for any one customer tenant, run this command. Replace  _<customer TenantId value>_ with the actual value.</span></span>
  
```
Get-MsolDomain -TenantId <customer TenantId value>
```

<span data-ttu-id="a519b-127">추가 도메인을 등록한 경우 고객 **TenantId** 와 관련된 모든 도메인이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="a519b-127">If you have registered additional domains, this will return all domains associated with the customer **TenantId**.</span></span>
  
### <a name="get-a-mapping-of-all-tenants-and-registered-domains"></a><span data-ttu-id="a519b-128">모든 테넌트 및 등록된 도메인의 매핑 가져오기</span><span class="sxs-lookup"><span data-stu-id="a519b-128">Get a mapping of all tenants and registered domains</span></span>

<span data-ttu-id="a519b-p107">Office 365 명령에 대한 이전 Windows PowerShell은 테넌트 ID나 도메인 중 하나를 검색하는 방법을 보여 줍니다(단, 동시에 둘 다를 검색하는 것이 아니며 이 둘 간에 명백한 매핑이 없음). 이 명령은 모든 고객 테넌트 ID와 도메인 목록을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="a519b-p107">The previous Windows PowerShell for Office 365 commands showed you how to retrieve either tenant IDs or domains but not both at the same time, and with no clear mapping between them all. This command generates a listing of all your customer tenant IDs and their domains.</span></span>
  
```
$Tenants = Get-MsolPartnerContract -All; $Tenants | foreach {$Domains = $_.TenantId; Get-MsolDomain -TenantId $Domains | fl @{Label="TenantId";Expression={$Domains}},name}
```

### <a name="get-all-users-for-a-tenant"></a><span data-ttu-id="a519b-131">테넌트에 대한 모든 사용자 가져오기</span><span class="sxs-lookup"><span data-stu-id="a519b-131">Get all users for a tenant</span></span>

<span data-ttu-id="a519b-p108">이렇게 하면 특정 테넌트의 모든 사용자에 대한 **UserPrincipalName**, **DisplayName**, **isLicensed** 상태가 표시됩니다. _<customer TenantId value>_ 을 실제 값으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="a519b-p108">This will display the **UserPrincipalName**, the **DisplayName**, and the **isLicensed** status for all users for a particular tenant. Replace _<customer TenantId value>_ with the actual value.</span></span>
  
```
Get-MsolUser -TenantID <customer TenantId value>
```

### <a name="get-all-details-about-a-user"></a><span data-ttu-id="a519b-134">사용자에 대한 모든 세부 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="a519b-134">Get all details about a user</span></span>

<span data-ttu-id="a519b-p109">특정 사용자에 대한 모든 속성을 확인하려면 이 명령을 실행합니다.  _<customer TenantId value>_ 과 _<user principal name value>_ 을 실제 값으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="a519b-p109">If you want to see all the properties of a particular user, run this command. Replace  _<customer TenantId value>_ and _<user principal name value>_ with the actual values.</span></span>
  
```
Get-MsolUser -TenantId <customer TenantId value> -UserPrincipalName <user principal name value>
```

### <a name="add-users-set-options-and-assign-licenses"></a><span data-ttu-id="a519b-137">사용자 추가, 옵션 설정 및 라이선스 할당</span><span class="sxs-lookup"><span data-stu-id="a519b-137">Add users, set options, and assign licenses</span></span>

<span data-ttu-id="a519b-p110">Office 365 사용자의 대량 생성, 구성, 라이선싱은 특히 Office 365용 Windows PowerShell 사용 시 효율적입니다. 이 2단계 프로세스에서 먼저 쉼표로 구분된 값(CSV) 파일에 추가하려는 모든 사용자에 대한 항목을 만든 다음 Office 365용 Windows PowerShell을 사용하여 해당 파일을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a519b-p110">The bulk creation, configuration, and licensing of Office 365 users is particularly efficient by using Windows PowerShell for Office 365. In this two-step process, you first create entries for all the users you want to add in a comma-separated value (CSV) file and then import that file by using Windows PowerShell for Office 365.</span></span> 
  
#### <a name="create-a-csv-file"></a><span data-ttu-id="a519b-140">CSV 파일 만들기</span><span class="sxs-lookup"><span data-stu-id="a519b-140">Create a CSV file</span></span>

<span data-ttu-id="a519b-141">다음 형식을 사용하여 CSV 파일 만들기</span><span class="sxs-lookup"><span data-stu-id="a519b-141">Create a CSV file by using this format:</span></span>
  
-  `UserPrincipalName,FirstName,LastName,DisplayName,Password,TenantId,UsageLocation,LicenseAssignment`
    
<span data-ttu-id="a519b-142">여기서 각 부분이 나타내는 의미는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a519b-142">where:</span></span>
  
- <span data-ttu-id="a519b-p111">**UsageLocation**: 이 값은 사용자의 두 글자 ISO 국가/지역 코드입니다. 국가/지역 코드는[ISO Online Browsing Platform](https://go.microsoft.com/fwlink/p/?LinkId=532703)에서 조회할 수 있습니다. 예를 들어 미국의 코드는 US이고 브라질의 코드는 BR입니다.</span><span class="sxs-lookup"><span data-stu-id="a519b-p111">**UsageLocation**: The value for this is the two-letter ISO country/region code of the user. The country/region codes can be looked up at the[ISO Online Browsing Platform](https://go.microsoft.com/fwlink/p/?LinkId=532703). For example, the code for the United States is US, and the code for Brazil is BR.</span></span> 
    
- <span data-ttu-id="a519b-p112">**LicenseAssignment**: 이 값은 `syndication-account:<PROVISIONING_ID>` 형식을 사용합니다. 예를 들어 고객 테넌트 사용자 O365_Business_Premium 라이선스를 할당 중인 경우 **LicenseAssignment** 값은 **syndication-account:O365_Business_Premium** 입니다. Syndication 또는 CSP 파트너로 액세스 권한이 있는 Syndication 파트너 포털에서 PROVISIONING_IDs를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a519b-p112">**LicenseAssignment**: The value for this uses this format: `syndication-account:<PROVISIONING_ID>`. For example, if you are assigning customer tenant users O365_Business_Premium licenses, the **LicenseAssignment** value looks like this: **syndication-account:O365_Business_Premium**. You will find the PROVISIONING_IDs in the Syndication Partner Portal that you have access to as a Syndication or CSP partner.</span></span>
    
#### <a name="import-the-csv-file-and-create-the-users"></a><span data-ttu-id="a519b-149">CSV 파일 가져오기 및 사용자 만들기</span><span class="sxs-lookup"><span data-stu-id="a519b-149">Import the CSV file and create the users</span></span>

<span data-ttu-id="a519b-p113">CSV 파일을 만든 후 이 명령을 실행하여 사용자가 처음 로그인 시 변경해야 하며 지정한 라이선스를 할당하는 만료되지 않은 암호로 사용자 계정을 만듭니다. 올바른 CSV 파일 이름을 대체해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a519b-p113">After you have your CSV file created, run this command to create user accounts with non-expiring passwords that the user must change at first sign-in and that assigns the license you specify. Be sure to substitute the correct CSV file name.</span></span>
  
```
Import-Csv .\FILENAME.CSV | foreach {New-MsolUser -UserPrincipalName $_.UserPrincipalName -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -Password $_.Password -UsageLocation $_.UsageLocation -LicenseAssignment $_.LicenseAssignment -ForceChangePassword:$true -PasswordNeverExpires:$true -TenantId $_.TenantId}
```

## <a name="see-also"></a><span data-ttu-id="a519b-152">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a519b-152">See also</span></span>

#### 

[<span data-ttu-id="a519b-153">파트너를 위한 도움말</span><span class="sxs-lookup"><span data-stu-id="a519b-153">Help for partners</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=533477)

