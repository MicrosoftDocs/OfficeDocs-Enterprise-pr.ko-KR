---
title: Office 365 연결에 대한 ExpressRoute 관리
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 7/13/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365_Setup
search.appverid:
- MET150
- BCS160
ms.assetid: e4468915-15e1-4530-9361-cd18ce82e231
description: Office 365에 대 한 ExpressRoute 탈출 인터넷에 대 한 모든 트래픽을 작성할 필요 없이 다양 한 Office 365 서비스에 도달 하는 대체 라우팅 경로 제공 합니다. Office 365에 대 한 인터넷 연결을 여전히 필요 하지만 개인 네트워크를 통해 BGP 보급 하는 Microsoft는 특정 경로 네트워크의 다른 구성은 아니면 기본적으로 사용 되는 직접 ExpressRoute 회로 확인 합니다. 이 라우팅 포함 관리를 구성 하는 것이 좋습니다 세 공통 영역 필터링, 보안 및 규정 준수를 붙여야 합니다.
ms.openlocfilehash: 5345c4067f4ecf9b1b1bc1a0ad20d6e1f5273f65
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541968"
---
# <a name="managing-expressroute-for-office-365-connectivity"></a>Office 365 연결에 대한 ExpressRoute 관리

Office 365에 대 한 ExpressRoute 탈출 인터넷에 대 한 모든 트래픽을 작성할 필요 없이 다양 한 Office 365 서비스에 도달 하는 대체 라우팅 경로 제공 합니다. Office 365에 대 한 인터넷 연결을 여전히 필요 하지만 개인 네트워크를 통해 BGP 보급 하는 Microsoft는 특정 경로 네트워크의 다른 구성은 아니면 기본적으로 사용 되는 직접 ExpressRoute 회로 확인 합니다. 이 라우팅 포함 관리를 구성 하는 것이 좋습니다 세 공통 영역 필터링, 보안 및 규정 준수를 붙여야 합니다.
  
