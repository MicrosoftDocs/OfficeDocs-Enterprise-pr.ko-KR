---
title: Office 365에서 서비스 거부 공격 으로부터 보호
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
f1.keywords:
- NOCSH
description: DoS (서비스 거부) 공격의 개요
ms.openlocfilehash: 16378800fc7bb61b8f78e2c4c51eb7940cb45d17
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843591"
---
# <a name="defend-against-denial-of-service-attacks-in-office-365"></a><span data-ttu-id="f72c2-103">Office 365에서 서비스 거부 공격 으로부터 보호</span><span class="sxs-lookup"><span data-stu-id="f72c2-103">Defend Against Denial-of-Service Attacks in Office 365</span></span>

## <a name="introduction"></a><span data-ttu-id="f72c2-104">소개</span><span class="sxs-lookup"><span data-stu-id="f72c2-104">Introduction</span></span>

<span data-ttu-id="f72c2-105">Microsoft는 100 데이터 센터 보다 많은 글로벌 클라우드 인프라에 호스트 되는 200 개 이상의 클라우드 서비스에 대해 신뢰할 수 있는 인프라를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="f72c2-105">Microsoft delivers a trustworthy infrastructure for more than 200 cloud services hosted in a global cloud infrastructure of more than 100 datacenters.</span></span> <span data-ttu-id="f72c2-106">여기에는 다음이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="f72c2-106">These include:</span></span>

- <span data-ttu-id="f72c2-107">Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="f72c2-107">Microsoft Azure</span></span>
- <span data-ttu-id="f72c2-108">Microsoft Bing</span><span class="sxs-lookup"><span data-stu-id="f72c2-108">Microsoft Bing</span></span>
- <span data-ttu-id="f72c2-109">Microsoft Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="f72c2-109">Microsoft Dynamics 365</span></span>
- <span data-ttu-id="f72c2-110">Microsoft Office 365</span><span class="sxs-lookup"><span data-stu-id="f72c2-110">Microsoft Office 365</span></span>
- <span data-ttu-id="f72c2-111">Microsoft OneDrive</span><span class="sxs-lookup"><span data-stu-id="f72c2-111">Microsoft OneDrive</span></span>
- <span data-ttu-id="f72c2-112">시간이</span><span class="sxs-lookup"><span data-stu-id="f72c2-112">Skype</span></span>
- <span data-ttu-id="f72c2-113">Xbox LIVE</span><span class="sxs-lookup"><span data-stu-id="f72c2-113">Xbox Live</span></span>

<span data-ttu-id="f72c2-114">인터넷 현재 상태와 클라우드 서비스를 제공 하는 다양 한 인터넷 속성을 가진 전역 조직으로, Microsoft는 해커 및 기타 악의적인 개인이 사용할 수 있는 광범위 한 일반 목표입니다.</span><span class="sxs-lookup"><span data-stu-id="f72c2-114">As a global organization with a significant Internet presence and many prominent Internet properties that provide cloud services, Microsoft is a large, common target for hackers and other malicious individuals.</span></span> <span data-ttu-id="f72c2-115">클라이언트와 Microsoft 클라우드 간의 네트워크 통신 계층은 악의적인 공격의 가장 큰 목표 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="f72c2-115">The network communication layer between clients and the Microsoft Cloud is one of the biggest targets of malicious attacks.</span></span> <span data-ttu-id="f72c2-116">실제로 Microsoft는 특정 형태의 네트워크 기반에서는 사이버 공격과 계속 해 서 지속적으로 영구적으로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f72c2-116">In fact, Microsoft is continuously and persistently under some form of network-based cyberattack.</span></span> <span data-ttu-id="f72c2-117">이 줄에서 Microsoft는 심층 방어 보안 원칙을 사용 하 여 클라우드 서비스 및 네트워크를 보호 합니다.</span><span class="sxs-lookup"><span data-stu-id="f72c2-117">In line with this, Microsoft uses defense-in-depth security principles to protect its cloud services and networks.</span></span> <span data-ttu-id="f72c2-118">이러한 공격 으로부터 보호 하는 안정적이 고 지속적인 완화 시스템이 없는 경우 Microsoft의 클라우드 서비스는 오프 라인 상태 이며 고객이 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f72c2-118">Without reliable and persistent mitigation systems that defend against these attacks, Microsoft's cloud services would be offline and unavailable to customers.</span></span>

## <a name="definition-and-symptoms-of-denial-of-service-attacks"></a><span data-ttu-id="f72c2-119">서비스 거부 공격의 정의 및 증상</span><span class="sxs-lookup"><span data-stu-id="f72c2-119">Definition and Symptoms of Denial-of-Service Attacks</span></span>

