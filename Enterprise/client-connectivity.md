---
title: 클라이언트 연결
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 7/6/2017
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 4232abcf-4ae5-43aa-bfa1-9a078a99c78b
description: '요약: 클라이언트 컴퓨터 및 Office 365 테 넌 트 데이터 센터의 위치에 따라 클라이언트 컴퓨터가 Office 365 테 넌 트에 연결 되는 방식을 설명 합니다.'
ms.openlocfilehash: 0a5a7351b3d756763f05a8136e7ce6bc16f8f881
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843829"
---
# <a name="client-connectivity"></a><span data-ttu-id="075bb-103">클라이언트 연결</span><span class="sxs-lookup"><span data-stu-id="075bb-103">Client connectivity</span></span>

 <span data-ttu-id="075bb-104">**요약:** 클라이언트 컴퓨터 및 Office 365 테 넌 트 데이터 센터의 위치에 따라 클라이언트 컴퓨터가 Office 365 테 넌 트에 연결 되는 방식을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="075bb-104">**Summary:** Explains how client computers connect to Office 365 tenants, depending on the location of the client computer and Office 365 tenant datacenter.</span></span>
  
<span data-ttu-id="075bb-105">Office 365는 지진 또는 정전 같은 한 지역에 주요 문제가 있는 경우에도 서비스를 유지 하 고 실행 하는 데 도움이 되는 Microsoft 데이터 센터에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="075bb-105">Office 365 resides in Microsoft datacenters around the world which help keep the service up and running even when there's a major problem in one region, such as an earthquake or a power outage.</span></span> <span data-ttu-id="075bb-106">Office 365 테 넌 트에 연결 하면 클라이언트 연결에 테 넌 트가 호스트 되는 해당 데이터 센터가 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="075bb-106">When you connect to your Office 365 tenant, the client connection will be directed to the appropriate datacenter where your tenant is being hosted.</span></span> <span data-ttu-id="075bb-107">테 넌 트를 호스팅할 수 있는 위치를 결정 하는 규칙은 Microsoft와의 계약에 따라 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="075bb-107">The rules that determine where your tenant can be hosted are defined by your agreement with Microsoft.</span></span> <span data-ttu-id="075bb-108">클라이언트의 데이터를 가져오는 방법을 결정 하는 규칙은 사용 중인 서비스의 아키텍처에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="075bb-108">The rules that determine how your client acquires the data from that datacenter location depend on the architecture of the service you're using.</span></span>
  
<span data-ttu-id="075bb-109">예를 들어 Office 365 포털에 로그온 하는 경우 일반적으로 클라이언트에 가장 가까운 데이터 센터에 연결 되 고 다음에 사용 하는 서비스에 따라 방향이 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="075bb-109">For example, when you log on to the Office 365 portal, you're usually connected to the closest datacenter to the client and then directed depending on the service you use next.</span></span> <span data-ttu-id="075bb-110">전자 메일을 시작 하면 가장 가까운 데이터 센터에서 UI를 표시 하는 초기 연결이 가능 하지만, 사용자가 읽은 전자 메일의 내용을 표시 하기 위해 테 넌 트에 있는 가장 가까운 데이터 센터와 데이터 센터 사이에 보조 연결이 열릴 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="075bb-110">If you launch email, the initial connection to display the UI may still come from the nearest datacenter, but a second connection might be opened between the nearest datacenter and the datacenter where your tenant is located to show you what's in the emails you read.</span></span> <span data-ttu-id="075bb-111">Microsoft는 전세계 상위 10 개 네트워크 중 하나를 운영 하 여 데이터 센터 간 연결이 매우 빠릅니다.</span><span class="sxs-lookup"><span data-stu-id="075bb-111">Microsoft operates one of the top ten networks in the world, resulting in incredibly fast datacenter-to-datacenter connections.</span></span>
  
<span data-ttu-id="075bb-112">이 문서를 읽은 후에는 데이터 센터 당 [Office 365 url 및 IP 주소 범위](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2) 를 제공 하지 않는 이유를 이해 하 고, 단순히 상호 연결 되어 있으며 서로 의존 하 여 해당 항목을 적절 하 게 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="075bb-112">After you read the article, you'll likely understand why we don't provide [Office 365 URLs and IP address ranges](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2) per datacenter, they are simply too interconnected and reliant on each other to make that feasible.</span></span>
  
