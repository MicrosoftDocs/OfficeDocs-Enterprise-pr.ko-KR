---
title: Microsoft 365 관리 센터의 네트워크 성능 권장 사항 (미리 보기)
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 02/04/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Microsoft 365 관리 센터의 네트워크 성능 권장 사항 개요 (미리 보기)
ms.openlocfilehash: d944814effc62956d5047bad1f3088d0919793ee
ms.sourcegitcommit: e2f7bb4ccd4c74902235f680104ca6b56c051587
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/19/2020
ms.locfileid: "42106397"
---
# <a name="network-performance-recommendations-in-the-microsoft-365-admin-center-preview"></a>Microsoft 365 관리 센터의 네트워크 성능 권장 사항 (미리 보기)

Microsoft 365 관리 센터의 네트워크 성능 페이지에는 기업 고객을 위한 네트워크 정보 및 네트워크 점수가 표시 됩니다. 네트워크 통찰력은 Office 365에 대 한 네트워크 연결과 관련 된 사용자 환경을 개선 하기 위해 권장 되는 네트워크 아키텍처 디자인 변경 사항 이며 네트워크 점수는 네트워크 연결이 사용자 환경에 영향을 주는 방법을 보여 줍니다. 서로 다른 사용자 위치 네트워크 연결 여러 사무실 위치 및 특수 네트워크 경계 아키텍처를 사용 하는 Office 365의 경우 office 365에 대 한 초기 온 보 딩 중에 또는 사용과 함께 검색 된 네트워크 성능 문제를 해결 하기 위해이 기능이 도움이 될 수 있습니다. 성장을. 일반적으로 Office 365을 사용 하는 소규모 기업이 나 간단 하 고 직접적인 네트워크 연결이 이미 있는 모든 기업에서는이 작업이 필요 하지 않습니다. 500 개를 초과 하는 사용자 및 여러 사무실 위치를 사용 하는 기업은 대부분 혜택을 누릴 수 있습니다.

>[!IMPORTANT]
>네트워크 성능 권장 사항, Microsoft 365 관리 센터의 통찰력 및 평가는 현재 미리 보기 상태 이며, 기능 미리 보기 프로그램에 등록 되어 있는 Office 365 테 넌 트에만 사용할 수 있습니다.

## <a name="enterprise-network-connectivity-challenges"></a>엔터프라이즈 네트워크 연결 문제

![고객 네트워크에서 클라우드로](Media/m365-mac-perf/m365-mac-perf-first-last-mile.png)

