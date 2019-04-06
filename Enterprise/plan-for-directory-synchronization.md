---
title: Office 365에 대 한 디렉터리 동기화 계획
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MOE150
- MET150
ms.assetid: d3577c90-dda5-45ca-afb0-370d2889b10f
description: Office 365, Active directory 정리 및 Azure Active directory Connect 도구를 사용한 디렉터리 동기화에 대해 설명 합니다.
ms.openlocfilehash: 1a7c63f699c51c829aaab5b70cb6a1a203bca3be
ms.sourcegitcommit: 29f937b7430c708c9dbec23bdc4089e86c37c225
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/29/2019
ms.locfileid: "31001831"
---
# <a name="plan-for-directory-synchronization-for-office-365"></a>Office 365에 대 한 디렉터리 동기화 계획

비즈니스 요구 사항 및 기술 요건에 따라 디렉터리 동기화는 Office 365로 전환 하는 엔터프라이즈 고객에 게 가장 일반적인 프로 비전 선택입니다. 디렉터리 동기화를 통해 온-프레미스 Active Directory에서 id를 관리할 수 있으며 해당 id에 대 한 모든 업데이트가 Office 365에 동기화 됩니다.
  
디렉터리 준비, Azure Active directory의 요구 사항 및 기능을 비롯 하 여 디렉터리 동기화 구현을 계획할 때는 주의 해야 할 몇 가지 사항이 있습니다. 디렉터리 준비는 상당히 많은 영역을 포함 합니다. 여기에는 특성 업데이트, 감사 및 계획 도메인 컨트롤러 배치 등이 포함 됩니다. 계획 요구 사항 및 기능에는 필요한 사용 권한 결정, 다중 포리스트/디렉터리 시나리오 계획, 용량 계획, 양방향 동기화 등이 포함 됩니다.
  
## <a name="office-365-identity-models"></a>Office 365 id 모델

Office 365에서는 두 가지 주요 인증 및 id 모델, 즉 클라우드 인증과 페더레이션 인증을 사용 합니다.
  
### <a name="cloud-authentication"></a>클라우드 인증

