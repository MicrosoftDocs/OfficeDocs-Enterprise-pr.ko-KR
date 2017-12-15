---
title: "Office 365 및 Dynamics 365 개발/테스트 환경에 대 한 Exchange Online 통합"
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
- Ent_O365_Hybrid
- Ent_O365_Top
ms.custom:
- apr17entnews
- DecEntMigration
- mar17entnews
- Ent_TLGs
ms.assetid: 499c5823-427a-4ba2-8fc1-9553bc2ff2d3
description: "요약:이 테스트 랩 가이드를 사용 하 여 Office 365 평가판 구독에서 Exchange Online에 대 한 Dynamics 365 통합을 사용 하도록 설정 합니다."
ms.openlocfilehash: 9cecd13f0ffc3c2822ac6c66a3bde9c9e6a3c798
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2017
---
# <a name="exchange-online-integration-for-your-office-365-and-dynamics-365-devtest-environment"></a>Office 365 및 Dynamics 365 개발/테스트 환경에 대 한 Exchange Online 통합

 **요약:** 이 테스트 랩 가이드를 사용 하 여 Office 365 평가판 구독에서 Exchange Online에 대 한 Dynamics 365 통합을 사용 하도록 설정 합니다.
  
Microsoft Dynamics 365 사용 하는 중요 한 적절 한 권한이 있는 모든 사용자의 모든 관련 고객 레코드를 볼 수 있도록 한 곳에서 모든 고객의 통신을 저장 하는 것입니다. 예, 특정 연락처, 계정, 기회, 또는 대/소문자와 관련 된 모든 전자 메일을 봅니다.
  
Dynamics 365 전자 메일 및 기타 메시징 레코드를 저장 하려면 Dynamics 365 전자 메일 시스템을 동기화 해야 합니다. 서버쪽 동기화는 전자 메일 동기화를 위해 선택한 방법입니다.
  
이 테스트 랩 가이드를 사용 하 여를 구성 하 여 Exchange Online 및 Outlook 온라인 클라이언트 수 활용 하는 방법을 Dynamics 365 저장 된 정보를 보여줍니다. 
  
## <a name="phase-1-build-out-the-office-365-and-dynamics-365-devtest-environment"></a>1 단계: Office 365 및 Dynamics 365 개발/테스트 환경 구축

Office 365 및 Dynamics 365 개발/테스트 환경의 경량 또는 시뮬레이션 된 enterprise 버전을 만들려면 [Office 365와 Dynamics 365 개발/테스트 환경에서](office-365-and-dynamics-365-dev-test-environment.md) 의 지침을 사용 합니다.
  
> [!NOTE]
> 이 문서의 구성 인터넷에 연결 하는 시뮬레이션 된 인트라넷을 포함 하는 시뮬레이션 된 엔터프라이즈 개발/테스트 환경에 원하지 않는 및 Windows Server Active Directory (AD) 포리스트에 대 한 디렉터리 동기화 합니다. 제공은 일반적인 조직을 대표 하는 환경에서 Office 365와 Dynamics 365 테스트할 수 있도록 하는 옵션으로 여기 
  
## <a name="phase-2-configure-and-demonstrate-dynamics-365-integration-in-exchange-online"></a>2 단계: 구성 및 Exchange Online Dynamics 365 통합을 시연

다음이 단계를 사용 하 여 Dynamics 365 및 Exchange Online의 통합에 대 한 전역 관리자의 사서함을 구성 합니다.
  
