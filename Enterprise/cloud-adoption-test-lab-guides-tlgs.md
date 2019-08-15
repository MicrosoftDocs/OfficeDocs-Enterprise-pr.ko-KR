---
title: TLG (테스트 랩 가이드)를 사용하여 Office 365 테스트
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 08/12/2019
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
description: '요약: 이 TLG(테스트 랩 가이드)를 사용하여 Office 365의 데모, 개념 증명 또는 개발/테스트 환경을 설정합니다.'
ms.openlocfilehash: 32675683846789f1e7be0e398e5b140d25d7ba80
ms.sourcegitcommit: d58cdc7b2296df12f7a05d14ba05ab224ffb3e0c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/13/2019
ms.locfileid: "36302740"
---
# <a name="test-office-365-with-test-lab-guides-tlgs"></a>TLG (테스트 랩 가이드)를 사용하여 Office 365 테스트

 **요약:** 이 문서를 사용하여 Office 365의 데모, 개념 증명 또는 개발/테스트 환경을 설정합니다.
  
TLG를 사용하면 Microsoft 제품을 빠르게 학습할 수 있습니다. 기술 또는 구성이 자신에게 적합한지 결정을 내리거나, 기술 또는 구성을 디자인, 계획하고, 사용자에게 선보이기 전에 먼저 평가해야 하는 경우에 유용합니다. "직접 구축 후 정상 작동 확인" 실습을 통해 새로운 제품 또는 솔루션의 배포 요구 사항을 이해할 수 있으므로 프로덕션에서 호스팅을 더욱 잘 계획할 수 있습니다.
  
또한, TLG는 응용 프로그램의 개발 및 테스트를 위한 대표적 환경(개발/테스트 환경이라고도 함)을 만들 수도 있습니다.
  
![Microsoft 클라우드의 테스트 랩 가이드](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
## <a name="office-365-devtest-environment"></a>Office 365 개발/테스트 환경

이러한 문서를 사용하여 Office 365 개발/테스트 환경을 구축하세요.
  
- [기본 구성 개발/테스트 환경](base-configuration-dev-test-environment.md)
    
    Microsoft Azure 인프라 서비스에서 실행되는 단순화된 인트라넷을 생성합니다. 이 단계는 시뮬레이트된 엔터프라이즈 구성을 구축하려는 경우에 가능한 선택 사항입니다.
    
- [Office 365 개발/테스트 환경](office-365-dev-test-environment.md)
    
    Office 365 Enterprise E5 평가판 구독을 만듭니다. 이는 컴퓨터에서 또는 Azure 인프라 서비스에서 실행되는 단순화된 인트라넷에서 만들 수 있습니다.
    
- [디렉터리 동기화](dirsync-for-your-office-365-dev-test-environment.md)
    
    암호 해시 동기화를 사용하여 디렉터리를 동기화하는 Azure AD Connect를 설치하고 구성합니다. 이 단계는 시뮬레이트된 엔터프라이즈 구성을 구축하려는 경우에 가능한 선택 사항입니다.
    
Office 365 개발/테스트 환경의 경우 이러한 문서를 사용하여 Office 365의 엔터프라이즈 기능을 보여 줍니다.
  
- [다단계 인증](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
    Office 365 구독 계정을 위해 스마트폰에 전송된 구독 텍스트 메시지를 사용하여 보조 인증을 구성하고 테스트합니다.
    
- [페더레이션 ID](federated-identity-for-your-office-365-dev-test-environment.md)
    
    AD DS(Active Directory Domain Services) 도메인의 계정을 사용하여 페더레이션된 인증을 구성하고 보여 줍니다.
    
- [Advanced Threat Protection](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
    전자 메일에서 맬웨어를 차단하는 EOP(Exchange Online Protection)의 기능인 Advanced Threat Protection을 구성하고 보여 줍니다.

## <a name="simulated-cross-premises-devtest-environment"></a>시뮬레이션된 프레미스 간 개발/테스트 환경

하이브리드 클라우드 구성에서 Azure Virtual Network에 연결된 [시뮬레이션된 인트라넷](simulated-cross-premises-virtual-network-in-azure.md)을 만듭니다.
    
## <a name="sharepoint-server-2016-devtest-environment"></a>SharePoint Server 2016 개발/테스트 환경

Azure 인프라 서비스에 [단일 서버 SharePoint Server 2016 팜](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-dev-test-environment-in-azure)을 구축합니다.

## <a name="microsoft-365-enterprise-devtest-environment"></a>Microsoft 365 Enterprise 개발/테스트 환경

[Microsoft 365 Enterprise](https://docs.microsoft.com/microsoft-365/enterprise/m365-enterprise-test-lab-guides) 개발/테스트 환경을 만듭니다.  
    
## <a name="see-also"></a>참고 항목

[클라우드 채택 및 하이브리드 솔루션](cloud-adoption-and-hybrid-solutions.md)
  
[Microsoft 클라우드 IT 아키텍처 리소스](microsoft-cloud-it-architecture-resources.md)
  
[Exchange, SharePoint, 비즈니스용 Skype 및 Lync에 대한 아키텍처 모델](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[하이브리드 솔루션](hybrid-solutions.md)
