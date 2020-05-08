---
title: OneDrive 사이트를 다른 지리적 위치로 이동
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
ms.collection:
- Strat_SP_gtc
- SPO_Content
localization_priority: Priority
description: OneDrive 사이트를 다른 지리적 위치로 이동하는 방법을 알아봅니다.
ms.openlocfilehash: ce631cc8f922fd9f64586bb41e6dd1ec64ac1141
ms.sourcegitcommit: 012bf4d8ad132435f9baeffd6f7e5ed264a8bfe0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/06/2020
ms.locfileid: "44058008"
---
# <a name="move-a-onedrive-site-to-a-different-geo-location"></a>OneDrive 사이트를 다른 지리적 위치로 이동 

OneDrive 지리적 이동을 사용하면 사용자의 OneDrive를 다른 지리적 위치로 이동할 수 있습니다. OneDrive 지리적 이동은 SharePoint Online 관리자 또는 Microsoft 365 전역 관리자가 수행합니다. OneDrive 지리적 이동을 시작하기 전에 OneDrive을 이동할 사용자에게 알리고 이동하는 동안 모든 파일을 닫도록 권유합니다. (이동하는 동안 Office 클라이언트를 사용하여 문서를 열어 둔 경우 이동이 완료된 후에 문서를 새 위치에 저장해야 합니다.) 원할 경우 나중에 이동하도록 예약할 수 있습니다.

OneDrive 서비스는 Azure Blob 저장소를 사용하여 콘텐츠를 저장합니다. 사용자의 OneDrive와 연결된 Storage Blob는 대상 OneDrive를 사용할 수 있게 되고 40일 이내에 원본에서 대상 지리적 위치로 이동됩니다. 사용자의 OneDrive에 대한 액세스 권한은 대상 OneDrive가 사용할 수 있게 되는 즉시 복원됩니다.

OneDrive 지리적 이동 기간(약 2 ~ 6시간) 동안 사용자의 OneDrive는 읽기 전용으로 설정됩니다. 사용자는 OneDrive 동기화 클라이언트 또는 SharePoint Online의 OneDrive 사이트를 통해 해당 파일에 계속 액세스할 수 있습니다. OneDrive 지리적 이동이 완료되면 사용자는 Microsoft 365 앱 시작 관리자에서 OneDrive로 이동할 때 대상 지리적 위치에 자동으로 연결됩니다. 동기화 클라이언트는 자동으로 새 위치에서 동기화를 시작합니다.

