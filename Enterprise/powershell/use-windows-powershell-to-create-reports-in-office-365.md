---
title: PowerShell을 사용 하 여 Microsoft 365에 대 한 보고서 만들기
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: ''
ms.assetid: 1ea4d4ec-af89-496f-9678-701867f5a6fc
description: '요약: microsoft 365 용 PowerShell을 사용 하 여 Microsoft 365 관리 센터에서 생성할 수 없는 보고서를 만듭니다.'
ms.openlocfilehash: 855f6529445b95dd949fb672f978a82f1afd6149
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/22/2020
ms.locfileid: "45229804"
---
# <a name="use-powershell-to-create-reports-for-microsoft-365"></a><span data-ttu-id="db842-103">PowerShell을 사용 하 여 Microsoft 365에 대 한 보고서 만들기</span><span class="sxs-lookup"><span data-stu-id="db842-103">Use PowerShell to create reports for Microsoft 365</span></span>

<span data-ttu-id="db842-104">*이 문서는 Microsoft 365 Enterprise 및 Office 365 Enterprise에 모두 적용 됩니다.*</span><span class="sxs-lookup"><span data-stu-id="db842-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="db842-105">Microsoft 365 관리 센터에서는 다양한 보고서가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="db842-105">There are many different reports available in the Microsoft 365 admin center.</span></span> <span data-ttu-id="db842-106">그러나 이러한 보고서에는 제공되는 정보가 너무 많거나 부족할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db842-106">However, these reports only provide so much information and sometimes you need more.</span></span> <span data-ttu-id="db842-107">Microsoft 365 용 PowerShell이 필요한 경우</span><span class="sxs-lookup"><span data-stu-id="db842-107">That's when you need PowerShell for Microsoft 365</span></span>
  
<span data-ttu-id="db842-108">다음 문서에서는 Microsoft 365 용 PowerShell을 사용 하 여 Microsoft 365 테 넌 트에서 정보를 가져오는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="db842-108">These articles that describe how to use PowerShell for Microsoft 365 to obtain information from your Microsoft 365 tenant:</span></span>
  
- <span data-ttu-id="db842-109">Microsoft 365 용 PowerShell을 사용 하 여 보고 기능을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="db842-109">Getting started with reporting using PowerShell for Microsoft 365:</span></span>
    
  - [<span data-ttu-id="db842-110">Microsoft 365 용 PowerShell을 사용 하면 관리 센터에서는 볼 수 없는 추가 정보를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db842-110">PowerShell for Microsoft 365 can reveal additional information that you cannot see with the Admin center</span></span>](https://technet.microsoft.com/library/dn568034.aspx#reveal)
    
  - [<span data-ttu-id="db842-111">Microsoft 365 용 PowerShell은 데이터를 필터링 하는 데 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="db842-111">PowerShell for Microsoft 365 is great at filtering data</span></span>](https://technet.microsoft.com/library/dn568034.aspx#filter)
    
  - [<span data-ttu-id="db842-112">Microsoft 365 용 PowerShell을 사용 하면 데이터를 쉽게 인쇄 하거나 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db842-112">PowerShell for Microsoft 365 makes it easy to print or save data</span></span>](https://technet.microsoft.com/library/dn568034.aspx#printsave)
    
- <span data-ttu-id="db842-113">사용자 계정 및 라이선스에 대한 보고서:</span><span class="sxs-lookup"><span data-stu-id="db842-113">Reports for user accounts and licenses:</span></span>
    
  - [<span data-ttu-id="db842-114">PowerShell을 사용 하 여 Microsoft 365 라이선스 및 서비스 보기</span><span class="sxs-lookup"><span data-stu-id="db842-114">View Microsoft 365 licenses and services with PowerShell</span></span>](view-licenses-and-services-with-office-365-powershell.md)
    
  - [<span data-ttu-id="db842-115">PowerShell을 사용 하 여 Microsoft 365 허가 및 라이선스가 없는 사용자 보기</span><span class="sxs-lookup"><span data-stu-id="db842-115">View Microsoft 365 licensed and unlicensed users with PowerShell</span></span>](view-licensed-and-unlicensed-users-with-office-365-powershell.md)
    
  - [<span data-ttu-id="db842-116">PowerShell을 사용 하 여 Microsoft 365 계정 라이선스 및 서비스 세부 정보 보기</span><span class="sxs-lookup"><span data-stu-id="db842-116">View Microsoft 365 account license and service details with PowerShell</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
    
  - [<span data-ttu-id="db842-117">PowerShell을 사용 하 여 Microsoft 365 사용자 계정 보기</span><span class="sxs-lookup"><span data-stu-id="db842-117">View Microsoft 365 user accounts with PowerShell</span></span>](view-user-accounts-with-office-365-powershell.md)
    
- <span data-ttu-id="db842-118">SharePoint Online용 보고서:</span><span class="sxs-lookup"><span data-stu-id="db842-118">Reports for SharePoint Online:</span></span>
    
  - [<span data-ttu-id="db842-119">SharePoint Online 관리 셸 시작하기</span><span class="sxs-lookup"><span data-stu-id="db842-119">Get started with SharePoint Online Management Shell</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)
    
  - [<span data-ttu-id="db842-120">PowerShell을 사용 하 여 SharePoint Online 사이트 그룹 관리</span><span class="sxs-lookup"><span data-stu-id="db842-120">Manage SharePoint Online site groups with PowerShell</span></span>](https://technet.microsoft.com/library/122f4099-c78d-4cce-bab0-4343b04596ae.aspx)
    
- <span data-ttu-id="db842-121">Exchange Online용 보고서:</span><span class="sxs-lookup"><span data-stu-id="db842-121">Reports for Exchange Online:</span></span>
    
  - [<span data-ttu-id="db842-122">PowerShell을 사용하여 Exchange Online 사서함 정보 표시</span><span class="sxs-lookup"><span data-stu-id="db842-122">Display Exchange Online mailbox information with PowerShell</span></span>](https://technet.microsoft.com/library/13843002-56ca-4b75-81c5-84386522b01b.aspx)
    
  - [<span data-ttu-id="db842-123">PowerShell 사용하여 Exchange Online 보고서 표시</span><span class="sxs-lookup"><span data-stu-id="db842-123">Display Exchange Online reports with PowerShell</span></span>](https://technet.microsoft.com/library/4873a063-9fc4-4ed9-826a-6e935fef61d4.aspx)
    
## <a name="see-also"></a><span data-ttu-id="db842-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="db842-124">See also</span></span>

[<span data-ttu-id="db842-125">PowerShell을 사용 하 여 Microsoft 365 관리</span><span class="sxs-lookup"><span data-stu-id="db842-125">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="db842-126">Microsoft 365 용 PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="db842-126">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)
  
[<span data-ttu-id="db842-127">PowerShell을 사용 하 여 SharePoint Online 관리</span><span class="sxs-lookup"><span data-stu-id="db842-127">Manage SharePoint Online with PowerShell</span></span>](manage-sharepoint-online-with-office-365-powershell.md)
  
[<span data-ttu-id="db842-128">PowerShell을 사용 하 여 Microsoft 365 사용자 계정, 라이선스 및 그룹 관리</span><span class="sxs-lookup"><span data-stu-id="db842-128">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
