---
title: Office 365에 대한 네트워크 연결
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 4/2/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 64b420ef-0218-48f6-8a34-74bb27633b10
description: Office 365는 전세계 고객에 게 인터넷 연결을 사용 하 여 서비스에 연결할 수 있도록 설계 되었습니다. 서비스 발전 함에 따라 보안, 성능 및 안정성을 Office 365는 향상 된 기반 서비스에 대 한 연결을 설정 하는 인터넷을 사용 하는 고객에 있습니다.
ms.openlocfilehash: b72b0a4584542e4c8673c7cf009c66aa97c6b81c
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542152"
---
# <a name="network-connectivity-to-office-365"></a>Office 365에 대한 네트워크 연결

Office 365는 전세계 고객에 게 인터넷 연결을 사용 하 여 서비스에 연결할 수 있도록 설계 되었습니다. 서비스 발전 함에 따라 보안, 성능 및 안정성을 Office 365는 향상 된 기반 서비스에 대 한 연결을 설정 하는 인터넷을 사용 하는 고객에 있습니다.
  
Office 365를 사용 하 여 계획 하는 고객 배포 프로젝트의 일부로 자신의 기존 수준과 예상 인터넷 연결 요구를 평가 해야 합니다. 엔터프라이즈 클래스 배포에 대 한 안정적이 고 적절 한 크기의 인터넷 연결이 사용 (영문) Office 365 기능 및 시나리오의 중요 한 부분입니다.
  
대부분의 다른 사용자 및 크기 및 기본 설정에 따라 조직에서 네트워크 평가 수행할 수 있습니다. 평가의 네트워크 범위도 배포 프로세스에서에 위치에 따라 달라질 수 있습니다. 보다 잘 이해 하는 네트워크 평가 수행 하는 데 걸리는 얻을 수 있도록, 사용할 수 있는 옵션을 이해 하는데 도움이 되는 네트워크 평가 가이드를 생성 했을 때 했습니다. 이 평가 단계 및 리소스 필요한 정보 성공적으로 Office 365를 채택할 수 있도록 하는 배포 프로젝트에 추가할 수를 결정 합니다.
  
