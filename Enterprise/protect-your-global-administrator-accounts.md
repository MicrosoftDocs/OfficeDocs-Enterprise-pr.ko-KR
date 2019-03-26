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
description: 다음 세 가지 단계를 수행 하 여 Office 365 구독에 대 한 전역 관리자 액세스를 보호 합니다.
ms.openlocfilehash: 23d47ec1f5fc4126113dd69e1ac6400d003ca41f
ms.sourcegitcommit: 4ef8e113fa20b539de1087422455fc26ff123d55
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/19/2019
ms.locfileid: "30573922"
---
# <a name="protect-your-office-365-global-administrator-accounts"></a>Office 365 전역 관리자 계정 보호

 **요약:** 전역 관리자 계정의 손상에 따라 공격 으로부터 Office 365 구독을 보호 합니다. 
  
정보 수집 및 피싱 공격을 비롯 한 office 365 구독의 보안 침해는 일반적으로 office 365 전역 관리자 계정의 자격 증명을 손상 시켜 수행 합니다. 클라우드의 보안은 사용자와 Microsoft 간의 파트너 관계입니다.
  
- Microsoft 클라우드 서비스는 신뢰 및 보안을 기반으로 구축 됩니다. Microsoft는 데이터와 응용 프로그램을 보호 하는 데 도움이 되는 보안 제어 및 기능을 제공 합니다.
    
- 사용자의 데이터 및 id를 보호 하 고, 온-프레미스 리소스의 보안을 관리 하 고, 사용자가 제어 하는 클라우드 구성 요소의 보안을 담당 합니다.
    
Microsoft는 조직을 보호 하기 위한 기능을 제공 하지만, 이러한 기능은 사용 하는 경우에만 적용 됩니다. 사용 하지 않는 경우 공격에 취약할 수 있습니다. 전역 관리자 계정을 보호 하기 위해 Microsoft는 다음에 대 한 자세한 지침을 제공 하는 데 도움이 되는 정보를 제공 합니다.
  
1. 전용 Office 365 전역 관리자 계정을 만들고 필요한 경우에만이를 사용 합니다.
    
2. 전용 Office 365 전역 관리자 계정에 대해 multi-factor authentication을 구성 하 고 가장 강력한 형태의 보조 인증을 사용 합니다.
    
3. 의심 스러운 전역 관리자 계정 활동을 모니터링 하도록 Office 365 Cloud App Security를 사용 하도록 설정 하 고 구성 합니다.
    
> [!NOTE]
> 이 문서에서는 전역 관리자 계정에 초점을 맞추었습니다 하지만 구독에 포함 된 데이터에 액세스 하는 데 필요한 추가 계정 (예: eDiscovery 관리자 또는 보안 또는 규정 준수)이 있는지도 고려해 야 합니다. 관리자 계정을 동일한 방식으로 보호 해야 합니다. 
  
## <a name="step-1-create-dedicated-office-365-global-administrator-accounts-and-use-them-only-when-necessary"></a>1단계. 전용 Office 365 전역 관리자 계정을 만들고 필요한 경우에만이를 사용 합니다.

전역 관리자 권한이 필요한 관리 작업 (예: 사용자 계정에 역할 할당)은 비교적 적습니다. 따라서 전역 관리자 역할이 할당 된 일상적인 사용자 계정을 사용 하는 대신, 다음 단계를 수행 합니다.
  
1. 전역 관리자 역할이 할당 된 사용자 계정 집합을 확인 합니다. Windows PowerShell 용 Microsoft Azure Active Directory 모듈 명령 프롬프트에서 다음 명령을 사용 하 여이 작업을 수행할 수 있습니다.
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

2. 전역 관리자 역할이 할당 된 사용자 계정으로 Office 365 구독에 로그인 합니다.
    
3. 최대 5 개의 전용 전역 관리자 사용자 계정을 하나 이상 만듭니다. **최소 12 자 이상의 강력한 암호를 사용 합니다.** 자세한 내용은 [강력한 암호 만들기를](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password) 참조 하세요. 새 계정에 대 한 암호를 안전한 위치에 저장 합니다. 
    
4. 전역 관리자 역할을 각각의 새 전용 전역 관리자 사용자 계정에 할당 합니다.
    
5. Office 365에서 로그 아웃 합니다.
    
6. 새로운 전용 전역 관리자 사용자 계정 중 하나를 사용 하 여 로그인 합니다.
    
7. 1 단계에서 전역 관리자 역할이 할당 된 각 기존 사용자 계정에 대해 다음을 수행 합니다.
    
  - 전역 관리자 역할을 제거 합니다.
    
  - 해당 사용자의 작업 기능 및 책임에 해당 하는 관리자 역할을 계정에 할당 합니다. office 365의 다양 한 관리자 역할에 대 한 자세한 내용은 [office 365 관리자 역할 정보](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d)를 참조 하세요.
    
