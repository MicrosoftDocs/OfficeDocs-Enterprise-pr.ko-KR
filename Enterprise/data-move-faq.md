---
title: 데이터 이동 일반 FAQ
ms.author: deniseb
author: denisebmsft
manager: laurawi
ms.date: 9/14/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 1f01bc6f-5d37-4d14-bdd3-9d94a1e23e14
description: 다음은 새 데이터 센터 지리적으로 핵심 데이터를 이동 하는 방법에 대 한 일반적인 질문에 대답 합니다.
ms.openlocfilehash: 40f83ee94aaa7c919f08d91d888ff131da02df67
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542076"
---
# <a name="data-move-general-faq"></a><span data-ttu-id="2074f-103">데이터 이동 일반 FAQ</span><span class="sxs-lookup"><span data-stu-id="2074f-103">Data move general FAQ</span></span>

<span data-ttu-id="2074f-104">다음은 새 데이터 센터 지리적으로 핵심 데이터를 이동 하는 방법에 대 한 일반적인 질문에 대답 합니다.</span><span class="sxs-lookup"><span data-stu-id="2074f-104">Here are answers to general questions about moving core data to a new datacenter geo.</span></span>
  
 <span data-ttu-id="2074f-105">**질문: 이동 중에 고객 데이터를 안전하게 유지하고 가동 중지가 발생하지 않게 하려면 어떻게 해야 하나요?**</span><span class="sxs-lookup"><span data-stu-id="2074f-105">**Q. How do you make sure my customer data is safe during the move and that I won't experience downtime?**</span></span>
  
