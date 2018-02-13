---
title: "클라우드 도입 TLG(테스트 랩 가이드)"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365, Strat_O365_Enterprise
ms.custom: Strat_O365_Enterprise, Ent_TLGs
ms.assetid: 706d5449-45e5-4b0c-a012-ab60501899ad
description: "요약: 이러한 클라우드 채택 테스트 랩 가이드 (Tlg)를 사용 하 여 데모, 개념, 또는 개발/테스트 환경 영수증 Office 365 \",\" Enterprise 이동성 \"+\" 보안 (EMS) \",\" Dynamics 365 \"및\" Office 서버 제품에 대 한 설정 합니다."
ms.openlocfilehash: f9d2d9a5e092cf310f2d700da0419096a6a15b36
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/13/2018
---
# <a name="cloud-adoption-test-lab-guides-tlgs"></a>클라우드 도입 TLG(테스트 랩 가이드)

 **요약:** 이러한 클라우드 채택 테스트 랩 가이드 (Tlg)를 사용 하 여 데모, 개념, 또는 개발/테스트 환경 영수증 Office 365 "," Enterprise 이동성 "+" 보안 (EMS) "," Dynamics 365 "및" Office 서버 제품에 대 한 설정 합니다.
  
Tlg 도움말을 신속 하 게 Microsoft 제품에 알아봅니다. 기술 이나 구성 하면 또는 사용자에 게 공개 하기 전에 적합 한지 여부를 결정 하기 전에 평가 해야 하는 경우에 유용 합니다. "내 계정 아웃 작성 하 고 작동 하 는" 실습 환경에는 프로덕션 환경에서 호스팅에 대 한 더 잘 계획할 수 있도록 새 제품 또는 솔루션의 배포 요구 사항을 확인할 수 있습니다.
  
또한, TLG는 응용 프로그램의 개발 및 테스트를 위한 대표적 환경(개발/테스트 환경이라고도 함)을 만들 수도 있습니다.
  
