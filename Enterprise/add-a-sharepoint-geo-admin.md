---
title: 지역 관리자 추가 또는 제거
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
description: Office 365 Multi-Geo에서 지역 관리자를 추가하거나 제거하는 방법에 대해 알아봅니다.
ms.openlocfilehash: 767dcf5284e93b9a2e908d4ec837f034b29cb6db
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068474"
---
# <a name="add-or-remove-a-geo-administrator-in-office-365-multi-geo"></a>Office 365 Multi-Geo에서 지역 관리자 추가 또는 제거

테넌트가 있는 지리적 위치마다 별도의 관리자를 구성할 수 있습니다. 이러한 관리자는 지리적 위치와 관련된 SharePoint Online 및 OneDrive 설정에 액세스할 수 있습니다.

용어 저장소와 같은 일부 서비스는 중앙 위치에서 관리되고 위성 위치로 복제됩니다. 중앙 위치의 지역 관리자는 이러한 위치 정보에 액세스할 수 있지만 위성 위치 지역 관리자는 액세스하지 못합니다.

전역 관리자와 SharePoint Online 관리자는 중앙 위치 및 모든 위성 위치의 설정에 계속 액세스할 수 있습니다.

## <a name="configuring-geo-administrators"></a>지역 관리자 구성

지역 관리자를 구성하려면 SharePoint Online PowerShell 모듈이 필요합니다.

[Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService)를 사용하여 지역 관리자를 추가할 지리적 위치의 관리 센터에 연결합니다. (예 : Connect-SPOService  https://ContosoEUR-admin.sharepoint.com.)

어떤 위치의 기존 지역 관리자를 보려면 다음을 실행하세요. `Get-SPOGeoAdministrator` 

### <a name="adding-a-user-as-a-geo-admin"></a>지역 관리자 권한으로 사용자를 추가

지역 관리자 권한으로로 사용자를 추가하려면 다음을 실행하세요. `Add-SPOGeoAdministrator -UserPrincipalName <UPN>`

한 위치의 지역 관리자를 제거하려면 다음을 실행하세요.  `Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`

### <a name="adding-a-group-as-a-geo-admin"></a>지역 관리자 권한으로 그룹을 추가

지역 관리자 권한으로 보안 그룹이나 메일 사용 가능 보안 그룹을 추가할 수 있습니다. (메일 그룹 및 Office 365 그룹은 지원되지 않습니다.)

지역 관리자 권한으로 그룹을 추가하려면 다음을 실행하세요. `Add-SPOGeoAdministrator -GroupAlias <alias>`

지역 관리자 권한으로 그룹을 제거하려면 다음을 실행하세요. `Remove-SPOGeoAdministrator -GroupAlias <alias>`

모든 보안 그룹이 그룹 별칭이 있는 것은 아닙니다. 별칭이 없는 보안 그룹을 추가하려면 [Get-MsolGroup](https://docs.microsoft.com/en-us/powershell/module/msonline/get-msolgroup)을 실행하여 그룹 목록을 검색하고 보안 그룹의 ObjectID를 찾은 다음 다음을 실행합니다.

`Add-SPOGeoAdministrator -ObjectID <ObjectID>`

ObjectID를 사용하여 그룹을 제거하려면 다음을 실행하세요. `Remove-SPOGeoAdministrator -ObjectID <ObjectID>`

## <a name="see-also"></a>참고 항목

[Add-SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/add-spogeoadministrator)

[Get-SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spogeoadministrator)

[Remove-SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/remove-spogeoadministrator)

[보안 그룹에 대한 별칭(MailNickName) 설정](https://docs.microsoft.com/en-us/powershell/module/azuread/set-azureadgroup)