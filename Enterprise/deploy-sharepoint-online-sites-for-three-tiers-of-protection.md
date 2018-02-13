---
title: "보호의 세 계층에 대 한 SharePoint Online 사이트 배포"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365, Strat_O365_Enterprise
ms.custom: Strat_O365_Enterprise, Ent_Solutions
ms.assetid: 1e8e3cfd-b878-4088-b941-9940363a5fae
description: "요약: 만들기 및 다양 한 수준의 정보 보호에 대 한 SharePoint Online 팀 사이트를 구성 합니다."
ms.openlocfilehash: 4e6e70377f27bcd3cf367aefa1a640188abefc50
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/13/2018
---
# <a name="deploy-sharepoint-online-sites-for-three-tiers-of-protection"></a>보호의 세 계층에 대 한 SharePoint Online 사이트 배포

 **요약:** 페이지를 만들고 다양 한 수준의 정보 보호에 대 한 SharePoint Online 팀 사이트를 구성 합니다.
  
이 문서의 단계를 사용 하 여 디자인 하 고 초기 계획, 소문자를 구분 하 고 매우 기밀 SharePoint Online 팀 사이트를 배포 합니다. 이러한 세 계층의 보호 하는 방법에 대 한 자세한 내용은 [SharePoint Online 보안 사이트 및 파일을](secure-sharepoint-online-sites-and-files.md)참조 하십시오.
  
## <a name="baseline-sharepoint-online-team-sites"></a>초기 계획 SharePoint Online 팀 사이트

초기 계획 보호 모두 공용 및 개인 팀 사이트를 포함합니다. 공용 팀 사이트를 검색 하 고 조직에서 누구나 하 여 액세스할 수 있습니다. 개인 사이트 수만 검색 하 고 팀 사이트와 연결 된 Office 365 그룹의 구성원으로 액세스 합니다. 이러한 유형의 팀 사이트의 두 구성원이 다른 사용자와 사이트를 공유할 수 있습니다.
  
### <a name="public"></a>공용

일반 액세스 및 사용 권한으로 초기 SharePoint Online 팀 사이트를 만들려면 다음을 수행 합니다.
  
1. SharePoint Online 팀 사이트 (SharePoint Online 관리자)를 관리 하는데 사용 되는 계정 사용 하 여 Office 365 포털에 로그인 합니다. 도움말을 보려면 [Office 365에 로그인 할 위치](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)를 참조 하십시오.
    
2. 타일의 목록에서 **SharePoint**를 클릭 합니다.
    
3. 브라우저에서 새 **SharePoint** 탭에서 **+ 사이트 만들기를**클릭 합니다.
    
4. **사이트 만들기** 페이지에서 **팀 사이트**를 클릭 합니다.
    
5. **사이트 이름**공용 팀 사이트에 대 한 이름을 입력 합니다. 
    
6. **팀 사이트 설명**사이트의 용도에 대 한 설명을 입력 합니다.
    
7. **개인 설정** **공용-이 사이트에 액세스할 수는 조직의 모든 사용자**를 선택 하 고 ****을 클릭 합니다.
    
8. 에 **가 수행 하려는 추가?** 창 **마침**을 클릭 합니다.
    
구성 결과는 다음과 같습니다.
  
![공용 SharePoint Online 팀 사이트에 대한 기준 수준 보호입니다.](images/bcd46b8d-3f89-4398-80ce-4da17ee85e03.png)
  
### <a name="private"></a>개인

개인 액세스 및 사용 권한으로 초기 SharePoint Online 팀 사이트를 만들려면 다음을 수행 합니다.
  
1. SharePoint Online 팀 사이트 (SharePoint Online 관리자)를 관리 하는데 사용 되는 계정 사용 하 여 Office 365 포털에 로그인 합니다. 도움말을 보려면 [Office 365에 로그인 할 위치](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)를 참조 하십시오.
    
2. 타일의 목록에서 **SharePoint**를 클릭 합니다.
    
3. 브라우저에서 새 **SharePoint** 탭에서 **+ 사이트 만들기를**클릭 합니다.
    
4. **사이트 만들기** 페이지에서 **팀 사이트**를 클릭 합니다.
    
5. **사이트 이름**개인 팀 사이트에 대 한 이름을 입력 합니다. 
    
6. **팀 사이트 설명** 에 사이트의 용도에 대 한 설명을 입력 합니다.
    
