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
ms.openlocfilehash: 416565d862038362c152505a89d2c51bd48c465e
ms.sourcegitcommit: c1a1b028195342affe0f3367db4e79c42429582a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/23/2020
ms.locfileid: "45387731"
---
# <a name="office-365-germany-endpoints"></a><span data-ttu-id="a7637-103">Office 365 Germany 끝점</span><span class="sxs-lookup"><span data-stu-id="a7637-103">Office 365 Germany endpoints</span></span>

 <span data-ttu-id="a7637-104">*적용 대상: Office 365 관리자*</span><span class="sxs-lookup"><span data-stu-id="a7637-104">*Applies To: Office 365 Admin*</span></span>

<span data-ttu-id="a7637-105">Office 365를 사용 하려면 인터넷에 연결 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7637-105">Office 365 requires connectivity to the Internet.</span></span> <span data-ttu-id="a7637-106">아래 끝점은 **Office 365 독일** 요금제만 사용 하는 고객에 게 연결할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7637-106">The endpoints below should be reachable for customers using **Office 365 Germany** plans only.</span></span>
  
 <span data-ttu-id="a7637-107">**Office 365 끝점:** [전 세계(GCC 포함)](urls-and-ip-address-ranges.md)  | [21vianet에서 운영하는 Microsoft Office 365](urls-and-ip-address-ranges-21vianet.md)  | *Microsoft Office 365 Germany*  |  [Office 365 U.S. Government DoD](office-365-u-s-government-dod-endpoints.md) | [Office 365 U.S. Government GCC High](office-365-u-s-government-gcc-high-endpoints.md)  |</span><span class="sxs-lookup"><span data-stu-id="a7637-107">**Office 365 endpoints:** [Worldwide (including GCC)](urls-and-ip-address-ranges.md)  | [Office 365 operated by 21 Vianet](urls-and-ip-address-ranges-21vianet.md)  | *Office 365 Germany* | [Office 365 U.S. Government DoD](office-365-u-s-government-dod-endpoints.md) | [Office 365 U.S. Government GCC High](office-365-u-s-government-gcc-high-endpoints.md)  |</span></span>
  
