---
title: NAT 지원(Office 365)
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 1/24/2017
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- BCS160
ms.assetid: 170e96ea-d65d-4e51-acac-1de56abe39b9
description: '요약: NAT (Network Address Translation)를 사용 하 여 조직 내에서 IP 주소당 사용할 수 있는 정확한 클라이언트 수를 대략적으로 결정 하는 방법에 대해 자세히 설명 합니다.'
ms.openlocfilehash: 6140cf664a08701e9491c241d5754d51196e3922
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844569"
---
# <a name="nat-support-with-office-365"></a><span data-ttu-id="925f7-103">NAT 지원(Office 365)</span><span class="sxs-lookup"><span data-stu-id="925f7-103">NAT support with Office 365</span></span>

<span data-ttu-id="925f7-104">*이 문서는 Microsoft 365 Enterprise와 Office 365 Enterprise에 모두 적용됩니다.*</span><span class="sxs-lookup"><span data-stu-id="925f7-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="925f7-105">이전에는 네트워크 포트당 약 2000 클라이언트에서 IP 주소당 365에 사용 해야 하는 최대 Exchange 클라이언트 수를 제안 했습니다.</span><span class="sxs-lookup"><span data-stu-id="925f7-105">Previously, guidance suggested that the maximum number of Exchange clients you should use per IP address to connect to Office 365 was about 2,000 clients per network port.</span></span>
  
## <a name="why-use-nat"></a><span data-ttu-id="925f7-106">NAT를 사용 하는 이유</span><span class="sxs-lookup"><span data-stu-id="925f7-106">Why use NAT?</span></span>

<span data-ttu-id="925f7-107">NAT를 사용 하 여 회사 네트워크에 있는 수천 명의 사용자가 공용으로 라우팅할 수 있는 IP 주소를 몇 개 "공유" 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="925f7-107">By using NAT, thousands of people on a corporate network can "share" a few publicly routable IP addresses.</span></span>
  
<span data-ttu-id="925f7-108">대부분의 회사 네트워크는 개인 (RFC1918) IP 주소 공간을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="925f7-108">Most corporate networks use private (RFC1918) IP address space.</span></span> <span data-ttu-id="925f7-109">개인 주소 공간은 인터넷에서 할당 된 번호 기관 (IANA)에 의해 할당 되며 전역 인터넷으로 직접 라우팅 되지 않는 네트워크 에서만 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="925f7-109">Private address space is allocated by the Internet Assigned Numbers Authority (IANA) and intended solely for networks that do not route directly to and from the global Internet.</span></span>
  
<span data-ttu-id="925f7-110">개인 IP 주소 공간에서 장치에 대 한 인터넷 액세스를 제공 하기 위해 조직은 NAT (network address translation) 또는 PAT (포트 주소 변환) 서비스를 제공 하는 방화벽과 같은 게이트웨이 기술을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="925f7-110">To provide Internet access to devices on a private IP address space, organizations use gateway technologies like firewalls and proxies that provide network address translation (NAT) or port address translation (PAT) services.</span></span> <span data-ttu-id="925f7-111">이러한 게이트웨이는 내부 장치에서 인터넷으로의 트래픽 (Office 365 포함)을 공용으로 라우팅할 수 있는 하나 이상의 IP 주소에서 보내는 것으로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="925f7-111">These gateways make traffic from internal devices to the Internet (including Office 365) appear to be coming from one or more publicly routable IP addresses.</span></span> <span data-ttu-id="925f7-112">내부 장치에서의 각 아웃 바운드 연결은 공용 IP 주소의 다른 원본 TCP 포트로 변환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="925f7-112">Each outbound connection from an internal device translates to a different source TCP port on the public IP address.</span></span> 
  
## <a name="why-do-you-need-to-have-so-many-connections-open-to-office-365-at-the-same-time"></a><span data-ttu-id="925f7-113">Office 365에서 여러 연결이 동시에 열리도록 해야 하는 이유는 무엇 인가요?</span><span class="sxs-lookup"><span data-stu-id="925f7-113">Why do you need to have so many connections open to Office 365 at the same time?</span></span>