7. **개인정보 보호 설정**선택 **개인-이 사이트에 액세스할 수 있는 구성원만**, **다음**을 클릭 하 고 있습니다.
    
8. 에 **가 수행 하려는 추가?** 창, **구성원 추가**개인 팀 사이트에 액세스할 수 있는 사용자 계정의 이름을 입력 합니다.
    
9. 작업이 완료 되 면 **마침** 을 클릭 하는 사이트에 추가 된 구성원 초기 집합 추가 (영문)
    
구성 결과는 다음과 같습니다.
  
![개인 SharePoint Online 팀 사이트에 대한 기준 수준의 보호입니다.](images/91769026-37e3-4383-ac3c-dbf7aca98e41.png)
  
## <a name="sensitive-sharepoint-online-team-sites"></a>중요 한 SharePoint Online 팀 사이트

중요 한 SharePoint Online 팀 사이트는 사용 권한을 팀 사이트와 연결 된 Office 365 그룹의 구성원 이어야 하는 대신 SharePoint 그룹의 구성원 자격을 통해 제어 되는 것을 의미 하는 한 격리 된 팀 사이트입니다.
  
격리 된 팀 사이트를 만들려면 두 가지 주요 단계가 있습니다.
  
### <a name="step-1-design-your-isolated-site"></a>1 단계: 격리 된 사이트를 디자인 합니다.

격리 된 팀 사이트를 디자인 하려면 결정 해야 합니다.
  
- SharePoint 그룹 및 권한 수준입니다.
    
- SharePoint 그룹의 구성원 포함 될 액세스 그룹의 집합입니다.
    
     액세스 그룹의 권장 집합이 사이트 구성원에 대 한 하나, 사이트 뷰어에 대 한 표시 하 고 사이트 관리자를 위한 하나 있습니다.
    
- 여부에 대 한 액세스 그룹 내에서 중첩 된 그룹을 사용 합니다.
    
예, 권장된 그룹 구조 및 사용 권한 수준을 다음과 같습니다.
  
|**SharePoint 그룹**|**사용 권한 수준**|**액세스 그룹 (예)**|
|:-----|:-----|:-----|
|[사이트 이름] 구성원  <br/> |편집  <br/> |[사이트 이름] 구성원  <br/> |
|[사이트 이름] 방문자  <br/> |읽기  <br/> |[사이트 이름] 뷰어  <br/> |
|[사이트 이름] 소유자  <br/> |모든 권한  <br/> |[사이트 이름] 관리자  <br/> |
   
SharePoint 그룹 및 권한 수준을 팀 사이트에 대 한 기본적으로 만들어집니다. 액세스 그룹의 이름을 결정 해야 합니다.
  
디자인 프로세스의 세부 정보에 대 한 [디자인 한 격리 된 SharePoint Online 팀 사이트를](design-an-isolated-sharepoint-online-team-site.md)참조 합니다.
  
### <a name="step-2-deploy-your-isolated-site"></a>2 단계: 격리 된 사이트를 배포 합니다.

격리 된 사이트를 배포 하려면 먼저 해야 합니다.
  
- 사용자 계정 및 각 access 그룹에 추가할 그룹을 결정 합니다.
    
- 액세스 그룹을 만들고 사용자 및 그룹 구성원을 추가 합니다.
    
자세한 단계 [는 격리 된 SharePoint Online 팀 사이트 배포](deploy-an-isolated-sharepoint-online-team-site.md)의 **1 단계** 참조 하십시오.
  
그런 다음 이러한 단계를 SharePoint Online 팀 사이트를 만듭니다.
  
1. SharePoint Online 팀 사이트 (SharePoint Online 관리자)를 관리 하는데 사용 되는 계정 사용 하 여 Office 365 포털에 로그인 합니다. 도움말을 보려면 [Office 365에 로그인 할 위치](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)를 참조 하십시오.
    
2. 타일의 목록에서 **SharePoint**를 클릭 합니다.
    
3. 브라우저의 새 **SharePoint** 탭에서 **+ 사이트 만들기를**클릭 합니다.
    
4. **사이트 만들기** 페이지에서 **팀 사이트**를 클릭 합니다.
    
5. **사이트 이름**개인 팀 사이트에 대 한 이름을 입력 합니다.
    
6. **팀 사이트 설명**대 한 선택적 설명을 입력 합니다.
    
7. **개인정보 보호 설정**선택 **개인-이 사이트에 액세스할 수 있는 구성원만**, **다음**을 클릭 하 고 있습니다.
    
