---
title: Office 365 개발/테스트 환경에 대한 디렉터리 동기화
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/18/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: e6b27e25-74ae-4b54-9421-c8e911aef543
description: '요약: Office 365 개발/테스트 환경에 대한 디렉터리 동기화를 구성합니다.'
ms.openlocfilehash: 74457cca2d199fe7bfa8839908b0f6a413890f8a
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487330"
---
# <a name="directory-synchronization-for-your-office-365-devtest-environment"></a>Office 365 개발/테스트 환경에 대한 디렉터리 동기화

 **요약:** Office 365 개발/테스트 환경에 대한 디렉터리 동기화를 구성합니다.
  
많은 조직에서는 Azure AD Connect 및 디렉터리 동기화를 사용하여 온-프레미스 Active Directory Domain Services(AD DS) 포리스트의 계정 집합을 Office 365의 계정 집합과 동기화합니다. 이 문서에서는 암호 해시 동기화를 사용한 디렉터리 동기화를 Office 365 개발/테스트 환경에 추가하여 다음과 같이 구성하는 방법을 설명합니다.
  
![디렉터리 동기화를 사용하는 Office 365 개발/테스트 환경](media/be5b37b0-f832-4878-b153-436c31546e21.png)
  
이 구성은 다음으로 이루어집니다. 
  
- Office 365 E5 평가판 구독: 만들고 30일 후에 만료됩니다.
- 인터넷에 연결된 간소화된 조직 인트라넷: Azure Virtual Network 서브넷에 있는 3개의 가상 머신(DC1, APP1 및 CLIENT1)으로 구성됩니다. Azure AD Connect는 APP1에서 실행되며 AD DS 도메인을 Office 365와 동기화합니다.
    
이 개발/테스트 환경의 2가지 주요 설정 단계는 다음과 같습니다.
  
1. Office 365 개발/테스트 환경을 만듭니다(Office 365 E5 평가판 구독, Azure Virtual Network의 DC1, APP1, and CLIENT1 가상 머신).
2. APP1에 Azure AD Connect를 설치 및 구성합니다.
    
