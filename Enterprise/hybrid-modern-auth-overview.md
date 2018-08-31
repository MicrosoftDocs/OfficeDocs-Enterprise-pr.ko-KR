---
title: 하이브리드 현대 인증 개요 및 온-프레미스 Skype를 사용 하 여 비즈니스 및 Exchange 서버에 대 한 필수 구성 요소
ms.author: tracyp
ms.reviewer: smithre4
author: MSFTTracyP
manager: laurawi
ms.date: 8/27/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.assetid: ef753b32-7251-4c9e-b442-1a5aec14e58d
description: '현대 인증은 보다 안전한 사용자 인증 및 권한 부여를 제공 하는 id 관리 방법입니다. 비즈니스 서버 온-프레미스 및 Exchange server 온-프레미스,으로 비즈니스 하이브리드에 대 한 분할 도메인 Skype 용 Skype의 하이브리드 배포에 사용할 수 있는 것입니다. 이 문서 링크를 제공 하 고 관련된 클라이언트 (예: Outlook 및 Skype 클라이언트) 정보 중 일부에 필수 구성 요소를 설치/사용 안함 현대 인증에 대 한 문서 관련 합니다.'
ms.openlocfilehash: 3d510c6d3e9f8ff885279dc008eeefb5d1014639
ms.sourcegitcommit: 2ffe998e58ce1466366d697d99f0dd3e85b0605c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/28/2018
ms.locfileid: "23240593"
---
# <a name="hybrid-modern-authentication-overview-and-prerequisites-for-using-it-with-on-premises-skype-for-business-and-exchange-servers"></a>하이브리드 현대 인증 개요 및 온-프레미스 Skype를 사용 하 여 비즈니스 및 Exchange 서버에 대 한 필수 구성 요소

현대 인증은 보다 안전한 사용자 인증 및 권한 부여를 제공 하는 id 관리 방법입니다. 물론에 대 한 비즈니스 서버 온-프레미스 및 Exchange server 온-프레미스, 비즈니스 하이브리드에 대 한 분할 도메인 Skype Skype의 Office 365 하이브리드 배포에 사용할 수 있는 것입니다. 이 문서 링크를 제공 하 고 관련된 클라이언트 (예: Outlook 및 Skype 클라이언트) 정보 중 일부에 필수 구성 요소를 설치/사용 안함 현대 인증에 대 한 문서 관련 합니다. 
  
