---
title: 용량 계획 및 부하 테스트를 SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/18/2016
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: c932bd9b-fb9a-47ab-a330-6979d03688c0
description: 이 문서에서는 배포 하는 방법 SharePoint Online으로 허용 되지 않은 이후 전통적인 부하 테스트를 수행 하지 않고에 대해 설명 합니다.
ms.openlocfilehash: 490d05598c42cd5d94f61dd21ee5a11701d4b4a7
ms.sourcegitcommit: 033156d46ac0fb5f05d2b1a594d5ef368b93b893
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/04/2018
ms.locfileid: "27134673"
---
# <a name="capacity-planning-and-load-testing-sharepoint-online"></a><span data-ttu-id="4752f-103">용량 계획 및 부하 테스트를 SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="4752f-103">Capacity planning and load testing SharePoint Online</span></span>

<span data-ttu-id="4752f-104">이 문서에서는 배포 하는 방법 SharePoint online 권장 되므로 일반적인 부하 테스트를 수행 하지 않고에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="4752f-104">This article describes how you can deploy to SharePoint Online without performing traditional load testing since it is strongly discouraged.</span></span>
  
<span data-ttu-id="4752f-105">현재 부하를 SharePoint Online에서 테스트는 권장 하는 다른 방법도 있습니다 수 있는지 확인 하는 사이트를 실행 하는 경우 사이트 불량 사용자 환경을 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4752f-105">Although active load testing on SharePoint Online is strongly discouraged, there are other ways you can make sure that a site will not produce a poor user experience when you launch the site.</span></span> 
  
<span data-ttu-id="4752f-p101">SharePoint Online을 사용한 필요가 없습니다 용량 계획을 수행 대로이 당사의 서비스 구축의 일부로 귀하에 대 한 작업을 수행 합니다. 온-프레미스 환경으로 배율 가정의 유효성을 검사 하 고 결국 팜; 분리 지점을 찾을 사용은 부하 테스트 여 부하와 그 포화 합니다. SharePoint Online과 다르게 작업을 수행 해야 합니다. 다중 테 넌 트 환경에는 모든 부하 테스트를 자동으로 제한 됩니다는 되므로 동일한 팜에 있는 모든 테 넌 트를 보호 하기 위해 했습니다. 이 실망 메시지가 나타나고 잠재적으로 잘못 된 결과 로드 하려고 하면 테스트 환경을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="4752f-p101">With SharePoint Online you don't have to do capacity planning, as this is done for you as part of our service offering. With on-premises environments, load testing is used to validate scale assumption and ultimately find the breaking point of a farm; by saturating it with load. With SharePoint Online we need to do things differently. Being a multi-tenant environment, we have to protect all tenants in the same farm, so we will automatically throttle any load tests. This means you will receive disappointing and potentially misleading results if you attempt to load test your environment.</span></span>
  
<span data-ttu-id="4752f-p102">온-프레미스 배포를 통해 SharePoint Online의 주요 이점 중 하나는 클라우드의 탄성입니다. 이 대규모 환경의 하도록 설정 된 사용자가 매일 수백만 서비스 수 있으므로을 처리 하는 용량 효과적으로 필요할 때와 같이 팜, 자동으로 확장 하 여 중요 합니다. 이 문서에서는 용량 증가 및 확장에 대 한 계획 방법에 대해 설명의 전체 확장 합니다. 문서에는 방법 중 하나를 사용 하는 부하 테스트를 포함 하지 않으며 내용을 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="4752f-p102">One of the main benefits of SharePoint Online over an on-premises deployment is the elasticity of the cloud. Our large scale environment is set up to service millions of users on a daily basis so it is important that we handle capacity effectively by automatically expanding farms, as and when needed. This article explains how we plan for capacity growth and scale out in place. The article also covers approaches for you to use that don't involve load testing.</span></span>
  
