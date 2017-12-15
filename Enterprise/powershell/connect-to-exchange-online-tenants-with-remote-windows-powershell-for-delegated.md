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
ms.custom: DecEntMigration
ms.assetid: ae5f1a87-8b77-4f93-a1b8-56f800aeb283
description: "요약: 원격 Windows PowerShell을 사용 하 여 DelegatedOrg 매개 변수를 사용 하 여 Exchange Online에 연결 합니다."
ms.openlocfilehash: 9bb6a5a316f4bc23c6586da825b8755cf755f484
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2017
---
# <a name="connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="7c9ac-103">DAP(위임된 액세스 권한) 파트너용 원격 Windows PowerShell을 사용하여 Exchange Online 테넌트에 연결</span><span class="sxs-lookup"><span data-stu-id="7c9ac-103">Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

 <span data-ttu-id="7c9ac-104">**요약:** 원격 Windows PowerShell을 사용 하 여 _DelegatedOrg_ 매개 변수를 사용 하 여 Exchange Online에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c9ac-104">**Summary:** Use remote Windows PowerShell to connect to Exchange Online by using the _DelegatedOrg_ parameter.</span></span>
  
<span data-ttu-id="7c9ac-p101">원격 Windows PowerShell를 사용 하면 명령줄에서 Exchange Online 설정을 관리할 수 있습니다. 로컬 컴퓨터에서 Windows PowerShell를 사용 하 여 Exchange Online에 대 한 원격 세션을 만들 수 있습니다. 해당 Exchange Online 자격 증명을 입력, 필요한 연결 설정을 제공 하 고 있는 다음 사용할 수 있도록 Exchange Online cmdlet은 로컬 Windows PowerShell 세션으로 가져올 3 단계 프로세스로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7c9ac-p101">Remote Windows PowerShell lets you manage your Exchange Online settings from the command line. You use Windows PowerShell on your local computer to create a remote session to Exchange Online. It's a three-step process where you enter your Exchange Online credentials, provide the required connection settings, and then import the Exchange Online cmdlets into your local Windows PowerShell session so that you can use them.</span></span>
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="7c9ac-108">시작하기 전에 알아야 할 내용</span><span class="sxs-lookup"><span data-stu-id="7c9ac-108">What do you need to know before you begin?</span></span>

- <span data-ttu-id="7c9ac-109">예상 완료 시간: 5분</span><span class="sxs-lookup"><span data-stu-id="7c9ac-109">Estimated time to complete: 5 minutes</span></span>
    
- <span data-ttu-id="7c9ac-110">다음 Windows 버전을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c9ac-110">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="7c9ac-111">Windows 10</span><span class="sxs-lookup"><span data-stu-id="7c9ac-111">Windows 10</span></span>
    
  - <span data-ttu-id="7c9ac-112">Windows 8.1 또는 Windows 8</span><span class="sxs-lookup"><span data-stu-id="7c9ac-112">Windows 8.1 or Windows 8</span></span>
    
  - <span data-ttu-id="7c9ac-113">Windows Server 2012 R2 또는 Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="7c9ac-113">Windows Server 2012 R2 or Windows Server 2012</span></span>
    
  - <span data-ttu-id="7c9ac-114">Windows 7 SP1(서비스 팩 1)*</span><span class="sxs-lookup"><span data-stu-id="7c9ac-114">Windows 7 Service Pack 1 (SP1)*</span></span>
    
  - <span data-ttu-id="7c9ac-115">Windows Server 2008 R2 SP1*</span><span class="sxs-lookup"><span data-stu-id="7c9ac-115">Windows Server 2008 R2 SP1*</span></span>
    
    * <span data-ttu-id="7c9ac-p102">4.0 또는 Windows Management Framework 3.0 설치는.NET Framework 4.5.1 또는.NET Framework 4.5 하 고 다음 중 하나는 Windows 관리 프레임 워크에 필요 합니다. 자세한 내용은 다음 리소스를 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c9ac-p102">You need to install the .NET Framework 4.5.1 or the .NET Framework 4.5 and then either the Windows Management Framework 4.0 or the Windows Management Framework 3.0 . For more information, see the following resources:</span></span>
    
  - [<span data-ttu-id="7c9ac-118">.NET Framework를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="7c9ac-118">Installing the .NET Framework</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=257868)
    
  - <span data-ttu-id="7c9ac-119">[Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) 또는[Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344)</span><span class="sxs-lookup"><span data-stu-id="7c9ac-119">[Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) or[Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344)</span></span>
    
