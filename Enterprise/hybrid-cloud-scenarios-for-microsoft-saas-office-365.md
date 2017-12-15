---
title: "Microsoft SaaS (Office 365)에 대 한 하이브리드 클라우드 시나리오"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Visuals
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: db117e59-389f-46f5-a5df-4eeac0040aa8
description: "요약: Microsoft의 SaaS 기반에 대 한 하이브리드 아키텍처 및 시나리오 이해 클라우드 제품 (Office 365)."
ms.openlocfilehash: 5f50573376b70ad94b3b1cd4b86ce3ef1fdc67dd
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2017
---
# <a name="hybrid-cloud-scenarios-for-microsoft-saas-office-365"></a>Microsoft SaaS (Office 365)에 대 한 하이브리드 클라우드 시나리오

 **요약:** Microsoft의 SaaS 기반에 대 한 하이브리드 아키텍처 및 시나리오 이해 클라우드 제품 (Office 365).
  
자신의 대응 하는 클라우드 마이그레이션 또는 장기 통합 전략의 일부분으로 Office 365를 사용한 Exchange, SharePoint, 또는 비즈니스를 위한 Skype의 온-프레미스 배포를 결합 합니다.
  
## <a name="microsoft-saas-hybrid-scenario-architecture"></a>Microsoft SaaS 하이브리드 시나리오 아키텍처

그림 1 Office 365에 대 한 Microsoft SaaS 기반 하이브리드 시나리오의 아키텍처를 보여줍니다.
  
**Office 365에 대 한 그림 1: Microsoft SaaS 기반 하이브리드 시나리오**

![Office 365용 Microsoft SaaS 기반 하이브리드 시나리오](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS.png)
  
아키텍처의 각 레이어에:
  
- 앱 및 시나리오
    
    SaaS 기반 하이브리드 시나리오를 중심으로 Office 서버 제품 및 Office 365 대응 하는 해당 맞춤의 다양 한 가지가 있습니다.
    
  - Exchange Online (Exchange Server 하이브리드)와 결합 하는 Exchange Server
    
  - Skype 비즈니스 서버에 대 한 비즈니스 온라인 및 새로운 클라우드 PBX와 클라우드 커넥터 Edition 시나리오에 대 한 Skype와 결합합니다.
    
  - SharePoint Server 2016 또는 SharePoint Server 2013 결합 된 SharePoint Online (여러 시나리오)
    
    방법이 Skype와 Exchange Online Business Server 온-프레미스, 제품 간 하이브리드 시나리오에 대 한입니다.
    
- Identity
    
    온-프레미스 Windows Server AD와 디렉터리 동기화를 포함할 수 있습니다. 또는 타사 id 공급자와 페더레이션 할 Azure AD를 구성할 수 있습니다.
    
- 네트워크
    
    Microsoft Office 365 또는 Dynamics 365 대 한 피어 링와 기존 인터넷 파이프 대화 또는 ExpressRoute에 대 한 연결 구성 됩니다.
    
- 온-프레미스
    
    Exchange, SharePoint 및 최신 버전으로 업데이트 되어야 하는 비즈니스를 위한 Skype에 대 한 기존 서버의 구성할 수 있습니다. 다음 하이브리드 시나리오를 위한 Office 365 대응 하는 자신의으로 조합할 수 있습니다.
    
사용자가 자신의 [Office 365 개발/테스트 환경](office-365-dev-test-environment.md)설정 합니다.
  
## <a name="skype-for-business-2015-hybrid"></a>비즈니스 2015 하이브리드 용 Skype

비즈니스 2015 하이브리드에 대 한 Skype를 사용 하면 비즈니스 Online 용 Skype 포함 하는 기존 온-프레미스 배포를 결합 하 여 있습니다. 일부 사용자는 홈된 온-프레미스 및 일부 사용자가 온라인 상태에 있는 하지만 사용자가 동일한 프로토콜 SIP (Session Initiation) 도메인 contoso.com 등을 공유 합니다. 이 하이브리드 구성을 마이그레이션하려면 온-프레미스에서 Office 365 시간이 지남에 따라 일정에 사용할 수 있습니다. 비즈니스 2015 용 Skype Exchange Online과 통합 수도 있습니다.
  
**그림 2: 비즈니스 2015 하이브리드 구성에 대 한 Skype**

