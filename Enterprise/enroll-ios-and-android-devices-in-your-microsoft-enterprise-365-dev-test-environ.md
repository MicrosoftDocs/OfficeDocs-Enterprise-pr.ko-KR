---
title: Microsoft 365 Enterprise 개발/테스트 환경에서 iOS 및 Android 장치 등록
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/20/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: 요약:이 테스트 랩 가이드를 사용 하 여 Microsoft 365 개발/테스트 환경에서 장치를 등록 하 고 원격으로 관리 하기를.
ms.openlocfilehash: e4b8491a70d0d0177e0a434d228136243201e788
ms.sourcegitcommit: c3869a332512dd1cc25cd5a92a340050f1da0418
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/20/2018
ms.locfileid: "20720414"
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-365-enterprise-devtest-environment"></a>Microsoft 365 Enterprise 개발/테스트 환경에서 iOS 및 Android 장치 등록

 **요약:** 이 테스트 랩 가이드를 Microsoft 365 개발/테스트 환경에서 장치를 등록 하 고 원격으로 관리 하기를 사용 합니다.
  
Microsoft Enterprise 이동성 제품군 (EMS) 직원에 게 조직의 데이터를 보호 하는 동안 자신의 좋아하는 앱 및 장치를 사용 하 여 생산성을 유지 도움이 됩니다. 자세한 내용은 [엔터프라이즈 이동성 + 보안 (EMS)를](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)참조 하십시오.
  
장치 수준에서 보안을 적용 해야하는 경우에 Microsoft Intune에 장치를 등록 해야 합니다. 장치 등록 뿐아니라를 사용 하면 조직 소유의 장치를 관리할 수 (BYOD) 개인 및 공유 장치를 조직에 따라서는 법적 수도 있지만 정책입니다.
  
이 문서에서 제공 하는 지침을 따르면를 등록 하 고 Microsoft 365 개발/테스트 환경에서 iOS 및 Android 장치에 대 한 기본 모바일 장치 관리 기능을 테스트 하는 작업을 할 수 있습니다.
  
## <a name="phase-1-create-your-microsoft-365-devtest-environment"></a>1 단계: Microsoft 365 개발/테스트 환경 만들기

[개발/테스트 환경에서 Microsoft 365 Enterprise의](the-microsoft-365-enterprise-dev-test-environment.md)에서 지시를 따릅니다.
  
## <a name="phase-2-enroll-your-ios-and-android-devices"></a>2 단계: iOS 및 Android 장치 등록

먼저,의 지침을 사용 하 여 [설치 회사 포털 응용 프로그램에 로그인 하 고](https://docs.microsoft.com/intune-user-help/install-and-sign-in-to-the-intune-company-portal-app-ios) 테스트 환경에 대 한 Microsoft Intune 회사 포털 응용 프로그램을 사용자 지정할 수 있습니다.

다음으로 iOS 장치를 등록 하려면 [회사 리소스에 대 한 액세스를 설정](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios) 하는의 지침을 따르십시오.

다음으로, Android 장치와 등록 [등록 Intune에서 Android 장치에서](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android) 에서 지침을 따르십시오.

## <a name="phase-3-manage-your-ios-and-android-devices-remotely"></a>3 단계: iOS 및 Android 장치를 원격으로 관리

Microsoft Intune 원격 잠금 및 암호를 모두 재설정 기능을 제공 합니다. 다른 사용자가 장치를 잃을 하는 경우 원격으로 장치를 잠글 수 있습니다. 다른 사용자가 자신의 암호를 잊어버린를 원격으로 재설정할 수 있습니다.
  
IOS 또는 Android 장치를 원격으로 잠그려면:

1. Azure 포털에 로그인 [https://portal.azure.com](https://portal.azure.com) 전역 관리자 계정의 자격 증명을 사용 합니다.
2. **모든 서비스**를 클릭 하 고 **Intune**입력 다음 **Intune**를 클릭 합니다.
3. 클릭 **장치 > 모든 장치**합니다.
4. 장치 목록에서 iOS 또는 Android 장치를 클릭 하 고 **원격 잠금** 동작을 클릭 합니다.

    
원격으로 암호를 초기화하려면:

1. 필요한 경우에서 Azure 포털에 로그인 [https://portal.azure.com](https://portal.azure.com) 전역 관리자 계정의 자격 증명을 사용 합니다.
2. **모든 서비스**를 클릭 하 고 **Intune**입력 다음 **Intune**를 클릭 합니다.
3. 클릭 **장치 > 모든 장치**합니다.
4. 관리 장치 목록에서는 iOS 또는 Android 장치를 클릭 한 **선택... 더 많은**합니다. 다음 **암호를 제거** 장치 원격 작업을 선택 합니다.

추가 실험 [사용 가능한 장치에 작업](https://docs.microsoft.com/intune/device-management#available-device-actions)을 참조 하십시오.

    

> [!TIP]
> [여기](http://aka.ms/catlgstack)를 클릭하여 One Microsoft 클라우드 테스트 랩 가이드 스택의 모든 기사에 대한 가상 맵을 확인할 수 있습니다.
  
## <a name="see-also"></a>참고 항목

[Microsoft 365 Enterprise 개발/테스트 환경](the-microsoft-365-enterprise-dev-test-environment.md)
  
[Microsoft 365 Enterprise 개발/테스트 환경용 MAM(모바일 응용 프로그램 관리) 정책](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[클라우드 도입 TLG(테스트 랩 가이드)](cloud-adoption-test-lab-guides-tlgs.md)

[엔터프라이즈 이동성 + 보안 (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


