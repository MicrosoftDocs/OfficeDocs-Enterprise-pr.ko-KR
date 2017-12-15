---
title: "DAP(위임된 액세스 권한) 파트너용 Windows PowerShell을 사용하여 클라이언트 테넌트에 도메인 추가"
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
ms.assetid: f49b4d24-9aa0-48a6-95dd-6bae9cf53d2c
description: "요약:는 Windows PowerShell을 사용 하는 대체 도메인 이름을 기존 고객 테 넌 트에 추가 하려면 Office 365에 대 한 합니다."
ms.openlocfilehash: 182750a5706dbb23c6207c6bd63334cbf2a2a795
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2017
---
# <a name="add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-permission-dap-partners"></a>DAP(위임된 액세스 권한) 파트너용 Windows PowerShell을 사용하여 클라이언트 테넌트에 도메인 추가

 **요약:** Office 365에 대 한 Windows PowerShell을 사용 하 여 기존 고객 테 넌 트에는 대체 도메인 이름을 추가 해야 합니다.
  
만들 수 있으며 연결할 새 도메인 Windows PowerShell을 사용한 고객의 테 넌 시 Office 365 용 Office 365 관리 센터를 사용 하 여 보다 빠르게 있습니다.
  
위임 된 액세스 권한 (DAP) 파트너는 신디케이션 및 클라우드 솔루션 공급자 (CSP) 파트너입니다. 다른 회사 네트워크 또는 전화 통신 공급자 자주 됩니다. 이러한 번들를 고객에 게 자신의 서비스 제품으로 Office 365 구독 합니다. Office 365 구독을 판매 하는 경우 고객 테에서 thecustomer 테 자신이 관리할 수 있도록 하 고 보고서에 사용 권한은 관리할 대리 (AOBO)를 자동으로 부여 됩니다.
## <a name="what-do-you-need-to-know-before-you-begin"></a>시작하기 전에 알아야 할 내용

UNRESOLVED_TOKEN_VAL(GENL_O365_PowerShell_BeforeYouBegin)
  
다음 정보도 필요합니다.
  
- 고객이 원하는 FQDN(정규화된 도메인 이름)이 필요합니다.
    
- 고객의 **테**해야 합니다.
    
