---
title: 단일 Windows PowerShell 창에서 모든 Office 365 서비스에 연결 합니다.
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/28/2019
audience: ITPro
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
description: '요약: 단일 Windows PowerShell 창에서 모든 Office 365 서비스에 Windows PowerShell을 연결 합니다.'
ms.openlocfilehash: ae9487f48439c6f8d98f927c610e5f2af4c1b361
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069184"
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a><span data-ttu-id="25212-103">단일 Windows PowerShell 창에서 모든 Office 365 서비스에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="25212-103">Connect to all Office 365 services in a single Windows PowerShell window</span></span>

 <span data-ttu-id="25212-104">**요약:** 별도의 PowerShell 콘솔 창에서 서로 다른 Office 365 서비스를 관리 하는 대신, 모든 Office 365 서비스에 연결 하 여 단일 콘솔 창의 관리를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25212-104">**Summary:** Instead of managing different Office 365 services in separate PowerShell console windows, you can connect to all Office 365 services and manage them from single console window.</span></span>
  
<span data-ttu-id="25212-105">PowerShell을 사용 하 여 Office 365을 관리 하는 경우 Microsoft 365 관리 센터, SharePoint Online, Exchange Online, 비즈니스용 Skype Online 및 보안에 해당 하는 Windows PowerShell 세션이 최대 5 개까지 있을 수 있습니다. &amp; 준수 센터</span><span class="sxs-lookup"><span data-stu-id="25212-105">When you use PowerShell to manage Office 365, it is possible to have up to five different Windows PowerShell sessions open at the same time corresponding to Microsoft 365 admin center, SharePoint Online, Exchange Online, Skype for Business Online, and the Security &amp; Compliance Center.</span></span> <span data-ttu-id="25212-106">별도의 Windows PowerShell 세션에서 5 가지 서로 다른 연결 방법을 사용 하는 경우 데스크톱은 다음과 같이 표시 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25212-106">With five different connection methods in separate Windows PowerShell sessions, your desktop could look like this:</span></span>
  
