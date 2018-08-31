---
title: Exchange Online 성능 조정
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 12/14/2017
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Adm_O365
ms.assetid: 026e83cb-a945-4543-97b0-a8af6e80ac61
description: 이 문서는 일반 팁 및 Exchange Online의 성능을 개선 하는 방법을 안내 하는 기타 리소스에 대 한 링크를 포함 합니다.
ms.openlocfilehash: 20a3a61517212df88cb380ade47c268c429e52a8
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542275"
---
# <a name="tune-exchange-online-performance"></a><span data-ttu-id="f7ae0-103">Exchange Online 성능 조정</span><span class="sxs-lookup"><span data-stu-id="f7ae0-103">Tune Exchange Online performance</span></span>

<span data-ttu-id="f7ae0-p101">이 문서는 일반 팁 및 Exchange Online의 성능을 개선 하는 방법을 안내 하는 기타 리소스에 대 한 링크를 포함 합니다. 이 문서는 [네트워크 계획 및 성능 조정 Office 365에 대 한](https://aka.ms/tune) 프로젝트의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ae0-p101">This article contains general tips and links to other resources that tell you how to improve performance of Exchange Online. This article is part of the [Network planning and performance tuning for Office 365](https://aka.ms/tune) project.</span></span>
   
## <a name="things-to-consider-in-order-to-improve-exchange-online-performance"></a><span data-ttu-id="f7ae0-106">Exchange Online 성능을 개선 하기 위해 고려 해야할 사항</span><span class="sxs-lookup"><span data-stu-id="f7ae0-106">Things to consider in order to improve Exchange Online performance</span></span>

<span data-ttu-id="f7ae0-107">마이그레이션 속도 개선 하 고 Exchange Online에 대 한 조직의 대역폭 제약 조건을 줄이려면, 하려면 다음을 고려 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ae0-107">To improve the speed of migration and reduce your organization's bandwidth constraints for Exchange Online, consider the following:</span></span>
  
- <span data-ttu-id="f7ae0-p102">**사서함 크기를 줄입니다.** 사서함 크기가 작을수록 마이그레이션 속도가 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7ae0-p102">**Reduce mailbox sizes.** Smaller mailbox size improves migration speed.</span></span> 
    
- <span data-ttu-id="f7ae0-p103">**Exchange 하이브리드 배포를 통해 사서함 이동 기능을 사용합니다.** Exchange 하이브리드 배포를 사용하면 Exchange Online으로 마이그레이션할 때 오프라인 메일(.OST 파일 형태)을 다시 다운로드할 필요가 없습니다. 따라서 다운로드 대역폭 요구 사항이 크게 감소합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ae0-p103">**Use the mailbox move capabilities with an Exchange hybrid deployment.** With an Exchange hybrid deployment, offline mail (in the form of .OST files) does not require re-download when migrating to Exchange Online. This significantly reduces your download bandwidth requirements.</span></span> 
    
- <span data-ttu-id="f7ae0-p104">**인터넷 트래픽이 낮고 온-프레미스 Exchange 사용량이 적을 때 사서함을 이동하도록 예약합니다.** 이동을 예약하면 마이그레이션 요청이 사서함 복제 프록시로 제출되며 즉시 진행되지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7ae0-p104">**Schedule mailbox moves to occur during periods of low Internet traffic and low on-premises Exchange use.** When scheduling moves, migration requests are submitted to the mailbox replication proxy and may not take place immediately.</span></span> 
    
- <span data-ttu-id="f7ae0-p105">**웹에서 Outlook에 대 한 간결한 popouts를 사용 하 여.** 간결한 popouts 더 작은, 서버에서 일부 구성 요소를 렌더링 하 여 Microsoft에 지 또는 Internet Explorer에서 특정 전자 메일 메시지의 적은 메모리를 많이 사용 버전을 제공 합니다. 자세한 내용은 [메일 메시지를 읽을 때 사용 하는 메모리를 줄일 수 간결한 popouts 사용을](https://support.office.com/article/a6d6ba01-2562-4c3d-a8f1-78748dd506cf)참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="f7ae0-p105">**Use lean popouts for Outlook on the web.** Lean popouts provide smaller, less memory-intensive versions of certain email messages in Microsoft Edge or Internet Explorer by rendering some components on the server. For more information, see [Use lean popouts to reduce memory used when reading mail messages](https://support.office.com/article/a6d6ba01-2562-4c3d-a8f1-78748dd506cf).</span></span>
    
<span data-ttu-id="f7ae0-118">Exchange 마이그레이션 성능에 대 한 자세한 내용은 [Office 365 마이그레이션 성능 및 모범 사례를](https://support.office.com/article/d9acb371-fd6c-4c14-aa8e-db5cbe39aa57)참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="f7ae0-118">For more information about Exchange migration performance, see [Office 365 migration performance and best practices](https://support.office.com/article/d9acb371-fd6c-4c14-aa8e-db5cbe39aa57).</span></span>
  

