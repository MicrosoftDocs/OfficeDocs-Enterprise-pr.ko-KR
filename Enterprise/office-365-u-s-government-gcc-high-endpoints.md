---
title: Office 365 미국 정부 GCC 높은 끝점
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 06/29/2020
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
ms.openlocfilehash: 995fb0265b3e2854b85291a8152469c3034e75a2
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "44997560"
---
# <a name="office-365-us-government-gcc-high-endpoints"></a>Office 365 미국 정부 GCC 높은 끝점

 *적용 대상: Office 365 관리자*

Office 365를 사용 하려면 인터넷에 연결 해야 합니다. 아래 끝점은 Office 365 미국 정부 GCC High 요금제만 사용 하는 고객에 게 연결할 수 있어야 합니다.
  
> [!NOTE]
> Microsoft has released a REST-based web service for the IP address and FQDN entries on this page. This new service will help you configure and update network perimeter devices such as firewalls and proxy servers. You can download the list of endpoints, the current version of the list, or specific changes. This service replaces the XML document linked from this page, which was deprecated on October 2, 2018. To try out this new service, go to [Web service](office-365-ip-web-service.md).
  
 **Office 365 끝점:** [전 세계(GCC 포함)](urls-and-ip-address-ranges.md) | [21vianet에서 운영하는 Microsoft Office 365](urls-and-ip-address-ranges-21vianet.md)  | [Microsoft Office 365 Germany](office-365-germany-endpoints.md)   |  [Office 365 U.S. Government DoD](office-365-u-s-government-dod-endpoints.md) | *Office 365 U.S. Government GCC High* |
  
|||
|:-----|:-----|
|**마지막 업데이트:** 06/29/2020- ![ RSS ](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [변경 로그 구독](https://endpoints.office.com/version/USGOVGCCHigh?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) <br/> |**다운로드:** [JSON 형식의](https://endpoints.office.com/endpoints/USGOVGCCHigh?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) 전체 목록 <br/> |

 [Office 365 끝점 관리](managing-office-365-endpoints.md) 를 시작 하 여이 데이터를 사용 하 여 네트워크 연결을 관리 하기 위한 권장 사항을 이해 합니다. 끝점 데이터는 각 월의 시작 부분에서 새 IP 주소와 30 일이 지난 후에 게시 된 Url을 사용 하 여 업데이트 됩니다. 이렇게 하면 새 연결이 필요 하기 전에 아직 자동화 된 업데이트를 통해 프로세스를 완료할 수 있습니다. 지원 되는 에스컬레이션, 보안 문제 또는 기타 즉각적인 운영 요구 사항을 해결 해야 하는 경우에는 한 달 동안에도 끝점이 업데이트 될 수 있습니다. 아래이 페이지에 표시 된 데이터는 모두 REST 기반 웹 서비스에서 생성 됩니다. 스크립트나 네트워크 장치를 사용 하 여이 데이터에 액세스 하는 경우에는 [웹 서비스로](office-365-ip-web-service.md) 직접 이동 해야 합니다.

Endpoint data below lists requirements for connectivity from a user’s machine to Office 365. It does not include network connections from Microsoft into a customer network, sometimes called hybrid or inbound network connections.

The endpoints are grouped into four service areas. The first three service areas can be independently selected for connectivity. The fourth service area is a common dependency (called Microsoft 365 Common and Office) and must always have network connectivity.

표시된 데이터 열:

- **ID**: The ID number of the row, also known as an endpoint set. This ID is the same as is returned by the web service for the endpoint set.

- **Category**: Shows whether the endpoint set is categorized as “Optimize”, “Allow”, or “Default”. You can read about these categories and guidance for management of them at [https://aka.ms/pnc](https://aka.ms/pnc). This column also lists which endpoint sets are required to have network connectivity. For endpoint sets which are not required to have network connectivity, we provide notes in this field to indicate what functionality would be missing if the endpoint set is blocked. If you are excluding an entire service area, the endpoint sets listed as required do not require connectivity.

- **ER**: Office 365 경로 접두사를 사용한 Azure express에서 끝점 집합이 지원 되는 경우에는이를 **예로** 들 수 있습니다. 표시 되는 경로 접두사를 포함 하는 BGP 커뮤니티는 나열 된 서비스 영역에 맞게 정렬 됩니다. ER가 **No**이면이 끝점 집합에 대해 express가 지원 되지 않습니다. 그러나 ER가 **no**인 끝점 집합에 대해 경로가 보급 되지 않는다고 가정 해서는 안 됩니다. Azure AD Connect를 사용 하려는 경우 [특별 고려 사항 섹션](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-instances#microsoft-azure-government) 을 읽어 적절 한 Azure ad connect 구성이 있는지 확인 합니다.

- **Addresses**: Lists the FQDNs or wildcard domain names and IP Address ranges for the endpoint set. Note that an IP Address range is in CIDR format and may include many individual IP Addresses in the specified network.
 
- **Ports**: Lists the TCP or UDP ports that are combined with the Addresses to form the network endpoint. You may notice some duplication in IP Address ranges where there are different ports listed.
 
[!INCLUDE [Office 365 U.S. Government GCC High endpoints](./includes/office-365-u.s.-government-gcc-high-endpoints.md)]

이 표에 대한 참고 사항

- SCC (보안 및 준수 센터)는 Office 365 용 Azure Express를 지원 합니다. 이는 보고, 감사, Advanced eDiscovery, 통합 DLP 및 데이터 거 버 넌 스와 같은 SCC를 통해 제공 되는 많은 기능에도 적용 됩니다. 두 가지 특정 기능인 PST 가져오기 및 eDiscovery 내보내기에서는 현재 Azure Blob Storage에 대 한 종속성으로 인해 Office 365 경로 필터만 사용 하는 Azure Express를 지원 하지 않습니다. 이러한 기능을 사용 하려면 azure 공용 경로 필터를 사용한 Azure Express 주소나 인터넷 연결을 포함 하는 지원 되지 않는 Azure 연결 옵션을 통해 Azure Blob Storage에 대 한 별도의 연결이 필요 합니다. 이러한 두 기능에 대 한 이러한 연결을 평가 해야 합니다. Office 365 Information Protection 팀은 이러한 기능에 대 한 Office 365 경로 필터로 제한 되는, Office 365에 대 한 Azure Express를 지원 하기 위해 현재 이러한 제한을 확인 하 고 있습니다.

- 사용자가 엔터프라이즈 응용 프로그램에 대해 Microsoft 365 앱을 시작 하 고 문서를 편집 하는 데 필요한 Microsoft 365 앱 for enterprise 용 추가 끝점이 나열 되어 있지 않습니다. 선택적 끝점은 Microsoft 데이터 센터에서 호스트 되며, 고객 데이터가 처리, 전송 또는 저장 되지 않습니다. 이러한 끝점에 대 한 사용자 연결을 기본 인터넷 송신 주변으로 보내는 것이 좋습니다.

