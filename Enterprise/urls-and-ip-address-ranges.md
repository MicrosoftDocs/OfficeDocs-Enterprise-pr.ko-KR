---
title: 'Office 365 URL 및 IP 주소 범위 '
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/09/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- MOM160
- BCS160
ms.assetid: 8548a211-3fe7-47cb-abb1-355ea5aa88a2
description: 'Summary: Office 365 requires connectivity to the Internet. The endpoints below should be reachable for customers using Office 365 plans, including Government Community Cloud (GCC).'
hideEdit: true
ms.openlocfilehash: 175359f998c4dd695c301540f94e7d7527377ffc
ms.sourcegitcommit: 338e3bcf0a62842fbbb17145b67a4a93f3b90aac
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/09/2020
ms.locfileid: "45091212"
---
# <a name="office-365-urls-and-ip-address-ranges"></a>Office 365 URL 및 IP 주소 범위

Office 365 requires connectivity to the Internet. The endpoints below should be reachable for customers using Office 365 plans, including Government Community Cloud (GCC).
  
> [!NOTE]
> COVID-19 위기에 대한 대응의 일환으로 Microsoft는 일부 계획된 URL과 IP 주소 변경에 대해 일시적인 모라토리엄을 선언했습니다. 이번 모라토리엄은 재택 근무 Office 365 시나리오에 권장되는 네트워크 최적화를 구현할 때 고객 IT 팀에 자신감과 간편함을 제공하기 위한 것입니다. 2020년 3월 24부터 2020년 6월 30일까지, 이번 모라토리엄으로 주요 Office 365 서비스(Exchange Online, SharePoint Online, Microsoft Teams)부터 최적화 범주에 포함된 IP 범위와 URL에 대한 변경이 중단됩니다. 다른 엔드포인트 범주의 변경은 평소와 같이 수행됩니다. 이 기간 동안, 고객은 클라우드 측 네트워크 변경으로 인해 Office 365 연결 시 위험을 최소화하며 Office 365 최적화 범주 서비스 엔드포인트 정의를 정적 방식으로 사용하여 대상 네트워크 최적화를수행할 수 있습니다. 모라토리엄 기간이 끝날 때 서비스 중단이 발생하지 않도록, 고객은 [Office 365 엔드포인트 관리](managing-office-365-endpoints.md)에서 제공하는 지침을 사용하여 Office 365 서비스 엔드포인트의 변경 관리 및/또는 자동화 프로세스를 구현하는 것이 좋습니다.

> [!NOTE]
> Microsoft has released a REST-based web service for the IP address and FQDN entries on this page. This new service will help you configure and update network perimeter devices such as firewalls and proxy servers. You can download the list of endpoints, the current version of the list, or specific changes. This service replaces the XML document linked from this page, which was deprecated on October 2, 2018. To try out this new service, go to [Web service](office-365-ip-web-service.md).
  
*Office 365 Worldwide(+GCC)* | [21vianet에서 운영하는 Microsoft Office 365](urls-and-ip-address-ranges-21vianet.md) | [Microsoft Office 365 Germany](office-365-germany-endpoints.md) | [Office 365 U.S. Government DoD](office-365-u-s-government-dod-endpoints.md)  | [Office 365 U.S. Government GCC High](office-365-u-s-government-gcc-high-endpoints.md) |
  
||||
|:-----|:-----|:-----|
|**마지막 업데이트:** 2020년 7월 9일 - ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [로그 구독 변경](https://endpoints.office.com/version/worldwide?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) <br/> |**다운로드:** 모든 필수 및 선택 대상을 [JSON 형식](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) 목록에 다운로드합니다.  <br/> | **사용:** 프록시 [PAC 파일](managing-office-365-endpoints.md#pacfiles) <br/> |

 Start with [Managing Office 365 endpoints](managing-office-365-endpoints.md) to understand our recommendations for managing network connectivity using this data. Endpoints data is updated at the beginning of each month with new IP Addresses and URLs published 30 days in advance of being active. This allows for customers who do not yet have automated updates to complete their processes before new connectivity is required. Endpoints may also be updated during the month if needed to address support escalations, security incidents, or other immediate operational requirements. The data shown on this page below is all generated from the REST-based web services. If you are using a script or a network device to access this data, you should go to the [Web service](office-365-ip-web-service.md) directly.

Endpoint data below lists requirements for connectivity from a user's machine to Office 365. It does not include network connections from Microsoft into a customer network, sometimes called hybrid or inbound network connections. See [Additional endpoints](additional-office365-ip-addresses-and-urls.md) for more information.

The endpoints are grouped into four service areas. The first three service areas can be independently selected for connectivity. The fourth service area is a common dependency (called Microsoft 365 Common and Office) and must always have network connectivity.

표시된 데이터 열:

- **ID**: The ID number of the row, also known as an endpoint set. This ID is the same as is returned by the web service for the endpoint set.

- **Category**: Shows whether the endpoint set is categorized as "Optimize", "Allow", or "Default". You can read about these categories and guidance for management of them at [New Office 365 endpoint categories](https://docs.microsoft.com/office365/enterprise/office-365-network-connectivity-principles#new-office-365-endpoint-categories). This column also lists which endpoint sets are required to have network connectivity. For endpoint sets which are not required to have network connectivity, we provide notes in this field to indicate what functionality would be missing if the endpoint set is blocked. If you are excluding an entire service area, the endpoint sets listed as required do not require connectivity.

- **ER**: This is **Yes** if the endpoint set is supported over Azure ExpressRoute with Office 365 route prefixes. The BGP community that includes the route prefixes shown aligns with the service area listed. When ER is **No**, this means that ExpressRoute is not supported for this endpoint set. However, it should not be assumed that no routes are advertised for an endpoint set where ER is **No**.

- **Addresses**: Lists the FQDNs or wildcard domain names and IP Address ranges for the endpoint set. Note that an IP Address range is in CIDR format and may include many individual IP Addresses in the specified network.
 
- **Ports**: Lists the TCP or UDP ports that are combined with the Addresses to form the network endpoint. You may notice some duplication in IP Address ranges where there are different ports listed.

[!INCLUDE [Office 365 worldwide endpoints](./includes/office-365-worldwide-endpoints.md)]

>[!Note]
>Yammer IP 주소 및 URL에 대한 권장 사항은 [이 블로그 게시물](https://techcommunity.microsoft.com/t5/Yammer-Blog/Using-hard-coded-IP-addresses-for-Yammer-is-not-recommended/ba-p/276592)을 참조하세요.
>

## <a name="related-topics"></a>관련 주제

[Office 365 끝점 관리](managing-office-365-endpoints.md)
  
[Office 365 연결 문제 해결](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d.aspx)
  
[클라이언트 연결](https://support.office.com/article/client-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b)
  
[콘텐츠 배달 네트워크](https://support.office.com/article/content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f)
  
[Microsoft Azure 데이터 센터 IP 범위](https://www.microsoft.com/download/details.aspx?id=41653)
  
[Microsoft 공용 IP 공간](https://www.microsoft.com/download/details.aspx?id=53602)
