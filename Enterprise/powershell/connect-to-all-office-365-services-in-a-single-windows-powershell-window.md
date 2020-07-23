---
title: 단일 Windows PowerShell 창에서 모든 Microsoft 365 서비스에 연결
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/10/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- LIL_Placement
- Ent_Office_Other
- O365ITProTrain
- httpsfix
ms.assetid: 53d3eef6-4a16-4fb9-903c-816d5d98d7e8
description: '요약: 단일 Windows PowerShell 창에서 모든 Microsoft 365 서비스에 Windows PowerShell을 연결 합니다.'
ms.openlocfilehash: a037de53dcbf8fed95b9b4d5f05677997135dfb3
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230844"
---
# <a name="connect-to-all-microsoft-365-services-in-a-single-windows-powershell-window"></a>단일 Windows PowerShell 창에서 모든 Microsoft 365 서비스에 연결

PowerShell을 사용 하 여 Microsoft 365을 관리 하는 경우 Microsoft 365 관리 센터, SharePoint Online, Exchange Online, 비즈니스용 Skype Online, Microsoft 팀 및 보안 준수 센터에 해당 하는 것과 동일한 시간에 최대 5 개의 서로 다른 Windows PowerShell 세션이 열리도록 할 수 있습니다 &amp; . 별도의 Windows PowerShell 세션에서 5 가지 서로 다른 연결 방법을 사용 하는 경우 데스크톱은 다음과 같이 표시 될 수 있습니다.
  
