---
title: "고가용성 연결 된 인증 Office 365에 대 한 연결 된 인증 단계 5 구성"
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
- Ent_O365_Hybrid_Top
ms.custom:
- DecEntMigration
- Ent_Solutions
ms.assetid: 0f1dbf52-5bff-44cc-a264-1b48641af98f
description: "요약: Microsoft Azure의 Office 365에 대 한 고가용성 연결 된 인증 사용자에 대 한 Azure AD 연결을 구성 합니다."
ms.openlocfilehash: 8340058dc93389d4b2b1e843726bc7e8ef30cdde
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2017
---
# <a name="high-availability-federated-authentication-phase-5-configure-federated-authentication-for-office-365"></a>고가용성 페더레이션 인증 5 단계: Office 365에 대 한 연결 된 인증 구성

 **요약:** Microsoft Azure의 Office 365에 대 한 고가용성 연결 된 인증 사용자에 대 한 Azure AD 연결을 구성 합니다.
 
Azure 인프라 서비스에서 Office 365에 대 한 고가용성 페더레이션된 인증 배포의이 마지막 단계에서 가져올 하 고 공용 인증 기관에서 발급 한 인증서를 설치, 구성, 확인 하 고 설치 하 고 실행 Azure AD 디렉터리 동기화 서버에 연결 합니다. Azure AD 연결 Office 365 구독 및 Active Directory Federation Services (AD FS) 및 연결 된 인증에 대 한 웹 응용 프로그램 프록시 서버를 구성합니다.
  
모든 단계에 대 한 [Azure의 Office 365에 대 한 고가용성 연결 된 인증 배포를](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) 참조 하십시오.
  
## <a name="get-a-public-certificate-and-copy-it-to-the-dirsync-server"></a>공용 인증서를 얻고 디렉터리 동기화 서버에 복사

다음 속성을 갖는 공용 인증 기관에서 디지털 인증서를 가져옵니다.
  
- SSL 연결을 만들기 위한 적합 한 X.509 인증서입니다.
    
- 주체 대체 이름 (SAN) 속성을 확장 페더레이션 서비스 FQDN으로 설정 됩니다 (예: fs.contoso.com).
    
- 인증서 개인 키가 있어야 하 고 PFX 형식에 저장할 수 있습니다.
    
또한 조직 컴퓨터와 장치에서 디지털 인증서를 발급 하는 공용 인증 기관을 신뢰 해야 합니다. 이 트러스트를 컴퓨터와 장치에서 신뢰할 수 있는 루트 인증 기관 저장소에 설치 하는 공용 인증 기관에서 루트 인증서를 사용 함으로써 설정 됩니다. 일반적으로 Microsoft Windows를 실행 하는 컴퓨터에는 이러한 유형의 일반적으로 사용 되는 인증 기관에서 설치 된 인증서 집합이 포함 됩니다. 공용 인증 기관에서 루트 인증서가 아직 설치 되지 않은,이 컴퓨터와 조직의 장치에 배포 해야 합니다.
  
