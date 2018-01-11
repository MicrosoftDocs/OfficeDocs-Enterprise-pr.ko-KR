---
title: "DAP(위임된 액세스 권한) 파트너용 원격 Windows PowerShell을 사용하여 Exchange Online 테넌트에 연결"
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: 
ms.assetid: ae5f1a87-8b77-4f93-a1b8-56f800aeb283
description: "요약:DelegatedOrg 매개 변수를 사용하여 Exchange Online에 연결하도록 원격 Windows PowerShell을 사용합니다."
ms.openlocfilehash: 857c97e5d3374f293b98298419932af4ce2dfa19
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/11/2018
---
# <a name="connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="7f66a-103">DAP(위임된 액세스 권한) 파트너용 원격 Windows PowerShell을 사용하여 Exchange Online 테넌트에 연결</span><span class="sxs-lookup"><span data-stu-id="7f66a-103">Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

 <span data-ttu-id="7f66a-104">**요약:** _DelegatedOrg_ 매개 변수를 사용하여 Exchange Online에 연결하도록 원격 Windows PowerShell을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7f66a-104">**Summary:** Use remote Windows PowerShell to connect to Exchange Online by using the _DelegatedOrg_ parameter.</span></span>
  
<span data-ttu-id="7f66a-p101">원격 Windows PowerShell을 통해 명령줄에서 Exchange Online 설정을 관리할 수 있습니다. 로컬 컴퓨터에서 Windows PowerShell을 사용하여 원격 세션을 Exchange Online에 만듭니다. Exchange Online 자격 증명을 입력하고, 필수 연결 설정을 제공한 다음, 사용할 수 있도록 Exchange Online cmdlet을 로컬 Windows PowerShell 세션으로 가져오는 3단계 프로세스입니다.</span><span class="sxs-lookup"><span data-stu-id="7f66a-p101">Remote Windows PowerShell lets you manage your Exchange Online settings from the command line. You use Windows PowerShell on your local computer to create a remote session to Exchange Online. It's a three-step process where you enter your Exchange Online credentials, provide the required connection settings, and then import the Exchange Online cmdlets into your local Windows PowerShell session so that you can use them.</span></span>
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="7f66a-108">시작하기 전에 알아야 할 내용</span><span class="sxs-lookup"><span data-stu-id="7f66a-108">What do you need to know before you begin?</span></span>

- <span data-ttu-id="7f66a-109">예상 완료 시간: 5분</span><span class="sxs-lookup"><span data-stu-id="7f66a-109">Estimated time to complete: 5 minutes</span></span>
    
- <span data-ttu-id="7f66a-110">다음 Windows 버전을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f66a-110">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="7f66a-111">Windows 10</span><span class="sxs-lookup"><span data-stu-id="7f66a-111">Windows 10</span></span>
    
  - <span data-ttu-id="7f66a-112">Windows 8.1 또는 Windows 8</span><span class="sxs-lookup"><span data-stu-id="7f66a-112">Windows 8.1 or Windows 8</span></span>
    
  - <span data-ttu-id="7f66a-113">Windows Server 2012 R2 또는 Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="7f66a-113">Windows Server 2012 R2 or Windows Server 2012</span></span>
    
  - <span data-ttu-id="7f66a-114">Windows 7 SP1(서비스 팩 1)\*</span><span class="sxs-lookup"><span data-stu-id="7f66a-114">Windows 7 Service Pack 1 (SP1)\*</span></span>
    
  - <span data-ttu-id="7f66a-115">Windows Server 2008 R2 SP1\*</span><span class="sxs-lookup"><span data-stu-id="7f66a-115">Windows Server 2008 R2 SP1\*</span></span>
    
    * <span data-ttu-id="7f66a-p102">Microsoft .NET Framework 4.5.1 또는 .NET Framework 4.5를 설치한 다음 Windows Management Framework 4.0 또는 Windows Management Framework 3.0을 설치해야 합니다. 자세한 내용은 다음 리소스를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7f66a-p102">You need to install the .NET Framework 4.5.1 or the .NET Framework 4.5 and then either the Windows Management Framework 4.0 or the Windows Management Framework 3.0 . For more information, see the following resources:</span></span>
    
  - [<span data-ttu-id="7f66a-118">.NET Framework 설치</span><span class="sxs-lookup"><span data-stu-id="7f66a-118">Installing the .NET Framework</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=257868)
    
  - <span data-ttu-id="7f66a-119">[Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) 또는[Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344)</span><span class="sxs-lookup"><span data-stu-id="7f66a-119">[Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) or[Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344)</span></span>
    
