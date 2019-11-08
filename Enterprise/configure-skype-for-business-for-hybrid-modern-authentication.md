---
title: 하이브리드 최신 인증을 사용하도록 비즈니스용 Skype 온-프레미스를 구성하는 방법
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/4/2018
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 522d5cec-4e1b-4cc3-937f-293570717bc6
ms.collection:
- M365-security-compliance
description: 최신 인증은 보다 안전한 사용자 인증 및 권한 부여를 제공 하는 id 관리 방법으로, 비즈니스용 skype 서버 온-프레미스 및 Exchange server 온-프레미스에서 사용 가능 하 고, 하이브리드의 wmi for Business 비즈니스를 사용할 수 있습니다.
ms.openlocfilehash: 17079ab5e47e2e739780d3df4a9a523edccda14f
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2019
ms.locfileid: "38029132"
---
# <a name="how-to-configure-skype-for-business-on-premises-to-use-hybrid-modern-authentication"></a>하이브리드 최신 인증을 사용하도록 비즈니스용 Skype 온-프레미스를 구성하는 방법

최신 인증은 보다 안전한 사용자 인증 및 권한 부여를 제공 하는 id 관리 방법으로, 비즈니스용 skype 서버 온-프레미스 및 Exchange server 온-프레미스에서 사용 가능 하 고, 하이브리드의 wmi for Business 비즈니스를 사용할 수 있습니다.
  
 **중요** 최신 인증 (MA)에 대 한 자세한 내용과 회사나 조직에서이를 사용 하는 데 도움이 될 수 있는 이유를 확인 하세요. [이 문서](hybrid-modern-auth-overview.md) 에서 개요를 확인 합니다. MA에서 어떤 비즈니스용 Skype 토폴로지가 지원 되는지 파악 해야 하는 경우 여기에서 문서화 되었습니다. 
  
 **시작 하기 전에**다음을 호출 합니다. 
  
- 최신 인증 \> MA
    
- 하이브리드 최신 인증 \> HMA
    
- Exchange 온-프레미스 \> exch
    
- Exchange Online \> exo
    
- 비즈니스용 Skype 온-프레미스 \> SFB
    
- 및 비즈니스용 Skype Online \> SFBO
    
또한이 문서의 그래픽에 ' 흐리게 ' 또는 ' 희미하게 ' 개체를 사용 하는 경우에는 회색으로 표시 된 요소가 MA 한정 구성에 포함 되어 **있지** 않은 것입니다. * 
  
## <a name="read-the-summary"></a>요약 읽기

이 요약은 프로세스를 실행 하는 동안 손실 될 수 있는 단계에 boils 프로세스를 진행 하는 위치를 추적 하기 위해 전체 검사를 수행 하는 것이 좋습니다.
  
1. 먼저 모든 필수 구성 요소를 충족 하는지 확인 합니다.
    
1. 비즈니스용 Skype 및 Exchange에 대 한 대부분의 **필수 구성 요소** 는 일반적인 것 이므로, [사전 필수 검사 목록에 대 한 개요 문서를 참조](hybrid-modern-auth-overview.md)하세요. 이 문서에 나와 있는 단계를 시작 *하기 전에* 이 작업을 수행 하십시오. 
    
2. 파일 또는 OneNote에서 필요한 HMA 관련 정보를 수집 합니다.
    
3. EXO에 대 한 최신 인증을 사용 하도록 설정 합니다 (아직 설정 되지 않은 경우).
    
4. SFBO에 대 한 최신 인증을 사용 하도록 설정 합니다 (아직 설정 되지 않은 경우).
    
5. Exchange 온-프레미스에 대해 하이브리드 최신 인증을 사용 하도록 설정 합니다.
    
6. 비즈니스용 Skype 온-프레미스에 대해 하이브리드 최신 인증을 사용 하도록 설정 합니다.
    
참고 이러한 단계는 SFB, SFBO, EXCH 및 EXCH에 대해 MA를 설정 하며, 즉 SFB 및 SFBO의 HMA 구성에 참여할 수 있는 모든 제품 (EXCH/EXCH에 대 한 종속성 포함)입니다. 즉, 사용자에 게 하이브리드 (EXO + SFBO, EXO + SFB, EXO + SFBO 또는 EXO + SFB) 중 어떤 부분 에서도 만들어진 사서함이 있는 경우 완성 된 제품은 다음과 같이 표시 됩니다.
  
![혼합 6 비즈니스용 Skype HMA 토폴로지의 경우 네 가지 가능한 위치 모두에서 MA가 설정 됩니다.](media/ab89cdf2-160b-49ac-9b71-0160800acfc8.png)
  