<span data-ttu-id="925f7-114">Outlook에서는 추가 기능, 공유 일정, 사서함 등이 있는 경우 8 개 이상의 연결을 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="925f7-114">Outlook may open eight or more connections (in situations where there are add-ins, shared calendars, mailboxes, etc.).</span></span> <span data-ttu-id="925f7-115">Windows 기반 NAT 장치에서는 최대 64000 개의 포트를 사용할 수 있으므로 포트를 모두 사용 하기 전에 IP 주소 뒤에 최대 8000 명의 사용자가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="925f7-115">Because there are a maximum of 64,000 ports available on a Windows-based NAT device, there can be a maximum of 8,000 users behind an IP address before the ports are exhausted.</span></span> <span data-ttu-id="925f7-116">고객이 NAT에 대해 비 Windows OS 기반 장치를 사용 하는 경우 사용할 수 있는 총 포트는 사용 중인 NAT 장치나 소프트웨어에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="925f7-116">Note that if customers are using non-Windows OS-based devices for NAT, the total available ports are dependent on what NAT device or software is being used.</span></span> <span data-ttu-id="925f7-117">이 시나리오에서 포트의 최대 수는 64000 보다 작을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="925f7-117">In this scenario, the maximum number of ports could be less than 64,000.</span></span> <span data-ttu-id="925f7-118">포트를 사용 하는 경우에도 Windows 제한 4000 포트와 같은 다른 요인의 영향을 받으며, 사용할 수 있는 총 포트 수가 60, 000 개까지 줄어듭니다. Internet Explorer와 같이 동시에 연결할 수 있는 다른 응용 프로그램이 있을 수 있습니다. 추가 포트를 요구 합니다.</span><span class="sxs-lookup"><span data-stu-id="925f7-118">Availability of ports is also affected by other factors such as Windows restricting 4,000 ports for its own use, which reduces the total number of available ports to 60,000.There may be other applications, such as Internet Explorer, that could connect at the same time, requiring additional ports.</span></span>
  
## <a name="calculating-maximum-supported-devices-behind-a-single-public-ip-address-with-office-365"></a><span data-ttu-id="925f7-119">Office 365을 사용 하 여 단일 공용 IP 주소에서 지원 되는 최대 장치 계산</span><span class="sxs-lookup"><span data-stu-id="925f7-119">Calculating maximum supported devices behind a single public IP address with Office 365</span></span>

<span data-ttu-id="925f7-120">단일 공용 IP 주소에 포함 되는 최대 장치 수를 확인 하려면 네트워크 트래픽을 모니터링 하 여 클라이언트당 최대 포트 사용량을 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="925f7-120">To determine the maximum number of devices behind a single public IP address, you should monitor network traffic to determine peak port consumption per client.</span></span> <span data-ttu-id="925f7-121">또한 포트 사용 (최소 4)에 대해 최대 인수를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="925f7-121">Also, a peak factor should be used for the port usage (minimum 4).</span></span> 
  
 <span data-ttu-id="925f7-122">**다음 수식을 사용 하 여 IP 주소당 지원 되는 장치 수를 계산 합니다.**</span><span class="sxs-lookup"><span data-stu-id="925f7-122">**Use the following formula to calculate the number of supported devices per IP address:**</span></span>
  
<span data-ttu-id="925f7-123">단일 공용 IP 주소에서 지원 되는 최대 장치 수 = (64000-제한 된 포트)/(최대 포트 소비 + 피크 계수)</span><span class="sxs-lookup"><span data-stu-id="925f7-123">Maximum supported devices behind a single public IP address = (64,000 - restricted ports)/(Peak port consumption + peak factor)</span></span>
  
 <span data-ttu-id="925f7-124">**예를 들어 다음과 같은 경우를 예로 들 있습니다.**</span><span class="sxs-lookup"><span data-stu-id="925f7-124">**For example, if the following were true:**</span></span>
  
- <span data-ttu-id="925f7-125">**제한 된 포트:** 운영 체제의 경우 4000</span><span class="sxs-lookup"><span data-stu-id="925f7-125">**Restricted ports:** 4,000 for the operating system</span></span>

- <span data-ttu-id="925f7-126">**최대 포트 소비:** 장치당 6 개</span><span class="sxs-lookup"><span data-stu-id="925f7-126">**Peak port consumption:** 6 per device</span></span>

- <span data-ttu-id="925f7-127">**최대 인수:** 4</span><span class="sxs-lookup"><span data-stu-id="925f7-127">**Peak factor:** 4</span></span>

<span data-ttu-id="925f7-128">그런 다음 단일 공용 IP 주소에서 지원 되는 최대 장치 수 = (64000-4000)/(6 + 4) = 6000</span><span class="sxs-lookup"><span data-stu-id="925f7-128">Then, the maximum supported devices behind a single public IP address = (64,000 - 4,000)/(6 + 4) = 6,000</span></span>
  
