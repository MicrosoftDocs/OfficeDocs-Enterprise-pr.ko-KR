---
title: Microsoft 365 관리 센터의 네트워크 성능 권장 사항 (미리 보기)
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
description: Microsoft 365 관리 센터의 네트워크 성능 권장 사항 개요 (미리 보기)
ms.openlocfilehash: 9bd1470b80d0c65c11748bee3e8a6a73a218f55f
ms.sourcegitcommit: 6508db0a839427e1a21b1cde883d828e3c8886c6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "43185779"
---
# <a name="network-performance-recommendations-in-the-microsoft-365-admin-center-preview"></a>Microsoft 365 관리 센터의 네트워크 성능 권장 사항 (미리 보기)

Microsoft 365 관리 센터에는 이제 Microsoft 365 테 넌 트에서 수집 된 라이브 성능 메트릭이 포함 되며, 테 넌 트의 관리 사용자만 볼 수 있습니다. **네트워크 insights 및 성능 권장 사항** 및 **네트워크 평가가** Microsoft 365 관리 센터 ()에 표시 <https://portal.microsoft.com/adminportal/home#/networkperformance>됩니다. 탐색 창의 상태 |에 페이지를 찾을 수 있습니다. ** 네트워크 성능**

![네트워크 성능 페이지](Media/m365-mac-perf/m365-mac-perf-page-nav.png)

