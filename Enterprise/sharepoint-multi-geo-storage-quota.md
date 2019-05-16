---
title: 다중 지역 환경에서 SharePoint 저장소 할당량
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: 다중 지역 환경에서 SharePoint 저장소 할당량에 대해 알아봅니다.
ms.openlocfilehash: a9ccc32940293dcd11e2f3b89607950f7b6ae3f0
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070754"
---
# <a name="sharepoint-storage-quotas-in-multi-geo-environments"></a>다중 지역 환경에서 SharePoint 저장소 할당량

기본적으로 다중 지역 환경의 모든 지리적 위치는 사용 가능한 테넌트 저장소 할당량을 공유합니다.

SharePoint 지역 저장소 할당량 설정을 사용하면 각 위치별로 저장소 할당량을 관리할 수 있습니다. 지리적 위치에 대한 저장소 할당량을 할당하면 해당 지리적 위치에서 사용할 수 있는 최대 저장 용량이 되며 사용 가능한 테넌트 저장 할당량에서 공제됩니다. 나머지 사용 가능한 테넌트 스토리지 할당량은 특정 스토리지 할당량이 할당되지 않은 구성된 지리적 위치에서 공유됩니다.

지리적 위치에 대한 SharePoint 저장소 할당량은 중앙 위치에 연결하여 SharePoint Online 관리자가 할당할 수 있습니다. 위성 위치에 대한 지역 관리자는 저장소 할당량을 볼 수는 있지만 할당할 수는 없습니다.

## <a name="configure-a-storage-quota-for-a-geo-location"></a>지리적 위치에 대한 저장소 할당량 구성

[Microsoft SharePoint Online 모듈](https://www.microsoft.com/en-us/download/details.aspx?id=35588 )을 사용하고 중앙 위치에 연결하여 지리적 위치에 대한 저장소 할당량을 할당합니다. 

한 위치에 저장소 할당량을 할당하려면 cmdlet을 실행합니다.

`Set-SPOGeoStorageQuota -GeoLocation <geolocationcode> -StorageQuotaMB <value>`

현재 지리적 위치에 대한 저장소 할당량을 보려면 다음을 실행하세요.

`Get-SPOGeoStorageQuota`

![Get-SPOGeoStorageQuota cmdlet이 표시된 PowerShell 창의 스크린 샷](media/multi-geo-storage-quota.png)

모든 지리적 위치에 대한 저장소 할당량을 보려면 다음을 실행하세요.

`Get-SPOGeoStorageQuota -AllLocations`

지리적 위치에 할당된 저장소 할당량을 제거하려면 다음을 설정하세요. `StorageQuota value = 0`

`Set-SPOGeoStorageQuota -GeoLocation <geolocationcode> -StorageQuotaMB 0`
