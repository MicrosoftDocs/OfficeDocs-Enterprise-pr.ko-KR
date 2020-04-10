---
title: Microsoft 365 네트워크 연결 위치 서비스 (미리 보기)
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 03/31/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Microsoft 365 네트워크 연결 위치 서비스 (미리 보기)
ms.openlocfilehash: 13ca35afe4bd375482a9fc924801e240c361bb6b
ms.sourcegitcommit: 6508db0a839427e1a21b1cde883d828e3c8886c6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "43185729"
---
# <a name="microsoft-365-network-connectivity-location-services-preview"></a><span data-ttu-id="95a5a-103">Microsoft 365 네트워크 연결 위치 서비스 (미리 보기)</span><span class="sxs-lookup"><span data-stu-id="95a5a-103">Microsoft 365 Network Connectivity Location Services (preview)</span></span>

<span data-ttu-id="95a5a-104">Microsoft 365 관리 센터에는 이제 Microsoft 365 테 넌 트에서 수집 되며 테 넌 트의 관리 사용자만 볼 수 있는 live performance 메트릭이 있는 **네트워크 Insights 및 성능 권장 사항이**나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95a5a-104">The Microsoft 365 Admin Center now shows **Network Insights and performance recommendations**, which are live performance metrics collected from your Microsoft 365 tenant and available to view only by administrative users in your tenant.</span></span> <span data-ttu-id="95a5a-105">조직 네트워크 연결은 네트워크 송신 위치를 통해 인터넷으로 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="95a5a-105">Organizational network connectivity is designed per office location through a network egress location to the Internet.</span></span> <span data-ttu-id="95a5a-106">Microsoft 365 클라이언트 연결은이 경로를 사용 하 여 인터넷을 통해 Microsoft 서비스 전면 도어 서버로 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="95a5a-106">Microsoft 365 client connectivity uses that route and then across the Internet to Microsoft service front door servers.</span></span> <span data-ttu-id="95a5a-107">Office 위치를 확인 하는 것은 이러한 네트워크 통찰력을 표시할 수 있는 열쇠입니다.</span><span class="sxs-lookup"><span data-stu-id="95a5a-107">Identifying office locations is key to being able to show these network insights.</span></span>

## <a name="location-in-network-measurements"></a><span data-ttu-id="95a5a-108">네트워크 측정의 위치</span><span class="sxs-lookup"><span data-stu-id="95a5a-108">Location in network measurements</span></span>

<span data-ttu-id="95a5a-109">조직의 관리자가이 기능에서 사용 하는 네트워크 측정값에 포함할 위치를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95a5a-109">An organization's administrator can opt in for location to be included in the network measurements used by this feature.</span></span> <span data-ttu-id="95a5a-110">이렇게 하면 각 office가 있는 도시의 자동 검색이 가능해 집니다.</span><span class="sxs-lookup"><span data-stu-id="95a5a-110">This enables auto-discovery of the city where each office is located.</span></span> <span data-ttu-id="95a5a-111">위치 정보는 정확 하지 않으며 300m로 난독 처리 되며 도시별로 분류 됩니다.</span><span class="sxs-lookup"><span data-stu-id="95a5a-111">Location information is not precise and is obfuscated to 300m and categorized by city.</span></span> <span data-ttu-id="95a5a-112">Windows 디바이스에서 위치를 캡처하면 도구 트레이에 위치 하는 **사용** 중 아이콘이 표시 되 고 관리자가이를 사용자에 게 알릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95a5a-112">At the time when location is captured on a Windows device it will show a **Location In-Use** icon in the tool tray and administrators may want to notify users of this.</span></span> <span data-ttu-id="95a5a-113">이 처리를 통해 위치는 회사 사무실 위치로 취급 되 고 개인 또는 장치의 위치는 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="95a5a-113">With this processing, the location is treated as the organization office location and not the location of a person or a device.</span></span> <span data-ttu-id="95a5a-114">네트워크 insights는 이러한 검색 된 office 위치 도시에 표시 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95a5a-114">Network insights can be shown at these discovered office location cities.</span></span> <span data-ttu-id="95a5a-115">추천 값이 더 필요한 경우 관리자는 특정 office 위치 주소를 입력할 수 있으며 네트워크 insights가 대신 집계 됩니다.</span><span class="sxs-lookup"><span data-stu-id="95a5a-115">If greater accuracy of recommendations is desired, an administrator can enter specific office location addresses and the network insights will be aggregated to those instead.</span></span> <span data-ttu-id="95a5a-116">Office 위치를 300 미터 보다 더 가깝게 집계할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="95a5a-116">Office locations cannot be aggregated more closely than 300 meters.</span></span>

