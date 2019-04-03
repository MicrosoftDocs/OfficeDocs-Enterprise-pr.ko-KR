---
title: 위성 지리적 위치에서 SharePoint Multi-Geo 사용
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: 위성 지리적 위치에서 SharePoint Multi-Geo 사용
ms.openlocfilehash: 98666f76a5b3ec055a6f26d30f502c3cc6b6d3bb
ms.sourcegitcommit: 0ddd9b0c9c23dc6479dce9f5701b69d533d76127
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/01/2019
ms.locfileid: "31025198"
---
# <a name="enabling-sharepoint-multi-geo-in-your-satellite-geo-location"></a>위성 지리적 위치에서 SharePoint Multi-Geo 사용

이 문서는 SharePoint Multi-Geo Capabilities가 2019년 3월 27일에 출시되기 **전**에 Multi-Geo 위성 위치를 만들고, 해당 위성 지리적 위치에서 SharePoint Multi-Geo를 사용하도록 설정하지 않은 전역 또는 SharePoint 관리자를 위해 작성되었습니다. 

>[!Note]
>**3월 27일** 이후에 새 지리적 위치를 추가한 경우, 새 지리적 위치가 이미 OneDrive 및 SharePoint Multi-Geo용으로 사용하도록 설정되어 있으므로 이 지침을 따라 작업을 수행할 필요가 없습니다.

이 지침을 따라 작업을 수행하면 위성 위치에서 SharePoint를 사용하도록 설정하여 Multi-Geo 위성 사용자가 O365에서 OneDrive와 SharePoint Multi-Geo Capabilities 모두를 활용할 수 있습니다. 

>[!IMPORTANT]
>이 방법은 한 방향 설정만 가능합니다. SPO 모드를 설정하면 지원이 포함된 권한 상승 없이 테넌트를 OneDrive 전용 Multi-Geo 모드로 되돌릴 수 없습니다. 

## <a name="to-set-a-geo-location-into-spo-mode"></a>지리적 위치를 SPO 모드로 설정

지리적 위치를 SPO 모드로 설정하려면 SPO 모드에서 설정하려는 지리적 위치에 연결하세요.

1.  SharePoint Online 관리 셸을 여세요. 
2.  Connect-SPOService -URL "https://$tenantGeo-admin.sharepoint.com" -Credential $credential
3.  Set-SPOMultiGeoExperience</br></br>
![Set-SPOMultiGeoExperience](media/Set-SPO-MultiGeo.jpg)
4.  서비스에서 다양한 게시 작업을 수행하고 테넌트를 다시 표시하는 동안 이 작업은 보통 1시간 정도 걸립니다. 최소 1시간이 지나면 Get-SPOMultiGeoExperience를 수행해 주세요.  이 작업을 수행하면 지리적 위치가 SPO 모드에 설정되었는지 여부가 표시됩니다.</br></br>
![Set-SPOMultiGeoExperience](media/Get-SPO-MultiGeo.jpg)

 
 
 
>[!Note]
>서비스의 특정 캐시를 24시간 마다 업데이트하면 최대 24시간의 기간 동안 위성 지리적 위치가 계속 ODB 모드에 있는 것처럼 간헐적으로 작동할 수 있습니다. 이 작업으로 인해 기술 문제가 발생하지 않습니다. 
 
SharePoint Multi-Geo에 관해 더 많은 정보를 확인하려면 [aka.ms/sharepointmultigeo](https://docs.microsoft.com/ko-KR/office365/enterprise/multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365)를 참조하세요.


