---
title: 단일 Windows PowerShell 창에서 모든 Office 365 서비스에 연결 합니다.
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/04/2018
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
ms.openlocfilehash: ccd8ed1dc53d306aa77d79ac0270f5bd24dd9298
ms.sourcegitcommit: 21cc62118b78b76d16ef12e2c3eff2c0c789e3d0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/05/2018
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a><span data-ttu-id="b1ca8-103">단일 Windows PowerShell 창에서 모든 Office 365 서비스에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1ca8-103">Connect to all Office 365 services in a single Windows PowerShell window</span></span>

 <span data-ttu-id="b1ca8-104">**요약:** 별도 PowerShell 콘솔 창에서 다른 Office 365 서비스를 관리 하는 대신 모든 Office 365 서비스에 연결할 수 있으며 해당 단일 콘솔 창에서 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1ca8-104">**Summary:** Instead of managing different Office 365 services in separate PowerShell console windows, you can connect to all Office 365 services and manage them from single console window.</span></span>
  
<span data-ttu-id="b1ca8-p101">PowerShell을 사용 하 여 Office 365를 관리 하는 Office 365 관리 센터, SharePoint Online, Exchange Online, 비즈니스 온라인 용 Skype 및 보안 &amp;준수 센터입니다. 별도 Windows PowerShell 세션에 다섯 개의 서로 다른 연결 메서드를 통해 사용자의 데스크톱은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b1ca8-p101">When you use PowerShell to manage Office 365, it is possible to have up to five different Windows PowerShell sessions open at the same time corresponding to Office 365 admin center, SharePoint Online, Exchange Online, Skype for Business Online, and the Security &amp; Compliance Center. With five different connection methods in separate Windows PowerShell sessions, your desktop could look like this:</span></span>
  
