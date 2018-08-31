---
title: Office 365 전역 관리자 계정 보호
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 4/10/2018
ms.audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Strat_O365_IP
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: 6b4ded77-ac8d-42ed-8606-c014fd947560
description: 이 세 단계를 통해 Office 365 구독에 대 한 전역 관리자 액세스를 보호 합니다.
ms.openlocfilehash: 7260e903ea007735c87ab8aa826e3b97e7bd28c1
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542162"
---
# <a name="protect-your-office-365-global-administrator-accounts"></a>Office 365 전역 관리자 계정 보호

 **요약:** 전역 관리자 계정의 손상에 따라 공격 으로부터 Office 365 구독을 보호 합니다. 
  
정보 수집을 포함 하는 Office 365 구독 및 피싱 공격의 보안 위반으로 인해 발생할은 일반적으로 Office 365 전역 관리자 계정의 자격 증명을 그대로 유지 하 여 수행 됩니다. 클라우드에서 보안은와 Microsoft 간의 파트너 관계입니다.
  
- Microsoft 클라우드 서비스의 트러스트와 보안 기초를 기반으로 구축 됩니다. Microsoft 보안 제어 기능 및 응용 프로그램 및 데이터를 보호 하는 데 도움이 되는 기능을 제공 합니다.
    
- 데이터 및 id 및, 온-프레미스 자원의 보안 및 제어 하는 클라우드 구성 요소의 보안을 보호 하는 것에 대 한 책임을 소유 합니다.
    
Microsoft는 조직를 보호 하는 기능을 제공 하지만 사용 하는 경우에 적용 됩니다. 사용 하지 않는 경우 공격에 취약 수 있습니다. 전역 관리자 계정을 보호 하려면 Microsoft 여기에 대 한 자세한 내용은 도움이 되는:
  
1. 전용된 Office 365 전역 관리자 계정을 만들고 필요한 경우에 사용 해야 합니다.
    
2. 전용된 Office 365 전역 관리자 계정에 대 한 다단계 인증을 구성 하 고 가장 강력한 형태의 보조 인증을 사용 합니다.
    
3. 사용 하도록 설정 하 고 Office 365 클라우드 앱 보안 의심 스러운 전역 관리자 계정 활동에 대 한 모니터링을 구성 합니다.
    
> [!NOTE]
> 추가 여부도 고려해 야이 문서에서는 전역 관리자 계정에 초점을 맞춥니다 있지만 eDiscovery 관리자 또는 보안 또는 규정 준수와 같은 구독에서 데이터에 액세스할 수 있는 광범위 한 권한이 있는 계정 관리자 계정 같은 방식으로 보호 해야 합니다. 
  
## <a name="step-1-create-dedicated-office-365-global-administrator-accounts-and-use-them-only-when-necessary"></a>1 단계입니다. 전용된 Office 365 전역 관리자 계정을 만들고 필요한 경우에 사용

전역 관리자 권한이 필요한 사용자 계정에 역할을 할당 하는 등의 상대적으로 적은 관리 작업을 있습니다. 따라서 전역 관리자 역할을 할당 된 일상적인 사용자 계정을 사용 하 여을 하는 대신 다음이 단계를 수행 합니다.
  
1. 전역 관리자 역할을 할당 된 사용자 계정 집합을 결정 합니다. Microsoft Azure Active Directory 모듈에 대 한 Windows PowerShell 명령 프롬프트에서이 명령을 사용 하 여이 수행할 수 있습니다.
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

2. 전역 관리자 역할 할당 된 사용자 계정 사용 하 여 Office 365 구독에 로그인 합니다.
    
3. 적어도 하나 만들고 최대 5 개까지 전역 관리자 사용자 계정을 전용 합니다. **사용 하 여 강력한 암호 최소 12 문자 깁니다.** 자세한 내용은 [강력한 암호 만들기](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password) 를 참조 하십시오. 안전한 위치에 새 계정에 대 한 암호를 저장 합니다. 
    
4. 각 새 전용된 전역 관리자 사용자 계정에 전역 관리자 역할을 할당 합니다.
    
5. Office 365에서 로그 아웃 합니다.
    
6. 새 전용된 전역 관리자 사용자 계정 중 하나를 사용 하 여 로그인 합니다.
    
7. 각 기존 사용자 계정에 대해 1 단계에서 전역 관리자 역할 할당 된 했습니다.
    
  - 전역 관리자 역할을 제거 합니다.
    
  - 해당 사용자의 작업 함수 및 책임에 적절 한 계정에 관리자 역할을 할당 합니다. Office 365의 다양 한 관리 역할에 대 한 자세한 내용은 [Office 365에 대 한 관리자 역할](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d)을 참조 하십시오.
    
8. Office 365에서 로그 아웃 합니다.
    
결과 다음과 같아야 합니다.
  
- 전역 관리자 역할을 포함 하는 구독에 있는 유일한 사용자 계정이 새 집합 전용된 전역 관리자 계정입니다. 다음 PowerShell 명령을 사용 하 여이 확인 합니다.
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

