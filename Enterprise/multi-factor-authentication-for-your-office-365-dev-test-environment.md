---
title: Office 365 개발/테스트 환경용 Multi-Factor Authentication
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/20/2019
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
ms.assetid: e2b354b9-7f18-4da0-9107-6245eae0f33f
description: '요약: Office 365 개발/테스트 환경에서 스마트 전화로 전송 되는 텍스트 메시지를 사용 하 여 다단계 인증을 구성 합니다.'
ms.openlocfilehash: 6e78d826cd010230218048ef320d8f32430ac02b
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2019
ms.locfileid: "38032133"
---
# <a name="multi-factor-authentication-for-your-office-365-devtest-environment"></a>Office 365 개발/테스트 환경용 Multi-Factor Authentication

 **요약:** Office 365 개발/테스트 환경의 스마트 전화로 전송 되는 텍스트 메시지를 사용 하 여 다단계 인증을 구성 합니다.
  
Office 365 구독에 로그인 하는 데 필요한 추가 보안 수준을 설정 하려면 계정을 인증 하기 위해 사용자 이름 및 암호를 초과 해야 하는 Azure multi-factor authentication을 사용 하도록 설정할 수 있습니다. Office 365에 대 한 다단계 인증을 사용 하는 경우 사용자는 전화 통화를 승인 하거나, 문자 메시지로 보낸 확인 코드를 입력 하거나, 암호를 올바르게 입력 한 후 스마트 전화에서 앱 암호를 지정 해야 합니다. 사용자는 이 두 번째 인증 요소를 충족해야 로그인할 수 있습니다. 
  
이 문서에서는 특정 Office 365 계정에 대해 텍스트 메시지 기반 인증을 사용 하 고 테스트 하는 방법에 대해 설명 합니다.
  
개발/테스트 환경에서 Office 365에 대 한 다단계 인증을 설정 하는 단계는 다음 두 단계로 진행 됩니다.
  
1. Office 365 개발/테스트 환경을 만듭니다.
    
2. 사용자 2 계정에 대해 multi-factor authentication을 사용 하도록 설정 하 고 테스트 합니다.
    
> [!TIP]
> [여기](https://aka.ms/catlgstack)를 클릭하여 Office 365 테스트 랩 가이드 스택의 모든 문서에 대한 가상 맵을 확인할 수 있습니다.
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>1단계: 경량 또는 시뮬레이트된 엔터프라이즈 Office 365 개발/테스트 환경을 구축합니다.

최소 요구 사항을 사용 하 여 경량 방식으로 multi-factor authentication을 테스트 하려는 경우에는 [Office 365 개발/테스트 환경의](office-365-dev-test-environment.md)2 단계 및 3 단계의 지침을 따릅니다.
  
시뮬레이트된 엔터프라이즈에서 다단계 인증을 테스트 하려는 경우에는 [Office 365 개발/테스트 환경에 대 한 DirSync](dirsync-for-your-office-365-dev-test-environment.md)의 지침을 따르세요.
  
> [!NOTE]
> 다단계 인증을 테스트 하는 경우에는 AD DS (Active Directory 도메인 서비스) 포리스트의 인터넷 및 디렉터리 동기화에 연결 된 시뮬레이트된 인트라넷을 포함 하는 시뮬레이트된 엔터프라이즈 개발/테스트 환경이 필요 하지 않습니다. 다단계 인증을 테스트 하 고 일반적인 조직을 나타내는 환경에서 테스트할 수 있도록 옵션으로 제공 됩니다. 
  
## <a name="phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account"></a>2 단계: 사용자 2 계정에 대해 multi-factor authentication 사용 및 테스트

사용자 2 계정에 대해 다단계 인증을 사용 하도록 설정 하려면 다음 단계를 수행 합니다.
  
1. 별도의 브라우저 인스턴스를 열고 Office 365 portal ([https://www.office.com](https://www.office.com))로 이동한 다음 전역 관리자 계정을 사용 하 여 office 365 평가판 구독에 로그인 합니다.
    
2. 기본 포털 페이지에서 **관리자**를 클릭합니다.
    
3. 왼쪽 탐색에서 **사용자 > 활성화된 사용자**를 클릭합니다.
    
4. 활성 사용자 창에서 **multi-factor authentication 설치 >** 를 클릭 합니다.
    
5. 목록에서 **사용자 2** 계정을 선택 합니다.
    
6. **사용자 2** 섹션의 **빠른 단계**에서 **사용**을 클릭 합니다.
    
7. **다단계 인증 사용** 대화 상자에서 **다단계 인증 사용**을 클릭 합니다.
    
8. **업데이트 완료** 대화 상자에서 **닫기를**클릭 합니다.
    
9. **Microsoft Office 홈** 탭의 오른쪽 위에 있는 사용자 계정 아이콘을 클릭 한 다음 **로그 아웃**을 클릭 합니다.
    
10. 브라우저 인스턴스를 닫습니다.
    
사용자 2 계정에 대 한 구성을 완료 하 여 유효성 검사에 텍스트 메시지를 사용 하 고 다음 단계를 사용 하 여 테스트 합니다.
  
1. 브라우저의 새 인스턴스를 엽니다.
    
2. Office 365 portal ([https://www.office.com](https://www.office.com))로 이동 하 여 사용자 2 계정 (user2@\<조직 이름> onmicrosoft.com) 및 암호를 사용 하 여 로그인 합니다.
    
3. 로그인 한 후에는 추가 보안 유효성 검사를 위해 계정을 설정 하 라는 메시지가 표시 됩니다. **지금 설정**을 클릭 합니다.
    
4. **추가 보안 확인** 페이지에서 다음을 수행 합니다.
    
  - 국가 또는 지역을 선택 합니다.
    
  - 텍스트 메시지를 받을 스마트 폰의 전화 번호를 입력 합니다.
    
  - **방법**에서 **문자 메시지로 코드 보내기를**클릭 합니다.
    
5. **다음**을 클릭합니다.
    
6. 스마트 폰에서 받은 문자 메시지의 확인 코드를 입력 하 고 **확인**을 클릭 합니다.
    
7. **3 단계: 기존 응용 프로그램 유지** 페이지에서 사용자 2 계정에 대해 표시 된 앱 암호를 안전한 위치에 기록 하 고 **완료**를 클릭 합니다.
    
8. 사용자 2 계정으로 처음 로그인 하는 경우 암호를 변경 하 라는 메시지가 표시 됩니다. 원래 암호와 새 암호를 두 번 입력 한 다음 **암호 업데이트 및 로그인**을 클릭 합니다. 새 암호를 안전한 위치에 기록 합니다.
    
    브라우저의 **Microsoft Office 홈** 탭에 사용자 2에 대 한 Office 365 포털이 표시 됩니다.
    
## <a name="see-also"></a>참고 항목

[클라우드 도입 TLG(테스트 랩 가이드)](cloud-adoption-test-lab-guides-tlgs.md)
  
[기본 구성 개발/테스트 환경](base-configuration-dev-test-environment.md)
  
[Office 365 개발/테스트 환경](office-365-dev-test-environment.md)
  
[클라우드 도입 및 하이브리드 솔루션](cloud-adoption-and-hybrid-solutions.md)

[Office 365 배포에 대 한 다단계 인증 계획](https://support.office.com/article/Plan-for-multi-factor-authentication-for-Office-365-Deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)

