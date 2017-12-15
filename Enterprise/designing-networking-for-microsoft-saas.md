---
title: "Microsoft SaaS에 대 한 네트워킹 디자인 (영문)"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Hybrid
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 4194020a-3847-4259-9f2d-5c556a4510f9
description: "요약: Office 365, Microsoft Intune 및 Dynamics 365 포함 한 Microsoft의 SaaS 서비스에 대 한 액세스에 대 한 네트워크를 최적화 하는 방법을 이해 합니다."
ms.openlocfilehash: 432789d03f5208a379dc2ab4f17f38f95223e10d
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2017
---
# <a name="designing-networking-for-microsoft-saas"></a><span data-ttu-id="a84f5-103">Microsoft SaaS에 대 한 네트워킹 디자인 (영문)</span><span class="sxs-lookup"><span data-stu-id="a84f5-103">Designing networking for Microsoft SaaS</span></span>

 <span data-ttu-id="a84f5-104">**요약:** Office 365, Microsoft Intune 및 Dynamics 365 포함 한 Microsoft의 SaaS 서비스에 대 한 액세스에 대 한 네트워크를 최적화 하는 방법을 이해 합니다.</span><span class="sxs-lookup"><span data-stu-id="a84f5-104">**Summary:** Understand how to optimize your network for access to Microsoft's SaaS services, including Office 365, Microsoft Intune, and Dynamics 365.</span></span>
  
<span data-ttu-id="a84f5-105">Microsoft SaaS 서비스에 대한 네트워크를 최적화하려면 인터넷 에지, 클라이언트 장치 및 일반적인 IT 운영을 신중하게 분석해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a84f5-105">Optimizing your network for Microsoft SaaS services requires careful analysis of your Internet edge, your client devices, and typical IT operations.</span></span>
  
## <a name="steps-to-prepare-your-network-for-microsoft-saas-services"></a><span data-ttu-id="a84f5-106">Microsoft SaaS 서비스에 대 한 네트워크를 준비 하는 단계</span><span class="sxs-lookup"><span data-stu-id="a84f5-106">Steps to prepare your network for Microsoft SaaS services</span></span>

<span data-ttu-id="a84f5-107">Microsoft SaaS 서비스에 대 한 네트워크를 최적화 하기 위해 다음이 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="a84f5-107">Follow these steps to optimize your network for Microsoft SaaS services:</span></span>
  
1. <span data-ttu-id="a84f5-108">[Microsoft 클라우드 연결의 공통 요소](common-elements-of-microsoft-cloud-connectivity.md)에 **Microsoft 클라우드 서비스에 대 한 네트워크를 준비 하는 단계** 섹션을 통해 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="a84f5-108">Go through the **Steps to prepare your network for Microsoft cloud services** section in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).</span></span>
    
2. <span data-ttu-id="a84f5-109">프록시 서버 권장 사항에 따라 Microsoft SaaS 서비스에 대 한 인터넷 탈출 대화를 최적화 합니다.</span><span class="sxs-lookup"><span data-stu-id="a84f5-109">Optimize your Internet egress for Microsoft SaaS services using the proxy server recommendations.</span></span>
    
3. <span data-ttu-id="a84f5-110">근접 및 위치 권장 사항을 사용 하 여 인터넷 처리량을 최적화 합니다.</span><span class="sxs-lookup"><span data-stu-id="a84f5-110">Optimize your Internet throughput using the proximity and location recommendations.</span></span>
    
4. <span data-ttu-id="a84f5-111">클라이언트 컴퓨터와 기반이 있든 클라이언트 사용 고려 사항을 사용 하 여 인트라넷의 성능을 최적화 합니다.</span><span class="sxs-lookup"><span data-stu-id="a84f5-111">Optimize the performance of your client computers and the intranet on which they are located using the client usage considerations.</span></span>
    
5. <span data-ttu-id="a84f5-112">필요에 따라 데이터 마이그레이션 및 IT 운영 고려 사항을 사용 하 여 동기화의 성능을 최적화 합니다.</span><span class="sxs-lookup"><span data-stu-id="a84f5-112">As needed, optimize the performance of data migrations and synchronization using the IT operations considerations.</span></span>
    
## <a name="internet-edge-considerations"></a><span data-ttu-id="a84f5-113">인터넷에 지 고려 사항</span><span class="sxs-lookup"><span data-stu-id="a84f5-113">Internet edge considerations</span></span>