연결 된 인증에 대 한 인증서 요구 사항에 대 한 자세한 내용은 [페더레이션 설치 및 구성에 대 한 필수 구성 요소](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-prerequisites#prerequisites-for-federation-installation-and-configuration)를 참조 하십시오.
  
인증서를 받을 때의 폴더 디렉터리 동기화 서버 c: 드라이브에 복사 합니다. 예, SSL.pfx 파일 이름을 지정 하 고 c: 드라이브에 저장\\디렉터리 동기화 서버에서 인증서 폴더입니다.
  
## <a name="verify-your-configuration"></a>구성 확인

이제 Azure AD 연결 및 Office 365에 대 한 연결 된 인증을 구성 준비가 됩니다. 수 있는지를 확인, 검사 목록을 다음과 같습니다.
  
- Office 365 구독 조직의 공용 도메인 추가 됩니다.
    
- 조직의 Office 365 사용자 계정 조직의 공용 도메인 이름으로 구성 하 고 성공적으로 로그인 할 수 있습니다.
    
- 페더레이션 서비스 FQDN 기반 공용 도메인 이름을 결정 해야 합니다.
    
- 공용 IP 주소를 인터넷 Azure에 페더레이션 서비스 FQDN 포인트에 대 한 공용 DNS A 레코드를 부하 분산 장치는 웹 응용 프로그램 프록시 서버에 대 한 합니다.
    
- 개인 IP 주소에 AD FS 서버에 대 한 내부 Azure 부하 분산 장치에 페더레이션 서비스 FQDN 포인트에 대 한 개인 DNS A 레코드입니다.
    
- 공용 인증 기관 isssued 디지털 인증서를 페더레이션 서비스를 설정 하는 SAN와의 SSL 연결에 대 한 적절 한 FQDN은 디렉터리 동기화 서버에 저장 된 PFX 파일입니다.
    
- 공용 인증 기관에 대 한 루트 인증서가 신뢰할 수 있는 루트 인증 기관에 설치 되어 컴퓨터와 장치에 저장 합니다.
    
Contoso 조직에 대 한 예는 다음과 같습니다.
  
**높은 가용성을 위해 구성의 예는 페더레이션 Azure에서 인증 인프라**

![Azure에서 고가용성 Office 365 페더레이션 인증 인프라의 예제 구성](images/ac1a6a0d-0156-4407-9336-6e4cd6db8633.png)
  
## <a name="run-azure-ad-connect-to-configure-federated-authentication"></a>연결 된 인증을 구성 하려면 Azure AD 연결을 실행 합니다.

Azure AD 연결 도구이 단계와 연결 된 인증에 대 한 AD FS 서버, 웹 응용 프로그램 프록시 서버 및 Office 365를 구성합니다.
  
1. 로컬 관리자 권한이 있는 도메인 계정을 사용 하 여 디렉터리 동기화 서버를 원격 데스크톱 연결을 만듭니다.
    
2. 디렉터리 동기화 서버 바탕 화면에서 Internet Explorer를 열고 [https://aka.ms/aadconnect](https://aka.ms/aadconnect)로 이동 합니다.
    
3. **Microsoft Azure Active Directory에 연결** 페이지에서 **다운로드**를 클릭 한 다음 **실행**을 클릭 합니다.
    
4. **Azure AD 연결을 시작** 페이지에서 **동의 함**클릭 하 고 다음을 클릭 **계속.**
    
5. **Express 설정** 페이지에서 **사용자 지정**을 클릭 합니다.
    
6. **필수 구성 요소 설치** 페이지에서 **설치**를 클릭 합니다.
    
7. **사용자 로그인** 페이지에서 **AD FS와의 페더레이션을 사용**을 클릭 하 고 ****을 클릭 합니다.
    
8. **Azure AD에 연결** 페이지에서 이름 및 Office 365 구독의 전역 관리자 계정의 암호를 입력 하 고 ****을 클릭 합니다.
    
9. **디렉터리에 연결** 페이지에서 온-프레미스 Windows Server AD 포리스트에 **포리스트에서**선택 되어있는지 확인, 이름 및 도메인 관리자 계정의 암호를 입력, **디렉터리 추가**클릭 하 고 ****을 클릭 합니다.
    
10. **Azure AD 로그인 구성** 페이지에서 **다음**을 클릭 합니다.
    
11. **도메인 및 OU 필터링** 페이지에서 **다음**을 클릭 합니다.
    
12. **사용자를 고유 하 게 확인** 페이지에서 **다음**을 클릭 합니다.
    
13. **사용자 및 장치 필터** 페이지에서 **다음**을 클릭 합니다.
    
14. **선택적 기능** 페이지에서 **다음**을 클릭 합니다.
    
15. **AD FS 팜** 페이지에서 **새 AD FS 팜 구성**을 클릭 합니다.
    
16. **찾아보기** 를 클릭 하 고 공용 인증 기관에서 얻은 SSL 인증서의 이름과 위치를 지정 합니다.
    
17. 대화 상자가 나타나면 인증서 암호를 입력 한 다음 **확인**을 클릭 합니다.
    
18. **주체 이름** 및 **페더레이션 서비스 이름** 으로 페더레이션 서비스 FQDN 설정 하 고 **다음**을 클릭 한 다음 되었는지 확인
    
19. **AD FS 서버** 페이지에서 첫번째 AD FS 서버 이름 (테이블 M-항목 4-가상 컴퓨터 이름 열)를 입력 한 다음 **추가**클릭 합니다.
    
20. 두번째 AD FS 서버 이름 (테이블 M-항목 5-가상 컴퓨터 이름 열)를 입력 하 고 **추가**클릭 한 다음 **다음**을 클릭 한 다음 키를 누릅니다.
    
21. **웹 응용 프로그램 프록시 서버** 페이지에서 첫번째 웹 응용 프로그램 프록시 서버의 이름 (테이블 M-항목 6-가상 컴퓨터 이름 열)를 입력 한 다음 **추가**클릭 합니다.
    
22. 두번째 웹 응용 프로그램 프록시 서버의 이름 (테이블 M-항목 7-가상 컴퓨터 이름 열)를 입력 하 고 **추가**클릭 한 다음 **다음**을 클릭 한 다음 키를 누릅니다.
    
23. **도메인 관리자 자격 증명** 페이지에서 사용자 이름 및 도메인 관리자 계정의 암호를 입력 하 고 ****을 클릭 합니다.
    
24. **AD FS 서비스 계정** 페이지에서 사용자 이름 및 엔터프라이즈 관리자 계정의 암호를 입력 하 고 ****을 클릭 합니다.
    
25. **도메인** **Azure AD 도메인** 페이지에서 조직의 DNS 도메인 이름을 선택 하 고 ****을 클릭 합니다.
    
26. **구성 준비 완료** 페이지에서 **설치**를 클릭 합니다.
    
27. **설치 완료** 페이지에서 **확인**을 클릭 합니다. 인트라넷 및 인터넷 모두 있는지 여부를 나타내는 두 메시지를 참조 해야 구성을 성공적으로 확인 되었습니다.
    
  - 인트라넷 메시지 AD FS 서버에 대 한 Azure 내부 부하 분산 장치의 개인 IP 주소를 나열 해야 합니다.
    
  - 인터넷 메시지 웹 응용 프로그램 프록시 서버에 대 한 Azure 인터넷 연결 부하 분산 장치의 공용 IP 주소를 나열 해야 합니다.
    
28. **설치 완료** 페이지에서 **끝내기**를 클릭 합니다.
    
여기에서는 서버에 대 한 자리 표시자 이름 사용 하 여 최종 구성 합니다.
  
**단계 5: 높은 가용성의 최종 구성을 페더레이션 Azure에서 인증 인프라**

![Azure에서 고가용성 Office 365 페더레이션 인증 인프라의 최종 구성.](images/c5da470a-f2aa-489a-a050-df09b4d641df.png)
  
Azure의 Office 365에 대 한 고가용성 연결 된 인증 인프라가 완료 됩니다.
  
## <a name="see-also"></a>See Also

[Azure의 Office 365에 대 한 고가용성 연결 된 인증 배포](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[Office 365 개발/테스트 환경에 대 한 페더레이션된 id](federated-identity-for-your-office-365-dev-test-environment.md)
  
[클라우드 채택 및 하이브리드 솔루션](cloud-adoption-and-hybrid-solutions.md)

[Office 365용 페더레이션 ID](https://support.office.com/article/Understanding-Office-365-identity-and-Azure-Active-Directory-06a189e7-5ec6-4af2-94bf-a22ea225a7a9#bk_federated)


