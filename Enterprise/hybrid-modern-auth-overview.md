---
title: 하이브리드 최신 인증 개요 및 온-프레미스 비즈니스용 Skype와 Exchange 서버를 사용 하기 위한 필수 구성 요소
ms.author: kvice
ms.reviewer: smithre4
author: kelleyvice-msft
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.assetid: ef753b32-7251-4c9e-b442-1a5aec14e58d
ms.collection:
- M365-security-compliance
description: '최신 인증은 사용자 인증 및 권한 부여를 보다 안전 하 게 제공 하는 id 관리 방법입니다. 비즈니스용 Skype 서버 온-프레미스 및 Exchange server 온-프레미스의 하이브리드 배포에는 사용할 수 있으며,이는 분할 도메인 하이브리드 비즈니스를 지원 합니다. 이 문서에서는 필수 구성 요소, 최신 인증 설정/해제, 관련 클라이언트 (예: Outlook 및 Skype 클라이언트) 정보'
ms.openlocfilehash: 6a724ae48166f8946e71cf3f2235e07ee399712a
ms.sourcegitcommit: c8acfa57a22d7d055500f2e8b84a9ef252c70e82
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2019
ms.locfileid: "36493305"
---
# <a name="hybrid-modern-authentication-overview-and-prerequisites-for-using-it-with-on-premises-skype-for-business-and-exchange-servers"></a>하이브리드 최신 인증 개요 및 온-프레미스 비즈니스용 Skype와 Exchange 서버를 사용 하기 위한 필수 구성 요소

최신 인증은 사용자 인증 및 권한 부여를 보다 안전 하 게 제공 하는 id 관리 방법입니다. Office 365 하이브리드 배포는 비즈니스용 skype 서버 온-프레미스 및 Exchange server 온-프레미스에 제공 되 고, 분할 된 비즈니스용 Skype 하이브리드에도 사용할 수 있습니다. 이 문서에서는 필수 구성 요소, 최신 인증 설정/해제, 관련 클라이언트 (예: Outlook 및 Skype 클라이언트) 정보 
  
