---
title: Multi-Geo 환경에서 Exchange Online 사서함 관리
ms.author: chrisda
author: chrisda
manager: serdars
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: ''
localization_priority: Priority
description: Microsoft PowerShell을 사용하여 Exchange Online Multi-Geo 설정을 관리하는 방법을 알아보세요.
ms.openlocfilehash: 135d3af76e03dfb7e6fcc9f55ba3be8ab21a6906
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844659"
---
# <a name="administering-exchange-online-mailboxes-in-a-multi-geo-environment"></a>Multi-Geo 환경에서 Exchange Online 사서함 관리

Office 365 환경에서 Multi-Geo 속성을 보고 구성하려면 원격 PowerShell이 필요합니다. Exchange Online PowerShell에 연결하려면 [Exchange Online PowerShell에 연결](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)을 참조하세요.

사용자 개체의 **PreferredDataLocation** 속성을 보려면 v1.x에서 [Microsoft Azure Active Directory PowerShell 모듈](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) v1.1.166.0 이상이 필요합니다. AAD Connect를 통해 AAD에 동기화된 사용자 개체의 **PreferredDataLocation** 값은 AAD PowerShell을 통해 직접 수정할 수 없습니다. 클라우드 전용 사용자 개체는 AAD PowerShell을 통해 수정할 수 있습니다. Azure AD PowerShell에 연결하려면 [Office 365 PowerShell에 연결](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell)을 참조하세요.

## <a name="connect-directly-to-a-geo-location-using-exchange-online-powershell"></a>Exchange Online PowerShell을 사용하여 지리적 위치에 직접 연결

일반적으로 Exchange Online PowerShell은 중앙 지리적 위치에 연결합니다. 그러나 위성 지리적 위치에 직접 연결할 수도 있습니다. 특정 위치의 사용자만 관리하는 경우 성능 개선을 위해 해당 위성 위치에 직접 연결할 것을 권장합니다.

특정 지리적 위치에 연결하려는 경우 *ConnectionUri* 매개 변수가 일반 연결 지침과는 달라집니다. 나머지 명령과 값은 동일합니다. 그 단계는 다음과 같습니다.

1. 로컬 컴퓨터에서 Windows PowerShell을 열고 다음 명령을 실행합니다.

   ```powershell
   $UserCredential = Get-Credential
   ```

   **Windows PowerShell 자격 증명 요청** 대화 상자에서 회사 또는 학교 계정 사용자 이름과 비밀번호를 입력한 다음, **확인**을 클릭합니다.

2. 대상 지리적 위치에서 `<emailaddress>`를 **원하는** 사서함의 이메일 주소로 바꾸고 다음 명령을 실행합니다. 1단계에서 사서함에 대한 권한과 자격 증명과의 관계는 요인이 아닙니다. 이메일 주소는 단지 연결할 위치를 Exchange Online에 알려줄 뿐입니다.
  
   ```powershell
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=<emailaddress> -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```

   예를 들어 olga@contoso.onmicrosoft.com이 연결할 지리적 위치의 유효한 사서함 전자 메일 주소인 경우 다음 명령을 실행합니다.

   ```powershell
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=olga@contoso.onmicrosoft.com -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```

3. 다음 명령을 실행합니다.

    ```powershell
    Import-PSSession $Session
    ```

## <a name="view-the-available-geo-locations-that-are-configured-in-your-exchange-online-organization"></a>Exchange Online 조직에서 구성된 사용 가능한 지리적 위치 보기

Office 365 Multi-Geo에서 구성된 지리적 위치 목록을 보려면 Exchange Online PowerShell에서 다음 명령을 실행합니다.

```powershell
Get-OrganizationConfig | Select -ExpandProperty AllowedMailboxRegions | Format-Table
```

## <a name="view-the-central-geo-location-for-your-exchange-online-organization"></a>Exchange Online 조직의 중앙 지리적 위치 보기

테넌트의 중앙 지리적 위치를 보려면 Exchange Online PowerShell에서 다음 명령을 실행합니다.

```powershell
Get-OrganizationConfig | Select DefaultMailboxRegion
```

## <a name="find-the-geo-location-of-a-mailbox"></a>사서함의 지리적 위치 찾기

Exchange Online PowerShell의 **Get-Mailbox** cmdlet은 사서함에 다음과 같은 Multi-Geo 관련 속성을 표시합니다.

- **Database**: 데이터베이스 이름의 첫 세 글자는 지역 코드에 해당하며, 사서함의 현재 위치를 알려줍니다. 온라인 보관 사서함의 경우 **ArchiveDatabase** 속성을 사용해야 합니다.

- **MailboxRegion**: 관리자가 설정한 지리적 위치 코드를 지정합니다(Azure AD의 **PreferredDataLocation**에서 동기화됨).

- **MailboxRegionLastUpdateTime**: MailboxRegion이 마지막으로 업데이트(자동 또는 수동으로)된 시간을 나타냅니다.

사서함의 속성을 보려면 다음 구문을 사용합니다.

