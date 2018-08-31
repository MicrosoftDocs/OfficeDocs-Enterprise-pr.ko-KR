---
title: Office 365의 NAT 지원
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 1/24/2017
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- BCS160
ms.assetid: 170e96ea-d65d-4e51-acac-1de56abe39b9
description: '요약: NAT(Network Address Translation)를 사용하여 조직 내에서 IP 주소당 사용할 수 있는 정확한 클라이언트 수를 예측하는 방법에 대한 세부 정보를 제공합니다.'
ms.openlocfilehash: 733d591bded599cfaece988a624baa7a3c0d4b06
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541892"
---
# <a name="nat-support-with-office-365"></a><span data-ttu-id="23fda-103">Office 365의 NAT 지원</span><span class="sxs-lookup"><span data-stu-id="23fda-103">NAT support with Office 365</span></span>

 <span data-ttu-id="23fda-104">**요약:** NAT(Network Address Translation)를 사용하여 조직 내에서 IP 주소당 사용할 수 있는 정확한 클라이언트 수를 예측하는 방법에 대한 세부 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="23fda-104">**Summary:** Provides details about how to approximate the correct number of clients you can use per IP address within your organization using Network Address Translation (NAT).</span></span> 
  
<span data-ttu-id="23fda-105">이전에 대 한 지침 IP 주소 당 사용 하 여 Office 365에 연결 해야 하는 Exchange 클라이언트의 최대 네트워크 포트 당 약 2, 000 클라이언트 했음을 제시 합니다.</span><span class="sxs-lookup"><span data-stu-id="23fda-105">Previously, guidance suggested that the maximum number of Exchange clients you should use per IP address to connect to Office 365 was about 2,000 clients per network port.</span></span>
  
## <a name="why-use-nat"></a><span data-ttu-id="23fda-106">NAT를 사용하는 이유</span><span class="sxs-lookup"><span data-stu-id="23fda-106">Why use NAT?</span></span>

<span data-ttu-id="23fda-107">NAT를 사용 하 여 다양 한 회사 네트워크에 있는 사용자 수 "공유" 몇 공개적으로 라우팅 가능한 IP 주소.</span><span class="sxs-lookup"><span data-stu-id="23fda-107">By using NAT, thousands of people on a corporate network can "share" a few publicly routable IP addresses.</span></span>
  
<span data-ttu-id="23fda-p101">대부분의 회사 네트워크에서는 개인(RFC1918) IP 주소 공간을 사용합니다. 개인 주소 공간은 IANA(Internet Assigned Numbers Authority)를 통해 할당되며 글로벌 인터넷으로/인터넷에서 직접 라우팅되지 않는 네트워크 전용으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="23fda-p101">Most corporate networks use private (RFC1918) IP address space. Private address space is allocated by the Internet Assigned Numbers Authority (IANA) and intended solely for networks that do not route directly to and from the global Internet.</span></span>
  
<span data-ttu-id="23fda-p102">개인 IP 주소 공간에서 장치에 대 한 인터넷 액세스를 제공 하려면 조직은 방화벽 및 네트워크 주소 변환 (NAT) 또는 포트 주소 변환 (PAT) 서비스를 제공 하는 프록시 같은 게이트웨이 기술을 사용 합니다. 이러한 게이트웨이 내부 트래픽을 확인 (Office 365 포함)의 인터넷 장치 하나 이상의 공개적으로 라우팅 가능한 IP 주소에서 들리는 수를 표시 합니다. 서로 다른 원본 TCP 포트는 공용 IP 주소에는 내부 장치에서 각 아웃 바운드 연결으로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="23fda-p102">To provide Internet access to devices on a private IP address space, organizations use gateway technologies like firewalls and proxies that provide network address translation (NAT) or port address translation (PAT) services. These gateways make traffic from internal devices to the Internet (including Office 365) appear to be coming from one or more publicly routable IP addresses. Each outbound connection from an internal device translates to a different source TCP port on the public IP address.</span></span> 
  
## <a name="why-do-you-need-to-have-so-many-connections-open-to-office-365-at-the-same-time"></a><span data-ttu-id="23fda-113">Office 365에 개방 됨 동시에 너무 많은 연결 시간이 필요한 이유?</span><span class="sxs-lookup"><span data-stu-id="23fda-113">Why do you need to have so many connections open to Office 365 at the same time?</span></span>

