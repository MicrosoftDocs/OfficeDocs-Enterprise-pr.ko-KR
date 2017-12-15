---
title: "SharePoint Online 팀 사이트를 격리 관리"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Ent_Solutions
ms.assetid: 79a61003-4905-4ba8-9e8a-16def7add37c
description: "요약: 이러한 절차로 격리 된 SharePoint Online 팀 사이트를 관리 합니다."
ms.openlocfilehash: 516bf9d1c94992789bd8341b347a5788dbb04933
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2017
---
# <a name="manage-an-isolated-sharepoint-online-team-site"></a>SharePoint Online 팀 사이트를 격리 관리

 **요약:** 이러한 절차로 격리 된 SharePoint Online 팀 사이트를 관리 합니다.
  
이 문서에서는 SharePoint Online 팀 사이트를 격리에 대 한 일반적인 관리 작업에 설명 합니다.
  
## <a name="add-a-new-user"></a>새 사용자 추가

새로운 사용자가 사이트에 참가 자신의 사이트에 대 한 참가 수준의 결정 해야 합니다.
  
- 관리: 사이트에 새 사용자 계정 추가 admins 그룹에 액세스
    
- 현재 공동 작업: 사이트에 사용자 계정을 추가 구성원 그룹에 액세스
    
- 보기: 사이트에 사용자 계정을 추가 뷰어 그룹에 액세스
    
사용자 계정 및 그룹을 통해 Windows Server Active Directory (AD)를 관리 하는 경우 보통 Windows Server AD 사용자 및 그룹 관리 절차를 사용 하 여 적절 한 액세스 그룹에 적절 한 사용자를 추가 하 고와 동기화를 기다립니다 프로그램 Office 365 구독 합니다.
  
사용자 계정 및 그룹을 통해 Office 365를 관리 하는 경우에 Office 관리 센터 또는 Microsoft PowerShell을 사용할 수 있습니다.
  
- Office 관리 센터에 대 한 사용자 계정 관리자 또는 회사 관리자 역할 할당 된 사용자 계정을 사용 하 여 로그인 하 고 적절 한 액세스 그룹에 적절 한 사용자를 추가할 그룹을 사용 합니다.
    
