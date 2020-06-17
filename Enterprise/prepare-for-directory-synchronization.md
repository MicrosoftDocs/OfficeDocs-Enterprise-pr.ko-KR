---
title: Microsoft 365에 대 한 디렉터리 동기화 준비
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/25/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: 디렉터리 동기화 및이 방법을 사용할 경우의 장기적 이점을 사용 하 여 사용자를 Microsoft 365에 프로 비전 하도록 준비 하는 방법에 대해 설명 합니다.
ms.openlocfilehash: 2a4b5f54d7b5aafd5e5eb7a43859e49caa57a519
ms.sourcegitcommit: c112869b3ecc0f574b7054ee1edc8c57132f8237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2020
ms.locfileid: "44735696"
---
# <a name="prepare-for-directory-synchronization-to-microsoft-365"></a>Microsoft 365에 대 한 디렉터리 동기화 준비

*이 문서는 Microsoft 365 Enterprise 및 Microsoft 365 Enterprise에 모두 적용 됩니다.*

조직에 대 한 하이브리드 id 및 디렉터리 동기화의 이점은 다음과 같습니다.
  
- 조직의 관리 프로그램 감소
- 선택적으로 single sign-on 시나리오를 사용 하도록 설정
- Microsoft 365에서 계정 변경 자동화
    
