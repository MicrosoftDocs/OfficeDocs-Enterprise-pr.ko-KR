---
title: 비즈니스용 Skype 및 Exchange에서 하이브리드 최신 인증 제거 또는 사용 안 함
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 11/3/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 5a91b9e3-1508-475b-93e0-710fa5d5cd2d
description: 하이브리드 현대 인증 (HMA)는 현재 환경에 적합 하지 찾을에을 설정한 경우에 HMA를 해제할 수 있습니다. 이 문서에 설명 방법입니다.
ms.openlocfilehash: 802add6295edffe3ec80e70e9bd70663479ec61a
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2019
ms.locfileid: "25359030"
---
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a>비즈니스용 Skype 및 Exchange에서 하이브리드 최신 인증 제거 또는 사용 안 함

하이브리드 현대 인증 (HMA)는 현재 환경에 적합 하지 찾을에을 설정한 경우에 HMA를 해제할 수 있습니다. 이 문서에 설명 방법입니다.
  
## <a name="who-is-this-article-for"></a>이 문서는 누구 입니까?

비즈니스 온라인 또는 온-프레미스, 및/또는 Exchange Online 또는 온-프레미스에 대 한 Skype에서 현대 인증을 사용 하도록 설정 하 고 HMA를 사용 하지 않도록 설정 해야 발견 했을 때, 하는 경우 이러한 단계 수는 있습니다.

> [!IMPORTANT]
> 비즈니스 온라인 또는 온-프레미스 용 Skype 하 고 있는 경우 '[비즈니스 토폴로지 용 Skype 현대 인증을 지원](https://technet.microsoft.com/en-us/library/mt803262.aspx)' 문서를 참조 하는 혼합 토폴로지 HMA 있고 시작 하기 전에 지원 되는 토폴로지를 살펴보는 필요 합니다.
  
## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a>하이브리드 현대 인증 (Exchange)를 사용 하지 않도록 설정 하는 방법

1. **Exchange 온-프레미스**: Exchange 관리 셸을 열고 다음 명령을 실행 합니다. 

```powershell
Set-OrganizationConfig -OAuth2ClientProfileEnabled $false
Set-AuthServer -Identity evoSTS -IsDefaultAuthorizationEndpoint $false
```

2. **Exchange Online**: 원격 PowerShell을 사용 하 여 [Exchange Online에 연결](https://docs.microsoft.com/en-us/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) 을 합니다. E'로 *OAuth2ClientProfileEnabled* 플래그를 설정 하려면 다음 명령을 실행 합니다.

```powershell    
Set-OrganizationConfig -OAuth2ClientProfileEnabled:$false
```
    
## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a>하이브리드 현대 인증 (비즈니스용 Skype)를 사용 하지 않도록 설정 하는 방법

1. **비즈니스 온-프레미스 용 Skype**: 비즈니스 관리 셸의 Skype에서 다음 명령을 실행 합니다.

```powershell
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity ""
```

2. **온라인 비즈니스에 대 한 Skype**: 원격 PowerShell을 사용한 [온라인 비즈니스에 대 한 Skype에 연결](https://docs.microsoft.com/en-us/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell) 합니다. 현대 인증을 사용 하지 않도록 설정 하려면 다음 명령을 실행 합니다.

```powershell    
Set-CsOAuthConfiguration -ClientAdalAuthOverride Disallowed
```

[현대 인증 개요에 다시 연결](hybrid-modern-auth-overview.md) 합니다. 
  

