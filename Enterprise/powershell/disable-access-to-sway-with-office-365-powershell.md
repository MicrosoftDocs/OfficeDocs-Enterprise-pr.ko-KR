---
title: Microsoft 365 용 PowerShell을 사용 하 여 Sway에 대 한 액세스 사용 안 함
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: 7221a4c9-ae03-4598-81fe-a655c02f40ab
description: Microsoft 365 조직의 Sway에 대 한 액세스를 사용 하지 않도록 설정 하는 데 사용할 수 있는 ManageSway.ps1 PowerShell 스크립트를 다운로드 하는 위치에 대해 알아봅니다.
ms.openlocfilehash: d02a197e2767a1883abcc8fcb4074f3ac92de88a
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230704"
---
# <a name="disable-access-to-sway-with-powershell-for-microsoft-365"></a><span data-ttu-id="e540e-103">Microsoft 365 용 PowerShell을 사용 하 여 Sway에 대 한 액세스 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="e540e-103">Disable access to Sway with PowerShell for Microsoft 365</span></span>

<span data-ttu-id="e540e-104">*이 문서는 Microsoft 365 Enterprise 및 Office 365 Enterprise에 모두 적용 됩니다.*</span><span class="sxs-lookup"><span data-stu-id="e540e-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="e540e-105">ManageSway.ps1 PowerShell 스크립트를 사용 하면 Sway를 포함 하 여 Microsoft 365 조직에서 서비스를 확인 하 고 사용 하지 않도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e540e-105">The ManageSway.ps1 PowerShell script lets you view and disable services in your Microsoft 365 organization, including Sway.</span></span> <span data-ttu-id="e540e-106">이 스크립트는 다음 항목에서 설명하는 절차를 자동화합니다.</span><span class="sxs-lookup"><span data-stu-id="e540e-106">This script automates the procedures that are described in the following topics:</span></span>
  
- [<span data-ttu-id="e540e-107">PowerShell을 사용 하 여 라이선스 및 서비스 보기</span><span class="sxs-lookup"><span data-stu-id="e540e-107">View licenses and services with PowerShell</span></span>](view-licenses-and-services-with-office-365-powershell.md)
    
- [<span data-ttu-id="e540e-108">PowerShell을 사용 하 여 서비스에 대 한 액세스 비활성화</span><span class="sxs-lookup"><span data-stu-id="e540e-108">Disable access to services with PowerShell</span></span>](disable-access-to-services-with-office-365-powershell.md)
    
<span data-ttu-id="e540e-109">이 스크립트와 연결된 두 개의 파일을 다운로드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e540e-109">You need to download the two files that are associated with the script:</span></span>
  
- <span data-ttu-id="e540e-110">[https://go.microsoft.com/fwlink/p/?LinkId=785070](https://go.microsoft.com/fwlink/p/?LinkId=785070)에서 ManageSway.ps1 스크립트 다운로드</span><span class="sxs-lookup"><span data-stu-id="e540e-110">The ManageSway.ps1 script at [https://go.microsoft.com/fwlink/p/?LinkId=785070](https://go.microsoft.com/fwlink/p/?LinkId=785070)</span></span>
    
- <span data-ttu-id="e540e-111">[https://go.microsoft.com/fwlink/p/?LinkId=785072](https://go.microsoft.com/fwlink/p/?LinkId=785072)에서 스크립트의 도움말 파일 다운로드</span><span class="sxs-lookup"><span data-stu-id="e540e-111">The help file for the script at [https://go.microsoft.com/fwlink/p/?LinkId=785072](https://go.microsoft.com/fwlink/p/?LinkId=785072)</span></span>
    

