---
title: ExpressRoute BGP 커뮤니티를 사용 하 여 Office 365 시나리오에 대 한
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/26/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099
description: 'Office 365에 연결 Azure ExpressRoute를 사용 하 여 기반으로 Office 365 끝점이 배포 된 네트워크를 표시 하는 특정 IP 서브넷의 BGP 광고 합니다. 고객은 전역의 특성으로 인해 Office 365 및 Office 365를 구성 하는 서비스의 수, 해당 네트워크에 모임 참가자가 수락 광고를 관리 하 해야 하는 경우가 많습니다. IP 서브넷;의 수 줄이기 라고 고객을 위한 최종 목표는 다음과 같은 역할 BGP 네트워크 관리 용어에 맞춰이 문서의 나머지 부분에서는 전체 IP 접두사:'
ms.openlocfilehash: c6e40dc29df55aa87e8d40c6203100fa1e7ad38f
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541932"
---
# <a name="using-bgp-communities-in-expressroute-for-office-365-scenarios"></a>ExpressRoute BGP 커뮤니티를 사용 하 여 Office 365 시나리오에 대 한

Office 365에 연결 Azure ExpressRoute를 사용 하 여 기반으로 Office 365 끝점이 배포 된 네트워크를 표시 하는 특정 IP 서브넷의 BGP 광고 합니다. 고객은 전역의 특성으로 인해 Office 365 및 Office 365를 구성 하는 서비스의 수, 해당 네트워크에 모임 참가자가 수락 광고를 관리 하 해야 하는 경우가 많습니다. IP 서브넷;의 수 줄이기 라고 고객을 위한 최종 목표는 다음과 같은 역할 BGP 네트워크 관리 용어에 맞춰이 문서의 나머지 부분에서는 전체 IP 접두사:
  
- **수락 번호 보급된 IP 접두사 관리** -고객에 게 하는 내부 네트워크 인프라 또는 제한 된 수의 IP 접두사를 지 원하는 네트워크 통신사업자 및 접두사를 수락 하는 것에 대 한 해당 요금 네트워크 통신사업자에 있는 고객 제한 된 수를 자신의 네트워크에 이미 보급 한 접두사의 총 수를 계산할 위와 ExpressRoute에 가장 적합 한 된 Office 365 응용 프로그램을 선택 합니다.

- **Azure ExpressRoute 회로에 필요한 대역폭 관리** -고객 인터넷 경로 비교 ExpressRoute 경로 통해 Office 365 서비스의 대역폭 봉투를 제어할 수도 있습니다. 이렇게 하면 고객 비즈니스를 위한 Skype 등의 특정 응용 프로그램에 대 한 ExpressRoute 대역폭을 예약 하 고 나머지 Office 365 응용 프로그램의 인터넷 경로 통해 라우팅할 수 있습니다.

이러한 목표와 고객을 위해 ExpressRoute를 통해 보급 되는 Office 365 IP 접두사 아래 예제와 같이 서비스 특정 BGP 커뮤니티 값을 가진 태그가 지정 됩니다.
  
> [!NOTE]
> 커뮤니티 값에 포함할 다른 응용 프로그램과 연결 된 일부 네트워크 트래픽이 예상할 수 있습니다. 이 목록은 공유 서비스 및 데이터 센터를 제공 하는 서비스 글로벌 소프트웨어에 대 한 예상 되는 동작입니다. 이 접두사 count 및/또는 염두에 대역폭을 관리 하는 위의 두 목표는 사용 가능한 경우 최소화 된 합니다.