포괄적인 네트워크 평가-이러한 규정된에 [Skype 작업 프레임 워크](https://www.skypeoperationsframework.com/) 를 제공할 구현 세부 사항 함께 네트워킹 디자인 문제를 해결할 수와 동일 하 게 합니다. 대부분의 네트워크 평가 Office 365에 대 한 네트워크 연결을 사용 하 여 [보조 구성 또는 디자인 변경](https://aka.ms/manageo365endpoints) 기존 네트워크와 인터넷 탈출 인프라를 수용할 수 있습니다 표시 됩니다.

일부 평가 Office 365에 대 한 네트워크 연결에는 네트워킹 구성 요소에 대 한 추가 투자가 필요 표시 됩니다. WAN 대역폭 또는 인터넷을 통해 연결 Office 365를 지원 하기 위해 최적화 된 라우팅 인프라 투자 예입니다. 필요에 따라 평가 사용 하는 Office 365에 대 한 네트워크 연결 [비즈니스 온라인 미디어 품질에 대 한 Skype](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917)등의 시나리오에 대 한 규정 또는 성능 요구 사항에 의해 영향을 받습니다 표시 됩니다. 이러한 추가 요구 사항에 투자 한 인터넷 연결 인프라, 라우팅 최적화 및 특수 직접 연결 될 수 있습니다.
  
> [!NOTE]
> Microsoft은 Azure ExpressRoute에 대 한 Microsoft Peering 라우팅 도메인을 검토 하는 방법을 변경 합니다. 2017 년 7 월 31, 시작 Azure ExpressRoute 고객을 모두 사용 하도록 설정할 수 Microsoft Peering Azure 관리 콘솔에서 직접 또는 PowerShell을 통해 합니다. Microsoft Peering를 활성화 한 후 모든 고객에 Dynamics 365 고객 계약 응용 프로그램 (이전의 CRM Online)에 대 한 BGP 경로 알림의 받을 경로 필터를 만들 수 있습니다. Office 365 용 Azure ExpressRoute 필요 고객 계정을 얻어야 검토 Microsoft에서 Office 365에 대 한 경로 필터를 만들 수 있습니다. Office 365 ExpressRoute를 사용 하도록 설정 하는 것에 대 한 검토를 요청 하는 방법에 대해 자세히 알아보려면 Microsoft 계정 팀에 게 문의 하십시오. Office 365에 대 한 경로 필터를 만들 권한이 없는 구독 [오류 메시지](https://support.microsoft.com/kb/3181709)를 받습니다.
  
Office 365에 대 한 네트워크 평가 계획할 때 고려할 주요 내용을:
  
- Office 365는 공용 인터넷을 통해 실행 되는 보안, 안정성, 높은 성능을 서비스입니다. 서비스의 이러한 측면을 향상 시키기 위해 투자 계속 합니다. 모든 Office 365 서비스는 인터넷 연결을 통해 사용할 수 있습니다.

- 가용성, 글로벌 예: Office 365의 측면에 도달 하는 핵심을 지속적으로 최적화는 우리 하 고 인터넷에 대 한 성능 기반 연결 합니다. 등 대부분의 Office 365 서비스 인터넷에 연결 합니다 지 노드를 확장 집합을 활용 합니다. 이 지 네트워크 가장 근접 및 성능 인터넷을 통해 들어오는 연결을 제공 합니다.

- Office 365를 사용 하 여 비즈니스 온라인 음성, 비디오, 또는 모임 기능에 대 한 Skype와 같은 포함 된 서비스 중 하나에 대 한 고려 하 고, 고객을 종단간 네트워크 평가 완료 하 고이 Skype 작업 프레임 워크를 사용 하 여 요구 사항을 충족 해야 합니다. 이러한 고객 ExpressRoute를 포함 하 여 클라우드 연결에 대 한 특정 요구를 충족 하기 위해 여러 옵션이 됩니다.

Microsoft의 사례 연구 [Microsoft Office 365에 대 한 네트워크 성능 최적화를](https://msdn.microsoft.com/en-us/library/mt450488.aspx)보세요. Office 365를 평가 하 고 및 되지 않은 경우 네트워크 평가로 시작 하거나 네트워크 디자인을 찾을 수 있는 위치를 Microsoft 계정 팀과 함께 작업 하십시오 극복 하기 위해 지원 해야 과제 있는지 확인 합니다.
  
또한 안전 하 게 Office 365 트래픽을 관리 하 고 사용 가능한 최고의 성능을 연결 원칙을 이해 하려면 [Office 365 네트워크 연결 원칙](https://aka.ms/o365networkingprinciples) 읽어보십시오. 이 문서는 안전 하 게 Office 365 네트워크 연결을 최적화 하는 것에 대 한 최신 지침을 이해 하는데 도움이 됩니다.
  
다음은 짧은 링크를 다시 사용할 수 있습니다: [ https://aka.ms/o365networkconnectivity합니다.](https://aka.ms/o365networkconnectivity)
  
## <a name="see-also"></a>참고 항목

[Office 365 끝점 관리](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Office 365 끝점 FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
  
[Office 365 네트워크 및 성능 조정](network-planning-and-performance.md)
  
[Office 365용 Azure ExpressRoute](azure-expressroute.md)
  
[Office 365용 ExpressRoute를 사용한 라우팅](routing-with-expressroute.md)
  
[Office 365용 ExpressRoute를 사용한 네트워크 계획](network-planning-with-expressroute.md)
  
[ExpressRoute BGP 커뮤니티를 사용 하 여 Office 365 시나리오 (미리 보기)](bgp-communities-in-expressroute.md)
  
[미디어 품질 및 온라인 비즈니스 Skype 네트워크 연결 성능](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Office 365 URL 및 IP 주소 범위](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Office 365 네트워크 연결 원칙](https://aka.ms/o365networkingprinciples)
