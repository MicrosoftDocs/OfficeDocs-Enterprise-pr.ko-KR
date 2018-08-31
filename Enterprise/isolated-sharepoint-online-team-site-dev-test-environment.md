---
title: 개발/테스트 환경에서 격리된 SharePoint Online 팀 사이트
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: d1795031-beef-49ea-a6fc-5da5450d320d
description: '요약: Office 365 개발/테스트 환경에서 조직의 나머지 부분에서 격리 된 SharePoint Online 팀 사이트를 구성 합니다.'
ms.openlocfilehash: d2a75f3a3a410116c454892c9ecf3747fb3da53d
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915053"
---
# <a name="isolated-sharepoint-online-team-site-devtest-environment"></a>개발/테스트 환경에서 격리된 SharePoint Online 팀 사이트

 **요약:** Office 365 개발/테스트 환경에서 조직의 나머지 부분에서 분리 되는 SharePoint Online 팀 사이트를 구성 합니다.
  
Office 365의 SharePoint Online 팀 사이트는 일반적인 문서 라이브러리, OneNote 전자 필기장 및 기타 서비스를 사용 하 여 공동 작업에 대 한 위치입니다. 대부분의 경우에서 원하는 전체 액세스 및 공동 작업 부서 또는 조직 전체에서 합니다. 그러나 일부 경우에 조밀 하 게 제어 하려는 액세스 및 공동 작업이 용이해 집니다 소규모 사용자에 대 한 사용 권한입니다.
  
SharePoint Online 팀 사이트 및 사용자가 수행할 수 있는 작업에 대 한 액세스는 SharePoint 그룹 및 권한 수준을 통해 제어 됩니다. 기본적으로 SharePoint Online 사이트에 있는 세가지 수준의 액세스:
  
- **구성원**: 사이트의 리소스를 보고, 만들고, 수정할 수 있습니다.
    
- **소유자**: 권한 변경 기능을 비롯하여 사이트를 완전히 제어할 수 있습니다.
    
- **방문자**: 사이트의 리소스를 볼 수만 있습니다.
    
이 문서의 단계 ProjectX 라는 비밀 리서치 프로젝트에 대해 격리 된 SharePoint Online 팀 사이트의 구성을 안내 합니다. 액세스 요구 사항을합니다.
  
- 프로젝트의 구성원만 사이트 및 해당 콘텐츠(문서, OneNote 전자 필기장, 페이지)에 액세스할 수 있고, SharePoint 편집 및 보기 권한 수준은 그룹 구성원 자격을 통해 제어됩니다.
    
- 사이트의 사이트 작성자 및 관리자 그룹의 구성원만 사이트 수준 권한 수정을 비롯한 사이트 관리 작업을 수행할 수 있습니다.
    
Office 365 개발/테스트 환경에서 격리 된 SharePoint Online 팀 사이트를 설정 하는 세 단계로 가지가 있습니다.
  
1. Office 365 개발/테스트 환경을 만듭니다.

    
2. ProjectX에 대한 사용자 및 그룹을 만듭니다.
    
3. 새 ProjectX SharePoint Online 팀 사이트를 만들고 발견 하면 격리 합니다.
    
