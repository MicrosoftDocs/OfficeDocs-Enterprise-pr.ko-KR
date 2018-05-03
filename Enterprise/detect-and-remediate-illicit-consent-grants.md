---
title: 검색 및 Office 365의에서 불법 사용자의 동의 부여 수정
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 4/23/2018
ms.audience: ITPro
ms.topic: article
ms.collection:
- o365_security_incident_response
- Strat_O365_IP
ms.service: o365-solutions
localization_priority: Normal
ms.custom: ''
ms.assetid: ''
description: 인식 하 고 Office 365의 불법 사용자의 동의 부여 공격을 수정 하는 방법에 알아봅니다.
ms.openlocfilehash: f6576fccd7cac49dbbf2e9ea359e08257ddc42d0
ms.sourcegitcommit: a4322cac992ce64b92f0335bf005a7420195d9be
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="detect-and-remediate-illicit-consent-grants-in-office-365"></a>검색 및 Office 365의에서 불법 사용자의 동의 부여 수정

**요약**  인식 하 고 Office 365의 불법 사용자의 동의 부여 공격을 수정 하는 방법에 알아봅니다.

## <a name="what-is-the-illicit-consent-grant-attack-in-office-365"></a>Office 365의 불법 사용자의 동의 부여 공격 이란?
불법 사용자의 동의 권한을 부여 하 공격에서 공격자가 문서 또는 전자 메일, 연락처 정보 등의 데이터에 대 한 액세스를 요청 하는 Azure에 등록 된 응용 프로그램을 만듭니다. 공격자가 다음 기술 (영문) 최종 사용자에 피싱 공격을 통해 또는 신뢰할 수 있는 웹사이트에 불법 코드를 삽입 하 여 자신의 데이터에 액세스 하려면 해당 응용 프로그램의 동의 부여 합니다. 불법 응용 프로그램이 사용자의 동의 부여 된, 후에 조직 구성 단위 계정에 대 한 필요 없이 데이터에 대 한 계정 수준 액세스를 있습니다. 타사 응용 프로그램은 이러한 및 외부 조직에는 이후 침해 계정의 암호를 다시 설정 또는 다단계 인증 (MFA) 계정에 필요한 기본 복구 단계를 효과적으로 이러한 종류의 공격을 방어 없습니다. 이러한 공격 정보를 호출 하 고 있는 엔터티는 자동화 및 human 하지으로 가정 하는 상호 작용 모델을 활용 합니다.

## <a name="what-does-an-illicit-consent-grant-attack-look-like-in-office-365"></a>Office 365에는 불법 사용자의 동의 부여 공격 모양 like 기능
Office 365 **감사 로그** 라고도 함 표시기의 손상 (IOC)이 공격의 징후를 찾으려고 검색 해야 합니다. 많은 Azure에 등록 된 응용 프로그램 및 구성 된 대규모 사용자 기반 조직용 매주 조직에서는 사용자의 동의 부여 대화를 검토 하는 것이 좋습니다.
### <a name="steps-for-finding-signs-of-this-attack"></a>이 공격의 징후 찾기 (영문)에 대 한 단계
1. Office 365 테 넌 트에는 **보안 및 규정 준수 센터를** 엽니다.
2. **검색 및 조사** 노드로 이동한 **감사 로그** 검색을 선택 합니다.
3. (모든 활동 및 모든 사용자)를 검색 하 고 만들고 응용 프로그램을 사용자의 동의 대 한 결과 필터링 OAuth2PermissionGrant를 추가 합니다.
4. 확장 된 속성 및 확인 IsAdminContent이 True로 설정 하는 경우 참조를 검사 합니다.


