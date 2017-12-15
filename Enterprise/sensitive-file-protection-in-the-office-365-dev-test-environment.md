---
title: "Office 365 개발/테스트 환경에서 중요 한 파일 보호"
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
- jan17entnews
- TLG
- Ent_TLGs
ms.assetid: 27ecff45-06a6-4629-bc45-9dab4eef3a21
description: "요약: 구성 및 잘못 된 SharePoint Online 사이트 모음에 게시 된 경우에 Office 365 정보 권한 관리에 중요 한 파일을 보호 하는 방법을 시연 합니다."
ms.openlocfilehash: a6547cf4327980e3909323d5bda4455dfffd37f4
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2017
---
# <a name="sensitive-file-protection-in-the-office-365-devtest-environment"></a>Office 365 개발/테스트 환경에서 중요 한 파일 보호

 **요약:** 구성 하 고 잘못 된 SharePoint Online 사이트 모음에 게시 된 경우에 Office 365 정보 권한 관리에 중요 한 파일을 보호 하는 방법을 시연 합니다.
  
Office 365의 정보 권한 관리 (IRM)는 SharePoint Online 라이브러리 및 목록에서 다운로드 하는 문서를 보호 하기 위해 기능 집합입니다. 다운로드 한 파일 저장, 열기, 복사본을 포함 및 저장 된 SharePoint Online 라이브러리를 반영 하는 권한이 인쇄 암호화 됩니다.
  
이 문서의 지침을 함께 사용 하도록 설정 및 Office 365 평가판 구독에서 사용할 수 있는 중요 한 정보를 포함 하는 파일에 대 한 Office 365에서 IRM을 테스트 합니다.
  
