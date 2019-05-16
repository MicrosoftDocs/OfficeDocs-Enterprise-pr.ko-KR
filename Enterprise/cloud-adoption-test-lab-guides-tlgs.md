---
title: 클라우드 채택 TLG(테스트 랩 가이드)로 Office 365 테스트
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/09/2019
audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 706d5449-45e5-4b0c-a012-ab60501899ad
description: '요약: 이러한 클라우드 채택 TLG(테스트 랩 가이드)를 사용하여 Office 365의 데모, 개념 증명 또는 개발/테스트 환경을 설정합니다.'
ms.openlocfilehash: a61716ae34d8dbe3f710696570c46cefd0f4aa4c
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068144"
---
# <a name="test-office-365-with-cloud-adoption-test-lab-guides-tlgs"></a>클라우드 채택 TLG(테스트 랩 가이드)로 Office 365 테스트

 **요약:** 이러한 클라우드 채택 TLG(테스트 랩 가이드)를 사용하여 Office 365의 데모, 개념 증명 또는 개발/테스트 환경을 설정합니다.
  
TLG를 사용하면 Microsoft 제품을 빠르게 학습할 수 있습니다. 기술 또는 구성이 자신에게 적합한지 결정을 내리거나, 기술 또는 구성을 디자인, 계획하고, 사용자에게 선보이기 전에 먼저 평가해야 하는 경우에 유용합니다. "직접 구축 후 정상 작동 확인" 실습을 통해 새로운 제품 또는 솔루션의 배포 요구 사항을 이해할 수 있으므로 프로덕션에서 호스팅을 더욱 잘 계획할 수 있습니다.
  
또한, TLG는 응용 프로그램의 개발 및 테스트를 위한 대표적 환경(개발/테스트 환경이라고도 함)을 만들 수도 있습니다.
  
