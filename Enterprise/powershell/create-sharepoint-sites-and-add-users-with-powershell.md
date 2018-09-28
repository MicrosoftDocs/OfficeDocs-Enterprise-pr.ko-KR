---
title: SharePoint Online 사이트를 만들고 Office 365 PowerShell을 사용하여 사용자 추가
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: '요약: Office 365 PowerShell을 사용 새 SharePoint Online 사이트를 만들고 다음 해당 사이트에 사용자 및 그룹을 추가 합니다.'
ms.openlocfilehash: 41ca26249bd494d5603a425689e47f9fe6809f1a
ms.sourcegitcommit: 82219b5f8038ae066405dfb7933c40bd1f598bd0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/14/2018
ms.locfileid: "23975206"
---
# <a name="create-sharepoint-online-sites-and-add-users-with-office-365-powershell"></a>SharePoint Online 사이트를 만들고 Office 365 PowerShell을 사용하여 사용자 추가

 **요약:** Office 365 PowerShell을 사용 하 여 새 SharePoint Online 사이트를 만드는 하 고 해당 사이트에 사용자 및 그룹을 추가 합니다.

Office 365 PowerShell을 사용 하 여 SharePoint Online 사이트를 만들고 사용자를 추가 하려면 작업 Office 356 관리 센터에서 수 있는 것 보다 훨씬 더 빠르게 신속 하 고 반복적으로 수행할 수 있습니다. 또한 Office 356 관리 센터에서 수행할 수 없는 작업을 수행할 수 있습니다. 

## <a name="before-you-begin"></a>시작하기 전에

이 항목의 절차에서는 SharePoint Online에 연결 해야 합니다. 자세한 내용은 [Connect to SharePoint Online PowerShell를](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps) 참조 하십시오.

## <a name="step-1-create-new-site-collections-using-office-365-powershell"></a>1 단계: Office 365 PowerShell을 사용 하 여 새 사이트 모음 만들기

Office 365 PowerShell 및 제공 하는 예제 코드 및 메모장을 사용 하 여 만든.csv 파일을 사용 하 여 여러 사이트를 만듭니다. 이 절차에 대 한 사용자의 사이트 및 테 넌 트 관련 정보로 괄호 안에 표시 되는 개체 틀 정보를 교체 합니다. 이 프로세스를 사용 하면 단일 파일을 만들고 해당 파일을 사용 하는 단일 Office 365 PowerShell 명령을 실행할 수 있습니다. 이 반복 및 휴대용 모두를 수행 하는 작업을 만들고 하는 경우 SharePoint Online 관리 셸에 입력 하는 long 명령에서 발생할 수 있는 모든 오류를 여러 명 제거 합니다. 이 절차를 두 부분으로 구성 있습니다. .Csv 파일을 만들 먼저 하 고를 사용 하 여 해당 콘텐츠는 사이트를 만들 Office 365 PowerShell을 사용 하 여 해당.csv 파일을 참조 합니다.

Office 365 PowerShell cmdlet은.csv 파일 가져오고 중괄호 안에 열 머리글로 파일의 첫 줄을 읽고 하는 루프에 파이프 합니다. Office 365 PowerShell cmdlet은 다음 나머지 레코드를 반복, 각 레코드에 대 한 새 사이트 모음을 만들고 열 머리글에 따라 사이트 모음의 속성을 할당 합니다.

### <a name="create-a-csv-file"></a>.csv 파일 만들기

1. 메모장을 열고 다음 텍스트 블록을 붙여 넣습니다.<br/>

```
Owner,StorageQuota,Url,ResourceQuota,Template,TimeZoneID,Name
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/TeamSite01,25,EHS#1,10,Contoso Team Site
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/Blog01,25,BLOG#0,10,Contoso Blog
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Project01,25,PROJECTSITE#0,10,Project Alpha
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Community01,25,COMMUNITY#0,10,Community Site
```
<br/>여기서 *테 넌 트* 은 테 넌 트의 이름 및 *소유자* 는 누구에 게를 테 넌 트에 대 한 사용자의 사용자 이름에 주 사이트 모음 관리자의 역할을 부여 하려는 합니다.<br/>(누르면 Ctrl + H 메모장을 사용 하 여 바꾸기 대량으로 보다 빠르게.)<br/>

2. 파일을 바탕 **화면에 SiteCollections.csv**로 저장 합니다.<br/>

> [!TIP]
> 이 또는 기타 모든.csv 또는 Windows PowerShell 스크립트 파일을 사용 하기 전에 것이 좋습니다 불필요 한 또는 인쇄할 수 없는 문자가 없는 되었는지 있는지 확인 합니다. Word에서 하 고 리본 메뉴에서 파일을 엽니다, 그리고 인쇄할 수 없는 문자를 표시 하려면 단락 아이콘을 클릭 합니다. 불필요 한 인쇄할 수 없는 문자가 더 있어야 합니다. 예, 없는 단락 기호 파일의 끝에 최종 하나 이상 있어야 합니다.

### <a name="run-the-windows-powershell-command"></a>Windows PowerShell 명령 실행

1. Windows PowerShell 프롬프트에서 입력 또는 복사 하 고 다음 cmdlet를 붙여넣은 Enter 키를 누릅니다.<br/>
```
Import-Csv C:\users\MyAlias\desktop\SiteCollections.csv | ForEach-Object {New-SPOSite -Owner $_.Owner -StorageQuota $_.StorageQuota -Url $_.Url -NoWait -ResourceQuota $_.ResourceQuota -Template $_.Template -TimeZoneID $_.TimeZoneID -Title $_.Name}
```
<br/>여기서 *MyAlias* 는 사용자 별칭입니다.<br/>

