---
title: Office 365용 Azure Express 경로
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/01/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 6d2534a2-c19c-4a99-be5e-33a0cee5d3bd
description: azure express를 office 365에서 사용 하는 방법과 office 365에 사용할 azure express 경로를 배포 하는 경우에 필요한 네트워크 구현 프로젝트를 계획 하는 방법에 대해 알아봅니다.
ms.openlocfilehash: c8cff4ef85c4383ba04829cf3cf8da3a1bc36715
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/30/2019
ms.locfileid: "33490360"
---
# <a name="azure-expressroute-for-office-365"></a><span data-ttu-id="f2271-103">Office 365용 Azure Express 경로</span><span class="sxs-lookup"><span data-stu-id="f2271-103">Azure ExpressRoute for Office 365</span></span>

<span data-ttu-id="f2271-104">azure express를 office 365에서 사용 하는 방법과 office 365에 사용할 azure express 경로를 배포 하는 경우에 필요한 네트워크 구현 프로젝트를 계획 하는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="f2271-104">Learn how Azure ExpressRoute is used with Office 365 and how to plan the network implementation project that will be required if you are deploying Azure ExpressRoute for use with Office 365.</span></span> <span data-ttu-id="f2271-105">Azure에서 실행 되는 인프라 및 플랫폼 서비스는 네트워크 아키텍처 및 성능 고려 사항에 영향을 주는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="f2271-105">Infrastructure and platform services running in Azure will often benefit by addressing network architecture and performance considerations.</span></span> <span data-ttu-id="f2271-106">이러한 경우 Azure에 대 한 모든 방법을 사용할 것을 권장 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2271-106">We recommend ExpressRoute for Azure in these cases.</span></span> <span data-ttu-id="f2271-107">Office 365 및 Dynamics 365과 같은 서비스 제품을 제공 하는 소프트웨어는 인터넷을 통해 안전 하 고 안정적으로 액세스할 수 있도록 작성 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f2271-107">Software as a Service offerings like Office 365 and Dynamics 365 have been built to be accessed securely and reliably via the Internet.</span></span> <span data-ttu-id="f2271-108">인터넷 성능 및 보안에 대해 자세히 설명 하 고 office [365에 대 한 네트워크 연결](network-connectivity.md)문서에서 office 365에 대 한 Azure express를 고려할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2271-108">You can read about Internet performance and security and when you might consider Azure ExpressRoute for Office 365 in the article [Network connectivity to Office 365](network-connectivity.md).</span></span>

> [!NOTE]
> <span data-ttu-id="f2271-109">Microsoft authorization는 Office 365 용 express 경로를 사용 하는 데 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2271-109">Microsoft authorization is required to use ExpressRoute for Office 365.</span></span> <span data-ttu-id="f2271-110">고객의 규정 요구 사항에 직접 연결 하는 경우 모든 고객을 검토 하 고 Office 365 사용에 대 한 사용자를 요청 하 고 권한을 부여 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2271-110">Microsoft reviews every customer request and authorizes ExpressRoute for Office 365 usage when a customer's regulatory requirement mandates direct connectivity.</span></span> <span data-ttu-id="f2271-111">이러한 요구 사항을 충족 하는 경우 해석 하는 규정에 대 한 텍스트 발췌문 및 웹 링크를 제공 하 여 Microsoft 검토를 시작 하기 [위한 Office 365의 express 경로 요청 양식에](https://aka.ms/O365ERReview) 직접 연결이 필요 하다는 것을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2271-111">If you have such requirements, please provide the text excerpt and web link to the regulation which you interpret to mean that direct connectivity is required in the [ExpressRoute for Office 365 Request Form](https://aka.ms/O365ERReview) to begin a Microsoft review.</span></span> <span data-ttu-id="f2271-112">인증 되지 않은 구독에서 Office 365에 대 한 경로 필터를 만들려고 하면 [오류 메시지가](https://support.microsoft.com/kb/3181709)표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2271-112">Unauthorized subscriptions trying to create route filters for Office 365 will receive an [error message](https://support.microsoft.com/kb/3181709).</span></span> 

