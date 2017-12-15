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
description: "요약: 개별 고객 테 넌 트에서 보고서를 검색 하려면 remoteWindows Microsoft Exchange online PowerShell을 사용 합니다."
ms.openlocfilehash: 40c1dedd8fb223ea6fa478b3a5c3e716fe07dd93
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2017
---
# <a name="retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="34b3e-103">DAP(위임된 액세스 권한) 파트너용 Windows PowerShell을 사용하여 고객 테넌트 보고 데이터 검색</span><span class="sxs-lookup"><span data-stu-id="34b3e-103">Retrieve customer tenant reporting data with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

 <span data-ttu-id="34b3e-104">**요약:** RemoteWindows Microsoft Exchange online PowerShell을 사용 하 여 개별 고객 테 넌 트에서 보고서를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="34b3e-104">**Summary:** Use remoteWindows PowerShell for Microsoft Exchange Online to retrieve reports from individual customer tenants.</span></span>
  
<span data-ttu-id="34b3e-p101">신디케이션 및 클라우드 솔루션 공급자 (CSP) 파트너 Exchange Online PowerShell에 대 한 remoteWindows PowerShell 통해 직접 고객 테 넌 트 보고서를 구성 하는 데이터에 액세스할 수 있습니다. 이렇게 하면 파트너를 수집 및 보고 데이터를 저장 하 고 다음에 다른 작업을 수행할 수 있습니다. 원격 연결을 연 후에 고객 테 넌 트에 대 한 보고 데이터를 검색 하는 프로그램 고객 테 넌 트에 대해 모든 cmdlet을 실행 하 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="34b3e-p101">Syndication and Cloud Solution Provider (CSP) partners can access the data that makes up customer tenant reports directly via remoteWindows PowerShell for Exchange Online PowerShell. This lets partners collect and save the reporting data and then perform other operations on it. After you open a remote connection, retrieving reporting data about a customer tenancy is identical to running any cmdlet against a customer tenancy.</span></span>
  
<span data-ttu-id="34b3e-p102">이 문서에서는 단일 고객 테 넌에 연결 하 고 보고서를 검색할 remoteWindows Exchange Online에 대 한 PowerShell을 사용 합니다. 기본적으로 Windows PowerShell 지원 하지 않습니다 여러 고객 테에서 보고 데이터를 집계 합니다. 이 절차를 검색 하는 보고서에 연결 하는 _DelegatedOrg_ 에 대해서만 됩니다.</span><span class="sxs-lookup"><span data-stu-id="34b3e-p102">In this article, you use remoteWindows PowerShell for Exchange Online to connect to a single customer tenancy and retrieve a report. By default, Windows PowerShell does not support aggregating reporting data from multiple customer tenancies. The reports you retrieve with this procedure are only for the  _DelegatedOrg_ that you connect to.</span></span>
  
<span data-ttu-id="34b3e-111">대화 모든 고객 테에 대 한 단일 보고서를 검색 하려는 경우이 작업을 수행 하는 샘플 스크립트는 [위임 된 액세스 권한 (DAP) 파트너에 대 한 Windows PowerShell을 통해 집계 고객 보고 데이터](aggregate-customer-reporting-data-via-windows-powershell-for-delegated-access-pe.md) 에 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34b3e-111">If you want to retrieve a single report for all your customer tenancies, a sample script to do this can be found in [Aggregate customer reporting data via Windows PowerShell for Delegated Access Permission (DAP) partners](aggregate-customer-reporting-data-via-windows-powershell-for-delegated-access-pe.md) .</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="34b3e-112">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="34b3e-112">Before you begin</span></span>

- <span data-ttu-id="34b3e-p103">원격 Windows PowerShell을 사용 하 여 Exchange Online 테 넌 트에 연결 해야 합니다. 자세한 내용은 [연결에 대 한 액세스 권한을 위임 (DAP) 파트너에 대 한 원격 Windows PowerShell을 사용한 Exchange Online 테 넌 트를](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md) 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="34b3e-p103">You need to connect to your Exchange Online tenant by using remote Windows PowerShell. For instructions, see [Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)</span></span>
    
## <a name="run-the-get-stalemailboxreport-sample"></a><span data-ttu-id="34b3e-115">Get-StaleMailboxReport 샘플 실행</span><span class="sxs-lookup"><span data-stu-id="34b3e-115">Run the Get-StaleMailboxReport sample</span></span>

<span data-ttu-id="34b3e-116">날짜 범위에 대 한 **Get StaleMailboxReport** 를 검색 하려면이 명령을 실행 하는 Exchange Online에 대 한 원격 세션을 연 후 03/25/2015 03/31/2015 통해 합니다.</span><span class="sxs-lookup"><span data-stu-id="34b3e-116">After you have opened a remote session to Exchange Online, run this command to retrieve the **Get-StaleMailboxReport** for the date range 03/25/2015 through 03/31/2015.</span></span>
  
```
Get-StaleMailboxReport -StartDate 03/25/2015 -EndDate 03/31/2015
```

<span data-ttu-id="34b3e-p104">사용할 수 있는 메시지 추적에 대 한 Exchange Online, Lync Online 및 SharePoint Online으로 다른 사용자에 대해 사용할 수 있는 다른 많은 보고 cmdlet이 있습니다. 사용 가능한 보고 cmdlet 및 Office 365 보고 웹 서비스에 대 한 자세한 내용을 보려면 다음 섹션의 항목은를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="34b3e-p104">There are many other reporting cmdlets available for Exchange Online, Lync Online, and SharePoint Online as well as others for message tracing that you can use. To find out more about the available reporting cmdlets and the Office 365 Reporting web service, see the topics in the following section.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="34b3e-119">See also</span><span class="sxs-lookup"><span data-stu-id="34b3e-119">See also</span></span>

#### 

[<span data-ttu-id="34b3e-120">Office 365 보고 웹 서비스</span><span class="sxs-lookup"><span data-stu-id="34b3e-120">Office 365 Reporting web service</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532777)
  
[<span data-ttu-id="34b3e-121">Exchange Online의 보고 cmdlet</span><span class="sxs-lookup"><span data-stu-id="34b3e-121">Reporting cmdlets in Exchange Online</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=526430)
  
[<span data-ttu-id="34b3e-122">파트너에 대 한 도움말</span><span class="sxs-lookup"><span data-stu-id="34b3e-122">Help for partners</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=533477)

