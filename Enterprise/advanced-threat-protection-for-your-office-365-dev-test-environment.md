---
title: Office 365 개발/테스트 환경용 Advanced Threat Protection
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 51019757-20ac-498c-b51e-cae6d41a8c08
description: '요약: Office 365 개발/테스트 환경의 Office 365 Advanced Threat Protection을 구성하고 보여 줍니다.'
ms.openlocfilehash: 53bff386490ed9647a511f75c997cb91b0acc181
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/30/2019
ms.locfileid: "33490154"
---
# <a name="advanced-threat-protection-for-your-office-365-devtest-environment"></a>Office 365 개발/테스트 환경용 Advanced Threat Protection

 **요약:** Office 365 개발/테스트 환경의 Office 365 Advanced Threat Protection을 구성하고 보여 줍니다.
  
Office 365 ATP(Advanced Threat Protection)는 EOP(Exchange Online Protection)의 기능으로 전자 메일에서 맬웨어를 차단합니다. ATP를 사용 하 여 EAC (Exchange 관리 센터) 또는 보안 &amp; 및 준수 센터에서 사용자가 악성이 아닌 것으로 확인 된 전자 메일의 링크나 첨부 파일에만 액세스할 수 있도록 하는 정책을 만듭니다. 자세한 내용은 [안전한 첨부 파일 및 안전한 링크를 위한 Advanced Threat Protection](https://technet.microsoft.com/library/mt148491%28v=exchg.150%29.aspx)를 참조하세요.
  
이 문서의 지침을 사용하여 Office 365 평가판 구독의 ATP를 구성하고 테스트할 수 있습니다.
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>1단계: 경량 또는 시뮬레이트된 엔터프라이즈 Office 365 개발/테스트 환경을 구축합니다.

최소 요구 사항의 간단한 방식으로 ATP를 테스트 하려면 [Office 365 개발/테스트 환경의](office-365-dev-test-environment.md)2 단계 및 3 단계의 지침을 따릅니다.
  
시뮬레이트된 엔터프라이즈에서 ATP를 테스트 하려면 [Office 365 개발/테스트 환경에 대 한 DirSync](dirsync-for-your-office-365-dev-test-environment.md)의 지침을 따르세요.
  
> [!NOTE]
> ATP 테스트에는 AD DS (Active directory 도메인 서비스) 포리스트의 인터넷 및 디렉터리 동기화에 연결 된 시뮬레이트된 인트라넷을 포함 하는 시뮬레이트된 엔터프라이즈 개발/테스트 환경이 필요 하지 않습니다. 이 기능은 나중에 일반적인 조직을 나타내는 환경에서 ATP를 테스트 하 고 시험해 볼 수 있도록 옵션으로 제공 됩니다. 
  
## <a name="phase-2-demonstrate-the-default-email-delivery-behavior-of-office-365"></a>2 단계: Office 365의 기본 전자 메일 배달 동작을 보여 줍니다.

이 단계에서는 ATP 정책을 구성하기 전에 잠재적인 악성 전자 메일이 차단 또는 완화되지 않고 Office 365 사서함으로 배달될 수 있음을 보여 줍니다.
  
1. Internet Explorer를 열고 [Office 365 개발/테스트 환경](office-365-dev-test-environment.md)2 단계에서 만든 Outlook 계정에 로그인 합니다.
    
  - 경량 Office 365 개발/테스트 환경을 사용하는 경우 Internet Explorer의 비공개 세션을 열고 로컬 컴퓨터에서 로그인합니다.
    
  - 시뮬레이트된 enterprise Office 365 개발/테스트 환경을 사용 하는 경우 [Azure portal](https://portal.azure.com) 을 사용 하 여 client1 가상 컴퓨터에 연결한 다음, client1에서 로그인 합니다.
    
2. 메모장을 실행하고 일부 텍스트를 입력합니다.
    
3. 파일을 **getKeys.js**로 문서 폴더에 저장합니다.
    
4. Internet Explorer의 Outlook 메일 탭에서 **새 전자 메일**을 클릭합니다.
    
5. **받는 사람**에 평가판 구독 Office 365 전역 관리자 이름의 전자 메일 주소를 입력합니다.
    
6. 제목에 **새 키**를 입력합니다.
    
7. 본문에 **파일 전달**을 입력합니다.
    
8. **첨부**를 클릭하고 문서 폴더에서 **getKeys.js**를 두 번 클릭하고 **복사본으로 첨부**를 클릭한 다음 **보내기**를 클릭합니다.
    
9. **새로 만들기**를 클릭합니다.
    
10. **받는 사람**에 평가판 구독 Office 365 전역 관리자 이름의 전자 메일 주소를 입력합니다.
    
11. 제목에 **새 여행 웹 사이트**를 입력합니다.
    
12. 본문에 **이 사이트를 전달받았음**을 입력합니다.
    
13. 본문에 **이 사이트** 텍스트를 선택하고 도구 모음에 하이퍼링크 아이콘을 클릭합니다.
    
14. **URL**에 입력 **http://www.spamlink.contoso.com/** 하 고 **확인**을 클릭 한 다음 **보내기를**클릭 합니다.
    
15. 전용 탐색 모드에서 별도의 Internet Explorer 인스턴스를 열고 Microsoft 365 관리 센터 ([https://admin.microsoft.com](https://admin.microsoft.com))로 이동한 후 전역 관리자 계정으로 Office 365 평가판 구독에 로그인 합니다.
    
16. 기본 포털 페이지에서 앱 타일을 클릭한 다음 **메일**을 클릭합니다.
    
17. 받은 편지함에서 제목이 **새 키**인 메시지를 클릭합니다.
    
18. 정크 메일 폴더에서 제목 **새 여행 웹 사이트가**있는 메시지를 클릭 합니다. 메시지 내에서 **이 사이트** 링크를 클릭 합니다. "죄송 합니다. Internet Explorer에서 spamlink.contoso.com를 찾을 수 없습니다. " 페이지. 해당 위치에 웹 페이지가 없기 때문에이 결과가 올바른 결과입니다.
    
이러한 잠재적인 악성 전자 메일이 모두 배달되었습니다. **새 키** 전자 메일에 검색되지 않은 맬웨어가 포함될 수 있으며 사용자는 **새 여행 웹 사이트** 전자 메일의 잠재적인 악성 링크를 클릭할 수 있습니다.
  
## <a name="phase-3-configure-safe-attachment-and-safe-links-policies-for-atp"></a>3단계: ATP의 안전한 첨부 파일 및 안전한 링크 정책 구성

이 단계에서는 안전한 첨부 파일 정책을 만들고 구성하여 잠재적인 악성 첨부 파일이 배달되지 않도록 하고 안전한 링크 정책을 통해 사용자가 잠재적으로 안전하지 않은 URL로 이동할 수 없도록 합니다.
  
1. Internet Explorer의 **Microsoft Office 홈** 탭에서 **관리** 타일을 클릭 합니다.
    
2. 왼쪽 창에서 **관리 센터**를 클릭한 다음 **Exchange**를 클릭합니다.
    
3. Exchange 관리 센터 탭의 왼쪽 탐색 창에서 **고급 위협**을 클릭합니다.
    
4. **안전한 첨부파일** 탭을 클릭한 다음 + 기호를 클릭합니다.
    
5. **새 안전 첨부 파일 정책** 창의 **이름**에 **안전한 첨부 파일 정책 차단을**입력 합니다.
    
6. **안전한 첨부 파일 알 수 없는 맬웨어 응답**에서 **차단을**클릭 합니다.
    
7. **검색에 첨부 파일 리디렉션**에서 **리디렉션 사용**을 클릭하고 Office 365 전역 관리자 계정의 전자 메일 주소를 입력합니다.
    
8. **적용 대상**에서 아래쪽 화살표를 클릭한 다음 **받는 사람 도메인이 다음과 같음**을 클릭합니다. 창에서 조직 이름 (예: contoso.onmicrosoft.com)을 클릭 하 고 **확인**을 클릭 합니다.
    
9. **저장**을 클릭합니다. 업데이트 후에는 새로운 및 사용 가능한 **안전한 첨부 파일 정책 블록이**표시 됩니다.
    
10. **안전한 링크** 탭을 클릭한 다음 + 기호를 클릭합니다.
    
11. **새 안전한 링크 정책** 창의 **이름**에 **안전한 링크 정책**을 입력합니다.
    
12. **메시지에서 알려지지 않은 잠재적인 악성 URL에 대한 작업 선택**에서 **설정**을 클릭한 다음 **사용자가 원래 URL을 클릭하여 이동하도록 허용하지 않음**을 선택합니다.
    
13. **적용 대상**에서 아래쪽 화살표를 클릭한 다음 **받는 사람 도메인이 다음과 같음**을 클릭합니다. 창에서 조직 이름 (예: contoso.onmicrosoft.com)을 클릭 하 고 **확인**을 클릭 합니다.
    
14. **저장**을 클릭합니다. 사용 가능한 새로운 **안전한 링크 정책**이 표시됩니다.
    
## <a name="phase-4-show-atp-in-action"></a>4단계: 실행되는 ATP 표시

이 단계에서는 ATP에서 잠재적인 악성 전자 메일을 처리하는 방법을 보여 줍니다.
  
1. 2 단계에서 전자 메일을 보내는 데 사용한 Internet Explorer의 인스턴스에서 왼쪽 탐색 영역의 보낸 편지함을 클릭 합니다 **.**
    
2. **새 키**제목의 전자 메일을 클릭 하 고 아래쪽 화살표 아이콘을 클릭 한 다음 **전달을**클릭 합니다.
    
3. 새 메시지의 경우 **받는 사람**에 평가판 구독 Office 365 전역 관리자 이름의 전자 메일 주소를 입력한 다음 **보내기**를 클릭합니다.
    
4. 제목이 **새 여행 웹 사이트인**전자 메일을 클릭 하 고 아래쪽 화살표 아이콘을 클릭 한 다음 **전체 회신**을 클릭 하 고 **보내기를**클릭 합니다.
    
5. 3단계에서 ATP 정책을 구성하는 데 사용한 Internet Explorer의 인스턴스에서 Exchange 관리 센터 탭을 클릭하고 앱 타일을 클릭한 다음 **메일**을 클릭합니다. 받은 편지함에 다음과 같은 새 전자 메일 메시지가 두 개 표시됩니다.
    
  - 제목이 **FW: 새 키**인 메시지
    
  - 제목이 **FW: 새 여행 웹 사이트**인 메시지
    
6. **Fw: 새 여행 웹 사이트** 라는 전자 메일 메시지를 열고 **이 사이트** 링크를 클릭 합니다. "이 웹 사이트가 악성으로 분류 되었습니다."가 표시 됩니다. 페이지. 이는 ATP가 잠재적으로 악의적인 웹 사이트에 액세스할 수 없다는 것을 보여 줍니다.
    
7. Internet Explorer의 Exchange 관리 센터 탭의 왼쪽 탐색 창에서 **메일 흐름**을 클릭합니다.
    
8. **메시지 추적** 탭을 클릭한 다음 **검색**을 클릭합니다.
    
9. **메시지 추적 결과** 창에서 제목이 **새 키**인 메시지를 두 번 클릭합니다. 이 메시지는 받은 편지 함으로 배달 되었습니다. 이 창을 닫습니다.
    
10. 제목이 **새 여행 웹 사이트**인 메시지를 두 번 클릭합니다. 이 메시지는 받은 편지 함으로 배달 되었습니다. 이 창을 닫습니다.
    
11. 제목이 **FW: 새 키**인 메시지를 두 번 클릭합니다. ATP에서이 메시지를 처리 한 후 받은 편지 함으로 배달 하는 방법을 확인 하세요. 이 창을 닫습니다.
    
    > [!NOTE]
    > 안전한 첨부 파일 정책의 목적은 악성 코드에 대 한 첨부 파일 검색을 시작 하는 것 이었습니다. getkeys .js 첨부 파일이 악성으로 확인 되지 않았으므로 허용 되지 않았습니다. 이 단계에서는 ATP가 첨부 파일 검사를 수행 했는지를 보여 줍니다. 
  
12. 제목이 **FW: 새 여행 웹 사이트**인 메시지를 두 번 클릭합니다. 이 메시지는 받은 편지 함으로 배달 되었습니다.
    
이제 이 환경을 사용하여 새 정책을 만들고 ATP를 실험할 수 있습니다.
  
> [!TIP]
> [여기](http://aka.ms/catlgstack)를 클릭하여 Office 365 테스트 랩 가이드 스택의 모든 문서에 대한 가상 맵을 확인할 수 있습니다.
  
## <a name="see-also"></a>참고 항목

[클라우드 도입 TLG(테스트 랩 가이드)](cloud-adoption-test-lab-guides-tlgs.md)
  
[기본 구성 개발/테스트 환경](base-configuration-dev-test-environment.md)
  
[Office 365 개발/테스트 환경](office-365-dev-test-environment.md)
  
[Office 365 개발/테스트 환경용 DirSync](dirsync-for-your-office-365-dev-test-environment.md)
  
[Office 365 개발/테스트 환경용 Cloud App Security](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[클라우드 도입 및 하이브리드 솔루션](cloud-adoption-and-hybrid-solutions.md) 

[안전한 첨부 파일 및 안전한 링크를 위한 Advanced Threat Protection](https://support.office.com/article/Office-365-Advanced-Threat-Protection-E100FE7C-F2A1-4B7D-9E08-622330B83653)


