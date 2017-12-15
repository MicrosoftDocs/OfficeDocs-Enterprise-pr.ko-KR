---
title: "Office 365에서 Windows PowerShell을 사용하여 보고서 만들기"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- DecEntMigration
ms.assetid: 1ea4d4ec-af89-496f-9678-701867f5a6fc
description: "요약: Office 365 관리 센터에서 생성할 수 없는 있는 만들기를 사용 하 여 Office 365 PowerShell 보고 합니다."
ms.openlocfilehash: b1cbbbef73a266a62a417d2714fefcd630c604c4
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2017
---
# <a name="use-windows-powershell-to-create-reports-in-office-365"></a><span data-ttu-id="e2193-103">Office 365에서 Windows PowerShell을 사용하여 보고서 만들기</span><span class="sxs-lookup"><span data-stu-id="e2193-103">Use Windows PowerShell to create reports in Office 365</span></span>

 <span data-ttu-id="e2193-104">**요약:** Office 365 PowerShell을 사용 하 여 Office 365 관리 센터에서 생성할 수 없는 보고서를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2193-104">**Summary:** Use Office 365 PowerShell to create reports that you cannot produce in the Office 365 Admin center.</span></span>
  
<span data-ttu-id="e2193-p101">Office 365 관리 센터에서 사용할 수 있는 다양 한 보고서 있습니다. 그러나 이러한 보고서만 너무 많은 정보를 제공 하 고 더 필요한 경우에 따라 합니다. 이 경우 Office 365 PowerShell 필요</span><span class="sxs-lookup"><span data-stu-id="e2193-p101">There are many different reports available in the Office 365 Admin center. However, these reports only provide so much information and sometimes you need more. That's when you need Office 365 PowerShell</span></span>
  
<span data-ttu-id="e2193-108">Office 365 테 넌 트에서 정보를 가져오려면 Office 365 PowerShell을 사용 하는 방법에 설명 하는 이러한 문서:</span><span class="sxs-lookup"><span data-stu-id="e2193-108">These articles that describe how to use Office 365 PowerShell to obtain information from your Office 365 tenant:</span></span>
  
