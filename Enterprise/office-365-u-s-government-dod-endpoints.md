---
title: Office 365 미국 정부 DoD 끝점
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 8/13/2018
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
ms.openlocfilehash: 3faca62176b1467829f0333b76a57ce0d5124a96
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541924"
---
# <a name="office-365-us-government-dod-endpoints"></a>Office 365 미국 정부 DoD 끝점

*적용 대상: Office 365 관리*

 **요약:** Office 365를 사용 하려면 인터넷에 연결을 해야 합니다. 아래 끝점 Office 365 미국 정부 DoD 계획만을 사용 하는 고객을 위한 연결할 수 있어야 합니다.
  
> [!NOTE]
> Microsoft는 IP 주소와 FQDN 항목을이 페이지에 대 한 REST 기반 웹 서비스를 개발 하 고 있습니다. 이 새로운 서비스를 구성 하 고 방화벽 및 프록시 서버와 같은 네트워크 경계 장치를 업데이트 하는데 도움이 됩니다. 끝점, 목록 또는 특정 변경의 현재 버전의 목록을 다운로드할 수 있습니다. 이 서비스는 XML 문서, RSS 피드, IP 주소 및 FQDN 항목을이 페이지에 결국 대체할 수 있습니다. 이 새로운 서비스를 실행 하려면 [웹 서비스](managing-office-365-endpoints.md#webservice)로 이동 합니다.
  
 **Office 365 끝점:** [Worldwide (GCC 포함)](urls-and-ip-address-ranges.md)  |  [21 Vianet 하 여 office 365 작동할](urls-and-ip-address-ranges-21vianet.md)  | [Office 365 독일](office-365-germany-endpoints.md) | *Office 365 미국 정부 DoD* | [Office 365 미국 정부 GCC 높음](office-365-u-s-government-gcc-high-endpoints.md) |
  
|||
|:-----|:-----|
|8/1/2018 **마지막 업데이트 날짜:** - ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [변경 로그 구독](https://aka.ms/dodendpointrss) <br/> |**다운로드:** [XML](https://aka.ms/usdodendpoints) 형식의 전체 목록은 <br/> |
   
 이 데이터를 사용 하 여 네트워크 연결을 관리 하기 위한 권장 사항 이해 하려면 [Office 365 관리 끝점](managing-office-365-endpoints.md) 으로 시작 합니다. 새 IP 주소 및 활성화 되 고 전 30 일 게시 된 Url 사용 하 여 각 월의 시작 부분에 끝점 데이터가 업데이트 됩니다. 이 고객에 게 하지 않는 아직 새 연결이 필요 하기 전에 해당 프로세스를 완료 하려면 업데이트 자동 수 있습니다. 주소 지원 에스컬레이션, 보안 문제 또는 기타 즉시 운영 요구 사항에 필요한 경우에 끝점 달 하는 동안 업데이트 될 수 있습니다. 이 페이지 아래에 표시 되는 데이터는 모든 REST 기반 웹 서비스에서 생성 됩니다. 스크립트 또는 네트워크 장치를 사용 하 여이 데이터에 액세스 하는, [웹 서비스](managing-office-365-endpoints.md#webservice) 에 직접 서 해야 합니다.

아래의 끝점 데이터 연결을 사용자의 컴퓨터에서 Office 365에 대 한 요구 사항을 나열합니다. 고객 네트워크, 하이브리드 라고도 함 또는 인바운드 네트워크 연결에 Microsoft에서 네트워크 연결을 포함 하지는 않습니다.

끝점을 4 개의 서비스 영역으로 그룹화 됩니다. 처음 세 서비스 영역 선택 될 수 독립적으로 연결 합니다. 네번째 서비스 영역 (Microsoft 365 일반적이 고 Office Online 라고 함)는 일반적인 의존 관계 이며 항상 네트워크 연결에 있어야 합니다.

데이터 열이 표시 됩니다.

- **ID**: 끝점 집합 라고도 하는 행의 ID 번호입니다. 이 ID는 끝점 집합에 대 한 웹 서비스에 의해 반환 되는 동일 합니다.

- **범주**: 끝점 집합 "최적화", "허용" 또는 "Default"로 분류 되는지 여부를 표시 합니다. 이러한 범주 및 관리에 그 중에 대 한 지침에 대 한 읽을 수 있는 [http://aka.ms/pnc](http://aka.ms/pnc)합니다. 이 열에도 끝점으로 설정 하는 네트워크 연결이 필요가 나열 합니다. 없어도 네트워크에 연결 하는 끝점 집합에 대 한 끝점 집합 차단 되 면 기능에 설명 누락 된 것을 나타내기 위해이 필드에 대 한 정보를 제공 합니다. 전체 서비스 영역을 제외 하는 경우 필요에 따라 나열 하는 끝점 집합 연결이 필요 하지 않습니다.

- **ER**:이 방법이 **Yes** 끝점 집합 경로 접두사를 Office 365와 Azure ExpressRoute을 통해 지원 됩니다. 표시 된 경로 접두사를 포함 하는 BGP 커뮤니티 나열 된 서비스 영역에 맞춥니다. ER **No**때 즉, ExpressRoute이 끝점 집합에 대 한 지원 되지 않습니다. 그러나 해당 간주할 수는 없습니다 ER **No**가 한 끝점 집합에 대 한 경로 되지는 보급는 합니다. Azure AD 연결을 사용 하려는 경우 적절 한 해야 [특별 고려 사항 섹션](https://docs.microsoft.com/azure/active-directory/connect/active-directory-AADconnect-instances#microsoft-azure-government-cloud) 읽고 Azure AD 연결 구성 합니다.

- **주소**: Fqdn 또는 와일드 카드 도메인 이름 및 끝점 집합에 대 한 IP 주소 범위를 나열 합니다. 참고 IP 주소 범위는 CIDR 형식에 있으며 지정 된 네트워크에서 많은 개별 IP 주소를 포함 될 수 있습니다.
 
- **포트**: 네트워크 끝점을 형성 하는 주소와 결합 되는 TCP 또는 UDP 포트를 나열 합니다. IP 주소 범위에서 일부 중복 되는 경우도 있습니다 있는 서로 다른 포트를 나열 합니다.
 
[!INCLUDE [Office 365 U.S. Government DoD endpoints](./includes/office-365-u.s.-government-dod-endpoints.md)]
  
이 표에 대한 참고 사항

- 보안 및 규정 준수 센터 SCC ()에 Office 365 용 Azure ExpressRoute에 대 한 지원을 제공 합니다. 보고, 감사, 고급 eDiscovery, DLP 통합 및 데이터 관리 방식 등 소스 코드 제어를 통해 노출 다양 한 기능에 대 한도 마찬가지입니다. 현재 두 특정 기능 PST 가져오기 및 내보내기, eDiscovery Azure Blob 저장소의 의존성 때문에 Office 365 경로 필터와 함께 Azure ExpressRoute를 지원 하지 않습니다. 이러한 기능을 사용 하려면 인터넷에 연결 또는 Azure ExpressRoute Azure 공용 경로 필터와 함께 포함 하는 모든 지원 가능한 Azure 연결 옵션을 사용 하 여 Azure Blob 저장소에 대 한 별도 연결을 해야 합니다. 이러한 기능을 모두에 대 한 이러한 연결 설정 평가 해야 합니다. Office 365 정보 보호 팀은이 제한의를 알고 있으며 이러한 기능을 모두에 대 한 제한으로 Office 365에 대 한 지원 Azure ExpressRoute에 대 한 Office 365 경로 필터를 가져올 적극적으로 작동 합니다.

- 나열 되지 않은 하 고 사용자가 Office 365 ProPlus 응용 프로그램을 실행 하 고 문서를 편집할 수에 필요 하지 않은 Office 365 ProPlus에 대 한 추가 선택적 끝점 있습니다. 선택적 끝점 Microsoft 데이터 센터에서 호스팅되는 하 고 수행 하지 처리, 전송, 또는 고객 데이터를 저장 합니다. 이러한 끝점에 대 한 사용자 연결 기본 인터넷 탈출 경계를 이동 하는 것이 좋습니다.
