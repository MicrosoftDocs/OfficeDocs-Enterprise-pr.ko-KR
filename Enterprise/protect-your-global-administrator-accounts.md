---
title: Microsoft 365 전역 관리자 계정 보호
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 06/15/2020
audience: Admin
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
f1.keywords:
- NOCSH
ms.assetid: 6b4ded77-ac8d-42ed-8606-c014fd947560
description: Microsoft 365 구독에 대 한 전역 관리자 액세스를 보호 합니다.
ms.openlocfilehash: fdab22944902b554bc7fa295d189cfd2899933ef
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/22/2020
ms.locfileid: "45229764"
---
# <a name="protect-your-microsoft-365-global-administrator-accounts"></a>Microsoft 365 전역 관리자 계정 보호

*이 문서는 Microsoft 365 Enterprise 및 Office 365 Enterprise에 모두 적용 됩니다.*

정보 수집 및 피싱 공격을 포함 하 여 Microsoft 365 구독의 보안 침해는 일반적으로 Microsoft 365 전역 관리자 계정의 자격 증명을 손상 시켜 수행 합니다. 클라우드의 보안은 사용자와 Microsoft 간의 파트너 관계입니다.
  
- Microsoft 클라우드 서비스는 신뢰 및 보안을 기반으로 구축 됩니다. Microsoft는 데이터와 응용 프로그램을 보호 하는 데 도움이 되는 보안 제어 및 기능을 제공 합니다.
    
- 사용자의 데이터 및 id를 보호 하 고, 온-프레미스 리소스의 보안을 관리 하 고, 사용자가 제어 하는 클라우드 구성 요소의 보안을 담당 합니다.
    
Microsoft는 조직을 보호 하기 위한 기능을 제공 하지만, 이러한 기능은 사용 하는 경우에만 적용 됩니다. 사용 하지 않는 경우 공격에 취약할 수 있습니다. 전역 관리자 계정을 보호 하기 위해 Microsoft는 다음에 대 한 자세한 지침을 제공 하는 데 도움이 되는 정보를 제공 합니다.
  
1. 전용 Microsoft 365 전역 관리자 계정을 만들고 필요한 경우에만이를 사용 합니다.
    
2. 전용 Microsoft 365 글로벌 관리자 계정에 대해 multi-factor authentication을 구성 하 고 가장 강력한 형태의 보조 인증을 사용 합니다.
    
> [! 참고]이 문서에서는 전역 관리자 계정에 초점을 맞추었습니다 하지만 구독에 포함 된 데이터에 액세스 하는 데 필요한 추가 계정 (예: eDiscovery 관리자 또는 보안 또는 준수 관리자 계정)이 동일한 방식으로 보호 되어야 하는지 여부를 고려해 야 합니다. <br > 라이선스를 추가 하지 않고 전역 관리자 계정을 만들 수 있습니다.
  
## <a name="step-1-create-dedicated-microsoft-365-global-administrator-accounts-and-use-them-only-when-necessary"></a>1단계. 전용 Microsoft 365 전역 관리자 계정을 만들고 필요한 경우에만 사용 합니다.

전역 관리자 권한이 필요한 관리 작업 (예: 사용자 계정에 역할 할당)은 비교적 적습니다. 따라서 전역 관리자 역할이 할당 된 일상적인 사용자 계정을 사용 하는 대신, 다음 단계를 수행 합니다.
  
1. 전역 관리자 역할이 할당 된 사용자 계정 집합을 확인 합니다. 이 작업은 Graph 용 Azure 활성 (Azure AD) 디렉터리 PowerShell 명령에 대해 수행할 수 있습니다.
  
  ```powershell
  Get-AzureADDirectoryRole | where { $_.DisplayName -eq "Company Administrator" } | Get-AzureADDirectoryRoleMember | Ft DisplayName
  ```

2. 전역 관리자 역할이 할당 된 사용자 계정으로 Microsoft 365 구독에 로그인 합니다.
    
3. 최대 4 개의 전용 전역 관리자 사용자 계정을 만듭니다. **최소 12 자 이상의 강력한 암호를 사용 합니다.** 자세한 내용은 [강력한 암호 만들기를](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password) 참조 하세요. 새 계정에 대 한 암호를 안전한 위치에 저장 합니다. 
    
4. 전역 관리자 역할을 각각의 새 전용 전역 관리자 사용자 계정에 할당 합니다.
    
5. Microsoft 365에서 로그 아웃 합니다.
    
6. 새로운 전용 전역 관리자 사용자 계정 중 하나를 사용 하 여 로그인 합니다.
    
