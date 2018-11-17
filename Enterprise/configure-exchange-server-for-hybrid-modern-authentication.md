---
title: 하이브리드 최신 인증을 사용하도록 Exchange Server 온-프레미스를 구성하는 방법
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 11/16/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: cef3044d-d4cb-4586-8e82-ee97bd3b14ad
description: 하이브리드 현대 인증 (HMA)는 보다 안전한 사용자 인증 및 권한 부여를 제공 하 고 Exchange server 온-프레미스 하이브리드 배포에 사용할 수 있는 id 관리 방법입니다.
ms.openlocfilehash: df5ea03b06ee1c101b03e19c7acb445c9543586b
ms.sourcegitcommit: 45633b7034ee98d0cd833db9743f283b638237f4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/16/2018
ms.locfileid: "26547160"
---
# <a name="how-to-configure-exchange-server-on-premises-to-use-hybrid-modern-authentication"></a>하이브리드 최신 인증을 사용하도록 Exchange Server 온-프레미스를 구성하는 방법

하이브리드 현대 인증 (HMA)는 보다 안전한 사용자 인증 및 권한 부여를 제공 하 고 Exchange server 온-프레미스 하이브리드 배포에 사용할 수 있는 id 관리 방법입니다.
  
## <a name="fyi"></a>선택 참석자

시작 하기 전에 다음을 호출 I:
  
- 하이브리드 현대 인증 \> HMA
    
- 온-프레미스 exchange \> EXCH
    
- Exchange Online \> EXO
    
또한 *이 문서는가 ' 흐리게 표시 ' 또는 '흐리게 표시' 즉, 회색으로 표시 된 요소 HMA 관련 구성에 포함 되지 않은 개체는 하는 경우에 그래픽은* 합니다. 
  
## <a name="enabling-hybrid-modern-authentication"></a>하이브리드 현대 인증을 사용 하도록 설정

HMA 의미를 설정 합니다.
  
1. 시작 하기 전에 선행 조건 충족 되 고 있습니다.
    
1. 많은 **필수 구성 요소** 이후 비즈니스 및 Exchange, [하이브리드 현대 인증 개요와 함께 사용 하는 것에 대 한 필수 구성 요소 온-프레미스 비즈니스 및 Exchange 서버에 대 한 Skype](hybrid-modern-auth-overview.md)Skype 모두에 대 한 일반적인 됩니다. 이 문서의 단계 중 하나를 시작 하기 전에이 작업을 수행 합니다.
    
2. 추가 (영문) 온-프레미스 웹 서비스 Url (Spn) 서비스 사용자 이름으로 Azure AD에 있습니다.
    
3. HMA를 사용할 수 있는 모든 가상 디렉터리를 확인 합니다.
    
4. EvoSTS 인증 서버 개체를 확인 하는 기능
    
5. EXCH.에서 HMA를 사용 하도록 설정
    
 **참고 사항** Office의 버전 MA를 지원 합니까? [Office 2013 및 Office 2016 클라이언트 응용 프로그램에 대 한 인증 작동 방법 현대](modern-auth-for-office-2013-and-2016.md)를 참조 하십시오.
  
## <a name="make-sure-you-meet-all-the-pre-reqs"></a>모든는 p r e-요구 사항 충족 하는지 확인

많은 필수 구성 요소는 일반적으로 비즈니스 및 Exchange에 대 한 두 Skype, 이후 [하이브리드 현대 인증 개요 및 사용 하 여 비즈니스 및 Exchange 서버에 대 한 온-프레미스 Skype 사용 하기 위한 필수 구성 요소를](hybrid-modern-auth-overview.md)검토 합니다. 이 수행 *하기 전에* 이 문서의 단계 중 하나를 시작 합니다. 
  
## <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a>온-프레미스 Azure AD에 Spn으로 서비스 Url을 웹 추가

Azure AD Spn. Spn은 클라이언트 컴퓨터 및 장치에서 인증 및 권한 부여 하는 동안 사용 되는 대로 온-프레미스 웹 서비스 Url을 할당 하는 명령을 실행 합니다. Azure Active Directory (AAD)를 온-프레미스에서 연결을 사용할 수 있는 모든 Url (내부 및 외부 네임 스페이스 포함) AAD에 등록 되어 있어야 합니다.
  
먼저, AAD에 추가 하는 모든 Url을 수집 합니다. 이러한 명령을 온-프레미스를 실행 합니다.
  
```powershell
Get-MapiVirtualDirectory | FL server,*url*
Get-WebServicesVirtualDirectory | FL server,*url*
Get-ActiveSyncVirtualDirectory | FL server,*url*
Get-OABVirtualDirectory | FL server,*url*
```
    
클라이언트가 수 AAD에서 HTTPS 서비스 사용자 이름으로 나열 된 연결할 Url을 확인 합니다.
  
1. 먼저, [이러한 지침](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell)과 함께 AAD에 연결 합니다. 

 **참고 사항** 아래 명령을 사용할 수 있도록이 페이지에서 Connect-msolservice 옵션을 사용 해야 합니다. 
    
2. Exchange에 대 한 관련된 Url에 다음 명령을 입력 합니다.
    
```powershell
Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 | select -ExpandProperty ServicePrincipalNames
```

https:// *autodiscover.yourdomain.com* 및 https:// *mail.yourdomain.com* URL 포함 되어야 하지만 대개로 시작 하는 Spn을 구성 하는이 명령의 출력을 메모해 두십시오 (및 나중에 비교에 대 한 스크린샷)를 수행 00000002-0000-0ff1-ce00-000000000000 / 합니다. Https:// Url에서 온-프레미스 누락 된 경우이 목록에 해당 특정 레코드를 추가 하는 것이 할 수 있습니다. 
  