## <a name="how-office-365-predicts-load-and-expands-capacity"></a><span data-ttu-id="4752f-115">Office 365 부하를 예측 하 고 용량을 확장 하는 방법</span><span class="sxs-lookup"><span data-stu-id="4752f-115">How Office 365 predicts load and expands capacity</span></span>

<span data-ttu-id="4752f-116">SharePoint Online 서버 용량 관리 작업은 두 메서드를 통해 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4752f-116">SharePoint Online server capacity management work is done through two methods:</span></span>
  
- <span data-ttu-id="4752f-117">용량 예측</span><span class="sxs-lookup"><span data-stu-id="4752f-117">Capacity forecasting</span></span>
    
- <span data-ttu-id="4752f-118">단일 서버 팜에서 부하 분산</span><span class="sxs-lookup"><span data-stu-id="4752f-118">Load-balancing on single server farms</span></span>
    
<span data-ttu-id="4752f-p103">SharePoint Online에서 용량 예측 하는 온-프레미스 환경에 대 한 계획 달리 통계 컴파일 및 지정 된 서버 그룹의 잠재적인 요구 그래프를 수 있습니다. 집계 제안 같을 수 있습니다는 요청 영역 (영역은 SharePoint 팜의 그룹)의 성장 줄 아래 이미지에서:</span><span class="sxs-lookup"><span data-stu-id="4752f-p103">Unlike planning for an on-premises environment, for capacity forecasting in SharePoint Online, we are able to compile statistics and graph potential requirements in any given server group. The aggregate demand might look something like the Requests in zone (where a zone is a group of SharePoint farms) growth line in the image below:</span></span>
  
![예측 용량을 보여 주는 차트:](media/ca800cb6-cc59-451f-98bd-55e035489af3.png)
  
<span data-ttu-id="4752f-p104">모든 팜 증가 예측 가능한 인 영역에서 요청의 집계 된 합계는 예측 가능한 합니다. SharePoint Online에서 성장 추세를 식별 하 여 향후 확장에 대 한 계획할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4752f-p104">While the growth is unpredictable in any one farm, the aggregated sum of requests in a zone is predictable. By identifying the growth trends in SharePoint Online, we can plan for future expansion.</span></span>
  
<span data-ttu-id="4752f-p105">효율적으로 용량을 사용 하 고 모든 팜에서 예기치 않은 증가 처리 하기 위해 프런트엔드 부하를 추적 하 고 필요할 때 장소 조정 하는 자동화를 했습니다. 최첨단 비율을 조정 하려면 신호 종료으로 사용 하는 주요 메트릭을 CPU 부하입니다. 이러한 목표는 최대 CPU 부하에서 40%를 유지 하는 것입니다. 이것은 예기치 않은 급증 상황을 처리 하기 위해 충분 한 버퍼 수 있게 만들기 위해입니다. 부하 접근 방법, 40% 안정 상태에서으로 팜에 프런트엔드 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="4752f-p105">In order to efficiently use capacity and deal with unexpected growth, in any farm, we have automation that tracks front-end load and scales up in place, when needed. The main metric we use as a signal to scale up front ends is CPU load. Our goal is to keep peak CPU load under 40%. This is in order to have enough buffer to absorb unexpected spikes. As load approaches 40% in steady state, we add front ends to farms.</span></span>
  
![예상 용량을 보여주는 차트: 농장 관리](media/6b2a8c63-24c1-4504-b7a3-3d3b3be2583a.png)
  
<span data-ttu-id="4752f-130">Forecast 사용을 통해 영역에 추가 된 하는 것을 사용 하는 팜에 추가 서버를 신속 하 게 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4752f-130">Additional servers can be quickly added to a farm, using those which have been previously added to the zone through the usage forecast.</span></span> 
  
## <a name="how-do-i-plan-for-a-site-launch"></a><span data-ttu-id="4752f-131">어떻게 사이트 출시에 대 한 계획 합니까?</span><span class="sxs-lookup"><span data-stu-id="4752f-131">How do I plan for a site launch?</span></span>

