---
title: Office 365 IP 주소 및 URL 웹 서비스
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 8/6/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.reviewer: pandrew
search.appverid:
- MET150
- MOE150
- BCS160
description: Office 365 IP 주소 및 URL 웹 서비스를 통해 Office 365 네트워크 트래픽을 보다 잘 식별하고 차별화할 수 있으므로 변경 사항을 보다 쉽게 평가, 구성 하고 최신 상태로 유지할 수 있습니다.
ms.openlocfilehash: 7a1d882b6bc5e34e3d59cf4bade30a58a1c76d6f
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843601"
---
# <a name="office-365-ip-address-and-url-web-service"></a><span data-ttu-id="5fd7b-103">Office 365 IP 주소 및 URL 웹 서비스</span><span class="sxs-lookup"><span data-stu-id="5fd7b-103">Office 365 IP Address and URL web service</span></span>

<span data-ttu-id="5fd7b-104">Office 365 IP 주소 및 URL 웹 서비스를 통해 Office 365 네트워크 트래픽을 보다 잘 식별하고 차별화할 수 있으므로 변경 사항을 보다 쉽게 평가, 구성 하고 최신 상태로 유지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-104">The Office 365 IP Address and URL web service helps you better identify and differentiate Office 365 network traffic, making it easier for you to evaluate, configure, and stay up to date with changes.</span></span> <span data-ttu-id="5fd7b-105">이 REST 기반 웹 서비스는 2018년 10월 2일에 단계적으로 폐지된 이전 XML 다운로드 가능 파일을 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-105">This REST-based web service replaces the previous XML downloadable files, which were phased out on October 2, 2018.</span></span>

<span data-ttu-id="5fd7b-106">고객 또는 네트워크 주변 장치 공급 업체는 Office 365 IP 주소 및 FQDN 항목에 대한 웹 서비스를 구축할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-106">As a customer or a network perimeter device vendor, you can build against the web service for Office 365 IP address and FQDN entries.</span></span> <span data-ttu-id="5fd7b-107">웹 브라우저에서 다음 URL을 사용하여 데이터에 직접 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-107">You can access the data directly in a web browser using these URLs:</span></span>