![동시에 실행되는 5개의 Windows PowerShell 콘솔](media/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
<span data-ttu-id="25212-108">서비스 간 관리를 위해 이러한 5 개의 창 간에 데이터를 교환할 수 없으므로 Office 365을 관리 하는 것이 최적이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="25212-108">This is not optimal for managing Office 365 because you can't exchange data among those five windows for cross-service management.</span></span> <span data-ttu-id="25212-109">이 항목에서는 Office 365, 비즈니스용 Skype Online, Exchange Online, SharePoint Online, 보안 &amp; 및 준수 센터를 관리할 수 있는 Windows PowerShell의 단일 인스턴스를 사용 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="25212-109">This topic describes how to use a single instance of Windows PowerShell from which you can manage Office 365, Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center.</span></span>

>[!Note]
><span data-ttu-id="25212-110">이 문서에는 현재 Office 365 전 세계 (+ GCC) 클라우드에 연결 하는 명령만 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25212-110">This article currently only contains the commands to connect to the Office 365 Worldwide (+GCC) cloud.</span></span> <span data-ttu-id="25212-111">추가 참고 사항에는 다른 Office 365 클라우드에 연결에 대 한 정보가 포함 된 문서 링크가 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="25212-111">Additional notes provide links to articles with information about connecting to the other Office 365 clouds.</span></span>
>

## <a name="before-you-begin"></a><span data-ttu-id="25212-112">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="25212-112">Before you begin</span></span>

<span data-ttu-id="25212-113">단일 Windows PowerShell 인스턴스에서 모든 Office 365을 관리 하려면 먼저 다음 필수 구성 요소를 고려 하십시오.</span><span class="sxs-lookup"><span data-stu-id="25212-113">Before you can manage all of Office 365 from a single instance of Windows PowerShell, consider the following prerequisites:</span></span>
  
- <span data-ttu-id="25212-114">이러한 절차에 사용하는 Office 365회사 또는 학교 계정은 Office 365 관리자 역할의 구성원이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="25212-114">The Office 365 work or school account that you use for these procedures needs to be a member of an Office 365 admin role.</span></span> <span data-ttu-id="25212-115">자세한 내용은 [Office 365 관리자 역할 정보](https://go.microsoft.com/fwlink/p/?LinkId=532367)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="25212-115">For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span></span> <span data-ttu-id="25212-116">이는 Office 365 PowerShell에 대 한 요구 사항으로, 다른 모든 Office 365 서비스에 꼭 필요한 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="25212-116">This a requirement for Office 365 PowerShell, not necessarily for all other Office 365 services.</span></span>
    
- <span data-ttu-id="25212-117">다음 Windows 버전을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25212-117">You can use the following 64-bit versions of Windows:</span></span>
    
  - <span data-ttu-id="25212-118">Windows 10</span><span class="sxs-lookup"><span data-stu-id="25212-118">Windows 10</span></span>
    
  - <span data-ttu-id="25212-119">Windows 8.1 또는 Windows 8</span><span class="sxs-lookup"><span data-stu-id="25212-119">Windows 8.1 or Windows 8</span></span>
    
  - <span data-ttu-id="25212-120">Windows Server 2019</span><span class="sxs-lookup"><span data-stu-id="25212-120">Windows Server 2019</span></span>
    
  - <span data-ttu-id="25212-121">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="25212-121">Windows Server 2016</span></span>
    
  - <span data-ttu-id="25212-122">Windows Server 2012 R2 또는 Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="25212-122">Windows Server 2012 R2 or Windows Server 2012</span></span>
    
  - <span data-ttu-id="25212-123">Windows 7 SP1(서비스 팩 1)\*</span><span class="sxs-lookup"><span data-stu-id="25212-123">Windows 7 Service Pack 1 (SP1)\*</span></span>
    
  - <span data-ttu-id="25212-124">Windows Server 2008 R2 SP1\*</span><span class="sxs-lookup"><span data-stu-id="25212-124">Windows Server 2008 R2 SP1\*</span></span>
    
    <span data-ttu-id="25212-125">\*Microsoft .NET Framework 4.5를 설치 해야 합니다. *x* 를 누른 다음 Windows management framework 3.0 또는 Windows management framework 4.0 중 하나를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="25212-125">\* You need to install the Microsoft .NET Framework 4.5.*x* and then either the Windows Management Framework 3.0 or the Windows Management Framework 4.0.</span></span> <span data-ttu-id="25212-126">자세한 내용은 [.Net Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) 및 [windows management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) 또는 [Windows management framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344)설치를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="25212-126">For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) and [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) or [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span></span>
    
    <span data-ttu-id="25212-127">비즈니스용 Skype Online 모듈 및 Office 365 모듈 중 하나에 대 한 요구 사항으로 인해 64 비트 버전의 Windows를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="25212-127">You need to use a 64-bit version of Windows because of the requirements for the Skype for Business Online module and one of the Office 365 modules.</span></span>
    
- <span data-ttu-id="25212-128">Azure AD, SharePoint Online 및 비즈니스용 Skype Online에 필요한 모듈을 설치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="25212-128">You need to install the modules that are required for Azure AD, SharePoint Online, and Skype for Business Online:</span></span>
    
   - [<span data-ttu-id="25212-129">Azure Active Directory V2</span><span class="sxs-lookup"><span data-stu-id="25212-129">Azure Active Directory V2</span></span>](connect-to-office-365-powershell.md##connect-with-the-azure-active-directory-powershell-for-graph-module)
   - [<span data-ttu-id="25212-130">SharePoint Online 관리 셸</span><span class="sxs-lookup"><span data-stu-id="25212-130">SharePoint Online Management Shell</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [<span data-ttu-id="25212-131">비즈니스용 Skype Online, Windows PowerShell 모듈</span><span class="sxs-lookup"><span data-stu-id="25212-131">Skype for Business Online, Windows PowerShell Module</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532439)
    
-  <span data-ttu-id="25212-132">비즈니스용 Skype Online, Exchange Online 및 보안 &amp; 및 준수 센터에 대해 서명 된 스크립트를 실행 하도록 Windows PowerShell을 구성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="25212-132">Windows PowerShell needs to be configured to run signed scripts for Skype for Business Online, Exchange Online, and the Security &amp; Compliance Center.</span></span> <span data-ttu-id="25212-133">이 작업을 수행 하려면 **관리자 권한으로 실행**을 선택 하 여 연 windows powershell 창에서 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="25212-133">To do this, run the following command in an elevated Windows PowerShell session (a Windows PowerShell window you open by selecting **Run as administrator**).</span></span>
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="connection-steps-when-using-a-password"></a><span data-ttu-id="25212-134">암호를 사용할 때의 연결 단계</span><span class="sxs-lookup"><span data-stu-id="25212-134">Connection steps when using a password</span></span>

<span data-ttu-id="25212-135">단일 PowerShell 창에서 모든 서비스에 연결 하는 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="25212-135">Here are the steps to connect to all the services in a single PowerShell window.</span></span>
  
1. <span data-ttu-id="25212-136">관리자 권한으로 Windows PowerShell을 엽니다 ( **관리자 권한으로 실행**사용).</span><span class="sxs-lookup"><span data-stu-id="25212-136">Open Windows PowerShell as an administrator (use **Run as administrator**).</span></span>
    
2. <span data-ttu-id="25212-137">이 명령을 실행 하 고 Office 365 회사 또는 학교 계정 자격 증명을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="25212-137">Run this command, and enter your Office 365 work or school account credentials.</span></span>
    
  ```
  $credential = Get-Credential
  ```

3. <span data-ttu-id="25212-138">이 명령을 실행 하 여 Graph 모듈에 대 한 Azure Active Directory PowerShell을 사용 하 여 Azure AD (Active Directory)에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="25212-138">Run this command to connect to Azure Active Directory (AD) using the Azure Active Directory PowerShell for Graph module.</span></span>
    
  ```
  Connect-AzureAD -Credential $credential
  ```
  
  <span data-ttu-id="25212-139">또는 Windows PowerShell 모듈에 대 한 Microsoft Azure Active Directory 모듈을 사용 하는 경우에는이 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="25212-139">Alternately, if you are using the Microsoft Azure Active Directory Module for Windows PowerShell module, run this command.</span></span>
      
  ```
  Connect-MsolService -Credential $credential
 ```

4. <span data-ttu-id="25212-140">다음 명령을 실행 하 여 SharePoint Online에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="25212-140">Run these commands to connect to SharePoint Online.</span></span> <span data-ttu-id="25212-141">_ \<Domainhost>_ 를 도메인의 실제 값으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="25212-141">Replace  _\<domainhost>_ with the actual value for your domain.</span></span> <span data-ttu-id="25212-142">예를 들어 "litwareinc.onmicrosoft.com"의 경우 _ \<domainhost>_ 값은 "litwareinc"입니다.</span><span class="sxs-lookup"><span data-stu-id="25212-142">For example, for "litwareinc.onmicrosoft.com", the  _\<domainhost>_ value is "litwareinc".</span></span>
    
  ```
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. <span data-ttu-id="25212-143">다음 명령을 실행 하 여 비즈니스용 Skype Online에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="25212-143">Run these commands to connect to Skype for Business Online.</span></span> <span data-ttu-id="25212-144">처음 연결할 때 `WSMan NetworkDelayms` 값을 늘리는 경고는 예상 되며 무시 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="25212-144">A warning about increasing the `WSMan NetworkDelayms` value is expected the first time you connect and should be ignored.</span></span>
    
  ```
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. <span data-ttu-id="25212-145">다음 명령을 실행 하 여 Exchange Online에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="25212-145">Run these commands to connect to Exchange Online.</span></span>
    
  ```
  $exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $exchangeSession -DisableNameChecking
  ```

>[!Note]
><span data-ttu-id="25212-146">전 세계 이외의 Office 365 클라우드에서 Exchange Online에 연결 하려면 [Exchange Online PowerShell에 연결](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="25212-146">To connect to Exchange Online for Office 365 clouds other than Worldwide, see [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span></span>
>

7. <span data-ttu-id="25212-147">보안 &amp; 및 준수 센터에 연결 하려면 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="25212-147">Run these commands to connect to the Security &amp; Compliance Center.</span></span>
    
  ```
  $SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $SccSession -Prefix cc
  ```

>[!Note]
><span data-ttu-id="25212-148">전 세계 이외의 Office 365 &amp; 클라우드의 보안 및 준수 센터에 연결 하려면 [연결에 Office 365 Security _AMP_ 준수 센터 PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="25212-148">To connect to the Security &amp; Compliance Center for Office 365 clouds other than Worldwide, see [Connect to Office 365 Security & Compliance Center PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).</span></span>
>

<span data-ttu-id="25212-149">다음은 Graph 모듈에 대 한 Azure Active Directory PowerShell을 사용할 때 단일 블록에 있는 모든 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="25212-149">Here are all the commands in a single block when using the Azure Active Directory PowerShell for Graph module.</span></span> <span data-ttu-id="25212-150">도메인 호스트의 이름을 지정 하 고 한 번에 모두 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="25212-150">Specify the name of your domain host, and then run them all at one time.</span></span>
  
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

<span data-ttu-id="25212-151">다음에는 Windows PowerShell 용 Microsoft Azure Active Directory 모듈 모듈을 사용할 때 단일 블록에 있는 모든 명령이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25212-151">Alternately, here are all the commands in a single block when using the Microsoft Azure Active Directory Module for Windows PowerShell module.</span></span> <span data-ttu-id="25212-152">도메인 호스트의 이름을 지정 하 고 한 번에 모두 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="25212-152">Specify the name of your domain host, and then run them all at one time.</span></span>
  
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

<span data-ttu-id="25212-153">Windows PowerShell 창을 종료할 준비가 되 면 다음 명령을 실행 하 여 비즈니스용 Skype Online, Exchange Online, SharePoint Online 및 보안 &amp; 및 준수 센터에 대 한 활성 세션을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="25212-153">When you are ready to close down the Windows PowerShell window, run this command to remove the active sessions to Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center:</span></span>
  
```
Remove-PSSession $sfboSession ; Remove-PSSession $exchangeSession ; Remove-PSSession $SccSession ; Disconnect-SPOService
```

## <a name="connection-steps-when-using-multi-factor-authentication"></a><span data-ttu-id="25212-154">다단계 인증을 사용 하는 경우의 연결 단계</span><span class="sxs-lookup"><span data-stu-id="25212-154">Connection steps when using multi-factor authentication</span></span>

<span data-ttu-id="25212-155">다음은 Graph 모듈에 대 한 Azure Active Directory PowerShell을 사용 하 여 단일 창에서 Azure AD, SharePoint Online 및 Buiness 비즈니스용 Skype에 연결 하는 모든 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="25212-155">Here are all the commands in a single block to connect to Azure AD, SharePoint Online, and Skype for Buiness using multi-factor authentication in a single window using the Azure Active Directory PowerShell for Graph module.</span></span> <span data-ttu-id="25212-156">사용자 계정의 UPN (사용자 계정 이름) 이름과 도메인 호스트 이름을 지정한 다음 한 번에 모두 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="25212-156">Specify the user principal name (UPN) name of a user account and your domain host name, and then run them all at one time.</span></span>

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

<span data-ttu-id="25212-157">다음에는 Windows PowerShell 용 Microsoft Azure Active Directory 모듈 모듈을 사용할 때의 모든 명령이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25212-157">Alternately, here are all the commands when using the Microsoft Azure Active Directory Module for Windows PowerShell module.</span></span>

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

<span data-ttu-id="25212-158">Exchange Online 및 보안 &amp; 및 준수 센터에 대해 multi-factor authentication을 사용 하 여 연결 하려면 다음 항목을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="25212-158">For Exchange Online and the Security &amp; Compliance Center, see the following topics to connect using multi-factor authentication:</span></span>

- [<span data-ttu-id="25212-159">다단계 인증을 사용하여 Exchange Online PowerShell에 연결</span><span class="sxs-lookup"><span data-stu-id="25212-159">Connect to Exchange Online PowerShell using multi-factor authentication</span></span>](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell)
- [<span data-ttu-id="25212-160">다단계 인증을 사용 하 여 Office 365 보안 & 준수 센터 PowerShell에 연결</span><span class="sxs-lookup"><span data-stu-id="25212-160">Connect to Office 365 Security & Compliance Center PowerShell using multi-factor authentication</span></span>](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps)
 
<span data-ttu-id="25212-161">두 경우 모두 Exchange Online 원격 PowerShell 모듈의 개별 세션을 사용 하 여 연결 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="25212-161">Note that in both cases, you must connect using separate sessions of the Exchange Online Remote PowerShell Module.</span></span>


## <a name="see-also"></a><span data-ttu-id="25212-162">참고 항목</span><span class="sxs-lookup"><span data-stu-id="25212-162">See also</span></span>

- [<span data-ttu-id="25212-163">PowerShell Office 365에 연결</span><span class="sxs-lookup"><span data-stu-id="25212-163">Connect to Office 365 PowerShell</span></span>](connect-to-office-365-powershell.md)
- [<span data-ttu-id="25212-164">Office 365 PowerShell을 사용하여 SharePoint Online 관리</span><span class="sxs-lookup"><span data-stu-id="25212-164">Manage SharePoint Online with Office 365 PowerShell</span></span>](manage-sharepoint-online-with-office-365-powershell.md)
- [<span data-ttu-id="25212-165">사용자 계정 및 Office 365 PowerShell을 사용 하 여 라이센스 관리</span><span class="sxs-lookup"><span data-stu-id="25212-165">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="25212-166">Office 365에서 Windows PowerShell을 사용하여 보고서 만들기</span><span class="sxs-lookup"><span data-stu-id="25212-166">Use Windows PowerShell to create reports in Office 365</span></span>](use-windows-powershell-to-create-reports-in-office-365.md)
