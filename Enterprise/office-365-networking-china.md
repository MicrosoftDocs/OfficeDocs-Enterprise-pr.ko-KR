---
title: 중국 사용자에 대 한 Microsoft 365 전역 테 넌 트 성능 최적화
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/23/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- remotework
search.appverid: MET150
f1.keywords:
- NOCSH
description: 이 문서에서는 글로벌 Microsoft 365 테 넌 트의 중국 사용자에 대 한 네트워크 성능을 최적화 하기 위한 지침을 제공 합니다.
ms.openlocfilehash: e5d74bdae23545c1e7c65fae44010a8c5a3829e3
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "44997808"
---
# <a name="microsoft-365-global-tenant-performance-optimization-for-china-users"></a>중국 사용자에 대 한 Microsoft 365 전역 테 넌 트 성능 최적화

>[!IMPORTANT]
>이 지침은 **중국에 위치한 엔터프라이즈 microsoft 365 사용자가** **글로벌 microsoft 365 테 넌 트**에 연결 하는 사용 시나리오에만 해당 됩니다. 이 지침은 21Vianet에서 운영 하는 Office 365의 테 넌 트에는 적용 **되지** 않습니다.

중국에 글로벌 Microsoft 365 테 넌 트 및 회사 현재 상태인 기업에 대 한 Microsoft 365 클라이언트 성능은 중국 Telco의 인터넷 아키텍처에 고유한 요인에 따라 복잡할 수 있습니다.

중국 Isp는 전체적인 경계 네트워크 혼잡에 취약 한 경계 장치를 통과 하는 글로벌 공용 인터넷에 대 한 offshore 연결을 규정 합니다. 이 혼잡은 중국 들어오고 나가는 모든 인터넷 트래픽에 대 한 패킷 손실 및 대기 시간을 만듭니다.

![Microsoft 365 트래픽 최적화 되지 않음](media/O365-networking/China-O365-unoptimized.png)

패킷 손실 및 대기 시간은 네트워크 서비스 (특히 대용량 파일 전송)가 필요 하거나 실시간 고성능 (오디오 및 비디오 응용 프로그램)을 필요로 하는 대규모 데이터 교환이 필요한 서비스의 성능에 부정적인 영향을 주는 일입니다.

이 항목의 목표는 Microsoft 365 서비스에서 중국 테두리 간 네트워크 혼잡의 영향을 완화 하기 위한 모범 사례를 제공 하는 데 사용 됩니다. 이 항목에서는 중국 캐리어 내의 복잡 한 라우팅으로 인 한 높은 패킷 대기 시간 문제와 같은 다른 일반적인 지난 마일 성능 문제를 해결 하지 않습니다.

## <a name="corporate-network-best-practices"></a>회사 네트워크 모범 사례

글로벌 Microsoft 365 테 넌 트 및 중국의 사용자가 포함 된 대부분의 기업에서는 중국 사무실 위치와 전 세계 offshore 위치 간에 회사 네트워크 트래픽을 전송 하는 개인 네트워크를 구현 했습니다. 이러한 기업은 이러한 네트워크 인프라를 활용 하 여 경계 간 네트워크 혼잡을 방지 하 고 중국에서 Microsoft 365 서비스 성능을 최적화할 수 있습니다.

>[!IMPORTANT]
>모든 사설 WAN 구현과 마찬가지로, 사용자의 국가 및/또는 지역에 대 한 규정 요구 사항을 항상 확인 하 여 네트워크 구성이 준수 되도록 해야 합니다.