디렉터리 동기화를 사용할 때의 이점에 대 한 자세한 내용은 [디렉터리 동기화 로드맵]( https://go.microsoft.com/fwlink/p/?LinkId=525398) 및 [Microsoft 365의 하이브리드 id](plan-for-directory-synchronization.md)를 참조 하세요.

그러나 디렉터리 동기화의 경우에는 계획 및 준비를 수행 하 여 AD DS (Active Directory 도메인 서비스)가 Microsoft 365 구독의 azure AD (azure Active Directory) 테 넌 트와 동기화 하 여 오류가 최소화 되도록 해야 합니다. 

최상의 결과를 위해 다음 단계를 순서 대로 수행 합니다.
  
## <a name="1-directory-cleanup-tasks"></a>1. 디렉터리 정리 작업

Azure AD 테 넌 트에 AD DS를 동기화 하기 전에 AD DS를 정리 해야 합니다.

> [!IMPORTANT]
> 동기화 하기 전에 AD DS 정리를 수행 하지 않으면 배포 프로세스에 큰 부정적인 영향을 받을 수 있습니다. 디렉터리 동기화 주기, 오류 식별 및 다시 동기화를 진행 하는 데 며칠 또는 몇 주가 소요 될 수 있습니다. 
  
AD DS에서 Microsoft 365 라이선스가 할당 될 각 사용자 계정에 대해 다음과 같은 정리 작업을 완료 합니다.
  
1. **ProxyAddresses** 특성에 유효한 전자 메일 주소와 고유한 주소가 있는지 확인 합니다. 
  
2. **ProxyAddresses** 특성에서 중복 된 값을 모두 제거 합니다. 
    
3.  가능한 경우 사용자의 **user** 개체에 있는 **userPrincipalName** 특성에 대 한 유효한 값 및 고유함을 확인 합니다. 최상의 동기화 환경을 위해 AD DS UPN이 Azure AD UPN과 일치 하는지 확인 합니다. 사용자에 게 **userPrincipalName** 특성에 대 한 값이 없는 경우에는 **사용자** 개체에 **sAMAccountName** 특성에 대 한 유효한 값과 고유 정보가 있어야 합니다. **UserPrincipalName** 특성에서 중복 된 값을 모두 제거 합니다. 
    
4. 전체 주소 목록 (GAL)을 최적의 상태로 사용 하려면 AD DS 사용자 계정의 다음 특성에 있는 정보가 올바른지 확인 합니다.
    
  - givenName
  - 성
  - n
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
  - 국가
    
## <a name="2-directory-object-and-attribute-preparation"></a>2. 디렉터리 개체 및 특성 준비

AD DS와 Microsoft 365 간의 디렉터리 동기화가 정상적으로 수행 되려면 AD DS 특성이 적절 하 게 준비 되어 있어야 합니다. 예를 들어 Microsoft 365 환경과 동기화 되는 특정 특성에 특정 문자가 사용 되지 않는지 확인 해야 합니다. 예기치 않은 문자로 인해 디렉터리 동기화가 실패 하는 것은 아니지만 경고를 반환할 수 있습니다. 잘못 된 문자가 있으면 디렉터리 동기화가 실패 합니다.
  
AD DS 사용자 중 일부에 중복 된 특성이 하나 이상 있는 경우에도 디렉터리 동기화가 실패 합니다. 각 사용자에 게는 고유한 특성이 있어야 합니다.
  
준비 해야 하는 특성은 다음과 같습니다.
  
- **n**
    
  - 사용자 개체에 특성이 있으면 Microsoft 365와 동기화 됩니다.
  - 이 특성이 사용자 개체에 있는 경우에는 해당 특성에 대 한 값이 있어야 합니다. 즉, 특성을 비워 두면 안 됩니다.
  - 최대 문자 수: 256
    
- **givenName**
    
  - 특성이 사용자 개체에 있는 경우 Microsoft 365와 동기화 되지만 Microsoft 365에서는이를 필요로 하거나 사용 하지 않습니다.
  - 최대 문자 수: 64
    
- **메일**
    
  - 특성 값은 디렉터리 내에서 고유 해야 합니다.
    
    > [!NOTE]
    > 중복 된 값이 있는 경우 값이 있는 첫 번째 사용자가 동기화 됩니다. 이후 사용자는 Microsoft 365에 나타나지 않습니다. 두 사용자가 Microsoft 365에 나타나려면 Microsoft 365의 값을 수정 하거나 AD DS의 값을 모두 수정 해야 합니다. 
  
- **mailNickname** (Exchange 별칭) 
    
  - 특성 값은 마침표 (.)로 시작할 수 없습니다.
  - 특성 값은 디렉터리 내에서 고유 해야 합니다.
  
    > [!NOTE]
    > 동기화 된 이름에서 밑줄 ("_")은이 특성의 원래 값에 잘못 된 문자가 있음을 나타냅니다. 이 특성에 대 한 자세한 내용은 [Exchange alias 특성](https://docs.microsoft.com/powershell/module/exchange/mailboxes/set-mailbox?view=exchange-ps)을 참조 하십시오.
    >
      
- **proxyAddresses**
    
  - 여러 값 특성
  - 값 당 최대 문자 수: 256
  - 특성 값에는 공백이 없어야 합니다.
  - 특성 값은 디렉터리 내에서 고유 해야 합니다.
  - 유효 하지 않은 문자: \< \> ();, [] "'
    
    잘못 된 문자는 형식 구분 기호 뒤에 있는 문자에 적용 되 고, SMTP:User@contso.com는 허용 되지만 SMTP:user:M@contoso.com는 그렇지 않습니다.
    
    > [!IMPORTANT]
    > 모든 SMTP (Simple Mail Transport Protocol) 주소는 전자 메일 메시징 표준을 준수 해야 합니다. 중복 또는 원치 않는 주소가 있으면 [Exchange에서 중복 및 원하지 않는 프록시 주소 제거](https://go.microsoft.com/fwlink/?LinkId=293860)도움말 항목을 참조 하십시오. 
  
- **sAMAccountName**
    
  - 최대 문자 수: 20
  - 특성 값은 디렉터리 내에서 고유 해야 합니다.
  - 유효 하지 않은 문자: [\ "|,/: \< \> + =;? \* ']
  - 사용자의 **sAMAccountName** 특성이 유효 하지 않지만 **userPrincipalName** 특성이 유효한 경우 사용자 계정이 Microsoft 365에서 만들어집니다. 
  - **SAMAccountName** 및 **userPrincipalName** 이 둘 다 유효 하지 않은 경우 AD DS **userPrincipalName** 특성을 업데이트 해야 합니다. 
    
- **sn** (성) 
    
  - 특성이 사용자 개체에 있는 경우 Microsoft 365와 동기화 되지만 Microsoft 365에서는이를 필요로 하거나 사용 하지 않습니다.
    
- **targetAddress**
    
    사용자에 대해 채워지는 **targetAddress** 특성 (예: SMTP:tom@contoso.com)이 MICROSOFT 365 GAL에 나타나야 합니다. 타사 메시징 마이그레이션 시나리오에서이를 위해서는 AD DS에 대 한 Microsoft 365 스키마 확장이 필요 합니다. Microsoft 365 스키마 확장은 또한 AD DS에서 디렉터리 동기화 도구를 사용 하 여 채워지는 Microsoft 365 개체를 관리 하는 데 유용한 다른 특성도 추가 합니다. 예를 들어, 숨겨진 사서함 또는 메일 그룹을 관리 하기 위한 **msExchHideFromAddressLists** 특성이 추가 됩니다. 
   
  - 최대 문자 수: 256
  - 특성 값에는 공백이 없어야 합니다.
  - 특성 값은 디렉터리 내에서 고유 해야 합니다.
  - 유효 하지 않은 문자: \ \< \> ();, [] "
  - 모든 SMTP (Simple Mail Transport Protocol) 주소는 전자 메일 메시징 표준을 준수 해야 합니다.
    
- **userPrincipalName**
    
  - **UserPrincipalName** 특성은 사용자 이름 뒤에 @ 기호와 도메인 이름 (예: user@contoso.com)이 오는 인터넷 스타일 로그인 형식 이어야 합니다. 모든 SMTP (Simple Mail Transport Protocol) 주소는 전자 메일 메시징 표준을 준수 해야 합니다.
  - **UserPrincipalName** 특성의 최대 문자 수는 113입니다. 다음과 같이 @ 기호 앞 이나 뒤에 특정 문자를 사용할 수 있습니다. 
  - @ 기호 앞에 있는 사용자 이름의 최대 문자 수: 64
  - @ 기호 뒤에 있는 도메인 이름의 최대 문자 수: 48
  - 유효 하지 않은 문자: \% &amp; \* +/=? { } | \< \> ( ) ; : , [ ] " '
  - 움라우트도 잘못 된 문자입니다.
  - @ 문자는 각 **userPrincipalName** 값에 필요 합니다. 
  - @ 문자는 각 **userPrincipalName** 값의 첫 번째 문자일 수 없습니다. 
  - 사용자 이름은 마침표 (.), 앰퍼샌드 ( &amp; ), 공백 또는 @ 기호로 끝날 수 없습니다.
  - 사용자 이름에는 공백을 포함할 수 없습니다.
  - 라우팅 가능한 도메인을 사용 해야 합니다. 예를 들어 로컬 또는 내부 도메인은 사용할 수 없습니다.
  - 유니코드는 밑줄 문자로 변환됩니다.
  - **userPrincipalName** 는 디렉터리에 중복 된 값을 포함할 수 없습니다. 

Idfix 도구를 사용 하 여 [디렉터리 특성 준비](prepare-directory-attributes-for-synch-with-idfix.md) 를 참조 하 여 AD DS의 특성에서 오류를 식별 합니다.
    
## <a name="3-prepare-the-userprincipalname-attribute"></a>3. userPrincipalName 특성을 준비 합니다.

Active Directory는 조직의 최종 사용자가 **sAMAccountName** 또는 **userPrincipalName**를 사용 하 여 디렉터리에 로그인 할 수 있도록 설계 되었습니다. 마찬가지로 최종 사용자는 회사 또는 학교 계정의 UPN (사용자 계정 이름)을 사용 하 여 Microsoft 365에 로그인 할 수 있습니다. 디렉터리 동기화는 AD DS에 있는 것과 동일한 UPN을 사용 하 여 Azure Active Directory에 새 사용자를 만들려고 시도 합니다. UPN은 전자 메일 주소와 같은 형식으로 지정 됩니다. 

Microsoft 365에서 UPN은 전자 메일 주소를 생성 하는 데 사용 되는 기본 특성입니다. **UserPrincipalName** (AD DS 및 Azure ad) 및 **proxyAddresses** 의 기본 전자 메일 주소를 다른 값으로 설정 하는 것이 쉽습니다. 서로 다른 값으로 설정 하면 관리자와 최종 사용자에 게 혼동이 있을 수 있습니다. 
  
혼동을 줄이려면 이러한 특성을 맞추는 것이 좋습니다. AD FS (Active Directory Federation Services) 2.0에서 single sign-on 요구 사항을 충족 하려면 Azure Active Directory 및 AD DS의 Upn이 일치 하며 유효한 도메인 네임 스페이스를 사용 하 고 있는지 확인 해야 합니다.
  
## <a name="4-add-an-alternative-upn-suffix-to-ad-ds"></a>4. AD DS에 대체 UPN 접미사 추가

사용자의 회사 자격 증명을 Microsoft 365 환경과 연결 하기 위해 대체 UPN 접미사를 추가 해야 할 수 있습니다. UPN 접미사는 UPN에서 @ 문자 오른쪽에 있는 부분입니다. Single Sign-On에 사용되는 UPN에는 문자, 숫자, 마침표, 대시 및 밑줄을 포함할 수 있으며 다른 유형의 문자는 포함할 수 없습니다.
  
Active Directory에 대체 UPN 접미사를 추가 하는 방법에 대 한 자세한 내용은 [디렉터리 동기화 준비]( https://go.microsoft.com/fwlink/p/?LinkId=525430)를 참조 하세요.
  
## <a name="5-match-the-ad-ds-upn-with-the-microsoft-365-upn"></a>5. AD DS UPN과 Microsoft 365 UPN을 일치 시킵니다.

디렉터리 동기화를 이미 설정한 경우 사용자의 Microsoft 365 UPN이 AD DS에 정의 된 사용자의 AD DS UPN과 일치 하지 않을 수 있습니다. 도메인이 확인되기 전에 사용자에게 라이선스가 할당된 경우 이와 같은 문제가 발생할 수 있습니다. 이 문제를 해결 하려면 [PowerShell을](https://go.microsoft.com/fwlink/p/?LinkId=396730) 사용 하 여 중복 UPN을 수정 하 여 MICROSOFT 365 upn이 회사 사용자 이름 및 도메인과 일치 하도록 사용자의 upn을 업데이트 합니다. AD DS에서 UPN을 업데이트 하 고 Azure Active Directory id와 동기화 하 고 싶은 경우 AD DS에서 변경 작업을 수행 하기 전에 Microsoft 365에서 해당 사용자의 라이선스를 제거 해야 합니다. 
  
또한 [디렉터리 동기화를 위해 라우팅할 수 없는 도메인 (예: 로컬 도메인)을 준비 하는 방법을](prepare-a-non-routable-domain-for-directory-synchronization.md)참조 하세요.


## <a name="next-steps"></a>다음 단계

디렉터리 동기화 전에 AD DS 특성의 오류를 수정 하는 데 도움이 되도록 [IdFix 도구를 사용 하 여 디렉터리 특성 준비](prepare-directory-attributes-for-synch-with-idfix.md) 를 참조 하세요.

IdFix 도구로 식별 된 모든 특성 오류를 수정 하 고 위의 1 ~ 5 단계를 수행한 경우 [디렉터리 동기화 설정을](set-up-directory-synchronization.md)참조 하십시오.
