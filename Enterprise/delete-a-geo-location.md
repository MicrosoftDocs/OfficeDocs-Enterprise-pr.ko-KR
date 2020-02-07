---
title: 위성 위치 삭제
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
description: Office 365 Multi-Geo에서 위성 위치를 삭제하는 방법을 알아봅니다.
ms.openlocfilehash: 8f6f52a42cef1aee88b590115bf54ba4e2179830
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41840555"
---
# <a name="delete-a-satellite-location-in-office-365-multi-geo"></a><span data-ttu-id="986c4-103">Office 365 Multi-Geo에서 위성 위치를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="986c4-103">Delete a satellite location in Office 365 Multi-Geo</span></span>

<span data-ttu-id="986c4-104">위성 위치가 더 이상 필요하지 않으면 SharePoint 관리 센터를 사용하여 테넌트에서 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="986c4-104">If you no longer need a satellite location, you can delete it from your tenant from the SharePoint admin center.</span></span>

> [!WARNING]
> <span data-ttu-id="986c4-105">위성 위치의 모든 사용자 데이터가 영구적으로 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="986c4-105">All user data in the satellite location will be permanently deleted.</span></span> <span data-ttu-id="986c4-106">여기에는 OneDrive for Business의 모든 콘텐츠, SharePoint 사이트 및 Office 365 그룹 사서함을 포함한 Exchange 사서함이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="986c4-106">This includes all OneDrive for Business content, SharePoint sites and Exchange mailboxes including Office 365 Group mailboxes.</span></span> <span data-ttu-id="986c4-107">위성 위치를 삭제하기 전에 데이터를 다른 위성 위치 또는 중앙 위치로 마이그레이션 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="986c4-107">You must migrate any data to another satellite location or the central location before you delete the satellite location.</span></span> <span data-ttu-id="986c4-108">이 작업은 취소할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="986c4-108">This action cannot be undone.</span></span>

<span data-ttu-id="986c4-109">전역 관리자만 위성 위치를 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="986c4-109">Only global administrators can delete satellite locations.</span></span>

![지리적 위치 삭제 UI가 표시된 다중 지역 관리 센터의 스크린샷](media/multi-geo-delete-satellite-location.png)

<span data-ttu-id="986c4-111">위성 위치를 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="986c4-111">To delete a satellite location</span></span>

1. <span data-ttu-id="986c4-112">SharePoint 관리 센터를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="986c4-112">Open the SharePoint admin center</span></span>

2. <span data-ttu-id="986c4-113">**지리적 위치** 탭으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="986c4-113">Navigate to the **Geo locations** tab.</span></span>

3. <span data-ttu-id="986c4-114">지도에서 삭제하려는 지리적 위치를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="986c4-114">On the map, click the geo location that you want to delete.</span></span>

4. <span data-ttu-id="986c4-115">**위치 삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="986c4-115">Click **Delete location**.</span></span>

5. <span data-ttu-id="986c4-116">확인 확인란을 선택하여 삭제를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="986c4-116">Confirm the deletion by selecting the confirmation check boxes.</span></span>

6. <span data-ttu-id="986c4-117">**삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="986c4-117">Click **Delete**.</span></span>
