---
title: Microsoft 365의 데이터 복구
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
f1.keywords:
- NOCSH
description: Microsoft Microsoft 365의 데이터 복구 기능을 이해 합니다.
ms.openlocfilehash: 368f1d56ef2b4f4c9677b53122e58453ff627335
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998472"
---
# <a name="data-resiliency-in-microsoft-365"></a><span data-ttu-id="31401-103">Microsoft 365의 데이터 복구</span><span class="sxs-lookup"><span data-stu-id="31401-103">Data Resiliency in Microsoft 365</span></span>

## <a name="introduction"></a><span data-ttu-id="31401-104">소개</span><span class="sxs-lookup"><span data-stu-id="31401-104">Introduction</span></span>

<span data-ttu-id="31401-105">클라우드 컴퓨팅의 복잡 한 특성이 제공 되는 경우 Microsoft는 문제가 발생 하는 경우를 대비 하 여 문제에 대 한 것이 아니라는 것을 고려 합니다.</span><span class="sxs-lookup"><span data-stu-id="31401-105">Given the complex nature of cloud computing, Microsoft is mindful that it's not a case of if things will go wrong, but rather when.</span></span> <span data-ttu-id="31401-106">안정성을 최대화 하 고 문제가 발생 했을 때 고객에 게 부정적인 영향을 최소화 하도록 클라우드 서비스를 설계 합니다.</span><span class="sxs-lookup"><span data-stu-id="31401-106">We design our cloud services to maximize reliability and minimize the negative effects on customers when things do go wrong.</span></span> <span data-ttu-id="31401-107">Microsoft는 복잡 한 실제 인프라에 의존 하는 전통적인 전략을 넘어서 클라우드 서비스에 직접 중복성을 구축 했습니다.</span><span class="sxs-lookup"><span data-stu-id="31401-107">We have moved beyond the traditional strategy of relying on complex physical infrastructure, and we have built redundancy directly into our cloud services.</span></span> <span data-ttu-id="31401-108">Microsoft는 덜 복잡 한 실제 인프라와 서비스에 데이터 복구를 구축 하 고 고객에 게 고가용성을 제공 하는 보다 지능적 소프트웨어를 조합 하 여 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="31401-108">We use a combination of less complex physical infrastructure and more intelligent software that builds data resiliency into our services and delivers high availability to our customers.</span></span> 

## <a name="resiliency-and-recoverability-are-built-in"></a><span data-ttu-id="31401-109">복구 및 복구 기능이 기본적으로 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="31401-109">Resiliency and Recoverability Are Built-in</span></span> 

<span data-ttu-id="31401-110">복원 및 복구의 건물은 기본 인프라 및 프로세스가 어떤 점에서도 실패 한다고 가정 하 고 시작 됩니다. 하드웨어 (인프라)가 실패 하 고 오류가 발생 하 고 소프트웨어에 버그가 있는 것으로 간주 됩니다.</span><span class="sxs-lookup"><span data-stu-id="31401-110">Building in resiliency and recovery starts with the assumption that the underlying infrastructure and processes will fail at some point: hardware (infrastructure) will fail, humans will make mistakes, and software will have bugs.</span></span> <span data-ttu-id="31401-111">소프트웨어 개발자가 클라우드 전에 이러한 사항을 고려 하지 않았으므로 일반적인 IT 구현에서 이러한 문제가 처리 되는 방식은 클라우드 전에 크게 다를 것입니다.</span><span class="sxs-lookup"><span data-stu-id="31401-111">While it would be incorrect to say that software developers were not thinking about these things before the cloud, how these issues were handled in a typical IT implementation was very different before the cloud:</span></span>

