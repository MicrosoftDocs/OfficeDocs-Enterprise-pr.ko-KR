---
title: Office 365 서비스 상태를 확인하는 방법
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: article
f1_keywords:
- O365P_ServiceHealthModern
- O365M_ServiceHealthModern
- O365E_ViewStatusServices
- O365E_ServiceHealthModern
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
- IWA160
ms.assetid: 932ad3ad-533c-418a-b938-6e44e8bc33b0
description: 활성 서비스 중단 되었는지 확인 하려면 지원팀에 문의 하기 전에 Office 365 서비스의 상태를 확인 합니다.
ms.openlocfilehash: 7e04e1309c990ccced67663576285f7276603ccc
ms.sourcegitcommit: 6826e0ea4a777f7d98500209a9d3bc75e89f8d15
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/30/2019
ms.locfileid: "29651192"
---
# <a name="how-to-check-office-365-service-health"></a><span data-ttu-id="5cf97-103">Office 365 서비스 상태를 확인하는 방법</span><span class="sxs-lookup"><span data-stu-id="5cf97-103">How to check Office 365 service health</span></span>

<span data-ttu-id="5cf97-p101">관리 센터에서 Office 365 **서비스 상태** 페이지에서 Office 365, Yammer, Microsoft Dynamics CRM 및 Microsoft Intune 클라우드 서비스의 상태를 볼 수 있습니다. 클라우드 서비스에 문제가 발생 하는 경우에 지원팀에 문의 하거나 시간을 백분율로 나타내는 시간 문제를 해결 하기 전에 진행 중인 해상도 알려진된 문제가 인지 여부를 확인 하려면 서비스 상태를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cf97-p101">You can view the health of Office 365, Yammer, Microsoft Dynamics CRM, and Microsoft Intune cloud services on the Office 365 **Service health** page in the admin center. If you are experiencing problems with a cloud service, you can check the service health to determine whether this is a known issue with a resolution in progress before you call support or spend time troubleshooting.</span></span> 

