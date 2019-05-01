---
title: 고가용성 페더레이션 인증 단계 5 Office 365에 대 한 페더레이션 인증 구성
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: 0f1dbf52-5bff-44cc-a264-1b48641af98f
description: '요약: Microsoft azure에서 Office 365에 대 한 고가용성 페더레이션 인증에 대해 Azure AD Connect를 구성 합니다.'
ms.openlocfilehash: e5a4381b6795a1159c1398f4155b059998a30818
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487940"
---
# <a name="high-availability-federated-authentication-phase-5-configure-federated-authentication-for-office-365"></a>고가용성 페더레이션 인증 5단계: Office 365에 대해 페더레이션 인증 구성

 **요약:** Microsoft azure에서 Office 365에 대 한 고가용성 페더레이션 인증에 대해 Azure AD Connect를 구성 합니다.
 
Azure 인프라 서비스에서 Office 365에 대 한 고가용성 페더레이션 인증을 배포 하는 마지막 단계에서는 공개 인증 기관에서 발급 한 인증서를 가져오고 설치 하 고, 구성을 확인 한 다음 Azure AD를 설치 및 실행 합니다. 디렉터리 동기화 서버에서 연결 합니다. Azure ad Connect는 페더레이션 인증을 위해 Office 365 구독 및 AD FS (Active Directory Federation Services) 및 웹 응용 프로그램 프록시 서버를 구성 합니다.
  
모든 단계에 대해 [Azure에서 Office 365에 대 한 고가용성 페더레이션 인증 배포](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) 를 참조 하세요.
  
## <a name="get-a-public-certificate-and-copy-it-to-the-directory-synchronization-server"></a>공용 인증서를 가져와 디렉터리 동기화 서버에 복사

다음 속성을 사용 하 여 공용 인증 기관에서 디지털 인증서를 가져올 수 있습니다.
  
- SSL 연결을 만드는 데 적합 한 x.509 인증서입니다.
    
- SAN (주체 대체 이름) 확장 속성은 페더레이션 서비스 FQDN으로 설정 됩니다 (예: fs.contoso.com).
    
- 인증서에는 개인 키가 있고 PFX 형식으로 저장 되어 있어야 합니다.
    
또한 조직 컴퓨터 및 장치는 디지털 인증서를 발급 하는 공용 인증 기관을 신뢰 해야 합니다. 이 트러스트는 컴퓨터 및 장치에 있는 신뢰할 수 있는 루트 인증 기관 저장소에 설치 된 공용 인증 기관의 루트 인증서를 보유 하 여 설정 됩니다. 일반적으로 Microsoft Windows를 실행 하는 컴퓨터에는 일반적으로 사용 되는 인증 기관에서 설치 된 이러한 유형의 인증서가 포함 됩니다. 공용 인증 기관의 루트 인증서가 아직 설치 되어 있지 않은 경우이를 조직의 컴퓨터 및 장치에 배포 해야 합니다.
  