![Microsoft 클라우드의 테스트 랩 가이드](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
[여기](http://aka.ms/catlgstack)를 클릭하여 Office 365 테스트 랩 가이드 스택의 모든 문서에 대한 가상 맵을 확인할 수 있습니다.
    
## <a name="office-365-devtest-environment"></a>Office 365 개발/테스트 환경

이러한 문서를 사용하여 Office 365 개발/테스트 환경을 구축하세요.
  
- [기본 구성 개발/테스트 환경](base-configuration-dev-test-environment.md)
    
    Microsoft Azure 인프라 서비스에서 실행되는 단순화된 인트라넷을 생성합니다. 이 단계는 시뮬레이트된 엔터프라이즈 구성을 구축하려는 경우에 가능한 선택 사항입니다.
    
- [Office 365 개발/테스트 환경](office-365-dev-test-environment.md)
    
    Office 365 Enterprise E5 평가판 구독을 만듭니다. 이는 컴퓨터에서 또는 Azure 인프라 서비스에서 실행되는 단순화된 인트라넷에서 만들 수 있습니다.
    
- [Office 365 개발/테스트 환경용 DirSync](dirsync-for-your-office-365-dev-test-environment.md)
    
    암호 해시 동기화를 사용하여 디렉터리를 동기화하는 Azure AD Connect를 설치하고 구성합니다. 이 단계는 시뮬레이트된 엔터프라이즈 구성을 구축하려는 경우에 가능한 선택 사항입니다.
    
Office 365 개발/테스트 환경의 경우 이러한 문서를 사용하여 Office 365의 엔터프라이즈 기능을 보여 줍니다.
  
- [Office 365 개발/테스트 환경용 다단계 인증](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
    Office 365 구독 계정을 위해 스마트폰에 전송된 구독 텍스트 메시지를 사용하여 보조 인증을 구성하고 테스트합니다.
    
- [Office 365 개발/테스트 환경용 페더레이션된 ID](federated-identity-for-your-office-365-dev-test-environment.md)
    
    AD DS(Active Directory Domain Services) 도메인의 계정을 사용하여 페더레이션된 인증을 구성하고 보여 줍니다.
    
- [Office 365 개발/테스트 환경용 Cloud App Security](cloud-app-security-for-your-office-365-dev-test-environment.md)
    
    Office 365 구독에서의 의심스러운 활동을 모니터링하고 알려주는 정책을 만들 수 있는 Office 365 Cloud App Security를 구성하고 보여 줍니다.
    
- [Office 365 개발/테스트 환경용 Advanced Threat Protection](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
    전자 메일에서 맬웨어를 차단하는 EOP(Exchange Online Protection)의 기능인 Advanced Threat Protection을 구성하고 보여 줍니다.
    
- [Office 365 개발/테스트 환경용 고급 eDiscovery](advanced-ediscovery-for-your-office-365-dev-test-environment.md)
    
    Office 365에 저장된 전자 메일, 문서 등의 데이터를 빠르게 찾고 분석하도록 예제 데이터를 추가하고 Advanced eDiscovery를 보여 줍니다.
    
- [Office 365 개발/테스트 환경용 중요 파일 보호](sensitive-file-protection-in-the-office-365-dev-test-environment.md)
    
    실수로 문서를 잘못된 폴더에 게시한다 하더라도 Office 365 정보 권한 관리를 사용하여 중요한 문서의 데이터를 보호할 수 있는 방법을 보여 줍니다.
    
- [Office 365 개발/테스트 환경에서 데이터 분류 및 레이블 지정](data-classification-and-labeling-in-the-office-365-dev-test-environment.md)
    
    Azure Information Protection 클라이언트를 사용하여 다양한 수준의 보안으로 문서를 분류하는 방법을 보여 줍니다.
    
- [격리된 SharePoint Online 팀 사이트 개발/테스트 환경](isolated-sharepoint-online-team-site-dev-test-environment.md)
    
    중요하거나 극비 사항인 리소스를 위해 조직의 나머지와 분리된 SharePoint Online Group 사이트를 만드는 방법을 보여 줍니다.
    

## <a name="simulated-cross-premises-devtest-environments"></a>시뮬레이션된 프레미스 간 개발/테스트 환경

이러한 문서를 사용하여 Azure Virtual Network, 시뮬레이션된 온-프레미스 네트워크 등의 프레미스 간 개발/테스트 환경을 만들 수 있습니다.
  
- [시뮬레이트된 Azure의 크로스-프레미스 가상 네트워크](simulated-cross-premises-virtual-network-in-azure.md)
    
    하이브리드 클라우드 구성에서 Azure Virtual Network에 연결된 시뮬레이션된 인트라넷을 만듭니다.
    
- [Azure 개발/테스트 환경의 인트라넷 SharePoint Server 2016](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx)
    
    Azure Virtual Network에 단일 서버 SharePoint Server 2016 팜을 만들고 시뮬레이션된 온-프레미스 네트워크의 연결 및 관리를 테스트합니다.
    
## <a name="sharepoint-server-2016-devtest-environments"></a>SharePoint Server 2016 개발/테스트 환경

다음은 Azure 인프라 서비스에서 만들 수 있는 SharePoint Server 2016 개발/테스트 환경입니다.
  
- [Azure의 SharePoint Server 2016 개발/테스트 환경](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-dev-test-environment-in-azure)
    
    Azure 인프라 서비스에 단일 서버 SharePoint Server 2016 팜을 구축합니다.

- [Azure 개발/테스트 환경의 인트라넷 SharePoint Server 2016](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment)
    
    Azure 인프라 서비스에 단일 서버 SharePoint Server 2016 팜을 구축하고 시뮬레이션된 인트라넷에서 액세스합니다.


## <a name="the-microsoft-365-enterprise-devtest-environments"></a>Microsoft 365 Enterprise 개발/테스트 환경

[이러한 문서](https://docs.microsoft.com/microsoft-365/enterprise/m365-enterprise-test-lab-guides)에 따라 [Microsoft 365 Enterprise](https://docs.microsoft.com/microsoft-365-enterprise/)용 개발/테스트 환경을 만들어보세요.  
    
## <a name="see-also"></a>참고 항목

[클라우드 채택 및 하이브리드 솔루션](cloud-adoption-and-hybrid-solutions.md)
  
[Microsoft 클라우드 IT 아키텍처 리소스](microsoft-cloud-it-architecture-resources.md)
  
[Exchange, SharePoint, 비즈니스용 Skype 및 Lync에 대한 아키텍처 모델](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[하이브리드 솔루션](hybrid-solutions.md)
