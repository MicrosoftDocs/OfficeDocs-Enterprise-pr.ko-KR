---
title: Office 365의에서 관리 기능에 액세스 권한
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 7/13/2018
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Strat_O365_IP
ms.custom: Ent_Solutions
ms.assetid: ''
description: Office 365의 액세스 권한을된 관리 기능에 대 한 자세한 내용은이 항목을 사용 하 여
ms.openlocfilehash: b2db3e16e53cca7deb2bf8fbff61b5b981f42fa6
ms.sourcegitcommit: b39b8ae3b4268d6475b54e2fdb62982b2c7d9943
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/12/2018
ms.locfileid: "20319209"
---
# <a name="privileged-access-management-in-office-365"></a>Office 365의에서 관리 기능에 액세스 권한

> [!IMPORTANT]
> 이 항목에서는 Office 365 e 5 및 고급 준수 Sku에만 현재 제공 되는 공용 베타 기능에 대 한 배포 및 구성 지침에 설명 합니다.

액세스 권한 관리 Office 365에서 권한이 부여 된 관리 작업을 통해 세분화 된 액세스 제어를 허용 합니다.  기존 관리자가 권한이 부여 된 사용자 계정은 중요 한 데이터에 대 한 순위 액세스 또는 중요 한 구성 설정에 대 한 액세스를 사용할 수 있는 침해에서 조직을 보호 하는 것이 도움이 됩니다. 권한이 부여 된 액세스 관리를 사용 하도록 설정한 후 사용자가 높은 범위가 지정 되며 시간 제한이 있는 승인 워크플로 통해 관리자 권한 및 권한 있는 작업을 완료 하려면 적시에 액세스를 요청 해야 합니다. 이 사용자가 액세스할 수 방금-만큼 충분히-중요 한 데이터 나 중요 한 구성 설정의 노출 시 키 지 않고, 수행 중인 작업을 수행할 수 있습니다. Office 365에서 권한이 부여 된 액세스 관리를 사용 하도록 설정 하면 조직 0 순위 권한으로 작동 하 고 이러한 순위 관리 액세스로 인해 발생 하는 취약점에 대 한 방어 계층을 제공할 수 있습니다. 

이 항목에 사용 하도록 설정 하 고 Office 365 조직에서 권한이 부여 된 액세스 관리를 구성 하는 과정을 안내 합니다 및 요청, 승인 및 기능 관리에 대 한 참조 (영문) 지침으로 사용 합니다. 

## <a name="before-you-begin"></a>시작하기 전에

### <a name="limited-functionality"></a>제한 된 기능
공개 베타 하는 동안 액세스 권한이 부여 된 관리 기능을 Office 365의 [Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps) 통해 사용할 수만 있습니다. 권한 관리 하는 방법을 다룹니다 Exchange 관리 cmdlet의 수준에서 작업 정의 액세스합니다. Office 365 놓을 나중에 권한이 부여 된 액세스 기능 관리 포털을 통해 사용할 수 및 다른 Office 365 작업 서비스에 적용 됩니다.

### <a name="connecting-to-exchange-online-powershell"></a>Exchange Online PowerShell 연결
이 항목의 구성 단계 과정을 안내 합니다 활성화 및 Exchange Online PowerShell을 사용 하 여 Office 365에서 권한이 부여 된 액세스를 사용 합니다. 

[다단계 인증을 사용 하 여 Exchange Online powershell 연결을](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell?view=exchange-ps) 사용 하도록 설정 하 고 조직에 대 한 액세스 권한을된 구성 하 여 Office 365 자격 증명으로 Exchange Online PowerShell에 연결 하려면의 단계를 수행 합니다.

> [!NOTE]
> Exchange Online PowerShell에 연결 하는 동안 액세스 권한을된 사용 하도록 설정 하는 단계를 사용 하 여 Office 365 조직에 대해 다단계 인증을 사용할 필요가 없습니다. 다단계 인증을 통해 연결 요청에 서명 하는 것에 대 한 권한이 부여 된 액세스에 사용 되는 OAuth 토큰을 만듭니다.

## <a name="enable-and-configure-privileged-access-management"></a>설정 하 고 액세스 권한을된 관리 구성

### <a name="step-1---create-an-approvers-group"></a>1 단계-승인자의 그룹 만들기
Office 365 관리 포털에서 **그룹**을 선택 > **그룹 추가**누른 다음 권한이 부여 된 기본 액세스 승인자에 대 한 메일 사용 가능 보안 그룹을 만듭니다. 완료 되 면 만들고 승인자 그룹을 저장 하려면 **추가** 선택 합니다.