7. 1 단계에서 전역 관리자 역할이 할당 된 각 기존 사용자 계정에 대해 다음을 수행 합니다.
    
  - 전역 관리자 역할을 제거 합니다.
    
  - 해당 사용자의 작업 기능 및 책임에 해당 하는 관리자 역할을 계정에 할당 합니다. Microsoft 365의 다양 한 관리자 역할에 대 한 자세한 내용은 [관리 역할 정보](https://docs.microsoft.com/office365/admin/add-users/about-admin-roles)를 참조 하십시오.
    
8. Microsoft 365에서 로그 아웃 합니다.
    
결과는 다음과 같습니다.
  
- 구독에서 전역 관리자 역할이 할당된 사용자 계정은 새로운 전용 전역 관리자 계정 집합뿐입니다. 다음 PowerShell 명령을 사용 하 여이를 확인 합니다.
    
  ```powershell
  Get-AzureADDirectoryRole | where { $_.DisplayName -eq "Company Administrator" } | Get-AzureADDirectoryRoleMember | Ft DisplayName
  ```

- 구독을 관리하는 다른 모든 일상적인 사용자 계정에는 업무 책임과 연관된 관리자 역할이 할당되어 있습니다.
    
이 순간 부터는 전역 관리자 권한이 필요한 작업에 대해서만 전용 전역 관리자 계정으로 로그인 합니다. 다른 모든 Microsoft 365 관리는 사용자 계정에 다른 관리 역할을 할당 하 여 수행 해야 합니다.
  
> [!NOTE]
> 이렇게 하려면 일상적인 사용자 계정으로 로그 아웃 하 고 전용 전역 관리자 계정으로 로그인 하기 위한 추가 단계가 필요 합니다. 하지만이 작업을 가끔씩만 수행 하면 됩니다. 전역 관리자 계정 위반 후 Microsoft 365 구독을 복구 하려면 많은 단계가 필요 합니다.
  
## <a name="step-2-configure-multi-factor-authentication-for-your-dedicated-microsoft-365-global-administrator-accounts-and-use-the-strongest-form-of-additional-verification"></a>2단계. 전용 Microsoft 365 전역 관리자 계정에 대해 multi-factor authentication을 구성 하 고 가장 강력한 형태의 추가 확인을 사용 합니다.

MFA (multi-factor authentication)에는 계정 이름 및 암호 외에 추가 정보가 필요 합니다. Microsoft 365에서는 다음과 같은 추가 확인 방법을 지원 합니다.
  
- Microsoft Authenticator 앱

- 전화 통화
    
- 문자 메시지를 통해 보낸 임의로 생성 되는 확인 코드
    
- 스마트 카드(가상 또는 실제)
    
- 생체 인식 장치
    
>[!Note]
>국내 표준 및 기술 (NIST) 표준을 준수 해야 하는 조직의 경우 전화 통화 또는 문자 메시지 기반 추가 확인 방법을 사용 하는 것이 제한 됩니다. 세부 정보를 보려면 [여기](https://pages.nist.gov/800-63-FAQ/#q-b01) 를 클릭 하십시오.
>

클라우드에만 저장 된 사용자 계정을 사용 하는 소규모 회사 인 경우 (클라우드 전용 id 모델) 이러한 단계를 사용 하 여 전화 통화 또는 스마트 전화로 전송 되는 텍스트 메시지 확인 코드를 사용 하 여 MFA를 구성 합니다.
  
1. [MFA를 설정](https://docs.microsoft.com/office365/admin/security-and-compliance/set-up-multi-factor-authentication)합니다.
    
2. [Microsoft 365에 대 한 MFA를 설정](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) 하 여 전화 통화 또는 문자 메시지에 대 한 각 전용 전역 관리자 계정을 확인 방법으로 구성 합니다. 
    
Microsoft 365 하이브리드 id 모델을 사용 하는 대규모 조직인 경우 더 많은 확인 옵션을 사용할 수 있습니다. 더 강력한 보조 인증 방법으로 보안 인프라가 이미 마련 되어 있는 경우 다음 단계를 사용 합니다.
  
1. [MFA를 설정](https://docs.microsoft.com/office365/admin/security-and-compliance/set-up-multi-factor-authentication)합니다.
    
2. [새 전역 관리자 계정에 대해 MFA를 설정](https://support.office.com/article/set-up-your-microsoft-365-sign-in-for-multi-factor-authentication-ace1d096-61e5-449b-a875-58eb3d74de14) 하 여 적절 한 확인 방법에 대해 각 전용 전역 관리자 계정을 구성 합니다. 
    
원하는 보다 강력한 확인 방법에 대 한 보안 인프라가 적절 하 게 제공 되지 않고 Microsoft 365 MFA에 대해 작동 하는 경우 Microsoft 인증자 앱, 전화 통화 또는 전역 관리자 계정의 스마트 전화로 전송 되는 텍스트 메시지 확인 코드를 임시 보안 조치로 사용 하 여 MFA를 사용 하 여 전용 전역 관리자 계정을 구성 하는 것이 좋습니다. MFA에서 제공 하는 추가 보호를 사용 하지 않고 전용 전역 관리자 계정을 그대로 사용 하지 마십시오.
  
자세한 내용은 [Microsoft 365 배포에 대 한 다단계 인증 계획](https://docs.microsoft.com/office365/admin/security-and-compliance/multi-factor-authentication-plan)을 참조 하세요.
  
MFA 및 PowerShell을 사용 하 여 Microsoft 365 서비스에 연결 하려면 다음 문서를 참조 하세요.

- [사용자 계정, 그룹 및 라이선스에 대 한 Microsoft 365 용 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell)
- [Microsoft Teams](https://docs.microsoft.com/office365/enterprise/powershell/manage-microsoft-teams-with-office-365-powershell#sign-in-with-multi-factor-authentication-mfa)
- [Exchange Online](https://docs.microsoft.com/powershell/exchange/mfa-connect-to-exchange-online-powershell?view=exchange-ps#connect-to-exchange-online-powershell-by-using-mfa)
- [SharePoint Online](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online#to-connect-with-multifactor-authentication-mfa)
- [비즈니스용 Skype Online](https://docs.microsoft.com/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell#connect-using-a-skype-for-business-online-administrator-account-with-multi-factor-authentication)

## <a name="additional-protections-for-enterprise-organizations"></a>엔터프라이즈 조직에 대 한 추가 보호

1 ~ 2 단계를 수행한 후에는 이러한 추가 방법을 사용 하 여 전역 관리자 계정 및이 계정을 사용 하 여 수행 하는 구성이 최대한 안전한 지 확인 합니다.
  
### <a name="privileged-access-workstation"></a>권한이 부여 된 액세스 워크스테이션

높은 권한 작업의 실행을 최대한 안전한 상태로 유지 하려면 권한이 부여 된 액세스 워크스테이션 (발 없는)을 사용 합니다. 발 없는는 전역 관리자 계정이 필요한 Microsoft 365 구성 같은 중요 한 구성 작업에만 사용 되는 전용 컴퓨터입니다. 이 컴퓨터는 인터넷 브라우징이 나 전자 메일에 대해 매일 사용 되지 않으므로 인터넷 공격 및 위협 으로부터 보호 되는 것이 좋습니다.
  
발 없는를 설정 하는 방법에 대 한 자세한 내용은를 참조 하세요 [https://aka.ms/cyberpaw](https://aka.ms/cyberpaw) .
  
### <a name="azure-ad-privileged-identity-management"></a>Azure AD Privileged Identity Management

전역 관리자 계정을 전역 관리자 역할에 영구적으로 할당 하는 것 보다 Azure AD PIM (권한 부여 Id 관리)을 사용 하 여 필요에 따라 전역 관리자 역할을 주문형으로 할당 하도록 설정할 수 있습니다.
  
전역 관리자 계정 대신 영구 관리자가 됩니다. 전역 관리자 역할은 사용자가 필요한 경우에만 비활성화 됩니다. 그런 다음 정품 인증 프로세스를 완료 하 여 전역 관리자 계정에 미리 정의 된 시간에 대 한 역할을 추가 합니다. 시간이 만료 되 면 PIM은 전역 관리자 계정에서 전역 관리자 역할을 제거 합니다.
  
PIM 및이 프로세스를 사용 하면 악의적인 사용자가 공격 하 고 사용할 수 있는 전역 관리자 계정의 시간이 크게 줄어듭니다.

PIM은 Microsoft 365 Enterprise E5 또는 EMS (Enterprise Mobility + Security) e 5에 포함 된 Azure AD Premium P2에 제공 되거나, 전역 관리자 계정에 대 한 개별 라이선스를 구입할 수 있습니다.
  
자세한 내용은 [AZURE AD 권한 Id 관리](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure)를 참조 하세요.
  
### <a name="security-information-and-event-management-siem-software-for-microsoft-365-logging"></a>Microsoft 365 로깅을 위한 SIEM (보안 정보 및 이벤트 관리) 소프트웨어

SIEM 소프트웨어 서버에서 실행 되는 응용 프로그램 및 네트워크 하드웨어에 의해 생성 되는 이벤트에 대 한 실시간 분석을 수행 합니다. SIEM 서버에서 Microsoft 365 보안 경고 및 이벤트를 해당 분석 및 보고 기능에 포함 하도록 허용 하려면 Azure AD를 사용자에 게 통합 합니다. [Azure 로그 통합 소개를](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview)참조 하세요.

## <a name="next-step"></a>다음 단계

Microsoft 365 구독에 대 한 id를 설정 하는 경우 다음을 참조 하세요.

- 클라우드 전용 id를 사용 하는 경우 [클라우드 전용 id](cloud-only-identities.md)
- 하이브리드 id를 사용 하 [는 경우 디렉터리 동기화 준비](prepare-for-directory-synchronization.md)

  
## <a name="see-also"></a>참고 항목

[Microsoft 365 보안 로드맵](https://docs.microsoft.com/office365/securitycompliance/security-roadmap)
