---
title: "Office 365 PowerShell을 사용하여 Sway에 대한 액세스 비활성화"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- DecEntMigration
ms.assetid: 7221a4c9-ae03-4598-81fe-a655c02f40ab
description: "Office 365 조직에서 영향에 대 한 액세스를 사용 하지 않도록 설정할 수 있도록 하는 ManageSway.ps1 PowerShell 스크립트를 다운로드 하는 위치에 알아봅니다."
ms.openlocfilehash: c27aaa7006fa0e29644b11ebc53c0d50e0d97fda
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2017
---
# <a name="disable-access-to-sway-with-office-365-powershell"></a><span data-ttu-id="f306f-103">Office 365 PowerShell을 사용하여 Sway에 대한 액세스 비활성화</span><span class="sxs-lookup"><span data-stu-id="f306f-103">Disable access to Sway with Office 365 PowerShell</span></span>

<span data-ttu-id="f306f-104">**요약** ManageSway.ps1 PowerShell 스크립트를 사용 하 여 Office 365 조직에서 영향에 대 한 액세스를 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f306f-104">**Summary** Use the ManageSway.ps1 PowerShell script to disable access to Sway in your Office 365 organization.</span></span>
  
<span data-ttu-id="f306f-p101">ManageSway.ps1 PowerShell 스크립트를 사용 하면 보기 및 Office 365 조직 전체에서 영향을 포함 하 여 서비스를 사용 하지 않도록 설정할 수 있습니다. 이 스크립트는 다음 항목에서 설명 하는 절차를 자동화 합니다.</span><span class="sxs-lookup"><span data-stu-id="f306f-p101">The ManageSway.ps1 PowerShell script allows you to view and disable services in your Office 365 organization, including Sway. This script automates the procedures that are described in the following topics:</span></span>
  
- [<span data-ttu-id="f306f-107">라이선스 및 Office 365 PowerShell을 사용 하 여 서비스 보기</span><span class="sxs-lookup"><span data-stu-id="f306f-107">View licenses and services with Office 365 PowerShell</span></span>](view-licenses-and-services-with-office-365-powershell.md)
    
- [<span data-ttu-id="f306f-108">Office 365 PowerShell을 사용 하 여 서비스에 대 한 액세스를 사용 하지 않도록 설정</span><span class="sxs-lookup"><span data-stu-id="f306f-108">Disable access to services with Office 365 PowerShell</span></span>](disable-access-to-services-with-office-365-powershell.md)
    
<span data-ttu-id="f306f-109">이 스크립트와 연결된 두 개의 파일을 다운로드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f306f-109">You need to download the two files that are associated with the script:</span></span>
  
- <span data-ttu-id="f306f-110">[Https://go.microsoft.com/fwlink/p/?LinkId=785070](https://go.microsoft.com/fwlink/p/?LinkId=785070) 에서 ManageSway.ps1 스크립트</span><span class="sxs-lookup"><span data-stu-id="f306f-110">The ManageSway.ps1 script at [https://go.microsoft.com/fwlink/p/?LinkId=785070](https://go.microsoft.com/fwlink/p/?LinkId=785070)</span></span>
    
- <span data-ttu-id="f306f-111">[Https://go.microsoft.com/fwlink/p/?LinkId=785072](https://go.microsoft.com/fwlink/p/?LinkId=785072) 에서 스크립트에 대 한 도움말 파일</span><span class="sxs-lookup"><span data-stu-id="f306f-111">The help file for the script at [https://go.microsoft.com/fwlink/p/?LinkId=785072](https://go.microsoft.com/fwlink/p/?LinkId=785072)</span></span>
    

