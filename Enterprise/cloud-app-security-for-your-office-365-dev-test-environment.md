---
title: Office 365 개발/테스트 환경용 Cloud App Security
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/05/2018
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 22248f2f-b370-435e-b6ac-0ae0cae36b96
description: '요약: Office 365 개발/테스트 환경에서 Office 365 Cloud App Security를 구성 하 고 시연 하는 방법을 설명 합니다.'
ms.openlocfilehash: f76aaa5b13e409f08a4b96714e1f4bdfcc84ecac
ms.sourcegitcommit: a578baeb0d8b85941c13afa268447d2592f89fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2020
ms.locfileid: "43793721"
---
# <a name="cloud-app-security-for-your-office-365-devtest-environment"></a>Office 365 개발/테스트 환경용 Cloud App Security

 **요약:** Office 365 개발/테스트 환경에서 Office 365 Cloud App Security를 구성 하 고 시연 합니다.
  
Office 365 Cloud App Security (이전에는 Office 365 Advanced Security Management)를 통해 Office 365 구독에서 의심 스러운 활동을 모니터링 하 고 사용자에 게 알리기 위한 정책을 만들고 가능한 업데이트 작업을 수행할 수 있습니다. 자세한 내용은 [Office 365의 Cloud App Security 개요](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475)를 참조 하세요.
  
이 문서의 지침을 사용 하 여 Office 365 평가판 구독에서 Cloud App Security를 사용 하도록 설정 하 고 테스트 합니다.
  