<span data-ttu-id="f72c2-120">네트워크 서비스를 공격할 수 있는 한 가지 방법은 네트워크 및 서버가 합법적인 사용자에 게 서비스를 거부할 수 있도록 서비스 호스트에 대 한 많은 요청을 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f72c2-120">One way to attack network services is to create many requests against service hosts to overwhelm the network and servers to deny service to legitimate users.</span></span> <span data-ttu-id="f72c2-121">이를 DoS (서비스 거부) 공격 이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="f72c2-121">This is referred to as a denial-of-service (DoS) attack.</span></span> <span data-ttu-id="f72c2-122">여러 행위자, 끝점 및/또는 벡터로 공격을 수행 하는 경우 분산 서비스 거부 (DDoS) 공격 이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="f72c2-122">When the attack is performed by multiple actors, endpoints, and/or vectors, it is referred to as a distributed denial-of-service (DDoS) attack.</span></span> <span data-ttu-id="f72c2-123">방법, 동기, 대상이 서로 다를 수 있지만 DoS 및 DDoS 공격은 일반적으로 인터넷 사이트 또는 서비스가 일시적으로 또는 무기한으로 정상적으로 작동 하는 것을 방지 하기 위한 노력으로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f72c2-123">Although the means, motives, and targets vary, DoS and DDoS attacks generally consist of efforts to prevent an Internet site or service from functioning correctly or at all, either temporarily or indefinitely.</span></span>

<span data-ttu-id="f72c2-124">[미국 컴퓨터 응급 준비 팀](https://www.us-cert.gov/) (미국-CERT)은 DoS 공격이 포함 될 증상을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="f72c2-124">The [United States Computer Emergency Readiness Team](https://www.us-cert.gov/) (US-CERT) defines symptoms of DoS attacks to include:</span></span>

- <span data-ttu-id="f72c2-125">네트워크 성능이 비정상적으로 느립니다 (파일을 열거나 인터넷 사이트에 액세스 하는 경우).</span><span class="sxs-lookup"><span data-stu-id="f72c2-125">Unusually slow network performance (when opening files or accessing Internet sites)</span></span>
- <span data-ttu-id="f72c2-126">웹 사이트를 사용할 비 사용할 때</span><span class="sxs-lookup"><span data-stu-id="f72c2-126">Unavailability of a Web site</span></span>
- <span data-ttu-id="f72c2-127">웹 사이트에 액세스할 수 없음</span><span class="sxs-lookup"><span data-stu-id="f72c2-127">Inability to access a Web site</span></span>
- <span data-ttu-id="f72c2-128">받은 스팸의 급격 한 증가</span><span class="sxs-lookup"><span data-stu-id="f72c2-128">Dramatic increase in received spam</span></span>
- <span data-ttu-id="f72c2-129">무선 또는 유선 인터넷 연결 끊기</span><span class="sxs-lookup"><span data-stu-id="f72c2-129">Disconnection of a wireless or wired Internet connection</span></span>
- <span data-ttu-id="f72c2-130">웹 또는 인터넷 서비스에 대 한 장기간 액세스 권한 손실</span><span class="sxs-lookup"><span data-stu-id="f72c2-130">Long-term loss of access to the Web or any Internet services</span></span>

## <a name="related-topics"></a><span data-ttu-id="f72c2-131">관련 주제</span><span class="sxs-lookup"><span data-stu-id="f72c2-131">Related Topics</span></span>

- [<span data-ttu-id="f72c2-132">서비스 거부 공격에 대한 보안 핵심 원칙</span><span class="sxs-lookup"><span data-stu-id="f72c2-132">Core Principles of Defense Against Denial-of-Service Attacks</span></span>](office-365-core-principles-of-defense-against-dos-attacks.md)
- [<span data-ttu-id="f72c2-133">Microsoft의 서비스 거부 방어 전략</span><span class="sxs-lookup"><span data-stu-id="f72c2-133">Microsoft's Denial-of-Service Defense Strategy</span></span>](office-365-microsoft-dos-defense-strategy.md)
- [<span data-ttu-id="f72c2-134">서비스 거부 공격에 대해 Microsoft 클라우드 서비스 방어</span><span class="sxs-lookup"><span data-stu-id="f72c2-134">Defending Microsoft Cloud Services Against Denial-of-Service Attacks</span></span>](office-365-defending-cloud-services-against-dos-attacks.md)
