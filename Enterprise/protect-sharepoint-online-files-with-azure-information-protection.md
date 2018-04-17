---
title: Azure 정보 보호와 SharePoint Online 파일 보호
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
ms.assetid: 5b9c8e41-25d2-436d-89bb-9aecb9ec2b80
description: '요약: Azure 정보 보호 기밀 사항이 SharePoint Online 팀 사이트의 파일을 보호 하기 위해 적용 됩니다.'
ms.openlocfilehash: 84bd1f48c7051f945e7b851f829421364de2a557
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
---
# <a name="protect-sharepoint-online-files-with-azure-information-protection"></a>Azure 정보 보호와 SharePoint Online 파일 보호

 **요약:** 기밀 사항이 SharePoint Online 팀 사이트의 파일을 보호 하기 위해 Azure 정보 보호 기능을 적용 합니다.
  
이 문서의 단계를 사용 하 여 암호화 및 기밀 사항이 SharePoint Online 팀 사이트의 파일에 대 한 사용 권한을 제공 하는 Azure 정보 보호 기능을 구성 합니다. 암호화 및 사용 권한 보호의 사이트에서 다운로드 하는 경우에 파일을 함께 이동 합니다. 기밀 사항이 SharePoint Online 팀 사이트에 대 한 자세한 내용은 [SharePoint Online 보안 사이트 및 파일을](secure-sharepoint-online-sites-and-files.md)참조 하십시오.
  
> [!NOTE]
> Office 365에 저장된 파일에 Azure Information Protection 암호화가 적용되어 있으면 이 파일의 내용을 처리할 수 없습니다. 즉 공동 작성, eDiscovery, 검색, Delve 및 기타 공동 작업 기능이 작동하지 않습니다. DLP(데이터 손실 방지) 정책은 메타데이터(Office 365 레이블 포함)에만 작동할 수 있지만 파일의 내용(예: 파일 내의 신용 카드 번호)에는 작동할 수 없습니다. 
  
