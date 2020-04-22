---
title: Office 365 하이브리드 id 및 디렉터리 동기화
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.date: 04/20/2010
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MOE150
- MET150
ms.assetid: d3577c90-dda5-45ca-afb0-370d2889b10f
description: Office 365, Active Directory 도메인 서비스 정리 및 Azure Active Directory Connect 도구를 사용한 디렉터리 동기화에 대해 설명 합니다.
ms.openlocfilehash: 44894cdbc65c243ce0c4a66ceba1d123ece49c62
ms.sourcegitcommit: f2e640ffdbef95c6d98845f85fd9bea21a7388aa
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/21/2020
ms.locfileid: "43580935"
---
# <a name="hybrid-identity-and-directory-synchronization-for-office-365"></a>Office 365 하이브리드 id 및 디렉터리 동기화

*이 문서는 Microsoft 365 Enterprise와 Office 365 Enterprise에 모두 적용됩니다.*

비즈니스 요구 사항과 기술 요구 사항에 따라 하이브리드 id 모델 및 디렉터리 동기화가 Office 365를 채택 하는 엔터프라이즈 고객에 게 가장 일반적으로 선택 됩니다. 디렉터리 동기화를 사용 하면 AD DS (Active Directory 도메인 서비스)에서 id를 관리할 수 있으며, 사용자 계정, 그룹 및 연락처에 대 한 모든 업데이트는 Office 365 구독의 azure AD (azure Active Directory) 테 넌 트와 동기화 됩니다.

>[!Note]
>AD DS 사용자 계정이 처음으로 동기화 되 면 Office 365 라이선스가 자동으로 할당 되지 않으며 전자 메일과 같은 Office 365 서비스에 액세스할 수 없습니다. 이러한 사용자 계정에 개별적으로 또는 동적으로 그룹 구성원을 통해 라이선스를 할당 해야 합니다.
>

## <a name="authentication-for-hybrid-identity"></a>하이브리드 id에 대 한 인증

하이브리드 id 모델을 사용 하는 경우 다음 두 가지 유형의 인증을 사용할 수 있습니다.

- 관리되는 인증

  Azure AD는 로컬로 저장 된 해시 버전의 암호를 사용 하 여 인증 프로세스를 처리 하거나 온-프레미스 AD DS에서 인증 하기 위해 온-프레미스 소프트웨어 에이전트로 자격 증명을 전송 합니다.

- 페더레이션 인증

  Azure AD는 클라이언트 컴퓨터에서 인증 요청을 리디렉션하여 다른 id 공급자에 게 연결 합니다.

### <a name="managed-authentication"></a>관리되는 인증

관리 되는 인증에는 다음과 같은 두 가지 유형이 있습니다.

- 암호 해시 동기화 (PHS)

  Azure AD는 인증 자체를 수행 합니다.

- 통과 인증(PTA)

  Azure AD에 AD DS가 인증을 수행 합니다.


#### <a name="password-hash-synchronization"></a>암호 해시 동기화

PHS (암호 해시 동기화)를 사용 하 여 AD DS 사용자 계정을 Office 365와 동기화 하 고 온-프레미스 사용자를 관리 합니다. 사용자 암호는 온-프레미스와 클라우드에서 동일한 암호를 사용 하도록 AD DS에서 Azure AD로 동기화 됩니다. Azure AD에서 AD DS id에 대 한 인증을 사용 하는 가장 간단한 방법입니다. 

![암호 해시 동기화 (PHS)](./media/plan-for-directory-synchronization/phs-authentication.png)

암호가 변경 되거나 온-프레미스에서 다시 설정 되 면 새 암호 해시가 Azure AD와 동기화 되어 사용자가 항상 클라우드 리소스 및 온-프레미스 리소스에 대해 동일한 암호를 사용할 수 있습니다. 사용자 암호가 Azure ad로 전송 되지 않거나 Azure AD의 일반 텍스트로 저장 됩니다. Id 보호와 같은 Azure AD의 일부 프리미엄 기능은 선택한 인증 방법에 관계 없이 PHS를 요구 합니다.
  
