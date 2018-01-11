---
title: "단일 Windows PowerShell 창에서 모든 Office 365 서비스에 연결 합니다."
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
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
description: 'Summary: Connect Windows PowerShell to all Office 365 services in a single Windows PowerShell window.'
ms.openlocfilehash: 2dccfc73b016cbe97436c822432331ee30ba4bcd
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/11/2018
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a>단일 Windows PowerShell 창에서 모든 Office 365 서비스에 연결 합니다.

 **Summary:** Instead of managing different Office 365 services in separate PowerShell console windows, you can connect to all Office 365 services and manage them from single console window.
  
When you use PowerShell to manage Office 365, it is possible to have up to five different Windows PowerShell sessions open at the same time corresponding to Office 365 admin center, SharePoint Online, Exchange Online, Skype for Business Online, and the Security &amp; Compliance Center. With five different connection methods in separate Windows PowerShell sessions, your desktop could look like this:
  
![동시에 실행되는 5개의 Windows PowerShell 콘솔](images/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
This is not optimal for managing Office 365 because you can't exchange data among those five windows for cross-service management. This topic describes how to use a single instance of Windows PowerShell from which you can manage Office 365, Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center.
  
## <a name="before-you-begin"></a>시작하기 전에
<a name="BeforeYouBegin"> </a>

Before you can manage all of Office 365 from a single instance of Windows PowerShell, consider the following prerequisites:
  
- The Office 365 work or school account that you use for these procedures needs to be a member of an Office 365 admin role. For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367). This a requirement for Office 365 PowerShell, not necessarily for all other Office 365 services.
    
- 다음 Windows 버전을 사용할 수 있습니다.
    
  - Windows 10
    
  - Windows 8.1 또는 Windows 8
    
  - Windows Server 2016
    
  - Windows Server 2012 R2 또는 Windows Server 2012
    
  - Windows 7 SP1(서비스 팩 1)*
    
  - Windows Server 2008 R2 SP1*
    
    * You need to install the Microsoft .NET Framework 4.5. _x_ and then either the Windows Management Framework 3.0 or the Windows Management Framework 4.0. For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) and [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) or [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).
    
    You need to use a 64-bit version of Windows because of the requirements for the Skype for Business Online module and one of the Office 365 modules.
    