<span data-ttu-id="925f7-129">Office 365 호스팅 팩을 사용 하는 경우 Microsoft Office Outlook 2007 용 2011 년 9 월에 제공 되는 업데이트 또는 Microsoft Outlook 2010의 11 월 2011 또는 이후 업데이트에 포함 된 Outlook의 연결 수 (Office Outlook 2007 with Service Exchange에 대 한 팩 2 및 Outlook 2010)는 2 개까지 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="925f7-129">With the release of Office 365 hosting pack, included in the updates from September 2011 for Microsoft Office Outlook 2007, or November 2011 for Microsoft Outlook 2010, or a later update, the number of connections from Outlook (both Office Outlook 2007 with Service Pack 2 and Outlook 2010) to Exchange can be as few as 2.</span></span> <span data-ttu-id="925f7-130">네트워크 사용량이 최대 수준으로 요구 되는 최소 및 최대 포트 수를 결정 하려면 여러 운영 체제, 사용자 동작 등의 요소를 고려해 야 합니다.</span><span class="sxs-lookup"><span data-stu-id="925f7-130">You'll need to factor in the different operating systems, user behaviors, and so on to determine the minimum and maximum number of ports that your network will require at peak.</span></span>
  
<span data-ttu-id="925f7-131">단일 공용 IP 주소에서 더 많은 장치를 지원 하려면 설명 된 단계에 따라 지원 가능한 최대 장치 수를 평가 합니다.</span><span class="sxs-lookup"><span data-stu-id="925f7-131">If you want to support more devices behind a single public IP address, follow the steps outlined to assess the maximum number of devices that can be supported:</span></span>
  
<span data-ttu-id="925f7-132">네트워크 트래픽을 모니터링 하 여 클라이언트당 최대 포트 사용량을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="925f7-132">Monitor network traffic to determine peak port consumption per client.</span></span> <span data-ttu-id="925f7-133">다음 데이터를 수집 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="925f7-133">You should collect this data:</span></span>
  
- <span data-ttu-id="925f7-134">여러 위치에서</span><span class="sxs-lookup"><span data-stu-id="925f7-134">From multiple locations</span></span>
    
- <span data-ttu-id="925f7-135">여러 장치에서</span><span class="sxs-lookup"><span data-stu-id="925f7-135">From multiple devices</span></span>
    
- <span data-ttu-id="925f7-136">여러 번에</span><span class="sxs-lookup"><span data-stu-id="925f7-136">At multiple times</span></span>
    
<span data-ttu-id="925f7-137">이전 공식을 사용 하 여 환경에서 지원할 수 있는 IP 주소당 당 최대 사용자 개수를 계산 합니다.</span><span class="sxs-lookup"><span data-stu-id="925f7-137">Use the preceding formula to calculate the maximum users per IP address that can be supported in their environment.</span></span>
  
<span data-ttu-id="925f7-138">클라이언트 부하를 추가 공용 IP 주소에 분산 하는 방법에는 여러 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="925f7-138">There are various methods for distributing client load across additional public IP addresses.</span></span> <span data-ttu-id="925f7-139">사용 가능한 전략은 회사 게이트웨이 솔루션의 기능에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="925f7-139">Strategies available depend on the capabilities of the corporate gateway solution.</span></span> <span data-ttu-id="925f7-140">가장 간단한 방법은 사용자 주소 공간을 분할 하 고 각 게이트웨이에 여러 IP 주소를 정적으로 "할당" 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="925f7-140">The simplest solution is to segment your user address space and statically "assign" a number of IP addresses to each gateway.</span></span> <span data-ttu-id="925f7-141">많은 게이트웨이 장치에서 제공 하는 또 다른 대안은 IP 주소 풀을 사용 하는 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="925f7-141">Another alternative that many gateway devices offer is the ability to use a pool of IP addresses.</span></span> <span data-ttu-id="925f7-142">주소 풀의 이점은 보다 동적이 고 사용자 기반이 증가 함에 따라 조정이 필요할 가능성이 더 낮습니다.</span><span class="sxs-lookup"><span data-stu-id="925f7-142">The benefit of the address pool is that it is much more dynamic and less likely to require adjustment as your user base grows.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="925f7-143">참고 항목</span><span class="sxs-lookup"><span data-stu-id="925f7-143">See also</span></span>

[<span data-ttu-id="925f7-144">Office 365 끝점 관리</span><span class="sxs-lookup"><span data-stu-id="925f7-144">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[<span data-ttu-id="925f7-145">Office 365 끝점 FAQ</span><span class="sxs-lookup"><span data-stu-id="925f7-145">Office 365 endpoints FAQ</span></span>](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
