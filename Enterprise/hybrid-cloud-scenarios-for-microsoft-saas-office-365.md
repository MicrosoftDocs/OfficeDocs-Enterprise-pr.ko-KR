---
title: Microsoft SaaS(Office 365)용 하이브리드 클라우드 시나리오
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: db117e59-389f-46f5-a5df-4eeac0040aa8
description: '요약: Microsoft의 SaaS 기반 클라우드 서비스에 대 한 하이브리드 아키텍처 및 시나리오를 이해 합니다 (Office 365).'
ms.openlocfilehash: 90b751e4bbea42d723961eb2ac339d23faf8c259
ms.sourcegitcommit: 682b180061dc63cd602bee567d5414eae6942572
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/09/2019
ms.locfileid: "31741394"
---
# <a name="hybrid-cloud-scenarios-for-microsoft-saas-office-365"></a>Microsoft SaaS(Office 365)용 하이브리드 클라우드 시나리오

 **요약:** Microsoft의 SaaS 기반 클라우드 서비스 (Office 365)에 대 한 하이브리드 아키텍처 및 시나리오를 이해 합니다.
  
클라우드 마이그레이션 또는 장기적인 통합 전략의 일환으로, Exchange, SharePoint 또는 비즈니스용 Skype를 Office 365의 해당 항목을 사용 하 여 온-프레미스 배포를 결합 합니다.
  
## <a name="microsoft-saas-hybrid-scenario-architecture"></a>Microsoft SaaS 하이브리드 시나리오 아키텍처

그림 1에서는 Office 365 용 Microsoft SaaS 기반 하이브리드 시나리오의 아키텍처를 보여 줍니다.
  
**그림 1: Office 365 용 Microsoft SaaS 기반 하이브리드 시나리오**

![Office 365 용 Microsoft SaaS 기반 하이브리드 시나리오](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS.png)
  
아키텍처의 각 계층에 대해 다음을 수행 합니다.
  
- 앱 및 시나리오
    
    office Server 제품에 맞추고 office 365 대응 하는 다양 한 SaaS 기반 하이브리드 시나리오를 사용할 수 있습니다.
    
  - exchange Online과 통합 된 exchange server (exchange server hybrid)
    
  - 비즈니스용 skype 서버와 skype 온라인 및 새로운 클라우드 PBX 및 클라우드 커넥터 버전 시나리오를 결합
    
  - sharepoint server 2019, sharepoint server 2016 또는 sharepoint server 2013가 sharepoint Online과 결합 됨 (여러 시나리오)
    
    제품 간 하이브리드 시나리오인 비즈니스용 Skype 서버 온-프레미스를 사용 하는 Exchange Online도 있습니다.
    
- ID
    
    온-프레미스 AD DS (Active directory 도메인 서비스)와 디렉터리 동기화를 포함할 수 있습니다. 또는 타사 id 공급자와 페더레이션 하도록 Azure AD를 구성할 수 있습니다.
    
- 네트워크
    
    기존 인터넷 파이프 또는 Office 365 또는 Dynamics 365에 대 한 Microsoft 피어 링과의 express 방식 연결로 구성 됩니다.
    
- 온-프레미스
    
    Exchange, SharePoint 및 비즈니스용 Skype에 대 한 기존 서버로 구성 하 여 최신 버전으로 업데이트 해야 할 수 있습니다. 그런 다음 하이브리드 시나리오를 위해 이러한 항목을 Office 365과 결합할 수 있습니다.
    
자체 office 365 개발/테스트 환경을 설정 하려면 [office 365 테스트 랩 가이드](cloud-adoption-test-lab-guides-tlgs.md)를 참조 하세요.
  
## <a name="skype-for-business-hybrid"></a>비즈니스용 Skype 하이브리드

