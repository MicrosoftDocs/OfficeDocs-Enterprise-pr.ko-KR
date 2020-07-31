---
title: 하이브리드 최신 인증 개요 및 온-프레미스 비즈니스용 Skype 및 Exchange 서버에서 사용하기 위한 필수 구성 요소
ms.author: kvice
ms.reviewer: smithre4
author: kelleyvice-msft
manager: laurawi
ms.date: 04/15/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.assetid: ef753b32-7251-4c9e-b442-1a5aec14e58d
ms.collection:
- M365-security-compliance
f1.keywords:
- NOCSH
description: '최신 인증은 더욱 안전한 사용자 인증 및 권한 부여를 제공하는 ID 관리 방법입니다. 비즈니스용 Skype 서버 온-프레미스 및 Exchange 서버 온-프레미스의 하이브리드 배포뿐 아니라, 분할된 도메인 비즈니스용 Skype 하이브리드에 사용할 수 있습니다. 이 문서는 필수 구성 요소에 대한 관련 문서, 최신 인증 설정/해제 및 일부 관련 클라이언트(예: Outlook 및 Skype 클라이언트) 정보의 링크가 있습니다.'
ms.openlocfilehash: 8b5fcbd20ed0a4f630cda7a05eb068008296d694
ms.sourcegitcommit: d9abb99b336170f07b8f3f6d00fac19ad2159d3a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/28/2020
ms.locfileid: "46502603"
---
# <a name="hybrid-modern-authentication-overview-and-prerequisites-for-using-it-with-on-premises-skype-for-business-and-exchange-servers"></a>하이브리드 최신 인증 개요 및 온-프레미스 비즈니스용 Skype 및 Exchange 서버에서 사용하기 위한 필수 구성 요소

*이 문서는 Microsoft 365 Enterprise와 Office 365 Enterprise에 모두 적용됩니다.*

_최신 인증_은 더욱 안전한 사용자 인증 및 권한 부여를 제공하는 ID 관리 방법입니다. 비즈니스용 Skype 서버 온-프레미스 및 Exchange 서버 온-프레미스의 Office 365 하이브리드 배포뿐 아니라, 분할 도메인 비즈니스용 Skype 하이브리드에 사용할 수 있습니다. 이 문서에는 필수 구성 요소, 최신 인증 설정/해제에 대한 관련 문서 및 일부 관련 클라이언트(예: Outlook 및 Skype 클라이언트) 정보의 링크가 있습니다.
  
