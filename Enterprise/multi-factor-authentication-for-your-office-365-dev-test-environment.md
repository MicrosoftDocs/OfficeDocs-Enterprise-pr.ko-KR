---
title: "Office 365 개발/테스트 환경에 대해 다단계 인증"
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
- DecEntMigration
- mar17entnews
- TLG
- Ent_TLGs
ms.assetid: e2b354b9-7f18-4da0-9107-6245eae0f33f
description: "요약: Office 365 개발/테스트 환경에서 스마트폰으로 전송 하는 텍스트 메시지를 사용 하 여 다단계 인증을 구성 합니다."
ms.openlocfilehash: 87fdcc2ccd910e8da399e14d37fe3d0d1f0a66d4
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2017
---
# <a name="multi-factor-authentication-for-your-office-365-devtest-environment"></a>Office 365 개발/테스트 환경에 대해 다단계 인증

 **요약:** Office 365 개발/테스트 환경에서 스마트폰으로 전송 하는 텍스트 메시지를 사용 하 여 다단계 인증을 구성 합니다.
  
추가 된 Office 365 구독에 로그인 하는 것에 대 한 보안 수준을 대 한 사용자 이름 및 암호 계정을 확인 하려면 단순한 필요로 하는 Azure 다단계 인증을 사용할 수 있습니다. Office 365에 대 한 다단계 인증을 사용 하면 사용자가 전화 통화, 텍스트 메시지를 열고 전송 확인 코드를 입력 하거나 올바르게 자신의 암호를 입력 한 후 스마트 전화 앱 암호를 지정 해야 합니다. 이 두번째 인증 요소를 충족 된 후에에 로그인 수 있습니다. 
  
이 문서에서는 설정 하 고 특정 Office 365 계정에 대 한 텍스트 메시지 기반 인증을 테스트 하는 방법에 설명 합니다.
  
개발/테스트 환경에서 Office 365에 대 한 다단계 인증을 설정 하는 두 단계로 가지가 있습니다.
  
1. Office 365 개발/테스트 환경을 만듭니다.
    
2. 사용 하도록 설정 하 고 사용자 2 계정에 대 한 다단계 인증을 테스트 합니다.
    
