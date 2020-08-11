---
title: DAP 파트너에 대해 Windows PowerShell을 사용 하 여 Microsoft 365 테 넌 트 관리
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
ms.custom: seo-marvel-apr2020
ms.assetid: f92d5116-5b66-4150-ad20-1452fc3dd712
description: 이 문서에서는 Microsoft 365 용 PowerShell을 사용 하 여 고객 테 넌 트를 관리 하는 방법을 알아봅니다.
ms.openlocfilehash: b1e0459b906bd0a06758147923dff0dcc0af1b3e
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605944"
---
# <a name="manage-microsoft-365-tenants-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="c2163-103">DAP (위임 된 액세스 권한) 파트너에 대해 Windows PowerShell을 사용 하 여 Microsoft 365 테 넌 트 관리</span><span class="sxs-lookup"><span data-stu-id="c2163-103">Manage Microsoft 365 tenants with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

<span data-ttu-id="c2163-104">*이 문서는 Microsoft 365 Enterprise와 Office 365 Enterprise에 모두 적용됩니다.*</span><span class="sxs-lookup"><span data-stu-id="c2163-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="c2163-p101">Windows PowerShell을 사용 하면 배포 및 CSP (클라우드 솔루션 공급자) 파트너가 Microsoft 365 관리 센터에서 사용할 수 없는 고객 테 넌 트 설정을 쉽게 관리 하 고 보고할 수 있습니다. 파트너 관리자 계정을 사용 하 여 고객의 테 넌 트에 연결 하려면 (AOBO) 권한이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2163-p101">Windows PowerShell allows Syndication and Cloud Solution Provider (CSP) partners to easily administer and report on customer tenancy settings that are not available in the Microsoft 365 admin center. Note that Administer on Behalf Of (AOBO) permissions are required for the partner administrator account to connect to its customer tenancies.</span></span>
  
<span data-ttu-id="c2163-107">DAP(위임된 액세스 권한) 파트너는 Syndication 및 CSP(클라우드 솔루션 공급자) 파트너입니다.</span><span class="sxs-lookup"><span data-stu-id="c2163-107">Delegated Access Permission (DAP) partners are Syndication and Cloud Solution Providers (CSP) Partners.</span></span> <span data-ttu-id="c2163-108">이러한 공급자는 다른 회사의 네트워크 또는 전자 통신 공급자인 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="c2163-108">They are frequently network or telecom providers to other companies.</span></span> <span data-ttu-id="c2163-109">Microsoft 365 구독을 고객에 게 서비스 제공으로 번들 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2163-109">They bundle Microsoft 365 subscriptions into their service offerings to their customers.</span></span> <span data-ttu-id="c2163-110">Microsoft 365 구독을 판매할 때 고객 테 넌 트에 대 한 관리 및 보고를 수행할 수 있도록 사용자에 게 테 넌 트에 대 한 "대신 (AOBO) 사용 권한을 자동으로 부여 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2163-110">When they sell a Microsoft 365 subscription, they are automatically granted Administer On Behalf Of (AOBO) permissions to the customer tenancies so they can administer and report on the customer tenancies.</span></span>
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="c2163-111">시작하기 전에 알아야 할 내용</span><span class="sxs-lookup"><span data-stu-id="c2163-111">What do you need to know before you begin?</span></span>

<span data-ttu-id="c2163-112">이 항목의 절차를 수행 하려면 [PowerShell을 사용 하 여 Microsoft 365에 연결](connect-to-office-365-powershell.md)해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2163-112">The procedures in this topic require you to connect to [Connect to Microsoft 365 with PowerShell](connect-to-office-365-powershell.md).</span></span>
  
<span data-ttu-id="c2163-113">파트너 테넌트 관리자 자격 증명도 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="c2163-113">You also need your partner tenant administrator credentials.</span></span>
  
## <a name="what-do-you-want-to-do"></a><span data-ttu-id="c2163-114">무슨 작업을 하고 싶으십니까?</span><span class="sxs-lookup"><span data-stu-id="c2163-114">What do you want to do?</span></span>

### <a name="list-all-tenant-ids"></a><span data-ttu-id="c2163-115">모든 테넌트 ID 나열</span><span class="sxs-lookup"><span data-stu-id="c2163-115">List all tenant IDs</span></span>

> [!NOTE]
> <span data-ttu-id="c2163-p103">테넌트가 500개 넘는 경우  _-All_ 또는 _-MaxResultsParameter_를 사용하여 cmdlet 구문의 범위를 지정합니다. 이는 **Get-MsolUser** 등의 대규모 출력을 제공할 수 있는 다른 cmdlet에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c2163-p103">If you have more than 500 tenants, scope the cmdlet syntax with either  _-All_ or _-MaxResultsParameter_. This applies to other cmdlets that can give a large output, such as **Get-MsolUser**.</span></span>
  
<span data-ttu-id="c2163-118">액세스 권한이 있는 모든 고객의 테넌트 ID를 나열하려면 이 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c2163-118">To list all customer tenant Ids that you have access to, run this command.</span></span>
  