|||
|:-----|:-----|
|<span data-ttu-id="a7637-108">**마지막 업데이트:** 2020년 7월 9일 - ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [로그 구독 변경](https://endpoints.office.com/version/Germany?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="a7637-108">**Last updated:** 07/09/2020 - ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [Change Log subscription](https://endpoints.office.com/version/Germany?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span> |<span data-ttu-id="a7637-109">**다운로드:** 모든 필수 및 선택 대상을 [JSON 형식](https://endpoints.office.com/endpoints/Germany?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) 목록에 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="a7637-109">**Download:** all required and optional destinations in one [JSON formatted](https://endpoints.office.com/endpoints/Germany?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) list.</span></span>  <br/> |

<span data-ttu-id="a7637-110">[Office 365 끝점 관리](managing-office-365-endpoints.md) 를 시작 하 여이 데이터를 사용 하 여 네트워크 연결을 관리 하기 위한 권장 사항을 이해 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7637-110">Start with [Managing Office 365 endpoints](managing-office-365-endpoints.md) to understand our recommendations for managing network connectivity using this data.</span></span> <span data-ttu-id="a7637-111">끝점 데이터는 각 월의 시작 부분에서 새 IP 주소와 30 일이 지난 후에 게시 된 Url을 사용 하 여 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a7637-111">Endpoints data is updated at the beginning of each month with new IP Addresses and URLs published 30 days in advance of being active.</span></span> <span data-ttu-id="a7637-112">이렇게 하면 새 연결이 필요 하기 전에 아직 자동화 된 업데이트를 통해 프로세스를 완료할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7637-112">This lets customers who do not yet have automated updates to complete their processes before new connectivity is required.</span></span> <span data-ttu-id="a7637-113">지원 되는 에스컬레이션, 보안 문제 또는 기타 즉각적인 운영 요구 사항을 해결 해야 하는 경우에는 한 달 동안에도 끝점이 업데이트 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7637-113">Endpoints may also be updated during the month if needed to address support escalations, security incidents, or other immediate operational requirements.</span></span> <span data-ttu-id="a7637-114">언제 든 지 [변경 로그 구독](https://endpoints.office.com/version/Germany?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7637-114">You can always refer to the [change log subscription](https://endpoints.office.com/version/Germany?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>

<span data-ttu-id="a7637-115">아래이 페이지에 표시 된 데이터는 모두 REST 기반 웹 서비스에서 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a7637-115">The data shown on this page below is all generated from the REST-based web services.</span></span> <span data-ttu-id="a7637-116">스크립트나 네트워크 장치를 사용 하 여이 데이터에 액세스 하는 경우에는 [웹 서비스로](office-365-ip-web-service.md) 직접 이동 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7637-116">If you are using a script or a network device to access this data, you should go to the [Web service](office-365-ip-web-service.md) directly.</span></span>

<span data-ttu-id="a7637-p104">아래의 끝점 데이터는 사용자의 컴퓨터에서 Microsoft Office 365에 연결할 때의 요구 사항을 나열합니다. 이는 하이브리드 또는 인바운드 네트워크 연결이라 불리며 Microsoft에서 고객 네트워크로의 네트워크 연결을 포함하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a7637-p104">Endpoint data below lists requirements for connectivity from a user’s machine to Office 365. It does not include network connections from Microsoft into a customer network, sometimes called hybrid or inbound network connections.</span></span>

<span data-ttu-id="a7637-p105">끝점은 네 가지 서비스 영역으로 그룹화됩니다. 첫 번째 세 개의 서비스 영역은 연결용으로 개별 선택할 수 있습니다. 네 번째 서비스 영역(Microsoft 365 Common 및 Office 라고 함)은 일반적인 종속성이 있으며 항상 네트워크에 연결된 상태여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7637-p105">The endpoints are grouped into four service areas. The first three service areas can be independently selected for connectivity. The fourth service area is a common dependency (called Microsoft 365 Common and Office) and must always have network connectivity.</span></span>

<span data-ttu-id="a7637-122">표시된 데이터 열:</span><span class="sxs-lookup"><span data-stu-id="a7637-122">Data columns shown are:</span></span>

- <span data-ttu-id="a7637-p106">**ID**: 행의 ID 번호는 끝점 집합이라고도 합니다. 이 ID는 해당 끝점 집합에 대한 웹 서비스에서 반환되는 것과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="a7637-p106">**ID**: The ID number of the row, also known as an endpoint set. This ID is the same as is returned by the web service for the endpoint set.</span></span>

- <span data-ttu-id="a7637-p107">**범주**: 끝점 집합이 "최적화", "허용" 또는 "기본"으로 분류되는지 여부를 보여줍니다. [https://aka.ms/pnc](https://aka.ms/pnc)에서 이러한 범주 및 관리에 대한 지침을 읽을 수 있습니다. 이 열에서도 네트워크에 연결하는 데 필요한 끝점 집합을 나열합니다. 네트워크에 연결하는 데 필요하지 않은 끝점 집합의 경우, 이 필드에서 메모를 제공해 끝점 집합이 차단되면 어떤 기능을 사용할 수 없는지 표시해줍니다. 전체 서비스 영역을 제외하는 경우, 필요한 것으로 나열된 끝점 집합은 연결이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a7637-p107">**Category**: Shows whether the endpoint set is categorized as “Optimize”, “Allow”, or “Default”. You can read about these categories and guidance for management of them at [https://aka.ms/pnc](https://aka.ms/pnc). This column also lists which endpoint sets are required to have network connectivity. For endpoint sets which are not required to have network connectivity, we provide notes in this field to indicate what functionality would be missing if the endpoint set is blocked. If you are excluding an entire service area, the endpoint sets listed as required do not require connectivity.</span></span>

- <span data-ttu-id="a7637-p108">**ER**: Microsoft Azure ExpressRoute 및 Microsoft Office 365 경로 접두사에서 끝점 집합을 지원하는 경우 **예**로 설정되어 있습니다. 표시된 경로 접두사를 포함하는 BGP 커뮤니티를 나열된 서비스 영역과 맞춥니다. ER이 **아니요**인 경우는 ExpressRoute가 끝점 집합을 지원하지 않는다는 것을 의미합니다. 그러나 ER이 **아니요**라고 하여 끝점 집합에 보급되는 경로가 없다고 간주할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a7637-p108">**ER**: This is **Yes** if the endpoint set is supported over Azure ExpressRoute with Office 365 route prefixes. The BGP community that includes the route prefixes shown aligns with the service area listed. When ER is **No**, this means that ExpressRoute is not supported for this endpoint set. However, it should not be assumed that no routes are advertised for an endpoint set where ER is **No**.</span></span>

- <span data-ttu-id="a7637-p109">**주소**: 끝점 집합의 FQDN 또는 와일드카드 도메인 이름 및 IP 주소 범위를 보여줍니다. IP 주소 범위가 CIDR 형식이며 특정 네트워크에서 여러 개의 개별 IP 주소를 포함할 수 있다는 점에 유의하시기 바랍니다.</span><span class="sxs-lookup"><span data-stu-id="a7637-p109">**Addresses**: Lists the FQDNs or wildcard domain names and IP Address ranges for the endpoint set. Note that an IP Address range is in CIDR format and may include many individual IP Addresses in the specified network.</span></span>
 
- <span data-ttu-id="a7637-p110">**포트**: 주소와 결합하여 네트워크 끝점을 이루는 TCP 또는 UDP 포트를 나열합니다. 다른 포트도 나열되어 있으면, IP 주소 범위에서 몇 가지 중복되는 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7637-p110">**Ports**: Lists the TCP or UDP ports that are combined with the Addresses to form the network endpoint. You may notice some duplication in IP Address ranges where there are different ports listed.</span></span>

[!INCLUDE [Office 365 Germany endpoints](./includes/office-365-germany-endpoints.md)]

 

