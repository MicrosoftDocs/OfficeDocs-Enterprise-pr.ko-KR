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
# <a name="manage-microsoft-365-tenants-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a>DAP (위임 된 액세스 권한) 파트너에 대해 Windows PowerShell을 사용 하 여 Microsoft 365 테 넌 트 관리

Windows PowerShell을 사용 하면 배포 및 CSP (클라우드 솔루션 공급자) 파트너가 Microsoft 365 관리 센터에서 사용할 수 없는 고객 테 넌 트 설정을 쉽게 관리 하 고 보고할 수 있습니다. AOBO(관리 위임자) 권한은 파트너 관리자 계정에서 고객 테넌트에 연결하는 데 필요합니다.
  
DAP(위임된 액세스 권한) 파트너는 Syndication 및 CSP(클라우드 솔루션 공급자) 파트너입니다. 이러한 공급자는 다른 회사의 네트워크 또는 전자 통신 공급자인 경우가 많습니다. Microsoft 365 구독을 고객에 게 서비스 제공으로 번들 합니다. Microsoft 365 구독을 판매할 때 고객 테 넌 트에 대 한 관리 및 보고를 수행할 수 있도록 사용자에 게 테 넌 트에 대 한 "대신 (AOBO) 사용 권한을 자동으로 부여 합니다.
## <a name="what-do-you-need-to-know-before-you-begin"></a>시작하기 전에 알아야 할 내용

The procedures in this topic require you to connect to Windows PowerShell for Office 365. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).
  
파트너 테넌트 관리자 자격 증명도 필요합니다.
  
## <a name="what-do-you-want-to-do"></a>무슨 작업을 하고 싶으십니까?

### <a name="list-all-tenant-ids"></a>모든 테넌트 ID 나열

> [!NOTE]
> If you have more than 500 tenants, scope the cmdlet syntax with either  _-All_ or _-MaxResultsParameter_. This applies to other cmdlets that can give a large output, such as **Get-MsolUser**.
  
액세스 권한이 있는 모든 고객의 테넌트 ID를 나열하려면 이 명령을 실행합니다.
  
```
Get-MsolPartnerContract -All | Select-Object TenantId
```

그러면 **TenantId** 별로 모든 고객 테넌트 목록이 표시됩니다.

>[!Note]
>PowerShell Core는 Windows PowerShell용 Microsoft Azure Active Directory 모듈 및 이름에 **Msol**이 있는 cmdlet을 지원하지 않습니다. 이러한 cmdlet을 계속 사용하려면 Windows PowerShell에서 이를 실행해야 합니다.
>
  
### <a name="get-a-tenant-id-by-using-the-domain-name"></a>도메인 이름을 사용하여 테넌트 ID 받기

To get the **TenantId** for a specific customer tenant by domain name, run this command. Replace _<domainname.onmicrosoft.com>_ with the actual domain name of the customer tenant that you want.
  
```
Get-MsolPartnerContract -DomainName <domainname.onmicrosoft.com> | Select-Object TenantId
```

### <a name="list-all-domains-for-a-tenant"></a>테넌트에 대한 모든 도메인 나열

To get all domains for any one customer tenant, run this command. Replace  _<customer TenantId value>_ with the actual value.
  
```
Get-MsolDomain -TenantId <customer TenantId value>
```

추가 도메인을 등록한 경우 고객 **TenantId** 와 관련된 모든 도메인이 반환됩니다.
  
### <a name="get-a-mapping-of-all-tenants-and-registered-domains"></a>모든 테넌트 및 등록된 도메인의 매핑 가져오기

The previous Windows PowerShell for Office 365 commands showed you how to retrieve either tenant IDs or domains but not both at the same time, and with no clear mapping between them all. This command generates a listing of all your customer tenant IDs and their domains.
  
```
$Tenants = Get-MsolPartnerContract -All; $Tenants | foreach {$Domains = $_.TenantId; Get-MsolDomain -TenantId $Domains | fl @{Label="TenantId";Expression={$Domains}},name}
```

### <a name="get-all-users-for-a-tenant"></a>테넌트에 대한 모든 사용자 가져오기

This will display the **UserPrincipalName**, the **DisplayName**, and the **isLicensed** status for all users for a particular tenant. Replace _<customer TenantId value>_ with the actual value.
  
```
Get-MsolUser -TenantID <customer TenantId value>
```

### <a name="get-all-details-about-a-user"></a>사용자에 대한 모든 세부 정보 가져오기

If you want to see all the properties of a particular user, run this command. Replace  _<customer TenantId value>_ and _<user principal name value>_ with the actual values.
  
```
Get-MsolUser -TenantId <customer TenantId value> -UserPrincipalName <user principal name value>
```

### <a name="add-users-set-options-and-assign-licenses"></a>사용자 추가, 옵션 설정 및 라이선스 할당

Microsoft 365 사용자의 대량 생성, 구성 및 라이선스는 특히 Office 365 용 Windows PowerShell을 사용 하 여 효율적으로 사용할 수 있습니다. 이 2단계 프로세스에서 먼저 쉼표로 구분된 값(CSV) 파일에 추가하려는 모든 사용자에 대한 항목을 만든 다음 Office 365용 Windows PowerShell을 사용하여 해당 파일을 가져옵니다. 
  
#### <a name="create-a-csv-file"></a>CSV 파일 만들기

다음 형식을 사용하여 CSV 파일 만들기
  
-  `UserPrincipalName,FirstName,LastName,DisplayName,Password,TenantId,UsageLocation,LicenseAssignment`
    
여기서 각 부분이 나타내는 의미는 다음과 같습니다.
  
- **UsageLocation**: The value for this is the two-letter ISO country/region code of the user. The country/region codes can be looked up at the[ISO Online Browsing Platform](https://go.microsoft.com/fwlink/p/?LinkId=532703). For example, the code for the United States is US, and the code for Brazil is BR. 
    
- **LicenseAssignment**: The value for this uses this format: `syndication-account:<PROVISIONING_ID>`. For example, if you are assigning customer tenant users O365_Business_Premium licenses, the **LicenseAssignment** value looks like this: **syndication-account:O365_Business_Premium**. You will find the PROVISIONING_IDs in the Syndication Partner Portal that you have access to as a Syndication or CSP partner.
    
#### <a name="import-the-csv-file-and-create-the-users"></a>CSV 파일 가져오기 및 사용자 만들기

After you have your CSV file created, run this command to create user accounts with non-expiring passwords that the user must change at first sign-in and that assigns the license you specify. Be sure to substitute the correct CSV file name.
  
```
Import-Csv .\FILENAME.CSV | foreach {New-MsolUser -UserPrincipalName $_.UserPrincipalName -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -Password $_.Password -UsageLocation $_.UsageLocation -LicenseAssignment $_.LicenseAssignment -ForceChangePassword:$true -PasswordNeverExpires:$true -TenantId $_.TenantId}
```

## <a name="see-also"></a>참고 항목

#### 

[파트너를 위한 도움말](https://go.microsoft.com/fwlink/p/?LinkId=533477)