첫 번째 단계로, [Microsoft 365의 네트워크 계획 및 성능 조정](https://aka.ms/tune)에서 벤치 마크 네트워크 지침을 따르는 것이 중요 합니다. 기본 목표는 가능한 경우 중국의 인터넷에서 글로벌 Microsoft 365 서비스에 액세스 하지 않도록 하기 위한 것입니다.

- 기존 개인 네트워크를 활용 하 여 중국 사무실 네트워크와 중국 외부의 공용 인터넷에서 전송 되는 offshore 위치 간의 Microsoft 365 네트워크 트래픽을 이동 합니다. 중국 외부에 있는 거의 모든 위치에서 분명 한 이점이 제공 됩니다. 네트워크 관리자는 [Microsoft 글로벌 네트워크](https://docs.microsoft.com/azure/networking/microsoft-global-network)와의 대기 시간이 낮은 상호 연결을 사용 하는 영역에서 더 최적화할 수 있습니다. 예를 들어, 홍콩, 일본, 대한민국을 사용할 수 있습니다.
- Microsoft 365 트래픽이 회사 네트워크의 개인 offshore 링크를 통과 하도록 허용 하기 위해 VPN 연결을 통해 회사 네트워크에 액세스 하도록 사용자 장치를 구성 합니다. VPN 클라이언트가 분할 터널링을 사용 하도록 구성 되지 않았는지 또는 사용자 장치가 Microsoft 365 트래픽에 대 한 분할 터널링을 무시 하도록 구성 되어 있는지 확인 합니다.
- 개인 offshore 링크를 통해 모든 Microsoft 365 트래픽을 라우팅하도록 네트워크를 구성 합니다. 개인 링크에 대 한 트래픽 양을 최소화 해야 하는 경우에는 **최적화** 범주에서 끝점만 경로를 설정 하 고 요청을 **허용** **하 고 끝점에서** 인터넷을 전송할 수 있도록 허용 하도록 선택할 수 있습니다. 이렇게 하면 높은 대기 시간 및 패킷 손실을 가장 많이 받는 중요 한 서비스에 최적화 된 트래픽을 제한 하 여 성능을 개선 하 고 대역폭 소비를 최소화할 수 있습니다.
- 가능한 경우 TCP 대신, 라이브 미디어 스트리밍 트래픽 (예: 팀)에 대해 UDP를 사용 합니다. UDP는 TCP 보다 더 나은 라이브 미디어 스트리밍 성능을 제공 합니다.

Microsoft 365 트래픽을 선택적으로 라우팅하는 방법에 대 한 자세한 내용은 [Office 365 끝점 관리](managing-office-365-endpoints.md)를 참조 하세요. 모든 국가별 Office 365 Url 및 IP 주소 목록은 [Office 365 url 및 ip 주소 범위](urls-and-ip-address-ranges.md)를 참조 하세요.

![Microsoft 365 트래픽 최적화](media/O365-networking/China-O365-optimized.png)

## <a name="user-best-practices"></a>사용자 모범 사례

집, 커피숍, 호텔 및 기업 네트워크에 연결 되지 않은 지사나 같은 원격 위치에서 글로벌 Microsoft 365 테 넌 트에 연결 하는 중국의 사용자는 자신의 장치와 Microsoft 365 간의 트래픽이 중국의 혼잡 한 경계 네트워크 회로를 통과 해야 하므로 네트워크 성능이 저하 될 수 있습니다.

회사 네트워크에 대 한 경계 간 개인 네트워크 및/또는 VPN 액세스가 옵션이 아닌 경우에는 이러한 모범 사례를 따르기 위해 중국 기반 사용자에 게 교육 하 여 사용자별 성능 문제를 완화할 수 있습니다.

- 캐싱을 지 원하는 리치 Office 클라이언트 (예: Outlook, 팀, OneDrive 등)를 활용 하 고 웹 기반 클라이언트를 사용 하지 않습니다. Office 클라이언트 캐싱 및 오프 라인 액세스 기능을 사용 하면 네트워크 혼잡 및 대기 시간에 대 한 영향을 크게 줄일 수 있습니다.
- _오디오 회의_ 기능을 사용 하 여 Microsoft 365 테 넌 트를 구성한 경우 팀 사용자는 PSTN (공중 전화망)을 통해 모임에 참가할 수 있습니다. 자세한 내용은 [Office 365의 오디오 회의](https://docs.microsoft.com/microsoftteams/audio-conferencing-in-office-365)를 참조 하세요.
- 사용자에 게 네트워크 성능 문제가 발생 하면 Microsoft 365 서비스에 문제가 있는 것으로 의심 되는 문제 해결을 위해 IT 부서에 보고 하 고 Microsoft의 지원을 제공 해야 합니다. 일부 문제가 교차 테두리 네트워크 성능으로 인해 발생 하는 것은 아닙니다.

Microsoft는 광범위 한 네트워크 아키텍처 및 특성 범위에서 Microsoft 365 사용자 환경 및 클라이언트 성능 개선을 위한 지속적인 작업을 수행 하 고 있습니다. [Office 365 기술 커뮤니티](https://techcommunity.microsoft.com/t5/office-365/bd-p/Office365General) 를 방문 하 여 대화를 시작 하거나 참여 하 고, 리소스를 찾고, 기능 요청 및 제안을 제출 합니다.

## <a name="related-topics"></a>관련 항목

[Microsoft 365의 네트워크 계획 및 성능 조정](https://aka.ms/tune)

[Microsoft 365 네트워크 연결 원칙](office-365-network-connectivity-principles.md)

[Office 365 끝점 관리](managing-office-365-endpoints.md)

[Office 365 URL 및 IP 주소 범위](urls-and-ip-address-ranges.md)

[Microsoft 글로벌 네트워크](https://docs.microsoft.com/azure/networking/microsoft-global-network)