- Powershell, 첫번째 [Azure Active Directory V2 PowerShell 모듈을 사용 하 여 연결](https://go.microsoft.com/fwlink/?linkid=842218)합니다. 해당 사용자 계정 이름 (UPN) 액세스 그룹에 사용자 계정을 추가 하려면 다음 PowerShell 명령 블록을 사용 합니다.
    
```
$userUPN="<UPN of the user account>"
$grpName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

> [!TIP]
> 모든 PowerShell 명령 및 Excel을 포함 하는 텍스트 파일에 대 한 PowerShell 명령에서 생성 하는 구성 워크시트에 따라 그룹 및 사용자 계정 이름, [격리 된 SharePoint Online 팀 사이트 배포 키트](https://gallery.technet.microsoft.com/Isolated-SharePoint-Online-0b364907)를 다운로드 합니다. 

표시 이름과 함께 액세스 그룹에 사용자 계정을 추가 하려면 다음 PowerShell 명령 블록을 사용 합니다.

```
$userDisplayName="<display name of the user account>"
$grpName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $userDisplayName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

## <a name="add-a-new-group"></a>새 그룹 추가

전체 그룹에 대 한 액세스를 추가할 사이트에 있는 그룹의 모든 구성원의 참여가의 수준을 결정 해야 합니다.
  
- 관리: 사이트에 그룹을 추가 하 admins 그룹에 액세스
    
- 현재 공동 작업: 사이트에 그룹 추가 구성원 그룹에 액세스
    
- 보기: 사이트에 그룹을 추가 하 뷰어 그룹에 액세스
    
사용자 계정 및 Windows Server AD 통해 그룹을 관리 하는 경우 일반 Windows Server AD 사용자 및 그룹 관리 절차를 사용 하 여 적절 한 그룹에 적절 한 그룹을 추가 하 고 Office 365 구독와의 동기화를 기다립니다.
  
사용자 계정 및 그룹을 통해 Office 365를 관리 하는 경우에 Office 관리 센터 또는 PowerShell을 사용할 수 있습니다.
  
- Office 관리 센터에 대 한 사용자 계정 관리자 또는 회사 관리자 역할 할당 된 사용자 계정을 사용 하 여 로그인 하 고 적절 한 액세스 그룹에 적절 한 그룹을 추가할 그룹을 사용 합니다.
    
- Powershell, 첫번째 [Azure Active Directory V2 PowerShell 모듈을 사용 하 여 연결](https://go.microsoft.com/fwlink/?linkid=842218)합니다. 그런 다음, 다음 PowerShell 명령을 사용 하십시오.
 
```
$newGroupName="<display name of the new group to add>"
$siteGrpName="<display name of the access group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $newGroupName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $siteGrpName }).ObjectID
```

## <a name="remove-a-user"></a>사용자를 제거 합니다.

사이트에서 다른 사용자의 액세스를 제거 해야 하는 경우는 현재 사이트에서 자신의 참가 기반으로 구성원 액세스 그룹에서 제거 있습니다.
  
- 사이트 관리자 액세스 그룹에서 사용자 계정 관리: 제거
    
- 현재 공동 작업: 사이트 구성원 액세스 그룹에서 사용자 계정 제거
    
- 보기: 사이트 뷰어 액세스 그룹에서 사용자 계정 제거
    
사용자 계정 및 Windows Server AD 통해 그룹을 관리 하는 경우 일반 Windows Server AD 사용자 및 그룹 관리 절차를 사용 하 여 적절 한 액세스 그룹에서 적절 한 사용자를 제거 하 고 Office 365와의 동기화를 기다립니다 구독 합니다.
  
사용자 계정 및 그룹을 통해 Office 365를 관리 하는 경우에 Office 관리 센터 또는 PowerShell을 사용할 수 있습니다.
  
- Office 관리 센터에 대 한 사용자 계정 관리자 또는 회사 관리자 역할 할당 된 사용자 계정을 사용 하 여 로그인 하 고 그룹을 사용 하 여 적절 한 액세스 그룹에서 적절 한 사용자를 제거 합니다.
    
- Powershell, 첫번째 [Azure Active Directory V2 PowerShell 모듈을 사용 하 여 연결](https://go.microsoft.com/fwlink/?linkid=842218)합니다. 사용자 계정의 해당 UPN 함께 액세스 그룹에서 제거 하려면 다음 PowerShell 명령 블록을 사용 하 여:
    
```
$userUPN="<UPN of the user account>"
$grpName="<display name of the access group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

표시 이름과 함께 액세스 그룹에서 사용자 계정을 제거 하려면 다음 PowerShell 명령 블록을 사용 하 여:
    
```
$userDisplayName="<display name of the user account>"
$grpName="<display name of the access group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.DisplayName -eq $userDisplayName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

## <a name="remove-a-group"></a>그룹을 제거 합니다.

전체 그룹에 대 한 액세스를 제거 하려면는 현재 사이트에서 자신의 참가 기반으로 구성원 액세스 그룹에서 그룹을 제거 합니다.
  
- 사이트 관리자 액세스 그룹에서 그룹 관리: 제거
    
- 현재 공동 작업: 사이트 구성원 액세스 그룹에서 그룹 제거
    
- 보기: 사이트 뷰어 액세스 그룹에서 그룹 제거
    
사용자 계정 및 Windows Server Active Directory를 통해 그룹을 관리 하는 경우 보통 Windows Server AD 사용자 및 그룹 관리 절차를 사용 하 여 적절 한 액세스 그룹에서 적절 한 그룹을 제거 하 고와 동기화를 기다립니다 프로그램 Office 365 구독 합니다.
  
사용자 계정 및 그룹을 통해 Office 365를 관리 하는 경우에 Office 관리 센터 또는 PowerShell을 사용할 수 있습니다.
  
- Office 관리 센터에 대 한 사용자 계정 관리자 또는 회사 관리자 역할 할당 된 사용자 계정을 사용 하 여 로그인 하 고 적절 한 액세스 그룹에서 적절 한 그룹을 제거 하려면 그룹을 사용 합니다.
    
- Powershell, 첫번째 [Azure Active Directory V2 PowerShell 모듈을 사용 하 여 연결](https://go.microsoft.com/fwlink/?linkid=842218)합니다.    
표시 된 이름을 사용 하는 액세스 그룹에서 그룹을 제거 하려면 다음 PowerShell 명령 블록을 사용 하 여:
    
```
$groupMemberName="<display name of the group to remove>"
$grpName="<display name of the access group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

## <a name="create-a-documents-subfolder-with-custom-permissions"></a>사용자 지정 사용 권한으로 문서 하위 폴더를 만듭니다.

경우에 따라 격리 된 사이트 내에서 근무 하는 사용자의 하위 집합에는 공동 작업을 보다 개인 전체를 해야 합니다. SharePoint Online 사이트에 대 한 사이트의 문서 폴더에 하위 폴더를 만들 수 있으며 사용자 지정 사용 권한을 할당할 키를 누릅니다. 권한 없는는 하위를 표시 되지 않습니다.
  
사용자 지정 사용 권한으로 문서 하위 폴더를 만들려면 다음을 수행 합니다.
  
1. Office 365에는 사이트에 대 한 관리자 액세스 그룹의 구성원 인 계정으로 로그인 합니다. 도움말을 보려면 [Office 365에 로그인 할 위치](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)를 참조 하십시오.
    
2. 격리 된 팀 사이트를 이동 하 고 **문서**를 클릭 합니다.
    
3. 사용자 지정 사용 권한 가진 하위 폴더 포함, 폴더를 만들고 다음 파일을 엽니다 문서 폴더에 폴더를 찾습니다.
    
4. **공유**를 클릭 합니다.
    
5. 클릭 **와 공유 > 고급**합니다.
    
6. **사용 권한 상속 중지**를 클릭 한 다음 **확인**을 클릭 합니다.
    
7. **공유**를 클릭 합니다.
    
8. 클릭 **와 공유 > 고급**합니다.
    
9. 클릭 **사용 권한 부여 >와 공유 > 고급**합니다.
    
10. 사용 권한 페이지에서 다음을 클릭 ** \<사이트 이름 > 목록에서 구성원**합니다.
    
11. 에 ** \<사이트 이름 > 구성원** 페이지, 사이트 구성원 액세스 그룹 옆에 확인 표시가 표시를 선택, **작업**을 클릭, **그룹에서 사용자 제거**를 클릭 한 다음 **확인**을 클릭 합니다.
    
12. 이 하위 폴더에 특정 구성원을 추가 하려면 클릭 **새로 만들기 > 사용자 추가**합니다.
    
13. **공유** 대화 상자에서 파일의 하위 폴더에 대해 공동으로 작업 하 고 **공유**를 클릭 한 다음 수 있는 사용자 계정의 이름을 입력 합니다.
    
14. 새 결과 표시 하려면 웹 페이지를 새로 고쳐 합니다.
    
15. 왼쪽 탐색 영역에서 **그룹** 를 클릭은 ** \<사이트 이름 > 방문자** 그룹화 하 고 필요에 따라 하위 폴더에 파일을 볼 수 있는 사용자 계정 집합을 지정 하려면 11-14 단계를 사용 합니다.
    
16. 왼쪽 탐색 영역에서 **그룹** 를 클릭은 ** \<사이트 이름 > 소유자** 그룹화 하 고 필요에 따라 하위 폴더에 사용 권한을 관리할 수 있는 사용자 계정 집합을 지정 하려면 11-14 단계를 사용 합니다.
    
17. 브라우저에서 **사용자 및 그룹** 탭을 닫습니다.
    
## <a name="see-also"></a>See Also

[격리 된 SharePoint Online 팀 사이트](isolated-sharepoint-online-team-sites.md)
  
[격리 된 SharePoint Online 팀 사이트를 디자인 합니다.](design-an-isolated-sharepoint-online-team-site.md)
  
[보안 솔루션](security-solutions.md)

[SharePoint Online 팀 사이트를 격리를 배포 합니다.](deploy-an-isolated-sharepoint-online-team-site.md)



