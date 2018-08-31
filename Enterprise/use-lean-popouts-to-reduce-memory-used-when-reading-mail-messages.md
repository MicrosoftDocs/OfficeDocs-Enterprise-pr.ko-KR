---
title: 간결한 popouts를 사용 하 여 메일 메시지를 읽을 때 사용 되는 메모리를 줄일 수
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 3/8/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: a6d6ba01-2562-4c3d-a8f1-78748dd506cf
description: 이 문서 웹에 있는 Outlook에서 메시지 다운로드 성능 개선 (영문)에 대 한 정보를 포함 합니다.
ms.openlocfilehash: 07c427793c1cd60d25020a1ab49855ed1bc77cf6
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541985"
---
# <a name="use-lean-popouts-to-reduce-memory-used-when-reading-mail-messages"></a><span data-ttu-id="7ba10-103">간결한 popouts를 사용 하 여 메일 메시지를 읽을 때 사용 되는 메모리를 줄일 수</span><span class="sxs-lookup"><span data-stu-id="7ba10-103">Use lean popouts to reduce memory used when reading mail messages</span></span>

<span data-ttu-id="7ba10-p101">이 문서 웹에 있는 Outlook에서 메시지 다운로드 성능 개선 (영문)에 대 한 정보를 포함 합니다. 이 문서는 [네트워크 계획 및 성능 조정 Office 365에 대 한](https://aka.ms/tune) 프로젝트의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="7ba10-p101">This article contains information for improving message download performance in Outlook on the web. This article is part of the [Network planning and performance tuning for Office 365](https://aka.ms/tune) project.</span></span>
   
<span data-ttu-id="7ba10-p102">Office 365 전역 관리자 *간결한 popouts* , Microsoft 지 또는 Internet Explorer에서 특정 전자 메일 메시지의 메모리를 많이 사용 버전 보다 작은을 제공 하기 위해 웹에서 Outlook을 구성할 수 있습니다. 간결한 popouts 웹에서 Outlook을 사용 하도록 구성 된 성능을 최적화 하는 서버쪽 구성 요소를 렌더링 로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ba10-p102">As an Office 365 global administrator, you can configure Outlook on the web to deliver  *lean popouts*  , a smaller, less memory-intensive version of certain email messages in Microsoft Edge or Internet Explorer. When lean popouts are configured for Outlook on the web, server-side rendered components are loaded that optimize performance.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="7ba10-108">3 월 2018 이후로 간결한 popouts 현재 사용할 수 없을 경우 사용 권한 제한, 예: 권한 관리 IRM (정보)를 지정 하는 메시지에 대 한</span><span class="sxs-lookup"><span data-stu-id="7ba10-108">As of March 2018, lean popouts are currently not available for messages that specify usage rights restrictions, such as Information Rights Management (IRM).</span></span> 
  
<span data-ttu-id="7ba10-109">이러한 기능 계속 주 창에서 작동 하지만 간결한 popouts에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7ba10-109">These features will continue to work in the main window but are not available in lean popouts:</span></span>
  
- <span data-ttu-id="7ba10-110">Outlook 추가 기능</span><span class="sxs-lookup"><span data-stu-id="7ba10-110">Outlook add-ins</span></span>
    
- <span data-ttu-id="7ba10-111">비즈니스 현재 상태에 대 한 Skype</span><span class="sxs-lookup"><span data-stu-id="7ba10-111">Skype for Business presence</span></span>
    
 <span data-ttu-id="7ba10-112">**Office 365 조직 내의 모든 사용자에 대 한 간결한 popouts를 구성 하려면**</span><span class="sxs-lookup"><span data-stu-id="7ba10-112">**To configure lean popouts for all users within your Office 365 organization**</span></span>
  
1. <span data-ttu-id="7ba10-113">[원격 PowerShell을 사용 하 여 온라인 Exchange에 연결](http://technet.microsoft.com/library/jj984289%28v=exchg.150%29.aspx )합니다.</span><span class="sxs-lookup"><span data-stu-id="7ba10-113">[Connect to Exchange Online Using Remote PowerShell](http://technet.microsoft.com/library/jj984289%28v=exchg.150%29.aspx ).</span></span>
    
2. <span data-ttu-id="7ba10-114">다음과 같이 LeanPopoutEnabled 매개 변수와 함께 [Set-organizationconfig](https://technet.microsoft.com/library/aa997443%28v=exchg.160%29.aspx) cmdlet를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ba10-114">Run the [Set-OrganizationConfig](https://technet.microsoft.com/library/aa997443%28v=exchg.160%29.aspx) cmdlet with the LeanPopoutEnabled parameter as follows:</span></span> 
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled <$true |$false >
  ```

    <span data-ttu-id="7ba10-115">예: 조직에서 모든 사용자에 대 한 간결한 popouts를 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ba10-115">For example, to enable lean popouts for all users in your organization:</span></span>
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $true
  ```

    <span data-ttu-id="7ba10-116">조직에서 모든 사용자에 대 한 간결한 popouts를 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ba10-116">To disable lean popouts for all users in your organization:</span></span>
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $false
  ```


