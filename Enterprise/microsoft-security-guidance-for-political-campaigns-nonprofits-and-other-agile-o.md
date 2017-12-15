---
title: "정치적 캠페인, 비영리, 및 기타 민첩 한 조직에 대 한 Microsoft 보안 지침"
ms.author: bcarter
author: bcarter
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.custom:
- DecEntMigration
- Strat_O365_Enterprise
ms.assetid: 10d1004b-42b6-4e2b-aaa2-18ddd9118f64
description: "요약: 계획 및 구현 지침 빠른 이동에 대 한 증가 위협 프로필 하는 조직에서는 합니다."
ms.openlocfilehash: 632cb63877e159f18707dbf68eb7733082319654
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2017
---
# <a name="microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-organizations"></a><span data-ttu-id="6f400-103">정치적 캠페인, 비영리, 및 기타 민첩 한 조직에 대 한 Microsoft 보안 지침</span><span class="sxs-lookup"><span data-stu-id="6f400-103">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>

 <span data-ttu-id="6f400-104">**요약:** 빠른 이동에 대 한 계획 및 구현 지침 증가 위협 프로필 하는 조직에서는 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f400-104">**Summary:** Planning and implementation guidance for fast-moving organizations that have an increased threat profile.</span></span>
  
<span data-ttu-id="6f400-p101">조직은 신속한, 소규모 IT 팀 있고 경우 위협 프로필은 평균 보다 높은,이 설명서 하기 위해 고안 되었습니다. 이 솔루션을 신속 하 게 시작 부분에서 보안 컨트롤을 포함 하는 필수 클라우드 서비스를 사용 하는 환경을 만드는 방법을 보여줍니다. 이 설명서에는 모바일 장치에서 데이터, id, 전자 메일 및 액세스를 보호 하기 위해 규정 보안 권장 사항이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f400-p101">If your organization is agile, you have a small IT team, and your threat profile is higher than average, this guidance is designed for you. This solution demonstrates how to quickly build an environment with essential cloud services that include secure controls from the start. This guidance includes prescriptive security recommendations for protecting data, identities, email, and access from mobile devices.</span></span>
  
## <a name="security-solution-guidance"></a><span data-ttu-id="6f400-108">보안 솔루션 가이드</span><span class="sxs-lookup"><span data-stu-id="6f400-108">Security solution guidance</span></span>

<span data-ttu-id="6f400-p102">이 설명서에서는 보안 클라우드 환경을 구현 하는 방법에 설명 합니다. 모든 조직에서 솔루션 파일에 대 한 지침을 사용할 수 있습니다. 민첩 한 조직 BYOD 액세스 및 게스트 계정에 대 한 추가 도움말을 포함합니다. 사용자가 자신의 환경 디자인 (영문)에 대 한 시작 지점으로이 설명서를 사용할 수 있습니다. [CloudAdopt@microsoft.com](mailto:CloudAdopt@microsoft.com)에서 여러분의 의견을 환영합니다.</span><span class="sxs-lookup"><span data-stu-id="6f400-p102">This guidance describes how to implement a secure cloud environment. The solution guidance can be used by any organization. It includes extra help for agile organizations with BYOD access and guest accounts. You can use this guidance as a starting-point for designing your own environment. We welcome your feedback at [CloudAdopt@microsoft.com](mailto:CloudAdopt@microsoft.com).</span></span> 
  
