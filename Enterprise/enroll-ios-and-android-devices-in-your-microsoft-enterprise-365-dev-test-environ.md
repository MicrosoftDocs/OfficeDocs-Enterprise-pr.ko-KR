---
title: IOS 및 Microsoft 기업 365 개발/테스트 환경에서 Android 장치 등록
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/14/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: 요약:이 테스트 랩 가이드를 사용 하 여 Microsoft 365 개발/테스트 환경에서 장치를 등록 하 고 원격으로 관리 하기를.
ms.openlocfilehash: b5ceecd74ac010d787bc580054d5dd43db952fef
ms.sourcegitcommit: 29c8571ca4912549bac55ec9d1642d21eba5b0e4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/16/2018
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-devtest-environment"></a>IOS 및 Microsoft 기업 365 개발/테스트 환경에서 Android 장치 등록

 **요약:** 이 테스트 랩 가이드를 Microsoft 365 개발/테스트 환경에서 장치를 등록 하 고 원격으로 관리 하기를 사용 합니다.
  
Microsoft Enterprise 이동성 제품군 (EMS) 직원에 게 조직의 데이터를 보호 하는 동안 자신의 좋아하는 앱 및 장치를 사용 하 여 생산성을 유지 도움이 됩니다. 자세한 내용은 [엔터프라이즈 이동성 + 보안 (EMS)를](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)참조 하십시오.
  
장치 수준에서 보안을 적용 해야하는 경우에 Microsoft Intune에 장치를 등록 해야 합니다. 장치 등록 뿐아니라를 사용 하면 조직 소유의 장치를 관리할 수 (BYOD) 개인 및 공유 장치를 조직에 따라서는 법적 수도 있지만 정책입니다.
  
이 문서에서 제공 하는 지침을 따르면를 등록 하 고 Microsoft 365 개발/테스트 환경에서 iOS 및 Android 장치에 대 한 기본 모바일 장치 관리 기능을 테스트 하는 작업을 할 수 있습니다.
  
## <a name="phase-1-create-your-microsoft-365-devtest-environment"></a>1 단계: Microsoft 365 개발/테스트 환경 만들기

[개발/테스트 환경에서 Microsoft 365 Enterprise의](the-microsoft-365-enterprise-dev-test-environment.md)에서 지시를 따릅니다.
  
## <a name="phase-2-enroll-your-ios-and-android-devices"></a>2 단계: iOS 및 Android 장치 등록

먼저,의 지침을 사용 하 여 [설치 회사 포털 응용 프로그램에 로그인 하 고](https://docs.microsoft.com/intune-user-help/install-and-sign-in-to-the-intune-company-portal-app-ios) 개발/테스트 테 넌 트에 대 한 Microsoft Intune 회사 포털 응용 프로그램을 사용자 지정할 수 있습니다.

다음으로 iOS 장치를 등록 하려면 [회사 리소스에 대 한 액세스를 설정](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios) 하는의 지침을 따르십시오.

다음으로, Android 장치와 등록 [등록 Intune에서 Android 장치에서](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android) 에서 지침을 따르십시오.

## <a name="phase-2-manage-your-ios-and-android-devices-remotely"></a>2 단계: iOS 및 Android 장치를 원격으로 관리

Microsoft Intune에서는 원격 잠금 및 암호 초기화 기능을 모두 제공합니다. 장치를 분실한 경우 원격으로 장치를 잠글 수 있습니다. 암호를 잊은 경우 원격으로 암호를 제거할 수 있습니다.
  
원격으로 iOS 장치를 잠그려면:
  
1.  새 탭을 열고 이동 http://manage.microsoft.com (필요한 경우). 

2.  브라우저의 Microsoft Intune 관리 콘솔에서의 왼쪽된 탐색 영역에서 **그룹** 을 클릭 합니다.

3. **그룹** 창에서 엽니다 **모든 장치 > 모든 모바일 장치 > 모두 직접 관리 하는 장치**합니다.
    
4. **모든 직접 관리 하는 장치** 창에서 **장치** 탭을 클릭 합니다.
    
5. 장치 목록에서 해당하는 iOS 장치를 클릭합니다.  
    
6. iOS 장치에서 기본 화면이 표시되도록 합니다.  
    
7. 작업 표시줄에서 사용자 관리 컴퓨터에서 클릭 **원격 작업 > 원격 잠금**합니다. 잠금 화면으로 전환 하는 것 처럼 iOS 장치를 시청 합니다.
    
암호를 제거하려면:
  
1. **모든 직접 관리 하는 장치** 창에서 관리 컴퓨터에서 **장치** 탭을 클릭 합니다.
    
2. 목록에서 iOS 장치를 클릭 합니다. 작업 표시줄에서 클릭 **원격 작업 > 암호 재설정**합니다. 1 분까지 기다립니다.
    
3. IOS 장치에서 잠금을 해제 하 고 암호 더이상 인지 확인 합니다. 암호를 다시을 변경 하려면 **설정**하 고 다음 **암호**으로 이동 합니다.
    
원격으로 Android 장치를 잠그려면:
  
1. 브라우저의 Microsoft Intune 관리 콘솔에서의 왼쪽된 탐색 영역에서 **그룹** 을 클릭 합니다.
    
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

[Microsoft 365 Enterprise 개발/테스트 환경](the-microsoft-365-enterprise-dev-test-environment.md)
  
[Microsoft 365 Enterprise 개발/테스트 환경용 MAM(모바일 응용 프로그램 관리) 정책](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[클라우드 도입 TLG(테스트 랩 가이드)](cloud-adoption-test-lab-guides-tlgs.md)

[엔터프라이즈 이동성 + 보안 (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


