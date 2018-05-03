---
title: 검색 하 고 양식 주입 공격을 Office 365 수정 Outlook 규칙 및 사용자 지정
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 04/23/2018
ms.audience: ITPro
ms.topic: article
ms.collection:
- o365_security_incident_response
- Strat_O365_IP
ms.service: o365-solutions
localization_priority: Normal
ms.custom: ''
ms.assetid: ''
description: 인식 하 고 Outlook 규칙 및 Office 365에서 사용자 지정 양식 주입 공격을 수정 하는 방법을 설명 합니다.
ms.openlocfilehash: d0f54a0dc47d7a3602a7b4ce57a04c83d15d9301
ms.sourcegitcommit: a4322cac992ce64b92f0335bf005a7420195d9be
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="detect-and-remediate-outlook-rules-and-custom-forms-injections-attacks-in-office-365"></a>검색 및 Outlook 규칙 및 Office 365에서에서 사용자 지정 양식 주입 공격 수정

**요약** 인식 하 고 Outlook 규칙 및 Office 365에서 사용자 지정 양식 주입 공격을 수정 하는 방법에 알아봅니다.

## <a name="what-is-the-outlook-rules-and-custom-forms-injection-attack"></a>Outlook 규칙 및 사용자 지정 양식 주입 공격 이란?
공격자가 계정을 테 넌 시에 도달 했습니다에 가져옵니다 후 다음과 같은 사용 하려고 시도 하 고 연결 유지 하는 방법 또는 검색 하 고 제거 된 후 다시 가져올 수를 설정 합니다. 지 속성 메커니즘을 설정 하기 라고 합니다. 이 작업 수행할 수 있습니다는 두가지 방법으로 Outlook 규칙을 악용 하 여 또는 Outlook에 사용자 정의 폼을 삽입 하 여입니다. 두 경우 모두 규칙 또는 양식 동기화 되는 데스크톱 클라이언트까지 아래로 클라우드 서비스에서 전체 형식 및 클라이언트 소프트웨어를 다시 설치 주입 메커니즘을 제거 하지 않도록 합니다. 규칙 및 클라우드에서 양식을 다시 다운로드 됩니다 클라우드의 사서함에 다시 연결 되는 Outlook 클라이언트 소프트웨어 때문입니다. 일단 규칙 및 폼의 전체 되 면 공격자가 사용 하 여 로컬 컴퓨터에서 맬웨어를 설치 하는 일반적으로 원격 또는 사용자 지정 코드를 실행 합니다. 맬웨어가 다음 자격 증명을 훔쳐 다시 또는 기타의 불법적인 동작을 수행 합니다. 좋은 소식 여기 최신 버전에 패치를 적용 하 여 클라이언트를 유지 하는 경우 있다는 것 하지 위협에 취약 대로 현재 Outlook 클라이언트 기본값 두 메커니즘을 차단 합니다. 

공격은 일반적으로 이러한 패턴을 따릅니다.

