---
title: "Office 365 개발/테스트 환경에 대 한 디렉터리 동기화"
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
- Strat_O365_Enterprise
ms.custom:
- Strat_O365_Enterprise
- TLG
- Ent_TLGs
ms.assetid: e6b27e25-74ae-4b54-9421-c8e911aef543
description: "요약: Office 365 개발/테스트 환경에 대 한 디렉터리 동기화를 구성 합니다."
ms.openlocfilehash: 8a656ea742af642a8b4dc3e096764f0e8cbde074
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2018
---
# <a name="dirsync-for-your-office-365-devtest-environment"></a>Office 365 개발/테스트 환경에 대 한 디렉터리 동기화

 **요약:** Office 365 개발/테스트 환경에 대 한 디렉터리 동기화를 구성 합니다.
  
많은 조직에서는 사용 Azure AD 연결 및 디렉터리 동기화 (DirSync)의 온-프레미스 Windows Server Active Directory (AD) 포리스트에 Office 365에서 계정 집합에 있는 계정의 집합 동기화 합니다. 이 문서에 추가 하는 방법을 DirSync Office 365 개발/테스트 환경에 대 한 암호 동기화와 다음 구성의 결과 설명 합니다.
  
![DirSync를 사용하는 Office 365 개발/테스트 환경](images/be5b37b0-f832-4878-b153-436c31546e21.png)
  
이 구성은 다음으로 이루어집니다. 
  
- Office 365 e 5 평가판 구독을 만들 때에서 30 일이 지나면 만료는 합니다.
    
- 간소화 된 조직 인트라넷 (d c 1, a p p 1을 및 CLIENT1) Azure 가상 네트워크의 서브넷에 세 가상 컴퓨터의 구성 되는 인터넷에 연결 합니다. Azure AD 연결 Office 365에 Windows Server AD 도메인을 동기화 하는 a p p 1을 실행 합니다.
    
이 개발/테스트 환경 설정 하는 두 단계로 가지가 있습니다.
  
1. Office 365 개발/테스트 환경 (d c 1, a p p 1을 및 CLIENT1 가상 컴퓨터에 Office 365 E5 평가판 구독을 Azure 가상 네트워크를)을 만듭니다.
    
2. 설치 하 고 a p p 1에서 Azure AD 연결을 구성 합니다.
    