8. 에 **가 수행 하려는 추가?** 창 **마침**을 클릭 합니다.
    
다음으로 새 SharePoint Online 팀 사이트에서 권한을 이러한 단계를 구성 합니다.
  
1. 결정은 이름 UPN (사용자 계정) IT 관리자 또는 다른 사람에 대 한 응답 및 사이트에 대 한 액세스에 대 한 요청을 해결 하는 일을 담당 됩니다 (belindan@contoso.com은 UPN의 예). 쓰기 여기에 해당 UPN: ___ 합니다.
    
2. 도구 모음에서 설정 아이콘을 클릭 한 다음 **사이트 사용 권한**을 클릭 합니다.
    
3. **사이트 사용 권한** 창에서 **고급 사용 권한 설정**을 클릭 합니다.
    
4. 브라우저의 새 **사용 권한** 탭에서 **액세스 요청 설정**을 클릭 합니다.
    
5. **액세스 요청 설정** 대화 상자:
    
  - **사이트 및 개별 파일 및 폴더 공유 허용 구성원** 및 **사이트 구성원 그룹에 다른 사용자를 초대 하도록 허용 구성원** 확인란의 선택을 취소 합니다.
    
  - **액세스에 대 한 모든 요청**에서 1 단계에서 IT 관리자의 UPN을 입력 합니다.
    
  - **확인**을 클릭합니다.
    
6. 브라우저의 **사용 권한** 탭에서 목록에서 **[사이트 이름] 구성원** 을 클릭 합니다.
    
7. **사용자 및 그룹에서** **새로 만들기**를 클릭 합니다.
    
8. **공유** 대화 상자에서이 사이트에 대 한 사이트 구성원 액세스 그룹의 이름을 입력을 선택한 다음 **공유**를 클릭 합니다.
    
9. 브라우저에서 뒤로 단추를 클릭합니다.
    
10. 목록에서 **[사이트 이름] 소유자** 를 클릭 합니다.
    
11. **사용자 및 그룹에서** **새로 만들기**를 클릭 합니다.
    
12. **공유** 대화 상자에서이 사이트에 대 한 사이트 관리자가 액세스 그룹의 이름을 입력을 선택한 다음 **공유**를 클릭 합니다.
    
13. 브라우저에서 뒤로 단추를 클릭합니다.
    
14. 목록에서 **[사이트 이름] 방문자** 를 클릭 합니다.
    
15. **사용자 및 그룹에서** **새로 만들기**를 클릭 합니다.
    
16. **공유** 대화 상자에서이 사이트에 대 한 사이트 뷰어 액세스 그룹의 이름을 입력을 선택한 다음 **공유**를 클릭 합니다.
    
17. 브라우저의 **사용 권한** 탭을 닫습니다.
    
이러한 사용 권한 설정의 결과:
  
- **[사이트 이름] Owners** SharePoint 그룹의 모든 구성원에 **모든 권한** 권한 수준을 가진 사이트 관리자가 액세스 그룹을 포함 합니다.
    
- **[사이트 이름] 구성원** SharePoint 그룹의 모든 구성원에 있는 사용 권한 수준 **편집** 사이트 구성원 액세스 그룹을 포함 합니다.
    
- **[사이트 이름] 방문자** SharePoint 그룹의 모든 구성원에 **읽기** 권한 수준을 가진 사이트 뷰어 액세스 그룹을 포함 합니다.
    
- 다른 구성원을 초대 하는 구성원에 대 한 기능을 사용 하는 사용할 수 없습니다.
    
- 액세스 요청을 비 구성원에 대 한 기능을 사용 합니다.
    
구성 결과는 다음과 같습니다.
  
![격리된 SharePoint Online 팀 사이트에 대한 중요한 수준의 보호입니다.](images/7a6ab9c6-560a-4674-ac39-8175644dbe6f.png)
  
액세스 그룹 중 하나에서 그룹 구성원 자격을 통해 사이트의 구성원은 사이트의 리소스에 안전 하 게 공동 작업 이제 수 있습니다.
  
## <a name="highly-confidential-sharepoint-online-team-sites"></a>기밀 사항이 SharePoint Online 팀 사이트

기밀 사항이 SharePoint Online 팀 사이트는 사용 권한을 팀 사이트와 연결 된 Office 365 그룹의 구성원 이어야 하는 대신 SharePoint 그룹의 구성원 자격을 통해 제어 되는 것을 의미 하는 한 격리 된 팀 사이트입니다.
  
