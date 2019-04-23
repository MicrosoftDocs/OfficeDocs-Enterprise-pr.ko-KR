---
title: DAP(위임된 액세스 권한) 파트너용 Windows PowerShell을 사용하여 Office 365 관리
ms.author: chrfox
author: chrfox
manager: laurawi
ms.audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-subscription-management
ms.custom: ''
ms.assetid: be497751-596f-431d-b256-0a89d36a47ce
description: 요약:Syndication 및 CSP(클라우드 솔루션 공급자) 파트너에서는 Windows PowerShell을 사용하여 Office 365 고객 테넌트를 관리할 수 있습니다.
ms.openlocfilehash: 93b323d8de7016008ba7e4f75ff4b1c011adb9f2
ms.sourcegitcommit: 509bcf92580d7a0bcebbf6f1d10311d6b0014984
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "31992818"
---
# <a name="manage-office-365-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="ad383-103">DAP(위임된 액세스 권한) 파트너용 Windows PowerShell을 사용하여 Office 365 관리</span><span class="sxs-lookup"><span data-stu-id="ad383-103">Manage Office 365 with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

 <span data-ttu-id="ad383-104">**요약:** Syndication 및 CSP(클라우드 솔루션 공급자) 파트너에서는 Windows PowerShell을 사용하여 Office 365 고객 테넌트를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad383-104">**Summary:** Syndication and Cloud Solution Provider (CSP) partners can use Windows PowerShell to manage Office 365 customer tenants.</span></span>
  
<span data-ttu-id="ad383-105">DAP(위임된 액세스 권한) 파트너는 Syndication 및 CSP(클라우드 솔루션 공급자) 파트너입니다.</span><span class="sxs-lookup"><span data-stu-id="ad383-105">Delegated Access Permission (DAP) partners are Syndication and Cloud Solution Providers (CSP) Partners.</span></span> <span data-ttu-id="ad383-106">이러한 공급자는 다른 회사의 네트워크 또는 전자 통신 공급자인 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="ad383-106">They are frequently network or telecom providers to other companies.</span></span> <span data-ttu-id="ad383-107">이러한 공급자는 서비스와 Office 365 구독을 통합해서 고객에게 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ad383-107">They bundle Office 365 subscriptions into their service offerings to their customers.</span></span> <span data-ttu-id="ad383-108">Office 365 구독을 판매하는 경우 고객 테넌트에 대한 AOBO(관리 위임자) 권한이 자동으로 부여되므로 고객 테넌트를 관리하고 보고할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad383-108">When they sell an Office 365 subscription, they are automatically granted Administer On Behalf Of (AOBO) permissions to the customer tenancies so they can administer and report on the customer tenancies.</span></span> <span data-ttu-id="ad383-109">관리를 잘하더라도 Office 365 관리 센터에서의 수행 작업은 어렵고 시간이 많이 걸립니다.</span><span class="sxs-lookup"><span data-stu-id="ad383-109">At best, this is difficult and time consuming to do in the Office 365 admin center.</span></span> <span data-ttu-id="ad383-110">모든 고객 **TenantIds** 를 나열하거나 모든 사용자를 고객 테넌트 및 Office 365용 Windows PowerShell을 사용하여 할당된 라이선스에서 식별하는 등의 관리 작업을 수행하는 것이 훨씬 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="ad383-110">It is much easier to do administrative tasks like listing all the customer **TenantIds** and their domains or identifying all users in a customer tenancy and what licenses they are assigned by using Windows PowerShell for Office 365.</span></span> <span data-ttu-id="ad383-111">어떤 경우에는 Office 365용 Windows PowerShell에서만 이러한 관리 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad383-111">In some cases, it is possible to do these administrative tasks only in Windows PowerShell for Office 365.</span></span> <span data-ttu-id="ad383-112">다음은 Syndication 및 CSP 파트너가 고객 테넌트를 관리하는 데 가장 자주 사용하는 시나리오 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="ad383-112">Here are samples of scenarios that Syndication and CSP partners most frequently use to administer their customer tenancies:</span></span>
  
## 

- [<span data-ttu-id="ad383-113">DAP(위임된 액세스 권한) 파트너용 Windows PowerShell을 사용하여 Office 365 테넌트 관리</span><span class="sxs-lookup"><span data-stu-id="ad383-113">Manage Office 365 tenants with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>](manage-office-365-tenants-with-windows-powershell-for-delegated-access-permissio.md)
    
- [<span data-ttu-id="ad383-114">DAP(위임된 액세스 권한) 파트너용 Windows PowerShell을 사용하여 클라이언트 테넌트에 도메인 추가</span><span class="sxs-lookup"><span data-stu-id="ad383-114">Add a domain to a client tenancy with Windows PowerShell for Delegated Access Permission (DAP) partners</span></span>](add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-pe.md)
    
- [<span data-ttu-id="ad383-115">DAP(위임된 액세스 권한) 파트너용 원격 Windows PowerShell을 사용하여 Exchange Online 테넌트에 연결</span><span class="sxs-lookup"><span data-stu-id="ad383-115">Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)
    
- [<span data-ttu-id="ad383-116">DAP(위임된 액세스 권한) 파트너용 Windows PowerShell을 사용하여 고객 테넌트 보고 데이터 검색</span><span class="sxs-lookup"><span data-stu-id="ad383-116">Retrieve customer tenant reporting data with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>](retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-ac.md)
    

    

