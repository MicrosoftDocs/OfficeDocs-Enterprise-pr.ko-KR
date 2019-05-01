---
title: Microsoft Azure IaaS에 대한 네트워킹 디자인
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/28/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 9cb70c9d-9ed9-47cc-af5a-6403d87d3372
description: '요약: Microsoft Azure IaaS에서 작업을 위한 최적화 된 네트워킹을 디자인 하는 방법을 알아봅니다.'
ms.openlocfilehash: c41e92445dd01a94b7d305b521bbd4330311fcb4
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/30/2019
ms.locfileid: "33491106"
---
# <a name="designing-networking-for-microsoft-azure-iaas"></a><span data-ttu-id="17fe4-103">Microsoft Azure IaaS에 대한 네트워킹 디자인</span><span class="sxs-lookup"><span data-stu-id="17fe4-103">Designing networking for Microsoft Azure IaaS</span></span>

 <span data-ttu-id="17fe4-104">**요약:** Microsoft Azure IaaS에서 작업을 위해 최적화 된 네트워킹을 디자인 하는 방법을 이해 합니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-104">**Summary:** Understand how to design optimized networking for workloads in Microsoft Azure IaaS.</span></span>
  
<span data-ttu-id="17fe4-105">네트워킹 최적화 azure IaaS에서 호스트 되는 작업에 대해 azure virtual network (vnet), 주소 공간, 라우팅, DNS 및 부하 분산을 이해 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-105">Optimizing networking for IT workloads hosted in Azure IaaS requires an understanding of Azure virtual networks (VNets), address spaces, routing, DNS, and load balancing.</span></span>
  
## <a name="planning-steps-for-any-vnet"></a><span data-ttu-id="17fe4-106">VNet에 대 한 단계 계획</span><span class="sxs-lookup"><span data-stu-id="17fe4-106">Planning steps for any VNet</span></span>

<span data-ttu-id="17fe4-107">모든 유형의 VNet에 대해 다음 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-107">Follow these steps for any type of VNet.</span></span>
  
### <a name="step-1-prepare-your-intranet-for-microsoft-cloud-services"></a><span data-ttu-id="17fe4-108">1 단계: 인트라넷에서 Microsoft 클라우드 서비스를 준비 합니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-108">Step 1: Prepare your intranet for Microsoft cloud services.</span></span>

<span data-ttu-id="17fe4-109">[microsoft 클라우드 연결의 공통 요소](common-elements-of-microsoft-cloud-connectivity.md)에 있는 **microsoft 클라우드 서비스용 네트워크 섹션을 준비 하는 단계** 를 진행 합니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-109">Go through the **Steps to prepare your network for Microsoft cloud services** section in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).</span></span>
  
### <a name="step-2-optimize-your-internet-bandwidth"></a><span data-ttu-id="17fe4-110">2 단계: 인터넷 대역폭을 최적화 합니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-110">Step 2: Optimize your Internet bandwidth.</span></span>

<span data-ttu-id="17fe4-111">[microsoft saas에 대 한 네트워킹 디자인](designing-networking-for-microsoft-saas.md)에서 **microsoft saas 서비스용 네트워크 준비** 섹션의 단계 2-4을 사용 하 여 인터넷 대역폭을 최적화 합니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-111">Optimize your Internet bandwidth using steps 2 - 4 of the **Steps to prepare your network for Microsoft SaaS services** section in [Designing networking for Microsoft SaaS](designing-networking-for-microsoft-saas.md).</span></span>
  
### <a name="step-3-determine-the-type-of-vnet-cloud-only-or-cross-premises"></a><span data-ttu-id="17fe4-112">3 단계: VNet 유형 (클라우드 전용 또는 크로스-프레미스)을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-112">Step 3: Determine the type of VNet (cloud-only or cross-premises).</span></span>

<span data-ttu-id="17fe4-113">클라우드 전용 VNet은 온-프레미스 네트워크에 연결 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-113">A cloud-only VNet has no connection to an on-premises network.</span></span> <span data-ttu-id="17fe4-114">예제는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-114">Here is an example.</span></span>
  
<span data-ttu-id="17fe4-115">**그림 1: 클라우드 전용 VNet**</span><span class="sxs-lookup"><span data-stu-id="17fe4-115">**Figure 1: A cloud-only VNet**</span></span>

![그림 1: Azure의 클라우드 전용 가상 네트워크](media/8be19104-02b3-4a7f-b0a0-30d6fcf8890b.png)
  
<span data-ttu-id="17fe4-117">그림 1은 클라우드 전용 VNet에 있는 가상 컴퓨터 집합을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-117">Figure 1 shows a set of virtual machines in a cloud-only VNet.</span></span>
  
<span data-ttu-id="17fe4-118">크로스-프레미스 VNet에는 Azure 게이트웨이를 통한 온-프레미스 네트워크에 대 한 S2S (사이트 간) VPN 또는 express 간 연결이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-118">A cross-premises VNet has a site-to-site (S2S) VPN or ExpressRoute connection to an on-premises network through an Azure gateway.</span></span> <span data-ttu-id="17fe4-119">예제는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-119">Here is an example.</span></span>
  
<span data-ttu-id="17fe4-120">**그림 2: 크로스-프레미스 VNet**</span><span class="sxs-lookup"><span data-stu-id="17fe4-120">**Figure 2: A cross-premises VNet**</span></span>

![그림 2: Azure의 크로스-프레미스 가상 네트워크](media/caacf007-e0dc-45d3-9531-441109776d25.png)
  
<span data-ttu-id="17fe4-122">그림 2에서는 온-프레미스 네트워크에 연결 된 크로스-프레미스 VNet의 가상 컴퓨터 집합을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-122">Figure 2 shows a set of virtual machines in a cross-premises VNet, which is connected to an on-premises network.</span></span>
  