먼저, Office 365 구독에 대 한 [Office 365 관리 센터와 Azure RMS 활성화](https://docs.microsoft.com/information-protection/deploy-use/activate-office365) 의 지침을 따르십시오.
  
다음으로 새 범위가 지정 된 정책 및 보호 및 기밀 사항이 SharePoint Online 팀 사이트의 사용 권한을 하위 레이블을 사용 하 여 Azure 정보 보호를 구성 합니다.
  
1. 보안 관리자 또는 회사 관리자 역할을 가진 계정으로 사용 하 여 Office 365 포털에 로그인 합니다. 도움말을 보려면 [Office 365에 로그인 할 위치](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)를 참조 하십시오.
    
2. 브라우저의 별도 탭에서 포털로 이동 하 여 Azure ([https://portal.azure.com](https://portal.azure.com)).
    
3. 처음으로 Azure 정보 보호를 구성 하는 경우 다음 [지침](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time)을 참조 하십시오.
    
4. 목록 창에서 **서비스를 더**, **정보**를 입력 한 다음 **Azure 정보 보호**를 클릭 합니다.
    
5. **Azure 정보 보호** 블레이드에서를 클릭 **정책 범위 > 새 정책을 추가 +**합니다.
    
6. **정책 이름**에 새 정책의 이름을 입력하고 **설명**에 설명을 입력합니다.
    
7. **이 정책을 가져올 사용자 또는 그룹을 선택합니다 > 사용자/그룹**을 클릭한 후 극비 SharePoint Online 팀 사이트에 대한 사이트 멤버 액세스 그룹을 선택합니다. 
    
8. **선택 > 확인**을 클릭합니다.
    
9. **기밀** 레이블에서 생략 부호(…)를 클릭한 후 **하위 레이블 추가**를 클릭합니다.
    
10. **이름**에 하위 레이블의 이름을 입력하고 **설명**에 하위 레이블에 대한 설명을 입력합니다.
    
11. **이 레이블을 포함하는 문서 및 전자 메일에 대한 권한 설정**에서 **보호**를 클릭합니다.
    
12. **보호** 섹션에서 **Azure(클라우드 키)**를 클릭합니다.
    
13. **보호** 블레이드의 **보호 설정** 아래에서 **+ 권한 추가**를 클릭합니다.
    
14. **권한 추가** 블레이드의 **사용자 및 그룹 지정** 아래에서 **+ 디렉터리 찾아보기**를 클릭합니다.
    
15. **AAD 사용자 및 그룹** 창에서 매우 중요 한 SharePoint Online 팀 사이트에 대 한 사이트 구성원 액세스 그룹을 선택 하 고 **선택**을 클릭 합니다.
    
16. **사전 설정에서 사용 권한을 선택**아래에서 **인쇄**, **복사 및 콘텐츠 추출**및 **앞으로** 확인란의 선택을 취소 합니다.
    
17. 두 번 **확인** 을 클릭 합니다.
    
18. **하위 레이블** 블레이드에서 **저장**을 클릭합니다.
    
19. 새로운 범위 지정 정책 블레이드를 닫습니다.
    
20. **Azure 정보 보호-범위가 지정 된 정책** 블레이드에서 **게시**를 클릭 합니다.
    
기밀 사항이 SharePoint Online 팀 사이트에 대 한 결과 구성입니다.
  
![격리된 SharePoint Online 팀 사이트에 대한 Azure Information Protection 레이블입니다.](images/8cc92aa4-e7bc-4c2f-a4a4-3b034b21aebf.png)
  
이제 문서를 작성하고 Azure Information Protection 및 새로운 레이블을 사용하여 해당 문서를 보호할 준비가 완료되었습니다.
  
장치 또는 Windows 기반 컴퓨터에서 [Azure 정보 보호 클라이언트 설치](https://docs.microsoft.com/information-protection/rms-client/install-client-app) 를 수행 해야 합니다. 스크립트 하 고, 설치를 자동화 또는 사용자가 클라이언트를 수동으로 설치할 수 있습니다. 다음 리소스를 참조 합니다.
  
- [Azure Information Protection의 클라이언트 측면](https://docs.microsoft.com/information-protection/rms-client/use-client)
    
- [Azure Information Protection 클라이언트 설치](https://docs.microsoft.com/information-protection/rms-client/client-admin-guide)
    
- [수동 설치를 위한 다운로드 페이지](https://www.microsoft.com/download/details.aspx?id=53018)
    
설치 되 면 사용자에 게를 실행 하 고 로그인 자신의 Office 365 계정 (예: Microsoft Word) Office 응용 프로그램에서 합니다. 새 **정보 보호** 모음을 사용자가 새 레이블을 선택할 수 있습니다. SharePoint Online 팀 사이트와 그 기밀 파일을 보호 하기 위해 사용 하 여 레이블을 지정 하는 프로그램 사용자에 게 있는지 확인 하십시오.
  
> [!NOTE]
> 극비 SharePoint Online 팀 사이트가 여러 개인 경우, 각 하위 레이블에 대한 권한을 특정 SharePoint Online 팀 사이트의 사이트 멤버 액세스 그룹으로 설정하고 위의 설정을 사용하여 하위 레이블이 포함된 Azure Information Protection 범위 지정 정책 여러 개를 만들어야 합니다. 
  
## <a name="see-also"></a>참고 항목

[SharePoint Online 사이트 및 파일 보호](secure-sharepoint-online-sites-and-files.md)
  
[개발/테스트 환경의 SharePoint Online 사이트 보호](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[정치적 캠페인, 비영리 조직 및 기타 기밀 조직에 대한 Microsoft 보안 지침](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[클라우드 채택 및 하이브리드 솔루션](cloud-adoption-and-hybrid-solutions.md)