<span data-ttu-id="a84f5-114">인터넷에 지 및 Microsoft SaaS 서비스에 대 한 처리량을 최적화 하는 몇가지 사항을 고려해 야 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a84f5-114">Here are some things to consider optimize your Internet edge and throughput to Microsoft SaaS services.</span></span>
  
<span data-ttu-id="a84f5-115">**Microsoft SaaS 서비스에 대 한 그림 1: 연결 옵션**</span><span class="sxs-lookup"><span data-stu-id="a84f5-115">**Figure 1: Connection options for Microsoft SaaS services**</span></span>

![그림 1: Microsoft SaaS 서비스를 위한 연결 옵션](images/Network_Poster/SaaS1.png)
  
<span data-ttu-id="a84f5-117">그림 1 인터넷 파이프 또는 ExpressRoute을 통해 Microsoft SaaS 서비스에 연결 하는 온-프레미스 네트워크를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="a84f5-117">Figure 1 shows an on-premises network connecting to Microsoft SaaS services over an Internet pipe or ExpressRoute.</span></span>
  
<span data-ttu-id="a84f5-118">프록시 서버를 최적화 하기 위해 일부 권장 사항은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a84f5-118">Here are some recommendations to optimize your proxy server:</span></span>
  
- <span data-ttu-id="a84f5-119">WPAD, PAC, 또는 GPO를 사용 하 여 웹 클라이언트를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="a84f5-119">Configure web clients using WPAD, PAC, or GPO</span></span>
    
- <span data-ttu-id="a84f5-120">SSL 가로채기를 사용 하지 않는</span><span class="sxs-lookup"><span data-stu-id="a84f5-120">Don't use SSL interception</span></span>
    
- <span data-ttu-id="a84f5-121">PAC 파일을 사용 하 여 Microsoft SaaS 서비스 DNS 이름에 대 한 프록시를 무시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a84f5-121">Use a PAC file to bypass the proxy for Microsoft SaaS service DNS names</span></span>
    
- <span data-ttu-id="a84f5-122">CRL/OCSP 확인에 대 한 트래픽을 허용합니다</span><span class="sxs-lookup"><span data-stu-id="a84f5-122">Allow traffic for CRL/OCSP verification</span></span>
    
<span data-ttu-id="a84f5-123">일부 프록시 서버 병목 현상을 확인 하는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a84f5-123">Here are some proxy server bottlenecks to check:</span></span>
  
- <span data-ttu-id="a84f5-124">부족 하 여 영구 연결 (Outlook)</span><span class="sxs-lookup"><span data-stu-id="a84f5-124">Insufficient persistent connections (Outlook)</span></span>
    
- <span data-ttu-id="a84f5-125">용량이 부족</span><span class="sxs-lookup"><span data-stu-id="a84f5-125">Insufficient capacity</span></span>
    
- <span data-ttu-id="a84f5-126">이렇게 하면 오프 네트워크 평가</span><span class="sxs-lookup"><span data-stu-id="a84f5-126">Doing off-network evaluation</span></span>
    
- <span data-ttu-id="a84f5-127">인증 필요</span><span class="sxs-lookup"><span data-stu-id="a84f5-127">Requiring authentication</span></span>
    
- <span data-ttu-id="a84f5-128">UDP 트래픽 (비즈니스용 Skype)에 대 한 지원 되지 않습니다</span><span class="sxs-lookup"><span data-stu-id="a84f5-128">No support for UDP traffic (Skype for Business)</span></span>
    
<span data-ttu-id="a84f5-129">일부 근접 및 위치 권장 사항은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a84f5-129">Here are some proximity and location recommendations:</span></span>
  
- <span data-ttu-id="a84f5-130">개인 WAN을 통해 인터넷 트래픽을 라우팅 하지 마십시오</span><span class="sxs-lookup"><span data-stu-id="a84f5-130">Don't route your Internet traffic over the private WAN</span></span>
    
- <span data-ttu-id="a84f5-131">Out (영문)-region의 사용자에 대 한 영역에서 DNS 및 인터넷 트래픽 흐름을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a84f5-131">Use in-region DNS and Internet traffic flow for out-of-region users</span></span>
    
- <span data-ttu-id="a84f5-132">Office 365와 Azure 서비스와의 연결을 동시에 대 한 높은 대역폭에 대 한 ExpressRoute를 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="a84f5-132">Use ExpressRoute for high bandwidth to Office 365 and concurrent connectivity with Azure services</span></span>
    
