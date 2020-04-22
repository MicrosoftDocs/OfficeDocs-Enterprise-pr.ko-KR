---
title: Microsoft 365 네트워크 평가 (미리 보기)
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 04/21/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Microsoft 365 네트워크 평가 (미리 보기)
ms.openlocfilehash: 3554c86b94e6b24cf82231da640b7e010fe07c11
ms.sourcegitcommit: 07ab7d300c8df8b1665cfe569efc506b00915d23
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/21/2020
ms.locfileid: "43612898"
---
# <a name="microsoft-365-network-assessment-preview"></a>Microsoft 365 네트워크 평가 (미리 보기)

Microsoft 365 관리 센터의 Microsoft 365 페이지 연결에서 **네트워크 평가** 는 많은 네트워크 성능 메트릭 집계를 1-100의 포인트 값으로 표시 되는 엔터프라이즈 네트워크 상태의 스냅숏으로 정제 합니다. 네트워크 평가는 전체 테 넌 트와 사용자가 테 넌 트에 연결 하는 각 지리적 위치에 대해 범위가 지정 되므로 Microsoft 365 관리자는 회사의 네트워크 상태를 신속 하 게 파악 하 고 전체 사무실 위치에 대 한 자세한 보고서로 드릴 다운할 수 있는 쉬운 방법을 제공 합니다.

Network 평가 점수 값은 표시 되는 시간에 실시간으로 컴파일된 대기 시간, 대역폭, 다운로드 속도 및 연결 품질 메트릭에 대 한 평균 측정 단위입니다. Microsoft 소유의 네트워크에 대 한 성능 메트릭은 평가 결과가 모호 하 고 회사 네트워크에 한정 되도록 하기 위해 이러한 측정값에서 제외 됩니다.

![네트워크 평가 값](Media/m365-mac-perf/m365-mac-perf-overview-score-top.png)

아주 낮은 네트워크 평가 값은 Microsoft 365 클라이언트에 테 넌 트에 연결 하는 중요 한 문제가 있거나 응답성이 뛰어난 사용자 환경을 유지 관리 하는 반면, 값이 높으면 성능 문제가 거의 없는 네트워크를 올바르게 구성한 것을 의미 합니다. 값이 80%는 네트워크 성능으로 인 한 Microsoft 365 연결 또는 응답성에 대 한 일반 사용자 불만을 수신 하지 않을 것으로 예상 되는 정상적인 기준을 나타냅니다. 반복적으로 네트워크 연결이 개선 됨에 따라이 값은 사용자 환경에 따라 증가 합니다.

>[!IMPORTANT]
>네트워크 insights, Microsoft 365 관리 센터의 성능 권장 사항 및 평가는 현재 미리 보기 상태 이며, 기능 미리 보기 프로그램에 등록 되어 있는 Microsoft 365 테 넌 트에만 사용할 수 있습니다.

## <a name="network-assessment-panel"></a>네트워크 평가 패널

테 넌 트 또는 특정 사무실 위치로 범위가 지정 되었는지 여부에 관계 없이 각 네트워크 평가에는 평가에 대 한 세부 정보가 포함 된 패널이 표시 됩니다. 이 패널에는 평가에 대 한 가로 막대형 차트와 측정 데이터를 받은 작업을 포함 하는 각 구성 요소 작업의 총 지점에 대 한 완료율이 표시 됩니다. Office 위치 네트워크 평가의 경우 office 위치와 같은 도시의 데이터를 보고 한 모든 Microsoft 365 클라이언트의 중앙값을 나타내는 벤치 마크가 표시 됩니다.

![네트워크 평가 값 예](Media/m365-mac-perf/m365-mac-perf-overview-score.png)

패널의 **평가 분석** 에서는 각 구성 요소 작업에 대 한 평가를 보여 줍니다.

**평가 기록** 에는 평가 및 벤치 마크의 최근 30 일이 표시 됩니다.

## <a name="tenant-network-assessments-and-office-location-network-assessments"></a>테 넌 트 네트워크 평가 및 사무실 위치 네트워크 평가

네트워크 평가는 사무실의 네트워크 경계를 Microsoft 네트워크로의 디자인을 측정 합니다. 네트워크 경계에 대 한 향상은 각 사무실 위치에서 또는 네트워크 연결이 집계 되는 위치에 있어 여러 위치에 영향을 주는 향상 된 기능을 제공 하는 것이 좋습니다.

네트워크 성능 개요 페이지에는 전체 Microsoft 365 테 넌 트에 대 한 네트워크 평가 값과 해당 위치의 요약 페이지에 있는 검색 된 각 사무실 위치에 대 한 특정 값이 표시 됩니다.

## <a name="exchange-online"></a>Exchange Online

Exchange Online의 경우 클라이언트 컴퓨터에서 Exchange 프런트 엔드 서버로의 TCP 대기 시간이 측정 됩니다. 이는 네트워크가 고객 LAN 및 WAN을 통과 하는 거리에 영향을 받을 수 있습니다. 또한 연결을 지연 시키거나 패킷을 다시 전송 하도록 하는 네트워크 매개 장치 또는 서비스의 영향을 받을 수 있습니다.

## <a name="sharepoint-online"></a>SharePoint Online

SharePoint Online의 경우 사용자가 문서에 액세스 하는 데 사용할 수 있는 다운로드 속도가 측정 됩니다. 이는 클라이언트 컴퓨터와 Microsoft 네트워크 간의 네트워크 회로에서 사용 가능한 대역폭의 영향을 받을 수 있습니다. 또한 복잡 한 네트워크 장치에서 병목 현상이 발생 한 네트워크 혼잡 이나 적절 하지 않은 서비스 범위에 있는 경우에도 영향을 받습니다.

## <a name="microsoft-teams"></a>Microsoft Teams

Microsoft 팀의 경우 네트워크 품질은 UDP 대기 시간, UDP 지터 및 UDP 패킷 손실으로 측정 됩니다. UDP는 Microsoft 팀의 통화 및 회의 오디오 및 비디오 미디어 연결에 사용 됩니다. 이는 UDP가 보다 일반적인 TCP 프로토콜과 별도로 구성 되므로 네트워크의 UDP 지원에서의 연결 간격 외에도 대기 시간 및 다운로드 속도와 동일한 요인의 영향을 받을 수 있습니다.

## <a name="related-topics"></a>관련 항목

[Microsoft 365 관리 센터의 네트워크 성능 권장 사항 (미리 보기)](office-365-network-mac-perf-overview.md)

[Microsoft 365 network performance insights (preview)](office-365-network-mac-perf-insights.md)

[M365 관리 센터의 Microsoft 365 connectivity test (preview)](office-365-network-mac-perf-onboarding-tool.md)

[Microsoft 365 네트워크 연결 위치 서비스 (미리 보기)](office-365-network-mac-location-services.md)
