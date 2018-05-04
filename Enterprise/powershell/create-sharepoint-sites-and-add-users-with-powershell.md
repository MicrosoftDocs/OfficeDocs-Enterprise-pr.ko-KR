---
title: SharePoint Online 사이트를 만들고 Office 365 PowerShell을 사용하여 사용자 추가
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
description: '요약: Office 365 PowerShell을 사용 새 SharePoint Online 사이트를 만들고 다음 해당 사이트에 사용자 및 그룹을 추가 합니다.'
ms.openlocfilehash: 0a0438917f6e7010b56703ce0bf73e89e1db0533
ms.sourcegitcommit: 74cdb2534bce376abc9cf4fef85ff039c46ee790
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="create-sharepoint-online-sites-and-add-users-with-office-365-powershell"></a>SharePoint Online 사이트를 만들고 Office 365 PowerShell을 사용하여 사용자 추가

 **요약:** Office 365 PowerShell을 사용 하 여 새 SharePoint Online 사이트를 만드는 하 고 해당 사이트에 사용자 및 그룹을 추가 합니다.

Office 365 PowerShell을 사용 하 여 SharePoint Online 사이트를 만들고 사용자를 추가 하려면 작업 Office 356 관리 센터에서 수 있는 것 보다 훨씬 더 빠르게 신속 하 고 반복적으로 수행할 수 있습니다. 또한 Office 356 관리 센터에서 수행할 수 없는 작업을 수행할 수 있습니다. 

## <a name="before-you-begin"></a>시작하기 전에

이 항목의 절차에서는 SharePoint Online에 연결 해야 합니다. 자세한 내용은 [Connect to SharePoint Online PowerShell를](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps) 참조 하십시오.

## <a name="step-1-create-new-site-collections-using-office-365-powershell"></a>1 단계: Office 365 PowerShell을 사용 하 여 새 사이트 모음 만들기

Office 365 PowerShell 및 제공 하는 예제 코드 및 메모장을 사용 하 여 만든.csv 파일을 사용 하 여 여러 사이트를 만듭니다. 이 절차에 대 한 사용자의 사이트 및 테 넌 트 관련 정보로 괄호 안에 표시 되는 개체 틀 정보를 교체 합니다. 이 프로세스를 사용 하면 단일 파일을 만들고 해당 파일을 사용 하는 단일 Office 365 PowerShell 명령을 실행할 수 있습니다. 이 반복 및 휴대용 모두를 수행 하는 작업을 만들고 하는 경우 SharePoint Online 관리 셸에 입력 하는 long 명령에서 발생할 수 있는 모든 오류를 여러 명 제거 합니다. 이 절차를 두 부분으로 구성 있습니다. .Csv 파일을 만들 먼저 하 고를 사용 하 여 해당 콘텐츠는 사이트를 만들 Office 365 PowerShell을 사용 하 여 해당.csv 파일을 참조 합니다.

Office 365 PowerShell cmdlet은.csv 파일 가져오고 중괄호 안에 열 머리글로 파일의 첫 줄을 읽고 하는 루프에 파이프 합니다. Office 365 PowerShell cmdlet은 다음 나머지 레코드를 반복, 각 레코드에 대 한 새 사이트 모음을 만들고 열 머리글에 따라 사이트 모음의 속성을 할당 합니다.

###<a name="create-a-csv-file"></a>.csv 파일 만들기

1. 메모장을 열고 다음 텍스트 블록을 붙여 넣습니다.</br>
```
Owner,StorageQuota,Url,ResourceQuota,Template,TimeZoneID,Name
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/TeamSite01,25,EHS#1,10,Contoso Team Site
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/Blog01,25,BLOG#0,10,Contoso Blog
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Project01,25,PROJECTSITE#0,10,Project Alpha
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Community01,25,COMMUNITY#0,10,Community Site
```</br>Where *tenant* is the name of your tenant, and *owner* is the user name of the user on your tenant to whom you want to grant the role of primary site collection administrator.</br>(You can press Ctrl+H when you use Notepad to bulk replace faster.)</br>
2. Save the file on your desktop as **SiteCollections.csv**.

 > [!TIP]
> Before you use this or any other .csv or Windows PowerShell script file, it is good practice to make sure that there are no extraneous or nonprinting characters. Open the file in Word, and in the ribbon, click the paragraph icon to show nonprinting characters. There should be no extraneous nonprinting characters. For example, there should be no paragraph marks beyond the final one at the end of the file.

### Run the Windows PowerShell command