1. 브라우저의 개인 세션을 사용 하 여, [http://portal.office.com](http://portal.office.com) 로 이동 하 고 프로그램 Office 365 전역 관리자 계정을 사용 하 여 로그인 합니다.
    
2. **Microsoft Office 홈** 페이지에서 **메일** 타일을 클릭 합니다.
    
3. 브라우저에서 새 **메일** 탭에서 **새로 만들기** 를 클릭 하 고 메시지를 입력 하는 것에 대 한 상자 아래에 있는 창의 아래쪽 모서리 내 서식 파일에 대 한 아이콘을 포함 하는 방법을 확인할 수 있습니다.
    
     ![Dynamics 365와 통합되지 않은 비어 있는 새 전자 메일 메시지입니다.](images/879b54fd-a68f-4581-9f89-d5050df6f4de.png)
  
4. **취소** 를 클릭 하 고 **메일** 탭을 열어둡니다.
    
5. 브라우저에서 **Microsoft Office Home** 탭을 클릭 하 고 **Admin** 타일을 클릭 합니다.
    
6. **Office 관리 센터** 탭의 왼쪽 탐색 영역에서 클릭 **관리 센터 > Dynamics 365**합니다.
    
7. Dynamics 365 인스턴스 목록에서 브라우저에서 새 **Dynamics 365** 탭에서 **열기**를 클릭 합니다.
    
8. 탐색 모음에서 브라우저에서 새 **관리** 탭에서 **설정**옆에 있는 아래쪽 화살표를 클릭 하 고 **시스템**에서 **전자 메일 구성** 을 클릭 합니다.
    
9.  **전자 메일 구성** 페이지에서 **전자 메일 구성 설정**을 클릭 합니다.
    
10. **시스템 설정** 대화 상자에 **전자 메일** 탭에서 **서버쪽 동기화** **약속, 연락처 및 작업을** 변경 하 고 **확인**을 클릭 합니다.
    
11. **전자 메일 구성** 페이지에서 **사서함**을 클릭 합니다.
    
12. 확인 표시가 왼쪽된 열에서 Office 365 전역 관리자 이름을 선택 하 고 도구 모음에서 **기본 전자 메일 설정 적용** 을 클릭 한 다음 **확인**을 클릭 합니다.
    
13. 도구 모음에서 **승인 전자 메일** 을 클릭 한 다음 **확인**을 클릭 합니다.
    
14. 확인 표시가 왼쪽된 열에서 Office 365 전역 관리자 이름을 선택, 클릭 **테스트 &amp; 사서함을 사용 하도록 설정** 도구에서 막대를 한 다음 **확인**을 클릭 합니다.
    
15. 열기 **메일** 탭을 클릭 하 고 전역 관리자 테스트 메시지를 수신 되었는지 확인 합니다.
    
16. 브라우저에서 **사서함 내 활성 사서함** 탭으로 돌아가서 페이지를 새로 고칠 합니다. **받는 전자 메일 상태** 및 **보내는 전자 메일 상태** 열 전역 관리자의 계정 이름에 대 한 **성공** 로 설정 해야 합니다. 두 테스트를 완료 하려면 최대 15 분까지 걸릴 수 있다는 note 합니다.
    
다음이 단계를 사용 하 여 Outlook Dynamics 365 응용 프로그램을 설치 하 고 전역 관리자의 사서함에서 Dynamics 365 기능 시연 하려면:
  
1. 브라우저에서 **사서함 내 활성 사서함** 탭에서 **설정**옆에 있는 아래쪽 화살표를 클릭 하 고 **시스템**에서 **Outlook에 대 한 Dynamics 365 응용 프로그램** 을 클릭 합니다.
    
2. **Outlook 용 Microsoft Dynamics 365 응용 프로그램 시작** 페이지에서 전역 관리자 이름을 클릭 하 고 **Outlook에 앱 추가**클릭 합니다. **상태** 열에 **보류 중인**변경합니다.
    
3. **Outlook에 추가 된**상태가 변경 될 때까지 페이지를 새로 고칠 합니다. 이 구성을 완료 하려면 최대 15 분까지 걸릴 수 있다는 note 합니다.
    
4. 브라우저에서 **메일** 탭에서 클릭 하 고 닫습니다.
    
5. 브라우저에서 **Microsoft Office Home** 탭을 클릭 하 고 **메일** 타일을 클릭 합니다.
    
6. 브라우저에서 새 **메일** 탭에서 **새로 만들기**를 클릭 합니다. 이제 메시지를 입력 하는 것에 대 한 상자 아래에 있는 창의 아래쪽 모서리 Dynamics 365 대 한 아이콘을 포함 되어있는지 확인 합니다.
    
     ![Dynamics 365와 통합된 비어 있는 새 전자 메일 메시지로, 새 아이콘을 표시합니다.](images/ecb822e1-45fe-4481-99a1-294317d1d2de.png)
  
7. Dynamics 365 아이콘을 클릭 합니다. 이 전자 메일 또는 access 서식 파일, 영업 홍보 자료 또는 문서를 추적할 수 있는 프로그램 **Dynamics 365** 창을 표시 됩니다.
    
8. **받는** 사람 필드에는 전자 메일 메시지를에서 **alex.y.wu@outlook.com**입력 하 고 **Dynamics 365** 창에서 **다시 시도** 클릭 합니다. Alex Wu, 평가판 구독에 대 한 예제 데이터와 함께 제공 된 판매 응용 프로그램에서 대화 상대에 정보로 **Dynamics 365** 창에서 **받는 사람에 게** 섹션에 표시 됩니다.
    
     ![Dynamics 365에 저장된 판매 연락처에 대한 Dynamics 365 정보 창입니다.](images/a010fa5f-3f1b-47d4-ab5e-d00d85a24a3f.png)
  
9. **취소**를 클릭 합니다.

> [!TIP]
> 클릭 [여기](http://aka.ms/catlgstack) 에 한 맵이 하나의 Microsoft 클라우드 테스트 랩 가이드 스택의 문서는 모든 시각적으로 표시 합니다.
    
## <a name="see-also"></a>See Also

[Office 365 및 Dynamics 365 개발/테스트 환경](office-365-and-dynamics-365-dev-test-environment.md)
  
[클라우드 채택 테스트 랩 가이드 (Tlg)](cloud-adoption-test-lab-guides-tlgs.md)
  
[기본 구성 개발/테스트 환경](base-configuration-dev-test-environment.md)
  
[Office 365 개발/테스트 환경](office-365-dev-test-environment.md)
  
[Office 365 개발/테스트 환경에 대 한 디렉터리 동기화](dirsync-for-your-office-365-dev-test-environment.md)

[Dynamics 365 (온라인)에 대 한 구독 관리](https://technet.microsoft.com/library/jj679903.aspx)
  
[Dynamics 365 관리](https://technet.microsoft.com/library/dn531101.aspx)


