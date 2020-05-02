---
title: DAP(위임된 액세스 권한) 파트너용 Windows PowerShell을 사용하여 클라이언트 테넌트에 도메인 추가
ms.author: chrfox
author: chrfox
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
ms.assetid: f49b4d24-9aa0-48a6-95dd-6bae9cf53d2c
description: 요약:Office 365에 대한 Windows PowerShell을 사용하여 대체 도메인 이름을 기존 고객 테넌트에 추가합니다.
ms.openlocfilehash: 693dbc22fea27c24fb6b578e22d0d2b150a8dfd5
ms.sourcegitcommit: d1022143bdefdd5583d8eff08046808657b49c94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/02/2020
ms.locfileid: "44004751"
---
# <a name="add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-permission-dap-partners"></a>DAP(위임된 액세스 권한) 파트너용 Windows PowerShell을 사용하여 클라이언트 테넌트에 도메인 추가

 **요약:** Office 365에 대한 Windows PowerShell을 사용하여 대체 도메인 이름을 기존 고객 테넌트에 추가합니다.
  
Office 365 관리 센터를 사용하는 것보다 빠른 Microsoft 365용 Windows PowerShell이 포함된 고객의 테넌트로 새로운 도메인을 만들고 연결할 수 있습니다.
  
DAP(위임된 액세스 권한) 파트너는 Syndication 및 CSP(클라우드 솔루션 공급자) 파트너입니다. 이러한 공급자는 다른 회사의 네트워크 또는 전자 통신 공급자인 경우가 많습니다. 이러한 공급자는 서비스와 Office 365 구독을 통합해서 고객에게 제공합니다. Office 365 구독을 판매하는 경우 고객 테넌트에 대한 AOBO(관리 위임자) 권한이 자동으로 부여되므로 고객 테넌트를 관리하고 보고할 수 있습니다.
## <a name="what-do-you-need-to-know-before-you-begin"></a>시작하기 전에 알아야 할 내용

이 항목의 절차를 수행하려면 Windows PowerShell용 Office 365에 연결되어 있어야 합니다.지침을 보려면 [PowerShell Office 365에 연결](connect-to-office-365-powershell.md)을 참조하세요.
  
파트너 테넌트 관리자 자격 증명도 필요합니다.
  
다음 정보도 필요합니다.
  
- 고객이 원하는 FQDN(정규화된 도메인 이름)이 필요합니다.
    
- 고객의 **TenantId** 가 필요합니다.
    
