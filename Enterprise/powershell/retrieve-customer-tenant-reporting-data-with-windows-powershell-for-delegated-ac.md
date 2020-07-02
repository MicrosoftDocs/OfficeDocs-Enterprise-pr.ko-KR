---
title: DAP(위임된 액세스 권한) 파트너용 Windows PowerShell을 사용하여 고객 테넌트 보고 데이터 검색
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
ms.custom: ''
ms.assetid: 893e5275-30b3-433f-8ecd-644f78f513e2
description: 요약:Microsoft Exchange Online용 원격Windows PowerShell을 사용하여 개별 고객 테넌트에서 보고서를 검색합니다.
ms.openlocfilehash: d4b8d931b6b8ea8c7b8467dd70326e1b0fbfc3d5
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998627"
---
# <a name="retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="a3825-103">DAP(위임된 액세스 권한) 파트너용 Windows PowerShell을 사용하여 고객 테넌트 보고 데이터 검색</span><span class="sxs-lookup"><span data-stu-id="a3825-103">Retrieve customer tenant reporting data with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

<span data-ttu-id="a3825-104">Microsoft Exchange Online 용 원격 Windows PowerShell을 사용 하 여 개별 고객 테 넌 트에서 보고서를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="a3825-104">Use remote Windows PowerShell for Microsoft Exchange Online to retrieve reports from individual customer tenants.</span></span>
  
<span data-ttu-id="a3825-105">Syndication and Cloud Solution Provider (CSP) partners can access the data that makes up customer tenant reports directly via remoteWindows PowerShell for Exchange Online PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a3825-105">Syndication and Cloud Solution Provider (CSP) partners can access the data that makes up customer tenant reports directly via remoteWindows PowerShell for Exchange Online PowerShell.</span></span> <span data-ttu-id="a3825-106">This lets partners collect and save the reporting data and then perform other operations on it.</span><span class="sxs-lookup"><span data-stu-id="a3825-106">This lets partners collect and save the reporting data and then perform other operations on it.</span></span> <span data-ttu-id="a3825-107">After you open a remote connection, retrieving reporting data about a customer tenancy is identical to running any cmdlet against a customer tenancy.</span><span class="sxs-lookup"><span data-stu-id="a3825-107">After you open a remote connection, retrieving reporting data about a customer tenancy is identical to running any cmdlet against a customer tenancy.</span></span>
  
<span data-ttu-id="a3825-108">In this article, you use remoteWindows PowerShell for Exchange Online to connect to a single customer tenancy and retrieve a report.</span><span class="sxs-lookup"><span data-stu-id="a3825-108">In this article, you use remoteWindows PowerShell for Exchange Online to connect to a single customer tenancy and retrieve a report.</span></span> <span data-ttu-id="a3825-109">By default, Windows PowerShell does not support aggregating reporting data from multiple customer tenancies.</span><span class="sxs-lookup"><span data-stu-id="a3825-109">By default, Windows PowerShell does not support aggregating reporting data from multiple customer tenancies.</span></span> <span data-ttu-id="a3825-110">The reports you retrieve with this procedure are only for the  _DelegatedOrg_ that you connect to.</span><span class="sxs-lookup"><span data-stu-id="a3825-110">The reports you retrieve with this procedure are only for the  _DelegatedOrg_ that you connect to.</span></span>
  
 
## <a name="before-you-begin"></a><span data-ttu-id="a3825-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="a3825-111">Before you begin</span></span>

- <span data-ttu-id="a3825-112">You need to connect to your Exchange Online tenant by using remote Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a3825-112">You need to connect to your Exchange Online tenant by using remote Windows PowerShell.</span></span> <span data-ttu-id="a3825-113">For instructions, see [Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)</span><span class="sxs-lookup"><span data-stu-id="a3825-113">For instructions, see [Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)</span></span>
    
## <a name="run-the-get-stalemailboxreport-sample"></a><span data-ttu-id="a3825-114">Get-StaleMailboxReport 샘플 실행</span><span class="sxs-lookup"><span data-stu-id="a3825-114">Run the Get-StaleMailboxReport sample</span></span>

<span data-ttu-id="a3825-115">원격 세션을 Exchange Online으로 연 후 이 명령을 실행하여 날짜 범위 2015/03/25에서 2015/03/31까지에 대해 **Get-StaleMailboxReport** 를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="a3825-115">After you have opened a remote session to Exchange Online, run this command to retrieve the **Get-StaleMailboxReport** for the date range 03/25/2015 through 03/31/2015.</span></span>
  
```
Get-StaleMailboxReport -StartDate 03/25/2015 -EndDate 03/31/2015
```

<span data-ttu-id="a3825-116">There are many other reporting cmdlets available for Exchange Online, Lync Online, and SharePoint Online as well as others for message tracing that you can use.</span><span class="sxs-lookup"><span data-stu-id="a3825-116">There are many other reporting cmdlets available for Exchange Online, Lync Online, and SharePoint Online as well as others for message tracing that you can use.</span></span> <span data-ttu-id="a3825-117">To find out more about the available reporting cmdlets and the Office 365 Reporting web service, see the topics in the following section.</span><span class="sxs-lookup"><span data-stu-id="a3825-117">To find out more about the available reporting cmdlets and the Office 365 Reporting web service, see the topics in the following section.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a3825-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a3825-118">See also</span></span>

#### 

[<span data-ttu-id="a3825-119">Office 365 보고 웹 서비스</span><span class="sxs-lookup"><span data-stu-id="a3825-119">Office 365 Reporting web service</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532777)
  
[<span data-ttu-id="a3825-120">Exchange Online의 보고 cmdlet</span><span class="sxs-lookup"><span data-stu-id="a3825-120">Reporting cmdlets in Exchange Online</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=526430)
  
[<span data-ttu-id="a3825-121">파트너를 위한 도움말</span><span class="sxs-lookup"><span data-stu-id="a3825-121">Help for partners</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=533477)