<span data-ttu-id="23fda-p103">Outlook에서는 추가 기능, 공유 일정, 사서함 등이 있는 경우 연결을 8개 이상 열 수도 있습니다. Windows 기반 NAT 장치에서 사용 가능한 최대 포트 수는 64,000개이므로, 포트가 소모될 때까지 각 IP 주소를 최대 8,000명의 사용자가 사용할 수 있습니다. 고객이 NAT에 대해 Windows OS를 기반으로 하지 않는 장치를 사용하는 경우 사용 가능한 총 포트 수는 사용 중인 NAT 장치 또는 소프트웨어에 따라 다릅니다. 이러한 경우 최대 포트 수는 64,000개보다 적을 수 있습니다. 포트 사용 가능성은 다른 요인에도 영향을 받는데, 예를 들어 자체 사용을 위해 포트 4,000개를 제한하는 Windows에서는 사용 가능한 총 포트 수가 60,000개로 줄어듭니다. 또한 동시에 연결이 가능하여 추가 포트가 필요한 Internet Explorer 등의 기타 응용 프로그램이 있을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23fda-p103">Outlook may open eight or more connections (in situations where there are add-ins, shared calendars, mailboxes, etc.). Because there are a maximum of 64,000 ports available on a Windows-based NAT device, there can be a maximum of 8,000 users behind an IP address before the ports are exhausted. Note that if customers are using non-Windows OS-based devices for NAT, the total available ports are dependent on what NAT device or software is being used. In this scenario, the maximum number of ports could be less than 64,000. Availability of ports is also affected by other factors such as Windows restricting 4,000 ports for its own use, which reduces the total number of available ports to 60,000.There may be other applications, such as Internet Explorer, that could connect at the same time, requiring additional ports.</span></span>
  
## <a name="calculating-maximum-supported-devices-behind-a-single-public-ip-address-with-office-365"></a><span data-ttu-id="23fda-119">Office 365와 함께 단일 공용 IP 주소 뒤에 최대 지원 되는 장치 수 계산</span><span class="sxs-lookup"><span data-stu-id="23fda-119">Calculating maximum supported devices behind a single public IP address with Office 365</span></span>

<span data-ttu-id="23fda-p104">단일 공용 IP 주소 뒤에 있는 장치의 최대 수를 확인 하려면 클라이언트 당 최대 포트 사용량을 확인 하려면 네트워크 트래픽을 모니터링 해야 합니다. 또한 포트 사용량 (최소 4)에 대 한 최대 계수를 사용할 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="23fda-p104">To determine the maximum number of devices behind a single public IP address, you should monitor network traffic to determine peak port consumption per client. Also, a peak factor should be used for the port usage (minimum 4).</span></span> 
  
 <span data-ttu-id="23fda-122">**다음 수식을 사용 하 여 IP 주소 당 지원 되는 장치 수를 계산 합니다.**</span><span class="sxs-lookup"><span data-stu-id="23fda-122">**Use the following formula to calculate the number of supported devices per IP address:**</span></span>
  
<span data-ttu-id="23fda-123">단일 공용 IP 주소 뒤에 장치를 지원 되는 최대 = (64000-제한 된 포트) / (최대 포트 사용량 + 최대 계수)</span><span class="sxs-lookup"><span data-stu-id="23fda-123">Maximum supported devices behind a single public IP address = (64,000 - restricted ports)/(Peak port consumption + peak factor)</span></span>
  
 <span data-ttu-id="23fda-124">**예: true 인 다음 하는 경우:**</span><span class="sxs-lookup"><span data-stu-id="23fda-124">**For example, if the following were true:**</span></span>
  
- <span data-ttu-id="23fda-125">운영 체제에 대 한 **제한 된 포트:** 4000</span><span class="sxs-lookup"><span data-stu-id="23fda-125">**Restricted ports:** 4,000 for the operating system</span></span> 
    
- <span data-ttu-id="23fda-126">장치당 **최대 포트 사용량:** 6</span><span class="sxs-lookup"><span data-stu-id="23fda-126">**Peak port consumption:** 6 per device</span></span> 
    
- <span data-ttu-id="23fda-127">**최대 계수:** 4</span><span class="sxs-lookup"><span data-stu-id="23fda-127">**Peak factor:** 4</span></span> 
    