<span data-ttu-id="f2271-113">이제 선택한 office 365 네트워크 트래픽에 대해 office 365에 직접 네트워크 연결을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2271-113">You can now add a direct network connection to Office 365 for selected Office 365 network traffic.</span></span> <span data-ttu-id="f2271-114">Azure express에서는 Microsoft 네트워킹 구성 요소에 대 한 직접 연결과 예측 가능한 성능을 제공 하 고 가동 시간 SLA를 99.95%와 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2271-114">Azure ExpressRoute offers a direct connection, predictable performance, and comes with an uptime SLA of 99.95% for the Microsoft networking components.</span></span> <span data-ttu-id="f2271-115">Azure express 경로를 통해 지원 되지 않는 서비스의 경우에도 인터넷 연결이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2271-115">You'll still require an internet connection for services that aren't supported over Azure ExpressRoute.</span></span>

## <a name="planning-azure-expressroute-for-office-365"></a><span data-ttu-id="f2271-116">Office 365에 대 한 Azure express 경로 계획</span><span class="sxs-lookup"><span data-stu-id="f2271-116">Planning Azure ExpressRoute for Office 365</span></span>

<span data-ttu-id="f2271-117">인터넷에 연결 하는 것 외에도 예측 가능성 및 Microsoft 네트워킹 구성 요소에 대 한 99.95%의 가동 시간 SLA를 제공 하는 직접 연결을 통해 Office 365 네트워크 트래픽의 하위 집합을 라우팅하도록 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2271-117">In addition to internet connectivity, you may choose to route a subset of their Office 365 network traffic over a direct connection that offers predictability and a 99.95% uptime SLA for the Microsoft networking components.</span></span> <span data-ttu-id="f2271-118">Azure express 서버는 Office 365 및 기타 Microsoft 클라우드 서비스에 대 한 이러한 전용 네트워크 연결을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2271-118">Azure ExpressRoute provides you with this dedicated network connection to Office 365 and other Microsoft cloud services.</span></span>

