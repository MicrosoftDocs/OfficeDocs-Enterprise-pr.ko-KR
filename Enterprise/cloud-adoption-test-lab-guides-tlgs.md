---
title: 클라우드 채택 TLG(테스트 랩 가이드)
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Strat_O365_Enterprise
- Ent_TLGs
ms.assetid: 706d5449-45e5-4b0c-a012-ab60501899ad
description: '요약: 이러한 클라우드 채택 TLG(테스트 랩 가이드)를 사용하여 Office 365, EMS(Enterprise Mobility + Security), Dynamics 365, Office Server 제품의 데모, 개념 증명 또는 개발/테스트 환경을 설정합니다.'
ms.openlocfilehash: 3172b6033fbb7dd79b8eb786d92a4f58886a8fd5
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2018
---
# <a name="cloud-adoption-test-lab-guides-tlgs"></a>클라우드 채택 TLG(테스트 랩 가이드)

 **요약:** 이러한 클라우드 채택 TLG(테스트 랩 가이드)를 사용하여 Office 365, EMS(Enterprise Mobility + Security), Dynamics 365, Office Server 제품의 데모, 개념 증명 또는 개발/테스트 환경을 설정합니다.
  
TLG를 사용하면 Microsoft 제품을 빠르게 학습할 수 있습니다. 기술 또는 구성이 자신에게 적합한지 결정을 내리거나 기술 또는 구성을 사용자에게 선보이기 전에 먼저 평가해야 하는 경우에 유용합니다. "직접 구축 후 정상 작동 확인" 실습을 통해 새로운 제품 또는 솔루션의 배포 요구 사항을 이해할 수 있으므로 프로덕션에서 호스팅을 더욱 잘 계획할 수 있습니다.
  
또한, TLG는 응용 프로그램의 개발 및 테스트를 위한 대표적 환경(개발/테스트 환경이라고도 함)을 만들 수도 있습니다.
  
