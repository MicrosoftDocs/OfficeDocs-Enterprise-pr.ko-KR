---
title: SharePoint 사이트를 다른 지리적 위치로 이동
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.collection:
- Strat_SP_gtc
- SPO_Content
localization_priority: Priority
f1.keywords:
- NOCSH
description: SharePoint 사이트를 다른 지리적 위치로 이동하는 방법을 알아봅니다.
ms.openlocfilehash: 156c180841318aaee1c830ea3d9d665cbaeabe77
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843729"
---
# <a name="move-a-sharepoint-site-to-a-different-geo-location"></a>SharePoint 사이트를 다른 지리적 위치로 이동

SharePoint 사이트 지리적 이동으로 SharePoint 사이트를 Multi-Geo 환경 내에서 다른 지리적 위치로 이동할 수 있습니다.

다음과 같은 유형의 사이트를 지리적 위치 간에 이동할 수 있습니다.

- Office 365 그룹에 연결된 사이트
- Office 365 그룹과 연결되지 않은 최신 사이트
- 클래식 SharePoint 사이트
- 커뮤니케이션 사이트

지리적 위치 간에 사이트를 이동하려면 전역 관리자 또는 SharePoint 관리자여야 합니다.

사이트 콘텐츠에 따라 약 4~6시간이 걸리는 SharePoint 사이트 지리적 이동 기간에 읽기 전용 창이 있습니다.
 
## <a name="best-practices"></a>모범 사례

- 절차에 익숙해지려면 테스트 사이트에서 SharePoint 사이트 이동을 수행해 보세요. 
- 이동을 예약하거나 수행하기 전에 사이트를 이동할 수 있는지를 확인합니다. 
- 가능한 경우 사용자 영향을 줄이기 위해 업무 외 시간에 지역 간 사이트 이동을 예약합니다.
- 사이트를 이동하기 전에 영향을 받을 사용자에게 정보를 전달합니다. 

## <a name="communicating-to-your-users"></a>사용자에게 정보 전달

지리적 위치 간에 SharePoint 사이트를 이동할 때 사이트의 사용자(일반적으로 사이트를 편집할 수 있는 사용자)에게 앞으로 일어날 일에 대한 정보를 알려주는 것이 중요합니다. 그러면 사용자의 혼란을 막고 문의 전화를 줄일 수 있습니다. 이동하기 전에 사이트의 사용자에게 이메일로 다음 정보를 전달합니다.

- 이동 시작 시간 및 소요 시간
- 사이트가 이동할 지리적 위치 및 새 위치에 액세스하기 위한 URL
- 이동 중에는 파일을 닫고 편집하지 말아야 합니다.
- 이동해도 파일 권한 및 공유는 달라지지 않습니다.
- Multi-Geo 환경의 사용자 환경에서 예상할 점

이동이 완료되면 사이트의 사용자에게 이메일을 보내 이제 사이트에서 작업을 다시 시작할 수 있음을 알려야 합니다.

## <a name="scheduling-sharepoint-site-moves"></a>SharePoint 사이트 이동 예약

SharePoint 사이트 이동을 사전에 예약할 수 있습니다(이 문서의 뒷부분에서 설명). 이동 작업은 다음과 같이 예약할 수 있습니다.

- 한 번에 이동을 최대 4,000개 예약할 수 있습니다.
- 이동이 시작되면 큐와 주어진 시간에 보류 중인 이동 최대 4,000개를 추가로 예약할 수 있습니다.
 
SharePoint 사이트 지리적 이동 일정을 나중으로 예약하려면 이동하기 시작할 때 다음 매개 변수 중 하나를 포함합니다.
- `PreferredMoveBeginDate` - 이 지정 시간에 이동하기 시작할 가능성이 높습니다.
- `PreferredMoveEndDate` - 최선의 노력에 따라, 이 지정 시간에 이동을 완료할 가능성이 높습니다. 

두 매개 변수 모두 시간이 UTC(협정 세계시)로 지정되어야 합니다.

## <a name="moving-the-site"></a>사이트 이동

SharePoint 사이트 지리적 이동을 수행하려면 사이트가 있는 지리적 위치의 SharePoint 관리자 URL에서 연결 후 이동을 해야 합니다.

예를 들어 사이트 URL이 https://contosohealthcare.sharepoint.com/sites/Turbines인 경우, https://contosohealthcare-admin.sharepoint.com:에서 SharePoint 관리자 URL에 연결

`Connect-SPOService -url https://contosohealthcare-admin.sharepoint.com`

![](media/move-onedrive-between-geo-locations-image1.png)
 
### <a name="validating-the-environment"></a>환경 유효성 검사

사이트 이동을 예약하기 전에 먼저 유효성 검사를 수행하여 사이트를 이동할 수 있는지를 확인하는 것이 좋습니다.

