---
title: "Azure IaaS에 대 한 하이브리드 클라우드 시나리오"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 978f2b76-5aba-4e11-9434-f0efda987be1
description: "요약: 경우 서비스로 (IaaS) Microsoft의 인프라에 대 한 하이브리드 아키텍처 및 시나리오 이해-Azure의 클라우드 서비스를 기반으로 합니다."
ms.openlocfilehash: 66024c708cb4fbc904de18f27077871d52f0e70c
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/09/2018
---
# <a name="hybrid-cloud-scenarios-for-azure-iaas"></a><span data-ttu-id="69f75-103">Azure IaaS에 대 한 하이브리드 클라우드 시나리오</span><span class="sxs-lookup"><span data-stu-id="69f75-103">Hybrid cloud scenarios for Azure IaaS</span></span>

 <span data-ttu-id="69f75-104">**요약:** 서비스로 (IaaS) Microsoft의 인프라에 대 한 하이브리드 아키텍처 및 시나리오 이해-Azure의 클라우드 서비스를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="69f75-104">**Summary:** Understand the hybrid architecture and scenarios for Microsoft's Infrastructure as a Service (IaaS)-based cloud offerings in Azure.</span></span>
  
<span data-ttu-id="69f75-105">온-프레미스 컴퓨팅을 확장 하 고 id 인프라에서 실행 되는 IT 작업 부하를 호스트 하 여 클라우드로 크로스-프레미스 Azure 가상 네트워크 (VNets).</span><span class="sxs-lookup"><span data-stu-id="69f75-105">Extend your on-premises computing and identity infrastructure into the cloud by hosting IT workloads running in cross-premises Azure virtual networks (VNets).</span></span> 
  
## <a name="azure-iaas-hybrid-scenario-architecture"></a><span data-ttu-id="69f75-106">Azure IaaS 하이브리드 시나리오 아키텍처</span><span class="sxs-lookup"><span data-stu-id="69f75-106">Azure IaaS hybrid scenario architecture</span></span>

<span data-ttu-id="69f75-107">그림 1 Azure의 Microsoft IaaS 기반 하이브리드 시나리오의 아키텍처를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="69f75-107">Figure 1 shows the architecture of Microsoft IaaS-based hybrid scenarios in Azure.</span></span>
  
<span data-ttu-id="69f75-108">**Azure의 그림 1: Microsoft IaaS 기반 하이브리드 시나리오**</span><span class="sxs-lookup"><span data-stu-id="69f75-108">**Figure 1: Microsoft IaaS-based hybrid scenarios in Azure**</span></span>

![Azure의 Microsoft IaaS 기반 하이브리드 시나리오](images/Hybrid_Poster/Hybrid_Cloud_Stack_IaaS.png)
  
<span data-ttu-id="69f75-110">아키텍처의 각 레이어에:</span><span class="sxs-lookup"><span data-stu-id="69f75-110">For each layer of the architecture:</span></span>
  
- <span data-ttu-id="69f75-111">앱 및 시나리오</span><span class="sxs-lookup"><span data-stu-id="69f75-111">Apps and scenarios</span></span>
    
    <span data-ttu-id="69f75-112">IT 작업은 일반적으로 다중 계층, 항상 사용 가능한 응용 프로그램은 Azure 가상 컴퓨터 (Vm)의 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="69f75-112">An IT workload is typically a multi-tier, highly-available application composed of Azure virtual machines (VMs).</span></span>
    
- <span data-ttu-id="69f75-113">Identity</span><span class="sxs-lookup"><span data-stu-id="69f75-113">Identity</span></span>
    
    <span data-ttu-id="69f75-114">로컬 인증에 대 한 Azure VNets에서 실행 하는 서버 집합에 Windows Server AD 도메인 컨트롤러와 같은 identity 서버를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="69f75-114">Add identity servers, such as Windows Server AD domain controllers, to the set of servers running in Azure VNets for local authentication.</span></span>
    
