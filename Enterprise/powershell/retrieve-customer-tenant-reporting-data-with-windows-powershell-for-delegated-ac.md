---
title: "DAP(위임된 액세스 권한) 파트너용 Windows PowerShell을 사용하여 고객 테넌트 보고 데이터 검색"
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
ms.assetid: 893e5275-30b3-433f-8ecd-644f78f513e2
description: "요약:Microsoft Exchange Online용 원격Windows PowerShell을 사용하여 개별 고객 테넌트에서 보고서를 검색합니다."
ms.openlocfilehash: 40c1dedd8fb223ea6fa478b3a5c3e716fe07dd93
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2017
---
# <a name="retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="31599-103">DAP(위임된 액세스 권한) 파트너용 Windows PowerShell을 사용하여 고객 테넌트 보고 데이터 검색</span><span class="sxs-lookup"><span data-stu-id="31599-103">Retrieve customer tenant reporting data with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

 <span data-ttu-id="31599-104">**요약:** Microsoft Exchange Online용 원격Windows PowerShell을 사용하여 개별 고객 테넌트에서 보고서를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="31599-104">Summary: Use remoteWindows PowerShell for Microsoft Exchange Online to retrieve reports from individual customer tenants.</span></span>
  
<span data-ttu-id="31599-p101">Syndication 및 CSP(클라우드 솔루션 공급자) 파트너는 Exchange Online PowerShell용 원격Windows PowerShell을 통해 직접 고객 테넌트 보고를 구성하는 데이터에 액세스할 수 있습니다. 이를 통해 파트너는 보고 데이터를 수집하고 저장한 후 여기에서 다른 작업을 수행할 수 있습니다. 원격 연결을 연 후 고객 테넌트에 대한 보고 데이터 검색은 고객 테넌트에 대해 cmdlet을 실행하는 것과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="31599-p101">Syndication and Cloud Solution Provider (CSP) partners can access the data that makes up customer tenant reports directly via remoteWindows PowerShell for Exchange Online PowerShell. This lets partners collect and save the reporting data and then perform other operations on it. After you open a remote connection, retrieving reporting data about a customer tenancy is identical to running any cmdlet against a customer tenancy.</span></span>
  
<span data-ttu-id="31599-p102">이 문서에서는 Exchange Online용 원격Windows PowerShell을 사용하여 단일 고객 테넌트에 연결하고 보고서를 검색합니다. 기본적으로 Windows PowerShell은 여러 고객 테넌트에서 보고 데이터 집계를 지원하지 않습니다. 이 절차를 사용하여 검색하는 보고서는 연결되는  _DelegatedOrg_에만 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="31599-p102">In this article, you use remoteWindows PowerShell for Exchange Online to connect to a single customer tenancy and retrieve a report. By default, Windows PowerShell does not support aggregating reporting data from multiple customer tenancies. The reports you retrieve with this procedure are only for the  _DelegatedOrg_ that you connect to.</span></span>
  
<span data-ttu-id="31599-111">모든 고객 테넌트에 대해 단일 보고서를 검색하려는 경우 이를 수행할 샘플 스크립트는 [DAP(위임된 액세스 권한) 파트너용 Windows PowerShell을 통해 고객 보고 데이터 집계](aggregate-customer-reporting-data-via-windows-powershell-for-delegated-access-pe.md)에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31599-111">If you want to retrieve a single report for all your customer tenancies, a sample script to do this can be found in [Aggregate customer reporting data via Windows PowerShell for Delegated Access Permission (DAP) partners](aggregate-customer-reporting-data-via-windows-powershell-for-delegated-access-pe.md) .</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="31599-112">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="31599-112">Before you begin</span></span>

- <span data-ttu-id="31599-p103">원격 Windows PowerShell을 사용하여 Exchange Online 테넌트에 연결해야 합니다. 자세한 내용은 [DAP(위임된 액세스 권한) 파트너용 원격 Windows PowerShell을 사용하여 Exchange Online 테넌트에 연결](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="31599-p103">You need to connect to your Exchange Online tenant by using remote Windows PowerShell. For instructions, see [Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)</span></span>
    
## <a name="run-the-get-stalemailboxreport-sample"></a><span data-ttu-id="31599-115">Get-StaleMailboxReport 샘플 실행</span><span class="sxs-lookup"><span data-stu-id="31599-115">Run the Get-StaleMailboxReport sample</span></span>

<span data-ttu-id="31599-116">원격 세션을 Exchange Online으로 연 후 이 명령을 실행하여 날짜 범위 2015/03/25에서 2015/03/31까지에 대해 **Get-StaleMailboxReport** 를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="31599-116">After you have opened a remote session to Exchange Online, run this command to retrieve the **Get-StaleMailboxReport** for the date range 03/25/2015 through 03/31/2015.</span></span>
  
```
Get-StaleMailboxReport -StartDate 03/25/2015 -EndDate 03/31/2015
```

<span data-ttu-id="31599-p104">사용할 수 있는 메시지 추적에 대해 Exchange Online, Lync Online, SharePoint Online 등에 다양한 보고 cmdlet을 사용할 수 있습니다. 사용 가능한 보고 cmdlet 및 Office 365 보고 웹 서비스에 대한 자세한 내용은 다음 섹션의 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="31599-p104">There are many other reporting cmdlets available for Exchange Online, Lync Online, and SharePoint Online as well as others for message tracing that you can use. To find out more about the available reporting cmdlets and the Office 365 Reporting web service, see the topics in the following section.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="31599-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="31599-119">See also</span></span>

#### 

[<span data-ttu-id="31599-120">Office 365 보고 웹 서비스</span><span class="sxs-lookup"><span data-stu-id="31599-120">Office 365 Reporting web service</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532777)
  
[<span data-ttu-id="31599-121">Exchange Online의 보고 cmdlet</span><span class="sxs-lookup"><span data-stu-id="31599-121">Reporting cmdlets in Exchange Online</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=526430)
  
[<span data-ttu-id="31599-122">파트너를 위한 도움말</span><span class="sxs-lookup"><span data-stu-id="31599-122">Help for partners</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=533477)

