---
title: 특정 PDL을 사용 하 여 Microsoft 365 그룹 만들기
ms.reviewer: adwood
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
localization_priority: Normal
description: 다중 위치 환경에서 지정 된 기본 설정 데이터 위치를 사용 하 여 Microsoft 365 그룹을 만드는 방법을 알아봅니다.
ms.openlocfilehash: bcababe39035550be445f2eee4d8121a2983132f
ms.sourcegitcommit: aac21bb1a7c1dfc3ba76a2db883e0457037c5667
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/28/2020
ms.locfileid: "45433859"
---
# <a name="create-a-microsoft-365-group-with-a-specific-pdl"></a>특정 PDL을 사용 하 여 Microsoft 365 그룹 만들기

다중 위치 환경에서 사용자가 Microsoft 365 그룹을 만들면 그룹 기본 설정 데이터 위치가 자동으로 해당 사용자의로 설정 됩니다. 전역, SharePoint, Exchange 관리자는 선택하는 모든 영역에서 그룹을 만들 수 있습니다. 

특정 PDL로 그룹을 만들어야 할 경우 SharePoint 관리자 센터에서 만들거나 혹은 Exchange Online New-UnifiedGroup Microsoft PowerShell cmdlet을 사용하여 그룹을 만들 수 있습니다. 이 작업을 진행 시 그룹 사서함 및 그룹과 연결된 SharePoint 사이트가 지정된 PDL에서 프로비저닝됩니다.

지정한 PDL을 사용 하 여 Microsoft 365 그룹을 만들려면 그룹 사이트를 만들 지리적 위치에서 SharePoint 관리 센터로 이동 합니다.

예시:

호주의 위치에서 그룹 사이트를 만드려는 경우 https://ContosoAUS-admin.sharepoint.com/_layouts/15/online/AdminHome.aspx#/siteManagement로 이동할 수 있습니다.

1. **+ 만들기**를 선택합니다.
2. 프로세스를 따라 그룹 사이트를 만듭니다.

사이트 만들기 요청을 시작한 SharePoint 관리 센터에 해당하는 지리적 위치에서 그룹 사이트가 프로비저닝됩니다. 

Exchange PowerShell 사용하기 

Exchange Online PowerShell에 연결하고 *MailBoxRegion* 매개 변수를 지리적 위치 코드와 함께 전달합니다.

예: 

```PowerShell
New-UnifiedGroup -DisplayName MultiGeoEUR -Alias "MultiGeoEUR" -AccessType Public -MailboxRegion EUR 
```

![구문을 사용하는 New-UnifiedGroup PowerShell cmdlet의 스크린 샷](media/multi-geo-new-group-with-pdl-powershell.png)

SharePoint 그룹 사이트 프로비전은 주문형입니다. 그룹 소유자 또는 구성원이 처음 액세스할 때 사이트가 프로비저닝됩니다.

## <a name="geo-location-codes"></a>지리적 위치 코드

[!INCLUDE [Microsoft 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

## <a name="see-also"></a>참고 항목

[Exchange Online PowerShell에 연결](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)
