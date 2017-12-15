---
title: "SharePoint Online 팀 사이트를 격리를 배포 합니다."
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
ms.assetid: 3033614b-e23b-4f68-9701-f62525eafaab
description: "요약: 새 격리 된 SharePoint Online 팀 사이트가 단계별 지침을 배포 합니다."
ms.openlocfilehash: 9715c6168276b6ba9ffc63591cc6421708bbda27
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2017
---
# <a name="deploy-an-isolated-sharepoint-online-team-site"></a>SharePoint Online 팀 사이트를 격리를 배포 합니다.

 **요약:** 새 격리 된 SharePoint Online 팀 사이트가 단계별 지침을 배포 합니다.
  
이 문서 만들기 (영문) 및 Microsoft Office 365에서 격리 된 SharePoint Online 팀 사이트를 구성 하기 위한 단계별 배포 가이드는. 이러한 단계 세 기본 SharePoint 그룹 및 각 액세스 수준에 대 한 단일 Azure Active Directory 기반 액세스 그룹과 해당 사용 권한 수준을 사용 한다고 가정 합니다.
  
## <a name="phase-1-create-and-populate-the-team-site-access-groups"></a>1 단계: 만들기 및 팀 사이트 액세스 그룹 채우기

이 단계에서 세개의 기본 SharePoint 그룹에 대 한 세 Azure AD 기반 액세스 그룹 만들고 적절 한 사용자 계정으로 채울 합니다.
  
> [!NOTE]
> 다음 단계는 모든 필요한 사용자 계정이 이미 존재 하 고 적절 한 라이선스를 할당 된 가정 합니다. 그렇지 않은 경우 추가 하 고 1 단계를 진행 하기 전에 라이선스를 할당 합니다. 
  
### <a name="step-1-list-the-sharepoint-online-admins-for-the-site"></a>1 단계: 사이트에 대 한 SharePoint Online 관리자를 나열 합니다.

사용자 집합에 해당 하는 격리 된 팀 사이트에 대 한 SharePoint Online 관리자 계정을 결정 합니다.
  
사용자 계정 및 그룹을 통해 Office 365를 관리 하는 Windows PowerShell을 사용 하려고 하는 경우 해당 사용자의 목록을 Upn (이름)를 만듭니다 (UPN 예제: belindan@contoso.com).
  
### <a name="step-2-list-the-members-for-the-site"></a>2 단계: 사이트에 대 한 멤버를 나열 합니다.

사용자 계정에 해당 하는 공동 작업 사이트 내에 저장 된 리소스에 받는 사람이 격리 된 팀 사이트에 대 한 구성원의 집합을 결정 합니다.
  
사용자 계정 및 그룹을 통해 Office 365를 관리 하는 PowerShell을 사용 하 여 원하는 하는 경우에 해당 Upn 목록이 확인 합니다. 사이트 구성원의 많은 경우 텍스트 파일에 Upn 목록이 저장 하 고 단일 PowerShell 명령을 사용 하 여 모든 추가할 수 있습니다.
  
### <a name="step-3-list-the-viewers-for-the-site"></a>3 단계: 사이트에 대 한 뷰어를 나열 합니다.

받는 사람이 수 없는 사이트에 저장 된 리소스를 보려면 하지만 하지 수정 하거나의 내용에 직접 공동 작업 격리 된 팀 사이트의 사용자에 게 해당 사용자 계정의 집합을 결정 합니다.
  
사용자 계정 및 그룹을 통해 Office 365를 관리 하는 PowerShell을 사용 하 여 원하는 하는 경우에 해당 Upn 목록이 확인 합니다. 사이트 구성원의 많은 경우 텍스트 파일에 Upn 목록이 저장 하 고 단일 PowerShell 명령을 사용 하 여 모든 추가할 수 있습니다.
  
사이트에 대 한 뷰어 경영진, 법적 자문 위원 또는 inter-departmental 이해 관계자 포함 될 수 있습니다.
  
### <a name="step-4-create-the-three-access-groups-for-the-site-in-azure-ad"></a>4 단계: Azure AD에서 해당 사이트에 대 한 세 액세스 그룹 만들기