|**서비스**|**BGP 커뮤니티 값**|**참고**|
|:-----|:-----|:-----|
|exchange\*  <br/> |12076:5010  <br/> |Exchange와 EOP 서비스를 포함합니다.\*  <br/> |
|sharepoint\*  <br/> |12076:5020  <br/> |SharePoint Online  <br/> |
|비즈니스를 위한 skype\*  <br/> |12076:5030  <br/> |비즈니스용 Skype Online  <br/> |
|다른 Office 365 서비스\*  <br/> |12076:5100  <br/> |Office 365 포털 서비스와 Azure Active Directory (인증 및 디렉터리 동기화 시나리오)를 포함합니다.  <br/> |
|\*ExpressRoute에 포함 된 서비스 시나리오의 범위는 [Office 365 끝점](https://aka.ms/o365endpoints) 문서에서 설명 됩니다.  <br/> \*\*추가 서비스 및 BGP 커뮤니티 값 나중에 추가 될 수 있습니다. [BGP 커뮤니티의 현재 목록을 참조 하십시오](https://azure.microsoft.com/documentation/articles/expressroute-routing/).<br/> |

## <a name="what-are-the-most-common-scenarios-for-using-bgp-communities"></a>BGP 커뮤니티를 사용 하는 가장 일반적인 시나리오는 무엇입니까?

고객은 Azure ExpressRoute, 따라서 총 IP 접두사 수 및 특정 Office 365 서비스의 예상된 대역폭 봉투 영향을 주는 통해 자신의 네트워크에서 허용 되는 IP 접두사 그룹 규제 BGP 커뮤니티를 사용할 수 있습니다. 것은 인터넷 바운드 트래픽은 Azure ExpressRoute 또는 BGP 커뮤니티의 사용에 관계 없이 모든 Office 365는 필요를 이해 하는 것이 중요 합니다. 다음 세 시나리오는이 기능을 사용 하는 가장 일반적인 합니다.
  
### <a name="scenario-1-minimizing-the-number-of-office-365-ip-prefixes"></a>시나리오 1: Office 365 IP 접두사의 수를 최소화합니다.

Contoso Corporation는 50, 000 개인 회사 현재 Office 365를 사용 하 여 Exchange Online 및 SharePoint Online에 대 한입니다. ExpressRoute 검토에서 Contoso 여러 지역 위치에 해당 네트워크 장치를 결정 하는 요구 사항을 100 추가 경로 항목 위에 라우팅 테이블 크기를 처리할 수 없습니다. Contoso는 ExpressRoute는 Office 365 서비스의 전체 집합에 대해 알리고 100을 초과 하면를 기록 하는 IP 접두사의 총 수를 검토 합니다. 100 추가 경로 항목 아래에서 상태를 유지 하려면 Contoso 범위로 지정 방금 SharePoint Online BGP 커뮤니티는 값으로 12076:5020, ExpressRoute Microsoft 피어 링을 통해 받은 Office 365에 대 한 ExpressRoute 사용 합니다.

|**BGP 커뮤니티 태그 사용**|**Azure ExpressRoute를 통해 라우팅할 수 있는 기능**|**필요한 인터넷 경로**|
|:-----|:-----|:-----|
|SharePoint  <br/> (12076:5020)  <br/> |SharePoint Online &amp; 비즈니스용 OneDrive  <br/> | DNS, CRL, &amp; CDN 요청  <br/>  Azure ExpressRoute을 통해 지원 되지않는 다른 모든 Office 365 서비스  <br/>  다른 모든 Microsoft 클라우드 서비스  <br/>  Office 365 포털, Office 365 인증 &amp; Office Online  <br/>  Exchange Online, Exchange Online 보호 및 Skype 비즈니스에 대 한 온라인  <br/> |

> [!NOTE]
> 각 서비스에 대 한 더 낮은 접두사 개수를 달성 하기 위해 최소한의 사용 서비스 간의 겹치는 기간 지속 됩니다. 예상 되는 동작입니다.
  
### <a name="scenario-2-scoping-expressroute-and-internal-bandwidth-use-to-some-office-365-services"></a>시나리오 2: 범위 지정 ExpressRoute와 내부 대역폭 사용 하 여 일부 Office 365 서비스

Fabrikam Inc, 분산된 다른 유형의 네트워크와 다국적 대기업이;을 포함 하 여 대부분의 Office 365 서비스의 구독자 Exchange Online, SharePoint Online, 및 온라인 비즈니스에 대 한 Skype 합니다. 내부 라우팅 인프라 Fabrikam의 다양 한 IP 라우팅 테이블에 해당; 접두사를 처리할 수 있습니다. 그러나 Fabrikam만 ExpressRoute 및 네트워크 성능을 하 고 다른 모든 Office 365 응용 프로그램의 기존 인터넷 대역폭을 사용 하는 가장 중요 한 되는 Office 365 응용 프로그램에 대 한 내부 대역폭을 프로 비전 하 길 원합니다.
  
이런 이유로 Fabrikam 범위로 해당 Azure ExpressRoute 대역폭 값에 대해 비즈니스 온라인 BGP 커뮤니티 12076:5030, ExpressRoute Microsoft 피어 링을 통해 받은 Skype만을 지정 합니다. Office 365와 관련 된 나머지 네트워크 트래픽을 인터넷 탈출 포인트를 사용 하 여 계속 합니다.

|**BGP 커뮤니티 태그 사용**|**Azure ExpressRoute를 통해 라우팅할 수 있는 기능**|**필요한 인터넷 경로**|
|:-----|:-----|:-----|
|비즈니스용 Skype  <br/> (12076:5030)  <br/> |Skype SIP 신호, 다운로드, 음성, 비디오 및 데스크톱 공유  <br/> | DNS, CRL, &amp; CDN 요청  <br/>  Azure ExpressRoute을 통해 지원 되지않는 다른 모든 Office 365 서비스  <br/>  다른 모든 Microsoft 클라우드 서비스  <br/>  Office 365 포털, Office 365 인증 &amp; Office Online  <br/>  비즈니스 원격 분석, Skype 클라이언트에 대 한 빠른 팁, 공용 IM 연결에 대 한 Skype  <br/>  Exchange Online, Exchange Online 보호 및 SharePoint Online  <br/> |

### <a name="scenario-3-scoping-azure-expressroute-for-office-365-services-only"></a>시나리오 3: Office 365 서비스용 Azure ExpressRoute를 범위 지정

Woodgrove Bank Office 365를 포함 하 여 여러 Microsoft 클라우드 서비스의 고객은입니다. 자신의 네트워크를 확인 한 후 용량 및 소비 Woodgrove Bank Azure ExpressRoute 배포 하는 지원 되는 Office 365 서비스에 대 한 기본 설정된 경로를 결정 합니다. 라우팅 테이블에는 Office 365 IP 접두사의 전체 집합을 지원할 수 및 프로 비전는 Azure ExpressRoute 회로 예상된으로 실행 되는 모든 대역폭 및 대기 시간 요구를 지원 합니다.
  
Office 365 특정 BGP 커뮤니티 값, 12076:5010, 12076:5020, 12076:5030, 태그가 지정 된 Office 365, Woodgrove Bank 모든 IP 접두사를 Office 365에 대 한 ExpressRoute의 사용 범위 외에 Microsoft 클라우드 서비스와 연결 된 네트워크 트래픽을 확인 하려면 12076:5100 합니다.

|**BGP 커뮤니티 태그 사용**|**Azure ExpressRoute를 통해 라우팅할 수 있는 기능**|**필요한 인터넷 경로**|
|:-----|:-----|:-----|
|Exchange, SharePoint, 비즈니스용 Skype &amp; 다른 서비스  <br/> (12076:5010, 12076:5020, 12076:5030, 12076:5100)  <br/> |Exchange Online &amp; Exchange Online Protection  <br/> SharePoint Online &amp; 비즈니스용 OneDrive  <br/> Skype SIP 신호, 다운로드, 음성, 비디오 및 데스크톱 공유  <br/> Office 365 포털, Office 365 인증 &amp; Office Online  <br/> | DNS, CRL, &amp; CDN 요청  <br/>  Azure ExpressRoute을 통해 지원 되지않는 다른 모든 Office 365 서비스  <br/>  다른 모든 Microsoft 클라우드 서비스  <br/> |

## <a name="key-planning-considerations-to-using-bgp-communities"></a>주요 계획 고려 사항 BGP 커뮤니티를 사용 하 여

ExpressRoute은 보급 하 고 고객 네트워크를 통해 전파 하는 방법에 영향을 BGP 커뮤니티를 활용 하도록 선택 하는 고객에는 다음 사항을 고려 취해야 합니다.
  
- 확인을 고려해 야 네트워크 설계에 BGP 커뮤니티를 사용 하는 경우 경로 대칭 계속 유지 됩니다. 경우에 따라 추가 또는 제거 BGP 커뮤니티의 여기서 대칭 라우팅 끊어진 상태 이며 라우팅 구성을 다시 대칭 라우팅 설정을 업데이트 해야 하는 상황을 만들 수 있습니다.

- Azure ExpressRoute BGP 커뮤니티 값으로 범위 지정 하는 것은 고객 작업입니다. Microsoft 고객에 의해 구성 된 모든 범위에 관계 없이 피어 링 관계와 관련 된 모든 IP 접두사 보급 됩니다.

- Azure ExpressRoute BGP 커뮤니티를 할당 하는 고객에 따라 Microsoft의 네트워크에 모든 작업을 지원 하지 않습니다.

- IP 접두사를 사용 하 여 Office 365are 서비스 특정 BGP 커뮤니티 값으로 특정 BGP 커뮤니티 지원 되지 않습니다 위치만 표시 합니다. Office 365 서비스는 테 넌 트의 위치를 기반으로 접두사 필터링 기본적으로 전역적 또는 Office 365 클라우드 내에서 데이터 지원 되지 않습니다. 가장 짧은 조정 하는 네트워크 또는 Office 365 서비스의 IP 주소의 실제 위치에 관계 없이 Microsoft 글로벌 네트워크에는 사용자의 네트워크 위치에서 가장 선호 되 네트워크 경로 구성 하는 것이 좋습니다. 요청 중입니다.

- 각 BGP 커뮤니티 값에 포함 된 IP 접두사 값과 연결 된 Office 365 응용 프로그램에 대 한 IP 주소를 포함 하는 서브넷을 나타냅니다. 경우에 따라 둘 이상의 Office 365 응용 프로그램 내의 둘 이상의 커뮤니티 값에서 기존 IP 접두사를에서 발생 하는 서브넷 IP 주소에 있습니다. 이것은 상황이 거의 할당 조각화로 인해 동작 예상 된 경고 이므로 접두사 count 또는 대역폭 관리 목표에 영향을 주지 않습니다. 고객에 게는 "허용 하는 필요한"를 사용 하는 것이 좋습니다 "거부 기능 필요 하지 않습니다." 것과 반대로 접근 하는 영향을 최소화 하기 위해 Office 365에 대 한 BGP 커뮤니티를 활용 하는 경우.

- BGP 커뮤니티를 사용 하 여 원본으로 사용 하는 네트워크 연결 요구 사항 또는 Office 365를 사용 하 여 필요한 구성 변경 되지 않습니다. Office 365에 액세스 하려는 고객에 게는 인터넷에 액세스할 수 있도록 계속 수행 해야 합니다.

- Azure ExpressRoute BGP 커뮤니티와 범위 지정 Microsoft 피어 링 관계를 통해 내부 네트워크를 볼 수 있습니다 경로만 영향을 줍니다. 범위가 지정 된 라우팅와 함께에 PAC 또는 WPAD 구성의 사용 등 추가 응용 프로그램 수준 구성을 설정 해야 합니다.

- Microsoft에서 할당 BGP 커뮤니티를 사용 하 여, 외에도 고객 Azure ExpressRoute 내부 라우팅에 영향을 통해 얻은 Office 365 IP 접두사에 자신의 BGP 커뮤니티를 할당할 수도 있습니다. 인기 사용 사례는 위치 피어 링 및 고객 네트워크에 해당 정보를 다운스트림 사용 하 여 가장 짧은 조정 하기 위해 지정 된 각 ExpressRoute를 통해 얻은 모든 경로를 위치 기반 BGP 커뮤니티를 할당 하거나 대부분에 네트워크 경로 기본 설정 Microsoft의 네트워크 선택 합니다. Office 365 시나리오에 대 한 ExpressRoute와 BGP 커뮤니티를 할당 하는 고객의 사용 하 여 Microsoft 컨트롤 표시 유형 등의 범위를 벗어났습니다.

다음은 짧은 링크를 다시 사용할 수 있습니다: [https://aka.ms/bgpexpressroute365](https://aka.ms/bgpexpressroute365)합니다.
  
## <a name="related-topics"></a>관련 항목

[Office 365에 대한 네트워크 연결](network-connectivity.md)
  
[Office 365용 Azure ExpressRoute](azure-expressroute.md)
  
[Office 365 연결에 대한 ExpressRoute 관리](managing-expressroute-for-connectivity.md)
  
[Office 365용 ExpressRoute를 사용한 라우팅](routing-with-expressroute.md)
  
[Office 365용 ExpressRoute를 사용한 네트워크 계획](network-planning-with-expressroute.md)
  
[미디어 품질 및 온라인 비즈니스 Skype 네트워크 연결 성능](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[ExpressRoute 및 온라인 비즈니스에 대 한 Skype에서 QoS](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[ExpressRoute를 사용 하 여 호출 흐름](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[Office 365용 ExpressRoute 구현](implementing-expressroute.md)
  
[BGP 커뮤니티에 대 한 지원](https://azure.microsoft.com/documentation/articles/expressroute-routing/)
  
[초기 계획 및 성능 기록을 사용하여 Office 365 성능 조정](performance-tuning-using-baselines-and-history.md)
  
[Office 365 성능 문제 해결 계획](performance-troubleshooting-plan.md)
  
[Office 365 교육에 대 한 azure ExpressRoute](https://channel9.msdn.com/series/aer)
