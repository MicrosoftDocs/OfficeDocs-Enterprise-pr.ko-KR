---
title: 서비스 거부 공격에 대 한 방어의 Office 365 핵심 원리
ms.author: robmazz
author: robmazz
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
description: Microsoft가 DoS (서비스 거부) 공격에 대 한 방어에서 absorption, 검색 및 완화의 핵심 원칙을 활용 하는 방법
ms.openlocfilehash: abfb0efda679930c22d9ce87709aded9a2880f06
ms.sourcegitcommit: 55a046bdf49bf7c62ab74da73be1fd1cf6f0ad86
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/20/2019
ms.locfileid: "37067698"
---
# <a name="core-principles-of-defense-against-denial-of-service-attacks"></a><span data-ttu-id="d14b6-103">서비스 거부 공격에 대한 보안 핵심 원칙</span><span class="sxs-lookup"><span data-stu-id="d14b6-103">Core Principles of Defense Against Denial-of-Service Attacks</span></span>

<span data-ttu-id="d14b6-104">네트워크 기반 DoS 공격 으로부터 방어할 때의 세 가지 핵심 원리는 Absorption, 검색 및 완화입니다.</span><span class="sxs-lookup"><span data-stu-id="d14b6-104">The three core principles when defending against network-based DoS attacks are Absorption, Detection, and Mitigation.</span></span> <span data-ttu-id="d14b6-105">Absorption가 검색 전에 수행 되 고 완화 되기 전에 검색이 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d14b6-105">Absorption happens before detection, and detection happens before mitigation.</span></span> <span data-ttu-id="d14b6-106">DoS 공격에 대 한 최선의 방어는 Absorption입니다.</span><span class="sxs-lookup"><span data-stu-id="d14b6-106">Absorption is the best defense against a DoS attack.</span></span> <span data-ttu-id="d14b6-107">공격을 검색할 수 없는 경우에는이를 완화할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d14b6-107">If the attack can't be detected, it can't be mitigated.</span></span> <span data-ttu-id="d14b6-108">그러나 가장 작은 DoS 공격을 수용할 수 없는 경우에도 서비스는 공격을 감지할 수 있을 정도로 오래 지속 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d14b6-108">But if even the smallest DoS attack can't be absorbed, then services aren't going to survive long enough for the attack to be detected.</span></span>

<span data-ttu-id="d14b6-109">대부분의 조직에서는 기술 및 기술 기술에 상당한 투자가 필요 하기 때문에 대부분의 조직은 DoS 공격을 위해 과다 한 용량을 구매 하는 것이 economically 불가능 합니다.</span><span class="sxs-lookup"><span data-stu-id="d14b6-109">It is not economically feasible for most organizations to purchase excess capacity to absorb DoS attacks, as this requires a considerable investment in technology and technical skills.</span></span> <span data-ttu-id="d14b6-110">이를 통해 Microsoft 클라우드 서비스를 사용 하는 경우의 보안 혜택 중 하나가 강조 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d14b6-110">This highlights one of the security benefits of using Microsoft cloud services.</span></span> <span data-ttu-id="d14b6-111">Microsoft 서비스의 엄청난 규모는 클라우드 고객에 게 비용 효율적인 방식으로 강력한 네트워크 보호 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="d14b6-111">The sheer scale of Microsoft services provides strong network protection to cloud customers in a cost-effective manner.</span></span> <span data-ttu-id="d14b6-112">그러나 규모가 큰 경우에도 absorption, 검색 및 완화 간의 균형이 유지 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d14b6-112">But even at a large scale, there must be a balance between absorption, detection, and mitigation.</span></span> <span data-ttu-id="d14b6-113">이러한 균형을 확인 하기 위해 Microsoft는 microsoft에서 충족 해야 하는 비용을 예측 하 여 공격을 평가 합니다.</span><span class="sxs-lookup"><span data-stu-id="d14b6-113">To find that balance, Microsoft studies attack growth rates to estimate how much Microsoft needs to absorb.</span></span>

<span data-ttu-id="d14b6-114">검색은 cat and 마우스 게임입니다.</span><span class="sxs-lookup"><span data-stu-id="d14b6-114">Detection is a cat-and-mouse game.</span></span> <span data-ttu-id="d14b6-115">사용자가 공격 하는 새로운 방법을 끊임없이 확인 하 여 시스템을 처치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d14b6-115">You must constantly look for new ways people are attack and try to defeat your systems.</span></span> <span data-ttu-id="d14b6-116">탐지 기능 > 완화-> 검색 > 완화 등은 무한정 지속 되는 정품 영구 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="d14b6-116">Detect -> Mitigate -> Detect -> Mitigate, etc., is a perpetual, persistent state that continues indefinitely.</span></span>