자세한 내용을 보려면 [PHS 선택을](https://docs.microsoft.com/azure/active-directory/hybrid/choose-ad-authn) 참조 하십시오.
  
#### <a name="pass-through-authentication"></a>통과 인증

PTA (통과 인증)는 AD DS와 직접 유효성을 검사 하기 위해 하나 이상의 온-프레미스 서버에서 실행 되는 소프트웨어 에이전트를 사용 하는 Azure AD 인증 서비스에 대 한 간단한 암호 유효성 검사를 제공 합니다. PTA (통과 인증)를 사용 하는 경우 AD DS 사용자 계정을 Office 365와 동기화 하 고 온-프레미스 사용자를 관리 합니다. 

![통과 인증(PTA)](./media/plan-for-directory-synchronization/pta-authentication.png)

PTA 사용자는 온-프레미스 계정 및 암호를 사용 하 여 온-프레미스 및 Office 365 리소스와 응용 프로그램 모두에 로그인 할 수 있습니다. 이 구성은 Azure AD에 암호 해시를 저장 하지 않고 온-프레미스 AD DS에 대해 직접 사용자 암호의 유효성을 검사 합니다. 

또한 PTA는 온-프레미스 사용자 계정 상태, 암호 정책 및 로그온 시간을 즉시 적용 하기 위한 보안 요구 사항이 있는 조직에도 적합 합니다. 
  
자세한 내용을 보려면 [PTA 선택을](https://docs.microsoft.com/azure/active-directory/hybrid/choose-ad-authn) 참조 하세요.
  
### <a name="federated-authentication"></a>페더레이션 인증

페더레이션 인증은 인증 요구 사항이 더 복잡 한 대규모 엔터프라이즈 조직에 주로 사용 됩니다. AD DS id는 Office 365와 동기화 되며 사용자 계정은 온-프레미스에서 관리 됩니다. 페더레이션 인증을 사용 하는 경우 사용자는 온-프레미스와 클라우드에서 동일한 암호를 사용 하며, Office 365를 사용할 수 있도록 다시 로그인 할 필요가 없습니다. 

페더레이션 인증은 스마트 카드 기반 인증 또는 타사 다단계 인증과 같은 추가 인증 요구 사항을 지원할 수 있으며, 일반적으로 조직이 Azure AD에서 기본적으로 지원 하지 않는 인증 요구 사항을 충족 하는 경우에 필요 합니다.
 
자세히 알아보려면 [페더레이션 인증 선택을](https://docs.microsoft.com/azure/active-directory/hybrid/choose-ad-authn) 참조 하세요.
  
#### <a name="third-party-authentication-and-identity-providers"></a>타사 인증 및 id 공급자

온-프레미스 디렉터리 개체는 Office 365와 동기화 될 수 있으며, 클라우드 리소스 액세스는 주로 타사 id 공급자 (IdP)를 통해 관리 됩니다. 조직에서 타사 페더레이션 솔루션을 사용 하는 경우 타사 페더레이션 솔루션이 Azure AD와 호환 되는 경우 Office 365에 대 한 해당 솔루션에 대 한 로그온을 구성할 수 있습니다.
  
자세한 내용은 [AZURE AD 페더레이션 호환성](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility) 을 참조 하세요.
  
## <a name="ad-ds-cleanup"></a>AD DS 정리

동기화를 사용 하 여 Office 365로 원활 하 게 전환할 수 있도록 하려면 Office 365 디렉터리 동기화 배포를 시작 하기 전에 AD DS 포리스트를 준비 해야 합니다.
  
[Office 365에서 디렉터리 동기화를 설정](set-up-directory-synchronization.md)하면 [idfix 도구를 다운로드 하 여 실행](install-and-run-idfix.md)하는 단계 중 하나입니다. IdFix 도구를 사용 하 여 [디렉터리 정리](prepare-directory-attributes-for-synch-with-idfix.md)를 지원할 수 있습니다.
  
디렉터리 정리는 다음 작업에 중점을 두어야 합니다.

- 중복 **Proxyaddress** 및 **userPrincipalName** 특성을 제거 합니다.
- 비어 있거나 잘못 된 **userPrincipalName** 특성을 올바른 **userPrincipalName** 특성으로 업데이트 합니다.
- **GivenName**, 성 ( **Sn** ), **sAMAccountName**, **displayName**, **mail**, **proxyAddresses**, **mailNickname**및 **userPrincipalName** 특성에서 잘못 되었거나 불확실 한 문자를 제거 합니다. 특성을 준비 하는 방법에 대 한 자세한 내용은 [Azure Active Directory 동기화 도구를 통해 동기화 되는 특성 목록을](https://go.microsoft.com/fwlink/p/?LinkId=396719)참조 하십시오.

    > [!NOTE]
    > Azure AD Connect에서 동기화 하는 것과 동일한 특성이 여기에 해당 됩니다. 
  
## <a name="multi-forest-deployment-considerations"></a>다중 포리스트 배포 시 고려 사항

여러 포리스트와 SSO 옵션에 대해 [AZURE AD Connect의 사용자 지정 설치](https://go.microsoft.com/fwlink/p/?LinkId=698430)를 사용 합니다.
  
조직에 인증 (로그온 포리스트)을 위한 포리스트가 여러 개 있는 경우에는 다음을 수행 하는 것이 좋습니다.
  
- **포리스트를 통합 하는 것이 좋습니다.** 일반적으로 여러 포리스트를 유지 관리 하려면 오버 헤드가 더 많이 필요 합니다. 조직에 별도의 포리스트에 대 한 요구를 규정 하는 보안 제약 조건이 없는 경우에는 온-프레미스 환경을 단순화 하는 것이 좋습니다.
- **기본 로그온 포리스트에서만 사용 합니다.** Office 365의 초기 롤아웃을 위해 기본 로그온 포리스트에만 Office 365을 배포 하는 것이 좋습니다. 

다중 포리스트 AD DS 배포를 통합할 수 없거나 다른 디렉터리 서비스를 사용 하 여 id를 관리 하는 경우에는 이러한 정보를 Microsoft 또는 파트너의 도움말과 동기화 할 수 있습니다.
  
자세한 내용은 [Single Sign-on 시나리오를 사용 하 여 다중 포리스트 디렉터리 동기화](https://go.microsoft.com/fwlink/p/?LinkId=525321) 를 참조 하세요.
  
## <a name="features-that-are-dependent-on-directory-synchronization"></a>디렉터리 동기화에 따라 달라 지는 기능
  
디렉터리 동기화는 다음과 같은 기능을 수행 하는 데 필요 합니다.
  
- Azure AD에 원활한 SSO (Single Sign-on)
- Skype 동시 사용
- 다음을 포함 한 Exchange 하이브리드 배포
  - 온-프레미스 Exchange 환경과 Office 365 간에 완전히 공유 되는 GAL (전체 주소 목록)입니다.
  - 다양 한 메일 시스템에서 GAL 정보 동기화
  - Office 365 서비스 제품에서 사용자를 추가 및 제거 하는 기능 이를 위해서는 다음이 필요 합니다.
  - 양방향 동기화는 디렉터리 동기화 설정 중에 구성 해야 합니다. 기본적으로 디렉터리 동기화 도구는 디렉터리 정보를 클라우드에만 기록 합니다. 양방향 동기화를 구성 하는 경우 제한 된 수의 개체 특성이 클라우드에서 복사 되 고 로컬 AD DS에 다시 기록 되도록 쓰기 기능을 사용 하도록 설정 합니다. 쓰기 저장은 Exchange 하이브리드 모드 라고도 합니다. 
  - 온-프레미스 Exchange 하이브리드 배포
  - 다른 사용자 사서함을 온-프레미스에 유지 하면서 일부 사용자 사서함을 Office 365로 이동 하는 기능
  - 온-프레미스의 수신 허용 및 수신 거부는 Office 365에 복제 됩니다.
  - 기본 위임 및 대신 보내기 전자 메일 기능
  - 통합 된 온-프레미스 스마트 카드 또는 다단계 인증 솔루션을 사용 하 고 있습니다.
- 사진, 축소판 그림, 회의실 및 보안 그룹 동기화

## <a name="next-step"></a>다음 단계

하이브리드 id를 배포할 준비가 되 면 [사용자 프로 비전 준비를](prepare-for-directory-synchronization.md)참조 하세요.
  
## <a name="see-also"></a>참고 항목

[Microsoft 365 Enterprise 개요](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)

