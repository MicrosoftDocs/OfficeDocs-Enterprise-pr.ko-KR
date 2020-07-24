---
title: Office 365 미국 정부 GCC 높은 끝점
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/09/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid: MET150
ms.assetid: cbd2369c-fd96-464c-bf48-c99826b459ee
description: 조직에서 Office 365을 사용 하 고 네트워크의 컴퓨터에서 인터넷에 연결 하지 못하도록 제한 하는 경우 아래에서 아웃 바운드 허용 목록에 포함 해야 하는 끝점 (Fqdn, 포트, Url, IPv4 및 IPv6 주소 범위)을 확인 하 여 컴퓨터에서 Office 365를 정상적으로 사용할 수 있는지 확인 합니다.
hideEdit: true
ms.openlocfilehash: a22a73e970228cc873410df916a071d89a74ba02
ms.sourcegitcommit: c1a1b028195342affe0f3367db4e79c42429582a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/23/2020
ms.locfileid: "45387747"
---
# <a name="office-365-us-government-gcc-high-endpoints"></a>Office 365 미국 정부 GCC 높은 끝점

 *적용 대상: Office 365 관리자*

Office 365를 사용 하려면 인터넷에 연결 해야 합니다. 아래 끝점은 Office 365 미국 정부 GCC High 요금제만 사용 하는 고객에 게 연결할 수 있어야 합니다.
  
 **Office 365 끝점:** [전 세계(GCC 포함)](urls-and-ip-address-ranges.md) | [21vianet에서 운영하는 Microsoft Office 365](urls-and-ip-address-ranges-21vianet.md)  | [Microsoft Office 365 Germany](office-365-germany-endpoints.md)   |  [Office 365 U.S. Government DoD](office-365-u-s-government-dod-endpoints.md) | *Office 365 U.S. Government GCC High* |
  