<span data-ttu-id="075bb-113">Office 365 용 Azure Express 경로를 사용 하는 경우 대부분의 경우 여기에 설명 된 공용 연결 대신 Office 365에 대 한 개인 연결을 통해 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="075bb-113">If you're using Azure ExpressRoute for Office 365, in most cases your connectivity will go over a private connection to Office 365 instead of the public connection described here.</span></span> <span data-ttu-id="075bb-114">클라이언트 연결 방법에 대 한 원칙은 여전히 정확 합니다.</span><span class="sxs-lookup"><span data-stu-id="075bb-114">The principles about how clients connect are still accurate.</span></span> <span data-ttu-id="075bb-115">[Office 365의 Azure express](azure-expressroute.md)경로에 대해 자세히 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="075bb-115">Learn more about [Azure ExpressRoute for Office 365](azure-expressroute.md).</span></span>
  
<span data-ttu-id="075bb-116">비즈니스용 Skype 네트워크 요청에 대 한 자세한 내용은 [비즈니스용 Skype Online의 미디어 품질 및 네트워크 연결 성능](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917)문서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="075bb-116">For more depth on Skype for Business network requests, read the article [Media Quality and Network Connectivity Performance in Skype for Business Online](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917).</span></span>

||
|:-----|
| <span data-ttu-id="075bb-117">이 문서는 [Office 365의 네트워크 계획 및 성능 조정](https://aka.ms/tune)의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="075bb-117">This article is part of [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>|

> [!NOTE]
> <span data-ttu-id="075bb-118">Microsoft는 데이터 센터에서 안전 하 고 개인적으로 it를 관리 하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="075bb-118">We take great care to manage customer data so it's secure and private in our datacenters.</span></span> <span data-ttu-id="075bb-119">개인 정보를 관리 하기 위해 수행 하는 단계에 대 한 자세한 내용은 [보안 센터](https://go.microsoft.com/fwlink/?LinkID=397383)에 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="075bb-119">Details about the steps we take to manage privacy are included in the [Trust Center](https://go.microsoft.com/fwlink/?LinkID=397383).</span></span>
  
## <a name="connecting-to-the-nearest-datacenter"></a><span data-ttu-id="075bb-120">가장 가까운 데이터 센터에 연결</span><span class="sxs-lookup"><span data-stu-id="075bb-120">Connecting to the nearest datacenter</span></span>

<span data-ttu-id="075bb-121">가장 일반적인 연결 유형이 며 Office 365 포털 및 Exchange Online 둘 다에서 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="075bb-121">This is the most common type of connection, and it's used by both the Office 365 portal and Exchange Online.</span></span> <span data-ttu-id="075bb-122">이러한 상황에서 클라이언트가 Office 365에 연결을 시도 하면 해당 컴퓨터의 DNS 쿼리에서 컴퓨터가 들어오는 세계 지역을 확인 하 고, Office 365에서 가장 가까운 데이터 센터로 요청을 리디렉션합니다.</span><span class="sxs-lookup"><span data-stu-id="075bb-122">In this situation, when clients attempt to connect to Office 365, their computer's DNS query determines the region of the world their computer is coming from, and Office 365 redirects the request to the nearest datacenter.</span></span>
  
<span data-ttu-id="075bb-123">포털에 대 한 연결이 가장 가까운 데이터 센터에서 중지 되 고 클라이언트 컴퓨터에 해당 위치의 클라이언트 테 넌 트에 대 한 정보가 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="075bb-123">Connections to the portal stop at the nearest datacenter, and the client computer is presented with information about the client's tenant from that location.</span></span>
  
<span data-ttu-id="075bb-124">Exchange Online에는 추가 단계가 더 진행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="075bb-124">Exchange Online goes a step further.</span></span> <span data-ttu-id="075bb-125">클라이언트 컴퓨터가 가장 가까운 데이터 센터에 연결 되 면 아래의 *작업 방법 섹션* 에 나와 있는 것 처럼 해당 데이터 센터의 Exchange 서버가 테 넌 트를 실제로 사용 하는 데이터 센터에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="075bb-125">Once the client computer is connected to the nearest datacenter, an Exchange server in that datacenter connects to the datacenter where the tenant is actually located as illustrated in the  *How does this work section*  below.</span></span> <span data-ttu-id="075bb-126">가장 가까운 데이터 센터의 Exchange Online 서버는 클라이언트 컴퓨터의 요청을 사서함 서버로 프록시 합니다.</span><span class="sxs-lookup"><span data-stu-id="075bb-126">The Exchange Online servers in the nearest datacenter then proxy the requests from the client computer to the mailbox server.</span></span> <span data-ttu-id="075bb-127">이렇게 하면 전자 메일 및 일정 항목을 Microsoft 네트워크로 검색 하는 데 많은 문제가 발생 하 여 클라이언트 컴퓨터의 환경이 향상 됩니다.</span><span class="sxs-lookup"><span data-stu-id="075bb-127">This speeds up the experience for the client computer by moving the heavy lifting of retrieving emails and calendar items to the Microsoft network.</span></span>
  
## <a name="how-does-this-work-for-standard-cloud-offerings"></a><span data-ttu-id="075bb-128">표준 클라우드 제품에 대 한이 작업은 어떤 방식으로 작동 하나요?</span><span class="sxs-lookup"><span data-stu-id="075bb-128">How does this work for standard cloud offerings?</span></span>

<span data-ttu-id="075bb-129">이 연결 프로세스는 Office 365와 같은 높은 트래픽, 높은 가치 웹 응용 프로그램의 표준입니다.</span><span class="sxs-lookup"><span data-stu-id="075bb-129">This connection process is standard for high traffic, high value web applications like Office 365.</span></span> <span data-ttu-id="075bb-130">이 섹션에서는 프로세스의 단계를 대략적으로 설명 하 고 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="075bb-130">In this section, we outline and illustrate the steps in the process.</span></span> <span data-ttu-id="075bb-131">클라이언트 컴퓨터가 테 넌 트와 같은 지역에 있지 않으면 클라이언트에서 연결 하는 서비스에 따라 연결이 크게 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="075bb-131">When the client computer is not in the same region as the tenant, the connection looks much different depending on the service the client is connecting to.</span></span>
  
 <span data-ttu-id="075bb-132">이 다이어그램은 북미의 테 넌 트와 함께 표준 Office 365 제공을 사용 하는 고객을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="075bb-132">This diagram depicts a customer using a standard Office 365 offering with a tenant in North America.</span></span> <span data-ttu-id="075bb-133">이 시나리오에서는 요청을 만드는 사용자가 유럽으로 이동 되었으며 해당 위치에서 Office 365을 사용 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="075bb-133">In this scenario, the person making the request has traveled to Europe and is using Office 365 from that location.</span></span>
  
1. <span data-ttu-id="075bb-134">클라이언트 컴퓨터에서 로컬 DNS 서버에 Office 365와 연결 된 IP 주소를 묻습니다.</span><span class="sxs-lookup"><span data-stu-id="075bb-134">The client computer asks the local DNS servers for the IP address associated with Office 365.</span></span>

2. <span data-ttu-id="075bb-135">클라이언트 컴퓨터의 로컬 DNS 서버가 Microsoft DNS 서버에 Office 365와 연결 된 IP 주소를 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="075bb-135">The client computer's local DNS servers ask the Microsoft DNS servers for the IP address associated with Office 365.</span></span>

3. <span data-ttu-id="075bb-136">Microsoft의 DNS 서버에서 클라이언트의 DNS 서버 위치를 기반으로 지역 서버 이름을 반환 하며, 클라이언트 컴퓨터에서 1 단계와 2 단계가 반복 하 여 지역 사무소 365 데이터 센터의 IP 주소를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="075bb-136">Microsoft's DNS servers return the regional server name (based on the location of the client's DNS servers), and the client computer repeats steps 1 and 2 to obtain the IP address of the regional Office 365 datacenter.</span></span>

