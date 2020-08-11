---
title: SharePoint Online 사이트 만들기 및 PowerShell을 사용 하 여 사용자 추가
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
- SPO_Content
- seo-marvel-apr2020
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: '요약: PowerShell을 사용 하 여 새 SharePoint Online 사이트를 만든 다음 해당 사이트에 사용자 및 그룹을 추가 합니다.'
ms.openlocfilehash: 85694799c32d0a075a158df47dc021bbbbe0c844
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606004"
---
# <a name="create-sharepoint-online-sites-and-add-users-with-powershell"></a>SharePoint Online 사이트 만들기 및 PowerShell을 사용 하 여 사용자 추가

*이 문서는 Microsoft 365 Enterprise와 Office 365 Enterprise에 모두 적용됩니다.*

Microsoft 365 용 PowerShell을 사용 하 여 SharePoint Online 사이트를 만들고 사용자를 추가 하는 경우 Microsoft 365 관리 센터에서 보다 훨씬 빠르게 작업을 빠르게 수행할 수 있습니다. Microsoft 365 관리 센터에서 수행할 수 없는 작업을 수행할 수도 있습니다. 

## <a name="connect-to-sharepoint-online"></a>SharePoint Online에 연결

이 항목의 절차를 수행 하려면 SharePoint Online에 연결 해야 합니다. 자세한 내용은 [SharePoint Online PowerShell에 연결을](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps) 참조 하세요.

## <a name="step-1-create-new-site-collections-using-powershell"></a>1 단계: PowerShell을 사용 하 여 새 사이트 모음 만들기

제공 된 예제 코드와 메모장을 사용 하 여 만든 PowerShell 및 .csv 파일을 사용 하 여 여러 사이트를 만듭니다. 이 절차에서는 괄호로 표시 된 자리 표시자 정보를 자체 사이트 및 테 넌 트 관련 정보와 함께 대체 합니다. 이 프로세스를 통해 단일 파일을 만들고 해당 파일을 사용 하는 단일 PowerShell 명령을 실행할 수 있습니다. 이렇게 하면 반복 및 이식 가능 하 게 작업을 수행 하 고 SharePoint Online 관리 셸에 긴 명령을 입력 하는 것과 같은 여러 가지 오류를 모두 없앨 수 있습니다. 이 절차는 두 부분으로 구성 됩니다. 먼저 .csv 파일을 만든 다음 PowerShell을 사용 하 여 해당 .csv 파일을 참조 하 여 해당 콘텐츠를 사용 하 여 사이트를 만듭니다.

PowerShell cmdlet은 .csv 파일을 가져온 후 파일의 첫 번째 줄을 열 머리글로 읽는 중괄호 내부의 루프에 파이프 합니다. 그런 다음 PowerShell cmdlet은 나머지 레코드를 반복 하 고 각 레코드에 대해 새 사이트 모음을 만들고, 열 머리글에 따라 사이트 모음의 속성을 할당 합니다.

### <a name="create-a-csv-file"></a>.csv 파일 만들기

1. 메모장을 열고 다음 텍스트 블록을 붙여 넣습니다.<br/>

```powershell
Owner,StorageQuota,Url,ResourceQuota,Template,TimeZoneID,Name
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/TeamSite01,25,EHS#1,10,Contoso Team Site
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/Blog01,25,BLOG#0,10,Contoso Blog
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Project01,25,PROJECTSITE#0,10,Project Alpha
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Community01,25,COMMUNITY#0,10,Community Site
```
<br/>여기서 *테* 넌 트에서은 테 넌 트의 이름이 고 *소유자* 는 기본 사이트 모음 관리자 역할을 부여 하려는 테 넌 트에 있는 사용자의 사용자 이름입니다.<br/>(메모장을 사용 하 여 빠르게 대량으로 바꿀 때 Ctrl + H를 누를 수 있습니다.)<br/>

2. **SiteCollections.csv**으로 데스크톱에 파일을 저장 합니다.<br/>

> [!TIP]
> 이 또는 다른 .csv 또는 Windows PowerShell 스크립트 파일을 사용 하기 전에 불필요 하거나 인쇄 되지 않는 문자가 없는지 확인 하는 것이 좋습니다. 이렇게 하려면 Word에서 파일을 열고 리본 메뉴에서 단락 아이콘을 클릭하여 인쇄할 수 없는 문자를 표시합니다. 불필요한 인쇄할 수 없는 문자가 없어야 합니다. 예를 들어 파일 끝의 마지막 단락 표시 뒤에는 단락 표시가 없어야 합니다.

### <a name="run-the-windows-powershell-command"></a>Windows PowerShell 명령 실행

1. Windows PowerShell 프롬프트에서 다음 명령을 입력 하거나 복사 하 여 붙여 넣은 다음 enter 키를 누릅니다.<br/>
```powershell
Import-Csv C:\users\MyAlias\desktop\SiteCollections.csv | ForEach-Object {New-SPOSite -Owner $_.Owner -StorageQuota $_.StorageQuota -Url $_.Url -NoWait -ResourceQuota $_.ResourceQuota -Template $_.Template -TimeZoneID $_.TimeZoneID -Title $_.Name}
```
<br/>여기서 *Myalias* 는 사용자 별칭과 같습니다.<br/>

2. Windows PowerShell 프롬프트가 다시 나타날 때까지 기다립니다. 1~2분 정도 걸릴 수 있습니다.<br/>

