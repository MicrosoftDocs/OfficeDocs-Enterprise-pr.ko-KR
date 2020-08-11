---
title: DAP 파트너에 대해 Windows PowerShell을 사용 하 여 고객 테 넌 트 보고 데이터 검색
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
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
ms.assetid: 893e5275-30b3-433f-8ecd-644f78f513e2
description: '요약: Microsoft Exchange Online용 원격Windows PowerShell을 사용하여 개별 고객 테넌트에서 보고서를 검색합니다.'
ms.openlocfilehash: 69c441f1e241f964ec3ef24a915331a8980a4794
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606244"
---
# <a name="retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="f6d5c-103">DAP(위임된 액세스 권한) 파트너용 Windows PowerShell을 사용하여 고객 테넌트 보고 데이터 검색</span><span class="sxs-lookup"><span data-stu-id="f6d5c-103">Retrieve customer tenant reporting data with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

<span data-ttu-id="f6d5c-104">*이 문서는 Microsoft 365 Enterprise와 Office 365 Enterprise에 모두 적용됩니다.*</span><span class="sxs-lookup"><span data-stu-id="f6d5c-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="f6d5c-105">Microsoft Exchange Online 용 원격 Windows PowerShell을 사용 하 여 개별 고객 테 넌 트에서 보고서를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6d5c-105">Use remote Windows PowerShell for Microsoft Exchange Online to retrieve reports from individual customer tenants.</span></span>
  
<span data-ttu-id="f6d5c-106">배포 및 CSP (클라우드 솔루션 공급자) 파트너는 원격 Windows PowerShell을 사용 하 여 Exchange Online PowerShell을 통해 직접 고객 테 넌 트 보고서를 구성 하는 데이터에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6d5c-106">Syndication and Cloud Solution Provider (CSP) partners can access the data that makes up customer tenant reports directly via remote Windows PowerShell for Exchange Online PowerShell.</span></span> <span data-ttu-id="f6d5c-107">이를 통해 파트너는 보고 데이터를 수집하고 저장한 후 여기에서 다른 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6d5c-107">This lets partners collect and save the reporting data and then perform other operations on it.</span></span> <span data-ttu-id="f6d5c-108">원격 연결을 연 후 고객 테넌트에 대한 보고 데이터 검색은 고객 테넌트에 대해 cmdlet을 실행하는 것과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="f6d5c-108">After you open a remote connection, retrieving reporting data about a customer tenancy is identical to running any cmdlet against a customer tenancy.</span></span>
  
<span data-ttu-id="f6d5c-109">이 문서에서는 Exchange Online 용 원격 Windows PowerShell을 사용 하 여 단일 고객의 테 넌 트에 연결 하 고 보고서를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6d5c-109">In this article, you use remote Windows PowerShell for Exchange Online to connect to a single customer tenancy and retrieve a report.</span></span> <span data-ttu-id="f6d5c-110">기본적으로 Windows PowerShell에서는 여러 고객 테 넌 트의 보고 데이터 집계를 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f6d5c-110">By default, Windows PowerShell does not support aggregating reporting data from multiple customer tenancies.</span></span> <span data-ttu-id="f6d5c-111">이 절차를 사용 하 여 검색 하는 보고서는 연결 하는 _DelegatedOrg_ 에만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6d5c-111">The reports you retrieve with this procedure are only for the  _DelegatedOrg_ that you connect to.</span></span>
  
 
## <a name="before-you-begin"></a><span data-ttu-id="f6d5c-112">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="f6d5c-112">Before you begin</span></span>

- <span data-ttu-id="f6d5c-p103">원격 Windows PowerShell을 사용하여 Exchange Online 테넌트에 연결해야 합니다. 자세한 내용은 [DAP(위임된 액세스 권한) 파트너용 원격 Windows PowerShell을 사용하여 Exchange Online 테넌트에 연결](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f6d5c-p103">You need to connect to your Exchange Online tenant by using remote Windows PowerShell. For instructions, see [Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)</span></span>
    
## <a name="run-the-get-stalemailboxreport-sample"></a><span data-ttu-id="f6d5c-115">Get-StaleMailboxReport 샘플 실행</span><span class="sxs-lookup"><span data-stu-id="f6d5c-115">Run the Get-StaleMailboxReport sample</span></span>

<span data-ttu-id="f6d5c-116">원격 세션을 Exchange Online으로 연 후 이 명령을 실행하여 날짜 범위 2015/03/25에서 2015/03/31까지에 대해 **Get-StaleMailboxReport** 를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="f6d5c-116">After you have opened a remote session to Exchange Online, run this command to retrieve the **Get-StaleMailboxReport** for the date range 03/25/2015 through 03/31/2015.</span></span>
  
```
Get-StaleMailboxReport -StartDate 03/25/2015 -EndDate 03/31/2015
```

<span data-ttu-id="f6d5c-p104">사용할 수 있는 메시지 추적에 대해 Exchange Online, Lync Online, SharePoint Online 등에 다양한 보고 cmdlet을 사용할 수 있습니다. 사용 가능한 보고 cmdlet 및 Office 365 보고 웹 서비스에 대한 자세한 내용은 다음 섹션의 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f6d5c-p104">There are many other reporting cmdlets available for Exchange Online, Lync Online, and SharePoint Online as well as others for message tracing that you can use. To find out more about the available reporting cmdlets and the Office 365 Reporting web service, see the topics in the following section.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="f6d5c-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f6d5c-119">See also</span></span>

#### 

[<span data-ttu-id="f6d5c-120">Office 365 보고 웹 서비스</span><span class="sxs-lookup"><span data-stu-id="f6d5c-120">Office 365 Reporting web service</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532777)
  
[<span data-ttu-id="f6d5c-121">Exchange Online의 보고 cmdlet</span><span class="sxs-lookup"><span data-stu-id="f6d5c-121">Reporting cmdlets in Exchange Online</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=526430)
  
[<span data-ttu-id="f6d5c-122">파트너를 위한 도움말</span><span class="sxs-lookup"><span data-stu-id="f6d5c-122">Help for partners</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=533477)