먼저 네트워크 성능 페이지로 이동 하면 전역 네트워크 성능 맵과 전체 테 넌 트로 범위가 지정 된 네트워크 평가가 포함 된 개요 창 및 현재 문제 목록이 표시 됩니다. 이 개요에서는 드릴 다운을 통해 위치로 특정 네트워크 성능 메트릭 및 문제를 볼 수 있습니다. 자세한 내용은 [Microsoft 365 관리 센터의 네트워크 성능 개요](#network-performance-overview-in-the-microsoft-365-admin-center)를 참조 하세요.

## <a name="pre-requisites-for-connectivity-measurements-to-appear"></a>연결 측정을 위한 필수 구성 요소

연결 측정이 표시 되도록 하려면 사전 필수 구성 요소를 지 원하는 각 사무실 위치에서 실행 되는 컴퓨터가 두 대 이상 있어야 합니다. OneDrive for Business 동기화 클라이언트 버전 19.232 이상이 각 컴퓨터에 설치 되어 있어야 합니다. 자세한 내용은 [OneDrive 릴리스 노트](https://support.office.com/article/onedrive-release-notes-845dcf18-f921-435e-bf28-4e24b95e5fc0)를 참조 하세요.

Windows 위치 서비스는 컴퓨터에서 consented 해야 합니다. **지도** 앱을 실행 하 고 자신을 찾아 테스트할 수 있습니다. "앱에서 위치 액세스 허용" 설정을 사용 **하도록 설정 하** -> 여**개인 정보 보호** -> **위치가** 있는 단일 컴퓨터에서이 기능을 사용 하도록 설정할 수 있습니다. Windows 위치 서비스 동의 _를 설정 하는 경우에_는 MDM 또는 그룹 정책을 사용 하 여 pc에 배포할 수 있습니다.

컴퓨터에는 이더넷 케이블이 아닌 Wi-fi 네트워킹이 있어야 합니다. 이더넷 케이블을 사용 하는 컴퓨터는 정확한 위치 정보를 포함 하지 않습니다.

측정 및 사무실 위치는 이러한 필수 구성 요소가 충족 된 후 24 시간 전에 표시 되어야 합니다.

## <a name="how-do-i-use-this-information"></a>이 정보를 어떻게 사용 하나요?

**네트워크 insights**와 관련 된 성능 권장 사항 및 네트워크 평가는 사무실 사무소에 대 한 네트워크 perimeters 디자인에 도움을 주기 위한 것입니다. 각 통찰력은 사용자가 테 넌 트에 액세스 하는 각 지리적 위치에 대 한 특정 일반적인 문제의 성능 특성에 대 한 실시간 세부 정보를 제공 합니다. 각 네트워크 통찰력에 대 한 **성능 권장 사항은** Microsoft 365 네트워크 연결과 관련 된 사용자 환경을 개선 하기 위해 구체적인 네트워크 아키텍처 디자인 변경 사항을 제공 합니다. 네트워크 평가에서는 네트워크 연결이 사용자 환경에 미치는 영향을 보여 주므로 서로 다른 사용자 위치 네트워크 연결을 비교할 수 있습니다.

**네트워크 평가** 에서는 많은 네트워크 성능 메트릭 집계를 1-100의 포인트 값으로 표시 되는 엔터프라이즈 네트워크 상태의 스냅숏으로 정제 합니다. 네트워크 평가는 전체 테 넌 트와 사용자가 테 넌 트에 연결 하는 각 지리적 위치에 대해 범위가 지정 되므로 Microsoft 365 관리자는 회사의 네트워크 상태를 신속 하 게 파악 하 고 전체 사무실 위치에 대 한 자세한 보고서로 드릴 다운할 수 있는 쉬운 방법을 제공 합니다.

여러 사무실 위치 및 특수 네트워크 경계 아키텍처가 포함 된 복잡 한 기업에서는 Microsoft 365에 대 한 초기 온 보 딩 중에이 정보를 활용 하거나 사용 성장률에 따라 검색 된 네트워크 성능 문제를 해결 하는 데 도움이 될 수 있습니다. Microsoft 365를 사용 하는 소규모 기업이 나 이미 간단한 네트워크 연결이 있는 기업에서는 일반적으로이 작업이 필요 하지 않습니다. 500 개를 초과 하는 사용자 및 여러 사무실 위치를 사용 하는 기업은 대부분 혜택을 누릴 수 있습니다.

>[!IMPORTANT]
>네트워크 insights, Microsoft 365 관리 센터의 성능 권장 사항 및 평가는 현재 미리 보기 상태 이며, 기능 미리 보기 프로그램에 등록 되어 있는 Microsoft 365 테 넌 트에만 사용할 수 있습니다.

## <a name="enterprise-network-connectivity-challenges"></a>엔터프라이즈 네트워크 연결 문제

![고객 네트워크에서 클라우드로](Media/m365-mac-perf/m365-mac-perf-first-last-mile.png)

많은 기업에는 시간이 지남에 따라 증가 되는 네트워크 경계 구성이 있으며, 주로 대부분의 웹 사이트가 미리 알려지지 않고 신뢰할 수 없는 직원 인터넷 웹 사이트 액세스를 수용할 수 있도록 설계 되었습니다. Prevailing이 알 수 없는 웹 사이트에서 맬웨어 및 낚시 공격을 방지 하는 데 중점을 둔 것입니다. 보안 목적에 도움이 되는이 네트워크 구성 전략은 Microsoft 365 사용자 성능 및 사용자 경험을 저하 시킬 수 있습니다.

## <a name="how-we-can-solve-these-challenges"></a>이러한 문제를 해결 하는 방법

기업에서는 [Office 365 연결 원리](https://aka.ms/pnc) 와 Microsoft 365 관리 센터 네트워크 성능 기능을 사용 하 여 일반적인 사용자 환경을 개선 하 고 환경을 보호할 수 있습니다. 대부분의 경우 이러한 일반 원칙에 따라 최종 사용자 대기 시간, 서비스 안정성 및 Microsoft 365의 전반적인 성능에 큰 영향을 미칩니다.

Microsoft는 대규모 엔터프라이즈 고객을 위해 Microsoft 365의 네트워크 성능 문제를 조사 해야 하는 경우가 많으므로, 이러한 경우에는 고객 네트워크 송신 인프라와 관련 된 근본적인 원인이 있습니다. 고객 네트워크 경계 문제를 해결 하는 일반적인 근본적인 원인이 발견 되 면이를 식별 하는 단순한 테스트 측정을 확인 합니다. 특정 문제를 식별 하는 측정 임계값을 갖는 테스트는 어떤 위치에서 든 동일한 측정 단위를 테스트할 수 있으므로이 근본적인 원인이 제공 되는지 여부를 확인 하 고 관리자에 게 네트워크에 대 한 정보를 공유 하는 것이 중요 합니다.

일부 네트워크 정보는 추가 조사가 필요한 문제를 나타냅니다. 근본 원인을 해결 하기 위한 특정 수정 작업을 표시할 수 있는 충분 한 테스트를 제공 하는 네트워크 통찰력은 **권장 작업**으로 나열 되어 있습니다. 미리 정의 된 임계값을 벗어나는 값을 표시 하는 라이브 메트릭에 기반을 둔 이러한 권장 사항은 환경에 따라 달라 지 며, 권장 사항이 변경 되 면 실제 개선 사항을 표시 하기 때문에 일반적인 모범 사례 권장 사항에 비해 훨씬 더 귀중 한 방법입니다.

## <a name="network-performance-overview-in-the-microsoft-365-admin-center"></a>Microsoft 365 관리 센터의 네트워크 성능 개요

Microsoft에는 Microsoft 365의 작업을 지 원하는 여러 Office 데스크톱 및 웹 클라이언트의 기존 네트워크 측정값이 포함 되어 있습니다. 이러한 측정값은 이제 네트워크 아키텍처 디자인 정보를 제공 하 고 Microsoft 365 관리 센터의 **네트워크 성능** 페이지에 표시 되는 네트워크 성능 평가를 수행 하는 데 사용 됩니다.

기본적으로 네트워크 측정값과 연결 된 근사 위치 정보는 클라이언트 장치가 있는 구/군/시를 식별 합니다. 각 위치에서의 네트워크 평가가 색으로 표시 되며 각 위치의 상대 사용자 수는 원의 크기로 표시 됩니다.

![네트워크 insights 개요 맵](Media/m365-mac-perf/m365-mac-perf-overview-map.png)

또한 개요 페이지에는 고객에 대 한 네트워크 평가가 모든 사무실 위치에서 가중치가 매겨진 평균으로 표시 됩니다.

![네트워크 평가](Media/m365-mac-perf/m365-mac-perf-overview-score.png)

## <a name="specific-office-location-network-performance-summary-and-insights"></a>특정 사무실 위치 네트워크 성능 요약 및 정보

사무실 위치를 선택 하면 해당 사무실 위치에 대해 측정 된 네트워크 egress에 대 한 세부 정보가 표시 되는 위치 관련 요약 페이지가 열립니다.

![위치인 네트워크 insights 세부 정보](Media/m365-mac-perf/m365-mac-perf-locations-plan-overview.png)

또한 office 위치 요약 페이지에는 위치의 네트워크 평가, 네트워크 평가 기록, 같은 도시의 다른 고객에 대 한이 위치 평가의 비교 및 네트워크 성능 및 안정성을 개선 하기 위해 수행할 수 있는 구체적인 정보 및 권장 사항 목록이 표시 됩니다. 특정 권장 사항이 있는 위치에는 예상 대기 시간 개선도 포함 될 수 있습니다.

같은 도시에 있는 고객 간의 비교는 모든 고객이 네트워크 서비스 공급자, 통신 인프라 및 주변의 Microsoft 네트워크 상태에 대 한 액세스를 동일 하 게 한다는 기대를 기반으로 합니다.

![네트워크 insights 위치](Media/m365-mac-perf/m365-mac-perf-locations.png)

Office 위치 페이지의 세부 정보 탭에는 모든 정보, 추천 사항 및 네트워크 평가에 사용 된 구체적인 측정 결과가 표시 됩니다. 이는 네트워크 엔지니어가 환경에 있는 제한이 나 구체적인 사항을 고려 하 여 권장 사항 및 요인을 확인할 수 있도록 하기 위해 제공 됩니다.

![위치 관련 세부 정보](Media/m365-mac-perf/m365-mac-perf-locations-plan-details-all.png)

위치 관련 메트릭 및 권장 사항의 정확성을 향상 시키려는 고객의 경우 더 구체적인 정보를 입력 하는 데 사용할 수 있습니다. 이렇게 하면 네트워크 측정에 사용할 수 있는 위치 정보에 내재 된 따라 근사값을 줄일 수 있습니다. 특정 사무실 위치의 주소를 편집 하려면 <functionality not there yet>.

## <a name="import-undiscovered-office-locations"></a>발견 하지 않은 office 위치 가져오기

네트워크 성능 **위치** 탭에는 네트워크 원격 분석에서 자동으로 검색 되는 office 위치 목록이 표시 됩니다. 이러한 사무실 위치는 검색 된 도시입니다. 이러한 도시를 CSV 파일에서 가져와서 목록에 자동으로 표시 하지 않는 경우 해당 도시의 범위 내에서 해당 위치를 수동으로 추가할 수 있습니다. Office 위치가 전혀 표시 되지 않으면 여기에 위치만 추가 하는 것이 아니라 네트워크 측정이 나타나지 않는 이유를 해결 해야 합니다. 기존 사무실 위치의 주소 값도 업데이트할 수 있습니다.

CSV 파일 aA에서 검색 된 도시 위치는 **구/군/시**로 레이블이 지정 되 고 수동으로 추가 된 사무실 위치는 **location**입니다.

1. _Microsoft 365에 대 한 기본 연결_ 창에서 **위치** 탭을 클릭 합니다.
1. 위치 목록 바로 위에 있는 **가져오기** 단추를 클릭 합니다. **가져오기 office 위치** 플라이 아웃이 표시 됩니다.

   ![CSV 가져오기 오류 메시지](Media/m365-mac-perf/m365-mac-perf-import.png)

1. 현재 위치 목록을 CSV 파일로 내보낸 다음 로컬 하드 디스크에 저장 하려면 **최신 office 위치 (.csv) 링크 다운로드** 를 클릭 합니다. 이렇게 하면 위치를 추가할 수 있는 올바른 형식의 CSV가 제공 됩니다. 내보낸 위치를 그대로 둘 수 있습니다. 업데이트 된 CSV를 가져올 때도 해당 사용자가 복제 되지 않습니다. 기존 위치의 주소를 변경 하려면 CSV를 가져올 때 업데이트 됩니다. 검색 된 도시의 주소는 변경할 수 없습니다.
1. CSV를 열고 추가 하려는 각 위치에 대해 새 줄에서 다음 필드를 채워 위치를 추가 합니다. 다른 모든 필드는 비워 둡니다. 다른 필드에 입력 한 값은 무시 됩니다.
   1. **주소** (필수): office의 실제 주소
   1. **Latitude** (선택 사항): Bing 지도 조회가 비어 있는 경우 해당 조회에서 채워짐
   1. **경도** (선택 사항): Bing 지도 조회가 비어 있는 경우 해당 조회에서 채워짐
   1. **EGRESS IP 주소 범위 1-5** (선택 사항): 각 범위에 대해 회로 이름 다음에 유효한 IPv4 또는 IPv6 CIDR 주소의 공백으로 구분 된 목록을 입력 합니다. 이러한 값은 지정 된 사무실 위치에 대해 SDWAN 통합을 사용 하도록 설정한 경우에만 사용 됩니다.
1. Office 위치를 추가 하 고 파일을 저장 한 후에 **는 완료 됨 필드 업로드** 옆에 있는 **찾아보기** 단추를 클릭 하 고 저장 된 CSV 파일을 선택 합니다.
1. 파일 유효성 검사가 자동으로 수행 됩니다. 유효성 검사 오류가 있으면 가져오기 파일에 오류가 있는 것입니다. 라는 오류 메시지가 표시 됩니다 _. 오류를 검토 하 고 가져올 파일을 수정한 다음 다시 시도 하십시오._ 특정 필드 유효성 검사 오류 목록에 대 한 **열기 오류 정보** 링크를 클릭 합니다.

   ![CSV 가져오기 오류 메시지](Media/m365-mac-perf/m365-mac-perf-import-error.png)

1. 파일에 오류가 없으면 _보고서가 준비 되었다는 메시지가 표시 됩니다. 추가할 x 위치 및 x 위치를 업데이트할 수 있습니다._ **가져오기** 단추를 클릭 하 여 CSV를 업로드 합니다.

   ![CSV 가져오기 준비 메시지](Media/m365-mac-perf/m365-mac-perf-import-ready.png)

## <a name="faq"></a>FAQ

### <a name="what-is-a-microsoft-365-service-front-door"></a>Microsoft 365 서비스 전면 도어 란?

Microsoft 365 서비스 전면 도어는 Microsoft의 글로벌 네트워크에서 Office 클라이언트 및 서비스가 네트워크 연결을 종료 하는 진입점입니다. Microsoft 365에 대 한 최적의 네트워크 연결을 위해 네트워크 연결이 도시나 메트로 가장 가까운 Microsoft 365 전면 도어로 종료 되는 것이 좋습니다.

>[!NOTE]
>Microsoft 365 서비스 전면 도어는 Azure marketplace에서 사용 가능한 Azure direct 도어 서비스 제품과 직접 관계가 없습니다.

### <a name="what-is-an-optimal-microsoft-365-service-front-door"></a>최적의 Microsoft 365 서비스 전면 도어 란 무엇입니까?

최적의 Microsoft 365 서비스 전면 도어는 일반적으로 구/군/시 또는 메트로 지역에 있는 네트워크 egress에 가장 가까운 곳입니다. [Microsoft 365 네트워크 온 보 딩 도구](office-365-network-mac-perf-onboarding-tool.md) 를 사용 하 여 사용 중인 microsoft 365 서비스 전면 도어 및 최적의 서비스 전면 도어 위치를 확인 합니다. 사용 중인 전면 문이 최적 상태 이면 도구에서 Microsoft의 글로벌 네트워크에 최적 상태로 연결 하는 것입니다.

### <a name="what-is-an-internet-egress-location"></a>인터넷 송신 위치 란?

인터넷 송신 위치는 네트워크 트래픽이 기업 네트워크를 종료 하 고 인터넷에 연결 하는 위치입니다. 또한 NAT (Network Address Translation) 장치가 있는 위치로도 식별 되며, 대개 ISP (인터넷 서비스 공급자)와 연결 됩니다. 위치와 인터넷 송신 위치 사이에 긴 거리가 표시 되 면이는 상당한 WAN 백을 나타낼 수 있습니다.

## <a name="related-topics"></a>관련 항목

[Microsoft 365 Network insights (미리 보기)](office-365-network-mac-perf-insights.md)

[Microsoft 365 네트워크 평가 (미리 보기)](office-365-network-mac-perf-score.md)

[M365 관리 센터의 Microsoft 365 네트워크 온 보 딩 도구 (미리 보기)](office-365-network-mac-perf-onboarding-tool.md)

[Microsoft 365 네트워크 연결 위치 서비스 (미리 보기)](office-365-network-mac-location-services.md)