- 구독을 관리하는 다른 모든 일상적인 사용자 계정에는 해당 업무와 연관된 관리자 역할이 할당되어 있습니다.
    
이 시점부터 이후로, 전역 관리자 권한이 필요로 하는 작업에 대해서만 전용된 전역 관리자 계정을 사용 하 여 로그인 있습니다. 다른 모든 Office 365 관리는 사용자 계정에 다른 관리 역할을 할당 하 여 작업을 수행 해야 합니다.
  
> [!NOTE]
> 예,이 경우 일상적인 사용자 계정으로 로그 아웃 하 고 전용된 전역 관리자 계정을 사용 하 여 로그인 하기 위한 추가 단계 해야 합니다. 하지만이 전역 관리자 작업에 대 한 경우에 따라 수행 해야 합니다. 전역 관리자 계정 위반 사항이 더 많은 단계가 필요 후 Office 365 구독을 복구 하는 것이 좋습니다. 
  
## <a name="step-2-configure-multi-factor-authentication-for-your-dedicated-office-365-global-administrator-accounts-and-use-the-strongest-form-of-secondary-authentication"></a>2 단계입니다. 전용된 Office 365 전역 관리자 계정에 대 한 다단계 인증을 구성 하 고 가장 강력한 형태의 보조 인증을 사용 하 여

전역 관리자 계정에 대 한 다단계 인증 (MFA) 계정 이름 및 암호 외의 추가 정보를 필요합니다. Office 365에는 이러한 확인 방법을 지원합니다.
  
- 전화 통화
    
- 임의로 생성 된 암호
    
- 스마트 카드 (가상 또는 실제)
    
- 생체 인식 장치
    
중소기업 클라우드 (cloud id 모델)에 저장 된 사용자 계정을 사용 하는 경우에 다음이 단계를 사용 하 여 전화 통화 나 스마트폰으로 전송 하는 텍스트 메시지 확인 코드를 사용 하 여 MFA를 구성 하려면:
  
1. [MFA를 사용 하도록 설정](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6)합니다.
    
2. 각 구성 하려면 [Office 365에 대해 2 단계 확인 설정](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) 확인 방법으로 전화 통화 또는 텍스트 메시지에 대 한 전역 관리자 계정을 전용입니다. 
    
Office 365 하이브리드 id 모델을 사용 하는 대규모 조직의 경우 기타 옵션을 확인 해야 합니다. 보다 강력한 보조 인증 방법에 대 한 전체 보안 인프라에 이미 있는 경우 다음이 단계를 사용 합니다.
  
1. [MFA를 사용 하도록 설정](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6)합니다.
    
2. 각 구성 하려면 [Office 365에 대해 2 단계 확인 설정](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) 전용 적절 한 확인 방법에 대 한 전역 관리자 계정이 사용 됩니다. 
    
원하는 보다 강력한 확인 방법에 대 한 보안 인프라 전체 및 Office 365 MFA에 대 한 작동에 없는 경우는 것이 좋습니다 MFA와 전용된 전역 관리자 계정을 구성 하는 전화 또는 텍스트 메시지를 사용 하 여 확인 코드를 중간 보안 조치로 전역 관리자 계정에 대 한 스마트 전화에 전송 합니다. MFA에서 제공 하는 추가 보호 하지 않고 전용된 전역 관리자 계정의 두지 마십시오.
  
