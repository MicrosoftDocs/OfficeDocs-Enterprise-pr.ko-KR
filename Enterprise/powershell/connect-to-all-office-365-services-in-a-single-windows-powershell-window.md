---
title: 단일 Windows PowerShell 창에서 모든 Microsoft 365 서비스에 연결
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/10/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- LIL_Placement
- Ent_Office_Other
- O365ITProTrain
- httpsfix
ms.assetid: 53d3eef6-4a16-4fb9-903c-816d5d98d7e8
description: '요약: Windows PowerShell 창에서 모든 Windows PowerShell을 Microsoft 365 서비스에 연결'
ms.openlocfilehash: de6bb592233b44a14848b1512230197bb8eb75fb
ms.sourcegitcommit: 1aaa4c6d10eb14f4b3d5a452f2e64c96f5d96ae4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "46560063"
---
# <a name="connect-to-all-microsoft-365-services-in-a-single-windows-powershell-window"></a>단일 Windows PowerShell 창에서 모든 Microsoft 365 서비스에 연결

PowerShell을 사용하여 Microsoft 365를 관리하는 경우 Microsoft 365 관리 센터, SharePoint 온라인, Exchange 온라인, 비즈니스용 Skype 온라인, Microsoft 팀 및 보안 &amp; 준수 센터에 해당 하는 최대 5개의 다른 Windows PowerShell 세션을 열 수 있습니다. 별도의 Windows PowerShell 세션에서 5개의 다른 연결 방법을 사용하면 바탕 화면은 다음과 같이 표시됩니다.
  