<span data-ttu-id="17fe4-123">이 문서에 있는 [크로스-프레미스 VNet에 대 한 추가 계획 단계](designing-networking-for-microsoft-azure-iaas.md#cross_prem) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="17fe4-123">See the additional [Planning steps for a cross-premises VNet](designing-networking-for-microsoft-azure-iaas.md#cross_prem) section in this article.</span></span>
  
### <a name="step-4-determine-the-address-space-of-the-vnet"></a><span data-ttu-id="17fe4-124">4 단계: VNet의 주소 공간을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-124">Step 4: Determine the address space of the VNet.</span></span>

<span data-ttu-id="17fe4-125">표 1에는 다양 한 유형의 vnet에 대 한 주소 공간이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-125">Table 1 shows the address spaces for the different types of VNets.</span></span>
  
|<span data-ttu-id="17fe4-126">**VNet 유형**</span><span class="sxs-lookup"><span data-stu-id="17fe4-126">**Type of VNet**</span></span>|<span data-ttu-id="17fe4-127">**가상 네트워크 주소 공간**</span><span class="sxs-lookup"><span data-stu-id="17fe4-127">**Virtual network address space**</span></span>|
|:-----|:-----|
|<span data-ttu-id="17fe4-128">클라우드 전용</span><span class="sxs-lookup"><span data-stu-id="17fe4-128">Cloud-only</span></span>  <br/> |<span data-ttu-id="17fe4-129">임의의 개인 주소 공간</span><span class="sxs-lookup"><span data-stu-id="17fe4-129">Arbitrary private address space</span></span>  <br/> |
|<span data-ttu-id="17fe4-130">상호 연결 된 클라우드 전용</span><span class="sxs-lookup"><span data-stu-id="17fe4-130">Interconnected cloud-only</span></span>  <br/> |<span data-ttu-id="17fe4-131">임의 전용 이지만 연결 된 다른 vnet와 겹치지 않음</span><span class="sxs-lookup"><span data-stu-id="17fe4-131">Arbitrary private, but not overlapping with other connected VNets</span></span>  <br/> |
|<span data-ttu-id="17fe4-132">크로스-프레미스</span><span class="sxs-lookup"><span data-stu-id="17fe4-132">Cross-premises</span></span>  <br/> |<span data-ttu-id="17fe4-133">비공개, 온-프레미스와 겹치지 않음</span><span class="sxs-lookup"><span data-stu-id="17fe4-133">Private, but not overlapping with on-premises</span></span>  <br/> |
|<span data-ttu-id="17fe4-134">상호 연결 된 크로스-프레미스</span><span class="sxs-lookup"><span data-stu-id="17fe4-134">Interconnected cross-premises</span></span>  <br/> |<span data-ttu-id="17fe4-135">비공개, 온-프레미스 및 기타 연결 된 vnet와 겹치지 않음</span><span class="sxs-lookup"><span data-stu-id="17fe4-135">Private, but not overlapping with on-premises and other connected VNets</span></span>  <br/> |
   
 <span data-ttu-id="17fe4-136">**표 1: vnet의 유형 및 해당 하는 주소 공간**</span><span class="sxs-lookup"><span data-stu-id="17fe4-136">**Table 1: Types of VNets and their corresponding address space**</span></span>
  
<span data-ttu-id="17fe4-137">DHCP를 통해 서브넷의 주소 공간에서 가상 컴퓨터에 주소 구성이 할당 됩니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-137">Virtual machines are assigned an address configuration from the address space of the subnet by DHCP:</span></span>
  
- <span data-ttu-id="17fe4-138">주소/서브넷 마스크</span><span class="sxs-lookup"><span data-stu-id="17fe4-138">Address/subnet mask</span></span>
    
- <span data-ttu-id="17fe4-139">기본 게이트웨이</span><span class="sxs-lookup"><span data-stu-id="17fe4-139">Default gateway</span></span>
    
- <span data-ttu-id="17fe4-140">DNS 서버 IP 주소</span><span class="sxs-lookup"><span data-stu-id="17fe4-140">DNS server IP addresses</span></span>
    
<span data-ttu-id="17fe4-141">고정 IP 주소를 예약할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-141">You can also reserve a static IP address.</span></span>
  
<span data-ttu-id="17fe4-142">또한 가상 컴퓨터에는 개별적으로 또는 포함 하는 클라우드 서비스에서 공용 IP 주소를 할당할 수 있습니다 (클래식 배포 시스템에만 해당).</span><span class="sxs-lookup"><span data-stu-id="17fe4-142">Virtual machines can also be assigned a public IP address, either individually or from the containing cloud service (for classic deployment machines only).</span></span>
  
### <a name="step-5-determine-the-subnets-within-the-vnet-and-the-address-spaces-assigned-to-each"></a><span data-ttu-id="17fe4-143">5 단계: VNet 내의 서브넷과 각에 할당 된 주소 공간을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-143">Step 5: Determine the subnets within the VNet and the address spaces assigned to each.</span></span>

<span data-ttu-id="17fe4-144">VNet에는 게이트웨이 서브넷과 가상 컴퓨터 호스팅 서브넷의 두 가지 서브넷 유형이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-144">There are two types of subnets in a VNet, a gateway subnet and a virtual machine-hosting subnet.</span></span>
  
<span data-ttu-id="17fe4-145">**그림 3: Azure의 두 가지 서브넷 유형**</span><span class="sxs-lookup"><span data-stu-id="17fe4-145">**Figure 3: The two types of subnets in Azure**</span></span>

![그림 3: Azure의 두 가지 서브넷 유형](media/2eaa512d-1293-4e9b-b927-6bfe0fc0acb4.png)
  
<span data-ttu-id="17fe4-147">그림 3은 Azure 게이트웨이가 있는 게이트웨이 서브넷과 가상 컴퓨터를 포함 하는 가상 컴퓨터 호스팅 서브넷 집합을 포함 하는 VNet을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-147">Figure 3 shows a VNet containing a gateway subnet that has an Azure gateway and a set of virtual machine-hosting subnets containing virtual machines.</span></span>
  
<span data-ttu-id="17fe4-148">azure는 azure 게이트웨이 서브넷의 가상 컴퓨터 두 개를 호스트 하는 데 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-148">The Azure gateway subnet is needed by Azure to host the two virtual machines of your Azure gateway.</span></span> <span data-ttu-id="17fe4-149">최소 29 비트 접두사 길이를 사용 하 여 주소 공간을 지정 합니다 (예: 192.168.15.248/29).</span><span class="sxs-lookup"><span data-stu-id="17fe4-149">Specify an address space with at least a 29-bit prefix length (example: 192.168.15.248/29).</span></span> <span data-ttu-id="17fe4-150">특히 express를 사용할 계획인 경우 27 비트 또는 더 작은 접두사 길이를 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-150">A 27-bit or smaller prefix length is recommended, especially if you are planning to use ExpressRoute.</span></span>
  
<span data-ttu-id="17fe4-151">Azure 게이트웨이 서브넷의 주소 공간을 확인 하는 가장 좋은 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-151">A best practice for determining the address space of the Azure gateway subnet is:</span></span>
  
1. <span data-ttu-id="17fe4-152">게이트웨이 서브넷의 크기를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-152">Decide on the size of the gateway subnet.</span></span>
    
2. <span data-ttu-id="17fe4-153">VNet의 주소 공간에 있는 변수 비트에서 게이트웨이 서브넷에 사용 되는 비트를 0으로 설정 하 고 나머지 비트를 1로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-153">In the variable bits in the address space of the VNet, set the bits used for the gateway subnet to 0 and set the remaining bits to 1.</span></span>
    
3. <span data-ttu-id="17fe4-154">접두사 길이가 게이트웨이 서브넷 크기로 설정 된 주소 공간으로 10 진수 및 express로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-154">Convert to decimal and express as an address space with the prefix length set to the size of the gateway subnet.</span></span>
    
<span data-ttu-id="17fe4-155">이 방법을 사용 하는 경우 게이트웨이 서브넷의 주소 공간은 항상 VNet 주소 공간의 가장 끝에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-155">With this method, the address space for the gateway subnet is always at the farthest end of the VNet address space.</span></span>
  
<span data-ttu-id="17fe4-156">다음은 게이트웨이 서브넷의 주소 접두사를 정의 하는 예입니다. VNet의 주소 공간은 10.119.0.0/16입니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-156">Here is an example of defining the address prefix for the gateway subnet: The address space of the VNet is 10.119.0.0/16.</span></span> <span data-ttu-id="17fe4-157">조직에서는 처음에 사이트 간 VPN 연결을 사용 하지만 결국에는이를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-157">The organization will initially use a site-to-site VPN connection, but will eventually get ExpressRoute.</span></span> <span data-ttu-id="17fe4-158">표 2는 네트워크 접두사 표기법 (CIDR이 라고도 함)에서 게이트웨이 서브넷 주소 접두사를 확인 한 단계 및 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-158">Table 2 shows the steps and results of determining the gateway subnet address prefix in network prefix notation (also known as CIDR).</span></span>

<span data-ttu-id="17fe4-159">게이트웨이 서브넷 주소 접두사를 결정 하는 단계와 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-159">Here are the steps and example of determining the gateway subnet address prefix:</span></span>

1. <span data-ttu-id="17fe4-160">게이트웨이 서브넷의 크기를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-160">Decide on the size of the gateway subnet.</span></span> <span data-ttu-id="17fe4-161">이 예에서는/28을 선택 했습니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-161">For our example, we chose /28.</span></span>
2. <span data-ttu-id="17fe4-162">VNet 주소 공간 (b)의 변수 부분에 있는 비트를 G (게이트웨이 서브넷 비트)에 대해 0으로, 그렇지 않으면 1 (V)로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-162">Set the bits in the variable portion of the VNet address space (b) to 0 for the gateway subnet bits (G), otherwise 1 (V).</span></span> <span data-ttu-id="17fe4-163">이 예에서는 VNet에 대해 10.119.0.0/16 주소 공간을 사용 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-163">For our example, we are using the 10.119.0.0/16 address space for the VNet.</span></span>
<br/>
<br/><span data-ttu-id="17fe4-164">10.119</span><span class="sxs-lookup"><span data-stu-id="17fe4-164">10.119.</span></span> <span data-ttu-id="17fe4-165">bbbbbbbb</span><span class="sxs-lookup"><span data-stu-id="17fe4-165">bbbbbbbb .</span></span> <span data-ttu-id="17fe4-166">bbbbbbbb</span><span class="sxs-lookup"><span data-stu-id="17fe4-166">bbbbbbbb</span></span>
<br/><span data-ttu-id="17fe4-167">10.119</span><span class="sxs-lookup"><span data-stu-id="17fe4-167">10.119.</span></span> <span data-ttu-id="17fe4-168">vvvvvvv</span><span class="sxs-lookup"><span data-stu-id="17fe4-168">VVVVVVVV .</span></span> <span data-ttu-id="17fe4-169">VVVVGGGG</span><span class="sxs-lookup"><span data-stu-id="17fe4-169">VVVVGGGG</span></span>
<br/><span data-ttu-id="17fe4-170">10.119</span><span class="sxs-lookup"><span data-stu-id="17fe4-170">10.119.</span></span> <span data-ttu-id="17fe4-171">11111111</span><span class="sxs-lookup"><span data-stu-id="17fe4-171">11111111 .</span></span> <span data-ttu-id="17fe4-172">1111만</span><span class="sxs-lookup"><span data-stu-id="17fe4-172">11110000</span></span>
<br/><br/>
3. <span data-ttu-id="17fe4-173">2 단계에서 10 진수 및 express로 결과를 주소 공간으로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-173">Convert the result from step 2 to decimal and express as an address space.</span></span> <span data-ttu-id="17fe4-174">이 예에서는 10.119를 사용할 것입니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-174">For our example, 10.119.</span></span> <span data-ttu-id="17fe4-175">11111111</span><span class="sxs-lookup"><span data-stu-id="17fe4-175">11111111 .</span></span> <span data-ttu-id="17fe4-176">1111만은 10.119.255.240이 고 1 단계의 접두사 길이를 포함 하 여, 결과 게이트웨이 서브넷 주소 접두사는 10.119.255.240/28입니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-176">11110000 is 10.119.255.240, and with the prefix length from step 1, (28 in our example), the resulting gateway subnet address prefix is 10.119.255.240/28.</span></span>
  
<span data-ttu-id="17fe4-177">자세한 내용은 [Azure 게이트웨이 서브넷의 주소 공간 계산기](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="17fe4-177">See [Address space calculator for Azure gateway subnets](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) for more information.</span></span>
  
<span data-ttu-id="17fe4-178">가상 컴퓨터 호스팅 서브넷은 응용 프로그램의 공통 역할 또는 계층, 즉 서브넷 격리와 같은 일반적인 온-프레미스 지침에 따라 수행할 수 있는 Azure 가상 컴퓨터를 배치 하는 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-178">Virtual machine-hosting subnets are where you place Azure virtual machines, which you can do according to typical on-premises guidelines, such as a common role or tier of an application or for subnet isolation.</span></span>
  
<span data-ttu-id="17fe4-179">Azure에서는 각 서브넷에서 처음 3 개의 주소를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-179">Azure uses the first 3 addresses on each subnet.</span></span> <span data-ttu-id="17fe4-180">따라서 Azure 서브넷에서 가능한 주소 수는 2<sup>n</sup> -5 이며 여기에서 n은 호스트 비트의 수입니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-180">Therefore, the number of possible addresses on an Azure subnet is 2<sup>n</sup> - 5, where n is the number of host bits.</span></span> <span data-ttu-id="17fe4-181">표 3에서는 필요한 가상 컴퓨터의 범위, 필요한 호스트 수 및 해당 서브넷 크기를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-181">Table 3 shows the range of virtual machines required, the number of hosts bits needed, and the corresponding subnet size.</span></span>
  
|<span data-ttu-id="17fe4-182">**필요한 가상 컴퓨터**</span><span class="sxs-lookup"><span data-stu-id="17fe4-182">**Virtual machines required**</span></span>|<span data-ttu-id="17fe4-183">**호스트 비트**</span><span class="sxs-lookup"><span data-stu-id="17fe4-183">**Host bits**</span></span>|<span data-ttu-id="17fe4-184">**서브넷 크기**</span><span class="sxs-lookup"><span data-stu-id="17fe4-184">**Subnet size**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="17fe4-185">1-3</span><span class="sxs-lookup"><span data-stu-id="17fe4-185">1-3</span></span>  <br/> |<span data-ttu-id="17fe4-186">3(sp3)</span><span class="sxs-lookup"><span data-stu-id="17fe4-186">3</span></span>  <br/> |<span data-ttu-id="17fe4-187">/29</span><span class="sxs-lookup"><span data-stu-id="17fe4-187">/29</span></span>  <br/> |
|<span data-ttu-id="17fe4-188">4-11</span><span class="sxs-lookup"><span data-stu-id="17fe4-188">4-11</span></span>  <br/> |<span data-ttu-id="17fe4-189">1-4</span><span class="sxs-lookup"><span data-stu-id="17fe4-189">4</span></span>  <br/> |<span data-ttu-id="17fe4-190">/28</span><span class="sxs-lookup"><span data-stu-id="17fe4-190">/28</span></span>  <br/> |
|<span data-ttu-id="17fe4-191">12-27</span><span class="sxs-lookup"><span data-stu-id="17fe4-191">12-27</span></span>  <br/> |<span data-ttu-id="17fe4-192">2-5</span><span class="sxs-lookup"><span data-stu-id="17fe4-192">5</span></span>  <br/> |<span data-ttu-id="17fe4-193">/27</span><span class="sxs-lookup"><span data-stu-id="17fe4-193">/27</span></span>  <br/> |
|<span data-ttu-id="17fe4-194">28-59</span><span class="sxs-lookup"><span data-stu-id="17fe4-194">28-59</span></span>  <br/> |<span data-ttu-id="17fe4-195">번</span><span class="sxs-lookup"><span data-stu-id="17fe4-195">6</span></span>  <br/> |<span data-ttu-id="17fe4-196">/26</span><span class="sxs-lookup"><span data-stu-id="17fe4-196">/26</span></span>  <br/> |
|<span data-ttu-id="17fe4-197">60-123</span><span class="sxs-lookup"><span data-stu-id="17fe4-197">60-123</span></span>  <br/> |<span data-ttu-id="17fe4-198">연중</span><span class="sxs-lookup"><span data-stu-id="17fe4-198">7</span></span>  <br/> |<span data-ttu-id="17fe4-199">/25</span><span class="sxs-lookup"><span data-stu-id="17fe4-199">/25</span></span>  <br/> |
   
 <span data-ttu-id="17fe4-200">**표 3: 가상 컴퓨터 요구 사항 및 해당 서브넷 크기**</span><span class="sxs-lookup"><span data-stu-id="17fe4-200">**Table 3: Virtual machine requirements and their subnet sizes**</span></span>
  
<span data-ttu-id="17fe4-201">서브넷 또는 VNet에 있는 가상 컴퓨터의 최대 크기에 대 한 자세한 내용은 [네트워킹 제한을](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits)참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="17fe4-201">For more information about the maximum amount of virtual machines on a subnet or VNet, see [Networking Limits](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits).</span></span>
  
<span data-ttu-id="17fe4-202">자세한 내용은 [Azure Virtual network 계획 및 디자인](https://azure.microsoft.com/documentation/articles/virtual-network-vnet-plan-design-arm/)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="17fe4-202">For more information, see [Plan and design Azure Virtual Networks](https://azure.microsoft.com/documentation/articles/virtual-network-vnet-plan-design-arm/).</span></span>
  
### <a name="step-6-determine-the-dns-server-configuration-and-the-addresses-of-the-dns-servers-to-assign-to-vms-in-the-vnet"></a><span data-ttu-id="17fe4-203">6 단계: VNet의 vm에 할당할 dns 서버의 주소와 dns 서버 구성을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-203">Step 6: Determine the DNS server configuration and the addresses of the DNS servers to assign to VMs in the VNet.</span></span>

<span data-ttu-id="17fe4-204">Azure는 가상 컴퓨터에 DHCP를 통해 DNS 서버의 주소를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-204">Azure assigns virtual machines the addresses of DNS servers by DHCP.</span></span> <span data-ttu-id="17fe4-205">DNS 서버는 다음이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-205">DNS servers can be:</span></span>
  
- <span data-ttu-id="17fe4-206">Azure에서 제공: 로컬 이름 등록 및 로컬 및 인터넷 이름 확인을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-206">Supplied by Azure: Provides local name registration and local and Internet name resolution</span></span>
    
- <span data-ttu-id="17fe4-207">제공: 로컬 또는 인트라넷 이름 등록 및 인트라넷 또는 인터넷 이름 확인을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-207">Provided by you: Provides local or intranet name registration and either intranet or Internet name resolution</span></span>
    
<span data-ttu-id="17fe4-208">표 4에서는 각 VNet 유형에 대 한 DNS 서버의 다양 한 구성을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-208">Table 4 shows the different configurations of DNS servers for each type of VNet.</span></span>
    
|<span data-ttu-id="17fe4-209">**VNet 유형**</span><span class="sxs-lookup"><span data-stu-id="17fe4-209">**Type of VNet**</span></span>|<span data-ttu-id="17fe4-210">**DNS 서버**</span><span class="sxs-lookup"><span data-stu-id="17fe4-210">**DNS server**</span></span>|
|:-----|:-----|
|<span data-ttu-id="17fe4-211">클라우드 전용</span><span class="sxs-lookup"><span data-stu-id="17fe4-211">Cloud-only</span></span>  <br/> |<span data-ttu-id="17fe4-212">Azure-로컬 및 인터넷 이름 확인에 대해 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-212">Azure-supplied for local and Internet name resolution</span></span>  <br/> <span data-ttu-id="17fe4-213">로컬 및 인터넷 이름 확인을 위한 Azure 가상 컴퓨터 (DNS 전달)</span><span class="sxs-lookup"><span data-stu-id="17fe4-213">Azure virtual machine for local and Internet name resolution (DNS forwarding)</span></span>  <br/> |
|<span data-ttu-id="17fe4-214">크로스-프레미스</span><span class="sxs-lookup"><span data-stu-id="17fe4-214">Cross-premises</span></span>  <br/> |<span data-ttu-id="17fe4-215">로컬 및 인트라넷 이름 확인을 위해 온-프레미스</span><span class="sxs-lookup"><span data-stu-id="17fe4-215">On-premises for local and intranet name resolution</span></span>  <br/> <span data-ttu-id="17fe4-216">로컬 및 인트라넷 이름 확인에 대 한 Azure 가상 컴퓨터 (DNS 복제 및 전달)</span><span class="sxs-lookup"><span data-stu-id="17fe4-216">Azure virtual machine for local and intranet name resolution (DNS replication and forwarding)</span></span>  <br/> |
   
 <span data-ttu-id="17fe4-217">**표 4: 서로 다른 두 가지 유형의 vnet DNS 서버 옵션**</span><span class="sxs-lookup"><span data-stu-id="17fe4-217">**Table 4: DNS server options for the two different types of VNets**</span></span>
  
<span data-ttu-id="17fe4-218">자세한 내용은 [vm 및 역할 인스턴스에 대 한 이름 확인](https://docs.microsoft.com/azure/virtual-network/virtual-networks-name-resolution-for-vms-and-role-instances)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="17fe4-218">For more information, see [Name Resolution for VMs and Role Instances](https://docs.microsoft.com/azure/virtual-network/virtual-networks-name-resolution-for-vms-and-role-instances).</span></span>
  
### <a name="step-7-determine-the-load-balancing-configuration-internet-facing-or-internal"></a><span data-ttu-id="17fe4-219">7 단계: 부하 분산 구성 (인터넷 연결 또는 내부)을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-219">Step 7: Determine the load balancing configuration (Internet-facing or internal).</span></span>

<span data-ttu-id="17fe4-220">경우에 따라 같은 역할을 가진 서버 집합에 들어오는 트래픽을 분산 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-220">In some cases, you want to distribute incoming traffic to a set of servers that have the same role.</span></span> <span data-ttu-id="17fe4-221">Azure IaaS에는 인터넷 연결 및 내부 트래픽 부하에 대해이 작업을 수행 하기 위한 기본 제공 기능이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-221">Azure IaaS has a built-in facility to do this for Internet-facing and internal traffic loads.</span></span>
  
<span data-ttu-id="17fe4-222">Azure 인터넷 연결 부하 분산은 원치 않는 들어오는 트래픽을 인터넷에서 부하 분산 된 집합의 구성원으로 임의로 분산 합니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-222">Azure Internet-facing load balancing randomly distributes unsolicited incoming traffic from the Internet to the members of a load-balanced set.</span></span>
  
<span data-ttu-id="17fe4-223">**그림 4: Azure의 외부 부하 분산 장치**</span><span class="sxs-lookup"><span data-stu-id="17fe4-223">**Figure 4: An external load balancer in Azure**</span></span>

![그림 4: Azure의 외부 부하 분산 장치](media/eb5945e5-0c2b-40f1-b9ed-54bb2b0f9e59.png)
  
<span data-ttu-id="17fe4-225">그림 4에서는 인바운드 NAT 규칙 또는 끝점에 들어오는 트래픽을 부하 분산 집합에 있는 가상 컴퓨터 집합에 분산 하는 Azure의 외부 부하 분산 장치를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-225">Figure 4 shows an external load balancer in Azure that distributes incoming traffic on an inbound NAT rule or endpoint to a set of virtual machines in a load-balanced set.</span></span>
  
<span data-ttu-id="17fe4-226">Azure 내부 부하 분산은 다른 Azure vm 또는 인트라넷 컴퓨터에서 들어오는 원치 않는 트래픽을 부하 분산 된 집합의 구성원으로 임의로 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-226">Azure internal load balancing randomly distributes unsolicited incoming traffic from other Azure VMs or from intranet computers to the members of a load-balanced set.</span></span> 
  
<span data-ttu-id="17fe4-227">**그림 5: Azure의 내부 부하 분산 장치**</span><span class="sxs-lookup"><span data-stu-id="17fe4-227">**Figure 5: An internal load balancer in Azure**</span></span>

![그림 5: Azure의 내부 부하 분산 장치](media/d1451b73-6465-449d-b3e6-22160ce51f35.png)
  
<span data-ttu-id="17fe4-229">그림 5에서는 인바운드 NAT 규칙 또는 끝점에 들어오는 트래픽을 부하 분산 집합에 있는 가상 컴퓨터 집합에 분산 하는 Azure의 내부 부하 분산 장치를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-229">Figure 5 shows an internal load balancer in Azure that distributes incoming traffic on an inbound NAT rule or endpoint to a set of virtual machines in a load-balanced set.</span></span>
  
<span data-ttu-id="17fe4-230">자세한 내용은 [Azure 부하 분산 장치](https://docs.microsoft.com/azure/load-balancer/load-balancer-overview)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="17fe4-230">For more information, see [Azure Load Balancer](https://docs.microsoft.com/azure/load-balancer/load-balancer-overview).</span></span>
  
### <a name="step-8-determine-the-use-of-virtual-appliances-and-user-defined-routes"></a><span data-ttu-id="17fe4-231">8 단계: 가상 어플라이언스 및 사용자 정의 경로 사용을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-231">Step 8: Determine the use of virtual appliances and user-defined routes.</span></span>

<span data-ttu-id="17fe4-232">VNet의 가상 기기로 트래픽을 전달 해야 하는 경우에는 하나 이상의 사용자 정의 경로를 서브넷에 추가 해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-232">If you need to forward traffic to virtual appliances in your VNet, you may need to add one or more user-defined routes to a subnet.</span></span>
  
<span data-ttu-id="17fe4-233">**그림 6: Azure의 가상 어플라이언스 및 사용자 정의 경로**</span><span class="sxs-lookup"><span data-stu-id="17fe4-233">**Figure 6: Virtual appliances and user-defined routes in Azure**</span></span>

![그림 6: Azure의 가상 어플라이언스 및 사용자 정의 경로](media/f181d0f4-ebf9-439e-9c98-dec17428c32b.png)
  
<span data-ttu-id="17fe4-235">그림 6에서는 가상 어플라이언스를 가리키는 가상 컴퓨터 호스팅 서브넷에 할당 되는 크로스-프레미스 VNet 및 사용자 정의 경로를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-235">Figure 6 shows a cross-premises VNet and a user-defined route assigned to a virtual machine-hosting subnet that points to a virtual appliance.</span></span>
  
<span data-ttu-id="17fe4-236">자세한 내용은 [사용자 정의 경로 및 IP 전달을](https://docs.microsoft.com/azure/virtual-network/virtual-networks-udr-overview)참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="17fe4-236">For more information, see [User Defined Routes and IP Forwarding](https://docs.microsoft.com/azure/virtual-network/virtual-networks-udr-overview).</span></span>
  
### <a name="step-9-determine-how-computers-from-the-internet-will-connect-to-virtual-machines"></a><span data-ttu-id="17fe4-237">9 단계: 인터넷의 컴퓨터가 가상 컴퓨터에 연결 하는 방법을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-237">Step 9: Determine how computers from the Internet will connect to virtual machines.</span></span>

<span data-ttu-id="17fe4-238">VNet의 가상 컴퓨터에 대 한 인터넷 액세스를 제공 하는 방법에는 여러 가지가 있으며, 프록시 서버나 기타에 지 장치를 통해 조직 네트워크에 대 한 액세스를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-238">There are multiple ways to provide Internet access to the virtual machines on a VNet, which includes access from your organization network through your proxy server or other edge device.</span></span>
  
<span data-ttu-id="17fe4-239">표 5에는 원치 않는 들어오는 트래픽을 필터링 하거나 검사 하는 방법이 나열 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-239">Table 5 lists the methods for filtering or inspecting unsolicited incoming traffic.</span></span>
  
|<span data-ttu-id="17fe4-240">**방법**</span><span class="sxs-lookup"><span data-stu-id="17fe4-240">**Method**</span></span>|<span data-ttu-id="17fe4-241">**배포 모델**</span><span class="sxs-lookup"><span data-stu-id="17fe4-241">**Deployment model**</span></span>|
|:-----|:-----|
|<span data-ttu-id="17fe4-242">1. 클라우드 서비스에 구성 된 끝점 및 acl</span><span class="sxs-lookup"><span data-stu-id="17fe4-242">1. Endpoints and ACLs configured on cloud services</span></span>  <br/> |<span data-ttu-id="17fe4-243">기존</span><span class="sxs-lookup"><span data-stu-id="17fe4-243">Classic</span></span>  <br/> |
|<span data-ttu-id="17fe4-244">2. 네트워크 보안 그룹</span><span class="sxs-lookup"><span data-stu-id="17fe4-244">2. Network security groups</span></span>  <br/> |<span data-ttu-id="17fe4-245">자원 관리자 및 클래식</span><span class="sxs-lookup"><span data-stu-id="17fe4-245">Resource Manager and classic</span></span>  <br/> |
|<span data-ttu-id="17fe4-246">3. 인바운드 NAT 규칙을 사용 하는 인터넷 연결 부하 분산 장치</span><span class="sxs-lookup"><span data-stu-id="17fe4-246">3. Internet-facing load balancer with inbound NAT rules</span></span>  <br/> |<span data-ttu-id="17fe4-247">자원 관리자</span><span class="sxs-lookup"><span data-stu-id="17fe4-247">Resource Manager</span></span>  <br/> |
|<span data-ttu-id="17fe4-248">4. Azure Marketplace의 네트워크 보안 어플라이언스 (표시 되지 않음)</span><span class="sxs-lookup"><span data-stu-id="17fe4-248">4. Network security appliances in the Azure Marketplace (not shown)</span></span>  <br/> |<span data-ttu-id="17fe4-249">자원 관리자 및 클래식</span><span class="sxs-lookup"><span data-stu-id="17fe4-249">Resource Manager and classic</span></span>  <br/> |
   
 <span data-ttu-id="17fe4-250">**표 5: 가상 컴퓨터 및 해당 Azure 배포 모델에 연결 하는 방법**</span><span class="sxs-lookup"><span data-stu-id="17fe4-250">**Table 5: Methods of connecting to virtual machines and their corresponding Azure deployment models**</span></span>
  
<span data-ttu-id="17fe4-251">**그림 7: 인터넷을 통한 Azure 가상 컴퓨터에 연결**</span><span class="sxs-lookup"><span data-stu-id="17fe4-251">**Figure 7: Connecting to Azure virtual machines over the Internet**</span></span>

![그림 7: 인터넷을 통한 Azure 가상 컴퓨터에 연결](media/c5e3531b-170a-4482-a6ff-fb8fbbe81b35.png)
  
<span data-ttu-id="17fe4-253">그림 7은 끝점, 네트워크 보안 그룹을 사용 하는 서브넷의 가상 컴퓨터 및 외부 부하 분산 장치 및 인바운드 NAT 규칙을 사용 하 여 서브넷의 가상 컴퓨터를 사용 하 여 클라우드 서비스의 가상 컴퓨터에 연결 하는 인터넷 연결 컴퓨터를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-253">Figure 7 shows an Internet-connected computer connecting to a virtual machine in a cloud service using an endpoint, a virtual machine on a subnet using a network security group, and a virtual machine on a subnet using an external load balancer and inbound NAT rules.</span></span>
  
<span data-ttu-id="17fe4-254">추가 보안은 다음에 의해 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-254">Additional security is provided by:</span></span>
  
- <span data-ttu-id="17fe4-255">원격 데스크톱 및 SSH 연결 (인증 및 암호화 됨)</span><span class="sxs-lookup"><span data-stu-id="17fe4-255">Remote Desktop and SSH connections, which are authenticated and encrypted.</span></span>
    
- <span data-ttu-id="17fe4-256">원격 PowerShell 세션 (인증 및 암호화 됨)</span><span class="sxs-lookup"><span data-stu-id="17fe4-256">Remote PowerShell sessions, which are authenticated and encrypted.</span></span>
    
- <span data-ttu-id="17fe4-257">IPsec 전송 모드-종단 간 암호화에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-257">IPsec transport mode, which you can use for end-to-end encryption.</span></span>
    
- <span data-ttu-id="17fe4-258">외부 및 내부 공격을 방지 하는 Azure DDOS protection</span><span class="sxs-lookup"><span data-stu-id="17fe4-258">Azure DDOS protection, which helps prevent external and internal attacks</span></span>
    
<span data-ttu-id="17fe4-259">자세한 내용은 [Microsoft Cloud Security for Enterprise 설계자](https://aka.ms/cloudarchsecurity) 및 [Azure Network Security](https://azure.microsoft.com/blog/azure-network-security/)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="17fe4-259">For more information, see [Microsoft Cloud Security for Enterprise Architects](https://aka.ms/cloudarchsecurity) and [Azure Network Security](https://azure.microsoft.com/blog/azure-network-security/).</span></span>
  
### <a name="step-10-for-multiple-vnets-determine-the-vnet-to-vnet-connection-topology"></a><span data-ttu-id="17fe4-260">10 단계: 여러 vnet에 대해 vnet-vnet 연결 토폴로지를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-260">Step 10: For multiple VNets, determine the VNet-to-VNet connection topology.</span></span>

<span data-ttu-id="17fe4-261">조직의 사이트를 연결 하는 데 사용 되는 것과 비슷한 토폴로지를 사용 하 여 vnet를 서로 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-261">VNets can be connected to each other using topologies similar to those used for connecting the sites of an organization.</span></span>
  
<span data-ttu-id="17fe4-262">데이지 체인 구성은 일련의 vnet 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-262">A daisy chain configuration connects the VNets in a series.</span></span>
  
<span data-ttu-id="17fe4-263">**그림 8: vnet에 대 한 데이지 체인 구성**</span><span class="sxs-lookup"><span data-stu-id="17fe4-263">**Figure 8: A daisy-chained configuration for VNets**</span></span>

![그림 8: Azure 가상 네트워크에 대 한 데이지 체인 구성](media/264d5dd4-06c5-483f-9428-a18cc1f68ac1.png)
  
<span data-ttu-id="17fe4-265">그림 8은 데이지 체인 구성을 사용 하 여 시리즈에 연결 된 5 개의 vnet를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-265">Figure 8 shows five VNets connected in series using a daisy-chained configuration.</span></span>
  
<span data-ttu-id="17fe4-266">스포크 및 허브 구성은 서로 연결 되어 있는 중앙 vnet 집합에 여러 vnet를 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-266">A spoke and hub configuration connects multiple VNets to a set of central VNets, which are themselves connected to each other.</span></span>
  
<span data-ttu-id="17fe4-267">**그림 9: vnet에 대 한 스포크 및 허브 구성**</span><span class="sxs-lookup"><span data-stu-id="17fe4-267">**Figure 9: A spoke and hub configuration for VNets**</span></span>

![그림 9: Azure 가상 네트워크에 대 한 스포크 및 허브 구성](media/dd442a38-5b76-4ac5-b743-8fc7711a91ba.png)
  
<span data-ttu-id="17fe4-269">그림 9에서는 여섯 개의 vnet, 두 vnet는 서로 연결 되는 허브, 그리고 다른 두 spoke vnet를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-269">Figure 9 shows six VNets, two VNets are hubs that are connected to each other and also two other spoke VNets.</span></span>
  
<span data-ttu-id="17fe4-270">전체 메시 구성은 모든 VNet을 서로 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-270">A full mesh configuration connects every VNet to each other.</span></span>
  
<span data-ttu-id="17fe4-271">**그림 10: vnet에 대 한 풀 메시 구성**</span><span class="sxs-lookup"><span data-stu-id="17fe4-271">**Figure 10: A full mesh configuration for VNets**</span></span>

![그림 10: Azure 가상 네트워크에 대 한 메시 구성](media/9dda0738-10db-4a63-95b3-79851a399b71.png)
  
<span data-ttu-id="17fe4-273">그림 10은 총 6 개의 vnet-vnet 연결을 사용 하 여 서로 연결 된 네 가지 vnet를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-273">Figure 10 shows four VNets that are all connected to each other, using a total of six VNet-to-VNet connections.</span></span>
  
## <a name="planning-steps-for-a-cross-premises-vnet"></a><span data-ttu-id="17fe4-274">크로스-프레미스 VNet에 대 한 계획 단계</span><span class="sxs-lookup"><span data-stu-id="17fe4-274">Planning steps for a cross-premises VNet</span></span>
<span data-ttu-id="17fe4-275"><a name="cross_prem"> </a></span><span class="sxs-lookup"><span data-stu-id="17fe4-275"></span></span>

<span data-ttu-id="17fe4-276">크로스-프레미스 VNet에 대해 다음 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-276">Follow these steps for a cross-premises VNet.</span></span>
  
> [!TIP]
> <span data-ttu-id="17fe4-277">시뮬레이션 된 크로스-프레미스 개발/테스트 환경을 만들려면 [Azure에서 시뮬레이트된 크로스-프레미스 가상 네트워크](simulated-cross-premises-virtual-network-in-azure.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="17fe4-277">To create a simulated cross-premises dev/test environment, see [Simulated cross-premises virtual network in Azure](simulated-cross-premises-virtual-network-in-azure.md).</span></span> 
  
### <a name="step-1-determine-the-cross-premises-connection-to-the-vnet-s2s-vpn-or-expressroute"></a><span data-ttu-id="17fe4-278">1 단계: VNet (S2S VPN 또는 express)에 대 한 크로스-프레미스 연결을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-278">Step 1: Determine the cross-premises connection to the VNet (S2S VPN or ExpressRoute).</span></span>

<span data-ttu-id="17fe4-279">표 6에는 다양 한 유형의 연결이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-279">Table 6 lists the different types of connections.</span></span>
  
|<span data-ttu-id="17fe4-280">**연결 유형**</span><span class="sxs-lookup"><span data-stu-id="17fe4-280">**Type of connection**</span></span>|<span data-ttu-id="17fe4-281">**용도**</span><span class="sxs-lookup"><span data-stu-id="17fe4-281">**Purpose**</span></span>|
|:-----|:-----|
|<span data-ttu-id="17fe4-282">S2S (사이트 간) VPN</span><span class="sxs-lookup"><span data-stu-id="17fe4-282">Site-to-Site (S2S) VPN</span></span>  <br/> |<span data-ttu-id="17fe4-283">1-10 사이트 (다른 vnet 포함)를 단일 VNet에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-283">Connect 1-10 sites (including other VNets) to a single VNet.</span></span>  <br/> |
|<span data-ttu-id="17fe4-284">ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="17fe4-284">ExpressRoute</span></span>  <br/> |<span data-ttu-id="17fe4-285">IXP (인터넷 Exchange 공급자) 또는 NSP (네트워크 서비스 공급자)를 통해 Azure에 대 한 안전한 사설 링크입니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-285">A private, secure link to Azure via an Internet Exchange Provider (IXP) or a Network Service Provider (NSP).</span></span>  <br/> |
|<span data-ttu-id="17fe4-286">지점 간 (P2S) VPN</span><span class="sxs-lookup"><span data-stu-id="17fe4-286">Point-to-Site (P2S) VPN</span></span>  <br/> |<span data-ttu-id="17fe4-287">단일 컴퓨터를 VNet에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-287">Connects a single computer to a VNet.</span></span>  <br/> |
|<span data-ttu-id="17fe4-288">vnet 피어 링 또는 vnet-vnet (V2V) VPN</span><span class="sxs-lookup"><span data-stu-id="17fe4-288">VNet peering or VNet-to-VNet (V2V) VPN</span></span>  <br/> |<span data-ttu-id="17fe4-289">vnet을 다른 VNet에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-289">Connects a VNet to another VNet.</span></span>  <br/> |
   
 <span data-ttu-id="17fe4-290">**표 6: 크로스-프레미스 vnet 연결 유형**</span><span class="sxs-lookup"><span data-stu-id="17fe4-290">**Table 6: The types of connections for cross-premises VNets**</span></span>
  
<span data-ttu-id="17fe4-291">최대 연결 수에 대 한 자세한 내용은 [네트워킹 제한을](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits)참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="17fe4-291">For more information on the maximum number of connections, see [Networking Limits](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits).</span></span>
  
<span data-ttu-id="17fe4-292">vpn 장치에 대 한 자세한 내용은 [사이트 간 가상 네트워크 연결에 대 한 vpn 장치](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="17fe4-292">For more information about VPN devices, see [VPN devices for site-to-site virtual network connections](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).</span></span>
  
<span data-ttu-id="17fe4-293">vnet 피어 링에 대 한 자세한 내용은 [vnet 피어 링](https://docs.microsoft.com/azure/virtual-network/virtual-network-peering-overview)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="17fe4-293">For more information about VNet peering, see [VNet peering](https://docs.microsoft.com/azure/virtual-network/virtual-network-peering-overview).</span></span>
  
<span data-ttu-id="17fe4-294">**그림 11: 크로스-프레미스 VNet에 연결 하는 네 가지 방법**</span><span class="sxs-lookup"><span data-stu-id="17fe4-294">**Figure 11: The four ways to connect to a cross-premises VNet**</span></span>

![그림 11: 크로스-프레미스 Azure virtual network에 연결 하는 세 가지 방법](media/d5d4a625-cfbd-4a77-9159-eaca69d07e93.png)
  
<span data-ttu-id="17fe4-296">그림 11은 컴퓨터의 P2S 연결, 온-프레미스 네트워크의 S2S VPN 연결, 온-프레미스 네트워크 로부터의 간 연결, 다른 vnet에서의 vnet-vnet 연결과 같은 네 가지 유형의 연결이 포함 된 VNet을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-296">Figure 11 shows a VNet with the four types of connections: a P2S connection from a computer, an S2S VPN connection from an on-premises network, an ExpressRoute connection from an on-premises network, and a VNet-to-VNet connection from another VNet.</span></span> 
  
<span data-ttu-id="17fe4-297">다음과 같은 방법으로 VNet의 vm에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-297">You can connect to VMs in a VNet in the following ways:</span></span>
  
- <span data-ttu-id="17fe4-298">온-프레미스 네트워크 또는 인터넷에서 VNet vm 관리</span><span class="sxs-lookup"><span data-stu-id="17fe4-298">Administration of VNet VMs from your on-premises network or the Internet</span></span>
    
- <span data-ttu-id="17fe4-299">온-프레미스 네트워크에서의 IT 워크 로드 액세스</span><span class="sxs-lookup"><span data-stu-id="17fe4-299">IT workload access from your on-premises network</span></span>
    
- <span data-ttu-id="17fe4-300">추가 vnet를 통한 네트워크 확장</span><span class="sxs-lookup"><span data-stu-id="17fe4-300">Extension of your network through additional VNets</span></span>
    
<span data-ttu-id="17fe4-301">연결에 대 한 보안은 다음을 통해 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-301">Security for connections is provided by the following:</span></span>
  
- <span data-ttu-id="17fe4-302">P2S는 SSTP (Secure Socket Tunneling Protocol)를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-302">P2S uses the Secure Socket Tunneling Protocol (SSTP)</span></span> 
    
- <span data-ttu-id="17fe4-303">S2S 및 vnet과 vnet 간 VPN 연결에서는 AES256과 함께 IPsec 터널 모드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-303">S2S and VNet-to-VNet VPN connections use IPsec tunnel mode with AES256</span></span>
    
- <span data-ttu-id="17fe4-304">express는 사설 WAN 연결</span><span class="sxs-lookup"><span data-stu-id="17fe4-304">ExpressRoute is a private WAN connection</span></span>
    
<span data-ttu-id="17fe4-305">자세한 내용은 [Microsoft Cloud Security for Enterprise 설계자](https://aka.ms/cloudarchsecurity) 및 [Azure Network Security](https://azure.microsoft.com/blog/azure-network-security/)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="17fe4-305">For more information, see [Microsoft Cloud Security for Enterprise Architects](https://aka.ms/cloudarchsecurity) and [Azure Network Security](https://azure.microsoft.com/blog/azure-network-security/).</span></span>
  
### <a name="step-2-determine-the-on-premises-vpn-device-or-router"></a><span data-ttu-id="17fe4-306">2 단계: 온-프레미스 VPN 장치 또는 라우터를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-306">Step 2: Determine the on-premises VPN device or router.</span></span>

<span data-ttu-id="17fe4-307">온-프레미스 VPN 장치 또는 라우터는 다음과 같이 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-307">Your on-premises VPN device or router acts as:</span></span>
  
- <span data-ttu-id="17fe4-308">IPsec 피어-Azure 게이트웨이에서 S2S VPN 연결을 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-308">An IPsec peer, terminating the S2S VPN connection from the Azure gateway.</span></span>
    
- <span data-ttu-id="17fe4-309">개인 피어 링 express 연결에 대 한 bpg 피어 및 종료 지점입니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-309">The BPG peer and termination point for the private peering ExpressRoute connection.</span></span>
    
<span data-ttu-id="17fe4-310">**그림 12: 온-프레미스 VPN 라우터 또는 장치**</span><span class="sxs-lookup"><span data-stu-id="17fe4-310">**Figure 12: The on-premises VPN router or device**</span></span>

![그림 12: 온-프레미스 VPN 라우터 또는 장치](media/bd221468-a660-4730-aa55-0426986480b9.png)
  
<span data-ttu-id="17fe4-312">그림 12에서는 온-프레미스 VPN 라우터 또는 장치에 연결 된 크로스-프레미스 VNet을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-312">Figure 12 shows a cross-premises VNet connected to an on-premises VPN router or device.</span></span>
  
<span data-ttu-id="17fe4-313">자세한 내용은 [About VPN gateway](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="17fe4-313">For more information, see [About VPN gateway](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways).</span></span>
  
### <a name="step-3-add-routes-to-your-intranet-to-make-the-address-space-of-the-vnet-reachable"></a><span data-ttu-id="17fe4-314">3 단계: 인트라넷에 경로를 추가 하 여 VNet의 주소 공간에 연결할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-314">Step 3: Add routes to your intranet to make the address space of the VNet reachable.</span></span>

<span data-ttu-id="17fe4-315">온-프레미스에서 vnet로의 라우팅은 다음으로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-315">Routing to VNets from on-premises consists of the following:</span></span>
  
1. <span data-ttu-id="17fe4-316">VPN 장치를 가리키는 VNet 주소 공간에 대 한 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-316">A route for the VNet address space that points toward your VPN device.</span></span>
    
2. <span data-ttu-id="17fe4-317">vpn 장치에서 S2S VPN 또는 express 연결을 가리키는 VNet 주소 공간에 대 한 경로</span><span class="sxs-lookup"><span data-stu-id="17fe4-317">A route for the VNet address space on your VPN device that points across the S2S VPN or ExpressRoute connection</span></span>
    
<span data-ttu-id="17fe4-318">**그림 13: VNet에 연결할 수 있도록 하는 데 필요한 온-프레미스 경로**</span><span class="sxs-lookup"><span data-stu-id="17fe4-318">**Figure 13: The on-premises routes needed to make a VNet reachable**</span></span>

![그림 13: Azure VNet에 연결할 수 있도록 설정 하는 데 필요한 온-프레미스 경로](media/7a1e20c1-fbc4-4cb9-9961-735da4e23307.png)
  
<span data-ttu-id="17fe4-320">그림 13은 온-프레미스 라우터에서 필요한 라우팅 정보 및 VNet의 주소 공간을 나타내는 VPN 라우터 또는 장치를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-320">Figure 13 shows the routing information needed by the on-premises routers and the VPN router or device that represents the address space of the VNet.</span></span>
  
### <a name="step-4-for-expressroute-plan-for-the-new-connection-with-your-provider"></a><span data-ttu-id="17fe4-321">4 단계: express에서 공급자와의 새 연결을 계획 합니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-321">Step 4: For ExpressRoute, plan for the new connection with your provider.</span></span>

<span data-ttu-id="17fe4-322">온-프레미스 네트워크와 Microsoft 클라우드 사이에는 다음과 같은 세 가지 방법으로 개인 피어 링을 통한 간 연결을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-322">You can create an ExpressRoute connection with private peering between your on-premises network and the Microsoft cloud in three different ways:</span></span>
  
- <span data-ttu-id="17fe4-323">클라우드 exchange에 배치</span><span class="sxs-lookup"><span data-stu-id="17fe4-323">Co-located at a cloud exchange</span></span>
    
- <span data-ttu-id="17fe4-324">지점 간 이더넷 연결</span><span class="sxs-lookup"><span data-stu-id="17fe4-324">Point-to-point Ethernet connections</span></span>
    
- <span data-ttu-id="17fe4-325">임의 (IP VPN) 네트워크</span><span class="sxs-lookup"><span data-stu-id="17fe4-325">Any-to-any (IP VPN) networks</span></span>
    
<span data-ttu-id="17fe4-326">**그림 14: express를 사용 하 여 크로스-프레미스 VNet에 연결**</span><span class="sxs-lookup"><span data-stu-id="17fe4-326">**Figure 14: Using ExpressRoute to connect to a cross-premises VNet**</span></span>

![그림 14: express를 사용 하 여 크로스-프레미스 Azure virtual network에 연결](media/7030bd39-69a6-4283-8567-3434e1ab6ba6.png)
  
<span data-ttu-id="17fe4-328">그림 14에서는 온-프레미스 라우터에서 Microsoft Azure로의 크로스-프레미스 VNet 및 간 연결을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-328">Figure 14 shows a cross-premises VNet and an ExpressRoute connection from an on-premises router to Microsoft Azure.</span></span>
  
<span data-ttu-id="17fe4-329">자세한 내용은 [Microsoft 클라우드 연결용 express](expressroute-for-microsoft-cloud-connectivity.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="17fe4-329">For more information, see [ExpressRoute for Microsoft cloud connectivity](expressroute-for-microsoft-cloud-connectivity.md).</span></span>
  
### <a name="step-5-determine-the-local-network-address-space-for-the-azure-gateway"></a><span data-ttu-id="17fe4-330">5 단계: Azure 게이트웨이의 로컬 네트워크 주소 공간을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-330">Step 5: Determine the Local Network address space for the Azure gateway.</span></span>

<span data-ttu-id="17fe4-331">온-프레미스 또는 VNet에서 다른 vnet에 대 한 라우팅에서 azure는 게이트웨이에 할당 된 로컬 네트워크 주소 공간과 일치 하는 azure 게이트웨이 간에 트래픽을 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-331">For the routing to on-premises or other VNets from a VNet, Azure forwards traffic across an Azure gateway that matches the Local Network address space assigned to the gateway.</span></span>
  
<span data-ttu-id="17fe4-332">**그림 15: 크로스-프레미스 VNet에 대 한 로컬 네트워크 주소 공간**</span><span class="sxs-lookup"><span data-stu-id="17fe4-332">**Figure 15: The Local Network address space for a cross-premises VNet**</span></span>

![그림 15: 크로스-프레미스 Azure virtual network에 대 한 로컬 네트워크 주소 공간](media/e3af2652-8b8e-4551-9a0b-b550e6e7e3c0.png)
  
<span data-ttu-id="17fe4-334">그림 15에서는 온-프레미스 네트워크에서 연결 가능한 주소 공간을 나타내는 Azure 게이트웨이의 크로스-프레미스 VNet과 로컬 네트워크 주소 공간을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-334">Figure 15 shows a cross-premises VNet and the Local Network address space on the Azure gateway, which represents the reachable address space on the on-premises network.</span></span> 
  
<span data-ttu-id="17fe4-335">다음과 같은 방법으로 로컬 네트워크 주소 공간을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-335">You can define the Local Network address space in these ways:</span></span>
  
- <span data-ttu-id="17fe4-336">옵션 1: 현재 필요 하거나 사용 중인 주소 공간의 접두사 목록 (새 서브넷을 추가할 때 업데이트가 필요할 수 있음)</span><span class="sxs-lookup"><span data-stu-id="17fe4-336">Option 1: The list of prefixes for the address space currently needed or in use (updates might be needed when you add new subnets).</span></span>
    
- <span data-ttu-id="17fe4-337">옵션 2: 전체 온-프레미스 주소 공간 (새 주소 공간을 추가 하는 경우에만 필요 함)</span><span class="sxs-lookup"><span data-stu-id="17fe4-337">Option 2: Your entire on-premises address space (updates only needed when you add new address space).</span></span>
    
<span data-ttu-id="17fe4-338">Azure 게이트웨이가 요약 된 경로를 허용 하지 않으므로 옵션 2에 대 한 로컬 네트워크 주소 공간을 정의 하 여 VNet 주소 공간을 포함 하지 않도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-338">Because the Azure gateway does not allow summarized routes, you must define the Local Network address space for option 2 so that it does not include the VNet address space.</span></span>
  
<span data-ttu-id="17fe4-339">**그림 16: VNet 주소 공간에 의해 생성 되는 주소 공간 구멍**</span><span class="sxs-lookup"><span data-stu-id="17fe4-339">**Figure 16: The address space hole created by the VNet address space**</span></span>

![그림 16: 가상 네트워크 주소 공간에 의해 생성 되는 주소 공간 구멍](media/e79c4840-f9e3-4741-9b72-59db6043aefa.png)
  
<span data-ttu-id="17fe4-341">그림 16은 루트 공간과 VNet 주소 공간을 사용 하 여 주소 공간을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-341">Figure 16 shows a representation of an address space, with the root space and the VNet address space.</span></span>
  
<span data-ttu-id="17fe4-342">다음은 VNet에서 만든 주소 공간 "구멍" 주변의 로컬 네트워크 주소 공간에 대 한 접두사를 정의 하는 예입니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-342">Here is an example of defining the prefixes for the Local Network address space around the address space "hole" created by the VNet:</span></span>
  
- <span data-ttu-id="17fe4-343">조직에서는 온-프레미스 네트워크에서 개인 주소 공간 일부 (10.0.0.0/8, 172.16.0.0/12 및 192.168.0.0/16)를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-343">An organization uses portions of the private address space (10.0.0.0/8, 172.16.0.0/12, and 192.168.0.0/16) across their on-premises network.</span></span> <span data-ttu-id="17fe4-344">옵션 2와 10.100.100.0/24를 VNet 주소 공간으로 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-344">They chose option 2 and 10.100.100.0/24 as their VNet address space.</span></span>
    
<span data-ttu-id="17fe4-345">표 7에는이 예의 로컬 네트워크 주소 공간을 정의 하는 단계 및 결과 접두사가 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-345">Table 7 shows the steps and resulting prefixes that define the Local Network address space for this example.</span></span>
  
|<span data-ttu-id="17fe4-346">**단계**</span><span class="sxs-lookup"><span data-stu-id="17fe4-346">**Step**</span></span>|<span data-ttu-id="17fe4-347">**결과**</span><span class="sxs-lookup"><span data-stu-id="17fe4-347">**Results**</span></span>|
|:-----|:-----|
|<span data-ttu-id="17fe4-348">1. VNet 주소 공간에 대 한 루트 공간이 아닌 접두사를 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-348">1. List the prefixes that are not the root space for the VNet address space.</span></span>  <br/> |<span data-ttu-id="17fe4-349">172.16.0.0/12 및 192.168.0.0/16</span><span class="sxs-lookup"><span data-stu-id="17fe4-349">172.16.0.0/12 and 192.168.0.0/16</span></span>  <br/> |
|<span data-ttu-id="17fe4-350">2.8 진수 가변 접두사에 대 한 겹치지 않는 접두 번호를 VNet 주소 공간에 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-350">2. List the non-overlapping prefixes for variable octets up to but not including the last used octet in the VNet address space.</span></span>  <br/> |<span data-ttu-id="17fe4-351">10.0.0.0/16, 10.1.0.0/16 10.99.0.0/16, 10.101.0.0/16 10.254.0.0/16, 10.255.0.0/16 (255 접두사, 10.100.0.0/16 건너뜀)</span><span class="sxs-lookup"><span data-stu-id="17fe4-351">10.0.0.0/16, 10.1.0.0/16…10.99.0.0/16, 10.101.0.0/16…10.254.0.0/16, 10.255.0.0/16 (255 prefixes, skipping 10.100.0.0/16)</span></span>  <br/> |
|<span data-ttu-id="17fe4-352">3. VNet 주소 공간의 마지막으로 사용한 옥텟에 겹치지 않는 접두사를 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-352">3. List the non-overlapping prefixes within the last used octet of the VNet address space.</span></span>  <br/> |<span data-ttu-id="17fe4-353">10.100.0.0/24, 10.100.1.0/24 ... 10.100.99.0/24, 10.100.101.0/24 ... 10.100.254.0/24, 10.100.0.255.0/24 (255 접두사, 10.100.100.0/24 건너뛰기)</span><span class="sxs-lookup"><span data-stu-id="17fe4-353">10.100.0.0/24, 10.100.1.0/24…10.100.99.0/24, 10.100.101.0/24…10.100.254.0/24, 10.100.0.255.0/24 (255 prefixes, skipping 10.100.100.0/24)</span></span>  <br/> |
   
 <span data-ttu-id="17fe4-354">**표 7: 예 로컬 주소 네트워크 공간**</span><span class="sxs-lookup"><span data-stu-id="17fe4-354">**Table 7: Example Local Address network space**</span></span>
  
### <a name="step-6-configure-on-premises-dns-servers-for-dns-replication-with-dns-servers-hosted-in-azure"></a><span data-ttu-id="17fe4-355">6 단계: Azure에 호스트 되는 dns 서버를 사용 하 여 dns 복제를 위한 온-프레미스 dns 서버를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-355">Step 6: Configure on-premises DNS servers for DNS replication with DNS servers hosted in Azure.</span></span>

<span data-ttu-id="17fe4-356">온-프레미스 컴퓨터가 azure 기반 서버 이름을 확인 하 고 azure 기반 서버가 온-프레미스 컴퓨터의 이름을 확인할 수 있도록 하려면 다음을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-356">To ensure that on-premises computers can resolve the names of Azure-based servers and Azure-based servers can resolve the names of on-premises computers, configure:</span></span>
  
- <span data-ttu-id="17fe4-357">온-프레미스 dns 서버에 전달 하는 데 사용 되는 VNet의 DNS 서버</span><span class="sxs-lookup"><span data-stu-id="17fe4-357">The DNS servers in your VNet to forward to on-premises DNS servers</span></span>
    
- <span data-ttu-id="17fe4-358">온-프레미스와 VNet에 있는 dns 서버 간의 적절 한 영역에 대 한 DNS 복제</span><span class="sxs-lookup"><span data-stu-id="17fe4-358">DNS replication of the appropriate zones between DNS servers on-premises and in the VNet</span></span>
    
<span data-ttu-id="17fe4-359">**그림 17: 크로스-프레미스 VNet의 dns 서버에 대 한 dns 복제 및 전달**</span><span class="sxs-lookup"><span data-stu-id="17fe4-359">**Figure 17: DNS replication and forwarding for a DNS server in a cross-premises VNet**</span></span>

![그림 17: 크로스-프레미스 Azure virtual network의 dns 서버에 대 한 dns 복제 및 전달](media/ab55e5ce-ccb0-49d4-a301-657a727f97b2.png)
  
<span data-ttu-id="17fe4-361">그림 17에서는 온-프레미스 네트워크의 DNS 서버와 VNet의 서브넷에 있는 크로스-프레미스 VNet을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-361">Figure 17 shows a cross-premises VNet with DNS servers in the on-premises network and on a subnet in the VNet.</span></span> <span data-ttu-id="17fe4-362">두 dns 서버 간에 dns 복제 및 전달이 구성 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-362">DNS replication and forwarding has been configured between the two DNS servers.</span></span>
  
### <a name="step-7-determine-the-use-of-forced-tunneling"></a><span data-ttu-id="17fe4-363">7 단계: 강제 터널링 사용을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-363">Step 7: Determine the use of forced tunneling.</span></span>

<span data-ttu-id="17fe4-364">Azure 서브넷의 기본 시스템 경로는 인터넷을 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-364">The default system route for Azure subnets points to the Internet.</span></span> <span data-ttu-id="17fe4-365">가상 컴퓨터의 모든 트래픽이 크로스-프레미스 연결에서 이동 되도록 하려면 Azure 게이트웨이를 다음 홉 주소로 사용 하는 기본 경로를 사용 하 여 라우팅 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-365">To ensure that all traffic from virtual machines travels across the cross-premises connection, create a routing table with the default route that uses the Azure gateway as its next-hop address.</span></span> <span data-ttu-id="17fe4-366">그런 다음 경로 테이블을 서브넷과 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-366">You then associate the route table with the subnet.</span></span> <span data-ttu-id="17fe4-367">이를 강제 터널링 이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-367">This is known as forced tunneling.</span></span> <span data-ttu-id="17fe4-368">자세한 내용은 [강제 터널링 구성을](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-forced-tunneling-rm)참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="17fe4-368">For more information, see [Configure forced tunneling](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-forced-tunneling-rm).</span></span>
  
<span data-ttu-id="17fe4-369">**그림 18: 크로스-프레미스 VNet에 대 한 강제 터널링 및 사용자 정의 경로**</span><span class="sxs-lookup"><span data-stu-id="17fe4-369">**Figure 18: User-defined routes and forced tunneling for a cross-premises VNet**</span></span>

![그림 18: 크로스-프레미스 Azure virtual network에 대 한 강제 터널링 및 사용자 정의 경로](media/1e545ec6-c2d9-48d2-bb5e-e0a581fee004.png)
  
<span data-ttu-id="17fe4-371">그림 18은 Azure 게이트웨이를 가리키는 서브넷에 대 한 사용자 정의 경로가 있는 크로스-프레미스 VNet을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-371">Figure 18 shows a cross-premises VNet with a user-defined route for a subnet pointing to the Azure gateway.</span></span>
  
## <a name="sharepoint-server-2016-farm-in-azure"></a><span data-ttu-id="17fe4-372">Azure의 SharePoint Server 2016 팜</span><span class="sxs-lookup"><span data-stu-id="17fe4-372">SharePoint Server 2016 farm in Azure</span></span>
<span data-ttu-id="17fe4-373"><a name="cross_prem"> </a></span><span class="sxs-lookup"><span data-stu-id="17fe4-373"></span></span>

<span data-ttu-id="17fe4-374">Azure IaaS에서 호스트 되는 인트라넷 IT 작업의 예로는 가용성이 높은 다중 계층 SharePoint Server 2016 팜이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-374">An example of an intranet IT workload hosted in Azure IaaS is a highly-available, multi-tier SharePoint Server 2016 farm.</span></span>
  
<span data-ttu-id="17fe4-375">**그림 19: Azure IaaS에서 사용 가능한 고가용성 인트라넷 SharePoint Server 2016 팜**</span><span class="sxs-lookup"><span data-stu-id="17fe4-375">**Figure 19: A highly-available intranet SharePoint Server 2016 farm in Azure IaaS**</span></span>

![Azure IaaS의 고가용성 SharePoint Server 2016 팜](media/3a922e21-df91-455f-ba90-78abdd48d98d.png)
  
<span data-ttu-id="17fe4-377">그림 19에서는 프런트 엔드 및 데이터 계층에 대 한 내부 부하 분산 장치를 사용 하는 크로스-프레미스 VNet에 배포 된 SharePoint Server 2016 팜의 9 개 서버를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="17fe4-377">Figure 19 shows the nine servers of a SharePoint Server 2016 farm deployed in a cross-premises VNet that uses internal load balancers for the front-end and data tiers.</span></span> <span data-ttu-id="17fe4-378">단계별 디자인 및 배포 지침을 비롯 한 자세한 내용은 [Microsoft Azure의 SharePoint Server 2016](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-in-microsoft-azure)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="17fe4-378">For more information, including step-by-step design and deployment instructions, see [SharePoint Server 2016 in Microsoft Azure](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-in-microsoft-azure).</span></span>
  
> [!TIP]
> <span data-ttu-id="17fe4-379">시뮬레이트된 크로스-프레미스 VNet에 단일 서버 SharePoint server 2016 팜을 만들려면 [Azure 개발/테스트 환경의 인트라넷 SharePoint server 2016](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="17fe4-379">To create a single-server SharePoint Server 2016 farm in a simulated cross-premises VNet, see [Intranet SharePoint Server 2016 in Azure dev/test environment](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment).</span></span> 
  
<span data-ttu-id="17fe4-380">크로스-프레미스 azure 가상 네트워크의 가상 컴퓨터에 배포 된 IT 워크 로드에 대 한 추가 예제를 보려면 [Azure IaaS 용 하이브리드 클라우드 시나리오](https://docs.microsoft.com/office365/enterprise/hybrid-cloud-scenarios-for-azure-iaas)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="17fe4-380">For additional examples of IT workloads deployed on virtual machines in a cross-premises Azure virtual network, see [Hybrid cloud scenarios for Azure IaaS](https://docs.microsoft.com/office365/enterprise/hybrid-cloud-scenarios-for-azure-iaas).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="17fe4-381">참고 항목</span><span class="sxs-lookup"><span data-stu-id="17fe4-381">See also</span></span>

[<span data-ttu-id="17fe4-382">Microsoft Cloud Networking for Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="17fe4-382">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="17fe4-383">Microsoft 클라우드 IT 아키텍처 리소스</span><span class="sxs-lookup"><span data-stu-id="17fe4-383">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)


