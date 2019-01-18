---
title: Office 365 미국 정부 DoD 끝점
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/17/2019
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- OGA150
- OGC150
- OGD150
- MOE150
ms.assetid: 5d7dce60-4892-4b58-b45e-ee42fe8a907f
description: '요약: Office 365에서 인터넷에 연결을 해야합니다. 아래 끝점 Office 365 미국 정부 DoD 계획만을 사용 하는 고객을 위한 연결할 수 있어야 합니다.'
hideEdit: true
ms.openlocfilehash: 87577b62e4180d74652e973e2a4644536bbf4cea
ms.sourcegitcommit: 0c4f50aa55699b8390038efbb8b50dbe10f3eefe
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/17/2019
ms.locfileid: "28723395"
---
# <a name="office-365-us-government-dod-endpoints"></a>Office 365 미국 정부 DoD 끝점

*적용 대상: Office 365 관리*

 **요약:** Office 365를 사용 하려면 인터넷에 연결을 해야 합니다. 아래 끝점 Office 365 미국 정부 DoD 계획만을 사용 하는 고객을 위한 연결할 수 있어야 합니다.
  
> [!NOTE]
> Microsoft는 이 페이지에 있는 IP 주소와 FQDN 항목을 위해 REST 기반 웹 서비스를 출시했습니다. 이 새로운 서비스는 방화벽 및 프록시 서버와 같은 네트워크 경계 장치를 구성하고 업데이트하는 작업을 도와줍니다. 끝점, 최신 버전의 목록 또는 특정 변경 사항의 목록을 다운로드할 수 있습니다. 이 서비스는 2018년 10월 2일부터 사용되지 않는 이 페이지에 연결된 XML 문서를 대체합니다. 새로운 서비스를 실행하려면 [웹 서비스](office-365-ip-web-service.md)로 이동하세요.
  
 **Office 365 끝점:** [전 세계(GCC 포함)](urls-and-ip-address-ranges.md) | [21vianet에서 운영하는 Microsoft Office 365](urls-and-ip-address-ranges-21vianet.md)  | [Microsoft Office 365 Germany](office-365-germany-endpoints.md)  |  *Office 365 U.S. Government DoD* | [Office 365 U.S. Government GCC High](office-365-u-s-government-gcc-high-endpoints.md) |
  