> [!TIP]
> 클릭 [여기](http://aka.ms/catlgstack) 에 한 맵이 하나의 Microsoft 클라우드 테스트 랩 가이드 스택의 모든 문서를 시각적으로 표시 합니다.
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a>1 단계: Office 365 개발/테스트 환경을 구축합니다

최소 요구 사항을 경량 방식으로 중요 한 파일 보호 기능을 테스트 하려면 2와 [Office 365 개발/테스트 환경](office-365-dev-test-environment.md)의 3 단계에서 지침을 따릅니다.
  
시뮬레이션 된 엔터프라이즈에서 중요 한 파일 보호 기능을 테스트 하려는 경우 [Office 365 개발/테스트 환경에 대 한 디렉터리 동기화](dirsync-for-your-office-365-dev-test-environment.md)의 지시를 따릅니다.
  
> [!NOTE]
> 중요 한 파일 보호를 테스트 하지 않아도 인터넷에 연결 하는 시뮬레이션 된 인트라넷을 포함 하는 시뮬레이션 된 엔터프라이즈 개발/테스트 환경 및 Windows Server AD 포리스트에 대 한 디렉터리 동기화 합니다. 제공은 중요 한 파일 보호 기능을 테스트 하 고 일반적인 조직을 대표 하는 환경에서 사용해 수 있도록 하는 옵션으로 여기 합니다. 
  
## <a name="phase-2-demonstrate-how-documents-from-permissions-protected-sites-can-be-leaked"></a>2 단계: 사용 권한으로 보호 된 사이트에서 문서 수 유출 하는 방법을 보여줍니다.

이 단계는 다른 사용자 수는 사용 권한으로 보호 된 사이트에서 문서를 다운로드 하 고 다음 널리 개방 된 사용 권한이 있는 사이트에 업로드를 보여줍니다.
  
먼저, 임원 진술 하 고 Office 365 E5 라이선스를 할당 하는 3 개의 새 사용자 계정을 추가 합니다.
  
[Office 365 PowerShell 연결](https://technet.microsoft.com/library/dn975125.aspx) 에 지침을 사용 하 여 PowerShell 모듈 (필요한 경우)를 설치 하 고에서 새로운 Office 365 구독에 연결 합니다.
  
- 사용하는 컴퓨터(경량 Office 365 개발/테스트 환경)
    
- (시뮬레이션 된 엔터프라이즈 Office 365 개발/테스트 환경)에 대 한 CLIENT1 가상 컴퓨터로 합니다.
    
**Windows PowerShell 자격 증명 요청** 대화 상자에서 Office 365 전역 관리자 이름을 입력 합니다 (예: jdoe@contosotoycompany.onmicrosoft.com) 및 Office 365 평가판 구독의 암호입니다.
  
조직 이름을 입력 (예: contosotoycompany) 및 사용자 위치에 대 한 코드 및 Windows Azure Active Directory 모듈에 대 한 Windows PowerShell 프롬프트에서 다음 명령을 실행 하는 다음 두 자리 국가:
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "ceo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CEO" -FirstName "Chief" -LastName "Executive Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

**New-msoluser** 명령의 디스플레이에서 CEO 계정에 대해 생성 된 암호를 확인 하 고 안전한 위치에 기록 합니다.
  
Windows PowerShell 프롬프트에 대한 Microsoft Azure Active Directory 모듈에서 다음 명령을 실행합니다.
  
```
$userName= "cfo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CFO" -FirstName "Chief" -LastName "Financial Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

**New-msoluser** 명령의 디스플레이에서 CFO 계정에 대해 생성 된 암호를 확인 하 고 안전한 위치에 기록 합니다.
  
Windows PowerShell 프롬프트에 대한 Microsoft Azure Active Directory 모듈에서 다음 명령을 실행합니다.
  
```
$userName= "coo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "COO" -FirstName "Chief" -LastName "Operations Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

**New-msoluser** 명령의 디스플레이에서 COO 계정에 대해 생성 된 암호를 확인 하 고 안전한 위치에 기록 합니다.
  
다음으로, 개인 임원 그룹을 만들고 새 임원 계정을 추가 합니다.
  
1. 브라우저에서 [http://portal.office.com](http://portal.office.com) 에서 Office 포털로 이동 하 고 전역 관리자 계정 사용 하 여 Office 365 평가판 구독에 로그인 합니다.
    
  - Office 365 개발/테스트 환경 lightweight를 사용 하는 경우 Internet Explorer 또는 브라우저의 개인 세션을 열고 로컬 컴퓨터에서 로그인 합니다.
    
  - 시뮬레이션 된 엔터프라이즈 Office 365 개발/테스트 환경을 사용 하는 경우 Azure 포털을 사용 하 여 CLIENT1 가상 컴퓨터에 연결한 다음 CLIENT1에서 로그인 합니다.
    
2. **Microsoft Office 홈** 탭에서 클릭 **관리 > 그룹 > 그룹**, **그룹 추가**클릭 하 고 있습니다.
    
3. **추가 그룹**에서 그룹 종류에 대 한 **Office 365 그룹** 을 선택, **임원** **이름과 **그룹 Id**를** 입력 **개인** **개인정보 보호**대 한 선택한 다음 클릭 **소유자를 선택**합니다.
    
4. 목록에서 전역 관리자 계정 이름을 클릭 합니다.
    
5. **추가**클릭 한 다음 **닫기**를 클릭 합니다.
    
6. 그룹 목록에서 **중역**을 클릭 합니다.
    
7. **구성원에 대 한 편집**을 클릭 합니다.
    
8. **구성원 추가**클릭 합니다. 구성원 목록에서 다음 사용자 계정을 선택 합니다.
    
  - 중역이 책임자
    
  - 회계 부 책임자
    
  - 작업 책임자
    
9. **저장**을 클릭 한 다음 **닫기**를 클릭 합니다.
    
10. **Office 관리 센터** 탭을 닫습니다.
    
다음으로 임원 사이트 모음을 만들고에 대 한 액세스는 임원 그룹의 구성원만 허용 합니다.
  
1. **Microsoft Office 홈** 탭에서 **관리** 타일을 클릭 합니다.
    
2. **Office 관리 센터** 탭을 클릭 **관리 센터 > SharePoint**합니다.
    
3. **SharePoint 관리 센터** 탭을 클릭 **새로 만들기 > 개인 사이트 모음**합니다.
    
4. 새 사이트 모음 창에서 **임원** **제목**, 경영진의 URL 상자에서에 입력 하 고 **관리자**, 전역 관리자 계정의 이름을 지정 한 다음 **확인**을 클릭 합니다.
    
5. 새 사이트 모음도 만들지 않은 때까지 기다립니다. 완료 되 면 새 임원 사이트 모음의 URL을 복사 하 고 브라우저의 새 탭에 붙여넣습니다.
    
6. **임원** 사이트 모음의 오른쪽 위에 있는 설정 아이콘을 클릭 하 고 **공유 대상을**클릭 합니다.
    
7. **공유 '임원'** **고급**을 클릭 합니다.
    
8. SharePoint 그룹의 목록에서 **임원 구성원**을 클릭 합니다.
    
9. **사용자 및 그룹** 페이지에서 **새로 만들기**를 클릭 합니다.
    
10. **공유 '임원'** **임원**를 입력 하 고 **임원** 그룹을 클릭 한 다음 **공유**를 클릭 합니다.
    
11. **사용자 및 그룹** 탭을 닫습니다.
    
다음으로 모든 사용자가 판매 사이트 모음에 액세스 허용 합니다.
  
1. **SharePoint 관리 센터** 탭에서 Sales 사이트 모음의 URL을 복사 하 고 브라우저의 새 탭에 붙여넣습니다.
    
2. 오른쪽 위에 있는 설정 아이콘을 클릭 하 고 **공유 대상을**클릭 합니다.
    
3. **공유 '영업 사이트 모음의'** **고급**을 클릭 합니다.
    
4. SharePoint 그룹의 목록에서 **판매 사이트 모음 구성원을**클릭 합니다.
    
5. **사용자 및 그룹** 페이지에서 **새로 만들기**를 클릭 합니다.
    
6. **'영업 사이트 모음의' 공유** **모든 사용자**를 입력 하 고 **외부 사용자를 제외한 모든**를 클릭 한 다음 **공유**를 클릭 합니다.
    
7. 다음은 **Sales 사이트 모음** 및 **SharePoint** 탭을 닫습니다.
    
다음으로, 임원 계정을 사용 하 여 로그인 및 임원 사이트 모음에서 문서를 만듭니다.
  
1. **Microsoft Office 홈** 탭에서 위 오른쪽에 있는 사용자 아이콘을 클릭 한 다음 **로그 아웃**을 클릭 합니다.
    
2. [Http://portal.office.com](http://portal.office.com)로 이동 합니다.
    
3. **Office 365 로그인** 페이지에서 **다른 계정 사용**을 클릭 합니다.
    
4. **CEO** 계정 이름 및 해당 암호를 입력 하 고 **로그인**을 클릭 합니다.
    
5. 브라우저의 새 탭에서 임원 사이트 모음에 URL을 입력 합니다 ( **https://**\<조직 이름 >**.sharepoint.com/sites/executives**).
    
6. **문서**를 클릭 하 고 **새로 만들기** 를 클릭 한 다음 **Word 문서**를 클릭 합니다.
    
7. 제목 표시줄에서 클릭 하 고 **SensitiveData BeforeIRM**를 입력 합니다.
    
8. 문서 본문에 클릭 하 고 **최신 보드 모임에서 시간 (분)을**입력 한 다음 **경영진**을 클릭 하 고 합니다.
    
     **문서** 폴더에 **SensitiveData BeforeIRM.docx** 표시 됩니다.
    
다음으로 SensitiveData BeforeIRM.docx 문서의 로컬 복사본을 다운로드 하 고 Sales 사이트 모음을 실수로 게시 합니다.
  
1. 로컬 컴퓨터에서 새 폴더를 만듭니다 (예: c:\\Tlg\\SensitiveDataTestFiles).
    
2. 브라우저에서 **문서** 탭에서 **SensitiveData BeforeIRM.docx** 문서를 선택, 있는 줄임표를 클릭 하 고 **다운로드**를 클릭 합니다.
    
3. 1 단계에서 만든 폴더에 **SensitiveData BeforeIRM.docx** 문서를 저장 합니다.
    
4. 브라우저의 새 탭에서 Sales 사이트 모음에 URL을 입력 합니다 ( **https://**\<조직 이름 >**.sharepoint.com/sites/sales**).
    
5. **판매 사이트 모음을 사이트**의 **문서** 폴더를 클릭 합니다.
    
6. **업로드**를 클릭 하 고 1 단계에서 만든 폴더에 **SensitiveData BeforeIRM.docx** 문서를 지정 하 고 **확인**을 클릭 합니다.
    
7. **문서** 폴더에 **SensitiveData BeforeIRM.docx** 문서 인지 확인 합니다.
    
8. **판매** 및 **SharePoint** 탭을 닫습니다.
    
다음으로 User5로 로그인 한 Sales 사이트 모음에서 SensitiveData BeforeIRM.docx 문서를 열려고 시도 합니다.
  
1. **Microsoft Office 홈** 탭에서 위 오른쪽에 있는 사용자 아이콘을 클릭 한 다음 **로그 아웃**을 클릭 합니다.
    
2. [Http://portal.office.com](http://portal.office.com)로 이동 합니다.
    
3. **Office 365 로그인** 페이지에서 **다른 계정 사용**을 클릭 합니다.
    
4. User5 계정 이름 및 해당 암호를 입력 하 고 **로그인**을 클릭 합니다.
    
5. 브라우저의 새 탭에서 Sales 사이트 모음에 URL을 입력 합니다.
    
6. **판매 사이트 모음을 사이트**의 **문서** 폴더를 **SensitiveData BeforeIRM.docx** 문서를 클릭 합니다.
    
    해당 내용을 표시 됩니다.
    
7. 다음은 **문서** 및 **판매 사이트 모음** 탭을 닫습니다.
    
영업 사이트 모음의 SensitiveData BeforeIRM.docx 문서를 실수로 게시, 하 여 CEO 임원 사이트 모음의 사용 권한 보안을 무시 됩니다.
  
단계 3과 4에 대 한 Office 365를 준비 하려면 SharePoint Online에 대 한 IRM을 사용 하도록 설정 합니다.
  
1. **Microsoft Office 홈** 탭에서 위 오른쪽에 있는 사용자 아이콘을 클릭 한 다음 **로그 아웃**을 클릭 합니다.
    
2. [Http://portal.office.com](http://portal.office.com)로 이동 합니다.
    
3. **Office 365 로그인** 페이지에서 전역 관리자 계정 이름을 클릭 하 고 해당 암호를 입력 한 다음 **로그인**을 클릭 합니다.
    
4. **Microsoft Office 홈** 탭에서 클릭 **관리 > 관리 센터 > SharePoint**합니다.
    
5. **SharePoint 관리 센터** 탭에서 **설정**을 클릭 합니다.
    
6. **설정** 페이지의 **정보 권한 관리 (IRM)** 섹션에서 **구성에 지정 된 IRM 서비스를 사용 하 여**를 선택한 다음 **새로고침 IRM 설정**을 선택 합니다.
    
7. **SharePoint 관리 센터** 탭을 닫습니다.
    
## <a name="phase-3-use-sharepoint-information-rights-management-with-an-office-365-private-group"></a>Office 365 개인 그룹과 3 단계: 사용 하 여 SharePoint 정보 권한 관리

이 단계에서 열기 권한으로 사이트에 게시 하는 경우에 중요 한 정보를 사용 하 여 문서에 대 한 액세스를 보호 하기 위해 Office 365 개인 그룹과 SharePoint 정보 권한 관리를 사용 합니다.
  
첫째, 사용 하도록 설정 및 임원 사이트 모음의 문서 라이브러리에 대 한 IRM을 구성 합니다. 
  
1. 브라우저의 새 탭에서 임원 사이트 모음에 URL을 입력 합니다.
    
2. **문서**를 클릭 합니다.
    
3. 위 오른쪽에서 설정 아이콘을 클릭 하 고 **라이브러리 설정**을 클릭 합니다.
    
4. **설정** 페이지의 **사용 권한 및 관리**에서 **정보 권한 관리**를 클릭 합니다.
    
5. **정보 권한 관리 설정** 페이지 수행 합니다.
    
  - **다운로드 시이 라이브러리에서 문서에 대 한 사용 권한을 제한**을 선택 합니다.
    
  - **권한 정책 제목 만들기**대 한 **경영진**을 입력 합니다.
    
  - **추가 권한 정책 설명**대 한 **중역에 대 한 IRM**을 입력 합니다.
    
6. **옵션 표시**를 클릭 합니다.
    
7. **추가 IRM 라이브러리 설정을**에서 **IRM을 지원 하지 않는 문서를 업로드할 수 없도록 함**을 선택 합니다.
    
8. **구성 문서 액세스 권한** **허용 뷰어 인쇄** 하 고 **허용 뷰어 다운로드 한 문서의 복사본에 쓸 수**를 선택 합니다.
    
9. **그룹 보호 및 자격 증명 간격 설정**에서 **허용 그룹 보호** 를 선택 하 고 **기본 그룹**에 대 한 **경영진**을 입력 합니다.
    
10. **확인**을 클릭합니다.
    
다음으로, CEO 역할을 있습니다 임원 문서 폴더에 새 문서를 업로드, 다운로드, 다음 실수로 Sales 문서 폴더에 업로드 합니다.
  
1. **SensitiveData BeforeIRM.docx** 문서를 저장 하는 로컬 폴더를 엽니다.
    
2. **SensitiveData BeforeIRM.docx**마우스 오른쪽 단추로 클릭 한 다음 **복사**를 클릭 합니다.
    
3. 폴더를 마우스 오른쪽 **붙여넣기**를 클릭 합니다.
    
4. 새 **SensitiveData-BeforeIRM-Copy.docx** 파일을 **SensitiveData AfterIRM.docx**을 바꿉니다.
    
5. 브라우저에서 **Microsoft Office 홈** 탭에서 위 오른쪽에 있는 사용자 아이콘을 클릭 한 다음 **로그 아웃**을 클릭 합니다.
    
6. [Http://portal.office.com](http://portal.office.com)로 이동 합니다.
    
7. **Office 365 로그인** 페이지에서 CEO 계정 이름을 클릭 하 고 해당 암호를 입력 한 다음 **로그인**을 클릭 합니다.
    
8. 브라우저의 새 탭에서 임원 사이트 모음에 URL을 입력 합니다.
    
9. **문서** 페이지에서 **업로드**를 클릭, 로컬 폴더, **SensitiveData AfterIRM.docx** 문서를 지정 하 고 **열기**를 클릭 합니다.
    
10. **문서** 페이지에서 새 **SensitiveData AfterIRM.docx** 문서를 선택 하 고 메뉴 모음에서 줄임표 (...)를 클릭 한 다음 **다운로드**를 클릭 합니다.
    
11. 대화 상자가 나타나면 원래 버전을 덮어쓰지 로컬 폴더, **SensitiveData AfterIRM.docx** 문서를 저장 합니다.
    
12. **문서** 페이지에 대 한 탭을 닫습니다.
    
13. 브라우저의 새 탭에서 Sales 사이트 모음에 URL을 입력 합니다.
    
14. **문서**를 클릭 합니다.
    
15. **문서** 페이지에서 **업로드**를 클릭, 로컬 폴더, **SensitiveData AfterIRM.docx** 문서를 지정 하 고 **열기**를 클릭 합니다.
    
16. 다음은 **Sales 사이트 모음** 및 **SharePoint** 탭을 닫습니다.
    
다음으로 일반 사용자 역할을 하려고 하면 Sales 문서 폴더에 **SensitiveData AfterIRM.docx** 문서에 액세스 합니다.
  
1. 브라우저에서 **Microsoft Office 홈** 탭에서 위 오른쪽에 있는 사용자 아이콘을 클릭 한 다음 **로그 아웃**을 클릭 합니다.
    
2. [Http://portal.office.com](http://portal.office.com)로 이동 합니다.
    
3. **Office 365 로그인** 페이지에서 User5 계정 이름을 클릭 하 고 해당 암호를 입력 한 다음 **로그인**을 클릭 합니다.
    
4. 브라우저의 새 탭에서 Sales 사이트 모음에 URL을 입력 합니다.
    
5. **문서**를 클릭 합니다.
    
6. **문서** 페이지에서 **SensitiveData AfterIRM.docx** 문서를 엽니다.
    
    "사과, Word 온라인 정보 권한 관리 (IRM)를 통해 보호 되어 있으므로이 문서를 열 수 없습니다." 되었다는 메시지가 나타나야 합니다. 
    
7. **Word에서 편집**을 클릭 합니다. 메시지가 표시 되는 파일을 열 하려는 경우. **예**를 클릭 합니다.
    
8. 로그인 하는 메시지가 User5 계정의 계정 이름을 입력 하 고 **다음**을 클릭 합니다.
    
9. 암호를 제공 하 라는 메시지가 표시 됩니다. User5 계정에 대 한 암호를 입력 한 다음 **로그인**을 클릭 합니다. 
    
    확인할 수는 없다는 메시지: "없는이 문서를 열 수 있도록 하는 자격 증명입니다."
    
10. **아니요**를 클릭 합니다.
    
IRM 보호를 참조 하는 다른 방법은 로컬 폴더에 파일에서 확인 하는 것입니다. **SensitiveData AfterIRM.docx** **SensitiveData BeforeIRM.docx** 파일 보다 훨씬 더 큰 있어야 합니다. **SensitiveData AfterIRM.docx** 파일은 암호화 및 IRM 보호 정보를 사용 하 여 추가 합니다.
  
## <a name="see-also"></a>See Also

[클라우드 채택 테스트 랩 가이드 (Tlg)](cloud-adoption-test-lab-guides-tlgs.md)
  
[기본 구성 개발/테스트 환경](base-configuration-dev-test-environment.md)
  
[Office 365 개발/테스트 환경](office-365-dev-test-environment.md)
  
[클라우드 채택 및 하이브리드 솔루션](cloud-adoption-and-hybrid-solutions.md)


