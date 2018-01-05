---
title: "DAP(위임된 액세스 권한) 파트너용 Windows PowerShell을 사용하여 Office 365 테넌트 관리"
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: DecEntMigration
ms.assetid: f92d5116-5b66-4150-ad20-1452fc3dd712
description: "요약:Office 365에 대해 Windows PowerShell을 사용하여 고객 테넌트를 관리합니다."
ms.openlocfilehash: 6001a6b40d2851d13e8fb74da615a2b8137f17ec
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2017
---
# <a name="manage-office-365-tenants-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a>DAP(위임된 액세스 권한) 파트너용 Windows PowerShell을 사용하여 Office 365 테넌트 관리

 **요약:** Office 365에 대해 Windows PowerShell을 사용하여 고객 테넌트를 관리합니다.
  
Windows PowerShell을 통해 Syndication 및 CSP(클라우드 솔루션 공급자) 파트너가 Office 365 관리 센터에서 사용할 수 없는 고객 테넌트 설정을 쉽게 관리하고 보고할 수 있습니다. AOBO(관리 위임자) 권한은 파트너 관리자 계정에서 고객 테넌트에 연결하는 데 필요합니다.
  
DAP(위임된 액세스 권한) 파트너는 Syndication 및 CSP(클라우드 솔루션 공급자) 파트너입니다. 이러한 공급자는 다른 회사의 네트워크 또는 전자 통신 공급자인 경우가 많습니다. 이러한 공급자는 서비스와 Office 365 구독을 통합해서 고객에게 제공합니다. Office 365 구독을 판매하는 경우 고객 테넌트에 대한 AOBO(관리 위임자) 권한이 자동으로 부여되므로 고객 테넌트를 관리하고 보고할 수 있습니다.
## <a name="what-do-you-need-to-know-before-you-begin"></a>시작하기 전에 알아야 할 내용

이 항목의 절차를 수행하려면 Windows PowerShell용 Office 365에 연결되어 있어야 합니다.지침을 보려면 [PowerShell Office 365에 연결](connect-to-office-365-powershell.md)을 참조하세요.
  
파트너 테넌트 관리자 자격 증명도 필요합니다.
  
## <a name="what-do-you-want-to-do"></a>무슨 작업을 하고 싶으십니까?

### <a name="list-all-tenant-ids"></a>모든 테넌트 ID 나열

> [!NOTE]
> 테넌트가 500개 넘는 경우  _-All_ 또는 _-MaxResultsParameter_를 사용하여 cmdlet 구문의 범위를 지정합니다. 이는 **Get-MsolUser** 등의 대규모 출력을 제공할 수 있는 다른 cmdlet에 적용됩니다.
  
액세스 권한이 있는 모든 고객의 테넌트 ID를 나열하려면 이 명령을 실행합니다.
  
```
Get-MsolPartnerContract -All | Select-Object -TenantId
```

그러면 **TenantId** 별로 모든 고객 테넌트 목록이 표시됩니다.
  
### <a name="get-a-tenant-id-by-using-the-domain-name"></a>도메인 이름을 사용하여 테넌트 ID 받기

도메인 이름별로 특정 고객 테넌트에 대한 **TenantId** 를 받으려면 이 명령을 실행합니다. _<domainname.onmicrosoft.com>_을 원하는 고객 테넌트의 실제 도메인 이름으로 바꿉니다.
  
```
Get-MsolPartnerContract -DomainName <domainname.onmicrosoft.com> | Select-Object -TenantId
```

### <a name="list-all-domains-for-a-tenant"></a>테넌트에 대한 모든 도메인 나열

고객 테넌트에 대한 모든 도메인을 받으려면 이 명령을 실행합니다. _<customer TenantId value>_을 실제 값으로 바꿉니다.
  
```
Get-MsolDomain -TenantId <customer TenantId value>
```

추가 도메인을 등록한 경우 고객 **TenantId** 와 관련된 모든 도메인이 반환됩니다.
  
### <a name="get-a-mapping-of-all-tenants-and-registered-domains"></a>모든 테넌트 및 등록된 도메인의 매핑 가져오기

