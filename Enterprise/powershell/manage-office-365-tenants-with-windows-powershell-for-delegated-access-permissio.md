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
# <a name="manage-microsoft-365-tenants-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a>DAP (위임 된 액세스 권한) 파트너에 대해 Windows PowerShell을 사용 하 여 Microsoft 365 테 넌 트 관리

*이 문서는 Microsoft 365 Enterprise와 Office 365 Enterprise에 모두 적용됩니다.*

Windows PowerShell을 사용 하면 배포 및 CSP (클라우드 솔루션 공급자) 파트너가 Microsoft 365 관리 센터에서 사용할 수 없는 고객 테 넌 트 설정을 쉽게 관리 하 고 보고할 수 있습니다. 파트너 관리자 계정을 사용 하 여 고객의 테 넌 트에 연결 하려면 (AOBO) 권한이 필요 합니다.
  
DAP(위임된 액세스 권한) 파트너는 Syndication 및 CSP(클라우드 솔루션 공급자) 파트너입니다. 이러한 공급자는 다른 회사의 네트워크 또는 전자 통신 공급자인 경우가 많습니다. Microsoft 365 구독을 고객에 게 서비스 제공으로 번들 합니다. Microsoft 365 구독을 판매할 때 고객 테 넌 트에 대 한 관리 및 보고를 수행할 수 있도록 사용자에 게 테 넌 트에 대 한 "대신 (AOBO) 사용 권한을 자동으로 부여 합니다.
## <a name="what-do-you-need-to-know-before-you-begin"></a>시작하기 전에 알아야 할 내용

이 항목의 절차를 수행 하려면 [PowerShell을 사용 하 여 Microsoft 365에 연결](connect-to-office-365-powershell.md)해야 합니다.
  
파트너 테넌트 관리자 자격 증명도 필요합니다.
  
## <a name="what-do-you-want-to-do"></a>무슨 작업을 하고 싶으십니까?

### <a name="list-all-tenant-ids"></a>모든 테넌트 ID 나열

> [!NOTE]
> 테넌트가 500개 넘는 경우  _-All_ 또는 _-MaxResultsParameter_를 사용하여 cmdlet 구문의 범위를 지정합니다. 이는 **Get-MsolUser** 등의 대규모 출력을 제공할 수 있는 다른 cmdlet에 적용됩니다.
  
액세스 권한이 있는 모든 고객의 테넌트 ID를 나열하려면 이 명령을 실행합니다.
  
```
Get-MsolPartnerContract -All | Select-Object TenantId
```

그러면 **TenantId** 별로 모든 고객 테넌트 목록이 표시됩니다.

>[!Note]
>PowerShell Core는 Windows PowerShell용 Microsoft Azure Active Directory 모듈 및 이름에 **Msol**이 있는 cmdlet을 지원하지 않습니다. 이러한 cmdlet을 계속 사용하려면 Windows PowerShell에서 이를 실행해야 합니다.
>
  
### <a name="get-a-tenant-id-by-using-the-domain-name"></a>도메인 이름을 사용하여 테넌트 ID 받기

도메인 이름별로 특정 고객 테넌트에 대한 **TenantId** 를 받으려면 이 명령을 실행합니다. _<domainname.onmicrosoft.com>_ 을 원하는 고객 테넌트의 실제 도메인 이름으로 바꿉니다.
  
```
Get-MsolPartnerContract -DomainName <domainname.onmicrosoft.com> | Select-Object TenantId
```

### <a name="list-all-domains-for-a-tenant"></a>테넌트에 대한 모든 도메인 나열

고객 테넌트에 대한 모든 도메인을 받으려면 이 명령을 실행합니다. _<customer TenantId value>_ 을 실제 값으로 바꿉니다.
  
```
Get-MsolDomain -TenantId <customer TenantId value>
```

추가 도메인을 등록한 경우 고객 **TenantId** 와 관련된 모든 도메인이 반환됩니다.
  
### <a name="get-a-mapping-of-all-tenants-and-registered-domains"></a>모든 테넌트 및 등록된 도메인의 매핑 가져오기

