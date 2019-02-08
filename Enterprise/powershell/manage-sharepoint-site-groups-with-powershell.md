---
title: Manage SharePoint Online site groups with Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/01/2018
ms.audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: '요약: SharePoint Online 사이트 그룹을 관리 하려면 Office 365 PowerShell를 사용 합니다.'
ms.openlocfilehash: 62643cabb2377c07117299dc25314cd515a06791
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897161"
---
# <a name="manage-sharepoint-online-site-groups-with-office-365-powershell"></a>Manage SharePoint Online site groups with Office 365 PowerShell

 **요약:** SharePoint Online 사이트 그룹을 관리 하려면 Office 365 PowerShell을 사용 합니다.
  
Office 365 관리 센터를 사용할 수 있지만 SharePoint Online 사이트 그룹을 관리 하려면 Office 365 PowerShell를 사용할 수도 있습니다.

## <a name="before-you-begin"></a>시작하기 전에

이 문서의 절차에서는 SharePoint Online에 연결 해야 합니다. 자세한 내용은 [SharePoint Online PowerShell 연결](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)을 참조 하십시오.

## <a name="view-sharepoint-online-with-office-365-powershell"></a>Office 365 PowerShell 사용 하 여 보기 SharePoint를 온라인

SharePoint Online 관리 센터에 사이트 그룹을 관리 하기 위한 일부 사용 하기 쉬운 메서드가 있습니다. 예, 그룹 및 그룹 구성원에 대 한 확인 하려는 경우를 가정해 보겠습니다는 `https://litwareinc.sharepoint.com/sites/finance` 사이트입니다. 다음을 수행 해야하는 작업은입니다.

1. Office 365 관리 센터에서 **자원**을 클릭 > **사이트**를 한 다음 사이트의 URL을 클릭 합니다.
2. 사이트 모음 대화 상자에서 **이 사이트로 이동**합니다.를 클릭 합니다.
3. 사이트 페이지에서 (페이지의 오른쪽 상단 모서리에 있음) **설정** 아이콘을 클릭 한 다음 **사이트 설정**을 클릭 합니다.<br/>
![SharePoint Online 사이트 설정](media/spo-site-settings.png)<br/>
4. 사이트 설정 페이지의 **사용자 및 사용 권한에서** **사이트 사용 권한** 을 클릭 합니다.

확인하려는 다음 사이트에 대해 프로세스를 반복합니다.

Office 365 powershell 그룹의 목록을 가져오려면, 하려면 다음 명령 집합을 사용 있습니다.

```
$siteURL = "https://litwareinc.sharepoint.com/sites/finance"
$x = Get-SPOSiteGroup -Site $siteURL
foreach ($y in $x)
    {
        Write-Host $y.Title -ForegroundColor "Yellow"
        Get-SPOSiteGroup -Site $siteURL -Group $y.Title | Select-Object -ExpandProperty Users
        Write-Host
    }
```

두 가지 방법을 사용 하 여 SharePoint Online 관리 셸 명령 프롬프트에서 설정이 명령을 실행할 수 있습니다.

- 명령을 메모장 (또는 다른 텍스트 편집기)에 복사, **$siteURL** 변수의 값을 수정, 명령, 선택한 SharePoint Online 관리 셸 명령 프롬프트에 붙여넣습니다. PowerShell에서 중지를 수행 하면 한 **>>** 프롬프트 합니다. Enter 키를 눌러 **foreach** 명령을 실행 합니다.<br/>
- 메모장 (또는 다른 텍스트 편집기)에 명령을 복사 하 고 **$siteURL** 변수의 값을 수정 이름과 적절 한 폴더에.ps1 확장명으로이 텍스트 파일을 저장 합니다. 다음으로, 해당 경로 파일 이름을 지정 하 여 SharePoint Online 관리 셸 명령 프롬프트에서 스크립트를 실행 합니다. 다음은 예제 명령이입니다.

```
C:\Scripts\SiteGroupsAndUsers.ps1
```

두 경우 모두이 다음과 비슷한 결과가 나타납니다.

![SharePoint Online 사이트 그룹](media/SPO-site-groups.png)

다음은 사이트에 대해 만들어진 모든 그룹 `https://litwareinc.sharepoint.com/sites/finance`, 하 고 해당 그룹에 할당 된 모든 사용자입니다. 그룹 이름은 구성원 에게만에서 별도 그룹 이름 하는데 도움이 되는 노란색에서입니다.

다른 예로 명령 집합은 그룹 및 모든 SharePoint Online 사이트의 모든 그룹 구성원을 나열 하는 다음과 같습니다.

```
$x = Get-SPOSite
foreach ($y in $x)
    {
        Write-Host $y.Url -ForegroundColor "Yellow"
        $z = Get-SPOSiteGroup -Site $y.Url
        foreach ($a in $z)
            {
                 $b = Get-SPOSiteGroup -Site $y.Url -Group $a.Title 
                 Write-Host $b.Title -ForegroundColor "Cyan"
                 $b | Select-Object -ExpandProperty Users
                 Write-Host
            }
    }
```
    
## <a name="see-also"></a>참고 항목

[SharePoint Online PowerShell에 연결](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[SharePoint Online 사이트를 만들고 Office 365 PowerShell을 사용하여 사용자 추가](create-sharepoint-sites-and-add-users-with-powershell.md)

[Office 365 PowerShell을 사용하여 SharePoint Online 사용자 및 그룹 관리](manage-sharepoint-users-and-groups-with-powershell.md)

[Office 365 PowerShell로 Office 365 관리](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell 시작](getting-started-with-office-365-powershell.md)

