---
title: 특정 PDL로 Office 365 그룹 만들기
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Multi-Geo 환경에서 지정된 기본 설정 데이터 위치를 사용하여 Office 365 그룹을 만드는 방법에 대해 알아봅니다.
ms.openlocfilehash: fb512478d69502eafd633b552d1db2acbec43ef4
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070004"
---
# <a name="create-an-office-365-group-with-a-specific-pdl"></a><span data-ttu-id="46c26-103">특정 PDL로 Office 365 그룹 만들기</span><span class="sxs-lookup"><span data-stu-id="46c26-103">Create an Office 365 Group with a specific PDL</span></span>

<span data-ttu-id="46c26-104">Multi-Gep 환경의 사용자가 Office 365 그룹을 만들 때 그룹 기본 설정 데이터 위치가 자동으로 사용자의 위치로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="46c26-104">When users in a multi-geo environment create an Office 365 Group, the group preferred data location is automatically set to that of the user.</span></span> <span data-ttu-id="46c26-105">특정 PDL로 그룹을 만들어야 할 경우 Exchange Online New-UnifiedGroup Microsoft PowerShell cmdlet을 사용하여 그룹을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46c26-105">If you need to create a group with a specific PDL, you can do that using the Exchange Online New-UnifiedGroup Microsoft PowerShell cmdlet.</span></span> <span data-ttu-id="46c26-106">이렇게하면 그룹 사서함 및 그룹과 연결된 SharePoint 사이트가 지정된 PDL로 프로비저닝됩니다.</span><span class="sxs-lookup"><span data-stu-id="46c26-106">When you do this, both the group mailbox and SharePoint site associated with the group will be provisioned in the specified PDL.</span></span>

<span data-ttu-id="46c26-107">이 작업을 수행하려면 전역 관리자 또는 SharePoint Online 또는 Exchange Online 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="46c26-107">You must be a global administrator or a SharePoint Online or Exchange Online administrator to do this.</span></span>

<span data-ttu-id="46c26-108">지정한 PDL로 Office 365 그룹을 만들려면 Exchange Online PowerShell에 연결하고 *-MailBoxRegion* 매개 변수를 지리적 위치 코드와 함께 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="46c26-108">To create an Office 365 Group with the PDL that you specify, connect to Exchange Online PowerShell and pass the parameter *-MailBoxRegion* with the geo location code.</span></span>

<span data-ttu-id="46c26-109">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="46c26-109">For example:</span></span> 

```PowerShell
New-UnifiedGroup -DisplayName MultiGeoEUR -Alias "MultiGeoEUR" -AccessType Public -MailboxRegion EUR 
```

![구문을 사용하는 New-UnifiedGroup PowerShell cmdlet의 스크린 샷](media/multi-geo-new-group-with-pdl-powershell.png)

<span data-ttu-id="46c26-111">SharePoint 그룹 사이트 프로비전은 주문형입니다.</span><span class="sxs-lookup"><span data-stu-id="46c26-111">Note that SharePoint group site provisioning is on-demand.</span></span> <span data-ttu-id="46c26-112">그룹 소유자 또는 구성원이 처음 액세스할 때 사이트가 프로비저닝됩니다.</span><span class="sxs-lookup"><span data-stu-id="46c26-112">The site will be provisioned the first time a group owner or member attempts to access it.</span></span>

## <a name="geo-location-codes"></a><span data-ttu-id="46c26-113">지리적 위치 코드</span><span class="sxs-lookup"><span data-stu-id="46c26-113">Geo location codes</span></span>

[!INCLUDE [Office 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

## <a name="see-also"></a><span data-ttu-id="46c26-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="46c26-114">See also</span></span>

[<span data-ttu-id="46c26-115">Exchange Online PowerShell에 연결</span><span class="sxs-lookup"><span data-stu-id="46c26-115">Connect to Exchange Online PowerShell</span></span>](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)