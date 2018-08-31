---
title: Office 365 미국 정부 높은 GCC 끝점
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 8/13/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: MET150
ms.assetid: cbd2369c-fd96-464c-bf48-c99826b459ee
description: 조직 Office 365를 사용 하 여 사용할 수 있는 네트워크에 있는 컴퓨터에서 인터넷에 연결할 수 없도록 제한 한 경우 아래를 찾을 수 (Fqdn, 포트, Url, IPv4 및 IPv6 주소 범위)는 끝점에 포함 되어야 하는 프로그램 아웃 바운드 허용 목록을 확인 하 여 컴퓨터에는 Office 365 성공적으로 사용할 수 있습니다.
hideEdit: true
ms.openlocfilehash: eb1ac47ad8317b46ce19106e8eeab5dae3c25432
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542148"
---
# <a name="office-365-us-government-gcc-high-endpoints"></a><span data-ttu-id="56a05-103">Office 365 미국 정부 높은 GCC 끝점</span><span class="sxs-lookup"><span data-stu-id="56a05-103">Office 365 U.S. Government GCC High endpoints</span></span>

 <span data-ttu-id="56a05-104">*적용 대상: Office 365 관리*</span><span class="sxs-lookup"><span data-stu-id="56a05-104">*Applies To: Office 365 Admin*</span></span>

<span data-ttu-id="56a05-p101">**요약:** Office 365를 사용 하려면 인터넷에 연결을 해야 합니다. 아래 끝점 Office 365 미국 정부 GCC 높은 계획만을 사용 하는 고객을 위한 연결할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="56a05-p101">**Summary:** Office 365 requires connectivity to the Internet. The endpoints below should be reachable for customers using Office 365 U.S. Government GCC High plans only.</span></span>
  