4. <span data-ttu-id="075bb-137">클라이언트 컴퓨터에서 지역별 데이터 센터 IP 주소에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="075bb-137">The client computer connects to the regional datacenter IP address.</span></span>

5. <span data-ttu-id="075bb-138">Exchange Online 서버는 고객의 테 넌 트가 있는 활성 데이터 센터에 대 한 연결을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="075bb-138">The Exchange Online servers establish a connection to the active datacenter where the customer's tenant resides.</span></span>

![가장 가까운 지역 데이터 센터](media/4ea108e9-a299-4e3d-b0d3-469b434ff899.png)
  
## <a name="how-does-this-work-for-sovereign-cloud-offerings"></a><span data-ttu-id="075bb-140">Sovereign 클라우드에 클라우드 제품에서이 작업을 수행 하는 방법은 무엇 인가요?</span><span class="sxs-lookup"><span data-stu-id="075bb-140">How does this work for sovereign cloud offerings?</span></span>

<span data-ttu-id="075bb-141">이 연결은 21 Vianet 되며에서 운영 하는 Office 365와 같은 sovereign 클라우드에 클라우드 서비스와 약간 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="075bb-141">This connection is slightly different for sovereign cloud offerings such as Office 365 operated by 21 Vianet.</span></span> <span data-ttu-id="075bb-142">테 넌 트를 Office 365의 sovereign 클라우드에 인스턴스에서 사용 하는 경우에는 포털 연결을 허용 하는 가장 가까운 Office 365 서버가 테 넌 트가 상주 하는 sovereign 클라우드에 지역 내의 서버입니다.</span><span class="sxs-lookup"><span data-stu-id="075bb-142">With the tenant in a sovereign instance of Office 365, the nearest Office 365 servers that will accept portal connections are the servers within the sovereign region where the tenant resides.</span></span> <span data-ttu-id="075bb-143">마찬가지로, sovereign 클라우드에 클라우드 또는 표준 제품에서 SharePoint Online에 액세스 하는 고객은 테 넌 트가 있는 프런트 엔드 서버로 향합니다.</span><span class="sxs-lookup"><span data-stu-id="075bb-143">Similarly, customers accessing SharePoint Online in our sovereign cloud or standard offerings will be directed to front end servers where the tenant resides.</span></span> <span data-ttu-id="075bb-144">아래에서 활성 데이터 센터에 연결을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="075bb-144">See connecting to the active datacenter below.</span></span>
  
