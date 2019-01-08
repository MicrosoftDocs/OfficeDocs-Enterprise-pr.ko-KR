---
title: Office 365 Germany 엔드포인트
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/07/2019
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365_Setup
search.appverid: MOE150
ms.assetid: 8a113a50-0071-4155-bb8e-eba5a8dbd4c8
description: 조직 Office 365를 사용 하 여 사용할 수 있는 네트워크에 있는 컴퓨터에서 인터넷에 연결할 수 없도록 제한 한 경우 아래를 찾을 수 (Fqdn, 포트, Url 및 IPv4 및 IPv6 주소 범위)는 끝점에 포함 되어야 하는 프로그램 아웃 바운드 허용 목록을 확인 하 여 컴퓨터에는 Office 365 성공적으로 사용할 수 있습니다.
hideEdit: true
ms.openlocfilehash: 05bbcb1cb4e6b90b3f7a61d84ae3488ce97245c2
ms.sourcegitcommit: e3fa9998321f6fa5d31217d107b672258993826e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/07/2019
ms.locfileid: "27746138"
---
# <a name="office-365-germany-endpoints"></a>Office 365 Germany 엔드포인트

 *적용 대상: Office 365 관리*

**요약:** Office 365를 사용 하려면 인터넷에 연결을 해야 합니다. 아래 끝점 **Office 365 독일** 계획만을 사용 하는 고객을 위한 연결할 수 있어야 합니다.
  
> [!NOTE]
> Microsoft는 이 페이지에 있는 IP 주소와 FQDN 항목을 위해 REST 기반 웹 서비스를 출시했습니다. 이 새로운 서비스는 방화벽 및 프록시 서버와 같은 네트워크 경계 장치를 구성하고 업데이트하는 작업을 도와줍니다. 끝점, 최신 버전의 목록 또는 특정 변경 사항의 목록을 다운로드할 수 있습니다. 이 서비스는 2018년 10월 2일부터 사용되지 않는 이 페이지에 연결된 XML 문서를 대체합니다. 새로운 서비스를 실행하려면 [웹 서비스](office-365-ip-web-service.md)로 이동하세요.
  
 **Office 365 끝점:** [전 세계(GCC 포함)](urls-and-ip-address-ranges.md)  | [21vianet에서 운영하는 Microsoft Office 365](urls-and-ip-address-ranges-21vianet.md)  | *Microsoft Office 365 Germany*  |  [Office 365 U.S. Government DoD](office-365-u-s-government-dod-endpoints.md) | [Office 365 U.S. Government GCC High](office-365-u-s-government-gcc-high-endpoints.md)  |
  
|||
|:-----|:-----|
|01/07/2019 **마지막 업데이트 날짜:** - ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [변경 로그 구독](https://endpoints.office.com/version/Germany?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) |**다운로드:** 모든 필수 및 선택 대상을 [JSON 형식](https://endpoints.office.com/endpoints/Germany?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) 목록에 다운로드합니다.  <br/> |

이 데이터를 사용 하 여 네트워크 연결을 관리 하기 위한 권장 사항 이해 하려면 [Office 365 관리 끝점](managing-office-365-endpoints.md) 으로 시작 합니다. 새 IP 주소 및 활성화 되 고 전 30 일 게시 된 Url 사용 하 여 각 월의 시작 부분에 끝점 데이터가 업데이트 됩니다. 이 사용 하지 않도록 아직 새 연결이 필요 하기 전에 해당 프로세스를 완료 하려면 업데이트 자동 고객 수 있습니다. 주소 지원 에스컬레이션, 보안 문제 또는 기타 즉시 운영 요구 사항에 필요한 경우에 끝점 달 하는 동안 업데이트 될 수 있습니다. [로그 구독을 변경](https://endpoints.office.com/version/Germany?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)하려면 항상 참조할 수 있습니다.

이 페이지 아래에 표시 되는 데이터는 모든 REST 기반 웹 서비스에서 생성 됩니다. 스크립트 또는 네트워크 장치를 사용 하 여이 데이터에 액세스 하는, [웹 서비스](office-365-ip-web-service.md) 에 직접 서 해야 합니다.

아래의 끝점 데이터는 사용자의 컴퓨터에서 Microsoft Office 365에 연결할 때의 요구 사항을 나열합니다. 이는 하이브리드 또는 인바운드 네트워크 연결이라 불리며 Microsoft에서 고객 네트워크로의 네트워크 연결을 포함하지 않습니다.

끝점은 네 가지 서비스 영역으로 그룹화됩니다. 첫 번째 세 개의 서비스 영역은 연결용으로 개별 선택할 수 있습니다. 네 번째 서비스 영역(Microsoft 365 Common 및 Office Online이라고 함)은 일반적인 종속성이 있으며 항상 네트워크에 연결된 상태여야 합니다.

표시된 데이터 열:

- **ID**: 행의 ID 번호는 끝점 집합이라고도 합니다. 이 ID는 해당 끝점 집합에 대한 웹 서비스에서 반환되는 것과 동일합니다.

- **범주**: 끝점 집합이 "최적화", "허용" 또는 "기본"으로 분류되는지 여부를 보여줍니다. [http://aka.ms/pnc](http://aka.ms/pnc)에서 이러한 범주 및 관리에 대한 지침을 읽을 수 있습니다. 이 열에서도 네트워크에 연결하는 데 필요한 끝점 집합을 나열합니다. 네트워크에 연결하는 데 필요하지 않은 끝점 집합의 경우, 이 필드에서 메모를 제공해 끝점 집합이 차단되면 어떤 기능을 사용할 수 없는지 표시해줍니다. 전체 서비스 영역을 제외하는 경우, 필요한 것으로 나열된 끝점 집합은 연결이 필요하지 않습니다.

- **ER**: Microsoft Azure ExpressRoute 및 Microsoft Office 365 경로 접두사에서 끝점 집합을 지원하는 경우 **예**로 설정되어 있습니다. 표시된 경로 접두사를 포함하는 BGP 커뮤니티를 나열된 서비스 영역과 맞춥니다. ER이 **아니요**인 경우는 ExpressRoute가 끝점 집합을 지원하지 않는다는 것을 의미합니다. 그러나 ER이 **아니요**라고 하여 끝점 집합에 보급되는 경로가 없다고 간주할 수는 없습니다.

- **주소**: 끝점 집합의 FQDN 또는 와일드카드 도메인 이름 및 IP 주소 범위를 보여줍니다. IP 주소 범위가 CIDR 형식이며 특정 네트워크에서 여러 개의 개별 IP 주소를 포함할 수 있다는 점에 유의하시기 바랍니다.
 
- **포트**: 주소와 결합하여 네트워크 끝점을 이루는 TCP 또는 UDP 포트를 나열합니다. 다른 포트도 나열되어 있으면, IP 주소 범위에서 몇 가지 중복되는 경우도 있습니다.

[!INCLUDE [Office 365 Germany endpoints](./includes/office-365-germany-endpoints.md)]

 

