---
title: DAP(위임된 액세스 권한) 파트너용 원격 Windows PowerShell을 사용하여 Exchange Online 테넌트에 연결
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
ms.custom: ''
ms.assetid: ae5f1a87-8b77-4f93-a1b8-56f800aeb283
description: 요약:DelegatedOrg 값을 사용하여 Exchange Online에 연결하도록 원격 Windows PowerShell을 사용합니다.
ms.openlocfilehash: 4a9f08325fc56308b27467423b047375985562c5
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "44997374"
---
# <a name="connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="c780d-103">DAP(위임된 액세스 권한) 파트너용 원격 Windows PowerShell을 사용하여 Exchange Online 테넌트에 연결</span><span class="sxs-lookup"><span data-stu-id="c780d-103">Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c780d-104">The procedures in this topic are only for Delegated Access Permission (DAP) partners.</span><span class="sxs-lookup"><span data-stu-id="c780d-104">The procedures in this topic are only for Delegated Access Permission (DAP) partners.</span></span> <span data-ttu-id="c780d-105">If you aren't a DAP partner, don't use the procedures in this topic.</span><span class="sxs-lookup"><span data-stu-id="c780d-105">If you aren't a DAP partner, don't use the procedures in this topic.</span></span> 
  
<span data-ttu-id="c780d-106">DAP 파트너는 신디케이션 및 CSP(클라우드 솔루션 공급자 파트너)입니다.</span><span class="sxs-lookup"><span data-stu-id="c780d-106">DAP partners are Syndication and Cloud Solution Providers (CSP) partners.</span></span> <span data-ttu-id="c780d-107">이러한 공급자는 다른 회사의 네트워크 또는 전자 통신 공급자인 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="c780d-107">They are frequently network or telecom providers to other companies.</span></span> <span data-ttu-id="c780d-108">구독을 고객에 대한 서비스 제공 사항으로 통합합니다.</span><span class="sxs-lookup"><span data-stu-id="c780d-108">They bundle subscriptions into their service offerings to their customers.</span></span> <span data-ttu-id="c780d-109">이러한 사용자는 Microsoft 365 고객 테 넌 트에 게 자동으로 관리 되는 (AOBO) 권한을 부여 하는 파트너 테 넌 트를 소유 하 여 모든 고객 테 넌 트을 관리 하 고 보고할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="c780d-109">They own a partner tenancy that is automatically granted Administer On Behalf Of (AOBO) permissions to their Microsoft 365 customer tenancies so they can administer and report on all of their customer tenancies.</span></span>

<span data-ttu-id="c780d-110">DAP 파트너는 Exchange Online PowerShell을 사용 하 여 고객 Exchange Online 설정을 관리 하 고 명령줄에서 Microsoft 365 보고서를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c780d-110">DAP partners can use Exchange Online PowerShell to manage customer Exchange Online settings and get Microsoft 365 reports from the command line.</span></span> <span data-ttu-id="c780d-111">로컬 컴퓨터에서 Windows PowerShell을 사용하여 Exchange Online에 대한 원격 PowerShell 셸 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c780d-111">You use Windows PowerShell on your local computer to create a remote PowerShell session to Exchange Online.</span></span> <span data-ttu-id="c780d-112">자격 증명을 입력 하 고 필요한 연결 설정을 제공한 다음 Exchange Online cmdlet을 사용 하 여 로컬 Windows PowerShell 세션으로 가져와서 사용할 수 있는 간단한 세 단계로 진행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c780d-112">It's a simple three-step process where you enter your credentials, provide the required connection settings, and then import the Exchange Online cmdlets into your local Windows PowerShell session so that you can use them.</span></span>

> [!NOTE]
> <span data-ttu-id="c780d-113">DAP partners can't use the procedures in [Connect to Exchange Online PowerShell using multi-factor authentication](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell) to connect to their customer tenant organizations in Exchange Online PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c780d-113">DAP partners can't use the procedures in [Connect to Exchange Online PowerShell using multi-factor authentication](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell) to connect to their customer tenant organizations in Exchange Online PowerShell.</span></span> <span data-ttu-id="c780d-114">MFA and the Exchange Online Remote PowerShell Module don't work with delegated authentication.</span><span class="sxs-lookup"><span data-stu-id="c780d-114">MFA and the Exchange Online Remote PowerShell Module don't work with delegated authentication.</span></span>
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="c780d-115">시작하기 전에 알아야 할 내용</span><span class="sxs-lookup"><span data-stu-id="c780d-115">What do you need to know before you begin?</span></span>