<span data-ttu-id="a84f5-133">Office 365 트래픽에 대 한 필요한 아웃 바운드 포트는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a84f5-133">Here are the outbound ports needed for Office 365 traffic:</span></span>
  
- <span data-ttu-id="a84f5-134">TCP 80 (검사를 위해 CRL/OCSP)</span><span class="sxs-lookup"><span data-stu-id="a84f5-134">TCP 80 (for CRL/OCSP checks)</span></span>
    
- <span data-ttu-id="a84f5-135">TCP 443</span><span class="sxs-lookup"><span data-stu-id="a84f5-135">TCP 443</span></span>
    
- <span data-ttu-id="a84f5-136">UDP 3478</span><span class="sxs-lookup"><span data-stu-id="a84f5-136">UDP 3478</span></span>
    
- <span data-ttu-id="a84f5-137">TCP 5223</span><span class="sxs-lookup"><span data-stu-id="a84f5-137">TCP 5223</span></span>
    
- <span data-ttu-id="a84f5-138">TCP 50000-59999</span><span class="sxs-lookup"><span data-stu-id="a84f5-138">TCP 50000-59999</span></span>
    
- <span data-ttu-id="a84f5-139">UDP 50000-59999</span><span class="sxs-lookup"><span data-stu-id="a84f5-139">UDP 50000-59999</span></span>
    
## <a name="client-usage-considerations"></a><span data-ttu-id="a84f5-140">클라이언트 사용 고려 사항</span><span class="sxs-lookup"><span data-stu-id="a84f5-140">Client usage considerations</span></span>

<span data-ttu-id="a84f5-141">먼저, 클라이언트를 사용과 같은 서비스 집합을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="a84f5-141">First, configure the set of services that your clients will be using, such as:</span></span>
  
- <span data-ttu-id="a84f5-142">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="a84f5-142">Azure Active Directory</span></span>
    
- <span data-ttu-id="a84f5-143">Office 365</span><span class="sxs-lookup"><span data-stu-id="a84f5-143">Office 365</span></span>
    
  - <span data-ttu-id="a84f5-144">Office 클라이언트 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="a84f5-144">Office client apps</span></span>
    
  - <span data-ttu-id="a84f5-145">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="a84f5-145">SharePoint Online</span></span>
    
  - <span data-ttu-id="a84f5-146">Exchange Online</span><span class="sxs-lookup"><span data-stu-id="a84f5-146">Exchange Online</span></span>
    
  - <span data-ttu-id="a84f5-147">비즈니스용 Skype</span><span class="sxs-lookup"><span data-stu-id="a84f5-147">Skype for Business</span></span>
    
- <span data-ttu-id="a84f5-148">Microsoft Intune</span><span class="sxs-lookup"><span data-stu-id="a84f5-148">Microsoft Intune</span></span>
    
- <span data-ttu-id="a84f5-149">Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="a84f5-149">Dynamics 365</span></span>
    
<span data-ttu-id="a84f5-150">클라이언트 컴퓨터에 대해 다음 사항을 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a84f5-150">For your client computers, determine the following:</span></span>
  
- <span data-ttu-id="a84f5-151">일별, 계절적, 최대 부하 및 사용 현황 캡처에서 표준시로 한번에 최대 수</span><span class="sxs-lookup"><span data-stu-id="a84f5-151">Maximum number at any one time (time of day, seasonal, peaks and troughs in usage)</span></span>
    
- <span data-ttu-id="a84f5-152">최대 부하에 필요한 총 대역폭</span><span class="sxs-lookup"><span data-stu-id="a84f5-152">Total bandwidth needed for peaks</span></span>
    
- <span data-ttu-id="a84f5-153">인터넷 송신 장치에 대 한 대기 시간</span><span class="sxs-lookup"><span data-stu-id="a84f5-153">Latency to the Internet egress device</span></span>
    
- <span data-ttu-id="a84f5-154">데이터 센터 배치의 국가 및 비교 원점의 국가</span><span class="sxs-lookup"><span data-stu-id="a84f5-154">Country of origin vs. country of datacenter co-location</span></span>
    
<span data-ttu-id="a84f5-155">각 유형의 클라이언트 (PC, smartphone, 태블릿)에 대 한 현재를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="a84f5-155">For each type of client (PC, smartphone, tablet), ensure the current:</span></span>
  
