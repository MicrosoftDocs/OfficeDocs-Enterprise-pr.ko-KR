---
title: Exchange Multi-Geo
ms.reviewer: adwood
ms.author: chrisda
author: chrisda
manager: serdars
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: ''
localization_priority: Priority
description: Exchange Onlinedl 다중 위치 기능에 대해 알아봅니다.
ms.openlocfilehash: 27b636e1fb7f209a425a070f8024a1cdd461f59b
ms.sourcegitcommit: 1c3aa0654336acec14098241f785ea1d8c6caf50
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/21/2020
ms.locfileid: "42890550"
---
# <a name="multi-geo-capabilities-in-exchange-online"></a><span data-ttu-id="988b6-103">Exchange Online의 다중 위치 기능</span><span class="sxs-lookup"><span data-stu-id="988b6-103">Multi-Geo Capabilities in Exchange Online</span></span>

<span data-ttu-id="988b6-104">다중 위치 환경에서, 사용자별 기준으로 Exchange Online 사서함 콘텐츠(보관 중인 데이터)의 위치를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="988b6-104">In a multi-geo environment, you can select the location of Exchange Online mailbox content (data at rest) on a per-user basis.</span></span>

<span data-ttu-id="988b6-105">다음과 같은 방법으로 위성의 지리적 위치에서 사서함을 배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="988b6-105">You can place mailboxes in satellite geo locations by:</span></span>

- <span data-ttu-id="988b6-106">위성의 지리적 위치에서 새 Exchange Online 사서함을 바로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="988b6-106">Creating a new Exchange Online mailbox directly in a satellite geo location.</span></span>

- <span data-ttu-id="988b6-107">사용자의 기본 설정된 데이터 위치를 변경하 여 기존 Exchange Online 사서함을 위성의 지리적 위치로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="988b6-107">Moving an existing Exchange Online mailbox to a satellite geo location by changing the user's preferred data location.</span></span>

- <span data-ttu-id="988b6-108">온-프레미스 Exchange 조직의 사서함을 위성의 지리적 위치로 바로 온보딩합니다.</span><span class="sxs-lookup"><span data-stu-id="988b6-108">Onboarding a mailbox from an on-premises Exchange organization directly into a satellite geo location.</span></span>

## <a name="mailbox-placement-and-moves"></a><span data-ttu-id="988b6-109">사서함 배치 및 이동</span><span class="sxs-lookup"><span data-stu-id="988b6-109">Mailbox placement and moves</span></span>

<span data-ttu-id="988b6-110">Microsoft에서 필수 다중 위치 구성 단계를 완료한 후, Exchange Online에서 Azure AD의 사용자 개체에 있는 **PreferredDataLocation** 특성을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="988b6-110">After Microsoft completes the prerequisite multi-geo configuration steps, Exchange Online will honor the **PreferredDataLocation** attribute on user objects in Azure AD.</span></span>

<span data-ttu-id="988b6-111">Exchange Online에서 Azure AD의 **PreferredDataLocation** 속성을 Exchange Online 디렉터리 서비스의 **MailboxRegion** 속성으로 동기화합니다.</span><span class="sxs-lookup"><span data-stu-id="988b6-111">Exchange Online synchronizes the **PreferredDataLocation** property from Azure AD into the **MailboxRegion** property in the Exchange Online directory service.</span></span> <span data-ttu-id="988b6-112">**MailboxRegion**의 값이 사용자 사서함 및 관련된 보관 사서함이 위치하는 지리적 위치를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="988b6-112">The value of **MailboxRegion** determines the geo location where user mailboxes and any associated archive mailboxes will be placed.</span></span> <span data-ttu-id="988b6-113">사용자의 기본 사서함과 보관 사서함이 여러 지리적 위치에 있도록 구성할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="988b6-113">It is not possible to configure a user's primary mailbox and archive mailboxes to reside in different geo locations.</span></span> <span data-ttu-id="988b6-114">사용자 개체당 하나의 지리적 위치만 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="988b6-114">Only one geo location may be configured per user object.</span></span>

- <span data-ttu-id="988b6-115">**PreferredDataLocation**이 기존 사서함을 사용하는 사용자에게 구성된 경우, 사서함이 재배치 큐에 저장되고 특정 지리적 위치로 자동으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="988b6-115">When **PreferredDataLocation** is configured on a user with an existing mailbox, the mailbox will be put into a relocation queue and automatically moved to the specified geo location.</span></span>

- <span data-ttu-id="988b6-116">**PreferredDataLocation**이 기존 사서함이 없는 사용자에게 구성된 경우, 사서함을 프로비저닝하면 사서함이 지정된 지리적 위치로 프로비저닝됩니다.</span><span class="sxs-lookup"><span data-stu-id="988b6-116">When **PreferredDataLocation** is configured on a user without an existing mailbox, when you provision the mailbox, it will be provisioned into the specified geo location.</span></span>

- <span data-ttu-id="988b6-117">**PreferredDataLocation**이 사용자에게 지정되지 않은 경우, 사서함을 프로비저닝하면 사서함이 중앙 지리적 위치로 프로비저닝됩니다.</span><span class="sxs-lookup"><span data-stu-id="988b6-117">When **PreferredDataLocation** is not specified on a user, when you provision the mailbox, it will be provisioned in the central geo location.</span></span>

- <span data-ttu-id="988b6-118">**PreferredDataLocation** 코드가 틀린 경우(예: NAM 대신 NAN 입력), 사서함이 중앙 지리적 위치에서 프로비저닝됩니다.</span><span class="sxs-lookup"><span data-stu-id="988b6-118">If the **PreferredDataLocation** code is incorrect (e.g. a type of NAN instead of NAM), the mailbox will be provisioned in the central geo location.</span></span>

