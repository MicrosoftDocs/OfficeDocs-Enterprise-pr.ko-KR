---
title: Office 365용 Azure Express 경로
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/01/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 6d2534a2-c19c-4a99-be5e-33a0cee5d3bd
description: Office 365와 Azure ExpressRoute를 사용 하는 방법 및 Office 365에 사용 하기 위한 Azure ExpressRoute를 배포 하는 경우 필요할 수 있는 네트워크 구현 프로젝트를 계획 하는 방법에 알아봅니다.
ms.openlocfilehash: c8cff4ef85c4383ba04829cf3cf8da3a1bc36715
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2019
ms.locfileid: "25911402"
---
# <a name="azure-expressroute-for-office-365"></a>Office 365용 Azure Express 경로

Office 365와 Azure ExpressRoute를 사용 하는 방법 및 Office 365에 사용 하기 위한 Azure ExpressRoute를 배포 하는 경우 필요할 수 있는 네트워크 구현 프로젝트를 계획 하는 방법에 알아봅니다. Azure에서 실행 중인 인프라 및 플랫폼 서비스 네트워크 아키텍처 및 성능 고려 사항이 해결 하 여 사용 하면 좋은 됩니다. 이러한 경우 azure ExpressRoute를 좋습니다. Office 365 및 Dynamics 365 빌드되어에 안전 하 게 하 고 안정적으로 인터넷을 통해 액세스할 수와 동일 하 게 하는 서비스 제품으로 소프트웨어입니다. 인터넷 성능 및 보안에 대 한 및 좋습니다 Azure ExpressRoute Office 365에 대 한 문서 [Office 365에 대 한 네트워크 연결](network-connectivity.md)에서 읽을 수 있습니다.