- 인터넷 도메인 이름 서비스 (DNS) 등록자, GoDaddy와 같은 FQDN 등록 해야 합니다. 공개적으로 도메인 이름 등록 하는 방법에 대 한 자세한 내용은 [도메인 이름을 구입 하는 방법](https://go.microsoft.com/fwlink/p/?LinkId=532541)을 참조 하십시오.
    
- TXT 레코드를 DNS 등록자에 대 한 등록 된 DNS 영역에 추가 하는 방법을 알아야 합니다. TXT 레코드를 추가 하는 방법에 대 한 자세한 내용은 [Office 365에 대 한 모든 DNS 호스팅 공급자에서 만들기 DNS 레코드](https://go.microsoft.com/fwlink/p/?LinkId=532542)를 참조 하십시오. 이러한 절차 하면 작동 하지 않으면 DNS 등록자에 대 한 절차를 확인 해야 합니다.
    
## <a name="create-domains"></a>도메인 만들기

 고객이 가능성이 게 직접 요청할 기본 싶어하지 않기 때문에 자신의 테 넌 시와 연결할 추가 도메인을 만들 수 있습니다 <domain>. onmicrosoft.com 도메인 세계 자신의 회사 id를 나타내는 기본 것입니다. 이 절차에서는 고객의 테 넌 시와 관련 된 새 도메인 만들기 (영문) 조정과 합니다.
  
> [!NOTE]
> 일부 이러한 작업을 수행 하기에 구성 된 로그인 파트너 관리자 계정을 설정 해야 **완전 한 관리를** **지원 회사에 대 한 할당 관리 액세스** 에 대 한 관리자 계정에 대 한 세부 정보에서 볼 수 있는 설정의 Office 365 관리 센터입니다. 파트너 관리자 역할 관리에 대 한 자세한 내용은 참조 하십시오.[파트너: 위임 된 관리 제공](https://go.microsoft.com/fwlink/p/?LinkId=532435)합니다. 
  
### <a name="create-the-domain-in-azure-active-directory"></a>Azure Active Directory에서 도메인 만들기

이 명령은 Azure Active Directory에서 도메인 만들지만 공개적으로 등록 된 도메인과 연결 하지는 않습니다. 기업 위한 Microsoft Office 365에 공개적으로 등록 된 도메인의 소유를 증명 하는 경우를 가져옵니다.
  
```
New-MsolDomain -TenantId <customer TenantId> -Name <FQDN of new domain>
```

### <a name="get-the-data-for-the-dns-txt-verification-record"></a>DNS TXT 확인 레코드에 대한 데이터 가져오기

 Office 365 TXT DNS 확인 레코드에 배치 하는 특정 데이터가 생성 됩니다. 데이터를 가져오려면이 명령을 실행 합니다.
  
```
Get-MsolDomainVerificationDNS -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

이는 다음과 같은 출력을 제공합니다.
  
 `Label: domainname.com`
  
 `Text: MS=ms########`
  
 `Ttl: 3600`
  
> [!NOTE]
> 공개적으로 등록된 DNS 영역에서 TXT 레코드를 만들려면 이 텍스트가 필요합니다. 텍스트를 복사하고 저장해야 합니다. 
  
### <a name="add-a-txt-record-to-the-publically-registered-dns-zone"></a>TXT 레코드를 공개적으로 등록된 DNS 영역에 추가

Office 365를 공개적으로 등록 된 도메인 이름에 게 전달 되는 트래픽을 수락를 시작 전에 소유 하 고 도메인에 대 한 관리자 권한이 확인 해야 합니다. 도메인의 TXT 레코드를 작성 하 여 도메인의 소유를 증명 합니다. TXT 레코드는 도메인에 아무 작업도 수행 하지 하 고 도메인의 대화 소유권이 설정 된 후 삭제할 수 있습니다. TXT 레코드를 만들려면 [Office 365에 대 한 모든 DNS 호스팅 공급자에서 만드는 DNS 레코드](https://go.microsoft.com/fwlink/p/?LinkId=532542)에 절차를 따릅니다. 이러한 절차 하면 작동 하지 않으면 DNS 등록자에 대 한 절차를 찾이 필요가 있습니다.
  
Nslookup 통해 TXT 레코드의 성공적인 생성을 확인 합니다. 다음이 구문을 사용 합니다.
  
```
nslookup -type=TXT <FQDN of registered domain>
```

이는 다음과 같은 출력을 제공합니다.
  
 `Non-authoritative answer:`
  
 `FQDN of the registered domain`
  
 `text=MS=ms########`
  
### <a name="validate-domain-ownership-in-office-365"></a>Office 365의 도메인 소유권 확인

이 마지막 단계에서는 하면 유효성을 검사 Office 365에 공개적으로 등록 된 도메인의 소유를 합니다. 이 단계를 수행한 후 새 도메인 이름으로 라우팅되는 트래픽을 허용 하지 Office 365 시작 됩니다. 도메인 만들기 및 등록 프로세스를 완료 하려면이 명령을 실행 합니다. 
  
```
Confirm-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

이 명령은 출력을 반환하지 않으므로 이 작업을 확인하려면 다음 명령을 실행합니다.
  
```
Get-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

그러면 다음과 같이 반환됩니다.
  
||||
|:-----|:-----|:-----|
| `Name` <br/> | `Status` <br/> | `Authentication` <br/> |
| `FQDN of new domain` <br/> | `Verified` <br/> | `Managed` <br/> |
   
## <a name="see-also"></a>See also

#### 

[파트너에 대 한 도움말](https://go.microsoft.com/fwlink/p/?LinkID=533477)

