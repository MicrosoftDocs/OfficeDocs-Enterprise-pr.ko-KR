---
title: Office 365 Germany 끝점
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
ms.custom: Adm_O365_Setup
search.appverid: MOE150
ms.assetid: 8a113a50-0071-4155-bb8e-eba5a8dbd4c8
description: 조직에서 Office 365을 사용 하 고 네트워크의 컴퓨터에서 인터넷에 연결 하지 못하도록 제한 하는 경우 아래에서 아웃 바운드 허용 목록에 포함 해야 하는 끝점 (Fqdn, 포트, Url 및 IPv4 및 IPv6 주소 범위)을 확인 하 여 컴퓨터에서 Office 365를 정상적으로 사용할 수 있는지 확인 합니다.
hideEdit: true
ms.openlocfilehash: a0f7f0ac9892363c5f60c509c1e48d7f16f4d96d
ms.sourcegitcommit: 338e3bcf0a62842fbbb17145b67a4a93f3b90aac
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/09/2020
ms.locfileid: "45091157"
---
# <a name="office-365-germany-endpoints"></a>Office 365 Germany 끝점

 *적용 대상: Office 365 관리자*

Office 365를 사용 하려면 인터넷에 연결 해야 합니다. 아래 끝점은 **Office 365 독일** 요금제만 사용 하는 고객에 게 연결할 수 있어야 합니다.
  
> [!NOTE]
> Microsoft has released a REST-based web service for the IP address and FQDN entries on this page. This new service will help you configure and update network perimeter devices such as firewalls and proxy servers. You can download the list of endpoints, the current version of the list, or specific changes. This service replaces the XML document linked from this page, which was deprecated on October 2, 2018. To try out this new service, go to [Web service](office-365-ip-web-service.md).
 
 **Office 365 끝점:** [전 세계(GCC 포함)](urls-and-ip-address-ranges.md)  | [21vianet에서 운영하는 Microsoft Office 365](urls-and-ip-address-ranges-21vianet.md)  | *Microsoft Office 365 Germany*  |  [Office 365 U.S. Government DoD](office-365-u-s-government-dod-endpoints.md) | [Office 365 U.S. Government GCC High](office-365-u-s-government-gcc-high-endpoints.md)  |
  
|||
|:-----|:-----|
|**마지막 업데이트:** 07/09/2020- ![ RSS ](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [변경 로그 구독](https://endpoints.office.com/version/Germany?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) |**다운로드:** 모든 필수 및 선택 대상을 [JSON 형식](https://endpoints.office.com/endpoints/Germany?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) 목록에 다운로드합니다.  <br/> |

[Office 365 끝점 관리](managing-office-365-endpoints.md) 를 시작 하 여이 데이터를 사용 하 여 네트워크 연결을 관리 하기 위한 권장 사항을 이해 합니다. 끝점 데이터는 각 월의 시작 부분에서 새 IP 주소와 30 일이 지난 후에 게시 된 Url을 사용 하 여 업데이트 됩니다. 이렇게 하면 새 연결이 필요 하기 전에 아직 자동화 된 업데이트를 통해 프로세스를 완료할 수 있습니다. 지원 되는 에스컬레이션, 보안 문제 또는 기타 즉각적인 운영 요구 사항을 해결 해야 하는 경우에는 한 달 동안에도 끝점이 업데이트 될 수 있습니다. 언제 든 지 [변경 로그 구독](https://endpoints.office.com/version/Germany?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)을 참조할 수 있습니다.

아래이 페이지에 표시 된 데이터는 모두 REST 기반 웹 서비스에서 생성 됩니다. 스크립트나 네트워크 장치를 사용 하 여이 데이터에 액세스 하는 경우에는 [웹 서비스로](office-365-ip-web-service.md) 직접 이동 해야 합니다.

Endpoint data below lists requirements for connectivity from a user’s machine to Office 365. It does not include network connections from Microsoft into a customer network, sometimes called hybrid or inbound network connections.

The endpoints are grouped into four service areas. The first three service areas can be independently selected for connectivity. The fourth service area is a common dependency (called Microsoft 365 Common and Office) and must always have network connectivity.

표시된 데이터 열:

- **ID**: The ID number of the row, also known as an endpoint set. This ID is the same as is returned by the web service for the endpoint set.

- **Category**: Shows whether the endpoint set is categorized as “Optimize”, “Allow”, or “Default”. You can read about these categories and guidance for management of them at [https://aka.ms/pnc](https://aka.ms/pnc). This column also lists which endpoint sets are required to have network connectivity. For endpoint sets which are not required to have network connectivity, we provide notes in this field to indicate what functionality would be missing if the endpoint set is blocked. If you are excluding an entire service area, the endpoint sets listed as required do not require connectivity.

- **ER**: This is **Yes** if the endpoint set is supported over Azure ExpressRoute with Office 365 route prefixes. The BGP community that includes the route prefixes shown aligns with the service area listed. When ER is **No**, this means that ExpressRoute is not supported for this endpoint set. However, it should not be assumed that no routes are advertised for an endpoint set where ER is **No**.

- **Addresses**: Lists the FQDNs or wildcard domain names and IP Address ranges for the endpoint set. Note that an IP Address range is in CIDR format and may include many individual IP Addresses in the specified network.
 
- **Ports**: Lists the TCP or UDP ports that are combined with the Addresses to form the network endpoint. You may notice some duplication in IP Address ranges where there are different ports listed.

[!INCLUDE [Office 365 Germany endpoints](./includes/office-365-germany-endpoints.md)]

 

