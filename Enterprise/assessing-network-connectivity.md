---
title: Office 365 네트워크 연결 평가
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 8/7/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 64b420ef-0218-48f6-8a34-74bb27633b10
description: Office 365은 전세계의 모든 고객이 인터넷 연결을 사용 하 여 서비스에 연결할 수 있도록 하기 위한 것입니다. 서비스가 발전 함에 따라 Office 365의 보안, 성능 및 안정성이 인터넷을 사용 하 여 서비스에 대 한 연결을 설정 하는 고객에 따라 개선 됩니다.
ms.openlocfilehash: c96cb8aa7341c0749d198e1fa5459433c40e1062
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844699"
---
# <a name="assessing-office-365-network-connectivity"></a>Office 365 네트워크 연결 평가

*이 문서는 Microsoft 365 Enterprise와 Office 365 Enterprise에 모두 적용됩니다.*

Office 365은 전세계의 모든 고객이 인터넷 연결을 사용 하 여 서비스에 연결할 수 있도록 하기 위한 것입니다. 서비스가 발전 함에 따라 Office 365의 보안, 성능 및 안정성이 인터넷을 사용 하 여 서비스에 대 한 연결을 설정 하는 고객에 따라 개선 됩니다.
  
Office 365을 사용 하려는 고객은 기존 및 예상 인터넷 연결 요구 사항을 배포 프로젝트의 일부로 평가 해야 합니다. 엔터프라이즈 클래스 배포를 안정적이 고 적절 한 크기의 인터넷 연결을 사용 하는 것은 Office 365 기능과 시나리오를 소비 하는 중요 한 부분입니다.
  
네트워크 평가는 크기 및 기본 설정에 따라 다양 한 사용자 및 조직에서 수행할 수 있습니다. 또한 평가의 네트워크 범위는 배포 프로세스의 위치에 따라 달라질 수 있습니다. 네트워크 평가를 수행 하는 데 필요한 정보를 보다 쉽게 이해할 수 있도록 지원 되는 옵션을 이해 하는 데 도움이 되는 네트워크 평가 가이드를 만들었습니다. 이 평가에서는 Office 365을 성공적으로 채택할 수 있도록 배포 프로젝트에 추가 해야 하는 단계 및 리소스를 결정 합니다.
  
포괄적인 네트워크 평가가 구현 정보와 함께 네트워킹 디자인 문제에 대 한 해결 방법을 제공 합니다. 일부 네트워크 평가에서는 기존 네트워크 및 인터넷 송신 인프라에 대 한 사소한 구성 또는 디자인 변경을 통해 Office 365에 대 한 최적의 네트워크 연결을 수용할 수 있음을 보여 줍니다.

Office 365에 대 한 네트워크 연결을 나타내는 몇 가지 평가는 네트워킹 구성 요소에 대 한 추가 투자가 필요 합니다. 예를 들어 분기 사무소 및 여러 지리적 지역에 걸쳐 있는 엔터프라이즈 네트워크에는 SD-WAN 솔루션에 대 한 투자 또는 Office 365에 대 한 인터넷 연결을 지원 하기 위한 최적화 된 라우팅 인프라가 필요할 수 있습니다. 경우에 따라 평가는 Office 365에 대 한 네트워크 연결이 [비즈니스용 Skype 온라인 미디어 품질과](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917)같은 시나리오에 대 한 규제 또는 성능 요구 사항의 영향을 받게 되는 경우가 있습니다. 이러한 추가 요구 사항에 따라 인터넷 연결 인프라, 라우팅 최적화 및 특수 직접 연결에 대 한 투자가 발생할 수 있습니다.

네트워크를 평가 하는 데 도움이 되는 리소스는 다음과 같습니다.

