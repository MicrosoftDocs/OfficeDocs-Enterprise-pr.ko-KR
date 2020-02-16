---
title: SharePoint 사이트 콘텐츠를 지리적 위치로 제한
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
localization_priority: Priority
description: 다중 지역 환경에서 SharePoint 사이트를 특정한 지리적 위치로 제한하는 방법에 대해 알아봅니다.
ms.openlocfilehash: ca63f46ba45d1b3ddfdf4f676b678d62387b801f
ms.sourcegitcommit: 265cc03b600e9015a44c60c3f8bb9075b1c20888
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2020
ms.locfileid: "41973960"
---
# <a name="restrict-sharepoint-site-content-to-a-geo-location"></a>SharePoint 사이트 콘텐츠를 지리적 위치로 제한

상황에 따라 사이트가 이동되지 않도록 하거나 다른 지리적 위치에 있는 사이트의 파일 콘텐츠를 캐싱하지 못하게 하여 사이트가 만들어진 위치에 남아 있도록 사이트와 파일 콘텐츠를 적용할 수 있습니다.

[Set-SPOSite](https://docs.microsoft.com/powershell/module/sharepoint-online/set-sposite) cmdlet을 **RestrictedToGeo** 매개 변수와 함께 사용하여 이 작업을 할 수 있습니다. 이 매개 변수의 기본값은 NULL이지만 다음 중 하나로 변경할 수 있습니다.

|제한|설명|
|:----------|:----------|
|NoRestriction|사이트를 다른 지리적 위치로 이동할 수 있습니다.|
|BlockMoveOnly|사이트를 다른 지리적 위치로 이동할 수는 없지만 사이트 콘텐츠는 다른 지리적 위치에 캐시될 수 있습니다.|
|BlockFull|사이트를 다른 지리적 위치로 이동할 수 없으며 전체 파일 콘텐츠는 다른 지리적 위치에 캐시될 수 없습니다. 파일의 제목(콘텐츠에서 수집), 파일 이름 및 파일의 기타 속성은 다른 지리적 위치에 계속 캐시될 수 있습니다.<br>BlockFull로 구성되기 전에 사이트에 저장된 콘텐츠는 다른 지역의 위치에 계속 캐시될 수 있습니다.|

다음 구문을 사용합니다.

`Set-SPOSite -Identity <siteURL> -RestrictedToGeo <restriction>`

예를 들면 다음과 같습니다.

`Set-SPOSite -Identity https://contoso.sharepoint.com/sites/RegionRestrictedTeamSite -RestrictedToGeo BlockFull`
