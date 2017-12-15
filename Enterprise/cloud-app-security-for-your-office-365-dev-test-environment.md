---
title: "Office 365 개발/테스트 환경에 대 한 클라우드 응용 프로그램 보안"
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
- TLG
- Ent_TLGs
ms.assetid: 22248f2f-b370-435e-b6ac-0ae0cae36b96
description: "요약: 구성 및 Office 365 개발/테스트 환경에서 Office 365 클라우드 응용 프로그램 보안을 시연 합니다."
ms.openlocfilehash: 1fab5ebfd6e0670ba59fe34b2cca8a7282e75723
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2017
---
# <a name="cloud-app-security-for-your-office-365-devtest-environment"></a>Office 365 개발/테스트 환경에 대 한 클라우드 응용 프로그램 보안

 **요약:** 구성 하 고 Office 365 개발/테스트 환경에서 Office 365 클라우드 응용 프로그램 보안을 시연 합니다.
  
이전에 Office 365 고급 보안 관리 라고 office 365 클라우드 응용 프로그램 보안에 대 한 모니터링 하 고 알리기 위해 Office 365 구독에 의심 스러운 활동의 조사 하 고 가능한 수행할 수 있도록 하는 정책을 만들 수 있습니다. 업데이트 관리 작업입니다. 자세한 내용은 [개요의 클라우드 앱 Office 365의 보안](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475)을 참조 하십시오.
  
이 문서의 지침을 사용 하도록 설정 하 고 Office 365 평가판 구독에서 클라우드 응용 프로그램 보안 테스트 합니다.
  
