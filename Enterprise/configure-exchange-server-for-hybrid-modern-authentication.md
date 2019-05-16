---
title: 하이브리드 최신 인증을 사용하도록 Exchange Server 온-프레미스를 구성하는 방법
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 11/16/2018
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: cef3044d-d4cb-4586-8e82-ee97bd3b14ad
ms.collection:
- M365-security-compliance
description: 하이브리드 최신 인증 (HMA)은 보다 안전한 사용자 인증 및 권한 부여를 제공 하 고 Exchange server 온-프레미스 하이브리드 배포에 사용할 수 있는 id 관리 방법입니다.
ms.openlocfilehash: 98a47f9527b3922767bfd8240790d7cfdeb14936
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068044"
---
# <a name="how-to-configure-exchange-server-on-premises-to-use-hybrid-modern-authentication"></a>하이브리드 최신 인증을 사용하도록 Exchange Server 온-프레미스를 구성하는 방법

하이브리드 최신 인증 (HMA)은 보다 안전한 사용자 인증 및 권한 부여를 제공 하 고 Exchange server 온-프레미스 하이브리드 배포에 사용할 수 있는 id 관리 방법입니다.
  
## <a name="fyi"></a>선택적

시작 하기 전에 다음을 호출 합니다.
  
- 하이브리드 최신 인증 \> HMA
    
- Exchange 온-프레미스 \> exch
    
- Exchange Online \> exo
    
또한 *이 문서의 그래픽에 ' 흐리게 ' 또는 ' 희미하게 ' 개체를 사용 하 여 회색으로 표시 된 요소가 HMA 별 구성에 포함 되지 않음을 의미* 합니다. 
  
## <a name="enabling-hybrid-modern-authentication"></a>하이브리드 최신 인증 사용

HMA를 켜는 방법은 다음과 같습니다.
  
1. 시작 하기 전에 필수 구성 요소을 충족 하는지 확인해 보십시오.
    
1. 대부분의 **필수 구성 요소** 는 비즈니스용 Skype 및 Exchange, [하이브리드 최신 인증 개요 및 온-프레미스 비즈니스용 skype 및 exchange 서버에서 사용 하기 위한 필수 구성 요소](hybrid-modern-auth-overview.md)에 공통 됩니다. 이 문서에 나와 있는 단계를 시작 하기 전에이 작업을 수행 하십시오.
    
2. Azure AD에서 온-프레미스 웹 서비스 Url을 Spn (서비스 사용자 이름)으로 추가
    
3. 모든 가상 디렉터리가 HMA에 사용 되도록 설정
    
4. EvoSTS 인증 서버 개체 확인
    
5. EXCH에서 HMA를 사용 하도록 설정
    
 **참고 사항** Office에서 지원 되는 버전은 무엇입니까? [최신 인증이 Office 2013 및 office 2016 클라이언트 앱에 작동 하는 방식을](modern-auth-for-office-2013-and-2016.md)참조 하세요.
  
## <a name="make-sure-you-meet-all-the-pre-reqs"></a>모든 사전 요구 사항을 충족 해야 합니다.

비즈니스용 Skype 및 Exchange에 대 한 많은 필수 구성 요소가 공통적 이므로 [온-프레미스 비즈니스용 skype 및 exchange 서버에서 하이브리드 최신 인증 개요 및 필수 구성 요소를 사용 하](hybrid-modern-auth-overview.md)는 경우를 참조 하세요. 이 문서에 나와 있는 단계를 시작 *하기 전에* 이 작업을 수행 하십시오. 
  
## <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a>Azure AD에서 온-프레미스 웹 서비스 Url을 Spn으로 추가

온-프레미스 웹 서비스 Url을 Azure AD Spn으로 할당 하는 명령을 실행 합니다. 인증 및 권한 부여 중에는 클라이언트 컴퓨터 및 장치에서 Spn을 사용 합니다. 온-프레미스에서 Azure Active Directory (AAD)에 연결 하는 데 사용할 수 있는 모든 Url은 AAD (내부 및 외부 네임 스페이스가 모두 포함 됨)에 등록 되어야 합니다.
  
먼저 AAD에서 추가 해야 하는 모든 Url을 수집 합니다. 온-프레미스에서 다음 명령을 실행 합니다.
  
```powershell
Get-MapiVirtualDirectory | FL server,*url*
Get-WebServicesVirtualDirectory | FL server,*url*
Get-ActiveSyncVirtualDirectory | FL server,*url*
Get-OABVirtualDirectory | FL server,*url*
```
    
클라이언트가 연결할 수 있는 Url이 AAD에서 HTTPS 서비스 사용자 이름으로 나열 되어 있는지 확인 합니다.
  
1. 먼저 [다음 지침](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell)을 사용 하 여 AAD에 연결 합니다. 

 **참고 사항** 아래 명령을 사용할 수 있으려면이 페이지의 Connect-msolservice 옵션을 사용 해야 합니다. 
    
2. Exchange 관련 Url에 대해 다음 명령을 입력 합니다.
    
```powershell
Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 | select -ExpandProperty ServicePrincipalNames
```