- You need to install the modules that are required for Office 365, SharePoint Online, and Skype for Business Online:
    
  - [Microsoft Online Service Sign-in Assistant for IT Professionals RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152)
    
  - [Windows Azure Active Directory Module for Windows PowerShell (64-bit version)](https://go.microsoft.com/fwlink/p/?linkid=236297)
    
  - [SharePoint Online Management Shell](https://go.microsoft.com/fwlink/p/?LinkId=255251)
    
  - [Skype for Business Online, Windows PowerShell Module](https://go.microsoft.com/fwlink/p/?LinkId=532439)
    
-  Windows PowerShell needs to be configured to run signed scripts for Skype for Business Online, Exchange Online, and the Security &amp; Compliance Center. To do this, run the following command in an elevated Windows PowerShell session (a Windows PowerShell window you open by selecting **Run as administrator**).
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="the-short-version-instructions-without-explanations"></a>간략 한 (설명 없이 지침)
<a name="ShortVersion"> </a>

이 섹션에서는 자세한 설명 없이 연결 단계를 나타냅니다. 질문이 있거나 추가 정보를 원할 경우 항목의 나머지 부분을 읽어볼 수 있습니다. 여기에 나오는 단계 변호는 항목의 나머지에 포함된 단계 번호가 매겨진 섹션에 해당합니다.
  
1. Open Windows PowerShell as an administrator (use **Run as administrator**).
    
2. Run this command, and enter your Office 365 work or school account credentials.
    
  ```
  $credential = Get-Credential
  ```

3. Run these commands to connect to Office 365.
    
  ```
  Import-Module MsOnline
  Connect-MsolService -Credential $credential
  ```

4. Run these commands to connect to SharePoint Online. Replace  _\<domainhost>_ with the actual value for your domain. For example, for `litwareinc.onmicrosoft.com`, the  _\<domainhost>_ value is `litwareinc`.
    
  ```
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. Run these commands to connect to Skype for Business Online. A warning about increasing the `WSMan NetworkDelayms` value is expected the first time you connect and should be ignored.
    
  ```
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. Run these commands to connect to Exchange Online.
    
  ```
  $exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $exchangeSession -DisableNameChecking
  ```

7. Run these commands to connect to the Security &amp; Compliance Center.
    
  ```
  $ccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication Basic -AllowRedirection
  Import-PSSession $ccSession -Prefix cc
  ```
> [!NOTE]
> The text prefix "cc" is added to  *all*  Security &amp; Compliance Center cmdlet names so you can run cmdlets that exist in both Exchange Online and the Security &amp; Compliance Center in the same Windows PowerShell session. For example, **Get-RoleGroup** becomes **Get-ccRoleGroup** in the Security &amp; Compliance Center.
  
Here are all the commands in a single block. Specify the name of your domain host, and then run them all at one time.
  
```
$domainHost="<domain host name, such as litware for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Import-Module MsOnline
Connect-MsolService -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$domainHost-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $exchangeSession -DisableNameChecking
$ccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication Basic -AllowRedirection
Import-PSSession $ccSession -Prefix cc
```

When you are ready to close down the Windows PowerShell window, run this command to remove the active sessions to Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center:
  
```
Remove-PSSession $sfboSession ; Remove-PSSession $exchangeSession ; Remove-PSSession $ccSession ; Disconnect-SPOService
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a>긴 버전 (명령에 대 한 세부 정보)
<a name="LongVersion"> </a>

### <a name="step-1-open-windows-powershell-as-an-administrator"></a>관리자 권한으로 Windows PowerShell 시작
<a name="Step1"> </a>

If you're running Windows 10, Windows 8, Windows 8.1, Windows Server 2016, Windows Server 2012 R2, or Windows Server 2012 R2, do this:
  
1. Use any of these methods to find the shortcut for **Windows PowerShell**:
    
  - On the Start screen, click an empty area, and type Windows PowerShell.
    
  - On the desktop or the Start screen, press the Windows key+Q. In the Search charm, type Windows PowerShell.
    
  - On the desktop or the Start screen, move your cursor to the upper-right corner, or swipe left from the right edge of the screen to show the charms. Select the Search charm, and enter Windows PowerShell.
    
2. In the results, right-click **Windows PowerShell**, and select **Run as administrator**.
    
3. If the **User Account Control** dialog box appears, select **Yes** to verify that you want to run Windows PowerShell under administrator credentials.
    
If you're running Windows 7 SP1 (or Windows Server 2008 R2 SP1), do this:
  
1. On the **Start** menu, select **All Programs** > **Accessories** > **Windows PowerShell**. Right-click **Windows PowerShell**, and then select **Run as administrator**.
    
2. If the **User Account Control** dialog box appears, select **Yes** to verify that you want to run Windows PowerShell under administrator credentials.
    
You must run Windows PowerShell as an administrator. If you don't, you're going to get an error message similar to this when you try to import one of the required modules.
  
```
The specified module 'Microsoft.Online.SharePoint.Online.PowerShell' was not loaded because no valid module file was found in any directory.
```

The only way to remedy the situation is to close Windows PowerShell and restart it as an administrator. Here's a quick and easy way to tell if you're running Windows PowerShell as an administrator: the prompt is  `PS C:\Windows\System32>`, not  `PS C:\Users\YourUserName>`.

  
### <a name="step-2-create-a-windows-powershell-credentials-object"></a>2단계: Windows PowerShell credentials 개체 만들기
<a name="Step2"> </a>

The credentials object provides an encrypted way to pass your user name and password to Windows PowerShell. To create a credentials object, run the following command in Windows PowerShell.
  
```
$credential = Get-Credential
```

> [!NOTE]
>  `$credential` is a variable that will store the credentials object. You don't have to name the variable `$credential`, but doing so makes it easier to remember which variable contains the credentials object. (And that's important, because we'll reuse this variable several times.) That will also make it easier for you to follow our examples, because this article will always use  `$credential` to represent the credentials object.
  
Windows PowerShell will then display a dialog box that looks like this.
  
![빈 자격 증명 요청 대화 상자](images/o365_powershell_empty_credentials_box.png)
  
Type your work or school account user name in the **User name** box, using the format _username@domainname_ (for example, kenmyer@litwareinc.onmicrosoft.com); type your password in the **Password** box; and then click **OK**:
  
![완료된 자격 증명 요청 대화 상자](images/o365_powershell_completed_credentials_box.png)
  
메모를 있는 그대로 자주 대/소문자를 볼 수 없습니다 모든 종류의 자격 증명 개체가 만들어졌는지 확인 합니다. (Windows PowerShell 일반적으로 알려줍니다 작업의 잘못 된 이동 하지만 항상 알 수 없는 경우 무엇 인가 오른쪽 때.) 자격 증명 개체가 만들어졌는지 확인 하려면 Windows PowerShell에서 다음 명령을 입력 하 고 Enter 키를 누릅니다.
  
```
$credential
```

그러면 화면에 다음과 비슷한 결과가 표시됩니다.
  
```
UserName                               Password
--------                               --------
kenmyer@litwareinc.onmicrosoft.com     System.Security.SecureString
```

One thing to keep in mind here is that the [Get-Credential](https://go.microsoft.com/fwlink/p/?LinkId=389618) cmdlet only creates the credentials object; it does not authenticate you or otherwise verify that the user name and password you supplied are correct. For example, suppose you mistyped the user name as kenmyer@litwareinc.onmicrosoft.com. If you do that, **Get-Credential** will create a credentials object using that user name, and without checking to see if that is actually a valid user name. You won't know whether you have created a truly valid credentials object until you actually use that object to try to connect to the Office 365 services.
  
### <a name="step-3-connect-to-office-365"></a>3단계: Office 365에 연결
<a name="Step3"> </a>

We'll start by connecting to Office 365 itself. 
  
The first thing we need to do here is import the Office 365 module (the Microsoft Azure Active Directory Module for Windows PowerShell). To do that, run this command in Windows PowerShell.
  
```
Import-Module MsOnline
```

모듈을 가져왔는지 확인하려면 다음 명령을 실행합니다.
  
```
Get-Module
```

Somewhere in the list of modules that are returned by this command you should see something that looks like this:  `Manifest 1.0 MSOnline {Add-MsolForeignGroupToRole, Add-MsolG...}`.
  
If you see  `MSOnline` listed, that means that everything went according to plan.
  
With the credentials object created (see [Step 2: Create a Windows PowerShell credentials object](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md#Step2)) and with the  `MsOnline` module loaded, we can now connect to Office 365 by using the [Connect-MsolService](https://go.microsoft.com/fwlink/p/?LinkId=532375) cmdlet and the following command.
  
```
Connect-MsolService -Credential $credential
```

Notice that all you have to provide is the credentials object ( `$credential`). Based on those credentials, Office 365 will automatically connect you to the correct domain. You do not have to specify your domain name when running **Connect-MsolService**.
  
To verify that you really  *are*  connected to Office 365, run this command.
  
```
Get-MsolDomain
```

그러면 다음과 비슷한 결과가 반환되어야 합니다.
  
```
Name                         Status          Authentication
----                         ------          --------------
litwareinc.onmicrosoft.com   Verified        Managed
```

### <a name="step-4-connect-to-sharepoint-online"></a>4단계: SharePoint Online에 연결
<a name="Step4"> </a>

다음 명령 사용 하 여 SharePoint Online 모듈을 가져옵니다.
  
```
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
```

_DisableNameChecking_ 스위치는이 경고를 표시 하지 않습니다.
  
```
WARNING: The names of some imported commands from the module 'Microsoft.Online.SharePoint.PowerShell' include unapproved verbs that might make them less discoverable. To find the commands with unapproved verbs, run the Import-Module command again with the Verbose parameter. For a list of approved verbs, type Get-Verb.
```

SharePoint online에 연결 하기 위해 두 가지 정보를 제공 해야: 사용자의 자격 증명 및 SharePoint Online 관리 사이트의 URL입니다. 자격 증명 부분은 쉽습니다: 변수에 이미 저장 했을 때 `$credential` (참조 [2 단계: Windows PowerShell 자격 증명 개체를 만들](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md#Step2)). 관리 사이트의 URL, 것 처럼 임을 충분히도 결정을 합니다. Office 365 도메인 이름을 인스턴트 메시징 세션을 `litwareinc.onmicrosoft.com`합니다.
  
관리 사이트 URL을 확인하려면 다음 작업을 수행합니다.
  
1. Start by using the prefix  `https://`.
    
2. Add the domain host portion of your domain name. For example, for  `litwareinc.onmicrosoft.com`, the domain host name is  `litwareinc`. For  `contoso.onmicrosoft.com`, the domain host name is  `contoso`.
    
3. Add a hyphen (-) followed by  `admin.sharepoint.com`.
    
위의 명령이 반환하는 결과는 다음과 같습니다.
  
 `https://` + `litwareinc` + `-admin.sharepoint.com` = `https://litwareinc-admin.sharepoint.com`
  
After you've constructed the URL, you can then use that URL and your credentials object to connect to SharePoint Online. Just call the [Connect-SPOService](https://go.microsoft.com/fwlink/p/?LinkId=532436) cmdlet, using a command similar to this one.
  
```
Connect-SPOService -Url https://litwareinc-admin.sharepoint.com -credential $credential
```

To verify that the connection has been made, run the following command in Windows PowerShell.
  
```
Get-SPOSite
```

You should get a list of all your SharePoint Online sites. Here is an example:
  
```
Url                                       Owner          Storage Quota
---                                       -----          -------------
http://litwareinc-public.sharepoint.com/                 1000
https://litwareinc.sharepoint.com/                       1000
https://litwareinc.sharepoint.com/search                 1000
```

Your Office 365 commands (the ones described in [Step 3: Connect to Office 365](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md#Step3)) will still work. (Try running **Get-MsolUser**, and see for yourself.) That means that you can now manage both Office 365 and SharePoint Online from the same instance of Windows PowerShell.
  
### <a name="step-5-connect-to-skype-for-business-online"></a>5단계: 온라인 비즈니스를 위한 Skype에 연결
<a name="Step5"> </a>

Connecting to Skype for Business Online (and to Exchange Online or the Security &amp; Compliance Center) is different than connecting to Office 365 or to SharePoint Online. That's because the Skype for Business Online and Exchange Online cmdlets don't get installed on your computer like the Office 365 and the SharePoint Online cmdlets do. Instead, each time you sign in, the appropriate cmdlets are temporarily copied to your computer. When you sign off, those cmdlets are then removed from your computer.
  
In order to connect to Skype for Business Online, you need to import the Skype for Business Online module. To do that, run this command.
  
```
Import-Module SkypeOnlineConnector
```

이를 처음으로 수행하면 다음 경고 메시지가 표시될 수 있습니다. 이 경고 메시지는 무시해도 안전합니다.
  
```
WARNING: WSMan NetworkDelayms has been set to 30000 milliseconds. The previous value was 5000 milliseconds.
WARNING: To improve the performance of the Lync Online Connector, it is recommended that the network delay be set to
30000 milliseconds (30 seconds). However, you can use Set-WinRMNetworkDelayMS to change the network delay to any
integer value.
```

모듈을 가져온 후 이 명령을 실행합니다.
  
```
$sfboSession = New-CsOnlineSession -Credential $credential
```

We have created a remote PowerShell session. In this case, that means that we've connected to an instance of Windows PowerShell running on one of the Office 365 servers. 
  
Although we've made a connection to Office 365, we haven't downloaded the scripts, cmdlets, and other items needed to manage Skype for Business Online. To do that, we have to run this command.
  
```
Import-PSSession $sfboSession
```

When you import the Windows PowerShell session, you should see a progress bar similar to the following, a progress bar that reports on all the Skype for Business Online cmdlets being imported to your computer.
  
![Lync Online 진행률 표시줄](images/o365_powershell_lync_progress_bar.png)
  
진행률 표시줄이 사라지면 다음과 비슷한 출력이 표시됩니다.
  
```
ModuleType Version    Name               ExportedCommands
---------- -------    ----               ----------------
Script     1.0        tmp_swc5mp4v.1ck  {Copy-CsVoicePolicy, Disabl...
```

### <a name="step-6-connect-to-exchange-online"></a>6단계: Exchange Online에 연결
<a name="Step6"> </a>

Exchange Online을 사용한 원격 Windows PowerShell 세션을 만들고이 명령을 실행 합니다.
  
```
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
```

> [!NOTE]
> Why is the command for connecting to Exchange Online more complicated than the command to connect to Skype for Business Online? Technically, it's not: both commands do the exact same thing. However, the Skype for Business Online team created its own cmdlet— **New-CsOnlineSession** —that hides some of the parameters (like _Authentication_ and _AllowRedirection_) that are used when connecting to Exchange Online. Instead of requiring you to type that information yourself, the  _Authentication_ and _AllowRedirection_ parameters are effectively built in to the **New-CsOnlineSession** cmdlet. You have to type those parameters when connecting to Exchange Online because Exchange Online uses the standard [New-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389621) cmdlet to connect to Office 365. The disadvantage is that you have a little more typing to do. The advantage is that you don't have to download and install an Exchange Online module.
  
All you have to do now is import this remote session, just like we did with Skype for Business Online.
  
```
Import-PSSession $exchangeSession -DisableNameChecking
```

그러면 화면에 다음과 같은 내용이 표시됩니다.
  
```
ModuleType Version  Name             ExportedCommands
---------- -------  ----             ----------------
Script     1.0      tmp_nweiqjvl.geu {Add-AvailabilityAddressSpace...
```

이제 다음 명령을 실행합니다.
  
```
Get-AcceptedDomain
```

반환, 구성 된 전자 메일 주소에 대 한 Exchange Online Office 365 도메인에 대 한 정보를 표시 됩니다.
  
```
Name            DomainName          DomainType      Default
----            ----------          ----------      -------
litwareinc.com  litwareinc.com      Authoritative   True
```

### <a name="step-7-connect-to-the-security-amp-compliance-center"></a>Step 7: Connect to the Security &amp; Compliance Center
<a name="Step7"> </a>

The Security &amp; Compliance Center is a service in Office 365 that lets you to manage compliance features from one location. For more information, see [Office 365 compliance center](http://technet.microsoft.com/library/fde83656-f136-448d-b250-6fa17b503e4e.aspx).
  
The connection instructions for the Security &amp; Compliance Center are very similar to those for Exchange Online, but with an added twist, which you'll see in a moment.
  
Run this command, which creates a remote PowerShell session with the Security &amp; Compliance Center.
  
```
$ccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication Basic -AllowRedirection
```

그런 후 다음 명령을 실행합니다.
  
```
Import-PSSession $ccSession -Prefix cc
```

Again, this command is very similar to the command for Exchange Online. The  _DisableNameChecking_ switch isn't required because there are no unapproved verbs in the Security &amp; Compliance Center. But what about that additional `-Prefix cc` parameter and value? That's the added twist we told you about.
  
Exchange Online and the Security &amp; Compliance Center share some cmdlets that have exactly the same names and provide the same functionality. **Get-RoleGroup** is an example.
  
So what happens if you try to import two sessions that contain cmdlets with the same name? They collide. You'll get a big yellow warning message that says,  `WARNING: Proxy creation has been skipped for the following command:` followed by the list of conflicting cmdlets that couldn't be imported. The end result? You can run **Get-RoleGroup** in Exchange Online because you connected there first, but you can't run **Get-RoleGroup** in the Security &amp; Compliance Center because you connected there last and the conflicting cmdlets refused to import.
  
The easiest way to deal with this problem is to add an arbitrary text prefix to the imported Security &amp; Compliance Center cmdlets. We did that using the  _Prefix_ parameter with the value "cc" on the **Import-PSSession** cmdlet. What did that do for us? It eliminated the conflicts by (slightly) changing the Security &amp; Compliance Center cmdlet names for this session. All of the imported Security &amp; Compliance Center cmdlets now start with "cc" in the noun part of the cmdlet name (to the right of the "-"). For example, the contentious **Get-RoleGroup** cmdlet becomes **Get-ccRoleGroup** for the Security &amp; Compliance Center so it doesn't conflict with **Get-RoleGroup** for Exchange Online.
  
The downside?  *All*  Security &amp; Compliance Center cmdlet names receive the "cc" prefix—even unique cmdlets that don't need it. For example, **Get-ComplianceSearch** becomes **Get-ccComplianceSearch** even though there is no such cmdlet in Exchange Online. It's a bit of a pain, but not too bad when you consider the benefits of managing all Office 365 services in a single Windows PowerShell session. Just remember to add "cc" to the cmdlet names for all procedures in the Security &amp; Compliance Center.
  
그런 다음 모든 작업을 완료하면 화면에 다음과 유사한 메시지가 표시됩니다.
  
```
ModuleType Version  Name             ExportedCommands
---------- -------  ----             ----------------
Script     1.0      tmp_xbbx5exr.ehm {Add-ccRoleGroupMember, Get-ccAdminAuditLogConfig, Get-ccA...
```

Now you are free to manage all Office 365 services in a single Windows PowerShell session.
  
### <a name="step-8-gracefully-end-your-powershell-sessions"></a>8단계: PowerShell 세션을 정상적으로 종료
<a name="Step8"> </a>

Windows PowerShell 창을 닫으면 하는 경우 다음 15 분 정도 대 한 비즈니스 온라인 원격 연결에 대 한 사용자 Skype 활성 상태로 유지 됩니다. 모든 한 명 또는 하나의 도메인 열기를 가질 수 있다는 동시 연결 수를 제한 하는 비즈니스 온라인 용 Skype, 때문에 문제가 발생할 수 있는 합니다. 온라인 비즈니스에 대 한 Skype와 개별 관리자, 최대 세 열린 한번에 연결 하 고 도메인을 최대 9 개의 열린 연결을 가질 수 있습니다. 온라인 비즈니스에 대 한 Skype에 로그인 하 고 다음 세션을 제대로 닫지 않고를 종료 하는 경우 다음 15 분 정도 대 한 해당 세션 계속 열려 있습니다. 결과적으로,는 연결이 하나 더 적은 사용자나 도메인에서 다른 관리자에 게 사용할 수 있습니다.
  
Instead, let's close the remote sessions for Skype for Business Online, Exchange Online, and the Security &amp; Compliance Center gracefully. Before we do that, run this command.
  
```
Get-PSSession
```

The [Get-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=532437) cmdlet should show you that you have at least three remote sessions open, one for Skype for Business Online, one for Exchange Online and one for the Security &amp; Compliance Center (it's possible you could have more than three remote sessions running, depending on whether you've used this instance of Windows PowerShell to connect to something else besides the Office 365 services). You should see something similar to the following.
  
```
Id Name     ComputerName     State   ConfigurationName    Availability
-- ----     ------------     -----   -----------------    ------------
 1 Session1 webdir0a.onl...  Opened  Microsoft.PowerShell    Available
 2 Session2 outlook.offi...  Opened  Microsoft.Exchange      Available
 3 Session3 ps.complianc...  Opened  Microsoft.Exchange      Available
```

To close these three sessions, run these commands one at a time. The first command closes the Skype for Business Online session, the second closes the Exchange Online session, and the third closes the Security &amp; Compliance Center session.
  
```
Remove-PSSession $sfboSession
Remove-PSSession $exchangeSession
Remove-PSSession $ccSession
```

이제 **Get-pssession** cmdlet을 실행 하는 경우 표시 되어야 nothing 전혀 (않은 경우 다른 원격 세션이 작동 및 실행 중).
  
![원격 세션이 없는 Windows PowerShell 콘솔](images/o365_powershell_no_remote_sessions.png)
  
> [!NOTE]
> If you'd prefer to close all your remote sessions at the same time, you can use this command: >  `Get-PSSession | Remove-PSSession`
  
If you now try running a cmdlet from any of these closed sessions (for example, **Get-CsMeetingConfiguration** in Skype for Business Online) you'll get an error message that's similar to this one.
  
```
Get-CsMeetingConfiguration : The term 'Get-CsMeetingConfiguration' is not recognized as the name of a cmdlet, function, script file, or operable program. Check the spelling of the name, or if a path was included, verify that the path is correct and try again.
```

We get that error message because the cmdlets for Skype for Business Online, Exchange Online, and the Security &amp; Compliance Center were deleted when we closed the remote sessions.
  
SharePoint Online 세션을 닫으려면 다음이 명령을 입력 합니다.
  
```
Disconnect-SPOService
```

이제 **Get-sposite** cmdlet을 실행 하려고 하는 경우 다음과 같은 오류 메시지가 가져옵니다.
  
```
get-sposite : No connection available. Use Connect-SPOService before running this CmdLet.
```

더이상 SharePoint Online에 연결 되어있지 않으므로 사이트 정보를 검색할 수 없습니다.
  
Office 365에 대 한 연결을 것 처럼 **Connect-msolservice** cmdlet을 없지만 방법이 해당 **연결 끊기 MsolService** cmdlet 없습니다. 따라서 Office 365에 대 한 Windows PowerShell 창을 닫습니다. 그럼에도 불구 하 고 것도이 작업을 수행 하는 것이 좋습니다 제대로 제거할 수 있도록 SharePoint에서 온라인으로 Skype 비즈니스 Online, Exchange Online 및 보안에 대 한 마지막 &amp; 준수 센터입니다.
  
## <a name="new-to-office-365"></a>Office 365의 새로운 기능
<a name="LongVersion"> </a>

||
|:-----|
|![LinkedIn 학습에 대 한 짧은 아이콘](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **새로 만들기를 Office 365?**         [Office 365 관리자 및 IT 전문가](https://support.office.com/article/Office-365-admin-and-IT-pro-courses-68cc9b95-0bdc-491e-a81f-ee70b3ec63c5), LinkedIn 학습에 의해 제공자에 대 한 무료 비디오 코스를 검색 합니다. |
   
## <a name="see-also"></a>참고 항목

#### 

[Office 365 PowerShell 사용한 Office 365 관리](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell 시작](getting-started-with-office-365-powershell.md)
  
[Office 365 PowerShell을 사용하여 SharePoint Online 관리](manage-sharepoint-online-with-office-365-powershell.md)
  
[사용자 계정 및 Office 365 PowerShell을 사용 하 여 라이센스 관리](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Office 365에서 Windows PowerShell을 사용하여 보고서 만들기](use-windows-powershell-to-create-reports-in-office-365.md)