> [!TIP]
> [여기](http://aka.ms/catlgstack)를 클릭하여 One Microsoft 클라우드 테스트 랩 가이드 스택의 모든 문서에 대한 가상 맵을 확인할 수 있습니다.
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>1단계: 경량 또는 시뮬레이트된 엔터프라이즈 Office 365 개발/테스트 환경을 구축합니다.

최소 요구 사항을 경량 방식으로 격리 된 SharePoint Online 팀 사이트를 만들 하려면 2와 [Office 365 개발/테스트 환경](office-365-dev-test-environment.md)의 3 단계에서 지침을 따릅니다.
  
시뮬레이션 된 엔터프라이즈 구성에서 격리 된 SharePoint Online 팀 사이트를 만들려는 경우 [Office 365 개발/테스트 환경에 대 한 디렉터리 동기화](dirsync-for-your-office-365-dev-test-environment.md)의 지시를 따릅니다.
  
> [!NOTE]
> 격리된 SharePoint Online 사이트를 만들기 위해 시뮬레이트된 엔터프라이즈 개발/테스트 환경이 필요하지 않습니다. 해당 환경에는 Windows Server AD 포리스트의 디렉터리 동기화 및 인터넷에 연결된 시뮬레이트된 인트라넷이 포함되어 있습니다. 여기서는 옵션으로 제공되므로 격리된 SharePoint Online 사이트를 테스트하고 일반적인 조직을 나타내는 환경에서 실험할 수 있습니다. 
  
## <a name="phase-2-create-user-accounts-and-access-groups"></a>2 단계: 사용자 계정 만들기 및 그룹에 액세스

[Office 365 PowerShell 연결](https://technet.microsoft.com/library/dn975125.aspx) 지침을 사용 하 여 Office 365 내역 구독에서 전역 관리자 계정으로 연결할 수 있습니다:
  
- 사용하는 컴퓨터(경량 Office 365 개발/테스트 환경)
    
- CLIENT1 가상 컴퓨터(시뮬레이트된 엔터프라이즈 Office 365 개발/테스트 환경)
    
ProjectX SharePoint Online 팀 사이트에 대 한 새 액세스 그룹을 만들려면 Windows Azure Active Directory 모듈에 대 한 Windows PowerShell 프롬프트에서 다음이 명령을 실행 합니다.
  
```
$groupName="ProjectX-Members"
$groupDesc="People allowed to collaborate for ProjectX."
New-MsolGroup -DisplayName $groupName -Description $groupDesc
$groupName="ProjectX-Admins"
$groupDesc="People allowed to administer SharePoint for ProjectX."
New-MsolGroup -DisplayName $groupName -Description $groupDesc
$groupName="ProjectX-Viewers"
$groupDesc="People allowed to view the SharePoint resources for ProjectX."
New-MsolGroup -DisplayName $groupName -Description $groupDesc
```

> [!TIP]
> 클릭 [여기](https://gallery.technet.microsoft.com/PowerShell-commands-for-an-b2608df1) 모든이 문서의 PowerShell 명령을 포함 하는 텍스트 파일에 대 한 합니다.
  
조직 이름(예: contosotoycompany), 위치에 대한 2자리 국가 코드를 입력한 후 Windows PowerShell 프롬프트에 대한 Microsoft Azure Active Directory 모듈에서 다음 명령을 실행합니다.
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "designer@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "Lead Designer" -FirstName Lead -LastName Designer -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment -ForceChangePassword $false
```

**New-MsolUser** 명령 표시에서 Lead Designer 계정에 대해 생성된 암호를 적어둔 후 안전한 위치에 보관합니다.
  
Windows PowerShell 프롬프트에 대한 Microsoft Azure Active Directory 모듈에서 다음 명령을 실행합니다.
  
```
$userName= "researcher@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "Lead Researcher" -FirstName Lead -LastName Researcher -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment -ForceChangePassword $false
```

**New-MsolUser** 명령 표시에서 Lead Researcher 계정에 대해 생성된 암호를 적어둔 후 안전한 위치에 보관합니다.
  
Windows PowerShell 프롬프트에 대한 Microsoft Azure Active Directory 모듈에서 다음 명령을 실행합니다.
  
```
$userName= "devvp@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "Development VP" -FirstName Development -LastName VP -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment -ForceChangePassword $false
```

**New-MsolUser** 명령 표시에서 Development VP 계정에 대해 생성된 암호를 적어둔 후 안전한 위치에 보관합니다.
  
다음으로 새 액세스 그룹에 새 계정을 추가 하려면 Windows Azure Active Directory 모듈에 대 한 Windows PowerShell 프롬프트에서 다음 PowerShell 명령을 실행 합니다.
  
```
$grpName="ProjectX-Members"
$userUPN="designer@" + $orgName + ".onmicrosoft.com"
Add-MsolGroupMember -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $grpName }).ObjectID -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupMemberType "User"
$userUPN="researcher@" + $orgName + ".onmicrosoft.com"
Add-MsolGroupMember -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $grpName }).ObjectID -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupMemberType "User"
$grpName="ProjectX-Admins"
Add-MsolGroupMember -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $grpName }).ObjectID -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userCredential.UserName }).ObjectID -GroupMemberType "User"
$grpName="ProjectX-Viewers"
$userUPN="devvp@" + $orgName + ".onmicrosoft.com"
Add-MsolGroupMember -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $grpName }).ObjectID -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupMemberType "User"
```

결과:
  
- ProjectX 멤버 액세스 그룹에는 포함 디자이너 잠재 고객 및 잠재 고객 연구원 사용자 계정
    
- ProjectX 관리자 액세스 그룹 평가판 구독에 대 한 전역 관리자 계정이 포함
    
- ProjectX 뷰어 액세스 그룹에는 포함 개발 VP 사용자 계정
    
그림 1 액세스 그룹 및 그룹 구성원을 표시합니다.
  
**그림 1**

![Office 365 그룹 및 격리된 SharePoint Online 그룹 사이트에 대한 멤버 자격](media/5b7373b9-2a80-4880-afe5-63ffb17237e6.png)
  
## <a name="phase-3-create-a-new-projectx-sharepoint-online-team-site-and-isolate-it"></a>3 단계: 새 ProjectX SharePoint Online 팀 사이트를 만들고 발견 하면 격리

ProjectX에 대 한 SharePoint Online 팀 사이트를 만들려면 다음을 수행 합니다.
  
1. 브라우저를 사용 하는 중 하나에서 로컬 컴퓨터 (경량 구성) 또는 CLIENT1 (시뮬레이션 된 엔터프라이즈 구성) Office 365 포털에 로그인 ([https://portal.office.com](https://portal.office.com)) 전역 관리자 계정을 사용 하 여 합니다.
    
2. 타일 목록에서 **SharePoint**를 클릭합니다.
    
3. 브라우저의 새 SharePoint 탭에서 **+ 사이트 만들기**를 클릭합니다.
    
4. **팀 사이트 이름** **ProjectX**를 입력 합니다. **개인 설정**선택 **개인-이 사이트에 액세스할 수 있는 구성원만**합니다.
    
5. **팀 사이트 설명**에서 **ProjectX에 대한 SharePoint 사이트**를 입력하고 **다음**을 클릭합니다.
    
6. **가 수행 하려는 추가**에서? 창 **마침**을 클릭 합니다.
    
7. 브라우저의 새 **ProjectX-Home** 탭에 있는 도구 모음에서 설정 아이콘을 클릭한 다음 **사이트 권한**을 클릭합니다.
    
8. **사이트 권한** 창에서 **고급 권한 설정**을 클릭합니다.
    
9. 브라우저의 새 **사용 권한: Project X** 탭에서 **액세스 요청 설정**을 클릭합니다.
    
10. **액세스 요청 설정** 대화 상자에서 **구성원이 사이트와 개별 파일 및 폴더를 공유할 수 있도록 허용합니다.** 및 **액세스 요청 허용**(3개의 확인란이 모두 선택 취소됨)을 선택 취소하고 **확인**을 클릭합니다.
    
11. 목록에서 **ProjectX Members**를 클릭합니다.
    
12. **사용자 및 그룹** 페이지에서 **새로 만들기**를 클릭합니다.
    
13. **공유** 대화 상자에 **ProjectX-Members**를 입력하고 **공유**를 클릭합니다.
    
14. 브라우저에서 뒤로 단추를 클릭합니다.
    
15. 목록에서 **ProjectX Owners**를 클릭합니다.
    
16. **사용자 및 그룹** 페이지에서 **새로 만들기**를 클릭합니다.
    
17. **공유** 대화 상자에 **ProjectX-Admins**를 입력하고 **공유**를 클릭합니다.
    
18. 브라우저에서 뒤로 단추를 클릭합니다.
    
19. 목록에서 **ProjectX Visitors**를 클릭합니다.
    
20. **사용자 및 그룹** 페이지에서 **새로 만들기**를 클릭합니다.
    
21. **공유** 대화 상자에 **ProjectX-Viewers**를 입력하고 **공유**를 클릭합니다.
    
22. 브라우저에서 **사용자 및 그룹** 탭을 닫고 브라우저에서 **ProjectX-Home**을 클릭한 다음 **사이트 권한** 창을 닫습니다.

    
권한 구성의 결과는 다음과 같습니다.
  
- ProjectX Members SharePoint 그룹 (포함 하는 디자이너 잠재 고객 및 잠재 고객 연구원 사용자 계정만) ProjectX 구성원 액세스 그룹만 및 (포함 하는 전역 관리자 사용자 계정이) ProjectX 그룹을 포함 합니다.
    
- ProjectX Owners SharePoint 그룹 (포함 하는 전역 관리자 사용자 계정이) ProjectX 관리자 액세스 그룹만 포함 합니다.
    
- ProjectX 방문자 SharePoint 그룹 (포함 하는 개발 VP 사용자 계정만) ProjectX 뷰어 액세스 그룹만 포함 합니다.
    
- 구성원은 사이트 수준 권한을 수정할 수 없습니다(이 작업은 ProjectX-Admins 그룹의 구성원만 수행할 수 있음).
    
- 다른 사용자 계정은 사이트나 해당 리소스에 액세스할 수 없고 사이트에 대한 액세스를 요청할 수 없습니다.
    
그림 2는 SharePoint 그룹 및 해당 그룹 구성원을 보여 줍니다.
  
**그림 2**

![SharePoint Online 그룹 및 격리된 SharePoint Online 그룹 사이트에 대한 멤버 자격](media/595abff4-64f9-49de-a37a-c70c6856936b.png)
  
이제 잠재 고객 디자이너 사용자 계정을 사용 하 여 액세스를 살펴보겠습니다.
  
1. 브라우저에서 **ProjectX-Home** 탭을 닫은 후 브라우저에서 **Microsoft Office 홈** 탭을 클릭합니다.
    
2. 전역 관리자의 이름을 클릭한 다음 **로그아웃**을 클릭합니다.
    
3. Office 365 포털에 로그인 ([https://portal.office.com](https://portal.office.com)) 디자이너 잠재 고객 계정 이름과 암호를 사용 하 여 합니다.
    
4. 타일 목록에서 **SharePoint**를 클릭합니다.
    
5. 브라우저에서 새 **SharePoint** 탭에서 검색 상자에 **ProjectX** 를 입력 하 고 검색을 활성화 한 다음 **ProjectX** 팀 사이트를 클릭 합니다. ProjectX 팀 사이트에 대 한 브라우저에서 새 탭이 표시 됩니다.
    
6. 설정 아이콘을 선택합니다. **사이트 권한**에 대한 옵션은 없습니다. 즉, ProjectX-Admins 그룹의 구성원만 사이트에서 사용 권한을 수정할 수 있기 때문입니다.
    
7. 메모장 또는 원하는 텍스트 편집기를 엽니다.
    
8. ProjectX 팀 사이트의 URL을 복사 하 고 메모장 이나 텍스트 편집기에서 새 줄에 붙여넣습니다.
    
9. 브라우저의 새 **ProjectX-Home** 탭에서 **문서**를 클릭합니다.
    
10. ProjectX 문서 폴더 URL을 복사한 후 메모장이나 텍스트 편집기에서 새 줄에 붙여 넣습니다.
    
11. 브라우저의 새 **ProjectX-Documents** 탭에서 **새로 만들기 > Word 문서**를 클릭합니다.
    
12. **Word Online** 페이지에서 일부 텍스트를 입력하고, 상태가 **저장됨**이 될 때까지 기다린 후 브라우저에서 뒤로 단추를 클릭하고 페이지를 새로 고칩니다. **문서** 폴더에는 새 **Document.docx**가 표시됩니다.
    
13. **Document.docx** 문서에 대해 줄임표를 클릭하고 **링크 가져오기**를 클릭합니다.
    
14. **'Document.docx' 공유** 대화 상자에서 URL을 복사 하 고 메모장 이나 다른 텍스트 편집기에서 새 줄에 붙여 **'Document.docx' 공유** 대화 상자를 닫습니다.
    
15. 브라우저에서 **ProjectX-Documents** 및 **SharePoint** 탭을 닫은 후 **Microsoft Office 홈** 탭을 클릭합니다.
    
16. **Lead Designer** 이름을 클릭하고 **로그아웃**을 클릭합니다.

    
이제 개발 VP 사용자 계정을 사용 하 여 액세스를 살펴보겠습니다.
  
1. Office 365 포털에 로그인 ([https://portal.office.com](https://portal.office.com)) 개발 VP 계정 이름과 암호를 사용 하 여 합니다.
    
2. 타일 목록에서 **SharePoint**를 클릭합니다.
    
3. 브라우저에서 새 **SharePoint** 탭에서 검색 상자에 **ProjectX** 를 입력 하 고 검색을 활성화 한 다음 **ProjectX** 팀 사이트를 클릭 합니다. ProjectX 팀 사이트에 대 한 브라우저에서 새 탭이 표시 됩니다.
    
4. **문서**를 클릭하고 **Document.docx** 파일을 클릭합니다.
    
5. 브라우저의 **Document.docx** 탭에서 텍스트를 수정해 봅니다. **이 문서는 읽기 전용입니다.** 라는 메시지가 표시됩니다. Development VP 사용자 계정에는 사이트에 대한 보기 권한만 있기 때문입니다.
    
6. 브라우저에서 **Document.docx**, **ProjectX-Documents** 및 **SharePoint** 탭을 닫습니다.
    
7. **Microsoft Office 홈** 탭을 클릭하고 **Development VP** 이름을 클릭한 후 **로그아웃**을 클릭합니다.

    
이제 없는 사용 권한이 있는 사용자 계정 사용 하 여 액세스를 살펴보겠습니다.
  
1. Office 365 포털에 로그인 ([https://portal.office.com](https://portal.office.com)) 사용자 3 계정 이름과 암호를 사용 하 여 합니다.
    
2. 타일 목록에서 **SharePoint**를 클릭합니다.
    
3. 	브라우저의 새 **SharePoint** 탭에서 검색 상자에 **ProjectX**를 입력하고 검색을 활성화합니다. **여기에는 검색에 일치하는 항목이 없습니다.** 메시지가 표시됩니다.
    
4. 열려 있는 메모장 또는 텍스트 편집기 인스턴스에서 ProjectX 사이트의 URL을 브라우저의 주소 표시줄에 복사하고 **Enter** 키를 누릅니다. **액세스가 거부되었습니다.** 페이지가 표시됩니다.
    
5. 메모장 또는 텍스트 편집기에서 ProjectX Documents 폴더의 URL을 브라우저의 주소 표시줄에 복사하고 **Enter** 키를 누릅니다. **액세스가 거부되었습니다.** 페이지가 표시됩니다.
    
6. 메모장 또는 텍스트 편집기에서 Documents.docx 파일의 URL을 브라우저의 주소 표시줄에 복사하고 **Enter** 키를 누릅니다. **액세스가 거부되었습니다.** 페이지가 표시됩니다.
    
7. 브라우저에서 **SharePoint** 탭을 닫고 **Microsoft Office 홈** 탭을 클릭한 후 **사용자 3** 이름을 클릭하고 **로그아웃**을 클릭합니다.

    
격리 된 SharePoint Online 사이트 추가 테스트를 수행할 준비가 되었습니다.
  
## <a name="next-step"></a>다음 단계

프로덕션 환경에 격리된 SharePoint Online 팀 사이트를 배포할 준비가 되면 [격리된 SharePoint Online 팀 사이트 디자인](design-an-isolated-sharepoint-online-team-site.md)에서 단계별 디자인 고려 사항을 참조하세요.
  
## <a name="see-also"></a>참고 항목

[격리된 SharePoint Online 팀 사이트](isolated-sharepoint-online-team-sites.md)
  
[클라우드 도입 TLG(테스트 랩 가이드)](cloud-adoption-test-lab-guides-tlgs.md)
  
[기본 구성 개발/테스트 환경](base-configuration-dev-test-environment.md)
  
[Office 365 개발/테스트 환경](office-365-dev-test-environment.md)
  
[클라우드 도입 및 하이브리드 솔루션](cloud-adoption-and-hybrid-solutions.md)