- <span data-ttu-id="69f75-115">네트워크</span><span class="sxs-lookup"><span data-stu-id="69f75-115">Network</span></span>
    
    <span data-ttu-id="69f75-116">Azure IaaS에 개인 피어 링으로 인터넷을 통해 사이트 간 VPN 연결 또는 ExpressRoute 연결 중 하나를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="69f75-116">Use either a site-to-site VPN connection over the Internet or an ExpressRoute connection with private peering to Azure IaaS.</span></span>
    
- <span data-ttu-id="69f75-117">온-프레미스</span><span class="sxs-lookup"><span data-stu-id="69f75-117">On-premises</span></span>
    
    <span data-ttu-id="69f75-p101">Azure에서 실행 하는 identity 서버와 동기화 되는 identity 서버가 포함 됩니다. Azure에서 실행 중인 Vm에 액세스할 수 있는, 저장소 및 시스템 관리 인프라와 같은 리소스를 포함할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69f75-p101">Contains identity servers that are synchronized with the identity servers running in Azure. Can also contain resources that VMs running in Azure can access, such as storage and systems management infrastructure.</span></span>
    
## <a name="dirsync-server-for-office-365"></a><span data-ttu-id="69f75-120">Office 365에 대 한 디렉터리 동기화 서버</span><span class="sxs-lookup"><span data-stu-id="69f75-120">DirSync server for Office 365</span></span>

<span data-ttu-id="69f75-121">그림 2와 같이 Azure VNet에서 디렉터리 동기화 (DirSync) 서버를 실행 하는 것은 컴퓨팅 및 id 인프라가 클라우드로 확장 (영문)의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="69f75-121">Running your directory synchronization (DirSync) server from an Azure VNet, as shown in Figure 2, is an example of extending your computing and identity infrastructure to the cloud.</span></span>
  
<span data-ttu-id="69f75-122">**Azure IaaS에서 Office 365에 대 한 그림 2: 디렉터리 동기화 서버**</span><span class="sxs-lookup"><span data-stu-id="69f75-122">**Figure 2: DirSync server for Office 365 in Azure IaaS**</span></span>

![Azure IaaS의 Office 365 디렉터리 동기화 서버](images/Hybrid_Poster/Hybrid_Cloud_Stack_IaaS_DirSync.png)
  
<span data-ttu-id="69f75-p102">그림 2의 온-프레미스 네트워크 프록시 서버 및 해당에 지에서 라우터를 사용 하 여 Windows Server AD 인프라를 호스팅합니다. 라우터는 Azure 게이트웨이 사이트 마다 VPN 또는 ExpressRoute 연결에는 Azure VNet의 가장자리에 연결합니다. 디렉터리 동기화 서버는 VNet 내부 Azure AD 연결을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="69f75-p102">In Figure 2, an on-premises network hosts a Windows Server AD infrastructure, with a proxy server and a router at its edge. The router connects to an Azure gateway at the edge of an Azure VNet with a site-to-site VPN or ExpressRoute connection. Inside the VNet, a DirSync server runs Azure AD Connect.</span></span>
  
<span data-ttu-id="69f75-127">Office 365에 대 한 디렉터리 동기화 서버는 Office 365 구독의 Azure AD 테 넌 트의 Windows Server AD 계정 목록을 동기화합니다.</span><span class="sxs-lookup"><span data-stu-id="69f75-127">A DirSync server for Office 365 synchronizes the list of accounts in Windows Server AD with the Azure AD tenant of an Office 365 subscription.</span></span>
  
<span data-ttu-id="69f75-p103">디렉터리 동기화 서버에는 Azure AD 연결을 실행 하는 Windows 기반 서버가입니다. 더 빠른 프로 비전을 위한 또는 조직에서 온-프레미스 서버 수를 줄이는 Azure IaaS에서 가상 네트워크 (VNet)에서 디렉터리 동기화 서버를 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="69f75-p103">A DirSync server is a Windows-based server that runs Azure AD Connect. For faster provisioning or to reduce the number of on-premises servers in your organization, deploy your DirSync server in a virtual network (VNet) in Azure IaaS.</span></span>
  
<span data-ttu-id="69f75-130">디렉터리 동기화 서버는 Windows Server AD 변경 내용에 대 한 폴링 하 고 Office 365 구독을 동기화 합니다.</span><span class="sxs-lookup"><span data-stu-id="69f75-130">The DirSync server polls Windows Server AD for changes and then synchronizes them with the Office 365 subscription.</span></span>
  
