---
title: Office 365 SharePoint Online 데이터 삭제
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
description: SharePoint Online의 데이터 삭제에 대 한 설명
ms.openlocfilehash: 44b05ce6c028e79e489a94157f264fcedd63ea1a
ms.sourcegitcommit: 9eb68633728cc78e9906dab222edbf9977b17e21
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2019
ms.locfileid: "38035478"
---
# <a name="sharepoint-online-data-deletion-in-office-365"></a><span data-ttu-id="b6433-103">Office 365에서 SharePoint Online 데이터 삭제</span><span class="sxs-lookup"><span data-stu-id="b6433-103">SharePoint Online Data Deletion in Office 365</span></span>

<span data-ttu-id="b6433-104">SharePoint Online은 개체를 응용 프로그램 데이터베이스 내에서 추상화 된 코드로 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6433-104">SharePoint Online stores objects as abstracted code within application databases.</span></span> <span data-ttu-id="b6433-105">사용자가 SharePoint Online에 파일을 업로드 하면 해당 파일이 분해 되어 응용 프로그램 코드로 변환 되어 여러 데이터베이스에 걸쳐 여러 테이블에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6433-105">When a user uploads a file to SharePoint Online, that file is disassembled and translated into application code and stored in multiple tables across multiple databases.</span></span> <span data-ttu-id="b6433-106">SharePoint Online에서 고객이 업로드 하는 모든 콘텐츠는 청크, 암호화 (여러 AES 256 비트 키 사용 가능)로 분할 되 고 데이터 센터 전체에 분산 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6433-106">In SharePoint Online, all content that a customer uploads is broken into chunks, encrypted (potentially with multiple AES 256-bit keys), and distributed across the datacenter.</span></span> <span data-ttu-id="b6433-107">청크 및 암호화 프로세스에 대 한 구체적인 정보는 [Microsoft 클라우드에서 암호화](https://docs.microsoft.com/microsoft-365/compliance/office-365-encryption-in-the-microsoft-cloud-overview)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b6433-107">For specific details about the chunking and encryption process, see [Encryption in the Microsoft Cloud](https://docs.microsoft.com/microsoft-365/compliance/office-365-encryption-in-the-microsoft-cloud-overview).</span></span> 

<span data-ttu-id="b6433-108">SharePoint Online에서 항목은 원래 위치에서 삭제 한 시간부터 93 일 동안 보존 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6433-108">In SharePoint Online, items are retained for 93 days from the time you delete them from their original location.</span></span> <span data-ttu-id="b6433-109">일부 사용자가 휴지통에서 삭제 한 경우를 제외 하 고는 전체 시간으로 사이트 휴지통에 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6433-109">They stay in the site Recycle Bin the entire time, unless someone deletes them from there or empties that Recycle Bin.</span></span> <span data-ttu-id="b6433-110">이 경우 항목은 나머지 93 일 동안 유지 되는 사이트 모음 휴지통으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6433-110">In that case, the items go to the site collection Recycle Bin, where they stay for the remainder of the 93 days.</span></span> <span data-ttu-id="b6433-111">삭제 된 항목을 복원 하는 방법에 대 한 자세한 내용은 [SharePoint 사이트의 휴지통에서 항목 복원](https://support.office.com/article/6df466b6-55f2-4898-8d6e-c0dff851a0be#ID0EAADAAA=Online
) 및 [사이트 모음 휴지통에서 삭제 된 항목 복원을](https://support.office.com/article/5fa924ee-16d7-487b-9a0a-021b9062d14b)참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="b6433-111">For info about restoring deleted items, see [Restore items in the Recycle Bin of a SharePoint site](https://support.office.com/article/6df466b6-55f2-4898-8d6e-c0dff851a0be#ID0EAADAAA=Online
) and [Restore deleted items from the site collection recycle bin](https://support.office.com/article/5fa924ee-16d7-487b-9a0a-021b9062d14b).</span></span> <span data-ttu-id="b6433-112">휴지통 보존 시간은 SharePoint Online에서 구성할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b6433-112">The Recycle Bin retention time is not configurable in SharePoint Online.</span></span>

<span data-ttu-id="b6433-113">사이트 모음을 삭제 하면 모음에 있는 사이트의 계층 구조와 모든 콘텐츠가 삭제 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6433-113">When you delete a site collection, you're also deleting the hierarchy of sites in the collection, and all content within them:</span></span>

- <span data-ttu-id="b6433-114">문서 및 문서 라이브러리</span><span class="sxs-lookup"><span data-stu-id="b6433-114">Documents and document libraries</span></span>
- <span data-ttu-id="b6433-115">목록 및 목록 데이터</span><span class="sxs-lookup"><span data-stu-id="b6433-115">Lists and list data</span></span>
- <span data-ttu-id="b6433-116">사이트 구성 설정</span><span class="sxs-lookup"><span data-stu-id="b6433-116">Site configuration settings</span></span>
- <span data-ttu-id="b6433-117">사이트나 해당 사이트와 관련 된 역할 및 보안 정보</span><span class="sxs-lookup"><span data-stu-id="b6433-117">Role and security information that is related to the site or its subsites</span></span>
- <span data-ttu-id="b6433-118">최상위 웹 사이트, 해당 콘텐츠 및 사용자 정보 하위 사이트</span><span class="sxs-lookup"><span data-stu-id="b6433-118">Subsites of the top-level website, their contents, and user information</span></span>

<span data-ttu-id="b6433-119">실수로 사이트 모음을 삭제 한 경우에는 SharePoint 관리 센터를 사용 하 여 전역 관리자 또는 SharePoint 관리에 의해 복원 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6433-119">If you accidentally delete a site collection, it can be restored by a global or SharePoint admin using the SharePoint admin center.</span></span> 

<span data-ttu-id="b6433-120">하드 삭제는 사용자가 사이트 모음 휴지통에서 삭제 된 항목을 제거 하거나, 보존 및 백업 기간이 만료 되거나, 관리자가 [remove-spodeletedsite cmdlet](/powershell/module/sharepoint-online/Remove-SPODeletedSite?view=sharepoint-ps)을 사용 하 여 사이트 모음을 영구적으로 삭제할 때 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6433-120">Hard deletion occurs when a user purges deleted items from the site collection Recycle Bin, when the retention and backup periods expire, or when an administrator permanently deletes a site collection using the [Remove-SPODeletedSite cmdlet](/powershell/module/sharepoint-online/Remove-SPODeletedSite?view=sharepoint-ps).</span></span> <span data-ttu-id="b6433-121">사용자가 SharePoint Online에서 콘텐츠를 영구적으로 삭제 하거나 제거 하면 삭제 된 청크의 모든 암호화 키도 삭제 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6433-121">When a user hard deletes (permanently deletes, or purges) content from SharePoint Online, all encryption keys for the deleted chunks are also deleted.</span></span> <span data-ttu-id="b6433-122">이전에 삭제 한 청크를 저장 한 디스크의 블록은 사용 되지 않는 것으로 표시 되며 다시 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6433-122">The blocks on the disks that previously stored the deleted chunks are marked as unused and available for re-use.</span></span>
