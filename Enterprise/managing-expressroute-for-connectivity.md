---
title: Office 365 연결을 위한 ExpressRoute 관리
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 7/13/2017
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365_Setup
search.appverid:
- MET150
- BCS160
ms.assetid: e4468915-15e1-4530-9361-cd18ce82e231
description: Office 365의 경우에는 인터넷으로 송신 하는 모든 트래픽을 필요로 하지 않고 다양 한 Office 365 서비스에 연결 하는 대체 라우팅 경로를 제공 합니다. Office 365에 대 한 인터넷 연결이 여전히 필요 하지만 Microsoft가 BGP를 통해 네트워크에 알리는 특정 경로는 네트워크에 다른 구성이 없는 경우에는 직접 대상 지정 회로가 기본 설정 되어 있어야 합니다. 이 라우팅을 관리 하기 위해 구성할 수 있는 세 가지 일반적인 영역에는 접두사 필터링, 보안 및 준수 등이 포함 됩니다.
ms.openlocfilehash: 08c991deaaf1b8fa1e17addbed8a23cbfcf37b87
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067134"
---
# <a name="managing-expressroute-for-office-365-connectivity"></a>Office 365 연결을 위한 ExpressRoute 관리

Office 365의 경우에는 인터넷으로 송신 하는 모든 트래픽을 필요로 하지 않고 다양 한 Office 365 서비스에 연결 하는 대체 라우팅 경로를 제공 합니다. Office 365에 대 한 인터넷 연결이 여전히 필요 하지만 Microsoft가 BGP를 통해 네트워크에 알리는 특정 경로는 네트워크에 다른 구성이 없는 경우에는 직접 대상 지정 회로가 기본 설정 되어 있어야 합니다. 이 라우팅을 관리 하기 위해 구성할 수 있는 세 가지 일반적인 영역에는 접두사 필터링, 보안 및 준수 등이 포함 됩니다.
  
