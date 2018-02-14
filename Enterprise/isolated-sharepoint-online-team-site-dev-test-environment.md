---
title: "격리 된 SharePoint Online 팀 사이트 개발/테스트 환경"
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
description: "요약: Office 365 개발/테스트 환경에서 조직의 나머지 부분에서 격리 된 SharePoint Online 팀 사이트를 구성 합니다."
ms.openlocfilehash: c6115e48f1b2453aaf173b384a30c1cc34ce7b5a
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2018
---
# <a name="isolated-sharepoint-online-team-site-devtest-environment"></a>격리 된 SharePoint Online 팀 사이트 개발/테스트 환경

 **요약:** Office 365 개발/테스트 환경에서 조직의 나머지 부분에서 분리 되는 SharePoint Online 팀 사이트를 구성 합니다.
  
Office 365의 SharePoint Online 팀 사이트는 일반적인 문서 라이브러리, OneNote 전자 필기장 및 기타 서비스를 사용 하 여 공동 작업에 대 한 위치입니다. 대부분의 경우에서 원하는 전체 액세스 및 공동 작업 부서 또는 조직 전체에서 합니다. 그러나 일부 경우에 조밀 하 게 제어 하려는 액세스 및 공동 작업이 용이해 집니다 소규모 사용자에 대 한 사용 권한입니다.
  
SharePoint Online 팀 사이트 및 사용자가 수행할 수 있는 작업에 대 한 액세스는 SharePoint 그룹 및 권한 수준을 통해 제어 됩니다. 기본적으로 SharePoint Online 사이트에 있는 세가지 수준의 액세스:
  
- **구성원**보기, 작성 및 사이트에 있는 리소스를 수정할 수 있습니다.
    
- **소유자**는 사이트의 완벽 한 제어를 가진 사용 권한을 변경 하는 기능을 포함 합니다.
    
- **방문자**만 사이트에서 리소스를 볼 수 있는 사용자입니다.
    
이 문서의 단계 ProjectX 라는 비밀 리서치 프로젝트에 대해 격리 된 SharePoint Online 팀 사이트의 구성을 안내 합니다. 액세스 요구 사항을합니다.
  
- 프로젝트의 구성원만 사이트 및 해당 콘텐츠(문서, OneNote 전자 필기장, 페이지)에 액세스할 수 있고, SharePoint 편집 및 보기 권한 수준은 그룹 구성원 자격을 통해 제어됩니다.
    
- 사이트의 사이트 작성자 및 관리자 그룹의 구성원만 사이트 수준 권한 수정을 비롯한 사이트 관리 작업을 수행할 수 있습니다.
    
Office 365 개발/테스트 환경에서 격리 된 SharePoint Online 팀 사이트를 설정 하는 세 단계로 가지가 있습니다.
  
1. Office 365 개발/테스트 환경을 만듭니다.
    
2. ProjectX에 대한 사용자 및 그룹을 만듭니다.
    
3. 새 ProjectX SharePoint Online 팀 사이트를 만들고 발견 하면 격리 합니다.
    
