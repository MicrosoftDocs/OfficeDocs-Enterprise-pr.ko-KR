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
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a><span data-ttu-id="3f591-103">단일 Windows PowerShell 창에서 모든 Office 365 서비스에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f591-103">Connect to all Office 365 services in a single Windows PowerShell window</span></span>

 <span data-ttu-id="3f591-104">**Summary:** Instead of managing different Office 365 services in separate PowerShell console windows, you can connect to all Office 365 services and manage them from single console window.</span><span class="sxs-lookup"><span data-stu-id="3f591-104">**Summary:** Instead of managing different Office 365 services in separate PowerShell console windows, you can connect to all Office 365 services and manage them from single console window.</span></span>
  
<span data-ttu-id="3f591-p101">When you use PowerShell to manage Office 365, it is possible to have up to five different Windows PowerShell sessions open at the same time corresponding to Office 365 admin center, SharePoint Online, Exchange Online, Skype for Business Online, and the Security &amp; Compliance Center. With five different connection methods in separate Windows PowerShell sessions, your desktop could look like this:</span><span class="sxs-lookup"><span data-stu-id="3f591-p101">When you use PowerShell to manage Office 365, it is possible to have up to five different Windows PowerShell sessions open at the same time corresponding to Office 365 admin center, SharePoint Online, Exchange Online, Skype for Business Online, and the Security &amp; Compliance Center. With five different connection methods in separate Windows PowerShell sessions, your desktop could look like this:</span></span>
  
![동시에 실행되는 5개의 Windows PowerShell 콘솔](images/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
<span data-ttu-id="3f591-p102">This is not optimal for managing Office 365 because you can't exchange data among those five windows for cross-service management. This topic describes how to use a single instance of Windows PowerShell from which you can manage Office 365, Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center.</span><span class="sxs-lookup"><span data-stu-id="3f591-p102">This is not optimal for managing Office 365 because you can't exchange data among those five windows for cross-service management. This topic describes how to use a single instance of Windows PowerShell from which you can manage Office 365, Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="3f591-110">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="3f591-110">Before you begin</span></span>
<span data-ttu-id="3f591-111"><a name="BeforeYouBegin"> </a></span><span class="sxs-lookup"><span data-stu-id="3f591-111"></span></span>

<span data-ttu-id="3f591-112">Before you can manage all of Office 365 from a single instance of Windows PowerShell, consider the following prerequisites:</span><span class="sxs-lookup"><span data-stu-id="3f591-112">Before you can manage all of Office 365 from a single instance of Windows PowerShell, consider the following prerequisites:</span></span>
  
- <span data-ttu-id="3f591-p103">The Office 365 work or school account that you use for these procedures needs to be a member of an Office 365 admin role. For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367). This a requirement for Office 365 PowerShell, not necessarily for all other Office 365 services.</span><span class="sxs-lookup"><span data-stu-id="3f591-p103">The Office 365 work or school account that you use for these procedures needs to be a member of an Office 365 admin role. For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367). This a requirement for Office 365 PowerShell, not necessarily for all other Office 365 services.</span></span>
    