<span data-ttu-id="23fda-128">그런 다음, 지원 되는 최대 장치 단일 공용 IP 주소 뒤에 = (64000 4000) / (6 + 4) = 6000</span><span class="sxs-lookup"><span data-stu-id="23fda-128">Then, the maximum supported devices behind a single public IP address = (64,000 - 4,000)/(6 + 4) = 6,000</span></span>
  
<span data-ttu-id="23fda-p105">호스팅 팩, Microsoft Office Outlook 2007 용 2011 년 9 월 또는 Microsoft Outlook 2010 용 2011 년 11 월에서 업데이트 또는 이후의 업데이트, Outlook (두 Office Outlook 2007과 함께 서비스에서에서 연결 수에 포함 된 Office 365의 릴리스와 함께 2와 Outlook 2010 팩)를 Exchange 2 정도로 적은 수 있습니다. 다른 운영 체제, 포트는 최대에서 네트워크에 필요한 최소 및 최대 수를 결정 하는 등 사용자 동작에에서 영향을 주지 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="23fda-p105">With the release of Office 365 hosting pack, included in the updates from September 2011 for Microsoft Office Outlook 2007, or November 2011 for Microsoft Outlook 2010, or a later update, the number of connections from Outlook (both Office Outlook 2007 with Service Pack 2 and Outlook 2010) to Exchange can be as few as 2. You'll need to factor in the different operating systems, user behaviors, and so on to determine the minimum and maximum number of ports that your network will require at peak.</span></span>
  
<span data-ttu-id="23fda-131">단일 공용 IP 주소 뒤에 더 많은 장치를 지원 하려면 장치 지원 될 수 있는 최대 수를 평가 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="23fda-131">If you want to support more devices behind a single public IP address, follow the steps outlined to assess the maximum number of devices that can be supported:</span></span>
  
<span data-ttu-id="23fda-p106">클라이언트 당 최대 포트 사용량을 확인 하려면 네트워크 트래픽을 모니터링 합니다. 이 데이터를 수집 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="23fda-p106">Monitor network traffic to determine peak port consumption per client. You should collect this data:</span></span>
  
- <span data-ttu-id="23fda-134">여러 위치에서</span><span class="sxs-lookup"><span data-stu-id="23fda-134">From multiple locations</span></span>
    
- <span data-ttu-id="23fda-135">여러 장치에서</span><span class="sxs-lookup"><span data-stu-id="23fda-135">From multiple devices</span></span>
    
- <span data-ttu-id="23fda-136">여러 번에 걸쳐</span><span class="sxs-lookup"><span data-stu-id="23fda-136">At multiple times</span></span>
    
<span data-ttu-id="23fda-137">위의 수식을 사용하여 환경에서 지원할 수 있는 IP 주소당 최대 사용자 수를 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="23fda-137">Use the preceding formula to calculate the maximum users per IP address that can be supported in their environment.</span></span>
  
<span data-ttu-id="23fda-p107">추가 공용 IP 주소를 클라이언트 부하 분산에 대 한 다양 한 방법이 있습니다. 사용 가능한 전략 회사 게이트웨이 솔루션의 기능에 따라 달라 집니다. 간단한 솔루션은 사용자 주소 공간을 분리 하 고 정적으로 "할당" 다양 한 IP 주소를 각 게이트웨이에 하는 것입니다. 다른 많은 게이트웨이 장치를 제공 하는 방법은 풀의 IP 주소를 사용 하는 기능입니다. 주소 풀의 장점은 훨씬 더 동적이 고 사용자 수가 늘어남에 따라 조정을 요구 하도록 되지 않을 것입니다.</span><span class="sxs-lookup"><span data-stu-id="23fda-p107">There are various methods for distributing client load across additional public IP addresses. Strategies available depend on the capabilities of the corporate gateway solution. The simplest solution is to segment your user address space and statically "assign" a number of IP addresses to each gateway. Another alternative that many gateway devices offer is the ability to use a pool of IP addresses. The benefit of the address pool is that it is much more dynamic and less likely to require adjustment as your user base grows.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="23fda-143">참고 항목</span><span class="sxs-lookup"><span data-stu-id="23fda-143">See also</span></span>

[<span data-ttu-id="23fda-144">Office 365 끝점 관리</span><span class="sxs-lookup"><span data-stu-id="23fda-144">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[<span data-ttu-id="23fda-145">Office 365 끝점 FAQ</span><span class="sxs-lookup"><span data-stu-id="23fda-145">Office 365 endpoints FAQ</span></span>](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