Azure AD에서 다음과 같은 액세스 그룹을 만들 해야 합니다.
  
- (1 단계에서 목록 포함)이 표시 된 사이트 관리자
    
- (2 단계에서 목록 포함)이 표시 된 사이트 구성원
    
- (3 단계에서 목록 포함)이 표시 된 사이트 뷰어
    
1. 브라우저에서 [https://portal.azure.com](https://portal.azure.com) 에서 Azure 포털로 이동 하 고 사용자 관리 관리자 또는 회사 관리자 역할을 가진 할당 된 계정의 자격 증명을 사용 하 여 로그인 합니다.
    
2. Azure 포털에서 클릭 **Azure Active Directory > 사용자 및 그룹 > 모든 그룹**합니다.
    
3. **모든 그룹** 블레이드에서 **+ 새 그룹을**클릭 합니다.
    
4. **그룹** 블레이드에서:
    
  - **이름**에 그룹 이름을 입력 합니다.
    
  - **멤버 자격**에서 **할당** 을 선택 합니다.
    
  - **Office를 사용 하도록 설정 기능**에 대 한 **예** 를 클릭 합니다.
    
5. **만들기**클릭 한 다음 **그룹** 블레이드를 닫습니다.
    
6. 추가 그룹에 대해 3-5 단계를 반복 합니다.
    
> [!NOTE]
> 사용 하도록 설정 하는 Office 기능을가지고 있습니다. 그룹을 만들 수는 Azure 포털을 사용 해야 합니다. SharePoint Online 격리 된 사이트는 나중에 사용 하도록 구성 파일을 암호화 하 고 특정 그룹에 권한 할당을 Azure 정보 보호 (AIP) 레이블이 있는 기밀 사항이 사이트로 허용 된 그룹 만들어져 있어야 Office 기능 사용할 수 있습니다. 가 만들어진 후 Azure AD 그룹의 Office 기능 설정을 변경할 수 없습니다. 
  
세 개 사이트 액세스 그룹과 결과 구성에는 다음과 같습니다.
  
![격리된 SharePoint Online 사이트 배포용 세 개의 액세스 그룹입니다.](images/c2557f61-478b-4494-95e9-d79fe5909e8b.png)
  
### <a name="step-5-add-the-user-accounts-to-the-access-groups"></a>5 단계입니다. Access 그룹에 사용자 계정 추가

이 단계에서 다음을 수행 합니다.
  
1. 사이트 관리자 액세스 그룹을 1 단계에서 사용자의 목록 추가
    
2. 사이트 구성원 액세스 그룹에 2 단계에서 사용자의 목록 추가
    
3. 사이트 뷰어 액세스 그룹에 3 단계에서 사용자의 목록 추가
    
사용자 계정 및 Windows Server AD 통해 그룹을 관리 하는 경우 일반 Windows Server AD 사용자 및 그룹 관리 절차를 사용 하 여 적절 한 액세스 그룹에 사용자를 추가 하 고 Office 365 구독와의 동기화를 기다립니다.
  
사용자 계정 및 그룹을 통해 Office 365를 관리 하는 경우에 Office 관리 센터 또는 PowerShell을 사용할 수 있습니다. 액세스 그룹 중 하나에 대 한 중복 그룹 이름이 Office 관리 센터를 사용 해야 합니다.
  
Office 관리 센터에 대 한 사용자 계정 관리자 또는 회사 관리자 역할 할당 된 사용자 계정을 사용 하 여 로그인 하 고 적절 한 사용자 계정을 추가 하려면 그룹 및 그룹을 적절 한 액세스 그룹을 사용 합니다.
  
Powershell, 첫번째 [Azure Active Directory V2 PowerShell 모듈을 사용 하 여 연결](https://go.microsoft.com/fwlink/?linkid=842218)합니다.
  
다음으로, 다음 명령은 블록을 사용 하 여 access 그룹에 개별 사용자 계정을 추가 하려면:
  
```
$userUPN="<UPN of the user account>"
$grpName="<display name of the access group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

> [!TIP]
> 모든 PowerShell 명령 및 Excel을 포함 하는 텍스트 파일에 대 한 PowerShell 명령에서 생성 하는 구성 워크시트에 따라 그룹 및 사용자 계정 이름, [격리 된 SharePoint Online 팀 사이트 배포 키트](https://gallery.technet.microsoft.com/Isolated-SharePoint-Online-0b364907)를 다운로드 합니다. 
  
텍스트 파일에 대 한 액세스 그룹 중 하나에 대 한 사용자 계정의 Upn을 저장 하는 경우에 한번에 추가 합니다 다음 PowerShell 명령 블록을 사용할 수 있습니다.
  
```
$grpName="<display name of the access group>"
$fileName="<path and name of the file containing the list of account UPNs>"
$grpID=(Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
Get-Content $fileName | ForEach { $userUPN=$_; Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID $grpID }
```

PowerShell에 대 한 다음 명령 블록을 사용 하 여 access 그룹에 개별 그룹을 추가 하려면:
  
```
$nestedGrpName="<display name of the group to add to the access group>"
$grpName="<display name of the access group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $nestedGrpName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID

```

결과 다음과 같은 있어야 합니다.
  
- 사이트 관리자 사용자 계정 또는 그룹을 포함 하는 사이트 관리자 Azure AD 그룹
    
- 사이트 구성원 사용자 계정 또는 그룹을 포함 하는 사이트 구성원 Azure AD 그룹
    
- 사용자 계정 또는 사이트 콘텐츠를 볼 수만 있는 그룹을 포함 하는 사이트 Azure AD viewers 그룹
    
각 액세스 그룹 Office 관리 센터 또는 다음 PowerShell 명령 블록에 대 한 그룹 구성원의 목록을 유효성을 검사 합니다.
  
```
$grpName="<display name of the access group>"
Get-AzureADGroupMember -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID | Sort UserPrincipalName | Select UserPrincipalName,DisplayName,UserType
```

사용자 계정 또는 그룹으로 채워진 세 사이트 액세스 그룹과 결과 구성에는 다음과 같습니다.
  
![세 개의 액세스 그룹은 사용자 계정으로 채워집니다.](images/2320107c-dad6-4c8f-94e5-f6427c125e71.png)
  
## <a name="phase-2-create-and-configure-the-isolated-team-site"></a>2 단계: 만들기 및 격리 된 팀 사이트 구성

이 단계에서 격리 된 SharePoint Online 사이트 만들고 새 Azure AD 기반 액세스 그룹을 사용 하 여 기본 SharePoint Online 사용 권한 수준에 대 한 사용 권한을 구성 합니다.
  
먼저, 다음이 단계와 SharePoint Online 팀 사이트를 만듭니다.
  
1. SharePoint Online 팀 사이트 (SharePoint Online 관리자)를 관리 하는데 사용 되는 계정 사용 하 여 Office 365 포털에 로그인 합니다. 도움말을 보려면 [Office 365에 로그인 할 위치](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)를 참조 하십시오.
    
2. 타일의 목록에서 **SharePoint**를 클릭 합니다.
    
3. 브라우저의 새 **SharePoint** 탭에서 **+ 사이트 만들기를**클릭 합니다.
    
4. **사이트 만들기** 페이지에서 **팀 사이트**를 클릭 합니다.
    
5. **사이트 이름**팀 사이트에 대 한 이름을 입력 합니다. 
    
6. **팀 사이트 설명** 에 사이트의 용도 대 한 선택적 설명을 입력 합니다.
    
7. **개인정보 보호 설정**선택 **개인-이 사이트에 액세스할 수 있는 구성원만**, **다음**을 클릭 하 고 있습니다.
    
8. 에 **가 수행 하려는 추가?** 창 **마침**을 클릭 합니다.
    
다음으로 새 SharePoint Online 팀 사이트에서 사용 권한을 구성 합니다.
  
1. 도구 모음에서 설정 아이콘을 클릭 한 다음 **사이트 사용 권한**을 클릭 합니다.
    
2. **사이트 사용 권한** 창에서 **고급 사용 권한 설정**을 클릭 합니다.
    
3. 브라우저의 새 **사용 권한** 탭에서 **액세스 요청 설정**을 클릭 합니다.
    
4. **액세스 요청 설정** 대화 상자에서의 선택을 취소 **허용 액세스 요청** 및 **사이트 및 개별 파일 및 폴더 공유 허용 구성원** (되도록 세 확인란을 모두 선택 취소)를 한 다음 **확인**을 클릭 합니다.
    
5. 브라우저의 **사용 권한** 탭을 클릭 ** \<사이트 이름 > 구성원** 목록에 있습니다.
    
6. **사용자 및 그룹에서** **새로 만들기**를 클릭 합니다.
    
7. **공유** 대화 상자에서 사이트 구성원 액세스 그룹의 이름을 입력을 선택한 다음 **공유**를 클릭 합니다.
    
8. 브라우저에서 뒤로 단추를 클릭합니다.
    
9. 클릭 ** \<사이트 이름 > 소유자** 목록에 있습니다.
    
10. **사용자 및 그룹에서** **새로 만들기**를 클릭 합니다.
    
11. **공유** 대화 상자에서 사이트 관리자 액세스 그룹의 이름을 입력을 선택한 다음 **공유**를 클릭 합니다.
    
12. 브라우저에서 뒤로 단추를 클릭합니다.
    
13. 클릭 ** \<사이트 이름 > 방문자** 목록에 있습니다.
    
14. **사용자 및 그룹에서** **새로 만들기**를 클릭 합니다.
    
15. **공유** 대화 상자에서 사이트 뷰어 액세스 그룹의 이름을 입력을 선택한 다음 **공유**를 클릭 합니다.
    
16. 브라우저의 **사용 권한** 탭을 닫습니다.
    
이러한 사용 권한 설정의 결과:
  
- ** \<사이트 이름 > 소유자** SharePoint 그룹의 모든 구성원, **모든 권한** 권한 수준을 가진 사이트 관리자 액세스 그룹을 포함 합니다.
    
- ** \<사이트 이름 > 구성원** SharePoint 그룹 모두에는 구성원에 게 사용 권한 수준 **편집** 사이트 구성원 액세스 그룹을 포함 합니다.
    
- ** \<사이트 이름 > 방문자** SharePoint 그룹 모든 구성원에 **읽기** 권한 수준을 가진 사이트 뷰어 액세스 그룹을 포함 합니다.
    
- 다른 구성원을 초대 하는 구성원에 대 한 또는 비-구성원 액세스 요청에 대 한 기능을 사용 하는 사용할 수 없습니다.
    
사용자 계정으로 입력 되는 세가지 액세스 그룹이 나 Azure AD 그룹을 사용 하도록 구성 된 사이트에 대 한 세 SharePoint 그룹과 결과 구성에는 다음과 같습니다.
  
![액세스 그룹 및 사용자 계정이 있는 격리된 SharePoint Online 사이트의 최종 구성입니다.](images/e7618971-06ab-447b-90ff-d8be3790fe63.png)
  
및 액세스 그룹 중 하나에서 그룹 구성원 자격을 통해 사이트의 구성원 수 이제 공동 작업 사이트의 리소스를 사용 하 여 합니다.
  
## <a name="next-step"></a>다음 단계

사이트 액세스 그룹 구성원 자격을 변경 하거나 사용자 지정 사용 권한으로 문서 폴더를 만들어 해야하는 경우 [Manage SharePoint Online 팀 사이트를 격리](manage-an-isolated-sharepoint-online-team-site.md)를 참조 합니다.
  
## <a name="see-also"></a>See Also

[격리 된 SharePoint Online 팀 사이트](isolated-sharepoint-online-team-sites.md)
  
[격리 된 SharePoint Online 팀 사이트를 디자인 합니다.](design-an-isolated-sharepoint-online-team-site.md)
  
[SharePoint Online 팀 사이트를 격리 관리](manage-an-isolated-sharepoint-online-team-site.md)
  
[보안 솔루션](security-solutions.md)



