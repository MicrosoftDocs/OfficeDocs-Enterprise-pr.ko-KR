---
title: "고가용성 연결 된 인증 단계 1 구성 Azure"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: 91266aac-4d00-4b5f-b424-86a1a837792c
description: "요약: Microsoft Azure 인프라 호스트에 대 한 고가용성 정보를 구성 하는 Office 365에 대 한 연결 된 인증 합니다."
ms.openlocfilehash: 829bad1dadc3c3987e42d32f8afe8c1f76459ff0
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/09/2018
---
# <a name="high-availability-federated-authentication-phase-1-configure-azure"></a><span data-ttu-id="7b070-103">고가용성 페더레이션 인증 1단계: Azure 구성</span><span class="sxs-lookup"><span data-stu-id="7b070-103">High availability federated authentication Phase 1: Configure Azure</span></span>

 <span data-ttu-id="7b070-104">**요약:** Office 365에 대 한 호스트 고가용성 페더레이션 인증 하는 Microsoft Azure 인프라를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b070-104">**Summary:** Configure the Microsoft Azure infrastructure to host high availability federated authentication for Office 365.</span></span>
  
<span data-ttu-id="7b070-p101">이 단계에서는 자원 그룹, 저장소 계정, 2, 3 및 4 단계에서 가상 컴퓨터를 호스팅할 Azure에 가상 네트워크 (VNet) 및 가용성 집합을 만듭니다. 레코드로 이동 하기 전에이 단계를 완료 해야 [고가용성 페더레이션 인증 2 단계: 도메인 컨트롤러 구성](high-availability-federated-authentication-phase-2-configure-domain-controllers.md)합니다. 모든 단계에 대 한 [Azure의 Office 365에 대 한 고가용성 연결 된 인증 배포를](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="7b070-p101">In this phase, you create the resource groups, storage accounts, virtual network (VNet), and availability sets in Azure that will host the virtual machines in phases 2, 3, and 4. You must complete this phase before moving on to [High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md). See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
<span data-ttu-id="7b070-108">이러한 기본 구성 요소와 함께 azure 프로 비전 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b070-108">Azure must be provisioned with these basic components:</span></span>
  
- <span data-ttu-id="7b070-109">리소스 그룹</span><span class="sxs-lookup"><span data-stu-id="7b070-109">Resource groups</span></span>
    
- <span data-ttu-id="7b070-110">Azure Virtual Machines를 호스팅하기 위한 서브넷이 있는 프레미스 간 Azure Virtual Network(VNet)</span><span class="sxs-lookup"><span data-stu-id="7b070-110">A cross-premises Azure virtual network (VNet) with subnets for hosting the Azure virtual machines</span></span>
    
- <span data-ttu-id="7b070-111">수행 중인 서브넷 격리용 네트워크 보안 그룹</span><span class="sxs-lookup"><span data-stu-id="7b070-111">Network security groups for performing subnet isolation</span></span>
    
- <span data-ttu-id="7b070-112">가용성 집합</span><span class="sxs-lookup"><span data-stu-id="7b070-112">Availability sets</span></span>
    
## <a name="configure-azure-components"></a><span data-ttu-id="7b070-113">Azure 구성 요소 구성</span><span class="sxs-lookup"><span data-stu-id="7b070-113">Configure Azure components</span></span>

<span data-ttu-id="7b070-p102">Azure 구성 요소를 시작 하기 전에 다음 표를 입력 합니다. 에 도움을 주고 Azure를 구성 하는 절차를이 섹션을 인쇄 하 고 필요한 정보를 적어둡니다 또는 문서에이 섹션에 복사 하 고에 내용을 입력 합니다. VNet의 설정에 대해 테이블 V를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b070-p102">Before you begin configuring Azure components, fill in the following tables. To assist you in the procedures for configuring Azure, print this section and write down the needed information or copy this section to a document and fill it in. For the settings of the VNet, fill in Table V.</span></span>
  
|<span data-ttu-id="7b070-117">**항목**</span><span class="sxs-lookup"><span data-stu-id="7b070-117">**Item**</span></span>|<span data-ttu-id="7b070-118">**구성 설정**</span><span class="sxs-lookup"><span data-stu-id="7b070-118">**Configuration setting**</span></span>|<span data-ttu-id="7b070-119">**설명**</span><span class="sxs-lookup"><span data-stu-id="7b070-119">**Description**</span></span>|<span data-ttu-id="7b070-120">**값**</span><span class="sxs-lookup"><span data-stu-id="7b070-120">**Value**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="7b070-121">1.</span><span class="sxs-lookup"><span data-stu-id="7b070-121">1.</span></span>  <br/> |<span data-ttu-id="7b070-122">VNet 이름</span><span class="sxs-lookup"><span data-stu-id="7b070-122">VNet name</span></span>  <br/> |<span data-ttu-id="7b070-123">VNet에 할당할 이름(예: FedAuthNet)입니다.</span><span class="sxs-lookup"><span data-stu-id="7b070-123">A name to assign to the VNet (example FedAuthNet).</span></span>  <br/> |<span data-ttu-id="7b070-124">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7b070-124"></span></span>  <br/> |
|<span data-ttu-id="7b070-125">2.</span><span class="sxs-lookup"><span data-stu-id="7b070-125">2.</span></span>  <br/> |<span data-ttu-id="7b070-126">VNet 위치</span><span class="sxs-lookup"><span data-stu-id="7b070-126">VNet location</span></span>  <br/> |<span data-ttu-id="7b070-127">지역 Azure 데이터 센터에 가상 네트워크가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b070-127">The regional Azure datacenter that will contain the virtual network.</span></span>  <br/> |<span data-ttu-id="7b070-128">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7b070-128"></span></span>  <br/> |
|<span data-ttu-id="7b070-129">3.</span><span class="sxs-lookup"><span data-stu-id="7b070-129">3.</span></span>  <br/> |<span data-ttu-id="7b070-130">VPN 장치 IP 주소</span><span class="sxs-lookup"><span data-stu-id="7b070-130">VPN device IP address</span></span>  <br/> |<span data-ttu-id="7b070-131">인터넷에서 VPN 장치 인터페이스의 공용 IPv4 주소입니다. </span><span class="sxs-lookup"><span data-stu-id="7b070-131">The public IPv4 address of your VPN device's interface on the Internet.</span></span>  <br/> |<span data-ttu-id="7b070-132">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7b070-132"></span></span>  <br/> |
|<span data-ttu-id="7b070-133">4.</span><span class="sxs-lookup"><span data-stu-id="7b070-133">4.</span></span>  <br/> |<span data-ttu-id="7b070-134">VNet 주소 공간</span><span class="sxs-lookup"><span data-stu-id="7b070-134">VNet address space</span></span>  <br/> |<span data-ttu-id="7b070-p103">가상 네트워크의 주소 공간입니다. IT 부서에서 이 주소 공간을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="7b070-p103">The address space for the virtual network. Work with your IT department to determine this address space.</span></span>  <br/> |<span data-ttu-id="7b070-137">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7b070-137"></span></span>  <br/> |
|<span data-ttu-id="7b070-138">5.</span><span class="sxs-lookup"><span data-stu-id="7b070-138">5.</span></span>  <br/> |<span data-ttu-id="7b070-139">IPsec 공유 키</span><span class="sxs-lookup"><span data-stu-id="7b070-139">IPsec shared key</span></span>  <br/> |<span data-ttu-id="7b070-p104">32 자 임의의 영숫자 문자열 사이트 마다 VPN 연결의 양쪽 모두를 인증 하는데 사용 되는입니다. IT 작업 또는 보안 부서가 키 값을 결정 합니다. 또는 [IPsec 미리 공유한 키에 대 한 임의의 문자열 만들기](http://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="7b070-p104">A 32-character random, alphanumeric string that will be used to authenticate both sides of the site-to-site VPN connection. Work with your IT or security department to determine this key value. Alternately, see [Create a random string for an IPsec preshared key](http://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx).  </span></span><br/> |<span data-ttu-id="7b070-143">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7b070-143"></span></span>  <br/> |
   
 <span data-ttu-id="7b070-144">**테이블 V: 프레미스 간 가상 네트워크 구성**</span><span class="sxs-lookup"><span data-stu-id="7b070-144">**Table V: Cross-premises virtual network configuration**</span></span>
  
<span data-ttu-id="7b070-p105">다음으로 이 솔루션의 서브넷에 대해서는 테이블 S를 채웁니다. 모든 주소 공간은 CIDR(Classless Interdomain Routing) 형식이어야 하며 네트워크 접두사 형식이라고도 합니다. 예를 들어 10.24.64.0/20입니다.</span><span class="sxs-lookup"><span data-stu-id="7b070-p105">Next, fill in Table S for the subnets of this solution. All address spaces should be in Classless Interdomain Routing (CIDR) format, also known as network prefix format. An example is 10.24.64.0/20.</span></span>
  
<span data-ttu-id="7b070-p106">처음 세 개의 서브넷의 경우 가상 네트워크 주소 공간에 따라 이름과 단일 IP 주소 공간을 지정합니다. 게이트웨이 서브넷의 경우 Azure 게이트웨이 서브넷의 27비트 주소 공간(/27 접두사 길이)을 다음과 같이 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="7b070-p106">For the first three subnets, specify a name and a single IP address space based on the virtual network address space. For the gateway subnet, determine the 27-bit address space (with a /27 prefix length) for the Azure gateway subnet with the following:</span></span>
  
1. <span data-ttu-id="7b070-150">VNet의 주소 공간에 있는 변수 비트를 1(게이트웨이 서브넷에서 사용하는 비트까지)로 설정한 다음 나머지 비트를 0으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="7b070-150">Set the variable bits in the address space of the VNet to 1, up to the bits being used by the gateway subnet, then set the remaining bits to 0.</span></span>
    
2. <span data-ttu-id="7b070-151">결과 비트를 10진수로 변환하고 이를 접두사 길이가 게이트웨이 서브넷 크기로 설정된 주소 공간으로 표현합니다.</span><span class="sxs-lookup"><span data-stu-id="7b070-151">Convert the resulting bits to decimal and express it as an address space with the prefix length set to the size of the gateway subnet.</span></span>
    
<span data-ttu-id="7b070-152">PowerShell 명령 블록 및 하면이 계산을 수행 하는 C# 또는 Python 콘솔 응용 프로그램에 대 한 [Azure 게이트웨이 서브넷에 대 한 주소 공간 계산기](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) 를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="7b070-152">See [Address space calculator for Azure gateway subnets](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) for a PowerShell command block and C# or Python console application that performs this calculation for you.</span></span>
  
<span data-ttu-id="7b070-153">IT 부서에서 가상 네트워크 주소 공간의 이러한 주소 공간을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="7b070-153">Work with your IT department to determine these address spaces from the virtual network address space.</span></span>
  
|<span data-ttu-id="7b070-154">**항목**</span><span class="sxs-lookup"><span data-stu-id="7b070-154">**Item**</span></span>|<span data-ttu-id="7b070-155">**서브넷 이름**</span><span class="sxs-lookup"><span data-stu-id="7b070-155">**Subnet name**</span></span>|<span data-ttu-id="7b070-156">**서브넷 주소 공간**</span><span class="sxs-lookup"><span data-stu-id="7b070-156">**Subnet address space**</span></span>|<span data-ttu-id="7b070-157">**용도**</span><span class="sxs-lookup"><span data-stu-id="7b070-157">**Purpose**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="7b070-158">1.</span><span class="sxs-lookup"><span data-stu-id="7b070-158">1.</span></span>  <br/> |<span data-ttu-id="7b070-159">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7b070-159"></span></span>  <br/> |<span data-ttu-id="7b070-160">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7b070-160"></span></span>  <br/> |<span data-ttu-id="7b070-161">Windows Server Active Directory(AD) 도메인 컨트롤러 및 DirSync 서버 가상 컴퓨터(VM)에서 사용하는 서브넷입니다.</span><span class="sxs-lookup"><span data-stu-id="7b070-161">The subnet used by the Windows Server Active Directory (AD) domain controller and DirSync server virtual machines (VMs).</span></span>  <br/> |
|<span data-ttu-id="7b070-162">2.</span><span class="sxs-lookup"><span data-stu-id="7b070-162">2.</span></span>  <br/> |<span data-ttu-id="7b070-163">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7b070-163"></span></span>  <br/> |<span data-ttu-id="7b070-164">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7b070-164"></span></span>  <br/> |<span data-ttu-id="7b070-165">AD FS VM에서 사용하는 서브넷입니다.</span><span class="sxs-lookup"><span data-stu-id="7b070-165">The subnet used by the AD FS VMs.</span></span>  <br/> |
|<span data-ttu-id="7b070-166">3.</span><span class="sxs-lookup"><span data-stu-id="7b070-166">3.</span></span>  <br/> |<span data-ttu-id="7b070-167">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7b070-167"></span></span>  <br/> |<span data-ttu-id="7b070-168">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7b070-168"></span></span>  <br/> |<span data-ttu-id="7b070-169">웹 응용 프로그램 프록시 VM에서 사용하는 서브넷입니다.</span><span class="sxs-lookup"><span data-stu-id="7b070-169">The subnet used by the web application proxy VMs.</span></span>  <br/> |
|<span data-ttu-id="7b070-170">4.</span><span class="sxs-lookup"><span data-stu-id="7b070-170">4.</span></span>  <br/> |<span data-ttu-id="7b070-171">GatewaySubnet</span><span class="sxs-lookup"><span data-stu-id="7b070-171">GatewaySubnet</span></span>  <br/> |<span data-ttu-id="7b070-172">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7b070-172"></span></span>  <br/> |<span data-ttu-id="7b070-173">Azure 게이트웨이 VM에서 사용하는 서브넷입니다.</span><span class="sxs-lookup"><span data-stu-id="7b070-173">The subnet used by the Azure gateway VMs.</span></span>  <br/> |
   
 <span data-ttu-id="7b070-174">**테이블 S: 가상 네트워크의 서브넷**</span><span class="sxs-lookup"><span data-stu-id="7b070-174">**Table S: Subnets in the virtual network**</span></span>
  
<span data-ttu-id="7b070-175">다음으로 가상 컴퓨터와 부하 분산 장치 인스턴스에 할당된 고정 IP 주소에 대해서는 테이블 I를 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="7b070-175">Next, fill in Table I for the static IP addresses assigned to virtual machines and load balancer instances.</span></span>
  
|<span data-ttu-id="7b070-176">**항목**</span><span class="sxs-lookup"><span data-stu-id="7b070-176">**Item**</span></span>|<span data-ttu-id="7b070-177">**용도**</span><span class="sxs-lookup"><span data-stu-id="7b070-177">**Purpose**</span></span>|<span data-ttu-id="7b070-178">**서브넷에 IP 주소**</span><span class="sxs-lookup"><span data-stu-id="7b070-178">**IP address on the subnet**</span></span>|<span data-ttu-id="7b070-179">**값**</span><span class="sxs-lookup"><span data-stu-id="7b070-179">**Value**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="7b070-180">1.</span><span class="sxs-lookup"><span data-stu-id="7b070-180">1.</span></span>  <br/> |<span data-ttu-id="7b070-181">첫 번째 도메인 컨트롤러의 고정 IP 주소</span><span class="sxs-lookup"><span data-stu-id="7b070-181">Static IP address of the first domain controller</span></span>  <br/> |<span data-ttu-id="7b070-182">테이블 S의 항목 1에 정의된 서브넷의 주소 공간에 사용할 수 있는 네 번째 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="7b070-182">The fourth possible IP address for the address space of the subnet defined in Item 1 of Table S.</span></span>  <br/> |<span data-ttu-id="7b070-183">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7b070-183"></span></span>  <br/> |
|<span data-ttu-id="7b070-184">2.</span><span class="sxs-lookup"><span data-stu-id="7b070-184">2.</span></span>  <br/> |<span data-ttu-id="7b070-185">두 번째 도메인 컨트롤러의 고정 IP 주소</span><span class="sxs-lookup"><span data-stu-id="7b070-185">Static IP address of the second domain controller</span></span>  <br/> |<span data-ttu-id="7b070-186">테이블 S의 항목 1에 정의된 서브넷의 주소 공간에 사용할 수 있는 다섯 번째 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="7b070-186">The fifth possible IP address for the address space of the subnet defined in Item 1 of Table S.</span></span>  <br/> |<span data-ttu-id="7b070-187">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7b070-187"></span></span>  <br/> |
|<span data-ttu-id="7b070-188">3.</span><span class="sxs-lookup"><span data-stu-id="7b070-188">3.</span></span>  <br/> |<span data-ttu-id="7b070-189">DirSync 서버의 고정 IP 주소</span><span class="sxs-lookup"><span data-stu-id="7b070-189">Static IP address of the DirSync server</span></span>  <br/> |<span data-ttu-id="7b070-190">테이블 S의 항목 1에 정의된 서브넷의 주소 공간에 사용할 수 있는 여섯 번째 IP 주소입니다. </span><span class="sxs-lookup"><span data-stu-id="7b070-190">The sixth possible IP address for the address space of the subnet defined in Item 1 of Table S.</span></span>  <br/> |<span data-ttu-id="7b070-191">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7b070-191"></span></span>  <br/> |
|<span data-ttu-id="7b070-192">4.</span><span class="sxs-lookup"><span data-stu-id="7b070-192">4.</span></span>  <br/> |<span data-ttu-id="7b070-193">AD FS 서버용 내부 부하 분산 장치의 고정 IP 주소</span><span class="sxs-lookup"><span data-stu-id="7b070-193">Static IP address of the internal load balancer for the AD FS servers</span></span>  <br/> |<span data-ttu-id="7b070-194">테이블 S의 항목 2에 정의된 서브넷의 주소 공간에 사용할 수 있는 네 번째 IP 주소입니다. </span><span class="sxs-lookup"><span data-stu-id="7b070-194">The fourth possible IP address for the address space of the subnet defined in Item 2 of Table S.</span></span>  <br/> |<span data-ttu-id="7b070-195">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7b070-195"></span></span>  <br/> |
|<span data-ttu-id="7b070-196">5.</span><span class="sxs-lookup"><span data-stu-id="7b070-196">5.</span></span>  <br/> |<span data-ttu-id="7b070-197">첫 번째 AD FS 서버의 고정 IP 주소</span><span class="sxs-lookup"><span data-stu-id="7b070-197">Static IP address of the first AD FS server</span></span>  <br/> |<span data-ttu-id="7b070-198">테이블 S의 항목 2에 정의된 서브넷의 주소 공간에 사용할 수 있는 다섯 번째 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="7b070-198">The fifth possible IP address for the address space of the subnet defined in Item 2 of Table S.</span></span>  <br/> |<span data-ttu-id="7b070-199">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7b070-199"></span></span>  <br/> |
|<span data-ttu-id="7b070-200">6.</span><span class="sxs-lookup"><span data-stu-id="7b070-200">6.</span></span>  <br/> |<span data-ttu-id="7b070-201">두 번째 AD FS 서버의 고정 IP 주소</span><span class="sxs-lookup"><span data-stu-id="7b070-201">Static IP address of the second AD FS server</span></span>  <br/> |<span data-ttu-id="7b070-202">테이블 S의 항목 2에 정의된 서브넷의 주소 공간에 사용할 수 있는 여섯 번째 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="7b070-202">The sixth possible IP address for the address space of the subnet defined in Item 2 of Table S.</span></span>  <br/> |<span data-ttu-id="7b070-203">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7b070-203"></span></span>  <br/> |
|<span data-ttu-id="7b070-204">7.</span><span class="sxs-lookup"><span data-stu-id="7b070-204">7.</span></span>  <br/> |<span data-ttu-id="7b070-205">첫 번째 웹 응용 프로그램 프록시 서버의 고정 IP 주소</span><span class="sxs-lookup"><span data-stu-id="7b070-205">Static IP address of the first web application proxy server</span></span>  <br/> |<span data-ttu-id="7b070-206">테이블 S의 항목 3에 정의된 서브넷의 주소 공간에 사용할 수 있는 네 번째 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="7b070-206">The fourth possible IP address for the address space of the subnet defined in Item 3 of Table S.</span></span>  <br/> |<span data-ttu-id="7b070-207">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7b070-207"></span></span>  <br/> |
|<span data-ttu-id="7b070-208">8입니다.</span><span class="sxs-lookup"><span data-stu-id="7b070-208">8.</span></span>  <br/> |<span data-ttu-id="7b070-209">두 번째 웹 응용 프로그램 프록시 서버의 고정 IP 주소</span><span class="sxs-lookup"><span data-stu-id="7b070-209">Static IP address of the second web application proxy server</span></span>  <br/> |<span data-ttu-id="7b070-210">테이블 S의 항목 3에 정의된 서브넷의 주소 공간에 사용할 수 있는 다섯 번째 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="7b070-210">The fifth possible IP address for the address space of the subnet defined in Item 3 of Table S.</span></span>  <br/> |<span data-ttu-id="7b070-211">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7b070-211"></span></span>  <br/> |
   
 <span data-ttu-id="7b070-212">**가상 네트워크에 있는 표 i: 고정 IP 주소**</span><span class="sxs-lookup"><span data-stu-id="7b070-212">**Table I: Static IP addresses in the virtual network**</span></span>
  
<span data-ttu-id="7b070-213">가상 네트워크에서 도메인 컨트롤러를 처음 설정할 때 사용하려는 온-프레미스 네트워크의 두 DNS(Domain Name System) 서버에 대해서는 테이블 D를 채웁니다. IT 부서에서 이 목록을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="7b070-213">For two Domain Name System (DNS) servers in your on-premises network that you want to use when initially setting up the domain controllers in your virtual network, fill in Table D. Work with your IT department to determine this list.</span></span>
  
|<span data-ttu-id="7b070-214">**항목**</span><span class="sxs-lookup"><span data-stu-id="7b070-214">**Item**</span></span>|<span data-ttu-id="7b070-215">**DNS 서버 식별 이름**</span><span class="sxs-lookup"><span data-stu-id="7b070-215">**DNS server friendly name**</span></span>|<span data-ttu-id="7b070-216">**DNS 서버 IP 주소**</span><span class="sxs-lookup"><span data-stu-id="7b070-216">**DNS server IP address**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="7b070-217">1.</span><span class="sxs-lookup"><span data-stu-id="7b070-217">1.</span></span>  <br/> |<span data-ttu-id="7b070-218">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7b070-218"></span></span>  <br/> |<span data-ttu-id="7b070-219">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7b070-219"></span></span>  <br/> |
|<span data-ttu-id="7b070-220">2.</span><span class="sxs-lookup"><span data-stu-id="7b070-220">2.</span></span>  <br/> |<span data-ttu-id="7b070-221">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7b070-221"></span></span>  <br/> |<span data-ttu-id="7b070-222">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7b070-222"></span></span>  <br/> |
   
 <span data-ttu-id="7b070-223">**테이블 D: 온-프레미스 DNS 서버**</span><span class="sxs-lookup"><span data-stu-id="7b070-223">**Table D: On-premises DNS servers**</span></span>
  
<span data-ttu-id="7b070-p107">사이트 간 VPN 연결을 통해 프레미스 간 네트워크에서 조직 네트워크로 패킷을 라우팅하려면, 조직의 온-프레미스 네트워크에 있는 연결 가능한 모든 위치의 주소 공간 목록(CIDR 표기법)을 포함한 로컬 네트워크로 가상 네트워크를 구성해야 합니다. 로컬 네트워크를 정의하는 주소 공간 목록은 고유해야 하며 다른 가상 네트워크 또는 다른 로컬 네트워크에 사용되는 주소 공간과 중복되면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b070-p107">To route packets from the cross-premises network to your organization network across the site-to-site VPN connection, you must configure the virtual network with a local network that contains a list of the address spaces (in CIDR notation) for all of the reachable locations on your organization's on-premises network. The list of address spaces that define your local network must be unique and must not overlap with the address space used for other virtual networks or other local networks.</span></span>
  
<span data-ttu-id="7b070-p108">로컬 네트워크 주소 공간의 집합에 대해서는 테이블 L을 채웁니다. 세 개의 빈 항목이 나열되지만 일반적으로 더 많이 필요합니다. IT 부서에서 주소 공간의 목록을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="7b070-p108">For the set of local network address spaces, fill in Table L. Note that three blank entries are listed but you will typically need more. Work with your IT department to determine this list of address spaces.</span></span>
  
|<span data-ttu-id="7b070-228">**항목**</span><span class="sxs-lookup"><span data-stu-id="7b070-228">**Item**</span></span>|<span data-ttu-id="7b070-229">**로컬 네트워크 주소 공간**</span><span class="sxs-lookup"><span data-stu-id="7b070-229">**Local network address space**</span></span>|
|:-----|:-----|
|<span data-ttu-id="7b070-230">1.</span><span class="sxs-lookup"><span data-stu-id="7b070-230">1.</span></span>  <br/> |<span data-ttu-id="7b070-231">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7b070-231"></span></span>  <br/> |
|<span data-ttu-id="7b070-232">2.</span><span class="sxs-lookup"><span data-stu-id="7b070-232">2.</span></span>  <br/> |<span data-ttu-id="7b070-233">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7b070-233"></span></span>  <br/> |
|<span data-ttu-id="7b070-234">3.</span><span class="sxs-lookup"><span data-stu-id="7b070-234">3.</span></span>  <br/> |<span data-ttu-id="7b070-235">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7b070-235"></span></span>  <br/> |
   
 <span data-ttu-id="7b070-236">**테이블 L: 로컬 네트워크의 주소 접두사**</span><span class="sxs-lookup"><span data-stu-id="7b070-236">**Table L: Address prefixes for the local network**</span></span>
  
<span data-ttu-id="7b070-237">이제 Azure 인프라를 구축하여 Office 365용 페더레이션 인증을 호스트합니다.</span><span class="sxs-lookup"><span data-stu-id="7b070-237">Now let's begin building the Azure infrastructure to host your federated authentication for Office 365.</span></span>
  
> [!NOTE]
> <span data-ttu-id="7b070-p109">Azure PowerShell의 최신 버전을 사용 하는 다음 명령 집합입니다. [Azure PowerShell cmdlet 시작](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="7b070-p109">The following command sets use the latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span></span> 
  
<span data-ttu-id="7b070-240">먼저 Azure PowerShell 프롬프트를 시작하고 계정에 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="7b070-240">First, start an Azure PowerShell prompt and login to your account.</span></span>
  
```
Login-AzureRMAccount
```

> [!TIP]
> <span data-ttu-id="7b070-241">모든이 문서와 사용자 지정 설정을 기반으로 준비 간편 실행 PowerShell 명령 블록을 생성 하는 Microsoft Excel 구성 통합 문서에 PowerShell 명령을 포함 하는 텍스트 파일에 대 한 Office 365에 대 한 페더레이션 인증 [에서 참조 Azure 배포 키트](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664)합니다.</span><span class="sxs-lookup"><span data-stu-id="7b070-241">For a text file that contains all of the PowerShell commands in this article and a Microsoft Excel configuration workbook that generates ready-to-run PowerShell command blocks based on your custom settings, see the [Federated Authentication for Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664).</span></span> 
  
<span data-ttu-id="7b070-242">다음 명령을 사용하여 구독 이름을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="7b070-242">Get your subscription name using the following command.</span></span>
  
```
Get-AzureRMSubscription | Sort Name | Select Name
```

<span data-ttu-id="7b070-243">Azure PowerShell의 이전 버전에 대 한이 명령을 대신 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b070-243">For older versions of Azure PowerShell, use this command instead.</span></span>
  
```
Get-AzureRMSubscription | Sort Name | Select SubscriptionName
```

<span data-ttu-id="7b070-p110">Azure 구독을 설정 합니다. 따옴표를 포함 하 여 입력을 내에 있는 모든 항목을 교체는 \< 및 > 올바른 이름의 문자입니다.</span><span class="sxs-lookup"><span data-stu-id="7b070-p110">Set your Azure subscription. Replace everything within the quotes, including the \< and > characters, with the correct name.</span></span>
  
```
$subscr="<subscription name>"
Get-AzureRmSubscription -SubscriptionName $subscr | Select-AzureRmSubscription
```

<span data-ttu-id="7b070-p111">다음으로 새 리소스 그룹을 만듭니다. 고유한 리소스 그룹 이름의 집합을 확인하려면 이 명령을 사용하여 기존 리소스 그룹을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="7b070-p111">Next, create the new resource groups. To determine a unique set of resource group names, use this command to list your existing resource groups.</span></span>
  
```
Get-AzureRMResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

<span data-ttu-id="7b070-248">고유한 리소스 그룹 이름의 집합에 대해서는 다음 테이블을 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="7b070-248">Fill in the following table for the set of unique resource group names.</span></span>
  
|<span data-ttu-id="7b070-249">**항목**</span><span class="sxs-lookup"><span data-stu-id="7b070-249">**Item**</span></span>|<span data-ttu-id="7b070-250">**리소스 그룹 이름**</span><span class="sxs-lookup"><span data-stu-id="7b070-250">**Resource group name**</span></span>|<span data-ttu-id="7b070-251">**용도**</span><span class="sxs-lookup"><span data-stu-id="7b070-251">**Purpose**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="7b070-252">1.</span><span class="sxs-lookup"><span data-stu-id="7b070-252">1.</span></span>  <br/> |<span data-ttu-id="7b070-253">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7b070-253"></span></span>  <br/> |<span data-ttu-id="7b070-254">도메인 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="7b070-254">Domain controllers</span></span>  <br/> |
|<span data-ttu-id="7b070-255">2.</span><span class="sxs-lookup"><span data-stu-id="7b070-255">2.</span></span>  <br/> |<span data-ttu-id="7b070-256">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7b070-256"></span></span>  <br/> |<span data-ttu-id="7b070-257">AD FS 서버</span><span class="sxs-lookup"><span data-stu-id="7b070-257">AD FS servers</span></span>  <br/> |
|<span data-ttu-id="7b070-258">3.</span><span class="sxs-lookup"><span data-stu-id="7b070-258">3.</span></span>  <br/> |<span data-ttu-id="7b070-259">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7b070-259"></span></span>  <br/> |<span data-ttu-id="7b070-260">웹 응용 프로그램 프록시 서버</span><span class="sxs-lookup"><span data-stu-id="7b070-260">Web application proxy servers</span></span>  <br/> |
|<span data-ttu-id="7b070-261">4.</span><span class="sxs-lookup"><span data-stu-id="7b070-261">4.</span></span>  <br/> |<span data-ttu-id="7b070-262">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7b070-262"></span></span>  <br/> |<span data-ttu-id="7b070-263">인프라 구성 요소</span><span class="sxs-lookup"><span data-stu-id="7b070-263">Infrastructure elements</span></span>  <br/> |
   
 <span data-ttu-id="7b070-264">**표 r: 자원 그룹**</span><span class="sxs-lookup"><span data-stu-id="7b070-264">**Table R: Resource groups**</span></span>
  
<span data-ttu-id="7b070-265">이러한 명령을 사용하여 새 리소스 그룹을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7b070-265">Create your new resource groups with these commands.</span></span>
  
```
$locName="<an Azure location, such as West US>"
$rgName="<Table R - Item 1 - Name column>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 2 - Name column>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 3 - Name column>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 4 - Name column>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
```

<span data-ttu-id="7b070-266">다음으로 Azure Virtual Network와 그 서브넷을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7b070-266">Next, you create the Azure virtual network and its subnets.</span></span>
  
```
$rgName="<Table R - Item 4 - Resource group name column>"
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$vnetAddrPrefix="<Table V - Item 4 - Value column>"
$dnsServers=@( "<Table D - Item 1 - DNS server IP address column>", "<Table D - Item 2 - DNS server IP address column>" )
# Get the shortened version of the location
$locShortName=(Get-AzureRmResourceGroup -Name $rgName).Location

# Create the subnets
$subnet1Name="<Table S - Item 1 - Subnet name column>"
$subnet1Prefix="<Table S - Item 1 - Subnet address space column>"
$subnet1=New-AzureRMVirtualNetworkSubnetConfig -Name $subnet1Name -AddressPrefix $subnet1Prefix
$subnet2Name="<Table S - Item 2 - Subnet name column>"
$subnet2Prefix="<Table S - Item 2 - Subnet address space column>"
$subnet2=New-AzureRMVirtualNetworkSubnetConfig -Name $subnet2Name -AddressPrefix $subnet2Prefix
$subnet3Name="<Table S - Item 3 - Subnet name column>"
$subnet3Prefix="<Table S - Item 3 - Subnet address space column>"
$subnet3=New-AzureRMVirtualNetworkSubnetConfig -Name $subnet3Name -AddressPrefix $subnet3Prefix
$gwSubnet4Prefix="<Table S - Item 4 - Subnet address space column>"
$gwSubnet=New-AzureRMVirtualNetworkSubnetConfig -Name "GatewaySubnet" -AddressPrefix $gwSubnet4Prefix

# Create the virtual network
New-AzureRMVirtualNetwork -Name $vnetName -ResourceGroupName $rgName -Location $locName -AddressPrefix $vnetAddrPrefix -Subnet $gwSubnet,$subnet1,$subnet2,$subnet3 -DNSServer $dnsServers

```

<span data-ttu-id="7b070-p112">다음으로, 네트워크 가상 컴퓨터를 포함 하는 각 서브넷에 대 한 보안 그룹을 만듭니다. 서브넷 격리를 수행 하 여 특정 유형의 트래픽 허용 또는 서브넷의 네트워크 보안 그룹에 대 한 거부에 대 한 규칙을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b070-p112">Next, you create network security groups for each subnet that contains virtual machines. To perform subnet isolation, you can add rules for the specific types of traffic allowed or denied to the network security group of a subnet.</span></span>
  
```
# Create network security groups
$vnet=Get-AzureRMVirtualNetwork -ResourceGroupName $rgName -Name $vnetName

New-AzureRMNetworkSecurityGroup -Name $subnet1Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzureRMNetworkSecurityGroup -Name $subnet1Name -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet1Name -AddressPrefix $subnet1Prefix -NetworkSecurityGroup $nsg

New-AzureRMNetworkSecurityGroup -Name $subnet2Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzureRMNetworkSecurityGroup -Name $subnet2Name -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet2Name -AddressPrefix $subnet2Prefix -NetworkSecurityGroup $nsg

New-AzureRMNetworkSecurityGroup -Name $subnet3Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzureRMNetworkSecurityGroup -Name $subnet3Name -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet3Name -AddressPrefix $subnet3Prefix -NetworkSecurityGroup $nsg
```

<span data-ttu-id="7b070-269">다음으로 이러한 명령을 사용하여 사이트 간 VPN 연결의 게이트웨이를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7b070-269">Next, use these commands to create the gateways for the site-to-site VPN connection.</span></span>
  
```
$rgName="<Table R - Item 4 - Resource group name column>"
$locName="<Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$vnet=Get-AzureRMVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzureRmVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name "GatewaySubnet"

# Attach a virtual network gateway to a public IP address and the gateway subnet
$publicGatewayVipName="PublicIPAddress"
$vnetGatewayIpConfigName="PublicIPConfig"
New-AzureRMPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$publicGatewayVip=Get-AzureRMPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName
$vnetGatewayIpConfig=New-AzureRMVirtualNetworkGatewayIpConfig -Name $vnetGatewayIpConfigName -PublicIpAddressId $publicGatewayVip.Id -Subnet $subnet

# Create the Azure gateway
$vnetGatewayName="AzureGateway"
$vnetGateway=New-AzureRMVirtualNetworkGateway -Name $vnetGatewayName -ResourceGroupName $rgName -Location $locName -GatewayType Vpn -VpnType RouteBased -IpConfigurations $vnetGatewayIpConfig

# Create the gateway for the local network
$localGatewayName="LocalNetGateway"
$localGatewayIP="<Table V - Item 3 - Value column>"
$localNetworkPrefix=@( <comma-separated, double-quote enclosed list of the local network address prefixes from Table L, example: "10.1.0.0/24", "10.2.0.0/24"> )
$localGateway=New-AzureRMLocalNetworkGateway -Name $localGatewayName -ResourceGroupName $rgName -Location $locName -GatewayIpAddress $localGatewayIP -AddressPrefix $localNetworkPrefix

# Define the Azure virtual network VPN connection
$vnetConnectionName="S2SConnection"
$vnetConnectionKey="<Table V - Item 5 - Value column>"
$vnetConnection=New-AzureRMVirtualNetworkGatewayConnection -Name $vnetConnectionName -ResourceGroupName $rgName -Location $locName -ConnectionType IPsec -SharedKey $vnetConnectionKey -VirtualNetworkGateway1 $vnetGateway -LocalNetworkGateway2 $localGateway

```

> [!NOTE]
> <span data-ttu-id="7b070-p113">개별 사용자의 연결 된 인증 모든 온-프레미스 리소스에 의존 하지 않습니다. 그러나이 사이트 마다 VPN 연결을 사용할 수 없게 하는 경우에 도메인 컨트롤러는 VNet에는 사용자 계정 및 온-프레미스 Windows Server AD에서 그룹에 대 한 업데이트를 받지 않습니다. 을 보장 하기 위해이 발생 하지 않는 사이트에 대 한 VPN 연결에 대 한 고가용성을 구성할 수 있습니다. 자세한 내용은 [항상 사용 가능한 크로스-프레미스 및 VNet-VNet 연결을](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable) 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="7b070-p113">Federated authentication of individual users does not rely on any on-premises resources. However, if this site-to-site VPN connection becomes unavailable, the domain controllers in the VNet will not receive updates to user accounts and groups made in the on-premises Windows Server AD. To ensure this does not happen, you can configure high availability for your site-to-site VPN connection. For more information, see [Highly Available Cross-Premises and VNet-to-VNet Connectivity](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)</span></span>
  
<span data-ttu-id="7b070-274">그런 다음 이 명령의 디스플레이에서 가상 네트워크용 Azure VPN 게이트웨이의 공용 IPv4 주소를 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="7b070-274">Next, record the public IPv4 address of the Azure VPN gateway for your virtual network from the display of this command:</span></span>
  
```
Get-AzureRMPublicIpAddress -Name $publicGatewayVipName -ResourceGroupName $rgName
```

<span data-ttu-id="7b070-p114">다음으로 Azure VPN 게이트웨이를 연결 하기 위해 온-프레미스 VPN 장치를 구성 합니다. 자세한 내용은 [Configure VPN 장치를](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices)참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b070-p114">Next, configure your on-premises VPN device to connect to the Azure VPN gateway. For more information, see [Configure your VPN device](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).</span></span>
  
<span data-ttu-id="7b070-277">온-프레미스 VPN 장치를 구성하려면 다음 항목이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="7b070-277">To configure your on-premises VPN device, you will need the following:</span></span>
  
- <span data-ttu-id="7b070-278">Azure VPN 게이트웨이의 공용 IPv4 주소.</span><span class="sxs-lookup"><span data-stu-id="7b070-278">The public IPv4 address of the Azure VPN gateway.</span></span>
    
- <span data-ttu-id="7b070-279">사이트 마다 VPN 연결 (테이블 V-항목 5-값 열)에 대 한 IPsec 사전 공유 키입니다.</span><span class="sxs-lookup"><span data-stu-id="7b070-279">The IPsec pre-shared key for the site-to-site VPN connection (Table V - Item 5 - Value column).</span></span>
    
<span data-ttu-id="7b070-p115">다음으로 가상 네트워크의 주소 공간이 온-프레미스 네트워크에서 연결 가능한지 확인합니다. 일반적으로 가상 네트워크 주소 공간에 해당하는 경로를 VPN 장치에 추가한 다음 이 경로를 조직 네트워크의 나머지 라우팅 인프라에 보급합니다. IT 부서에서 이 작업을 수행하는 방법을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="7b070-p115">Next, ensure that the address space of the virtual network is reachable from your on-premises network. This is usually done by adding a route corresponding to the virtual network address space to your VPN device and then advertising that route to the rest of the routing infrastructure of your organization network. Work with your IT department to determine how to do this.</span></span>
  
<span data-ttu-id="7b070-p116">그 다음 세 가지 가용성 집합의 이름을 정의합니다. 테이블 A를 채웁니다. </span><span class="sxs-lookup"><span data-stu-id="7b070-p116">Next, define the names of three availability sets. Fill out Table A.</span></span> 
  
|<span data-ttu-id="7b070-285">**항목**</span><span class="sxs-lookup"><span data-stu-id="7b070-285">**Item**</span></span>|<span data-ttu-id="7b070-286">**용도**</span><span class="sxs-lookup"><span data-stu-id="7b070-286">**Purpose**</span></span>|<span data-ttu-id="7b070-287">**가용성 집합 이름**</span><span class="sxs-lookup"><span data-stu-id="7b070-287">**Availability set name**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="7b070-288">1.</span><span class="sxs-lookup"><span data-stu-id="7b070-288">1.</span></span>  <br/> |<span data-ttu-id="7b070-289">도메인 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="7b070-289">Domain controllers</span></span>  <br/> |<span data-ttu-id="7b070-290">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7b070-290"></span></span>  <br/> |
|<span data-ttu-id="7b070-291">2.</span><span class="sxs-lookup"><span data-stu-id="7b070-291">2.</span></span>  <br/> |<span data-ttu-id="7b070-292">AD FS 서버</span><span class="sxs-lookup"><span data-stu-id="7b070-292">AD FS servers</span></span>  <br/> |<span data-ttu-id="7b070-293">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7b070-293"></span></span>  <br/> |
|<span data-ttu-id="7b070-294">3.</span><span class="sxs-lookup"><span data-stu-id="7b070-294">3.</span></span>  <br/> |<span data-ttu-id="7b070-295">웹 응용 프로그램 프록시 서버</span><span class="sxs-lookup"><span data-stu-id="7b070-295">Web application proxy servers</span></span>  <br/> |<span data-ttu-id="7b070-296">_______________________________</span><span class="sxs-lookup"><span data-stu-id="7b070-296"></span></span>  <br/> |
   
 <span data-ttu-id="7b070-297">**설정 하는 테이블 a: 가용성**</span><span class="sxs-lookup"><span data-stu-id="7b070-297">**Table A: Availability sets**</span></span>
  
<span data-ttu-id="7b070-298">2, 3 및 4단계에서 가상 컴퓨터를 만들 때 이러한 이름이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="7b070-298">You will need these names when you create the virtual machines in phases 2, 3, and 4.</span></span>
  
<span data-ttu-id="7b070-299">이러한 Azure PowerShell 명령을 사용하여 새 가용성 집합을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7b070-299">Create the new availability sets with these Azure PowerShell commands.</span></span>
  
```
$locName="<the Azure location for your new resource group>"
$rgName="<Table R - Item 1 - Resource group name column>"
$avName="<Table A - Item 1 - Availability set name column>"
New-AzureRMAvailabilitySet -Name $avName -ResourceGroupName $rgName -Location $locName
$rgName="<Table R - Item 2 - Resource group name column>"
$avName="<Table A - Item 2 - Availability set name column>"
New-AzureRMAvailabilitySet -Name $avName -ResourceGroupName $rgName -Location $locName
$rgName="<Table R - Item 3 - Resource group name column>"
$avName="<Table A - Item 3 - Availability set name column>"
New-AzureRMAvailabilitySet -Name $avName -ResourceGroupName $rgName -Location $locName
```

<span data-ttu-id="7b070-300">이 단계를 성공적으로 완료하면 다음 구성을 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b070-300">This is the configuration resulting from the successful completion of this phase.</span></span>
  
<span data-ttu-id="7b070-301">**1 단계: Office 365에 대 한 고가용성 연결 된 인증을 위한 Azure 인프라**</span><span class="sxs-lookup"><span data-stu-id="7b070-301">**Phase 1: The Azure infrastructure for high availability federated authentication for Office 365**</span></span>

![Azure 인프라를 포함한 Azure에서 고가용성 Office 365 페더레이션 인증 1단계](images/4e7ba678-07df-40ce-b372-021bf7fc91fa.png)
  
## <a name="next-step"></a><span data-ttu-id="7b070-303">다음 단계</span><span class="sxs-lookup"><span data-stu-id="7b070-303">Next step</span></span>

<span data-ttu-id="7b070-304">사용 하 여 [고가용성 페더레이션 인증 2 단계: 도메인 컨트롤러를 구성](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) 이 작업의 구성을 사용 하 여 계속 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b070-304">Use [High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) to continue with the configuration of this workload.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="7b070-305">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7b070-305">See Also</span></span>

[<span data-ttu-id="7b070-306">Azure의 Office 365에 대 한 고가용성 연결 된 인증 배포</span><span class="sxs-lookup"><span data-stu-id="7b070-306">Deploy high availability federated authentication for Office 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="7b070-307">Office 365 개발/테스트 환경에 대 한 페더레이션된 id</span><span class="sxs-lookup"><span data-stu-id="7b070-307">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="7b070-308">클라우드 채택 및 하이브리드 솔루션</span><span class="sxs-lookup"><span data-stu-id="7b070-308">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="7b070-309">Office 365용 페더레이션 ID</span><span class="sxs-lookup"><span data-stu-id="7b070-309">Federated identity for Office 365</span></span>](https://support.office.com/article/Understanding-Office-365-identity-and-Azure-Active-Directory-06a189e7-5ec6-4af2-94bf-a22ea225a7a9#bk_federated)