> [!TIP]
> 클릭 [여기](http://aka.ms/catlgstack) 에 한 맵이 하나의 Microsoft 클라우드 테스트 랩 가이드 스택의 모든 문서를 시각적으로 표시 합니다.
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>1단계: 경량 또는 시뮬레이트된 엔터프라이즈 Office 365 개발/테스트 환경을 구축합니다.

최소 요구 사항을 경량 방식으로 클라우드 응용 프로그램 보안을 테스트 하려면 2와 [Office 365 개발/테스트 환경](office-365-dev-test-environment.md)의 3 단계에서 지침을 따릅니다.
  
시뮬레이션 된 엔터프라이즈에서 클라우드 응용 프로그램 보안을 테스트 하려는 경우 [Office 365 개발/테스트 환경에 대 한 디렉터리 동기화](dirsync-for-your-office-365-dev-test-environment.md)의 지시를 따릅니다.
  
> [!NOTE]
> 테스트 클라우드 앱 보안 인터넷에 연결 하는 시뮬레이션 된 인트라넷을 포함 하는 시뮬레이션 된 엔터프라이즈 개발/테스트 환경에 원하지 않는 및 Windows Server AD 포리스트에 대 한 디렉터리 동기화 합니다. 제공은 클라우드 응용 프로그램 보안을 테스트 하 고 일반적인 조직을 대표 하는 환경에서 사용해 수 있도록 하는 옵션으로 여기 합니다. 
  
## <a name="phase-2-before-enabling-cloud-app-security-and-creating-a-policy"></a>2 단계: 하기 전에 클라우드 응용 프로그램 보안을 사용 하도록 설정 하 고 정책 만들기

이 절차는 클라우드 응용 프로그램 보안을 사용 하도록 설정 하기 전에 사용자의 역할을 변경 없음 전자 메일 알림을 제공 전역 관리자에 게 보여줍니다.
  
### <a name="test-the-default-notification-behavior-of-office-365"></a>Office 365의 기본 알림 동작 테스트

1. Office 365 포털 ([https://portal.office.com](https://portal.office.com))에 이동 하 고 전역 관리자 계정 사용 하 여 Office 365 평가판 구독에 로그인 합니다.
    
  - 경량 Office 365 개발/테스트 환경을 사용하는 경우 로컬 컴퓨터에서 로그인합니다.
    
  - 시뮬레이션 된 엔터프라이즈 Office 365 개발/테스트 환경을 사용 하는 경우 [Azure 포털](https://portal.azure.com) 을 사용 하 여 CLIENT1 가상 컴퓨터에 연결한 다음 CLIENT1에서 로그인 합니다.
    
2. 주 포털 페이지에서 **관리**를 클릭 합니다.
    
3. 왼쪽 탐색 영역에서 클릭 **사용자 > 활성 사용자**합니다.
    
4. **사용자 4** 계정을 클릭 합니다.
    
5. **사용자 4** 페이지에서 **역할** 행에 대 한 **편집** 을 클릭 합니다.
    
6. **사용자 역할 편집** 페이지에서 **전역 관리자**를 클릭 하 고 **user4@contoso.com** **대체 전자 메일 주소**입력 한 다음 **저장**을 클릭 합니다. **닫기** 를 두 번 클릭 합니다.
    
7. 왼쪽 위에서에서 응용 프로그램 시작 관리자 아이콘을 선택 하 고 **메일**을 선택 합니다.
    
8. 30 분 기다립니다. 전역 관리자 권한으로 사용자 4 역할에서 변경 된 알려주는 받은 편지함에 전자 메일 메시지 없이 것을 볼 수 있습니다.
    
## <a name="phase-3-enable-cloud-app-security-and-create-a-policy"></a>3 단계: 클라우드 응용 프로그램 보안을 사용 하도록 설정 하 고 정책 만들기

이 절차를 있습니다 클라우드 응용 프로그램 보안을 설정 하 고 사용자 계정 역할의 변경 내용에 대 한 전역 관리자 계정에 게 전자 메일 알림을 보내도록 하는 새 정책을 만듭니다. 이 절차를 수행 하려면:
  
- Office 365 평가판 구독의 전역 관리자 계정 이름 및 암호.
    
- Office 365 평가판 구독의 User 5 계정 이름 및 암호.
    
### <a name="enable-and-configure-cloud-app-security"></a>설정 하 고 클라우드 응용 프로그램 보안 설정 구성

1. Office 365 포털 ([https://portal.office.com](https://portal.office.com))에 이동 하 고 전역 관리자 계정 사용 하 여 Office 365 평가판 구독에 로그인 합니다.
    
2. 클릭 하 고 **보안 &amp; 준수** 바둑판식으로 배열 합니다.
    
3. 왼쪽된 탐색 창의 클릭 **알림 > 고급 알림 관리**합니다.
    
4. **고급 알림 관리** 페이지에서 **Office 365 클라우드 응용 프로그램 보안 설정**를 클릭 한 다음 **Office 365 클라우드 응용 프로그램 보안으로 이동**를 클릭 합니다.
    
5. 새 **대시보드** 탭을 클릭 **제어 > 정책**합니다.
    
6. **정책** 페이지에서 **정책 만들기**클릭 한 다음 **활동 정책**을 클릭 합니다.
    
7. **정책 이름** **관리 작업**을 입력 합니다.
    
8. **정책 심각도** **높은**클릭 합니다.
    
9. **범주** **권한이 부여 된 계정**을 클릭 합니다.
    
10. **정책에 대 한 만들기 필터**에 **일치 하는 다음의 모든 활동**을에서 **관리 작업**을 클릭 합니다.
    
11. **경고** **경고로 전자 메일 보내기**를 클릭 합니다. (영문) **를**, 전역 관리자 계정의 전자 메일 주소를 입력 합니다.
    
12. 페이지의 맨 아래에 **만들기**를 클릭 합니다.
    
## <a name="phase-4-show-cloud-app-security-in-action"></a>4 단계: 동작의 표시 클라우드 응용 프로그램 보안

이 절차에서는 클라우드 앱 보안 경고를 만드는 방법을 보여주는 및 사용자 4가 사용자 5 암호 및 사용자 관리 관리자가 전역 관리자 계정에 전자 메일 알림을 보냅니다.
  
### <a name="demonstrate-email-notification-for-a-change-in-user-account-roles"></a>사용자 계정 역할 변경에 대한 전자 메일 알림 보여 주기

1. 위 오른쪽에서 사용자 아이콘을 클릭 하 고 **로그 아웃**을 클릭 합니다.
    
2. [Https://portal.office.com](https://portal.office.com)로 이동 합니다.
    
3. Office 365 로그인 페이지에서 **다른 계정 사용**을 클릭 합니다.
    
4. 사용자 4 계정 이름 및 해당 암호를 입력 하 고 **로그인**을 클릭 합니다.
    
5. 필요한 경우 사용자 4 계정 암호를 변경 하 고 **암호를 업데이트 하 고 로그인**을 클릭 합니다.
    
6. Office 365 포털 페이지에서 **관리**를 클릭 합니다.
    
7. 필요한 경우에 프로그램 관리자의 연락처 정보를 업데이트 하려면 대화 상자가 나타나면 **취소** 를 클릭 합니다.
    
8. 주 포털 페이지에서 **관리**를 클릭 합니다.
    
9. 왼쪽 탐색 영역에서 클릭 **사용자 > 활성 사용자**합니다.
    
10. **5 사용자** 계정을 클릭 합니다.
    
11. **사용자 5** 페이지에서 **역할** 행에 대 한 **편집** 을 클릭 합니다.
    
12. **사용자 역할 편집** 페이지에서 **사용자 지정 된 관리자**를 클릭합니다, 그리고 **암호 관리자** 및 **사용자 관리 관리자**를 클릭합니다, 그리고 **user5@contoso.com** **대체 전자 메일 주소**입력 하 고을 클릭합니다 **저장**합니다. **닫기** 를 두 번 클릭 합니다.
    
13. 위 오른쪽에 있는 사용자 아이콘을 클릭 하 고 **로그 아웃**을 클릭 합니다. 
    
14. [Https://portal.office.com](https://portal.office.com)로 이동 합니다.
    
15. **Office 365 로그인** 페이지에서 전역 관리자 계정 이름을 클릭 합니다.
    
16. 암호를 입력 한 다음 **로그인**을 클릭 합니다.
    
17. 주 포털 페이지에서 **관리**를 클릭 합니다.
    
18. 클릭 하 고 **보안 &amp; 준수** 바둑판식으로 배열 합니다.
    
19. 왼쪽된 탐색 창의 클릭 **알림 > 고급 알림 관리**합니다.
    
20. **고급 알림 관리** 페이지에서 **Office 365 클라우드 응용 프로그램 보안으로 이동**합니다.를 클릭 합니다.
    
21. 새 **대시보드** 탭에서 **관리 작업**에 대 한 두 새 경고를 확인 합니다.
    
22. **Microsoft Office 홈** 탭에서 **메일**을 클릭 합니다. 최대 30 분까지 기다립니다. 
    
    두 새 전자 메일 메시지 제목 **Microsoft Azure AD 알림 서비스**와 받은 편지함에 나타납니다. 하나의 메시지 나타내고 사용자 5 계정 **암호 관리자** 역할에 추가 된 사용자 5 계정이 **사용자 관리자** 역할에 추가 된 다른 메시지를 나타냅니다 (같은 사용자 관리 관리자 역할에 Office 365 관리 센터)입니다.
    
이제 새 정책 만들기 및 추가 Office 365 클라우드 응용 프로그램 보안을 사용해이 환경에 사용할 수 있습니다. 추가 구성 문서 링크를 [Office 365 클라우드 응용 프로그램 보안에 대 한 준비](https://support.office.com/article/Get-ready-for-Office-365-Cloud-App-Security-d9ee4d67-f2b3-42b4-9c9e-c4529904990a) 를 참조 하십시오.
  
## <a name="see-also"></a>See Also

[클라우드 채택 테스트 랩 가이드 (Tlg)](cloud-adoption-test-lab-guides-tlgs.md)
  
[Office 365 개발/테스트 환경](office-365-dev-test-environment.md)
  
[클라우드 채택 및 하이브리드 솔루션](cloud-adoption-and-hybrid-solutions.md)

[Office 365의에서 클라우드 앱 보안 개요](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475)


