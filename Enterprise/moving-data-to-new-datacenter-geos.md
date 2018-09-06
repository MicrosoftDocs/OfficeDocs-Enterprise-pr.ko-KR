---
title: 핵심 데이터를 새 Office 365 데이터 센터 지역으로 이동
ms.author: deniseb
author: denisebmsft
manager: laurawi
ms.date: 09/05/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 0a35176a-e585-4dec-a90b-36be8314667f
description: '새 데이터 센터 geos 용량을 추가 하 고이 진행 중인 고객 제안 및 사용 현황 성장을 지원 하기 위해 리소스를 계산 합니다. 또한 새 데이터 센터 geos 핵심 고객 데이터에 대 한 데이터 residency에서-지리적으로 분산을 제공합니다. 핵심 고객 데이터는 Microsoft Online Services 용어에 정의 된 고객 데이터의 하위 집합을 참조 하는 용어: Exchange Online 사서함 콘텐츠 (전자 메일 본문, 일정 항목 및 전자 메일 첨부 파일의 콘텐츠) 및 SharePoint Online 사이트 콘텐츠 및 파일 해당 사이트 내에 저장 하 고 파일은 비즈니스용 OneDrive에 업로드 합니다.'
ms.openlocfilehash: 362cb257f2098c1acaf08541f34278ed9b4987d2
ms.sourcegitcommit: 75ad9af1fa8adc73611fc6140546222b001861d5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/06/2018
ms.locfileid: "23839586"
---
# <a name="moving-core-data-to-new-office-365-datacenter-geos"></a><span data-ttu-id="7d7dd-105">핵심 데이터를 새 Office 365 데이터 센터 지역으로 이동</span><span class="sxs-lookup"><span data-stu-id="7d7dd-105">Moving core data to new Office 365 datacenter geos</span></span>

<span data-ttu-id="7d7dd-p102">Office 365에 대 한 비즈니스 서비스에 대 한 새 데이터 센터 geos를 열고 계속 합니다. 이러한 새 데이터 센터 geos 용량을 추가 하 고이 진행 중인 고객 제안 및 사용 현황 성장을 지원 하기 위해 리소스를 계산 합니다. 또한 새 데이터 센터 geos 핵심 고객 데이터에 대 한 데이터 residency에서-지리적으로 분산을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7d7dd-p102">We continue to open new datacenter geos for Office 365 for business services. These new datacenter geos add capacity and compute resources to support our ongoing customer demand and usage growth. Additionally, the new datacenter geos offer in-geo data residency for core customer data.</span></span> 

