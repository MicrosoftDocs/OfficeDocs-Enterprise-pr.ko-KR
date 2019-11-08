---
title: Office 365 개발/테스트 환경용 고급 eDiscovery
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: d4c49a6f-abfd-4d68-b353-259b4eefb033
description: '요약: Office 365 개발/테스트 환경의 샘플 데이터로 Office 365 고급 eDiscovery를 구성하고 보여 줍니다.'
ms.openlocfilehash: dbd03c1a75b63f4fdaff49db47c8d415f267aaf3
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2019
ms.locfileid: "38030672"
---
# <a name="advanced-ediscovery-for-your-office-365-devtest-environment"></a>Office 365 개발/테스트 환경용 고급 eDiscovery

 **요약:** Office 365 개발/테스트 환경의 샘플 데이터로 Office 365 고급 eDiscovery를 구성하고 보여 줍니다.
  
Office 365 Advanced eDiscovery를 사용 하면 전자 메일 및 문서를 비롯 하 여 Office 365에 저장 된 데이터를 통해 관련 정보를 신속 하 게 찾고 분석할 수 있습니다. 특히 소송 상황에서 엄청난 시간과 비용을 절약할 수 있습니다. 자세한 내용은 [Office 365 고급 eDiscovery](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4)를 참조하세요.
  
이 기사의 지침에 따라 가상 계약 분쟁에 대한 작은 데이터 집합을 만들고 고급 eDiscovery로 이를 분석합니다.
  