![Office 365 관리 포털에 액세스 권한을된 승인자 화면](images/privileged-access-approvers-ui.png)

> [!NOTE] 
> 이 시간에 관리자 액세스 권한 가진 사용자만가 Office 365 특수 액세스에서 요청을 승인 수 있습니다. 나중에 승인자 그룹의 구성원 인 모든 사용자 액세스 요청 승인 됩니다.

### <a name="step-2---enable-privileged-access-in-office-365"></a>2 단계-Office 365에 대 한 액세스 권한을된 사용 하도록 설정
권한이 부여 된 액세스 권한이 부여 된 액세스 관리 액세스 제어에서 제외 하려는 시스템 계정 집합을 포함 하 여 기본 승인자 그룹 명시적으로 설정 해야 합니다. 

액세스 권한을된 사용 하도록 설정 하 고 승인자의 그룹을 할당 하려면 Exchange Online PowerShell에서 다음 명령을 실행 합니다.
```
Enable-ElevatedAccessControl -AdminGroup '<default approver group>' -SystemAccounts @('<systemAccountUPN1>','<systemAccountUPN2>')
```
예제:
```
Enable-ElevatedAccessControl -AdminGroup 'pamapprovers@fabrikam.onmicrosoft.com' -SystemAccounts @('sys1@fabrikamorg.onmicrosoft.com', sys2@fabrikamorg.onmicrosoft.com')
```

> [!NOTE]
> 그러나 기능 사용 가능 조직 내에서 특정 자동화가 되도록 시스템 계정 액세스 권한을된 의존 관계 없이 사용할 수 있는, 것이 좋습니다 이러한 제외 뛰어난 수 및 승인 고 감사를 수행 해야 허용 된 정기적으로 합니다.

### <a name="step-3---create-an-approval-policy"></a>3 단계-승인 정책 만들기
승인 정책을 사용 하면 개별 작업에서 범위가 지정 된 특정 승인 요구 사항을 정의할 수 있습니다. 승인 유형 옵션은 **자동** 또는 **수동**입니다. 

다음 명령을 실행 Exchange 온라인 승인 정책을 정의 하는 PowerShell:
```
New-ElevatedAccessApprovalPolicy -Task 'Exchange\<exchange management cmdlet name>' -ApprovalType <Manual, Auto> -ApproverGroup '<default/custom approver group>'
```
예제:
```
New-ElevatedAccessApprovalPolicy -Task 'Exchange\New-MoveRequest' -ApprovalType Manual -ApproverGroup 'mbmanagers@fabrikamorg.onmicrosoft.com'
```

## <a name="using-privileged-access-in-your-office-365-organization"></a>Office 365 조직에서 권한이 부여 된 액세스를 사용 하 여

### <a name="requesting-elevation-authorization-to-execute-tasks"></a>요청 하는 작업을 실행 하기 상승 권한 부여
한번 사용 하도록 설정, 권한이 부여 된 액세스는 연결 된 승인 정책 정의 된 모든 작업을 실행 하는 것에 대 한 승인 필요 합니다. 필요에 포함 된 작업을 실행 하는 사용자는 승인 정책을 요청 해야 하 고 작업을 실행 하는 데 필요한 사용 권한이 하기 위해 액세스 승인에 게 부여 합니다.

다음 명령을 실행 Exchange Online을 만들고 승인자의 그룹에 대 한 승인 요청을 제출 하는 PowerShell:
```
New-ElevatedAccessRequest -Task 'Exchange\<exchange management cmdlet name>' -Reason '<appropriate reason>' -DurationHours <duration in hours>
```
예제:
```
New-ElevatedAccessRequest -Task 'Exchange\New-MoveRequest' -Reason 'Attempting to fix the user mailbox error' -DurationHours 4
```
### <a name="view-status-of-elevation-requests"></a>권한 상승 요청 상태 보기
승인 요청을 만든 후 상승 요청 상태를 검토할 수 있습니다 사용 하 여 연결 된 요청 id

다음 명령을 실행 Exchange 온라인 PowerShell 특정 요청 ID에 대 한 승인 요청 상태를 볼 수 있습니다.
```
Get-ElevatedAccessRequest -Identity <request ID> | select RequestStatus
```
예제:
```
Get-ElevatedAccessRequest -Identity 28560ed0-419d-4cc3-8f5b-603911cbd450 | select RequestStatus
```

### <a name="approving-an-elevation-authorization-request"></a>권한 상승 권한 부여 요청이 승인
관련 승인자 그룹의 구성원이 전자 메일 알림을 받게 됩니다 및 요청 ID와 연결 된 요청을 승인할 수를 승인 요청을 만들 때 

