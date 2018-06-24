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
ms.openlocfilehash: ba23dde0fd79d13274244b52c5914d9249640570
ms.sourcegitcommit: f496a401245240ec01754edcd4d44e7a0194d068
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/22/2018
ms.locfileid: "19907189"
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a><span data-ttu-id="30cc0-103">단일 Windows PowerShell 창에서 모든 Office 365 서비스에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="30cc0-103">Connect to all Office 365 services in a single Windows PowerShell window</span></span>

 <span data-ttu-id="30cc0-104">**요약:** 별도 PowerShell 콘솔 창에서 다른 Office 365 서비스를 관리 하는 대신 모든 Office 365 서비스에 연결할 수 있으며 해당 단일 콘솔 창에서 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30cc0-104">**Summary:** Instead of managing different Office 365 services in separate PowerShell console windows, you can connect to all Office 365 services and manage them from single console window.</span></span>
  
<span data-ttu-id="30cc0-p101">PowerShell을 사용 하 여 Office 365를 관리 하는 Office 365 관리 센터, SharePoint Online, Exchange Online, 비즈니스 온라인 용 Skype 및 보안 &amp;준수 센터입니다. 별도 Windows PowerShell 세션에 다섯 개의 서로 다른 연결 메서드를 통해 사용자의 데스크톱은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="30cc0-p101">When you use PowerShell to manage Office 365, it is possible to have up to five different Windows PowerShell sessions open at the same time corresponding to Office 365 admin center, SharePoint Online, Exchange Online, Skype for Business Online, and the Security &amp; Compliance Center. With five different connection methods in separate Windows PowerShell sessions, your desktop could look like this:</span></span>
  