![비즈니스용 Skype 2015 하이브리드 구성](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS_SfB.png)
  
그림 2는 온-프레미스 Skype 비즈니스 2015 프런트엔드 풀과 Office 365의 온라인 비즈니스에 대 한 Skype와에 지 서버 통신에 대해 구성 된 비즈니스 2015 하이브리드 구성에 대 한 Skype를 보여줍니다.
  
자세한 내용은 다음을 참조하십시오.
  
- [비즈니스 서버에 대 한 Skype와 비즈니스 온라인 용 Skype 간의 하이브리드 연결 계획](https://technet.microsoft.com/library/jj205403.aspx)
    
- [비즈니스 서버 2015 용 Skype에 대 한 지원 되는 하이브리드 구성](https://technet.microsoft.com/library/jj945633.aspx)
    
- [비즈니스 하이브리드 용 Skype](http://hybrid.office.com/skype-for-business/)
    
## <a name="cloud-pbx-with-skype-for-business-server"></a>비즈니스용 Skype 서버가 포함된 클라우드 PBX

클라우드 비즈니스 서버에 대 한 Skype와 PBX를 사용 하는 기존 Skype 토폴로지로 Business Server 온-프레미스 배포를 위한 온-프레미스 공용 전화 네트워크 (PSTN) 연결이 설정 된 전환 수 있습니다. 
  
**그림 3: 클라우드 비즈니스 서버에 대 한 Skype와 PBX**

![비즈니스용 Skype 서버가 포함된 클라우드 PBX](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS_SfB_CloudPBX.png)
  
그림 3 비즈니스 서버 구성의 경우 온-프레미스 비즈니스를 위한 Skype를 포함 하는 Office 365의 Microsoft 클라우드 PBX에 연결 하는 기존 PBX 또는 Telco 게이트웨이, 비즈니스 서버에 대 한 Skype와 PSTN으로 이루어진 Skype와 클라우드 PBX를 보여줍니다. 온라인.
  
조직에 있는 사용자의 클라우드에서 신호 및 음성 메일을 포함 하는 Microsoft 클라우드에서 private branch exchange (PBX) 서비스를 받을 수는 있지만 PSTN 연결 (발신음)에서 온-프레미스에서 Enterprise Voice를 통해 제공 됩니다. Business Server 배포에 대 한 Skype 합니다.
  
클라우드 기반 서비스를 점진적으로 마이그레이션할 수 있도록 하는 하이브리드 구성의 예입니다. 비즈니스 Online 용 Skype를 이동 하기 시작 하면 사용자의 음성 기능을 유지할 수 있습니다. 속도 자신의 음성 기능 no 계속 될 거 알고 있으면 직접 문제에는 홈 지정 사용자에 게 이동할 수 있습니다. 
  
자세한 내용은 [비즈니스 서버 및 비즈니스 Online 또는 Lync Server 2013에 대 한 Skype Skype 간의 하이브리드 연결 계획](https://technet.microsoft.com/library/jj205403.aspx)을 참조 하십시오.
  
수행 하지 이미 있는 경우 기존 Lync 서버나 Skype Business Server 배포에 대 한, Skype 비즈니스 클라우드 커넥터 edition의 경우 가공된 Vm (가상 컴퓨터) 클라우드 PBX와의 온-프레미스 PSTN 연결을 구현 하는 집합을 사용할 수 있습니다.
  
자세한 내용은 [Skype 비즈니스 클라우드 커넥터 edition에 대 한 계획](https://technet.microsoft.com/library/mt605227.aspx)을 참조 하십시오.
  
## <a name="sharepoint-hybrid"></a>SharePoint 하이브리드

두 세계, 연결 된 경험의 가장에 대 한 온-프레미스 SharePoint 팜과 SharePoint 하이브리드 Office 365의 SharePoint Online으로 결합합니다.
  
**그림 4: SharePoint 하이브리드 구성**

![SharePoint 하이브리드 구성](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS_SP.png)
  
그림 4에는 Office 365의 SharePoint Online과 통신 하는 온-프레미스 SharePoint 팜 구성 된 SharePoint 하이브리드 구성으로를 보여줍니다.
  
SharePoint 하이브리드 시나리오의 경우:
  
- [비즈니스를 위한 하이브리드 OneDrive](https://technet.microsoft.com/library/mt147425%28v=office.16%29.aspx)
    
- [하이브리드 팀 사이트](https://technet.microsoft.com/library/mt346110%28v=office.16%29.aspx)
    
- [하이브리드 익스트라넷 B2B](https://support.office.com/article/SharePoint-Business-to-Business-Collaboration-Extranet-for-Partners-with-Office-365-7b087413-165a-4e94-8871-4393e0b9c037)
    
- [하이브리드 검색](https://technet.microsoft.com/library/dn720906%28v=office.16%29.aspx)
    
- [하이브리드 프로필](https://support.office.com/article/Plan-hybrid-profiles-96d1eaf0-94eb-40c5-ab76-c82907777db4)
    
- [하이브리드 선택](https://support.office.com/article/Hybrid-picker-in-the-SharePoint-Online-admin-center-efce8417-c9bc-4a2c-ac9d-cce6c4e84a9c)
    
    Office 365의 SharePoint Online 관리 센터에서 사용할 수 있는 하이브리드 구성을 자동화 하는 마법사를 사용 하 여 하이브리드 시나리오를 사용 하는 것이 쉽습니다.
    
- [확장 가능한 하이브리드 응용 프로그램 시작 관리자](https://support.office.com/article/The-extensible-hybrid-app-launcher-617a7cb5-53da-4128-961a-64a840c0ab91)
    
    보고 하 여 Office 365 비디오 및 Delve 앱을 사용 하 여 사용자가 허용 하 고 자신의 온-프레미스 SharePoint 팜의 페이지 내에서 발생 합니다.
    
확장할 수 있는 하이브리드 응용 프로그램 시작 관리자를 제외 하 고 이러한 SharePoint 하이브리드 시나리오 모두 SharePoint 2016 및 SharePoint 2013 사용자 모두에 대해 사용할 수 있습니다.
  
자세한 내용은 [SharePoint 하이브리드](http://hybrid.office.com/sharepoint/)를 참조 하십시오.
  
## <a name="exchange-server-2016-hybrid"></a>Exchange Server 2016 하이브리드

Exchange Server 2016 하이브리드 사용 하면 기존 Exchange 서버 인프라를 사용 하 여 온-프레미스 사용자가 계속 되는 동안 온라인 사용자를 위한 Office 365의 Exchange Online의 이점을 인식할 수 있습니다. 
  
**그림 5: Exchange 2016 하이브리드 구성**

![Exchange 2016 하이브리드 구성](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS_EX.png)
  
그림 5는 Exchange Online Protection 및 Office 365에서 사서함와 통신 하는 온-프레미스 Exchange 사서함 서버 구성 된 Exchange 2016 하이브리드 구성 합니다.
  
일부 사용자는 온-프레미스 전자 메일 서버 및 일부 사용자를 사용 하 여 Exchange Online 되었지만 동일한 전자 메일 주소 공간을 공유 하는 모든 사용자에 게 합니다. 
  
이 하이브리드 구성:
  
- 마이그레이션할 Exchange Online으로 시간이 지남에 따라 일정에 하는 동안 사용 하도록 기존 Exchange 서버 인프라를 활용 합니다.
    
- Branch office 인프라에 투자 하지 않고도 원격 사이트를 지원할 수 있습니다.
    
- Office 365의 Exchange Online Protection을 통해 들어오는 인터넷 전자 메일을 라우팅할 수 있습니다.
    
- 온-프레미스 상주 하는 데이터를 필요로 하는 자회사와 다국적 조직의 요구를 처리 합니다.
    
이 하이브리드 구성 Skype를 포함 하 여 비즈니스 온라인 및 SharePoint Online에 대 한 다른 Microsoft Office 365 응용 프로그램과 통합할 수 있습니다.
  
자세한 내용은 [Exchange Server 하이브리드 배포](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx) 및 [Exchange 하이브리드](http://hybrid.office.com/exchange/)를 참조 하십시오.
  
## <a name="see-also"></a>See Also

[엔터프라이즈 설계자 용 Microsoft 하이브리드 클라우드](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Microsoft 클라우드 IT 아키텍처 리소스](microsoft-cloud-it-architecture-resources.md)

[Microsoft의 엔터프라이즈 클라우드 로드맵: IT 의사 결정권자를 위한 리소스](https://sway.com/FJ2xsyWtkJc2taRD)