> [!TIP]
> [여기](https://aka.ms/catlgstack)를 클릭하여 Office 365 테스트 랩 가이드 스택의 모든 문서에 대한 가상 맵을 확인할 수 있습니다.
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>1단계: 경량 또는 시뮬레이트된 엔터프라이즈 Office 365 개발/테스트 환경을 구축합니다.

최소 요구 사항에 따라 간단한 방법으로 Cloud App Security를 테스트 하려면 [Office 365 개발/테스트 환경의](office-365-dev-test-environment.md)2, 3 단계의 지침을 따릅니다.
  
시뮬레이트된 엔터프라이즈에서 Cloud App Security를 테스트 하려면 [Office 365 개발/테스트 환경용 DirSync](dirsync-for-your-office-365-dev-test-environment.md)의 지침을 따르세요.
  
> [!NOTE]
> 클라우드 앱 보안을 테스트 하는 경우 AD DS (Active Directory 도메인 서비스) 포리스트의 인터넷 및 디렉터리 동기화에 연결 된 시뮬레이트된 인트라넷을 포함 하는 시뮬레이트된 엔터프라이즈 개발/테스트 환경이 필요 하지 않습니다. 클라우드 앱 보안을 테스트 하 고 일반적인 조직을 나타내는 환경에서 테스트해 볼 수 있도록 여기에 제공 되는 옵션입니다. 
  
## <a name="phase-2-before-enabling-cloud-app-security-and-creating-a-policy"></a>2 단계: Cloud App Security를 사용 하도록 설정 하 고 정책을 만들기 전

이 절차에서는 Cloud App Security를 사용 하기 전에 사용자 역할을 변경 하면 전역 관리자에 게 전자 메일 알림이 제공 되지 않음을 보여 줍니다.
  
### <a name="test-the-default-notification-behavior-of-office-365"></a>Office 365의 기본 알림 동작 테스트

1. Microsoft 365 관리 센터 ([https://admin.microsoft.com](https://admin.microsoft.com))로 이동 하 고 전역 관리자 계정을 사용 하 여 Office 365 평가판 구독에 로그인 합니다.
    
  - 경량 Office 365 개발/테스트 환경을 사용하는 경우 로컬 컴퓨터에서 로그인합니다.
    
  - 시뮬레이트된 enterprise Office 365 개발/테스트 환경을 사용 하는 경우 [Azure portal](https://portal.azure.com) 을 사용 하 여 client1 가상 컴퓨터에 연결한 다음, client1에서 로그인 합니다.
    
2. 기본 포털 페이지에서 **관리자**를 클릭합니다.
    
3. 왼쪽 탐색에서 **사용자 > 활성화된 사용자**를 클릭합니다.
    
4. **User 4** 계정을 클릭합니다.
    
5. **User 4** 페이지에서 **규칙** 열에 대한 **편집**을 클릭합니다.
    
6. **사용자 역할 편집** 페이지에서 **전역 관리자**를 클릭하고 **대체 전자 메일 주소**에 **user4@contoso.com**을 입력한 다음 **저장**을 클릭합니다. **닫기**를 두 번 클릭합니다.
    
7. 	왼쪽 위에서 앱 시작 관리자 아이콘을 선택하고 **메일**을 선택합니다.
    
8. 30분간 기다립니다. 사용자 4의 역할이 전역 관리자로 변경 되었음을 알리는 받은 편지함에 전자 메일 메시지가 없는 것을 볼 수 있습니다.
    
## <a name="phase-3-enable-cloud-app-security-and-create-a-policy"></a>3 단계: Cloud App Security를 사용 하도록 설정 하 고 정책 만들기

이 절차에서는 Cloud App Security을 사용 하도록 설정 하 고 사용자 계정 역할 변경에 대 한 전자 메일 알림을 전역 관리자 계정에 보내도록 새 정책을 만듭니다. 이 프로시저에는 다음 항목이 필요합니다.
  
- Office 365 평가판 구독의 전역 관리자 계정 이름 및 암호.
    
- Office 365 평가판 구독의 User 5 계정 이름 및 암호.
    
### <a name="enable-and-configure-cloud-app-security"></a>Cloud App Security 사용 및 구성

1. Microsoft 365 관리 센터 ([https://admin.microsoft.com](https://admin.microsoft.com))로 이동 하 고 전역 관리자 계정을 사용 하 여 Office 365 평가판 구독에 로그인 합니다.
    
2. **관리** 타일을 클릭합니다. **Office 관리 센터** 탭에서 **관리 센터 > 보안 & 규정 준수**를 클릭 합니다.
    
3. 왼쪽 탐색 창에서 **경고 > 고급 알림 관리**를 클릭 합니다.
    
4. **고급 알림 관리** 페이지에서 **Office 365 Cloud app security 사용**을 클릭 하 고 **office 365 cloud app security로 이동을**클릭 합니다.
    
5. 새 **대시보드** 탭에서 **> 정책 제어**를 클릭 합니다.
    
6. **정책** 페이지에서 **정책 만들기**를 클릭 한 다음 **활동 정책을**클릭 합니다.
    
7. **정책 이름**에 **관리 활동**을 입력 합니다.
    
8. **정책 심각도**에서 **높음**을 클릭합니다.
    
9. **범주**에서 **권한이 부여 된 계정을**클릭 합니다.
    
10. **정책에 대 한 필터 만들기**의 **다음 작업과 일치 하는 작업**의 **관리 작업**을 클릭 합니다.
    
11. **경고**에서 **전자 메일로 경고 보내기**를 클릭합니다. **받는 사람**에서 전역 관리자 계정의 전자 메일 주소를 입력합니다.
    
12. 페이지 하단에서 **만들기**를 클릭합니다.
    
## <a name="phase-4-show-cloud-app-security-in-action"></a>4 단계: Cloud App Security in action을 표시 합니다.

이 절차에서는 사용자 4가 사용자 5를 암호 및 사용자 관리 관리자로 설정한 경우 Cloud App Security에서 알림을 만들고 전역 관리자 계정으로 전자 메일 알림을 보내는 방법을 보여 줍니다.
  
### <a name="demonstrate-email-notification-for-a-change-in-user-account-roles"></a>사용자 계정 역할 변경에 대한 전자 메일 알림 보여 주기

1. 오른쪽 위에서 사용자 아이콘을 클릭한 다음 **로그아웃**을 클릭합니다.
    
2. [https://www.office.com](https://www.office.com)으로 이동합니다.
    
3. Office 365 로그인 페이지에서 **다른 계정 사용**을 클릭합니다.
    
4. User 4 계정 이름 및 암호를 입력한 다음 **로그인**을 클릭합니다.
    
5. 필요한 경우 User 4 계정 암호를 변경한 다음 **암호 업데이트 및 로그인**을 클릭합니다.
    
6. Office 365 포털 페이지에서 **관리자**를 클릭합니다.
    
7. 관리자 연락처 정보를 업데이트하라는 메시지가 표시되면 필요한 경우 **취소**를 클릭합니다.
    
8. 기본 포털 페이지에서 **관리자**를 클릭합니다.
    
9. 왼쪽 탐색에서 **사용자 > 활성화된 사용자**를 클릭합니다.
    
10. **User 5** 계정을 클릭합니다.
    
11. **User 5** 페이지에서 **규칙** 열에 대한 **편집**을 클릭합니다.
    
12. **사용자 역할 편집** 페이지에서 **사용자 지정된 관리자**를 클릭하고 **암호 관리자** 및 **사용자 관리 관리자**를 클릭한 다음 **대체 전자 메일 주소**에 **user5@contoso.com**을 입력하고 **저장**을 클릭합니다. **닫기**를 두 번 클릭합니다.
    
13. 오른쪽 위에서 사용자 아이콘을 클릭한 다음 **로그아웃**을 클릭합니다. 
    
14. [https://www.office.com](https://www.office.com)으로 이동합니다.
    
15. **Office 365 로그인** 페이지에서 전역 관리자 계정 이름을 클릭합니다.
    
16. 암호를 입력한 다음 **로그인**을 클릭합니다.
    
17. Office 365 포털 페이지에서 **관리자**를 클릭 합니다.
    
18. **보안 &amp; 준수** 타일을 클릭 합니다.
    
19. 왼쪽 탐색 창에서 **경고 > 고급 알림 관리**를 클릭 합니다.
    
20. **고급 알림 관리** 페이지에서 **Office 365 Cloud App Security로 이동을**클릭 합니다.
    
21. 새 **대시보드** 탭에서 **관리 활동**에 대 한 두 개의 새로운 알림을 확인 합니다.
    
22. **Microsoft Office 홈** 탭에서 **메일**을 클릭 합니다. 최대 30분을 기다립니다. 
    
    받은 편지함에 제목 **Microsoft AZURE AD 알림 서비스**와 함께 새 전자 메일 메시지가 두 개 표시 됩니다. 한 메시지는 사용자 5 계정을 **암호 관리자** 역할에 추가 했으며 사용자 5 계정이 **사용자 관리자** 역할에 추가 되었다는 것을 의미 합니다 (Microsoft 365 관리 센터의 사용자 관리 관리자 역할과 같음).
    
이제이 환경을 사용 하 여 새 정책을 만들고 Office 365 Cloud App Security를 추가로 경험해 볼 수 있습니다. 추가 구성 문서에 대 한 링크는 [Office 365 Cloud App Security 준비](https://support.office.com/article/Get-ready-for-Office-365-Cloud-App-Security-d9ee4d67-f2b3-42b4-9c9e-c4529904990a) 를 참조 하세요.
  
## <a name="see-also"></a>참고 항목

[클라우드 도입 TLG(테스트 랩 가이드)](cloud-adoption-test-lab-guides-tlgs.md)
  
[Office 365 개발/테스트 환경](office-365-dev-test-environment.md)
  
[클라우드 도입 및 하이브리드 솔루션](cloud-adoption-and-hybrid-solutions.yml)

[Office 365의 Cloud App Security 개요](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475)


