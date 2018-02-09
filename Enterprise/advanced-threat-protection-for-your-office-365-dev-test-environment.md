---
title: "Office 365 개발/테스트 환경용 Advanced Threat Protection"
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
ms.assetid: 51019757-20ac-498c-b51e-cae6d41a8c08
description: "요약: 구성 및 Office 365 개발/테스트 환경에서 Office 365 고급 위협 보호 기능을 시연 합니다."
ms.openlocfilehash: bc703bd01f3430a01810795b9d2ccea9e4ac9bc0
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/09/2018
---
# <a name="advanced-threat-protection-for-your-office-365-devtest-environment"></a>Office 365 개발/테스트 환경용 Advanced Threat Protection

 **요약:** Office 365 개발/테스트 환경에서 Office 365 고급 위협 보호 시연 및 구성 합니다.
  
Office 365 고급 위협 보호 (ATP) 기능의 Exchange Online Protection EOP ()는 데 도움이 되는 전자 메일에서 맬웨어를 유지 됩니다. ATP와 Exchange 관리 센터 (EAC) 또는 보안 정책을 만듭니다 &amp; 사용자에 게 링크 또는 하지 악의적으로 식별 되는 전자 메일에서 첨부 파일에 액세스할 수 있도록 하는 준수 센터입니다. 자세한 내용은 [안전한 첨부 파일 및 안전 링크에 대 한 고급 위협 보호](https://technet.microsoft.com/library/mt148491%28v=exchg.150%29.aspx)를 참조 하십시오.
  
이 문서의 지침을 사용하여 Office 365 평가판 구독의 ATP를 구성하고 테스트할 수 있습니다.
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>1단계: 경량 또는 시뮬레이트된 엔터프라이즈 Office 365 개발/테스트 환경을 구축합니다.

최소 요구 사항을 경량 방식으로 ATP를 테스트 하려면 2와 [Office 365 개발/테스트 환경](office-365-dev-test-environment.md)의 3 단계에서 지침을 따릅니다.
  
ATP 시뮬레이션 된 엔터프라이즈에서 테스트 하려는 경우 [Office 365 개발/테스트 환경에 대 한 디렉터리 동기화](dirsync-for-your-office-365-dev-test-environment.md)의 지시를 따릅니다.
  
> [!NOTE]
> ATP 테스트에는 시뮬레이트된 엔터프라이즈 개발/테스트 환경이 필요하지 않습니다. 해당 환경에는 Windows Server AD 포리스트의 디렉터리 동기화 및 인터넷에 연결된 시뮬레이트된 인트라넷이 포함되어 있습니다. 여기서는 옵션으로 제공되므로 ATP를 테스트하고 일반적인 조직을 나타내는 환경에서 실험할 수 있습니다. 
  
## <a name="phase-2-demonstrate-the-default-email-delivery-behavior-of-office-365"></a>2 단계: Office 365의 기본 전자 메일 전달 동작을 시연

이 단계에서는 ATP 정책을 구성하기 전에 잠재적인 악성 전자 메일이 차단 또는 완화되지 않고 Office 365 사서함으로 배달될 수 있음을 보여 줍니다.
  
1. Internet Explorer를 열고 [Office 365 개발/테스트 환경](office-365-dev-test-environment.md)중 2 단계에서에서 만든 Outlook 계정에 로그인 합니다.
    
  - 경량 Office 365 개발/테스트 환경을 사용하는 경우 Internet Explorer의 비공개 세션을 열고 로컬 컴퓨터에서 로그인합니다.
    
  - 시뮬레이션 된 엔터프라이즈 Office 365 개발/테스트 환경을 사용 하는 경우 [Azure 포털](https://portal.azure.com) 을 사용 하 여 CLIENT1 가상 컴퓨터에 연결한 다음 CLIENT1에서 로그인 합니다.
    
2. 메모장을 실행하고 일부 텍스트를 입력합니다.
    
3. **GetKeys.js**로 문서 폴더에 파일을 저장 합니다.
    
4. Internet Explorer의 Outlook 메일 탭에서 **새로 만들기**를 클릭 합니다.
    
5. (영문) **를**, 평가판 구독에 Office 365 전역 관리자 이름의 전자 메일 주소를 입력 합니다.
    
6. 주제에 대 한 **새 키**를 입력 합니다.
    
7. 본문에 **다음은 파일을**입력 합니다.
    
8. **연결**, **getKeys.js** 문서 폴더에서를 두번클릭 하 고 **복사본으로 연결**클릭 **보내기**를 클릭 합니다.
    
9. **새**를 클릭 합니다.
    
10. (영문) **를**, 평가판 구독에 Office 365 전역 관리자 이름의 전자 메일 주소를 입력 합니다.
    
11. 주제에 대 한 **새로운 웹사이트 출장**을 입력 합니다.
    
12. 본문에 **다른 사람이 전달한이 사이트를**입력 합니다.
    
13. 본문에 **이 사이트** 텍스트를 선택 하 고 도구 모음에서 하이퍼링크 아이콘을 클릭 합니다.
    
14. **URL** **http://www.spamlink.contoso.com/**입력, **확인**을 클릭 하 고 **보내기**를 클릭 합니다.
    
15. 개인 검색 모드에서 Internet Explorer의 별도 인스턴스를 열고 Office 365 포털 ([https://portal.office.com](https://portal.office.com))로 이동 전역 관리자 계정 사용 하 여 Office 365 평가판 구독에 로그인 합니다.
    
16. 주 포털 페이지에서 앱 타일을 클릭 하 고 **메일**을 클릭 합니다.
    
17. 받은 편지함에서 제목에 **새 키**와 메시지를 클릭 합니다.
    
18. 정크 메일 폴더에서 **새로운 웹사이트 출장**주체와 메시지를 클릭 합니다. 메시지를 내에서 **이 사이트** 링크를 클릭 합니다. "Oops 나타나야 합니다.! Internet Explorer 찾을 수 없습니다 spamlink.contoso.com."페이지입니다. 해당 위치에 없는 웹 페이지 때문에 올바른 결과입니다.
    
이러한 위험할 수 있는 전자 메일을 모두 성공적으로 배달 된 알 수 있습니다. **새 키에** 전자 메일 검색 되지 않은 맬웨어를 포함 될 수 및 **새로운 웹사이트 출장을** 전자 메일에서 위험할 수 있는 링크를 클릭 하는 사용자가 허용 합니다.
  
## <a name="phase-3-configure-safe-attachment-and-safe-links-policies-for-atp"></a>3단계: ATP의 안전한 첨부 파일 및 안전한 링크 정책 구성

이 단계에서는 안전한 첨부 파일 정책을 만들고 구성하여 잠재적인 악성 첨부 파일이 배달되지 않도록 하고 안전한 링크 정책을 통해 사용자가 잠재적으로 안전하지 않은 URL로 이동할 수 없도록 합니다.
  
1. Internet Explorer의 **Microsoft Office 홈** 탭에서 **관리** 타일을 클릭 합니다.
    
2. 왼쪽 탐색 영역에서 **관리 센터**, 및 **Exchange**를 클릭 합니다.
    
3. Exchange 관리 센터 탭의 왼쪽 탐색 영역에서 **고급 위협 요소**를 클릭 합니다.
    
4. **안전한 첨부 파일** 탭을 클릭 하 고 더하기 기호를 클릭 합니다.
    
5. **이름** **새 안전한 첨부 파일 정책** 창에서 **안전한 첨부 파일 정책-블록을**입력 합니다.
    
6. **알 수 없는 맬웨어 응답 안전한 첨부 파일**대 한 **차단**을 클릭 합니다.
    
7. **검색에서 첨부 파일을 리디렉션**에에 대 한 **리디렉션 사용** 을 클릭 하 고 Office 365 전역 관리자 계정의 전자 메일 주소를 입력 합니다.
    
8. **에 적용 되며**대 한 아래쪽 화살표를 클릭 하 고 **받는 사람 도메인은**를 클릭 합니다. 창에서 조직 이름 (예: contoso.onmicrosoft.com 형식)를 클릭 한 다음 **확인**을 클릭 합니다.
    
9. **저장**을 클릭 합니다. 업데이트 된 후 새 나타납니다 및 **안전한 첨부 파일 정책-블록을**사용 하도록 설정 합니다.
    
10. **안전한 링크** 탭을 클릭 하 고 더하기 기호를 클릭 합니다.
    
11. **이름** **새 안전한 링크 정책** 창에서 **안전한 링크 정책**을 입력 합니다.
    
12. **메시지에 알 수 없는 위험할 수 있는 Url에 대 한 작업을 선택**하는 것에 대 한 **에서**클릭 하 고 **사용자가 클릭 하 여 원래 URL을을 허용 하지 않습니다**를 선택 합니다.
    
13. **에 적용 되며**대 한 아래쪽 화살표를 클릭 하 고 **받는 사람 도메인은**를 클릭 합니다. 창에서 조직 이름 (예: contoso.onmicrosoft.com 형식)를 클릭 한 다음 **확인**을 클릭 합니다.
    
14. **저장**을 클릭 합니다. 새 참조 해야 하 고이 정보를 **안전한 링크 정책**를 활성화 합니다.
    
## <a name="phase-4-show-atp-in-action"></a>4단계: 실행되는 ATP 표시

이 단계에서는 ATP에서 잠재적인 악성 전자 메일을 처리하는 방법을 보여 줍니다.
  
1. Internet Explorer의 왼쪽된 탐색 영역에서 2 단계에서에서 전자 메일을 보내는 데 사용 하는 인스턴스에서 클릭 **보낸편지함.**
    
2. **새 키**라는 제목의 전자 메일을 클릭 하 고 아래쪽 화살표 아이콘을 클릭 **전달**을 클릭 합니다.
    
3. (영문) **를**, 새 메시지에 대 한 평가판 구독에 Office 365 전역 관리자 이름의 전자 메일 주소를 입력 하 고 **보내기**를 클릭 합니다.
    
4. **새로 만들기 출장 웹사이트**라는 제목의 전자 메일, 아래쪽 화살표 아이콘을 클릭 하 고 **전체 회신**을 클릭 **보내기**를 클릭 합니다.
    
5. 3 단계에서에서 ATP 정책을 구성 하는 사용 되는 Internet Explorer의 인스턴스에서 Exchange 관리 센터 탭을 클릭, 앱 타일을 클릭 하 고 **메일**을 클릭 합니다. 받은 편지함의 두 새 전자 메일 메시지를 볼 수 있습니다.
    
  - 1 이라는 **펌웨어: 새 키**
    
  - 1 이라는 **펌웨어: 새 출장 웹사이트**
    
6. 라는 제목의 전자 메일 메시지를 열고 **펌웨어: 새 출장 웹사이트** **이 사이트** 링크를 클릭 하 고 있습니다. "이이 웹사이트 분류 않은 악성 소프트웨어로." 페이지를 참조 해야 합니다. ATP 인해 없음을 하면 위험할 수 있는 웹사이트에 액세스 하지 못하도록 보여줍니다.
    
7. 왼쪽 탐색 영역에서 Internet Explorer의 Exchange 관리 센터 탭에서 **메일 흐름**을 클릭 합니다.
    
8. **메시지 추적** 탭을 클릭 하 고 **검색**을 클릭 합니다.
    
9. **메시지 추적 결과** 창에서 **새 키에**제목 포함 된 메시지를 두번클릭 합니다. 이 메시지가 받은 편지 함으로 배달 되었습니다. 이 창을 닫습니다.
    
10. **새로 만들기 출장 웹사이트**제목 포함 된 메시지를 두번클릭 합니다. 이 메시지가 받은 편지 함으로 배달 되었습니다. 이 창을 닫습니다.
    
11. 제목 포함 된 메시지를 두번클릭 **펌웨어: 새 키에**합니다. 이 메시지 된 ATP에서 처리 하 고 다음 편지 함으로 배달 하는 방법을 note 합니다. 이 창을 닫습니다.
    
    > [!NOTE]
    > 안전한 첨부 파일 정책의 목적 악성 코드에 대 한 첨부 파일을 검색을 시작 했습니다. GetKeys.js 첨부 파일에는 악성 코드가 포함 될를 결정 하지 되었으므로 하도록 허용 되었습니다. 이 단계에서는 ATP 첨부 파일의 검색을 수행 않은 보여줍니다. 
  
12. 제목 포함 된 메시지를 두번클릭 **펌웨어: 새 출장 웹사이트**합니다. 이 메시지는 받은 편지함에 성공적으로 배달 하는 내용의 합니다.
    
이제 이 환경을 사용하여 새 정책을 만들고 ATP를 실험할 수 있습니다.
  
> [!TIP]
> 클릭 [여기](http://aka.ms/catlgstack) 에 한 맵이 하나의 Microsoft 클라우드 테스트 랩 가이드 스택의 모든 문서를 시각적으로 표시 합니다.
  
## <a name="see-also"></a>참고 항목

[클라우드 도입 TLG(테스트 랩 가이드)](cloud-adoption-test-lab-guides-tlgs.md)
  
[기본 구성 개발/테스트 환경](base-configuration-dev-test-environment.md)
  
[Office 365 개발/테스트 환경](office-365-dev-test-environment.md)
  
[Office 365 개발/테스트 환경용 DirSync](dirsync-for-your-office-365-dev-test-environment.md)
  
[Office 365 개발/테스트 환경에 대 한 클라우드 응용 프로그램 보안](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[클라우드 채택 및 하이브리드 솔루션](cloud-adoption-and-hybrid-solutions.md) 

[안전한 첨부 파일 및 안전 링크에 대 한 고급 위협 보호](https://support.office.com/article/Office-365-Advanced-Threat-Protection-E100FE7C-F2A1-4B7D-9E08-622330B83653)