<span data-ttu-id="988b6-119">**참고**: 다중 위치 기능 및 비즈니스용 Skype에서 지리적으로 호스팅된 모임은 사용자 개체에서 **PreferredDataLocation** 속성을 사용하여 서비스를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="988b6-119">**Note**: Multi-geo capabilities and Skype for Business Online regionally hosted meetings both use the **PreferredDataLocation** property on user objects to locate services.</span></span> <span data-ttu-id="988b6-120">지리적으로 호스팅된 모임에 대해 사용자 개체에서 **PreferredDataLocation** 값을 구성하는 경우, Office 365 테넌트에서 다중 지역이 활성화된 후 해당 사용자의 사서함이 지정된 지리적 위치로 자동으로 이동합니다. </span><span class="sxs-lookup"><span data-stu-id="988b6-120">If you configure **PreferredDataLocation** values on user objects for regionally hosted meetings, the mailbox for those users will be automatically moved to the specified geo location after multi-geo is enabled on the Office 365 tenant.</span></span>

## <a name="feature-limitations-for-multi-geo-in-exchange-online"></a><span data-ttu-id="988b6-121">Exchange Online의 다중 지역에 대한 기능 제한 사항</span><span class="sxs-lookup"><span data-stu-id="988b6-121">Feature limitations for multi-geo in Exchange Online</span></span>

- <span data-ttu-id="988b6-122">EAC(Exchange 관리 센터)에서 사용할 수 있는 보안 및 준수 기능(예: 감사 및 eDiscovery)을 다중 지역 조직에서는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="988b6-122">Security and compliance features (for example, auditing and eDiscovery) that are available in the Exchange admin center (EAC) aren't available in multi-geo organizations.</span></span> <span data-ttu-id="988b6-123">대신, [Office 365 보안 및 준수 센터](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8)를 사용하여 보안 및 준수 기능을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="988b6-123">Instead, you need to use the [Office 365 Security & Compliance Center](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8) to configure security and compliance features.</span></span>

- <span data-ttu-id="988b6-124">Mac용 Outlook 사용자는 사서함을 새 지리적 위치로 이동하는 동안 온라인 보관함 폴더에 대한 액세스가 일시적으로 중단될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="988b6-124">Outlook for Mac users may experience a temporary loss of access to their Online Archive folder while you move their mailbox to a new geo location.</span></span> <span data-ttu-id="988b6-125">교차 지역 사서함 이동이 다른 시간에 완료될 수 있으므로, 이 조건은 사용자의 기본 및 보관 사서함이 다른 지리적 위치에 있을 때 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="988b6-125">This condition occurs when the user's the primary and archive mailboxes are in different geo locations, because cross-geo mailbox moves may complete at different times.</span></span>

- <span data-ttu-id="988b6-126">웹용 Outlook(이전의 Outlook Web App 또는 OWA)에서 지리적 위치를 넘어서 *사서함 폴더*를 공유할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="988b6-126">Users can't share *mailbox folders* across geo locations in Outlook on the web (formerly known as Outlook Web App or OWA).</span></span> <span data-ttu-id="988b6-127">예를 들어, 유럽 연합에 있는 사용자는 웹용 Outlook을 사용하여 미국에 있는 사서함에서 공유 폴더를 열 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="988b6-127">For example, a user in the European Union can't use Outlook on the web to open a shared folder in a mailbox that's located in the United States.</span></span> <span data-ttu-id="988b6-128">그러나 웹용 Outlook 사용자는 [Outlook Web App의 개별 브라우저 창에서 다른 사용자의 사서함 열기](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362)에 설명된 대로 별도의 브라우저 창을 사용하여 다른 지리적 위치에서 *다른 사서함*을 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="988b6-128">However, Outlook on the Web users can open *other mailboxes* in different geo locations by using a separate browser window as described in [Open another person's mailbox in a separate browser window in Outlook Web App](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362).</span></span>

  <span data-ttu-id="988b6-129">**참고**: 교차 지역 사서함 폴더 공유가 Windows의 Outlook에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="988b6-129">**Note**: Cross-geo mailbox folder sharing is supported in Outlook on Windows.</span></span>

- <span data-ttu-id="988b6-130">공용 폴더는 다중 지역 조직에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="988b6-130">Public folders are supported in multi-geo organizations.</span></span> <span data-ttu-id="988b6-131">그러나 공용 폴더가 중앙 지리적 위치에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="988b6-131">However, the public folders must remain in the central geo location.</span></span> <span data-ttu-id="988b6-132">공용 폴더를 위성의 지리적 위치로 이동할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="988b6-132">You can't move public folders to satellite geo locations.</span></span>

- <span data-ttu-id="988b6-133">다중 지리적 환경에서는 지역 횡단 사서함 감사가 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="988b6-133">In a multi-geo environment, cross-geo mailbox auditing is not supported.</span></span> <span data-ttu-id="988b6-134">예를 들어 사용자가 다른 지리적 위치에서 공유 사서함에 액세스할 수 있는 권한을 할당받더라도 그 사용자가 수행한 사서함 작업이 공유 사서함의 사서함 감사 로그에 기록되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="988b6-134">For example, if a user is assigned permissions to access a shared mailbox in a different geo location, mailbox actions performed by that user are not logged in the mailbox audit log of the shared mailbox.</span></span> <span data-ttu-id="988b6-135">자세한 내용은 [사서함 감사 관리](https://docs.microsoft.com/microsoft-365/compliance/enable-mailbox-auditing?view=o365-worldwide)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="988b6-135">For more information, see [Manage mailbox auditing](https://docs.microsoft.com/microsoft-365/compliance/enable-mailbox-auditing?view=o365-worldwide).</span></span>
