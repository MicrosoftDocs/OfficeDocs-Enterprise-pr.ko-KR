---
title: Office 365의 디렉터리 동기화 계획
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MOE150
- MET150
ms.assetid: d3577c90-dda5-45ca-afb0-370d2889b10f
description: Office 365, Active Directory 정리 및 Azure Active Directory 연결 도구를 사용 하 여 디렉터리 동기화에 설명 합니다.
ms.openlocfilehash: cc2a2ca050facaf53f0a235898c31ae7aaeff4ae
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542066"
---
# <a name="plan-for-directory-synchronization-for-office-365"></a>Office 365의 디렉터리 동기화 계획
비즈니스 요구 및 기술 요구 사항에 따라 디렉터리 동기화는 엔터프라이즈 고객에 게 Office 365로 이동 하는 가장 일반적인 프로 비전 선택입니다. 해당 id에 대 한 모든 업데이트는 Office 365와 동기화 및 디렉터리 동기화에 id가 온-프레미스 Active Directory에서 관리할 수 있습니다.
  
디렉터리 동기화를 디렉터리 준비 및 요구 사항 및 Azure Active Directory의 기능 등의 구현을 계획 하는 경우 유의 해야할 사항 중 몇가지 있습니다. 디렉터리 준비는 몇 관련 된 내용을 다룹니다. 특성 업데이트, 감사, 및 도메인 컨트롤러 배치 계획 포함 됩니다. 계획 요구 사항 및 기능 포함 multiforest/디렉터리 시나리오, 용량 계획 및 양방향 동기화에 대 한 계획 필요한 사용 권한을 확인 합니다.
  
## <a name="office-365-identity-models"></a>Office 365 id 모델
두 기본 인증 및 id 모델을 사용 하 여 office 365: 클라우드 인증 및 연결 된 인증 합니다.
  
### <a name="cloud-authentication"></a>클라우드 인증
[클라우드 id](about-office-365-identity.md) -만들기 및 Office 365 관리 센터에서 사용자 관리, 사용자를 관리 하려면 Windows PowerShell 또는 Azure Active Directory을 사용할 수도 있습니다. 
  
[암호 해시를 원활 하 게 single sign-on 동기화](about-office-365-identity.md) -Azure AD에서 온-프레미스 디렉터리 개체에 대 한 인증을 사용 하는 가장 간단한 방법은 합니다. 암호 해시 동기화 (PHS)를 사용한 Office 365와 온-프레미스 Active Directory 사용자 계정 개체를 동기화 및 사용자가 온-프레미스를 관리 합니다. 
  
하나 이상의 온-프레미스 서버에서 실행 되는 소프트웨어 에이전트를 사용 하 여 직접 사용 하는 사용자의 유효성을 검사 하려면 Azure AD 인증 서비스에 대 한 간단한 암호 유효성을 제공 하는 [원활 하 게 single sign-on 통과 인증](about-office-365-identity.md) -사용자 온-프레미스 Active Directory 합니다. 
  
### <a name="federated-authentication"></a>연결 된 인증
[Active Directory Federation Services AD FS 갖는 페더레이션 id](about-office-365-identity.md) -대기업 조직 보다 복잡 한 인증 요구 사항에 대 한 주로 온-프레미스 디렉터리 개체는 Office 365와 동기화 되며 사용자 계정 관리 되는 온-프레미스 합니다. 
  
[타사 인증 및 id 공급자](about-office-365-identity.md) -온-프레미스 디렉터리 개체를 Office 365로 동기화 될 수 및 리소스 액세스를 클라우드는 주로 타사 id 공급자 (IdP)에 의해 관리 됩니다. 
  
## <a name="active-directory-cleanup"></a>Active Directory 정리
을 동기화를 사용 하 여 Office 365로 원활 하 게 전환을 보장 하기 위해 Office 365 디렉터리 동기화 배포를 시작 하기 전에 Active Directory 포리스트를 준비 하는 것이 좋습니다.
  
[다운로드 하 고 IdFix 도구를 실행](install-and-run-idfix.md)하려면이 [Office 365에서 디렉터리 동기화를 설정](set-up-directory-synchronization.md)하는 경우는 단계 중 하나입니다. [디렉터리 정리](prepare-directory-attributes-for-synch-with-idfix.md)를 위해 IdFix 도구를 사용할 수 있습니다.
  
디렉터리 정리 다음과 같은 작업에 초점 해야 합니다.