![Microsoft 클라우드의 테스트 랩 가이드](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
살펴보기 전에 이러한 추가 리소스를 참조 합니다.
  
- [클라우드 채택 테스트 랩 가이드와 함께 Microsoft 클라우드 환경](https://mva.microsoft.com/en-US/training-courses/experience-the-microsoft-cloud-with-cloud-adoption-test-lab-guides-17960?l=LXNRdhSLE_1000115881 ) Microsoft 가상 Academy 세션 (만 22 시간 (분))를 봅니다.
    
- 클릭 [여기](http://aka.ms/catlgstack) 에 한 맵이 하나의 Microsoft 클라우드 테스트 랩 가이드 스택의 모든 문서를 시각적으로 표시 합니다.
    
## <a name="office-365-devtest-environment"></a>Office 365 개발/테스트 환경
<a name="O365"> </a>

이러한 문서를 사용하여 Office 365 개발/테스트 환경을 구축하세요.
  
- [기본 구성 개발/테스트 환경](base-configuration-dev-test-environment.md)
    
    Microsoft Azure 인프라 서비스에서 실행되는 단순화된 인트라넷을 생성합니다. 이 단계는 시뮬레이트된 엔터프라이즈 구성을 구축하려는 경우에 가능한 선택 사항입니다.
    
- [Office 365 개발/테스트 환경](office-365-dev-test-environment.md)
    
    Azure 인프라 서비스에서 실행 하는 간소화 된 인트라넷 나 사용자의 컴퓨터에서 수행할 수 있는 작업 하는 Office 365 Enterprise E5 평가판 구독을 만듭니다.
    
- [Office 365 개발/테스트 환경용 DirSync](dirsync-for-your-office-365-dev-test-environment.md)
    
    암호 동기화를 사용하여 디렉터리를 동기화하는 Azure AD Connect를 설치하고 구성합니다. 이 단계는 시뮬레이트된 엔터프라이즈 구성을 구축하려는 경우에 가능한 선택 사항입니다.
    
Office 365 개발/테스트 환경에 대 한 이러한 문서를 사용 하 여 Office 365의 enterprise 기능을 설명 합니다.
  
- [Office 365 개발/테스트 환경에 대해 다단계 인증](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
    Office 365 구독 계정을 위해 스마트폰에 전송된 구독 텍스트 메시지를 사용하여 보조 인증을 구성하고 테스트합니다.
    
- [Office 365 개발/테스트 환경에 대 한 페더레이션된 id](federated-identity-for-your-office-365-dev-test-environment.md)
    
    Windows Server Active Directory 도메인의 계정을 사용하여 페더레이션된 인증을 구성하고 보여 줍니다.
    
- [Office 365 개발/테스트 환경에 대 한 클라우드 응용 프로그램 보안](cloud-app-security-for-your-office-365-dev-test-environment.md)
    
    구성 하 고에 대 한 모니터링 하 고 Office 365 구독 의심 스러운 활동의 알리기 위해 여부를 지정 하는 정책을 만들 수 있도록 하는 Office 365 클라우드 응용 프로그램 보안을 시연 합니다.
    
- [Office 365 개발/테스트 환경에 대 한 위협 보호 고급](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
    전자 메일에서 맬웨어를 차단하는 EOP(Exchange Online Protection)의 기능인 Advanced Threat Protection을 구성하고 보여 줍니다.
    
- [Office 365 개발/테스트 환경에 대 한 고급 eDiscovery](advanced-ediscovery-for-your-office-365-dev-test-environment.md)
    
    Office 365에 저장된 전자 메일, 문서 등의 데이터를 빠르게 찾고 분석하도록 예제 데이터를 추가하고 Advanced eDiscovery를 보여 줍니다.
    
- [Office 365 개발/테스트 환경에서 중요 한 파일 보호](sensitive-file-protection-in-the-office-365-dev-test-environment.md)
    
    실수로 문서를 잘못된 폴더에 게시한다 하더라도 Office 365 정보 권한 관리를 사용하여 중요한 문서의 데이터를 보호할 수 있는 방법을 보여 줍니다.
    
- [데이터 분류 및 Office 365 개발/테스트 환경에서 레이블 지정](data-classification-and-labeling-in-the-office-365-dev-test-environment.md)
    
    다양 한 수준의 보안을 사용 하 여 문서를 분류 하는 Azure 정보 보호 (AIP) 클라이언트를 사용할 수 있는 방법을 보여줍니다.
    
- [격리 된 SharePoint Online 팀 사이트 개발/테스트 환경](isolated-sharepoint-online-team-site-dev-test-environment.md)
    
    중요 한 내용 또는 기밀 사항이 자원에 대 한 조직의 나머지 부분에서 분리 되는 SharePoint Online 팀 사이트를 만드는 방법을 보여줍니다.
    
## <a name="the-microsoft-365-enterprise-devtest-environment"></a>Microsoft 365 엔터프라이즈 개발/테스트 환경
<a name="O365"> </a>

이러한 문서와 함께 [Microsoft 365 엔터프라이즈](https://docs.microsoft.com/microsoft-365-enterprise/) 시나리오에 대 한 개발/테스트 환경 만들기:
  
- [Microsoft 365 엔터프라이즈 개발/테스트 환경](the-microsoft-365-enterprise-dev-test-environment.md)
    
    Office 365 e 5, EMS e 5 및 Windows 10 Enterprise를 실행 하는 컴퓨터를 포함 하는 초기 환경을 만듭니다.
    
- [Microsoft 365 엔터프라이즈 개발/테스트 환경에 대 한 MAM 정책](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
    
    사용자 그룹과 iOS 및 Android 장치용 MAM(모바일 응용 프로그램 관리) 정책을 만듭니다.
    
- [IOS 및 Microsoft 기업 365 개발/테스트 환경에서 Android 장치 등록](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
    
    iOS 또는 Android 장치를 등록하고 원격으로 관리합니다.
    
## <a name="office-365-and-dynamics-365-devtest-environment"></a>Office 365 및 Dynamics 365 개발/테스트 환경
<a name="O365_D365"> </a>

이러한 문서를 사용하여 Dynamics 365 평가판 구독을 추가하고 Office 365 및 Dynamics 365 통합 기능 및 시나리오를 테스트합니다.
  
- [Office 365 및 Dynamics 365 개발/테스트 환경](office-365-and-dynamics-365-dev-test-environment.md)
    
    Dynamics 365 평가판 구독과 Dynamics 365 라이선스 및 권한을 사용자 계정에 추가합니다.
    
- [Office 365 및 Dynamics 365 개발/테스트 환경에 대 한 Exchange Online 통합](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md)
    
    Office 365 및 Dynamics 365 작동 하는 방법을 Exchange Online 사서함을 설명 하 고 구성 합니다.
    
## <a name="the-one-microsoft-cloud-devtest-environment"></a>하나의 Microsoft 클라우드 개발/테스트 환경
<a name="O365_D365"> </a>

Microsoft의 클라우드 서비스를 모두 포함 하는 개발/테스트 환경 만들기: Office 365, Azure, EMS, 및 Dynamics 365 합니다. [하나는 Microsoft 클라우드 개발/테스트 환경](the-one-microsoft-cloud-dev-test-environment.md) 대 한 단계별 지침을 참조 하십시오.
  
## <a name="simulated-cross-premises-devtest-environments"></a>시뮬레이션된 프레미스 간 개발/테스트 환경
<a name="O365_D365"> </a>

이러한 문서를 사용하여 Azure Virtual Network, 시뮬레이션된 온-프레미스 네트워크 등의 프레미스 간 개발/테스트 환경을 만들 수 있습니다.
  
- [Azure의 시뮬레이션 된 크로스-프레미스 가상 네트워크](simulated-cross-premises-virtual-network-in-azure.md)
    
    하이브리드 클라우드 구성에서 Azure Virtual Network에 연결된 시뮬레이션된 인트라넷을 만듭니다.
    
- [Azure 개발/테스트 환경에서 인트라넷 SharePoint Server 2016](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx)
    
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
    
**토론에 참가**

|**문의처**|**설명**|
|:-----|:-----|
|**클라우드 채택 콘텐츠 합니까 필요 합니까?** <br/> |여러 Microsoft 클라우드 플랫폼 및 서비스에 걸쳐 있는 클라우드 채택에 대 한 콘텐츠를 만듭니다. 보겠습니다 작업을 알 사용해 클라우드 채택 콘텐츠를 구상할 [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20)에 전자 메일을 발송 하 여 특정 콘텐츠를 요청 합니다.<br/> |
|**클라우드 채택 토론에 참가** <br/> |클라우드 기반 솔루션에 열정을 갖고 인 경우에는 클라우드 채택 자문 보드 (CAAB) Microsoft 콘텐츠 개발자, 업계 전문가는 전세계 어디에서 고객의 더 큰, 생생한 커뮤니티와 연결할에 참가 하는 것이 좋습니다. 참가, Microsoft 기술 커뮤니티의 [CAAB (클라우드 채택 자문 위원회) 공간](https://aka.ms/caab) 의 구성원으로 자신을 추가 하 고 [CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!)에서 빠른 전자 메일을 보내주시기 합니다. 누구나 [CAAB 블로그 (영문)](https://blogs.technet.com/b/solutions_advisory_board/)에서 커뮤니티 관련 콘텐츠를 읽을 수 있습니다. 그러나 CAAB 구성원에 게 새 클라우드 채택 리소스 및 솔루션에 설명 하는 개인 웨 초대장을 가져옵니다.<br/> |
|**여기에서 참조 하 여 아트 가져오기** <br/> |이 문서에서 참조 하는 이미지의 편집 가능한 복사본을 원하는 귀하에 게 보내야 기꺼이 표시 됩니다. URL 및 [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20)는 이미지의 제목을 포함 하 여 요청을 전자 메일로 보냅니다.<br/> |
   
## <a name="see-also"></a>참고 항목

<a name="ADD_TLGs"> </a>

[클라우드 채택 및 하이브리드 솔루션](cloud-adoption-and-hybrid-solutions.md)
  
[Microsoft 클라우드 IT 아키텍처 리소스](microsoft-cloud-it-architecture-resources.md)
  
[Exchange, SharePoint, 비즈니스용 Skype 및 Lync에 대한 아키텍처 모델](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[하이브리드 솔루션](hybrid-solutions.md)