이 값이 true 이면이 전역 관리자 액세스 권한이 있는 사용자 수 데이터에 대 한 광범위 한 액세스 부여 있음을 나타냅니다. 이것이 예상 되 [는 공격을 확인](detect-and-remediate-illicit-consent-grants.md#confirmattack)하려면 단계를 수행 합니다.

<a name="confirmattack"> </a>
## <a name="how-to-confirm-an-attack"></a>공격을 확인 하는 방법
수행 하기 위해 필요한 하나 이거나 위에 나열 된는 IOCs의 인스턴스를 더을 하는 경우 추가 긍정적인 발생 한 공격을 확인 하는 조사 합니다. 공격을 확인 하려면 다음 세가지 방법 중 하나를 사용할 수 있습니다.
- 응용 프로그램 및 Azure Active Directory 포털을 사용 하 여 해당 사용 권한을 조사 합니다. 이 메서드는 완벽 하 게 하지만 확인할 수 있습니다 사용자가 한 명 시간이 매우 많이 소요 될 수 있는 시간에 많은 사용자가 확인할 수 있는 경우.
- 응용 프로그램 및 PowerShell을 사용 하 여 해당 사용 권한을 조사 합니다. 이것이 가장 빠른 하 고 가장 철저 한 메서드는 최소한의 오버 헤드입니다.
- 사용자가 개별적으로 해당 앱 및 사용 권한 확인 및 업데이트 관리에 대 한 관리자에 게 결과 보고 하 게 합니다.

## <a name="inventory-apps-with-access-in-your-organization"></a>조직에서 액세스할 수 있는 인벤토리 앱
Azure Active Directory 포털 또는 PowerShell와 사용자를 위해이 작업을 수행 하거나 사용자를 개별적으로 응용 프로그램 액세스를 열거할 수 있습니다.

### <a name="steps-for-using-the-azure-active-directory-portal"></a>Azure Active Directory 포털을 사용 하기 위한 단계
응용 프로그램을 개별 사용자가 권한을 부여 [Azure Active Directory 포털](https://portal.azure.com/)을 사용 하 여 조회할 수 있습니다. 
1. 관리 권한 사용 하 여 Azure 포털에 로그인 합니다.
2. Azure Active Directory 블레이드를 선택 합니다.
3. **사용자**를 선택 합니다.
4. 검토 하려는 사용자를 선택 합니다.
5. **응용 프로그램**을 선택 합니다.

이 대해 살펴봅니다 사용자와 기능에 할당 된 응용 프로그램의 응용 프로그램 한 권한이 있습니다.

### <a name="steps-for-having-your-users-enumerate-their-application-access"></a>사용자가 보유 한 단계 열거의 응용 프로그램 액세스
로 이동 하 여 사용자가 https://myapps.microsoft.com 하 고 다음과 같은 자신의 응용 프로그램 액세스를 검토 합니다. 액세스 권한이 있는 모든 앱을 표시 하도록 해당 (access의 범위를 포함 하 여)에 대 한 세부 정보를 볼 수 있으며 의심 스러운 또는 불법 앱에 대 한 권한을 해지할 수 해야 합니다.

### <a name="steps-for-doing-this-with-powershell"></a>Powershell이 작업을 수행 하기 위한 단계
불법 타고 부여 공격을 확인 하는 가장 간단한 방법은 [Get AzureADPSPermissions.ps1](https://gist.github.com/psignoret/41793f8c6211d2df5051d77ca3728c09), 덤프 모든 OAuth 사용자의 동의 부여 및 모든 사용자에 대 한 앱 권한을 테 넌 시에 하나의.csv 파일에는 실행 하는 합니다. 

#### <a name="pre-requisites"></a>필수 구성 요소
- Azure AD PowerShell 라이브러리를 설치 합니다.
- 스크립트에 대해 실행 되는 테 넌 트에 대 한 전역 관리자 권한
- 하는 컴퓨터에서 로컬 관리자 스크립트를 실행 합니다.

> [!IMPORTANT]
> 관리 계정에 다단계 인증을 요구 하는 것이 좋습니다.  이 스크립트는 MFA 인증을 지원합니다.

1. 로컬 관리자 권한을 가진에서 스크립트를 실행할 컴퓨터에 로그인 합니다.
2. 다운로드 하거나 신청을 scruipt를 실행할 폴더에 GitHub에서 [Get AzureADPSPermissions.ps1](https://gist.github.com/psignoret/41793f8c6211d2df5051d77ca3728c09) 스크립트를 복사 합니다.  이 출력 "permissions.csv" 파일 쓸 수 같은 폴더 지정 됩니다.
3. 관리자 권한으로 PowerShell 인스턴스를 열고 스크립트를 저장 하는 폴더를 엽니다.
4. [Connect AzureAD](https://docs.microsoft.com/en-us/powershell/module/azuread/connect-azuread?view=azureadps-2.0) cmdlet을 사용 하 여 디렉터리에 연결 합니다.
5. 다음과 같이이 PowerShell 명령줄을 실행 합니다.`.Get-AzureASPSPermissions.ps1 | Export-csv -path "Permissions.csv" -NoTypeInformation`

스크립트는 Permissions.csv 이라는 하나의 파일을 생성 합니다. 불법 응용 프로그램 사용 권한 부여를 확인 하려면 다음이 단계를 수행 합니다. 
1. ConsentType 열 (열 G)에서 "AllPrinciples" 값을 검색 합니다. AllPrincipals 권한 클라이언트 응용 프로그램을 테 넌 시의 모든 사용자의 콘텐츠에 액세스할 수 있습니다. 기본 Office 365 응용 프로그램에는 제대로 작동 하려면이 권한이 필요 합니다. 이 권한이 있는 모든 비 Microsoft 응용 프로그램을 신중 하 게 검토 해야 합니다.
2.  응용 프로그램을 위임 된 각 권한 콘텐츠에 하는 사용 권한 (F 열) 열 검토 합니다. "읽기" 및 "쓰기" 권한 찾습니다 또는 "*. "모든 권한, 및 이러한 신중 하 게 하지 못할 수 있으므로 적절 한 검토 합니다.
3.  부여 동의 수 있는 특정 사용자를 검토 합니다. 중요 한 비즈니스 또는 영향력이 사용자에 부여 부적절 한 동의 자세히 조사 해야 합니다.
4.  ClientDisplayName 열 (C 열)에서 의심 스러운 것 처럼 보일 앱을 찾습니다. 철자가 잘못 된 이름, 고급 밋밋하게 이름 또는 해커 운 이름을 함께 응용 프로그램을 신중 하 게 검토 해야 합니다.

## <a name="determine-the-scope-of-the-attack"></a>공격 범위 결정
응용 프로그램 액세스 인벤토리를 완료 한 후 검토 하는 Office 365 **감사 로그를** 위반의 전체 범위를 결정 합니다.  검색 영향을 받는 사용자에 게 불법 응용 프로그램 했던 시간 프레임 앱 명의 사용 권한 및 조직, 액세스 합니다. [Office 365 보안 및 규정 준수 센터](https://support.office.com/en-us/article/Search-the-audit-log-in-the-Office-365-Security-Compliance-Center-0d4d0f35-390b-4518-800e-0c7ec95e946c) **감사 로그** 를 검색할 수 있습니다. 

> [!IMPORTANT]
> [사서함 감사](https://support.office.com/en-us/article/Enable-mailbox-auditing-in-Office-365-aaca8987-5b62-458b-9882-c28476a66918) 및 [작업 관리자 및 사용자에 대 한 감사](https://support.office.com/en-us/article/turn-office-365-audit-log-search-on-or-off-e893b19a-660c-41f2-9074-d3631c95a014) 해야 활성화 된 전에 공격이이 정보를 얻을 수 있습니다.

## <a name="how-to-stop-and-remediate-an-illicit-consent-grant--attack"></a>중지 하 고 불법 사용자의 동의 부여 공격을 수정 하는 방법
불법 사용 권한으로 응용 프로그램을 식별 한 후 해당 액세스 권한을 제거 하는 여러가지 방법을 해야 합니다.
- 하 여 Azure Active Directory 포털에서 응용 프로그램의 사용 권한을 해지할 수 있습니다.
    - **Azure Active Directory 사용자** 블레이드에 영향을 받는 사용자로 이동 합니다.
    - **응용 프로그램**을 선택 합니다.
    - 불법 응용 프로그램을 선택 합니다.
    - 에서 **제거** 를 클릭 드릴 다운 합니다.
- [제거 AzureADOAuth2PermissionGrant](https://docs.microsoft.com/en-us/powershell/module/azuread/Remove-AzureADOAuth2PermissionGrant?view=azureadps-2.0)의 단계를 수행 하 여 powershell OAuth 사용자의 동의 권한 부여를 취소할 수 있습니다.
- [제거 AzureADServiceAppRoleAssignment](https://docs.microsoft.com/en-us/powershell/module/azuread/Remove-AzureADServiceAppRoleAssignment?view=azureadps-2.0)의 단계를 수행 하 여 powershell 서비스 응용 프로그램 역할 할당을 취소할 수 있습니다.
- 그러면 해당 계정에는 데이터에 대 한 응용 프로그램 액세스 비활성화 하는 영향을 받는 계정 모두에 대 한 로그인 비활성화할 수 있습니다. 이 문서가 최종 사용자의 생산성을 위한 이상적인 물론, 영향을 신속 하 게 제한 하려면 작동 하는 경우 수 없지만 사용 가능한 단기 수정 합니다.
- 테 넌 트에 대 한 통합 된 응용 프로그램을 해제할 수 있습니다. 최종 사용자가 테 넌 트 수준으로 사용자의 동의 부여 하는 기능을 사용 하지 않도록 설정 하는 단계입니다. 이렇게 하면 사용자가 실수로 악의적인 응용 프로그램에 대 한 액세스 권한 부여에서 않습니다. 심각 하 게 영향을 주게 제 3 자 응용 프로그램과 함께 생산성을 높일 수 있는 기능 사용자의 것 처럼이 권장 강력 하 게 되지 않습니다.  [설정 또는 해제 기능을 통합 된 앱](https://support.office.com/en-us/article/Turning-Integrated-Apps-on-or-off-7e453a40-66df-44ab-92a1-96786cb7fb34)의 단계를 수행 하 여이 수행할 수 있습니다.

## <a name="secure-office-365-like-a-cybersecurity-pro"></a>Office 365 전문가 cybersecurity와 같은 보안
Office 365 구독 강력한 데이터 및 사용자를 보호 하기 위해 사용할 수 있는 보안 기능 집합을 함께 제공 됩니다.  사용 하는 [Office 365 보안 로드맵: 처음 30 일, 90 일 동안 및 이외 우선순위 가지 주요](https://support.office.com/en-us/article/office-365-security-roadmap-top-priorities-for-the-first-30-days-90-days-and-beyond-28c86a1c-e4dd-4aad-a2a6-c768a21cb352) Microsoft Office 365 테 넌 트를 보호 하기 위한 최상의 방법을 구현 하 합니다.
- 처음 30 일에서 수행 하는 작업입니다.  낮은 영향 및 영향을 주지는 즉시 이러한 사용자에 게 있습니다.
- 90 일에서을 수행 하는 작업입니다. 이러한 계획 및 구현 하지만 보안 환경을 크게 개선 하는 약간 더 많은 시간이 걸릴.
- 90 일 이상. 이러한 향상 된 첫번째 90 일이 작업의에서 작성합니다.

## <a name="see-also"></a>참고 항목:
- [내 응용 프로그램 목록에서 예기치 않은 응용 프로그램](https://docs.microsoft.com/en-us/azure/active-directory/application-access-unexpected-application) 하면서 데이터에 액세스할 수 있는 예기치 않은 응용 프로그램은 실현 한 후 수행 해야할 수도 다양 한 작업을 통해 관리자가 작업을 수행 합니다.
- [Azure Active Directory와 응용 프로그램 통합 (영문)]  (https://docs.microsoft.com/en-us/azure/active-directory/active-directory-apps-permissions-consent) 은 한 높은 수준의 개요 사용자의 동 및 사용 권한입니다.  [사용자의 동의 프레임 워크의 개요](https://docs.microsoft.com/en-us/azure/active-directory/develop/active-directory-integrating-applications#overview-of-the-consent-framework) 섹션에 특히 주의 해야 합니다.
- [내 응용 프로그램을 개발 하는 문제에](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-application-dev-development-content-map) 대 한 링크를 다양 한 동의 관련된 문서를 제공 합니다.
- [응용 프로그램 및 서비스의 보안 주체 개체는 Azure Active Directory (Azure AD)에서](https://docs.microsoft.com/en-us/azure/active-directory/develop/active-directory-application-objects) 핵심 응용 프로그램 모델에는 응용 프로그램 및 서비스 계정 개체에 대 한 개요를 제공 합니다.
- [앱에 대 한 관리 액세스](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-managing-access-to-apps) 은 개요 관리자에 게 앱에 대 한 사용자 액세스를 관리 하는 기능입니다.