많은 기업에는 시간이 지남에 따라 증가 되는 네트워크 경계 구성이 있으며, 주로 대부분의 웹 사이트가 미리 알려지지 않고 신뢰할 수 없는 직원 인터넷 웹 사이트 액세스를 수용할 수 있도록 설계 되었습니다. Prevailing이 알 수 없는 웹 사이트에서 맬웨어 및 낚시 공격을 방지 하는 데 중점을 둔 것입니다. 보안 목적에 도움이 되는이 네트워크 구성 전략은 Office 365 사용자 성능 및 사용자 환경에 대 한 저하를 야기할 수 있습니다. 기업은 사용자 환경을 향상 시킬 수 있을 뿐만 아니라 새로운 Microsoft 365 관리 센터 네트워크 성능 기능을 사용 하 여 [Office 365 연결 원칙](https://aka.ms/pnc) 을 따라 환경을 계속 보호할 수도 있습니다. 이 기능은 Office 365 연결 원칙에 맞게 네트워크 아키텍처 디자인을 지원 하며, Office 365에 연결 하기 위해 최적화 된 네트워크 성능을 제공 합니다.

## <a name="how-we-can-solve-these-challenges"></a>이러한 문제를 해결 하는 방법

Microsoft는 대규모 엔터프라이즈 고객을 위해 Office 365의 네트워크 성능 문제를 조사 해야 하는 경우가 많으므로, 이러한 경우에는 고객 네트워크 egress 인프라와 관련 된 근본적인 원인이 있습니다. 고객 네트워크 경계 문제를 해결 하는 일반적인 근본적인 원인이 발견 되 면이를 식별 하는 단순한 테스트 측정을 확인 합니다. 특정 문제를 식별 하는 측정 임계값을 갖는 테스트는 어떤 위치에서 든 동일한 측정 단위를 테스트할 수 있으므로이 근본적인 원인이 제공 되는지 여부를 확인 하 고 관리자에 게 네트워크에 대 한 정보를 공유 하는 것이 중요 합니다. 일부 네트워크 정보는 추가 조사가 필요한 문제를 나타냅니다. 근본 원인을 해결 하기 위한 특정 수정 작업을 표시할 수 있는 충분 한 테스트를 제공 하는 네트워크 통찰력은 권장 작업으로 나열 되어 있습니다. 미리 정의 된 임계값을 초과 하는 이러한 네트워크 통찰력은 특정 모범 사례를 적용 하 고 사용자 환경이 크게 개선 되는 것을 확인할 필요가 없기 때문에 일반적인 모범 사례 권장 사항에 비해 훨씬 더 중요 한 역할을 합니다. .

## <a name="network-performance-overview-in-the-microsoft-365-admin-center"></a>Microsoft 365 관리 센터의 네트워크 성능 개요

Microsoft는 Office 365의 작업을 지 원하는 여러 Office 데스크톱 및 웹 클라이언트를 포함 하 고 있는 기존 네트워크 측정이 있습니다. 이러한 측정값은 이제 네트워크 아키텍처 디자인 정보를 제공 하는 데 사용 되며, Microsoft 365 관리 센터의 네트워크 성능 페이지에 표시 되는 네트워크 성능 점수입니다.

네트워크 측정값과 관련 된 근사 위치 정보는 클라이언트 장치가 있는 구/군/시를 식별할 수 있습니다. 이는 고객의 사무실 위치를 표시 하는 데 사용 되며 네트워크 측정값은 해당 사무실 위치에 대 한 네트워크 통찰력을 제공 하도록 그룹화 됩니다. 각 위치의 네트워크 점수가 컬러로 표시 되 고 각 위치의 상대 사용자 수가 원의 크기로 표시 됩니다. 또한 개요 페이지에는 고객의 네트워크 점수가 모든 사무실 위치에서 가중치가 매겨진 평균으로 표시 됩니다.

## <a name="specific-office-location-network-performance-summary-and-insights"></a>특정 사무실 위치 네트워크 성능 요약 및 정보

사무실 위치를 선택 하면 특정 위치에 대 한 요약 페이지가 열립니다. 여기서는 해당 사무실 위치에 대해 측정값 으로부터 식별 된 네트워크 egress에 대 한 세부 정보를 표시 합니다.

Office 위치 요약 페이지에는 또한 네트워크 점수, 네트워크 점수 기록,이 위치 점수를 같은 도시의 다른 고객에 대 한 비교, 고객이 선택할 수 있는 특정 한 의견 및 권장 사항 목록이 표시 됩니다. 네트워크 연결을 개선 합니다. 같은 도시에 있는 고객 간의 비교는 모든 고객이 네트워크 서비스 공급자, 통신 인프라 및 주변의 Microsoft 네트워크 상태에 대 한 액세스를 동일 하 게 한다는 기대를 기반으로 합니다.

Office 위치 페이지의 세부 정보 탭에는 모든 정보, 추천 사항 및 네트워크 점수를 제공 하는 데 사용 된 구체적인 측정 결과가 표시 됩니다. 이는 네트워크 엔지니어가 환경에 있는 제한이 나 구체적인 사항을 고려 하 여 권장 사항 및 요인을 확인할 수 있도록 하기 위해 제공 됩니다.
제공 되는 office 위치 및 권장 사항의 정확성을 향상 시키려는 고객의 경우 더 구체적인 정보를 입력할 수 있습니다. 이 작업은 검색 된 위치 정보를 편집 하 여 수행 되며 네트워크 측정에 사용할 수 있는 위치 정보에 내재 된 따라 근사값을 줄일 수 있습니다.

## <a name="faq"></a>FAQ

### <a name="what-is-office-365-service-front-door"></a>Office 365 서비스 전면 도어 란?

Office 365 서비스 전면 도어는 Microsoft의 글로벌 네트워크에서 Office 클라이언트 및 서비스가 네트워크 연결을 종료 하는 진입점입니다. Office 365에 대 한 최적의 네트워크 연결을 위해 네트워크 연결이 도시나 메트로 가장 가까운 Office 365 전면 도어로 종료 되는 것이 좋습니다.
참고: Office 365 서비스 전면 도어는 Azure marketplace에서 사용할 수 있는 "Azure 전면 도어 서비스" 제품과 직접 관계가 없습니다.

### <a name="what-is-an-optimal-office-365-service-front-door"></a>최적의 Office 365 서비스 전면 도어 란 무엇입니까?

최적의 Office 365 서비스 전면 도어는 일반적으로 구/군/시 또는 지하철 지역에 있는 네트워크 egress에 가장 가까운 곳입니다. Office 365 네트워크 성능 도구를 사용 하 여 사용 중인 Office 365 서비스 전면 도어 및 최적의 서비스 전면 도어 위치를 확인 합니다. 사용 중인 전면 문이 최적 상태 이면 도구에서 Microsoft의 글로벌 네트워크에 최적 상태로 연결 하는 것입니다.

### <a name="what-is-an-internet-egress-location"></a>인터넷 송신 위치 란?

인터넷 송신 위치는 네트워크 트래픽이 기업 네트워크를 종료 하 고 인터넷에 연결 하는 위치입니다. 또한 NAT (Network Address Translation) 장치가 있는 위치로도 식별 되며, 대개 ISP (인터넷 서비스 공급자)와 연결 됩니다. 위치와 인터넷 송신 위치 사이에 긴 거리가 표시 되 면이로 인해 상당한 WAN 백을 확인할 수 있습니다.

## <a name="related-topics"></a>관련 항목

[Office 365 network performance insights (미리 보기)](office-365-network-mac-perf-insights.md)

[Office 365 네트워크 평가 (미리 보기)](office-365-network-mac-perf-score.md)

[M365 관리 센터의 Office 365 네트워크 온 보 딩 도구 (미리 보기)](office-365-network-mac-perf-onboarding-tool.md)