<span data-ttu-id="5cf97-106">서비스 포털에 로그인 할 수 없는 경우에에서 테 넌 트에 로그인 하는 경우를 방지 하는 알려진된 문제를 확인 하는 [서비스 상태 페이지](https://status.office365.com) 를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cf97-106">If you are unable to sign in to the service portal, you can use the [service status page](https://status.office365.com) to check for known issues preventing you from logging into your tenant.</span></span>
  
### <a name="how-to-check-service-health"></a><span data-ttu-id="5cf97-107">서비스 상태 확인 방법</span><span class="sxs-lookup"><span data-stu-id="5cf97-107">How to check service health</span></span>

1. <span data-ttu-id="5cf97-108">[https://portal.office.com/adminportal/home](https://portal.office.com/adminportal/home#/homepage)으로 이동하여 관리자 계정으로 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="5cf97-108">Go to [https://portal.office.com/adminportal/home](https://portal.office.com/adminportal/home#/homepage) and sign in with an admin account.</span></span> 
    
    > [!NOTE]
    > <span data-ttu-id="5cf97-p102">전역 관리자 또는 서비스 관리자 역할이 할당된 사용자는 서비스 상태를 볼 수 있습니다. Exchange, SharePoint 및 비즈니스용 Skype 관리자가 서비스 상태를 볼 수 있도록 하려면 이러한 관리자에게도 서비스 관리자 역할을 할당해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cf97-p102">People who are assigned the global admin or service administrator role can view service health. To allow Exchange, SharePoint, and Skype for Business admins to view service health, they must also be assigned the Service admin role.</span></span>
  
2. <span data-ttu-id="5cf97-p103">관리 센터에서 서비스 상태를 열려면 **상태**로 이동 > **서비스 상태**하거나 **홈 대시보드** **서비스 상태 카드** 를 클릭 합니다. 대시보드 카드 활성 서비스 문제 및 자세한 서비스 상태 페이지에 대 한 링크를 인지를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5cf97-p103">To open service health, in the admin center, go to **Health** > **Service health**, or click the **Service health card** on the **Home dashboard**. The dashboard card indicates whether there is an active service issue and links to the detailed service health page.</span></span>
    
    ![Dashboard card for service health](media/8ae3de43-7bd5-4ee9-90ed-8b5ba5f9b474.png)
  
3. <span data-ttu-id="5cf97-114">각 클라우드 서비스의 상태는 가능한 상태를 표시하는 아이콘이 포함된 표 형식으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cf97-114">The health state of each cloud service is shown in a table format with an icon to indicate possible states.</span></span>
    
> [!TIP]
> <span data-ttu-id="5cf97-115">모바일 장치에서 [Office 365 관리 앱](https://go.microsoft.com/fwlink/p/?linkid=627216)을 사용하여 서비스 상태를 볼 수도 있습니다. 이 방법은 푸시 알림을 통해 최신 상태를 유지하는 좋은 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="5cf97-115">You can also use the [Office 365 Admin app](https://go.microsoft.com/fwlink/p/?linkid=627216) on your mobile device to view Service health, which is a great way to stay current with push notifications.</span></span> 
  
### <a name="view-details-of-posted-service-health"></a><span data-ttu-id="5cf97-116">게시된 서비스 상태의 세부 정보 보기</span><span class="sxs-lookup"><span data-stu-id="5cf97-116">View details of posted service health</span></span>

<span data-ttu-id="5cf97-p104">기본 보기에서 모든 서비스 및 현재 상태 상태로 표시 됩니다. 인시던트를 발생 하는 현재 서비스에 보기를 필터링 하려면 음영 처리 된 막대를 왼쪽에에서 **인시던트** 를 선택 합니다. **권고** 를 선택 하면 현재 게시 하는 권고를가지고 있는 서비스에만 표시 됩니다. **모든 서비스** 보기에서 표시 된 서비스의 상태를 클릭 하면 자문 또는 사고 요약 보기를 열립니다.</span><span class="sxs-lookup"><span data-stu-id="5cf97-p104">In the default view, all services and their current health state are displayed. To filter your view to services currently experiencing an incident, select **Incidents** from the shaded bar on the left. Selecting **Advisories** will show only services that currently have an advisory posted. From the **All services** view, clicking the displayed service state will open a summary view of the advisory or incident.</span></span> 
  
![View of current issues in service health](media/f829a3af-1aca-4dc2-97eb-15d805349b24.png)
  
<span data-ttu-id="5cf97-122">권고 또는 인시던트 요약은 다음 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="5cf97-122">The advisory or incident summary provides the following information:</span></span> 
  
![서비스 자문의 필드에 레이블을 지정 하는 스크린샷](media/0dd6065c-1381-4a5c-8ca0-854c3e043a5c.png)
  
1. <span data-ttu-id="5cf97-124">문제 식별자 및 문제에 대한 요약 설명.</span><span class="sxs-lookup"><span data-stu-id="5cf97-124">An issue identifier and summary statement of the problem.</span></span>
    
2. <span data-ttu-id="5cf97-p105">현재 상태. 각 잠재적 상태에 대한 설명은 이 문서의 상태 정의를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5cf97-p105">The current status. See status definitions in this article for an explanation of each potential status.</span></span>
    
3. <span data-ttu-id="5cf97-127">이 문제가 사용자에게 영향을 줄 수 있는 방법에 대한 설명.</span><span class="sxs-lookup"><span data-stu-id="5cf97-127">A description of how this issue can affect users.</span></span>
    
4. <span data-ttu-id="5cf97-p106">문제가 시작된 시간과 서비스 상태 메시지가 마지막으로 업데이트된 시간. 문제가 지속되는 기간 내내 해결 방법을 적용하는 것과 관련한 진행 상태를 알 수 있도록 메시지를 빈번하게 게시합니다.</span><span class="sxs-lookup"><span data-stu-id="5cf97-p106">The time that the issue was started and the last time that the service health message was updated. Throughout the duration of an issue we post frequent messages to let you know the progress that we're making in applying a solution.</span></span>
    
5. <span data-ttu-id="5cf97-130">해결 방법에 대해 작업하는 동안 게시된 모든 메시지 기록을 비롯한 문제에 대한 세부 정보를 보려면 **세부 정보 표시** 링크를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5cf97-130">Select the **Show details** link to see more details about the issue, including the history of all messages posted while we work on a solution.</span></span> 
    
### <a name="translate-service-health-details"></a><span data-ttu-id="5cf97-131">서비스 상태 세부 정보 번역</span><span class="sxs-lookup"><span data-stu-id="5cf97-131">Translate service health details</span></span>

<span data-ttu-id="5cf97-p107">서비스 상태 설명은 실시간으로 게시되므로 해당 언어로 자동 번역되지 않으며 서비스 이벤트의 세부 정보는 영어로만 제공됩니다. 설명을 번역하려면 다음 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="5cf97-p107">Because service health explanations are posted in real-time, they are not automatically translated to your language and the details of a service event are in English only. To translate the explanation, follow these steps:</span></span>
  
1. <span data-ttu-id="5cf97-134">1.[번역기](https://www.bing.com/translator/)로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="5cf97-134">Go to [Translator](https://www.bing.com/translator/).</span></span>
    
2. <span data-ttu-id="5cf97-p108">**서비스 상태** 페이지에서 인시던트 또는 권고를 선택합니다. **세부 정보 표시** 아래에서 문제에 대한 텍스트를 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="5cf97-p108">On the **Service health** page, select an incident or advisory. Under **Show details**, copy the text about the issue.</span></span>
    
3. <span data-ttu-id="5cf97-137">번역기에서 텍스트를 붙여넣고 **번역하기**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5cf97-137">In Translator, paste the text and choose **Translate**.</span></span>
    
### <a name="definitions"></a><span data-ttu-id="5cf97-138">정의</span><span class="sxs-lookup"><span data-stu-id="5cf97-138">Definitions</span></span>

<span data-ttu-id="5cf97-p109">대부분의 시간에 서비스는 추가 정보 없이 정상으로 표시됩니다. 서비스에 문제가 있으면 문제가 권고 또는 인시던트로 식별되고 현재 상태를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5cf97-p109">Most of the time services will appear as healthy with no further information. When a service is having a problem, the issue is identified as either an advisory or an incident and shows a current status.</span></span>
  
> [!TIP]
> <span data-ttu-id="5cf97-p110">계획된 유지 관리 이벤트는 서비스 상태에 표시되지 않습니다. **메시지 센터**를 통해 최신 상태를 유지함으로써 계획된 유지 관리 이벤트를 추적할 수 있습니다. 변경 계획으로 분류된 메시지로 필터링하여 변경이 발생하는 시기, 해당 효과 및 이러한 변경에 대해 준비하는 방법을 확인하세요. 자세한 내용은 [Office 365의 메시지 센터](https://support.office.com/article/38fb3333-bfcc-4340-a37b-deda509c2093)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5cf97-p110">Planned maintenance events aren't shown in service health. You can track planned maintenance events by staying up to date with the **Message center**. Filter to messages categorized as Plan for change to find out when the change is going to happen, its effect, and how to prepare for it. See [Message center in Office 365](https://support.office.com/article/38fb3333-bfcc-4340-a37b-deda509c2093) for more details.</span></span> 
  
### <a name="incidents-and-advisories"></a><span data-ttu-id="5cf97-145">인시던트 및 권고</span><span class="sxs-lookup"><span data-stu-id="5cf97-145">Incidents and advisories</span></span>

|||
|:-----|:-----|
|![Information icon for advisory](media/a7f5fd21-c760-4948-9bc1-50f7c8070e28.png)|<span data-ttu-id="5cf97-p111">서비스에 권고가 표시되면 Microsoft에서 일부 사용자에게 영향을 미치는 문제를 알고 있지만, 서비스를 계속 사용할 수는 있습니다. 권고에는 일반적으로 문제에 대한 해결 방법이 있으며, 문제가 일시적으로 발생하는 것일 수 있거나 범위 및 사용자 영향에서 제한적입니다.</span><span class="sxs-lookup"><span data-stu-id="5cf97-p111">If a service has an advisory shown, we are aware of a problem that is affecting some users, but the service is still available. In an advisory, there is often a workaround to the problem and the problem may be intermittent or is limited in scope and user impact.</span></span>  <br/> |
|![Exclamation point icon for incident](media/a636db57-6083-44dc-bbd5-556850804f17.png)|<span data-ttu-id="5cf97-p112">서비스에 활성 인시던트가 표시되면 이 인시던트가 중요 문제이며 서비스 또는 서비스의 주요 기능을 사용할 수 없습니다. 예를 들어 사용자가 전자 메일을 보내고 받을 수 없거나 로그인할 수 없습니다. 인시던트는 사용자에게 눈에 띄는 영향을 줍니다. 진행 중인 인시던트가 있는 경우 서비스 상태 대시보드에서 조사, 완화 노력 및 해결 확인과 관련된 업데이트를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="5cf97-p112">If a service has an active incident shown, it's a critical issue and the service or a major function of the service is unavailable. For example, users may be unable to send and receive email or unable to sign-in. Incidents will have noticeable impact to users. When there is an incident in progress, we will provide updates regarding the investigation, mitigation efforts, and confirmation of resolution in the Service health dashboard.</span></span>  <br/> |
   
### <a name="status-definitions"></a><span data-ttu-id="5cf97-154">상태 정의</span><span class="sxs-lookup"><span data-stu-id="5cf97-154">Status definitions</span></span>

|<span data-ttu-id="5cf97-155">**상태**</span><span class="sxs-lookup"><span data-stu-id="5cf97-155">**Status**</span></span>|<span data-ttu-id="5cf97-156">**정의**</span><span class="sxs-lookup"><span data-stu-id="5cf97-156">**Definition**</span></span>|
|:-----|:-----|
|<span data-ttu-id="5cf97-157">**조사하는 중**</span><span class="sxs-lookup"><span data-stu-id="5cf97-157">**Investigating**</span></span> | <span data-ttu-id="5cf97-158">Microsoft에서 잠재적인 문제를 알고 있으며 문제의 상황과 영향의 범위에 대한 추가 정보를 수집하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cf97-158">We're aware of a potential issue and are gathering more information about what's going on and the scope of impact.</span></span> |
|<span data-ttu-id="5cf97-159">**서비스 저하**</span><span class="sxs-lookup"><span data-stu-id="5cf97-159">**Service degradation**</span></span> | <span data-ttu-id="5cf97-p113">Microsoft에서 서비스 또는 기능 사용에 영향을 줄 수 있는 문제가 있음을 확인했습니다. 서비스가 평소보다 느리게 작동하거나, 일시적인 중단이 발생하거나, 기능이 작동하지 않는 등의 경우에 이 상태가 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cf97-p113">We've confirmed that there is an issue that may affect use of a service or feature. You might see this status if a service is performing more slowly than usual, there are intermittent interruptions, or if a feature isn't working, for example.</span></span> |
|<span data-ttu-id="5cf97-162">**서비스 중단**</span><span class="sxs-lookup"><span data-stu-id="5cf97-162">**Service interruption**</span></span> | <span data-ttu-id="5cf97-p114">문제가 사용자의 서비스 액세스 기능에 영향을 준다고 판단한 이 상태가 표시됩니다. 이 경우 문제가 중대하며 일관되게 재현될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cf97-p114">You'll see this status if we determine that an issue affects the ability for users to access the service. In this case, the issue is significant and can be reproduced consistently.</span></span> |
|<span data-ttu-id="5cf97-165">**서비스를 복원하는 중**</span><span class="sxs-lookup"><span data-stu-id="5cf97-165">**Restoring service**</span></span> | <span data-ttu-id="5cf97-166">문제의 원인이 식별되었으며, Microsoft에서 수행할 정정 작업을 알고 있고 서비스를 다시 정상 상태로 복원하는 프로세스를 진행하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cf97-166">The cause of the issue has been identified, we know what corrective action to take, and are in the process of bringing the service back to a healthy state.</span></span> |
|<span data-ttu-id="5cf97-167">**확장된 복구**</span><span class="sxs-lookup"><span data-stu-id="5cf97-167">**Extended recovery**</span></span> | <span data-ttu-id="5cf97-p115">이 상태는 대부분의 사용자에 대해 서비스를 복원하기 위한 정정 작업이 진행 중이지만, 영향을 받는 모든 시스템에 이를 적용하는 데 시간이 다소 소요될 것임을 나타냅니다. 영구적인 수정 사항을 적용하기 위해 대기하는 동안 영향을 줄이기 위해 임시 수정 사항을 적용한 경우에도 이 상태가 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cf97-p115">This status indicates that corrective action is in progress to restore service to most users but will take some time to reach all the affected systems. You might also see this status if we've made a temporary fix to reduce impact while we wait to apply a permanent fix.</span></span> |
|<span data-ttu-id="5cf97-170">**조사 일시 중단됨**</span><span class="sxs-lookup"><span data-stu-id="5cf97-170">**Investigation suspended**</span></span> | <span data-ttu-id="5cf97-p116">잠재적 문제에 대한 자세한 조사 결과, 추가 조사를 하기 위한 고객의 추가 정보가 필요한 경우 이 상태가 표시됩니다. 고객의 행동이 요구되는 경우 필요한 데이터나 로그를 알려드립니다.</span><span class="sxs-lookup"><span data-stu-id="5cf97-p116">If our detailed investigation of a potential issue results in a request for additional information from customers to allow us to investigate further, you'll see this status. If we need you to act, we'll let you know what data or logs we need.</span></span> |
|<span data-ttu-id="5cf97-173">**서비스 복원됨**</span><span class="sxs-lookup"><span data-stu-id="5cf97-173">**Service restored**</span></span> | <span data-ttu-id="5cf97-p117">Microsoft에서 정정 작업이 기본 문제를 해결했으며 서비스가 정상 상태로 복원되었음을 확인했습니다. 문제를 확인하려면 문제 세부 정보를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="5cf97-p117">We've confirmed that corrective action has resolved the underlying problem and the service has been restored to a healthy state. To find out what went wrong, view the issue details.</span></span> |
|<span data-ttu-id="5cf97-176">**게시 된 이후 문제 보고서**</span><span class="sxs-lookup"><span data-stu-id="5cf97-176">**Post-incident report published**</span></span> | <span data-ttu-id="5cf97-177">루트 원인 정보 및 비슷한 문제가 발생 하지 확인 하려면 다음 단계를 포함 하는 특정 문제에 대 한 게시물 위해 문제 보고서를 게시 한 했습니다.</span><span class="sxs-lookup"><span data-stu-id="5cf97-177">We’ve published a Post Incident Report for a specific issue that includes root cause information and next steps to ensure a similar issue doesn’t reoccur.</span></span> |
   
## <a name="history"></a><span data-ttu-id="5cf97-178">기록</span><span class="sxs-lookup"><span data-stu-id="5cf97-178">History</span></span>

<span data-ttu-id="5cf97-p118">서비스 상태를 통해 현재 상태를 확인하고 지난 30일간의 모든 서비스 권고 및 인시던트 기록을 볼 수 있습니다. 모든 서비스의 과거 상태를 보려면 **서비스 상태** 페이지에서 **기록 보기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5cf97-p118">Service health lets you look at current health status and view the history of any service advisories and incidents in the past 30 days. To view the past health of all services, select **View history** on the **Service health** page.</span></span> 
  
![Show link to health history](media/12a3e484-1eb4-497f-8cab-8064bccc2ef5.png)
  
<span data-ttu-id="5cf97-182">선택한 시간 범위에서 게시된 모든 서비스 상태 메시지 목록이 다음과 같이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cf97-182">A list of all service health messages posted in the selected timeframe is displayed, as shown below:</span></span>
  
![View service health history](media/5ed20247-121c-4abe-9fe7-9025e26a2d0e.png)
  
<span data-ttu-id="5cf97-p119">7 일이 지난 또는 지난 30 일에 대 한 상태 기록을 볼 수 있습니다. 이 문제에 대 한 자세한 세부 정보를 보려면 모든 행을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cf97-p119">You may view the health history for either the last 7 days or last 30 days. Select any row to view more details about that issue.</span></span>
  
<span data-ttu-id="5cf97-186">가동 시간을 위한 노력 하는 방법에 대 한 자세한 내용은 [Office 365에서 투명 하 게 작업](https://go.microsoft.com/fwlink/?linkid=848695)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="5cf97-186">For more information about our commitment to uptime, see [Transparent operations from Office 365](https://go.microsoft.com/fwlink/?linkid=848695).</span></span>
  
## <a name="leave-feedback"></a><span data-ttu-id="5cf97-187">사용자 의견 남기기</span><span class="sxs-lookup"><span data-stu-id="5cf97-187">Leave feedback</span></span>

<span data-ttu-id="5cf97-p120">Microsoft의 목표는 진행 중인 문제에 대해 고객에게 제공하는 정보가 시기적절하고 정확하며 유용하도록 하는 것입니다. Microsoft에 대해 평가하려면 별 등급을 선택하세요. 별 1~5개 등급으로 점수를 입력하면 특정 세부 정보에 대한 사용자 의견을 남길 수 있습니다. Microsoft에서는 사용자 의견을 사용하여 서비스 상태 시스템을 세밀하게 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="5cf97-p120">Our goal is to make sure that the information we provide to you about an ongoing issue is timely, accurate, and useful. To tell us how we're doing, select a star rating. After you give us a score from 1 to 5 stars, you can give feedback on any specific details. We'll use your feedback to fine-tune our service health system.</span></span>
  
![Feedback form for service health issues](media/fd083fdb-fde8-47b4-9136-b90d1d003864.png)
  
## <a name="see-also"></a><span data-ttu-id="5cf97-193">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5cf97-193">See also</span></span>

[<span data-ttu-id="5cf97-194">Office 365 관리 센터의 활동 보고서</span><span class="sxs-lookup"><span data-stu-id="5cf97-194">Activity Reports in the Office 365 admin center</span></span>](https://support.office.com/article/0d6dfb17-8582-4172-a9a9-aed798150263)