- <span data-ttu-id="7f66a-120">이 항목에서 절차에 적용할 수도 있는 키보드 바로 가기에 대한 자세한 내용은 [Exchange 관리 센터의 키보드 바로 가기](https://go.microsoft.com/fwlink/p/?LinkId=534017)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7f66a-120">For information about keyboard shortcuts that might apply to the procedures in this topic, see [Keyboard shortcuts in the Exchange admin center](https://go.microsoft.com/fwlink/p/?LinkId=534017).</span></span>
    
## 

> [!IMPORTANT]
> <span data-ttu-id="7f66a-p103">이 절차는위임된 액세스 권한(DAP) 파트너전용입니다. DAP 파트너가 아닌 경우 이 절차를 사용해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7f66a-p103">This procedure is only for Delegated Access Permission (DAP) partners. If you are not a DAP partner, do not use this procedure.</span></span> 
  
<span data-ttu-id="7f66a-p104">DAP 파트너는 신디케이션 및 CSP(클라우드 솔루션 공급자 파트너)입니다. 이러한 공급자는 다른 회사의 네트워크 또는 전자 통신 공급자인 경우가 많습니다. 구독을 고객에 대한 서비스 제공 사항으로 통합합니다. 또한 모든 고객 테넌트를 관리하고 보고할 수 있도록 Office 365고객 테넌트에 대해 AOBO(관리 위임자) 권한이 자동으로 부여되는 파트너 테넌트를 보유합니다.</span><span class="sxs-lookup"><span data-stu-id="7f66a-p104">DAP partners are Syndication and Cloud Solution Providers (CSP) partners. They are frequently network or telecom providers to other companies. They bundle subscriptions into their service offerings to their customers. They own a partner tenancy that is automatically granted Administer On Behalf Of (AOBO) permissions to their Office 365customer tenancies so they can administer and report on all of their customer tenancies.</span></span>
  
## <a name="connect-to-exchange-online"></a><span data-ttu-id="7f66a-127">Exchange Online에 연결</span><span class="sxs-lookup"><span data-stu-id="7f66a-127">Connect to Exchange Online</span></span>

1. <span data-ttu-id="7f66a-128">로컬 컴퓨터에서 Windows PowerShell을 열고 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="7f66a-128">On your local computer, open Windows PowerShell and run the following command.</span></span>
    
  ```
  $UserCredential = Get-Credential
  ```

    <span data-ttu-id="7f66a-129">**Windows PowerShell 자격 증명 요청** 대화 상자에 DAP 관리자 사용자 이름과 암호를 입력한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7f66a-129">In the **Windows PowerShell Credential Request** dialog box, enter your DAP administrator user name and password, and then click **OK**.</span></span>
    
2. <span data-ttu-id="7f66a-130">_<customer tenant domain name>_을 연결하려는 테넌트 도메인의 이름으로 교체하는 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="7f66a-130">Run the following command, replacing  _<customer tenant domain name>_ with the name of the tenant domain that you want to connect to.</span></span>
    
  ```
  $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell-liveid?DelegatedOrg=<customer tenant domain name>-Credential $UserCredential -Authentication Basic -AllowRedirection
  ```

    <span data-ttu-id="7f66a-p105">이 명령에서 중요한 단계는 보고 정보에 액세스하는 고객을 지정하는 것입니다. 초기 도메인 이름의 FQDN을 값으로  _ConnectionURI_ 매개 변수에 제공하는 _DelegatedOrg_ 매개 변수에서 이를 수행합니다. 이는 연결할 끝점인 Exchange Online PowerShell 원격 Windows PowerShell에 대한 원격 Windows PowerShell을 의미합니다. 원격 Windows PowerShell은 보고서가 실행될 때마다 특정 고객의 컨텍스트에 보고되는 Office 365에 연결되어야 합니다. 이 고객이 지정되면 다음과 같은 모든 명령이 해당 고객의 컨텍스트에서 실행됩니다. 이를 통해 파트너는 이 고객에 대해 사용할 수 있는 모든 보고서에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f66a-p105">The key step in this command is specifying which customer to access for the reporting information. You do this in the  _ConnectionURI_ parameter, where you provide the FQDN of the initial domain name as the value to the _DelegatedOrg_ parameter. This tells remote Windows PowerShell for Exchange Online PowerShell remote Windows PowerShell the endpoint to connect to. remote Windows PowerShell must connect to Office 365 reporting in the context of a specific customer each time a report is run. After this customer is specified, all of the following commands are run in the context of that customer. This lets the partner to access all the available reports for this customer.</span></span>
    
3. <span data-ttu-id="7f66a-137">다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="7f66a-137">Run the following command.</span></span>
    
  ```
  Import-PSSession $Session
  ```

> [!NOTE]
> <span data-ttu-id="7f66a-p106">한 계정에 실행할 수 있는 동시 세션은 3개로 제한됩니다. 완료되면 원격 Windows PowerShell 세션의 연결을 끊어야 합니다. 세션 연결을 끊지 않고 Windows PowerShell 창을 닫으면 사용할 수 있는 원격 Windows PowerShell 세션을 전부 써버릴 수 있으며 세션이 만료될 때까지 기다려야 합니다. 원격 Windows PowerShell 세션의 연결을 끊으려면 다음 명령을 실행합니다. >  `Remove-PSSession $Session`</span><span class="sxs-lookup"><span data-stu-id="7f66a-p106">There is a limit of three simultaneous sessions that can run under one account. Be sure to disconnect the remote Windows PowerShell session when you're finished. If you close the Windows PowerShell window without disconnecting the session, you can use up all the remote Windows PowerShell sessions available to you, and you'll need to wait for the sessions to expire. To disconnect the remote Windows PowerShell session, run the following command. >  `Remove-PSSession $Session`</span></span>
  
## <a name="how-do-you-know-this-worked"></a><span data-ttu-id="7f66a-142">작동 여부는 어떻게 확인합니까?</span><span class="sxs-lookup"><span data-stu-id="7f66a-142">How do you know this worked?</span></span>

<span data-ttu-id="7f66a-p107">3단계를 수행하고 나면 Exchange Online cmdlet이 진행률 표시줄을 통해 추적한 대로 로컬 Windows PowerShell 세션으로 가져오기됩니다. 오류가 발생하지 않으면 정상적으로 연결된 것입니다. 빠르게 테스트하려면 Exchange Online cmdlet(예: **Get-Mailbox** )을 실행하여 결과를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="7f66a-p107">After Step 3, the Exchange Online cmdlets are imported into your local Windows PowerShell session as tracked by a progress bar. If you don't receive any errors, you connected successfully. A quick test is to run an Exchange Online cmdlet—for example, **Get-Mailbox** —and see the results.</span></span>
  
<span data-ttu-id="7f66a-146">오류가 발생하면 다음 요구 사항을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="7f66a-146">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="7f66a-p108">가장 흔한 문제는 암호를 잘못 입력한 경우입니다. 세 단계를 다시 실행하고 1단계에서 사용자 이름과 암호를 입력할 때 신중하게 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="7f66a-p108">A common problem is an incorrect password. Run the three steps again and pay close attention to the user name and password you enter in Step 1.</span></span>
    
- <span data-ttu-id="7f66a-149">DoS(서비스 거부) 공격을 방지하기 위해 Exchange Online 조직에 세 개의 개방형 원격 Windows PowerShell 연결만 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f66a-149">To help prevent denial-of-service (DoS) attacks, you're limited to three open remote Windows PowerShell connections to your Exchange Online organization.</span></span>
    
- <span data-ttu-id="7f66a-p109">Windows PowerShell은 스크립트를 실행하도록 구성해야 합니다. 이 설정은 연결할 때마다 구성하는 것이 아니라 컴퓨터에서 한 번만 구성하면 됩니다. Windows PowerShell이 서명된 스크립트를 실행하도록 하려면 상승된 Windows PowerShell 창( **관리자 권한으로 실행**을 선택하여 열린 Windows PowerShell 창)에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="7f66a-p109">Windows PowerShell needs to be configured to run scripts. You need to configure this setting only once on your computer, not every time you connect. To enable Windows PowerShell to run signed scripts, run the following command in an elevated Windows PowerShell window (a Windows PowerShell window you opened by selecting **Run as administrator**).</span></span>
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

- <span data-ttu-id="7f66a-p110">Exchange Online에 연결하는 데 사용하는 계정은 원격 Windows PowerShell에 대해 사용할 수 있어야 합니다. 자세한 내용은 [Exchange Online에서 원격 PowerShell 액세스 관리](https://go.microsoft.com/fwlink/p/?LinkId=534018)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7f66a-p110">The account you use to connect to Exchange Online must be enabled for remote Windows PowerShell. For more information, see [Manage Remote PowerShell Access in Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534018).</span></span>
    
- <span data-ttu-id="7f66a-p111">로컬 컴퓨터와 Exchange Online 간에 TCP 포트 80 트래픽을 열어야 합니다. 이 포트는 이미 열려 있을 수도 있지만 조직에서 제한적인 인터넷 액세스 정책을 사용하는 경우에는 열려 있는지를 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f66a-p111">TCP port 80 traffic needs to be open between your local computer and Exchange Online. It's probably open, but it's something to consider if your organization has a restrictive Internet access policy.</span></span>
    
## <a name="call-the-cmdlet-directly-with-invoke-command"></a><span data-ttu-id="7f66a-157">Invoke-Command를 사용하여 cmdlet 직접 호출</span><span class="sxs-lookup"><span data-stu-id="7f66a-157">Call the cmdlet directly with Invoke-Command</span></span>

<span data-ttu-id="7f66a-p112">원격 Windows PowerShell 세션을 가져오는 작업은 모든 Exchange Online cmdlet에서 가져오므로 시간이 오래 걸리는 프로세스일 수 있습니다. 이는 일괄 처리에 문제가 될 수 있습니다(예: 다른 테넌트에 대한 보고서를 실행하거나 대량 변경 시). **Import-PSSession** 사용에 대한 대안으로 **Invoke-Command** 로 사용하려는 cmdlet을 직접 호출할 수 있습니다. 예: **get-mailbox** cmdlet를 호출하려면 `Import-PSSession $Session`에 대해 이 구문을 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="7f66a-p112">Importing a remote Windows PowerShell session can be a lengthy process because it brings in all Exchange Online cmdlets. This can be an issue in batch processing—for example, when you are running reports or making bulk changes for different tenants. As an alternative to using **Import-PSSession**, you can call cmdlets you want to use directly with **Invoke-Command**. For example, to call the **get-mailbox** cmdlet, substitute this syntax for `Import-PSSession $Session`.</span></span>
  
```
Invoke-Command -Session $Session -ScriptBlock {Get-Mailbox}
```

## <a name="more-reporting-cmdlets"></a><span data-ttu-id="7f66a-162">자세한 보고 cmdlet 내용</span><span class="sxs-lookup"><span data-stu-id="7f66a-162">More reporting cmdlets</span></span>

<span data-ttu-id="7f66a-p113">이 항목에서 사용한 cmdlet은 Windows PowerShell cmdlet입니다. 이러한 cmdlet에 대한 자세한 내용은 다음 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7f66a-p113">The cmdlets that you used in this topic are Windows PowerShell cmdlets. For more information about these cmdlets, see the following topics:</span></span>
  
- [<span data-ttu-id="7f66a-165">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="7f66a-165">Get-Credential</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389618)
    
- [<span data-ttu-id="7f66a-166">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="7f66a-166">New-PSSession</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389621)
    
- [<span data-ttu-id="7f66a-167">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="7f66a-167">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389619)
    
- [<span data-ttu-id="7f66a-168">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="7f66a-168">Remove-PSSession</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389620)
    
- [<span data-ttu-id="7f66a-169">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="7f66a-169">Set-ExecutionPolicy</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389623)
    

