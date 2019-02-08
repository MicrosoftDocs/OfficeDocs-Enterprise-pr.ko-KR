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
description: Office 365와 Azure ExpressRoute를 사용 하는 방법 및 Office 365에 사용 하기 위한 Azure ExpressRoute를 배포 하는 경우 필요할 수 있는 네트워크 구현 프로젝트를 계획 하는 방법에 알아봅니다.
ms.openlocfilehash: c8cff4ef85c4383ba04829cf3cf8da3a1bc36715
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2019
ms.locfileid: "25911402"
---
# <a name="azure-expressroute-for-office-365"></a><span data-ttu-id="6570d-103">Office 365용 Azure Express 경로</span><span class="sxs-lookup"><span data-stu-id="6570d-103">Azure ExpressRoute for Office 365</span></span>

<span data-ttu-id="6570d-p101">Office 365와 Azure ExpressRoute를 사용 하는 방법 및 Office 365에 사용 하기 위한 Azure ExpressRoute를 배포 하는 경우 필요할 수 있는 네트워크 구현 프로젝트를 계획 하는 방법에 알아봅니다. Azure에서 실행 중인 인프라 및 플랫폼 서비스 네트워크 아키텍처 및 성능 고려 사항이 해결 하 여 사용 하면 좋은 됩니다. 이러한 경우 azure ExpressRoute를 좋습니다. Office 365 및 Dynamics 365 빌드되어에 안전 하 게 하 고 안정적으로 인터넷을 통해 액세스할 수와 동일 하 게 하는 서비스 제품으로 소프트웨어입니다. 인터넷 성능 및 보안에 대 한 및 좋습니다 Azure ExpressRoute Office 365에 대 한 문서 [Office 365에 대 한 네트워크 연결](network-connectivity.md)에서 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6570d-p101">Learn how Azure ExpressRoute is used with Office 365 and how to plan the network implementation project that will be required if you are deploying Azure ExpressRoute for use with Office 365. Infrastructure and platform services running in Azure will often benefit by addressing network architecture and performance considerations. We recommend ExpressRoute for Azure in these cases. Software as a Service offerings like Office 365 and Dynamics 365 have been built to be accessed securely and reliably via the Internet. You can read about Internet performance and security and when you might consider Azure ExpressRoute for Office 365 in the article [Network connectivity to Office 365](network-connectivity.md).</span></span>