다음 명령을 실행 Exchange 온라인는 상승 인증 요청을 승인 하는 PowerShell:
```
Approve-ElevatedAccessRequest -RequestId <request id> -Comment '<approval comment>'
```
예제:
```
Approve-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<approval comment>'
```
### <a name="denying-an-elevation-authorization-request"></a>권한 상승 인증 요청이 거부
그룹의 구성원은 관련 승인자 요청 ID와 연결 된 요청을 거부할 수를 승인 요청을 만들 때 

다음 명령을 실행 Exchange Online PowerShell는 상승 인증 요청을 거부 하려면:
```
Deny-ElevatedAccessRequest -RequestId <request id> -Comment '<denial comment>'
```
예제:
```
Deny-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<denial comment>'
```

### <a name="running-the-task"></a>작업을 실행합니다.
승인 권한이 부여 되 면 요청 하는 사용자 의도 한 작업을 실행할 수 있고 권한이 부여 된 액세스 권한을 부여 하 고 사용자를 대신 하 여 작업을 실행 됩니다. 승인의 요청에 대해 유효 기간 (기본 기간은 4 시간)을 하는 동안 요청자 수 의도 한 작업을 여러 번 실행 합니다. 이러한 모든 실행 기록 하 고 보안 및 규정 준수 감사를 위해 사용할 수 있게 됩니다. 

### <a name="disable-privileged-access-in-office-365"></a>Office 365에 대 한 액세스 권한을된 사용 하지 않도록 설정
필요한 경우에 Office 365에서 권한이 부여 된 액세스 관리를 비활성화할 수 있습니다. 권한 사용 하지 않도록 설정 액세스 삭제 되지 않습니다 모든 관련된 승인 정책 또는 승인자 그룹.

다음 명령을 실행 Exchange Online Powershell 액세스 권한을된 사용 하지 않도록 설정 하려면:

```
Disable-ElevatedAccessControl
```
## <a name="managed-access-to-microsoft-graph-in-microsoft-azure"></a>다음은 Microsoft Graph in Microsoft Azure에 대 한 액세스 관리

> [!IMPORTANT]
> 이 섹션에서는 Office 365 e 5 및 고급 준수 Sku에서 현재 사용할 수만 공개 베타 Microsoft Graph 기능에 대 한 배포 및 구성 지침에 설명 합니다.

Microsoft Azure의 Microsoft Graph에 대 한 관리 되는 액세스는 세분화 된 자신의 Office 365 데이터에 대 한 제어 수준을 강력 하는 조직에 도움이 되는 서비스입니다. 이 시스템에는 응용 프로그램 개발자가 해당 데이터와 의견을 대장간을 수 있습니다. 

이 시스템 액세스 권한이 부여 된 Office 365를 사용 하 여 관리 감독을 사용 하 여 Office 365 데이터에 대 한 범위가 지정 된 액세스를 허용 하는 승인 워크플로 통해 자신의 데이터에 대 한 제어를 가정 합니다. 응용 프로그램을 설치 하 고 Office 365 데이터에 액세스할 수 있어야 하는 경우 데이터에 대 한 요청 제공 됩니다.

### <a name="view-request-details"></a>요청 세부 정보 보기
Office 365 데이터에 대 한 액세스 요청에 대 한 세부 정보를 봅니다.

다음 명령을 실행 Exchange Online Powershell 데이터 요청을 보려면:
```
Get-ElevatedAccessRequest | where {$_.RequestedAccess -like '*Data Access Request*'} | select RequestorUPN, Service, RequestedAccess | fl
```
예제 출력 합니다.
```
RequestorUPN    : admin@contoso.com
Service         : Office365
RequestedAccess : Data Access Request
```

### <a name="approve-data-access-requests"></a>데이터 액세스 요청을 승인
표준 액세스 권한을된 승인 cmdlet을 통해 모든 데이터 액세스 요청을 승인할 수 있습니다.

다음 명령을 실행 Exchange 온라인 특정 요청자에 대 한 모든 데이터 요청을 승인 하는 Powershell:

```
Approve-ElevatedAccessRequest -RequestId <request id> -Comment '<approval comment>'
```
예제:
```
Approve-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<approval comment>'
```