## <a name="defending-against-dos-attacks"></a><span data-ttu-id="d14b6-117">DoS 공격 으로부터 방어</span><span class="sxs-lookup"><span data-stu-id="d14b6-117">Defending Against DoS Attacks</span></span>

<span data-ttu-id="d14b6-118">DoS 공격을 성공적으로 방어 하려면 초기 검색이 필수적입니다.</span><span class="sxs-lookup"><span data-stu-id="d14b6-118">To successfully defend against a DoS attack, early detection is essential.</span></span> <span data-ttu-id="d14b6-119">시스템이 너무 defenders 전에 공격을 감지 하 여 응답 계획을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d14b6-119">By detecting an attack before the system is overwhelmed, defenders can execute a response plan.</span></span>

<span data-ttu-id="d14b6-120">다음 수식을 사용 하면 DoS 공격의 영향을 보다 근접 하 게 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d14b6-120">The following formula helps approximate the time to impact of a DoS attack:</span></span>

   <span data-ttu-id="d14b6-121">**최대 용량 (바이트/초)/증가율 (바이트/초) = 영향에 대 한 시간 (바이트/초)**</span><span class="sxs-lookup"><span data-stu-id="d14b6-121">**Maximum Capacity (in bytes/sec) / Growth Rate (in bytes/sec) = Time to Impact (in bytes/sec)**</span></span>

<span data-ttu-id="d14b6-122">시간에 영향을 미치는 후에도 검색이 시간에 발생 하는 경우 DoS 공격이 성공할 가능성이 높습니다.</span><span class="sxs-lookup"><span data-stu-id="d14b6-122">If the time-to-detection occurs after time-to-impact, it is likely the DoS attack will be successful.</span></span> <span data-ttu-id="d14b6-123">시간에 영향을 미치는 시간을 검색 하는 경우 공격에 대 한 서비스는 온라인 상태를 유지 하 고 완화 전략이 사용 되는 경우에도 액세스할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d14b6-123">If the time-to-detection occurs before time-to-impact, the attacked services should remain online and accessible if mitigation strategies are used.</span></span> <span data-ttu-id="d14b6-124">따라서 DoS 공격 으로부터 보호 하기 위해 두 가지 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d14b6-124">Thus, there are only two things that can be done to defend against DoS attacks:</span></span>

- <span data-ttu-id="d14b6-125">용량을 늘려 최대 용량에 대 한 천장을 증대 시켜 공격을 감지 하는 데 더 많은 시간을 제공 합니다. 사용자나</span><span class="sxs-lookup"><span data-stu-id="d14b6-125">Increase capacity to raise the ceiling of maximum capacity (which in turn provides more time to detect an attack); or</span></span>
- <span data-ttu-id="d14b6-126">검색 하는 데 걸리는 시간을 단축 합니다.</span><span class="sxs-lookup"><span data-stu-id="d14b6-126">Decrease the time to detect.</span></span>

<span data-ttu-id="d14b6-127">용량 증가는 회계에 직접적인 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d14b6-127">Increasing capacity has a direct fiscal impact.</span></span> <span data-ttu-id="d14b6-128">고객은 기본 absorption 용량을 개발 하 여 일부 DoS 공격 수준을 유지 하도록 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d14b6-128">Microsoft recommends that customers develop at least basic absorption capacity to ensure that they can survive some level of DoS attack.</span></span> <span data-ttu-id="d14b6-129">각 고객이 노출, 위험 및 재무 outlay에 대 한 자체 임계값을 가지 며 실제 absorption 용량은 고객 마다 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="d14b6-129">The actual absorption capacity varies from customer to customer, as each customer has their own thresholds for exposure, risk, and financial outlay.</span></span> <span data-ttu-id="d14b6-130">경제적 이유로 인해 검색 시간을 줄이는 방법에 대 한 연구 및 시간 투자는 대개 가장 비용 효율적인 방어 수단입니다.</span><span class="sxs-lookup"><span data-stu-id="d14b6-130">For economic reasons, investments in research and time for ways to decrease time-to-detection are usually the most cost-effective defense.</span></span>