<span data-ttu-id="7d7dd-109">핵심 고객 데이터는 [Microsoft Online Services 용어](https://go.microsoft.com/fwlink/p/?LinkID=249048)에 정의 된 고객 데이터의 하위 집합을 참조 하는 용어:</span><span class="sxs-lookup"><span data-stu-id="7d7dd-109">Core customer data is a term that refers to a subset of customer data defined in the [Microsoft Online Services Terms](https://go.microsoft.com/fwlink/p/?LinkID=249048):</span></span> 
- <span data-ttu-id="7d7dd-110">Exchange Online 사서함 콘텐츠 (전자 메일 본문, 일정 항목 및 전자 메일 첨부 파일의 콘텐츠)</span><span class="sxs-lookup"><span data-stu-id="7d7dd-110">Exchange Online mailbox content (email body, calendar entries, and the content of email attachments)</span></span>
- <span data-ttu-id="7d7dd-111">SharePoint Online 사이트 콘텐츠 및 해당 사이트 내에 저장 된 파일</span><span class="sxs-lookup"><span data-stu-id="7d7dd-111">SharePoint Online site content and the files stored within that site</span></span>
- <span data-ttu-id="7d7dd-112">비즈니스용 OneDrive에 업로드 된 파일</span><span class="sxs-lookup"><span data-stu-id="7d7dd-112">Files uploaded to OneDrive for Business</span></span> 
  
<span data-ttu-id="7d7dd-p103">새 데이터 센터 지리적으로 분산에 시작 하 여 이미 있는 기존 데이터 센터 지리적으로 분산에 저장 된 핵심 고객 데이터를 기존 고객 영향을 받지 않습니다. 소개 없는 고유한 기능, 기능 또는 새 데이터 센터 지리적으로 분산 된 규정 준수 인증. 이러한 두 geos 중 하나에 고객,으로 이전과 동일한 방법으로 서비스, 성능 및 보안 컨트롤의 동일한 품질을 발생할 수 있습니다. 기존 고객 엄격한 데이터 residency 요구 하 고 아래 표에 나열 된 새로운 지리적으로 분산으로 이동 핵심 고객 데이터를 포함 하는 옵션도 포함 되어 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d7dd-p103">Existing customers that have their core customer data stored in an already existing datacenter geo are not impacted by the launch of a new datacenter geo. We introduce no unique capabilities, features or compliance certifications with the new datacenter geo. As a customer in any of those two geos, you will experience the same quality of service, performance and security controls as you did before. We offer existing customers that have strict data residency requirements, and that are listed in the table below, an option to have their core customer data moved to the new geo.</span></span>
  
|<span data-ttu-id="7d7dd-117">대금 청구를 사용 하는 고객의 주소 \* \* \*</span><span class="sxs-lookup"><span data-stu-id="7d7dd-117">\*\*\*\*Customers with billing address in\*\*\*\*</span></span>|<span data-ttu-id="7d7dd-118">이전 데이터 센터 지리적으로 분산 \* \* \*</span><span class="sxs-lookup"><span data-stu-id="7d7dd-118">\*\*\*\*Previous datacenter geo\*\*\*\*</span></span>|<span data-ttu-id="7d7dd-119">새 데이터 센터 지리적으로 분산 \* \* \*</span><span class="sxs-lookup"><span data-stu-id="7d7dd-119">\*\*\*\*New datacenter geo\*\*\*\*</span></span>|<span data-ttu-id="7d7dd-120">지리적으로 분산 이후에 사용할 수 있는 \* \* \*</span><span class="sxs-lookup"><span data-stu-id="7d7dd-120">\*\*\*\*Geo available since\*\*\*\*</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="7d7dd-121">일본 \* \* \*</span><span class="sxs-lookup"><span data-stu-id="7d7dd-121">\*\*\*\*Japan\*\*\*\*</span></span>| <span data-ttu-id="7d7dd-122">아시아/태평양</span><span class="sxs-lookup"><span data-stu-id="7d7dd-122">Asia/Pacific</span></span> | <span data-ttu-id="7d7dd-123">일본</span><span class="sxs-lookup"><span data-stu-id="7d7dd-123">Japan</span></span> | <span data-ttu-id="7d7dd-124">2014년 12월</span><span class="sxs-lookup"><span data-stu-id="7d7dd-124">December 2014</span></span> |
|<span data-ttu-id="7d7dd-125">오스트레일리아, 뉴질랜드, 피지 \* \* \*</span><span class="sxs-lookup"><span data-stu-id="7d7dd-125">\*\*\*\*Australia, New Zealand, Fiji\*\*\*\*</span></span>| <span data-ttu-id="7d7dd-126">아시아/태평양</span><span class="sxs-lookup"><span data-stu-id="7d7dd-126">Asia/Pacific</span></span> | <span data-ttu-id="7d7dd-127">오스트레일리아</span><span class="sxs-lookup"><span data-stu-id="7d7dd-127">Australia</span></span> | <span data-ttu-id="7d7dd-128">2015년 3월</span><span class="sxs-lookup"><span data-stu-id="7d7dd-128">March 2015</span></span> |
|<span data-ttu-id="7d7dd-129">인도 \* \* \*</span><span class="sxs-lookup"><span data-stu-id="7d7dd-129">\*\*\*\*India\*\*\*\*</span></span>| <span data-ttu-id="7d7dd-130">아시아/태평양</span><span class="sxs-lookup"><span data-stu-id="7d7dd-130">Asia/Pacific</span></span> | <span data-ttu-id="7d7dd-131">인도</span><span class="sxs-lookup"><span data-stu-id="7d7dd-131">India</span></span> | <span data-ttu-id="7d7dd-132">2015년 10월</span><span class="sxs-lookup"><span data-stu-id="7d7dd-132">October 2015</span></span> |
|<span data-ttu-id="7d7dd-133">캐나다 \* \* \*</span><span class="sxs-lookup"><span data-stu-id="7d7dd-133">\*\*\*\*Canada\*\*\*\*</span></span>| <span data-ttu-id="7d7dd-134">북미</span><span class="sxs-lookup"><span data-stu-id="7d7dd-134">North America</span></span> | <span data-ttu-id="7d7dd-135">캐나다</span><span class="sxs-lookup"><span data-stu-id="7d7dd-135">Canada</span></span> | <span data-ttu-id="7d7dd-136">2016년 5월</span><span class="sxs-lookup"><span data-stu-id="7d7dd-136">May 2016</span></span> |
|<span data-ttu-id="7d7dd-137">영국 \* \* \*</span><span class="sxs-lookup"><span data-stu-id="7d7dd-137">\*\*\*\*United Kingdom\*\*\*\*</span></span>| <span data-ttu-id="7d7dd-138">유럽</span><span class="sxs-lookup"><span data-stu-id="7d7dd-138">Europe</span></span> | <span data-ttu-id="7d7dd-139">영국</span><span class="sxs-lookup"><span data-stu-id="7d7dd-139">United Kingdom</span></span> | <span data-ttu-id="7d7dd-140">2016년 9월</span><span class="sxs-lookup"><span data-stu-id="7d7dd-140">September 2016</span></span> |
|<span data-ttu-id="7d7dd-141">대한민국 \* \* \*</span><span class="sxs-lookup"><span data-stu-id="7d7dd-141">\*\*\*\*South Korea\*\*\*\*</span></span>| <span data-ttu-id="7d7dd-142">아시아/태평양</span><span class="sxs-lookup"><span data-stu-id="7d7dd-142">Asia/Pacific</span></span> | <span data-ttu-id="7d7dd-143">대한민국</span><span class="sxs-lookup"><span data-stu-id="7d7dd-143">South Korea</span></span> | <span data-ttu-id="7d7dd-144">2017년 4월</span><span class="sxs-lookup"><span data-stu-id="7d7dd-144">April 2017</span></span> |
|<span data-ttu-id="7d7dd-145">프랑스 \* \* \*</span><span class="sxs-lookup"><span data-stu-id="7d7dd-145">\*\*\*\*France\*\*\*\*</span></span>| <span data-ttu-id="7d7dd-146">유럽</span><span class="sxs-lookup"><span data-stu-id="7d7dd-146">Europe</span></span> | <span data-ttu-id="7d7dd-147">프랑스</span><span class="sxs-lookup"><span data-stu-id="7d7dd-147">France</span></span> | <span data-ttu-id="7d7dd-148">2018년 3월</span><span class="sxs-lookup"><span data-stu-id="7d7dd-148">March 2018</span></span> |
   
> [!NOTE]
> <span data-ttu-id="7d7dd-p104">데이터 상주 옵션 및 고객 데이터를 새 지역으로 이동할 수 있는 기능이 시작되는 모든 새 지역에서 기본적으로 제공되는 것은 아닙니다. 향후에 새 지역으로 확장하게 되면 지역별로 데이터 이동의 가용성 및 조건을 평가할 것입니다.</span><span class="sxs-lookup"><span data-stu-id="7d7dd-p104">The data residency option, and the availability to move customer data into the new geo, is not a default for every new geo we launch. As we expand into new geos in the future, we'll evaluate the availability and the conditions of data moves on a geo by geo basis.</span></span> 
  
<span data-ttu-id="7d7dd-151">새 데이터 센터 지역이 사용 가능해진 이후에 만들어진 신규 고객 또는 Office 365 테넌트의 경우 휴지 상태의 핵심 고객 데이터가 새 데이터 센터 지역에 자동으로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d7dd-151">New customers or Office 365 tenants created after the availability of the new datacenter geo will have their core customer data stored at rest in the new datacenter geo automatically.</span></span>
  
<span data-ttu-id="7d7dd-152">전체 목록은 모든 데이터 센터 geos, 데이터 센터 및 보관 된 고객 데이터의 위치를 사용할 수 있는 [대화형 데이터 센터에 매핑합니다](https://aka.ms/dcmaps)의 일부로 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d7dd-152">A complete list of all datacenter geos, datacenters, and the location of customer data at rest is available as part of the [interactive datacenter maps](https://aka.ms/dcmaps).</span></span> 
  
## <a name="data-residency-option"></a><span data-ttu-id="7d7dd-153">데이터 상주 옵션</span><span class="sxs-lookup"><span data-stu-id="7d7dd-153">Data residency option</span></span>

<span data-ttu-id="7d7dd-p105">위의 표에 나열 된 데이터 센터 geos에 포함 된 기존 Office 365 고객 데이터 residency 옵션을 제공 합니다. 이 옵션을 고객 데이터 residency 요구 사항에는 새로운 지리적으로 분산으로 핵심 고객 데이터를 이동 하려면 요청할 수 있습니다. 해당 조직에서는 핵심 고객 데이터를 자신의 해당 새 데이터 센터 지리적으로 분산의 나머지 부분에 저장 해야 하지 않는 한 것을 고객을에 아무 작업도 좋습니다. 해당 데이터를 이동 하려면를 선택 하 여 고객 나머지가 현재 또는 새 데이터 센터 지리적으로 분산 된 핵심 고객 데이터의 위치를 최적화 하기 위해 Microsoft의 가능성을 제한 합니다. 이러한 두 geos 중 하나에 고객,으로 이전과 동일한 방법으로 서비스, 성능 및 보안 컨트롤의 동일한 품질을 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d7dd-p105">We provide a data residency option to existing Office 365 customers who are covered by the datacenter geos listed in the table above. With this option, customers with data residency requirements can request to move their core customer data into the new geo. We recommend our customers to take no action, unless their organization needs core customer data to be stored at rest in their respective new datacenter geo. By choosing to move their data, customers limit Microsoft's possibilities to optimize the location of core customer data at rest in either their current or the new datacenter geo. As a customer in any of those two geos, you will experience the same quality of service, performance and security controls as you did before.</span></span>
  
<span data-ttu-id="7d7dd-159">핵심 데이터를 새 지역으로 이동해야 하는 고객:</span><span class="sxs-lookup"><span data-stu-id="7d7dd-159">For customers who need to have their core data moved to the new geo:</span></span>
  
- <span data-ttu-id="7d7dd-p106">고객 집합 등록 창 내에서 이동 되는 해당 데이터를 요청 해야 합니다. 등록 창에 지리적으로 분산 하 고 프로그램으로 등록 하는 단계에 대 한 자세한 내용은 [데이터 이동 요청 하는 방법](request-your-data-move.md) 페이지를 검토 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d7dd-p106">Customers will need to request to have their data moved within a set enrollment window. Review the [How to request your data move](request-your-data-move.md) page for more details about the enrollment window for your geo and the steps to enroll into the program.</span></span> 
    
- <span data-ttu-id="7d7dd-162">데이터 이동은 요청 기간이 완료되고 24개월까지 소요될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d7dd-162">Data moves can take up to 24 months after the request period to complete.</span></span>
    
- <span data-ttu-id="7d7dd-163">Microsoft는 새 데이터 센터 지역에 고유한 기능 또는 규정 준수 인증을 도입하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7d7dd-163">We introduce no unique capabilities, features or compliance certifications with the new datacenter geo.</span></span>
    
- <span data-ttu-id="7d7dd-p107">전체적으로 운영되는 자동화 환경에서 데이터 이동을 수행할 때 수반되는 복잡성, 정밀도 및 규모 때문에 귀하의 테넌트 또는 다른 단일 테넌트에서 데이터 이동이 완료될 것으로 예상되는 시기를 알려드리기가 어렵습니다. 고객은 데이터 이동이 완료되었을 때 메시지 센터에서 관련 서비스별로 1번의 확인을 받게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d7dd-p107">The complexity, precision and scale at which we need to perform data moves within a globally operated and automated environment prohibit us from sharing when a data move is expected to complete for your tenant or any other single tenant. Customers will receive one confirmation in Message Center per participating service when its data move has completed.</span></span> 
    
- <span data-ttu-id="7d7dd-p108">데이터 이동은 백엔드 서비스 작업을 최종 사용자에 게 미치는 영향 최소화 합니다. 영향을 미칠 수 있는 기능 [중 및 데이터 이동 후](during-and-after-your-data-move.md) 페이지에 나열 됩니다. 위치 고객 필요한 준비 하기 위해 또는 이동 하는 동안 모니터링 하는 경우 nothing 이므로 가용성을 위해 [Microsoft Online Services 서비스 수준 계약 (SLA)를](https://go.microsoft.com/fwlink/p/?LinkId=523897) 준수 합니다. 필요한 모든 서비스 유지 관리에 대 한 알림은 작업이 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d7dd-p108">Data moves are a back-end service operation with minimal impact to end-users. Features that can be impacted are listed on the [During and after your data move](during-and-after-your-data-move.md) page. We adhere to the [Microsoft Online Services Service Level Agreement (SLA)](https://go.microsoft.com/fwlink/p/?LinkId=523897) for availability so there is nothing that customers need to prepare for or to monitor during the move. Notification of any service maintenance is done if needed.</span></span> 
    
## <a name="related-topics"></a><span data-ttu-id="7d7dd-170">관련 항목</span><span class="sxs-lookup"><span data-stu-id="7d7dd-170">Related topics</span></span> 
 
[<span data-ttu-id="7d7dd-171">데이터 이동을 요청하는 방법</span><span class="sxs-lookup"><span data-stu-id="7d7dd-171">How to request your data move</span></span>](request-your-data-move.md)
    
[<span data-ttu-id="7d7dd-172">데이터 이동 일반 FAQ</span><span class="sxs-lookup"><span data-stu-id="7d7dd-172">Data move general FAQ</span></span>](data-move-faq.md)
  
[<span data-ttu-id="7d7dd-173">Microsoft Dynamics CRM Online에 대 한 새 데이터 센터 geos</span><span class="sxs-lookup"><span data-stu-id="7d7dd-173">New datacenter geos for Microsoft Dynamics CRM Online</span></span>](https://go.microsoft.com/fwlink/p/?Linkid=615924)
  
[<span data-ttu-id="7d7dd-174">지역별 azure 서비스</span><span class="sxs-lookup"><span data-stu-id="7d7dd-174">Azure services by region</span></span>](https://azure.microsoft.com/en-us/regions/)
  

