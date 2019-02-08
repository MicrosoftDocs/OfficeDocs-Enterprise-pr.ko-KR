---
title: 고가용성 연결 된 인증 단계 1 구성 Azure
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/06/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: 91266aac-4d00-4b5f-b424-86a1a837792c
description: '요약: Microsoft Azure 인프라를 구성하여 Office 365 페더레이션 인증의 고가용성을 호스트합니다.'
ms.openlocfilehash: bbaefffb6bfa55d9af11e08c2011c7333cefe46e
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897481"
---
# <a name="high-availability-federated-authentication-phase-1-configure-azure"></a><span data-ttu-id="205bb-103">고가용성 페더레이션 인증 1단계: Azure 구성</span><span class="sxs-lookup"><span data-stu-id="205bb-103">High availability federated authentication Phase 1: Configure Azure</span></span>

 <span data-ttu-id="205bb-104">**요약:** Microsoft Azure 인프라를 구성하여 Office 365 페더레이션 인증의 고가용성을 호스트합니다.</span><span class="sxs-lookup"><span data-stu-id="205bb-104">**Summary:** Configure the Microsoft Azure infrastructure to host high availability federated authentication for Office 365.</span></span>
  
<span data-ttu-id="205bb-p101">이 단계에서는 자원 그룹, 2, 3 및 4 단계에서 가상 컴퓨터를 호스팅할 Azure에 가상 네트워크 (VNet) 및 가용성 집합을 만듭니다. 레코드로 이동 하기 전에이 단계를 완료 해야 [고가용성 페더레이션 인증 2 단계: 도메인 컨트롤러 구성](high-availability-federated-authentication-phase-2-configure-domain-controllers.md)합니다. 모든 단계에 대 한 [Azure의 Office 365에 대 한 고가용성 연결 된 인증 배포를](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="205bb-p101">In this phase, you create the resource groups, virtual network (VNet), and availability sets in Azure that will host the virtual machines in phases 2, 3, and 4. You must complete this phase before moving on to [High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md). See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
<span data-ttu-id="205bb-108">이러한 기본 구성 요소와 함께 azure 프로 비전 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="205bb-108">Azure must be provisioned with these basic components:</span></span>
  
- <span data-ttu-id="205bb-109">리소스 그룹</span><span class="sxs-lookup"><span data-stu-id="205bb-109">Resource groups</span></span>
    
- <span data-ttu-id="205bb-110">Azure Virtual Machines를 호스팅하기 위한 서브넷이 있는 프레미스 간 Azure Virtual Network(VNet)</span><span class="sxs-lookup"><span data-stu-id="205bb-110">A cross-premises Azure virtual network (VNet) with subnets for hosting the Azure virtual machines</span></span>
    
- <span data-ttu-id="205bb-111">수행 중인 서브넷 격리용 네트워크 보안 그룹</span><span class="sxs-lookup"><span data-stu-id="205bb-111">Network security groups for performing subnet isolation</span></span>
    
- <span data-ttu-id="205bb-112">가용성 집합</span><span class="sxs-lookup"><span data-stu-id="205bb-112">Availability sets</span></span>
    
## <a name="configure-azure-components"></a><span data-ttu-id="205bb-113">Azure 구성 요소 구성</span><span class="sxs-lookup"><span data-stu-id="205bb-113">Configure Azure components</span></span>

<span data-ttu-id="205bb-p102">Azure 구성 요소를 시작 하기 전에 다음 표를 입력 합니다. 에 도움을 주고 Azure를 구성 하는 절차를이 섹션을 인쇄 하 고 필요한 정보를 적어둡니다 또는 문서에이 섹션에 복사 하 고에 내용을 입력 합니다. VNet의 설정에 대해 테이블 V를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="205bb-p102">Before you begin configuring Azure components, fill in the following tables. To assist you in the procedures for configuring Azure, print this section and write down the needed information or copy this section to a document and fill it in. For the settings of the VNet, fill in Table V.</span></span>
  
|<span data-ttu-id="205bb-117">**항목**</span><span class="sxs-lookup"><span data-stu-id="205bb-117">**Item**</span></span>|<span data-ttu-id="205bb-118">**구성 설정**</span><span class="sxs-lookup"><span data-stu-id="205bb-118">**Configuration setting**</span></span>|<span data-ttu-id="205bb-119">**설명**</span><span class="sxs-lookup"><span data-stu-id="205bb-119">**Description**</span></span>|<span data-ttu-id="205bb-120">**값**</span><span class="sxs-lookup"><span data-stu-id="205bb-120">**Value**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="205bb-121">1.</span><span class="sxs-lookup"><span data-stu-id="205bb-121">1.</span></span>  <br/> |<span data-ttu-id="205bb-122">VNet 이름</span><span class="sxs-lookup"><span data-stu-id="205bb-122">VNet name</span></span>  <br/> |<span data-ttu-id="205bb-123">VNet에 할당할 이름(예: FedAuthNet)입니다.</span><span class="sxs-lookup"><span data-stu-id="205bb-123">A name to assign to the VNet (example FedAuthNet).</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="205bb-124">2.</span><span class="sxs-lookup"><span data-stu-id="205bb-124">2.</span></span>  <br/> |<span data-ttu-id="205bb-125">VNet 위치</span><span class="sxs-lookup"><span data-stu-id="205bb-125">VNet location</span></span>  <br/> |<span data-ttu-id="205bb-126">지역 Azure 데이터 센터에 가상 네트워크가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="205bb-126">The regional Azure datacenter that will contain the virtual network.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="205bb-127">3.</span><span class="sxs-lookup"><span data-stu-id="205bb-127">3.</span></span>  <br/> |<span data-ttu-id="205bb-128">VPN 장치 IP 주소</span><span class="sxs-lookup"><span data-stu-id="205bb-128">VPN device IP address</span></span>  <br/> |<span data-ttu-id="205bb-129">인터넷에서 VPN 장치 인터페이스의 공용 IPv4 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="205bb-129">The public IPv4 address of your VPN device's interface on the Internet.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="205bb-130">4.</span><span class="sxs-lookup"><span data-stu-id="205bb-130">4.</span></span>  <br/> |<span data-ttu-id="205bb-131">VNet 주소 공간</span><span class="sxs-lookup"><span data-stu-id="205bb-131">VNet address space</span></span>  <br/> |<span data-ttu-id="205bb-p103">가상 네트워크의 주소 공간입니다. IT 부서에서 이 주소 공간을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="205bb-p103">The address space for the virtual network. Work with your IT department to determine this address space.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="205bb-134">5.</span><span class="sxs-lookup"><span data-stu-id="205bb-134">5.</span></span>  <br/> |<span data-ttu-id="205bb-135">IPsec 공유 키</span><span class="sxs-lookup"><span data-stu-id="205bb-135">IPsec shared key</span></span>  <br/> |<span data-ttu-id="205bb-p104">사이트 간 VPN 연결의 양측을 인증하는 데 사용되는 32자의 무작위 영숫자 문자열입니다. IT 또는 보안 부서에서 이 키 값을 확인합니다. 또한, [IPsec 미리 공유한 키의 무작위 문자열 만들기](http://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx)를 참조하세요.  </span><span class="sxs-lookup"><span data-stu-id="205bb-p104">A 32-character random, alphanumeric string that will be used to authenticate both sides of the site-to-site VPN connection. Work with your IT or security department to determine this key value. Alternately, see [Create a random string for an IPsec preshared key](http://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx).  </span></span><br/> |![](./media/Common-Images/TableLine.png)  <br/> |
   
 <span data-ttu-id="205bb-139">**테이블 V: 프레미스 간 가상 네트워크 구성**</span><span class="sxs-lookup"><span data-stu-id="205bb-139">**Table V: Cross-premises virtual network configuration**</span></span>
  
<span data-ttu-id="205bb-p105">다음으로 이 솔루션의 서브넷에 대해서는 테이블 S를 채웁니다. 모든 주소 공간은 CIDR(Classless Interdomain Routing) 형식이어야 하며 네트워크 접두사 형식이라고도 합니다. 예를 들어 10.24.64.0/20입니다.</span><span class="sxs-lookup"><span data-stu-id="205bb-p105">Next, fill in Table S for the subnets of this solution. All address spaces should be in Classless Interdomain Routing (CIDR) format, also known as network prefix format. An example is 10.24.64.0/20.</span></span>
  
<span data-ttu-id="205bb-p106">처음 세 개의 서브넷의 경우 가상 네트워크 주소 공간에 따라 이름과 단일 IP 주소 공간을 지정합니다. 게이트웨이 서브넷의 경우 Azure 게이트웨이 서브넷의 27비트 주소 공간(/27 접두사 길이)을 다음과 같이 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="205bb-p106">For the first three subnets, specify a name and a single IP address space based on the virtual network address space. For the gateway subnet, determine the 27-bit address space (with a /27 prefix length) for the Azure gateway subnet with the following:</span></span>
  
1. <span data-ttu-id="205bb-145">VNet의 주소 공간에 있는 변수 비트를 1(게이트웨이 서브넷에서 사용하는 비트까지)로 설정한 다음 나머지 비트를 0으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="205bb-145">Set the variable bits in the address space of the VNet to 1, up to the bits being used by the gateway subnet, then set the remaining bits to 0.</span></span>
    
2. <span data-ttu-id="205bb-146">결과 비트를 10진수로 변환하고 이를 접두사 길이가 게이트웨이 서브넷 크기로 설정된 주소 공간으로 표현합니다.</span><span class="sxs-lookup"><span data-stu-id="205bb-146">Convert the resulting bits to decimal and express it as an address space with the prefix length set to the size of the gateway subnet.</span></span>
    
<span data-ttu-id="205bb-147">PowerShell 명령 블록 및 하면이 계산을 수행 하는 C# 또는 Python 콘솔 응용 프로그램에 대 한 [Azure 게이트웨이 서브넷에 대 한 주소 공간 계산기](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) 를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="205bb-147">See [Address space calculator for Azure gateway subnets](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) for a PowerShell command block and C# or Python console application that performs this calculation for you.</span></span>
  
<span data-ttu-id="205bb-148">IT 부서에서 가상 네트워크 주소 공간의 이러한 주소 공간을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="205bb-148">Work with your IT department to determine these address spaces from the virtual network address space.</span></span>
  
|<span data-ttu-id="205bb-149">**항목**</span><span class="sxs-lookup"><span data-stu-id="205bb-149">**Item**</span></span>|<span data-ttu-id="205bb-150">**서브넷 이름**</span><span class="sxs-lookup"><span data-stu-id="205bb-150">**Subnet name**</span></span>|<span data-ttu-id="205bb-151">**서브넷 주소 공간**</span><span class="sxs-lookup"><span data-stu-id="205bb-151">**Subnet address space**</span></span>|<span data-ttu-id="205bb-152">**용도**</span><span class="sxs-lookup"><span data-stu-id="205bb-152">**Purpose**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="205bb-153">1.</span><span class="sxs-lookup"><span data-stu-id="205bb-153">1.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="205bb-154">Windows Server Active Directory(AD) 도메인 컨트롤러 및 DirSync 서버 가상 컴퓨터(VM)에서 사용하는 서브넷입니다.</span><span class="sxs-lookup"><span data-stu-id="205bb-154">The subnet used by the Windows Server Active Directory (AD) domain controller and DirSync server virtual machines (VMs).</span></span>  <br/> |
|<span data-ttu-id="205bb-155">2.</span><span class="sxs-lookup"><span data-stu-id="205bb-155">2.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="205bb-156">AD FS VM에서 사용하는 서브넷입니다.</span><span class="sxs-lookup"><span data-stu-id="205bb-156">The subnet used by the AD FS VMs.</span></span>  <br/> |
|<span data-ttu-id="205bb-157">3.</span><span class="sxs-lookup"><span data-stu-id="205bb-157">3.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="205bb-158">웹 응용 프로그램 프록시 VM에서 사용하는 서브넷입니다.</span><span class="sxs-lookup"><span data-stu-id="205bb-158">The subnet used by the web application proxy VMs.</span></span>  <br/> |
|<span data-ttu-id="205bb-159">4.</span><span class="sxs-lookup"><span data-stu-id="205bb-159">4.</span></span>  <br/> |<span data-ttu-id="205bb-160">GatewaySubnet</span><span class="sxs-lookup"><span data-stu-id="205bb-160">GatewaySubnet</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="205bb-161">Azure 게이트웨이 VM에서 사용하는 서브넷입니다.</span><span class="sxs-lookup"><span data-stu-id="205bb-161">The subnet used by the Azure gateway VMs.</span></span>  <br/> |
   
 <span data-ttu-id="205bb-162">**테이블 S: 가상 네트워크의 서브넷**</span><span class="sxs-lookup"><span data-stu-id="205bb-162">**Table S: Subnets in the virtual network**</span></span>
  
<span data-ttu-id="205bb-163">다음으로 가상 컴퓨터와 부하 분산 장치 인스턴스에 할당된 고정 IP 주소에 대해서는 테이블 I를 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="205bb-163">Next, fill in Table I for the static IP addresses assigned to virtual machines and load balancer instances.</span></span>
  
|<span data-ttu-id="205bb-164">**항목**</span><span class="sxs-lookup"><span data-stu-id="205bb-164">**Item**</span></span>|<span data-ttu-id="205bb-165">**용도**</span><span class="sxs-lookup"><span data-stu-id="205bb-165">**Purpose**</span></span>|<span data-ttu-id="205bb-166">**서브넷의 IP 주소**</span><span class="sxs-lookup"><span data-stu-id="205bb-166">**IP address on the subnet**</span></span>|<span data-ttu-id="205bb-167">**값**</span><span class="sxs-lookup"><span data-stu-id="205bb-167">**Value**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="205bb-168">1.</span><span class="sxs-lookup"><span data-stu-id="205bb-168">1.</span></span>  <br/> |<span data-ttu-id="205bb-169">첫 번째 도메인 컨트롤러의 고정 IP 주소</span><span class="sxs-lookup"><span data-stu-id="205bb-169">Static IP address of the first domain controller</span></span>  <br/> |<span data-ttu-id="205bb-170">테이블 S의 항목 1에 정의된 서브넷의 주소 공간에 사용할 수 있는 네 번째 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="205bb-170">The fourth possible IP address for the address space of the subnet defined in Item 1 of Table S.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="205bb-171">2.</span><span class="sxs-lookup"><span data-stu-id="205bb-171">2.</span></span>  <br/> |<span data-ttu-id="205bb-172">두 번째 도메인 컨트롤러의 고정 IP 주소</span><span class="sxs-lookup"><span data-stu-id="205bb-172">Static IP address of the second domain controller</span></span>  <br/> |<span data-ttu-id="205bb-173">테이블 S의 항목 1에 정의된 서브넷의 주소 공간에 사용할 수 있는 다섯 번째 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="205bb-173">The fifth possible IP address for the address space of the subnet defined in Item 1 of Table S.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="205bb-174">3.</span><span class="sxs-lookup"><span data-stu-id="205bb-174">3.</span></span>  <br/> |<span data-ttu-id="205bb-175">DirSync 서버의 고정 IP 주소</span><span class="sxs-lookup"><span data-stu-id="205bb-175">Static IP address of the DirSync server</span></span>  <br/> |<span data-ttu-id="205bb-176">테이블 S의 항목 1에 정의된 서브넷의 주소 공간에 사용할 수 있는 여섯 번째 IP 주소입니다. </span><span class="sxs-lookup"><span data-stu-id="205bb-176">The sixth possible IP address for the address space of the subnet defined in Item 1 of Table S.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="205bb-177">4.</span><span class="sxs-lookup"><span data-stu-id="205bb-177">4.</span></span>  <br/> |<span data-ttu-id="205bb-178">AD FS 서버용 내부 부하 분산 장치의 고정 IP 주소</span><span class="sxs-lookup"><span data-stu-id="205bb-178">Static IP address of the internal load balancer for the AD FS servers</span></span>  <br/> |<span data-ttu-id="205bb-179">테이블 S의 항목 2에 정의된 서브넷의 주소 공간에 사용할 수 있는 네 번째 IP 주소입니다. </span><span class="sxs-lookup"><span data-stu-id="205bb-179">The fourth possible IP address for the address space of the subnet defined in Item 2 of Table S.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="205bb-180">5.</span><span class="sxs-lookup"><span data-stu-id="205bb-180">5.</span></span>  <br/> |<span data-ttu-id="205bb-181">첫 번째 AD FS 서버의 고정 IP 주소</span><span class="sxs-lookup"><span data-stu-id="205bb-181">Static IP address of the first AD FS server</span></span>  <br/> |<span data-ttu-id="205bb-182">테이블 S의 항목 2에 정의된 서브넷의 주소 공간에 사용할 수 있는 다섯 번째 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="205bb-182">The fifth possible IP address for the address space of the subnet defined in Item 2 of Table S.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="205bb-183">6.</span><span class="sxs-lookup"><span data-stu-id="205bb-183">6.</span></span>  <br/> |<span data-ttu-id="205bb-184">두 번째 AD FS 서버의 고정 IP 주소</span><span class="sxs-lookup"><span data-stu-id="205bb-184">Static IP address of the second AD FS server</span></span>  <br/> |<span data-ttu-id="205bb-185">테이블 S의 항목 2에 정의된 서브넷의 주소 공간에 사용할 수 있는 여섯 번째 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="205bb-185">The sixth possible IP address for the address space of the subnet defined in Item 2 of Table S.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="205bb-186">7.</span><span class="sxs-lookup"><span data-stu-id="205bb-186">7.</span></span>  <br/> |<span data-ttu-id="205bb-187">첫 번째 웹 응용 프로그램 프록시 서버의 고정 IP 주소</span><span class="sxs-lookup"><span data-stu-id="205bb-187">Static IP address of the first web application proxy server</span></span>  <br/> |<span data-ttu-id="205bb-188">테이블 S의 항목 3에 정의된 서브넷의 주소 공간에 사용할 수 있는 네 번째 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="205bb-188">The fourth possible IP address for the address space of the subnet defined in Item 3 of Table S.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="205bb-189">8.</span><span class="sxs-lookup"><span data-stu-id="205bb-189">8.</span></span>  <br/> |<span data-ttu-id="205bb-190">두 번째 웹 응용 프로그램 프록시 서버의 고정 IP 주소</span><span class="sxs-lookup"><span data-stu-id="205bb-190">Static IP address of the second web application proxy server</span></span>  <br/> |<span data-ttu-id="205bb-191">테이블 S의 항목 3에 정의된 서브넷의 주소 공간에 사용할 수 있는 다섯 번째 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="205bb-191">The fifth possible IP address for the address space of the subnet defined in Item 3 of Table S.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
   
 <span data-ttu-id="205bb-192">**테이블 I: 가상 네트워크의 고정 IP 주소**</span><span class="sxs-lookup"><span data-stu-id="205bb-192">**Table I: Static IP addresses in the virtual network**</span></span>
  
<span data-ttu-id="205bb-193">가상 네트워크에서 도메인 컨트롤러를 처음 설정할 때 사용하려는 온-프레미스 네트워크의 두 DNS(Domain Name System) 서버에 대해서는 테이블 D를 채웁니다. IT 부서에서 이 목록을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="205bb-193">For two Domain Name System (DNS) servers in your on-premises network that you want to use when initially setting up the domain controllers in your virtual network, fill in Table D. Work with your IT department to determine this list.</span></span>
  
|<span data-ttu-id="205bb-194">**항목**</span><span class="sxs-lookup"><span data-stu-id="205bb-194">**Item**</span></span>|<span data-ttu-id="205bb-195">**DNS 서버 식별 이름**</span><span class="sxs-lookup"><span data-stu-id="205bb-195">**DNS server friendly name**</span></span>|<span data-ttu-id="205bb-196">**DNS 서버 IP 주소**</span><span class="sxs-lookup"><span data-stu-id="205bb-196">**DNS server IP address**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="205bb-197">1.</span><span class="sxs-lookup"><span data-stu-id="205bb-197">1.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="205bb-198">2.</span><span class="sxs-lookup"><span data-stu-id="205bb-198">2.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
   
 <span data-ttu-id="205bb-199">**테이블 D: 온-프레미스 DNS 서버**</span><span class="sxs-lookup"><span data-stu-id="205bb-199">**Table D: On-premises DNS servers**</span></span>
  
<span data-ttu-id="205bb-p107">사이트 마다 VPN 연결을 통해 조직의 네트워크에 크로스-프레미스 네트워크에서 패킷이 경로에 연결할 수 있는 모든 CIDR 표기법으로 주소 공간 목록이 들어 있는 로컬 네트워크와 가상 네트워크를 구성 해야 조직의 온-프레미스 네트워크에 위치 합니다. 로컬 네트워크를 정의 하는 주소 공간 목록이 고유 해야 하며 다른 가상 네트워크 또는 다른 로컬 네트워크에 사용 되는 주소 공간으로 중첩 되지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="205bb-p107">To route packets from the cross-premises network to your organization network across the site-to-site VPN connection, you must configure the virtual network with a local network that has a list of the address spaces (in CIDR notation) for all of the reachable locations on your organization's on-premises network. The list of address spaces that define your local network must be unique and must not overlap with the address space used for other virtual networks or other local networks.</span></span>
  
<span data-ttu-id="205bb-p108">로컬 네트워크 주소 공간의 집합에 대해서는 테이블 L을 채웁니다. 세 개의 빈 항목이 나열되지만 일반적으로 더 많이 필요합니다. IT 부서에서 주소 공간의 목록을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="205bb-p108">For the set of local network address spaces, fill in Table L. Note that three blank entries are listed but you will typically need more. Work with your IT department to determine this list of address spaces.</span></span>
  
|<span data-ttu-id="205bb-204">**항목**</span><span class="sxs-lookup"><span data-stu-id="205bb-204">**Item**</span></span>|<span data-ttu-id="205bb-205">**로컬 네트워크 주소 공간**</span><span class="sxs-lookup"><span data-stu-id="205bb-205">**Local network address space**</span></span>|
|:-----|:-----|
|<span data-ttu-id="205bb-206">1.</span><span class="sxs-lookup"><span data-stu-id="205bb-206">1.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="205bb-207">2.</span><span class="sxs-lookup"><span data-stu-id="205bb-207">2.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="205bb-208">3.</span><span class="sxs-lookup"><span data-stu-id="205bb-208">3.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
   
 <span data-ttu-id="205bb-209">**테이블 L: 로컬 네트워크의 주소 접두사**</span><span class="sxs-lookup"><span data-stu-id="205bb-209">**Table L: Address prefixes for the local network**</span></span>
  
<span data-ttu-id="205bb-210">이제 Azure 인프라를 구축하여 Office 365용 페더레이션 인증을 호스트합니다.</span><span class="sxs-lookup"><span data-stu-id="205bb-210">Now let's begin building the Azure infrastructure to host your federated authentication for Office 365.</span></span>
  
> [!NOTE]
> <span data-ttu-id="205bb-p109">다음 명령 집합은 최신 버전의 Azure PowerShell을 사용합니다. [Azure PowerShell cmdlet으로 시작](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="205bb-p109">The following command sets use the latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span></span> 
  
<span data-ttu-id="205bb-213">먼저 Azure PowerShell 프롬프트를 시작하고 계정에 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="205bb-213">First, start an Azure PowerShell prompt and login to your account.</span></span>
  
```
Login-AzureRMAccount
```

> [!TIP]
> <span data-ttu-id="205bb-214">이 문서와 사용자 지정 설정을 기반으로 준비 간편 실행 PowerShell 명령 블록을 생성 하는 Microsoft Excel 구성 통합 문서에서 PowerShell 명령의 모든 텍스트 파일을 Azure의 Office 365에 대 한 페더레이션 인증 [를 참조 하십시오. 배포 키트](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664)합니다.</span><span class="sxs-lookup"><span data-stu-id="205bb-214">For a text file that has all of the PowerShell commands in this article and a Microsoft Excel configuration workbook that generates ready-to-run PowerShell command blocks based on your custom settings, see the [Federated Authentication for Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664).</span></span> 
  
<span data-ttu-id="205bb-215">다음 명령을 사용하여 구독 이름을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="205bb-215">Get your subscription name using the following command.</span></span>
  
```
Get-AzureRMSubscription | Sort Name | Select Name
```

<span data-ttu-id="205bb-216">Azure PowerShell의 이전 버전에 대 한이 명령을 대신 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="205bb-216">For older versions of Azure PowerShell, use this command instead.</span></span>
  
```
Get-AzureRMSubscription | Sort Name | Select SubscriptionName
```

<span data-ttu-id="205bb-p110">Azure 구독을 설정합니다. \< 및 > 문자를 포함하여 따옴표 안에 있는 모든 것을 올바른 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="205bb-p110">Set your Azure subscription. Replace everything within the quotes, including the \< and > characters, with the correct name.</span></span>
  
```
$subscr="<subscription name>"
Get-AzureRmSubscription -SubscriptionName $subscr | Select-AzureRmSubscription
```

<span data-ttu-id="205bb-p111">다음으로 새 리소스 그룹을 만듭니다. 고유한 리소스 그룹 이름의 집합을 확인하려면 이 명령을 사용하여 기존 리소스 그룹을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="205bb-p111">Next, create the new resource groups. To determine a unique set of resource group names, use this command to list your existing resource groups.</span></span>
  
```
Get-AzureRMResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

<span data-ttu-id="205bb-221">고유한 리소스 그룹 이름의 집합에 대해서는 다음 테이블을 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="205bb-221">Fill in the following table for the set of unique resource group names.</span></span>
  
|<span data-ttu-id="205bb-222">**항목**</span><span class="sxs-lookup"><span data-stu-id="205bb-222">**Item**</span></span>|<span data-ttu-id="205bb-223">**리소스 그룹 이름**</span><span class="sxs-lookup"><span data-stu-id="205bb-223">**Resource group name**</span></span>|<span data-ttu-id="205bb-224">**용도**</span><span class="sxs-lookup"><span data-stu-id="205bb-224">**Purpose**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="205bb-225">1.</span><span class="sxs-lookup"><span data-stu-id="205bb-225">1.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="205bb-226">도메인 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="205bb-226">Domain controllers</span></span>  <br/> |
|<span data-ttu-id="205bb-227">2.</span><span class="sxs-lookup"><span data-stu-id="205bb-227">2.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="205bb-228">AD FS 서버</span><span class="sxs-lookup"><span data-stu-id="205bb-228">AD FS servers</span></span>  <br/> |
|<span data-ttu-id="205bb-229">3.</span><span class="sxs-lookup"><span data-stu-id="205bb-229">3.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="205bb-230">웹 응용 프로그램 프록시 서버</span><span class="sxs-lookup"><span data-stu-id="205bb-230">Web application proxy servers</span></span>  <br/> |
|<span data-ttu-id="205bb-231">4.</span><span class="sxs-lookup"><span data-stu-id="205bb-231">4.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="205bb-232">인프라 구성 요소</span><span class="sxs-lookup"><span data-stu-id="205bb-232">Infrastructure elements</span></span>  <br/> |
   
 <span data-ttu-id="205bb-233">**테이블 R: 리소스 그룹**</span><span class="sxs-lookup"><span data-stu-id="205bb-233">**Table R: Resource groups**</span></span>
  
<span data-ttu-id="205bb-234">이러한 명령을 사용하여 새 리소스 그룹을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="205bb-234">Create your new resource groups with these commands.</span></span>
  
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

<span data-ttu-id="205bb-235">다음으로 Azure Virtual Network와 그 서브넷을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="205bb-235">Next, you create the Azure virtual network and its subnets.</span></span>
  
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

<span data-ttu-id="205bb-p112">다음으로, 네트워크 가상 컴퓨터에 있는 각 서브넷에 대 한 보안 그룹을 만듭니다. 서브넷 격리를 수행 하 여 특정 유형의 트래픽 허용 또는 서브넷의 네트워크 보안 그룹에 대 한 거부에 대 한 규칙을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="205bb-p112">Next, you create network security groups for each subnet that has virtual machines. To perform subnet isolation, you can add rules for the specific types of traffic allowed or denied to the network security group of a subnet.</span></span>
  
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

<span data-ttu-id="205bb-238">다음으로 이러한 명령을 사용하여 사이트 간 VPN 연결의 게이트웨이를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="205bb-238">Next, use these commands to create the gateways for the site-to-site VPN connection.</span></span>
  
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
> <span data-ttu-id="205bb-p113">개별 사용자의 연결 된 인증 모든 온-프레미스 리소스에 의존 하지 않습니다. 그러나이 사이트 마다 VPN 연결을 사용할 수 없게 하는 경우에 도메인 컨트롤러는 VNet에는 사용자 계정 및 온-프레미스 Windows Server AD에서 그룹에 대 한 업데이트를 받지 않습니다. 을 보장 하기 위해이 발생 하지 않는 사이트에 대 한 VPN 연결에 대 한 고가용성을 구성할 수 있습니다. 자세한 내용은 [항상 사용 가능한 크로스-프레미스 및 VNet-VNet 연결을](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable) 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="205bb-p113">Federated authentication of individual users does not rely on any on-premises resources. However, if this site-to-site VPN connection becomes unavailable, the domain controllers in the VNet will not receive updates to user accounts and groups made in the on-premises Windows Server AD. To ensure this does not happen, you can configure high availability for your site-to-site VPN connection. For more information, see [Highly Available Cross-Premises and VNet-to-VNet Connectivity](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)</span></span>
  
<span data-ttu-id="205bb-243">그런 다음 이 명령의 디스플레이에서 가상 네트워크용 Azure VPN 게이트웨이의 공용 IPv4 주소를 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="205bb-243">Next, record the public IPv4 address of the Azure VPN gateway for your virtual network from the display of this command:</span></span>
  
```
Get-AzureRMPublicIpAddress -Name $publicGatewayVipName -ResourceGroupName $rgName
```

<span data-ttu-id="205bb-p114">계속해서 Azure VPN 게이트웨이에 연결할 온-프레미스 VPN 장치를 구성합니다. 자세한 내용은 [VPN 장치 구성](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="205bb-p114">Next, configure your on-premises VPN device to connect to the Azure VPN gateway. For more information, see [Configure your VPN device](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).</span></span>
  
<span data-ttu-id="205bb-246">온-프레미스 VPN 장치를 구성하려면 다음 항목이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="205bb-246">To configure your on-premises VPN device, you will need the following:</span></span>
  
- <span data-ttu-id="205bb-247">Azure VPN 게이트웨이의 공용 IPv4 주소.</span><span class="sxs-lookup"><span data-stu-id="205bb-247">The public IPv4 address of the Azure VPN gateway.</span></span>
    
- <span data-ttu-id="205bb-248">사이트 간 VPN 연결용 IPsec 미리 공유한 키(테이블 V - 항목 5 - 값 열).</span><span class="sxs-lookup"><span data-stu-id="205bb-248">The IPsec pre-shared key for the site-to-site VPN connection (Table V - Item 5 - Value column).</span></span>
    
<span data-ttu-id="205bb-p115">다음으로 가상 네트워크의 주소 공간이 온-프레미스 네트워크에서 연결 가능한지 확인합니다. 일반적으로 가상 네트워크 주소 공간에 해당하는 경로를 VPN 장치에 추가한 다음 이 경로를 조직 네트워크의 나머지 라우팅 인프라에 보급합니다. IT 부서에서 이 작업을 수행하는 방법을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="205bb-p115">Next, ensure that the address space of the virtual network is reachable from your on-premises network. This is usually done by adding a route corresponding to the virtual network address space to your VPN device and then advertising that route to the rest of the routing infrastructure of your organization network. Work with your IT department to determine how to do this.</span></span>
  
<span data-ttu-id="205bb-p116">그 다음 세 가지 가용성 집합의 이름을 정의합니다. 테이블 A를 채웁니다. </span><span class="sxs-lookup"><span data-stu-id="205bb-p116">Next, define the names of three availability sets. Fill out Table A.</span></span> 
  
|<span data-ttu-id="205bb-254">**항목**</span><span class="sxs-lookup"><span data-stu-id="205bb-254">**Item**</span></span>|<span data-ttu-id="205bb-255">**용도**</span><span class="sxs-lookup"><span data-stu-id="205bb-255">**Purpose**</span></span>|<span data-ttu-id="205bb-256">**가용성 집합 이름**</span><span class="sxs-lookup"><span data-stu-id="205bb-256">**Availability set name**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="205bb-257">1.</span><span class="sxs-lookup"><span data-stu-id="205bb-257">1.</span></span>  <br/> |<span data-ttu-id="205bb-258">도메인 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="205bb-258">Domain controllers</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="205bb-259">2.</span><span class="sxs-lookup"><span data-stu-id="205bb-259">2.</span></span>  <br/> |<span data-ttu-id="205bb-260">AD FS 서버</span><span class="sxs-lookup"><span data-stu-id="205bb-260">AD FS servers</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="205bb-261">3.</span><span class="sxs-lookup"><span data-stu-id="205bb-261">3.</span></span>  <br/> |<span data-ttu-id="205bb-262">웹 응용 프로그램 프록시 서버</span><span class="sxs-lookup"><span data-stu-id="205bb-262">Web application proxy servers</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
   
 <span data-ttu-id="205bb-263">**테이블 A: 가용성 집합**</span><span class="sxs-lookup"><span data-stu-id="205bb-263">**Table A: Availability sets**</span></span>
  
<span data-ttu-id="205bb-264">2, 3 및 4단계에서 가상 컴퓨터를 만들 때 이러한 이름이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="205bb-264">You will need these names when you create the virtual machines in phases 2, 3, and 4.</span></span>
  
<span data-ttu-id="205bb-265">이러한 Azure PowerShell 명령을 사용하여 새 가용성 집합을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="205bb-265">Create the new availability sets with these Azure PowerShell commands.</span></span>
  
```
$locName="<the Azure location for your new resource group>"
$rgName="<Table R - Item 1 - Resource group name column>"
$avName="<Table A - Item 1 - Availability set name column>"
New-AzureRMAvailabilitySet -ResourceGroupName $rgName -Name $avName -Location $locName -Sku Aligned  -PlatformUpdateDomainCount 5 -PlatformFaultDomainCount 2
$rgName="<Table R - Item 2 - Resource group name column>"
$avName="<Table A - Item 2 - Availability set name column>"
New-AzureRMAvailabilitySet -ResourceGroupName $rgName -Name $avName -Location $locName -Sku Aligned  -PlatformUpdateDomainCount 5 -PlatformFaultDomainCount 2
$rgName="<Table R - Item 3 - Resource group name column>"
$avName="<Table A - Item 3 - Availability set name column>"
New-AzureRMAvailabilitySet -ResourceGroupName $rgName -Name $avName -Location $locName -Sku Aligned  -PlatformUpdateDomainCount 5 -PlatformFaultDomainCount 2
```

<span data-ttu-id="205bb-266">이 단계를 성공적으로 완료하면 다음 구성을 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="205bb-266">This is the configuration resulting from the successful completion of this phase.</span></span>
  
<span data-ttu-id="205bb-267">**1단계: Office 365 고가용성 페더레이션 인증용 Azure 인프라**</span><span class="sxs-lookup"><span data-stu-id="205bb-267">**Phase 1: The Azure infrastructure for high availability federated authentication for Office 365**</span></span>

![Azure 인프라를 포함한 Azure에서 고가용성 Office 365 페더레이션 인증 1단계](media/4e7ba678-07df-40ce-b372-021bf7fc91fa.png)
  
## <a name="next-step"></a><span data-ttu-id="205bb-269">다음 단계</span><span class="sxs-lookup"><span data-stu-id="205bb-269">Next step</span></span>

<span data-ttu-id="205bb-270">[High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md)를 사용하여 이 작업을 계속 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="205bb-270">Use [High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) to continue with the configuration of this workload.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="205bb-271">참고 항목</span><span class="sxs-lookup"><span data-stu-id="205bb-271">See Also</span></span>

[<span data-ttu-id="205bb-272">Azure에서 Office 365용 고가용성 페더레이션 인증 배포</span><span class="sxs-lookup"><span data-stu-id="205bb-272">Deploy high availability federated authentication for Office 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="205bb-273">Office 365 개발/테스트 환경에 대 한 페더레이션된 id</span><span class="sxs-lookup"><span data-stu-id="205bb-273">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="205bb-274">클라우드 채택 및 하이브리드 솔루션</span><span class="sxs-lookup"><span data-stu-id="205bb-274">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="205bb-275">Office 365 ID 및 Azure Active Directory 이해</span><span class="sxs-lookup"><span data-stu-id="205bb-275">Understanding Office 365 identity and Azure Active Directory</span></span>](about-office-365-identity.md)


