---
title: Microsoft 365 Network Insights (미리 보기)
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 03/31/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Microsoft 365 Network Insights (미리 보기)
ms.openlocfilehash: baab4716ace0b15df5878d21987c037372a2754e
ms.sourcegitcommit: 6508db0a839427e1a21b1cde883d828e3c8886c6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "43185759"
---
# <a name="microsoft-365-network-insights-preview"></a>Microsoft 365 Network Insights (미리 보기)

**Network insights** 는 Microsoft 365 테 넌 트에서 수집 된 live 성능 메트릭 이며, 테 넌 트의 관리 사용자만 볼 수 있습니다. Insights는 Microsoft 365 관리 센터에 표시 됩니다 <https://portal.microsoft.com/adminportal/home#/networkperformance>.

Insights는 사무실 사무소에 대 한 네트워크 perimeters 디자인에 도움을 주기 위한 것입니다. 각 통찰력은 사용자가 테 넌 트에 액세스 하는 각 지리적 위치에 대 한 특정 일반적인 문제의 성능 특성에 대 한 실시간 세부 정보를 제공 합니다.

각 사무실 위치에 대해 표시할 수 있는 5 가지 특정 네트워크 정보가 있습니다.

- [Backhauled 네트워크 송신](#backhauled-network-egress)
- [주변 고객에 게 더 나은 성능 검색](#better-performance-detected-for-customers-near-you)
- [최적이 아닌 Exchange Online 서비스 전면 도어 사용](#use-of-a-non-optimal-exchange-online-service-front-door)
- [최적이 아닌 SharePoint Online 서비스 전면 도어 사용](#use-of-a-non-optimal-sharepoint-online-service-front-door)
- [SharePoint 전면 도어에서 다운로드 속도 낮음](#low-download-speed-from-sharepoint-front-door)

>[!IMPORTANT]
>네트워크 insights, Microsoft 365 관리 센터의 성능 권장 사항 및 평가는 현재 미리 보기 상태 이며, 기능 미리 보기 프로그램에 등록 되어 있는 Microsoft 365 테 넌 트에만 사용할 수 있습니다.

## <a name="backhauled-network-egress"></a>Backhauled 네트워크 송신

이 통찰력은 네트워크 insights 서비스가 지정 된 사용자 위치에서 네트워크 송신으로의 거리가 500 마일 (800 킬로미터) 보다 크면 Microsoft 365 트래픽이 일반 인터넷에 지 장치 또는 프록시로 backhauled는 것을 의미 합니다.

이 통찰력은 일부 요약 보기에서 "Egress"로 간략 한 것입니다.

![Backhauled 네트워크 송신](Media/m365-mac-perf/m365-mac-perf-insights-detail-backhauled.png)

### <a name="what-does-this-mean"></a>시나리오

이는 사무실 위치와 네트워크 송신 사이의 거리가 500 마일 (800 킬로미터) 보다 큼을 식별 합니다. Office 위치는 난독 처리 된 클라이언트 컴퓨터 위치로 식별 되며 네트워크 송신 위치는 역방향 IP 주소를 위치 데이터베이스에 사용 하 여 식별 됩니다. 컴퓨터에서 Windows 위치 서비스를 사용 하지 않도록 설정 하면 office 위치가 정확 하지 않을 수 있습니다. 역방향 IP 주소 데이터베이스 정보가 부정확 한 경우 네트워크 송신 위치가 부정확 하 게 될 수 있습니다.

이러한 통찰력에 대 한 자세한 내용은 사무실 위치, 현재 네트워크 송신 위치, egress 위치의 관련성, 위치 및 현재 송신 지점 간의 거리, 조건이 처음 검색 된 날짜, 조건이 해결 된 날짜 등을 포함 합니다.

### <a name="what-should-i-do"></a>제가 뭘 해야 하나요?

이에 대 한 자세한 내용은 연결을 통해 최적의 microsoft 글로벌 네트워크 및 가장 가까운 Microsoft 365 서비스 전면 도어로 경로를 지정할 수 있도록 네트워크를 office 위치에 더 가깝게 egress 것을 권장 합니다. 또한 사용자에 게 네트워크를 닫도록 네트워크가 송신 되도록 설정 하면 향후에도 Microsoft는 네트워크의 현재 상태와 Microsoft 365 서비스 전면 도어를 모두 확장 하는 동시에 성능을 향상 시킬 수 있습니다.

이 문제를 해결 하는 방법에 대 한 자세한 내용은 [Office 365 네트워크 연결 원리](office-365-network-connectivity-principles.md)에서 [로컬로 Egress 네트워크 연결](office-365-network-connectivity-principles.md#egress-network-connections-locally) 을 참조 하십시오.

## <a name="better-performance-detected-for-customers-near-you"></a>주변 고객에 게 더 나은 성능 검색

이 통찰력은 네트워크 insights 서비스에서이 사무실 위치에 있는 조직의 사용자 보다 많은 수의 metro 영역을 검색 하는 경우에 표시 됩니다.

이 통찰력은 일부 요약 보기에서 "피어"로 간략 한 것입니다.

![상대적 네트워크 성능](Media/m365-mac-perf/m365-mac-perf-insights-detail-cust-near-you.png)

### <a name="what-does-this-mean"></a>시나리오

이러한 통찰력은이 사무실 위치와 같은 도시의 Microsoft 365 고객의 집계 성과를 검사 합니다. 이러한 통찰력은 사용자의 평균 대기 시간이 인접 한 테 넌 트의 평균 대기 시간 보다 10% 보다 많은 경우에 표시 됩니다.

### <a name="what-should-i-do"></a>제가 뭘 해야 하나요?

회사 네트워크 또는 ISP의 대기 시간, 병목 현상 또는 아키텍처 디자인 문제를 포함 하 여 이러한 상황이 발생 하는 여러 가지 이유가 있을 수 있습니다. Office 네트워크와 현재 Microsoft 365 전면 도어 간의 경로에 있는 각 홉 사이의 대기 시간을 검사 합니다. 자세한 내용은 [Office 365 네트워크 연결 원리](office-365-network-connectivity-principles.md)를 참조 하세요.

## <a name="use-of-a-non-optimal-exchange-online-service-front-door"></a>최적이 아닌 Exchange Online 서비스 전면 도어 사용

이 통찰력은 네트워크 insights 서비스가 특정 위치의 사용자가 최적의 Exchange Online 서비스 전면 도어에 연결 되지 않는 것을 감지 하는 경우에 표시 됩니다.

이에 대 한 자세한 정보는 요약 보기의 "라우팅" 이라고 합니다.

![최적이 아닌 전면 도어](Media/m365-mac-perf/m365-mac-perf-insights-detail-front-door-exo.png)

### <a name="what-does-this-mean"></a>시나리오

적절 한 성능을 제공 하는 office 위치 도시에서 사용 하기에 적합 한 Exchange Online 서비스 프런트 도어를 나열 합니다. 현재 테스트에서이 목록에 없는 Exchange Online 서비스 앞 도어를 사용 하는 경우에는이 권장 사항을 확인 합니다.

### <a name="what-should-i-do"></a>제가 뭘 해야 하나요?

Exchange Online 서비스 프런트 도어를 사용 하는 경우에는 회사 네트워크 egress가 되기 전에 로컬 및 직접 네트워크 송신을 권장 하는 네트워크 교환이 발생 하는 경우가 있습니다. 또한 원격 DNS 재귀 해결 프로그램 서버를 사용 하는 경우에도 DNS 재귀 해결 프로그램 서버를 네트워크 egress에 정렬 하는 것이 좋습니다.

## <a name="use-of-a-non-optimal-sharepoint-online-service-front-door"></a>최적이 아닌 SharePoint Online 서비스 전면 도어 사용

이 통찰력은 네트워크 insights 서비스가 특정 위치의 사용자가 가장 가까운 SharePoint Online 서비스 앞 도어에 연결 되지 않는 것을 감지 하는 경우에 표시 됩니다.

이 통찰력은 일부 요약 보기에서 "Afd"로 간략 한 것입니다.

![최적이 아닌 전면 도어](Media/m365-mac-perf/m365-mac-perf-insights-detail-front-door-spo.png)

### <a name="what-does-this-mean"></a>시나리오

테스트 클라이언트가 연결 되는 SharePoint Online 서비스 프런트 도어를 식별 합니다. 그런 다음 office 위치 도시에서 해당 도시의 예상 SharePoint Online 서비스 전면 도어를 비교 합니다. 일치 하지 않는 경우이 권장 사항을 확인 합니다.

### <a name="what-should-i-do"></a>제가 뭘 해야 하나요?

네트워크를 사용 하기 전에 회사 네트워크 송신이 가장 좋지 않은 경우 (예를 들어 로컬 및 직접 네트워크 송신을 권장 하는 경우)에는 최적이 아닌 SharePoint Online 서비스 프런트 도어를 사용할 수 있습니다. 또한 원격 DNS 재귀 해결 프로그램 서버를 사용 하는 경우에도 DNS 재귀 해결 프로그램 서버를 네트워크 egress에 정렬 하는 것이 좋습니다.

## <a name="low-download-speed-from-sharepoint-front-door"></a>SharePoint 전면 도어에서 다운로드 속도 낮음

네트워크 insights 서비스가 특정 사무실 위치와 SharePoint Online 간의 대역폭이 1 MBps 미만인 경우이 정보가 표시 됩니다.

이 통찰력은 일부 요약 보기에서 "처리량"으로 간략하게 정리 되었습니다.

### <a name="what-does-this-mean"></a>시나리오

사용자가 SharePoint Online에서 가져올 수 있는 다운로드 속도 및 비즈니스용 OneDrive 서비스의 프런트 도어는 초당 메가바이트 (MBps)로 측정 됩니다. 이 값이 1 MBps 보다 작으면 이러한 통찰력을 제공 합니다.

### <a name="what-should-i-do"></a>제가 뭘 해야 하나요?

다운로드 속도를 개선 하기 위해 대역폭을 늘려야 할 수도 있습니다. 또는 사무실 위치에 있는 사용자 컴퓨터와 SharePoint Online 서비스 전면 도어의 네트워크 정체가 있을 수 있습니다. 이를 congestive 손실 이라고 하는 경우도 있으며 충분 한 대역폭을 사용할 수 있는 경우에도 사용자가 사용할 수 있는 다운로드 속도를 제한 합니다.

## <a name="china-user-optimal-network-egress"></a>중국 사용자 최적 네트워크 송신

이 정보는 조직에서 다른 지리적 위치에 있는 Microsoft 365 테 넌 트에 연결 하는 사용자가 있는 경우에 표시 됩니다. 

### <a name="what-does-this-mean"></a>시나리오

조직에 사설 WAN 연결이 있는 경우 중국의 사무실 위치에서 네트워크 WAN 회로를 구성 하는 것이 좋습니다 (다음 위치에서 인터넷으로 네트워크가 송신 됨).

- 홍콩
- 일본
- 대만
- 대한민국
- 싱가포르
- 말레이시아

인터넷 egress 사용자가 이러한 위치 보다 더 멀리 떨어진 경우에는 성능이 저하 되 고 중국에서 egress로 인해 경계 간 혼잡으로 인 한 대기 시간 및 연결 문제가 발생할 수 있습니다.

### <a name="what-should-i-do"></a>제가 뭘 해야 하나요?

이러한 정보와 관련 된 성능 문제를 완화 하는 방법에 대 한 자세한 내용은 [중국 사용자에 대 한 Office 365 전역 테 넌 트 성능 최적화](https://docs.microsoft.com/office365/enterprise/office-365-networking-china)를 참조 하세요.

## <a name="related-topics"></a>관련 항목

[Microsoft 365 관리 센터의 네트워크 성능 권장 사항 (미리 보기)](office-365-network-mac-perf-overview.md)

[Microsoft 365 네트워크 평가 (미리 보기)](office-365-network-mac-perf-score.md)

[M365 관리 센터의 Microsoft 365 네트워크 온 보 딩 도구 (미리 보기)](office-365-network-mac-perf-onboarding-tool.md)

[Microsoft 365 네트워크 연결 위치 서비스 (미리 보기)](office-365-network-mac-location-services.md)