8. Office 365에서 로그 아웃 합니다.
    
결과는 다음과 같습니다.
  
- 구독에서 전역 관리자 역할이 있는 사용자 계정만 새 전용 전역 관리자 계정 집합입니다. 다음 PowerShell 명령을 사용 하 여이를 확인 합니다.
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

- 구독을 관리하는 다른 모든 일상적인 사용자 계정에는 해당 업무와 연관된 관리자 역할이 할당되어 있습니다.
    
이 순간 부터는 전역 관리자 권한이 필요한 작업에 대해서만 전용 전역 관리자 계정으로 로그인 합니다. 다른 모든 Office 365 관리는 사용자 계정에 다른 관리 역할을 할당 하 여 수행 해야 합니다.
  
> [!NOTE]
> 예, 일상적인 사용자 계정으로 로그 아웃 하 고 전용 전역 관리자 계정을 사용 하 여 로그인 하려면 추가 단계가 필요 합니다. 하지만이 작업을 가끔씩만 수행 하면 됩니다. 전역 관리자 계정 위반 후에 Office 365 구독을 복구 하려면 많은 단계가 필요 합니다. 
  
## <a name="step-2-configure-multi-factor-authentication-for-your-dedicated-office-365-global-administrator-accounts-and-use-the-strongest-form-of-secondary-authentication"></a>2단계. 전용 Office 365 전역 관리자 계정에 대해 multi-factor authentication을 구성 하 고 가장 강력한 형태의 보조 인증 사용

전역 관리자 계정에 대 한 MFA (multi-factor authentication)에는 계정 이름 및 암호 외에 추가 정보가 필요 합니다. Office 365에서는 다음과 같은 확인 방법을 지원 합니다.
  
- 전화 통화
    
- 임의로 생성된 암호
    
- 스마트 카드(가상 또는 실제)
    
- 생체 인식 장치
    
클라우드에만 저장 된 사용자 계정을 사용 하는 소규모 회사 인 경우 (클라우드 id 모델) 이러한 단계를 사용 하 여 전화 통화 또는 스마트 전화로 전송 된 텍스트 메시지 확인 코드를 사용 하 여 MFA를 구성 합니다.
  
1. [MFA를 사용 하도록 설정](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6)합니다.
    
2. [Office 365에 대 한 2 단계 인증을 설정](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) 하 여 전화 통화 또는 문자 메시지에 대 한 각 전용 전역 관리자 계정을 확인 방법으로 구성 합니다. 
    
Office 365 하이브리드 id 모델을 사용 하는 조직 규모가 큰 경우에는 더 많은 확인 옵션을 사용할 수 있습니다. 더 강력한 보조 인증 방법으로 보안 인프라가 이미 마련 되어 있는 경우 다음 단계를 사용 합니다.
  
1. [MFA를 사용 하도록 설정](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6)합니다.
    
2. [Office 365에 대 한 2 단계 인증을 설정](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) 하 여 적절 한 확인 방법에 대해 각 전용 전역 관리자 계정을 구성 합니다. 
    
원하는 보다 강력한 확인 방법의 보안 인프라가 제대로 작동 하지 않고 Office 365 MFA에 적합 하지 않은 경우 전화 통화 또는 문자 메시지를 사용 하 여 MFA로 전용 전역 관리자 계정을 구성 하는 것이 좋습니다. 중간 보안 조치로 전역 관리자 계정의 스마트 전화로 전송 되는 확인 코드입니다. MFA에서 제공 하는 추가 보호를 사용 하지 않고 전용 전역 관리자 계정을 그대로 사용 하지 마십시오.
  