> [!TIP]
> 클릭 [여기](http://aka.ms/catlgstack) 에 한 맵이 하나의 Microsoft 클라우드 테스트 랩 가이드 스택의 모든 문서를 시각적으로 표시 합니다.
  
## <a name="phase-1-create-an-office-365-devtest-environment"></a>1 단계: Office 365 개발/테스트 환경 만들기

1, 2 및 [Office 365 개발/테스트 환경](office-365-dev-test-environment.md) 문서의 3 단계에서 지침을 따릅니다. 결과 구성은 다음과 같습니다.
  
![Office 365 개발/테스트 환경](images/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
이 구성은 다음으로 이루어집니다. 
  
- Office 365 e 5 평가판 구독 합니다.
    
- 간소화 된 조직 인트라넷 Azure 가상 네트워크의 서브넷에서 d c 1, a p p 1을 및 CLIENT1 가상 컴퓨터의 구성 되는 인터넷에 연결 합니다.
    
## <a name="phase-2-install-azure-ad-connect-on-app1"></a>2 단계: 설치 Azure AD a p p 1에 연결

설치 및 구성한 후 Azure AD 연결 Office 365 평가판 구독에서 계정 집합으로 CORP Windows Server AD 도메인의 계정 집합을 동기화 합니다. 다음 절차를 안내 Azure AD Connect a p p 1을 설치 하 고 작동 하는지 확인 (영문)를 통해 있습니다.
  
### <a name="install-and-configure-azure-ad-connect-on-app1"></a>설치 하 고 a p p 1에서 Azure AD 연결 구성

1. [Azure 포털](https://portal.azure.com)는 회사와 a p p 1에 연결\\User1 계정을 합니다.
    
2. A p p 1을에서 관리자 수준 Windows PowerShell 명령 프롬프트를 열고 하 고 이러한 명령을 실행 합니다.
    
  ```
  Set-ItemProperty -Path "HKLM:\\SOFTWARE\\Microsoft\\Active Setup\\Installed Components\\{A509B1A7-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Set-ItemProperty -Path "HKLM:\\SOFTWARE\\Microsoft\\Active Setup\\Installed Components\\{A509B1A8-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Stop-Process -Name Explorer -Force

  ```

3. 작업 표시줄에서 **Internet Explorer** 를 클릭 하 고 [https://aka.ms/aadconnect](https://aka.ms/aadconnect)로 이동 합니다.
    
4. Microsoft Azure Active Directory에 연결 페이지에서 **다운로드**를 클릭 한 다음 **실행**을 클릭 합니다.
    
5. **Azure AD 연결을 시작** 페이지에서 **동의 함**를 클릭 한 다음 **계속**을 클릭 합니다.
    
6. **Express 설정** 페이지에서 **express 설정 사용을**클릭 합니다.
    
7. **Azure AD에 연결** 페이지에서 **암호**해당 암호 **사용자 이름,** 형식에 전역 관리자 계정 이름을 입력 하 고 ****을 클릭 합니다.
    
8. **AD DS에 연결** 페이지에서 입력 **CORP\\User1** **사용자 이름** 에서 **암호**를에서 계정의 암호를 입력 하 고 **다음**을 클릭 합니다.
    
9. **Azure AD 로그인 구성** 페이지에서 **확인 된 모든 도메인 키 지 않고 계속**클릭 하 고 ****을 클릭 합니다.
    
10. **구성 준비 완료** 페이지에서 **설치**를 클릭 합니다.
    
11. **구성 완료** 페이지에서 **끝내기**를 클릭 합니다.
    
12. Internet Explorer에서 Office 365 포털 ([https://portal.office.com](https://portal.office.com))로 이동 하 고 전역 관리자 계정 사용 하 여 Office 365 평가판 구독에 로그인 합니다.
    
13. 주 포털 페이지에서 **관리**를 클릭 합니다.
    
14. 왼쪽 탐색 영역에서 클릭 **사용자 > 활성 사용자**합니다.
    
    **사용자 1**이라는 새 계정을 note 합니다. 이 계정은 CORP Windows Server AD 도메인에서 형식이 며 교정본을 디렉터리 동기화 장치가 작동 합니다.
    
15. **User1** 계정을 클릭 합니다. 제품 라이선스에 대 한 **편집**을 클릭 합니다.
    
16. **제품 라이선스**해당 국가 선택 하 고 **Office 365 Enterprise E5** ( **On**으로 전환)에 대 한 **오프** 컨트롤을 클릭 합니다. 페이지의 맨 아래에 **저장** 을 클릭 하 고 **닫기**를 클릭 합니다.
    
결과 구성입니다.
  
![DirSync를 사용하는 Office 365 개발/테스트 환경](images/be5b37b0-f832-4878-b153-436c31546e21.png)
  
이 구성은 다음으로 이루어집니다. 
  
- Office 365 e 5 평가판 구독 합니다.
    
- 간소화 된 조직 인트라넷 Azure 가상 네트워크의 서브넷에서 d c 1, a p p 1을 및 CLIENT1 가상 컴퓨터의 구성 되는 인터넷에 연결 합니다. Azure AD 연결 Office 365에 CORP Windows Server AD 도메인 30 분 마다 동기화 하는 a p p 1을 실행 합니다.
    
## <a name="next-step"></a>다음 단계

조직에 대 한 디렉터리 동기화를 배포할 준비가 되 면 [배포 Office 365에서에서 디렉터리 동기화 (DirSync) Microsoft Azure을](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md)참조 하십시오.

## <a name="see-also"></a>참고 항목

[클라우드 도입 TLG(테스트 랩 가이드)](cloud-adoption-test-lab-guides-tlgs.md)
  
[기본 구성 개발/테스트 환경](base-configuration-dev-test-environment.md)
  
[Office 365 개발/테스트 환경](office-365-dev-test-environment.md)
  
[Office 365 개발/테스트 환경에 대 한 클라우드 응용 프로그램 보안](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[Office 365 개발/테스트 환경에 대 한 위협 보호 고급](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
  
[클라우드 채택 및 하이브리드 솔루션](cloud-adoption-and-hybrid-solutions.md)




