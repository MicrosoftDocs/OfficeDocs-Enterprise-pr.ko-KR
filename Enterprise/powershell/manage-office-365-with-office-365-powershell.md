---
title: Office 365 PowerShell로 Office 365 관리
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/06/2019
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- O365ITProTrain
- Ent_Office_Other
ms.assetid: 932d57c0-1520-4f0f-8ec9-9966d646480f
description: '요약: Office 365 사용자 및 라이선스, 비즈니스용 Skype Online, SharePoint Online, Exchange Online, Office 365 보안 및 준수 센터에 Office 365 PowerShell을 사용하는 방법을 알아봅니다.'
ms.openlocfilehash: a1d71dddd26122fe925762228e63fedd6a4ba702
ms.sourcegitcommit: 77b8fd702d3a1010d3906d4024d272ad2097f54f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2019
ms.locfileid: "39962495"
---
# <a name="manage-office-365-with-office-365-powershell"></a><span data-ttu-id="a2a14-103">Office 365 PowerShell로 Office 365 관리</span><span class="sxs-lookup"><span data-stu-id="a2a14-103">Manage Office 365 with Office 365 PowerShell</span></span>

<span data-ttu-id="a2a14-104">*이 문서는 Office 365 및 Microsoft 365에 모두 적용 됩니다.*</span><span class="sxs-lookup"><span data-stu-id="a2a14-104">*This article applies to both Office 365 and Microsoft 365.*</span></span>

<span data-ttu-id="a2a14-105">Office 365 PowerShell은 Microsoft 365 관리 센터를 보완 하는 강력한 관리 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="a2a14-105">Office 365 PowerShell is a powerful management tool that complements the Microsoft 365 admin center.</span></span> <span data-ttu-id="a2a14-106">예를 들어 Office 365 PowerShell 자동화를 사용 하 여 여러 사용자 계정 및 라이선스를 보다 신속 하 게 관리 하 고 보고서를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2a14-106">For example, you can use Office 365 PowerShell automation to more quickly manage multiple user accounts and licenses and create reports.</span></span> <span data-ttu-id="a2a14-107">Office 365 사용자 및 라이선스, 비즈니스용 Skype Online, SharePoint Online, Exchange Online, Office 365 Security & 준수 센터에 Office 365 PowerShell을 사용 하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="a2a14-107">Learn how to use Office 365 PowerShell with Office 365 users and licenses, Skype for Business Online, SharePoint Online, Exchange Online, and the Office 365 Security & Compliance Center.</span></span>
  
<span data-ttu-id="a2a14-108">필요에 따라 항목을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a2a14-108">Select the topic based on your needs:</span></span>
  
- [<span data-ttu-id="a2a14-109">시작</span><span class="sxs-lookup"><span data-stu-id="a2a14-109">Get started</span></span>](getting-started-with-office-365-powershell.md)

    <span data-ttu-id="a2a14-110">Office 365 PowerShell에 익숙하고 office 365 PowerShell 모듈을 설치 하 고 Office 365 구독에 연결 하려면 여기에서 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2a14-110">Start here if you are not familiar with Office 365 PowerShell and want to install the Office 365 PowerShell modules and connect to your Office 365 subscription.</span></span>

- [<span data-ttu-id="a2a14-111">사용자 계정, 라이선스 및 그룹</span><span class="sxs-lookup"><span data-stu-id="a2a14-111">User accounts, licenses, and groups</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)

    <span data-ttu-id="a2a14-112">Office 365 PowerShell 모듈을 설치 했으며 자동화 명령을 사용 하 여 사용자 계정, 라이선스 및 그룹을 관리 하는 방법에 대해 자세히 알아보려면 여기에서 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2a14-112">Start here if you have installed the Office 365 PowerShell modules and want to learn more about using automation commands to manage user accounts, licenses, and groups.</span></span>

- [<span data-ttu-id="a2a14-113">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="a2a14-113">SharePoint Online</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/manage-sharepoint-online-with-office-365-powershell)

    <span data-ttu-id="a2a14-114">Office 365 PowerShell 모듈을 설치했으며 자동화 명령을 사용하여 SharePoint Online의 관리를 수행하려면 여기에서 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="a2a14-114">Start here if you have installed the Office 365 PowerShell modules and want to use automation commands to perform management of SharePoint Online.</span></span>

- [<span data-ttu-id="a2a14-115">Exchange Online PowerShell</span><span class="sxs-lookup"><span data-stu-id="a2a14-115">Exchange Online PowerShell</span></span>](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell)

    <span data-ttu-id="a2a14-116">자동화 명령을 사용하여 Exchange Online을 관리하려면 여기에서 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="a2a14-116">Start here if you want to use automation commands to manage Exchange Online.</span></span>

- [<span data-ttu-id="a2a14-117">Office 365로의 전자 메일 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="a2a14-117">Email migration to Office 365</span></span>](use-powershell-for-email-migration-to-office-365.md)

    <span data-ttu-id="a2a14-118">Office 365 PowerShell 모듈을 설치했으며 기존 시스템에서 전자 메일을 마이그레이션하려면 여기에서 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="a2a14-118">Start here if you have installed the Office 365 PowerShell modules and want to migrate your email from existing systems.</span></span>

- [<span data-ttu-id="a2a14-119">보안 & 준수 센터</span><span class="sxs-lookup"><span data-stu-id="a2a14-119">Security & Compliance Center</span></span>](https://docs.microsoft.com/powershell/exchange/office-365-scc/office-365-scc-powershell)

    <span data-ttu-id="a2a14-120">자동화 명령을 사용하여 보안 및 준수 센터를 관리하려면 여기에서 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="a2a14-120">Start here if you want to use automation commands to manage the Security & Compliance Center.</span></span>

- [<span data-ttu-id="a2a14-121">DAP (위임 된 액세스 권한) 파트너</span><span class="sxs-lookup"><span data-stu-id="a2a14-121">Delegated Access Permissions (DAP) partners</span></span>](manage-office-365-with-windows-powershell-for-delegated-access-permissions-dap-p.md)

    <span data-ttu-id="a2a14-122">신디케이션 및 CSP(클라우드 솔루션 공급자) 파트너를 사용하여 Office 365 고객 테넌트를 관리하려면 여기에서 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="a2a14-122">Start here if you want to use Syndication and Cloud Solution Provider (CSP) partners to manage your Office 365 customer tenants.</span></span>

- [<span data-ttu-id="a2a14-123">비즈니스용 Skype Online</span><span class="sxs-lookup"><span data-stu-id="a2a14-123">Skype for Business Online</span></span>](manage-skype-for-business-online-with-office-365-powershell.md)

    <span data-ttu-id="a2a14-124">Office 365 PowerShell 모듈을 설치했으며 비즈니스용 Skype Online의 관리를 수행하려면 여기에서 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="a2a14-124">Start here if you have installed the Office 365 PowerShell modules and want to perform management of Skype for Business Online.</span></span>