- <span data-ttu-id="7c9ac-120">이 항목의 절차에 적용 될 수 있는 바로 가기 키에 대 한 정보를 [Exchange 관리 센터에서 바로 가기 키](https://go.microsoft.com/fwlink/p/?LinkId=534017)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="7c9ac-120">For information about keyboard shortcuts that might apply to the procedures in this topic, see [Keyboard shortcuts in the Exchange admin center](https://go.microsoft.com/fwlink/p/?LinkId=534017).</span></span>
    
## 

> [!IMPORTANT]
> <span data-ttu-id="7c9ac-p103">위임 액세스 권한 (DAP) 파트너에 대해서만이 절차는 합니다. DAP 파트너 모를 경우에이 절차를 사용 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="7c9ac-p103">This procedure is only for Delegated Access Permission (DAP) partners. If you are not a DAP partner, do not use this procedure.</span></span> 
  
<span data-ttu-id="7c9ac-p104">DAP 파트너 신디케이션 및 클라우드 솔루션 공급자 (CSP) 파트너 됩니다. 다른 회사 네트워크 또는 전화 통신 공급자 자주 됩니다. 이러한 번들를 고객에 게 자신의 서비스 제품에 구독 합니다. 자신이 소유한 모든 자신의 고객 테에서 자동으로 자신이 관리할 수 있도록 자신의 Office 365customer 테 및 보고서에 대 한 관리 대리 (AOBO) 권한이 부여 되는 파트너 테 넌 트입니다.</span><span class="sxs-lookup"><span data-stu-id="7c9ac-p104">DAP partners are Syndication and Cloud Solution Providers (CSP) partners. They are frequently network or telecom providers to other companies. They bundle subscriptions into their service offerings to their customers. They own a partner tenancy that is automatically granted Administer On Behalf Of (AOBO) permissions to their Office 365customer tenancies so they can administer and report on all of their customer tenancies.</span></span>
  
## <a name="connect-to-exchange-online"></a><span data-ttu-id="7c9ac-127">Exchange Online에 연결</span><span class="sxs-lookup"><span data-stu-id="7c9ac-127">Connect to Exchange Online</span></span>

1. <span data-ttu-id="7c9ac-128">로컬 컴퓨터에서 Windows PowerShell을 열고 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="7c9ac-128">On your local computer, open Windows PowerShell and run the following command.</span></span>
    
  ```
  $UserCredential = Get-Credential
  ```

    <span data-ttu-id="7c9ac-129">**Windows PowerShell 자격 증명 요청** 대화 상자에서 DAP 관리자의 사용자 이름 및 암호를 입력 한 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c9ac-129">In the **Windows PowerShell Credential Request** dialog box, enter your DAP administrator user name and password, and then click **OK**.</span></span>
    
2. <span data-ttu-id="7c9ac-130">다음 명령을 실행 바꾸기 _<customer tenant domain name>_ 에 연결 하려는 테 넌 트 도메인의 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="7c9ac-130">Run the following command, replacing  _<customer tenant domain name>_ with the name of the tenant domain that you want to connect to.</span></span>
    
  ```
  $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell-liveid?DelegatedOrg=<customer tenant domain name>-Credential $UserCredential -Authentication Basic -AllowRedirection
  ```

    <span data-ttu-id="7c9ac-p105">이 명령에서 중요 한 단계는 보고 정보에 액세스 하는 고객을 지정 합니다. _DelegatedOrg_ 매개 변수를 값으로 초기 도메인 이름의 FQDN을 제공한 _ConnectionURI_ 매개 변수에서이 수행 합니다. 이렇게 하면 원격 Windows PowerShell Exchange Online PowerShell 원격 Windows PowerShell에 대 한 연결할 끝점입니다. 원격 Windows PowerShell 보고서를 실행할 때마다 특정 고객의 컨텍스트에서 Office 365 보고에 연결 해야 합니다. 이 고객을 지정한 후 다음 명령 중 모든 해당 고객의 컨텍스트에서 실행 됩니다. 이렇게 하면 파트너를이 고객에 대 한 모든 사용 가능한 보고서에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c9ac-p105">The key step in this command is specifying which customer to access for the reporting information. You do this in the  _ConnectionURI_ parameter, where you provide the FQDN of the initial domain name as the value to the _DelegatedOrg_ parameter. This tells remote Windows PowerShell for Exchange Online PowerShell remote Windows PowerShell the endpoint to connect to. remote Windows PowerShell must connect to Office 365 reporting in the context of a specific customer each time a report is run. After this customer is specified, all of the following commands are run in the context of that customer. This lets the partner to access all the available reports for this customer.</span></span>
    
3. <span data-ttu-id="7c9ac-137">다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="7c9ac-137">Run the following command.</span></span>
    
  ```
  Import-PSSession $Session
  ```

> [!NOTE]
> <span data-ttu-id="7c9ac-p106">계정 아래에서 하나를 실행할 수 있는 3 개의 동시 세션의 제한이 됩니다. 작업이 완료 되는 원격 Windows PowerShell 세션의 연결을 해제 해야 합니다. 세션을 분리 하지 않고 Windows PowerShell 창을 닫으면 모든 원격 Windows PowerShell 세션을 사용할 수 있습니다를 사용할 수 및 만료 되도록 하는 세션에 대 한 대기 해야 합니다. 원격 Windows PowerShell 세션을 끊으려면 다음 명령을 실행 합니다. >`Remove-PSSession $Session`</span><span class="sxs-lookup"><span data-stu-id="7c9ac-p106">There is a limit of three simultaneous sessions that can run under one account. Be sure to disconnect the remote Windows PowerShell session when you're finished. If you close the Windows PowerShell window without disconnecting the session, you can use up all the remote Windows PowerShell sessions available to you, and you'll need to wait for the sessions to expire. To disconnect the remote Windows PowerShell session, run the following command. >  `Remove-PSSession $Session`</span></span>
  
## <a name="how-do-you-know-this-worked"></a><span data-ttu-id="7c9ac-142">작동 여부는 어떻게 확인합니까?</span><span class="sxs-lookup"><span data-stu-id="7c9ac-142">How do you know this worked?</span></span>

<span data-ttu-id="7c9ac-p107">3 단계 후 Exchange Online cmdlet 진행률 표시줄에서 추적 로컬 Windows PowerShell 세션으로 가져옵니다. 모든 오류가 하지 않으면 하는 경우 성공적으로 연결한 합니다. 빠른 테스트는 Exchange Online cmdlet을 실행 하는-예: **Get-mailbox** -하 고 결과 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="7c9ac-p107">After Step 3, the Exchange Online cmdlets are imported into your local Windows PowerShell session as tracked by a progress bar. If you don't receive any errors, you connected successfully. A quick test is to run an Exchange Online cmdlet—for example, **Get-Mailbox** —and see the results.</span></span>
  
<span data-ttu-id="7c9ac-146">오류가 발생하면 다음 요구 사항을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="7c9ac-146">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="7c9ac-p108">가장 흔한 문제는 암호를 잘못 입력한 경우입니다. 세 단계를 다시 실행하고 1단계에서 사용자 이름과 암호를 입력할 때 신중하게 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="7c9ac-p108">A common problem is an incorrect password. Run the three steps again and pay close attention to the user name and password you enter in Step 1.</span></span>
    
- <span data-ttu-id="7c9ac-149">서비스 거부 (DoS) 공격을 방지 하려면 자신이 세개의 개방형 원격 Windows PowerShell 연결만 Exchange Online 조직에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c9ac-149">To help prevent denial-of-service (DoS) attacks, you're limited to three open remote Windows PowerShell connections to your Exchange Online organization.</span></span>
    
- <span data-ttu-id="7c9ac-p109">Windows PowerShell 스크립트를 실행 하도록 구성 해야 합니다. 이 설정은 한번만 사용자 컴퓨터에 연결할 때마다 하지 구성 해야 합니다. 서명 된 스크립트를 실행 하는 Windows PowerShell을 사용 하도록 설정 하려면 관리자 권한으로 Windows PowerShell 창 ( **관리자 권한으로 실행**을 선택 하 여 연 Windows PowerShell 창)에서 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c9ac-p109">Windows PowerShell needs to be configured to run scripts. You need to configure this setting only once on your computer, not every time you connect. To enable Windows PowerShell to run signed scripts, run the following command in an elevated Windows PowerShell window (a Windows PowerShell window you opened by selecting **Run as administrator**).</span></span>
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

- <span data-ttu-id="7c9ac-p110">Exchange Online에 연결을 사용 하는 계정이 원격 Windows PowerShell에 대해 활성화 되어야 합니다. 자세한 내용은 [Manage 원격 PowerShell 액세스 Exchange Online을](https://go.microsoft.com/fwlink/p/?LinkId=534018)참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="7c9ac-p110">The account you use to connect to Exchange Online must be enabled for remote Windows PowerShell. For more information, see [Manage Remote PowerShell Access in Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534018).</span></span>
    
- <span data-ttu-id="7c9ac-p111">TCP 포트 80 트래픽에 로컬 컴퓨터와 Exchange Online 사이 열려 있어야 합니다. 아마도 열려 있지만 조직에는 제한적인 인터넷 액세스 정책이 하는 경우를 고려 하는 것이.</span><span class="sxs-lookup"><span data-stu-id="7c9ac-p111">TCP port 80 traffic needs to be open between your local computer and Exchange Online. It's probably open, but it's something to consider if your organization has a restrictive Internet access policy.</span></span>
    
## <a name="call-the-cmdlet-directly-with-invoke-command"></a><span data-ttu-id="7c9ac-157">Invoke-Command를 사용하여 cmdlet 직접 호출</span><span class="sxs-lookup"><span data-stu-id="7c9ac-157">Call the cmdlet directly with Invoke-Command</span></span>

<span data-ttu-id="7c9ac-p112">원격 Windows PowerShell 세션을 가져오기 (영문) 하는 모든 Exchange Online cmdlet에서 가져오는 시간이 오래 걸리는 프로세스 수 있습니다. 이 일괄 처리에서 문제가 될 수-등 때는 보고서를 실행 하거나 다른 테 넌 트에 대 한 대량 변경 작업을 수행 합니다. **Import-pssession**를 사용 하는 대신, **Invoke 명령을**사용 하 여 직접 사용 하 여 원하는 cmdlet을 호출할 수 있습니다. 예, **get 사서함** cmdlet을 호출 하려면이 구문에 대 한으로 대체 `Import-PSSession $Session`합니다.</span><span class="sxs-lookup"><span data-stu-id="7c9ac-p112">Importing a remote Windows PowerShell session can be a lengthy process because it brings in all Exchange Online cmdlets. This can be an issue in batch processing—for example, when you are running reports or making bulk changes for different tenants. As an alternative to using **Import-PSSession**, you can call cmdlets you want to use directly with **Invoke-Command**. For example, to call the **get-mailbox** cmdlet, substitute this syntax for `Import-PSSession $Session`.</span></span>
  
```
Invoke-Command -Session $Session -ScriptBlock {Get-Mailbox}
```

## <a name="more-reporting-cmdlets"></a><span data-ttu-id="7c9ac-162">자세한 보고 cmdlet 내용</span><span class="sxs-lookup"><span data-stu-id="7c9ac-162">More reporting cmdlets</span></span>

<span data-ttu-id="7c9ac-p113">이 항목에서 사용 되는 cmdlet에는 Windows PowerShell cmdlet은입니다. 이러한 cmdlet에 대 한 자세한 내용은 다음 항목을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="7c9ac-p113">The cmdlets that you used in this topic are Windows PowerShell cmdlets. For more information about these cmdlets, see the following topics:</span></span>
  
- [<span data-ttu-id="7c9ac-165">Get-자격 증명</span><span class="sxs-lookup"><span data-stu-id="7c9ac-165">Get-Credential</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389618)
    
- [<span data-ttu-id="7c9ac-166">새 PSSession</span><span class="sxs-lookup"><span data-stu-id="7c9ac-166">New-PSSession</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389621)
    
- [<span data-ttu-id="7c9ac-167">Import-pssession</span><span class="sxs-lookup"><span data-stu-id="7c9ac-167">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389619)
    
- [<span data-ttu-id="7c9ac-168">Remove-pssession</span><span class="sxs-lookup"><span data-stu-id="7c9ac-168">Remove-PSSession</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389620)
    
- [<span data-ttu-id="7c9ac-169">Set-executionpolicy</span><span class="sxs-lookup"><span data-stu-id="7c9ac-169">Set-ExecutionPolicy</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389623)
    