매우 기밀 정보 및 공동 작업에 대 한 격리 된 팀 사이트를 만들려면 두 가지 주요 단계가 있습니다.
  
### <a name="step-1-design-your-isolated-site"></a>1 단계: 격리 된 사이트를 디자인 합니다.

격리 된 팀 사이트를 디자인 하려면 결정 해야 합니다.
  
- SharePoint 그룹 및 권한 수준입니다.
    
- SharePoint 그룹의 구성원 포함 될 액세스 그룹의 집합입니다.
    
     액세스 그룹의 권장 집합이 사이트 구성원에 대 한 하나, 사이트 뷰어에 대 한 표시 하 고 사이트 관리자를 위한 하나 있습니다.
    
- 여부에 대 한 액세스 그룹 내에서 중첩 된 그룹을 사용 합니다.
    
예, 권장된 그룹 구조 및 사용 권한 수준을 다음과 같습니다.
  
|**SharePoint 그룹**|**사용 권한 수준**|**액세스 그룹 (예)**|
|:-----|:-----|:-----|
|[사이트 이름] 구성원  <br/> |편집  <br/> |[사이트 이름] 구성원  <br/> |
|[사이트 이름] 방문자  <br/> |읽기  <br/> |[사이트 이름] 뷰어  <br/> |
|[사이트 이름] 소유자  <br/> |모든 권한  <br/> |[사이트 이름] 관리자  <br/> |
   
SharePoint 그룹 및 권한 수준을 팀 사이트에 대 한 기본적으로 만들어집니다. 액세스 그룹의 이름을 결정 해야 합니다.
  
디자인 프로세스의 세부 정보에 대 한 [디자인 한 격리 된 SharePoint Online 팀 사이트를](design-an-isolated-sharepoint-online-team-site.md)참조 합니다.
  
### <a name="step-2-deploy-your-isolated-site"></a>2 단계: 격리 된 사이트를 배포 합니다.

격리 된 사이트를 배포 하려면 먼저 해야 합니다.
  
- 각 액세스 그룹의 사용자 및 그룹 구성원을 결정
    
- 액세스 그룹을 만들고 사용자 및 그룹 구성원 추가
    
- 액세스 그룹을 사용 하는 격리 된 팀 사이트 만들기
    
자세한 단계 [는 격리 된 SharePoint Online 팀 사이트의 배포](deploy-an-isolated-sharepoint-online-team-site.md)를 참조 합니다.
  
결과의 사용 권한 설정 됩니다.
  
- **[사이트 이름] Owners** SharePoint 그룹의 모든 구성원에 **모든 권한** 권한 수준을 가진 사이트 관리자가 액세스 그룹을 포함 합니다.
    
- **[사이트 이름] 구성원** SharePoint 그룹의 모든 구성원에 있는 사용 권한 수준 **편집** 사이트 구성원 액세스 그룹을 포함 합니다.
    
- **[사이트 이름] 방문자** SharePoint 그룹의 모든 구성원에 **읽기** 권한 수준을 가진 사이트 뷰어 액세스 그룹을 포함 합니다.
    
- 다른 구성원을 초대 하는 구성원에 대 한 기능을 사용 하는 사용할 수 없습니다.
    
- 액세스 요청을 비 구성원에 대 한 기능을 사용 하는 사용할 수 없습니다.
    
구성 결과는 다음과 같습니다.
  
![격리된 SharePoint Online 팀 사이트에 대한 높은 기밀 수준의 보호입니다.](images/196359ab-d7ed-4fcf-97b4-61820a74aca4.png)
  
액세스 그룹 중 하나에서 그룹 구성원 자격을 통해 사이트의 구성원은 사이트의 리소스에 안전 하 게 공동 작업 이제 수 있습니다.
  
## <a name="next-step"></a>다음 단계

[Office 365 레이블 및 DLP 사용 하 여 SharePoint Online 파일 보호](protect-sharepoint-online-files-with-office-365-labels-and-dlp.md)
    
## <a name="see-also"></a>참고 항목

[SharePoint Online 사이트 및 파일의 보안](secure-sharepoint-online-sites-and-files.md)
  
[개발/테스트 환경에서 SharePoint Online 사이트 보호](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[정치적 캠페인, 비영리, 및 기타 민첩 한 조직에 대 한 Microsoft 보안 지침](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[클라우드 채택 및 하이브리드 솔루션](cloud-adoption-and-hybrid-solutions.md)