3. Windows PowerShell 프롬프트에서 다음 cmdlet을 입력 하거나 복사 하 여 붙여 넣은 다음 enter 키를 누릅니다.<br/>

```powershell
Get-SPOSite -Detailed | Format-Table -AutoSize
```
<br/>

4. 목록의 새 사이트 모음을 확인합니다. 예제 CSV 파일을 사용 하 여 **TeamSite01**, **Blog01**, **Project01**및 **Community01** 사이트 모음을 확인할 수 있습니다.

그거에요. 만든 .csv 파일 및 단일 Windows PowerShell 명령을 사용 하 여 여러 사이트 모음을 만들었습니다. 이제이 사이트에 사용자를 만들고 할당할 준비가 되었습니다.

## <a name="step-2-add-users-and-groups"></a>2단계: 사용자 및 그룹 추가

이제 사용자를 만들어 사이트 모음 그룹에 추가할 수 있습니다. 그런 다음 .csv 파일을 사용하여 새 그룹 및 사용자를 대량 업로드합니다.

다음 절차에서는 TeamSite01, Blog01, Project01 및 Community01의 예제 사이트를 계속 사용 합니다.

### <a name="create-csv-and-ps1-files"></a>.csv 및 .ps1 파일 만들기

1. 메모장을 열고 다음 텍스트 블록을 붙여 넣습니다.<br/>

```powershell
Site,Group,PermissionLevels
https://tenant.sharepoint.com/sites/Community01,Contoso Project Leads,Full Control
https://tenant.sharepoint.com/sites/Community01,Contoso Auditors,View Only
https://tenant.sharepoint.com/sites/Community01,Contoso Designers,Design
https://tenant.sharepoint.com/sites/TeamSite01,XT1000 Team Leads,Full Control
https://tenant.sharepoint.com/sites/TeamSite01,XT1000 Advisors,Edit
https://tenant.sharepoint.com/sites/Blog01,Contoso Blog Designers,Design
https://tenant.sharepoint.com/sites/Blog01,Contoso Blog Editors,Edit
https://tenant.sharepoint.com/sites/Project01,Project Alpha Approvers,Full Control
```
<br/>여기서 *테 넌* 트에서 테 넌 트 이름과 같습니다.<br/>

2. **GroupsAndPermissions.csv**으로 데스크톱에 파일을 저장 합니다.<br/>

3. 새 메모장 인스턴스를 열고 다음 텍스트 블록을 붙여 넣습니다.<br/>

```powershell
Group,LoginName,Site
Contoso Project Leads,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Community01
Contoso Auditors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Community01
Contoso Designers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Community01
XT1000 Team Leads,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/TeamSite01
XT1000 Advisors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/TeamSite01
Contoso Blog Designers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Blog01
Contoso Blog Editors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Blog01
Project Alpha Approvers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Project01
```
<br/>여기서 *테 넌 트는* 테 넌 트 이름과 같고 *username* 은 기존 사용자의 사용자 이름과 같습니다.<br/>

4. **Users.csv**으로 데스크톱에 파일을 저장 합니다.<br/>

5. 새 메모장 인스턴스를 열고 다음 텍스트 블록을 붙여 넣습니다.<br/>

```powershell
Import-Csv C:\users\MyAlias\desktop\GroupsAndPermissions.csv | ForEach-Object {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\users\MyAlias\desktop\Users.csv | where {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```
<br/>여기서 MyAlias는 현재 로그온 되어 있는 사용자의 사용자 이름과 같습니다.<br/>

6. **UsersAndGroups.ps1**으로 데스크톱에 파일을 저장 합니다. 간단한 Windows PowerShell 스크립트입니다.

이제 UsersAndGroup.ps1 스크립트를 실행하여 사용자와 그룹을 여러 사이트 모음에 추가할 수 있습니다.

### <a name="run-usersandgroupsps1-script"></a>UsersAndGroups.ps1 스크립트 실행

1. SharePoint Online 관리 셸로 돌아갑니다.<br/>
2. Windows PowerShell 프롬프트에서 다음 줄을 입력 하거나 복사 하 여 붙여 넣은 다음 enter 키를 누릅니다.<br/>
```powershell
Set-ExecutionPolicy Bypass
```
<br/>

3. 확인 메시지가 나타나면 **Y**키를 누릅니다.<br/>

4. Windows PowerShell 프롬프트에서 다음을 입력 하거나 복사 하 여 붙여 넣은 다음 enter 키를 누릅니다.<br/>

```powershell
c:\users\MyAlias\desktop\UsersAndGroups.ps1
```
<br/>여기서 *Myalias* 는 사용자 이름과 같습니다.<br/>

5. 프롬프트가 반환될 때까지 기다렸다가 계속 진행합니다. 먼저 작성된 그룹이 표시되고, 사용자를 추가하면 그룹 목록이 반복적으로 표시됩니다.

## <a name="see-also"></a>기타 참고 항목

[SharePoint Online PowerShell에 연결](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[PowerShell을 사용 하 여 SharePoint Online 사이트 그룹 관리](manage-sharepoint-site-groups-with-powershell.md)

[PowerShell로 Microsoft 365 관리](manage-office-365-with-office-365-powershell.md)
  
[Microsoft 365 용 PowerShell 시작](getting-started-with-office-365-powershell.md)