이전에 Microsoft 365 용 PowerShell 명령을 사용 하 여 테 넌 트 Id 또는 도메인을 검색 하는 방법을 설명 했지만이 둘을 모두 제외 하 고는 두 항목을 모두 삭제 하지는 않습니다. 이 명령은 모든 고객 테넌트 ID와 도메인 목록을 생성합니다.
  
```
$Tenants = Get-MsolPartnerContract -All; $Tenants | foreach {$Domains = $_.TenantId; Get-MsolDomain -TenantId $Domains | fl @{Label="TenantId";Expression={$Domains}},name}
```

### <a name="get-all-users-for-a-tenant"></a>테넌트에 대한 모든 사용자 가져오기

이렇게 하면 특정 테넌트의 모든 사용자에 대한 **UserPrincipalName**, **DisplayName**, **isLicensed** 상태가 표시됩니다. _<customer TenantId value>_ 을 실제 값으로 바꿉니다.
  
```
Get-MsolUser -TenantID <customer TenantId value>
```

### <a name="get-all-details-about-a-user"></a>사용자에 대한 모든 세부 정보 가져오기

특정 사용자에 대한 모든 속성을 확인하려면 이 명령을 실행합니다.  _<customer TenantId value>_ 과 _<user principal name value>_ 을 실제 값으로 바꿉니다.
  
```
Get-MsolUser -TenantId <customer TenantId value> -UserPrincipalName <user principal name value>
```

### <a name="add-users-set-options-and-assign-licenses"></a>사용자 추가, 옵션 설정 및 라이선스 할당

Microsoft 365 사용자의 대량 생성, 구성 및 라이선스는 특히 PowerShell for Microsoft 365을 사용 하 여 효율적으로 수행 됩니다. 이 2 단계 프로세스에서는 먼저 쉼표로 구분 된 값 (CSV) 파일에 추가할 모든 사용자에 대 한 항목을 만든 다음 PowerShell for Microsoft 365를 사용 하 여 해당 파일을 가져옵니다. 
  
#### <a name="create-a-csv-file"></a>CSV 파일 만들기

다음 형식을 사용하여 CSV 파일 만들기
  
-  `UserPrincipalName,FirstName,LastName,DisplayName,Password,TenantId,UsageLocation,LicenseAssignment`
    
여기서 각 부분이 나타내는 의미는 다음과 같습니다.
  
- **UsageLocation**: 이 값은 사용자의 두 글자 ISO 국가/지역 코드입니다. 국가/지역 코드는[ISO Online Browsing Platform](https://go.microsoft.com/fwlink/p/?LinkId=532703)에서 조회할 수 있습니다. 예를 들어 미국의 코드는 US이고 브라질의 코드는 BR입니다. 
    
- **LicenseAssignment**: 이 값은 `syndication-account:<PROVISIONING_ID>` 형식을 사용합니다. 예를 들어 고객 테넌트 사용자 O365_Business_Premium 라이선스를 할당 중인 경우 **LicenseAssignment** 값은 **syndication-account:O365_Business_Premium** 입니다. Syndication 또는 CSP 파트너로 액세스 권한이 있는 Syndication 파트너 포털에서 PROVISIONING_IDs를 찾을 수 있습니다.
    
#### <a name="import-the-csv-file-and-create-the-users"></a>CSV 파일 가져오기 및 사용자 만들기

CSV 파일을 만든 후 이 명령을 실행하여 사용자가 처음 로그인 시 변경해야 하며 지정한 라이선스를 할당하는 만료되지 않은 암호로 사용자 계정을 만듭니다. 올바른 CSV 파일 이름을 대체해야 합니다.
  
```
Import-Csv .\FILENAME.CSV | foreach {New-MsolUser -UserPrincipalName $_.UserPrincipalName -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -Password $_.Password -UsageLocation $_.UsageLocation -LicenseAssignment $_.LicenseAssignment -ForceChangePassword:$true -PasswordNeverExpires:$true -TenantId $_.TenantId}
```

## <a name="see-also"></a>참고 항목

#### 

[파트너를 위한 도움말](https://go.microsoft.com/fwlink/p/?LinkId=533477)