메모 작성 (및 이후 비교)이 명령의 출력에는 https:// *autodiscover.yourdomain.com* 및 Https:// *mail.yourdomain.com* URL이 포함 되어 있지만 대부분의 경우에 시작 하는 spn으로 구성 됩니다. 00000002-0000-0ff1-ce00-000000000000/. 누락 된 https://Url이 있는 경우이 목록에 특정 레코드를 추가 해야 합니다. 
  
3. 이 목록에 내부 및 외부 MAPI/HTTP, EWS, ActiveSync, OAB 및 자동 검색 레코드가 표시 되지 않으면 아래 명령을 사용 하 여 추가 해야 합니다 (예: Url은 '`mail.corp.contoso.com`' 및 '`owa.contoso.com`' 임). **** : <br/>
```powershell
$x= Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000   
$x.ServicePrincipalnames.Add("https://mail.corp.contoso.com/")
$x.ServicePrincipalnames.Add("https://owa.contoso.com/")
$x.ServicePrincipalnames.Add("https://eas.contoso.com/")
Set-MSOLServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
```
 
4. 2 단계에서 (New-msolserviceprincipal 명령을 다시 실행 하 고 출력을 검토 하 여 새 레코드가 추가 되었는지 확인 합니다. 목록/스크린샷에서 새 Spn 목록을 비교 합니다 (레코드의 새 목록을 스크린샷 할 수도 있음). 성공적으로 완료 되 면 목록에 두 개의 새 Url이 표시 됩니다. 예를 들어, Spn 목록에는 이제 특정 Url `https://mail.corp.contoso.com` 과 `https://owa.contoso.com`가 포함 됩니다. 
  
## <a name="verify-virtual-directories-are-properly-configured"></a>가상 디렉터리가 올바르게 구성 되었는지 확인

이제 다음 명령을 실행 하 여 Outlook에서 사용할 수 있는 모든 가상 디렉터리의 Exchange에서 OAuth가 제대로 사용 하도록 설정 되어 있는지 확인 합니다.

```powershell
Get-MapiVirtualDirectory | FL server,*url*,*auth* 
Get-WebServicesVirtualDirectory | FL server,*url*,*oauth*
Get-OABVirtualDirectory | FL server,*url*,*oauth*
Get-AutoDiscoverVirtualDirectory | FL server,*oauth*
```

출력을 확인 하 여 이러한 각 VDirs에 **OAuth** 가 사용 되도록 설정 되어 있는지 확인 하 고,이에 대 한 자세한 내용은 ' OAuth '와 같이 확인 해야 합니다. 

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
  
서버 및 4 개의 가상 디렉터리에서 OAuth가 누락 된 경우 계속 하기 전에 관련 명령을 사용 하 여이를 추가 해야 합니다.
  
## <a name="confirm-the-evosts-auth-server-object-is-present"></a>EvoSTS 인증 서버 개체가 있는지 확인

이 마지막 명령에 대해 온-프레미스 Exchange 관리 셸로 돌아갑니다. 이제 온-프레미스에 evoSTS 인증 공급자에 대 한 항목이 있는지 확인할 수 있습니다.
  
```powershell
Get-AuthServer | where {$_.Name -eq "EvoSts"}
```

출력에는 EvoSts 이름의 AuthServer이 표시 되 고 ' Enabled ' 상태가 True 여야 합니다. 이 표시 되지 않으면 최신 버전의 하이브리드 구성 마법사를 다운로드 하 여 실행 해야 합니다.
  
 **중요** 환경에서 Exchange 2010을 실행 하는 경우 EvoSTS 인증 공급자가 만들어지지 않습니다. 
  
## <a name="enable-hma"></a>HMA 사용

Exchange 관리 셸에서 온-프레미스에 다음 명령을 실행 합니다.

```powershell
Set-AuthServer -Identity EvoSTS -IsDefaultAuthorizationEndpoint $true  
Set-OrganizationConfig -OAuth2ClientProfileEnabled $true
```
    
## <a name="verify"></a>지

HMA를 사용 하도록 설정 하면 클라이언트의 다음 로그인은 새 인증 흐름을 사용 합니다. HMA를 설정 하는 것 만으로도 클라이언트에 대 한 재인증이 트리거되지 않습니다. 클라이언트는 인증 토큰 및/또는 인증서의 수명에 따라 다시 인증 합니다.
  
또한 CTRL 키를 누른 상태로 Outlook 클라이언트 아이콘 (Windows 알림 트레이)을 마우스 오른쪽 단추로 클릭 하 고 ' 연결 상태 '를 클릭 합니다. OAuth에서 사용 되는 전달자 토큰을 나타내는 ' 전달자\*' 유형 (' 인증 ' 형식)에 대해 클라이언트의 SMTP 주소를 찾습니다.
  
 **참고 사항** HMA를 사용 하 여 비즈니스용 Skype를 구성 해야 하나요? [지원 되는 토폴로지](https://docs.microsoft.com/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported)를 나열 하는 문서와 [구성을 수행](configure-skype-for-business-for-hybrid-modern-authentication.md)하는 방법을 보여 주는 두 개의 문서가 필요 합니다.
  

## <a name="related-topics"></a>관련 항목

[하이브리드 최신 인증 개요 및 온-프레미스 비즈니스용 Skype와 Exchange 서버를 사용 하기 위한 필수 구성 요소](hybrid-modern-auth-overview.md) 
  

