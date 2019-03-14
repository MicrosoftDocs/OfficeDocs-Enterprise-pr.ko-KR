---
title: 단일 Windows PowerShell 창에서 모든 Office 365 서비스에 연결 합니다.
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/28/2019
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- Ent_Office_Other
- O365ITProTrain
- httpsfix
ms.assetid: 53d3eef6-4a16-4fb9-903c-816d5d98d7e8
description: '요약: 단일 windows powershell 창에서 모든 Office 365 서비스에 windows powershell을 연결 합니다.'
ms.openlocfilehash: 38221a2c9b50aaeab217016336cf4d020abd706a
ms.sourcegitcommit: 2e5e2c65a1b785e229f1f7fd5b219f1b3de96f97
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/28/2019
ms.locfileid: "30339516"
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a>단일 Windows PowerShell 창에서 모든 Office 365 서비스에 연결 합니다.

 **요약:** 별도의 PowerShell 콘솔 창에서 서로 다른 office 365 서비스를 관리 하는 대신, 모든 office 365 서비스에 연결 하 여 단일 콘솔 창의 관리를 관리할 수 있습니다.
  
PowerShell을 사용 하 여 office 365을 관리 하는 경우 office 365 관리 센터, SharePoint online, Exchange online, 비즈니스용 Skype Online, 보안 &amp;준수 센터 별도의 Windows PowerShell 세션에서 5 가지 서로 다른 연결 방법을 사용 하는 경우 데스크톱은 다음과 같이 표시 될 수 있습니다.
  
