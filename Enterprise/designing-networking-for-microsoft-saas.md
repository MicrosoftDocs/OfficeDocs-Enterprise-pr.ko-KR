---
title: "Microsoft SaaS에 대 한 네트워킹 디자인 (영문)"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 4194020a-3847-4259-9f2d-5c556a4510f9
description: "요약: Office 365, Microsoft Intune 및 Dynamics 365 포함 한 Microsoft의 SaaS 서비스에 대 한 액세스에 대 한 네트워크를 최적화 하는 방법을 이해 합니다."
ms.openlocfilehash: 970d27e50e06f4d872de67589295c490aaa6e0e7
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/11/2018
---
# <a name="designing-networking-for-microsoft-saas"></a>Microsoft SaaS에 대 한 네트워킹 디자인 (영문)

 **요약:** Office 365, Microsoft Intune 및 Dynamics 365 포함 한 Microsoft의 SaaS 서비스에 대 한 액세스에 대 한 네트워크를 최적화 하는 방법을 이해 합니다.
  
Microsoft SaaS 서비스에 대한 네트워크를 최적화하려면 인터넷 에지, 클라이언트 장치 및 일반적인 IT 운영을 신중하게 분석해야 합니다.
  
## <a name="steps-to-prepare-your-network-for-microsoft-saas-services"></a>Microsoft SaaS 서비스에 대 한 네트워크를 준비 하는 단계

Microsoft SaaS 서비스에 대 한 네트워크를 최적화 하기 위해 다음이 단계를 수행 합니다.
  
1. [Microsoft 클라우드 연결의 공통 요소](common-elements-of-microsoft-cloud-connectivity.md)에 **Microsoft 클라우드 서비스에 대 한 네트워크를 준비 하는 단계** 섹션을 통해 이동 합니다.
    
2. 프록시 서버 권장 사항에 따라 Microsoft SaaS 서비스에 대 한 인터넷 탈출 대화를 최적화 합니다.
    
3. 근접 및 위치 권장 사항을 사용 하 여 인터넷 처리량을 최적화 합니다.
    
4. 클라이언트 컴퓨터와 기반이 있든 클라이언트 사용 고려 사항을 사용 하 여 인트라넷의 성능을 최적화 합니다.
    
5. 필요에 따라 데이터 마이그레이션 및 IT 운영 고려 사항을 사용 하 여 동기화의 성능을 최적화 합니다.
    
## <a name="internet-edge-considerations"></a>인터넷에 지 고려 사항

인터넷에 지 및 Microsoft SaaS 서비스에 대 한 처리량을 최적화 하는 몇가지 사항을 고려해 야 다음과 같습니다.
  
**Microsoft SaaS 서비스에 대 한 그림 1: 연결 옵션**

![그림 1: Microsoft SaaS 서비스를 위한 연결 옵션](images/Network_Poster/SaaS1.png)
  
그림 1 인터넷 파이프 또는 ExpressRoute을 통해 Microsoft SaaS 서비스에 연결 하는 온-프레미스 네트워크를 보여줍니다.
  
프록시 서버를 최적화 하기 위해 일부 권장 사항은 다음과 같습니다.
  
- WPAD, PAC, 또는 GPO를 사용 하 여 웹 클라이언트를 구성 합니다.
    
- SSL 가로채기를 사용 하지 않는
    
- PAC 파일을 사용 하 여 Microsoft SaaS 서비스 DNS 이름에 대 한 프록시를 무시 합니다.
    
- CRL/OCSP 확인에 대 한 트래픽을 허용합니다
    
일부 프록시 서버 병목 현상을 확인 하는 다음과 같습니다.
  
- 부족 하 여 영구 연결 (Outlook)
    
- 용량이 부족
    
- 이렇게 하면 오프 네트워크 평가
    
- 인증 필요
    
- UDP 트래픽 (비즈니스용 Skype)에 대 한 지원 되지 않습니다
    
일부 근접 및 위치 권장 사항은 다음과 같습니다.
  
- 개인 WAN을 통해 인터넷 트래픽을 라우팅 하지 마십시오
    
- Out (영문)-region의 사용자에 대 한 영역에서 DNS 및 인터넷 트래픽 흐름을 사용 합니다.
    
- Office 365와 Azure 서비스와의 연결을 동시에 대 한 높은 대역폭에 대 한 ExpressRoute를 사용 하 여
    
Office 365 트래픽에 대 한 필요한 아웃 바운드 포트는 다음과 같습니다.
  
- TCP 80 (검사를 위해 CRL/OCSP)
    
- TCP 443
    
- UDP 3478
    
- TCP 5223
    
- TCP 50000-59999
    