규칙 악용
1. 공격자는 사용자 이름 및 암호를 사용자에 게 하나 훔쳐 합니다.
2. 공격자는 다음 해당 사용자가 Exchange 사서함에 로그인합니다. 사서함 수 Exchange online 또는 Exchange 온-프레미스 합니다.
3. 공격자는 다음 사서함 규칙의 조건과 일치 하는 전자 메일을 받을 때 트리거되는 사서함에서 착신 전환 규칙을 만듭니다. 규칙의 조건 및 트리거 전자 메일의 내용을 다른 사용자에 대 한 맞춤 구성 됩니다.
4. 공격자는 사용자에 게 자신의 사서함을 정상적으로 사용 하는 트리거 전자 메일을 보냅니다.
5. 전자 메일을 받을 때 규칙이 트리거됩니다. 규칙의 매크로 함수는 일반적으로 원격 (WebDAV) 서버에서 응용 프로그램을 실행 합니다.
6. 응용 프로그램 일반적으로 [Powershell 제국](https://www.powershellempire.com/)같은 맬웨어, 로컬 컴퓨터에 설치 하는 사용자의
7. 맬웨어가는 공격자가 사용자의 사용자 이름 및 암호 또는 로컬 컴퓨터에서 다른 자격 증명을 훔쳐 다시 및 기타 악성 작업을 수행할 수 있습니다.

양식 악용
1. 공격자는 사용자 이름 및 암호를 사용자에 게 하나 훔쳐 합니다.
2. 공격자는 다음 해당 사용자가 Exchange 사서함에 로그인 합니다. 사서함 수 Exchange online 또는 Exchange 온-프레미스 합니다.
3. 그런 다음 공격자는 사용자 지정 메일 양식 서식 파일을 만드는 하 고 사용자의 사서함에 삽입 합니다.  사용자 정의 폼에는 사서함 사용자 정의 폼을 로드 하는 사서함을 필요로 하는 전자 메일을 받을 때 트리거됩니다. 사용자 지정 양식 및 전자 메일의 서식을 다른 사용자에 대 한 맞춤 구성 됩니다.
4. 공격자가 사서함을 정상적으로 사용 하는 사용자에 게 트리거 전자 메일을 보냅니다.
5. 전자 메일을 받을 때에 폼이 로드 됩니다. 폼에서 원격 (WebDAV) 서버에서 응용 프로그램을 시작합니다.
6. 응용 프로그램 일반적으로 [Powershell 제국](https://www.powershellempire.com/)같은 맬웨어, 로컬 컴퓨터에 설치 하는 사용자의
7. 맬웨어가는 공격자가 사용자의 사용자 이름 및 암호 또는 로컬 컴퓨터에서 다른 자격 증명을 훔쳐 다시 및 기타 악성 작업을 수행할 수 있습니다.


## <a name="what-a-rules-and-custom-forms-injection-attack-might-look-like-office-365"></a>어떤 규칙 및 사용자 지정 양식 주입 공격 아래 Office 365와 같습니다.

이러한 지 속성 메커니즘 사용자가 발견 될 가능성이 하지 않으며 일부 경우에 표시 하지 못할 자신에 게 있습니다.  이 문서에서는 아래에 나열 된 모든 7 기호 (표시기의 손상)를 확인 하는 방법을 알려줍니다. 둘 중 하나를 찾을 경우 업데이트 관리 단계를 수행 해야 합니다.

- 규칙 손상의 표시기
    - 규칙 동작 응용 프로그램을 시작 하는 합니다.
    - 규칙은 EXE, ZIP, 또는 URL을 참조합니다.
    - 로컬 컴퓨터에서 Outlook PID에서 발생 하는 새 프로세스 시작을 찾습니다.
- 사용자 정의 폼의 지표 손상 
    - 사용자 정의 폼이 매개 변수가 자신의 메시지 클래스로 저장 합니다.
    - 메시지 클래스는 실행 코드를 포함합니다.
    - 일반적으로 개인 양식 라이브러리 또는 받은 편지함 폴더에 저장 합니다.
    - 양식 IPM을 라고 합니다. 메모 합니다. [사용자 지정 이름]입니다.

## <a name="steps-for-finding-signs-of-this-attack-and-confirming-it"></a>이 공격의 징후를 찾아 것을 확인 하기 위한 단계
공격을 확인 하려면 다음 두 방법 중 하나를 사용할 수 있습니다.
- 수동으로 규칙 및 Outlook 클라이언트를 사용 하 여 각 사서함에 대 한 양식을 검사 합니다.  이 메서드는 완벽 하 게 하지만 확인할 수 있습니다 사서함 사용자 시간이 매우 많이 소요 될 수 있는 시간에 많은 사용자가 확인할 수 있는 경우.  검사를 실행 하는 컴퓨터의 위반에서 될 수도 있습니다.
- 규칙 및 모든 사용자에 대 한 사용자 지정 양식 테 넌 트에 전달 하는 모든 메일을 자동으로 덤프를 [Get AllTenantRulesAndForms.ps1](https://github.com/OfficeDev/O365-InvestigationTooling/blob/master/Get-AllTenantRulesAndForms.ps1) PowerShell 스크립트를 사용 합니다. 최소한의 오버 헤드를 빠르고 가장 안전한 방법입니다.


### <a name="confirm-the-rules-attack-using-the-outlook-client"></a>규칙 공격 사용 Outlook 클라이언트 확인
1. 사용자와 사용자가 Outlook 클라이언트를 엽니다.  자신의 사서함에 대해 규칙 검사에 도움이 필요할 수 있습니다.
2. 규칙 인터페이스의 Outlook 2007, 2010 또는 2013 버전에서 여는 방법에 대 한 절차에 대 한 [전자 메일 규칙을 사용 하 여 메시지 관리](https://support.office.com/en-us/article/manage-email-messages-by-using-rules-c24f5dea-9465-4df4-ad17-a50704d66c59#ID0EAABAAA=2010) 문서를 참조 하십시오.
3. 사용자를 만들지 않은 규칙 또는 예기치 않은 규칙 또는 의심 스러운 이름이 포함 된 규칙에 대 한 정보를 제공 합니다.
4. 규칙 동작에 대 한 규칙 설명에서 해당 시작 및 응용 프로그램을 참조 하거나는 합니다. EXE, 합니다. ZIP 파일 또는 URL을 시작 합니다.
5. Outlook 프로세스 ID를 사용 하 여 시작 하는 모든 새 프로세스에 대 한 모양  [프로세스 ID를 찾을](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/finding-the-process-id)참조 하십시오.

### <a name="steps-to-confirm-the-forms-attack-using-the-outlook-client"></a>Outlook 클라이언트를 사용 하 여 양식 공격을 확인 하는 단계
1. 사용자와 사용자 Outlook 클라이언트를 엽니다.
2. 사용자 버전의 Outlook에서 [개발 도구 탭 표시](https://support.office.com/en-us/article/show-the-developer-tab-e1192344-5e56-4d45-931b-e5fd9bea2d45) 하는 단계를 따릅니다.
3. Outlook에서 이제 표시 개발 도구 탭을 열고 **양식 디자인**을 클릭 합니다.
4. **찾는 위치** 목록에서 **받은 편지함** 을 선택 합니다. 모든 사용자 정의 폼을 찾습니다.  사용자 지정 양식은 전혀 모든 사용자 정의 폼을 설치한 경우 인지 대 한 상세한 정보를가지고 있는 가치의 충분히 드문 있습니다.
5. 특히 숨김으로 표시 된 모든 사용자 지정 양식을 조사 합니다.
6. 모든 사용자 지정 양식을 열고 **양식** 그룹에서 폼을 로드할 때 실행 되는 기능을 볼 수 있는 **코드 보기를** 클릭 합니다.

### <a name="steps-to-confirm-the-rules-and-forms-attack-using-powershell"></a>PowerShell을 사용 하 여 규칙 및 양식 공격을 확인 하는 단계
규칙을 확인 하는 가장 간단한 방법은 또는 사용자 지정 양식 공격 [Get AllTenantRulesAndForms.ps1](https://github.com/OfficeDev/O365-InvestigationTooling/blob/master/Get-AllTenantRulesAndForms.ps1) PowerShell 스크립트를 실행 하는 것입니다.  이 스크립트 모든 규칙으로 덤프 및 양식을 두.csv 파일에 테 넌 트의 모든 사서함에 연결 합니다.

#### <a name="pre-requisites"></a>필수 구성 요소
규칙 및 양식 읽을 수 테 넌 시의 모든 사서함에 연결 하는 스크립트 때문에 스크립트를 실행 하려면 전역 관리자 권한을 가지도록 해야 합니다.

1. 로컬 관리자 권한을 가진에서 스크립트를 실행할 컴퓨터에 로그인 합니다.
2. 다운로드 하거나 실행 하는 해당 폴더에 GitHub에서 Get AllTenantRulesAndForms.ps1 스크립트를 복사 합니다.  스크립트는이 폴더, MailboxFormsExport-yyyy-m m-dd.csv, 및 MailboxRulesExport-yyyy-m m-dd.csv 두 날짜 스탬프가 지정 된 파일이 만들어집니다.
3. 관리자 권한으로 PowerShell 인스턴스를 열고 스크립트를 저장 한 폴더를 엽니다.
4. 다음과 같이이 PowerShell 명령줄을 실행 `.\Get-AllTenantRulesAndForms.ps1`.\Get-AllTenantRulesAndForms.ps1

#### <a name="interpreting-the-output"></a>출력을 해석

MailboxRulesExport-*yyyy-월-일*.csv-응용 프로그램 또는 실행 파일을 포함 하는 작업 조건에 대 한 규칙 (행 당 하나)를 검사 합니다.
- ActionType (A 열) – 값 "ID_ACTION_CUSTOM"를 참조 하는 경우 규칙은 가능성이 악의적인 합니다.
- IsPotentiallyMalicious (D 열)-이 값은 "TRUE", 규칙은 가능성이 악의적인 합니다.
- ActionCommand (G 열)-응용 프로그램 또는 파일을.exe,.zip 확장명 또는 URL 있을 하지 않는는 참조 하는 항목을 나열 하는이 규칙은 가능성이 악의적인 합니다.

일반적으로 사용자 지정 양식을 사용을 누르는 MailboxFormsExport-*yyyy-월-일*.csv-은 거의입니다.  이 통합 문서에을 찾을 수 있으면 해당 사용자의 사서함을 열고 폼 자체를 검사 합니다.  조직 않은 위치에 배치 하 있습니다 의도적으로, 경우 악의적인 합니다.



## <a name="how-to-stop-and-remediate-the-outlook-rules-and-forms-attack"></a>중지 하 고 Outlook 규칙 및 양식 공격을 수정 하는 방법
이러한 공격 중 하나에의 한 증거를 찾은 경우 수정은 간단 하 고 방금 사서함에서 규칙 또는 폼을 삭제 합니다. 이렇게 하려면 Outlook 클라이언트 또는 원격 PowerShell을 사용 하 여 규칙을 제거 합니다.

### <a name="using-outlook"></a>Outlook을 사용 하 여
1. 사용자가 Outlook과 함께 사용 하는 모든 장치를 식별 합니다.  이러한 모든 할 잠재적인 맬웨어 제거 될 수 있습니다.  로그온 하 고 모든 장치는 제거 될 때까지 전자 메일을 사용 하 여 사용자를 허용 하지 않습니다.
2. 각 장치에 대 한 [규칙을 삭제](https://support.office.com/en-us/article/Delete-a-rule-2F0E7139-F696-4422-8498-44846DB9067F) 의 단계를 수행 합니다.
3. 다른 맬웨어의 현재 상태에 대 한 잘 모르는 경우에 서식을 수 있으며 장치에서 모든 소프트웨어를 다시 설치 수 있습니다.  모바일 장치에 대 한 장치를 공장 이미지를 다시 설정 하는 제조업체 단계를 따라 수 있습니다.
4. Outlook의 최신 버전을 설치 합니다.  현재 버전의 Outlook은 기본적으로 두 유형의이 공격을 차단 하는 기억 합니다.
5. 사서함의 모든 오프 라인 복사본을 제거한 후 사용자의 암호 (고품질 하나 사용)를 다시 설정 하 고 MFA 이미 활성화 되지 않은 경우 [Office 365 사용자에 대 한 설치 다단계 인증](https://support.office.com/en-us/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6) 의 단계를 수행 합니다. 이렇게 하면 사용자의 자격 증명 (예: 피싱 또는 암호를 다시 사용) 다른 수단을 통해 노출 되지 않습니다.

### <a name="using-powershell"></a>PowerShell을 사용 하 여
두 원격 PowerShell cmdlet을 제거 하거나 위험한 규칙을 사용 하지 않도록 설정 하는데 사용할 수 있습니다. 단계를 수행 합니다.
 
Exchange 서버에 있는 사서함에 대 한 단계

1. 원격 PowerShell을 사용 하 여 Exchange 서버에 연결 합니다. [원격 PowerShell을 사용 하 여 Exchange 서버에 연결](https://docs.microsoft.com/en-us/powershell/exchange/exchange-server/connect-to-exchange-servers-using-remote-powershell?view=exchange-ps)의 단계를 수행 합니다.
2. 사서함 사용- [제거 받은 편지함 규칙 cmdlet ](https://docs.microsoft.com/en-us/powershell/module/exchange/mailboxes/Remove-InboxRule?view=exchange-ps)에서 단일 규칙, 여러 규칙 또는 모든 규칙을 완전히 제거 하려는 경우 사서함에서 완전히 제거 하나, 여러 하려면이 옵션을 또는 모든 규칙을 사용 합니다.
3. 규칙을 유지 하려면 하 고 자세한 조사를 위해 해당 내용을 [Disable-inboxrule cmdlet](https://technet.microsoft.com/en-us/library/dd298120(v=exchg.160).aspx)을 사용 합니다. 

Exchange Online의 사서함에 대 한 단계
1. [PowerShell을 사용 하는 Exchange Online에 연결](https://docs.microsoft.com/en-us/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell?view=exchange-ps)의 단계를 수행 합니다.
2.  단일 규칙을 완전히 제거 하려는 경우 여러 규칙 또는 사서함에서 모든 규칙 [제거 받은 편지함 규칙 cmdlet](https://docs.microsoft.com/en-us/powershell/module/exchange/mailboxes/Remove-InboxRule?view=exchange-ps)을 사용 합니다.
3.  규칙을 유지 하려면 하 고 자세한 조사를 위해 해당 내용을 [Disable-inboxrule cmdlet](https://technet.microsoft.com/en-us/library/dd298120(v=exchg.160).aspx)을 사용 합니다. 

## <a name="how-to-minimize-future-attacks"></a>앞으로 공격을 최소화 하는 방법

### <a name="first-protect-your-accounts"></a>1: 사용자 계정을 보호합니다

규칙 및 양식 악용 도난 또는 사용자의 계정 중 하나를 위반 후에 공격자가 사용 됩니다. 따라서 사용 하면 조직에 대해 이러한 악용을 방지 하 여 첫 단계 적극적으로 사용자 계정을 보호 하는 것입니다.  피싱 또는 [암호 spraying](http://www.dabcc.com/microsoft-defending-against-password-spray-attacks/) 를 통해 계정 도달는 가장 일반적인 방법 중 일부는 공격입니다.



사용자 계정과 관리자 계정, 특히 보호 하기 위해 [Office 365 사용자에 게 다단계 인증을 설정](https://support.office.com/en-us/article/set-up-multi-factor-authentication-for-office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6)하는 가장 좋은 방법은 합니다.  또한 해야 합니다.
<ol>
    <li>사용자 계정에 <a href="https://docs.microsoft.com/en-us/azure/active-directory/active-directory-view-access-usage-reports">액세스 하 고 사용 하</a>는 하는 방법을 모니터링 합니다. 초기 침해를 방해 하지 않을 수 있지만 빨리 여 검색 하 여 기간 및 위반의 영향을 단축 됩니다. 이 사용할 수: 계정 및 비정상적인 활동에 대 한 경고를 모니터링 하도록 <a href="https://support.office.com/en-us/article/overview-of-office-365-cloud-app-security-81f0ee9a-9645-45ab-ba56-de9cbccab475">Office 365 클라우드 응용 프로그램 보안 정책</a> 입니다.<ol type="a">
            <li><b>여러 실패 한 로그인 시도</b> 사용자는 시도한 침해를 일으킬 수 있는 습득된 초기 계획 관련 하 여 단일 세션에서 여러 실패 한 로그인 활동을 수행 하는 경우이 정책 프로필 사용자 환경 및 트리거 알림입니다.</li>
            <li><b>Impossible 출장</b> - 이 정책을 사용자 환경 프로필 및 두 위치 사이의 예상된 출장 시간 보다 짧은 기간 내에서 서로 다른 위치에 동일한 사용자 활동 감지 되 면 경고를 트리거합니다. 이 다른 사용자가 동일한 자격 증명 사용 하 여 나타낼 수 있습니다. 이 비정상적인 동작 하 여 검색 초기 학습 기간을 새 사용자의 작업 패턴을 학습 해당 하는 동안 7 일이 필요 합니다.</li>
            <li><b>비정상적 가장할 활동 (사용자별)</b> - 이 정책을 사용자 환경 프로필 및 사용자가 수행할 때 여러 가장 된 활동 습득 하 고, 초기 계획 관련 하 여 단일 세션에서는 시도한 침해를 일으킬 수 있는 경고를 트리거합니다.</li>
        </ol>
    </li>
    <li>계정 보안 구성 및 동작을 관리 하는 <a href="https://securescore.office.com/">Office 365 보안 점수</a> 와 같은 도구를 활용 합니다. 
    </li>
</ol> 

### <a name="second-keep-your-outlook-clients-current"></a>두번째: Outlook 클라이언트를 최신 상태로 유지
완벽 하 게 업데이트 및 패치 버전의 Outlook 2013 및 2016 기본적으로 "응용 프로그램 시작" 규칙/양식 동작을 해제합니다.  이렇게 하면는 공격자는 계정이 breaches, 하는 경우에 규칙 및 양식 동작 차단 됩니다.  [Office 설치 업데이트](https://support.office.com/en-us/article/Install-Office-updates-2ab296f3-7f03-43a2-8e50-46de917611c5)의 단계를 수행 하 여 최신 업데이트와 보안 패치를 설치할 수 있습니다.

Outlook 2013 및 2016 클라이언트에 대 한 패치 버전은 다음과 같습니다.
- Outlook 2013: 15.0.4937.1000 이상
- Outlook 2016: 16.0.4534.1001 이상

개별 보안 패치에 대 한 자세한 내용은 다음을 참조 합니다.

- [Outlook 2013 보안 패치](https://support.microsoft.com/en-us/help/3191938) 
- [Outlook 2016 보안 패치](https://support.microsoft.com/en-us/help/3191883)

### <a name="third-monitor-your-outlook-clients"></a>3: Outlook 클라이언트를 모니터링
패치 및 업데이트가 설치 되어 있어도 사항에 유의 공격자가 다시 "응용 프로그램 시작" 동작을 사용 하도록 설정 하려면 로컬 컴퓨터 구성을 변경 하는 것과 같습니다. 모니터링 하 고 클라이언트에 로컬 컴퓨터 정책을 적용 하려면 [고급 그룹 정책 관리](https://docs.microsoft.com/en-us/microsoft-desktop-optimization-pack/agpm/) 를 사용할 수 있습니다.  
"응용 프로그램 시작"을 다시 사용 하는 레지스트리에 재정의 통해 [64 비트 버전의 Windows 사용 하 여 시스템 레지스트리를 확인 하는 방법](https://support.microsoft.com/en-us/help/305097/how-to-view-the-system-registry-by-using-64-bit-versions-of-windows)에 정보를 사용 하 여 참조를 할 수 있습니다.  이러한 하위 키를 확인 합니다. 

- Outlook 2016: HKEY_CURRENT_USER\Software\Microsoft\Office\16.0\Outlook\Security\
- Outlook 2013: HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Outlook\Security\

EnableUnsafeClientMailRules 키를 찾습니다. 있다는 것을 1로 설정 하는 경우 Outlook 보안 패치를 재정의 하 고 컴퓨터를 폼/규칙 공격에 취약 합니다. 값이 0 이면 "응용 프로그램 시작" 작업은 사용할 수 없습니다.  패치 및 업데이트 된 버전의 Outlook 설치 된 경우이 레지스트리 키가이 매개 변수가 아니면 시스템은 이러한 공격에 취약 하지 않습니다.

온-프레미스 Exchange 설치 하 여 고객 패치를 사용할 수 없는 이전 버전의 Outlook 차단 고려해 야 합니다. 이 프로세스에 대 한 자세한 내용은 문서를 [차단 하는 구성 Outlook 클라이언트](https://technet.microsoft.com/en-us/library/dd335207(v=exchg.150).aspx)에서 확인할 수 있습니다.

## <a name="secure-office-365-like-a-cybersecurity-pro"></a>Office 365 전문가 cybersecurity와 같은 보안
Office 365 구독 강력한 데이터 및 사용자를 보호 하기 위해 사용할 수 있는 보안 기능 집합을 함께 제공 됩니다.  사용 하는 [Office 365 보안 로드맵: 처음 30 일, 90 일 동안 및 이외 우선순위 가지 주요](https://support.office.com/en-us/article/Office-365-security-roadmap-Top-priorities-for-the-first-30-days-90-days-and-beyond-28c86a1c-e4dd-4aad-a2a6-c768a21cb352) Microsoft Office 365 테 넌 트를 보호 하기 위한 최상의 방법을 구현 하 합니다.
- 처음 30 일에서 수행 하는 작업입니다.  낮은 영향 및 영향을 주지는 즉시 이러한 사용자에 게 있습니다.
- 90 일에서을 수행 하는 작업입니다. 이러한 계획 및 구현 하지만 보안 환경을 크게 개선 하는 약간 더 많은 시간이 걸릴.
- 90 일 이상. 이러한 향상 된 첫번째 90 일이 작업의에서 작성합니다.

## <a name="see-also"></a>참고 항목:
- 방법에 대 한 자세한 검토를 제공 하는 규칙 벡터에 대 한 보안 게시물 SilentBreak 하 여 [악의적인 Outlook 규칙](https://silentbreaksecurity.com/malicious-outlook-rules/) Outlook 규칙입니다. 
- [MAPI over HTTP 및 Mailrule Pwnage](https://sensepost.com/blog/2016/mapi-over-http-and-mailrule-pwnage/) Mailrule Pwnage 하는 방법에 대 한 Sensepost 블로그의에서는 Outlook 규칙을 통해 사서함을 악용할 수 있는 눈금자를 호출 하는 도구에 설명 합니다.
- [Outlook 양식 및 셸](https://sensepost.com/blog/2017/outlook-forms-and-shells/) 양식 위협 벡터에 대 한 Sensepost 블로그의 합니다. 
- [눈금자 코드 베이스](https://github.com/sensepost/ruler)
- [손상의 눈금자 표시기](https://github.com/sensepost/notruler/blob/master/iocs.md)