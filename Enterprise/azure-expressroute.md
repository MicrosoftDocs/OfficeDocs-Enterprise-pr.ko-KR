---
title: Office 365용 Azure Express 경로
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/5/2019
audience: ITPro
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
description: Azure Express를 Office 365에서 사용 하는 방법과 Office 365에 사용할 Azure Express 경로를 배포 하는 경우에 필요한 네트워크 구현 프로젝트를 계획 하는 방법에 대해 알아봅니다.
ms.openlocfilehash: 360cae39010f35b5a921ec95f6e8ed1d02afb808
ms.sourcegitcommit: ecfa362182f906befa885bf5f0094528ff570779
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/09/2019
ms.locfileid: "37435412"
---
# <a name="azure-expressroute-for-office-365"></a>Office 365용 Azure Express 경로

*이 문서는 Office 365 Enterprise 및 Microsoft 365 Enterprise에 모두 적용 됩니다.*

Azure Express를 Office 365에서 사용 하는 방법과 Office 365에 사용할 Azure Express 경로를 배포 하는 경우에 필요한 네트워크 구현 프로젝트를 계획 하는 방법에 대해 알아봅니다. Azure에서 실행 되는 인프라 및 플랫폼 서비스는 네트워크 아키텍처 및 성능 고려 사항에 영향을 주는 경우가 많습니다. 이러한 경우 Azure에 대 한 모든 방법을 사용할 것을 권장 합니다. Office 365 및 Dynamics 365과 같은 서비스 제품을 제공 하는 소프트웨어는 인터넷을 통해 안전 하 고 안정적으로 액세스할 수 있도록 작성 되었습니다. [Office 365 네트워크 연결을 평가](assessing-network-connectivity.md)하는 문서에서 인터넷 성능 및 보안에 대해 자세히 설명 하 고 office 365의 Azure express를 고려할 수 있는 경우를 확인할 수 있습니다.