- FQDN은 GoDaddy 등의 DNS(인터넷 도메인 이름 서비스) 등록 기관으로 등록해야 합니다. 도메인 이름을 공개적으로 등록하는 방법에 대한 자세한 내용은 [도메인 이름 구입 방법](https://go.microsoft.com/fwlink/p/?LinkId=532541)을 참조하세요.
    
- DNS 등록 기관에 대해 TXT 레코드를 등록된 DNS 영역에 추가하는 방법을 알아야 합니다. TXT 레코드 추가 방법에 대한 자세한 내용은 [원하는 DNS 호스팅 공급자에서 Office 365용 DNS 레코드 만들기](https://go.microsoft.com/fwlink/p/?LinkId=532542)를 참조하세요. 이러한 절차가 작동하지 않으면 DNS 등록 기관에 대한 절차를 찾아야 합니다.
    
## <a name="create-domains"></a>도메인 만들기

 고객이 기본<domain>.onmicrosoft.com도메인을 회사 ID로 표시할 기본 도메인으로 원하지 않으므로 테넌트와 연결할 추가 도메인 만들기를 문의할 수 있습니다. 이 절차를 통해 고객의 테넌트와 연관된 새 도메인 만들기가 진행됩니다.
  
> [!NOTE]
> 이러한 작업 중 일부를 수행 하려면 로그인 하는 파트너 관리자 계정을 Microsoft 365 관리 센터의 관리자 계정 세부 정보에 있는 지원 되는 **회사에 대 한 관리 액세스 권한 할당** 에 대 한 **전체 관리** 로 설정 해야 합니다. 파트너 관리자 역할 관리에 대한 자세한 내용은 [파트너: 위임된 관리 제안](https://go.microsoft.com/fwlink/p/?LinkId=532435)을 참조하세요. 
  
### <a name="create-the-domain-in-azure-active-directory"></a>Azure Active Directory에서 도메인 만들기

이 명령은 Azure Active Directory에서 도메인을 만들지만 공개적으로 등록된 도메인으로 연결하지는 않습니다. Microsoft Office 365 엔터프라이즈 에디션에 대해 공개적으로 등록된 도메인을 소유하고 있다고 증명될 때 수행됩니다.
  
```
New-MsolDomain -TenantId <customer TenantId> -Name <FQDN of new domain>
```

>[!Note]
>PowerShell Core는 Windows PowerShell용 Microsoft Azure Active Directory 모듈 및 이름에 **Msol**이 있는 cmdlet을 지원하지 않습니다. 이러한 cmdlet을 계속 사용하려면 Windows PowerShell에서 이를 실행해야 합니다.
>

### <a name="get-the-data-for-the-dns-txt-verification-record"></a>DNS TXT 확인 레코드에 대한 데이터 가져오기

 Office 365는 DNS TXT 확인 레코드에 배치해야 하는 특정 데이터를 생성합니다. 데이터를 가져오려면 이 명령을 실행합니다.
  
```
Get-MsolDomainVerificationDNS -TenantId <customer TenantId> -DomainName <FQDN of new domain> -Mode DnsTxtRecord
```

이는 다음과 같은 출력을 제공합니다.
  
 `Label: domainname.com`
  
 `Text: MS=ms########`
  
 `Ttl: 3600`
  
> [!NOTE]
> 공개적으로 등록된 DNS 영역에서 TXT 레코드를 만들려면 이 텍스트가 필요합니다. 텍스트를 복사하고 저장해야 합니다. 
  
### <a name="add-a-txt-record-to-the-publically-registered-dns-zone"></a>TXT 레코드를 공개적으로 등록된 DNS 영역에 추가

Office 365가 공개적으로 등록된 도메인 이름으로 연결된 트래픽을 수락하려면 해당 도메인에 대한 관리자 권한을 소유하고 있음을 증명해야 합니다. 도메인에서 TXT 레코드를 생성하여 도메인 소유를 증명합니다. TXT 레코드는 도메인에서 아무 작업도 수행하지 않으며 도메인 소유권이 설정되고 나면 삭제할 수 있습니다. TXT 레코드를 만들려면 [원하는 DNS 호스팅 공급자에서 Office 365용 DNS 레코드 만들기](https://go.microsoft.com/fwlink/p/?LinkId=532542)의 절차를 따릅니다. 이러한 절차가 작동하지 않으면 DNS 등록 기관에 대한 절차를 찾아야 합니다.
  
nslookup을 통해 TXT 레코드가 만들어졌음을 확인합니다. 이 구문을 사용합니다.
  
```
nslookup -type=TXT <FQDN of registered domain>
```

이는 다음과 같은 출력을 제공합니다.
  
 `Non-authoritative answer:`
  
 `FQDN of the registered domain`
  
 `text=MS=ms########`
  
### <a name="validate-domain-ownership-in-office-365"></a>Office 365에서 도메인 소유권 확인

이 마지막 단계에서 공개적으로 등록된 도메인을 소유하는 Office 365를 확인합니다. 이 단계를 수행한 후 Office 365에서는 새 도메인 이름에 라우팅된 트래픽 수락을 시작합니다. 도메인 만들기 및 등록 프로세스를 완료하려면 이 명령을 실행합니다. 
  
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
   
## <a name="see-also"></a>참고 항목

#### 

[파트너를 위한 도움말](https://go.microsoft.com/fwlink/p/?LinkID=533477)