다음을 사용한 사이트 이동은 지원하지 않습니다.
-   Business Connectivity Services
-   InfoPath 양식 

모든 지리적 위치가 호환되는지 확인하려면 `Get-SPOGeoMoveCrossCompatibilityStatus`를 실행합니다. 그러면 모든 지리적 위치가 표시되고 환경이 대상 지리적 위치와 호환되는지 표시됩니다.

사이트의 유효성만을 검사하려면 `Start-SPOSiteContentMove`와 `-ValidationOnly` 매개 변수를 사용하여 사이트를 이동할 수 있는지 여부를 확인합니다. 예:

```PowerShell
Start-SPOSiteContentMove -SourceSiteUrl <SourceSiteUrl> -ValidationOnly -DestinationDataLocation <DestinationLocation>
```

이 경우 사이트가 이동 가능한 상태면 *성공*을 반환하고, 차단된 조건이 하나라도 있으면 *실패*를 반환합니다.

### <a name="start-a-sharepoint-site-geo-move-for-a-site-with-no-associated-office-365-group"></a>Office 365 그룹에 연결되지 않은 사이트의 SharePoint 사이트 지리적 이동 시작

기본적으로 사이트의 초기 URL이 대상 지리적 위치의 URL로 변경됩니다. 예:

https://Contoso.sharepoint.com/sites/projectx에서 https://ContosoEUR.sharepoint.com/sites/projectx로

Office 365 그룹에 연결되지 않은 사이트의 경우에도 `-DestinationUrl` 매개 변수를 사용하여 이름을 변경할 수 있습니다. 예:

https://Contoso.sharepoint.com/sites/projectx에서 https://ContosoEUR.sharepoint.com/sites/projecty로

사이트 이동을 시작하려면 다음을 실행합니다.

`Start-SPOSiteContentMove -SourceSiteUrl <siteURL> -DestinationDataLocation <DestinationDataLocation> -DestinationUrl <DestinationSiteURL>`

![Start-SPOSiteContentMove cmdlet을 보여주는 PowerShell 창 스크린샷](media/multi-geo-sharepoint-site-move-powershell.png)

### <a name="start-a-sharepoint-site-geo-move-for-an-office-365-group-connected-site"></a>Office 365 그룹에 연결된 사이트의 SharePoint 사이트 지리적 이동 시작

Office 365 그룹에 연결된 사이트를 이동하려면 먼저 전역 관리자가 Office 365 그룹의 PDL(기본 데이터 위치) 특성을 변경해야 합니다.

Office 365 그룹의 PDL을 설정하려면:

```PowerShell
Set-SPOUnifiedGroup -PreferredDataLocation <PDL> -GroupAlias <GroupAlias>
Get-SPOUnifiedGroup -GroupAlias <GroupAlias>
```
PDL을 업데이트하고 나면 사이트 이동을 시작할 수 있습니다. 

```PowerShell
Start-SPOUnifiedGroupMove -GroupAlias <GroupAlias> -DestinationDataLocation <DestinationDataLocation>
```

## <a name="cancel-a-sharepoint-site-geo-move"></a>SharePoint 사이트 지리적 이동 취소

SharePoint 사이트 지리적 이동이 진행 중이거나 `Stop-SPOSiteContentMove` cmdlet을 통해 완료한 경우가 아니라면 이동을 중지할 수 있습니다.

## <a name="determining-the-status-of-a-sharepoint-site-geo-move"></a>SharePoint 사이트 지리적 이동의 상태 확인

다음 cmdlet을 사용하면, 연결된 지역 안팎으로 이동하는 사이트의 이동 상태를 확인할 수 있습니다.

- [Get-SPOSiteContentMoveState](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spositecontentmovestate)(그룹에 연결되지 않은 사이트)
- Get-SPOUnifiedGroupMoveState(그룹에 연결된 사이트)

`-SourceSiteUrl` 매개 변수를 사용하여 이동 상태를 볼 사이트를 지정합니다.

다음 표에는 이동 상태에 대한 설명이 나와 있습니다.

|상태|설명|
|:-----|:----------|
|트리거 준비 완료|이동이 시작되지 않았습니다.|
|예약됨|이동 작업이 큐에 있지만 아직 시작되지는 않았습니다.|
|InProgress(n/4)|이동이 유효성 검사(1/4), 백업(2/4), 복원(3/4), 정리(4/4)의 네 가지 상태 중 하나로 진행 중입니다.|
|Success|이동이 성공적으로 완료되었습니다.|
|Failed|이동이 실패했습니다.|

`-Verbose` 옵션을 적용하여 이동에 대한 추가 정보를 표시할 수도 있습니다.

## <a name="user-experience"></a>사용자 환경