![동시에 실행되는 5개의 Windows PowerShell 콘솔](images/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
<span data-ttu-id="b1ca8-p102">이 교차 서비스 관리에 대 한 이러한 5 개의 창 사이에서 데이터를 교환할 수 없습니다 때문에 Office 365를 관리 하기 위한 최적의있지 않습니다. 이 항목에서는 Office 365, 비즈니스 Online, Exchange Online, SharePoint Online 용 Skype 및 보안을 관리할 수 있는 Windows PowerShell의 단일 인스턴스를 사용 하는 방법을 설명 &amp; 준수 센터입니다.</span><span class="sxs-lookup"><span data-stu-id="b1ca8-p102">This is not optimal for managing Office 365 because you can't exchange data among those five windows for cross-service management. This topic describes how to use a single instance of Windows PowerShell from which you can manage Office 365, Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center.</span></span>

>[!Note]
><span data-ttu-id="b1ca8-110">이 문서에는 업데이트 Azure Active Directory V2 PowerShell 모듈을 사용 하 게 진행 하 고 다단계 인증 (MFA)에.</span><span class="sxs-lookup"><span data-stu-id="b1ca8-110">This article is in the process of being updated to use the Azure Active Directory V2 PowerShell module and for multifactor authentication (MFA).</span></span>
>
  
## <a name="before-you-begin"></a><span data-ttu-id="b1ca8-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="b1ca8-111">Before you begin</span></span>
<span data-ttu-id="b1ca8-112"><a name="BeforeYouBegin"> </a></span><span class="sxs-lookup"><span data-stu-id="b1ca8-112"></span></span>

<span data-ttu-id="b1ca8-113">모든 Office 365에서 Windows PowerShell의 단일 인스턴스를 관리할 수 있습니다를 하기 전에 다음 필수 구성 요소를 고려:</span><span class="sxs-lookup"><span data-stu-id="b1ca8-113">Before you can manage all of Office 365 from a single instance of Windows PowerShell, consider the following prerequisites:</span></span>
  
- <span data-ttu-id="b1ca8-p103">Office 365 작동 또는 학교 계정을 사용 하는 이러한 절차에 대 한 요구를 Office 365 관리자 역할의 구성원 이어야 합니다. 자세한 내용은 [Office 365에 대 한 관리자 역할](https://go.microsoft.com/fwlink/p/?LinkId=532367)을 참조 하십시오. 이 Office 365 PowerShell에 대 한, 다른 모든 Office 365 서비스에 대 한 반드시 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1ca8-p103">The Office 365 work or school account that you use for these procedures needs to be a member of an Office 365 admin role. For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367). This a requirement for Office 365 PowerShell, not necessarily for all other Office 365 services.</span></span>
    
- <span data-ttu-id="b1ca8-117">다음 Windows 버전을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1ca8-117">You can use the following 64-bit versions of Windows:</span></span>
    
  - <span data-ttu-id="b1ca8-118">Windows 10</span><span class="sxs-lookup"><span data-stu-id="b1ca8-118">Windows 10</span></span>
    
  - <span data-ttu-id="b1ca8-119">Windows 8.1 또는 Windows 8</span><span class="sxs-lookup"><span data-stu-id="b1ca8-119">Windows 8.1 or Windows 8</span></span>
    
  - <span data-ttu-id="b1ca8-120">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="b1ca8-120">Windows Server 2016</span></span>
    
  - <span data-ttu-id="b1ca8-121">Windows Server 2012 R2 또는 Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="b1ca8-121">Windows Server 2012 R2 or Windows Server 2012</span></span>
    
  - <span data-ttu-id="b1ca8-122">Windows 7 SP1(서비스 팩 1)\*</span><span class="sxs-lookup"><span data-stu-id="b1ca8-122">Windows 7 Service Pack 1 (SP1)\*</span></span>
    
  - <span data-ttu-id="b1ca8-123">Windows Server 2008 R2 SP1\*</span><span class="sxs-lookup"><span data-stu-id="b1ca8-123">Windows Server 2008 R2 SP1\*</span></span>
    
    * <span data-ttu-id="b1ca8-p104">Microsoft.NET Framework 4.5를 설치 해야 합니다. *x* 하 고 다음 중 하나는 Windows Management Framework 3.0 또는 Windows 관리 프레임 워크 4.0 합니다. 자세한 내용은 [.NET Framework를 설치](https://go.microsoft.com/fwlink/p/?LinkId=257868) 하 고 [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) 또는 [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="b1ca8-p104">You need to install the Microsoft .NET Framework 4.5.*x* and then either the Windows Management Framework 3.0 or the Windows Management Framework 4.0. For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) and [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) or [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span></span>
    
    <span data-ttu-id="b1ca8-126">비즈니스 온라인 모듈 및 Office 365 모듈 중 하나는 Skype에 대 한 요구 사항으로 인해 64 비트 버전의 Windows 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1ca8-126">You need to use a 64-bit version of Windows because of the requirements for the Skype for Business Online module and one of the Office 365 modules.</span></span>
    
- <span data-ttu-id="b1ca8-127">Office 365, SharePoint Online 및 비즈니스 온라인 용 Skype에 필요한 모듈을 설치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1ca8-127">You need to install the modules that are required for Office 365, SharePoint Online, and Skype for Business Online:</span></span>
    
   - [<span data-ttu-id="b1ca8-128">Microsoft 온라인 서비스 로그인 도우미 IT 전문가 위한 RTW</span><span class="sxs-lookup"><span data-stu-id="b1ca8-128">Microsoft Online Service Sign-in Assistant for IT Professionals RTW</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=286152)
   - <span data-ttu-id="b1ca8-129">Windows Azure Active Directory 모듈에 대 한 Windows PowerShell (64 비트 버전)는 상승 된 PowerShell 명령 프롬프트에서 **설치 모듈 MSOnline** 명령 사용 하 여 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1ca8-129">Windows Azure Active Directory Module for Windows PowerShell (64-bit version) with the **Install-Module MSOnline** command at an elevated PowerShell command prompt.</span></span>
   - [<span data-ttu-id="b1ca8-130">SharePoint Online 관리 셸</span><span class="sxs-lookup"><span data-stu-id="b1ca8-130">SharePoint Online Management Shell</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [<span data-ttu-id="b1ca8-131">온라인으로 비즈니스 Windows PowerShell 모듈에 대 한 Skype</span><span class="sxs-lookup"><span data-stu-id="b1ca8-131">Skype for Business Online, Windows PowerShell Module</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532439)
    
-  <span data-ttu-id="b1ca8-p105">Windows PowerShell 스크립트를 실행 하려면 서명 된 Skype에 대 한 비즈니스 Online, Exchange Online 및 보안에 대 한 구성 해야하는 &amp; 준수 센터입니다. 이 작업을 수행 하려면 관리자 권한으로 Windows PowerShell 세션에서 다음 명령을 실행 ( **관리자 권한으로 실행**을 선택 하 여 열면 Windows PowerShell 창)입니다.</span><span class="sxs-lookup"><span data-stu-id="b1ca8-p105">Windows PowerShell needs to be configured to run signed scripts for Skype for Business Online, Exchange Online, and the Security &amp; Compliance Center. To do this, run the following command in an elevated Windows PowerShell session (a Windows PowerShell window you open by selecting **Run as administrator**).</span></span>
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="connection-steps"></a><span data-ttu-id="b1ca8-134">연결 단계</span><span class="sxs-lookup"><span data-stu-id="b1ca8-134">Connection steps</span></span>
<span data-ttu-id="b1ca8-135"><a name="BeforeYouBegin"> </a></span><span class="sxs-lookup"><span data-stu-id="b1ca8-135"></span></span>

<span data-ttu-id="b1ca8-136">단일 PowerShell 창에서 모든 서비스에 연결 하는 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b1ca8-136">Here are the steps to connect to all the services in a single PowerShell window.</span></span>
  
1. <span data-ttu-id="b1ca8-137">관리자 권한 ( **관리자 권한으로 실행**하는 사용)으로 Windows PowerShell을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="b1ca8-137">Open Windows PowerShell as an administrator (use **Run as administrator**).</span></span>
    
2. <span data-ttu-id="b1ca8-138">이 명령을 실행 하 고 Office 365 작업 시간을 입력 하거나 계정 자격 증명을 학교 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1ca8-138">Run this command, and enter your Office 365 work or school account credentials.</span></span>
    
  ```
  $credential = Get-Credential
  ```

3. <span data-ttu-id="b1ca8-139">Office 365에 연결 하려면 다음이 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1ca8-139">Run these commands to connect to Office 365.</span></span>
    
  ```
  Import-Module MsOnline
  Connect-MsolService -Credential $credential
  ```

4. <span data-ttu-id="b1ca8-p106">SharePoint Online에 연결 하려면 다음이 명령을 실행 합니다. 교체 _ \<domainhost >_ 도메인에 대 한 실제 값입니다. 예: `litwareinc.onmicrosoft.com`는 _ \<domainhost >_ 값은 `litwareinc`합니다.</span><span class="sxs-lookup"><span data-stu-id="b1ca8-p106">Run these commands to connect to SharePoint Online. Replace  _\<domainhost>_ with the actual value for your domain. For example, for `litwareinc.onmicrosoft.com`, the  _\<domainhost>_ value is `litwareinc`.</span></span>
    
  ```
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. <span data-ttu-id="b1ca8-p107">비즈니스 온라인 용 Skype 연결에 다음이 명령을 실행 합니다. 증가 하는 방법에 대 한 경고는 `WSMan NetworkDelayms` 값 처음으로 예상 되는 연결 하 고 무시 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1ca8-p107">Run these commands to connect to Skype for Business Online. A warning about increasing the `WSMan NetworkDelayms` value is expected the first time you connect and should be ignored.</span></span>
    
  ```
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. <span data-ttu-id="b1ca8-145">Exchange Online에 연결 하려면 다음이 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1ca8-145">Run these commands to connect to Exchange Online.</span></span>
    
  ```
  $exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $exchangeSession -DisableNameChecking
  ```

7. <span data-ttu-id="b1ca8-146">보안에 연결 하려면 다음이 명령을 실행 &amp; 준수 센터입니다.</span><span class="sxs-lookup"><span data-stu-id="b1ca8-146">Run these commands to connect to the Security &amp; Compliance Center.</span></span>
    
  ```
  $ccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication Basic -AllowRedirection
  Import-PSSession $ccSession -Prefix cc
  ```
> [!NOTE]
> <span data-ttu-id="b1ca8-p108">텍스트 접두사 "참조" *모든* 보안에 추가 됩니다 &amp; 준수 센터 cmdlet 이름을 cmdlet를 실행할 수 있도록 Exchange Online 및 보안에 존재 &amp; 같은 Windows PowerShell 세션에서 준수 센터입니다. 예, **Get-rolegroup** 즉시 보안에서 **Get ccRoleGroup** &amp; 준수 센터입니다.</span><span class="sxs-lookup"><span data-stu-id="b1ca8-p108">The text prefix "cc" is added to  *all*  Security &amp; Compliance Center cmdlet names so you can run cmdlets that exist in both Exchange Online and the Security &amp; Compliance Center in the same Windows PowerShell session. For example, **Get-RoleGroup** becomes **Get-ccRoleGroup** in the Security &amp; Compliance Center.</span></span>
  
<span data-ttu-id="b1ca8-p109">단일 블록에 있는 모든 명령을 다음과 같습니다. 사용자 도메인 호스트의 이름을 지정 하 고 모두 한번에 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1ca8-p109">Here are all the commands in a single block. Specify the name of your domain host, and then run them all at one time.</span></span>
  
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
<span data-ttu-id="b1ca8-151">비즈니스 Online, Exchange Online, SharePoint Online 및 보안에 대 한 활성 세션 Skype 제거 하려면이 명령을 실행 하는 Windows PowerShell 창을 닫아야 준비가 되 면 &amp; 준수 센터:</span><span class="sxs-lookup"><span data-stu-id="b1ca8-151">When you are ready to close down the Windows PowerShell window, run this command to remove the active sessions to Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center:</span></span>
  
```
Remove-PSSession $sfboSession ; Remove-PSSession $exchangeSession ; Remove-PSSession $ccSession ; Disconnect-SPOService
```

## <a name="new-to-office-365"></a><span data-ttu-id="b1ca8-152">Office 365의 새로운 기능</span><span class="sxs-lookup"><span data-stu-id="b1ca8-152">New to Office 365?</span></span>
<span data-ttu-id="b1ca8-153"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="b1ca8-153"></span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a><span data-ttu-id="b1ca8-154">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b1ca8-154">See also</span></span>

- [<span data-ttu-id="b1ca8-155">Office 365 PowerShell 사용한 Office 365 관리</span><span class="sxs-lookup"><span data-stu-id="b1ca8-155">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="b1ca8-156">Office 365 PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="b1ca8-156">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
- [<span data-ttu-id="b1ca8-157">Office 365 PowerShell을 사용하여 SharePoint Online 관리</span><span class="sxs-lookup"><span data-stu-id="b1ca8-157">Manage SharePoint Online with Office 365 PowerShell</span></span>](manage-sharepoint-online-with-office-365-powershell.md)
- [<span data-ttu-id="b1ca8-158">사용자 계정 및 Office 365 PowerShell을 사용 하 여 라이센스 관리</span><span class="sxs-lookup"><span data-stu-id="b1ca8-158">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="b1ca8-159">Office 365에서 Windows PowerShell을 사용하여 보고서 만들기</span><span class="sxs-lookup"><span data-stu-id="b1ca8-159">Use Windows PowerShell to create reports in Office 365</span></span>](use-windows-powershell-to-create-reports-in-office-365.md)
