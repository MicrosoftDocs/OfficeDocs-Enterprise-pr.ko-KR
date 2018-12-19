---
title: 디렉터리 동기화를 통해 사용자를 Office 365에 프로비전하기 위한 준비
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
f1_keywords:
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: 이 메서드를 사용 하 여의 장기 이점과 디렉터리 동기화를 사용 하 여 사용자를 Office 365에 프로 비전을 준비 하는 방법에 설명 합니다.
ms.openlocfilehash: 8e84f4602b79ce321cd9a71e6c35331baf40f7f0
ms.sourcegitcommit: c5761d3c41aa2d26815f0d24c73dbcd53ab37957
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/19/2018
ms.locfileid: "27371122"
---
# <a name="prepare-to-provision-users-through-directory-synchronization-to-office-365"></a>디렉터리 동기화를 통해 사용자를 Office 365에 프로비전하기 위한 준비

디렉터리 동기화를 통해 사용자를 프로 비전 더 많은 계획 및 준비 단순히 Office 365에서 직접 작업이 나 교육용 계정 관리 보다 필요 합니다. 추가 계획 및 준비 작업은 온-프레미스 Active Directory Azure Active Directory에 올바르게 동기화 보장 하기 위해 필요 합니다. 조직에 추가 된 이점은 다음과 같습니다.
  
- 조직의 관리 프로그램 감소
- 필요에 따라 single sign-on 및 시나리오를 사용 하도록 설정
- Office 365에서 계정 변경 자동화
    
