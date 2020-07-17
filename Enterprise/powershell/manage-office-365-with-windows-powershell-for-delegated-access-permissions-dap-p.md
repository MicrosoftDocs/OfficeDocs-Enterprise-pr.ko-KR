---
title: DAP (위임 된 액세스 권한) 파트너에 대해 Windows PowerShell을 사용 하 여 Microsoft 365을 관리 합니다.
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- M365-subscription-management
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: be497751-596f-431d-b256-0a89d36a47ce
description: '요약: 배포 및 CSP (클라우드 솔루션 공급자) 파트너는 Windows PowerShell을 사용 하 여 Microsoft 365 고객 테 넌 트를 관리할 수 있습니다.'
ms.openlocfilehash: 00e60693ad10b705765da9ed57142c893a74b034
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998224"
---
# <a name="manage-microsoft-365-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="5b6aa-103">DAP (위임 된 액세스 권한) 파트너에 대해 Windows PowerShell을 사용 하 여 Microsoft 365을 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b6aa-103">Manage Microsoft 365 with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

<span data-ttu-id="5b6aa-104">DAP(위임된 액세스 권한) 파트너는 Syndication 및 CSP(클라우드 솔루션 공급자) 파트너입니다.</span><span class="sxs-lookup"><span data-stu-id="5b6aa-104">Delegated Access Permission (DAP) partners are Syndication and Cloud Solution Providers (CSP) Partners.</span></span> <span data-ttu-id="5b6aa-105">이러한 공급자는 다른 회사의 네트워크 또는 전자 통신 공급자인 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="5b6aa-105">They are frequently network or telecom providers to other companies.</span></span> <span data-ttu-id="5b6aa-106">Microsoft 365 구독을 고객에 게 서비스 제공으로 번들 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b6aa-106">They bundle Microsoft 365 subscriptions into their service offerings to their customers.</span></span> <span data-ttu-id="5b6aa-107">Microsoft 365 구독을 판매할 때 고객 테 넌 트에 대 한 관리 및 보고를 수행할 수 있도록 사용자에 게 테 넌 트에 대 한 "대신 (AOBO) 사용 권한을 자동으로 부여 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b6aa-107">When they sell a Microsoft 365 subscription, they are automatically granted Administer On Behalf Of (AOBO) permissions to the customer tenancies so they can administer and report on the customer tenancies.</span></span> <span data-ttu-id="5b6aa-108">이는 Microsoft 365 관리 센터에서 수행 하는 것이 어렵고 시간이 많이 소요 되는 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="5b6aa-108">At best, this is difficult and time consuming to do in the Microsoft 365 admin center.</span></span> <span data-ttu-id="5b6aa-109">모든 고객 **TenantIds** 를 나열하거나 모든 사용자를 고객 테넌트 및 Office 365용 Windows PowerShell을 사용하여 할당된 라이선스에서 식별하는 등의 관리 작업을 수행하는 것이 훨씬 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="5b6aa-109">It is much easier to do administrative tasks like listing all the customer **TenantIds** and their domains or identifying all users in a customer tenancy and what licenses they are assigned by using Windows PowerShell for Office 365.</span></span> <span data-ttu-id="5b6aa-110">어떤 경우에는 Office 365용 Windows PowerShell에서만 이러한 관리 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b6aa-110">In some cases, it is possible to do these administrative tasks only in Windows PowerShell for Office 365.</span></span> <span data-ttu-id="5b6aa-111">다음은 Syndication 및 CSP 파트너가 고객 테넌트를 관리하는 데 가장 자주 사용하는 시나리오 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="5b6aa-111">Here are samples of scenarios that Syndication and CSP partners most frequently use to administer their customer tenancies:</span></span>
  
## 

- [<span data-ttu-id="5b6aa-112">DAP (위임 된 액세스 권한) 파트너에 대해 Windows PowerShell을 사용 하 여 Microsoft 365 테 넌 트 관리</span><span class="sxs-lookup"><span data-stu-id="5b6aa-112">Manage Microsoft 365 tenants with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>](manage-office-365-tenants-with-windows-powershell-for-delegated-access-permissio.md)
    
- [<span data-ttu-id="5b6aa-113">DAP(위임된 액세스 권한) 파트너용 Windows PowerShell을 사용하여 클라이언트 테넌트에 도메인 추가</span><span class="sxs-lookup"><span data-stu-id="5b6aa-113">Add a domain to a client tenancy with Windows PowerShell for Delegated Access Permission (DAP) partners</span></span>](add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-pe.md)
    
- [<span data-ttu-id="5b6aa-114">DAP(위임된 액세스 권한) 파트너용 원격 Windows PowerShell을 사용하여 Exchange Online 테넌트에 연결</span><span class="sxs-lookup"><span data-stu-id="5b6aa-114">Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)
    
- [<span data-ttu-id="5b6aa-115">DAP(위임된 액세스 권한) 파트너용 Windows PowerShell을 사용하여 고객 테넌트 보고 데이터 검색</span><span class="sxs-lookup"><span data-stu-id="5b6aa-115">Retrieve customer tenant reporting data with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>](retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-ac.md)
    

    