- UDP 50000-59999
    
## <a name="client-usage-considerations"></a>클라이언트 사용 고려 사항

먼저, 클라이언트를 사용과 같은 서비스 집합을 구성 합니다.
  
- Azure Active Directory
    
- Office 365
    
  - Office 클라이언트 응용 프로그램
    
  - SharePoint Online
    
  - Exchange Online
    
  - 비즈니스용 Skype
    
- Microsoft Intune
    
- Dynamics 365
    
클라이언트 컴퓨터에 대해 다음 사항을 확인 해야 합니다.
  
- 일별, 계절적, 최대 부하 및 사용 현황 캡처에서 표준시로 한번에 최대 수
    
- 최대 부하에 필요한 총 대역폭
    
- 인터넷 송신 장치에 대 한 대기 시간
    
- 데이터 센터 배치의 국가 및 비교 원점의 국가
    
각 유형의 클라이언트 (PC, smartphone, 태블릿)에 대 한 현재를 확인 합니다.
  
- 운영 체제
    
- 인터넷 브라우저
    
- TCP/IP 스택
    
- 네트워크 하드웨어
    
- 네트워크 하드웨어에 대 한 운영 체제 드라이버
    
- 업데이트 및 패치 설치
    
또한 인트라넷 연결 처리량을 최적화 (유선, 무선 또는 VPN).
  
자세한 내용은 [Office 365와의 NAT 지원](https://support.office.com/article/NAT-support-with-Office-365-170e96ea-d65d-4e51-acac-1de56abe39b9)을 참조 하십시오.
  
Office 365와 함께 ExpressRoute를 사용 하는 것에 대 한 최신 권장 사항에 대 한 [Office 365에 대 한 ExpressRoute](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd)를 참조 합니다.
  
인트라넷 성능을 최적화 하기 위해 다음을 수행 합니다.
  
- 인터넷에 지 장치 (PsPing, Ping, Tracert, TraceTCP, 네트워크 모니터)에 (RTTs) 왕복 시간 측정 하는 도구 사용
    
- 흐름 프로토콜을 사용 하 여 탈출 경로 분석을 수행 합니다.
    
- 중간 장치 (예: 시간, 상태) 분석을 수행
    
자세한 내용은 [PsPing 도구](https://technet.microsoft.com/sysinternals/jj729731.aspx)를 참조 하십시오.
  
## <a name="it-operations-considerations"></a>IT 운영 고려 사항

다음은 Microsoft SaaS 서비스에는 IT 작업 부하를 운영 하는 경우 고려 해야할 사항입니다.
  
### <a name="one-time-migrations"></a>1 회 마이그레이션

1 회 마이그레이션 예는 클라우드 기반 응용 프로그램 또는 보관 저장소에 대 한 대량 데이터를 전송 합니다.
  
시간에 마이그레이션에 대 한 네트워크를 최적화 합니다.
  
- 최대 네트워크 사용량 및 시간에 패치를 적용 하는 컴퓨터를 방지 합니다.
    
- 기준 지정 하 고 파일럿, 네트워크 상태를 평가 하 고 실제 마이그레이션 시도 하기 전에 문제를 해결 해야
    
- 향후 마이그레이션에 대 한 사후 평가 수행 합니다.
    
### <a name="ongoing-synchronizations"></a>진행 중인 동기화

진행 중인 동기화의 예는 디렉터리 정보, 설정, 또는 파일입니다.
  
진행 중인 동기화에 대 한 네트워크를 최적화 합니다.
  
- 전체에서 시스템을 모니터링 하는 네트워크 대역폭 인지 확인, 해결 또는 수집 된 오류를 해제 합니다.
    
- 결과 모니터링 하는 대역폭을 사용 하 여 네트워크 변경 (수직/수평, 새 회로 또는 추가 장치)에 대 한 요구를 확인 하려면
    
자세한 내용은 다음을 참조하십시오.
  
- [네트워크 및 마이그레이션 Office 365에 대 한 계획](https://aka.ms/tune)
    
- [Office 365 성능 관리 Microsoft 가상 Academy 코스 (영문)](https://aka.ms/o365perf)
    
- [Office 365에 대 한 ExpressRoute](https://aka.ms/expressrouteoffice365)
    
## <a name="see-also"></a>참고 항목

[Microsoft Cloud Networking for Enterprise Architects](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Microsoft 클라우드 IT 아키텍처 리소스](microsoft-cloud-it-architecture-resources.md)

[Microsoft의 엔터프라이즈 클라우드 로드맵: IT 의사 결정권자를 위한 리소스](https://sway.com/FJ2xsyWtkJc2taRD)



