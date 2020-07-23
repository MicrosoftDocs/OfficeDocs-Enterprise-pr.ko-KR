---
title: PowerShell을 사용 하 여 Microsoft 365 관리
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- O365ITProTrain
- Ent_Office_Other
ms.assetid: 932d57c0-1520-4f0f-8ec9-9966d646480f
description: '요약: PowerShell을 사용 하 여 Microsoft 365 사용자 및 라이선스, 비즈니스용 Skype Online, SharePoint Online, Exchange Online, 보안 & 준수 센터를 관리 하는 방법을 알아봅니다.'
ms.openlocfilehash: 741ec15a78db9393e11ba6d06720457e20741581
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230514"
---
# <a name="manage-microsoft-365-with-powershell"></a><span data-ttu-id="c4a7d-103">PowerShell을 사용 하 여 Microsoft 365 관리</span><span class="sxs-lookup"><span data-stu-id="c4a7d-103">Manage Microsoft 365 with PowerShell</span></span>

<span data-ttu-id="c4a7d-104">*이 문서는 Microsoft 365 Enterprise 및 Office 365 Enterprise에 모두 적용 됩니다.*</span><span class="sxs-lookup"><span data-stu-id="c4a7d-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="c4a7d-105">Microsoft 365 용 PowerShell은 Microsoft 365 관리 센터를 보완 하는 강력한 관리 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="c4a7d-105">PowerShell for Microsoft 365 is a powerful management tool that complements the Microsoft 365 admin center.</span></span> <span data-ttu-id="c4a7d-106">예를 들어 PowerShell automation을 사용 하 여 여러 사용자 계정 및 라이선스를 보다 신속 하 게 관리 하 고 보고서를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4a7d-106">For example, you can use PowerShell automation to more quickly manage multiple user accounts and licenses and create reports.</span></span> <span data-ttu-id="c4a7d-107">Microsoft 365 사용자 및 라이선스, 비즈니스용 Skype Online, SharePoint Online, Exchange Online, 보안 & 준수 센터에 PowerShell을 사용 하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="c4a7d-107">Learn how to use PowerShell for Microsoft 365 users and licenses, Skype for Business Online, SharePoint Online, Exchange Online, and the Security & Compliance Center.</span></span>
  
<span data-ttu-id="c4a7d-108">필요에 따라 항목을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c4a7d-108">Select the topic based on your needs:</span></span>
  
- [<span data-ttu-id="c4a7d-109">시작</span><span class="sxs-lookup"><span data-stu-id="c4a7d-109">Get started</span></span>](getting-started-with-office-365-powershell.md)

    <span data-ttu-id="c4a7d-110">Microsoft 365 용 PowerShell에 익숙하고 microsoft 365 모듈을 설치 하 고 Microsoft 365 구독에 연결 하려면 여기에서 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4a7d-110">Start here if you are not familiar with PowerShell for Microsoft 365 and want to install the Microsoft 365 modules and connect to your Microsoft 365 subscription.</span></span>

- [<span data-ttu-id="c4a7d-111">사용자 계정, 라이선스 및 그룹</span><span class="sxs-lookup"><span data-stu-id="c4a7d-111">User accounts, licenses, and groups</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)

    <span data-ttu-id="c4a7d-112">Microsoft 365 모듈을 설치 했으며 자동화 명령을 사용 하 여 사용자 계정, 라이선스 및 그룹을 관리 하는 방법에 대해 자세히 알아보려면 여기에서 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4a7d-112">Start here if you have installed the Microsoft 365 modules and want to learn more about using automation commands to manage user accounts, licenses, and groups.</span></span>

- [<span data-ttu-id="c4a7d-113">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="c4a7d-113">SharePoint Online</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/manage-sharepoint-online-with-office-365-powershell)

    <span data-ttu-id="c4a7d-114">Microsoft 365 모듈을 설치 했으며 자동화 명령을 사용 하 여 SharePoint Online의 관리를 수행 하려면 여기에서 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4a7d-114">Start here if you have installed the Microsoft 365 modules and want to use automation commands to perform management of SharePoint Online.</span></span>

- [<span data-ttu-id="c4a7d-115">Exchange Online PowerShell</span><span class="sxs-lookup"><span data-stu-id="c4a7d-115">Exchange Online PowerShell</span></span>](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell)

    <span data-ttu-id="c4a7d-116">자동화 명령을 사용하여 Exchange Online을 관리하려면 여기에서 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="c4a7d-116">Start here if you want to use automation commands to manage Exchange Online.</span></span>

- [<span data-ttu-id="c4a7d-117">전자 메일 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="c4a7d-117">Email migration</span></span>](use-powershell-for-email-migration-to-office-365.md)

    <span data-ttu-id="c4a7d-118">PowerShell 365 모듈을 설치 했으며 기존 시스템에서 전자 메일을 마이그레이션하려면 여기에서 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4a7d-118">Start here if you have installed the PowerShell 365 modules and want to migrate your email from existing systems.</span></span>

- [<span data-ttu-id="c4a7d-119">보안 및 준수 센터</span><span class="sxs-lookup"><span data-stu-id="c4a7d-119">Security & Compliance Center</span></span>](https://docs.microsoft.com/powershell/exchange/office-365-scc/office-365-scc-powershell)

    <span data-ttu-id="c4a7d-120">자동화 명령을 사용하여 보안 및 준수 센터를 관리하려면 여기에서 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="c4a7d-120">Start here if you want to use automation commands to manage the Security & Compliance Center.</span></span>

- [<span data-ttu-id="c4a7d-121">DAP (위임 된 액세스 권한) 파트너</span><span class="sxs-lookup"><span data-stu-id="c4a7d-121">Delegated Access Permissions (DAP) partners</span></span>](manage-office-365-with-windows-powershell-for-delegated-access-permissions-dap-p.md)

    <span data-ttu-id="c4a7d-122">배포 및 CSP (클라우드 솔루션 공급자) 파트너를 사용 하 여 Microsoft 365 고객 테 넌 트를 관리 하려면 여기에서 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4a7d-122">Start here if you want to use Syndication and Cloud Solution Provider (CSP) partners to manage your Microsoft 365 customer tenants.</span></span>

- [<span data-ttu-id="c4a7d-123">비즈니스용 Skype Online</span><span class="sxs-lookup"><span data-stu-id="c4a7d-123">Skype for Business Online</span></span>](manage-skype-for-business-online-with-office-365-powershell.md)

    <span data-ttu-id="c4a7d-124">PowerShell 모듈을 설치 했으며 비즈니스용 Skype Online의 관리를 수행 하려면 여기에서 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4a7d-124">Start here if you have installed the PowerShell modules and want to perform management of Skype for Business Online.</span></span>