- 중복 **되는 proxyAddress** 및 **userPrincipalName** 특성을 제거 합니다.
- 비어 있거나 잘못된 **userPrincipalName** 특성을 올바른 **userPrincipalName** 특성으로 업데이트합니다.
- **GivenName**, 성 ( **sn** ), **sAMAccountName**, **displayName**, **메일**, **proxyAddresses**, **mailNickname**및 **userPrincipalName** 문제가 되 고 잘못 된 문자를 제거 합니다. 특성입니다. 특성을 준비 하는 방법에 대 한 자세한 내용은, [Azure Active Directory 동기화 도구에 의해 동기화 하는 특성의 목록은](https://go.microsoft.com/fwlink/p/?LinkId=396719)참조 하십시오.
    
    > [!NOTE]
    > 다음은 Azure AD 연결 동기화 되는 동일한 특성입니다. 
  
## <a name="multiforest-deployment-considerations"></a>다중 포리스트 배포 시 고려 사항
여러 포리스트 및 SSO 옵션에 대 한 [사용자 정의 설치의 Azure AD 연결](https://go.microsoft.com/fwlink/p/?LinkId=698430)을 사용 합니다.
  
조직에 인증 (로그온 포리스트)에 대 한 다중 포리스트, 하는 경우 좋습니다 다음 합니다.
  
- **포리스트 통합 (영문) 평가.** 일반적으로 다중 포리스트를 유지 관리 하는 데 필요한 더 많은 오버 헤드가 합니다. 조직에 별도 포리스트에 대 한 필요성을 지정 하는 보안 제약 조건, 하지 않은 경우에 온-프레미스 환경의 간소화 하는 것이 좋습니다.
- **기본 로그온 포리스트에만 사용 합니다.** Office 365의 초기 롤아웃에 대 한 기본 로그온 포리스트에만 Office 365를 배포 하는 것이 좋습니다. 
    
다중 포리스트 Active Directory 배포에 통합할 수 없을 또는 다른 디렉터리 서비스를 사용 하 여 id가 관리 하는 경우에 Microsoft 또는 파트너를 활용 하 여 이러한 동기화 할 수 있습니다.
  
자세한 내용은 [Single Sign-on 시나리오를 사용 하는 다중 포리스트 디렉터리 동기화](https://go.microsoft.com/fwlink/p/?LinkId=525321)를 참조 하십시오.
  
## <a name="directory-integration-tools"></a>디렉터리 통합 도구
디렉터리 동기화 온-프레미스 Active Directory 환경에서 Office 365 디렉터리 인프라 (사용자, 그룹 및 연락처) 디렉터리 개체 동기화 시작 됩니다. 사용 가능한 도구 및 해당 기능 목록에 대 한 [디렉터리 통합 도구](https://go.microsoft.com/fwlink/p/?LinkID=510956) 참조 하십시오. 사용 하 여 권장 되는 도구 [Azure Active Directory 연결](https://go.microsoft.com/fwlink/?LinkId=525323)됩니다.
  
사용자 계정의 처음으로 Office 365 디렉터리와 동기화 됩니다 활성화 되지 않은으로 표시 됩니다. 전자 메일을 수신 하거나 보낼 수는 없습니다 및 구독 라이선스를 사용 하지 않습니다. 특정 사용자에 게 Office 365 구독을 할당 하려면 준비 되 면를 선택 하 고 유효한 라이선스를 할당 하 여이 활성화 해야 합니다.
  
디렉터리 동기화가 다음과 같은 특징 및 기능 필요 합니다.
  
- SSO
    
- Lync 공존 성
    
- Exchange 하이브리드 배포를 포함 합니다.
    
  - 온-프레미스 Exchange 환경과 Office 365 간에 공유 전체 주소 목록 (gal 전체) 완벽 하 게 합니다.
  - 다양한 메일 시스템의 GAL 정보 동기화
  - 사용자를 추가 하 고 Office 365 서비스 제품에서 사용자를 제거할 수 있습니다. 이렇게 하려면 다음이 필요 합니다.
  - 디렉터리 동기화 설치 하는 동안 양방향 동기화를 구성 해야 합니다. 기본적으로 디렉터리 동기화 도구는 클라우드로만 디렉터리 정보를 작성합니다. 양방향 동기화를 구성할 때 개체 특성의 제한 된 수의 클라우드에서 복사 되며 하 여 로컬 Active Directory에 다시 작성 있도록 쓰기 저장 기능이 활성화 합니다. 쓰기 저장 Exchange 하이브리드 모드 라고도 합니다. 
  - 온-프레미스 Exchange 하이브리드 배포
  - Office 365에 다른 사용자 온-프레미스 사서함을 유지 하면서 일부 사용자 사서함을 이동 하는 기능입니다.
  - 수신 허용-보낸사람 및 수신된 거부 온-프레미스 Office 365로 복제 됩니다.
  - 기본 위임 및 대신 보내기 전자 메일 기능
  - 통합 된 온-프레미스 스마트 카드 또는 다단계 인증 솔루션은 해야합니다.
    
- 사진, 축소판 그림, 회의실 및 보안 그룹의 동기화