|||
|:-----|:-----|
|01/17/2019 **마지막 업데이트 날짜:** - ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [변경 로그 구독](https://endpoints.office.com/version/USGOVDoD?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) <br/> |**다운로드:** [JSON](https://endpoints.office.com/endpoints/USGOVDoD?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) 형식의 전체 목록은 <br/> |
   
 이 데이터를 사용 하 여 네트워크 연결을 관리 하기 위한 권장 사항 이해 하려면 [Office 365 관리 끝점](managing-office-365-endpoints.md) 으로 시작 합니다. 새 IP 주소 및 활성화 되 고 전 30 일 게시 된 Url 사용 하 여 각 월의 시작 부분에 끝점 데이터가 업데이트 됩니다. 이 사용 하지 않도록 아직 새 연결이 필요 하기 전에 해당 프로세스를 완료 하려면 업데이트 자동 고객 수 있습니다. 주소 지원 에스컬레이션, 보안 문제 또는 기타 즉시 운영 요구 사항에 필요한 경우에 끝점 달 하는 동안 업데이트 될 수 있습니다. 이 페이지 아래에 표시 되는 데이터는 모든 REST 기반 웹 서비스에서 생성 됩니다. 스크립트 또는 네트워크 장치를 사용 하 여이 데이터에 액세스 하는, [웹 서비스](office-365-ip-web-service.md) 에 직접 서 해야 합니다.

아래의 끝점 데이터는 사용자의 컴퓨터에서 Microsoft Office 365에 연결할 때의 요구 사항을 나열합니다. 이는 하이브리드 또는 인바운드 네트워크 연결이라 불리며 Microsoft에서 고객 네트워크로의 네트워크 연결을 포함하지 않습니다.

끝점은 네 가지 서비스 영역으로 그룹화됩니다. 첫 번째 세 개의 서비스 영역은 연결용으로 개별 선택할 수 있습니다. 네 번째 서비스 영역(Microsoft 365 Common 및 Office Online이라고 함)은 일반적인 종속성이 있으며 항상 네트워크에 연결된 상태여야 합니다.

표시된 데이터 열:

- **ID**: 행의 ID 번호는 끝점 집합이라고도 합니다. 이 ID는 해당 끝점 집합에 대한 웹 서비스에서 반환되는 것과 동일합니다.

- **범주**: 끝점 집합이 "최적화", "허용" 또는 "기본"으로 분류되는지 여부를 보여줍니다. [http://aka.ms/pnc](http://aka.ms/pnc)에서 이러한 범주 및 관리에 대한 지침을 읽을 수 있습니다. 이 열에서도 네트워크에 연결하는 데 필요한 끝점 집합을 나열합니다. 네트워크에 연결하는 데 필요하지 않은 끝점 집합의 경우, 이 필드에서 메모를 제공해 끝점 집합이 차단되면 어떤 기능을 사용할 수 없는지 표시해줍니다. 전체 서비스 영역을 제외하는 경우, 필요한 것으로 나열된 끝점 집합은 연결이 필요하지 않습니다.

- **ER**:이 방법이 **Yes** 끝점 집합 경로 접두사를 Office 365와 Azure ExpressRoute을 통해 지원 됩니다. 표시 된 경로 접두사를 포함 하는 BGP 커뮤니티 나열 된 서비스 영역에 맞춥니다. ER **No**때 즉, ExpressRoute이 끝점 집합에 대 한 지원 되지 않습니다. 그러나 해당 간주할 수는 없습니다 ER **No**가 한 끝점 집합에 대 한 경로 되지는 보급는 합니다. Azure AD 연결을 사용 하려는 경우 적절 한 해야 [특별 고려 사항 섹션](https://docs.microsoft.com/azure/active-directory/connect/active-directory-AADconnect-instances#microsoft-azure-government-cloud) 읽고 Azure AD 연결 구성 합니다.

- **주소**: 끝점 집합의 FQDN 또는 와일드카드 도메인 이름 및 IP 주소 범위를 보여줍니다. IP 주소 범위가 CIDR 형식이며 특정 네트워크에서 여러 개의 개별 IP 주소를 포함할 수 있다는 점에 유의하시기 바랍니다.
 
- **포트**: 네트워크 끝점을 형성하기 위해 주소와 결합된 TCP 또는 UDP 포트를 나열합니다. 다른 포트가 나열된 IP 주소 범위에서 일부 중복을 볼 수 있습니다.
 
[!INCLUDE [Office 365 U.S. Government DoD endpoints](./includes/office-365-u.s.-government-dod-endpoints.md)]
  
이 표에 대한 참고 사항

- 보안 및 규정 준수 센터 SCC ()에 Office 365 용 Azure ExpressRoute에 대 한 지원을 제공 합니다. 보고, 감사, 고급 eDiscovery, DLP 통합 및 데이터 관리 방식 등 소스 코드 제어를 통해 노출 다양 한 기능에 대 한도 마찬가지입니다. 현재 두 특정 기능 PST 가져오기 및 내보내기, eDiscovery Azure Blob 저장소의 의존성 때문에 Office 365 경로 필터와 함께 Azure ExpressRoute를 지원 하지 않습니다. 이러한 기능을 사용 하려면 인터넷에 연결 또는 Azure ExpressRoute Azure 공용 경로 필터와 함께 포함 하는 모든 지원 가능한 Azure 연결 옵션을 사용 하 여 Azure Blob 저장소에 대 한 별도 연결을 해야 합니다. 이러한 기능을 모두에 대 한 이러한 연결 설정 평가 해야 합니다. Office 365 정보 보호 팀은이 제한의를 알고 있으며 이러한 기능을 모두에 대 한 제한으로 Office 365에 대 한 지원 Azure ExpressRoute에 대 한 Office 365 경로 필터를 가져올 적극적으로 작동 합니다.

- 나열 되지 않은 하 고 사용자가 Office 365 ProPlus 응용 프로그램을 실행 하 고 문서를 편집할 수에 필요 하지 않은 Office 365 ProPlus에 대 한 추가 선택적 끝점 있습니다. 선택적 끝점 Microsoft 데이터 센터에서 호스팅되는 하 고 수행 하지 처리, 전송, 또는 고객 데이터를 저장 합니다. 이러한 끝점에 대 한 사용자 연결 기본 인터넷 탈출 경계를 이동 하는 것이 좋습니다.
