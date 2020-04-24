---
title: 고가용성 페더레이션 인증 1 단계 Azure 구성
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/25/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Ent_Solutions
ms.assetid: 91266aac-4d00-4b5f-b424-86a1a837792c
description: '요약: Microsoft Azure 인프라를 구성하여 Office 365 페더레이션 인증의 고가용성을 호스트합니다.'
ms.openlocfilehash: 9f2991ef495093f2aed01e57f47dab3371b97de3
ms.sourcegitcommit: a578baeb0d8b85941c13afa268447d2592f89fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2020
ms.locfileid: "43793831"
---
# <a name="high-availability-federated-authentication-phase-1-configure-azure"></a><span data-ttu-id="b6110-103">고가용성 페더레이션 인증 1단계: Azure 구성</span><span class="sxs-lookup"><span data-stu-id="b6110-103">High availability federated authentication Phase 1: Configure Azure</span></span>

<span data-ttu-id="b6110-104">이 단계에서는 2, 3, 4 단계에서 가상 컴퓨터를 호스팅할 Azure의 리소스 그룹, VNet (가상 네트워크) 및 가용성 집합을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b6110-104">In this phase, you create the resource groups, virtual network (VNet), and availability sets in Azure that will host the virtual machines in phases 2, 3, and 4.</span></span> <span data-ttu-id="b6110-105">[2 단계: 도메인 컨트롤러 구성](high-availability-federated-authentication-phase-2-configure-domain-controllers.md)으로 넘어가기 전에이 단계를 완료 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6110-105">You must complete this phase before moving on to [Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md).</span></span> <span data-ttu-id="b6110-106">모든 단계에 대해 [Azure에서 Office 365에 대 한 고가용성 페더레이션 인증 배포](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b6110-106">See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
<span data-ttu-id="b6110-107">Azure는 다음과 같은 기본 구성 요소로 구축 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6110-107">Azure must be provisioned with these basic components:</span></span>
  
- <span data-ttu-id="b6110-108">리소스 그룹</span><span class="sxs-lookup"><span data-stu-id="b6110-108">Resource groups</span></span>
    
- <span data-ttu-id="b6110-109">Azure virtual machines를 호스팅하기 위한 서브넷이 있는 프레미스 간 Azure VNet (가상 네트워크)</span><span class="sxs-lookup"><span data-stu-id="b6110-109">A cross-premises Azure virtual network (VNet) with subnets for hosting the Azure virtual machines</span></span>
    
- <span data-ttu-id="b6110-110">수행 중인 서브넷 격리용 네트워크 보안 그룹</span><span class="sxs-lookup"><span data-stu-id="b6110-110">Network security groups for performing subnet isolation</span></span>
    
- <span data-ttu-id="b6110-111">가용성 집합</span><span class="sxs-lookup"><span data-stu-id="b6110-111">Availability sets</span></span>
    
## <a name="configure-azure-components"></a><span data-ttu-id="b6110-112">Azure 구성 요소 구성</span><span class="sxs-lookup"><span data-stu-id="b6110-112">Configure Azure components</span></span>

<span data-ttu-id="b6110-113">Azure 구성 요소를 구성하기 전에 다음 테이블을 채워야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6110-113">Before you begin configuring Azure components, fill in the following tables.</span></span> <span data-ttu-id="b6110-114">Azure 구성 프로시저를 지원하려면 이 섹션을 인쇄하여 필요한 정보를 적어두거나 이 섹션을 문서에 복사하여 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="b6110-114">To assist you in the procedures for configuring Azure, print this section and write down the needed information or copy this section to a document and fill it in.</span></span> <span data-ttu-id="b6110-115">VNet의 설정에 대 한 자세한 내용은 Table V를 입력 하십시오.</span><span class="sxs-lookup"><span data-stu-id="b6110-115">For the settings of the VNet, fill in Table V.</span></span>
  
|<span data-ttu-id="b6110-116">**항목**</span><span class="sxs-lookup"><span data-stu-id="b6110-116">**Item**</span></span>|<span data-ttu-id="b6110-117">**구성 설정**</span><span class="sxs-lookup"><span data-stu-id="b6110-117">**Configuration setting**</span></span>|<span data-ttu-id="b6110-118">**설명**</span><span class="sxs-lookup"><span data-stu-id="b6110-118">**Description**</span></span>|<span data-ttu-id="b6110-119">**값**</span><span class="sxs-lookup"><span data-stu-id="b6110-119">**Value**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="b6110-120">1.</span><span class="sxs-lookup"><span data-stu-id="b6110-120">1.</span></span>  <br/> |<span data-ttu-id="b6110-121">VNet 이름</span><span class="sxs-lookup"><span data-stu-id="b6110-121">VNet name</span></span>  <br/> |<span data-ttu-id="b6110-122">VNet에 할당할 이름 (예:: Fedauthnet)입니다.</span><span class="sxs-lookup"><span data-stu-id="b6110-122">A name to assign to the VNet (example FedAuthNet).</span></span>  <br/> |![라인](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="b6110-124">2.</span><span class="sxs-lookup"><span data-stu-id="b6110-124">2.</span></span>  <br/> |<span data-ttu-id="b6110-125">VNet 위치</span><span class="sxs-lookup"><span data-stu-id="b6110-125">VNet location</span></span>  <br/> |<span data-ttu-id="b6110-126">가상 네트워크를 포함 하는 지역별 Azure 데이터 센터입니다.</span><span class="sxs-lookup"><span data-stu-id="b6110-126">The regional Azure datacenter that will contain the virtual network.</span></span>  <br/> |![라인](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="b6110-128">3.</span><span class="sxs-lookup"><span data-stu-id="b6110-128">3.</span></span>  <br/> |<span data-ttu-id="b6110-129">VPN 장치 IP 주소</span><span class="sxs-lookup"><span data-stu-id="b6110-129">VPN device IP address</span></span>  <br/> |<span data-ttu-id="b6110-130">인터넷에서 VPN 장치 인터페이스의 공용 IPv4 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="b6110-130">The public IPv4 address of your VPN device's interface on the Internet.</span></span>  <br/> |![라인](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="b6110-132">4.</span><span class="sxs-lookup"><span data-stu-id="b6110-132">4.</span></span>  <br/> |<span data-ttu-id="b6110-133">VNet 주소 공간</span><span class="sxs-lookup"><span data-stu-id="b6110-133">VNet address space</span></span>  <br/> |<span data-ttu-id="b6110-p103">가상 네트워크의 주소 공간입니다. IT 부서에서 이 주소 공간을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b6110-p103">The address space for the virtual network. Work with your IT department to determine this address space.</span></span>  <br/> |![라인](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="b6110-137">5.</span><span class="sxs-lookup"><span data-stu-id="b6110-137">5.</span></span>  <br/> |<span data-ttu-id="b6110-138">IPsec 공유 키</span><span class="sxs-lookup"><span data-stu-id="b6110-138">IPsec shared key</span></span>  <br/> |<span data-ttu-id="b6110-p104">사이트 간 VPN 연결의 양측을 인증하는 데 사용되는 32자의 무작위 영숫자 문자열입니다. IT 또는 보안 부서에서 이 키 값을 확인합니다. 또한, [IPsec 미리 공유한 키의 무작위 문자열 만들기](https://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx)를 참조하세요.  </span><span class="sxs-lookup"><span data-stu-id="b6110-p104">A 32-character random, alphanumeric string that will be used to authenticate both sides of the site-to-site VPN connection. Work with your IT or security department to determine this key value. Alternately, see [Create a random string for an IPsec preshared key](https://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx).  </span></span><br/> |![라인](./media/Common-Images/TableLine.png)  <br/> |
   
 <span data-ttu-id="b6110-143">**테이블 V: 프레미스 간 가상 네트워크 구성**</span><span class="sxs-lookup"><span data-stu-id="b6110-143">**Table V: Cross-premises virtual network configuration**</span></span>
  
<span data-ttu-id="b6110-p105">다음으로 이 솔루션의 서브넷에 대해서는 테이블 S를 채웁니다. 모든 주소 공간은 CIDR(Classless Interdomain Routing) 형식이어야 하며 네트워크 접두사 형식이라고도 합니다. 예를 들어 10.24.64.0/20입니다.</span><span class="sxs-lookup"><span data-stu-id="b6110-p105">Next, fill in Table S for the subnets of this solution. All address spaces should be in Classless Interdomain Routing (CIDR) format, also known as network prefix format. An example is 10.24.64.0/20.</span></span>
  
<span data-ttu-id="b6110-147">처음 3 개 서브넷의 경우 가상 네트워크 주소 공간에 따라 이름과 단일 IP 주소 공간을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6110-147">For the first three subnets, specify a name and a single IP address space based on the virtual network address space.</span></span> <span data-ttu-id="b6110-148">게이트웨이 서브넷의 경우 Azure 게이트웨이 서브넷의 27 비트 주소 공간 (/27 접두사 길이)을 다음과 같이 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6110-148">For the gateway subnet, determine the 27-bit address space (with a /27 prefix length) for the Azure gateway subnet with the following:</span></span>
  
1. <span data-ttu-id="b6110-149">VNet의 주소 공간에 있는 변수 비트를 1(게이트웨이 서브넷에서 사용하는 비트까지)로 설정한 다음 나머지 비트를 0으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="b6110-149">Set the variable bits in the address space of the VNet to 1, up to the bits being used by the gateway subnet, then set the remaining bits to 0.</span></span>
    
2. <span data-ttu-id="b6110-150">결과 비트를 10진수로 변환하고 이를 접두사 길이가 게이트웨이 서브넷 크기로 설정된 주소 공간으로 표현합니다.</span><span class="sxs-lookup"><span data-stu-id="b6110-150">Convert the resulting bits to decimal and express it as an address space with the prefix length set to the size of the gateway subnet.</span></span>
    
<span data-ttu-id="b6110-151">이러한 계산을 수행 하는 PowerShell 명령 블록 및 c # 또는 Python 콘솔 응용 프로그램의 경우 [Azure 게이트웨이 서브넷에 대 한 주소 공간 계산기](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b6110-151">See [Address space calculator for Azure gateway subnets](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) for a PowerShell command block and C# or Python console application that performs this calculation for you.</span></span>
  
<span data-ttu-id="b6110-152">IT 부서에서 가상 네트워크 주소 공간의 이러한 주소 공간을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b6110-152">Work with your IT department to determine these address spaces from the virtual network address space.</span></span>
  
|<span data-ttu-id="b6110-153">**항목**</span><span class="sxs-lookup"><span data-stu-id="b6110-153">**Item**</span></span>|<span data-ttu-id="b6110-154">**서브넷 이름**</span><span class="sxs-lookup"><span data-stu-id="b6110-154">**Subnet name**</span></span>|<span data-ttu-id="b6110-155">**서브넷 주소 공간**</span><span class="sxs-lookup"><span data-stu-id="b6110-155">**Subnet address space**</span></span>|<span data-ttu-id="b6110-156">**용도**</span><span class="sxs-lookup"><span data-stu-id="b6110-156">**Purpose**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="b6110-157">1.</span><span class="sxs-lookup"><span data-stu-id="b6110-157">1.</span></span>  <br/> |![라인](./media/Common-Images/TableLine.png)  <br/> |![라인](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="b6110-160">AD DS (Active Directory 도메인 서비스) 도메인 컨트롤러 및 디렉터리 동기화 서버 Vm (가상 컴퓨터)에서 사용 하는 서브넷입니다.</span><span class="sxs-lookup"><span data-stu-id="b6110-160">The subnet used by the Active Directory Domain Services (AD DS) domain controller and directory synchronization server virtual machines (VMs).</span></span>  <br/> |
|<span data-ttu-id="b6110-161">2.</span><span class="sxs-lookup"><span data-stu-id="b6110-161">2.</span></span>  <br/> |![라인](./media/Common-Images/TableLine.png)  <br/> |![라인](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="b6110-164">AD FS Vm에서 사용 하는 서브넷입니다.</span><span class="sxs-lookup"><span data-stu-id="b6110-164">The subnet used by the AD FS VMs.</span></span>  <br/> |
|<span data-ttu-id="b6110-165">3.</span><span class="sxs-lookup"><span data-stu-id="b6110-165">3.</span></span>  <br/> |![라인](./media/Common-Images/TableLine.png)  <br/> |![라인](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="b6110-168">웹 응용 프로그램 프록시 Vm에서 사용 하는 서브넷입니다.</span><span class="sxs-lookup"><span data-stu-id="b6110-168">The subnet used by the web application proxy VMs.</span></span>  <br/> |
|<span data-ttu-id="b6110-169">4.</span><span class="sxs-lookup"><span data-stu-id="b6110-169">4.</span></span>  <br/> |<span data-ttu-id="b6110-170">GatewaySubnet</span><span class="sxs-lookup"><span data-stu-id="b6110-170">GatewaySubnet</span></span>  <br/> |![라인](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="b6110-172">Azure 게이트웨이 Vm에서 사용 하는 서브넷입니다.</span><span class="sxs-lookup"><span data-stu-id="b6110-172">The subnet used by the Azure gateway VMs.</span></span>  <br/> |
   
 <span data-ttu-id="b6110-173">**테이블 S: 가상 네트워크의 서브넷**</span><span class="sxs-lookup"><span data-stu-id="b6110-173">**Table S: Subnets in the virtual network**</span></span>
  
<span data-ttu-id="b6110-174">다음으로 가상 컴퓨터와 부하 분산 장치 인스턴스에 할당된 고정 IP 주소에 대해서는 테이블 I를 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="b6110-174">Next, fill in Table I for the static IP addresses assigned to virtual machines and load balancer instances.</span></span>
  
|<span data-ttu-id="b6110-175">**항목**</span><span class="sxs-lookup"><span data-stu-id="b6110-175">**Item**</span></span>|<span data-ttu-id="b6110-176">**용도**</span><span class="sxs-lookup"><span data-stu-id="b6110-176">**Purpose**</span></span>|<span data-ttu-id="b6110-177">**서브넷의 IP 주소**</span><span class="sxs-lookup"><span data-stu-id="b6110-177">**IP address on the subnet**</span></span>|<span data-ttu-id="b6110-178">**값**</span><span class="sxs-lookup"><span data-stu-id="b6110-178">**Value**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="b6110-179">1.</span><span class="sxs-lookup"><span data-stu-id="b6110-179">1.</span></span>  <br/> |<span data-ttu-id="b6110-180">첫 번째 도메인 컨트롤러의 고정 IP 주소</span><span class="sxs-lookup"><span data-stu-id="b6110-180">Static IP address of the first domain controller</span></span>  <br/> |<span data-ttu-id="b6110-181">테이블 S의 항목 1에 정의된 서브넷의 주소 공간에 사용할 수 있는 네 번째 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="b6110-181">The fourth possible IP address for the address space of the subnet defined in Item 1 of Table S.</span></span>  <br/> |![라인](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="b6110-183">2.</span><span class="sxs-lookup"><span data-stu-id="b6110-183">2.</span></span>  <br/> |<span data-ttu-id="b6110-184">두 번째 도메인 컨트롤러의 고정 IP 주소</span><span class="sxs-lookup"><span data-stu-id="b6110-184">Static IP address of the second domain controller</span></span>  <br/> |<span data-ttu-id="b6110-185">테이블 S의 항목 1에 정의된 서브넷의 주소 공간에 사용할 수 있는 다섯 번째 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="b6110-185">The fifth possible IP address for the address space of the subnet defined in Item 1 of Table S.</span></span>  <br/> |![라인](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="b6110-187">3.</span><span class="sxs-lookup"><span data-stu-id="b6110-187">3.</span></span>  <br/> |<span data-ttu-id="b6110-188">디렉터리 동기화 서버의 고정 IP 주소</span><span class="sxs-lookup"><span data-stu-id="b6110-188">Static IP address of the directory synchronization server</span></span>  <br/> |<span data-ttu-id="b6110-189">테이블 S의 항목 1에 정의 된 서브넷의 주소 공간에 사용할 수 있는 여섯 번째 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="b6110-189">The sixth possible IP address for the address space of the subnet defined in Item 1 of Table S.</span></span>  <br/> |![라인](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="b6110-191">4.</span><span class="sxs-lookup"><span data-stu-id="b6110-191">4.</span></span>  <br/> |<span data-ttu-id="b6110-192">AD FS 서버에 대 한 내부 부하 분산 장치의 고정 IP 주소</span><span class="sxs-lookup"><span data-stu-id="b6110-192">Static IP address of the internal load balancer for the AD FS servers</span></span>  <br/> |<span data-ttu-id="b6110-193">테이블 S의 항목 2에 정의된 서브넷의 주소 공간에 사용할 수 있는 네 번째 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="b6110-193">The fourth possible IP address for the address space of the subnet defined in Item 2 of Table S.</span></span>  <br/> |![라인](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="b6110-195">5.</span><span class="sxs-lookup"><span data-stu-id="b6110-195">5.</span></span>  <br/> |<span data-ttu-id="b6110-196">첫 번째 AD FS 서버의 고정 IP 주소</span><span class="sxs-lookup"><span data-stu-id="b6110-196">Static IP address of the first AD FS server</span></span>  <br/> |<span data-ttu-id="b6110-197">테이블 S의 항목 2에 정의된 서브넷의 주소 공간에 사용할 수 있는 다섯 번째 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="b6110-197">The fifth possible IP address for the address space of the subnet defined in Item 2 of Table S.</span></span>  <br/> |![라인](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="b6110-199">6.</span><span class="sxs-lookup"><span data-stu-id="b6110-199">6.</span></span>  <br/> |<span data-ttu-id="b6110-200">두 번째 AD FS 서버의 고정 IP 주소</span><span class="sxs-lookup"><span data-stu-id="b6110-200">Static IP address of the second AD FS server</span></span>  <br/> |<span data-ttu-id="b6110-201">테이블 S의 항목 2에 정의된 서브넷의 주소 공간에 사용할 수 있는 여섯 번째 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="b6110-201">The sixth possible IP address for the address space of the subnet defined in Item 2 of Table S.</span></span>  <br/> |![라인](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="b6110-203">7.</span><span class="sxs-lookup"><span data-stu-id="b6110-203">7.</span></span>  <br/> |<span data-ttu-id="b6110-204">첫 번째 웹 응용 프로그램 프록시 서버의 고정 IP 주소</span><span class="sxs-lookup"><span data-stu-id="b6110-204">Static IP address of the first web application proxy server</span></span>  <br/> |<span data-ttu-id="b6110-205">테이블 S의 항목 3에 정의된 서브넷의 주소 공간에 사용할 수 있는 네 번째 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="b6110-205">The fourth possible IP address for the address space of the subnet defined in Item 3 of Table S.</span></span>  <br/> |![라인](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="b6110-207">8.</span><span class="sxs-lookup"><span data-stu-id="b6110-207">8.</span></span>  <br/> |<span data-ttu-id="b6110-208">두 번째 웹 응용 프로그램 프록시 서버의 고정 IP 주소</span><span class="sxs-lookup"><span data-stu-id="b6110-208">Static IP address of the second web application proxy server</span></span>  <br/> |<span data-ttu-id="b6110-209">테이블 S의 항목 3에 정의된 서브넷의 주소 공간에 사용할 수 있는 다섯 번째 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="b6110-209">The fifth possible IP address for the address space of the subnet defined in Item 3 of Table S.</span></span>  <br/> |![라인](./media/Common-Images/TableLine.png)  <br/> |
   
 <span data-ttu-id="b6110-211">**테이블 I: 가상 네트워크의 고정 IP 주소**</span><span class="sxs-lookup"><span data-stu-id="b6110-211">**Table I: Static IP addresses in the virtual network**</span></span>
  
<span data-ttu-id="b6110-212">가상 네트워크에서 도메인 컨트롤러를 처음 설정할 때 사용 하려는 온-프레미스 네트워크의 두 DNS (Domain Name System) 서버에 대해 표 D를 입력 합니다. IT 부서와 협력 하 여이 목록을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6110-212">For two Domain Name System (DNS) servers in your on-premises network that you want to use when initially setting up the domain controllers in your virtual network, fill in Table D. Work with your IT department to determine this list.</span></span>
  
|<span data-ttu-id="b6110-213">**항목**</span><span class="sxs-lookup"><span data-stu-id="b6110-213">**Item**</span></span>|<span data-ttu-id="b6110-214">**DNS 서버 식별 이름**</span><span class="sxs-lookup"><span data-stu-id="b6110-214">**DNS server friendly name**</span></span>|<span data-ttu-id="b6110-215">**DNS 서버 IP 주소**</span><span class="sxs-lookup"><span data-stu-id="b6110-215">**DNS server IP address**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="b6110-216">1.</span><span class="sxs-lookup"><span data-stu-id="b6110-216">1.</span></span>  <br/> |![라인](./media/Common-Images/TableLine.png)  <br/> |![라인](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="b6110-219">2.</span><span class="sxs-lookup"><span data-stu-id="b6110-219">2.</span></span>  <br/> |![라인](./media/Common-Images/TableLine.png)  <br/> |![라인](./media/Common-Images/TableLine.png)  <br/> |
   
 <span data-ttu-id="b6110-222">**테이블 D: 온-프레미스 DNS 서버**</span><span class="sxs-lookup"><span data-stu-id="b6110-222">**Table D: On-premises DNS servers**</span></span>
  
<span data-ttu-id="b6110-223">사이트 간 VPN 연결을 통해 크로스-프레미스 네트워크에서 조직 네트워크로 패킷을 라우팅하려면 조직의 온-프레미스 네트워크에 있는 모든 위치에 대 한 주소 공간 (CIDR 표기법) 목록이 있는 로컬 네트워크를 사용 하 여 가상 네트워크를 구성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6110-223">To route packets from the cross-premises network to your organization network across the site-to-site VPN connection, you must configure the virtual network with a local network that has a list of the address spaces (in CIDR notation) for all of the reachable locations on your organization's on-premises network.</span></span> <span data-ttu-id="b6110-224">로컬 네트워크를 정의하는 주소 공간 목록은 고유해야 하며 다른 가상 네트워크 또는 다른 로컬 네트워크에 사용되는 주소 공간과 중복되면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6110-224">The list of address spaces that define your local network must be unique and must not overlap with the address space used for other virtual networks or other local networks.</span></span>
  
<span data-ttu-id="b6110-p108">로컬 네트워크 주소 공간의 집합에 대해서는 테이블 L을 채웁니다. 세 개의 빈 항목이 나열되지만 일반적으로 더 많이 필요합니다. IT 부서에서 주소 공간의 목록을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b6110-p108">For the set of local network address spaces, fill in Table L. Note that three blank entries are listed but you will typically need more. Work with your IT department to determine this list of address spaces.</span></span>
  
|<span data-ttu-id="b6110-227">**항목**</span><span class="sxs-lookup"><span data-stu-id="b6110-227">**Item**</span></span>|<span data-ttu-id="b6110-228">**로컬 네트워크 주소 공간**</span><span class="sxs-lookup"><span data-stu-id="b6110-228">**Local network address space**</span></span>|
|:-----|:-----|
|<span data-ttu-id="b6110-229">1.</span><span class="sxs-lookup"><span data-stu-id="b6110-229">1.</span></span>  <br/> |![라인](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="b6110-231">2.</span><span class="sxs-lookup"><span data-stu-id="b6110-231">2.</span></span>  <br/> |![라인](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="b6110-233">3.</span><span class="sxs-lookup"><span data-stu-id="b6110-233">3.</span></span>  <br/> |![라인](./media/Common-Images/TableLine.png)  <br/> |
   
 <span data-ttu-id="b6110-235">**테이블 L: 로컬 네트워크의 주소 접두사**</span><span class="sxs-lookup"><span data-stu-id="b6110-235">**Table L: Address prefixes for the local network**</span></span>
  
<span data-ttu-id="b6110-236">이제 Office 365에 대 한 페더레이션 인증을 호스트 하기 위한 Azure 인프라를 구축 해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="b6110-236">Now let's begin building the Azure infrastructure to host your federated authentication for Office 365.</span></span>
  
> [!NOTE]
> <span data-ttu-id="b6110-237">다음 명령 집합은 최신 버전의 Azure PowerShell을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b6110-237">The following command sets use the latest version of Azure PowerShell.</span></span> <span data-ttu-id="b6110-238">[Azure PowerShell을 시작 하기를](https://docs.microsoft.com/powershell/azure/get-started-azureps)참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b6110-238">See [Get started with Azure PowerShell](https://docs.microsoft.com/powershell/azure/get-started-azureps).</span></span> 
  
<span data-ttu-id="b6110-239">먼저 Azure PowerShell 프롬프트를 시작하고 계정에 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="b6110-239">First, start an Azure PowerShell prompt and login to your account.</span></span>
  
```powershell
Connect-AzAccount
```

> [!TIP]
> <span data-ttu-id="b6110-240">사용자 지정 설정에 따라 실행 가능한 PowerShell 명령 블록을 생성 하려면이 [Microsoft Excel 구성 통합 문서](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/deploy-high-availability-federated-authentication-for-office-365-in-azure/O365FedAuthInAzure_Config.xlsx)를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6110-240">To generate ready-to-run PowerShell command blocks based on your custom settings, use this [Microsoft Excel configuration workbook](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/deploy-high-availability-federated-authentication-for-office-365-in-azure/O365FedAuthInAzure_Config.xlsx).</span></span> 

<span data-ttu-id="b6110-241">다음 명령을 사용하여 구독 이름을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b6110-241">Get your subscription name using the following command.</span></span>
  
```powershell
Get-AzSubscription | Sort Name | Select Name
```

<span data-ttu-id="b6110-242">이전 버전의 Azure PowerShell의 경우 대신이 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6110-242">For older versions of Azure PowerShell, use this command instead.</span></span>
  
```powershell
Get-AzSubscription | Sort Name | Select SubscriptionName
```

<span data-ttu-id="b6110-243">Azure 구독을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="b6110-243">Set your Azure subscription.</span></span> <span data-ttu-id="b6110-244">\< 및 > 문자를 포함 하 여 따옴표 안에 있는 모든 내용을 올바른 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="b6110-244">Replace everything within the quotes, including the \< and > characters, with the correct name.</span></span>
  
```powershell
$subscrName="<subscription name>"
Select-AzSubscription -SubscriptionName $subscrName
```

<span data-ttu-id="b6110-245">다음으로 새 리소스 그룹을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b6110-245">Next, create the new resource groups.</span></span> <span data-ttu-id="b6110-246">고유한 리소스 그룹 이름의 집합을 확인하려면 이 명령을 사용하여 기존 리소스 그룹을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="b6110-246">To determine a unique set of resource group names, use this command to list your existing resource groups.</span></span>
  
```powershell
Get-AzResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

<span data-ttu-id="b6110-247">고유한 리소스 그룹 이름의 집합에 대해서는 다음 테이블을 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="b6110-247">Fill in the following table for the set of unique resource group names.</span></span>
  
|<span data-ttu-id="b6110-248">**항목**</span><span class="sxs-lookup"><span data-stu-id="b6110-248">**Item**</span></span>|<span data-ttu-id="b6110-249">**리소스 그룹 이름**</span><span class="sxs-lookup"><span data-stu-id="b6110-249">**Resource group name**</span></span>|<span data-ttu-id="b6110-250">**용도**</span><span class="sxs-lookup"><span data-stu-id="b6110-250">**Purpose**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="b6110-251">1.</span><span class="sxs-lookup"><span data-stu-id="b6110-251">1.</span></span>  <br/> |![라인](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="b6110-253">도메인 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="b6110-253">Domain controllers</span></span>  <br/> |
|<span data-ttu-id="b6110-254">2.</span><span class="sxs-lookup"><span data-stu-id="b6110-254">2.</span></span>  <br/> |![라인](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="b6110-256">AD FS 서버</span><span class="sxs-lookup"><span data-stu-id="b6110-256">AD FS servers</span></span>  <br/> |
|<span data-ttu-id="b6110-257">3.</span><span class="sxs-lookup"><span data-stu-id="b6110-257">3.</span></span>  <br/> |![라인](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="b6110-259">웹 응용 프로그램 프록시 서버</span><span class="sxs-lookup"><span data-stu-id="b6110-259">Web application proxy servers</span></span>  <br/> |
|<span data-ttu-id="b6110-260">4.</span><span class="sxs-lookup"><span data-stu-id="b6110-260">4.</span></span>  <br/> |![라인](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="b6110-262">인프라 구성 요소</span><span class="sxs-lookup"><span data-stu-id="b6110-262">Infrastructure elements</span></span>  <br/> |
   
 <span data-ttu-id="b6110-263">**테이블 R: 리소스 그룹**</span><span class="sxs-lookup"><span data-stu-id="b6110-263">**Table R: Resource groups**</span></span>
  
<span data-ttu-id="b6110-264">이러한 명령을 사용하여 새 리소스 그룹을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b6110-264">Create your new resource groups with these commands.</span></span>
  
```powershell
$locName="<an Azure location, such as West US>"
$rgName="<Table R - Item 1 - Name column>"
New-AzResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 2 - Name column>"
New-AzResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 3 - Name column>"
New-AzResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 4 - Name column>"
New-AzResourceGroup -Name $rgName -Location $locName
```

<span data-ttu-id="b6110-265">다음으로 Azure virtual network 및 해당 서브넷을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b6110-265">Next, you create the Azure virtual network and its subnets.</span></span>
  
```powershell
$rgName="<Table R - Item 4 - Resource group name column>"
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$vnetAddrPrefix="<Table V - Item 4 - Value column>"
$dnsServers=@( "<Table D - Item 1 - DNS server IP address column>", "<Table D - Item 2 - DNS server IP address column>" )
# Get the shortened version of the location
$locShortName=(Get-AzResourceGroup -Name $rgName).Location

# Create the subnets
$subnet1Name="<Table S - Item 1 - Subnet name column>"
$subnet1Prefix="<Table S - Item 1 - Subnet address space column>"
$subnet1=New-AzVirtualNetworkSubnetConfig -Name $subnet1Name -AddressPrefix $subnet1Prefix
$subnet2Name="<Table S - Item 2 - Subnet name column>"
$subnet2Prefix="<Table S - Item 2 - Subnet address space column>"
$subnet2=New-AzVirtualNetworkSubnetConfig -Name $subnet2Name -AddressPrefix $subnet2Prefix
$subnet3Name="<Table S - Item 3 - Subnet name column>"
$subnet3Prefix="<Table S - Item 3 - Subnet address space column>"
$subnet3=New-AzVirtualNetworkSubnetConfig -Name $subnet3Name -AddressPrefix $subnet3Prefix
$gwSubnet4Prefix="<Table S - Item 4 - Subnet address space column>"
$gwSubnet=New-AzVirtualNetworkSubnetConfig -Name "GatewaySubnet" -AddressPrefix $gwSubnet4Prefix

# Create the virtual network
New-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName -Location $locName -AddressPrefix $vnetAddrPrefix -Subnet $gwSubnet,$subnet1,$subnet2,$subnet3 -DNSServer $dnsServers

```

<span data-ttu-id="b6110-266">다음으로, 가상 컴퓨터를 포함 하는 각 서브넷에 대해 네트워크 보안 그룹을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b6110-266">Next, you create network security groups for each subnet that has virtual machines.</span></span> <span data-ttu-id="b6110-267">서브넷 격리를 수행하려면 서브넷의 네트워크 보안 그룹에서 허용되거나 거부되는 특정 유형의 트래픽에 대한 규칙을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6110-267">To perform subnet isolation, you can add rules for the specific types of traffic allowed or denied to the network security group of a subnet.</span></span>
  
```powershell
# Create network security groups
$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name $vnetName

New-AzNetworkSecurityGroup -Name $subnet1Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzNetworkSecurityGroup -Name $subnet1Name -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet1Name -AddressPrefix $subnet1Prefix -NetworkSecurityGroup $nsg

New-AzNetworkSecurityGroup -Name $subnet2Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzNetworkSecurityGroup -Name $subnet2Name -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet2Name -AddressPrefix $subnet2Prefix -NetworkSecurityGroup $nsg

New-AzNetworkSecurityGroup -Name $subnet3Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzNetworkSecurityGroup -Name $subnet3Name -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet3Name -AddressPrefix $subnet3Prefix -NetworkSecurityGroup $nsg
$vnet | Set-AzVirtualNetwork
```

<span data-ttu-id="b6110-268">다음으로 이러한 명령을 사용하여 사이트 간 VPN 연결의 게이트웨이를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b6110-268">Next, use these commands to create the gateways for the site-to-site VPN connection.</span></span>
  
```powershell
$rgName="<Table R - Item 4 - Resource group name column>"
$locName="<Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name "GatewaySubnet"

# Attach a virtual network gateway to a public IP address and the gateway subnet
$publicGatewayVipName="PublicIPAddress"
$vnetGatewayIpConfigName="PublicIPConfig"
New-AzPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$publicGatewayVip=Get-AzPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName
$vnetGatewayIpConfig=New-AzVirtualNetworkGatewayIpConfig -Name $vnetGatewayIpConfigName -PublicIpAddressId $publicGatewayVip.Id -Subnet $subnet

# Create the Azure gateway
$vnetGatewayName="AzureGateway"
$vnetGateway=New-AzVirtualNetworkGateway -Name $vnetGatewayName -ResourceGroupName $rgName -Location $locName -GatewayType Vpn -VpnType RouteBased -IpConfigurations $vnetGatewayIpConfig

# Create the gateway for the local network
$localGatewayName="LocalNetGateway"
$localGatewayIP="<Table V - Item 3 - Value column>"
$localNetworkPrefix=@( <comma-separated, double-quote enclosed list of the local network address prefixes from Table L, example: "10.1.0.0/24", "10.2.0.0/24"> )
$localGateway=New-AzLocalNetworkGateway -Name $localGatewayName -ResourceGroupName $rgName -Location $locName -GatewayIpAddress $localGatewayIP -AddressPrefix $localNetworkPrefix

# Define the Azure virtual network VPN connection
$vnetConnectionName="S2SConnection"
$vnetConnectionKey="<Table V - Item 5 - Value column>"
$vnetConnection=New-AzVirtualNetworkGatewayConnection -Name $vnetConnectionName -ResourceGroupName $rgName -Location $locName -ConnectionType IPsec -SharedKey $vnetConnectionKey -VirtualNetworkGateway1 $vnetGateway -LocalNetworkGateway2 $localGateway

```

> [!NOTE]
> <span data-ttu-id="b6110-269">개별 사용자의 페더레이션 인증은 온-프레미스 리소스를 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b6110-269">Federated authentication of individual users does not rely on any on-premises resources.</span></span> <span data-ttu-id="b6110-270">그러나이 사이트 간 VPN 연결을 사용할 수 없는 경우 VNet의 도메인 컨트롤러는 온-프레미스 Active Directory 도메인 서비스에 있는 사용자 계정 및 그룹에 대 한 업데이트를 수신 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b6110-270">However, if this site-to-site VPN connection becomes unavailable, the domain controllers in the VNet will not receive updates to user accounts and groups made in the on-premises Active Directory Domain Services.</span></span> <span data-ttu-id="b6110-271">이 문제가 발생 하지 않도록 하려면 사이트 간 VPN 연결에 대 한 고가용성을 구성 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6110-271">To ensure this does not happen, you can configure high availability for your site-to-site VPN connection.</span></span> <span data-ttu-id="b6110-272">자세한 내용은 [항상 사용 가능한 프레미스 간 및 VNet 간 연결](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b6110-272">For more information, see [Highly Available Cross-Premises and VNet-to-VNet Connectivity](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)</span></span>
  
<span data-ttu-id="b6110-273">그런 다음 이 명령의 디스플레이에서 가상 네트워크용 Azure VPN 게이트웨이의 공용 IPv4 주소를 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="b6110-273">Next, record the public IPv4 address of the Azure VPN gateway for your virtual network from the display of this command:</span></span>
  
```powershell
Get-AzPublicIpAddress -Name $publicGatewayVipName -ResourceGroupName $rgName
```

<span data-ttu-id="b6110-p114">계속해서 Azure VPN 게이트웨이에 연결할 온-프레미스 VPN 장치를 구성합니다. 자세한 내용은 [VPN 장치 구성](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b6110-p114">Next, configure your on-premises VPN device to connect to the Azure VPN gateway. For more information, see [Configure your VPN device](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).</span></span>
  
<span data-ttu-id="b6110-276">온-프레미스 VPN 장치를 구성하려면 다음 항목이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="b6110-276">To configure your on-premises VPN device, you will need the following:</span></span>
  
- <span data-ttu-id="b6110-277">Azure VPN 게이트웨이의 공용 IPv4 주소.</span><span class="sxs-lookup"><span data-stu-id="b6110-277">The public IPv4 address of the Azure VPN gateway.</span></span>
    
- <span data-ttu-id="b6110-278">사이트 간 VPN 연결용 IPsec 미리 공유한 키(테이블 V - 항목 5 - 값 열).</span><span class="sxs-lookup"><span data-stu-id="b6110-278">The IPsec pre-shared key for the site-to-site VPN connection (Table V - Item 5 - Value column).</span></span>
    
<span data-ttu-id="b6110-p115">다음으로 가상 네트워크의 주소 공간이 온-프레미스 네트워크에서 연결 가능한지 확인합니다. 일반적으로 가상 네트워크 주소 공간에 해당하는 경로를 VPN 장치에 추가한 다음 이 경로를 조직 네트워크의 나머지 라우팅 인프라에 보급합니다. IT 부서에서 이 작업을 수행하는 방법을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b6110-p115">Next, ensure that the address space of the virtual network is reachable from your on-premises network. This is usually done by adding a route corresponding to the virtual network address space to your VPN device and then advertising that route to the rest of the routing infrastructure of your organization network. Work with your IT department to determine how to do this.</span></span>
  
<span data-ttu-id="b6110-282">다음으로, 세 가지 가용성 집합의 이름을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6110-282">Next, define the names of three availability sets.</span></span> <span data-ttu-id="b6110-283">테이블 A를 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="b6110-283">Fill out Table A.</span></span> 
  
|<span data-ttu-id="b6110-284">**항목**</span><span class="sxs-lookup"><span data-stu-id="b6110-284">**Item**</span></span>|<span data-ttu-id="b6110-285">**용도**</span><span class="sxs-lookup"><span data-stu-id="b6110-285">**Purpose**</span></span>|<span data-ttu-id="b6110-286">**가용성 집합 이름**</span><span class="sxs-lookup"><span data-stu-id="b6110-286">**Availability set name**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="b6110-287">1.</span><span class="sxs-lookup"><span data-stu-id="b6110-287">1.</span></span>  <br/> |<span data-ttu-id="b6110-288">도메인 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="b6110-288">Domain controllers</span></span>  <br/> |![라인](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="b6110-290">2.</span><span class="sxs-lookup"><span data-stu-id="b6110-290">2.</span></span>  <br/> |<span data-ttu-id="b6110-291">AD FS 서버</span><span class="sxs-lookup"><span data-stu-id="b6110-291">AD FS servers</span></span>  <br/> |![라인](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="b6110-293">3.</span><span class="sxs-lookup"><span data-stu-id="b6110-293">3.</span></span>  <br/> |<span data-ttu-id="b6110-294">웹 응용 프로그램 프록시 서버</span><span class="sxs-lookup"><span data-stu-id="b6110-294">Web application proxy servers</span></span>  <br/> |![라인](./media/Common-Images/TableLine.png)  <br/> |
   
 <span data-ttu-id="b6110-296">**테이블 A: 가용성 집합**</span><span class="sxs-lookup"><span data-stu-id="b6110-296">**Table A: Availability sets**</span></span>
  
<span data-ttu-id="b6110-297">2, 3 및 4단계에서 가상 컴퓨터를 만들 때 이러한 이름이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="b6110-297">You will need these names when you create the virtual machines in phases 2, 3, and 4.</span></span>
  
<span data-ttu-id="b6110-298">다음 Azure PowerShell 명령을 사용 하 여 새 가용성 집합을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b6110-298">Create the new availability sets with these Azure PowerShell commands.</span></span>
  
```powershell
$locName="<the Azure location for your new resource group>"
$rgName="<Table R - Item 1 - Resource group name column>"
$avName="<Table A - Item 1 - Availability set name column>"
New-AzAvailabilitySet -ResourceGroupName $rgName -Name $avName -Location $locName -Sku Aligned  -PlatformUpdateDomainCount 5 -PlatformFaultDomainCount 2
$rgName="<Table R - Item 2 - Resource group name column>"
$avName="<Table A - Item 2 - Availability set name column>"
New-AzAvailabilitySet -ResourceGroupName $rgName -Name $avName -Location $locName -Sku Aligned  -PlatformUpdateDomainCount 5 -PlatformFaultDomainCount 2
$rgName="<Table R - Item 3 - Resource group name column>"
$avName="<Table A - Item 3 - Availability set name column>"
New-AzAvailabilitySet -ResourceGroupName $rgName -Name $avName -Location $locName -Sku Aligned  -PlatformUpdateDomainCount 5 -PlatformFaultDomainCount 2
```

<span data-ttu-id="b6110-299">이 단계를 성공적으로 완료하면 다음 구성을 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6110-299">This is the configuration resulting from the successful completion of this phase.</span></span>
  
<span data-ttu-id="b6110-300">**1 단계: Office 365에 대 한 고가용성 페더레이션 인증용 Azure 인프라**</span><span class="sxs-lookup"><span data-stu-id="b6110-300">**Phase 1: The Azure infrastructure for high availability federated authentication for Office 365**</span></span>

![Azure 인프라를 사용 하 여 Azure의 고가용성 Office 365 페더레이션 인증 1 단계](media/4e7ba678-07df-40ce-b372-021bf7fc91fa.png)
  
## <a name="next-step"></a><span data-ttu-id="b6110-302">다음 단계</span><span class="sxs-lookup"><span data-stu-id="b6110-302">Next step</span></span>

<span data-ttu-id="b6110-303">[2 단계: 도메인 컨트롤러 구성](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) 을 사용 하 여이 작업의 구성을 계속 진행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6110-303">Use [Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) to continue with the configuration of this workload.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="b6110-304">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b6110-304">See Also</span></span>

[<span data-ttu-id="b6110-305">Azure에서 Office 365용 고가용성 페더레이션 인증 배포</span><span class="sxs-lookup"><span data-stu-id="b6110-305">Deploy high availability federated authentication for Office 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="b6110-306">Office 365 개발/테스트 환경에 대 한 페더레이션된 id</span><span class="sxs-lookup"><span data-stu-id="b6110-306">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="b6110-307">클라우드 채택 및 하이브리드 솔루션</span><span class="sxs-lookup"><span data-stu-id="b6110-307">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.yml)

[<span data-ttu-id="b6110-308">Office 365 ID 및 Azure Active Directory 이해</span><span class="sxs-lookup"><span data-stu-id="b6110-308">Understanding Office 365 identity and Azure Active Directory</span></span>](about-office-365-identity.md)


