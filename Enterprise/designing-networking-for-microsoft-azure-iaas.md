---
title: "Microsoft Azure IaaS에 대 한 네트워킹 디자인 (영문)"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: concetpual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 9cb70c9d-9ed9-47cc-af5a-6403d87d3372
description: "요약: Microsoft Azure IaaS에는 작업에 대해 최적화 된 네트워킹을 디자인 하는 방법을 이해 합니다."
ms.openlocfilehash: e4861de51f386af6e142debdafc64f655f010880
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2017
---
# <a name="designing-networking-for-microsoft-azure-iaas"></a><span data-ttu-id="88142-103">Microsoft Azure IaaS에 대 한 네트워킹 디자인 (영문)</span><span class="sxs-lookup"><span data-stu-id="88142-103">Designing networking for Microsoft Azure IaaS</span></span>

 <span data-ttu-id="88142-104">**요약:** Microsoft Azure IaaS에는 작업에 대해 최적화 된 네트워킹을 디자인 하는 방법을 이해 합니다.</span><span class="sxs-lookup"><span data-stu-id="88142-104">**Summary:** Understand how to design optimized networking for workloads in Microsoft Azure IaaS.</span></span>
  
<span data-ttu-id="88142-105">Azure IaaS에서 호스팅되는 IT 작업 부하에 대 한 네트워킹 최적화 Azure 가상 네트워크 (VNets) 주소 공간, 라우팅, DNS 및 부하 분산에 대 한 이해를 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="88142-105">Optimizing networking for IT workloads hosted in Azure IaaS requires an understanding of Azure virtual networks (VNets), address spaces, routing, DNS, and load balancing.</span></span>
  
## <a name="planning-steps-for-any-vnet"></a><span data-ttu-id="88142-106">모든 VNet에 대 한 계획 단계</span><span class="sxs-lookup"><span data-stu-id="88142-106">Planning steps for any VNet</span></span>

<span data-ttu-id="88142-107">모든 유형의 VNet에 대 한 다음이 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="88142-107">Follow these steps for any type of VNet.</span></span>
  
### <a name="step-1-prepare-your-intranet-for-microsoft-cloud-services"></a><span data-ttu-id="88142-108">1 단계: Microsoft 클라우드 서비스에 대 한 인트라넷을 준비 합니다.</span><span class="sxs-lookup"><span data-stu-id="88142-108">Step 1: Prepare your intranet for Microsoft cloud services.</span></span>

<span data-ttu-id="88142-109">[Microsoft 클라우드 연결의 공통 요소](common-elements-of-microsoft-cloud-connectivity.md)에 **Microsoft 클라우드 서비스에 대 한 네트워크를 준비 하는 단계** 섹션을 통해 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="88142-109">Go through the **Steps to prepare your network for Microsoft cloud services** section in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).</span></span>
  
### <a name="step-2-optimize-your-internet-bandwidth"></a><span data-ttu-id="88142-110">2 단계: 인터넷 대역폭을 최적화 합니다.</span><span class="sxs-lookup"><span data-stu-id="88142-110">Step 2: Optimize your Internet bandwidth.</span></span>

<span data-ttu-id="88142-111">[Microsoft SaaS에 대 한 네트워킹 디자인 (영문)](designing-networking-for-microsoft-saas.md)에서 **Microsoft SaaS 서비스에 대 한 네트워크를 준비 하는 단계** 섹션의 2-4 단계를 사용 하 여 인터넷 대역폭을 최적화 합니다.</span><span class="sxs-lookup"><span data-stu-id="88142-111">Optimize your Internet bandwidth using steps 2 - 4 of the **Steps to prepare your network for Microsoft SaaS services** section in [Designing networking for Microsoft SaaS](designing-networking-for-microsoft-saas.md).</span></span>
  
### <a name="step-3-determine-the-type-of-vnet-cloud-only-or-cross-premises"></a><span data-ttu-id="88142-112">3 단계: VNet의 형식을 확인 (클라우드 전용 또는 크로스-프레미스).</span><span class="sxs-lookup"><span data-stu-id="88142-112">Step 3: Determine the type of VNet (cloud-only or cross-premises).</span></span>

<span data-ttu-id="88142-p101">클라우드 전용 VNet는 온-프레미스 네트워크에 연결 합니다. 다음은 한 예입니다.</span><span class="sxs-lookup"><span data-stu-id="88142-p101">A cloud-only VNet has no connection to an on-premises network. Here is an example.</span></span>
  
<span data-ttu-id="88142-115">**그림 1:는 클라우드 전용 VNet**</span><span class="sxs-lookup"><span data-stu-id="88142-115">**Figure 1: A cloud-only VNet**</span></span>

![그림 1: Azure에 있는 클라우드 전용 Virtual Network](images/8be19104-02b3-4a7f-b0a0-30d6fcf8890b.png)
  
<span data-ttu-id="88142-117">그림 1 클라우드 전용 VNet에서 가상 컴퓨터의 집합을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="88142-117">Figure 1 shows a set of virtual machines in a cloud-only VNet.</span></span>
  
<span data-ttu-id="88142-p102">A 크로스-프레미스 VNet가을--사이트 마다 S2S ()는 Azure 게이트웨이 통해 온-프레미스 네트워크로 VPN 또는 ExpressRoute 연결 합니다. 다음은 한 예입니다.</span><span class="sxs-lookup"><span data-stu-id="88142-p102">A cross-premises VNet has a site-to-site (S2S) VPN or ExpressRoute connection to an on-premises network through an Azure gateway. Here is an example.</span></span>
  
<span data-ttu-id="88142-120">**그림 2: 크로스-프레미스 VNet**</span><span class="sxs-lookup"><span data-stu-id="88142-120">**Figure 2: A cross-premises VNet**</span></span>

![그림 2: Azure의 크로스-프레미스 Virtual Network](images/caacf007-e0dc-45d3-9531-441109776d25.png)
  
<span data-ttu-id="88142-122">그림 2는 온-프레미스 네트워크에 연결 되는 크로스-프레미스 VNet에서 가상 컴퓨터의 집합을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="88142-122">Figure 2 shows a set of virtual machines in a cross-premises VNet, which is connected to an on-premises network.</span></span>
  