- [최신 인증은 무엇인가요?](hybrid-modern-auth-overview.md#BKMK_WhatisModAuth)
- [최신 인증을 사용하면 어떤 변화가 있나요?](hybrid-modern-auth-overview.md#BKMK_WhatChanges)
- [온-프레미스 환경의 최신 인증 상태 확인](hybrid-modern-auth-overview.md#BKMK_CheckStatus)
- [최신 인증 필수 구성 요소를 충족하나요?](#do-you-meet-modern-authentication-prerequisites)
- [시작하기 전에 그 밖에 알아야 할 사항은 무엇인가요?](hybrid-modern-auth-overview.md#BKMK_Whatelse)

## <a name="what-is-modern-authentication"></a>최신 인증은 무엇 인가요?
<a name="BKMK_WhatisModAuth"> </a>

최신 인증은 클라이언트(예: 노트북 또는 휴대폰)와 서버 사이의 인증 및 권한 부여 방법의 조합뿐 아니라, 이미 익숙한 액세스 정책에 의존하는 일부 보안 조치에 대한 포괄적인 용어입니다. 이 목록에는 다음과 같은 내용이 포함됩니다.
  
- **인증 방법**: MFA(다단계 인증), 스마트 카드 인증, 클라이언트 인증서 기반 인증
- **인증 방법**: Microsoft의 OAuth(Open Authorization) 구현
- **조건부 액세스 정책**: MAM(모바일 응용 프로그램 관리) 및 Azure AD(Azure Active Directory) 조건부 액세스

최신 인증을 사용하여 사용자 ID를 관리하면 관리자에게 리소스 보호에 사용할 수 있는 많은 도구를 제공하고 온-프레미스(Exchange 및 비즈니스용 Skype), Exchange 하이브리드 및 비즈니스용 Skype 하이브리드/분할된 도메인 시나리오에 더 안전한 ID 관리 방법을 지원할 수 있습니다.
  
비즈니스용 Skype는 Exchange와 긴밀한 관련이 있으므로 비즈니스용 Skype 클라이언트 사용자에게 표시되는 로그인 동작은 Exchange의 최신 인증 상태의 영향을 받습니다. 비즈니스용 Skype _분할 도메인_ 하이브리드 아키텍처를 사용하고, 여기에 비즈니스용 Skype Online 및 비즈니스용 Skype 온-프레미스가 포함되고 사용자가 양쪽 위치한 경우에도 적용됩니다.

Office 365의 최신 인증에 대한 자세한 내용은 [Office 365 클라이언트 앱 지원 - 최신 인증](office-365-client-support-modern-authentication.md)을 참조하세요.
  
> [!IMPORTANT]
> 2017년 8월을 기준으로 비즈니스용 Skype Online 및 Exchange Online을 포함하는 모든 새 Office 365 테넌트는 기본적으로 최신 인증을 사용하도록 설정되어 있습니다. 기존 테넌트는 기본 MA 상태에 변경이 없지만, 모든 새 테넌트는 위에 나열된 ID 기능의 확장 세트를 자동으로 지원합니다. MA 상태를 확인하려면 [온-프레미스 환경의 최신 인증 상태 확인](hybrid-modern-auth-overview.md#BKMK_CheckStatus) 섹션을 참조하세요.
  
## <a name="what-changes-when-i-use-modern-authentication"></a>최신 인증을 사용하면 어떤 변화가 있나요?
<a name="BKMK_WhatChanges"> </a>

온-프레미스 비즈니스용 Skype 또는 Exchange 서버에 최신 인증을 사용하는 경우, 사용자 온-프레미스를 계속 *인증*하지만, 리소스(파일 또는 전자 메일)에 대한 액세스 *권한 부여* 내용은 변합니다. 따라서 최신 인증은 클라이언트와 서버 통신에 대한 것이지만, MA를 구성하는 동안 수행된 단계로 인해 evoSTS(Azure AD에서 사용하는 보안 토큰 서비스)가 비즈니스용 Skype 및 Exchange 서버 온-프레미스의 인증 서버로 설정됩니다.
  
EvoSTS를 변경하면 온-프레미스 서버에서 클라이언트를 인증하는 데 OAuth(토큰 발급)를 활용하고 온-프레미스에서 클라우드(예: 다단계 인증)에 일반적인 보안 방법을 사용할 수 있습니다. 또한 evoSTS는 사용자가 요청의 일부로 암호를 제공하지 않고도 리소스에 대한 액세스를 요청할 수 있는 토큰을 발행합니다. 사용자가 어디에 있든(온라인 또는 온-프레미스), 필요한 리소스가 어느 위치에 있든 상관 없이, 최신 인증이 구성되면 EvoSTS가 사용자 및 클라이언트에 대한 권한 부여의 핵심적인 요소가 됩니다.
  
예를 들어, 비즈니스용 Skype 클라이언트에서 사용자를 대신하여 일정 정보를 받기 위해 Exchange 서버에 액세스해야 하는 경우에는 ADAL(Active Directory Authentication Library)을 사용합니다. ADAL은 디렉터리에 있는 보안 리소스를 OAuth 보안 토큰을 사용하는 클라이언트 응용 프로그램에서 사용할 수 있도록 설계된 코드 라이브러리입니다. 사용자에게 리소스에 대한 액세스 권한을 부여하기 위해 ADAL은 OAuth와 작업하여 클레임 확인하고 토큰(암호가 아닌)을 교환합니다. 과거에는 이와 같은 트랙잭션의 권한(사용자 클레임의 유효성을 검사하고 필요한 토큰을 발행하는 방법을 아는 서버)이 보안 토큰 서비스 온-프레미스이거나 Active Directory Federation Service일 수 있습니다. 그러나 최신 인증은 Azure AD를 사용하여 해당 권한을 중앙 집중화합니다.
  
즉, Exchange 서버와 비즈니스용 Skype 환경이 완전히 온-프레미스인 경우에도, 인증 서버는 온라인이고, 온-프레미스 환경에 클라우드의 Office 365 구독에 대한 연결을 만들고 유지 관리하는 기능(및 구독에서 디렉터리로 사용하는 Azure AD 인스턴스)이 포함되어 있어야 합니다.
  
어떤 변화가 있나요? 분할 도메인 하이브리드 상태인지 또는 비즈니스용 Skype 및 Exchange 서버 온-프레미스를 사용하는지에 상관 없이, 먼저 모든 사용자가 *온-프레미스*를 인증해야 합니다. 최신 인증을 하이브리드 방식으로 구현하는 경우에는 _Lyncdiscovery_ 및 _Autodiscovery_에서 온-프레미스 서버를 가리킵니다.
  
> [!IMPORTANT]
> MA에서 지원되는 특정 비즈니스용 Skype 토폴로지를 알아야 하는 경우에는 [여기를 참조](https://technet.microsoft.com/library/mt803262.aspx)하세요.
  
## <a name="check-the-modern-authentication-status-of-your-on-premises-environment"></a>온-프레미스 환경의 최신 인증 상태를 확인합니다.
<a name="BKMK_CheckStatus"> </a>

최신 인증은 서비스에서 OAuth/S2S를 활용하는 데 사용되는 인증 서버를 변경하기 때문에 온-프레미스 비즈니스용 Skype 및 Exchange 환경에 대해 최신 인증을 사용하도록 설정했는지 여부를 알고 있어야 합니다. 다음 PowerShell 명령을 실행하여 Exchange 서버에서 상태를 확인할 수 있습니다.

```powershell
Get-OrganizationConfig | ft OAuth*
```

_OAuth2ClientProfileEnabled_ 속성 값이 **False**인 경우 최신 인증을 사용할 수 없습니다.

Get-OrganizationConfig cmdlet에 대한 자세한 내용은 [Get-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/get-organizationconfig)를 참조하세요.

다음 PowerShell 명령을 실행하여 비즈니스용 Skype 서버를 확인할 수 있습니다.

```powershell
Get-CSOAuthConfiguration
```

명령이 비어 있는 _OAuthServers_ 속성을 반환하거나 _ClientADALAuthOverride_ 속성의 값을 **허용**하지 않는 경우 최신 인증을 사용하지 않도록 설정됩니다.

Get-CsOAuthConfiguration cmdlet에 대한 자세한 내용은 [Get-CsOAuthConfiguration](https://docs.microsoft.com/powershell/module/skype/get-csoauthconfiguration)을 참조하세요.
  
## <a name="do-you-meet-modern-authentication-prerequisites"></a>최신 인증 필수 구성 요소를 충족하나요?

계속하기 전에 목록에서 해당 항목을 확인합니다.
  
- **비즈니스용 Skype 관련**
  - 모든 서버에 비즈니스용 Skype Server 2015 이상에 대한 2017년 5월 누적 업데이트(CU5)가 있어야 합니다.
    - **예외** - SBA(Survivability Branch Appliance)는 현재 버전(Lync 2013 기반)일 수 있습니다.
  - SIP 도메인은 Office 365에서 페더레이션 도메인으로 추가됩니다.
  - 모든 SFB 프론트 엔드에는 인터넷과 [Office 365 URL 및 IP 주소 범위](urls-and-ip-address-ranges.md)의 'Microsoft 365 Common and Office' 섹션의 열 56 및 125에 나열된 Office 365 인증 URL(TCP 443) 및 잘 알려진 인증 루트 CRL(TCP 80)에 대한 아웃바운드 연결이 있어야 합니다. 
  
- **하이브리드 Office 365 환경의 비즈니스용 Skype 온-프레미스**
  - 비즈니스용 Skype 서버 2019 배포 - 모든 서버에서 비즈니스용 Skype 서버 2019 실행
  - 비즈니스용 Skype 서버 2015 배포 - 모든 서버에서 비즈니스용 Skype 서버 2015 실행
  - 아래에 나열된 대로 최대 2 개의 서로 다른 서버 버전을 포함하여 배포.
    - 비즈니스용 Skype 서버 2015
    - 비즈니스용 Skype 서버 2019
  - 모든 비즈니스용 Skype 서버에는 최신 누적 업데이트가 설치되어 있어야 하며, [비즈니스용 Skype 서버 업데이트](https://docs.microsoft.com/skypeforbusiness/sfb-server-updates)를 참조하여 사용 가능한 모든 업데이트를 찾고 관리하세요.
  - 하이브리드 환경에 Lync Server 2010 또는 2013이 없습니다.

>[!NOTE]
>비즈니스용 Skype 프런트 엔드 서버에서 인터넷 액세스에 프록시 서버를 사용하는 경우, 사용되는 프록시 서버 IP 및 포트 번호를 각 프론트 엔드에 대한 web.config 파일의 구성 섹션에 입력해야 합니다.
  
- C:\Program Files\Skype for Business Server 2015\Web Components\Web ticket\int\web.config
- C:\Program Files\Skype for Business Server 2015\Web Components\Web ticket\ext\web.config

```xml
<configuration>
  <system.net>
    <defaultProxy>
      <proxy
        proxyaddress="https://192.168.100.60:8080"
        bypassonlocal="true" />
    </defaultProxy>
  </system.net>
</configuration>
```

> [!IMPORTANT]
> [Office 365 URL 및 IP 주소 범위](urls-and-ip-address-ranges.md)에 대한 RSS 피드를 구독하고 필수 URL의 최신 목록으로 최신 상태를 유지하세요.
  
- **Exchange 서버 관련**
  - Exchange 서버 2013 CU19 이상, Exchange 서버 2016 CU8 이상 또는 Exchange 서버 2019 CU1 이상을 사용하고 있습니다.
  - 환경에 Exchange 서버 2010이 없습니다.
  - SSL 오프로딩이 구성되지 않았습니다. SSL 종료 및 다시 암호화가 지원됩니다.
  - 사용자 환경이 프록시 서버 인프라를 사용하여 서버에서 인터넷에 연결할 수 있도록 하려면 모든 Exchange 서버에서 [InternetWebProxy](https://technet.microsoft.com/library/bb123716%28v=exchg.160%29.aspx) 속성에 정의된 프록시 서버를 사용해야 합니다.
  
- **하이브리드 Office 365 환경에서 Exchange Server 온-프레미스**

  - Exchange Server 2013를 사용하는 경우 하나 이상의 서버에 사서함 및 클라이언트 액세스 서버 역할이 설치되어 있어야 합니다. 사서함 및 클라이언트 액세스 역할을 별도 서버에 설치할 수도 있지만, 두 가지 역할을 동일한 서버에 모두 설치해 추가 유연성과 개선된 성능을 확보하는 것이 좋습니다.
  - Exchange 서버 2016 이상을 사용하는 경우 하나 이상의 서버에 사서함 서버 역할이 설치되어 있어야 합니다.
  - 하이브리드 환경에 Exchange 서버 2007 또는 2010이 없습니다.
  - 모든 Exchange 서버에는 최신 누적 업데이트가 설치되어 있어야 하며, [Exchange를 최신 누적 업데이트로 업그레이드](https://docs.microsoft.com/exchange/plan-and-deploy/install-cumulative-updates?view=exchserver-2019)를 참조하여 사용 가능한 모든 업데이트를 찾고 관리하세요.

- **Exchange 클라이언트 및 프로토콜 요구 사항**
  
  - 다음 클라이언트는 최신 인증을 지원합니다.

  |**클라이언트**|**기본 프로토콜**|**참고**|
  |:-----|:-----|:-----|
  |Outlook 2013 및 Outlook 2016  <br/> |HTTP를 통한 MAPI  <br/> |이러한 클라이언트와 최신 인증을 활용하려면 Exchange에서 MAPI를 통한 MAPI를 사용하도록 설정(Exchange 2013 Service Pack 1 이상의 경우 사용 또는 True). 자세한 내용을 보려면 [최신 인증이 Office 2013 및 Office 2016 클라이언트 앱에서 작동하는 방식](https://docs.microsoft.com/office365/enterprise/modern-auth-for-office-2013-and-2016)을 참조하세요.  <br/> Outlook의 최소 필수 빌드를 실행하고 있는지 확인합니다. [Windows Installer(MSI)를 사용하는 Outlook 버전의 최신 업데이트](https://docs.microsoft.com/officeupdates/outlook-updates-msi)를 참조하세요.  <br/> |
  |Mac용 Outlook 2016  <br/> |Exchange 웹 서비스  <br/> |  <br/> |
  |iOS 및 Android용 Outlook  <br/> |  <br/> |자세한 내용은 [Android 및 iOS용 Outlook에서 하이브리드 최신 인증 사용](https://docs.microsoft.com/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth)을 참조하세요.  <br/> |
  |Exchange ActiveSync 클라이언트(예: iOS11 메일)  <br/> |Exchange ActiveSync  <br/> |최신 인증을 지원하는 Exchange ActiveSync 클라이언트의 경우, 기본 인증에서 최신 인증으로 전환하려면 프로필을 다시 만들어야 합니다.  <br/> |

- **일반 필수 구성 요소**
  - AD FS를 사용하는 경우, 페더레이션을 위해 Windows 2012 R2 AD FS 3.0 이상이 있어야 합니다.
  - ID 구성은 암호 해시 동기화, 통과 인증 및 Office 365에서 지원되는 온-프레미스 STS와 같이 Azure AD Connect에서 지원하는 유형입니다.
  - Azure AD Connect가 구성되어 있으며 사용자 복제 및 동기화를 위해 작동하고 있습니다.
  - 온-프레미스 및 Office 365 환경 간에 Exchange 클래식 하이브리드 토폴로지 모드를 사용하여 하이브리드가 구성되었음을 확인했습니다. Exchange 하이브리드의 공식 지원 정책에는 최신 CU 또는 최신 CU - 1이 있어야 합니다.
    > [!NOTE]
    > 하이브리드 최신 인증은 [하이브리드 에이전트](https://docs.microsoft.com/exchange/hybrid-deployment/hybrid-agent)에서 지원되지 않습니다.

  - 온-프레미스 테스트 사용자를 비롯하여 Office 365의 하이브리드 테스트 사용자가 비즈니스용 Skype 데스크톱 클라이언트(Skype에 최신 인증을 사용하려는 경우) 및 Microsoft Outlook(Exchange에 최신 인증을 사용하려는 경우)에 로그인할 수 있는지 확인합니다.

## <a name="what-else-do-i-need-to-know-before-i-begin"></a>시작하기 전에 알아야 할 사항은 무엇입니까?
<a name="BKMK_Whatelse"> </a>

- 인증 및 권한 부여를 담당하는 서버가 Microsoft 클라우드(Azure AD의 보안 토큰 서비스. 'evoSTS'라고 함)에 있고, 비즈니스용 Skype 또는 Exchange의 온-프레미스 설치에 사용되는 URL 또는 네임스페이스에 대한 Azure AD를 업데이트하도록, 온-프레미스 서버에 대한 모든 시나리오에는 최신 인증 온-프레미스를 설정하는 작업이 포함(비즈니스용 Skype의 경우 지원되는 토폴로지 목록이 있음)합니다. 따라서 온-프레미스 서버는 Microsoft 클라우드 종속성을 이용합니다. 이 작업을 수행하면 '하이브리드 인증'을 구성하는 것으로 간주될 수 있습니다.
- 이 문서에는 지원되는 최신 인증 토폴로지를 선택하는 데 도움이 되는 다른 항목뿐 아니라, 설정 단계나 Exchange 온-프레미스 및 비즈니스용 Skype 온-프레미스에서 최신 인증을 사용하지 않도록 설정하는 단계를 설명한 방법 문서에 대한 링크가 있습니다. 서버 환경에서 최신 인증을 사용하는 홈 베이스가 필요한 경우 브라우저에서 이 페이지를 즐겨찾기에 추가하세요.

## <a name="related-topics"></a>관련 항목
<a name="BKMK_URLListforMA"> </a>

- [최신 인증을 사용하도록 Exchange Server 온-프레미스를 구성하는 방법](configure-exchange-server-for-hybrid-modern-authentication.md)
- [최신 인증으로 지원되는 비즈니스용 Skype 토폴로지](https://technet.microsoft.com/library/mt803262.aspx)
- [최신 인증을 사용하도록 비즈니스용 Skype 온-프레미스를 구성하는 방법](configure-skype-for-business-for-hybrid-modern-authentication.md)
- [비즈니스용 Skype 및 Exchange에서 하이브리드 최신 인증 제거 또는 사용 안 함](remove-or-disable-hybrid-modern-authentication-from-skype-for-business-and-excha.md)