- <span data-ttu-id="3f591-116">다음 Windows 버전을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f591-116">You can use the following 64-bit versions of Windows:</span></span>
    
  - <span data-ttu-id="3f591-117">Windows 10</span><span class="sxs-lookup"><span data-stu-id="3f591-117">Windows 10</span></span>
    
  - <span data-ttu-id="3f591-118">Windows 8.1 또는 Windows 8</span><span class="sxs-lookup"><span data-stu-id="3f591-118">Windows 8.1 or Windows 8</span></span>
    
  - <span data-ttu-id="3f591-119">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="3f591-119">Windows Server 2016</span></span>
    
  - <span data-ttu-id="3f591-120">Windows Server 2012 R2 또는 Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="3f591-120">Windows Server 2012 R2 or Windows Server 2012</span></span>
    
  - <span data-ttu-id="3f591-121">Windows 7 SP1(서비스 팩 1)*</span><span class="sxs-lookup"><span data-stu-id="3f591-121">Windows 7 Service Pack 1 (SP1)*</span></span>
    
  - <span data-ttu-id="3f591-122">Windows Server 2008 R2 SP1*</span><span class="sxs-lookup"><span data-stu-id="3f591-122">Windows Server 2008 R2 SP1*</span></span>
    
    * <span data-ttu-id="3f591-p104">You need to install the Microsoft .NET Framework 4.5. _x_ and then either the Windows Management Framework 3.0 or the Windows Management Framework 4.0. For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) and [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) or [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span><span class="sxs-lookup"><span data-stu-id="3f591-p104">You need to install the Microsoft .NET Framework 4.5. _x_ and then either the Windows Management Framework 3.0 or the Windows Management Framework 4.0. For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) and [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) or [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span></span>
    
    <span data-ttu-id="3f591-126">You need to use a 64-bit version of Windows because of the requirements for the Skype for Business Online module and one of the Office 365 modules.</span><span class="sxs-lookup"><span data-stu-id="3f591-126">You need to use a 64-bit version of Windows because of the requirements for the Skype for Business Online module and one of the Office 365 modules.</span></span>
    
- <span data-ttu-id="3f591-127">You need to install the modules that are required for Office 365, SharePoint Online, and Skype for Business Online:</span><span class="sxs-lookup"><span data-stu-id="3f591-127">You need to install the modules that are required for Office 365, SharePoint Online, and Skype for Business Online:</span></span>
    
  - [<span data-ttu-id="3f591-128">Microsoft Online Service Sign-in Assistant for IT Professionals RTW</span><span class="sxs-lookup"><span data-stu-id="3f591-128">Microsoft Online Service Sign-in Assistant for IT Professionals RTW</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=286152)
    
  - [<span data-ttu-id="3f591-129">Windows Azure Active Directory Module for Windows PowerShell (64-bit version)</span><span class="sxs-lookup"><span data-stu-id="3f591-129">Windows Azure Active Directory Module for Windows PowerShell (64-bit version)</span></span>](https://go.microsoft.com/fwlink/p/?linkid=236297)
    
  - [<span data-ttu-id="3f591-130">SharePoint Online Management Shell</span><span class="sxs-lookup"><span data-stu-id="3f591-130">SharePoint Online Management Shell</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=255251)
    
  - [<span data-ttu-id="3f591-131">Skype for Business Online, Windows PowerShell Module</span><span class="sxs-lookup"><span data-stu-id="3f591-131">Skype for Business Online, Windows PowerShell Module</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532439)
    
-  <span data-ttu-id="3f591-p105">Windows PowerShell needs to be configured to run signed scripts for Skype for Business Online, Exchange Online, and the Security &amp; Compliance Center. To do this, run the following command in an elevated Windows PowerShell session (a Windows PowerShell window you open by selecting **Run as administrator**).</span><span class="sxs-lookup"><span data-stu-id="3f591-p105">Windows PowerShell needs to be configured to run signed scripts for Skype for Business Online, Exchange Online, and the Security &amp; Compliance Center. To do this, run the following command in an elevated Windows PowerShell session (a Windows PowerShell window you open by selecting **Run as administrator**).</span></span>
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="the-short-version-instructions-without-explanations"></a><span data-ttu-id="3f591-134">간략 한 (설명 없이 지침)</span><span class="sxs-lookup"><span data-stu-id="3f591-134">The short version (instructions without explanations)</span></span>
<span data-ttu-id="3f591-135"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="3f591-135"></span></span>

<span data-ttu-id="3f591-p106">이 섹션에서는 자세한 설명 없이 연결 단계를 나타냅니다. 질문이 있거나 추가 정보를 원할 경우 항목의 나머지 부분을 읽어볼 수 있습니다. 여기에 나오는 단계 변호는 항목의 나머지에 포함된 단계 번호가 매겨진 섹션에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="3f591-p106">This section presents the connection steps without in-depth explanations. If you have questions or want more information, you can read rest of the topic. The step numbers here match the step-numbered sections in the rest of the topic:</span></span>
  
1. <span data-ttu-id="3f591-139">Open Windows PowerShell as an administrator (use **Run as administrator**).</span><span class="sxs-lookup"><span data-stu-id="3f591-139">Open Windows PowerShell as an administrator (use **Run as administrator**).</span></span>
    
2. <span data-ttu-id="3f591-140">Run this command, and enter your Office 365 work or school account credentials.</span><span class="sxs-lookup"><span data-stu-id="3f591-140">Run this command, and enter your Office 365 work or school account credentials.</span></span>
    
  ```
  $credential = Get-Credential
  ```

3. <span data-ttu-id="3f591-141">Run these commands to connect to Office 365.</span><span class="sxs-lookup"><span data-stu-id="3f591-141">Run these commands to connect to Office 365.</span></span>
    
  ```
  Import-Module MsOnline
  Connect-MsolService -Credential $credential
  ```

4. <span data-ttu-id="3f591-p107">Run these commands to connect to SharePoint Online. Replace  _\<domainhost>_ with the actual value for your domain. For example, for `litwareinc.onmicrosoft.com`, the  _\<domainhost>_ value is `litwareinc`.</span><span class="sxs-lookup"><span data-stu-id="3f591-p107">Run these commands to connect to SharePoint Online. Replace  _\<domainhost>_ with the actual value for your domain. For example, for `litwareinc.onmicrosoft.com`, the  _\<domainhost>_ value is `litwareinc`.</span></span>
    
  ```
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. <span data-ttu-id="3f591-p108">Run these commands to connect to Skype for Business Online. A warning about increasing the `WSMan NetworkDelayms` value is expected the first time you connect and should be ignored.</span><span class="sxs-lookup"><span data-stu-id="3f591-p108">Run these commands to connect to Skype for Business Online. A warning about increasing the `WSMan NetworkDelayms` value is expected the first time you connect and should be ignored.</span></span>
    
  ```
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. <span data-ttu-id="3f591-147">Run these commands to connect to Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="3f591-147">Run these commands to connect to Exchange Online.</span></span>
    
  ```
  $exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $exchangeSession -DisableNameChecking
  ```

7. <span data-ttu-id="3f591-148">Run these commands to connect to the Security &amp; Compliance Center.</span><span class="sxs-lookup"><span data-stu-id="3f591-148">Run these commands to connect to the Security &amp; Compliance Center.</span></span>
    
  ```
  $ccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication Basic -AllowRedirection
  Import-PSSession $ccSession -Prefix cc
  ```
> [!NOTE]
> <span data-ttu-id="3f591-p109">The text prefix "cc" is added to  *all*  Security &amp; Compliance Center cmdlet names so you can run cmdlets that exist in both Exchange Online and the Security &amp; Compliance Center in the same Windows PowerShell session. For example, **Get-RoleGroup** becomes **Get-ccRoleGroup** in the Security &amp; Compliance Center.</span><span class="sxs-lookup"><span data-stu-id="3f591-p109">The text prefix "cc" is added to  *all*  Security &amp; Compliance Center cmdlet names so you can run cmdlets that exist in both Exchange Online and the Security &amp; Compliance Center in the same Windows PowerShell session. For example, **Get-RoleGroup** becomes **Get-ccRoleGroup** in the Security &amp; Compliance Center.</span></span>
  
<span data-ttu-id="3f591-p110">Here are all the commands in a single block. Specify the name of your domain host, and then run them all at one time.</span><span class="sxs-lookup"><span data-stu-id="3f591-p110">Here are all the commands in a single block. Specify the name of your domain host, and then run them all at one time.</span></span>
  
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

<span data-ttu-id="3f591-153">When you are ready to close down the Windows PowerShell window, run this command to remove the active sessions to Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center:</span><span class="sxs-lookup"><span data-stu-id="3f591-153">When you are ready to close down the Windows PowerShell window, run this command to remove the active sessions to Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center:</span></span>
  
```
Remove-PSSession $sfboSession ; Remove-PSSession $exchangeSession ; Remove-PSSession $ccSession ; Disconnect-SPOService
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a><span data-ttu-id="3f591-154">긴 버전 (명령에 대 한 세부 정보)</span><span class="sxs-lookup"><span data-stu-id="3f591-154">The long version (instructions with detailed explanations)</span></span>
<span data-ttu-id="3f591-155"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="3f591-155"></span></span>

### <a name="step-1-open-windows-powershell-as-an-administrator"></a><span data-ttu-id="3f591-156">관리자 권한으로 Windows PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="3f591-156">Step 1: Open Windows PowerShell as an administrator</span></span>
<span data-ttu-id="3f591-157"><a name="Step1"> </a></span><span class="sxs-lookup"><span data-stu-id="3f591-157"></span></span>

<span data-ttu-id="3f591-158">If you're running Windows 10, Windows 8, Windows 8.1, Windows Server 2016, Windows Server 2012 R2, or Windows Server 2012 R2, do this:</span><span class="sxs-lookup"><span data-stu-id="3f591-158">If you're running Windows 10, Windows 8, Windows 8.1, Windows Server 2016, Windows Server 2012 R2, or Windows Server 2012 R2, do this:</span></span>
  
1. <span data-ttu-id="3f591-159">Use any of these methods to find the shortcut for **Windows PowerShell**:</span><span class="sxs-lookup"><span data-stu-id="3f591-159">Use any of these methods to find the shortcut for **Windows PowerShell**:</span></span>
    
  - <span data-ttu-id="3f591-160">On the Start screen, click an empty area, and type Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3f591-160">On the Start screen, click an empty area, and type Windows PowerShell.</span></span>
    
  - <span data-ttu-id="3f591-p111">On the desktop or the Start screen, press the Windows key+Q. In the Search charm, type Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3f591-p111">On the desktop or the Start screen, press the Windows key+Q. In the Search charm, type Windows PowerShell.</span></span>
    
  - <span data-ttu-id="3f591-p112">On the desktop or the Start screen, move your cursor to the upper-right corner, or swipe left from the right edge of the screen to show the charms. Select the Search charm, and enter Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3f591-p112">On the desktop or the Start screen, move your cursor to the upper-right corner, or swipe left from the right edge of the screen to show the charms. Select the Search charm, and enter Windows PowerShell.</span></span>
    
2. <span data-ttu-id="3f591-165">In the results, right-click **Windows PowerShell**, and select **Run as administrator**.</span><span class="sxs-lookup"><span data-stu-id="3f591-165">In the results, right-click **Windows PowerShell**, and select **Run as administrator**.</span></span>
    
3. <span data-ttu-id="3f591-166">If the **User Account Control** dialog box appears, select **Yes** to verify that you want to run Windows PowerShell under administrator credentials.</span><span class="sxs-lookup"><span data-stu-id="3f591-166">If the **User Account Control** dialog box appears, select **Yes** to verify that you want to run Windows PowerShell under administrator credentials.</span></span>
    
<span data-ttu-id="3f591-167">If you're running Windows 7 SP1 (or Windows Server 2008 R2 SP1), do this:</span><span class="sxs-lookup"><span data-stu-id="3f591-167">If you're running Windows 7 SP1 (or Windows Server 2008 R2 SP1), do this:</span></span>
  
1. <span data-ttu-id="3f591-p113">On the **Start** menu, select **All Programs** > **Accessories** > **Windows PowerShell**. Right-click **Windows PowerShell**, and then select **Run as administrator**.</span><span class="sxs-lookup"><span data-stu-id="3f591-p113">On the **Start** menu, select **All Programs** > **Accessories** > **Windows PowerShell**. Right-click **Windows PowerShell**, and then select **Run as administrator**.</span></span>
    
2. <span data-ttu-id="3f591-170">If the **User Account Control** dialog box appears, select **Yes** to verify that you want to run Windows PowerShell under administrator credentials.</span><span class="sxs-lookup"><span data-stu-id="3f591-170">If the **User Account Control** dialog box appears, select **Yes** to verify that you want to run Windows PowerShell under administrator credentials.</span></span>
    
<span data-ttu-id="3f591-p114">You must run Windows PowerShell as an administrator. If you don't, you're going to get an error message similar to this when you try to import one of the required modules.</span><span class="sxs-lookup"><span data-stu-id="3f591-p114">You must run Windows PowerShell as an administrator. If you don't, you're going to get an error message similar to this when you try to import one of the required modules.</span></span>
  
```
The specified module 'Microsoft.Online.SharePoint.Online.PowerShell' was not loaded because no valid module file was found in any directory.
```

<span data-ttu-id="3f591-p115">The only way to remedy the situation is to close Windows PowerShell and restart it as an administrator. Here's a quick and easy way to tell if you're running Windows PowerShell as an administrator: the prompt is  `PS C:\Windows\System32>`, not  `PS C:\Users\YourUserName>`.</span><span class="sxs-lookup"><span data-stu-id="3f591-p115">The only way to remedy the situation is to close Windows PowerShell and restart it as an administrator. Here's a quick and easy way to tell if you're running Windows PowerShell as an administrator: the prompt is  `PS C:\Windows\System32>`, not  `PS C:\Users\YourUserName>`.</span></span>

  
### <a name="step-2-create-a-windows-powershell-credentials-object"></a><span data-ttu-id="3f591-175">2단계: Windows PowerShell credentials 개체 만들기</span><span class="sxs-lookup"><span data-stu-id="3f591-175">Step 2: Create a Windows PowerShell credentials object</span></span>
<span data-ttu-id="3f591-176"><a name="Step2"> </a></span><span class="sxs-lookup"><span data-stu-id="3f591-176"></span></span>

<span data-ttu-id="3f591-p116">The credentials object provides an encrypted way to pass your user name and password to Windows PowerShell. To create a credentials object, run the following command in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3f591-p116">The credentials object provides an encrypted way to pass your user name and password to Windows PowerShell. To create a credentials object, run the following command in Windows PowerShell.</span></span>
  
```
$credential = Get-Credential
```

> [!NOTE]
>  <span data-ttu-id="3f591-p117">`$credential` is a variable that will store the credentials object. You don't have to name the variable `$credential`, but doing so makes it easier to remember which variable contains the credentials object. (And that's important, because we'll reuse this variable several times.) That will also make it easier for you to follow our examples, because this article will always use  `$credential` to represent the credentials object.</span><span class="sxs-lookup"><span data-stu-id="3f591-p117">`$credential` is a variable that will store the credentials object. You don't have to name the variable `$credential`, but doing so makes it easier to remember which variable contains the credentials object. (And that's important, because we'll reuse this variable several times.) That will also make it easier for you to follow our examples, because this article will always use  `$credential` to represent the credentials object.</span></span>
  
<span data-ttu-id="3f591-182">Windows PowerShell will then display a dialog box that looks like this.</span><span class="sxs-lookup"><span data-stu-id="3f591-182">Windows PowerShell will then display a dialog box that looks like this.</span></span>
  
![빈 자격 증명 요청 대화 상자](images/o365_powershell_empty_credentials_box.png)
  
<span data-ttu-id="3f591-184">Type your work or school account user name in the **User name** box, using the format _username@domainname_ (for example, kenmyer@litwareinc.onmicrosoft.com); type your password in the **Password** box; and then click **OK**:</span><span class="sxs-lookup"><span data-stu-id="3f591-184">Type your work or school account user name in the **User name** box, using the format _username@domainname_ (for example, kenmyer@litwareinc.onmicrosoft.com); type your password in the **Password** box; and then click **OK**:</span></span>
  
![완료된 자격 증명 요청 대화 상자](images/o365_powershell_completed_credentials_box.png)
  
<span data-ttu-id="3f591-p118">메모를 있는 그대로 자주 대/소문자를 볼 수 없습니다 모든 종류의 자격 증명 개체가 만들어졌는지 확인 합니다. (Windows PowerShell 일반적으로 알려줍니다 작업의 잘못 된 이동 하지만 항상 알 수 없는 경우 무엇 인가 오른쪽 때.) 자격 증명 개체가 만들어졌는지 확인 하려면 Windows PowerShell에서 다음 명령을 입력 하 고 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="3f591-p118">Note that, as is often the case, you won't see any sort of confirmation that the credentials object was created. (Windows PowerShell typically tells you when things go wrong but doesn't always tell you when things go right.) If you want to verify that the credentials object was created, type the following in Windows PowerShell and then press Enter.</span></span>
  
```
$credential
```

<span data-ttu-id="3f591-188">그러면 화면에 다음과 비슷한 결과가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f591-188">You should then see something similar to this on the screen.</span></span>
  
```
UserName                               Password
--------                               --------
kenmyer@litwareinc.onmicrosoft.com     System.Security.SecureString
```

<span data-ttu-id="3f591-p119">One thing to keep in mind here is that the [Get-Credential](https://go.microsoft.com/fwlink/p/?LinkId=389618) cmdlet only creates the credentials object; it does not authenticate you or otherwise verify that the user name and password you supplied are correct. For example, suppose you mistyped the user name as kenmyer@litwareinc.onmicrosoft.com. If you do that, **Get-Credential** will create a credentials object using that user name, and without checking to see if that is actually a valid user name. You won't know whether you have created a truly valid credentials object until you actually use that object to try to connect to the Office 365 services.</span><span class="sxs-lookup"><span data-stu-id="3f591-p119">One thing to keep in mind here is that the [Get-Credential](https://go.microsoft.com/fwlink/p/?LinkId=389618) cmdlet only creates the credentials object; it does not authenticate you or otherwise verify that the user name and password you supplied are correct. For example, suppose you mistyped the user name as kenmyer@litwareinc.onmicrosoft.com. If you do that, **Get-Credential** will create a credentials object using that user name, and without checking to see if that is actually a valid user name. You won't know whether you have created a truly valid credentials object until you actually use that object to try to connect to the Office 365 services.</span></span>
  
### <a name="step-3-connect-to-office-365"></a><span data-ttu-id="3f591-192">3단계: Office 365에 연결</span><span class="sxs-lookup"><span data-stu-id="3f591-192">Step 3: Connect to Office 365</span></span>
<span data-ttu-id="3f591-193"><a name="Step3"> </a></span><span class="sxs-lookup"><span data-stu-id="3f591-193"></span></span>

<span data-ttu-id="3f591-194">We'll start by connecting to Office 365 itself.</span><span class="sxs-lookup"><span data-stu-id="3f591-194">We'll start by connecting to Office 365 itself.</span></span> 
  
<span data-ttu-id="3f591-p120">The first thing we need to do here is import the Office 365 module (the Microsoft Azure Active Directory Module for Windows PowerShell). To do that, run this command in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3f591-p120">The first thing we need to do here is import the Office 365 module (the Microsoft Azure Active Directory Module for Windows PowerShell). To do that, run this command in Windows PowerShell.</span></span>
  
```
Import-Module MsOnline
```

<span data-ttu-id="3f591-197">모듈을 가져왔는지 확인하려면 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="3f591-197">If you want to verify that the module was imported, run this command.</span></span>
  
```
Get-Module
```

<span data-ttu-id="3f591-198">Somewhere in the list of modules that are returned by this command you should see something that looks like this:  `Manifest 1.0 MSOnline {Add-MsolForeignGroupToRole, Add-MsolG...}`.</span><span class="sxs-lookup"><span data-stu-id="3f591-198">Somewhere in the list of modules that are returned by this command you should see something that looks like this:  `Manifest 1.0 MSOnline {Add-MsolForeignGroupToRole, Add-MsolG...}`.</span></span>
  
<span data-ttu-id="3f591-199">If you see  `MSOnline` listed, that means that everything went according to plan.</span><span class="sxs-lookup"><span data-stu-id="3f591-199">If you see  `MSOnline` listed, that means that everything went according to plan.</span></span>
  
<span data-ttu-id="3f591-200">With the credentials object created (see [Step 2: Create a Windows PowerShell credentials object](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md#Step2)) and with the  `MsOnline` module loaded, we can now connect to Office 365 by using the [Connect-MsolService](https://go.microsoft.com/fwlink/p/?LinkId=532375) cmdlet and the following command.</span><span class="sxs-lookup"><span data-stu-id="3f591-200">With the credentials object created (see [Step 2: Create a Windows PowerShell credentials object](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md#Step2)) and with the  `MsOnline` module loaded, we can now connect to Office 365 by using the [Connect-MsolService](https://go.microsoft.com/fwlink/p/?LinkId=532375) cmdlet and the following command.</span></span>
  
```
Connect-MsolService -Credential $credential
```

<span data-ttu-id="3f591-p121">Notice that all you have to provide is the credentials object ( `$credential`). Based on those credentials, Office 365 will automatically connect you to the correct domain. You do not have to specify your domain name when running **Connect-MsolService**.</span><span class="sxs-lookup"><span data-stu-id="3f591-p121">Notice that all you have to provide is the credentials object ( `$credential`). Based on those credentials, Office 365 will automatically connect you to the correct domain. You do not have to specify your domain name when running **Connect-MsolService**.</span></span>
  
<span data-ttu-id="3f591-204">To verify that you really  *are*  connected to Office 365, run this command.</span><span class="sxs-lookup"><span data-stu-id="3f591-204">To verify that you really  *are*  connected to Office 365, run this command.</span></span>
  
```
Get-MsolDomain
```

<span data-ttu-id="3f591-205">그러면 다음과 비슷한 결과가 반환되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f591-205">In return, you should get back something similar to this.</span></span>
  
```
Name                         Status          Authentication
----                         ------          --------------
litwareinc.onmicrosoft.com   Verified        Managed
```

### <a name="step-4-connect-to-sharepoint-online"></a><span data-ttu-id="3f591-206">4단계: SharePoint Online에 연결</span><span class="sxs-lookup"><span data-stu-id="3f591-206">Step 4: Connect to SharePoint Online</span></span>
<span data-ttu-id="3f591-207"><a name="Step4"> </a></span><span class="sxs-lookup"><span data-stu-id="3f591-207"></span></span>

<span data-ttu-id="3f591-208">다음 명령 사용 하 여 SharePoint Online 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3f591-208">Import the SharePoint Online module with the following command:</span></span>
  
```
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
```

<span data-ttu-id="3f591-209">_DisableNameChecking_ 스위치는이 경고를 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3f591-209">The  _DisableNameChecking_ switch suppresses this warning.</span></span>
  
```
WARNING: The names of some imported commands from the module 'Microsoft.Online.SharePoint.PowerShell' include unapproved verbs that might make them less discoverable. To find the commands with unapproved verbs, run the Import-Module command again with the Verbose parameter. For a list of approved verbs, type Get-Verb.
```

<span data-ttu-id="3f591-p122">SharePoint online에 연결 하기 위해 두 가지 정보를 제공 해야: 사용자의 자격 증명 및 SharePoint Online 관리 사이트의 URL입니다. 자격 증명 부분은 쉽습니다: 변수에 이미 저장 했을 때 `$credential` (참조 [2 단계: Windows PowerShell 자격 증명 개체를 만들](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md#Step2)). 관리 사이트의 URL, 것 처럼 임을 충분히도 결정을 합니다. Office 365 도메인 이름을 인스턴트 메시징 세션을 `litwareinc.onmicrosoft.com`합니다.</span><span class="sxs-lookup"><span data-stu-id="3f591-p122">In order to connect to SharePoint Online, you need to supply two pieces of information: your credentials and the URL of your SharePoint Online admin site. The credentials part is easy: we've already stored that in the variable  `$credential` (see [Step 2: Create a Windows PowerShell credentials object](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md#Step2)). As for the URL of your admin site, that's easy enough to determine, as well. Suppose your Office 365 domain name is  `litwareinc.onmicrosoft.com`.</span></span>
  
<span data-ttu-id="3f591-214">관리 사이트 URL을 확인하려면 다음 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="3f591-214">To determine the admin site URL, do this:</span></span>
  
1. <span data-ttu-id="3f591-215">Start by using the prefix  `https://`.</span><span class="sxs-lookup"><span data-stu-id="3f591-215">Start by using the prefix  `https://`.</span></span>
    
2. <span data-ttu-id="3f591-p123">Add the domain host portion of your domain name. For example, for  `litwareinc.onmicrosoft.com`, the domain host name is  `litwareinc`. For  `contoso.onmicrosoft.com`, the domain host name is  `contoso`.</span><span class="sxs-lookup"><span data-stu-id="3f591-p123">Add the domain host portion of your domain name. For example, for  `litwareinc.onmicrosoft.com`, the domain host name is  `litwareinc`. For  `contoso.onmicrosoft.com`, the domain host name is  `contoso`.</span></span>
    
3. <span data-ttu-id="3f591-219">Add a hyphen (-) followed by  `admin.sharepoint.com`.</span><span class="sxs-lookup"><span data-stu-id="3f591-219">Add a hyphen (-) followed by  `admin.sharepoint.com`.</span></span>
    
<span data-ttu-id="3f591-220">위의 명령이 반환하는 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3f591-220">In other words:</span></span>
  
 `https://` + `litwareinc` + `-admin.sharepoint.com` = `https://litwareinc-admin.sharepoint.com`
  
<span data-ttu-id="3f591-p124">After you've constructed the URL, you can then use that URL and your credentials object to connect to SharePoint Online. Just call the [Connect-SPOService](https://go.microsoft.com/fwlink/p/?LinkId=532436) cmdlet, using a command similar to this one.</span><span class="sxs-lookup"><span data-stu-id="3f591-p124">After you've constructed the URL, you can then use that URL and your credentials object to connect to SharePoint Online. Just call the [Connect-SPOService](https://go.microsoft.com/fwlink/p/?LinkId=532436) cmdlet, using a command similar to this one.</span></span>
  
```
Connect-SPOService -Url https://litwareinc-admin.sharepoint.com -credential $credential
```

<span data-ttu-id="3f591-223">To verify that the connection has been made, run the following command in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3f591-223">To verify that the connection has been made, run the following command in Windows PowerShell.</span></span>
  
```
Get-SPOSite
```

<span data-ttu-id="3f591-p125">You should get a list of all your SharePoint Online sites. Here is an example:</span><span class="sxs-lookup"><span data-stu-id="3f591-p125">You should get a list of all your SharePoint Online sites. Here is an example:</span></span>
  
```
Url                                       Owner          Storage Quota
---                                       -----          -------------
http://litwareinc-public.sharepoint.com/                 1000
https://litwareinc.sharepoint.com/                       1000
https://litwareinc.sharepoint.com/search                 1000
```

<span data-ttu-id="3f591-p126">Your Office 365 commands (the ones described in [Step 3: Connect to Office 365](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md#Step3)) will still work. (Try running **Get-MsolUser**, and see for yourself.) That means that you can now manage both Office 365 and SharePoint Online from the same instance of Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3f591-p126">Your Office 365 commands (the ones described in [Step 3: Connect to Office 365](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md#Step3)) will still work. (Try running **Get-MsolUser**, and see for yourself.) That means that you can now manage both Office 365 and SharePoint Online from the same instance of Windows PowerShell.</span></span>
  
### <a name="step-5-connect-to-skype-for-business-online"></a><span data-ttu-id="3f591-228">5단계: 온라인 비즈니스를 위한 Skype에 연결</span><span class="sxs-lookup"><span data-stu-id="3f591-228">Step 5: Connect to Skype for Business Online</span></span>
<span data-ttu-id="3f591-229"><a name="Step5"> </a></span><span class="sxs-lookup"><span data-stu-id="3f591-229"></span></span>

<span data-ttu-id="3f591-p127">Connecting to Skype for Business Online (and to Exchange Online or the Security &amp; Compliance Center) is different than connecting to Office 365 or to SharePoint Online. That's because the Skype for Business Online and Exchange Online cmdlets don't get installed on your computer like the Office 365 and the SharePoint Online cmdlets do. Instead, each time you sign in, the appropriate cmdlets are temporarily copied to your computer. When you sign off, those cmdlets are then removed from your computer.</span><span class="sxs-lookup"><span data-stu-id="3f591-p127">Connecting to Skype for Business Online (and to Exchange Online or the Security &amp; Compliance Center) is different than connecting to Office 365 or to SharePoint Online. That's because the Skype for Business Online and Exchange Online cmdlets don't get installed on your computer like the Office 365 and the SharePoint Online cmdlets do. Instead, each time you sign in, the appropriate cmdlets are temporarily copied to your computer. When you sign off, those cmdlets are then removed from your computer.</span></span>
  
<span data-ttu-id="3f591-p128">In order to connect to Skype for Business Online, you need to import the Skype for Business Online module. To do that, run this command.</span><span class="sxs-lookup"><span data-stu-id="3f591-p128">In order to connect to Skype for Business Online, you need to import the Skype for Business Online module. To do that, run this command.</span></span>
  
```
Import-Module SkypeOnlineConnector
```

<span data-ttu-id="3f591-236">이를 처음으로 수행하면 다음 경고 메시지가 표시될 수 있습니다. 이 경고 메시지는 무시해도 안전합니다.</span><span class="sxs-lookup"><span data-stu-id="3f591-236">The first time you do this, you might see the following warning message, which you can safely ignore.</span></span>
  
```
WARNING: WSMan NetworkDelayms has been set to 30000 milliseconds. The previous value was 5000 milliseconds.
WARNING: To improve the performance of the Lync Online Connector, it is recommended that the network delay be set to
30000 milliseconds (30 seconds). However, you can use Set-WinRMNetworkDelayMS to change the network delay to any
integer value.
```

<span data-ttu-id="3f591-237">모듈을 가져온 후 이 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="3f591-237">After the module has been imported, run this command.</span></span>
  
```
$sfboSession = New-CsOnlineSession -Credential $credential
```

<span data-ttu-id="3f591-p129">We have created a remote PowerShell session. In this case, that means that we've connected to an instance of Windows PowerShell running on one of the Office 365 servers.</span><span class="sxs-lookup"><span data-stu-id="3f591-p129">We have created a remote PowerShell session. In this case, that means that we've connected to an instance of Windows PowerShell running on one of the Office 365 servers.</span></span> 
  
<span data-ttu-id="3f591-p130">Although we've made a connection to Office 365, we haven't downloaded the scripts, cmdlets, and other items needed to manage Skype for Business Online. To do that, we have to run this command.</span><span class="sxs-lookup"><span data-stu-id="3f591-p130">Although we've made a connection to Office 365, we haven't downloaded the scripts, cmdlets, and other items needed to manage Skype for Business Online. To do that, we have to run this command.</span></span>
  
```
Import-PSSession $sfboSession
```

<span data-ttu-id="3f591-242">When you import the Windows PowerShell session, you should see a progress bar similar to the following, a progress bar that reports on all the Skype for Business Online cmdlets being imported to your computer.</span><span class="sxs-lookup"><span data-stu-id="3f591-242">When you import the Windows PowerShell session, you should see a progress bar similar to the following, a progress bar that reports on all the Skype for Business Online cmdlets being imported to your computer.</span></span>
  
![Lync Online 진행률 표시줄](images/o365_powershell_lync_progress_bar.png)
  
<span data-ttu-id="3f591-244">진행률 표시줄이 사라지면 다음과 비슷한 출력이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f591-244">When the progress bar disappears, you should then see output similar to the following.</span></span>
  
```
ModuleType Version    Name               ExportedCommands
---------- -------    ----               ----------------
Script     1.0        tmp_swc5mp4v.1ck  {Copy-CsVoicePolicy, Disabl...
```

### <a name="step-6-connect-to-exchange-online"></a><span data-ttu-id="3f591-245">6단계: Exchange Online에 연결</span><span class="sxs-lookup"><span data-stu-id="3f591-245">Step 6: Connect to Exchange Online</span></span>
<span data-ttu-id="3f591-246"><a name="Step6"> </a></span><span class="sxs-lookup"><span data-stu-id="3f591-246"></span></span>

<span data-ttu-id="3f591-247">Exchange Online을 사용한 원격 Windows PowerShell 세션을 만들고이 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f591-247">Run this command, which creates a remote Windows PowerShell session with Exchange Online.</span></span>
  
```
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
```

> [!NOTE]
> <span data-ttu-id="3f591-p131">Why is the command for connecting to Exchange Online more complicated than the command to connect to Skype for Business Online? Technically, it's not: both commands do the exact same thing. However, the Skype for Business Online team created its own cmdlet— **New-CsOnlineSession** —that hides some of the parameters (like _Authentication_ and _AllowRedirection_) that are used when connecting to Exchange Online. Instead of requiring you to type that information yourself, the  _Authentication_ and _AllowRedirection_ parameters are effectively built in to the **New-CsOnlineSession** cmdlet. You have to type those parameters when connecting to Exchange Online because Exchange Online uses the standard [New-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389621) cmdlet to connect to Office 365. The disadvantage is that you have a little more typing to do. The advantage is that you don't have to download and install an Exchange Online module.</span><span class="sxs-lookup"><span data-stu-id="3f591-p131">Why is the command for connecting to Exchange Online more complicated than the command to connect to Skype for Business Online? Technically, it's not: both commands do the exact same thing. However, the Skype for Business Online team created its own cmdlet— **New-CsOnlineSession** —that hides some of the parameters (like _Authentication_ and _AllowRedirection_) that are used when connecting to Exchange Online. Instead of requiring you to type that information yourself, the  _Authentication_ and _AllowRedirection_ parameters are effectively built in to the **New-CsOnlineSession** cmdlet. You have to type those parameters when connecting to Exchange Online because Exchange Online uses the standard [New-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389621) cmdlet to connect to Office 365. The disadvantage is that you have a little more typing to do. The advantage is that you don't have to download and install an Exchange Online module.</span></span>
  
<span data-ttu-id="3f591-255">All you have to do now is import this remote session, just like we did with Skype for Business Online.</span><span class="sxs-lookup"><span data-stu-id="3f591-255">All you have to do now is import this remote session, just like we did with Skype for Business Online.</span></span>
  
```
Import-PSSession $exchangeSession -DisableNameChecking
```

<span data-ttu-id="3f591-256">그러면 화면에 다음과 같은 내용이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f591-256">You should see something similar to this on the screen.</span></span>
  
```
ModuleType Version  Name             ExportedCommands
---------- -------  ----             ----------------
Script     1.0      tmp_nweiqjvl.geu {Add-AvailabilityAddressSpace...
```

<span data-ttu-id="3f591-257">이제 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="3f591-257">Now try running this command.</span></span>
  
```
Get-AcceptedDomain
```

<span data-ttu-id="3f591-258">반환, 구성 된 전자 메일 주소에 대 한 Exchange Online Office 365 도메인에 대 한 정보를 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f591-258">In return, you should see information about your Office 365 domains that are configured for email addresses in Exchange Online.</span></span>
  
```
Name            DomainName          DomainType      Default
----            ----------          ----------      -------
litwareinc.com  litwareinc.com      Authoritative   True
```

### <a name="step-7-connect-to-the-security-amp-compliance-center"></a><span data-ttu-id="3f591-259">Step 7: Connect to the Security &amp; Compliance Center</span><span class="sxs-lookup"><span data-stu-id="3f591-259">Step 7: Connect to the Security &amp; Compliance Center</span></span>
<span data-ttu-id="3f591-260"><a name="Step7"> </a></span><span class="sxs-lookup"><span data-stu-id="3f591-260"></span></span>

<span data-ttu-id="3f591-p132">The Security &amp; Compliance Center is a service in Office 365 that lets you to manage compliance features from one location. For more information, see [Office 365 compliance center](http://technet.microsoft.com/library/fde83656-f136-448d-b250-6fa17b503e4e.aspx).</span><span class="sxs-lookup"><span data-stu-id="3f591-p132">The Security &amp; Compliance Center is a service in Office 365 that lets you to manage compliance features from one location. For more information, see [Office 365 compliance center](http://technet.microsoft.com/library/fde83656-f136-448d-b250-6fa17b503e4e.aspx).</span></span>
  
<span data-ttu-id="3f591-263">The connection instructions for the Security &amp; Compliance Center are very similar to those for Exchange Online, but with an added twist, which you'll see in a moment.</span><span class="sxs-lookup"><span data-stu-id="3f591-263">The connection instructions for the Security &amp; Compliance Center are very similar to those for Exchange Online, but with an added twist, which you'll see in a moment.</span></span>
  
<span data-ttu-id="3f591-264">Run this command, which creates a remote PowerShell session with the Security &amp; Compliance Center.</span><span class="sxs-lookup"><span data-stu-id="3f591-264">Run this command, which creates a remote PowerShell session with the Security &amp; Compliance Center.</span></span>
  
```
$ccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication Basic -AllowRedirection
```

<span data-ttu-id="3f591-265">그런 후 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="3f591-265">Now run this command:</span></span>
  
```
Import-PSSession $ccSession -Prefix cc
```

<span data-ttu-id="3f591-p133">Again, this command is very similar to the command for Exchange Online. The  _DisableNameChecking_ switch isn't required because there are no unapproved verbs in the Security &amp; Compliance Center. But what about that additional `-Prefix cc` parameter and value? That's the added twist we told you about.</span><span class="sxs-lookup"><span data-stu-id="3f591-p133">Again, this command is very similar to the command for Exchange Online. The  _DisableNameChecking_ switch isn't required because there are no unapproved verbs in the Security &amp; Compliance Center. But what about that additional `-Prefix cc` parameter and value? That's the added twist we told you about.</span></span>
  
<span data-ttu-id="3f591-p134">Exchange Online and the Security &amp; Compliance Center share some cmdlets that have exactly the same names and provide the same functionality. **Get-RoleGroup** is an example.</span><span class="sxs-lookup"><span data-stu-id="3f591-p134">Exchange Online and the Security &amp; Compliance Center share some cmdlets that have exactly the same names and provide the same functionality. **Get-RoleGroup** is an example.</span></span>
  
<span data-ttu-id="3f591-p135">So what happens if you try to import two sessions that contain cmdlets with the same name? They collide. You'll get a big yellow warning message that says,  `WARNING: Proxy creation has been skipped for the following command:` followed by the list of conflicting cmdlets that couldn't be imported. The end result? You can run **Get-RoleGroup** in Exchange Online because you connected there first, but you can't run **Get-RoleGroup** in the Security &amp; Compliance Center because you connected there last and the conflicting cmdlets refused to import.</span><span class="sxs-lookup"><span data-stu-id="3f591-p135">So what happens if you try to import two sessions that contain cmdlets with the same name? They collide. You'll get a big yellow warning message that says,  `WARNING: Proxy creation has been skipped for the following command:` followed by the list of conflicting cmdlets that couldn't be imported. The end result? You can run **Get-RoleGroup** in Exchange Online because you connected there first, but you can't run **Get-RoleGroup** in the Security &amp; Compliance Center because you connected there last and the conflicting cmdlets refused to import.</span></span>
  
<span data-ttu-id="3f591-p136">The easiest way to deal with this problem is to add an arbitrary text prefix to the imported Security &amp; Compliance Center cmdlets. We did that using the  _Prefix_ parameter with the value "cc" on the **Import-PSSession** cmdlet. What did that do for us? It eliminated the conflicts by (slightly) changing the Security &amp; Compliance Center cmdlet names for this session. All of the imported Security &amp; Compliance Center cmdlets now start with "cc" in the noun part of the cmdlet name (to the right of the "-"). For example, the contentious **Get-RoleGroup** cmdlet becomes **Get-ccRoleGroup** for the Security &amp; Compliance Center so it doesn't conflict with **Get-RoleGroup** for Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="3f591-p136">The easiest way to deal with this problem is to add an arbitrary text prefix to the imported Security &amp; Compliance Center cmdlets. We did that using the  _Prefix_ parameter with the value "cc" on the **Import-PSSession** cmdlet. What did that do for us? It eliminated the conflicts by (slightly) changing the Security &amp; Compliance Center cmdlet names for this session. All of the imported Security &amp; Compliance Center cmdlets now start with "cc" in the noun part of the cmdlet name (to the right of the "-"). For example, the contentious **Get-RoleGroup** cmdlet becomes **Get-ccRoleGroup** for the Security &amp; Compliance Center so it doesn't conflict with **Get-RoleGroup** for Exchange Online.</span></span>
  
<span data-ttu-id="3f591-p137">The downside?  *All*  Security &amp; Compliance Center cmdlet names receive the "cc" prefix—even unique cmdlets that don't need it. For example, **Get-ComplianceSearch** becomes **Get-ccComplianceSearch** even though there is no such cmdlet in Exchange Online. It's a bit of a pain, but not too bad when you consider the benefits of managing all Office 365 services in a single Windows PowerShell session. Just remember to add "cc" to the cmdlet names for all procedures in the Security &amp; Compliance Center.</span><span class="sxs-lookup"><span data-stu-id="3f591-p137">The downside?  *All*  Security &amp; Compliance Center cmdlet names receive the "cc" prefix—even unique cmdlets that don't need it. For example, **Get-ComplianceSearch** becomes **Get-ccComplianceSearch** even though there is no such cmdlet in Exchange Online. It's a bit of a pain, but not too bad when you consider the benefits of managing all Office 365 services in a single Windows PowerShell session. Just remember to add "cc" to the cmdlet names for all procedures in the Security &amp; Compliance Center.</span></span>
  
<span data-ttu-id="3f591-288">그런 다음 모든 작업을 완료하면 화면에 다음과 유사한 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f591-288">If all goes well, you'll see something similar to this:</span></span>
  
```
ModuleType Version  Name             ExportedCommands
---------- -------  ----             ----------------
Script     1.0      tmp_xbbx5exr.ehm {Add-ccRoleGroupMember, Get-ccAdminAuditLogConfig, Get-ccA...
```

<span data-ttu-id="3f591-289">Now you are free to manage all Office 365 services in a single Windows PowerShell session.</span><span class="sxs-lookup"><span data-stu-id="3f591-289">Now you are free to manage all Office 365 services in a single Windows PowerShell session.</span></span>
  
### <a name="step-8-gracefully-end-your-powershell-sessions"></a><span data-ttu-id="3f591-290">8단계: PowerShell 세션을 정상적으로 종료</span><span class="sxs-lookup"><span data-stu-id="3f591-290">Step 8: Gracefully end your PowerShell sessions</span></span>
<span data-ttu-id="3f591-291"><a name="Step8"> </a></span><span class="sxs-lookup"><span data-stu-id="3f591-291"></span></span>

<span data-ttu-id="3f591-p138">Windows PowerShell 창을 닫으면 하는 경우 다음 15 분 정도 대 한 비즈니스 온라인 원격 연결에 대 한 사용자 Skype 활성 상태로 유지 됩니다. 모든 한 명 또는 하나의 도메인 열기를 가질 수 있다는 동시 연결 수를 제한 하는 비즈니스 온라인 용 Skype, 때문에 문제가 발생할 수 있는 합니다. 온라인 비즈니스에 대 한 Skype와 개별 관리자, 최대 세 열린 한번에 연결 하 고 도메인을 최대 9 개의 열린 연결을 가질 수 있습니다. 온라인 비즈니스에 대 한 Skype에 로그인 하 고 다음 세션을 제대로 닫지 않고를 종료 하는 경우 다음 15 분 정도 대 한 해당 세션 계속 열려 있습니다. 결과적으로,는 연결이 하나 더 적은 사용자나 도메인에서 다른 관리자에 게 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f591-p138">If you just close the Windows PowerShell window, your Skype for Business Online remote connection will remain active for the next 15 minutes or so. Because Skype for Business Online limits the number of simultaneous connections that any one person or any one domain can have open, that could be a problem. With Skype for Business Online, an individual administrator can have, at most, three open connections at one time, and a domain can have a maximum of nine open connections. If you sign in to Skype for Business Online and then exit without properly closing the session, that session remains open for the next 15 minutes or so. As a result, that's one fewer connection available to you or to other administrators in your domain.</span></span>
  
<span data-ttu-id="3f591-p139">Instead, let's close the remote sessions for Skype for Business Online, Exchange Online, and the Security &amp; Compliance Center gracefully. Before we do that, run this command.</span><span class="sxs-lookup"><span data-stu-id="3f591-p139">Instead, let's close the remote sessions for Skype for Business Online, Exchange Online, and the Security &amp; Compliance Center gracefully. Before we do that, run this command.</span></span>
  
```
Get-PSSession
```

<span data-ttu-id="3f591-p140">The [Get-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=532437) cmdlet should show you that you have at least three remote sessions open, one for Skype for Business Online, one for Exchange Online and one for the Security &amp; Compliance Center (it's possible you could have more than three remote sessions running, depending on whether you've used this instance of Windows PowerShell to connect to something else besides the Office 365 services). You should see something similar to the following.</span><span class="sxs-lookup"><span data-stu-id="3f591-p140">The [Get-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=532437) cmdlet should show you that you have at least three remote sessions open, one for Skype for Business Online, one for Exchange Online and one for the Security &amp; Compliance Center (it's possible you could have more than three remote sessions running, depending on whether you've used this instance of Windows PowerShell to connect to something else besides the Office 365 services). You should see something similar to the following.</span></span>
  
```
Id Name     ComputerName     State   ConfigurationName    Availability
-- ----     ------------     -----   -----------------    ------------
 1 Session1 webdir0a.onl...  Opened  Microsoft.PowerShell    Available
 2 Session2 outlook.offi...  Opened  Microsoft.Exchange      Available
 3 Session3 ps.complianc...  Opened  Microsoft.Exchange      Available
```

<span data-ttu-id="3f591-p141">To close these three sessions, run these commands one at a time. The first command closes the Skype for Business Online session, the second closes the Exchange Online session, and the third closes the Security &amp; Compliance Center session.</span><span class="sxs-lookup"><span data-stu-id="3f591-p141">To close these three sessions, run these commands one at a time. The first command closes the Skype for Business Online session, the second closes the Exchange Online session, and the third closes the Security &amp; Compliance Center session.</span></span>
  
```
Remove-PSSession $sfboSession
Remove-PSSession $exchangeSession
Remove-PSSession $ccSession
```

<span data-ttu-id="3f591-303">이제 **Get-pssession** cmdlet을 실행 하는 경우 표시 되어야 nothing 전혀 (않은 경우 다른 원격 세션이 작동 및 실행 중).</span><span class="sxs-lookup"><span data-stu-id="3f591-303">If you now run the **Get-PSSession** cmdlet, you should see nothing at all (unless you have other remote sessions up and running).</span></span>
  
![원격 세션이 없는 Windows PowerShell 콘솔](images/o365_powershell_no_remote_sessions.png)
  
> [!NOTE]
> <span data-ttu-id="3f591-305">If you'd prefer to close all your remote sessions at the same time, you can use this command: >  `Get-PSSession | Remove-PSSession`</span><span class="sxs-lookup"><span data-stu-id="3f591-305">If you'd prefer to close all your remote sessions at the same time, you can use this command: >  `Get-PSSession | Remove-PSSession`</span></span>
  
<span data-ttu-id="3f591-306">If you now try running a cmdlet from any of these closed sessions (for example, **Get-CsMeetingConfiguration** in Skype for Business Online) you'll get an error message that's similar to this one.</span><span class="sxs-lookup"><span data-stu-id="3f591-306">If you now try running a cmdlet from any of these closed sessions (for example, **Get-CsMeetingConfiguration** in Skype for Business Online) you'll get an error message that's similar to this one.</span></span>
  
```
Get-CsMeetingConfiguration : The term 'Get-CsMeetingConfiguration' is not recognized as the name of a cmdlet, function, script file, or operable program. Check the spelling of the name, or if a path was included, verify that the path is correct and try again.
```

<span data-ttu-id="3f591-307">We get that error message because the cmdlets for Skype for Business Online, Exchange Online, and the Security &amp; Compliance Center were deleted when we closed the remote sessions.</span><span class="sxs-lookup"><span data-stu-id="3f591-307">We get that error message because the cmdlets for Skype for Business Online, Exchange Online, and the Security &amp; Compliance Center were deleted when we closed the remote sessions.</span></span>
  
<span data-ttu-id="3f591-308">SharePoint Online 세션을 닫으려면 다음이 명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f591-308">To close the SharePoint Online session, type this command.</span></span>
  
```
Disconnect-SPOService
```

<span data-ttu-id="3f591-309">이제 **Get-sposite** cmdlet을 실행 하려고 하는 경우 다음과 같은 오류 메시지가 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3f591-309">If you now try to run the **Get-SPOSite** cmdlet, you'll get an error message like this.</span></span>
  
```
get-sposite : No connection available. Use Connect-SPOService before running this CmdLet.
```

<span data-ttu-id="3f591-310">더이상 SharePoint Online에 연결 되어있지 않으므로 사이트 정보를 검색할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3f591-310">You can't retrieve site information because you're no longer connected to SharePoint Online.</span></span>
  
<span data-ttu-id="3f591-p142">Office 365에 대 한 연결을 것 처럼 **Connect-msolservice** cmdlet을 없지만 방법이 해당 **연결 끊기 MsolService** cmdlet 없습니다. 따라서 Office 365에 대 한 Windows PowerShell 창을 닫습니다. 그럼에도 불구 하 고 것도이 작업을 수행 하는 것이 좋습니다 제대로 제거할 수 있도록 SharePoint에서 온라인으로 Skype 비즈니스 Online, Exchange Online 및 보안에 대 한 마지막 &amp; 준수 센터입니다.</span><span class="sxs-lookup"><span data-stu-id="3f591-p142">As for your connection to Office 365, although there's a **Connect-MsolService** cmdlet, there's no corresponding **Disconnect-MsolService** cmdlet. So for Office 365, just close the Windows PowerShell window. Nevertheless, it's still a good idea to do this last so you can properly disconnect from SharePoint Online, Skype for Business Online, Exchange Online, and the Security &amp; Compliance Center.</span></span>
  
## <a name="new-to-office-365"></a><span data-ttu-id="3f591-314">Office 365의 새로운 기능</span><span class="sxs-lookup"><span data-stu-id="3f591-314">New to Office 365?</span></span>
<span data-ttu-id="3f591-315"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="3f591-315"></span></span>

||
|:-----|
|<span data-ttu-id="3f591-p143">![LinkedIn 학습에 대 한 짧은 아이콘](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **새로 만들기를 Office 365?**         [Office 365 관리자 및 IT 전문가](https://support.office.com/article/Office-365-admin-and-IT-pro-courses-68cc9b95-0bdc-491e-a81f-ee70b3ec63c5), LinkedIn 학습에 의해 제공자에 대 한 무료 비디오 코스를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f591-p143">![The short icon for LinkedIn Learning](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **New to Office 365?**         Discover free video courses for [Office 365 admins and IT pros](https://support.office.com/article/Office-365-admin-and-IT-pro-courses-68cc9b95-0bdc-491e-a81f-ee70b3ec63c5), brought to you by LinkedIn Learning.</span></span> |
   
## <a name="see-also"></a><span data-ttu-id="3f591-318">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3f591-318">See also</span></span>

#### 

[<span data-ttu-id="3f591-319">Office 365 PowerShell 사용한 Office 365 관리</span><span class="sxs-lookup"><span data-stu-id="3f591-319">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="3f591-320">Office 365 PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="3f591-320">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
  
[<span data-ttu-id="3f591-321">Office 365 PowerShell을 사용하여 SharePoint Online 관리</span><span class="sxs-lookup"><span data-stu-id="3f591-321">Manage SharePoint Online with Office 365 PowerShell</span></span>](manage-sharepoint-online-with-office-365-powershell.md)
  
[<span data-ttu-id="3f591-322">사용자 계정 및 Office 365 PowerShell을 사용 하 여 라이센스 관리</span><span class="sxs-lookup"><span data-stu-id="3f591-322">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="3f591-323">Office 365에서 Windows PowerShell을 사용하여 보고서 만들기</span><span class="sxs-lookup"><span data-stu-id="3f591-323">Use Windows PowerShell to create reports in Office 365</span></span>](use-windows-powershell-to-create-reports-in-office-365.md)