> [!TIP]
> [여기](http://aka.ms/catlgstack)를 클릭하여 Office 365 테스트 랩 가이드 스택의 모든 문서에 대한 가상 맵을 확인할 수 있습니다.
  
## <a name="phase-1-create-an-office-365-devtest-environment"></a>1단계: Office 365 개발/테스트 환경 만들기

[Office 365 개발/테스트 환경](office-365-dev-test-environment.md) 문서의 1, 2 및 3단계 지침을 따릅니다. 구성 결과는 다음과 같습니다.
  
![Office 365 개발/테스트 환경](media/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
이 구성은 다음으로 이루어집니다. 
  
- Office 365 E5 평가판 구독
- 인터넷에 연결된 간소화된 조직 인트라넷: Azure Virtual Network 서브넷에 있는 DC1, APP1 및 CLIENT1 가상 머신으로 구성됩니다.
    
## <a name="phase-2-install-azure-ad-connect-on-app1"></a>2단계: APP1에 Azure AD Connect 설치

일단 설치 및 구성되면, Azure AD Connect는 CORP AD DS 도메인의 계정 집합을 Office 365 평가판 구독의 계정 집합과 동기화합니다. 다음 절차에서는 APP1에 Azure AD Connect를 설치하고 작동하는지 확인하는 과정을 안내합니다.
  
### <a name="install-and-configure-azure-ad-connect-on-app1"></a>APP1에 Azure AD Connect 설치 및 구성

1. [Azure Portal](https://portal.azure.com)에서 CORP\\User1 계정을 사용하여 APP1에 연결합니다.
    
2. APP1에서 관리자 수준 Windows PowerShell 명령 프롬프트를 열고 다음 명령을 실행합니다.
    
  ```
  Set-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Active Setup\Installed Components\{A509B1A7-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Set-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Active Setup\Installed Components\{A509B1A8-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Stop-Process -Name Explorer -Force

  ```

3. 작업 표시줄에서 **Internet Explorer**를 클릭하고 [https://aka.ms/aadconnect](https://aka.ms/aadconnect)로 이동합니다.
    
4. Microsoft Azure Active Directory Connect 페이지에서 **다운로드**를 클릭하고 **실행**을 클릭합니다.
    
5. **Azure AD Connect 시작** 페이지에서 **동의**를 클릭하고 **계속**을 클릭합니다.
    
6. **기본 설정** 페이지에서 **기본 설정 사용**을 클릭합니다.
    
7. **Azure AD에 연결** 페이지에서 **사용자 이름**에 전역 관리자 계정 이름을 입력하고 **암호**에 해당 암호를 입력한 후 **다음 **을 클릭합니다.
    
8. **AD DS에 연결** 페이지에서 **사용자 이름**에 **CORP\\User1**을 입력하고 **암호**에 암호를 입력한 후 **다음**을 클릭합니다.
    
9. **Azure AD 로그인 구성** 페이지에서 **확인된 도메인 없이 계속**을 클릭한 후 **다음**을 클릭합니다.
    
10. **구성 준비 완료** 페이지에서 **설치**를 클릭합니다.
    
11. **구성 완료** 페이지에서 **끝내기**를 클릭합니다.
    
12. Internet Explorer에서 Microsoft 365 관리 센터([https://admin.microsoft.com](https://admin.microsoft.com))로 이동한 후 전역 관리자 계정으로 Office 365 평가판 구독에 로그인합니다.
    
13. 기본 포털 페이지에서 **관리자**를 클릭합니다.
    
14. 왼쪽 탐색에서 **사용자 > 활성화된 사용자**를 클릭합니다.
    
    **User1** 계정을 확인합니다. 이 계정은 CORP AD DS 도메인에서 가져온 것이며 디렉터리 동기화가 진행되었다는 증거입니다.
    
15. **User1** 계정을 클릭합니다. 제품 라이선스에 대해 **편집**을 클릭합니다.
    
16. **제품 라이선스**에서 국가를 선택하고 **Office 365 Enterprise E5**에 대해 **해제**를 클릭합니다(**설정**으로 전환됨). 페이지 아래쪽의 **저장**을 클릭하고 **닫기**를 클릭합니다.
    
구성 결과는 다음과 같습니다.
  
![디렉터리 동기화를 사용하는 Office 365 개발/테스트 환경](media/be5b37b0-f832-4878-b153-436c31546e21.png)
  
이 구성은 다음으로 이루어집니다. 
  
- Office 365 E5 평가판 구독
- 인터넷에 연결된 간소화된 조직 인트라넷: Azure Virtual Network 서브넷에 있는 DC1, APP1 및 CLIENT1 가상 머신으로 구성됩니다. Azure AD Connect는 APP1에서 실행되며 30분 간격으로 CORP AD DS 도메인을 Office 365와 동기화합니다.
    
## <a name="next-step"></a>다음 단계

조직에 대한 디렉터리 동기화 배포 준비가 완료되면 [Microsoft Azure에서 Office 365 디렉터리 동기화 배포](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md)를 참조하세요.

## <a name="see-also"></a>참고 항목

[클라우드 도입 TLG(테스트 랩 가이드)](cloud-adoption-test-lab-guides-tlgs.md)

[기본 구성 개발/테스트 환경](base-configuration-dev-test-environment.md)

[Office 365 개발/테스트 환경](office-365-dev-test-environment.md)

[Office 365 개발/테스트 환경용 Cloud App Security](cloud-app-security-for-your-office-365-dev-test-environment.md)

[Office 365 개발/테스트 환경용 Advanced Threat Protection](advanced-threat-protection-for-your-office-365-dev-test-environment.md)

[클라우드 도입 및 하이브리드 솔루션](cloud-adoption-and-hybrid-solutions.md)