- [최신 인증 이란?](hybrid-modern-auth-overview.md#BKMK_WhatisModAuth)
    
- [최신 인증을 사용 하는 경우 변경 되는 내용](hybrid-modern-auth-overview.md#BKMK_WhatChanges)
    
- [온-프레미스 환경의 최신 인증 상태 확인](hybrid-modern-auth-overview.md#BKMK_CheckStatus)
    
- [최신 인증 필수 구성 요소를 충족 합니까?](#do-you-meet-modern-authentication-prerequisites)
    
- [시작 하기 전에 알아야 할 사항](hybrid-modern-auth-overview.md#BKMK_Whatelse)
    
- [최신 인증 Url 목록](hybrid-modern-auth-overview.md#BKMK_URLListforMA)
    
## <a name="what-is-modern-authentication"></a>최신 인증 이란?
<a name="BKMK_WhatisModAuth"> </a>

랩톱 또는 휴대폰 등의 클라이언트와 서버 간의 통신에 대 한 의견을 교환할 때 Microsoft는 해당 구를 사용 하 여 최신 인증을 합니다.
  
최신 인증은 인증 및 권한 부여 방법을 함께 사용할 수 있는 포괄적인 용어 뿐 아니라 이미 익숙한 액세스 정책을 사용 하는 몇 가지 보안 수단을 포함 합니다. 여기에는 다음이 포함 됩니다.
  
- **인증 방법**: multi-factor Authentication; 클라이언트 인증서 기반 인증
    
- **권한 부여 방법**: Microsoft의 개방형 권한 부여 (OAuth) 구현 
    
- **조건부 액세스 정책**: MAM (모바일 응용 프로그램 관리) 및 Azure Active Directory 조건부 액세스 
    
최신 인증을 사용 하 여 사용자 id 관리 관리자는 리소스를 보호 하 고 온-프레미스 (Exchange 및 비즈니스용 Skype) 둘 다에 보다 안전한 id 관리 방법을 제공할 때 다양 한 도구를 사용할 수 있습니다. 및 비즈니스용 Skype 하이브리드/분할 도메인 시나리오
  
비즈니스용 Skype가 Exchange와 긴밀 하 게 작동 하기 때문에 비즈니스용 Skype 클라이언트 사용자에 게는 Exchange의 최신 인증 상태에 대 한 영향을 받게 된다는 것을 알 수 있습니다. 비즈니스용 Skype 분할이 있는 경우에도 적용 됩니다. 또한 최신 인증을 사용 하는 비즈니스용 Skype 하이브리드 유형을 ' 분할-도메인 ' (분할 도메인) 이라고 하는 경우에 따라 비즈니스용 Skype Online 및 비즈니스용 Skype를 모두 사용 하 고 사용자가 두 위치에 모두 프레미스 합니다.
  
> [!IMPORTANT]
> 8 월 2017 일에, 비즈니스용 Skype online 및 Exchange online을 포함 하는 모든 새 Office 365 테 넌 트에 기본적으로 최신 인증이 사용 되도록 설정 되어 있는지 확인 해야 합니다. 기존 테 넌 트의 기본 MA 상태는 변경 되지 않지만 모든 새 테 넌 트는 위에 나열 된 것 처럼 표시 되는 확장 된 id 기능 집합을 자동으로 지원 합니다. 비즈니스용 Skype online에 대 한 MA 상태를 확인 하려면 비즈니스용 Skype online PowerShell에 전역 관리자 자격 증명을 사용할 수 있습니다. - `Get-CsOAuthConfiguration` ClientADALAuthOverride의 출력을 확인 하기 위해 실행 됩니다. -ClientADALAuthOverride이 현재 인증을 사용 하 고 있습니다. 
  
## <a name="what-changes-when-i-use-modern-authentication"></a>최신 인증을 사용 하는 경우 변경 되는 내용
<a name="BKMK_WhatChanges"> </a>

온-프레미스 비즈니스용 Skype 또는 Exchange server에서 최신 인증을 사용 하는 경우에도 온-프레미스에서 사용자를 *인증* 하는 중이지만 리소스에 대 한 액세스 *권한 부여* 에 대 한 영역 (예를 들어, 파일 또는 전자 메일)이 변경 됩니다. 이러한 이유는 최신 인증이 클라이언트 및 서버 통신에 대 한 것 이지만, evoSTS (Azure에서 사용 되는 보안 토큰 서비스)가 비즈니스용 Skype 및 Exchange server 온-프레미스의 인증 서버로 설정 되는 동안 수행 되는 단계를 예로 들 수 있습니다. 
  
EvoSTS를 사용 하면 온-프레미스 서버가 OAuth (토큰 발급)을 활용 하 여 클라이언트에 게 권한을 부여할 수 있으며, 온-프레미스에서 클라우드의 공통 보안 방법 (예를 들어 Multi-factor Authentication)을 사용할 수 있습니다. 또한, evoSTS는 사용자가 요청의 일부로 자신의 암호를 제공 하지 않고 리소스에 대 한 액세스를 요청할 수 있도록 하는 토큰을 발급 합니다. 사용자가 로그인 한 위치 (온라인 또는 온-프레미스)와 관계 없이 필요한 리소스를 호스트 하는 위치도 확인 하기 때문에, 이제는 최신 인증이 구성 된 후 사용자 및 클라이언트에 게 권한을 부여 하는 것이 핵심입니다.
  
다음은 I를 의미 하는 결과의 예입니다. 비즈니스용 Skype 클라이언트가 사용자를 대신 하 여 일정 정보를 가져오기 위해 Exchange server에 액세스 해야 하는 경우에는 ADAL (Active Directory 인증 라이브러리)을 사용 하 여이 작업을 수행 합니다. ADAL은 클라이언트 응용 프로그램에서 OAuth 보안 토큰을 사용 하 여 디렉터리의 보안 리소스를 사용할 수 있도록 설계 된 코드 라이브러리입니다. ADAL은 OAuth를 통해 사용자에 게 리소스에 대 한 액세스 권한을 부여 하기 위해 클레임 및 암호가 아닌 exchange 토큰을 확인 합니다. 이 처럼, 이와 같은 트랜잭션의 경우 사용자 클레임의 유효성을 검사 하 고 필요한 토큰을 발급 하는 방법을 아는 서버는 보안 토큰 서비스 온-프레미스 또는 Active Directory Federation Services 일 수 있습니다. 그러나 최신 인증은 클라우드의 azure Active Directory (Azure AD)를 사용 하 여 해당 기관을 중앙에 맞춥니다.
  
또한 Exchange server 및 비즈니스용 Skype 환경이 완전히 온-프레미스이 고 권한 부여 서버가 온라인 상태이 고 온-프레미스 환경에 Office에 대 한 연결을 만들고 유지 관리 하는 기능이 포함 되어 있어야 한다는 것을 의미 합니다. 클라우드의 365 구독 (구독에서 디렉터리로 사용 하는 Azure Active Directory 인스턴스)
  
변경 되지 않는 내용 온-프레미스를 분할 도메인에 포함시킬지 아니면 비즈니스용 Skype 및 Exchange server를 사용 하 고 있는지 여부에 관계 없이 모든 사용자는 먼저 *온-프레미스* 인증을 받아야 합니다. 최신 인증의 하이브리드 구현에서 Lyncdiscovery 및 자동 검색은 온-프레미스 서버를 가리킵니다. 
  
> [!IMPORTANT]
> MA에서 지원 되는 특정 비즈니스용 Skype 토폴로지를 파악 해야 하는 경우 여기에 [설명](https://technet.microsoft.com/en-us/library/mt803262.aspx)된 대로 진행 됩니다.
  
## <a name="check-the-modern-authentication-status-of-your-on-premises-environment"></a>온-프레미스 환경의 최신 인증 상태 확인
<a name="BKMK_CheckStatus"> </a>

최신 인증은 서비스가 OAuth/S2S를 활용할 때 사용 되는 인증 서버를 변경 하기 때문에 비즈니스용 Skype 및 Exchange 환경에 대 한 최신 인증을 설정 했는지 확인 해야 합니다. PowerShell에서 `Get-CSOAuthConfiguration` 명령을 실행 하 여 온-프레미스에서 Exchange 또는 비즈니스용 Skype 서버의 상태를 확인할 수 있습니다. 명령에서 빈 ' OAuthServers ' 속성을 반환 하면 최신 인증이 사용 하지 않도록 설정 됩니다.
  
## <a name="do-you-meet-modern-authentication-prerequisites"></a>최신 인증 필수 구성 요소를 충족 합니까?

계속 하기 전에 목록에서 이러한 항목을 확인 하 고 확인 하세요.
  
- **비즈니스용 Skype 관련**
    
  - 모든 서버에 SFB 서버 2015 CU5 이상이 있어야 합니다.
    
  - **예외** -Sba (Branch 지 속성)가 현재 버전에 있을 수 있습니다 (Lync 2013 기반). 
    
  - SIP 도메인이 Office 365에서 페더레이션 도메인으로 추가 됨
    
  - 모든 SFB 프런트 엔드는 365 인터넷에 대 한 연결 아웃 바운드 (TCP 443) 및 office [125 url 및 IP 주소의 ' Microsoft 365 Common And Office ' 섹션에 있는의 알려진 인증서 루트 crl (tcp 80 56)에 대 한 연결이 있어야 합니다. 범위](urls-and-ip-address-ranges.md)입니다.
  
- **하이브리드 Office 365 환경에서 비즈니스용 Skype 온-프레미스**
  - 비즈니스용 skype 서버 2019을 실행 중인 모든 서버와의 비즈니스용 Skype 서버 2019 배포
  
  - 비즈니스용 skype 서버 2015을 실행 중인 모든 서버와의 비즈니스용 Skype 서버 2015 배포
  
  - 아래에 나열 된 것과 같은 최대 2 개의 서로 다른 서버 버전을 포함 하는 배포
  
     - 비즈니스용 skype 서버 2015 및 비즈니스용 Skype 서버 2019
     
  - 모든 비즈니스용 Skype 서버에는 최신 cummulative 업데이트가 설치 되어 있어야 하며, [비즈니스용 Skype 서버 업데이트](https://docs.microsoft.com/skypeforbusiness/sfb-server-updates) 에서 사용 가능한 모든 업데이트를 찾고 관리 하는 방법을 참조 하세요.
  - 하이브리드 환경에 Lync Server 2010 또는 2013이 없습니다.
    
 **참고 사항** 비즈니스용 Skype 프런트 엔드 서버가 인터넷 액세스용으로 프록시 서버를 사용 하는 경우에는 각 프런트 엔드에 대해 web.config 파일의 구성 섹션에 사용 되는 프록시 서버 IP 및 포트 번호를 입력 해야 합니다. 
  
- C:\Program Files\Skype for Business Server 2015 \ Web Components\Web ticket\int\web.config
    
- C:\Program Files\Skype for Business Server 2015 \ Web Components\Web ticket\ext\web.config
    
```xml
<system.identityModel.services>
  <system.net>
    <defaultProxy>
      <proxy
        proxyaddress="http://192.168.100.60:8080"
        bypassonlocal="true" />
    </defaultProxy>
  </system.net>
</system.identityModel.services>
```
    
> [!IMPORTANT]
> [Office 365 url 및 IP 주소 범위](urls-and-ip-address-ranges.md) 에 대 한 RSS 피드를 구독 하 여 필수 url의 최신 목록으로 현재 상태를 유지 해야 합니다. 
  
- **Exchange Server 관련**
    
  - Exchange server 2013 CU19 및 up 또는 Exchange server 2016 않았습니다 및 up을 사용 하 고 있습니다.
    
  - 해당 환경에 Exchange 서버 2010이 없습니다.
    
  - SSL 오프 로딩이 구성 되어 있지 않습니다. SSL 종료 및 다시 암호화가 지원 됩니다.
    
  - 사용자 환경에서 프록시 서버 인프라를 사용 하 여 서버에서 인터넷에 연결할 수 있도록 하는 경우 모든 Exchange 서버에는 [Internetwebproxy](https://technet.microsoft.com/library/bb123716%28v=exchg.160%29.aspx) 속성에 정의 된 프록시 서버가 있어야 합니다.
  
- **하이브리드 Office 365 환경에서 Exchange Server 온-프레미스**

  - Exchange server 2013를 사용 하는 경우 하나 이상의 서버에 사서함 및 클라이언트 액세스 서버 역할이 설치 되어 있어야 합니다. 사서함 및 클라이언트 액세스 역할을 별도의 서버에 설치할 수 있지만, 추가 안정성과 향상 된 성능을 제공 하기 위해 각 서버에 두 역할을 모두 설치 하는 것이 좋습니다.
  
  - Exchange server 2016 이상 버전을 사용 하는 경우 하나 이상의 서버에 사서함 서버 역할이 설치 되어 있어야 합니다.
  
  - 하이브리드 환경에는 Exchange 서버 2007 또는 2010이 없습니다.
  
  - 모든 Exchange 서버에는 최신 cummulative 업데이트가 설치 되어 있어야 하며, [최신 누적 업데이트로 Exchange 업그레이드](https://docs.microsoft.com/en-us/exchange/plan-and-deploy/install-cumulative-updates?view=exchserver-2019) 를 참조 하 여 사용 가능한 모든 업데이트를 찾고 관리 합니다.
    
- **Exchange 클라이언트 및 프로토콜 요구 사항**
  
  - 다음 클라이언트는 최신 인증을 지원 합니다.

  |**클라이언트**|**기본 프로토콜**|**참고**|
  |:-----|:-----|:-----|
  |Outlook 2013 및 Outlook 2016  <br/> |HTTP를 통한 MAPI  <br/> |HTTP를 통한 MAPI는 이러한 클라이언트와의 최신 인증을 활용 하기 위해 Exchange에서 사용 하도록 설정 해야 합니다 (일반적으로 Exchange 2013 서비스 팩 1 이상에 새로 설치 하는 경우에는 사용 또는 True). 자세한 내용은 [office 2013 및 office 2016 클라이언트 앱에 대 한 최신 인증이 작동 하는 방법을](https://docs.microsoft.com/en-us/office365/enterprise/modern-auth-for-office-2013-and-2016)참조 하세요.  <br/> Outlook의 최소 필수 빌드를 실행 중인지 확인 합니다. [Windows Installer (MSI)를 사용 하는 Outlook 버전에 대 한 최신 업데이트를](https://docs.microsoft.com/en-us/officeupdates/outlook-updates-msi)참조 하세요.  <br/> |
  |Mac용 Outlook 2016  <br/> |Exchange Web Services  <br/> |  <br/> |
  |iOS 및 Android용 Outlook  <br/> |  <br/> |자세한 내용은 [iOS 및 Android 용 Outlook에서 하이브리드 최신 인증 사용](https://docs.microsoft.com/en-us/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth) 을 참조 하세요.  <br/> |
  |Exchange ActiveSync 클라이언트 (예: iOS11 Mail)  <br/> |Exchange ActiveSync  <br/> |최신 인증을 지 원하는 Exchange ActiveSync 클라이언트의 경우 기본 인증에서 최신 인증으로 전환 하기 위해 프로필을 다시 만들어야 합니다.  <br/> |

- **일반 필수 구성 요소**
    
  - ADFS를 사용 하는 경우 페더레이션 하려면 Windows 2012 R2 ADFS 3.0 이상이 있어야 합니다.
    
  - Id 구성은 AAD Connect에서 지 원하는 형식 (예: 암호 해시 동기화, 통과 인증, Office 365, et cetera에서 지 원하는 온-프레미스 STS)입니다.
    
  - 사용자 복제 및 동기화를 위해 AAD 연결이 구성 되었으며 제대로 작동 하 고 있습니다.
    
  - 온-프레미스 및 Office 365 환경 간에 Exchange 클래식 하이브리드 토폴로지 모드를 사용 하 여 하이브리드가 구성 되어 있는지 확인 해야 합니다. Exchange 하이브리드에 대 한 공식적인 지원 설명은 현재 CU 또는 current CU가 있어야 한다고 명시 되어 있습니다.
    
    > [!Note]
    > 하이브리드 최신 인증은 [하이브리드 에이전트](https://docs.microsoft.com/exchange/hybrid-deployment/hybrid-agent)에서 지원 되지 않습니다.
    
  - 온-프레미스 테스트 사용자 및 Office 365에 있는 하이브리드 테스트 사용자가 모두 비즈니스용 Skype 데스크톱 클라이언트 (Skype에서 최신 인증을 사용 하려는 경우) 및 Microsoft Outlook에 로그인 할 수 있는지 확인 합니다 (필요한 경우 다음 사용자에 게 최신 인증을 사용 하려면 Exchange).
    
## <a name="what-else-do-i-need-to-know-before-i-begin"></a>시작 하기 전에 알아야 할 사항
<a name="BKMK_Whatelse"> </a>

1. 온-프레미스 서버에 대 한 모든 시나리오에서 최신 인증을 온-프레미스 (실제로 비즈니스용 Skype)를 설정 하는 작업을 수행 하는 경우 인증 및 권한 부여를 담당 하는 서버가 Microsoft 클라우드에 있을 수 있도록 지원 되는 토폴로지의 목록이 제공 됩니다 ( AAD의 보안 토큰 서비스 (' evoSTS ') 이며 비즈니스용 Skype 또는 Exchange를 온-프레미스 설치에서 사용 하는 Url 또는 네임 스페이스에 대 한 Azure Active Directory (AAD)를 업데이트 하는 중입니다. 따라서 온-프레미스 서버는 Microsoft 클라우드 종속성을 사용 합니다. 이 작업을 수행 하려면 ' 하이브리드 인증 '을 구성 하는 것이 원인일 수 있습니다.
    
2. 이 문서에서는 Exchange 온-프레미스에 대해 지원 되는 최신 인증 토폴로지 (비즈니스용 Skype에만 필요 함) 및 설치 단계를 설명 하는 방법 문서 및 최신 인증을 사용 하지 않도록 설정 하는 단계에 대 한 링크를 제공 하는 다른 사용자에 게 제공 됩니다. 비즈니스용 Skype 온-프레미스 서버 환경에서 최신 인증을 사용 하기 위해 home 기반이 필요한 경우 브라우저에서이 페이지를 즐겨 보세요.
    
## <a name="list-of-modern-authentication-urls"></a>최신 인증 Url 목록
<a name="BKMK_URLListforMA"> </a>

- [최신 인증을 사용 하도록 Exchange Server 온-프레미스를 구성 하는 방법](configure-exchange-server-for-hybrid-modern-authentication.md)
    
- [최신 인증과 함께 지원 되는 비즈니스용 Skype 토폴로지](https://technet.microsoft.com/en-us/library/mt803262.aspx)
    
- [최신 인증을 사용 하도록 비즈니스용 Skype 온-프레미스를 구성 하는 방법](configure-skype-for-business-for-hybrid-modern-authentication.md)
    
- [비즈니스용 Skype 및 Exchange에서 하이브리드 최신 인증 제거 또는 사용 안 함](remove-or-disable-hybrid-modern-authentication-from-skype-for-business-and-excha.md)
    