> [!NOTE]
> <span data-ttu-id="6570d-p102">Office 365에 대 한 ExpressRoute를 사용 하는 데 Microsoft 인증이 필요 합니다. Microsoft는 모든 고객의 요청을 검토 하 고 요구 사항을 규정 하는 고객의 요구 하는 경우 직접 연결 하는 경우 Office 365 사용 현황에 대 한 ExpressRoute에 권한을 부여 합니다. 이러한 요구 사항, 있는 경우 Microsoft 검토를 시작 하려면 [Office 365 요청 양식에 대 한 ExpressRoute](https://aka.ms/O365ERReview) 에 직접 연결 필요 하다는 것을 의미를 해석 하는 규정을 텍스트 발췌문 및 웹 링크를 제공 하십시오. Office 365에 대 한 경로 필터를 만들 권한이 없는 구독 [오류 메시지](https://support.microsoft.com/kb/3181709)를 받습니다.</span><span class="sxs-lookup"><span data-stu-id="6570d-p102">Microsoft authorization is required to use ExpressRoute for Office 365. Microsoft reviews every customer request and authorizes ExpressRoute for Office 365 usage when a customer's regulatory requirement mandates direct connectivity. If you have such requirements, please provide the text excerpt and web link to the regulation which you interpret to mean that direct connectivity is required in the [ExpressRoute for Office 365 Request Form](https://aka.ms/O365ERReview) to begin a Microsoft review. Unauthorized subscriptions trying to create route filters for Office 365 will receive an [error message](https://support.microsoft.com/kb/3181709).</span></span> 

<span data-ttu-id="6570d-p103">선택한 Office 365 네트워크 트래픽에 대 한 Office 365에 대 한 네트워크에 직접 연결을 추가할 수 있습니다. Azure ExpressRoute 직접 연결을 예측 가능한 성능을 제공 하 고 Microsoft 네트워킹 구성 요소에 대 한 가동 시간 SLA 99.95%와 함께 제공 합니다. Azure ExpressRoute을 통해 지원 하지 않는 서비스에 대 한 인터넷에 연결을 여전히 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6570d-p103">You can now add a direct network connection to Office 365 for selected Office 365 network traffic. Azure ExpressRoute offers a direct connection, predictable performance, and comes with an uptime SLA of 99.95% for the Microsoft networking components. You'll still require an internet connection for services that aren't supported over Azure ExpressRoute.</span></span>

## <a name="planning-azure-expressroute-for-office-365"></a><span data-ttu-id="6570d-116">Office 365 용 Azure ExpressRoute 계획</span><span class="sxs-lookup"><span data-stu-id="6570d-116">Planning Azure ExpressRoute for Office 365</span></span>

<span data-ttu-id="6570d-p104">인터넷 연결 외에도 하기도 하 고 Microsoft 네트워킹 구성 요소에 대 한 99.95% 가동 시간 SLA 제공 하는 직접 연결을 통해 자신의 Office 365 네트워크 트래픽의 하위 집합을 라우팅할 수 있습니다. Azure ExpressRoute Office 365 및 기타 Microsoft 클라우드 서비스에 전용된 네트워크 연결이를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6570d-p104">In addition to internet connectivity, you may choose to route a subset of their Office 365 network traffic over a direct connection that offers predictability and a 99.95% uptime SLA for the Microsoft networking components. Azure ExpressRoute provides you with this dedicated network connection to Office 365 and other Microsoft cloud services.</span></span>

<span data-ttu-id="6570d-p105">있는지 여부는 기존 MPLS WAN을 관계 없이 ExpressRoute에 추가할 수; 세가지 방법 중 하나에서 네트워크 아키텍처 지원 되는 클라우드 exchange 공동 위치 공급자, 이더넷 지점간 연결 공급자를 통해 또는 MPLS 연결 공급자를 통해 합니다. 어떤 [사용자의 지역에서 사용할 수 있는 공급자를](https://azure.microsoft.com/documentation/articles/expressroute-locations/)참조 합니다. 직접 ExpressRoute 연결에 설명 된 응용 프로그램에 대 한 연결을 사용 하는 [어떤 Office 365 서비스는 포함 되어 있습니까?](azure-expressroute.md#BKMK_WhatDoIGet) 아래 있습니다. 인터넷을 통과 하는 다른 모든 응용 프로그램 및 서비스에 대 한 네트워크 트래픽을 계속 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6570d-p105">Regardless of whether you have an existing MPLS WAN, ExpressRoute can be added to your network architecture in one of three ways; through a supported cloud exchange co-location provider, an Ethernet point-to-point connection provider, or through an MPLS connection provider. See what [providers are available in your region](https://azure.microsoft.com/documentation/articles/expressroute-locations/). The direct ExpressRoute connection will enable connectivity to the applications outlined in [What Office 365 services are included?](azure-expressroute.md#BKMK_WhatDoIGet) below. Network traffic for all other applications and services will continue to traverse the internet.</span></span>

<span data-ttu-id="6570d-p106">Office 365, Windows Update 및 TechNet 등의 모든 Microsoft 응용 프로그램에 대 한 액세스에 대 한 인터넷을 통해 Microsoft의 데이터 센터에 연결 하는 일반적인 Office 365 고객을 표시 하는 다음과 같은 높은 수준의 네트워크 다이어그램을 고려 합니다. 고객 여부 독립적인 인터넷에 연결 또는 온-프레미스 네트워크에서을 연결 하는경우에만 자신이 관계 없이 비슷한 네트워크 경로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="6570d-p106">Consider the following high level network diagram which shows a typical Office 365 customer connecting to Microsoft's datacenters over the internet for access to all Microsoft applications such as Office 365, Windows Update, and TechNet. Customers use a similar network path regardless of whether they're connecting from an on-premises network or from an independent internet connection.</span></span>

![Office 365 네트워크 연결](media/9d8bc622-4a38-4a3b-a0f3-68657712d460.png)

<span data-ttu-id="6570d-p107">이제 인터넷 및 ExpressRoute를 사용 하 여 Office 365에 연결 하는 Office 365 고객에서는 설명 하는 업데이트 된 다이어그램을 살펴봅니다. 공용 DNS 및 콘텐츠 배달 네트워크 노드와 같은 일부 연결에 여전히 공용 인터넷 연결 필요를 확인 합니다. 또한 인터넷을 통해 연결 하는 연결 된 건물 자신의 ExpressRoute에 있지 않은 고객의 사용자를 확인 하십시오.</span><span class="sxs-lookup"><span data-stu-id="6570d-p107">Now look at the updated diagram which depicts an Office 365 customer who uses both the internet and ExpressRoute to connect to Office 365. Notice that some connections such as Public DNS and Content Delivery Network nodes still require the public internet connection. Also notice the customer's users who are not located in their ExpressRoute connected building are connecting over the Internet.</span></span>

![ExpressRoute와의 연결을 office 365](media/251788c4-0937-4584-9b2c-df08e11611fc.png)

<span data-ttu-id="6570d-p108">자세한 내용은 여전히 지 여부 설명 [Office 365 용 Azure ExpressRoute와 네트워크 트래픽을 관리](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408) 하는 방법을 설명 하 고 [Office 365 용 Azure ExpressRoute를 구성](https://azure.microsoft.com/documentation/articles/expressroute-faqs/)하는 방법입니다. Channel 9를 더 철저 하 게 개념에 설명 하는 데 도움이에서 10 부 [Office 365 교육에 대 한 Azure ExpressRoute](https://channel9.msdn.com/series/aer) 시리즈를 기록 했을 때 했습니다.</span><span class="sxs-lookup"><span data-stu-id="6570d-p108">Still want more information? Learn how to [manage your network traffic with Azure ExpressRoute for Office 365](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408) and learn how to [configure Azure ExpressRoute for Office 365](https://azure.microsoft.com/documentation/articles/expressroute-faqs/). We've also recorded a 10 part [Azure ExpressRoute for Office 365 Training](https://channel9.msdn.com/series/aer) series on Channel 9 to help explain the concepts more thoroughly.</span></span>

<span data-ttu-id="6570d-133">([Office 365 용 azure ExpressRoute](azure-expressroute.md#BKMK_HOME))</span><span class="sxs-lookup"><span data-stu-id="6570d-133">([Azure ExpressRoute for Office 365](azure-expressroute.md#BKMK_HOME))</span></span>

## <a name="what-office-365-services-are-included"></a><span data-ttu-id="6570d-134">어떤 Office 365 서비스는 포함 되어 있습니까?</span><span class="sxs-lookup"><span data-stu-id="6570d-134">What Office 365 services are included?</span></span>
<span data-ttu-id="6570d-135"><a name="BKMK_WhatDoIGet"> </a></span><span class="sxs-lookup"><span data-stu-id="6570d-135"></span></span>

<span data-ttu-id="6570d-p109">다음 표에서 ExpressRoute을 통해 지원 되는 Office 365 서비스를 보여줍니다. 이러한 응용 프로그램에 대 한 네트워크 요청은 인터넷 연결 필요를 이해 하는 [Office 365 끝점 문서](https://aka.ms/o365endpoints) 를 검토 하십시오.</span><span class="sxs-lookup"><span data-stu-id="6570d-p109">The following table lists the Office 365 services that are supported over ExpressRoute. Please review the [Office 365 endpoints article](https://aka.ms/o365endpoints) to understand which network requests for these applications require internet connectivity.</span></span>

|<span data-ttu-id="6570d-138">**포함 된 응용 프로그램**</span><span class="sxs-lookup"><span data-stu-id="6570d-138">**Applications included**</span></span>|
|:-----|
|<span data-ttu-id="6570d-139">Exchange Online<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="6570d-139">Exchange Online<sup>1</sup></span></span> <br/> <span data-ttu-id="6570d-140">Exchange Online Protection<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="6570d-140">Exchange Online Protection<sup>1</sup></span></span> <br/> <span data-ttu-id="6570d-141"><sup>1</sup> 굴</span><span class="sxs-lookup"><span data-stu-id="6570d-141">Delve<sup>1</sup></span></span> <br/> |
|<span data-ttu-id="6570d-142">비즈니스 온라인<sup>1</sup> 에 대 한 Skype</span><span class="sxs-lookup"><span data-stu-id="6570d-142">Skype for Business Online<sup>1</sup></span></span> <br/> |
|<span data-ttu-id="6570d-143">SharePoint Online<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="6570d-143">SharePoint Online<sup>1</sup></span></span> <br/> <span data-ttu-id="6570d-144">비즈니스<sup>1</sup> 에 대 한 OneDrive</span><span class="sxs-lookup"><span data-stu-id="6570d-144">OneDrive for Business<sup>1</sup></span></span> <br/> <span data-ttu-id="6570d-145">Project Online<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="6570d-145">Project Online<sup>1</sup></span></span> <br/> |
|<span data-ttu-id="6570d-146">포털 및 공유<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="6570d-146">Portal and shared<sup>1</sup></span></span> <br/> <span data-ttu-id="6570d-147">Azure Active Directory<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="6570d-147">Azure Active Directory<sup>1</sup></span></span> <br/> <span data-ttu-id="6570d-148">AAD 연결<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="6570d-148">AAD Connect<sup>1</sup></span></span> <br/> <span data-ttu-id="6570d-149">Office Online<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="6570d-149">Office Online<sup>1</sup></span></span> <br/> |

<span data-ttu-id="6570d-150"><sup>1</sup> 이러한 응용 프로그램의 각 ExpressRoute을 통해 지원 되지 인터넷 연결 요구 사항이 적용에 대 한 자세한 내용은 [Office 365 끝점 문서](https://aka.ms/o365endpoints) 를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="6570d-150"><sup>1</sup>Each of these applications have internet connectivity requirements not supported over ExpressRoute, see the [Office 365 endpoints article](https://aka.ms/o365endpoints) for more information.</span></span>

<span data-ttu-id="6570d-151">Office 365에 대 한 ExpressRoute에 포함 되지 않은 서비스는 Office 365 ProPlus 클라이언트 다운로드, 온-프레미스 Identity 공급자 로그인, 중국에서 (21 Vianet에서 운영) Office 365 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="6570d-151">The services that aren't included with ExpressRoute for Office 365 are Office 365 ProPlus client downloads, On-premises Identity Provider Sign-In, and Office 365 (operated by 21 Vianet) service in China.</span></span>

<span data-ttu-id="6570d-152">([Office 365 용 azure ExpressRoute](azure-expressroute.md#BKMK_HOME))</span><span class="sxs-lookup"><span data-stu-id="6570d-152">([Azure ExpressRoute for Office 365](azure-expressroute.md#BKMK_HOME))</span></span>

## <a name="implementing-expressroute-for-office-365"></a><span data-ttu-id="6570d-153">Office 365용 ExpressRoute 구현</span><span class="sxs-lookup"><span data-stu-id="6570d-153">Implementing ExpressRoute for Office 365</span></span>

<span data-ttu-id="6570d-p110">네트워크 및 응용 프로그램 소유자가 참여 해야 하 고 새 [네트워크 라우팅 아키텍처](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408), 대역폭 요구 사항, 보안 될 위치를 확인 하려면 계획 신중 하 게 구현 고가용성 필요 ExpressRoute 구현 합니다. 를 구현 하기 위해 ExpressRoute 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6570d-p110">Implementing ExpressRoute requires the involvement of network and application owners and requires careful planning to determine the new [network routing architecture](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408), bandwidth requirements, where security will be implemented, high availability, and so on. To implement ExpressRoute, you'll need to:</span></span>

1. <span data-ttu-id="6570d-p111">Office 365 연결 계획에 맞는 ExpressRoute 필요를 완벽 하 게 이해 합니다. 어떤 응용 프로그램이 인터넷 또는 ExpressRoute 사용 하 여를 이해 하 고 완벽 하 게 네트워크 용량을 계획, 보안 및 고가용성 필요한 인터넷 및 ExpressRoute를 사용 하 여 Office 365의 컨텍스트에서 트래픽입니다.</span><span class="sxs-lookup"><span data-stu-id="6570d-p111">Fully understand the need ExpressRoute satisfies in your Office 365 connectivity planning. Understand what applications will use the internet or ExpressRoute and fully plan your network capacity, security, and high availability needs in the context of using both the internet and ExpressRoute for Office 365 traffic.</span></span>

2. <span data-ttu-id="6570d-158">송신 및 인터넷과 ExpressRoute 트래픽을<sup>1</sup>에 대 한 피어 링 위치를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6570d-158">Determine the egress and peering locations for both internet and ExpressRoute traffic<sup>1</sup>.</span></span>

3. <span data-ttu-id="6570d-159">인터넷 및 ExpressRoute 연결에 필요한 용량을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6570d-159">Determine the capacity required on the internet and ExpressRoute connections.</span></span>

4. <span data-ttu-id="6570d-160">보안 및 기타 표준 경계 컨트롤<sup>1</sup>을 구현 하기 위한 전체 요금제에 가입한 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="6570d-160">Have a plan in place for implementing security and other standard perimeter controls<sup>1</sup>.</span></span>

5. <span data-ttu-id="6570d-161">유효한 Microsoft Azure 계정이 ExpressRoute 구독할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6570d-161">Have a valid Microsoft Azure account to subscribe to ExpressRoute.</span></span>

6. <span data-ttu-id="6570d-p112">[공급자를 승인](https://azure.microsoft.com/documentation/articles/expressroute-locations/)하 고 연결 모델을 선택 합니다. 염두에, 고객 여러 연결 모델을 선택할 수 또는 파트너와의 파트너 기존 네트워크 공급자와 같이 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6570d-p112">Select a connectivity model and an [approved provider](https://azure.microsoft.com/documentation/articles/expressroute-locations/). Keep in mind, customers can select multiple connectivity models or partners and the partner doesn't need to be the same as your existing network provider.</span></span>

7. <span data-ttu-id="6570d-164">ExpressRoute 트래픽을 웹서버로 전송 하기 전에 배포의 유효성을 검사 합니다.</span><span class="sxs-lookup"><span data-stu-id="6570d-164">Validate deployment prior to directing traffic to ExpressRoute.</span></span>

8. <span data-ttu-id="6570d-165">필요에 따라 [QoS를 구현](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d) 하 고 지역 확장을 평가 합니다.</span><span class="sxs-lookup"><span data-stu-id="6570d-165">Optionally [implement QoS](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d) and evaluate regional expansion.</span></span>

<span data-ttu-id="6570d-p113"><sup>1</sup> 중요 한 성능 고려 사항입니다. 여기에 결정 비즈니스를 위한 Skype 등의 응용 프로그램에 대 한 중요 한는 대기 시간에 영향을 줄 크게 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6570d-p113"><sup>1</sup>Important performance considerations. Decisions here can dramatically impact latency which is a critical for applications such as Skype for Business.</span></span>

<span data-ttu-id="6570d-168">추가 참조에 대 한 [ExpressRoute 설명서](https://azure.microsoft.com/documentation/articles/expressroute-introduction/)외에도 한 [라우팅 가이드](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408) 를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="6570d-168">For additional references, use our [routing guide](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408) in addition to the [ExpressRoute documentation](https://azure.microsoft.com/documentation/articles/expressroute-introduction/).</span></span>

<span data-ttu-id="6570d-p114">Office 365에 대 한 ExpressRoute를 구입 하려면 하나 이상의 [공급자 승인](https://azure.microsoft.com/documentation/articles/expressroute-locations/) 원하는 수 및 크기 회로 ExpressRoute 프리미엄 구독을 프로 비전을 함께 작동 하도록 필요 합니다. 추가 라이선스가 Office 365에서 구입할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6570d-p114">To purchase ExpressRoute for Office 365, you'll need to work with one or more [approved providers](https://azure.microsoft.com/documentation/articles/expressroute-locations/) to provision the desired number and size circuits with an ExpressRoute Premium subscription. There are no additional licenses to purchase from Office 365.</span></span>

<span data-ttu-id="6570d-171">다음의 간단한 링크를 사용할 수 있습니다. [https://aka.ms/expressrouteoffice365](https://aka.ms/expressrouteoffice365)</span><span class="sxs-lookup"><span data-stu-id="6570d-171">Here's a short link you can use to come back: [https://aka.ms/expressrouteoffice365](https://aka.ms/expressrouteoffice365)</span></span>

<span data-ttu-id="6570d-172">[Office 365에 대 한 ExpressRoute](https://aka.ms/ert)에 대 한로 등록을 준비?</span><span class="sxs-lookup"><span data-stu-id="6570d-172">Ready to sign-up for [ExpressRoute for Office 365](https://aka.ms/ert)?</span></span>

<span data-ttu-id="6570d-173">([Office 365 용 azure ExpressRoute](azure-expressroute.md#BKMK_HOME))</span><span class="sxs-lookup"><span data-stu-id="6570d-173">([Azure ExpressRoute for Office 365](azure-expressroute.md#BKMK_HOME))</span></span>

## <a name="related-topics"></a><span data-ttu-id="6570d-174">관련 항목</span><span class="sxs-lookup"><span data-stu-id="6570d-174">Related Topics</span></span>

[<span data-ttu-id="6570d-175">Office 365에 대한 네트워크 연결</span><span class="sxs-lookup"><span data-stu-id="6570d-175">Network connectivity to Office 365</span></span>](network-connectivity.md)

[<span data-ttu-id="6570d-176">Office 365 연결에 대한 ExpressRoute 관리</span><span class="sxs-lookup"><span data-stu-id="6570d-176">Managing ExpressRoute for Office 365 connectivity</span></span>](managing-expressroute-for-connectivity.md)

[<span data-ttu-id="6570d-177">Office 365용 ExpressRoute를 사용한 라우팅</span><span class="sxs-lookup"><span data-stu-id="6570d-177">Routing with ExpressRoute for Office 365</span></span>](routing-with-expressroute.md)

[<span data-ttu-id="6570d-178">Office 365용 ExpressRoute를 사용한 네트워크 계획</span><span class="sxs-lookup"><span data-stu-id="6570d-178">Network planning with ExpressRoute for Office 365</span></span>](network-planning-with-expressroute.md)

[<span data-ttu-id="6570d-179">Office 365용 ExpressRoute 구현</span><span class="sxs-lookup"><span data-stu-id="6570d-179">Implementing ExpressRoute for Office 365</span></span>](implementing-expressroute.md)

[<span data-ttu-id="6570d-180">Office 365용 ExpressRoute 시나리오에서 BGP 커뮤니티 사용(미리 보기)</span><span class="sxs-lookup"><span data-stu-id="6570d-180">Using BGP communities in ExpressRoute for Office 365 scenarios (preview)</span></span>](bgp-communities-in-expressroute.md)

[<span data-ttu-id="6570d-181">비즈니스용 Skype Online의 미디어 품질 및 네트워크 연결 성능</span><span class="sxs-lookup"><span data-stu-id="6570d-181">Media Quality and Network Connectivity Performance in Skype for Business Online</span></span>](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)

[<span data-ttu-id="6570d-182">초기 계획 및 성능 기록을 사용하여 Office 365 성능 조정</span><span class="sxs-lookup"><span data-stu-id="6570d-182">Office 365 performance tuning using baselines and performance history</span></span>](performance-tuning-using-baselines-and-history.md)

[<span data-ttu-id="6570d-183">Office 365 성능 문제 해결 계획</span><span class="sxs-lookup"><span data-stu-id="6570d-183">Performance troubleshooting plan for Office 365</span></span>](performance-troubleshooting-plan.md)

[<span data-ttu-id="6570d-184">Office 365 URL 및 IP 주소 범위</span><span class="sxs-lookup"><span data-stu-id="6570d-184">Office 365 URLs and IP address ranges</span></span>](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges)

[<span data-ttu-id="6570d-185">Office 365 네트워크 및 성능 조정</span><span class="sxs-lookup"><span data-stu-id="6570d-185">Office 365 network and performance tuning</span></span>](network-planning-and-performance.md)
