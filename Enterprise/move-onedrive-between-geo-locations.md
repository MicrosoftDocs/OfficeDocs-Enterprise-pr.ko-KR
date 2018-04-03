---
title: OneDrive 사이트를 다른 지리적 위치를 이동
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: OneDrive 사이트를 다른 지리적 위치로 이동 하는 방법에 알아봅니다.
ms.openlocfilehash: a31f683170fdb83dac90e9d09884c3020d1a47b1
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/03/2018
---
# <a name="move-a-onedrive-site-to-a-different-geo-location"></a>OneDrive 사이트를 다른 지리적 위치를 이동 

지리적으로 분산 이동, OneDrive와 사용자의 OneDrive 다른 지리적 위치를 이동할 수 있습니다. OneDrive 지리적으로 분산 이동 Office 365 전역 관리자 또는 SharePoint Online 관리자가 수행 됩니다. 지리적으로 분산 이동 OneDrive를 시작 하기 전에 해야 해당 OneDrive를 이동 하는 사용자에 게 알리고 이동의 기간에 대 한 파일을 모두 닫고 자신이 하는 것이 좋습니다. (사용자에 게 하는 경우에 따라 다음 이동 하는 동안 Office 클라이언트를 사용 하 여 문서를 연 이동 완료 문서의 새 위치에 저장 해야 합니다.) 원하는 경우에 나중에 대 한 이동을 예약할 수 있습니다.

Azure Blob 저장소를 사용 하 여 콘텐츠를 저장 하는 OneDrive 서비스입니다. 사용자의 OneDrive와 연결 된 저장소 blob 이동할 원본에서 대상 지리적 위치에 대상 사용자에 게 제공 되는 OneDrive의 40 일 이내입니다. 대상 OneDrive를 사용할 수는 즉시 사용자의 OneDrive에 대 한 액세스를 복원 됩니다.

OneDrive 지리적으로 분산 이동 창 (약 2-6 시간) 하는 동안 사용자의 OneDrive 설정은 읽기 전용으로 설정 합니다. 사용자는 OneDrive 동기화 클라이언트 또는 SharePoint Online에서 자신의 OneDrive 사이트를 통해 해당 파일에 계속 액세스할 수 있습니다. OneDrive 지리적으로 분산 이동을 완료 되 면 사용자가 자동으로 연결할 수 대상 지리적 위치에 자신의 OneDrive Office 365 응용 프로그램 시작 관리자의 OneDrive을 탐색할 때. 동기화 클라이언트는 새 위치에서 동기화 하는 중에 자동으로 시작 됩니다.