1. <span data-ttu-id="075bb-145">클라이언트 컴퓨터에서 로컬 DNS 서버에 Office 365와 연결 된 IP 주소를 묻습니다.</span><span class="sxs-lookup"><span data-stu-id="075bb-145">The client computer asks the local DNS servers for the IP address associated with Office 365.</span></span>

2. <span data-ttu-id="075bb-146">클라이언트 컴퓨터의 로컬 DNS 서버가 Microsoft DNS 서버에 Office 365와 연결 된 IP 주소를 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="075bb-146">The client computer's local DNS servers ask the Microsoft DNS servers for the IP address associated with Office 365.</span></span>

3. <span data-ttu-id="075bb-147">Microsoft의 DNS 서버에서 클라이언트의 DNS 서버 위치를 기반으로 지역 서버 이름을 반환 하며, 클라이언트 컴퓨터에서 1 단계와 2 단계가 반복 하 여 지역 사무소 365 데이터 센터의 IP 주소를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="075bb-147">Microsoft's DNS servers return the regional server name (based on the location of the client's DNS servers), and the client computer repeats steps 1 and 2 to obtain the IP address of the regional Office 365 datacenter.</span></span>

4. <span data-ttu-id="075bb-148">클라이언트 컴퓨터에서 지역별 데이터 센터 IP 주소에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="075bb-148">The client computer connects to the regional datacenter IP address.</span></span>

5. <span data-ttu-id="075bb-149">Exchange Online 서버는 고객의 테 넌 트가 있는 활성 데이터 센터에 대 한 연결을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="075bb-149">The Exchange Online servers establish a connection to the active datacenter where the customer's tenant resides.</span></span>

![가장 가까운 지역 한국 데이터 센터](media/c0628c54-0059-48c5-8a0f-41bf392ee182.png)
  
## <a name="connecting-to-the-active-datacenter"></a><span data-ttu-id="075bb-151">활성 데이터 센터에 연결</span><span class="sxs-lookup"><span data-stu-id="075bb-151">Connecting to the active datacenter</span></span>