<span data-ttu-id="f2271-119">기존 MPLS WAN이 있는지 여부에 관계 없이, 세 가지 방법 중 하나를 통해이를 네트워크 아키텍처에 추가할 수 있습니다. 지원 되는 클라우드 exchange 공동 위치 공급자, 이더넷 지점간 연결 공급자 또는 MPLS 연결 공급자를 통해 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2271-119">Regardless of whether you have an existing MPLS WAN, ExpressRoute can be added to your network architecture in one of three ways; through a supported cloud exchange co-location provider, an Ethernet point-to-point connection provider, or through an MPLS connection provider.</span></span> <span data-ttu-id="f2271-120">[해당 지역에서 사용할 수 있는 공급자를](https://azure.microsoft.com/documentation/articles/expressroute-locations/)참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f2271-120">See what [providers are available in your region](https://azure.microsoft.com/documentation/articles/expressroute-locations/).</span></span> <span data-ttu-id="f2271-121">직접 express 연결을 사용 하면 아래에 나와 있는 [Office 365 서비스가 포함 된](azure-expressroute.md#BKMK_WhatDoIGet) 응용 프로그램에 대 한 연결을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2271-121">The direct ExpressRoute connection will enable connectivity to the applications outlined in [What Office 365 services are included?](azure-expressroute.md#BKMK_WhatDoIGet) below.</span></span> <span data-ttu-id="f2271-122">다른 모든 응용 프로그램 및 서비스에 대 한 네트워크 트래픽은 인터넷을 계속 통과 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2271-122">Network traffic for all other applications and services will continue to traverse the internet.</span></span>

<span data-ttu-id="f2271-123">office 365, Windows Update, TechNet 등의 모든 Microsoft 응용 프로그램에 액세스할 수 있도록 인터넷을 통해 microsoft의 데이터 센터에 연결 하는 일반적인 Office 365 고객을 보여 주는 다음과 같은 높은 수준의 네트워크 다이어그램을 고려해 야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2271-123">Consider the following high level network diagram which shows a typical Office 365 customer connecting to Microsoft's datacenters over the internet for access to all Microsoft applications such as Office 365, Windows Update, and TechNet.</span></span> <span data-ttu-id="f2271-124">고객은 온-프레미스 네트워크에서 연결 하는지 아니면 독립적으로 인터넷 연결을 사용 하 든 관계 없이 비슷한 네트워크 경로를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2271-124">Customers use a similar network path regardless of whether they're connecting from an on-premises network or from an independent internet connection.</span></span>

![Office 365 네트워크 연결](media/9d8bc622-4a38-4a3b-a0f3-68657712d460.png)

<span data-ttu-id="f2271-126">이제 인터넷 및 express 사용자를 모두 사용 하 여 office 365에 연결 하는 office 365 고객을 나타내는 업데이트 된 다이어그램을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2271-126">Now look at the updated diagram which depicts an Office 365 customer who uses both the internet and ExpressRoute to connect to Office 365.</span></span> <span data-ttu-id="f2271-127">공용 DNS 및 콘텐츠 배달 네트워크 노드와 같은 일부 연결에서는 여전히 공용 인터넷 연결이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2271-127">Notice that some connections such as Public DNS and Content Delivery Network nodes still require the public internet connection.</span></span> <span data-ttu-id="f2271-128">또한 사용자가 연결 된 거 짓는 건물에 없는 고객은 인터넷을 통해 연결 하는 것을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2271-128">Also notice the customer's users who are not located in their ExpressRoute connected building are connecting over the Internet.</span></span>

![간 Office 365 연결 (express)](media/251788c4-0937-4584-9b2c-df08e11611fc.png)

<span data-ttu-id="f2271-130">계속 해 서 정보를 원하십니까?</span><span class="sxs-lookup"><span data-stu-id="f2271-130">Still want more information?</span></span> <span data-ttu-id="f2271-131">[office 365의 azure express 경로를 사용 하 여 네트워크 트래픽을 관리](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408) 하는 방법에 대해 알아보고 [office 365에 대 한 azure express](https://azure.microsoft.com/documentation/articles/expressroute-faqs/)경로를 구성 하는 방법을 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="f2271-131">Learn how to [manage your network traffic with Azure ExpressRoute for Office 365](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408) and learn how to [configure Azure ExpressRoute for Office 365](https://azure.microsoft.com/documentation/articles/expressroute-faqs/).</span></span> <span data-ttu-id="f2271-132">또한 채널 9에 [대 한 Office 365 교육](https://channel9.msdn.com/series/aer) 시리즈를 위한 10 부 Azure express를 기록 하 여 개념을 보다 철저히 설명할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2271-132">We've also recorded a 10 part [Azure ExpressRoute for Office 365 Training](https://channel9.msdn.com/series/aer) series on Channel 9 to help explain the concepts more thoroughly.</span></span>

<span data-ttu-id="f2271-133">([Office 365 용 Azure express](azure-expressroute.md#BKMK_HOME)경로)</span><span class="sxs-lookup"><span data-stu-id="f2271-133">([Azure ExpressRoute for Office 365](azure-expressroute.md#BKMK_HOME))</span></span>

## <a name="what-office-365-services-are-included"></a><span data-ttu-id="f2271-134">어떤 Office 365 서비스가 포함 됩니까?</span><span class="sxs-lookup"><span data-stu-id="f2271-134">What Office 365 services are included?</span></span>
<span data-ttu-id="f2271-135"><a name="BKMK_WhatDoIGet"> </a></span><span class="sxs-lookup"><span data-stu-id="f2271-135"></span></span>

<span data-ttu-id="f2271-136">다음 표에는 express를 통해 지원 되는 Office 365 서비스가 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2271-136">The following table lists the Office 365 services that are supported over ExpressRoute.</span></span> <span data-ttu-id="f2271-137">이러한 응용 프로그램에 대 한 네트워크 요청에 인터넷 연결이 필요한 지 알아보려면 [Office 365 endpoints 문서](https://aka.ms/o365endpoints) 를 검토 하세요.</span><span class="sxs-lookup"><span data-stu-id="f2271-137">Please review the [Office 365 endpoints article](https://aka.ms/o365endpoints) to understand which network requests for these applications require internet connectivity.</span></span>

|<span data-ttu-id="f2271-138">**포함 된 응용 프로그램**</span><span class="sxs-lookup"><span data-stu-id="f2271-138">**Applications included**</span></span>|
|:-----|
|<span data-ttu-id="f2271-139">Exchange Online<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="f2271-139">Exchange Online<sup>1</sup></span></span> <br/> <span data-ttu-id="f2271-140">Exchange Online Protection<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="f2271-140">Exchange Online Protection<sup>1</sup></span></span> <br/> <span data-ttu-id="f2271-141">Delve<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="f2271-141">Delve<sup>1</sup></span></span> <br/> |
|<span data-ttu-id="f2271-142">비즈니스용 Skype Online<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="f2271-142">Skype for Business Online<sup>1</sup></span></span> <br/> |
|<span data-ttu-id="f2271-143">SharePoint Online<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="f2271-143">SharePoint Online<sup>1</sup></span></span> <br/> <span data-ttu-id="f2271-144">비즈니스용 OneDrive<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="f2271-144">OneDrive for Business<sup>1</sup></span></span> <br/> <span data-ttu-id="f2271-145">Project Online<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="f2271-145">Project Online<sup>1</sup></span></span> <br/> |
|<span data-ttu-id="f2271-146">포털 및 공유<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="f2271-146">Portal and shared<sup>1</sup></span></span> <br/> <span data-ttu-id="f2271-147">Azure Active Directory<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="f2271-147">Azure Active Directory<sup>1</sup></span></span> <br/> <span data-ttu-id="f2271-148">AAD Connect<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="f2271-148">AAD Connect<sup>1</sup></span></span> <br/> <span data-ttu-id="f2271-149">Office Online<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="f2271-149">Office Online<sup>1</sup></span></span> <br/> |

<span data-ttu-id="f2271-150"><sup>1</sup> 이러한 각 응용 프로그램은 express에서 지원 되지 않는 인터넷 연결 요구 사항이 있습니다. 자세한 내용은 [Office 365 endpoints 문서](https://aka.ms/o365endpoints) 를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="f2271-150"><sup>1</sup>Each of these applications have internet connectivity requirements not supported over ExpressRoute, see the [Office 365 endpoints article](https://aka.ms/o365endpoints) for more information.</span></span>

<span data-ttu-id="f2271-151">office 365에 대 한 express에 포함 되지 않은 서비스는 중국의 office 365 ProPlus 클라이언트 다운로드, 온-프레미스 id 공급자 로그인 및 office 365 (21 vianet 되며) 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="f2271-151">The services that aren't included with ExpressRoute for Office 365 are Office 365 ProPlus client downloads, On-premises Identity Provider Sign-In, and Office 365 (operated by 21 Vianet) service in China.</span></span>

<span data-ttu-id="f2271-152">([Office 365 용 Azure express](azure-expressroute.md#BKMK_HOME)경로)</span><span class="sxs-lookup"><span data-stu-id="f2271-152">([Azure ExpressRoute for Office 365](azure-expressroute.md#BKMK_HOME))</span></span>

## <a name="implementing-expressroute-for-office-365"></a><span data-ttu-id="f2271-153">Office 365용 ExpressRoute 구현</span><span class="sxs-lookup"><span data-stu-id="f2271-153">Implementing ExpressRoute for Office 365</span></span>

<span data-ttu-id="f2271-154">이 방법을 구현 하려면 네트워크 및 응용 프로그램 소유자의 참여가 필요 하며, 새 [네트워크 라우팅 아키텍처](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408), 대역폭 요구 사항, 보안을 구현할 위치, 고가용성 등을 결정 하기 위한 신중한 계획이 필요 합니다. 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2271-154">Implementing ExpressRoute requires the involvement of network and application owners and requires careful planning to determine the new [network routing architecture](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408), bandwidth requirements, where security will be implemented, high availability, and so on.</span></span> <span data-ttu-id="f2271-155">express를 구현 하려면 다음을 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2271-155">To implement ExpressRoute, you'll need to:</span></span>

1. <span data-ttu-id="f2271-156">Office 365 연결 계획에서 요구 하는 express가 충족 하는지 완전히 이해 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2271-156">Fully understand the need ExpressRoute satisfies in your Office 365 connectivity planning.</span></span> <span data-ttu-id="f2271-157">인터넷 또는 express를 사용 하는 응용 프로그램을 이해 하 고, Office 365 트래픽에 대 한 인터넷 및 용 수를 모두 사용 하는 컨텍스트에서 네트워크 용량, 보안 및 고가용성 요구 사항을 완전히 계획 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2271-157">Understand what applications will use the internet or ExpressRoute and fully plan your network capacity, security, and high availability needs in the context of using both the internet and ExpressRoute for Office 365 traffic.</span></span>

2. <span data-ttu-id="f2271-158">인터넷 및 express 통신<sup>1</sup>의 egress 및 피어 링 위치를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2271-158">Determine the egress and peering locations for both internet and ExpressRoute traffic<sup>1</sup>.</span></span>

3. <span data-ttu-id="f2271-159">인터넷 및가을 연결 하는 데 필요한 용량을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2271-159">Determine the capacity required on the internet and ExpressRoute connections.</span></span>

4. <span data-ttu-id="f2271-160">보안 및 기타 표준 주변 컨트롤<sup>1</sup>을 구현 하기 위한 계획을 마련 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2271-160">Have a plan in place for implementing security and other standard perimeter controls<sup>1</sup>.</span></span>

5. <span data-ttu-id="f2271-161">express를 구독 하려면 유효한 Microsoft Azure 계정이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2271-161">Have a valid Microsoft Azure account to subscribe to ExpressRoute.</span></span>

6. <span data-ttu-id="f2271-162">연결 모델 및 [승인 된 공급자](https://azure.microsoft.com/documentation/articles/expressroute-locations/)를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2271-162">Select a connectivity model and an [approved provider](https://azure.microsoft.com/documentation/articles/expressroute-locations/).</span></span> <span data-ttu-id="f2271-163">고객은 여러 연결 모델 또는 파트너를 선택할 수 있으며, 파트너가 기존 네트워크 공급자와 같을 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f2271-163">Keep in mind, customers can select multiple connectivity models or partners and the partner doesn't need to be the same as your existing network provider.</span></span>

7. <span data-ttu-id="f2271-164">트래픽을 express로 전송 하기 전에 배포 유효성을 검사 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2271-164">Validate deployment prior to directing traffic to ExpressRoute.</span></span>

8. <span data-ttu-id="f2271-165">선택적으로 [QoS를 구현](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d) 하 고 지역별 확장을 평가 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2271-165">Optionally [implement QoS](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d) and evaluate regional expansion.</span></span>

<span data-ttu-id="f2271-166"><sup>1</sup> 중요 한 성능 고려 사항</span><span class="sxs-lookup"><span data-stu-id="f2271-166"><sup>1</sup>Important performance considerations.</span></span> <span data-ttu-id="f2271-167">여기에서 결정 사항은 비즈니스용 Skype와 같은 응용 프로그램에 중요 한 대기 시간에 영향을 미칠 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2271-167">Decisions here can dramatically impact latency which is a critical for applications such as Skype for Business.</span></span>

<span data-ttu-id="f2271-168">추가 참조에 대해서는 [라우팅 가이드](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408) 와, [express 경로 설명서](https://azure.microsoft.com/documentation/articles/expressroute-introduction/)를 사용 하십시오.</span><span class="sxs-lookup"><span data-stu-id="f2271-168">For additional references, use our [routing guide](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408) in addition to the [ExpressRoute documentation](https://azure.microsoft.com/documentation/articles/expressroute-introduction/).</span></span>

<span data-ttu-id="f2271-169">Office 365에 대 한 express를 구입 하려면 하나 이상의 [승인 된 공급자](https://azure.microsoft.com/documentation/articles/expressroute-locations/) 와 협력 하 여 express Premium 구독에 원하는 수 및 크기의 회로를 프로 비전 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2271-169">To purchase ExpressRoute for Office 365, you'll need to work with one or more [approved providers](https://azure.microsoft.com/documentation/articles/expressroute-locations/) to provision the desired number and size circuits with an ExpressRoute Premium subscription.</span></span> <span data-ttu-id="f2271-170">Office 365에서 구입할 추가 라이선스가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f2271-170">There are no additional licenses to purchase from Office 365.</span></span>

<span data-ttu-id="f2271-171">다음의 간단한 링크를 사용할 수 있습니다. [https://aka.ms/expressrouteoffice365](https://aka.ms/expressrouteoffice365)</span><span class="sxs-lookup"><span data-stu-id="f2271-171">Here's a short link you can use to come back: [https://aka.ms/expressrouteoffice365](https://aka.ms/expressrouteoffice365)</span></span>

<span data-ttu-id="f2271-172">[Office 365에 대 한 express](https://aka.ms/ert)를 등록할 준비가 되셨습니까?</span><span class="sxs-lookup"><span data-stu-id="f2271-172">Ready to sign-up for [ExpressRoute for Office 365](https://aka.ms/ert)?</span></span>

<span data-ttu-id="f2271-173">([Office 365 용 Azure express](azure-expressroute.md#BKMK_HOME)경로)</span><span class="sxs-lookup"><span data-stu-id="f2271-173">([Azure ExpressRoute for Office 365](azure-expressroute.md#BKMK_HOME))</span></span>

## <a name="related-topics"></a><span data-ttu-id="f2271-174">관련 항목</span><span class="sxs-lookup"><span data-stu-id="f2271-174">Related Topics</span></span>

[<span data-ttu-id="f2271-175">Office 365에 대한 네트워크 연결</span><span class="sxs-lookup"><span data-stu-id="f2271-175">Network connectivity to Office 365</span></span>](network-connectivity.md)

[<span data-ttu-id="f2271-176">Office 365 연결에 대한 ExpressRoute 관리</span><span class="sxs-lookup"><span data-stu-id="f2271-176">Managing ExpressRoute for Office 365 connectivity</span></span>](managing-expressroute-for-connectivity.md)

[<span data-ttu-id="f2271-177">Office 365용 ExpressRoute를 사용한 라우팅</span><span class="sxs-lookup"><span data-stu-id="f2271-177">Routing with ExpressRoute for Office 365</span></span>](routing-with-expressroute.md)

[<span data-ttu-id="f2271-178">Office 365용 ExpressRoute를 사용한 네트워크 계획</span><span class="sxs-lookup"><span data-stu-id="f2271-178">Network planning with ExpressRoute for Office 365</span></span>](network-planning-with-expressroute.md)

[<span data-ttu-id="f2271-179">Office 365용 ExpressRoute 구현</span><span class="sxs-lookup"><span data-stu-id="f2271-179">Implementing ExpressRoute for Office 365</span></span>](implementing-expressroute.md)

[<span data-ttu-id="f2271-180">Office 365의 express에서 BGP 커뮤니티 사용 (미리 보기)</span><span class="sxs-lookup"><span data-stu-id="f2271-180">Using BGP communities in ExpressRoute for Office 365 scenarios (preview)</span></span>](bgp-communities-in-expressroute.md)

[<span data-ttu-id="f2271-181">비즈니스용 Skype Online의 미디어 품질 및 네트워크 연결 성능</span><span class="sxs-lookup"><span data-stu-id="f2271-181">Media Quality and Network Connectivity Performance in Skype for Business Online</span></span>](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)

[<span data-ttu-id="f2271-182">초기 계획 및 성능 기록을 사용하여 Office 365 성능 조정</span><span class="sxs-lookup"><span data-stu-id="f2271-182">Office 365 performance tuning using baselines and performance history</span></span>](performance-tuning-using-baselines-and-history.md)

[<span data-ttu-id="f2271-183">Office 365 성능 문제 해결 계획</span><span class="sxs-lookup"><span data-stu-id="f2271-183">Performance troubleshooting plan for Office 365</span></span>](performance-troubleshooting-plan.md)

[<span data-ttu-id="f2271-184">Office 365 URL 및 IP 주소 범위</span><span class="sxs-lookup"><span data-stu-id="f2271-184">Office 365 URLs and IP address ranges</span></span>](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges)

[<span data-ttu-id="f2271-185">Office 365 네트워크 및 성능 조정</span><span class="sxs-lookup"><span data-stu-id="f2271-185">Office 365 network and performance tuning</span></span>](network-planning-and-performance.md)
