---
title: "Microsoft 365 엔터프라이즈 개발/테스트 환경에 대 한 MAM 정책"
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
ms.assetid: 1aa9639b-2862-49c4-bc33-1586dda636b8
description: "요약:이 테스트 랩 가이드를 사용 하 여 EMS 모바일 응용 프로그램 관리 (MAM) 정책 Microsoft 365 개발/테스트 환경에 추가 합니다."
ms.openlocfilehash: 9eb636fe14b2fbd1fe45fb7dac528a0d4e31be36
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/09/2018
---
# <a name="mam-policies-for-your-microsoft-365-enterprise-devtest-environment"></a>Microsoft 365 엔터프라이즈 개발/테스트 환경에 대 한 MAM 정책

 **요약:** 이 테스트 랩 가이드를 사용 하 여 Microsoft 365 개발/테스트 환경에 EMS 모바일 응용 프로그램 관리 (MAM) 정책을 추가 합니다.
  
Microsoft 엔터프라이즈 이동성 + 보안 (EMS) 직원에 게 조직의 데이터를 보호 하는 동안 자신의 좋아하는 앱 및 장치를 사용 하 여 생산성을 유지 하는데 도움이 됩니다. 자세한 내용은 [엔터프라이즈 이동성 + 보안 (EMS)를](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)참조 하십시오.
  
이 문서의 지침을과 함께 Microsoft 365 개발/테스트 환경에 모바일 응용 프로그램 관리 (MAM) 정책을 추가 합니다.
  
## <a name="phase-1-build-out-your-microsoft-365-devtest-environment"></a>1 단계: Microsoft 365 개발/테스트 환경을 구축합니다

[개발/테스트 환경에서 Microsoft 365 Enterprise의](the-microsoft-365-enterprise-dev-test-environment.md)에서 지시를 따릅니다.
  
## <a name="phase-2-create-and-deploy-mam-policies-for-ios-and-android-devices"></a>2단계: iOS 및 Android 장치용으로 MAM 정책 만들고 배포하기

이 단계에서는 두 개의 다른 MAM 정책을 만들고 배포할 수 있습니다. 하나는 iOS 장치용이며 하나는 Android 장치용입니다.
  