> [!NOTE]
> Microsoft은 Azure ExpressRoute에 대 한 Microsoft Peering 라우팅 도메인을 검토 하는 방법을 변경 합니다. 2017 년 7 월 31, 시작 Azure ExpressRoute 고객을 모두 사용 하도록 설정할 수 Microsoft Peering Azure 관리 콘솔에서 직접 또는 PowerShell을 통해 합니다. Microsoft Peering를 활성화 한 후 모든 고객에 Dynamics 365 고객 계약 응용 프로그램 (이전의 CRM Online)에 대 한 BGP 경로 알림의 받을 경로 필터를 만들 수 있습니다. Office 365 용 Azure ExpressRoute 필요 고객 계정을 얻어야 검토 Microsoft에서 Office 365에 대 한 경로 필터를 만들 수 있습니다. Office 365 ExpressRoute를 사용 하도록 설정 하는 것에 대 한 검토를 요청 하는 방법에 대해 자세히 알아보려면 Microsoft 계정 팀에 게 문의 하십시오. Office 365에 대 한 경로 필터를 만들 권한이 없는 구독 [오류 메시지](https://support.microsoft.com/kb/3181709) 를 받습니다.
  
## <a name="prefix-filtering"></a>필터링 접두사

고객을 수락 하 고 모든 BGP 경로 알리는 Microsoft에서 제공 하 여 경로 제거 하는 추가 된 대 한 조사를 모든 혜택 엄격한 검토 및 유효성 검사 프로세스를 거쳐 되는지 확인 하는 것이 좋습니다. 기본적으로 ExpressRoute 고객 측면에 대 한 필터링 없는 인바운드 경로와 IP 접두사 소유권, 무결성 및 확장-같은 권장된 컨트롤을 제공 합니다.
  
ExpressRoute 공용 피어 링 별 경로 소유권의 유효성을 추가로 필요로 하는 경우에 [Microsoft의 공용 IP 범위](https://www.microsoft.com/download/details.aspx?id=53602)를 표시 하는 모든 i p v 4와 i p v 6 IP 접두사 목록에 대해 보급된 경로 확인할 수 있습니다. 이러한 범위 전체 Microsoft 주소 공간을 설명 하 고도 비 Microsoft 경로에 누수 소유 하 고 우려되는 고객에 게 추가 보호 기능을 제공 하는 신뢰할 수 있는 필터링 기준으로 삼을 범위 집합을 제공 자주 변경 자신의 환경입니다. 변경 인 경우에 달의 1에서 이루어집니다 및 페이지의 **세부 정보** 섹션에서 버전 번호는 파일은 업데이트 될 때마다 변경 됩니다.
  
접두사 필터 목록을 생성 (영문)에 대 한 [Office 365 Url 및 IP 주소 범위](https://aka.ms/o365endpoints) 를 사용 하지 않도록 하는 이유 수가 있습니다. 다음을 포함 합니다.
  
- Office 365 IP 접두사 자주 별로 변경 된 많은 거쳐야 합니다.

- 범위는 방화벽 관리 위한 Office 365 Url 및 IP 주소 허용 목록 및 프록시 인프라 라우팅 하지 않습니다.

- Office 365 Url 및 IP 주소 범위 ExpressRoute 연결에 대 한 범위에 있을 수 있는 다른 Microsoft 서비스에 설명 하지 않습니다.

| |
|**옵션**|**복잡성**|**컨트롤을 변경 합니다.**|
|:-----|:-----|:-----|
|모든 Microsoft 경로 수락 합니다.  <br/> |**낮음:** 고객은 Microsoft 컨트롤 모든 경로가 제대로 소유 하는 확인을 사용 합니다.  <br/> |없음  <br/> |
|Supernets 소유 하 고 Microsoft 필터링  <br/> |**중간:** 고객 경로 소유 하는 Microsoft만 허용 하려면 필터 목록을 요약 된 접두사를 구현 합니다.  <br/> |고객은 자주 사용 하지 않는 업데이트 경로 필터에 반영 되도록 확인 해야 합니다.  <br/> |
|Office 365 IP 범위를 필터링 합니다.  <br/> [!CAUTION] Not 권장
|**높은:** 고객 정의 된 Office 365 IP 접두사를 기반으로 경로 필터링 합니다.  <br/> |고객 월별 업데이트에 대 한 강력한 변경 관리 프로세스를 구현 해야 합니다.  <br/> [!CAUTION]이 솔루션에는 중요 한 지속적인 변경 해야합니다. 변경 된 시간이 될 가능성이 서비스 중단에에서 구현 되지 않았습니다.   |

Office 365에 연결 Azure ExpressRoute를 사용 하 여 기반으로 Office 365 끝점이 배포 된 네트워크를 표시 하는 특정 IP 서브넷의 BGP 광고 합니다. 고객은 전역의 특성으로 인해 Office 365 및 Office 365를 구성 하는 서비스의 수, 해당 네트워크에 모임 참가자가 수락 광고를 관리 하 해야 하는 경우가 많습니다. 관심이 있다면 사용자의 환경에 보급 한 접두사의 번호로, [BGP 커뮤니티](https://support.office.com/article/Using-BGP-communities-in-ExpressRoute-for-Office-365-scenarios-preview-9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099) 기능을 사용 하면 특정 Office 365 서비스 집합을 광고를 필터링 할 수 있습니다. 이 기능은 미리 보기에 포함 되었습니다.
  
Microsoft에서 들리는 BGP 경로 광고를 관리 하는 방법에 관계 없이 비교 만으로는 인터넷 회로 통해 Office 365에 연결 하는 Office 365 서비스에 대 한 모든 특수 노출 얻을 수 없습니다. Microsoft에는 동일한 보안과 규정 준수, 고객을 사용 하 여 Office 365에 연결 하는 회로의 유형에 관계 없이 성능 수준을 유지 관리 합니다.
  
### <a name="security"></a>보안

유지 하는 공용 ExpressRoute 및 Microsoft 피어 링, 간에 이동 하는 연결에 대 한 직접 네트워크 및 보안 경계 컨트롤을 및 Office 365 서비스에서 연결을 포함 하는 것이 좋습니다. 보안 제어 기능을 Microsoft의 네트워크에 네트워크에서 아웃 바운드 출장 뿐 아니라 네트워크에 Microsoft의 네트워크에서 인바운드 네트워크 요청에 대 한 전체에 있어야 합니다.
  
#### <a name="outbound-from-customer-to-microsoft"></a>Microsoft 고객에 게 서 아웃 바운드
  
Office 365에 연결 하는 컴퓨터는 인터넷 이나 ExpressRoute 회로 통해 연결이 수행 되는지 여부에 관계 없이 끝점의 동일한 집합에 연결 합니다. 사용 중인 회로 관계 없이 일반 인터넷 대상 보다 더 신뢰할 수 있는으로 Office 365 서비스를 처리 하는 것이 좋습니다. 아웃 바운드 보안 컨트롤 해야 하는 포트 및 프로토콜을 노출 줄이고 지속적인 유지 관리를 최소화할에 초점을 맞춥니다. 필요한 포트 정보는 [Office 365 끝점](https://aka.ms/o365endpoints) 참조 (영문) 문서에서 사용할 수 있습니다.
  
추가 된 컨트롤에 대 한 FQDN 수준 프록시 인프라 내에서 필터링을 제한 하거나 인터넷 또는 Office 365에 대 한 대상으로 하는 일부 또는 모든 네트워크 요청을 검사 합니다. 사용할 수 있습니다. 보다 강력한 변경 관리 및 게시 된 [Office 365 끝점](https://aka.ms/o365endpoints)에 변경 내용 추적 기능이 해제 되 고 Office 365 제품 여지가으로 Fqdn 목록이 유지 관리이 필요 합니다.
  
> [!CAUTION]
> Office 365로 아웃 바운드 보안을 관리 하는 IP 접두사에만 의존 하지는 것이 좋습니다.

|**옵션**|**복잡성**|**컨트롤을 변경 합니다.**|
|:-----|:-----|:-----|
|제한 없음  <br/> |**낮음:** 고객은 Microsoft에 대 한 아웃 바운드 무제한 액세스를 허용합니다.  <br/> |없음  <br/> |
|포트 제한  <br/> |**낮음:** 고객 포트를 예상된 하 여 Microsoft에 아웃 바운드 액세스를 제한합니다.  <br/> |자주 사용 하지 않는 합니다.  <br/> |
|FQDN 제한 사항  <br/> |**높은:** 고객 게시 된 Fqdn에 따라 Office 365로 아웃 바운드 액세스를 제한 합니다.  <br/> |월별 변경 합니다.  <br/> |

#### <a name="inbound-from-microsoft-to-customer"></a>고객에 게 Microsoft에서 인바운드
  
네트워크에 대 한 연결을 시작 하는 Microsoft를 필요로 하는 여러 선택 사항 경우도 있습니다.
  
- 로그인에 대 한 암호 유효성 검사 하는 동안 ADFS 합니다.

- [Exchange Server 하이브리드 배포](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx)합니다.

- 온-프레미스 호스트에는 Exchange Online 테 넌 트에서 메일입니다.

- SharePoint Online 메일 SharePoint Online에서 온-프레미스 호스트에 보냅니다.

- [SharePoint 하이브리드 검색 페더레이션](https://technet.microsoft.com/library/dn197174.aspx)합니다.

- [SharePoint 하이브리드 BCS](https://technet.microsoft.com/library/dn197239.aspx )합니다.

- [비즈니스 하이브리드에 대 한 Skype](https://technet.microsoft.com/en-us/library/jj205403.aspx) 및/또는 [비즈니스 페더레이션 위한 Skype](https://technet.microsoft.com/library/skype-for-business-online-federation-and-public-im-conectivity.aspx)합니다.

- [비즈니스 클라우드 커넥터에 대 한 Skype](https://technet.microsoft.com/library/mt605227.aspx )합니다.

복잡성을 줄이기 위한 ExpressRoute 회로 대화 하는 대신 인터넷 회로 통해 이러한 연결을 허용 하는 것이 좋습니다. 규정 준수 또는 성능 요구를 ExpressRoute 회로 통해 이러한 인바운드 연결을 수락 해야 하도록 지시를 방화벽 또는 역방향 프록시를 사용 하 여 승인 된 연결 범위를 지정 하는 것이 좋습니다. 오른쪽 Fqdn 및 IP 접두사를 파악 하는 [Office 365 끝점](https://aka.ms/o365endpoints) 을 사용할 수 있습니다.
  
### <a name="compliance"></a>규정 준수

사용해 준수 컨트롤을 사용 하는 라우팅 경로에 의존 하지 않습니다. 여부 하면 Office 365 서비스를 통해에 연결 된 ExpressRoute 또는 인터넷 회로 관계 없이 준수 컨트롤 변경 되지 않습니다. 다양 한 규정 준수 및 조직의 요구를 충족 하는 것에 대 한 최선책 파악 하려면 Office 365에 대 한 보안 인증 수준을 검토 해야 합니다.
  
짧은 링크를 다시 사용할 수는 다음과 같습니다.[https://aka.ms/manageexpressroute365](https://aka.ms/manageexpressroute365)
  
## <a name="related-topics"></a>관련 항목

[콘텐츠 배달 네트워크](content-delivery-networks.md)
  
[Office 365 URL 및 IP 주소 범위](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Office 365 끝점 관리](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Office 365 교육에 대 한 azure ExpressRoute](https://channel9.msdn.com/series/aer)
