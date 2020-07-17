---
title: Microsoft 365 데이터 손상 처리
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
description: Microsoft 365의 데이터 손상 및 Microsoft의 예방 및 복구 작업에 대해 설명 합니다.
ms.openlocfilehash: 674f2a3a026c5706f5c3a23db6e2d968ed815656
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998452"
---
# <a name="dealing-with-data-corruption-in-microsoft-365"></a><span data-ttu-id="3fc1c-103">Microsoft 365의 데이터 손상 처리</span><span class="sxs-lookup"><span data-stu-id="3fc1c-103">Dealing with Data Corruption in Microsoft 365</span></span>

<span data-ttu-id="3fc1c-104">대규모 클라우드 서비스를 실행할 때의 까다로운 측면 중 하나는 대규모 데이터 및 독립 시스템에 따라 데이터 손상을 처리 하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="3fc1c-104">One of the challenging aspects of running a large-scale cloud service is how to handle data corruption, given the large volume of data and independent systems.</span></span> <span data-ttu-id="3fc1c-105">데이터 손상은 다음과 같은 이유로 인해 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3fc1c-105">Data corruption can be caused by:</span></span>

- <span data-ttu-id="3fc1c-106">응용 프로그램 또는 인프라 버그 (일부 또는 모든 응용 프로그램 상태 손상)</span><span class="sxs-lookup"><span data-stu-id="3fc1c-106">Application or infrastructure bugs, corrupting some or all of the application state</span></span>
- <span data-ttu-id="3fc1c-107">데이터가 손실 되거나 데이터를 읽을 수 없게 되는 하드웨어 문제</span><span class="sxs-lookup"><span data-stu-id="3fc1c-107">Hardware issues that result in lost data or an inability to read data</span></span>
- <span data-ttu-id="3fc1c-108">사용자 운영 오류</span><span class="sxs-lookup"><span data-stu-id="3fc1c-108">Human operational errors</span></span>
- <span data-ttu-id="3fc1c-109">악의적인 해커 및 불만을 품은 직원</span><span class="sxs-lookup"><span data-stu-id="3fc1c-109">Malicious hackers and disgruntled employees</span></span>
- <span data-ttu-id="3fc1c-110">데이터 손실을 발생 시키는 외부 서비스의 사건</span><span class="sxs-lookup"><span data-stu-id="3fc1c-110">Incidents in external services that result in some loss of data</span></span>

<span data-ttu-id="3fc1c-111">데이터 무결성이 높을수록 데이터 손상 사고가 더 적기 때문에 Microsoft는 손상 발생을 방지 하기 위해 Microsoft 365 보호 메커니즘을 기본적으로 제공 하 고 시스템 및 프로세스를 통해 데이터를 복구할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3fc1c-111">Because greater resiliency in data integrity means fewer data corruption incidents, Microsoft has built into Microsoft 365 protection mechanisms to prevent corruption from happening, as well as systems and processes that enable us to recover data if it does.</span></span> <span data-ttu-id="3fc1c-112">다음을 포함 하 여 데이터 손상에 대 한 복구 력을 늘리기 위해 엔지니어링 릴리스 프로세스의 다양 한 단계 내에 검사 및 프로세스가 존재 합니다.</span><span class="sxs-lookup"><span data-stu-id="3fc1c-112">Checks and processes exist within the various stages of the engineering release process to increase resiliency against data corruption, including:</span></span>

- <span data-ttu-id="3fc1c-113">시스템 디자인</span><span class="sxs-lookup"><span data-stu-id="3fc1c-113">System Design</span></span>
- <span data-ttu-id="3fc1c-114">코드 구성 및 구조</span><span class="sxs-lookup"><span data-stu-id="3fc1c-114">Code organization and structure</span></span>
- <span data-ttu-id="3fc1c-115">코드 검토</span><span class="sxs-lookup"><span data-stu-id="3fc1c-115">Code review</span></span>
- <span data-ttu-id="3fc1c-116">단위 테스트, 통합 테스트 및 시스템 테스트</span><span class="sxs-lookup"><span data-stu-id="3fc1c-116">Unit tests, integration tests, and system tests</span></span>
- <span data-ttu-id="3fc1c-117">여행 와이어 테스트/게이트</span><span class="sxs-lookup"><span data-stu-id="3fc1c-117">Trip wires tests/gates</span></span>

<span data-ttu-id="3fc1c-118">Microsoft 365 프로덕션 환경에서 데이터 센터 간의 피어 복제를 사용 하면 항상 모든 데이터가 포함 된 라이브 복사본을 여러 개 유지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3fc1c-118">Within Microsoft 365 production environments, peer replication between datacenters ensures that there are always multiple live copies of any data.</span></span> <span data-ttu-id="3fc1c-119">표준 이미지 및 스크립트는 손실 된 서버를 복구 하는 데 사용 되 고, 복제 된 데이터는 고객 데이터를 복원 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3fc1c-119">Standard images and scripts are used to recover lost servers, and replicated data is used to restore customer data.</span></span> <span data-ttu-id="3fc1c-120">기본 제공 되는 데이터 복구 력 검사 및 프로세스로 인해 Microsoft는 SharePoint Online의 기본 제공 복제 및 내부 코드 리포지토리 도구인 원본 서비스 센터를 사용 하 여 Microsoft 365 information system 설명서 (보안 관련 문서 포함)의 백업만 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="3fc1c-120">Because of the built-in data resiliency checks and processes, Microsoft maintains backups only of Microsoft 365 information system documentation (including security-related documentation), using built-in replication in SharePoint Online and our internal code repository tool, Source Depot.</span></span> <span data-ttu-id="3fc1c-121">시스템 설명서는 SharePoint Online에 저장 되며, 원본 서비스 센터에는 시스템 및 응용 프로그램 이미지가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3fc1c-121">System documentation is stored in SharePoint Online, and Source Depot contains system and application images.</span></span> <span data-ttu-id="3fc1c-122">SharePoint Online 및 원본 서비스는 모두 버전 관리를 사용 하며 거의 실시간으로 복제 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3fc1c-122">Both SharePoint Online and Source Depot use versioning and are replicated in near real time.</span></span>