1. Office 365 포털 ([https://portal.office.com](https://portal.office.com))에 이동 하 고 전역 관리자 계정 사용 하 여 Office 365 평가판 구독에 로그인 합니다.
    
2. 브라우저의 새 탭에서 Azure 포털 ([https://azure.portal.com](https://azure.portal.com)) 열고 프로그램 Office 365 전역 관리자 계정을 사용 하 여 로그인 합니다.
    
3. 탐색 창에서 Internet Explorer에서 포털 Azure 탭에서 **더 많은 서비스** (또는 오른쪽 화살표)를 클릭 하 고 **Intune**입력 **Intune**를 클릭 한 다음 합니다.
    
4. 왼쪽 탐색 창에서 **그룹**을 클릭합니다.
    
5. **사용자 및 그룹 모든 그룹** 블레이드에서 **추가**클릭 합니다.
    
6. **멤버 자격 종류**에 **할당 됨** 을 선택 **iOS 장치 사용자를 관리 되는** **이름**입력을 **그룹** 블레이드에서 **예** 에 대 한 선택 **를 사용 하도록 설정 하는 Office 기능?**, 다음 **만들기**를 클릭 하 고 있습니다. 
    
7. **그룹** 블레이드를 닫습니다.
    
8. **사용자 및 그룹 모든 그룹** 블레이드에서 **추가**클릭 합니다.
    
9. 사이트 **멤버 자격 종류**에 **할당 됨** 을 선택 **Android 관리 되는 장치 사용자** **이름**입력 하 고을 **그룹** 블레이드에서를 **예** 에 대 한 선택 **를 사용 하도록 설정 하는 Office 기능?**, 다음 **만들기**를 클릭 하 고 합니다.
    
10. **사용자 및 그룹 모든 그룹** 블레이드를 닫습니다.
    
11. **Intune** 블레이드 **빠른 작업** 목록에서 **준수 정책 만들기**를 클릭 합니다.
    
12. **규정 준수 정책 프로필** 블레이드 **정책 만들기**를 클릭 합니다.
    
13. **정책 만들기** 블레이드 **이름** **iOS**를 입력 합니다. **플랫폼** **iOS**, 선택한 **iOS 규정 준수 정책** 블레이드에서 **확인** 을 클릭 한 다음 **만들기**를 클릭 합니다.
    
14. **규정 준수 정책 프로필** 블레이드 **정책 만들기**를 클릭 합니다.
    
15. **정책 만들기** 블레이드 **이름**, **Android**을 입력 합니다. **플랫폼** **Android**선택, **Android 규정 준수 정책** 블레이드에서 **확인** 을 클릭 하 고 **만들기**를 클릭 합니다.
    
16. **규정 준수 정책 프로필** 블레이드 **Android** 정책 이름을 클릭 합니다.
    
17. **Android-속성** 블레이드의 왼쪽 탐색 영역에서 **할당**을 클릭 하 고 **그룹을 선택 합니다.**를 클릭 합니다.
    
18. **그룹을 선택** 블레이드 **Android 관리 되는 장치 사용자** 그룹을 클릭 하 고 **선택**을 클릭 합니다.
    
19. **저장**을 클릭 하 고 **Android-배정** 블레이드를 닫습니다.
    
20. **규정 준수 정책 프로필** 블레이드 **iOS** 정책 이름을 클릭 합니다.
    
21. **IOS-속성** 블레이드의 왼쪽 탐색 영역에서 **할당**을 클릭 하 고 **그룹을 선택 합니다.**를 클릭 합니다.
    
22. **그룹 선택** 블레이드 **관리 되는 iOS 장치 사용자** 그룹을 클릭 하 고 **선택**을 클릭 합니다.
    
23. **저장**을 클릭 하 고 **iOS-배정** 블레이드를 닫습니다.
    
24. **규정 준수 정책 프로필** 블레이드를 닫습니다.
    
25. **Intune** 블레이드에서의 왼쪽된 탐색 영역에서 **관리 앱** 을 클릭 합니다.
    
26. **모바일 앱** 블레이드 **앱**을 클릭 합니다.
    
27. 앱 목록에서 **PowerPoint**클릭 합니다. 
    
28. **PowerPoint 개요** 블레이드 클릭 **할당 > 그룹을 선택 > 관리 되는 iOS 장치 > 선택**합니다. **형식** **가능 시간**선택 하 고 **저장**을 클릭 합니다.
    
29. 다음 앱은 28단계를 반복합니다.
    
  - Android용 Outlook
    
  - iOS용 Word
    
  - IOS용 Excel
    
  - iOS용 Outlook
    
  - iOS용 iPad의 Microsoft Dynamics CRM
    
  - iOS용 iPhone의 Microsoft Dynamics CRM
    
  - Android 휴대폰용 Dynamics CRM
    
  - Android 태블릿용 Dynamics CRM
    
  - Android용 Excel
    
  - Android용 Word
    
  - iOS용 OneNote
    
30. **모바일 응용 프로그램-응용 프로그램** 블레이드를 닫습니다.
    
31. **모바일 앱** 블레이드 **App 보호 정책**을 클릭 합니다.
    
32. **응용 프로그램 보호 정책** 블레이드에서 **정책을 추가**클릭 합니다.
    
33. **추가 정책** 블레이드에서 **iOS**입력 하 고 **필요한 앱을 선택 합니다.**를 클릭 합니다.
    
34. **앱** 블레이드에서 **PowerPoint**, **iPhone에서 Microsoft Dynamics CRM**, **Excel**, **iPhone에서 Microsoft Dynamics CRM**, **단어**, **OneNote**및 **Outlook**누르고 **을 선택**합니다.
    
35. **추가 정책** 블레이드에서 **만들기**를 클릭 합니다.
    
36. **응용 프로그램 보호 정책** 블레이드에서 **정책을 추가**클릭 합니다.
    
37. **추가 정책** 블레이드에서 입력 **Android** **Android** **플랫폼**선택한 다음 **필요한 앱을 선택 합니다.**를 클릭 합니다.
    
38. **앱** 블레이드에서 **PowerPoint**, **태블릿에 대 한 Dynamics CRM**, **Excel**, **Word**, **Outlook**및 **전화에 대 한 Dynamics CRM**누르고 **을 선택**합니다.
    
39. **추가 정책** 블레이드에서 **만들기**를 클릭 합니다.
    
이제 iOS 장치용과 Android 장치용의 두 가지 MAM 정책이 있으며 선택한 앱의 설정 테스트를 실험할 준비가 되었습니다.
  
> [!TIP]
> [여기](http://aka.ms/catlgstack)를 클릭하여 One Microsoft 클라우드 테스트 랩 가이드 스택의 모든 기사에 대한 가상 맵을 확인할 수 있습니다.
  
## <a name="see-also"></a>참고 항목

[Microsoft 365 엔터프라이즈 개발/테스트 환경](the-microsoft-365-enterprise-dev-test-environment.md)
  
[IOS 및 Microsoft 기업 365 개발/테스트 환경에서 Android 장치 등록](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
  
[클라우드 도입 TLG(테스트 랩 가이드)](cloud-adoption-test-lab-guides-tlgs.md)

[엔터프라이즈 이동성 + 보안 (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