1. At the Windows PowerShell prompt, type or copy and paste the following cmdlet, and press Enter:</br>
```
Csv 가져오기 C:\users\MyAlias\desktop\SiteCollections.csv | ForEach 개체 {새 SPOSite-소유자 $_합니다. 소유자-StorageQuota $_ 합니다. StorageQuota-Url $_합니다. Url NoWait-ResourceQuota $_ 합니다. ResourceQuota-서식 파일 $_합니다. 서식 파일-된 TimeZoneID $_ 합니다. 된 TimeZoneID-$_ 제목입니다. 이름}
```
</br>Where *MyAlias* equals your user alias.</br>
2. Wait for the Windows PowerShell prompt to reappear. It might take a minute or two.</br>
3. At the Windows PowerShell prompt, type or copy and paste the following cmdlet, and press Enter:</br>
```
Get-sposite-자세한 | Format-table-자동 크기 조정
```</br>
4. Note the new site collections in the list. You should see the following site collections: **contosotest**, **TeamSite01**, **Blog01**, and **Project01**.

That’s it. You’ve created multiple site collections using the .csv file you created and a single Windows PowerShell cmdlet. You’re now ready to create and assign users to these sites.

## Step 2: Add users and groups

Now you’re going to create users and add them to a site collection group. You will then use a .csv file to bulk upload new groups and users.

The following procedures assume that you successfully created the site collections contosotest, TeamSite01, Blog01, and Project01.

### Create .csv and .ps1 files

1. Open Notepad, and paste the following text block into it:</br>
```
사이트, 그룹, PermissionLevels https://tenant.sharepoint.com/sites/contosotest, Contoso 프로젝트 책임자, 모든 권한 https://tenant.sharepoint.com/sites/contosotest, Contoso 감사자 보기 전용 https://tenant.sharepoint.com/sites/contosotest, Contoso 디자이너, 디자인 https://tenant.sharepoint.com/sites/TeamSite01, XT1000 팀 리더, 모든 권한 https://tenant.sharepoint.com/sites/TeamSite01, XT1000 상담 편집 https://tenant.sharepoint.com/sites/Blog01, Contoso 블로그 (영문) 디자이너, 디자인 https://tenant.sharepoint.com/sites/Blog01, Contoso 블로그 (영문) 편집자 편집 https://tenant.sharepoint.com/sites/Project01, 알파 승인자 프로젝트, 모든 권한
```
</br>Where *tenant* equals your tenant name.</br>
2. Save the file to your desktop as **GroupsAndPermissions.csv**.</br>
3. Open a new instance of Notepad, and paste the following text block into it:</br>
```
그룹, LoginName, 사이트 Contoso 프로젝트 책임자, username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/contosotest Contoso 감사자, username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/contosotest Contoso 디자이너, username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/contosotest XT1000 팀 리더 username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/TeamSite01 XT1000 문에, username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/TeamSite01 Contoso 블로그 (영문) 디자이너, username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Blog01 Contoso 블로그 (영문) 편집자, username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Blog01 프로젝트 알파 승인자, username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Project01
```
</br>Where *tenant* equals your tenant name, and *username* equals the user name of an existing user.</br>
4. Save the file to your desktop as **Users.csv**.</br>
5. Open a new instance of Notepad, and paste the following text block into it:</br>
```
Csv 가져오기 C:\users\MyAlias\desktop\GroupsAndPermissions.csv | ForEach 개체 {새 SPOSiteGroup-$_를 그룹화 합니다. 그룹-PermissionLevels $_ 합니다. PermissionLevels-$_사이트입니다. 사이트} Import-csv C:\users\MyAlias\desktop\Users.csv | 여기에서 {추가 SPOUser-$ 그룹_합니다. $_– LoginName를 그룹화 합니다. LoginName-$ 사이트_합니다. 사이트}
```
</br>Where MyAlias equals the user name of the user that is currently logged on.</br>
6. Save the file to your desktop as **UsersAndGroups.ps1**. This is a simple Windows PowerShell script.

You’re now ready to run the UsersAndGroup.ps1 script to add users and groups to multiple site collections.

### Run UsersAndGroups.ps1 script

1. Return to the SharePoint Online Management Shell.</br>
2. At the Windows PowerShell prompt, type or copy and paste the following line, and press Enter:</br>
```
Set-executionpolicy 바이패스
```</br>
3. At the confirmation prompt, press **Y**.</br>
4. At the Windows PowerShell prompt, type or copy and paste the following, and press Enter:</br>
```
c:\users\MyAlias\desktop\UsersAndGroups.ps1
```
</br>Where *MyAlias* equals your user name.</br>
5. Wait for the prompt to return before moving on. You will first see the groups appear as they are created. Then you will see the group list repeated as users are added.

## See also

[Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[Manage SharePoint Online site groups Office 365 PowerShell](manage-sharepoint-site-groups-with-powershell.md)

[Manage Office 365 with Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Getting started with Office 365 PowerShell](getting-started-with-office-365-powershell.md)