자세한 내용은 [Office 365 배포에 대한 다단계 인증 계획](https://support.office.com/article/043807b2-21db-4d5c-b430-c8a6dee0e6ba)을 참조하세요.
  
MFA 및 PowerShell을 사용 하 여 Office 365 서비스에 연결 하려면 [이 문서](https://blogs.technet.microsoft.com/solutions_advisory_board/2017/04/27/connect-to-office-365-services-with-multifactor-authentication-mfa-and-powershell/)를 참조 하세요.
  
## <a name="step-3-monitor-for-suspicious-global-administrator-account-activity"></a>3단계. 의심 스러운 전역 관리자 계정 활동에 대 한 모니터링

Office 365 Cloud App Security를 사용 하 여 구독에서 의심 스러운 동작을 알리는 정책을 만들 수 있습니다. Cloud App Security는 Office 365 E5에 기본 제공 되지만 별도의 서비스로도 사용할 수 있습니다. 예를 들어, Office 365 E5가 없는 경우 전역 관리자, 보안 관리자 및 준수 관리자 역할이 할당 된 사용자 계정에 대해 개별 Cloud App Security 라이선스를 구입할 수 있습니다.
  
Office 365 구독에 Cloud App Security가 있는 경우 다음 단계를 사용 합니다.
  
1. 보안 관리자 또는 준수 관리자 역할이 할당 된 계정으로 Microsoft 365 관리 센터에 로그인 합니다.
    
2. [Office 365 Cloud App Security를 설정](https://support.office.com/article/ba919c73-d021-404d-9850-eec57e78678c)합니다.
    
3. [Office 365 Cloud App Security에서 변칙 검색 정책을](https://support.office.com/article/88935b4e-dcb1-47f1-8aca-1bf8fb069db6) 검토 하 여 권한이 있는 관리 활동의 비정상 패턴을 전자 메일로 알려 줍니다. 
    
사용자 계정을 보안 관리자 역할에 추가 하려면 전용 전역 관리자 계정 및 MFA를 사용 하 여 [Office 365 PowerShell에 연결](https://technet.microsoft.com/library/dn975125.aspx#step3) 하 고 사용자 계정의 사용자 계정 이름을 입력 한 후 다음 명령을 실행 합니다. 
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upn -RoleName "Security Administrator"
```

준수 관리자 역할에 사용자 계정을 추가 하려면 사용자 계정의 사용자 계정 이름을 입력 하 고 다음 명령을 실행 합니다.
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress  $upn -RoleName "Compliance Administrator"
```

## <a name="additional-protections-for-enterprise-organizations"></a>엔터프라이즈 조직에 대 한 추가 보호

1-3 단계를 수행한 후에는 이러한 추가 방법을 사용 하 여 전역 관리자 계정 및이 계정을 사용 하 여 수행 하는 구성이 최대한 안전한 지 확인 합니다.
  
### <a name="privileged-access-workstation-paw"></a>발 없는 (권한이 부여 된 액세스 워크스테이션)

높은 권한의 작업 실행이 최대한 안전한 지 확인 하려면 발 없는를 사용 합니다. 발 없는는 전역 관리자 계정이 필요한 Office 365 구성 같은 중요 한 구성 작업에만 사용 되는 전용 컴퓨터입니다. 이 컴퓨터는 인터넷 브라우징이 나 전자 메일에 대해 매일 사용 되지 않으므로 인터넷 공격 및 위협 으로부터 보호 되는 것이 좋습니다.
  
발 없는를 설정 하는 방법에 대 한 자세한 내용은 [http://aka.ms/cyberpaw](http://aka.ms/cyberpaw)를 참조 하세요.
  
### <a name="azure-ad-privileged-identity-management-pim"></a>Azure AD PIM (권한 부여 id 관리)

전역 관리자 계정을 전역 관리자 역할에 영구적으로 할당 하는 대신 Azure AD PIM을 사용 하 여 필요에 따라 전역 관리자 역할을 주문형으로 할당 하도록 설정할 수 있습니다.
  
전역 관리자 계정 대신 영구 관리자가 됩니다. 전역 관리자 역할은 사용자가 필요한 경우에만 비활성화 됩니다. 그런 다음 정품 인증 프로세스를 완료 하 여 전역 관리자 계정에 미리 정의 된 시간에 대 한 역할을 추가 합니다. 시간이 만료 되 면 PIM은 전역 관리자 계정에서 전역 관리자 역할을 제거 합니다.
  
PIM 및이 프로세스를 사용 하면 악의적인 사용자가 공격 하 고 사용할 수 있는 전역 관리자 계정의 시간이 크게 줄어듭니다.
  
자세한 내용은 [Configure Azure AD 권한이 있는 id 관리](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure)를 참조 하세요.
  
> [!NOTE]
> PIM은 EMS (Enterprise Mobility + Security) E5에 포함 되어 있는 Azure Active Directory Premium P2와 함께 사용할 수 있거나, 전역 관리자 계정에 대 한 개별 라이선스를 구입할 수 있습니다. 
  
### <a name="security-information-and-event-management-siem-software-for-office-365-logging"></a>Office 365 용 siem (보안 정보 및 이벤트 관리) 소프트웨어

siem 소프트웨어 서버에서 실행 되는 응용 프로그램 및 네트워크 하드웨어에 의해 생성 되는 이벤트에 대 한 실시간 분석을 수행 합니다. siem 서버에서 분석 및 보고 기능에 Office 365 보안 경고 및 이벤트를 포함 하도록 허용 하려면 siem 시스템에서이를 통합 합니다.
  
- Azure AD
    
    자세한 내용은 [Azure 리소스의 로그를 siem 시스템에 통합](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview)을 참조 하세요.
    
- Office 365 Cloud App Security
    
    자세한 내용은 [siem server를 Office 365 Cloud App Security와 통합](https://support.office.com/article/dd6d2417-49c4-4de6-9294-67fdabbf8532)을 참조 하세요.
    
## <a name="next-step"></a>다음 단계

[Office 365에 대 한 보안 모범 사례를](https://support.office.com/article/9295e396-e53d-49b9-ae9b-0b5828cdedc3)참조 하세요.
  