- <span data-ttu-id="5fd7b-108">최신 버전의 Office 365 URL 및 IP 주소 범위에 대해서는 [https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-108">For the latest version of the Office 365 URLs and IP address ranges, use [https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>
- <span data-ttu-id="5fd7b-109">Office 365 URL 및 방화벽과 프록시 서버에 대한 IP 주소 범위 데이터에 대해서는 [https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-109">For the data on the Office 365 URLs and IP address ranges page for firewalls and proxy servers, use [https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>
- <span data-ttu-id="5fd7b-110">웹 서비스를 처음 사용할 수 있던 2018년 7월 이후의 모든 최신 변경 내용을 가져오려면 [https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-110">To get all the latest changes since July 2018 when the web service was first available, use [https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>

<span data-ttu-id="5fd7b-111">고객은 이 웹 서비스를 사용하여 다음을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-111">As a customer, you can use this web service to:</span></span>

- <span data-ttu-id="5fd7b-112">Office 365 끝점 데이터를 가져오고 네트워킹 장치에 대한 모든 서식을 수정하기 위한 PowerShell 스크립트를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-112">Update your PowerShell scripts to obtain Office 365 endpoint data and modify any formatting for your networking devices.</span></span>
- <span data-ttu-id="5fd7b-113">이 정보를 사용하여 클라이언트 컴퓨터에 배포된 PAC 파일을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-113">Use this information to update PAC files deployed to client computers.</span></span>

<span data-ttu-id="5fd7b-114">네트워크 주변 장치 공급업체는 이 웹 서비스를 사용하여 다음을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-114">As a network perimeter device vendor, you can use this web service to:</span></span>

- <span data-ttu-id="5fd7b-115">자동화된 구성 목록을 다운로드하기 위한 장치 소프트웨어를 만들고 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-115">Create and test device software to download the list for automated configuration.</span></span>
- <span data-ttu-id="5fd7b-116">현재 버전을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-116">Check for the current version.</span></span>
- <span data-ttu-id="5fd7b-117">현재 변경 내용을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-117">Get the current changes.</span></span>

> [!NOTE]
> <span data-ttu-id="5fd7b-118">Azure ExpressRoute를 사용하여 Office 365에 연결하는 경우 Azure ExpressRoute에서 지원되는 Office 365 서비스에 익숙해질 수 있또록 [Office 365용 Azure ExpressRoute](https://docs.microsoft.com/office365/enterprise/azure-expressroute)를 검토하십시오.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-118">If you are using Azure ExpressRoute to connect to Office 365, please review [Azure ExpressRoute for Office 365](https://docs.microsoft.com/office365/enterprise/azure-expressroute) to familiarize yourself with the Office 365 services supported over Azure ExpressRoute.</span></span> <span data-ttu-id="5fd7b-119">또한 [Office 365 URL 및 IP 주소 범위](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges?redirectSourcePath=%252farticle%252fOffice-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) 문서를 검토하여 Office 365 응용 프로그램의 네트워크 연결 중 인터넷 연결이 필요한 것은 무엇인지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-119">Also review the article [Office 365 URLs and IP address ranges](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges?redirectSourcePath=%252farticle%252fOffice-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) to understand which network requests for Office 365 applications require Internet connectivity.</span></span> <span data-ttu-id="5fd7b-120">이렇게 하면 주변 보안 장치를 보다 잘 구성하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-120">This will help to better configure your perimeter security devices.</span></span>

<span data-ttu-id="5fd7b-121">자세한 내용은 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-121">For more information, see:</span></span>

- [<span data-ttu-id="5fd7b-122">Office 365 기술 커뮤니티 포럼의 공지 사항 블로그 게시물</span><span class="sxs-lookup"><span data-stu-id="5fd7b-122">Announcement blog post in the Office 365 Tech Community Forum</span></span>](https://techcommunity.microsoft.com/t5/Office-365-Blog/Announcing-Office-365-endpoint-categories-and-Office-365-IP/ba-p/177638)
- [<span data-ttu-id="5fd7b-123">웹 서비스 사용에 대한 질문이 있는 경우 Office 365 기술 커뮤니티 포럼</span><span class="sxs-lookup"><span data-stu-id="5fd7b-123">Office 365 Tech Community Forum for questions about use of the web services</span></span>](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)

## <a name="common-parameters"></a><span data-ttu-id="5fd7b-124">일반 매개 변수</span><span class="sxs-lookup"><span data-stu-id="5fd7b-124">Common parameters</span></span>

<span data-ttu-id="5fd7b-125">다음은 모든 웹 서비스 메서드에서 공통되는 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-125">These parameters are common across all the web service methods:</span></span>

- <span data-ttu-id="5fd7b-126">**format=<JSON | CSV>** - 기본적으로 반환되는 데이터 형식은 JSON입니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-126">**format=<JSON | CSV>** — By default, the returned data format is JSON.</span></span> <span data-ttu-id="5fd7b-127">이 선택적 매개 변수를 사용하여 쉼표로 구분된 값(CSV) 형식으로 데이터를 반환하십시오.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-127">Use this optional parameter to return the data in comma-separated values (CSV) format.</span></span>
- <span data-ttu-id="5fd7b-128">**ClientRequestId =\<guid >** - 클라이언트 연결을 위해 생성해야 하는 필수 GUID입니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-128">**ClientRequestId=\<guid>** — A required GUID that you generate for client association.</span></span> <span data-ttu-id="5fd7b-129">웹 서비스를 호출하는 각 시스템에 대해 고유한 GUID를 생성합니다(이 페이지에 포함된 스크립트가 GUID를 생성함).</span><span class="sxs-lookup"><span data-stu-id="5fd7b-129">Generate a unique GUID for each machine that calls the web service (the scripts included on this page generate a GUID for you).</span></span> <span data-ttu-id="5fd7b-130">다음 예제에 표시된 GUID는 앞으로 웹 서비스에 의해 차단될 수 있으므로 사용하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-130">Do not use the GUIDs shown in the following examples because they might be blocked by the web service in the future.</span></span> <span data-ttu-id="5fd7b-131">GUID 형식은 _xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx_이며 여기서 x는 16진수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-131">GUID format is _xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx_, where x represents a hexadecimal number.</span></span>

  <span data-ttu-id="5fd7b-132">GUID를 생성하려면 [New-Guid](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6) PowerShell 명령을 사용하거나 [Online GUID 생성기](https://www.guidgenerator.com/)와 같은 온라인 서비스를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-132">To generate a GUID, you can use the [New-Guid](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6) PowerShell command, or use an online service such as [Online GUID Generator](https://www.guidgenerator.com/).</span></span>

## <a name="version-web-method"></a><span data-ttu-id="5fd7b-133">버전 웹 메서드</span><span class="sxs-lookup"><span data-stu-id="5fd7b-133">Version web method</span></span>

<span data-ttu-id="5fd7b-134">Microsoft는 매월 마지막에 Office 365 IP 주소와 FQDN 항목을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-134">Microsoft updates the Office 365 IP address and FQDN entries at the end of each month.</span></span> <span data-ttu-id="5fd7b-135">지원 인시던트, 보안 업데이트 또는 기타 운영 요구 사항으로 인해 대역 외 업데이트가 게시되는 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-135">Out-of-band updates are sometimes published due to support incidents, security updates or other operational requirements.</span></span>

<span data-ttu-id="5fd7b-136">게시된 각 인스턴스의 데이터에는 버전 번호가 할당되며 버전 웹 메소드를 사용하면 각 Office 365 서비스 인스턴스의 최신 버전을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-136">The data for each published instance is assigned a version number, and the version web method enables you to check for the latest version of each Office 365 service instance.</span></span> <span data-ttu-id="5fd7b-137">한 시간에 한 번 이하로 버전을 확인하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-137">We recommend that you check the version not more than once an hour.</span></span>

<span data-ttu-id="5fd7b-138">버전 웹 메서드의 매개 변수는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-138">Parameters for the version web method are:</span></span>

- <span data-ttu-id="5fd7b-139">**AllVersions = < true | false >** -기본적으로 반환되는 버전은 최신 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-139">**AllVersions=<true | false>** — By default, the version returned is the latest.</span></span> <span data-ttu-id="5fd7b-140">이 선택적 매개 변수를 포함하여 웹 서비스가 처음 릴리스된 이후에 모든 게시된 버전을 요청하십시오.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-140">Include this optional parameter to request all published versions since the web service was first released.</span></span>
- <span data-ttu-id="5fd7b-141">**형식 = < JSON | CSV | RSS >** -는 JSON 및 CSV 형식 외에도 버전 웹 메서드로도 RSS를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-141">**Format=<JSON | CSV | RSS>** — In addition to the JSON and CSV formats, the version web method also supports RSS.</span></span> <span data-ttu-id="5fd7b-142">이 선택적 매개 변수를 _AllVersions = true_ 매개 변수와 함께 사용하여 Outlook이나 다른 RSS 판독기에서 사용할 수 있는 RSS 피드를 요청할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-142">You can use this optional parameter along with the _AllVersions=true_ parameter to request an RSS feed that can be used with Outlook or other RSS readers.</span></span>
- <span data-ttu-id="5fd7b-143">\*\*인스턴스=<전세계 | 중국 | 독일 | USGovDoD | USGovGCCHigh> \*\* -이 선택적 매개 변수는 버전을 반환할 인스턴스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-143">**Instance=<Worldwide | China | Germany | USGovDoD | USGovGCCHigh>** — This optional parameter specifies the instance to return the version for.</span></span> <span data-ttu-id="5fd7b-144">생략할 경우 모든 인스턴스가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-144">If omitted, all instances are returned.</span></span> <span data-ttu-id="5fd7b-145">유효한 인스턴스는 전세계, 중국, 독일, USGovDoD, USGovGCCHigh입니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-145">Valid instances are: Worldwide, China, Germany, USGovDoD, USGovGCCHigh.</span></span>

<span data-ttu-id="5fd7b-146">버전 웹 메소드는 속도 제한이 없으며 429 HTTP 응답 코드를 반환하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-146">The version web method is not rate limited and does not ever return 429 HTTP Response Codes.</span></span> <span data-ttu-id="5fd7b-147">버전 웹 방법에 대한 응답에는 1시간 동안 데이터 캐싱을 권장하는 캐시 제어 헤더가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-147">The response to the version web method does include a cache-control header recommending caching of the data for 1 hour.</span></span> <span data-ttu-id="5fd7b-148">버전 웹 메서드의 결과는 단일 레코드 또는 레코드의 배열일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-148">The result from the version web method can be a single record or an array of records.</span></span> <span data-ttu-id="5fd7b-149">각 레코드의 요소는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-149">The elements of each record are:</span></span>

- <span data-ttu-id="5fd7b-150">instance - Office 365 서비스 인스턴스의 짧은 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-150">instance — The short name of the Office 365 service instance.</span></span>
- <span data-ttu-id="5fd7b-151">latest - 지정된 인스턴스 끝점의 최신 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-151">latest — The latest version for endpoints of the specified instance.</span></span>
- <span data-ttu-id="5fd7b-152">versions - 지정된 인스턴스의 모든 이전 버전 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-152">versions — A list of all previous versions for the specified instance.</span></span> <span data-ttu-id="5fd7b-153">이 요소는 _AllVersions_ 매개 변수가 true인 경우에만 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-153">This element is only included if the _AllVersions_ parameter is true.</span></span>

### <a name="examples"></a><span data-ttu-id="5fd7b-154">예제:</span><span class="sxs-lookup"><span data-stu-id="5fd7b-154">Examples:</span></span>

<span data-ttu-id="5fd7b-155">예제 1 요청 URI: [https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="5fd7b-155">Example 1 request URI: [https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="5fd7b-p113">이 URI은 각 Office 365 서비스 인스턴스의 최신 버전을 반환합니다. 예제 결과:</span><span class="sxs-lookup"><span data-stu-id="5fd7b-p113">This URI returns the latest version of each Office 365 service instance. Example result:</span></span>

```json
[
 {
  "instance": "Worldwide",
  "latest": "2018063000"
 },
 {
  "instance": "USGovDoD",
  "latest": "2018063000"
 },
 {
  "instance": "USGovGCCHigh",
  "latest": "2018063000"
 },
 {
  "instance": "China",
  "latest": "2018063000"
 },
 {
  "instance": "Germany",
  "latest": "2018063000"
 }
]
```

> [!IMPORTANT]
> <span data-ttu-id="5fd7b-p114">이러한 URI의 ClientRequestID 매개 변수에 대한 GUID는 예제에 불과합니다. 웹 서비스 URL을 사용해보려면 자체 GUID를 생성합니다. 이러한 예제에 표시되는 GUID는 앞으로 웹 서비스에 의해 차단될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-p114">The GUID for the ClientRequestID parameter in these URIs are only an example. To try the web service URIs out, generate your own GUID. The GUIDs shown in these examples may be blocked by the web service in the future.</span></span>

<span data-ttu-id="5fd7b-161">예제 2 요청 URI: [https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="5fd7b-161">Example 2 request URI: [https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="5fd7b-p115">이 URI은 지정된 Office 365 서비스 인스턴스의 최신 버전을 반환합니다. 예제 결과:</span><span class="sxs-lookup"><span data-stu-id="5fd7b-p115">This URI returns the latest version of the specified Office 365 service instance. Example result:</span></span>

```json
{
 "instance": "Worldwide",
 "latest": "2018063000"
}
```

<span data-ttu-id="5fd7b-164">예제 3 요청 URI: [https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="5fd7b-164">Example 3 request URI: [https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="5fd7b-p116">이 URI는 출력을 CSV 형식으로 표시합니다. 예제 결과:</span><span class="sxs-lookup"><span data-stu-id="5fd7b-p116">This URI shows output in CSV format. Example result:</span></span>

```csv
instance,latest
Worldwide,2018063000
```

<span data-ttu-id="5fd7b-167">예제 4 요청 URI: [https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="5fd7b-167">Example 4 request URI: [https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="5fd7b-p117">이 URI는 Office 365 Worldwide 서비스 인스턴스에 대해 게시된 모든 이전 버전을 보여 줍니다. 예제 결과:</span><span class="sxs-lookup"><span data-stu-id="5fd7b-p117">This URI shows all prior versions that have been published for the Office 365 worldwide service instance. Example result:</span></span>

```json
{
  "instance": "Worldwide",
  "latest": "2018063000",
  "versions": [
    "2018063000",
    "2018062000"
  ]
}
```

<span data-ttu-id="5fd7b-170">예제 5 RSS 피드 URI: [https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS](https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS)</span><span class="sxs-lookup"><span data-stu-id="5fd7b-170">Example 5 RSS Feed URI: [https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS](https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS)</span></span>

<span data-ttu-id="5fd7b-p118">이 URI는 각 버전의 변경 내용 목록에 대한 링크를 포함하는 게시된 버전의 RSS 피드를 보여 줍니다. 예제 결과:</span><span class="sxs-lookup"><span data-stu-id="5fd7b-p118">This URI shows an RSS feed of the published versions that include links to the list of changes for each version. Example result:</span></span>

```xml
<?xml version="1.0" encoding="ISO-8859-1"?>
<rss version="2.0" xmlns:a10="https://www.w3.org/2005/Atom">
<channel>
<link>https://aka.ms/o365ip</link>
<description/>
<language>en-us</language>
<lastBuildDate>Thu, 02 Aug 2018 00:00:00 Z</lastBuildDate>
<item>
<guid isPermaLink="false">2018080200</guid>
<link>https://endpoints.office.com/changes/Worldwide/2018080200?singleVersion&clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7</link> <description>Version 2018080200 includes 2 changes. IPs: 2 added and 0 removed.</description>
<pubDate>Thu, 02 Aug 2018 00:00:00 Z</pubDate>
</item>
```

## <a name="endpoints-web-method"></a><span data-ttu-id="5fd7b-173">엔드포인트 웹 메서드</span><span class="sxs-lookup"><span data-stu-id="5fd7b-173">Endpoints web method</span></span>

<span data-ttu-id="5fd7b-174">엔드포인트 웹 메서드는 Office 365 서비스를 구성하는 IP 주소 범위 및 URL에 대한 모든 레코드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-174">The endpoints web method returns all records for IP address ranges and URLs that make up the Office 365 service.</span></span> <span data-ttu-id="5fd7b-175">끝점 웹 메서드의 최신 데이터는 항상 네트워크 장치 구성에 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-175">The latest data from the endpoints web method should always be used for network device configuration.</span></span> <span data-ttu-id="5fd7b-176">Microsoft는 새로운 추가 기능을 게시하기 30일 전에 미리 액세스 제어 목록 및 프록시 서버 우회 목록을 업데이트할 수 있도록 미리 알림을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-176">Microsoft provides advance notice 30 days prior to publishing new additions to give you time to update access control lists and proxy server bypass lists.</span></span> <span data-ttu-id="5fd7b-177">버전 웹 메소드가 새 버전의 데이터를 사용할 수 있음을 나타내면 엔드 포인트 웹 메소드만 다시 호출할 것을 권장합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-177">We recommend that you only call the endpoints web method again when the version web method indicates that a new version of the data is available.</span></span>

<span data-ttu-id="5fd7b-178">엔드포인트 웹 메서드의 매개 변수는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-178">Parameters for the endpoints web method are:</span></span>

- <span data-ttu-id="5fd7b-179">\*\*ServiceAreas=<공통 | 교환 | SharePoint | Skype> \*\* - 쉼표로 구분 된 서비스 영역 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-179">**ServiceAreas=<Common | Exchange | SharePoint | Skype>** — A comma-separated list of service areas.</span></span> <span data-ttu-id="5fd7b-180">유효한 항목은 _공통_, _Exchange_, _SharePoint_ 및 _Skype_입니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-180">Valid items are _Common_, _Exchange_, _SharePoint_, and _Skype_.</span></span> <span data-ttu-id="5fd7b-181">_공통_ 서비스 영역 항목은 다른 모든 서비스 영역의 전제 조건이므로 웹 서비스에 항상 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-181">Because _Common_ service area items are a prerequisite for all other service areas, the web service always includes them.</span></span> <span data-ttu-id="5fd7b-182">이 매개 변수를 포함하지 않으면 모든 서비스 영역이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-182">If you do not include this parameter, all service areas are returned.</span></span>
- <span data-ttu-id="5fd7b-183">**TenantName=<tenant_name >** - Office 365 테넌트 이름.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-183">**TenantName=<tenant_name>** — Your Office 365 tenant name.</span></span> <span data-ttu-id="5fd7b-184">웹 서비스는 제공된 이름을 가져와 테넌트 이름이 포함된 URL의 일부에 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-184">The web service takes your provided name and inserts it in parts of URLs that include the tenant name.</span></span> <span data-ttu-id="5fd7b-185">테넌트 이름을 제공하지 않으면 URL의 해당 부분에 와일드 카드 문자(\*)가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-185">If you don't provide a tenant name, those parts of URLs have the wildcard character (\*).</span></span>
- <span data-ttu-id="5fd7b-186">**NoIPv6=<true | false>** - 네트워크에서 IPv6를 사용하지 않는 경우 출력에서 IPv6 주소를 제외하려면 이 매개 변수를 _true_로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-186">**NoIPv6=<true | false>** — Set the value to _true_ to exclude IPv6 addresses from the output if you don't use IPv6 in your network.</span></span>
- <span data-ttu-id="5fd7b-187">\*\*인스턴스=<전세계 | 중국 | 독일 | USGovDoD | USGovGCCHigh> \*\* -이 필수 매개 변수는 끝점을 반환할 인스턴스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-187">**Instance=<Worldwide | China | Germany | USGovDoD | USGovGCCHigh>** — This required parameter specifies the instance from which to return the endpoints.</span></span> <span data-ttu-id="5fd7b-188">유효한 인스턴스는 _전세계_, _중국_, _독일_, _USGovDoD_, _USGovGCCHigh_입니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-188">Valid instances are: _Worldwide_, _China_, _Germany_, _USGovDoD_, and _USGovGCCHigh_.</span></span>

<span data-ttu-id="5fd7b-189">끝점 웹 메서드를 동일한 클라이언트 IP 주소에서 너무 많이 호출하면 HTTP 응답 코드 _429(너무 많은 요청)_ 가 수신될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-189">If you call the endpoints web method too many times from the same client IP address, you might receive HTTP response code _429 (Too Many Requests)_.</span></span> <span data-ttu-id="5fd7b-190">이 응답 코드를 받은 경우, 다시 요청을 반복하기까지 1시간을 기다리거나 요청에 대한 새 GUID를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-190">If you get this response code, wait 1 hour before repeating your request, or generate a new GUID for the request.</span></span> <span data-ttu-id="5fd7b-191">일반적으로 버전 웹 메서드가 사용 가능한 새 버전이 있음을 표시하면 끝점 웹 메서드 만 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-191">As a general best practice, only call the endpoints web method when the version web method indicates that a new version is available.</span></span>

<span data-ttu-id="5fd7b-192">끝점 웹 메소드의 결과는 각 레코드가 특정 끝점 집합을 나타내는 레코드 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-192">The result from the endpoints web method is an array of records in which each record represents a specific endpoint set.</span></span> <span data-ttu-id="5fd7b-193">각 레코드의 요소는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-193">The elements for each record are:</span></span>

- <span data-ttu-id="5fd7b-194">id - 끝점 집합의 변경이 불가능한 ID 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-194">id — The immutable id number of the endpoint set.</span></span>
- <span data-ttu-id="5fd7b-195">serviceArea - 이 요소가 속하는 서비스 영역은 _Common_, _Exchange_, _SharePoint_ 또는 _Skype_입니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-195">serviceArea — The service area that this is part of: _Common_, _Exchange_, _SharePoint_, or _Skype_.</span></span>
- <span data-ttu-id="5fd7b-196">urls - 끝점 집합의 URL입니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-196">urls — URLs for the endpoint set.</span></span> <span data-ttu-id="5fd7b-197">DNS 레코드의 JSON 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-197">A JSON array of DNS records.</span></span> <span data-ttu-id="5fd7b-198">비워 두면 생략됩니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-198">Omitted if blank.</span></span>
- <span data-ttu-id="5fd7b-199">tcpPorts - 끝점 집합의 TCP 포트입니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-199">tcpPorts — TCP ports for the endpoint set.</span></span> <span data-ttu-id="5fd7b-200">모든 포트 요소는 쉼표로 구분된 포트 또는 포트 범위가 대시 문자(-)로 구분되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-200">All ports elements are formatted as a comma-separated list of ports or port ranges separated by a dash character (-).</span></span> <span data-ttu-id="5fd7b-201">포트는 주어진 범주에 대한 끝점에 설정된 모든 IP 주소 및 모든 URL에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-201">Ports apply to all IP addresses and all URLs in the endpoint set for a given category.</span></span> <span data-ttu-id="5fd7b-202">비워 두면 생략됩니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-202">Omitted if blank.</span></span>
- <span data-ttu-id="5fd7b-203">udpPorts - 이 끝점 집합의 IP 주소 범위에 대한 UDP 포트입니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-203">udpPorts — UDP ports for the IP address ranges in this endpoint set.</span></span> <span data-ttu-id="5fd7b-204">비워 두면 생략됩니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-204">Omitted if blank.</span></span>
- <span data-ttu-id="5fd7b-205">ips - 나열된 TCP 또는 UDP 포트와 연결된 이 끝점 집합과 연결된 IP 주소 범위입니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-205">ips — The IP address ranges associated with this endpoint set as associated with the listed TCP or UDP ports.</span></span> <span data-ttu-id="5fd7b-206">IP 주소 범위의 JSON 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-206">A JSON array of IP address ranges.</span></span> <span data-ttu-id="5fd7b-207">비워 두면 생략됩니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-207">Omitted if blank.</span></span>
- <span data-ttu-id="5fd7b-208">category - 끝점 집합에 대한 연결 범주입니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-208">category — The connectivity category for the endpoint set.</span></span> <span data-ttu-id="5fd7b-209">유효한 값은 _최적화_, _허용_및 _기본값_입니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-209">Valid values are _Optimize_, _Allow_, and _Default_.</span></span> <span data-ttu-id="5fd7b-210">특정 IP 주소 또는 URL 범주에 대한 끝점 웹 메서드 출력을 검색하는 경우에는 쿼리가 여러 범주를 반환하게 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-210">If you search the endpoints web method output for the category of a specific IP address or URL, it is possible that your query will return multiple categories.</span></span> <span data-ttu-id="5fd7b-211">이 경우 우선 순위가 가장 높은 범주에 대한 권장 사항을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-211">In such a case, follow the recommendation for the highest priority category.</span></span> <span data-ttu-id="5fd7b-212">예를 들어, 끝점 _최적화_와 _허용_ 둘 다에 표시되면 _최적화_ 요구 사항을 따라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-212">For example, if the endpoint appears in both _Optimize_ and _Allow_, you should follow the requirements for _Optimize_.</span></span> <span data-ttu-id="5fd7b-213">필수 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-213">Required.</span></span>
- <span data-ttu-id="5fd7b-214">expressRoute - 이 끝점 집합이 ExpressRoute를 통해 라우팅되는 경우 _True_ 그렇지 않으면 _False_입니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-214">expressRoute — _True_ if this endpoint set is routed over ExpressRoute, _False_ if not.</span></span>
- <span data-ttu-id="5fd7b-215">required - Office 365에 대한 연결이 지원되기 위해 이 끝점 집합이 필요한 경우 _True_입니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-215">required — _True_ if this endpoint set is required to have connectivity for Office 365 to be supported.</span></span> <span data-ttu-id="5fd7b-216">이 끝점 집합이 선택 사항이면 _False_입니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-216">_False_ if this endpoint set is optional.</span></span>
- <span data-ttu-id="5fd7b-217">notes - 선택적 끝점의 경우 이 텍스트는 네트워크 계층에서 이 끝점 집합의 IP 주소나 URL에 액세스할 수 없는 경우 사용할 수 없는 Office 365 기능에 대해 설명합니다. </span><span class="sxs-lookup"><span data-stu-id="5fd7b-217">notes — For optional endpoints, this text describes Office 365 functionality that would be unavailable if IP addresses or URLs in this endpoint set cannot be accessed at the network layer.</span></span> <span data-ttu-id="5fd7b-218">비워 두면 생략됩니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-218">Omitted if blank.</span></span>

### <a name="examples"></a><span data-ttu-id="5fd7b-219">예제:</span><span class="sxs-lookup"><span data-stu-id="5fd7b-219">Examples:</span></span>

<span data-ttu-id="5fd7b-220">예제 1 요청 URI: [https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="5fd7b-220">Example 1 request URI: [https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="5fd7b-221">이 URI은 모든 워크로드에 대한 Office 365 Worldwide 인스턴스에 대한 모든 끝점을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-221">This URI obtains all endpoints for the Office 365 worldwide instance for all workloads.</span></span> <span data-ttu-id="5fd7b-222">출력 일부를 보여 주는 예제 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-222">Example result that shows an excerpt of the output:</span></span>

```json
[
 {
  "id": 1,
  "serviceArea": "Exchange",
  "serviceAreaDisplayName": "Exchange Online",
  "urls":
   [
    "*.protection.outlook.com"
   ],
  "ips":
   [
    "2a01:111:f403::/48", "23.103.132.0/22", "23.103.136.0/21", "23.103.198.0/23", "23.103.212.0/22", "40.92.0.0/14", "40.107.0.0/17", "40.107.128.0/18", "52.100.0.0/14", "213.199.154.0/24", "213.199.180.128/26", "94.245.120.64/26", "207.46.163.0/24", "65.55.88.0/24", "216.32.180.0/23", "23.103.144.0/20", "65.55.169.0/24", "207.46.100.0/24", "2a01:111:f400:7c00::/54", "157.56.110.0/23", "23.103.200.0/22", "104.47.0.0/17", "2a01:111:f400:fc00::/54", "157.55.234.0/24", "157.56.112.0/24", "52.238.78.88/32"
   ],
  "tcpPorts": "443",
  "expressRoute": true,
  "category": "Allow"
 },
 {
  "id": 2,
  "serviceArea": "Exchange",
  "serviceAreaDisplayName": "Exchange Online",
  "urls":
   [
    "*.mail.protection.outlook.com"
   ],
```

<span data-ttu-id="5fd7b-223">이 예제에서 요청의 전체 결과에는 다른 끝점 집합이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-223">Note that the full output of the request in this example would contain other endpoint sets.</span></span>

<span data-ttu-id="5fd7b-224">예제 2 요청 URI: [https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="5fd7b-224">Example 2 request URI: [https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="5fd7b-225">이 예제에서는 Exchange Online에 대한 Office 365 Worldwide 인스턴스의 끝점과 종속성만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-225">This example obtains endpoints for the Office 365 Worldwide instance for Exchange Online and dependencies only.</span></span>

<span data-ttu-id="5fd7b-226">예제 2의 출력은 결과에 SharePoint Online 또는 비즈니스용 Skype Online에 대한 끝점이 포함되지 않는다는 점을 제외하고 예제 1과 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-226">The output for example 2 is similar to example 1 except that the results would not include endpoints for SharePoint Online or Skype for Business Online.</span></span>

## <a name="changes-web-method"></a><span data-ttu-id="5fd7b-227">변경 웹 메서드</span><span class="sxs-lookup"><span data-stu-id="5fd7b-227">Changes web method</span></span>

<span data-ttu-id="5fd7b-228">변경 웹 메서드에서는 게시된 최신 업데이트를 반환합니다. 일반적으로 지난 달의 IP 주소 범위 및 URL에 대한 변경 내용입니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-228">The changes web method returns the most recent updates that have been published, typically the previous month's changes to IP address ranges and URLs.</span></span>

<span data-ttu-id="5fd7b-229">끝점 데이터의 가장 중요한 변경 사항은 새 URL 및 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-229">The most critical changes to endpoints data are new URLs and IP addresses.</span></span> <span data-ttu-id="5fd7b-230">방화벽 액세스 제어 목록에 IP 주소를 추가하지 않거나 프록시 서버 바이패스 목록에 URL을 추가하지 않으면 해당 네트워크 장치 뒤에 있는 Office 365 사용자에게 중단이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-230">Failure to add an IP address to a firewall access control list or a URL to a proxy server bypass list can cause an outage for Office 365 users behind that network device.</span></span> <span data-ttu-id="5fd7b-231">운영 요구 사항에도 불구하고 액세스 제어 목록 및 프록시 서버 바이패스 목록을 업데이트할 시간을 제공하기 위해 끝점이 제공되는 날짜보다 30일 전에 새 끝점이 웹 서비스에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-231">Notwithstanding operational requirements, new endpoints are published to the web service 30 days in advance of the date the endpoints are provisioned for use to give you time to update access control lists and proxy server bypass lists.</span></span>

<span data-ttu-id="5fd7b-232">변경 내용 웹 메서드에 대한 필수 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-232">The required parameter for the changes web method is:</span></span>

- <span data-ttu-id="5fd7b-233">\*\* 버전 = \<YYYYMMDDNN>\*\* - 필수 URL 경로 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-233">**Version=\<YYYYMMDDNN>** — Required URL route parameter.</span></span> <span data-ttu-id="5fd7b-234">이 값은 현재 구현한 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-234">This value is the version that you have currently implemented.</span></span> <span data-ttu-id="5fd7b-235">웹 서비스는 해당 버전 이후의 변경 사항을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-235">The web service will return the changes since that version.</span></span> <span data-ttu-id="5fd7b-236">형식은 _YYYYMMDD_입니다. 여기서 _NN_은 하루 동안 게시해야하는 여러 버전이 있는 경우 자연수 증가분이고 _00_은 해당 날짜의 첫 번째 업데이트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-236">The format is _YYYYMMDDNN_, where _NN_ is a natural number incremented if there are multiple versions required to be published on a single day, with _00_ representing the first update for a given day.</span></span> <span data-ttu-id="5fd7b-237">웹 서비스는 _버전_ 매개 변수가 정확히 10 자리를 포함하도록 요구합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-237">The web service requires the _version_ parameter to contain exactly 10 digits.</span></span>

<span data-ttu-id="5fd7b-238">변경 웹 메서드는 엔드 포인트 웹 메서드와 같은 방식으로 비율이 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-238">The changes web method is rate limited in the same way as the endpoints web method.</span></span> <span data-ttu-id="5fd7b-239">429 HTTP 응답 코드를 받은 경우, 다시 요청을 반복하기까지 1시간을 기다리거나 요청에 대한 새 GUID를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-239">If you receive a 429 HTTP response code, wait 1 hour before repeating your request or generate a new GUID for the request.</span></span>

<span data-ttu-id="5fd7b-240">변경 웹 메소드의 결과는 각 레코드가 특정 버전의 끝점에서 변경된 내용을 나타내는 레코드 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-240">The result from the changes web method is an array of records in which each record represents a change in a specific version of the endpoints.</span></span> <span data-ttu-id="5fd7b-241">각 레코드의 요소는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-241">The elements for each record are:</span></span>

- <span data-ttu-id="5fd7b-242">id - 변경 레코드의 변경이 불가능한 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-242">id — The immutable id of the change record.</span></span>
- <span data-ttu-id="5fd7b-243">endpointSetId - 변경된 끝점 집합 레코드의 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-243">endpointSetId — The ID of the endpoint set record that is changed.</span></span>
- <span data-ttu-id="5fd7b-244">disposition - 끝점 설정 레코드에 대한 변경 내용에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-244">disposition — Describes what the change did to the endpoint set record.</span></span> <span data-ttu-id="5fd7b-245">값은 _변경_, _추가_ 또는 _제거_입니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-245">Values are _change_, _add_, or _remove_.</span></span>
- <span data-ttu-id="5fd7b-246">impact - 모든 환경에서 모든 변경이 똑같이 중요하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-246">impact — Not all changes will be equally important to every environment.</span></span> <span data-ttu-id="5fd7b-247">이 요소는 이러한 변경으로 인해 엔터프라이즈 네트워크 주변 환경에 미치는 영향을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-247">This element describes the expected impact to an enterprise network perimeter environment as a result of this change.</span></span> <span data-ttu-id="5fd7b-248">이 요소는 버전 **2018112800** 이상의 변경 레코드에만 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-248">This element is included only in change records of version **2018112800** and later.</span></span> <span data-ttu-id="5fd7b-249">영향에 대한 옵션은 다음과 같습니다. — AddedIp – IP 주소가 Office 365에 추가되었고 곧 서비스에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-249">Options for the impact are: — AddedIp – An IP address was added to Office 365 and will be live on the service soon.</span></span> <span data-ttu-id="5fd7b-250">이는 방화벽 또는 다른 계층 3 네트워크 주변 장치에서 수행해야하는 변경 사항을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-250">This represents a change you need to take on a firewall or other layer 3 network perimeter device.</span></span> <span data-ttu-id="5fd7b-251">사용하기 전에 이것을 먼저 추가하지 않으면 중단이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-251">If you don’t add this before we start using it, you may experience an outage.</span></span>
  <span data-ttu-id="5fd7b-252">— AddedUrl - URL이 Office 365에 추가되었으며 곧 서비스에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-252">— AddedUrl – A URL was added to Office 365 and will be live on the service soon.</span></span> <span data-ttu-id="5fd7b-253">이는 프록시 서버 또는 URL 파싱 네트워크 주변 장치에서 수행해야하는 변경 사항을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-253">This represents a change you need to take on a proxy server or URL parsing network perimeter device.</span></span> <span data-ttu-id="5fd7b-254">사용하기 전에 이 URL을 먼저 추가하지 않으면 중단이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-254">If you don’t add this URL before we start using it, you may experience an outage.</span></span>
  <span data-ttu-id="5fd7b-255">— AddedIpAndUrl - IP 주소와 URL이 모두 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-255">— AddedIpAndUrl — Both an IP address and a URL were added.</span></span> <span data-ttu-id="5fd7b-256">이는 방화벽 계층 3 장치나 프록시 서버 또는 URL 구문 분석 장치에서 수행해야 하는 변경을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-256">This represents a change you need to take on either a firewall layer 3 device or a proxy server or URL parsing device.</span></span> <span data-ttu-id="5fd7b-257">사용하기 전에 이 IP/URL 쌍을 먼저 추가하지 않으면 중단이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-257">If you don’t add this IP/URL pair before we start using it, you may experience an outage.</span></span>
  <span data-ttu-id="5fd7b-258">— RemovedIpOrUrl – 적어도 하나의 IP 주소 또는 URL이 Office 365에서 제거되었습니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-258">— RemovedIpOrUrl – At least one IP address or URL was removed from Office 365.</span></span> <span data-ttu-id="5fd7b-259">주변 장치에서 네트워크 끝점을 제거하지만 이 작업은 마감일이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-259">Remove the network endpoints from your perimeter devices, but there’s no deadline for you to do this.</span></span>
  <span data-ttu-id="5fd7b-260">— ChangedIsExpressRoute – ExpressRoute 지원 속성이 변경되었습니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-260">— ChangedIsExpressRoute – The ExpressRoute support attribute was changed.</span></span> <span data-ttu-id="5fd7b-261">ExpressRoute를 사용하는 경우 구성에 따라 조치를 취해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-261">If you use ExpressRoute, you might need to take action depending on your configuration.</span></span>
  <span data-ttu-id="5fd7b-262">— MovedIpOrUrl – 이 끝점 세트와 다른 끝점 세트 간에 IP 주소 또는 URL을 이동했습니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-262">— MovedIpOrUrl – We moved an IP address or Url between this endpoint set and another one.</span></span> <span data-ttu-id="5fd7b-263">일반적으로 필요한 작업은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-263">Generally no action is required.</span></span>
  <span data-ttu-id="5fd7b-264">— RemovedDuplicateIpOrUrl – 중복된 IP 주소 또는 URL을 제거했으나 Office 365에 여전히 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-264">— RemovedDuplicateIpOrUrl – We removed a duplicate IP address or Url but it’s still published for Office 365.</span></span> <span data-ttu-id="5fd7b-265">일반적으로 필요한 작업은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-265">Generally no action is required.</span></span>
  <span data-ttu-id="5fd7b-266">— OtherNonPriorityChanges – 메모 필드와 같이 다른 옵션보다 덜 중요한 항목이 변경되었습니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-266">— OtherNonPriorityChanges – We changed something less critical than all of the other options, such as the contents of a note field.</span></span>
- <span data-ttu-id="5fd7b-267">version — 변경 사항이 도입된 게시된 끝점 집합의 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-267">version — The version of the published endpoint set in which the change was introduced.</span></span> <span data-ttu-id="5fd7b-268">버전 번호의 형식은 _YYYYMMDD_입니다. 여기서 _NN_은 하루 동안 게시해야 하는 여러 버전이 있는 경우 자연수 증가분입니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-268">Version numbers are of the format _YYYYMMDDNN_, where _NN_ is a natural number incremented if there are multiple versions required to be published on a single day.</span></span>
- <span data-ttu-id="5fd7b-269">previous - 끝점 집합에서 변경된 요소의 이전 값을 설명하는 하위 구조입니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-269">previous — A substructure detailing previous values of changed elements on the endpoint set.</span></span> <span data-ttu-id="5fd7b-270">새로 추가된 엔드포인트 집합에는 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-270">This will not be included for newly added endpoint sets.</span></span> <span data-ttu-id="5fd7b-271">_ExpressRoute_, _serviceArea_, _category_, _required_, _tcpPorts_, _udpPorts_, 및 _notes_를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-271">Includes  _ExpressRoute_, _serviceArea_, _category_, _required_, _tcpPorts_, _udpPorts_, and _notes_.</span></span>
- <span data-ttu-id="5fd7b-272">current - 끝점 집합의 변경 요소에 대한 업데이트된 값을 설명하는 하부 구조입니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-272">current — A substructure detailing updated values of changes elements on the endpoint set.</span></span> <span data-ttu-id="5fd7b-273">_ExpressRoute_, _serviceArea_, _category_, _required_, _tcpPorts_, _udpPorts_, 및 _notes_를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-273">Includes _ExpressRoute_, _serviceArea_, _category_, _required_, _tcpPorts_, _udpPorts_, and _notes_.</span></span>
- <span data-ttu-id="5fd7b-274">add - 끝점 집합 컬렉션에 추가할 항목을 자세히 설명하는 하위 구조입니다. 추가할 항목이 없으면 생략합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-274">add — A substructure detailing items to be added to endpoint set collections.</span></span> <span data-ttu-id="5fd7b-275">추가할 항목이 없으면 생략합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-275">Omitted if there are no additions.</span></span>
  <span data-ttu-id="5fd7b-276">— effectiveDate - 서비스에서 추가가 적용될 날짜를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-276">— effectiveDate — Defines the data when the additions will be live in the service.</span></span>
  <span data-ttu-id="5fd7b-277">— ips - _ips_ 배열에 추가할 항목입니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-277">— ips — Items to be added to the _ips_ array.</span></span>
  <span data-ttu-id="5fd7b-278">— urls - _urls_ 배열에 추가할 항목입니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-278">— urls- Items to be added to the _urls_ array.</span></span>
- <span data-ttu-id="5fd7b-279">remove - 끝점 집합에서 제거할 항목을 자세히 설명하는 하위 구조입니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-279">remove — A substructure detailing items to be removed from the endpoint set.</span></span> <span data-ttu-id="5fd7b-280">제거할 항목이 없으면 생략합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-280">Omitted if there are no removals.</span></span>
  <span data-ttu-id="5fd7b-281">— ips- _ips_ 배열에서 제거할 항목입니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-281">— ips — Items to be removed from the _ips_ array.</span></span>
  <span data-ttu-id="5fd7b-282">— urls -_urls_l 배열에서 제거할 항목입니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-282">— urls- Items to be removed from the _urls_ array.</span></span>

### <a name="examples"></a><span data-ttu-id="5fd7b-283">예제:</span><span class="sxs-lookup"><span data-stu-id="5fd7b-283">Examples:</span></span>

<span data-ttu-id="5fd7b-284">예제 1 요청 URI: [https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="5fd7b-284">Example 1 request URI: [https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="5fd7b-p144">Office 365 Worldwide 서비스 인스턴스에 대한 모든 이전 변경 내용을 요청합니다. 예제 결과:</span><span class="sxs-lookup"><span data-stu-id="5fd7b-p144">This requests all previous changes to the Office 365 worldwide service instance. Example result:</span></span>

```json
[
 {
  "id": 424,
  "endpointSetId": 32,
  "disposition": "Change",
  "version": "2018062700",
  "remove":
   {
    "urls":
     [
      "*.api.skype.com", "skypegraph.skype.com"
     ]
   }
 },
 {
  "id": 426,
  "endpointSetId": 31,
  "disposition": "Change",
  "version": "2018062700",
  "add":
   {
    "effectiveDate": "20180609",
    "ips":
     [
      "51.140.203.190/32"
     ]
   },
  "remove":
   {
    "ips":
     [
```

<span data-ttu-id="5fd7b-287">예제 2 요청 URI: [https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="5fd7b-287">Example 2 request URI: [https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="5fd7b-p145">Office 365 Worldwide 인스턴스에 대한 지정된 버전 이후의 변경 내용을 요청합니다. 이 경우 지정된 버전은 최신 버전입니다. 예제 결과:</span><span class="sxs-lookup"><span data-stu-id="5fd7b-p145">This requests changes since the specified version to the Office 365 Worldwide instance. In this case, the version specified is the latest. Example result:</span></span>

```json
[
  {
    "id":3,
    "endpointSetId":33,
    "changeDescription":"Removing old IP prefixes",
    "disposition":"Change",
    "version":"2018031301",
    "remove":{
      "ips":["65.55.127.0/24","66.119.157.192/26","66.119.158.0/25",
      "111.221.76.128/25","111.221.77.0/26","207.46.5.0/24"]
    }
  },
  {
    "id":4,
    "endpointSetId":45,
    "changeDescription":"Removing old IP prefixes",
    "disposition":"Change",
    "version":"2018031301",
    "remove":{
      "ips":["13.78.93.8/32","40.113.87.220/32","40.114.149.220/32",
      "40.117.100.83/32","40.118.214.164/32","104.208.31.113/32"]
    }
  }
]
```

## <a name="example-powershell-script"></a><span data-ttu-id="5fd7b-291">예제 PowerShell 스크립트</span><span class="sxs-lookup"><span data-stu-id="5fd7b-291">Example PowerShell Script</span></span>

<span data-ttu-id="5fd7b-292">업데이트된 데이터에 대해 수행해야 하는 작업이 있는지 알아보기 위해 실행할 수 있는 PowerShell 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-292">You can run this PowerShell script to see if there are actions you need to take for updated data.</span></span> <span data-ttu-id="5fd7b-293">이 스크립트를 예약된 작업으로 실행하여 버전 업데이트를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-293">You can run this script as a scheduled task to check for a version update.</span></span> <span data-ttu-id="5fd7b-294">웹 서비스에 과도한 부하를 피하려면 한 시간에 한 번 이상 스크립트를 실행하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-294">To avoid excessive load on the web service, try not to run the script more than once an hour.</span></span>

<span data-ttu-id="5fd7b-295">이 스크립트는 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-295">The script does the following:</span></span>

- <span data-ttu-id="5fd7b-296">웹 서비스 REST API를 호출하여 현재 Office 365 Worldwide 인스턴스 끝점의 버전 번호를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-296">Checks the version number of the current Office 365 Worldwide instance endpoints by calling the web service REST API.</span></span>
- <span data-ttu-id="5fd7b-297">_$Env:TEMP\O365_endpoints_latestversion.txt_에서 현재 버전 파일을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-297">Checks for a current version file at _$Env:TEMP\O365_endpoints_latestversion.txt_.</span></span> <span data-ttu-id="5fd7b-298">전역 변수의 **$Env:TEMP**의 경로는 일반적으로 _C:\Users\\<username\>\AppData\Local\Temp_입니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-298">The path of the global variable **$Env:TEMP** is usually _C:\Users\\<username\>\AppData\Local\Temp_.</span></span>
- <span data-ttu-id="5fd7b-299">스크립트가 처음 실행된 경우, 스크립트는 현재 버전과 모든 현재 IP 주소 및 URL을 반환하고 끝점 버전을 _$Env:TEMP\O365_endpoints_latestversion.txt_ 파일에 쓰고 끝점 데이터 출력을 _$Env:TEMP\O365_endpoints_data.txt_ 파일에 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-299">If this is the first time the script has been run, the script returns the current version and all current IP addresses and URLs, writes the endpoints version to the file _$Env:TEMP\O365_endpoints_latestversion.txt_ and the endpoints data output to the file _$Env:TEMP\O365_endpoints_data.txt_.</span></span> <span data-ttu-id="5fd7b-300">다음 줄을 편집하여 출력 파일의 경로 및/또는 이름을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-300">You can modify the path and/or name of the output file by editing these lines:</span></span>

    ``` powershell
    $versionpath = $Env:TEMP + "\O365_endpoints_latestversion.txt"
    $datapath = $Env:TEMP + "\O365_endpoints_data.txt"
    ```

- <span data-ttu-id="5fd7b-301">이후에 스크립트를 실행할 때마다 최신 웹 서비스 버전이 _O365_endpoints_latestversion.txt_ 파일의 버전과 동일한 경우 스크립트는 변경하지 않고 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-301">On each subsequent execution of the script, if the latest web service version is identical to the version in the _O365_endpoints_latestversion.txt_ file, the script exits without making any changes.</span></span>
- <span data-ttu-id="5fd7b-302">최신 웹 서비스 버전이 _O365_endpoints_latestversion.txt_ 파일의 버전보다 최신인 경우 스크립트는 **허용** 및 **최적화** 범주 끝점에 대한 끝접 및 필터를 반환하고 _O365_endpoints_latestversion.txt_ 파일에서 버전을 업데이트하고 업데이트된 데이터를 _O365_endpoints_data.txt_ 파일에 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-302">When the latest web service version is newer than the version in the _O365_endpoints_latestversion.txt_ file, the script returns the endpoints and filters for the **Allow** and **Optimize** category endpoints, updates the version in the _O365_endpoints_latestversion.txt_ file, and writes the updated data to the _O365_endpoints_data.txt_ file.</span></span>

<span data-ttu-id="5fd7b-303">스크립트는 해당 스크립트가 실행되는 컴퓨터에 대해 고유한 _ClientRequestId_를 생성하고 여러 호출에서 이 ID를 재사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-303">The script generates a unique _ClientRequestId_ for the computer it is executed on, and reuses this ID across multiple calls.</span></span> <span data-ttu-id="5fd7b-304">이 ID는 _O365_endpoints_latestversion_ 파일에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-304">This ID is stored in the _O365_endpoints_latestversion.txt_ file.</span></span>

### <a name="to-run-the-powershell-script"></a><span data-ttu-id="5fd7b-305">PowerShell 스크립트 실행하려면</span><span class="sxs-lookup"><span data-stu-id="5fd7b-305">To run the PowerShell script</span></span>

1. <span data-ttu-id="5fd7b-306">스크립트를 복사하고 로컬 하드 드라이브 또는 스크립트 위치에 _Get-O365WebServiceUpdates.ps1_로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-306">Copy the script and save it to your local hard drive or script location as _Get-O365WebServiceUpdates.ps1_.</span></span>
1. <span data-ttu-id="5fd7b-307">다음 명령을 사용하여 PowerShell ISE 또는 VS 코드와 같은 기본 스크립트 편집기 또는 PowerShell 콘솔에서 스크립트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-307">Execute the script in your preferred script editor such as the PowerShell ISE or VS Code, or from a PowerShell console using the following command:</span></span>

    ``` powershell
   powershell.exe -file <path>\Get-O365WebServiceUpdates.ps1
    ```

    <span data-ttu-id="5fd7b-308">스크립트에 전달할 매개 변수가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-308">There are no parameters to pass to the script.</span></span>

```powershell
<# Get-O365WebServiceUpdates.ps1
From https://aka.ms/ipurlws
v1.1 8/6/2019

DESCRIPTION
This script calls the REST API of the Office 365 IP and URL Web Service (Worldwide instance)
and checks to see if there has been a new update since the version stored in an existing
$Env:TEMP\O365_endpoints_latestversion.txt file in your user directory's temp folder
(usually C:\Users\<username>\AppData\Local\Temp).
If the file doesn't exist, or the latest version is newer than the current version in the
file, the script returns IPs and/or URLs that have been changed, added or removed in the latest
update and writes the new version and data to the output file $Env:TEMP\O365_endpoints_data.txt.

USAGE
Run as a scheduled task every 60 minutes.

PARAMETERS
n/a

PREREQUISITES
PS script execution policy: Bypass
PowerShell 3.0 or later
Does not require elevation
#>

#Requires -Version 3.0

# web service root URL
$ws = "https://endpoints.office.com"
# path where output files will be stored
$versionpath = $Env:TEMP + "\O365_endpoints_latestversion.txt"
$datapath = $Env:TEMP + "\O365_endpoints_data.txt"

# fetch client ID and version if version file exists; otherwise create new file and client ID
if (Test-Path $versionpath) {
    $content = Get-Content $versionpath
    $clientRequestId = $content[0]
    $lastVersion = $content[1]
    Write-Output ("Version file exists! Current version: " + $lastVersion)
}
else {
    Write-Output ("First run! Creating version file at " + $versionpath + ".")
    $clientRequestId = [GUID]::NewGuid().Guid
    $lastVersion = "0000000000"
    @($clientRequestId, $lastVersion) | Out-File $versionpath
}

# call version method to check the latest version, and pull new data if version number is different
$version = Invoke-RestMethod -Uri ($ws + "/version/Worldwide?clientRequestId=" + $clientRequestId)
if ($version.latest -gt $lastVersion) {
    Write-Host "New version of Office 365 worldwide commercial service instance endpoints detected"
    # write the new version number to the version file
    @($clientRequestId, $version.latest) | Out-File $versionpath
    # invoke endpoints method to get the new data
    $endpointSets = Invoke-RestMethod -Uri ($ws + "/endpoints/Worldwide?clientRequestId=" + $clientRequestId)
    # filter results for Allow and Optimize endpoints, and transform these into custom objects with port and category
    # URL results
    $flatUrls = $endpointSets | ForEach-Object {
        $endpointSet = $_
        $urls = $(if ($endpointSet.urls.Count -gt 0) { $endpointSet.urls } else { @() })
        $urlCustomObjects = @()
        if ($endpointSet.category -in ("Allow", "Optimize")) {
            $urlCustomObjects = $urls | ForEach-Object {
                [PSCustomObject]@{
                    category = $endpointSet.category;
                    url      = $_;
                    tcpPorts = $endpointSet.tcpPorts;
                    udpPorts = $endpointSet.udpPorts;
                }
            }
        }
        $urlCustomObjects
    }
    # IPv4 results
    $flatIp4s = $endpointSets | ForEach-Object {
        $endpointSet = $_
        $ips = $(if ($endpointSet.ips.Count -gt 0) { $endpointSet.ips } else { @() })
        # IPv4 strings contain dots
        $ip4s = $ips | Where-Object { $_ -like '*.*' }
        $ip4CustomObjects = @()
        if ($endpointSet.category -in ("Allow", "Optimize")) {
            $ip4CustomObjects = $ip4s | ForEach-Object {
                [PSCustomObject]@{
                    category = $endpointSet.category;
                    ip = $_;
                    tcpPorts = $endpointSet.tcpPorts;
                    udpPorts = $endpointSet.udpPorts;
                }
            }
        }
        $ip4CustomObjects
    }
    # IPv6 results
    $flatIp6s = $endpointSets | ForEach-Object {
        $endpointSet = $_
        $ips = $(if ($endpointSet.ips.Count -gt 0) { $endpointSet.ips } else { @() })
        # IPv6 strings contain colons
        $ip6s = $ips | Where-Object { $_ -like '*:*' }
        $ip6CustomObjects = @()
        if ($endpointSet.category -in ("Optimize")) {
            $ip6CustomObjects = $ip6s | ForEach-Object {
                [PSCustomObject]@{
                    category = $endpointSet.category;
                    ip = $_;
                    tcpPorts = $endpointSet.tcpPorts;
                    udpPorts = $endpointSet.udpPorts;
                }
            }
        }
        $ip6CustomObjects
    }

    # write output to screen
    Write-Output ("Client Request ID: " + $clientRequestId)
    Write-Output ("Last Version: " + $lastVersion)
    Write-Output ("New Version: " + $version.latest)
    Write-Output ""
    Write-Output "IPv4 Firewall IP Address Ranges"
    ($flatIp4s.ip | Sort-Object -Unique) -join "," | Out-String
    Write-Output "IPv6 Firewall IP Address Ranges"
    ($flatIp6s.ip | Sort-Object -Unique) -join "," | Out-String
    Write-Output "URLs for Proxy Server"
    ($flatUrls.url | Sort-Object -Unique) -join "," | Out-String
    Write-Output ("IP and URL data written to " + $datapath)

    # write output to data file
    Write-Output "Office 365 IP and UL Web Service data" | Out-File $datapath
    Write-Output "Worldwide instance" | Out-File $datapath -Append
    Write-Output "" | Out-File $datapath -Append
    Write-Output ("Version: " + $version.latest) | Out-File $datapath -Append
    Write-Output "" | Out-File $datapath -Append
    Write-Output "IPv4 Firewall IP Address Ranges" | Out-File $datapath -Append
    ($flatIp4s.ip | Sort-Object -Unique) -join "," | Out-File $datapath -Append
    Write-Output "" | Out-File $datapath -Append
    Write-Output "IPv6 Firewall IP Address Ranges" | Out-File $datapath -Append
    ($flatIp6s.ip | Sort-Object -Unique) -join "," | Out-File $datapath -Append
    Write-Output "" | Out-File $datapath -Append
    Write-Output "URLs for Proxy Server" | Out-File $datapath -Append
    ($flatUrls.url | Sort-Object -Unique) -join "," | Out-File $datapath -Append
}
else {
    Write-Host "Office 365 worldwide commercial service instance endpoints are up-to-date."
}
```

## <a name="example-python-script"></a><span data-ttu-id="5fd7b-309">예제 Python 스크립트</span><span class="sxs-lookup"><span data-stu-id="5fd7b-309">Example Python Script</span></span>

<span data-ttu-id="5fd7b-p150">다음은 업데이트된 데이터에 대해 수행해야 하는 작업이 있는지 확인하기 위해 실행할 수 있는 Windows 10의 Python 3.6.3으로 테스트된 Python 스크립트입니다. 이 스크립트는 Office 365 Worldwide 인스턴스 끝점에 대한 버전 번호를 확인합니다. 변경 내용이 있는 경우 끝점을 다운로드하고 _Allow_ 및 _Optimize_ 범주 끝점을 필터링합니다. 또한 여러 호출에서 고유한 ClientRequestId를 사용하고 찾은 최신 버전을 임시 파일에 저장합니다. 이 스크립트를 1시간에 1회 호출하여 버전 업데이트를 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-p150">Here is a Python script, tested with Python 3.6.3 on Windows 10, that you can run to see if there are actions you need to take for updated data. This script checks the version number for the Office 365 Worldwide instance endpoints. When there is a change, it downloads the endpoints and filters for the _Allow_ and _Optimize_ category endpoints. It also uses a unique ClientRequestId across multiple calls and saves the latest version found in a temporary file. You should call this script once an hour to check for a version update.</span></span>

```python
import json
import tempfile
from pathlib import Path
import urllib.request
import uuid
# helper to call the webservice and parse the response
def webApiGet(methodName, instanceName, clientRequestId):
    ws = "https://endpoints.office.com"
    requestPath = ws + '/' + methodName + '/' + instanceName + '?clientRequestId=' + clientRequestId
    request = urllib.request.Request(requestPath)
    with urllib.request.urlopen(request) as response:
        return json.loads(response.read().decode())
# path where client ID and latest version number will be stored
datapath = Path(tempfile.gettempdir() + '/endpoints_clientid_latestversion.txt')
# fetch client ID and version if data exists; otherwise create new file
if datapath.exists():
    with open(datapath, 'r') as fin:
        clientRequestId = fin.readline().strip()
        latestVersion = fin.readline().strip()
else:
    clientRequestId = str(uuid.uuid4())
    latestVersion = '0000000000'
    with open(datapath, 'w') as fout:
        fout.write(clientRequestId + '\n' + latestVersion)
# call version method to check the latest version, and pull new data if version number is different
version = webApiGet('version', 'Worldwide', clientRequestId)
if version['latest'] > latestVersion:
    print('New version of Office 365 worldwide commercial service instance endpoints detected')
    # write the new version number to the data file
    with open(datapath, 'w') as fout:
        fout.write(clientRequestId + '\n' + version['latest'])
    # invoke endpoints method to get the new data
    endpointSets = webApiGet('endpoints', 'Worldwide', clientRequestId)
    # filter results for Allow and Optimize endpoints, and transform these into tuples with port and category
    flatUrls = []
    for endpointSet in endpointSets:
        if endpointSet['category'] in ('Optimize', 'Allow'):
            category = endpointSet['category']
            urls = endpointSet['urls'] if 'urls' in endpointSet else []
            tcpPorts = endpointSet['tcpPorts'] if 'tcpPorts' in endpointSet else ''
            udpPorts = endpointSet['udpPorts'] if 'udpPorts' in endpointSet else ''
            flatUrls.extend([(category, url, tcpPorts, udpPorts) for url in urls])
    flatIps = []
    for endpointSet in endpointSets:
        if endpointSet['category'] in ('Optimize', 'Allow'):
            ips = endpointSet['ips'] if 'ips' in endpointSet else []
            category = endpointSet['category']
            # IPv4 strings have dots while IPv6 strings have colons
            ip4s = [ip for ip in ips if '.' in ip]
            tcpPorts = endpointSet['tcpPorts'] if 'tcpPorts' in endpointSet else ''
            udpPorts = endpointSet['udpPorts'] if 'udpPorts' in endpointSet else ''
            flatIps.extend([(category, ip, tcpPorts, udpPorts) for ip in ip4s])
    print('IPv4 Firewall IP Address Ranges')
    print(','.join(sorted(set([ip for (category, ip, tcpPorts, udpPorts) in flatIps]))))
    print('URLs for Proxy Server')
    print(','.join(sorted(set([url for (category, url, tcpPorts, udpPorts) in flatUrls]))))

    # TODO send mail (e.g. with smtplib/email modules) with new endpoints data
else:
    print('Office 365 worldwide commercial service instance endpoints are up-to-date')
```

## <a name="web-service-interface-versioning"></a><span data-ttu-id="5fd7b-315">웹 서비스 인터페이스 버전 관리</span><span class="sxs-lookup"><span data-stu-id="5fd7b-315">Web Service interface versioning</span></span>

<span data-ttu-id="5fd7b-316">이러한 웹 서비스 메서드의 매개 변수나 결과의 업데이트는 나중에 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-316">Updates to the parameters or results for these web service methods may be required in the future.</span></span> <span data-ttu-id="5fd7b-317">이러한 웹 서비스의 일반 가용성 버전이 게시된 후 Microsoft는 웹 서비스에 대한 중요한 업데이트의 사전 통지를 제공하기 위해 합리적인 노력을 기울일 것입니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-317">After the general availability version of these web services is published, Microsoft will make reasonable efforts to provide advance notice of material updates to the web service.</span></span> <span data-ttu-id="5fd7b-318">Microsoft가 업데이트에 웹 서비스를 사용하는 클라이언트를 변경해야 할 것으로 판단하면 Microsoft는 새 버전이 릴리스된 후 12개월 이상 웹 서비스의 이전 버전(한 버전 이전)을 계속 사용할 수 있도록 할 것입니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-318">When Microsoft believes that an update will require changes to clients using the web service, Microsoft will keep the previous version (one version back) of the web service available for at least 12 months after the release of the new version.</span></span> <span data-ttu-id="5fd7b-319">해당 기간 동안 업그레이드하지 않은 고객은 웹 서비스 및 해당 메서드에 액세스하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-319">Customers who do not upgrade during that time may be unable to access the web service and its methods.</span></span> <span data-ttu-id="5fd7b-320">웹 서비스 인터페이스 서명이 다음과 같이 변경되면 고객은 웹 서비스의 클라이언트가 오류 없이 계속 작동하는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-320">Customers must ensure that clients of the web service continue working without error if the following changes are made to the web service interface signature:</span></span>

- <span data-ttu-id="5fd7b-321">이전 클라이언트가 제공할 필요가 없으며 이전 클라이언트가 수신하는 결과에 영향을 미치지 않는 새로운 선택적 매개 변수를 기존 웹 메서드에 추가</span><span class="sxs-lookup"><span data-stu-id="5fd7b-321">Adding a new optional parameter to an existing web method that doesn't have to be provided by older clients and doesn't impact the result an older client receives.</span></span>
- <span data-ttu-id="5fd7b-322">응답 REST 항목 또는 추가 열 중 하나에 있는 새로운 명명된 특성을 응답 CSV 에 추가</span><span class="sxs-lookup"><span data-stu-id="5fd7b-322">Adding a new named attribute in one of the response REST items or additional columns to the response CSV.</span></span>
- <span data-ttu-id="5fd7b-323">이전 클라이언트에서 호출하지 않는 새 이름의 새 웹 메서드 추가</span><span class="sxs-lookup"><span data-stu-id="5fd7b-323">Adding a new web method with a new name that is not called by the older clients.</span></span>

## <a name="update-notifications"></a><span data-ttu-id="5fd7b-324">업데이트 알림</span><span class="sxs-lookup"><span data-stu-id="5fd7b-324">Update notifications</span></span>

<span data-ttu-id="5fd7b-325">IP 주소 및 URL 변경 사항이 웹 서비스에 게시될 때 몇 가지 방법을 사용하여 전자 메일 알림을 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-325">You can use a few different methods to get email notifications when changes to the IP addresses and URLs are published to the web service.</span></span>

- <span data-ttu-id="5fd7b-326">Microsoft Flow 솔루션을 사용하려면 [Microsoft Flow 사용하여 Office 365 IP 주소 및 URL 변경 내용에 대한 전자 메일 받기](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/m-p/240651)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-326">To use a Microsoft Flow solution, see [Use Microsoft Flow to receive an email for changes to Office 365 IP Addresses and URLs](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/m-p/240651).</span></span>
- <span data-ttu-id="5fd7b-327">ARM 서식 파일을 사용하여 Azure Logic 앱을 배포하려면 [Office 365 업데이트 알림(v1.1)](https://aka.ms/ipurlws-updates-template)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-327">To deploy an Azure Logic App using an ARM template, see [Office 365 Update Notification (v1.1)](https://aka.ms/ipurlws-updates-template).</span></span>
- <span data-ttu-id="5fd7b-328">PowerShell을 사용하여 알림 스크립트를 직접 작성하려면 [Send-MailMessage](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/send-mailmessage)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-328">To write your own notification script using PowerShell, see [Send-MailMessage](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/send-mailmessage).</span></span>

## <a name="exporting-a-proxy-pac-file"></a><span data-ttu-id="5fd7b-329">프록시 PAC 파일 내보내기</span><span class="sxs-lookup"><span data-stu-id="5fd7b-329">Exporting a Proxy PAC file</span></span>

<span data-ttu-id="5fd7b-330">[¡Get-PacFile](https://www.powershellgallery.com/packages/Get-PacFile)은 Office 365 IP 주소 및 URL 웹 서비스에서 최신 네트워크 끝점을 읽고 샘플 PAC 파일을 만드는 PowerShell 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-330">[Get-PacFile](https://www.powershellgallery.com/packages/Get-PacFile) is a PowerShell script that reads the latest network endpoints from the Office 365 IP Address and URL web service and creates a sample PAC file.</span></span> <span data-ttu-id="5fd7b-331">Get-PacFile 사용에 대한 자세한 내용은 [중요 Office 365 트래픽을 직접 라우팅하는 데 PAC 파일 사용](managing-office-365-endpoints.md#use-a-pac-file-for-direct-routing-of-vital-office-365-traffic)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5fd7b-331">For information on using Get-PacFile, see [Use a PAC file for direct routing of vital Office 365 traffic](managing-office-365-endpoints.md#use-a-pac-file-for-direct-routing-of-vital-office-365-traffic).</span></span>

## <a name="related-topics"></a><span data-ttu-id="5fd7b-332">관련 주제</span><span class="sxs-lookup"><span data-stu-id="5fd7b-332">Related Topics</span></span>
  
[<span data-ttu-id="5fd7b-333">Office 365 URL 및 IP 주소 범위</span><span class="sxs-lookup"><span data-stu-id="5fd7b-333">Office 365 URLs and IP address ranges</span></span>](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)

[<span data-ttu-id="5fd7b-334">Office 365 끝점 관리</span><span class="sxs-lookup"><span data-stu-id="5fd7b-334">Managing Office 365 endpoints</span></span>](managing-office-365-endpoints.md)
  
[<span data-ttu-id="5fd7b-335">Office 365 끝점 FAQ</span><span class="sxs-lookup"><span data-stu-id="5fd7b-335">Office 365 endpoints FAQ</span></span>](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

[<span data-ttu-id="5fd7b-336">Office 365 네트워크 연결 원칙</span><span class="sxs-lookup"><span data-stu-id="5fd7b-336">Office 365 Network Connectivity Principles</span></span>](office-365-network-connectivity-principles.md)

[<span data-ttu-id="5fd7b-337">Office 365 네트워크 및 성능 조정</span><span class="sxs-lookup"><span data-stu-id="5fd7b-337">Office 365 network and performance tuning</span></span>](network-planning-and-performance.md)

<span data-ttu-id="5fd7b-338">[Office 365 네트워크 연결 평가](assessing-network-connectivity.md) </span><span class="sxs-lookup"><span data-stu-id="5fd7b-338">[Assessing Office 365 network connectivity](assessing-network-connectivity.md)</span></span>
  
[<span data-ttu-id="5fd7b-339">비즈니스용 Skype Online의 미디어 품질 및 네트워크 연결 성능</span><span class="sxs-lookup"><span data-stu-id="5fd7b-339">Media Quality and Network Connectivity Performance in Skype for Business Online</span></span>](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[<span data-ttu-id="5fd7b-340">비즈니스용 Skype Online의 네트워크 최적화</span><span class="sxs-lookup"><span data-stu-id="5fd7b-340">Optimizing your network for Skype for Business Online</span></span>](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)

[<span data-ttu-id="5fd7b-341">초기 계획 및 성능 기록을 사용하여 Office 365 성능 조정</span><span class="sxs-lookup"><span data-stu-id="5fd7b-341">Office 365 performance tuning using baselines and performance history</span></span>](performance-tuning-using-baselines-and-history.md)
  
[<span data-ttu-id="5fd7b-342">Office 365 성능 문제 해결 계획</span><span class="sxs-lookup"><span data-stu-id="5fd7b-342">Performance troubleshooting plan for Office 365</span></span>](performance-troubleshooting-plan.md)
