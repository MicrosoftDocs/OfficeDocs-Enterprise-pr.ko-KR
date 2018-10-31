---
title: 지역 관리자 추가 또는 제거
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: 추가 또는 OneDrive에 대 한 비즈니스 다중-지리적으로 분산 지리적으로 분산 관리자를 제거 하는 방법에 알아봅니다.
ms.openlocfilehash: 4e8c8bec148d5a4e7e55ffa2b08a49cd2ea6aa0a
ms.sourcegitcommit: a3e2b2e58c328238c15d3f9daf042ea3de9d66be
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/30/2018
ms.locfileid: "25849814"
---
# <a name="add-or-remove-a-geo-administrator-in-onedrive-for-busniess-multi-geo"></a>추가 또는 OneDrive에 대 한 Busniess 다중-지리적으로 분산 지리적으로 분산 관리자 제거

테 넌 트에 있는 각 지리적 위치에 대 한 별도 관리자를 구성할 수 있습니다. 이러한 관리자에는 해당 지리적 위치에만 적용 되는 SharePoint Online 및 OneDrive 설정에 액세스할을 수 있습니다.

용어 저장소-등의 일부 서비스-중앙 위치에서 관리 되며 위성 위치에 복제 됩니다. 중앙 위치에 대 한 지리적으로 분산 관리는 위성 위치에 대 한 지리적으로 분산 admins 하지 하는 반면, 여기에 액세스할 수 있습니다.

전역 관리자 및 SharePoint Online 관리자가 중앙 위치 및 위성 위치를 모두의 설정에 대 한 액세스를 계속 합니다.

## <a name="configuring-geo-administrators"></a>지리적으로 분산 관리자 구성

지리적으로 분산 관리자를 구성 하려면 SharePoint Online PowerShell 모듈이 필요 합니다.

[Connect-sposervice](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) 를 사용 하 여 지리적으로 분산 관리자를 추가 하려는 지리적으로 분산 위치의 관리 센터에 연결 하려면 (예: Connect-sposervicehttps://ContosoEUR-admin.sharepoint.com.)

실행 하는 기존 지리적으로 분산 admins의 위치를 보려면`Get-SPOGeoAdministrator`

### <a name="adding-a-user-as-a-geo-admin"></a>지리적으로 분산 관리 권한으로 사용자 추가 (영문)

지리적으로 분산 관리 권한으로 사용자를 추가, 실행`Add-SPOGeoAdministrator -UserPrincipalName <UPN>`

사용자의 위치를 지리적으로 분산 관리자를 제거 하려면 다음을 실행합니다`Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`

### <a name="adding-a-group-as-a-geo-admin"></a>지리적으로 분산 관리자 그룹 추가 (영문)

지리적으로 분산 관리자로 보안 그룹 또는 메일 사용이 가능한 보안 그룹을 추가할 수 있습니다. (메일 그룹 및 Office 365 그룹 지원 되지 않습니다.)

지리적으로 분산 관리자 권한으로 그룹을 추가 하려면 실행`Add-SPOGeoAdministrator -GroupAlias <alias>`

지리적으로 분산 관리자 권한으로 그룹을 제거 하려면 다음을 실행합니다`Remove-SPOGeoAdministrator -GroupAlias <alias>`

참고는 일부 보안 그룹의 경우 그룹 별칭입니다. 그룹 목록을 검색 하려면 [Get MsolGroup](https://docs.microsoft.com/en-us/powershell/module/msonline/get-msolgroup) 실행 하는 별칭 없는 보안 그룹을 추가 하려는 경우 보안 그룹의 ObjectID 찾아 다음을 실행 합니다.

`Add-SPOGeoAdministrator -ObjectID <ObjectID>`

실행 하는 ObjectID를 사용 하 여 그룹을 제거 하려면`Remove-SPOGeoAdministrator -ObjectID <ObjectID>`

### <a name="accessing-the-admin-center-for-a-specific-geo-location"></a>특정 지리적 위치에 대 한 관리 센터 액세스 (영문)

지리적 위치에 대 한 OneDrive 설정을 관리 하려면 관리자가 다음 URL 형식을 사용 하 여 직접 OneDrive 관리 센터에 액세스 해야 합니다.

https://admin.onedrive.com/?geo=<*지리적으로 분산*>

캐나다에 대 한 OneDrive 관리 센터에는 예: https://admin.onedrive.com/?geo=CAN합니다.

## <a name="see-also"></a>참고 항목

[추가 SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/add-spogeoadministrator)

[Get-SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spogeoadministrator)

[SPOGeoAdministrator 제거](https://docs.microsoft.com/powershell/module/sharepoint-online/remove-spogeoadministrator)

[보안 그룹에 대 한 별칭 (MailNickName) 설정](https://docs.microsoft.com/en-us/powershell/module/azuread/set-azureadgroup)