> [!TIP]
> 클릭 [여기](http://aka.ms/catlgstack) 에 한 맵이 하나의 Microsoft 클라우드 테스트 랩 가이드 스택의 모든 문서를 시각적으로 표시 합니다.
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>1단계: 경량 또는 시뮬레이트된 엔터프라이즈 Office 365 개발/테스트 환경을 구축합니다.

최소 요구 사항을 경량 방식으로 다단계 인증을 테스트 하려면 2와 [Office 365 개발/테스트 환경](office-365-dev-test-environment.md)의 3 단계에서 지침을 따릅니다.
  
시뮬레이션 된 엔터프라이즈에서 다단계 인증을 테스트 하려는 경우 [Office 365 개발/테스트 환경에 대 한 디렉터리 동기화](dirsync-for-your-office-365-dev-test-environment.md)의 지시를 따릅니다.
  
> [!NOTE]
> 다단계 인증을 테스트 하지 않아도 인터넷에 연결 하는 시뮬레이션 된 인트라넷을 포함 하는 시뮬레이션 된 엔터프라이즈 개발/테스트 환경 및 Windows Server AD 포리스트에 대 한 디렉터리 동기화 합니다. 제공은 다단계 인증을 테스트 하 고 일반적인 조직을 대표 하는 환경에서 사용해 수 있도록 하는 옵션으로 여기 합니다. 
  
## <a name="phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account"></a>2 단계: 사용 하도록 설정 하 고 사용자 2 계정에 대 한 다단계 인증 테스트

다음이 단계를 사용 하 여 사용자 2 계정에 대 한 다단계 인증을 사용 하도록 설정 합니다.
  
1. 브라우저의 개별 인스턴스를 열고 Office 365 포털 ([https://portal.office.com](https://portal.office.com))로 이동 다음 전역 관리자 계정 사용 하 여 Office 365 평가판 구독에 로그인 합니다.
    
2. 주 포털 페이지에서 **관리**를 클릭 합니다.
    
3. 왼쪽 탐색 영역에서 클릭 **사용자 > 활성 사용자**합니다.
    
4. 현재 사용자가 창에서 클릭 **더 > 설치 Azure 다단계 인증**합니다.
    
5. 목록에서 **사용자 2** 계정을 클릭 합니다.
    
6. **사용자 2** 섹션에서 **빠른 단계** **사용**을 클릭 합니다.
    
7. **다단계 인증을 사용 하도록 설정 하는 방법에 대 한** 대화 상자에서 **다단계 인증 사용**을 클릭 합니다.
    
8. **업데이트 성공** 대화 상자에서 **닫기**를 클릭 합니다.
    
9. **Microsoft Office 홈** 탭의 오른쪽 위에 있는 사용자 계정 아이콘을 클릭 하 고 **로그 아웃**을 클릭 합니다.
    
10. 브라우저 인스턴스를 닫습니다.
    
유효성 검사에 대 한 텍스트 메시지를 사용 하 고 이러한 단계를 테스트 하는 사용자 2 계정에 대 한 구성을 완료 합니다.
  
1. 브라우저의 새 인스턴스를 엽니다.
    
2. Office 365 포털 ([https://portal.office.com](https://portal.office.com)) 및 사용자 2 계정 사용 하 여 로그인으로 이동 (@ user2\<조직 이름 >. onmicrosoft.com) 및 암호입니다.
    
3. 로그인 한 후 추가 보안 유효성 검사에 대 한 계정을 설정 하 라는 메시지가 표시 됩니다. **지금 설정**를 클릭 합니다.
    
4. **추가 보안 확인** 페이지 수행 합니다.
    
  - 국가 또는 지역을 선택 합니다.
    
  - 텍스트 메시지를 받을 스마트 전화의 전화번호를 입력 합니다.
    
  - **보내기 나에 게 텍스트 메시지를 여는 코드를**선택 합니다.
    
5. **대화 상대 한 다음**을 클릭 합니다.
    
6. 스마트 전화기에서 받은 텍스트 메시지에서 확인 코드를 입력 한 다음 **확인**을 클릭 합니다.
    
7. **3 단계: 기존 응용 프로그램을 유지** 페이지를 안전한 위치에 2 사용자 계정에 대 한 표시 된 앱 암호를 기록 하 고 다음 **완료**를 클릭 합니다.
    
8. 다시 로그인 페이지에서 사용자 2 계정의 암호를 입력 하 고 **로그인**을 클릭 합니다.
    
9. 스마트 전화기에서 받은 텍스트 메시지에서 확인 코드를 입력 한 다음 **로그인**을 클릭 합니다.
    
10. 이것은 처음으로 하는 경우 귀하가 사용자 2 계정을 사용 하 여 메시지가 표시 되는 암호를 변경 해야 합니다. 원래 암호와 새 암호를을 두번 입력 하 고 **암호를 업데이트 하 고 로그인**을 클릭 합니다. 안전한 위치에 새 암호를 기록 합니다.
    
    사용자 2에 대 한 Office 365 포털에 표시 됩니다.
    
## <a name="see-also"></a>See Also

[클라우드 채택 테스트 랩 가이드 (Tlg)](cloud-adoption-test-lab-guides-tlgs.md)
  
[기본 구성 개발/테스트 환경](base-configuration-dev-test-environment.md)
  
[Office 365 개발/테스트 환경](office-365-dev-test-environment.md)
  
[클라우드 채택 및 하이브리드 솔루션](cloud-adoption-and-hybrid-solutions.md)

[Office 365 배포에 대 한 다중 요소 인증에 대 한 계획](https://support.office.com/article/Plan-for-multi-factor-authentication-for-Office-365-Deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)

