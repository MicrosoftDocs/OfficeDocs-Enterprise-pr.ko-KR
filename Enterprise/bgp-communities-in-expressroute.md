---
title: Office 365 시나리오에서 (으)로의 BGP 커뮤니티 사용
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/26/2018
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099
description: Azure Express 경로를 사용 하 여 Office 365에 연결 하는 기능은 Office 365 끝점이 배포 되는 네트워크를 나타내는 특정 IP 서브넷의 BGP 광고를 기반으로 합니다. Office 365의 전역 특성 및 Office 365을 구성 하는 서비스 수로 인해 고객은 네트워크에서 허용 되는 광고를 관리 해야 하는 경우가 많습니다. IP 서브넷 수 줄이기 BGP network 관리 용어를 정렬 하기 위해이 문서의 나머지 부분에서 IP 접두사 라고 하며, 고객을 위해 다음과 같은 최종 목표를 사용 합니다.
ms.openlocfilehash: e9b9d78df4898c1bb212b62444e5a9911a0e548c
ms.sourcegitcommit: 89ecf793443963b4c87cf1033bf0284cbfb83d9a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/09/2019
ms.locfileid: "38077937"
---
# <a name="using-bgp-communities-in-expressroute-for-office-365-scenarios"></a>Office 365 시나리오에서 (으)로의 BGP 커뮤니티 사용

Azure Express 경로를 사용 하 여 Office 365에 연결 하는 기능은 Office 365 끝점이 배포 되는 네트워크를 나타내는 특정 IP 서브넷의 BGP 광고를 기반으로 합니다. Office 365의 전역 특성 및 Office 365을 구성 하는 서비스 수로 인해 고객은 네트워크에서 허용 되는 광고를 관리 해야 하는 경우가 많습니다. IP 서브넷 수 줄이기 BGP network 관리 용어를 정렬 하기 위해이 문서의 나머지 부분에서 IP 접두사 라고 하며, 고객을 위해 다음과 같은 최종 목표를 사용 합니다.
  
- 수신 되 **는 ip 접두사를 관리 합니다. 허용** 된 수의 ip 접두사를 지원 하는 내부 네트워크 인프라 또는 네트워크 캐리어가 있고 제한 된 번호 위의 접두사를 허용 하는 데 드는 비용이 청구 되는 고객은 네트워크에 이미 보급 되어 있는 총 접두사 수를 평가 하 고, 더 많은 Office 365 응용 프로그램을 사용 하는 것이 가장 적합 합니다.

- **Azure express** 경로를 사용 하 여 필요한 대역폭을 관리할 수 있습니다. 고객은 Emailpath와 인터넷 경로를 통해 Office 365 서비스의 대역폭 봉투를 제어 하는 것이 좋습니다. 이를 통해 고객은 비즈니스용 Skype와 같은 특정 응용 프로그램에 대해가 위 대역폭을 예약 하 고 나머지 Office 365 응용 프로그램을 인터넷 경로를 통해 라우팅할 수 있습니다.

이러한 목표를 고객에 게 지원 하기 위해, 아래 예에서와 같이,를 사용 하 여 서비스 관련 BGP 커뮤니티 값에 태그를 지정한 Office 365 IP 접두사에 태그가 지정 됩니다.
  
> [!NOTE]
> 다른 응용 프로그램과 연결 된 일부 네트워크 트래픽은 커뮤니티 값에 포함 될 것으로 예상 해야 합니다. 이는 공유 서비스 및 데이터 센터를 사용 하 여 서비스를 제공 하는 글로벌 소프트웨어에 대해 예상 되는 동작입니다. 이는 위의 두 목표를 고려 하 여 가능한 경우이를 최소화 하 고 접두사 개수 및/또는 대역폭을 염두에 두십시오.