![동시에 실행되는 5개의 Windows PowerShell 콘솔](images/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
<span data-ttu-id="30cc0-p102">이 교차 서비스 관리에 대 한 이러한 5 개의 창 사이에서 데이터를 교환할 수 없습니다 때문에 Office 365를 관리 하기 위한 최적의있지 않습니다. 이 항목에서는 Office 365, 비즈니스 Online, Exchange Online, SharePoint Online 용 Skype 및 보안을 관리할 수 있는 Windows PowerShell의 단일 인스턴스를 사용 하는 방법을 설명 &amp; 준수 센터입니다.</span><span class="sxs-lookup"><span data-stu-id="30cc0-p102">This is not optimal for managing Office 365 because you can't exchange data among those five windows for cross-service management. This topic describes how to use a single instance of Windows PowerShell from which you can manage Office 365, Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center.</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="30cc0-110">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="30cc0-110">Before you begin</span></span>
<span data-ttu-id="30cc0-111"><a name="BeforeYouBegin"> </a></span><span class="sxs-lookup"><span data-stu-id="30cc0-111"></span></span>

<span data-ttu-id="30cc0-112">모든 Office 365에서 Windows PowerShell의 단일 인스턴스를 관리할 수 있습니다를 하기 전에 다음 필수 구성 요소를 고려:</span><span class="sxs-lookup"><span data-stu-id="30cc0-112">Before you can manage all of Office 365 from a single instance of Windows PowerShell, consider the following prerequisites:</span></span>
  
- <span data-ttu-id="30cc0-p103">Office 365 작동 또는 학교 계정을 사용 하는 이러한 절차에 대 한 요구를 Office 365 관리자 역할의 구성원 이어야 합니다. 자세한 내용은 [Office 365에 대 한 관리자 역할](https://go.microsoft.com/fwlink/p/?LinkId=532367)을 참조 하십시오. 이 Office 365 PowerShell에 대 한, 다른 모든 Office 365 서비스에 대 한 반드시 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="30cc0-p103">The Office 365 work or school account that you use for these procedures needs to be a member of an Office 365 admin role. For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367). This a requirement for Office 365 PowerShell, not necessarily for all other Office 365 services.</span></span>
    
- <span data-ttu-id="30cc0-116">다음 Windows 버전을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30cc0-116">You can use the following 64-bit versions of Windows:</span></span>
    
  - <span data-ttu-id="30cc0-117">Windows 10</span><span class="sxs-lookup"><span data-stu-id="30cc0-117">Windows 10</span></span>
    
  - <span data-ttu-id="30cc0-118">Windows 8.1 또는 Windows 8</span><span class="sxs-lookup"><span data-stu-id="30cc0-118">Windows 8.1 or Windows 8</span></span>
    
  - <span data-ttu-id="30cc0-119">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="30cc0-119">Windows Server 2016</span></span>
    
  - <span data-ttu-id="30cc0-120">Windows Server 2012 R2 또는 Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="30cc0-120">Windows Server 2012 R2 or Windows Server 2012</span></span>
    
  - <span data-ttu-id="30cc0-121">Windows 7 SP1(서비스 팩 1)\*</span><span class="sxs-lookup"><span data-stu-id="30cc0-121">Windows 7 Service Pack 1 (SP1)\*</span></span>
    
  - <span data-ttu-id="30cc0-122">Windows Server 2008 R2 SP1\*</span><span class="sxs-lookup"><span data-stu-id="30cc0-122">Windows Server 2008 R2 SP1\*</span></span>
    
    <span data-ttu-id="30cc0-p104">\*Microsoft.NET Framework 4.5를 설치 해야 합니다. *x* 하 고 다음 중 하나는 Windows Management Framework 3.0 또는 Windows 관리 프레임 워크 4.0 합니다. 자세한 내용은 [.NET Framework를 설치](https://go.microsoft.com/fwlink/p/?LinkId=257868) 하 고 [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) 또는 [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="30cc0-p104">\* You need to install the Microsoft .NET Framework 4.5.*x* and then either the Windows Management Framework 3.0 or the Windows Management Framework 4.0. For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) and [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) or [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span></span>
    
    <span data-ttu-id="30cc0-125">비즈니스 온라인 모듈 및 Office 365 모듈 중 하나는 Skype에 대 한 요구 사항으로 인해 64 비트 버전의 Windows 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="30cc0-125">You need to use a 64-bit version of Windows because of the requirements for the Skype for Business Online module and one of the Office 365 modules.</span></span>
    
- <span data-ttu-id="30cc0-126">Azure AD에 필요한 사용 되는 모듈을 설치 해야 SharePoint Online 및 비즈니스 온라인 용 Skype:</span><span class="sxs-lookup"><span data-stu-id="30cc0-126">You need to install the modules that are required for Azure AD, SharePoint Online, and Skype for Business Online:</span></span>
    
   - [<span data-ttu-id="30cc0-127">Azure Active Directory V2</span><span class="sxs-lookup"><span data-stu-id="30cc0-127">Azure Active Directory V2</span></span>](connect-to-office-365-powershell.md#ConnectV2)
   - [<span data-ttu-id="30cc0-128">SharePoint Online 관리 셸</span><span class="sxs-lookup"><span data-stu-id="30cc0-128">SharePoint Online Management Shell</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [<span data-ttu-id="30cc0-129">온라인으로 비즈니스 Windows PowerShell 모듈에 대 한 Skype</span><span class="sxs-lookup"><span data-stu-id="30cc0-129">Skype for Business Online, Windows PowerShell Module</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532439)
    
-  <span data-ttu-id="30cc0-p105">Windows PowerShell 스크립트를 실행 하려면 서명 된 Skype에 대 한 비즈니스 Online, Exchange Online 및 보안에 대 한 구성 해야하는 &amp; 준수 센터입니다. 이 작업을 수행 하려면 관리자 권한으로 Windows PowerShell 세션에서 다음 명령을 실행 ( **관리자 권한으로 실행**을 선택 하 여 열면 Windows PowerShell 창)입니다.</span><span class="sxs-lookup"><span data-stu-id="30cc0-p105">Windows PowerShell needs to be configured to run signed scripts for Skype for Business Online, Exchange Online, and the Security &amp; Compliance Center. To do this, run the following command in an elevated Windows PowerShell session (a Windows PowerShell window you open by selecting **Run as administrator**).</span></span>
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="connection-steps-when-using-a-password"></a><span data-ttu-id="30cc0-132">암호를 사용 하는 경우에 연결 단계</span><span class="sxs-lookup"><span data-stu-id="30cc0-132">Connection steps when using a password</span></span>
<span data-ttu-id="30cc0-133"><a name="ConnStepsPassword"> </a></span><span class="sxs-lookup"><span data-stu-id="30cc0-133"></span></span>

<span data-ttu-id="30cc0-134">단일 PowerShell 창에서 모든 서비스에 연결 하는 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="30cc0-134">Here are the steps to connect to all the services in a single PowerShell window.</span></span>
  
1. <span data-ttu-id="30cc0-135">관리자 권한 ( **관리자 권한으로 실행**하는 사용)으로 Windows PowerShell을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="30cc0-135">Open Windows PowerShell as an administrator (use **Run as administrator**).</span></span>
    
2. <span data-ttu-id="30cc0-136">이 명령을 실행 하 고 Office 365 작업 시간을 입력 하거나 계정 자격 증명을 학교 합니다.</span><span class="sxs-lookup"><span data-stu-id="30cc0-136">Run this command, and enter your Office 365 work or school account credentials.</span></span>
    
  ```
  $credential = Get-Credential
  ```

3. <span data-ttu-id="30cc0-137">연결을 Azure Active Directory (AD) 그래프 모듈에 대 한 Active Directory Azure PowerShell을 사용 하 여이 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="30cc0-137">Run this command to connect to Azure Active Directory (AD) using the Azure Active Directory PowerShell for Graph module.</span></span>
    
  ```
   Connect-AzureAD -Credential $credential
  ```
  
  <span data-ttu-id="30cc0-138">또는 Microsoft Azure Active Directory 모듈에 대 한 Windows PowerShell 모듈을 사용 하는 경우에이 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="30cc0-138">Alternately, if you are using the Microsoft Azure Active Directory Module for Windows PowerShell module, run this command.</span></span>
      
  ```
   Connect-MsolService -Credential $credential
 ```

4. <span data-ttu-id="30cc0-p106">SharePoint Online에 연결 하려면 다음이 명령을 실행 합니다. 교체 _ \<domainhost >_ 도메인에 대 한 실제 값입니다. 예: "litwareinc.onmicrosoft.com"는 _ \<domainhost >_ 값은 "litwareinc"입니다.</span><span class="sxs-lookup"><span data-stu-id="30cc0-p106">Run these commands to connect to SharePoint Online. Replace  _\<domainhost>_ with the actual value for your domain. For example, for "litwareinc.onmicrosoft.com", the  _\<domainhost>_ value is "litwareinc".</span></span>
    
  ```
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. <span data-ttu-id="30cc0-p107">비즈니스 온라인 용 Skype 연결에 다음이 명령을 실행 합니다. 증가 하는 방법에 대 한 경고는 `WSMan NetworkDelayms` 값 처음으로 예상 되는 연결 하 고 무시 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="30cc0-p107">Run these commands to connect to Skype for Business Online. A warning about increasing the `WSMan NetworkDelayms` value is expected the first time you connect and should be ignored.</span></span>
    
  ```
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. <span data-ttu-id="30cc0-144">Exchange Online에 연결 하려면 다음이 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="30cc0-144">Run these commands to connect to Exchange Online.</span></span>
    
  ```
  $exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $exchangeSession
  ```

7. <span data-ttu-id="30cc0-145">보안에 연결 하려면 다음이 명령을 실행 &amp; 준수 센터입니다.</span><span class="sxs-lookup"><span data-stu-id="30cc0-145">Run these commands to connect to the Security &amp; Compliance Center.</span></span>
    
  ```
  $SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $SccSession -Prefix cc
  ```

<span data-ttu-id="30cc0-p108">다음 그래프 모듈에 대 한 Active Directory Azure PowerShell을 사용 하는 경우 단일 블록에 있는 모든 명령을입니다. 사용자 도메인 호스트의 이름을 지정 하 고 모두 한번에 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="30cc0-p108">Here are all the commands in a single block when using the Azure Active Directory PowerShell for Graph module. Specify the name of your domain host, and then run them all at one time.</span></span>
  
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

<span data-ttu-id="30cc0-p109">또는 다음은 모든 명령 단일 블록의 Microsoft Azure Active Directory 모듈에 대 한 Windows PowerShell 모듈을 사용 하는 경우입니다. 사용자 도메인 호스트의 이름을 지정 하 고 모두 한번에 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="30cc0-p109">Alternately, here are all the commands in a single block when using the Microsoft Azure Active Directory Module for Windows PowerShell module. Specify the name of your domain host, and then run them all at one time.</span></span>
  
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

<span data-ttu-id="30cc0-150">비즈니스 Online, Exchange Online, SharePoint Online 및 보안에 대 한 활성 세션 Skype 제거 하려면이 명령을 실행 하는 Windows PowerShell 창을 닫아야 준비가 되 면 &amp; 준수 센터:</span><span class="sxs-lookup"><span data-stu-id="30cc0-150">When you are ready to close down the Windows PowerShell window, run this command to remove the active sessions to Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center:</span></span>
  
```
Remove-PSSession $sfboSession ; Remove-PSSession $exchangeSession ; Remove-PSSession $SccSession ; Disconnect-SPOService
```

## <a name="connection-steps-when-using-multi-factor-authentication"></a><span data-ttu-id="30cc0-151">연결 단계 다단계 인증을 사용 하는 경우</span><span class="sxs-lookup"><span data-stu-id="30cc0-151">Connection steps when using multi-factor authentication</span></span>
<span data-ttu-id="30cc0-152"><a name="ConnStepsMFA"> </a></span><span class="sxs-lookup"><span data-stu-id="30cc0-152"></span></span>

<span data-ttu-id="30cc0-p110">Azure AD에 연결 하는 단일 블록에서 모든 명령을 사항은 SharePoint Online 및 Buiness 다단계 인증을 사용 하 여 단일 창에서에 대 한 Skype 합니다. 전역 관리자 계정의 사용자 계정 이름 (UPN) 이름 및 도메인 호스트 이름을 지정 하 고 모두 한번에 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="30cc0-p110">Here are all the commands in a single block to connect to Azure AD, SharePoint Online, and Skype for Buiness using multi-factor authentication in a single window. Specify the user principal name (UPN) name of a global administrator account and your domain host name, and then run them all at one time.</span></span>

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

<span data-ttu-id="30cc0-155">또는 Microsoft Azure Active Directory 모듈에 대 한 Windows PowerShell 모듈을 사용 하는 경우 모든 명령을 같습니다.</span><span class="sxs-lookup"><span data-stu-id="30cc0-155">Alternately, here are all the commands when using the Microsoft Azure Active Directory Module for Windows PowerShell module.</span></span>

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

<span data-ttu-id="30cc0-156">Exchange Online 및 보안에 대 한 &amp; 준수 센터 다단계 인증을 사용 하 여 연결 하려면 다음 항목을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="30cc0-156">For Exchange Online and the Security &amp; Compliance Center, see the following topics to connect using multi-factor authentication:</span></span>

- [<span data-ttu-id="30cc0-157">다단계 인증을 사용 하 여 Exchange Online PowerShell에 연결</span><span class="sxs-lookup"><span data-stu-id="30cc0-157">Connect to Exchange Online PowerShell using multi-factor authentication</span></span>](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell)
- [<span data-ttu-id="30cc0-158">Office 365 보안 및 규정 준수 센터 PowerShell 다단계 인증을 사용 하 여 연결</span><span class="sxs-lookup"><span data-stu-id="30cc0-158">Connect to Office 365 Security & Compliance Center PowerShell using multi-factor authentication</span></span>](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps)
 
<span data-ttu-id="30cc0-159">두 경우 모두 사항에 유의 Exchange Online 원격 PowerShell 모듈의 별도 세션을 사용 하 여 연결 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="30cc0-159">Note that in both cases, you must connect using separate sessions of the Exchange Online Remote PowerShell Module.</span></span>


## <a name="new-to-office-365"></a><span data-ttu-id="30cc0-160">Office 365의 새로운 기능</span><span class="sxs-lookup"><span data-stu-id="30cc0-160">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a><span data-ttu-id="30cc0-161">참고 항목</span><span class="sxs-lookup"><span data-stu-id="30cc0-161">See also</span></span>

- [<span data-ttu-id="30cc0-162">PowerShell Office 365에 연결</span><span class="sxs-lookup"><span data-stu-id="30cc0-162">Connect to Office 365 PowerShell</span></span>](connect-to-office-365-powershell.md)
- [<span data-ttu-id="30cc0-163">Office 365 PowerShell을 사용하여 SharePoint Online 관리</span><span class="sxs-lookup"><span data-stu-id="30cc0-163">Manage SharePoint Online with Office 365 PowerShell</span></span>](manage-sharepoint-online-with-office-365-powershell.md)
- [<span data-ttu-id="30cc0-164">사용자 계정 및 Office 365 PowerShell을 사용 하 여 라이센스 관리</span><span class="sxs-lookup"><span data-stu-id="30cc0-164">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="30cc0-165">Office 365에서 Windows PowerShell을 사용하여 보고서 만들기</span><span class="sxs-lookup"><span data-stu-id="30cc0-165">Use Windows PowerShell to create reports in Office 365</span></span>](use-windows-powershell-to-create-reports-in-office-365.md)