- <span data-ttu-id="c780d-116">예상 완료 시간: 5분</span><span class="sxs-lookup"><span data-stu-id="c780d-116">Estimated time to complete: 5 minutes</span></span>

- <span data-ttu-id="c780d-117">다음 Windows 버전을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c780d-117">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="c780d-118">Windows 10</span><span class="sxs-lookup"><span data-stu-id="c780d-118">Windows 10</span></span>

  - <span data-ttu-id="c780d-119">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="c780d-119">Windows 8.1</span></span>

  - <span data-ttu-id="c780d-120">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="c780d-120">Windows Server 2016</span></span>

  - <span data-ttu-id="c780d-121">Windows Server 2012 또는 Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="c780d-121">Windows Server 2012 or Windows Server 2012 R2</span></span>

  - <span data-ttu-id="c780d-122">Windows 7 SP1(서비스 팩 1)<sup>\*</sup></span><span class="sxs-lookup"><span data-stu-id="c780d-122">Windows 7 Service Pack 1 (SP1)<sup>\*</sup></span></span>

  - <span data-ttu-id="c780d-123">Windows Server 2008 R2 SP1<sup>\*</sup></span><span class="sxs-lookup"><span data-stu-id="c780d-123">Windows Server 2008 R2 SP1<sup>\*</sup></span></span>

    <span data-ttu-id="c780d-124"><sup>\*</sup> For older versions of Windows, you need to install the Microsoft.NET Framework 4.5 or later and then an updated version of the Windows Management Framework: 3.0, 4.0, or 5.1 (only one).</span><span class="sxs-lookup"><span data-stu-id="c780d-124"><sup>\*</sup> For older versions of Windows, you need to install the Microsoft.NET Framework 4.5 or later and then an updated version of the Windows Management Framework: 3.0, 4.0, or 5.1 (only one).</span></span> <span data-ttu-id="c780d-125">For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868), [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757), [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344), and [Windows Management Framework 5.1](https://aka.ms/wmf5download).</span><span class="sxs-lookup"><span data-stu-id="c780d-125">For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868), [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757), [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344), and [Windows Management Framework 5.1](https://aka.ms/wmf5download).</span></span>

- <span data-ttu-id="c780d-126">Windows PowerShell needs to be configured to run scripts, and by default, it isn't.</span><span class="sxs-lookup"><span data-stu-id="c780d-126">Windows PowerShell needs to be configured to run scripts, and by default, it isn't.</span></span> <span data-ttu-id="c780d-127">You'll get the following error when you try to connect:</span><span class="sxs-lookup"><span data-stu-id="c780d-127">You'll get the following error when you try to connect:</span></span>

  `Files cannot be loaded because running scripts is disabled on this system. Provide a valid certificate with which to sign the files.`

  <span data-ttu-id="c780d-128">인터넷에서 다운로드하는 모든 PowerShell 스크립트를 신뢰할 수 있는 게시자가 서명하도록 하려면 관리자 권한 Windows PowerShell 창(**관리자 권한으로 실행**을 선택하면 열리는 Windows PowerShell 창)에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c780d-128">To require all PowerShell scripts that you download from the internet are signed by a trusted publisher, run the following command in an elevated Windows PowerShell window (a Windows PowerShell window you open by selecting **Run as administrator**):</span></span>

    ```
    Set-ExecutionPolicy RemoteSigned
    ```

  <span data-ttu-id="c780d-129">이 설정은 연결할 때마다 구성하는 것이 아니라 컴퓨터에서 한 번만 구성하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c780d-129">You need to configure this setting only once on your computer, not every time you connect.</span></span>

- <span data-ttu-id="c780d-130">이 항목에서 절차에 적용할 수도 있는 키보드 바로 가기에 대한 자세한 내용은 [Exchange 관리 센터의 키보드 바로 가기](https://go.microsoft.com/fwlink/p/?LinkId=534017)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c780d-130">For information about keyboard shortcuts that might apply to the procedures in this topic, see [Keyboard shortcuts in the Exchange admin center](https://go.microsoft.com/fwlink/p/?LinkId=534017).</span></span>

## <a name="connect-to-exchange-online-for-customer-organizations"></a><span data-ttu-id="c780d-131">고객 조직을 위해 Exchange Online에 연결</span><span class="sxs-lookup"><span data-stu-id="c780d-131">Connect to Exchange Online for customer organizations</span></span>

1. <span data-ttu-id="c780d-132">로컬 컴퓨터에서 Windows PowerShell을 열고 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c780d-132">On your local computer, open Windows PowerShell and run the following command.</span></span>
    
    ```
    $UserCredential = Get-Credential
    ```

    <span data-ttu-id="c780d-133">**Windows PowerShell 자격 증명 요청** 대화 상자에 DAP 관리자 사용자 이름과 암호를 입력한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c780d-133">In the **Windows PowerShell Credential Request** dialog box, enter your DAP administrator user name and password, and then click **OK**.</span></span>
    
2. <span data-ttu-id="c780d-134">_\<customer tenant domain name\>_ 연결 하려는 테 넌 트 도메인의 이름으로 바꾸고 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="c780d-134">Replace _\<customer tenant domain name\>_ with the name of the tenant domain that you want to connect to, and run the following command:</span></span>
    
    ```
    $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell-liveid?DelegatedOrg=<customer tenant domain name> -Credential $UserCredential -Authentication Basic -AllowRedirection
    ```

    <span data-ttu-id="c780d-135">이 명령에서 중요한 단계는 보고 정보에 액세스하는 고객을 지정하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c780d-135">The key step in this command is specifying which customer to access for the reporting information.</span></span> <span data-ttu-id="c780d-136">초기 도메인 이름의 FQDN을 값으로 제공 하는 _Connectionuri_ 매개 변수에서이 작업을 수행 `?DelegatedOrg=` 합니다.</span><span class="sxs-lookup"><span data-stu-id="c780d-136">You do this in the  _ConnectionURI_ parameter, where you provide the FQDN of the initial domain name as the value for `?DelegatedOrg=`.</span></span> <span data-ttu-id="c780d-137">이 값은 연결할 올바른 Exchange Online PowerShell 끝점을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c780d-137">This value indicates the correct Exchange Online PowerShell endpoint to connect to.</span></span> <span data-ttu-id="c780d-138">원격 PowerShell은 보고서를 실행할 때마다 특정 고객의 컨텍스트에서 Microsoft 365 보고에 연결 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c780d-138">Remote PowerShell must connect to Microsoft 365 reporting in the context of a specific customer each time a report is run.</span></span> <span data-ttu-id="c780d-139">Exchange Online PowerShell에 연결한 후에는 모든 후속 명령이 고객의 컨텍스트에서 실행 되므로 고객의 모든 사용 가능한 보고서에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c780d-139">After you connect to Exchange Online PowerShell, all subsequent commands are run in the context of the customer, which gives you access to all of the available reports for the customer.</span></span>
    
3. <span data-ttu-id="c780d-140">다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c780d-140">Run the following command.</span></span>
    
    ```
    Import-PSSession $Session
    ```

> [!NOTE]
> <span data-ttu-id="c780d-141">There's a limit of three simultaneous sessions that can run under one account.</span><span class="sxs-lookup"><span data-stu-id="c780d-141">There's a limit of three simultaneous sessions that can run under one account.</span></span> <span data-ttu-id="c780d-142">Be sure to disconnect the remote PowerShell session when you're finished.</span><span class="sxs-lookup"><span data-stu-id="c780d-142">Be sure to disconnect the remote PowerShell session when you're finished.</span></span> <span data-ttu-id="c780d-143">If you close the Windows PowerShell window without disconnecting the session, you can use up all the remote PowerShell sessions available to you, and you'll need to wait for the sessions to expire.</span><span class="sxs-lookup"><span data-stu-id="c780d-143">If you close the Windows PowerShell window without disconnecting the session, you can use up all the remote PowerShell sessions available to you, and you'll need to wait for the sessions to expire.</span></span> <span data-ttu-id="c780d-144">To disconnect the remote PowerShell session, run the following command:</span><span class="sxs-lookup"><span data-stu-id="c780d-144">To disconnect the remote PowerShell session, run the following command:</span></span>

```
Remove-PSSession $Session
```
  
## <a name="how-do-you-know-this-worked"></a><span data-ttu-id="c780d-145">작동 여부는 어떻게 확인하나요?</span><span class="sxs-lookup"><span data-stu-id="c780d-145">How do you know this worked?</span></span>

<span data-ttu-id="c780d-146">After Step 3, the Exchange Online cmdlets are imported into your local Windows PowerShell session as tracked by a progress bar.</span><span class="sxs-lookup"><span data-stu-id="c780d-146">After Step 3, the Exchange Online cmdlets are imported into your local Windows PowerShell session as tracked by a progress bar.</span></span> <span data-ttu-id="c780d-147">If you don't receive any errors, you connected successfully.</span><span class="sxs-lookup"><span data-stu-id="c780d-147">If you don't receive any errors, you connected successfully.</span></span> <span data-ttu-id="c780d-148">A quick test is to run an Exchange Online cmdlet (for example, **Get-Mailbox**) and see the results.</span><span class="sxs-lookup"><span data-stu-id="c780d-148">A quick test is to run an Exchange Online cmdlet (for example, **Get-Mailbox**) and see the results.</span></span>
  
<span data-ttu-id="c780d-149">오류가 발생하면 다음 요구 사항을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="c780d-149">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="c780d-150">A common problem is an incorrect password.</span><span class="sxs-lookup"><span data-stu-id="c780d-150">A common problem is an incorrect password.</span></span> <span data-ttu-id="c780d-151">Run the three steps again and pay close attention to the user name and password you enter in Step 1.</span><span class="sxs-lookup"><span data-stu-id="c780d-151">Run the three steps again and pay close attention to the user name and password you enter in Step 1.</span></span>
    
- <span data-ttu-id="c780d-152">The account you use to connect to Exchange Online must be enabled for remote PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c780d-152">The account you use to connect to Exchange Online must be enabled for remote PowerShell.</span></span> <span data-ttu-id="c780d-153">For more information, see [Enable or disable access to Exchange Online PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534018).</span><span class="sxs-lookup"><span data-stu-id="c780d-153">For more information, see [Enable or disable access to Exchange Online PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534018).</span></span>
    
- <span data-ttu-id="c780d-154">TCP port 80 traffic needs to be open between your local computer and Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="c780d-154">TCP port 80 traffic needs to be open between your local computer and Exchange Online.</span></span> <span data-ttu-id="c780d-155">It's probably open, but it's something to consider if your organization has a restrictive Internet access policy.</span><span class="sxs-lookup"><span data-stu-id="c780d-155">It's probably open, but it's something to consider if your organization has a restrictive Internet access policy.</span></span>
    
## <a name="call-the-cmdlet-directly-with-invoke-command"></a><span data-ttu-id="c780d-156">Invoke-Command를 사용하여 cmdlet 직접 호출</span><span class="sxs-lookup"><span data-stu-id="c780d-156">Call the cmdlet directly with Invoke-Command</span></span>

<span data-ttu-id="c780d-157">Importing a remote PowerShell session (Step 3) can be a lengthy process because it brings in _all_ Exchange Online cmdlets.</span><span class="sxs-lookup"><span data-stu-id="c780d-157">Importing a remote PowerShell session (Step 3) can be a lengthy process because it brings in _all_ Exchange Online cmdlets.</span></span> <span data-ttu-id="c780d-158">This can be an issue in batch processing (for example, when you're running reports or making bulk changes for different tenants).</span><span class="sxs-lookup"><span data-stu-id="c780d-158">This can be an issue in batch processing (for example, when you're running reports or making bulk changes for different tenants).</span></span> <span data-ttu-id="c780d-159">As an alternative to using **Import-PSSession**, you can call cmdlets you want to use directly with **Invoke-Command**.</span><span class="sxs-lookup"><span data-stu-id="c780d-159">As an alternative to using **Import-PSSession**, you can call cmdlets you want to use directly with **Invoke-Command**.</span></span> <span data-ttu-id="c780d-160">For example, to call the **Get-Milbox** cmdlet, substitute this syntax for the `Import-PSSession $Session` command in Step 3:</span><span class="sxs-lookup"><span data-stu-id="c780d-160">For example, to call the **Get-Milbox** cmdlet, substitute this syntax for the `Import-PSSession $Session` command in Step 3:</span></span>
  
```
Invoke-Command -Session $Session -ScriptBlock {Get-Mailbox}
```

## <a name="more-reporting-cmdlets"></a><span data-ttu-id="c780d-161">자세한 보고 cmdlet 내용</span><span class="sxs-lookup"><span data-stu-id="c780d-161">More reporting cmdlets</span></span>

<span data-ttu-id="c780d-162">The cmdlets that you used in this topic are Windows PowerShell cmdlets.</span><span class="sxs-lookup"><span data-stu-id="c780d-162">The cmdlets that you used in this topic are Windows PowerShell cmdlets.</span></span> <span data-ttu-id="c780d-163">For more information about these cmdlets, see the following topics:</span><span class="sxs-lookup"><span data-stu-id="c780d-163">For more information about these cmdlets, see the following topics:</span></span>
  
- [<span data-ttu-id="c780d-164">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="c780d-164">Get-Credential</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389618)
    
- [<span data-ttu-id="c780d-165">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="c780d-165">New-PSSession</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389621)
    
- [<span data-ttu-id="c780d-166">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="c780d-166">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389619)
    
- [<span data-ttu-id="c780d-167">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="c780d-167">Remove-PSSession</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389620)
    
- [<span data-ttu-id="c780d-168">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="c780d-168">Set-ExecutionPolicy</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389623)
    