![동시에 실행되는 5개의 Windows PowerShell 콘솔](media/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
서비스 간 관리를 위해 이러한 5 개의 창 간에 데이터를 교환할 수 없으므로 Office 365을 관리 하는 것이 최적이 아닙니다. 이 항목에서는 Office 365, 비즈니스용 Skype online, Exchange online, SharePoint online, 보안 &amp; 및 준수 센터를 관리할 수 있는 Windows PowerShell의 단일 인스턴스를 사용 하는 방법에 대해 설명 합니다.

>[!Note]
>이 문서에는 현재 Office 365 전 세계 (+ GCC) 클라우드에 연결 하는 명령만 포함 되어 있습니다. 추가 참고 사항에는 다른 Office 365 클라우드에 연결에 대 한 정보가 포함 된 문서 링크가 제공 됩니다.
>

## <a name="before-you-begin"></a>시작하기 전에

단일 Windows PowerShell 인스턴스에서 모든 Office 365을 관리 하려면 먼저 다음 필수 구성 요소를 고려 하십시오.
  
- 이러한 절차에 사용하는 Office 365회사 또는 학교 계정은 Office 365 관리자 역할의 구성원이어야 합니다. 자세한 내용은 [Office 365 관리자 역할 정보](https://go.microsoft.com/fwlink/p/?LinkId=532367)를 참조하세요. 이는 office 365 PowerShell에 대 한 요구 사항으로, 다른 모든 Office 365 서비스에 꼭 필요한 것은 아닙니다.
    
- 다음 Windows 버전을 사용할 수 있습니다.
    
  - Windows 10
    
  - Windows 8.1 또는 Windows 8
    
  - Windows Server 2019
    
  - Windows Server 2016
    
  - Windows Server 2012 R2 또는 Windows Server 2012
    
  - Windows 7 SP1(서비스 팩 1)*
    
  - Windows Server 2008 R2 SP1*
    
    \*Microsoft .net Framework 4.5를 설치 해야 합니다. *x* 를 누른 다음 windows management framework 3.0 또는 windows management framework 4.0 중 하나를 클릭 합니다. 자세한 내용은 [.net Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) 및 [windows management framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) 또는 [Windows management framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344)설치를 참조 하세요.
    
    비즈니스용 Skype Online 모듈 및 Office 365 모듈 중 하나에 대 한 요구 사항으로 인해 64 비트 버전의 Windows를 사용 해야 합니다.
    
- Azure AD, SharePoint Online 및 비즈니스용 Skype Online에 필요한 모듈을 설치 해야 합니다.
    
   - [Azure Active Directory V2](connect-to-office-365-powershell.md##connect-with-the-azure-active-directory-powershell-for-graph-module)
   - [SharePoint Online 관리 셸](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [비즈니스용 Skype Online, Windows PowerShell 모듈](https://go.microsoft.com/fwlink/p/?LinkId=532439)
    
-  비즈니스용 Skype online, Exchange Online 및 보안 &amp; 및 준수 센터에 대해 서명 된 스크립트를 실행 하도록 Windows PowerShell을 구성 해야 합니다. 이 작업을 수행 하려면 **관리자 권한으로 실행**을 선택 하 여 연 windows powershell 창에서 다음 명령을 실행 합니다.
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="connection-steps-when-using-a-password"></a>암호를 사용할 때의 연결 단계

단일 PowerShell 창에서 모든 서비스에 연결 하는 단계는 다음과 같습니다.
  
1. 관리자 권한으로 Windows PowerShell을 엽니다 ( **관리자 권한으로 실행**사용).
    
2. 이 명령을 실행 하 고 Office 365 회사 또는 학교 계정 자격 증명을 입력 합니다.
    
  ```
  $credential = Get-Credential
  ```

3. 이 명령을 실행 하 여 Graph 모듈에 대 한 azure active directory PowerShell을 사용 하 여 azure AD (Active directory)에 연결 합니다.
    
  ```
  Connect-AzureAD -Credential $credential
  ```
  
  또는 Windows PowerShell 모듈에 대 한 Microsoft Azure Active Directory 모듈을 사용 하는 경우에는이 명령을 실행 합니다.
      
  ```
  Connect-MsolService -Credential $credential
 ```

4. 다음 명령을 실행 하 여 SharePoint Online에 연결 합니다. _ \<domainhost>_ 를 도메인의 실제 값으로 바꿉니다. 예를 들어 "litwareinc.onmicrosoft.com"의 경우 _ \<domainhost>_ 값은 "litwareinc"입니다.
    
  ```
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. 다음 명령을 실행 하 여 비즈니스용 Skype Online에 연결 합니다. 처음 연결할 때 `WSMan NetworkDelayms` 값을 늘리는 경고는 예상 되며 무시 해야 합니다.
    
  ```
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. 다음 명령을 실행 하 여 Exchange Online에 연결 합니다.
    
  ```
  $exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $exchangeSession -DisableNameChecking
  ```

>[!Note]
>전 세계 이외의 Office 365 클라우드에서 exchange online에 연결 하려면 [exchange online PowerShell에 연결](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)을 참조 하세요.
>

7. 보안 &amp; 및 준수 센터에 연결 하려면 다음 명령을 실행 합니다.
    
  ```
  $SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $SccSession -Prefix cc
  ```

>[!Note]
>전 세계 이외의 office 365 &amp; 클라우드의 보안 및 준수 센터에 연결 하려면 [연결에 office 365 Security & 준수 센터 PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell)을 참조 하세요.
>

다음은 Graph 모듈에 대 한 Azure Active Directory PowerShell을 사용할 때 단일 블록에 있는 모든 명령입니다. 도메인 호스트의 이름을 지정 하 고 한 번에 모두 실행 합니다.
  
```
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-AzureAD -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $exchangeSession -DisableNameChecking
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
```

다음에는 Windows PowerShell 용 Microsoft Azure Active Directory 모듈 모듈을 사용할 때 단일 블록에 있는 모든 명령이 나와 있습니다. 도메인 호스트의 이름을 지정 하 고 한 번에 모두 실행 합니다.
  
```
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-MsolService -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $exchangeSession -DisableNameChecking
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
```

Windows PowerShell 창을 종료할 준비가 되 면 다음 명령을 실행 하 여 비즈니스용 Skype online, Exchange online, SharePoint online 및 보안 &amp; 및 준수 센터에 대 한 활성 세션을 제거 합니다.
  
```
Remove-PSSession $sfboSession ; Remove-PSSession $exchangeSession ; Remove-PSSession $SccSession ; Disconnect-SPOService
```

## <a name="connection-steps-when-using-multi-factor-authentication"></a>다단계 인증을 사용 하는 경우의 연결 단계

다음은 Graph 모듈에 대 한 azure Active Directory PowerShell을 사용 하 여 단일 창에서 azure AD, SharePoint Online 및 Buiness 비즈니스용 Skype에 연결 하는 모든 명령입니다. 사용자 계정의 UPN (사용자 계정 이름) 이름과 도메인 호스트 이름을 지정한 다음 한 번에 모두 실행 합니다.

````
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-AzureAD
#SharePoint Online
Connect-SPOService -Url https://$orgName-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
````

다음에는 Windows PowerShell 용 Microsoft Azure Active Directory 모듈 모듈을 사용할 때의 모든 명령이 나와 있습니다.

````
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-MsolService
#SharePoint Online
Connect-SPOService -Url https://$orgName-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
````

Exchange Online 및 보안 &amp; 및 준수 센터에 대해 multi-factor authentication을 사용 하 여 연결 하려면 다음 항목을 참조 하세요.

- [다단계 인증을 사용하여 Exchange Online PowerShell에 연결](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell)
- [다단계 인증을 사용 하 여 Office 365 보안 & 준수 센터 PowerShell에 연결](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps)
 
두 경우 모두 Exchange Online 원격 PowerShell 모듈의 개별 세션을 사용 하 여 연결 해야 합니다.


## <a name="see-also"></a>참고 항목

- [PowerShell Office 365에 연결](connect-to-office-365-powershell.md)
- [Office 365 PowerShell을 사용하여 SharePoint Online 관리](manage-sharepoint-online-with-office-365-powershell.md)
- [사용자 계정 및 Office 365 PowerShell을 사용 하 여 라이센스 관리](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [Office 365에서 Windows PowerShell을 사용하여 보고서 만들기](use-windows-powershell-to-create-reports-in-office-365.md)
