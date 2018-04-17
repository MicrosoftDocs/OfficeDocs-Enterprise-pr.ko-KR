---
title: Office 365 레이블 및 DLP 사용 하 여 SharePoint Online 파일 보호
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
- Strat_O365_Enterprise
ms.custom:
- Ent_Solutions
ms.assetid: c9f837af-8d71-4df1-a285-dedb1c5618b3
description: '요약: 다양 한 수준의 정보 보호와 SharePoint Online 팀 사이트에 대 한 Office 365 레이블 및 데이터 손실 방지 (DLP) 정책을 적용 합니다.'
ms.openlocfilehash: a6413ac556cf63cbe7491180d65b4425cd0dba3d
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
---
# <a name="protect-sharepoint-online-files-with-office-365-labels-and-dlp"></a>Office 365 레이블 및 DLP 사용 하 여 SharePoint Online 파일 보호

 **요약:** 정보 보호의 다양 한 수준 사용 하 여 SharePoint Online 팀 사이트에 대 한 Office 365 레이블 및 데이터 손실 방지 (DLP) 정책을 적용 합니다.
  
이 문서의 단계를 사용 하 여 디자인 하 고 Office 365 레이블 및 초기 계획, 소문자를 구분 하 고 매우 기밀 SharePoint Online 팀 사이트에 대 한 DLP 정책 배포 합니다. 이러한 세 계층의 보호 하는 방법에 대 한 자세한 내용은 [SharePoint Online 보안 사이트 및 파일을](secure-sharepoint-online-sites-and-files.md)참조 하십시오.
  
## <a name="office-365-labels-for-your-sharepoint-online-sites"></a>SharePoint Online 사이트에 대한 Office 365 레이블

만들기 (영문)을 세 단계로 되며 Office 365를 할당 한 다음 SharePoint Online 팀 사이트에 레이블을 지정 합니다.
  
### <a name="phase-1-determine-the-office-365-label-names"></a>1단계: Office 365 레이블 이름 결정

이 단계에서는 SharePoint Online 팀 사이트에 적용되는 네 가지 정보 보호 수준에 대한 Office 365 레이블의 이름을 결정합니다. 다음 표에는 각 수준에 권장되는 이름이 나와 있습니다.
  
|**SharePoint Online 팀 사이트 보호 수준**|**레이블 이름**|
|:-----|:-----|
|초기 공용  <br/> |내부 공용  <br/> |
|초기 개인  <br/> |개인  <br/> |
|중요  <br/> |중요  <br/> |
|극비  <br/> |극비  <br/> |
   
### <a name="phase-2-create-the-office-365-labels"></a>2단계: Office 365 레이블 만들기

이 단계에서는 서로 다른 수준의 정보 보호를 위해 결정한 레이블을 만들어 게시합니다.
  
레이블을 만들려면 Office 365 관리 센터 또는 Microsoft PowerShell을 사용하면 됩니다.
  
### <a name="create-office-365-labels-with-the-office-365-admin-center"></a>Office 365 관리 센터를 사용 하 여 Office 365 레이블 만들기

1. 보안 관리자 또는 회사 관리자 역할을 가진 계정으로 사용 하 여 Office 365 포털에 로그인 합니다. 도움말을 보려면 [Office 365에 로그인 할 위치](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)를 참조 하십시오.
    
2. **Microsoft Office 홈** 탭에서 **관리** 타일을 클릭합니다.
    
3. 브라우저의 새 **Office 관리 센터** 탭을 클릭 **관리 센터 > 보안 &amp; 준수**합니다.
    
4. 새에서 **홈-보안 &amp; 준수** 탭 클릭 하 여 브라우저의 **분류 > 레이블**합니다.
    
5. **홈 > 레이블** 창에서 **레이블 만들기**를 클릭합니다.
    
6. **이름에 레이블** 창에서 레이블의 이름을 입력 하 고 ****을 클릭 합니다.
    
7. **레이블 설정** 창에서 **다음**을 클릭합니다.
    
8. **설정 검토** 창에서 **이 레이블 만들기**를 클릭 하 고 **닫기**를 클릭 합니다.
    