|||
|:-----|:-----|
|**마지막 업데이트:** 2020년 7월 9일 - ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [로그 구독 변경](https://endpoints.office.com/version/USGOVGCCHigh?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) <br/> |**다운로드:** [JSON 형식의](https://endpoints.office.com/endpoints/USGOVGCCHigh?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) 전체 목록 <br/> |

 [Office 365 끝점 관리](managing-office-365-endpoints.md) 를 시작 하 여이 데이터를 사용 하 여 네트워크 연결을 관리 하기 위한 권장 사항을 이해 합니다. 끝점 데이터는 각 월의 시작 부분에서 새 IP 주소와 30 일이 지난 후에 게시 된 Url을 사용 하 여 업데이트 됩니다. 이렇게 하면 새 연결이 필요 하기 전에 아직 자동화 된 업데이트를 통해 프로세스를 완료할 수 있습니다. 지원 되는 에스컬레이션, 보안 문제 또는 기타 즉각적인 운영 요구 사항을 해결 해야 하는 경우에는 한 달 동안에도 끝점이 업데이트 될 수 있습니다. 아래이 페이지에 표시 된 데이터는 모두 REST 기반 웹 서비스에서 생성 됩니다. 스크립트나 네트워크 장치를 사용 하 여이 데이터에 액세스 하는 경우에는 [웹 서비스로](office-365-ip-web-service.md) 직접 이동 해야 합니다.

아래의 끝점 데이터는 사용자의 컴퓨터에서 Microsoft Office 365에 연결할 때의 요구 사항을 나열합니다. 이는 하이브리드 또는 인바운드 네트워크 연결이라 불리며 Microsoft에서 고객 네트워크로의 네트워크 연결을 포함하지 않습니다.

끝점은 네 가지 서비스 영역으로 그룹화됩니다. 첫 번째 세 개의 서비스 영역은 연결용으로 개별 선택할 수 있습니다. 네 번째 서비스 영역(Microsoft 365 Common 및 Office 라고 함)은 일반적인 종속성이 있으며 항상 네트워크에 연결된 상태여야 합니다.

표시된 데이터 열:

- **ID**: 행의 ID 번호는 끝점 집합이라고도 합니다. 이 ID는 해당 끝점 집합에 대한 웹 서비스에서 반환되는 것과 동일합니다.

- **범주**: 끝점 집합이 "최적화", "허용" 또는 "기본"으로 분류되는지 여부를 보여줍니다. [https://aka.ms/pnc](https://aka.ms/pnc)에서 이러한 범주 및 관리에 대한 지침을 읽을 수 있습니다. 이 열에서도 네트워크에 연결하는 데 필요한 끝점 집합을 나열합니다. 네트워크에 연결하는 데 필요하지 않은 끝점 집합의 경우, 이 필드에서 메모를 제공해 끝점 집합이 차단되면 어떤 기능을 사용할 수 없는지 표시해줍니다. 전체 서비스 영역을 제외하는 경우, 필요한 것으로 나열된 끝점 집합은 연결이 필요하지 않습니다.

- **ER**: Office 365 경로 접두사를 사용한 Azure express에서 끝점 집합이 지원 되는 경우에는이를 **예로** 들 수 있습니다. 표시 되는 경로 접두사를 포함 하는 BGP 커뮤니티는 나열 된 서비스 영역에 맞게 정렬 됩니다. ER가 **No**이면이 끝점 집합에 대해 express가 지원 되지 않습니다. 그러나 ER가 **no**인 끝점 집합에 대해 경로가 보급 되지 않는다고 가정 해서는 안 됩니다. Azure AD Connect를 사용 하려는 경우 [특별 고려 사항 섹션](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-instances#microsoft-azure-government) 을 읽어 적절 한 Azure ad connect 구성이 있는지 확인 합니다.

- **주소**: 끝점 집합의 FQDN 또는 와일드카드 도메인 이름 및 IP 주소 범위를 보여줍니다. IP 주소 범위가 CIDR 형식이며 특정 네트워크에서 여러 개의 개별 IP 주소를 포함할 수 있다는 점에 유의하시기 바랍니다.
 
- **포트**: 주소와 결합하여 네트워크 끝점을 이루는 TCP 또는 UDP 포트를 나열합니다. 다른 포트도 나열되어 있으면, IP 주소 범위에서 몇 가지 중복되는 경우도 있습니다.
 
[!INCLUDE [Office 365 U.S. Government GCC High endpoints](./includes/office-365-u.s.-government-gcc-high-endpoints.md)]

이 표에 대한 참고 사항

- SCC (보안 및 준수 센터)는 Office 365 용 Azure Express를 지원 합니다. 이는 보고, 감사, Advanced eDiscovery, 통합 DLP 및 데이터 거 버 넌 스와 같은 SCC를 통해 제공 되는 많은 기능에도 적용 됩니다. 두 가지 특정 기능인 PST 가져오기 및 eDiscovery 내보내기에서는 현재 Azure Blob Storage에 대 한 종속성으로 인해 Office 365 경로 필터만 사용 하는 Azure Express를 지원 하지 않습니다. 이러한 기능을 사용 하려면 azure 공용 경로 필터를 사용한 Azure Express 주소나 인터넷 연결을 포함 하는 지원 되지 않는 Azure 연결 옵션을 통해 Azure Blob Storage에 대 한 별도의 연결이 필요 합니다. 이러한 두 기능에 대 한 이러한 연결을 평가 해야 합니다. Office 365 Information Protection 팀은 이러한 기능에 대 한 Office 365 경로 필터로 제한 되는, Office 365에 대 한 Azure Express를 지원 하기 위해 현재 이러한 제한을 확인 하 고 있습니다.

- 사용자가 엔터프라이즈 응용 프로그램에 대해 Microsoft 365 앱을 시작 하 고 문서를 편집 하는 데 필요한 Microsoft 365 앱 for enterprise 용 추가 끝점이 나열 되어 있지 않습니다. 선택적 끝점은 Microsoft 데이터 센터에서 호스트 되며, 고객 데이터가 처리, 전송 또는 저장 되지 않습니다. 이러한 끝점에 대 한 사용자 연결을 기본 인터넷 송신 주변으로 보내는 것이 좋습니다.

