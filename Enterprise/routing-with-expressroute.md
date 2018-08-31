---
title: Office 365용 ExpressRoute를 사용한 라우팅
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/7/2017
ms.audience: ITPro
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
ms.assetid: e1da26c6-2d39-4379-af6f-4da213218408
description: Azure ExpressRoute를 사용 하 여 Office 365에 대 한 라우팅 트래픽을 제대로 이해 하려면 핵심 ExpressRoute 라우팅 요구 사항 및 ExpressRoute 회로 및 라우팅 도메인의 파악 하는 필요 합니다. 이러한 개체는 Office 365 고객을 사용 하는 ExpressRoute를 사용 하기 위한 기본 사항 배치 합니다.
ms.openlocfilehash: e80ce78c0b229881349a4d02c7708fb9509748a9
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541956"
---
# <a name="routing-with-expressroute-for-office-365"></a>Office 365용 ExpressRoute를 사용한 라우팅

Azure ExpressRoute를 사용 하 여 Office 365에 대 한 라우팅 트래픽을 제대로 이해 하려면 핵심 [ExpressRoute 라우팅 요구 사항](https://azure.microsoft.com/documentation/articles/expressroute-routing/) 및는 [ExpressRoute 회로 및 라우팅 도메인의](https://azure.microsoft.com/documentation/articles/expressroute-circuit-peerings/)파악 하는 필요 합니다. 이러한 개체는 Office 365 고객을 사용 하는 ExpressRoute를 사용 하기 위한 기본 사항 배치 합니다.
  
일부 주요 항목을 이해 해야 하는 위의 문서에는 다음과 같습니다.
  
- Microsoft와 사용자를 대신 하 여 피어 링 공급자가 단일 피어 링 위치에 대 한 논리적 연결 ExpressRoute 회로 이지만 특정 물리적 인프라에 매핑된 되지 않습니다.

- ExpressRoute 회로 고객의 키 간에 1:1 매핑을 방법이 있습니다.

- 각 회로 최대 3 독립 피어 관계 (Azure 공용 피어 링, Azure 개인 피어 링 및 Microsoft 피어 링);를 지원할 수 있습니다. Office 365 Microsoft 피어 링 필요합니다.

- 각 회로 모든 피어 관계 간에 공유 되는 고정된 대역폭을 있습니다.

- 모든 공용 IPv4 주소를 입력 하며 사용 되는 숫자로 공용는 ExpressRoute에 대 한 회로, 소유한 것으로 유효성을 검사 하거나 단독으로 자신에 게 할당 하는 주소 범위의 소유자입니다.

- 가상 ExpressRoute 회로 전역적으로 중복 되며 표준 BGP 라우팅 사례를 수행 합니다. 이 때문에 액티브/액티브 구성에서 공급자에 탈출 당 두 실제 회로 것이 좋습니다.

자세한 내용은 지원 되는 서비스, 비용 및 구성 세부 정보에 대 한 [FAQ 페이지](https://azure.microsoft.com/documentation/articles/expressroute-faqs/) 를 참조 하십시오. Microsoft 피어 링 기술 지원 서비스를 제공 하는 연결 공급자 목록에서 정보에 대 한 [ExpressRoute 위치 문서](https://azure.microsoft.com/documentation/articles/expressroute-locations/) 를 참조 하십시오. Channel 9를 더 철저 하 게 개념에 설명 하는 데 도움이에서 10 부 [Office 365 교육에 대 한 Azure ExpressRoute](https://channel9.msdn.com/series/aer) 시리즈를 기록 했을 때 했습니다.
  
## <a name="ensuring-route-symmetry"></a>경로 대칭 수 있는지 확인

Office 365 프런트엔드 서버는 인터넷 및 ExpressRoute에 액세스할 수 있습니다. 이러한 서버를 모두 사용할 수 있는 경우 ExpressRoute 회로 통해 라우팅할 선호 됩니다. 이 때문에 방법이 경로 비대칭 가능성 네트워크 트래픽을 인터넷 회로 통해 라우팅할 선호 하는 경우입니다. 비대칭 경로 문제가 되므로 상태 저장 패킷 검사를 수행 하는 장치 뒤에 아웃 바운드 패킷 보다 서로 다른 경로 따라 이동 하는 반환 되는 트래픽이 차단할 수 있습니다.
  
여부는 인터넷 이나 ExpressRoute을 통해 Office 365에 대 한 연결을 시작에 관계 없이 원본 공개적으로 라우팅할 수 있는 주소 여야 합니다. Microsoft와 직접 피어 링 많은 고객을 중복 고객 간의 가능한가 개인 주소를 가진 불가능 합니다.
  
Office 365에서 온-프레미스 네트워크 통신을 시작할 수는 시나리오는 다음과 같습니다. 네트워크 디자인을 단순화 하려면 인터넷 경로 통해 이러한 라우팅 하는 것이 좋습니다.
  
- 로그인에 대 한 암호 유효성 검사 하는 동안 ADFS 합니다.

- [Exchange Server 하이브리드 배포](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx)합니다.

- 온-프레미스 호스트에는 Exchange Online 테 넌 트에서 메일입니다.

- SharePoint Online 메일 SharePoint Online에서 온-프레미스 호스트에 보냅니다.

- [SharePoint 하이브리드 검색 페더레이션](https://technet.microsoft.com/library/dn197174.aspx)합니다.

- [SharePoint 하이브리드 BCS](https://technet.microsoft.com/library/dn197239.aspx )합니다.

- [비즈니스 하이브리드에 대 한 Skype](https://technet.microsoft.com/en-us/library/jj205403.aspx) 및/또는 [비즈니스 페더레이션 위한 Skype](https://technet.microsoft.com/library/skype-for-business-online-federation-and-public-im-conectivity.aspx)합니다.

- [비즈니스 클라우드 커넥터에 대 한 Skype](https://technet.microsoft.com/library/mt605227.aspx )합니다.

이러한 양방향 트래픽 흐름에 대 한 네트워크 다시 회람 하는 microsoft의 경우, Microsoft와 온-프레미스 장치에 BGP 경로 공유 합니다.
  
## <a name="deciding-which-applications-and-features-route-over-expressroute"></a>ExpressRoute을 통해 라우팅 응용 프로그램 및 기능을 결정 합니다.

Microsoft 피어 링 라우팅 도메인을 사용 하 여 피어 링 관계를 구성 하 고 적절 한 액세스에 대해 승인 된 경우 ExpressRoute을 통해 사용할 수 있는 모든 PaaS 및 SaaS 서비스를 볼 수 있습니다. [BGP 커뮤니티](https://aka.ms/bgpexpressroute365) 또는 [경로 필터](https://docs.microsoft.com/azure/expressroute/how-to-routefilter-portal)와 ExpressRoute 하기 위한 Office 365 서비스를 관리할 수 있습니다.
  
Office 365 비디오 등의 다른 응용 프로그램은 Office 365 응용 프로그램입니다. 그러나 Office 365 비디오 세 서로 다른 구성 요소, 포털, 스트리밍 서비스 및 콘텐츠 배달 네트워크로 구성 됩니다. SharePoint Online, Azure 미디어 서비스 내에서 스트리밍 서비스 생활 내 거주 하는 포털 및 Azure CDN 내에서 거주 하 고 콘텐츠 배달 네트워크입니다. 다음 표에서 이러한 구성 요소를 설명합니다.
  
| |
|**구성 요소**|**응용 프로그램을 원본으로 사용**|**SharePoint Online BGP 커뮤니티에 포함 된?**|**사용**|
|:-----|:-----|:-----|:-----|
|Office 365 비디오 포털  <br/> |SharePoint Online  <br/> |예  <br/> |구성, 업로드  <br/> |
|Office 365 비디오 스트리밍 서비스  <br/> |Azure 미디어 서비스  <br/> |아니요  <br/> |스트리밍 비디오를 CDN에서 사용할 수 없는 경우에 사용 되는 서비스  <br/> |
|Office 365 비디오 콘텐츠 배달 네트워크  <br/> |Azure CDN  <br/> |아니요  <br/> |비디오 다운로드/스트리밍의 기본 소스입니다. [Office 365 비디오 네트워킹에 자세히 알아봅니다](https://support.office.com/article/Office-365-Video-networking-Frequently-Asked-Questions-FAQ-2bed67a1-4052-49ff-a4ce-b7e6530eb98e).<br/> |

응용 프로그램 종류 및 FQDN 하 여 [Office 365 끝점을 문서](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) 에 나열 된 각 Microsoft 피어 링를 사용 하 여 사용할 수 있는 Office 365 기능입니다. 테이블의 FQDN을 사용 하는 이유는 고객 파일 예 PAC [끝점을 Office 365를 관리](https://aka.ms/manageo365endpoints) 하는 가이드를 참조 하십시오 트래픽을 PAC 파일 또는 다른 프록시 구성을 사용 하 여 관리할 수 있도록 합니다.
  
일부 경우에 하나 이상의 하위 Fqdn 더 높은 수준의 와일드 카드 도메인 다르게 보급는 와일드 카드 도메인을 사용 했습니다. 이 문제는 일반적으로 와일드 카드는 모두 보급 ExpressRoute 및 인터넷을 대상의 작은 하위 집합에서 인터넷 또는 그 반대로 보급만 동안 서버 목록이 긴을 나타낼 때 발생 합니다. 차이 이해 하려면 아래 표를 참조 하십시오.
  
이 표에 인터넷에만 보급 sub Fqdn과 함께 인터넷과 Azure ExpressRoute에 Fqdn이 보급는 와일드 카드를 표시 합니다.

|**와일드 카드 도메인 ExpressRoute 및 인터넷 회로에 보급**|**Sub FQDN으로 인터넷 회로 보급**|
|:-----|:-----|
|\*. microsoftonline.com  <br/> |click.email.microsoftonline.com  <br/> portal.microsoftonline.com  <br/> provisioningapi.microsoftonline.com  <br/> adminwebservice.microsoftonline.com  <br/> |
|\*. officeapps.live.com  <br/> |nexusRules.officeapps.live.com  <br/> nexus.officeapps.live.com  <br/> odc.officeapps.live.com  <br/> odc.officeapps.live.com  <br/> cdn.odc.officeapps.live.com  <br/> ols.officeapps.live.com  <br/> ocsredir.officeapps.live.com  <br/> ocws.officeapps.live.com  <br/> ocsa.officeapps.live.com  <br/> |

PAC 파일은 ExpressRoute 네트워크 요청을 보내는 하기 위한 것 하는 일반적으로 보급 회선에 직접 끝점 및 기타 모든 네트워크 요청을 프록시 합니다. 다음과 같이 PAC 파일을 구성 하는 경우 다음과 같은 순서로 PAC 파일을 작성 합니다.
  
1. 프록시 향해 트래픽을 전송 하 고 PAC 파일의 맨 위의 표에 열 2에서에서 sub Fqdn을 포함 합니다. 위해 [끝점을 Office 365 관리](https://aka.ms/manageexpressroute365)에 대 한 문서를 사용할 수에 대 한 샘플 PAC 파일을 작성 했습니다.

2. ExpressRoute 회로에 직접 트래픽을 보내는 보급 ExpressRoute를 [이 문서](https://aka.ms/o365endpoints) 첫번째 구역 아래에 표시 된 모든 Fqdn을 포함 합니다.

3. 다른 네트워크 끝점 또는 프록시 향해 트래픽을 전송 하는 이러한 두 항목, 아래에 있는 규칙이 포함 됩니다.

이 표에서 Azure ExpressRoute를 알리는 sub Fqdn만 함께 인터넷 회로 및 인터넷 회로 보급 된 와일드 카드 도메인을 표시 합니다. Fqdn의 두 열에 위의 PAC 파일에 대 한는 테이블의 아래 파일에 있는 항목의 두번째 그룹에 포함 될 것을 의미 하는 참조, 링크에서 ExpressRoute로 보급 되 고으로 나열 됩니다.

|**인터넷 회로에 와일드 카드 도메인 보급**|**Sub FQDN ExpressRoute 및 인터넷 회로에 보급**|
|:-----|:-----|
|\*. office.com  <br/> |\*. outlook.office.com  <br/> home.office.com  <br/> outlook.office.com  <br/> portal.office.com  <br/> www.office.com  <br/> |
|\*. office.net  <br/> |agent.office.net  <br/> |
|\*. office365.com  <br/> |outlook.office365.com  <br/> smtp.office365.com  <br/> |
|\*. outlook.com  <br/> |\*. protection.outlook.com  <br/> \*. mail.protection.outlook.com  <br/> 자동 검색-\<테 넌 트\>. outlook.com  <br/> |
|\*. windows.net  <br/> |login.windows.net  <br/> |

## <a name="routing-office-365-traffic-over-the-internet-and-expressroute"></a>인터넷 및 ExpressRoute을 통해 Office 365 트래픽 라우팅

Office 365로 라우팅할 적절 하면 응용 프로그램의 핵심 요소 수를 확인 하려면 필요 합니다.
  
1. 대역폭 응용 프로그램이 필요 합니다. 기존 사용 현황을 샘플링 하는 것은 조직에서이 결정 하기 위한만 신뢰할 수 있는 방법입니다.

2. 네트워크 트래픽을 원하는 어떤 탈출 위치에서 네트워크를 그대로 둡니다. 성능에 영향이 발생이 처럼 Office 365에 대 한 연결에 대 한 네트워크 대기 시간을 최소화 하기 위해 계획 해야 합니다. 있기 때문에 실시간 음성 및 비디오를 사용 하는 비즈니스를 위한 Skype 불량 네트워크 대기 시간에 특히 취약 합니다.

3. 원할 경우 전체 또는 ExpressRoute을 활용 하 여 네트워크 위치의 하위 집합입니다.

4. 어떤 위치에서 선택한 네트워크 공급자에서 ExpressRoute를 제공 합니다.

이러한 질문에 대 한 대답을 확인 한 후 대역폭 및 위치 요구를 충족 하는 ExpressRoute 회로 프로 비전 할 수 있습니다. 더 많은 네트워크 지원 계획 [가이드를 조정 하는 Office 365 네트워크](https://aka.ms/tune) 와 [Microsoft 핸들을 네트워크 성능 계획 하는 방법에 대 한 사례 연구](https://aka.ms/tunemsit)를 참조 하십시오.
  
### <a name="example-1-single-geographic-location"></a>예 1: 단일 지리적 위치
  
이 예제는 단일 지리적 위치를 가진 Trey Research 라는 가상 회사에 대 한 시나리오입니다.
  
Trey research 직원 서비스 및 웹사이트 보안 부서에서 회사 네트워크와 해당 하는 ISP 사이 배치 하는 아웃 바운드 프록시 쌍에 명시적으로 허용 하는 인터넷에 연결할 에서만 허용 됩니다.
  
Trey Research Azure ExpressRoute Office 365에 대 한 사용을 계획 하 고 인식 하는 콘텐츠 배달 네트워크 사람에 게 보내는 트래픽와 같은 일부 트래픽은 Office 365 연결에 대 한 ExpressRoute를 통해 라우팅할 수 없게 됩니다. 모든 트래픽 이미 프록시 장치에 대 한 경로가 기본적으로, 이후 이러한 요청 계속 이전과 같이 작동 합니다. Trey Research Azure ExpressRoute 라우팅 요구를 충족 수를 결정 한 후에 회로 만들기, 라우팅, 및 새 ExpressRoute 회로 가상 네트워크에 연결을 구성 하려면 계속 진행 합니다. 현재 위치에서 기본 Azure ExpressRoute 구성 되 면 Trey Research를 사용 하 여 트래픽을 라우팅하 [게시 #2 PAC 파일](https://aka.ms/manageo365endpoints#ID0EACAAA=2._Proxies) 고객 특정 데이터로 직접 ExpressRoute을 통해 Office 365 연결에 대 한 합니다.
  
다음 다이어그램에 표시 된 것과 같이 Trey Research는 라우팅 및 아웃 바운드 프록시 구성 변경의 조합을 사용 하 여 ExpressRoute를 통해 인터넷 및 트래픽의 하위 집합을 통해 Office 365 트래픽을 라우팅 하는 요구 사항을 만족 시킬 수 있습니다.
  
1. Azure ExpressRoute에 대 한 별도 인터넷 탈출 지점의 통해 트래픽을 라우팅하 [게시 #2 PAC 파일](https://aka.ms/manageo365endpoints#ID0EACAAA=2._Proxies) 을 사용 하 여 Office 365에 대 한 합니다.

2. 클라이언트는 기본 경로 프록시 Trey Research 쪽으로 구성 됩니다.

이 예제 시나리오에서는 Trey Research 장치를 사용 하는 아웃 바운드 프록시 합니다. 마찬가지로, 고객에 게 Office 365 용 Azure ExpressRoute를 사용 하지 않는 경로 트래픽을 잘 알려진 높은 볼륨 끝점 사람에 게 보내는 트래픽을 검사의 비용에 따라이 기술을 사용 하 여 사용할 수 있습니다.
  
가장 높은 볼륨 Exchange Online, SharePoint Online 및 Skype 온라인 비즈니스에 대 한 Fqdn은 다음과 같습니다.
  
![ExpressRoute 고객 지 네트워크](media/dab8cc42-b1d6-46d6-b2f6-d70f9e16d5ea.png)
  
- outlook.office365.com, outlook.office.com

- \<테 넌 트 이름\>. sharepoint.com, \<테 넌 트 이름\>-my.sharepoint.com, \<테 넌 트 이름\>-\<app\>. sharepoint.com

- \*. 비 TCP 트래픽에 대 한 IP 범위와 함께 Lync.com

- \*broadcast.officeapps.live.com, \*excel.officeapps.live.com, \*onenote.officeapps.live.com, \*powerpoint.officeapps.live.com, \*view.officeapps.live.com, \*visio.officeapps.live.com, \* word-edit.officeapps.live.com \*word view.officeapps.live.com, office.live.com

[프로그램 프록시에 의해 제한 되지 않습니다 Office 365를 보장](https://blogs.technet.com/b/onthewire/archive/2014/03/28/ensuring-your-office-365-network-connection-isn-t-throttled-by-your-proxy.aspx)하 고 [배포 하 고 Windows 8에서 프록시 설정을 관리](https://blogs.technet.com/b/deploymentguys/archive/2013/05/08/windows-8-supporting-proxy-services-with-static-configurations-web-hosted-pac-files-and-domain-policy-configured-proxy.aspx) 하는 방법에 대 한 자세한 내용은.
  
단일 ExpressRoute 회로와 Trey Research에 대 한 고가용성 부재 됩니다. Trey의 쌍의 중복 ExpressRoute 연결을 처리 하는 지 장치 실패 이벤트에 없는 장애 조치를 수행 하는 추가 ExpressRoute 회로 합니다. 이 인터넷에 대 한 장애 조치 다시 수동 구성 필요 합니다 및 새 IP 주소를 일부 경우에는 predicament에서 Trey Research 둡니다. Trey를 고가용성을 추가 하려는 경우 각 위치에 대 한 추가 ExpressRoute 회로 추가 하 고 액티브/액티브 되는 방식에서으로 회로 구성 하는 가장 간단한 솔루션은 합니다.
  
## <a name="routing-expressroute-for-office-365-with-multiple-locations"></a>여러 위치를 사용 하 여 Office 365에 대 한 라우팅 ExpressRoute

ExpressRoute을 통해 Office 365 트래픽을 라우팅 마지막 시나리오에는 더욱 복잡 한 라우팅 아키텍처에 대 한 기본 토대입니다. 위치 개수, 이러한 위치 존재 하는 위치 대륙의 수, ExpressRoute 회로 및 등의 수에 관계 없이 ExpressRoute을 통해 인터넷 및 일부 트래픽을 일부 트래픽을 라우팅 가능 해야 합니다.
  
여러 지역에서 여러 위치를 사용 하는 고객에 대 한 응답 해야 하는 추가 질문에는 다음이 포함 됩니다.
  
1. 모든 위치에는 ExpressRoute 회로 필요 여부 온라인 비즈니스에 대 한 Skype를 사용 하는 SharePoint Online 또는 Exchange Online에 대 한 대기 시간 민감도 고려 하는 경우 각 위치에 중복 된 한 쌍의 액티브/액티브 ExpressRoute 회로 권장 됩니다. 자세한 내용은 비즈니스 미디어 품질 및 네트워크 연결 가이드에 대 한 Skype를 참조 하십시오.

2. 특정 지역에서 사용할 수 없는 ExpressRoute 회로, 경우 어떻게 해야 전송 되는 Office 365 트래픽이 라우팅될?

3. 많은 소규모 위치를 사용 하는 네트워크의 경우 통합 트래픽에 대 한 기본 설정된 하는 방법은 무엇입니까?

이러한 각 직접 네트워크는 물론 Microsoft에서 제공 되는 옵션을 평가 해야 하는 고유한 과제를 제공 합니다.

|**고려 사항**|**네트워크 구성 요소 평가**|
|:-----|:-----|
|둘 이상의 위치에서 회로  <br/> |액티브/액티브 방식으로 구성 된 두 회로 최소를 사용 하는 것이 좋습니다.  <br/> 비용, 대기 시간 및 대역폭 요구 사항을 비교할 수 있어야 합니다.  <br/> BGP 경로 비용, PAC 파일 및 NAT를 사용 하 여 여러 회로 사용 하 여 라우팅을 관리할 수 있습니다.  <br/> |
|ExpressRoute 회로 없이 위치에서 라우팅  <br/> |송신 및 DNS 해상도로 Office 365에 대 한 요청을 시작 하는 사용자에 근접 한 것이 좋습니다.  <br/> 원격 사무실을 적절 한 끝점을 검색할 수 있도록 DNS 전달을 사용할 수 있습니다.  <br/> 원격 office의 클라이언트 ExpressRoute 회로에 대 한 액세스를 제공 하는 사용할 수 있는 경로가 있어야 합니다.  <br/> |
|소규모 통합  <br/> |사용 가능한 대역폭 및 데이터 사용 현황 신중 하 게 비교 되어야 합니다.  <br/> |

> [!NOTE]
> Microsoft는 경로 실제 위치에 관계 없이 사용할 수 있는 경우 인터넷을 통해 ExpressRoute 선호 됩니다.
  
이러한 고려 사항에 각각 고유한 각 네트워크에 대 한 계정 점을 고려해 야 합니다. 다음은 한 예입니다.
  
### <a name="example-2-multi-geographic-locations"></a>예 2: 여러 지리적 위치
  
이 예제는 여러 지리적 위치를 가진 Humongous 보험 라는 가상 회사에 대 한 시나리오입니다.
  
광성의 사무실을 갖는 지리적으로 분산 되어있는 합니다. 대부분의 Office 365 트래픽 자신의 네트워크에 직접 연결 유지 하기 위해서는 Office 365 용 Azure ExpressRoute를 구현 하 고 원합니다. 광성 사무실 두 추가 대륙에는 있습니다. ExpressRoute 하기가 쉽지 않으면 원격 사무실에서 직원 ExpressRoute 연결을 사용 하는 주요 기능 중 하나 또는 모두를 다시 라우팅할 해야 합니다.
  
원칙은은 Microsoft 데이터 센터에 대 한 트래픽이 전송 되는 Office 365를 최대한 신속 하 게 얻는 것입니다. 이 예제에서는 Humongous 보험 해야 결정 하려면 Microsoft 데이터 센터에 모든 연결을 통해 가능한 또는 지사를 자신의 Microsoft를 내부 네트워크를 통해 라우팅할 해야 하는 경우로 신속 하 게 인터넷을 통해 자신의 원격 사무실 회람 해야 하는 경우 ExpressRoute 연결을 통해 데이터 센터 최대한 신속 하 게 합니다.
  
Microsoft의 데이터 센터, 네트워크 및 응용 프로그램 아키텍처는 전역적으로 서로 다른 통신을 수행 하 고 가능한 가장 효율적인 방식으로 서비스 하도록 설계 되었습니다. 이 세계에서 가장 큰 네트워크 중 하나입니다. 이 아키텍처를 활용 하기 위해 필요한 것 보다 긴 고객 네트워크에 남아 있는 Office 365 사람에 게 보내는 요청 수 없습니다.
  
Humongous 보험의 상황에서는 ExpressRoute를 통해 사용 하려는 응용 프로그램에 따라 진행 해야 있습니다. 예: 비즈니스를 위한 Skype 온라인는 고객, 하거나 비즈니스 온라인 미디어 품질 및 네트워크에 대 한 Skype에서 권장 디자인 비즈니스 온라인 모임에 대 한 외부 Skype에 연결할 때 ExpressRoute 연결을 활용할 수 있도록 계획 연결 가이드 세번째 위치에 대 한 추가 ExpressRoute 회로 구축 하는 것입니다. 네트워킹 관점에서 더 비싼 수 있음 그러나 요청을 라우팅하면 하나의 대륙에서 다른 Microsoft 데이터 센터를 전달 하는 발생할 수 불량 또는 사용할 수 없게 경험 Skype 하는 동안 비즈니스 온라인 모임 및 통신을 위해 전에 합니다.
  
Humongous 보험를 사용할 수 없는 하거나 온라인 비즈니스에 대 한 Skype를 활용 하 여 어떤 식으로도 계획 하지 않으면 연결 수를 ExpressRoute와 대륙에 다시 전송 되는 Office 365 네트워크 트래픽을 라우팅 가능 하지만 발생할 수 불필요 한 대기 시간 또는 TCP 정체 합니다. 두 경우 모두 콘텐츠 배달 네트워크는 Office 365을 활용 하는 로컬 사이트에서 인터넷으로 보내는 트래픽을 것이 좋습니다. 라우팅 인터넷에 의존 합니다.
  
![ExpressRoute 여러 지리적 위치](media/98fdd883-2c5a-4df7-844b-bd28cd0b9f50.png)
  
Humongous 보험를 계획 하는 자신의 다중 geography 전략 때 중심으로 회로, 수의 회로, 장애 조치의 크기를 고려 하 고 등 해야할 수가 있습니다.
  
여러 영역을 회선을 사용 하 여 시도할 수 있는 단일 위치에서 ExpressRoute와 Humongous 보험가 원격 사무실에서 Office 365에 대 한 연결 본사 가장 가까운 Office 365 데이터 센터에 전송 및 받은 되도록는 본사 위치입니다. 이 작업을 수행 하려면 Humongous 보험 구현 왕복 및 본사 인터넷 탈출 지점에서 가장 가까운 Office 365 환경과 적절 한 연결을 설정 하는 데 필요한 DNS 조회의 수를 줄이는 DNS 전달 합니다. 클라이언트의 로컬 프런트엔드 서버를 해결 하는 것을 금지 하 고 여기서 Humongous 보험은 피어 링 Microsoft와 인사부 근처에 연결 하는 사용자는 프런트엔드 서버는 보장 합니다. [도메인 이름에 대 한 조건부 전달 자가 할당](https://technet.microsoft.com/library/Cc794735%28v=WS.10%29.aspx)을 배울 수 있습니다.
  
이 시나리오에서는 원격 사무실에서 트래픽을 북미에서 Office 365 프런트엔드 인프라를 해결 하 고 Office 365 응용 프로그램의 아키텍처에 따라 백엔드 서버에 연결 하려면 Office 365를 활용 합니다. 예: 북미에서 연결을 종료 Exchange Online 및 테 넌 트 상주한 위치에 관계 없이 이러한 프런트엔드 서버 backend 사서함 서버에 연결 합니다. 모든 서비스 유니캐스트 및 애니캐스트 대상으로 이루어진 광범위 하 게 분산된 앞면 도어 서비스를 포함 합니다.
  
Humongous 여러 대륙의 주요 지사가, 비즈니스 온라인 용 Skype와 같은 중요 한 응용 프로그램에 대 한 대기 시간 감소 하기 위해 두 액티브/액티브 회로 지역 당 최소는 것이 좋습니다. 모든 사무실을 단일 대륙에 실시간으로 공동 작업을 사용 하는 경우 고객 특정 결정은 가리킨 통합 또는 분산 탈출 필요 합니다. 여러 회로 사용할 수 있는 경우 BGP 라우팅 확인할 장애 조치 해야 모든 단일 회로 사용할 수 없게 합니다.
  
샘플 [라우팅 구성](https://azure.microsoft.com/documentation/articles/expressroute-config-samples-routing/) 에 대 한 자세한 내용은 및 [https://azure.microsoft.com/en-us/documentation/articles/expressroute-config-samples-nat/](https://azure.microsoft.com/documentation/articles/expressroute-config-samples-nat/)합니다.
  
## <a name="selective-routing-with-expressroute"></a>ExpressRoute를 사용 하 여 라우팅을 선택

ExpressRoute를 사용 하 여 선택적 라우팅을에 필요할 수 다양 한 이유로 인해 테스트, 예: ExpressRoute 사용자의 하위 집합을 제공 합니다. 다양 한 도구 고객 선택적으로 ExpressRoute을 통해 Office 365 네트워크 트래픽을 라우팅 하는데 사용할 수 있습니다.
  
1. **경로 필터링/격리** -서브넷 또는 라우터의 하위 집합에 ExpressRoute을 통해 Office 365로 BGP 경로 허용 합니다. 이 고객 네트워크 세그먼트 또는 실제 사무실 위치에서 선택적으로 라우팅합니다. Office 365에 대 한 ExpressRoute 스 태거 배포에 대 한 일반적인 며 BGP 장치에 구성 됩니다.

2. 특정 경로에 라우팅하는 특정 Fqdn에 대 한 네트워크 트래픽을 보내는 하는 **PAC 파일/Url** -Office 365 지시 합니다. 이 선택적으로 라우팅합니다 클라이언트 컴퓨터에서 [PAC 파일 배포](https://aka.ms/manageo365endpoints#ID0EACAAA=2._Proxies)하 여 확인 합니다.

3. **경로 필터링** - [경로 필터](https://docs.microsoft.com/azure/expressroute/how-to-routefilter-portal) 는 Microsoft 피어 링을 통해 지원 되는 서비스의 하위 집합을 사용 하는 방법입니다.

4. **BGP 커뮤니티** - [BGP 커뮤니티 태그](https://aka.ms/bgpexpressroute365) 에 따라 필터링 확인 하는 Office 365 응용 프로그램을 ExpressRoute 통과 됩니다 하 고 인터넷을 통과 하는 고객 수 있습니다.

짧은 링크를 다시 사용할 수는 다음과 같습니다.[https://aka.ms/erorouting](https://aka.ms/erorouting)
  
## <a name="related-topics"></a>관련 항목

[Office 365에 대한 네트워크 연결](network-connectivity.md)
  
[Office 365용 Azure ExpressRoute](azure-expressroute.md)
  
[Office 365 연결에 대한 ExpressRoute 관리](managing-expressroute-for-connectivity.md)
  
[Office 365용 ExpressRoute를 사용한 네트워크 계획](network-planning-with-expressroute.md)
  
[Office 365용 ExpressRoute 구현](implementing-expressroute.md)
  
[미디어 품질 및 온라인 비즈니스 Skype 네트워크 연결 성능](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[비즈니스 온라인 용 Skype에 대 한 네트워크를 최적화](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)
  
[ExpressRoute 및 온라인 비즈니스에 대 한 Skype에서 QoS](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[ExpressRoute를 사용 하 여 호출 흐름](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[ExpressRoute BGP 커뮤니티를 사용 하 여 Office 365 시나리오에 대 한](bgp-communities-in-expressroute.md)
  
[초기 계획 및 성능 기록을 사용하여 Office 365 성능 조정](performance-tuning-using-baselines-and-history.md)
  
[Office 365 성능 문제 해결 계획](performance-troubleshooting-plan.md)
  
[Office 365 URL 및 IP 주소 범위](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Office 365 네트워크 및 성능 조정](network-planning-and-performance.md)