자세한 내용은 [Office 365 배포에 대한 다단계 인증 계획](https://support.office.com/article/043807b2-21db-4d5c-b430-c8a6dee0e6ba)을 참조하세요.
  
MFA 및 PowerShell Office 365 서비스에 연결할 [이 문서](https://blogs.technet.microsoft.com/solutions_advisory_board/2017/04/27/connect-to-office-365-services-with-multifactor-authentication-mfa-and-powershell/)를 참조 하십시오.
  
## <a name="step-3-monitor-for-suspicious-global-administrator-account-activity"></a>3 단계입니다. 의심 스러운 전역 관리자 계정 작업에 대 한 모니터링

Office 365 클라우드 응용 프로그램 보안을 사용 하면 사용자에 게 알리도록 구독에서 의심 스러운 동작의 정책을 만들 수 있습니다. 클라우드 App 보안은 Office 365 e 5에 되었지만 별도 서비스도도 제공 됩니다. 예, Office 365 e 5에 하지 않은 경우 전역 관리자, 보안 관리자 및 규정 준수 관리자 역할에 할당 된 사용자 계정에 대 한 개별 클라우드 앱 보안 라이선스를 구입할 수 있습니다.
  
Office 365 구독에서 클라우드 응용 프로그램 보안을 설치한 경우 다음이 단계를 따라 합니다.
  
1. 보안 관리자 또는 규정 준수 관리자 역할에 할당 된 계정 사용 하 여 Office 365 포털에 로그인 합니다.
    
2. [Office 365 클라우드 응용 프로그램 보안 설정](https://support.office.com/article/ba919c73-d021-404d-9850-eec57e78678c)입니다.
    
3. 사용자에 게 권한이 부여 된 관리 작업의 비정상적인 패턴의 전자 메일을 여 알리도록 [Office 365 클라우드 앱 보안에서 예외 탐지 정책](https://support.office.com/article/88935b4e-dcb1-47f1-8aca-1bf8fb069db6) 에 검토 합니다. 
    
보안 관리자 역할에 사용자 계정을 추가 하려면 전용된 전역 관리자 계정과 MFA를 사용 하 여 [Office 365 PowerShell에 연결](https://technet.microsoft.com/library/dn975125.aspx#step3) 하 고 사용자 계정의 사용자 계정 이름 입력 한 다음 이러한 명령을 실행 합니다. 
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upn -RoleName "Security Administrator"
```

규정 준수 관리자 역할에 사용자 계정을 추가 하려면 사용자 계정의 사용자 계정 이름에 입력 하 고 이러한 명령을 실행 합니다.
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress  $upn -RoleName "Compliance Administrator"
```

## <a name="additional-protections-for-enterprise-organizations"></a>엔터프라이즈 조직에 대 한 추가 보호

전역 관리자 계정과 해당를 사용 하 여 수행 하는 구성 되었는지 확인 하려면 이러한 추가 방법을 사용 하는 1-3 단계를 최대한 안전 된 것입니다.
  
### <a name="privileged-access-workstation-paw"></a>액세스 권한을된 워크스테이션 (발)

권한이 높은 작업을 실행 하는 보안을 최대한 지 확인 하려면를 발을 사용 합니다. 한 발은는 전역 관리자 계정에 필요한 Office 365 구성 등의 중요 한 구성 작업에만 사용 되는 전용된 컴퓨터입니다. 이 컴퓨터는 인터넷 검색 또는 전자 메일에 대 한 매일 사용 되지 않으므로, 아주 좋음 인터넷 공격 및 위협 으로부터 보호 됩니다.
  
발을 설정 하는 방법에 대 한 지침을 참조 하십시오. [http://aka.ms/cyberpaw](http://aka.ms/cyberpaw)합니다.
  
### <a name="azure-ad-privileged-identity-management-pim"></a>Azure AD 권한 Id 관리 (p i M)

것이 아니라 전역 관리자 역할을 영구적으로 할당 하 여 전역 관리자 계정, 필요할 때 전역 관리자 역할의 주문형, 적시에 배정 수 있도록 Azure AD p i M을 사용할 수 있습니다.
  
영구 관리 되 고 하 여 전역 관리자 계정 하는 대신 사용할 수 있는 관리자 데이터베이스가 됩니다. 다른 사용자가 필요한 때까지 전역 관리자 역할을 활성화 되지 않았습니다. 미리 정의 된 시간 동안 전역 관리자 계정에 전역 관리자 역할을 추가 하는 정품 인증 프로세스를 완료 합니다. 시간에는 다음이 만료 되 면 p i M 전역 관리자 계정에서 전역 관리자 역할을 제거 합니다.
  
P i M를 사용 하 여이 프로세스는 공격 및 악의적인 사용자가 사용 하 여 전역 관리자 계정 취약 시간을 크게 감소 합니다.
  
자세한 내용은 [Azure AD 권한 구성 Id 관리](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure)를 참조 하십시오.
  
> [!NOTE]
> P i M Azure Active Directory 프리미엄 P2, 엔터프라이즈 이동성 + 보안 (EMS) e 5에 포함 된 함께 사용할 수 없거나 전역 관리자 계정에 대 한 개별 라이선스를 구입할 수 있습니다. 
  
### <a name="security-information-and-event-management-siem-software-for-office-365-logging"></a>Office 365 로깅에 대 한 보안 정보 및 이벤트 관리 (SIEM) 소프트웨어

서버에서 실행 하는 SIEM 소프트웨어 보안 경고 및 응용 프로그램 및 네트워크 하드웨어에서 만든 이벤트의 실시간 분석을 수행 합니다. 분석 및 보고 기능에서 Office 365 보안 경고 및 이벤트를 포함 하도록 SIEM 서버를 허용 하려면 SIEM 시스템에서이 통합 합니다.
  
- Azure AD
    
    자세한 내용은 [SIEM 시스템에 Azure 리소스에서 통합 대상 로그](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview)를 참조 하십시오.
    
- Office 365 Cloud App Security
    
    자세한 내용은 [Office 365 클라우드 응용 프로그램 보안 사용 하 여 SIEM 서버 통합](https://support.office.com/article/dd6d2417-49c4-4de6-9294-67fdabbf8532)을 참조 하십시오.
    
## <a name="next-step"></a>다음 단계

[Office 365에 대 한 보안 모범 사례](https://support.office.com/article/9295e396-e53d-49b9-ae9b-0b5828cdedc3)를 참조 하십시오.
  

