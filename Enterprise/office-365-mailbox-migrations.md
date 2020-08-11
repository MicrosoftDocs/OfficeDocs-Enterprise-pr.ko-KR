---
title: Microsoft 365 사서함 마이그레이션
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
description: 이 문서에는 Microsoft 365 사서함 마이그레이션에 대 한 간략 한 요약과 마이그레이션에 사용 되는 cmdlet 목록이 포함 되어 있습니다.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: c28ab1702e6a81826ce77bf0b4ef30e4d24832b4
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605570"
---
# <a name="microsoft-365-mailbox-migrations"></a><span data-ttu-id="75557-103">Microsoft 365 사서함 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="75557-103">Microsoft 365 mailbox migrations</span></span>

<span data-ttu-id="75557-104">Exchange 기반 하이브리드 배포를 사용 하는 경우 고객은 온-프레미스 Exchange 사서함을 [Exchange online](https://docs.microsoft.com/Exchange/exchange-online) 조직으로 이동 하거나 exchange online 사서함을 [exchange 온-프레미스](https://docs.microsoft.com/Exchange/exchange-server) 조직으로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75557-104">With an Exchange-based hybrid deployment, customers can choose to either move on-premises Exchange mailboxes to an [Exchange Online](https://docs.microsoft.com/Exchange/exchange-online) organization or move Exchange Online mailboxes to an [Exchange on-premises](https://docs.microsoft.com/Exchange/exchange-server) organization.</span></span> <span data-ttu-id="75557-105">마이그레이션 일괄 처리는 온-프레미스 조직과 Exchange Online 조직 간에 사서함을 이동할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="75557-105">Migration batches are used when moving mailboxes between on-premises and Exchange Online organizations.</span></span>

<span data-ttu-id="75557-106">고객은 다음 cmdlet을 사용 하 여 사서함 마이그레이션에 대 한 통계 및 기타 정보를 검토할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75557-106">Customers can review statistics and other information about mailbox migrations with the following cmdlets:</span></span>

- <span data-ttu-id="75557-107">[Get-moverequeststatistics](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/Get-MoveRequestStatistics?view=exchange-ps): 상태, 사서함 크기, 보관 사서함 크기 및 완료율이 포함 된 사용자 사서함에 대 한 기본 통계를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="75557-107">[Get-MoveRequestStatistics](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/Get-MoveRequestStatistics?view=exchange-ps): Provides default statistics for a user mailbox, which includes the status, mailbox size, archive mailbox size, and percentage complete.</span></span>
- <span data-ttu-id="75557-108">[Get-mailbox](https://docs.microsoft.com/powershell/module/exchange/mailboxes/Get-Mailbox?view=exchange-ps
): 조직의 사서함 개체 및 특성에 대 한 요약 목록을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="75557-108">[Get-Mailbox](https://docs.microsoft.com/powershell/module/exchange/mailboxes/Get-Mailbox?view=exchange-ps
): Provides a summary list of mailbox objects and attributes in the organization.</span></span>
- <span data-ttu-id="75557-109">[Get-Recipient](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Get-Recipient?view=exchange-ps): 사서함, 메일 사용자, 연락처, 메일 그룹 등의 기존 메일 사용 가능 개체 목록을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="75557-109">[Get-Recipient](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Get-Recipient?view=exchange-ps): Provides a list of existing mail-enabled objects such as mailboxes, mail users, contacts, and distribution groups.</span></span>
- <span data-ttu-id="75557-110">[New-moverequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/Get-MoveRequest?view=exchange-ps): 진행 중인 사서함 마이그레이션의 자세한 상태를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="75557-110">[Get-MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/Get-MoveRequest?view=exchange-ps): Provides a detailed status of an ongoing mailbox migration.</span></span>
- <span data-ttu-id="75557-111">[Get-migrationuser](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/Get-MigrationUser?view=exchange-ps): 사서함 이동 및 마이그레이션 사용자에 대 한 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="75557-111">[Get-MigrationUser](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/Get-MigrationUser?view=exchange-ps): Provides information about the mailbox move and migration users.</span></span>
- <span data-ttu-id="75557-112">[New-migrationbatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/Get-MigrationBatch?view=exchange-ps): 현재 마이그레이션 일괄 처리의 상태에 대 한 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="75557-112">[Get-MigrationBatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/Get-MigrationBatch?view=exchange-ps): Provides information on the status of current migration batch.</span></span>
- <span data-ttu-id="75557-113">[Get-migrationuserstatistics](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/Get-MigrationUserStatistics?view=exchange-ps): 특정 사용자의 마이그레이션 상태에 대 한 자세한 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="75557-113">[Get-MigrationUserStatistics](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/Get-MigrationUserStatistics?view=exchange-ps): Provides detailed information about the migration status for a specific user.</span></span>
- <span data-ttu-id="75557-114">[Get-mailboxstatistics](https://docs.microsoft.com/powershell/module/exchange/mailboxes/Get-MailboxStatistics?view=exchange-ps): 크기, 메시지 수, 마지막으로 액세스 한 시간 등 사서함에 대 한 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="75557-114">[Get-MailboxStatistics](https://docs.microsoft.com/powershell/module/exchange/mailboxes/Get-MailboxStatistics?view=exchange-ps): Provides information about mailboxes, such as size, the number of messages, and the last accessed time.</span></span>

<span data-ttu-id="75557-115">Cmdlet에 대 한 자세한 내용은 [Exchange Online의 이동 및 마이그레이션 cmdlet](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="75557-115">For more information about cmdlets, see [Move and Migration cmdlets in Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps).</span></span>