<span data-ttu-id="075bb-152">활성 데이터 센터에 연결 하는 기능은 더 무거운 데이터 전송 작업을 위해 디자인 되었으며, 현재 SharePoint Online에서 사용 되 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="075bb-152">Connecting to the active datacenter is designed for heavier data transfer workloads and is currently used by SharePoint Online.</span></span> <span data-ttu-id="075bb-153">이러한 상황에서 클라이언트가 Office 365에 연결 하려고 하면 해당 브라우저가 SharePoint Online 테 넌 트에 대 한 활성 데이터 센터로 리디렉션됩니다.</span><span class="sxs-lookup"><span data-stu-id="075bb-153">In this situation, when clients attempt to connect to Office 365, their browser is redirected to the active datacenter for their SharePoint Online tenant.</span></span>
  
## <a name="how-does-this-work"></a><span data-ttu-id="075bb-154">작동 방식</span><span class="sxs-lookup"><span data-stu-id="075bb-154">How does this work?</span></span>

<span data-ttu-id="075bb-155">클라이언트 컴퓨터가 다른 지역에서 SharePoint Online에 연결 하는 경우에는 연결이 활성 SharePoint Online 데이터 센터로 리디렉션됩니다.</span><span class="sxs-lookup"><span data-stu-id="075bb-155">When the client computer is connecting to SharePoint Online from a different region, the connection is redirected to the active SharePoint Online datacenter.</span></span> <span data-ttu-id="075bb-156">이 시나리오에서 고객은 표준 제공을 사용 하 여 포털 연결이 나머지 로컬에 있고 SharePoint Online 연결이 활성 데이터 센터로 이동 하 게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="075bb-156">In this scenario, the customer is using a standard offering, resulting in the portal connections remaining local and the SharePoint Online connections being directed to the active datacenter.</span></span>
  
1. <span data-ttu-id="075bb-157">클라이언트 컴퓨터에서 로컬 DNS 서버에 Office 365와 연결 된 IP 주소를 묻습니다.</span><span class="sxs-lookup"><span data-stu-id="075bb-157">The client computer asks the local DNS servers for the IP address associated with Office 365.</span></span>

2. <span data-ttu-id="075bb-158">클라이언트 컴퓨터의 로컬 DNS 서버가 Microsoft DNS 서버에 Office 365와 연결 된 IP 주소를 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="075bb-158">The client computer's local DNS servers ask the Microsoft DNS servers for the IP address associated with Office 365.</span></span>

3. <span data-ttu-id="075bb-159">Microsoft의 DNS 서버가 클라이언트의 Office 365 테 넌 트의 위치를 기반으로 활성 SharePoint Online 데이터 센터의 서버 이름을 반환 하며, 클라이언트 컴퓨터에서 1 단계와 2 단계로 반복 하 여 활성 Office 365 데이터 센터의 IP 주소를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="075bb-159">Microsoft's DNS servers return the server name of the active SharePoint Online datacenter (based on the location of the client's Office 365 tenant), and the client computer repeats steps 1 and 2 to obtain the IP address of the active Office 365 datacenter.</span></span>

4. <span data-ttu-id="075bb-160">클라이언트 컴퓨터에서 활성 데이터 센터의 IP 주소에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="075bb-160">The client computer connects to the active datacenter IP address.</span></span>

![활성 한국 데이터 센터](media/c6d2933f-49cb-4536-bea7-c868707755ae.png)
  
## <a name="connecting-over-virtual-private-networks-vpns"></a><span data-ttu-id="075bb-162">Vpn (가상 사설망)을 통해 연결</span><span class="sxs-lookup"><span data-stu-id="075bb-162">Connecting over Virtual Private Networks (VPNs)</span></span>

<span data-ttu-id="075bb-163">이 연결 유형은 클라이언트 컴퓨터에서 VPN (가상 사설망)을 사용 하는 경우에만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="075bb-163">This type of connection applies only when a virtual private network (VPN) is used by client computers.</span></span> <span data-ttu-id="075bb-164">365 실제로는 VPN이 사용 되지만 vpn은 일반적으로 클라이언트 컴퓨터가 Office 365에 연결을 설정 하는 방법을 제어 하는 데 사용 되며, 일반적으로는 환경에 성능이 저하 되기 때문에, 이러한 동작은 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="075bb-164">In reality, Office 365 behavior isn't changed simply because a VPN is used, but VPNs are commonly used to control how client computers establish connections to Office 365 and usually results in a degraded experience, so it's important to cover.</span></span>
  