|||
|:-----|:-----|
|<span data-ttu-id="6f400-114">**항목**</span><span class="sxs-lookup"><span data-stu-id="6f400-114">**Item**</span></span> <br/> |<span data-ttu-id="6f400-115">**설명**</span><span class="sxs-lookup"><span data-stu-id="6f400-115">**Description**</span></span> <br/> |
|<span data-ttu-id="6f400-116">**정치적 캠페인에 대 한 Microsoft 보안 지침**</span><span class="sxs-lookup"><span data-stu-id="6f400-116">**Microsoft Security Guidance for Political Campaigns**</span></span> <br/> <span data-ttu-id="6f400-117">[![미니 포스터 (영문)에 대 한 축소판 그림 못 설정합니다.](images/d370ce28-ca40-4930-9a2c-907312aa06c8.png)          ](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security for political campaigns.pdf)</span><span class="sxs-lookup"><span data-stu-id="6f400-117">[![Thumb nail for mini poster set.](images/d370ce28-ca40-4930-9a2c-907312aa06c8.png)          ](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security for political campaigns.pdf)</span></span> <br/> <span data-ttu-id="6f400-118">[PDF](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security for political campaigns.pdf)  \\</span><span class="sxs-lookup"><span data-stu-id="6f400-118">[PDF](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security for political campaigns.pdf)  \\</span></span>| [<span data-ttu-id="6f400-119">Visio</span><span class="sxs-lookup"><span data-stu-id="6f400-119">Visio</span></span>](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security for political campaigns.vsdx) <br/> |<span data-ttu-id="6f400-p103">이 지침을 예로 정치적 캠페인 조직을 사용합니다. 모든 환경에 대 한 시작 지점으로이 가이드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f400-p103">This guidance uses a political campaign organization as an example. Use this guidance as a starting point for any environment.</span></span>  <br/> |
|<span data-ttu-id="6f400-122">**비영리에 대 한 Microsoft 보안 지침**</span><span class="sxs-lookup"><span data-stu-id="6f400-122">**Microsoft Security Guidance for Nonprofits**</span></span> <br/> <span data-ttu-id="6f400-123">[![다운로드 가능한 파일에 대 한 축소판 그림 이미지](images/e4784889-1c69-4067-9a8f-31d31d1eceea.png)          ](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud Architecture_Security for Nonprofits.pdf)</span><span class="sxs-lookup"><span data-stu-id="6f400-123">[![Thumnail image for downloadable file](images/e4784889-1c69-4067-9a8f-31d31d1eceea.png)          ](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud Architecture_Security for Nonprofits.pdf)</span></span> <br/> <span data-ttu-id="6f400-124">[PDF](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud Architecture_Security for Nonprofits.pdf)  \\</span><span class="sxs-lookup"><span data-stu-id="6f400-124">[PDF](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud Architecture_Security for Nonprofits.pdf)  \\</span></span>| [<span data-ttu-id="6f400-125">Visio</span><span class="sxs-lookup"><span data-stu-id="6f400-125">Visio</span></span>](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud Architecture_Security for Nonprofits.vsdx) <br/> |<span data-ttu-id="6f400-p104">이 가이드는 약간 비 이익 조직에 대 한 개정 됩니다. 예, Office 365 비 이익 계획을 참조합니다. 기술 설명서 정치적 캠페인 솔루션 가이드와 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f400-p104">This guide is slightly revised for nonprofit organizations. For example, it references Office 365 Nonprofit plans. The technical guidance is the same as the political campaign solution guide.</span></span>  <br/> |
   
## <a name="test-lab-guides"></a><span data-ttu-id="6f400-129">테스트 랩 가이드</span><span class="sxs-lookup"><span data-stu-id="6f400-129">Test Lab Guides</span></span>

<span data-ttu-id="6f400-130">이 솔루션에 대 한 개발/테스트 환경을 만들려면 다음과 같은 테스트 랩 가이드를 사용 하 여:</span><span class="sxs-lookup"><span data-stu-id="6f400-130">To create a dev/test environment for this solution, use the following test lab guides:</span></span> 
  
- [<span data-ttu-id="6f400-131">정치적 캠페인 개발/테스트 환경에 대 한 사용자 및 그룹 구성</span><span class="sxs-lookup"><span data-stu-id="6f400-131">Configure groups and users for a political campaign dev/test environment</span></span>](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md)
    
     <span data-ttu-id="6f400-132">Office 365 및 EMS 평가판 구독 만들고 그룹 및 대표 정치적 캠페인에 대 한 사용자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6f400-132">Create trial subscriptions for Office 365 and EMS and then create groups and users for a representative political campaign.</span></span>
    
- [<span data-ttu-id="6f400-133">정치적 캠페인 개발/테스트 환경에서 팀 사이트 만들기</span><span class="sxs-lookup"><span data-stu-id="6f400-133">Create team sites in a political campaign dev/test environment</span></span>](create-team-sites-in-a-political-campaign-dev-test-environment.md)
    
    <span data-ttu-id="6f400-134">보안의 내부, 개인, 민감한 및 기밀 수준을 사용 하 여 4 개의 SharePoint Online 팀 사이트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6f400-134">Create four SharePoint Online team sites with Internal, Private, Sensitive, and Highly Confidential levels of security.</span></span>
    
<span data-ttu-id="6f400-135">데모 또는 개념 증명에 대 한 추가 보안 기능을 [Office 365 테스트 랩 가이드](http://aka.ms/o365tlgs)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="6f400-135">For additional security features for demonstration or proof of concept, see [Office 365 Test Lab Guides](http://aka.ms/o365tlgs).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="6f400-136">See Also</span><span class="sxs-lookup"><span data-stu-id="6f400-136">See Also</span></span>

[<span data-ttu-id="6f400-137">보안 솔루션</span><span class="sxs-lookup"><span data-stu-id="6f400-137">Security solutions</span></span>](security-solutions.md)
  
[<span data-ttu-id="6f400-138">클라우드 채택 테스트 랩 가이드 (Tlg)</span><span class="sxs-lookup"><span data-stu-id="6f400-138">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="6f400-139">Microsoft 클라우드 IT 아키텍처 리소스</span><span class="sxs-lookup"><span data-stu-id="6f400-139">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)



