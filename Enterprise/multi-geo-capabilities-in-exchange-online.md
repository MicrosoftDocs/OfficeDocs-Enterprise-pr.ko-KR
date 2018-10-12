---
title: Exchange Online의 다중-지리적으로 분산 기능
ms.author: chrisda
author: chrisda
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Normal
ms.assetid: ''
description: Exchange Online의 다중-지리적으로 분산 기능을 사용 하는 여러 지리적 영역을 Office 365 현재 상태를 확장 합니다.
ms.openlocfilehash: aa83b5040cdc98a1c651388fa82d746b852c2313
ms.sourcegitcommit: 5cb4dbdd10ab399af414503cb518a9f530919ef5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/11/2018
ms.locfileid: "25498228"
---
# <a name="multi-geo-capabilities-in-exchange-online"></a>Exchange Online의 다중-지리적으로 분산 기능

Office 365의 다중-지리적으로 분산 기능 여러 지리적 위치 (Geos)에 걸쳐를 단일 테 넌 트를 사용 하도록 설정 합니다. 다중-지리적으로 분산을 사용 하는 경우 고객 사용자 단위로에서 Exchange Online 사서함 콘텐츠 (보관 된 데이터)의 위치를 선택할 수 있습니다.

초기 테 넌 트 위치 (라고 함 "기본" 또는 "중앙" 위치) 청구 주소에 따라 결정 됩니다. 다중-지리적으로 분산을 사용 하는 경우에 하 여 추가 "위성" 위치에서 사서함을 배치할 수 있습니다.

- 위성 직접 새 Exchange Online 사서함을 만듭니다.

- 위성에 기존 Exchange Online 사서함을 이동합니다.

- 온 보 딩 위성에 직접 온-프레미스 Exchange 조직에서 사서함입니다.

다음 Geos 다중-지리적으로 분산 구성에서 사용 하기 위해 사용할 수 있습니다.

- 아시아 태평양

- 오스트레일리아

- 캐나다

- 유럽 연합

- 프랑스

- 인도 (현재 인도에서 대금 청구 주소를 가진 고객에 게에 사용할 수)

- 일본

- 한국

- 영국

- 미국

## <a name="prerequisite-configuration"></a>필수 구성 요소 구성
수를 시작 하기 전에 사용 하 여 다중-지리적으로 분산 기능 Exchange Online Microsoft 다중-지리적으로 분산 지원에 대 한 Exchange Online 테 넌 트를 구성 해야 합니다. 라이선스 및 지리적 다중 테 넌 트에 표시 순서 후이 일회성 구성 프로세스가 트리거됩니다. 이 일회성 구성 프로세스를 완료 하려면 30 일 보다 작은 걸릴 일반적으로 해야 합니다. 다중-지리적으로 분산 주문 하려면 Microsoft 담당자에 게 문의 합니다. 자세한 내용은 참조 https://aka.ms/Multi-Geo합니다.