사이트가 다른 지리적 위치로 이동해도 사이트 사용자는 영향을 별로 느끼지 못할 것입니다. 이동 중에 발생하는 일시적인 읽기 전용 상태를 제외하면, 이동 후에도 기존 링크와 권한은 예상대로 계속 작동합니다.

### <a name="site"></a>사이트

이동이 진행 중일 때 사이트는 읽기 전용으로 설정됩니다. 이동이 완료된 후, 책갈피를 클릭하거나 사이트로 연결하는 다른 링크를 클릭하면 사용자가 새 지리적 위치의 새 사이트로 리디렉션됩니다.

### <a name="permissions"></a>권한

이동하는 동안 그리고 완료된 후, 사이트에 대한 권한이 있는 사용자는 해당 사이트에 계속 액세스할 수 있습니다.

### <a name="sync-client"></a>동기화 클라이언트

사이트 이동이 완료되고 나면 동기화 클라이언트가 자동 검색 후 원활하게 새 사이트 위치와의 동기화를 전송합니다. 사용자가 다시 로그인하거나 다른 조치를 취할 필요가 없습니다. 동기화 클라이언트 버전 17.3.6943.0625 이상이 필요합니다.

이동이 진행되는 동안 사용자가 파일을 업데이트하는 경우 동기화 클라이언트는 이동이 진행되는 동안에는 파일 업로드가 보류된다는 사실을 알려줍니다.

### <a name="sharing-links"></a>링크 공유

SharePoint 사이트 지리적 이동이 완료되면, 이동한 파일의 기존 공유 링크가 새로운 지리적 위치로 자동으로 리디렉션됩니다.

### <a name="most-recently-used-files-in-office-mru"></a>Office에서 MRU(최근에 사용한) 파일

이동이 완료되면 MRU 서비스의 사이트 URL과 해당 콘텐츠 URL이 업데이트됩니다. 이는 Word, Excel, PowerPoint에 적용됩니다.

### <a name="onenote-experience"></a>OneNote 환경

사이트 이동이 완료되고 나면 OneNote Win32 클라이언트와 UWP(유니버설) 앱이 자동 검색 후 전자 필기장을 원활하게 새 사이트 위치에 동기화합니다. 사용자가 다시 로그인하거나 다른 조치를 취할 필요가 없습니다. 사이트 이동이 진행 중일 때 사용자에게 보이는 유일한 표시는 전자 필기장 동기화 실패 표시입니다. 이 환경은 다음 OneNote 클라이언트 버전에서 사용할 수 있습니다.

- OneNote win32 - 버전 16.0.8326.2096 이상
- OneNote UWP - 버전 16.0.8431.1006 이상
- OneNote 모바일 앱 - 버전 16.0.8431.1011 이상

### <a name="teams-applicable-to-office-365-group-connected-sites"></a>Teams(Office 365 그룹에 연결된 사이트에 적용 가능)

SharePoint 사이트 지리적 이동이 완료되면 사용자가 Teams 앱의 Office 365 그룹 사이트 파일에 액세스할 수 있습니다. 또한 지리적 이동 이전에 사이트의 Teams 채팅을 통해 공유한 파일은 이동이 완료되 후 계속해서 사용 가능합니다.

### <a name="sharepoint-mobile-app-iosandroid"></a>SharePoint 모바일 앱(iOS/Android)

SharePoint Mobile 앱은 지역 간에 호환되며 사이트의 새 지리적 위치를 검색할 수 있습니다.

### <a name="sharepoint-workflows"></a>SharePoint 워크플로

사이트가 이동하고 나면 SharePoint 2013 워크플로를 다시 게시해야 합니다. SharePoint 2010 워크플로는 계속해서 정상적으로 작동합니다.

### <a name="apps"></a>앱

앱이 포함된 사이트를 이동하는 경우, 대상 지리적 위치에서 앱과 연결을 사용하지 못할 수 있으므로 사이트의 새 지리적 위치에서 앱을 다시 인스턴스화해야 합니다.

### <a name="flow"></a>흐름

대부분의 경우 SharePoint 사이트 지리적 이동 후에도 흐름이 계속해서 정상적으로 작동합니다. 이동이 완료되면 한 번 테스트하는 것이 좋습니다.

### <a name="powerapps"></a>PowerApps

대상 위치에 PowerApps를 다시 만들어야 합니다.

### <a name="data-movement-between-geo-locations"></a>지리적 위치 간 데이터 이동

SharePoint는 콘텐츠를 Azure Blob Storage에 저장하고, 사이트 및 파일과 연결된 메타데이터는 SharePoint 내에 저장합니다. 사이트가 원본 지리적 위치에서 대상 지리적 위치로 이동하고 나면, 서비스도 그와 연결된 Blob Storage를 이동합니다. Blob Storage 이동은 약 40일 후에 완료됩니다. 