- [현대 인증 이란?](hybrid-modern-auth-overview.md#BKMK_WhatisModAuth)
    
- [현대 인증을 사용 하는 경우 변경 사항은 무엇입니까?](hybrid-modern-auth-overview.md#BKMK_WhatChanges)
    
- [온-프레미스 환경의 현대 인증 상태 확인](hybrid-modern-auth-overview.md#BKMK_CheckStatus)
    
- [현대 인증 필수 구성 요소를 충족 하면?](hybrid-modern-auth-overview.md#BKMK_MeetPrereq)
    
- [시작 하기 전에 시 필요한 사항](hybrid-modern-auth-overview.md#BKMK_Whatelse)
    
- [현대 인증 Url 목록](hybrid-modern-auth-overview.md#BKMK_URLListforMA)
    
## <a name="what-is-modern-authentication"></a>현대 인증 이란?
<a name="BKMK_WhatisModAuth"> </a>

(예: 랩톱 또는 휴대폰) 클라이언트와 서버 간의 통신에 대 한 음성 채팅을 하는 경우 Microsoft 구를 '현대 인증'를 사용 합니다.
  
현대 인증은 인증 및 권한 부여 방법으로 액세스 정책에 이미 익숙한 있을 사용 하는 일부 보안 조치의 조합에 대 한 포괄적인 용어입니다. 포함 됩니다.
  
- **인증 방법**: 다중 요소 인증 클라이언트 인증서 기반 인증 및 Active Directory 인증 라이브러리 ( [ADAL](https://technet.microsoft.com/en-us/library/mt710548.aspx))을 지정 합니다.
    
- **권한 부여 방법**: OAuth (Open Authorization)의 Microsoft의 구현 합니다. 
    
- **조건부 액세스 정책**: 모바일 응용 프로그램 관리 (MAM) 및 Azure Active Directory 조건부 액세스 합니다. 
    
현대 인증 된 사용자 id를 관리 관리자에 게 제공, 사용 하 여 리소스 보안을 제공 하 고 두 온-프레미스 (Exchange와 비즈니스를 위한 Skype)에 id 관리의 보안을 강화 메서드를 제공 하는 경우 Exchange 하이브리드 다양 한 도구 및 비즈니스 하이브리드/분할 도메인 시나리오에 대 한 Skype 합니다.
  
Skype 비즈니스를 위한 Exchange와의 밀접 하 게 작동 하기 때문에 사용자에 게는 표시 하는 비즈니스 클라이언트에 대 한 로그인 동작 Skype Exchange의 현대 인증 상태에 따라 영향 됩니다에 유의 합니다. 이 비즈니스 분할 도메인 하이브리드에 대 한 Skype 있는 경우에 적용 됩니다. 또한 현대 인증 사용을 지 원하는 비즈니스 하이브리드에 대 한 Skype 유형의 흔히 이라고 ' 분할 도메인 ' (비즈니스 온라인 용 Skype와 비즈니스에서-prem, 용 Skype가 분할 도메인 및 사용자가 두 위치에 있는).
  
 **중요 한** 않은 있습니다 한다는 것을 알, 2017 년 8 월 기준 온라인 비즈니스를 위한 Skype를 포함 하 고 온라인 교환 하는 모든 새 Office 365 테 넌은 기본적으로 사용 하도록 설정 하는 현대 인증? 기존 테 넌 트 기본 MA 상태로 변경을 갖지 않도록 하지만 모든 새 테 넌 트 자동으로 확장된 기능 집합을 identity 위에 나열 된 참조를 지원 합니다. 비즈니스를 위한 Skype에 대 한 MA 상태를 온라인 확인 하려면 전역 관리자 자격 증명을 가진 비즈니스 온라인 PowerShell 용 Skype를 사용할 수 있습니다. ' Get-csoauthconfiguration '-ClientADALAuthOverride의 출력을 확인 하려면를 실행 합니다. -ClientADALAuthOverride은 '허용 되는 경우' 현대 인증 켜져 있습니다. 
  
## <a name="what-changes-when-i-use-modern-authentication"></a>현대 인증을 사용 하는 경우 변경 사항은 무엇입니까?
<a name="BKMK_WhatChanges"> </a>

온-프레미스 Skype와 현대 인증을 사용 하 여 비즈니스 또는 Exchange 서버에 대 한 때 넌 아직도 *인증* 사용자가 온-프레미스, 하지만 *권한 부여* 의 story 리소스 (예: 파일 또는 전자 메일) 변경 내용에 대 한 액세스 합니다. EvoSTS (보안 토큰 서비스 Azure AD에서 사용 하는)에서 MA 결과 구성 하는 동안 수행 하는 단계 클라이언트 및 서버 통신 하는 방법에 대 한 최신 인증은 하지만이 인해, 비즈니스 및 Exchange server 온-프레미스 용 Skype에 대 한 인증 서버로 설정 합니다. 
  
EvoSTS 하 여 변경 내용을 사용 하면 온-프레미스 클라이언트, 권한 부여에 대 한 OAuth (토큰 발급) 기능을 활용 하는 서버 및 클라우드 (예: 다단계 인증)의 일반적인 온-프레미스 사용 하 여 보안 메서드를 사용 하면 수 있습니다. 또한는 evoSTS 요청의 일부로 자신의 암호를 제공 하지 않고 리소스에 대 한 액세스를 요청할 수 있도록 하는 토큰을 발급 합니다. 사용자가 있는 위치에 관계 없이 (의 온라인 또는 온-프레미스), 필요한 리소스를 호스팅하는 어느 위치에 관계 없이 EvoSTS 될 핵심 요소인 현대 인증을 구성한 후에 사용자 및 클라이언트의 권한을 부여 하 고 있습니다.
  
I 의미의 예는 다음과 같습니다. Skype 비즈니스 클라이언트에 대 한 사용자를 대신 하 여 일정 정보를 보려면 Exchange 서버에 액세스 하는 경우에 Active Directory 인증 라이브러리 (ADAL)을 사용 하 여 되도록 합니다. ADAL 코드 라이브러리 하도록 디렉터리의 보안된 리소스를 OAuth 보안 토큰을 사용 하는 클라이언트 응용 프로그램에 사용할 수 있도록 설정 합니다. 클레임을 확인 하 고 토큰 (암호 대신), 리소스에 대 한 사용자 액세스 권한을 부여 하려면 exchange OAuth와 ADAL 작동 합니다. 과거에 인증 기관에서 이와 같은-사용자 클레임의 유효성을 검사 하 고 필요한 토큰을 발급 하는 방법을 알고 있는 서버--트랜잭션 되었을 수 있습니다는 보안 토큰 서비스 온-프레미스, 또는 Active Directory Federation Services도 합니다. 그러나 현대 인증 클라우드에서 Azure Active Directory (Azure AD)와 해당 기관 중앙 집중화합니다.
  
즉, 하는 경우에 Exchange 서버와 Skype 비즈니스 환경을 완전히 수에 대 한 온-프레미스, 권한을 부여 하는 서버는 온라인 상태 이며, 온-프레미스 환경을 만들고 사무실에 대 한 연결을 유지 관리할 수 있어야 합니다. 클라우드 (및 해당 디렉터리도 구독을 사용 하는 Azure Active Directory 인스턴스)에 365 구독 합니다.
  
기능 변경 되지 않습니다. 분할 도메인 하이브리드 또는 비즈니스 및 Exchange server 온-프레미스 용 Skype를 사용 하 든 모든 사용자에 게 *온-프레미스* 를 먼저 인증 해야 합니다. 하이브리드 구현 하는 현대 인증, Lyncdiscovery 및 자동 검색 온-프레미스 서버를 가리킵니다. 
  
 **중요 한** MA에 대해서는 지원 되는 비즈니스 토폴로지에 대 한 특정 Skype 알아야 하는 경우 [오른쪽 여기서 설명](https://technet.microsoft.com/en-us/library/mt803262.aspx)하는 것이입니다.
  
## <a name="check-the-modern-authentication-status-of-your-on-premises-environment"></a>온-프레미스 환경의 현대 인증 상태 확인
<a name="BKMK_CheckStatus"> </a>

서비스 OAuth/S2S을 활용 하는 경우 사용 되는 인증 서버를 변경 하는 현대 인증, 때문에 비즈니스 및 Exchange 환경에 대 한 사용자 Skype에 대 한 최신 인증이 설정 또는 해제 하는 경우 알고 해야 합니다. PowerShell에서 Get-csoauthconfiguration 명령을 실행 하 여 온-프레미스, 비즈니스 서버에 대 한 Exchange 또는 Skype 상태를 확인할 수 있습니다. 명령이 빈 'OAuthServers' 속성을 반환 하는 경우 최신 인증 비활성화 됩니다.
  
## <a name="do-you-meet-modern-authentication-prerequisites"></a>현대 인증 필수 구성 요소를 충족 하면?

확인 하 고 계속 하기 전에 대화 목록 오프 이러한 항목을 확인 합니다.
  
- **비즈니스 관련 용 Skype**
    
  - 모든 서버에는 SFB 서버 2015 c u 5 있어야 합니다. 이상
    
  - **예외** -지속 가능성 분기 기기 (SBA) (Lync 2013 기준) 현재 버전에 있을 수 있습니다 
    
  - SIP 도메인이 Office 365에서 페더레이션 도메인으로 추가 됩니다.
    
  - Office 365 인증 Url (TCP 443) 및 잘 알려진 인증서 루트 Crl (TCP 80)를 인터넷에 아웃 바운드 연결 행 1과 2/ [Office 365 Url 및 IP 'Office 365 인증 및 id' 섹션에 나열 된 모든 SFB 프런트엔드 있어야 주소 범위](https://www.bing.com/search?q=%22Office+365+URLs+and+IP+address+ranges%22&amp;src=IE-SearchBox&amp;FORM=IESR3N&amp;redir=5&amp;itrid=96B6C7422F9F4019B37C1B7FDAF8831E)합니다.
    
 **참고 사항** 인터넷 액세스를 위한 프록시 서버를 사용 하는 비즈니스 프런트엔드 서버에 대 한 사용자 Skype, 하는 경우 각 프런트엔드에 대 한 web.config 파일의 구성 섹션에서 사용 되는 프록시 서버 IP와 포트 번호를 입력 해야 합니다. 
  
- Business Server 2015\Web Components\Web ticket\int\web.config에 대 한 c:\program files\Skype
    
- Business Server 2015\Web Components\Web ticket\ext\web.config에 대 한 c:\program files\Skype
    
- \</system.identityModel.services\>
    
     \<system.net\> 
    
     \<자세한\> 
    
     \<프록시 
    
     되는 proxyaddress = "http://192.168.100.60:8080" 
    
     생성자 = "true" 
    
     /\> 
    
     \</defaultProxy\> 
    
     \</system.net\> 
    
    \</configuration\>
    
 **중요 한** RSS [Office 365 Url 및 IP 주소 범위를](https://support.office.com/en-us/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) 필요한 Url의 최신 목록을와 최신 정보에 대 한 피드를 구독 해야 합니다. 
  
- **특정 Exchange 서버**
    
  - Exchange server 2013 CU19 중 하나를 사용 하는 위로, 또는 Exchange server 2016 CU8 및 up 합니다.
    
  - 환경에 없는 Exchange server 2010 방법이 있습니다.
    
  - SSL 오프 로딩 구성 되지 않았습니다. SSL 종료 하 고 다시 암호화가 지원 됩니다.
    
  - 서버에서 인터넷에 연결할 수 있도록 하는 프록시 서버 인프라를 이용 하는 환경, 이벤트에서 모든 Exchange 서버 [InternetWebProxy](https://technet.microsoft.com/en-us/library/bb123716%28v=exchg.160%29.aspx) 속성에 정의 된 프록시 서버에 있는 확인 해야 합니다.
    
- **Exchange 클라이언트와 프로토콜 요구 사항**
  
  - 다음 클라이언트 현대 인증을 지원 합니다.

  |**클라이언트**|**기본 프로토콜**|**참고**|
  |:-----|:-----|:-----|
  |Outlook 2013 및 Outlook 2016  <br/> |HTTP를 통한 MAPI  <br/> |이러한 클라이언트 (일반적으로 사용 하거나 새 설치 하 고 위의 Exchange 2013 서비스 팩 1의 경우에 True); 함께 현대 인증을 활용 하기 위해 Exchange 내에서 HTTP 통한 MAPI는 사용할 수 있어야 자세한 내용은 [Office 2013 및 Office 2016 클라이언트 응용 프로그램에 대 한 인증 작동 방법을 현대](https://docs.microsoft.com/en-us/office365/enterprise/modern-auth-for-office-2013-and-2016)를 참조 하십시오.  <br/> Outlook;의 최소 필요한 빌드를 실행 하는 확인 [Windows Installer (MSI)을 사용 하는 Outlook의 버전에 대 한 최신 업데이트](https://docs.microsoft.com/en-us/officeupdates/outlook-updates-msi)를 참조 하십시오.  <br/> |
  |Mac용 Outlook 2016  <br/> |Exchange Web Services  <br/> |  <br/> |
  |iOS 및 Android용 Outlook  <br/> |  <br/> |자세한 정보를 [사용 하 여 하이브리드 iOS와 Android에 대 한 Outlook 사용 하 여 최신 인증을](https://docs.microsoft.com/en-us/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth) 참조 하십시오.  <br/> |
  |Exchange ActiveSync 클라이언트 (예: iOS11 메일)  <br/> |Exchange ActiveSync  <br/> |현대 인증을 지 원하는 Exchange ActiveSync 클라이언트에 대 한 기본 인증에서 현대 인증으로 전환 하기 위해 프로필을 다시 만들어야 합니다.  <br/> |

- **일반 필수 구성 요소**
    
  - ADFS를 사용 하는 경우 Windows 2012 R2 ADFS 3.0 있어야 이상인 페더레이션에 대 한
    
  - Identity 구성을 AAD 연결 하 여 지원 되는 형식 중 하나는 (암호 해시 동기화, 통과 인증 온-프레미스 STS Office 365에서 지 원하는와 같은 et cetera.)
    
  - AAD 연결 구성 및 사용자 복제 및 동기화에 대 한 작동 해야 합니다.
    
  - 해당 하이브리드 온-프레미스 및 Office 365 간의 작동 확인:
    
  - Exchange 하이브리드에 대 한 공식적으로 지원 문을 이라는 현재 CU 또는 현재 CU-1 중 하나를 사용 하도록 해야 합니다.
    
  - (현대 인증을 사용 하는 것이 원하는 경우 확인 하이브리드 테스트 사용자와 온-프레미스 테스트 사용자를 홈으로 지정 된 Office 365의 비즈니스 데스크톱 클라이언트 (Skype와 현대 인증을 사용할 경우)에 대 한 Skype와 Microsoft Outlook에 로그인 할 수 있습니다. Exchange)입니다.
    
## <a name="what-else-do-i-need-to-know-before-i-begin"></a>시작 하기 전에 시 필요한 사항
<a name="BKMK_Whatelse"> </a>

1. 온-프레미스 서버에 대 한 모든 시나리오와 관련 현대 인증 온-프레미스 설정 (사실에 대 한 비즈니스를 위한 Skype 지원 되는 토폴로지 목록이 방법이) 인증 및 권한 부여 하는 일을 담당 하는 서버에 있는 Microsoft 클라우드 (있도록 AAD의 보안 토큰 서비스), 'evoSTS' 라는), Azure Active Directory (AAD) Url 또는 비즈니스 또는 Exchange에 대 한 두 Skype의 온-프레미스 설치에서 사용 하는 네임 스페이스에 대 한 업데이트 하 고 있습니다. 따라서 온-프레미스 서버 Microsoft 클라우드 의존 관계 적용 됩니다. 이 작업을 수행 '하이브리드 인증' 구성 간주 될 수 있습니다.
    
2. 이 문서 링크 아웃 다른 사용자에 게 선택 하는데 도움이 되는 지원 되는 (비즈니스용 Skype에만 필요), 현대 인증 토폴로지 및 사용 방법 해당 개요 설치 단계에서 문서 또는 Exchange 온-프레미스에 대 한 최신 인증을 사용 하지 않도록 설정 하는 단계 비즈니스 온-프레미스 용 Skype 하 고 있습니다. 좋아하는 홈-기반 서버 환경에서 현대 인증을 사용 하기 위한 필요 하려고 하는 경우 브라우저에서이 페이지입니다.
    
## <a name="list-of-modern-authentication-urls"></a>현대 인증 Url 목록
<a name="BKMK_URLListforMA"> </a>

- [Exchange Server 온-프레미스 현대 인증을 사용 하도록 구성 하는 방법](configure-exchange-server-for-hybrid-modern-authentication.md)
    
- [현대 인증을 지원 되는 비즈니스 토폴로지 용 Skype](https://technet.microsoft.com/en-us/library/mt803262.aspx)
    
- [현대 인증을 사용 하 여 비즈니스 온-프레미스 용 Skype를 구성 하는 방법](configure-skype-for-business-for-hybrid-modern-authentication.md)
    
- [비즈니스용 Skype 및 Exchange에서 하이브리드 최신 인증 제거 또는 사용 안 함](remove-or-disable-hybrid-modern-authentication-from-skype-for-business-and-excha.md)
    