- Office 365 네트워킹에 대 한 개념 정보는 [office 365 네트워크 연결 개요](office-365-networking-overview.md) 를 참조 하세요.
- Office [365 네트워크 연결 원리](https://aka.ms/o365networkingprinciples) 를 참조 하 여 365 안전 하 고 효과적으로 해결 되는 방법 및 최적의 성능을 얻는 데 필요한 연결 원칙을 이해 합니다.
- Office 365 계획, 디자인 및 배포에 대 한 안내가 제공 되는 [Microsoft FastTrack](https://www.microsoft.com/fasttrack) 에 등록 합니다. 
- 지정한 사용자 위치와 Office 365 사이에 설치할 수 있는 네트워킹 연결 개선 사항에 대 한 구체적인 지침을 제공 하는 기본 연결 테스트를 실행 하려면 아래의 [Office 365 네트워크 온 보 딩 도구](assessing-network-connectivity.md#the-office-365-network-onboarding-tool) 섹션을 참조 하십시오.

> [!NOTE]
> Microsoft authorization는 Office 365 용 Express 경로를 사용 하는 데 필요 합니다. 고객의 규정 요구 사항에 직접 연결 하는 경우 Microsoft는 모든 고객 요청을 검토 하 고 Office 365 사용에 대 한 사용자만 권한 부여를 승인 합니다. 이러한 요구 사항을 충족 하는 경우 해석 하는 규정에 대 한 텍스트 발췌문 및 웹 링크를 제공 하 여 Microsoft 검토를 시작 하기 [위한 Office 365의 express 경로 요청 양식에](https://aka.ms/O365ERReview) 직접 연결이 필요 하다는 것을 의미 합니다. 인증 되지 않은 구독에서 Office 365에 대 한 경로 필터를 만들려고 하면 [오류 메시지가](https://support.microsoft.com/kb/3181709)표시 됩니다.
  
Office 365에 대 한 네트워크 평가를 계획할 때 고려해 야 할 주요 사항은 다음과 같습니다.
  
- Office 365은 공용 인터넷을 통해 실행 되는 안전 하 고 신뢰할 수 있는 고성능 서비스입니다. 서비스의 이러한 측면을 개선 하기 위해 계속 투자 하 고 있습니다. 인터넷 연결을 통해 모든 Office 365 서비스를 사용할 수 있습니다.

- Microsoft는 가용성, 글로벌, 인터넷 기반 연결에 대 한 성능과 같은 Office 365의 핵심 측면을 지속적으로 최적화 하 고 있습니다. 예를 들어 많은 Office 365 서비스는 확장 된 인터넷 연결에 지 노드 집합을 활용 합니다. 이에 지 네트워크는 인터넷을 통해 들어오는 연결에 대해 가장 적합 한 근접성 및 성능을 제공 합니다.

- 비즈니스용 Skype Online 음성, 비디오 또는 모임 기능과 같은 포함 된 서비스에 대해 Office 365을 사용 하는 경우, 고객은 종단 간 네트워크 평가를 완료 하 고 [Microsoft FastTrack](https://www.microsoft.com/fasttrack)을 사용 하 여 연결 요구 사항을 충족 해야 합니다.

Office 365을 평가 중 이며 네트워크 평가로 시작할 위치를 잘 모르거나 문제를 해결 하는 데 도움이 필요한 네트워크 디자인 문제가 있는지 확실 하지 않은 경우 Microsoft 계정 팀에 문의 하세요.

## <a name="the-office-365-network-onboarding-tool"></a>Office 365 네트워크 온 보 딩 도구

[Office 365 네트워크 온 보 딩 도구](https://aka.ms/netonboard) 는 office 365 테 넌 트에 대해 기본 연결성 테스트를 실행 하 고 최적의 Office 365 성능을 위해 특정 네트워크 디자인을 권장 하는 개념 증명 (POC) 네트워크 평가 도구입니다. 이 도구는 인터넷 웹 브라우징에 유용 하지만 Office 365와 같은 대규모 SaaS 응용 프로그램의 성능에 영향을 주는 일반적인 대규모 엔터프라이즈 네트워크 경계 디자인 옵션을 강조 표시 합니다.

네트워크 온 보 딩 도구는 다음을 수행 합니다.

- 위치를 검색 하거나 테스트할 위치를 지정할 수 있습니다.
- 네트워크 송신 위치를 확인 합니다.
- 네트워크 경로에서 가장 가까운 Office 365 서비스 전면 도어를 테스트 합니다.
- 다운로드 가능한 Windows 10 응용 프로그램을 사용 하 여 프록시 서버, 방화벽 및 DNS와 관련 된 경계 네트워크 디자인 권장 사항을 만드는 고급 테스트를 제공 합니다. 또한이 도구는 비즈니스용 Skype Online, Microsoft 팀, SharePoint Online 및 Exchange Online에 대 한 성능 테스트를 실행 합니다.

이 도구에는 기본 연결 정보를 수집 하는 브라우저 기반 UI와 고급 테스트를 실행 하 고 추가 평가 데이터를 반환 하는 다운로드 가능한 Windows 10 응용 프로그램의 두 가지 구성 요소가 있습니다.

브라우저 기반 도구는 다음 정보를 표시 합니다.

- 결과 및 영향 탭
  - 사용 중 서비스 전면 도어 맵의 위치
  - 최적의 연결을 제공 하는 다른 서비스 전면 문의 맵의 위치
  - 사용자 가까이에 있는 다른 Office 365 고객에 비해 상대적인 성능
- 세부 정보 및 솔루션 탭
  - 구/군/시 및 국가별로 사용자 위치
  - 구/군/시, 시/도를 사용한 네트워크 송신 위치
  - 사용자에서 네트워크로의 송신 거리
  - Office 365 Exchange Online 서비스 전면 도어 위치
  - 최적의 Office 365 사용자 위치에 대 한 Exchange Online 서비스 프런트 도어
  - 사용자의 metro 영역에 있는 고객 (성능 향상)

다운로드 가능한 고급 테스트 응용 프로그램은 다음과 같은 추가 정보를 제공 합니다.

- 세부 정보 및 솔루션 탭 (추가)
  - 사용자의 기본 게이트웨이
  - 클라이언트 DNS 서버
  - 클라이언트 DNS 재귀 해결 프로그램
  - Exchange Online DNS 서버
  - SharePoint Online DNS 서버
  - 프록시 서버 id
  - 미디어 연결 확인
  - 미디어 품질 패킷 손실
  - 미디어 품질 대기 시간
  - 미디어 품질 지터
  - 미디어 품질 패킷 다시 정렬
- 여러 기능별 끝점에 대 한 연결 테스트
- Exchange Online, SharePoint Online 및 팀 서비스에 대 한 tracert 및 대기 시간 데이터를 포함 하는 네트워크 경로 진단

Office 365 네트워크 온 보 딩 도구에 대해 자세히 살펴보고 [업데이트 된 office 365 네트워크 온 보 딩 도구 POC에서 새 네트워크 디자인 권장 사항](https://techcommunity.microsoft.com/t5/Office-365-Networking/Updated-Office-365-Network-Onboarding-Tool-POC-with-new-network/m-p/711130#M130) 블로그 게시물에 대 한 의견을 제공 합니다. 이 도구 및 기타 Office 365 네트워킹 업데이트에 대 한 이후 업데이트에 대 한 정보가 [Office 365 네트워킹](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking) 블로그에 게시 됩니다.
  
여기서는 다음을 수행 [ https://aka.ms/o365networkconnectivity하는 데 사용할 수 있는 간단한 링크를 제공 합니다.](https://aka.ms/o365networkconnectivity)
  
## <a name="see-also"></a>참고 항목

[Office 365 네트워크 연결 개요](office-365-networking-overview.md)

[Office 365 네트워크 연결 원칙](https://aka.ms/o365networkingprinciples)

[Office 365 끝점 관리](managing-office-365-endpoints.md)

[Office 365 URL 및 IP 주소 범위](urls-and-ip-address-ranges.md)

[Office 365 IP 주소 및 URL 웹 서비스](office-365-ip-web-service.md)

[Office 365 네트워크 및 성능 조정](network-planning-and-performance.md)

[Microsoft 365 Enterprise 개요](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