구성 완료 되 면 [Office 365 메시지 센터](https://support.office.com/article/Message-center-in-Office-365-38FB3333-BFCC-4340-A37B-DEDA509C2093) 에서 알림이 표시 됩니다. 다중-지리적으로 분산 라이선스 테 넌 트에 표시 되 면 자동으로 구성이 트리거됩니다.

## <a name="mailbox-placement-and-moves"></a>사서함 배치 및 이동 합니다.
Microsoft 다중-지리적으로 분산 되는 필수 구성 요소 구성 단계를 완료 한 후 Exchange Online는 제한이 사용자 개체의 **PreferredDataLocation** 특성 Azure AD에 있습니다.

Exchange Online은 Exchange Online 디렉터리 서비스에서 **MailboxRegion** 속성으로 Azure AD에서 **PreferredDataLocation** 속성을 동기화합니다. **MailboxRegion** 의 값은 지리적으로 분산 사용자 사서함과 연결 된 보관 사서함 배치할 수를 결정 합니다. 사용자의 기본 사서함 및 보관 사서함을 다른 Geos에 있는 구성 하는 것이 불가능 합니다. 사용자 개체 당 하나만 지리적으로 분산을 구성할 수 있습니다.

- **PreferredDataLocation** 기존 사서함 사용자에 대해 구성 된 사서함 재배치 큐에 배치 될 하 고 자동으로 지정 된 지리적으로 분산으로 이동 합니다. 

- **PreferredDataLocation** 는 기존 사서함이 없는 사용자에 대해 구성 되 면 지정 된 지리적으로 사서함 프로 비전 됩니다. 

- **PreferredDataLocation** 사용자를 지정 하지 않으면 기본 지리적으로 분산 된 사서함 표시 됩니다.

- **PreferredDataLocation** 코드 올바르지 않은 경우 (예: 이름 대신 NAN의 형식), 사서함을 기본 지리적으로 분산에에서 배치 됩니다.

**참고**: 다중-지리적으로 분산 기능 및 Skype 모두 지역별로 호스팅되는 비즈니스 온라인 모임에 대 한 속성을 사용 **PreferredDataLocation** 사용자 개체에 서비스를 찾습니다. 지역별로 호스팅된 모임에 대 한 사용자 개체에 **PreferredDataLocation** 값을 구성 하는 경우 해당 사용자에 대 한 사서함 자동으로 이동할 지정 된 지리적으로 분산 다중-지리적으로 분산이 Office 365 테 넌 트에 설정 된 후 합니다.

## <a name="feature-limitations-for-multi-geo-in-exchange-online"></a>다중-지리적으로 분산 Exchange online에 대 한 기능 제한
1. 사용자 사서함, 리소스 사서함 (회의실 및 기 자재 사서함) 및 공유 사서함 다중-지리적으로 분산 기능을 지원 합니다. 공용 폴더 사서함 및 Office 365 그룹 고객의 홈 지리적으로 분산에 남아 있습니다.
 
2. 보안 및 규정 준수 기능 (예: 감사 및 eDiscovery) (EAC)의 Exchange 관리 센터에서 사용할 수 있는 다중-지리적으로 분산 조직에서 사용할 수 없습니다. 대신, 보안 및 규정 준수 기능을 구성 하는 [Office 365 보안 및 규정 준수 센터를](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8) 사용 해야 합니다.

3. 새로운 지리적으로 자신의 사서함을 이동 하는 동안 Mac 사용자를 위한 outlook에서 자신의 온라인 보관 함 폴더에 대 한 액세스의 임시 손실을 경험할 수 있습니다. 이 조건은 크로스-지리적으로 분산 사서함 이동 서로 다른 시간에 완료 될 수 있습니다 때문에 사용자의 기본 및 다른 Geos에 보관 사서함이 있는 경우에 발생 합니다.

4. 사용자가 Outlook에서 (이전의 Outlook Web App 또는 OWA) 웹에 Geos 별 *사서함 폴더* 를 공유할 수 없습니다. 예, 유럽 연합의 사용자 미국에 있는 사서함에 공유 폴더를 열려면 웹에 있는 Outlook을 사용할 수 없습니다. 그러나 웹 사용자에 게 Outlook [Outlook Web App에서 별도 브라우저 창에서 다른 사용자의 사서함을 열](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362)에서 설명한 대로 별도 브라우저 창을 사용 하 여 서로 다른 Geos의 *다른 사서함* 을 열 수 있습니다.

    **참고**: 크로스-지리적으로 분산 사서함 폴더 공유는 Windows에서 Outlook에서 지원 합니다.

## <a name="administration"></a>관리 
원격 PowerShell은 보기 및 Office 365 환경에서 지리적으로 분산 관련 속성을 구성 해야 합니다. Office 365를 관리 하는 데 사용 하는 다양 한 PowerShell 모듈에 대 한 자세한 내용은 [Office 365를 관리 하 고 Windows PowerShell을 사용한 Exchange Online](https://support.office.com//article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6)을 참조 하십시오.

- [Microsoft Azure Active Directory PowerShell 모듈](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) v1.1.166.0 또는 사용자 개체에 **PreferredDataLocation** 속성을 표시 하려면 나중에 v1.x 필요 합니다. AAD에 AAD 연결을 통해 동기화 하는 사용자 개체 AAD PowerShell을 통해 직접 수정 하는 **PreferredDataLocation** 값을 가질 수 없습니다. AAD PowerShell을 통해 클라우드 전용 사용자 개체를 수정할 수 있습니다. Azure AD PowerShell 연결할 [Office 365 PowerShell에 연결](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell)을 참조 합니다. 

- Exchange Online PowerShell 연결할 [Connect to Exchange Online PowerShell를](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)참조 하십시오. 

### <a name="connect-directly-to-a-specific-geo-using-exchange-online-powershell"></a>Exchange Online PowerShell을 사용 하는 특정 지리적으로 분산에 직접 연결
일반적으로 Exchange Online PowerShell 기본 지리적으로 분산에 연결 됩니다. 하지만 기본이 아닌 Geos에 직접 연결할 수도 있습니다. 성능 개선 사항으로 인해만 해당 지리적으로 분산에서 사용자를 관리 하는 경우 기본이 아닌 지리적으로 분산에 직접 연결 하는 것이 좋습니다.

특정 지리적 연결할 *ConnectionUri* 매개 변수는은 일반 연결 지침은 다릅니다. 명령 및 값의 나머지 부분 동일 합니다. 단계는.

1. 로컬 컴퓨터에서 Windows PowerShell을 열고 다음 명령을 실행 합니다.
    
    ```
    $UserCredential = Get-Credential
    ```
   **Windows PowerShell 자격 증명 요청** 대화 상자에 작업 또는 학교 계정 및 암호를 입력 한 다음 **확인**을 클릭 합니다.
    
2. 바꾸기 `<emailaddress>` 지리적으로 분산 대상에서 **모든** 사서함 및 다음 명령 실행 하는 전자 메일 주소와 합니다. 사서함과 1 단계에서에서 자격 증명에 대 한 관계에 대 한 사용자 권한을 요인; 되지 않습니다. 전자 메일 주소 단순히 위치에 알려 Exchange Online에 연결 합니다.
  
   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=<emailaddress> -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```

   예 연결 하려는 지리적으로 유효한 사서함의 전자 메일 주소 olga@contoso.onmicrosoft.com을 사용 하는 경우에 다음 명령을 실행 합니다.

   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=olga@contoso.onmicrosoft.com -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```
3. 다음 명령을 실행합니다.
    
    ```
    Import-PSSession $Session
    ```

### <a name="azure-ad-connect-version-requirements"></a>Azure AD 연결 버전 요구 사항
AAD 연결 버전 1.1.524.0 또는 이상 온-프레미스 Active Directory에서 동기화 되는 사용자 개체에서 **PreferredDataLocation** 속성을 설정 하기 위한 방법만 지원된 됩니다. AAD에 AAD 연결을 통해 동기화 하는 사용자 개체 AAD PowerShell을 통해 직접 수정 하는 **PreferredDataLocation** 값을 가질 수 없습니다. AAD PowerShell을 통해 클라우드 전용 사용자 개체를 수정할 수 있습니다. 자세한 내용은 참조 하십시오. [Azure Active Directory 연결 동기화: Office 365 리소스에 대 한 기본 설정된 데이터 위치 구성](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation)합니다.

### <a name="geo-codes"></a>지리적으로 분산 코드
세 글자로 된 코드를 사용 하 여 **PreferredDataLocation** 속성에는 지리적으로 분산을 지정 합니다. 다음 표에서 사용 가능한 Geos에 대 한 코드가 나와 있습니다.

|지역 |코드 |
|---------|---------|
|아시아/태평양 |APC |
|오스트레일리아 |AUS |
|캐나다 |CAN |
|유럽 연합 |EUR |
|프랑스 |FRA|
|인도 |찾기 |
|일본 |JPN |
|한국 |KOR |
|영국 |GBR |
|미국 |NAM |

**참고**: **PreferredDataLocation** 및 **MailboxRegion** 속성은 문자열 없음 오류 검사 합니다. 잘못 된 값 (예: NAN)를 입력 하는 경우 사서함 기본 지리적으로 분산에에서 배치 됩니다.

### <a name="view-the-available-geos-that-are-configured-in-your-exchange-online-organization"></a>Exchange Online 조직에 구성 된 사용 가능한 Geos 보기
Exchange Online 조직에 구성 된 Geos의 목록을 보려면 다음 명령을 실행 Exchange Online PowerShell:

```
Get-OrganizationConfig | Select -ExpandProperty AllowedMailboxRegions | Format-Table
```

이 명령의 출력은 다음과 같습니다.

```
APC
AUS
CAN
EUR
FRA
GBR
JPN
KOR
NAM
```

### <a name="view-the-default-geo-for-your-exchange-online-organization"></a>Exchange Online 조직에 대 한 기본 지리적으로 분산 보기
Exchange Online 조직의 기본 geo를 보려면 다음 명령을 실행 Exchange Online PowerShell:

```
Get-OrganizationConfig | Select DefaultMailboxRegion
```

이 명령의 출력은 다음과 같습니다.

```
DefaultMailboxRegion
--------------------
NAM
```


### <a name="find-the-geo-location-of-a-mailbox"></a>사서함의 지리적 위치를 찾기
사서함에서 다음 지리적으로 분산 관련 속성을 표시 하는 Exchange Online PowerShell에서 **Get-mailbox** cmdlet:

- **데이터베이스**: 사서함이 현재 위치한 지시 지리적으로 분산 코드에 해당 하는 처음 3 글자 데이터베이스 이름입니다. 온라인 보관 사서함 **archivedatabase 사서함의 경우** 에 대 한 속성을 사용 해야 합니다.

- **MailboxRegion**: (Azure AD에 **PreferredDataLocation** 에서 동기화) 관리자에 의해 설정 된 지리적으로 분산 코드를 지정 합니다.

- **MailboxRegionLastUpdateTime**: MailboxRegion 마지막으로 업데이트 된 시간 (자동 또는 수동)를 나타냅니다.

사서함에 대 한 이러한 속성을 보려면 다음 구문을 사용 합니다.

```
Get-Mailbox -Identity <MailboxIdentity> | Format-List Database,MailboxRegion*
```

예, 사서함 chris@contoso.onmicrosoft.com에 대 한 지리적으로 분산 정보를 보려면 다음 명령을 실행 합니다.

```
Get-Mailbox -Identity chris@contoso.onmicrosoft.com | Format-List Database, MailboxRegion*
```

이 명령의 출력은 다음과 같습니다.

```
Database                    : EURPR03DG077-db007 
MailboxRegion               : EUR 
MailboxRegionLastUpdateTime : 2/6/2018 8:21:01 PM 
```

> **참고:** 데이터베이스 이름에서 지리적으로 분산 코드 **MailboxRegion** 값을 일치 하지 않으면, 사서함 자동으로 재배치 큐에 배치 될 수 있습니다 하 고 이러한 불일치에 대 한 (Exchange Online 모양 **MailboxRegion** 값으로 지정 된 지리적으로 이동 속성 값)입니다.

### <a name="move-an-existing-cloud-only-mailbox-to-a-specific-geo"></a>특정 지리적으로 기존 클라우드 전용 사서함 이동
클라우드 전용 사용자가 사용자를 AAD 연결을 통해 테 넌 트 syncrhonized 하지 않습니다. 이 사용자는 Azure AD에서 직접 작성 되었습니다. Windows PowerShell 용 Azure AD 모듈 **Get-msoluser** 및 **이와** cmdlet을 사용 하 여를 보거나 클라우드 전용 사용자의 사서함을 저장할 하 여 지리적으로 분산을 지정 합니다.

사용자에 대 한 **PreferredDataLocation** 값을 보려면 Azure AD PowerShell에서이 구문을 사용 합니다.

```
Get-MsolUser -UserPrincipalName <UserPrincipalName> | Format-List UserPrincipalName,PreferredDataLocation
```

예, 사용자 michelle@contoso.onmicrosoft.com에 대 한 **PreferredDataLocation** 값을 보려면 다음 명령을 실행 합니다.

```
Get-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com | Format-List
```

이 명령의 출력은 다음과 같습니다.

```
UserPrincipalName     : michelle@contoso.onmicrosoft.com
PreferredDataLocation : EUR
```

클라우드 전용 사용자 개체에 대 한 **PreferredDataLocation** 값을 수정 하려면 다음 구문을 사용 하 여 Azure AD PowerShell에서:

``` 
Set-MsolUser -UserPrincipalName <UserPrincipalName> -PreferredDataLocation <GeoCode>
```

예, 사용자 michelle@contoso.onmicrosoft.com에 대 한 유럽 연합 (EUR) geo로 **PreferredDataLocation** 값을 설정 하려면 다음 명령을 실행 합니다.

``` 
Set-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com -PreferredDataLocation EUR
```

**참고:**

- 설명한 것 처럼 이전에 사용할 수 없습니다이 절차에서 온-프레미스 Active Directory 동기화 된 사용자 개체에 대 한 합니다. AAD 연결을 사용 하 여 **PreferredDataLocation** 값을 변경 해야 합니다. 자세한 내용은 참조 [Azure Active Directory 연결 동기화: Office 365 리소스에 대 한 기본 설정된 데이터 위치 구성](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation)합니다. 

- 얼마나 오래 걸리는 여러 요인에 따라 새 원하는 지리적으로 분산 하는 현재 지리적으로 분산 mailboxfrom 위치를 변경 하려면:
 
  - 사서함의 종류와 크기입니다.
 
  - 이동 중인 사서함의 수입니다.
 
  - 이동 리소스의 가용성입니다.

#### <a name="move-disabled-mailboxes-that-are-on-litigation-hold"></a>소송 보존으로 설정에 있는 사서함을 사용 하지 않도록 설정 하는 이동
EDiscovery 목적으로 사용할 수 없는 상태로 자신의 **PreferredDataLocation** 값을 변경 하 여 이동할 수에 대 한 보존 되 소송 보존으로 설정에 있는 사서함을 사용할 수 없습니다. 소송 보존에 사용할 수 없는 사서함을 이동할:

1. 일시적으로 사서함 라이선스를 할당 합니다.

2. **PreferredDataLocation**를 변경 합니다.

3. 그를 사용할 수 없는 상태로 다시 설정 하려면 선택 된 지리적으로 분산을 이동 된 후 사서함에서 라이선스를 제거 합니다.

### <a name="create-new-cloud-mailboxes-in-a-specific-geo"></a>특정 지리적에서 새 클라우드 사서함 만들기 
새 사서함에는 특정 지리적으로 분산을 만들려면 다음이 단계 중 하나를 수행 해야 합니다.

- 이전 섹션 *하기 전에* 사서함이 Exchange에서 만든 온라인에서 설명한 대로 **PreferredDataLocation** 값을 구성 합니다. 라이선스를 할당 하기 전에 사용자에 **PreferredDataLocation** 값을 구성 예입니다. 

- **PreferredDataLocation** 값을 설정 하는 동시에 게 라이선스를 할당 합니다.

새 클라우드 전용 사용이 허가 된 사용자 (AAD 연결 하지 동기화)에 특정 지리적으로 분산을 만들려면 Azure AD PowerShell에서 다음 구문을 사용 합니다.

```
New-MsolUser -UserPrincipalName <UserPrincipalName> -DisplayName "<Display Name>" [-FirstName <FirstName>] [-LastName <LastName>] [-Password <Password>] [-LicenseAssignment <AccountSkuId>] -PreferredDataLocation <GeoCode> 
```
이 예제에서는 다음 값을 갖는 동 Brunner에 대 한 새 사용자 계정을 만듭니다.

- 사용자 계정 이름: ebrunner@contoso.onmicrosoft.com

- 이름: 동

- 성: Brunner

- 표시 이름 동 Brunner

- 암호: 임의로 생성 하 고 (하기 때문에 *Password* 매개 변수를 사용 하지) 명령의 결과에 표시 된

- 라이선스: contoso:ENTERPRISEPREMIUM (e 5)

- 위치: 오스트레일리아 (오스트레일리아)

```
New-MsolUser -UserPrincipalName ebrunner@contoso.onmicrosoft.com -DisplayName "Elizabeth Brunner" -FirstName Elizabeth -LastName Brunner -LicenseAssignment contoso:ENTERPRISEPREMIUM -PreferredDataLocation AUS
```

새 사용자 계정 만들기 및 Azure AD PowerShell에서 LicenseAssignment 값 찾기 (영문) 하는 방법에 대 한 자세한 내용은 [Office 365 PowerShell을 사용한 사용자 계정 만들기](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell) 및 [보기 라이선스 및 Office 365 PowerShell을 사용 하 여 서비스를](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell)참조 하십시오.

> **참고:** 예: **Enable-mailbox** 또는 **New-mailbox Exchange Online cmdlet을 사용 하 여 해야 사서함을 사용 하도록 설정 하 고 필요한 **PreferredDataLocation**에 지정 된 지리적으로 분산에서 직접 만들어야 하는 사서함을 Exchange Online PowerShell를 사용 하는 경우 **클라우드 서비스에 대해 직접 합니다. **Enable-remotemailbox** 온-프레미스 Exchange cmdlet을 사용 하면 사서함의 기본 지리적으로 분산에서에서 만들어집니다.

### <a name="onboard-existing-on-premises-mailboxes-in-a-specific-geo"></a>온보드 기존 온-프레미스 사서함에는 특정 지리적으로 분산
온-프레미스 Exchange 조직에서 사서함을 Exchange Online에 포함 하 여 [EAC의 마이그레이션 대시보드](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331)및 [New-migrationbatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch) cmdlet은 Exchange 온라인 마이그레이션할 표준 온 보 딩 도구와 프로세스를 사용할 수 있습니다. PowerShell 합니다.

첫번째 단계에서는 onboarded, 되어야 하 고 Azure AD에 올바른 **PreferredDataLocation** 값을 구성 하는 확인 하는 각 사서함에 대해 존재 하는 사용자 개체를 확인 하는 것입니다. 온 보 딩 도구 **PreferredDataLocation** 값 존중 하 고는 지정 된 지리적으로 분산을 직접는 사서함을 마이그레이션합니다.

또는 Exchange Online PowerShell에서 [New-moverequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest) cmdlet을 사용 하는 특정 지리적으로 분산에서 직접 온보드 사서함에 다음 단계를 사용할 수 있습니다.

1. Onboarded 및 **PreferredDataLocation** Azure AD에 원하는 값으로 설정 되어 되도록 각 사서함에 대 한 사용자 개체가 있는지 확인 합니다. **PreferredDataLocation** 값 동기화 됩니다 해당 메일 사용자 개체의 **MailboxRegion** 특성에 Exchange Online.

2. 이 항목의 앞부분에서 연결 지침을 사용 하 여 지리적으로 분산 된 특정 위성에 직접 연결 합니다.

3. Exchange Online PowerShell에서 다음 명령을 실행 하 여 변수에 사서함 마이그레이션을 수행 하기 위해 사용 되는 온-프레미스 관리자 자격 증명을 저장 합니다.

    ```
    $RC = Get-Credential
    ```

4. Exchange Online PowerShell에서 새 **New-moverequest** 를 다음 예제와 비슷한 만듭니다. 

    ```
    New-MoveRequest -Remote -RemoteHostName mail.contoso.com -RemoteCredential $RC -Identity user@contoso.com -TargetDeliveryDomain <YourAppropriateDomain>
    ```

5. 온-프레미스 Exchange에서 연결할 현재 지리적으로 분산 위성으로 마이그레이션하기 위해 필요한 모든 사서함에 대 한 #4 단계를 반복 합니다.

6. 다른 위성 지리적으로 분산을 추가 사서함 마이그레이션 해야하는 경우 각 특정 위성 지리적으로 분산에 대해 2 ~ 4 단계를 반복 합니다.

### <a name="multi-geo-reporting"></a>다중-지리적으로 분산 보고
지리적으로 분산 하 여 사용자 수를 표시 하는 Office 365 관리 센터에서 **다중-지리적으로 분산 사용 현황 보고서** 입니다. 보고서 현재 달에 대 한 사용자 분포를 표시 하 고 지난 6 개월에 대 한 기록 데이터를 제공 합니다.