![한번에 5개의 Windows PowerShell 콘솔 실행](media/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
5개의 서비스 관리센터간에 데이터를 교환 할 수 없기 때문에 최적의 Microsoft 365 관리 방법이 아닙니다. 이 항목에서는 Microsoft 365 계정, 비즈니스용 Skype 온라인, Exchange 온라인, SharePoint 온라인, Microsoft 팀 및 보안 &amp; 준수 센터를 관리 하는 데 사용할 수 있는 Windows PowerShell의 단일 인스턴스를 사용하는 방법을 설명합니다.

>[!Note]
>현재 이 문서에는 전 세계(+GCC) 클라우드에 연결하는 명령만 포함 되어 있습니다. 추가 노트에서는 Microsoft 365 클라우드에 연결하는 방법에 대한 정보가 포함 된 문서 링크를 제공합니다.
>

## <a name="before-you-begin"></a>시작하기 전에

단일 Windows PowerShell 인스턴스에서 모든 Microsoft 365를 관리하기 전에 다음 필수 구성 요소를 고려하세요.
  
- 이러한 절차에 사용하는 Microsoft 365회사 또는 학교 계정은 Microsoft 365 관리자 역할의 구성원이어야 합니다. 자세한 내용은 [관리자 역할 정보](https://docs.microsoft.com/microsoft-365/admin/add-users/about-admin-roles?view=o365-worldwide)를 참조하세요. 이러한 Microsoft 365 PowerShell 요구 사항은 모든 Microsoft 365 서비스 요구 사항이 아닙니다.
    
- 다음 64비트 Windows 버전을 사용할 수 있습니다.
    
  - Windows 10
    
  - Windows 8.1 또는 Windows 8
    
  - Windows Server 2019
    
  - Windows Server 2016
    
  - Windows Server 2012 R2 또는 Windows Server 2012
    
  - Windows 7 SP1(서비스 팩 1)*
    
  - Windows Server 2008 R2 SP1*
    
    \* Microsoft .NET Framework 4.5. *x*를 설치한 다음 Windows Management Framework 3.0 또는 Windows Management Framework 4.0을 설치해야 합니다. 자세한 내용은 [.NET Framework 설치](https://go.microsoft.com/fwlink/p/?LinkId=257868) 및 [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) 혹은 [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344)을 참조하세요.
    
    비즈니스용 Skype 온라인과 하나의 Microsoft 365 모듈 요구 사항 때문에 64비트 버전의 Windows를 사용해야 합니다.
    
- Azure Active Directory(Azure AD), Exchange 온라인, SharePoint 온라인, 비즈니스용 Skype 온라인 및 Teams에 필요한 모듈을 설치해야 합니다.
    
   - [Azure Active Directory V2](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)
   - [SharePoint Online 관리 셸](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [Windows PowerShell 모듈을 사용하여 비즈니스용 Skype 온라인 관리](https://go.microsoft.com/fwlink/p/?LinkId=532439)
   - [Exchange 온라인 PowerShell V2](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell-v2/exchange-online-powershell-v2?view=exchange-ps#install-and-maintain-the-exchange-online-powershell-v2-module)
   - [Teams PowerShell 개요](https://docs.microsoft.com/microsoftteams/teams-powershell-overview)
    
-  비즈니스용 Skype 온라인 및 보안 &amp; 준수 센터에 대한 서명 된 스크립트를 실행 하려면 Windows PowerShell을 구성해야 합니다. 이렇게 하려면 다음 명령어를 상위 Windows PowerShell 세션에서 실행하세요(**관리자 권한으로 실행**을 선택하여 열린 Windows PowerShell).
    
   ```powershell
   Set-ExecutionPolicy RemoteSigned
   ```

## <a name="connection-steps-when-using-just-a-password"></a>암호만 사용하는 경우 연결 단계

로그인에 암호만 사용 하는 경우 단일 PowerShell 창에서 모든 서비스에 연결 하기 위한 단계는 다음과 같습니다.
  
1. Windows PowerShell을 엽니다.
    
2. 이 명령을 실행하여 Microsoft 365 회사 또는 학교 계정 자격 증명을 입력합니다.
    
   ```powershell
   $credential = Get-Credential
   ```

3. 이 명령을 실행하여 Graph 모듈인 Azure Active Directory PowerShell을 사용해 Azure AD에 연결 합니다.
    
   ```powershell
   Connect-AzureAD -Credential $credential
   ```
  
   또는, Windows PowerShell 모듈에 대한 Microsoft Azure Active Directory 모듈을 사용 중이라면 이 명령을 실행하세요.
      
   ```powershell
   Connect-MsolService -Credential $credential
   ```

   > [!Note]
   > PowerShell Core는 Windows PowerShell용 Microsoft Azure Active Directory 모듈 및 이름에 **Msol**이 있는 cmdlet을 지원하지 않습니다. 이러한 cmdlet을 계속 사용하려면 Windows PowerShell에서 이를 실행해야 합니다.

4. SharePoint 온라인에 연결 하려면 이 명령을 실행하세요. 도메인에 대한 조직 이름을 지정합니다. 예를 들어 "litwareinc.onmicrosoft.com"의 경우 조직 이름 값은 "litwareinc"입니다.
    
   ```powershell
   $orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
   Connect-SPOService -Url https://$orgName-admin.sharepoint.com -Credential $userCredential
   ```

5. 비즈니스용 Skype 온라인에 연결하려면 다음 명령어를 실행합니다. `WSMan NetworkDelayms`값 증가에 대한 경고는 처음 연결 시 보여지지만 무시해야 합니다.
     
   ```powershell
   Import-Module SkypeOnlineConnector
   $sfboSession = New-CsOnlineSession -Credential $credential
   Import-PSSession $sfboSession
   ```

6. 이 명령을 실행하여 Exchange 온라인에 연결합니다.
    
   ```powershell
   Connect-ExchangeOnline -Credential $credential -ShowProgress $true
   ```

   > [!Note]
   > 전 세계 외의 Microsoft 365 클라우드에 Exchange 온라인에 연결하려면 **-ExchangeEnvironmentName** 매개 변수를 사용하세요. 자세한 내용은 [연결-ExchangeOnline](https://docs.microsoft.com/powershell/module/exchange/powershell-v2-module/connect-exchangeonline?view=exchange-ps)를 참조하세요.

7. 다음 명령을 실행하여 Teams PowerShell에 연결하세요.
    
   ```powershell
   Import-Module MicrosoftTeams
   Connect-MicrosoftTeams -Credential $credential
   ```
  
   > [!Note]
   > 전 세계 이외의 Microsoft Teams 클라우드에 연결하려면 [연결-MicrosoftTeams](https://docs.microsoft.com/powershell/module/teams/connect-microsoftteams?view=teams-ps)를 참조하세요.

8. 다음 명령을 실행하여 보안 &amp; 준수 센터에 연결합니다.
    
   ```powershell
   $SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
   Import-PSSession $SccSession -Prefix cc
   ```

   > [!Note]
   > 전 세계 이외의 Microsoft 365 클라우드에 대한 보안 &amp; 준수 센터에 연결하려면 [PowerShell 보안 준수 센터에 연결](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell)을 참조하세요.

다음은 Graph 모듈에 Azure Active Directory PowerShell을 사용하는 경우 단일 블록의 모든 명령입니다. 도메인 호스트의 이름을 지정하고 한 번에 모두 실행합니다.
  
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

또는, Winsows PowerShell 모듈에 Microsoft Azure Active Directory 모듈을 사용할 때 단일 블록에 있는 모든 명령입니다. 도메인 호스트의 이름을 지정하고 한 번에 모두 실행합니다.
  
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

Windows PowerShell 창을 닫을 준비가 되면 이 명령을 실행하여 비즈니스용 Skype 온라인, SharePoint 온라인, 보안 &amp; 준수 센터 및 Teams에 활성 세션을 제거합니다.
  
```powershell
Remove-PSSession $sfboSession ; Remove-PSSession $SccSession ; Disconnect-SPOService ; Disconnect-MicrosoftTeams 
```

## <a name="connection-steps-when-using-multi-factor-authentication"></a>다단계 인증을 사용 하는 경우 연결 단계

단일 창에서 그래프 모듈에 Azure Active Directory PowerShell에 다단계 인증을 사용하는 Azure AD, SharePoint 온라인, 비즈니스용 Skype, Exchange 온라인 및 Teams에 연결하기 위해 사용하는 단일 블록의 모든 명령어입니다. 사용자 계정의 UPN(사용자 계정 이름) 이름과 도메인 호스트 이름을 지정하 고 한 번에 모두 실행합니다.

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

또는, Winsows PowerShell 모듈에 Microsoft Azure Active Directory 모듈을 사용할 때 단일 블록에 있는 모든 명령입니다.

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

보안 &amp; 준수 센터에 대한 자세한 내용은 다단계 인증을 사용하여 [다단계 인증을 사용하는 보안 및 준수 센터 PowerShell에 연결](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps)을 참조하세요.

## <a name="see-also"></a>참고 항목

- [PowerShell로 Microsoft 365에 연결](connect-to-office-365-powershell.md)
- [PowerShell로 SharePoint 온라인 관리](manage-sharepoint-online-with-office-365-powershell.md)
- [PowerShell로 Microsoft 365 사용자 계정, 라이선스 및 그룹 관리](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [Microsoft 365에서 Windows PowerShell을 사용하여 보고서 만들기](use-windows-powershell-to-create-reports-in-office-365.md)
