---
title: 21Vianet에서 운영하는 Microsoft Office 365 URL 및 IP 주소 범위
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/08/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
search.appverid:
- GMA150
- GPA150
- GEA150
ms.assetid: 5c47c07d-f9b6-4b78-a329-bfdc1b6da7a0
f1.keywords:
- NOCSH
description: 이 문서는 중국의 21Vianet에서 운영하는 Microsoft Office 365에 적용됩니다. 이 문서는 21Vianet에서 운영하는 Microsoft Office 365에서 사용하는 URL 및 IP 주소 범위를 나열합니다.
hideEdit: true
ms.openlocfilehash: 7a28581d860f6c690b5d3fcf9317fae7946bae02
ms.sourcegitcommit: b2767740251b257bb5e66d056731c6c9e7f2677d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/08/2020
ms.locfileid: "46596957"
---
# <a name="urls-and-ip-address-ranges-for-office-365-operated-by-21vianet"></a>21Vianet에서 운영하는 Microsoft Office 365 URL 및 IP 주소 범위

 *적용 대상: 21vianet에서 운영하는 Microsoft Office 365 - Small Business Admin, 21Vianet에서 운영하는Microsoft Office 365 - 관리자*

**요약**: 다음 끝점(FQDN, 포트, URL, IPv4 및 IPv6 접두사)은 21 Vianet에서 운영하는 Microsoft Office 365에 적용되며, 이러한 계획만 사용하는 조직에 생산성 서비스를 제공하도록 설계되었습니다.
  
 **Office 365 끝점:** [전 세계(GCC 포함)](urls-and-ip-address-ranges.md)  | *21vianet에서 운영하는 Microsoft Office 365* | [Microsoft Office 365 Germany](office-365-germany-endpoints.md)  |  [Office 365 U.S. Government DoD](office-365-u-s-government-dod-endpoints.md) | [Office 365 U.S. Government GCC High](office-365-u-s-government-gcc-high-endpoints.md) |
  
|||
|:-----|:-----|
|**마지막 업데이트:** 07/08/2020- ![ RSS ](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [변경 로그 구독](https://endpoints.office.com/version/China?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)|**다운로드:** 모든 필수 및 선택 대상을 [JSON 형식](https://endpoints.office.com/endpoints/China?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) 목록에 다운로드합니다.  <br/> |

[Office 365 끝점 관리](managing-office-365-endpoints.md)에서 시작해 이 데이터를 사용해 네트워크 연결을 관리하는 데 추천하는 사항을 파악합니다. 끝점 데이터는 새 IP 주소 및 URL이 활성화되기 30일 전인 월초에 업데이트됩니다. 이렇게 하면 자동 업데이트를 설정하지 않은 고객에게 새로운 연결이 필요하기 해당 프로세스를 완료할 수 있습니다. 끝점 주소는 지원 에스컬레이션, 보안 문제 또는 그 외의 즉각적인 운영 요구 사항을 처리하는 데 필요한 경우 월중에 업데이트될 수 있습니다. 이 페이지 아래에 표시되는 데이터는 모두 REST 기반 웹 서비스에서 생성됩니다. 스크립트 또는 네트워크 장치를 사용하여 이 데이터에 액세스 하는 경우, 직접 [웹 서비스](office-365-ip-web-service.md)로 이동해야 합니다.

아래의 끝점 데이터는 사용자의 컴퓨터에서 Microsoft Office 365에 연결할 때의 요구 사항을 나열합니다. 이는 하이브리드 또는 인바운드 네트워크 연결이라 불리며 Microsoft에서 고객 네트워크로의 네트워크 연결을 포함하지 않습니다.

끝점은 네 가지 서비스 영역으로 그룹화됩니다. 첫 번째 세 개의 서비스 영역은 연결용으로 개별 선택할 수 있습니다. 네 번째 서비스 영역(Microsoft 365 Common 및 Office 라고 함)은 일반적인 종속성이 있으며 항상 네트워크에 연결된 상태여야 합니다.

표시된 데이터 열:

- **ID**: 행의 ID 번호는 끝점 집합이라고도 합니다. 이 ID는 해당 끝점 집합에 대한 웹 서비스에서 반환되는 것과 동일합니다.

- **범주**: 끝점 집합이 "최적화", "허용" 또는 "기본"으로 분류되는지 여부를 보여줍니다. [https://aka.ms/pnc](https://aka.ms/pnc)에서 이러한 범주 및 관리에 대한 지침을 읽을 수 있습니다. 이 열에서도 네트워크에 연결하는 데 필요한 끝점 집합을 나열합니다. 네트워크에 연결하는 데 필요하지 않은 끝점 집합의 경우, 이 필드에서 메모를 제공해 끝점 집합이 차단되면 어떤 기능을 사용할 수 없는지 표시해줍니다. 전체 서비스 영역을 제외하는 경우, 필요한 것으로 나열된 끝점 집합은 연결이 필요하지 않습니다.

- **ER**: Microsoft Azure ExpressRoute 및 Microsoft Office 365 경로 접두사에서 끝점 집합을 지원하는 경우 **예**로 설정되어 있습니다. 표시된 경로 접두사를 포함하는 BGP 커뮤니티를 나열된 서비스 영역과 맞춥니다. ER이 **아니요**인 경우는 ExpressRoute가 끝점 집합을 지원하지 않는다는 것을 의미합니다. 그러나 ER이 **아니요**라고 하여 끝점 집합에 보급되는 경로가 없다고 간주할 수는 없습니다.

- **주소**: 끝점 집합의 FQDN 또는 와일드카드 도메인 이름 및 IP 주소 범위를 보여줍니다. IP 주소 범위가 CIDR 형식이며 특정 네트워크에서 여러 개의 개별 IP 주소를 포함할 수 있다는 점에 유의하시기 바랍니다.
 
- **포트**: 주소와 결합하여 네트워크 끝점을 이루는 TCP 또는 UDP 포트를 나열합니다. 다른 포트도 나열되어 있으면, IP 주소 범위에서 몇 가지 중복되는 경우도 있습니다.

[!INCLUDE [Office 365 operated by 21Vianet endpoints](./includes/office-365-operated-by-21vianet-endpoints.md)]