- <span data-ttu-id="a84f5-156">운영 체제</span><span class="sxs-lookup"><span data-stu-id="a84f5-156">Operating system</span></span>
    
- <span data-ttu-id="a84f5-157">인터넷 브라우저</span><span class="sxs-lookup"><span data-stu-id="a84f5-157">Internet browser</span></span>
    
- <span data-ttu-id="a84f5-158">TCP/IP 스택</span><span class="sxs-lookup"><span data-stu-id="a84f5-158">TCP/IP stack</span></span>
    
- <span data-ttu-id="a84f5-159">네트워크 하드웨어</span><span class="sxs-lookup"><span data-stu-id="a84f5-159">Network hardware</span></span>
    
- <span data-ttu-id="a84f5-160">네트워크 하드웨어에 대 한 운영 체제 드라이버</span><span class="sxs-lookup"><span data-stu-id="a84f5-160">OS drivers for network hardware</span></span>
    
- <span data-ttu-id="a84f5-161">업데이트 및 패치 설치</span><span class="sxs-lookup"><span data-stu-id="a84f5-161">Updates and patches are installed</span></span>
    
<span data-ttu-id="a84f5-162">또한 인트라넷 연결 처리량을 최적화 (유선, 무선 또는 VPN).</span><span class="sxs-lookup"><span data-stu-id="a84f5-162">Additionally, optimize intranet connection throughput (wired, wireless, or VPN).</span></span>
  
