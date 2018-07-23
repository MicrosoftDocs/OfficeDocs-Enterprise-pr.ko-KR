---
title: 단일 Windows PowerShell 창에서 모든 Office 365 서비스에 연결 합니다.
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 06/11/2018
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
description: '요약: 단일 Windows PowerShell 창에서 모든 Office 365 서비스에 Windows PowerShell에 연결 합니다.'
ms.openlocfilehash: bf5e81012eaa3e7e200f9b1984b3d3fe01c30799
ms.sourcegitcommit: c3869a332512dd1cc25cd5a92a340050f1da0418
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/20/2018
ms.locfileid: "20720374"
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a>단일 Windows PowerShell 창에서 모든 Office 365 서비스에 연결 합니다.

 **요약:** 별도 PowerShell 콘솔 창에서 다른 Office 365 서비스를 관리 하는 대신 모든 Office 365 서비스에 연결할 수 있으며 해당 단일 콘솔 창에서 관리할 수 있습니다.
  
PowerShell을 사용 하 여 Office 365를 관리 하는 Office 365 관리 센터, SharePoint Online, Exchange Online, 비즈니스 온라인 용 Skype 및 보안 &amp;준수 센터입니다. 별도 Windows PowerShell 세션에 다섯 개의 서로 다른 연결 메서드를 통해 사용자의 데스크톱은 다음과 같습니다.
  
