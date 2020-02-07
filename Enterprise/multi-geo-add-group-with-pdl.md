---
title: 특정 PDL로 Office 365 그룹 만들기
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Multi-Geo 환경에서 지정된 기본 설정 데이터 위치를 사용하여 Office 365 그룹을 만드는 방법에 대해 알아봅니다.
ms.openlocfilehash: 5a6417f1758cd6c5e4eb9d4df9e7796d4309e62c
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843739"
---
# <a name="create-an-office-365-group-with-a-specific-pdl"></a><span data-ttu-id="25c3a-103">특정 PDL로 Office 365 그룹 만들기</span><span class="sxs-lookup"><span data-stu-id="25c3a-103">Create an Office 365 Group with a specific PDL</span></span>

<span data-ttu-id="25c3a-104">Multi-Gep 환경의 사용자가 Office 365 그룹을 만들 때 그룹 기본 설정 데이터 위치가 자동으로 사용자의 위치로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="25c3a-104">When users in a multi-geo environment create an Office 365 Group, the group preferred data location is automatically set to that of the user.</span></span> <span data-ttu-id="25c3a-105">전역, SharePoint, Exchange 관리자는 선택하는 모든 영역에서 그룹을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25c3a-105">Global, SharePoint, and Exchange Administrators can create groups in any region they select.</span></span> 

<span data-ttu-id="25c3a-106">특정 PDL로 그룹을 만들어야 할 경우 SharePoint 관리자 센터에서 만들거나 혹은 Exchange Online New-UnifiedGroup Microsoft PowerShell cmdlet을 사용하여 그룹을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25c3a-106">If you need to create a group with a specific PDL, you can do that using from the SharePoint admin center or through the Exchange Online New-UnifiedGroup Microsoft PowerShell cmdlet.</span></span> <span data-ttu-id="25c3a-107">이 작업을 진행 시 그룹 사서함 및 그룹과 연결된 SharePoint 사이트가 지정된 PDL에서 프로비저닝됩니다.</span><span class="sxs-lookup"><span data-stu-id="25c3a-107">When you do this, both the group mailbox and SharePoint site associated with the group will be provisioned in the specified PDL.</span></span>

<span data-ttu-id="25c3a-108">PDL을 사용하여 지정하는 Office 365 그룹을 만들려면 그룹 사이트를 만들 지리적 위치에서 SharePoint 관리 센터로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="25c3a-108">To create an Office 365 Group with the PDL that you specify, go to the SharePoint admin center in the geo location where you want to create the group site.</span></span>

<span data-ttu-id="25c3a-109">예:</span><span class="sxs-lookup"><span data-stu-id="25c3a-109">For example:</span></span>

<span data-ttu-id="25c3a-110">호주의 위치에서 그룹 사이트를 만드려는 경우 https://ContosoAUS-admin.sharepoint.com/_layouts/15/online/AdminHome.aspx#/siteManagement로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25c3a-110">If you wan to create a group site in your Australtia location, you can go to https://ContosoAUS-admin.sharepoint.com/_layouts/15/online/AdminHome.aspx#/siteManagement</span></span>

1. <span data-ttu-id="25c3a-111">**+ 만들기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="25c3a-111">Select **+ Create**.</span></span>
2. <span data-ttu-id="25c3a-112">프로세스를 따라 그룹 사이트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="25c3a-112">Follow the process to create a group site.</span></span>

<span data-ttu-id="25c3a-113">사이트 만들기 요청을 시작한 SharePoint 관리 센터에 해당하는 지리적 위치에서 그룹 사이트가 프로비저닝됩니다.</span><span class="sxs-lookup"><span data-stu-id="25c3a-113">Your group site will be provisioned in the geo location corresponding to the SharePoint admin center from which you initiated the site creation request.</span></span> 

<span data-ttu-id="25c3a-114">Exchange PowerShell 사용하기</span><span class="sxs-lookup"><span data-stu-id="25c3a-114">Using Exchange PowerShell</span></span> 

<span data-ttu-id="25c3a-115">Exchange Online PowerShell에 연결하고 *MailBoxRegion* 매개 변수를 지리적 위치 코드와 함께 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="25c3a-115">Connect to Exchange Online PowerShell and pass the parameter *-MailBoxRegion* with the geo location code.</span></span>

<span data-ttu-id="25c3a-116">예:</span><span class="sxs-lookup"><span data-stu-id="25c3a-116">For example:</span></span> 

```PowerShell
New-UnifiedGroup -DisplayName MultiGeoEUR -Alias "MultiGeoEUR" -AccessType Public -MailboxRegion EUR 
```

![구문을 사용하는 New-UnifiedGroup PowerShell cmdlet의 스크린 샷](media/multi-geo-new-group-with-pdl-powershell.png)

<span data-ttu-id="25c3a-118">SharePoint 그룹 사이트 프로비전은 주문형입니다.</span><span class="sxs-lookup"><span data-stu-id="25c3a-118">Note that SharePoint group site provisioning is on-demand.</span></span> <span data-ttu-id="25c3a-119">그룹 소유자 또는 구성원이 처음 액세스할 때 사이트가 프로비저닝됩니다.</span><span class="sxs-lookup"><span data-stu-id="25c3a-119">The site will be provisioned the first time a group owner or member attempts to access it.</span></span>

## <a name="geo-location-codes"></a><span data-ttu-id="25c3a-120">지리적 위치 코드</span><span class="sxs-lookup"><span data-stu-id="25c3a-120">Geo location codes</span></span>

[!INCLUDE [Office 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

## <a name="see-also"></a><span data-ttu-id="25c3a-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="25c3a-121">See also</span></span>

[<span data-ttu-id="25c3a-122">Exchange Online PowerShell에 연결</span><span class="sxs-lookup"><span data-stu-id="25c3a-122">Connect to Exchange Online PowerShell</span></span>](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)