비즈니스용 skype 하이브리드를 사용 하 여 기존 온-프레미스 배포를 비즈니스용 skype Online과 결합할 수 있습니다. 일부 사용자는 온-프레미스에 있고 일부 사용자는 온라인으로 설정 되지만, 사용자는 contoso.com과 같은 동일한 SIP (세션 시작 프로토콜) 도메인을 공유 합니다. 일정에 따라이 하이브리드 구성을 사용 하 여 시간에 따라 온-프레미스에서 Office 365로 마이그레이션할 수 있습니다. 비즈니스용 Skype도 [Exchange Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/integration-with-exchange-and-sharepoint)과 통합할 수 있습니다.
  
**그림 2: 비즈니스용 Skype 하이브리드 구성**

![비즈니스용 Skype 하이브리드 구성](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SfB.png)
  
그림 2는 Office 365에서 비즈니스용 skype Online과 통신 하는 온-프레미스 비즈니스용 skype 프런트 엔드 풀 및에 지 서버로 구성 된 비즈니스용 skype 하이브리드 구성을 보여 줍니다.
  
자세한 내용은 비즈니스용 [skype 서버 및 비즈니스용 skype Online 간의 하이브리드 연결 계획](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity)을 참조 하세요.
    
## <a name="cloud-pbx-with-skype-for-business-server"></a>비즈니스용 Skype 서버가 포함 된 클라우드 PBX

비즈니스용 skype 서버가 포함 된 클라우드 PBX를 사용 하 여 기존 비즈니스용 skype 서버 온-프레미스 배포를 온-프레미스 PSTN (공중 전화망) 연결을 사용 하는 토폴로지로 전환할 수 있습니다. 
  
**그림 3: 비즈니스용 Skype 서버가 포함 된 클라우드 PBX**

![비즈니스용 Skype 서버가 포함 된 클라우드 PBX](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SfB-CloudPBX.png)
  
그림 3에서는 비즈니스용 skype를 포함 하 여 Office 365에서 Microsoft 클라우드 PBX에 연결 된 온-프레미스 pbx 또는 Telco 게이트웨이, 비즈니스용 skype 서버로 구성 되는 비즈니스용 skype 서버 구성이 포함 된 클라우드 pbx를 보여 줍니다. 온라인.
  
클라우드에 있는 조직의 사용자는 신호 및 음성 메일을 포함 하는 Microsoft 클라우드에서 PBX (private branch exchange) 서비스를 받을 수 있지만 온-프레미스에서 Enterprise Voice를 통해 PSTN 연결 (발신음)이 제공 됩니다. 비즈니스용 Skype 서버 배포
  
이 예제는 클라우드 기반 서비스로 점진적으로 마이그레이션할 수 있도록 하는 하이브리드 구성의 좋은 예입니다. 비즈니스용 Skype Online으로 이동 하기 시작할 때 사용자의 음성 기능을 유지할 수 있습니다. 사용자를 원하는 속도로 이동 하 여 자신의 음성 기능이 홈 위치에 관계 없이 계속 해 서 사용할 수 있습니다. 
  
자세한 내용은 비즈니스용 [skype 서버 및 비즈니스용 skype Online 간의 하이브리드 연결 계획](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity)을 참조 하세요.
  
기존 Lync server 또는 비즈니스용 skype 서버 배포가 아직 없는 경우 비즈니스용 skype 클라우드 커넥터 Edition, 클라우드 PBX로 온-프레미스 PSTN 연결을 구현 하는 패키지 vm (가상 컴퓨터) 집합을 사용할 수 있습니다.
  
자세한 내용은 [비즈니스용 Skype 클라우드 Connector Edition 계획](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-skype-for-business-cloud-connector-edition)을 참조 하십시오.

  
## <a name="sharepoint-hybrid"></a>SharePoint 하이브리드

sharepoint 하이브리드는 연결 된 세계 최고의 환경을 위해 Office 365의 sharepoint Online을 온-프레미스 sharepoint 팜과 결합 합니다.
  
**그림 4: SharePoint 하이브리드 구성**

![SharePoint 하이브리드 구성](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SP.png)
  