- <span data-ttu-id="31401-112">먼저 하드웨어 및 인프라 보호가 중요 한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="31401-112">First, hardware and infrastructure protections were significant.</span></span> <span data-ttu-id="31401-113">이에 따라 데이터 센터가 99.99% 안정성을 갖는 경우 상당한 전력 및 네트워크 중복성이 필요 하며, 서버는 하드웨어 기반 클러스터링, 이중 전원 공급 장치 및 이중 네트워크 인터페이스와 같은 방식으로 구현 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="31401-113">This meant having datacenters with 99.99% reliability required significant power and network redundancy, and servers were implemented with hardware-based clustering, dual power supplies, dual network interfaces, and the like.</span></span> 
- <span data-ttu-id="31401-114">둘째, 프로세스는 매우 중요 했습니다.</span><span class="sxs-lookup"><span data-stu-id="31401-114">Second, process was paramount.</span></span> <span data-ttu-id="31401-115">운영 팀이 엄격한 절차를 유지 하 고 변경 된 windows를 적용 했으며 프로젝트 관리 오버 헤드가 크게 증가 했습니다.</span><span class="sxs-lookup"><span data-stu-id="31401-115">Operations teams maintained rigorous procedures, change windows were employed, and there was often significant project management overhead.</span></span> 
- <span data-ttu-id="31401-116">세 번째, 배포는 glacial 속도로 진행 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="31401-116">Third, deployment took place at a glacial pace.</span></span> <span data-ttu-id="31401-117">원본에 패치 릴리스를 기다리는 것을 소유 하지 않고 코드를 배포 하 고, 하드웨어 교체 및 중요 한 자본 outlay을 포함 하는 주 버전 릴리스</span><span class="sxs-lookup"><span data-stu-id="31401-117">Deploying code without owning the source meant waiting for patch releases, and major version releases involved hardware replacement and significant capital outlay.</span></span> <span data-ttu-id="31401-118">또한 문제를 해결 하는 유일한 방법은 롤백 이었습니다.</span><span class="sxs-lookup"><span data-stu-id="31401-118">Moreover, the only way to correct a problem was to roll back.</span></span> <span data-ttu-id="31401-119">따라서 대부분의 IT 조직은 주요 릴리스로 배포 하 여 최신 상태를 유지 하는 작업을 방지 합니다.</span><span class="sxs-lookup"><span data-stu-id="31401-119">Thus, most IT organizations would deploy only major releases to avoid the work to keep up-to-date.</span></span> 
- <span data-ttu-id="31401-120">마지막으로, 배포 된 시스템의 규모 뿐만 아니라 interconnectedness의 수준도 지금 보다 훨씬 더 작습니다.</span><span class="sxs-lookup"><span data-stu-id="31401-120">Finally, the scale of deployed systems, as well as the level of their interconnectedness was historically much smaller than it is now.</span></span> 

<span data-ttu-id="31401-121">현재 고객은 품질을 손상 시 키 지 않고 Microsoft의 지속적인 혁신을 기대 하며,이는 Microsoft의 서비스 및 소프트웨어가 복구 및 복구 력을 염두에 두고 구축 되는 이유 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="31401-121">Today, customers expect continuous innovation from Microsoft without compromising quality, and this is one of the reasons why Microsoft's services and software are built with resiliency and recoverability in mind.</span></span> 

## <a name="microsoft-365-data-resiliency-principles"></a><span data-ttu-id="31401-122">Microsoft 365 데이터 복구 원칙</span><span class="sxs-lookup"><span data-stu-id="31401-122">Microsoft 365 Data Resiliency Principles</span></span>

<span data-ttu-id="31401-123">회복성은 클라우드 기반 서비스에서 특정 유형의 오류를 견딜 수 있지만 고객 측면에서 완전히 작동 하는 기능을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="31401-123">Resiliency refers to the ability of a cloud-based service to withstand certain types of failures and yet remain fully-functional from the customers' perspective.</span></span> <span data-ttu-id="31401-124">데이터 복구는 Microsoft 365 내에서 발생 하는 오류에 관계 없이 중요 한 고객 데이터는 그대로 유지 되 고 영향을 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="31401-124">Data resiliency means that no matter what failures occur within Microsoft 365, critical customer data remains intact and unaffected.</span></span> <span data-ttu-id="31401-125">이를 위해 Microsoft 365 서비스는 다음과 같은 다섯 가지 복원 원칙을 기반으로 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="31401-125">To that end, Microsoft 365 services have been designed around five specific resiliency principles:</span></span>