![동시에 실행되는 5개의 Windows PowerShell 콘솔](images/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
이 교차 서비스 관리에 대 한 이러한 5 개의 창 사이에서 데이터를 교환할 수 없습니다 때문에 Office 365를 관리 하기 위한 최적의있지 않습니다. 이 항목에서는 Office 365, 비즈니스 Online, Exchange Online, SharePoint Online 용 Skype 및 보안을 관리할 수 있는 Windows PowerShell의 단일 인스턴스를 사용 하는 방법을 설명 &amp; 준수 센터입니다.

## <a name="before-you-begin"></a>시작하기 전에
<a name="BeforeYouBegin"> </a>

모든 Office 365에서 Windows PowerShell의 단일 인스턴스를 관리할 수 있습니다를 하기 전에 다음 필수 구성 요소를 고려:
  
- Office 365 작동 또는 학교 계정을 사용 하는 이러한 절차에 대 한 요구를 Office 365 관리자 역할의 구성원 이어야 합니다. 자세한 내용은 [Office 365에 대 한 관리자 역할](https://go.microsoft.com/fwlink/p/?LinkId=532367)을 참조 하십시오. 이 Office 365 PowerShell에 대 한, 다른 모든 Office 365 서비스에 대 한 반드시 필요 합니다.
    
- 다음 Windows 버전을 사용할 수 있습니다.
    
  - Windows 10
    
  - Windows 8.1 또는 Windows 8
    
  - Windows Server 2016
    
  - Windows Server 2012 R2 또는 Windows Server 2012
    
  - Windows 7 SP1(서비스 팩 1)*
    
  - Windows Server 2008 R2 SP1*
    
    \*Microsoft.NET Framework 4.5를 설치 해야 합니다. *x* 하 고 다음 중 하나는 Windows Management Framework 3.0 또는 Windows 관리 프레임 워크 4.0 합니다. 자세한 내용은 [.NET Framework를 설치](https://go.microsoft.com/fwlink/p/?LinkId=257868) 하 고 [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) 또는 [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344)을 참조 하십시오.
    
    비즈니스 온라인 모듈 및 Office 365 모듈 중 하나는 Skype에 대 한 요구 사항으로 인해 64 비트 버전의 Windows 사용 해야 합니다.
    
- Azure AD에 필요한 사용 되는 모듈을 설치 해야 SharePoint Online 및 비즈니스 온라인 용 Skype:
    
   - [Azure Active Directory V2](connect-to-office-365-powershell.md##connect-with-the-azure-active-directory-powershell-for-graph-module)
   - [SharePoint Online 관리 셸](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [온라인으로 비즈니스 Windows PowerShell 모듈에 대 한 Skype](https://go.microsoft.com/fwlink/p/?LinkId=532439)
    
-  Windows PowerShell 스크립트를 실행 하려면 서명 된 Skype에 대 한 비즈니스 Online, Exchange Online 및 보안에 대 한 구성 해야하는 &amp; 준수 센터입니다. 이 작업을 수행 하려면 관리자 권한으로 Windows PowerShell 세션에서 다음 명령을 실행 ( **관리자 권한으로 실행**을 선택 하 여 열면 Windows PowerShell 창)입니다.
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="connection-steps-when-using-a-password"></a>암호를 사용 하는 경우에 연결 단계
<a name="ConnStepsPassword"> </a>

단일 PowerShell 창에서 모든 서비스에 연결 하는 단계는 다음과 같습니다.
  
1. 관리자 권한 ( **관리자 권한으로 실행**하는 사용)으로 Windows PowerShell을 엽니다.
    
2. 이 명령을 실행 하 고 Office 365 작업 시간을 입력 하거나 계정 자격 증명을 학교 합니다.
    
  ```
  $credential = Get-Credential
  ```

3. 연결을 Azure Active Directory (AD) 그래프 모듈에 대 한 Active Directory Azure PowerShell을 사용 하 여이 명령을 실행 합니다.
    
  ```
   Connect-AzureAD -Credential $credential
  ```
  
  또는 Microsoft Azure Active Directory 모듈에 대 한 Windows PowerShell 모듈을 사용 하는 경우에이 명령을 실행 합니다.
      
  ```
   Connect-MsolService -Credential $credential
 ```

4. SharePoint Online에 연결 하려면 다음이 명령을 실행 합니다. 교체 _ \<domainhost >_ 도메인에 대 한 실제 값입니다. 예: "litwareinc.onmicrosoft.com"는 _ \<domainhost >_ 값은 "litwareinc"입니다.
    
  ```
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. 비즈니스 온라인 용 Skype 연결에 다음이 명령을 실행 합니다. 증가 하는 방법에 대 한 경고는 `WSMan NetworkDelayms` 값 처음으로 예상 되는 연결 하 고 무시 해야 합니다.
    
  ```
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. Exchange Online에 연결 하려면 다음이 명령을 실행 합니다.
    
  ```
  $exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $exchangeSession
  ```

7. 보안에 연결 하려면 다음이 명령을 실행 &amp; 준수 센터입니다.
    
  ```
  $SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $SccSession -Prefix cc
  ```

다음 그래프 모듈에 대 한 Active Directory Azure PowerShell을 사용 하는 경우 단일 블록에 있는 모든 명령을입니다. 사용자 도메인 호스트의 이름을 지정 하 고 모두 한번에 실행 합니다.
  
```
$domainHost="<domain host name, such as litware for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-AzureAD -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$domainHost-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $exchangeSession
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
```

또는 다음은 모든 명령 단일 블록의 Microsoft Azure Active Directory 모듈에 대 한 Windows PowerShell 모듈을 사용 하는 경우입니다. 사용자 도메인 호스트의 이름을 지정 하 고 모두 한번에 실행 합니다.
  
```
$domainHost="<domain host name, such as litware for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-MsolService -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$domainHost-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $exchangeSession
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
```

비즈니스 Online, Exchange Online, SharePoint Online 및 보안에 대 한 활성 세션 Skype 제거 하려면이 명령을 실행 하는 Windows PowerShell 창을 닫아야 준비가 되 면 &amp; 준수 센터:
  
```
Remove-PSSession $sfboSession ; Remove-PSSession $exchangeSession ; Remove-PSSession $SccSession ; Disconnect-SPOService
```

## <a name="connection-steps-when-using-multi-factor-authentication"></a>연결 단계 다단계 인증을 사용 하는 경우
<a name="ConnStepsMFA"> </a>

Azure AD에 연결 하는 단일 블록에서 모든 명령을 사항은 SharePoint Online 및 Buiness 다단계 인증을 사용 하 여 단일 창에서에 대 한 Skype 합니다. 전역 관리자 계정의 사용자 계정 이름 (UPN) 이름 및 도메인 호스트 이름을 지정 하 고 모두 한번에 실행 합니다.

````
$acctName="<UPN of a global administrator account>"
$domainHost="<domain host name, such as litware for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-AzureAD
#SharePoint Online
Connect-SPOService -Url https://$domainHost-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
````

또는 Microsoft Azure Active Directory 모듈에 대 한 Windows PowerShell 모듈을 사용 하는 경우 모든 명령을 같습니다.

````
$acctName="<UPN of a global administrator account>"
$domainHost="<domain host name, such as litware for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-MsolService
#SharePoint Online
Connect-SPOService -Url https://$domainHost-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
````

Exchange Online 및 보안에 대 한 &amp; 준수 센터 다단계 인증을 사용 하 여 연결 하려면 다음 항목을 참조 하십시오.

- [다단계 인증을 사용하여 Exchange Online PowerShell에 연결](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell)
- [Office 365 보안 및 규정 준수 센터 PowerShell 다단계 인증을 사용 하 여 연결](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps)
 
두 경우 모두 사항에 유의 Exchange Online 원격 PowerShell 모듈의 별도 세션을 사용 하 여 연결 해야 합니다.


## <a name="new-to-office-365"></a>Office 365의 새로운 기능

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a>See also

- [PowerShell Office 365에 연결](connect-to-office-365-powershell.md)
- [Office 365 PowerShell을 사용하여 SharePoint Online 관리](manage-sharepoint-online-with-office-365-powershell.md)
- [사용자 계정 및 Office 365 PowerShell을 사용 하 여 라이센스 관리](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [Office 365에서 Windows PowerShell을 사용하여 보고서 만들기](use-windows-powershell-to-create-reports-in-office-365.md)
