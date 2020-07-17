---
title: Microsoft 365 리소스 제한
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
description: '요약: Microsoft 365 내의 다양 한 응용 프로그램에 대 한 리소스 제한에 대해 설명 합니다.'
ms.openlocfilehash: c3f10be1e64cb5d355d319a603cc0c1d2f238dc7
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "44997855"
---
# <a name="resource-limits"></a><span data-ttu-id="77cf5-103">리소스 제한 사항</span><span class="sxs-lookup"><span data-stu-id="77cf5-103">Resource Limits</span></span>

<span data-ttu-id="77cf5-104">리소스 제한은 할당량 (제한) 및 제한을 사용 하 여 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="77cf5-104">Resource limits are enforced using quotas (limits) and throttling.</span></span> <span data-ttu-id="77cf5-105">Azure Active Directory (Azure AD) 및 개별 Microsoft 365 서비스는 둘 다 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="77cf5-105">Azure Active Directory (Azure AD) and the individual Microsoft 365 services use both.</span></span> <span data-ttu-id="77cf5-106">제한은 새로운 기능이 추가 됨에 따라 서비스에 따라 달라 지 며 시간이 지나면서 변경 됩니다.</span><span class="sxs-lookup"><span data-stu-id="77cf5-106">Limits are service-specific and change over time as new capabilities are added.</span></span> <span data-ttu-id="77cf5-107">다양 한 서비스에 대 한 현재 제한 사항에 대 한 자세한 내용은 다음 항목을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="77cf5-107">For details on the current limits for the various services, see the following topics:</span></span>

- [<span data-ttu-id="77cf5-108">Azure AD 서비스 제한 및 제한 사항</span><span class="sxs-lookup"><span data-stu-id="77cf5-108">Azure AD service limits and restrictions</span></span>](https://docs.microsoft.com/azure/azure-resource-manager/management/azure-subscription-service-limits)
- [<span data-ttu-id="77cf5-109">Exchange Online 제한</span><span class="sxs-lookup"><span data-stu-id="77cf5-109">Exchange Online Limits</span></span>](https://technet.microsoft.com/library/exchange-online-limits.aspx)
- [<span data-ttu-id="77cf5-110">Exchange Online Protection 제한</span><span class="sxs-lookup"><span data-stu-id="77cf5-110">Exchange Online Protection Limits</span></span>](https://technet.microsoft.com/library/exchange-online-protection-limits.aspx)
- [<span data-ttu-id="77cf5-111">SharePoint Online 소프트웨어 경계 및 제한 사항</span><span class="sxs-lookup"><span data-stu-id="77cf5-111">SharePoint Online software boundaries and limits</span></span>](https://support.office.com/article/SharePoint-Online-software-boundaries-and-limits-8F34FF47-B749-408B-ABC0-B605E1F6D498)
- [<span data-ttu-id="77cf5-112">비즈니스용 Skype 제한</span><span class="sxs-lookup"><span data-stu-id="77cf5-112">Skype for Business Limits</span></span>](https://technet.microsoft.com/library/skype-for-business-online-limits.aspx)
- [<span data-ttu-id="77cf5-113">Yammer REST API 및 속도 제한</span><span class="sxs-lookup"><span data-stu-id="77cf5-113">Yammer REST API and Rate Limits</span></span>](https://developer.yammer.com/docs/rest-api-rate-limits)
- [<span data-ttu-id="77cf5-114">Sway의 파일 크기 제한</span><span class="sxs-lookup"><span data-stu-id="77cf5-114">File Size Limits in Sway</span></span>](https://support.office.com/article/File-size-limits-in-Sway-4db21bc6-b42b-499f-9272-66e089db109f)

<span data-ttu-id="77cf5-115">이러한 제한 외에도 다양 한 제한 메커니즘이 Azure AD 및 Microsoft 365에서 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="77cf5-115">In addition to these limits, several throttling mechanisms are used throughout Azure AD and Microsoft 365.</span></span> <span data-ttu-id="77cf5-116">Microsoft 데이터 센터의 네트워크 리소스가 서비스를 사용 하는 광범위 한 고객 집합에 맞게 최적화 되어 있는 경우 서비스 내의 제한이 특히 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="77cf5-116">Throttling within the service is especially important, given that network resources in Microsoft's datacenters are optimized for the broad set of customers that use the services.</span></span> <span data-ttu-id="77cf5-117">제한 메커니즘은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="77cf5-117">Throttling mechanisms include:</span></span>

- <span data-ttu-id="77cf5-118">Azure AD 및 Microsoft 365 기능 사용자 수준 제한은 단일 사용자가 수행할 수 있는 트랜잭션 수 또는 스크립트 또는 코드에의 한 동시 통화를 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="77cf5-118">Azure AD and Microsoft 365 feature user-level throttling, which limit the number of transactions or concurrent calls (by script or code) that can be performed by a single user.</span></span>
- <span data-ttu-id="77cf5-119">기본 PowerShell 제한 정책이 테 넌 트를 만들 때 각 테 넌 트에 할당 됩니다.</span><span class="sxs-lookup"><span data-stu-id="77cf5-119">A default PowerShell throttling policy is assigned to each tenant at tenant creation.</span></span> <span data-ttu-id="77cf5-120">이러한 설정은 단일 관리자가 열 수 있는 동시 PowerShell 세션의 최대 수와 같은 다른 항목에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="77cf5-120">These settings affect other items, such as the maximum number of simultaneous PowerShell sessions that can be opened by a single administrator.</span></span>
- <span data-ttu-id="77cf5-121">각 Exchange Online 고객에 게 EWS 클라이언트 작업에 맞게 조정 된 기본 EWS (Exchange 웹 서비스) 정책 및 모든 Outlook 클라이언트에 적용 되는 제한 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77cf5-121">Each Exchange Online customer has a default Exchange Web Services (EWS) policy that is tuned for EWS client operations, and throttling that applies to all Outlook clients.</span></span>