<span data-ttu-id="4752f-p106">새 사이트에서 시작 하는 팜이 자동으로 모니터링할 수 없도록 새 프런트엔드 서버를 추가 하 고, 되도록 위에서 설명한 것 처럼 예상할 수 있습니다. 이러한 이유 때문에 대 한 새 사이트 실행 프로그램에 대 한 모든 알림을 하지 않아도 했습니다.</span><span class="sxs-lookup"><span data-stu-id="4752f-p106">You should expect that the farm on which your new site launches will automatically be monitored so that new front-end servers are added, as described above. For this reason, we don't need any notification for your new site launch.</span></span>
  
<span data-ttu-id="4752f-134">SharePoint Online의 단일 페이지에 대 한 기타 유용한 과정을 따라는 100, 000도 사용자에 게는 새로운 사이트 출시 들이 있는 모든 영향 팜에 가능성이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4752f-134">Following other best practices for a single page on SharePoint Online it is unlikely that a new site launch to even 100,000 users will have any impact to the farm.</span></span>
  
<span data-ttu-id="4752f-p107">새 SharePoint Online 사이트의 버전을 계획 하는 몇 전략 가지가 있습니다. 다음 그림에 표시 된 것과 같이 자주는 초대 하는 사용자는 실제로 해당 사이트를 사용 하는 것 보다 훨씬 더 높은입니다. 이 이미지는 버전을 시작 하는 방법에 대 한 전략을 보여줍니다. 이 메서드를 성능 로드 하 여는 데 도움이 뿐아니라도 식별 하도록 도와주는 대다수 사용자의 표시 되기 전에 SharePoint 사이트를 개선 하는 방법은 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4752f-p107">There are a few strategies to plan for a release of a new SharePoint Online site. As shown in the following image, often the amount of users that are invited is significantly higher than those that actually use the site. This image shows a strategy about how to roll out a release. This method not only helps with performance loading but also can help identify ways to improve the SharePoint site before the large majority of the users see it.</span></span>
  
![초대받은 사용자 및 활성 사용자를 보여 주는 그래프](media/0bc14a20-9420-4986-b9b9-fbcd2c6e0fb9.png)
  
<span data-ttu-id="4752f-p108">파일럿 단계에서 조직 신뢰 하 고 참여 하 고가 알고 있는 사용자의 피드백을 받을 하는 것이 좋습니다. 이러한 방식으로 수 수행 하는 방법, 시스템의 사용 방식을 측정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4752f-p108">In the pilot phase, it is good to get feedback from users that the organization trusts and knows will be engaged. This way it is possible to gauge how the system is being used, as well as how it is performing.</span></span>
  
<span data-ttu-id="4752f-p109">이후 부터는 물결;에서 모든 사용자에 게 롤아웃을 시작합니다 피드백을 가져오고 성능을 정기적으로 검토 합니다. 이 느리게 시스템을 소개 하 고 향상 된 시스템 가져옵니다 더 많은 사용으로의 장점이 있습니다. 또한 점점 더 많은 사용자에 게 출시 되는 사이트와 증가 부하에 대 한 대응 수도 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="4752f-p109">After this, begins a roll out to all users in waves; getting feedback and reviewing the performance regularly. This has the advantage of slowly introducing the system and making improvements as the system gets more use. This also allows us to react to the increased load as the site is rolled out to more and more users.</span></span>
  
<span data-ttu-id="4752f-p110">마지막으로, 부하 테스트는 금지 하는 동안 고객 서비스 측정 사용 가능 여부 및 대기 시간에 정기 간행물 ping 테스트를 설정 하려는 수 있습니다. 이 자신의 사이트에 대 한 초기 계획을 식별할 수 있습니다. 그러나 이러한 제한 앞에서 설명한 문제를 방지 하기 위해 낮은 주파수를 유지 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4752f-p110">Finally, while load tests are prohibited, customers may want to set up periodical pings to the service to measure availability and latency. This will identify a baseline for their site. However, these must be kept to low frequency to avoid throttling issues previously described.</span></span>
  