<span data-ttu-id="88142-123">참조를 추가로이 문서에서 [크로스-프레미스 VNet에 대 한 계획 수립 단계](designing-networking-for-microsoft-azure-iaas.md#cross_prem) 섹션입니다.</span><span class="sxs-lookup"><span data-stu-id="88142-123">See the additional [Planning steps for a cross-premises VNet](designing-networking-for-microsoft-azure-iaas.md#cross_prem) section in this article.</span></span>
  
### <a name="step-4-determine-the-address-space-of-the-vnet"></a><span data-ttu-id="88142-124">4 단계:는 VNet의 주소 공간을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="88142-124">Step 4: Determine the address space of the VNet.</span></span>

<span data-ttu-id="88142-125">표 1은 다양 한 유형의 VNets에 대 한 주소 공간을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="88142-125">Table 1 shows the address spaces for the different types of VNets.</span></span>
  
|<span data-ttu-id="88142-126">**VNet의 유형**</span><span class="sxs-lookup"><span data-stu-id="88142-126">**Type of VNet**</span></span>|<span data-ttu-id="88142-127">**가상 네트워크 주소 공간**</span><span class="sxs-lookup"><span data-stu-id="88142-127">**Virtual network address space**</span></span>|
|:-----|:-----|
|<span data-ttu-id="88142-128">클라우드 전용</span><span class="sxs-lookup"><span data-stu-id="88142-128">Cloud-only</span></span>  <br/> |<span data-ttu-id="88142-129">임의의 개인 주소 공간</span><span class="sxs-lookup"><span data-stu-id="88142-129">Arbitrary private address space</span></span>  <br/> |
|<span data-ttu-id="88142-130">클라우드 전용 상호 연결</span><span class="sxs-lookup"><span data-stu-id="88142-130">Interconnected cloud-only</span></span>  <br/> |<span data-ttu-id="88142-131">임의의 개인 하지만 다른 겹치는 하지 VNets 연결</span><span class="sxs-lookup"><span data-stu-id="88142-131">Arbitrary private, but not overlapping with other connected VNets</span></span>  <br/> |
|<span data-ttu-id="88142-132">크로스-프레미스</span><span class="sxs-lookup"><span data-stu-id="88142-132">Cross-premises</span></span>  <br/> |<span data-ttu-id="88142-133">개인, 하지만 하지 온-프레미스와 겹침</span><span class="sxs-lookup"><span data-stu-id="88142-133">Private, but not overlapping with on-premises</span></span>  <br/> |
|<span data-ttu-id="88142-134">상호 연결 된 크로스-프레미스</span><span class="sxs-lookup"><span data-stu-id="88142-134">Interconnected cross-premises</span></span>  <br/> |<span data-ttu-id="88142-135">개인, 하지만에 온-프레미스 및 기타 겹치는 하지 VNets 연결</span><span class="sxs-lookup"><span data-stu-id="88142-135">Private, but not overlapping with on-premises and other connected VNets</span></span>  <br/> |
   
 <span data-ttu-id="88142-136">**표 1: 유형의 VNets 및 해당 하는 주소 공간**</span><span class="sxs-lookup"><span data-stu-id="88142-136">**Table 1: Types of VNets and their corresponding address space**</span></span>
  
<span data-ttu-id="88142-137">가상 컴퓨터는 서브넷의 주소 공간에서 주소 구성은 DHCP가 할당 됩니다.</span><span class="sxs-lookup"><span data-stu-id="88142-137">Virtual machines are assigned an address configuration from the address space of the subnet by DHCP:</span></span>
  
- <span data-ttu-id="88142-138">주소/서브넷 마스크</span><span class="sxs-lookup"><span data-stu-id="88142-138">Address/subnet mask</span></span>
    
- <span data-ttu-id="88142-139">기본 게이트웨이</span><span class="sxs-lookup"><span data-stu-id="88142-139">Default gateway</span></span>
    
- <span data-ttu-id="88142-140">DNS 서버 IP 주소</span><span class="sxs-lookup"><span data-stu-id="88142-140">DNS server IP addresses</span></span>
    
<span data-ttu-id="88142-141">고정 IP 주소를 예약할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88142-141">You can also reserve a static IP address.</span></span>
  
<span data-ttu-id="88142-142">가상 컴퓨터도 할당할 수 공용 IP 주소를 개별적으로 또는 (클래식 배포 컴퓨터에만 해당)에 포함 된 클라우드 서비스에서.</span><span class="sxs-lookup"><span data-stu-id="88142-142">Virtual machines can also be assigned a public IP address, either individually or from the containing cloud service (for classic deployment machines only).</span></span>
  
### <a name="step-5-determine-the-subnets-within-the-vnet-and-the-address-spaces-assigned-to-each"></a><span data-ttu-id="88142-143">5 단계:은 VNet 및 각 할당 된 주소 공간 내 서브넷을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="88142-143">Step 5: Determine the subnets within the VNet and the address spaces assigned to each.</span></span>

<span data-ttu-id="88142-144">서브넷에는 VNet, 게이트웨이 서브넷 및 가상 컴퓨터 호스팅 서브넷의는 다음과 같은 두가지 유형이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88142-144">There are two types of subnets in a VNet, a gateway subnet and a virtual machine-hosting subnet.</span></span>
  
<span data-ttu-id="88142-145">**그림 3: Azure에서 서브넷의 두 형식**</span><span class="sxs-lookup"><span data-stu-id="88142-145">**Figure 3: The two types of subnets in Azure**</span></span>

![그림 3: Azure에 있는 서브넷 두 종류](images/2eaa512d-1293-4e9b-b927-6bfe0fc0acb4.png)
  
<span data-ttu-id="88142-147">그림 3에는 Azure 게이트웨이 및 가상 컴퓨터를 포함 하는 가상 컴퓨터 호스팅 서브넷의 집합을 포함 하는 게이트웨이 서브넷을 포함 하는 VNet 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88142-147">Figure 3 shows a VNet containing a gateway subnet that contains an Azure gateway and a set of virtual machine-hosting subnets containing virtual machines.</span></span>
  
<span data-ttu-id="88142-p103">Azure 게이트웨이 서브넷은 Azure 게이트웨이 두 가상 컴퓨터 호스트를 위해 Azure가 필요 합니다. 29 비트 접두사 길이 사용 하 여 주소 공간 지정 (예: 192.168.15.248/29). ExpressRoute를 사용 하 여 계획 하는 경우에 특히 28 비트 또는 더 작은 접두사 길이 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="88142-p103">The Azure gateway subnet is needed by Azure to host the two virtual machines of your Azure gateway. Specify an address space with at least a 29-bit prefix length (example: 192.168.15.248/29). A 28-bit or smaller prefix length is recommended, especially if you are planning to use ExpressRoute.</span></span>
  
<span data-ttu-id="88142-151">Azure 게이트웨이 서브넷의 주소 공간을 결정 하기 위한 최상의 방법 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="88142-151">A best practice for determining the address space of the Azure gateway subnet is the following:</span></span>
  
1. <span data-ttu-id="88142-152">게이트웨이 서브넷의 크기를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="88142-152">Decide on the size of the gateway subnet.</span></span>
    
2. <span data-ttu-id="88142-153">VNet의 주소 공간에서 가변 비트를 0으로 게이트웨이 서브넷에 사용 되는 비트를 설정 하 고 나머지 비트를 1로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="88142-153">In the variable bits in the address space of the VNet, set the bits used for the gateway subnet to 0 and set the remaining bits to 1.</span></span>
    
3. <span data-ttu-id="88142-154">8 진수를 변환 하 고 게이트웨이 서브넷의 크기를 설정 하는 접두사 길이와 주소 공간으로 표현 합니다.</span><span class="sxs-lookup"><span data-stu-id="88142-154">Convert to decimal and express as an address space with the prefix length set to the size of the gateway subnet.</span></span>
    
<span data-ttu-id="88142-155">이 메서드와 함께 게이트웨이 서브넷에 대 한 주소 공간 끝인지 항상 먼 VNet 주소 공간입니다.</span><span class="sxs-lookup"><span data-stu-id="88142-155">With this method, the address space for the gateway subnet is always at the farthest end of the VNet address space.</span></span>
  
<span data-ttu-id="88142-p104">다음은 게이트웨이 서브넷에 대 한 주소 접두사를 정의 하는 예제:은 VNet의 주소 공간은 10.119.0.0/16 합니다. 조직 처음 사이트 마다 VPN 연결을 사용할 수는 있지만 ExpressRoute 결국. 표 2 단계 및 네트워크 접두사 표기법 (CIDR) 게이트웨이 서브넷 주소 접두사를 결정 하는 결과 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="88142-p104">Here is an example of defining the address prefix for the gateway subnet: The address space of the VNet is 10.119.0.0/16. The organization will initially use a site-to-site VPN connection, but will eventually get ExpressRoute. Table 2 shows the steps and results of determining the gateway subnet address prefix in network prefix notation (also known as CIDR).</span></span>

<span data-ttu-id="88142-159">다음은 단계 및 게이트웨이 서브넷 주소 접두사를 결정 하는 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="88142-159">Here are the steps and example of determining the gateway subnet address prefix:</span></span>

1. <span data-ttu-id="88142-p105">게이트웨이 서브넷의 크기를 결정 합니다. 이 예제에 대 한 /28을 선택 했습니다.</span><span class="sxs-lookup"><span data-stu-id="88142-p105">Decide on the size of the gateway subnet. For our example, we chose /28.</span></span>
2. <span data-ttu-id="88142-p106">비트 VNet 주소 공간 (b)의 변수 부분에 0으로 설정 게이트웨이에 대 한 서브넷 비트 (G), 그렇지 않은 경우 1 (V) 합니다. 이 예제에 대 한는 VNet에 대 한 10.119.0.0/16 주소 공간을 사용 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="88142-p106">Set the bits in the variable portion of the VNet address space (b) to 0 for the gateway subnet bits (G), otherwise 1 (V). For our example, we are using the 10.119.0.0/16 address space for the VNet. </span></span><br/>
<br/><span data-ttu-id="88142-p107">10.119. bbbbbbbb 합니다. bbbbbbbb</span><span class="sxs-lookup"><span data-stu-id="88142-p107">10.119. bbbbbbbb . bbbbbbbb </span></span><br/><span data-ttu-id="88142-p108">10.119입니다. VVVVVVVV 합니다. VVVVGGGG</span><span class="sxs-lookup"><span data-stu-id="88142-p108">10.119. VVVVVVVV . VVVVGGGG </span></span><br/><span data-ttu-id="88142-p109">10.119입니다. 11111111 합니다. 11110000</span><span class="sxs-lookup"><span data-stu-id="88142-p109">10.119. 11111111 . 11110000 </span></span><br/><br/>
3. <span data-ttu-id="88142-p110">10 진수 및 주소 공간으로 express 2 단계에서 결과 변환 합니다. 예제에 10.119 합니다. 11111111 합니다. 11110000 10.119.255.240, 이며 (이 예제에서는 28) 하 여 1 단계에서 접두사 길이, 결과 게이트웨이 서브넷 주소 접두사가 10.119.255.240/28 합니다.</span><span class="sxs-lookup"><span data-stu-id="88142-p110">Convert the result from step 2 to decimal and express as an address space. For our example, 10.119. 11111111 . 11110000 is 10.119.255.240, and with the prefix length from step 1, (28 in our example), the resulting gateway subnet address prefix is 10.119.255.240/28.</span></span>
  
<span data-ttu-id="88142-177">자세한 내용은 [Azure 게이트웨이 서브넷에 대 한 주소 공간 계산기](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) 를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="88142-177">See [Address space calculator for Azure gateway subnets](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) for more information.</span></span>
  
<span data-ttu-id="88142-178">서브넷 가상 컴퓨터를 호스팅하는 일반적인 역할 또는 응용 프로그램의 또는 서브넷 격리에 대 한 계층 등의 일반적인 온-프레미스 지침에 따라 수행할 수 있는 Azure 가상 컴퓨터를 배치 하는 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="88142-178">Virtual machine-hosting subnets are where you place Azure virtual machines, which you can do according to typical on-premises guidelines, such as a common role or tier of an application or for subnet isolation.</span></span>
  
<span data-ttu-id="88142-p111">Azure의 처음 3 주소를 사용 하 여 각 서브넷에 있습니다. 따라서 Azure 서브넷에서 사용할 수 있는 주소의 수는 2<sup>n</sup> -5, 여기서 n은 호스트 비트 수 있습니다. 표 3에서는 필요에 따라 비트를 호스트 하는 가상 컴퓨터를 필요한 수의 범위 및 해당 서브넷 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="88142-p111">Azure uses the first 3 addresses on each subnet. Therefore, the number of possible addresses on an Azure subnet is 2<sup>n</sup> - 5, where n is the number of host bits. Table 3 shows the range of virtual machines required, the number of hosts bits needed, and the corresponding subnet size.</span></span>
  
|<span data-ttu-id="88142-182">**필요한 가상 컴퓨터**</span><span class="sxs-lookup"><span data-stu-id="88142-182">**Virtual machines required**</span></span>|<span data-ttu-id="88142-183">**호스트 비트**</span><span class="sxs-lookup"><span data-stu-id="88142-183">**Host bits**</span></span>|<span data-ttu-id="88142-184">**서브넷 크기**</span><span class="sxs-lookup"><span data-stu-id="88142-184">**Subnet size**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="88142-185">1-3</span><span class="sxs-lookup"><span data-stu-id="88142-185">1-3</span></span>  <br/> |<span data-ttu-id="88142-186">3</span><span class="sxs-lookup"><span data-stu-id="88142-186">3</span></span>  <br/> |<span data-ttu-id="88142-187">/29</span><span class="sxs-lookup"><span data-stu-id="88142-187">/29</span></span>  <br/> |
|<span data-ttu-id="88142-188">4-11</span><span class="sxs-lookup"><span data-stu-id="88142-188">4-11</span></span>  <br/> |<span data-ttu-id="88142-189">4</span><span class="sxs-lookup"><span data-stu-id="88142-189">4</span></span>  <br/> |<span data-ttu-id="88142-190">/28</span><span class="sxs-lookup"><span data-stu-id="88142-190">/28</span></span>  <br/> |
|<span data-ttu-id="88142-191">12-27</span><span class="sxs-lookup"><span data-stu-id="88142-191">12-27</span></span>  <br/> |<span data-ttu-id="88142-192">5</span><span class="sxs-lookup"><span data-stu-id="88142-192">5</span></span>  <br/> |<span data-ttu-id="88142-193">/27</span><span class="sxs-lookup"><span data-stu-id="88142-193">/27</span></span>  <br/> |
|<span data-ttu-id="88142-194">28-59</span><span class="sxs-lookup"><span data-stu-id="88142-194">28-59</span></span>  <br/> |<span data-ttu-id="88142-195">6</span><span class="sxs-lookup"><span data-stu-id="88142-195">6</span></span>  <br/> |<span data-ttu-id="88142-196">/26</span><span class="sxs-lookup"><span data-stu-id="88142-196">/26</span></span>  <br/> |
|<span data-ttu-id="88142-197">60-123</span><span class="sxs-lookup"><span data-stu-id="88142-197">60-123</span></span>  <br/> |<span data-ttu-id="88142-198">7</span><span class="sxs-lookup"><span data-stu-id="88142-198">7</span></span>  <br/> |<span data-ttu-id="88142-199">/25</span><span class="sxs-lookup"><span data-stu-id="88142-199">/25</span></span>  <br/> |
   
 <span data-ttu-id="88142-200">**표 3: 가상 컴퓨터 요구 사항 및 서브넷 크기에 따라**</span><span class="sxs-lookup"><span data-stu-id="88142-200">**Table 3: Virtual machine requirements and their subnet sizes**</span></span>
  
<span data-ttu-id="88142-201">서브넷 또는 VNet에 가상 컴퓨터의 최대 크기에 대 한 자세한 내용은 [네트워킹 제한](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="88142-201">For more information about the maximum amount of virtual machines on a subnet or VNet, see [Networking Limits](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits).</span></span>
  
<span data-ttu-id="88142-202">자세한 내용은 [계획 및 디자인 Azure 가상 네트워크를](https://azure.microsoft.com/documentation/articles/virtual-network-vnet-plan-design-arm/)참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="88142-202">For more information, see [Plan and design Azure Virtual Networks](https://azure.microsoft.com/documentation/articles/virtual-network-vnet-plan-design-arm/).</span></span>
  
### <a name="step-6-determine-the-dns-server-configuration-and-the-addresses-of-the-dns-servers-to-assign-to-vms-in-the-vnet"></a><span data-ttu-id="88142-203">6 단계: DNS 서버 구성 및 vm를 포함 하는 VNet에 게 할당 하려면 DNS 서버 주소를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="88142-203">Step 6: Determine the DNS server configuration and the addresses of the DNS servers to assign to VMs in the VNet.</span></span>

<span data-ttu-id="88142-p112">Azure 가상 컴퓨터의 DHCP에 의해 DNS 서버 주소를 할당합니다. DNS 서버 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88142-p112">Azure assigns virtual machines the addresses of DNS servers by DHCP. DNS servers can be:</span></span>
  
- <span data-ttu-id="88142-206">Azure에서 제공: 로컬 이름 등록 하 고 로컬 및 인터넷 이름 확인을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="88142-206">Supplied by Azure: Provides local name registration and local and Internet name resolution</span></span>
    
- <span data-ttu-id="88142-207">사용자에 의해 제공: 로컬 또는 인트라넷 이름 등록 하 고 인트라넷 또는 인터넷 이름 확인을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="88142-207">Provided by you: Provides local or intranet name registration and either intranet or Internet name resolution</span></span>
    
<span data-ttu-id="88142-208">표 4에서는 각 유형의 VNet에 대 한 DNS 서버의 다양 한 구성을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="88142-208">Table 4 shows the different configurations of DNS servers for each type of VNet.</span></span>
    
|<span data-ttu-id="88142-209">**VNet의 유형**</span><span class="sxs-lookup"><span data-stu-id="88142-209">**Type of VNet**</span></span>|<span data-ttu-id="88142-210">**DNS 서버**</span><span class="sxs-lookup"><span data-stu-id="88142-210">**DNS server**</span></span>|
|:-----|:-----|
|<span data-ttu-id="88142-211">클라우드 전용</span><span class="sxs-lookup"><span data-stu-id="88142-211">Cloud-only</span></span>  <br/> |<span data-ttu-id="88142-212">로컬 복사본과 인터넷 이름 확인에 대 한 azure 제공</span><span class="sxs-lookup"><span data-stu-id="88142-212">Azure-supplied for local and Internet name resolution</span></span>  <br/> <span data-ttu-id="88142-213">로컬 복사본과 인터넷 이름 확인 (DNS 전달)에 대 한 azure 가상 컴퓨터</span><span class="sxs-lookup"><span data-stu-id="88142-213">Azure virtual machine for local and Internet name resolution (DNS forwarding)</span></span>  <br/> |
|<span data-ttu-id="88142-214">크로스-프레미스</span><span class="sxs-lookup"><span data-stu-id="88142-214">Cross-premises</span></span>  <br/> |<span data-ttu-id="88142-215">온-프레미스 로컬 복사본과 인트라넷 이름 확인을 위해</span><span class="sxs-lookup"><span data-stu-id="88142-215">On-premises for local and intranet name resolution</span></span>  <br/> <span data-ttu-id="88142-216">로컬 복사본과 인트라넷 이름 확인 (DNS 복제 및 전달)에 대 한 azure 가상 컴퓨터</span><span class="sxs-lookup"><span data-stu-id="88142-216">Azure virtual machine for local and intranet name resolution (DNS replication and forwarding)</span></span>  <br/> |
   
 <span data-ttu-id="88142-217">**서로 다른 두 유형의 VNets에 대 한 표 4: DNS 서버 옵션**</span><span class="sxs-lookup"><span data-stu-id="88142-217">**Table 4: DNS server options for the two different types of VNets**</span></span>
  
<span data-ttu-id="88142-218">자세한 내용은 [Vm 및 역할 인스턴스에 대 한 이름 확인](https://docs.microsoft.com/azure/virtual-network/virtual-networks-name-resolution-for-vms-and-role-instances)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="88142-218">For more information, see [Name Resolution for VMs and Role Instances](https://docs.microsoft.com/azure/virtual-network/virtual-networks-name-resolution-for-vms-and-role-instances).</span></span>
  
### <a name="step-7-determine-the-load-balancing-configuration-internet-facing-or-internal"></a><span data-ttu-id="88142-219">7 단계: 부하 분산 구성 확인 (인터넷 또는 내부).</span><span class="sxs-lookup"><span data-stu-id="88142-219">Step 7: Determine the load balancing configuration (Internet-facing or internal).</span></span>

<span data-ttu-id="88142-p113">일부 경우에는 동일한 역할을 하는 서버 집합에 들어오는 트래픽을 배포 하려고 합니다. Azure IaaS가 인터넷에 대 한이 작업을 수행 하는 기본 제공 기능 및 내부 트래픽을 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="88142-p113">In some cases, you want to distribute incoming traffic to a set of servers that have the same role. Azure IaaS has a built-in facility to do this for Internet-facing and internal traffic loads.</span></span>
  
<span data-ttu-id="88142-222">Azure 인터넷 부하 분산을 임의로 부하 분산 된 집합의 구성원에 게 인터넷에서 들어오는 원치 않는 트래픽을 분산 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="88142-222">Azure Internet-facing load balancing randomly distributes unsolicited incoming traffic from the Internet to the members of a load-balanced set.</span></span>
  
<span data-ttu-id="88142-223">**그림 4: 외부 부하 분산 장치를 Azure의**</span><span class="sxs-lookup"><span data-stu-id="88142-223">**Figure 4: An external load balancer in Azure**</span></span>

![그림 4: Azure의 외부 부하 분산 장치](images/eb5945e5-0c2b-40f1-b9ed-54bb2b0f9e59.png)
  
<span data-ttu-id="88142-225">그림 4는 인바운드 NAT 규칙 또는 부하 분산 된 집합의 가상 컴퓨터의 집합에는 끝점에서 들어오는 트래픽을 분배 하는 Azure에는 외부 부하 분산 장치를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="88142-225">Figure 4 shows an external load balancer in Azure that distributes incoming traffic on an inbound NAT rule or endpoint to a set of virtual machines in a load-balanced set.</span></span>
  
<span data-ttu-id="88142-226">Azure 내부 부하 분산을 임의로 부하 분산 된 집합의 구성원에 게 인트라넷 컴퓨터 또는 다른 Azure Vm에서 임의의 들어오는 트래픽을 분산 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="88142-226">Azure internal load balancing randomly distributes unsolicited incoming traffic from other Azure VMs or from intranet computers to the members of a load-balanced set.</span></span> 
  
<span data-ttu-id="88142-227">**그림 5: 내부 부하 분산 장치를 Azure의**</span><span class="sxs-lookup"><span data-stu-id="88142-227">**Figure 5: An internal load balancer in Azure**</span></span>

![그림 5: Azure의 내부 부하 분산 장치](images/d1451b73-6465-449d-b3e6-22160ce51f35.png)
  
<span data-ttu-id="88142-229">그림 5는 인바운드 NAT 규칙 또는 부하 분산 된 집합의 가상 컴퓨터의 집합에는 끝점에서 들어오는 트래픽을 분배 하는 Azure에는 내부 부하 분산 장치를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="88142-229">Figure 5 shows an internal load balancer in Azure that distributes incoming traffic on an inbound NAT rule or endpoint to a set of virtual machines in a load-balanced set.</span></span>
  
<span data-ttu-id="88142-230">자세한 내용은 [Azure 부하 분산 장치](https://docs.microsoft.com/azure/load-balancer/load-balancer-overview)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="88142-230">For more information, see [Azure Load Balancer](https://docs.microsoft.com/azure/load-balancer/load-balancer-overview).</span></span>
  
### <a name="step-8-determine-the-use-of-virtual-appliances-and-user-defined-routes"></a><span data-ttu-id="88142-231">8 단계: 가상 장비 및 사용자 정의 경로 사용을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="88142-231">Step 8: Determine the use of virtual appliances and user-defined routes.</span></span>

<span data-ttu-id="88142-232">사용자 VNet의 가상 기기에 대 한 트래픽 음성 메일로 착신 전환 해야하는 경우 서브넷에 하나 이상의 사용자 정의 경로 추가 해야할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88142-232">If you need to forward traffic to virtual appliances in your VNet, you may need to add one or more user-defined routes to a subnet.</span></span>
  
<span data-ttu-id="88142-233">**그림 6: 가상 장비 및 Azure에서 사용자 정의 경로**</span><span class="sxs-lookup"><span data-stu-id="88142-233">**Figure 6: Virtual appliances and user-defined routes in Azure**</span></span>

![그림 6: Azure의 가상 어플라이언스 및 사용자 정의 경로](images/f181d0f4-ebf9-439e-9c98-dec17428c32b.png)
  
<span data-ttu-id="88142-235">그림 6 크로스-프레미스 VNet 및 가상 기기를 가리키는 가상 컴퓨터 호스팅 서브넷에 할당 된 사용자 정의 경로 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="88142-235">Figure 6 shows a cross-premises VNet and a user-defined route assigned to a virtual machine-hosting subnet that points to a virtual appliance.</span></span>
  
<span data-ttu-id="88142-236">자세한 내용은 [사용자 정의 된 경로 및 IP 전달](https://docs.microsoft.com/azure/virtual-network/virtual-networks-udr-overview)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="88142-236">For more information, see [User Defined Routes and IP Forwarding](https://docs.microsoft.com/azure/virtual-network/virtual-networks-udr-overview).</span></span>
  
### <a name="step-9-determine-how-computers-from-the-internet-will-connect-to-virtual-machines"></a><span data-ttu-id="88142-237">9 단계: 인터넷에서 컴퓨터 가상 컴퓨터에 연결 하는 방법을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="88142-237">Step 9: Determine how computers from the Internet will connect to virtual machines.</span></span>

<span data-ttu-id="88142-238">여러 가지 방법으로 프록시 서버 또는 다른에 지 장치를 통해 조직 네트워크에서의 액세스를 포함 하는 프로그램 VNet에 가상 컴퓨터에 대 한 인터넷 액세스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="88142-238">There are multiple ways to provide Internet access to the virtual machines on a VNet, which includes access from your organization network through your proxy server or other edge device.</span></span>
  
<span data-ttu-id="88142-239">표 5 필터링 하거나 원치 않는 들어오는 트래픽을 검사 하기 위한 메서드를 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="88142-239">Table 5 lists the methods for filtering or inspecting unsolicited incoming traffic.</span></span>
  
|<span data-ttu-id="88142-240">**메서드**</span><span class="sxs-lookup"><span data-stu-id="88142-240">**Method**</span></span>|<span data-ttu-id="88142-241">**배포 모델**</span><span class="sxs-lookup"><span data-stu-id="88142-241">**Deployment model**</span></span>|
|:-----|:-----|
|<span data-ttu-id="88142-242">1. 끝점 및 클라우드 서비스에 구성 된 Acl</span><span class="sxs-lookup"><span data-stu-id="88142-242">1. Endpoints and ACLs configured on cloud services</span></span>  <br/> |<span data-ttu-id="88142-243">Classic</span><span class="sxs-lookup"><span data-stu-id="88142-243">Classic</span></span>  <br/> |
|<span data-ttu-id="88142-244">2. 네트워크 보안 그룹</span><span class="sxs-lookup"><span data-stu-id="88142-244">2. Network security groups</span></span>  <br/> |<span data-ttu-id="88142-245">리소스 관리자 및 클래식</span><span class="sxs-lookup"><span data-stu-id="88142-245">Resource Manager and classic</span></span>  <br/> |
|<span data-ttu-id="88142-246">3. 인바운드 NAT 규칙과 인터넷 연결 부하 분산 장치</span><span class="sxs-lookup"><span data-stu-id="88142-246">3. Internet-facing load balancer with inbound NAT rules</span></span>  <br/> |<span data-ttu-id="88142-247">자원 관리자</span><span class="sxs-lookup"><span data-stu-id="88142-247">Resource Manager</span></span>  <br/> |
|<span data-ttu-id="88142-248">4. 네트워크 보안 어플라이언스는 Azure의</span><span class="sxs-lookup"><span data-stu-id="88142-248">4. Network security appliances in the Azure</span></span> 
 <span data-ttu-id="88142-249">마켓플레이스 (표시 되지 않음)</span><span class="sxs-lookup"><span data-stu-id="88142-249">Marketplace (not shown)</span></span>  <br/> |<span data-ttu-id="88142-250">리소스 관리자 및 클래식</span><span class="sxs-lookup"><span data-stu-id="88142-250">Resource Manager and classic</span></span>  <br/> |
   
 <span data-ttu-id="88142-251">**표 5: 가상 컴퓨터 및 해당 Azure 배포 모델에 연결 하는 방법**</span><span class="sxs-lookup"><span data-stu-id="88142-251">**Table 5: Methods of connecting to virtual machines and their corresponding Azure deployment models**</span></span>
  
<span data-ttu-id="88142-252">**그림 7: 인터넷을 통해 Azure 가상 컴퓨터에 연결합니다.**</span><span class="sxs-lookup"><span data-stu-id="88142-252">**Figure 7: Connecting to Azure virtual machines over the Internet**</span></span>

![그림 7: 인터넷을 통한 Azure 가상 컴퓨터에 연결](images/c5e3531b-170a-4482-a6ff-fb8fbbe81b35.png)
  
<span data-ttu-id="88142-254">그림 7 끝점을 사용 하 여 클라우드 서비스에서 가상 컴퓨터, 네트워크 보안 그룹을 사용 하 여 서브넷에 가상 컴퓨터 및 가상 컴퓨터에는 외부 부하 분산 장치 및 인바운드 규칙의 NAT 사용 하는 서브넷에 연결 하는 인터넷에 연결 된 컴퓨터를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="88142-254">Figure 7 shows an Internet-connected computer connecting to a virtual machine in a cloud service using an endpoint, a virtual machine on a subnet using a network security group, and a virtual machine on a subnet using an external load balancer and inbound NAT rules.</span></span>
  
<span data-ttu-id="88142-255">추가 보안 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="88142-255">Additional security is provided by:</span></span>
  
- <span data-ttu-id="88142-256">원격 데스크톱 및 SSH 연결을 인증 하 고 암호화 하는 합니다.</span><span class="sxs-lookup"><span data-stu-id="88142-256">Remote Desktop and SSH connections, which are authenticated and encrypted.</span></span>
    
- <span data-ttu-id="88142-257">인증 되 고 암호화 하는 원격 PowerShell 세션입니다.</span><span class="sxs-lookup"><span data-stu-id="88142-257">Remote PowerShell sessions, which are authenticated and encrypted.</span></span>
    
- <span data-ttu-id="88142-258">IPsec 전송 모드-종단간 암호화에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88142-258">IPsec transport mode, which you can use for end-to-end encryption.</span></span>
    
- <span data-ttu-id="88142-259">외부 및 내부 공격을 방지 하 여 azure DDOS 보호,</span><span class="sxs-lookup"><span data-stu-id="88142-259">Azure DDOS protection, which helps prevent external and internal attacks</span></span>
    
<span data-ttu-id="88142-260">자세한 내용은 [엔터프라이즈 설계자에 대 한 Microsoft 클라우드 보안](https://aka.ms/cloudarchsecurity) 및 [Azure 네트워크 보안](https://azure.microsoft.com/blog/azure-network-security/)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="88142-260">For more information, see [Microsoft Cloud Security for Enterprise Architects](https://aka.ms/cloudarchsecurity) and [Azure Network Security](https://azure.microsoft.com/blog/azure-network-security/).</span></span>
  
### <a name="step-10-for-multiple-vnets-determine-the-vnet-to-vnet-connection-topology"></a><span data-ttu-id="88142-261">단계 10: 여러 VNets에 대 한 VNet-VNet 연결 토폴로지를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="88142-261">Step 10: For multiple VNets, determine the VNet-to-VNet connection topology.</span></span>

<span data-ttu-id="88142-262">VNets 연결 하는 조직의 사이트에 사용 되는 것과 유사한 토폴로지를 사용 하 여 서로 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88142-262">VNets can be connected to each other using topologies similar to those used for connecting the sites of an organization.</span></span>
  
<span data-ttu-id="88142-263">데이지 체인 구성 시리즈에서 VNets를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="88142-263">A daisy chain configuration connects the VNets in a series.</span></span>
  
<span data-ttu-id="88142-264">**그림 8: 데이지 체인에 대 한 구성을 VNets**</span><span class="sxs-lookup"><span data-stu-id="88142-264">**Figure 8: A daisy-chained configuration for VNets**</span></span>

![그림 8: Azure Virtual Network에 대한 데이지 체인 구성](images/264d5dd4-06c5-483f-9428-a18cc1f68ac1.png)
  
<span data-ttu-id="88142-266">그림 8 연속적으로 연결 된 구성을 사용 하 여 계열에 있는 연결 된 다섯 개의 VNets를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="88142-266">Figure 8 shows five VNets connected in series using a daisy-chained configuration.</span></span>
  
<span data-ttu-id="88142-267">여러 VNets 자체도 서로 게 연결 하는 중앙 VNets 집합에 연결 하는 허브 및 스포크 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="88142-267">A spoke and hub configuration connects multiple VNets to a set of central VNets, which are themselves connected to each other.</span></span>
  
<span data-ttu-id="88142-268">**그림 9: 허브 및 스포크에 대 한 구성을 VNets**</span><span class="sxs-lookup"><span data-stu-id="88142-268">**Figure 9: A spoke and hub configuration for VNets**</span></span>

![그림 9: Azure Virtual Network를 위한 스포크 및 허브 구성](images/dd442a38-5b76-4ac5-b743-8fc7711a91ba.png)
  
<span data-ttu-id="88142-270">그림 9 두 VNets는 대화 상대와 두 다른 스포크 VNets에 연결 된 허브 6 VNets를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="88142-270">Figure 9 shows six VNets, two VNets are hubs that are connected to each other and also two other spoke VNets.</span></span>
  
<span data-ttu-id="88142-271">모든 VNet 서로 게 연결 하는 풀 메시 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="88142-271">A full mesh configuration connects every VNet to each other.</span></span>
  
<span data-ttu-id="88142-272">**그림 10: 전체 메쉬 VNets에 대 한 구성**</span><span class="sxs-lookup"><span data-stu-id="88142-272">**Figure 10: A full mesh configuration for VNets**</span></span>

![그림 10: Azure Virtual Network를 위한 망 구성](images/9dda0738-10db-4a63-95b3-79851a399b71.png)
  
<span data-ttu-id="88142-274">그림 10 4 개의 VNets 6 VNet-VNet 연결의 합계를 사용 하 여, 서로 게 연결을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="88142-274">Figure 10 shows four VNets that are all connected to each other, using a total of six VNet-to-VNet connections.</span></span>
  
## <a name="planning-steps-for-a-cross-premises-vnet"></a><span data-ttu-id="88142-275">크로스-프레미스 VNet에 대 한 계획 단계</span><span class="sxs-lookup"><span data-stu-id="88142-275">Planning steps for a cross-premises VNet</span></span>
<span data-ttu-id="88142-276"><a name="cross_prem"> </a></span><span class="sxs-lookup"><span data-stu-id="88142-276"></span></span>

<span data-ttu-id="88142-277">크로스-프레미스 VNet에 대 한 다음이 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="88142-277">Follow these steps for a cross-premises VNet.</span></span>
  
> [!TIP]
> <span data-ttu-id="88142-278">시뮬레이션 된 크로스-프레미스 개발/테스트 환경을 만들려면 [Simulated 크로스-프레미스 Azure에 가상 네트워크를](simulated-cross-premises-virtual-network-in-azure.md)참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="88142-278">To create a simulated cross-premises dev/test environment, see [Simulated cross-premises virtual network in Azure](simulated-cross-premises-virtual-network-in-azure.md).</span></span> 
  
### <a name="step-1-determine-the-cross-premises-connection-to-the-vnet-s2s-vpn-or-expressroute"></a><span data-ttu-id="88142-279">1 단계: VNet (S2S VPN 또는 ExpressRoute)에 대 한 크로스-프레미스 연결을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="88142-279">Step 1: Determine the cross-premises connection to the VNet (S2S VPN or ExpressRoute).</span></span>

<span data-ttu-id="88142-280">표 6 다양 한 유형의 연결을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="88142-280">Table 6 lists the different types of connections.</span></span>
  
|<span data-ttu-id="88142-281">**연결 유형**</span><span class="sxs-lookup"><span data-stu-id="88142-281">**Type of connection**</span></span>|<span data-ttu-id="88142-282">**용도**</span><span class="sxs-lookup"><span data-stu-id="88142-282">**Purpose**</span></span>|
|:-----|:-----|
|<span data-ttu-id="88142-283">사이트 (S2S) VPN</span><span class="sxs-lookup"><span data-stu-id="88142-283">Site-to-Site (S2S) VPN</span></span>  <br/> |<span data-ttu-id="88142-284">단일 VNet에 (다른 VNets 포함)는 1 ~ 10 개의 사이트를 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="88142-284">Connect 1-10 sites (including other VNets) to a single VNet.</span></span>  <br/> |
|<span data-ttu-id="88142-285">ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="88142-285">ExpressRoute</span></span>  <br/> |<span data-ttu-id="88142-286">인터넷 Exchange 공급자 (IXP) 또는 네트워크 서비스 공급자 (NSP)를 통해 Azure에 안전 하 고 개인 링크입니다.</span><span class="sxs-lookup"><span data-stu-id="88142-286">A private, secure link to Azure via an Internet Exchange Provider (IXP) or a Network Service Provider (NSP).</span></span>  <br/> |
|<span data-ttu-id="88142-287">지점 사이트 (P2S) VPN</span><span class="sxs-lookup"><span data-stu-id="88142-287">Point-to-Site (P2S) VPN</span></span>  <br/> |<span data-ttu-id="88142-288">VNet 단일 컴퓨터에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="88142-288">Connects a single computer to a VNet.</span></span>  <br/> |
|<span data-ttu-id="88142-289">VNet 피어 링 또는 VNet VNet (V2V) VPN</span><span class="sxs-lookup"><span data-stu-id="88142-289">VNet peering or VNet-to-VNet (V2V) VPN</span></span>  <br/> |<span data-ttu-id="88142-290">다른 VNet에는 VNet를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="88142-290">Connects a VNet to another VNet.</span></span>  <br/> |
   
 <span data-ttu-id="88142-291">**표 6: 크로스-프레미스 VNets에 대 한 연결 유형**</span><span class="sxs-lookup"><span data-stu-id="88142-291">**Table 6: The types of connections for cross-premises VNets**</span></span>
  
<span data-ttu-id="88142-292">최대 연결 수에 대 한 자세한 내용은 [네트워킹 제한](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="88142-292">For more information on the maximum number of connections, see [Networking Limits](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits).</span></span>
  
<span data-ttu-id="88142-293">VPN 장치에 대 한 자세한 내용은 [사이트 마다 가상 네트워크 연결에 대 한 VPN 장치](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="88142-293">For more information about VPN devices, see [VPN devices for site-to-site virtual network connections](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).</span></span>
  
<span data-ttu-id="88142-294">피어 링 VNet 하는 방법에 대 한 자세한 내용은 [VNet 피어 링](https://docs.microsoft.com/azure/virtual-network/virtual-network-peering-overview)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="88142-294">For more information about VNet peering, see [VNet peering](https://docs.microsoft.com/azure/virtual-network/virtual-network-peering-overview).</span></span>
  
<span data-ttu-id="88142-295">**그림 11: 크로스-프레미스 VNet에 연결 하 네가지 방법**</span><span class="sxs-lookup"><span data-stu-id="88142-295">**Figure 11: The four ways to connect to a cross-premises VNet**</span></span>

![그림 11: 크로스-프레미스 Azure Virtual Network에 연결하는 세 가지 방법 ](images/d5d4a625-cfbd-4a77-9159-eaca69d07e93.png)
  
<span data-ttu-id="88142-297">그림 11에는 다음과 같은 네가지 유형의 연결 된 VNet 나와: P2S 연결 하는 컴퓨터에서 온-프레미스 네트워크에서는 S2S VPN 연결는 온-프레미스 네트워크에서는 ExpressRoute 연결 및 다른 VNet에서 VNet-VNet 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="88142-297">Figure 11 shows a VNet with the four types of connections: a P2S connection from a computer, an S2S VPN connection from an on-premises network, an ExpressRoute connection from an on-premises network, and a VNet-to-VNet connection from another VNet.</span></span> 
  
<span data-ttu-id="88142-298">다음과 같은 방법으로 VNet에서 Vm에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88142-298">You can connect to VMs in a VNet in the following ways:</span></span>
  
- <span data-ttu-id="88142-299">온-프레미스 네트워크 또는 인터넷에서 VNet Vm 관리</span><span class="sxs-lookup"><span data-stu-id="88142-299">Administration of VNet VMs from your on-premises network or the Internet</span></span>
    
- <span data-ttu-id="88142-300">온-프레미스 네트워크에서 IT 작업량 액세스</span><span class="sxs-lookup"><span data-stu-id="88142-300">IT workload access from your on-premises network</span></span>
    
- <span data-ttu-id="88142-301">추가 VNets 통해 네트워크의 확장을 필터링</span><span class="sxs-lookup"><span data-stu-id="88142-301">Extension of your network through additional VNets</span></span>
    
<span data-ttu-id="88142-302">연결에 대 한 보안은 다음에 의해 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="88142-302">Security for connections is provided by the following:</span></span>
  
- <span data-ttu-id="88142-303">P2S는 Secure Socket 터널링 프로토콜 (SSTP)를 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="88142-303">P2S uses the Secure Socket Tunneling Protocol (SSTP)</span></span> 
    
- <span data-ttu-id="88142-304">AES256와 IPsec 터널 모드를 사용 하는 S2S 및 VNet-VNet VPN 연결</span><span class="sxs-lookup"><span data-stu-id="88142-304">S2S and VNet-to-VNet VPN connections use IPsec tunnel mode with AES256</span></span>
    
- <span data-ttu-id="88142-305">ExpressRoute는 개인 WAN 연결</span><span class="sxs-lookup"><span data-stu-id="88142-305">ExpressRoute is a private WAN connection</span></span>
    
<span data-ttu-id="88142-306">자세한 내용은 [엔터프라이즈 설계자에 대 한 Microsoft 클라우드 보안](https://aka.ms/cloudarchsecurity) 및 [Azure 네트워크 보안](https://azure.microsoft.com/blog/azure-network-security/)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="88142-306">For more information, see [Microsoft Cloud Security for Enterprise Architects](https://aka.ms/cloudarchsecurity) and [Azure Network Security](https://azure.microsoft.com/blog/azure-network-security/).</span></span>
  
### <a name="step-2-determine-the-on-premises-vpn-device-or-router"></a><span data-ttu-id="88142-307">2 단계: 온-프레미스 VPN 장치 또는 라우터를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="88142-307">Step 2: Determine the on-premises VPN device or router.</span></span>

<span data-ttu-id="88142-308">온-프레미스 VPN 장치 또는 라우터 역할을 합니다.</span><span class="sxs-lookup"><span data-stu-id="88142-308">Your on-premises VPN device or router acts as:</span></span>
  
- <span data-ttu-id="88142-309">IPsec 피어 Azure 게이트웨이에서 S2S VPN 연결을 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="88142-309">An IPsec peer, terminating the S2S VPN connection from the Azure gateway.</span></span>
    
- <span data-ttu-id="88142-310">개인 피어 링 ExpressRoute 연결에 대 한 BPG 피어 및 종료 지점입니다.</span><span class="sxs-lookup"><span data-stu-id="88142-310">The BPG peer and termination point for the private peering ExpressRoute connection.</span></span>
    
<span data-ttu-id="88142-311">**그림 12: 온-프레미스 VPN 라우터 또는 장치**</span><span class="sxs-lookup"><span data-stu-id="88142-311">**Figure 12: The on-premises VPN router or device**</span></span>

![그림 12: 온-프레미스 VPN 라우터 또는 장치](images/bd221468-a660-4730-aa55-0426986480b9.png)
  
<span data-ttu-id="88142-313">그림 12는 온-프레미스 VPN 라우터 또는 장치에 연결 된 크로스-프레미스 VNet를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="88142-313">Figure 12 shows a cross-premises VNet connected to an on-premises VPN router or device.</span></span>
  
<span data-ttu-id="88142-314">자세한 내용은 [대 한 VPN 게이트웨이](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways)참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="88142-314">For more information, see [About VPN gateway](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways).</span></span>
  
### <a name="step-3-add-routes-to-your-intranet-to-make-the-address-space-of-the-vnet-reachable"></a><span data-ttu-id="88142-315">3 단계:는 VNet의 주소 공간에 접속할 수 있도록 하려면 인트라넷에 경로 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="88142-315">Step 3: Add routes to your intranet to make the address space of the VNet reachable.</span></span>

<span data-ttu-id="88142-316">온-프레미스에서 라우팅 VNets에는 다음의 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="88142-316">Routing to VNets from on-premises consists of the following:</span></span>
  
1. <span data-ttu-id="88142-317">VPN 장치를 향해 가리키는 VNet 주소 공간에 대 한 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="88142-317">A route for the VNet address space that points toward your VPN device.</span></span>
    
2. <span data-ttu-id="88142-318">S2S VPN 또는 ExpressRoute 연결을 통해 가리키는 VPN 장치에서 VNet 주소 공간에 대 한 경로</span><span class="sxs-lookup"><span data-stu-id="88142-318">A route for the VNet address space on your VPN device that points across the S2S VPN or ExpressRoute connection</span></span>
    
<span data-ttu-id="88142-319">**그림 13: 온-프레미스 경로 VNet에 접속할 수 있도록 하는 데 필요한**</span><span class="sxs-lookup"><span data-stu-id="88142-319">**Figure 13: The on-premises routes needed to make a VNet reachable**</span></span>

![그림 13: Azure VNet에 연결하는 데 필요한 온-프레미스 경로](images/7a1e20c1-fbc4-4cb9-9961-735da4e23307.png)
  
<span data-ttu-id="88142-321">그림 13 온-프레미스 라우터 및 VPN 라우터 또는 VNet의 주소 공간을 나타내는 장치에 필요한 라우팅 정보를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="88142-321">Figure 13 shows the routing information needed by the on-premises routers and the VPN router or device that represents the address space of the VNet.</span></span>
  
### <a name="step-4-for-expressroute-plan-for-the-new-connection-with-your-provider"></a><span data-ttu-id="88142-322">4 단계:에 대 한 ExpressRoute, 공급 업체에 문의 새 연결에 대 한 계획 합니다.</span><span class="sxs-lookup"><span data-stu-id="88142-322">Step 4: For ExpressRoute, plan for the new connection with your provider.</span></span>

<span data-ttu-id="88142-323">세 가지 방법으로 온-프레미스 네트워크 및 Microsoft 클라우드 간에 개인 피어 링와 ExpressRoute에 대 한 연결을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88142-323">You can create an ExpressRoute connection with private peering between your on-premises network and the Microsoft cloud in three different ways:</span></span>
  
- <span data-ttu-id="88142-324">클라우드 exchange에 함께 배치</span><span class="sxs-lookup"><span data-stu-id="88142-324">Co-located at a cloud exchange</span></span>
    
- <span data-ttu-id="88142-325">지점간 이더넷 연결</span><span class="sxs-lookup"><span data-stu-id="88142-325">Point-to-point Ethernet connections</span></span>
    
- <span data-ttu-id="88142-326">모든-를-모든 (IP VPN) 네트워크</span><span class="sxs-lookup"><span data-stu-id="88142-326">Any-to-any (IP VPN) networks</span></span>
    
<span data-ttu-id="88142-327">**그림 14: ExpressRoute를 사용 하 여 크로스-프레미스 VNet에 연결**</span><span class="sxs-lookup"><span data-stu-id="88142-327">**Figure 14: Using ExpressRoute to connect to a cross-premises VNet**</span></span>

![그림 14: ExpressRoute를 사용해 크로스-프레미스 Azure Virtual Network에 연결](images/7030bd39-69a6-4283-8567-3434e1ab6ba6.png)
  
<span data-ttu-id="88142-329">그림 14 크로스-프레미스 VNet 및 온-프레미스 라우터에서 Microsoft Azure로는 ExpressRoute 연결을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="88142-329">Figure 14 shows a cross-premises VNet and an ExpressRoute connection from an on-premises router to Microsoft Azure.</span></span>
  
<span data-ttu-id="88142-330">자세한 내용은 [Microsoft 클라우드 연결에 대 한 ExpressRoute](expressroute-for-microsoft-cloud-connectivity.md)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="88142-330">For more information, see [ExpressRoute for Microsoft cloud connectivity](expressroute-for-microsoft-cloud-connectivity.md).</span></span>
  
### <a name="step-5-determine-the-local-network-address-space-for-the-azure-gateway"></a><span data-ttu-id="88142-331">5 단계: Azure 게이트웨이에 대 한 로컬 네트워크 주소 공간을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="88142-331">Step 5: Determine the Local Network address space for the Azure gateway.</span></span>

<span data-ttu-id="88142-332">Azure는 라우팅에 대 한는 온-프레미스 또는 다른 VNets는 VNet에서, 게이트웨이에 할당 된 로컬 네트워크 주소 공간에 일치 하는 Azure 게이트웨이 통해 트래픽을 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="88142-332">For the routing to on-premises or other VNets from a VNet, Azure forwards traffic across an Azure gateway that matches the Local Network address space assigned to the gateway.</span></span>
  
<span data-ttu-id="88142-333">**그림 15: 크로스-프레미스 VNet는 로컬 네트워크 주소 공간**</span><span class="sxs-lookup"><span data-stu-id="88142-333">**Figure 15: The Local Network address space for a cross-premises VNet**</span></span>

![그림 15: 크로스-프레미스 Azure Virtual Network에 대한 로컬 네트워크 주소 공간](images/e3af2652-8b8e-4551-9a0b-b550e6e7e3c0.png)
  
<span data-ttu-id="88142-335">그림 15 온-프레미스 네트워크에 연결할 수 있는 주소 공간을 나타내는 Azure 게이트웨이에서 크로스-프레미스 VNet 및 로컬 네트워크 주소 공간을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="88142-335">Figure 15 shows a cross-premises VNet and the Local Network address space on the Azure gateway, which represents the reachable address space on the on-premises network.</span></span> 
  
<span data-ttu-id="88142-336">다음과 같은 방법으로 로컬 네트워크 주소 공간을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88142-336">You can define the Local Network address space in the following ways:</span></span>
  
- <span data-ttu-id="88142-337">옵션 1: 사용 (업데이트 필요할 수 새 서브넷을 추가 하는 경우) 또는 현재 필요한 주소 공간에 대 한 접두사 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="88142-337">Option 1: The list of prefixes for the address space currently needed or in use (updates might be needed when you add new subnets).</span></span>
    
- <span data-ttu-id="88142-338">옵션 2: 전체 온-프레미스 주소 공간 (업데이트 새 주소 공간을 추가 하는 경우에 필요).</span><span class="sxs-lookup"><span data-stu-id="88142-338">Option 2: Your entire on-premises address space (updates only needed when you add new address space).</span></span>
    
<span data-ttu-id="88142-339">Azure 게이트웨이 요약 된 경로 허용 하지 않으므로 VNet 주소 공간을 포함 하지 않는 되도록 옵션 2에 대 한 로컬 네트워크 주소 공간을 정의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="88142-339">Because the Azure gateway does not allow summarized routes, you must define the Local Network address space for option 2 so that it does not include the VNet address space.</span></span>
  
<span data-ttu-id="88142-340">**그림 16: 주소 공간 구멍 VNet 주소 공간에서 만든**</span><span class="sxs-lookup"><span data-stu-id="88142-340">**Figure 16: The address space hole created by the VNet address space**</span></span>

![그림 16: Virtual Network 공간에서 만든 주소 공간 구멍](images/e79c4840-f9e3-4741-9b72-59db6043aefa.png)
  
<span data-ttu-id="88142-342">그림 16 루트 공간을 사용 하는 주소 공간, 및 VNet 주소 공간 표시를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="88142-342">Figure 16 shows a representation of an address space, with the root space and the VNet address space.</span></span>
  
<span data-ttu-id="88142-343">다음은 주소 공간 "구멍"는 VNet 하 여 만든 주위 로컬 네트워크 주소 공간에 대 한 접두사를 정의 하는 예제가입니다.</span><span class="sxs-lookup"><span data-stu-id="88142-343">Here is an example of defining the prefixes for the Local Network address space around the address space "hole" created by the VNet:</span></span>
  
- <span data-ttu-id="88142-p114">개인 주소 공간 (10.0.0.0/8, 172.16.0.0/12, 및 192.168.0.0/16)의 일부를 사용 하 여 자신의 온-프레미스 네트워크를 통해 조직 합니다. 이러한 옵션 2 및 10.100.100.0/24 자신의 VNet 주소 공간 했습니다.</span><span class="sxs-lookup"><span data-stu-id="88142-p114">An organization uses portions of the private address space (10.0.0.0/8, 172.16.0.0/12, and 192.168.0.0/16) across their on-premises network. They chose option 2 and 10.100.100.0/24 as their VNet address space.</span></span>
    
<span data-ttu-id="88142-346">표 7 단계 및이 예제에 대 한 로컬 네트워크 주소 공간을 정의 하는 접두사를 결과 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="88142-346">Table 7 shows the steps and resulting prefixes that define the Local Network address space for this example.</span></span>
  
|<span data-ttu-id="88142-347">**단계**</span><span class="sxs-lookup"><span data-stu-id="88142-347">**Step**</span></span>|<span data-ttu-id="88142-348">**결과**</span><span class="sxs-lookup"><span data-stu-id="88142-348">**Results**</span></span>|
|:-----|:-----|
|<span data-ttu-id="88142-349">1. VNet 주소 공간에 대 한 루트 공간 없는 접두사를 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="88142-349">1. List the prefixes that are not the root space for the VNet address space.</span></span>  <br/> |<span data-ttu-id="88142-350">172.16.0.0/12 및 192.168.0.0/16</span><span class="sxs-lookup"><span data-stu-id="88142-350">172.16.0.0/12 and 192.168.0.0/16</span></span>  <br/> |
|<span data-ttu-id="88142-351">2. 변수 옥텟에 대 한 겹치지 않는 접두사를 최대 목록은 아니지만 사용 되는 마지막을 포함 하지 않음</span><span class="sxs-lookup"><span data-stu-id="88142-351">2. List the non-overlapping prefixes for variable octets up to but not including the last used</span></span> 
 <span data-ttu-id="88142-352">8 진수 VNet 주소 공간에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88142-352">octet in the VNet address space.</span></span>  <br/> |<span data-ttu-id="88142-353">10.0.0.0/16, 10.1.0.0/16... 10.99.0.0/16, 10.101.0.0/16... 10.254.0.0/16, 10.255.0.0/16 (255 접두사, 10.100.0.0/16 건너뛰기)</span><span class="sxs-lookup"><span data-stu-id="88142-353">10.0.0.0/16, 10.1.0.0/16…10.99.0.0/16, 10.101.0.0/16…10.254.0.0/16, 10.255.0.0/16 (255 prefixes, skipping 10.100.0.0/16)</span></span>  <br/> |
|<span data-ttu-id="88142-354">3. 목록 내에서 접두사 아닌 겹치는</span><span class="sxs-lookup"><span data-stu-id="88142-354">3. List the non-overlapping prefixes within the</span></span> 
 <span data-ttu-id="88142-355">마지막 옥텟 VNet 주소 공간으로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="88142-355">last used octet of the VNet address space.</span></span>  <br/> <span data-ttu-id="88142-356">| 10.100.0.0/24, 10.100.1.0/24... 10.100.99.0/24, 10.100.101.0/24... 10.100.254.0/24, 10.100.0.255.0/24 (255 접두사, 10.100.100.0/24 건너뛰기)</span><span class="sxs-lookup"><span data-stu-id="88142-356">|10.100.0.0/24, 10.100.1.0/24…10.100.99.0/24, 10.100.101.0/24…10.100.254.0/24, 10.100.0.255.0/24 (255 prefixes, skipping 10.100.100.0/24)</span></span>  <br/> |
   
 <span data-ttu-id="88142-357">**표 7: 예에서는 로컬 주소 네트워크 공간**</span><span class="sxs-lookup"><span data-stu-id="88142-357">**Table 7: Example Local Address network space**</span></span>
  
### <a name="step-6-configure-on-premises-dns-servers-for-dns-replication-with-dns-servers-hosted-in-azure"></a><span data-ttu-id="88142-358">6 단계: Azure에서 호스팅되는 DNS 서버와 DNS 복제를 위해 온-프레미스 DNS 서버를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="88142-358">Step 6: Configure on-premises DNS servers for DNS replication with DNS servers hosted in Azure.</span></span>

<span data-ttu-id="88142-359">온-프레미스 컴퓨터 Azure 기반 서버의 이름을 확인할 수 있고 Azure 기반 서버에는 온-프레미스 컴퓨터의 이름을 확인할 수를 확인, 다음을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="88142-359">To ensure that on-premises computers can resolve the names of Azure-based servers and Azure-based servers can resolve the names of on-premises computers, configure:</span></span>
  
- <span data-ttu-id="88142-360">온-프레미스 DNS 서버에 전달 하 여 VNet에서 DNS 서버</span><span class="sxs-lookup"><span data-stu-id="88142-360">The DNS servers in your VNet to forward to on-premises DNS servers</span></span>
    
- <span data-ttu-id="88142-361">DNS 서버 온-프레미스 간 및는 VNet에서 적절 한 영역의 DNS 복제</span><span class="sxs-lookup"><span data-stu-id="88142-361">DNS replication of the appropriate zones between DNS servers on-premises and in the VNet</span></span>
    
<span data-ttu-id="88142-362">**그림 17: DNS 복제 및 크로스-프레미스 VNet에서 DNS 서버에 대 한 착신 전환**</span><span class="sxs-lookup"><span data-stu-id="88142-362">**Figure 17: DNS replication and forwarding for a DNS server in a cross-premises VNet**</span></span>

![그림 17: 크로스-프레미스 Azure Virtual Network의 DNS 서버에 대한 DNS 복제 및 전달](images/ab55e5ce-ccb0-49d4-a301-657a727f97b2.png)
  
<span data-ttu-id="88142-p115">그림 17은 VNet의 서브넷 및 온-프레미스 네트워크에 있는 DNS 서버와 크로스-프레미스 VNet를 표시합니다. DNS 복제 및 전달 두 DNS 서버 간에 구성 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="88142-p115">Figure 17 shows a cross-premises VNet with DNS servers in the on-premises network and on a subnet in the VNet. DNS replication and forwarding has been configured between the two DNS servers.</span></span>
  
### <a name="step-7-determine-the-use-of-forced-tunneling"></a><span data-ttu-id="88142-366">7 단계: 강제 적용 된 터널링의 사용을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="88142-366">Step 7: Determine the use of forced tunneling.</span></span>

<span data-ttu-id="88142-p116">Azure 서브넷에 대 한 기본 시스템 경로 인터넷을 가리킵니다. 모든 가상 컴퓨터에서의 트래픽은 크로스-프레미스 연결을 통해 되도록 그 다음 홉 주소로 Azure 게이트웨이 사용 하는 기본 경로와 라우팅 테이블을 만듭니다. 다음은 서브넷과 경로 테이블을 연결합니다. 터널링 강제로으로 알려져 있습니다. 자세한 내용은 [Configure 강제 터널링](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-forced-tunneling-rm)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="88142-p116">The default system route for Azure subnets points to the Internet. To ensure that all traffic from virtual machines travels across the cross-premises connection, create a routing table with the default route that uses the Azure gateway as its next-hop address. You then associate the route table with the subnet. This is known as forced tunneling. For more information, see [Configure forced tunneling](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-forced-tunneling-rm).</span></span>
  
<span data-ttu-id="88142-372">**그림 18: 사용자 정의 경로 및 크로스-프레미스 VNet에 대 한 강제 적용 된 터널링**</span><span class="sxs-lookup"><span data-stu-id="88142-372">**Figure 18: User-defined routes and forced tunneling for a cross-premises VNet**</span></span>

![그림 18: 크로스-프레미스 Azure Virtual Network에 대한 강제 터널링 및 사용자 정의 경로](images/1e545ec6-c2d9-48d2-bb5e-e0a581fee004.png)
  
<span data-ttu-id="88142-374">그림 18 Azure 게이트웨이를 가리키도록 설정 하는 서브넷에 대 한 사용자 정의 경로와 크로스-프레미스 VNet를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="88142-374">Figure 18 shows a cross-premises VNet with a user-defined route for a subnet pointing to the Azure gateway.</span></span>
  
## <a name="sharepoint-server-2016-farm-in-azure"></a><span data-ttu-id="88142-375">Azure의 SharePoint Server 2016 팜</span><span class="sxs-lookup"><span data-stu-id="88142-375">SharePoint Server 2016 farm in Azure</span></span>
<span data-ttu-id="88142-376"><a name="cross_prem"> </a></span><span class="sxs-lookup"><span data-stu-id="88142-376"></span></span>

<span data-ttu-id="88142-377">인트라넷 Azure IaaS에서 호스팅되는 IT 작업의 예로 항상 사용 가능, 다중 계층 SharePoint Server 2016 팜 그림 19와 같이 합니다.</span><span class="sxs-lookup"><span data-stu-id="88142-377">An example of an intranet IT workload hosted in Azure IaaS is a highly-available, multi-tier SharePoint Server 2016 farm, as shown in Figure 19.</span></span>
  
<span data-ttu-id="88142-378">**그림 19: Azure IaaS의 가용성이 인트라넷 SharePoint Server 2016 팜**</span><span class="sxs-lookup"><span data-stu-id="88142-378">**Figure 19: A highly-available intranet SharePoint Server 2016 farm in Azure IaaS**</span></span>

![Azure IaaS에 팜 된 고가용성 SharePoint Server 2016 ](images/3a922e21-df91-455f-ba90-78abdd48d98d.png)
  
<span data-ttu-id="88142-p117">그림 19 프런트엔드 및 데이터 계층에 대 한 내부 부하 분산 장치를 사용 하는 크로스-프레미스 VNet에 배포 된 SharePoint Server 2016 팜 9 명의 서버를 표시 합니다. 단계별 디자인 및 배포 지침을 비롯 한 자세한 내용은 [Microsoft Azure의 SharePoint Server 2016](https://technet.microsoft.com/library/mt779107%28v=office.16%29.aspx)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="88142-p117">Figure 19 shows the nine servers of a SharePoint Server 2016 farm deployed in a cross-premises VNet that uses internal load balancers for the front-end and data tiers. For more information, including step-by-step design and deployment instructions, see [SharePoint Server 2016 in Microsoft Azure](https://technet.microsoft.com/library/mt779107%28v=office.16%29.aspx).</span></span>
  
> [!TIP]
> <span data-ttu-id="88142-382">시뮬레이션 된 크로스-프레미스 VNet에서 단일 서버 SharePoint Server 2016 팜을 만들려면 [Azure 개발/테스트 환경에서 인트라넷 SharePoint Server 2016](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx)를 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="88142-382">To create a single-server SharePoint Server 2016 farm in a simulated cross-premises VNet, see [Intranet SharePoint Server 2016 in Azure dev/test environment](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx).</span></span> 
  
<span data-ttu-id="88142-383">가상는 크로스-프레미스 Azure에 가상 컴퓨터에 배포 하는 IT 작업의 추가 예제를 보려면 네트워크 [Azure IaaS에 대 한 하이브리드 클라우드 시나리오](https://technet.microsoft.com/library/mt750502.aspx)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="88142-383">For additional examples of IT workloads deployed on virtual machines in a cross-premises Azure virtual network, see [Hybrid cloud scenarios for Azure IaaS](https://technet.microsoft.com/library/mt750502.aspx).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="88142-384">See Also</span><span class="sxs-lookup"><span data-stu-id="88142-384">See Also</span></span>

<span data-ttu-id="88142-385"><a name="cross_prem"> </a></span><span class="sxs-lookup"><span data-stu-id="88142-385"></span></span>

[<span data-ttu-id="88142-386">Microsoft 클라우드 엔터프라이즈 설계자에 대 한 네트워킹</span><span class="sxs-lookup"><span data-stu-id="88142-386">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="88142-387">Microsoft 클라우드 IT 아키텍처 리소스</span><span class="sxs-lookup"><span data-stu-id="88142-387">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="88142-388">Microsoft의 엔터프라이즈 클라우드 로드맵: IT 의사 결정권자를 위한 리소스</span><span class="sxs-lookup"><span data-stu-id="88142-388">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