페더레이션 인증의 인증서 요구 사항에 대 한 자세한 내용은 [페더레이션 설치 및 구성에 대 한 필수 구성 요소](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-prerequisites#prerequisites-for-federation-installation-and-configuration)를 참조 하십시오.
  
인증서를 받으면 디렉터리 동기화 서버의 C: 드라이브에 있는 폴더로 복사 합니다. 예를 들어, 파일 이름을 p C\\e. e l e.
  
## <a name="verify-your-configuration"></a>구성 확인

이제 Office 365에 대해 Azure AD Connect 및 페더레이션 인증을 구성할 준비가 되었습니다. 다음은 검사 목록을 확인 하는 예제입니다.
  
- 조직의 공용 도메인이 Office 365 구독에 추가 됩니다.
    
- 조직의 Office 365 사용자 계정이 조직의 공용 도메인 이름으로 구성 되 고 성공적으로 로그인 할 수 있습니다.
    
- 공용 도메인 이름을 기반으로 하는 페더레이션 서비스 FQDN을 결정 했습니다.
    
- 페더레이션 서비스 FQDN에 대 한 공용 DNS a 레코드는 웹 응용 프로그램 프록시 서버에 대 한 인터넷 연결에 사용 되는 Azure 부하 분산 장치의 공용 IP 주소를 가리킵니다.
    
- 페더레이션 서비스 FQDN에 대 한 개인 DNS a 레코드는 AD FS 서버에 대 한 내부 Azure 부하 분산 장치의 개인 IP 주소를 가리킵니다.
    
- 페더레이션 서비스 FQDN으로 설정 된 SAN과의 SSL 연결에 적합 한 공용 인증 기관-isssued 디지털 인증서는 디렉터리 동기화 서버에 저장 되는 PFX 파일입니다.
    
- 공용 인증 기관의 루트 인증서는 컴퓨터 및 장치에 있는 신뢰할 수 있는 루트 인증 기관 저장소에 설치 됩니다.
    
다음은 Contoso 조직에 대 한 예입니다.
  
**Azure의 고가용성 페더레이션 인증 인프라에 대 한 예제 구성**

![Azure에서 고가용성 Office 365 페더레이션 인증 인프라의 예제 구성](media/ac1a6a0d-0156-4407-9336-6e4cd6db8633.png)
  
## <a name="run-azure-ad-connect-to-configure-federated-authentication"></a>Azure AD Connect를 실행 하 여 페더레이션 인증 구성

Azure ad Connect 도구는 다음 단계를 사용 하 여 페더레이션 인증을 위해 AD FS 서버, 웹 응용 프로그램 프록시 서버 및 Office 365을 구성 합니다.
  
1. 로컬 관리자 권한이 있는 도메인 계정을 사용 하 여 디렉터리 동기화 서버에 대 한 원격 데스크톱 연결을 만듭니다.
    
2. 디렉터리 동기화 서버의 데스크톱에서 Internet Explorer를 열고로 [https://aka.ms/aadconnect](https://aka.ms/aadconnect)이동 합니다.
    
3. **Microsoft Azure Active Directory 연결** 페이지에서 **다운로드**를 클릭 한 다음 **실행**을 클릭 합니다.
    
4. **Azure AD Connect 시작** 페이지에서 **동의 함**을 클릭 하 고 계속을 클릭 **합니다.**
    
5. **기본 설정** 페이지에서 **사용자 지정**을 클릭합니다.
    
6. **필수 구성 요소 설치** 페이지에서 **설치**를 클릭합니다.
    
7. **사용자 로그인** 페이지에서 **AD FS로 페더레이션**을 클릭하고 **다음**을 클릭합니다.
    
8. **Azure AD에 연결** 페이지에서 Office 365 구독에 대 한 전역 관리자 계정의 이름과 암호를 입력 하 고 **다음**을 클릭 합니다.
    
9. **디렉터리 연결** 페이지에서 온-프레미스 AD DS (Active Directory 도메인 서비스) 포리스트가 **포리스트에서**선택 되어 있는지 확인 하 고 도메인 관리자 계정의 이름과 암호를 입력 한 다음 **디렉터리 추가**를 클릭 하 고 **다음**을 클릭 합니다.
    
10. **Azure AD 로그인 구성** 페이지에서 **다음**을 클릭 합니다.
    
11. **도메인 및 OU 필터링** 페이지에서 **다음**을 클릭 합니다.
    
12. 사용자를 **고유 하 게 식별** 페이지에서 **다음**을 클릭 합니다.
    
13. **사용자 및 장치 필터링** 페이지에서 **다음**을 클릭 합니다.
    
14. **선택적 기능** 페이지에서 **다음**을 클릭 합니다.
    
15. **ad fs 팜** 페이지에서 **새 AD FS 팜 구성을**클릭 합니다.
    
16. **찾아보기를** 클릭 하 고 공용 인증 기관에서 SSL 인증서의 위치와 이름을 지정 합니다.
    
17. 메시지가 나타나면 인증서 암호를 입력 하 고 **확인**을 클릭 합니다.
    
18. **주체 이름** 및 **페더레이션 서비스 이름이** 페더레이션 서비스 FQDN으로 설정 되어 있는지 확인 하 고 **다음**을 클릭 합니다.
    
19. **ad fs 서버** 페이지에서 첫 번째 AD fs 서버의 이름 (테이블 M-항목 4-가상 컴퓨터 이름 열)을 입력 하 고 **추가**를 클릭 합니다.
    
20. 두 번째 AD FS 서버 이름 (테이블 M-항목 5-가상 컴퓨터 이름 열)을 입력 하 고 **추가**를 클릭 한 후 **다음**을 클릭 합니다.
    
21. **웹 응용 프로그램 프록시 서버** 페이지에서 첫 번째 웹 응용 프로그램 프록시 서버의 이름 (테이블 M-항목 6-가상 컴퓨터 이름 열)을 입력 한 다음 **추가**를 클릭 합니다.
    
22. 두 번째 웹 응용 프로그램 프록시 서버의 이름 (테이블 M-항목 7-가상 컴퓨터 이름 열)을 입력 하 고 **추가**를 클릭 한 후 **다음**을 클릭 합니다.
    
23. **도메인 관리자 자격 증명** 페이지에서 도메인 관리자 계정의 사용자 이름과 암호를 입력 한 후 **다음**을 클릭 합니다.
    
24. **AD FS 서비스 계정** 페이지에서 엔터프라이즈 관리자 계정의 사용자 이름과 암호를 입력 한 후 **다음**을 클릭 합니다.
    
25. **Azure AD 도메인** 페이지의 **도메인**에서 조직의 DNS 도메인 이름을 선택 하 고 **다음**을 클릭 합니다.
    
26. **구성 준비 완료** 페이지에서 **설치**를 클릭합니다.
    
27. **설치 완료** 페이지에서 **확인**을 클릭합니다. 인트라넷 구성과 인터넷 구성이 모두 성공적으로 확인 되었음을 나타내는 두 개의 메시지가 표시 되어야 합니다.
    
  - 인트라넷 메시지는 AD FS 서버에 대 한 Azure 내부 부하 분산 장치의 개인 IP 주소를 나열 해야 합니다.
    
  - 인터넷 메시지에는 웹 응용 프로그램 프록시 서버에 대 한 Azure 인터넷 연결 부하 분산 장치의 공용 IP 주소가 나열 되어야 합니다.
    
28. **설치 완료** 페이지에서 **끝내기**를 클릭합니다.
    
다음은 서버에 대 한 자리 표시자 이름이 포함 된 최종 구성입니다.
  
**5 단계: Azure의 고가용성 페더레이션 인증 인프라에 대 한 최종 구성**

![Azure에서 고가용성 Office 365 페더레이션 인증 인프라의 최종 구성.](media/c5da470a-f2aa-489a-a050-df09b4d641df.png)
  
Azure의 Office 365에 대 한 고가용성 페더레이션 인증 인프라가 완료 되었습니다.
  
## <a name="see-also"></a>참고 항목

[Azure에서 Office 365용 고가용성 페더레이션 인증 배포](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[Office 365 개발/테스트 환경에 대 한 페더레이션된 id](federated-identity-for-your-office-365-dev-test-environment.md)
  
[클라우드 채택 및 하이브리드 솔루션](cloud-adoption-and-hybrid-solutions.md)

[Office 365용 페더레이션 ID](https://support.office.com/article/Understanding-Office-365-identity-and-Azure-Active-Directory-06a189e7-5ec6-4af2-94bf-a22ea225a7a9#bk_federated)


