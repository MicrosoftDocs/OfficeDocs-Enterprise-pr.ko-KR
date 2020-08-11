---
title: DAP 파트너에 대해 원격 Windows PowerShell을 사용 하 여 Exchange Online 테 넌 트에 연결
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.assetid: ae5f1a87-8b77-4f93-a1b8-56f800aeb283
description: 요약:DelegatedOrg 값을 사용하여 Exchange Online에 연결하도록 원격 Windows PowerShell을 사용합니다.
ms.openlocfilehash: bfb041a9ab91cda54e643e8410704662c11ef175
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606014"
---
# <a name="connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="39b01-103">DAP(위임된 액세스 권한) 파트너용 원격 Windows PowerShell을 사용하여 Exchange Online 테넌트에 연결</span><span class="sxs-lookup"><span data-stu-id="39b01-103">Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

<span data-ttu-id="39b01-104">*이 문서는 Microsoft 365 Enterprise와 Office 365 Enterprise에 모두 적용됩니다.*</span><span class="sxs-lookup"><span data-stu-id="39b01-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="39b01-p101">이 항목의 절차는 DAP(위임된 액세스 권한) 파트너에게만 해당합니다. DAP 파트너가 아닌 경우 이 항목의 절차를 사용하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="39b01-p101">The procedures in this topic are only for Delegated Access Permission (DAP) partners. If you aren't a DAP partner, don't use the procedures in this topic.</span></span> 
  
<span data-ttu-id="39b01-107">DAP 파트너는 신디케이션 및 CSP(클라우드 솔루션 공급자 파트너)입니다.</span><span class="sxs-lookup"><span data-stu-id="39b01-107">DAP partners are Syndication and Cloud Solution Providers (CSP) partners.</span></span> <span data-ttu-id="39b01-108">이러한 공급자는 다른 회사의 네트워크 또는 전자 통신 공급자인 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="39b01-108">They are frequently network or telecom providers to other companies.</span></span> <span data-ttu-id="39b01-109">구독을 고객에 대한 서비스 제공 사항으로 통합합니다.</span><span class="sxs-lookup"><span data-stu-id="39b01-109">They bundle subscriptions into their service offerings to their customers.</span></span> <span data-ttu-id="39b01-110">이러한 사용자는 Microsoft 365 고객 테 넌 트에 게 자동으로 관리 되는 (AOBO) 권한을 부여 하는 파트너 테 넌 트를 소유 하 여 모든 고객 테 넌 트을 관리 하 고 보고할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="39b01-110">They own a partner tenancy that is automatically granted Administer On Behalf Of (AOBO) permissions to their Microsoft 365 customer tenancies so they can administer and report on all of their customer tenancies.</span></span>

<span data-ttu-id="39b01-111">DAP 파트너는 Exchange Online PowerShell을 사용 하 여 고객 Exchange Online 설정을 관리 하 고 명령줄에서 Microsoft 365 보고서를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39b01-111">DAP partners can use Exchange Online PowerShell to manage customer Exchange Online settings and get Microsoft 365 reports from the command line.</span></span> <span data-ttu-id="39b01-112">로컬 컴퓨터에서 Windows PowerShell을 사용하여 Exchange Online에 대한 원격 PowerShell 셸 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="39b01-112">You use Windows PowerShell on your local computer to create a remote PowerShell session to Exchange Online.</span></span> <span data-ttu-id="39b01-113">자격 증명을 입력 하 고 필요한 연결 설정을 제공한 다음 Exchange Online cmdlet을 사용 하 여 로컬 Windows PowerShell 세션으로 가져와서 사용할 수 있는 간단한 세 단계로 진행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="39b01-113">It's a simple three-step process where you enter your credentials, provide the required connection settings, and then import the Exchange Online cmdlets into your local Windows PowerShell session so that you can use them.</span></span>

> [!NOTE]
> <span data-ttu-id="39b01-p104">DAP 파트너는 Exchange Online PowerShell서 고객 테넌트 조직에 연결하기 위해 [다단계 인증을 사용하여 Exchange Online PowerShell에 연결](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell)의 절차를 사용할 수 없습니다. MFA와 Exchange Online 원격 PowerShell 모듈은 위임된 인증을 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="39b01-p104">DAP partners can't use the procedures in [Connect to Exchange Online PowerShell using multi-factor authentication](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell) to connect to their customer tenant organizations in Exchange Online PowerShell. MFA and the Exchange Online Remote PowerShell Module don't work with delegated authentication.</span></span>
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="39b01-116">시작하기 전에 알아야 할 내용은 무엇인가요?</span><span class="sxs-lookup"><span data-stu-id="39b01-116">What do you need to know before you begin?</span></span>