## <a name="getting-help-and-providing-feedback"></a>도움말 및 의견을 제공 합니다.
공개 베타 하는 동안 필요에 따른 버그를 발견할 수도 있습니다 피드백 및 액세스 권한을된 관리 개선할 수 있는 방법에 대 한 추천 항목으로 확인 되었습니다. 여러분의 의견을 값 하 고 촉진 우리와 공유할 수 있습니다.
- [Office 미리 보기 Yammer 그룹](https://www.yammer.com/officeenterprisenda/#/threads/inGroup?type=in_group&feedId=14435206)에서 여러분의 의견 ad 추천 항목을 게시 합니다.
- [Office 미리 보기 VSO](https://office-previews.visualstudio.com/previews)에서 영역 경로 "Office 365 권한이 부여 된 액세스 관리"에서 버그 보고서 파일입니다.

## <a name="frequently-asked-questions"></a>질문과 대답

### <a name="what-skus-do-i-need-to-use-privileged-access-in-office-365"></a>Office 365에서 권한이 부여 된 액세스를 사용 하 여 어떤 Sku를 필요 합니까?
액세스 권한이 부여 된 현재 Office 365의 관리는 e 5 및 고급 준수 Sku와 고객을 위해 사용할 수만 있습니다.

### <a name="when-will-privileged-access-be-available-for-office-365-workloads-beyond-exchange"></a>액세스 권한을된 사용할 수 있게 될 Exchange 이외 Office 365 작업 부하에 대 한?
다른 Office 365 작업에서이 기능을 곧 제공 예정입니다. 시간 표시 막대를 공유할 준비가 되었습니다, Office 365 로드맵을 통해 사용할 수 있습니다.

### <a name="how-is-this-different-from-azure-active-directorys-privileged-identity-management"></a>어떻게 Azure Active Directory 권한 있는 Id 관리와에서 다른 인가요?
권한 다른 범위에서 적시에 액세스할 수 있는 Office 365에 대 한 액세스를 제공 하 여 서로 제어 하는 [Azure AD 권한 있는 Id 관리](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure) 보수 관리에 액세스 합니다. 함께 데이터를 보호 하는 것에 대 한 강력한 컨트롤 집합을 제공 합니다.

액세스 권한이 부여 된 Office 365의 관리를 정의 하 고 여러 작업을 실행 하는 기능 역할 수준에서 적용 하는 Azure AD 권한 있는 Id 관리 하는 동안 작업 수준으로 범위가 지정 수 있습니다.  Azure AD 권한 있는 Id 관리 주로 AD 역할 및 권한 하는 동안 역할 그룹에 대 한 액세스를 관리할 수 있도록 Office 365에서 액세스 관리 작업 수준에서 적용 됩니다.

 - **이미 Azure AD 권한 있는 Id 관리를 사용 하는 동안 Office 365의에서 관리 기능에 대 한 사용 권한 액세스:** Office 365에서 액세스 권한을된 관리 추가 (영문) 다른 세분화 된 보호 계층을 제공 하 고 Office 365 데이터에 대 한 권한이 부여 된 액세스에 대 한 기능을 감사할 수 있습니다.

- **이미 사용 하는 동안 Id 관리를 사용 하도록 설정 Azure AD 권한 있는 사용자는 Office 365에 대 한 액세스 관리 권한이:**  Azure AD 권한 있는 Id 관리 권한 추가 Office 365에서 액세스 관리는 주로 사용자의 역할 또는 id에 의해 정의 된 Office 365의 외부 데이터에 대 한 액세스 권한을된를 확장할 수 있습니다. 

### <a name="do-i-need-to-be-a-global-admin-to-manage-privileged-access-in-office-365"></a>Office 365에 대 한 액세스 권한을된 관리 하는 전역 관리자 되도록 필요 합니까?
미리 보기 하는 동안 Office 365에 대 한 액세스 권한을된 관리할 수 있도록 전역 관리자 권한이 필요 합니다. 승인자의 그룹에 포함 된 사용자 수를 검토 하 고 요청을 승인 하려면 전역 관리자 필요가 없습니다. 

### <a name="how-is-privileged-access-management-in-office-365-related-to-customer-lockbox"></a>Office 365와 관련 된 고객 Lockbox에서에서 액세스 권한을된 관리는 어떻게 합니까?
[고객 Lockbox](https://support.office.com/article/Office-365-Customer-Lockbox-Requests-36f9cdd1-e64c-421b-a7e4-4a54d16440a2) 서비스 공급자, 즉, Microsoft가 데이터에 대 한 액세스에 대 한 조직에 대 한 액세스 제어의 수준 수 있습니다. 액세스 권한이 부여 된 Office 365의 관리는 모든 Office 365의 권한 있는 작업에 대 한 조직 내에서 세분화 된 액세스 제어를 허용 합니다.