3. 아래 명령을 사용 하 여 추가 해야이 목록에 내부 및 외부 MAPI/HTTP, EWS, ActiveSync, OAB 및 자동 검색 레코드 보이지 않으면 (이 예제에서는 Url은 '`mail.corp.contoso.com`'및'`owa.contoso.com`', **자신의 예제 Url을 교체** 했지만) : <br/>
```powershell
$x= Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000   
$x.ServicePrincipalnames.Add("https://mail.corp.contoso.com/")
$x.ServicePrincipalnames.Add("https://owa.contoso.com/")
$x.ServicePrincipalnames.Add("https://eas.contoso.com/")
Set-MSOLServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
```
 
4. 마찬가지로 2 단계에서 Get MsolServicePrincipal 명령을 실행 하 고 출력을 통해을 찾고 추가 된 새 레코드를 확인 합니다. 목록 비교 / Spn (수도 있습니다 스크린샷 새 목록에 레코드에 대 한)의 새 목록에 앞에서 스크린샷. 성공한, 두 새 Url 목록에 표시 됩니다. 이 예제에서 이동, Spn 목록이 이제 포함 됩니다 특정 Url `https://mail.corp.contoso.com` 및 `https://owa.contoso.com`합니다. 
  
## <a name="verify-virtual-directories-are-properly-configured"></a>가상 디렉터리는 제대로 구성 확인

이제 확인 OAuth에서 제대로 설정 되어 Exchange 모든 가상 디렉터리 Outlook에서 다음 명령을 실행 하 여 사용할 수:

```powershell
Get-MapiVirtualDirectory | FL server,*url*,*auth* 
Get-WebServicesVirtualDirectory | FL server,*url*,*oauth*
Get-OABVirtualDirectory | FL server,*url*,*oauth*
Get-AutoDiscoverVirtualDirectory | FL server,*oauth*
```

이러한 VDirs의 각에서 검사 **OAuth** 있는지 확인 하려면 출력을 사용할지, 모양과 동일 하 게 다음과 같이 (이며 살펴보는 것 'OAuth'); 

```powershell
Get-MapiVirtualDirectory | fl server,*url*,*auth*
```

```
Server                        : EX1
InternalUrl                   : https://mail.contoso.com/mapi
ExternalUrl                   : https://mail.contoso.com/mapi
IISAuthenticationMethods      : {Ntlm, OAuth, Negotiate}
InternalAuthenticationMethods : {Ntlm, OAuth, Negotiate}
ExternalAuthenticationMethods : {Ntlm, OAuth, Negotiate}
```
  
OAuth 서버 및 4 개의 가상 디렉터리의 모든에서 누락 된 경우 계속 하기 전에 관련 명령을 사용 하 여 추가 해야 합니다.
  
## <a name="confirm-the-evosts-auth-server-object-is-present"></a>EvoSTS 인증 서버 개체가 있는지 확인 합니다.

이 마지막 명령에 대 한 온-프레미스 Exchange 관리 셸을 반환 합니다. 이제 evoSTS 인증 공급자에 대 한 온-프레미스에 항목이 있는지 확인할 수 있습니다.
  
```powershell
Get-AuthServer | where {$_.Name -eq "EvoSts"}
```

사용자가 출력 한 AuthServer 이름 EvoSts의 표시 및 'Enabled' 상태 True 여야 합니다. 이 표시 되지 않으면를 다운로드 하 고 하이브리드 구성 마법사의 최신 버전을 실행 해야 합니다.
  
 **중요 한** 환경에서 Exchange 2010을 실행 하는 경우에 EvoSTS 인증 공급자를 만들 수 없습니다. 
  
## <a name="enable-hma"></a>HMA를 사용 하도록 설정

온-프레미스 Exchange 관리 셸에서 다음 명령을 실행 합니다.

```powershell
Set-AuthServer -Identity EvoSTS -IsDefaultAuthorizationEndpoint $true  
Set-OrganizationConfig -OAuth2ClientProfileEnabled $true
```
    
## <a name="verify"></a>확인

HMA를 사용 하도록 설정 되 면 클라이언트의 다음 로그인 하는 새 인증 흐름을 사용 합니다. 참고 방금 HMA를 켜서는 다시 인증 하는 모든 클라이언트에 대 한 트리거하지 않습니다. 클라이언트를 다시 인증에 따라 인증 토큰 및/또는 인증서의 수명 동안 갖게 됩니다.
  
또한 Outlook 클라이언트 (도: Windows 알림 트레이)에 대 한 아이콘 마우스 오른쪽 단추로 클릭 하는 동시에 CTRL 키를 누른 하 고 ' 연결 상태 '를 클릭 해야 합니다. 'Authn' 형식에 대해 클라이언트의 SMTP 주소를 찾습니다 ' Bearer\*'를 사용 하 여 OAuth bearer 토큰을 나타냅니다.
  
 **참고 사항** HMA를 사용 하 여 비즈니스를 위한 Skype 구성 해야 합니까? 두 문서를 수행 해야: [지원 되는 토폴로지](https://docs.microsoft.com/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported)를 나열 하 고 하나 [구성 작업을 수행 하는 방법](configure-skype-for-business-for-hybrid-modern-authentication.md)을 보여줍니다.
  

## <a name="related-topics"></a>관련 항목

[하이브리드 현대 인증 개요 및 온-프레미스 Skype를 사용 하 여 비즈니스 및 Exchange 서버에 대 한 필수 구성 요소](hybrid-modern-auth-overview.md) 
  