이 문서의 절차에는 [Microsoft SharePoint Online PowerShell 모듈](https://www.microsoft.com/en-us/download/details.aspx?id=35588)필요 합니다.

## <a name="moving-a-onedrive-site"></a>OneDrive 사이트를 이동합니다.

지리적으로 분산 이동, 프로그램 OneDrive를 수행 하려면 적절 한 지리적 위치로 테 넌 트 관리자가 사용자의 기본 설정 데이터 위치 (PDL)를 먼저 설정 해야 합니다. PDL가 설정 되 면 OneDrive 지리적으로 분산 이동을 시작 하기 전에 여러 지리적 위치에 걸친 동기화 할 PDL 업데이트에 대 한 최소 24 시간까지 기다립니다.

지리적으로 분산을 사용 하 여 cmdlet를 이동 하는 경우 다음 구문을 사용 하 여 사용자의 현재 OneDrive 지리적 위치에 SPO 서비스에 연결 합니다.

`connect-sposervice -url https://<tenantName>-admin.sharepoint.com`

예: 'Matt@contosoenergy.onmicrosoft.com' 사용자의 OneDrive를 이동 하려면 연결 EUR SharePoint 관리 센터에는 사용자의 OneDrive EUR 지리적 위치에 있는 그대로:

`connect-sposervice -url https://contosoenergyeur-admin.sharepoint.com`

![](media/move-onedrive-between-geo-locations_image1.png)

## <a name="validating-the-environment"></a>유효성을 검사 하는 환경

시작 하기 전에 OneDrive geo 이동, 환경 유효성을 검사 하는 것이 좋습니다.

모든 지리적 위치 호환 되는지 확인, 다음을 실행 합니다.

`Get-SPOGeoMoveCompatibilityStatus -AllLocations 1`

법적 보유에서 사용 되는 OneDrive 또는 하위 사이트를 포함 하는 경우에 이동할 수 없습니다. OneDrive가 이동 될 수의 유효성을 검사 하는-ValidationOnly 매개 변수와 함께 시작 SPOUserAndContentMove cmdlet을 사용할 수 있습니다.

`Start-SPOUserAndContentMove -UserPrincipalName <UPN> -DestinationDataLocation <DestinationDataLocation> -ValidationOnly`

OneDrive은 이동 또는 법적 보존 또는 하위 사이트 이동 하는 것을 방지할 수 있는 경우 실패를 준비 하는 경우 성공이 반환 됩니다. OneDrive 이동 하려면를 수행할 준비가 되었는지 확인 한 후에 이동을 시작할 수 있습니다.

## <a name="start-a-onedrive-geo-move"></a>OneDrive 지리적으로 분산 이동 시작

이동을 시작 하려면 다음을 실행 합니다.  

`Start-SPOUserAndContentMove -UserPrincipalName <UserPrincipalName> -DestinationDataLocation <DestinationDataLocation>`

이러한 매개 변수를 사용 합니다.

-   _UserPrincipalName_ – 해당 OneDrive를 이동 하는 사용자의 UPN 합니다.

-   _DestinationDataLocation_ – 지리적 위치 OneDrive 위치 이동 해야 합니다. 이 사용자의 기본 데이터 위치와 동일 해야 합니다.

> [!NOTE]
> 실행 하는 것이 좋습니다 `Get-SPOGeoMoveStateCompatibility` 와 `ValidationOnly` OneDrive를 시작 하기 전에 지리적으로 분산 이동 합니다.

예, matt@contosoenergy.onmicrosoft.com의 OneDrive EUR에서 오스트레일리아를 이동 하려면 다음을 실행 합니다.

`Start-SPOUserAndContentMove -UserPrincipalName matt@contosoenergy.onmicrosoft.com -DestinationDataLocation AUS`

![](media/move-onedrive-between-geo-locations_image2.png)

나중에 대 한 지리적으로 분산 이동을 예약 하려면 다음 매개 변수 중 하나를 사용 합니다.

-   이 지정 된 시간에서 시작 됩니다 _PreferredMoveBeginDate_ -가능성이 이동 하면 됩니다.

-   _PreferredMoveEndDate_ -가능성이 이동 하면 됩니다 최상의 노력 별로이 지정한 시간까지 완료 합니다.

## <a name="cancel-a-onedrive-geo-move"></a>OneDrive 지리적으로 분산 이동을 취소 합니다. 

이동 하는 진행 중인 아닌 경우 사용자의 OneDrive의 지리적으로 분산 이동을 중지할 수 또는 cmdlet을 사용 하 여 완료 합니다.

`Stop-SPOUserAndContentMove – UserPrincipalName <UserPrincipalName>`

여기서 _UserPrincipalName_ 은 해당 OneDrive 중지 하려는 이동 하는 사용자의 UPN입니다.

## <a name="determining-current-status"></a>현재 상태를 확인합니다.

지리적으로 분산 이동 또는 Get SPOUserAndContentMoveState cmdlet을 사용 하 여에 연결 된 지리적으로 분산 로그 OneDrive의 상태를 확인할 수 있습니다.

이동 상태를 확인 하는 다음 표에 설명 되어있습니다.

<table>
<thead>
<tr class="header">
<th align="left"><strong>Status</strong></th>
<th align="left"><strong>설명</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">이 notstarted 인</td>
<td align="left">이동 하는 시작 되지 않았습니다.</td>
</tr>
<tr class="even">
<td align="left">진행 중 (<em></em>n/4)</td>
<td align="left">이동이 상태는 다음 중 하나에서 진행 중인: 유효성 검사 (1/4) (2/4)를 백업, 복원 (3/4) 정리 (4/4).</td>
</tr>
<tr class="odd">
<td align="left">성공</td>
<td align="left">이동이 성공적으로 완료 했습니다.</td>
</tr>
<tr class="even">
<td align="left">Failed</td>
<td align="left">이동에 실패 했습니다.</td>
</tr>
</tbody>
</table>

특정 사용자를 이동의 상태를 찾으려면 UserPrincipalName 매개 변수를 사용 합니다.

`Get-SPOUserAndContentMoveState -UserPrincipalName <UPN>`

모든는 이동의 상태를 찾으려면 또는 지리적 위치에 연결 된 로그는 다음 값 중 하나로 MoveState 매개 변수를 사용:이 notstarted 인, 진행 중, 성공, 실패, 모든 합니다.

`Get-SPOUserAndContentMoveState -MoveState <value>`

추가할 수 있습니다는 `-Verbose` 에 대 한 더 자세한 설명은 이동 상태 매개 변수입니다.

## <a name="user-experience"></a>사용자 환경

자신의 OneDrive 다른 지리적 위치로 이동 하는 경우 OneDrive의 사용자가 영향을 최소화 하는 것을 알 해야 합니다. 간단한 읽기 전용 상태를 이동 하는 동안 외에도 이동이 완료 되 면 예상 대로 작동 하도록 기존 링크 및 사용 권한을 계속 됩니다.

### <a name="onedrive-for-business"></a>비즈니스용 OneDrive

진행 중인으로 이동 하는 동안에 읽기 전용 사용자의 OneDrive 설정 됩니다. 이동이 완료 되 면 Office 365 응용 프로그램 시작 관리자 또는 웹 브라우저를 OneDrive을 탐색할 때 사용자가 새로운 지리적 위치에 자신의 OneDrive로 전달 됩니다.

### <a name="permissions-on-onedrive-content"></a>OneDrive 내용에 대 한 권한

OneDrive 콘텐츠에 대 한 사용 권한 가진 사용자는 이동 하는 동안 및 완료 된 후 콘텐츠에 액세스할 수 있도록 계속 됩니다.

### <a name="onedrive-sync-client"></a>OneDrive 동기화 클라이언트 

OneDrive 동기화 클라이언트는 자동으로 검색 하 고 원활 하 게 OneDrive 지리적으로 분산 이동이 완료 되 면 새 OneDrive 위치에 동기화를 전송 됩니다. 사용자 다시 로그인 하거나 다른 작업을 수행할 필요가 없습니다.

OneDrive 지리적으로 분산 이동 하는 진행 중인 동안 파일을 업데이트 하는 사용자, 하는 경우 동기화 클라이언트에서이 알려줍니다 하기 때문에 보류 중인 파일 업로드가 이동이 진행 되는 동안 합니다.

### <a name="sharing-links"></a>링크를 공유합니다. 

OneDrive 지리적으로 분산 시 완료를 이동, 이동 된 파일에 대 한 기존 공유 링크는 새로운 지리적 위치에 자동으로 리디렉션합니다.

### <a name="onenote-experience"></a>OneNote 환경 

OneNote win32 클라이언트와 UWP (범용) App 자동으로 검색 하 고 원활 하 게 OneDrive 지리적으로 분산 이동이 완료 되 면 새 OneDrive 위치로 전자 필기장을 동기화 됩니다. 사용자 다시 로그인 하거나 다른 작업을 수행할 필요가 없습니다. 사용자에 게 표시 되는 항목만 표시기가 OneDrive 지리적으로 분산 이동이 진행 중인 경우 전자 필기장 동기화 실패 하 게 합니다. 이 작업이 다음 버전의 OneNote 클라이언트에서 사용할 수 있습니다.

-   OneNote win32 – 버전 16.0.8326.2096 (및 이상)

-   OneNote UWP – 버전 16.0.8431.1006 (및 이상)

-   OneNote Mobile App – 버전 16.0.8431.1011 (및 이상)

### <a name="teams-app"></a>팀이 응용 프로그램

OneDrive 지리적으로 분산 시 완료를 이동 하 고, 사용자는 액세스할 자신의 OneDrive 파일에 팀 app. 또한 하 고, 지리적으로 분산 이동 하기 전에 해당 OneDrive에서 팀 채팅을 통해 공유 하는 파일 이동이 완료 한 후에 작동을 계속 됩니다.

### <a name="onedrive-for-business-mobile-app-ios"></a>비즈니스 모바일 응용 프로그램 (iOS)에 대 한 OneDrive 

OneDrive 지리적으로 분산 시 완료를 이동, 로그 아웃 하 고 다시 로그인 iOS 모바일 응용 프로그램에 새 OneDrive 위치를 동기화 하는 사용자가 있어야 합니다.

### <a name="existing-followed-groups-and-sites"></a>그룹 및 사이트 뒤에 기존

열어본된 사이트 및 그룹의 지리적 위치에 관계 없이 비즈니스에 대 한 사용자의 OneDrive에 표시 됩니다. 사이트 및 다른 지리적 위치에 호스트 그룹을 별도 탭에서 열립니다.