여기에서 볼 수 있듯이 MA를 켜는 네 가지 위치는 다음과 같습니다. 최상의 사용자 환경에서는 이러한 네 가지 위치 모두에 MA를 설정 하는 것이 좋습니다. 이러한 모든 위치에서 MA를 설정할 수 없는 경우 환경에 필요한 위치 에서만 MA를 설정 하도록 단계를 조정 합니다.
  
지원 되는 토폴로지의 [MA가 있는 비즈니스용 Skype에 대 한 지원 가능성 항목](https://technet.microsoft.com/library/mt803262.aspx) 을 참조 하세요. 
  
 **중요** 시작 하기 전에 모든 필수 구성 요소가 충족 되었는지 다시 한 번 확인 합니다. 이 정보는 [여기](hybrid-modern-auth-overview.md)에서 찾을 수 있습니다.
  
## <a name="collect-all-hma-specific-info-youll-need"></a>필요한 모든 HMA 관련 정보 수집

최신 인증을 사용 하기 위한 [필수 구성 요소](hybrid-modern-auth-overview.md) (위의 참고 사항 참조)를 두 번 확인 한 후 앞 단계에서 HMA를 구성 하는 데 필요한 정보를 저장할 파일을 만들어야 합니다. 이 문서에서 사용 되는 예: 
  
- **SIP/SMTP 도메인**
    
  - Ex. contoso.com (Office 365에 페더레이션 됨)
    
- **테 넌 트 ID**
    
  - Office 365 테 넌 트를 나타내는 GUID (contoso.onmicrosoft.com의 로그인)입니다.
    
- **SFB 2015 CU5 웹 서비스 Url**
    
모든 SfB 2015 풀에 배포 된 내부 및 외부 웹 서비스 URL이 필요 합니다. 이러한 사항을 가져오려면 비즈니스용 Skype 관리 셸에서 다음을 실행 합니다.
  
```
Get-CsService -WebServer | Select-Object PoolFqdn, InternalFqdn, ExternalFqdn | FL
```

- Ex. 내https://lyncwebint01.contoso.com
    
- Ex. 외부로https://lyncwebext01.contoso.com
    
Standard Edition 서버를 사용 하는 경우 내부 URL은 비어 있습니다. 이 경우 내부 URL에 대 한 풀 fqdn을 사용 합니다.
  
## <a name="turn-on-modern-authentication-for-exo"></a>EXO에 대 한 최신 인증 설정

[Exchange Online: 최신 인증용으로 테 넌 트를 사용 하도록 설정 하는 방법에 대 한](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx) 지침을 따릅니다.
  
## <a name="turn-on-modern-authentication-for-sfbo"></a>SFBO에 대 한 최신 인증 설정

[비즈니스용 Skype Online: 최신 인증용으로 테 넌 트를 사용 하도록 설정](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx)합니다.
  
## <a name="turn-on-hybrid-modern-authentication-for-exchange-on-premises"></a>Exchange 온-프레미스에 대해 하이브리드 최신 인증을 사용 하도록 설정

여기서 설명 하는 지침에 따라 [하이브리드 최신 인증을 사용 하도록 Exchange Server 온-프레미스를 구성 하는 방법을 설명](configure-exchange-server-for-hybrid-modern-authentication.md)합니다.
  
## <a name="turn-on-hybrid-modern-authentication-for-skype-for-business-on-premises"></a>비즈니스용 Skype 온-프레미스에 대해 하이브리드 최신 인증을 사용 하도록 설정

### <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a>Azure AD에서 온-프레미스 웹 서비스 Url을 Spn으로 추가

이제 SFBO에서 서비스 주체로 이전에 수집한 Url을 추가 하기 위한 명령을 실행 해야 합니다.
  
 **참고 사항** Spn (서비스 사용자 이름)은 웹 서비스를 식별 하 고이를 보안 주체 (예: 계정 이름 또는 그룹)와 연결 하 여 인증 된 사용자를 대신 하 여 서비스를 수행할 수 있도록 합니다. 서버에 인증 하는 클라이언트는 Spn에 포함 된 정보를 사용 합니다. 
  
1. 먼저 [다음 지침](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-1.0)을 사용 하 여 AAD에 연결 합니다.
    
2. 온-프레미스에서이 명령을 실행 하 여 SFB 웹 서비스 Url의 목록을 가져옵니다.

   AppPrincipalId는로 `00000004`시작 합니다. 이는 비즈니스용 Skype Online에 해당 합니다.
    
   메모 작성 및 현재 상태 URL을 포함 하는이 명령의 출력이 며, 대부분은로 `00000004-0000-0ff1-ce00-000000000000/`시작 하는 spn으로 구성 됩니다.
    
```
Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 | Select -ExpandProperty ServicePrincipalNames
```
    
3. https://lyncwebint01.contoso.com 예 https://lyncwebext01.contoso.com) 를 들어 온-프레미스의 내부 **또는** 외부 SFB url이 없는 경우에는이 목록에 특정 레코드를 추가 해야 합니다. 
    
    아래의 *예제 url* 을 추가 명령에 있는 실제 url로 바꿔야 합니다. 
  
```  
$x= Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000
$x.ServicePrincipalnames.Add("https://lyncwebint01.contoso.com/")
$x.ServicePrincipalnames.Add("https://lyncwebext01.contoso.com/")
Set-MSOLServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
```
  
4. 2 단계에서 (New-msolserviceprincipal 명령을 다시 실행 하 고 출력을 검토 하 여 새 레코드가 추가 되었는지 확인 합니다. 목록/스크린샷에서 새 Spn 목록을 비교 합니다 (레코드의 새 목록을 스크린샷 할 수도 있음). 성공적으로 완료 되 면 목록에 두 개의 새 Url이 표시 됩니다. 예를 들어, Spn 목록에는 이제 특정 Url https://lyncwebint01.contoso.com 과 https://lyncwebext01.contoso.com/가 포함 됩니다.
    
### <a name="create-the-evosts-auth-server-object"></a>EvoSTS 인증 서버 개체 만들기

비즈니스용 Skype 관리 셸에서 다음 명령을 실행 합니다.
  
```
New-CsOAuthServer -Identity evoSTS -MetadataURL https://login.windows.net/common/FederationMetadata/2007-06/FederationMetadata.xml -AcceptSecurityIdentifierInformation $true -Type AzureAD
```
    
### <a name="enable-hybrid-modern-authentication"></a>하이브리드 최신 인증 사용

실제로 MA를 설정 하는 단계입니다. 클라이언트 인증 흐름을 변경 하지 않고 앞의 모든 단계를 미리 실행할 수 있습니다. 인증 흐름을 변경할 준비가 되 면 비즈니스용 Skype 관리 셸에서이 명령을 실행 합니다. 
  
```
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity evoSTS
```
    
## <a name="verify"></a>지

HMA를 사용 하도록 설정 하면 클라이언트의 다음 로그인은 새 인증 흐름을 사용 합니다. HMA를 설정 하는 것 만으로도 클라이언트에 대 한 재인증이 트리거되지 않습니다. 클라이언트는 인증 토큰 및/또는 인증서의 수명에 따라 다시 인증 합니다.
  
해당 HMA가 사용 하도록 설정한 후에 작동 하는지 테스트 하려면 테스트 SFB Windows 클라이언트에서 로그 아웃 하 고 ' 내 자격 증명 삭제 '를 클릭 해야 합니다. 다시 로그인 합니다. 이제 클라이언트에서 최신 인증 흐름을 사용 하 고 있으며, 클라이언트가 서버에 연결 하 여 로그인 하기 바로 전에 확인 된 ' 회사 또는 학교 ' 계정에 대 한 **Office 365** 프롬프트를 포함 합니다. 
  
' OAuth 기관 '에 대 한 비즈니스용 Skype 클라이언트의 ' 구성 정보 '도 확인 해야 합니다. 클라이언트 컴퓨터에서이 작업을 수행 하려면 CTRL 키를 누른 상태에서 Windows 알림 트레이에서 비즈니스용 Skype 아이콘을 마우스 오른쪽 단추로 클릭 합니다. 나타나는 메뉴에서 구성 정보를 클릭 합니다. 바탕 화면에 표시 되는 ' 비즈니스용 Skype 구성 정보 ' 창에서 다음을 찾습니다.
  
![최신 인증을 사용 하는 비즈니스용 Skype 클라이언트의 구성 정보에는의 https://login.windows.net/common/oauth2/authorizeLYNC 및 EWS OAUTH 인증 기관 URL이 표시 됩니다.](media/4e54edf5-c8f8-4e7f-b032-5d413b0232de.png)
  
또한 CTRL 키를 누른 상태로 Outlook 클라이언트 아이콘 (Windows 알림 트레이)을 마우스 오른쪽 단추로 클릭 하 고 ' 연결 상태 '를 클릭 합니다. OAuth에서 사용 되는 전달자 토큰을 나타내는 ' 전달자\*' 유형의 인증 유형에 대해 클라이언트의 SMTP 주소를 찾습니다.
  
## <a name="related-articles"></a>관련 문서

[최신 인증 개요에 다시 연결](hybrid-modern-auth-overview.md) 합니다. 
  
비즈니스용 Skype 클라이언트에 대해 ADAL (최신 인증)을 사용 하는 방법을 알고 있어야 하나요? [여기](https://technet.microsoft.com/library/mt710548.aspx)에는 단계가 있습니다.
  
SFB 없이 실행 되는 Exchange Server 온-프레미스에 대해 이러한 단계를 읽어 보 시겠습니까? 이러한 단계는 여기에서 사용할 수 있습니다.
  

