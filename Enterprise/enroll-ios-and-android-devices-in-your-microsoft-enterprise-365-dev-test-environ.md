---
title: "IOS 및 Microsoft 기업 365 개발/테스트 환경에서 Android 장치 등록"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: "요약:이 테스트 랩 가이드를 사용 하 여 Microsoft 365 개발/테스트 환경에서 장치를 등록 하 고 원격으로 관리 하기를."
ms.openlocfilehash: 77b5074b083656fdfa2cd460510231dae0689d10
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/09/2018
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-devtest-environment"></a>IOS 및 Microsoft 기업 365 개발/테스트 환경에서 Android 장치 등록

 **요약:** 이 테스트 랩 가이드를 Microsoft 365 개발/테스트 환경에서 장치를 등록 하 고 원격으로 관리 하기를 사용 합니다.
  
Microsoft Enterprise 이동성 제품군 (EMS) 직원에 게 조직의 데이터를 보호 하는 동안 자신의 좋아하는 앱 및 장치를 사용 하 여 생산성을 유지 도움이 됩니다. 자세한 내용은 [엔터프라이즈 이동성 + 보안 (EMS)를](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)참조 하십시오.
  
장치 수준에서 보안을 적용해야 하면 Microsoft Intune에 장치를 등록해야 합니다. 장치 등록은 조직의 법적 정책을 기준으로 회사 소유 장치와 개인(BYOD) 및 공유 장치를 관리합니다.
  
이 문서에서 제공 하는 지침을 따르면를 등록 하 고 Microsoft 365 개발/테스트 환경에서 iOS 및 Android 장치에 대 한 기본 모바일 장치 관리 기능을 테스트 하는 작업을 할 수 있습니다.
  
## <a name="phase-1-create-your-microsoft-365-devtest-environment"></a>1 단계: Microsoft 365 개발/테스트 환경 만들기

[개발/테스트 환경에서 Microsoft 365 Enterprise의](the-microsoft-365-enterprise-dev-test-environment.md)에서 지시를 따릅니다.
  
## <a name="phase-2-customize-the-microsoft-intune-company-portal-app"></a>2단계: Microsoft Intune 회사 포털 앱 사용자 지정

이러한 단계를 사용하여 가상 회사의 Microsoft Intune 회사 포털 앱을 사용자 지정합니다.
  