그림 4에서는 Office 365에서 sharepoint Online과 통신 하는 온-프레미스 sharepoint 팜으로 구성 된 sharepoint 하이브리드 구성을 보여 줍니다.
  
SharePoint 하이브리드 시나리오:
  
- [하이브리드 비즈니스용 OneDrive](https://docs.microsoft.com/SharePoint/hybrid/configure-hybrid-onedrive-for-businessroadmap)
    
- [하이브리드 엑스트라넷 B2B](https://docs.microsoft.com/sharepoint/create-b2b-extranet)
    
- [Hybrid search](https://docs.microsoft.com/SharePoint/hybrid/configure-cloud-hybrid-searchroadmap)
    
- [하이브리드 프로필](https://docs.microsoft.com/SharePoint/hybrid/plan-hybrid-profiles)
    
- [하이브리드 선택기](https://docs.microsoft.com/SharePoint/hybrid/hybrid-picker-in-the-sharepoint-online-admin-center)
    
    Office 365의 SharePoint Online 관리 센터에서 사용할 수 있는 하이브리드 구성을 자동화 하는 마법사를 사용 하 여 하이브리드 시나리오를 간편 하 게 활성화할 수 있습니다.
    
- [확장 가능한 하이브리드 앱 시작 관리자](https://docs.microsoft.com/SharePoint/hybrid/the-extensible-hybrid-app-launcher)
    
    사용자가 온-프레미스 SharePoint 팜의 페이지 내에서 Office 365 비디오 및 Delve 앱과 경험을 보고 사용할 수 있습니다.
    
확장 가능한 하이브리드 앱 시작 관리자를 제외한 이러한 모든 sharepoint 하이브리드 시나리오는 sharepoint 2016 및 sharepoint 2013 사용자 모두에 게 제공 됩니다.
  
## <a name="exchange-server-2016-hybrid"></a>Exchange Server 2016 하이브리드

exchange server 2016 Hybrid에서는 온-프레미스 사용자가 기존 exchange Server 인프라를 계속 사용 하는 동안 온라인 사용자를 위해 Office 365에서 exchange online의 이점을 실현할 수 있습니다. 
  
**그림 5: Exchange 2016 하이브리드 구성**

![Exchange 2016 하이브리드 구성](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-EX.png)
  
그림 5에서는 exchange Online Protection과 통신 하는 온-프레미스 Exchange 사서함 서버와 Office 365의 사서함으로 구성 되는 exchange 2016 하이브리드 구성을 보여 줍니다.
  
일부 사용자에 게는 온-프레미스 전자 메일 서버가 있으며 일부 사용자는 Exchange Online을 사용 하지만 모든 사용자는 같은 전자 메일 주소 공간을 공유 합니다. 
  
다음과 같은 하이브리드 구성을 수행 합니다.
  
- 일정에 따라 시간에 따라 exchange Online으로 마이그레이션하는 동안 기존 exchange Server 인프라를 활용 합니다.
    
- 지점 인프라에 대 한 투자 없이 원격 사이트를 지원할 수 있습니다.
    
- Office 365에서 Exchange Online Protection을 통해 들어오는 인터넷 전자 메일을 라우팅할 수 있습니다.
    
- 데이터를 온-프레미스에 배치 해야 하는 자회사와 다국적 조직의 요구 사항을 충족 합니다.
    
또한이 하이브리드 구성을 비즈니스용 Skype online 및 SharePoint Online을 포함 하 여 다른 Microsoft Office 365 응용 프로그램에 통합할 수 있습니다.
  
자세한 내용은 [Exchange Server 하이브리드 배포](https://docs.microsoft.com/exchange/exchange-hybrid)를 참조 하세요.
  
## <a name="see-also"></a>참고 항목

[Microsoft Hybrid Cloud for Enterprise Architects](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Microsoft 클라우드 IT 아키텍처 리소스](microsoft-cloud-it-architecture-resources.md)

