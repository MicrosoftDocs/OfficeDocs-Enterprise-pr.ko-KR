---
title: Office 365 개발/테스트 환경용 중요 파일 보호
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/01/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 27ecff45-06a6-4629-bc45-9dab4eef3a21
description: '요약: 잘못 된 SharePoint Online 사이트 모음에 게시 된 경우에도 Office 365 정보 권한 관리가 중요 한 파일을 보호 하는 방법을 구성 하 고 설명 합니다.'
ms.openlocfilehash: 3fa771d63ca30fb53ac2c77466546cf3a2098deb
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2019
ms.locfileid: "38031573"
---
# <a name="sensitive-file-protection-in-the-office-365-devtest-environment"></a>Office 365 개발/테스트 환경용 중요 파일 보호

 **요약:** Office 365 정보 권한 관리가 잘못 된 SharePoint Online 사이트 모음에 게시 된 경우에도 중요 한 파일을 보호 하는 방법을 구성 하 고 보여 줍니다.
  
Office 365의 IRM (정보 권한 관리)은 SharePoint Online 라이브러리 및 목록에서 다운로드 되는 문서를 보호 하는 기능 집합입니다. 다운로드 된 파일은 암호화 되며 저장 된 SharePoint Online 라이브러리를 반영 하는 열기, 복사, 저장 및 인쇄 권한을 포함 합니다.
  
이 문서의 지침을 사용 하 여 Office 365 평가판 구독에서 가능한 중요 한 정보가 포함 된 파일에 대 한 IRM을 설정 하 고 Office 365에서 테스트 합니다.
  