디렉터리 동기화를 사용 하 여의 장점에 대 한 자세한 내용은 [디렉터리 동기화 로드맵]( https://go.microsoft.com/fwlink/p/?LinkId=525398) 및 [Office 365 Id 이해 및 Azure Active Directory를](about-office-365-identity.md)참조 하십시오.
  
시나리오를 조직에 대 한 최고를 확인 하려면 [디렉터리 통합 도구 비교](https://go.microsoft.com/fwlink/p/?LinkId=525320)를 검토 합니다.
  
## <a name="directory-cleanup-tasks"></a>디렉터리 정리 작업

디렉터리 동기화를 시작 하기 전에 디렉터리를 정리 해야 합니다.
  
[Azure AD 연결 하 여 Azure Active Directory 특성 동기화](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-sync-attributes-synchronized)한도 검토 합니다.
  
> [!IMPORTANT]
> 동기화 하기 전에 디렉터리 정리를 수행 하지는 배포 프로세스에 중요 한 부정적인 영향을 있을 수 있습니다. 일, 수행 또는 디렉터리 동기화를 다시 동기화 및 오류를 식별 하는 주기를 통과 하도록 주에도 될 수 있습니다. 
  
프로그램 온-프레미스 디렉터리에서 다음과 같은 정리 작업을 완료 합니다.
  
1. Office 365 서비스 제품을 할당받을 각 사용자의 올바르고 고유한 전자 메일 주소가 **proxyAddresses** 특성에 포함되는 있는지 확인합니다. 
    
2. **proxyAddresses** 속성에서 중복되는 값을 모두 제거합니다. 
    
3.  가능한 경우 Office 365 서비스 제품 할당 받을 각 사용자가 사용자의 **사용자** 개체의 **userPrincipalName** 특성에 대 한 유효 하 고 고유한 값을 확인 합니다. 최상의 동기화 경험에 대 한 온-프레미스 Active Directory UPN 클라우드 UPN과 일치 하는지 확인 합니다. 사용자의 **userPrincipalName** 특성에 대 한 값이 없는 경우 **사용자** 개체의 **sAMAccountName** 특성에 대 한 유효 하 고 고유한 값을 포함 해야 합니다. **UserPrincipalName** 특성에 중복 된 값을 제거 합니다. 
    
4. GAL(전체 주소 목록)을 가장 효과적으로 사용하려면 다음 특성의 정보가 올바른지 확인합니다.
    
  - givenName 
  - 성
  - displayName
  - 직함
  - 부서
  - 사무실
  - 사무실 전화
  - 휴대폰 번호
  - 팩스 번호
  - 주소
  - 구/군/시
  - 시/도
  - 우편 번호
  - 국가 또는 지역
    
## <a name="directory-object-and-attribute-preparation"></a>디렉터리 개체 및 특성 준비

온-프레미스 디렉터리 및 Office 365 간의 성공적인 디렉터리 동기화 온-프레미스 디렉터리 특성 적절히 준비는 필요 합니다. 예, Office 365 환경과 동기화 되는 특정 특성에 사용 되지 않은 특정 문자를 확인 해야 합니다. 예기치 않은 문자 실패에 대 한 디렉터리 동기화를 일으키지 않습니다 하지만 알리는 경고 메시지를 반환할 수 있습니다. 잘못 된 문자가 디렉터리 동기화 실패 하면 발생 합니다.
  
디렉터리 동기화는 Active Directory 사용자의 일부는 중복 된 특성을 하나 이상 하는 경우에 실패 합니다. 각 사용자에는 고유한 특성이 있어야 합니다.
  
준비 하는 특성은 다음과 같습니다.
  
 **참고:** 또한이 프로세스를 훨씬 쉽게 [IdFix 도구](install-and-run-idfix.md) 를 사용할 수 있습니다. 
  
- **displayName**
    
  - 이 특성이 사용자 개체에 있으면 Office 365와 동기화됩니다.
  - 사용자 개체에 이 특성이 있으면 해당하는 값이 있어야 합니다. 즉 특성은 비워 두면 안 됩니다.
  - 최대 문자 수: 256
    
- **givenName **
    
  - 사용자 개체에 특성이 있으면 Office 365와 동기화되지만, Office 365에서 해당 특성이 필요하거나 이를 사용하지는 않습니다.
  - 최대 문자 수: 64
    
- **메일**
    
  - 특성 값은 디렉터리 내에서 고유해야 합니다.
    
    > [!NOTE]
    > 중복 값이 없으면 값을 가진 첫번째 사용자 동기화 됩니다. 이후 사용자가 Office 365에 나타나지 않습니다. Office 365의 값을 수정 하거나 두 사용자가 Office 365에 표시 하는 순서는 온-프레미스 디렉터리의 값을 모두 수정 해야 합니다. 
  
- **mailNickname**(Exchange 별칭) 
    
  - 특성 값에 마침표 (.)로 시작할 수 없습니다.
  - 특성 값은 디렉터리 내에서 고유해야 합니다.
    
- **proxyAddresses **
    
  - 다중값 특성
  - 값당 최대 문자 수: 256
  - 특성 값에 공백이 포함 해서는 안됩니다.
  - 특성 값은 디렉터리 내에서 고유해야 합니다.
  - 유효 하지 않은 문자: \< \> (); , [ ] "
    
    잘못 된 문자는 문자에 유형을 구분 기호 뒤에 적용 하 고 ":" SMTP:User@contso.com를 사용할 수 있지만 SMTP:user:M@contoso.com 하지는 않도록, 합니다.
    
    > [!IMPORTANT]
    > 모든 메일 전송 SMTP (Simple Protocol) 주소는 전자 메일 메시징 표준을 준수 해야 합니다. 중복 되거나 불필요 한 주소 존재 하는 경우 [Exchange에서 주소를 복제 하 고 불필요 한 프록시를 제거](https://go.microsoft.com/fwlink/?LinkId=293860)하는 도움말 항목을 참조 합니다. 
  
- **sAMAccountName**
    
  - 최대 문자 수: 20
  - 특성 값은 디렉터리 내에서 고유해야 합니다.
  - 유효 하지 않은 문자: [\ "|, /: \< \> + =;? \* ]
  - 사용자의 **sAMAccountName** 특성이 유효하지 않지만 **userPrincipalName** 특성이 유효한 경우 사용자 계정이 Office 365에서 만들어집니다. 
  - **SAMAccountName** 및 **userPrincipalName** 이 둘다 유효 하지 않은 경우에 온-프레미스 Active Directory **userPrincipalName** 특성을 업데이트 해야 합니다. 
    
- **sn**(성) 
    
  - 사용자 개체에 특성이 있으면 Office 365와 동기화되지만, Office 365에서 해당 특성이 필요하거나 이를 사용하지는 않습니다.
    
- **targetAddress**
    
    Office 365 GAL에에서는 사용자에 대 한 채워지는 **targetAddress** 특성 (예: SMTP:tom@contoso.com) 해야 나타나는지 필요한 합니다. 타사 메시징 마이그레이션 시나리오에서 온-프레미스 디렉터리에 대 한 Office 365 스키마를 확장을 해야 합니다. Office 365 스키마 확장은 온-프레미스 디렉터리에서 디렉터리 동기화 도구를 사용 하 여 채워져 있는 Office 365 개체를 관리 하는데 유용한 다른 특성 추가적으로 합니다. 예, 숨겨진된 사서함 또는 메일 그룹을 관리할 **msExchHideFromAddressLists** 특성 추가지 않습니다. 
   
  - 최대 문자 수: 256
  - 특성 값에 공백이 포함 해서는 안됩니다.
  - 특성 값은 디렉터리 내에서 고유해야 합니다.
  - 유효 하지 않은 문자: \ \< \> (); , [ ] "
  - 모든 SMTP(Simple Mail Transport Protocol) 주소는 전자 메일 메시징 표준을 준수해야 합니다.
    
- **userPrincipalName**
    
  - **UserPrincipalName** 특성 하 여 사용자 이름 뒤에 있는 로그인 형식 인터넷 스타일에에서 있어야는 at 기호 (@) 및 도메인 이름: 예: user@contoso.com 합니다. 모든 메일 전송 SMTP (Simple Protocol) 주소는 전자 메일 메시징 표준을 준수 해야 합니다.
  - **userPrincipalName** 특성의 최대 문자 수는 113자입니다. 다음과 같이 @ 기호 앞뒤에는 특정 개수의 문자가 허용됩니다. 
  - @ 기호 앞에 있는 사용자 이름의 최대 문자 수: 64
  - @ 기호 뒤에 있는 도메인 이름의 최대 문자 수: 48
  - 유효 하지 않은 문자: \ % &amp; \* + / =? { } | \< \> ( ) ; : , [ ] "
  - 움라우트 잘못 된 문자가 이기도합니다.
  - @ 문자가 각 **userPrincipalName** 값에 필요 합니다. 
  - @ 문자는 각 **userPrincipalName** 값의 첫 번째 문자일 수 없습니다. 
  - 사용자 이름은 마침표 (.), 앰퍼샌드 끝날 수 없습니다 (&amp;), 공백, a 또는 한 at 기호 (@).
  - 사용자 이름에는 공백을 포함할 수 없습니다.
  - 라우팅할 수 있는 도메인을 사용 해야 합니다. 예, 로컬 또는 내부 도메인을 사용할 수 없습니다.
  - 유니코드는 밑줄 문자로 변환됩니다.
  - **userPrincipalName**에는 디렉터리에서 중복된 값을 포함할 수 없습니다. 
    
## <a name="prepare-the-userprincipalname-attribute"></a>userPrincipalName 특성 준비

Active Directory는 **sAMAccountName** 또는 **userPrincipalName**중 하나를 사용 하 여 디렉터리에 로그인 하 여 조직에서 최종 사용자를 허용 하도록 설계 되었습니다. 마찬가지로, 최종 사용자가 자신의 작업의 사용자 계정 이름 (UPN)를 사용 하 여 Office 365에 로그인 하거나 계정 학교 수 있습니다. 디렉터리 동기화 온-프레미스 디렉터리에 있는 동일한 UPN을 사용 하 여 Azure Active Directory에 새 사용자를 만들려고 시도 합니다. UPN 전자 메일 주소 형식으로 지정 됩니다. 

Office 365 UPN 전자 메일 주소를 생성 하는데 사용 되는 기본 특성을입니다. **UserPrincipalName** 가져올 쉽습니다 (온-프레미스 및 Azure Active Directory에서) 및 **proxyAddresses** 서로 다른 값으로 설정의 기본 전자 메일 주소입니다. 서로 다른 값으로 설정 하는 경우 관리자와 최종 사용자에 대 한 혼란 있을 수 있습니다. 
  
이러한 특성 혼동을 줄이기 위한을 정렬 하는 것이 좋습니다. Active Directory Federation services (AD FS)에서 single sign-on의 요구 사항에 맞게 2.0, 해야 Azure Active Directory 및 온-프레미스 Active Directory에서 Upn을 확인 하는 유효한 도메인 네임 스페이스를 사용 하 여 일치 합니다.
  
## <a name="add-an-alternative-upn-suffix-to-ad-ds"></a>AD DS에 대체 UPN 접미사를 추가

Office 365 환경과 사용자의 회사 자격 증명을 연결 하려면 대체 UPN 접미사를 추가 해야 합니다. UPN 접미사는 오른쪽에 UPN의 일부는 @ 문자입니다. Single sign-on에 사용 되는 Upn 문자, 숫자, 기간, 대시 및 밑줄을 사용할 수 있지만 다른 종류의 문자를 포함할 수 있습니다.
  
Active Directory에 대체 UPN 접미사를 추가 하는 방법에 대 한 자세한 내용은 [디렉터리 동기화 준비]( https://go.microsoft.com/fwlink/p/?LinkId=525430)를 참조 하십시오.
  
## <a name="match-the-on-premises-upn-with-the-office-365-upn"></a>Office 365와 함께 온-프레미스 UPN과 일치 UPN

디렉터리 동기화를 이미 설정한 경우 Office 365에 대 한 사용자의 UPN 온-프레미스 디렉터리 서비스에 정의 된 사용자의 온-프레미스 UPN와 일치 하지 않을 수 있습니다. 이 사용자의 도메인 확인 되었음을 전에 라이선스를 할당 된 경우 발생할 수 있습니다. 이 문제를 해결 하려면 회사 사용자 이름과 도메인 Office 365 UPN과 일치 하는지 확인 하는 사용자의 UPN을 업데이트 하려면 [중복 된 UPN을 수정 하는 PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=396730) 을 사용 합니다. 온-프레미스 디렉터리 서비스에서 UPN을 업데이트 하는 id가 Azure Active Directory와 동기화 되도록 구매할 하는 경우 변경 내용을 온-프레미스를 만들기 전에 Office 365에서 사용자의 라이선스를 제거 해야 합니다. 
  
[디렉터리 동기화를 위한 라우팅할 수 없는 도메인 (예:.local 도메인)를 준비 하는 방법](prepare-a-non-routable-domain-for-directory-synchronization.md)을 참고 하십시오.
  
## <a name="directory-integration-tools"></a>디렉터리 통합 도구

디렉터리 동기화가 디렉터리 개체의 (사용자, 그룹 및 연락처)를 온-프레미스 Active Directory 환경에서에서 Office 365 디렉터리 인프라 Azure Active Directory 동기화 합니다. 사용 가능한 도구 및 해당 기능 목록에 대 한 [디렉터리 통합 도구](https://go.microsoft.com/fwlink/p/?LinkID=510956) 를 참조 하십시오. 권장 되는 도구는 [Microsoft Azure Active Directory에 연결](https://go.microsoft.com/fwlink/p/?LinkID=510956)합니다. Azure Active Directory에 연결 하는 방법에 대 한 자세한 내용은 [Azure Active Directory를 사용 하 여 온-프레미스 id가 통합 (영문)을](https://go.microsoft.com/fwlink/p/?LinkId=527969)참조 하십시오.
  
표시 된 사용자 계정을 처음에 대 한 Office 365 디렉터리와 동기화 된 경우 활성화 되지 않은 것으로 합니다. 전자 메일을 수신 하거나 보낼 수는 없습니다 및 구독 라이선스를 사용 하지 않습니다. 특정 사용자에 게 Office 365 구독을 할당 하려면 준비 되 면를 선택 하 고 [비즈니스를 위한 Office 365에서 사용자에 게 라이선스를 할당](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc)하 여이 활성화 해야 합니다.
  
[PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=613097) 을 사용 하 여 라이선스를 할당 하려면 수도 있습니다. 자동화 된 솔루션에 대 한 [PowerShell Office 365 사용자에 게 자동으로 할당 라이선스를 사용 하는 방법](https://go.microsoft.com/fwlink/p?LinkID=329805) 을 참조 하십시오.