```powershell
Get-Mailbox -Identity <MailboxIdentity> | Format-List Database,MailboxRegion*
```

예를 들어 chris@contoso.onmicrosoft.com의 사서함 위치 정보를 보려면 다음 명령을 실행합니다.

```powershell
Get-Mailbox -Identity chris@contoso.onmicrosoft.com | Format-List Database, MailboxRegion*
```

이 명령의 출력은 다음과 같습니다.

```powershell
Database                    : EURPR03DG077-db007
MailboxRegion               : EUR
MailboxRegionLastUpdateTime : 2/6/2018 8:21:01 PM
```

> **참고:** 데이터베이스 이름의 지리적 위치 코드가 **MailboxRegion** 값과 일치하지 않는 경우 사서함은 자동으로 재배치 큐에 넣어지며 **MailboxRegion** 값에서 지정한 지리적 위치로 이동합니다(Exchange Online이 이러한 속성 값 사이의 불일치를 찾음).

## <a name="move-an-existing-cloud-only-mailbox-to-a-specific-geo-location"></a>기존 클라우드 전용 사서함을 특정 지리적 위치로 이동

클라우드 전용 사용자는 AAD Connect로 테넌트에 동기화되지 않은 사용자입니다. 이 사용자는 Azure AD에서 직접 만들어졌습니다. Windows PowerShell용 Azure AD 모듈에서 **Get-MsolUser** 및 **Set-MsolUser** cmdlet을 사용하여 클라우드 전용 사용자의 사서함을 저장할 지리적 위치를 보거나 지정할 수 있습니다.

사용자의 **PreferredDataLocation** 값을 보려면 Azure AD PowerShell에서 이 구문을 사용합니다.

```powershell
Get-MsolUser -UserPrincipalName <UserPrincipalName> | Format-List UserPrincipalName,PreferredDataLocation
```

예를 들어 사용자 michelle@contoso.onmicrosoft.com의 **PreferredDataLocation** 값을 보려면 다음 명령을 실행합니다.

```powershell
Get-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com | Format-List
```

클라우드 전용 사용자 개체의 **PreferredDataLocation** 값을 수정하려면 Azure AD PowerShell에서 다음 구문을 사용합니다.

```powershell
Set-MsolUser -UserPrincipalName <UserPrincipalName> -PreferredDataLocation <GeoLocationCode>
```

예를 들어 사용자 michelle@contoso.onmicrosoft.com의 유럽 연합(EUR) 지역에 **PreferredDataLocation** 값을 설정하려면 다음 명령을 실행합니다.

```powershell
Set-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com -PreferredDataLocation EUR
```

**참고**:

- 앞서 설명한 대로 온-프레미스 Active Directory의 동기화된 사용자 개체에는 이 절차를 사용할 수 없습니다. Active Directory에서 **PreferredDataLocation** 값을 변경하고 AAD Connect를 사용하여 동기화해야 합니다. 자세한 내용은 [Azure Active Directory Connect 동기화: Office 365 리소스의 기본 데이터 위치 구성](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation)을 참조하세요.

- 새로운 지리적 위치로 사서함 위치를 변경하는 데 걸리는 시간은 몇 가지 요인에 따라 달라집니다.

  - 사서함 크기 및 유형

  - 이동 중인 사서함 수

  - 이동 리소스의 가용성

### <a name="move-disabled-mailboxes-that-are-on-litigation-hold"></a>사용하지 않도록 설정한 소송 보존 중인 사서함 이동

eDiscovery 목적으로 보존된 소송 보존 중인 사서함을 사용하지 않도록 설정하면, 사용하지 않도록 설정한 상태에서 **PreferredDataLocation** 값을 변경해도 이동할 수가 없습니다. 사용하지 않도록 설정한 소송 보존 중인 사서함을 이동하려면:

1. 사서함에 일시적으로 라이선스를 할당합니다.

2. **PreferredDataLocation**을 변경합니다.

3. 선택한 지리적 위치로 라이선스를 이동한 후 사서함에서 라이선스를 제거함으로써 사용 안 함 상태로 되돌립니다.

## <a name="create-new-cloud-mailboxes-in-a-specific-geo-location"></a>특정 지리적 위치에 새 클라우드 사서함 만들기

특정 지리적 위치에 새 사서함을 만들려면 다음 단계 중 하나를 수행해야 합니다.

- Exchange Online에 사서함을 만들기 *전에* 이전 섹션에 설명된 대로 **PreferredDataLocation** 값부터 구성합니다. 예를 들어 라이선스를 할당하기 전에 먼저 사용자의 **PreferredDataLocation** 값을 구성합니다.

- **PreferredDataLocation** 값을 설정함과 동시에 라이선스를 할당합니다.

특정 지리적 위치에 새로운 클라우드 전용 라이선스 사용자 (AAD Connect 동기화가 아닌)를 만들려면 Azure AD PowerShell에서 다음 구문을 사용하십시오.