> [!NOTE]
> Microsoft는 Microsoft 피어 링 라우팅 도메인에서 Azure Express를 위해 검토 하는 방법을 변경 했습니다. 2017 년 7 월 31 일부터 모든 Azure Express 고객은 Azure 관리 콘솔 또는 PowerShell을 통해 직접 Microsoft 피어 링을 사용 하도록 설정할 수 있습니다. Microsoft 피어 링을 사용 하도록 설정한 후 모든 고객은 이전에 CRM Online 이라고 했던 Dynamics 365 고객 계약 응용 프로그램에 대 한 BGP 경로 알림을 수신 하는 경로 필터를 만들 수 있습니다. Office 365에 대 한 Azure Express를 필요로 하는 고객은 Microsoft 로부터 검토를 받아야 Office 365에 대 한 경로 필터를 만들 수 있습니다. Microsoft 계정 팀에 문의 하 여 Office 365 Express를 사용 하도록 설정 하는 방법을 알아보세요. 인증 되지 않은 구독에서 Office 365에 대 한 경로 필터를 만들려고 하면 [오류 메시지가](https://support.microsoft.com/kb/3181709) 표시 됨
  
## <a name="prefix-filtering"></a>접두사 필터링

고객은 Microsoft에서 보급 한 모든 BGP 경로를 승인 하 고, 제공 된 경로는 엄격한 검토 및 유효성 검사 프로세스를 통해 확인이 추가 되었습니다. 비트 단위는 고객 측에서 인바운드 경로 필터링을 사용 하지 않고 IP 접두사 소유권, 무결성 및 규모와 같은 권장 되는 컨트롤을 기본적으로 제공 합니다.
  
Express 공용 피어 링에서 경로 소유권을 추가로 확인 해야 하는 경우에는 [Microsoft의 공용 IP 범위](https://www.microsoft.com/download/details.aspx?id=53602)를 나타내는 모든 IPv4 및 IPv6 IP 접두사 목록에 대해 알린 경로를 확인할 수 있습니다. 이러한 범위는 전체 Microsoft 주소 공간을 포함 하 고 자주 변경 되며, 이러한 범위에 대해 Microsoft가 소유 하지 않은 경로 누수가 발생 하는 고객에 게 추가 보호 기능을 제공 합니다. 환경. 이벤트가 변경 되 면 해당 월의 1 일에 변경이 수행 되 고 페이지 **세부 정보** 섹션의 버전 번호가 파일을 업데이트할 때마다 변경 됩니다.
  
접두사 필터 목록을 생성 하기 위한 [Office 365 url 및 IP 주소 범위](https://aka.ms/o365endpoints) 를 사용 하지 않아야 하는 이유에는 여러 가지가 있습니다. 다음 포함:
  
- Office 365 IP 접두사는 빈번한 변경 내용이 많이 발생 합니다.

- Office 365 Url 및 IP 주소 범위는 라우팅이 아닌 방화벽 허용 목록 및 프록시 인프라를 관리 하기 위해 디자인 되었습니다.

- Office 365 Url 및 IP 주소 범위는 사용자 간의 연결 범위에 포함 될 수 있는 다른 Microsoft 서비스에는 적용 되지 않습니다.

| |
|**옵션**|**단순화할**|**컨트롤 변경**|
|:-----|:-----|:-----|
|모든 Microsoft 경로 허용  <br/> |**낮음:** 고객은 Microsoft 컨트롤을 사용 하 여 모든 경로가 올바르게 소유 되 고 있는지 확인 합니다.  <br/> |없음  <br/> |
|Microsoft 소유 supernets 필터링  <br/> |**중간 크기:** 고객은 요약 된 접두사 필터 목록을 구현 하 여 Microsoft 소유의 경로만 허용 하도록 합니다.  <br/> |고객은 자주 업데이트 하지 않는 업데이트가 경로 필터에 반영 되도록 해야 합니다.  <br/> |
|Office 365 IP 범위 필터링  <br/> [!CAUTION] 권장 하지 않음
|**High:** 고객은 정의 된 Office 365 IP 접두사를 기반으로 경로를 필터링 합니다.  <br/> |고객은 월별 업데이트에 대 한 강력한 변경 관리 프로세스를 구현 해야 합니다.  <br/> [!CAUTION] 이 솔루션을 사용 하려면 상당한 지속적인 변화가 필요 합니다. 시간에 구현 되지 않은 변경 내용으로 인해 서비스가 중단 될 수 있습니다.   |

Azure Express 경로를 사용 하 여 Office 365에 연결 하는 기능은 Office 365 끝점이 배포 되는 네트워크를 나타내는 특정 IP 서브넷의 BGP 광고를 기반으로 합니다. Office 365의 전역 특성 및 Office 365을 구성 하는 서비스 수로 인해 고객은 네트워크에서 허용 되는 광고를 관리 해야 하는 경우가 많습니다. 환경에 알려진 접두사 수에 관심이 있는 경우 [BGP 커뮤니티](https://support.office.com/article/Using-BGP-communities-in-ExpressRoute-for-Office-365-scenarios-preview-9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099) 기능을 사용 하 여 특정 Office 365 서비스 집합에 대 한 광고를 필터링 할 수 있습니다. 이 기능은 현재 미리 보기에 있습니다.
  
Microsoft에서 들어오는 BGP 경로 보급을 관리 하는 방법에 관계 없이 인터넷 회로를 통해 Office 365에 연결 하는 것과 비교할 때 Office 365 서비스에 특별 한 노출을 받지 않습니다. Microsoft는 고객이 Office 365에 연결 하는 데 사용 하는 회로 유형에 관계 없이 동일한 보안, 규정 준수 및 성능 수준을 유지 관리 합니다.
  
### <a name="security"></a>보안

Office 365 서비스에 대 한 연결을 포함 하는 Express 공용 및 Microsoft 피어 링 간의 연결에 대 한 네트워크 및 보안 경계 제어를 유지 하는 것이 좋습니다. 네트워크에서 Microsoft 네트워크로 전송 되는 네트워크 요청에 대해 보안 제어 기능을 적용 하 고 Microsoft 네트워크에서 네트워크로 인바운드를 이동 하도록 합니다.
  
#### <a name="outbound-from-customer-to-microsoft"></a>고객에서 Microsoft로의 아웃 바운드
  
컴퓨터가 Office 365에 연결 되 면 인터넷 또는 Express 경로를 통해 연결 되는지 여부에 관계 없이 동일한 끝점 집합에 연결 됩니다. 사용 중인 회로에 관계 없이 Office 365 서비스를 일반 인터넷 대상 보다 신뢰할 수 있는 것으로 간주 하는 것이 좋습니다. 아웃 바운드 보안 제어는 포트와 프로토콜에 중점을 두어야 노출을 줄이고 지속적인 유지 관리를 최소화할 수 있습니다. 필요한 포트 정보는 [Office 365 끝점](https://aka.ms/o365endpoints) 참조 문서에서 확인할 수 있습니다.
  
추가 된 컨트롤의 경우 프록시 인프라 내의 FQDN 수준 필터링을 사용 하 여 인터넷 또는 Office 365에 대해 전송 되는 일부 또는 모든 네트워크 요청을 제한 하거나 검사할 수 있습니다. 기능이 출시 되 고 Office 365 제공이 발전 함에 따라 Fqdn 목록을 유지 관리 하려면 보다 강력한 변경 관리 작업을 수행 하 고 게시 된 [office 365 끝점](https://aka.ms/o365endpoints)의 변경 내용을 추적 해야 합니다.
  
> [!CAUTION]
> Microsoft는 IP 접두사에만 의존 하 여 Office 365에 대 한 아웃 바운드 보안을 관리 하는 것이 좋습니다.

|**옵션**|**단순화할**|**컨트롤 변경**|
|:-----|:-----|:-----|
|제한 없음  <br/> |**낮음:** 고객은 Microsoft에 대해 무제한의 아웃 바운드 액세스를 허용 합니다.  <br/> |없음  <br/> |
|포트 제한  <br/> |**낮음:** 고객은 필요한 포트에 따라 Microsoft에 대 한 아웃 바운드 액세스를 제한 합니다.  <br/> |발생.  <br/> |
|FQDN 제한  <br/> |**High:** 고객은 게시 된 Fqdn을 기반으로 하는 Office 365에 대 한 아웃 바운드 액세스를 제한 합니다.  <br/> |월별 변경  <br/> |

#### <a name="inbound-from-microsoft-to-customer"></a>Microsoft에서 고객에 게 인바운드
  
Microsoft에서 네트워크 연결을 시작 해야 하는 몇 가지 선택적 시나리오가 있습니다.
  
- 로그인 하는 동안 ADFS를 확인 합니다.

- [Exchange Server 하이브리드 배포](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx)

- Exchange Online 테 넌 트에서 온-프레미스 호스트로 메일을 보낼 수 있습니다.

- SharePoint Online 메일 SharePoint Online에서 온-프레미스 호스트로 보냅니다.

- [SharePoint 페더레이션 하이브리드 검색](https://technet.microsoft.com/library/dn197174.aspx)

- [SharePoint 하이브리드 BCS](https://technet.microsoft.com/library/dn197239.aspx )

- 비즈니스용 skype [하이브리드](https://technet.microsoft.com/en-us/library/jj205403.aspx) 및/또는 [비즈니스용 skype 페더레이션](https://technet.microsoft.com/library/skype-for-business-online-federation-and-public-im-conectivity.aspx)

- [비즈니스용 Skype 클라우드 커넥터](https://technet.microsoft.com/library/mt605227.aspx )입니다.

복잡도를 줄이기 위해 Express 회로 대신 인터넷 회로를 통해 이러한 연결을 수락 하는 것이 좋습니다. 준수 또는 성능 요구 사항이 있는 경우 이러한 인바운드 연결을가을 수 있는 회로에서 수락 해야 하 고, 방화벽 또는 역방향 프록시를 사용 하 여 허용 되는 연결 범위를 결정 하는 것이 좋습니다. [Office 365 끝점](https://aka.ms/o365endpoints) 을 사용 하 여 올바른 FQDN 및 IP 접두사를 파악할 수 있습니다.
  
### <a name="compliance"></a>규정 준수

여기서는 준수 제어에 사용 하는 라우팅 경로에 의존해 서는 안 됩니다. 사용자가 거 든, 인터넷 회로를 통해 Office 365 서비스에 연결 하는지 여부에 관계 없이 준수 제어는 변경 되지 않습니다. Office 365의 서로 다른 준수 및 보안 인증 수준을 검토 하 여 조직의 요구 사항에 가장 적합 한 옵션을 파악 해야 합니다.
  
다음의 간단한 링크를 사용할 수 있습니다. [https://aka.ms/manageexpressroute365](https://aka.ms/manageexpressroute365)
  
## <a name="related-topics"></a>관련 주제

[콘텐츠 배달 네트워크](content-delivery-networks.md)
  
[Office 365 URL 및 IP 주소 범위](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Office 365 끝점 관리](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Office 365 교육을 위한 Azure Express 경로](https://channel9.msdn.com/series/aer)
