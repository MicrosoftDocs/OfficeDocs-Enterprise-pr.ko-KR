---
title: Microsoft 365 Enterprise 개발/테스트 환경에서 iOS 및 Android 장치 등록
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/14/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: 요약:이 테스트 랩 가이드를 사용 하 여 Microsoft 365 개발/테스트 환경에서 장치를 등록 하 고 원격으로 관리 하기를.
ms.openlocfilehash: a5d43a0ef3ed090f84c8415de3ac26f53fdafe0a
ms.sourcegitcommit: c23b95d32a865e45be7843f38a1f23b5693ba76d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2018
ms.locfileid: "20188106"
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-365-enterprise-devtest-environment"></a>Microsoft 365 Enterprise 개발/테스트 환경에서 iOS 및 Android 장치 등록

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

3. **그룹** 창에서 **모든 장치 > 모든 모바일 장치 > 모든 직접 관리 장치**를 엽니다.
    
4. **모든 직접 관리 장치** 창에서 **장치** 탭을 클릭합니다.
    
5. 장치 목록에서 해당하는 iOS 장치를 클릭합니다.  
    
6. iOS 장치에서 기본 화면이 표시되도록 합니다.  
    
7. 관리자 컴퓨터의 작업 표시줄에서 **원격 작업 > 원격 잠금**을 클릭합니다. iOS 장치가 잠금 화면으로 전환되는 것을 확인합니다.
    
암호를 제거하려면:
  
1. 관리 컴퓨터의 **모든 직접 관리 장치** 창에서 **장치** 탭을 클릭합니다.
    
2. 목록에서 해당하는 iOS 장치를 클릭합니다. 작업 표시줄에서 **원격 작업 > 암호 초기화**를 클릭합니다. 1분 동안 기다립니다.
    
3. iOS 장치에서 잠금 해제하면 암호가 제거된 것을 확인할 수 있습니다. 암호를 다시 변경하려면 **설정**에서 **암호**로 이동합니다.
    
원격으로 Android 장치를 잠그려면:
  
1. 브라우저의 Microsoft Intune 관리 콘솔에서의 왼쪽된 탐색 영역에서 **그룹** 을 클릭 합니다.
    
2. **그룹** 창에서 **모든 장치 > 모든 모바일 장치 > 모든 직접 관리 장치**를 엽니다.
    
3. **모든 직접 관리 장치** 창에서 **장치** 탭을 클릭합니다.
    
4. 장치 목록에서 해당하는 Android 장치를 클릭합니다.  
    
5. Android 장치에서 기본 화면이 표시되도록 합니다.  
    
6. 관리자 컴퓨터의 작업 표시줄에서 **원격 작업 > 원격 잠금**을 클릭합니다. 메시지가 표시되면 **예**를 클릭합니다.
    
7. Android 장치가 잠금 화면으로 전환되는 것을 확인합니다.
    
Android 장치에 대 한 암호를 다시 설정할 때 Intune 관리 포털을 생성 하 고 강력한 암호를 구성 합니다.
  
원격으로 암호를 초기화하려면:
  
1. 관리 컴퓨터 브라우저의 Microsoft Intune 관리 콘솔 탭에 있는 **모든 직접 관리 장치** 창에서 해당하는 Android 장치를 클릭합니다.
    
2. 작업 표시줄에서 **원격 작업 > 암호 초기화**를 클릭합니다.
    
3. **원격 작업: 암호 초기화** 메시지가 표시되면 **예**를 클릭합니다. 1분 동안 기다립니다.
    
4. **모든 직접 관리 장치** 창에서 **속성 보기**를 클릭합니다.
    
5. **암호 초기화**에서 새 암호를 확인합니다.
    
6. Android 장치에서 잠금 화면의 새 암호를 입력합니다.  
    
7. 암호를 다시 변경하려면 **설정**으로 이동하여 **장치** 및 **잠금 화면**을 차례로 누릅니다. 새 암호를 다시 입력하고 **화면 잠금**을 누른 다음 선택한 암호를 누릅니다.
    

> [!TIP]
> [여기](http://aka.ms/catlgstack)를 클릭하여 One Microsoft 클라우드 테스트 랩 가이드 스택의 모든 기사에 대한 가상 맵을 확인할 수 있습니다.
  
## <a name="see-also"></a>참고 항목

[Microsoft 365 Enterprise 개발/테스트 환경](the-microsoft-365-enterprise-dev-test-environment.md)
  
[Microsoft 365 Enterprise 개발/테스트 환경용 MAM(모바일 응용 프로그램 관리) 정책](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[클라우드 도입 TLG(테스트 랩 가이드)](cloud-adoption-test-lab-guides-tlgs.md)

[엔터프라이즈 이동성 + 보안 (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


