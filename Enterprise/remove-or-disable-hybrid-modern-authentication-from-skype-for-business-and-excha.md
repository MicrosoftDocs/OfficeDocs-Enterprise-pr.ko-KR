---
title: 비즈니스용 Skype 및 Exchange에서 하이브리드 최신 인증 제거 또는 사용 안 함
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/3/2017
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 5a91b9e3-1508-475b-93e0-710fa5d5cd2d
ms.collection:
- M365-security-compliance
f1.keywords:
- NOCSH
ms.custom:
- seo-marvel-apr2020
description: 이 문서에서는 비즈니스용 Skype 및 Exchange에서 하이브리드 최신 인증을 제거 하거나 사용 하지 않도록 설정 하는 방법에 대해 설명 합니다.
ms.openlocfilehash: 9c3dcb2f4bb8993964707a3f30c699bcea3f0dbb
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606174"
---
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a>비즈니스용 Skype 및 Exchange에서 하이브리드 최신 인증 제거 또는 사용 안 함

*이 문서는 Microsoft 365 Enterprise와 Office 365 Enterprise에 모두 적용됩니다.*

현재 환경에 적합 하지 않은 것을 찾기 위해 HMA (Hybrid 현대 Authentication)만 사용 하도록 설정한 경우에는 HMA를 사용 하지 않도록 설정할 수 있습니다. 이 문서에서는 이러한 방법을 설명 합니다.
  
## <a name="who-is-this-article-for"></a>이 문서는 누구에 게 있나요?

비즈니스용 Skype Online 또는 온-프레미스 및/또는 Exchange Online 또는 온-프레미스에서 최신 인증을 사용 하도록 설정한 경우 HMA를 사용 하지 않도록 설정 해야 하는 경우 다음 단계를 수행 합니다.

> [!IMPORTANT]
> 비즈니스용 Skype Online 또는 온-프레미스에 있는 경우 '[최신 인증과 함께 지원 되는 비즈니스용 skype 토폴로지](https://technet.microsoft.com/library/mt803262.aspx)' 문서를 참조 하 고, 혼합 된 토폴로지 HMA를 사용 하며, 시작 하기 전에 지원 되는 토폴로지를 확인 해야 합니다.
  
## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a>하이브리드 최신 인증을 사용 하지 않도록 설정 하는 방법 (Exchange)

1. **Exchange 온-프레미스**: Exchange 관리 셸을 열고 다음 명령을 실행 합니다. 

```powershell
Set-OrganizationConfig -OAuth2ClientProfileEnabled $false
Set-AuthServer -Identity evoSTS -IsDefaultAuthorizationEndpoint $false
```

2. **Exchange online**: 원격 PowerShell을 사용 [하 여 exchange online에 연결](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) 합니다. 다음 명령을 실행 하 여 *OAuth2ClientProfileEnabled* 플래그를 ' f a l i e '로 설정 합니다.

```powershell    
Set-OrganizationConfig -OAuth2ClientProfileEnabled:$false
```
    
## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a>하이브리드 최신 인증을 사용 하지 않도록 설정 하는 방법 (비즈니스용 Skype)

1. 비즈니스용 **Skype 온-프레미스**: 비즈니스용 Skype 관리 셸에서 다음 명령을 실행 합니다.

```powershell
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity ""
```

2. 비즈니스용 **Skype online**: 원격 PowerShell을 사용 [하 여 비즈니스용 skype online에 연결](https://docs.microsoft.com/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell) 합니다. 다음 명령을 실행 하 여 최신 인증을 사용 하지 않도록 설정 합니다.

```powershell    
Set-CsOAuthConfiguration -ClientAdalAuthOverride Disallowed
```

[최신 인증 개요에 다시 연결](hybrid-modern-auth-overview.md) 합니다. 
  