9. 레이블을 추가하려면 5-8단계를 반복합니다.
    
### <a name="create-office-365-labels-with-powershell"></a>PowerShell을 사용한 Office 365 레이블 만들기

1. [Office 365 보안 연결 &amp; 원격 PowerShell을 사용 하 여 준수 센터](http://go.microsoft.com/fwlink/?LinkID=799771&amp;clcid=0x409) 하 고 보안 관리자 또는 회사 관리자 역할이 있는 계정의 자격 증명을 지정 합니다.
    
2. 레이블 이름 목록을 작성한 다음 PowerShell 명령 프롬프트에서 다음 명령을 실행합니다.
    
  ```
  $labelNames=@(<list of label names, each enclosed in quotes and separated by commas>)
ForEach ($element in $labelNames){ New-ComplianceTag -Name $element }
  ```

그리고 나서 다음 단계를 사용하여 새 Office 365 레이블을 게시합니다.
  
1. **홈 > 레이블** 창 보안 &amp; 준수 센터 **게시 레이블**을 클릭 합니다.
    
2. **게시할 레이블 선택** 창에서 **게시할 레이블 선택**을 클릭합니다.
    
3. **레이블 선택** 창에서 **추가**를 클릭하고 네 개의 레이블을 모두 선택합니다.
    
4. **완료**를 클릭합니다.
    
5. **게시할 레이블 선택** 창에서 **다음**을 클릭합니다.
    
6. **위치 선택** 창에서 **다음**을 클릭합니다.
    
7. **이름 정책에 따라** 창에서 **이름**레이블 사용자 집합에 대 한 이름을 입력 하 고 ****을 클릭 합니다.
    
8. **설정 검토** 창에서 **게시 레이블**를 클릭 한 다음 **닫기**를 클릭 합니다.
    
### <a name="phase-3-apply-the-office-365-labels-to-your-sharepoint-online-sites"></a>3단계: SharePoint Online 사이트에 Office 365 레이블 적용

다음 단계에 따라 Office 365 레이블을 SharePoint Online 팀 사이트의 문서 폴더에 적용합니다.
  
1. 브라우저의 **Microsoft Office 홈** 탭에서 **SharePoint** 타일을 클릭합니다.
    
2. 브라우저의 새 **SharePoint** 탭에서 할당된 Office 365 레이블이 필요한 사이트를 클릭합니다.
    
3. 브라우저의 새 SharePoint 사이트 탭에서 **문서**를 클릭합니다.
    
4. 설정 아이콘을 클릭한 다음 **라이브러리 설정**을 클릭합니다.
    
5. **권한 및 관리** 아래에서 **Apply label to items in this library(이 라이브러리의 항목에 레이블 적용)**을 클릭합니다.
    
6. **레이블 설정 적용**을 적절 한 레이블을 선택 하 고 **저장**을 클릭 합니다.
    
7. SharePoint Online 사이트의 탭을 닫습니다.
    
8. 3-8단계를 반복하여 추가 SharePoint Online 사이트에 Office 365 레이블을 할당합니다.
    
결과적으로 구성은 다음과 같습니다.
  
![SharePoint Online 팀 사이트의 네 가지 유형에 대한 Office 365 레이블입니다.](images/e0a4fdd2-1c30-4d93-8af4-a6f0c6c29966.png)
  
## <a name="dlp-policies-for-your-sharepoint-online-sites"></a>SharePoint Online 사이트에 대한 DLP 정책

다음 단계를 사용하여 사용자가 조직 외부의 중요 SharePoint Online 팀 사이트에서 문서를 공유할 때 다른 사용자에게 알려주는 DLP 정책을 구성합니다.
  
1. 브라우저에서 **Microsoft Office 홈** 탭에서 클릭 된 **보안 &amp; 준수** 바둑판식으로 배열 합니다.
    
2. 새에서 **보안 &amp; 준수** 브라우저에서 탭을 클릭 **데이터 손실 방지 > 정책**합니다.
    
3. **데이터 손실 방지** 창에서 **+ 정책 만들기**를 클릭합니다.
    
4. **서식 파일을 시작 하거나 사용자 지정 정책을 만들** 창 **사용자 지정**을 클릭 하 고 **다음**을 클릭 합니다.
    
5. **이름에 정책** 창에서 **이름**중요 한 수준 DLP 정책에 대 한 이름을 입력 하 고 ****을 클릭 합니다.
    
6. **위치 선택** 창에서 **Let me choose specific locations(특정 위치 직접 선택)**를 선택하고 **다음**을 클릭합니다.
    
7. 위치 목록에서 **Exchange 전자 메일** 및 **OneDrive 계정** 위치를 사용 하지 않도록 설정 하 고 ****을 클릭 합니다.
    
8. **Customize the types of sensitive info you want to protect(보호할 중요 정보 유형 사용자 지정)** 창에서 **편집**을 클릭합니다.
    
9. **보호 하기 위해 콘텐츠 형식 선택** 창에서 드롭다운 목록 상자에서 **추가** 클릭 하 고 **레이블**을 클릭 합니다.
    
10. **레이블** 창에서 **+ 기호 추가**클릭, **중요 한** 레이블을 선택, **추가**클릭 하 고 **완료**를 클릭 합니다.
    
11. **Choose the types of content to protect(보호할 콘텐츠 형식 선택)** 창에서 **저장**을 클릭합니다.
    
12. **Customize the types of sensitive info you want to protect(보호할 중요 정보 유형 사용자 지정)** 창에서 **다음**을 클릭합니다.
    
13. **중요한 정보를 발견하면**  창에서 **팁 및 전자 메일 사용자 지정**을 클릭합니다.
    
14. **Customize policy tips and email notifications(정책 팁 및 전자 메일 알림 사용자 지정)** 창에서 **Customize the policy tip text(정책 팁 텍스트 사용자 지정)**를 클릭합니다.
    
15. 텍스트 상자에 다음을 입력하거나 붙여넣습니다.
    
  - 조직 외부의 사용자와 공유하려면 파일을 다운로드한 다음 파일을 엽니다. 파일, 문서 보호, 암호 설정을 차례로 클릭한 다음 강력한 암호를 지정합니다. 암호를 별도의 전자 메일 또는 다른 통신 수단으로 보냅니다.
    
    또는 입력 하거나 조직 외부에 파일을 공유 하는 방법에 대 한 사용자가 지시 하는 정책 팁에 붙여넣습니다.
    
16. **확인**을 클릭합니다.
    
17. **는 중요 한 정보를 검색 하는 경우 작업을 수행 하 시겠습니까?** 창에서 **공유, 다른 사람을 차단 하 고 공유 내용에 대 한 액세스를 제한** 확인란의 선택을 취소 하 고 **다음**을 클릭 합니다.
    
18. **먼저 수행 정책 또는 테스트 작업을 설정 하 시겠습니까?** 창 **예, 귀하가 켜기**를 클릭 한 후에 **다음**을 클릭 합니다.
    
19. **설정 검토** 창에서 **만들기**를 클릭 한 다음 **닫기**를 클릭 합니다.
    
결과적으로 중요 SharePoint Online 팀 사이트에 대한 구성은 다음과 같습니다.
  
![중요한 Office 365 레이블을 사용하는 격리된 SharePoint Online 팀 사이트의 DLP 정책입니다.](images/2ff4cc53-87a8-43e3-b637-3068d88409f3.png)
  
그리고 나서 다음 단계를 사용하여 사용자가 조직 외부의 극비 SharePoint Online 팀 사이트에서 문서를 공유할 때 다른 사용자를 차단하는 DLP 정책을 구성합니다.
  
1. 브라우저에서 **Microsoft Office 홈** 탭에서 클릭 된 **보안 &amp; 준수** 바둑판식으로 배열 합니다.
    
2. 새에서 **보안 &amp; 준수** 브라우저에서 탭을 클릭 **데이터 손실 방지 > 정책**합니다.
    
3. **데이터 손실 방지** 창에서 **+ 정책 만들기**를 클릭합니다.
    
4. **서식 파일을 시작 하거나 사용자 지정 정책을 만들** 창 **사용자 지정**을 클릭 하 고 **다음**을 클릭 합니다.
    
5. **이름에 정책** 창에서 **이름**매우 중요 한 수준 DLP 정책에 대 한 이름을 입력 하 고 ****을 클릭 합니다.
    
6. **위치 선택** 창에서 **Let me choose specific locations(특정 위치 직접 선택)**를 선택하고 **다음**을 클릭합니다.
    
7. 위치 목록에서 **Exchange 전자 메일** 및 **OneDrive 계정** 위치를 사용 하지 않도록 설정 하 고 ****을 클릭 합니다.
    
8. **Customize the types of sensitive info you want to protect(보호할 중요 정보 유형 사용자 지정)** 창에서 **편집**을 클릭합니다.
    
9. **보호 하기 위해 콘텐츠 형식 선택** 창에서 드롭다운 목록 상자에서 **추가** 클릭 하 고 **레이블**을 클릭 합니다.
    
10. **레이블** 창에서 **+ 기호 추가**클릭, **기밀 사항이** 레이블을 선택, **추가**클릭 하 고 **완료**를 클릭 합니다.
    
11. **Choose the types of content to protect(보호할 콘텐츠 형식 선택)** 창에서 **저장**을 클릭합니다.
    
12. **Customize the types of sensitive info you want to protect(보호할 중요 정보 유형 사용자 지정)** 창에서 **다음**을 클릭합니다.
    
13. **중요한 정보를 발견하면**  창에서 **팁 및 전자 메일 사용자 지정**을 클릭합니다.
    
14. **Customize policy tips and email notifications(정책 팁 및 전자 메일 알림 사용자 지정)** 창에서 **Customize the policy tip text(정책 팁 텍스트 사용자 지정)**를 클릭합니다.
    
15. 텍스트 상자에 다음을 입력하거나 붙여넣습니다.
    
  - 조직 외부의 사용자와 공유하려면 파일을 다운로드한 다음 파일을 엽니다. 파일, 문서 보호, 암호 설정을 차례로 클릭한 다음 강력한 암호를 지정합니다. 암호를 별도의 전자 메일 또는 다른 통신 수단으로 보냅니다.
    
    또는 입력 하거나 조직 외부에 파일을 공유 하는 방법에 대 한 사용자가 지시 하는 정책 팁에 붙여넣습니다.
    
16. **확인**을 클릭합니다.
    
17. **는 중요 한 정보를 검색 하는 경우 작업을 수행 하 시겠습니까?** 창 **, 업무 효율성을 재정의 하려면 필요**를 선택 하 고 **다음**을 클릭 합니다.
    
18. **먼저 수행 정책 또는 테스트 작업을 설정 하 시겠습니까?** 창 **예, 귀하가 켜기**를 클릭 한 후에 **다음**을 클릭 합니다.
    
19. **설정 검토** 창에서 **만들기**를 클릭 한 다음 **닫기**를 클릭 합니다.
    
결과적으로 극비 SharePoint Online 팀 사이트에 대한 구성은 다음과 같습니다.
  
![높은 수준의 기밀 Office 365 레이블을 사용하는 격리된 SharePoint Online 팀 사이트의 DLP 정책입니다.](images/f705d3d0-23c9-4333-8b70-ad3b91f835ea.png)
  
## <a name="next-step"></a>다음 단계

[Azure Information Protection을 사용한 SharePoint Online 파일 보호](protect-sharepoint-online-files-with-azure-information-protection.md)
    
## <a name="see-also"></a>참고 항목

[SharePoint Online 사이트 및 파일 보호](secure-sharepoint-online-sites-and-files.md)
  
[개발/테스트 환경의 SharePoint Online 사이트 보호](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[정치적 캠페인, 비영리 조직 및 기타 기밀 조직에 대한 Microsoft 보안 지침](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[클라우드 채택 및 하이브리드 솔루션](cloud-adoption-and-hybrid-solutions.md)