- <span data-ttu-id="31401-126">중요 한 데이터와 중요 하지 않은 데이터가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31401-126">There is critical and non-critical data.</span></span> <span data-ttu-id="31401-127">드문 오류 시나리오에서 중요 하지 않은 데이터 (예: 메시지를 읽은 경우)를 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31401-127">Non-critical data (for example, whether a message was read) can be dropped in rare failure scenarios.</span></span> <span data-ttu-id="31401-128">중요 한 데이터 (예: 전자 메일 메시지 등의 고객 데이터)는 극단적인 비용으로 보호 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="31401-128">Critical data (for example, customer data such as email messages) should be protected at extreme cost.</span></span> <span data-ttu-id="31401-129">디자인 목표에 따라 배달 되는 메일 메시지는 항상 중요 하며 메시지를 읽었는지 여부와 같은 작업은 중요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="31401-129">As a design goal, delivered mail messages are always critical, and things like whether a message has been read is non-critical.</span></span> 
- <span data-ttu-id="31401-130">고객 데이터의 복사본은 다양 한 오류 영역으로 구분 하거나 가능한 한 많은 수 (예: 단일 자격 증명 (프로세스, 서버 또는 운영자)가 액세스할 수 있는 데이터 센터)로 분리 하 여 오류 격리를 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="31401-130">Copies of customer data must be separated into different fault zones or as many fault domains as possible (e.g., datacenters, accessible by single credentials (process, server, or operator)) to provide failure isolation.</span></span> 
- <span data-ttu-id="31401-131">중요 한 고객 데이터는 원자성, 일관성, 격리성, 내구성 (ACID)의 모든 부분이 실패 하는지 모니터링 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="31401-131">Critical customer data must be monitored for failing any part of Atomicity, Consistency, Isolation, Durability (ACID).</span></span> 
- <span data-ttu-id="31401-132">고객 데이터를 손상 으로부터 보호 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="31401-132">Customer data must be protected from corruption.</span></span> <span data-ttu-id="31401-133">이를 검색 하거나 모니터링, 복구 및 복구할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="31401-133">It must be actively scanned or monitored, repairable, and recoverable.</span></span> 
- <span data-ttu-id="31401-134">대부분의 데이터 손실은 고객 작업을 통해 발생 하므로 고객이 실수로 삭제 된 항목을 복원할 수 있도록 하는 GUI를 사용 하 여 자체적으로 복구할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31401-134">Most data loss results from customer actions, so allow customers to recover on their own using a GUI that enables them to restore accidentally deleted items.</span></span> 
 
<span data-ttu-id="31401-135">강력한 테스트 및 유효성 검사와 더불어, 이러한 원칙에 대 한 클라우드 서비스 구축을 통해 Microsoft 365는 고객의 요구 사항을 충족 하 고 충족할 수 있으며, 플랫폼을 지속적으로 혁신 하 고 개선 하도록 보장 합니다.</span><span class="sxs-lookup"><span data-stu-id="31401-135">Through the building of our cloud services to these principles, coupled with robust testing and validation, Microsoft 365 is able to meet and exceed the requirements of customers while ensuring a platform for continuous innovation and improvement.</span></span> 

## <a name="related-links"></a><span data-ttu-id="31401-136">관련 링크</span><span class="sxs-lookup"><span data-stu-id="31401-136">Related Links</span></span>

- [<span data-ttu-id="31401-137">데이터 손상 처리</span><span class="sxs-lookup"><span data-stu-id="31401-137">Dealing with Data Corruption</span></span>](office-365-dealing-with-data-corruption.md)
- [<span data-ttu-id="31401-138">맬웨어 및 랜섬웨어 보호</span><span class="sxs-lookup"><span data-stu-id="31401-138">Malware and Ransomware Protection</span></span>](office-365-malware-and-ransomware-protection.md)
- [<span data-ttu-id="31401-139">모니터링 및 자동 복구</span><span class="sxs-lookup"><span data-stu-id="31401-139">Monitoring and Self-Healing</span></span>](office-365-monitoring-and-self-healing.md)
- [<span data-ttu-id="31401-140">Exchange 데이터 복구</span><span class="sxs-lookup"><span data-stu-id="31401-140">Exchange Data Resiliency</span></span>](office-365-exchange-data-resiliency.md)