```powershell
New-MsolUser -UserPrincipalName <UserPrincipalName> -DisplayName "<Display Name>" [-FirstName <FirstName>] [-LastName <LastName>] [-Password <Password>] [-LicenseAssignment <AccountSkuId>] -PreferredDataLocation <GeoLocationCode>
```

이 예제에서는 다음 값을 사용하여 Elizabeth Brunner를 위한 새 사용자 계정을 만듭니다.

- 사용자 계정 이름: ebrunner@contoso.onmicrosoft.com

- 이름: Elizabeth

- 성: Brunner

- 표시할 이름: Elizabeth Brunner

- 비밀번호: 임의로 생성되고 명령의 결과에 표시됨(*비밀번호* 매개 변수를 사용하지 않고 있기 때문)

- 라이선스: `contoso:ENTERPRISEPREMIUM` (E5)

- 위치: 오스트레일리아(AUS)

```powershell
New-MsolUser -UserPrincipalName ebrunner@contoso.onmicrosoft.com -DisplayName "Elizabeth Brunner" -FirstName Elizabeth -LastName Brunner -LicenseAssignment contoso:ENTERPRISEPREMIUM -PreferredDataLocation AUS
```

새 사용자 계정을 만들고 Azure AD PowerShell에서 LicenseAssignment 값을 찾는 방법에 대한 자세한 내용은 [Office 365 PowerShell을 사용하여 사용자 계정 만들기](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell) 및 [Office 365 PowerShell을 사용하여 라이선스 및 서비스 보기](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell)를 참조하세요.

> [!NOTE]
> Exchange Online PowerShell로 사서함을 사용하도록 설정하고 해당 사서함을 **PreferredDataLocation**에 지정된 지리적 위치에 직접 만들려면 **Enable-Mailbox** 또는 **New-Mailbox** 등의 Exchange Online cmdlet을 클라우드 서비스에 직접 사용해야 합니다. 온 - 프레미스 Exchange PowerShell에서 **Enable-RemoteMailbox** cmdlet를 사용하면 사서함이 중앙 지리적 위치에 만들어집니다.

## <a name="onboard-existing-on-premises-mailboxes-in-a-specific-geo-location"></a>특정 지리적 위치에 기존 온-프레미스 사서함 등록

표준 등록 도구와 프로세스를 사용하여 사서함을 온-프레미스 Exchange 조직에서 Exchange Online으로 마이그레이션할 수 있습니다([EAC의 마이그레이션 대시보드](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331), Exchange Online PowerShell의 [New-MigrationBatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch) cmdlet 포함).

첫 번째 단계는 등록될 사서함마다 사용자 개체가 있는지 확인하고 Azure AD에 올바른 **PreferredDataLocation** 값이 구성되었는지 확인하는 일입니다. 등록 도구는 **PreferredDataLocation** 값을 고려하고 사서함을 지정된 지리적 위치에 직접 마이그레이션합니다.

또는 Exchange Online PowerShell의 [새로 만들기 MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest) cmdlet을 사용하는 다음 단계를 통해 사서함을 특정 지리적 위치에 직접 등록할 수 있습니다.

1. 등록될 사서함마다 사용자 개체가 있고 **PreferredDataLocation**이 Azure AD에서 원하는 값으로 설정되어 있는지 확인합니다. **PreferredDataLocation** 값은 Exchange Online에서 해당 메일 사용자 개체의 **MailboxRegion** 특성에 동기화됩니다.

2. 이 항목 앞부분의 연결 지침을 사용하여 특정 위성 지리적 위치에 직접 연결하십시오.

3. Exchange Online PowerShell에서 다음 명령을 실행하여, 변수에서 사서함 마이그레이션을 수행하는 데 사용되는 온-프레미스 관리자 자격 증명을 저장합니다.

   ```powershell
   $RC = Get-Credential
   ```

4. Exchange Online PowerShell에서 다음 예제와 비슷한 새로운 **New-MoveRequest**를 만듭니다.

   ```powershell
   New-MoveRequest -Remote -RemoteHostName mail.contoso.com -RemoteCredential $RC -Identity user@contoso.com -TargetDeliveryDomain <YourAppropriateDomain>
   ```

5. 온-프레미스 Exchange에서 현재 연결된 위성 지리적 위치로 마이그레이션해야 할 모든 사서함에 4단계를 반복합니다.

6. 다른 위성 지리적 위치에 추가 사서함을 마이그레이션해야 할 경우 각각의 특정 위치에 2단계에서 4단계까지를 반복합니다.

## <a name="multi-geo-reporting"></a>Multi-Geo 보고

Microsoft 365 관리자 센터의 **Multi-Geo 사용 보고서**는 지리적 위치별 사용자 수를 표시합니다. 보고서는 이번 달의 사용자 분포를 표시하고 지난 6개월 동안의 기록 데이터를 제공합니다.

## <a name="see-also"></a>참고 항목

[Windows PowerShell로 Office 365 및 Exchange Online 관리](https://support.office.com//article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6)