![동시에 실행되는 5개의 Windows PowerShell 콘솔](media/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
서비스 간 관리를 위해 이러한 5 개의 창 간에 데이터를 교환할 수 없기 때문에 Microsoft 365을 관리 하는 데는 최적이 지 않습니다. 이 항목에서는 Microsoft 365 계정, 비즈니스용 Skype Online, Exchange Online, SharePoint Online, Microsoft 팀 및 보안 준수 센터를 관리할 수 있는 단일 Windows PowerShell 인스턴스를 사용 하는 방법에 대해 설명 합니다 &amp; .

>[!Note]
>이 문서에는 현재 전 세계 (+ GCC) 클라우드에 연결 하는 명령만 포함 되어 있습니다. 추가 참고 사항에는 다른 Microsoft 365 클라우드에 연결에 대 한 정보가 포함 된 문서의 링크가 제공 됩니다.
>

## <a name="before-you-begin"></a>시작하기 전에

단일 Windows PowerShell 인스턴스에서 모든 Microsoft 365을 관리 하려면 먼저 다음 필수 구성 요소를 고려 하십시오.
  
- 이러한 절차에 사용 하는 Microsoft 365 회사 또는 학교 계정은 Microsoft 365 관리자 역할의 구성원 이어야 합니다. 자세한 내용은 [관리자 역할 정보](https://docs.microsoft.com/microsoft-365/admin/add-users/about-admin-roles?view=o365-worldwide)를 참조하세요. 이는 Microsoft 365 용 PowerShell에 대 한 요구 사항으로, 다른 모든 Microsoft 365 서비스에 꼭 필요한 것은 아닙니다.
    
- 다음 Windows 버전을 사용할 수 있습니다.
    
  - Windows 10
    
  - Windows 8.1 또는 Windows 8
    
  - Windows Server 2019
    
  - Windows Server 2016
    
  - Windows Server 2012 R2 또는 Windows Server 2012
    
  - Windows 7 SP1(서비스 팩 1)*
    
  - Windows Server 2008 R2 SP1*
    
    \*Microsoft .NET Framework 4.5를 설치 해야 합니다. *x* 를 누른 다음 Windows management framework 3.0 또는 Windows management framework 4.0 중 하나를 클릭 합니다. 자세한 내용은 [.Net Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) 및 [windows management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) 또는 [Windows management framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344)설치를 참조 하세요.
    
    비즈니스용 Skype Online 모듈 및 Microsoft 365 모듈 중 하나에 대 한 요구 사항으로 인해 64 비트 버전의 Windows를 사용 해야 합니다.
    
- Azure Active Directory (Azure AD), Exchange Online, SharePoint Online, 비즈니스용 Skype Online 및 팀에 필요한 모듈을 설치 해야 합니다.
    
   - [Azure Active Directory V2](connect-to-office-365-powershell.md##connect-with-the-azure-active-directory-powershell-for-graph-module)
   - [SharePoint Online 관리 셸](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [비즈니스용 Skype Online, Windows PowerShell 모듈](https://go.microsoft.com/fwlink/p/?LinkId=532439)
   - [Exchange Online PowerShell V2](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell-v2/exchange-online-powershell-v2?view=exchange-ps#install-and-maintain-the-exchange-online-powershell-v2-module)
   - [팀 PowerShell 개요](https://docs.microsoft.com/microsoftteams/teams-powershell-overview)
    
-  비즈니스용 Skype 온라인 및 보안 및 준수 센터에 대 한 서명 된 스크립트를 실행 하도록 Windows PowerShell을 구성 해야 &amp; 합니다. 이 작업을 수행 하려면 **관리자 권한으로 실행**을 선택 하 여 연 windows powershell 창에서 다음 명령을 실행 합니다.
    
  ```powershell
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="connection-steps-when-using-just-a-password"></a>암호만 사용 하는 경우의 연결 단계

로그인에 대 한 암호만 사용 하는 경우에는 단일 PowerShell 창에서 모든 서비스에 연결 하는 단계는 다음과 같습니다.
  
1. Windows PowerShell을 엽니다.
    
2. 이 명령을 실행 하 고 Microsoft 365 회사 또는 학교 계정 자격 증명을 입력 합니다.
    
  ```powershell
  $credential = Get-Credential
  ```

3. 이 명령을 실행 하 여 Graph 모듈에 대 한 Azure Active Directory PowerShell을 사용 하 여 Azure AD에 연결 합니다.
    
  ```powershell
  Connect-AzureAD -Credential $credential
  ```
  
  또는 Windows PowerShell 모듈에 대 한 Microsoft Azure Active Directory 모듈을 사용 하는 경우에는이 명령을 실행 합니다.
      
  ```powershell
  Connect-MsolService -Credential $credential
 ```

>[!Note]
>PowerShell Core는 Windows PowerShell용 Microsoft Azure Active Directory 모듈 및 이름에 **Msol**이 있는 cmdlet을 지원하지 않습니다. 이러한 cmdlet을 계속 사용하려면 Windows PowerShell에서 이를 실행해야 합니다.
>

4. 다음 명령을 실행 하 여 SharePoint Online에 연결 합니다. 도메인의 조직 이름을 지정 합니다. 예를 들어 "litwareinc.onmicrosoft.com"의 경우 조직 이름 값은 "litwareinc"입니다.
    
  ```powershell
  $orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
  Connect-SPOService -Url https://$orgName-admin.sharepoint.com -Credential $userCredential
  ```

5. 다음 명령을 실행 하 여 비즈니스용 Skype Online에 연결 합니다. 처음 연결할 때 값을 늘리는 경고는 `WSMan NetworkDelayms` 예상 되며 무시 해야 합니다.
    
  ```powershell
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. 이 명령을 실행 하 여 Exchange Online에 연결 합니다.
    
  ```powershell
  Connect-ExchangeOnline -Credential $credential -ShowProgress $true
  ```

>[!Note]
>전 세계 이외의 Microsoft 365 클라우드를 위해 Exchange Online에 연결 하려면 **-ExchangeEnvironmentName** 매개 변수를 사용 합니다. 자세한 내용은 [ExchangeOnline](https://docs.microsoft.com/powershell/module/exchange/powershell-v2-module/connect-exchangeonline?view=exchange-ps) 를 참조 하십시오.
>

7. 다음 명령을 실행 하 여 팀 PowerShell에 연결 합니다.
    
  ```powershell
  Import-Module MicrosoftTeams
  Connect-MicrosoftTeams -Credential $credential
  ```
  
>[!Note]
>전 세계 이외의 Microsoft 팀 클라우드에 연결 하려면 [연결-MicrosoftTeams](https://docs.microsoft.com/powershell/module/teams/connect-microsoftteams?view=teams-ps)를 참조 하세요.
>

8. 보안 및 준수 센터에 연결 하려면 다음 명령을 실행 &amp; 합니다.
    
  ```powershell
  $SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $SccSession -Prefix cc
  ```

>[!Note]
>&amp;전 세계적인 Microsoft 365 클라우드의 보안 준수 센터에 연결 하려면 [Connect to Security & 준수 센터 PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell)를 참조 하세요.
>

다음은 Graph 모듈에 대 한 Azure Active Directory PowerShell을 사용할 때 단일 블록에 있는 모든 명령입니다. 도메인 호스트의 이름을 지정 하 고 한 번에 모두 실행 합니다.
  
```powershell
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-AzureAD -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
Connect-ExchangeOnline -Credential $credential -ShowProgress $true
Import-Module MicrosoftTeams
Connect-MicrosoftTeams -Credential $credential
```

다음에는 Windows PowerShell 용 Microsoft Azure Active Directory 모듈 모듈을 사용할 때 단일 블록에 있는 모든 명령이 나와 있습니다. 도메인 호스트의 이름을 지정 하 고 한 번에 모두 실행 합니다.
  
```powershell
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-MsolService -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
Connect-ExchangeOnline -Credential $credential -ShowProgress $true
Import-Module MicrosoftTeams
Connect-MicrosoftTeams -Credential $credential
```

Windows PowerShell 창을 종료할 준비가 되 면 다음 명령을 실행 하 여 비즈니스용 Skype Online, SharePoint Online, 보안 &amp; 준수 센터 및 팀에 대 한 활성 세션을 제거 합니다.
  
```powershell
Remove-PSSession $sfboSession ; Remove-PSSession $SccSession ; Disconnect-SPOService ; Disconnect-MicrosoftTeams 
```

## <a name="connection-steps-when-using-multi-factor-authentication"></a>다단계 인증을 사용 하는 경우의 연결 단계

다음은 Graph 모듈에 대 한 Azure Active Directory PowerShell을 사용 하 여 단일 창에서 Azure AD, SharePoint Online, 비즈니스용 Skype, Exchange Online 및 팀에 연결 하는 단일 블록의 모든 명령입니다. 사용자 계정의 UPN (사용자 계정 이름) 이름과 도메인 호스트 이름을 지정한 다음 한 번에 모두 실행 합니다.

```powershell
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-AzureAD
#SharePoint Online
Connect-SPOService -Url https://$orgName-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
#Exchange Online
Connect-ExchangeOnline -UserPrincipalName $acctName -ShowProgress $true
#Teams
Import-Module MicrosoftTeams
Connect-MicrosoftTeams
```

다음에는 Windows PowerShell 용 Microsoft Azure Active Directory 모듈 모듈을 사용할 때의 모든 명령이 나와 있습니다.

```powershell
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-MsolService
#SharePoint Online
Connect-SPOService -Url https://$orgName-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
#Exchange Online
Connect-ExchangeOnline -UserPrincipalName $acctName -ShowProgress $true
#Teams
Import-Module MicrosoftTeams
Connect-MicrosoftTeams
```

보안 및 준수 센터에 대해 multi-factor authentication을 사용 하 여 다단계 인증을 통해 연결 하는 &amp; [보안 & 준수 센터 PowerShell에 연결](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps) 을 참조 하세요.

## <a name="see-also"></a>참고 항목

- [PowerShell을 사용 하 여 Microsoft 365에 연결](connect-to-office-365-powershell.md)
- [PowerShell을 사용 하 여 SharePoint Online 관리](manage-sharepoint-online-with-office-365-powershell.md)
- [PowerShell을 사용 하 여 Microsoft 365 사용자 계정, 라이선스 및 그룹 관리](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [Windows PowerShell을 사용 하 여 Microsoft 365에서 보고서 만들기](use-windows-powershell-to-create-reports-in-office-365.md)