<span data-ttu-id="69f75-131">자세한 내용은 [Office 365 DirSync Azure에서 배포](https://technet.microsoft.com/library/dn635310.aspx)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="69f75-131">For more information, see [Deploy Office 365 DirSync in Azure](https://technet.microsoft.com/library/dn635310.aspx).</span></span>
  
## <a name="line-of-business-lob-application"></a><span data-ttu-id="69f75-132">기간 업무 (LOB) 응용 프로그램의 줄</span><span class="sxs-lookup"><span data-stu-id="69f75-132">Line of business (LOB) application</span></span>

<span data-ttu-id="69f75-133">그림 3 Azure IaaS에서 실행 중인 응용 프로그램 서버 기반 LOB 구성을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="69f75-133">Figure 3 shows the configuration of a server-based LOB application running in Azure IaaS.</span></span>
  
<span data-ttu-id="69f75-134">**Azure IaaS에서 그림 3: LOB 응용 프로그램**</span><span class="sxs-lookup"><span data-stu-id="69f75-134">**Figure 3: LOB application in Azure IaaS**</span></span>

![Azure IaaS의 서버 기반 LOB 응용 프로그램](images/Hybrid_Poster/Hybrid_Cloud_Stack_IaaS_Ex.png)
  
<span data-ttu-id="69f75-p104">그림 3에서는 온-프레미스 네트워크 id 인프라 및 사용자를 호스트합니다. 사이트 마다 VPN 또는 ExpressRoute 연결에는 Azure IaaS 게이트웨이에 연결 됩니다. Azure IaaS LOB 응용 프로그램의 서버를 포함 하는 가상 네트워크를 호스팅합니다.</span><span class="sxs-lookup"><span data-stu-id="69f75-p104">In Figure 3, an on-premises network hosts an identity infrastructure and users. It is connected to an Azure IaaS gateway with a site-to-site VPN or ExpressRoute connection. Azure IaaS hosts a virtual network containing the servers of the LOB application.</span></span>
  
<span data-ttu-id="69f75-139">Azure 데이터 센터 (위치)의 Azure VNet의 서브넷에 상주 하는 Azure Vm에서 실행 되는 LOB 응용 프로그램을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69f75-139">You can create LOB applications running on Azure VMs, which reside on subnets of an Azure VNet in an Azure datacenter (also known as a location).</span></span>
  
<span data-ttu-id="69f75-140">사용자 VNets에 고유한 개인 주소 공간을 할당 하 고 온-프레미스를 업데이트 해야 기본적으로 Azure를 사용 하도록 온-프레미스 인프라를 확장 하는, 때문에 라우팅 테이블에 각 VNet에 연결 가능성을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="69f75-140">Because you are essentially extending your on-premises infrastructure to Azure, you must assign unique private address space to your VNets and update your on-premises routing tables to ensure reachability to each VNet.</span></span>
  
<span data-ttu-id="69f75-141">연결 된 후에 온-프레미스 서버와 마찬가지로 시스템 관리 소프트웨어를 사용 하거나 원격 데스크톱 연결 이러한 Vm 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69f75-141">Once connected, these VMs can be managed with remote desktop connections or with your systems management software, just like your on-premises servers.</span></span>
  
<span data-ttu-id="69f75-142">공개적으로 노출 포트를 구성 하 여 이러한 Vm 액세스할 수도 있습니다 인터넷에서 모바일 또는 원격 사용자가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69f75-142">By configuring publically-exposed ports, these VMs can also be accessed from the Internet by mobile or remote users.</span></span>
  
<span data-ttu-id="69f75-143">개념 증명 구성을 [Simulated 크로스-프레미스 Azure에 가상 네트워크를](simulated-cross-premises-virtual-network-in-azure.md)참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="69f75-143">For a proof-of-concept configuration, see [Simulated cross-premises virtual network in Azure](simulated-cross-premises-virtual-network-in-azure.md).</span></span>
  
<span data-ttu-id="69f75-144">Azure Vm에서 호스팅되는 LOB 응용 프로그램의 특성은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="69f75-144">Attributes of LOB applications hosted on Azure VMs are the following:</span></span>
  
- <span data-ttu-id="69f75-145">여러 계층</span><span class="sxs-lookup"><span data-stu-id="69f75-145">Multiple tiers</span></span>
    
    <span data-ttu-id="69f75-p105">계층화 된 방식을 사용 하는 일반적인 LOB 응용 프로그램입니다. 두 서버 집합이 직원 또는 고객에 대 한 액세스에 대 한 id, 데이터베이스 처리, 응용 프로그램 및 논리 처리 및 프런트엔드 웹 서버를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="69f75-p105">Typical LOB applications use a tiered approach. Sets of servers provide identity, database processing, application and logic processing, and front-end web servers for employee or customer access.</span></span> 
    
- <span data-ttu-id="69f75-148">고가용성</span><span class="sxs-lookup"><span data-stu-id="69f75-148">High availability</span></span>
    
    <span data-ttu-id="69f75-p106">각 계층에서 여러 서버를 사용 하 여 고가용성을 제공 하는 일반적인 LOB 응용 프로그램입니다. Azure IaaS Azure 가용성 집합에는 서버에 대 한 99.9% 가동 시간 SLA를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="69f75-p106">Typical LOB applications provide high availability by using multiple servers in each tier. Azure IaaS provides a 99.9% uptime SLA for servers in Azure availability sets.</span></span> 
    
- <span data-ttu-id="69f75-151">부하 분산</span><span class="sxs-lookup"><span data-stu-id="69f75-151">Load distribution</span></span>
    
    <span data-ttu-id="69f75-p107">계층에서 여러 서버 간에 네트워크 트래픽 부하를 배포 하려면 인터넷 또는 내부 Azure 부하 분산 장치를 사용할 수 있습니다. 또는 Azure marketplace에서 제공 하는 전용된 부하 분산 장치 기기를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69f75-p107">To distribute the load of network traffic among multiple servers in a tier, you can use an Internet-facing or internal Azure load balancer. Or, you can use a dedicated load balancer appliance available from the Azure marketplace.</span></span>
    
- <span data-ttu-id="69f75-154">보안</span><span class="sxs-lookup"><span data-stu-id="69f75-154">Security</span></span>
    
    <span data-ttu-id="69f75-p108">인터넷에서 들어오는 원치 않는 트래픽을에서 서버를 보호 하려면 Azure 네트워크 보안 그룹을 사용할 수 있습니다. 허용 하거나 서브넷 또는 개별 가상 컴퓨터의 네트워크 인터페이스에 대 한 트래픽을 거부를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69f75-p108">To protect servers from unsolicited incoming traffic from the Internet, you can use Azure network security groups. You can define allowed or denied traffic for a subnet or the network interface of an individual virtual machine.</span></span>
    
## <a name="sharepoint-server-2016-farm-in-azure"></a><span data-ttu-id="69f75-157">Azure의 SharePoint Server 2016 팜</span><span class="sxs-lookup"><span data-stu-id="69f75-157">SharePoint Server 2016 farm in Azure</span></span>

<span data-ttu-id="69f75-158">다중 계층의 예로, Azure의 가용성이 LOB 응용 프로그램 그림 4와 같이 SharePoint Server 2016 팜은 합니다.</span><span class="sxs-lookup"><span data-stu-id="69f75-158">An example of a multi-tier, highly-available LOB application in Azure is a SharePoint Server 2016 farm, as shown in Figure 4.</span></span>
  
<span data-ttu-id="69f75-159">**그림 4: 고가용성 SharePoint Server 2016의에서 팜 Azure IaaS**</span><span class="sxs-lookup"><span data-stu-id="69f75-159">**Figure 4: A high-availability SharePoint Server 2016 farm in Azure IaaS**</span></span>

![Azure IaaS에 팜 된 고가용성 SharePoint Server 2016 ](images/Hybrid_Poster/Hybrid_Cloud_Stack_IaaS_SP2016.png)
  
<span data-ttu-id="69f75-p109">그림 4는 온-프레미스 네트워크 id 인프라 및 사용자를 호스트합니다. 사이트 마다 VPN 또는 ExpressRoute 연결에는 Azure IaaS 게이트웨이에 연결 됩니다. Azure VNet 프런트엔드 서버, 응용 프로그램 서버, SQL Server 클러스터 및 도메인 컨트롤러에 대 한 별도 계층을 포함 하는 SharePoint Server 2016 팜의 서버를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="69f75-p109">In Figure 4, an on-premises network hosts an identity infrastructure and users. It is connected to an Azure IaaS gateway with a site-to-site VPN or ExpressRoute connection. The Azure VNet contains the servers of the SharePoint Server 2016 farm, which includes separate tiers for the front-end servers, the application servers, the SQL Server cluster, and the domain controllers.</span></span>
  
<span data-ttu-id="69f75-164">이 구성은 다음과 같은 특성이 LOB 응용 프로그램의 Azure에서:</span><span class="sxs-lookup"><span data-stu-id="69f75-164">This configuration has the following attributes of LOB applications in Azure:</span></span> 
  
- <span data-ttu-id="69f75-165">계층</span><span class="sxs-lookup"><span data-stu-id="69f75-165">Tiers</span></span>
    
    <span data-ttu-id="69f75-166">팜 내에서 다양 한 역할을 실행 하는 서버는 계층 만들고 각 계층에는 자체 서브넷입니다.</span><span class="sxs-lookup"><span data-stu-id="69f75-166">Servers running different roles within the farm create the tiers and each tier has its own subnet.</span></span>
    
- <span data-ttu-id="69f75-167">고가용성</span><span class="sxs-lookup"><span data-stu-id="69f75-167">High-availability</span></span>
    
    <span data-ttu-id="69f75-168">동일한 가용성 집합에 있는 계층의 모든 서버를 배치 하 고 각 계층에 둘 이상의 서버를 사용 하 여 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="69f75-168">Achieved by using more than one server in each tier and placing all the servers of a tier in the same availability set.</span></span>
    
- <span data-ttu-id="69f75-169">부하 분산</span><span class="sxs-lookup"><span data-stu-id="69f75-169">Load distribution</span></span>
    
    <span data-ttu-id="69f75-170">내부 Azure 부하 분산 장치에는 들어오는 클라이언트 웹 트래픽을 (s q l 1, SQL2 및 MN1) SQL Server 클러스터의 수신기 IP 주소와 프런트엔드 서버 (WEB1 및 w e b 2)에 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="69f75-170">Internal Azure load balancers distribute the incoming client web traffic to the front-end servers (WEB1 and WEB2) and to the listener IP address of the SQL Server cluster (SQL1, SQL2, and MN1).</span></span>
    
- <span data-ttu-id="69f75-171">보안</span><span class="sxs-lookup"><span data-stu-id="69f75-171">Security</span></span>
    
    <span data-ttu-id="69f75-172">각 서브넷에 대 한 네트워크 보안 그룹을 통해 허용 된 인바운드 및 아웃 바운드 트래픽을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69f75-172">Network security groups for each subnet let you to configure allowed inbound and outbound traffic.</span></span>
    
<span data-ttu-id="69f75-173">성공적인 채택에 대 한이 경로 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="69f75-173">Follow this path for successful adoption:</span></span>
  
1. <span data-ttu-id="69f75-174">평가 및 테스트</span><span class="sxs-lookup"><span data-stu-id="69f75-174">Evaluate and experiment</span></span>
    
    <span data-ttu-id="69f75-175">[Microsoft Azure의 SharePoint Server 2016](https://technet.microsoft.com/library/mt779107%28v=office.16%29.aspx) Azure의 SharePoint Server 2016 실행의 장점을 이해를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="69f75-175">See [SharePoint Server 2016 in Microsoft Azure](https://technet.microsoft.com/library/mt779107%28v=office.16%29.aspx) to understand the benefits of running SharePoint Server 2016 in Azure.</span></span>
    
    <span data-ttu-id="69f75-176">[Azure 개발/테스트 환경에서 인트라넷 SharePoint Server 2016](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx) 시뮬레이션 된 개발/테스트 환경을 구축 하기를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="69f75-176">See [Intranet SharePoint Server 2016 in Azure dev/test environment](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx) to build a simulated dev/test environment</span></span>
    
2. <span data-ttu-id="69f75-177">디자인</span><span class="sxs-lookup"><span data-stu-id="69f75-177">Design</span></span>
    
    <span data-ttu-id="69f75-178">Azure IaaS 네트워킹, 계산, 및 저장소 요소를 호스팅할 팜 및 설정의 집합을 결정 하는 프로세스를 통해의 8 단계 [Azure의 SharePoint Server 2016 팜 디자인 (영문)을](https://technet.microsoft.com/library/mt779108%28v=office.16%29.aspx) 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="69f75-178">See [Designing a SharePoint Server 2016 farm in Azure](https://technet.microsoft.com/library/mt779108%28v=office.16%29.aspx) to step through a process to determine the set of Azure IaaS networking, compute, and storage elements to host your farm and their settings.</span></span>
    
3. <span data-ttu-id="69f75-179">배포</span><span class="sxs-lookup"><span data-stu-id="69f75-179">Deploy</span></span>
    
    <span data-ttu-id="69f75-180">5 단계에서 끝-구성 고가용성 팜의 각 단계를 수행 하려면 [SharePoint Server 2016 Azure에서 SQL Server AlwaysOn 가용성 그룹으로 배포](https://technet.microsoft.com/library/mt793552%28v=office.16%29.aspx) 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="69f75-180">See [Deploying SharePoint Server 2016 with SQL Server AlwaysOn Availability Groups in Azure](https://technet.microsoft.com/library/mt793552%28v=office.16%29.aspx) to step through the end-to-end configuration of the high-availability farm in five phases.</span></span>
    
## <a name="federated-identity-for-office-365-in-azure"></a><span data-ttu-id="69f75-181">Azure의 Office 365에 대 한 페더레이션된 id</span><span class="sxs-lookup"><span data-stu-id="69f75-181">Federated identity for Office 365 in Azure</span></span>

<span data-ttu-id="69f75-182">Azure의 다중 계층, 항상 사용 가능한 LOB 응용 프로그램의 다른 예에는 Office 365에 대 한 페더레이션된 id입니다.</span><span class="sxs-lookup"><span data-stu-id="69f75-182">Another example of a multi-tier, highly-available LOB application in Azure is federated identity for Office 365.</span></span>
  
<span data-ttu-id="69f75-183">**그림 5: Azure IaaS에서 Office 365에 대 한 고가용성 페더레이션된 id 인프라를**</span><span class="sxs-lookup"><span data-stu-id="69f75-183">**Figure 5: A high-availability federated identity infrastructure for Office 365 in Azure IaaS**</span></span>

![Azure에서 고가용성 Office 365 페더레이션 인증 인프라의 최종 구성.](images/Hybrid_Poster/Hybrid_Cloud_Stack_IaaS_ADFS.png)
  
<span data-ttu-id="69f75-p110">그림 5는 온-프레미스 네트워크 id 인프라 및 사용자를 호스트합니다. 사이트 마다 VPN 또는 ExpressRoute 연결에는 Azure IaaS 게이트웨이에 연결 됩니다. Azure VNet 웹 프록시 서버, Active Directory Federation Services (AD FS) 서버 및 Windows Server Active Directory (AD) 도메인 컨트롤러를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="69f75-p110">In Figure 5, an on-premises network hosts an identity infrastructure and users. It is connected to an Azure IaaS gateway with a site-to-site VPN or ExpressRoute connection. The Azure VNet contains web proxy servers, Active Directory Federation Services (AD FS) servers, and Windows Server Active Directory (AD) domain controllers.</span></span>
  
<span data-ttu-id="69f75-188">이 구성은 다음과 같은 특성이 LOB 응용 프로그램의 Azure에서:</span><span class="sxs-lookup"><span data-stu-id="69f75-188">This configuration has the following attributes of LOB applications in Azure:</span></span>
  
- <span data-ttu-id="69f75-189">**계층:** 웹 프록시 서버, AD FS 서버 및 Windows Server AD 도메인 컨트롤러에 대 한 계층 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69f75-189">**Tiers:** There are tiers for web proxy servers, AD FS servers, and Windows Server AD domain controllers.</span></span>
    
- <span data-ttu-id="69f75-190">**메일 로드:** 웹 프록시를 받는 클라이언트 인증 요청을 분산 하는 외부 Azure 부하 분산 및 내부 Azure 부하 분산 장치를 AD FS 서버에 인증 요청을 분산 합니다.</span><span class="sxs-lookup"><span data-stu-id="69f75-190">**Load distribution:** An external Azure load balancer distributes the incoming client authentication requests to the web proxies and an internal Azure load balancer distributes authentication requests to the AD FS servers.</span></span>
    
<span data-ttu-id="69f75-191">성공적인 채택에 대 한이 경로 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="69f75-191">Follow this path for successful adoption:</span></span>
  
1. <span data-ttu-id="69f75-192">평가 및 테스트</span><span class="sxs-lookup"><span data-stu-id="69f75-192">Evaluate and experiment</span></span>
    
    <span data-ttu-id="69f75-193">Office 365와 연결 된 인증에 대 한 시뮬레이션 된 개발/테스트 환경을 구축 하 [여 Office 365 개발/테스트 환경에 대 한 페더레이션 id](federated-identity-for-your-office-365-dev-test-environment.md) 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="69f75-193">See [Federated identity for your Office 365 dev/test environment](federated-identity-for-your-office-365-dev-test-environment.md) to build a simulated dev/test environment for federated authentication with Office 365.</span></span>
    
2. <span data-ttu-id="69f75-194">배포</span><span class="sxs-lookup"><span data-stu-id="69f75-194">Deploy</span></span>
    
    <span data-ttu-id="69f75-195">5 단계에서 끝-구성 고가용성 AD FS 인프라의 각 단계를 수행 하 [Azure의 Office 365에 대 한 고가용성 연결 된 인증 배포를](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="69f75-195">See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) to step through the end-to-end configuration of the high availability AD FS infrastructure in five phases.</span></span>
    
<span data-ttu-id="69f75-196">다음의 추가 리소스를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="69f75-196">See these additional resources:</span></span>
  
- [<span data-ttu-id="69f75-197">하이브리드 클라우드 환경 설계</span><span class="sxs-lookup"><span data-stu-id="69f75-197">Architecting Hybrid Cloud Environments</span></span>](https://gallery.technet.microsoft.com/Architecting-Hybrid-Cloud-a7dc9f24/file/147475/1/Architecting%20Hybrid%20Cloud%20Environments%20V1.docx)
    
- [<span data-ttu-id="69f75-198">클라우드 Microsoft 가상 Academy 코스를 Your 데이터 센터를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="69f75-198">Extend Your Datacenter to the Cloud Microsoft Virtual Academy course</span></span>](https://mva.microsoft.com/en-US/training-courses/extend-your-datacenter-to-the-cloud-13908?l=7fG3tAouB_7100115881)
    
- [<span data-ttu-id="69f75-199">디자인 및 Azure의 LOB 응용 프로그램 구축</span><span class="sxs-lookup"><span data-stu-id="69f75-199">Design and Build an LOB application in Azure </span></span>](https://techcommunity.microsoft.com/t5/CAAB-Cloud-Adoption-Advisory/EXTRA-November-2016-Webinar/m-p/30058#M41)
    
## <a name="see-also"></a><span data-ttu-id="69f75-200">참고 항목</span><span class="sxs-lookup"><span data-stu-id="69f75-200">See Also</span></span>

[<span data-ttu-id="69f75-201">Microsoft Hybrid Cloud for Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="69f75-201">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="69f75-202">Microsoft 클라우드 IT 아키텍처 리소스</span><span class="sxs-lookup"><span data-stu-id="69f75-202">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="69f75-203">Microsoft의 엔터프라이즈 클라우드 로드맵: IT 의사 결정권자를 위한 리소스</span><span class="sxs-lookup"><span data-stu-id="69f75-203">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