<span data-ttu-id="2074f-p101">A. 데이터 이동은 백엔드 서비스 작업을 최종 사용자에 게 미치는 영향 최소화 합니다. 영향을 미칠 수 있는 기능 [중 및 데이터 이동 후](during-and-after-your-data-move.md)에 나열 됩니다. 위치 고객 필요한 준비 하기 위해 또는 이동 하는 동안 모니터링 하는 경우 nothing 이므로 가용성을 위해 [Microsoft Online Services 서비스 수준 계약 (SLA)를](https://go.microsoft.com/fwlink/p/?LinkId=523897) 준수 합니다.</span><span class="sxs-lookup"><span data-stu-id="2074f-p101">A. Data moves are a back-end service operation with minimal impact to end-users. Features that can be impacted are listed in [During and after your data move](during-and-after-your-data-move.md). We adhere to the [Microsoft Online Services Service Level Agreement (SLA)](https://go.microsoft.com/fwlink/p/?LinkId=523897) for availability so there is nothing that customers need to prepare for or to monitor during the move.</span></span> 
  
<span data-ttu-id="2074f-p102">모든 Office 365 서비스는 데이터 센터에서 동일한 버전이 실행되므로 일관된 기능이 보장될 수 있습니다. 서비스는 프로세스 전반에 걸쳐 완벽하게 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="2074f-p102">All Office 365 services run the same versions in the datacenters, so you can be assured of consistent functionality. Your service is fully supported throughout the process.</span></span>
  
 <span data-ttu-id="2074f-112">**Q: 서로 다른 geos에 있는 다른 서비스의 영향 란 무엇입니까?**</span><span class="sxs-lookup"><span data-stu-id="2074f-112">**Q. What is the impact of having different services located in different geos?**</span></span>
  
<span data-ttu-id="2074f-p103">A.에 대 한 일부 기존 고객 및 고객 이동 프로세스 중에 Office 365 서비스 중 일부를 다른 geos에 있을 수 있습니다. 이 서비스는 서로 독립적으로 실행 하 고 방법이 다음의 경우에는 해당 하는 경우 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2074f-p103">A. For some existing customers and customers in the middle of the move process, some of the Office 365 services may be located in different geos. Our services run independently of each other and there is no user impact if this is the case.</span></span>
  
 <span data-ttu-id="2074f-116">**Q: 새 Office 365 고객에 게 자동으로 구축할 새 데이터 센터 geos?**</span><span class="sxs-lookup"><span data-stu-id="2074f-116">**Q. Will new Office 365 customers be automatically provisioned in the new datacenter geos?**</span></span>
  
<span data-ttu-id="2074f-p104">A. 예입니다. 새 데이터 센터 지리적으로 분산을 사용할 수 있는 새로운 Office 365 등록 하는 동안 자신의 국가으로 새로운 지리적으로 분산에 대 한 가능한 국가 선택 하는 비즈니스 고객에 대 한 새 데이터 센터 지리적으로 분산에서 호스팅되는 자신의 핵심 데이터 갖게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2074f-p104">A. Yes. Once a new datacenter geo is available, new Office 365 for business customers who select a country eligible for the new geo as their country during sign-up will have their core data hosted in the new datacenter geo.</span></span>
  
 <span data-ttu-id="2074f-120">**질문: 내 데이터는 어디에 있나요?**</span><span class="sxs-lookup"><span data-stu-id="2074f-120">**Q. Where is my data is located?**</span></span>
  
<span data-ttu-id="2074f-p105">데이터 센터 geos, 데이터 센터 및 [Office 365 대화형 데이터 센터에 매핑합니다 ](https://o365datacentermap.azurewebsites.net)에서 고객 데이터의 위치는 위치를 게시합니다. 8 월 1 일 이후로 데이터 위치 섹션에서 Office 365 관리 센터에서 조직 프로필을 통해 나머지 부분에서 고객 데이터의 위치를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2074f-p105">We publish the location of datacenter geos, datacenters, and location of customer data on the [ Office 365 interactive datacenter maps ](https://o365datacentermap.azurewebsites.net). As of August 1, you will be able to verify the location of your customer data at rest via the Data Location section under your Organization Profile in the Office 365 Admin Center.</span></span>
  
 <span data-ttu-id="2074f-123">**Q: 기존 Office 365 고객으로 이동할 새 데이터 센터 geos?**</span><span class="sxs-lookup"><span data-stu-id="2074f-123">**Q. Will existing Office 365 customers be moved to the new datacenter geos?**</span></span>
  
<span data-ttu-id="2074f-p106">A. 가능한 Office 365 고객은이 새로운 geos로 이동 핵심 데이터를 요청할 수 있습니다. 고객 참가 하기 위해 자신의 지리적으로 분산에 대 한 마감 하기 전에 요청을 제출 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2074f-p106">A. Eligible Office 365 customers can request to have their core data moved to the new geos. Customers will need to submit a request before the deadline for their geo in order to participate.</span></span> 
  
 <span data-ttu-id="2074f-127">**질문: 어떤 고객이 이동을 요청할 수 있나요?**</span><span class="sxs-lookup"><span data-stu-id="2074f-127">**Q. What customers are eligible to request a move?**</span></span>
  
<span data-ttu-id="2074f-p107">A. 기존 Office 365 상업용 고객에 게 새 데이터 센터 지리적으로 분산에 대 한 가능한 국가 선택가 이동 요청 수입니다.</span><span class="sxs-lookup"><span data-stu-id="2074f-p107">A. Existing Office 365 commercial customers who selected a country eligible for the new datacenter geo will be able to request a move.</span></span> 
  
 <span data-ttu-id="2074f-130">**질문: 언제 이동을 요청할 수 있나요?**</span><span class="sxs-lookup"><span data-stu-id="2074f-130">**Q. When will I be able to request a move?**</span></span>
  
<span data-ttu-id="2074f-p108">A. 요청 기간 [데이터 이동 요청 하는 방법](request-your-data-move.md) 페이지에서 발표 될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="2074f-p108">A. The request period will be announced on the [How to request your data move](request-your-data-move.md) page.</span></span> 
  
 <span data-ttu-id="2074f-133">**질문: 이동을 요청하려면 어떻게 해야 하나요?**</span><span class="sxs-lookup"><span data-stu-id="2074f-133">**Q. How can I request to be moved?**</span></span>
  
<span data-ttu-id="2074f-p109">A. 가능한 고객의 페이지는 [Office 365 관리 포털](https://portal.office.com/)에 표시 됩니다. 이동 요청 하는 방법에 대 한 지침은 [데이터 이동 요청 하는 방법](request-your-data-move.md) 을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="2074f-p109">A. Eligible customers will see a page in their [Office 365 Admin Portal](https://portal.office.com/). Please see [How to request your data move](request-your-data-move.md) for instructions on how to request a move.</span></span> 
  
 <span data-ttu-id="2074f-137">**질문: 이동을 요청하면 선택 옵션이 달라지나요?**</span><span class="sxs-lookup"><span data-stu-id="2074f-137">**Q. Can I change my selection after requesting a move?**</span></span>
  
<span data-ttu-id="2074f-p110">
대답: 요청을 제출하면 저희가 프로세스에서 귀하를 제거할 수 없게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2074f-p110">A. It is not possible for us to remove you from the process after you submit your request.</span></span>
  
 <span data-ttu-id="2074f-140">**질문: 마감 날짜가 될 때까지 이동을 요청하지 않으면 어떻게 되나요?**</span><span class="sxs-lookup"><span data-stu-id="2074f-140">**Q. What happens if I do not request a move before the deadline?**</span></span>
  
<span data-ttu-id="2074f-p111">A.는 각 지리적으로 분산에서 마감일 이동할 수에 대 한 요청을 수락할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2074f-p111">A. We are unable to accept requests to be moved after the deadline in each geo.</span></span>
  
 <span data-ttu-id="2074f-143">**질문: 더 나은 네트워크 성능을 얻기 위해 데이터를 이동하고 싶으면 어떻게 해야 하나요?**</span><span class="sxs-lookup"><span data-stu-id="2074f-143">**Q. What if I want to move my data in order to get better network performance?**</span></span>
  
<span data-ttu-id="2074f-p112">네트워킹 성능 향상을 위해 보장 되지는 않음을 Office 365 datacenter 근접 하는 것입니다. 다양 한 요인 및 최종 사용자와 Office 365 서비스 간의 네트워크 성능에 영향이 발생 하는 구성 요소가 있습니다. 자세한 내용은이 대 한 및 성능 조정에 대 한 [네트워크 계획 및 Office 365에 대 한 성능 조정](network-planning-and-performance.md)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="2074f-p112">Being close to an Office 365 datacenter is not a guarantee for a better networking performance. There are many factors and components that impact the network performance between the end user and the Office 365 service. For more information about this and performance tuning see [Network planning and performance tuning for Office 365](network-planning-and-performance.md).</span></span>
  
 <span data-ttu-id="2074f-147">**질문: 모든 서비스가 같은 날에 데이터를 이동하나요?**</span><span class="sxs-lookup"><span data-stu-id="2074f-147">**Q. Do all the services move their data on the same day?**</span></span>
  
<span data-ttu-id="2074f-p113">
대답: 서비스가 동시에 데이터를 이동하지는 않습니다. 각 서비스는 독립적으로 이동하며 다른 시간에 데이터를 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2074f-p113">A. The services do not move their data at the same time. Each service will move independently and will likely move their data at different times.</span></span>
  
 <span data-ttu-id="2074f-151">**질문: 데이터를 이동하고 싶은 시기를 선택할 수 있나요?**</span><span class="sxs-lookup"><span data-stu-id="2074f-151">**Q. Can I choose when I want my data to be moved?**</span></span>
  
<span data-ttu-id="2074f-p114">
대답: 고객은 특정 날짜를 선택할 수 없으며 이동을 연기할 수도 없습니다. Microsoft는 이동의 구체적 날짜나 기간을 알려드릴 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2074f-p114">A. Customers are not able to select a specific date, they cannot delay their move, and we cannot share a specific date or timeframe for the moves.</span></span>
  
 <span data-ttu-id="2074f-154">**질문: 내 데이터가 언제 이동될지 알려줄 수 있나요?**</span><span class="sxs-lookup"><span data-stu-id="2074f-154">**Q. Can you share when my data will be be moved?**</span></span>
  
<span data-ttu-id="2074f-p115">대답: 데이터 이동은 최종 사용자에게 최소의 영향만 미치는 백 엔드 작업입니다. 전체적으로 운영되는 자동화 환경에서 데이터 이동을 수행할 때 수반되는 복잡성, 정밀도 및 규모 때문에 귀하의 테넌트 또는 다른 단일 테넌트에서 데이터 이동이 완료될 것으로 예상되는 시기를 알려드리기가 어렵습니다. 고객은 데이터 이동이 완료되었을 때 메시지 센터에서 관련 서비스별로 1번의 확인을 받게 됩니다. </span><span class="sxs-lookup"><span data-stu-id="2074f-p115">A. Data moves are a back-end operation with minimal impact to end-users. The complexity, precision and scale at which we need to perform data moves within a globally operated and automated environment prohibit us from sharing when a data move is expected to complete for your tenant or any other single tenant. Customers will receive one confirmation in Message Center per participating service when its data move has completed.</span></span> 
  
 <span data-ttu-id="2074f-159">**질문: 데이터가 이동되는 동안 사용자가 서비스에 액세스하면 어떻게 되나요?**</span><span class="sxs-lookup"><span data-stu-id="2074f-159">**Q. What happens if users access services while the data is being moved?**</span></span>
  
<span data-ttu-id="2074f-p116">
대답: 각 서비스에 대한 데이터 이동 중에 제한될 수 있는 기능의 전체 목록을 보려면 [During and after your data move](during-and-after-your-data-move.md)를 참조하세요.

</span><span class="sxs-lookup"><span data-stu-id="2074f-p116">A. See [During and after your data move](during-and-after-your-data-move.md) for a complete list of features that may be limited during portions of the data move for each service.</span></span> 
  
 <span data-ttu-id="2074f-162">**질문: 이동이 완료되었는지를 어떻게 알 수 있나요?**</span><span class="sxs-lookup"><span data-stu-id="2074f-162">**Q. How do I know the move is complete?**</span></span>
  
<span data-ttu-id="2074f-p117">A. 조사 Office 365 메시지 센터에서 각 서비스의 데이터 이동이 완료 되었는지 확인 합니다. 각 서비스의 데이터를 이동할 때 하겠습니다 게시 하는 완료 주의 표시 세 완료 통지를 얻을 수 있도록: 각각에 대 한 Exchange Online, SharePoint Online 및 비즈니스 온라인 용 Skype 합니다.</span><span class="sxs-lookup"><span data-stu-id="2074f-p117">A. Watch the Office 365 message center for confirmation that the move of each service's data is complete. When each service's data is moved, we'll post a completion notice so you'll get three completion notices: one each for Exchange Online, SharePoint Online, and Skype for Business Online.</span></span>
  
<span data-ttu-id="2074f-166">이동 후 문제를 참조 하는 경우 도움을 받을를 [Office 365 지원](https://go.microsoft.com/fwlink/p/?LinkID=522459) 문의 합니다.</span><span class="sxs-lookup"><span data-stu-id="2074f-166">If you see any issues after the move, contact [Office 365 Support](https://go.microsoft.com/fwlink/p/?LinkID=522459) to get assistance.</span></span> 
  
 <span data-ttu-id="2074f-167">**Q: Office 365에 대 한 데이터는 새 데이터 센터 geos에 저장 되어 있습니까?**</span><span class="sxs-lookup"><span data-stu-id="2074f-167">**Q. What data for Office 365 is stored in the new datacenter geos?**</span></span>
  
<span data-ttu-id="2074f-p118">A. 나머지는 지리적으로 분산 내에서 다음과 같은 고객 데이터를 저장 하는 새 데이터 센터 geos Microsoft 중 하나에 해당 테 넌 트 고객 규정 하는 경우:</span><span class="sxs-lookup"><span data-stu-id="2074f-p118">A. If a customer provisions its tenant in one of the new datacenter geos, Microsoft stores the following customer data at rest within the geo:</span></span>
  
- <span data-ttu-id="2074f-170">Exchange Online 사서함 콘텐츠(전자 메일 본문, 일정 항목 및 전자 메일 첨부 파일 콘텐츠)</span><span class="sxs-lookup"><span data-stu-id="2074f-170">Exchange Online mailbox content (e-mail body, calendar entries, and the content of email attachments)</span></span>
    
- <span data-ttu-id="2074f-171">해당 사이트 내에 저장된 SharePoint Online 사이트 콘텐츠 및 파일(Project Online 및 Access Online 콘텐츠 포함)</span><span class="sxs-lookup"><span data-stu-id="2074f-171">SharePoint Online site content and the files stored within that site, including Project Online and Access Online content.</span></span>
    
<span data-ttu-id="2074f-172">또한이 데이터는 지리적으로 분산 외부의 복제 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2074f-172">In addition, this data is not replicated outside of the geo.</span></span>
  
 <span data-ttu-id="2074f-173">**Q: 결정에 새 데이터 센터 geos 중 하나는 Office 365 고객 하지만 등록 된 I I 다른 국가 선택 합니다. 어떻게 합니까으로 이동할 수 새 데이터 센터 지리적으로 분산?**</span><span class="sxs-lookup"><span data-stu-id="2074f-173">**Q. I am an Office 365 customer in one of the new datacenter geos, but when I signed up, I selected a different country. How can I be moved to the new datacenter geo?**</span></span>
  
<span data-ttu-id="2074f-p119">
대답: 아쉽게도 해당 테넌트와 연결된 국가는 변경할 수 없습니다. 대신, 새 구독으로 새 Office 365 테넌트를 만들고 사용자 및 데이터를 새 테넌트에 수동으로 이동해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2074f-p119">A. Unfortunately, it is not possible to change the country associated with your tenant. Instead, you need to create a new Office 365 tenant with a new subscription and manually move your users and data to the new tenant.</span></span>
  
 <span data-ttu-id="2074f-177">**질문: 요금 청구서가 달라지나요?**</span><span class="sxs-lookup"><span data-stu-id="2074f-177">**Q. Will there be any changes on my bill?**</span></span>
  
<span data-ttu-id="2074f-p120">
대답: 대부분의 경우 고객의 요금 청구서는 달라지지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2074f-p120">A. In most cases there are no changes that customers in will see on their billing statement.</span></span>
  
<span data-ttu-id="2074f-p121">Microsoft는 호주의 모든 Office 365 고객에게 Office 365용 호주 GST 서비스와 동일한 추가 요금을 부과하며, 세금 청구서를 발행합니다. 이러한 변경은 호주 GST가 호주에서 제공되는 상품 및 서비스 중에서 과세 대상 항목에 청구되기 때문에 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="2074f-p121">Microsoft will charge all Australian customers of Office 365 an additional amount equal to the Australian GST for Office 365 services and will issue tax invoices. This change will occur because Australian GST is payable on taxable supplies of goods and services provided and offered in Australia.</span></span>
  
 <span data-ttu-id="2074f-182">**질문: 우리는 Exchange Online 이동 하는 동안 Office 365로 전자 메일 데이터 마이그레이션 중일 경우 어떻게 됩니까?**</span><span class="sxs-lookup"><span data-stu-id="2074f-182">**Q. What happens if we are in process of email data migration to Office 365 during the Exchange Online move?**</span></span>
  
<span data-ttu-id="2074f-p122">
대답: 전자 메일 마이그레이션이 진행되는 경우 테넌트 이동이 완료되는 동안 현재 마이그레이션 중인 개별 사서함이 취소되고, 해당 사서함의 마이그레이션은 테넌트가 대상 데이터 센터에 포함되면 자동으로 다시 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="2074f-p122">A. If email migrations are in progress, any individual mailboxes that are currently being migrated will be canceled while the tenant move finalizes, and migration of those mailboxes will automatically restart once the tenant is in the target datacenters.</span></span>
  
 <span data-ttu-id="2074f-185">**Q: 한 후 데이터는 이전 데이터 센터 지리적으로 분산 밖으로 이동 될, 해당 데이터 센터에서 제거 됩니다?**</span><span class="sxs-lookup"><span data-stu-id="2074f-185">**Q. After data is moved out of the previous datacenter geo, is it removed from those datacenters?**</span></span>
  
<span data-ttu-id="2074f-p123">
대답: 예. 일정 시간 후에 오래된 데이터는 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="2074f-p123">A. Yes, the old data will be purged after a period of time.</span></span>
  
 <span data-ttu-id="2074f-188">**질문: 일부 사용자에게 파일럿 테스트를 수행할 수 있나요?**</span><span class="sxs-lookup"><span data-stu-id="2074f-188">**Q. Can I pilot some users?**</span></span>
  
<span data-ttu-id="2074f-p124">A. 때 새 데이터 센터 지리적으로 분산에서 Office 365 테 넌 트를 이동 모든 사용자에 게 동시에 이동 됩니다. 연결을 테스트 하는 별도 평가판 테 넌 트를 만들 수 있지만 기존 테 넌 트와 어떤 식으로도 평가판 테 넌 트를 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2074f-p124">A. When your Office 365 tenant is moved to a new datacenter geo, all users are moved at once. You can create a separate trial tenant to test connectivity, but the trial tenant can't be combined in any way with your existing tenant.</span></span>
  
 <span data-ttu-id="2074f-192">**질문: 이동에 대해 알림을 받으려면 어떻게 해야 하며 회사에서 누구에게 알림이 제공되나요?**</span><span class="sxs-lookup"><span data-stu-id="2074f-192">**Q. How will I be notified about the move and who at my company will be notified?**</span></span>
  
<span data-ttu-id="2074f-p125">A.는 Office 365에서 모든 관리 권한이 있는 모든 사용자에 게 표시 되는 Office 365 메시지 센터를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="2074f-p125">A. We'll use the Office 365 message center, which is visible to anyone with any admin permissions in Office 365.</span></span>
  
 <span data-ttu-id="2074f-195">**Q: 하지 않겠습니다 내 데이터를 이동 하는 Microsoft 기다립니다. 수 있습니까 방금 새 테 넌 트를 만들고 이동 아니오?**</span><span class="sxs-lookup"><span data-stu-id="2074f-195">**Q. I don't want to wait for Microsoft to move my data. Can I just create a new tenant and move myself?**</span></span>
  
<span data-ttu-id="2074f-p126">
대답: 예. 그렇지만 Microsoft가 데이터 이동을 수행하는 것처럼 프로세스가 원활하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2074f-p126">A. Yes, however the process will not be as seamless as if Microsoft were to perform the data move.</span></span>
  
<span data-ttu-id="2074f-p127">사용할 수 있는 새 데이터 센터 지리적으로 분산 된 후 새 테 넌 트를 만드는 경우 새 테 넌 트는 새로운 지리적으로 분산에서 호스팅할 수 있습니다. 이 새 테 넌 트 이전 테 넌 트 완전히 별개 이며 모든 사용자 사서함, 사이트 콘텐츠, 도메인 이름 및 기타 데이터를 이동 하는 일을 담당 해야 합니다. 참고 다른 테 넌 트 이름을 이동할 한 테 넌 트에서 수 없도록 합니다. 모든 설정, 데이터 및 사용자에 대 한 구독을 이동 하는 주의 하는 대로 Microsoft에서 제공 하는 move 프로그램이 나올 때까지 기다리는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="2074f-p127">If you create a new tenant after the new datacenter geo is available, the new tenant will be hosted in the new geo. This new tenant is completely separate from your previous tenant and you would be responsible for moving all user mailboxes, site content, domain names, and any other data. Note that you can't move the tenant name from one tenant to another. We recommend that you wait for the move program provided by Microsoft as we'll take care of moving all settings, data, and subscriptions for your users.</span></span>
  
 <span data-ttu-id="2074f-202">**Q: 없으므로 이동할 준비가, 특정 이동 날짜를 선택할 수 있습니까?**</span><span class="sxs-lookup"><span data-stu-id="2074f-202">**Q. I'm not ready to be moved, can I pick a specific move date?**</span></span>
  
<span data-ttu-id="2074f-p128">
대답: 각 서비스의 고객 데이터가 이동될 시기를 변경할 수는 없습니다. 데이터 이동은 최종 사용자에게 최소의 영향만 미치는 백 엔드 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="2074f-p128">A. It is not possible for you to change when each service's customer data will be moved. Data moves are a back-end operation with minimal impact to end-users.</span></span>
  
 <span data-ttu-id="2074f-206">**Q: 내 고객 데이터는 새 데이터 센터 지리적으로 분산을 이미 이동 했습니다. 다시 이동할 수 있습니까?**</span><span class="sxs-lookup"><span data-stu-id="2074f-206">**Q. My customer data has already been moved to a new datacenter geo. Can I move back?**</span></span>
  
<span data-ttu-id="2074f-p129">A.이 불가능합니다. 새로운 지리적으로 분산 데이터 센터에 이동 된 고객은 다시 이동할 수 없습니다. 모든 지리적으로 분산에서 고객을으로 이전과 동일한 방법으로 서비스, 성능 및 보안 컨트롤의 동일한 품질을 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2074f-p129">A. This is not possible. Customers who have been moved to new geo datacenters cannot be moved back. As a customer in any geo, you will experience the same quality of service, performance, and security controls as you did before.</span></span>
  
 <span data-ttu-id="2074f-211">**질문: 새 데이터 센터 geos 현재 데이터 센터 geos와 동일한 버전의 Office 365 서비스를 사용 합니까?**</span><span class="sxs-lookup"><span data-stu-id="2074f-211">**Q. Do the new datacenter geos use the same versions of Office 365 services as the current datacenter geos?**</span></span>
  
<span data-ttu-id="2074f-p130">A. 예입니다.</span><span class="sxs-lookup"><span data-stu-id="2074f-p130">A. Yes.</span></span>
  
 <span data-ttu-id="2074f-214">**질문: Office 365 테넌트는 해외 사용자가 사용할 수 있는 새로운 데이터 센터에 호스트되나요?**</span><span class="sxs-lookup"><span data-stu-id="2074f-214">**Q. Will Office 365 tenants hosted in the new datacenters be available to users outside of the country?**</span></span>
  
<span data-ttu-id="2074f-p131">
대답: 예. Microsoft는 1,500개가 넘는 ISP(인터넷 서비스 공급자)와 피어링 계약을 맺고 전 세계 23개국에 있는 50여 위치에서 공용 인터넷 연결이 구축된 대규모 전역 네트워크를 제공하고 있습니다. 사용자는 인터넷의 어디에서든지 데이터 센터에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2074f-p131">A. Yes. Microsoft maintains a large global network with public Internet connections in more than 50 locations in 23 countries around the world with peering agreements with more than 1,500 Internet Service Providers (ISPs). Users will be able to access the datacenters from wherever they are on the Internet.</span></span>
  