|**서비스**|**BGP 커뮤니티 값**|**참고**|
|:-----|:-----|:-----|
|환율\*  <br/> |12076:5010  <br/> |Exchange 및 EOP 서비스 포함\*  <br/> |
|sharepoint\*  <br/> |12076:5020  <br/> |SharePoint Online  <br/> |
|비즈니스용 skype\*  <br/> |12076:5030  <br/> |비즈니스용 Skype Online  <br/> |
|기타 Office 365 서비스\*  <br/> |12076:5100  <br/> |Office 365 포털 서비스와 함께 Azure Active Directory (인증 및 디렉터리 동기화 시나리오)가 포함 됩니다.  <br/> |
|\*Express에 포함 된 서비스 시나리오의 범위는 [Office 365 endpoints](https://aka.ms/o365endpoints) 문서에 설명 되어 있습니다.  <br/> \*\*추가 서비스 및 BGP 커뮤니티 값이 나중에 추가 될 수 있습니다. [현재 BGP 커뮤니티 목록을 참조](https://azure.microsoft.com/documentation/articles/expressroute-routing/)하세요.  <br/> |

## <a name="what-are-the-most-common-scenarios-for-using-bgp-communities"></a>BGP 커뮤니티를 사용 하는 가장 일반적인 시나리오는 무엇 인가요?

고객은 BGP 커뮤니티를 사용 하 여 Azure Express 경로를 통해 네트워크에서 허용 하는 IP 접두사 그룹을 규제 하 여 특정 Office 365 서비스의 총 IP 접두사 수 및 예상 대역폭 봉투에 영향을 주는 것을 알 수 있습니다. 모든 Office 365에서 Azure Express 경로 또는 BGP 커뮤니티 사용에 상관 없이 인터넷에 바인딩된 트래픽이 필요한 지 이해 하는 것이 중요 합니다. 다음 세 가지 시나리오는이 기능의 가장 일반적인 사용 방법입니다.
  
### <a name="scenario-1-minimizing-the-number-of-office-365-ip-prefixes"></a>시나리오 1: Office 365 IP 접두사 수 최소화

Contoso Corporation은 현재 Exchange Online 및 SharePoint Online 용 Office 365을 사용 하는 5만 사용자 회사입니다. "Express에서의 요구 사항 검토" Contoso는 여러 지역에서 네트워크 장치에서 100 추가 경로 항목 보다 많은 라우팅 테이블 크기를 처리할 수 없음을 결정 합니다. Contoso는 전체 Office 365 서비스에 대해이를 알리는 총 IP 접두사 수를 검토 했으며 100을 초과 하는 것으로 결론을 했습니다. Contoso는 100 추가 경로 항목을 유지 하기 위해 Office 365에 대 한 Express를 사용 하는 것을 SharePoint Online BGP 커뮤니티 가치 (12076:5020, Microsoft 피어 링을 통해 수신)로 범위를 조정 합니다.

|**사용 되는 BGP 커뮤니티 태그**|**Azure Express를 통해 라우팅할 수 있는 기능**|**인터넷 경로 필요**|
|:-----|:-----|:-----|
|SharePoint  <br/> (12076:5020)  <br/> |SharePoint Online &amp; 비즈니스용 OneDrive  <br/> | DNS, CRL, &amp; CDN 요청  <br/>  기타 모든 Office 365 서비스는 Azure Express를 통해 명시적으로 지원 되지 않습니다.  <br/>  다른 모든 Microsoft 클라우드 서비스  <br/>  Office 365 포털, Office 365 인증, &amp; office (브라우저)  <br/>  Exchange Online, Exchange Online Protection 및 비즈니스용 Skype Online  <br/> |

> [!NOTE]
> 각 서비스에 대 한 접두사 카운트를 낮추려면 서비스 간에 최소한의 겹치는 부분이 유지 됩니다. 이는 예상 되는 동작입니다.
  
### <a name="scenario-2-scoping-expressroute-and-internal-bandwidth-use-to-some-office-365-services"></a>시나리오 2: 일부 Office 365 서비스에 대 한 대상 및 내부 대역폭 사용 범위 지정

분산 된 이기종 네트워크를 사용 하는 대규모 다국적 국내 기업에서는 다음을 비롯 한 여러 Office 365 서비스의 구독자입니다. Exchange Online, SharePoint Online 및 비즈니스용 Skype Online Fabrikam의 내부 라우팅 인프라는 라우팅 테이블에서 수천 개의 IP 접두사를 처리할 수 있습니다. 그러나 Fabrikam은 네트워크 성능에 가장 중요 한 Office 365 응용 프로그램에 대 한 데이터 (내부 대역폭과 기타)를 프로 비전 하 고 다른 모든 Office 365 응용 프로그램에 대해 기존 인터넷 대역폭을 사용 하려고 합니다.
  
따라서 Fabrikam은 Azure Express에서 Microsoft 피어 링을 통해 수신 되는 비즈니스용 Skype Online BGP 커뮤니티 가치 12076:5030로 범위가 이동 합니다. Office 365와 관련 된 나머지 네트워크 트래픽은 인터넷 송신 지점을 계속 사용 합니다.

|**사용 되는 BGP 커뮤니티 태그**|**Azure Express를 통해 라우팅할 수 있는 기능**|**인터넷 경로 필요**|
|:-----|:-----|:-----|
|비즈니스용 Skype  <br/> (12076:5030)  <br/> |Skype SIP 신호, 다운로드, 음성, 비디오 및 데스크톱 공유  <br/> | DNS, CRL, &amp; CDN 요청  <br/>  기타 모든 Office 365 서비스는 Azure Express를 통해 명시적으로 지원 되지 않습니다.  <br/>  다른 모든 Microsoft 클라우드 서비스  <br/>  Office 365 포털, Office 365 인증, &amp; office (브라우저)  <br/>  비즈니스용 skype 원격 분석, Skype 클라이언트 빠른 팁, 공용 IM 연결  <br/>  Exchange Online, Exchange Online Protection 및 SharePoint Online  <br/> |

### <a name="scenario-3-scoping-azure-expressroute-for-office-365-services-only"></a>시나리오 3: Office 365 서비스 전용 Azure Express 범위 지정

Woodgrove 은행은 Office 365을 비롯 한 여러 Microsoft 클라우드 서비스를 포함 하는 고객입니다. 네트워크 용량을 평가 하 고 Woodgrove 은행은 지원 되는 Office 365 서비스의 기본 경로로 Azure Express 경로를 배포 하기로 결정 합니다. 라우팅 테이블은 전체 Office 365 IP 접두사와 모든 예상 대역폭과 대기 시간 요구를 지원 하도록 프로 비전 된 Azure Express 회로를 지원할 수 있습니다.
  
Office 365 이외의 Microsoft 클라우드 서비스와 관련 된 네트워크 트래픽을 확인 하기 위해 Woodgrove 은행은 office 365에 대 한 모든 IP 접두사에 대 한 office 365 관련 BGP 커뮤니티 값, 12076:5010, 12076:5020, 12076:5030 등을 사용 하는 것의 범위를 지정 합니다. 12076:5100

|**사용 되는 BGP 커뮤니티 태그**|**Azure Express를 통해 라우팅할 수 있는 기능**|**인터넷 경로 필요**|
|:-----|:-----|:-----|
|Exchange, 비즈니스용 Skype, SharePoint, &amp; 기타 서비스  <br/> (12076:5010, 12076:5020, 12076:5030, 12076:5100)  <br/> |Exchange Online &amp; Exchange online Protection  <br/> SharePoint Online &amp; 비즈니스용 OneDrive  <br/> Skype SIP 신호, 다운로드, 음성, 비디오 및 데스크톱 공유  <br/> Office 365 포털, Office 365 인증, &amp; office (브라우저)  <br/> | DNS, CRL, &amp; CDN 요청  <br/>  기타 모든 Office 365 서비스는 Azure Express를 통해 명시적으로 지원 되지 않습니다.  <br/>  다른 모든 Microsoft 클라우드 서비스  <br/> |

## <a name="key-planning-considerations-to-using-bgp-communities"></a>BGP 커뮤니티 사용에 대 한 주요 계획 고려 사항

BGP 커뮤니티를 활용 하 여 고객 네트워크를 통해 거가 보급 되 고 전파 되는 방식에 영향을 주는 고객은 다음과 같은 고려 사항을 고려해 야 합니다.
  
- 네트워크 디자인에서 BGP 커뮤니티를 사용 하는 경우 경로 대칭이 계속 유지 되 고 있는지 확인 하는 것이 중요 합니다. 경우에 따라 BGP 커뮤니티를 추가 하거나 제거 하면 대칭 라우팅이 중단 되 고, 대칭 라우팅을 다시 설정 하기 위해 라우팅 구성을 업데이트 해야 하는 상황이 발생할 수 있습니다.

- BGP 커뮤니티 값을 사용 하 여 Azure Express를 범위 지정 하는 것은 고객 작업입니다. Microsoft는 고객이 구성한 범위에 관계 없이 피어 링 관계와 관련 된 모든 IP 접두사를 보급 합니다.

- Azure Express는 고객이 할당 한 BGP 커뮤니티에 따라 Microsoft 네트워크에서 작업을 지원 하지 않습니다.

- Office 365에서 사용 되는 IP 접두사는 서비스 관련 BGP 커뮤니티 값 으로만 표시 되며 location 관련 BGP 커뮤니티는 지원 되지 않습니다. Office 365 서비스는 본질적으로 전역적으로 진행 되며, 테 넌 트의 위치 또는 Office 365 클라우드 내의 데이터를 기반으로 하는 접두사는 지원 되지 않습니다. 권장 되는 방법은 Office 365 서비스의 IP 주소에 대 한 실제 위치에 관계 없이 사용자 네트워크 위치에서 Microsoft 글로벌 네트워크로 가장 짧은 네트워크 경로를 조정 하도록 네트워크를 구성 하는 것입니다. 요청 하 고 있습니다.

- 각 BGP 커뮤니티 값에 포함 된 IP 접두사는 값과 연결 된 Office 365 응용 프로그램에 대 한 IP 주소를 포함 하는 서브넷을 나타냅니다. 경우에 따라 둘 이상의 Office 365 응용 프로그램에 서브넷 내에 ip 주소가 있는 경우 두 개 이상의 커뮤니티 값에 IP 접두사가 존재 합니다. 드문 경우는 아니지만, 할당 조각화로 인 한 동작이 며 접두사 개수 나 대역폭 관리 목표에는 영향을 주지 않습니다. 고객은 Office 365의 BGP 커뮤니티를 활용 하 여 영향을 최소화할 때 "필요 하지 않은 작업을 수행 합니다." 방식을 사용 하는 것이 좋습니다.

- BGP 커뮤니티를 사용 하는 경우 Office 365을 사용 하는 데 필요한 기본 네트워크 연결 요구 사항 또는 구성이 변경 되지 않습니다. Office 365에 액세스 하려는 고객은 여전히 인터넷에 액세스할 수 있어야 합니다.

- BGP 커뮤니티를 사용한 Azure Express에서의 범위 지정은 내부 네트워크가 Microsoft 피어 링 관계를 통해 볼 수 있는 경로에만 영향을 줍니다. 범위 지정 라우팅과 함께 PAC 또는 WPAD 구성을 사용 하는 등의 추가 응용 프로그램 수준 구성을 수행 해야 할 수 있습니다.

- Microsoft에서 할당 한 BGP 커뮤니티를 사용 하는 것 외에도, 고객은 Azure Express를 통해 배운 Office 365 IP 접두사에 자체 BGP 커뮤니티를 할당 하 여 내부 라우팅에 영향을 줄 수 있습니다. 일반적인 사용 사례는 지정 된 각 정보 기반 피어 링 위치를 통해 배운 모든 경로에 위치 기반의 BGP 커뮤니티를 할당 한 다음 고객 네트워크에서 해당 정보 다운스트림을 사용 하 여 가장 짧은 우선 순위 또는 가장 선호 되는 네트워크 경로를 조정 합니다. Microsoft 네트워크 Office 365에 대 한 외부로의 할당 된 BGP 커뮤니티를 사용 하는 것은 Microsoft 통제 또는 가시성 범위를 벗어납니다.

여기서는 다음을 수행 [https://aka.ms/bgpexpressroute365](https://aka.ms/bgpexpressroute365)하는 데 사용할 수 있는 간단한 링크를 제공 합니다.
  
## <a name="related-topics"></a>관련 주제

[Office 365 네트워크 연결 평가](assessing-network-connectivity.md) 
  
[Office 365용 Azure ExpressRoute](azure-expressroute.md)
  
[Office 365 연결에 대한 ExpressRoute 관리](managing-expressroute-for-connectivity.md)
  
[Office 365용 ExpressRoute를 사용한 라우팅](routing-with-expressroute.md)
  
[Office 365용 ExpressRoute를 사용한 네트워크 계획](network-planning-with-expressroute.md)
  
[비즈니스용 Skype Online의 미디어 품질 및 네트워크 연결 성능](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[비즈니스용 Skype Online의 Express 경로 및 QoS](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[Express를 사용 하는 호출 흐름](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[Office 365용 ExpressRoute 구현](implementing-expressroute.md)
  
[BGP 커뮤니티 지원](https://azure.microsoft.com/documentation/articles/expressroute-routing/)
  
[초기 계획 및 성능 기록을 사용하여 Office 365 성능 조정](performance-tuning-using-baselines-and-history.md)
  
[Office 365 성능 문제 해결 계획](performance-troubleshooting-plan.md)
  
[Office 365 교육을 위한 Azure Express 경로](https://channel9.msdn.com/series/aer)