<span data-ttu-id="a84f5-163">자세한 내용은 [Office 365와의 NAT 지원](https://support.office.com/article/NAT-support-with-Office-365-170e96ea-d65d-4e51-acac-1de56abe39b9)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="a84f5-163">For more information, see [NAT support with Office 365](https://support.office.com/article/NAT-support-with-Office-365-170e96ea-d65d-4e51-acac-1de56abe39b9).</span></span>
  
<span data-ttu-id="a84f5-164">Office 365와 함께 ExpressRoute를 사용 하는 것에 대 한 최신 권장 사항에 대 한 [Office 365에 대 한 ExpressRoute](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd)를 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="a84f5-164">For the latest recommendations for using ExpressRoute with Office 365, see [ExpressRoute for Office 365](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd).</span></span>
  
<span data-ttu-id="a84f5-165">인트라넷 성능을 최적화 하기 위해 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="a84f5-165">To optimize your intranet performance, do the following:</span></span>
  
- <span data-ttu-id="a84f5-166">인터넷에 지 장치 (PsPing, Ping, Tracert, TraceTCP, 네트워크 모니터)에 (RTTs) 왕복 시간 측정 하는 도구 사용</span><span class="sxs-lookup"><span data-stu-id="a84f5-166">Use tools to gauge round trip times (RTTs) to your Internet edge devices (PsPing, Ping, Tracert, TraceTCP, Network Monitor)</span></span>
    
- <span data-ttu-id="a84f5-167">흐름 프로토콜을 사용 하 여 탈출 경로 분석을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="a84f5-167">Perform egress path analysis using flow protocols</span></span>
    
- <span data-ttu-id="a84f5-168">중간 장치 (예: 시간, 상태) 분석을 수행</span><span class="sxs-lookup"><span data-stu-id="a84f5-168">Perform analysis of intermediate devices (age, health, etc.)</span></span>
    
<span data-ttu-id="a84f5-169">자세한 내용은 [PsPing 도구](https://technet.microsoft.com/sysinternals/jj729731.aspx)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="a84f5-169">For more information, see the [PsPing tool](https://technet.microsoft.com/sysinternals/jj729731.aspx).</span></span>
  
## <a name="it-operations-considerations"></a><span data-ttu-id="a84f5-170">IT 운영 고려 사항</span><span class="sxs-lookup"><span data-stu-id="a84f5-170">IT operations considerations</span></span>

<span data-ttu-id="a84f5-171">다음은 Microsoft SaaS 서비스에는 IT 작업 부하를 운영 하는 경우 고려 해야할 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="a84f5-171">Here are some things to consider when operating an IT workload in a Microsoft SaaS service.</span></span>
  
### <a name="one-time-migrations"></a><span data-ttu-id="a84f5-172">1 회 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="a84f5-172">One-time migrations</span></span>

<span data-ttu-id="a84f5-173">1 회 마이그레이션 예는 클라우드 기반 응용 프로그램 또는 보관 저장소에 대 한 대량 데이터를 전송 합니다.</span><span class="sxs-lookup"><span data-stu-id="a84f5-173">Examples of one-time migrations are bulk data transfer for cloud-based applications or archival storage.</span></span>
  
<span data-ttu-id="a84f5-174">시간에 마이그레이션에 대 한 네트워크를 최적화 합니다.</span><span class="sxs-lookup"><span data-stu-id="a84f5-174">To optimize your network for on-time migrations:</span></span>
  
- <span data-ttu-id="a84f5-175">최대 네트워크 사용량 및 시간에 패치를 적용 하는 컴퓨터를 방지 합니다.</span><span class="sxs-lookup"><span data-stu-id="a84f5-175">Avoid peak network usage and computer patching times</span></span>
    
- <span data-ttu-id="a84f5-176">기준 지정 하 고 파일럿, 네트워크 상태를 평가 하 고 실제 마이그레이션 시도 하기 전에 문제를 해결 해야</span><span class="sxs-lookup"><span data-stu-id="a84f5-176">Should be baselined and piloted, assess network health and resolve issues before attempting actual migration</span></span>
    
- <span data-ttu-id="a84f5-177">향후 마이그레이션에 대 한 사후 평가 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="a84f5-177">Perform post-mortem for future migrations</span></span>
    
### <a name="ongoing-synchronizations"></a><span data-ttu-id="a84f5-178">진행 중인 동기화</span><span class="sxs-lookup"><span data-stu-id="a84f5-178">Ongoing synchronizations</span></span>

<span data-ttu-id="a84f5-179">진행 중인 동기화의 예는 디렉터리 정보, 설정, 또는 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="a84f5-179">Examples of ongoing synchronizations are directory information, settings, or files.</span></span>
  
<span data-ttu-id="a84f5-180">진행 중인 동기화에 대 한 네트워크를 최적화 합니다.</span><span class="sxs-lookup"><span data-stu-id="a84f5-180">To optimize your network for ongoing synchronizations:</span></span>
  
- <span data-ttu-id="a84f5-181">전체에서 시스템을 모니터링 하는 네트워크 대역폭 인지 확인, 해결 또는 수집 된 오류를 해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="a84f5-181">Ensure that a network bandwidth monitoring system is in place, resolve or dismiss collected errors</span></span>
    
- <span data-ttu-id="a84f5-182">결과 모니터링 하는 대역폭을 사용 하 여 네트워크 변경 (수직/수평, 새 회로 또는 추가 장치)에 대 한 요구를 확인 하려면</span><span class="sxs-lookup"><span data-stu-id="a84f5-182">Use bandwidth monitoring results to determine need for network changes (scale-up/out, new circuits, or adding devices)</span></span>
    
<span data-ttu-id="a84f5-183">자세한 내용은 다음을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="a84f5-183">For more information, see:</span></span>
  
- [<span data-ttu-id="a84f5-184">네트워크 및 마이그레이션 Office 365에 대 한 계획</span><span class="sxs-lookup"><span data-stu-id="a84f5-184">Network and migration planning for Office 365</span></span>](https://aka.ms/tune)
    
- [<span data-ttu-id="a84f5-185">Office 365 성능 관리 Microsoft 가상 Academy 코스 (영문)</span><span class="sxs-lookup"><span data-stu-id="a84f5-185">Office 365 Performance Management Microsoft Virtual Academy course</span></span>](https://aka.ms/o365perf)
    
- [<span data-ttu-id="a84f5-186">Office 365에 대 한 ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="a84f5-186">ExpressRoute for Office 365</span></span>](https://aka.ms/expressrouteoffice365)
    
## <a name="see-also"></a><span data-ttu-id="a84f5-187">See Also</span><span class="sxs-lookup"><span data-stu-id="a84f5-187">See Also</span></span>

[<span data-ttu-id="a84f5-188">Microsoft 클라우드 엔터프라이즈 설계자에 대 한 네트워킹</span><span class="sxs-lookup"><span data-stu-id="a84f5-188">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="a84f5-189">Microsoft 클라우드 IT 아키텍처 리소스</span><span class="sxs-lookup"><span data-stu-id="a84f5-189">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="a84f5-190">Microsoft의 엔터프라이즈 클라우드 로드맵: IT 의사 결정권자를 위한 리소스</span><span class="sxs-lookup"><span data-stu-id="a84f5-190">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