> [!TIP]
> [여기](https://aka.ms/catlgstack)를 클릭하여 Office 365 테스트 랩 가이드 스택의 모든 문서에 대한 가상 맵을 확인할 수 있습니다.
  
## <a name="phase-1-create-your-office-365-devtest-environment"></a>1단계: Office 365 개발/테스트 환경 만들기

최소 요구 사항에 따라 간단한 방법으로 고급 eDiscovery를 테스트 하려면 [Office 365 개발/테스트 환경의](office-365-dev-test-environment.md)2 단계 및 3 단계의 지침을 따릅니다.
  
시뮬레이트된 엔터프라이즈에서 고급 eDiscovery를 테스트 하려면 [Office 365 개발/테스트 환경에 대 한 DirSync](dirsync-for-your-office-365-dev-test-environment.md)의 지침을 따르세요.
  
> [!NOTE]
> 고급 eDiscovery를 테스트 하는 경우에는 AD DS (Active Directory 도메인 서비스) 포리스트의 인터넷 및 디렉터리 동기화에 연결 된 시뮬레이트된 인트라넷을 포함 하는 시뮬레이트된 엔터프라이즈 환경이 필요 하지 않습니다. 일반적인 조직을 나타내는 환경에서 테스트 및 시험을 수행할 수 있도록 여기에 옵션으로 제공 됩니다. 
  
## <a name="phase-2-create-example-data-for-advanced-ediscovery"></a>2단계: 고급 eDiscovery의 예제 데이터 만들기

이 프로시저에서는 나중에 고급 eDiscovery 사례에서 분석할 전자 메일 메시지를 만듭니다.
  
1. Internet Explorer를 열고 [https://outlook.com](https://outlook.com) [Office 365 개발/테스트 환경](office-365-dev-test-environment.md)2 단계에서 만든 Outlook 계정에 로그인 합니다.
    
  - 경량 개발/테스트 환경을 사용하는 경우 Internet Explorer의 비공개 세션을 열고 로컬 컴퓨터에서 로그인합니다.
    
  - 시뮬레이트된 엔터프라이즈 개발/테스트 환경을 사용 하는 경우 Azure portal ([https://portal.azure.com](https://portal.azure.com))을 사용 하 여 client1 가상 컴퓨터에 연결한 다음 client1에서 로그인 합니다.
    
2. **Outlook 메일** 탭에서 **새 전자 메일**을 클릭합니다.
    
3. **To To**에 평가판 구독의 User6 계정 전자 메일 주소 (user6@를 입력 **합니다.**<organization name> **. onmicrosoft.com**)
    
4. 제목에 **테스트 전자 메일 1**을 입력합니다.
    
5. 본문에 **Tailspin 계약 초안**을 입력한 다음 **보내기**를 클릭합니다.
    
6. **Outlook 메일** 탭에서 **새 전자 메일**을 클릭합니다.
    
7. **받는 사람**에 평가판 구독의 User6 계정 전자 메일 주소를 입력합니다.
    
8. 제목에 **테스트 전자 메일 2**를 입력합니다.
    
9. 본문에 **Tailspin 점심 회의**를 입력한 다음 **보내기**를 클릭합니다.
    
10. **Outlook 메일** 탭에서 **새 전자 메일**을 클릭합니다.
    
11. **받는 사람**에 평가판 구독의 User6 계정 전자 메일 주소를 입력합니다.
    
12. 제목에 **테스트 전자 메일 3**을 입력합니다.
    
13. 본문에 **Tailspin 계약 불일치**를 입력한 다음 **보내기**를 클릭합니다.
    
14. 오른쪽 위 모서리에 있는 사용자 아이콘을 클릭한 다음 **로그아웃**을 클릭합니다.
    
15. 새 탭을 열고 평가판 구독의 User6 계정 계정 이름과 암호를 사용[https://www.office.com](https://www.office.com)하 여 Office 365 portal ()에 로그인 합니다.
    
16. **Office 365 포털** 탭에서 **메일**을 클릭합니다.
    
17. **User6-outlook** 탭에서 User6가 Outlook 전자 메일 계정에서 세 개의 전자 메일을 모두 받았는지 확인 합니다.
    
18. User6의 **Office 365 포털 탭**으로 다시 전환합니다.
    
19. 오른쪽 위 모서리에 있는 사용자 아이콘을 클릭한 다음 **로그아웃**을 클릭합니다.
    
이 프로시저에서는 나중에 고급 eDiscovery 사례에서 분석할 두 개의 Word 문서를 만듭니다.
  
1. **Office** 페이지에서 **로그인**을 클릭하고 전역 관리자 계정의 자격 증명을 사용하여 로그인합니다.
    
2. 새 탭에서 프로덕션 SharePoint 사이트의 URL에 액세스 합니다. **https://** <fictional organization name> **. sharepoint.com/sites/production**
    
3. **프로덕션 사이트 모음** 탭의 **문서**에서 **새 문서 > Word 문서**를 클릭합니다.
    
4. **Word** 페이지에서 **Tailspin 초안 계약**을 입력 하 고 제목에 **저장** 됨이 표시 될 때까지 기다린 다음 **Word** 페이지 탭을 닫습니다.
    
5. **프로덕션 사이트 모음** 탭의 **문서**에서 **새 문서 > Word 문서**를 클릭합니다.
    
6. **Word** 탭에서 **Tailspin 계약 분쟁 정보**를 입력 하 고 제목에 **저장** 됨이 표시 되 면 **Word** 탭을 닫습니다.
    
7. **프로덕션 사이트 모음** 탭의 문서 목록에 **문서** 및 **문서1**이 표시됩니다.
    
8. **프로덕션 사이트 모음** 탭을 닫습니다.
    
## <a name="phase-3-use-advanced-ediscovery-for-a-legal-dispute"></a>3 단계: 법적 분쟁에 고급 eDiscovery 사용

안타깝게도 조직과 Tailspin Toys 간의 계약 분쟁이 법적 조치가 필요한 시점에 도달했습니다. 이 절차에서는 "Tailspin 계약" 텍스트를 포함 하는 전자 메일 및 문서를 검색 하 고 분석 하기 위한 고급 eDiscovery 사례를 만들고 구성 합니다.
  
고급 eDiscovery를 사용하는 프로세스는 다음과 같습니다.
  
- 보안 &amp; 및 준수 센터에서 검색을 만들고 결과를 분석 한 다음 고급 eDiscovery의 결과를 준비 합니다.
    
- 고급 eDiscovery에서 사례를 만들고 구성한 다음 검색 결과를 분석합니다.
    
이 절차에서는 보안 &amp; 및 준수 센터에서 "Tailspin 계약"에 대 한 검색을 만들고 결과를 검토 한 다음 고급 eDiscovery의 결과를 준비 합니다.
  
1. **Office 365 포털** 탭에서 **관리자**를 클릭합니다.
    
2. 관리 센터 탭의 왼쪽 탐색 창에서 **관리 센터 > 준수**를 클릭합니다.
    
3. **보안 &amp; 및 준수** 탭에서 **사용 권한을**클릭 합니다.
    
4. **사용 권한** 목록에서 **조직 관리**를 두 번 클릭합니다.
    
5. **역할 그룹** 창의 **구성원**에서 +기호를 클릭합니다.
    
6. **구성원 선택** 창에서 관리자 계정의 이름을 두 번 클릭한 다음 **확인**을 클릭합니다.
    
7. **역할 그룹** 창에서 **저장**을 클릭합니다.
    
8. **사용 권한** 목록에서 **eDiscovery 관리자**를 두 번 클릭합니다.
    
9. **역할 그룹** 창의 **eDiscovery 관리자**에서 +기호를 클릭합니다.
    
10. **구성원 선택** 창에서 관리자 계정의 이름을 두 번 클릭한 다음 **확인**을 클릭합니다.
    
11. **역할 그룹** 창에서 **저장**을 클릭합니다.
    
12. 왼쪽 탐색 창에서 **검색 &amp; 조사 > 콘텐츠 검색**을 클릭 합니다.
    
13. +기호를 클릭하여 검색을 추가합니다.
    
14. **새 검색** 창에서 **이름**에 **Tailspin 계약 검색**을 입력합니다.
    
15. **어느 위치를 검색하시겠습니까?** 에서 **전체 검색**을 클릭하고 **Exchange**, **SharePoint** 및 **공용 폴더**를 선택한 후 **다음**을 클릭합니다.
    
16. **무엇을 검색하시겠습니까?** 에서 **Tailspin 계약**을 입력한 다음 **검색**을 클릭합니다.
    
17. 검색 목록에서 **Tailspin 계약 검색** 이름을 클릭합니다.
    
18. **Tailspin 계약 검색** 창의 **결과**에서 **검색 결과 미리 보기**를 클릭합니다. 프로덕션 SharePoint 사이트에서 두 문서 ( **문서** **및 문서**1)를 나열 하는 창, **테스트 전자 메일** 및 테스트 전자 메일 **3** 전자 메일을 User6에 게 표시 해야 합니다. 창을 닫습니다.
    
19. **콘텐츠 검색** 창의 **고급 eDiscovery를 사용한 결과 분석**에서 **분석 결과 미리 보기**를 클릭합니다.
    
20. **Tailspin 계약 검색의 검색 결과 준비** 창에서 **준비**를 클릭하고 완료될 때까지 기다립니다.
    
이 프로시저에서는 고급 eDiscovery의 새 사례를 만들고 Tailspin 계약 검색 결과를 분석합니다.
  
1. 왼쪽 탐색 창의 ** &amp; 검색 조사**에서 **eDiscovery** 를 클릭 합니다.
    
2. **eDiscovery** 창에서 **고급 eDiscovery로 이동**을 클릭합니다.
    
3. **고급 eDiscovery** 탭에서 +기호를 클릭하여 새 사례를 추가합니다. 
    
4. **사례 추가** 창에서 **이름**에 **Tailspin 계약 분쟁**을 입력한 다음 **확인**을 클릭합니다. 사례가 다 만들어질 때까지 기다립니다.
    
5. 목록에서 **Tailspin 계약 분쟁** 사례를 두 번 클릭합니다. 
    
6. **컨테이너** 목록에서 **Tailspin 계약 검색** 컨테이너를 클릭 한 다음 **프로세스**를 클릭 합니다. 처리가 완료될 때까지 기다립니다.
    
7. 창 하단에 **프로세스: 완료됨**이 표시되면 왼쪽 탐색 창에서 **프로세스 요약**을 클릭하여 요약을 확인합니다.
    
8. 위쪽 탐색 창에서 **분석**을 클릭합니다.
    
9. **설정** 페이지에 있는 **테마**의 **최대 테마 수**에 **3**을 입력합니다.
    
10. **분석**을 클릭하고 완료할 때까지 기다립니다. 대상 인구, 문서, 전자 메일 및 첨부 파일을 분석한 일련의 원형 차트가 표시됩니다. 자세한 내용은 [분석 결과 보기](https://support.office.com/article/Viewing-Analyze-results-5974f3c2-89fe-4c5f-ac7b-57f214437f7e)를 참조 하세요.
    
이제 이 환경을 사용하여 새 콘텐츠, 새 검색 및 사례를 만들고 Office 365의 고급 eDiscovery를 추가로 실험할 수 있습니다.
  
## <a name="see-also"></a>참고 항목

[클라우드 도입 TLG(테스트 랩 가이드)](cloud-adoption-test-lab-guides-tlgs.md)
  
[기본 구성 개발/테스트 환경](base-configuration-dev-test-environment.md)
  
[Office 365 개발/테스트 환경](office-365-dev-test-environment.md)
  
[Office 365 개발/테스트 환경용 DirSync](dirsync-for-your-office-365-dev-test-environment.md)
  
[클라우드 도입 및 하이브리드 솔루션](cloud-adoption-and-hybrid-solutions.md)

[Office 365 Advanced eDiscovery](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4)