![Microsoft 클라우드의 테스트 랩 가이드](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
본격적으로 시작하기 전에 다음의 추가 리소스를 참조하세요.
  
- Microsoft Virtual Academy 세션 [클라우드 채택 테스트 랩 가이드로 Microsoft 클라우드 경험하기](https://mva.microsoft.com/en-US/training-courses/experience-the-microsoft-cloud-with-cloud-adoption-test-lab-guides-17960?l=LXNRdhSLE_1000115881 )를 보세요(22분밖에 소요되지 않습니다).
    
- [여기](http://aka.ms/catlgstack)를 클릭하여 One Microsoft 클라우드 테스트 랩 가이드 스택의 모든 문서에 대한 가상 맵을 확인할 수 있습니다.
    
## <a name="office-365-devtest-environment"></a>Office 365 개발/테스트 환경
<a name="O365"> </a>

이러한 문서를 사용하여 Office 365 개발/테스트 환경을 구축하세요.
  
- [기본 구성 개발/테스트 환경](base-configuration-dev-test-environment.md)
    
    Microsoft Azure 인프라 서비스에서 실행되는 단순화된 인트라넷을 생성합니다. 이 단계는 시뮬레이트된 엔터프라이즈 구성을 구축하려는 경우에 가능한 선택 사항입니다.
    
- [Office 365 개발/테스트 환경](office-365-dev-test-environment.md)
    
    Office 365 Enterprise E5 평가판 구독을 만듭니다. 이는 컴퓨터에서 또는 Azure 인프라 서비스에서 실행되는 단순화된 인트라넷에서 만들 수 있습니다.
    
- [Office 365 개발/테스트 환경용 DirSync](dirsync-for-your-office-365-dev-test-environment.md)
    
    암호 동기화를 사용하여 디렉터리를 동기화하는 Azure AD Connect를 설치하고 구성합니다. 이 단계는 시뮬레이트된 엔터프라이즈 구성을 구축하려는 경우에 가능한 선택 사항입니다.
    
Office 365 개발/테스트 환경의 경우 이러한 문서를 사용하여 Office 365의 엔터프라이즈 기능을 보여 줍니다.
  
- [Office 365 개발/테스트 환경용 다단계 인증](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
    Office 365 구독 계정을 위해 스마트폰에 전송된 구독 텍스트 메시지를 사용하여 보조 인증을 구성하고 테스트합니다.
    
- [Office 365 개발/테스트 환경용 페더레이션된 ID](federated-identity-for-your-office-365-dev-test-environment.md)
    
    Windows Server Active Directory 도메인의 계정을 사용하여 페더레이션된 인증을 구성하고 보여 줍니다.
    
- [Office 365 개발/테스트 환경용 Cloud App Security](cloud-app-security-for-your-office-365-dev-test-environment.md)
    
    Office 365 구독에서의 의심스러운 활동을 모니터링하고 알려주는 정책을 만들 수 있는 Office 365 Cloud App Security를 구성하고 보여 줍니다.
    
- [Office 365 개발/테스트 환경용 Advanced Threat Protection](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
    전자 메일에서 맬웨어를 차단하는 EOP(Exchange Online Protection)의 기능인 Advanced Threat Protection을 구성하고 보여 줍니다.
    
- [Office 365 개발/테스트 환경용 고급 eDiscovery](advanced-ediscovery-for-your-office-365-dev-test-environment.md)
    
    Office 365에 저장된 전자 메일, 문서 등의 데이터를 빠르게 찾고 분석하도록 예제 데이터를 추가하고 Advanced eDiscovery를 보여 줍니다.
    
- [Office 365 개발/테스트 환경용 중요 파일 보호](sensitive-file-protection-in-the-office-365-dev-test-environment.md)
    
    실수로 문서를 잘못된 폴더에 게시한다 하더라도 Office 365 정보 권한 관리를 사용하여 중요한 문서의 데이터를 보호할 수 있는 방법을 보여 줍니다.
    
- [Office 365 개발/테스트 환경에서 데이터 분류 및 레이블 지정](data-classification-and-labeling-in-the-office-365-dev-test-environment.md)
    
    Azure Information Protection(AIP) 클라이언트를 사용하여 다양한 수준의 보안으로 문서를 분류하는 방법을 보여 줍니다.
    
- [개발/테스트 환경에서 격리된 SharePoint Online 팀 사이트](isolated-sharepoint-online-team-site-dev-test-environment.md)
    
    중요하거나 극비 사항인 리소스를 위해 조직의 나머지와 분리된 SharePoint Online Group 사이트를 만드는 방법을 보여 줍니다.
    
## <a name="the-microsoft-365-enterprise-devtest-environment"></a>Microsoft 365 Enterprise 개발/테스트 환경
<a name="O365"> </a>

다음 문서의 시나리오를 따라 [Microsoft 365 Enterprise](https://docs.microsoft.com/microsoft-365-enterprise/)용 개발/테스트 환경을 만들어보세요.
  
- [Microsoft 365 Enterprise 개발/테스트 환경](the-microsoft-365-enterprise-dev-test-environment.md)
    
    Office 365 E5, EMS E5 및 Windows 10 Enterprise를 실행하는 컴퓨터를 포함한 초기 환경을 만듭니다.
    
- [Microsoft 365 Enterprise 개발/테스트 환경용 MAM(모바일 응용 프로그램 관리) 정책](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
    
    사용자 그룹과 iOS 및 Android 장치용 MAM(모바일 응용 프로그램 관리) 정책을 만듭니다.
    
- [Microsoft Enterprise 365 개발/테스트 환경에서 iOS 및 Android 장치 등록](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
    
    iOS 또는 Android 장치를 등록하고 원격으로 관리합니다.
    
## <a name="office-365-and-dynamics-365-devtest-environment"></a>Office 365 및 Dynamics 365 개발/테스트 환경
<a name="O365_D365"> </a>

이러한 문서를 사용하여 Dynamics 365 평가판 구독을 추가하고 Office 365 및 Dynamics 365 통합 기능 및 시나리오를 테스트합니다.
  
- [Office 365 및 Dynamics 365 개발/테스트 환경](office-365-and-dynamics-365-dev-test-environment.md)
    
    Dynamics 365 평가판 구독과 Dynamics 365 라이선스 및 권한을 사용자 계정에 추가합니다.
    
- [Office 365 및 Dynamics 365 개발/테스트 환경용 Exchange Online 통합](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md)
    
    Office 365 및 Dynamics 365가 Exchange Online 사서함에서 함께 작동하는 방식을 구성한 다음 보여 줍니다.
    
## <a name="the-one-microsoft-cloud-devtest-environment"></a>One Microsoft Cloud 개발/테스트 환경
<a name="O365_D365"> </a>

Microsoft의 모든 클라우드 서비스(Office 365, Azure, EMS, 및 Dynamics 365)를 포함하여 개발/테스트 환경을 만들어보세요. 단계별 지침에 대해서는 [One Microsoft Cloud 개발/테스트 환경](the-one-microsoft-cloud-dev-test-environment.md)을 참조하세요.
  
## <a name="simulated-cross-premises-devtest-environments"></a>시뮬레이션된 프레미스 간 개발/테스트 환경
<a name="O365_D365"> </a>

이러한 문서를 사용하여 Azure Virtual Network, 시뮬레이션된 온-프레미스 네트워크 등의 프레미스 간 개발/테스트 환경을 만들 수 있습니다.
  
- [시뮬레이트된 Azure의 크로스-프레미스 가상 네트워크](simulated-cross-premises-virtual-network-in-azure.md)
    
    하이브리드 클라우드 구성에서 Azure Virtual Network에 연결된 시뮬레이션된 인트라넷을 만듭니다.
    
- [Azure 개발/테스트 환경의 인트라넷 SharePoint Server 2016](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx)
    
    Azure Virtual Network에 단일 서버 SharePoint Server 2016 팜을 만들고 시뮬레이션된 온-프레미스 네트워크의 연결 및 관리를 테스트합니다.
    
## <a name="additional-cloud-based-devtest-environments"></a>추가 클라우드 기반 개발/테스트 환경
<a name="ADD_TLGs"> </a>

다음은 Azure 인프라 서비스에서 만들 수 있는 추가적인 클라우드 기반 개발/테스트 환경입니다.
  
- [Azure의 SharePoint Server 2016 개발/테스트 환경](https://technet.microsoft.com/library/mt723354.aspx)
    
    Azure 인프라 서비스에 단일 서버 SharePoint Server 2016 팜을 구축합니다.
    
- [Azure의 Exchange 2016 개발/테스트 환경](https://technet.microsoft.com/library/mt733070%28v=exchg.160%29.aspx)
    
    Azure 인프라 서비스에 단일 Exchange 2016 서버를 구축합니다.
    
- [Azure의 SharePoint Server 2013 개발/테스트 환경](http://technet.microsoft.com/library/165de4d5-8fe6-4fbb-a15b-39a8b0a0eb23.aspx)
    
    Azure 인프라 서비스에 기본 및 고가용성 SharePoint Server 2013 팜을 구축합니다.
    
**토론 참여**

|**연락처**|**설명**|
|:-----|:-----|
|**어떤 클라우드 채택 콘텐츠가 필요한가요?** <br/> |여러 Microsoft 클라우드 플랫폼 및 서비스에 적용되는 클라우드 채택 콘텐츠를 만들고 있습니다. 클라우드 채택 콘텐츠에 대한 의견을 제공하거나 [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20)으로 이 메일을 보내서 특정 콘텐츠를 요청하세요.  <br/> |
|**클라우드 채택 토론에 가입** <br/> |클라우드 기반 솔루션에 관심이 있다면 CAAB(클라우드 채택 자문 위원회)에 가입하여 Microsoft 콘텐츠 개발자, 산업 전문가 및 전 세계 고객으로 구성된 더 크고 활발한 커뮤니티에 연결할 수 있습니다. 참가하려면 Microsoft 기술 커뮤니티의 [CAAB(Cloud Adoption Advisory Board) 영역](https://aka.ms/caab)에 본인을 회원으로 추가하고 [CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!)에서 간단한 이메일을 보내주세요. [CAAB 블로그](https://blogs.technet.com/b/solutions_advisory_board/)에서는 누구나 커뮤니티 관련 콘텐츠를 읽을 수 있습니다. 그러나 CAAB 구성원은 새 클라우드 채택 리소스와 솔루션에 대해 설명하는 비공개 웹 세미나에 초대됩니다.<br/> |
|**여기에 표시된 아트 받기** <br/> |이 문서에 표시된 아트의 편집 가능한 복사본을 원하시면 보내드리겠습니다. 아트의 URL과 제목을 적어서 [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20)으로 요청 이메일을 보내주세요.  <br/> |
   
## <a name="see-also"></a>참고 항목

<a name="ADD_TLGs"> </a>

[클라우드 채택 및 하이브리드 솔루션](cloud-adoption-and-hybrid-solutions.md)
  
[Microsoft 클라우드 IT 아키텍처 리소스](microsoft-cloud-it-architecture-resources.md)
  
[Exchange, SharePoint, 비즈니스용 Skype 및 Lync에 대한 아키텍처 모델](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[하이브리드 솔루션](hybrid-solutions.md)


