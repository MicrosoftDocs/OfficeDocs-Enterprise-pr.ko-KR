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
description: "요약: 고객 테를 관리 하는 Office 365에 대 한 Windows PowerShell를 사용 합니다."
ms.openlocfilehash: 6001a6b40d2851d13e8fb74da615a2b8137f17ec
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2017
---
# <a name="manage-office-365-tenants-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a>DAP(위임된 액세스 권한) 파트너용 Windows PowerShell을 사용하여 Office 365 테넌트 관리

 **요약:** Office 365에 대 한 Windows PowerShell을 사용 하 여 고객 클라우드에서 관리 합니다.
  
Windows PowerShell 신디케이션 및 클라우드 솔루션 공급자 (CSP) 파트너를 쉽게 관리 하 고 Office 365 관리 센터에서 사용할 수 없는 고객 테 넌 시 설정에 대해 보고를 허용 합니다. 관리 권한 (AOBO)를 대신 하 여 해당 고객 테 연결할 파트너 관리자 계정에 대 한 필요 하다는 note 합니다.
  
위임 된 액세스 권한 (DAP) 파트너는 신디케이션 및 클라우드 솔루션 공급자 (CSP) 파트너입니다. 다른 회사 네트워크 또는 전화 통신 공급자 자주 됩니다. 이러한 번들를 고객에 게 자신의 서비스 제품으로 Office 365 구독 합니다. Office 365 구독을 판매 하는 경우 고객 테에서 thecustomer 테 자신이 관리할 수 있도록 하 고 보고서에 사용 권한은 관리할 대리 (AOBO)를 자동으로 부여 됩니다.
## <a name="what-do-you-need-to-know-before-you-begin"></a>시작하기 전에 알아야 할 내용

이 항목의 절차에서는 Office 365에 대 한 Windows PowerShell에 연결 해야 합니다. 자세한 내용은 [Office 365 PowerShell 연결](connect-to-office-365-powershell.md)을 참조 하십시오.
  
파트너 테넌트 관리자 자격 증명도 필요합니다.
  
## <a name="what-do-you-want-to-do"></a>무슨 작업을 하고 싶으십니까?

### <a name="list-all-tenant-ids"></a>모든 테넌트 ID 나열

> [!NOTE]
> 500 명이 넘는 테 넌 트를 사용 하는 경우 범위는 cmdlet 구문을 사용 하 여 _-모든_ 또는 _-MaxResultsParameter_합니다. 이 **Get-msoluser**등의 큰 출력을 제공할 수 있는 다른 cmdlet에 적용 됩니다.
  
액세스 권한이 있는 모든 고객의 테넌트 ID를 나열하려면 이 명령을 실행합니다.
  
```
Get-MsolPartnerContract -All | Select-Object -TenantId
```

이 **테**하 여 모든 고객 테 넌 트의 목록에 표시 됩니다.
  
### <a name="get-a-tenant-id-by-using-the-domain-name"></a>도메인 이름을 사용하여 테넌트 ID 받기

도메인 이름으로 특정 고객 테 넌 트에 대 한 **테** 를 가져오려면,이 명령을 실행 합니다. _< Domainname.onmicrosoft.com >_ 하려는 고객 테 넌 트의 실제 도메인 이름으로 바꿉니다.
  
```
Get-MsolPartnerContract -DomainName <domainname.onmicrosoft.com> | Select-Object -TenantId
```

### <a name="list-all-domains-for-a-tenant"></a>테넌트에 대한 모든 도메인 나열

임의의 한 고객 테 넌 트에 대 한 모든 도메인을 얻으려면이 명령을 실행 합니다. 바꾸기 _<customer TenantId value>_ 실제 값을 가진 합니다.
  
```
Get-MsolDomain -TenantId <customer TenantId value>
```

추가 도메인에 등록 한 경우이 고객 **테**와 관련 된 모든 도메인이 반환 됩니다.
  
### <a name="get-a-mapping-of-all-tenants-and-registered-domains"></a>모든 테넌트 및 등록된 도메인의 매핑 가져오기