- <span data-ttu-id="39b01-117">예상 완료 시간: 5분</span><span class="sxs-lookup"><span data-stu-id="39b01-117">Estimated time to complete: 5 minutes</span></span>

- <span data-ttu-id="39b01-118">다음 Windows 버전을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39b01-118">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="39b01-119">Windows 10</span><span class="sxs-lookup"><span data-stu-id="39b01-119">Windows 10</span></span>

  - <span data-ttu-id="39b01-120">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="39b01-120">Windows 8.1</span></span>

  - <span data-ttu-id="39b01-121">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="39b01-121">Windows Server 2016</span></span>

  - <span data-ttu-id="39b01-122">Windows Server 2012 또는 Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="39b01-122">Windows Server 2012 or Windows Server 2012 R2</span></span>

  - <span data-ttu-id="39b01-123">Windows 7 SP1(서비스 팩 1)<sup>\*</sup></span><span class="sxs-lookup"><span data-stu-id="39b01-123">Windows 7 Service Pack 1 (SP1)<sup>\*</sup></span></span>

  - <span data-ttu-id="39b01-124">Windows Server 2008 R2 SP1<sup>\*</sup></span><span class="sxs-lookup"><span data-stu-id="39b01-124">Windows Server 2008 R2 SP1<sup>\*</sup></span></span>

    <span data-ttu-id="39b01-p105"><sup>\*</sup> 이전 버전의 Windows의 경우 Microsoft .NET Framework 4.5 또는 이상을 설치한 후 업데이트된 Windows Management Framework 버전 3.0, 4.0 또는 5.1(하나만)을 설치해야 합니다. 자세한 내용은 [.NET Framework 설치](https://go.microsoft.com/fwlink/p/?LinkId=257868), [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757), [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344) 및 [Windows Management Framework 5.1](https://aka.ms/wmf5download)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="39b01-p105"><sup>\*</sup> For older versions of Windows, you need to install the Microsoft.NET Framework 4.5 or later and then an updated version of the Windows Management Framework: 3.0, 4.0, or 5.1 (only one). For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868), [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757), [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344), and [Windows Management Framework 5.1](https://aka.ms/wmf5download).</span></span>

- <span data-ttu-id="39b01-p106">Windows_PowerShell이 스크립트를 실행하도록 구성되어야 합니다. 기본값은 이렇게 구성되지 않는 것입니다. 연결하려고 하면 다음 오류가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="39b01-p106">Windows PowerShell needs to be configured to run scripts, and by default, it isn't. You'll get the following error when you try to connect:</span></span>

  `Files cannot be loaded because running scripts is disabled on this system. Provide a valid certificate with which to sign the files.`

  <span data-ttu-id="39b01-129">인터넷에서 다운로드하는 모든 PowerShell 스크립트를 신뢰할 수 있는 게시자가 서명하도록 하려면 관리자 권한 Windows PowerShell 창(**관리자 권한으로 실행**을 선택하면 열리는 Windows PowerShell 창)에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="39b01-129">To require all PowerShell scripts that you download from the internet are signed by a trusted publisher, run the following command in an elevated Windows PowerShell window (a Windows PowerShell window you open by selecting **Run as administrator**):</span></span>

    ```
    Set-ExecutionPolicy RemoteSigned
    ```

  <span data-ttu-id="39b01-130">이 설정은 연결할 때마다 구성하는 것이 아니라 컴퓨터에서 한 번만 구성하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="39b01-130">You need to configure this setting only once on your computer, not every time you connect.</span></span>

- <span data-ttu-id="39b01-131">이 항목에서 절차에 적용할 수도 있는 키보드 바로 가기에 대한 자세한 내용은 [Exchange 관리 센터의 키보드 바로 가기](https://go.microsoft.com/fwlink/p/?LinkId=534017)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="39b01-131">For information about keyboard shortcuts that might apply to the procedures in this topic, see [Keyboard shortcuts in the Exchange admin center](https://go.microsoft.com/fwlink/p/?LinkId=534017).</span></span>

## <a name="connect-to-exchange-online-for-customer-organizations"></a><span data-ttu-id="39b01-132">고객 조직을 위해 Exchange Online에 연결</span><span class="sxs-lookup"><span data-stu-id="39b01-132">Connect to Exchange Online for customer organizations</span></span>

1. <span data-ttu-id="39b01-133">로컬 컴퓨터에서 Windows PowerShell을 열고 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="39b01-133">On your local computer, open Windows PowerShell and run the following command.</span></span>
    
    ```
    $UserCredential = Get-Credential
    ```

    <span data-ttu-id="39b01-134">**Windows PowerShell 자격 증명 요청** 대화 상자에 DAP 관리자 사용자 이름과 암호를 입력한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="39b01-134">In the **Windows PowerShell Credential Request** dialog box, enter your DAP administrator user name and password, and then click **OK**.</span></span>
    
2. <span data-ttu-id="39b01-135">_\<customer tenant domain name\>_ 연결 하려는 테 넌 트 도메인의 이름으로 바꾸고 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="39b01-135">Replace _\<customer tenant domain name\>_ with the name of the tenant domain that you want to connect to, and run the following command:</span></span>
    
    ```
    $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell-liveid?DelegatedOrg=<customer tenant domain name> -Credential $UserCredential -Authentication Basic -AllowRedirection
    ```

    <span data-ttu-id="39b01-136">이 명령에서 중요한 단계는 보고 정보에 액세스하는 고객을 지정하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="39b01-136">The key step in this command is specifying which customer to access for the reporting information.</span></span> <span data-ttu-id="39b01-137">초기 도메인 이름의 FQDN을 값으로 제공 하는 _Connectionuri_ 매개 변수에서이 작업을 수행 `?DelegatedOrg=` 합니다.</span><span class="sxs-lookup"><span data-stu-id="39b01-137">You do this in the  _ConnectionURI_ parameter, where you provide the FQDN of the initial domain name as the value for `?DelegatedOrg=`.</span></span> <span data-ttu-id="39b01-138">이 값은 연결할 올바른 Exchange Online PowerShell 끝점을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="39b01-138">This value indicates the correct Exchange Online PowerShell endpoint to connect to.</span></span> <span data-ttu-id="39b01-139">원격 PowerShell은 보고서를 실행할 때마다 특정 고객의 컨텍스트에서 Microsoft 365 보고에 연결 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="39b01-139">Remote PowerShell must connect to Microsoft 365 reporting in the context of a specific customer each time a report is run.</span></span> <span data-ttu-id="39b01-140">Exchange Online PowerShell에 연결한 후에는 모든 후속 명령이 고객의 컨텍스트에서 실행 되므로 고객의 모든 사용 가능한 보고서에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39b01-140">After you connect to Exchange Online PowerShell, all subsequent commands are run in the context of the customer, which gives you access to all of the available reports for the customer.</span></span>
    
3. <span data-ttu-id="39b01-141">다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="39b01-141">Run the following command.</span></span>
    
    ```
    Import-PSSession $Session
    ```

> [!NOTE]
> <span data-ttu-id="39b01-p108">한 계정에 실행할 수 있는 동시 세션은 3개로 제한됩니다. 완료되면 원격 PowerShell 세션의 연결을 끊어야 합니다. 세션 연결을 끊지 않고 PowerShell 창을 닫으면 사용할 수 있는 원격 PowerShell 세션을 전부 써버릴 수 있으며 세션이 만료될 때까지 기다려야 합니다. 원격 Windows PowerShell 세션의 연결을 끊으려면 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="39b01-p108">There's a limit of three simultaneous sessions that can run under one account. Be sure to disconnect the remote PowerShell session when you're finished. If you close the Windows PowerShell window without disconnecting the session, you can use up all the remote PowerShell sessions available to you, and you'll need to wait for the sessions to expire. To disconnect the remote PowerShell session, run the following command:</span></span>

```
Remove-PSSession $Session
```
  
## <a name="how-do-you-know-this-worked"></a><span data-ttu-id="39b01-146">작동 여부는 어떻게 확인하나요?</span><span class="sxs-lookup"><span data-stu-id="39b01-146">How do you know this worked?</span></span>

<span data-ttu-id="39b01-p109">3단계를 수행하고 나면 Exchange Online cmdlet이 진행률 표시줄을 통해 추적한 대로 로컬 Windows PowerShell 세션으로 가져오기됩니다. 오류가 발생하지 않으면 정상적으로 연결된 것입니다. 빠르게 테스트하려면 Exchange Online cmdlet(예: **Get-Mailbox**)을 실행하여 결과를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="39b01-p109">After Step 3, the Exchange Online cmdlets are imported into your local Windows PowerShell session as tracked by a progress bar. If you don't receive any errors, you connected successfully. A quick test is to run an Exchange Online cmdlet (for example, **Get-Mailbox**) and see the results.</span></span>
  
<span data-ttu-id="39b01-150">오류가 발생하면 다음 요구 사항을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="39b01-150">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="39b01-p110">가장 흔한 문제는 암호를 잘못 입력한 경우입니다. 세 단계를 다시 실행하고 1단계에서 사용자 이름과 암호를 입력할 때 신중하게 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="39b01-p110">A common problem is an incorrect password. Run the three steps again and pay close attention to the user name and password you enter in Step 1.</span></span>
    
- <span data-ttu-id="39b01-p111">Exchange Online에 연결하는 데 사용하는 계정은 원격 PowerShell에 대해 사용할 수 있어야 합니다. 자세한 내용은 [Exchange Online PowerShell에 대한 액세스 사용 또는 사용 안 함](https://go.microsoft.com/fwlink/p/?LinkId=534018)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="39b01-p111">The account you use to connect to Exchange Online must be enabled for remote PowerShell. For more information, see [Enable or disable access to Exchange Online PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534018).</span></span>
    
- <span data-ttu-id="39b01-p112">로컬 컴퓨터와 Exchange Online 간에 TCP 포트 80 트래픽을 열어야 합니다. 이 포트는 이미 열려 있을 수도 있지만 조직에서 제한적인 인터넷 액세스 정책을 사용하는 경우에는 열려 있는지를 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="39b01-p112">TCP port 80 traffic needs to be open between your local computer and Exchange Online. It's probably open, but it's something to consider if your organization has a restrictive Internet access policy.</span></span>
    
## <a name="call-the-cmdlet-directly-with-invoke-command"></a><span data-ttu-id="39b01-157">Invoke-Command를 사용하여 cmdlet 직접 호출</span><span class="sxs-lookup"><span data-stu-id="39b01-157">Call the cmdlet directly with Invoke-Command</span></span>

<span data-ttu-id="39b01-p113">원격 PowerShell 세션을 가져오는 작업(3단계)은 _모든_ Exchange Online cmdlet에서 가져오므로 시간이 오래 걸리는 프로세스일 수 있습니다. 이는 일괄 처리에 문제가 될 수 있습니다(예: 다른 테넌트에 대한 보고서를 실행하거나 대량 변경 시). **Import-PSSession** 사용에 대한 대안으로 **Invoke-Command**로 사용하려는 cmdlet을 직접 호출할 수 있습니다. 예를 들어 **Get-Milbox** cmdlet을 호출하려면 이 구문을 3단계의 `Import-PSSession $Session` 명령으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="39b01-p113">Importing a remote PowerShell session (Step 3) can be a lengthy process because it brings in _all_ Exchange Online cmdlets. This can be an issue in batch processing (for example, when you're running reports or making bulk changes for different tenants). As an alternative to using **Import-PSSession**, you can call cmdlets you want to use directly with **Invoke-Command**. For example, to call the **Get-Milbox** cmdlet, substitute this syntax for the `Import-PSSession $Session` command in Step 3:</span></span>
  
```
Invoke-Command -Session $Session -ScriptBlock {Get-Mailbox}
```

## <a name="more-reporting-cmdlets"></a><span data-ttu-id="39b01-162">자세한 보고 cmdlet 내용</span><span class="sxs-lookup"><span data-stu-id="39b01-162">More reporting cmdlets</span></span>

<span data-ttu-id="39b01-p114">이 항목에서 사용한 cmdlet은 Windows PowerShell cmdlet입니다. 이러한 cmdlet에 대한 자세한 내용은 다음 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="39b01-p114">The cmdlets that you used in this topic are Windows PowerShell cmdlets. For more information about these cmdlets, see the following topics:</span></span>
  
- [<span data-ttu-id="39b01-165">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="39b01-165">Get-Credential</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389618)
    
- [<span data-ttu-id="39b01-166">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="39b01-166">New-PSSession</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389621)
    
- [<span data-ttu-id="39b01-167">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="39b01-167">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389619)
    
- [<span data-ttu-id="39b01-168">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="39b01-168">Remove-PSSession</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389620)
    
- [<span data-ttu-id="39b01-169">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="39b01-169">Set-ExecutionPolicy</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389623)
    