```
Get-MsolPartnerContract -All | Select-Object TenantId
```

<span data-ttu-id="c2163-119">그러면 **TenantId** 별로 모든 고객 테넌트 목록이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c2163-119">This will display a listing of all your customer tenants by **TenantId**.</span></span>

>[!Note]
><span data-ttu-id="c2163-120">PowerShell Core는 Windows PowerShell용 Microsoft Azure Active Directory 모듈 및 이름에 **Msol**이 있는 cmdlet을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c2163-120">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="c2163-121">이러한 cmdlet을 계속 사용하려면 Windows PowerShell에서 이를 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2163-121">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>
  
### <a name="get-a-tenant-id-by-using-the-domain-name"></a><span data-ttu-id="c2163-122">도메인 이름을 사용하여 테넌트 ID 받기</span><span class="sxs-lookup"><span data-stu-id="c2163-122">Get a tenant ID by using the domain name</span></span>

<span data-ttu-id="c2163-p105">도메인 이름별로 특정 고객 테넌트에 대한 **TenantId** 를 받으려면 이 명령을 실행합니다. _<domainname.onmicrosoft.com>_ 을 원하는 고객 테넌트의 실제 도메인 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="c2163-p105">To get the **TenantId** for a specific customer tenant by domain name, run this command. Replace _<domainname.onmicrosoft.com>_ with the actual domain name of the customer tenant that you want.</span></span>
  
```
Get-MsolPartnerContract -DomainName <domainname.onmicrosoft.com> | Select-Object TenantId
```

### <a name="list-all-domains-for-a-tenant"></a><span data-ttu-id="c2163-125">테넌트에 대한 모든 도메인 나열</span><span class="sxs-lookup"><span data-stu-id="c2163-125">List all domains for a tenant</span></span>

<span data-ttu-id="c2163-p106">고객 테넌트에 대한 모든 도메인을 받으려면 이 명령을 실행합니다. _<customer TenantId value>_ 을 실제 값으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="c2163-p106">To get all domains for any one customer tenant, run this command. Replace  _<customer TenantId value>_ with the actual value.</span></span>
  
```
Get-MsolDomain -TenantId <customer TenantId value>
```

<span data-ttu-id="c2163-128">추가 도메인을 등록한 경우 고객 **TenantId** 와 관련된 모든 도메인이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="c2163-128">If you have registered additional domains, this will return all domains associated with the customer **TenantId**.</span></span>
  
### <a name="get-a-mapping-of-all-tenants-and-registered-domains"></a><span data-ttu-id="c2163-129">모든 테넌트 및 등록된 도메인의 매핑 가져오기</span><span class="sxs-lookup"><span data-stu-id="c2163-129">Get a mapping of all tenants and registered domains</span></span>

<span data-ttu-id="c2163-130">이전에 Microsoft 365 용 PowerShell 명령을 사용 하 여 테 넌 트 Id 또는 도메인을 검색 하는 방법을 설명 했지만이 둘을 모두 제외 하 고는 두 항목을 모두 삭제 하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c2163-130">The previous PowerShell for Microsoft 365 commands showed you how to retrieve either tenant IDs or domains but not both at the same time, and with no clear mapping between them all.</span></span> <span data-ttu-id="c2163-131">이 명령은 모든 고객 테넌트 ID와 도메인 목록을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="c2163-131">This command generates a listing of all your customer tenant IDs and their domains.</span></span>
  
```
$Tenants = Get-MsolPartnerContract -All; $Tenants | foreach {$Domains = $_.TenantId; Get-MsolDomain -TenantId $Domains | fl @{Label="TenantId";Expression={$Domains}},name}
```

### <a name="get-all-users-for-a-tenant"></a><span data-ttu-id="c2163-132">테넌트에 대한 모든 사용자 가져오기</span><span class="sxs-lookup"><span data-stu-id="c2163-132">Get all users for a tenant</span></span>

<span data-ttu-id="c2163-p108">이렇게 하면 특정 테넌트의 모든 사용자에 대한 **UserPrincipalName**, **DisplayName**, **isLicensed** 상태가 표시됩니다. _<customer TenantId value>_ 을 실제 값으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="c2163-p108">This will display the **UserPrincipalName**, the **DisplayName**, and the **isLicensed** status for all users for a particular tenant. Replace _<customer TenantId value>_ with the actual value.</span></span>
  
```
Get-MsolUser -TenantID <customer TenantId value>
```

### <a name="get-all-details-about-a-user"></a><span data-ttu-id="c2163-135">사용자에 대한 모든 세부 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="c2163-135">Get all details about a user</span></span>

<span data-ttu-id="c2163-p109">특정 사용자에 대한 모든 속성을 확인하려면 이 명령을 실행합니다.  _<customer TenantId value>_ 과 _<user principal name value>_ 을 실제 값으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="c2163-p109">If you want to see all the properties of a particular user, run this command. Replace  _<customer TenantId value>_ and _<user principal name value>_ with the actual values.</span></span>
  