> [!NOTE]
> Microsoft authorization는 Office 365 용 Express 경로를 사용 하는 데 필요 합니다. 고객의 규정 요구 사항에 직접 연결 하는 경우 모든 고객을 검토 하 고 Office 365 사용에 대 한 사용자를 요청 하 고 권한을 부여 합니다. 이러한 요구 사항을 충족 하는 경우 해석 하는 규정에 대 한 텍스트 발췌문 및 웹 링크를 제공 하 여 Microsoft 검토를 시작 하기 [위한 Office 365의 express 경로 요청 양식에](https://aka.ms/O365ERReview) 직접 연결이 필요 하다는 것을 의미 합니다. 인증 되지 않은 구독에서 Office 365에 대 한 경로 필터를 만들려고 하면 [오류 메시지가](https://support.microsoft.com/kb/3181709)표시 됩니다.

이제 선택한 Office 365 네트워크 트래픽에 대해 Office 365에 직접 네트워크 연결을 추가할 수 있습니다. Azure Express에서는 Microsoft 네트워킹 구성 요소에 대 한 직접 연결과 예측 가능한 성능을 제공 하 고 가동 시간 SLA를 99.95%와 제공 합니다. Azure Express 경로를 통해 지원 되지 않는 서비스의 경우에도 인터넷 연결이 필요 합니다.

## <a name="planning-azure-expressroute-for-office-365"></a>Office 365에 대 한 Azure Express 경로 계획

인터넷에 연결 하는 것 외에도 예측 가능성 및 Microsoft 네트워킹 구성 요소에 대 한 99.95%의 가동 시간 SLA를 제공 하는 직접 연결을 통해 Office 365 네트워크 트래픽의 하위 집합을 라우팅하도록 선택할 수 있습니다. Azure Express 서버는 Office 365 및 기타 Microsoft 클라우드 서비스에 대 한 이러한 전용 네트워크 연결을 제공 합니다.

기존 MPLS WAN이 있는지 여부에 관계 없이, 세 가지 방법 중 하나를 통해이를 네트워크 아키텍처에 추가할 수 있습니다. 지원 되는 클라우드 exchange 공동 위치 공급자, 이더넷 지점간 연결 공급자 또는 MPLS 연결 공급자를 통해 제공 됩니다. [해당 지역에서 사용할 수 있는 공급자를](https://azure.microsoft.com/documentation/articles/expressroute-locations/)참조 하세요. 직접 Express 연결을 사용 하면 아래에 나와 있는 [Office 365 서비스가 포함 된](azure-expressroute.md#BKMK_WhatDoIGet) 응용 프로그램에 대 한 연결을 사용할 수 있습니다. 다른 모든 응용 프로그램 및 서비스에 대 한 네트워크 트래픽은 인터넷을 계속 통과 합니다.

Office 365, Windows Update, TechNet 등의 모든 Microsoft 응용 프로그램에 액세스할 수 있도록 인터넷을 통해 Microsoft의 데이터 센터에 연결 하는 일반적인 Office 365 고객을 보여 주는 다음과 같은 높은 수준의 네트워크 다이어그램을 고려해 야 합니다. 고객은 온-프레미스 네트워크에서 연결 하는지 아니면 독립적으로 인터넷 연결을 사용 하 든 관계 없이 비슷한 네트워크 경로를 사용할 수 있습니다.

![Office 365 네트워크 연결](media/9d8bc622-4a38-4a3b-a0f3-68657712d460.png)

이제 인터넷 및 Express 사용자를 모두 사용 하 여 Office 365에 연결 하는 Office 365 고객을 나타내는 업데이트 된 다이어그램을 확인 합니다. 공용 DNS 및 콘텐츠 배달 네트워크 노드와 같은 일부 연결에서는 여전히 공용 인터넷 연결이 필요 합니다. 또한 사용자가 연결 된 거 짓는 건물에 없는 고객은 인터넷을 통해 연결 하는 것을 볼 수 있습니다.

![간 Office 365 연결 (Express)](media/251788c4-0937-4584-9b2c-df08e11611fc.png)

계속 해 서 정보를 원하십니까? [Office 365의 Azure express 경로를 사용 하 여 네트워크 트래픽을 관리](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408) 하는 방법에 대해 알아보고 [office 365에 대 한 azure express](https://azure.microsoft.com/documentation/articles/expressroute-faqs/)경로를 구성 하는 방법을 알아보세요. 또한 채널 9에 [대 한 Office 365 교육](https://channel9.msdn.com/series/aer) 시리즈를 위한 10 부 Azure express를 기록 하 여 개념을 보다 철저히 설명할 수 있습니다.

## <a name="what-office-365-services-are-included"></a>어떤 Office 365 서비스가 포함 됩니까?
<a name="BKMK_WhatDoIGet"> </a>

다음 표에는 Express를 통해 지원 되는 Office 365 서비스가 나와 있습니다. 이러한 응용 프로그램에 대 한 네트워크 요청에 인터넷 연결이 필요한 지 알아보려면 [Office 365 endpoints 문서](https://aka.ms/o365endpoints) 를 검토 하세요.

|**포함 된 응용 프로그램**|
|:-----|
|Exchange Online<sup>1</sup> <br/> Exchange Online Protection<sup>1</sup> <br/> Delve<sup>1</sup> <br/> |
|비즈니스용 Skype Online<sup>1</sup> <br/> Microsoft 팀 <sup>1</sup> <br/> |
|SharePoint Online<sup>1</sup> <br/> 비즈니스용 OneDrive<sup>1</sup> <br/> Project Online<sup>1</sup> <br/> |
|포털 및 공유<sup>1</sup> <br/> Azure Active Directory<sup>1</sup> <br/> AAD Connect<sup>1</sup> <br/> Office<sup>1</sup> <br/> |

<sup>1</sup> 이러한 각 응용 프로그램은 Express에서 지원 되지 않는 인터넷 연결 요구 사항이 있습니다. 자세한 내용은 [Office 365 endpoints 문서](https://aka.ms/o365endpoints) 를 참조 하십시오.

Office 365에 대 한 Express에 포함 되지 않은 서비스는 중국의 Office 365 ProPlus 클라이언트 다운로드, 온-프레미스 Id 공급자 로그인 및 Office 365 (21 Vianet 되며) 서비스입니다.

## <a name="implementing-expressroute-for-office-365"></a>Office 365용 ExpressRoute 구현

이 방법을 구현 하려면 네트워크 및 응용 프로그램 소유자의 참여가 필요 하며, 새 [네트워크 라우팅 아키텍처](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408), 대역폭 요구 사항, 보안을 구현할 위치, 고가용성 등을 결정 하기 위한 신중한 계획이 필요 합니다. 합니다. Express를 구현 하려면 다음을 수행 해야 합니다.

1. Office 365 연결 계획에서 요구 하는 Express가 충족 하는지 완전히 이해 합니다. 인터넷 또는 Express를 사용 하는 응용 프로그램을 이해 하 고, Office 365 트래픽에 대 한 인터넷 및 용 수를 모두 사용 하는 컨텍스트에서 네트워크 용량, 보안 및 고가용성 요구 사항을 완전히 계획 합니다.

2. 인터넷 및 Express 통신<sup>1</sup>의 egress 및 피어 링 위치를 확인 합니다.

3. 인터넷 및가을 연결 하는 데 필요한 용량을 결정 합니다.

4. 보안 및 기타 표준 주변 컨트롤<sup>1</sup>을 구현 하기 위한 계획을 마련 합니다.

5. Express를 구독 하려면 유효한 Microsoft Azure 계정이 있어야 합니다.

6. 연결 모델 및 [승인 된 공급자](https://azure.microsoft.com/documentation/articles/expressroute-locations/)를 선택 합니다. 고객은 여러 연결 모델 또는 파트너를 선택할 수 있으며, 파트너가 기존 네트워크 공급자와 같을 필요는 없습니다.

7. 트래픽을 Express로 전송 하기 전에 배포 유효성을 검사 합니다.

8. 선택적으로 [QoS를 구현](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d) 하 고 지역별 확장을 평가 합니다.

<sup>1</sup> 중요 한 성능 고려 사항 여기에서 결정 사항은 비즈니스용 Skype와 같은 응용 프로그램에 중요 한 대기 시간에 영향을 미칠 수 있습니다.

추가 참조에 대해서는 [라우팅 가이드](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408) 와, [express 경로 설명서](https://azure.microsoft.com/documentation/articles/expressroute-introduction/)를 사용 하십시오.

Office 365에 대 한 Express를 구입 하려면 하나 이상의 [승인 된 공급자](https://azure.microsoft.com/documentation/articles/expressroute-locations/) 와 협력 하 여 express Premium 구독에 원하는 수 및 크기의 회로를 프로 비전 해야 합니다. Office 365에서 구입할 추가 라이선스가 없습니다.

다음의 간단한 링크를 사용할 수 있습니다. [https://aka.ms/expressrouteoffice365](https://aka.ms/expressrouteoffice365)

[Office 365에 대 한 express](https://aka.ms/ert)를 등록할 준비가 되셨습니까?

## <a name="related-topics"></a>관련 주제

[Office 365 네트워크 연결 평가](assessing-network-connectivity.md)

[Office 365 연결에 대한 ExpressRoute 관리](managing-expressroute-for-connectivity.md)

[Office 365용 ExpressRoute를 사용한 라우팅](routing-with-expressroute.md)

[Office 365용 ExpressRoute를 사용한 네트워크 계획](network-planning-with-expressroute.md)

[Office 365용 ExpressRoute 구현](implementing-expressroute.md)

[Office 365의 Express에서 BGP 커뮤니티 사용 (미리 보기)](bgp-communities-in-expressroute.md)

[비즈니스용 Skype Online의 미디어 품질 및 네트워크 연결 성능](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)

[초기 계획 및 성능 기록을 사용하여 Office 365 성능 조정](performance-tuning-using-baselines-and-history.md)

[Office 365 성능 문제 해결 계획](performance-troubleshooting-plan.md)

[Office 365 URL 및 IP 주소 범위](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges)

[Office 365 네트워크 및 성능 조정](network-planning-and-performance.md)

## <a name="see-also"></a>참고 항목

[Microsoft 365 Enterprise 개요](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
