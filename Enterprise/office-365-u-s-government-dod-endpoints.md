---
title: Office 365 미국 정부 DoD 끝점
ms.author: laurawi
author: LauraWi
manager: laurawi
ms.date: 01/02/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
search.appverid:
- OGA150
- OGC150
- OGD150
- MOE150
ms.assetid: 5d7dce60-4892-4b58-b45e-ee42fe8a907f
description: '요약: Office 365을 사용 하려면 인터넷에 연결 해야 합니다. 아래 끝점은 Office 365 U.S. 정부 DoD 요금제만 사용 하는 고객에 게 연결할 수 있어야 합니다.'
hideEdit: true
ms.openlocfilehash: 3f603ceb8211a46dec43d5b06677b6a316b4fefa
ms.sourcegitcommit: f9888d1c27e38d3c489a0cbed7684a2e67c3afbd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/07/2020
ms.locfileid: "40951528"
---
# <a name="office-365-us-government-dod-endpoints"></a>Office 365 미국 정부 DoD 끝점

*적용 대상: Office 365 관리자*

 **요약:** Office 365를 사용 하려면 인터넷에 연결 해야 합니다. 아래 끝점은 Office 365 U.S. 정부 DoD 요금제만 사용 하는 고객에 게 연결할 수 있어야 합니다.
  
> [!NOTE]
> Microsoft는 이 페이지에 있는 IP 주소와 FQDN 항목을 위해 REST 기반 웹 서비스를 출시했습니다. 이 새로운 서비스는 방화벽 및 프록시 서버와 같은 네트워크 경계 장치를 구성하고 업데이트하는 작업을 도와줍니다. 끝점, 최신 버전의 목록 또는 특정 변경 사항의 목록을 다운로드할 수 있습니다. 이 서비스는 2018년 10월 2일부터 사용되지 않는 이 페이지에 연결된 XML 문서를 대체합니다. 새로운 서비스를 실행하려면 [웹 서비스](office-365-ip-web-service.md)로 이동하세요.
  
 **Office 365 끝점:** [전 세계(GCC 포함)](urls-and-ip-address-ranges.md) | [21vianet에서 운영하는 Microsoft Office 365](urls-and-ip-address-ranges-21vianet.md)  | [Microsoft Office 365 Germany](office-365-germany-endpoints.md)  |  *Office 365 U.S. Government DoD* | [Office 365 U.S. Government GCC High](office-365-u-s-government-gcc-high-endpoints.md) |
  