> [!NOTE]
> Office 365에 대 한 ExpressRoute를 사용 하는 데 Microsoft 인증이 필요 합니다. Microsoft는 모든 고객의 요청을 검토 하 고 요구 사항을 규정 하는 고객의 요구 하는 경우 직접 연결 하는 경우 Office 365 사용 현황에 대 한 ExpressRoute에 권한을 부여 합니다. 이러한 요구 사항, 있는 경우 Microsoft 검토를 시작 하려면 [Office 365 요청 양식에 대 한 ExpressRoute](https://aka.ms/O365ERReview) 에 직접 연결 필요 하다는 것을 의미를 해석 하는 규정을 텍스트 발췌문 및 웹 링크를 제공 하십시오. Office 365에 대 한 경로 필터를 만들 권한이 없는 구독 [오류 메시지](https://support.microsoft.com/kb/3181709)를 받습니다. 

선택한 Office 365 네트워크 트래픽에 대 한 Office 365에 대 한 네트워크에 직접 연결을 추가할 수 있습니다. Azure ExpressRoute 직접 연결을 예측 가능한 성능을 제공 하 고 Microsoft 네트워킹 구성 요소에 대 한 가동 시간 SLA 99.95%와 함께 제공 합니다. Azure ExpressRoute을 통해 지원 하지 않는 서비스에 대 한 인터넷에 연결을 여전히 필요할 수 있습니다.

## <a name="planning-azure-expressroute-for-office-365"></a>Office 365 용 Azure ExpressRoute 계획

인터넷 연결 외에도 하기도 하 고 Microsoft 네트워킹 구성 요소에 대 한 99.95% 가동 시간 SLA 제공 하는 직접 연결을 통해 자신의 Office 365 네트워크 트래픽의 하위 집합을 라우팅할 수 있습니다. Azure ExpressRoute Office 365 및 기타 Microsoft 클라우드 서비스에 전용된 네트워크 연결이를 제공합니다.

있는지 여부는 기존 MPLS WAN을 관계 없이 ExpressRoute에 추가할 수; 세가지 방법 중 하나에서 네트워크 아키텍처 지원 되는 클라우드 exchange 공동 위치 공급자, 이더넷 지점간 연결 공급자를 통해 또는 MPLS 연결 공급자를 통해 합니다. 어떤 [사용자의 지역에서 사용할 수 있는 공급자를](https://azure.microsoft.com/documentation/articles/expressroute-locations/)참조 합니다. 직접 ExpressRoute 연결에 설명 된 응용 프로그램에 대 한 연결을 사용 하는 [어떤 Office 365 서비스는 포함 되어 있습니까?](azure-expressroute.md#BKMK_WhatDoIGet) 아래 있습니다. 인터넷을 통과 하는 다른 모든 응용 프로그램 및 서비스에 대 한 네트워크 트래픽을 계속 됩니다.

Office 365, Windows Update 및 TechNet 등의 모든 Microsoft 응용 프로그램에 대 한 액세스에 대 한 인터넷을 통해 Microsoft의 데이터 센터에 연결 하는 일반적인 Office 365 고객을 표시 하는 다음과 같은 높은 수준의 네트워크 다이어그램을 고려 합니다. 고객 여부 독립적인 인터넷에 연결 또는 온-프레미스 네트워크에서을 연결 하는경우에만 자신이 관계 없이 비슷한 네트워크 경로 사용 합니다.

![Office 365 네트워크 연결](media/9d8bc622-4a38-4a3b-a0f3-68657712d460.png)

이제 인터넷 및 ExpressRoute를 사용 하 여 Office 365에 연결 하는 Office 365 고객에서는 설명 하는 업데이트 된 다이어그램을 살펴봅니다. 공용 DNS 및 콘텐츠 배달 네트워크 노드와 같은 일부 연결에 여전히 공용 인터넷 연결 필요를 확인 합니다. 또한 인터넷을 통해 연결 하는 연결 된 건물 자신의 ExpressRoute에 있지 않은 고객의 사용자를 확인 하십시오.

![ExpressRoute와의 연결을 office 365](media/251788c4-0937-4584-9b2c-df08e11611fc.png)

자세한 내용은 여전히 지 여부 설명 [Office 365 용 Azure ExpressRoute와 네트워크 트래픽을 관리](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408) 하는 방법을 설명 하 고 [Office 365 용 Azure ExpressRoute를 구성](https://azure.microsoft.com/documentation/articles/expressroute-faqs/)하는 방법입니다. Channel 9를 더 철저 하 게 개념에 설명 하는 데 도움이에서 10 부 [Office 365 교육에 대 한 Azure ExpressRoute](https://channel9.msdn.com/series/aer) 시리즈를 기록 했을 때 했습니다.

([Office 365 용 azure ExpressRoute](azure-expressroute.md#BKMK_HOME))

## <a name="what-office-365-services-are-included"></a>어떤 Office 365 서비스는 포함 되어 있습니까?
<a name="BKMK_WhatDoIGet"> </a>

다음 표에서 ExpressRoute을 통해 지원 되는 Office 365 서비스를 보여줍니다. 이러한 응용 프로그램에 대 한 네트워크 요청은 인터넷 연결 필요를 이해 하는 [Office 365 끝점 문서](https://aka.ms/o365endpoints) 를 검토 하십시오.

|**포함 된 응용 프로그램**|
|:-----|
|Exchange Online<sup>1</sup> <br/> Exchange Online Protection<sup>1</sup> <br/> <sup>1</sup> 굴 <br/> |
|비즈니스 온라인<sup>1</sup> 에 대 한 Skype <br/> |
|SharePoint Online<sup>1</sup> <br/> 비즈니스<sup>1</sup> 에 대 한 OneDrive <br/> Project Online<sup>1</sup> <br/> |
|포털 및 공유<sup>1</sup> <br/> Azure Active Directory<sup>1</sup> <br/> AAD 연결<sup>1</sup> <br/> Office Online<sup>1</sup> <br/> |

<sup>1</sup> 이러한 응용 프로그램의 각 ExpressRoute을 통해 지원 되지 인터넷 연결 요구 사항이 적용에 대 한 자세한 내용은 [Office 365 끝점 문서](https://aka.ms/o365endpoints) 를 참조 하십시오.

Office 365에 대 한 ExpressRoute에 포함 되지 않은 서비스는 Office 365 ProPlus 클라이언트 다운로드, 온-프레미스 Identity 공급자 로그인, 중국에서 (21 Vianet에서 운영) Office 365 서비스입니다.

([Office 365 용 azure ExpressRoute](azure-expressroute.md#BKMK_HOME))

## <a name="implementing-expressroute-for-office-365"></a>Office 365용 ExpressRoute 구현

네트워크 및 응용 프로그램 소유자가 참여 해야 하 고 새 [네트워크 라우팅 아키텍처](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408), 대역폭 요구 사항, 보안 될 위치를 확인 하려면 계획 신중 하 게 구현 고가용성 필요 ExpressRoute 구현 합니다. 를 구현 하기 위해 ExpressRoute 해야 합니다.

1. Office 365 연결 계획에 맞는 ExpressRoute 필요를 완벽 하 게 이해 합니다. 어떤 응용 프로그램이 인터넷 또는 ExpressRoute 사용 하 여를 이해 하 고 완벽 하 게 네트워크 용량을 계획, 보안 및 고가용성 필요한 인터넷 및 ExpressRoute를 사용 하 여 Office 365의 컨텍스트에서 트래픽입니다.

2. 송신 및 인터넷과 ExpressRoute 트래픽을<sup>1</sup>에 대 한 피어 링 위치를 결정 합니다.

3. 인터넷 및 ExpressRoute 연결에 필요한 용량을 결정 합니다.

4. 보안 및 기타 표준 경계 컨트롤<sup>1</sup>을 구현 하기 위한 전체 요금제에 가입한 상태입니다.

5. 유효한 Microsoft Azure 계정이 ExpressRoute 구독할 수 있습니다.

6. [공급자를 승인](https://azure.microsoft.com/documentation/articles/expressroute-locations/)하 고 연결 모델을 선택 합니다. 염두에, 고객 여러 연결 모델을 선택할 수 또는 파트너와의 파트너 기존 네트워크 공급자와 같이 필요가 없습니다.

7. ExpressRoute 트래픽을 웹서버로 전송 하기 전에 배포의 유효성을 검사 합니다.

8. 필요에 따라 [QoS를 구현](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d) 하 고 지역 확장을 평가 합니다.

<sup>1</sup> 중요 한 성능 고려 사항입니다. 여기에 결정 비즈니스를 위한 Skype 등의 응용 프로그램에 대 한 중요 한는 대기 시간에 영향을 줄 크게 수 있습니다.

추가 참조에 대 한 [ExpressRoute 설명서](https://azure.microsoft.com/documentation/articles/expressroute-introduction/)외에도 한 [라우팅 가이드](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408) 를 사용 합니다.

Office 365에 대 한 ExpressRoute를 구입 하려면 하나 이상의 [공급자 승인](https://azure.microsoft.com/documentation/articles/expressroute-locations/) 원하는 수 및 크기 회로 ExpressRoute 프리미엄 구독을 프로 비전을 함께 작동 하도록 필요 합니다. 추가 라이선스가 Office 365에서 구입할 수 있습니다.

다음의 간단한 링크를 사용할 수 있습니다. [https://aka.ms/expressrouteoffice365](https://aka.ms/expressrouteoffice365)

[Office 365에 대 한 ExpressRoute](https://aka.ms/ert)에 대 한로 등록을 준비?

([Office 365 용 azure ExpressRoute](azure-expressroute.md#BKMK_HOME))

## <a name="related-topics"></a>관련 항목

[Office 365에 대한 네트워크 연결](network-connectivity.md)

[Office 365 연결에 대한 ExpressRoute 관리](managing-expressroute-for-connectivity.md)

[Office 365용 ExpressRoute를 사용한 라우팅](routing-with-expressroute.md)

[Office 365용 ExpressRoute를 사용한 네트워크 계획](network-planning-with-expressroute.md)

[Office 365용 ExpressRoute 구현](implementing-expressroute.md)

[Office 365용 ExpressRoute 시나리오에서 BGP 커뮤니티 사용(미리 보기)](bgp-communities-in-expressroute.md)

[비즈니스용 Skype Online의 미디어 품질 및 네트워크 연결 성능](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)

[초기 계획 및 성능 기록을 사용하여 Office 365 성능 조정](performance-tuning-using-baselines-and-history.md)

[Office 365 성능 문제 해결 계획](performance-troubleshooting-plan.md)

[Office 365 URL 및 IP 주소 범위](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges)

[Office 365 네트워크 및 성능 조정](network-planning-and-performance.md)
