---
title: 'Office 365 URL 및 IP 주소 범위 '
ms.author: laurawi
author: LauraWi
manager: laurawi
ms.date: 01/02/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- MOM160
- BCS160
ms.assetid: 8548a211-3fe7-47cb-abb1-355ea5aa88a2
description: '요약: Office 365를 사용하려면 인터넷에 연결되어 있어야 합니다. 아래의 끝점은 Government 커뮤니티 클라우드(GCC)를 포함하여 Office 365 요금제를 사용하는 고객에 연결할 수 있어야 합니다.'
hideEdit: true
ms.openlocfilehash: aa07bb55b87d1fa15c76239390622fcdc4f5e88c
ms.sourcegitcommit: f9888d1c27e38d3c489a0cbed7684a2e67c3afbd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/07/2020
ms.locfileid: "40951518"
---
# <a name="office-365-urls-and-ip-address-ranges"></a><span data-ttu-id="f1f24-104">Office 365 URL 및 IP 주소 범위 </span><span class="sxs-lookup"><span data-stu-id="f1f24-104">Office 365 URLs and IP address ranges</span></span>

 <span data-ttu-id="f1f24-p102">**요약:** Office 365를 사용하려면 인터넷에 연결되어 있어야 합니다. 아래의 끝점은 Government 커뮤니티 클라우드(GCC)를 포함하여 Office 365 요금제를 사용하는 고객에 연결할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1f24-p102">**Summary:** Office 365 requires connectivity to the Internet. The endpoints below should be reachable for customers using Office 365 plans, including Government Community Cloud (GCC).</span></span>
  
> [!NOTE]
> <span data-ttu-id="f1f24-p103">Microsoft는 이 페이지에 있는 IP 주소와 FQDN 항목을 위해 REST 기반 웹 서비스를 출시했습니다. 이 새로운 서비스는 방화벽 및 프록시 서버와 같은 네트워크 경계 장치를 구성하고 업데이트하는 작업을 도와줍니다. 끝점, 최신 버전의 목록 또는 특정 변경 사항의 목록을 다운로드할 수 있습니다. 이 서비스는 2018년 10월 2일부터 사용되지 않는 이 페이지에 연결된 XML 문서를 대체합니다. 새로운 서비스를 실행하려면 [웹 서비스](office-365-ip-web-service.md)로 이동하세요.</span><span class="sxs-lookup"><span data-stu-id="f1f24-p103">Microsoft has released a REST-based web service for the IP address and FQDN entries on this page. This new service will help you configure and update network perimeter devices such as firewalls and proxy servers. You can download the list of endpoints, the current version of the list, or specific changes. This service replaces the XML document linked from this page, which was deprecated on October 2, 2018. To try out this new service, go to [Web service](office-365-ip-web-service.md).</span></span>
  
<span data-ttu-id="f1f24-112">*Office 365 Worldwide(+GCC)* | [21vianet에서 운영하는 Microsoft Office 365](urls-and-ip-address-ranges-21vianet.md) | [Microsoft Office 365 Germany](office-365-germany-endpoints.md) | [Office 365 U.S. Government DoD](office-365-u-s-government-dod-endpoints.md)  | [Office 365 U.S. Government GCC High](office-365-u-s-government-gcc-high-endpoints.md) |</span><span class="sxs-lookup"><span data-stu-id="f1f24-112">*Office 365 Worldwide (+GCC)* | [Office 365 operated by 21 Vianet](urls-and-ip-address-ranges-21vianet.md) | [Office 365 Germany](office-365-germany-endpoints.md) | [Office 365 U.S. Government DoD](office-365-u-s-government-dod-endpoints.md)  | [Office 365 U.S. Government GCC High](office-365-u-s-government-gcc-high-endpoints.md) |</span></span>
  