Office 365 명령에 대한 이전 Windows PowerShell은 테넌트 ID나 도메인 중 하나를 검색하는 방법을 보여 줍니다(단, 동시에 둘 다를 검색하는 것이 아니며 이 둘 간에 명백한 매핑이 없음). 이 명령은 모든 고객 테넌트 ID와 도메인 목록을 생성합니다.
  
```
$Tenants = Get-MsolPartnerContract -All; $Tenants | foreach {$Domains = $_.TenantId; Get-MsolDomain -TenantId $Domains | fl @{Label="TenantId";Expression={$Domains}},name}
```

### <a name="get-all-users-for-a-tenant"></a>테넌트에 대한 모든 사용자 가져오기

이렇게 하면 특정 테넌트의 모든 사용자에 대한 **UserPrincipalName**, **DisplayName**, **isLicensed** 상태가 표시됩니다. _<customer TenantId value>_을 실제 값으로 바꿉니다.
  
```
Get-MsolUser -TenantID <customer TenantId value>
```

### <a name="get-all-details-about-a-user"></a>사용자에 대한 모든 세부 정보 가져오기

특정 사용자에 대한 모든 속성을 확인하려면 이 명령을 실행합니다.  _<customer TenantId value>_과 _<user principal name value>_을 실제 값으로 바꿉니다.
  
```
Get-MsolUser -TenantId <customer TenantId value> -UserPrincipalName <user principal name value>
```

### <a name="add-users-set-options-and-assign-licenses"></a>사용자 추가, 옵션 설정 및 라이선스 할당

Office 365 사용자의 대량 생성, 구성, 라이선싱은 특히 Office 365용 Windows PowerShell 사용 시 효율적입니다. 이 2단계 프로세스에서 먼저 쉼표로 구분된 값(CSV) 파일에 추가하려는 모든 사용자에 대한 항목을 만든 다음 Office 365용 Windows PowerShell을 사용하여 해당 파일을 가져옵니다. 
  
#### <a name="create-a-csv-file"></a>CSV 파일 만들기

다음 형식을 사용하여 CSV 파일 만들기
  
-  `UserPrincipalName,FirstName,LastName,DisplayName,Password,TenantId,UsageLocation,LicenseAssignment`
    
여기서 각 부분이 나타내는 의미는 다음과 같습니다.
  
- **UsageLocation**: 이 값은 사용자의 두 글자 ISO 국가/지역 코드입니다. 국가/지역 코드는[ISO Online Browsing Platform](https://go.microsoft.com/fwlink/p/?LinkId=532703)에서 조회할 수 있습니다. 예를 들어 미국의 코드는 US이고 브라질의 코드는 BR입니다. 
    
- **LicenseAssignment**: 이 값은 `syndication-account:<PROVISIONING_ID>` 형식을 사용합니다. 예를 들어 고객 테넌트 사용자 O365_Business_Premium 라이선스를 할당 중인 경우 **LicenseAssignment** 값은 **syndication-account:O365_Business_Premium** 입니다. Syndication 또는 CSP 파트너로 액세스 권한이 있는 Syndication 파트너 포털에서 PROVISIONING_IDs를 찾을 수 있습니다.
    
#### <a name="import-the-csv-file-and-create-the-users"></a>CSV 파일 가져오기 및 사용자 만들기

CSV 파일을 만든 후 이 명령을 실행하여 사용자가 처음 로그인 시 변경해야 하며 지정한 라이선스를 할당하는 만료되지 않은 암호로 사용자 계정을 만듭니다. 올바른 CSV 파일 이름을 대체해야 합니다.
  
```
Import-Csv .\\FILENAME.CSV | foreach {New-MsolUser -UserPrincipalName $_.UserPrincipalName -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -Password $_.Password -UsageLocation $_.UsageLocation -LicenseAssignment $_.LicenseAssignment -ForceChangePassword:$true -PasswordNeverExpires:$true -TenantId $_.TenantId}
```

## <a name="see-also"></a>참고 항목

#### 

[파트너를 위한 도움말](https://go.microsoft.com/fwlink/p/?LinkId=533477)

