---
title: SharePoint Server 인증에 Azure AD를 사용
ms.author: tracyp
author: MSFTTracyP
ms.reviewer: kirke, josephd, kirks
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Ent_O365_Hybrid
ms.custom: Ent_Solutions
ms.assetid: ''
description: '요약: Azure 액세스 제어 서비스를 우회 하 고 SAML 1.1을 사용 하 여 SharePoint Server 사용자를 Azure Active Directory에 인증 하는 방법에 대해 알아봅니다.'
ms.openlocfilehash: c2c9f33aa5e095a8b7fdde08e80cb1a61e88f3eb
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070794"
---
# <a name="using-azure-ad-for-sharepoint-server-authentication"></a>SharePoint Server 인증에 Azure AD를 사용

 **요약:** Azure Active Directory를 사용 하 여 SharePoint Server 2016 사용자를 인증 하는 방법을 알아봅니다. 

<blockquote>
<p>이 문서에서는 Azure Active Directory Graph와 상호 작용 하는 코드 예제를 참조 합니다. [여기](https://github.com/kaevans/spsaml11/tree/master/scripts)에서 코드 예제를 다운로드할 수 있습니다.</p>
</blockquote>

SharePoint Server 2016에서는 클레임 기반 인증을 사용 하 여 사용자를 인증할 수 있는 기능을 제공 하므로 신뢰할 수 있지만 다른 사용자가 관리 하는 다양 한 id 공급자를 사용 하 여 사용자를 인증 하 여 쉽게 관리할 수 있습니다. 예를 들어 AD DS (Active Directory 도메인 서비스)를 통해 사용자 인증을 관리 하는 대신 azure AD (Active directory)를 사용 하 여 인증을 사용 하도록 설정할 수 있습니다. 이렇게 하면 사용자 이름에 onmicrosoft.com 접미사가 있는 클라우드 전용 사용자의 인증을 사용할 수 있으며,이는 온-프레미스 디렉터리와 동기화 되며 다른 디렉터리에서 게스트 사용자에 게 초대 됩니다. 또한 다단계 인증 및 고급 보고 기능과 같은 Azure AD 기능을 활용할 수 있습니다.

> [!IMPORTANT]
> 이 문서에서 설명 하는 해결 방법은 SharePoint Server 2013 에서도 사용할 수 있습니다. 그러나 SharePoint Server 2013은 기본 지원의 끝에 가까워졌습니다. 자세한 내용은 [Microsoft 수명 주기 정책](https://support.microsoft.com/en-us/lifecycle/search?alpha=SharePoint%20Server%202013) 및 [업데이트 된 제품 서비스 정책 SharePoint 2013](https://technet.microsoft.com/library/684173bb-e90a-4eb7-b268-b8d7458bc802(v=office.16).aspx)를 참조 하세요.

이 문서에서는 온-프레미스 AD DS 대신 Azure AD를 사용 하 여 사용자를 인증 하는 방법에 대해 설명 합니다. 이 구성에서 Azure AD는 SharePoint Server 2016에 대 한 신뢰할 수 있는 id 공급자가 됩니다. 이 구성은 SharePoint Server 2016 설치 자체에서 사용 하는 AD DS 인증과는 별개의 사용자 인증 방법을 추가 합니다. 이 문서의 이점을 활용 하려면 WS-FEDERATION에 익숙해야 합니다. 자세한 내용은 [WS-페더레이션 이해](https://go.microsoft.com/fwlink/p/?linkid=188052)를 참조 하세요. Azure Active Directory를 사용 하 여 SharePoint 온-프레미스를 통합 하는 방법에 대 한 자세한 내용은 [전용 자습서](https://docs.microsoft.com/azure/active-directory/saas-apps/sharepoint-on-premises-tutorial)를 참조 하세요.

![SharePoint 인증에 Azure AD 사용](media/SAML11/fig1-architecture.png)

이전에는이 구성에 필요한 페더레이션 서비스 (클라우드의 ACS (액세스 제어 서비스) 또는 AD FS (Active Directory Federation Services)를 호스트 하 여 SAML 2.0에서 SAML 1.1로 토큰을 변환 하는 환경을 필요로 합니다. 이제 Azure AD에서 SAML 1.1 토큰 발급을 사용 하도록 설정 하면이 변환이 더 이상 필요 하지 않습니다. 위의 다이어그램은이 구성에서 SharePoint 2016 사용자에 대 한 인증이 작동 하는 방법을 보여 주며, 중개자가이 변환을 수행 하는 데 더 이상 필요 하지 않음을 보여 줍니다.

> [!NOTE]
> 이 구성은 SharePoint 팜이 Azure virtual machine 또는 온-프레미스에 호스트 되어 있는지 여부에 따라 작동 합니다. 사용자가 브라우저에서 Azure Active Directory에 액세스할 수 있도록 하는 것 외에는 추가 방화벽 포트를 열 필요가 없습니다.

SharePoint 2016 내게 필요한 옵션에 대 한 자세한 내용은 [Sharepoint Server 2016의 내게 필요한 옵션 지침](https://go.microsoft.com/fwlink/p/?LinkId=393123)을 참조 하세요.

## <a name="configuration-overview"></a>구성 개요

다음의 일반적인 단계에 따라 Azure AD를 SharePoint Server 2016 id 공급자로 사용 하도록 환경을 설정 합니다.

1. 새 Azure AD 디렉터리를 만들거나 기존 디렉터리를 사용 합니다.
2. Azure AD를 사용 하 여 보안을 유지할 웹 응용 프로그램의 영역이 SSL을 사용 하도록 구성 되어 있는지 확인 합니다.
3. Azure AD에서 새 엔터프라이즈 응용 프로그램을 만듭니다.
4. SharePoint Server 2016에서 신뢰할 수 있는 id 공급자를 새로 구성 합니다.
5. 웹 응용 프로그램에 대 한 사용 권한을 설정 합니다.
6. Azure AD에서 SAML 1.1 토큰 발급 정책을 추가 합니다.
7. 새 공급자를 확인 합니다.

다음 섹션에서는 이러한 작업을 수행 하는 방법에 대해 설명 합니다.

## <a name="step-1-create-a-new-azure-ad-directory-or-use-your-existing-directory"></a>1 단계: 새 Azure AD 디렉터리를 만들거나 기존 디렉터리를 사용 합니다.

Azure Portal ([https://portal.azure.com](https://portal.azure.com))에서 새 디렉터리를 만듭니다. 조직 이름, 초기 도메인 이름 및 국가 또는 지역을 제공 합니다.

![디렉터리 만들기](media/SAML11/fig2-createdirectory.png) 

 Microsoft Office 365 또는 Microsoft Azure 구독에 사용 되는 것과 같은 디렉터리가 이미 있는 경우에는 해당 디렉터리를 대신 사용할 수 있습니다. 디렉터리에 응용 프로그램을 등록할 수 있는 권한이 있어야 합니다.

## <a name="step-2-ensure-the-zone-for-the-web-application-that-you-want-to-secure-with-azure-ad-is-configured-to-use-ssl"></a>2 단계: Azure AD를 사용 하 여 보안을 유지 하려는 웹 응용 프로그램의 영역이 SSL을 사용 하도록 구성 되어 있는지 확인

이 문서는 [Azure에서 고가용성 SharePoint Server 2016 팜 실행](https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/sharepoint)의 참조 아키텍처를 사용 하 여 작성 되었습니다. [이 문서](https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/sharepoint) 에서 설명 하는 솔루션을 배포 하는 데 사용 되는 문서와 함께 제공 되는 스크립트는 SSL을 사용 하지 않는 사이트를 만듭니다.  

SAML를 사용 하려면 응용 프로그램이 SSL을 사용 하도록 구성 되어 있어야 합니다. SharePoint 웹 응용 프로그램이 SSL을 사용 하도록 구성 되지 않은 경우 다음 단계를 수행 하 여 SSL에 맞게 웹 응용 프로그램을 구성할 새 자체 서명 된 인증서를 만듭니다. 이 구성은 랩 환경에만 사용 되 고 프로덕션에 사용 하기 위한 것이 아닙니다. 프로덕션 환경에서는 서명 된 인증서를 사용 해야 합니다.

1. **중앙 관리** > **응용 프로그램 관리** > 로 이동 하 여**웹 응용 프로그램 관리**를 수행 하 고 SSL을 사용 하도록 확장 해야 하는 웹 응용 프로그램을 선택 합니다. 웹 응용 프로그램을 선택 하 고 **리본 메뉴 확장** 단추를 클릭 합니다. 웹 응용 프로그램을 확장 하 여 동일한 URL을 사용 하지만 SSL을 포트 443와 함께 사용 합니다.<br/>![다른 IIS 사이트로 웹 응용 프로그램 확장](media/SAML11/fig3-extendwebapptoiis.png)<br/>
2. IIS 관리자에서 **서버 인증서**를 두 번 클릭 합니다.
3. **동작** 창에서 **자체 서명된 인증서 만들기**를 클릭합니다. 인증서 이름 지정 상자에 인증서의 이름을 입력 하 고 **확인**을 클릭 합니다.
4. **사이트 바인딩 편집** 대화 상자에서 다음 이미지에 나와 있는 것 처럼 호스트 이름이 친숙 한 이름과 동일한 지 확인 합니다.<br/>![IIS에서 사이트 바인딩 편집](media/SAML11/fig4-editsitebinding.png)<br/>

SharePoint 팜의 각 웹 프런트 엔드 서버는 IIS에서 사이트 바인딩에 대 한 인증서를 구성 해야 합니다.


## <a name="step-3-create-a-new-enterprise-application-in-azure-ad"></a>3 단계: Azure AD에서 새 엔터프라이즈 응용 프로그램 만들기

1. Azure Portal ([https://portal.azure.com](https://portal.azure.com))에서 azure AD 디렉터리를 엽니다. **엔터프라이즈 응용 프로그램**을 클릭 한 다음 **새 응용 프로그램**을 클릭 합니다. **비 갤러리 응용 프로그램**을 선택 합니다. *SHAREPOINT SAML 통합과* 같은 이름을 지정 하 고 **추가**를 클릭 합니다.<br/>![새 비 갤러리 응용 프로그램 추가](media/SAML11/fig5-addnongalleryapp.png)<br/>
2. 탐색 창에서 Single sign-on 링크를 클릭 하 여 응용 프로그램을 구성 합니다. **Single Sign-on 모드** 드롭다운을 **saml 기반 로그온** 으로 변경 하 여 응용 프로그램에 대 한 SAML 구성 속성을 표시 합니다. 다음 속성을 사용 하 여 구성 합니다.<br/>
    - 한정자`urn:sharepoint:portal.contoso.local`
    - 회신 URL:`https://portal.contoso.local/_trust/default.aspx`
    - 로그온 URL:`https://portal.contoso.local/_trust/default.aspx`
    - 사용자 식별자:`user.userprincipalname`<br/>
    - 참고: 보안을 설정할 SharePoint 사이트의 URL ** 을 사용 하 여 url을 변경 해야 합니다.<br/>
3. 다음 행을 포함 하는 표 (아래 표 1과 비슷함)를 설정 합니다.<br/> 
    - Realm
    - SAML 서명 인증서 파일의 전체 경로입니다.
    - SAML Sso (Single Sign-on service) URL (대체 */pr2* with */pr급지됨*)
    - 응용 프로그램 개체 ID입니다. <br/>
*Realm* 속성의 *식별자* 값을 테이블에 복사 합니다 (아래의 표 1 참조).
4. 변경 내용을 저장합니다.
5. **구성 (앱 이름)** 링크를 클릭 하 여 sign-on 구성 페이지에 액세스 합니다.<br/>![Single sign on 페이지 구성](media/SAML11/fig7-configssopage.png)<br/> 
    -  Saml 서명 **인증서-Raw** 링크를 클릭 하 여 Saml 서명 인증서를 .cer 확장명을 가진 파일로 다운로드 합니다. 다운로드 한 파일의 전체 경로를 테이블에 복사 하 여 붙여넣습니다.
    - SAML Single Sign-on 서비스 URL 링크를 복사 하 여에 붙여 넣고 ( */tr급지됨*로 URL의 */p22* 부분을 교체 합니다.<br/>
6.  응용 프로그램의 **속성** 창으로 이동 합니다. 3 단계에서 설정한 테이블에 개체 ID 값을 복사 하 여 붙여 넣습니다.<br/>![응용 프로그램의 속성 창](media/SAML11/fig8-propertiespane.png)<br/>
7. 캡처한 값을 사용 하 여 3 단계에서 설정한 테이블이 아래 표 1과 같은지 확인 합니다.


| 표 1: 캡처된 값  |  |
|---------|---------|
|Realm | `urn:sharepoint:portal.contoso.local` |
|SAML 서명 인증서 파일의 전체 경로입니다. | `C:/temp/SharePoint SAML Integration.cer`  |
|SAML single sign-on 서비스 URL (replace/pr2 with/pr급지됨) | `https://login.microsoftonline.com/b1726649-b616-460d-8d20-defab80d476c/wsfed` |
|응용 프로그램 개체 ID | `a812f48b-d1e4-4c8e-93be-e4808c8ca3ac` |

> [!IMPORTANT]
> */Tr급지됨*URL의 */p22* 값을 바꿉니다. */P22* 끝점은 SAML 2.0 토큰을 처리 합니다. */Pr급지됨* 끝점은 saml 1.1 토큰을 처리할 수 있도록 하며 SHAREPOINT 2016 SAML 페더레이션에 필요 합니다.

## <a name="step-4-configure-a-new-trusted-identity-provider-in-sharepoint-server-2016"></a>4 단계: SharePoint Server 2016에서 신뢰할 수 있는 새 id 공급자 구성

SharePoint Server 2016 서버에 로그인 하 고 SharePoint 2016 관리 셸을 엽니다. 테이블 1의 $realm, $wsfedurl 및 $filepath 값을 입력 하 고 다음 명령을 실행 하 여 새 신뢰할 수 있는 id 공급자를 구성 합니다.

> [!TIP]
> PowerShell을 처음 사용 하는 경우 또는 PowerShell 작동 방식에 대해 자세히 알아보려면 [SharePoint PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/overview?view=sharepoint-ps)을 참조 하세요. 

```
$realm = "<Realm from Table 1>"
$wsfedurl="<SAML single sign-on service URL from Table 1>"
$filepath="<Full path to SAML signing certificate file from Table 1>"
$cert = New-Object System.Security.Cryptography.X509Certificates.X509Certificate2($filepath)
New-SPTrustedRootAuthority -Name "AzureAD" -Certificate $cert
$map = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" -IncomingClaimTypeDisplayName "name" -LocalClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/upn"
$map2 = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname" -IncomingClaimTypeDisplayName "GivenName" -SameAsIncoming
$map3 = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname" -IncomingClaimTypeDisplayName "SurName" -SameAsIncoming
$ap = New-SPTrustedIdentityTokenIssuer -Name "AzureAD" -Description "SharePoint secured by Azure AD" -realm $realm -ImportTrustCertificate $cert -ClaimsMappings $map,$map2,$map3 -SignInUrl $wsfedurl -IdentifierClaim "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name"
```

다음으로, 다음 단계에 따라 응용 프로그램에 대해 신뢰할 수 있는 id 공급자를 사용 하도록 설정 합니다.
1. 중앙 관리에서 **웹 응용 프로그램 관리** 로 이동 하 고 Azure AD를 사용 하 여 보호할 웹 응용 프로그램을 선택 합니다. 
2. 리본 메뉴에서 **인증 공급자** 를 클릭 하 고 사용할 영역을 선택 합니다.
3. **신뢰할 수 있는 id 공급자** 를 선택 하 고 방금 등록 한 *AzureAD*이라는 식별 공급자를 선택 합니다.  
4. 로그인 페이지 URL 설정에서 **사용자 지정 로그인 페이지** 를 선택 하 고 값을 "/_trust/"로 지정 합니다. 
5. **확인**을 클릭합니다.

![인증 공급자 구성](media/SAML11/fig10-configauthprovider.png)

> [!IMPORTANT]
> 표시 된 대로 사용자 지정 로그인 페이지를 "/_trust/"로 설정 하는 것을 포함 하 여 모든 단계를 수행 하는 것이 중요 합니다. 모든 단계를 따르지 않으면 구성이 제대로 작동 하지 않습니다.

## <a name="step-5-set-the-permissions"></a>5 단계: 사용 권한 설정

Azure AD에 로그인 하 고 SharePoint에 액세스 하는 사용자에 게 응용 프로그램에 대 한 액세스 권한을 부여 해야 합니다. 

1. Azure Portal에서 Azure AD 디렉터리를 엽니다. **엔터프라이즈 응용 프로그램**을 클릭 한 다음 **모든 응용 프로그램**을 클릭 합니다. 이전에 만든 응용 프로그램 (SharePoint SAML 통합)을 클릭 합니다.
2. **사용자 및 그룹을**클릭 합니다. 
3. **사용자 추가** 를 클릭 하 여 Azure AD를 사용 하 여 SharePoint에 로그인 할 수 있는 권한이 있는 사용자 또는 그룹을 추가 합니다.
4. 사용자 또는 그룹을 선택 하 고 **할당**을 클릭 합니다.
 
사용자에 게 Azure AD에 대 한 권한이 부여 되었지만 SharePoint에서 사용 권한을 부여 받아야 합니다. 다음 단계에 따라 웹 응용 프로그램에 액세스 하는 데 필요한 사용 권한을 설정 합니다.

1. 중앙 관리에서 **응용 프로그램 관리**를 클릭합니다.
2. **응용 프로그램 관리** 페이지의 **웹 응용 프로그램** 섹션에서 **웹 응용 프로그램 관리**를 클릭합니다.
3. 적절 한 웹 응용 프로그램을 클릭 한 다음 **사용자 정책을**클릭 합니다.
4. 웹 응용 프로그램 정책에서 **사용자 추가**를 클릭 합니다.<br/>![이름 클레임에 따라 사용자 검색](media/SAML11/fig11-searchbynameclaim.png)<br/>
5. **사용자 추가** 대화 상자의 **영역**에서 해당 영역을 클릭 하 고 **다음**을 클릭 합니다.
6. **웹 응용 프로그램 정책** 대화 상자의 **사용자 선택** 섹션에서 **찾아보기** 아이콘을 클릭 합니다.
7. **찾기** 텍스트 상자에 디렉터리에 있는 사용자의 로그인 이름을 입력 하 고 **검색**을 클릭 합니다. <br/>예: *demouser@blueskyabove.onmicrosoft.com*.
8. 목록 보기의 AzureAD 머리글 아래에 있는 name 속성을 선택 하 고 **추가** 를 클릭 한 다음 **확인** 을 클릭 하 여 대화 상자를 닫습니다.
9. 사용 권한에서 **모든**권한을 클릭 합니다.<br/>![클레임 사용자에 게 모든 권한 부여](media/SAML11/fig12-grantfullcontrol.png)<br/>
10. **마침**, **확인**을 차례로 클릭합니다.

## <a name="step-6-add-a-saml-11-token-issuance-policy-in-azure-ad"></a>6 단계: Azure AD에서 SAML 1.1 토큰 발급 정책 추가

포털에서 Azure AD 응용 프로그램을 만들면 기본적으로 SAML 2.0을 사용 하 게 됩니다. SharePoint Server 2016에는 SAML 1.1 토큰 형식이 필요 합니다. 다음 스크립트는 기본 SAML 2.0 정책을 제거 하 고 SAML 1.1 토큰을 발급 하는 새 정책을 추가 합니다. 

> 이 코드를 사용 하려면 [Azure Active Directory Graph와 상호 작용 하는 방법을 보여 주는 샘플](https://github.com/kaevans/spsaml11/tree/master/scripts)을 다운로드 해야 합니다. GitHub에서 Windows 데스크톱으로 스크립트를 ZIP 파일로 다운로드 하는 경우 `MSGraphTokenLifetimePolicy.psm1` script module 파일과 `Initialize.ps1` 스크립트 파일 (속성을 마우스 오른쪽 단추로 클릭 하 고, 차단 해제, 확인을 차례로 클릭)의 차단을 해제 해야 합니다. 
![다운로드 한 파일 차단 해제](media/SAML11/fig17-unblock.png)

예제 스크립트를 다운로드 한 후에는 다음 코드를 사용 하 여 새 PowerShell 스크립트를 만들고 로컬 컴퓨터에 다운로드 `Initialize.ps1` 한 파일 경로로 자리 표시자를 대체 합니다. 응용 프로그램 개체 ID 자리 표시자를 표 1에 입력 한 응용 프로그램 개체 ID로 바꿉니다. 만든 후에는 PowerShell 스크립트를 실행 합니다. 

```
function AssignSaml11PolicyToAppPrincipal
{
    Param(
        [Parameter(Mandatory=$true)]
        [string]$pathToInitializeScriptFile, 
        [Parameter(Mandatory=$true)]
        [string]$appObjectid
    )

    $folder = Split-Path $pathToInitializeScriptFile
    Push-Location $folder

    #Loads the dependent ADAL module used to acquire tokens
    Import-Module $pathToInitializeScriptFile 

    #Gets the existing token issuance policy
    $existingTokenIssuancePolicy = Get-PoliciesAssignedToServicePrincipal -servicePrincipalId $appObjectid | ?{$_.type -EQ "TokenIssuancePolicy"} 
    Write-Host "The following TokenIssuancePolicy policies are assigned to the service principal." -ForegroundColor Green
    Write-Host $existingTokenIssuancePolicy -ForegroundColor White
    $policyId = $existingTokenIssuancePolicy.objectId

    #Removes existing token issuance policy
    Write-Host "Only a single policy can be assigned to the service principal. Removing the existing policy with ID $policyId" -ForegroundColor Green
    Remove-PolicyFromServicePrincipal -policyId $policyId -servicePrincipalId $appObjectid

    #Creates a new token issuance policy and assigns to the service principal
    Write-Host "Adding the new SAML 1.1 TokenIssuancePolicy" -ForegroundColor Green
    $policy = Add-TokenIssuancePolicy -DisplayName SPSAML11 -SigningAlgorithm "http://www.w3.org/2001/04/xmldsig-more#rsa-sha256" -TokenResponseSigningPolicy TokenOnly -SamlTokenVersion "1.1"
    Write-Host "Assigning the new SAML 1.1 TokenIssuancePolicy $policy.objectId to the service principal $appObjectid" -ForegroundColor Green
    Set-PolicyToServicePrincipal -policyId $policy.objectId -servicePrincipalId $appObjectid
    Pop-Location
}

#Only edit the following two variables
$pathToInitializeScriptFile = "<file path of Initialize.ps1>"
$appObjectid = "<Application Object ID from Table 1>"

AssignSaml11PolicyToAppPrincipal $pathToInitializeScriptFile $appObjectid
```
> [!IMPORTANT]
> PowerShell 스크립트는 서명 되지 않으며 실행 정책을 설정 하 라는 메시지가 표시 될 수 있습니다. 실행 정책에 대 한 자세한 내용은 [실행 정책 정보](http://go.microsoft.com/fwlink/?LinkID=135170)를 참조 하십시오. 또한 예제 스크립트에 포함 된 명령을 성공적으로 실행 하려면 관리자 권한 명령 프롬프트를 열어야 할 수도 있습니다.

다음 예제 PowerShell 명령에는 Graph API에 대해 쿼리를 실행 하는 방법에 대 한 예가 나와 있습니다. Azure AD를 사용한 토큰 발급 정책에 대 한 자세한 내용은 [policy에 대 한 작업에 대 한 GRAPH API 참조](https://msdn.microsoft.com/en-us/library/azure/ad/graph/api/policy-operations#create-a-policy)를 참조 하십시오.

## <a name="step-7-verify-the-new-provider"></a>7 단계: 새 공급자 확인

이전 단계에서 구성한 웹 응용 프로그램의 URL에 대 한 브라우저를 엽니다. Azure AD에 로그인 하기 위해 리디렉션됩니다.

![페더레이션을 위해 구성 된 Azure AD에 로그인](media/SAML11/fig13-examplesignin.png)

로그인 상태를 유지할 것인지 묻는 메시지가 나타납니다.

![로그인 상태를 유지 하 시겠습니까?](media/SAML11/fig14-staysignedin.png)

마지막으로 Azure Active Directory 테 넌 트에서 사용자로 로그인 한 사이트에 액세스할 수 있습니다.

![SharePoint에 로그인 한 사용자](media/SAML11/fig15-signedinsharepoint.png)

## <a name="managing-certificates"></a>인증서 관리
위의 4 단계에서 신뢰할 수 있는 id 공급자에 대해 구성 된 서명 인증서에 만료 날짜가 있는지 이해 하 고 있어야 합니다. 인증서 갱신에 대 한 자세한 내용은 [Azure Active Directory에서 페더레이션된 single sign-on 인증서 관리](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-sso-certs) 문서를 참조 하세요. Azure AD에서 인증서가 갱신 되 면 로컬 파일에 다운로드 하 고 다음 스크립트를 사용 하 여 갱신 된 서명 인증서로 신뢰할 수 있는 id 공급자를 구성 합니다. 

```
$filepath="<Full path to renewed SAML signing certificate file>"
$cert= New-Object System.Security.Cryptography.X509Certificates.X509Certificate2($filePath)
New-SPTrustedRootAuthority -Name "AzureAD" -Certificate $cert
Get-SPTrustedIdentityTokenIssuer "AzureAD" | Set-SPTrustedIdentityTokenIssuer -ImportTrustCertificate $cert
```
## <a name="configuring-one-trusted-identity-provider-for-multiple-web-applications"></a>여러 웹 응용 프로그램에 대해 신뢰할 수 있는 id 공급자 하나 구성
구성은 단일 웹 응용 프로그램에서 작동 하지만, 여러 웹 응용 프로그램에 대해 동일한 신뢰할 수 있는 id 공급자를 사용 하려는 경우에는 추가 구성이 필요 합니다. 예를 들어, URL `https://portal.contoso.local` 을 사용 하 여 사용자를 `https://sales.contoso.local` 인증 하기 위해 웹 응용 프로그램을 확장 했다고 가정 합시다. 이 작업을 수행 하려면 WReply 매개 변수를 적용 하 고 Azure AD에서 응용 프로그램 등록을 업데이트 하 여 회신 URL을 추가 하도록 id 공급자를 업데이트 해야 합니다.

1. Azure Portal에서 Azure AD 디렉터리를 엽니다. **앱 등록**을 클릭 하 고 **모든 응용 프로그램 보기**를 클릭 합니다. 이전에 만든 응용 프로그램 (SharePoint SAML 통합)을 클릭 합니다.
2. **설정을**클릭 합니다.
3. 설정 블레이드에서 **응답 url**을 클릭 합니다. 
4. URL에 추가 된 추가 웹 응용 프로그램 `/_trust/default.aspx` 의 url (예: `https://sales.contoso.local/_trust/default.aspx`)을 추가 하 고 **저장**을 클릭 합니다. 
5. SharePoint 서버에서 **sharepoint 2016 관리 셸을** 열고 이전에 사용한 신뢰할 수 있는 id 토큰 발급자의 이름을 사용 하 여 다음 명령을 실행 합니다.

```
$t = Get-SPTrustedIdentityTokenIssuer "AzureAD"
$t.UseWReplyParameter=$true
$t.Update()
```
6. 중앙 관리에서 웹 응용 프로그램으로 이동 하 여 기존의 신뢰할 수 있는 id 공급자를 사용 하도록 설정 합니다. 로그인 페이지 URL을 사용자 지정 로그인 페이지로 `/_trust/`도 구성 해야 합니다.
7. 중앙 관리에서 웹 응용 프로그램을 클릭 하 고 **사용자 정책을**선택 합니다. 이 문서의 앞부분에서 설명한 대로 적절 한 사용 권한이 있는 사용자를 추가 합니다.

## <a name="fixing-people-picker"></a>사용자 선택 수정
이제 사용자가 Azure AD의 id를 사용 하 여 SharePoint 2016에 로그인 할 수 있지만, 사용자 환경 개선에 대 한 기회는 여전히 제공 됩니다. 예를 들어 사용자를 검색 하면 여러 검색 결과가 사용자 선택에 표시 됩니다. 클레임 매핑에서 만든 3 개의 클레임 유형 각각에 대 한 검색 결과가 있습니다. 사용자 선택 기능을 사용 하 여 한 명을 선택한 후에는 사용자 이름을 정확히 입력 하 고 **이름** 클레임 결과를 선택 해야 합니다.

![검색 결과 클레임](media/SAML11/fig16-claimssearchresults.png)

검색 하는 값에 대 한 유효성 검사를 수행 하지 않고, 맞춤법 오류가 발생 하거나 잘못 된 클레임 유형을 실수로 선택 하 여 **성** 클레임 등을 할당할 수 없습니다. 이로 인해 사용자가 리소스에 성공적으로 액세스 하지 못할 수 있습니다.

이 시나리오를 지원 하기 위해 SharePoint 2016에 대 한 사용자 지정 클레임 공급자를 제공 하는 [AzureCP](https://yvand.github.io/AzureCP/) 라는 오픈 소스 솔루션을 사용할 수 있습니다. Azure AD Graph를 사용 하 여 사용자가 입력 하 고 유효성 검사를 수행 하는 작업을 확인 합니다. 자세한 내용은 [AzureCP](https://yvand.github.io/AzureCP/)을 참고 하세요. 

## <a name="additional-resources"></a>추가 리소스

[WS-FEDERATION 이해](https://go.microsoft.com/fwlink/p/?linkid=188052)
  
[클라우드 도입 및 하이브리드 솔루션](cloud-adoption-and-hybrid-solutions.md)
  
## <a name="join-the-discussion"></a>토론 참여

|**연락처**|**설명**|
|:-----|:-----|
|**어떤 클라우드 채택 콘텐츠가 필요한가요?** <br/> |여러 Microsoft 클라우드 플랫폼 및 서비스에 적용되는 클라우드 채택 콘텐츠를 만들고 있습니다. 클라우드 채택 콘텐츠에 대한 의견을 제공하거나 [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20)으로 이메일을 보내서 특정 콘텐츠를 요청하세요.<br/> |
|**클라우드 채택 토론에 가입** <br/> |클라우드 기반 솔루션에 관심이 있다면 CAAB(클라우드 채택 자문 위원회)에 가입하여 Microsoft 콘텐츠 개발자, 산업 전문가 및 전 세계 고객으로 구성된 더 크고 활발한 커뮤니티에 연결할 수 있습니다. 참가하려면 Microsoft 기술 커뮤니티의 [CAAB(Cloud Adoption Advisory Board) 영역](https://aka.ms/caab)에 본인을 회원으로 추가하고 [CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!)에서 간단한 전자 메일을 보내주세요. [CAAB 블로그](https://blogs.technet.com/b/solutions_advisory_board/)에서는 누구나 커뮤니티 관련 콘텐츠를 읽을 수 있습니다. 그러나 CAAB 구성원은 새 클라우드 채택 리소스와 솔루션에 대해 설명하는 비공개 웹 세미나에 초대됩니다.<br/> |
|**여기에 표시된 아트 받기** <br/> |이 문서에 표시된 아트의 편집 가능한 복사본을 원하시면 보내드리겠습니다. 아트의 URL과 제목을 적어서 [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20)으로 요청 이메일을 보내주세요.  <br/> |
   