||||
|:-----|:-----|:-----|
|<span data-ttu-id="f1f24-113">**마지막 업데이트 날짜:** 2020년 1월 2일 - ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [로그 구독 변경](https://endpoints.office.com/version/worldwide?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="f1f24-113">**Last updated:** 11/27/2019 - ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [Change Log subscription](https://endpoints.office.com/version/worldwide?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span> <br/> |<span data-ttu-id="f1f24-114">**다운로드:** 모든 필수 및 선택 대상을 [JSON 형식](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) 목록에 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="f1f24-114">**Download:** all required and optional destinations in one [JSON formatted](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) list.</span></span>  <br/> | <span data-ttu-id="f1f24-115">**사용:** 프록시 [PAC 파일](managing-office-365-endpoints.md#pacfiles)</span><span class="sxs-lookup"><span data-stu-id="f1f24-115">**Use:** our proxy [PAC files](managing-office-365-endpoints.md#pacfiles)</span></span> <br/> |
   
 <span data-ttu-id="f1f24-p104">[Office 365 끝점 관리](managing-office-365-endpoints.md)에서 시작해 이 데이터를 사용해 네트워크 연결을 관리하는 데 추천하는 사항을 파악합니다. 끝점 데이터는 새 IP 주소 및 URL이 활성화되기 30일 전인 월초에 업데이트됩니다. 이렇게 하면 자동 업데이트를 설정하지 않은 고객에게 새로운 연결이 필요하기 해당 프로세스를 완료할 수 있습니다. 끝점 주소는 지원 에스컬레이션, 보안 문제 또는 그 외의 즉각적인 운영 요구 사항을 처리하는 데 필요한 경우 월중에 업데이트될 수 있습니다. 이 페이지 아래에 표시되는 데이터는 모두 REST 기반 웹 서비스에서 생성됩니다. 스크립트 또는 네트워크 장치를 사용하여 이 데이터에 액세스 하는 경우, 직접 [웹 서비스](office-365-ip-web-service.md)로 이동해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1f24-p104">Start with [Managing Office 365 endpoints](managing-office-365-endpoints.md) to understand our recommendations for managing network connectivity using this data. Endpoints data is updated at the beginning of each month with new IP Addresses and URLs published 30 days in advance of being active. This allows for customers who do not yet have automated updates to complete their processes before new connectivity is required. Endpoints may also be updated during the month if needed to address support escalations, security incidents, or other immediate operational requirements. The data shown on this page below is all generated from the REST-based web services. If you are using a script or a network device to access this data, you should go to the [Web service](office-365-ip-web-service.md) directly.</span></span>

<span data-ttu-id="f1f24-p105">아래의 끝점 데이터는 사용자의 컴퓨터에서 Microsoft Office 365에 연결할 때의 요구 사항을 나열합니다. 이는 하이브리드 또는 인바운드 네트워크 연결이라 불리며 Microsoft에서 고객 네트워크로의 네트워크 연결을 포함하지 않습니다. 자세한 내용은 [추가 끝점](additional-office365-ip-addresses-and-urls.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f1f24-p105">Endpoint data below lists requirements for connectivity from a user’s machine to Office 365. It does not include network connections from Microsoft into a customer network, sometimes called hybrid or inbound network connections. See [Additional endpoints](additional-office365-ip-addresses-and-urls.md) for more information.</span></span>

<span data-ttu-id="f1f24-p106">끝점은 네 가지 서비스 영역으로 그룹화됩니다. 첫 번째 세 개의 서비스 영역은 연결용으로 개별 선택할 수 있습니다. 네 번째 서비스 영역(Microsoft 365 Common 및 Office 라고 함)은 일반적인 종속성이 있으며 항상 네트워크에 연결된 상태여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1f24-p106">The endpoints are grouped into four service areas. The first three service areas can be independently selected for connectivity. The fourth service area is a common dependency (called Microsoft 365 Common and Office) and must always have network connectivity.</span></span>

<span data-ttu-id="f1f24-128">표시된 데이터 열:</span><span class="sxs-lookup"><span data-stu-id="f1f24-128">Data columns shown are:</span></span>

- <span data-ttu-id="f1f24-p107">**ID**: 행의 ID 번호는 끝점 집합이라고도 합니다. 이 ID는 해당 끝점 집합에 대한 웹 서비스에서 반환되는 것과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="f1f24-p107">**ID**: The ID number of the row, also known as an endpoint set. This ID is the same as is returned by the web service for the endpoint set.</span></span>

- <span data-ttu-id="f1f24-p108">**범주**: 끝점 집합이 "최적화", "허용" 또는 "기본"으로 분류되는지 여부를 보여줍니다. [https://aka.ms/pnc](https://aka.ms/pnc)에서 이러한 범주 및 관리에 대한 지침을 읽을 수 있습니다. 이 열에서도 네트워크에 연결하는 데 필요한 끝점 집합을 나열합니다. 네트워크에 연결하는 데 필요하지 않은 끝점 집합의 경우, 이 필드에서 메모를 제공해 끝점 집합이 차단되면 어떤 기능을 사용할 수 없는지 표시해줍니다. 전체 서비스 영역을 제외하는 경우, 필요한 것으로 나열된 끝점 집합은 연결이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f1f24-p108">**Category**: Shows whether the endpoint set is categorized as “Optimize”, “Allow”, or “Default”. You can read about these categories and guidance for management of them at [https://aka.ms/pnc](https://aka.ms/pnc). This column also lists which endpoint sets are required to have network connectivity. For endpoint sets which are not required to have network connectivity, we provide notes in this field to indicate what functionality would be missing if the endpoint set is blocked. If you are excluding an entire service area, the endpoint sets listed as required do not require connectivity.</span></span>

- <span data-ttu-id="f1f24-p109">**ER**: Microsoft Azure ExpressRoute 및 Microsoft Office 365 경로 접두사에서 끝점 집합을 지원하는 경우 **예**로 설정되어 있습니다. 표시된 경로 접두사를 포함하는 BGP 커뮤니티를 나열된 서비스 영역과 맞춥니다. ER이 **아니요**인 경우는 ExpressRoute가 끝점 집합을 지원하지 않는다는 것을 의미합니다. 그러나 ER이 **아니요**라고 하여 끝점 집합에 보급되는 경로가 없다고 간주할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f1f24-p109">**ER**: This is **Yes** if the endpoint set is supported over Azure ExpressRoute with Office 365 route prefixes. The BGP community that includes the route prefixes shown aligns with the service area listed. When ER is **No**, this means that ExpressRoute is not supported for this endpoint set. However, it should not be assumed that no routes are advertised for an endpoint set where ER is **No**.</span></span>

- <span data-ttu-id="f1f24-p110">**주소**: 끝점 집합의 FQDN 또는 와일드카드 도메인 이름 및 IP 주소 범위를 보여줍니다. IP 주소 범위가 CIDR 형식이며 특정 네트워크에서 여러 개의 개별 IP 주소를 포함할 수 있다는 점에 유의하시기 바랍니다.</span><span class="sxs-lookup"><span data-stu-id="f1f24-p110">**Addresses**: Lists the FQDNs or wildcard domain names and IP Address ranges for the endpoint set. Note that an IP Address range is in CIDR format and may include many individual IP Addresses in the specified network.</span></span>
 
- <span data-ttu-id="f1f24-p111">**포트**: 네트워크 끝점을 형성하기 위해 주소와 결합된 TCP 또는 UDP 포트를 나열합니다. 다른 포트가 나열된 IP 주소 범위에서 일부 중복을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1f24-p111">**Ports**: Lists the TCP or UDP ports that are combined with the Addresses to form the network endpoint. You may notice some duplication in IP Address ranges where there are different ports listed.</span></span>

[!INCLUDE [Office 365 worldwide endpoints](./includes/office-365-worldwide-endpoints.md)]

>[!Note]
><span data-ttu-id="f1f24-144">Yammer IP 주소 및 URL에 대한 권장 사항은 [이 블로그 게시물](https://techcommunity.microsoft.com/t5/Yammer-Blog/Using-hard-coded-IP-addresses-for-Yammer-is-not-recommended/ba-p/276592)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f1f24-144">For recommendations on Yammer IP addresses and URLs, see [this blog post](https://techcommunity.microsoft.com/t5/Yammer-Blog/Using-hard-coded-IP-addresses-for-Yammer-is-not-recommended/ba-p/276592).</span></span>
>


## <a name="related-topics"></a><span data-ttu-id="f1f24-145">관련 주제</span><span class="sxs-lookup"><span data-stu-id="f1f24-145">Related Topics</span></span>

[<span data-ttu-id="f1f24-146">Office 365 끝점 관리</span><span class="sxs-lookup"><span data-stu-id="f1f24-146">Managing Office 365 endpoints</span></span>](managing-office-365-endpoints.md)
  
[<span data-ttu-id="f1f24-147">Office 365 연결 문제 해결</span><span class="sxs-lookup"><span data-stu-id="f1f24-147">Troubleshooting Office 365 connectivity</span></span>](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d.aspx)
  
[<span data-ttu-id="f1f24-148">클라이언트 연결</span><span class="sxs-lookup"><span data-stu-id="f1f24-148">Client connectivity</span></span>](https://support.office.com/article/client-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b)
  
[<span data-ttu-id="f1f24-149">콘텐츠 배달 네트워크</span><span class="sxs-lookup"><span data-stu-id="f1f24-149">Content delivery networks</span></span>](https://support.office.com/article/content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f)
  
[<span data-ttu-id="f1f24-150">Microsoft Azure 데이터 센터 IP 범위</span><span class="sxs-lookup"><span data-stu-id="f1f24-150">Microsoft Azure Datacenter IP Ranges</span></span>](https://www.microsoft.com/download/details.aspx?id=41653)
  
[<span data-ttu-id="f1f24-151">Microsoft 공용 IP 공간</span><span class="sxs-lookup"><span data-stu-id="f1f24-151">Microsoft Public IP Space</span></span>](https://www.microsoft.com/download/details.aspx?id=53602)