> [!TIP]
> 클릭 [여기](http://aka.ms/catlgstack) 에 한 맵이 하나의 Microsoft 클라우드 테스트 랩 가이드 스택의 모든 문서를 시각적으로 표시 합니다.
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>1단계: 경량 또는 시뮬레이트된 엔터프라이즈 Office 365 개발/테스트 환경을 구축합니다.

최소 요구 사항을 경량 방식으로 격리 된 SharePoint Online 팀 사이트를 만들 하려면 2와 [Office 365 개발/테스트 환경](office-365-dev-test-environment.md)의 3 단계에서 지침을 따릅니다.
  
시뮬레이션 된 엔터프라이즈 구성에서 격리 된 SharePoint Online 팀 사이트를 만들려는 경우 [Office 365 개발/테스트 환경에 대 한 디렉터리 동기화](dirsync-for-your-office-365-dev-test-environment.md)의 지시를 따릅니다.
  
> [!NOTE]
> 격리된 SharePoint Online 사이트를 만들기 위해 시뮬레이트된 엔터프라이즈 개발/테스트 환경이 필요하지 않습니다. 해당 환경에는 Windows Server AD 포리스트의 디렉터리 동기화 및 인터넷에 연결된 시뮬레이트된 인트라넷이 포함되어 있습니다. 여기서는 옵션으로 제공되므로 격리된 SharePoint Online 사이트를 테스트하고 일반적인 조직을 나타내는 환경에서 실험할 수 있습니다. 
  
## <a name="phase-2-create-user-accounts-and-access-groups"></a>2 단계: 사용자 계정 만들기 및 그룹에 액세스

[Office 365 PowerShell 연결](https://technet.microsoft.com/library/dn975125.aspx) 지침을 사용 하 여 Office 365 내역 구독에서 전역 관리자 계정으로 연결할 수 있습니다:
  
- 사용하는 컴퓨터(경량 Office 365 개발/테스트 환경)
    
- (시뮬레이션 된 엔터프라이즈 Office 365 개발/테스트 환경)에 대 한 CLIENT1 가상 컴퓨터로 합니다.
    
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

**New-msoluser** 명령의 디스플레이에서 디자이너 잠재 고객 계정에 대해 생성 된 암호를 확인 하 고 안전한 위치에 기록 합니다.
  
Windows PowerShell 프롬프트에 대한 Microsoft Azure Active Directory 모듈에서 다음 명령을 실행합니다.
  
```
$userName= "researcher@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "Lead Researcher" -FirstName Lead -LastName Researcher -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment -ForceChangePassword $false
```

**New-msoluser** 명령의 디스플레이에서 잠재 고객 연구원 계정에 대해 생성 된 암호를 확인 하 고 안전한 위치에 기록 합니다.
  
Windows PowerShell 프롬프트에 대한 Microsoft Azure Active Directory 모듈에서 다음 명령을 실행합니다.
  
```
$userName= "devvp@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "Development VP" -FirstName Development -LastName VP -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment -ForceChangePassword $false
```

**New-msoluser** 명령의 디스플레이에서 개발 VP 계정에 대해 생성 된 암호를 확인 하 고 안전한 위치에 기록 합니다.
  
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

![Office 365 그룹 및 격리된 SharePoint Online 그룹 사이트에 대한 멤버 자격](images/5b7373b9-2a80-4880-afe5-63ffb17237e6.png)
  
## <a name="phase-3-create-a-new-projectx-sharepoint-online-team-site-and-isolate-it"></a>3 단계: 새 ProjectX SharePoint Online 팀 사이트를 만들고 발견 하면 격리

ProjectX에 대 한 SharePoint Online 팀 사이트를 만들려면 다음을 수행 합니다.
  
1. 브라우저를 사용 하는 중 하나에서 로컬 컴퓨터 (경량 구성) 또는 CLIENT1 (시뮬레이션 된 엔터프라이즈 구성) 전역 관리자 계정을 사용 하 여 Office 365 포털 ([https://portal.office.com](https://portal.office.com))에 로그인 합니다.
    
2. 타일의 목록에서 **SharePoint**를 클릭 합니다.
    
3. 브라우저에서 새 SharePoint 탭에서 **+ 사이트 만들기를**클릭 합니다.
    
4. **팀 사이트 이름** **ProjectX**를 입력 합니다. **개인 설정**선택 **개인-이 사이트에 액세스할 수 있는 구성원만**합니다.
    
5. **팀 사이트 설명** **ProjectX에 대 한 SharePoint 사이트**입력 하 고 ****을 클릭 합니다.
    
6. **가 수행 하려는 추가**에서? 창 **마침**을 클릭 합니다.
    
7. 도구 모음에서 브라우저에서 새 **ProjectX 홈** 탭에서 설정 아이콘을 클릭 한 다음 **사이트 사용 권한**을 클릭 합니다.
    
8. **사이트 사용 권한** 창에서 **고급 사용 권한 설정**을 클릭 합니다.
    
9. 새 **사용 권한: 프로젝트 X** 브라우저에서 탭, **액세스 요청 설정**을 클릭 합니다.
    
10. **액세스 요청 설정** 대화 상자에서의 선택을 취소 **허용 구성원 사이트 및 개별 파일 및 폴더 공유** 및 **액세스 요청 허용** (되도록 세 확인란을 모두 선택 취소)를 한 다음 **확인**을 클릭 합니다.
    
11. 목록에서 **ProjectX 구성원** 을 클릭 합니다.
    
12. **사용자 및 그룹** 페이지에서 **새로 만들기**를 클릭 합니다.
    
13. **공유** 대화 상자에서 입력 **ProjectX 구성원**을 선택한 다음 **공유**를 클릭 합니다.
    
14. 브라우저에서 뒤로 단추를 클릭합니다.
    
15. 목록에서 **ProjectX 소유자** 를 클릭 합니다.
    
16. **사용자 및 그룹** 페이지에서 **새로 만들기**를 클릭 합니다.
    
17. **공유** 대화 상자에서 입력 **ProjectX Admins**를 선택한 다음 **공유**를 클릭 합니다.
    
18. 브라우저에서 뒤로 단추를 클릭합니다.
    
19. 목록에서 **ProjectX 방문자** 를 클릭 합니다.
    
20. **사용자 및 그룹** 페이지에서 **새로 만들기**를 클릭 합니다.
    
21. **공유** 대화 상자에서 입력 **ProjectX 뷰어**를 선택한 다음 **공유**를 클릭 합니다.
    
22. 브라우저에서 **사용자 및 그룹** 탭을 닫은 브라우저에서 **ProjectX 홈** 탭을 클릭 한 다음 **사이트 사용 권한** 창을 닫습니다.
    
사용 권한 구성 결과는 다음과 같습니다.
  
- ProjectX Members SharePoint 그룹 (포함 하는 디자이너 잠재 고객 및 잠재 고객 연구원 사용자 계정만) ProjectX 구성원 액세스 그룹만 및 (포함 하는 전역 관리자 사용자 계정이) ProjectX 그룹을 포함 합니다.
    
- ProjectX Owners SharePoint 그룹 (포함 하는 전역 관리자 사용자 계정이) ProjectX 관리자 액세스 그룹만 포함 합니다.
    
- ProjectX 방문자 SharePoint 그룹 (포함 하는 개발 VP 사용자 계정만) ProjectX 뷰어 액세스 그룹만 포함 합니다.
    
- 구성원은 사이트 수준 권한을 수정할 수 없습니다(이 작업은 ProjectX-Admins 그룹의 구성원만 수행할 수 있음).
    
- 다른 사용자 계정은 사이트나 해당 리소스에 액세스할 수 없고 사이트에 대한 액세스를 요청할 수 없습니다.
    
그림 2는 SharePoint 그룹 및 해당 그룹 구성원을 보여 줍니다.
  
**그림 2**

![SharePoint Online 그룹 및 격리된 SharePoint Online 그룹 사이트에 대한 멤버 자격](images/595abff4-64f9-49de-a37a-c70c6856936b.png)
  
이제 잠재 고객 디자이너 사용자 계정을 사용 하 여 액세스를 살펴보겠습니다.
  
1. **ProjectX 홈** 탭에서 브라우저를 닫은 다음 브라우저에서 **Microsoft Office Home** 탭을 클릭 합니다.
    
2. 전역 관리자의 이름을 클릭 한 다음 **로그 아웃**을 클릭 합니다.
    
3. 잠재 고객 디자이너 계정 이름과 암호를 사용 하 여 Office 365 포털 ([https://portal.office.com](https://portal.office.com))에 로그인 합니다.
    
4. 타일의 목록에서 **SharePoint**를 클릭 합니다.
    
5. 브라우저에서 새 **SharePoint** 탭에서 검색 상자에 **ProjectX** 를 입력 하 고 검색을 활성화 한 다음 **ProjectX** 팀 사이트를 클릭 합니다. ProjectX 팀 사이트에 대 한 브라우저에서 새 탭이 표시 됩니다.
    
6. 설정 아이콘을 클릭 합니다. **사이트**사용 권한 없음 옵션 인지 확인 합니다. ProjectX Admins 그룹의 구성원만 사이트에 대 한 권한을 수정할 수 있기 때문에 올바른지
    
7. 메모장 또는 원하는 텍스트 편집기를 엽니다.
    
8. ProjectX 팀 사이트의 URL을 복사 하 고 메모장 이나 텍스트 편집기에서 새 줄에 붙여넣습니다.
    
9. 브라우저에서 새 **ProjectX 홈** 탭에서 **문서**를 클릭 합니다.
    
10. ProjectX 문서 폴더 URL을 복사한 후 메모장이나 텍스트 편집기에서 새 줄에 붙여 넣습니다.
    
11. 브라우저에서 새 **ProjectX 문서** 탭을 클릭 **새로 만들기 > Word 문서**합니다.
    
12. **Word 온라인** 페이지에 일부 텍스트를 입력, 상태를 **저장**, 브라우저에서 뒤로 단추를 클릭 하 고 페이지를 새로 고칠 때까지 대기 합니다. **문서** 폴더에 새 **Document.docx** 이 표시 됩니다.
    
13. **Document.docx** 문서에 대 한 줄임표 (...)를 클릭 하 고 **가져오기 링크를**클릭 합니다.
    
14. **'Document.docx' 공유** 대화 상자에서 URL을 복사 하 고 메모장 이나 다른 텍스트 편집기에서 새 줄에 붙여 **'Document.docx' 공유** 대화 상자를 닫습니다.
    
15. 브라우저에서 **ProjectX 문서** 및 **SharePoint** 탭 닫은 다음 **Microsoft Office Home** 탭을 클릭 합니다.
    
16. **잠재 고객 디자이너** 이름을 클릭 한 다음 **로그 아웃**을 클릭 합니다.
    
이제 개발 VP 사용자 계정을 사용 하 여 액세스를 살펴보겠습니다.
  
1. 개발 VP 계정 이름과 암호를 사용 하 여 Office 365 포털 ([https://portal.office.com](https://portal.office.com))에 로그인 합니다.
    
2. 타일의 목록에서 **SharePoint**를 클릭 합니다.
    
3. 브라우저에서 새 **SharePoint** 탭에서 검색 상자에 **ProjectX** 를 입력 하 고 검색을 활성화 한 다음 **ProjectX** 팀 사이트를 클릭 합니다. ProjectX 팀 사이트에 대 한 브라우저에서 새 탭이 표시 됩니다.
    
4. **문서**클릭 하 고 **Document.docx** 파일을 클릭 합니다.
    
5. 브라우저에서 **Document.docx** 탭에서 텍스트를 수정 하려고 합니다. 확인할 수 없다는 메시지가 **이 문서는 읽기 전용으로 설정 합니다.** 이 개발 VP 사용자 계정에 게는 사이트에 대 한 보기 권한이 있어야 합니다.
    
6. 브라우저에서 **Document.docx**, **ProjectX 문서**및 **SharePoint** 탭을 닫습니다.
    
7. **Microsoft Office Home** 탭을 클릭 하 고 **개발 VP** 이름을 클릭 한 다음 **로그 아웃**을 클릭 합니다.
    
이제 없는 사용 권한이 있는 사용자 계정 사용 하 여 액세스를 살펴보겠습니다.
  
1. 사용자 3 계정 이름과 암호를 사용 하 여 Office 365 포털 ([https://portal.office.com](https://portal.office.com))에 로그인 합니다.
    
2. 타일의 목록에서 **SharePoint**를 클릭 합니다.
    
3. 브라우저에서 새 **SharePoint** 탭에서 검색 상자에 **ProjectX** 를 입력 한 다음 검색을 활성화 합니다. 메시지를 참조 해야 **검색 일치 Nothing 여기.**
    
4. 메모장 이나 텍스트 편집기의 열린 인스턴스를에서 브라우저의 주소 표시줄에 ProjectX 사이트에 대 한 URL을 복사 하 고 **Enter**키를 누릅니다. **액세스 거부** 페이지가 표시 됩니다.
    
5. 메모장 이나 텍스트 편집기에서 사용자의 브라우저 주소 표시줄에 ProjectX 문서 폴더에 대 한 URL을 복사 하 고 **Enter**키를 누릅니다. **액세스 거부** 페이지가 표시 됩니다.
    
6. 메모장 이나 텍스트 편집기에서 사용자의 브라우저 주소 표시줄에 Documents.docx 파일에 대 한 URL을 복사 하 고 **Enter**키를 누릅니다. **액세스 거부** 페이지가 표시 됩니다.
    
7. 브라우저에서 **SharePoint** 탭을 닫습니다 **Microsoft Office Home** 탭을 클릭 **사용자 3** 이름을 클릭 한 다음 **로그 아웃**을 클릭 합니다.
    
격리 된 SharePoint Online 사이트 추가 테스트를 수행할 준비가 되었습니다.
  
## <a name="next-step"></a>다음 단계

프로덕션 환경에서 격리 된 SharePoint Online 팀 사이트를 배포할 준비가 되 면 [디자인 한 격리 된 SharePoint Online 팀 사이트에](design-an-isolated-sharepoint-online-team-site.md)대 한 단계별 디자인 고려 사항을 참조 하십시오.
  
## <a name="see-also"></a>참고 항목

[격리 된 SharePoint Online 팀 사이트](isolated-sharepoint-online-team-sites.md)
  
[클라우드 도입 TLG(테스트 랩 가이드)](cloud-adoption-test-lab-guides-tlgs.md)
  
[기본 구성 개발/테스트 환경](base-configuration-dev-test-environment.md)
  
[Office 365 개발/테스트 환경](office-365-dev-test-environment.md)
  
[클라우드 채택 및 하이브리드 솔루션](cloud-adoption-and-hybrid-solutions.md)