- <span data-ttu-id="e2193-109">Office 365 PowerShell을 사용 하 여 보고 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2193-109">Getting started with reporting using Office 365 PowerShell:</span></span>
    
  - [<span data-ttu-id="e2193-110">Office 365 PowerShell 관리 센터를 볼 수 없습니다는 추가 정보를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2193-110">Office 365 PowerShell can reveal additional information that you cannot see with the Admin center</span></span>](https://technet.microsoft.com/library/dn568034.aspx#reveal)
    
  - [<span data-ttu-id="e2193-111">Office 365 PowerShell은 데이터를 필터링에 뛰어난</span><span class="sxs-lookup"><span data-stu-id="e2193-111">Office 365 PowerShell is great at filtering data</span></span>](https://technet.microsoft.com/library/dn568034.aspx#filter)
    
  - [<span data-ttu-id="e2193-112">Office 365 PowerShell을 통해 손쉽게 데이터 인쇄 또는 저장</span><span class="sxs-lookup"><span data-stu-id="e2193-112">Office 365 PowerShell makes it easy to print or save data</span></span>](https://technet.microsoft.com/library/dn568034.aspx#printsave)
    
- <span data-ttu-id="e2193-113">사용자 계정 및 라이선스에 대한 보고서:</span><span class="sxs-lookup"><span data-stu-id="e2193-113">Reports for user accounts and licenses:</span></span>
    
  - [<span data-ttu-id="e2193-114">라이선스 및 Office 365 PowerShell을 사용 하 여 서비스 보기</span><span class="sxs-lookup"><span data-stu-id="e2193-114">View licenses and services with Office 365 PowerShell</span></span>](view-licenses-and-services-with-office-365-powershell.md)
    
  - [<span data-ttu-id="e2193-115">Office 365 powershell 사용이 허가 된 및 허가 되지 않은 사용자 보기</span><span class="sxs-lookup"><span data-stu-id="e2193-115">View licensed and unlicensed users with Office 365 PowerShell</span></span>](view-licensed-and-unlicensed-users-with-office-365-powershell.md)
    
  - [<span data-ttu-id="e2193-116">Office 365 powershell 계정 라이선스 및 서비스 정보 보기</span><span class="sxs-lookup"><span data-stu-id="e2193-116">View account license and service details with Office 365 PowerShell</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
    
  - [<span data-ttu-id="e2193-117">Office 365 PowerShell을 사용한 사용자 계정 보기</span><span class="sxs-lookup"><span data-stu-id="e2193-117">View user accounts with Office 365 PowerShell</span></span>](view-user-accounts-with-office-365-powershell.md)
    
- <span data-ttu-id="e2193-118">SharePoint Online용 보고서:</span><span class="sxs-lookup"><span data-stu-id="e2193-118">Reports for SharePoint Online:</span></span>
    
  - [<span data-ttu-id="e2193-119">Office 365 PowerShell 있는 SharePoint Online 사용자 및 그룹 관리</span><span class="sxs-lookup"><span data-stu-id="e2193-119">Manage SharePoint Online users and groups with Office 365 PowerShell</span></span>](http://technet.microsoft.com/library/9680af2e-a965-4e62-92ee-da72105c7800.aspx)
    
  - [<span data-ttu-id="e2193-120">Office 365 PowerShell을 사용한 SharePoint Online 사이트 그룹 관리</span><span class="sxs-lookup"><span data-stu-id="e2193-120">Manage SharePoint Online site groups with Office 365 PowerShell</span></span>](http://technet.microsoft.com/library/122f4099-c78d-4cce-bab0-4343b04596ae.aspx)
    
- <span data-ttu-id="e2193-121">Exchange Online용 보고서:</span><span class="sxs-lookup"><span data-stu-id="e2193-121">Reports for Exchange Online:</span></span>
    
  - [<span data-ttu-id="e2193-122">Office 365 PowerShell을 사용한 Exchange Online 사서함 정보를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2193-122">Display Exchange Online mailbox information with Office 365 PowerShell</span></span>](http://technet.microsoft.com/library/13843002-56ca-4b75-81c5-84386522b01b.aspx)
    
  - [<span data-ttu-id="e2193-123">Office 365 PowerShell을 사용 하 여 Exchange Online 보고서를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2193-123">Display Exchange Online reports with Office 365 PowerShell</span></span>](http://technet.microsoft.com/library/4873a063-9fc4-4ed9-826a-6e935fef61d4.aspx)
    
## <a name="see-also"></a><span data-ttu-id="e2193-124">See also</span><span class="sxs-lookup"><span data-stu-id="e2193-124">See also</span></span>

#### 

[<span data-ttu-id="e2193-125">Office 365 PowerShell로 Office 365 관리</span><span class="sxs-lookup"><span data-stu-id="e2193-125">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="e2193-126">Office 365 PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="e2193-126">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
  
[<span data-ttu-id="e2193-127">Office 365 PowerShell 사용한 SharePoint Online 관리</span><span class="sxs-lookup"><span data-stu-id="e2193-127">Manage SharePoint Online with Office 365 PowerShell</span></span>](manage-sharepoint-online-with-office-365-powershell.md)
  
[<span data-ttu-id="e2193-128">사용자 계정 및 Office 365 powershell 라이선스 관리</span><span class="sxs-lookup"><span data-stu-id="e2193-128">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="e2193-129">Excel을 사용 하 여 Office 365 보고 데이터를 검색 하려면</span><span class="sxs-lookup"><span data-stu-id="e2193-129">Using Excel to Retrieve Office 365 Reporting Data</span></span>](using-excel-to-retrieve-office-365-reporting-data.md)