> [!TIP]
> [여기](https://aka.ms/catlgstack)를 클릭하여 Office 365 테스트 랩 가이드 스택의 모든 문서에 대한 가상 맵을 확인할 수 있습니다.
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a>1 단계: Office 365 개발/테스트 환경 구축

최소 요구 사항에 따라 간단한 방법으로 중요 한 파일 보호를 테스트 하려는 경우에는 [Office 365 개발/테스트 환경의](office-365-dev-test-environment.md)2, 3 단계의 지침을 따릅니다.
  
시뮬레이트된 엔터프라이즈에서 중요 한 파일 보호를 테스트 하려면 [Office 365 개발/테스트 환경용 DirSync](dirsync-for-your-office-365-dev-test-environment.md)의 지침을 따릅니다.
  
> [!NOTE]
> 중요 한 파일 보호를 테스트 하려면 AD DS (Active Directory 도메인 서비스) 포리스트의 인터넷 및 디렉터리 동기화에 연결 된 시뮬레이트된 인트라넷을 포함 하는 시뮬레이트된 엔터프라이즈 개발/테스트 환경이 필요 하지 않습니다. 중요 한 파일 보호 기능을 테스트 하 고 일반적인 조직을 나타내는 환경에서 테스트해 볼 수 있도록 여기에 제공 되는 옵션입니다. 
  
## <a name="phase-2-demonstrate-how-documents-from-permissions-protected-sites-can-be-leaked"></a>2 단계: 사용 권한으로 보호 되는 사이트의 문서가 누수 될 수 있는 방식 설명

이 단계에서는 누군가가 사용 권한으로 보호 된 사이트에서 문서를 다운로드 한 다음, 사용자를 사이트에 업로드 하 여 파일을 광범위 하 게 사용할 수 있도록 하는 방법을 보여 줍니다.
  
먼저 임원을 나타내는 새 사용자 계정을 세 개 추가 하 고 Office 365 E5 라이선스를 할당 합니다.
  
[Office 365 powershell에 연결](https://technet.microsoft.com/library/dn975125.aspx) 의 지침을 사용 하 여 powershell 모듈 (필요한 경우)을 설치 하 고 다음에서 새 Office 365 구독에 연결 합니다.
  
- 사용하는 컴퓨터(경량 Office 365 개발/테스트 환경)
    
- CLIENT1 가상 컴퓨터(시뮬레이트된 엔터프라이즈 Office 365 개발/테스트 환경)
    
**Windows PowerShell 자격 증명 요청** 대화 상자에서 office 365 전역 관리자 이름 (예: jdoe@contosotoycompany.onmicrosoft.com)과 office 365 평가판 구독의 암호를 입력 합니다.
  
조직 이름 (예: contosotoycompany)과 해당 위치에 대 한 두 문자로 된 국가 코드를 입력 한 다음 windows PowerShell 프롬프트 용 Windows Azure Active Directory 모듈에서 다음 명령을 실행 합니다.
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "ceo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CEO" -FirstName "Chief" -LastName "Executive Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

**Get-msoluser** 명령을 표시할 때 CEO 계정에 대해 생성 된 암호를 확인 하 고 안전한 위치에 기록 합니다.
  
Windows PowerShell 프롬프트에 대한 Microsoft Azure Active Directory 모듈에서 다음 명령을 실행합니다.
  
```
$userName= "cfo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CFO" -FirstName "Chief" -LastName "Financial Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

**Get-msoluser** 명령을 표시 하 고 CFO 계정에 대해 생성 된 암호를 확인 하 여 안전한 위치에 기록 합니다.
  
Windows PowerShell 프롬프트에 대한 Microsoft Azure Active Directory 모듈에서 다음 명령을 실행합니다.
  
```
$userName= "coo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "COO" -FirstName "Chief" -LastName "Operations Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

**Get-msoluser** 명령을 표시할 때 coo 계정에 대해 생성 된 암호를 확인 하 고 안전한 위치에 기록 합니다.
  
다음으로, 비공개 임원 그룹을 만들고 새 executive 계정을 추가 합니다.
  
1. 브라우저에서 Office 포털로 이동 [https://admin.microsoft.com](https://admin.microsoft.com) 하 여 전역 관리자 계정을 사용 하 여 office 365 평가판 구독에 로그인 합니다.
    
  - 경량 Office 365 개발/테스트 환경을 사용 하는 경우 Internet Explorer 또는 브라우저의 개인 세션을 열고 로컬 컴퓨터에서 로그인 합니다.
    
  - 시뮬레이트된 enterprise Office 365 개발/테스트 환경을 사용 하는 경우 Azure portal을 사용 하 여 CLIENT1 가상 컴퓨터에 연결한 다음, CLIENT1에서 로그인 합니다.
    
2. **Microsoft Office 홈** 탭에서 **관리 > 그룹 > 그룹**을 클릭 한 다음 **그룹 추가**를 클릭 합니다.
    
3. **그룹 추가**에서 그룹 유형에 대해 **Office 365 그룹** 을 선택 하 고 **이름** 및 **그룹 Id**에 **임원** 을 입력 한 다음 개인 **정보 보호** **를 선택 하** 고 **소유자 선택을**클릭 합니다.
    
4. 목록에서 전역 관리자 계정 이름을 클릭 합니다.
    
5. **추가**를 클릭한 다음 **닫기**를 클릭합니다.
    
6. 그룹 목록에서 **임원**을 클릭 합니다.
    
7. **구성원에 대해 편집을**클릭 합니다.
    
8. **구성원 추가**를 클릭합니다. 구성원 목록에서 다음 사용자 계정을 선택 합니다.
    
  - 경영 최고 책임자
    
  - 최고 회계 담당자
    
  - 운영 책임자 최고
    
9. **저장**을 클릭한 다음 **닫기**를 클릭합니다.
    
10. **Office 관리 센터** 탭을 닫습니다.
    
다음에는 임원 사이트 모음을 만들고 중역 그룹의 구성원만 액세스할 수 있도록 허용 합니다.
  
1. **Microsoft Office 홈** 탭에서 **관리** 타일을 클릭 합니다.
    
2. **Office 관리 센터** 탭에서 **관리 센터 > SharePoint**를 클릭 합니다.
    
3. **SharePoint 관리 센터** 탭에서 **새 > 개인 사이트 모음**을 클릭 합니다.
    
4. 새 사이트 모음 창에서 **제목**에 **임원** , URL 상자에 임원을 차례로 입력 하 고 **관리자**에 게 전역 관리자 계정의 이름을 지정한 다음 **확인**을 클릭 합니다.
    
5. 새 사이트 모음을 만들 때까지 기다립니다. 완료 되 면 새 임원 사이트 모음의 URL을 복사 하 여 브라우저의 새 탭에 붙여넣습니다.
    
6. **임원** 사이트 모음의 오른쪽 위에 있는 설정 아이콘을 클릭 한 다음 **공유를**클릭 합니다.
    
7. **' 임원 ' 공유**에서 **고급**을 클릭 합니다.
    
8. SharePoint 그룹 목록에서 **임원 구성원**을 클릭 합니다.
    
9. **사용자 및 그룹** 페이지에서 **새로 만들기**를 클릭합니다.
    
10. **' 임원 ' 공유**에 **임원**을 입력 하 고 **임원** 그룹을 클릭 한 다음 **공유**를 클릭 합니다.
    
11. **사용자 및 그룹** 탭을 닫습니다.
    
다음으로, 모든 사용자가 Sales 사이트 모음에 액세스할 수 있도록 허용 합니다.
  
1. **SharePoint 관리 센터** 탭에서 Sales 사이트 모음의 URL을 복사 하 여 브라우저의 새 탭에 붙여넣습니다.
    
2. 오른쪽 위에 있는 설정 아이콘을 클릭 한 다음 **공유를**클릭 합니다.
    
3. **공유 ' 판매 사이트 모음 '** 에서 **고급**을 클릭 합니다.
    
4. SharePoint 그룹 목록에서 **판매 사이트 모음 구성원**을 클릭 합니다.
    
5. **사용자 및 그룹** 페이지에서 **새로 만들기**를 클릭합니다.
    
6. **' 판매 사이트 모음 ' 공유**에 **모든 사람**을 입력 하 고 **외부 사용자를 제외한 모든 사람**을 클릭 한 다음 **공유**를 클릭 합니다.
    
7. **Sales 사이트 모음** 및 **SharePoint** 탭을 닫습니다.
    
다음으로 중역 계정으로 로그인 하 고 임원 사이트 모음에 문서를 만듭니다.
  
1. **Microsoft Office 홈** 탭의 오른쪽 위에 있는 사용자 아이콘을 클릭 한 다음 **로그 아웃**을 클릭 합니다.
    
2. [https://admin.microsoft.com](https://admin.microsoft.com)으로 이동합니다.
    
3. **Office 365 로그인** 페이지에서 **다른 계정 사용**을 클릭 합니다.
    
4. **CEO** 계정 이름 및 암호를 입력 하 고 **로그인**을 클릭 합니다.
    
5. 브라우저의 새 탭에서 임원 사이트 모음에 대 한 URL ( **https://**\<조직 이름>**sharepoint.com/sites/executives**)을 입력 합니다.
    
6. **문서**를 클릭 하 고 **새로 만들기를** 클릭 한 다음 **Word 문서**를 클릭 합니다.
    
7. 제목 표시줄을 클릭 하 고 **SensitiveData-BeforeIRM**를 입력 합니다.
    
8. 문서 본문을 클릭 하 고 **최신 보드 회의에서 의사록**을 입력 한 다음 **중역**을 클릭 합니다.
    
     **문서** 폴더에 **SensitiveData-BeforeIRM** 가 표시 됩니다.
    
다음으로, SensitiveData-BeforeIRM의 로컬 복사본을 다운로드 한 후 실수로 판매 사이트 모음에 게시 합니다.
  
1. 로컬 컴퓨터에서 새 폴더를 만듭니다 (예를 들어, C:\\tlgs\\SensitiveDataTestFiles).
    
2. 브라우저의 **문서** 탭에서 **SensitiveData-BeforeIRM** 문서를 선택 하 고 줄임표를 클릭 한 다음 **다운로드**를 클릭 합니다.
    
3. 1 단계에서 만든 폴더에 **SensitiveData-BeforeIRM** 문서를 저장 합니다.
    
4. 브라우저의 새 탭에서 판매 사이트 모음에 대 한 URL ( **https://**\<조직 이름>**sharepoint.com/sites/sales**)을 입력 합니다.
    
5. **Sales 사이트 모음의** **문서** 폴더를 클릭 합니다.
    
6. **업로드**를 클릭 하 고 1 단계에서 만든 폴더에 **SensitiveData-BeforeIRM** 문서를 지정한 다음 **확인**을 클릭 합니다.
    
7. **SensitiveData-BeforeIRM** 문서가 **문서** 폴더에 있는지 확인 합니다.
    
8. **영업** 및 **SharePoint** 탭을 닫습니다.
    
다음에는 User5으로 로그인 하 고 Sales site collection에서 SensitiveData-BeforeIRM 문서를 엽니다.
  
1. **Microsoft Office 홈** 탭의 오른쪽 위에 있는 사용자 아이콘을 클릭 한 다음 **로그 아웃**을 클릭 합니다.
    
2. [https://admin.microsoft.com](https://admin.microsoft.com)으로 이동합니다.
    
3. **Office 365 로그인** 페이지에서 **다른 계정 사용**을 클릭 합니다.
    
4. User5 계정 이름 및 암호를 입력 한 다음 **로그인**을 클릭 합니다.
    
5. 브라우저의 새 탭에서 판매 사이트 모음의 URL을 입력 합니다.
    
6. **영업 사이트 모음의** **문서** 폴더에서 **SensitiveData-BeforeIRM** 문서를 클릭 합니다.
    
    해당 콘텐츠가 표시 됩니다.
    
7. **문서** 및 **판매 사이트 모음** 탭을 닫습니다.
    
실수로 영업 사이트 모음에 SensitiveData-BeforeIRM 문서를 게시 하면 CEO가 임원 사이트 모음의 사용 권한 보안을 무시 합니다.
  
3 ~ 4 단계에 대해 Office 365을 준비 하려면 SharePoint Online에 대해 IRM을 사용 하도록 설정 합니다.
  
1. **Microsoft Office 홈** 탭의 오른쪽 위에 있는 사용자 아이콘을 클릭 한 다음 **로그 아웃**을 클릭 합니다.
    
2. [https://admin.microsoft.com](https://admin.microsoft.com)으로 이동합니다.
    
3. **Office 365 로그인** 페이지에서 전역 관리자 계정 이름을 클릭 하 고 암호를 입력 한 다음 **로그인**을 클릭 합니다.
    
4. **Microsoft Office 홈** 탭에서 **관리 > 관리 센터 > SharePoint**를 클릭 합니다.
    
5. **SharePoint 관리 센터** 탭에서 **설정을**클릭 합니다.
    
6. 페이지의 **IRM (정보 권한 관리** ) 섹션에서 **구성에 지정 된 IRM 서비스 사용**을 선택 하 고 **IRM 설정 새로 고침**을 선택 합니다.
    
7. **SharePoint 관리 센터** 탭을 닫습니다.
    
## <a name="phase-3-use-sharepoint-information-rights-management-with-an-office-365-private-group"></a>3 단계: Office 365 전용 그룹에서 SharePoint 정보 권한 관리 사용

이 단계에서는 Office 365 전용 그룹의 SharePoint 정보 권한 관리를 사용 하 여 문서에 대 한 액세스 권한이 열려 있는 사이트에 게시 된 경우에도 해당 정보를 보호 합니다.
  
먼저, 임원 사이트 모음의 문서 라이브러리에 대해 IRM을 사용 하도록 설정 하 고 구성 합니다. 
  
1. 브라우저의 새 탭에서 임원 사이트 모음의 URL을 입력 합니다.
    
2. **문서**를 클릭합니다.
    
3. 오른쪽 위에서 설정 아이콘을 클릭 한 다음 **라이브러리 설정을**클릭 합니다.
    
4. **설정** 페이지의 **사용 권한 및 관리**에서 **정보 권한 관리**를 클릭 합니다.
    
5. **정보 권한 관리 설정** 페이지에서 다음을 수행 합니다.
    
  - **다운로드 시이 라이브러리의 문서에 대 한 사용 권한 제한을**선택 합니다.
    
  - **권한 정책 제목 만들기**에 대해 **임원**을 입력 합니다.
    
  - **권한 정책 설명 추가**에 대해 **임원에 IRM**을 입력 합니다.
    
6. **옵션 표시**를 클릭합니다.
    
7. **추가 irm 라이브러리 설정 설정**에서 irm을 **지원 하지 않는 문서를 사용자가 업로드 하도록 허용**안 함을 선택 합니다.
    
8. **문서 액세스 권한 구성**에서 보기 **허용** 을 선택 하 고 **다운로드 한 문서 복사본에 보는 사람이 쓰기**저장을 허용 합니다.
    
9. **그룹 보호 및 자격 증명 간격 설정**에서 **그룹 보호 허용을 선택 합니다. 기본 그룹**을 선택한 다음 **임원**을 입력 합니다.
    
10. **확인**을 클릭합니다.
    
다음으로, CEO 역할을 하 여 임원 문서 폴더에 새 문서를 업로드 하 고 다운로드 한 다음 판매 문서 폴더에 실수로 업로드 합니다.
  
1. **SensitiveData-BeforeIRM** 문서를 저장 한 로컬 폴더를 엽니다.
    
2. **SensitiveData-BeforeIRM**를 마우스 오른쪽 단추로 클릭 한 다음 **복사**를 클릭 합니다.
    
3. 폴더 내에서 마우스 오른쪽 단추를 클릭 하 고 **붙여넣기**를 클릭 합니다.
    
4. 새 **SensitiveData** 파일의 이름을 **SensitiveData-AfterIRM**로 바꿉니다.
    
5. 브라우저의 **Microsoft Office 홈** 탭에서 오른쪽 위에 있는 사용자 아이콘을 클릭 한 다음 **로그 아웃**을 클릭 합니다.
    
6. [https://admin.microsoft.com](https://admin.microsoft.com)으로 이동합니다.
    
7. **Office 365 로그인** 페이지에서 CEO 계정 이름을 클릭 하 고 암호를 입력 한 다음 **로그인**을 클릭 합니다.
    
8. 브라우저의 새 탭에서 임원 사이트 모음의 URL을 입력 합니다.
    
9. **문서** 페이지에서 **업로드**를 클릭 하 고 로컬 폴더에 **SensitiveData-AfterIRM** 문서를 지정한 다음 **열기**를 클릭 합니다.
    
10. **문서** 페이지에서 새 **SensitiveData-AfterIRM** 문서를 선택 하 고 메뉴 모음에서 줄임표 (...)를 클릭 한 다음 **다운로드**를 클릭 합니다.
    
11. 메시지가 표시 되 면 로컬 폴더에 **SensitiveData-AfterIRM** 문서를 저장 하 고 원본 버전을 덮어씁니다.
    
12. **문서** 페이지에 대 한 탭을 닫습니다.
    
13. 브라우저의 새 탭에서 판매 사이트 모음의 URL을 입력 합니다.
    
14. **문서**를 클릭합니다.
    
15. **문서** 페이지에서 **업로드**를 클릭 하 고 로컬 폴더에 **SensitiveData-AfterIRM** 문서를 지정한 다음 **열기**를 클릭 합니다.
    
16. **Sales 사이트 모음** 및 **SharePoint** 탭을 닫습니다.
    
다음으로, 일반 사용자 역할을 하 고 영업 문서 폴더의 **SensitiveData-AfterIRM** 문서에 액세스 하려고 합니다.
  
1. 브라우저의 **Microsoft Office 홈** 탭에서 오른쪽 위에 있는 사용자 아이콘을 클릭 한 다음 **로그 아웃**을 클릭 합니다.
    
2. [https://admin.microsoft.com](https://admin.microsoft.com)으로 이동합니다.
    
3. **Office 365 로그인** 페이지에서 User5 계정 이름을 클릭 하 고 암호를 입력 한 다음 **로그인**을 클릭 합니다.
    
4. 브라우저의 새 탭에서 판매 사이트 모음의 URL을 입력 합니다.
    
5. **문서**를 클릭합니다.
    
6. **문서** 페이지에서 **SensitiveData-AfterIRM** 문서를 엽니다.
    
    "죄송 하지만이 문서는 IRM (정보 권한 관리)으로 보호 되어 있으므로 Word에서 열 수 없습니다." 라는 메시지가 표시 됩니다. 
    
7. **Word에서 편집을**클릭 합니다. 파일을 열 것인지 묻는 메시지가 표시 됩니다. **예**를 클릭합니다.
    
8. 로그인 하 라는 메시지가 표시 됩니다. User5 계정의 계정 이름을 입력 하 고 **다음**을 클릭 합니다.
    
9. 암호를 입력 하 라는 메시지가 표시 됩니다. User5 계정의 암호를 입력 하 고 **로그인**을 클릭 합니다. 
    
    "이 문서를 열 수 있는 자격 증명을가지고 있지 않습니다." 라는 메시지가 표시 됩니다.
    
10. **아니요**를 클릭 합니다.
    
IRM 보호를 확인 하는 또 다른 방법은 로컬 폴더의 파일을 확인 하는 것입니다. **SensitiveData-AfterIRM** 는 **SensitiveData-BeforeIRM** 파일 보다 훨씬 커야 합니다. **SensitiveData-AfterIRM** 파일은 암호화 되며 IRM 보호 정보가 추가 됩니다.
  
## <a name="see-also"></a>참고 항목

[클라우드 도입 TLG(테스트 랩 가이드)](cloud-adoption-test-lab-guides-tlgs.md)
  
[기본 구성 개발/테스트 환경](base-configuration-dev-test-environment.md)
  
[Office 365 개발/테스트 환경](office-365-dev-test-environment.md)
  
[클라우드 도입 및 하이브리드 솔루션](cloud-adoption-and-hybrid-solutions.md)