[클라우드 id](about-office-365-identity.md) - [Microsoft 365 관리 센터](https://admin.microsoft.com)에서 사용자를 만들고 관리 하 고, Windows PowerShell 또는 Azure Active Directory를 사용 하 여 사용자를 관리할 수도 있습니다.
  
[원활한 single sign-on을 사용한 암호 해시 동기화](about-office-365-identity.md) -Azure AD의 온-프레미스 디렉터리 개체에 대 한 인증을 사용 하도록 설정 하는 가장 간단한 방법입니다. 암호 해시 동기화 (phs)를 사용 하 여 온-프레미스 Active Directory 사용자 계정 개체를 Office 365와 동기화 하 고 온-프레미스 사용자를 관리 합니다.
  
[원활한 single sign-on을 통한 통과 인증](about-office-365-identity.md) -하나 이상의 온-프레미스 서버에서 실행 되는 소프트웨어 에이전트를 사용 하 여 Azure AD 인증 서비스에 대 한 간단한 암호 유효성 검사를 제공 하 여 사용자의 유효성을 직접 검사 합니다. 온-프레미스 Active Directory
  
### <a name="federated-authentication"></a>페더레이션 인증

[페더레이션 id Active Directory Federation Services AD FS](about-office-365-identity.md) -주로 인증 요구 사항이 더 많은 대규모 엔터프라이즈 조직에서 온-프레미스 디렉터리 개체는 Office 365와 사용자 계정으로 동기화 됩니다. 온-프레미스에서 관리 됩니다.
  
타사 [인증 및 id 공급자](about-office-365-identity.md) -온-프레미스 디렉터리 개체는 Office 365와 동기화 될 수 있으며, 클라우드 리소스 액세스는 주로 타사 id 공급자 (IdP)를 통해 관리 됩니다.
  
## <a name="active-directory-cleanup"></a>Active Directory 정리

동기화를 사용 하 여 office 365로 원활 하 게 전환할 수 있도록 office 365 디렉터리 동기화 배포를 시작 하기 전에 Active Directory 포리스트를 준비 하는 것이 좋습니다.
  
[Office 365에서 디렉터리 동기화를 설정](set-up-directory-synchronization.md)하면 [idfix 도구를 다운로드 하 여 실행](install-and-run-idfix.md)하는 단계 중 하나입니다. idfix 도구를 사용 하 여 [디렉터리 정리](prepare-directory-attributes-for-synch-with-idfix.md)를 지원할 수 있습니다.
  
디렉터리 정리는 다음 작업에 중점을 두어야 합니다.

- 중복 **proxyaddress** 및 **userPrincipalName** 특성을 제거 합니다.
- 비어 있거나 잘못 된 **userPrincipalName** 특성을 올바른 **userPrincipalName** 특성으로 업데이트 합니다.
- **givenName**, 성 ( **sn** ), **sAMAccountName**, **displayName**, **mail**, **proxyAddresses**, **mailNickname**및 **userPrincipalName** 에서 잘못 되었거나 불확실 한 문자 제거 특성만. 특성을 준비 하는 방법에 대 한 자세한 내용은 [Azure Active Directory 동기화 도구를 통해 동기화 되는 특성 목록을](https://go.microsoft.com/fwlink/p/?LinkId=396719)참조 하십시오.

    > [!NOTE]
    > Azure AD Connect가 동기화 하는 것과 동일한 특성이 여기에 해당 됩니다. 
  
## <a name="multi-forest-deployment-considerations"></a>다중 포리스트 배포 시 고려 사항

여러 포리스트와 SSO 옵션에 대해 [Azure AD Connect의 사용자 지정 설치](https://go.microsoft.com/fwlink/p/?LinkId=698430)를 사용 합니다.
  
조직에 인증 (로그온 포리스트)을 위한 포리스트가 여러 개 있는 경우에는 다음을 수행 하는 것이 좋습니다.
  
- **포리스트 통합 평가** 일반적으로 여러 포리스트를 유지 관리 하려면 오버 헤드가 더 많이 필요 합니다. 조직에 별도의 포리스트에 대 한 요구를 규정 하는 보안 제약 조건이 없는 경우에는 온-프레미스 환경을 단순화 하는 것이 좋습니다.
- **기본 로그온 포리스트에서만 사용 합니다.** office 365의 초기 롤아웃을 위해 기본 로그온 포리스트에만 office 365을 배포 하는 것이 좋습니다. 

다중 포리스트 Active Directory 배포를 통합할 수 없거나 다른 디렉터리 서비스를 사용 하 여 id를 관리 하는 경우에는 이러한 정보를 Microsoft 또는 파트너의 도움말과 동기화 할 수 있습니다.
  
자세한 내용은 [Single sign-on 시나리오를 사용 하 여 다중 포리스트 디렉터리 동기화](https://go.microsoft.com/fwlink/p/?LinkId=525321)를 참조 하세요.
  
## <a name="directory-integration-tools"></a>디렉터리 통합 도구

디렉터리 동기화는 온-프레미스 Active directory 환경의 디렉터리 개체 (사용자, 그룹 및 연락처)를 Office 365 디렉터리 인프라와 동기화 하는 것입니다. 사용할 수 있는 도구 및 해당 기능 목록은 [디렉터리 통합 도구](https://go.microsoft.com/fwlink/p/?LinkID=510956) 를 참조 하십시오. 사용이 권장 되는 도구는 [Azure Active Directory Connect](https://go.microsoft.com/fwlink/?LinkId=525323)입니다.
  
사용자 계정이 처음에 Office 365 디렉터리와 동기화 되 면 활성화 되지 않은 것으로 표시 됩니다. 전자 메일을 보내거나 받을 수 없으며 구독 라이선스를 사용 하지 않습니다. 특정 사용자에 게 Office 365 구독을 할당할 준비가 되 면 유효한 라이선스를 할당 하 여 선택 하 고 활성화 해야 합니다.
  
디렉터리 동기화는 다음과 같은 기능을 수행 하는 데 필요 합니다.
  
- SSO
- Skype 동시 사용
- 다음을 포함 한 Exchange 하이브리드 배포
  - 온-프레미스 Exchange 환경과 Office 365 간에 완전히 공유 되는 GAL (전체 주소 목록)입니다.
  - 다양 한 메일 시스템에서 GAL 정보 동기화
  - Office 365 서비스 제품에서 사용자를 추가 및 제거 하는 기능 이를 위해서는 다음이 필요 합니다.
  - 양방향 동기화는 디렉터리 동기화 설정 중에 구성 해야 합니다. 기본적으로 디렉터리 동기화 도구는 디렉터리 정보를 클라우드에만 기록 합니다. 양방향 동기화를 구성 하는 경우에는 다시 쓰기 기능을 사용 하도록 설정 하 여 제한 된 수의 개체 특성을 클라우드에서 복사한 다음 로컬 Active Directory에 다시 씁니다. 쓰기 저장은 Exchange 하이브리드 모드 라고도 합니다. 
  - 온-프레미스 Exchange 하이브리드 배포
  - 다른 사용자 사서함을 온-프레미스에 유지 하면서 일부 사용자 사서함을 Office 365로 이동 하는 기능
  - 온-프레미스의 수신 허용 및 수신 거부는 Office 365에 복제 됩니다.
  - 기본 위임 및 대신 보내기 전자 메일 기능
  - 통합 된 온-프레미스 스마트 카드 또는 다단계 인증 솔루션을 사용 하 고 있습니다.
- 사진, 축소판 그림, 회의실 및 보안 그룹 동기화