> [!NOTE]
> <span data-ttu-id="56a05-p102">Microsoft는 IP 주소와 FQDN 항목을이 페이지에 대 한 REST 기반 웹 서비스를 개발 하 고 있습니다. 이 새로운 서비스를 구성 하 고 방화벽 및 프록시 서버와 같은 네트워크 경계 장치를 업데이트 하는데 도움이 됩니다. 끝점, 목록 또는 특정 변경의 현재 버전의 목록을 다운로드할 수 있습니다. 이 서비스는 XML 문서, RSS 피드, IP 주소 및 FQDN 항목을이 페이지에 결국 대체할 수 있습니다. 이 새로운 서비스를 실행 하려면 [웹 서비스](managing-office-365-endpoints.md#webservice)로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="56a05-p102">Microsoft is developing a REST-based web service for the IP address and FQDN entries on this page. This new service will help you configure and update network perimeter devices such as firewalls and proxy servers. You can download the list of endpoints, the current version of the list, or specific changes. This service will eventually replace the XML document, RSS feed, and the IP address and FQDN entries on this page. To try out this new service, go to [Web service](managing-office-365-endpoints.md#webservice).</span></span>
  
 <span data-ttu-id="56a05-112">**Office 365 끝점:** [Worldwide (GCC 포함)](urls-and-ip-address-ranges.md)  |  [21 Vianet 하 여 office 365 작동할](urls-and-ip-address-ranges-21vianet.md)  | [Office 365 독일](office-365-germany-endpoints.md)  | [Office 365 미국 정부 DoD](office-365-u-s-government-dod-endpoints.md) | *Office 365 미국 정부 GCC 높음* |</span><span class="sxs-lookup"><span data-stu-id="56a05-112">**Office 365 endpoints:** [Worldwide (including GCC)](urls-and-ip-address-ranges.md) | [Office 365 operated by 21 Vianet](urls-and-ip-address-ranges-21vianet.md)  | [Office 365 Germany](office-365-germany-endpoints.md)  | [Office 365 U.S. Government DoD](office-365-u-s-government-dod-endpoints.md) | *Office 365 U.S. Government GCC High* |</span></span>
  
|||
|:-----|:-----|
|<span data-ttu-id="56a05-113">7/2/2018 **마지막 업데이트 날짜:** - ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [변경 로그 구독](https://aka.ms/usendpointrss)</span><span class="sxs-lookup"><span data-stu-id="56a05-113">**Last updated:** 7/2/2018 - ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [Change Log subscription](https://aka.ms/usendpointrss)</span></span> <br/> |<span data-ttu-id="56a05-114">**다운로드:** [XML](https://aka.ms/usdefenseendpoints) 형식의 전체 목록은</span><span class="sxs-lookup"><span data-stu-id="56a05-114">**Download:** the full list in [XML format](https://aka.ms/usdefenseendpoints)</span></span> <br/> |
   
 <span data-ttu-id="56a05-p103">이 데이터를 사용 하 여 네트워크 연결을 관리 하기 위한 권장 사항 이해 하려면 [Office 365 관리 끝점](managing-office-365-endpoints.md) 으로 시작 합니다. 새 IP 주소 및 활성화 되 고 전 30 일 게시 된 Url 사용 하 여 각 월의 시작 부분에 끝점 데이터가 업데이트 됩니다. 이 고객에 게 하지 않는 아직 새 연결이 필요 하기 전에 해당 프로세스를 완료 하려면 업데이트 자동 수 있습니다. 주소 지원 에스컬레이션, 보안 문제 또는 기타 즉시 운영 요구 사항에 필요한 경우에 끝점 달 하는 동안 업데이트 될 수 있습니다. 이 페이지 아래에 표시 되는 데이터는 모든 REST 기반 웹 서비스에서 생성 됩니다. 스크립트 또는 네트워크 장치를 사용 하 여이 데이터에 액세스 하는, [웹 서비스](managing-office-365-endpoints.md#webservice) 에 직접 서 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="56a05-p103">Start with [Managing Office 365 endpoints](managing-office-365-endpoints.md) to understand our recommendations for managing network connectivity using this data. Endpoints data is updated at the beginning of each month with new IP Addresses and URLs published 30 days in advance of being active. This allows for customers who do not yet have automated updates to complete their processes before new connectivity is required. Endpoints may also be updated during the month if needed to address support escalations, security incidents, or other immediate operational requirements. The data shown on this page below is all generated from the REST-based web services. If you are using a script or a network device to access this data, you should go to the [Web service](managing-office-365-endpoints.md#webservice) directly.</span></span>

<span data-ttu-id="56a05-p104">아래의 끝점 데이터 연결을 사용자의 컴퓨터에서 Office 365에 대 한 요구 사항을 나열합니다. 고객 네트워크, 하이브리드 라고도 함 또는 인바운드 네트워크 연결에 Microsoft에서 네트워크 연결을 포함 하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="56a05-p104">Endpoint data below lists requirements for connectivity from a user’s machine to Office 365. It does not include network connections from Microsoft into a customer network, sometimes called hybrid or inbound network connections.</span></span>

<span data-ttu-id="56a05-p105">끝점을 4 개의 서비스 영역으로 그룹화 됩니다. 처음 세 서비스 영역 선택 될 수 독립적으로 연결 합니다. 네번째 서비스 영역 (Microsoft 365 일반적이 고 Office Online 라고 함)는 일반적인 의존 관계 이며 항상 네트워크 연결에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="56a05-p105">The endpoints are grouped into four service areas. The first three service areas can be independently selected for connectivity. The fourth service area is a common dependency (called Microsoft 365 Common and Office Online) and must always have network connectivity.</span></span>

<span data-ttu-id="56a05-126">데이터 열이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="56a05-126">Data columns shown are:</span></span>

- <span data-ttu-id="56a05-p106">**ID**: 끝점 집합 라고도 하는 행의 ID 번호입니다. 이 ID는 끝점 집합에 대 한 웹 서비스에 의해 반환 되는 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="56a05-p106">**ID**: The ID number of the row, also known as an endpoint set. This ID is the same as is returned by the web service for the endpoint set.</span></span>

- <span data-ttu-id="56a05-p107">**범주**: 끝점 집합 "최적화", "허용" 또는 "Default"로 분류 되는지 여부를 표시 합니다. 이러한 범주 및 관리에 그 중에 대 한 지침에 대 한 읽을 수 있는 [http://aka.ms/pnc](http://aka.ms/pnc)합니다. 이 열에도 끝점으로 설정 하는 네트워크 연결이 필요가 나열 합니다. 없어도 네트워크에 연결 하는 끝점 집합에 대 한 끝점 집합 차단 되 면 기능에 설명 누락 된 것을 나타내기 위해이 필드에 대 한 정보를 제공 합니다. 전체 서비스 영역을 제외 하는 경우 필요에 따라 나열 하는 끝점 집합 연결이 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="56a05-p107">**Category**: Shows whether the endpoint set is categorized as “Optimize”, “Allow”, or “Default”. You can read about these categories and guidance for management of them at [http://aka.ms/pnc](http://aka.ms/pnc). This column also lists which endpoint sets are required to have network connectivity. For endpoint sets which are not required to have network connectivity, we provide notes in this field to indicate what functionality would be missing if the endpoint set is blocked. If you are excluding an entire service area, the endpoint sets listed as required do not require connectivity.</span></span>

- <span data-ttu-id="56a05-p108">**ER**:이 방법이 **Yes** 끝점 집합 경로 접두사를 Office 365와 Azure ExpressRoute을 통해 지원 됩니다. 표시 된 경로 접두사를 포함 하는 BGP 커뮤니티 나열 된 서비스 영역에 맞춥니다. ER **No**때 즉, ExpressRoute이 끝점 집합에 대 한 지원 되지 않습니다. 그러나 해당 간주할 수는 없습니다 ER **No**가 한 끝점 집합에 대 한 경로 되지는 보급는 합니다. Azure AD 연결을 사용 하려는 경우 적절 한 해야 [특별 고려 사항 섹션](https://docs.microsoft.com/azure/active-directory/connect/active-directory-AADconnect-instances#microsoft-azure-government-cloud) 읽고 Azure AD 연결 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="56a05-p108">**ER**: This is **Yes** if the endpoint set is supported over Azure ExpressRoute with Office 365 route prefixes. The BGP community that includes the route prefixes shown aligns with the service area listed. When ER is **No**, this means that ExpressRoute is not supported for this endpoint set. However, it should not be assumed that no routes are advertised for an endpoint set where ER is **No**. If you plan to use Azure AD Connect, read the [special considerations section](https://docs.microsoft.com/azure/active-directory/connect/active-directory-AADconnect-instances#microsoft-azure-government-cloud) to ensure you have the appropriate Azure AD Connect configuration.</span></span>

- <span data-ttu-id="56a05-p109">**주소**: Fqdn 또는 와일드 카드 도메인 이름 및 끝점 집합에 대 한 IP 주소 범위를 나열 합니다. 참고 IP 주소 범위는 CIDR 형식에 있으며 지정 된 네트워크에서 많은 개별 IP 주소를 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56a05-p109">**Addresses**: Lists the FQDNs or wildcard domain names and IP Address ranges for the endpoint set. Note that an IP Address range is in CIDR format and may include many individual IP Addresses in the specified network.</span></span>
 
- <span data-ttu-id="56a05-p110">**포트**: 네트워크 끝점을 형성 하는 주소와 결합 되는 TCP 또는 UDP 포트를 나열 합니다. IP 주소 범위에서 일부 중복 되는 경우도 있습니다 있는 서로 다른 포트를 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="56a05-p110">**Ports**: Lists the TCP or UDP ports that are combined with the Addresses to form the network endpoint. You may notice some duplication in IP Address ranges where there are different ports listed.</span></span>
 
[!INCLUDE [Office 365 U.S. Government GCC High endpoints](./includes/office-365-u.s.-government-gcc-high-endpoints.md)]

<span data-ttu-id="56a05-143">이 표에 대한 참고 사항</span><span class="sxs-lookup"><span data-stu-id="56a05-143">Notes for this table:</span></span>

- <span data-ttu-id="56a05-p111">보안 및 규정 준수 센터 SCC ()에 Office 365 용 Azure ExpressRoute에 대 한 지원을 제공 합니다. 보고, 감사, 고급 eDiscovery, DLP 통합 및 데이터 관리 방식 등 소스 코드 제어를 통해 노출 다양 한 기능에 대 한도 마찬가지입니다. 현재 두 특정 기능 PST 가져오기 및 내보내기, eDiscovery Azure Blob 저장소의 의존성 때문에 Office 365 경로 필터와 함께 Azure ExpressRoute를 지원 하지 않습니다. 이러한 기능을 사용 하려면 인터넷에 연결 또는 Azure ExpressRoute Azure 공용 경로 필터와 함께 포함 하는 모든 지원 가능한 Azure 연결 옵션을 사용 하 여 Azure Blob 저장소에 대 한 별도 연결을 해야 합니다. 이러한 기능을 모두에 대 한 이러한 연결 설정 평가 해야 합니다. Office 365 정보 보호 팀은이 제한의를 알고 있으며 이러한 기능을 모두에 대 한 제한으로 Office 365에 대 한 지원 Azure ExpressRoute에 대 한 Office 365 경로 필터를 가져올 적극적으로 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="56a05-p111">The Security and Compliance Center (SCC) provides support for Azure ExpressRoute for Office 365. The same applies for many features exposed through the SCC such as Reporting, Auditing, Advanced eDiscovery, Unified DLP, and Data Governance. Two specific features, PST Import and eDiscovery Export, currently do not support Azure ExpressRoute with only Office 365 route filters due to their dependency on Azure Blob Storage. To consume those features, you need separate connectivity to Azure Blob Storage using any supportable Azure connectivity options, which include Internet connectivity or Azure ExpressRoute with Azure Public route filters. You have to evaluate establishing such connectivity for both of those features. The Office 365 Information Protection team is aware of this limitation and is actively working to bring support for Azure ExpressRoute for Office 365 as limited to Office 365 route filters for both of those features.</span></span>

- <span data-ttu-id="56a05-p112">나열 되지 않은 하 고 사용자가 Office 365 ProPlus 응용 프로그램을 실행 하 고 문서를 편집할 수에 필요 하지 않은 Office 365 ProPlus에 대 한 추가 선택적 끝점 있습니다. 선택적 끝점 Microsoft 데이터 센터에서 호스팅되는 하 고 수행 하지 처리, 전송, 또는 고객 데이터를 저장 합니다. 이러한 끝점에 대 한 사용자 연결 기본 인터넷 탈출 경계를 이동 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="56a05-p112">There are additional optional endpoints for Office 365 ProPlus that are not listed and are not required for users to launch Office 365 ProPlus applications and edit documents. Optional endpoints are hosted in Microsoft datacenters and do not process, transmit, or store customer data. We recommend that user connections to these endpoints be directed to the default Internet egress perimeter.</span></span>