```
Get-MsolUser -TenantId <customer TenantId value> -UserPrincipalName <user principal name value>
```

### <a name="add-users-set-options-and-assign-licenses"></a><span data-ttu-id="c2163-138">사용자 추가, 옵션 설정 및 라이선스 할당</span><span class="sxs-lookup"><span data-stu-id="c2163-138">Add users, set options, and assign licenses</span></span>

<span data-ttu-id="c2163-139">Microsoft 365 사용자의 대량 생성, 구성 및 라이선스는 특히 PowerShell for Microsoft 365을 사용 하 여 효율적으로 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c2163-139">The bulk creation, configuration, and licensing of Microsoft 365 users is particularly efficient by using PowerShell for Microsoft 365.</span></span> <span data-ttu-id="c2163-140">이 2 단계 프로세스에서는 먼저 쉼표로 구분 된 값 (CSV) 파일에 추가할 모든 사용자에 대 한 항목을 만든 다음 PowerShell for Microsoft 365를 사용 하 여 해당 파일을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c2163-140">In this two-step process, you first create entries for all the users you want to add in a comma-separated value (CSV) file and then import that file by using PowerShell for Microsoft 365.</span></span> 
  
#### <a name="create-a-csv-file"></a><span data-ttu-id="c2163-141">CSV 파일 만들기</span><span class="sxs-lookup"><span data-stu-id="c2163-141">Create a CSV file</span></span>

<span data-ttu-id="c2163-142">다음 형식을 사용하여 CSV 파일 만들기</span><span class="sxs-lookup"><span data-stu-id="c2163-142">Create a CSV file by using this format:</span></span>
  
-  `UserPrincipalName,FirstName,LastName,DisplayName,Password,TenantId,UsageLocation,LicenseAssignment`
    
<span data-ttu-id="c2163-143">여기서 각 부분이 나타내는 의미는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c2163-143">where:</span></span>
  
- <span data-ttu-id="c2163-p111">**UsageLocation**: 이 값은 사용자의 두 글자 ISO 국가/지역 코드입니다. 국가/지역 코드는[ISO Online Browsing Platform](https://go.microsoft.com/fwlink/p/?LinkId=532703)에서 조회할 수 있습니다. 예를 들어 미국의 코드는 US이고 브라질의 코드는 BR입니다.</span><span class="sxs-lookup"><span data-stu-id="c2163-p111">**UsageLocation**: The value for this is the two-letter ISO country/region code of the user. The country/region codes can be looked up at the[ISO Online Browsing Platform](https://go.microsoft.com/fwlink/p/?LinkId=532703). For example, the code for the United States is US, and the code for Brazil is BR.</span></span> 
    
- <span data-ttu-id="c2163-p112">**LicenseAssignment**: 이 값은 `syndication-account:<PROVISIONING_ID>` 형식을 사용합니다. 예를 들어 고객 테넌트 사용자 O365_Business_Premium 라이선스를 할당 중인 경우 **LicenseAssignment** 값은 **syndication-account:O365_Business_Premium** 입니다. Syndication 또는 CSP 파트너로 액세스 권한이 있는 Syndication 파트너 포털에서 PROVISIONING_IDs를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2163-p112">**LicenseAssignment**: The value for this uses this format: `syndication-account:<PROVISIONING_ID>`. For example, if you are assigning customer tenant users O365_Business_Premium licenses, the **LicenseAssignment** value looks like this: **syndication-account:O365_Business_Premium**. You will find the PROVISIONING_IDs in the Syndication Partner Portal that you have access to as a Syndication or CSP partner.</span></span>
    
#### <a name="import-the-csv-file-and-create-the-users"></a><span data-ttu-id="c2163-150">CSV 파일 가져오기 및 사용자 만들기</span><span class="sxs-lookup"><span data-stu-id="c2163-150">Import the CSV file and create the users</span></span>

<span data-ttu-id="c2163-p113">CSV 파일을 만든 후 이 명령을 실행하여 사용자가 처음 로그인 시 변경해야 하며 지정한 라이선스를 할당하는 만료되지 않은 암호로 사용자 계정을 만듭니다. 올바른 CSV 파일 이름을 대체해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2163-p113">After you have your CSV file created, run this command to create user accounts with non-expiring passwords that the user must change at first sign-in and that assigns the license you specify. Be sure to substitute the correct CSV file name.</span></span>
  
```
Import-Csv .\FILENAME.CSV | foreach {New-MsolUser -UserPrincipalName $_.UserPrincipalName -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -Password $_.Password -UsageLocation $_.UsageLocation -LicenseAssignment $_.LicenseAssignment -ForceChangePassword:$true -PasswordNeverExpires:$true -TenantId $_.TenantId}
```

## <a name="see-also"></a><span data-ttu-id="c2163-153">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c2163-153">See also</span></span>

#### 

[<span data-ttu-id="c2163-154">파트너를 위한 도움말</span><span class="sxs-lookup"><span data-stu-id="c2163-154">Help for partners</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=533477)