## <a name="location-in-the-microsoft-365-admin-center"></a><span data-ttu-id="95a5a-117">Microsoft 365 관리 센터의 위치</span><span class="sxs-lookup"><span data-stu-id="95a5a-117">Location in the Microsoft 365 Admin Center</span></span>

<span data-ttu-id="95a5a-118">Microsoft 365 관리 센터에서 Bing 지도 컨트롤은 조직 사무실 위치를 표시 하 고 선택한 사무실 위치에 대 한 네트워크 경계 토폴로지를 표시 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="95a5a-118">In the Microsoft 365 Admin Center, Bing map controls are used to show where organization office locations are and to show network perimeter topology for a selected office location.</span></span> <span data-ttu-id="95a5a-119">관리자가 office 위치에 대 한 특정 주소 세부 정보를 추가할 때 Bing 맵은 데이터를 보다 쉽게 입력할 수 있도록 주소를 제안 하는 데에도 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="95a5a-119">When an administrator adds specific address details for office locations, Bing Maps is also used to suggest addresses to make data entry easier.</span></span>

## <a name="terms-of-use"></a><span data-ttu-id="95a5a-120">사용 약관</span><span class="sxs-lookup"><span data-stu-id="95a5a-120">Terms of Use</span></span>

<span data-ttu-id="95a5a-121">Geocodes를 비롯 하 여 Bing 지도를 통해 제공 되는 모든 콘텐츠는 콘텐츠를 제공 하는 제품 내 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95a5a-121">Any content provided through Bing Maps, including geocodes, can only be used within the product through which the content is provided.</span></span> <span data-ttu-id="95a5a-122">Microsoft 365 관리 센터 Location Services 기능을 사용 하 여 Bing 지도를 통해 제공 되는 고객은 _Bing 지도 최종 사용자의 사용 약관_ <https://go.microsoft.com/?linkid=9710837> 및에서 _microsoft 개인 정보 취급_ 방침을 사용할 수 있습니다.<https://go.microsoft.com/fwlink/?LinkID=248686.></span><span class="sxs-lookup"><span data-stu-id="95a5a-122">Customer's use of the Microsoft 365 Admin Center Location Services feature, powered by Bing Maps, is governed by the _Bing Maps End User Terms of Use_ available at <https://go.microsoft.com/?linkid=9710837> and the _Microsoft Privacy Statement_ available at <https://go.microsoft.com/fwlink/?LinkID=248686.></span></span>

<span data-ttu-id="95a5a-123">Bing 지도를 통해 제공 되는이 기능은 여기에서 지 원하는 **기술**에서도 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="95a5a-123">This feature, provided through Bing Maps, is also supported by **Here Technologies**.</span></span> <span data-ttu-id="95a5a-124">Bing Maps에서 제공 하는 기술 _서비스 용어_ 에 따라 지원 되는 위치 서비스가 활용 됩니다 <https://legal.here.com/en-gb/terms>.</span><span class="sxs-lookup"><span data-stu-id="95a5a-124">How Bing Maps leverages location services provided by Here Technologies is governed by the _Here Technologies Service Terms_ available at <https://legal.here.com/en-gb/terms>.</span></span>
