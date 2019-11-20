---
title: Office 365에서 Windows PowerShell을 사용하여 보고서 만들기
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 06/22/2018
audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Office_Other
ms.assetid: 1ea4d4ec-af89-496f-9678-701867f5a6fc
description: '요약: Office 365 PowerShell을 사용하여 Microsoft 365 관리 센터에서 생성할 수 없는 보고서를 만듭니다.'
ms.openlocfilehash: 4303f03c282c84972428ab8e5010aa316f40c90a
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2019
ms.locfileid: "38746261"
---
# <a name="use-windows-powershell-to-create-reports-in-office-365"></a><span data-ttu-id="b8635-103">Office 365에서 Windows PowerShell을 사용하여 보고서 만들기</span><span class="sxs-lookup"><span data-stu-id="b8635-103">Use Windows PowerShell to create reports in Office 365</span></span>

<span data-ttu-id="b8635-104">Microsoft 365 관리 센터에서는 다양한 보고서가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8635-104">There are many different reports available in the Microsoft 365 admin center.</span></span> <span data-ttu-id="b8635-105">그러나 이러한 보고서에는 제공되는 정보가 너무 많거나 부족할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8635-105">However, these reports only provide so much information and sometimes you need more.</span></span> <span data-ttu-id="b8635-106">그럴 때는 Office 365 PowerShell이 필요한 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="b8635-106">That's when you need Office 365 PowerShell</span></span>
  
<span data-ttu-id="b8635-107">다음 문서에서는 Office 365 PowerShell을 사용하여 Office 365 테넌트에서 정보를 얻는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b8635-107">These articles that describe how to use Office 365 PowerShell to obtain information from your Office 365 tenant:</span></span>
  
- <span data-ttu-id="b8635-108">Office 365 PowerShell을 사용하여 보고 작업 시작</span><span class="sxs-lookup"><span data-stu-id="b8635-108">Getting started with reporting using Office 365 PowerShell:</span></span>
    
  - [<span data-ttu-id="b8635-109">Office 365 PowerShell은 Office 365 관리 센터에서는 볼 수 없는 추가 정보를 제공할 수 있음</span><span class="sxs-lookup"><span data-stu-id="b8635-109">Office 365 PowerShell can reveal additional information that you cannot see with the Admin center</span></span>](https://technet.microsoft.com/library/dn568034.aspx#reveal)
    
  - [<span data-ttu-id="b8635-110">Office 365 PowerShell은 데이터를 필터링하는 데 유용함</span><span class="sxs-lookup"><span data-stu-id="b8635-110">Office 365 PowerShell is great at filtering data</span></span>](https://technet.microsoft.com/library/dn568034.aspx#filter)
    
  - [<span data-ttu-id="b8635-111">Office 365 PowerShell을 사용하면 데이터 쉽게 인쇄 또는 저장할 수 있음</span><span class="sxs-lookup"><span data-stu-id="b8635-111">Office 365 PowerShell makes it easy to print or save data</span></span>](https://technet.microsoft.com/library/dn568034.aspx#printsave)
    
- <span data-ttu-id="b8635-112">사용자 계정 및 라이선스에 대한 보고서:</span><span class="sxs-lookup"><span data-stu-id="b8635-112">Reports for user accounts and licenses:</span></span>
    
  - [<span data-ttu-id="b8635-113">라이선스 및 Office 365 PowerShell을 사용 하 여 서비스를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8635-113">View licenses and services with Office 365 PowerShell</span></span>](view-licenses-and-services-with-office-365-powershell.md)
    
  - [<span data-ttu-id="b8635-114">Office 365 PowerShell을 사용 하 여 허가 된 / 허가 되지 않은 사용자 보기</span><span class="sxs-lookup"><span data-stu-id="b8635-114">View licensed and unlicensed users with Office 365 PowerShell</span></span>](view-licensed-and-unlicensed-users-with-office-365-powershell.md)
    
  - [<span data-ttu-id="b8635-115">Office 365 PowerShell을 사용 하 여 계정 라이센스와 서비스 정보 보기</span><span class="sxs-lookup"><span data-stu-id="b8635-115">View account license and service details with Office 365 PowerShell</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
    
  - [<span data-ttu-id="b8635-116">Office 365 PowerShell을 사용한 사용자 계정 보기</span><span class="sxs-lookup"><span data-stu-id="b8635-116">View user accounts with Office 365 PowerShell</span></span>](view-user-accounts-with-office-365-powershell.md)
    
- <span data-ttu-id="b8635-117">SharePoint Online용 보고서:</span><span class="sxs-lookup"><span data-stu-id="b8635-117">Reports for SharePoint Online:</span></span>
    
  - [<span data-ttu-id="b8635-118">Office 365 PowerShell을 사용하여 SharePoint Online 사용자 및 그룹 관리</span><span class="sxs-lookup"><span data-stu-id="b8635-118">Manage SharePoint Online users and groups with Office 365 PowerShell</span></span>](https://technet.microsoft.com/library/9680af2e-a965-4e62-92ee-da72105c7800.aspx)
    
  - [<span data-ttu-id="b8635-119">Manage SharePoint Online site groups with Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="b8635-119">Manage SharePoint Online site groups with Office 365 PowerShell</span></span>](https://technet.microsoft.com/library/122f4099-c78d-4cce-bab0-4343b04596ae.aspx)
    
- <span data-ttu-id="b8635-120">Exchange Online용 보고서:</span><span class="sxs-lookup"><span data-stu-id="b8635-120">Reports for Exchange Online:</span></span>
    
  - [<span data-ttu-id="b8635-121">Display Exchange Online mailbox information with Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="b8635-121">Display Exchange Online mailbox information with Office 365 PowerShell</span></span>](https://technet.microsoft.com/library/13843002-56ca-4b75-81c5-84386522b01b.aspx)
    
  - [<span data-ttu-id="b8635-122">Display Exchange Online reports with Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="b8635-122">Display Exchange Online reports with Office 365 PowerShell</span></span>](https://technet.microsoft.com/library/4873a063-9fc4-4ed9-826a-6e935fef61d4.aspx)
    
## <a name="see-also"></a><span data-ttu-id="b8635-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b8635-123">See also</span></span>

[<span data-ttu-id="b8635-124">Office 365 PowerShell 사용한 Office 365 관리</span><span class="sxs-lookup"><span data-stu-id="b8635-124">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="b8635-125">Office 365 PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="b8635-125">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
  
[<span data-ttu-id="b8635-126">Office 365 PowerShell을 사용하여 SharePoint Online 관리</span><span class="sxs-lookup"><span data-stu-id="b8635-126">Manage SharePoint Online with Office 365 PowerShell</span></span>](manage-sharepoint-online-with-office-365-powershell.md)
  
[<span data-ttu-id="b8635-127">사용자 계정 및 Office 365 PowerShell을 사용 하 여 라이센스 관리</span><span class="sxs-lookup"><span data-stu-id="b8635-127">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