Office 365 명령에 대 한 이전 Windows PowerShell 테 넌 트 Id 또는 도메인 하지만 둘 중 하나는 동시에 하 고 모든 서로 없는 지우기 매핑을 사용 하 여 검색 하는 방법에 설명 했습니다. 이 명령은 모든 고객 테 넌 트 Id의 목록 및 해당 도메인을 생성합니다.
  
```
$Tenants = Get-MsolPartnerContract -All; $Tenants | foreach {$Domains = $_.TenantId; Get-MsolDomain -TenantId $Domains | fl @{Label="TenantId";Expression={$Domains}},name}
```

### <a name="get-all-users-for-a-tenant"></a>테넌트에 대한 모든 사용자 가져오기

**UserPrincipalName**, **DisplayName**및 모든 사용자에 대 한 **isLicensed** 상태를 특정 테 넌 트가 표시 됩니다. 바꾸기 _<customer TenantId value>_ 실제 값을 가진 합니다.
  
```
Get-MsolUser -TenantID <customer TenantId value>
```

### <a name="get-all-details-about-a-user"></a>사용자에 대한 모든 세부 정보 가져오기

특정 사용자의 모든 속성을 표시 하려는 경우에이 명령을 실행 합니다. 바꾸기 _<customer TenantId value>_ 및 _<user principal name value>_ 실제 값을 사용 합니다.
  
```
Get-MsolUser -TenantId <customer TenantId value> -UserPrincipalName <user principal name value>
```

### <a name="add-users-set-options-and-assign-licenses"></a>사용자 추가, 옵션 설정 및 라이선스 할당

대량 만들기, 구성 및 Office 365 사용자의 라이선스는 특히 효율적 Office 365에 대 한 Windows PowerShell을 사용 하 여 합니다. 이 2 단계 과정을 먼저 쉼표로 구분 된 값 (CSV) 파일에 추가 하 고 Office 365에 대 한 Windows PowerShell을 사용 하 여 해당 파일을 가져오려면 다음 하려는 모든 사용자에 대 한 항목을 만듭니다. 
  
#### <a name="create-a-csv-file"></a>CSV 파일 만들기

다음 형식을 사용하여 CSV 파일 만들기
  
-  `UserPrincipalName,FirstName,LastName,DisplayName,Password,TenantId,UsageLocation,LicenseAssignment`
    
여기서 각 부분이 나타내는 의미는 다음과 같습니다.
  
- **UsageLocation**:이 값은 사용자의 두 문자로 ISO 국가/지역 코드입니다. [ISO 온라인 검색 플랫폼](https://go.microsoft.com/fwlink/p/?LinkId=532703)에서 국가/지역 코드를 조회할 수 있습니다. 예를들어 미국에 대 한 코드 미국, 이며 브라질에 대 한 코드 BR. 
    
- **LicenseAssignment**:이 값이이 형식을 사용: `syndication-account:<PROVISIONING_ID>`합니다. 예, 고객 테 넌 트 사용자를 O365_Business_Premium 라이선스를 할당 하는 경우 **LicenseAssignment** 값 다음과 같은: **신디케이션-계정: O365_Business_Premium**합니다. 신디케이션 또는 CSP 파트너에 대 한 액세스 한다고 신디케이션 파트너 포털에는 PROVISIONING_IDs을 찾을 수 있습니다.
    
#### <a name="import-the-csv-file-and-create-the-users"></a>CSV 파일 가져오기 및 사용자 만들기

만든 CSV 파일을 설치한 후 사용자는 처음 로그인에서 변경 해야 하는 암호가 만료 되지 않은와 사용자 계정을 만들려면이 명령을 실행 하 고 지정한 라이선스를 할당 하는 합니다. 올바른 CSV 파일 이름으로 대체를 사용 해야 합니다.
  
```
Import-Csv .\\FILENAME.CSV | foreach {New-MsolUser -UserPrincipalName $_.UserPrincipalName -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -Password $_.Password -UsageLocation $_.UsageLocation -LicenseAssignment $_.LicenseAssignment -ForceChangePassword:$true -PasswordNeverExpires:$true -TenantId $_.TenantId}
```

## <a name="see-also"></a>See also

#### 

[파트너에 대 한 도움말](https://go.microsoft.com/fwlink/p/?LinkId=533477)