2. 다시 표시 하는 Windows PowerShell 메시지가 표시 될 때까지 기다립니다. -2 분 정도 걸릴 수 있습니다.<br/>

3. Windows PowerShell 프롬프트에서 입력 또는 복사 하 고 다음 cmdlet를 붙여넣은 Enter 키를 누릅니다.<br/>

```
Get-SPOSite -Detailed | Format-Table -AutoSize
```
<br/>

4. 목록에서 새 사이트 모음을 note 합니다. 다음 사이트 모음을 확인할: ** **contosotest**, **TeamSite01**, **Blog01**, project01**

그거에요. 만든.csv 파일을 사용 하 여 여러 사이트 모음 및 단일 Windows PowerShell cmdlet를 만들었습니다. 이제를 만들고 이러한 사이트에 사용자를 할당할 준비가 되었습니다.

## <a name="step-2-add-users-and-groups"></a>2단계: 사용자 및 그룹 추가

이제 사용자를 만들어 사이트 모음 그룹에 추가할 수 있습니다. 그런 다음 .csv 파일을 사용하여 새 그룹 및 사용자를 대량 업로드합니다.

다음 절차에서는 contosotest, TeamSite01, Blog01, Project01 사이트 모음을 정상적으로 만들었다고 가정합니다.

### <a name="create-csv-and-ps1-files"></a>.csv 및 .ps1 파일 만들기

1. 메모장을 열고 다음 텍스트 블록을 붙여 넣습니다.<br/>
```
Site,Group,PermissionLevels
https://tenant.sharepoint.com/sites/contosotest,Contoso Project Leads,Full Control
https://tenant.sharepoint.com/sites/contosotest,Contoso Auditors,View Only
https://tenant.sharepoint.com/sites/contosotest,Contoso Designers,Design
https://tenant.sharepoint.com/sites/TeamSite01,XT1000 Team Leads,Full Control
https://tenant.sharepoint.com/sites/TeamSite01,XT1000 Advisors,Edit
https://tenant.sharepoint.com/sites/Blog01,Contoso Blog Designers,Design
https://tenant.sharepoint.com/sites/Blog01,Contoso Blog Editors,Edit
https://tenant.sharepoint.com/sites/Project01,Project Alpha Approvers,Full Control
```
<br/>여기서 *테 넌 트* 테 넌 트 이름입니다.<br/>

2. 바탕 화면에 파일을 **화면에 GroupsAndPermissions.csv**로 저장 합니다.<br/>

3. 새 메모장 인스턴스를 열고 다음 텍스트 블록을 붙여 넣습니다.<br/>

```
Group,LoginName,Site
Contoso Project Leads,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/contosotest
Contoso Auditors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/contosotest
Contoso Designers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/contosotest
XT1000 Team Leads,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/TeamSite01
XT1000 Advisors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/TeamSite01
Contoso Blog Designers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Blog01
Contoso Blog Editors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Blog01
Project Alpha Approvers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Project01
```
<br/>여기서 *테 넌 트* 테 넌 트 이름, 하 고 *사용자 이름* 에 기존 사용자의 사용자 이름과 같습니다.<br/>

4. 파일을 바탕 화면에 **Users.csv**로 저장 합니다.<br/>

5. 새 메모장 인스턴스를 열고 다음 텍스트 블록을 붙여 넣습니다.<br/>

```
Import-Csv C:\users\MyAlias\desktop\GroupsAndPermissions.csv | ForEach-Object {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\users\MyAlias\desktop\Users.csv | where {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```
<br/>여기서 MyAlias는 현재 로그온 한 사용자의 사용자 이름과를 같습니다.<br/>

6. **UsersAndGroups.ps1**로 바탕 화면에 파일을 저장 합니다. 간단한 Windows PowerShell 스크립트입니다.

이제 UsersAndGroup.ps1 스크립트를 실행하여 사용자와 그룹을 여러 사이트 모음에 추가할 수 있습니다.

### <a name="run-usersandgroupsps1-script"></a>UsersAndGroups.ps1 스크립트 실행

1. SharePoint Online 관리 셸로 돌아갑니다.<br/>
2. Windows PowerShell 프롬프트에서 입력 하거나 복사 하 고, 다음 줄을 붙여 하 고 Enter 키를 누릅니다.<br/>
```
Set-ExecutionPolicy Bypass
```
<br/>

3. 확인 메시지가 나타나면 **Y**키를 누릅니다.<br/>

4. Windows PowerShell 프롬프트, 형식 또는 복사 및 붙여넣기에는 다음 Enter 키를 누릅니다.<br/>

```
c:\users\MyAlias\desktop\UsersAndGroups.ps1
```
<br/>여기서 *MyAlias* 는 사용자 이름입니다.<br/>

5. 프롬프트가 반환될 때까지 기다렸다가 계속 진행합니다. 먼저 작성된 그룹이 표시되고, 사용자를 추가하면 그룹 목록이 반복적으로 표시됩니다.

## <a name="see-also"></a>참고 항목

[SharePoint Online PowerShell에 연결](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[SharePoint Online 사이트 그룹 Office 365 PowerShell 관리](manage-sharepoint-site-groups-with-powershell.md)

[Office 365 PowerShell 사용한 Office 365 관리](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell 시작](getting-started-with-office-365-powershell.md)

