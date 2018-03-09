---
title: "Azure AD를 사용 하 여 SharePoint 서버 인증을 위해"
ms.author: tracyp
author: MSFTTracyP
ms.reviewer:
- kirke
- josephd
- kirks
manager: laurawi
ms.date: 3/2/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Hybrid
ms.custom: Ent_Solutions
ms.assetid: 
description: "요약: Azure 액세스 제어 서비스를 무시 하 고 SAML 1.1을 사용 하 여 Azure Active Directory와 SharePoint Server 사용자를 인증 하는 방법에 알아봅니다."
ms.openlocfilehash: 1e8ce1aad43e110311c1f5fcceca816871c07e9e
ms.sourcegitcommit: 2cfb30dd7c7a6bc9fa97a98f56ab8fe008504f41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/09/2018
---
# <a name="using-azure-ad-for-sharepoint-server-authentication"></a>Azure AD를 사용 하 여 SharePoint 서버 인증을 위해

 **요약:** Azure Active Directory와 SharePoint Server 2016 사용자를 인증 하는 방법에 알아봅니다.
  
> [!NOTE]
> 이 문서는 Kirk Evans, Microsoft 보안 주체 프로그램 관리자의 작업을 기반으로 합니다. 

<blockquote>
<p>이 문서는 Azure Active Directory 그래프와 상호작용 하기 위한 코드 예제를 참조 합니다. 코드 샘플을 다운로드할 수 [여기](https://github.com/kaevans/spsaml11/tree/master/scripts)합니다.</p>
</blockquote>

SharePoint Server 2016 쉽게 사용자를 관리 하 여 신뢰할 수 있지만 다른 사람을 관리 하는 다른 id 공급자를 사용 하 여 인증 하는 하 여 클레임 기반 인증을 사용 하 여 사용자를 인증 하는 기능을 제공 합니다. 예, Active Directory 도메인 서비스 (AD DS)를 통해 사용자 인증을 관리 하는 대신 Azure Active Directory (Azure AD)를 사용 하 여 인증에 사용자를 설정할 수 있습니다. 이렇게 하면 해당 사용자 이름에 onmicrosoft.com 접미사를 사용 하 여 클라우드 전용 사용자 인증, 사용자는 온-프레미스 디렉터리와 동기화 하 고 다른 디렉터리에서 게스트 사용자를 초대 합니다. 또한 다단계 인증 및 고급 보고 기능 등의 Azure AD 기능을 활용할 수 있습니다.

> [!IMPORTANT]
> 이 문서에서 설명 하는 솔루션을 사용 하 여 SharePoint Server 2013;도 수 있습니다. 그러나 염두에 SharePoint Server 2013은 메인스트림 지원 종료 거의 가득 차지 합니다. 자세한 내용은 [Microsoft 수명 주기 정책](https://support.microsoft.com/en-us/lifecycle/search?alpha=SharePoint%20Server%202013) 및 [SharePoint 2013에 대 한 제품 서비스 정책 업데이트](https://technet.microsoft.com/library/684173bb-e90a-4eb7-b268-b8d7458bc802(v=office.16).aspx)를 참조 하십시오.

이 문서에서는 Azure AD를 사용 하 여 온-프레미스 하는 대신 사용자를 인증 하는 방법을 설명 AD DS 합니다. 이 구성에서 Azure AD SharePoint Server 2016에 대 한 신뢰할 수 있는 id 공급자를 됩니다. 이 구성 추가 하는 SharePoint Server 2016 설치 자체에서 사용 하는 AD DS 인증 분리 하는 사용자 인증 방법입니다. 이 문서를 에서도 Ws-federation을 파악 해야 합니다. 자세한 내용은 [Ws-federation 이해를](https://go.microsoft.com/fwlink/p/?linkid=188052)참조 하십시오.

![Azure AD를 사용 하 여 SharePoint 인증에 대 한](images/SAML11/fig1-architecture.png)

이전에이 구성은 필요 했을 페더레이션 서비스와 같은 Azure 서비스 ACS (액세스 제어) 클라우드 또는 환경에서를 호스팅하는 Active Directory Federation Services (AD FS) SAML 1.1 SAML 2.0에서 되는 토큰을 변환 합니다. 이러한 변화는 Azure AD 이제 발급 SAML 1.1 토큰을 통해 더 이상 필요 합니다. 위 다이어그램에서는이 변환을 수행 하려면 중계 장치에 대 한 요구 사항이 더 이상 인지를 보여주는이 구성에서 SharePoint 2016 사용자에 대 한 인증을 작동 하는 방식을 보여줍니다.

> [!NOTE]
> 이 구성이 작동 하는 SharePoint 팜의 Azure 가상 컴퓨터 또는 온-프레미스에서 호스팅되는 여부. 사용자 확인이 아닌 추가 방화벽 포트를 열어 자신의 브라우저에서 Azure Active Directory에 액세스할 수는 필요 하지 않습니다.

SharePoint 2016 내게 필요한 옵션에 대 한 정보를 [SharePoint Server 2016의 내게 필요한 옵션 지침](https://go.microsoft.com/fwlink/p/?LinkId=393123)을 참조 하십시오.

## <a name="configuration-overview"></a>구성 개요

SharePoint Server 2016 id 공급자로 Azure AD를 사용 하 여 환경을 설정 하는 이러한 일반적인 단계를 따릅니다.

1. 새 만들기 Azure AD 디렉터리 하거나 기존 디렉터리를 사용 합니다.
2. Azure AD와 보안을 유지 하려는 웹 응용 프로그램에 대 한 영역 SSL을 사용 하도록 구성 되어있는지 확인 합니다.
3. Azure AD에 새 엔터프라이즈 응용 프로그램을 만듭니다.
4. SharePoint Server 2016에서 새 신뢰할 수 있는 id 공급자를 구성 합니다.
5. 웹 응용 프로그램에 대 한 사용 권한을 설정 합니다.
6. Azure AD에는 SAML 1.1 토큰 발급 정책을 추가 합니다.
7. 새 공급자를 확인 합니다.

다음 섹션에서는 이러한 작업을 수행 하는 방법에 설명 합니다.

## <a name="step-1-create-a-new-azure-ad-directory-or-use-your-existing-directory"></a>1 단계: 새 만들기 Azure AD 디렉터리 하거나 기존 디렉터리를 사용 하 여

Azure 포털 ([https://portal.azure.com](https://portal.azure.com))에서 새 디렉터리를 만듭니다. 조직 이름, 초기 도메인 이름 및 국가 또는 지역을 제공 합니다.

![디렉터리를 만들기 (영문)](images/SAML11/fig2-createdirectory.png) 

 Microsoft Office 365 또는 Microsoft Azure 구독에 사용 되는 것과 같은 디렉터리에 이미 있는 경우 해당 디렉터리를 대신 사용할 수 있습니다. 디렉터리에 응용 프로그램을 등록할 수 있는 권한이 있어야 합니다.

## <a name="step-2-ensure-the-zone-for-the-web-application-that-you-want-to-secure-with-azure-ad-is-configured-to-use-ssl"></a>2 단계: Azure AD와 보안을 유지 하려는 웹 응용 프로그램에 대 한 영역 SSL을 사용 하도록 구성 되었는지 확인 하십시오.

이 문서에서 [실행을 고가용성 Azure의 SharePoint Server 2016 팜](https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/sharepoint)참조 아키텍처를 사용 하 여 작성 되었습니다. [이 문서](https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/sharepoint) 에서 설명 하는 솔루션을 배포 하는 데 사용 하는 기사의 함께 제공 된 스크립트는 SSL을 사용 하지 않는 사이트를 만듭니다.  

SAML을 사용 하 여 응용 프로그램 SSL을 사용 하도록 구성 해야 합니다. SharePoint 웹 응용 프로그램이 SSL을 사용 하도록 구성 되지 않은, 경우 SSL에 대 한 웹 응용 프로그램을 구성 하는 새로운 자체 서명 된 인증서를 만들려면 다음 단계를 사용 합니다. 이 구성은 랩 환경에 대 한 기능만 및 프로덕션 환경에 대해 되지는지 않습니다. 프로덕션 환경에는 서명 된 인증서를 사용 해야 합니다.

1. **중앙 관리**로 이동 > **응용 프로그램 관리** > **웹 응용 프로그램 관리**, SSL을 사용 하 여 확장 되어야 하는 웹 응용 프로그램을 선택 합니다. 웹 응용 프로그램을 선택 하 고 **확장 리본 메뉴** 단추를 클릭 합니다. 동일한 URL을 사용 하려면 포트 443 사용 하 여 SSL 사용 웹 응용 프로그램을 확장 합니다.</br>![다른 IIS 사이트에 웹 응용 프로그램 확장 (영문)](images/SAML11/fig3-extendwebapptoiis.png)</br>
2. IIS 관리자에서 **서버 인증서**를 두번클릭 합니다.
3. **동작** 창에서 **자체 서명 된 인증서 만들기**를 클릭 합니다. 인증서 상자에 대 한 친숙 한 이름 지정에는 인증서에 대 한 친숙 한 이름을 입력 한 다음 **확인**을 클릭 합니다.
4. **사이트 바인딩 편집** 대화 상자에서 호스트 이름은 친숙 한 이름을와 동일 하 게 다음 이미지에 나와있는 것 처럼 확인 합니다.</br>![IIS의 사이트 바인딩 편집](images/SAML11/fig4-editsitebinding.png)</br>

각 SharePoint 팜의 웹 프런트엔드 서버에서 IIS의에서 사이트 바인딩에 대 한 인증서 구성 필요 합니다.


## <a name="step-3-create-a-new-enterprise-application-in-azure-ad"></a>3 단계: Azure AD에 새 엔터프라이즈 응용 프로그램 만들기

1. Azure 포털 ([https://portal.azure.com](https://portal.azure.com))에서 Azure AD 디렉터리를 엽니다. **엔터프라이즈 응용 프로그램**클릭 한 다음 **새 응용 프로그램**을 클릭 합니다. **비 갤러리 응용 프로그램**을 선택 합니다. *SharePoint SAML 통합* 와 같은 이름을 제공 하 고 **추가**클릭 합니다.</br>![새 갤러리가 아닌 응용 프로그램 추가 (영문)](images/SAML11/fig5-addnongalleryapp.png)</br>
2. 응용 프로그램을 구성 하는 탐색 창의 Single sign on 링크를 클릭 합니다. **SAML 기반 sign-on** 응용 프로그램에 대 한 SAML 구성 속성을 표시 하는 **Single sign-on 모드** 드롭다운을 변경 합니다. 다음과 같은 속성으로 구성 합니다.</br>
    - 식별자:`urn:sharepoint:portal.contoso.local`
    - 회신 URL:`https://portal.contoso.local/_trust/default.aspx`
    - 로그온 URL:`https://portal.contoso.local/_trust/default.aspx`
    - 사용자 Id:`user.userprincipalname`</br>
    - 참고: *portal.contoso.local* 보안을 유지 하려면 SharePoint 사이트의 URL로 대체 하 여 Url을 변경 해야 합니다.</br>
3. 다음 행을 포함 하는 표 (아래 표 1에서와 유사함)를 설정 합니다.</br> 
    - 영역
    - 인증서 파일에 서명 하는 SAML에 대 한 전체 경로
    - ( */Wsfed* */saml2* 바꿉니다) 서비스 URL SAML Single Sign-on
    - 응용 프로그램 개체 id입니다. </br>
*식별자* 값을 테이블로 (참조 아래 표 1.) *영역* 속성에 복사
4. 변경 내용을 저장합니다.
5. Configure 로그온 페이지에 액세스 하려면 **구성 (응용 프로그램 이름)** 링크를 클릭 합니다.</br>![페이지를 단일 기호 (+)를 구성합니다.](images/SAML11/fig7-configssopage.png)</br> 
    -  .Cer 확장명을 가진 파일로 SAML 서명 인증서를 다운로드 하려면 **SAML 서명 인증서-원시** 링크를 클릭 합니다. 복사한 테이블에 다운로드 한 파일의 전체 경로 붙여넣습니다.
    - 복사 및 붙여넣기에 SAML Single Sign-on 서비스 URL 링크를 */wsfed* */saml2* 부분 URL 바꿉니다.</br>
6.  응용 프로그램에 대 한 **속성** 창으로 이동 합니다. 복사 하 고 개체 ID 값 3 단계에서에서 설정한 테이블에 붙여넣습니다.</br>![응용 프로그램에 대 한 속성 창](images/SAML11/fig8-propertiespane.png)</br>
7. 캡처한 값을 사용 하 여, 3 단계에서에서 설정한 테이블 아래 표 1의 형식은 있는지 확인 합니다.


| 표 1: 값 캡처  |  |
|---------|---------|
|영역 | `urn:sharepoint:portal.contoso.local` |
|인증서 파일에 서명 하는 SAML에 대 한 전체 경로 | `C:/temp/SharePoint SAML Integration.cer`  |
|SAML single sign-on 서비스 URL (/wsfed /saml2 바꿉니다) | `https://login.microsoftonline.com/b1726649-b616-460d-8d20-defab80d476c/wsfed` |
|응용 프로그램 개체 ID | `a812f48b-d1e4-4c8e-93be-e4808c8ca3ac` |

> [!IMPORTANT]
> */Wsfed*URL에서 */saml2* 값을 바꿉니다. */Saml2* 끝점 2.0 SAML 토큰에 처리 됩니다. */Wsfed* 끝점 처리 SAML 1.1 토큰을 사용 하도록 설정 하 고 SharePoint 2016 SAML 페더레이션에 필요 합니다.

## <a name="step-4-configure-a-new-trusted-identity-provider-in-sharepoint-server-2016"></a>4 단계: SharePoint Server 2016에서 새 신뢰할 수 있는 id 공급자 구성

SharePoint Server 2016 서버에 서명 하 고 SharePoint 2016 관리 셸을 엽니다. $Realm, $wsfedurl, 그리고 $filepath 표 1에서 값 입력 하 고 새 신뢰할 수 있는 id 공급자를 구성 하려면 다음 명령을 실행 합니다.

> [!TIP]
> 새로운 기능 PowerShell을 사용 하는 PowerShell 작동 하는 방법에 대 한 자세한 내용을 보려면 원하는 경우 [SharePoint PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/overview?view=sharepoint-ps)를 참조 하십시오. 

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

다음으로, 응용 프로그램에 대 한 신뢰할 수 있는 id 공급자를 사용 하도록 설정 하려면 다음이 단계를 따릅니다.
1. 중앙 관리에서 **웹 응용 프로그램 관리** 로 이동 하 고 Azure AD와 보안을 유지 하려는 웹 응용 프로그램을 선택 합니다. 
2. 리본 메뉴에서 **인증 공급자** 를 클릭 하 고 사용 하려는 영역을 선택 합니다.
3. **신뢰할 수 있는 Id 공급자** 를 선택 하 고 *AzureAD*라는 방금 등록 식별 공급자를 선택 합니다.  
4. 로그인 페이지 URL 설정에서 **사용자 정의 페이지에서 로그인** 을 선택 하 고 "/_trust/" 값을 제공 합니다. 
5. **확인**을 클릭합니다.

![인증 공급자 구성](images/SAML11/fig10-configauthprovider.png)

## <a name="step-5-set-the-permissions"></a>5 단계: 사용 권한 설정

Azure AD에 로그인 하 고 SharePoint 액세스 사용자가 응용 프로그램에 대 한 액세스를 부여 되어야 합니다. 

1. Azure 포털에서 Azure AD 디렉터리를 엽니다. **엔터프라이즈 응용 프로그램**클릭 한 다음 **모든 응용 프로그램**을 클릭 합니다. 이전에 만든 응용 프로그램을 클릭 합니다. (SharePoint SAML 통합).
2. **사용자 및 그룹을**클릭 합니다. 
3. 사용자 또는 Azure AD를 사용 하 여 SharePoint에 로그인 하는 권한을 가진 그룹을 추가 하려면 **사용자 추가** 클릭 합니다.
4. 사용자 또는 그룹을 선택한 다음 **할당**을 누릅니다.
 
사용자 Azure AD에 권한을 부여 하지만 사용 권한을 부여 해야 SharePoint에서 합니다. 웹 응용 프로그램에 액세스 권한을 설정 하려면 다음 단계를 사용 합니다.

1. 중앙 관리의 **응용 프로그램 관리**를 클릭 합니다.
2. **응용 프로그램 관리** 페이지의 **웹 응용 프로그램** 섹션에서 **웹 응용 프로그램 관리를**클릭 합니다.
3. 적절 한 웹 응용 프로그램을 클릭 한 다음 **사용자 정책**을 클릭 합니다.
4. 웹 응용 프로그램에 대 한 정책에서 **사용자 추가**클릭 합니다.</br>![자신의 이름 클레임 하 여 사용자에 대 한 검색](images/SAML11/fig11-searchbynameclaim.png)</br>
5. **사용자 추가** 대화 상자에서 **영역**적절 한 영역을 클릭 하 고 ****을 클릭 합니다.
6. **사용자 선택** 섹션에서 **웹 응용 프로그램에 대 한 정책** 대화 상자에서 **찾아보기** 아이콘을 클릭 합니다.
7. **찾을** 텍스트 상자에 디렉터리에 사용자에 대 한 로그인 이름을 입력 하 고 **검색**을 클릭 합니다. </br>예: *demouser@blueskyabove.onmicrosoft.com*합니다.
8. 목록 보기에서 AzureAD 머리글 아래에서 name 속성을 선택 하 고 **추가** 클릭 한 다음 대화 상자를 닫으려면 **확인** 클릭 합니다.
9. 사용 권한에서 **모든 권한**을 클릭 합니다.</br>![클레임 사용자에 게 모든 권한 부여](images/SAML11/fig12-grantfullcontrol.png)</br>
10. **마침**, **확인**을 차례로 클릭합니다.

## <a name="step-6-add-a-saml-11-token-issuance-policy-in-azure-ad"></a>6 단계: Azure AD에 SAML 1.1 토큰 발급 정책 추가

포털에서 Azure AD 응용 프로그램이 만들어지면 SAML 2.0을 사용 하 여 기본값입니다. SharePoint Server 2016 SAML 1.1 토큰 형식이 필요합니다. 다음 스크립트는 기본 SAML 2.0 정책을 제거 하 고 문제 SAML 1.1 토큰에 새 정책 추가 됩니다. 이 코드는 해당 [Azure Active Directory 그래프와 상호작용을 보여주는 샘플](https://github.com/kaevans/spsaml11/tree/master/scripts)을 다운로드 해야 합니다.


```
Import-Module <file path of Initialize.ps1> 
$objectid = "<Application Object ID from Table 1>"
$saml2policyid = Get-PoliciesAssignedToServicePrincipal -servicePrincipalId $objectid | ?{$_.displayName -EQ "TokenIssuancePolicy"} | select objectId
Remove-PolicyFromServicePrincipal -policyId $saml2policyid -servicePrincipalId $objectid
$policy = Add-TokenIssuancePolicy -DisplayName SPSAML11 -SigningAlgorithm "http://www.w3.org/2001/04/xmldsig-more#rsa-sha256" -TokenResponseSigningPolicy TokenOnly -SamlTokenVersion "1.1"
Set-PolicyToServicePrincipal -policyId $policy.objectId -servicePrincipalId $objectid
```

Azure AD와 토큰 발급 정책에 대 한 자세한 내용은 [정책에 대 한 작업에 대 한 그래프 API 참조](https://msdn.microsoft.com/en-us/library/azure/ad/graph/api/policy-operations#create-a-policy)를 참조 하십시오.

## <a name="step-7-verify-the-new-provider"></a>7 단계: 새 공급자를 확인 하십시오.

이전 단계에서 사용자가 구성한 웹 응용 프로그램의 URL로 브라우저를 엽니다. Azure AD에 로그인 하는 것이 리디렉션됩니다.

![페더레이션에 대해 구성 된 Azure AD에 로그인](images/SAML11/fig13-examplesignin.png)

로그인 상태를 유지 하려는 경우가 있습니다.

![로그인 유지 것 입니까?](images/SAML11/fig14-staysignedin.png)

마지막으로 테 넌 트 Azure Active Directory에서에서 사용자로 로그인 사이트에 액세스할 수 있습니다.

![SharePoint에 로그인 하는 사용자](images/SAML11/fig15-signedinsharepoint.png)

## <a name="managing-certificates"></a>인증서 관리
것은 위의 4 단계에서 신뢰할 수 있는 id 공급자에 대해 구성 된 서명 인증서가 만료 날짜와 갱신 되기를 이해 하는 것이 중요 합니다. 인증서를 갱신 대 정보에 대 한 문서 [페더레이션 single sign-on 및 Azure Active directory에서에 대 한 관리 인증서](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-sso-certs) 를 참조 하십시오. Azure AD에 인증서를 갱신 된, 로컬 파일을 다운로드 하 고 다음 스크립트를 사용 하 여 갱신 된 서명 인증서를 사용 하 여 신뢰할 수 있는 id 공급자를 구성 합니다. 

```
$filepath="<Full path to renewed SAML signing certificate file>"
$cert= New-Object System.Security.Cryptography.X509Certificates.X509Certificate2($filePath)
New-SPTrustedRootAuthority -Name "AzureAD" -Certificate $cert
Get-SPTrustedIdentityTokenIssuer "AzureAD" | Set-SPTrustedIdentityTokenIssuer -ImportTrustCertificate $cert
```



## <a name="additional-resources"></a>추가 리소스

[Ws-federation 이해](https://go.microsoft.com/fwlink/p/?linkid=188052)
  
[클라우드 채택 및 하이브리드 솔루션](cloud-adoption-and-hybrid-solutions.md)
  
## <a name="join-the-discussion"></a>토론 참여

|**문의처**|**설명**|
|:-----|:-----|
|**어떤 클라우드 채택 콘텐츠가 필요한가요?** <br/> |여러 Microsoft 클라우드 플랫폼 및 서비스에 걸쳐 있는 클라우드 채택에 대 한 콘텐츠를 만듭니다. 보겠습니다 작업을 알 사용해 클라우드 채택 콘텐츠를 구상할 [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20)에 전자 메일을 발송 하 여 특정 콘텐츠를 요청 합니다.<br/> |
|**클라우드 채택 토론에 가입** <br/> |클라우드 기반 솔루션에 열정을 갖고 인 경우에는 클라우드 채택 자문 보드 (CAAB) Microsoft 콘텐츠 개발자, 업계 전문가는 전세계 어디에서 고객의 더 큰, 생생한 커뮤니티와 연결할에 참가 하는 것이 좋습니다. 참가, Microsoft 기술 커뮤니티의 [CAAB (클라우드 채택 자문 위원회) 공간](https://aka.ms/caab) 의 구성원으로 자신을 추가 하 고 [CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!)에서 빠른 전자 메일을 보내주시기 합니다. 누구나 [CAAB 블로그 (영문)](https://blogs.technet.com/b/solutions_advisory_board/)에서 커뮤니티 관련 콘텐츠를 읽을 수 있습니다. 그러나 CAAB 구성원에 게 새 클라우드 채택 리소스 및 솔루션에 설명 하는 개인 웨 초대장을 가져옵니다.<br/> |
|**여기에 표시된 아트 받기** <br/> |이 문서에서 참조 하는 이미지의 편집 가능한 복사본을 원하는 귀하에 게 보내야 기꺼이 표시 됩니다. URL 및 [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20)는 이미지의 제목을 포함 하 여 요청을 전자 메일로 보냅니다.<br/> |
   