|||
|:-----|:-----|
|**마지막 업데이트:** 01/02/2020- ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [변경 로그 구독](https://endpoints.office.com/version/USGOVDoD?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) <br/> |**다운로드:** [JSON 형식의](https://endpoints.office.com/endpoints/USGOVDoD?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) 전체 목록 <br/> |
   
 [Office 365 끝점 관리](managing-office-365-endpoints.md) 를 시작 하 여이 데이터를 사용 하 여 네트워크 연결을 관리 하기 위한 권장 사항을 이해 합니다. 끝점 데이터는 각 월의 시작 부분에서 새 IP 주소와 30 일이 지난 후에 게시 된 Url을 사용 하 여 업데이트 됩니다. 이렇게 하면 새 연결이 필요 하기 전에 아직 자동화 된 업데이트를 통해 프로세스를 완료할 수 있습니다. 지원 되는 에스컬레이션, 보안 문제 또는 기타 즉각적인 운영 요구 사항을 해결 해야 하는 경우에는 한 달 동안에도 끝점이 업데이트 될 수 있습니다. 아래이 페이지에 표시 된 데이터는 모두 REST 기반 웹 서비스에서 생성 됩니다. 스크립트나 네트워크 장치를 사용 하 여이 데이터에 액세스 하는 경우에는 [웹 서비스로](office-365-ip-web-service.md) 직접 이동 해야 합니다.

끝점 데이터 아래에는 사용자 컴퓨터에서 Office 365로의 연결을 위한 요구 사항이 나열 되어 있습니다. Microsoft 로부터의 네트워크 연결은 하이브리드 또는 인바운드 네트워크 연결 이라고 하는 고객 네트워크에는 포함 되지 않습니다. 자세한 내용은 [웹 서비스에 포함 되지 않은 추가 끝점](additional-office365-ip-addresses-and-urls.md)을 참조 하십시오. 

끝점은 네 가지 서비스 영역으로 그룹화됩니다. 첫 번째 세 개의 서비스 영역은 연결용으로 개별 선택할 수 있습니다. 네 번째 서비스 영역(Microsoft 365 Common 및 Office 라고 함)은 일반적인 종속성이 있으며 항상 네트워크에 연결된 상태여야 합니다.

표시된 데이터 열:

- **ID**: 행의 ID 번호는 끝점 집합이라고도 합니다. 이 ID는 해당 끝점 집합에 대한 웹 서비스에서 반환되는 것과 동일합니다.

- **범주**: 끝점 집합이 "최적화", "허용" 또는 "기본"으로 분류되는지 여부를 보여줍니다. [https://aka.ms/pnc](https://aka.ms/pnc)에서 이러한 범주 및 관리에 대한 지침을 읽을 수 있습니다. 이 열에서도 네트워크에 연결하는 데 필요한 끝점 집합을 나열합니다. 네트워크에 연결하는 데 필요하지 않은 끝점 집합의 경우, 이 필드에서 메모를 제공해 끝점 집합이 차단되면 어떤 기능을 사용할 수 없는지 표시해줍니다. 전체 서비스 영역을 제외하는 경우, 필요한 것으로 나열된 끝점 집합은 연결이 필요하지 않습니다.

- **ER**: Office 365 경로 접두사를 사용한 Azure express에서 끝점 집합이 지원 되는 경우에는이를 **예로** 들 수 있습니다. 표시 되는 경로 접두사를 포함 하는 BGP 커뮤니티는 나열 된 서비스 영역에 맞게 정렬 됩니다. ER가 **No**이면이 끝점 집합에 대해 express가 지원 되지 않습니다. 그러나 ER가 **no**인 끝점 집합에 대해 경로가 보급 되지 않는다고 가정 해서는 안 됩니다. Azure AD Connect를 사용 하려는 경우 [특별 고려 사항 섹션](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-instances#microsoft-azure-government) 을 읽어 적절 한 Azure ad connect 구성이 있는지 확인 합니다.

- **주소**: 끝점 집합의 FQDN 또는 와일드카드 도메인 이름 및 IP 주소 범위를 보여줍니다. IP 주소 범위가 CIDR 형식이며 특정 네트워크에서 여러 개의 개별 IP 주소를 포함할 수 있다는 점에 유의하시기 바랍니다.
 
- **포트**: 네트워크 끝점을 형성하기 위해 주소와 결합된 TCP 또는 UDP 포트를 나열합니다. 다른 포트가 나열된 IP 주소 범위에서 일부 중복을 볼 수 있습니다.
 
[!INCLUDE [Office 365 U.S. Government DoD endpoints](./includes/office-365-u.s.-government-dod-endpoints.md)]
  
이 표에 대한 참고 사항

- SCC (보안 및 준수 센터)는 Office 365 용 Azure Express를 지원 합니다. 이는 보고, 감사, Advanced eDiscovery, 통합 DLP 및 데이터 거 버 넌 스와 같은 SCC를 통해 제공 되는 많은 기능에도 적용 됩니다. 두 가지 특정 기능인 PST 가져오기 및 eDiscovery 내보내기에서는 현재 Azure Blob Storage에 대 한 종속성으로 인해 Office 365 경로 필터만 사용 하는 Azure Express를 지원 하지 않습니다. 이러한 기능을 사용 하려면 azure 공용 경로 필터를 사용한 Azure Express 주소나 인터넷 연결을 포함 하는 지원 되지 않는 Azure 연결 옵션을 통해 Azure Blob Storage에 대 한 별도의 연결이 필요 합니다. 이러한 두 기능에 대 한 이러한 연결을 평가 해야 합니다. Office 365 Information Protection 팀은 이러한 기능에 대 한 Office 365 경로 필터로 제한 되는, Office 365에 대 한 Azure Express를 지원 하기 위해 현재 이러한 제한을 확인 하 고 있습니다.

- 사용자가 Office 365 ProPlus 응용 프로그램을 시작 하 고 문서를 편집 하는 데 필요 하지 않으며 나열 되지 않고 Office 365 ProPlus에 대 한 추가 선택적 끝점이 있습니다. 선택적 끝점은 Microsoft 데이터 센터에서 호스트 되며, 고객 데이터가 처리, 전송 또는 저장 되지 않습니다. 이러한 끝점에 대 한 사용자 연결을 기본 인터넷 송신 주변으로 보내는 것이 좋습니다.