## <a name="how-does-this-work"></a><span data-ttu-id="075bb-165">작동 방식</span><span class="sxs-lookup"><span data-stu-id="075bb-165">How does this work?</span></span>

<span data-ttu-id="075bb-166">클라이언트 컴퓨터에서 다른 지역의 회사 사무실에 대 한 VPN 연결을 설정 하면 클라이언트 컴퓨터의 위치에 있는 DNS 서버 대신 해당 사무실의 DNS 서버가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="075bb-166">When the client computer establishes a VPN connection to a corporate office in a different region, the DNS servers at that office are used instead of the DNS servers at the client computer's location.</span></span> <span data-ttu-id="075bb-167">대부분의 경우 VPN을 통한이 추가 연결이 Office 365 환경을 저하 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="075bb-167">In most cases, this extra connection over the VPN will degrade the Office 365 experience.</span></span> <span data-ttu-id="075bb-168">Office 365 서비스는 최종 사용자에 게 가능한 한 근접으로 고객 연결 서비스에 최적화 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="075bb-168">The Office 365 services are optimized to service customer connections as close to the end user as possible.</span></span> <span data-ttu-id="075bb-169">대부분의 서비스에서는 Office 365 서비스에 대 한 네트워크 요청이 클라이언트 컴퓨터에 근접 한 경우 Microsoft 네트워크에서 Azure에 지 네트워크, 콘텐츠 배달 네트워크 및 안정적인 네트워크 용량을 활용 하 여 최상의 사용자 환경을 제공 합니다. 가능한 경우</span><span class="sxs-lookup"><span data-stu-id="075bb-169">Many services leverage the Azure edge network, Content Delivery Networks, and the reliable network capacity on the Microsoft network to deliver the best possible user experience when network requests for Office 365 services are made as close to the client computer as possible.</span></span>
  
1. <span data-ttu-id="075bb-170">클라이언트 컴퓨터에서 VPN DNS 서버에 Office 365와 연결 된 IP 주소를 묻습니다.</span><span class="sxs-lookup"><span data-stu-id="075bb-170">The client computer asks the VPN DNS servers for the IP address associated with Office 365.</span></span>

2. <span data-ttu-id="075bb-171">클라이언트 컴퓨터의 VPN DNS 서버는 Microsoft DNS 서버에 Office 365와 연결 된 IP 주소를 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="075bb-171">The client computer's VPN DNS servers ask the Microsoft DNS servers for the IP address associated with Office 365.</span></span>

3. <span data-ttu-id="075bb-172">Microsoft의 DNS 서버에서 VPN DNS 서버 위치를 기반으로 지역 서버 이름을 반환 하며, 클라이언트 컴퓨터에서 1 단계와 2 단계가 반복 되어 지역 사무소 365 데이터 센터의 IP 주소 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="075bb-172">Microsoft's DNS servers return the regional server name (based on the location of the VPN DNS servers), and the client computer repeats steps 1 and 2 to obtain the IP address information of the regional Office 365 datacenter.</span></span>

4. <span data-ttu-id="075bb-173">클라이언트 컴퓨터에서 VPN 연결을 설정한 본사와 가장 가까운 데이터 센터 IP 주소에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="075bb-173">The client computer connects to the datacenter IP address that's closest to the corporate office they established a VPN connection with.</span></span>

![VPN 데이터 센터 연결](media/b5f4c06c-65a3-462d-aae8-9a4602dd8d9e.png)
  
<span data-ttu-id="075bb-175">다음의 간단한 링크를 사용할 수 있습니다. [https://aka.ms/o365clientconnectivity](https://aka.ms/o365clientconnectivity)</span><span class="sxs-lookup"><span data-stu-id="075bb-175">Here's a short link you can use to come back: [https://aka.ms/o365clientconnectivity](https://aka.ms/o365clientconnectivity)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="075bb-176">참고 항목</span><span class="sxs-lookup"><span data-stu-id="075bb-176">See also</span></span>

[<span data-ttu-id="075bb-177">Office 365 끝점 관리</span><span class="sxs-lookup"><span data-stu-id="075bb-177">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
<span data-ttu-id="075bb-178">[Office 365 네트워크 연결성 평가하기](assessing-network-connectivity.md) </span><span class="sxs-lookup"><span data-stu-id="075bb-178">[Assessing Office 365 network connectivity](assessing-network-connectivity.md)</span></span>