이 문서에 나오는 절차를 수행하려면 [Microsoft SharePoint Online PowerShell 모듈](https://www.microsoft.com/download/details.aspx?id=35588)이 필요합니다.

## <a name="communicating-to-your-users"></a>사용자에게 정보 전달

지리적 위치 간에 OneDrive 사이트를 이동할 때는 예상되는 상황을 사용자에게 알리는 것이 중요합니다. 이를 통해 사용자 혼란과 지원 센터 문의 전화를 줄일 수 있습니다. 이동하기 전에 사용자에게 전자 메일로 다음 정보를 알릴 수 있습니다.

- 예상되는 이동 시작 시기 및 소요 기간
- OneDrive가 이동될 지리적 위치와 새 위치에 액세스하기 위한 URL
- 이동 중에는 해당 파일을 닫고, 편집하지 않아야 합니다.
- 파일 권한 및 공유는 이동 후에 달라지지 않습니다.
- [다중 위치 환경에서 예상되는 사용자 작업 환경](multi-geo-user-experience.md)

이동이 성공적으로 완료되면 OneDrive 작업을 다시 시작할 수 있음을 알리는 전자 메일을 사용자에게 전송해야 합니다.

## <a name="scheduling-onedrive-site-moves"></a>OneDrive 사이트 이동 예약

OneDrive 사이트 이동을 사전에 예약할 수 있습니다(이 문서의 뒷부분에서 설명). 적은 수의 사용자로 시작하여 워크플로 및 통신 전략의 유효성을 검사하는 것이 좋습니다. 프로세스에 익숙해지면 다음과 같이 이동을 예약할 수 있습니다.

- 한 번에 이동을 최대 4,000개 예약할 수 있습니다.
- 이동이 시작되면 큐와 주어진 시간에 보류 중인 이동 최대 4,000개를 추가로 예약할 수 있습니다.
- 이동할 수 있는 OneDrive의 최대 크기는 1 테라바이트(1 TB)입니다.

## <a name="moving-a-onedrive-site"></a>OneDrive 사이트 이동

OneDrive 지리적 이동을 수행하려면 테넌트 관리자는 먼저 사용자의 PDL(기본 설정 데이터 위치)을 해당 지리적 위치로 설정해야 합니다. PDL이 설정되면 OneDrive 지리적 이동을 시작하기 전에 PDL 업데이트가 지리적 위치 간에 동기화될 때까지 24시간 이상 기다립니다.

지리적 이동 cmdlet을 사용할 경우 다음 구문을 사용하여 사용자의 현재 OneDrive 지리적 위치에 있는 SPO 서비스에 연결합니다.

`Connect-SPOService -url https://<tenantName>-admin.sharepoint.com`

예를 들어, 'Matt@contosoenergy.onmicrosoft.com' 사용자의 OneDrive를 이동하려면 이 사용자의 OneDrive는 EUR 지리적 위치에 있으므로 EUR SharePoint 관리 센터에 연결합니다.

`Connect-SPOSservice -url https://contosoenergyeur-admin.sharepoint.com`

![connect-sposervice cmdlet이 표시된 PowerShell 창의 스크린샷](media/move-onedrive-between-geo-locations-image1.png)

## <a name="validating-the-environment"></a>환경 유효성 검사

OneDrive 지리적 이동을 시작하기 전에 환경이 유효한지 검사하는 것이 좋습니다.

모든 지리적 위치가 호환되는지 확인하려면 다음을 실행합니다.

`Get-SPOGeoMoveCrossCompatibilityStatus`

지리적 위치 목록을 확인할 수 있고, 지리적 위치 사이에서 콘텐츠가 이동할 수 있는지 여부는 “호환”으로 표시됩니다. 명령에서 “호환되지 않음”을 반환하는 경우 나중에 상태 유효성 검사를 다시 시도하세요.

예를 들어 OneDrive에 하위 사이트가 들어 있으면 이를 이동할 수 없습니다. ValidationOnly 매개 변수와 함께 Start-SPOUserAndContentMove cmdlet을 사용하여 OneDrive를 이동할 수 있는지 확인할 수 있습니다.

`Start-SPOUserAndContentMove -UserPrincipalName <UPN> -DestinationDataLocation <DestinationDataLocation> -ValidationOnly`

OneDrive를 이동할 준비가 되었으면 Success, 법적 보존 상태이거나 하위 사이트가 포함되어 있어서 이동할 수 없으면 Fail이 반환됩니다. OneDrive를 이동할 준비가 되어 있는지 확인한 후에는 이동을 시작할 수 있습니다.

## <a name="start-a-onedrive-geo-move"></a>OneDrive 지리적 이동 시작

이동을 시작하려면 다음을 실행합니다.  

`Start-SPOUserAndContentMove -UserPrincipalName <UserPrincipalName> -DestinationDataLocation <DestinationDataLocation>`

다음 매개 변수를 사용합니다.

-   _UserPrincipalName_ - OneDrive을 이동할 사용자의 UPN입니다.

-   _DestinationDataLocation_ - OneDrive를 이동해야 하는 지리적 위치입니다. 사용자의 기본 설정 데이터 위치와 동일해야 합니다.

예를 들어, matt@contosoenergy.onmicrosoft.com의 OneDrive를 EUR에서 AUS로 이동하려면 다음을 실행합니다.

`Start-SPOUserAndContentMove -UserPrincipalName matt@contosoenergy.onmicrosoft.com -DestinationDataLocation AUS`

![Start-SPOUserAndContentMove cmdlet을 보여주는 PowerShell 창 스크린샷](media/move-onedrive-between-geo-locations-image2.png)

지리적 이동을 나중을 수행하기 위해 예약하려면 다음 매개 변수 중 하나를 사용합니다.

-   _PreferredMoveBeginDate_ – 이 지정된 시간에 이동이 시작되게 됩니다. 시간은 UTC(협정 세계시)로 지정해야 합니다.

-   _PreferredMoveEndDate_ – 이 지정된 시간에 최상의 노력 방식으로 이동이 완료되게 됩니다. 시간은 UTC(협정 세계시)로 지정해야 합니다. 

## <a name="cancel-a-onedrive-geo-move"></a>OneDrive 지리적 이동 취소 

사용자 OneDrive의 지리적 이동이 진행 중이거나 cmdlet을 통해 완료된 경우가 아니면 이동을 중지할 수 있습니다.

`Stop-SPOUserAndContentMove – UserPrincipalName <UserPrincipalName>`

여기서 _UserPrincipalName_은 OneDrive 이동을 중지하려는 사용자의 UPN입니다.

## <a name="determining-current-status"></a>현재 상태 확인

Get-SPOUserAndContentMoveState cmdlet을 사용하여 연결된 지리적 위치로 들어오거나 해당 위치에서 나가는 OneDrive 지리적 이동의 상태를 확인할 수 있습니다.

다음 표에는 이동 상태에 대한 설명이 나와 있습니다.

<table>
<thead>
<tr class="header">
<th align="left"><strong>상태</strong></th>
<th align="left"><strong>설명</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">NotStarted</td>
<td align="left">이동이 시작되지 않았습니다.</td>
</tr>
<tr class="even">
<td align="left">InProgress(<em>n</em>/4)</td>
<td align="left">이동이 유효성 검사(1/4), 백업(2/4), 복원(3/4), 정리(4/4)의 네 가지 상태 중 하나로 진행 중입니다.</td>
</tr>
<tr class="odd">
<td align="left">Success</td>
<td align="left">이동이 성공적으로 완료되었습니다.</td>
</tr>
<tr class="even">
<td align="left">Failed</td>
<td align="left">이동이 실패했습니다.</td>
</tr>
</tbody>
</table>

특정 사용자 이동의 상태를 확인하려면 UserPrincipalName 매개 변수를 사용합니다.

`Get-SPOUserAndContentMoveState -UserPrincipalName <UPN>`

연결된 지리적 위치로 들어오거나 해당 위치에서 나가는 모든 이동의 상태를 확인하려면 NotStarted, InProgress, Success, Failed, All 값 중 하나를 갖는 MoveState 매개 변수를 사용합니다.

`Get-SPOUserAndContentMoveState -MoveState <value>`

이동 상태에 대한 좀 더 자세한 설명을 보려면 `-Verbose` 매개 변수를 추가할 수도 있습니다.

## <a name="user-experience"></a>사용자 환경

OneDrive 사용자는 OneDrive가 다른 지리적 위치로 이동될 경우 최소한의 작업 중단이 발생한다는 것을 알 수 있습니다. 이동하는 동안 잠깐 읽기 전용 상태가 되지만 이동이 완료되면 링크 및 사용 권한은 예상대로 계속 작동합니다.

### <a name="onedrive-for-business"></a>비즈니스용 OneDrive

이동이 진행되는 동안 사용자의 OneDrive는 읽기 전용으로 설정됩니다. 이동이 완료된 후 Microsoft 365 앱 시작 관리자 또는 웹 브라우저에서 OneDrive로 가면 새 지리적 위치의 OneDrive로 이동됩니다.

### <a name="permissions-on-onedrive-content"></a>OneDrive 콘텐츠에 대한 사용 권한

이동하는 동안 및 완료된 후, OneDrive 콘텐츠에 대해 사용 권한이 있는 사용자는 해당 콘텐츠에 계속 액세스할 수 있습니다.

### <a name="onedrive-sync-client"></a>OneDrive 동기화 클라이언트 

OneDrive 동기화 클라이언트는 OneDrive 지리적 이동이 완료되면 새 OneDrive 위치를 자동으로 감지하고, 해당 위치에 대한 동기화로 원활하게 전환합니다. 따라서 사용자가 다시 로그인하거나 다른 작업을 수행할 필요가 없습니다. (동기화 클라이언트 버전 17.3.6943.0625 이상이 필요합니다.)

OneDrive 지리적 이동이 진행되는 동안 사용자가 파일을 업데이트하는 경우 동기화 클라이언트는 이동이 진행 중일 때 파일 업로드가 보류된다는 사실을 알립니다.

### <a name="sharing-links"></a>링크 공유 

OneDrive 지리적 이동이 완료되면, 이동된 파일에 대한 기본 공유 링크가 새 위치로 자동으로 리디렉션됩니다.

### <a name="onenote-experience"></a>OneNote 환경 

OneNote win32 클라이언트 및 UWP(유니버설) 앱은 OneDrive 지리적 이동이 완료되면 새 OneDrive 위치를 자동으로 감지하고 전자 필기장을 원활하게 동기화합니다. 따라서 사용자가 다시 로그인하거나 다른 작업을 수행할 필요가 없습니다. 사용자에게 OneDrive 지리적 이동이 진행 중일 때 전자 필기장 동기화가 실패한다는 알림만 표ㅕ시됩니다. 이러한 환경은 다음 OneNote 클라이언트 버전에서 사용할 수 있습니다.

-   OneNote win32 - 버전 16.0.8326.2096 이상

-   OneNote UWP - 버전 16.0.8431.1006 이상

-   OneNote 모바일 앱 - 버전 16.0.8431.1011 이상

### <a name="teams-app"></a>Teams 앱

OneDrive 지리적 이동이 완료되면, Teams 앱의 해당 OneDrive 파일에 액세스할 수 있게 됩니다. 또한 지리적 이동 적에 해당 OneDrive에서 Teams 앱을 통해 공유한 파일은 이동이 완료된 후에도 계속 작동합니다.

### <a name="onedrive-for-business-mobile-app-ios"></a>비즈니스용 OneDrive 모바일 앱(iOS) 

OneDrive 지리적 이동이 완료되면, 사용자는 iOS 모바일 앱에서 로그아웃했다가 다시 로그인하여 새 OneDrive 위치와 동기화해야 합니다.

### <a name="existing-followed-groups-and-sites"></a>기존의 팔로우된 그룹 및 사이트

팔로우된 사이트 및 그룹은 해당 지리적 위치에 관계없이 사용자의 비즈니스용 OneDrive에 표시됩니다. 다른 지리적 위치에서 호스트된 사이트 및 그룹은 별도 탭에서 열립니다.