1. 새 탭에 있는 Microsoft Intune 관리 콘솔 ([https://manage.microsoft.com](https://manage.microsoft.com))을 엽니다.
    
2. 탐색 창의 **관리** 를 클릭 하 고 **관리** 창에서 **모바일 장치 관리** 를 차례로 클릭 합니다.
    
3. **작업** 목록에서 **모바일 장치 관리 기관 설정**을 선택 합니다. **Microsoft Intune**로 설정 되어 있는지 확인 합니다.
    
4. **관리** 창에서 **회사 포털**을 클릭 합니다.
    
5. **회사 포털** 창에서 다음 설정을 구성 합니다.
    
  - 회사 이름: \<가상의 회사 이름 >
    
  - IT 부서에 대 한 대화 상대 이름: **User5**
    
  - IT 부서 전화번호: **555-1234**
    
  - IT 부서 전자 메일 주소: **@ User5**\<가상의 조직 이름 > **. onmicrosoft.com** (User5 계정의 전자 메일 주소)
    
6. **사용자 지정** **테마 색**에서 **녹색** 선택 합니다.
    
7. **저장**을 클릭 합니다.
    
다음으로 Microsoft Intune 회사 포털 앱을 설치하고 iOS 또는 Android 장치를 등록한 다음 Microsoft Intune 관리 콘솔에서 기본 관리 기능을 테스트합니다.
  
## <a name="phase-3-for-ios-devices-only-enroll-and-manage-an-ios-device"></a>3단계(iOS 장치만 해당): iOS 장치 등록 및 관리

Intune에서 관리할 iOS 장치를 등록하려면 다음 항목이 필요합니다.
  
- Apple iPad 또는 iPhone과 같은 iOS 장치.
    
- IOS 장치 암호에 대 한 지식입니다.
    
- Apple ID (계정 이름 및 암호). 수행 하지 이미 있는 경우, [Apple ID 웹사이트](https://appleid.apple.com/#!&amp;page=signin) 로 이동 하 고 **Apple ID 만들기**를 클릭 합니다. Office 365 구독의 전역 관리자 계정에 대응 하는 Apple ID를 만듭니다. 안전한 위치에 새 Apple ID 계정 이름 및 암호를 기록 합니다.
    
Intune에서 iOS 및 Mac 장치를 관리하려면 APN(Apple Push Notification service) 인증서가 있어야 합니다. Intune에 인증서가 추가되면 사용자가 Microsoft Intune 회사 포털 앱을 설치하여 장치를 등록하거나 관리자가 회사 소유 iOS 장치 관리를 설정할 수 있습니다.
  
Apple Push Certificates 포털에서 트러스트 관계 인증서를 요청하려면 인증서 서명 요청 파일이 있어야 합니다. 인증서 서명 요청 파일을 가져오려면:
  
1. Microsoft Intune 관리 콘솔에서 탐색 창에서 **관리** 를 클릭 합니다.
    
    **관리** 창에서 엽니다 **모바일 장치 관리 > iOS 및 Mac OS X**, 다음 **작업**에 **한 apn을 사용할 인증서를 업로드** 를 클릭 하 고 있습니다. 
    
2. **한 apn을 사용할 인증서를 업로드** 창에서 **다운로드 한 apn을 사용할 인증서 요청을**클릭 합니다. 이름 **개발자 테스트**를 사용 하 여 로컬로 요청 (.csr) 파일에 서명 인증서를 저장 합니다.
    
Apple Push Notification Service 인증서를 가져오려면:
  
1. 새 탭 열기 [Apple 푸시 인증서 포털](https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=3fbfc9ad8dfedeb78be1d37f6458e72adc3160d1ad5b323a9e5c5eb2f8e7e3e2&amp;rv=2)이동 하 고가 프로그램 Apple ID로 로그인
    
2. **시작** 페이지에서 **인증서 만들기**를 클릭 합니다.
    
3. **사용 약관** 페이지에서 **읽어야 하는 이러한 조건 및 조건에 동의**선택 하 고 **수락**을 클릭 합니다.
    
4. **새 푸시 인증서 만들기** 페이지에서 이전 절차에서 저장 한 **개발 test.csr** 파일 **찾아보기** 를 클릭 선택한 다음 **업로드**를 클릭 합니다. Json 파일을 열려면 대화 상자가 나타나면 개발 test.csr 파일이 저장 된 동일한 폴더에 저장 합니다.
    
5. Open [Apple 푸시 인증서 포털](https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=3fbfc9ad8dfedeb78be1d37f6458e72adc3160d1ad5b323a9e5c5eb2f8e7e3e2&amp;rv=2) 다른 탭에 있는 및 **타사 서버에 대 한 인증서**대 한 **다운로드**를 클릭 합니다.
    
6. .Pem 파일을 열려면 대화 상자가 나타나면 이름 **개발 test.pem** 개발 test.csr 파일이 저장 된 동일한 폴더에 함께 저장 합니다. 한 apn을 사용할 인증서입니다.
    
APN 인증서를 Intune에 업로드하려면:
  
1. Microsoft Intune 관리 콘솔 탭 **한 apn을 사용할 인증서를 업로드** 페이지에 **업로드 한 apn을 사용할 인증서를**클릭 합니다.
    
2. **찾아보기** 를 클릭 하 고 **개발 test.pem** 파일을 지정 합니다.
    
3. **열기**를 클릭 하 고 Apple ID 계정 이름을 입력 한 다음 **업로드**를 클릭 합니다. **IOS 및 MaxOS X 모바일 장치 관리 설정** 페이지에서 **등록에 대 한 준비가 된** 메시지를 표시 됩니다.
    
이제 설치된 APN 인증서를 통해 Intune에서 등록된 모바일 장치에 정책을 푸시하여 iOS 장치를 등록하고 관리할 수 있습니다.
  
Microsoft Intune 회사 포털 앱을 다운로드하고 iOS 장치를 등록하려면:
  
1. iOS 장치에서 Apple ID로 로그인합니다.
    
2. **Apple 스토어** 앱을 엽니다.
    
3. 검색 상자에 **intune** 를 입력 하 고 **Microsoft Intune 회사 포털**을 한 다음 **가져오기**, 하 고 **설치**를 누릅니다.
    
4. 설치, **열기**를 누릅니다.
    
5. **Intune 회사 포털** 화면에서 Office 365 전역 관리자 계정을 사용 하 여 로그인 합니다.
    
6. **회사 액세스 설치** 화면에서 **시작**을 누른 다음 **계속** 을 두번 누릅니다.
    
7. **기능 가져온 다음?** 화면에서 **등록**을 누릅니다.
    
8. **활성화 장치의 관리자에 게?** 화면에서 **활성화**를 누릅니다.
    
9. **프로필 관리** 화면에서 **설치**를 누릅니다.
    
10. **암호를 입력**하면 iOS 장치 암호를 입력 합니다.
    
11. **어떤 가져온 다음** 화면에서 **등록**을 누릅니다.
    
12. **프로 파일 설치** **설치**를 누릅니다.
    
13. **경고** 페이지에서 **설치**를 누릅니다.
    
14. **원격 관리** **신뢰**를 누릅니다.
    
15. 등록 프로세스를 완료 하려면 **완료** 를 누릅니다.
    
16. 것인지 묻는 메시지가 나타나면 **"포털 Comp"에서이 페이지를 열고?**, **열기**를 누릅니다.
    
17. **회사 액세스 설치** 화면에서 **시작**을 누른 다음 **완료**를 누릅니다.
    
18. Microsoft Intune 회사 포털 앱의 기본 화면에 다음 항목이 표시됩니다.
    
  - 녹색 배너.
    
  - 가상 회사 이름(왼쪽 위).
    
  - **내 장치**에 나열 된 사용자 iOS 장치 이름입니다.
    
  - **헬프데스크** 섹션- **555-1234** 및 **전자 메일 하 여 대화 상대** 단추 전화번호와 **User5** **대화 상대 이름** .
    
Microsoft Intune에서는 원격 잠금 및 암호 초기화 기능을 모두 제공합니다. 장치를 분실한 경우 원격으로 장치를 잠글 수 있습니다. 암호를 잊은 경우 원격으로 암호를 제거할 수 있습니다.
  
원격으로 iOS 장치를 잠그려면:
  
1. 브라우저의 Microsoft Intune 관리 콘솔 탭에서 관리 컴퓨터에서의 왼쪽된 탐색 영역에서 **그룹** 을 클릭 합니다.
    
2. **그룹** 창에서 엽니다 **모든 장치 > 모든 모바일 장치 > 모두 직접 관리 하는 장치**합니다.
    
3. **모든 직접 관리 하는 장치** 창에서 **장치** 탭을 클릭 합니다.
    
4. 장치 목록에서 해당하는 iOS 장치를 클릭합니다.  
    
5. iOS 장치에서 기본 화면이 표시되도록 합니다.  
    
6. 작업 표시줄에서 사용자 관리 컴퓨터에서 클릭 **원격 작업 > 원격 잠금**합니다. 잠금 화면으로 전환 하는 것 처럼 iOS 장치를 시청 합니다.
    
암호를 제거하려면:
  
1. **모든 직접 관리 하는 장치** 창에서 관리 컴퓨터에서 **장치** 탭을 클릭 합니다.
    
2. 목록에서 iOS 장치를 클릭 합니다. 작업 표시줄에서 클릭 **원격 작업 > 암호 재설정**합니다. 1 분까지 기다립니다.
    
3. IOS 장치에서 잠금을 해제 하 고 암호 더이상 인지 확인 합니다. 암호를 다시을 변경 하려면 **설정**하 고 다음 **암호**으로 이동 합니다.
    
## <a name="phase-3-for-android-devices-only-enroll-and-manage-an-android-device"></a>3단계(Android 장치만 해당): Android 장치 등록 및 관리

Intune에서 관리할 Android 장치를 등록하려면 다음 항목이 필요합니다.
  
- Android 장치.
    
- 장치의 암호에 대 한 지식입니다.
    
Intune 회사 포털 앱을 다운로드하고 Android 장치를 등록하려면:
  
1. Android 장치에서 **Google 재생 저장소**이동 하 고 **시작**을 누릅니다.
    
2. 검색 상자에 **intune** 를 입력 하 고 검색 결과에서 **intune 회사 포털** 누릅니다.
    
3. **Intune 회사 포털** 항목을 누른 다음 **설치**를 누릅니다.
    
4. **계정 설정에 대 한 전체** 화면에 **계속**하 고 다음 **건너뛰기**를 누릅니다.
    
5. **Intune 회사 포털** **수락**을 누릅니다. 앱 설치 합니다.
    
6. **열기**를 누른 다음 **로그인**을 누릅니다.
    
7. **Intune 회사 포털** 화면에서 Office 365 전역 관리자 계정을 사용 하 여 로그인 합니다.
    
8. **회사 액세스 설정** 화면에서 두번 **시작**및 **계속** 누릅니다.
    
9. **기능 가져온 다음?** 화면에서 **등록**을 누릅니다.
    
10. **활성화 장치의 관리자에 게?** 화면에서 누릅니다 **활성화.**
    
11. **개인정보 보호 정책** 화면에서 **읽었으며** 선택 하 고 **확인**을 누릅니다. 등록 프로세스를 완료할 때까지 기다립니다.
    
12. **회사 액세스 설치** 화면에서 **계속**누른 다음 **완료**를 누릅니다.
    
13. Microsoft Intune 회사 포털 앱의 기본 화면 왼쪽 위에 녹색 배너와 가상 회사 이름이 표시됩니다.
    
14. **내 장치**를 누릅니다. Android 장치 이름 목록에 표시 됩니다.
    
15. **IT 대화 상대**를 누릅니다. **User5**의 대화 상대는 IT 및 **555-1234**, **전자 메일에 게 문의** 하는 버튼의 전화번호를 참조 해야 합니다.
    
Microsoft Intune에서는 원격 잠금 및 암호 초기화 기능을 모두 제공합니다. 장치를 분실한 경우 원격으로 장치를 잠글 수 있습니다. 암호를 잊은 경우 원격으로 암호를 초기화할 수 있습니다.
  
원격으로 Android 장치를 잠그려면:
  
1. 브라우저의 Microsoft Intune 관리 콘솔 탭에서 관리 컴퓨터에서의 왼쪽된 탐색 영역에서 **그룹** 을 클릭 합니다.
    
2. **그룹** 창에서 엽니다 **모든 장치 > 모든 모바일 장치 > 모두 직접 관리 하는 장치**합니다.
    
3. **모든 직접 관리 하는 장치** 창에서 **장치** 탭을 클릭 합니다.
    
4. 장치 목록에서 해당하는 Android 장치를 클릭합니다.  
    
5. Android 장치에서 기본 화면이 표시되도록 합니다.  
    
6. 작업 표시줄에서 사용자 관리 컴퓨터에서 클릭 **원격 작업 > 원격 잠금**합니다. 대화 상자가 나타나면 **예**를 클릭 합니다.
    
7. Android 장치가 잠금 화면으로 전환되는 것을 확인합니다.
    
Android 장치에 대 한 암호를 다시 설정할 때 Intune 관리 포털을 생성 하 고 강력한 암호를 구성 합니다.
  
원격으로 암호를 초기화하려면:
  
1. 관리 컴퓨터의 **모든 직접 관리 하는 장치** 창에서 브라우저를 Microsoft Intune 관리 콘솔 탭에서 Android 장치를 클릭 합니다.
    
2. 작업 표시줄에서 클릭 **원격 작업 > 암호 재설정**합니다.
    
3. **원격 작업: 암호 재설정** 메시지를 표시, **예**를 클릭 합니다. 1 분까지 기다립니다.
    
4. **모든 직접 관리 하는 장치** 창에서 **속성 보기를**클릭 합니다.
    
5. **암호 다시 설정**아래에서 새 암호를 note 합니다.
    
6. Android 장치에서 잠금 화면의 새 암호를 입력합니다.  
    
7. 암호를 다시을 변경 하려면 **설정**으로 이동, **장치**를 누릅니다, 그리고 **잠금 화면**을 누릅니다, 그리고은 암호에 대 한 새 암호를 다시, 누르고 **화면 잠금 기능**및 사용자가 선택한을 입력 합니다.
    
> [!TIP]
> [여기](http://aka.ms/catlgstack)를 클릭하여 One Microsoft 클라우드 테스트 랩 가이드 스택의 모든 기사에 대한 가상 맵을 확인할 수 있습니다.
  
## <a name="see-also"></a>참고 항목

[Microsoft 365 엔터프라이즈 개발/테스트 환경](the-microsoft-365-enterprise-dev-test-environment.md)
  
[Microsoft 365 엔터프라이즈 개발/테스트 환경에 대 한 MAM 정책](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[클라우드 도입 TLG(테스트 랩 가이드)](cloud-adoption-test-lab-guides-tlgs.md)

[엔터프라이즈 이동성 + 보안 (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


